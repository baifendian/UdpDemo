# 项目介绍
UDP 是百分点集体的一个平台级产品, 目前已经服务多家客户, 本项目的目的是提供相关的资源及其操作流程, 以方便产品演示使用.

# 数据集介绍
* [地球表面温度](https://www.kaggle.com/berkeleyearth/climate-change-earth-surface-temperature-data)
* [电影获奖记录](https://www.kaggle.com/theacademy/academy-awards)

# 模型和表设计
温度表

| 属性        | 类型   |  描述  |
| --------   | -----:  | :----:  |
| average_temperature     | double |   5     |
| average_temperature_uncertainty  |  double   |   12   |
|     city     |    string    |  城市  |
|     country     |    string    |  国家  |
|     latitude     |    string    |  纬度  |
|     longitude     |    string    |  经度  |
|     year     |    string    |  年份  |

获奖记录表

| 属性        | 类型   |  描述  |
| --------   | -----:  | :----:  |
| year     | string |   年份     |
| ceremony  |  int   |   典礼   |
|     award     |    string    |  奖项  |
|     winner     |    int    |  获得者  |
|     name     |    string    |  获奖者名字  |
|     film     |    string    |  电影  |


# 资源介绍
*
*
*

# 场景介绍
## 场景一
> 说明: 场景目的是希望用户了解整个建模和建表的过程, 以及执行一些数据探查和质量校验, 整个过程中, 可能会遇到权限问题, 需要解决相关的授权
1. 建模及建表

1. 将本地数据导入到数仓中

1. 对数据进行探查

1. 配置数据质量

## 场景二
> 说明: 场景的目的是希望用户了解工作流的基本概念和使用, 以及相应的数据质量检测
1. 统计记录数(MR/Spark)

1. 构建一个比较复杂的工作流

1. 配置调度

## 场景三
> 说明: 场景的目的是希望用户了解流任务的基本使用
1. 构建一个 Spark 流任务, 从 Socket 端口读取消息并写到控制台

2. 构建一个 Storm 流任务, 从 Kafka 读取消息, 做单词统计并写到控制台

## 场景四
> 说明: 场景的目的是希望用户了解 "可视化" ETL 的基本使用
1. 构建一个可视化 ETL 任务, 并执行(包括发布)
