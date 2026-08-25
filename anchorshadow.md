# NewsLink Archive Gateway

NewsLink Archive Gateway 是一个面向移动端新闻资源聚合与结构化归档的开源工具集。该项目定位为技术资源与外链汇总中间件，专注于对分散在移动网络中的新闻条目、信息页面及动态内容进行统一采集、分类存储与索引管理。目标用户包括新闻聚合平台运维人员、舆情监控系统开发者、学术研究机构的数据采集工程师，以及需要批量管理移动端新闻外链的技术团队。通过标准化的数据拉取策略、可配置的过滤规则与多格式导出能力，该项目解决移动新闻链接易失效、分散异构、难以批量维护与二次分发的问题，提供一套完整的外链生命周期管理方案。

## 功能概览

批量外链采集引擎 支持基于给定种子链接列表的并发拉取，自动处理移动端页面跳转与重定向逻辑。

结构化元数据抽取 从每个新闻页面中提取标题、发布时间、正文摘要、来源机构及关键词，输出为 JSON 或 CSV 格式。

链接健康度巡检 定时检测已归档外链的可访问状态，标记 4xx、5xx 及超时响应，生成异常报告。

分类标签自动映射 基于 URL 路径特征与内容关键词匹配，为每条外链打上地区、类别与热度等级标签。

增量更新与去重机制 通过内容哈希与指纹比对，避免重复收录相同新闻实体，支持仅拉取新增或变更条目。

多格式数据导出 支持将归档结果导出为 SQLite 数据库、Elasticsearch 批量索引文件或纯文本列表，便于下游系统集成。

访问统计与查询接口 提供轻量级 HTTP API，支持按日期、关键词、状态码等条件检索已归档链接，返回分页结果。

## 应用场景

舆情监控系统数据源构建 舆情分析团队可将本工具部署为定时任务，每日拉取指定移动新闻站点的最新文章列表，将结构化数据推送至 Kafka 或 RabbitMQ，供后续情感分析与热点识别模块使用。通过健康度巡检功能，可及时发现数据源变动，避免采集断层。

学术研究中的新闻语料采集 社会科学研究人员利用本工具批量归档特定时间段内的移动新闻外链，抽取正文纯文本作为语料库基础，配合标签映射功能按主题分类，支撑内容分析与传播路径研究。

新闻聚合平台的中间层缓存 新闻 App 或门户网站的后端服务可集成本工具的 API，将第三方移动新闻链接统一转为内部结构化数据，减少对外部站点的实时依赖，同时利用去重机制降低存储冗余，提升响应速度。

历史链接归档与迁移辅助 企业内容管理部门在系统升级或更换 CMS 时，通过本工具批量导出历史新闻外链的元数据与状态记录，生成迁移清单，辅助验证新系统中的链接可用性，降低数据迁移风险。

## 快速开始

以下命令展示从克隆仓库到启动服务的完整流程。

```bash
git clone https://github.com/yourorg/newslink-archive-gateway.git
cd newslink-archive-gateway
pip install -r requirements.txt
cp config.example.yaml config.yaml
python scripts/init_db.py
python main.py --input seeds.txt --output ./archive --format json
```

其中 seeds.txt 为每行一个 URL 的种子列表文件。执行后将在 archive 目录下生成带时间戳的结果文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，推荐使用 pyenv 管理版本 |
| SQLite | 3.35 及以上 | 内置元数据存储引擎，用于去重与状态管理 |
| lxml | 4.9.0 及以上 | HTML 解析与 XPath 查询依赖，用于内容抽取 |
| requests | 2.28.0 及以上 | HTTP 会话管理与连接池，处理移动端请求头 |
| pyyaml | 6.0 及以上 | 配置文件解析，支持自定义采集规则 |
| aiohttp | 3.8.0 及以上 | 可选依赖，启用异步并发采集模式时使用 |
| elasticsearch | 8.0 及以上 | 可选依赖，用于导出索引文件或直接写入 ES |
| pytest | 7.0 及以上 | 开发测试依赖，运行单元测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速配置种子列表、运行首次采集并导出结果？ |
| 配置参考 | docs/configuration.md | config.yaml 中每个字段的含义、默认值与调优建议是什么？ |
| API 手册 | docs/api_reference.md | HTTP 查询接口的端点、参数格式、返回结构及错误码有哪些？ |
| 数据模型 | docs/data_model.md | 内部使用的链接记录、元数据、状态快照的字段定义与关联关系如何？ |
| 扩展开发 | docs/extension_guide.md | 如何自定义抽取规则、新增输出格式或接入其他存储后端？ |
| 运维指南 | docs/operations.md | 如何设置定时任务、监控队列积压及恢复异常中断的批次？ |

