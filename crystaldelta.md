# WebLink Navigator

WebLink Navigator 是一个面向技术调研、数据采集和内容聚合场景的轻量级外链资源汇总与导航系统。该项目定位于帮助开发者、研究员与内容运营人员以结构化方式管理和访问大量分散的外部链接资源，提供统一的入口视图、状态标记与快速检索能力，特别适用于处理批次量大、来源单一或域名集中的链接集合。

项目采用静态站点生成与动态筛选相结合的设计思路，核心数据层基于 Markdown 与 YAML Frontmatter 构建，支持将原始链接列表转化为可按类别、批次、状态和关键词过滤的导航面板。项目本身不依赖重型数据库或外部服务，所有资源索引与元数据均可本地维护，适合作为个人知识管理工具、团队共享书签库或自动化采集任务的前端展示层。

目标用户包括需要进行大规模外链归档的技术文档工程师、从事舆情监测与新闻聚合的数据采集人员、以及日常需要维护大量参考链接的软件开发团队。WebLink Navigator 不对链接内容本身做任何修改或代理转发，仅提供元数据标注、分类组织和快速跳转能力，确保原始链接的完整性与可追溯性。

## 功能概览

- 批次化链接管理：支持将链接按导入批次分组展示，当前批次为第 121/240 批，共包含 250 个资源链接，批次信息自动记录并可用于筛选与统计。
- 域名聚合视图：自动识别并提取链接中的根域名与子域名，支持按域名快速筛选同一来源的所有资源，便于分析特定站点的内容分布。
- 原始链接严格保真：系统对用户导入的每条链接执行零改写策略，不添加协议前缀、不补全 www、不修改大小写、不追加尾部斜杠，确保跳转目标与用户预期完全一致。
- 状态标记与进度追踪：每条资源支持自定义状态标签（待阅、已读、待归档、已归档、失效等），并可按状态过滤，方便跟踪处理进度。
- 全文检索与备注系统：支持对链接标题、备注说明和自定义标签进行关键词搜索，备注字段可用于记录摘要、评分或待办事项，提升链接的可用信息密度。
- 静态站点输出与离线可用：项目构建后生成纯静态 HTML 文件，无需运行后端服务即可在浏览器中打开使用，也支持部署到任意 Web 服务器或 CDN。
- 数据导入导出标准化：所有链接数据以 Markdown 表格加 YAML 头信息的形式存储，支持批量导入、导出和版本控制，便于团队协作与数据迁移。

## 应用场景

技术文档团队进行外部参考链接归档
技术文档撰写过程中常需引用大量外部规范、RFC 文档、博客文章和开源项目地址。WebLink Navigator 可作为团队内部统一的参考链接仓库，按批次导入后分配状态与备注，确保文档评审时所有引用来源可查、可验证，避免链接散落在邮件或即时通讯中导致丢失。

数据采集人员管理采集任务中的 URL 清单
在舆情监控或竞品分析等场景中，数据采集人员面对成百上千条待采集的 URL。使用 WebLink Navigator 可将链接按采集批次组织，标记采集状态、记录异常情况，并可配合检索功能快速定位特定域名或关键词对应的链接，提高采集任务的执行效率。

个人研究者构建阅读清单与文献索引
研究人员在阅读文献或浏览技术博客时积累大量待读链接。WebLink Navigator 允许以本地文件方式维护个人阅读清单，按批次记录发现来源，通过状态标记区分已读、待读和需精读，备注字段可用于记录核心观点或引用价值，长期积累后可形成个人化的知识索引。

运维与安全团队监控外部资源变更
运维或安全审计人员需要定期检查依赖的外部资源（如 CDN 地址、第三方 API 文档、开源许可证页面）是否可访问或内容是否变更。通过 WebLink Navigator 导入待监控链接列表，结合定期导出比对或状态更新，可对链接的可用性变化进行追踪记录。

## 快速开始

