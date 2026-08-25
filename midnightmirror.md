# WebLink Hub

WebLink Hub 是一个面向技术内容聚合与外部链接治理的开源工具集，旨在为开发者、技术博主及内容运营团队提供一套标准化的外链采集、归档、健康检查与展示方案。本项目不依赖特定 CMS 或前端框架，以纯数据管道方式处理海量外链资源，适用于中大规模技术资源站点的日常维护与重构场景。

项目定位于“技术外链的资产管理层”，解决技术博客、导航站、文档中心中常见的外链失效、协议不一致、重复收录、来源不可追溯等问题。通过提供统一的 URL 归一化、批量校验、元数据抓取与状态监控能力，帮助用户将散落在各页面中的原始链接转化为可查询、可分析、可更新的结构化数据集。

## 功能概览

- **批量链接归一化**：自动处理 URL 中协议缺失、大小写混用、末尾斜杠、WWW 前缀不一致等问题，输出统一格式的规范链接。

- **多源采集与去重**：支持从 RSS 订阅源、站点地图、HTML 页面、纯文本列表等多种渠道采集外链，基于内容指纹与 URL 结构进行智能去重。

- **健康状态轮询**：内置异步 HTTP 探测引擎，可配置超时与重试策略，定期检查各链接的可达性、响应码及页面标题变更。

- **元数据增强**：对有效链接自动抓取页面标题、描述、关键词、最后修改时间，并提取顶级域名与路径层级，便于分类统计。

- **标签化分类管理**：支持对链接打上技术领域、来源站点、内容类型等多维度标签，并提供标签组合筛选与导出功能。

- **快照与变更追踪**：记录每次检测的响应状态与元数据，生成链接变更日志，支持回溯任意时间点的资源状态。

- **结构化数据导出**：内置 CSV、JSON、Markdown 表格三种导出格式，可直接嵌入技术文档或数据看板。

- **RESTful API 接口**：提供完整的只读与写入 API，方便与现有运维系统、CI/CD 流水线或静态站点生成器集成。

## 应用场景

**技术博客外链审计**：独立技术博主或团队博客在年度内容审查时，可使用本工具批量扫描所有历史文章中的外部链接，快速发现已失效或内容被篡改的资源，并生成替换建议列表。

**开发者导航站数据维护**：运营技术导航站或开源工具列表的开发者，通过本工具每日定时检测收录链接的可用性，自动标记响应超时或返回 4xx/5xx 状态码的条目，辅助管理员及时下架或更新。

**文档中心资源迁移**：企业文档团队在合并多个知识库或更换域名时，利用本工具的批量归一化与重写规则功能，将旧文档中全部外链按映射表一次性转换为新地址，避免链接断裂。

**开源项目 README 外链复核**：开源项目维护者在发布新版本前，使用本工具检查 README、贡献指南、文档目录中的所有引用链接，确保用户文档中的每一处跳转均有效且指向预期内容。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/weblink-hub/weblink-hub.git

# 进入项目目录
cd weblink-hub

# 安装 Python 依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 使用示例数据运行采集与检测流程
python run_pipeline.py --source ./samples/links.txt --output ./reports/ --check
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，类型注解与异步特性依赖 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发探测链接健康状态 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 元数据解析，提取页面标题与描述 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 bs4 后端 |
| pandas | 2.0.0 及以上 | 数据表格处理，支持去重、筛选与导出 |
| pyyaml | 6.0.0 及以上 | 配置文件解析，支持用户自定义归一化规则 |
| click | 8.1.0 及以上 | 命令行交互框架，提供子命令与参数解析 |
| pytest | 7.0.0 及以上 | 单元测试框架，用于开发阶段功能验证 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user_guide.md | 如何安装、配置、运行采集与检测任务；如何解读输出报告 |
| API 参考 | /docs/api_reference.md | 每个 RESTful 接口的请求方法、参数、响应格式及错误码 |
| 配置说明 | /docs/configuration.md | 配置文件中的超时时间、重试策略、归一化规则、标签体系如何调整 |
| 架构设计 | /docs/architecture.md | 数据管道各阶段（采集、清洗、检测、增强、导出）的设计思路与扩展点 |