## 资源列表

- http://m.3g.fcful.cn/snews/872982.htm
- http://m.3g.fcful.cn/snews/67527.htm
- http://m.3g.fcful.cn/snews/2725.htm
- http://m.3g.fcful.cn/snews/30488.htm
- http://m.3g.fcful.cn/snews/91041.htm
- http://m.3g.fcful.cn/snews/9408090.htm
- http://m.3g.fcful.cn/snews/55006.htm
- http://m.3g.fcful.cn/snews/440198.htm
- http://m.3g.fcful.cn/snews/0264.htm
- http://m.3g.fcful.cn/snews/4612840.htm
- http://m.3g.fcful.cn/snews/7092193.htm
- http://m.3g.fcful.cn/snews/6060.htm
- http://m.3g.fcful.cn/snews/4431345.htm
- http://m.3g.fcful.cn/snews/7210.htm
- http://m.3g.fcful.cn/snews/3288.htm
- http://m.3g.fcful.cn/snews/766511.htm
- http://m.3g.fcful.cn/snews/6342769.htm
- http://m.3g.fcful.cn/snews/64854.htm
- http://m.3g.fcful.cn/snews/2415.htm
- http://m.3g.fcful.cn/snews/7296200.htm
- http://m.3g.fcful.cn/snews/23263.htm
- http://m.3g.fcful.cn/snews/4017564.htm
- http://m.3g.fcful.cn/snews/07455.htm
- http://m.3g.fcful.cn/snews/07496.htm
- http://m.3g.fcful.cn/snews/526150.htm
- http://m.3g.fcful.cn/snews/5018363.htm
- http://m.3g.fcful.cn/snews/1032565.htm
- http://m.3g.fcful.cn/snews/804015.htm
- http://m.3g.fcful.cn/snews/0239.htm
- http://m.3g.fcful.cn/snews/6744801.htm
- http://m.3g.fcful.cn/snews/472135.htm
- http://m.3g.fcful.cn/snews/16535.htm
- http://m.3g.fcful.cn/snews/4336720.htm
- http://m.3g.fcful.cn/snews/45188.htm
- http://m.3g.fcful.cn/snews/361227.htm
- http://m.3g.fcful.cn/snews/3202.htm
- http://m.3g.fcful.cn/snews/705153.htm
- http://m.3g.fcful.cn/snews/2247586.htm
- http://m.3g.fcful.cn/snews/164898.htm
- http://m.3g.fcful.cn/snews/96503.htm
- http://m.3g.fcful.cn/snews/8998.htm
- http://m.3g.fcful.cn/snews/1950437.htm
- http://m.3g.fcful.cn/snews/478161.htm
- http://m.3g.fcful.cn/snews/240783.htm
- http://m.3g.fcful.cn/snews/316056.htm
- http://m.3g.fcful.cn/snews/893557.htm
- http://m.3g.fcful.cn/snews/168898.htm
- http://m.3g.fcful.cn/snews/5707046.htm
- http://m.3g.fcful.cn/snews/696250.htm
- http://m.3g.fcful.cn/snews/021917.htm
- http://m.3g.fcful.cn/snews/1083987.htm
- http://m.3g.fcful.cn/snews/1587737.htm
- http://m.3g.fcful.cn/snews/99988.htm
- http://m.3g.fcful.cn/snews/7150.htm
- http://m.3g.fcful.cn/snews/9145222.htm
- http://m.3g.fcful.cn/snews/3759640.htm
- http://m.3g.fcful.cn/snews/92654.htm
- http://m.3g.fcful.cn/snews/1127387.htm
- http://m.3g.fcful.cn/snews/51386.htm
- http://m.3g.fcful.cn/snews/241795.htm
- http://m.3g.fcful.cn/snews/47997.htm
- http://m.3g.fcful.cn/snews/73465.htm
- http://m.3g.fcful.cn/snews/489108.htm
- http://m.3g.fcful.cn/snews/40541.htm
- http://m.3g.fcful.cn/snews/7730506.htm
- http://m.3g.fcful.cn/snews/8711.htm
- http://m.3g.fcful.cn/snews/8033835.htm
- http://m.3g.fcful.cn/snews/9281291.htm
- http://m.3g.fcful.cn/snews/5400204.htm
- http://m.3g.fcful.cn/snews/373880.htm
- http://m.3g.fcful.cn/snews/3481827.htm
- http://m.3g.fcful.cn/snews/725277.htm
- http://m.3g.fcful.cn/snews/7249955.htm
- http://m.3g.fcful.cn/snews/967577.htm
- http://m.3g.fcful.cn/snews/55210.htm
- http://m.3g.fcful.cn/snews/40555.htm
- http://m.3g.fcful.cn/snews/132255.htm
- http://m.3g.fcful.cn/snews/0614668.htm
- http://m.3g.fcful.cn/snews/86181.htm
- http://m.3g.fcful.cn/snews/7053677.htm
- http://m.3g.fcful.cn/snews/943224.htm
- http://m.3g.fcful.cn/snews/941831.htm
- http://m.3g.fcful.cn/snews/521130.htm
- http://m.3g.fcful.cn/snews/72444.htm
- http://m.3g.fcful.cn/snews/13929.htm
- http://m.3g.fcful.cn/snews/4299939.htm
- http://m.3g.fcful.cn/snews/565187.htm
- http://m.3g.fcful.cn/snews/2550256.htm
- http://m.3g.fcful.cn/snews/87278.htm
- http://m.3g.fcful.cn/snews/481571.htm
- http://m.3g.fcful.cn/snews/69877.htm
- http://m.3g.fcful.cn/snews/9268.htm
- http://m.3g.fcful.cn/snews/04427.htm
- http://m.3g.fcful.cn/snews/37103.htm
- http://m.3g.fcful.cn/snews/416526.htm
- http://m.3g.fcful.cn/snews/844618.htm
- http://m.3g.fcful.cn/snews/243811.htm
- http://m.3g.fcful.cn/snews/878206.htm
- http://m.3g.fcful.cn/snews/964121.htm
- http://m.3g.fcful.cn/snews/283304.htm
- http://m.3g.fcful.cn/snews/534824.htm
- http://m.3g.fcful.cn/snews/7728384.htm
- http://m.3g.fcful.cn/snews/3633821.htm
- http://m.3g.fcful.cn/snews/39242.htm
- http://m.3g.fcful.cn/snews/4510.htm
- http://m.3g.fcful.cn/snews/57384.htm
- http://m.3g.fcful.cn/snews/9774.htm
- http://m.3g.fcful.cn/snews/6245.htm
- http://m.3g.fcful.cn/snews/4704103.htm
- http://m.3g.fcful.cn/snews/649286.htm
- http://m.3g.fcful.cn/snews/7928331.htm
- http://m.3g.fcful.cn/snews/3862.htm
- http://m.3g.fcful.cn/snews/73362.htm
- http://m.3g.fcful.cn/snews/5414708.htm
- http://m.3g.fcful.cn/snews/6493.htm
- http://m.3g.fcful.cn/snews/5592.htm
- http://m.3g.fcful.cn/snews/13892.htm
- http://m.3g.fcful.cn/snews/167943.htm
- http://m.3g.fcful.cn/snews/18812.htm
- http://m.3g.fcful.cn/snews/6843147.htm
- http://m.3g.fcful.cn/snews/1015075.htm
- http://m.3g.fcful.cn/snews/22265.htm
- http://m.3g.fcful.cn/snews/22902.htm
- http://m.3g.fcful.cn/snews/984967.htm
- http://m.3g.fcful.cn/snews/169315.htm
- http://m.3g.fcful.cn/snews/8113.htm
- http://m.3g.fcful.cn/snews/852266.htm
- http://m.3g.fcful.cn/snews/27335.htm
- http://m.3g.fcful.cn/snews/79467.htm
- http://m.3g.fcful.cn/snews/6748619.htm
- http://m.3g.fcful.cn/snews/43751.htm
- http://m.3g.fcful.cn/snews/1127.htm
- http://m.3g.fcful.cn/snews/2487.htm
- http://m.3g.fcful.cn/snews/41202.htm
- http://m.3g.fcful.cn/snews/968290.htm
- http://m.3g.fcful.cn/snews/01200.htm
- http://m.3g.fcful.cn/snews/4711.htm
- http://m.3g.fcful.cn/snews/1898.htm
- http://m.3g.fcful.cn/snews/0758820.htm
- http://m.3g.fcful.cn/snews/592240.htm
- http://m.3g.fcful.cn/snews/5873119.htm
- http://m.3g.fcful.cn/snews/9980.htm
- http://m.3g.fcful.cn/snews/5826918.htm
- http://m.3g.fcful.cn/snews/913188.htm
- http://m.3g.fcful.cn/snews/817481.htm
- http://m.3g.fcful.cn/snews/4104.htm
- http://m.3g.fcful.cn/snews/9487.htm
- http://m.3g.fcful.cn/snews/70035.htm
- http://m.3g.fcful.cn/snews/1984051.htm
- http://m.3g.fcful.cn/snews/8786656.htm
- http://m.3g.fcful.cn/snews/7200820.htm
- http://m.3g.fcful.cn/snews/949601.htm
- http://m.3g.fcful.cn/snews/848380.htm
- http://m.3g.fcful.cn/snews/7193096.htm
- http://m.3g.fcful.cn/snews/7226.htm
- http://m.3g.fcful.cn/snews/8891820.htm
- http://m.3g.fcful.cn/snews/42415.htm
- http://m.3g.fcful.cn/snews/04454.htm
- http://m.3g.fcful.cn/snews/74263.htm
- http://m.3g.fcful.cn/snews/0351674.htm
- http://m.3g.fcful.cn/snews/4575.htm
- http://m.3g.fcful.cn/snews/5248.htm
- http://m.3g.fcful.cn/snews/54414.htm
- http://m.3g.fcful.cn/snews/7853659.htm
- http://m.3g.fcful.cn/snews/1986.htm
- http://m.3g.fcful.cn/snews/353026.htm
- http://m.3g.fcful.cn/snews/33549.htm
- http://m.3g.fcful.cn/snews/6452792.htm
- http://m.3g.fcful.cn/snews/9439.htm
- http://m.3g.fcful.cn/snews/46506.htm
- http://m.3g.fcful.cn/snews/4581831.htm
- http://m.3g.fcful.cn/snews/727814.htm
- http://m.3g.fcful.cn/snews/39524.htm
- http://m.3g.fcful.cn/snews/7784092.htm
- http://m.3g.fcful.cn/snews/428526.htm
- http://m.3g.fcful.cn/snews/7267217.htm
- http://m.3g.fcful.cn/snews/641353.htm
- http://m.3g.fcful.cn/snews/971086.htm
- http://m.3g.fcful.cn/snews/900454.htm
- http://m.3g.fcful.cn/snews/3424768.htm
- http://m.3g.fcful.cn/snews/662936.htm
- http://m.3g.fcful.cn/snews/5626655.htm
- http://m.3g.fcful.cn/snews/91990.htm
- http://m.3g.fcful.cn/snews/29185.htm
- http://m.3g.fcful.cn/snews/0656.htm
- http://m.3g.fcful.cn/snews/3732066.htm
- http://m.3g.fcful.cn/snews/4295.htm
- http://m.3g.fcful.cn/snews/44805.htm
- http://m.3g.fcful.cn/snews/369142.htm
- http://m.3g.fcful.cn/snews/3105672.htm
- http://m.3g.fcful.cn/snews/8345302.htm
- http://m.3g.fcful.cn/snews/4453296.htm
- http://m.3g.fcful.cn/snews/0625782.htm
- http://m.3g.fcful.cn/snews/3661.htm
- http://m.3g.fcful.cn/snews/2424.htm
- http://m.3g.fcful.cn/snews/4874261.htm
- http://m.3g.fcful.cn/snews/4515.htm
- http://m.3g.fcful.cn/snews/1746552.htm
- http://m.3g.fcful.cn/snews/16719.htm
- http://m.3g.fcful.cn/snews/9134.htm
- http://m.3g.fcful.cn/snews/4425046.htm
- http://m.3g.fcful.cn/snews/3661925.htm
- http://m.3g.fcful.cn/snews/107829.htm
- http://m.3g.fcful.cn/snews/3381.htm
- http://m.3g.fcful.cn/snews/3678.htm
- http://m.3g.fcful.cn/snews/274243.htm
- http://m.3g.fcful.cn/snews/436308.htm
- http://m.3g.fcful.cn/snews/5627382.htm
- http://m.3g.fcful.cn/snews/7568847.htm
- http://m.3g.fcful.cn/snews/69370.htm
- http://m.3g.fcful.cn/snews/9965823.htm
- http://m.3g.fcful.cn/snews/3582798.htm
- http://m.3g.fcful.cn/snews/327479.htm
- http://m.3g.fcful.cn/snews/59655.htm
- http://m.3g.fcful.cn/snews/5112.htm
- http://m.3g.fcful.cn/snews/379885.htm
- http://m.3g.fcful.cn/snews/8637.htm
- http://m.3g.fcful.cn/snews/23783.htm
- http://m.3g.fcful.cn/snews/399483.htm
- http://m.3g.fcful.cn/snews/0169628.htm
- http://m.3g.fcful.cn/snews/269177.htm
- http://m.3g.fcful.cn/snews/7298.htm
- http://m.3g.fcful.cn/snews/5729.htm
- http://m.3g.fcful.cn/snews/28800.htm
- http://m.3g.fcful.cn/snews/7676.htm
- http://m.3g.fcful.cn/snews/4996013.htm
- http://m.3g.fcful.cn/snews/9691.htm
- http://m.3g.fcful.cn/snews/6157669.htm
- http://m.3g.fcful.cn/snews/5495840.htm
- http://m.3g.fcful.cn/snews/4470.htm
- http://m.3g.fcful.cn/snews/2231225.htm
- http://m.3g.fcful.cn/snews/950567.htm
- http://m.3g.fcful.cn/snews/3745.htm
- http://m.3g.fcful.cn/snews/8992.htm
- http://m.3g.fcful.cn/snews/4403953.htm
- http://m.3g.fcful.cn/snews/8564.htm
- http://m.3g.fcful.cn/snews/66422.htm
- http://m.3g.fcful.cn/snews/9475660.htm
- http://m.3g.fcful.cn/snews/386220.htm
- http://m.3g.fcful.cn/snews/5292033.htm
- http://m.3g.fcful.cn/snews/3667298.htm
- http://m.3g.fcful.cn/snews/5582.htm
- http://m.3g.fcful.cn/snews/2126.htm
- http://m.3g.fcful.cn/snews/529346.htm
- http://m.3g.fcful.cn/snews/1184.htm
- http://m.3g.fcful.cn/snews/742749.htm
- http://m.3g.fcful.cn/snews/3523.htm
- http://m.3g.fcful.cn/snews/79614.htm
- http://m.3g.fcful.cn/snews/136422.htm
- http://m.3g.fcful.cn/snews/26731.htm

