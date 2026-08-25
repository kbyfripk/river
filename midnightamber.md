# WapInfo Aggregator

WapInfo Aggregator 是一个面向移动端资讯聚合与历史数据归档的开源工具集，专注于从 WAP 门户站点批量抓取、解析和结构化存储新闻类 HTML 页面。该项目主要服务于数据挖掘研究人员、历史内容存档工作者以及需要从移动端网页中提取结构化信息的开发者。

项目核心定位在于提供一套稳定、可扩展的抓取与解析管线，能够处理大量来源于移动端 WAP 页面的非标准 HTML 内容，并将其转换为结构化的 JSON 或 Markdown 格式，便于后续检索、分析与展示。当前版本已针对特定域名下的数千个新闻页面进行了适配优化。

## 功能概览

批量抓取引擎 支持多线程并发请求，可自定义请求头与超时策略，有效应对移动端页面的反爬机制。

智能编码检测 自动识别 GBK、UTF-8 等常见字符集，避免因编码问题导致的乱码或解析失败。

内容提取器 基于 XPath 与正则表达式的混合抽取策略，可精准提取标题、发布时间、正文文本及来源字段。

去重与增量更新 利用 URL 指纹与内容哈希实现文档级别的去重，支持增量抓取模式，避免重复处理已入库页面。

结构化导出 内置 JSON Lines 与 Markdown 表格两种输出格式，方便下游数据分析工具直接消费。

失败重试与日志 提供指数退避重试机制，配合分级日志记录，便于运维人员监控抓取任务状态。

代理支持 原生支持 HTTP/HTTPS 代理配置，适用于需要更换出口 IP 的大规模抓取场景。

## 应用场景

历史新闻数据归档 研究人员可通过 WapInfo Aggregator 将指定域名下的历史新闻页面批量下载并转换为结构化数据，构建长期可用的历史语料库。

移动端内容迁移 在 WAP 站点改版或下线前，使用本工具快速完成内容备份，确保原有资讯数据不丢失，并可导入到新系统中。

SEO 与舆情监控 运维人员可定期抓取目标站点的新闻更新，提取标题与发布时间，用于构建简单的舆情监控看板或搜索引擎索引源。

数据清洗训练集构建 机器学习工程师可利用本工具抽取的大量文本数据，经过去重和清洗后生成用于 NLP 模型训练的高质量语料集。

## 快速开始

以下命令演示了从克隆项目到运行一次完整抓取任务的全过程。

