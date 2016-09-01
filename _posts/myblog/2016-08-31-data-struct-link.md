---
title: 线性表-链式存储结构-单链表
tagline: ""
last_updated: 2016-08-31 11:13
category : data-struct
layout: post
tags : [data-struct]
---
线性表-链式存储结构-单链表

```php
class Node{
    private $data;
    private $next;
    public function __construct($data,$next = null){
        $this->data = $data;
        $this->next = $next;
    }
    public function getData(){
        return $this->data;
    }
    public function getNext(){
        return $this->next;
    }
    public function setData($data){
        $this->data = $data;
    }
    public function setNext($next){
        $this->next = $next;
    }
}
class Header{
    private $length;
    private $next;
    public function __construct($length,$next){
        $this->length = $length;
        $this->next = $next;
    }
    public function setLength($length){
        $this->length = $length;
    }
    public function getLength(){
        return $this->length;
    }
    public function getNext(){
        return $this->next;
    }
    public function setNext($next){
        $this->next = $next;
    }
}
class LinkList{
    private $header;//头指针
    public function __construct(){
        $this->header = new Header(0,null);
    }
    public function getNext(){
        $this->header->getNext();
    }
    public function setNext($next){
        $this->header->setNext($next);
    }
    public function getLength(){
        return $this->header->getLength();
    }
    //头插法
    public function headerInsert($dataList){
        $count = count($dataList);
        $prev = null;
        for($i = 0; $i < $count;$i++){
            $node = new Node($dataList[$i]);
            if(!is_null($prev)){
                $node->setNext($prev);
            }
            $this->header->setNext($node);
            $this->header->setLength($this->header->getLength() + 1);
            $prev = $node;
        }
        return $this;
    }
    //尾插法
    public function footerInsert($dataList){
        $prev = null;
        $count = count($dataList);
        for($i = 0;$i < $count;$i++){
            $node = new Node($dataList[$i]);
            if(is_null($prev)){
                $this->header->setNext($node);
            }else{
                $prev->setNext($node);
            }
            $this->header->setLength($this->header->getLength() + 1);
            $prev = $node;
        }
        return $this;
    }
    public function getElem($i){
        if($i < 1 || $i > $this->header->getLength()) return false;
        $j = 1;
        $node = $this->header->getNext();
        while($node && $j < $i){
            $node = $node->getNext();
            $j++;
        }
        return $node;
    }
    //插入
    public function insert($i,$node){
        if($i < 1 || $i > ($this->header->getLength() + 1)) return false;
        $prev = $this->getElem($i - 1);
        $node->setNext($prev->getNext());
        $prev->setNext($node);
    }
    //删除
    public function remove($i){
        if($i < 1 || $i > $this->header->getLength()) return false;
        $prev = $this->getElem($i - 1);
        $current = $prev->getNext();
        $prev->setNext($current->getNext());
    }
}
```