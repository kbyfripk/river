# LinkVault 聚合资源索引系统

LinkVault 是一个面向技术内容聚合与知识索引的开源工具，定位于帮助开发者、研究人员与技术内容消费者从散落的网络资源中高效提取结构化信息。本系统通过标准化的元数据采集与分类机制，将原始 URL 资源转化为可检索、可追溯的知识图谱节点，解决技术信息过载时代下链接失效、上下文缺失与重复检索的痛点。目标用户包括开源社区文档维护者、技术博客作者、数据采集工程师以及需要长期管理外链资源的知识工作者。

## 功能概览

- 批量链接导入与归一化清洗：支持从纯文本、CSV 及 Markdown 列表批量导入 URL，自动去除冗余查询参数、统一协议格式并检测重复条目。

- 元数据自动抽取与补全：对每条导入链接发起轻量级 HEAD 请求，提取内容类型、状态码、最后修改时间及服务器信息，并依据响应头自动补全缺失的协议信息。

- 分层标签系统与自定义分类：允许用户创建多级标签体系（如 后端 / 数据库 / 缓存），并支持基于路径匹配、域名规则或正则表达式的自动打标规则。

- 全文检索与高级过滤：基于 SQLite FTS5 或 Elasticsearch 可选后端，提供对 URL、标题、描述及标签的全文搜索，并支持按状态码、域名、内容类型等多维度过滤。

- 资源状态健康巡检：内置定时任务调度器，可周期性检查已收录链接的可访问性，输出存活率报表并标记失效链接，支持 Webhook 告警。

- 数据导入导出标准接口：支持 JSON、YAML、CSV 及 Markdown 列表格式的完整导入导出，便于与其他文档工具链或静态站点生成器集成。

- 访问统计与热度排序：记录每条链接的点击次数、最后访问时间与引用来源，生成基于时间衰减算法的基础热度评分，辅助内容排序。

## 应用场景

技术博客与文档站的外链管理：技术作者在编写教程或 API 文档时，常需引用大量外部资源。LinkVault 可作为本地预处理工具，批量导入草稿中的所有 URL，自动检测死链并生成统一引用列表，避免发布后出现链接失效。

开源项目 README 资源清单维护：开源项目的贡献者需要定期整理 README 中的学习资料、工具列表或社区链接。利用 LinkVault 的导入导出功能，可将 Markdown 列表转换为结构化的资源目录，并在版本更新时快速比对差异。

数据采集管道的源头校验：数据采集工程师在构建爬虫或 API 调用前，可用 LinkVault 对种子 URL 列表进行存活预检与内容类型分类，过滤无效或非目标资源，提升采集效率与成功率。

个人知识库的链接归档：研究员或开发者可将日常积累的收藏夹、阅读列表或 Newsletter 中的链接统一导入 LinkVault，通过标签与全文检索构建个人外链知识库，并定期执行健康检查以维持归档质量。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程。请确保系统已安装 Git、Python 3.9 及以上版本以及 SQLite。

```bash
git clone https://github.com/linkvault/linkvault-core.git
cd linkvault-core
python -m venv venv
source venv/bin/activate  # Windows 使用 venv\Scripts\activate
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py load_links --input sample_links.txt
python manage.py runserver --host 127.0.0.1 --port 8080
```

