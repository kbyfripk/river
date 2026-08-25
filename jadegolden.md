# NewsLink Indexer

NewsLink Indexer 是一个面向移动端新闻资源聚合与结构化索引的开源工具集。该项目定位于为内容聚合平台、舆情分析系统、个性化推荐引擎以及学术研究机构提供标准化的新闻外链采集、清洗、分类与持久化存储能力。目标用户包括数据工程师、后端开发人员、爬虫框架维护者以及需要批量处理半结构化新闻入口链接的技术团队。

项目通过解析特定域名下的 ID 型新闻资源路径，构建可扩展的增量索引机制，解决海量新闻入口链接分散、元数据缺失、有效性难以持续验证等实际问题。NewsLink Indexer 本身不存储新闻正文，而是作为一个高质量的外链引用层，为上层应用提供可复用的、带时间戳与状态标记的新闻引用记录。

## 功能概览

批量链接导入解析器 支持从文本文件、CSV 或标准输入流中批量读取新闻链接，自动识别资源 ID 与域名一致性，并生成内部唯一的记录指纹。

增量索引构建引擎 基于最后抓取时间与 HTTP 状态码，实现新闻链接的增量更新策略，避免重复处理已失效或未变更的资源。

资源可用性探测模块 对每条新闻链接执行可配置的超时与重试策略的 HEAD 请求，标记链接的实时可达性，并记录响应头中的内容类型与内容长度。

结构化元数据抽取器 从链接路径中提取数字型资源 ID，并根据预配置的正则规则集自动推断新闻可能的发布时间段与分类标签。

持久化存储适配层 提供 SQLite 本地存储与 MySQL/PostgreSQL 远程存储两种后端选项，支持批量写入、去重更新与条件查询。

定时任务调度器 内置基于 Cron 表达式的调度器，支持每日、每小时或自定义间隔自动运行索引刷新任务，并将执行日志输出至标准日志系统。

状态监控与报告生成器 汇总每次索引任务的统计信息，包括新增链接数、失效链接数、总索引量以及错误明细，并生成 JSON 或 Markdown 格式的摘要报告。

## 应用场景

舆情监控系统的底层数据源初始化 舆情分析团队可以使用 NewsLink Indexer 定期拉取指定域名下的新闻链接列表，作为后续内容抓取与情感分析管道的入口种子，确保覆盖度与时效性。

推荐引擎的热门新闻素材发现 内容推荐系统可依赖本工具每日生成的可用链接索引，结合外部点击量数据，快速筛选出高潜力新闻资源，从而降低人工配置成本。

新闻链接有效性长期追踪研究 学术研究机构可利用索引器对同一批新闻链接进行跨周、跨月的多次探测，分析新闻内容存续周期与域名稳定性，为网络信息生命周期研究提供结构化数据支撑。

个人开发者的轻量级新闻聚合测试环境 独立开发者可借助本地 SQLite 存储快速搭建个人新闻聚合站的后端数据层，无需依赖第三方付费 API，即可获得可编程的新闻入口数据集。

## 快速开始

以下步骤指导用户在 Linux 或 macOS 环境下完成项目的克隆、安装与初次运行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newslink-indexer.git

# 进入项目根目录
cd newslink-indexer

# 创建并激活 Python 虚拟环境（建议 Python 3.9 及以上）
python3 -m venv venv
source venv/bin/activate

# 安装核心依赖与生产环境所需包
pip install -r requirements.txt

# 复制示例配置文件并修改数据库连接等参数
cp config.example.yaml config.yaml

# 运行内置测试集，验证安装是否成功
python -m newslink_indexer.tests.run_all

