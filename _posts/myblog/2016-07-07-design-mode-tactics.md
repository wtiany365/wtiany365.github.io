---
title: 策略模式
tagline: ""
last_updated: 2016-07-07 9:01
category : php
layout: post
tags : [php]
---
策略模式

```php
<?php
interface pay{
    public funciton doPay();
}
class wechatPay implements pay{
    public function doPay(){
        echo 'wechat pay';
    }
}
class aliPay implements pay{
    public function doPay(){
        echo 'ali pay';
    }
}
class order{
    public function payBy(pay $pay){
        $pay->doPay();
    }
}
$order = new order;
$order->payBy(new wechatPay());//'wechat pay'
```