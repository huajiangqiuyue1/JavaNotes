索引是帮助MySQL高效获取数据的排好序的数据结构。

### 存储引擎

#### MyISAM

MyISAM存储引擎的索引文件和数据文件是分离的（非聚簇，即索引和数据是分开存储的）；

![image-20201021084421515](http://markdown.xiaonainiu.top/img/image-20201021084421515.png)

#### InnoDB

- InnoDB存储引擎的**表数据本身**就是按B+Tree组织的一个**索引文件**（聚簇索引）；

- 聚簇索引-叶节点包含了完整的数据记录

- 为什么InnoDB表必须有主键，并推荐使用整型的自增主键？

  InnoDB是按照B+Tree组织的一个索引结构文件，如果没有创建主键,InnoDB会选一个，或者添加一列维护。

  - 在B+Tree结构中，搜索一个数据时，如下图，比如搜索30时，它会先给15 和56比较，然后与20 49依次比较，所以此时整形的比较效率高速度快；

  ![image-20201021084458617](http://markdown.xiaonainiu.top/img/image-20201021084458617.png)

  - 如果是UUID生成的，则是一串字符串，此时不仅比较速率慢，其次索引还占用磁盘内存。

  - 如果不是自增的如下

    ![img](http://markdown.xiaonainiu.top/img/LW59U0SI$79Y71}IIDC_7MH.png)

    ![img](http://markdown.xiaonainiu.top/img/WYIHS586}ZX55%_KZ74WRSS.png)

    不是递增插入的 导致上面进行分裂 还可能在做树平衡，若递增的话 只会往右增加。

- 为什么非主键索引结构的叶子节点存储的是主键值？

  一致性和节省存储空间

### 为什么使用B+Tree索引而不使用Hash索引？

虽然Hash索引速度很快，但是它不支持范围查找，如：

```mysql
select * from t where id > 5;
```

### 为什么使用B+Tree索引而不使用B-Tree索引？

- B+Tree每行存储的节点较多，原因如下：

  B-Tree结构中是将数据存储到了节点中，因此每行存的索引就变少了（规定每行存16kb）相应的深度（阶）比B+Tree深，会造成进行IO操作过多，影响性能。

  

- 其次B+Tree中的叶子节点存在指针，由于指针的存在，在范围查找时，移动指针即可，而B-Tree不行