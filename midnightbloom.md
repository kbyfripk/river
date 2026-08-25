# XNews Resource Aggregator

XNews Resource Aggregator 是一个面向技术资讯聚合与内容索引的开源工具，专为需要从特定新闻源批量采集、归档和检索结构化数据的开发者与研究人员设计。该项目提供一套轻量级的 URL 资源管理框架，能够将大量散落的新闻链接纳入统一索引体系，支持标签分类、元数据提取与状态监控，适用于内容农场、舆情分析、历史存档等场景。

项目核心定位是解决信息碎片化问题，通过规范化链接格式、自动化校验可用性以及分类存储，帮助用户从海量异构的新闻页面中快速定位关键内容。目标用户包括数据采集工程师、新闻聚合平台运营者、学术研究机构以及个人知识管理爱好者。XNews 不依赖特定 CMS 或数据库，采用纯文件系统与内存索引，启动即可用，适合部署在低资源服务器或本地开发环境。

## 功能概览

批量链接导入与去重 支持从文本文件、CSV 或标准输入流批量加载 URL，自动识别重复条目并生成去重报告。

存活状态定时检测 内置异步 HTTP 客户端，周期性探测每个链接的可达性，记录响应状态码与耗时，标记异常链接。

多维标签分类体系 允许用户为每个资源链接添加多个自定义标签，支持按标签组合筛选和导出子集。

全文元数据提取 对于可访问的 HTML 页面，自动提取标题、摘要、发布时间、正文关键词等元数据，生成结构化摘要。

索引快照与恢复 定期将内存索引持久化为 JSON 快照文件，服务重启时可快速恢复全量资源状态，避免重复采集。

命令行交互与 API 服务 提供 CLI 工具用于日常管理操作，同时内置 RESTful API 支持第三方系统集成，便于嵌入自动化流水线。

资源黑名单与白名单 支持配置域名或路径正则规则，对特定来源进行过滤或优先处理，灵活适配不同采集策略。

## 应用场景

舆情监控与新闻追踪 媒体监测机构可使用 XNews 每日定时抓取指定新闻源的链接列表，自动检测新增内容并提取摘要，生成舆情简报供分析师审阅。

历史数据归档与回溯 研究人员需要长期保存特定新闻站点的文章索引，XNews 可定期对链接进行快照备份，即使原始页面被删除，仍保留元数据与标题信息，便于学术引用。

内容聚合站前置过滤 个人博客或小型新闻聚合站运营者可使用 XNews 作为数据清洗前置工具，从大量原始链接中过滤无效或重复条目，再将高质量资源导入最终展示系统。

开发测试数据填充 开发人员在构建搜索或推荐系统原型时，可利用 XNews 快速生成包含数百条真实链接的测试数据集，模拟生产环境下的资源分布与访问模式。

## 快速开始

以下命令演示了从克隆仓库到启动服务的完整流程。

```bash
git clone https://github.com/xnews-project/xnews-aggregator.git
cd xnews-aggregator
pip install -r requirements.txt
python cli.py import --source ./samples/links.txt
python cli.py scan --concurrency 10 --timeout 5
python cli.py serve --port 8080
```

导入示例链接文件后，扫描命令将对所有链接执行存活检测，服务启动后可通过本地 8080 端口访问 API 文档与仪表盘。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 以获得性能提升 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发链接检测与页面抓取 |
| lxml | 4.9.0 及以上 | HTML 解析引擎，用于元数据提取与内容清洗 |
| rich | 13.7.0 及以上 | 终端美化输出，提供进度条与彩色日志 |
| click | 8.1.0 及以上 | 命令行交互框架，用于解析子命令与参数 |
| pytest | 8.0.0 及以上 | 单元测试框架（仅开发环境需要） |

系统要求：Linux / macOS / Windows WSL2，内存不低于 512MB，磁盘空间建议 1GB 以上用于存储索引快照与日志。网络环境需能够访问目标新闻域名，若使用代理请配置 HTTP_PROXY 环境变量。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速安装、配置并运行第一次扫描任务？ |
| 命令行手册 | docs/cli-reference.md | 所有子命令、参数选项和示例用法有哪些？ |
| API 参考 | docs/api-reference.md | RESTful 接口的端点定义、请求格式与返回结构是什么？ |
| 最佳实践 | docs/best-practices.md | 如何优化并发数、处理反爬策略以及维护长期索引？ |

