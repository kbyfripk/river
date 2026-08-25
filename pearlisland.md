# WapFcNews Archive System

WapFcNews Archive System 是一个面向移动端新闻资源聚合与归档的开源工具集，专注于对特定域名下的结构化新闻页面进行批量采集、索引、快照存储与全文检索。该项目主要服务于新闻研究人员、内容聚合平台开发者、舆情监控系统集成商以及对移动端新闻内容结构分析有需求的工程团队。

与通用爬虫框架不同，WapFcNews Archive System 针对 m.wap.fcful.cn 域名的页面结构特征进行了专门适配，提供从 URL 规范化、内容抽取、去重存储到索引构建的完整工作流。项目本身不依赖外部云服务，所有组件均可本地部署，适合在内网或离线环境中运行。

## 功能概览

批量 URL 导入与校验：支持通过文本文件、CSV 或标准输入流导入大量新闻链接，自动进行格式校验与去重，输出规范化 URL 列表。

结构化内容抽取：针对移动端新闻页面常见的 HTML 结构模式，提供可配置的选择器模板，自动提取标题、正文、发布时间、来源、分类等核心字段。

增量索引与快照管理：基于内容哈希实现页面级去重，支持增量更新索引，同时保留历史快照以便追溯内容变更。

全文检索接口：内置基于倒排索引的全文检索引擎，支持布尔查询、短语查询、时间范围过滤以及相关性排序。

URL 路由与重定向处理：自动跟随页面重定向，识别并处理移动端特有的参数传递模式，确保采集链路的完整性。

定时任务调度：提供基于 Cron 表达式的周期性采集触发器，可对指定 URL 列表进行定时刷新，保持索引数据的新鲜度。

数据导出与互操作：支持将索引数据导出为 JSON Lines、CSV 或 SQLite 数据库文件，便于与其他数据处理工具链集成。

## 应用场景

新闻聚合平台内容采集：内容聚合类应用可通过本项目对 WapFcNews 域名下的文章进行结构化采集，将分散的新闻页面统一转换为结构化数据，存入本地内容库供前端展示。

舆情监控系统数据源接入：舆情分析系统可将本项目作为数据采集前置层，定期抓取指定分类或关键词相关的新闻页面，将抽取后的文本内容送入后续的 NLP 处理流水线。

历史新闻归档与检索：研究机构或个人研究者可利用本项目的增量索引能力，对特定时间段内的新闻页面进行批量归档，构建可全文检索的历史新闻数据库。

移动端新闻结构分析：前端开发或用户体验研究团队可通过本项目抽取的大规模样本数据，分析移动端新闻页面的 DOM 结构演变趋势、广告位分布或加载性能指标。

数据迁移与备份：需要将特定来源的新闻内容迁移至自有平台或进行本地备份时，本项目可提供稳定的批量抓取与格式转换能力。

## 快速开始

以下命令展示了从克隆仓库到启动完整服务的基本流程。请确保已安装 Git 与 Python 3.10 及以上版本。

```bash
git clone https://github.com/wapfc-archive/wapfc-news-archive.git
cd wapfc-news-archive

python -m venv venv
source venv/bin/activate
# Windows 用户请使用: venv\Scripts\activate

pip install -r requirements.txt

cp config/example.settings.yaml config/settings.yaml
# 编辑 settings.yaml 填写必要的数据库连接与采集参数

python manage.py init_db
python manage.py import_urls --input data/seed_urls.txt
python manage.py crawl --concurrency 5 --output data/archive.jsonl
python manage.py serve --host 127.0.0.1 --port 8080
```

