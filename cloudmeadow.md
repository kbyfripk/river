# WebLink Navigator

WebLink Navigator 是一个面向技术内容聚合与知识导航的开源工具集，专注于将分散在各类技术博客、新闻站点与文档平台中的优质外链进行结构化整理与分类呈现。该项目定位于技术团队、内容运营者与个人开发者，帮助其快速构建可维护、可扩展的外部资源索引体系，降低信息检索成本，提升知识复用效率。

项目核心能力围绕外链数据的采集、清洗、存储与展示展开，提供标准化的数据导入接口与前端渲染模板，支持自定义分类标签、全文检索与访问频率统计。通过配置文件即可完成站点适配与字段映射，无需编写额外代码。WebLink Navigator 适用于构建技术文档门户、团队知识库导航页、开源项目推荐列表或垂直领域的资源聚合站点。

## 功能概览

**批量链接导入** 支持从 CSV、JSON 及 Markdown 列表批量导入外链数据，自动识别 URL 结构与元信息字段。

**智能分类引擎** 基于规则与正则表达式匹配，根据 URL 路径、来源域名与内容关键词为每条链接自动生成分类标签。

**访问状态监控** 定时检测已收录链接的可访问性，返回 HTTP 状态码与响应时间，标记失效或重定向链接。

**自定义模板渲染** 提供默认的响应式前端模板，支持通过 Handlebars 或 Vue 组件自定义列表页与详情页布局。

**全文检索接口** 基于倒排索引实现标题与摘要的快速搜索，支持布尔查询与模糊匹配。

**数据导出功能** 支持将当前索引数据导出为 JSON、Markdown 表格或 HTML 目录结构，便于静态站点生成器使用。

**权限分级管理** 内置简单的角色控制，区分管理员、编辑与访客权限，便于团队协作维护。

**访问统计分析** 记录链接点击次数与来源页面，生成按日、周、月聚合的热度趋势图。

## 应用场景

**技术团队内部知识导航** 研发团队可在内部服务器部署 WebLink Navigator，将日常查阅的 API 文档、技术规范、运维手册与故障排查案例统一收录，按项目或技术栈分类，新成员入职时可快速获取所有必要参考链接。

**开源项目推荐聚合站** 社区运营者可使用该项目构建特定领域的开源工具推荐页面，例如 Python 数据科学库合集、前端 UI 框架索引或 DevOps 流水线组件列表，定期更新并对外公开，降低开发者的选型成本。

**技术博客外链索引页** 个人技术博主可将所有引用过的外部文章、论文、视频教程与代码仓库集中管理，为每篇博客生成独立的“参考资料”板块，提升内容可信度与可追溯性。

**在线课程辅助资源库** 教育机构或培训讲师可为每门课程建立配套的外链资源库，将延伸阅读、习题解答、项目案例与开发环境配置文档分类存放，学生可按章节或难度层级检索。

## 快速开始

以下命令演示如何在本地环境中完成 WebLink Navigator 的克隆、依赖安装与服务启动。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装后端依赖（使用 npm）
npm install

# 安装前端依赖（进入 client 目录）
cd client
npm install
cd ..

# 初始化配置文件
cp config/default.example.yaml config/default.yaml

