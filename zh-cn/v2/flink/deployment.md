# 部署与运行

> seatunnel For Flink 依赖Java运行环境和Flink，详细的seatunnel 安装步骤参考[安装seatunnel](/zh-cn/v2/flink/installation)

下面重点说明不同平台的运行方式:

> 首先编辑解压后seatunnel目录下的config/seatunnel-env.sh, 指定必须环境配置FLINK_HOME

### 在Flink Standalone集群上运行seatunnel

```
.bin/start-seatunnel-flink.sh --config config-path
# -p 2 指定flink job的并行度为2,还可以指定更多的参数，使用 flink run -h查看
.bin/start-seatunnel-flink.sh -p 2 --config config-path
```
### 在Yarn集群上运行seatunnel
```
.bin/start-seatunnel-flink.sh -m yarn-cluster --config config-path
# -ynm seatunnel 指定在yarn webUI显示的名称为seatunnel,还可以指定更多的参数，使用 flink run -h查看
.bin/start-seatunnel-flink.sh -m yarn-cluster -ynm seatunnel --config config-path
```


---

可参考: [Flink Yarn Setup](https://ci.apache.org/projects/flink/flink-docs-release-1.9/zh/ops/deployment/yarn_setup.html)


