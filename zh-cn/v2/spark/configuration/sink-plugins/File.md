## Sink plugin : File [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/seatunnel-docs
* Version: 2.0.0

### Description

输出数据到文件

### Options

| name | type | required | default value |
| --- | --- | --- | --- |
| [options](#options-object) | object | no | - |
| [partition_by](#partition_by-array) | array | no | - |
| [path](#path-string) | string | yes | - |
| [path_time_format](#path_time_format-string) | string | no | yyyyMMddHHmmss |
| [save_mode](#save_mode-string) | string | no | error |
| [serializer](#serializer-string) | string | no | json |
| [common-options](#common-options-string)| string | no | - |

##### options [object]

自定义参数

##### partition_by [array]

根据所选字段对数据进行分区

##### path [string]

输出文件路径，以 **file://** 开头

##### path_time_format [string]

当`path`参数中的格式为`xxxx-${now}`时，`path_time_format`可以指定路径的时间格式，默认值为 `yyyy.MM.dd`。常用的时间格式列举如下：

| Symbol | Description |
| --- | --- |
| y | Year |
| M | Month |
| d | Day of month |
| H | Hour in day (0-23) |
| m | Minute in hour |
| s | Second in minute |

详细的时间格式语法见[Java SimpleDateFormat](https://docs.oracle.com/javase/tutorial/i18n/format/simpleDateFormat.html)。

##### save_mode [string]

存储模式，当前支持overwrite，append，ignore以及error。每个模式具体含义见[save-modes](http://spark.apache.org/docs/2.2.0/sql-programming-guide.html#save-modes)

##### serializer [string]

序列化方法，当前支持csv、json、parquet、orc和text

##### common options [string]

`Sink` 插件通用参数，详情参照 [Sink Plugin](/zh-cn/v2/spark/configuration/sink-plugins/)


### Example

```
file {
    path = "file:///var/logs"
    serializer = "text"
}
```
