# WebLink Corpus Project

WebLink Corpus Project 是一个面向技术文档检索、外链监控与内容聚合场景的轻量级链接收集与整理工具。该项目定位于帮助开发者、技术内容运营人员以及信息分析研究者，以系统化的方式收集、分类、校验和导出分散于各类技术博客、新闻站点与公告页面中的外链资源。项目本身不生产内容，而是提供一套标准化的链接采集、去重、元数据提取与状态检测框架，使得用户能够从杂乱无章的页面集合中快速提炼出有价值的结构化链接清单。

目标用户包括需要定期追踪技术资讯的研发团队、负责外部资源引用的文档维护者、进行竞品动态监测的市场分析人员，以及从事网络信息结构研究的学术工作者。项目通过统一的数据接口与可扩展的规则引擎，显著降低大规模外链管理过程中的重复劳动与人工疏漏风险。


## 功能概览

批量链接提取：支持从给定的一组页面 URL 中自动提取所有超链接，并识别链接类型（内部链接、外部链接、资源文件链接、脚本链接等）。系统能够自动处理相对路径与绝对路径的转换，保证链接完整可用。

元数据自动补全：对每条提取出的链接，自动发起 HEAD 请求以获取响应状态码、内容类型、最后修改时间与内容长度等基础元数据，为后续筛选提供依据。

重复链接检测与去重：基于 URL 标准化算法与模糊匹配策略，对相同目标地址或指向同一规范 URL 的变体链接进行合并标记，避免统计时产生重复计数。

链接状态周期性巡检：支持用户自定义巡检周期，定期对已收录链接进行可访问性检查，输出失效链接报表，并提供快照对比功能以跟踪链接内容变更。

分类标签与自定义字段：允许用户为每条链接附加多个分类标签和自定义键值对注释，便于按主题、站点来源或业务用途进行多维筛选与分组。

数据导出接口：内置 CSV、JSON 与 Markdown 表格三种导出格式，并支持通过模板自定义导出字段顺序与样式，方便整合到技术文档、周报或外部系统中。

规则引擎与过滤管线：提供基于正则表达式与域名白名单/黑名单的过滤条件配置，用户可建立多级处理管线，在提取、清洗、输出各阶段分别应用不同规则。


## 应用场景

技术文档外链库构建：技术团队在编写产品文档或 API 参考手册时，需要引用大量外部标准、规范文档或社区讨论。使用本项目的批量提取与状态巡检功能，可维持一个长期有效的外链清单，避免文档中出现死链或过时引用，提升文档的专业可信度。

资讯聚合与竞争动态监测：市场分析人员可将竞品官网、技术公告栏与行业媒体作为种子页面，通过本项目定期提取新发布文章中的外部链接，结合标签分类与变更检测功能，快速定位竞品功能更新、版本发布或战略合作信息。

学术资源引用网络分析：研究人员在开展文献综述或技术趋势分析时，可从一批主题相关的技术新闻页面中提取所有参考文献链接，使用项目的元数据补全与分类标签功能构建小型引用网络，辅助识别高频引用资源与研究热点。


## 快速开始

以下指令演示了从代码仓库克隆项目、安装依赖并运行基础采集流程的完整步骤。

```bash
git clone https://github.com/weblink-corpus/weblink-corpus.git
cd weblink-corpus
pip install -r requirements.txt
cp config.example.yaml config.yaml
python cli.py collect --input seeds.txt --output result.json
```

执行上述命令后，系统将读取 seeds.txt 中的种子页面地址，完成链接提取、去重与基础元数据采集，最终将结果写入 result.json 文件。用户可通过修改 config.yaml 调整请求超时时间、并发数、过滤规则等参数。


## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时环境，用于执行采集脚本与规则引擎 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与响应，用于页面获取和链接状态检测 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 页面结构，提取链接与文本内容 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析后端，提供高性能 XML/HTML 解析 |
| pyyaml | 6.0 及以上 | 读写 YAML 格式的配置文件与规则定义 |
| pytest | 7.0 及以上 | 单元测试框架，仅在开发环境中需要 |


## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何安装、配置并运行第一次采集任务；种子文件与输出格式如何选择 |
| 规则编写 | docs/rules_engine.md | 过滤管线的语法规则如何定义；白名单与黑名单如何组合使用 |
| 元数据字段 | docs/metadata_spec.md | 每条链接记录包含哪些字段；自定义字段如何添加与映射 |
| 巡检与告警 | docs/health_check.md | 链接状态巡检如何配置周期；失效告警的通知方式与输出模板 |


## 资源列表

- http://m.blog.fcful.cn/bnews/155242.htm
- http://m.blog.fcful.cn/bnews/70463.htm
- http://m.blog.fcful.cn/bnews/22764.htm
- http://m.blog.fcful.cn/bnews/6963.htm
- http://m.blog.fcful.cn/bnews/633288.htm
- http://m.blog.fcful.cn/bnews/8512639.htm
- http://m.blog.fcful.cn/bnews/75474.htm
- http://m.blog.fcful.cn/bnews/95225.htm
- http://m.blog.fcful.cn/bnews/75956.htm
- http://m.blog.fcful.cn/bnews/95015.htm
- http://m.blog.fcful.cn/bnews/58754.htm
- http://m.blog.fcful.cn/bnews/899293.htm
- http://m.blog.fcful.cn/bnews/0401438.htm
- http://m.blog.fcful.cn/bnews/7365251.htm
- http://m.blog.fcful.cn/bnews/45781.htm
- http://m.blog.fcful.cn/bnews/31637.htm
- http://m.blog.fcful.cn/bnews/99866.htm
- http://m.blog.fcful.cn/bnews/68079.htm
- http://m.blog.fcful.cn/bnews/313484.htm
- http://m.blog.fcful.cn/bnews/893259.htm
- http://m.blog.fcful.cn/bnews/844378.htm
- http://m.blog.fcful.cn/bnews/658268.htm
- http://m.blog.fcful.cn/bnews/58179.htm
- http://m.blog.fcful.cn/bnews/0378.htm
- http://m.blog.fcful.cn/bnews/5772660.htm
- http://m.blog.fcful.cn/bnews/20893.htm
- http://m.blog.fcful.cn/bnews/704414.htm
- http://m.blog.fcful.cn/bnews/62312.htm
- http://m.blog.fcful.cn/bnews/1653181.htm
- http://m.blog.fcful.cn/bnews/0052694.htm
- http://m.blog.fcful.cn/bnews/805749.htm
- http://m.blog.fcful.cn/bnews/7705067.htm
- http://m.blog.fcful.cn/bnews/06072.htm
- http://m.blog.fcful.cn/bnews/692496.htm
- http://m.blog.fcful.cn/bnews/791823.htm
- http://m.blog.fcful.cn/bnews/3739.htm
- http://m.blog.fcful.cn/bnews/5746.htm
- http://m.blog.fcful.cn/bnews/3774.htm
- http://m.blog.fcful.cn/bnews/20373.htm
- http://m.blog.fcful.cn/bnews/0290.htm
- http://m.blog.fcful.cn/bnews/96749.htm
- http://m.blog.fcful.cn/bnews/06990.htm
- http://m.blog.fcful.cn/bnews/51665.htm
- http://m.blog.fcful.cn/bnews/8122534.htm
- http://m.blog.fcful.cn/bnews/2465094.htm
- http://m.blog.fcful.cn/bnews/2979447.htm
- http://m.blog.fcful.cn/bnews/535058.htm
- http://m.blog.fcful.cn/bnews/67660.htm
- http://m.blog.fcful.cn/bnews/784023.htm
- http://m.blog.fcful.cn/bnews/0302938.htm
- http://m.blog.fcful.cn/bnews/7956986.htm
- http://m.blog.fcful.cn/bnews/3238498.htm
- http://m.blog.fcful.cn/bnews/55277.htm
- http://m.blog.fcful.cn/bnews/2938484.htm
- http://m.blog.fcful.cn/bnews/700432.htm
- http://m.blog.fcful.cn/bnews/5170057.htm
- http://m.blog.fcful.cn/bnews/236178.htm
- http://m.blog.fcful.cn/bnews/18657.htm
- http://m.blog.fcful.cn/bnews/2566.htm
- http://m.blog.fcful.cn/bnews/12060.htm
- http://m.blog.fcful.cn/bnews/9386073.htm
- http://m.blog.fcful.cn/bnews/62016.htm
- http://m.blog.fcful.cn/bnews/974469.htm
- http://m.blog.fcful.cn/bnews/08323.htm
- http://m.blog.fcful.cn/bnews/1985638.htm
- http://m.blog.fcful.cn/bnews/3838885.htm
- http://m.blog.fcful.cn/bnews/4273.htm
- http://m.blog.fcful.cn/bnews/45082.htm
- http://m.blog.fcful.cn/bnews/4670869.htm
- http://m.blog.fcful.cn/bnews/99182.htm
- http://m.blog.fcful.cn/bnews/271729.htm
- http://m.blog.fcful.cn/bnews/1407009.htm
- http://m.blog.fcful.cn/bnews/557771.htm
- http://m.blog.fcful.cn/bnews/10325.htm
- http://m.blog.fcful.cn/bnews/905324.htm
- http://m.blog.fcful.cn/bnews/1345997.htm
- http://m.blog.fcful.cn/bnews/20237.htm
- http://m.blog.fcful.cn/bnews/3468811.htm
- http://m.blog.fcful.cn/bnews/7359347.htm
- http://m.blog.fcful.cn/bnews/3802.htm
- http://m.blog.fcful.cn/bnews/3445.htm
- http://m.blog.fcful.cn/bnews/5638313.htm
- http://m.blog.fcful.cn/bnews/89505.htm
- http://m.blog.fcful.cn/bnews/163999.htm
- http://m.blog.fcful.cn/bnews/493042.htm
- http://m.blog.fcful.cn/bnews/3170.htm
- http://m.blog.fcful.cn/bnews/60089.htm
- http://m.blog.fcful.cn/bnews/476310.htm
- http://m.blog.fcful.cn/bnews/503205.htm
- http://m.blog.fcful.cn/bnews/1652670.htm
- http://m.blog.fcful.cn/bnews/7903105.htm
- http://m.blog.fcful.cn/bnews/4354984.htm
- http://m.blog.fcful.cn/bnews/70687.htm
- http://m.blog.fcful.cn/bnews/23900.htm
- http://m.blog.fcful.cn/bnews/2593.htm
- http://m.blog.fcful.cn/bnews/1963.htm
- http://m.blog.fcful.cn/bnews/8085433.htm
- http://m.blog.fcful.cn/bnews/6528171.htm
- http://m.blog.fcful.cn/bnews/42892.htm
- http://m.blog.fcful.cn/bnews/4476.htm
- http://m.blog.fcful.cn/bnews/3987.htm
- http://m.blog.fcful.cn/bnews/022369.htm
- http://m.blog.fcful.cn/bnews/12876.htm
- http://m.blog.fcful.cn/bnews/52024.htm
- http://m.blog.fcful.cn/bnews/1531.htm
- http://m.blog.fcful.cn/bnews/45682.htm
- http://m.blog.fcful.cn/bnews/7112234.htm
- http://m.blog.fcful.cn/bnews/5966201.htm
- http://m.blog.fcful.cn/bnews/613754.htm
- http://m.blog.fcful.cn/bnews/678680.htm
- http://m.blog.fcful.cn/bnews/45952.htm
- http://m.blog.fcful.cn/bnews/79831.htm
- http://m.blog.fcful.cn/bnews/73896.htm
- http://m.blog.fcful.cn/bnews/451460.htm
- http://m.blog.fcful.cn/bnews/209570.htm
- http://m.blog.fcful.cn/bnews/7930974.htm
- http://m.blog.fcful.cn/bnews/07009.htm
- http://m.blog.fcful.cn/bnews/9509.htm
- http://m.blog.fcful.cn/bnews/84891.htm
- http://m.blog.fcful.cn/bnews/959793.htm
- http://m.blog.fcful.cn/bnews/542965.htm
- http://m.blog.fcful.cn/bnews/166927.htm
- http://m.blog.fcful.cn/bnews/4947.htm
- http://m.blog.fcful.cn/bnews/633302.htm
- http://m.blog.fcful.cn/bnews/15330.htm
- http://m.blog.fcful.cn/bnews/6978.htm
- http://m.blog.fcful.cn/bnews/436203.htm
- http://m.blog.fcful.cn/bnews/36423.htm
- http://m.blog.fcful.cn/bnews/0544.htm
- http://m.blog.fcful.cn/bnews/488311.htm
- http://m.blog.fcful.cn/bnews/18416.htm
- http://m.blog.fcful.cn/bnews/544645.htm
- http://m.blog.fcful.cn/bnews/81533.htm
- http://m.blog.fcful.cn/bnews/0278416.htm
- http://m.blog.fcful.cn/bnews/9440.htm
- http://m.blog.fcful.cn/bnews/754145.htm
- http://m.blog.fcful.cn/bnews/60918.htm
- http://m.blog.fcful.cn/bnews/182369.htm
- http://m.blog.fcful.cn/bnews/1215.htm
- http://m.blog.fcful.cn/bnews/3310689.htm
- http://m.blog.fcful.cn/bnews/0044.htm
- http://m.blog.fcful.cn/bnews/924346.htm
- http://m.blog.fcful.cn/bnews/730270.htm
- http://m.blog.fcful.cn/bnews/8607.htm
- http://m.blog.fcful.cn/bnews/6443.htm
- http://m.blog.fcful.cn/bnews/73499.htm
- http://m.blog.fcful.cn/bnews/651471.htm
- http://m.blog.fcful.cn/bnews/1642178.htm
- http://m.blog.fcful.cn/bnews/7481910.htm
- http://m.blog.fcful.cn/bnews/6909.htm
- http://m.blog.fcful.cn/bnews/6920.htm
- http://m.blog.fcful.cn/bnews/7346.htm
- http://m.blog.fcful.cn/bnews/3931696.htm
- http://m.blog.fcful.cn/bnews/785836.htm
- http://m.blog.fcful.cn/bnews/029338.htm
- http://m.blog.fcful.cn/bnews/9428.htm
- http://m.blog.fcful.cn/bnews/70373.htm
- http://m.blog.fcful.cn/bnews/584779.htm
- http://m.blog.fcful.cn/bnews/0207.htm
- http://m.blog.fcful.cn/bnews/2201607.htm
- http://m.blog.fcful.cn/bnews/69687.htm
- http://m.blog.fcful.cn/bnews/769234.htm
- http://m.blog.fcful.cn/bnews/24246.htm
- http://m.blog.fcful.cn/bnews/0574206.htm
- http://m.blog.fcful.cn/bnews/911256.htm
- http://m.blog.fcful.cn/bnews/5871526.htm
- http://m.blog.fcful.cn/bnews/3183728.htm
- http://m.blog.fcful.cn/bnews/6872517.htm
- http://m.blog.fcful.cn/bnews/515559.htm
- http://m.blog.fcful.cn/bnews/749293.htm
- http://m.blog.fcful.cn/bnews/521912.htm
- http://m.blog.fcful.cn/bnews/767334.htm
- http://m.blog.fcful.cn/bnews/9320.htm
- http://m.blog.fcful.cn/bnews/875873.htm
- http://m.blog.fcful.cn/bnews/8482.htm
- http://m.blog.fcful.cn/bnews/872689.htm
- http://m.blog.fcful.cn/bnews/8372293.htm
- http://m.blog.fcful.cn/bnews/7357321.htm
- http://m.blog.fcful.cn/bnews/04012.htm
- http://m.blog.fcful.cn/bnews/32071.htm
- http://m.blog.fcful.cn/bnews/8524308.htm
- http://m.blog.fcful.cn/bnews/837053.htm
- http://m.blog.fcful.cn/bnews/21404.htm
- http://m.blog.fcful.cn/bnews/16219.htm
- http://m.blog.fcful.cn/bnews/39988.htm
- http://m.blog.fcful.cn/bnews/94254.htm
- http://m.blog.fcful.cn/bnews/83539.htm
- http://m.blog.fcful.cn/bnews/004457.htm
- http://m.blog.fcful.cn/bnews/1891602.htm
- http://m.blog.fcful.cn/bnews/256672.htm
- http://m.blog.fcful.cn/bnews/5182.htm
- http://m.blog.fcful.cn/bnews/06108.htm
- http://m.blog.fcful.cn/bnews/8765703.htm
- http://m.blog.fcful.cn/bnews/78144.htm
- http://m.blog.fcful.cn/bnews/728593.htm
- http://m.blog.fcful.cn/bnews/2473504.htm
- http://m.blog.fcful.cn/bnews/2078150.htm
- http://m.blog.fcful.cn/bnews/3417.htm
- http://m.blog.fcful.cn/bnews/62902.htm
- http://m.blog.fcful.cn/bnews/8673327.htm
- http://m.blog.fcful.cn/bnews/6389912.htm
- http://m.blog.fcful.cn/bnews/423790.htm
- http://m.blog.fcful.cn/bnews/6431603.htm
- http://m.blog.fcful.cn/bnews/1487165.htm
- http://m.blog.fcful.cn/bnews/9031108.htm
- http://m.blog.fcful.cn/bnews/7060735.htm
- http://m.blog.fcful.cn/bnews/7099047.htm
- http://m.blog.fcful.cn/bnews/32957.htm
- http://m.blog.fcful.cn/bnews/2420159.htm
- http://m.blog.fcful.cn/bnews/9490909.htm
- http://m.blog.fcful.cn/bnews/090146.htm
- http://m.blog.fcful.cn/bnews/950478.htm
- http://m.blog.fcful.cn/bnews/4863.htm
- http://m.blog.fcful.cn/bnews/387664.htm
- http://m.blog.fcful.cn/bnews/4718414.htm
- http://m.blog.fcful.cn/bnews/046787.htm
- http://m.blog.fcful.cn/bnews/3999.htm
- http://m.blog.fcful.cn/bnews/18708.htm
- http://m.blog.fcful.cn/bnews/9718073.htm
- http://m.blog.fcful.cn/bnews/6811.htm
- http://m.blog.fcful.cn/bnews/694898.htm
- http://m.blog.fcful.cn/bnews/3086.htm
- http://m.blog.fcful.cn/bnews/3840.htm
- http://m.blog.fcful.cn/bnews/309468.htm
- http://m.blog.fcful.cn/bnews/3399563.htm
- http://m.blog.fcful.cn/bnews/52248.htm
- http://m.blog.fcful.cn/bnews/6581544.htm
- http://m.blog.fcful.cn/bnews/1368.htm
- http://m.blog.fcful.cn/bnews/768573.htm
- http://m.blog.fcful.cn/bnews/17577.htm
- http://m.blog.fcful.cn/bnews/241351.htm
- http://m.blog.fcful.cn/bnews/6889.htm
- http://m.blog.fcful.cn/bnews/0765705.htm
- http://m.blog.fcful.cn/bnews/7564408.htm
- http://m.blog.fcful.cn/bnews/17348.htm
- http://m.blog.fcful.cn/bnews/03019.htm
- http://m.blog.fcful.cn/bnews/61922.htm
- http://m.blog.fcful.cn/bnews/2165.htm
- http://m.blog.fcful.cn/bnews/1959742.htm
- http://m.blog.fcful.cn/bnews/753062.htm
- http://m.blog.fcful.cn/bnews/0880.htm
- http://m.blog.fcful.cn/bnews/05444.htm
- http://m.blog.fcful.cn/bnews/446290.htm
- http://m.blog.fcful.cn/bnews/2613.htm
- http://m.blog.fcful.cn/bnews/35608.htm
- http://m.blog.fcful.cn/bnews/9251625.htm
- http://m.blog.fcful.cn/bnews/0848460.htm
- http://m.blog.fcful.cn/bnews/72804.htm
- http://m.blog.fcful.cn/bnews/5185054.htm
- http://m.blog.fcful.cn/bnews/8406.htm

