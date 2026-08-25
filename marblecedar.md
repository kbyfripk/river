# NewsCollector

NewsCollector 是一个面向技术信息聚合与外部资源归档的开源工具集，定位于对特定域名下批量新闻类页面进行结构化采集、元数据提取与持久化存储。项目目标用户包括技术研究者、舆情监测人员、内容归档工程师以及需要定期对特定站点进行快照保存的自动化运维团队。通过提供标准化的采集流水线，NewsCollector 将散落在移动端新闻子站中的大量条目转化为可查询、可分析的结构化数据集，从而解决人工收集效率低下、链接失效难以追溯、页面内容难以二次利用等实际问题。

## 功能概览

批量链接导入与校验 支持从文本文件、CSV 或直接粘贴的链接列表中批量导入待采集 URL，自动去重并校验域名白名单。

移动端页面适配采集 内置针对移动端新闻页面的 DOM 解析规则，自动提取标题、正文发布时间、正文内容、来源字段，并过滤广告与导航噪音。

增量更新与去重存储 基于链接 MD5 和页面最后修改时间实现增量采集，避免重复抓取，每次运行仅处理新增或变更的页面。

结构化元数据输出 支持将采集结果输出为 JSON Lines、CSV 或 SQLite 数据库格式，每个条目包含原始 URL、标题、发布时间、正文摘要、完整 HTML 本地缓存路径等字段。

失败重试与超时控制 提供可配置的重试机制（默认 3 次）和请求超时阈值，针对网络波动或服务端限流自动降速，保证长时间采集任务的稳定性。

代理与请求头定制 允许用户为采集任务配置 HTTP 代理、自定义 User-Agent 以及附加请求头，以应对不同网络环境和站点反爬策略。

任务暂停与断点续传 采集任务支持中途暂停，并在下次启动时从最后成功的链接处继续，适用于需要长时间运行的大规模采集场景。

## 应用场景

舆情监控数据源构建 技术团队或公关部门可利用 NewsCollector 定期抓取特定新闻子站下的全部文章，构建用于情感分析、热点词频统计的原始语料库，为后续的数据分析任务提供稳定输入。

历史内容归档与回溯 图书馆、档案馆或研究机构可将本项目作为辅助工具，对某一时间段内移动端新闻页面进行批量快照保存，防止原始链接因站点改版或内容下架而无法访问。

第三方内容聚合平台原型开发 个人开发者或初创团队可使用 NewsCollector 快速搭建内容聚合服务的后端数据采集模块，无需从零编写爬虫逻辑，将更多精力投入前端展示与用户体验优化。

技术 SEO 与链接健康检查 运维人员可定期运行采集任务，检测指定域名下的新闻链接是否返回 200 状态码、页面标题是否为空、描述标签是否存在，从而批量发现死链或元数据缺失问题。

## 快速开始

以下命令演示了从克隆代码到运行一次基础采集任务的全过程。

