# redis

## 1.安装（ubuntu）

### 	1.1下载

​	在官网 https://redis.io/download/下载

![image-20230106202658132](redis_img\image-20230106202658132.png)

### 1.2安装

#### 1.安装编译环境

##### 1.1更新apt

```bash
sudo apt update
```

##### 1.2apt一键安装C/C++编译器及环境

``` bash
sudo apt install build-essential
```

1.3查看版本
至此已安装完毕，我们可以通过下面的命令查询build-essential安装包相关的依赖关系：

```bash
apt-cache depends build-essential
```

![image-20230106202714956](redis_img\image-20230106202714956.png)
通过下面的命令查询gcc的版本：

```bash
gcc -v
```

![image-20230106202723764](redis_img\image-20230106202723764.png)

#### 2.安装redis

##### 	2.1下载redis放在opt目录

![image-20230106202732370](redis_img\image-20230106202732370.png)

##### 	2.2解压

```bash
tar -zxvf redis-7.0.7.tar.gz
```

##### 2.3 进入目录 redis-7.0.7

```bash
cd redis-7.0.7
```

##### 2.4 执行make命令

##### 2.5如果报错C环境

make 会报错—Jemalloc/jemalloc.h：没有那个文件

解决方案：运行make distclean

##### 2.5在redis-7.0.7目录下再次执行make命令（只是编译好）

![image-20230106202751218](redis_img\image-20230106202751218.png)

##### 2.6跳过make test 继续执行: make install

![image-20230106202913815](redis_img\image-20230106202913815.png)

#### 3.安装目录 /usr/local/bin

##### 3.1命令

**查看默认安装目录：**

**redis-benchmark:性能测试工具，可以在自己本子运行，看看自己本子性能如何**

**redis-check-aof：修复有问题的AOF文件**

**redis-check-dump：修复有问题的dump.rdb文件**

**redis-sentinel：Redis集群使用**

**redis-server：Redis服务器启动命令**

**redis-cli：客户端，操作入口**

#### 4.前台启动（不推荐 不能关闭命令窗口）

![image-20230106203028407](redis_img\image-20230106203028407.png)

#### 5.后台启动

##### 5.1备份redis.conf

拷贝一份redis.conf到其他目录

```bash
cp redis.conf /etc/redis.conf
```

##### 5.2后台启动设置daemonize no改成yes

修改redis.conf文件将里面的daemonize no 改成 yes，让服务在后台启动

##### 5.3Redis启动(在安装目录启动)

```bash
redis-server /etc/redis.conf
```

查看 ps-ef | grep redis 	![image-20230106203510863](redis_img\image-20230106203510863.png)

##### 5.4用客户端访问 

```bash
redis-cli
```

![image-20230106203730124](redis_img\image-20230106203730124.png)

```bash
redis-cli --raw #解决中文乱码
```

![image-20230108195418237](redis_img\image-20230108195418237.png)

![image-20230108195425851](redis_img\image-20230108195425851.png)

##### 5.5关闭Redis

###### 5.5.1单例关闭

```bash
redis-cli shutdown	
```

![image-20230106204104892](redis_img\image-20230106204104892.png)

###### 5.5.2或者进入终端使用shutdown关闭

![image-20230106204205019](redis_img\image-20230106204205019.png)

###### 5.5.3杀进程关闭

```
kill -9 进程号
```

![image-20230106204418670](redis_img\image-20230106204418670.png)

## 2.五大数据类型

### 2.1 Redis键（key）

常用命令

### ![image-20230107122407227](redis_img\image-20230107122407227.png)2.2字符串String

String是Redis最基本的类型，你可以理解成与Memcached一模一样的类型，一个key对应一个value。

String类型是二进制安全的。意味着Redis的string可以包含任何数据。比如jpg图片或者序列化的对象。

String类型是Redis最基本的数据类型，一个Redis中字符串value最多可以是512M

#### 2.2.1常用命令

![image-20230107222345337](redis_img\image-20230107222345337.png)

#### 2.2.2数据结构

String的数据结构为简单动态字符串(Simple Dynamic String,缩写SDS)。是可以修改的字符串，内部结构实现上类似于Java的ArrayList，采用预分配冗余空间的方式来减少内存的频繁分配.

![img](redis_img\wps2.jpg) 

