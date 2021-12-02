# Redis命令

## key（键）

```bash
del 【key】						#【key】存在时删除【key】
exists 【key】					# 判断【key】是否存在
expire 【key】【seconds】		   # 给【key】设置过期时间，单位：秒
pexpire 【key】【milliSeconds】	   # 给【key】设置过期时间，单位：毫秒
keys 【pattern】					# 查找给定符合给定模式【pattern】的【key】
move 【key】【db】				   # 将当前数据库的【key】移动到指定数据库【db】中
persist 【key】					# 移除【key】的过期时间
pttl 【key】						# 返回【key】的剩余过期时间，单位：毫秒
ttl 【key】						# 返回【key】的剩余过期时间，单位：秒
rename 【key】【newKey】		   # 修改【key】的名称
renamenx 【key】【newKey】		   # 当【newKey】不存在时，将【key】改名为【newKey】
type 【key】						# 返回【key】存储值的类型
```

## connection（连接）

```bash
auth 【password】 				# 验证密码是否正确
echo 【message】					# 打印字符串
ping							 # 查看服务是否运行
quit							 # 关闭当前连接
select 【index】					# 切换到指定数据库
```

## server（服务器）

```bash
bgrewriteaof 					 # 异步执行一个AOF 文件重写操作
bgsave							 # 在后台异步保存当前数据库的数据到磁盘
client kill 【ip:port】			# 关闭客户端连接
client list						 # 获取服务器客户端连接列表
client getname					 # 获取连接名称
client pause 【timeout】			# 阻塞客户端命令一段时间，单位：毫秒
client setname 【connection-name】# 设置当前连接名称
cluster slots					 # 获取集群节点的映射数组
command							 # 获取Redis 命令详情数组
command count 					 # 获取Redis 命令总数
command getKeys					 # 获取给定命令的所有键
time							 # 返回当前服务器时间
command info 【command-name ...】 # 获取指定Redis 命令描述的数组，例如：set
config get 【parameter】			# 获取指定配置参数的值
config rewrite 					 # 对启动Redis 服务器所指定的redis.conf 进行改写
config set 【parameter】【value】 # 修改Redis 配置参数，无需重启
config resetstart				 # 重置info 命令中的某些统计数据
dbsize							 # 返回当前数据库的key 数量
debug setfault					 # 让Redis 服务器崩溃
flushall						 # 删除所有数据库中的所有key
flushdb							 # 删除当前数据库中的都有key
info 【section】					# 获取Redis 服务器中的各种信息和统计数值
lastsave 						 # 返回最近一次Redis 成功将数据保存在磁盘上的时间
monitor							 # 实时打印出Redis 服务器接收到的命令（调试）
role							 # 返回主从实例所属角色
save							 # 同步保存数据到硬盘
shutdown 【nosave】【save】		  # 异步保存数据到硬盘，并关闭服务器
slaveof 【host】【port】		  # 将当前服务器转变为指定服务器的从属服务器
```

## string（字符串）

```bash
set 【key】【value】				  # 设置指定【key】的值
get 【key】						   # 获取指定【key】的值
getrange 【key】【start】【end】	    # 返回【key】中字符串值的子字符串
getset 【key】【value】 			 # 将给定【key】的值设置为【value】，并返回【key]旧值
mget 【key ...]					   # 获取所有（一个或多个）给定【key】的值
setex 【key】【seconds】【value】	    # 将值【value】关联到【key】，并将【key】的过期时间设为 												 【seconds】，单位：秒。
setnx 【key】【value】				 # 只有【key】不存在时设置【key】的值
strlen 【key】					  # 返回【key】存储字符串值的长度
mset 【key value ...】			  # 同时设置一个或多个【key value】键值对
msetnx 【key value ...】			  # 同时设置一个或多个【key value】对，当且仅当所有给定key 都不存在
psetex【key】【milliseconds】【value】# 将值【value】关联到【key】，并将【key】的过期时间设为												 【milliseconds】，单位：毫秒。
incr 【key】						  # 将【key】中存储的数字值加一
incrby 【key】【increment】			 # 将【key】中存储的数字值加【increment】
incrbyfloat 【key】【increment】	 # 将【key】中存储的数字值加给定浮点数【increment】
decr 【key】						  # 将【key】中存储的数字值减一
decrby 【key】【increment】			 # 将【key】中存储的数字值减【increment】
decrbyfloat 【key】【increment】	 # 将【key】中存储的数字值减给定浮点数【increment】
```