## 项目结构

```
weblink-corpus/
├── cli.py                      # 命令行入口，注册 collect、check、export 等子命令
├── config.yaml                 # 主配置文件，包含并发数、超时、重试策略等全局参数
├── seeds.txt                   # 种子页面列表，每行一个 URL，供采集命令读取
├── requirements.txt            # Python 依赖声明，固定版本范围以保证环境一致性
├── src/                        # 核心源代码目录
│   ├── collector/              # 链接采集模块，负责页面抓取与链接解析
│   │   ├── fetcher.py          # 封装 requests 与重试逻辑，返回页面原始 HTML
│   │   ├── parser.py           # 使用 beautifulsoup4 解析 HTML，提取 href 并规范化
│   │   └── pipeline.py         # 协调抓取与解析流程，管理并发任务队列
│   ├── rules/                  # 规则引擎模块，实现过滤与标签逻辑
│   │   ├── loader.py           # 从 YAML 文件加载过滤规则与白名单配置
│   │   ├── matcher.py          # 执行正则匹配与域名匹配，返回是否通过过滤
│   │   └── context.py          # 维护规则执行过程中的上下文状态与统计计数器
│   ├── metadata/               # 元数据补全与状态检测模块
│   │   ├── head_client.py      # 发送 HEAD 请求获取状态码与响应头信息
│   │   ├── enricher.py         # 将元数据字段合并到链接记录中
│   │   └── health.py           # 周期性巡检逻辑，检测失效链接并生成报表
│   ├── exporters/              # 数据导出模块
│   │   ├── json_exporter.py    # 输出 JSON 格式结果，保留全部字段
│   │   ├── csv_exporter.py     # 输出 CSV 表格，可配置列顺序
│   │   └── markdown_exporter.py # 输出 Markdown 表格，适用于文档嵌入
│   └── utils/                  # 通用工具函数
│       ├── url_utils.py        # URL 标准化、域名提取、路径拼接等操作
│       ├── hash_utils.py       # 计算链接去重所用的摘要指纹
│       └── logger.py           # 统一日志格式，支持文件与控制台双输出
├── tests/                      # 单元测试目录，使用 pytest 框架
│   ├── test_parser.py          # 测试链接提取与规范化逻辑
│   ├── test_matcher.py         # 测试规则匹配与过滤条件
│   └── test_enricher.py        # 测试元数据补全与字段合并
├── docs/                       # 文档目录，包含入门指南与各模块详细说明
│   ├── getting_started.md
│   ├── rules_engine.md
│   ├── metadata_spec.md
│   └── health_check.md
└── LICENSE                     # MIT 许可证文件
```