如图中所示，内部为当前字符串实际分配的空间capacity一般要高于实际字符串长度len。当字符串长度小于1M时，扩容都是加倍现有的空间，如果超过1M，扩容时一次只会多扩1M的空间。需要注意的是字符串最大长度为512M。

### 2.3列表List

单键多值

Redis 列表是简单的字符串列表，按照插入顺序排序。你可以添加一个元素到列表的头部（左边）或者尾部（右边）。

它的底层实际是个双向链表，对两端的操作性能很高，通过索引下标的操作中间的节点性能会较差。

![img](redis_img\wps3.png)

#### 2.3.1常用命令

| lpush\rpush key value...                        | lpop\rpop key                             | rpoplpush key1 key2                        | lrange key start stop                 |
| :---------------------------------------------- | ----------------------------------------- | ------------------------------------------ | ------------------------------------- |
| 从左边/右边插入一个或多个值                     | 从左边/右边吐出一个值。值在键在，值亡键亡 | 从key1列表右边吐出一个值，插到key2列表左边 | 按照索引下标获得元素(从左到右)        |
| **lrange key 0 -1**                             | **lindex key index**                      | **llen key**                               | **linsert key before value newvalue** |
| 0左边第一个，-1右边第一个，（0 -1表示获取所有） | 按照索引下标获得元素(从左到右)            | 获得列表长度                               | 在value的前面插入newvalue插入值       |
| **lrem key n value**                            | **lset key index value**                  |                                            |                                       |
| 从左边删除n个value(从左到右)                    | 将列表key下标为index的值替换成value       |                                            |                                       |

#### 2.3.2数据结构

List的数据结构为快速链表quickList。

首先在列表元素较少的情况下会使用一块连续的内存存储，这个结构是ziplist，也即是压缩列表。

它将所有的元素紧挨着一起存储，分配的是一块连续的内存。

当数据量比较多的时候才会改成quicklist。

因为普通的链表需要的附加指针空间太大，会比较浪费空间。比如这个列表里存的只是int类型的数据，结构上还需要两个额外的指针prev和next。

![img](redis_img\wps1.jpg) 

Redis将链表和ziplist结合起来组成了quicklist。也就是将多个ziplist使用双向指针串起来使用。这样既满足了快速的插入删除性能，又不会出现太大的空间冗余。

### 2.4集合set

Redis set对外提供的功能与list类似是一个列表的功能，特殊之处在于set是可以**自动排重**的，当你需要存储一个列表数据，又不希望出现重复数据时，set是一个很好的选择，并且set提供了判断某个成员是否在一个set集合内的重要接口，这个也是list所不能提供的。

Redis的Set是string类型的无序集合。它底层其实是一个value为null的hash表，所以添加，删除，查找的**复杂度都是O(1)**

一个算法，随着数据的增加，执行时间的长短，如果是O(1)，数据增加，查找数据的时间不变

#### 2.4.1常用命令

| sadd key value...                                            | smembers key                         | sismember key value                                  | scard key                                |
| ------------------------------------------------------------ | ------------------------------------ | ---------------------------------------------------- | ---------------------------------------- |
| 将一个或多个 member 元素加入到集合 key 中，已经存在的 member 元素将被忽略 | 取出集合所有的值                     | 判断集合key是否含有该value值，有1，没有0             | 返回该集合的元素个数                     |
| **srem key value....**                                       | **spop key number**                  | **srandmember key n**                                | **smove source destination value**       |
| 删除集合中的某个元素                                         | 随机从该集合中吐出number个值(会删除) | 随机从该集合中取出n个值 不会从集合中删除             | 把集合中一个值从一个集合移动到另一个集合 |
| **sinter key1 key2**                                         | **sunion key1 key2**                 | **sdiff key1 key2**                                  |                                          |
| 返回两个集合的**交集**元素                                   | 返回两个集合的**并集**元素           | 返回两个集合的**差集**元素(key1中的，不包含key2中的) |                                          |

#### 2.4.2数据结构

Set数据结构是dict字典，字典是用哈希表实现的。

Java中HashSet的内部实现使用的是HashMap，只不过所有的value都指向同一个对象。Redis的set结构也是一样，它的内部也使用hash结构，所有的value都指向同一个内部值。

### 2.5哈希hash

Redis hash 是一个键值对集合。

Redis hash是一个string类型的**field**和**value**的映射表，hash特别适合用于存储对象。

类似Java里面的Map<String,Object>