以下命令演示了从 GitHub 克隆项目、安装依赖并启动开发服务器的完整流程。项目要求 Node.js 环境，构建工具基于 Vite 与 Vue 3。

```bash
# 克隆项目仓库到本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装项目依赖
npm install

# 启动开发服务器，默认监听 localhost:5173
npm run dev
```

执行上述命令后，在浏览器中访问 http://localhost:5173 即可查看当前批次的链接导航界面。如需构建生产环境静态文件，执行 `npm run build`，输出目录为 `dist`。

## 安装要求

项目运行与构建所需的环境依赖及核心工具库如下表所示。所有依赖均为开源组件，可通过 npm 或 yarn 直接安装。

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 项目运行时环境，需支持 ES Module 和 Vite 构建要求 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖和执行脚本命令 |
| Vite | 4.x | 前端构建工具，提供开发服务器与生产打包能力 |
| Vue 3 | 3.3.x | 前端核心框架，用于构建响应式用户界面 |
| marked | 5.x | Markdown 解析器，用于将链接备注或描述字段渲染为 HTML |
| gray-matter | 4.x | YAML Frontmatter 解析工具，用于处理链接元数据文件 |
| vitest | 0.34.x | 单元测试框架，用于运行项目内部功能测试与回归验证 |

## 文档导航

项目文档按使用角色和阅读目标划分为四个层面，下表分别说明各层面文档的目录位置及其主要回答的问题。

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户入门层 | docs/guide/getting-started.md | 如何安装、配置和首次启动项目？如何导入第一批链接并查看效果？ |
| 功能使用层 | docs/guide/usage.md | 如何添加状态标记？如何进行检索与筛选？如何导出当前批次数据？ |
| 数据管理层 | docs/developer/data-format.md | 链接数据文件的格式规范是什么？YAML 字段如何定义？如何自定义分类和标签？ |
| 扩展开发层 | docs/developer/architecture.md | 项目整体架构如何设计？如何新增数据源适配器或自定义 UI 组件？ |

## 资源列表

