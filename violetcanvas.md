# NewsIndexer

NewsIndexer 是一个面向移动端新闻资讯聚合与结构化索引的开源工具集，定位于帮助开发者、数据分析师与内容研究者快速构建轻量级新闻资源镜像站与元数据检索系统。项目核心解决移动端新闻页面分散、链接格式不统一、元数据抽取困难以及批量资源管理缺乏标准化方案等问题，提供从 URL 采集、内容解析到索引构建的完整工作流。目标用户包括独立开发者、学术研究人员、新闻聚合平台运维人员以及从事信息可视化项目的工程师。

## 功能概览

批量链接规范化处理 提供对非标准移动端新闻 URL 的自动清洗、补全与重定向校验，支持多批次导入。

元数据智能抽取引擎 从新闻页面中自动提取标题、发布时间、正文摘要、来源站点及分类标签，支持自定义正则匹配规则。

增量索引构建系统 基于 SQLite 与 Lunr.js 实现轻量级全文检索索引，支持增量更新与版本回溯。

资源状态监控面板 实时检测链接可用性、响应码状态、页面加载时长，生成健康度报告。

结构化数据导出接口 支持 JSON、CSV、RSS 三种输出格式，便于下游数据分析或静态站点生成。

批处理任务调度器 内置基于 CRON 表达式的定时任务系统，支持每日自动拉取、解析与索引更新。

离线缓存与回源策略 对已解析内容进行本地持久化缓存，配置可自定义回源间隔与缓存淘汰算法。

## 应用场景

移动端新闻归档项目 开发者可利用 NewsIndexer 批量导入历史新闻链接，构建可按时间、关键词检索的本地新闻档案库，适用于媒体研究或舆情回溯。

内容聚合站点后端 作为数据采集层，为个人或团队运营的新闻聚合网站提供稳定、可配置的链接解析与索引更新服务，降低手动维护成本。

学术数据集的构建 研究人员借助批量资源导入功能，快速生成带有结构化元数据的新闻语料数据集，用于自然语言处理或社会网络分析实验。

运维监控告警系统 通过资源状态监控面板定时探测链接可用性，及时发现内容源异常或页面改版导致的解析失效，保障下游服务稳定性。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/newsindexer/newsindexer.git

# 进入项目目录
cd newsindexer

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 执行初始化配置
python scripts/init_config.py

