# ClickHouse时区问题

Java dao层取ClickHouse中的Data类型，用String接收结果为`2021-10-27 03:30:00`，而在DataGrip客户端中查询结果为`2021-10-27 11:30:00`

`select now();`的结果也有问题，与实际差8小时，一看确实是时区问题

目前，以下方式只能解决`select now();`的结果问题，不能解决查询表中的Data类型字段

配置->Advanced
1. use_server_time_zone: false
2. use_time_zone: Asia\Shanghai
3. clickhouse-jdbc的0.3.1版本时间返回时区有bug，在General->driver中选择clickhouse-jdbc的版本为0.2.4，或等待官方修复bug后使用新版本

使用`toString()`，结果不受时区影响