### 介绍
java毕业设计，电影院购票系统
### 3000多套系统，需要联系
抠：3565014707 微：a13424421017

#### 软件架构
##### 整体架构模式
这是一个 电影票务与社区管理系统，采用 前后端分离架构，包含以下模块：

管理后台（src/main/resources/admin）：基于 Vue.js + ElementUI 的 SPA 应用，用于影院管理员管理电影、订单、用户等。

用户端（src/main/resources/front）：基于 Layui + jQuery 的传统前端，面向消费者提供电影浏览、购票、社区互动功能。

后端服务（src/main/java）：基于 Spring Boot + MyBatis 的 Java 服务，提供 RESTful API 和业务逻辑。

##### 分层架构设计
后端分层：

Controller层：controller 包（如 CommonController）处理 HTTP 请求，返回 JSON 数据。

Service层：service 包（CommonService）实现核心业务逻辑（如订单生成、库存扣减）。

DAO层：dao 包（CommonDao）通过 MyBatis XML 文件（CommonDao.xml）操作数据库。

实体与数据模型：

entity 包定义数据库实体（如 DianyingCollectionModel 电影收藏实体）；

vo（值对象）和 view（视图模型）用于接口数据传输和复杂查询结果封装。

前端分层：

管理后台（Vue.js）：

视图层：views/modules 定义页面（如 dianying 电影管理页）。

组件层：components 封装可复用组件（如 BreadCrumbs 面包屑导航）。

状态管理：通过 Vuex（store.js）管理全局状态（如用户权限）。

用户端（Layui）：

传统 MVC：通过 HTML + jQuery 实现动态页面（如 dianying/add.html 电影详情页）。
##### 关键技术特性
权限控制：

后端通过 AuthorizationInterceptor 拦截器和 @APPLoginUser 注解实现接口权限校验；

前端管理后台通过路由（router-static.js）限制页面访问权限。

多线程处理：

MyThreadMethod 可能用于异步任务（如订单超时取消、短信通知）。

第三方服务集成：

BaiduUtil 可能用于地图服务（影院定位）或 AI 能力（如电影推荐）。

富文本编辑器（tinymce）支持管理员发布带格式的公告或电影介绍。
#### 核心功能模块解析
##### 电影票务模块
电影管理：

dianying（电影信息）：维护电影名称、场次、票价、海报等。

dianyingOrder（电影订单）：处理用户购票订单，支持在线支付（dianyingOrderPayment）。

用户交互：

dianyingCollection（电影收藏）：用户收藏感兴趣的电影。

dianyingCommentback（电影评价）：用户对已观影电影进行评分和评论。

##### 社区互动模块
论坛功能：

forum（社区论坛）：用户发布影评、讨论话题，支持点赞和回复。

dictionaryForumState（论坛状态管理）：定义帖子状态（如正常、删除、置顶）。

##### 系统管理模块
数据字典：

dictionary 系列模块（如 dictionarySex 性别字典、dictionaryShangxia 上下架状态）维护系统基础数据。

用户与权限：

yonghu（用户管理）：审核用户注册信息，禁用违规账户。

news（新闻公告）：发布系统公告或影讯动态。
##### 支付与订单
支付集成：

dianyingOrderPayment 定义支付方式（微信/支付宝），通过 config.properties 配置支付密钥。

订单处理：

订单超时自动取消（通过 MyThreadMethod 实现定时任务）。
