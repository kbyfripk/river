# XNews Link Aggregator

XNews Link Aggregator 是一个面向移动端资讯聚合与结构化数据提取的开源工具集，专注于从标准化路径的新闻源中批量抓取、解析和归档 HTML 内容。该项目主要服务于数据采集工程师、舆情分析研究人员以及内容管理系统运维人员，解决从大量同构 URL 中高效提取元数据、正文结构化信息及附件链接的重复性劳动问题。

项目核心定位为轻量级链接调度与内容规范化管道，不依赖重型浏览器引擎，通过可配置的请求头伪装、重试策略与响应编码自动检测，实现对目标域名下海量 .htm 页面的稳定访问。内置的链接状态监控模块能够记录每次请求的响应码、耗时与内容摘要，为后续的数据质量分析提供原始依据。

## 功能概览

批量链接导入与校验 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入目标链接，自动去重并校验协议与域名白名单。

可插拔的解析管道 提供基于正则表达式与 XPath 两种模式的内容提取器，用户可根据目标页面结构调整解析规则，无需修改核心代码。

响应自动重试与降级 当目标服务器返回 5xx 或超时时，系统按指数退避策略自动重试最多 3 次；若持续失败则标记为异常并跳过，不影响后续链接处理。

内容摘要与元数据生成 对每个成功请求的页面自动提取标题、字符编码、正文长度、图片数量及外链域名列表，生成 JSON 格式的摘要报告。

增量存储与去重归档 支持将解析结果追加写入 SQLite 本地数据库或按日期分片的 JSONL 文件，避免重复处理已归档的链接。

代理与请求头轮换 内置常见 User-Agent 池，支持 HTTP/HTTPS 代理配置，适用于需要频繁切换出口 IP 的大规模采集场景。

命令行与 API 双模式 提供 CLI 工具用于一次性任务执行，同时暴露 RESTful API 接口供外部系统调用，方便嵌入自动化工作流。

## 应用场景

舆情监控系统的数据采集层 在舆论分析平台中，运维人员可将本项目部署为定时任务，每日凌晨自动抓取指定批次链接，将解析后的正文与元数据推送至 Kafka 或 Elasticsearch，供后续情感分析模块消费。

移动端新闻内容归档 内容管理员需要对特定域名下的历史新闻页面进行持久化存储时，可利用本工具的增量归档功能，将 .htm 文件原文及提取的纯文本内容按日期目录保存至对象存储，防止源站内容下线或改版导致数据丢失。

链接存活性与变化检测 质量保障团队可将本工具作为链路监控探针，定期请求大量 URL 并记录响应状态与内容哈希值，当检测到响应码异常或内容突变时触发告警，及时发现源站故障或内容被篡改。

数据迁移前的格式预检 在将旧版新闻系统迁移至新 CMS 之前，工程师可通过本工具批量导出所有链接的标题、发布时间与正文结构，提前发现编码不一致、标签缺失等数据质量问题，降低迁移风险。

## 快速开始

以下命令演示了从克隆代码到运行首次采集的完整流程。请确保已安装 Git 与 Python 3.9 及以上版本。

```bash
git clone https://github.com/example/xnews-link-aggregator.git
cd xnews-link-aggregator
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt
cp config.example.yaml config.yaml
python run.py --input urls.txt --output ./data --format jsonl
```