# 运行批处理导入示例（使用项目内置测试链接集）
python runner.py --batch ./data/sample_batch.json --output ./output/index.db
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 - 3.12 | 核心运行环境，低于 3.10 不支持 match 语法 |
| SQLite | 3.35.0+ | 内置索引存储引擎，支持 JSON 扩展 |
| aiohttp | 3.9.0+ | 异步 HTTP 客户端，用于并发请求 |
| beautifulsoup4 | 4.12.0+ | HTML 解析与 DOM 遍历 |
| lxml | 4.9.0+ | 高性能 XML/HTML 解析后端 |
| lunr.py | 0.6.0+ | 全文检索引擎 Python 适配版 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何安装并运行第一个导入任务，理解基本配置项 |
| 使用手册 | docs/usage/batch_import.md | 怎样编写批量链接 JSON 文件，支持哪些字段格式 |
| 进阶主题 | docs/advanced/custom_parser.md | 如何为特定新闻站点编写自定义解析规则 |
| API 参考 | docs/api/indexer.md | 索引器核心类与方法说明，参数及返回值定义 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/8830.htm
- http://m.3g.gqskj.cn/xnews/2561174.htm
- http://m.3g.gqskj.cn/xnews/448084.htm
- http://m.3g.gqskj.cn/xnews/1174366.htm
- http://m.3g.gqskj.cn/xnews/14976.htm
- http://m.3g.gqskj.cn/xnews/8209744.htm
- http://m.3g.gqskj.cn/xnews/4190.htm
- http://m.3g.gqskj.cn/xnews/44095.htm
- http://m.3g.gqskj.cn/xnews/1252.htm
- http://m.3g.gqskj.cn/xnews/2326297.htm
- http://m.3g.gqskj.cn/xnews/4772934.htm
- http://m.3g.gqskj.cn/xnews/53490.htm
- http://m.3g.gqskj.cn/xnews/23965.htm
- http://m.3g.gqskj.cn/xnews/2076.htm
- http://m.3g.gqskj.cn/xnews/2105258.htm
- http://m.3g.gqskj.cn/xnews/81086.htm
- http://m.3g.gqskj.cn/xnews/403995.htm
- http://m.3g.gqskj.cn/xnews/0379111.htm
- http://m.3g.gqskj.cn/xnews/5642.htm
- http://m.3g.gqskj.cn/xnews/3429534.htm
- http://m.3g.gqskj.cn/xnews/98803.htm
- http://m.3g.gqskj.cn/xnews/26291.htm
- http://m.3g.gqskj.cn/xnews/7672.htm
- http://m.3g.gqskj.cn/xnews/3650.htm
- http://m.3g.gqskj.cn/xnews/80859.htm
- http://m.3g.gqskj.cn/xnews/177676.htm
- http://m.3g.gqskj.cn/xnews/6613752.htm
- http://m.3g.gqskj.cn/xnews/8703.htm
- http://m.3g.gqskj.cn/xnews/80059.htm
- http://m.3g.gqskj.cn/xnews/0542.htm
- http://m.3g.gqskj.cn/xnews/7050282.htm
- http://m.3g.gqskj.cn/xnews/551031.htm
- http://m.3g.gqskj.cn/xnews/5497.htm
- http://m.3g.gqskj.cn/xnews/80809.htm
- http://m.3g.gqskj.cn/xnews/35207.htm
- http://m.3g.gqskj.cn/xnews/23952.htm
- http://m.3g.gqskj.cn/xnews/3735.htm
- http://m.3g.gqskj.cn/xnews/5116.htm
- http://m.3g.gqskj.cn/xnews/914051.htm
- http://m.3g.gqskj.cn/xnews/688700.htm
- http://m.3g.gqskj.cn/xnews/18342.htm
- http://m.3g.gqskj.cn/xnews/96237.htm
- http://m.3g.gqskj.cn/xnews/82666.htm
- http://m.3g.gqskj.cn/xnews/838899.htm
- http://m.3g.gqskj.cn/xnews/8865.htm
- http://m.3g.gqskj.cn/xnews/2397.htm
- http://m.3g.gqskj.cn/xnews/4586955.htm
- http://m.3g.gqskj.cn/xnews/908916.htm
- http://m.3g.gqskj.cn/xnews/1002740.htm
- http://m.3g.gqskj.cn/xnews/1859389.htm
- http://m.3g.gqskj.cn/xnews/612118.htm
- http://m.3g.gqskj.cn/xnews/8193.htm
- http://m.3g.gqskj.cn/xnews/0251.htm
- http://m.3g.gqskj.cn/xnews/60293.htm
- http://m.3g.gqskj.cn/xnews/44047.htm
- http://m.3g.gqskj.cn/xnews/7373712.htm
- http://m.3g.gqskj.cn/xnews/3379635.htm
- http://m.3g.gqskj.cn/xnews/6480.htm
- http://m.3g.gqskj.cn/xnews/8083588.htm
- http://m.3g.gqskj.cn/xnews/67695.htm
- http://m.3g.gqskj.cn/xnews/7683652.htm
- http://m.3g.gqskj.cn/xnews/7275170.htm
- http://m.3g.gqskj.cn/xnews/5777015.htm
- http://m.3g.gqskj.cn/xnews/27222.htm
- http://m.3g.gqskj.cn/xnews/1783160.htm
- http://m.3g.gqskj.cn/xnews/5103.htm
- http://m.3g.gqskj.cn/xnews/921470.htm
- http://m.3g.gqskj.cn/xnews/5461.htm
- http://m.3g.gqskj.cn/xnews/5191723.htm
- http://m.3g.gqskj.cn/xnews/845328.htm
- http://m.3g.gqskj.cn/xnews/47043.htm
- http://m.3g.gqskj.cn/xnews/3849276.htm
- http://m.3g.gqskj.cn/xnews/395255.htm
- http://m.3g.gqskj.cn/xnews/364610.htm
- http://m.3g.gqskj.cn/xnews/227130.htm
- http://m.3g.gqskj.cn/xnews/8971.htm
- http://m.3g.gqskj.cn/xnews/475002.htm
- http://m.3g.gqskj.cn/xnews/840342.htm
- http://m.3g.gqskj.cn/xnews/3509381.htm
- http://m.3g.gqskj.cn/xnews/05555.htm
- http://m.3g.gqskj.cn/xnews/957678.htm
- http://m.3g.gqskj.cn/xnews/037644.htm
- http://m.3g.gqskj.cn/xnews/2650060.htm
- http://m.3g.gqskj.cn/xnews/27651.htm
- http://m.3g.gqskj.cn/xnews/0582.htm
- http://m.3g.gqskj.cn/xnews/61591.htm
- http://m.3g.gqskj.cn/xnews/5419.htm
- http://m.3g.gqskj.cn/xnews/563565.htm
- http://m.3g.gqskj.cn/xnews/9248.htm
- http://m.3g.gqskj.cn/xnews/8020.htm
- http://m.3g.gqskj.cn/xnews/66965.htm
- http://m.3g.gqskj.cn/xnews/0773096.htm
- http://m.3g.gqskj.cn/xnews/117578.htm
- http://m.3g.gqskj.cn/xnews/57128.htm
- http://m.3g.gqskj.cn/xnews/255925.htm
- http://m.3g.gqskj.cn/xnews/50029.htm
- http://m.3g.gqskj.cn/xnews/7495913.htm
- http://m.3g.gqskj.cn/xnews/1688875.htm
- http://m.3g.gqskj.cn/xnews/150126.htm
- http://m.3g.gqskj.cn/xnews/69973.htm
- http://m.3g.gqskj.cn/xnews/4661521.htm
- http://m.3g.gqskj.cn/xnews/7201133.htm
- http://m.3g.gqskj.cn/xnews/4488.htm
- http://m.3g.gqskj.cn/xnews/0130.htm
- http://m.3g.gqskj.cn/xnews/2534.htm
- http://m.3g.gqskj.cn/xnews/5824015.htm
- http://m.3g.gqskj.cn/xnews/0368566.htm
- http://m.3g.gqskj.cn/xnews/0832436.htm
- http://m.3g.gqskj.cn/xnews/2072534.htm
- http://m.3g.gqskj.cn/xnews/48158.htm
- http://m.3g.gqskj.cn/xnews/16171.htm
- http://m.3g.gqskj.cn/xnews/5816.htm
- http://m.3g.gqskj.cn/xnews/208742.htm
- http://m.3g.gqskj.cn/xnews/4982433.htm
- http://m.3g.gqskj.cn/xnews/097354.htm
- http://m.3g.gqskj.cn/xnews/35388.htm
- http://m.3g.gqskj.cn/xnews/4691.htm
- http://m.3g.gqskj.cn/xnews/4686673.htm
- http://m.3g.gqskj.cn/xnews/5092130.htm
- http://m.3g.gqskj.cn/xnews/9227.htm
- http://m.3g.gqskj.cn/xnews/7360236.htm
- http://m.3g.gqskj.cn/xnews/2308.htm
- http://m.3g.gqskj.cn/xnews/414969.htm
- http://m.3g.gqskj.cn/xnews/58931.htm
- http://m.3g.gqskj.cn/xnews/226608.htm
- http://m.3g.gqskj.cn/xnews/8334.htm
- http://m.3g.gqskj.cn/xnews/438590.htm
- http://m.3g.gqskj.cn/xnews/37964.htm
- http://m.3g.gqskj.cn/xnews/61291.htm
- http://m.3g.gqskj.cn/xnews/5312801.htm
- http://m.3g.gqskj.cn/xnews/5965878.htm
- http://m.3g.gqskj.cn/xnews/78655.htm
- http://m.3g.gqskj.cn/xnews/0304.htm
- http://m.3g.gqskj.cn/xnews/33264.htm
- http://m.3g.gqskj.cn/xnews/541143.htm
- http://m.3g.gqskj.cn/xnews/1015.htm
- http://m.3g.gqskj.cn/xnews/38905.htm
- http://m.3g.gqskj.cn/xnews/6199281.htm
- http://m.3g.gqskj.cn/xnews/7395.htm
- http://m.3g.gqskj.cn/xnews/7797757.htm
- http://m.3g.gqskj.cn/xnews/8206224.htm
- http://m.3g.gqskj.cn/xnews/15171.htm
- http://m.3g.gqskj.cn/xnews/2423.htm
- http://m.3g.gqskj.cn/xnews/3313147.htm
- http://m.3g.gqskj.cn/xnews/9353820.htm
- http://m.3g.gqskj.cn/xnews/1018686.htm
- http://m.3g.gqskj.cn/xnews/5442508.htm
- http://m.3g.gqskj.cn/xnews/2187167.htm
- http://m.3g.gqskj.cn/xnews/821163.htm
- http://m.3g.gqskj.cn/xnews/6883928.htm
- http://m.3g.gqskj.cn/xnews/84038.htm
- http://m.3g.gqskj.cn/xnews/57168.htm
- http://m.3g.gqskj.cn/xnews/60452.htm
- http://m.3g.gqskj.cn/xnews/4414768.htm
- http://m.3g.gqskj.cn/xnews/537173.htm
- http://m.3g.gqskj.cn/xnews/6299.htm
- http://m.3g.gqskj.cn/xnews/8297986.htm
- http://m.3g.gqskj.cn/xnews/963139.htm
- http://m.3g.gqskj.cn/xnews/17193.htm
- http://m.3g.gqskj.cn/xnews/5065100.htm
- http://m.3g.gqskj.cn/xnews/09693.htm
- http://m.3g.gqskj.cn/xnews/7945941.htm
- http://m.3g.gqskj.cn/xnews/5563.htm
- http://m.3g.gqskj.cn/xnews/231944.htm
- http://m.3g.gqskj.cn/xnews/822505.htm
- http://m.3g.gqskj.cn/xnews/0418.htm
- http://m.3g.gqskj.cn/xnews/579261.htm
- http://m.3g.gqskj.cn/xnews/751530.htm
- http://m.3g.gqskj.cn/xnews/2192389.htm
- http://m.3g.gqskj.cn/xnews/8149.htm
- http://m.3g.gqskj.cn/xnews/2499938.htm
- http://m.3g.gqskj.cn/xnews/00831.htm
- http://m.3g.gqskj.cn/xnews/2229828.htm
- http://m.3g.gqskj.cn/xnews/8657.htm
- http://m.3g.gqskj.cn/xnews/323420.htm
- http://m.3g.gqskj.cn/xnews/8053602.htm
- http://m.3g.gqskj.cn/xnews/1220.htm
- http://m.3g.gqskj.cn/xnews/94575.htm
- http://m.3g.gqskj.cn/xnews/897949.htm
- http://m.3g.gqskj.cn/xnews/7228.htm
- http://m.3g.gqskj.cn/xnews/1433.htm
- http://m.3g.gqskj.cn/xnews/9600019.htm
- http://m.3g.gqskj.cn/xnews/11304.htm
- http://m.3g.gqskj.cn/xnews/695418.htm
- http://m.3g.gqskj.cn/xnews/89294.htm
- http://m.3g.gqskj.cn/xnews/478950.htm
- http://m.3g.gqskj.cn/xnews/3907812.htm
- http://m.3g.gqskj.cn/xnews/881439.htm
- http://m.3g.gqskj.cn/xnews/897259.htm
- http://m.3g.gqskj.cn/xnews/9645285.htm
- http://m.3g.gqskj.cn/xnews/45486.htm
- http://m.3g.gqskj.cn/xnews/9148.htm
- http://m.3g.gqskj.cn/xnews/6258718.htm
- http://m.3g.gqskj.cn/xnews/6774659.htm
- http://m.3g.gqskj.cn/xnews/6195183.htm
- http://m.3g.gqskj.cn/xnews/354628.htm
- http://m.3g.gqskj.cn/xnews/824337.htm
- http://m.3g.gqskj.cn/xnews/0271890.htm
- http://m.3g.gqskj.cn/xnews/75907.htm
- http://m.3g.gqskj.cn/xnews/0234.htm
- http://m.3g.gqskj.cn/xnews/05618.htm
- http://m.3g.gqskj.cn/xnews/835828.htm
- http://m.3g.gqskj.cn/xnews/70767.htm
- http://m.3g.gqskj.cn/xnews/215734.htm
- http://m.3g.gqskj.cn/xnews/8689.htm
- http://m.3g.gqskj.cn/xnews/2858133.htm
- http://m.3g.gqskj.cn/xnews/66287.htm
- http://m.3g.gqskj.cn/xnews/64148.htm
- http://m.3g.gqskj.cn/xnews/9623875.htm
- http://m.3g.gqskj.cn/xnews/6166499.htm
- http://m.3g.gqskj.cn/xnews/9192.htm
- http://m.3g.gqskj.cn/xnews/452732.htm
- http://m.3g.gqskj.cn/xnews/19476.htm
- http://m.3g.gqskj.cn/xnews/38302.htm
- http://m.3g.gqskj.cn/xnews/3553928.htm
- http://m.3g.gqskj.cn/xnews/84224.htm
- http://m.3g.gqskj.cn/xnews/3489398.htm
- http://m.3g.gqskj.cn/xnews/739436.htm
- http://m.3g.gqskj.cn/xnews/046693.htm
- http://m.3g.gqskj.cn/xnews/0999.htm
- http://m.3g.gqskj.cn/xnews/27093.htm
- http://m.3g.gqskj.cn/xnews/7906.htm
- http://m.3g.gqskj.cn/xnews/6787407.htm
- http://m.3g.gqskj.cn/xnews/7400905.htm
- http://m.3g.gqskj.cn/xnews/33881.htm
- http://m.3g.gqskj.cn/xnews/3502.htm
- http://m.3g.gqskj.cn/xnews/5048.htm
- http://m.3g.gqskj.cn/xnews/9037.htm
- http://m.3g.gqskj.cn/xnews/53427.htm
- http://m.3g.gqskj.cn/xnews/2375744.htm
- http://m.3g.gqskj.cn/xnews/52511.htm
- http://m.3g.gqskj.cn/xnews/9742384.htm
- http://m.3g.gqskj.cn/xnews/02335.htm
- http://m.3g.gqskj.cn/xnews/99458.htm
- http://m.3g.gqskj.cn/xnews/306541.htm
- http://m.3g.gqskj.cn/xnews/6398.htm
- http://m.3g.gqskj.cn/xnews/01103.htm
- http://m.3g.gqskj.cn/xnews/0735631.htm
- http://m.3g.gqskj.cn/xnews/990808.htm
- http://m.3g.gqskj.cn/xnews/356177.htm
- http://m.3g.gqskj.cn/xnews/03213.htm
- http://m.3g.gqskj.cn/xnews/9771.htm
- http://m.3g.gqskj.cn/xnews/8053553.htm
- http://m.3g.gqskj.cn/xnews/6955030.htm
- http://m.3g.gqskj.cn/xnews/3057512.htm
- http://m.3g.gqskj.cn/xnews/66132.htm
- http://m.3g.gqskj.cn/xnews/30118.htm
- http://m.3g.gqskj.cn/xnews/5659.htm
- http://m.3g.gqskj.cn/xnews/0587233.htm
- http://m.3g.gqskj.cn/xnews/2339.htm

