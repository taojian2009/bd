## 数据仓库 hive 

### 1.数据仓库 

####  1.1 基本概念

数据仓库是构建面向分析的集成化数据环境，为企业提供决策支持；

`面向分析的存储系统`

#### 1.2 主要特征
##### 面向主题 (subject-oriented)
数据仓库通过一个个主题域将多个业务系统的数据加载到一起，比如订单，用户，商品等；
用于分析；

##### 集成性(Integrated)

ETL 

##### 非易失性(Non-volatile)

不需要对数据仓库中的数据实时更新，而是一般每隔一段时间的较新的数据导入，
一般只做查询操作

##### 时变性


定期更新 
#### 1.3 数据库和数据仓库的区别

`OLTP` : 联机事务处理

`OLAP` : 联机分析处理

数据仓库是面向主题设计的；
数据仓库一般是存储历史数据，数据仓库有时候为了用于分析，一般会刻意冗余；

#### 1.4 数据仓库的分层架构

|username|schema|table_name|query_time|query_status|data_date|app_source|
|----|----|----|----|----|----|----|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:32:30|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:31:28|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:58|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:40|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:18|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:08|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:48|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:28|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:09|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:01|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:52|SUCCESS|2019-09-10|superset|
|jian.tao01|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:43|SUCCESS|2019-09-10|superset|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:32:30|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:31:28|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:58|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:40|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:18|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:08|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:48|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:28|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:09|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:01|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:52|SUCCESS|2019-09-12|davinci|
|zhang.san|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:43|SUCCESS|2019-09-12|davinci|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:32:30|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:31:28|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:58|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:40|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:18|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:30:08|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:48|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:29:28|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:09|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:28:01|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:52|SUCCESS|2019-09-12|sqlbuffet|
|jenny|analysis|analysis_lls_wechat_events_fuwuhao_daily|2019-09-05 11:27:43|SUCCESS|2019-09-12|sqlbuffet|