## 项目结构

```
newslink-archive-gateway/
├── main.py                         # 程序入口，解析命令行参数并调度采集流程
├── config.yaml                     # 主配置文件，包含并发数、超时、过滤规则及存储路径
├── requirements.txt                # Python 依赖列表，分为核心与可选两组
├── seeds.txt                       # 种子链接样例文件，每行一个 URL，供初始测试使用
├── archive/                        # 默认输出目录，按日期生成子文件夹存放结果
│   ├── 2026-08-25/                 # 按采集日期分组的归档批次
│   │   ├── manifest.json           # 批次元数据，含时间戳、种子总数、成功数
│   │   └── data/                   # 具体条目文件，按 id 分片存储
│   └── exports/                    # 导出目录，存放转换后的 CSV/ES 格式文件
├── core/                           # 核心业务逻辑模块
│   ├── fetcher.py                  # 异步与同步请求封装，含重试与代理切换
│   ├── parser.py                   # 基于 lxml 的 HTML 抽取器，定义默认字段映射
│   ├── deduper.py                  # 布隆过滤器与哈希比对去重实现
│   └── health.py                   # 链接状态巡检与告警触发器
├── storage/                        # 存储适配器层
│   ├── sqlite_store.py             # SQLite 本地存储操作，含建表语句与索引
│   ├── es_exporter.py              # Elasticsearch 批量索引生成与直接写入
│   └── file_writer.py              # JSON/CSV/纯文本文件输出工具
├── api/                            # 轻量级 HTTP 查询服务
│   ├── app.py                      # Flask/FastAPI 应用工厂
│   ├── routes.py                   # 搜索、统计、状态查询路由定义
│   └── schemas.py                  # 请求与响应数据模型校验
├── scripts/                        # 辅助运维脚本
│   ├── init_db.py                  # 初始化 SQLite 表结构与默认配置
│   ├── cron_daily.sh               # 每日定时采集的 shell 包装脚本
│   └── migrate_v1_to_v2.py         # 数据模型升级迁移工具
├── tests/                          # 单元测试与集成测试
│   ├── test_fetcher.py             # 模拟移动端请求的 HTTP 拉取测试
│   ├── test_parser.py              # 针对不同页面结构的抽取覆盖率测试
│   └── test_deduper.py             # 去重算法准确率与性能基准测试
└── docs/                           # 完整文档目录
    ├── quickstart.md
    ├── configuration.md
    ├── api_reference.md
    ├── data_model.md
    ├── extension_guide.md
    └── operations.md
```

