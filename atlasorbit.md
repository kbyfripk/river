# LinkPilot Resource Aggregator

LinkPilot 是一个轻量级的技术资源外链聚合与导航系统，专为开发者、技术内容创作者及研究团队设计，用于高效管理、分类展示和快速检索分散于互联网各处的优质技术文章、新闻动态与参考文档。该项目并非一个传统的内容管理系统，而是一个基于静态标记与动态过滤的链接治理工具，核心目标在于将零散、易失效的浏览器书签转化为结构化、可维护、可共享的组织化知识库。

LinkPilot 面向每日需要处理大量技术信息流的用户，解决收藏链接后难以查找、分类混乱、缺乏上下文描述以及团队内共享困难等常见问题。通过提供清晰的分类索引、全文元数据搜索以及批次化的链接导入能力，该项目帮助用户将被动的信息囤积转变为主动的知识资产管理。

## 功能概览

**批量链接导入与解析** 支持从纯文本列表、CSV 文件或直接粘贴的原始 URL 集中批量导入链接，并自动尝试提取页面标题、摘要及元数据，大幅降低手动录入成本。

**多维度分类与标签系统** 允许为每个链接资源赋予多个自定义标签，并依据技术领域、内容类型或来源站点进行二级分类，实现灵活的交叉索引。

**全文元数据检索** 基于轻量级倒排索引，支持对链接标题、描述、标签及注释内容进行快速关键字搜索，并可按添加日期、访问热度或分类筛选排序。

**链接健康状态检查** 内置定时任务，可周期性探测已收录链接的可访问性，自动标记失效或重定向的资源，并提供断链报告，辅助维护链接库的可用性。

**批次管理与版本追溯** 以导入批次为单位组织链接记录，保留每次批次的导入时间、来源说明与备注，便于团队协作时追踪资源来源与更新历史。

**只读外链导航页生成** 支持将选定的链接集合一键导出为静态 HTML 导航页面，可直接部署为团队内部的技术资源起始页，无需依赖数据库或后端服务。

## 应用场景

个人技术书签库的规范化管理 开发者可将长期积累的零散浏览器书签导出为链接列表，一次性导入 LinkPilot，随后利用分类与标签体系进行系统化整理，并定期通过健康检查清理失效资源，构建个人专属的技术参考手册。

技术团队共享知识库的构建 团队技术负责人或文档维护者可使用 LinkPilot 汇总项目相关的设计文档、API 参考、运维手册及第三方依赖库地址，通过统一的导航页发布，确保团队成员始终访问到最新且经过验证的资源集合。

技术资讯的周期性汇总与分发 内容运营人员或开源社区维护者可将每周或每月收集的技术动态、版本发布公告及社区讨论帖，以批次形式导入 LinkPilot，生成带时间戳的汇总索引，便于社区成员回溯查阅。

技术调研与竞品分析过程中的链接归档 在进行技术选型或竞品分析时，调研人员可将收集到的竞品官网、技术白皮书、性能测试报告等大量链接快速入库，利用标签区分优先级与关注维度，形成结构化的调研素材池。

## 快速开始

以下指令演示了从 GitHub 克隆项目、安装依赖并启动开发服务器的完整流程。

```bash
git clone https://github.com/linkpilot-dev/linkpilot-core.git
cd linkpilot-core
npm install
npm run dev
```

执行成功后，开发服务器默认运行于 localhost:3000。访问该地址即可进入 LinkPilot 实例的管理界面，开始创建您的第一个链接批次。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Node.js | >= 18.0.0 | 项目运行时环境，需支持 ES Modules |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 依赖管理与脚本执行工具 |
| SQLite3 | 系统自带或由 better-sqlite3 绑定 | 默认内置嵌入式数据库，无需额外安装 |
| Git | >= 2.30.0 | 用于克隆仓库及版本控制 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 管理界面需要 ES2020 及 CSS Grid 支持 |
| 操作系统 | Linux (Ubuntu 20.04+) / macOS 11+ / Windows 10+ | 开发与生产环境均支持主流操作系统 |
| 可选依赖：Python 3 | >= 3.8 | 仅当启用高级元数据提取脚本时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | /docs/user-guide/ | 如何导入链接、创建分类、配置标签以及生成导航页？ |
| 运维指南 | /docs/ops/ | 如何配置健康检查周期、备份数据库以及迁移部署环境？ |
| 开发者文档 | /docs/developer/ | 项目的模块划分、核心 API 接口说明及扩展插件开发规范？ |
| 设计概述 | /docs/design/ | LinkPilot 的数据模型设计、索引策略及静态页生成原理？ |
| 常见问题 | /docs/faq/ | 如何处理特殊字符标题、批量导入失败及搜索性能问题？ |

