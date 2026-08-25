# LinkVault 聚合索引系统

LinkVault 是一个面向技术内容聚合与轻量级知识索引的开源工具集，专注于将分散在各类新闻、公告、技术笔记与信息流中的半结构化数据转化为可检索、可标签化、可版本追踪的本地知识资产。项目目标用户包括技术文档维护者、信息采集工程师、个人知识管理爱好者以及需要长期追踪特定域名或内容路径变化的运营人员。LinkVault 不依赖外部数据库，不强制绑定云服务，所有索引数据以纯文本与 JSON 格式存储于本地，便于用户使用标准命令行工具或脚本进行二次加工。通过将原始链接映射为结构化条目，LinkVault 帮助用户从大量原始 URL 中提炼出稳定的标识符、内容指纹与时间戳特征，从而降低信息漂移带来的追踪成本。

## 功能概览

批量导入与规范化清洗 支持从纯文本文件、CSV 或标准输入流中导入原始 URL 列表，自动去除空白行、重复条目，并对 URL 进行协议一致性检查与路径归一化处理，同时保留原始链接的完整字符串形式作为不可变字段。

内容指纹提取与去重 对每个 URL 指向的资源执行轻量级 HTTP 头探测，根据 Content-Length、Last-Modified 及 ETag 生成内容指纹，辅助用户识别内容相同但路径不同的资源副本，减少冗余索引条目。

标签系统与多级分类 允许用户为每个条目附加自由标签，并支持标签层级结构（如 tech/frontend/react、news/industry/2026），标签数据独立存储于标签索引文件中，支持批量导入导出与冲突合并。

增量更新与变更追踪 通过记录首次发现时间、最近验证时间以及 HTTP 状态码历史，LinkVault 能够生成变更报告，标记状态从 200 变为 404 或 302 的链接，帮助用户主动发现内容迁移或失效情况。

全文检索与正则过滤 内置基于 ripgrep 风格的正则搜索接口，支持在 URL 字符串、标签集合、自定义备注字段中进行快速检索，检索结果支持按时间、状态码或自定义权重排序，并输出为 JSON Lines 格式供下游工具使用。

快照导出与订阅生成 支持将索引子集导出为静态 HTML 目录、RSS 订阅源或 Markdown 引用列表，方便用户将稳定的资源集合嵌入到自己的文档站点或知识库中。

插件钩子系统 提供基于 shell 脚本或任意可执行文件的钩子机制，允许用户在导入、更新、导出等阶段触发自定义处理逻辑，例如调用外部翻译 API、生成缩略图或发送通知。

## 应用场景

文档站外链监控 技术文档团队可以使用 LinkVault 定期扫描文档中引用的外部链接，生成状态报告，及时发现失效引用并在文档发布前修复，避免用户体验受损。

行业动态聚合简报 信息分析人员可将多个新闻类域名下的特定路径模式导入 LinkVault，配合标签系统与变更追踪，每日生成增量简报，只关注新增或状态发生变化的内容，减少重复阅读。

个人书签库去重与整理 长期收藏技术文章的用户可利用指纹去重功能合并重复收藏，然后通过标签层级整理为“待读”“已读”“参考”等分类，并导出为静态索引页，便于在不同浏览器间共享。

历史资源迁移辅助 在进行站点改版或域名迁移时，运维人员可使用 LinkVault 导出所有旧链接及其状态历史，与迁移映射表进行比对，生成重定向验证清单，降低迁移遗漏风险。

## 快速开始

以下命令演示了从克隆仓库到运行基础索引任务的完整流程。

