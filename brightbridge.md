# WapNews Resource Aggregator

WapNews Resource Aggregator 是一个面向移动端新闻资讯聚合与内容导航的开源工具集，专注于对 wap.fcful.cn 域名下的新闻资源进行结构化采集、分类整理与快速检索。该项目服务于需要从移动新闻站点批量获取内容链接、进行数据分析或构建垂直信息流的开发者与研究人员。通过提供标准化的资源索引与解析辅助工具，该项目降低了从零开始构建移动新闻抓取系统的门槛。

## 功能概览

**批量链接提取**：支持从指定域名路径下批量提取 .htm 新闻链接，自动识别链接命名模式与路径结构。

**资源分类索引**：根据 URL 中的数字编号特征对新闻资源进行自动归类，生成层级化的索引目录。

**去重与校验机制**：内置 URL 去重算法与链接可用性校验，确保资源列表的整洁性与可访问性。

**结构化数据导出**：支持将采集到的链接列表导出为 JSON、CSV 或纯文本格式，便于下游数据处理流程集成。

**定时更新触发器**：提供基于 cron 表达式的定时任务配置接口，允许用户设定资源更新频率。

**元数据模拟提取**：针对无法直接获取页面内容的场景，提供基于 URL 规则的模拟元数据生成功能，包括发布时间推测与分类标签预测。

**黑名单过滤规则**：支持用户自定义关键词或路径正则表达式，过滤无关或低质量链接。

**增量更新支持**：记录历史采集状态，仅对新增或变更链接进行处理，提升大规模采集场景下的执行效率。

## 应用场景

新闻聚合平台数据采集：内容聚合服务商可使用该项目快速构建针对 wap.fcful.cn 的资源采集管道，定期拉取最新新闻链接并推送至自身内容处理系统。

移动端信息流研发测试：移动应用开发者在构建信息流原型时，可将该项目作为数据源模拟工具，快速获得结构化的新闻链接列表用于 UI 渲染与交互测试。

舆情监控系统种子链接生成：舆情分析团队可基于该项目输出的资源列表作为爬虫入口种子，定向扩展至具体新闻页面进行内容抓取与情感分析。

学术研究数据采样：新闻传播学或计算社会科学研究者可利用该项目批量获取新闻链接样本，用于内容分类、传播路径或媒介框架的量化研究。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/wapnews-aggregator.git

# 进入项目目录
cd wapnews-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行资源列表采集示例
python cli.py collect --base http://m.wap.fcful.cn --output ./output/links.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 稳定版 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于发送网络请求与获取响应内容 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，辅助从页面中提取链接与文本信息 |
| lxml | 4.9.0 及以上 | XML/HTML 解析器后端，为 BeautifulSoup 提供高性能解析能力 |
| pandas | 2.0.0 及以上 | 数据处理库，用于结构化导出与数据帧操作（可选，但推荐） |
| click | 8.1.0 及以上 | 命令行界面框架，用于构建 CLI 交互命令 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | docs/user_guide.md | 如何安装、配置与运行采集任务；如何自定义输出格式与过滤规则 |
| 开发者手册 | docs/developer_manual.md | 项目模块划分与核心类设计说明；如何扩展新的解析器或导出器 |
| API 参考 | docs/api_reference.md | 各模块函数签名、参数说明与返回值定义；异常处理规范 |
| 部署运维 | docs/deployment.md | 生产环境下的定时任务配置、日志管理与性能调优建议 |

## 资源列表

