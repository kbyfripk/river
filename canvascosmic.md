# WAPLink Navigator

WAPLink Navigator 是一个面向移动端资讯聚合与短链导航的开源工具集，专门用于批量采集、清洗、归档和重组织来自移动 WAP 站点的海量新闻内容链接。该项目定位为技术资源与外链汇总站，服务于需要从半结构化 WAP 页面中提取可读内容并建立稳定跳转索引的开发者、数据工程师与内容研究人员。WAPLink Navigator 不依赖可视化浏览器，基于轻量级 HTTP 客户端与规则化解析器完成链接抽取与元信息标记，适用于低带宽、高并发的批量处理场景。当前批次覆盖第 165/240 批，共 250 个资源链接，全部来源于移动 WAP 域名 gqskj.cn 的新闻子目录。

## 功能概览

批量链接抓取：基于异步 HTTP 会话池并发请求目标域名下的 .htm 资源，支持自定义并发度与重试策略，自动处理超时与临时跳转。

元信息提取：从每个目标页面的 HTML 结构中抽取标题、发布时间、正文摘要、来源字段，输出结构化 JSON 记录，保留原始 URL 作为主键。

链接状态检测：对每个抓取到的链接执行响应状态码校验、内容长度校验和 MIME 类型识别，标记异常链接（404、500、空内容、非文本响应）。

数据持久化：支持将处理结果写入 SQLite 本地数据库或 CSV 文件，包含抓取时间戳、响应耗时、内容哈希值等运维字段。

增量更新机制：基于已存储记录的 URL 指纹与最后修改时间，仅对变更或新增的链接执行重新抓取，避免重复处理。

规则配置外部化：所有解析规则（XPath、CSS 选择器、正则表达式）通过 YAML 配置文件加载，无需修改源代码即可适配不同页面模板。

输出格式插件：内置 JSON Lines、CSV、Markdown 表格三种导出格式，可扩展自定义输出插件，便于接入下游数据处理流水线。

日志与监控：分级日志记录每次请求的详细信息，包括请求头、响应摘要、错误栈，支持将指标推送至 Prometheus 网关。

## 应用场景

移动 WAP 站点内容归档：对于需要长期保存移动新闻站点历史文章的团队，可使用 WAPLink Navigator 定期抓取指定目录下的所有 .htm 页面，生成带时间戳的内容快照，便于后续检索与回溯。

外链关系分析：研究人员可利用该工具批量获取某个 WAP 域名下的全部内部链接，构建站内链接拓扑图，分析页面之间的引用关系与中心度，识别核心内容页。

数据清洗与格式转换：当原始 WAP 页面包含大量广告脚本或非结构化排版时，可通过配置解析规则抽取纯净正文，输出为纯文本或 Markdown 格式，供 NLP 模型训练使用。

监控链接可用性：运维人员可设定定时任务，对所有已收录的链接执行周期性状态检查，生成可用性报告，及时发现被删除或迁移的页面。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/waplink-navigator/waplink-navigator.git
cd waplink-navigator

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行示例批处理任务（处理第一批 50 个链接）
python run_batch.py --batch-id 165 --input-file ./data/links_165.txt --output-dir ./output --config ./config/default.yaml
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.10 或 3.11 以获得更好的异步性能 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发请求管理 |
| lxml | 4.9.0 及以上 | HTML 解析引擎，支持 XPath 和 CSS 选择器 |
| pyyaml | 6.0 及以上 | 配置文件解析器，用于加载外部规则 |
| sqlite3 | 系统自带 | 本地数据库存储，Python 标准库内置无需额外安装 |
| prometheus-client | 0.17.0 及以上 | 可选依赖，用于指标导出 |
| pytest | 7.0 及以上 | 开发环境依赖，用于运行单元测试 |
| black | 22.0 及以上 | 开发环境依赖，用于代码格式化 |
| mypy | 1.0 及以上 | 开发环境依赖，用于静态类型检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|----------|
| 用户手册 | docs/user_guide.md | 如何安装、配置、运行批处理任务；如何理解输出文件格式；日志级别如何调整 |
| 配置参考 | docs/config_reference.md | YAML 配置文件中每个字段的含义；解析规则如何编写；超时与重试参数的推荐值 |
| 开发指南 | docs/development.md | 代码目录结构说明；如何新增一个输出插件；如何提交 PR 及编码规范 |
| API 参考 | docs/api_reference.md | 核心类与函数的签名、参数说明、异常类型；异步会话管理器的使用示例 |
| 运维手册 | docs/operations.md | 生产环境部署建议；数据库备份策略；监控指标含义与告警阈值设置 |
| 常见问题 | docs/faq.md | 链接抓取失败的常见原因；如何处理反爬机制；数据库迁移注意事项 |