用户ID为查找的key，存储的value用户对象包含姓名，年龄，生日等信息，如果用普通的key/value结构来存储

主要有以下2种存储方式：

![img](redis_img\wps7.png)

每次修改用户的某个属性需要，先反序列化改好后再序列化回去。开销较大。

![img](redis_img\wps8.png)

​											用户ID数据冗余

![image-20230108185409310](redis_img\image-20230108185409310.png)


通过 key(用户ID) + field(属性标签) 就可以操作对应属性数据了，既不需要重复存储数据，也不会带来序列化和并发修改控制的问题

#### 2.5.1常用命令

| hset key field value          | hget key field            | hmset key field value ....                   | hexists key field                                            |
| ----------------------------- | ------------------------- | -------------------------------------------- | ------------------------------------------------------------ |
| 给key集合中的field键赋值value | 从key1集合field取出 value | 批量设置hash的值                             | 查看哈希表key 中，给定域 field 是否存在                      |
| **hkeys key**                 | **hvals key**             | **hincrby key field increment**              | **hsetnx key field value**                                   |
| 列出该hash集合的所有field     | 列出该hash集合的所有value | 为哈希表 key 中的域 field 的值加上增量 1  -1 | 将哈希表 key 中的域 field 的值设置为 value ，当且仅当域 field 不存在 . |

#### 2.5.2数据结构

Hash类型对应的数据结构是两种：ziplist（压缩列表），hashtable（哈希表）。当field-value长度较短且个数较少时，使用ziplist，否则使用hashtable。

### 2.6 有序集合zset

Redis有序集合zset与普通集合set非常相似，是一个**没有重复元素**的字符串集合。

不同之处是有序集合的每个成员都关联了一个**评分（score**）,这个评分（score）被用来按照从最低分到最高分的方式排序集合中的成员。**集合的成员是唯一的，但是评分可以是重复了** 。

因为元素是有序的, 所以你也可以很快的根据评分（score）或者次序（position）来获取一个范围的元素。

访问有序集合的中间元素也是非常快的,因此你能够使用有序集合作为一个没有重复成员的智能列表。

#### 2.6.1 常用命令

| zadd key  score value1 ...                                   | zrange key start stop [WITHSCORES]                           | zrangebyscore key minmax [withscores] [limit offset count]   |
| ------------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 将一个或多个 member 元素及其 score 值加入到有序集 key 当中   | 返回有序集key中，下标在start stop之间的元素带WITHSCORES，可以让分数一起和值返回到结果集 | 返回有序集 key 中，所有 score 值介于 min 和 max 之间(包括等于 min 或 max )的成员。有序集成员按 score 值递增(从小到大)次序排列 |
| **zrevrangebyscore key maxmin [withscores] [limit offset count]** | **zincrby key increment value**                              | **zrem  key value**                                          |
| 返回有序集 key 中，所有 score 值介于 min 和 max 之间(包括等于 min 或 max )的成员。有序集成员按 score 值递增(从大到小)次序排列 | 为元素的score加上增量                                        | 删除该集合下，指定值的元素                                   |
| **zcount key min max**                                       | **zrank key value**                                          |                                                              |
| 统计该集合，分数区间内的元素个数                             | 返回该值在集合中的排名，从0开始。                            |                                                              |

#### 2.6.2数据结构

SortedSet(zset)是Redis提供的一个非常特别的数据结构，一方面它等价于Java的数据结构Map<String, Double>，可以给每一个元素value赋予一个权重score，另一方面它又类似于TreeSet，内部的元素会按照权重score进行排序，可以得到每个元素的名次，还可以通过score的范围来获取元素的列表。

zset底层使用了两个数据结构

（1）hash，hash的作用就是关联元素value和权重score，保障元素value的唯一性，可以通过元素value找到相应的score值。

（2）跳跃表，跳跃表的目的在于给元素value排序，根据score的范围获取元素列表。

#### 2.6.3跳跃表 

1、简介

​	有序集合在生活中比较常见，例如根据成绩对学生排名，根据得分对玩家排名等。对于有序集合的底层实现，可以用数组、平衡树、链表等。数组不便元素的插入、删除；平衡树或红黑树虽然效率高但结构复杂；链表查询需要遍历所有效率低。Redis采用的是跳跃表。跳跃表效率堪比红黑树，实现远比红黑树简单。

2、实例

​	对比有序链表和跳跃表，从链表中查询出51