## 贡献指南

1. 阅读项目根目录下的 CONTRIBUTING.md 文件，了解代码风格规范、提交信息格式及分支管理策略。所有 Pull Request 必须关联一个已登记的 Issue，并在描述中说明测试覆盖情况。

2. 从标记为 good-first-issue 或 help-wanted 的标签中选取任务，在 Issue 下回复认领以避免重复工作。核心模块的变更需先通过讨论帖达成初步共识，再着手编码。

3. 在本地开发环境中运行 make test 或 pytest tests/ 确保所有现有用例通过。新增功能需在 tests/ 对应子目录下补充至少两个用例：一个正常路径，一个异常路径。

4. 提交前执行 make lint 和 make format 以统一代码格式（基于 black 和 ruff）。提交信息需遵循 类型(范围): 简短描述 的模板，例如 feat(parser): 增加对 article 标签的 fallback 抽取逻辑。

5. 发起 Pull Request 后，维护者将在 48 小时内进行首次审查。如涉及配置变更或新增依赖，请在 PR 描述中明确影响范围与回滚方案。合并后 CI 将自动构建并发布至 PyPI 测试仓库。

## 常见问题

问：采集过程中遇到大量 403 或 429 状态码，如何调整策略？

答：这类响应通常由目标站点的反爬机制触发。建议在 config.yaml 中调整以下参数：降低并发数（max_concurrency）、增大请求间隔（request_delay）、启用随机 User-Agent 轮换（user_agent_pool），并配置代理列表（proxy_list）。此外，可将 health 模块的巡检频率调低，避免短时间内重复触发封锁。若仍无法解决，可启用 fetcher 中的浏览器指纹模拟选项（需额外安装 playwright）。

问：如何将已归档的数据迁移至其他数据库或全文检索引擎？

答：本工具提供多格式导出能力。若目标为 Elasticsearch，可使用 storage/es_exporter.py 直接生成批量索引文件，或通过 api 模块的导出端点触发异步写入。若需迁移至 PostgreSQL 或 MongoDB，建议先用 file_writer 输出 CSV 或 JSON 中间文件，再使用目标数据库的导入工具。对于超过 10 万条记录的大批量数据，推荐分页导出并开启压缩模式以节省磁盘 I/O。

问：项目是否支持自定义抽取字段，例如作者、点赞数或地理位置？

答：支持。用户可在 config.yaml 的 custom_fields 部分定义新字段名及其 XPath 或 CSS 选择器。parser 模块会在初始化时自动加载这些规则，并将抽取结果合并到每条记录的 extra 字典中。若需要更复杂的抽取逻辑（如调用外部 NLP 服务抽取实体），可在 extension_guide.md 的指导下编写自定义抽取插件，并在 config.yaml 中激活。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