```bash
# 克隆项目仓库
git clone https://github.com/example/news-collector.git
cd news-collector

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 准备链接列表文件 urls.txt，每行一个 URL
# 然后运行采集任务
python collector.py --input urls.txt --output data/output.jsonl --format json
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于发送网络请求和接收响应 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于从页面中提取结构化数据 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析器后端，提供高性能的 XML/HTML 解析能力 |
| sqlite3 | 系统自带 | 用于本地元数据存储和增量去重，Python 标准库中内置 |
| tqdm | 4.64.0 及以上 | 提供进度条显示，便于长时间采集任务中观察执行进度 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何在 5 分钟内完成首次采集任务？如何配置输入输出路径？ |
| 配置参考 | docs/configuration.md | 有哪些可调整的采集参数？重试次数、超时时间、并发数如何设置？ |
| 数据格式 | docs/data-format.md | 输出的 JSON/CSV/SQLite 各包含哪些字段？字段含义和数据类型是什么？ |
| 高级主题 | docs/advanced.md | 如何编写自定义解析规则？如何对接消息队列或云存储服务？ |

## 资源列表

- http://m.blog.gqskj.cn/nnews/34092.htm
- http://m.blog.gqskj.cn/nnews/400965.htm
- http://m.blog.gqskj.cn/nnews/169352.htm
- http://m.blog.gqskj.cn/nnews/3955953.htm
- http://m.blog.gqskj.cn/nnews/0199.htm
- http://m.blog.gqskj.cn/nnews/5724030.htm
- http://m.blog.gqskj.cn/nnews/28314.htm
- http://m.blog.gqskj.cn/nnews/5291169.htm
- http://m.blog.gqskj.cn/nnews/45658.htm
- http://m.blog.gqskj.cn/nnews/702794.htm
- http://m.blog.gqskj.cn/nnews/7249.htm
- http://m.blog.gqskj.cn/nnews/7513.htm
- http://m.blog.gqskj.cn/nnews/1896411.htm
- http://m.blog.gqskj.cn/nnews/5962.htm
- http://m.blog.gqskj.cn/nnews/580889.htm
- http://m.blog.gqskj.cn/nnews/0266.htm
- http://m.blog.gqskj.cn/nnews/916843.htm
- http://m.blog.gqskj.cn/nnews/3579.htm
- http://m.blog.gqskj.cn/nnews/6351.htm
- http://m.blog.gqskj.cn/nnews/888376.htm
- http://m.blog.gqskj.cn/nnews/4604828.htm
- http://m.blog.gqskj.cn/nnews/962667.htm
- http://m.blog.gqskj.cn/nnews/6517682.htm
- http://m.blog.gqskj.cn/nnews/9617.htm
- http://m.blog.gqskj.cn/nnews/59652.htm
- http://m.blog.gqskj.cn/nnews/7546395.htm
- http://m.blog.gqskj.cn/nnews/5842707.htm
- http://m.blog.gqskj.cn/nnews/3972.htm
- http://m.blog.gqskj.cn/nnews/240641.htm
- http://m.blog.gqskj.cn/nnews/002609.htm
- http://m.blog.gqskj.cn/nnews/584396.htm
- http://m.blog.gqskj.cn/nnews/8332327.htm
- http://m.blog.gqskj.cn/nnews/6880302.htm
- http://m.blog.gqskj.cn/nnews/21355.htm
- http://m.blog.gqskj.cn/nnews/7309930.htm
- http://m.blog.gqskj.cn/nnews/46321.htm
- http://m.blog.gqskj.cn/nnews/638271.htm
- http://m.blog.gqskj.cn/nnews/74220.htm
- http://m.blog.gqskj.cn/nnews/85345.htm
- http://m.blog.gqskj.cn/nnews/30543.htm
- http://m.blog.gqskj.cn/nnews/4497595.htm
- http://m.blog.gqskj.cn/nnews/0730.htm
- http://m.blog.gqskj.cn/nnews/0766110.htm
- http://m.blog.gqskj.cn/nnews/1713679.htm
- http://m.blog.gqskj.cn/nnews/3688405.htm
- http://m.blog.gqskj.cn/nnews/1003265.htm
- http://m.blog.gqskj.cn/nnews/23104.htm
- http://m.blog.gqskj.cn/nnews/8102558.htm
- http://m.blog.gqskj.cn/nnews/50792.htm
- http://m.blog.gqskj.cn/nnews/46934.htm
- http://m.blog.gqskj.cn/nnews/70214.htm
- http://m.blog.gqskj.cn/nnews/591578.htm
- http://m.blog.gqskj.cn/nnews/002460.htm
- http://m.blog.gqskj.cn/nnews/44882.htm
- http://m.blog.gqskj.cn/nnews/7061.htm
- http://m.blog.gqskj.cn/nnews/489337.htm
- http://m.blog.gqskj.cn/nnews/21085.htm
- http://m.blog.gqskj.cn/nnews/6549214.htm
- http://m.blog.gqskj.cn/nnews/73405.htm
- http://m.blog.gqskj.cn/nnews/5260567.htm
- http://m.blog.gqskj.cn/nnews/70693.htm
- http://m.blog.gqskj.cn/nnews/78628.htm
- http://m.blog.gqskj.cn/nnews/49584.htm
- http://m.blog.gqskj.cn/nnews/7829214.htm
- http://m.blog.gqskj.cn/nnews/1033252.htm
- http://m.blog.gqskj.cn/nnews/7766.htm
- http://m.blog.gqskj.cn/nnews/9639.htm
- http://m.blog.gqskj.cn/nnews/921293.htm
- http://m.blog.gqskj.cn/nnews/2208336.htm
- http://m.blog.gqskj.cn/nnews/7492.htm
- http://m.blog.gqskj.cn/nnews/28882.htm
- http://m.blog.gqskj.cn/nnews/14383.htm
- http://m.blog.gqskj.cn/nnews/1586632.htm
- http://m.blog.gqskj.cn/nnews/90683.htm
- http://m.blog.gqskj.cn/nnews/20343.htm
- http://m.blog.gqskj.cn/nnews/3495219.htm
- http://m.blog.gqskj.cn/nnews/529329.htm
- http://m.blog.gqskj.cn/nnews/56410.htm
- http://m.blog.gqskj.cn/nnews/3904.htm
- http://m.blog.gqskj.cn/nnews/95611.htm
- http://m.blog.gqskj.cn/nnews/35013.htm
- http://m.blog.gqskj.cn/nnews/80383.htm
- http://m.blog.gqskj.cn/nnews/814505.htm
- http://m.blog.gqskj.cn/nnews/996388.htm
- http://m.blog.gqskj.cn/nnews/25084.htm
- http://m.blog.gqskj.cn/nnews/1418.htm
- http://m.blog.gqskj.cn/nnews/26230.htm
- http://m.blog.gqskj.cn/nnews/94289.htm
- http://m.blog.gqskj.cn/nnews/77823.htm
- http://m.blog.gqskj.cn/nnews/5503.htm
- http://m.blog.gqskj.cn/nnews/25452.htm
- http://m.blog.gqskj.cn/nnews/2955.htm
- http://m.blog.gqskj.cn/nnews/8298904.htm
- http://m.blog.gqskj.cn/nnews/11504.htm
- http://m.blog.gqskj.cn/nnews/036885.htm
- http://m.blog.gqskj.cn/nnews/532613.htm
- http://m.blog.gqskj.cn/nnews/33713.htm
- http://m.blog.gqskj.cn/nnews/7371513.htm
- http://m.blog.gqskj.cn/nnews/12507.htm
- http://m.blog.gqskj.cn/nnews/248081.htm
- http://m.blog.gqskj.cn/nnews/189002.htm
- http://m.blog.gqskj.cn/nnews/69571.htm
- http://m.blog.gqskj.cn/nnews/5494.htm
- http://m.blog.gqskj.cn/nnews/4871.htm
- http://m.blog.gqskj.cn/nnews/82938.htm
- http://m.blog.gqskj.cn/nnews/3314828.htm
- http://m.blog.gqskj.cn/nnews/7044.htm
- http://m.blog.gqskj.cn/nnews/45078.htm
- http://m.blog.gqskj.cn/nnews/2141.htm
- http://m.blog.gqskj.cn/nnews/4264429.htm
- http://m.blog.gqskj.cn/nnews/9170.htm
- http://m.blog.gqskj.cn/nnews/7648.htm
- http://m.blog.gqskj.cn/nnews/39239.htm
- http://m.blog.gqskj.cn/nnews/7847.htm
- http://m.blog.gqskj.cn/nnews/0167.htm
- http://m.blog.gqskj.cn/nnews/3729.htm
- http://m.blog.gqskj.cn/nnews/3798492.htm
- http://m.blog.gqskj.cn/nnews/9761.htm
- http://m.blog.gqskj.cn/nnews/84061.htm
- http://m.blog.gqskj.cn/nnews/959168.htm
- http://m.blog.gqskj.cn/nnews/36424.htm
- http://m.blog.gqskj.cn/nnews/78719.htm
- http://m.blog.gqskj.cn/nnews/7647.htm
- http://m.blog.gqskj.cn/nnews/725098.htm
- http://m.blog.gqskj.cn/nnews/388019.htm
- http://m.blog.gqskj.cn/nnews/4736887.htm
- http://m.blog.gqskj.cn/nnews/1713.htm
- http://m.blog.gqskj.cn/nnews/102593.htm
- http://m.blog.gqskj.cn/nnews/14472.htm
- http://m.blog.gqskj.cn/nnews/5608.htm
- http://m.blog.gqskj.cn/nnews/9850.htm
- http://m.blog.gqskj.cn/nnews/5010113.htm
- http://m.blog.gqskj.cn/nnews/2972.htm
- http://m.blog.gqskj.cn/nnews/1166.htm
- http://m.blog.gqskj.cn/nnews/0895.htm
- http://m.blog.gqskj.cn/nnews/29506.htm
- http://m.blog.gqskj.cn/nnews/47083.htm
- http://m.blog.gqskj.cn/nnews/0558.htm
- http://m.blog.gqskj.cn/nnews/4074064.htm
- http://m.blog.gqskj.cn/nnews/0027424.htm
- http://m.blog.gqskj.cn/nnews/8907121.htm
- http://m.blog.gqskj.cn/nnews/7489074.htm
- http://m.blog.gqskj.cn/nnews/4692.htm
- http://m.blog.gqskj.cn/nnews/8562.htm
- http://m.blog.gqskj.cn/nnews/0998127.htm
- http://m.blog.gqskj.cn/nnews/731213.htm
- http://m.blog.gqskj.cn/nnews/1348.htm
- http://m.blog.gqskj.cn/nnews/37992.htm
- http://m.blog.gqskj.cn/nnews/8016.htm
- http://m.blog.gqskj.cn/nnews/2257.htm
- http://m.blog.gqskj.cn/nnews/65880.htm
- http://m.blog.gqskj.cn/nnews/568865.htm
- http://m.blog.gqskj.cn/nnews/9995329.htm
- http://m.blog.gqskj.cn/nnews/17393.htm
- http://m.blog.gqskj.cn/nnews/1614.htm
- http://m.blog.gqskj.cn/nnews/7572.htm
- http://m.blog.gqskj.cn/nnews/8804.htm
- http://m.blog.gqskj.cn/nnews/468036.htm
- http://m.blog.gqskj.cn/nnews/26337.htm
- http://m.blog.gqskj.cn/nnews/5893.htm
- http://m.blog.gqskj.cn/nnews/0914.htm
- http://m.blog.gqskj.cn/nnews/1589289.htm
- http://m.blog.gqskj.cn/nnews/99653.htm
- http://m.blog.gqskj.cn/nnews/6627.htm
- http://m.blog.gqskj.cn/nnews/67053.htm
- http://m.blog.gqskj.cn/nnews/6159983.htm
- http://m.blog.gqskj.cn/nnews/0526534.htm
- http://m.blog.gqskj.cn/nnews/96406.htm
- http://m.blog.gqskj.cn/nnews/7900240.htm
- http://m.blog.gqskj.cn/nnews/6975.htm
- http://m.blog.gqskj.cn/nnews/124450.htm
- http://m.blog.gqskj.cn/nnews/923735.htm
- http://m.blog.gqskj.cn/nnews/76528.htm
- http://m.blog.gqskj.cn/nnews/4016.htm
- http://m.blog.gqskj.cn/nnews/2873.htm
- http://m.blog.gqskj.cn/nnews/2229871.htm
- http://m.blog.gqskj.cn/nnews/044725.htm
- http://m.blog.gqskj.cn/nnews/5115137.htm
- http://m.blog.gqskj.cn/nnews/9987.htm
- http://m.blog.gqskj.cn/nnews/194929.htm
- http://m.blog.gqskj.cn/nnews/611848.htm
- http://m.blog.gqskj.cn/nnews/91980.htm
- http://m.blog.gqskj.cn/nnews/41201.htm
- http://m.blog.gqskj.cn/nnews/4110.htm
- http://m.blog.gqskj.cn/nnews/54696.htm
- http://m.blog.gqskj.cn/nnews/03332.htm
- http://m.blog.gqskj.cn/nnews/0052.htm
- http://m.blog.gqskj.cn/nnews/3581520.htm
- http://m.blog.gqskj.cn/nnews/1248.htm
- http://m.blog.gqskj.cn/nnews/31461.htm
- http://m.blog.gqskj.cn/nnews/76299.htm
- http://m.blog.gqskj.cn/nnews/1487965.htm
- http://m.blog.gqskj.cn/nnews/772260.htm
- http://m.blog.gqskj.cn/nnews/21093.htm
- http://m.blog.gqskj.cn/nnews/7758924.htm
- http://m.blog.gqskj.cn/nnews/480578.htm
- http://m.blog.gqskj.cn/nnews/6119661.htm
- http://m.blog.gqskj.cn/nnews/9460117.htm
- http://m.blog.gqskj.cn/nnews/9926764.htm
- http://m.blog.gqskj.cn/nnews/94065.htm
- http://m.blog.gqskj.cn/nnews/83028.htm
- http://m.blog.gqskj.cn/nnews/70467.htm
- http://m.blog.gqskj.cn/nnews/91729.htm
- http://m.blog.gqskj.cn/nnews/2476302.htm
- http://m.blog.gqskj.cn/nnews/56871.htm
- http://m.blog.gqskj.cn/nnews/529474.htm
- http://m.blog.gqskj.cn/nnews/02753.htm
- http://m.blog.gqskj.cn/nnews/893306.htm
- http://m.blog.gqskj.cn/nnews/66912.htm
- http://m.blog.gqskj.cn/nnews/6777813.htm
- http://m.blog.gqskj.cn/nnews/3127730.htm
- http://m.blog.gqskj.cn/nnews/1089.htm
- http://m.blog.gqskj.cn/nnews/4077255.htm
- http://m.blog.gqskj.cn/nnews/77525.htm
- http://m.blog.gqskj.cn/nnews/7019438.htm
- http://m.blog.gqskj.cn/nnews/0224170.htm
- http://m.blog.gqskj.cn/nnews/7686459.htm
- http://m.blog.gqskj.cn/nnews/033009.htm
- http://m.blog.gqskj.cn/nnews/0967.htm
- http://m.blog.gqskj.cn/nnews/592897.htm
- http://m.blog.gqskj.cn/nnews/2325063.htm
- http://m.blog.gqskj.cn/nnews/9914924.htm
- http://m.blog.gqskj.cn/nnews/9479.htm
- http://m.blog.gqskj.cn/nnews/492816.htm
- http://m.blog.gqskj.cn/nnews/5267.htm
- http://m.blog.gqskj.cn/nnews/92572.htm
- http://m.blog.gqskj.cn/nnews/26383.htm
- http://m.blog.gqskj.cn/nnews/2384061.htm
- http://m.blog.gqskj.cn/nnews/5674.htm
- http://m.blog.gqskj.cn/nnews/2135.htm
- http://m.blog.gqskj.cn/nnews/9351.htm
- http://m.blog.gqskj.cn/nnews/6750867.htm
- http://m.blog.gqskj.cn/nnews/1973.htm
- http://m.blog.gqskj.cn/nnews/199980.htm
- http://m.blog.gqskj.cn/nnews/654159.htm
- http://m.blog.gqskj.cn/nnews/2048045.htm
- http://m.blog.gqskj.cn/nnews/230812.htm
- http://m.blog.gqskj.cn/nnews/597137.htm
- http://m.blog.gqskj.cn/nnews/6104958.htm
- http://m.blog.gqskj.cn/nnews/0876.htm
- http://m.blog.gqskj.cn/nnews/7814.htm
- http://m.blog.gqskj.cn/nnews/5495843.htm
- http://m.blog.gqskj.cn/nnews/1409.htm
- http://m.blog.gqskj.cn/nnews/731883.htm
- http://m.blog.gqskj.cn/nnews/452169.htm
- http://m.blog.gqskj.cn/nnews/10141.htm
- http://m.blog.gqskj.cn/nnews/38007.htm
- http://m.blog.gqskj.cn/nnews/9681.htm
- http://m.blog.gqskj.cn/nnews/2335.htm
- http://m.blog.gqskj.cn/nnews/26614.htm

## 项目结构

```
news-collector/
├── collector.py                # 主入口脚本，负责解析命令行参数并调度采集流程
├── config.yaml                 # 全局配置文件，包含重试次数、超时时间、并发度等参数
├── requirements.txt            # Python 依赖清单，用于一键安装所有第三方库
├── src/                        # 核心源代码目录
│   ├── fetcher/                # 网络请求模块
│   │   ├── client.py           # 封装 requests 会话，处理代理和重试逻辑
│   │   └── middleware.py       # 请求前/后钩子，用于日志记录和速率控制
│   ├── parser/                 # 页面解析模块
│   │   ├── html_parser.py      # 基于 beautifulsoup4 的通用新闻页解析器
│   │   └── field_extractor.py  # 提取标题、时间、正文等字段的辅助函数
│   ├── storage/                # 存储模块
│   │   ├── writer.py           # 将结果写入 JSON/CSV/SQLite 的输出适配器
│   │   └── cache.py            # 本地 HTML 缓存管理，支持磁盘存储与过期清理
│   ├── scheduler/              # 任务调度模块
│   │   ├── dispatcher.py       # 控制并发任务分发与线程池管理
│   │   └── checkpoint.py       # 断点续传状态持久化与恢复
│   └── utils/                  # 通用工具函数
│       ├── url_utils.py        # URL 去重、域名校验、链接格式规范化
│       └── logger.py           # 统一日志输出，支持文件和控制台双通道
├── tests/                      # 单元测试与集成测试用例
│   ├── test_fetcher.py         # 模拟网络请求的测试套件
│   ├── test_parser.py          # 使用本地样本页面测试解析正确性
│   └── fixtures/               # 测试用的静态 HTML 样本文件
├── docs/                       # 完整文档目录
│   ├── quickstart.md           # 快速入门指南
│   ├── configuration.md        # 配置项详细说明
│   ├── data-format.md          # 输出数据格式规范
│   └── advanced.md             # 自定义解析与扩展开发指南
└── data/                       # 运行时数据目录（默认输出位置，可配置）
    ├── output.jsonl            # 默认 JSON 格式输出文件
    ├── cache/                  # 页面 HTML 缓存目录
    └── checkpoint.db           # SQLite 断点续传状态数据库
