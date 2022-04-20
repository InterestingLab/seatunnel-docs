## Source plugin : Kudu [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/seatunnel-docs
* Version: 2.0.0

### Description

从kudu中获取数据

### Options

| name                        | type   | required | default value |
| --------------------------- | ------ | -------- | ------------- |
| [kudu_master](#kudu_master) | array  | yes      | -             |
| [kudu_table](#kudu_table)   | string | yes      | -             |

##### kudu_master [array]

kudu 集群地址，格式为host:port，允许指定多个host。如 [host1:7051, host2:7051]

##### kudu_table [string]

kudu table名称


### Example

```
source {
  kudu {
    kudu_master = "host1:7051,host2:7051"
    kudu_table = "event.event_table"
    result_table_name = "tmp_event_table"
  }
}

```