其中 urls.txt 为每行一个 URL 的文本文件，示例内容可从项目根目录下的 sample_urls.txt 获得。首次运行前需编辑 config.yaml 设置目标域名白名单及请求间隔。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 - 3.11 | 核心运行环境，3.12 以上暂未进行完整兼容性测试 |
| requests | >=2.28.0 | HTTP 请求库，用于发送 GET 请求及管理会话 |
| lxml | >=4.9.0 | XPath 解析引擎，用于结构化内容提取 |
| beautifulsoup4 | >=4.11.0 | HTML 解析辅助库，提供更健壮的树遍历能力 |
| sqlite3 | 内置模块 | 本地数据库存储引擎，用于增量去重与历史记录查询 |
| pyyaml | >=6.0 | YAML 配置文件解析，支持复杂嵌套配置项 |
| click | >=8.1.0 | CLI 命令行参数解析框架，提供子命令与选项管理 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user_guide.md | 如何安装、配置、运行采集任务，以及输出文件的格式说明 |
| 开发者指南 | /docs/developer_guide.md | 如何编写自定义解析插件、扩展请求中间件及参与核心代码贡献 |
| API 参考 | /docs/api_reference.md | RESTful 接口的端点定义、请求参数与响应数据结构说明 |
| 运维手册 | /docs/operations.md | 生产环境部署建议、日志轮转策略、性能调优参数与常见故障排查 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/0696423.htm
- http://m.3g.gqskj.cn/xnews/7087002.htm
- http://m.3g.gqskj.cn/xnews/0241951.htm
- http://m.3g.gqskj.cn/xnews/2990398.htm
- http://m.3g.gqskj.cn/xnews/368232.htm
- http://m.3g.gqskj.cn/xnews/5492.htm
- http://m.3g.gqskj.cn/xnews/03770.htm
- http://m.3g.gqskj.cn/xnews/8777549.htm
- http://m.3g.gqskj.cn/xnews/9932793.htm
- http://m.3g.gqskj.cn/xnews/2970140.htm
- http://m.3g.gqskj.cn/xnews/415623.htm
- http://m.3g.gqskj.cn/xnews/4593.htm
- http://m.3g.gqskj.cn/xnews/35003.htm
- http://m.3g.gqskj.cn/xnews/2854163.htm
- http://m.3g.gqskj.cn/xnews/5850760.htm
- http://m.3g.gqskj.cn/xnews/026782.htm
- http://m.3g.gqskj.cn/xnews/12561.htm
- http://m.3g.gqskj.cn/xnews/137390.htm
- http://m.3g.gqskj.cn/xnews/2677414.htm
- http://m.3g.gqskj.cn/xnews/482361.htm
- http://m.3g.gqskj.cn/xnews/7528.htm
- http://m.3g.gqskj.cn/xnews/175979.htm
- http://m.3g.gqskj.cn/xnews/529051.htm
- http://m.3g.gqskj.cn/xnews/5238.htm
- http://m.3g.gqskj.cn/xnews/76162.htm
- http://m.3g.gqskj.cn/xnews/3934.htm
- http://m.3g.gqskj.cn/xnews/10602.htm
- http://m.3g.gqskj.cn/xnews/8010.htm
- http://m.3g.gqskj.cn/xnews/4605.htm
- http://m.3g.gqskj.cn/xnews/1822.htm
- http://m.3g.gqskj.cn/xnews/7908.htm
- http://m.3g.gqskj.cn/xnews/78358.htm
- http://m.3g.gqskj.cn/xnews/8538.htm
- http://m.3g.gqskj.cn/xnews/6257.htm
- http://m.3g.gqskj.cn/xnews/057929.htm
- http://m.3g.gqskj.cn/xnews/7464064.htm
- http://m.3g.gqskj.cn/xnews/5937882.htm
- http://m.3g.gqskj.cn/xnews/4059043.htm
- http://m.3g.gqskj.cn/xnews/9832.htm
- http://m.3g.gqskj.cn/xnews/26691.htm
- http://m.3g.gqskj.cn/xnews/0821.htm
- http://m.3g.gqskj.cn/xnews/8632052.htm
- http://m.3g.gqskj.cn/xnews/777710.htm
- http://m.3g.gqskj.cn/xnews/46424.htm
- http://m.3g.gqskj.cn/xnews/1076.htm
- http://m.3g.gqskj.cn/xnews/2797.htm
- http://m.3g.gqskj.cn/xnews/0344543.htm
- http://m.3g.gqskj.cn/xnews/385214.htm
- http://m.3g.gqskj.cn/xnews/27062.htm
- http://m.3g.gqskj.cn/xnews/5596386.htm
- http://m.3g.gqskj.cn/xnews/688790.htm
- http://m.3g.gqskj.cn/xnews/42346.htm
- http://m.3g.gqskj.cn/xnews/0222238.htm
- http://m.3g.gqskj.cn/xnews/119745.htm
- http://m.3g.gqskj.cn/xnews/675448.htm
- http://m.3g.gqskj.cn/xnews/797674.htm
- http://m.3g.gqskj.cn/xnews/6068111.htm
- http://m.3g.gqskj.cn/xnews/91774.htm
- http://m.3g.gqskj.cn/xnews/808166.htm
- http://m.3g.gqskj.cn/xnews/39767.htm
- http://m.3g.gqskj.cn/xnews/494230.htm
- http://m.3g.gqskj.cn/xnews/7229.htm
- http://m.3g.gqskj.cn/xnews/9650439.htm
- http://m.3g.gqskj.cn/xnews/33516.htm
- http://m.3g.gqskj.cn/xnews/035051.htm
- http://m.3g.gqskj.cn/xnews/59311.htm
- http://m.3g.gqskj.cn/xnews/28453.htm
- http://m.3g.gqskj.cn/xnews/559648.htm
- http://m.3g.gqskj.cn/xnews/7862.htm
- http://m.3g.gqskj.cn/xnews/0819.htm
- http://m.3g.gqskj.cn/xnews/627114.htm
- http://m.3g.gqskj.cn/xnews/9435.htm
- http://m.3g.gqskj.cn/xnews/54850.htm
- http://m.3g.gqskj.cn/xnews/95613.htm
- http://m.3g.gqskj.cn/xnews/5113.htm
- http://m.3g.gqskj.cn/xnews/65935.htm
- http://m.3g.gqskj.cn/xnews/9446986.htm
- http://m.3g.gqskj.cn/xnews/7540646.htm
- http://m.3g.gqskj.cn/xnews/435008.htm
- http://m.3g.gqskj.cn/xnews/5244960.htm
- http://m.3g.gqskj.cn/xnews/5701.htm
- http://m.3g.gqskj.cn/xnews/946847.htm
- http://m.3g.gqskj.cn/xnews/254791.htm
- http://m.3g.gqskj.cn/xnews/009049.htm
- http://m.3g.gqskj.cn/xnews/2436253.htm
- http://m.3g.gqskj.cn/xnews/67459.htm
- http://m.3g.gqskj.cn/xnews/11214.htm
- http://m.3g.gqskj.cn/xnews/628043.htm
- http://m.3g.gqskj.cn/xnews/7543.htm
- http://m.3g.gqskj.cn/xnews/3681285.htm
- http://m.3g.gqskj.cn/xnews/576183.htm
- http://m.3g.gqskj.cn/xnews/788566.htm
- http://m.3g.gqskj.cn/xnews/525561.htm
- http://m.3g.gqskj.cn/xnews/5695541.htm
- http://m.3g.gqskj.cn/xnews/67514.htm
- http://m.3g.gqskj.cn/xnews/7475.htm
- http://m.3g.gqskj.cn/xnews/108977.htm
- http://m.3g.gqskj.cn/xnews/374667.htm
- http://m.3g.gqskj.cn/xnews/111454.htm
- http://m.3g.gqskj.cn/xnews/5135.htm
- http://m.3g.gqskj.cn/xnews/8970480.htm
- http://m.3g.gqskj.cn/xnews/82536.htm
- http://m.3g.gqskj.cn/xnews/92524.htm
- http://m.3g.gqskj.cn/xnews/73178.htm
- http://m.3g.gqskj.cn/xnews/53345.htm
- http://m.3g.gqskj.cn/xnews/3410.htm
- http://m.3g.gqskj.cn/xnews/419380.htm
- http://m.3g.gqskj.cn/xnews/1184.htm
- http://m.3g.gqskj.cn/xnews/013433.htm
- http://m.3g.gqskj.cn/xnews/4534301.htm
- http://m.3g.gqskj.cn/xnews/7369.htm
- http://m.3g.gqskj.cn/xnews/785210.htm
- http://m.3g.gqskj.cn/xnews/5435.htm
- http://m.3g.gqskj.cn/xnews/7270.htm
- http://m.3g.gqskj.cn/xnews/73174.htm
- http://m.3g.gqskj.cn/xnews/3263.htm
- http://m.3g.gqskj.cn/xnews/723332.htm
- http://m.3g.gqskj.cn/xnews/685405.htm
- http://m.3g.gqskj.cn/xnews/4918604.htm
- http://m.3g.gqskj.cn/xnews/25808.htm
- http://m.3g.gqskj.cn/xnews/3092095.htm
- http://m.3g.gqskj.cn/xnews/9527.htm
- http://m.3g.gqskj.cn/xnews/4914.htm
- http://m.3g.gqskj.cn/xnews/5567.htm
- http://m.3g.gqskj.cn/xnews/4325.htm
- http://m.3g.gqskj.cn/xnews/0315918.htm
- http://m.3g.gqskj.cn/xnews/5395.htm
- http://m.3g.gqskj.cn/xnews/8961.htm
- http://m.3g.gqskj.cn/xnews/7299.htm
- http://m.3g.gqskj.cn/xnews/6394551.htm
- http://m.3g.gqskj.cn/xnews/9002.htm
- http://m.3g.gqskj.cn/xnews/4562.htm
- http://m.3g.gqskj.cn/xnews/93716.htm
- http://m.3g.gqskj.cn/xnews/71324.htm
- http://m.3g.gqskj.cn/xnews/2402553.htm
- http://m.3g.gqskj.cn/xnews/91360.htm
- http://m.3g.gqskj.cn/xnews/0708.htm
- http://m.3g.gqskj.cn/xnews/1845.htm
- http://m.3g.gqskj.cn/xnews/7707402.htm
- http://m.3g.gqskj.cn/xnews/2434498.htm
- http://m.3g.gqskj.cn/xnews/47609.htm
- http://m.3g.gqskj.cn/xnews/156139.htm
- http://m.3g.gqskj.cn/xnews/7479162.htm
- http://m.3g.gqskj.cn/xnews/3238.htm
- http://m.3g.gqskj.cn/xnews/67376.htm
- http://m.3g.gqskj.cn/xnews/6028.htm
- http://m.3g.gqskj.cn/xnews/2684.htm
- http://m.3g.gqskj.cn/xnews/11335.htm
- http://m.3g.gqskj.cn/xnews/9173.htm
- http://m.3g.gqskj.cn/xnews/17717.htm
- http://m.3g.gqskj.cn/xnews/1311353.htm
- http://m.3g.gqskj.cn/xnews/9939458.htm
- http://m.3g.gqskj.cn/xnews/0195327.htm
- http://m.3g.gqskj.cn/xnews/4632773.htm
- http://m.3g.gqskj.cn/xnews/01238.htm
- http://m.3g.gqskj.cn/xnews/0162.htm
- http://m.3g.gqskj.cn/xnews/6353642.htm
- http://m.3g.gqskj.cn/xnews/12921.htm
- http://m.3g.gqskj.cn/xnews/823194.htm
- http://m.3g.gqskj.cn/xnews/17520.htm
- http://m.3g.gqskj.cn/xnews/12076.htm
- http://m.3g.gqskj.cn/xnews/655377.htm
- http://m.3g.gqskj.cn/xnews/7585687.htm
- http://m.3g.gqskj.cn/xnews/1650.htm
- http://m.3g.gqskj.cn/xnews/8846122.htm
- http://m.3g.gqskj.cn/xnews/122291.htm
- http://m.3g.gqskj.cn/xnews/892605.htm
- http://m.3g.gqskj.cn/xnews/893303.htm
- http://m.3g.gqskj.cn/xnews/9766.htm
- http://m.3g.gqskj.cn/xnews/45587.htm
- http://m.3g.gqskj.cn/xnews/10595.htm
- http://m.3g.gqskj.cn/xnews/825730.htm
- http://m.3g.gqskj.cn/xnews/8536610.htm
- http://m.3g.gqskj.cn/xnews/60755.htm
- http://m.3g.gqskj.cn/xnews/9348.htm
- http://m.3g.gqskj.cn/xnews/94967.htm
- http://m.3g.gqskj.cn/xnews/684850.htm
- http://m.3g.gqskj.cn/xnews/0809.htm
- http://m.3g.gqskj.cn/xnews/9963.htm
- http://m.3g.gqskj.cn/xnews/4192.htm
- http://m.3g.gqskj.cn/xnews/711287.htm
- http://m.3g.gqskj.cn/xnews/01132.htm
- http://m.3g.gqskj.cn/xnews/03895.htm
- http://m.3g.gqskj.cn/xnews/98384.htm
- http://m.3g.gqskj.cn/xnews/056264.htm
- http://m.3g.gqskj.cn/xnews/2947787.htm
- http://m.3g.gqskj.cn/xnews/9373.htm
- http://m.3g.gqskj.cn/xnews/684364.htm
- http://m.3g.gqskj.cn/xnews/3220.htm
- http://m.3g.gqskj.cn/xnews/9234599.htm
- http://m.3g.gqskj.cn/xnews/5887.htm
- http://m.3g.gqskj.cn/xnews/090892.htm
- http://m.3g.gqskj.cn/xnews/9244646.htm
- http://m.3g.gqskj.cn/xnews/44211.htm
- http://m.3g.gqskj.cn/xnews/4974632.htm
- http://m.3g.gqskj.cn/xnews/7727864.htm
- http://m.3g.gqskj.cn/xnews/063770.htm
- http://m.3g.gqskj.cn/xnews/7621203.htm
- http://m.3g.gqskj.cn/xnews/239584.htm
- http://m.3g.gqskj.cn/xnews/7165737.htm
- http://m.3g.gqskj.cn/xnews/81891.htm
- http://m.3g.gqskj.cn/xnews/857686.htm
- http://m.3g.gqskj.cn/xnews/6182.htm
- http://m.3g.gqskj.cn/xnews/227118.htm
- http://m.3g.gqskj.cn/xnews/3747.htm
- http://m.3g.gqskj.cn/xnews/9805704.htm
- http://m.3g.gqskj.cn/xnews/8628.htm
- http://m.3g.gqskj.cn/xnews/71135.htm
- http://m.3g.gqskj.cn/xnews/7355252.htm
- http://m.3g.gqskj.cn/xnews/46061.htm
- http://m.3g.gqskj.cn/xnews/6058.htm
- http://m.3g.gqskj.cn/xnews/5381.htm
- http://m.3g.gqskj.cn/xnews/4242.htm
- http://m.3g.gqskj.cn/xnews/5196978.htm
- http://m.3g.gqskj.cn/xnews/108708.htm
- http://m.3g.gqskj.cn/xnews/635684.htm
- http://m.3g.gqskj.cn/xnews/34300.htm
- http://m.3g.gqskj.cn/xnews/0925.htm
- http://m.3g.gqskj.cn/xnews/3727715.htm
- http://m.3g.gqskj.cn/xnews/03646.htm
- http://m.3g.gqskj.cn/xnews/044255.htm
- http://m.3g.gqskj.cn/xnews/659484.htm
- http://m.3g.gqskj.cn/xnews/458729.htm
- http://m.3g.gqskj.cn/xnews/6788.htm
- http://m.3g.gqskj.cn/xnews/0151.htm
- http://m.3g.gqskj.cn/xnews/94491.htm
- http://m.3g.gqskj.cn/xnews/2012.htm
- http://m.3g.gqskj.cn/xnews/9222.htm
- http://m.3g.gqskj.cn/xnews/7774.htm
- http://m.3g.gqskj.cn/xnews/90596.htm
- http://m.3g.gqskj.cn/xnews/7674625.htm
- http://m.3g.gqskj.cn/xnews/893394.htm
- http://m.3g.gqskj.cn/xnews/409109.htm
- http://m.3g.gqskj.cn/xnews/5196.htm
- http://m.3g.gqskj.cn/xnews/7166.htm
- http://m.3g.gqskj.cn/xnews/5415.htm
- http://m.3g.gqskj.cn/xnews/84116.htm
- http://m.3g.gqskj.cn/xnews/3089637.htm
- http://m.3g.gqskj.cn/xnews/3645858.htm
- http://m.3g.gqskj.cn/xnews/1419.htm
- http://m.3g.gqskj.cn/xnews/515684.htm
- http://m.3g.gqskj.cn/xnews/6680091.htm
- http://m.3g.gqskj.cn/xnews/6416.htm
- http://m.3g.gqskj.cn/xnews/861400.htm
- http://m.3g.gqskj.cn/xnews/69182.htm
- http://m.3g.gqskj.cn/xnews/639672.htm
- http://m.3g.gqskj.cn/xnews/4314.htm
- http://m.3g.gqskj.cn/xnews/9512133.htm
- http://m.3g.gqskj.cn/xnews/479180.htm
- http://m.3g.gqskj.cn/xnews/76546.htm

