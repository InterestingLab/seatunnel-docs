## Source plugin : Phoenix [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/waterdrop
* Version: 2.0.0

### Description

通过Phoenix读取外部数据源数据，兼容Kerberos认证

### Options

| name | type | required | default value |
| --- | --- | --- | --- |
| [zk-connect](#zk-connect-string) | string | yes | - |
| [table](#table-string) | string| yes | |
| [columns](#columns-string-list) | string | no | - |
| [tenantId](#tenant-id-string) | string | no | - |
| [predicate](#predicate-string) | string | no | - |
| [result_table_name](#result_table_name-string) | string | yes | - |


##### zk-connect [string]

连接串, 配置示例：host1:2181,host2:2181,host3:2181【/znode】

##### table [string]

目标表名

##### columns [string-list]

读取列名配置. 读取全部列设置为[], 非必须配置项，默认为[]

##### tenant-id [string]

租户ID，非必须配置项

##### predicate [string]

条件过滤串配置, 非必须配置项

##### result_table_name [string]

Waterdrop Register as spark temporary view name

`Source` 插件通用参数，详情参照 [Source Plugin](/zh-cn/v2/spark/configuration/source-plugins/)


### Example

```
  Phoenix {
    zk-connect = "host1:2181,host2:2181,host3:2181"
    table = "table22"
    result_table_name = "tmp1"
  }
```

