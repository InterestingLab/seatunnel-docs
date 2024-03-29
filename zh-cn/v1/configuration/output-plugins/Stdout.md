## Output plugin : Stdout

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/seatunnel-docs
* Version: 1.0.0

### Description

输出数据到标准输出/终端, 常用于debug, 能够很方便输出数据.

### Options

| name | type | required | default value | engine |
| --- | --- | --- | --- | --- |
| [limit](#limit-number) | number | no | 100 | batch/spark streaming |
| [format](#format-string) | string | no | plain | batch/spark streaming |
| [common-options](#common-options-string)| string | no | - | all streaming |

##### limit [number]

限制输出Row的条数，合法范围[-1, 2147483647], `-1`表示输出最多2147483647条Row

##### format [string]

输出到终端的格式，可用的`format`包括: `json`, `plain` 以及 `schema`，用于输出数据的 **Schema**

##### common options [string]

`Output` 插件通用参数，详情参照 [Output Plugin](/zh-cn/v1/configuration/output-plugin)


### Example

```
stdout {
    limit = 10
    format = "json"
}
```

> 以Json格式输出10条数据
