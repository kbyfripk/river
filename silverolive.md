# NewsLink Navigator

NewsLink Navigator 是一个面向移动端新闻资讯聚合与深度链接管理的开源工具集，专门用于高效收集、清洗和归类来自垂直领域新闻源的海量链接数据。该项目为内容运营团队、舆情监测系统以及个人知识管理爱好者提供了一套标准化的外链处理流水线，能够将原始无序的新闻条目转化为结构化的可分析数据集。

项目定位为轻量级链接中间件，不依赖复杂的搜索引擎或人工智能模型，仅通过规则引擎和元数据提取策略，即可从指定新闻源（如本例中的 3g.gqskj.cn 移动站点）批量获取文章元信息，包括标题、发布时间、正文摘要和分类标签。目标用户包括数据采集工程师、开源情报分析人员以及需要定期跟踪特定新闻源的研究者。

## 功能概览

**批量链接抓取与去重**：支持从纯文本列表或 CSV 文件中导入大量新闻 URL，自动进行格式校验和重复链接过滤，确保后续处理的数据唯一性。

**智能元数据提取**：针对移动端新闻页面的常见 DOM 结构，内置多套解析模板，可自动提取文章标题、发布日期、正文预览和来源机构，减少人工干预。

**自定义分类规则引擎**：允许用户基于 URL 路径特征、关键词匹配或正则表达式为每一条新闻打上自定义标签，便于后续的专题追踪和趋势分析。

**数据导出与接口兼容**：支持将处理后的结构化数据导出为 JSON、CSV 或 Markdown 表格格式，同时提供 RESTful API 接口，方便对接 Grafana 仪表盘或企业微信机器人。

**增量更新与变更检测**：能够记录已处理链接的哈希值，在周期性抓取任务中仅对新出现的链接进行分析，大幅提升长周期运营效率。

**可配置的日志与监控**：内置分级日志系统，记录每次抓取任务的开始时间、成功数量、失败原因以及耗时，便于运维人员排查网络或解析异常。

**多源数据融合预览**：在终端界面或 Web 管理面板中，支持将不同批次的链接数据合并展示，并按照时间线或热度排序，辅助人工筛选高价值内容。

## 应用场景

舆情监测与热点追踪：企业公关部门或政府宣传机构可以使用本工具每日定时抓取指定新闻源的最新报道，通过分类标签快速定位涉及本行业或本地区的敏感信息，缩短舆情发现周期。

行业竞品情报收集：市场分析人员将竞品关键词或行业术语配置为分类规则，系统自动从海量新闻中筛选出相关文章，生成周报或月报数据，减少手动搜索和复制粘贴的时间成本。

个人阅读列表去重与归档：需要长期阅读特定来源的技术博客或深度报道的研究者，可以利用本工具生成一份不重复的阅读清单，并通过元数据提取的文章摘要快速判断内容相关性，避免遗漏重要信息。

数据仓库初始化构建：数据工程师在搭建新闻分析数据仓库时，可先使用本工具对历史链接进行批量回刷，生成带有时间戳和分类标签的基础数据表，为后续的自然语言处理或推荐算法提供干净的数据源。

## 快速开始

以下步骤将指导您在本地环境中快速部署并运行一次示例抓取任务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/example/newslink-navigator.git

# 进入项目根目录
cd newslink-navigator

# 安装核心依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 复制示例配置文件并修改数据库连接
cp config.example.yml config.yml

