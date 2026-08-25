# LinkSync Pro

LinkSync Pro 是一个面向技术团队与内容运营者的外链资产归集与健康度监测平台。该项目并非简单的 URL 列表，而是将散落在各类文档、历史代码库与运营配置中的超链接进行统一提取、版本追踪与可用性验证的工程化工具。其核心目标用户包括 DevOps 工程师、文档维护者、安全审计人员以及需要定期梳理外链资产的站点管理员。LinkSync Pro 解决的是大型项目中外部引用不可控、链接腐化、域名迁移导致引用失效以及合规性审计时外链台账缺失的问题。

## 功能概览

批量链接归集：支持从 Markdown、HTML、纯文本日志及 JSON 配置中自动提取所有 HTTP/HTTPS 链接，并去重归类。

存活状态探测：基于异步 HTTP 客户端并发执行 HEAD/GET 请求，检测每个链接的响应码、响应时间及 TLS 证书有效期。

变更差异比对：提供链接集合的版本差分功能，能够清晰标示新增链接、移除链接以及 URL 路径变更的记录。

元数据萃取：自动解析链接中的查询参数、片段标识符以及 MIME 类型，为主机名和路径建立索引。

过滤与标签系统：允许用户为链接打上分类标签，支持基于正则表达式的批量过滤与排除规则。

定时巡检任务：内置 Cron 调度器，可配置每日或每周自动执行全量链接扫描，并将异常结果输出至告警通道。

数据导出接口：提供 RESTful API 与 CLI 命令，支持将链接列表导出为 CSV、JSON 或 Markdown 表格格式。

## 应用场景

遗留系统文档重构：技术团队在整理数年前的项目文档时，可通过 LinkSync Pro 快速识别出引用了已下架内部服务的链接，从而批量替换为新的服务入口地址。

合规审计外链台账：金融或政务类项目在交付源码审计时，需要提供所有第三方依赖与外部引用的清单。LinkSync Pro 能够一键生成符合要求的链接清单，避免人工遗漏。

官网运营链接巡检：市场运营人员定期对官网底部的友情链接、合作伙伴入口及新闻稿中的引用链接进行连通性检查，及时发现被篡改或失效的跳转。

CI/CD 流水线集成：在代码合并请求触发时，自动运行 LinkSync Pro 扫描变更文件中的新增链接，若发现指向未知域名或黑名单站点的链接，则中断构建并通知提交者。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可通过 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/linksync/linksync-pro.git

# 进入项目工作目录
cd linksync-pro

# 安装项目依赖（使用 pip 虚拟环境）
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行快速扫描示例（扫描当前目录下所有 .md 文件）
python linksync.py scan --path ./docs --format markdown --output report.json

