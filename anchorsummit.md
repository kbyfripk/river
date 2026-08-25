# WebFront Navigator

WebFront Navigator 是一个面向前端开发者和技术内容策展人的轻量级技术资讯聚合与导航工具。该项目定位于将分散在互联网各处的技术博客、新闻快讯、版本发布公告和社区讨论贴进行结构化归集，并提供基于标签和全文检索的快速筛选能力。目标用户包括需要每日跟进前端生态变化的技术 leader、维护团队知识库的文档工程师以及希望系统化阅读技术文章的个人开发者。WebFront Navigator 不生产内容，而是通过可配置的数据源接入机制，帮助用户在信息过载的环境中建立高效、可定制的阅读工作流。

## 功能概览

**多源数据接入**：支持通过 JSON 配置接入外部 RSS 源、静态 HTML 列表或结构化 API，内置对常见技术博客和新闻站点的默认解析规则。

**全文检索与过滤**：基于倒排索引提供标题、正文和标签维度的关键词检索，并支持按发布时间、来源域名和阅读状态进行组合过滤。

**标签自动提取**：对每条外链内容进行分词和频率统计，自动生成相关性标签，降低人工打标成本。

**阅读状态管理**：提供已读、未读、收藏和稍后阅读四种状态标记，所有状态存储在本地 SQLite 数据库中，支持多设备同步（需配合自建后端）。

**自定义订阅源**：允许用户通过 YAML 配置文件添加自定义订阅源，并设置抓取频率和内容过滤规则。

**外部链接健康检查**：定时对已收录的外链进行 HTTP 状态码检测，标记失效链接并生成报告，便于策展人及时清理或更新。

**数据导入与导出**：支持将当前收藏和订阅配置导出为 JSON 或 CSV 格式，便于备份或迁移到其他工具。

**暗色主题与阅读模式**：内置明暗两套 UI 主题，并针对技术文章提供去侧边栏、去广告的沉浸式阅读模式。

## 应用场景

**个人技术阅读工作流**：开发者每日早晨通过 WebFront Navigator 查看订阅的五个主要前端技术博客的最新文章，利用全文检索快速定位与当前项目相关的 React 或 Vue 内容，将感兴趣的文章加入稍后阅读列表，在通勤时间集中阅读。

**团队技术周报生成**：技术团队的文档负责人每周五使用本工具的标签过滤和时间范围筛选功能，导出本周收录的高质量外链清单，并附带自动生成的摘要标签，作为团队周报的技术参考附录。

**技术内容归档与检索**：社区运营人员将历史发布的数千篇活动公告和教程链接导入 WebFront Navigator，利用全文检索和标签系统快速检索特定版本或特定主题的内容，提升内容复用效率。

**外链监控与失效修复**：大型技术文档站点的维护者使用健康检查功能，定期扫描站内所有外部引用链接，获取失效链接列表并批量更新或移除，保障文档质量。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动开发服务器。

```bash
# 克隆仓库
git clone https://github.com/webfront-navigator/webfront-navigator.git
cd webfront-navigator

# 安装依赖（使用 npm）
npm install

# 初始化数据库和默认配置
npm run init

# 启动开发服务器（默认监听 http://localhost:3000）
npm run dev
```

生产环境部署请参考 `docs/deployment.md` 文档，推荐使用 PM2 或 Docker 方式运行。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，推荐使用 LTS 版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.38.0 或更高 | 嵌入式数据库，用于存储链接元数据和状态 |
| Python（可选） | 3.10 或更高 | 仅当启用自动标签提取的 NLP 增强模式时需要 |
| 内存 | 最低 512MB，推荐 1GB | 开发环境下内存占用约为 300MB，生产环境建议 1GB |
| 磁盘 | 最低 200MB | 用于存储数据库文件和日志，实际占用随收录链接数量线性增长 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | `docs/user-guide/` | 如何添加订阅源、如何检索和过滤、如何导入导出数据 |
| 配置参考 | `docs/config-reference/` | YAML 配置文件的完整字段说明、示例和默认值 |
| 开发文档 | `docs/developer/` | 插件开发规范、API 接口文档、数据库 Schema 设计 |
| 运维手册 | `docs/operations/` | 生产环境部署步骤、性能调优参数、备份与恢复方案 |

