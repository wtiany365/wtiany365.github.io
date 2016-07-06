---
title: 工厂模式
tagline: ""
last_updated: 2016-07-06 17:29
category : php
layout: post
tags : [php]
---
工厂模式

```php
<?php
class operateFactory{
    static function create($type){
        switch ($type) {
            case 'add':
                $operate = new operateAdd();
                break;
            case 'minus':
                $operate = new operateMinus();
                break;
            case 'multiplication':
                $operate = new operateMultiplication();
                break;
            case 'division':
                $operate = new operateDivision();
                break;
        }
        return $operate;
    }
}
abstract class operate{
    public $a;
    public $b;
    abstract function getResult();
}
class operateAdd extends operate{
    function getResult(){
        return $a + $b;
    }
}
class operateMinus extends operate{
    function getResult(){
        return $a - $b;
    }
}
class operateMultiplication extends operate{
    function getResult(){
        return $a * $b;
    }
}
class operateDivision extends operate{
    function getResult(){
        if($b == 0) throw new ArithmeticException;
    }
}

$operate = operateFactory::create('add');
$operate->a = 1;
$operate->b = 2;
var_dump($operate->getResult());

```