# 执行首次索引任务（使用默认配置与示例链接列表）
python -m newslink_indexer.cli index --source sample_links.txt --output result.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 核心运行时环境，推荐使用 3.10 或 3.11 以获得最佳性能 |
| requests | 2.28.0 或更高 | 用于发送 HTTP HEAD 与 GET 请求进行可用性探测 |
| pyyaml | 6.0 或更高 | 解析 YAML 格式的配置文件 |
| apscheduler | 3.10.0 或更高 | 提供定时任务调度能力，支持 Cron 表达式 |
| sqlalchemy | 2.0.0 或更高 | 数据库 ORM 抽象层，用于支持多种后端存储 |
| pytest | 7.0.0 或更高 | 仅开发与测试环境必需，用于运行单元测试与集成测试 |
| mysqlclient | 2.2.0 或更高 | 仅当使用 MySQL 后端时需要额外安装 |
| psycopg2-binary | 2.9.0 或更高 | 仅当使用 PostgreSQL 后端时需要额外安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何快速配置并运行第一次索引任务；如何理解核心配置文件中的每一字段 |
| 运维手册 | docs/operations.md | 如何部署定时任务；如何迁移数据库存储后端；如何处理常见的网络超时与连接错误 |
| 开发指南 | docs/development.md | 如何扩展新的元数据抽取规则；如何增加自定义探测策略；如何提交符合规范的 Pull Request |
| API 参考 | docs/api_reference.md | 内部模块的类与函数说明；各方法接收的参数类型与返回值结构；异常定义与处理约定 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/23920.htm
- http://m.3g.gqskj.cn/xnews/634481.htm
- http://m.3g.gqskj.cn/xnews/8780.htm
- http://m.3g.gqskj.cn/xnews/192182.htm
- http://m.3g.gqskj.cn/xnews/9427893.htm
- http://m.3g.gqskj.cn/xnews/4222.htm
- http://m.3g.gqskj.cn/xnews/2924.htm
- http://m.3g.gqskj.cn/xnews/63576.htm
- http://m.3g.gqskj.cn/xnews/2265667.htm
- http://m.3g.gqskj.cn/xnews/5696426.htm
- http://m.3g.gqskj.cn/xnews/327015.htm
- http://m.3g.gqskj.cn/xnews/5329881.htm
- http://m.3g.gqskj.cn/xnews/693566.htm
- http://m.3g.gqskj.cn/xnews/1806.htm
- http://m.3g.gqskj.cn/xnews/27529.htm
- http://m.3g.gqskj.cn/xnews/9461484.htm
- http://m.3g.gqskj.cn/xnews/48513.htm
- http://m.3g.gqskj.cn/xnews/4891.htm
- http://m.3g.gqskj.cn/xnews/213510.htm
- http://m.3g.gqskj.cn/xnews/0763006.htm
- http://m.3g.gqskj.cn/xnews/3649.htm
- http://m.3g.gqskj.cn/xnews/7663701.htm
- http://m.3g.gqskj.cn/xnews/5470334.htm
- http://m.3g.gqskj.cn/xnews/0227.htm
- http://m.3g.gqskj.cn/xnews/9959.htm
- http://m.3g.gqskj.cn/xnews/0113280.htm
- http://m.3g.gqskj.cn/xnews/0229.htm
- http://m.3g.gqskj.cn/xnews/3224.htm
- http://m.3g.gqskj.cn/xnews/8432.htm
- http://m.3g.gqskj.cn/xnews/04984.htm
- http://m.3g.gqskj.cn/xnews/8893.htm
- http://m.3g.gqskj.cn/xnews/03119.htm
- http://m.3g.gqskj.cn/xnews/6294990.htm
- http://m.3g.gqskj.cn/xnews/992739.htm
- http://m.3g.gqskj.cn/xnews/00214.htm
- http://m.3g.gqskj.cn/xnews/755974.htm
- http://m.3g.gqskj.cn/xnews/555838.htm
- http://m.3g.gqskj.cn/xnews/7605119.htm
- http://m.3g.gqskj.cn/xnews/82585.htm
- http://m.3g.gqskj.cn/xnews/8877383.htm
- http://m.3g.gqskj.cn/xnews/10282.htm
- http://m.3g.gqskj.cn/xnews/9579.htm
- http://m.3g.gqskj.cn/xnews/2759634.htm
- http://m.3g.gqskj.cn/xnews/59825.htm
- http://m.3g.gqskj.cn/xnews/8457.htm
- http://m.3g.gqskj.cn/xnews/69739.htm
- http://m.3g.gqskj.cn/xnews/4162674.htm
- http://m.3g.gqskj.cn/xnews/8102.htm
- http://m.3g.gqskj.cn/xnews/32520.htm
- http://m.3g.gqskj.cn/xnews/9388.htm
- http://m.3g.gqskj.cn/xnews/28929.htm
- http://m.3g.gqskj.cn/xnews/3151.htm
- http://m.3g.gqskj.cn/xnews/71316.htm
- http://m.3g.gqskj.cn/xnews/0043.htm
- http://m.3g.gqskj.cn/xnews/02992.htm
- http://m.3g.gqskj.cn/xnews/84127.htm
- http://m.3g.gqskj.cn/xnews/992560.htm
- http://m.3g.gqskj.cn/xnews/5576.htm
- http://m.3g.gqskj.cn/xnews/7577.htm
- http://m.3g.gqskj.cn/xnews/980749.htm
- http://m.3g.gqskj.cn/xnews/90488.htm
- http://m.3g.gqskj.cn/xnews/36089.htm
- http://m.3g.gqskj.cn/xnews/2954677.htm
- http://m.3g.gqskj.cn/xnews/1556138.htm
- http://m.3g.gqskj.cn/xnews/29129.htm
- http://m.3g.gqskj.cn/xnews/1935946.htm
- http://m.3g.gqskj.cn/xnews/0946.htm
- http://m.3g.gqskj.cn/xnews/2720292.htm
- http://m.3g.gqskj.cn/xnews/5496330.htm
- http://m.3g.gqskj.cn/xnews/3981.htm
- http://m.3g.gqskj.cn/xnews/36888.htm
- http://m.3g.gqskj.cn/xnews/603849.htm
- http://m.3g.gqskj.cn/xnews/4971.htm
- http://m.3g.gqskj.cn/xnews/0180.htm
- http://m.3g.gqskj.cn/xnews/7592.htm
- http://m.3g.gqskj.cn/xnews/4224.htm
- http://m.3g.gqskj.cn/xnews/5934290.htm
- http://m.3g.gqskj.cn/xnews/8981.htm
- http://m.3g.gqskj.cn/xnews/0980.htm
- http://m.3g.gqskj.cn/xnews/1376375.htm
- http://m.3g.gqskj.cn/xnews/4647.htm
- http://m.3g.gqskj.cn/xnews/2430894.htm
- http://m.3g.gqskj.cn/xnews/3944703.htm
- http://m.3g.gqskj.cn/xnews/9079.htm
- http://m.3g.gqskj.cn/xnews/9178.htm
- http://m.3g.gqskj.cn/xnews/380751.htm
- http://m.3g.gqskj.cn/xnews/88833.htm
- http://m.3g.gqskj.cn/xnews/730450.htm
- http://m.3g.gqskj.cn/xnews/7465.htm
- http://m.3g.gqskj.cn/xnews/7885045.htm
- http://m.3g.gqskj.cn/xnews/6089.htm
- http://m.3g.gqskj.cn/xnews/9922707.htm
- http://m.3g.gqskj.cn/xnews/6861.htm
- http://m.3g.gqskj.cn/xnews/5541903.htm
- http://m.3g.gqskj.cn/xnews/5406.htm
- http://m.3g.gqskj.cn/xnews/37432.htm
- http://m.3g.gqskj.cn/xnews/9525354.htm
- http://m.3g.gqskj.cn/xnews/95680.htm
- http://m.3g.gqskj.cn/xnews/72779.htm
- http://m.3g.gqskj.cn/xnews/114813.htm
- http://m.3g.gqskj.cn/xnews/326774.htm
- http://m.3g.gqskj.cn/xnews/45475.htm
- http://m.3g.gqskj.cn/xnews/332090.htm
- http://m.3g.gqskj.cn/xnews/973857.htm
- http://m.3g.gqskj.cn/xnews/3103345.htm
- http://m.3g.gqskj.cn/xnews/532775.htm
- http://m.3g.gqskj.cn/xnews/6289.htm
- http://m.3g.gqskj.cn/xnews/676562.htm
- http://m.3g.gqskj.cn/xnews/898398.htm
- http://m.3g.gqskj.cn/xnews/7175395.htm
- http://m.3g.gqskj.cn/xnews/6852491.htm
- http://m.3g.gqskj.cn/xnews/4839.htm
- http://m.3g.gqskj.cn/xnews/3069.htm
- http://m.3g.gqskj.cn/xnews/8852575.htm
- http://m.3g.gqskj.cn/xnews/5957.htm
- http://m.3g.gqskj.cn/xnews/1188331.htm
- http://m.3g.gqskj.cn/xnews/4810.htm
- http://m.3g.gqskj.cn/xnews/6085.htm
- http://m.3g.gqskj.cn/xnews/0197.htm
- http://m.3g.gqskj.cn/xnews/6849341.htm
- http://m.3g.gqskj.cn/xnews/615117.htm
- http://m.3g.gqskj.cn/xnews/7092.htm
- http://m.3g.gqskj.cn/xnews/4227199.htm
- http://m.3g.gqskj.cn/xnews/9664164.htm
- http://m.3g.gqskj.cn/xnews/5087515.htm
- http://m.3g.gqskj.cn/xnews/31114.htm
- http://m.3g.gqskj.cn/xnews/2494078.htm
- http://m.3g.gqskj.cn/xnews/42096.htm
- http://m.3g.gqskj.cn/xnews/2654.htm
- http://m.3g.gqskj.cn/xnews/37132.htm
- http://m.3g.gqskj.cn/xnews/92298.htm
- http://m.3g.gqskj.cn/xnews/34247.htm
- http://m.3g.gqskj.cn/xnews/6113.htm
- http://m.3g.gqskj.cn/xnews/8738105.htm
- http://m.3g.gqskj.cn/xnews/4807.htm
- http://m.3g.gqskj.cn/xnews/2573942.htm
- http://m.3g.gqskj.cn/xnews/7960.htm
- http://m.3g.gqskj.cn/xnews/1555.htm
- http://m.3g.gqskj.cn/xnews/891868.htm
- http://m.3g.gqskj.cn/xnews/6047569.htm
- http://m.3g.gqskj.cn/xnews/171999.htm
- http://m.3g.gqskj.cn/xnews/45896.htm
- http://m.3g.gqskj.cn/xnews/927412.htm
- http://m.3g.gqskj.cn/xnews/8985994.htm
- http://m.3g.gqskj.cn/xnews/4173.htm
- http://m.3g.gqskj.cn/xnews/9151149.htm
- http://m.3g.gqskj.cn/xnews/49495.htm
- http://m.3g.gqskj.cn/xnews/608008.htm
- http://m.3g.gqskj.cn/xnews/3258148.htm
- http://m.3g.gqskj.cn/xnews/5268.htm
- http://m.3g.gqskj.cn/xnews/69187.htm
- http://m.3g.gqskj.cn/xnews/4151.htm
- http://m.3g.gqskj.cn/xnews/343762.htm
- http://m.3g.gqskj.cn/xnews/2714262.htm
- http://m.3g.gqskj.cn/xnews/8250750.htm
- http://m.3g.gqskj.cn/xnews/88256.htm
- http://m.3g.gqskj.cn/xnews/1858948.htm
- http://m.3g.gqskj.cn/xnews/01919.htm
- http://m.3g.gqskj.cn/xnews/713059.htm
- http://m.3g.gqskj.cn/xnews/8267.htm
- http://m.3g.gqskj.cn/xnews/3434.htm
- http://m.3g.gqskj.cn/xnews/8198.htm
- http://m.3g.gqskj.cn/xnews/5792.htm
- http://m.3g.gqskj.cn/xnews/98582.htm
- http://m.3g.gqskj.cn/xnews/1111234.htm
- http://m.3g.gqskj.cn/xnews/16378.htm
- http://m.3g.gqskj.cn/xnews/9021.htm
- http://m.3g.gqskj.cn/xnews/9684041.htm
- http://m.3g.gqskj.cn/xnews/671476.htm
- http://m.3g.gqskj.cn/xnews/464826.htm
- http://m.3g.gqskj.cn/xnews/991390.htm
- http://m.3g.gqskj.cn/xnews/034876.htm
- http://m.3g.gqskj.cn/xnews/26234.htm
- http://m.3g.gqskj.cn/xnews/98824.htm
- http://m.3g.gqskj.cn/xnews/7901391.htm
- http://m.3g.gqskj.cn/xnews/732005.htm
- http://m.3g.gqskj.cn/xnews/67977.htm
- http://m.3g.gqskj.cn/xnews/013368.htm
- http://m.3g.gqskj.cn/xnews/335326.htm
- http://m.3g.gqskj.cn/xnews/184879.htm
- http://m.3g.gqskj.cn/xnews/59873.htm
- http://m.3g.gqskj.cn/xnews/6117555.htm
- http://m.3g.gqskj.cn/xnews/75995.htm
- http://m.3g.gqskj.cn/xnews/528507.htm
- http://m.3g.gqskj.cn/xnews/87077.htm
- http://m.3g.gqskj.cn/xnews/4667.htm
- http://m.3g.gqskj.cn/xnews/5960772.htm
- http://m.3g.gqskj.cn/xnews/207387.htm
- http://m.3g.gqskj.cn/xnews/154109.htm
- http://m.3g.gqskj.cn/xnews/562076.htm
- http://m.3g.gqskj.cn/xnews/8011112.htm
- http://m.3g.gqskj.cn/xnews/11936.htm
- http://m.3g.gqskj.cn/xnews/00093.htm
- http://m.3g.gqskj.cn/xnews/6325.htm
- http://m.3g.gqskj.cn/xnews/5701201.htm
- http://m.3g.gqskj.cn/xnews/3421.htm
- http://m.3g.gqskj.cn/xnews/5230139.htm
- http://m.3g.gqskj.cn/xnews/402524.htm
- http://m.3g.gqskj.cn/xnews/02192.htm
- http://m.3g.gqskj.cn/xnews/3477879.htm
- http://m.3g.gqskj.cn/xnews/2915.htm
- http://m.3g.gqskj.cn/xnews/8311.htm
- http://m.3g.gqskj.cn/xnews/649431.htm
- http://m.3g.gqskj.cn/xnews/04823.htm
- http://m.3g.gqskj.cn/xnews/3636.htm
- http://m.3g.gqskj.cn/xnews/4251356.htm
- http://m.3g.gqskj.cn/xnews/3440.htm
- http://m.3g.gqskj.cn/xnews/381089.htm
- http://m.3g.gqskj.cn/xnews/6177572.htm
- http://m.3g.gqskj.cn/xnews/2236.htm
- http://m.3g.gqskj.cn/xnews/675369.htm
- http://m.3g.gqskj.cn/xnews/4732.htm
- http://m.3g.gqskj.cn/xnews/9824.htm
- http://m.3g.gqskj.cn/xnews/24701.htm
- http://m.3g.gqskj.cn/xnews/0758.htm
- http://m.3g.gqskj.cn/xnews/91434.htm
- http://m.3g.gqskj.cn/xnews/1004.htm
- http://m.3g.gqskj.cn/xnews/4157302.htm
- http://m.3g.gqskj.cn/xnews/10347.htm
- http://m.3g.gqskj.cn/xnews/2824.htm
- http://m.3g.gqskj.cn/xnews/31468.htm
- http://m.3g.gqskj.cn/xnews/83541.htm
- http://m.3g.gqskj.cn/xnews/1636969.htm
- http://m.3g.gqskj.cn/xnews/056110.htm
- http://m.3g.gqskj.cn/xnews/022629.htm
- http://m.3g.gqskj.cn/xnews/9235937.htm
- http://m.3g.gqskj.cn/xnews/458983.htm
- http://m.3g.gqskj.cn/xnews/8088.htm
- http://m.3g.gqskj.cn/xnews/094057.htm
- http://m.3g.gqskj.cn/xnews/863345.htm
- http://m.3g.gqskj.cn/xnews/9480723.htm
- http://m.3g.gqskj.cn/xnews/3448772.htm
- http://m.3g.gqskj.cn/xnews/0946993.htm
- http://m.3g.gqskj.cn/xnews/508506.htm
- http://m.3g.gqskj.cn/xnews/220513.htm
- http://m.3g.gqskj.cn/xnews/370135.htm
- http://m.3g.gqskj.cn/xnews/8340345.htm
- http://m.3g.gqskj.cn/xnews/1082694.htm
- http://m.3g.gqskj.cn/xnews/9058.htm
- http://m.3g.gqskj.cn/xnews/6615.htm
- http://m.3g.gqskj.cn/xnews/3248722.htm
- http://m.3g.gqskj.cn/xnews/2028.htm
- http://m.3g.gqskj.cn/xnews/57436.htm
- http://m.3g.gqskj.cn/xnews/9776.htm
- http://m.3g.gqskj.cn/xnews/56862.htm
- http://m.3g.gqskj.cn/xnews/22522.htm
- http://m.3g.gqskj.cn/xnews/6789372.htm
- http://m.3g.gqskj.cn/xnews/96786.htm
- http://m.3g.gqskj.cn/xnews/319412.htm
- http://m.3g.gqskj.cn/xnews/3543.htm

