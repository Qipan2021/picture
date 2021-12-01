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
setex 【key】【seconds】【value】	    # 将值【value】关联到【key】，并将【key】的过期时间									  设为【seconds】，单位：秒。
setnx 【key】【value】				 # 只有【key】不存在时设置【key】的值
strlen 【key】					  # 返回【key】存储字符串值的长度
mset 【key value ...】			  # 同时设置一个或多个【key value】键值对
msetnx 【key value ...】			  # 同时设置一个或多个【key value】对，当且仅当所有给定 										key 都不存在
psetex【key】【milliseconds】【value】# 将值【value】关联到【key】，并将【key】的过期时间									  设为【milliseconds】，单位：毫秒。
incr 【key】						  # 将【key】中存储的数字值加一
incrby 【key】【increment】			 # 将【key】中存储的数字值加【increment】
incrbyfloat 【key】【increment】	 # 将【key】中存储的数字值加给定浮点数【increment】
decr 【key】						  # 将【key】中存储的数字值减一
decrby 【key】【increment】			 # 将【key】中存储的数字值减【increment】
decrbyfloat 【key】【increment】	 # 将【key】中存储的数字值减给定浮点数【increment】
```

## hash（散列）