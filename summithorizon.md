# NewsLink Navigator

NewsLink Navigator 是一个面向移动端资讯聚合与深度链接导航的开源工具集，专注于将分散于移动网页端的新闻条目、信息页面与外部资源进行结构化整理与快速访问。该项目主要为内容研究者、舆情监测人员、移动端产品运营者以及个人知识管理爱好者提供一套轻量级、可定制的新闻链接提取与浏览解决方案。

项目核心定位为“移动新闻链接的索引中间层”，通过解析特定的新闻详情页 URL 模式，自动抓取页面标题、发布时间、正文摘要与分类标签，并生成可供二次处理的 JSON 或 CSV 数据流。用户可通过该项目快速构建自己的新闻简报系统、舆情监控看板或研究资料库，无需反复手动打开数十个零散的移动端页面。

## 功能概览

**批量链接解析与元数据提取**：自动识别并解析指定域名下的新闻详情页链接，从 HTML 结构中提取标题、发布日期、正文预览、来源等关键元数据，支持断点续抓与失败重试机制。

**分类标签自动推断**：基于 URL 路径特征、页面关键词密度与预设规则库，对每条新闻链接自动打上分类标签，如科技、财经、社会、体育、娱乐等，便于后续筛选与聚合。

**数据导出与 API 接口**：支持将解析结果导出为 JSON、CSV 或 Markdown 表格格式，同时提供内置的 HTTP API 服务，允许第三方应用通过 RESTful 接口调用解析能力。

**移动端自适应浏览视图**：内置一个轻量级的移动端适配页面，将解析后的链接列表以卡片流形式展示，支持按时间、分类、热度排序，方便在手机浏览器上直接查阅。

**链接状态健康检查**：定期对已收录的链接进行可用性探测，自动标记失效链接、重定向链接与响应缓慢链接，帮助用户维护一个健康的资源列表。

**自定义规则引擎**：允许高级用户通过 YAML 配置文件自定义页面解析规则，包括 CSS 选择器、正则表达式提取规则与字段映射关系，以适配不同站点结构的变化。

**书签与收藏管理**：用户可以对特定的新闻链接添加书签、备注标签与收藏标记，形成个人关注列表，并支持导入导出收藏数据。

## 应用场景

舆情监测与品牌追踪：市场公关人员可利用本工具批量抓取特定时间段内关于本品牌或竞品的新闻报道链接，快速汇总标题与摘要，生成每日舆情简报，大幅减少手动搜集与整理的时间。

行业研究与竞品分析：咨询分析师或行业研究员可将项目部署为内部工具，定期拉取特定行业分类下的新闻链接，构建行业动态数据库，结合导出功能进行词频分析与趋势研判。

个人知识库构建与信息沉淀：知识管理爱好者可将项目与个人笔记软件或知识库工具结合，通过 API 自动将感兴趣的新闻链接及其元数据归档至本地或云端，建立个人专属的新闻档案库。

内容聚合站与导航页运维：小型内容站点或导航页的运维人员可利用项目内置的导出功能，将经过筛选和分类的链接列表自动生成 HTML 导航代码或 Markdown 资源清单，减少手动更新维护成本。

## 快速开始