## 项目结构

```
newsindexer/
├── runner.py                 # 主入口，解析命令行参数并调度任务
├── requirements.txt          # Python 依赖声明文件
├── config/
│   ├── default.yaml          # 默认配置（并发数、超时、缓存路径）
│   └── custom.yaml.example   # 用户自定义配置模板
├── core/
│   ├── __init__.py
│   ├── fetcher.py            # 异步 HTTP 请求与重定向处理
│   ├── parser.py             # 基于 BeautifulSoup 的元数据抽取
│   ├── indexer.py            # SQLite + Lunr 索引构建核心
│   └── scheduler.py          # CRON 任务调度与状态机
├── pipelines/
│   ├── __init__.py
│   ├── json_exporter.py      # 导出 JSON 格式数据
│   ├── csv_exporter.py       # 导出 CSV 格式数据
│   └── rss_generator.py      # 生成 RSS 订阅源
├── scripts/
│   ├── init_config.py        # 初始化配置文件与环境检查
│   ├── validate_links.py     # 批量链接可用性预检
│   └── migrate_db.py         # 索引数据库版本升级脚本
├── tests/
│   ├── test_fetcher.py       # 单元测试：请求模块
│   ├── test_parser.py        # 单元测试：解析模块
│   └── fixtures/             # 测试用静态 HTML 样本
├── docs/                     # 完整文档目录（详见文档导航）
└── data/                     # 默认数据存储目录（含示例批次文件）
```

