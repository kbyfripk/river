# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的结构化外链资源归集与导航系统。该项目针对当前网络中技术资料分散、优质外链缺乏统一索引、历史快照难以追溯等问题，提供了一套基于静态站点生成逻辑的链接管理方案。项目本身不生产内容，而是通过人工筛选与自动化校验相结合的方式，将分散于各处的高价值信息节点进行主题化归档，从而降低信息检索的边际成本。

目标用户包括开源社区维护者、技术文档撰写人、网络安全分析员以及各类需要高频查阅外部参考资料的研究人员。WebLink Navigator 通过严格的 URL 存活检测、元数据提取和分类标签体系，帮助用户从海量信息中快速定位目标资源，同时为团队内部知识库的构建提供标准化的外链输入格式。

## 功能概览

链接存活周期监控 系统每日定时检测入库链接的可访问状态，并自动标记异常条目，确保资源列表的实时有效性。

元数据智能抽取 对每个入库 URL 自动抓取页面标题、关键词、发布时间及内容摘要，生成标准化的资源描述卡片。

多维度标签分类 支持按技术领域、文件类型、来源站点、时间范围等维度对链接进行标记与筛选，便于构建个性化导航视图。

批量导入与去重 提供基于文本列表的批量链接导入接口，内置模糊去重算法，避免同一资源多次录入。

自定义输出模板 用户可针对不同应用场景（如周报、技术选型、漏洞溯源）选择不同的链接展示模板，控制输出字段的详略程度。

全文检索支持 基于倒排索引为所有链接的元数据及页面快照提供轻量级搜索能力，支持布尔运算符与通配符查询。

协作评论与标注 允许团队成员在特定链接下添加备注、风险等级评定和使用心得，形成群体智慧沉淀。

## 应用场景

开源项目依赖链追踪 在引入第三方库或框架时，开发团队可通过 WebLink Navigator 快速查阅相关技术讨论、官方文档镜像和社区最佳实践案例，避免因单一信息源偏差导致的技术选型失误。

安全事件应急响应 安全分析人员在遭遇新兴漏洞时，可利用本系统汇总的漏洞公告、临时补丁链接和缓解措施页面，在数分钟内完成信息聚合，缩短响应窗口期。

技术文档撰写素材收集 文档工程师在编写版本发布说明或集成指南时，可通过本系统预先整理好的外链池，快速引用规范原文、接口定义和兼容性测试报告，提升文档的权威性。

历史页面归档与对比 对特定域名下的历史新闻页或技术公告进行批量收录，支持按时间线回溯内容演变过程，适用于合规审计和技术演进分析。

## 快速开始