## 项目结构

```
xnews-link-aggregator/
├── run.py                          # CLI 入口，解析命令行参数并调度核心流程
├── config.yaml                     # 主配置文件，包含域名白名单、重试策略与日志级别
├── requirements.txt                # Python 依赖声明，固定版本以保证环境一致性
├── src/                            # 核心源代码目录
│   ├── core/                       # 基础框架层
│   │   ├── fetcher.py              # 异步与同步请求封装，含重试与代理逻辑
│   │   ├── parser.py               # 通用解析基类，定义 extract 接口与异常类型
│   │   └── storage.py              # 存储抽象层，支持 SQLite 与 JSONL 两种后端
│   ├── plugins/                    # 解析插件目录，每个文件对应一种页面结构模板
│   │   ├── default_extractor.py    # 基于 XPath 的通用正文提取器
│   │   ├── meta_collector.py       # 专门提取 head 中 meta 标签的插件
│   │   └── link_normalizer.py      # 清理和补全页面中的相对链接
│   ├── utils/                      # 工具函数集
│   │   ├── url_validator.py        # URL 格式校验、域名黑白名单匹配
│   │   ├── encoding_detector.py    # 基于 chardet 的响应编码自动识别
│   │   └── logger.py               # 结构化日志配置，支持 JSON 格式输出
│   └── api/                        # RESTful API 子服务
│       ├── app.py                  # Flask 应用工厂，注册路由与错误处理器
│       └── schemas.py              # Pydantic 模型，用于请求参数与响应数据校验
├── tests/                          # 单元测试与集成测试目录
│   ├── test_fetcher.py             # 模拟 HTTP 响应的请求模块测试
│   ├── test_parser.py              # 使用本地样本页面的解析器功能测试
│   └── fixtures/                   # 测试用静态 HTML 样本文件
├── docs/                           # 文档源码，使用 MkDocs 构建
│   ├── user_guide.md               # 面向最终用户的操作手册
│   ├── developer_guide.md          # 面向贡献者的开发流程与规范
│   └── api_reference.md            # API 端点详细说明与示例
├── scripts/                        # 运维辅助脚本
│   ├── batch_import.py             # 从外部数据源批量导入 URL 列表
│   └── clean_archive.py            # 清理过期归档文件，释放存储空间
└── .github/                        # CI/CD 与社区模板
    └── workflows/                  # GitHub Actions 工作流定义
        ├── test.yml                # 每次 push 时自动运行测试套件
        └── publish.yml             # 打 tag 时自动构建 Docker 镜像并推送至 GHCR
```