完成上述步骤后，可通过 http://127.0.0.1:8080/api/search 访问检索接口，或通过 http://127.0.0.1:8080/admin 查看管理面板。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 至 3.12 | 核心运行环境，推荐使用 3.11 版本以获得最佳性能 |
| SQLite | 3.35 及以上 | 内置索引与元数据存储引擎，无需额外安装 |
| Redis | 7.0 及以上 | 用于分布式锁与任务队列，单机部署可选用内存模式替代 |
| lxml | 5.1.0 及以上 | HTML 解析与 XPath 查询引擎，内容抽取的核心依赖 |
| requests | 2.31.0 及以上 | HTTP 客户端库，处理所有网络请求与重定向逻辑 |
| elasticsearch | 8.10.0 及以上 | 可选组件，用于大规模部署时的分布式索引后端 |
| supervisor | 4.2.0 及以上 | 可选组件，用于生产环境下的进程守护与自动重启 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何快速配置并运行第一个采集任务；如何理解项目的核心工作流 |
| 配置参考 | docs/configuration.md | 所有配置项的含义与默认值；如何调整采集频率、并发数、超时时间 |
| API 文档 | docs/api_reference.md | 检索接口的请求参数与响应格式；管理接口的调用方法 |
| 开发指南 | docs/development.md | 如何扩展自定义抽取器；如何提交补丁；测试套件的运行方式 |

## 资源列表