- http://m.wap.fcful.cn/nnews/8866163.htm
- http://m.wap.fcful.cn/nnews/08478.htm
- http://m.wap.fcful.cn/nnews/843847.htm
- http://m.wap.fcful.cn/nnews/3118145.htm
- http://m.wap.fcful.cn/nnews/80356.htm
- http://m.wap.fcful.cn/nnews/3205638.htm
- http://m.wap.fcful.cn/nnews/6796.htm
- http://m.wap.fcful.cn/nnews/3346429.htm
- http://m.wap.fcful.cn/nnews/868135.htm
- http://m.wap.fcful.cn/nnews/3245.htm
- http://m.wap.fcful.cn/nnews/46276.htm
- http://m.wap.fcful.cn/nnews/5609770.htm
- http://m.wap.fcful.cn/nnews/2607133.htm
- http://m.wap.fcful.cn/nnews/0199224.htm
- http://m.wap.fcful.cn/nnews/7612040.htm
- http://m.wap.fcful.cn/nnews/748329.htm
- http://m.wap.fcful.cn/nnews/0608.htm
- http://m.wap.fcful.cn/nnews/655159.htm
- http://m.wap.fcful.cn/nnews/096182.htm
- http://m.wap.fcful.cn/nnews/635439.htm
- http://m.wap.fcful.cn/nnews/7645563.htm
- http://m.wap.fcful.cn/nnews/96064.htm
- http://m.wap.fcful.cn/nnews/1401984.htm
- http://m.wap.fcful.cn/nnews/3258.htm
- http://m.wap.fcful.cn/nnews/517557.htm
- http://m.wap.fcful.cn/nnews/50801.htm
- http://m.wap.fcful.cn/nnews/919413.htm
- http://m.wap.fcful.cn/nnews/12246.htm
- http://m.wap.fcful.cn/nnews/3725113.htm
- http://m.wap.fcful.cn/nnews/9720.htm
- http://m.wap.fcful.cn/nnews/0588.htm
- http://m.wap.fcful.cn/nnews/00377.htm
- http://m.wap.fcful.cn/nnews/794502.htm
- http://m.wap.fcful.cn/nnews/2598578.htm
- http://m.wap.fcful.cn/nnews/7554118.htm
- http://m.wap.fcful.cn/nnews/8547980.htm
- http://m.wap.fcful.cn/nnews/605059.htm
- http://m.wap.fcful.cn/nnews/1778.htm
- http://m.wap.fcful.cn/nnews/12458.htm
- http://m.wap.fcful.cn/nnews/60825.htm
- http://m.wap.fcful.cn/nnews/2474.htm
- http://m.wap.fcful.cn/nnews/549956.htm
- http://m.wap.fcful.cn/nnews/402337.htm
- http://m.wap.fcful.cn/nnews/7225908.htm
- http://m.wap.fcful.cn/nnews/7825710.htm
- http://m.wap.fcful.cn/nnews/15409.htm
- http://m.wap.fcful.cn/nnews/48880.htm
- http://m.wap.fcful.cn/nnews/52335.htm
- http://m.wap.fcful.cn/nnews/85774.htm
- http://m.wap.fcful.cn/nnews/9377.htm
- http://m.wap.fcful.cn/nnews/66318.htm
- http://m.wap.fcful.cn/nnews/2732.htm
- http://m.wap.fcful.cn/nnews/6194415.htm
- http://m.wap.fcful.cn/nnews/9647062.htm
- http://m.wap.fcful.cn/nnews/8498805.htm
- http://m.wap.fcful.cn/nnews/83974.htm
- http://m.wap.fcful.cn/nnews/12854.htm
- http://m.wap.fcful.cn/nnews/54576.htm
- http://m.wap.fcful.cn/nnews/0930.htm
- http://m.wap.fcful.cn/nnews/7908.htm
- http://m.wap.fcful.cn/nnews/4725.htm
- http://m.wap.fcful.cn/nnews/4383.htm
- http://m.wap.fcful.cn/nnews/68227.htm
- http://m.wap.fcful.cn/nnews/52593.htm
- http://m.wap.fcful.cn/nnews/5267.htm
- http://m.wap.fcful.cn/nnews/426236.htm
- http://m.wap.fcful.cn/nnews/1153.htm
- http://m.wap.fcful.cn/nnews/0504785.htm
- http://m.wap.fcful.cn/nnews/1833.htm
- http://m.wap.fcful.cn/nnews/2633174.htm
- http://m.wap.fcful.cn/nnews/098861.htm
- http://m.wap.fcful.cn/nnews/28137.htm
- http://m.wap.fcful.cn/nnews/99582.htm
- http://m.wap.fcful.cn/nnews/021535.htm
- http://m.wap.fcful.cn/nnews/08581.htm
- http://m.wap.fcful.cn/nnews/6195043.htm
- http://m.wap.fcful.cn/nnews/5266186.htm
- http://m.wap.fcful.cn/nnews/4719.htm
- http://m.wap.fcful.cn/nnews/9896605.htm
- http://m.wap.fcful.cn/nnews/47885.htm
- http://m.wap.fcful.cn/nnews/439723.htm
- http://m.wap.fcful.cn/nnews/0866659.htm
- http://m.wap.fcful.cn/nnews/1524512.htm
- http://m.wap.fcful.cn/nnews/8132.htm
- http://m.wap.fcful.cn/nnews/939339.htm
- http://m.wap.fcful.cn/nnews/95822.htm
- http://m.wap.fcful.cn/nnews/250185.htm
- http://m.wap.fcful.cn/nnews/903363.htm
- http://m.wap.fcful.cn/nnews/8165.htm
- http://m.wap.fcful.cn/nnews/2293152.htm
- http://m.wap.fcful.cn/nnews/1412.htm
- http://m.wap.fcful.cn/nnews/127078.htm
- http://m.wap.fcful.cn/nnews/79065.htm
- http://m.wap.fcful.cn/nnews/418399.htm
- http://m.wap.fcful.cn/nnews/969925.htm
- http://m.wap.fcful.cn/nnews/05542.htm
- http://m.wap.fcful.cn/nnews/0598.htm
- http://m.wap.fcful.cn/nnews/75291.htm
- http://m.wap.fcful.cn/nnews/78431.htm
- http://m.wap.fcful.cn/nnews/4496196.htm
- http://m.wap.fcful.cn/nnews/18577.htm
- http://m.wap.fcful.cn/nnews/8093961.htm
- http://m.wap.fcful.cn/nnews/252275.htm
- http://m.wap.fcful.cn/nnews/150583.htm
- http://m.wap.fcful.cn/nnews/9927.htm
- http://m.wap.fcful.cn/nnews/227483.htm
- http://m.wap.fcful.cn/nnews/455558.htm
- http://m.wap.fcful.cn/nnews/76387.htm
- http://m.wap.fcful.cn/nnews/096856.htm
- http://m.wap.fcful.cn/nnews/61452.htm
- http://m.wap.fcful.cn/nnews/7293032.htm
- http://m.wap.fcful.cn/nnews/7675593.htm
- http://m.wap.fcful.cn/nnews/08053.htm
- http://m.wap.fcful.cn/nnews/6573.htm
- http://m.wap.fcful.cn/nnews/7856683.htm
- http://m.wap.fcful.cn/nnews/907860.htm
- http://m.wap.fcful.cn/nnews/1296.htm
- http://m.wap.fcful.cn/nnews/5459.htm
- http://m.wap.fcful.cn/nnews/2045179.htm
- http://m.wap.fcful.cn/nnews/080884.htm
- http://m.wap.fcful.cn/nnews/3305761.htm
- http://m.wap.fcful.cn/nnews/071694.htm
- http://m.wap.fcful.cn/nnews/236959.htm
- http://m.wap.fcful.cn/nnews/94903.htm
- http://m.wap.fcful.cn/nnews/2383725.htm
- http://m.wap.fcful.cn/nnews/8856.htm
- http://m.wap.fcful.cn/nnews/7016.htm
- http://m.wap.fcful.cn/nnews/541898.htm
- http://m.wap.fcful.cn/nnews/1306144.htm
- http://m.wap.fcful.cn/nnews/9279.htm
- http://m.wap.fcful.cn/nnews/9416878.htm
- http://m.wap.fcful.cn/nnews/6580.htm
- http://m.wap.fcful.cn/nnews/2449669.htm
- http://m.wap.fcful.cn/nnews/288811.htm
- http://m.wap.fcful.cn/nnews/4005.htm
- http://m.wap.fcful.cn/nnews/2232839.htm
- http://m.wap.fcful.cn/nnews/7776521.htm
- http://m.wap.fcful.cn/nnews/66751.htm
- http://m.wap.fcful.cn/nnews/432374.htm
- http://m.wap.fcful.cn/nnews/6810222.htm
- http://m.wap.fcful.cn/nnews/5794.htm
- http://m.wap.fcful.cn/nnews/7618299.htm
- http://m.wap.fcful.cn/nnews/82998.htm
- http://m.wap.fcful.cn/nnews/17309.htm
- http://m.wap.fcful.cn/nnews/6182079.htm
- http://m.wap.fcful.cn/nnews/671871.htm
- http://m.wap.fcful.cn/nnews/6316410.htm
- http://m.wap.fcful.cn/nnews/6803.htm
- http://m.wap.fcful.cn/nnews/6676254.htm
- http://m.wap.fcful.cn/nnews/0793281.htm
- http://m.wap.fcful.cn/nnews/3794.htm
- http://m.wap.fcful.cn/nnews/687578.htm
- http://m.wap.fcful.cn/nnews/94216.htm
- http://m.wap.fcful.cn/nnews/36509.htm
- http://m.wap.fcful.cn/nnews/8765784.htm
- http://m.wap.fcful.cn/nnews/835095.htm
- http://m.wap.fcful.cn/nnews/9738740.htm
- http://m.wap.fcful.cn/nnews/75261.htm
- http://m.wap.fcful.cn/nnews/6131396.htm
- http://m.wap.fcful.cn/nnews/18621.htm
- http://m.wap.fcful.cn/nnews/4393442.htm
- http://m.wap.fcful.cn/nnews/7400.htm
- http://m.wap.fcful.cn/nnews/8610.htm
- http://m.wap.fcful.cn/nnews/143720.htm
- http://m.wap.fcful.cn/nnews/68861.htm
- http://m.wap.fcful.cn/nnews/588354.htm
- http://m.wap.fcful.cn/nnews/5412609.htm
- http://m.wap.fcful.cn/nnews/571524.htm
- http://m.wap.fcful.cn/nnews/6802.htm
- http://m.wap.fcful.cn/nnews/602395.htm
- http://m.wap.fcful.cn/nnews/5869.htm
- http://m.wap.fcful.cn/nnews/2389.htm
- http://m.wap.fcful.cn/nnews/026818.htm
- http://m.wap.fcful.cn/nnews/613476.htm
- http://m.wap.fcful.cn/nnews/7036825.htm
- http://m.wap.fcful.cn/nnews/50260.htm
- http://m.wap.fcful.cn/nnews/587034.htm
- http://m.wap.fcful.cn/nnews/33777.htm
- http://m.wap.fcful.cn/nnews/9511.htm
- http://m.wap.fcful.cn/nnews/260998.htm
- http://m.wap.fcful.cn/nnews/0185.htm
- http://m.wap.fcful.cn/nnews/56466.htm
- http://m.wap.fcful.cn/nnews/49760.htm
- http://m.wap.fcful.cn/nnews/8809933.htm
- http://m.wap.fcful.cn/nnews/717796.htm
- http://m.wap.fcful.cn/nnews/1130810.htm
- http://m.wap.fcful.cn/nnews/0401743.htm
- http://m.wap.fcful.cn/nnews/8278.htm
- http://m.wap.fcful.cn/nnews/6729.htm
- http://m.wap.fcful.cn/nnews/870016.htm
- http://m.wap.fcful.cn/nnews/84679.htm
- http://m.wap.fcful.cn/nnews/9824.htm
- http://m.wap.fcful.cn/nnews/00436.htm
- http://m.wap.fcful.cn/nnews/73018.htm
- http://m.wap.fcful.cn/nnews/3270.htm
- http://m.wap.fcful.cn/nnews/8453164.htm
- http://m.wap.fcful.cn/nnews/9955463.htm
- http://m.wap.fcful.cn/nnews/834247.htm
- http://m.wap.fcful.cn/nnews/7936811.htm
- http://m.wap.fcful.cn/nnews/47108.htm
- http://m.wap.fcful.cn/nnews/179165.htm
- http://m.wap.fcful.cn/nnews/05948.htm
- http://m.wap.fcful.cn/nnews/375648.htm
- http://m.wap.fcful.cn/nnews/89127.htm
- http://m.wap.fcful.cn/nnews/1912145.htm
- http://m.wap.fcful.cn/nnews/0653.htm
- http://m.wap.fcful.cn/nnews/847235.htm
- http://m.wap.fcful.cn/nnews/99750.htm
- http://m.wap.fcful.cn/nnews/98272.htm
- http://m.wap.fcful.cn/nnews/046289.htm
- http://m.wap.fcful.cn/nnews/863091.htm
- http://m.wap.fcful.cn/nnews/427786.htm
- http://m.wap.fcful.cn/nnews/044807.htm
- http://m.wap.fcful.cn/nnews/232600.htm
- http://m.wap.fcful.cn/nnews/6428.htm
- http://m.wap.fcful.cn/nnews/031431.htm
- http://m.wap.fcful.cn/nnews/52769.htm
- http://m.wap.fcful.cn/nnews/3672344.htm
- http://m.wap.fcful.cn/nnews/2526875.htm
- http://m.wap.fcful.cn/nnews/8504437.htm
- http://m.wap.fcful.cn/nnews/9557.htm
- http://m.wap.fcful.cn/nnews/14078.htm
- http://m.wap.fcful.cn/nnews/960022.htm
- http://m.wap.fcful.cn/nnews/825719.htm
- http://m.wap.fcful.cn/nnews/9123028.htm
- http://m.wap.fcful.cn/nnews/4758340.htm
- http://m.wap.fcful.cn/nnews/23469.htm
- http://m.wap.fcful.cn/nnews/80344.htm
- http://m.wap.fcful.cn/nnews/8980.htm
- http://m.wap.fcful.cn/nnews/4591.htm
- http://m.wap.fcful.cn/nnews/8097653.htm
- http://m.wap.fcful.cn/nnews/0838.htm
- http://m.wap.fcful.cn/nnews/3265188.htm
- http://m.wap.fcful.cn/nnews/9347.htm
- http://m.wap.fcful.cn/nnews/12934.htm
- http://m.wap.fcful.cn/nnews/514686.htm
- http://m.wap.fcful.cn/nnews/264123.htm
- http://m.wap.fcful.cn/nnews/581929.htm
- http://m.wap.fcful.cn/nnews/53991.htm
- http://m.wap.fcful.cn/nnews/225570.htm
- http://m.wap.fcful.cn/nnews/002069.htm
- http://m.wap.fcful.cn/nnews/81538.htm
- http://m.wap.fcful.cn/nnews/2226687.htm
- http://m.wap.fcful.cn/nnews/3214.htm
- http://m.wap.fcful.cn/nnews/0476898.htm
- http://m.wap.fcful.cn/nnews/0443.htm
- http://m.wap.fcful.cn/nnews/34221.htm
- http://m.wap.fcful.cn/nnews/15030.htm
- http://m.wap.fcful.cn/nnews/16960.htm
- http://m.wap.fcful.cn/nnews/4775.htm