## 资源列表

- http://m.blog.fcful.cn/bnews/7290818.htm
- http://m.blog.fcful.cn/bnews/344956.htm
- http://m.blog.fcful.cn/bnews/12843.htm
- http://m.blog.fcful.cn/bnews/594361.htm
- http://m.blog.fcful.cn/bnews/2363246.htm
- http://m.blog.fcful.cn/bnews/53322.htm
- http://m.blog.fcful.cn/bnews/1642219.htm
- http://m.blog.fcful.cn/bnews/58652.htm
- http://m.blog.fcful.cn/bnews/682846.htm
- http://m.blog.fcful.cn/bnews/9508.htm
- http://m.blog.fcful.cn/bnews/869838.htm
- http://m.blog.fcful.cn/bnews/809886.htm
- http://m.blog.fcful.cn/bnews/083081.htm
- http://m.blog.fcful.cn/bnews/8939.htm
- http://m.blog.fcful.cn/bnews/692262.htm
- http://m.blog.fcful.cn/bnews/3405.htm
- http://m.blog.fcful.cn/bnews/12628.htm
- http://m.blog.fcful.cn/bnews/4606368.htm
- http://m.blog.fcful.cn/bnews/51398.htm
- http://m.blog.fcful.cn/bnews/9384469.htm
- http://m.blog.fcful.cn/bnews/813994.htm
- http://m.blog.fcful.cn/bnews/9857.htm
- http://m.blog.fcful.cn/bnews/8095.htm
- http://m.blog.fcful.cn/bnews/1263205.htm
- http://m.blog.fcful.cn/bnews/7930.htm
- http://m.blog.fcful.cn/bnews/35792.htm
- http://m.blog.fcful.cn/bnews/00468.htm
- http://m.blog.fcful.cn/bnews/27545.htm
- http://m.blog.fcful.cn/bnews/5286.htm
- http://m.blog.fcful.cn/bnews/427601.htm
- http://m.blog.fcful.cn/bnews/1915836.htm
- http://m.blog.fcful.cn/bnews/691576.htm
- http://m.blog.fcful.cn/bnews/2438.htm
- http://m.blog.fcful.cn/bnews/88356.htm
- http://m.blog.fcful.cn/bnews/4317165.htm
- http://m.blog.fcful.cn/bnews/076190.htm
- http://m.blog.fcful.cn/bnews/00073.htm
- http://m.blog.fcful.cn/bnews/6841.htm
- http://m.blog.fcful.cn/bnews/64658.htm
- http://m.blog.fcful.cn/bnews/4469183.htm
- http://m.blog.fcful.cn/bnews/658226.htm
- http://m.blog.fcful.cn/bnews/6436399.htm
- http://m.blog.fcful.cn/bnews/5710942.htm
- http://m.blog.fcful.cn/bnews/879011.htm
- http://m.blog.fcful.cn/bnews/59425.htm
- http://m.blog.fcful.cn/bnews/834910.htm
- http://m.blog.fcful.cn/bnews/0495.htm
- http://m.blog.fcful.cn/bnews/841294.htm
- http://m.blog.fcful.cn/bnews/92655.htm
- http://m.blog.fcful.cn/bnews/31455.htm
- http://m.blog.fcful.cn/bnews/764918.htm
- http://m.blog.fcful.cn/bnews/469843.htm
- http://m.blog.fcful.cn/bnews/0789846.htm
- http://m.blog.fcful.cn/bnews/5810.htm
- http://m.blog.fcful.cn/bnews/9992426.htm
- http://m.blog.fcful.cn/bnews/948575.htm
- http://m.blog.fcful.cn/bnews/010172.htm
- http://m.blog.fcful.cn/bnews/58389.htm
- http://m.blog.fcful.cn/bnews/129256.htm
- http://m.blog.fcful.cn/bnews/793267.htm
- http://m.blog.fcful.cn/bnews/8978331.htm
- http://m.blog.fcful.cn/bnews/3617163.htm
- http://m.blog.fcful.cn/bnews/9686012.htm
- http://m.blog.fcful.cn/bnews/1009.htm
- http://m.blog.fcful.cn/bnews/9227879.htm
- http://m.blog.fcful.cn/bnews/18847.htm
- http://m.blog.fcful.cn/bnews/92449.htm
- http://m.blog.fcful.cn/bnews/305661.htm
- http://m.blog.fcful.cn/bnews/69087.htm
- http://m.blog.fcful.cn/bnews/19167.htm
- http://m.blog.fcful.cn/bnews/68433.htm
- http://m.blog.fcful.cn/bnews/0541230.htm
- http://m.blog.fcful.cn/bnews/21096.htm
- http://m.blog.fcful.cn/bnews/714346.htm
- http://m.blog.fcful.cn/bnews/9184393.htm
- http://m.blog.fcful.cn/bnews/9781039.htm
- http://m.blog.fcful.cn/bnews/368337.htm
- http://m.blog.fcful.cn/bnews/854071.htm
- http://m.blog.fcful.cn/bnews/4639161.htm
- http://m.blog.fcful.cn/bnews/935838.htm
- http://m.blog.fcful.cn/bnews/179467.htm
- http://m.blog.fcful.cn/bnews/49851.htm
- http://m.blog.fcful.cn/bnews/417275.htm
- http://m.blog.fcful.cn/bnews/0123.htm
- http://m.blog.fcful.cn/bnews/48664.htm
- http://m.blog.fcful.cn/bnews/7645.htm
- http://m.blog.fcful.cn/bnews/536404.htm
- http://m.blog.fcful.cn/bnews/908852.htm
- http://m.blog.fcful.cn/bnews/1846109.htm
- http://m.blog.fcful.cn/bnews/549009.htm
- http://m.blog.fcful.cn/bnews/801916.htm
- http://m.blog.fcful.cn/bnews/733723.htm
- http://m.blog.fcful.cn/bnews/238944.htm
- http://m.blog.fcful.cn/bnews/3312.htm
- http://m.blog.fcful.cn/bnews/8137270.htm
- http://m.blog.fcful.cn/bnews/081695.htm
- http://m.blog.fcful.cn/bnews/6330.htm
- http://m.blog.fcful.cn/bnews/05379.htm
- http://m.blog.fcful.cn/bnews/705162.htm
- http://m.blog.fcful.cn/bnews/7375526.htm
- http://m.blog.fcful.cn/bnews/336958.htm
- http://m.blog.fcful.cn/bnews/4350578.htm
- http://m.blog.fcful.cn/bnews/49988.htm
- http://m.blog.fcful.cn/bnews/5206626.htm
- http://m.blog.fcful.cn/bnews/4779.htm
- http://m.blog.fcful.cn/bnews/73226.htm
- http://m.blog.fcful.cn/bnews/812575.htm
- http://m.blog.fcful.cn/bnews/446497.htm
- http://m.blog.fcful.cn/bnews/7580.htm
- http://m.blog.fcful.cn/bnews/9272.htm
- http://m.blog.fcful.cn/bnews/104867.htm
- http://m.blog.fcful.cn/bnews/446817.htm
- http://m.blog.fcful.cn/bnews/4470647.htm
- http://m.blog.fcful.cn/bnews/3976.htm
- http://m.blog.fcful.cn/bnews/0031131.htm
- http://m.blog.fcful.cn/bnews/276737.htm
- http://m.blog.fcful.cn/bnews/96850.htm
- http://m.blog.fcful.cn/bnews/2098.htm
- http://m.blog.fcful.cn/bnews/246108.htm
- http://m.blog.fcful.cn/bnews/24389.htm
- http://m.blog.fcful.cn/bnews/4453789.htm
- http://m.blog.fcful.cn/bnews/6261.htm
- http://m.blog.fcful.cn/bnews/227674.htm
- http://m.blog.fcful.cn/bnews/160281.htm
- http://m.blog.fcful.cn/bnews/6298912.htm
- http://m.blog.fcful.cn/bnews/5295018.htm
- http://m.blog.fcful.cn/bnews/968493.htm
- http://m.blog.fcful.cn/bnews/102219.htm
- http://m.blog.fcful.cn/bnews/36824.htm
- http://m.blog.fcful.cn/bnews/96140.htm
- http://m.blog.fcful.cn/bnews/5454816.htm
- http://m.blog.fcful.cn/bnews/180371.htm
- http://m.blog.fcful.cn/bnews/450473.htm
- http://m.blog.fcful.cn/bnews/7924471.htm
- http://m.blog.fcful.cn/bnews/040139.htm
- http://m.blog.fcful.cn/bnews/2237.htm
- http://m.blog.fcful.cn/bnews/1072.htm
- http://m.blog.fcful.cn/bnews/4112.htm
- http://m.blog.fcful.cn/bnews/429793.htm
- http://m.blog.fcful.cn/bnews/16478.htm
- http://m.blog.fcful.cn/bnews/432482.htm
- http://m.blog.fcful.cn/bnews/8073.htm
- http://m.blog.fcful.cn/bnews/073112.htm
- http://m.blog.fcful.cn/bnews/62336.htm
- http://m.blog.fcful.cn/bnews/0499.htm
- http://m.blog.fcful.cn/bnews/46658.htm
- http://m.blog.fcful.cn/bnews/6584430.htm
- http://m.blog.fcful.cn/bnews/8947.htm
- http://m.blog.fcful.cn/bnews/5120.htm
- http://m.blog.fcful.cn/bnews/1668962.htm
- http://m.blog.fcful.cn/bnews/933841.htm
- http://m.blog.fcful.cn/bnews/170484.htm
- http://m.blog.fcful.cn/bnews/0455953.htm
- http://m.blog.fcful.cn/bnews/76561.htm
- http://m.blog.fcful.cn/bnews/97324.htm
- http://m.blog.fcful.cn/bnews/9716.htm
- http://m.blog.fcful.cn/bnews/543296.htm
- http://m.blog.fcful.cn/bnews/4636.htm
- http://m.blog.fcful.cn/bnews/5860316.htm
- http://m.blog.fcful.cn/bnews/1223012.htm
- http://m.blog.fcful.cn/bnews/1063.htm
- http://m.blog.fcful.cn/bnews/8867.htm
- http://m.blog.fcful.cn/bnews/4593761.htm
- http://m.blog.fcful.cn/bnews/9390748.htm
- http://m.blog.fcful.cn/bnews/1598.htm
- http://m.blog.fcful.cn/bnews/43519.htm
- http://m.blog.fcful.cn/bnews/8409909.htm
- http://m.blog.fcful.cn/bnews/7329.htm
- http://m.blog.fcful.cn/bnews/5408.htm
- http://m.blog.fcful.cn/bnews/9029.htm
- http://m.blog.fcful.cn/bnews/800607.htm
- http://m.blog.fcful.cn/bnews/2643.htm
- http://m.blog.fcful.cn/bnews/9468980.htm
- http://m.blog.fcful.cn/bnews/959096.htm
- http://m.blog.fcful.cn/bnews/6822.htm
- http://m.blog.fcful.cn/bnews/783872.htm
- http://m.blog.fcful.cn/bnews/3778888.htm
- http://m.blog.fcful.cn/bnews/572365.htm
- http://m.blog.fcful.cn/bnews/655086.htm
- http://m.blog.fcful.cn/bnews/4554940.htm
- http://m.blog.fcful.cn/bnews/7470719.htm
- http://m.blog.fcful.cn/bnews/0899677.htm
- http://m.blog.fcful.cn/bnews/1707.htm
- http://m.blog.fcful.cn/bnews/1394.htm
- http://m.blog.fcful.cn/bnews/099062.htm
- http://m.blog.fcful.cn/bnews/561866.htm
- http://m.blog.fcful.cn/bnews/0597.htm
- http://m.blog.fcful.cn/bnews/512910.htm
- http://m.blog.fcful.cn/bnews/426314.htm
- http://m.blog.fcful.cn/bnews/900570.htm
- http://m.blog.fcful.cn/bnews/61394.htm
- http://m.blog.fcful.cn/bnews/71747.htm
- http://m.blog.fcful.cn/bnews/26109.htm
- http://m.blog.fcful.cn/bnews/80191.htm
- http://m.blog.fcful.cn/bnews/7847.htm
- http://m.blog.fcful.cn/bnews/19062.htm
- http://m.blog.fcful.cn/bnews/07327.htm
- http://m.blog.fcful.cn/bnews/01053.htm
- http://m.blog.fcful.cn/bnews/596361.htm
- http://m.blog.fcful.cn/bnews/1281.htm
- http://m.blog.fcful.cn/bnews/62831.htm
- http://m.blog.fcful.cn/bnews/97430.htm
- http://m.blog.fcful.cn/bnews/2317.htm
- http://m.blog.fcful.cn/bnews/1043976.htm
- http://m.blog.fcful.cn/bnews/8300.htm
- http://m.blog.fcful.cn/bnews/0634955.htm
- http://m.blog.fcful.cn/bnews/10883.htm
- http://m.blog.fcful.cn/bnews/07628.htm
- http://m.blog.fcful.cn/bnews/49048.htm
- http://m.blog.fcful.cn/bnews/45614.htm
- http://m.blog.fcful.cn/bnews/4197376.htm
- http://m.blog.fcful.cn/bnews/954027.htm
- http://m.blog.fcful.cn/bnews/857060.htm
- http://m.blog.fcful.cn/bnews/953422.htm
- http://m.blog.fcful.cn/bnews/3666338.htm
- http://m.blog.fcful.cn/bnews/3098.htm
- http://m.blog.fcful.cn/bnews/479123.htm
- http://m.blog.fcful.cn/bnews/0397.htm
- http://m.blog.fcful.cn/bnews/71752.htm
- http://m.blog.fcful.cn/bnews/130887.htm
- http://m.blog.fcful.cn/bnews/092301.htm
- http://m.blog.fcful.cn/bnews/340591.htm
- http://m.blog.fcful.cn/bnews/070302.htm
- http://m.blog.fcful.cn/bnews/345805.htm
- http://m.blog.fcful.cn/bnews/3367475.htm
- http://m.blog.fcful.cn/bnews/675396.htm
- http://m.blog.fcful.cn/bnews/0867.htm
- http://m.blog.fcful.cn/bnews/405252.htm
- http://m.blog.fcful.cn/bnews/9552.htm
- http://m.blog.fcful.cn/bnews/83883.htm
- http://m.blog.fcful.cn/bnews/774547.htm
- http://m.blog.fcful.cn/bnews/15483.htm
- http://m.blog.fcful.cn/bnews/0039.htm
- http://m.blog.fcful.cn/bnews/0332.htm
- http://m.blog.fcful.cn/bnews/3296.htm
- http://m.blog.fcful.cn/bnews/13443.htm
- http://m.blog.fcful.cn/bnews/2869635.htm
- http://m.blog.fcful.cn/bnews/0274539.htm
- http://m.blog.fcful.cn/bnews/31062.htm
- http://m.blog.fcful.cn/bnews/75019.htm
- http://m.blog.fcful.cn/bnews/487417.htm
- http://m.blog.fcful.cn/bnews/7683.htm
- http://m.blog.fcful.cn/bnews/593161.htm
- http://m.blog.fcful.cn/bnews/83255.htm
- http://m.blog.fcful.cn/bnews/7043.htm
- http://m.blog.fcful.cn/bnews/5871.htm
- http://m.blog.fcful.cn/bnews/36534.htm
- http://m.blog.fcful.cn/bnews/042425.htm
- http://m.blog.fcful.cn/bnews/88816.htm
- http://m.blog.fcful.cn/bnews/27189.htm

