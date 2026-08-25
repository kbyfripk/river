# LinkVault 聚合导航系统

LinkVault 是一个面向技术文档、开发资源与知识库的高效外链聚合与导航系统，专为需要统一管理大量外部内容链接的团队、个人知识库运营者及开源文档维护者设计。该项目不是传统的网址收藏夹，而是一套具备分类索引、批量导入、内容校验与访问统计能力的轻量级链接治理工具。

LinkVault 解决的核心问题在于：当项目或知识库依赖大量外部参考链接、数据源或新闻条目时，链接分散、失效、无标注、无法检索等痛点会显著降低文档的可维护性与可用性。通过提供标准化的链接录入格式、自动化的可用性探测以及结构化的展示模板，LinkVault 帮助用户构建一个可长期稳定运行的链接资源中台。

本系统适用于各类技术博客聚合、开源项目外部依赖索引、行业新闻周报链接库、学术论文参考来源管理以及企业内部知识库的外链治理场景。当前批次为第 27/240 批，共计收录 250 个资源链接，均已完成格式归一化与基础可用性校验。

## 功能概览

批量链接导入：支持通过纯文本列表、CSV 或 JSON 格式一次性导入大量 URL，自动解析并提取域名、路径、扩展名等元信息。

链接可用性探测：对每条导入的链接执行异步 HEAD 请求，自动标记返回码非 200 或超时的条目，并在管理面板中高亮提示。

分类标签系统：允许用户为每个链接添加多个自定义标签，支持按标签筛选、聚合与导出，便于构建主题化的导航页面。

访问统计看板：记录每条链接的被点击次数、最后访问时间及来源页面，提供基于时间维度的热度趋势折线图。

Markdown 模板渲染：内置符合主流开源项目 README 规范的模板引擎，可将链接列表自动生成为结构化的 Markdown 文档，直接用于项目仓库。

链接状态监控与通知：定时任务每日扫描全部链接，当某链接连续三次探测失败时，通过 Webhook 或邮件发送告警通知。

导入去重与合并：自动检测重复 URL，支持保留最新记录或合并标签与访问计数，避免数据冗余。

## 应用场景

技术博客与教程的外部参考管理：技术作者在撰写系列教程时，往往需要引用数十篇外部文章、官方文档或视频地址。LinkVault 可为每篇教程建立一个链接集合，并自动生成附录式的参考列表，确保读者可一键跳转，同时作者能及时发现失效引用。

开源项目 README 的资源区维护：开源项目的 README 常包含"相关项目"、"学习资源"、"社区链接"等区块，手动维护这些链接在长期迭代中极易遗漏或过时。LinkVault 提供专门的项目资源页模板，每批新增或废弃链接均可追溯变更记录，生成标准化的 Markdown 列表。

行业资讯周报的数据源管理：每周发布行业动态的编辑团队需要从数十个固定来源抓取头条新闻。LinkVault 可存储这些来源链接并记录每期的引用频次，配合标签系统区分"官方公告"、"社区讨论"、"技术论文"等类别，大幅提升编辑效率。

企业内部知识库的外链审计：企业维基或 Confluence 中散布的大量外部链接常因供应商变更、文档迁移而失效。LinkVault 可作为独立审计工具，导入知识库导出的全部外链，批量探测并生成失效报告，辅助文档管理员进行清理。

学术论文与预印本索引库：研究人员在整理文献综述时，需跟踪 arXiv、IEEE、PubMed 等平台的大量链接。LinkVault 支持按主题、年份、期刊等维度自定义标签，并可导出为 BibTeX 或 RIS 格式的引用数据，方便插入论文写作工具。

## 快速开始

以下步骤将帮助您在本地环境中快速启动 LinkVault 服务，并导入第一批测试链接。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkvault.git
cd linkvault

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建默认配置
python manage.py init_db
python manage.py load_default_tags

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080

