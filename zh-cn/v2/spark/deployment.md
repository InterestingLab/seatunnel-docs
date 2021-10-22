# 部署与运行

> seatunnel v2 For Spark 依赖Java运行环境和Spark，详细的seatunnel 安装步骤参考[安装seatunnel](/zh-cn/v2/spark/installation)

下面重点说明不同平台的运行方式:

### 在本地以 local 方式运行 seatunnel

```
./bin/start-seatunnel-spark.sh --master local[4] --deploy-mode client --config ./config/application.conf
```

### 在 Spark Standalone 集群上运行 seatunnel

```
# client 模式
./bin/start-seatunnel-spark.sh --master spark://207.184.161.138:7077 --deploy-mode client --config ./config/application.conf

# cluster 模式
./bin/start-seatunnel-spark.sh --master spark://207.184.161.138:7077 --deploy-mode cluster --config ./config/application.conf
```

### 在 Yarn 集群上运行 seatunnel

```
# client 模式
./bin/start-seatunnel-spark.sh --master yarn --deploy-mode client --config ./config/application.conf

# cluster 模式
./bin/start-seatunnel-spark.sh --master yarn --deploy-mode cluster --config ./config/application.conf
```

### 在 Mesos 上运行 seatunnel

```
# cluster 模式
./bin/start-seatunnel-spark.sh --master mesos://207.184.161.138:7077 --deploy-mode cluster --config ./config/application.conf
```

---

`start-seatunnel-spark.sh` 的 `master`, `deploy-mode` 参数的含义请参考: [命令使用说明](/zh-cn/v2/spark/commands/start-seatunnel-spark.sh)

如果要指定 seatunnel 运行时占用的资源大小，或者其他 Spark 参数，可以在 `--config` 指定的配置文件里面指定：

```
env {
  spark.executor.instances = 2
  spark.executor.cores = 1
  spark.executor.memory = "1g"
  ...
}
...

```

关于如何配置 seatunnel, 请见 [seatunnel 通用配置](/zh-cn/v2/spark/configuration/)
