# 微服务实战演练


## 镜像库
[]()


## 代码库
[]()


## Maven
Maven 是一个项目管理和整合工具。Maven 为开发者提供了一套完整的构建生命周期框架。开发团队几乎不用花多少时间就能够自动完成工程的基础构建配置，因为 Maven 使用了一个标准的目录结构和一个默认的构建生命周期。

Note：

Maven 能够帮助开发者完成以下工作：
构建
文档生成
报告
依赖
SCMs
发布
分发
邮件列表
总的来说，Maven 简化了工程的构建过程，并对其标准化。它无缝衔接了编译、发布、文档生成、团队合作和其他任务。Maven 提高了重用性，负责了大部分构建相关的任务。


## POM

* POM 代表工程对象模型。它是使用 Maven工作时的基本组建，是一个xml文件。它被放在工程根目录下，文件命名为 pom.xml。
* POM 包含了关于工程和各种配置细节的信息，Maven 使用这些信息构建工程。
* POM 也包含了目标和插件。


## 服务注册发现实战
通过服务发现进行服务调用负载均衡。


### 所需服务：
1. eureka-server
2. eureka-clientx2
3. ribbon-demo
4. feign-demo


### 创建eureka-server

1. 创建Spring Boot工程，并在pom.xml中引入依赖：spring-cloud-starter-eureka-server
2. 在应用主类上使用@EnableEurekaServer注解启动一个服务注册中心提供给其他应用进行对话


### 创建eureka-client

1. 创建Spring Boot工程，并在pom.xml中引入依赖：spring-cloud-starter-eureka-server
2. 实现/add请求处理接口,通过DiscoveryClient对象获得服务实例的相关内容
3. 在主类中通过加上@EnableDiscoveryClient注解，激活DiscoveryClient
4. 在application.yml配置服务名称、指定服务注册中心等内容。


## 配置热刷新实战
通过配置中心进行配置热刷新。


### 所需服务：
1. eureka-server
2. config-server
3. config-clientx2


## 故障熔断实战
通过故障熔断阻止故障雪崩。


### 所需服务：
1. eureka-server
2. eureka-client
3. feign-demo


## 服务监控实战
通过性能面板和调用链追踪优化服务。


### 所需服务：
1. eureka-server
2. eureka-client
3. ribbon-demo
4. feign-demo
5. admin-demo
6. turbine-demo
7. zipkin-demo


## 服务网关实战
通过服务网关控制访问流量。


### 所需服务：
1. eureka-server
2. eureka-client
3. ribbon-demo
4. zuul-demo


### zuul-demo的实现
在pom.xml中引入依赖：spring-cloud-starter-zuul
在应用主类上使用@EnableZuulProxy注解开启Zuul的功能。

