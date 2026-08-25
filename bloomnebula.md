# WebIndexer

WebIndexer 是一个面向技术调研与信息聚合场景的轻量级外链导航与内容索引系统。该项目定位于帮助开发者、技术博主、数据分析师以及信息整理人员，将分散在多个来源的网页链接进行集中收录、分类标注与快速检索。WebIndexer 本身不存储网页正文内容，而是作为入口与索引层，提供高效的链接管理与前置信息提取能力，适用于个人知识库构建、团队共享书签库以及垂直领域信息汇总站等使用场景。

## 功能概览

**批量链接导入与解析**：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动解析域名、路径与查询参数，提取基础元数据。

**自定义标签与分类体系**：允许用户为每条链接添加多级标签和自定义分类，支持父子层级关系，便于构建符合自身逻辑的信息组织结构。

**全文检索与字段过滤**：基于导入的标题、标签、来源域名及备注字段提供全文检索功能，同时支持按日期范围、域名类型及自定义标签组合过滤。

**链接可用性监测**：内置定时检测任务，可配置周期对已收录链接进行 HTTP 状态码检查，自动标记失效或重定向链接，并提供异常报告。

**数据导出与订阅输出**：支持将索引数据导出为 JSON、CSV 及 HTML 静态页面格式，同时提供 RSS 订阅输出能力，便于与其他系统集成或公开分享。

**多用户协作与权限控制**：提供基于角色的访问控制，支持管理员、编辑者与只读查看者三种默认角色，可精细到分类目录级别的读写权限设置。

**访问统计与点击分析**：记录每条链接的点击次数、最后访问时间以及来源 IP 聚合统计，帮助识别高频使用资源与冷门内容。

## 应用场景

技术团队内部知识库管理：开发团队可将日常遇到的技术文章、官方文档、开源项目地址以及内部运维手册链接统一收录至 WebIndexer，按技术栈或业务模块分类，新成员入职时可快速获取所有必要参考资料。

垂直领域资讯聚合站：运营人员或行业分析师可以围绕特定主题，如人工智能论文、前端框架更新、云计算服务动态等，持续收集相关网页链接，通过 WebIndexer 生成带分类索引的静态门户页面，对外提供定向信息导航服务。

个人书签库迁移与增强：需要从浏览器书签系统迁移至更强大管理工具的用户，可将浏览器导出的 HTML 书签文件批量导入 WebIndexer，获得标签补全、失效检测与多维度检索能力，解决传统书签系统无法有效管理大量链接的痛点。

## 快速开始

以下命令演示了从代码仓库克隆、安装依赖到启动开发服务的完整流程。

```bash
git clone https://github.com/webindexer/webindexer.git
cd webindexer
npm install
cp .env.example .env
npm run migrate
npm run seed
npm run dev
```

