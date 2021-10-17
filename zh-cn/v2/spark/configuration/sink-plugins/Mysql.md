## Sink plugin : Mysql [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/earth-fleet-docs
* Version: 2.0.0

### Description

支持Update的方式输出数据到Mysql

### Options

| name                                         | type   | required | default value |
| -------------------------------------------- | ------ | -------- | ------------- |
| [url](#url-string)                           | string | yes      | -             |
| [user](#user-string)                         | string | yes      | -             |
| [password](#password-string)                 | string | yes      | -             |
| [save_mode](#save_mode-string)               | string | yes      | -             |
| [dbtable](#dbtable-string)                   | string | yes       | -             |
| [customUpdateStmt](#customUpdateStmt-string) | string | no       | -             |
| [duplicateIncs](#duplicateIncs-string)       | string | no       | -             |

##### url [string]

JDBC连接的URL。参考一个案例: `jdbc:mysql://localhost/dbName`

##### user [string]

用户名

##### Password [string]

用户密码

##### save_mode [string]

存储模式，添加模式`update`，在插入数据键冲突的时候进行可指定方式的数据覆盖

基本模式`overwrite`，`append`，`ignore`以及`error`。每个模式具体含义见[save-modes](http://spark.apache.org/docs/2.2.0/sql-programming-guide.html#save-modes)

##### dbtable [string]

源数据表名

##### customUpdateStmt [string]

在`save_mode`指定为`update`时配置，用于指定键冲突的更新语句模板

参考mysql的`INSERT INTO table (...) values (...) ON DUPLICATE KEY UPDATE...`的使用方式，values中使用占位符或固定值

##### duplicateIncs [string]

在`save_mode`指定为`update`时配置，指定键冲突时值更新为现有值加上原有值

### Examples

```
Mysql {
	save_mode = "update",
	truncate = true,
	url = "jdbc:mysql://192.168.1.1:3306/database",
	user= "userName",
	password = "***********",
	dbtable = "tableName",
	customUpdateStmt = "INSERT INTO table (column1, column2, created, modified, yn) values(?, ?, now(), now(), 1) ON DUPLICATE KEY UPDATE column1 = IFNULL(VALUES (column1), column1), column2 = IFNULL(VALUES (column2), column2)"
}
```