完整文档位于项目根目录下的 docs 文件夹，亦可在线浏览 GitHub Pages 版本。

## 资源列表

- http://m.3g.gqskj.cn/xnews/064839.htm
- http://m.3g.gqskj.cn/xnews/616545.htm
- http://m.3g.gqskj.cn/xnews/050363.htm
- http://m.3g.gqskj.cn/xnews/8853458.htm
- http://m.3g.gqskj.cn/xnews/6541482.htm
- http://m.3g.gqskj.cn/xnews/841155.htm
- http://m.3g.gqskj.cn/xnews/205853.htm
- http://m.3g.gqskj.cn/xnews/8546.htm
- http://m.3g.gqskj.cn/xnews/251200.htm
- http://m.3g.gqskj.cn/xnews/4762.htm
- http://m.3g.gqskj.cn/xnews/8522.htm
- http://m.3g.gqskj.cn/xnews/2455774.htm
- http://m.3g.gqskj.cn/xnews/848111.htm
- http://m.3g.gqskj.cn/xnews/68147.htm
- http://m.3g.gqskj.cn/xnews/3486.htm
- http://m.3g.gqskj.cn/xnews/847579.htm
- http://m.3g.gqskj.cn/xnews/6606.htm
- http://m.3g.gqskj.cn/xnews/508881.htm
- http://m.3g.gqskj.cn/xnews/0486.htm
- http://m.3g.gqskj.cn/xnews/98568.htm
- http://m.3g.gqskj.cn/xnews/3395.htm
- http://m.3g.gqskj.cn/xnews/88738.htm
- http://m.3g.gqskj.cn/xnews/65416.htm
- http://m.3g.gqskj.cn/xnews/89414.htm
- http://m.3g.gqskj.cn/xnews/861679.htm
- http://m.3g.gqskj.cn/xnews/80647.htm
- http://m.3g.gqskj.cn/xnews/8315.htm
- http://m.3g.gqskj.cn/xnews/17803.htm
- http://m.3g.gqskj.cn/xnews/7845549.htm
- http://m.3g.gqskj.cn/xnews/58179.htm
- http://m.3g.gqskj.cn/xnews/0585356.htm
- http://m.3g.gqskj.cn/xnews/88050.htm
- http://m.3g.gqskj.cn/xnews/973620.htm
- http://m.3g.gqskj.cn/xnews/52735.htm
- http://m.3g.gqskj.cn/xnews/2459166.htm
- http://m.3g.gqskj.cn/xnews/01568.htm
- http://m.3g.gqskj.cn/xnews/3771908.htm
- http://m.3g.gqskj.cn/xnews/7637.htm
- http://m.3g.gqskj.cn/xnews/252597.htm
- http://m.3g.gqskj.cn/xnews/70234.htm
- http://m.3g.gqskj.cn/xnews/90050.htm
- http://m.3g.gqskj.cn/xnews/6951.htm
- http://m.3g.gqskj.cn/xnews/3015242.htm
- http://m.3g.gqskj.cn/xnews/312060.htm
- http://m.3g.gqskj.cn/xnews/552541.htm
- http://m.3g.gqskj.cn/xnews/3827324.htm
- http://m.3g.gqskj.cn/xnews/678900.htm
- http://m.3g.gqskj.cn/xnews/195507.htm
- http://m.3g.gqskj.cn/xnews/3137641.htm
- http://m.3g.gqskj.cn/xnews/60497.htm
- http://m.3g.gqskj.cn/xnews/9829147.htm
- http://m.3g.gqskj.cn/xnews/0646.htm
- http://m.3g.gqskj.cn/xnews/4016835.htm
- http://m.3g.gqskj.cn/xnews/9160.htm
- http://m.3g.gqskj.cn/xnews/2471992.htm
- http://m.3g.gqskj.cn/xnews/112006.htm
- http://m.3g.gqskj.cn/xnews/950886.htm
- http://m.3g.gqskj.cn/xnews/1626189.htm
- http://m.3g.gqskj.cn/xnews/3402.htm
- http://m.3g.gqskj.cn/xnews/63235.htm
- http://m.3g.gqskj.cn/xnews/8653318.htm
- http://m.3g.gqskj.cn/xnews/1041398.htm
- http://m.3g.gqskj.cn/xnews/8934.htm
- http://m.3g.gqskj.cn/xnews/78707.htm
- http://m.3g.gqskj.cn/xnews/6858.htm
- http://m.3g.gqskj.cn/xnews/7019947.htm
- http://m.3g.gqskj.cn/xnews/717671.htm
- http://m.3g.gqskj.cn/xnews/14052.htm
- http://m.3g.gqskj.cn/xnews/78208.htm
- http://m.3g.gqskj.cn/xnews/1216770.htm
- http://m.3g.gqskj.cn/xnews/4056108.htm
- http://m.3g.gqskj.cn/xnews/31381.htm
- http://m.3g.gqskj.cn/xnews/9515536.htm
- http://m.3g.gqskj.cn/xnews/9372.htm
- http://m.3g.gqskj.cn/xnews/57374.htm
- http://m.3g.gqskj.cn/xnews/9137.htm
- http://m.3g.gqskj.cn/xnews/57672.htm
- http://m.3g.gqskj.cn/xnews/343310.htm
- http://m.3g.gqskj.cn/xnews/4460558.htm
- http://m.3g.gqskj.cn/xnews/6486037.htm
- http://m.3g.gqskj.cn/xnews/922868.htm
- http://m.3g.gqskj.cn/xnews/857498.htm
- http://m.3g.gqskj.cn/xnews/11058.htm
- http://m.3g.gqskj.cn/xnews/29997.htm
- http://m.3g.gqskj.cn/xnews/79605.htm
- http://m.3g.gqskj.cn/xnews/541170.htm
- http://m.3g.gqskj.cn/xnews/0485347.htm
- http://m.3g.gqskj.cn/xnews/6392.htm
- http://m.3g.gqskj.cn/xnews/8850.htm
- http://m.3g.gqskj.cn/xnews/7596.htm
- http://m.3g.gqskj.cn/xnews/3476.htm
- http://m.3g.gqskj.cn/xnews/41802.htm
- http://m.3g.gqskj.cn/xnews/7206774.htm
- http://m.3g.gqskj.cn/xnews/8119400.htm
- http://m.3g.gqskj.cn/xnews/39579.htm
- http://m.3g.gqskj.cn/xnews/4264.htm
- http://m.3g.gqskj.cn/xnews/8501481.htm
- http://m.3g.gqskj.cn/xnews/55166.htm
- http://m.3g.gqskj.cn/xnews/58868.htm
- http://m.3g.gqskj.cn/xnews/270176.htm
- http://m.3g.gqskj.cn/xnews/440874.htm
- http://m.3g.gqskj.cn/xnews/8835532.htm
- http://m.3g.gqskj.cn/xnews/47723.htm
- http://m.3g.gqskj.cn/xnews/4124.htm
- http://m.3g.gqskj.cn/xnews/1352223.htm
- http://m.3g.gqskj.cn/xnews/6660.htm
- http://m.3g.gqskj.cn/xnews/027445.htm
- http://m.3g.gqskj.cn/xnews/145661.htm
- http://m.3g.gqskj.cn/xnews/6078673.htm
- http://m.3g.gqskj.cn/xnews/0480.htm
- http://m.3g.gqskj.cn/xnews/07481.htm
- http://m.3g.gqskj.cn/xnews/0380.htm
- http://m.3g.gqskj.cn/xnews/4038352.htm
- http://m.3g.gqskj.cn/xnews/247857.htm
- http://m.3g.gqskj.cn/xnews/34412.htm
- http://m.3g.gqskj.cn/xnews/682814.htm
- http://m.3g.gqskj.cn/xnews/57164.htm
- http://m.3g.gqskj.cn/xnews/54742.htm
- http://m.3g.gqskj.cn/xnews/19925.htm
- http://m.3g.gqskj.cn/xnews/8672277.htm
- http://m.3g.gqskj.cn/xnews/25285.htm
- http://m.3g.gqskj.cn/xnews/0328514.htm
- http://m.3g.gqskj.cn/xnews/9978982.htm
- http://m.3g.gqskj.cn/xnews/2458361.htm
- http://m.3g.gqskj.cn/xnews/432945.htm
- http://m.3g.gqskj.cn/xnews/767064.htm
- http://m.3g.gqskj.cn/xnews/00053.htm
- http://m.3g.gqskj.cn/xnews/59776.htm
- http://m.3g.gqskj.cn/xnews/76580.htm
- http://m.3g.gqskj.cn/xnews/4675.htm
- http://m.3g.gqskj.cn/xnews/75085.htm
- http://m.3g.gqskj.cn/xnews/9770.htm
- http://m.3g.gqskj.cn/xnews/283433.htm
- http://m.3g.gqskj.cn/xnews/24243.htm
- http://m.3g.gqskj.cn/xnews/742996.htm
- http://m.3g.gqskj.cn/xnews/84295.htm
- http://m.3g.gqskj.cn/xnews/1913.htm
- http://m.3g.gqskj.cn/xnews/4986719.htm
- http://m.3g.gqskj.cn/xnews/1366209.htm
- http://m.3g.gqskj.cn/xnews/9662.htm
- http://m.3g.gqskj.cn/xnews/7938.htm
- http://m.3g.gqskj.cn/xnews/6675.htm
- http://m.3g.gqskj.cn/xnews/2427.htm
- http://m.3g.gqskj.cn/xnews/5834163.htm
- http://m.3g.gqskj.cn/xnews/6918.htm
- http://m.3g.gqskj.cn/xnews/1354715.htm
- http://m.3g.gqskj.cn/xnews/79351.htm
- http://m.3g.gqskj.cn/xnews/2047.htm
- http://m.3g.gqskj.cn/xnews/1293.htm
- http://m.3g.gqskj.cn/xnews/873967.htm
- http://m.3g.gqskj.cn/xnews/7065.htm
- http://m.3g.gqskj.cn/xnews/25306.htm
- http://m.3g.gqskj.cn/xnews/77046.htm
- http://m.3g.gqskj.cn/xnews/17074.htm
- http://m.3g.gqskj.cn/xnews/1784217.htm
- http://m.3g.gqskj.cn/xnews/6872253.htm
- http://m.3g.gqskj.cn/xnews/96531.htm
- http://m.3g.gqskj.cn/xnews/7511837.htm
- http://m.3g.gqskj.cn/xnews/0398367.htm
- http://m.3g.gqskj.cn/xnews/48653.htm
- http://m.3g.gqskj.cn/xnews/0978.htm
- http://m.3g.gqskj.cn/xnews/51747.htm
- http://m.3g.gqskj.cn/xnews/32435.htm
- http://m.3g.gqskj.cn/xnews/142559.htm
- http://m.3g.gqskj.cn/xnews/691906.htm
- http://m.3g.gqskj.cn/xnews/449969.htm
- http://m.3g.gqskj.cn/xnews/5054306.htm
- http://m.3g.gqskj.cn/xnews/1935031.htm
- http://m.3g.gqskj.cn/xnews/069833.htm
- http://m.3g.gqskj.cn/xnews/968788.htm
- http://m.3g.gqskj.cn/xnews/3778.htm
- http://m.3g.gqskj.cn/xnews/54063.htm
- http://m.3g.gqskj.cn/xnews/6363630.htm
- http://m.3g.gqskj.cn/xnews/992818.htm
- http://m.3g.gqskj.cn/xnews/98784.htm
- http://m.3g.gqskj.cn/xnews/428940.htm
- http://m.3g.gqskj.cn/xnews/425131.htm
- http://m.3g.gqskj.cn/xnews/3708528.htm
- http://m.3g.gqskj.cn/xnews/78911.htm
- http://m.3g.gqskj.cn/xnews/005060.htm
- http://m.3g.gqskj.cn/xnews/2456717.htm
- http://m.3g.gqskj.cn/xnews/778753.htm
- http://m.3g.gqskj.cn/xnews/3918985.htm
- http://m.3g.gqskj.cn/xnews/1026913.htm
- http://m.3g.gqskj.cn/xnews/59167.htm
- http://m.3g.gqskj.cn/xnews/818355.htm
- http://m.3g.gqskj.cn/xnews/0241.htm
- http://m.3g.gqskj.cn/xnews/31559.htm
- http://m.3g.gqskj.cn/xnews/7745.htm
- http://m.3g.gqskj.cn/xnews/32691.htm
- http://m.3g.gqskj.cn/xnews/64136.htm
- http://m.3g.gqskj.cn/xnews/654018.htm
- http://m.3g.gqskj.cn/xnews/87712.htm
- http://m.3g.gqskj.cn/xnews/6538.htm
- http://m.3g.gqskj.cn/xnews/146552.htm
- http://m.3g.gqskj.cn/xnews/8405528.htm
- http://m.3g.gqskj.cn/xnews/8325.htm
- http://m.3g.gqskj.cn/xnews/7658.htm
- http://m.3g.gqskj.cn/xnews/4233.htm
- http://m.3g.gqskj.cn/xnews/8573978.htm
- http://m.3g.gqskj.cn/xnews/938623.htm
- http://m.3g.gqskj.cn/xnews/3873.htm
- http://m.3g.gqskj.cn/xnews/32642.htm
- http://m.3g.gqskj.cn/xnews/89970.htm
- http://m.3g.gqskj.cn/xnews/27233.htm
- http://m.3g.gqskj.cn/xnews/834497.htm
- http://m.3g.gqskj.cn/xnews/9118215.htm
- http://m.3g.gqskj.cn/xnews/8577.htm
- http://m.3g.gqskj.cn/xnews/581772.htm
- http://m.3g.gqskj.cn/xnews/0337633.htm
- http://m.3g.gqskj.cn/xnews/0370036.htm
- http://m.3g.gqskj.cn/xnews/7111.htm
- http://m.3g.gqskj.cn/xnews/082623.htm
- http://m.3g.gqskj.cn/xnews/186324.htm
- http://m.3g.gqskj.cn/xnews/958368.htm
- http://m.3g.gqskj.cn/xnews/2531.htm
- http://m.3g.gqskj.cn/xnews/7129589.htm
- http://m.3g.gqskj.cn/xnews/6371.htm
- http://m.3g.gqskj.cn/xnews/12183.htm
- http://m.3g.gqskj.cn/xnews/232147.htm
- http://m.3g.gqskj.cn/xnews/42408.htm
- http://m.3g.gqskj.cn/xnews/532831.htm
- http://m.3g.gqskj.cn/xnews/226173.htm
- http://m.3g.gqskj.cn/xnews/508478.htm
- http://m.3g.gqskj.cn/xnews/551319.htm
- http://m.3g.gqskj.cn/xnews/5777146.htm
- http://m.3g.gqskj.cn/xnews/94189.htm
- http://m.3g.gqskj.cn/xnews/049246.htm
- http://m.3g.gqskj.cn/xnews/381499.htm
- http://m.3g.gqskj.cn/xnews/436342.htm
- http://m.3g.gqskj.cn/xnews/7021.htm
- http://m.3g.gqskj.cn/xnews/88952.htm
- http://m.3g.gqskj.cn/xnews/82447.htm
- http://m.3g.gqskj.cn/xnews/9611323.htm
- http://m.3g.gqskj.cn/xnews/8428.htm
- http://m.3g.gqskj.cn/xnews/616224.htm
- http://m.3g.gqskj.cn/xnews/245960.htm
- http://m.3g.gqskj.cn/xnews/61862.htm
- http://m.3g.gqskj.cn/xnews/212561.htm
- http://m.3g.gqskj.cn/xnews/738708.htm
- http://m.3g.gqskj.cn/xnews/8947.htm
- http://m.3g.gqskj.cn/xnews/876346.htm
- http://m.3g.gqskj.cn/xnews/123183.htm
- http://m.3g.gqskj.cn/xnews/1038994.htm
- http://m.3g.gqskj.cn/xnews/04282.htm
- http://m.3g.gqskj.cn/xnews/666380.htm
- http://m.3g.gqskj.cn/xnews/8746699.htm
- http://m.3g.gqskj.cn/xnews/9468.htm
- http://m.3g.gqskj.cn/xnews/5266151.htm
- http://m.3g.gqskj.cn/xnews/835232.htm