执行完上述步骤后，服务默认启动于 localhost:3000，管理员初始账号密码可在 .env 文件中配置或通过种子脚本自动生成。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 Active LTS 版本 |
| PostgreSQL | 14.x 或更高版本 | 主数据库，用于存储链接元数据、标签及用户信息 |
| Redis | 7.x 或更高版本 | 缓存与任务队列后端，用于提升检索性能及调度检测任务 |
| pnpm | 8.x 或更高版本 | 包管理器，用于依赖安装与 monorepo 工作流管理 |
| Nginx | 1.22 或更高版本 | 生产环境反向代理与静态资源服务（可选但推荐） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/guide/getting-started.md | 如何快速部署并创建第一个链接索引 |
| 配置参考 | /docs/guide/configuration.md | 所有环境变量、配置文件项及其默认值说明 |
| 插件开发 | /docs/developer/plugin-dev.md | 如何编写自定义解析器与标签生成插件 |
| 部署运维 | /docs/operations/deployment.md | 生产环境部署、日志管理及备份恢复方案 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/959448.htm
- http://m.blog.gqskj.cn/nnews/9197487.htm
- http://m.blog.gqskj.cn/nnews/1866.htm
- http://m.blog.gqskj.cn/nnews/3666.htm
- http://m.blog.gqskj.cn/nnews/2399.htm
- http://m.blog.gqskj.cn/nnews/315603.htm
- http://m.blog.gqskj.cn/nnews/475728.htm
- http://m.blog.gqskj.cn/nnews/5278293.htm
- http://m.blog.gqskj.cn/nnews/5478.htm
- http://m.blog.gqskj.cn/nnews/0045982.htm
- http://m.blog.gqskj.cn/nnews/3753754.htm
- http://m.blog.gqskj.cn/nnews/55842.htm
- http://m.blog.gqskj.cn/nnews/4440119.htm
- http://m.blog.gqskj.cn/nnews/8052067.htm
- http://m.blog.gqskj.cn/nnews/98817.htm
- http://m.blog.gqskj.cn/nnews/1086663.htm
- http://m.blog.gqskj.cn/nnews/419273.htm
- http://m.blog.gqskj.cn/nnews/3880.htm
- http://m.blog.gqskj.cn/nnews/2500.htm
- http://m.blog.gqskj.cn/nnews/617943.htm
- http://m.blog.gqskj.cn/nnews/82263.htm
- http://m.blog.gqskj.cn/nnews/2042358.htm
- http://m.blog.gqskj.cn/nnews/411416.htm
- http://m.blog.gqskj.cn/nnews/96293.htm
- http://m.blog.gqskj.cn/nnews/4341521.htm
- http://m.blog.gqskj.cn/nnews/8179.htm
- http://m.blog.gqskj.cn/nnews/7219684.htm
- http://m.blog.gqskj.cn/nnews/1868.htm
- http://m.blog.gqskj.cn/nnews/51428.htm
- http://m.blog.gqskj.cn/nnews/86019.htm
- http://m.blog.gqskj.cn/nnews/96079.htm
- http://m.blog.gqskj.cn/nnews/985353.htm
- http://m.blog.gqskj.cn/nnews/00080.htm
- http://m.blog.gqskj.cn/nnews/66647.htm
- http://m.blog.gqskj.cn/nnews/497165.htm
- http://m.blog.gqskj.cn/nnews/1102.htm
- http://m.blog.gqskj.cn/nnews/168022.htm
- http://m.blog.gqskj.cn/nnews/2860.htm
- http://m.blog.gqskj.cn/nnews/612142.htm
- http://m.blog.gqskj.cn/nnews/307688.htm
- http://m.blog.gqskj.cn/nnews/5356247.htm
- http://m.blog.gqskj.cn/nnews/3652287.htm
- http://m.blog.gqskj.cn/nnews/8406478.htm
- http://m.blog.gqskj.cn/nnews/28826.htm
- http://m.blog.gqskj.cn/nnews/12110.htm
- http://m.blog.gqskj.cn/nnews/58735.htm
- http://m.blog.gqskj.cn/nnews/97385.htm
- http://m.blog.gqskj.cn/nnews/351858.htm
- http://m.blog.gqskj.cn/nnews/4670919.htm
- http://m.blog.gqskj.cn/nnews/63574.htm
- http://m.blog.gqskj.cn/nnews/6094155.htm
- http://m.blog.gqskj.cn/nnews/23605.htm
- http://m.blog.gqskj.cn/nnews/32143.htm
- http://m.blog.gqskj.cn/nnews/43416.htm
- http://m.blog.gqskj.cn/nnews/48865.htm
- http://m.blog.gqskj.cn/nnews/2011.htm
- http://m.blog.gqskj.cn/nnews/94433.htm
- http://m.blog.gqskj.cn/nnews/2725996.htm
- http://m.blog.gqskj.cn/nnews/7836.htm
- http://m.blog.gqskj.cn/nnews/0719.htm
- http://m.blog.gqskj.cn/nnews/6993.htm
- http://m.blog.gqskj.cn/nnews/8425.htm
- http://m.blog.gqskj.cn/nnews/88397.htm
- http://m.blog.gqskj.cn/nnews/8601.htm
- http://m.blog.gqskj.cn/nnews/42495.htm
- http://m.blog.gqskj.cn/nnews/278320.htm
- http://m.blog.gqskj.cn/nnews/1318161.htm
- http://m.blog.gqskj.cn/nnews/884074.htm
- http://m.blog.gqskj.cn/nnews/5810144.htm
- http://m.blog.gqskj.cn/nnews/9034846.htm
- http://m.blog.gqskj.cn/nnews/0638.htm
- http://m.blog.gqskj.cn/nnews/5096318.htm
- http://m.blog.gqskj.cn/nnews/8752.htm
- http://m.blog.gqskj.cn/nnews/9878.htm
- http://m.blog.gqskj.cn/nnews/8105431.htm
- http://m.blog.gqskj.cn/nnews/3837106.htm
- http://m.blog.gqskj.cn/nnews/512071.htm
- http://m.blog.gqskj.cn/nnews/666621.htm
- http://m.blog.gqskj.cn/nnews/3596277.htm
- http://m.blog.gqskj.cn/nnews/5106484.htm
- http://m.blog.gqskj.cn/nnews/7352.htm
- http://m.blog.gqskj.cn/nnews/2970562.htm
- http://m.blog.gqskj.cn/nnews/408571.htm
- http://m.blog.gqskj.cn/nnews/087373.htm
- http://m.blog.gqskj.cn/nnews/3995503.htm
- http://m.blog.gqskj.cn/nnews/513325.htm
- http://m.blog.gqskj.cn/nnews/118011.htm
- http://m.blog.gqskj.cn/nnews/9063296.htm
- http://m.blog.gqskj.cn/nnews/7841290.htm
- http://m.blog.gqskj.cn/nnews/05895.htm
- http://m.blog.gqskj.cn/nnews/6392.htm
- http://m.blog.gqskj.cn/nnews/7477.htm
- http://m.blog.gqskj.cn/nnews/17121.htm
- http://m.blog.gqskj.cn/nnews/510293.htm
- http://m.blog.gqskj.cn/nnews/5750350.htm
- http://m.blog.gqskj.cn/nnews/3521816.htm
- http://m.blog.gqskj.cn/nnews/9574751.htm
- http://m.blog.gqskj.cn/nnews/08172.htm
- http://m.blog.gqskj.cn/nnews/843871.htm
- http://m.blog.gqskj.cn/nnews/70080.htm
- http://m.blog.gqskj.cn/nnews/4301578.htm
- http://m.blog.gqskj.cn/nnews/5118.htm
- http://m.blog.gqskj.cn/nnews/44944.htm
- http://m.blog.gqskj.cn/nnews/216749.htm
- http://m.blog.gqskj.cn/nnews/27424.htm
- http://m.blog.gqskj.cn/nnews/3975.htm
- http://m.blog.gqskj.cn/nnews/4310604.htm
- http://m.blog.gqskj.cn/nnews/2425246.htm
- http://m.blog.gqskj.cn/nnews/4216.htm
- http://m.blog.gqskj.cn/nnews/1345.htm
- http://m.blog.gqskj.cn/nnews/06553.htm
- http://m.blog.gqskj.cn/nnews/3485.htm
- http://m.blog.gqskj.cn/nnews/054643.htm
- http://m.blog.gqskj.cn/nnews/871981.htm
- http://m.blog.gqskj.cn/nnews/0765543.htm
- http://m.blog.gqskj.cn/nnews/04217.htm
- http://m.blog.gqskj.cn/nnews/5070028.htm
- http://m.blog.gqskj.cn/nnews/520339.htm
- http://m.blog.gqskj.cn/nnews/1049375.htm
- http://m.blog.gqskj.cn/nnews/905136.htm
- http://m.blog.gqskj.cn/nnews/35596.htm
- http://m.blog.gqskj.cn/nnews/27243.htm
- http://m.blog.gqskj.cn/nnews/9670.htm
- http://m.blog.gqskj.cn/nnews/8313291.htm
- http://m.blog.gqskj.cn/nnews/4557.htm
- http://m.blog.gqskj.cn/nnews/10156.htm
- http://m.blog.gqskj.cn/nnews/2510.htm
- http://m.blog.gqskj.cn/nnews/8113212.htm
- http://m.blog.gqskj.cn/nnews/7315971.htm
- http://m.blog.gqskj.cn/nnews/6478505.htm
- http://m.blog.gqskj.cn/nnews/4860739.htm
- http://m.blog.gqskj.cn/nnews/6942.htm
- http://m.blog.gqskj.cn/nnews/8814.htm
- http://m.blog.gqskj.cn/nnews/625236.htm
- http://m.blog.gqskj.cn/nnews/8986744.htm
- http://m.blog.gqskj.cn/nnews/840660.htm
- http://m.blog.gqskj.cn/nnews/0436208.htm
- http://m.blog.gqskj.cn/nnews/5974.htm
- http://m.blog.gqskj.cn/nnews/6497.htm
- http://m.blog.gqskj.cn/nnews/4237.htm
- http://m.blog.gqskj.cn/nnews/1047.htm
- http://m.blog.gqskj.cn/nnews/671633.htm
- http://m.blog.gqskj.cn/nnews/8502.htm
- http://m.blog.gqskj.cn/nnews/8653.htm
- http://m.blog.gqskj.cn/nnews/55855.htm
- http://m.blog.gqskj.cn/nnews/5471.htm
- http://m.blog.gqskj.cn/nnews/6789.htm
- http://m.blog.gqskj.cn/nnews/713923.htm
- http://m.blog.gqskj.cn/nnews/08725.htm
- http://m.blog.gqskj.cn/nnews/2305530.htm
- http://m.blog.gqskj.cn/nnews/14534.htm
- http://m.blog.gqskj.cn/nnews/772431.htm
- http://m.blog.gqskj.cn/nnews/3127431.htm
- http://m.blog.gqskj.cn/nnews/5545.htm
- http://m.blog.gqskj.cn/nnews/6961547.htm
- http://m.blog.gqskj.cn/nnews/176765.htm
- http://m.blog.gqskj.cn/nnews/5345.htm
- http://m.blog.gqskj.cn/nnews/9804290.htm
- http://m.blog.gqskj.cn/nnews/5559412.htm
- http://m.blog.gqskj.cn/nnews/757296.htm
- http://m.blog.gqskj.cn/nnews/0372658.htm
- http://m.blog.gqskj.cn/nnews/2627280.htm
- http://m.blog.gqskj.cn/nnews/0966321.htm
- http://m.blog.gqskj.cn/nnews/96823.htm
- http://m.blog.gqskj.cn/nnews/0295311.htm
- http://m.blog.gqskj.cn/nnews/26895.htm
- http://m.blog.gqskj.cn/nnews/79230.htm
- http://m.blog.gqskj.cn/nnews/28973.htm
- http://m.blog.gqskj.cn/nnews/2094385.htm
- http://m.blog.gqskj.cn/nnews/50590.htm
- http://m.blog.gqskj.cn/nnews/14846.htm
- http://m.blog.gqskj.cn/nnews/233337.htm
- http://m.blog.gqskj.cn/nnews/868723.htm
- http://m.blog.gqskj.cn/nnews/668835.htm
- http://m.blog.gqskj.cn/nnews/9622711.htm
- http://m.blog.gqskj.cn/nnews/4705758.htm
- http://m.blog.gqskj.cn/nnews/30447.htm
- http://m.blog.gqskj.cn/nnews/9963.htm
- http://m.blog.gqskj.cn/nnews/69255.htm
- http://m.blog.gqskj.cn/nnews/9408842.htm
- http://m.blog.gqskj.cn/nnews/4660829.htm
- http://m.blog.gqskj.cn/nnews/5998766.htm
- http://m.blog.gqskj.cn/nnews/718257.htm
- http://m.blog.gqskj.cn/nnews/1049.htm
- http://m.blog.gqskj.cn/nnews/38293.htm
- http://m.blog.gqskj.cn/nnews/687160.htm
- http://m.blog.gqskj.cn/nnews/65401.htm
- http://m.blog.gqskj.cn/nnews/176002.htm
- http://m.blog.gqskj.cn/nnews/86238.htm
- http://m.blog.gqskj.cn/nnews/400555.htm
- http://m.blog.gqskj.cn/nnews/03869.htm
- http://m.blog.gqskj.cn/nnews/9546671.htm
- http://m.blog.gqskj.cn/nnews/36260.htm
- http://m.blog.gqskj.cn/nnews/475153.htm
- http://m.blog.gqskj.cn/nnews/59060.htm
- http://m.blog.gqskj.cn/nnews/3133799.htm
- http://m.blog.gqskj.cn/nnews/0779138.htm
- http://m.blog.gqskj.cn/nnews/8296.htm
- http://m.blog.gqskj.cn/nnews/9728.htm
- http://m.blog.gqskj.cn/nnews/66978.htm
- http://m.blog.gqskj.cn/nnews/37741.htm
- http://m.blog.gqskj.cn/nnews/4148235.htm
- http://m.blog.gqskj.cn/nnews/57000.htm
- http://m.blog.gqskj.cn/nnews/20825.htm
- http://m.blog.gqskj.cn/nnews/675125.htm
- http://m.blog.gqskj.cn/nnews/3592.htm
- http://m.blog.gqskj.cn/nnews/7306.htm
- http://m.blog.gqskj.cn/nnews/39353.htm
- http://m.blog.gqskj.cn/nnews/0679693.htm
- http://m.blog.gqskj.cn/nnews/885163.htm
- http://m.blog.gqskj.cn/nnews/99575.htm
- http://m.blog.gqskj.cn/nnews/7616888.htm
- http://m.blog.gqskj.cn/nnews/30385.htm
- http://m.blog.gqskj.cn/nnews/23658.htm
- http://m.blog.gqskj.cn/nnews/5451973.htm
- http://m.blog.gqskj.cn/nnews/720747.htm
- http://m.blog.gqskj.cn/nnews/03433.htm
- http://m.blog.gqskj.cn/nnews/679684.htm
- http://m.blog.gqskj.cn/nnews/401773.htm
- http://m.blog.gqskj.cn/nnews/97954.htm
- http://m.blog.gqskj.cn/nnews/952288.htm
- http://m.blog.gqskj.cn/nnews/8522.htm
- http://m.blog.gqskj.cn/nnews/184042.htm
- http://m.blog.gqskj.cn/nnews/37311.htm
- http://m.blog.gqskj.cn/nnews/334479.htm
- http://m.blog.gqskj.cn/nnews/369726.htm
- http://m.blog.gqskj.cn/nnews/0944.htm
- http://m.blog.gqskj.cn/nnews/3682680.htm
- http://m.blog.gqskj.cn/nnews/57933.htm
- http://m.blog.gqskj.cn/nnews/7113409.htm
- http://m.blog.gqskj.cn/nnews/9232389.htm
- http://m.blog.gqskj.cn/nnews/1246.htm
- http://m.blog.gqskj.cn/nnews/74288.htm
- http://m.blog.gqskj.cn/nnews/03413.htm
- http://m.blog.gqskj.cn/nnews/46470.htm
- http://m.blog.gqskj.cn/nnews/4118.htm
- http://m.blog.gqskj.cn/nnews/5913.htm
- http://m.blog.gqskj.cn/nnews/83736.htm
- http://m.blog.gqskj.cn/nnews/2805.htm
- http://m.blog.gqskj.cn/nnews/5114661.htm
- http://m.blog.gqskj.cn/nnews/8213693.htm
- http://m.blog.gqskj.cn/nnews/2840308.htm
- http://m.blog.gqskj.cn/nnews/854009.htm
- http://m.blog.gqskj.cn/nnews/81405.htm
- http://m.blog.gqskj.cn/nnews/00293.htm
- http://m.blog.gqskj.cn/nnews/762234.htm
- http://m.blog.gqskj.cn/nnews/0275.htm
- http://m.blog.gqskj.cn/nnews/1641632.htm
- http://m.blog.gqskj.cn/nnews/4113973.htm
- http://m.blog.gqskj.cn/nnews/3216.htm