## 资源列表

- http://m.blog.fcful.cn/bnews/592070.htm
- http://m.blog.fcful.cn/bnews/9730.htm
- http://m.blog.fcful.cn/bnews/0500.htm
- http://m.blog.fcful.cn/bnews/3422060.htm
- http://m.blog.fcful.cn/bnews/3098749.htm
- http://m.blog.fcful.cn/bnews/9023799.htm
- http://m.blog.fcful.cn/bnews/6035.htm
- http://m.blog.fcful.cn/bnews/491911.htm
- http://m.blog.fcful.cn/bnews/71865.htm
- http://m.blog.fcful.cn/bnews/9879.htm
- http://m.blog.fcful.cn/bnews/9349.htm
- http://m.blog.fcful.cn/bnews/829535.htm
- http://m.blog.fcful.cn/bnews/464031.htm
- http://m.blog.fcful.cn/bnews/0968771.htm
- http://m.blog.fcful.cn/bnews/5547.htm
- http://m.blog.fcful.cn/bnews/7818399.htm
- http://m.blog.fcful.cn/bnews/38607.htm
- http://m.blog.fcful.cn/bnews/81112.htm
- http://m.blog.fcful.cn/bnews/8145141.htm
- http://m.blog.fcful.cn/bnews/286635.htm
- http://m.blog.fcful.cn/bnews/1604982.htm
- http://m.blog.fcful.cn/bnews/467515.htm
- http://m.blog.fcful.cn/bnews/78332.htm
- http://m.blog.fcful.cn/bnews/59562.htm
- http://m.blog.fcful.cn/bnews/1213174.htm
- http://m.blog.fcful.cn/bnews/229584.htm
- http://m.blog.fcful.cn/bnews/3645.htm
- http://m.blog.fcful.cn/bnews/67113.htm
- http://m.blog.fcful.cn/bnews/2782.htm
- http://m.blog.fcful.cn/bnews/5501.htm
- http://m.blog.fcful.cn/bnews/5094661.htm
- http://m.blog.fcful.cn/bnews/729069.htm
- http://m.blog.fcful.cn/bnews/5859.htm
- http://m.blog.fcful.cn/bnews/0106130.htm
- http://m.blog.fcful.cn/bnews/257220.htm
- http://m.blog.fcful.cn/bnews/9719774.htm
- http://m.blog.fcful.cn/bnews/034173.htm
- http://m.blog.fcful.cn/bnews/64082.htm
- http://m.blog.fcful.cn/bnews/07582.htm
- http://m.blog.fcful.cn/bnews/03927.htm
- http://m.blog.fcful.cn/bnews/12909.htm
- http://m.blog.fcful.cn/bnews/93810.htm
- http://m.blog.fcful.cn/bnews/5755.htm
- http://m.blog.fcful.cn/bnews/27159.htm
- http://m.blog.fcful.cn/bnews/33182.htm
- http://m.blog.fcful.cn/bnews/8475.htm
- http://m.blog.fcful.cn/bnews/67797.htm
- http://m.blog.fcful.cn/bnews/93015.htm
- http://m.blog.fcful.cn/bnews/948284.htm
- http://m.blog.fcful.cn/bnews/244530.htm
- http://m.blog.fcful.cn/bnews/4820654.htm
- http://m.blog.fcful.cn/bnews/8927.htm
- http://m.blog.fcful.cn/bnews/9737.htm
- http://m.blog.fcful.cn/bnews/1242.htm
- http://m.blog.fcful.cn/bnews/899618.htm
- http://m.blog.fcful.cn/bnews/9809014.htm
- http://m.blog.fcful.cn/bnews/3909071.htm
- http://m.blog.fcful.cn/bnews/075977.htm
- http://m.blog.fcful.cn/bnews/446672.htm
- http://m.blog.fcful.cn/bnews/35721.htm
- http://m.blog.fcful.cn/bnews/13572.htm
- http://m.blog.fcful.cn/bnews/51221.htm
- http://m.blog.fcful.cn/bnews/5581.htm
- http://m.blog.fcful.cn/bnews/4613877.htm
- http://m.blog.fcful.cn/bnews/9403502.htm
- http://m.blog.fcful.cn/bnews/14814.htm
- http://m.blog.fcful.cn/bnews/3314252.htm
- http://m.blog.fcful.cn/bnews/7794.htm
- http://m.blog.fcful.cn/bnews/92064.htm
- http://m.blog.fcful.cn/bnews/8265004.htm
- http://m.blog.fcful.cn/bnews/2121590.htm
- http://m.blog.fcful.cn/bnews/956765.htm
- http://m.blog.fcful.cn/bnews/7324.htm
- http://m.blog.fcful.cn/bnews/7565.htm
- http://m.blog.fcful.cn/bnews/59210.htm
- http://m.blog.fcful.cn/bnews/6065.htm
- http://m.blog.fcful.cn/bnews/82491.htm
- http://m.blog.fcful.cn/bnews/82701.htm
- http://m.blog.fcful.cn/bnews/680856.htm
- http://m.blog.fcful.cn/bnews/4108.htm
- http://m.blog.fcful.cn/bnews/62289.htm
- http://m.blog.fcful.cn/bnews/852451.htm
- http://m.blog.fcful.cn/bnews/10838.htm
- http://m.blog.fcful.cn/bnews/939367.htm
- http://m.blog.fcful.cn/bnews/9558.htm
- http://m.blog.fcful.cn/bnews/1208.htm
- http://m.blog.fcful.cn/bnews/4594671.htm
- http://m.blog.fcful.cn/bnews/444085.htm
- http://m.blog.fcful.cn/bnews/7271.htm
- http://m.blog.fcful.cn/bnews/9755.htm
- http://m.blog.fcful.cn/bnews/0436709.htm
- http://m.blog.fcful.cn/bnews/983049.htm
- http://m.blog.fcful.cn/bnews/1788322.htm
- http://m.blog.fcful.cn/bnews/70280.htm
- http://m.blog.fcful.cn/bnews/46378.htm
- http://m.blog.fcful.cn/bnews/7386701.htm
- http://m.blog.fcful.cn/bnews/091317.htm
- http://m.blog.fcful.cn/bnews/9150.htm
- http://m.blog.fcful.cn/bnews/323000.htm
- http://m.blog.fcful.cn/bnews/16186.htm
- http://m.blog.fcful.cn/bnews/6723.htm
- http://m.blog.fcful.cn/bnews/894294.htm
- http://m.blog.fcful.cn/bnews/98988.htm
- http://m.blog.fcful.cn/bnews/59442.htm
- http://m.blog.fcful.cn/bnews/7706276.htm
- http://m.blog.fcful.cn/bnews/78477.htm
- http://m.blog.fcful.cn/bnews/2107.htm
- http://m.blog.fcful.cn/bnews/3702.htm
- http://m.blog.fcful.cn/bnews/6952323.htm
- http://m.blog.fcful.cn/bnews/246286.htm
- http://m.blog.fcful.cn/bnews/7948223.htm
- http://m.blog.fcful.cn/bnews/3101705.htm
- http://m.blog.fcful.cn/bnews/6531278.htm
- http://m.blog.fcful.cn/bnews/7744977.htm
- http://m.blog.fcful.cn/bnews/7255668.htm
- http://m.blog.fcful.cn/bnews/11548.htm
- http://m.blog.fcful.cn/bnews/94303.htm
- http://m.blog.fcful.cn/bnews/2263.htm
- http://m.blog.fcful.cn/bnews/780399.htm
- http://m.blog.fcful.cn/bnews/946756.htm
- http://m.blog.fcful.cn/bnews/8098725.htm
- http://m.blog.fcful.cn/bnews/9037355.htm
- http://m.blog.fcful.cn/bnews/6797142.htm
- http://m.blog.fcful.cn/bnews/0231985.htm
- http://m.blog.fcful.cn/bnews/75018.htm
- http://m.blog.fcful.cn/bnews/890336.htm
- http://m.blog.fcful.cn/bnews/31222.htm
- http://m.blog.fcful.cn/bnews/7467578.htm
- http://m.blog.fcful.cn/bnews/2789566.htm
- http://m.blog.fcful.cn/bnews/2894389.htm
- http://m.blog.fcful.cn/bnews/39683.htm
- http://m.blog.fcful.cn/bnews/8502.htm
- http://m.blog.fcful.cn/bnews/60982.htm
- http://m.blog.fcful.cn/bnews/0016.htm
- http://m.blog.fcful.cn/bnews/53700.htm
- http://m.blog.fcful.cn/bnews/169557.htm
- http://m.blog.fcful.cn/bnews/30094.htm
- http://m.blog.fcful.cn/bnews/7384888.htm
- http://m.blog.fcful.cn/bnews/630581.htm
- http://m.blog.fcful.cn/bnews/098410.htm
- http://m.blog.fcful.cn/bnews/12164.htm
- http://m.blog.fcful.cn/bnews/42875.htm
- http://m.blog.fcful.cn/bnews/8966424.htm
- http://m.blog.fcful.cn/bnews/340473.htm
- http://m.blog.fcful.cn/bnews/920648.htm
- http://m.blog.fcful.cn/bnews/0917.htm
- http://m.blog.fcful.cn/bnews/48776.htm
- http://m.blog.fcful.cn/bnews/2267.htm
- http://m.blog.fcful.cn/bnews/314483.htm
- http://m.blog.fcful.cn/bnews/27046.htm
- http://m.blog.fcful.cn/bnews/631628.htm
- http://m.blog.fcful.cn/bnews/995555.htm
- http://m.blog.fcful.cn/bnews/66853.htm
- http://m.blog.fcful.cn/bnews/051832.htm
- http://m.blog.fcful.cn/bnews/254827.htm
- http://m.blog.fcful.cn/bnews/08263.htm
- http://m.blog.fcful.cn/bnews/232739.htm
- http://m.blog.fcful.cn/bnews/3638168.htm
- http://m.blog.fcful.cn/bnews/4103.htm
- http://m.blog.fcful.cn/bnews/9757723.htm
- http://m.blog.fcful.cn/bnews/05210.htm
- http://m.blog.fcful.cn/bnews/973122.htm
- http://m.blog.fcful.cn/bnews/69387.htm
- http://m.blog.fcful.cn/bnews/9173531.htm
- http://m.blog.fcful.cn/bnews/636902.htm
- http://m.blog.fcful.cn/bnews/02636.htm
- http://m.blog.fcful.cn/bnews/9093447.htm
- http://m.blog.fcful.cn/bnews/167471.htm
- http://m.blog.fcful.cn/bnews/56763.htm
- http://m.blog.fcful.cn/bnews/87136.htm
- http://m.blog.fcful.cn/bnews/4885.htm
- http://m.blog.fcful.cn/bnews/691748.htm
- http://m.blog.fcful.cn/bnews/4548.htm
- http://m.blog.fcful.cn/bnews/46962.htm
- http://m.blog.fcful.cn/bnews/3538.htm
- http://m.blog.fcful.cn/bnews/19662.htm
- http://m.blog.fcful.cn/bnews/2417.htm
- http://m.blog.fcful.cn/bnews/627898.htm
- http://m.blog.fcful.cn/bnews/34590.htm
- http://m.blog.fcful.cn/bnews/9094773.htm
- http://m.blog.fcful.cn/bnews/7841.htm
- http://m.blog.fcful.cn/bnews/23033.htm
- http://m.blog.fcful.cn/bnews/7895709.htm
- http://m.blog.fcful.cn/bnews/83424.htm
- http://m.blog.fcful.cn/bnews/8510.htm
- http://m.blog.fcful.cn/bnews/5321366.htm
- http://m.blog.fcful.cn/bnews/902332.htm
- http://m.blog.fcful.cn/bnews/19048.htm
- http://m.blog.fcful.cn/bnews/404222.htm
- http://m.blog.fcful.cn/bnews/0109105.htm
- http://m.blog.fcful.cn/bnews/9146871.htm
- http://m.blog.fcful.cn/bnews/2120.htm
- http://m.blog.fcful.cn/bnews/935212.htm
- http://m.blog.fcful.cn/bnews/1253.htm
- http://m.blog.fcful.cn/bnews/4831271.htm
- http://m.blog.fcful.cn/bnews/0336.htm
- http://m.blog.fcful.cn/bnews/0915.htm
- http://m.blog.fcful.cn/bnews/6858647.htm
- http://m.blog.fcful.cn/bnews/3952.htm
- http://m.blog.fcful.cn/bnews/3260538.htm
- http://m.blog.fcful.cn/bnews/896712.htm
- http://m.blog.fcful.cn/bnews/9116211.htm
- http://m.blog.fcful.cn/bnews/3345407.htm
- http://m.blog.fcful.cn/bnews/25174.htm
- http://m.blog.fcful.cn/bnews/331368.htm
- http://m.blog.fcful.cn/bnews/974866.htm
- http://m.blog.fcful.cn/bnews/1725.htm
- http://m.blog.fcful.cn/bnews/1727601.htm
- http://m.blog.fcful.cn/bnews/40743.htm
- http://m.blog.fcful.cn/bnews/33050.htm
- http://m.blog.fcful.cn/bnews/1705.htm
- http://m.blog.fcful.cn/bnews/3451.htm
- http://m.blog.fcful.cn/bnews/1850592.htm
- http://m.blog.fcful.cn/bnews/972858.htm
- http://m.blog.fcful.cn/bnews/2177357.htm
- http://m.blog.fcful.cn/bnews/9250972.htm
- http://m.blog.fcful.cn/bnews/039823.htm
- http://m.blog.fcful.cn/bnews/0066013.htm
- http://m.blog.fcful.cn/bnews/8434423.htm
- http://m.blog.fcful.cn/bnews/6373376.htm
- http://m.blog.fcful.cn/bnews/281356.htm
- http://m.blog.fcful.cn/bnews/4557990.htm
- http://m.blog.fcful.cn/bnews/6671771.htm
- http://m.blog.fcful.cn/bnews/53588.htm
- http://m.blog.fcful.cn/bnews/83220.htm
- http://m.blog.fcful.cn/bnews/7877860.htm
- http://m.blog.fcful.cn/bnews/717013.htm
- http://m.blog.fcful.cn/bnews/1134.htm
- http://m.blog.fcful.cn/bnews/2298.htm
- http://m.blog.fcful.cn/bnews/2359.htm
- http://m.blog.fcful.cn/bnews/96590.htm
- http://m.blog.fcful.cn/bnews/2347.htm
- http://m.blog.fcful.cn/bnews/1636.htm
- http://m.blog.fcful.cn/bnews/269121.htm
- http://m.blog.fcful.cn/bnews/1325.htm
- http://m.blog.fcful.cn/bnews/44130.htm
- http://m.blog.fcful.cn/bnews/9323.htm
- http://m.blog.fcful.cn/bnews/925521.htm
- http://m.blog.fcful.cn/bnews/502062.htm
- http://m.blog.fcful.cn/bnews/2056.htm
- http://m.blog.fcful.cn/bnews/6237.htm
- http://m.blog.fcful.cn/bnews/017036.htm
- http://m.blog.fcful.cn/bnews/907650.htm
- http://m.blog.fcful.cn/bnews/9448636.htm
- http://m.blog.fcful.cn/bnews/3696036.htm
- http://m.blog.fcful.cn/bnews/6031843.htm
- http://m.blog.fcful.cn/bnews/5777643.htm
- http://m.blog.fcful.cn/bnews/783030.htm
- http://m.blog.fcful.cn/bnews/71614.htm
- http://m.blog.fcful.cn/bnews/23982.htm