## 资源列表

- http://m.wap.gqskj.cn/snews/5393840.htm
- http://m.wap.gqskj.cn/snews/108699.htm
- http://m.wap.gqskj.cn/snews/07446.htm
- http://m.wap.gqskj.cn/snews/5093909.htm
- http://m.wap.gqskj.cn/snews/0940.htm
- http://m.wap.gqskj.cn/snews/5733791.htm
- http://m.wap.gqskj.cn/snews/8459.htm
- http://m.wap.gqskj.cn/snews/918814.htm
- http://m.wap.gqskj.cn/snews/4290.htm
- http://m.wap.gqskj.cn/snews/480819.htm
- http://m.wap.gqskj.cn/snews/7581.htm
- http://m.wap.gqskj.cn/snews/13301.htm
- http://m.wap.gqskj.cn/snews/3806390.htm
- http://m.wap.gqskj.cn/snews/507815.htm
- http://m.wap.gqskj.cn/snews/67700.htm
- http://m.wap.gqskj.cn/snews/2987278.htm
- http://m.wap.gqskj.cn/snews/476886.htm
- http://m.wap.gqskj.cn/snews/607570.htm
- http://m.wap.gqskj.cn/snews/4271.htm
- http://m.wap.gqskj.cn/snews/18907.htm
- http://m.wap.gqskj.cn/snews/67845.htm
- http://m.wap.gqskj.cn/snews/16991.htm
- http://m.wap.gqskj.cn/snews/312000.htm
- http://m.wap.gqskj.cn/snews/8190511.htm
- http://m.wap.gqskj.cn/snews/82760.htm
- http://m.wap.gqskj.cn/snews/031048.htm
- http://m.wap.gqskj.cn/snews/29058.htm
- http://m.wap.gqskj.cn/snews/417545.htm
- http://m.wap.gqskj.cn/snews/29736.htm
- http://m.wap.gqskj.cn/snews/589580.htm
- http://m.wap.gqskj.cn/snews/275496.htm
- http://m.wap.gqskj.cn/snews/0354346.htm
- http://m.wap.gqskj.cn/snews/81757.htm
- http://m.wap.gqskj.cn/snews/1701.htm
- http://m.wap.gqskj.cn/snews/3772188.htm
- http://m.wap.gqskj.cn/snews/386799.htm
- http://m.wap.gqskj.cn/snews/42158.htm
- http://m.wap.gqskj.cn/snews/2452492.htm
- http://m.wap.gqskj.cn/snews/6743.htm
- http://m.wap.gqskj.cn/snews/0013077.htm
- http://m.wap.gqskj.cn/snews/66866.htm
- http://m.wap.gqskj.cn/snews/4982548.htm
- http://m.wap.gqskj.cn/snews/16664.htm
- http://m.wap.gqskj.cn/snews/68270.htm
- http://m.wap.gqskj.cn/snews/035879.htm
- http://m.wap.gqskj.cn/snews/98540.htm
- http://m.wap.gqskj.cn/snews/3578.htm
- http://m.wap.gqskj.cn/snews/5522592.htm
- http://m.wap.gqskj.cn/snews/292185.htm
- http://m.wap.gqskj.cn/snews/25036.htm
- http://m.wap.gqskj.cn/snews/74506.htm
- http://m.wap.gqskj.cn/snews/91403.htm
- http://m.wap.gqskj.cn/snews/137724.htm
- http://m.wap.gqskj.cn/snews/590044.htm
- http://m.wap.gqskj.cn/snews/82325.htm
- http://m.wap.gqskj.cn/snews/574590.htm
- http://m.wap.gqskj.cn/snews/977898.htm
- http://m.wap.gqskj.cn/snews/7268.htm
- http://m.wap.gqskj.cn/snews/7805638.htm
- http://m.wap.gqskj.cn/snews/5192378.htm
- http://m.wap.gqskj.cn/snews/8889401.htm
- http://m.wap.gqskj.cn/snews/41009.htm
- http://m.wap.gqskj.cn/snews/88018.htm
- http://m.wap.gqskj.cn/snews/5662349.htm
- http://m.wap.gqskj.cn/snews/228829.htm
- http://m.wap.gqskj.cn/snews/81056.htm
- http://m.wap.gqskj.cn/snews/4114558.htm
- http://m.wap.gqskj.cn/snews/2192.htm
- http://m.wap.gqskj.cn/snews/2408407.htm
- http://m.wap.gqskj.cn/snews/94824.htm
- http://m.wap.gqskj.cn/snews/5149.htm
- http://m.wap.gqskj.cn/snews/298444.htm
- http://m.wap.gqskj.cn/snews/4272.htm
- http://m.wap.gqskj.cn/snews/0928.htm
- http://m.wap.gqskj.cn/snews/350199.htm
- http://m.wap.gqskj.cn/snews/268088.htm
- http://m.wap.gqskj.cn/snews/09059.htm
- http://m.wap.gqskj.cn/snews/4648843.htm
- http://m.wap.gqskj.cn/snews/798038.htm
- http://m.wap.gqskj.cn/snews/26391.htm
- http://m.wap.gqskj.cn/snews/62373.htm
- http://m.wap.gqskj.cn/snews/8477084.htm
- http://m.wap.gqskj.cn/snews/7452621.htm
- http://m.wap.gqskj.cn/snews/13755.htm
- http://m.wap.gqskj.cn/snews/664352.htm
- http://m.wap.gqskj.cn/snews/4381.htm
- http://m.wap.gqskj.cn/snews/992517.htm
- http://m.wap.gqskj.cn/snews/1347851.htm
- http://m.wap.gqskj.cn/snews/358363.htm
- http://m.wap.gqskj.cn/snews/7883285.htm
- http://m.wap.gqskj.cn/snews/97312.htm
- http://m.wap.gqskj.cn/snews/067619.htm
- http://m.wap.gqskj.cn/snews/4555371.htm
- http://m.wap.gqskj.cn/snews/12592.htm
- http://m.wap.gqskj.cn/snews/989216.htm
- http://m.wap.gqskj.cn/snews/3027389.htm
- http://m.wap.gqskj.cn/snews/712928.htm
- http://m.wap.gqskj.cn/snews/6865785.htm
- http://m.wap.gqskj.cn/snews/9903.htm
- http://m.wap.gqskj.cn/snews/164657.htm
- http://m.wap.gqskj.cn/snews/053027.htm
- http://m.wap.gqskj.cn/snews/7590.htm
- http://m.wap.gqskj.cn/snews/845471.htm
- http://m.wap.gqskj.cn/snews/7135386.htm
- http://m.wap.gqskj.cn/snews/14930.htm
- http://m.wap.gqskj.cn/snews/6720.htm
- http://m.wap.gqskj.cn/snews/3322393.htm
- http://m.wap.gqskj.cn/snews/4202273.htm
- http://m.wap.gqskj.cn/snews/1616637.htm
- http://m.wap.gqskj.cn/snews/0417.htm
- http://m.wap.gqskj.cn/snews/0946155.htm
- http://m.wap.gqskj.cn/snews/5891288.htm
- http://m.wap.gqskj.cn/snews/788607.htm
- http://m.wap.gqskj.cn/snews/13026.htm
- http://m.wap.gqskj.cn/snews/98648.htm
- http://m.wap.gqskj.cn/snews/44226.htm
- http://m.wap.gqskj.cn/snews/2177579.htm
- http://m.wap.gqskj.cn/snews/6563.htm
- http://m.wap.gqskj.cn/snews/032281.htm
- http://m.wap.gqskj.cn/snews/94006.htm
- http://m.wap.gqskj.cn/snews/006469.htm
- http://m.wap.gqskj.cn/snews/1847694.htm
- http://m.wap.gqskj.cn/snews/8827991.htm
- http://m.wap.gqskj.cn/snews/12570.htm
- http://m.wap.gqskj.cn/snews/60564.htm
- http://m.wap.gqskj.cn/snews/7471199.htm
- http://m.wap.gqskj.cn/snews/678952.htm
- http://m.wap.gqskj.cn/snews/7739.htm
- http://m.wap.gqskj.cn/snews/252714.htm
- http://m.wap.gqskj.cn/snews/604713.htm
- http://m.wap.gqskj.cn/snews/472607.htm
- http://m.wap.gqskj.cn/snews/5062261.htm
- http://m.wap.gqskj.cn/snews/14079.htm
- http://m.wap.gqskj.cn/snews/2529.htm
- http://m.wap.gqskj.cn/snews/5622.htm
- http://m.wap.gqskj.cn/snews/3222809.htm
- http://m.wap.gqskj.cn/snews/2078.htm
- http://m.wap.gqskj.cn/snews/6590283.htm
- http://m.wap.gqskj.cn/snews/885841.htm
- http://m.wap.gqskj.cn/snews/2143.htm
- http://m.wap.gqskj.cn/snews/1424788.htm
- http://m.wap.gqskj.cn/snews/80418.htm
- http://m.wap.gqskj.cn/snews/74027.htm
- http://m.wap.gqskj.cn/snews/80146.htm
- http://m.wap.gqskj.cn/snews/830989.htm
- http://m.wap.gqskj.cn/snews/1394.htm
- http://m.wap.gqskj.cn/snews/5910.htm
- http://m.wap.gqskj.cn/snews/41615.htm
- http://m.wap.gqskj.cn/snews/41235.htm
- http://m.wap.gqskj.cn/snews/5282.htm
- http://m.wap.gqskj.cn/snews/6410275.htm
- http://m.wap.gqskj.cn/snews/0635.htm
- http://m.wap.gqskj.cn/snews/6596.htm
- http://m.wap.gqskj.cn/snews/13789.htm
- http://m.wap.gqskj.cn/snews/70066.htm
- http://m.wap.gqskj.cn/snews/6931229.htm
- http://m.wap.gqskj.cn/snews/8406963.htm
- http://m.wap.gqskj.cn/snews/30259.htm
- http://m.wap.gqskj.cn/snews/715861.htm
- http://m.wap.gqskj.cn/snews/833042.htm
- http://m.wap.gqskj.cn/snews/5049489.htm
- http://m.wap.gqskj.cn/snews/1494.htm
- http://m.wap.gqskj.cn/snews/21736.htm
- http://m.wap.gqskj.cn/snews/4825.htm
- http://m.wap.gqskj.cn/snews/69670.htm
- http://m.wap.gqskj.cn/snews/246389.htm
- http://m.wap.gqskj.cn/snews/2690.htm
- http://m.wap.gqskj.cn/snews/9617.htm
- http://m.wap.gqskj.cn/snews/59407.htm
- http://m.wap.gqskj.cn/snews/6398.htm
- http://m.wap.gqskj.cn/snews/531748.htm
- http://m.wap.gqskj.cn/snews/995293.htm
- http://m.wap.gqskj.cn/snews/53581.htm
- http://m.wap.gqskj.cn/snews/064452.htm
- http://m.wap.gqskj.cn/snews/00952.htm
- http://m.wap.gqskj.cn/snews/538644.htm
- http://m.wap.gqskj.cn/snews/912057.htm
- http://m.wap.gqskj.cn/snews/901851.htm
- http://m.wap.gqskj.cn/snews/235148.htm
- http://m.wap.gqskj.cn/snews/80127.htm
- http://m.wap.gqskj.cn/snews/8517181.htm
- http://m.wap.gqskj.cn/snews/5584307.htm
- http://m.wap.gqskj.cn/snews/4116082.htm
- http://m.wap.gqskj.cn/snews/6036.htm
- http://m.wap.gqskj.cn/snews/323806.htm
- http://m.wap.gqskj.cn/snews/5743.htm
- http://m.wap.gqskj.cn/snews/192365.htm
- http://m.wap.gqskj.cn/snews/2814679.htm
- http://m.wap.gqskj.cn/snews/9338559.htm
- http://m.wap.gqskj.cn/snews/420600.htm
- http://m.wap.gqskj.cn/snews/580301.htm
- http://m.wap.gqskj.cn/snews/29602.htm
- http://m.wap.gqskj.cn/snews/6331845.htm
- http://m.wap.gqskj.cn/snews/776789.htm
- http://m.wap.gqskj.cn/snews/0954581.htm
- http://m.wap.gqskj.cn/snews/4405.htm
- http://m.wap.gqskj.cn/snews/8928.htm
- http://m.wap.gqskj.cn/snews/6456510.htm
- http://m.wap.gqskj.cn/snews/724047.htm
- http://m.wap.gqskj.cn/snews/80448.htm
- http://m.wap.gqskj.cn/snews/51192.htm
- http://m.wap.gqskj.cn/snews/08156.htm
- http://m.wap.gqskj.cn/snews/264767.htm
- http://m.wap.gqskj.cn/snews/1334688.htm
- http://m.wap.gqskj.cn/snews/0905.htm
- http://m.wap.gqskj.cn/snews/892354.htm
- http://m.wap.gqskj.cn/snews/23008.htm
- http://m.wap.gqskj.cn/snews/431198.htm
- http://m.wap.gqskj.cn/snews/3403231.htm
- http://m.wap.gqskj.cn/snews/1680659.htm
- http://m.wap.gqskj.cn/snews/343529.htm
- http://m.wap.gqskj.cn/snews/24513.htm
- http://m.wap.gqskj.cn/snews/7768131.htm
- http://m.wap.gqskj.cn/snews/966907.htm
- http://m.wap.gqskj.cn/snews/2206086.htm
- http://m.wap.gqskj.cn/snews/136854.htm
- http://m.wap.gqskj.cn/snews/6063.htm
- http://m.wap.gqskj.cn/snews/4239103.htm
- http://m.wap.gqskj.cn/snews/9769.htm
- http://m.wap.gqskj.cn/snews/236551.htm
- http://m.wap.gqskj.cn/snews/5826989.htm
- http://m.wap.gqskj.cn/snews/001952.htm
- http://m.wap.gqskj.cn/snews/368072.htm
- http://m.wap.gqskj.cn/snews/6228.htm
- http://m.wap.gqskj.cn/snews/21251.htm
- http://m.wap.gqskj.cn/snews/43841.htm
- http://m.wap.gqskj.cn/snews/78224.htm
- http://m.wap.gqskj.cn/snews/7004792.htm
- http://m.wap.gqskj.cn/snews/892580.htm
- http://m.wap.gqskj.cn/snews/749807.htm
- http://m.wap.gqskj.cn/snews/003180.htm
- http://m.wap.gqskj.cn/snews/366662.htm
- http://m.wap.gqskj.cn/snews/0916900.htm
- http://m.wap.gqskj.cn/snews/4377.htm
- http://m.wap.gqskj.cn/snews/07377.htm
- http://m.wap.gqskj.cn/snews/53508.htm
- http://m.wap.gqskj.cn/snews/16979.htm
- http://m.wap.gqskj.cn/snews/6923.htm
- http://m.wap.gqskj.cn/snews/078799.htm
- http://m.wap.gqskj.cn/snews/0374.htm
- http://m.wap.gqskj.cn/snews/64510.htm
- http://m.wap.gqskj.cn/snews/6276590.htm
- http://m.wap.gqskj.cn/snews/12646.htm
- http://m.wap.gqskj.cn/snews/8953585.htm
- http://m.wap.gqskj.cn/snews/15182.htm
- http://m.wap.gqskj.cn/snews/8390.htm
- http://m.wap.gqskj.cn/snews/3039.htm
- http://m.wap.gqskj.cn/snews/19891.htm
- http://m.wap.gqskj.cn/snews/2753.htm
- http://m.wap.gqskj.cn/snews/9712986.htm

