## Sink plugin : Email [Spark]

* Author: InterestingLab
* Homepage: https://interestinglab.github.io/seatunnel-docs
* Version: 2.0.0

### Description

支持数据通过邮件附件方式输出，附件是支持excel打开的xlsx格式，可用于将任务统计结果通过邮件附件的方式告知。

### Options

| name                                         | type   | required | default value |
| -------------------------------------------- | ------ | -------- | ------------- |
| [subject](#subject-string)                   | string | yes      | -             |
| [from](#from-string)                         | string | yes      | -             |
| [to](#to-string)                             | string | yes      | -             |
| [bodyText](#bodyText-string)                 | string | no       | -             |
| [bodyHtml](#bodyHtml-string)                 | string | no       | -             |
| [cc](#cc-string)                             | string | no       | -             |
| [bcc](#bcc-string)                           | string | no       | -             |
| [host](#host-string)                         | string | yes      | -             |
| [port](#port-string)                         | string | yes      | -             |
| [password](#password-string)                 | string | yes      | -             |
| [limit](#password-string)                    | string | no       | 100000           |

##### subject [string]

邮件主题

##### from [string]

邮件发件人

##### to [string]

邮件接受人，多个接受人逗号分隔

##### bodyText [string]

邮件内容，文本格式

##### bodyHtml [string]

邮件内容，超文本内容

##### cc [string]

邮件抄送人，多个抄送人逗号分隔

##### bcc [string]

邮件密送人，多个密送人逗号分隔

##### host [string]

邮件服务器地址，例如：stmp.exmail.qq.com

##### port [string]

邮件服务器端口  例如：25

##### password [string]

邮件发送人密码，用户名就是from指定的发件人

##### limit [string]

数据条数限制，默认100000条

### Examples

```
Email {
	subject = "报表统计数据",
	from = "xxxx@qq.com",
	to = "xxxxx1@qq.com,xxxxx2@qq.com",
    cc = "xxxxx3@qq.com,xxxxx4@qq.com",
    bcc = "xxxxx5@qq.com,xxxxx6@qq.com",
	host= "stmp.exmail.qq.com",
	port= "25",
	password = "***********",
    limit = "1000"
}
```