## 项目结构

```text
newslink-indexer/
├── config/                                 # 配置文件目录
│   ├── config.yaml.example                 # 示例配置文件，包含数据库、调度、日志等参数
│   └── logging.conf                        # 日志格式与输出级别配置
├── docs/                                   # 项目文档目录
│   ├── getting_started.md                  # 快速入门指南，涵盖安装与首次运行
│   ├── operations.md                       # 运维与部署相关文档
│   ├── development.md                      # 开发者指南，包含代码规范与提交流程
│   └── api_reference.md                    # 完整 API 接口文档
├── newslink_indexer/                       # 核心源码包
│   ├── __init__.py                         # 包初始化，版本号定义
│   ├── cli.py                              # 命令行入口，处理子命令解析与路由
│   ├── parser.py                           # 链接解析与校验模块，负责 ID 提取与格式清洗
│   ├── probe.py                            # 可用性探测模块，执行 HTTP 请求与超时控制
│   ├── indexer.py                          # 索引构建核心逻辑，包含增量更新与去重
│   ├── scheduler.py                        # 定时任务调度器，基于 apscheduler 实现
│   ├── storage.py                          # 存储适配层，包含 SQLAlchemy 模型与 CRUD 操作
│   ├── metadata.py                         # 元数据抽取规则集，包含正则表达式与分类映射
│   ├── reporter.py                         # 报告生成器，输出 JSON 与 Markdown 格式统计
│   └── utils.py                            # 通用工具函数，如日期转换、哈希计算与重试装饰器
├── tests/                                  # 单元测试与集成测试目录
│   ├── run_all.py                          # 测试执行入口，调用 pytest 运行全部用例
│   ├── test_parser.py                      # 针对解析模块的边界条件与异常用例
│   ├── test_probe.py                       # 探测模块的模拟响应测试与超时场景
│   └── test_storage.py                     # 存储模块的内存数据库测试与事务回滚验证
├── scripts/                                # 运维与辅助脚本目录
│   ├── init_db.sql                         # 数据库初始化脚本（MySQL/PostgreSQL 通用）
│   ├── migrate_v1_to_v2.sql                # 版本迁移脚本，用于升级已有数据库结构
│   └── sample_links.txt                    # 示例链接列表，供快速测试使用
├── requirements.txt                        # 生产环境依赖列表
├── requirements-dev.txt                    # 开发环境额外依赖，包含 pytest 与 black
├── setup.py                                # 项目打包与分发配置
├── LICENSE                                 # MIT 许可证文件
└── README.md                               # 项目首页文档，即当前文件
```

