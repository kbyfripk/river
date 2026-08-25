# GQSKJ News Aggregator

GQSKJ News Aggregator 是一个面向中文移动端资讯聚合与结构化数据抽取的开源中间件项目。该项目旨在为开发者、数据研究人员以及内容聚合平台提供一套稳定、高效的新闻链接采集与元数据标准化接口，解决移动端新闻源分散、链接结构不统一、内容提取成本高的问题。通过本项目的调度引擎和解析适配器，用户可以批量抓取指定新闻源的文章链接，并将其转换为可供下游系统使用的结构化数据。

本项目聚焦于移动端新闻链接的定时抓取、去重存储、状态监控与异常告警，适用于个人知识库构建、舆情监控系统原型开发以及新闻推荐算法的数据源准备。项目核心不依赖任何第三方闭源服务，完全基于开源技术栈构建，支持容器化部署与水平扩展。

## 功能概览

批量链接抓取: 支持基于域名前缀的批量链接扫描与抓取，可配置并发度与请求间隔，有效避免源站封禁。

结构化元数据抽取: 从抓取的 HTML 页面中自动提取标题、发布时间、正文摘要、作者及分类标签，支持自定义 XPath 与 CSS 选择器规则。

增量去重存储: 基于链接 URL 的哈希值进行增量去重，避免重复抓取，同时保留历史抓取记录与状态变更日志。

代理池集成: 支持 HTTP/HTTPS 代理池的动态切换，突破访问频率限制和地域封锁，提升抓取成功率。

异常重试与降级: 针对网络超时、HTTP 错误码及解析异常提供可配置的重试策略，并在连续失败时自动降级抓取频率。

监控告警接口: 提供 Prometheus 格式的指标暴露端点，记录抓取总数、成功数、失败数及平均响应耗时，支持接入 Grafana 可视化。

数据导出适配器: 支持将抓取结果导出为 JSON Lines、CSV 及 Parquet 格式，便于后续数据分析或导入数据仓库。

## 应用场景

舆情监测系统原型开发: 研究人员或产品经理可使用本项目快速采集特定新闻源的文章链接与元数据，构建小规模舆情监测看板，验证关键词预警与情感分析算法的可行性。

新闻推荐算法训练数据准备: 算法工程师可将本项目作为数据管道的第一环节，定时抓取新闻链接并提取文本摘要，结合用户行为日志构造训练样本，用于内容召回与排序模型训练。

个人知识库自动归档: 个人开发者可部署本项目并结合定时任务，每日抓取关注的新闻站点文章链接，通过元数据筛选后自动推送到阅读列表或笔记软件，实现资讯的自动化归档。

第三方内容迁移辅助工具: 在进行网站迁移或内容整合时，可使用本项目批量导出指定域名的历史文章链接及元数据，生成迁移清单或结构化索引文件。

## 快速开始

以下指令演示如何在 Linux 或 macOS 环境下从源码启动 GQSKJ News Aggregator。