（1） 有序链表

![img](redis_img\wps9.jpg) 

要查找值为51的元素，需要从第一个元素开始依次查找、比较才能找到。共需要6次比较。

（2） 跳跃表（随机建立索引）

![image-20230108222719828](A:\study\学习笔记\redis_img\image-20230108222719828.png)

第一层 每隔一个建立索引

第二层 每隔两个建立索引

从第2层开始，1节点比51节点小，向后比较。

41节点比51节点小，继续向后比较，后面就是NULL了，所以从41节点向下到第1层

在第1层，41节点比51节点小，继续向后，61节点比51节点大，所以从41向下

在第0层，51节点为要查找的节点，节点被找到，共查找4次。

从此可以看出跳跃表比有序链表效率要高

## 3.Redis配置文件

### 3.1untis单位

配置大小单位,开头定义了一些基本的度量单位，只支持bytes，不支持bit

大小写不敏感

![img](A:\study\学习笔记\redis_img\wps1.png) 

### 4.2INCLUDES包含

![img](A:\study\学习笔记\redis_img\wps2.png) 

类似jsp中的include，多实例的情况可以把公用的配置文件提取出来

### 4.3网络相关配置

#### 4.3.1bind

默认情况bind=127.0.0.1只能接受本机的访问请求

不写的情况下，无限制接受任何ip地址的访问

生产环境肯定要写你应用服务器的地址；服务器是需要远程访问的，所以需要将其注释掉

如果开启了protected-mode，那么在没有设定bind ip且没有设密码的情况下，Redis只允许接受本机的响应

![img](A:\study\学习笔记\redis_img\wps3-16732316723011.png) 

保存配置，停止服务，重启启动查看进程，不再是本机访问了。

![img](A:\study\学习笔记\redis_img\wps4-16732316723012.png) 

#### 4.3.2protected-mode

将本机访问保护模式设置no

![img](A:\study\学习笔记\redis_img\wps5-16732316723013.png) 

#### 4.3.3.Port

端口号，默认 6379

![img](A:\study\学习笔记\redis_img\wps6-16732316723014.png) 

#### 4.3.4.tcp-backlog

设置tcp的backlog，backlog其实是一个连接队列，backlog队列总和=未完成三次握手队列 + 已经完成三次握手队列。

在高并发环境下你需要一个高backlog值来避免慢客户端连接问题。

注意Linux内核会将这个值减小到/proc/sys/net/core/somaxconn的值（128），所以需要确认增大/proc/sys/net/core/somaxconn和/proc/sys/net/ipv4/tcp_max_syn_backlog（128）两个值来达到想要的效果

![img](A:\study\学习笔记\redis_img\wps7-16732316723015.png) 

#### 4.3.5.timeout

一个空闲的客户端维持多少秒会关闭，0表示关闭该功能。即永不关闭。

![img](A:\study\学习笔记\redis_img\wps8-16732316723016.png) 

#### 4.3.6.tcp-keepalive

对访问客户端的一种心跳检测，每个n秒检测一次。

单位为秒，如果设置为0，则不会进行Keepalive检测，建议设置成60 

![img](A:\study\学习笔记\redis_img\wps9.png) 

### 4.4GENERAL通用

#### 4.4.1 daemonize

是否为后台进程，设置为yes

守护进程，后台启动

![img](A:\study\学习笔记\redis_img\wps10.png) 

#### 4.4.2 pidfile

存放pid文件的位置，每个实例会产生一个不同的pid文件

![img](A:\study\学习笔记\redis_img\wps11.png) 

#### 4.4.3 loglevel

指定日志记录级别，Redis总共支持四个级别：debug、verbose、notice、warning，默认为***\*notice\****

四个级别根据使用阶段来选择，生产环境选择notice 或者warning

![img](A:\study\学习笔记\redis_img\wps12.png) 

#### 4.4.4 logfile

日志文件名称

![img](A:\study\学习笔记\redis_img\wps13.png) 

#### 4.4.5. databases 16 

设定库的数量 默认16，默认数据库为0，可以使用SELECT <dbid>命令在连接上指定数据库id

![img](A:\study\学习笔记\redis_img\wps14.png) 

 

### 4.5 SECURITY安全

***\*设置密码\****

![img](A:\study\学习笔记\redis_img\wps15.png) 

访问密码的查看、设置和取消