## 贡献指南

提交问题报告与功能请求 在 GitHub Issues 页面创建新议题时，请选择对应的模板类型，并详细描述复现步骤、预期行为与实际行为。对于功能请求，请阐明使用场景与优先级。

准备开发环境与分支策略 从 main 分支创建新的 feature/xxx 或 fix/xxx 分支进行开发。确保本地已安装所有开发依赖，并运行 pre-commit 钩子以统一代码风格。

编写测试用例与更新文档 任何新功能或修复都必须包含对应的单元测试，确保测试覆盖率达到 90% 以上。同时更新 docs 目录下相关文档，确保 API 变更同步反映至 api_reference.md。

提交 Pull Request 并参与评审 提交 PR 时请填写变更摘要、测试结果以及影响范围。至少需要一名维护者 Approve 后方可合并。对于较大变更，建议先创建设计讨论议题，与社区达成共识后再编码。

遵守行为准则与代码规范 所有贡献者需遵守项目行为准则。代码需通过 black 与 flake8 检查，变量命名遵循 PEP 8 规范，禁止提交包含敏感信息（如密钥、密码）的变更。

## 常见问题

问：索引任务运行过程中频繁出现连接超时错误，应如何调整？

答：连接超时通常由目标服务器响应缓慢或网络波动引起。建议依次尝试以下方法：1) 在 config.yaml 中增大 probe.timeout 的值（默认 10 秒，可调至 30 秒）；2) 启用 probe.retry 机制，设置重试次数为 3 次，重试间隔为 2 秒；3) 检查本地防火墙或代理设置，确保出口 IP 未被目标服务器限制。若问题持续，可考虑将调度任务分散至不同时段的低峰期执行。