## 贡献指南

1. 阅读开发者指南文档 /docs/developer_guide.md 了解代码风格要求（PEP 8 与 Google Python 风格指南）以及提交消息规范（Conventional Commits）。所有新增功能需附带对应的单元测试用例，测试覆盖率不低于 85%。

2. 在 GitHub Issues 中查找标记为 "help wanted" 或 "good first issue" 的任务，或自行创建新 Issue 描述待解决的问题或期望增加的功能。等待维护者确认后再开始编码，避免重复劳动。

3. Fork 本仓库到个人账号，创建以 feature/ 或 fix/ 为前缀的分支进行开发。开发过程中请保持与主分支的同步，定期执行 git rebase main 以减少合并冲突。

4. 完成代码与测试后，提交 Pull Request 至 main 分支。PR 描述中需引用相关 Issue 编号，并附上手动测试截图或日志片段。CI 流水线通过且至少一名维护者批准后方可合并。

## 常见问题

Q: 请求时出现 SSL 证书验证错误，但目标网站是 HTTP 协议，为何会触发 SSL 相关异常？

A: 该问题通常是因为系统环境变量中设置了 HTTPS_PROXY 代理，但代理服务器证书过期或不可信导致。解决方案是在 config.yaml 中将 verify_ssl 设为 false，或清除代理环境变量。注意该配置仅用于调试环境，生产环境建议正确配置代理证书链。

Q: 解析结果中正文内容包含大量 HTML 标签与转义字符，如何获得纯文本？

A: 默认解析器返回的是经过 lxml 清理后的 HTML 片段，如需纯文本可在调用 extract 方法时传入 text_only=True 参数。该参数会触发 beautifulsoup4 的 get_text() 方法，并自动合并多余空白字符。更精细的清洗规则可在 plugins/default_extractor.py 中自定义。

Q: 如何指定只处理 URL 列表中特定前缀的链接，而忽略其他链接？

A: 可在 config.yaml 的 url_filters 段下配置 include_patterns 列表，支持正则表达式。例如仅处理包含 "/xnews/" 路径的链接，可设置为 "- .*/xnews/.*" 。同时可使用 exclude_patterns 排除健康检查或其他内部路径。过滤器在链接导入阶段生效，不会对已归档链接产生二次影响。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:48