## 项目结构

```
linkpilot-core/
├── src/
│   ├── core/                      # 核心数据模型与业务逻辑
│   │   ├── link.model.js          # 链接实体类定义，包含 URL 规范化与元数据字段
│   │   ├── batch.model.js         # 批次实体类，管理批次状态与时间戳
│   │   └── tag.model.js           # 标签实体与多对多关联关系处理
│   ├── parser/                    # 链接解析与元数据提取模块
│   │   ├── html-parser.js         # 基于 cheerio 的 HTML 标题与描述抽取
│   │   └── url-normalizer.js      # URL 去重、协议补全与路径清理工具
│   ├── db/                        # 数据持久化层
│   │   ├── sqlite-adapter.js      # better-sqlite3 封装，提供 CRUD 接口
│   │   └── migration/             # 数据库表结构版本迁移脚本
│   ├── checker/                   # 链接健康检查模块
│   │   ├── health-check.js        # 并发 HTTP 探测与超时控制
│   │   └── reporter.js            # 生成失效链接报告 (Markdown 格式)
│   ├── exporter/                  # 静态导航页生成器
│   │   ├── template-engine.js     # 基于 EJS 的 HTML 模板渲染
│   │   └── static-writer.js       # 将渲染结果写入磁盘并复制静态资源
│   ├── api/                       # HTTP API 路由层 (Express)
│   │   ├── routes/                # 各业务路由定义 (批次、链接、标签、检索)
│   │   └── middleware/            # 认证、日志与错误处理中间件
│   └── ui/                        # 管理端前端应用 (React + Vite)
│       ├── pages/                 # 主要视图页面 (批次列表、链接网格、搜索页)
│       └── components/            # 可复用 UI 组件 (表格、标签输入、状态徽章)
├── config/                        # 环境变量与运行配置
│   ├── default.toml               # 默认端口、数据库路径、检查频率等配置
│   └── custom.toml.example        # 自定义配置示例文件
├── scripts/                       # 辅助运维脚本
│   ├── import-from-csv.js         # 从 CSV 文件批量导入链接的命令行工具
│   └── export-nav.js              # 手动触发导航页导出的 CLI 脚本
├── docs/                          # 完整文档目录 (详见文档导航章节)
├── tests/                         # 单元测试与集成测试 (Jest)
├── public/                        # 静态资源 (favicon, robots.txt)
├── package.json                   # npm 项目清单与依赖声明
├── README.md                      # 项目简介与快速入门 (当前文件)
└── LICENSE                        # MIT 许可证全文
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 描述您希望修复的缺陷或建议新增的功能，等待核心维护者反馈以避免重复工作或方向偏离。
2. 从项目仓库 fork 代码到个人账户，并在本地基于 main 分支创建新的功能分支，分支命名遵循 feat/功能简述 或 fix/问题简述 格式。
3. 完成代码修改后，确保所有现有测试用例通过，并为新增逻辑补充对应的单元测试或集成测试，测试覆盖率不应低于 80%。
4. 提交代码时遵循 Conventional Commits 规范编写 commit message，并以 Pull Request 形式向主仓库的 main 分支提交合并请求，PR 描述中需关联对应的 issue 编号。
5. 核心维护者将在代码审查通过后合并您的贡献，并在合并后更新贡献者列表。重大变更将在发布前通过 issue 或邮件列表进行公示。

## 常见问题

**问：导入包含大量链接的列表时，页面出现超时或无响应，应如何优化？**

答：LinkPilot 默认对单次批量导入的链接数量设有软限制（500 条/批次）。若需导入超过该数量的列表，建议将列表拆分为多个小批次，或使用项目提供的命令行导入脚本 scripts/import-from-csv.js，该脚本绕过 HTTP 请求超时限制，并实时输出导入进度日志。同时，检查网络环境是否允许访问目标链接，若部分链接需要特殊代理，可在配置文件中设置全局 HTTP 代理。

**问：为什么部分链接在健康检查中始终被标记为失效，但手动浏览器访问正常？**

答：此现象通常由以下原因导致：目标站点启用了反爬虫机制（如 User-Agent 过滤、JavaScript 渲染依赖或限速策略）；或站点响应时间超过健康检查默认的 5000 毫秒超时阈值。解决方案包括：在配置文件中调整 checker.timeout 参数值；在 checker.customHeaders 中配置与浏览器一致的 User-Agent；对于严重依赖 JavaScript 渲染的页面，可考虑将其加入白名单排除检查。

**问：如何将 LinkPilot 部署到生产环境，并确保数据持久化？**

答：生产环境部署建议使用 PM2 或 systemd 管理 Node.js 进程，并通过 Nginx 反向代理提供 HTTPS 服务。默认的 SQLite 数据库文件位于 ./data/linkpilot.db，务必定期备份该文件。若需使用 MySQL 或 PostgreSQL 作为生产数据库，可参考项目文档中的扩展数据库适配器开发指南，自行实现对应的 db 适配层。对于静态导航页，建议将其生成到 Nginx 静态目录下，以获得最佳访问性能。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:43
