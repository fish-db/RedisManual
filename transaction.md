# 事务

```js
// 开启事务
MULTI
SET a1 123
SET a2 2131

// 执行事务
EXEC

// 放弃事务
DISCARD
```

### 异常

#### 冤有头，债有主

```js
MULTI
SET a2 aass2222

// 这个命令报错后，不影响前后的命令
INCRBY a2 2
SET a3 aaaaaa
EXEC
```

#### 全体连坐

```js
MULTI
SET a2 bbb

// 前后两个操作都取消了
create_an_error
SET a3 bbbb
EXEC
```

