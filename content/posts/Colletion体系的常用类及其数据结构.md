---
title: "Colletion体系的常用类及其数据结构"
date: 2020-04-16T00:13:51+08:00
draft: true
---
## Colletion体系
**Collection体系**：Collection是所有集合类的父类，它提供了一组约定，任何实现了该接口表示履行这个约定，它的子类各自有不同的数据结构，但功能相似，这就形成集合的体系结构。

## 不能实例化Collection
因为Collection是接口，没有任何具体的实现方法，所以无法对Collection进行实例化，Java中的各种集合类型都是对java.util包中的Collection接口的继承，实例化只能通过父类Collection的引用指向子类对象，比如：

    Collection c = new ArrayList();

## Collection体系结构图
![](/images/Collection.png)

## List
List是有序可重复的数据结构，List接口继承了Collection接口。

1. **ArrayList**
* 是集合的一种实现，实现了接口List；
* 线性数据结构，它的底层是用数组实现的，相当于**动态数组**。可以实现容量动态增长。

2. **LinkedList**
* LinkedList是基于链表实现的双向链表，即可以通过向前或向后获取元素；
* 链表的尾节点的后一个节点是链表的头结点，链表的头结点的前一个节点是链表的尾节点。


## Set
Set是无序不重复的数据结构，Set实现了Collection接口。

1. **HashSet**
* HashSet实现Set接口，由哈希表（实际上是一个HashMap实例）支持；
* 不保证顺序不变
* 不允许有重复元素
* 需要内部元素有序的可以使用LinkedHashSet
  
2. **TreeSet**
* 是一个有序的集合，提供有序的且没有重复元素的Set集合；
* 具有排序功能：自然排序或者根据提供的Comparator进行排序
* TreeSet中的元素必须实现Comparable接口并重写compareTo()方法
* 依赖TreeMap