# 启动开发服务器（后端端口 3000，前端开发服务器端口 8080）
npm run dev
```

启动后，访问 http://localhost:8080 即可进入导航页面。管理员后台默认路径为 /admin，初始账号密码请查阅 config/default.yaml 中的初始化设置。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖 |
| MongoDB | 5.x 或 6.x | 主数据库，存储链接元数据与分类信息 |
| Redis | 7.x | 缓存与会话存储，用于提升检索性能 |
| Elasticsearch | 8.x | 可选依赖，启用全文检索高级功能时需安装 |
| PM2 | 5.x | 生产环境进程守护，非开发环境必需 |
| Nginx | 1.22+ | 反向代理与静态资源服务，生产部署推荐 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速部署并导入第一批链接；配置文件中的必填字段有哪些 |
| 数据管理 | docs/data-management.md | 如何批量更新链接状态；如何自定义分类规则与标签体系 |
| 前端定制 | docs/frontend-customization.md | 如何更换主题配色；如何修改列表页每页显示条数；如何添加自定义 CSS |
| 运维监控 | docs/operations.md | 如何配置定时检测任务；如何查看访问日志与错误报告；如何备份数据库 |
| API 参考 | docs/api-reference.md | 所有 RESTful 接口的请求参数与返回示例；如何通过 API 进行第三方集成 |
| 贡献指南 | CONTRIBUTING.md | 如何提交代码、报告缺陷或完善文档；代码风格与测试要求 |

## 资源列表

- http://m.blog.fcful.cn/bnews/79955.htm
- http://m.blog.fcful.cn/bnews/8918.htm
- http://m.blog.fcful.cn/bnews/7044.htm
- http://m.blog.fcful.cn/bnews/9089.htm
- http://m.blog.fcful.cn/bnews/51412.htm
- http://m.blog.fcful.cn/bnews/46687.htm
- http://m.blog.fcful.cn/bnews/5659235.htm
- http://m.blog.fcful.cn/bnews/67126.htm
- http://m.blog.fcful.cn/bnews/132445.htm
- http://m.blog.fcful.cn/bnews/59417.htm
- http://m.blog.fcful.cn/bnews/600145.htm
- http://m.blog.fcful.cn/bnews/2938560.htm
- http://m.blog.fcful.cn/bnews/0733.htm
- http://m.blog.fcful.cn/bnews/562192.htm
- http://m.blog.fcful.cn/bnews/8388529.htm
- http://m.blog.fcful.cn/bnews/58508.htm
- http://m.blog.fcful.cn/bnews/54597.htm
- http://m.blog.fcful.cn/bnews/2928.htm
- http://m.blog.fcful.cn/bnews/0639.htm
- http://m.blog.fcful.cn/bnews/4846.htm
- http://m.blog.fcful.cn/bnews/55141.htm
- http://m.blog.fcful.cn/bnews/0642159.htm
- http://m.blog.fcful.cn/bnews/00872.htm
- http://m.blog.fcful.cn/bnews/02392.htm
- http://m.blog.fcful.cn/bnews/1041.htm
- http://m.blog.fcful.cn/bnews/509385.htm
- http://m.blog.fcful.cn/bnews/3234.htm
- http://m.blog.fcful.cn/bnews/3510306.htm
- http://m.blog.fcful.cn/bnews/3258901.htm
- http://m.blog.fcful.cn/bnews/0896265.htm
- http://m.blog.fcful.cn/bnews/5094981.htm
- http://m.blog.fcful.cn/bnews/8866608.htm
- http://m.blog.fcful.cn/bnews/6141430.htm
- http://m.blog.fcful.cn/bnews/8284215.htm
- http://m.blog.fcful.cn/bnews/6318464.htm
- http://m.blog.fcful.cn/bnews/7749606.htm
- http://m.blog.fcful.cn/bnews/44858.htm
- http://m.blog.fcful.cn/bnews/37526.htm
- http://m.blog.fcful.cn/bnews/669553.htm
- http://m.blog.fcful.cn/bnews/30955.htm
- http://m.blog.fcful.cn/bnews/1290.htm
- http://m.blog.fcful.cn/bnews/2061.htm
- http://m.blog.fcful.cn/bnews/94750.htm
- http://m.blog.fcful.cn/bnews/6897513.htm
- http://m.blog.fcful.cn/bnews/20674.htm
- http://m.blog.fcful.cn/bnews/1678623.htm
- http://m.blog.fcful.cn/bnews/2419.htm
- http://m.blog.fcful.cn/bnews/6407888.htm
- http://m.blog.fcful.cn/bnews/551376.htm
- http://m.blog.fcful.cn/bnews/031951.htm
- http://m.blog.fcful.cn/bnews/2357.htm
- http://m.blog.fcful.cn/bnews/1646.htm
- http://m.blog.fcful.cn/bnews/80412.htm
- http://m.blog.fcful.cn/bnews/4263684.htm
- http://m.blog.fcful.cn/bnews/314691.htm
- http://m.blog.fcful.cn/bnews/46690.htm
- http://m.blog.fcful.cn/bnews/793065.htm
- http://m.blog.fcful.cn/bnews/2689831.htm
- http://m.blog.fcful.cn/bnews/9518.htm
- http://m.blog.fcful.cn/bnews/33173.htm
- http://m.blog.fcful.cn/bnews/720907.htm
- http://m.blog.fcful.cn/bnews/3197.htm
- http://m.blog.fcful.cn/bnews/4970900.htm
- http://m.blog.fcful.cn/bnews/38394.htm
- http://m.blog.fcful.cn/bnews/1616295.htm
- http://m.blog.fcful.cn/bnews/044291.htm
- http://m.blog.fcful.cn/bnews/877889.htm
- http://m.blog.fcful.cn/bnews/7521.htm
- http://m.blog.fcful.cn/bnews/203349.htm
- http://m.blog.fcful.cn/bnews/7471304.htm
- http://m.blog.fcful.cn/bnews/8547.htm
- http://m.blog.fcful.cn/bnews/0866.htm
- http://m.blog.fcful.cn/bnews/3092628.htm
- http://m.blog.fcful.cn/bnews/6826.htm
- http://m.blog.fcful.cn/bnews/6034915.htm
- http://m.blog.fcful.cn/bnews/0161198.htm
- http://m.blog.fcful.cn/bnews/14532.htm
- http://m.blog.fcful.cn/bnews/8365.htm
- http://m.blog.fcful.cn/bnews/2993535.htm
- http://m.blog.fcful.cn/bnews/738744.htm
- http://m.blog.fcful.cn/bnews/8240565.htm
- http://m.blog.fcful.cn/bnews/7006850.htm
- http://m.blog.fcful.cn/bnews/7594180.htm
- http://m.blog.fcful.cn/bnews/185345.htm
- http://m.blog.fcful.cn/bnews/3089.htm
- http://m.blog.fcful.cn/bnews/8491429.htm
- http://m.blog.fcful.cn/bnews/2865898.htm
- http://m.blog.fcful.cn/bnews/229866.htm
- http://m.blog.fcful.cn/bnews/09238.htm
- http://m.blog.fcful.cn/bnews/083726.htm
- http://m.blog.fcful.cn/bnews/9655.htm
- http://m.blog.fcful.cn/bnews/125833.htm
- http://m.blog.fcful.cn/bnews/6642939.htm
- http://m.blog.fcful.cn/bnews/34076.htm
- http://m.blog.fcful.cn/bnews/5296.htm
- http://m.blog.fcful.cn/bnews/856494.htm
- http://m.blog.fcful.cn/bnews/6519.htm
- http://m.blog.fcful.cn/bnews/5255.htm
- http://m.blog.fcful.cn/bnews/138735.htm
- http://m.blog.fcful.cn/bnews/2201873.htm
- http://m.blog.fcful.cn/bnews/251193.htm
- http://m.blog.fcful.cn/bnews/1137.htm
- http://m.blog.fcful.cn/bnews/6814.htm
- http://m.blog.fcful.cn/bnews/9346.htm
- http://m.blog.fcful.cn/bnews/1979.htm
- http://m.blog.fcful.cn/bnews/64730.htm
- http://m.blog.fcful.cn/bnews/36391.htm
- http://m.blog.fcful.cn/bnews/260338.htm
- http://m.blog.fcful.cn/bnews/310010.htm
- http://m.blog.fcful.cn/bnews/7733333.htm
- http://m.blog.fcful.cn/bnews/4894210.htm
- http://m.blog.fcful.cn/bnews/8545873.htm
- http://m.blog.fcful.cn/bnews/2515.htm
- http://m.blog.fcful.cn/bnews/693668.htm
- http://m.blog.fcful.cn/bnews/1103302.htm
- http://m.blog.fcful.cn/bnews/9468128.htm
- http://m.blog.fcful.cn/bnews/1749.htm
- http://m.blog.fcful.cn/bnews/447296.htm
- http://m.blog.fcful.cn/bnews/7726.htm
- http://m.blog.fcful.cn/bnews/4235.htm
- http://m.blog.fcful.cn/bnews/27399.htm
- http://m.blog.fcful.cn/bnews/768304.htm
- http://m.blog.fcful.cn/bnews/9740830.htm
- http://m.blog.fcful.cn/bnews/55377.htm
- http://m.blog.fcful.cn/bnews/7966.htm
- http://m.blog.fcful.cn/bnews/296739.htm
- http://m.blog.fcful.cn/bnews/9455.htm
- http://m.blog.fcful.cn/bnews/07049.htm
- http://m.blog.fcful.cn/bnews/23766.htm
- http://m.blog.fcful.cn/bnews/7420.htm
- http://m.blog.fcful.cn/bnews/353142.htm
- http://m.blog.fcful.cn/bnews/4109274.htm
- http://m.blog.fcful.cn/bnews/3046.htm
- http://m.blog.fcful.cn/bnews/8714.htm
- http://m.blog.fcful.cn/bnews/0592264.htm
- http://m.blog.fcful.cn/bnews/7376153.htm
- http://m.blog.fcful.cn/bnews/435119.htm
- http://m.blog.fcful.cn/bnews/22979.htm
- http://m.blog.fcful.cn/bnews/3546.htm
- http://m.blog.fcful.cn/bnews/92303.htm
- http://m.blog.fcful.cn/bnews/6858039.htm
- http://m.blog.fcful.cn/bnews/964227.htm
- http://m.blog.fcful.cn/bnews/3443.htm
- http://m.blog.fcful.cn/bnews/7767.htm
- http://m.blog.fcful.cn/bnews/0585969.htm
- http://m.blog.fcful.cn/bnews/402344.htm
- http://m.blog.fcful.cn/bnews/9388.htm
- http://m.blog.fcful.cn/bnews/70917.htm
- http://m.blog.fcful.cn/bnews/87444.htm
- http://m.blog.fcful.cn/bnews/996210.htm
- http://m.blog.fcful.cn/bnews/79177.htm
- http://m.blog.fcful.cn/bnews/7866156.htm
- http://m.blog.fcful.cn/bnews/1146776.htm
- http://m.blog.fcful.cn/bnews/9273.htm
- http://m.blog.fcful.cn/bnews/40819.htm
- http://m.blog.fcful.cn/bnews/2988.htm
- http://m.blog.fcful.cn/bnews/2161555.htm
- http://m.blog.fcful.cn/bnews/9343054.htm
- http://m.blog.fcful.cn/bnews/0944.htm
- http://m.blog.fcful.cn/bnews/1044.htm
- http://m.blog.fcful.cn/bnews/3203766.htm
- http://m.blog.fcful.cn/bnews/0846.htm
- http://m.blog.fcful.cn/bnews/66798.htm
- http://m.blog.fcful.cn/bnews/57802.htm
- http://m.blog.fcful.cn/bnews/42477.htm
- http://m.blog.fcful.cn/bnews/54368.htm
- http://m.blog.fcful.cn/bnews/2314727.htm
- http://m.blog.fcful.cn/bnews/263772.htm
- http://m.blog.fcful.cn/bnews/0885836.htm
- http://m.blog.fcful.cn/bnews/5852737.htm
- http://m.blog.fcful.cn/bnews/5431.htm
- http://m.blog.fcful.cn/bnews/004807.htm
- http://m.blog.fcful.cn/bnews/51030.htm
- http://m.blog.fcful.cn/bnews/22465.htm
- http://m.blog.fcful.cn/bnews/153880.htm
- http://m.blog.fcful.cn/bnews/428418.htm
- http://m.blog.fcful.cn/bnews/8619.htm
- http://m.blog.fcful.cn/bnews/1327527.htm
- http://m.blog.fcful.cn/bnews/121608.htm
- http://m.blog.fcful.cn/bnews/579298.htm
- http://m.blog.fcful.cn/bnews/85303.htm
- http://m.blog.fcful.cn/bnews/2618674.htm
- http://m.blog.fcful.cn/bnews/9357.htm
- http://m.blog.fcful.cn/bnews/718736.htm
- http://m.blog.fcful.cn/bnews/55749.htm
- http://m.blog.fcful.cn/bnews/0605365.htm
- http://m.blog.fcful.cn/bnews/41592.htm
- http://m.blog.fcful.cn/bnews/9672.htm
- http://m.blog.fcful.cn/bnews/407224.htm
- http://m.blog.fcful.cn/bnews/6946.htm
- http://m.blog.fcful.cn/bnews/711691.htm
- http://m.blog.fcful.cn/bnews/919278.htm
- http://m.blog.fcful.cn/bnews/8806.htm
- http://m.blog.fcful.cn/bnews/7789678.htm
- http://m.blog.fcful.cn/bnews/12342.htm
- http://m.blog.fcful.cn/bnews/89599.htm
- http://m.blog.fcful.cn/bnews/4132.htm
- http://m.blog.fcful.cn/bnews/16508.htm
- http://m.blog.fcful.cn/bnews/9110.htm
- http://m.blog.fcful.cn/bnews/40506.htm
- http://m.blog.fcful.cn/bnews/2956.htm
- http://m.blog.fcful.cn/bnews/7432.htm
- http://m.blog.fcful.cn/bnews/038067.htm
- http://m.blog.fcful.cn/bnews/34568.htm
- http://m.blog.fcful.cn/bnews/46148.htm
- http://m.blog.fcful.cn/bnews/6780686.htm
- http://m.blog.fcful.cn/bnews/236695.htm
- http://m.blog.fcful.cn/bnews/8988.htm
- http://m.blog.fcful.cn/bnews/04224.htm
- http://m.blog.fcful.cn/bnews/84023.htm
- http://m.blog.fcful.cn/bnews/7434410.htm
- http://m.blog.fcful.cn/bnews/3982016.htm
- http://m.blog.fcful.cn/bnews/0732.htm
- http://m.blog.fcful.cn/bnews/0604.htm
- http://m.blog.fcful.cn/bnews/6605.htm
- http://m.blog.fcful.cn/bnews/337214.htm
- http://m.blog.fcful.cn/bnews/6997.htm
- http://m.blog.fcful.cn/bnews/4593.htm
- http://m.blog.fcful.cn/bnews/7933229.htm
- http://m.blog.fcful.cn/bnews/3590086.htm
- http://m.blog.fcful.cn/bnews/0167542.htm
- http://m.blog.fcful.cn/bnews/25098.htm
- http://m.blog.fcful.cn/bnews/9259.htm
- http://m.blog.fcful.cn/bnews/873764.htm
- http://m.blog.fcful.cn/bnews/8550148.htm
- http://m.blog.fcful.cn/bnews/044839.htm
- http://m.blog.fcful.cn/bnews/8720.htm
- http://m.blog.fcful.cn/bnews/570306.htm
- http://m.blog.fcful.cn/bnews/574106.htm
- http://m.blog.fcful.cn/bnews/37723.htm
- http://m.blog.fcful.cn/bnews/479187.htm
- http://m.blog.fcful.cn/bnews/5517.htm
- http://m.blog.fcful.cn/bnews/909454.htm
- http://m.blog.fcful.cn/bnews/788816.htm
- http://m.blog.fcful.cn/bnews/6289335.htm
- http://m.blog.fcful.cn/bnews/7015738.htm
- http://m.blog.fcful.cn/bnews/7473293.htm
- http://m.blog.fcful.cn/bnews/2491.htm
- http://m.blog.fcful.cn/bnews/89017.htm
- http://m.blog.fcful.cn/bnews/2915.htm
- http://m.blog.fcful.cn/bnews/745955.htm
- http://m.blog.fcful.cn/bnews/271096.htm
- http://m.blog.fcful.cn/bnews/010056.htm
- http://m.blog.fcful.cn/bnews/75241.htm
- http://m.blog.fcful.cn/bnews/2774878.htm
- http://m.blog.fcful.cn/bnews/65481.htm
- http://m.blog.fcful.cn/bnews/3793.htm
- http://m.blog.fcful.cn/bnews/21023.htm
- http://m.blog.fcful.cn/bnews/6627.htm
- http://m.blog.fcful.cn/bnews/9013246.htm

## 项目结构

```
weblink-navigator/
├── client/                                 # 前端应用目录
│   ├── public/                             # 静态资源（favicon, manifest）
│   ├── src/
│   │   ├── components/                     # Vue 组件库
│   │   │   ├── LinkCard.vue               # 单个链接卡片组件
│   │   │   ├── CategoryFilter.vue         # 分类筛选器组件
│   │   │   └── SearchBar.vue              # 搜索输入框组件
│   │   ├── views/                          # 页面级视图
│   │   │   ├── HomePage.vue               # 首页列表与搜索
│   │   │   ├── DetailPage.vue             # 链接详情与访问统计
│   │   │   └── AdminPage.vue              # 后台管理界面
│   │   ├── stores/                         # Pinia 状态管理
│   │   │   ├── linkStore.js               # 链接数据与缓存
│   │   │   └── userStore.js               # 用户会话与权限
│   │   ├── utils/                          # 前端工具函数
│   │   │   ├── request.js                 # Axios 封装与拦截器
│   │   │   └── validator.js               # URL 校验与格式化
│   │   └── main.js                         # 前端入口文件
│   └── package.json                        # 前端依赖管理
├── server/                                 # 后端服务目录
│   ├── src/
│   │   ├── controllers/                    # 路由控制器
│   │   │   ├── linkController.js          # 链接增删改查接口
│   │   │   ├── categoryController.js      # 分类管理接口
│   │   │   └── authController.js          # 登录与鉴权接口
│   │   ├── models/                         # Mongoose 数据模型
│   │   │   ├── Link.js                    # 链接文档结构（url, title, tags, status）
│   │   │   ├── Category.js                # 分类文档结构
│   │   │   └── User.js                    # 用户文档结构（角色、密码哈希）
│   │   ├── services/                       # 业务逻辑层
│   │   │   ├── crawlerService.js          # 链接元数据抓取与更新
│   │   │   ├── healthCheckService.js      # 定时访问状态检测
│   │   │   └── searchService.js           # Elasticsearch 索引与查询
│   │   ├── middleware/                     # 中间件
│   │   │   ├── auth.js                    # JWT 令牌验证
│   │   │   └── rateLimiter.js             # API 限流配置
│   │   ├── routes/                         # 路由定义
│   │   │   ├── api.js                     # 所有 API 路由挂载
│   │   │   └── webhook.js                 # 外部回调接收端点
│   │   ├── config/                         # 配置加载
│   │   │   ├── database.js                # MongoDB 与 Redis 连接
│   │   │   └── env.js                     # 环境变量解析
│   │   └── app.js                          # Express 应用初始化
│   ├── tests/                              # 单元测试与集成测试
│   │   ├── unit/                           # 服务层与模型层测试
│   │   └── integration/                    # API 端点测试
│   └── package.json                        # 后端依赖管理
├── docs/                                   # 项目文档（入门、API、运维）
├── scripts/                                # 运维脚本
│   ├── init-db.js                          # 数据库初始化与种子数据
│   └── backup.sh                           # 定时备份脚本（cron 调用）
├── docker-compose.yml                      # 开发环境容器编排（MongoDB + Redis + ES）
├── Dockerfile                              # 生产环境镜像构建文件
├── .env.example                            # 环境变量模板（JWT_SECRET, DB_URI）
├── .gitignore                              # Git 忽略规则
├── LICENSE                                 # MIT 许可证
├── README.md                               # 项目说明文档（本文件）
└── package.json                            # 根目录聚合脚本（同时管理前后端）
```

## 贡献指南

1. 阅读项目行为准则与贡献守则，确保理解代码规范、提交信息格式（Conventional Commits）及测试覆盖率要求。所有提交需通过 ESLint 与 Prettier 检查。

2. 在 GitHub Issues 中查找标记为“good first issue”或“help wanted”的任务，或自行提出新功能提案。重大变更需先通过 Issue 与维护者讨论，避免无效工作。

3. 复刻主仓库至个人账户，在本地创建功能分支（命名格式为 feat/xxx 或 fix/xxx），完成代码实现后运行全部测试套件，确保无回归问题。

4. 提交 Pull Request 到主仓库的 develop 分支，在 PR 描述中清晰列出变更内容、测试结果及影响范围。维护者会在 3 个工作日内进行 Code Review。

5. 文档类贡献（如修正错别字、补充示例、完善 API 说明）可直接提交 PR 到 main 分支，无需创建功能分支，但仍需遵守提交信息格式。

## 常见问题

**问：导入大量链接时页面响应缓慢或超时，应该如何处理？**

答：建议使用命令行导入工具而非 Web 界面上传。项目提供了 scripts/bulk-import.js 脚本，支持分批提交（默认每批 200 条），并可通过 --delay 参数控制批次间隔。同时请检查 MongoDB 连接池大小配置，生产环境建议将 poolSize 设置为 50 以上。若链接数量超过 10 万条，推荐启用 Elasticsearch 并关闭实时索引，改为定时批量重建。

**问：访问状态检测任务误报率高，经常将正常站点标记为失效，如何优化？**

答：默认检测使用单次 GET 请求，超时时间为 5000 毫秒。对于响应较慢或存在反爬机制的站点，可在 config/default.yaml 的 healthCheck 部分调整 timeout 至 10000 毫秒，并启用 followRedirect 跟随重定向。同时可配置 retry 次数（建议 2 次）以及 userAgent 列表，轮换使用不同 UA 头。对于已知稳定的站点，可手动将其加入 whitelist 排除检测。

**问：前端页面加载时出现跨域错误，如何解决？**

答：开发环境下，前端开发服务器（默认 8080 端口）会通过 proxy 配置将 /api 请求转发至后端（默认 3000 端口），请检查 client/vue.config.js 中的 proxy 目标地址是否正确。生产环境下，建议使用 Nginx 统一处理静态资源与 API 路由，将 /api 前缀的请求代理至后端服务，其余请求返回前端构建产物。Nginx 配置示例可在 docs/operations.md 中找到。如果后端部署在非标准端口，请确保 CORS 中间件已正确配置 allowedOrigins。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