## 项目结构

```
waplink-navigator/
├── src/                                   # 核心源代码目录
│   ├── fetcher/                           # 请求抓取子模块
│   │   ├── session_pool.py                # 异步会话池管理，控制并发连接数
│   │   ├── request_builder.py             # 构造请求头、代理、超时参数
│   │   └── response_handler.py            # 处理响应状态、重定向、解码
│   ├── parser/                            # 内容解析子模块
│   │   ├── html_cleaner.py                # 清洗 HTML 标签，提取正文区块
│   │   ├── rule_engine.py                 # 加载 YAML 规则并执行 XPath 抽取
│   │   └── meta_extractor.py              # 抽取标题、日期、来源等元数据
│   ├── storage/                           # 存储子模块
│   │   ├── database.py                    # SQLite 建表、插入、更新操作
│   │   ├── csv_writer.py                  # 导出为 CSV 格式
│   │   └── jsonl_writer.py                # 导出为 JSON Lines 格式
│   ├── scheduler/                         # 调度与增量更新子模块
│   │   ├── batch_runner.py                # 批处理任务主流程控制器
│   │   ├── fingerprint.py                 # 计算 URL 与内容指纹用于去重
│   │   └── incremental.py                 # 对比上次抓取时间，决定是否重抓
│   └── utils/                             # 通用工具函数
│       ├── logger.py                      # 日志格式化与分级输出
│       ├── metrics.py                     # Prometheus 指标埋点
│       └── validators.py                  # URL 校验、内容长度校验
├── config/                                # 配置文件目录
│   ├── default.yaml                       # 默认全局配置（并发度、超时、重试）
│   ├── rules_news.yaml                    # 针对新闻类页面的解析规则
│   └── rules_general.yaml                 # 通用后备解析规则
├── tests/                                 # 单元测试与集成测试
│   ├── test_fetcher.py                    # 会话池与请求构造的测试用例
│   ├── test_parser.py                     # 解析引擎与规则加载的测试用例
│   └── test_storage.py                    # 数据库与导出功能的测试用例
├── scripts/                               # 运维与辅助脚本
│   ├── run_batch.py                       # 命令行入口，接受批次参数
│   ├── export_report.py                   # 从数据库生成统计报告
│   └── clean_duplicates.py                # 清理重复记录工具
├── docs/                                  # 项目文档
│   ├── user_guide.md                      # 用户手册
│   ├── config_reference.md                # 配置参考
│   └── development.md                     # 开发指南
├── data/                                  # 示例输入输出数据（不包含生产数据）
│   ├── sample_links.txt                   # 示例链接列表
│   └── sample_output.jsonl                # 示例输出结果
├── requirements.txt                       # 生产环境依赖列表
├── requirements-dev.txt                   # 开发环境额外依赖
├── setup.py                               # 项目安装脚本
├── README.md                              # 本文件
└── LICENSE                                # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub Issues 中查找或新建一个与您想要修复或实现的功能相关的议题，等待维护者确认后再开始编码，避免重复工作或方向偏差。
2. 克隆项目到本地，创建以 feature/ 或 fix/ 为前缀的分支，例如 feature/add-json-output-plugin，确保分支命名清晰反映变更内容。
3. 编写代码时遵循项目已配置的 black 和 mypy 规则，提交前运行 pytest 确保所有现有测试通过，并为新增功能补充相应的测试用例。
4. 提交 Pull Request 时填写标准模板，说明变更动机、实现方式、测试覆盖情况，并关联相关 Issue 编号，等待至少一位维护者审阅。
5. 更新 docs/ 目录下对应的文档文件，尤其是当变更影响到配置格式、命令行参数或输出结构时，确保用户手册与代码保持同步。

## 常见问题

**Q: 抓取过程中出现大量超时或连接重置错误，如何调整？**

A: 此类问题通常由目标服务器限流或网络不稳定引起。建议首先降低 config/default.yaml 中的并发度（concurrency 参数）至 5 以下，同时增大超时时间（timeout 参数）至 30 秒。若仍频繁失败，可启用 request_builder 中的代理轮换功能，或使用 incremental 模式仅重抓失败链接。

**Q: 解析规则不适用于某些页面，导致提取的标题或正文为空，如何排查？**

A: 首先检查该页面的实际 HTML 结构是否与规则中的 XPath 匹配。可在 parser/rule_engine.py 中添加调试日志，输出抽取前的 HTML 片段。若发现模板差异，建议在 config/rules_news.yaml 中新增一条针对该页面 URL 模式的正则匹配规则，并指定专用的 XPath 表达式。项目支持规则优先级顺序匹配，具体语法参考 config_reference.md。

**Q: 数据库文件体积增长过快，如何优化存储？**

A: 默认 SQLite 数据库会保存每次抓取的完整元数据和内容哈希。如果不需要保留历史变更记录，可定期执行 scripts/clean_duplicates.py 脚本，仅保留每个 URL 的最新一条记录。此外，可在 config/default.yaml 中启用内容摘要存储模式（存储前 200 字符而非全文），或在导出后手动执行 VACUUM 命令回收空间。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