## 贡献指南

1. 阅读项目行为准则与开发者协议，在 GitHub 上 fork 主仓库并 clone 到本地开发环境。
2. 创建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式，确保与主分支保持同步。
3. 编写代码时遵守 PEP 8 编码规范，为新增功能补充单元测试，测试覆盖率不低于 85%。
4. 提交前运行全部测试套件与静态检查工具，确保无回归错误与 lint 警告。
5. 发起 pull request 至主仓库的 dev 分支，在描述中清晰说明改动内容、影响范围及测试结果。

## 常见问题

Q: 导入批量链接时提示连接超时或 SSL 错误，如何解决？
A: 检查网络代理设置，在配置文件中调整 `request_timeout` 参数（默认 30 秒）。若目标站点使用过期 TLS 证书，可设置 `verify_ssl: false`（仅限测试环境）。生产环境建议更新系统 CA 证书包。

Q: 索引构建后搜索结果相关性较低，如何优化？
A: 调整 Lunr 索引的字段权重配置，在 `config/default.yaml` 中修改 `index.field_weights` 部分，例如为标题字段赋予更高权重。亦可启用自定义停用词表或扩展同义词词典。

Q: 是否支持增量更新已有的索引库？
A: 支持。在运行导入时指定 `--update` 参数，系统将依据链接 URL 的哈希值判断内容是否变更，仅对新页面或更新页面重新解析并追加到索引中，已存在且未变更的条目维持原状。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:48