## 项目结构

```
wapnews-aggregator/
├── cli.py                      # 命令行入口，定义 collect、validate、export 等子命令
├── requirements.txt            # Python 依赖清单，锁定所有第三方库版本
├── setup.py                    # 项目打包与安装配置，声明 entry_points 控制台脚本
├── wapnews/                    # 核心源码包
│   ├── __init__.py             # 包初始化，暴露 Collector、Parser、Exporter 类
│   ├── collector.py            # 链接采集器，包含并发请求控制与重试逻辑
│   ├── parser.py               # URL 解析器，负责提取编号、路径分段与格式规范化
│   ├── exporter.py             # 数据导出器，支持 json、csv、txt 三种输出格式
│   ├── filters.py              # 黑名单与白名单过滤规则引擎，基于正则表达式
│   ├── scheduler.py            # 定时任务调度器，封装 APScheduler 实现 cron 触发
│   └── utils.py                # 通用工具函数，包括日志配置、时间转换与文件操作
├── tests/                      # 单元测试与集成测试目录
│   ├── test_collector.py       # 测试采集器的超时处理与重试机制
│   ├── test_parser.py          # 测试解析器的 URL 拆分与编号提取准确性
│   └── test_filters.py         # 测试过滤规则的正则匹配与排除逻辑
├── config/                     # 配置文件目录
│   ├── default.yaml            # 默认配置，含请求头、超时、重试次数等参数
│   └── custom.yaml.example     # 用户自定义配置模板，展示过滤规则与输出路径
├── output/                     # 默认输出目录（gitignore 忽略）
│   └── links.json              # 示例输出文件，包含采集时间戳与链接列表
├── docs/                       # 文档目录
│   ├── user_guide.md           # 用户指南，详细说明各命令用法与配置项
│   ├── developer_manual.md     # 开发者手册，讲解核心类设计与扩展钩子
│   ├── api_reference.md        # 自动生成的 API 文档，含函数签名与示例
│   └── deployment.md           # 部署指南，涵盖 systemd 服务配置与日志轮转
└── LICENSE                     # MIT 许可证文件
```

