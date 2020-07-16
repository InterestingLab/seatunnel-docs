## Input plugin : Elasticsearch [Static]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/waterdrop
* Version: 1.3.2

### Description

从 Elasticsearch 中读取数据

### es作为input插件tips
在waterdrop对于es的读取中,注意:!(es.configuration)[https://www.elastic.co/guide/en/elasticsearch/hadoop/6.2/configuration.html]中对我们读取es效率有帮助的配置项，用以最大化waterdrop读取es的效率，该参数为：es.input.max.docs.per.partition的值如下：分区数 = 总数据条数/es.input.max.docs.per.partition。让用户选择合适的分区数，用以处理可能数据量较大时带来的shuffle过长使得es与其他组件迁移速率低下的问题。也是通过控制读取es的分区数来加快shuffle的过程，添加说明可以使得用户更加方便高效。这一点与es的官网对于读取es的分片所应用的cpu核数(线程数)的建议有点不一样，需要实践才能知道合适的大小。并且通过测试这个参数设置的合理，读取es的效率可以提升3-10倍。

### Options

| name | type | required | default value |
| --- | --- | --- | --- |
| [hosts](#hosts-array) | array | yes | - |
| [index](#index-string) | string | yes |  |
| [es](#es-string) | string | no |  |
| [common-options](#common-options-string)| string | yes | - |


##### hosts [array]

ElasticSearch 集群地址，格式为host:port，允许指定多个host。如 \["host1:9200", "host2:9200"]。


##### index [string]

ElasticSearch index名称，支持 `*` 模糊匹配


##### es.* [string]

用户还可以指定多个非必须参数，详细的参数列表见[Elasticsearch支持的参数](https://www.elastic.co/guide/en/elasticsearch/hadoop/current/configuration.html#cfg-mapping).

如指定 `es.read.metadata` 的方式是: `es.read.metadata = true`。如果不指定这些非必须参数，它们将使用官方文档给出的默认值。
如上所述的 `es.input.max.docs.per.partition`,需要用户自行根据实际的数据量进行调整

##### common options [string]

`Input` 插件通用参数，详情参照 [Input Plugin](/zh-cn/v1/configuration/input-plugin)


### Examples

```
elasticsearch {
    hosts = ["localhost:9200"]
    index = "waterdrop-20190424"
    result_table_name = "my_dataset"
  }
```


```
elasticsearch {
    hosts = ["localhost:9200"]
    index = "waterdrop-*"
    es.read.field.include = "name, age"
    resulttable_name = "my_dataset"
  }
```

> 匹配所有以 `waterdrop-` 开头的索引， 并且仅仅读取 `name`和 `age` 两个字段。