- http://m.wap.fcful.cn/nnews/5090088.htm
- http://m.wap.fcful.cn/nnews/0674196.htm
- http://m.wap.fcful.cn/nnews/8885.htm
- http://m.wap.fcful.cn/nnews/455172.htm
- http://m.wap.fcful.cn/nnews/6678.htm
- http://m.wap.fcful.cn/nnews/9395.htm
- http://m.wap.fcful.cn/nnews/75597.htm
- http://m.wap.fcful.cn/nnews/4191.htm
- http://m.wap.fcful.cn/nnews/62982.htm
- http://m.wap.fcful.cn/nnews/5063.htm
- http://m.wap.fcful.cn/nnews/133311.htm
- http://m.wap.fcful.cn/nnews/4046704.htm
- http://m.wap.fcful.cn/nnews/741191.htm
- http://m.wap.fcful.cn/nnews/152458.htm
- http://m.wap.fcful.cn/nnews/664997.htm
- http://m.wap.fcful.cn/nnews/4803.htm
- http://m.wap.fcful.cn/nnews/8033.htm
- http://m.wap.fcful.cn/nnews/5361277.htm
- http://m.wap.fcful.cn/nnews/636541.htm
- http://m.wap.fcful.cn/nnews/9834478.htm
- http://m.wap.fcful.cn/nnews/247086.htm
- http://m.wap.fcful.cn/nnews/0578604.htm
- http://m.wap.fcful.cn/nnews/487396.htm
- http://m.wap.fcful.cn/nnews/628944.htm
- http://m.wap.fcful.cn/nnews/5592635.htm
- http://m.wap.fcful.cn/nnews/4008552.htm
- http://m.wap.fcful.cn/nnews/193090.htm
- http://m.wap.fcful.cn/nnews/18580.htm
- http://m.wap.fcful.cn/nnews/58664.htm
- http://m.wap.fcful.cn/nnews/455972.htm
- http://m.wap.fcful.cn/nnews/632731.htm
- http://m.wap.fcful.cn/nnews/2002.htm
- http://m.wap.fcful.cn/nnews/68882.htm
- http://m.wap.fcful.cn/nnews/8180645.htm
- http://m.wap.fcful.cn/nnews/315340.htm
- http://m.wap.fcful.cn/nnews/73939.htm
- http://m.wap.fcful.cn/nnews/125370.htm
- http://m.wap.fcful.cn/nnews/25839.htm
- http://m.wap.fcful.cn/nnews/3959534.htm
- http://m.wap.fcful.cn/nnews/96547.htm
- http://m.wap.fcful.cn/nnews/185450.htm
- http://m.wap.fcful.cn/nnews/9914252.htm
- http://m.wap.fcful.cn/nnews/7432.htm
- http://m.wap.fcful.cn/nnews/624169.htm
- http://m.wap.fcful.cn/nnews/5081.htm
- http://m.wap.fcful.cn/nnews/28252.htm
- http://m.wap.fcful.cn/nnews/419813.htm
- http://m.wap.fcful.cn/nnews/44070.htm
- http://m.wap.fcful.cn/nnews/9709847.htm
- http://m.wap.fcful.cn/nnews/179536.htm
- http://m.wap.fcful.cn/nnews/8919.htm
- http://m.wap.fcful.cn/nnews/7520869.htm
- http://m.wap.fcful.cn/nnews/2893632.htm
- http://m.wap.fcful.cn/nnews/819259.htm
- http://m.wap.fcful.cn/nnews/3594585.htm
- http://m.wap.fcful.cn/nnews/7820.htm
- http://m.wap.fcful.cn/nnews/911784.htm
- http://m.wap.fcful.cn/nnews/2352.htm
- http://m.wap.fcful.cn/nnews/239995.htm
- http://m.wap.fcful.cn/nnews/1934685.htm
- http://m.wap.fcful.cn/nnews/7277.htm
- http://m.wap.fcful.cn/nnews/5512706.htm
- http://m.wap.fcful.cn/nnews/6902668.htm
- http://m.wap.fcful.cn/nnews/478939.htm
- http://m.wap.fcful.cn/nnews/29003.htm
- http://m.wap.fcful.cn/nnews/7191.htm
- http://m.wap.fcful.cn/nnews/0517.htm
- http://m.wap.fcful.cn/nnews/5144678.htm
- http://m.wap.fcful.cn/nnews/2633820.htm
- http://m.wap.fcful.cn/nnews/67104.htm
- http://m.wap.fcful.cn/nnews/87103.htm
- http://m.wap.fcful.cn/nnews/577461.htm
- http://m.wap.fcful.cn/nnews/9393.htm
- http://m.wap.fcful.cn/nnews/7137343.htm
- http://m.wap.fcful.cn/nnews/3685575.htm
- http://m.wap.fcful.cn/nnews/384769.htm
- http://m.wap.fcful.cn/nnews/228207.htm
- http://m.wap.fcful.cn/nnews/1988.htm
- http://m.wap.fcful.cn/nnews/452961.htm
- http://m.wap.fcful.cn/nnews/4222.htm
- http://m.wap.fcful.cn/nnews/831261.htm
- http://m.wap.fcful.cn/nnews/98036.htm
- http://m.wap.fcful.cn/nnews/9653642.htm
- http://m.wap.fcful.cn/nnews/7012572.htm
- http://m.wap.fcful.cn/nnews/569444.htm
- http://m.wap.fcful.cn/nnews/0662.htm
- http://m.wap.fcful.cn/nnews/4304.htm
- http://m.wap.fcful.cn/nnews/1746.htm
- http://m.wap.fcful.cn/nnews/542201.htm
- http://m.wap.fcful.cn/nnews/3429521.htm
- http://m.wap.fcful.cn/nnews/7417.htm
- http://m.wap.fcful.cn/nnews/7775930.htm
- http://m.wap.fcful.cn/nnews/5079649.htm
- http://m.wap.fcful.cn/nnews/430138.htm
- http://m.wap.fcful.cn/nnews/0546.htm
- http://m.wap.fcful.cn/nnews/51292.htm
- http://m.wap.fcful.cn/nnews/6117337.htm
- http://m.wap.fcful.cn/nnews/06144.htm
- http://m.wap.fcful.cn/nnews/0888345.htm
- http://m.wap.fcful.cn/nnews/9869.htm
- http://m.wap.fcful.cn/nnews/1571762.htm
- http://m.wap.fcful.cn/nnews/7790078.htm
- http://m.wap.fcful.cn/nnews/9763328.htm
- http://m.wap.fcful.cn/nnews/7106248.htm
- http://m.wap.fcful.cn/nnews/8836277.htm
- http://m.wap.fcful.cn/nnews/5108.htm
- http://m.wap.fcful.cn/nnews/578793.htm
- http://m.wap.fcful.cn/nnews/5730.htm
- http://m.wap.fcful.cn/nnews/71175.htm
- http://m.wap.fcful.cn/nnews/90564.htm
- http://m.wap.fcful.cn/nnews/4033958.htm
- http://m.wap.fcful.cn/nnews/068565.htm
- http://m.wap.fcful.cn/nnews/8671.htm
- http://m.wap.fcful.cn/nnews/29056.htm
- http://m.wap.fcful.cn/nnews/6225319.htm
- http://m.wap.fcful.cn/nnews/4061409.htm
- http://m.wap.fcful.cn/nnews/74811.htm
- http://m.wap.fcful.cn/nnews/8087.htm
- http://m.wap.fcful.cn/nnews/835298.htm
- http://m.wap.fcful.cn/nnews/7681.htm
- http://m.wap.fcful.cn/nnews/626083.htm
- http://m.wap.fcful.cn/nnews/4860298.htm
- http://m.wap.fcful.cn/nnews/7304.htm
- http://m.wap.fcful.cn/nnews/91998.htm
- http://m.wap.fcful.cn/nnews/80290.htm
- http://m.wap.fcful.cn/nnews/706650.htm
- http://m.wap.fcful.cn/nnews/3379.htm
- http://m.wap.fcful.cn/nnews/151903.htm
- http://m.wap.fcful.cn/nnews/080146.htm
- http://m.wap.fcful.cn/nnews/4629.htm
- http://m.wap.fcful.cn/nnews/09109.htm
- http://m.wap.fcful.cn/nnews/088843.htm
- http://m.wap.fcful.cn/nnews/7582908.htm
- http://m.wap.fcful.cn/nnews/548241.htm
- http://m.wap.fcful.cn/nnews/45359.htm
- http://m.wap.fcful.cn/nnews/39303.htm
- http://m.wap.fcful.cn/nnews/59163.htm
- http://m.wap.fcful.cn/nnews/0170.htm
- http://m.wap.fcful.cn/nnews/93989.htm
- http://m.wap.fcful.cn/nnews/1416.htm
- http://m.wap.fcful.cn/nnews/701056.htm
- http://m.wap.fcful.cn/nnews/4699198.htm
- http://m.wap.fcful.cn/nnews/407793.htm
- http://m.wap.fcful.cn/nnews/414061.htm
- http://m.wap.fcful.cn/nnews/8147177.htm
- http://m.wap.fcful.cn/nnews/1979846.htm
- http://m.wap.fcful.cn/nnews/825628.htm
- http://m.wap.fcful.cn/nnews/29052.htm
- http://m.wap.fcful.cn/nnews/8343.htm
- http://m.wap.fcful.cn/nnews/31177.htm
- http://m.wap.fcful.cn/nnews/173718.htm
- http://m.wap.fcful.cn/nnews/8452068.htm
- http://m.wap.fcful.cn/nnews/834773.htm
- http://m.wap.fcful.cn/nnews/1462540.htm
- http://m.wap.fcful.cn/nnews/05975.htm
- http://m.wap.fcful.cn/nnews/82731.htm
- http://m.wap.fcful.cn/nnews/6618.htm
- http://m.wap.fcful.cn/nnews/21634.htm
- http://m.wap.fcful.cn/nnews/2608.htm
- http://m.wap.fcful.cn/nnews/81535.htm
- http://m.wap.fcful.cn/nnews/5129.htm
- http://m.wap.fcful.cn/nnews/91506.htm
- http://m.wap.fcful.cn/nnews/296242.htm
- http://m.wap.fcful.cn/nnews/87837.htm
- http://m.wap.fcful.cn/nnews/059089.htm
- http://m.wap.fcful.cn/nnews/540926.htm
- http://m.wap.fcful.cn/nnews/7994.htm
- http://m.wap.fcful.cn/nnews/953263.htm
- http://m.wap.fcful.cn/nnews/9426799.htm
- http://m.wap.fcful.cn/nnews/7827.htm
- http://m.wap.fcful.cn/nnews/0935141.htm
- http://m.wap.fcful.cn/nnews/100835.htm
- http://m.wap.fcful.cn/nnews/7033913.htm
- http://m.wap.fcful.cn/nnews/3946398.htm
- http://m.wap.fcful.cn/nnews/7349050.htm
- http://m.wap.fcful.cn/nnews/5471.htm
- http://m.wap.fcful.cn/nnews/0639475.htm
- http://m.wap.fcful.cn/nnews/14390.htm
- http://m.wap.fcful.cn/nnews/3005.htm
- http://m.wap.fcful.cn/nnews/5275.htm
- http://m.wap.fcful.cn/nnews/8413.htm
- http://m.wap.fcful.cn/nnews/8461615.htm
- http://m.wap.fcful.cn/nnews/2121849.htm
- http://m.wap.fcful.cn/nnews/1500.htm
- http://m.wap.fcful.cn/nnews/6464.htm
- http://m.wap.fcful.cn/nnews/15909.htm
- http://m.wap.fcful.cn/nnews/93061.htm
- http://m.wap.fcful.cn/nnews/3514154.htm
- http://m.wap.fcful.cn/nnews/6348031.htm
- http://m.wap.fcful.cn/nnews/9230.htm
- http://m.wap.fcful.cn/nnews/10362.htm
- http://m.wap.fcful.cn/nnews/8402.htm
- http://m.wap.fcful.cn/nnews/25260.htm
- http://m.wap.fcful.cn/nnews/31543.htm
- http://m.wap.fcful.cn/nnews/6798.htm
- http://m.wap.fcful.cn/nnews/573316.htm
- http://m.wap.fcful.cn/nnews/15685.htm
- http://m.wap.fcful.cn/nnews/522651.htm
- http://m.wap.fcful.cn/nnews/698384.htm
- http://m.wap.fcful.cn/nnews/23001.htm
- http://m.wap.fcful.cn/nnews/70291.htm
- http://m.wap.fcful.cn/nnews/1702235.htm
- http://m.wap.fcful.cn/nnews/54962.htm
- http://m.wap.fcful.cn/nnews/51180.htm
- http://m.wap.fcful.cn/nnews/74805.htm
- http://m.wap.fcful.cn/nnews/72486.htm
- http://m.wap.fcful.cn/nnews/0748080.htm
- http://m.wap.fcful.cn/nnews/964681.htm
- http://m.wap.fcful.cn/nnews/51249.htm
- http://m.wap.fcful.cn/nnews/3811.htm
- http://m.wap.fcful.cn/nnews/117473.htm
- http://m.wap.fcful.cn/nnews/1442.htm
- http://m.wap.fcful.cn/nnews/118126.htm
- http://m.wap.fcful.cn/nnews/8403687.htm
- http://m.wap.fcful.cn/nnews/5400826.htm
- http://m.wap.fcful.cn/nnews/87040.htm
- http://m.wap.fcful.cn/nnews/964054.htm
- http://m.wap.fcful.cn/nnews/1063.htm
- http://m.wap.fcful.cn/nnews/5492847.htm
- http://m.wap.fcful.cn/nnews/17761.htm
- http://m.wap.fcful.cn/nnews/9568.htm
- http://m.wap.fcful.cn/nnews/0234.htm
- http://m.wap.fcful.cn/nnews/36925.htm
- http://m.wap.fcful.cn/nnews/0841193.htm
- http://m.wap.fcful.cn/nnews/8508.htm
- http://m.wap.fcful.cn/nnews/1125900.htm
- http://m.wap.fcful.cn/nnews/189138.htm
- http://m.wap.fcful.cn/nnews/6342258.htm
- http://m.wap.fcful.cn/nnews/080674.htm
- http://m.wap.fcful.cn/nnews/95225.htm
- http://m.wap.fcful.cn/nnews/735187.htm
- http://m.wap.fcful.cn/nnews/8926714.htm
- http://m.wap.fcful.cn/nnews/19136.htm
- http://m.wap.fcful.cn/nnews/1671993.htm
- http://m.wap.fcful.cn/nnews/222062.htm
- http://m.wap.fcful.cn/nnews/31964.htm
- http://m.wap.fcful.cn/nnews/53825.htm
- http://m.wap.fcful.cn/nnews/02946.htm
- http://m.wap.fcful.cn/nnews/23458.htm
- http://m.wap.fcful.cn/nnews/95769.htm
- http://m.wap.fcful.cn/nnews/59341.htm
- http://m.wap.fcful.cn/nnews/20107.htm
- http://m.wap.fcful.cn/nnews/1599633.htm
- http://m.wap.fcful.cn/nnews/01285.htm
- http://m.wap.fcful.cn/nnews/1009491.htm
- http://m.wap.fcful.cn/nnews/31411.htm
- http://m.wap.fcful.cn/nnews/82004.htm
- http://m.wap.fcful.cn/nnews/89083.htm
- http://m.wap.fcful.cn/nnews/52364.htm
- http://m.wap.fcful.cn/nnews/711379.htm