```

## 贡献指南

我们欢迎社区以多种形式参与 NewsCollector 项目。以下为标准的贡献流程，请所有贡献者遵照执行。

1. 提交议题（Issue）进行需求沟通。在实现新功能或修复缺陷之前，请先在 GitHub Issues 中搜索是否已有类似议题。若无，则新建议题并详细描述您发现的问题或希望新增的特性，等待维护者反馈后再进入编码阶段。

2. 派生（Fork）项目仓库并创建功能分支。将主仓库派生至个人账号下，然后克隆本地并创建以 `feature/` 或 `fix/` 为前缀的新分支，例如 `feature/add-rss-output`。请确保分支命名清晰反映变更内容。

3. 编写代码并补充单元测试。所有新增功能或缺陷修复均需在 `tests/` 目录下编写相应的测试用例，确保代码覆盖率达到 80% 以上。同时，请遵守项目现有代码风格（PEP 8），并运行 `flake8` 和 `pytest` 通过全部检查。

4. 发起合并请求（Pull Request）并填写模板。将分支推送至个人派生仓库后，向主仓库的 `main` 分支发起合并请求。请完整填写 PR 模板中的检查项，包括议题编号、变更摘要、测试结果和兼容性说明。

5. 接受代码审查与持续集成检查。维护者将在 PR 中进行逐行审查，并触发 GitHub Actions 运行自动化测试。请根据审查意见及时修改代码，直至所有检查通过并获批准后，PR 将被合并。

## 常见问题

问：采集过程中频繁超时或返回 403 状态码，应如何解决？

答：首先检查目标站点是否有反爬机制。建议在 `config.yaml` 中调整 `user_agent` 字段，更换为最新版移动端浏览器的 UA 字符串。其次，可降低 `concurrency` 并发数（例如从 10 改为 3），并适当增加 `request_timeout` 超时时间（例如从 10 秒改为 30 秒）。若仍无法解决，可启用 `proxy` 配置项，使用代理池轮换出口 IP。

问：如何仅采集指定时间段内发布的文章？

答：目前采集器默认对所有输入的 URL 进行抓取，不主动过滤发布时间。您可以在调用前通过外部脚本筛选 `urls.txt` 中的链接，或利用 `parser` 模块提取时间字段后，在 `storage` 层写入前进行过滤。后续版本计划增加 `--since` 和 `--until` 命令行参数以原生支持时间范围过滤。

问：输出 JSON 文件过大导致内存占用过高，如何处理？

答：推荐使用 SQLite 输出模式（`--format sqlite`），该模式采用逐条写入事务，内存占用恒定为低水平。若必须输出 JSON，可使用 `--batch-size` 参数控制每批次缓存条目数（默认 1000），配合 `--output` 指定为目录路径，采集器将自动分片生成多个 JSON 文件，每个文件大小不超过预设阈值。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:44
