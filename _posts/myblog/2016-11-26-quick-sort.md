---
title: 快速排序
tagline: ""
last_updated: 2016-08-31 11:13
category : algorithms
layout: post
tags : [algorithms,php]
---
快速排序算法php实现

```php
function qsort(&$array,$low,$high){
    $poivt = parten($array,$low,$high);
    if($low < $high){
        qsort($array,$low,$poivt-1);
        qsort($array,$poivt+1,$high);
    }
}
function parten(&$array,$low,$high){
    $poivtKey = $array[$low];
    while ($low < $high) {
        while ($low < $high && $array[$high] >= $poivtKey) {
            $high--;
        }

        swap($array,$low,$high);

        while ($low < $high && $array[$low] <= $poivtKey) {
            $low++;
        }
        swap($array,$low,$high);
    }

    return $low;
}
function swap(&$array,$low,$high){
    $swap = $array[$low];
    $array[$low] = $array[$high];
    $array[$high] = $swap;
}
$test = [10,30,5,2,9,90,15];
qsort($test,0,count($test)-1);
var_dump($test);exit;
```