## 项目结构

```
wapfc-news-archive/
├── archive/                           # 核心归档模块
│   ├── __init__.py
│   ├── fetcher.py                     # HTTP 请求与重定向处理
│   ├── parser.py                      # 页面结构解析与内容抽取
│   ├── dedup.py                       # 基于哈希的内容去重引擎
│   └── storage.py                     # 本地文件存储与快照管理
├── bin/                               # 可执行脚本与命令行入口
│   ├── crawl                          # 爬取任务启动脚本
│   ├── index                          # 索引构建脚本
│   └── serve                          # API 服务启动脚本
├── config/                            # 配置文件目录
│   ├── default.yaml                   # 默认配置参数
│   ├── example.settings.yaml          # 示例配置文件
│   └── schema/                        # 配置结构定义 JSON Schema
├── docs/                              # 完整文档目录
│   ├── getting_started.md
│   ├── configuration.md
│   ├── api_reference.md
│   └── development.md
├── lib/                               # 公共工具库
│   ├── url_normalizer.py              # URL 规范化与校验
│   ├── date_utils.py                  # 时间解析与格式化工具
│   └── log_manager.py                 # 日志配置与轮转管理
├── scripts/                           # 运维辅助脚本
│   ├── export_jsonl.py                # 数据导出为 JSON Lines
│   ├── import_seed.py                 # 种子 URL 批量导入
│   └── clean_expired.py               # 清理过期快照
├── tests/                             # 单元测试与集成测试
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── fixtures/                      # 测试用例固定样本
├── web/                               # Web 管理界面与 API 服务
│   ├── app.py                         # Flask / FastAPI 主应用
│   ├── templates/                     # Jinja2 模板文件
│   └── static/                        # CSS 与 JavaScript 静态资源
├── requirements.txt                   # Python 依赖清单
├── setup.py                           # 包安装配置
├── .github/                           # GitHub Actions 工作流定义
│   └── workflows/
│       ├── ci.yml                     # 持续集成流水线
│       └── release.yml                # 发布流水线
├── LICENSE                            # MIT 许可证
└── README.md                          # 本文件
```

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于代码提交、文档改进、问题报告与功能建议。请遵循以下步骤参与本项目。