```bash
# 克隆项目仓库
git clone https://github.com/example/wapinfo-aggregator.git
cd wapinfo-aggregator

# 安装项目依赖（建议使用 Python 虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行示例抓取任务（使用项目内置的测试 URL 列表）
python wapinfo.py --input urls.txt --output output.jsonl --threads 4
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 或更高版本 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与会话管理 |
| lxml | 4.9.0 及以上 | 解析 HTML/XML 文档，提供 XPath 支持 |
| charset-normalizer | 3.0.0 及以上 | 智能识别页面字符编码 |
| tqdm | 4.64.0 及以上 | 展示进度条，便于监控批量任务 |
| regex | 2022.10.31 及以上 | 提供更强大的正则匹配能力，用于内容清洗 |
| jsonlines | 3.1.0 及以上 | 支持 JSON Lines 格式的读写操作 |
| pyyaml | 6.0 及以上 | 用于解析配置文件 |
| click | 8.1.0 及以上 | 提供命令行交互接口 |
| tenacity | 8.2.0 及以上 | 实现指数退避重试逻辑 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/usage.md | 如何配置抓取参数、选择输出格式、调整并发数？ |
| 开发指南 | docs/development.md | 如何扩展新的内容抽取规则、添加自定义过滤器？ |
| 部署运维 | docs/deployment.md | 如何在服务器上长期运行、如何配置代理和日志轮转？ |
| 常见问题 | docs/faq.md | 遇到编码错误、超时、被封 IP 时该怎么办？ |
| API 参考 | docs/api.md | 各模块的类与方法详细说明、参数含义与返回值类型。 |

## 资源列表

- http://m.wap.fcful.cn/nnews/015593.htm
- http://m.wap.fcful.cn/nnews/4419.htm
- http://m.wap.fcful.cn/nnews/85191.htm
- http://m.wap.fcful.cn/nnews/080403.htm
- http://m.wap.fcful.cn/nnews/3767.htm
- http://m.wap.fcful.cn/nnews/155842.htm
- http://m.wap.fcful.cn/nnews/7712.htm
- http://m.wap.fcful.cn/nnews/031103.htm
- http://m.wap.fcful.cn/nnews/937798.htm
- http://m.wap.fcful.cn/nnews/5310300.htm
- http://m.wap.fcful.cn/nnews/6379.htm
- http://m.wap.fcful.cn/nnews/714721.htm
- http://m.wap.fcful.cn/nnews/53968.htm
- http://m.wap.fcful.cn/nnews/99413.htm
- http://m.wap.fcful.cn/nnews/63153.htm
- http://m.wap.fcful.cn/nnews/9824046.htm
- http://m.wap.fcful.cn/nnews/0895.htm
- http://m.wap.fcful.cn/nnews/30191.htm
- http://m.wap.fcful.cn/nnews/2155.htm
- http://m.wap.fcful.cn/nnews/599530.htm
- http://m.wap.fcful.cn/nnews/5907.htm
- http://m.wap.fcful.cn/nnews/2443207.htm
- http://m.wap.fcful.cn/nnews/03570.htm
- http://m.wap.fcful.cn/nnews/7188599.htm
- http://m.wap.fcful.cn/nnews/275294.htm
- http://m.wap.fcful.cn/nnews/745510.htm
- http://m.wap.fcful.cn/nnews/1269857.htm
- http://m.wap.fcful.cn/nnews/6001.htm
- http://m.wap.fcful.cn/nnews/6329378.htm
- http://m.wap.fcful.cn/nnews/1493999.htm
- http://m.wap.fcful.cn/nnews/2591.htm
- http://m.wap.fcful.cn/nnews/248028.htm
- http://m.wap.fcful.cn/nnews/727206.htm
- http://m.wap.fcful.cn/nnews/207901.htm
- http://m.wap.fcful.cn/nnews/5266.htm
- http://m.wap.fcful.cn/nnews/4991.htm
- http://m.wap.fcful.cn/nnews/4722449.htm
- http://m.wap.fcful.cn/nnews/662807.htm
- http://m.wap.fcful.cn/nnews/1585741.htm
- http://m.wap.fcful.cn/nnews/2501456.htm
- http://m.wap.fcful.cn/nnews/6713564.htm
- http://m.wap.fcful.cn/nnews/01685.htm
- http://m.wap.fcful.cn/nnews/4246593.htm
- http://m.wap.fcful.cn/nnews/9798498.htm
- http://m.wap.fcful.cn/nnews/8400858.htm
- http://m.wap.fcful.cn/nnews/4138672.htm
- http://m.wap.fcful.cn/nnews/7053.htm
- http://m.wap.fcful.cn/nnews/7327.htm
- http://m.wap.fcful.cn/nnews/5884882.htm
- http://m.wap.fcful.cn/nnews/2847035.htm
- http://m.wap.fcful.cn/nnews/7718610.htm
- http://m.wap.fcful.cn/nnews/0028.htm
- http://m.wap.fcful.cn/nnews/4399011.htm
- http://m.wap.fcful.cn/nnews/142071.htm
- http://m.wap.fcful.cn/nnews/736786.htm
- http://m.wap.fcful.cn/nnews/69151.htm
- http://m.wap.fcful.cn/nnews/3574.htm
- http://m.wap.fcful.cn/nnews/0601389.htm
- http://m.wap.fcful.cn/nnews/456571.htm
- http://m.wap.fcful.cn/nnews/412221.htm
- http://m.wap.fcful.cn/nnews/0814678.htm
- http://m.wap.fcful.cn/nnews/175395.htm
- http://m.wap.fcful.cn/nnews/3618.htm
- http://m.wap.fcful.cn/nnews/09358.htm
- http://m.wap.fcful.cn/nnews/25151.htm
- http://m.wap.fcful.cn/nnews/223903.htm
- http://m.wap.fcful.cn/nnews/84824.htm
- http://m.wap.fcful.cn/nnews/5407.htm
- http://m.wap.fcful.cn/nnews/2085866.htm
- http://m.wap.fcful.cn/nnews/9956.htm
- http://m.wap.fcful.cn/nnews/86457.htm
- http://m.wap.fcful.cn/nnews/3166.htm
- http://m.wap.fcful.cn/nnews/5554191.htm
- http://m.wap.fcful.cn/nnews/35914.htm
- http://m.wap.fcful.cn/nnews/698857.htm
- http://m.wap.fcful.cn/nnews/0228017.htm
- http://m.wap.fcful.cn/nnews/5168706.htm
- http://m.wap.fcful.cn/nnews/787179.htm
- http://m.wap.fcful.cn/nnews/415952.htm
- http://m.wap.fcful.cn/nnews/0737286.htm
- http://m.wap.fcful.cn/nnews/8168.htm
- http://m.wap.fcful.cn/nnews/5006.htm
- http://m.wap.fcful.cn/nnews/117993.htm
- http://m.wap.fcful.cn/nnews/6472.htm
- http://m.wap.fcful.cn/nnews/6491.htm
- http://m.wap.fcful.cn/nnews/207790.htm
- http://m.wap.fcful.cn/nnews/033982.htm
- http://m.wap.fcful.cn/nnews/5344560.htm
- http://m.wap.fcful.cn/nnews/399909.htm
- http://m.wap.fcful.cn/nnews/41027.htm
- http://m.wap.fcful.cn/nnews/0717066.htm
- http://m.wap.fcful.cn/nnews/039806.htm
- http://m.wap.fcful.cn/nnews/462815.htm
- http://m.wap.fcful.cn/nnews/4141883.htm
- http://m.wap.fcful.cn/nnews/1496849.htm
- http://m.wap.fcful.cn/nnews/03676.htm
- http://m.wap.fcful.cn/nnews/9576469.htm
- http://m.wap.fcful.cn/nnews/76691.htm
- http://m.wap.fcful.cn/nnews/22633.htm
- http://m.wap.fcful.cn/nnews/51518.htm
- http://m.wap.fcful.cn/nnews/5777854.htm
- http://m.wap.fcful.cn/nnews/172701.htm
- http://m.wap.fcful.cn/nnews/23159.htm
- http://m.wap.fcful.cn/nnews/7442.htm
- http://m.wap.fcful.cn/nnews/7148.htm
- http://m.wap.fcful.cn/nnews/8251.htm
- http://m.wap.fcful.cn/nnews/4335780.htm
- http://m.wap.fcful.cn/nnews/18968.htm
- http://m.wap.fcful.cn/nnews/8271.htm
- http://m.wap.fcful.cn/nnews/564203.htm
- http://m.wap.fcful.cn/nnews/620086.htm
- http://m.wap.fcful.cn/nnews/41170.htm
- http://m.wap.fcful.cn/nnews/5730591.htm
- http://m.wap.fcful.cn/nnews/0814376.htm
- http://m.wap.fcful.cn/nnews/78464.htm
- http://m.wap.fcful.cn/nnews/1206.htm
- http://m.wap.fcful.cn/nnews/760002.htm
- http://m.wap.fcful.cn/nnews/8079.htm
- http://m.wap.fcful.cn/nnews/9183695.htm
- http://m.wap.fcful.cn/nnews/77876.htm
- http://m.wap.fcful.cn/nnews/778365.htm
- http://m.wap.fcful.cn/nnews/11689.htm
- http://m.wap.fcful.cn/nnews/797768.htm
- http://m.wap.fcful.cn/nnews/6973451.htm
- http://m.wap.fcful.cn/nnews/9448943.htm
- http://m.wap.fcful.cn/nnews/09360.htm
- http://m.wap.fcful.cn/nnews/1480.htm
- http://m.wap.fcful.cn/nnews/047493.htm
- http://m.wap.fcful.cn/nnews/3641.htm
- http://m.wap.fcful.cn/nnews/9032.htm
- http://m.wap.fcful.cn/nnews/813872.htm
- http://m.wap.fcful.cn/nnews/8544958.htm
- http://m.wap.fcful.cn/nnews/3455532.htm
- http://m.wap.fcful.cn/nnews/1311.htm
- http://m.wap.fcful.cn/nnews/6045.htm
- http://m.wap.fcful.cn/nnews/84217.htm
- http://m.wap.fcful.cn/nnews/6695.htm
- http://m.wap.fcful.cn/nnews/5514440.htm
- http://m.wap.fcful.cn/nnews/83267.htm
- http://m.wap.fcful.cn/nnews/373645.htm
- http://m.wap.fcful.cn/nnews/430001.htm
- http://m.wap.fcful.cn/nnews/8266.htm
- http://m.wap.fcful.cn/nnews/0271.htm
- http://m.wap.fcful.cn/nnews/37768.htm
- http://m.wap.fcful.cn/nnews/1083899.htm
- http://m.wap.fcful.cn/nnews/8653.htm
- http://m.wap.fcful.cn/nnews/8700.htm
- http://m.wap.fcful.cn/nnews/739736.htm
- http://m.wap.fcful.cn/nnews/4813870.htm
- http://m.wap.fcful.cn/nnews/772119.htm
- http://m.wap.fcful.cn/nnews/256366.htm
- http://m.wap.fcful.cn/nnews/89620.htm
- http://m.wap.fcful.cn/nnews/03125.htm
- http://m.wap.fcful.cn/nnews/1020.htm
- http://m.wap.fcful.cn/nnews/8321704.htm
- http://m.wap.fcful.cn/nnews/7238.htm
- http://m.wap.fcful.cn/nnews/3982.htm
- http://m.wap.fcful.cn/nnews/99738.htm
- http://m.wap.fcful.cn/nnews/268753.htm
- http://m.wap.fcful.cn/nnews/5814633.htm
- http://m.wap.fcful.cn/nnews/2403.htm
- http://m.wap.fcful.cn/nnews/98385.htm
- http://m.wap.fcful.cn/nnews/5977422.htm
- http://m.wap.fcful.cn/nnews/7314.htm
- http://m.wap.fcful.cn/nnews/5434.htm
- http://m.wap.fcful.cn/nnews/4288.htm
- http://m.wap.fcful.cn/nnews/3762668.htm
- http://m.wap.fcful.cn/nnews/065669.htm
- http://m.wap.fcful.cn/nnews/05325.htm
- http://m.wap.fcful.cn/nnews/45482.htm
- http://m.wap.fcful.cn/nnews/28141.htm
- http://m.wap.fcful.cn/nnews/6118.htm
- http://m.wap.fcful.cn/nnews/1528.htm
- http://m.wap.fcful.cn/nnews/82251.htm
- http://m.wap.fcful.cn/nnews/370410.htm
- http://m.wap.fcful.cn/nnews/148469.htm
- http://m.wap.fcful.cn/nnews/683966.htm
- http://m.wap.fcful.cn/nnews/59100.htm
- http://m.wap.fcful.cn/nnews/54042.htm
- http://m.wap.fcful.cn/nnews/1610.htm
- http://m.wap.fcful.cn/nnews/78866.htm
- http://m.wap.fcful.cn/nnews/514064.htm
- http://m.wap.fcful.cn/nnews/984939.htm
- http://m.wap.fcful.cn/nnews/5191.htm
- http://m.wap.fcful.cn/nnews/7488548.htm
- http://m.wap.fcful.cn/nnews/90166.htm
- http://m.wap.fcful.cn/nnews/0150.htm
- http://m.wap.fcful.cn/nnews/4055152.htm
- http://m.wap.fcful.cn/nnews/3905.htm
- http://m.wap.fcful.cn/nnews/303101.htm
- http://m.wap.fcful.cn/nnews/0013.htm
- http://m.wap.fcful.cn/nnews/0346022.htm
- http://m.wap.fcful.cn/nnews/9796.htm
- http://m.wap.fcful.cn/nnews/6935.htm
- http://m.wap.fcful.cn/nnews/8081281.htm
- http://m.wap.fcful.cn/nnews/7398976.htm
- http://m.wap.fcful.cn/nnews/6460.htm
- http://m.wap.fcful.cn/nnews/5251161.htm
- http://m.wap.fcful.cn/nnews/10315.htm
- http://m.wap.fcful.cn/nnews/1917.htm
- http://m.wap.fcful.cn/nnews/755600.htm
- http://m.wap.fcful.cn/nnews/2055803.htm
- http://m.wap.fcful.cn/nnews/3377.htm
- http://m.wap.fcful.cn/nnews/9751023.htm
- http://m.wap.fcful.cn/nnews/7443.htm
- http://m.wap.fcful.cn/nnews/1830.htm
- http://m.wap.fcful.cn/nnews/8841489.htm
- http://m.wap.fcful.cn/nnews/9916.htm
- http://m.wap.fcful.cn/nnews/79765.htm
- http://m.wap.fcful.cn/nnews/3646827.htm
- http://m.wap.fcful.cn/nnews/95082.htm
- http://m.wap.fcful.cn/nnews/5260.htm
- http://m.wap.fcful.cn/nnews/5335.htm
- http://m.wap.fcful.cn/nnews/53049.htm
- http://m.wap.fcful.cn/nnews/9107.htm
- http://m.wap.fcful.cn/nnews/6340.htm
- http://m.wap.fcful.cn/nnews/26135.htm
- http://m.wap.fcful.cn/nnews/81913.htm
- http://m.wap.fcful.cn/nnews/51324.htm
- http://m.wap.fcful.cn/nnews/1671.htm
- http://m.wap.fcful.cn/nnews/8634371.htm
- http://m.wap.fcful.cn/nnews/1732.htm
- http://m.wap.fcful.cn/nnews/8873.htm
- http://m.wap.fcful.cn/nnews/3915.htm
- http://m.wap.fcful.cn/nnews/108507.htm
- http://m.wap.fcful.cn/nnews/10486.htm
- http://m.wap.fcful.cn/nnews/415167.htm
- http://m.wap.fcful.cn/nnews/99192.htm
- http://m.wap.fcful.cn/nnews/3386640.htm
- http://m.wap.fcful.cn/nnews/1085.htm
- http://m.wap.fcful.cn/nnews/3255.htm
- http://m.wap.fcful.cn/nnews/58795.htm
- http://m.wap.fcful.cn/nnews/7673.htm
- http://m.wap.fcful.cn/nnews/8838931.htm
- http://m.wap.fcful.cn/nnews/176521.htm
- http://m.wap.fcful.cn/nnews/54124.htm
- http://m.wap.fcful.cn/nnews/9742029.htm
- http://m.wap.fcful.cn/nnews/808795.htm
- http://m.wap.fcful.cn/nnews/706378.htm
- http://m.wap.fcful.cn/nnews/7431.htm
- http://m.wap.fcful.cn/nnews/3430.htm
- http://m.wap.fcful.cn/nnews/91489.htm
- http://m.wap.fcful.cn/nnews/4226381.htm
- http://m.wap.fcful.cn/nnews/7921925.htm
- http://m.wap.fcful.cn/nnews/9910613.htm
- http://m.wap.fcful.cn/nnews/0852812.htm
- http://m.wap.fcful.cn/nnews/09692.htm
- http://m.wap.fcful.cn/nnews/4762.htm
- http://m.wap.fcful.cn/nnews/68794.htm
- http://m.wap.fcful.cn/nnews/8884827.htm

## 项目结构

```
wapinfo-aggregator/
├── wapinfo.py                  # 主入口脚本，解析命令行参数并调度抓取流程
├── requirements.txt            # Python 依赖清单，记录所有外部库及版本约束
├── config.yaml                 # 全局配置文件，包含请求间隔、超时、重试策略等
├── src/                        # 核心源代码目录
│   ├── core/                   # 核心模块
│   │   ├── fetcher.py          # 请求发送与响应接收，含代理和重试逻辑
│   │   ├── parser.py           # HTML 解析与字段提取，封装 XPath 规则
│   │   └── dedup.py            # 基于 URL 指纹与内容哈希的去重过滤器
│   ├── utils/                  # 辅助工具集
│   │   ├── encoding.py         # 自动检测并转换字符编码
│   │   ├── logger.py           # 日志初始化与分级输出
│   │   └── exporter.py         # 将结构化数据导出为 JSONL 或 Markdown
│   └── models/                 # 数据模型定义
│       ├── article.py          # 文章实体类，定义字段与验证方法
│       └── task.py             # 任务队列模型，管理抓取状态与进度
├── tests/                      # 单元测试与集成测试用例
│   ├── test_fetcher.py         # 测试请求发送模块的各项功能
│   ├── test_parser.py          # 测试不同页面模板的解析准确性
│   └── fixtures/               # 测试用的固定 HTML 样本文件
├── docs/                       # 完整文档目录
│   ├── usage.md                # 用户使用手册
│   ├── development.md          # 开发与扩展指南
│   └── api.md                  # 自动生成的 API 参考文档
├── scripts/                    # 运维辅助脚本
│   ├── daily_run.sh            # 每日定时抓取的 cron 调用脚本
│   └── clean_cache.py          # 清理过期缓存与临时文件
└── README.md                   # 项目简介与快速入门
```

## 贡献指南

1. 阅读开发文档 docs/development.md 了解项目整体架构、代码风格与测试要求，确保理解各模块的职责边界。

2. 在 GitHub Issues 中搜索现有话题或创建新议题，描述您想要修复的问题或新增的功能，等待维护者确认后再开始编码。

3. 从 main 分支创建新的功能分支，命名遵循 feature/xxx 或 fix/xxx 格式，在该分支上进行开发，并确保所有现有单元测试能够通过。

4. 为新功能或修复补丁编写对应的单元测试，测试用例应放置于 tests/ 目录下，并保证代码覆盖率不低于 80%。

5. 提交 Pull Request 至 main 分支，在 PR 描述中清晰关联对应的 Issue 编号，并简要说明改动内容与测试结果，等待代码审查。

## 常见问题

问：抓取过程中频繁遇到 HTTP 403 或 429 状态码，如何解决？

答：此类状态码通常表示目标服务器开启了反爬保护。建议采取以下措施：降低并发线程数（例如从 4 调整为 2）、增大请求间隔（可在 config.yaml 中设置 delay 参数）、配置代理轮换（在配置文件中启用 proxy_list 并填入可用代理地址）。此外，检查 User-Agent 是否被目标站点屏蔽，必要时切换为移动端常见的 UA 字符串。

问：输出文件中的某些字段为空或乱码，应该如何处理？

答：字段为空通常是 XPath 规则未匹配到对应元素，可能是页面结构发生了变化。请先检查抓取的原始 HTML 是否存在该内容，然后调整 parser.py 中的抽取表达式。出现乱码则多为字符集检测失败，可在配置中强制指定 encoding 字段为 gbk 或 utf-8，或升级 charset-normalizer 到最新版本以改善检测准确率。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