```bash
# 克隆项目仓库
git clone https://github.com/gqskj-news-aggregator/gqskj-aggregator.git
cd gqskj-aggregator

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 复制示例配置文件并修改数据库连接与抓取目标
cp config.example.yaml config.yaml

# 初始化 SQLite 数据库表结构
python scripts/init_db.py

# 启动调度器（默认抓取配置中定义的新闻源）
python scheduler.py --config config.yaml
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 项目核心运行环境，低于 3.9 版本将无法兼容类型注解语法 |
| SQLite | 3.35 及以上 | 默认元数据存储引擎，支持 JSON 字段存储扩展属性 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于发送抓取请求及处理响应 |
| lxml | 4.9.0 及以上 | HTML/XML 解析引擎，用于 XPath 与 CSS 选择器数据抽取 |
| pyyaml | 6.0 及以上 | YAML 配置文件解析，用于加载调度策略与源站规则 |
| prometheus-client | 0.16.0 及以上 | 可选依赖，用于暴露监控指标端点 |
| redis | 6.2 及以上 | 可选依赖，用于分布式去重锁与任务队列共享 |
| docker | 20.10 及以上 | 可选依赖，用于容器化构建与一键部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何配置新闻源规则、设置抓取频率、调整并发参数及查看运行日志 |
| 开发指南 | docs/developer_guide.md | 如何扩展新的解析适配器、自定义元数据抽取逻辑以及贡献代码规范 |
| 部署运维 | docs/deployment.md | 如何使用 Docker Compose 进行单机部署、配置反向代理以及数据备份策略 |
| API 参考 | docs/api_reference.md | 调度器、解析器与存储模块的 Python API 文档，包含类与方法签名说明 |
| 常见问题 | docs/faq.md | 抓取超时处理、代理配置故障排除、数据库锁异常及性能调优建议 |
| 变更日志 | CHANGELOG.md | 各版本迭代的功能新增、缺陷修复与破坏性变更说明 |

## 资源列表

- http://m.wap.gqskj.cn/snews/43703.htm
- http://m.wap.gqskj.cn/snews/1335378.htm
- http://m.wap.gqskj.cn/snews/815270.htm
- http://m.wap.gqskj.cn/snews/216759.htm
- http://m.wap.gqskj.cn/snews/53500.htm
- http://m.wap.gqskj.cn/snews/7260763.htm
- http://m.wap.gqskj.cn/snews/4269512.htm
- http://m.wap.gqskj.cn/snews/9094690.htm
- http://m.wap.gqskj.cn/snews/6151.htm
- http://m.wap.gqskj.cn/snews/6742.htm
- http://m.wap.gqskj.cn/snews/3122.htm
- http://m.wap.gqskj.cn/snews/5388622.htm
- http://m.wap.gqskj.cn/snews/46757.htm
- http://m.wap.gqskj.cn/snews/60570.htm
- http://m.wap.gqskj.cn/snews/6335370.htm
- http://m.wap.gqskj.cn/snews/3799.htm
- http://m.wap.gqskj.cn/snews/550507.htm
- http://m.wap.gqskj.cn/snews/6970.htm
- http://m.wap.gqskj.cn/snews/6542.htm
- http://m.wap.gqskj.cn/snews/74366.htm
- http://m.wap.gqskj.cn/snews/83230.htm
- http://m.wap.gqskj.cn/snews/8934273.htm
- http://m.wap.gqskj.cn/snews/6124443.htm
- http://m.wap.gqskj.cn/snews/7509803.htm
- http://m.wap.gqskj.cn/snews/6711468.htm
- http://m.wap.gqskj.cn/snews/1781879.htm
- http://m.wap.gqskj.cn/snews/3275141.htm
- http://m.wap.gqskj.cn/snews/16155.htm
- http://m.wap.gqskj.cn/snews/992381.htm
- http://m.wap.gqskj.cn/snews/6357.htm
- http://m.wap.gqskj.cn/snews/0850102.htm
- http://m.wap.gqskj.cn/snews/2884.htm
- http://m.wap.gqskj.cn/snews/95165.htm
- http://m.wap.gqskj.cn/snews/21365.htm
- http://m.wap.gqskj.cn/snews/331920.htm
- http://m.wap.gqskj.cn/snews/656412.htm
- http://m.wap.gqskj.cn/snews/537539.htm
- http://m.wap.gqskj.cn/snews/4908.htm
- http://m.wap.gqskj.cn/snews/9017.htm
- http://m.wap.gqskj.cn/snews/5799.htm
- http://m.wap.gqskj.cn/snews/3893.htm
- http://m.wap.gqskj.cn/snews/43861.htm
- http://m.wap.gqskj.cn/snews/1586.htm
- http://m.wap.gqskj.cn/snews/048881.htm
- http://m.wap.gqskj.cn/snews/6517581.htm
- http://m.wap.gqskj.cn/snews/1082681.htm
- http://m.wap.gqskj.cn/snews/71645.htm
- http://m.wap.gqskj.cn/snews/508614.htm
- http://m.wap.gqskj.cn/snews/727692.htm
- http://m.wap.gqskj.cn/snews/727328.htm
- http://m.wap.gqskj.cn/snews/543556.htm
- http://m.wap.gqskj.cn/snews/66769.htm
- http://m.wap.gqskj.cn/snews/381844.htm
- http://m.wap.gqskj.cn/snews/468005.htm
- http://m.wap.gqskj.cn/snews/89641.htm
- http://m.wap.gqskj.cn/snews/8599875.htm
- http://m.wap.gqskj.cn/snews/215887.htm
- http://m.wap.gqskj.cn/snews/7581208.htm
- http://m.wap.gqskj.cn/snews/84901.htm
- http://m.wap.gqskj.cn/snews/257514.htm
- http://m.wap.gqskj.cn/snews/7150.htm
- http://m.wap.gqskj.cn/snews/027451.htm
- http://m.wap.gqskj.cn/snews/405611.htm
- http://m.wap.gqskj.cn/snews/987391.htm
- http://m.wap.gqskj.cn/snews/2724688.htm
- http://m.wap.gqskj.cn/snews/1873645.htm
- http://m.wap.gqskj.cn/snews/8466.htm
- http://m.wap.gqskj.cn/snews/645991.htm
- http://m.wap.gqskj.cn/snews/8434637.htm
- http://m.wap.gqskj.cn/snews/026484.htm
- http://m.wap.gqskj.cn/snews/080173.htm
- http://m.wap.gqskj.cn/snews/9085047.htm
- http://m.wap.gqskj.cn/snews/9813.htm
- http://m.wap.gqskj.cn/snews/897090.htm
- http://m.wap.gqskj.cn/snews/4945.htm
- http://m.wap.gqskj.cn/snews/7024.htm
- http://m.wap.gqskj.cn/snews/706220.htm
- http://m.wap.gqskj.cn/snews/60645.htm
- http://m.wap.gqskj.cn/snews/3633776.htm
- http://m.wap.gqskj.cn/snews/49297.htm
- http://m.wap.gqskj.cn/snews/290971.htm
- http://m.wap.gqskj.cn/snews/7047.htm
- http://m.wap.gqskj.cn/snews/033299.htm
- http://m.wap.gqskj.cn/snews/6967672.htm
- http://m.wap.gqskj.cn/snews/36252.htm
- http://m.wap.gqskj.cn/snews/6603.htm
- http://m.wap.gqskj.cn/snews/1248.htm
- http://m.wap.gqskj.cn/snews/0831.htm
- http://m.wap.gqskj.cn/snews/6112.htm
- http://m.wap.gqskj.cn/snews/848361.htm
- http://m.wap.gqskj.cn/snews/13559.htm
- http://m.wap.gqskj.cn/snews/62461.htm
- http://m.wap.gqskj.cn/snews/0429628.htm
- http://m.wap.gqskj.cn/snews/02597.htm
- http://m.wap.gqskj.cn/snews/7169747.htm
- http://m.wap.gqskj.cn/snews/75195.htm
- http://m.wap.gqskj.cn/snews/4731.htm
- http://m.wap.gqskj.cn/snews/052223.htm
- http://m.wap.gqskj.cn/snews/9498.htm
- http://m.wap.gqskj.cn/snews/8663.htm
- http://m.wap.gqskj.cn/snews/7632570.htm
- http://m.wap.gqskj.cn/snews/5685761.htm
- http://m.wap.gqskj.cn/snews/171397.htm
- http://m.wap.gqskj.cn/snews/65303.htm
- http://m.wap.gqskj.cn/snews/006426.htm
- http://m.wap.gqskj.cn/snews/48955.htm
- http://m.wap.gqskj.cn/snews/74452.htm
- http://m.wap.gqskj.cn/snews/33075.htm
- http://m.wap.gqskj.cn/snews/34872.htm
- http://m.wap.gqskj.cn/snews/511464.htm
- http://m.wap.gqskj.cn/snews/88499.htm
- http://m.wap.gqskj.cn/snews/9927928.htm
- http://m.wap.gqskj.cn/snews/8161409.htm
- http://m.wap.gqskj.cn/snews/568634.htm
- http://m.wap.gqskj.cn/snews/49815.htm
- http://m.wap.gqskj.cn/snews/3843.htm
- http://m.wap.gqskj.cn/snews/410030.htm
- http://m.wap.gqskj.cn/snews/8814.htm
- http://m.wap.gqskj.cn/snews/5456566.htm
- http://m.wap.gqskj.cn/snews/0730541.htm
- http://m.wap.gqskj.cn/snews/107736.htm
- http://m.wap.gqskj.cn/snews/10631.htm
- http://m.wap.gqskj.cn/snews/8618802.htm
- http://m.wap.gqskj.cn/snews/6192.htm
- http://m.wap.gqskj.cn/snews/97961.htm
- http://m.wap.gqskj.cn/snews/1100.htm
- http://m.wap.gqskj.cn/snews/1609.htm
- http://m.wap.gqskj.cn/snews/5893455.htm
- http://m.wap.gqskj.cn/snews/4889099.htm
- http://m.wap.gqskj.cn/snews/806647.htm
- http://m.wap.gqskj.cn/snews/8056.htm
- http://m.wap.gqskj.cn/snews/447513.htm
- http://m.wap.gqskj.cn/snews/705920.htm
- http://m.wap.gqskj.cn/snews/1654.htm
- http://m.wap.gqskj.cn/snews/5395629.htm
- http://m.wap.gqskj.cn/snews/55998.htm
- http://m.wap.gqskj.cn/snews/6729296.htm
- http://m.wap.gqskj.cn/snews/5581077.htm
- http://m.wap.gqskj.cn/snews/2661759.htm
- http://m.wap.gqskj.cn/snews/2793.htm
- http://m.wap.gqskj.cn/snews/69938.htm
- http://m.wap.gqskj.cn/snews/53024.htm
- http://m.wap.gqskj.cn/snews/3864066.htm
- http://m.wap.gqskj.cn/snews/36517.htm
- http://m.wap.gqskj.cn/snews/0915135.htm
- http://m.wap.gqskj.cn/snews/6372458.htm
- http://m.wap.gqskj.cn/snews/4920363.htm
- http://m.wap.gqskj.cn/snews/31259.htm
- http://m.wap.gqskj.cn/snews/80161.htm
- http://m.wap.gqskj.cn/snews/14820.htm
- http://m.wap.gqskj.cn/snews/4070929.htm
- http://m.wap.gqskj.cn/snews/6934.htm
- http://m.wap.gqskj.cn/snews/6166.htm
- http://m.wap.gqskj.cn/snews/56079.htm
- http://m.wap.gqskj.cn/snews/40045.htm
- http://m.wap.gqskj.cn/snews/7654.htm
- http://m.wap.gqskj.cn/snews/3423.htm
- http://m.wap.gqskj.cn/snews/5609049.htm
- http://m.wap.gqskj.cn/snews/1654475.htm
- http://m.wap.gqskj.cn/snews/47611.htm
- http://m.wap.gqskj.cn/snews/77235.htm
- http://m.wap.gqskj.cn/snews/346889.htm
- http://m.wap.gqskj.cn/snews/6822955.htm
- http://m.wap.gqskj.cn/snews/597058.htm
- http://m.wap.gqskj.cn/snews/93124.htm
- http://m.wap.gqskj.cn/snews/0623717.htm
- http://m.wap.gqskj.cn/snews/204726.htm
- http://m.wap.gqskj.cn/snews/25440.htm
- http://m.wap.gqskj.cn/snews/3885.htm
- http://m.wap.gqskj.cn/snews/151369.htm
- http://m.wap.gqskj.cn/snews/34032.htm
- http://m.wap.gqskj.cn/snews/7416.htm
- http://m.wap.gqskj.cn/snews/597345.htm
- http://m.wap.gqskj.cn/snews/6538851.htm
- http://m.wap.gqskj.cn/snews/9747503.htm
- http://m.wap.gqskj.cn/snews/98327.htm
- http://m.wap.gqskj.cn/snews/13666.htm
- http://m.wap.gqskj.cn/snews/44215.htm
- http://m.wap.gqskj.cn/snews/154952.htm
- http://m.wap.gqskj.cn/snews/7460878.htm
- http://m.wap.gqskj.cn/snews/55960.htm
- http://m.wap.gqskj.cn/snews/0468.htm
- http://m.wap.gqskj.cn/snews/4704762.htm
- http://m.wap.gqskj.cn/snews/62718.htm
- http://m.wap.gqskj.cn/snews/8990.htm
- http://m.wap.gqskj.cn/snews/9183567.htm
- http://m.wap.gqskj.cn/snews/1013.htm
- http://m.wap.gqskj.cn/snews/1310.htm
- http://m.wap.gqskj.cn/snews/4065883.htm
- http://m.wap.gqskj.cn/snews/3414.htm
- http://m.wap.gqskj.cn/snews/778535.htm
- http://m.wap.gqskj.cn/snews/40826.htm
- http://m.wap.gqskj.cn/snews/9924.htm
- http://m.wap.gqskj.cn/snews/78079.htm
- http://m.wap.gqskj.cn/snews/92855.htm
- http://m.wap.gqskj.cn/snews/63097.htm
- http://m.wap.gqskj.cn/snews/5387652.htm
- http://m.wap.gqskj.cn/snews/187301.htm
- http://m.wap.gqskj.cn/snews/4005004.htm
- http://m.wap.gqskj.cn/snews/97802.htm
- http://m.wap.gqskj.cn/snews/567438.htm
- http://m.wap.gqskj.cn/snews/2334961.htm
- http://m.wap.gqskj.cn/snews/657352.htm
- http://m.wap.gqskj.cn/snews/4932607.htm
- http://m.wap.gqskj.cn/snews/712756.htm
- http://m.wap.gqskj.cn/snews/64027.htm
- http://m.wap.gqskj.cn/snews/78124.htm
- http://m.wap.gqskj.cn/snews/235666.htm
- http://m.wap.gqskj.cn/snews/533857.htm
- http://m.wap.gqskj.cn/snews/4048858.htm
- http://m.wap.gqskj.cn/snews/40825.htm
- http://m.wap.gqskj.cn/snews/04839.htm
- http://m.wap.gqskj.cn/snews/0874.htm
- http://m.wap.gqskj.cn/snews/0177360.htm
- http://m.wap.gqskj.cn/snews/188418.htm
- http://m.wap.gqskj.cn/snews/31661.htm
- http://m.wap.gqskj.cn/snews/2379013.htm
- http://m.wap.gqskj.cn/snews/498945.htm
- http://m.wap.gqskj.cn/snews/26116.htm
- http://m.wap.gqskj.cn/snews/97941.htm
- http://m.wap.gqskj.cn/snews/0435.htm
- http://m.wap.gqskj.cn/snews/934604.htm
- http://m.wap.gqskj.cn/snews/5388216.htm
- http://m.wap.gqskj.cn/snews/6924889.htm
- http://m.wap.gqskj.cn/snews/85656.htm
- http://m.wap.gqskj.cn/snews/5550571.htm
- http://m.wap.gqskj.cn/snews/38085.htm
- http://m.wap.gqskj.cn/snews/959816.htm
- http://m.wap.gqskj.cn/snews/56969.htm
- http://m.wap.gqskj.cn/snews/35080.htm
- http://m.wap.gqskj.cn/snews/9290018.htm
- http://m.wap.gqskj.cn/snews/3529.htm
- http://m.wap.gqskj.cn/snews/833229.htm
- http://m.wap.gqskj.cn/snews/793999.htm
- http://m.wap.gqskj.cn/snews/78116.htm
- http://m.wap.gqskj.cn/snews/7692699.htm
- http://m.wap.gqskj.cn/snews/58808.htm
- http://m.wap.gqskj.cn/snews/656644.htm
- http://m.wap.gqskj.cn/snews/095722.htm
- http://m.wap.gqskj.cn/snews/9451544.htm
- http://m.wap.gqskj.cn/snews/565484.htm
- http://m.wap.gqskj.cn/snews/668064.htm
- http://m.wap.gqskj.cn/snews/815563.htm
- http://m.wap.gqskj.cn/snews/7004.htm
- http://m.wap.gqskj.cn/snews/3482063.htm
- http://m.wap.gqskj.cn/snews/5261.htm
- http://m.wap.gqskj.cn/snews/8611.htm
- http://m.wap.gqskj.cn/snews/3023426.htm
- http://m.wap.gqskj.cn/snews/1987706.htm
- http://m.wap.gqskj.cn/snews/3015026.htm

## 项目结构

```
gqskj-aggregator/
├── scheduler.py            # 调度器主入口，负责定时触发抓取任务并协调各模块工作
├── config.yaml             # 主配置文件，定义新闻源列表、抓取频率、数据库路径及日志级别
├── requirements.txt        # Python 依赖清单，锁定所有第三方库版本以保证环境一致性
├── Dockerfile              # 容器构建文件，基于 Alpine Linux 精简镜像打包运行环境
├── docker-compose.yml      # 本地开发与测试用编排文件，集成 Redis、Prometheus 等服务
│
├── core/                   # 核心功能模块目录
│   ├── fetcher.py          # 异步 HTTP 抓取器，实现连接池复用、超时控制与重试逻辑
│   ├── parser.py           # 通用解析基类，定义元数据抽取接口及 HTML 清洗方法
│   ├── storage.py          # 数据存储抽象层，支持 SQLite、PostgreSQL 及内存缓存
│   └── monitor.py          # 监控指标收集器，封装 Prometheus Counter 与 Histogram 操作
│
├── adapters/               # 站点适配器目录，每个文件对应一个新闻源的解析规则
│   ├── base.py             # 适配器基类，提供注册机制与默认解析空实现
│   ├── example_news.py     # 示例适配器，演示如何编写 XPath 抽取规则与字段映射
│   └── gqskj_mobile.py     # 针对 m.wap.gqskj.cn 域名的专用解析适配器
│
├── scripts/                # 运维与辅助脚本目录
│   ├── init_db.py          # 初始化数据库表结构，包含链接主表、抓取日志表与规则表
│   ├── export_jsonl.py     # 数据导出脚本，将数据库记录转换为 JSON Lines 格式文件
│   └── clean_old_logs.py   # 日志清理脚本，根据保留天数自动删除过期抓取记录
│
├── tests/                  # 单元测试与集成测试目录
│   ├── test_fetcher.py     # 针对抓取器的超时、重试及代理切换逻辑测试
│   ├── test_parser.py      # 解析器对各类畸形 HTML 的容错测试
│   └── fixtures/           # 测试用静态 HTML 样本文件，模拟不同新闻源页面结构
│
├── docs/                   # 完整文档目录，包含用户手册、API 参考与架构设计说明
│   ├── user_guide.md
│   ├── developer_guide.md
│   ├── deployment.md
│   └── api_reference.md
│
└── logs/                   # 运行时日志存储目录（默认按日期滚动切割）
    └── aggregator.log      # 主日志文件，记录 INFO 及以上级别的运行事件
