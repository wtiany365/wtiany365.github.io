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
class payFactory{
    static function create($type){
        switch ($type) {
            case 'wechat':
                $pay = new wechatPay();
                break;
            case 'alipay':
                $pay = new aliPay();
                break;
        }
        return $pay;
    }
}
class order{
    public function payBy($type){
        $pay = payFactory::create($type);
        $pay->doPay();
    }
}
$order = new order;
$order->payBy('wechat');//'wechat pay'
```