# 启动 Web 控制台（默认端口 8080）
python linksync.py serve --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 及以上 | 核心运行环境，低于此版本将无法解析异步语法 |
| aiohttp | 3.9.0 及以上 | 用于处理高并发异步 HTTP 请求与连接池管理 |
| lxml | 4.9.0 及以上 | 解析 HTML 与 XML 文档中的链接节点，支持 XPath 查询 |
| PyYAML | 6.0 及以上 | 加载用户自定义的配置文件与过滤规则集合 |
| cryptography | 39.0.0 及以上 | 用于解析 TLS 证书详情与过期时间计算 |
| uvicorn | 0.24.0 及以上 | 作为 Web 控制台的 ASGI 服务器网关 |
| pytest | 7.4.0 及以上 | 仅在开发与测试环境中用于单元测试与集成测试 |
| redis | 5.0 及以上 | 可选组件，用于分布式部署下的任务队列与缓存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | /docs/user_guide.md | 如何配置扫描范围、如何阅读扫描报告、如何设置定时任务 |
| API 参考 | /docs/api_reference.md | 每个 REST 接口的请求参数、响应结构以及鉴权方式 |
| 部署指南 | /docs/deployment.md | 如何在 Kubernetes 集群中部署高可用实例，环境变量清单 |
| 开发文档 | /docs/development.md | 项目模块划分、如何编写自定义链接解析器、提交 PR 的规范 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/5689.htm
- http://m.3g.gqskj.cn/xnews/101463.htm
- http://m.3g.gqskj.cn/xnews/620696.htm
- http://m.3g.gqskj.cn/xnews/9275031.htm
- http://m.3g.gqskj.cn/xnews/6162.htm
- http://m.3g.gqskj.cn/xnews/6214.htm
- http://m.3g.gqskj.cn/xnews/3360854.htm
- http://m.3g.gqskj.cn/xnews/1633326.htm
- http://m.3g.gqskj.cn/xnews/5211.htm
- http://m.3g.gqskj.cn/xnews/7297155.htm
- http://m.3g.gqskj.cn/xnews/912217.htm
- http://m.3g.gqskj.cn/xnews/9371391.htm
- http://m.3g.gqskj.cn/xnews/37015.htm
- http://m.3g.gqskj.cn/xnews/6235.htm
- http://m.3g.gqskj.cn/xnews/27090.htm
- http://m.3g.gqskj.cn/xnews/2215.htm
- http://m.3g.gqskj.cn/xnews/69898.htm
- http://m.3g.gqskj.cn/xnews/5132809.htm
- http://m.3g.gqskj.cn/xnews/02820.htm
- http://m.3g.gqskj.cn/xnews/4057168.htm
- http://m.3g.gqskj.cn/xnews/8928299.htm
- http://m.3g.gqskj.cn/xnews/52695.htm
- http://m.3g.gqskj.cn/xnews/81166.htm
- http://m.3g.gqskj.cn/xnews/32466.htm
- http://m.3g.gqskj.cn/xnews/0274893.htm
- http://m.3g.gqskj.cn/xnews/4546672.htm
- http://m.3g.gqskj.cn/xnews/53706.htm
- http://m.3g.gqskj.cn/xnews/2236460.htm
- http://m.3g.gqskj.cn/xnews/82016.htm
- http://m.3g.gqskj.cn/xnews/9609384.htm
- http://m.3g.gqskj.cn/xnews/430435.htm
- http://m.3g.gqskj.cn/xnews/697042.htm
- http://m.3g.gqskj.cn/xnews/1324.htm
- http://m.3g.gqskj.cn/xnews/215713.htm
- http://m.3g.gqskj.cn/xnews/896184.htm
- http://m.3g.gqskj.cn/xnews/2567487.htm
- http://m.3g.gqskj.cn/xnews/323957.htm
- http://m.3g.gqskj.cn/xnews/9536.htm
- http://m.3g.gqskj.cn/xnews/582088.htm
- http://m.3g.gqskj.cn/xnews/9914.htm
- http://m.3g.gqskj.cn/xnews/8695.htm
- http://m.3g.gqskj.cn/xnews/7301.htm
- http://m.3g.gqskj.cn/xnews/8243.htm
- http://m.3g.gqskj.cn/xnews/47568.htm
- http://m.3g.gqskj.cn/xnews/9277.htm
- http://m.3g.gqskj.cn/xnews/79984.htm
- http://m.3g.gqskj.cn/xnews/0998444.htm
- http://m.3g.gqskj.cn/xnews/4160764.htm
- http://m.3g.gqskj.cn/xnews/58878.htm
- http://m.3g.gqskj.cn/xnews/2048889.htm
- http://m.3g.gqskj.cn/xnews/0546519.htm
- http://m.3g.gqskj.cn/xnews/819029.htm
- http://m.3g.gqskj.cn/xnews/0931612.htm
- http://m.3g.gqskj.cn/xnews/65617.htm
- http://m.3g.gqskj.cn/xnews/20053.htm
- http://m.3g.gqskj.cn/xnews/2698.htm
- http://m.3g.gqskj.cn/xnews/9551690.htm
- http://m.3g.gqskj.cn/xnews/2637.htm
- http://m.3g.gqskj.cn/xnews/4209.htm
- http://m.3g.gqskj.cn/xnews/45343.htm
- http://m.3g.gqskj.cn/xnews/43468.htm
- http://m.3g.gqskj.cn/xnews/0266640.htm
- http://m.3g.gqskj.cn/xnews/235245.htm
- http://m.3g.gqskj.cn/xnews/57584.htm
- http://m.3g.gqskj.cn/xnews/5203036.htm
- http://m.3g.gqskj.cn/xnews/89861.htm
- http://m.3g.gqskj.cn/xnews/7637223.htm
- http://m.3g.gqskj.cn/xnews/32681.htm
- http://m.3g.gqskj.cn/xnews/863202.htm
- http://m.3g.gqskj.cn/xnews/5574829.htm
- http://m.3g.gqskj.cn/xnews/5342964.htm
- http://m.3g.gqskj.cn/xnews/966626.htm
- http://m.3g.gqskj.cn/xnews/4246009.htm
- http://m.3g.gqskj.cn/xnews/5693.htm
- http://m.3g.gqskj.cn/xnews/978850.htm
- http://m.3g.gqskj.cn/xnews/61428.htm
- http://m.3g.gqskj.cn/xnews/094992.htm
- http://m.3g.gqskj.cn/xnews/8955.htm
- http://m.3g.gqskj.cn/xnews/44067.htm
- http://m.3g.gqskj.cn/xnews/1062105.htm
- http://m.3g.gqskj.cn/xnews/5791841.htm
- http://m.3g.gqskj.cn/xnews/8986.htm
- http://m.3g.gqskj.cn/xnews/785517.htm
- http://m.3g.gqskj.cn/xnews/8324.htm
- http://m.3g.gqskj.cn/xnews/990000.htm
- http://m.3g.gqskj.cn/xnews/880542.htm
- http://m.3g.gqskj.cn/xnews/1868.htm
- http://m.3g.gqskj.cn/xnews/0683.htm
- http://m.3g.gqskj.cn/xnews/5496672.htm
- http://m.3g.gqskj.cn/xnews/9944.htm
- http://m.3g.gqskj.cn/xnews/71474.htm
- http://m.3g.gqskj.cn/xnews/405087.htm
- http://m.3g.gqskj.cn/xnews/081635.htm
- http://m.3g.gqskj.cn/xnews/90599.htm
- http://m.3g.gqskj.cn/xnews/7867.htm
- http://m.3g.gqskj.cn/xnews/524416.htm
- http://m.3g.gqskj.cn/xnews/0860216.htm
- http://m.3g.gqskj.cn/xnews/7158365.htm
- http://m.3g.gqskj.cn/xnews/8748795.htm
- http://m.3g.gqskj.cn/xnews/510483.htm
- http://m.3g.gqskj.cn/xnews/3126022.htm
- http://m.3g.gqskj.cn/xnews/687588.htm
- http://m.3g.gqskj.cn/xnews/1241.htm
- http://m.3g.gqskj.cn/xnews/71651.htm
- http://m.3g.gqskj.cn/xnews/7559.htm
- http://m.3g.gqskj.cn/xnews/450480.htm
- http://m.3g.gqskj.cn/xnews/4799.htm
- http://m.3g.gqskj.cn/xnews/25632.htm
- http://m.3g.gqskj.cn/xnews/139920.htm
- http://m.3g.gqskj.cn/xnews/2125745.htm
- http://m.3g.gqskj.cn/xnews/433772.htm
- http://m.3g.gqskj.cn/xnews/091656.htm
- http://m.3g.gqskj.cn/xnews/0600.htm
- http://m.3g.gqskj.cn/xnews/069007.htm
- http://m.3g.gqskj.cn/xnews/89354.htm
- http://m.3g.gqskj.cn/xnews/0071986.htm
- http://m.3g.gqskj.cn/xnews/4386580.htm
- http://m.3g.gqskj.cn/xnews/2373.htm
- http://m.3g.gqskj.cn/xnews/6724970.htm
- http://m.3g.gqskj.cn/xnews/8228594.htm
- http://m.3g.gqskj.cn/xnews/131890.htm
- http://m.3g.gqskj.cn/xnews/954996.htm
- http://m.3g.gqskj.cn/xnews/3937.htm
- http://m.3g.gqskj.cn/xnews/426682.htm
- http://m.3g.gqskj.cn/xnews/8936155.htm
- http://m.3g.gqskj.cn/xnews/7564959.htm
- http://m.3g.gqskj.cn/xnews/7423544.htm
- http://m.3g.gqskj.cn/xnews/7163.htm
- http://m.3g.gqskj.cn/xnews/0438521.htm
- http://m.3g.gqskj.cn/xnews/9816.htm
- http://m.3g.gqskj.cn/xnews/5141384.htm
- http://m.3g.gqskj.cn/xnews/0976388.htm
- http://m.3g.gqskj.cn/xnews/92591.htm
- http://m.3g.gqskj.cn/xnews/5469.htm
- http://m.3g.gqskj.cn/xnews/881603.htm
- http://m.3g.gqskj.cn/xnews/82172.htm
- http://m.3g.gqskj.cn/xnews/661068.htm
- http://m.3g.gqskj.cn/xnews/7122218.htm
- http://m.3g.gqskj.cn/xnews/3264824.htm
- http://m.3g.gqskj.cn/xnews/4017134.htm
- http://m.3g.gqskj.cn/xnews/720498.htm
- http://m.3g.gqskj.cn/xnews/814271.htm
- http://m.3g.gqskj.cn/xnews/33884.htm
- http://m.3g.gqskj.cn/xnews/83391.htm
- http://m.3g.gqskj.cn/xnews/9461.htm
- http://m.3g.gqskj.cn/xnews/9494119.htm
- http://m.3g.gqskj.cn/xnews/976924.htm
- http://m.3g.gqskj.cn/xnews/90623.htm
- http://m.3g.gqskj.cn/xnews/7096.htm
- http://m.3g.gqskj.cn/xnews/3777334.htm
- http://m.3g.gqskj.cn/xnews/870902.htm
- http://m.3g.gqskj.cn/xnews/010737.htm
- http://m.3g.gqskj.cn/xnews/040230.htm
- http://m.3g.gqskj.cn/xnews/0545892.htm
- http://m.3g.gqskj.cn/xnews/22769.htm
- http://m.3g.gqskj.cn/xnews/3917568.htm
- http://m.3g.gqskj.cn/xnews/8782968.htm
- http://m.3g.gqskj.cn/xnews/0257903.htm
- http://m.3g.gqskj.cn/xnews/250889.htm
- http://m.3g.gqskj.cn/xnews/2567.htm
- http://m.3g.gqskj.cn/xnews/796404.htm
- http://m.3g.gqskj.cn/xnews/9682.htm
- http://m.3g.gqskj.cn/xnews/2840194.htm
- http://m.3g.gqskj.cn/xnews/3774854.htm
- http://m.3g.gqskj.cn/xnews/9628.htm
- http://m.3g.gqskj.cn/xnews/5398357.htm
- http://m.3g.gqskj.cn/xnews/318496.htm
- http://m.3g.gqskj.cn/xnews/33521.htm
- http://m.3g.gqskj.cn/xnews/25238.htm
- http://m.3g.gqskj.cn/xnews/9380313.htm
- http://m.3g.gqskj.cn/xnews/15191.htm
- http://m.3g.gqskj.cn/xnews/984362.htm
- http://m.3g.gqskj.cn/xnews/6972.htm
- http://m.3g.gqskj.cn/xnews/8006.htm
- http://m.3g.gqskj.cn/xnews/30265.htm
- http://m.3g.gqskj.cn/xnews/289723.htm
- http://m.3g.gqskj.cn/xnews/279128.htm
- http://m.3g.gqskj.cn/xnews/1168726.htm
- http://m.3g.gqskj.cn/xnews/8523.htm
- http://m.3g.gqskj.cn/xnews/9607012.htm
- http://m.3g.gqskj.cn/xnews/0744684.htm
- http://m.3g.gqskj.cn/xnews/307926.htm
- http://m.3g.gqskj.cn/xnews/2115782.htm
- http://m.3g.gqskj.cn/xnews/3153807.htm
- http://m.3g.gqskj.cn/xnews/2453.htm
- http://m.3g.gqskj.cn/xnews/446842.htm
- http://m.3g.gqskj.cn/xnews/8002.htm
- http://m.3g.gqskj.cn/xnews/80095.htm
- http://m.3g.gqskj.cn/xnews/6893470.htm
- http://m.3g.gqskj.cn/xnews/2877.htm
- http://m.3g.gqskj.cn/xnews/6957917.htm
- http://m.3g.gqskj.cn/xnews/1580.htm
- http://m.3g.gqskj.cn/xnews/71963.htm
- http://m.3g.gqskj.cn/xnews/6773.htm
- http://m.3g.gqskj.cn/xnews/0208118.htm
- http://m.3g.gqskj.cn/xnews/96857.htm
- http://m.3g.gqskj.cn/xnews/52703.htm
- http://m.3g.gqskj.cn/xnews/95004.htm
- http://m.3g.gqskj.cn/xnews/7310.htm
- http://m.3g.gqskj.cn/xnews/9036086.htm
- http://m.3g.gqskj.cn/xnews/47498.htm
- http://m.3g.gqskj.cn/xnews/61149.htm
- http://m.3g.gqskj.cn/xnews/5557461.htm
- http://m.3g.gqskj.cn/xnews/569690.htm
- http://m.3g.gqskj.cn/xnews/6810691.htm
- http://m.3g.gqskj.cn/xnews/11641.htm
- http://m.3g.gqskj.cn/xnews/809050.htm
- http://m.3g.gqskj.cn/xnews/90683.htm
- http://m.3g.gqskj.cn/xnews/5324.htm
- http://m.3g.gqskj.cn/xnews/8657178.htm
- http://m.3g.gqskj.cn/xnews/54986.htm
- http://m.3g.gqskj.cn/xnews/2880.htm
- http://m.3g.gqskj.cn/xnews/69736.htm
- http://m.3g.gqskj.cn/xnews/913808.htm
- http://m.3g.gqskj.cn/xnews/030299.htm
- http://m.3g.gqskj.cn/xnews/772035.htm
- http://m.3g.gqskj.cn/xnews/45569.htm
- http://m.3g.gqskj.cn/xnews/7493.htm
- http://m.3g.gqskj.cn/xnews/3225599.htm
- http://m.3g.gqskj.cn/xnews/9884398.htm
- http://m.3g.gqskj.cn/xnews/6644.htm
- http://m.3g.gqskj.cn/xnews/927783.htm
- http://m.3g.gqskj.cn/xnews/461518.htm
- http://m.3g.gqskj.cn/xnews/0876.htm
- http://m.3g.gqskj.cn/xnews/5932.htm
- http://m.3g.gqskj.cn/xnews/886708.htm
- http://m.3g.gqskj.cn/xnews/9141.htm
- http://m.3g.gqskj.cn/xnews/631152.htm
- http://m.3g.gqskj.cn/xnews/8446704.htm
- http://m.3g.gqskj.cn/xnews/12764.htm
- http://m.3g.gqskj.cn/xnews/128073.htm
- http://m.3g.gqskj.cn/xnews/0801188.htm
- http://m.3g.gqskj.cn/xnews/5408.htm
- http://m.3g.gqskj.cn/xnews/213722.htm
- http://m.3g.gqskj.cn/xnews/9106292.htm
- http://m.3g.gqskj.cn/xnews/4784163.htm
- http://m.3g.gqskj.cn/xnews/0465342.htm
- http://m.3g.gqskj.cn/xnews/18411.htm
- http://m.3g.gqskj.cn/xnews/0293.htm
- http://m.3g.gqskj.cn/xnews/08922.htm
- http://m.3g.gqskj.cn/xnews/1958.htm
- http://m.3g.gqskj.cn/xnews/1103233.htm
- http://m.3g.gqskj.cn/xnews/566536.htm
- http://m.3g.gqskj.cn/xnews/2252.htm
- http://m.3g.gqskj.cn/xnews/7851468.htm
- http://m.3g.gqskj.cn/xnews/3479.htm
- http://m.3g.gqskj.cn/xnews/0035951.htm
- http://m.3g.gqskj.cn/xnews/2269223.htm
- http://m.3g.gqskj.cn/xnews/93272.htm
- http://m.3g.gqskj.cn/xnews/317120.htm