## 资源列表

- http://m.blog.fcful.cn/bnews/61510.htm
- http://m.blog.fcful.cn/bnews/28254.htm
- http://m.blog.fcful.cn/bnews/80348.htm
- http://m.blog.fcful.cn/bnews/1338290.htm
- http://m.blog.fcful.cn/bnews/44828.htm
- http://m.blog.fcful.cn/bnews/8750.htm
- http://m.blog.fcful.cn/bnews/65190.htm
- http://m.blog.fcful.cn/bnews/01401.htm
- http://m.blog.fcful.cn/bnews/899719.htm
- http://m.blog.fcful.cn/bnews/4099231.htm
- http://m.blog.fcful.cn/bnews/64531.htm
- http://m.blog.fcful.cn/bnews/413165.htm
- http://m.blog.fcful.cn/bnews/68971.htm
- http://m.blog.fcful.cn/bnews/2610.htm
- http://m.blog.fcful.cn/bnews/76802.htm
- http://m.blog.fcful.cn/bnews/9648.htm
- http://m.blog.fcful.cn/bnews/9785448.htm
- http://m.blog.fcful.cn/bnews/5299296.htm
- http://m.blog.fcful.cn/bnews/0707.htm
- http://m.blog.fcful.cn/bnews/190397.htm
- http://m.blog.fcful.cn/bnews/6232488.htm
- http://m.blog.fcful.cn/bnews/0458191.htm
- http://m.blog.fcful.cn/bnews/9686.htm
- http://m.blog.fcful.cn/bnews/7933.htm
- http://m.blog.fcful.cn/bnews/90267.htm
- http://m.blog.fcful.cn/bnews/533123.htm
- http://m.blog.fcful.cn/bnews/4960.htm
- http://m.blog.fcful.cn/bnews/14527.htm
- http://m.blog.fcful.cn/bnews/9805.htm
- http://m.blog.fcful.cn/bnews/41696.htm
- http://m.blog.fcful.cn/bnews/936359.htm
- http://m.blog.fcful.cn/bnews/520723.htm
- http://m.blog.fcful.cn/bnews/319833.htm
- http://m.blog.fcful.cn/bnews/1482.htm
- http://m.blog.fcful.cn/bnews/89837.htm
- http://m.blog.fcful.cn/bnews/8317248.htm
- http://m.blog.fcful.cn/bnews/7456841.htm
- http://m.blog.fcful.cn/bnews/19439.htm
- http://m.blog.fcful.cn/bnews/535640.htm
- http://m.blog.fcful.cn/bnews/73080.htm
- http://m.blog.fcful.cn/bnews/341097.htm
- http://m.blog.fcful.cn/bnews/830460.htm
- http://m.blog.fcful.cn/bnews/2245.htm
- http://m.blog.fcful.cn/bnews/35718.htm
- http://m.blog.fcful.cn/bnews/08295.htm
- http://m.blog.fcful.cn/bnews/0067.htm
- http://m.blog.fcful.cn/bnews/6470.htm
- http://m.blog.fcful.cn/bnews/99281.htm
- http://m.blog.fcful.cn/bnews/1937.htm
- http://m.blog.fcful.cn/bnews/3991.htm
- http://m.blog.fcful.cn/bnews/5002.htm
- http://m.blog.fcful.cn/bnews/5420.htm
- http://m.blog.fcful.cn/bnews/8077842.htm
- http://m.blog.fcful.cn/bnews/6821.htm
- http://m.blog.fcful.cn/bnews/254776.htm
- http://m.blog.fcful.cn/bnews/12023.htm
- http://m.blog.fcful.cn/bnews/1754491.htm
- http://m.blog.fcful.cn/bnews/41450.htm
- http://m.blog.fcful.cn/bnews/404548.htm
- http://m.blog.fcful.cn/bnews/209221.htm
- http://m.blog.fcful.cn/bnews/376586.htm
- http://m.blog.fcful.cn/bnews/01778.htm
- http://m.blog.fcful.cn/bnews/22398.htm
- http://m.blog.fcful.cn/bnews/72270.htm
- http://m.blog.fcful.cn/bnews/333658.htm
- http://m.blog.fcful.cn/bnews/3701090.htm
- http://m.blog.fcful.cn/bnews/99969.htm
- http://m.blog.fcful.cn/bnews/570421.htm
- http://m.blog.fcful.cn/bnews/4894.htm
- http://m.blog.fcful.cn/bnews/53033.htm
- http://m.blog.fcful.cn/bnews/3754683.htm
- http://m.blog.fcful.cn/bnews/551435.htm
- http://m.blog.fcful.cn/bnews/02032.htm
- http://m.blog.fcful.cn/bnews/3244090.htm
- http://m.blog.fcful.cn/bnews/443466.htm
- http://m.blog.fcful.cn/bnews/2674.htm
- http://m.blog.fcful.cn/bnews/63629.htm
- http://m.blog.fcful.cn/bnews/92221.htm
- http://m.blog.fcful.cn/bnews/2007.htm
- http://m.blog.fcful.cn/bnews/08737.htm
- http://m.blog.fcful.cn/bnews/3364611.htm
- http://m.blog.fcful.cn/bnews/02156.htm
- http://m.blog.fcful.cn/bnews/8179.htm
- http://m.blog.fcful.cn/bnews/7882238.htm
- http://m.blog.fcful.cn/bnews/19300.htm
- http://m.blog.fcful.cn/bnews/4956.htm
- http://m.blog.fcful.cn/bnews/66153.htm
- http://m.blog.fcful.cn/bnews/9301445.htm
- http://m.blog.fcful.cn/bnews/0775088.htm
- http://m.blog.fcful.cn/bnews/9981.htm
- http://m.blog.fcful.cn/bnews/8276.htm
- http://m.blog.fcful.cn/bnews/4561861.htm
- http://m.blog.fcful.cn/bnews/3335688.htm
- http://m.blog.fcful.cn/bnews/4993735.htm
- http://m.blog.fcful.cn/bnews/28141.htm
- http://m.blog.fcful.cn/bnews/13425.htm
- http://m.blog.fcful.cn/bnews/553334.htm
- http://m.blog.fcful.cn/bnews/9549.htm
- http://m.blog.fcful.cn/bnews/655169.htm
- http://m.blog.fcful.cn/bnews/267256.htm
- http://m.blog.fcful.cn/bnews/447793.htm
- http://m.blog.fcful.cn/bnews/573769.htm
- http://m.blog.fcful.cn/bnews/15674.htm
- http://m.blog.fcful.cn/bnews/8840.htm
- http://m.blog.fcful.cn/bnews/26562.htm
- http://m.blog.fcful.cn/bnews/2039876.htm
- http://m.blog.fcful.cn/bnews/456613.htm
- http://m.blog.fcful.cn/bnews/4633.htm
- http://m.blog.fcful.cn/bnews/707463.htm
- http://m.blog.fcful.cn/bnews/99574.htm
- http://m.blog.fcful.cn/bnews/345099.htm
- http://m.blog.fcful.cn/bnews/170785.htm
- http://m.blog.fcful.cn/bnews/9255179.htm
- http://m.blog.fcful.cn/bnews/2572158.htm
- http://m.blog.fcful.cn/bnews/88979.htm
- http://m.blog.fcful.cn/bnews/03531.htm
- http://m.blog.fcful.cn/bnews/8731.htm
- http://m.blog.fcful.cn/bnews/2266.htm
- http://m.blog.fcful.cn/bnews/11407.htm
- http://m.blog.fcful.cn/bnews/623167.htm
- http://m.blog.fcful.cn/bnews/44986.htm
- http://m.blog.fcful.cn/bnews/268483.htm
- http://m.blog.fcful.cn/bnews/949461.htm
- http://m.blog.fcful.cn/bnews/42004.htm
- http://m.blog.fcful.cn/bnews/612273.htm
- http://m.blog.fcful.cn/bnews/8110619.htm
- http://m.blog.fcful.cn/bnews/1447.htm
- http://m.blog.fcful.cn/bnews/5603415.htm
- http://m.blog.fcful.cn/bnews/3016.htm
- http://m.blog.fcful.cn/bnews/291844.htm
- http://m.blog.fcful.cn/bnews/9200051.htm
- http://m.blog.fcful.cn/bnews/0814505.htm
- http://m.blog.fcful.cn/bnews/977735.htm
- http://m.blog.fcful.cn/bnews/46699.htm
- http://m.blog.fcful.cn/bnews/6709661.htm
- http://m.blog.fcful.cn/bnews/4964.htm
- http://m.blog.fcful.cn/bnews/35895.htm
- http://m.blog.fcful.cn/bnews/6685412.htm
- http://m.blog.fcful.cn/bnews/15315.htm
- http://m.blog.fcful.cn/bnews/98341.htm
- http://m.blog.fcful.cn/bnews/3662.htm
- http://m.blog.fcful.cn/bnews/0493.htm
- http://m.blog.fcful.cn/bnews/5099191.htm
- http://m.blog.fcful.cn/bnews/1561.htm
- http://m.blog.fcful.cn/bnews/1360.htm
- http://m.blog.fcful.cn/bnews/8839109.htm
- http://m.blog.fcful.cn/bnews/615120.htm
- http://m.blog.fcful.cn/bnews/9061.htm
- http://m.blog.fcful.cn/bnews/6309662.htm
- http://m.blog.fcful.cn/bnews/31050.htm
- http://m.blog.fcful.cn/bnews/318446.htm
- http://m.blog.fcful.cn/bnews/594553.htm
- http://m.blog.fcful.cn/bnews/6073.htm
- http://m.blog.fcful.cn/bnews/7923.htm
- http://m.blog.fcful.cn/bnews/030578.htm
- http://m.blog.fcful.cn/bnews/805018.htm
- http://m.blog.fcful.cn/bnews/9143.htm
- http://m.blog.fcful.cn/bnews/73357.htm
- http://m.blog.fcful.cn/bnews/408285.htm
- http://m.blog.fcful.cn/bnews/447248.htm
- http://m.blog.fcful.cn/bnews/591616.htm
- http://m.blog.fcful.cn/bnews/31697.htm
- http://m.blog.fcful.cn/bnews/702819.htm
- http://m.blog.fcful.cn/bnews/1518146.htm
- http://m.blog.fcful.cn/bnews/1246.htm
- http://m.blog.fcful.cn/bnews/5711.htm
- http://m.blog.fcful.cn/bnews/7137.htm
- http://m.blog.fcful.cn/bnews/286526.htm
- http://m.blog.fcful.cn/bnews/6925286.htm
- http://m.blog.fcful.cn/bnews/65078.htm
- http://m.blog.fcful.cn/bnews/382339.htm
- http://m.blog.fcful.cn/bnews/6783377.htm
- http://m.blog.fcful.cn/bnews/523275.htm
- http://m.blog.fcful.cn/bnews/3947.htm
- http://m.blog.fcful.cn/bnews/909251.htm
- http://m.blog.fcful.cn/bnews/172880.htm
- http://m.blog.fcful.cn/bnews/0203.htm
- http://m.blog.fcful.cn/bnews/687331.htm
- http://m.blog.fcful.cn/bnews/8078467.htm
- http://m.blog.fcful.cn/bnews/087895.htm
- http://m.blog.fcful.cn/bnews/96931.htm
- http://m.blog.fcful.cn/bnews/68859.htm
- http://m.blog.fcful.cn/bnews/2753863.htm
- http://m.blog.fcful.cn/bnews/58808.htm
- http://m.blog.fcful.cn/bnews/376742.htm
- http://m.blog.fcful.cn/bnews/27784.htm
- http://m.blog.fcful.cn/bnews/82834.htm
- http://m.blog.fcful.cn/bnews/1973085.htm
- http://m.blog.fcful.cn/bnews/47166.htm
- http://m.blog.fcful.cn/bnews/04325.htm
- http://m.blog.fcful.cn/bnews/657226.htm
- http://m.blog.fcful.cn/bnews/95777.htm
- http://m.blog.fcful.cn/bnews/60840.htm
- http://m.blog.fcful.cn/bnews/6840.htm
- http://m.blog.fcful.cn/bnews/4232848.htm
- http://m.blog.fcful.cn/bnews/8890555.htm
- http://m.blog.fcful.cn/bnews/80276.htm
- http://m.blog.fcful.cn/bnews/463696.htm
- http://m.blog.fcful.cn/bnews/26721.htm
- http://m.blog.fcful.cn/bnews/377866.htm
- http://m.blog.fcful.cn/bnews/9178.htm
- http://m.blog.fcful.cn/bnews/2765130.htm
- http://m.blog.fcful.cn/bnews/17560.htm
- http://m.blog.fcful.cn/bnews/8579876.htm
- http://m.blog.fcful.cn/bnews/28027.htm
- http://m.blog.fcful.cn/bnews/5617225.htm
- http://m.blog.fcful.cn/bnews/4228.htm
- http://m.blog.fcful.cn/bnews/7434123.htm
- http://m.blog.fcful.cn/bnews/7019530.htm
- http://m.blog.fcful.cn/bnews/0676043.htm
- http://m.blog.fcful.cn/bnews/02204.htm
- http://m.blog.fcful.cn/bnews/024793.htm
- http://m.blog.fcful.cn/bnews/1508.htm
- http://m.blog.fcful.cn/bnews/92230.htm
- http://m.blog.fcful.cn/bnews/30615.htm
- http://m.blog.fcful.cn/bnews/4296.htm
- http://m.blog.fcful.cn/bnews/494973.htm
- http://m.blog.fcful.cn/bnews/1609.htm
- http://m.blog.fcful.cn/bnews/1227563.htm
- http://m.blog.fcful.cn/bnews/93480.htm
- http://m.blog.fcful.cn/bnews/2428.htm
- http://m.blog.fcful.cn/bnews/950741.htm
- http://m.blog.fcful.cn/bnews/1656.htm
- http://m.blog.fcful.cn/bnews/796510.htm
- http://m.blog.fcful.cn/bnews/467422.htm
- http://m.blog.fcful.cn/bnews/502405.htm
- http://m.blog.fcful.cn/bnews/1601197.htm
- http://m.blog.fcful.cn/bnews/8708.htm
- http://m.blog.fcful.cn/bnews/12512.htm
- http://m.blog.fcful.cn/bnews/633169.htm
- http://m.blog.fcful.cn/bnews/28780.htm
- http://m.blog.fcful.cn/bnews/19312.htm
- http://m.blog.fcful.cn/bnews/7540108.htm
- http://m.blog.fcful.cn/bnews/06171.htm
- http://m.blog.fcful.cn/bnews/47831.htm
- http://m.blog.fcful.cn/bnews/197499.htm
- http://m.blog.fcful.cn/bnews/3515371.htm
- http://m.blog.fcful.cn/bnews/6437.htm
- http://m.blog.fcful.cn/bnews/18601.htm
- http://m.blog.fcful.cn/bnews/9855191.htm
- http://m.blog.fcful.cn/bnews/483325.htm
- http://m.blog.fcful.cn/bnews/35725.htm
- http://m.blog.fcful.cn/bnews/561193.htm
- http://m.blog.fcful.cn/bnews/5335394.htm
- http://m.blog.fcful.cn/bnews/85110.htm
- http://m.blog.fcful.cn/bnews/8242.htm
- http://m.blog.fcful.cn/bnews/182329.htm
- http://m.blog.fcful.cn/bnews/003103.htm
- http://m.blog.fcful.cn/bnews/6176842.htm
- http://m.blog.fcful.cn/bnews/6112787.htm

