---
title: 装饰模式
tagline: ""
last_updated: 2016-07-09 15:04
category : php
layout: post
tags : [php]
---
装饰模式

```php
<?php
class component{
    
}
interface decorator{
    public function decorate($component);
}
class firstDecorator implements decorator{
    public function decorate($component){
        echo 'first decorator';
    }
}
class secondDecorator implements decorator{
    public function decorator($component){
        echo 'second decorator';
    }
}
$component = new component();
$firstDecorator = new firstDecorator();
$firstDecorator->decorate($component);
```