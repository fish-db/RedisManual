## 基本操作

对变量的用法和Python类似

- 直接使用变量而无需提前声明
- 变量有严格的类型但是语法上不必指明
- 每种类型的变量都有对应的操作，不能混用！！！



### 基本类型

#### 字符类型

```javascript
// 创建foo元素，值为fooooo，它属于字符类型
SET foo 'foooooo'

// 获得元素的值
GET foo

// 如果foo不存在，则设置
SETNX foo 'oooooooof' 

// 在字符串尾部追加字符串，返回字符串长度
APPEND foo 22

// 获得[0, 3]区间的字符
GETRANGE foo 0 3

// 同时设置多个变量
MSET k1 v1 k2 v2 k3 v3
MGET k1 k2 k3
```

#### 数值类型

```js
// 创建一个数值类型的变量
SET i 2
GET i

// 给它增加一个整数值
INCR i 3
// 给它增加一个浮点值
INCRBYFLOAT i 3.12

DECRBY i 2
DECR i
```

- 上面几个指令都是针对于整型、浮点类型的
- 针对数值类型的指令一般不能作用于字符，除非这个字符可以通过隐式类型转换转化为数值
- 针对字符的指令作用于数值时，会将数值类型隐式类型转换为字符类型

### List 列表

```js
// 创建一个列表，插入一组数据
// 每次都是从左边插入
LPUSH fish_list 1 2 3 3 4 5

// 非法操作 ，列表操作都是以L开头的，GET针对的是字符类型
GET fish_list

// 获得列表中所有的元素
LRANGE fish_list 0 -1

// 从右边插入
RPUSH fish_list 'sdf'

// 移除左边第一个元素，并获得它的值
LPOP fish_list
// 移除右边第一个元素，并获得它的值
RPOP fish_list
```

### Set 集合

数据不重复

```js
// 添加元素
SADD set01 1 3 3 32

// 获取所有元素
SMEMBERS set01

// 统计元素数量
SCARD set01
```



## Hash 哈希

```js
// 向hash表中添加一个记录
HSET players player1 'Jon Snow'

// 获得palys表中的play1字段
HGET players player1

// 多重赋值
HMSET players player2 'Aray' palyer3 'Ty'

// 获得所有的键
HKEYS players

// 获得所有的值
HVALS players
```

### 有序集合zset

或者说是无重复的List

相比于set，每个元素有一个隐藏的分值用来排序

```js
// 添加元素
ZADD zset01 00 v1 10 v2 20 v3

// 获得所有元素
ZRANGE zset01 0 -1
/*
v1
v2
v3
*/
```