## 贡献指南

提交问题报告与功能请求：请使用 GitHub Issues 提交 bug 描述或新功能建议。报告 bug 时需提供完整的错误日志、配置文件内容以及可复现的种子链接样例。功能请求请说明使用场景与期望的行为变化。

代码贡献流程：从主仓库 fork 个人副本，在 dev 分支上创建特性分支进行开发。提交代码前需运行 pytest 确保所有已有测试通过，并为新增功能补充对应的测试用例。完成开发后向主仓库的 dev 分支发起 Pull Request，描述中需列出变更摘要、测试结果与相关文档更新。

文档完善与翻译：欢迎对项目文档进行勘误、补充示例或提供英文版本翻译。文档修改可直接编辑 docs 目录下的 Markdown 文件，提交 Pull Request 时请注明文档变更的范围与目的。


## 常见问题

系统在采集大量页面时出现超时或连接中断应如何处理？

建议调整 config.yaml 中的并发数（concurrency）为较小值，如 4 或 2，同时增大单次请求超时时间（timeout）至 30 秒或 60 秒。对于持续失败的链接，系统会自动记录并跳过，用户可在日志文件中查看失败详情，后续通过单独重跑命令进行补偿采集。

如何对已导出的链接清单进行增量更新而不重复采集已有链接？

项目默认启用增量模式，系统会在本地缓存目录中保存已采集链接的指纹。再次运行采集命令时，会自动跳过指纹匹配的链接。如需强制全量重新采集，可在命令行中添加 --force 参数。

规则引擎中的黑白名单同时匹配某条链接时以哪个为准？

规则引擎的优先级为黑名单高于白名单。当一条链接同时匹配黑名单与白名单规则时，系统判定为不通过，该链接将被过滤掉，不会进入最终结果集。建议用户谨慎设计规则组合，避免无意中排除期望保留的链接。


## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:44
