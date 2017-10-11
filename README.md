# 项目介绍
UDP 是百分点集体的一个平台级产品, 目前已经服务多家客户, 本项目的目的是提供相关的资源及其操作流程, 以方便产品演示使用

UDP Demo 项目的目标是提供一个可操作的过程来对部署好的 UDP 系统进行验证，这里的验证会覆盖 UDP 主要的功能，对于如何部署、使用则不会做介绍（具体可以参见内部的`部署`和`使用`手册)

* 在验证之前或者过程中，请详细参阅 UDP 团队提供的 `部署手册`, `使用手册`
* 需要对本文档后面提到的 `验证矩阵汇总` 进行逐一验证并进行反馈
* 本文档提供了核心的场景描述，用户需要根据 `场景介绍` 提到的内容进行操作，并及时反馈操作中遇到的问题

# 验证矩阵

* 请仔细走完下面的场景，并及时反馈
* 每个模块的操作参考`使用手册`
* 注意: UDP 的用户分为管理员和非管理员(又分为租户管理员和非租户管理员)两类，验证不同的功能的时候，需要以不同用户登录

| 模块        | 子模块   | 说明 | 检查结果 |
| --------   | --------  | :-------- | :-------- |
| 队列同步    |			| 修改 hadoop yarn 队列，通过后台脚本可以将队列信息同步到 UDP 中，然后租户的配置中，在选择队列时，是可以查看到新的队列信息的 | |
| 租户管理(管理员)  | 用户管理 | 注意，新增的用户如果是在禁用用户列表里面，是不能新增的，禁用用户列表参见 [swordfish 部署文档](https://github.com/baifendian/swordfish/wiki/deploy] 中的 `prohibit.user.list` 配置 | |
|           | 租户管理 | | |
|           | 日志审计 | | 用户登陆，以及系统中的写操作都应该会有详细记录 | |
| 租户管理(非管理员) | 租户信息 | | |
|           | 用户管理 | | |
| 项目管理   | 我的项目 | | |
|           | 项目管理 | | |
| 模型开发   | 模型数据源 | 建立的数据源会在`物理模型`和`表管理`中使用 | |
|           | 主题域  | | |
|           | 逻辑模型 | | |
|           | 物理模型 | | |
|           | 表管理 | | |
| 数据开发   | 数据源设置 | | |
|           | 资源管理 | | |
|           | 函数管理 | | |
|           | 即席查询 | | |
|           | 流任务开发 | | |
|           | 工作流开发 | | |
| 运维中心   | 概览 | | |
|          | 工作流调度 | | |
|          | 工作流日志 | | |
|          | 流任务日志 | | |
| 数据视图  | 概览 | | |
|          | 数据地图 | | |
| 数据管理  | 数据库管理 | | |
|          | 权限管理 | | |
|          | 数据质量 | | |

# 数据集介绍
下面数据集来源于互联网，用户可以自行下载

* [地球表面温度](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data)
* [电影获奖记录](https://www.kaggle.com/theacademy/academy-awards)

# 模型和表设计
`温度`表

| 属性        | 类型   |  描述  |
| --------   | -----:  | :----:  |
| dt     |    date    |  日期  |
| average_temperature     | double |   平均气温     |
| average_temperature_uncertainty  |  double   |   平均气温浮动大小   |
| city     |    string    |  城市  |
| country     |    string    |  国家  |
| latitude     |    string    |  纬度  |
| longitude     |    string    |  经度  |
| year       |    int    |  年份  |

`获奖记录`表

| 属性        | 类型   |  描述  |
| --------   | -----:  | :----:  |
| year     | string |   年份     |
| ceremony  |  int  |   典礼   |
| award     |    string    |  奖项  |
| winner     |int    |  获得者  |
| name     |    string    |  获奖者名字  |
| film     |    string    |  电影  |

# 场景介绍

* 请仔细走完下面的场景，并及时反馈

## 场景一
> 说明: 演示整个建模、建表的过程, 以及执行一些数据探查、质量校验, 整个过程中, 可能会遇到权限问题, 需要解决相关的授权

1. [模型开发](https://github.com/baifendian/udp-demo/wiki/ER-example)
1. [数据上传和查询](https://github.com/baifendian/udp-demo/wiki/Import-example)
1. [数据质量](https://github.com/baifendian/udp-demo/wiki/DQ-example)

## 场景二
> 说明: 演示整个工作流的基本使用, 以及调度配置

1. [工作流及调度配置](https://github.com/baifendian/udp-demo/wiki/workflow-example)

## 场景三
> 说明: 演示流任务的基本使用

1. [构建一个 Spark 流任务, 从 Socket 端口读取消息并写到控制台](https://github.com/baifendian/udp-demo/wiki/spark-example)
1. [构建一个 Storm 流任务, 从 Kafka 读取消息, 分析错误日志并记录到 Kafka 中](https://github.com/baifendian/udp-demo/wiki/storm-example)

## 场景四
> 说明: 演示 "可视化" ETL 的基本使用

1. [构建一个可视化 ETL 任务, 并执行(包括发布)](https://github.com/baifendian/udp-demo/wiki/etl-example)

# FAQ

1.  **工作流发布失败，提示依赖资源未发布**

在`数据开发 -> 资源管理` 将依赖资源进行发布

2. **导入数据失败，HDFS或者Hive表无权限**

在`数据管理 -> 权限管理`里申请相关 Hive 表和 HDFS 路径的权限