```bash
git clone https://github.com/example/linkvault.git
cd linkvault
pip install -e .
linkvault init --db ./data
linkvault import --input ./samples/urls.txt --tag news
linkvault status --report ./reports/status_latest.json
linkvault export --format html --output ./docs/index.html
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于执行导入、索引、导出及钩子调度逻辑 |
| ripgrep | 13.0.0 及以上 | 用于提供高性能正则全文检索能力，若未安装则回退至 Python 内置 re 模块 |
| git | 2.25 及以上 | 用于版本控制与仓库克隆，非运行时强制依赖，但推荐用于更新管理 |
| curl | 7.68 及以上 | 用于 HTTP 探测与内容指纹获取，若缺失则使用 urllib 备用实现 |
| jq | 1.6 及以上 | 用于 JSON 数据的命令行格式化与过滤，在导出和报告生成环节提升效率 |
| sqlite3 | 3.31 及以上 | 用于可选的关系型存储后端，默认使用 JSON 文件存储，此依赖仅在启用 SQLite 模式时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/guide/getting-started.md | 如何安装、初始化数据库、执行第一次导入与查看状态 |
| 配置手册 | docs/guide/configuration.md | 如何配置标签映射、钩子脚本路径、存储后端及日志级别 |
| 命令参考 | docs/reference/cli.md | 所有子命令（init、import、status、export、search、hook）的完整参数说明与示例 |
| 钩子开发 | docs/developer/hooks.md | 如何编写自定义钩子脚本，传递的数据结构格式及错误处理规范 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/5829318.htm
- http://m.3g.gqskj.cn/xnews/8529.htm
- http://m.3g.gqskj.cn/xnews/48377.htm
- http://m.3g.gqskj.cn/xnews/4182.htm
- http://m.3g.gqskj.cn/xnews/09880.htm
- http://m.3g.gqskj.cn/xnews/7183868.htm
- http://m.3g.gqskj.cn/xnews/01639.htm
- http://m.3g.gqskj.cn/xnews/900649.htm
- http://m.3g.gqskj.cn/xnews/8035.htm
- http://m.3g.gqskj.cn/xnews/2867.htm
- http://m.3g.gqskj.cn/xnews/8068742.htm
- http://m.3g.gqskj.cn/xnews/16737.htm
- http://m.3g.gqskj.cn/xnews/35609.htm
- http://m.3g.gqskj.cn/xnews/333444.htm
- http://m.3g.gqskj.cn/xnews/0906665.htm
- http://m.3g.gqskj.cn/xnews/8076.htm
- http://m.3g.gqskj.cn/xnews/5475869.htm
- http://m.3g.gqskj.cn/xnews/3618.htm
- http://m.3g.gqskj.cn/xnews/7966018.htm
- http://m.3g.gqskj.cn/xnews/55351.htm
- http://m.3g.gqskj.cn/xnews/947494.htm
- http://m.3g.gqskj.cn/xnews/7183522.htm
- http://m.3g.gqskj.cn/xnews/9890.htm
- http://m.3g.gqskj.cn/xnews/413055.htm
- http://m.3g.gqskj.cn/xnews/050466.htm
- http://m.3g.gqskj.cn/xnews/4863638.htm
- http://m.3g.gqskj.cn/xnews/1977686.htm
- http://m.3g.gqskj.cn/xnews/3570.htm
- http://m.3g.gqskj.cn/xnews/72597.htm
- http://m.3g.gqskj.cn/xnews/72341.htm
- http://m.3g.gqskj.cn/xnews/71398.htm
- http://m.3g.gqskj.cn/xnews/98015.htm
- http://m.3g.gqskj.cn/xnews/29107.htm
- http://m.3g.gqskj.cn/xnews/8955191.htm
- http://m.3g.gqskj.cn/xnews/96858.htm
- http://m.3g.gqskj.cn/xnews/0482.htm
- http://m.3g.gqskj.cn/xnews/5413629.htm
- http://m.3g.gqskj.cn/xnews/13720.htm
- http://m.3g.gqskj.cn/xnews/824140.htm
- http://m.3g.gqskj.cn/xnews/2223.htm
- http://m.3g.gqskj.cn/xnews/17795.htm
- http://m.3g.gqskj.cn/xnews/830562.htm
- http://m.3g.gqskj.cn/xnews/5587.htm
- http://m.3g.gqskj.cn/xnews/3294.htm
- http://m.3g.gqskj.cn/xnews/76007.htm
- http://m.3g.gqskj.cn/xnews/174013.htm
- http://m.3g.gqskj.cn/xnews/7620343.htm
- http://m.3g.gqskj.cn/xnews/38625.htm
- http://m.3g.gqskj.cn/xnews/6018389.htm
- http://m.3g.gqskj.cn/xnews/4348865.htm
- http://m.3g.gqskj.cn/xnews/85420.htm
- http://m.3g.gqskj.cn/xnews/15856.htm
- http://m.3g.gqskj.cn/xnews/65862.htm
- http://m.3g.gqskj.cn/xnews/7339.htm
- http://m.3g.gqskj.cn/xnews/8074418.htm
- http://m.3g.gqskj.cn/xnews/141707.htm
- http://m.3g.gqskj.cn/xnews/49225.htm
- http://m.3g.gqskj.cn/xnews/9702.htm
- http://m.3g.gqskj.cn/xnews/5420.htm
- http://m.3g.gqskj.cn/xnews/9587480.htm
- http://m.3g.gqskj.cn/xnews/0659131.htm
- http://m.3g.gqskj.cn/xnews/4061.htm
- http://m.3g.gqskj.cn/xnews/74890.htm
- http://m.3g.gqskj.cn/xnews/3373559.htm
- http://m.3g.gqskj.cn/xnews/69697.htm
- http://m.3g.gqskj.cn/xnews/0192948.htm
- http://m.3g.gqskj.cn/xnews/5174.htm
- http://m.3g.gqskj.cn/xnews/91639.htm
- http://m.3g.gqskj.cn/xnews/767963.htm
- http://m.3g.gqskj.cn/xnews/877659.htm
- http://m.3g.gqskj.cn/xnews/09640.htm
- http://m.3g.gqskj.cn/xnews/0388.htm
- http://m.3g.gqskj.cn/xnews/5140.htm
- http://m.3g.gqskj.cn/xnews/52559.htm
- http://m.3g.gqskj.cn/xnews/961738.htm
- http://m.3g.gqskj.cn/xnews/8368.htm
- http://m.3g.gqskj.cn/xnews/919606.htm
- http://m.3g.gqskj.cn/xnews/697189.htm
- http://m.3g.gqskj.cn/xnews/0921047.htm
- http://m.3g.gqskj.cn/xnews/5417.htm
- http://m.3g.gqskj.cn/xnews/368021.htm
- http://m.3g.gqskj.cn/xnews/439713.htm
- http://m.3g.gqskj.cn/xnews/10363.htm
- http://m.3g.gqskj.cn/xnews/9526.htm
- http://m.3g.gqskj.cn/xnews/0455403.htm
- http://m.3g.gqskj.cn/xnews/9135.htm
- http://m.3g.gqskj.cn/xnews/3297051.htm
- http://m.3g.gqskj.cn/xnews/6539.htm
- http://m.3g.gqskj.cn/xnews/15891.htm
- http://m.3g.gqskj.cn/xnews/2039.htm
- http://m.3g.gqskj.cn/xnews/9664.htm
- http://m.3g.gqskj.cn/xnews/5975.htm
- http://m.3g.gqskj.cn/xnews/0674345.htm
- http://m.3g.gqskj.cn/xnews/364529.htm
- http://m.3g.gqskj.cn/xnews/8954193.htm
- http://m.3g.gqskj.cn/xnews/1279.htm
- http://m.3g.gqskj.cn/xnews/7227.htm
- http://m.3g.gqskj.cn/xnews/39957.htm
- http://m.3g.gqskj.cn/xnews/15382.htm
- http://m.3g.gqskj.cn/xnews/867050.htm
- http://m.3g.gqskj.cn/xnews/157159.htm
- http://m.3g.gqskj.cn/xnews/4619.htm
- http://m.3g.gqskj.cn/xnews/718280.htm
- http://m.3g.gqskj.cn/xnews/088750.htm
- http://m.3g.gqskj.cn/xnews/39702.htm
- http://m.3g.gqskj.cn/xnews/19912.htm
- http://m.3g.gqskj.cn/xnews/9050924.htm
- http://m.3g.gqskj.cn/xnews/022379.htm
- http://m.3g.gqskj.cn/xnews/5604.htm
- http://m.3g.gqskj.cn/xnews/24459.htm
- http://m.3g.gqskj.cn/xnews/3578.htm
- http://m.3g.gqskj.cn/xnews/5862.htm
- http://m.3g.gqskj.cn/xnews/0470.htm
- http://m.3g.gqskj.cn/xnews/35536.htm
- http://m.3g.gqskj.cn/xnews/2013538.htm
- http://m.3g.gqskj.cn/xnews/00311.htm
- http://m.3g.gqskj.cn/xnews/4251041.htm
- http://m.3g.gqskj.cn/xnews/2676467.htm
- http://m.3g.gqskj.cn/xnews/110904.htm
- http://m.3g.gqskj.cn/xnews/127569.htm
- http://m.3g.gqskj.cn/xnews/4525.htm
- http://m.3g.gqskj.cn/xnews/98220.htm
- http://m.3g.gqskj.cn/xnews/34984.htm
- http://m.3g.gqskj.cn/xnews/59853.htm
- http://m.3g.gqskj.cn/xnews/71311.htm
- http://m.3g.gqskj.cn/xnews/73436.htm
- http://m.3g.gqskj.cn/xnews/825509.htm
- http://m.3g.gqskj.cn/xnews/042917.htm
- http://m.3g.gqskj.cn/xnews/8190.htm
- http://m.3g.gqskj.cn/xnews/59639.htm
- http://m.3g.gqskj.cn/xnews/6324.htm
- http://m.3g.gqskj.cn/xnews/4140764.htm
- http://m.3g.gqskj.cn/xnews/005869.htm
- http://m.3g.gqskj.cn/xnews/219173.htm
- http://m.3g.gqskj.cn/xnews/3467.htm
- http://m.3g.gqskj.cn/xnews/9297.htm
- http://m.3g.gqskj.cn/xnews/1755.htm
- http://m.3g.gqskj.cn/xnews/242803.htm
- http://m.3g.gqskj.cn/xnews/0706005.htm
- http://m.3g.gqskj.cn/xnews/7280.htm
- http://m.3g.gqskj.cn/xnews/207464.htm
- http://m.3g.gqskj.cn/xnews/3730.htm
- http://m.3g.gqskj.cn/xnews/8664.htm
- http://m.3g.gqskj.cn/xnews/70859.htm
- http://m.3g.gqskj.cn/xnews/2416178.htm
- http://m.3g.gqskj.cn/xnews/0439945.htm
- http://m.3g.gqskj.cn/xnews/876611.htm
- http://m.3g.gqskj.cn/xnews/85892.htm
- http://m.3g.gqskj.cn/xnews/061721.htm
- http://m.3g.gqskj.cn/xnews/7165.htm
- http://m.3g.gqskj.cn/xnews/0485.htm
- http://m.3g.gqskj.cn/xnews/23631.htm
- http://m.3g.gqskj.cn/xnews/1634.htm
- http://m.3g.gqskj.cn/xnews/4471.htm
- http://m.3g.gqskj.cn/xnews/955090.htm
- http://m.3g.gqskj.cn/xnews/4128441.htm
- http://m.3g.gqskj.cn/xnews/7516813.htm
- http://m.3g.gqskj.cn/xnews/2598.htm
- http://m.3g.gqskj.cn/xnews/26813.htm
- http://m.3g.gqskj.cn/xnews/956070.htm
- http://m.3g.gqskj.cn/xnews/4003284.htm
- http://m.3g.gqskj.cn/xnews/914711.htm
- http://m.3g.gqskj.cn/xnews/64558.htm
- http://m.3g.gqskj.cn/xnews/94228.htm
- http://m.3g.gqskj.cn/xnews/60486.htm
- http://m.3g.gqskj.cn/xnews/798337.htm
- http://m.3g.gqskj.cn/xnews/8345.htm
- http://m.3g.gqskj.cn/xnews/5282808.htm
- http://m.3g.gqskj.cn/xnews/8660577.htm
- http://m.3g.gqskj.cn/xnews/758286.htm
- http://m.3g.gqskj.cn/xnews/2770145.htm
- http://m.3g.gqskj.cn/xnews/49188.htm
- http://m.3g.gqskj.cn/xnews/73386.htm
- http://m.3g.gqskj.cn/xnews/27963.htm
- http://m.3g.gqskj.cn/xnews/347602.htm
- http://m.3g.gqskj.cn/xnews/060764.htm
- http://m.3g.gqskj.cn/xnews/92805.htm
- http://m.3g.gqskj.cn/xnews/69609.htm
- http://m.3g.gqskj.cn/xnews/345278.htm
- http://m.3g.gqskj.cn/xnews/80590.htm
- http://m.3g.gqskj.cn/xnews/023350.htm
- http://m.3g.gqskj.cn/xnews/0659180.htm
- http://m.3g.gqskj.cn/xnews/4592220.htm
- http://m.3g.gqskj.cn/xnews/3955847.htm
- http://m.3g.gqskj.cn/xnews/8527.htm
- http://m.3g.gqskj.cn/xnews/283533.htm
- http://m.3g.gqskj.cn/xnews/2643491.htm
- http://m.3g.gqskj.cn/xnews/0739607.htm
- http://m.3g.gqskj.cn/xnews/7984839.htm
- http://m.3g.gqskj.cn/xnews/5930068.htm
- http://m.3g.gqskj.cn/xnews/111125.htm
- http://m.3g.gqskj.cn/xnews/9180.htm
- http://m.3g.gqskj.cn/xnews/930099.htm
- http://m.3g.gqskj.cn/xnews/992642.htm
- http://m.3g.gqskj.cn/xnews/228704.htm
- http://m.3g.gqskj.cn/xnews/02877.htm
- http://m.3g.gqskj.cn/xnews/54203.htm
- http://m.3g.gqskj.cn/xnews/1615.htm
- http://m.3g.gqskj.cn/xnews/6504.htm
- http://m.3g.gqskj.cn/xnews/792290.htm
- http://m.3g.gqskj.cn/xnews/522327.htm
- http://m.3g.gqskj.cn/xnews/9397.htm
- http://m.3g.gqskj.cn/xnews/0679398.htm
- http://m.3g.gqskj.cn/xnews/34322.htm
- http://m.3g.gqskj.cn/xnews/11389.htm
- http://m.3g.gqskj.cn/xnews/2803.htm
- http://m.3g.gqskj.cn/xnews/8879533.htm
- http://m.3g.gqskj.cn/xnews/312678.htm
- http://m.3g.gqskj.cn/xnews/7156.htm
- http://m.3g.gqskj.cn/xnews/068595.htm
- http://m.3g.gqskj.cn/xnews/4114496.htm
- http://m.3g.gqskj.cn/xnews/204074.htm
- http://m.3g.gqskj.cn/xnews/0770708.htm
- http://m.3g.gqskj.cn/xnews/5807573.htm
- http://m.3g.gqskj.cn/xnews/961185.htm
- http://m.3g.gqskj.cn/xnews/5044.htm
- http://m.3g.gqskj.cn/xnews/9215490.htm
- http://m.3g.gqskj.cn/xnews/4167164.htm
- http://m.3g.gqskj.cn/xnews/2396.htm
- http://m.3g.gqskj.cn/xnews/492568.htm
- http://m.3g.gqskj.cn/xnews/0653375.htm
- http://m.3g.gqskj.cn/xnews/815170.htm
- http://m.3g.gqskj.cn/xnews/74594.htm
- http://m.3g.gqskj.cn/xnews/478515.htm
- http://m.3g.gqskj.cn/xnews/5304718.htm
- http://m.3g.gqskj.cn/xnews/1709.htm
- http://m.3g.gqskj.cn/xnews/3239689.htm
- http://m.3g.gqskj.cn/xnews/12457.htm
- http://m.3g.gqskj.cn/xnews/626928.htm
- http://m.3g.gqskj.cn/xnews/881264.htm
- http://m.3g.gqskj.cn/xnews/58446.htm
- http://m.3g.gqskj.cn/xnews/1621.htm
- http://m.3g.gqskj.cn/xnews/1230380.htm
- http://m.3g.gqskj.cn/xnews/979397.htm
- http://m.3g.gqskj.cn/xnews/6639323.htm
- http://m.3g.gqskj.cn/xnews/51511.htm
- http://m.3g.gqskj.cn/xnews/18690.htm
- http://m.3g.gqskj.cn/xnews/64289.htm
- http://m.3g.gqskj.cn/xnews/45124.htm
- http://m.3g.gqskj.cn/xnews/6759698.htm
- http://m.3g.gqskj.cn/xnews/7535214.htm
- http://m.3g.gqskj.cn/xnews/6115518.htm
- http://m.3g.gqskj.cn/xnews/31877.htm
- http://m.3g.gqskj.cn/xnews/9455141.htm
- http://m.3g.gqskj.cn/xnews/14050.htm
- http://m.3g.gqskj.cn/xnews/94820.htm
- http://m.3g.gqskj.cn/xnews/314696.htm
- http://m.3g.gqskj.cn/xnews/65172.htm
- http://m.3g.gqskj.cn/xnews/02574.htm
- http://m.3g.gqskj.cn/xnews/178741.htm

## 项目结构

```
linkvault/
├── bin/                                 # 可执行脚本与命令行入口
│   └── linkvault                        # 主命令行入口文件，解析子命令并调用核心模块
├── linkvault/                           # 核心 Python 包目录
│   ├── __init__.py                      # 包版本声明与公开 API 导出
│   ├── cli/                             # 命令行子命令实现模块
│   │   ├── __init__.py                  # 子命令注册与路由
│   │   ├── import_cmd.py                # 实现 import 子命令，包含 URL 解析与清洗逻辑
│   │   ├── status_cmd.py                # 实现 status 子命令，输出状态报告与变更摘要
│   │   └── export_cmd.py                # 实现 export 子命令，支持 html/json/rss 格式
│   ├── core/                            # 核心数据模型与索引引擎
│   │   ├── entry.py                     # Entry 类定义，包含 URL、标签、指纹、时间戳等字段
│   │   ├── index.py                     # 索引读写器，负责 JSON 存储的序列化与反序列化
│   │   └── probe.py                     # HTTP 探测模块，封装 curl/urllib 获取内容指纹
│   ├── hooks/                           # 钩子系统实现
│   │   ├── dispatcher.py                # 钩子调度器，按事件类型执行外部脚本
│   │   └── samples/                     # 示例钩子脚本
│   │       └── notify.sh                # 状态变更时发送通知的示例脚本
│   └── utils/                           # 通用工具函数
│       ├── validators.py                # URL 格式校验、协议规范化
│       └── fingerprint.py               # 基于 ETag/Last-Modified 生成内容指纹
├── config/                              # 默认配置文件与模板
│   └── default.yaml                     # 包含存储路径、标签别名、钩子超时等默认设置
├── data/                                # 默认数据存储目录（可配置）
│   ├── entries.json                     # 主索引数据，每行一个 JSON 对象
│   ├── tags.json                        # 标签层级与别名映射
│   └── history/                         # 历史变更记录按月份分片存储
├── reports/                             # 默认报告输出目录
│   └── .gitkeep                         # 占位文件，用于保持目录被 git 追踪
├── docs/                                # 文档源文件
│   ├── guide/                           # 入门与配置指南
│   └── reference/                       # 命令行参考与 API 文档
├── tests/                               # 单元测试与集成测试
│   ├── test_core.py                     # 核心数据模型测试
│   └── test_cli.py                      # 命令行交互测试
├── .gitignore                           # git 忽略规则
├── LICENSE                              # MIT 许可证全文
├── README.md                            # 项目总览与快速入门（本文件）
└── setup.py                             # Python 包安装配置，定义入口点与依赖
```

## 贡献指南

1. 查阅 issue 列表或讨论区中标记为“help wanted”或“good first issue”的任务，确认当前开发优先级，避免与其他贡献者并行处理同一模块。若计划新增较大特性，建议先创建设计说明文档并与维护者沟通方案。

2. 派生项目仓库至个人账户，创建特性分支时采用 `feature/` 前缀，例如 `feature/add-hook-timeout` 或 `fix/import-empty-line`，确保分支命名清晰反映变更内容。

3. 编写或更新代码时，保持与现有代码风格一致。Python 代码遵循 PEP 8 规范，行宽限制为 100 字符；新增命令行参数需同步更新 docs/reference/cli.md 中的对应章节；所有公共函数与类须包含 docstring 说明。

4. 提交代码前运行本地测试套件，确保所有既有测试通过。若新增功能，需在 tests/ 目录下添加对应的测试用例，覆盖正常路径与异常路径。使用 `pytest` 执行全部测试。

5. 发起合并请求时，描述应包含变更动机、实现方式以及手动测试步骤。若变更涉及数据存储格式或配置结构，需提供迁移说明或向后兼容方案。合并请求至少需要一名维护者审阅后方可合并。

## 常见问题

问：LinkVault 是否支持对需要登录或验证的页面进行内容指纹探测？

答：当前版本仅支持基于 HTTP 标准头（如 Content-Length、Last-Modified、ETag）的轻量级探测，不处理 Cookie、Session 或 OAuth 认证。若需探测受限资源，建议使用钩子机制调用外部脚本（如带认证参数的 curl 命令）并自行解析返回数据，再将结果以约定格式写入条目备注字段。

问：导入大量 URL 时，如何避免频繁的 HTTP 探测导致目标服务器压力过大？

答：LinkVault 默认启用并发控制与延迟策略，可通过配置 `probe_parallelism` 参数设置同时探测的最大并发数（默认为 5），并通过 `probe_delay` 参数设置每次探测之间的最小间隔毫秒数。对于大规模导入场景，建议先用 `--no-probe` 选项执行快速导入，随后在低峰时段使用 `update` 子命令分批补充探测数据。

问：索引数据如何备份或迁移到另一台机器？

答：所有索引数据默认以纯文本 JSON 格式存储在 data/ 目录下，用户只需备份整个 data/ 目录即可。迁移时，在新机器上安装 LinkVault 后，将备份的 data/ 目录覆盖到对应路径即可。若需在不同存储后端之间迁移，可使用 `export --format jsonl` 导出全部条目，再使用 `import` 命令导入至目标环境。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:47
