# NewsLink Aggregator

NewsLink Aggregator 是一个面向移动端资讯聚合与内容导航的开源工具集，专注于对半结构化新闻页面进行批量采集、链接提取、内容归类与元数据标准化输出。项目定位为技术研究者、舆情分析人员与轻量级内容聚合平台提供可复用的新闻链接处理管道，不对新闻内容本身做立场判断，仅提供确定性链接提取与分类能力。

目标用户包括开源爬虫开发者、新闻聚合站点运维人员、NLP 数据集构建者以及需要定期跟踪特定新闻源链接变化的自动化脚本使用者。项目以完全离线可运行、无外部API依赖、低内存占用为设计原则，能够在单核1GB内存的云服务器上完成每日数万级链接的增量处理。

## 功能概览

批量链接提取 从指定新闻域名下批量提取所有HTML页面中的超链接，支持递归深度控制与路径去重。

移动端页面适配 自动识别wap移动端页面结构，提取正文内容链接与导航分类链接，过滤广告与追踪参数。

链接状态探测 对提取出的每一条链接执行HTTP状态码检查与重定向跟踪，输出可访问性状态与响应时间。

内容类型分类 依据链接路径特征与页面Meta信息，将链接归类为新闻正文、列表页、专题页、图片页或外部引用。

增量更新索引 维护本地SQLite索引库，记录每次抓取的链接集合与变更状态，支持按时间范围查询新增或失效链接。

去重与归一化 对同一新闻内容的多篇转载链接执行URL归一化与主域判定，保留最短有效路径作为唯一标识。

导出与集成接口 支持将处理结果导出为JSON Lines、CSV或纯文本列表格式，并提供HTTP回调接口供下游系统直接消费。

日志与监控 记录每次运行的任务ID、处理耗时、成功与失败计数，支持通过日志文件或syslog输出结构化事件。

## 应用场景

舆情监控系统的前置链路 在搭建区域性新闻舆情监控系统时，使用NewsLink Aggregator每日定时从指定的移动端新闻站点拉取最新链接列表，再将链接分发给后续的正文提取与情感分析模块，实现采集与处理的解耦。

历史链接归档与回溯分析 研究人员可基于本工具对特定新闻域名的历史链接进行全量抓取，生成按日期索引的链接快照，用于分析媒体关注度变化、事件传播路径或链接存活周期。

私有化RSS生成器 对于不提供RSS订阅的新闻站点，可利用本项目提取分类导航页下的所有文章链接，再结合正文摘要生成自定义RSS feed，供内部阅读器使用。

自动化链接可用性巡检 运维团队可将本工具集成到监控体系，定期检测关键新闻链接的访问状态，当大量链接返回404或5xx时触发告警，及时感知内容下架或站点异常。

数据标注辅助工具 在进行新闻文本标注或数据集构建时，通过本工具按关键词或路径模式筛选链接，批量导出待标注链接列表，减少人工检索成本。

## 快速开始

以下步骤指导您在Linux或macOS环境中完成项目的克隆、依赖安装与初次运行。

```bash
# 克隆项目仓库
git clone https://github.com/example/news-link-aggregator.git
cd news-link-aggregator

# 安装Python依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行示例抓取任务（默认从配置文件中读取目标域名）
python run_aggregator.py --domain http://m.wap.fcful.cn --depth 1 --output ./output/links_$(date +%Y%m%d).jsonl
```

若需要以配置文件方式运行，请复制示例配置并修改：