```bash
# 克隆项目仓库至本地
git clone https://github.com/newsnav/navigator.git

# 进入项目根目录
cd navigator

# 安装项目依赖（使用 pip 安装 Python 依赖包）
pip install -r requirements.txt

# 运行示例解析任务，解析 resources/sample_links.txt 中的链接列表
python cli.py parse --input resources/sample_links.txt --output result.json

# 启动本地 API 服务（默认监听 127.0.0.1:5000）
python app.py
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 项目核心运行环境，用于执行解析引擎与 API 服务 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 请求获取页面 HTML 内容 |
| beautifulsoup4 | 4.12.0 及以上 | 用于解析 HTML 文档结构，提取元数据 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析器后端，提升解析性能 |
| flask | 2.2.0 及以上 | 用于提供内置的 RESTful API 服务接口 |
| pytest | 7.0.0 及以上 | 单元测试框架，仅在开发与测试环境中需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何安装部署、配置解析规则、运行批量任务以及导出数据？ |
| API 参考 | docs/api_reference.md | RESTful API 的完整端点列表、请求参数格式与响应结构定义？ |
| 规则配置 | docs/rule_config.md | 如何编写 YAML 自定义规则文件以适配新的站点或页面结构？ |
| 贡献规范 | docs/contributing.md | 如何提交代码、报告缺陷、完善文档以及参与项目路线图讨论？ |

## 资源列表

- http://m.wap.fcful.cn/nnews/1500976.htm
- http://m.wap.fcful.cn/nnews/6106.htm
- http://m.wap.fcful.cn/nnews/311985.htm
- http://m.wap.fcful.cn/nnews/7169928.htm
- http://m.wap.fcful.cn/nnews/754830.htm
- http://m.wap.fcful.cn/nnews/0358.htm
- http://m.wap.fcful.cn/nnews/5169980.htm
- http://m.wap.fcful.cn/nnews/7597421.htm
- http://m.wap.fcful.cn/nnews/2799560.htm
- http://m.wap.fcful.cn/nnews/9092036.htm
- http://m.wap.fcful.cn/nnews/3644213.htm
- http://m.wap.fcful.cn/nnews/514979.htm
- http://m.wap.fcful.cn/nnews/013233.htm
- http://m.wap.fcful.cn/nnews/229403.htm
- http://m.wap.fcful.cn/nnews/1536394.htm
- http://m.wap.fcful.cn/nnews/500418.htm
- http://m.wap.fcful.cn/nnews/259702.htm
- http://m.wap.fcful.cn/nnews/69847.htm
- http://m.wap.fcful.cn/nnews/9908.htm
- http://m.wap.fcful.cn/nnews/722860.htm
- http://m.wap.fcful.cn/nnews/59052.htm
- http://m.wap.fcful.cn/nnews/2149029.htm
- http://m.wap.fcful.cn/nnews/2362778.htm
- http://m.wap.fcful.cn/nnews/1280751.htm
- http://m.wap.fcful.cn/nnews/658930.htm
- http://m.wap.fcful.cn/nnews/9663347.htm
- http://m.wap.fcful.cn/nnews/822799.htm
- http://m.wap.fcful.cn/nnews/17648.htm
- http://m.wap.fcful.cn/nnews/365655.htm
- http://m.wap.fcful.cn/nnews/8043.htm
- http://m.wap.fcful.cn/nnews/9517.htm
- http://m.wap.fcful.cn/nnews/21538.htm
- http://m.wap.fcful.cn/nnews/804421.htm
- http://m.wap.fcful.cn/nnews/727202.htm
- http://m.wap.fcful.cn/nnews/0248291.htm
- http://m.wap.fcful.cn/nnews/7790912.htm
- http://m.wap.fcful.cn/nnews/678762.htm
- http://m.wap.fcful.cn/nnews/37630.htm
- http://m.wap.fcful.cn/nnews/06054.htm
- http://m.wap.fcful.cn/nnews/812636.htm
- http://m.wap.fcful.cn/nnews/01809.htm
- http://m.wap.fcful.cn/nnews/9005.htm
- http://m.wap.fcful.cn/nnews/3643743.htm
- http://m.wap.fcful.cn/nnews/0052952.htm
- http://m.wap.fcful.cn/nnews/95511.htm
- http://m.wap.fcful.cn/nnews/3632282.htm
- http://m.wap.fcful.cn/nnews/607146.htm
- http://m.wap.fcful.cn/nnews/67250.htm
- http://m.wap.fcful.cn/nnews/88162.htm
- http://m.wap.fcful.cn/nnews/9784266.htm
- http://m.wap.fcful.cn/nnews/38511.htm
- http://m.wap.fcful.cn/nnews/75650.htm
- http://m.wap.fcful.cn/nnews/2109034.htm
- http://m.wap.fcful.cn/nnews/564707.htm
- http://m.wap.fcful.cn/nnews/8547559.htm
- http://m.wap.fcful.cn/nnews/912828.htm
- http://m.wap.fcful.cn/nnews/10772.htm
- http://m.wap.fcful.cn/nnews/4351.htm
- http://m.wap.fcful.cn/nnews/1848845.htm
- http://m.wap.fcful.cn/nnews/73670.htm
- http://m.wap.fcful.cn/nnews/7372929.htm
- http://m.wap.fcful.cn/nnews/659296.htm
- http://m.wap.fcful.cn/nnews/19952.htm
- http://m.wap.fcful.cn/nnews/9336789.htm
- http://m.wap.fcful.cn/nnews/8520581.htm
- http://m.wap.fcful.cn/nnews/3295.htm
- http://m.wap.fcful.cn/nnews/7360077.htm
- http://m.wap.fcful.cn/nnews/3106942.htm
- http://m.wap.fcful.cn/nnews/56103.htm
- http://m.wap.fcful.cn/nnews/6957360.htm
- http://m.wap.fcful.cn/nnews/90066.htm
- http://m.wap.fcful.cn/nnews/49669.htm
- http://m.wap.fcful.cn/nnews/0090.htm
- http://m.wap.fcful.cn/nnews/16667.htm
- http://m.wap.fcful.cn/nnews/182355.htm
- http://m.wap.fcful.cn/nnews/5415.htm
- http://m.wap.fcful.cn/nnews/0498473.htm
- http://m.wap.fcful.cn/nnews/512431.htm
- http://m.wap.fcful.cn/nnews/82469.htm
- http://m.wap.fcful.cn/nnews/4368957.htm
- http://m.wap.fcful.cn/nnews/7334.htm
- http://m.wap.fcful.cn/nnews/98114.htm
- http://m.wap.fcful.cn/nnews/051636.htm
- http://m.wap.fcful.cn/nnews/0476480.htm
- http://m.wap.fcful.cn/nnews/09659.htm
- http://m.wap.fcful.cn/nnews/4191346.htm
- http://m.wap.fcful.cn/nnews/686152.htm
- http://m.wap.fcful.cn/nnews/5156672.htm
- http://m.wap.fcful.cn/nnews/5510.htm
- http://m.wap.fcful.cn/nnews/688536.htm
- http://m.wap.fcful.cn/nnews/28803.htm
- http://m.wap.fcful.cn/nnews/9470.htm
- http://m.wap.fcful.cn/nnews/1004.htm
- http://m.wap.fcful.cn/nnews/3645498.htm
- http://m.wap.fcful.cn/nnews/471383.htm
- http://m.wap.fcful.cn/nnews/780155.htm
- http://m.wap.fcful.cn/nnews/9204791.htm
- http://m.wap.fcful.cn/nnews/3083633.htm
- http://m.wap.fcful.cn/nnews/5634311.htm
- http://m.wap.fcful.cn/nnews/30853.htm
- http://m.wap.fcful.cn/nnews/8306351.htm
- http://m.wap.fcful.cn/nnews/369077.htm
- http://m.wap.fcful.cn/nnews/64509.htm
- http://m.wap.fcful.cn/nnews/3991394.htm
- http://m.wap.fcful.cn/nnews/7494.htm
- http://m.wap.fcful.cn/nnews/35630.htm
- http://m.wap.fcful.cn/nnews/767225.htm
- http://m.wap.fcful.cn/nnews/8970172.htm
- http://m.wap.fcful.cn/nnews/2828.htm
- http://m.wap.fcful.cn/nnews/5339.htm
- http://m.wap.fcful.cn/nnews/1230576.htm
- http://m.wap.fcful.cn/nnews/53242.htm
- http://m.wap.fcful.cn/nnews/5483538.htm
- http://m.wap.fcful.cn/nnews/9625379.htm
- http://m.wap.fcful.cn/nnews/035083.htm
- http://m.wap.fcful.cn/nnews/50188.htm
- http://m.wap.fcful.cn/nnews/5431.htm
- http://m.wap.fcful.cn/nnews/2449.htm
- http://m.wap.fcful.cn/nnews/8565447.htm
- http://m.wap.fcful.cn/nnews/760243.htm
- http://m.wap.fcful.cn/nnews/84312.htm
- http://m.wap.fcful.cn/nnews/49625.htm
- http://m.wap.fcful.cn/nnews/9356.htm
- http://m.wap.fcful.cn/nnews/1630654.htm
- http://m.wap.fcful.cn/nnews/20729.htm
- http://m.wap.fcful.cn/nnews/330828.htm
- http://m.wap.fcful.cn/nnews/4513863.htm
- http://m.wap.fcful.cn/nnews/2961853.htm
- http://m.wap.fcful.cn/nnews/6381.htm
- http://m.wap.fcful.cn/nnews/7931269.htm
- http://m.wap.fcful.cn/nnews/2868.htm
- http://m.wap.fcful.cn/nnews/31747.htm
- http://m.wap.fcful.cn/nnews/0299914.htm
- http://m.wap.fcful.cn/nnews/38152.htm
- http://m.wap.fcful.cn/nnews/987734.htm
- http://m.wap.fcful.cn/nnews/242550.htm
- http://m.wap.fcful.cn/nnews/4550768.htm
- http://m.wap.fcful.cn/nnews/45233.htm
- http://m.wap.fcful.cn/nnews/777269.htm
- http://m.wap.fcful.cn/nnews/83154.htm
- http://m.wap.fcful.cn/nnews/819353.htm
- http://m.wap.fcful.cn/nnews/0552083.htm
- http://m.wap.fcful.cn/nnews/30798.htm
- http://m.wap.fcful.cn/nnews/8016408.htm
- http://m.wap.fcful.cn/nnews/9347770.htm
- http://m.wap.fcful.cn/nnews/536104.htm
- http://m.wap.fcful.cn/nnews/0568.htm
- http://m.wap.fcful.cn/nnews/02903.htm
- http://m.wap.fcful.cn/nnews/21594.htm
- http://m.wap.fcful.cn/nnews/0927461.htm
- http://m.wap.fcful.cn/nnews/1230757.htm
- http://m.wap.fcful.cn/nnews/2352923.htm
- http://m.wap.fcful.cn/nnews/0341074.htm
- http://m.wap.fcful.cn/nnews/93630.htm
- http://m.wap.fcful.cn/nnews/6543458.htm
- http://m.wap.fcful.cn/nnews/9531913.htm
- http://m.wap.fcful.cn/nnews/6718378.htm
- http://m.wap.fcful.cn/nnews/852301.htm
- http://m.wap.fcful.cn/nnews/235291.htm
- http://m.wap.fcful.cn/nnews/44743.htm
- http://m.wap.fcful.cn/nnews/6356128.htm
- http://m.wap.fcful.cn/nnews/2821332.htm
- http://m.wap.fcful.cn/nnews/343911.htm
- http://m.wap.fcful.cn/nnews/058987.htm
- http://m.wap.fcful.cn/nnews/97114.htm
- http://m.wap.fcful.cn/nnews/29964.htm
- http://m.wap.fcful.cn/nnews/304390.htm
- http://m.wap.fcful.cn/nnews/8735.htm
- http://m.wap.fcful.cn/nnews/0609395.htm
- http://m.wap.fcful.cn/nnews/839620.htm
- http://m.wap.fcful.cn/nnews/456815.htm
- http://m.wap.fcful.cn/nnews/59861.htm
- http://m.wap.fcful.cn/nnews/70131.htm
- http://m.wap.fcful.cn/nnews/7910.htm
- http://m.wap.fcful.cn/nnews/4765632.htm
- http://m.wap.fcful.cn/nnews/93027.htm
- http://m.wap.fcful.cn/nnews/597186.htm
- http://m.wap.fcful.cn/nnews/432122.htm
- http://m.wap.fcful.cn/nnews/7321.htm
- http://m.wap.fcful.cn/nnews/270023.htm
- http://m.wap.fcful.cn/nnews/103948.htm
- http://m.wap.fcful.cn/nnews/2768.htm
- http://m.wap.fcful.cn/nnews/4954.htm
- http://m.wap.fcful.cn/nnews/7941.htm
- http://m.wap.fcful.cn/nnews/105448.htm
- http://m.wap.fcful.cn/nnews/69018.htm
- http://m.wap.fcful.cn/nnews/1147272.htm
- http://m.wap.fcful.cn/nnews/19409.htm
- http://m.wap.fcful.cn/nnews/3713848.htm
- http://m.wap.fcful.cn/nnews/5198735.htm
- http://m.wap.fcful.cn/nnews/321847.htm
- http://m.wap.fcful.cn/nnews/633630.htm
- http://m.wap.fcful.cn/nnews/122026.htm
- http://m.wap.fcful.cn/nnews/59401.htm
- http://m.wap.fcful.cn/nnews/67587.htm
- http://m.wap.fcful.cn/nnews/623000.htm
- http://m.wap.fcful.cn/nnews/8932804.htm
- http://m.wap.fcful.cn/nnews/4439.htm
- http://m.wap.fcful.cn/nnews/8854.htm
- http://m.wap.fcful.cn/nnews/982035.htm
- http://m.wap.fcful.cn/nnews/9847794.htm
- http://m.wap.fcful.cn/nnews/4486.htm
- http://m.wap.fcful.cn/nnews/809413.htm
- http://m.wap.fcful.cn/nnews/23148.htm
- http://m.wap.fcful.cn/nnews/2736960.htm
- http://m.wap.fcful.cn/nnews/4483581.htm
- http://m.wap.fcful.cn/nnews/48986.htm
- http://m.wap.fcful.cn/nnews/4696900.htm
- http://m.wap.fcful.cn/nnews/055483.htm
- http://m.wap.fcful.cn/nnews/92102.htm
- http://m.wap.fcful.cn/nnews/3151863.htm
- http://m.wap.fcful.cn/nnews/966773.htm
- http://m.wap.fcful.cn/nnews/0345687.htm
- http://m.wap.fcful.cn/nnews/8258240.htm
- http://m.wap.fcful.cn/nnews/110798.htm
- http://m.wap.fcful.cn/nnews/626414.htm
- http://m.wap.fcful.cn/nnews/563147.htm
- http://m.wap.fcful.cn/nnews/2939140.htm
- http://m.wap.fcful.cn/nnews/771471.htm
- http://m.wap.fcful.cn/nnews/9007196.htm
- http://m.wap.fcful.cn/nnews/744580.htm
- http://m.wap.fcful.cn/nnews/90779.htm
- http://m.wap.fcful.cn/nnews/3541639.htm
- http://m.wap.fcful.cn/nnews/821692.htm
- http://m.wap.fcful.cn/nnews/944773.htm
- http://m.wap.fcful.cn/nnews/0306882.htm
- http://m.wap.fcful.cn/nnews/93865.htm
- http://m.wap.fcful.cn/nnews/2624.htm
- http://m.wap.fcful.cn/nnews/33308.htm
- http://m.wap.fcful.cn/nnews/5180148.htm
- http://m.wap.fcful.cn/nnews/6651379.htm
- http://m.wap.fcful.cn/nnews/7564.htm
- http://m.wap.fcful.cn/nnews/9715134.htm
- http://m.wap.fcful.cn/nnews/64868.htm
- http://m.wap.fcful.cn/nnews/764987.htm
- http://m.wap.fcful.cn/nnews/8198.htm
- http://m.wap.fcful.cn/nnews/621391.htm
- http://m.wap.fcful.cn/nnews/4818334.htm
- http://m.wap.fcful.cn/nnews/5993555.htm
- http://m.wap.fcful.cn/nnews/0296823.htm
- http://m.wap.fcful.cn/nnews/779160.htm
- http://m.wap.fcful.cn/nnews/7828252.htm
- http://m.wap.fcful.cn/nnews/689452.htm
- http://m.wap.fcful.cn/nnews/86746.htm
- http://m.wap.fcful.cn/nnews/4583.htm
- http://m.wap.fcful.cn/nnews/1428.htm
- http://m.wap.fcful.cn/nnews/7121827.htm
- http://m.wap.fcful.cn/nnews/1182.htm
- http://m.wap.fcful.cn/nnews/40404.htm
- http://m.wap.fcful.cn/nnews/08965.htm

## 项目结构

```
navigator/
├── cli.py                      # 命令行入口，处理 parse、check、export 等子命令
├── app.py                      # Flask API 服务入口，启动 RESTful 接口
├── requirements.txt            # Python 依赖清单
├── config/
│   ├── default.yaml            # 默认全局配置，含请求超时、重试次数、并发数
│   ├── rules/                  # 自定义解析规则目录
│   │   ├── fcful.yaml          # 针对 m.wap.fcful.cn 的解析规则
│   │   └── example.yaml        # 规则编写示例文件
├── core/
│   ├── parser.py               # 核心解析引擎，调用 fetcher 与 extractor
│   ├── fetcher.py              # HTTP 请求模块，处理重定向与请求头伪装
│   ├── extractor.py            # 基于 beautifulsoup4 的字段提取实现
│   ├── classifier.py           # 基于关键词与规则的分类器
│   └── checker.py              # 链接健康状态检查模块
├── api/
│   ├── routes.py               # API 路由定义，包含 /parse、/status、/export
│   └── schemas.py              # 请求与响应的 Pydantic 数据模型
├── exporters/
│   ├── json_exporter.py        # JSON 格式导出器
│   ├── csv_exporter.py         # CSV 格式导出器
│   └── markdown_exporter.py    # Markdown 表格导出器
├── resources/
│   ├── sample_links.txt        # 示例输入链接列表
│   └── user_agents.txt         # 请求头轮换池
├── tests/
│   ├── test_parser.py          # 解析引擎单元测试
│   ├── test_fetcher.py         # 请求模块单元测试
│   └── fixtures/               # 测试用 HTML 样本文件
├── docs/
│   ├── user_guide.md           # 用户手册
│   ├── api_reference.md        # API 参考文档
│   ├── rule_config.md          # 规则配置指南
│   └── contributing.md         # 贡献者指南
└── LICENSE                     # MIT 许可证文件
```

## 贡献指南

1. 查阅项目 Issue 列表与 Projects 看板，确认当前待处理的任务或您感兴趣的功能方向，在对应 Issue 下留言表明认领意向，避免重复工作。

2. 派生项目仓库至个人账户，创建以 feature/ 或 fix/ 为前缀的分支，例如 feature/add-rss-export，所有开发工作在该分支上进行。

3. 编写或修改代码时，请遵循项目根目录下的 .flake8 与 .pylintrc 规定的代码风格要求，并确保新增或变更的功能有对应的单元测试覆盖，测试文件放置于 tests/ 目录下。

4. 提交代码前运行全部测试套件（pytest tests/）以确保未引入回归问题，并更新 docs/ 目录下相关文档以反映您的改动，特别是涉及配置变更或 API 扩展时。

5. 发起合并请求至主仓库的 main 分支，在请求描述中清晰说明改动目的、实现方案与测试结果，项目维护者将在三个工作日内进行审核与反馈。

## 常见问题

问：项目是否支持解析 HTTPS 协议的链接或其它域名下的新闻页面？

答：核心解析引擎基于通用 HTTP 请求与 HTML 解析能力，理论上支持任意域名与协议。但不同站点的页面结构差异较大，默认规则仅针对示例中的域名进行了优化。对于其它站点，您需要参考 docs/rule_config.md 编写自定义 YAML 规则文件以适配对应的 DOM 结构或元数据位置。

问：批量解析大量链接时，如何避免被目标网站屏蔽？

答：项目内置了请求间隔控制、User-Agent 轮换和失败重试机制。您可以在 config/default.yaml 中调整 request_interval（请求间隔秒数）、max_retries（最大重试次数）以及使用代理列表。建议对于大规模抓取任务，合理设置间隔时间并遵守目标网站的 robots.txt 规则。

问：导出的数据可以用于商业项目吗？

答：项目本身采用 MIT 许可证，您可以将导出的数据用于商业用途。但请注意，导出的数据内容（如新闻标题、正文摘要等）的版权归属原始发布方，您需自行评估并遵守相关法律法规与内容提供者的使用条款。项目工具仅提供技术处理能力，不对数据内容的合规性承担法律责任。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