# 执行一次针对示例链接列表的抓取任务
python cli.py fetch --input sample_links.txt --output result.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求和响应，支持重试和超时控制 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 页面结构，用于元数据提取 |
| lxml | 4.9.0 及以上 | 作为 BeautifulSoup 的解析器后端，性能优于 html.parser |
| pyyaml | 6.0 及以上 | 读取和解析 YAML 格式的配置文件 |
| pandas | 1.5.0 及以上 | 处理导出的表格数据，提供数据透视和统计功能 |
| sqlite3 | 系统内置 | 用于本地缓存已处理的链接记录，避免重复抓取 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|----------|
| 用户手册 | docs/user_guide.md | 如何配置分类规则、如何调整抓取频率、如何导出报表 |
| 开发者指南 | docs/developer_guide.md | 如何添加新的解析模板、如何扩展自定义导出插件 |
| API 参考 | docs/api_reference.md | 每个模块和函数的参数说明、返回值定义及异常类型 |
| 运维手册 | docs/ops_manual.md | 如何部署为定时任务、如何配置日志轮转、如何备份缓存数据库 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/2140285.htm
- http://m.3g.gqskj.cn/xnews/2944.htm
- http://m.3g.gqskj.cn/xnews/695590.htm
- http://m.3g.gqskj.cn/xnews/0627457.htm
- http://m.3g.gqskj.cn/xnews/58574.htm
- http://m.3g.gqskj.cn/xnews/860560.htm
- http://m.3g.gqskj.cn/xnews/6368.htm
- http://m.3g.gqskj.cn/xnews/82769.htm
- http://m.3g.gqskj.cn/xnews/175736.htm
- http://m.3g.gqskj.cn/xnews/625623.htm
- http://m.3g.gqskj.cn/xnews/866869.htm
- http://m.3g.gqskj.cn/xnews/6911532.htm
- http://m.3g.gqskj.cn/xnews/140094.htm
- http://m.3g.gqskj.cn/xnews/7449.htm
- http://m.3g.gqskj.cn/xnews/79279.htm
- http://m.3g.gqskj.cn/xnews/495429.htm
- http://m.3g.gqskj.cn/xnews/4193.htm
- http://m.3g.gqskj.cn/xnews/6671389.htm
- http://m.3g.gqskj.cn/xnews/6681309.htm
- http://m.3g.gqskj.cn/xnews/26604.htm
- http://m.3g.gqskj.cn/xnews/76352.htm
- http://m.3g.gqskj.cn/xnews/28797.htm
- http://m.3g.gqskj.cn/xnews/1194975.htm
- http://m.3g.gqskj.cn/xnews/1700.htm
- http://m.3g.gqskj.cn/xnews/4932718.htm
- http://m.3g.gqskj.cn/xnews/00964.htm
- http://m.3g.gqskj.cn/xnews/0418851.htm
- http://m.3g.gqskj.cn/xnews/5574043.htm
- http://m.3g.gqskj.cn/xnews/3161513.htm
- http://m.3g.gqskj.cn/xnews/2815.htm
- http://m.3g.gqskj.cn/xnews/8340.htm
- http://m.3g.gqskj.cn/xnews/600191.htm
- http://m.3g.gqskj.cn/xnews/9275994.htm
- http://m.3g.gqskj.cn/xnews/23791.htm
- http://m.3g.gqskj.cn/xnews/50859.htm
- http://m.3g.gqskj.cn/xnews/625726.htm
- http://m.3g.gqskj.cn/xnews/051569.htm
- http://m.3g.gqskj.cn/xnews/458992.htm
- http://m.3g.gqskj.cn/xnews/4018908.htm
- http://m.3g.gqskj.cn/xnews/7478.htm
- http://m.3g.gqskj.cn/xnews/1211850.htm
- http://m.3g.gqskj.cn/xnews/2318416.htm
- http://m.3g.gqskj.cn/xnews/3166879.htm
- http://m.3g.gqskj.cn/xnews/8275912.htm
- http://m.3g.gqskj.cn/xnews/1197.htm
- http://m.3g.gqskj.cn/xnews/9930264.htm
- http://m.3g.gqskj.cn/xnews/7525295.htm
- http://m.3g.gqskj.cn/xnews/079623.htm
- http://m.3g.gqskj.cn/xnews/3630824.htm
- http://m.3g.gqskj.cn/xnews/1057122.htm
- http://m.3g.gqskj.cn/xnews/7812316.htm
- http://m.3g.gqskj.cn/xnews/1466.htm
- http://m.3g.gqskj.cn/xnews/3588916.htm
- http://m.3g.gqskj.cn/xnews/112396.htm
- http://m.3g.gqskj.cn/xnews/4990882.htm
- http://m.3g.gqskj.cn/xnews/028669.htm
- http://m.3g.gqskj.cn/xnews/3421739.htm
- http://m.3g.gqskj.cn/xnews/8345273.htm
- http://m.3g.gqskj.cn/xnews/08000.htm
- http://m.3g.gqskj.cn/xnews/657198.htm
- http://m.3g.gqskj.cn/xnews/7167284.htm
- http://m.3g.gqskj.cn/xnews/7979952.htm
- http://m.3g.gqskj.cn/xnews/075956.htm
- http://m.3g.gqskj.cn/xnews/06084.htm
- http://m.3g.gqskj.cn/xnews/4380335.htm
- http://m.3g.gqskj.cn/xnews/1341.htm
- http://m.3g.gqskj.cn/xnews/4820.htm
- http://m.3g.gqskj.cn/xnews/430868.htm
- http://m.3g.gqskj.cn/xnews/33477.htm
- http://m.3g.gqskj.cn/xnews/94183.htm
- http://m.3g.gqskj.cn/xnews/2026462.htm
- http://m.3g.gqskj.cn/xnews/0687.htm
- http://m.3g.gqskj.cn/xnews/82299.htm
- http://m.3g.gqskj.cn/xnews/477866.htm
- http://m.3g.gqskj.cn/xnews/52739.htm
- http://m.3g.gqskj.cn/xnews/9621044.htm
- http://m.3g.gqskj.cn/xnews/2535.htm
- http://m.3g.gqskj.cn/xnews/95023.htm
- http://m.3g.gqskj.cn/xnews/6621301.htm
- http://m.3g.gqskj.cn/xnews/72981.htm
- http://m.3g.gqskj.cn/xnews/1109.htm
- http://m.3g.gqskj.cn/xnews/89190.htm
- http://m.3g.gqskj.cn/xnews/8913509.htm
- http://m.3g.gqskj.cn/xnews/3557265.htm
- http://m.3g.gqskj.cn/xnews/5464600.htm
- http://m.3g.gqskj.cn/xnews/0100109.htm
- http://m.3g.gqskj.cn/xnews/191273.htm
- http://m.3g.gqskj.cn/xnews/3644.htm
- http://m.3g.gqskj.cn/xnews/851351.htm
- http://m.3g.gqskj.cn/xnews/4952.htm
- http://m.3g.gqskj.cn/xnews/3724335.htm
- http://m.3g.gqskj.cn/xnews/16216.htm
- http://m.3g.gqskj.cn/xnews/9673908.htm
- http://m.3g.gqskj.cn/xnews/5306.htm
- http://m.3g.gqskj.cn/xnews/74412.htm
- http://m.3g.gqskj.cn/xnews/2438140.htm
- http://m.3g.gqskj.cn/xnews/571199.htm
- http://m.3g.gqskj.cn/xnews/2782362.htm
- http://m.3g.gqskj.cn/xnews/4790.htm
- http://m.3g.gqskj.cn/xnews/330898.htm
- http://m.3g.gqskj.cn/xnews/9520.htm
- http://m.3g.gqskj.cn/xnews/527117.htm
- http://m.3g.gqskj.cn/xnews/0663.htm
- http://m.3g.gqskj.cn/xnews/078154.htm
- http://m.3g.gqskj.cn/xnews/2760664.htm
- http://m.3g.gqskj.cn/xnews/836567.htm
- http://m.3g.gqskj.cn/xnews/35528.htm
- http://m.3g.gqskj.cn/xnews/578272.htm
- http://m.3g.gqskj.cn/xnews/9048.htm
- http://m.3g.gqskj.cn/xnews/450992.htm
- http://m.3g.gqskj.cn/xnews/49369.htm
- http://m.3g.gqskj.cn/xnews/395308.htm
- http://m.3g.gqskj.cn/xnews/1892101.htm
- http://m.3g.gqskj.cn/xnews/5227078.htm
- http://m.3g.gqskj.cn/xnews/61972.htm
- http://m.3g.gqskj.cn/xnews/9876.htm
- http://m.3g.gqskj.cn/xnews/62854.htm
- http://m.3g.gqskj.cn/xnews/975030.htm
- http://m.3g.gqskj.cn/xnews/488536.htm
- http://m.3g.gqskj.cn/xnews/339455.htm
- http://m.3g.gqskj.cn/xnews/320981.htm
- http://m.3g.gqskj.cn/xnews/9460.htm
- http://m.3g.gqskj.cn/xnews/8730777.htm
- http://m.3g.gqskj.cn/xnews/58963.htm
- http://m.3g.gqskj.cn/xnews/3991133.htm
- http://m.3g.gqskj.cn/xnews/907130.htm
- http://m.3g.gqskj.cn/xnews/01638.htm
- http://m.3g.gqskj.cn/xnews/84616.htm
- http://m.3g.gqskj.cn/xnews/2527.htm
- http://m.3g.gqskj.cn/xnews/51110.htm
- http://m.3g.gqskj.cn/xnews/3585.htm
- http://m.3g.gqskj.cn/xnews/4122.htm
- http://m.3g.gqskj.cn/xnews/0003175.htm
- http://m.3g.gqskj.cn/xnews/295045.htm
- http://m.3g.gqskj.cn/xnews/1174908.htm
- http://m.3g.gqskj.cn/xnews/08099.htm
- http://m.3g.gqskj.cn/xnews/6253941.htm
- http://m.3g.gqskj.cn/xnews/201577.htm
- http://m.3g.gqskj.cn/xnews/198059.htm
- http://m.3g.gqskj.cn/xnews/5169574.htm
- http://m.3g.gqskj.cn/xnews/9052.htm
- http://m.3g.gqskj.cn/xnews/73387.htm
- http://m.3g.gqskj.cn/xnews/06498.htm
- http://m.3g.gqskj.cn/xnews/8028.htm
- http://m.3g.gqskj.cn/xnews/1944716.htm
- http://m.3g.gqskj.cn/xnews/40954.htm
- http://m.3g.gqskj.cn/xnews/57710.htm
- http://m.3g.gqskj.cn/xnews/572923.htm
- http://m.3g.gqskj.cn/xnews/1471868.htm
- http://m.3g.gqskj.cn/xnews/3610.htm
- http://m.3g.gqskj.cn/xnews/668889.htm
- http://m.3g.gqskj.cn/xnews/357557.htm
- http://m.3g.gqskj.cn/xnews/5396.htm
- http://m.3g.gqskj.cn/xnews/75289.htm
- http://m.3g.gqskj.cn/xnews/764656.htm
- http://m.3g.gqskj.cn/xnews/6783224.htm
- http://m.3g.gqskj.cn/xnews/22170.htm
- http://m.3g.gqskj.cn/xnews/4916335.htm
- http://m.3g.gqskj.cn/xnews/8802171.htm
- http://m.3g.gqskj.cn/xnews/5433.htm
- http://m.3g.gqskj.cn/xnews/302590.htm
- http://m.3g.gqskj.cn/xnews/110947.htm
- http://m.3g.gqskj.cn/xnews/779539.htm
- http://m.3g.gqskj.cn/xnews/40988.htm
- http://m.3g.gqskj.cn/xnews/23524.htm
- http://m.3g.gqskj.cn/xnews/165465.htm
- http://m.3g.gqskj.cn/xnews/631337.htm
- http://m.3g.gqskj.cn/xnews/1108413.htm
- http://m.3g.gqskj.cn/xnews/27836.htm
- http://m.3g.gqskj.cn/xnews/77386.htm
- http://m.3g.gqskj.cn/xnews/8409970.htm
- http://m.3g.gqskj.cn/xnews/02516.htm
- http://m.3g.gqskj.cn/xnews/26139.htm
- http://m.3g.gqskj.cn/xnews/75324.htm
- http://m.3g.gqskj.cn/xnews/1859863.htm
- http://m.3g.gqskj.cn/xnews/9879.htm
- http://m.3g.gqskj.cn/xnews/2491549.htm
- http://m.3g.gqskj.cn/xnews/9684032.htm
- http://m.3g.gqskj.cn/xnews/7770.htm
- http://m.3g.gqskj.cn/xnews/3051870.htm
- http://m.3g.gqskj.cn/xnews/8909.htm
- http://m.3g.gqskj.cn/xnews/1642032.htm
- http://m.3g.gqskj.cn/xnews/98747.htm
- http://m.3g.gqskj.cn/xnews/15155.htm
- http://m.3g.gqskj.cn/xnews/412734.htm
- http://m.3g.gqskj.cn/xnews/472156.htm
- http://m.3g.gqskj.cn/xnews/96508.htm
- http://m.3g.gqskj.cn/xnews/4833017.htm
- http://m.3g.gqskj.cn/xnews/05520.htm
- http://m.3g.gqskj.cn/xnews/982496.htm
- http://m.3g.gqskj.cn/xnews/770173.htm
- http://m.3g.gqskj.cn/xnews/5131.htm
- http://m.3g.gqskj.cn/xnews/533569.htm
- http://m.3g.gqskj.cn/xnews/062776.htm
- http://m.3g.gqskj.cn/xnews/9790579.htm
- http://m.3g.gqskj.cn/xnews/31590.htm
- http://m.3g.gqskj.cn/xnews/7549.htm
- http://m.3g.gqskj.cn/xnews/93463.htm
- http://m.3g.gqskj.cn/xnews/0691.htm
- http://m.3g.gqskj.cn/xnews/2334.htm
- http://m.3g.gqskj.cn/xnews/3455.htm
- http://m.3g.gqskj.cn/xnews/3699106.htm
- http://m.3g.gqskj.cn/xnews/303402.htm
- http://m.3g.gqskj.cn/xnews/81497.htm
- http://m.3g.gqskj.cn/xnews/447264.htm
- http://m.3g.gqskj.cn/xnews/77540.htm
- http://m.3g.gqskj.cn/xnews/839215.htm
- http://m.3g.gqskj.cn/xnews/5079.htm
- http://m.3g.gqskj.cn/xnews/947902.htm
- http://m.3g.gqskj.cn/xnews/6169276.htm
- http://m.3g.gqskj.cn/xnews/568345.htm
- http://m.3g.gqskj.cn/xnews/5852661.htm
- http://m.3g.gqskj.cn/xnews/8748.htm
- http://m.3g.gqskj.cn/xnews/97640.htm
- http://m.3g.gqskj.cn/xnews/082919.htm
- http://m.3g.gqskj.cn/xnews/5426823.htm
- http://m.3g.gqskj.cn/xnews/982910.htm
- http://m.3g.gqskj.cn/xnews/5204672.htm
- http://m.3g.gqskj.cn/xnews/18621.htm
- http://m.3g.gqskj.cn/xnews/116168.htm
- http://m.3g.gqskj.cn/xnews/407103.htm
- http://m.3g.gqskj.cn/xnews/73236.htm
- http://m.3g.gqskj.cn/xnews/2055.htm
- http://m.3g.gqskj.cn/xnews/2135.htm
- http://m.3g.gqskj.cn/xnews/5610.htm
- http://m.3g.gqskj.cn/xnews/2798877.htm
- http://m.3g.gqskj.cn/xnews/6621409.htm
- http://m.3g.gqskj.cn/xnews/73451.htm
- http://m.3g.gqskj.cn/xnews/03104.htm
- http://m.3g.gqskj.cn/xnews/58290.htm
- http://m.3g.gqskj.cn/xnews/35216.htm
- http://m.3g.gqskj.cn/xnews/1708.htm
- http://m.3g.gqskj.cn/xnews/7162393.htm
- http://m.3g.gqskj.cn/xnews/9657.htm
- http://m.3g.gqskj.cn/xnews/1575424.htm
- http://m.3g.gqskj.cn/xnews/9903.htm
- http://m.3g.gqskj.cn/xnews/46082.htm
- http://m.3g.gqskj.cn/xnews/0904.htm
- http://m.3g.gqskj.cn/xnews/3074024.htm
- http://m.3g.gqskj.cn/xnews/19209.htm
- http://m.3g.gqskj.cn/xnews/36996.htm
- http://m.3g.gqskj.cn/xnews/2468840.htm
- http://m.3g.gqskj.cn/xnews/760128.htm
- http://m.3g.gqskj.cn/xnews/9485.htm
- http://m.3g.gqskj.cn/xnews/47501.htm
- http://m.3g.gqskj.cn/xnews/75041.htm
- http://m.3g.gqskj.cn/xnews/1189.htm
- http://m.3g.gqskj.cn/xnews/15013.htm
- http://m.3g.gqskj.cn/xnews/6207783.htm
- http://m.3g.gqskj.cn/xnews/992353.htm