## 项目结构

```
linksync-pro/
├── linksync/                        # 核心 Python 包
│   ├── __init__.py                  # 包版本与导出声明
│   ├── cli.py                       # 命令行入口，解析子命令（scan, serve, diff）
│   ├── scanner/                     # 链接扫描子模块
│   │   ├── __init__.py
│   │   ├── file_parser.py           # 根据文件扩展名调用不同解析器
│   │   ├── markdown_extractor.py    # 使用正则提取 Markdown 内联链接与引用
│   │   └── html_extractor.py        # 基于 lxml 提取 a/img/link 标签的 href/src
│   ├── probe/                       # 链接探测子模块
│   │   ├── __init__.py
│   │   ├── http_client.py           # 封装 aiohttp 会话与重试策略
│   │   ├── ssl_checker.py           # 提取证书过期时间与颁发者信息
│   │   └── status_tracker.py        # 记录响应码、耗时、重定向链
│   ├── storage/                     # 数据持久化子模块
│   │   ├── __init__.py
│   │   ├── local_cache.py           # 使用 sqlite3 存储历史扫描记录
│   │   └── redis_queue.py           # 可选 Redis 连接器，用于任务分发
│   ├── report/                      # 报告生成子模块
│   │   ├── __init__.py
│   │   ├── json_exporter.py         # 输出结构化 JSON 供下游系统消费
│   │   └── markdown_renderer.py     # 生成人类可读的 Markdown 汇总表格
│   └── scheduler/                   # 定时任务子模块
│       ├── __init__.py
│       └── cron_runner.py           # 基于 schedule 库实现任务编排
├── config/                          # 配置目录
│   ├── default.yaml                 # 默认配置（并发数、超时、排除规则）
│   └── custom.yaml.example          # 用户自定义配置模板
├── tests/                           # 单元测试与集成测试
│   ├── test_scanner.py              # 针对各类文件格式的提取测试
│   ├── test_probe.py                # 模拟 HTTP 响应的探测测试
│   └── fixtures/                    # 测试用的静态样例文件
├── web/                             # Web 控制台前端静态资源
│   ├── index.html                   # 仪表板主页面
│   └── assets/                      # CSS 与 JavaScript 资源文件
├── docs/                            # 项目文档
│   ├── user_guide.md                # 用户操作指南
│   └── api_reference.md             # API 接口文档
├── scripts/                         # 运维与辅助脚本
│   ├── setup_db.sh                  # 初始化数据库表结构
│   └── run_scan_daily.sh            # 供 crontab 调用的每日扫描脚本
├── requirements.txt                 # 生产环境依赖清单
├── requirements-dev.txt             # 开发环境额外依赖（pytest, black, mypy）
├── Dockerfile                       # 基于 Python 3.11-slim 的容器镜像定义
├── docker-compose.yml               # 本地快速启动 Redis + 应用服务的编排文件
└── README.md                        # 项目入口说明文件
```

