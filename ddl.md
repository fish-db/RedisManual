### 数据库操作

```js
// Redis 默认有16个数据库

// 使用编号为0的数据库
SELECT 0

// 将foo元素移动到2号库
move foo 2

// 在当前数据库中，它的值为 NIL
GET foo

SELECT 2
GET foo // 可以在2号库拿到它的值了

// 获得当前数据库中的key的数量
DBSIZE
// O(1)
```

### Key操作

```js
// 获得符合匹配规则的key
KEYS *
// 结果可能会很多，不建议在生产环境中使用
// O(n)
  
KEYS f*
// 匹配f开头的键
  
EXISTS key1
// 判断key1是否存在：0不存在；1存在
// O(1)

type key
// 返回数据的类型
// O(1)
```


### 过期时间
```js
SET bar 'should EXPIRE'
TTL bar  // -1: means forever, never EXPIRE

EXPIRE bar 20  // bar will EXPIRE after 20s

TTL bar // -2
GET bar // NIL
```