## 项目结构

```
xnews-aggregator/
├── cli.py                      # 命令行入口，注册所有子命令
├── requirements.txt            # 生产环境依赖锁定
├── pyproject.toml              # 项目元数据与构建配置
├── src/
│   ├── core/
│   │   ├── index.py            # 内存索引核心类，管理URL与元数据映射
│   │   ├── loader.py           # 从文件/流加载链接，实现去重逻辑
│   │   └── serializer.py       # 快照序列化与反序列化（JSON格式）
│   ├── net/
│   │   ├── fetcher.py          # 异步HTTP客户端，支持超时与重试
│   │   ├── parser.py           # lxml封装，提取标题/时间/关键词
│   │   └── checker.py          # 存活状态检测器，返回状态码与耗时
│   ├── api/
│   │   ├── server.py           # aiohttp服务启动与路由注册
│   │   ├── handlers.py         # 各端点请求处理函数
│   │   └── schemas.py          # Pydantic模型用于请求/响应校验
│   ├── utils/
│   │   ├── logger.py           # 统一日志配置（按级别输出到文件与控制台）
│   │   ├── filters.py          # 黑白名单正则匹配工具
│   │   └── timer.py            # 性能计时装饰器
│   └── plugins/
│       ├── tagger.py           # 标签自动建议与分类辅助
│       └── exporter.py         # 导出为CSV/HTML/JSON等格式
├── tests/
│   ├── unit/                   # 单元测试，覆盖核心类与工具函数
│   ├── integration/            # 集成测试，模拟HTTP请求与API调用
│   └── fixtures/               # 样例数据与模拟HTML页面
├── docs/                       # 完整文档，包含入门指南与API参考
├── samples/
│   └── links.txt               # 示例链接文件，供快速导入测试
└── scripts/
    ├── build.sh                # 构建发布包的脚本
    └── dev-setup.sh            # 开发环境一键初始化（创建虚拟环境并安装依赖）
```