启动后访问 http://127.0.0.1:8080 即可进入 Web 管理界面。若需仅使用 CLI 模式，执行 `python linkvault.py --help` 查看全部子命令。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，低于 3.9 不支持类型注解新语法 |
| SQLite | 3.35.0 或更高 | 内置 FTS5 全文搜索支持，用于默认存储后端 |
| pip | 21.0 或更高 | 依赖安装工具，确保可解析 pyproject.toml |
| Git | 2.25 或更高 | 仅开发模式需要，用于拉取最新代码与贡献提交 |
| 内存 | 最低 512 MB / 推荐 2 GB | 内存影响批量导入与健康检查任务的并发性能 |
| 磁盘 | 最低 1 GB 可用空间 | 用于存储 SQLite 数据库及日志文件，按每万条链接约 50 MB 估算 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何安装、配置、导入链接、执行巡检与导出结果 |
| 开发者指南 | /docs/developer-guide/ | 如何扩展标签规则、编写自定义采集器、集成外部存储 |
| API 参考 | /docs/api-reference/ | RESTful API 端点定义、请求与响应示例、鉴权方式 |
| 运维手册 | /docs/operations/ | 生产环境部署建议、日志轮转、性能调参与故障排查 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/521586.htm
- http://m.3g.gqskj.cn/xnews/1373.htm
- http://m.3g.gqskj.cn/xnews/390586.htm
- http://m.3g.gqskj.cn/xnews/573524.htm
- http://m.3g.gqskj.cn/xnews/357062.htm
- http://m.3g.gqskj.cn/xnews/271955.htm
- http://m.3g.gqskj.cn/xnews/496072.htm
- http://m.3g.gqskj.cn/xnews/3077.htm
- http://m.3g.gqskj.cn/xnews/4843.htm
- http://m.3g.gqskj.cn/xnews/9484.htm
- http://m.3g.gqskj.cn/xnews/0837810.htm
- http://m.3g.gqskj.cn/xnews/5405.htm
- http://m.3g.gqskj.cn/xnews/263352.htm
- http://m.3g.gqskj.cn/xnews/788028.htm
- http://m.3g.gqskj.cn/xnews/808848.htm
- http://m.3g.gqskj.cn/xnews/6174291.htm
- http://m.3g.gqskj.cn/xnews/17873.htm
- http://m.3g.gqskj.cn/xnews/7422767.htm
- http://m.3g.gqskj.cn/xnews/133966.htm
- http://m.3g.gqskj.cn/xnews/6876.htm
- http://m.3g.gqskj.cn/xnews/391333.htm
- http://m.3g.gqskj.cn/xnews/35571.htm
- http://m.3g.gqskj.cn/xnews/71596.htm
- http://m.3g.gqskj.cn/xnews/93138.htm
- http://m.3g.gqskj.cn/xnews/4369494.htm
- http://m.3g.gqskj.cn/xnews/6506941.htm
- http://m.3g.gqskj.cn/xnews/1715448.htm
- http://m.3g.gqskj.cn/xnews/52107.htm
- http://m.3g.gqskj.cn/xnews/110241.htm
- http://m.3g.gqskj.cn/xnews/435664.htm
- http://m.3g.gqskj.cn/xnews/367856.htm
- http://m.3g.gqskj.cn/xnews/983239.htm
- http://m.3g.gqskj.cn/xnews/1211.htm
- http://m.3g.gqskj.cn/xnews/0577596.htm
- http://m.3g.gqskj.cn/xnews/5257309.htm
- http://m.3g.gqskj.cn/xnews/2319347.htm
- http://m.3g.gqskj.cn/xnews/5809.htm
- http://m.3g.gqskj.cn/xnews/5476253.htm
- http://m.3g.gqskj.cn/xnews/17274.htm
- http://m.3g.gqskj.cn/xnews/1232.htm
- http://m.3g.gqskj.cn/xnews/863481.htm
- http://m.3g.gqskj.cn/xnews/3464783.htm
- http://m.3g.gqskj.cn/xnews/797897.htm
- http://m.3g.gqskj.cn/xnews/549324.htm
- http://m.3g.gqskj.cn/xnews/7560.htm
- http://m.3g.gqskj.cn/xnews/03359.htm
- http://m.3g.gqskj.cn/xnews/23027.htm
- http://m.3g.gqskj.cn/xnews/6330.htm
- http://m.3g.gqskj.cn/xnews/72246.htm
- http://m.3g.gqskj.cn/xnews/1880208.htm
- http://m.3g.gqskj.cn/xnews/9338.htm
- http://m.3g.gqskj.cn/xnews/60459.htm
- http://m.3g.gqskj.cn/xnews/7457.htm
- http://m.3g.gqskj.cn/xnews/004269.htm
- http://m.3g.gqskj.cn/xnews/6217.htm
- http://m.3g.gqskj.cn/xnews/66679.htm
- http://m.3g.gqskj.cn/xnews/991354.htm
- http://m.3g.gqskj.cn/xnews/05286.htm
- http://m.3g.gqskj.cn/xnews/208199.htm
- http://m.3g.gqskj.cn/xnews/70947.htm
- http://m.3g.gqskj.cn/xnews/9780.htm
- http://m.3g.gqskj.cn/xnews/4348200.htm
- http://m.3g.gqskj.cn/xnews/6666.htm
- http://m.3g.gqskj.cn/xnews/355434.htm
- http://m.3g.gqskj.cn/xnews/3780893.htm
- http://m.3g.gqskj.cn/xnews/839115.htm
- http://m.3g.gqskj.cn/xnews/038886.htm
- http://m.3g.gqskj.cn/xnews/7703.htm
- http://m.3g.gqskj.cn/xnews/10291.htm
- http://m.3g.gqskj.cn/xnews/133028.htm
- http://m.3g.gqskj.cn/xnews/69471.htm
- http://m.3g.gqskj.cn/xnews/718825.htm
- http://m.3g.gqskj.cn/xnews/56372.htm
- http://m.3g.gqskj.cn/xnews/459883.htm
- http://m.3g.gqskj.cn/xnews/10722.htm
- http://m.3g.gqskj.cn/xnews/854580.htm
- http://m.3g.gqskj.cn/xnews/41785.htm
- http://m.3g.gqskj.cn/xnews/702618.htm
- http://m.3g.gqskj.cn/xnews/6949.htm
- http://m.3g.gqskj.cn/xnews/8084.htm
- http://m.3g.gqskj.cn/xnews/174610.htm
- http://m.3g.gqskj.cn/xnews/2991530.htm
- http://m.3g.gqskj.cn/xnews/0877066.htm
- http://m.3g.gqskj.cn/xnews/5286659.htm
- http://m.3g.gqskj.cn/xnews/516280.htm
- http://m.3g.gqskj.cn/xnews/107791.htm
- http://m.3g.gqskj.cn/xnews/9017.htm
- http://m.3g.gqskj.cn/xnews/9228184.htm
- http://m.3g.gqskj.cn/xnews/85204.htm
- http://m.3g.gqskj.cn/xnews/27798.htm
- http://m.3g.gqskj.cn/xnews/0665024.htm
- http://m.3g.gqskj.cn/xnews/776329.htm
- http://m.3g.gqskj.cn/xnews/268403.htm
- http://m.3g.gqskj.cn/xnews/198958.htm
- http://m.3g.gqskj.cn/xnews/07875.htm
- http://m.3g.gqskj.cn/xnews/977473.htm
- http://m.3g.gqskj.cn/xnews/840855.htm
- http://m.3g.gqskj.cn/xnews/820652.htm
- http://m.3g.gqskj.cn/xnews/1977.htm
- http://m.3g.gqskj.cn/xnews/3557.htm
- http://m.3g.gqskj.cn/xnews/180832.htm
- http://m.3g.gqskj.cn/xnews/934367.htm
- http://m.3g.gqskj.cn/xnews/5484.htm
- http://m.3g.gqskj.cn/xnews/670580.htm
- http://m.3g.gqskj.cn/xnews/60736.htm
- http://m.3g.gqskj.cn/xnews/2960.htm
- http://m.3g.gqskj.cn/xnews/8692342.htm
- http://m.3g.gqskj.cn/xnews/3520.htm
- http://m.3g.gqskj.cn/xnews/499194.htm
- http://m.3g.gqskj.cn/xnews/9790847.htm
- http://m.3g.gqskj.cn/xnews/7014352.htm
- http://m.3g.gqskj.cn/xnews/8299340.htm
- http://m.3g.gqskj.cn/xnews/743134.htm
- http://m.3g.gqskj.cn/xnews/2361951.htm
- http://m.3g.gqskj.cn/xnews/084480.htm
- http://m.3g.gqskj.cn/xnews/6051.htm
- http://m.3g.gqskj.cn/xnews/41081.htm
- http://m.3g.gqskj.cn/xnews/6316.htm
- http://m.3g.gqskj.cn/xnews/43137.htm
- http://m.3g.gqskj.cn/xnews/362417.htm
- http://m.3g.gqskj.cn/xnews/1818558.htm
- http://m.3g.gqskj.cn/xnews/82678.htm
- http://m.3g.gqskj.cn/xnews/0657264.htm
- http://m.3g.gqskj.cn/xnews/29251.htm
- http://m.3g.gqskj.cn/xnews/342468.htm
- http://m.3g.gqskj.cn/xnews/761422.htm
- http://m.3g.gqskj.cn/xnews/42592.htm
- http://m.3g.gqskj.cn/xnews/95198.htm
- http://m.3g.gqskj.cn/xnews/2230.htm
- http://m.3g.gqskj.cn/xnews/206607.htm
- http://m.3g.gqskj.cn/xnews/91919.htm
- http://m.3g.gqskj.cn/xnews/9147.htm
- http://m.3g.gqskj.cn/xnews/0509340.htm
- http://m.3g.gqskj.cn/xnews/1378099.htm
- http://m.3g.gqskj.cn/xnews/97836.htm
- http://m.3g.gqskj.cn/xnews/013968.htm
- http://m.3g.gqskj.cn/xnews/941137.htm
- http://m.3g.gqskj.cn/xnews/1859.htm
- http://m.3g.gqskj.cn/xnews/219990.htm
- http://m.3g.gqskj.cn/xnews/7879782.htm
- http://m.3g.gqskj.cn/xnews/9977.htm
- http://m.3g.gqskj.cn/xnews/9452007.htm
- http://m.3g.gqskj.cn/xnews/1401.htm
- http://m.3g.gqskj.cn/xnews/935490.htm
- http://m.3g.gqskj.cn/xnews/6425.htm
- http://m.3g.gqskj.cn/xnews/5546.htm
- http://m.3g.gqskj.cn/xnews/622824.htm
- http://m.3g.gqskj.cn/xnews/2074.htm
- http://m.3g.gqskj.cn/xnews/8605.htm
- http://m.3g.gqskj.cn/xnews/4128.htm
- http://m.3g.gqskj.cn/xnews/05387.htm
- http://m.3g.gqskj.cn/xnews/7736.htm
- http://m.3g.gqskj.cn/xnews/2802181.htm
- http://m.3g.gqskj.cn/xnews/2734628.htm
- http://m.3g.gqskj.cn/xnews/7112.htm
- http://m.3g.gqskj.cn/xnews/18804.htm
- http://m.3g.gqskj.cn/xnews/732273.htm
- http://m.3g.gqskj.cn/xnews/8818.htm
- http://m.3g.gqskj.cn/xnews/4347.htm
- http://m.3g.gqskj.cn/xnews/9030993.htm
- http://m.3g.gqskj.cn/xnews/7246391.htm
- http://m.3g.gqskj.cn/xnews/361843.htm
- http://m.3g.gqskj.cn/xnews/02133.htm
- http://m.3g.gqskj.cn/xnews/3437.htm
- http://m.3g.gqskj.cn/xnews/6730973.htm
- http://m.3g.gqskj.cn/xnews/6287.htm
- http://m.3g.gqskj.cn/xnews/926791.htm
- http://m.3g.gqskj.cn/xnews/7524.htm
- http://m.3g.gqskj.cn/xnews/841039.htm
- http://m.3g.gqskj.cn/xnews/7103948.htm
- http://m.3g.gqskj.cn/xnews/08913.htm
- http://m.3g.gqskj.cn/xnews/5347385.htm
- http://m.3g.gqskj.cn/xnews/51267.htm
- http://m.3g.gqskj.cn/xnews/8315809.htm
- http://m.3g.gqskj.cn/xnews/0369599.htm
- http://m.3g.gqskj.cn/xnews/299850.htm
- http://m.3g.gqskj.cn/xnews/1016.htm
- http://m.3g.gqskj.cn/xnews/435881.htm
- http://m.3g.gqskj.cn/xnews/856626.htm
- http://m.3g.gqskj.cn/xnews/170270.htm
- http://m.3g.gqskj.cn/xnews/86914.htm
- http://m.3g.gqskj.cn/xnews/534284.htm
- http://m.3g.gqskj.cn/xnews/4288464.htm
- http://m.3g.gqskj.cn/xnews/6962.htm
- http://m.3g.gqskj.cn/xnews/400680.htm
- http://m.3g.gqskj.cn/xnews/3362.htm
- http://m.3g.gqskj.cn/xnews/141301.htm
- http://m.3g.gqskj.cn/xnews/403823.htm
- http://m.3g.gqskj.cn/xnews/272673.htm
- http://m.3g.gqskj.cn/xnews/98162.htm
- http://m.3g.gqskj.cn/xnews/1736840.htm
- http://m.3g.gqskj.cn/xnews/4379142.htm
- http://m.3g.gqskj.cn/xnews/167082.htm
- http://m.3g.gqskj.cn/xnews/07664.htm
- http://m.3g.gqskj.cn/xnews/9559338.htm
- http://m.3g.gqskj.cn/xnews/3924417.htm
- http://m.3g.gqskj.cn/xnews/8556989.htm
- http://m.3g.gqskj.cn/xnews/750748.htm
- http://m.3g.gqskj.cn/xnews/75138.htm
- http://m.3g.gqskj.cn/xnews/5163.htm
- http://m.3g.gqskj.cn/xnews/099964.htm
- http://m.3g.gqskj.cn/xnews/0541415.htm
- http://m.3g.gqskj.cn/xnews/65010.htm
- http://m.3g.gqskj.cn/xnews/804288.htm
- http://m.3g.gqskj.cn/xnews/75498.htm
- http://m.3g.gqskj.cn/xnews/3197.htm
- http://m.3g.gqskj.cn/xnews/7619212.htm
- http://m.3g.gqskj.cn/xnews/9123.htm
- http://m.3g.gqskj.cn/xnews/8821085.htm
- http://m.3g.gqskj.cn/xnews/9586079.htm
- http://m.3g.gqskj.cn/xnews/4287197.htm
- http://m.3g.gqskj.cn/xnews/7815864.htm
- http://m.3g.gqskj.cn/xnews/1942.htm
- http://m.3g.gqskj.cn/xnews/899493.htm
- http://m.3g.gqskj.cn/xnews/6080.htm
- http://m.3g.gqskj.cn/xnews/15953.htm
- http://m.3g.gqskj.cn/xnews/082763.htm
- http://m.3g.gqskj.cn/xnews/981235.htm
- http://m.3g.gqskj.cn/xnews/29534.htm
- http://m.3g.gqskj.cn/xnews/934148.htm
- http://m.3g.gqskj.cn/xnews/001660.htm
- http://m.3g.gqskj.cn/xnews/5886146.htm
- http://m.3g.gqskj.cn/xnews/033410.htm
- http://m.3g.gqskj.cn/xnews/8156076.htm
- http://m.3g.gqskj.cn/xnews/7386602.htm
- http://m.3g.gqskj.cn/xnews/92112.htm
- http://m.3g.gqskj.cn/xnews/1321076.htm
- http://m.3g.gqskj.cn/xnews/2755614.htm
- http://m.3g.gqskj.cn/xnews/249549.htm
- http://m.3g.gqskj.cn/xnews/5954.htm
- http://m.3g.gqskj.cn/xnews/51974.htm
- http://m.3g.gqskj.cn/xnews/06022.htm
- http://m.3g.gqskj.cn/xnews/402407.htm
- http://m.3g.gqskj.cn/xnews/704370.htm
- http://m.3g.gqskj.cn/xnews/8014913.htm
- http://m.3g.gqskj.cn/xnews/453613.htm
- http://m.3g.gqskj.cn/xnews/00777.htm
- http://m.3g.gqskj.cn/xnews/6741.htm
- http://m.3g.gqskj.cn/xnews/2094.htm
- http://m.3g.gqskj.cn/xnews/1088.htm
- http://m.3g.gqskj.cn/xnews/913707.htm
- http://m.3g.gqskj.cn/xnews/044513.htm
- http://m.3g.gqskj.cn/xnews/38358.htm
- http://m.3g.gqskj.cn/xnews/12733.htm
- http://m.3g.gqskj.cn/xnews/4261612.htm
- http://m.3g.gqskj.cn/xnews/7194.htm
- http://m.3g.gqskj.cn/xnews/46696.htm
- http://m.3g.gqskj.cn/xnews/3642.htm
- http://m.3g.gqskj.cn/xnews/7551.htm
- http://m.3g.gqskj.cn/xnews/555937.htm