# 另开终端，执行示例批量导入（使用 samples/links_batch_27.txt）
python manage.py import --file samples/links_batch_27.txt --batch 27
```

访问本地 http://localhost:8080 即可进入管理仪表板，默认管理员账号为 admin，密码在首次启动时打印于终端日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 至 3.12 | 核心运行环境，低于 3.9 将无法使用异步语法特性 |
| SQLite | 3.31 及以上 | 内置数据库引擎，用于存储链接元数据、标签和访问日志 |
| requests | 2.28 及以上 | 用于发送 HTTP 探测请求，支持超时与重试策略 |
| aiohttp | 3.8 及以上 | 异步并发探测依赖，可显著提升批量检查效率 |
| markdown | 3.4 及以上 | 用于将链接列表渲染为 Markdown 格式文档 |
| click | 8.1 及以上 | 命令行交互框架，提供子命令解析与参数校验 |
| schedule | 1.2 及以上 | 定时任务调度器，驱动每日链接状态扫描 |
| pytest | 7.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| gunicorn | 20.1 及以上 | 生产环境 WSGI 服务器（部署时推荐使用） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/quickstart.md | 如何在一小时内完成首次安装、导入 100 条链接并生成第一份 README 报告 |
| 管理手册 | docs/administration.md | 如何配置 Webhook 告警、自定义探测超时阈值、调整并发数以及备份数据库 |
| 模板语法 | docs/templating.md | 如何编写自定义 Markdown 模板，控制链接列表的排序、分组与注释显示 |
| API 参考 | docs/api_reference.md | 如何通过 RESTful API 进行链接的增删改查、批量操作及状态批量查询 |
| 故障排查 | docs/troubleshooting.md | 常见部署错误、探测超时原因分析、数据库锁竞争问题及日志定位方法 |
| 性能调优 | docs/performance.md | 当链接数量超过 10 万条时，如何启用 Redis 缓存、分表存储与读写分离 |

## 资源列表

- http://m.3g.fcful.cn/snews/7981.htm
- http://m.3g.fcful.cn/snews/44370.htm
- http://m.3g.fcful.cn/snews/24206.htm
- http://m.3g.fcful.cn/snews/4842.htm
- http://m.3g.fcful.cn/snews/1781364.htm
- http://m.3g.fcful.cn/snews/9081143.htm
- http://m.3g.fcful.cn/snews/3440.htm
- http://m.3g.fcful.cn/snews/87562.htm
- http://m.3g.fcful.cn/snews/339945.htm
- http://m.3g.fcful.cn/snews/5894.htm
- http://m.3g.fcful.cn/snews/505462.htm
- http://m.3g.fcful.cn/snews/9297257.htm
- http://m.3g.fcful.cn/snews/8766558.htm
- http://m.3g.fcful.cn/snews/759975.htm
- http://m.3g.fcful.cn/snews/702499.htm
- http://m.3g.fcful.cn/snews/0047884.htm
- http://m.3g.fcful.cn/snews/7545783.htm
- http://m.3g.fcful.cn/snews/4150.htm
- http://m.3g.fcful.cn/snews/7973.htm
- http://m.3g.fcful.cn/snews/867074.htm
- http://m.3g.fcful.cn/snews/32632.htm
- http://m.3g.fcful.cn/snews/8384344.htm
- http://m.3g.fcful.cn/snews/1149032.htm
- http://m.3g.fcful.cn/snews/806650.htm
- http://m.3g.fcful.cn/snews/411408.htm
- http://m.3g.fcful.cn/snews/3823.htm
- http://m.3g.fcful.cn/snews/61414.htm
- http://m.3g.fcful.cn/snews/6068.htm
- http://m.3g.fcful.cn/snews/9645834.htm
- http://m.3g.fcful.cn/snews/8653.htm
- http://m.3g.fcful.cn/snews/6019.htm
- http://m.3g.fcful.cn/snews/6121840.htm
- http://m.3g.fcful.cn/snews/3397.htm
- http://m.3g.fcful.cn/snews/22616.htm
- http://m.3g.fcful.cn/snews/0356.htm
- http://m.3g.fcful.cn/snews/45002.htm
- http://m.3g.fcful.cn/snews/96592.htm
- http://m.3g.fcful.cn/snews/86961.htm
- http://m.3g.fcful.cn/snews/31055.htm
- http://m.3g.fcful.cn/snews/4849.htm
- http://m.3g.fcful.cn/snews/8792873.htm
- http://m.3g.fcful.cn/snews/353002.htm
- http://m.3g.fcful.cn/snews/1023399.htm
- http://m.3g.fcful.cn/snews/16951.htm
- http://m.3g.fcful.cn/snews/996097.htm
- http://m.3g.fcful.cn/snews/2902.htm
- http://m.3g.fcful.cn/snews/612570.htm
- http://m.3g.fcful.cn/snews/31446.htm
- http://m.3g.fcful.cn/snews/70369.htm
- http://m.3g.fcful.cn/snews/254093.htm
- http://m.3g.fcful.cn/snews/3755710.htm
- http://m.3g.fcful.cn/snews/72623.htm
- http://m.3g.fcful.cn/snews/0926.htm
- http://m.3g.fcful.cn/snews/716676.htm
- http://m.3g.fcful.cn/snews/13609.htm
- http://m.3g.fcful.cn/snews/5956.htm
- http://m.3g.fcful.cn/snews/31100.htm
- http://m.3g.fcful.cn/snews/00405.htm
- http://m.3g.fcful.cn/snews/5722624.htm
- http://m.3g.fcful.cn/snews/31404.htm
- http://m.3g.fcful.cn/snews/741866.htm
- http://m.3g.fcful.cn/snews/5268573.htm
- http://m.3g.fcful.cn/snews/1201.htm
- http://m.3g.fcful.cn/snews/94593.htm
- http://m.3g.fcful.cn/snews/8592.htm
- http://m.3g.fcful.cn/snews/0861.htm
- http://m.3g.fcful.cn/snews/3958488.htm
- http://m.3g.fcful.cn/snews/598234.htm
- http://m.3g.fcful.cn/snews/059745.htm
- http://m.3g.fcful.cn/snews/2528.htm
- http://m.3g.fcful.cn/snews/4429.htm
- http://m.3g.fcful.cn/snews/93509.htm
- http://m.3g.fcful.cn/snews/5797692.htm
- http://m.3g.fcful.cn/snews/23067.htm
- http://m.3g.fcful.cn/snews/60649.htm
- http://m.3g.fcful.cn/snews/64161.htm
- http://m.3g.fcful.cn/snews/760754.htm
- http://m.3g.fcful.cn/snews/023573.htm
- http://m.3g.fcful.cn/snews/1168.htm
- http://m.3g.fcful.cn/snews/1425603.htm
- http://m.3g.fcful.cn/snews/48201.htm
- http://m.3g.fcful.cn/snews/849559.htm
- http://m.3g.fcful.cn/snews/831079.htm
- http://m.3g.fcful.cn/snews/1165433.htm
- http://m.3g.fcful.cn/snews/0330335.htm
- http://m.3g.fcful.cn/snews/29222.htm
- http://m.3g.fcful.cn/snews/723805.htm
- http://m.3g.fcful.cn/snews/46723.htm
- http://m.3g.fcful.cn/snews/766301.htm
- http://m.3g.fcful.cn/snews/752816.htm
- http://m.3g.fcful.cn/snews/0461848.htm
- http://m.3g.fcful.cn/snews/7626.htm
- http://m.3g.fcful.cn/snews/7197.htm
- http://m.3g.fcful.cn/snews/98301.htm
- http://m.3g.fcful.cn/snews/717135.htm
- http://m.3g.fcful.cn/snews/6522788.htm
- http://m.3g.fcful.cn/snews/38289.htm
- http://m.3g.fcful.cn/snews/43499.htm
- http://m.3g.fcful.cn/snews/46829.htm
- http://m.3g.fcful.cn/snews/5114.htm
- http://m.3g.fcful.cn/snews/3616579.htm
- http://m.3g.fcful.cn/snews/6875.htm
- http://m.3g.fcful.cn/snews/53427.htm
- http://m.3g.fcful.cn/snews/5424244.htm
- http://m.3g.fcful.cn/snews/406732.htm
- http://m.3g.fcful.cn/snews/143675.htm
- http://m.3g.fcful.cn/snews/4150488.htm
- http://m.3g.fcful.cn/snews/05332.htm
- http://m.3g.fcful.cn/snews/310773.htm
- http://m.3g.fcful.cn/snews/1159.htm
- http://m.3g.fcful.cn/snews/215798.htm
- http://m.3g.fcful.cn/snews/8442358.htm
- http://m.3g.fcful.cn/snews/0721888.htm
- http://m.3g.fcful.cn/snews/500664.htm
- http://m.3g.fcful.cn/snews/3621944.htm
- http://m.3g.fcful.cn/snews/274118.htm
- http://m.3g.fcful.cn/snews/7394256.htm
- http://m.3g.fcful.cn/snews/75913.htm
- http://m.3g.fcful.cn/snews/89342.htm
- http://m.3g.fcful.cn/snews/4446.htm
- http://m.3g.fcful.cn/snews/29162.htm
- http://m.3g.fcful.cn/snews/4100.htm
- http://m.3g.fcful.cn/snews/3128572.htm
- http://m.3g.fcful.cn/snews/1609241.htm
- http://m.3g.fcful.cn/snews/25091.htm
- http://m.3g.fcful.cn/snews/4613004.htm
- http://m.3g.fcful.cn/snews/5366240.htm
- http://m.3g.fcful.cn/snews/0241.htm
- http://m.3g.fcful.cn/snews/282518.htm
- http://m.3g.fcful.cn/snews/0761157.htm
- http://m.3g.fcful.cn/snews/7940.htm
- http://m.3g.fcful.cn/snews/466534.htm
- http://m.3g.fcful.cn/snews/6245829.htm
- http://m.3g.fcful.cn/snews/383220.htm
- http://m.3g.fcful.cn/snews/2890.htm
- http://m.3g.fcful.cn/snews/642596.htm
- http://m.3g.fcful.cn/snews/4113.htm
- http://m.3g.fcful.cn/snews/80881.htm
- http://m.3g.fcful.cn/snews/549805.htm
- http://m.3g.fcful.cn/snews/1437188.htm
- http://m.3g.fcful.cn/snews/6861.htm
- http://m.3g.fcful.cn/snews/5844672.htm
- http://m.3g.fcful.cn/snews/0199.htm
- http://m.3g.fcful.cn/snews/6013446.htm
- http://m.3g.fcful.cn/snews/5471.htm
- http://m.3g.fcful.cn/snews/06956.htm
- http://m.3g.fcful.cn/snews/159355.htm
- http://m.3g.fcful.cn/snews/96478.htm
- http://m.3g.fcful.cn/snews/170574.htm
- http://m.3g.fcful.cn/snews/252101.htm
- http://m.3g.fcful.cn/snews/1599.htm
- http://m.3g.fcful.cn/snews/13247.htm
- http://m.3g.fcful.cn/snews/6537552.htm
- http://m.3g.fcful.cn/snews/1821.htm
- http://m.3g.fcful.cn/snews/503800.htm
- http://m.3g.fcful.cn/snews/46380.htm
- http://m.3g.fcful.cn/snews/02968.htm
- http://m.3g.fcful.cn/snews/816681.htm
- http://m.3g.fcful.cn/snews/38404.htm
- http://m.3g.fcful.cn/snews/6358678.htm
- http://m.3g.fcful.cn/snews/1743208.htm
- http://m.3g.fcful.cn/snews/2128.htm
- http://m.3g.fcful.cn/snews/18375.htm
- http://m.3g.fcful.cn/snews/889550.htm
- http://m.3g.fcful.cn/snews/4855.htm
- http://m.3g.fcful.cn/snews/17496.htm
- http://m.3g.fcful.cn/snews/8152666.htm
- http://m.3g.fcful.cn/snews/9414010.htm
- http://m.3g.fcful.cn/snews/3888816.htm
- http://m.3g.fcful.cn/snews/131374.htm
- http://m.3g.fcful.cn/snews/21923.htm
- http://m.3g.fcful.cn/snews/361976.htm
- http://m.3g.fcful.cn/snews/0961714.htm
- http://m.3g.fcful.cn/snews/3678486.htm
- http://m.3g.fcful.cn/snews/5380707.htm
- http://m.3g.fcful.cn/snews/1417.htm
- http://m.3g.fcful.cn/snews/3509.htm
- http://m.3g.fcful.cn/snews/5432.htm
- http://m.3g.fcful.cn/snews/53757.htm
- http://m.3g.fcful.cn/snews/8975.htm
- http://m.3g.fcful.cn/snews/83078.htm
- http://m.3g.fcful.cn/snews/2670501.htm
- http://m.3g.fcful.cn/snews/0745.htm
- http://m.3g.fcful.cn/snews/9349034.htm
- http://m.3g.fcful.cn/snews/16870.htm
- http://m.3g.fcful.cn/snews/752640.htm
- http://m.3g.fcful.cn/snews/3761587.htm
- http://m.3g.fcful.cn/snews/5067.htm
- http://m.3g.fcful.cn/snews/4802759.htm
- http://m.3g.fcful.cn/snews/2068263.htm
- http://m.3g.fcful.cn/snews/21259.htm
- http://m.3g.fcful.cn/snews/297074.htm
- http://m.3g.fcful.cn/snews/9330940.htm
- http://m.3g.fcful.cn/snews/300928.htm
- http://m.3g.fcful.cn/snews/7836084.htm
- http://m.3g.fcful.cn/snews/99909.htm
- http://m.3g.fcful.cn/snews/07279.htm
- http://m.3g.fcful.cn/snews/6782945.htm
- http://m.3g.fcful.cn/snews/81436.htm
- http://m.3g.fcful.cn/snews/36423.htm
- http://m.3g.fcful.cn/snews/6568554.htm
- http://m.3g.fcful.cn/snews/824097.htm
- http://m.3g.fcful.cn/snews/8404.htm
- http://m.3g.fcful.cn/snews/75270.htm
- http://m.3g.fcful.cn/snews/320152.htm
- http://m.3g.fcful.cn/snews/22787.htm
- http://m.3g.fcful.cn/snews/7308625.htm
- http://m.3g.fcful.cn/snews/2183261.htm
- http://m.3g.fcful.cn/snews/610909.htm
- http://m.3g.fcful.cn/snews/190206.htm
- http://m.3g.fcful.cn/snews/132719.htm
- http://m.3g.fcful.cn/snews/8873.htm
- http://m.3g.fcful.cn/snews/061502.htm
- http://m.3g.fcful.cn/snews/490333.htm
- http://m.3g.fcful.cn/snews/6504832.htm
- http://m.3g.fcful.cn/snews/533343.htm
- http://m.3g.fcful.cn/snews/8407.htm
- http://m.3g.fcful.cn/snews/904016.htm
- http://m.3g.fcful.cn/snews/231114.htm
- http://m.3g.fcful.cn/snews/84333.htm
- http://m.3g.fcful.cn/snews/56508.htm
- http://m.3g.fcful.cn/snews/1432.htm
- http://m.3g.fcful.cn/snews/92329.htm
- http://m.3g.fcful.cn/snews/89510.htm
- http://m.3g.fcful.cn/snews/265552.htm
- http://m.3g.fcful.cn/snews/64217.htm
- http://m.3g.fcful.cn/snews/8196.htm
- http://m.3g.fcful.cn/snews/0074.htm
- http://m.3g.fcful.cn/snews/8706562.htm
- http://m.3g.fcful.cn/snews/850410.htm
- http://m.3g.fcful.cn/snews/4214912.htm
- http://m.3g.fcful.cn/snews/4669497.htm
- http://m.3g.fcful.cn/snews/7172954.htm
- http://m.3g.fcful.cn/snews/0215080.htm
- http://m.3g.fcful.cn/snews/545428.htm
- http://m.3g.fcful.cn/snews/0212.htm
- http://m.3g.fcful.cn/snews/9769.htm
- http://m.3g.fcful.cn/snews/09898.htm
- http://m.3g.fcful.cn/snews/460189.htm
- http://m.3g.fcful.cn/snews/5042995.htm
- http://m.3g.fcful.cn/snews/7151.htm
- http://m.3g.fcful.cn/snews/218633.htm
- http://m.3g.fcful.cn/snews/0989.htm
- http://m.3g.fcful.cn/snews/828628.htm
- http://m.3g.fcful.cn/snews/45275.htm
- http://m.3g.fcful.cn/snews/1830.htm
- http://m.3g.fcful.cn/snews/66624.htm
- http://m.3g.fcful.cn/snews/3789603.htm
- http://m.3g.fcful.cn/snews/3278528.htm
- http://m.3g.fcful.cn/snews/5903.htm

## 项目结构

```
linkvault/
├── manage.py                    # 统一命令行入口，集成所有子命令
├── requirements.txt             # 生产环境核心依赖锁定文件
├── config/
│   ├── default.yaml             # 默认配置项：端口、探测超时、并发数、日志级别
│   └── logging.conf             # 日志滚动策略与格式定义
├── core/
│   ├── __init__.py
│   ├── models.py                # SQLAlchemy ORM 模型：Link, Tag, AccessLog, Batch
│   ├── schema.py                # Pydantic 校验模型，用于 API 输入输出
│   ├── detector.py              # 异步链接探测引擎，含重试与退避策略
│   └── importer.py              # 批量导入解析器，支持 txt / csv / json
├── web/
│   ├── __init__.py
│   ├── app.py                   # Flask 应用工厂与路由注册
│   ├── dashboard.py             # 仪表板视图：统计卡片、趋势图、最近失效列表
│   ├── api_v1.py                # RESTful API：/api/v1/links 增删改查与批量操作
│   └── templates/               # Jinja2 模板：管理界面与报告预览
├── render/
│   ├── __init__.py
│   ├── markdown.py              # Markdown 模板引擎，支持自定义占位符
│   ├── themes/                  # 预置模板主题：default, minimal, academic
│   └── filters.py               # 自定义过滤器：排序、分组、截断、标签聚合
├── monitor/
│   ├── __init__.py
│   ├── scheduler.py             # 基于 schedule 库的每日扫描任务
│   ├── notifier.py              # Webhook / SMTP 告警发送模块
│   └── health.py                # 健康检查端点与系统状态收集
├── tests/
│   ├── unit/                    # 单元测试：模型、探测、导入器
│   ├── integration/             # 集成测试：API 端到端、数据库迁移
│   └── fixtures/                # 测试样本数据：sample_links.csv
├── docs/                        # 完整文档目录，参见上文"文档导航"章节
├── samples/                     # 示例导入文件，包含每批链接的原始列表
└── scripts/
    ├── init_db.py               # 数据库初始化与迁移脚本
    └── deploy_prod.sh           # 生产环境部署脚本（gunicorn + systemd）