## 项目结构

项目采用模块化分层架构，核心目录及功能说明如下。

```
webfront-navigator/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心引擎模块
│   │   ├── crawler.js             # 抓取调度器，管理定时任务和并发请求
│   │   ├── parser.js              # 内容解析器，支持 RSS/HTML/JSON 格式
│   │   └── indexer.js             # 倒排索引构建与检索接口
│   ├── storage/                   # 存储层
│   │   ├── database.js            # SQLite 连接池与 CRUD 操作
│   │   ├── models/                # 数据模型定义（Link, Tag, State）
│   │   └── migrations/            # 数据库迁移脚本
│   ├── server/                    # HTTP 服务层
│   │   ├── app.js                 # Express 应用主入口
│   │   ├── routes/                # RESTful API 路由定义
│   │   └── middleware/            # 鉴权、日志、错误处理中间件
│   ├── client/                    # 前端界面
│   │   ├── pages/                 # 页面级组件（首页、检索、收藏、设置）
│   │   ├── components/            # 可复用 UI 组件（导航栏、卡片、过滤器）
│   │   └── static/                # CSS 主题文件与图片资源
│   └── utils/                     # 工具函数
│       ├── logger.js              # 日志工具（支持按日切割）
│       ├── validator.js           # URL 格式校验与标准化
│       └── health.js              # 链接健康检查实现
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认配置（端口、抓取间隔、超时）
│   ├── sources.yaml               # 默认订阅源列表
│   └── custom/                    # 用户自定义配置挂载点
├── docs/                          # 完整文档（用户指南、API 参考、运维手册）
├── tests/                         # 单元测试与集成测试（Jest）
├── scripts/                       # 辅助脚本（初始化数据库、导入导出数据）
├── .env.example                   # 环境变量模板
├── package.json                   # npm 依赖声明
├── Dockerfile                     # 容器化构建文件
└── README.md                      # 项目入口文档
```

