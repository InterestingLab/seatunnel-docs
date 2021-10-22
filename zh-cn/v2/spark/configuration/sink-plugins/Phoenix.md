## Sink plugin : Phoenix [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/seatunnel-docs
* Version: 2.0.0

### Description

输出数据到Phoenix，兼容Kerberos认证

### Options

| name | type | required | default value |
| --- | --- | --- | --- |
| [zk-connect](#zk-connect-string) | array | yes | - |
| [table](#table-string) | string | yes | - |
| [tenantId](#tenant-id-string) | string | no | - |
| [skipNormalizingIdentifier](#skipNormalizingIdentifier-boolean) | boolean | no | false |

| [skipNormalizingIdentifier](#skip-normalizing-identifier-boolean) | boolean | no | false |

##### zk-connect [string]

连接串, 配置示例：host1:2181,host2:2181,host3:2181【/znode】

##### table [string]

目标表名

##### tenant-id [string]

租户ID，非必须配置项

##### skipNormalizingIdentifier [boolean]

是否跳过规范化标识符，如果列名被双引号包围，它是按原样使用的，否则名称是大写的。非必须配置项，默认为false

##### common options [string]

`Sink` 插件通用参数，详情参照 [Sink Plugin](/zh-cn/v2/spark/configuration/sink-plugins/)

### Examples

```
  Phoenix {
    zk-connect = "host1:2181,host2:2181,host3:2181"
    table = "table22"
  }
```
