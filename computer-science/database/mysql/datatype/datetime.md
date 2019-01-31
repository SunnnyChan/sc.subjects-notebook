# 日期时间

## 日期格式
* YYYY-MM-DD HH:MM:SS[.fraction]
```md
date部分 对应格式中的“YYYY-MM-DD”
time部分 对应格式中的“HH:MM:SS[.fraction]”
```

## 日期类型
* [Date]
```md
对于date字段来说，它只支持date部分。
如果插入了time部分的内容，它会丢弃掉该部分的内容，并提示一个warning。
```
* [DateTime]
* [Time]
* [TimeStamp]

### TIMESTAMP 和 DATETIME
```md
两者都可用来表示YYYY-MM-DD HH:MM:SS[.fraction]类型的日期。
```
* 存储方式不一样
```md
对于跨时区的业务，TIMESTAMP更为合适。
```
* 存储的时间范围不一样
```md
timestamp：
'1970-01-01 00:00:01.000000' 到 '2038-01-19 03:14:07.999999'。

datetime：
'1000-01-01 00:00:00.000000' 到 '9999-12-31 23:59:59.999999'。
```

## 日期精度
```sql
  CREATE TABLE `t` ( 
  `id` int(11) AUTO_INCREMENT, 
  `t1` time(3), 
  `t2` timestamp(6), 
  `t3` datetime(1), 
  `t4` datetime, 
  PRIMARY KEY (`id`) 
) ENGINE=InnoDB 
```
```md
+----+--------------+----------------------------+-----------------------+---------------------+ 
| id | t1           | t2                         | t3                    | t4                  | 
+----+--------------+----------------------------+-----------------------+---------------------+ 
|  1 | 05:05:10.000 | 2013-07-04 05:05:10.000000 | 2013-07-04 05:05:10.0 | 2013-07-04 05:05:10 | 
```
## Automatic Initialization and Updating
```md
日期时间字段的自动初始化和更新：
`hiredate` timestamp NOT NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP

MySQL 5.6.5版本之前，只适用于TIMESTAMP，而且一张表中，最多允许一个TIMESTAMP字段采用该特性。
从MySQL 5.6.5开始，同时适用于TIMESTAMP和DATETIME，且不限制数量。
```

## 当前时间
* CURRENT_TIMESTAMP
* CURRENT_TIMESTAMP()
* NOW()
* LOCALTIME
* LOCALTIME()
* LOCALTIMESTAMP
* LOCALTIMESTAMP()

## 不存在的时间
```md
不存在的Date，DateTime或者TimeStamp值会被转换成各自类型的“Zero”值；
（’0000-00-00’ or ‘0000-00-00 00:00:00’）
```
