
第一天：
1. 确认需求，界定任务边界： 为华为CloudDragon设计API Gateway 方案，交付应用
2. 确认技术栈，spring-cloud框架，以及其下的技术zuul, eureka, Hystrix, robbin,config; spike 以上技术如何一起工作，出demo


第二天：
1.  zuul和Eureka的集成demo
使用Eureka作为服务发现，zuul作为智能代理
zuul demo， 使用zuul 作为微服务（例如ServiceA）的proxy，通过ServiceA的id把请求转到serviceA

2. 获得代码库，set up本地环境：在windows下配置maven，git，开发工具


第三天：
1.set up 本地开发环境
2.确认代码提交流程，部署流程：
   （启动前在选择snapshot version，选择要部署的环境：alpha）
3.部署第一个版本到alpha 环境



第四天：
1.用zuul搭建APIGateway，可以通过apigatway访问已有服务
2.部署APIGateway


第五天：
1.配置eureka，通过spring boot 的healthcheck检查服务状态（eureka默认是心跳检查）
2.	eureka注册中心使用域名, 找到部署相关人员，配置环境参数
3.访问zuul代理服务时需写两遍资源名，
   方案待定：
  （1），zuul自动寻找已注册到eureka的服务（需写两遍资源名：一个服务名，一个context path）
   （2），自己管理服务，不需写context path
   zuul：
     routes：
        serviceA:
        path: serviceA/**
        serviceId: serviceA
        stripprefix: false

4.spike 服务之间访问如何寻址，
   方案待定：
1，使用LoadBlancer 找到可以使用的 URI
         2，RestTemplate(spiking)



第六天：
1. zuul filter，拦截未认证请求
2.继续spike 服务之间访问如何寻址，
   方案待定：
1，使用LoadBlancer 找到可以使用的 URI 
         2，RestTemplate(spiking)：
封装请求，（1）apigateway 服务内请求  （2）客户端请求



第七天：
1. 创建service client 和apigatway client工程，第一版（用于封装请求方法，token， 签名）
2. zuul构成的apigateway工程不注册在uereka中心，不用智能路由方式，确定服务间调用方式



第八天：
1. 发布service client和apigatway client可用版本，封装用户原本使用的httpClient
2. 以配置文件方式配置ak/sk；从每个服务中读取ak/sk


第九天：
1. 迭代service client，封装用户原本使用的httpClient，添加各个已有服务的调用接口，支持云龙系统整改工作；
2. Service client 支持使用Rest template的请求方式，并支持https




