# 下载、安装

## 下载

### 社区版本（Community）

https://github.com/InterestingLab/seatunnel/releases

## 环境准备

### 准备好JDK1.8

seatunnel 依赖JDK1.8运行环境。

### 准备好 Spark
 
seatunnel 依赖 Spark，安装 seatunnel 前，需要先准备好Spark。
请先[下载Spark](http://spark.apache.org/downloads.html), Spark版本请选择 >= 2.x.x。下载解压后，不需要做任何配置即可提交Spark deploy-mode = local模式的任务。
如果你期望任务运行在Standalone集群或者Yarn、Mesos集群上，请参考Spark官网配置文档。

### 安装 seatunnel

下载seatunnel安装包并解压， 这里以社区版为例:

```
wget https://github.com/InterestingLab/seatunnel/releases/download/v<version>/seatunnel-<version>.zip -O seatunnel-<version>.zip
unzip seatunnel-<version>.zip
ln -s seatunnel-<version> seatunnel
```

没有任何复杂的安装配置步骤，seatunnel 的使用方法请参考 [Quick Start](/zh-cn/v2/spark/quick-start.md), 配置请参考 [Configuration](/zh-cn/v2/spark/configuration/)。

如果想把 seatunnel 部署在 Spark Standalone/Yarn/Mesos 集群上运行，请参考 [seatunnel部署](/zh-cn/v2/spark/deployment)