## 项目结构

```
webindexer/
├── apps/
│   ├── api/                           # 后端服务（Node.js + Fastify）
│   │   ├── src/
│   │   │   ├── controllers/           # 请求控制器，处理路由逻辑
│   │   │   ├── services/              # 核心业务逻辑层（链接管理、检测、统计）
│   │   │   ├── models/                # 数据库模型定义（Prisma ORM）
│   │   │   ├── queues/                # 任务队列定义（BullMQ + Redis）
│   │   │   └── validators/            # 请求参数校验器（JSON Schema）
│   │   └── tests/                     # 单元测试与集成测试
│   └── web/                           # 前端界面（React + Next.js）
│       ├── components/                # 可复用 UI 组件（表格、表单、过滤器）
│       ├── pages/                     # 路由页面（仪表盘、链接列表、设置页）
│       ├── hooks/                     # 自定义 React Hooks（数据请求与状态管理）
│       └── styles/                    # 全局样式与主题变量
├── packages/
│   ├── shared-types/                  # 前后端共享 TypeScript 类型定义
│   ├── link-parser/                   # 独立链接解析工具包（URL 规范化、元数据提取）
│   └── health-checker/                # 链接可用性检测核心模块（可独立运行）
├── docker/                            # Docker 编排文件（开发与生产环境配置）
│   ├── Dockerfile.api
│   ├── Dockerfile.web
│   └── docker-compose.yml
├── docs/                              # 完整文档源文件（Markdown + 架构图）
├── scripts/                           # 运维与工具脚本（数据库备份、种子数据生成）
├── .env.example                       # 环境变量配置模板
├── package.json                       # 根目录包管理配置（pnpm workspace）
├── pnpm-workspace.yaml                # pnpm 工作区定义
└── README.md                          # 项目入口文档
```

