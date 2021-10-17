## Sink plugin : Hbase [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/earth-fleet-docs
* Version: 2.0.4

### Description

采用[hbase-connectors](https://github.com/apache/hbase-connectors/tree/master/spark)将数据输出到Hbase, `Hbase(>=2.1.0)`以及`Spark(>=2.0.0)`的版本兼容均依赖于`hbase-connectors`。
Apache Hbase官方文档中`hbase-connectors`也是[Apache Hbase Repos](https://hbase.apache.org/book.html#repos)的其中之一。

### Options

| name                                              | type   | required | default value |
| ------------------------------------------------- | ------ | -------- | ------------- |
| [hbase.zookeeper.quorum](#hbase.zookeeper.quorum) | string | yes      |               |
| [catalog](#catalog)                               | string | yes      |               |
| [staging_dir](#staging_dir)                       | string | yes      |               |
| [save_mode](#save_mode)                           | string | no       | append        |
| [hbase.*](#hbase.*)                               | string | no       |               |

##### hbase.zookeeper.quorum [string]

zookeeper集群的地址，格式是：`centos01:2181,centos02:2181,centos03:2181`

##### catalog [string]

通过catalog来定义hbase表的结构，hbase的表名以及它的namespace，具体哪几个columns做rowkey, column family和columns的对应关系均可以通过catalog来进行定义。

[hbase table catalog](#https://hbase.apache.org/book.html#_define_catalog)

##### stagging_dir [string]

Hdfs上的某个路径，该路径会生成需要加载到hbase的数据，加载完数据后数据文件会被删除，目录还在。


##### save_mode [string]

支持两种写模式，`overwrite`和`append`，`overwrite`代表当hbase表中若存在数据，那么将会进行truncate清空，然后再加载数据。

`append`代表不会清空hbase表原有的数据，而直接进行加载操作。

##### hbase.* [string]

用户还可以指定多个非必须参数，详细的参数列表见[Hbase支持的参数](https://hbase.apache.org/book.html#config.files).

如果不指定这些非必须参数，它们将使用官方文档给出的默认值。

##### common options [string]

`Sink` 插件通用参数，详情参照 [Sink Plugin](/zh-cn/v2/spark/configuration/sink-plugins/)


### Examples

```
 hbase {
    source_table_name = "hive_dataset"
    hbase.zookeeper.quorum = "centos01:2181,centos02:2181,centos03:2181"
    catalog = "{\"table\":{\"namespace\":\"default\", \"name\":\"customer\"},\"rowkey\":\"c_custkey\",\"columns\":{\"c_custkey\":{\"cf\":\"rowkey\", \"col\":\"c_custkey\", \"type\":\"bigint\"},\"c_name\":{\"cf\":\"info\", \"col\":\"c_name\", \"type\":\"string\"},\"c_address\":{\"cf\":\"info\", \"col\":\"c_address\", \"type\":\"string\"},\"c_city\":{\"cf\":\"info\", \"col\":\"c_city\", \"type\":\"string\"},\"c_nation\":{\"cf\":\"info\", \"col\":\"c_nation\", \"type\":\"string\"},\"c_region\":{\"cf\":\"info\", \"col\":\"c_region\", \"type\":\"string\"},\"c_phone\":{\"cf\":\"info\", \"col\":\"c_phone\", \"type\":\"string\"},\"c_mktsegment\":{\"cf\":\"info\", \"col\":\"c_mktsegment\", \"type\":\"string\"}}}"
    staging_dir = "/tmp/hbase-staging/2020.11.9/"
    save_mode = "overwrite"
}
```
Hbase的这个插件没有给用户提供创建表的功能，因为hbase表的预分区方式会和业务逻辑有关，所以运行该插件的时候需要用户自己提前创建好hbase的表以及它的预分区；对于`rowkey`的设计，catalog本身就支持了多列联合 `rowkey=”col1:col2:col3“`，但若有其他对`rowkey`的设计需求，例如：加盐，等等操作，完全可以通过解耦的方式基于`transform plugin`对`rowkey`进行修改。