```

## 贡献指南

提交功能改进或缺陷修复前，请先查阅 docs/developer_guide.md 了解完整的开发规范与适配器扩展流程。

在 GitHub 上 Fork 本仓库，并在本地开发分支上完成代码修改，确保所有新增代码包含对应的单元测试用例，且测试通过率保持 100%。

提交 Pull Request 时，请使用项目提供的 PR 模板，清晰描述变更动机、实现方案以及测试覆盖情况，并关联相关的 Issue 编号。

对于新增新闻源适配器，需在 adapters/ 目录下创建独立模块，并在 config.yaml 的 sources 字段中添加对应配置项，同时提供至少 5 条示例 URL 用于验证解析正确性。

代码审查通过后，由项目维护者合并至 main 分支，并自动触发 CI 流水线完成构建、测试与容器镜像推送。

## 常见问题

Q: 抓取任务频繁超时或返回 HTTP 429 状态码，应如何调整配置？

A: 首先检查 config.yaml 中的 request_interval 参数，建议将其设置为 2 秒以上以降低请求频率。若仍存在限制，可启用 proxy_pool 配置项，通过轮换代理 IP 分散请求来源。此外，可调整 max_retries 和 backoff_factor 参数以延长重试间隔。

Q: 解析器无法正确提取部分新闻文章的发布时间或作者字段，如何调试？

A: 建议启用 DEBUG 日志级别，在 core/parser.py 中打印抽取到的原始 HTML 片段。然后使用浏览器开发者工具或 curl 命令获取目标页面的完整结构，对比 adapters/ 中配置的 XPath 表达式是否与实际 DOM 匹配。若站点改版，可临时继承 BaseAdapter 并重写 extract_metadata 方法实现快速适配。

Q: 数据库文件体积持续增长，是否有自动清理机制？

A: 项目未内置自动清理策略，但 scripts/clean_old_logs.py 脚本支持按天数删除历史抓取记录。用户可通过 crontab 定时任务每周执行一次清理，例如保留最近 30 天的数据。对于生产环境，建议使用 PostgreSQL 并配置分区表，结合外部工具进行数据归档。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:57