## 项目结构

```
newslink-navigator/
├── cli.py                      # 命令行入口，整合抓取、导出和监控子命令
├── config.example.yml          # 示例配置文件，包含超时、重试和日志级别
├── requirements.txt            # Python 依赖清单，锁定主要库的版本范围
├── src/                        # 核心源码目录
│   ├── fetcher/                # 网络请求与原始 HTML 获取模块
│   │   ├── client.py           # 封装 requests 会话，处理重试和代理
│   │   └── middleware.py       # 请求头轮转与延迟控制中间件
│   ├── parser/                 # 页面解析与元数据提取模块
│   │   ├── base.py             # 定义解析器抽象基类
│   │   ├── mobile_news.py      # 针对移动端新闻站点的具体解析实现
│   │   └── registry.py         # 解析器注册与动态选择工厂
│   ├── rules/                  # 分类规则引擎模块
│   │   ├── loader.py           # 从 YAML 加载关键词与正则规则
│   │   ├── matcher.py          # 执行多模式匹配与标签生成
│   │   └── builtin.yml         # 内置默认分类规则集
│   ├── storage/                # 数据持久化与缓存模块
│   │   ├── cache.py            # SQLite 缓存读写与哈希去重
│   │   ├── exporter.py         # 导出为 JSON、CSV 或 Markdown
│   │   └── models.py           # 定义文章数据的数据类结构
│   └── utils/                  # 公共工具函数模块
│       ├── logger.py           # 分级日志配置与格式化
│       ├── validator.py        # URL 格式校验与路径规范化
│       └── timer.py            # 任务耗时统计与性能打点
├── tests/                      # 单元测试与集成测试目录
│   ├── test_fetcher.py         # 模拟网络请求的测试用例
│   ├── test_parser.py          # 针对不同页面结构的解析测试
│   └── fixtures/               # 测试用的静态 HTML 样本文件
├── docs/                       # 完整文档目录
│   ├── user_guide.md           # 用户手册，包含配置详解
│   ├── developer_guide.md      # 开发者指南，包含插件编写教程
│   └── api_reference.md        # 自动生成的 API 文档
└── scripts/                    # 辅助运维脚本
    ├── daily_cron.sh           # 每日定时抓取任务的 shell 包装脚本
    └── migrate_db.py           # 数据库版本升级与迁移工具
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境中。确保您的 Python 版本满足安装要求，并创建独立的虚拟环境。
2. 在 `src/parser` 目录下新增或修改解析类，如果涉及新的新闻源模板，请在 `src/rules/builtin.yml` 中添加对应的测试规则和示例 URL。
3. 编写相应的单元测试用例，覆盖正常解析和异常处理分支。测试用例需放置在 `tests/` 对应模块下，并确保全部测试通过后方可提交。
4. 提交代码前，运行代码风格检查工具（如 black 和 flake8），并更新 `docs/` 目录下相关文档的变动说明，尤其是 `user_guide.md` 中关于配置项的部分。
5. 发起 Pull Request 并填写清晰的变更描述，包含本次改动解决的问题、新增的功能以及对向后兼容性的影响评估。项目维护者会在 48 小时内进行审查。

## 常见问题

问：抓取过程中遇到 HTTP 403 或 429 状态码，如何解决？
答：此类状态码通常表示目标服务器拒绝访问或触发了频率限制。建议在 `config.yml` 中调整 `request_interval` 参数（单位秒）以增加请求间隔，并检查 `user_agent` 池是否包含主流移动端浏览器标识。若问题持续，可启用代理轮转功能，通过配置 `proxy_list` 使用多个出口 IP。

问：部分链接的元数据提取不完整，标题或发布时间为空，如何排查？
答：这通常是因为目标页面的 DOM 结构与内置解析模板不匹配。可以启用调试模式（`--debug` 参数）查看原始 HTML 输出，然后使用浏览器开发者工具定位实际标题和时间的 CSS 选择器。确认后，在 `src/parser/mobile_news.py` 中新增或修改对应的 `selector` 映射，并提交更新。

问：如何清理缓存并重新处理所有链接？
答：执行 `python cli.py cache --clear` 可清空 SQLite 缓存表，重置所有链接的处理状态。之后再次运行 `fetch` 命令即可对所有链接重新进行抓取和提取。请注意，该操作会删除所有历史记录，且大量链接可能需要较长时间，建议在网络条件较好的时段进行。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