## 贡献指南

首先在 GitHub 上 Fork 本仓库，并将 Fork 后的仓库克隆至本地开发环境。请确保本地 Python 版本符合 3.9 以上的要求，并安装开发依赖。

创建新的功能分支，分支命名应遵循 `feature/描述` 或 `fix/描述` 的格式。所有代码变更需包含对应的单元测试，且测试覆盖率不得低于 80%。

提交代码前，运行 `make lint` 执行代码风格检查（基于 black 与 flake8），并运行 `make test` 确保所有测试用例通过。若涉及新增配置项或 API 字段，需同步更新 docs 目录下的对应文档。

完成本地验证后，发起 Pull Request 至主仓库的 develop 分支。PR 描述中需明确说明变更动机、影响范围以及如何手动验证该变更。核心维护者将在 48 小时内进行 Review。

## 常见问题

Q: 扫描大量链接时出现超时或连接错误，如何优化？

A: 可以在配置文件 default.yaml 中调整 `timeout` 和 `max_concurrent` 参数。对于网络环境较差的情况，建议将 `timeout` 提升至 30 秒，并将 `max_concurrent` 降低至 20 以避免端口耗尽。此外，可以启用 `retry` 策略，配置重试次数为 3 次。

Q: 如何忽略特定域名或路径的链接，避免误报？

A: 在 config/custom.yaml 中配置 `exclude_patterns` 列表，支持正则表达式。例如 `exclude_patterns: [".*\.local", ".*/internal/.*"]` 将忽略所有指向 .local 域名以及包含 /internal/ 路径的链接。修改配置后无需重启服务，下次扫描自动生效。

Q: LinkSync Pro 能否扫描需要登录态或带有 Cookie 的页面？

A: 目前该版本不支持携带动态会话凭证。对于需要认证的站点，建议在扫描前通过反向代理或本地 Hosts 映射将目标环境指向内部测试网关，由网关统一处理鉴权。后续版本计划支持自定义请求头注入，届时可配置固定的 Bearer Token。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:48
