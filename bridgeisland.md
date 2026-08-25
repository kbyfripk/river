# WebIndex 聚合导航系统

WebIndex 是一个轻量级的技术资源与外链聚合导航系统，面向开发者、技术博主与开源社区维护者，用于将分散在多个平台的技术文章、新闻动态、项目文档与教程资源集中管理，并提供统一的浏览与检索入口。该项目定位于中小型技术团队、个人知识库运营者以及社区内容聚合场景，解决信息碎片化、链接失效、资源查找效率低下等常见问题。

WebIndex 不依赖复杂的前端框架，基于原生 HTML 与静态文件生成机制构建，支持一键更新资源索引，能够以极低的维护成本运行在任意静态托管服务上。项目内置了批次化管理能力，当前为第 104/240 批次，共计管理 250 个外链资源，涵盖技术博客、行业资讯、开发工具文档等多个类别。

## 功能概览

- **批量外链导入与管理**：支持按批次导入大量 URL，自动生成索引页面，并保留原始链接地址与批次元信息。

- **分类标签与全文检索**：为每条资源标记分类标签与关键词，提供基于标题和描述的简单检索功能，帮助用户快速定位目标内容。

- **响应式移动端适配**：页面布局针对移动设备与桌面端分别优化，确保在手机、平板与电脑上均能获得良好的浏览体验。

- **静态页面生成机制**：所有资源列表与详情页在构建时预渲染为静态 HTML，无需后端服务即可运行，降低部署与运维成本。

- **链接可用性检测**：内置链接存活检测工具，可定期扫描资源列表，标记失效链接并生成报告，便于维护者及时更新或移除。

- **批次化版本管理**：每个资源批次独立存储，支持按批次编号查看资源清单，方便追溯不同时期收录的内容范围。

- **自定义元数据扩展**：每条资源可附加描述、来源站点、收录日期等元数据，支持通过配置文件批量修改与补充。

## 应用场景

- **技术团队内部知识库聚合**：开发团队可将日常查阅的 API 文档、框架教程、运维手册等外链统一收录至 WebIndex，新成员入职时无需逐个询问常用资源地址，直接通过导航页即可访问全部必要资料。

- **开源项目周边资源汇总**：开源项目维护者可将社区贡献的教程视频、博客解读、衍生工具列表集中展示在项目文档站点中，利用 WebIndex 的外链管理能力构建生态资源页，降低社区用户获取周边信息的门槛。

- **个人技术博客的友情链接与推荐阅读**：技术博主可将撰写文章时参考的权威资料、数据来源以及互惠推广的友链统一整理为资源页面，既丰富了博客内容层次，也为读者提供了延伸阅读的便利入口。

- **技术社区活动资源存档**：线上技术沙龙、黑客松或开源贡献赛等活动结束后，主办方可将活动过程中产生的直播回放链接、PPT 下载地址、代码仓库与讨论帖汇总至 WebIndex，形成可长期保存的活动资源档案。

## 快速开始

以下命令可在本地环境完成 WebIndex 的克隆、依赖安装与服务启动，适用于 Linux 与 macOS 系统。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装依赖（需要 Node.js 16+ 与 npm）
npm install

# 生成静态资源索引
npm run build

