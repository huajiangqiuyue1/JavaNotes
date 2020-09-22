# 漫画：什么是B-树？

![img](http://markdown.xiaonainiu.top/img/168232b112e3cafd)





![img](http://markdown.xiaonainiu.top/img/168232b112fb1628)





![img](http://markdown.xiaonainiu.top/img/168232b11318c5d4)





![img](http://markdown.xiaonainiu.top/img/168232b1128d012e)





————————————





![img](http://markdown.xiaonainiu.top/img/168232b114f8819c)





![img](http://markdown.xiaonainiu.top/img/168232b1145a551f)





![img](http://markdown.xiaonainiu.top/img/168232b12e859001)





![img](http://markdown.xiaonainiu.top/img/168232b130a34232)





![img](http://markdown.xiaonainiu.top/img/168232b12ecdc411)





![img](http://markdown.xiaonainiu.top/img/168232b13a49fa47)





![img](http://markdown.xiaonainiu.top/img/168232b1341bb1fb)





![img](http://markdown.xiaonainiu.top/img/168232b14cbca364)





![img](http://markdown.xiaonainiu.top/img/168232b14e154a13)





————————————





![img](http://markdown.xiaonainiu.top/img/168232b15067d88a)





![img](http://markdown.xiaonainiu.top/img/168232b15245db58)





![img](http://markdown.xiaonainiu.top/img/168232b152df328c)





![img](http://markdown.xiaonainiu.top/img/168232b171b42864)





![img](http://markdown.xiaonainiu.top/img/168232b1748c4597)





![img](http://markdown.xiaonainiu.top/img/168232b1756d0c10)





![img](http://markdown.xiaonainiu.top/img/168232b184a201db)





![img](http://markdown.xiaonainiu.top/img/168232b18c28e01c)





![img](http://markdown.xiaonainiu.top/img/168232b193207a94)





![img](http://markdown.xiaonainiu.top/img/168232b195001de4)





![img](http://markdown.xiaonainiu.top/img/168232b196b835b1)





![img](http://markdown.xiaonainiu.top/img/168232b1a5d58f0c)





![img](http://markdown.xiaonainiu.top/img/168232b1abfdfc89)





![img](http://markdown.xiaonainiu.top/img/168232b1ade5fc24)





二叉查找树的结构：



![img](http://markdown.xiaonainiu.top/img/168232b1b26bf2e8)





第1次磁盘IO：





![img](http://markdown.xiaonainiu.top/img/168232b1bc8f309b)





第2次磁盘IO：





![img](http://markdown.xiaonainiu.top/img/168232b1c828bb63)





第3次磁盘IO：





![img](http://markdown.xiaonainiu.top/img/168232b1cd0ac5f1)





第4次磁盘IO：



![img](http://markdown.xiaonainiu.top/img/168232b1cdc4983f)





![img](http://markdown.xiaonainiu.top/img/168232b1cf06b36f)





![img](http://markdown.xiaonainiu.top/img/168232b1d2bbfb75)





![img](http://markdown.xiaonainiu.top/img/168232b1d6649627)





![img](http://markdown.xiaonainiu.top/img/168232b1e51dbcf6)

下面来具体介绍一下B-树（Balance Tree），一个m阶的B树具有如下几个特征：



![image-20200922205720555](F:/Typora/Typora/upload/image-20200922205720555.png)

上图为3阶梯B树（阶数：（Order）阶定义为一个节点的子节点数目的最大值。（自带最大值属性））

至多有3颗子树，至多有2个关键字

1.根结点至少有两个子女。



2.每个中间节点都包含k-1个元素和k个孩子，其中 m/2 <= k <= m



3.每一个叶子节点都包含k-1个元素，其中 m/2 <= k <= m



4.所有的叶子结点都位于同一层。



5.每个节点中的元素从小到大排列，节点当中k-1个元素正好是k个孩子包含的元素的值域分划。





![img](http://markdown.xiaonainiu.top/img/168232b1ea6b615c)





![img](http://markdown.xiaonainiu.top/img/168232b1eab1116e)







![img](http://markdown.xiaonainiu.top/img/168232b1eb401c01)





![img](http://markdown.xiaonainiu.top/img/168232b1ec199d2f)





![img](http://markdown.xiaonainiu.top/img/168232b1f3d365da)





![img](http://markdown.xiaonainiu.top/img/168232b2001c6b90)





![img](http://markdown.xiaonainiu.top/img/168232b203a7f6f2)





第1次磁盘IO：







![img](http://markdown.xiaonainiu.top/img/168232b2028426a1)





在内存中定位（和9比较）：





![img](http://markdown.xiaonainiu.top/img/168232b20712252c)





第2次磁盘IO：





![img](http://markdown.xiaonainiu.top/img/168232b21ab39190)





在内存中定位（和2，6比较）：







![img](http://markdown.xiaonainiu.top/img/168232b21f1f6280)





第3次磁盘IO：





![img](http://markdown.xiaonainiu.top/img/168232b2210be1d5)





在内存中定位（和3，5比较）：





![img](http://markdown.xiaonainiu.top/img/168232b2268e1ef2)





![img](http://markdown.xiaonainiu.top/img/168232b222b71c31)





![img](http://markdown.xiaonainiu.top/img/168232b23783a7ec)





![img](http://markdown.xiaonainiu.top/img/168232b22b83bd29)





![img](http://markdown.xiaonainiu.top/img/168232b24568925a)





![img](http://markdown.xiaonainiu.top/img/168232b23cfbaff3)





自顶向下查找4的节点位置，发现4应当插入到节点元素3，5之间。



![img](http://markdown.xiaonainiu.top/img/168232b255827ba3)





节点3，5已经是两元素节点，无法再增加。父亲节点 2， 6 也是两元素节点，也无法再增加。根节点9是单元素节点，可以升级为两元素节点。于是**拆分**节点3，5与节点2，6，让根节点9升级为两元素节点4，9。节点6独立为根节点的第二个孩子。



![img](http://markdown.xiaonainiu.top/img/168232b26e7b69d1)







![img](http://markdown.xiaonainiu.top/img/168232b27634916b)





![img](http://markdown.xiaonainiu.top/img/168232b27df23411)





![img](http://markdown.xiaonainiu.top/img/168232b27eddceca)





自顶向下查找元素11的节点位置。





![img](http://markdown.xiaonainiu.top/img/168232b28771232f)





删除11后，节点12只有一个孩子，不符合B树规范。因此找出12,13,15三个节点的中位数13，取代节点12，而节点12自身下移成为第一个孩子。（这个过程称为**左旋**）





![img](http://markdown.xiaonainiu.top/img/168232b28e96f94d)





![img](http://markdown.xiaonainiu.top/img/168232b295c46fe3)





![img](http://markdown.xiaonainiu.top/img/168232b299dbe7d1)





![img](http://markdown.xiaonainiu.top/img/168232b2aa8e105f)





![img](http://markdown.xiaonainiu.top/img/168232b2ae791779)





![img](http://markdown.xiaonainiu.top/img/168232b2b25747e1)