```

## 贡献指南

我们欢迎并鼓励社区开发者以多种方式参与 LinkVault 项目，无论是代码贡献、文档完善还是问题反馈，都将帮助项目持续演进。

提交 Issue 报告缺陷或功能请求：请在 GitHub Issues 页面使用提供的模板详细描述问题，包括运行环境、复现步骤、预期行为与实际结果。功能请求请说明应用场景与收益。

Fork 仓库并创建特性分支：从主分支 checkout 新分支，命名遵循 feature/xxx 或 fix/xxx 格式。确保代码通过全部单元测试与集成测试，新功能需附带对应的测试用例。

编写或更新文档：文档位于 docs/ 目录，使用 Markdown 格式。若修改 API 行为，请同步更新 api_reference.md 中的请求响应示例。若新增配置项，请在 default.yaml 和 administration.md 中补充说明。

提交 Pull Request 前进行自我审查：确保无调试代码、无敏感信息泄漏，提交信息遵循 Conventional Commits 规范（feat / fix / docs / refactor / test / chore）。PR 描述中链接对应的 Issue 编号。

参与讨论与代码审查：活跃的社区成员可受邀加入核心贡献者团队，参与 PR 评审、路线图规划与版本发布决策。我们每月举办一次线上同步会议，具体时间在 Discord 频道公告。

## 常见问题

Q：导入大量链接时出现超时或内存溢出，应如何优化？

A：当单次导入超过 5000 条链接时，建议使用 --chunk-size 参数分批提交，默认值为 1000。您还可以在 config/default.yaml 中调整 async_batch_size 控制并发探测数，以及 sqlite_cache_size 提升数据库写入性能。若仍遇到瓶颈，可考虑切换至 PostgreSQL 生产环境。

Q：如何从旧版 LinkVault 迁移数据到新版？

A：我们提供了迁移脚本 scripts/migrate_v1_to_v2.py，支持从旧版 SQLite 数据库导出链接、标签和访问日志，并自动转换时间戳格式与标签关联关系。执行前请备份原数据库文件，迁移完成后运行 python manage.py verify_integrity 校验数据一致性。

Q：部署到生产环境后，如何配置 HTTPS 和域名反向代理？

A：推荐使用 Nginx 作为前端反向代理，将 SSL 终止层置于 Nginx，再转发 HTTP 请求至 Gunicorn 监听的本地 Unix Socket。我们提供了示例 Nginx 配置文件 docs/deployment/nginx.conf，包含 HTTP 自动跳转 HTTPS、静态资源缓存、以及 /health 端点的免认证访问规则。请确保环境变量中设置 FORCE_HTTPS=true 以启用安全 Cookie 标记。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