## 贡献指南

1. 阅读项目行为准则与贡献规范文档，确保理解社区协作流程与代码提交要求。所有贡献者需签署开发者原创声明，确认所提交代码无版权争议。

2. 在 GitHub Issues 中查找标记为 help-wanted 或 good-first-issue 的待办事项，或提交新议题描述你发现的问题或希望新增的功能，等待维护者确认后再开始编码。

3. 派生项目仓库至个人账户，在派生副本中创建功能分支，分支命名遵循 feat/功能名 或 fix/问题编号 的格式。开发过程中请遵循 ESLint 与 Prettier 配置的代码风格。

4. 完成代码编写后，确保通过全部现有单元测试，并为新增功能或修复内容补充对应的测试用例。执行 pnpm test 命令验证本地所有检查通过。

5. 向原始仓库的主分支发起拉取请求，在请求描述中清晰关联相关议题编号，列出变更摘要与测试结果。等待至少一名维护者审核，并根据反馈意见进行修改直至合并。

## 常见问题

**问：WebIndexer 能否直接抓取并存储网页正文内容？**

答：WebIndexer 设计为纯索引层，不主动抓取或存储网页正文。系统仅保存用户提交的 URL、标题、描述（用户手动填写）以及系统自动提取的基础元数据。若需要全文检索网页内容，建议搭配第三方搜索引擎 API 或浏览器扩展实现二次跳转检索。

**问：链接可用性检测会影响目标网站的正常访问吗？**

答：检测模块采用低频次、小并发策略，默认每 24 小时检测一次所有链接，单次检测间隔不低于 200 毫秒，且遵循 robots.txt 协议。该频率远低于普通爬虫，不会对目标服务器造成压力。用户也可在配置文件中调整检测频率或完全关闭该功能。

**问：如何将现有浏览器书签迁移至 WebIndexer？**

答：从 Chrome、Firefox 或 Edge 浏览器导出 HTML 格式书签文件后，在 WebIndexer 后台的「批量导入」功能中选择书签导入选项，系统会自动解析书签目录结构为分类标签，并提取每个书签的标题与 URL。导入完成后可进一步手动整理和补充备注信息。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:44