## 项目结构

```
linkvault-core/
├── cmd/                                  # 命令行入口与子命令注册
│   ├── server/                           # Web 服务启动命令
│   │   └── main.go                       # 服务入口，初始化路由与中间件
│   └── cli/                              # 离线任务命令集
│       ├── import.go                     # 批量导入命令，支持 txt/csv/json
│       ├── check.go                      # 健康检查命令，可并发探测
│       └── export.go                     # 导出命令，支持 markdown/json/yaml
├── internal/                             # 内部私有包，不对外暴露
│   ├── core/                             # 核心业务逻辑
│   │   ├── link.go                       # 链接实体定义，包含 URL、状态、标签
│   │   ├── indexer.go                    # 索引引擎，管理 FTS5 与倒排索引
│   │   └── scheduler.go                  # 定时任务调度，基于 cron 表达式
│   ├── storage/                          # 存储层实现
│   │   ├── sqlite.go                     # SQLite 驱动，包含表结构与迁移
│   │   └── cache.go                      # 内存缓存层，用于热点链接快速读取
│   └── probe/                            # 网络探测模块
│       ├── http.go                       # HTTP/HTTPS 探针，支持重定向跟踪
│       └── parser.go                     # 响应解析，提取标题与 meta 信息
├── pkg/                                  # 可被外部引用的公共库
│   ├── types/                            # 公共数据结构
│   │   └── link.go                       # Link 结构体，用于 API 交互
│   └── utils/                            # 工具函数
│       ├── url.go                        # URL 归一化、路径拼接、域名提取
│       └── hash.go                       # 内容去重哈希计算
├── web/                                  # Web 前端资源
│   ├── static/                           # 静态文件 (CSS, JS, 图标)
│   │   ├── style.css                     # 基础样式，适配桌面与移动端
│   │   └── dashboard.js                  # 仪表盘交互，图表渲染
│   └── templates/                        # HTML 模板
│       ├── index.html                    # 首页列表与搜索框
│       └── detail.html                   # 单条链接详情页
├── configs/                              # 配置文件目录
│   ├── app.yaml                          # 主配置，包含端口、数据库路径
│   └── rules.yaml                        # 自动打标规则，支持正则与路径匹配
├── scripts/                              # 辅助脚本
│   ├── migrate_db.sh                     # 数据库迁移脚本
│   └── sample_links.txt                  # 示例链接列表，供快速测试
├── docs/                                 # 文档目录
│   ├── user-guide/                       # 用户手册
│   └── developer-guide/                  # 开发者指南
├── test/                                 # 测试代码
│   ├── unit/                             # 单元测试，按模块划分
│   └── integration/                      # 集成测试，需启动本地服务
├── go.mod                                # Go 模块定义文件
├── go.sum                                # 依赖校验和
└── README.md                             # 项目总览文档
```