## 贡献指南

提交 Issue 报告缺陷或功能请求：请使用 GitHub Issues 模板，清晰描述问题现象、复现步骤与运行环境信息。若涉及链接采集失败，请附上完整的错误堆栈与目标 URL。

创建 Pull Request 进行代码贡献：从 main 分支创建新的 feature 或 fix 分支，确保代码通过所有单元测试（pytest）并保持测试覆盖率不低于 85%。提交前运行 pre-commit 钩子进行代码风格检查。

补充或完善文档：文档位于 docs/ 目录下，采用 Markdown 格式。修改后请确保目录索引与内部链接正确，并在 PR 描述中标注文档变更范围。

提供资源列表更新建议：若发现资源列表中存在失效链接或需增补新链接，请通过 Issue 提交更新请求，并附上验证可访问性的测试记录。

参与讨论与社区支持：加入项目讨论区（GitHub Discussions）回答其他用户的使用疑问，或分享自身基于该项目构建的应用案例。

## 常见问题

采集过程中遇到 HTTP 403 或 429 状态码应如何处理？

此类状态码通常表示目标服务器实施了访问频率限制或反爬策略。建议在配置文件中调低并发请求数（max_workers），并增加请求间隔延迟（delay_seconds）。亦可配置代理列表（proxies）实现 IP 轮换。若问题持续存在，请检查 User-Agent 请求头是否被目标站点识别为自动化工具。

能否用于采集其他域名下的新闻资源？

项目核心采集与解析逻辑设计为与域名解耦。你只需在命令行或配置文件中修改 base_url 参数为其他目标域名，并确保目标站点的 URL 路径结构与现有解析规则兼容。若路径结构存在较大差异，可通过继承 BaseParser 类并重写 parse_url 方法实现自定义解析器。

导出的链接列表如何对接下游爬虫系统？

导出器支持 json 与 csv 格式，可被 Scrapy、Apache Nutch 等主流爬虫框架的种子导入模块直接读取。对于定制化需求，可调用 exporter 模块中的 export_as 函数，传入自定义序列化函数以适配特定数据管道格式。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