- http://m.3g.gqskj.cn/xnews/8275283.htm
- http://m.3g.gqskj.cn/xnews/707455.htm
- http://m.3g.gqskj.cn/xnews/8483.htm
- http://m.3g.gqskj.cn/xnews/32785.htm
- http://m.3g.gqskj.cn/xnews/08813.htm
- http://m.3g.gqskj.cn/xnews/05844.htm
- http://m.3g.gqskj.cn/xnews/67381.htm
- http://m.3g.gqskj.cn/xnews/1202100.htm
- http://m.3g.gqskj.cn/xnews/1673609.htm
- http://m.3g.gqskj.cn/xnews/5613.htm
- http://m.3g.gqskj.cn/xnews/5633.htm
- http://m.3g.gqskj.cn/xnews/9607203.htm
- http://m.3g.gqskj.cn/xnews/3972.htm
- http://m.3g.gqskj.cn/xnews/22599.htm
- http://m.3g.gqskj.cn/xnews/651144.htm
- http://m.3g.gqskj.cn/xnews/4795.htm
- http://m.3g.gqskj.cn/xnews/0005.htm
- http://m.3g.gqskj.cn/xnews/463372.htm
- http://m.3g.gqskj.cn/xnews/42042.htm
- http://m.3g.gqskj.cn/xnews/05273.htm
- http://m.3g.gqskj.cn/xnews/020943.htm
- http://m.3g.gqskj.cn/xnews/629046.htm
- http://m.3g.gqskj.cn/xnews/91733.htm
- http://m.3g.gqskj.cn/xnews/50605.htm
- http://m.3g.gqskj.cn/xnews/3793.htm
- http://m.3g.gqskj.cn/xnews/7096067.htm
- http://m.3g.gqskj.cn/xnews/39061.htm
- http://m.3g.gqskj.cn/xnews/46544.htm
- http://m.3g.gqskj.cn/xnews/9872.htm
- http://m.3g.gqskj.cn/xnews/252843.htm
- http://m.3g.gqskj.cn/xnews/3987268.htm
- http://m.3g.gqskj.cn/xnews/083359.htm
- http://m.3g.gqskj.cn/xnews/7850654.htm
- http://m.3g.gqskj.cn/xnews/88047.htm
- http://m.3g.gqskj.cn/xnews/0217187.htm
- http://m.3g.gqskj.cn/xnews/456710.htm
- http://m.3g.gqskj.cn/xnews/977077.htm
- http://m.3g.gqskj.cn/xnews/3203.htm
- http://m.3g.gqskj.cn/xnews/0489003.htm
- http://m.3g.gqskj.cn/xnews/7061539.htm
- http://m.3g.gqskj.cn/xnews/4191322.htm
- http://m.3g.gqskj.cn/xnews/46914.htm
- http://m.3g.gqskj.cn/xnews/1393787.htm
- http://m.3g.gqskj.cn/xnews/7837.htm
- http://m.3g.gqskj.cn/xnews/02652.htm
- http://m.3g.gqskj.cn/xnews/21515.htm
- http://m.3g.gqskj.cn/xnews/09017.htm
- http://m.3g.gqskj.cn/xnews/0443.htm
- http://m.3g.gqskj.cn/xnews/8601330.htm
- http://m.3g.gqskj.cn/xnews/52978.htm
- http://m.3g.gqskj.cn/xnews/9332375.htm
- http://m.3g.gqskj.cn/xnews/925623.htm
- http://m.3g.gqskj.cn/xnews/064112.htm
- http://m.3g.gqskj.cn/xnews/7373.htm
- http://m.3g.gqskj.cn/xnews/9394.htm
- http://m.3g.gqskj.cn/xnews/7896.htm
- http://m.3g.gqskj.cn/xnews/441554.htm
- http://m.3g.gqskj.cn/xnews/839024.htm
- http://m.3g.gqskj.cn/xnews/30972.htm
- http://m.3g.gqskj.cn/xnews/701775.htm
- http://m.3g.gqskj.cn/xnews/7617061.htm
- http://m.3g.gqskj.cn/xnews/474855.htm
- http://m.3g.gqskj.cn/xnews/8720.htm
- http://m.3g.gqskj.cn/xnews/9991820.htm
- http://m.3g.gqskj.cn/xnews/7437588.htm
- http://m.3g.gqskj.cn/xnews/05885.htm
- http://m.3g.gqskj.cn/xnews/4421160.htm
- http://m.3g.gqskj.cn/xnews/68136.htm
- http://m.3g.gqskj.cn/xnews/9556.htm
- http://m.3g.gqskj.cn/xnews/14631.htm
- http://m.3g.gqskj.cn/xnews/78603.htm
- http://m.3g.gqskj.cn/xnews/3795449.htm
- http://m.3g.gqskj.cn/xnews/4659.htm
- http://m.3g.gqskj.cn/xnews/57445.htm
- http://m.3g.gqskj.cn/xnews/6347859.htm
- http://m.3g.gqskj.cn/xnews/1511.htm
- http://m.3g.gqskj.cn/xnews/701104.htm
- http://m.3g.gqskj.cn/xnews/877231.htm
- http://m.3g.gqskj.cn/xnews/83507.htm
- http://m.3g.gqskj.cn/xnews/8512088.htm
- http://m.3g.gqskj.cn/xnews/842580.htm
- http://m.3g.gqskj.cn/xnews/316194.htm
- http://m.3g.gqskj.cn/xnews/489700.htm
- http://m.3g.gqskj.cn/xnews/5080455.htm
- http://m.3g.gqskj.cn/xnews/914864.htm
- http://m.3g.gqskj.cn/xnews/4500174.htm
- http://m.3g.gqskj.cn/xnews/6399083.htm
- http://m.3g.gqskj.cn/xnews/7827.htm
- http://m.3g.gqskj.cn/xnews/6981370.htm
- http://m.3g.gqskj.cn/xnews/737051.htm
- http://m.3g.gqskj.cn/xnews/1604779.htm
- http://m.3g.gqskj.cn/xnews/0066464.htm
- http://m.3g.gqskj.cn/xnews/9693.htm
- http://m.3g.gqskj.cn/xnews/39708.htm
- http://m.3g.gqskj.cn/xnews/56637.htm
- http://m.3g.gqskj.cn/xnews/03803.htm
- http://m.3g.gqskj.cn/xnews/721571.htm
- http://m.3g.gqskj.cn/xnews/5124.htm
- http://m.3g.gqskj.cn/xnews/127310.htm
- http://m.3g.gqskj.cn/xnews/48282.htm
- http://m.3g.gqskj.cn/xnews/068876.htm
- http://m.3g.gqskj.cn/xnews/7312563.htm
- http://m.3g.gqskj.cn/xnews/17687.htm
- http://m.3g.gqskj.cn/xnews/5535.htm
- http://m.3g.gqskj.cn/xnews/3225.htm
- http://m.3g.gqskj.cn/xnews/8058907.htm
- http://m.3g.gqskj.cn/xnews/0512.htm
- http://m.3g.gqskj.cn/xnews/1865784.htm
- http://m.3g.gqskj.cn/xnews/99392.htm
- http://m.3g.gqskj.cn/xnews/7020991.htm
- http://m.3g.gqskj.cn/xnews/6881.htm
- http://m.3g.gqskj.cn/xnews/19567.htm
- http://m.3g.gqskj.cn/xnews/31985.htm
- http://m.3g.gqskj.cn/xnews/11763.htm
- http://m.3g.gqskj.cn/xnews/02621.htm
- http://m.3g.gqskj.cn/xnews/9319193.htm
- http://m.3g.gqskj.cn/xnews/1947.htm
- http://m.3g.gqskj.cn/xnews/9046.htm
- http://m.3g.gqskj.cn/xnews/9684.htm
- http://m.3g.gqskj.cn/xnews/5962.htm
- http://m.3g.gqskj.cn/xnews/44965.htm
- http://m.3g.gqskj.cn/xnews/7067.htm
- http://m.3g.gqskj.cn/xnews/591120.htm
- http://m.3g.gqskj.cn/xnews/56976.htm
- http://m.3g.gqskj.cn/xnews/38466.htm
- http://m.3g.gqskj.cn/xnews/8646484.htm
- http://m.3g.gqskj.cn/xnews/7805.htm
- http://m.3g.gqskj.cn/xnews/5795.htm
- http://m.3g.gqskj.cn/xnews/60751.htm
- http://m.3g.gqskj.cn/xnews/17780.htm
- http://m.3g.gqskj.cn/xnews/3388.htm
- http://m.3g.gqskj.cn/xnews/9196.htm
- http://m.3g.gqskj.cn/xnews/84309.htm
- http://m.3g.gqskj.cn/xnews/1346776.htm
- http://m.3g.gqskj.cn/xnews/80819.htm
- http://m.3g.gqskj.cn/xnews/795052.htm
- http://m.3g.gqskj.cn/xnews/94145.htm
- http://m.3g.gqskj.cn/xnews/2657823.htm
- http://m.3g.gqskj.cn/xnews/653755.htm
- http://m.3g.gqskj.cn/xnews/88012.htm
- http://m.3g.gqskj.cn/xnews/3157214.htm
- http://m.3g.gqskj.cn/xnews/31625.htm
- http://m.3g.gqskj.cn/xnews/43242.htm
- http://m.3g.gqskj.cn/xnews/976046.htm
- http://m.3g.gqskj.cn/xnews/038357.htm
- http://m.3g.gqskj.cn/xnews/011739.htm
- http://m.3g.gqskj.cn/xnews/78894.htm
- http://m.3g.gqskj.cn/xnews/9841686.htm
- http://m.3g.gqskj.cn/xnews/3155.htm
- http://m.3g.gqskj.cn/xnews/724086.htm
- http://m.3g.gqskj.cn/xnews/257271.htm
- http://m.3g.gqskj.cn/xnews/3732166.htm
- http://m.3g.gqskj.cn/xnews/2549.htm
- http://m.3g.gqskj.cn/xnews/8073661.htm
- http://m.3g.gqskj.cn/xnews/2176.htm
- http://m.3g.gqskj.cn/xnews/8114.htm
- http://m.3g.gqskj.cn/xnews/9853456.htm
- http://m.3g.gqskj.cn/xnews/4068283.htm
- http://m.3g.gqskj.cn/xnews/45880.htm
- http://m.3g.gqskj.cn/xnews/589310.htm
- http://m.3g.gqskj.cn/xnews/86071.htm
- http://m.3g.gqskj.cn/xnews/5835.htm
- http://m.3g.gqskj.cn/xnews/39296.htm
- http://m.3g.gqskj.cn/xnews/22841.htm
- http://m.3g.gqskj.cn/xnews/0922.htm
- http://m.3g.gqskj.cn/xnews/996579.htm
- http://m.3g.gqskj.cn/xnews/2611.htm
- http://m.3g.gqskj.cn/xnews/8328340.htm
- http://m.3g.gqskj.cn/xnews/6111.htm
- http://m.3g.gqskj.cn/xnews/07354.htm
- http://m.3g.gqskj.cn/xnews/8101.htm
- http://m.3g.gqskj.cn/xnews/47847.htm
- http://m.3g.gqskj.cn/xnews/691058.htm
- http://m.3g.gqskj.cn/xnews/17265.htm
- http://m.3g.gqskj.cn/xnews/521393.htm
- http://m.3g.gqskj.cn/xnews/53396.htm
- http://m.3g.gqskj.cn/xnews/9835979.htm
- http://m.3g.gqskj.cn/xnews/3360.htm
- http://m.3g.gqskj.cn/xnews/1363.htm
- http://m.3g.gqskj.cn/xnews/0456468.htm
- http://m.3g.gqskj.cn/xnews/3101009.htm
- http://m.3g.gqskj.cn/xnews/9209.htm
- http://m.3g.gqskj.cn/xnews/5270130.htm
- http://m.3g.gqskj.cn/xnews/6996660.htm
- http://m.3g.gqskj.cn/xnews/8452573.htm
- http://m.3g.gqskj.cn/xnews/579856.htm
- http://m.3g.gqskj.cn/xnews/21446.htm
- http://m.3g.gqskj.cn/xnews/535300.htm
- http://m.3g.gqskj.cn/xnews/723642.htm
- http://m.3g.gqskj.cn/xnews/123957.htm
- http://m.3g.gqskj.cn/xnews/1075125.htm
- http://m.3g.gqskj.cn/xnews/0828.htm
- http://m.3g.gqskj.cn/xnews/6454131.htm
- http://m.3g.gqskj.cn/xnews/31465.htm
- http://m.3g.gqskj.cn/xnews/753229.htm
- http://m.3g.gqskj.cn/xnews/8473147.htm
- http://m.3g.gqskj.cn/xnews/3639725.htm
- http://m.3g.gqskj.cn/xnews/119960.htm
- http://m.3g.gqskj.cn/xnews/688194.htm
- http://m.3g.gqskj.cn/xnews/125356.htm
- http://m.3g.gqskj.cn/xnews/79892.htm
- http://m.3g.gqskj.cn/xnews/31421.htm
- http://m.3g.gqskj.cn/xnews/879739.htm
- http://m.3g.gqskj.cn/xnews/3233.htm
- http://m.3g.gqskj.cn/xnews/6894.htm
- http://m.3g.gqskj.cn/xnews/06966.htm
- http://m.3g.gqskj.cn/xnews/3901.htm
- http://m.3g.gqskj.cn/xnews/71449.htm
- http://m.3g.gqskj.cn/xnews/2290280.htm
- http://m.3g.gqskj.cn/xnews/38525.htm
- http://m.3g.gqskj.cn/xnews/26667.htm
- http://m.3g.gqskj.cn/xnews/7964.htm
- http://m.3g.gqskj.cn/xnews/77560.htm
- http://m.3g.gqskj.cn/xnews/8869411.htm
- http://m.3g.gqskj.cn/xnews/3071.htm
- http://m.3g.gqskj.cn/xnews/946212.htm
- http://m.3g.gqskj.cn/xnews/4187.htm
- http://m.3g.gqskj.cn/xnews/505541.htm
- http://m.3g.gqskj.cn/xnews/89571.htm
- http://m.3g.gqskj.cn/xnews/7982.htm
- http://m.3g.gqskj.cn/xnews/3250.htm
- http://m.3g.gqskj.cn/xnews/316297.htm
- http://m.3g.gqskj.cn/xnews/4463133.htm
- http://m.3g.gqskj.cn/xnews/509497.htm
- http://m.3g.gqskj.cn/xnews/166910.htm
- http://m.3g.gqskj.cn/xnews/6700676.htm
- http://m.3g.gqskj.cn/xnews/6270027.htm
- http://m.3g.gqskj.cn/xnews/897467.htm
- http://m.3g.gqskj.cn/xnews/756316.htm
- http://m.3g.gqskj.cn/xnews/126622.htm
- http://m.3g.gqskj.cn/xnews/6039572.htm
- http://m.3g.gqskj.cn/xnews/0889167.htm
- http://m.3g.gqskj.cn/xnews/988057.htm
- http://m.3g.gqskj.cn/xnews/8640.htm
- http://m.3g.gqskj.cn/xnews/6317.htm
- http://m.3g.gqskj.cn/xnews/0655134.htm
- http://m.3g.gqskj.cn/xnews/55787.htm
- http://m.3g.gqskj.cn/xnews/315179.htm
- http://m.3g.gqskj.cn/xnews/8351163.htm
- http://m.3g.gqskj.cn/xnews/6647.htm
- http://m.3g.gqskj.cn/xnews/6142200.htm
- http://m.3g.gqskj.cn/xnews/888876.htm
- http://m.3g.gqskj.cn/xnews/5008259.htm
- http://m.3g.gqskj.cn/xnews/78049.htm
- http://m.3g.gqskj.cn/xnews/1053577.htm
- http://m.3g.gqskj.cn/xnews/985300.htm
- http://m.3g.gqskj.cn/xnews/157014.htm
- http://m.3g.gqskj.cn/xnews/9483.htm
- http://m.3g.gqskj.cn/xnews/8643468.htm
- http://m.3g.gqskj.cn/xnews/6388.htm

