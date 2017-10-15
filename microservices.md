# 微服务

`https://martinfowler.com/articles/microservices.html`



## 微服务架构的九大特性


### 单块应用和微服务

![单块应用和微服务](https://martinfowler.com/articles/microservices/images/sketch.png)

Note:

- 一个单块应用三个主要部分：客户端用户界面、数据库和服务端应用系统
- 应用系统的一个很小的部分的一处变更，也需要将整个单块应用系统进行重新构建和部署
- 随着时间的推移，单块应用开始变得经常难以保持一个良好的模块化结构，这使得它变得越来越难以将一个模块的变更的影响控制在该模块内


### 特性一：“组件化”与“多服务”

Note:

- 组件：能被链接到一段程序，且能通过内存中的函数来进行调用
- 服务：进程外的组件，它们通过诸如web service请求或远程过程调用这样的机制来进行通信
- 优点：服务可被独立部署；更加显式的（explicit）组件接口
- 缺点：远程调用更加昂贵，所以远程调用API接口必须是粗粒度的；难以修改组件间的职责分配


### 特性二：围绕“业务功能”组织团队


> 任何设计（广义上的）系统的组织，都会产生这样一个设计，即该设计的结构与该组织的沟通结构相一致。
>
>——梅尔文•康威（Melvyn Conway）, 1967年


#### 康威定律在起作用

![](https://martinfowler.com/articles/microservices/images/conways-law.png)

NOTE:

---传统从技术层面
* 用户界面团队、服务器端团队和数据库团队
* 变更


#### 被团队边界所强化的服务边界

![](https://martinfowler.com/articles/microservices/images/PreferFunctionalStaffOrganization.png)

NOTE:

---微服务从业务层面
* 全栈、自组织
* 一方面可以有效减少服务内部修改所产生的内耗；另一方面，团队边界可以变得更为清晰。


### 特性三：“产品”而非“项目”

> 谁构建，谁运行

Note:

- 单块应用系统的开发工作也可以
- 这样的“产品”理念，是与业务功能的联动绑定在一起的

* 奶妈和亲娘
* 一个团队在一个产品的整个生命周期中都应该保持对其拥有
* 一个开发团队对一个在生产环境下运行的软件负全责
* 微服务：更便于掌握和维护


### 特性四：“智能端点”与“傻瓜管道”

Note:

- ESB产品经常包括高度智能的设施，来进行消息的路由、编制(choreography)、转换，并应用业务规则。
- 与ESB形成对比（中心化和哑服务）
- 像经典Unix的“过滤器”(filter)那样来工作


> 成为Web，而不是躲着Web (Be of the web, not behind the web)
>
> ——Ian Robinson

Note:

- 轻量级的消息总线
- 将一个单块系统改造为若干微服务的最大问题，在于对通信模式的改变
- 第一种，使用HTTP协议的RESTful API或轻量级的消息发送协议，来实现信息传递与服务调用的触发。
- 第二种，通过在轻量级消息总线上传递消息，类似RabbitMQ等一些提供可靠异步交换的结构。


### 特性五：“去中心化”地治理技术

> 不是每一个问题都是钉子，不是每一个方案都是锤子

Note:

- 采用轻量级的契约定义接口
- 技术异构


### 特性六：“去中心化”地管理数据

![](https://martinfowler.com/articles/microservices/images/decentralised-data.png)

Note: 

* 数据库中的存储内容拆分到新的同平台的其他数据库实例中
* 对一些具有特殊结构或业务特性的数据存储到一些其他技术的数据库实例中
* 数据一致性也成为“微服务”架构中急需解决的问题之一，强调最终一致性


### 特性七：“基础设施”自动化

![](https://martinfowler.com/articles/microservices/images/basic-pipeline.png)

Note:

* 背景：云计算、容器技术以及DevOps，程序大爆炸
* 必须一开始就构建起“持续交付”平台来支撑整个实施过程
* 自动化测试：每次部署前的强心剂，尽可能的获得对正在运行软件的信心。
* 自动化部署：解放繁琐枯燥的重复操作以及对多环境的配置管理。


> 让“部署”工作变得“无聊”


### 特性八：“容错”设计

Note:

- 与一个单块设计相比，这是一个劣势
- 监控
- 微服务也会“一挂全挂”
- 故障检测
- 自动恢复


### 特性九：“演进式”设计

Note:

- 控制应用系统中的变化，而无须减少变化的发生
- 许多服务将来会报废，而不是守着这些服务做长期演进
- “一旦赛事结束，这样页面就可以被删除”
- 变化模式：
 - 将那些能在同时发生变化的东西，放到同一个模块中
 - 系统中那些很少发生变化的部分，应该被放到不同的服务中，以区别于那些当前正在经历大量变动的部分
 - 如果发现需要同时反复变更两个服务时，这就是它们两个需要被合并的一个信号
- 版本化



## 未来的方向是“微服务”吗？


### 难点

- 搞清楚某个组件的边界
- 将组件内的复杂性转移到组件之间的连接
- 技术更加过硬的团队


### 不要一上来就以微服务架构做为起点

- 要用一个单块系统做为起点，并保持其模块化。
- 当这个单块系统出现了问题后，再将其分解为微服务。


### 谨慎乐观

到目前为止，我们已经看到足够多的有关微服务风格的事物，并且觉得这是一条有价值去跋涉的道路。我们不能肯定地说，道路的尽头在哪里。但是，软件开发的挑战之一，就是只能基于“目前手上拥有但还不够完善”的信息来做出决策。



## Microservice Premium

Note:

- automated deployment
- monitoring
- dealing with failure
- eventual consistency
- and other factors that a distributed system introduces


![](https://martinfowler.com/bliki/images/microservice-verdict/productivity.png)



## Microservice Prerequisites


![](https://martinfowler.com/bliki/images/microservicePrerequisites/sketch.png)


- Rapid provisioning
- Basic Monitoring
- Rapid application deployment
- DevOps culture



## 参考资料

- https://martinfowler.com/articles/microservices.html
- https://martinfowler.com/bliki/MicroservicePremium.html
- https://martinfowler.com/bliki/MicroservicePrerequisites.html
- https://martinfowler.com/microservices/