在命令中设置密码，只是临时的。重启redis服务器，密码就还原了。

永久设置，需要再配置文件中进行设置。

![img](A:\study\学习笔记\redis_img\wps16.png) 

### 4.6 LIMITS限制

#### 4.6.1.maxclients

Ø 设置redis同时可以与多少个客户端进行连接。

Ø 默认情况下为10000个客户端。

Ø 如果达到了此限制，redis则会拒绝新的连接请求，并且向这些连接请求方发出“max number of clients reached”以作回应。

![img](A:\study\学习笔记\redis_img\wps17.png) 

#### 4.6.2maxmemory

Ø 建议***\*必须设置\****，否则，将内存占满，造成服务器宕机

Ø 设置redis可以使用的内存量。一旦到达内存使用上限，redis将会试图移除内部数据，移除规则可以通过maxmemory-policy来指定。

Ø 如果redis无法根据移除规则来移除内存中的数据，或者设置了“不允许移除”，那么redis则会针对那些需要申请内存的指令返回错误信息，比如SET、LPUSH等。

Ø 但是对于无内存申请的指令，仍然会正常响应，比如GET等。如果你的redis是主redis（说明你的redis有从redis），那么在设置内存使用上限时，需要在系统中留出一些内存空间给同步队列缓存，只有在你设置的是“不移除”的情况下，才不用考虑这个因素。

![img](A:\study\学习笔记\redis_img\wps18.png) 

#### 4.6.3.maxmemory-policy

Ø volatile-lru：使用LRU算法移除key，只对设置了过期时间的键；（最近最少使用）

Ø allkeys-lru：在所有集合key中，使用LRU算法移除key

Ø volatile-random：在过期集合中移除随机的key，只对设置了过期时间的键

Ø allkeys-random：在所有集合key中，移除随机的key

Ø volatile-ttl：移除那些TTL值最小的key，即那些最近要过期的key

Ø noeviction：不进行移除。针对写操作，只是返回错误信息

![img](A:\study\学习笔记\redis_img\wps19.png) 

#### 4.6.4axmemory-samples

Ø 设置样本数量，LRU算法和最小TTL算法都并非是精确的算法，而是估算值，所以你可以设置样本的大小，redis默认会检查这么多个key并选择其中LRU的那个。

Ø 一般设置3到7的数字，数值越小样本越不准确，但性能消耗越小。

![img](redis_img\wps20.png) 

## 4.订阅

1、客户端可以订阅频道如下图

![image-20230109112207691](A:\study\学习笔记\redis_img\image-20230109112207691.png)

2、当给这个频道发布消息后，消息就会发送给订阅的客户端

![image-20230109112210218](A:\study\学习笔记\redis_img\image-20230109112210218.png)

### 4.1订阅

```bash
subscribe chennl
```

![image-20230109112435763](A:\study\学习笔记\redis_img\image-20230109112435763.png)

### 4.2发布消息

```bash
publish chennl 消息
```

![image-20230109112635186](A:\study\学习笔记\redis_img\image-20230109112635186.png)

### 4.3实时收到

![image-20230109112642373](A:\study\学习笔记\redis_img\image-20230109112642373.png)

发布的消息没有持久化，如果在订阅的客户端收不到hello，只能收到订阅后发布的消息

## 5.Redis数据类型

### 5.1Bitmaps

### 5.1.1简介

现代计算机用二进制（位） 作为信息的基础单位， 1个字节等于8位， 例如“abc”字符串是由3个字节组成， 但实际在计算机存储时将其用二进制表示， “abc”分别对应的ASCII码分别是97、 98、 99， 对应的二进制分别是01100001、 01100010和01100011，如下图

![img](A:\study\学习笔记\redis_img\wps23.jpg) 

合理地使用操作位能够有效地提高内存使用率和开发效率。

​	Redis提供了Bitmaps这个“数据类型”可以实现对位的操作：

（1） Bitmaps本身不是一种数据类型， 实际上它就是字符串（key-value） ， 但是它可以对字符串的位进行操作。

（2） Bitmaps单独提供了一套命令， 所以在Redis中使用Bitmaps和使用字符串的方法不太相同。 可以把Bitmaps想象成一个以位为单位的数组， 数组的每个单元只能存储0和1， 数组的下标在Bitmaps中叫做偏移量。

![img](A:\study\学习笔记\redis_img\wps24.jpg) 