## 贡献指南

WebFront Navigator 遵循开源社区协作规范，欢迎各类贡献。请按照以下步骤参与项目。

1. 查阅 `docs/developer/CONTRIBUTING.md` 了解完整的贡献者行为准则和代码规范，确保提交内容符合项目风格要求。

2. 在 GitHub Issues 中查找标记为 `help wanted` 或 `good first issue` 的任务，或在 Discussions 中提出新的功能建议，等待维护者反馈后再开始编码。

3. 克隆项目并创建新的功能分支，分支命名格式为 `feature/简短描述` 或 `fix/问题编号`，例如 `feature/support-atom-feed`。

4. 提交代码前运行 `npm run lint` 和 `npm run test` 确保通过所有静态检查和单元测试，并为新增功能补充对应的测试用例。

5. 提交 Pull Request 时，请参照 PR 模板填写变更摘要、测试覆盖情况和相关 issue 编号，等待至少一位维护者进行 Code Review。

## 常见问题

**问：WebFront Navigator 是否支持 HTTPS 协议的外链？**

答：支持。项目内部使用 `node-fetch` 发起请求，默认跟随重定向并兼容 HTTPS 协议。用户配置订阅源时，URL 字段可以填写 `http://` 或 `https://` 开头的任意有效地址。对于资源列表中已收录的链接，系统会按照其原始协议进行访问，不会自动升级或降级。

**问：如何迁移已收藏的链接和阅读状态到另一台设备？**

答：使用导出功能生成 JSON 备份文件，然后将该文件通过 `npm run import -- --file=backup.json` 命令导入到目标设备的数据库中。需要注意的是，导入操作会覆盖目标设备上同 ID 的链接状态，建议在导入前先备份目标设备的数据。

**问：自动标签提取的准确率如何？是否可以手动修正？**

答：默认标签提取基于 TF-IDF 算法和预置的前端技术词库，对英文技术文章的准确率约为 72%，中文文章约为 65%。用户可以在 Web 界面的链接详情页中手动添加、删除或修改标签，所有手动修正的标签会被标记为 `manual` 类型，在后续自动更新中不会被覆盖。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