## hash（散列）

```bash
hdel 【key】【field ...】				# 删除一个或多hash 字段
hexists 【key】【field】				# 判断指定字段在hash 中是否存在
hget 【key】【field】					# 获取存储在hash 中指定字段的值
hgetall 【key】						 # 获取在hash 中指定【key】的所有字段和值
hincrby 【key】【field】【increment】	   # 为hash key 中指定字段数字值加【increment】
hincrfloat 【key】【field】【increment】 # 为hash key 中指定字段数字值给定浮点数												【increment】
hkeys 【key】							 # 获取hash 中的所有字段
hlen 【key】							 # 获取hash 中字段数量
hmget 【key】【field ...】				# 获取所有给定字段的值
hmset 【key】【field value ...】		# 同时设置多个【field value】到hash 中
hset 【key】【field value】				# 将hash 中的字段【field】的值设为【value】
hsetnx 【key】【field value】			# 当字段【field】不存在，设置hash 字段的值
hvals key							  # 获取hash 中所有值
HSCAN key cursor [MATCH pattern] [COUNT count] # 迭代哈希表中的键值对。
```

## list（列表）

```bash
lindex 【key】【index】					# 通过索引获取列表中的元素
linsert【key】BEFORE|AFTER【pivot】【value】# 将值 value 插入到列表 key 当中，位于值 												pivot 之前或之后。
llen 【key】							 # 获取列表长度
lpop 【key】							 # 移出并获取列表的第一个元素
lpush 【key】【value ...】				# 将一个或多个值插入到列表头部
lpushx 【key】【value】					# 将一个值插入到已经存在的列表头部
lrange 【key】【start】【end】		   # 获取列表指定范围内的元素
lrem 【key】【count】【value】		   # 根据参数 COUNT 的值，移除列表中与参数 VALUE 										   相等的元素。
	count > 0 : 从表头开始向表尾搜索，移除与 VALUE 相等的元素，数量为 COUNT 。
	count < 0 : 从表尾开始向表头搜索，移除与 VALUE 相等的元素，数量为 COUNT 的绝对值。
	count = 0 : 移除表中所有与 VALUE 相等的值。
lset 【key】【index】【value】		  # 通过索引来设置元素的值
ltrim key start stop				  # 对一个列表进行修剪(trim)，就是说，让列表只保留指										   定区间内的元素，不在指定区间之内的元素都将被删除
rpop 【key】							 # 移除列表的最后一个元素
rpush 【key】【value ...】				# 将一个或多个值插入到列表最后
rpushx 【key】【value】					# 将一个值插入到已经存在的列表最后
```

## set（集合）

```bash
sadd 【key】【member ...】				# 向集合添加一个或多个元素
scard 【key】							 # 获取集合成员数
sdiff 【key】【key1 ...]				# 返回第一个集合和其他集合的差异
sinter 【key ...】					 # 返回给定所有集合的交集
sinterstore 【destination】【key ...】	# 返回给定所有集合的交集并存储在 destination 中
sismember 【key】【member】 			# 返回【member】元素在集合中是否存在
smembers 【key】						 # 返回集合中所有元素
smove 【key1】【key2】[member]			# 将【member】元素从集合【key1】移动到【key2】
spop 【key】							 # 移除并返回集合中一个随机元素
srem 【key】【member ...】				# 移除集合中一个或多个元素
sunion 【key】【key1 ...】				# 返回所有集合的并集
SSCAN key cursor [MATCH pattern] [COUNT count] # 迭代集合中的元素
```

## sorted set（有序集合）

