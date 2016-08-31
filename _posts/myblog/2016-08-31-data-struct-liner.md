---
title: 线性表和单链表
tagline: ""
last_updated: 2016-08-31 11:13
category : data-struct
layout: post
tags : [data-struct]
---
线性表

查找：直接取位置i的元素`list[i]`;时间复杂度O(1);
插入：将i之后的元素逐一后移，新元素插入i位置；时间复杂度O(n);
删除：将i之后的元素向前移动一位；时间复杂度O(n);

```php
class LinerList{
    private $length;
    private $item;
    public function __construct(){
        $this->item = array();
        $this->length = 0;
    }
    public function getElem($i){
        if($this->length == 0 || $i < 1 || $i > $this->length) return false;
        return $this->item[$i-1];
    }
    public function getIndex($value){
        $i = 1;
        while($i < $this->length && $this->getElem($i) != $value){
            $i++;
        }
        if($i <= $this->length) return $i;
        return false;
    }
    public function insert($i,$value){
        if($i < 1 || $i > ($this->length + 1)) return false;
        //i之后的元素逐一向后移动
        for($j = ($this->length - 1);$j >= $i;$j--){
            $this->item[$j+1] = $this->item[$j];
        }
        $this->item[$i-1] = $value;//插入新元素
        $this->length += 1;
        return $this;
    }
    public function remove($i){
        if($i < 1 || $i > $this->length) return false;
        for($j = ($this->length - 1);$j >= $i;$j--){
            $this->item[$j-1] = $this->item[$j];
        }
        $this->length -= 1;
        return $this;
    }
    public function isEmpty(){
        return $this->length == 0;
    }
    public function getLength(){
        return $this->length;
    }
    public function getItem(){
        return $this->item;
    }
}
```