## 项目结构

```
weblink-hub/
├── pipeline/                           # 核心数据管道模块
│   ├── collector/                      # 采集器子模块
│   │   ├── base.py                     # 抽象采集基类，定义统一接口
│   │   ├── rss_reader.py               # RSS 订阅源采集实现
│   │   └── sitemap_parser.py           # 站点地图 XML 解析器
│   ├── cleaner/                        # 清洗与归一化子模块
│   │   ├── normalizer.py               # URL 协议/大小写/斜杠归一化核心逻辑
│   │   └── deduplicator.py             # 基于布隆过滤器的链接去重
│   ├── checker/                        # 健康检测子模块
│   │   ├── probe.py                    # 异步 HTTP 探测引擎，含超时与重试
│   │   └── status_tracker.py           # 状态记录与变更判定
│   └── exporter/                       # 数据导出子模块
│       ├── json_exporter.py            # JSON 格式序列化
│       ├── csv_exporter.py             # CSV 表格导出，含标题行
│       └── markdown_exporter.py        # Markdown 列表与表格生成
├── api/                                # RESTful API 服务层
│   ├── routes/                         # 路由定义
│   │   ├── links.py                    # /links 资源端点
│   │   └── tasks.py                    # /tasks 异步任务端点
│   └── middleware/                     # 中间件
│       └── cors.py                     # 跨域资源共享配置
├── config/                             # 配置管理
│   ├── default.yaml                    # 默认参数（超时 10s、重试 2 次、并发 50）
│   └── schema.py                       # 配置结构校验 Pydantic 模型
├── samples/                            # 示例数据与测试用例
│   ├── links.txt                       # 纯文本外链示例
│   └── expected_output.json            # 期望输出基准
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 各模块独立测试
│   └── integration/                    # 端到端管道测试
├── docs/                               # 文档目录
│   ├── user_guide.md                   # 用户手册
│   ├── api_reference.md                # API 详细参考
│   ├── configuration.md                # 配置参数说明
│   └── architecture.md                 # 架构设计文档
├── run_pipeline.py                     # 命令行主入口
├── requirements.txt                    # 生产依赖清单
├── setup.py                            # 项目安装脚本
└── README.md                           # 本文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账号，并克隆到本地开发环境。建议使用 Python 3.10 及以上版本并创建独立虚拟环境。

2. 在本地运行完整测试套件 `pytest tests/` 确保现有功能通过。新增功能或修复问题前，请在相应测试文件中补充覆盖用例。

3. 提交代码前执行代码格式化工具 `black .` 与 `isort .` 保持代码风格一致，并使用 `mypy` 进行静态类型检查。

4. 提交 pull request 时，请清晰描述变更动机、实现方式及测试结果，并关联相关 issue 编号。PR 标题使用 `feat:` `fix:` `docs:` `refactor:` 等前缀。

5. 文档更新同步进行。若新增配置项或 API 接口，需同步修改 `/docs` 目录下对应文档，并确保示例代码可运行。

## 常见问题

**Q：如何批量导入历史外链数据？**

A：本工具支持从纯文本列表（每行一条 URL）、CSV 文件（需包含 url 列）以及站点地图 XML 三种导入方式。使用 `run_pipeline.py --source` 参数指定文件路径即可。若数据量超过 1 万条，建议启用 `--batch` 分批处理模式，避免内存溢出。

**Q：检测时出现大量连接超时，如何处理？**

A：超时通常由目标服务器响应慢或网络环境不稳定引起。可在配置文件 `default.yaml` 中调整 `timeout` 参数（单位秒）和 `retry_times` 参数。同时，检查 `max_concurrency` 是否过大导致目标服务器限流，建议从 20 开始逐步上调。

**Q：输出的归一化链接与原始链接不一致，是否影响原始数据？**

A：归一化只作用于内部处理与导出结果，原始数据始终保存在 `raw_url` 字段中供追溯。归一化规则包括：补充缺失的协议头、移除默认端口号、统一域名为小写、去除多余斜杠和片段标识。若您对特定域有特殊归一化要求，可在配置文件的 `custom_rules` 段添加正则替换。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
