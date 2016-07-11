---
title: 建造者模式
tagline: ""
last_updated: 2016-07-11 15:10
category : php
layout: post
tags : [php]
---
建造者模式

```php
<?php
abstract builder{
    abstract function addWheel();
    abstract function addSeat();
    abstract function addSteeringWheel();
}
class carBuilder extends builder{
    public function addWheel(){
        echo 'add four wheel';
    }
    public function addSeat(){
        echo 'add four seat';
    }
    public function addSteeringWheel(){
        echo 'add one steering wheel';
    }
}
class bicycleBuilder extends builder{
    public function addWheel(){
        echo 'add two wheel';
    }
    public function addSeat(){
        echo 'add one seat';
    }
    public function addSteeringWheel(){
        echo 'add one handlebar';
    }
}
class director{
    function build($builder){
        $builder->addWheel();
        $builder->addSeat();
        $builder->addSteeringWheel();
    }
}
$director = new director();
$director->build(new bicycleBuilder());//build a bicycle
```