```bash
cp config/config.example.yaml config/config.yaml
# 编辑config.yaml中的target_domains与输出路径
python run_aggregator.py --config config/config.yaml
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用3.10或3.11长期支持版本 |
| requests | 2.28.0 及以上 | HTTP请求与链接状态探测库 |
| beautifulsoup4 | 4.11.0 及以上 | HTML解析与链接提取，依赖lxml或html.parser |
| lxml | 4.9.0 及以上 | 高性能XML/HTML解析器，推荐安装以提升解析速度 |
| sqlite3 | 内置模块 | Python内置轻量级数据库，用于增量索引存储 |
| urllib3 | 1.26.0 及以上 | 连接池与重试机制底层库，由requests自动依赖 |
| certifi | 2022.12.0 及以上 | SSL证书验证，确保HTTPS链接探测安全 |
| tldextract | 3.4.0 及以上 | 顶级域名提取与URL归一化辅助 |
| pytest | 7.0.0 及以上 | 单元测试框架，仅开发与测试环境需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何安装、配置与运行聚合器；如何理解输出文件格式 |
| 开发指南 | docs/developer_guide.md | 项目模块划分、如何新增解析器插件、如何扩展链接过滤器 |
| API参考 | docs/api_reference.md | 各核心类与函数的详细签名、参数说明与异常定义 |
| 运维手册 | docs/operations.md | 生产环境部署建议、定时任务配置、日志轮转与性能调优 |
| 常见问题 | docs/faq.md | 高频问题速查，涵盖网络错误、解析失败与索引异常 |

## 资源列表

- http://m.wap.fcful.cn/nnews/459702.htm
- http://m.wap.fcful.cn/nnews/5334.htm
- http://m.wap.fcful.cn/nnews/752701.htm
- http://m.wap.fcful.cn/nnews/8905642.htm
- http://m.wap.fcful.cn/nnews/770559.htm
- http://m.wap.fcful.cn/nnews/931625.htm
- http://m.wap.fcful.cn/nnews/236833.htm
- http://m.wap.fcful.cn/nnews/2548022.htm
- http://m.wap.fcful.cn/nnews/9476184.htm
- http://m.wap.fcful.cn/nnews/86598.htm
- http://m.wap.fcful.cn/nnews/69294.htm
- http://m.wap.fcful.cn/nnews/14111.htm
- http://m.wap.fcful.cn/nnews/2429148.htm
- http://m.wap.fcful.cn/nnews/7852.htm
- http://m.wap.fcful.cn/nnews/7302857.htm
- http://m.wap.fcful.cn/nnews/7428.htm
- http://m.wap.fcful.cn/nnews/71248.htm
- http://m.wap.fcful.cn/nnews/3234134.htm
- http://m.wap.fcful.cn/nnews/7182.htm
- http://m.wap.fcful.cn/nnews/707497.htm
- http://m.wap.fcful.cn/nnews/4658.htm
- http://m.wap.fcful.cn/nnews/2232.htm
- http://m.wap.fcful.cn/nnews/6074401.htm
- http://m.wap.fcful.cn/nnews/4613750.htm
- http://m.wap.fcful.cn/nnews/7366943.htm
- http://m.wap.fcful.cn/nnews/51775.htm
- http://m.wap.fcful.cn/nnews/0223.htm
- http://m.wap.fcful.cn/nnews/79261.htm
- http://m.wap.fcful.cn/nnews/138100.htm
- http://m.wap.fcful.cn/nnews/2528.htm
- http://m.wap.fcful.cn/nnews/2158.htm
- http://m.wap.fcful.cn/nnews/834352.htm
- http://m.wap.fcful.cn/nnews/2443117.htm
- http://m.wap.fcful.cn/nnews/66191.htm
- http://m.wap.fcful.cn/nnews/1648416.htm
- http://m.wap.fcful.cn/nnews/2195.htm
- http://m.wap.fcful.cn/nnews/9130.htm
- http://m.wap.fcful.cn/nnews/8413070.htm
- http://m.wap.fcful.cn/nnews/878657.htm
- http://m.wap.fcful.cn/nnews/76787.htm
- http://m.wap.fcful.cn/nnews/594956.htm
- http://m.wap.fcful.cn/nnews/1100823.htm
- http://m.wap.fcful.cn/nnews/27817.htm
- http://m.wap.fcful.cn/nnews/4515.htm
- http://m.wap.fcful.cn/nnews/18502.htm
- http://m.wap.fcful.cn/nnews/63563.htm
- http://m.wap.fcful.cn/nnews/90040.htm
- http://m.wap.fcful.cn/nnews/6696588.htm
- http://m.wap.fcful.cn/nnews/8660891.htm
- http://m.wap.fcful.cn/nnews/5428.htm
- http://m.wap.fcful.cn/nnews/0263202.htm
- http://m.wap.fcful.cn/nnews/93775.htm
- http://m.wap.fcful.cn/nnews/3126.htm
- http://m.wap.fcful.cn/nnews/51321.htm
- http://m.wap.fcful.cn/nnews/47757.htm
- http://m.wap.fcful.cn/nnews/9048149.htm
- http://m.wap.fcful.cn/nnews/280895.htm
- http://m.wap.fcful.cn/nnews/6465867.htm
- http://m.wap.fcful.cn/nnews/299312.htm
- http://m.wap.fcful.cn/nnews/75988.htm
- http://m.wap.fcful.cn/nnews/892757.htm
- http://m.wap.fcful.cn/nnews/8620985.htm
- http://m.wap.fcful.cn/nnews/9157.htm
- http://m.wap.fcful.cn/nnews/6127.htm
- http://m.wap.fcful.cn/nnews/473209.htm
- http://m.wap.fcful.cn/nnews/2858.htm
- http://m.wap.fcful.cn/nnews/6076887.htm
- http://m.wap.fcful.cn/nnews/372748.htm
- http://m.wap.fcful.cn/nnews/3830.htm
- http://m.wap.fcful.cn/nnews/357301.htm
- http://m.wap.fcful.cn/nnews/1481335.htm
- http://m.wap.fcful.cn/nnews/1235954.htm
- http://m.wap.fcful.cn/nnews/228667.htm
- http://m.wap.fcful.cn/nnews/76651.htm
- http://m.wap.fcful.cn/nnews/531756.htm
- http://m.wap.fcful.cn/nnews/74304.htm
- http://m.wap.fcful.cn/nnews/79693.htm
- http://m.wap.fcful.cn/nnews/5800262.htm
- http://m.wap.fcful.cn/nnews/56194.htm
- http://m.wap.fcful.cn/nnews/0155318.htm
- http://m.wap.fcful.cn/nnews/317523.htm
- http://m.wap.fcful.cn/nnews/005163.htm
- http://m.wap.fcful.cn/nnews/446449.htm
- http://m.wap.fcful.cn/nnews/97752.htm
- http://m.wap.fcful.cn/nnews/7174298.htm
- http://m.wap.fcful.cn/nnews/711877.htm
- http://m.wap.fcful.cn/nnews/5860277.htm
- http://m.wap.fcful.cn/nnews/5843402.htm
- http://m.wap.fcful.cn/nnews/6068201.htm
- http://m.wap.fcful.cn/nnews/02081.htm
- http://m.wap.fcful.cn/nnews/50955.htm
- http://m.wap.fcful.cn/nnews/3081454.htm
- http://m.wap.fcful.cn/nnews/6028632.htm
- http://m.wap.fcful.cn/nnews/0279115.htm
- http://m.wap.fcful.cn/nnews/62643.htm
- http://m.wap.fcful.cn/nnews/1065131.htm
- http://m.wap.fcful.cn/nnews/3823587.htm
- http://m.wap.fcful.cn/nnews/528611.htm
- http://m.wap.fcful.cn/nnews/2097590.htm
- http://m.wap.fcful.cn/nnews/6310661.htm
- http://m.wap.fcful.cn/nnews/880018.htm
- http://m.wap.fcful.cn/nnews/6757.htm
- http://m.wap.fcful.cn/nnews/6536.htm
- http://m.wap.fcful.cn/nnews/9933.htm
- http://m.wap.fcful.cn/nnews/9185560.htm
- http://m.wap.fcful.cn/nnews/541198.htm
- http://m.wap.fcful.cn/nnews/17997.htm
- http://m.wap.fcful.cn/nnews/344887.htm
- http://m.wap.fcful.cn/nnews/860621.htm
- http://m.wap.fcful.cn/nnews/61093.htm
- http://m.wap.fcful.cn/nnews/385465.htm
- http://m.wap.fcful.cn/nnews/8530444.htm
- http://m.wap.fcful.cn/nnews/10452.htm
- http://m.wap.fcful.cn/nnews/784468.htm
- http://m.wap.fcful.cn/nnews/4037.htm
- http://m.wap.fcful.cn/nnews/463605.htm
- http://m.wap.fcful.cn/nnews/69865.htm
- http://m.wap.fcful.cn/nnews/28194.htm
- http://m.wap.fcful.cn/nnews/9068712.htm
- http://m.wap.fcful.cn/nnews/622500.htm
- http://m.wap.fcful.cn/nnews/277184.htm
- http://m.wap.fcful.cn/nnews/0015.htm
- http://m.wap.fcful.cn/nnews/913295.htm
- http://m.wap.fcful.cn/nnews/94699.htm
- http://m.wap.fcful.cn/nnews/244138.htm
- http://m.wap.fcful.cn/nnews/8495410.htm
- http://m.wap.fcful.cn/nnews/40452.htm
- http://m.wap.fcful.cn/nnews/7861.htm
- http://m.wap.fcful.cn/nnews/9975107.htm
- http://m.wap.fcful.cn/nnews/78539.htm
- http://m.wap.fcful.cn/nnews/277428.htm
- http://m.wap.fcful.cn/nnews/3236.htm
- http://m.wap.fcful.cn/nnews/3038.htm
- http://m.wap.fcful.cn/nnews/061697.htm
- http://m.wap.fcful.cn/nnews/0171.htm
- http://m.wap.fcful.cn/nnews/64850.htm
- http://m.wap.fcful.cn/nnews/146869.htm
- http://m.wap.fcful.cn/nnews/10804.htm
- http://m.wap.fcful.cn/nnews/672167.htm
- http://m.wap.fcful.cn/nnews/5877311.htm
- http://m.wap.fcful.cn/nnews/714188.htm
- http://m.wap.fcful.cn/nnews/1603253.htm
- http://m.wap.fcful.cn/nnews/9315864.htm
- http://m.wap.fcful.cn/nnews/5200.htm
- http://m.wap.fcful.cn/nnews/22528.htm
- http://m.wap.fcful.cn/nnews/7044.htm
- http://m.wap.fcful.cn/nnews/5067826.htm
- http://m.wap.fcful.cn/nnews/611583.htm
- http://m.wap.fcful.cn/nnews/58462.htm
- http://m.wap.fcful.cn/nnews/600075.htm
- http://m.wap.fcful.cn/nnews/9263727.htm
- http://m.wap.fcful.cn/nnews/30912.htm
- http://m.wap.fcful.cn/nnews/405053.htm
- http://m.wap.fcful.cn/nnews/2349.htm
- http://m.wap.fcful.cn/nnews/3859.htm
- http://m.wap.fcful.cn/nnews/608834.htm
- http://m.wap.fcful.cn/nnews/6852824.htm
- http://m.wap.fcful.cn/nnews/4924634.htm
- http://m.wap.fcful.cn/nnews/576729.htm
- http://m.wap.fcful.cn/nnews/0114.htm
- http://m.wap.fcful.cn/nnews/042701.htm
- http://m.wap.fcful.cn/nnews/485252.htm
- http://m.wap.fcful.cn/nnews/9214.htm
- http://m.wap.fcful.cn/nnews/39649.htm
- http://m.wap.fcful.cn/nnews/742155.htm
- http://m.wap.fcful.cn/nnews/0504121.htm
- http://m.wap.fcful.cn/nnews/47397.htm
- http://m.wap.fcful.cn/nnews/63180.htm
- http://m.wap.fcful.cn/nnews/720889.htm
- http://m.wap.fcful.cn/nnews/97242.htm
- http://m.wap.fcful.cn/nnews/43822.htm
- http://m.wap.fcful.cn/nnews/726903.htm
- http://m.wap.fcful.cn/nnews/5734489.htm
- http://m.wap.fcful.cn/nnews/20974.htm
- http://m.wap.fcful.cn/nnews/2300097.htm
- http://m.wap.fcful.cn/nnews/4393256.htm
- http://m.wap.fcful.cn/nnews/091401.htm
- http://m.wap.fcful.cn/nnews/17191.htm
- http://m.wap.fcful.cn/nnews/954772.htm
- http://m.wap.fcful.cn/nnews/653472.htm
- http://m.wap.fcful.cn/nnews/7445931.htm
- http://m.wap.fcful.cn/nnews/40790.htm
- http://m.wap.fcful.cn/nnews/433666.htm
- http://m.wap.fcful.cn/nnews/5109.htm
- http://m.wap.fcful.cn/nnews/7235.htm
- http://m.wap.fcful.cn/nnews/665352.htm
- http://m.wap.fcful.cn/nnews/25345.htm
- http://m.wap.fcful.cn/nnews/051735.htm
- http://m.wap.fcful.cn/nnews/12839.htm
- http://m.wap.fcful.cn/nnews/54545.htm
- http://m.wap.fcful.cn/nnews/4917.htm
- http://m.wap.fcful.cn/nnews/16985.htm
- http://m.wap.fcful.cn/nnews/6960.htm
- http://m.wap.fcful.cn/nnews/0513011.htm
- http://m.wap.fcful.cn/nnews/138704.htm
- http://m.wap.fcful.cn/nnews/37431.htm
- http://m.wap.fcful.cn/nnews/01955.htm
- http://m.wap.fcful.cn/nnews/822995.htm
- http://m.wap.fcful.cn/nnews/1494.htm
- http://m.wap.fcful.cn/nnews/516195.htm
- http://m.wap.fcful.cn/nnews/760322.htm
- http://m.wap.fcful.cn/nnews/5047681.htm
- http://m.wap.fcful.cn/nnews/81558.htm
- http://m.wap.fcful.cn/nnews/16516.htm
- http://m.wap.fcful.cn/nnews/186442.htm
- http://m.wap.fcful.cn/nnews/19499.htm
- http://m.wap.fcful.cn/nnews/14374.htm
- http://m.wap.fcful.cn/nnews/1714.htm
- http://m.wap.fcful.cn/nnews/90311.htm
- http://m.wap.fcful.cn/nnews/88490.htm
- http://m.wap.fcful.cn/nnews/923094.htm
- http://m.wap.fcful.cn/nnews/60354.htm
- http://m.wap.fcful.cn/nnews/00300.htm
- http://m.wap.fcful.cn/nnews/499300.htm
- http://m.wap.fcful.cn/nnews/7534.htm
- http://m.wap.fcful.cn/nnews/602663.htm
- http://m.wap.fcful.cn/nnews/545300.htm
- http://m.wap.fcful.cn/nnews/2692.htm
- http://m.wap.fcful.cn/nnews/99051.htm
- http://m.wap.fcful.cn/nnews/150651.htm
- http://m.wap.fcful.cn/nnews/422488.htm
- http://m.wap.fcful.cn/nnews/09348.htm
- http://m.wap.fcful.cn/nnews/89554.htm
- http://m.wap.fcful.cn/nnews/70238.htm
- http://m.wap.fcful.cn/nnews/3029870.htm
- http://m.wap.fcful.cn/nnews/150460.htm
- http://m.wap.fcful.cn/nnews/726025.htm
- http://m.wap.fcful.cn/nnews/0613.htm
- http://m.wap.fcful.cn/nnews/85637.htm
- http://m.wap.fcful.cn/nnews/9561380.htm
- http://m.wap.fcful.cn/nnews/78040.htm
- http://m.wap.fcful.cn/nnews/7333.htm
- http://m.wap.fcful.cn/nnews/6512957.htm
- http://m.wap.fcful.cn/nnews/98173.htm
- http://m.wap.fcful.cn/nnews/57351.htm
- http://m.wap.fcful.cn/nnews/4587.htm
- http://m.wap.fcful.cn/nnews/6994.htm
- http://m.wap.fcful.cn/nnews/8529.htm
- http://m.wap.fcful.cn/nnews/29071.htm
- http://m.wap.fcful.cn/nnews/892780.htm
- http://m.wap.fcful.cn/nnews/57653.htm
- http://m.wap.fcful.cn/nnews/574547.htm
- http://m.wap.fcful.cn/nnews/82388.htm
- http://m.wap.fcful.cn/nnews/96159.htm
- http://m.wap.fcful.cn/nnews/46479.htm
- http://m.wap.fcful.cn/nnews/3981.htm
- http://m.wap.fcful.cn/nnews/652682.htm
- http://m.wap.fcful.cn/nnews/298744.htm
- http://m.wap.fcful.cn/nnews/72451.htm
- http://m.wap.fcful.cn/nnews/7973.htm

## 项目结构

```
news-link-aggregator/
├── run_aggregator.py          # 命令行入口，解析参数并启动主流程
├── config/
│   ├── config.example.yaml    # 示例配置文件，含目标域名、深度、输出格式
│   └── user_agents.txt        # 随机UA池，用于请求头轮换
├── core/
│   ├── __init__.py
│   ├── fetcher.py             # 异步/同步HTTP请求封装，含重试与超时控制
│   ├── parser.py              # HTML解析器，基于BeautifulSoup实现链接提取
│   ├── filter.py              # 链接过滤器，支持正则、路径前缀、域名白名单
│   ├── deduplicator.py        # 基于URL归一化的去重处理器
│   └── exporter.py            # 结果导出器，支持JSONL、CSV、纯文本格式
├── storage/
│   ├── __init__.py
│   ├── indexer.py             # SQLite索引管理，创建表与执行增量更新
│   └── migrations/            # 数据库迁移脚本，按版本升级索引结构
├── utils/
│   ├── __init__.py
│   ├── logger.py              # 结构化日志配置，支持JSON格式输出
│   ├── validators.py          # URL合法性校验、端口与协议检查
│   └── time_utils.py          # 时间戳转换与任务ID生成
├── tests/
│   ├── unit/                  # 单元测试，覆盖解析器、过滤器与去重逻辑
│   ├── integration/           # 集成测试，以本地测试服务器验证完整流程
│   └── fixtures/              # 测试用HTML样本与期望输出
├── docs/
│   ├── user_guide.md          # 用户手册，含安装与配置详解
│   ├── developer_guide.md     # 开发指南，含插件扩展接口说明
│   ├── api_reference.md       # API文档，由docstring自动生成
│   └── operations.md          # 运维手册，含systemd服务配置与监控
├── scripts/
│   ├── setup_cron.sh          # 自动配置cron定时任务的辅助脚本
│   └── cleanup_old_logs.sh    # 清理过期日志与备份文件的运维脚本
├── requirements.txt           # 生产环境Python依赖列表
├── requirements-dev.txt       # 开发与测试环境额外依赖
├── setup.py                   # 项目打包与安装脚本
├── README.md                  # 本文档
└── LICENSE                    # MIT许可证文件
```

## 贡献指南

1. 阅读开发者指南 在提交代码前，请完整阅读docs/developer_guide.md，了解项目的模块划分、编码规范与测试要求。

2. 创建议题讨论 对于新增功能或较大规模的改动，请先在GitHub Issues中创建议题，说明设计思路与预期变更范围，等待维护者反馈后再开始编码。

3. 编写单元测试 所有新增或修改的代码必须包含对应的单元测试，测试文件放置在tests/unit/目录下，测试覆盖率不低于百分之八十。

4. 提交拉取请求 分支命名采用feature/xxx或fix/xxx格式，PR描述中需关联相关议题，并确保所有CI检查通过，包括代码风格检查与测试套件。

5. 更新文档 如果变更涉及用户可见的行为或配置项，请同步更新docs/下的对应文档，并在PR中明确标注文档变更部分。

## 常见问题

问：运行抓取时出现SSL证书验证错误，该如何处理？

答：部分移动端新闻站点可能使用过期或自签名证书。您可在配置文件或命令行参数中设置verify_ssl: false来跳过证书验证。但请注意，此操作存在中间人攻击风险，建议仅在可信网络环境中临时使用。生产环境请更新系统CA证书包。

问：链接提取结果中出现大量站外链接或广告追踪链接，如何过滤？

答：您可以通过配置文件中的link_filters字段添加域名白名单或路径正则表达式。例如，仅保留包含/nnews/路径的链接，可设置path_include: ['/nnews/']。此外，项目支持自定义过滤器插件，您可以在core/filter.py中扩展FilterChain类。

问：增量索引库持续增长，如何清理过期数据？

答：索引库位于storage/index.db，您可以通过运行scripts/cleanup_index.py --days 30来清理30天前的链接记录。若需完全重置索引，可直接删除该数据库文件，项目会在下次运行时自动重建表结构。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