# 启动本地开发服务器
npm run dev
```

启动成功后，在浏览器中访问 http://localhost:3000 即可查看资源导航页面。如需自定义资源列表，请编辑 `data/batches/104.json` 文件，随后重新执行 `npm run build` 即可更新静态页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.x 或更高 | 运行构建脚本与开发服务器的运行时环境 |
| npm | 8.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与管理变更 |
| 静态托管服务 | 任意 | 生产环境部署时需要支持 HTML 与静态资源托管，如 Nginx、Apache、OSS 或 Pages 服务 |
| 浏览器 | 支持 ES6 的现代浏览器 | 访问导航页面所需，推荐 Chrome 90+、Firefox 88+ 或 Safari 14+ |
| 磁盘空间 | 100 MB 以上 | 用于存放项目源代码、生成静态文件与资源索引缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide.md | 如何使用 WebIndex 浏览资源、检索内容以及提交新的外链建议 |
| 维护者指南 | /docs/maintainer-guide.md | 如何管理资源批次、编辑元数据、执行链接检测与更新索引 |
| 开发者文档 | /docs/developer-guide.md | 如何二次开发、扩展数据模型、自定义页面模板与构建流程 |
| 部署手册 | /docs/deployment-guide.md | 如何将 WebIndex 部署到 Vercel、Netlify、Cloudflare Pages 或自建服务器 |

## 资源列表

- http://m.blog.fcful.cn/bnews/561264.htm
- http://m.blog.fcful.cn/bnews/772555.htm
- http://m.blog.fcful.cn/bnews/95102.htm
- http://m.blog.fcful.cn/bnews/7622.htm
- http://m.blog.fcful.cn/bnews/3113886.htm
- http://m.blog.fcful.cn/bnews/4830589.htm
- http://m.blog.fcful.cn/bnews/04232.htm
- http://m.blog.fcful.cn/bnews/897187.htm
- http://m.blog.fcful.cn/bnews/0971.htm
- http://m.blog.fcful.cn/bnews/58009.htm
- http://m.blog.fcful.cn/bnews/395209.htm
- http://m.blog.fcful.cn/bnews/683114.htm
- http://m.blog.fcful.cn/bnews/14739.htm
- http://m.blog.fcful.cn/bnews/3469574.htm
- http://m.blog.fcful.cn/bnews/171774.htm
- http://m.blog.fcful.cn/bnews/613452.htm
- http://m.blog.fcful.cn/bnews/1251.htm
- http://m.blog.fcful.cn/bnews/91022.htm
- http://m.blog.fcful.cn/bnews/882443.htm
- http://m.blog.fcful.cn/bnews/488696.htm
- http://m.blog.fcful.cn/bnews/12379.htm
- http://m.blog.fcful.cn/bnews/4045250.htm
- http://m.blog.fcful.cn/bnews/0506569.htm
- http://m.blog.fcful.cn/bnews/5016.htm
- http://m.blog.fcful.cn/bnews/2244613.htm
- http://m.blog.fcful.cn/bnews/214113.htm
- http://m.blog.fcful.cn/bnews/0632.htm
- http://m.blog.fcful.cn/bnews/0748044.htm
- http://m.blog.fcful.cn/bnews/0307.htm
- http://m.blog.fcful.cn/bnews/5069.htm
- http://m.blog.fcful.cn/bnews/7390.htm
- http://m.blog.fcful.cn/bnews/6068161.htm
- http://m.blog.fcful.cn/bnews/9666118.htm
- http://m.blog.fcful.cn/bnews/7682629.htm
- http://m.blog.fcful.cn/bnews/87942.htm
- http://m.blog.fcful.cn/bnews/7894636.htm
- http://m.blog.fcful.cn/bnews/3069634.htm
- http://m.blog.fcful.cn/bnews/8967542.htm
- http://m.blog.fcful.cn/bnews/8090.htm
- http://m.blog.fcful.cn/bnews/60280.htm
- http://m.blog.fcful.cn/bnews/4381.htm
- http://m.blog.fcful.cn/bnews/8820.htm
- http://m.blog.fcful.cn/bnews/225365.htm
- http://m.blog.fcful.cn/bnews/65411.htm
- http://m.blog.fcful.cn/bnews/0844126.htm
- http://m.blog.fcful.cn/bnews/697867.htm
- http://m.blog.fcful.cn/bnews/904941.htm
- http://m.blog.fcful.cn/bnews/785218.htm
- http://m.blog.fcful.cn/bnews/21121.htm
- http://m.blog.fcful.cn/bnews/151905.htm
- http://m.blog.fcful.cn/bnews/0584.htm
- http://m.blog.fcful.cn/bnews/5436.htm
- http://m.blog.fcful.cn/bnews/764134.htm
- http://m.blog.fcful.cn/bnews/5295121.htm
- http://m.blog.fcful.cn/bnews/40446.htm
- http://m.blog.fcful.cn/bnews/43623.htm
- http://m.blog.fcful.cn/bnews/0669.htm
- http://m.blog.fcful.cn/bnews/8195.htm
- http://m.blog.fcful.cn/bnews/951960.htm
- http://m.blog.fcful.cn/bnews/3525.htm
- http://m.blog.fcful.cn/bnews/3079.htm
- http://m.blog.fcful.cn/bnews/38093.htm
- http://m.blog.fcful.cn/bnews/5938.htm
- http://m.blog.fcful.cn/bnews/09191.htm
- http://m.blog.fcful.cn/bnews/384188.htm
- http://m.blog.fcful.cn/bnews/715887.htm
- http://m.blog.fcful.cn/bnews/13274.htm
- http://m.blog.fcful.cn/bnews/8270345.htm
- http://m.blog.fcful.cn/bnews/8087628.htm
- http://m.blog.fcful.cn/bnews/6970703.htm
- http://m.blog.fcful.cn/bnews/6856.htm
- http://m.blog.fcful.cn/bnews/36151.htm
- http://m.blog.fcful.cn/bnews/3067.htm
- http://m.blog.fcful.cn/bnews/2747695.htm
- http://m.blog.fcful.cn/bnews/0710297.htm
- http://m.blog.fcful.cn/bnews/41804.htm
- http://m.blog.fcful.cn/bnews/7504458.htm
- http://m.blog.fcful.cn/bnews/1696016.htm
- http://m.blog.fcful.cn/bnews/275684.htm
- http://m.blog.fcful.cn/bnews/912006.htm
- http://m.blog.fcful.cn/bnews/357356.htm
- http://m.blog.fcful.cn/bnews/233703.htm
- http://m.blog.fcful.cn/bnews/16285.htm
- http://m.blog.fcful.cn/bnews/4151398.htm
- http://m.blog.fcful.cn/bnews/169467.htm
- http://m.blog.fcful.cn/bnews/83119.htm
- http://m.blog.fcful.cn/bnews/247162.htm
- http://m.blog.fcful.cn/bnews/915167.htm
- http://m.blog.fcful.cn/bnews/550214.htm
- http://m.blog.fcful.cn/bnews/68808.htm
- http://m.blog.fcful.cn/bnews/1543.htm
- http://m.blog.fcful.cn/bnews/03907.htm
- http://m.blog.fcful.cn/bnews/102732.htm
- http://m.blog.fcful.cn/bnews/636607.htm
- http://m.blog.fcful.cn/bnews/7748.htm
- http://m.blog.fcful.cn/bnews/365925.htm
- http://m.blog.fcful.cn/bnews/2281.htm
- http://m.blog.fcful.cn/bnews/20138.htm
- http://m.blog.fcful.cn/bnews/05074.htm
- http://m.blog.fcful.cn/bnews/52366.htm
- http://m.blog.fcful.cn/bnews/9244212.htm
- http://m.blog.fcful.cn/bnews/3468132.htm
- http://m.blog.fcful.cn/bnews/2176224.htm
- http://m.blog.fcful.cn/bnews/391501.htm
- http://m.blog.fcful.cn/bnews/3193564.htm
- http://m.blog.fcful.cn/bnews/79645.htm
- http://m.blog.fcful.cn/bnews/1903922.htm
- http://m.blog.fcful.cn/bnews/0608.htm
- http://m.blog.fcful.cn/bnews/601498.htm
- http://m.blog.fcful.cn/bnews/96350.htm
- http://m.blog.fcful.cn/bnews/6854.htm
- http://m.blog.fcful.cn/bnews/006311.htm
- http://m.blog.fcful.cn/bnews/953662.htm
- http://m.blog.fcful.cn/bnews/534876.htm
- http://m.blog.fcful.cn/bnews/758500.htm
- http://m.blog.fcful.cn/bnews/5828013.htm
- http://m.blog.fcful.cn/bnews/498758.htm
- http://m.blog.fcful.cn/bnews/47059.htm
- http://m.blog.fcful.cn/bnews/7446.htm
- http://m.blog.fcful.cn/bnews/95269.htm
- http://m.blog.fcful.cn/bnews/914051.htm
- http://m.blog.fcful.cn/bnews/167459.htm
- http://m.blog.fcful.cn/bnews/718594.htm
- http://m.blog.fcful.cn/bnews/23690.htm
- http://m.blog.fcful.cn/bnews/2221965.htm
- http://m.blog.fcful.cn/bnews/749383.htm
- http://m.blog.fcful.cn/bnews/0005.htm
- http://m.blog.fcful.cn/bnews/9410910.htm
- http://m.blog.fcful.cn/bnews/58037.htm
- http://m.blog.fcful.cn/bnews/807772.htm
- http://m.blog.fcful.cn/bnews/8789985.htm
- http://m.blog.fcful.cn/bnews/947190.htm
- http://m.blog.fcful.cn/bnews/019753.htm
- http://m.blog.fcful.cn/bnews/079011.htm
- http://m.blog.fcful.cn/bnews/6110.htm
- http://m.blog.fcful.cn/bnews/2072.htm
- http://m.blog.fcful.cn/bnews/8151388.htm
- http://m.blog.fcful.cn/bnews/6984.htm
- http://m.blog.fcful.cn/bnews/4730571.htm
- http://m.blog.fcful.cn/bnews/972938.htm
- http://m.blog.fcful.cn/bnews/67017.htm
- http://m.blog.fcful.cn/bnews/395001.htm
- http://m.blog.fcful.cn/bnews/447335.htm
- http://m.blog.fcful.cn/bnews/55144.htm
- http://m.blog.fcful.cn/bnews/2016.htm
- http://m.blog.fcful.cn/bnews/54256.htm
- http://m.blog.fcful.cn/bnews/70115.htm
- http://m.blog.fcful.cn/bnews/180849.htm
- http://m.blog.fcful.cn/bnews/3771.htm
- http://m.blog.fcful.cn/bnews/8127.htm
- http://m.blog.fcful.cn/bnews/4551.htm
- http://m.blog.fcful.cn/bnews/02980.htm
- http://m.blog.fcful.cn/bnews/9151.htm
- http://m.blog.fcful.cn/bnews/9190.htm
- http://m.blog.fcful.cn/bnews/7612.htm
- http://m.blog.fcful.cn/bnews/876097.htm
- http://m.blog.fcful.cn/bnews/1028770.htm
- http://m.blog.fcful.cn/bnews/89649.htm
- http://m.blog.fcful.cn/bnews/0746.htm
- http://m.blog.fcful.cn/bnews/621557.htm
- http://m.blog.fcful.cn/bnews/2187403.htm
- http://m.blog.fcful.cn/bnews/1734.htm
- http://m.blog.fcful.cn/bnews/37195.htm
- http://m.blog.fcful.cn/bnews/6761.htm
- http://m.blog.fcful.cn/bnews/056917.htm
- http://m.blog.fcful.cn/bnews/8064.htm
- http://m.blog.fcful.cn/bnews/43504.htm
- http://m.blog.fcful.cn/bnews/649652.htm
- http://m.blog.fcful.cn/bnews/9738.htm
- http://m.blog.fcful.cn/bnews/4496.htm
- http://m.blog.fcful.cn/bnews/8107511.htm
- http://m.blog.fcful.cn/bnews/4687297.htm
- http://m.blog.fcful.cn/bnews/0161.htm
- http://m.blog.fcful.cn/bnews/078300.htm
- http://m.blog.fcful.cn/bnews/232967.htm
- http://m.blog.fcful.cn/bnews/41674.htm
- http://m.blog.fcful.cn/bnews/39066.htm
- http://m.blog.fcful.cn/bnews/761195.htm
- http://m.blog.fcful.cn/bnews/009690.htm
- http://m.blog.fcful.cn/bnews/073050.htm
- http://m.blog.fcful.cn/bnews/0427.htm
- http://m.blog.fcful.cn/bnews/450781.htm
- http://m.blog.fcful.cn/bnews/66640.htm
- http://m.blog.fcful.cn/bnews/48298.htm
- http://m.blog.fcful.cn/bnews/3675.htm
- http://m.blog.fcful.cn/bnews/2551.htm
- http://m.blog.fcful.cn/bnews/8191.htm
- http://m.blog.fcful.cn/bnews/27481.htm
- http://m.blog.fcful.cn/bnews/2296.htm
- http://m.blog.fcful.cn/bnews/88298.htm
- http://m.blog.fcful.cn/bnews/001605.htm
- http://m.blog.fcful.cn/bnews/3354581.htm
- http://m.blog.fcful.cn/bnews/88208.htm
- http://m.blog.fcful.cn/bnews/7054.htm
- http://m.blog.fcful.cn/bnews/27825.htm
- http://m.blog.fcful.cn/bnews/023267.htm
- http://m.blog.fcful.cn/bnews/83913.htm
- http://m.blog.fcful.cn/bnews/12515.htm
- http://m.blog.fcful.cn/bnews/6875.htm
- http://m.blog.fcful.cn/bnews/7492843.htm
- http://m.blog.fcful.cn/bnews/42524.htm
- http://m.blog.fcful.cn/bnews/2006.htm
- http://m.blog.fcful.cn/bnews/6225144.htm
- http://m.blog.fcful.cn/bnews/16707.htm
- http://m.blog.fcful.cn/bnews/2184328.htm
- http://m.blog.fcful.cn/bnews/46477.htm
- http://m.blog.fcful.cn/bnews/25731.htm
- http://m.blog.fcful.cn/bnews/9458159.htm
- http://m.blog.fcful.cn/bnews/2523078.htm
- http://m.blog.fcful.cn/bnews/1873558.htm
- http://m.blog.fcful.cn/bnews/4962.htm
- http://m.blog.fcful.cn/bnews/530527.htm
- http://m.blog.fcful.cn/bnews/121545.htm
- http://m.blog.fcful.cn/bnews/23563.htm
- http://m.blog.fcful.cn/bnews/15474.htm
- http://m.blog.fcful.cn/bnews/515700.htm
- http://m.blog.fcful.cn/bnews/3355.htm
- http://m.blog.fcful.cn/bnews/4372.htm
- http://m.blog.fcful.cn/bnews/239626.htm
- http://m.blog.fcful.cn/bnews/2118.htm
- http://m.blog.fcful.cn/bnews/6286.htm
- http://m.blog.fcful.cn/bnews/7799.htm
- http://m.blog.fcful.cn/bnews/39393.htm
- http://m.blog.fcful.cn/bnews/9490283.htm
- http://m.blog.fcful.cn/bnews/93238.htm
- http://m.blog.fcful.cn/bnews/266446.htm
- http://m.blog.fcful.cn/bnews/8786.htm
- http://m.blog.fcful.cn/bnews/580708.htm
- http://m.blog.fcful.cn/bnews/24980.htm
- http://m.blog.fcful.cn/bnews/8830.htm
- http://m.blog.fcful.cn/bnews/735573.htm
- http://m.blog.fcful.cn/bnews/9347.htm
- http://m.blog.fcful.cn/bnews/50039.htm
- http://m.blog.fcful.cn/bnews/0547.htm
- http://m.blog.fcful.cn/bnews/38486.htm
- http://m.blog.fcful.cn/bnews/6264.htm
- http://m.blog.fcful.cn/bnews/0321.htm
- http://m.blog.fcful.cn/bnews/14771.htm
- http://m.blog.fcful.cn/bnews/7992.htm
- http://m.blog.fcful.cn/bnews/193711.htm
- http://m.blog.fcful.cn/bnews/4163.htm
- http://m.blog.fcful.cn/bnews/6632251.htm
- http://m.blog.fcful.cn/bnews/1816320.htm
- http://m.blog.fcful.cn/bnews/22766.htm
- http://m.blog.fcful.cn/bnews/9871472.htm
- http://m.blog.fcful.cn/bnews/226659.htm
- http://m.blog.fcful.cn/bnews/06401.htm
- http://m.blog.fcful.cn/bnews/763761.htm
- http://m.blog.fcful.cn/bnews/2066240.htm
- http://m.blog.fcful.cn/bnews/9453.htm

## 项目结构

```
webindex/
├── build/                          # 构建输出目录，包含全部静态页面与资源文件
│   ├── index.html                  # 导航首页，展示批次列表与最新资源
│   ├── batch/                      # 批次详情页目录
│   │   └── 104.html                # 第104批次资源清单页面
│   └── assets/                     # 静态资源文件（CSS、JavaScript、图片）
│       ├── css/                    # 样式表文件，含响应式布局与暗色主题
│       ├── js/                     # 前端脚本，实现检索、过滤与交互逻辑
│       └── images/                 # 项目图标与默认占位图
├── data/                           # 数据存储目录，存放资源索引与批次配置
│   ├── batches/                    # 批次数据目录
│   │   ├── 104.json                # 第104批次资源列表（当前活跃批次）
│   │   └── index.json              # 所有批次的元信息汇总
│   └── categories.json             # 分类标签定义与颜色映射配置
├── docs/                           # 项目文档目录
│   ├── user-guide.md               # 用户使用手册
│   ├── maintainer-guide.md         # 维护者操作指南
│   ├── developer-guide.md          # 开发者二次开发文档
│   └── deployment-guide.md         # 部署与运维手册
├── scripts/                        # 工具脚本目录
│   ├── build.js                    # 主构建脚本，负责生成静态页面
│   ├── link-checker.js             # 链接存活检测脚本
│   └── import-csv.js               # 从CSV文件批量导入资源的辅助工具
├── templates/                      # 页面模板目录，用于生成HTML
│   ├── layout.html                 # 基础布局模板，含头部与底部
│   ├── index.html                  # 首页模板
│   └── batch.html                  # 批次详情页模板
├── tests/                          # 单元测试与集成测试目录
│   ├── build.test.js               # 构建流程测试用例
│   └── link-checker.test.js        # 链接检测工具测试用例
├── package.json                    # npm包配置文件，声明依赖与脚本命令
├── package-lock.json               # 依赖版本锁定文件
├── .gitignore                      # Git忽略规则配置
├── .eslintrc.js                    # ESLint代码风格检查配置
└── README.md                       # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻项目仓库至个人账户，并在本地克隆复刻后的版本。创建新的功能分支，分支命名格式为 `feature/描述性名称` 或 `fix/问题编号`，确保分支名称清晰反映变更内容。