## 贡献指南

1. 阅读项目行为准则与贡献规范，确保理解代码提交、issue 报告和讨论的基本礼仪。所有贡献者需签署开发者原创声明（DCO）。

2. 从 GitHub 仓库 Fork 项目到个人账户，然后克隆到本地，创建新分支进行开发。分支命名建议采用 feat/功能名 或 fix/问题编号 的格式。

3. 编写代码时保持与现有风格一致（遵循 PEP 8 规范），新增功能需同步编写单元测试，确保测试覆盖率不低于 80%。提交前运行 pytest 验证所有用例通过。

4. 提交 Pull Request 前更新相关文档，包括 docstrings、README 中的功能说明以及 docs 目录下的对应章节。PR 描述需清晰说明解决的问题、实现方案和测试结果。

5. 等待维护者 code review，根据反馈进行修改。合并后代码将自动触发 CI 流水线进行构建与发布。

## 常见问题

Q: 扫描大量链接时出现超时或连接错误，如何优化？

A: 建议降低并发数（--concurrency 参数），增加超时时间（--timeout 参数），并检查网络环境是否稳定。如果目标站点存在反爬机制，可配置 User-Agent 轮换或使用代理池。此外，可启用白名单模式仅检测关键来源，减少无效请求。

Q: 索引快照文件体积过大，加载缓慢怎么办？

A: 快照包含每个链接的完整元数据，随着资源数量增长文件会变大。建议定期执行导出和归档，清理超过 180 天未更新的失效链接。也可调整 serializer 模块中的压缩选项，开启 gzip 压缩以减小存储体积。对于大规模部署，可考虑将索引迁移至 SQLite 或 Redis 以提升查询性能。

Q: 如何自定义元数据提取规则，以适配非标准结构的新闻页面？

A: 可在 src/net/parser.py 中修改 XPath 或 CSS 选择器配置，或通过插件机制注册自定义解析函数。项目支持基于域名匹配不同的解析策略，用户可在 config.yaml 中为特定域名指定独立的标题、正文和日期提取规则，无需修改核心代码。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:48