问：如何将现有 SQLite 数据迁移至 MySQL 生产环境？

答：项目内置了迁移辅助脚本 scripts/migrate_v1_to_v2.sql，但该脚本仅处理表结构变更。完整的数据迁移步骤如下：1) 在 MySQL 中创建新数据库并运行 scripts/init_db.sql 初始化表结构；2) 使用 newslink_indexer.storage 模块中的 export_sqlite 工具将 SQLite 数据导出为 CSV 或 JSON 中间格式；3) 使用 import_mysql 工具将中间格式数据批量导入 MySQL。注意在迁移前先停止所有调度任务，避免数据写入冲突。

问：索引报告中的“失效链接”判定标准是什么？是否可以自定义？

答：默认判定标准基于 HTTP 响应状态码：任何返回 4xx 或 5xx 状态码的链接均标记为失效。同时，若链接在超时时间内无响应（无任何 TCP 握手或 TLS 协商完成），也计入失效。用户可在 config.yaml 的 probe.failure_criteria 下自定义状态码列表，例如将 429（Too Many Requests）视为暂时有效而非永久失效。此外，支持配置 content_type 验证，若响应内容的 MIME 类型与预期不符（如 text/html 缺失），也可作为额外失效判定条件。

## 许可证

MIT License

Copyright (c) 2026 NewsLink Indexer Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:47