以下指令适用于 Linux / macOS 环境，若使用 Windows 请通过 WSL 或 Git Bash 执行。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
pip install -r requirements.txt
python manage.py init --mode full
python manage.py serve --port 8080
```

完成上述步骤后，访问 http://localhost:8080 即可进入系统主界面。首次启动将自动执行数据库迁移和缓存预热，耗时约 30 秒。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，3.12 暂未通过完整测试 |
| SQLite | 3.35.0 以上 | 内置数据库，用于存储链接元数据与索引 |
| Redis | 6.2 以上 | 可选组件，用于提升检索速度和缓存命中率 |
| Node.js | 18.17.0 以上 | 仅在前端构建模式需要，运行时无需 |
| Nginx | 1.24 以上 | 生产环境推荐反向代理服务器，开发环境可忽略 |
| Celery | 5.3 以上 | 用于异步执行链接存活检测任务 |
| Git | 2.30 以上 | 用于版本管理和模板热更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何在一个小时内完成部署并录入第一批链接 |
| 管理员手册 | docs/admin/operation.md | 如何配置检测频率、管理用户权限和备份数据 |
| 开发者指南 | docs/dev/contribute.md | 如何扩展新的元数据提取器或自定义输出模板 |
| API 参考 | docs/api/endpoints.md | 如何通过 RESTful 接口批量读写链接数据 |
| 故障排查 | docs/troubleshoot/common.md | 遇到检测超时、索引不更新或界面报错时应如何处理 |

## 资源列表

- http://m.wap.fcful.cn/nnews/6531.htm
- http://m.wap.fcful.cn/nnews/7244.htm
- http://m.wap.fcful.cn/nnews/62066.htm
- http://m.wap.fcful.cn/nnews/783130.htm
- http://m.wap.fcful.cn/nnews/199363.htm
- http://m.wap.fcful.cn/nnews/213331.htm
- http://m.wap.fcful.cn/nnews/9065.htm
- http://m.wap.fcful.cn/nnews/0331266.htm
- http://m.wap.fcful.cn/nnews/34658.htm
- http://m.wap.fcful.cn/nnews/78541.htm
- http://m.wap.fcful.cn/nnews/0654195.htm
- http://m.wap.fcful.cn/nnews/5320730.htm
- http://m.wap.fcful.cn/nnews/242384.htm
- http://m.wap.fcful.cn/nnews/67984.htm
- http://m.wap.fcful.cn/nnews/7547.htm
- http://m.wap.fcful.cn/nnews/6743395.htm
- http://m.wap.fcful.cn/nnews/63825.htm
- http://m.wap.fcful.cn/nnews/902935.htm
- http://m.wap.fcful.cn/nnews/3824524.htm
- http://m.wap.fcful.cn/nnews/742701.htm
- http://m.wap.fcful.cn/nnews/35512.htm
- http://m.wap.fcful.cn/nnews/373190.htm
- http://m.wap.fcful.cn/nnews/0669770.htm
- http://m.wap.fcful.cn/nnews/3427193.htm
- http://m.wap.fcful.cn/nnews/7766157.htm
- http://m.wap.fcful.cn/nnews/19332.htm
- http://m.wap.fcful.cn/nnews/81130.htm
- http://m.wap.fcful.cn/nnews/5201.htm
- http://m.wap.fcful.cn/nnews/940186.htm
- http://m.wap.fcful.cn/nnews/0051836.htm
- http://m.wap.fcful.cn/nnews/156996.htm
- http://m.wap.fcful.cn/nnews/05783.htm
- http://m.wap.fcful.cn/nnews/31646.htm
- http://m.wap.fcful.cn/nnews/458891.htm
- http://m.wap.fcful.cn/nnews/73402.htm
- http://m.wap.fcful.cn/nnews/16341.htm
- http://m.wap.fcful.cn/nnews/6703.htm
- http://m.wap.fcful.cn/nnews/78498.htm
- http://m.wap.fcful.cn/nnews/3191783.htm
- http://m.wap.fcful.cn/nnews/215043.htm
- http://m.wap.fcful.cn/nnews/31883.htm
- http://m.wap.fcful.cn/nnews/1707910.htm
- http://m.wap.fcful.cn/nnews/7862051.htm
- http://m.wap.fcful.cn/nnews/86649.htm
- http://m.wap.fcful.cn/nnews/63368.htm
- http://m.wap.fcful.cn/nnews/0018.htm
- http://m.wap.fcful.cn/nnews/1706.htm
- http://m.wap.fcful.cn/nnews/8136.htm
- http://m.wap.fcful.cn/nnews/10349.htm
- http://m.wap.fcful.cn/nnews/603379.htm
- http://m.wap.fcful.cn/nnews/81091.htm
- http://m.wap.fcful.cn/nnews/6411.htm
- http://m.wap.fcful.cn/nnews/660153.htm
- http://m.wap.fcful.cn/nnews/754659.htm
- http://m.wap.fcful.cn/nnews/4985168.htm
- http://m.wap.fcful.cn/nnews/98931.htm
- http://m.wap.fcful.cn/nnews/3630.htm
- http://m.wap.fcful.cn/nnews/2769.htm
- http://m.wap.fcful.cn/nnews/1537.htm
- http://m.wap.fcful.cn/nnews/62126.htm
- http://m.wap.fcful.cn/nnews/692990.htm
- http://m.wap.fcful.cn/nnews/2368493.htm
- http://m.wap.fcful.cn/nnews/315709.htm
- http://m.wap.fcful.cn/nnews/355816.htm
- http://m.wap.fcful.cn/nnews/81134.htm
- http://m.wap.fcful.cn/nnews/3799.htm
- http://m.wap.fcful.cn/nnews/6332548.htm
- http://m.wap.fcful.cn/nnews/2611.htm
- http://m.wap.fcful.cn/nnews/413867.htm
- http://m.wap.fcful.cn/nnews/81329.htm
- http://m.wap.fcful.cn/nnews/93872.htm
- http://m.wap.fcful.cn/nnews/2140.htm
- http://m.wap.fcful.cn/nnews/9349.htm
- http://m.wap.fcful.cn/nnews/3768779.htm
- http://m.wap.fcful.cn/nnews/7676480.htm
- http://m.wap.fcful.cn/nnews/68003.htm
- http://m.wap.fcful.cn/nnews/533955.htm
- http://m.wap.fcful.cn/nnews/2037.htm
- http://m.wap.fcful.cn/nnews/0688.htm
- http://m.wap.fcful.cn/nnews/2157.htm
- http://m.wap.fcful.cn/nnews/4843.htm
- http://m.wap.fcful.cn/nnews/9572930.htm
- http://m.wap.fcful.cn/nnews/6652432.htm
- http://m.wap.fcful.cn/nnews/984565.htm
- http://m.wap.fcful.cn/nnews/6382393.htm
- http://m.wap.fcful.cn/nnews/38236.htm
- http://m.wap.fcful.cn/nnews/0582.htm
- http://m.wap.fcful.cn/nnews/5732.htm
- http://m.wap.fcful.cn/nnews/42592.htm
- http://m.wap.fcful.cn/nnews/034181.htm
- http://m.wap.fcful.cn/nnews/9426648.htm
- http://m.wap.fcful.cn/nnews/76296.htm
- http://m.wap.fcful.cn/nnews/517848.htm
- http://m.wap.fcful.cn/nnews/7593.htm
- http://m.wap.fcful.cn/nnews/25593.htm
- http://m.wap.fcful.cn/nnews/840639.htm
- http://m.wap.fcful.cn/nnews/98159.htm
- http://m.wap.fcful.cn/nnews/645317.htm
- http://m.wap.fcful.cn/nnews/307047.htm
- http://m.wap.fcful.cn/nnews/90330.htm
- http://m.wap.fcful.cn/nnews/2019668.htm
- http://m.wap.fcful.cn/nnews/5071.htm
- http://m.wap.fcful.cn/nnews/373412.htm
- http://m.wap.fcful.cn/nnews/71722.htm
- http://m.wap.fcful.cn/nnews/24367.htm
- http://m.wap.fcful.cn/nnews/430637.htm
- http://m.wap.fcful.cn/nnews/65031.htm
- http://m.wap.fcful.cn/nnews/704550.htm
- http://m.wap.fcful.cn/nnews/363008.htm
- http://m.wap.fcful.cn/nnews/9934.htm
- http://m.wap.fcful.cn/nnews/4561.htm
- http://m.wap.fcful.cn/nnews/016758.htm
- http://m.wap.fcful.cn/nnews/7659311.htm
- http://m.wap.fcful.cn/nnews/303194.htm
- http://m.wap.fcful.cn/nnews/1084.htm
- http://m.wap.fcful.cn/nnews/1056065.htm
- http://m.wap.fcful.cn/nnews/021662.htm
- http://m.wap.fcful.cn/nnews/4804923.htm
- http://m.wap.fcful.cn/nnews/9755.htm
- http://m.wap.fcful.cn/nnews/2209846.htm
- http://m.wap.fcful.cn/nnews/507116.htm
- http://m.wap.fcful.cn/nnews/017805.htm
- http://m.wap.fcful.cn/nnews/92012.htm
- http://m.wap.fcful.cn/nnews/91290.htm
- http://m.wap.fcful.cn/nnews/1433593.htm
- http://m.wap.fcful.cn/nnews/7520793.htm
- http://m.wap.fcful.cn/nnews/2508.htm
- http://m.wap.fcful.cn/nnews/4903.htm
- http://m.wap.fcful.cn/nnews/899778.htm
- http://m.wap.fcful.cn/nnews/22991.htm
- http://m.wap.fcful.cn/nnews/6579.htm
- http://m.wap.fcful.cn/nnews/26622.htm
- http://m.wap.fcful.cn/nnews/40089.htm
- http://m.wap.fcful.cn/nnews/83008.htm
- http://m.wap.fcful.cn/nnews/849150.htm
- http://m.wap.fcful.cn/nnews/0441.htm
- http://m.wap.fcful.cn/nnews/7355544.htm
- http://m.wap.fcful.cn/nnews/893634.htm
- http://m.wap.fcful.cn/nnews/9150.htm
- http://m.wap.fcful.cn/nnews/55415.htm
- http://m.wap.fcful.cn/nnews/07865.htm
- http://m.wap.fcful.cn/nnews/034492.htm
- http://m.wap.fcful.cn/nnews/069382.htm
- http://m.wap.fcful.cn/nnews/7956.htm
- http://m.wap.fcful.cn/nnews/43230.htm
- http://m.wap.fcful.cn/nnews/12237.htm
- http://m.wap.fcful.cn/nnews/736563.htm
- http://m.wap.fcful.cn/nnews/5534.htm
- http://m.wap.fcful.cn/nnews/66911.htm
- http://m.wap.fcful.cn/nnews/3191.htm
- http://m.wap.fcful.cn/nnews/2127603.htm
- http://m.wap.fcful.cn/nnews/5323717.htm
- http://m.wap.fcful.cn/nnews/4237.htm
- http://m.wap.fcful.cn/nnews/89765.htm
- http://m.wap.fcful.cn/nnews/5098987.htm
- http://m.wap.fcful.cn/nnews/853631.htm
- http://m.wap.fcful.cn/nnews/038771.htm
- http://m.wap.fcful.cn/nnews/1790.htm
- http://m.wap.fcful.cn/nnews/9349989.htm
- http://m.wap.fcful.cn/nnews/24918.htm
- http://m.wap.fcful.cn/nnews/1884367.htm
- http://m.wap.fcful.cn/nnews/8902.htm
- http://m.wap.fcful.cn/nnews/2572565.htm
- http://m.wap.fcful.cn/nnews/83510.htm
- http://m.wap.fcful.cn/nnews/1598182.htm
- http://m.wap.fcful.cn/nnews/0872050.htm
- http://m.wap.fcful.cn/nnews/9711.htm
- http://m.wap.fcful.cn/nnews/417148.htm
- http://m.wap.fcful.cn/nnews/07200.htm
- http://m.wap.fcful.cn/nnews/705193.htm
- http://m.wap.fcful.cn/nnews/3092.htm
- http://m.wap.fcful.cn/nnews/456401.htm
- http://m.wap.fcful.cn/nnews/064287.htm
- http://m.wap.fcful.cn/nnews/39823.htm
- http://m.wap.fcful.cn/nnews/6327713.htm
- http://m.wap.fcful.cn/nnews/1514878.htm
- http://m.wap.fcful.cn/nnews/043187.htm
- http://m.wap.fcful.cn/nnews/0859908.htm
- http://m.wap.fcful.cn/nnews/61123.htm
- http://m.wap.fcful.cn/nnews/0438.htm
- http://m.wap.fcful.cn/nnews/80974.htm
- http://m.wap.fcful.cn/nnews/7445.htm
- http://m.wap.fcful.cn/nnews/189586.htm
- http://m.wap.fcful.cn/nnews/12682.htm
- http://m.wap.fcful.cn/nnews/3386047.htm
- http://m.wap.fcful.cn/nnews/4601.htm
- http://m.wap.fcful.cn/nnews/142353.htm
- http://m.wap.fcful.cn/nnews/22618.htm
- http://m.wap.fcful.cn/nnews/2739.htm
- http://m.wap.fcful.cn/nnews/950723.htm
- http://m.wap.fcful.cn/nnews/1804.htm
- http://m.wap.fcful.cn/nnews/1960.htm
- http://m.wap.fcful.cn/nnews/7766395.htm
- http://m.wap.fcful.cn/nnews/512371.htm
- http://m.wap.fcful.cn/nnews/779629.htm
- http://m.wap.fcful.cn/nnews/7584177.htm
- http://m.wap.fcful.cn/nnews/66049.htm
- http://m.wap.fcful.cn/nnews/88430.htm
- http://m.wap.fcful.cn/nnews/326442.htm
- http://m.wap.fcful.cn/nnews/3477215.htm
- http://m.wap.fcful.cn/nnews/582123.htm
- http://m.wap.fcful.cn/nnews/5353572.htm
- http://m.wap.fcful.cn/nnews/6853.htm
- http://m.wap.fcful.cn/nnews/627438.htm
- http://m.wap.fcful.cn/nnews/73128.htm
- http://m.wap.fcful.cn/nnews/7568044.htm
- http://m.wap.fcful.cn/nnews/08520.htm
- http://m.wap.fcful.cn/nnews/4944.htm
- http://m.wap.fcful.cn/nnews/8773257.htm
- http://m.wap.fcful.cn/nnews/5451.htm
- http://m.wap.fcful.cn/nnews/4019002.htm
- http://m.wap.fcful.cn/nnews/7419326.htm
- http://m.wap.fcful.cn/nnews/3495023.htm
- http://m.wap.fcful.cn/nnews/9135464.htm
- http://m.wap.fcful.cn/nnews/65753.htm
- http://m.wap.fcful.cn/nnews/62359.htm
- http://m.wap.fcful.cn/nnews/56663.htm
- http://m.wap.fcful.cn/nnews/083722.htm
- http://m.wap.fcful.cn/nnews/90061.htm
- http://m.wap.fcful.cn/nnews/52620.htm
- http://m.wap.fcful.cn/nnews/9642048.htm
- http://m.wap.fcful.cn/nnews/9471109.htm
- http://m.wap.fcful.cn/nnews/602315.htm
- http://m.wap.fcful.cn/nnews/27610.htm
- http://m.wap.fcful.cn/nnews/37029.htm
- http://m.wap.fcful.cn/nnews/360771.htm
- http://m.wap.fcful.cn/nnews/2188.htm
- http://m.wap.fcful.cn/nnews/0588520.htm
- http://m.wap.fcful.cn/nnews/24717.htm
- http://m.wap.fcful.cn/nnews/67418.htm
- http://m.wap.fcful.cn/nnews/6402.htm
- http://m.wap.fcful.cn/nnews/6497346.htm
- http://m.wap.fcful.cn/nnews/9200.htm
- http://m.wap.fcful.cn/nnews/007128.htm
- http://m.wap.fcful.cn/nnews/61960.htm
- http://m.wap.fcful.cn/nnews/011159.htm
- http://m.wap.fcful.cn/nnews/1685591.htm
- http://m.wap.fcful.cn/nnews/293259.htm
- http://m.wap.fcful.cn/nnews/986278.htm
- http://m.wap.fcful.cn/nnews/785633.htm
- http://m.wap.fcful.cn/nnews/9867.htm
- http://m.wap.fcful.cn/nnews/3325.htm
- http://m.wap.fcful.cn/nnews/36273.htm
- http://m.wap.fcful.cn/nnews/5861836.htm
- http://m.wap.fcful.cn/nnews/9584947.htm
- http://m.wap.fcful.cn/nnews/625227.htm
- http://m.wap.fcful.cn/nnews/7436.htm
- http://m.wap.fcful.cn/nnews/870742.htm
- http://m.wap.fcful.cn/nnews/52449.htm
- http://m.wap.fcful.cn/nnews/4790158.htm

## 项目结构

项目采用分层架构设计，将数据采集、清洗、存储、检索和展示逻辑进行明确分离。核心代码全部位于 src 目录下，测试用例与主代码隔离，便于持续集成。

```
weblink-navigator/
├── src/
│   ├── core/                       # 核心数据模型与数据库抽象层
│   │   ├── models.py               # SQLAlchemy ORM 定义，包含 Link, Tag, CheckLog 等表
│   │   └── dao.py                  # 数据访问对象，封装增删改查与分页逻辑
│   ├── collector/                  # 链接采集与元数据抽取模块
│   │   ├── fetcher.py              # 基于 aiohttp 的异步 HTTP 请求器，支持重试与代理
│   │   ├── parser.py               # 基于 lxml 和 readability 的内容解析器
│   │   └── validator.py            # URL 格式校验与域名黑名单过滤
│   ├── indexer/                    # 全文索引构建与查询
│   │   ├── builder.py              # 基于 whoosh 的索引构建器，支持增量更新
│   │   └── searcher.py             # 查询解析器，支持字段权重与模糊匹配
│   ├── scheduler/                  # 定时任务调度
│   │   ├── tasks.py                # Celery 任务定义：检测存活、更新快照、清理过期
│   │   └── beat.py                 # 周期配置，默认每 6 小时触发一次全量检测
│   ├── web/                        # 可视化界面与 REST API
│   │   ├── routes/                 # Flask 蓝图路由，按功能拆分
│   │   ├── templates/              # Jinja2 模板，适配桌面与移动端
│   │   └── static/                 # 编译后的 CSS / JS 资源
│   └── utils/                      # 通用工具函数
│       ├── logger.py               # 基于 logging 的日志分级输出
│       └── config.py               # 环境变量与配置项加载
├── tests/                          # 单元测试与集成测试
│   ├── test_fetcher.py             # 模拟异常响应、超时和重定向
│   └── test_parser.py              # 对比不同页面结构的解析准确率
├── scripts/                        # 运维脚本
│   ├── init_db.py                  # 初始化数据库表结构和默认标签
│   └── import_batch.py             # 批量导入文本列表中的 URL
├── docs/                           # 完整文档源码
├── requirements.txt                # Python 依赖清单
├── Dockerfile                      # 多阶段构建，产出约 120MB 镜像
├── docker-compose.yml              # 整合 Redis、Nginx 和 Celery Worker
└── README.md                       # 本文件
```

## 贡献指南

贡献者需遵守行为准则，并确保所有提交内容符合项目许可协议。

1. 查阅 issue 列表，选择未被认领的任务或提出新需求，等待核心成员反馈后再着手开发，避免重复劳动。
2. 从主仓库 Fork 个人副本，在本地创建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。
3. 编写或修改代码后，必须补充对应的单元测试，确保原有测试用例全部通过，且新增代码覆盖率不低于 80%。
4. 提交前运行 `make lint` 和 `make test` 进行静态检查和完整测试套件验证，修复所有错误和警告。
5. 发起 Pull Request 至主仓库的 develop 分支，描述中需引用相关 issue 编号，并附上测试结果截图或日志。

## 常见问题

问：系统检测链接存活时，是否会频繁请求目标服务器，造成对方压力？

系统默认采用指数退避策略，并发请求数上限为 10，且每个目标域名在 60 秒内仅接受一次检测请求。对于已标记为稳定的链接，检测间隔自动延长至 24 小时。用户亦可手动调整并发阈值和间隔参数，以适应内部网络环境。

问：导入大量链接后，检索速度明显下降，应如何优化？

首先检查 Redis 缓存是否正常运行，索引构建任务是否已执行完毕。若数据量超过 10 万条，建议将 SQLite 替换为 PostgreSQL，并开启全文索引的 GIN 扩展。项目文档中提供了分库分表和读写分离的参考方案。

问：如何备份已录入的链接数据和标注信息？

系统提供了 `manage.py backup` 命令，可将数据库完整导出为 JSON 格式的压缩包，同时保留所有关联标签和评论。备份文件可通过 `manage.py restore` 在不同部署实例间迁移。建议配合 crontab 设置每周全量备份。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
