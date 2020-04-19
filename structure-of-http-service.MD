# Structure of Main Service

## 1. 程序入口（Main） 
程序的入口，主要负责
1. 配置的处理 （config）
2. 数据库，日志等服务的初始化 （service）
3. 路由加载（router）
4. 服务启动 / Graceful Start
5. Graceful Shutdown
6. 健康检查（health check）

## 2. 配置读取（config）
1. 注意配置的优先级
    1. 环境变量
    2. 启动的 args
    3. 远程配置库（etcd，consul）
    4. 本地配置文件
    5. defaults
2. 有时配置文件是通过启动进程的 args 进行指定

## 3. 服务的初始化
1. 日志组件的初始化
    * transport
        * stdout/stderr
        * 文件
            * rotation
                * size
                * date
        * remote
    * format
        * json
        * apach log

2. 数据库的初始化
    * 连接池配置
    * 鉴权

## 4. 路由加载
1. 中间件
2. 路由
    1. 路由 Group
    2. 统一错误处理中间件

## 5. 服务启动
1. addr， port 确定
2. graceful start
    * 在达成某些条件之后才接入流量

## 6. graceful shutdown
1. 不再接受新的请求
2. 等待当前进行的请求结束
3. 整体的 timeout 时间作为兜底

## 7. health check
1. 开放特定端口
2. 外部/内部

## 8. 整体
1. 统一的错误
    * 错误码、错误信息
        * 错误码表明模块
    * 统一的错误处理中间件，统一从错误日志
2. 统一的 http 返回结构
    * 固定的数据结构
    * 固定的错误处理方法：
        * 以 http status 标注
        * 返回 200，以返回体中的 code 做标注
    