## 项目结构

项目源码目录组织遵循前端工程化最佳实践，各模块职责清晰，便于后续维护与扩展。

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── main.js                         # 应用入口文件，负责初始化 Vue 实例与全局配置
│   ├── App.vue                         # 根组件，定义整体布局与路由出口
│   ├── assets/                         # 静态资源目录，存放样式、图片与字体文件
│   │   ├── styles/                     # 全局 CSS 与主题变量定义
│   │   └── images/                     # 项目图标与占位图
│   ├── components/                     # 可复用 Vue 组件目录
│   │   ├── LinkList.vue                # 链接列表核心组件，负责渲染资源条目与状态标记
│   │   ├── FilterPanel.vue             # 筛选面板组件，提供域名、状态、关键词筛选交互
│   │   ├── BatchInfo.vue               # 批次信息展示组件，显示当前批次号与资源总数
│   │   └── LinkDetail.vue              # 链接详情弹窗组件，展示备注、状态变更历史
│   ├── composables/                    # 组合式函数目录，封装可复用的逻辑
│   │   ├── useLinks.js                 # 链接数据的加载、筛选与状态管理逻辑
│   │   └── useFilter.js                # 筛选条件的状态管理与组合逻辑
│   ├── data/                           # 数据层目录，存放链接数据文件与解析工具
│   │   ├── batch-121.yaml              # 第 121 批链接数据，包含原始 URL 与元数据
│   │   └── linkParser.js               # 链接数据解析与校验工具函数
│   └── utils/                          # 通用工具函数目录
│       ├── urlUtils.js                 # URL 解析、域名提取、格式校验工具
│       └── storageUtils.js             # 本地存储读写与数据持久化工具
├── docs/                               # 项目文档目录，包含用户指南与开发文档
│   ├── guide/                          # 用户使用指南
│   └── developer/                      # 开发者文档与 API 参考
├── tests/                              # 单元测试目录
│   ├── unit/                           # 基于 Vitest 的单元测试用例
│   └── fixtures/                       # 测试用的固定数据样本
├── index.html                          # 项目主页面模板，Vite 构建入口
├── vite.config.js                      # Vite 构建配置文件，包含插件与路径别名设置
├── package.json                        # 项目依赖声明与脚本命令定义
├── package-lock.json                   # 依赖版本锁定文件
└── README.md                           # 项目自述文件（当前文档）
```

## 贡献指南

WebLink Navigator 欢迎社区贡献，包括但不限于功能建议、Bug 报告、代码提交和文档改进。请遵循以下步骤参与项目开发。

提交 Issue 进行问题反馈或功能建议
在 GitHub 仓库的 Issues 页面新建 Issue，使用提供的模板描述问题或建议。对于 Bug 报告，请附上复现步骤、预期行为与实际行为；对于功能建议，请清晰说明使用场景与价值。

Fork 仓库并创建功能分支
将项目 Fork 至个人账户，然后基于 main 分支创建新的功能分支，分支命名建议采用 `feat/功能简述` 或 `fix/问题简述` 格式，便于识别。

编写代码并确保测试通过
在本地开发环境中完成代码修改后，运行 `npm run test` 执行所有单元测试用例，确保新增或修改的代码未破坏现有功能。对于新增功能，请同步编写对应的测试用例。

提交 Pull Request 并等待代码审查
将功能分支推送至个人 Fork 仓库后，向主仓库的 main 分支提交 Pull Request。请在 PR 描述中关联相关 Issue 编号，并简要说明修改内容与影响范围。PR 需要至少一名项目维护者批准后方可合并。

## 常见问题

项目在初始化或运行过程中可能遇到以下典型问题，对应的解决方案如下。

如何导入自定义批次的外部链接数据？
项目支持通过 YAML 文件导入自定义链接数据。请在 `src/data/` 目录下新建 YAML 文件，按照 `batch-121.yaml` 的格式组织数据，字段包括 `id`、`url`、`title`、`status` 和 `remark`。导入后需重新运行 `npm run dev` 刷新数据索引。未来版本将提供图形化导入界面。

构建生产环境时出现内存不足或构建失败的错误
生产构建对内存有一定要求，建议在构建前关闭其他占用内存较大的应用程序。如果仍出现内存不足，可在 `package.json` 的 `build` 脚本中添加 `--max-old-space-size=4096` 参数以增加 Node.js 内存限制。例如：`"build": "NODE_OPTIONS=--max-old-space-size=4096 vite build"`。

链接列表加载后显示为空白或部分链接不显示
此情况通常由数据文件格式错误引起。请检查 `src/data/` 目录下的 YAML 文件是否符合格式规范，特别关注缩进、引号和特殊字符转义。项目在开发模式下会在浏览器控制台输出解析错误日志，可根据错误提示定位并修正数据文件。如确认数据文件无误但仍无法显示，可尝试清除浏览器本地缓存后重新加载。

## 许可证

MIT License

Copyright (c) 2026 WebLink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:45