首先，在 GitHub 上 Fork 本仓库，并将 Fork 后的仓库克隆至本地。创建新的功能分支时，请使用 `feature/` 或 `fix/` 前缀，并确保分支名称简要描述变更内容。

其次，所有代码变更必须通过现有的单元测试，并为新增功能或修复编写对应的测试用例。测试套件使用 pytest 框架，运行 `pytest tests/` 即可执行全部测试。

第三，提交代码前请确保代码风格符合 PEP 8 规范，并且所有 Python 文件头部包含正确的许可证声明。建议使用 black 和 isort 工具自动格式化代码。

第四，提交 Pull Request 时请填写清晰的变更描述，说明该 PR 解决的问题、实现方案以及测试覆盖情况。如果 PR 涉及 API 变更或配置格式变更，请同步更新对应的文档文件。

最后，重大功能变更或架构调整建议先通过 Issue 与维护者沟通，确认方案后再进行开发，以避免重复劳动或设计偏离。

## 常见问题

Q: 采集过程中遇到大量 HTTP 429 或 503 状态码如何解决？

A: 这通常表示目标服务器进行了限流或临时过载。建议在配置文件中调整 `crawl.delay` 参数增加请求间隔，同时将 `crawl.max_retries` 设置为 3 或更高。此外，可以启用 `crawl.random_user_agent` 选项以避免被识别为自动化脚本。如果问题持续，请检查网络出口 IP 是否被列入黑名单。

Q: 全文检索功能是否支持中文分词？

A: 内置的倒排索引引擎默认使用基于字符的 n-gram 分词策略，对中文有基本支持。对于更高质量的中文分词需求，建议配置可选的 Elasticsearch 后端，并安装 ik 或 smartcn 分词插件。在配置文件中将 `index.backend` 设置为 `elasticsearch` 并填写相应连接参数即可切换。

Q: 如何迁移已采集的数据到另一台服务器？

A: 迁移数据需要同时转移 SQLite 数据库文件（默认为 `data/index.db`）和快照存储目录（默认为 `data/snapshots/`）。将这两个目录复制到新服务器的相同相对路径下，并确保配置文件中的 `storage.base_dir` 指向正确位置。如果使用了 Redis 或 Elasticsearch 后端，则需额外导出对应数据源的内容。

## 许可证

MIT License

Copyright (c) 2026 WapFc Archive Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