## 贡献指南

1. 查阅开发者指南与现有 Issue 列表，确认待开发功能或待修复缺陷，在 GitHub Issue 中声明认领以避免重复工作。

2. 从主分支检出开发分支，分支命名规范为 `feature/功能简述` 或 `fix/缺陷编号`，确保所有代码变更均包含对应的单元测试与集成测试。

3. 提交代码前运行 `make lint` 与 `make test` 确保代码风格符合项目规范（gofmt + golangci-lint）且所有测试用例通过，并补充更新文档或示例。

4. 发起 Pull Request 至主分支，在描述中关联对应 Issue 编号并简要说明变更内容、测试覆盖情况及可能的破坏性变更，等待至少一位维护者进行 Code Review。

5. 维护者合入代码后，由 CI 流水线自动构建并发布至 nightly 版本，贡献者将列入 CONTRIBUTORS 列表及版本发布说明。

## 常见问题

Q: 导入大量链接时出现内存不足或超时错误，应如何优化？

A: 建议使用 `--batch-size` 参数将单次导入分割为多个小批次，例如 `--batch-size 100`。同时可在配置文件中降低 `probe.concurrency` 并发数以减少内存占用。若仍无法解决，可考虑关闭自动元数据抽取功能 `--no-fetch`，仅导入原始 URL 后再通过后台任务逐步补全。

Q: 健康检查任务如何配置自定义超时时间与重试策略？

A: 在 `configs/app.yaml` 中的 `probe` 字段下可设置 `timeout_seconds`（默认 5 秒）与 `retry_times`（默认 2 次）。对于特定域名，可通过 `rules.yaml` 的 `overrides` 节点单独配置，例如对已知慢速服务器调整超时至 15 秒。

Q: 是否支持将数据迁移至 PostgreSQL 或 MySQL 等外部数据库？

A: 当前版本默认仅支持 SQLite 以降低部署门槛，但存储层已抽象为接口。开发者可参考 `internal/storage/sqlite.go` 实现自定义驱动，并在 `cmd/server/main.go` 中通过环境变量切换数据源。官方计划在 v2.0 版本中提供官方 PostgreSQL 适配器。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:46