```bash
zadd 【key】【score】【member ...】	    	# 向集合添加一个或多个元素，或更新已存在成员分数
zcard 【key】							   	   # 获取有序集合的成员数
zcount 【key】【min】【max】					# 计算有序集合中指定字典区间分数的成员数
zincrby 【key】【increment】【member】		# 有序集合对指定成员的分数加上增量【increment】
zlexcount 【key】【min】【max】				# 有序集合计算指定字典区间成员数量
zrange 【key】【start】【stop】WITHSCORES 	# 通过索引返回集合指定区间成员，按分数从低到高排序
zrank 【key】【member】					 	 # 返回有序集合中指定成员的索引
zrem 【key】【member ...】				 	 # 移除有序集合中一个或多个元素
zremrangebylex 【key】【min】【max】			# 移除有序集合中给定字典区间的所有成员
zremrangebyrank 【key】【start】【stop】  	# 移除有序集合中给定排名区间的所有成员
zremrangebyscore 【key】【min】【max】		# 移除有序集合中给定的分数区间的所有成员
zrevrange 【key】【start】【stop】WITHSCORES  # 返回有序集合中指定区间元素，通过索引，分数从高到低
zrevrangebyscore 【key】【min】【max】WITHSCORES # 返回有序集中指定分数区间内的成员，分数从高到低排序
zrevrank 【key】【member】					 # 返回有序集合指定成员的索引，按分数从高到底排序
zscore 【key】【member】					 # 返回有序集合中成员的分数值
ZSCAN key cursor [MATCH pattern] [COUNT count] # 迭代有序集合中的元素（包括元素成员和元素分值）
```

## hyperLogLog（基数统计）

```bash
pfadd 【key】【elemnet ...】			# 添加指定的一个或多个元素到 HyperLogLog 中
pfcount 【key ...】					 # 返回给定 HyperLogLog 的基数值，如果多个则返回基数估值之和
pfmerge destkey [sourcekey ...]		   # 将多个 HyperLogLog 合并为一个 HyperLogLog
```

## Geospatial（地理空间）

```bash
geoadd 【key】[longitude latitude member ...] 		# 添加一个或多个地理空间位置到sorted set
geodist 【key】【member1】【member2】【unit】			# 获取两个地理空间的距离，unit：m 表示单位为米；													   km 表示单位为千米；mi 表示单位为英里；       													   ft 表示单位为英尺。
geohash 【key】【member ...】						  # 返回一个或多个地理空间字符串
geopos 【key】【member ...】						  # 返回地理空间的经纬度
GEORADIUS key longitude latitude radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count] [ASC|DESC] [STORE key] [STOREDIST key]
# 看文档，查询指定半径内所有地理空间元素的集合
GEORADIUSBYMEMBER key member radius m|km|ft|mi [WITHCOORD] [WITHDIST] [WITHHASH] [COUNT count]
# 看文档，查询指定半径匹配到最大距离的一个地理空间元素
```

## Transaction（事务）

```bash
disard					# 取消事务
exec					# 执行事务
multi					# 开启事务
unwatch 				# 取消watch 对所有key 的监视
watch 【key ...】		   # 监听一个或多个key，有改动，事务被打断
```

## Pub/Sub（发布订阅）

```bash
psubscribe 【pattern ...】 					# 订阅一个或多个符合给定模式的频道
pubsub subcommand 【argument ...】			# 查看订阅与发布系统状态，看文档
publish 【channel】【message】				   # 将信息发送到指定频道
punsubscribe 【parttern ...】					# 退订一个或多个符合给定模式的频道
subscribe 【channel ...】						# 订阅一个或多个频道的信息
ubsubscribe 【channel ...】					# 退订给定的频道
```

## stream（消息队列）



## 数据类型的区别

| 类型       | 简介                                                   | 特性                                                         | 场景                                                         |
| ---------- | ------------------------------------------------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| string     | 二进制安全                                             | 可以包含任何数据,比如jpg图片或者序列化的对象,<br>一个键最大能存储512M | --                                                           |
| hash       | 键值对集合,即编程语言中的Map类型                       | 适合存储对象,并且可以像数据库中update一个属性<br>一样只修改某一项属性值 | 存储、读取、修改用户属性                                     |
| list       | 链表(双向链表)                                         | 增删快,提供了操作某一段元素的API                             | 1,最新消息排行等功能<br/>(比如朋友圈的时间线) <br/>2,消息队列 |
| set        | 哈希表实现,元素不重复                                  | 1、添加、删除,查找的复杂度都是O(1) <br>2、为集合提供了求交集、并集、差集等操作 | 1、共同好友 <br>2、利用唯一性,统计访问网站的所有独立ip <br>3、好友推荐时,根据tag求交集,大于某个阈值就可以推荐 |
| sorted set | 将Set中的元素增加一个权重参数score,元素按score有序排列 | 数据插入集合时,已经进行天然排序                              | 1、排行榜 <br>2、带权重的消息队列                            |