2. 在 `data/batches/` 目录下新增或编辑批次 JSON 文件，按照既定 schema 添加资源链接、标题、描述与分类标签。所有新增资源链接需确保可公开访问，且不包含违法或侵权内容。

3. 运行 `npm run test` 执行本地测试套件，确保构建流程与链接检测工具均通过全部测试用例。若新增功能或修改核心逻辑，请同步补充对应的测试用例至 `tests/` 目录。

4. 提交变更时使用语义化提交信息格式，例如 `feat: 添加第105批次资源导入` 或 `fix: 修复移动端导航栏折叠异常`。提交前需确保代码通过 ESLint 检查。

5. 向主仓库发起 Pull Request，在描述中详细说明变更目的、影响范围以及测试覆盖情况。项目维护者将在 48 小时内审阅，并通过合并或提出修改意见的方式给予反馈。

## 常见问题

**问：如何更新已有批次中的资源链接？**

答：直接编辑 `data/batches/` 目录下对应批次的 JSON 文件，修改或删除其中的 URL 条目，随后重新运行 `npm run build` 即可重新生成静态页面。建议在修改前备份原文件，并运行链接检测工具确认新链接的有效性。

**问：WebIndex 是否支持从数据库动态加载资源？**

答：当前版本定位为静态站点生成器，所有资源数据在构建时预编译为静态 HTML。如需动态加载能力，可自行改造后端接口或集成第三方 CMS，但官方维护版本不提供运行时数据库查询支持，以保证部署的简便性与访问速度。

**问：项目是否提供 Docker 镜像以便快速部署？**

答：官方目前未提供预构建的 Docker 镜像。用户可自行编写 Dockerfile 将项目构建产物与 Nginx 或 Caddy 打包为镜像，亦可直接使用 Vercel、Netlify 等平台的一键部署功能。后续版本将考虑发布官方容器镜像。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:18
