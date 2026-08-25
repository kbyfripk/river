# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的高密度外链资源聚合与导航系统。本系统专注于从特定信源节点批量采集、归档和索引新闻资讯类外链，为后续的内容分析、趋势追踪和知识图谱构建提供结构化的数据入口。

本项目定位于技术资源汇聚层，不对页面内容进行实质性改写或二次传播，仅提供高效、稳定、可审计的链接管理能力。目标用户包括数据研究员、舆情监测工程师、SEO 分析师以及需要构建自定义新闻聚合流的开发者。通过标准化的链接格式和批次化管理，WebLink Navigator 解决了海量分散链接难以统一维护和快速定位的问题，尤其适用于需要长期追踪特定站点内容发布规律的场景。

## 功能概览

- **批量链接导入**：支持通过文本列表或 CSV 批量导入外链，自动解析 URL 结构并提取域名、路径、参数等元数据。
- **信源分组管理**：基于域名和子目录模式对链接进行自动分组，便于按站点或栏目筛选，本版本内置对 m.blog.gqskj.cn 下 nnews 路径的专项支持。
- **链接状态检测**：定期对已收录链接进行可达性检查，标记异常状态（超时、404、重定向循环），辅助清理失效资源。
- **元数据自动补全**：通过可配置的抓取策略，自动获取页面标题、发布时间、内容摘要等信息，丰富链接索引维度。
- **标签与注解系统**：支持为用户自定义标签和备注，便于标记链接的主题类别、重要程度或处理状态。
- **批次追溯与导出**：每个链接均记录收录批次编号（当前为第 210/240 批）及收录时间戳，支持按批次导出完整链接清单为纯文本或 JSON 格式。

## 应用场景

- **技术资讯日常追踪**：研究人员每日通过 WebLink Navigator 获取指定信源的最新链接列表，快速浏览标题和摘要，筛选出与自身领域相关的文章进行深度阅读，避免在多个站点间手动切换。
- **历史数据回溯分析**：数据分析师利用本项目的批次归档能力，调取特定批次（如第 210 批）的全部链接，结合外部工具分析该时段内信源的内容发布频率、标题词频变化等趋势。
- **自定义舆情监控管道**：运维人员将 WebLink Navigator 输出的链接列表作为数据管道的起点，对接后续的内容解析、关键词匹配和告警模块，构建轻量级舆情监控系统，无需关注底层数据采集细节。
- **链接库定期维护审计**：站点管理员使用内置的状态检测功能，每月对全量链接执行一次可达性审计，生成失效链接报告，确保内部引用资源的有效性。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebLink Navigator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装依赖（使用 pip 和 npm 分别安装后端与前端依赖）
pip install -r requirements.txt
npm install --prefix ./frontend

# 启动开发服务（后端 API 默认监听 8000 端口，前端开发服务器默认监听 3000 端口）
npm run dev --prefix ./frontend &
python -m uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
```

访问 http://localhost:3000 即可进入链接管理界面。首次启动时，系统会自动创建 SQLite 数据库文件并初始化必要的数据表结构。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 及以上 | 后端运行环境，核心业务逻辑与 API 服务 |
| Node.js | 16.x 或 18.x LTS | 前端构建与开发服务器运行时 |
| pip | 22.x 及以上 | Python 包管理工具，用于安装后端依赖 |
| npm 或 yarn | npm 8.x / yarn 1.22+ | 前端包管理工具 |
| SQLite | 3.35 及以上（内置） | 默认轻量级数据库，无需额外安装，生产环境可切换至 PostgreSQL |
| aiohttp | 3.8.x | 异步 HTTP 客户端，用于链接状态检测和元数据抓取 |
| fastapi | 0.95.x | Web API 框架 |
| uvicorn | 0.21.x | ASGI 服务器，用于运行 API 服务 |
| vue.js | 3.2.x | 前端 UI 框架（通过 CDN 或构建工具引入） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide/ | 如何导入链接、管理标签、执行状态检测以及导出数据？ |
| 开发者指南 | /docs/developer-guide/ | 如何配置抓取策略、扩展元数据解析器、替换为 PostgreSQL 数据库？ |
| API 参考 | /docs/api-reference/ | 提供哪些 RESTful 接口？请求参数与响应格式分别是什么？ |
| 运维手册 | /docs/operations/ | 如何部署到生产环境？如何配置日志轮转和备份策略？ |
| 设计文档 | /docs/design/ | 系统整体架构是怎样的？数据模型和批次管理机制如何设计？ |

## 资源列表

- http://m.blog.gqskj.cn/nnews/614329.htm
- http://m.blog.gqskj.cn/nnews/7764172.htm
- http://m.blog.gqskj.cn/nnews/216586.htm
- http://m.blog.gqskj.cn/nnews/5320493.htm
- http://m.blog.gqskj.cn/nnews/7994495.htm
- http://m.blog.gqskj.cn/nnews/6793.htm
- http://m.blog.gqskj.cn/nnews/0966.htm
- http://m.blog.gqskj.cn/nnews/03640.htm
- http://m.blog.gqskj.cn/nnews/19687.htm
- http://m.blog.gqskj.cn/nnews/6824123.htm
- http://m.blog.gqskj.cn/nnews/8913.htm
- http://m.blog.gqskj.cn/nnews/811550.htm
- http://m.blog.gqskj.cn/nnews/73661.htm
- http://m.blog.gqskj.cn/nnews/20757.htm
- http://m.blog.gqskj.cn/nnews/484980.htm
- http://m.blog.gqskj.cn/nnews/807860.htm
- http://m.blog.gqskj.cn/nnews/37538.htm
- http://m.blog.gqskj.cn/nnews/09317.htm
- http://m.blog.gqskj.cn/nnews/46858.htm
- http://m.blog.gqskj.cn/nnews/12695.htm
- http://m.blog.gqskj.cn/nnews/0091.htm
- http://m.blog.gqskj.cn/nnews/679768.htm
- http://m.blog.gqskj.cn/nnews/09831.htm
- http://m.blog.gqskj.cn/nnews/73616.htm
- http://m.blog.gqskj.cn/nnews/458460.htm
- http://m.blog.gqskj.cn/nnews/5617248.htm
- http://m.blog.gqskj.cn/nnews/94681.htm
- http://m.blog.gqskj.cn/nnews/2300445.htm
- http://m.blog.gqskj.cn/nnews/91418.htm
- http://m.blog.gqskj.cn/nnews/8950929.htm
- http://m.blog.gqskj.cn/nnews/114930.htm
- http://m.blog.gqskj.cn/nnews/8997.htm
- http://m.blog.gqskj.cn/nnews/42430.htm
- http://m.blog.gqskj.cn/nnews/732537.htm
- http://m.blog.gqskj.cn/nnews/95614.htm
- http://m.blog.gqskj.cn/nnews/0767889.htm
- http://m.blog.gqskj.cn/nnews/458120.htm
- http://m.blog.gqskj.cn/nnews/28292.htm
- http://m.blog.gqskj.cn/nnews/89874.htm
- http://m.blog.gqskj.cn/nnews/2316165.htm
- http://m.blog.gqskj.cn/nnews/0672517.htm
- http://m.blog.gqskj.cn/nnews/6441500.htm
- http://m.blog.gqskj.cn/nnews/500304.htm
- http://m.blog.gqskj.cn/nnews/8067.htm
- http://m.blog.gqskj.cn/nnews/587881.htm
- http://m.blog.gqskj.cn/nnews/4349.htm
- http://m.blog.gqskj.cn/nnews/025834.htm
- http://m.blog.gqskj.cn/nnews/79000.htm
- http://m.blog.gqskj.cn/nnews/72208.htm
- http://m.blog.gqskj.cn/nnews/5160.htm
- http://m.blog.gqskj.cn/nnews/7550.htm
- http://m.blog.gqskj.cn/nnews/213254.htm
- http://m.blog.gqskj.cn/nnews/9580610.htm
- http://m.blog.gqskj.cn/nnews/31108.htm
- http://m.blog.gqskj.cn/nnews/5546305.htm
- http://m.blog.gqskj.cn/nnews/1763382.htm
- http://m.blog.gqskj.cn/nnews/8632117.htm
- http://m.blog.gqskj.cn/nnews/89526.htm
- http://m.blog.gqskj.cn/nnews/103718.htm
- http://m.blog.gqskj.cn/nnews/6122.htm
- http://m.blog.gqskj.cn/nnews/9023.htm
- http://m.blog.gqskj.cn/nnews/3478.htm
- http://m.blog.gqskj.cn/nnews/0317.htm
- http://m.blog.gqskj.cn/nnews/658521.htm
- http://m.blog.gqskj.cn/nnews/1847.htm
- http://m.blog.gqskj.cn/nnews/7674970.htm
- http://m.blog.gqskj.cn/nnews/09685.htm
- http://m.blog.gqskj.cn/nnews/15081.htm
- http://m.blog.gqskj.cn/nnews/8827.htm
- http://m.blog.gqskj.cn/nnews/6200.htm
- http://m.blog.gqskj.cn/nnews/2550.htm
- http://m.blog.gqskj.cn/nnews/33320.htm
- http://m.blog.gqskj.cn/nnews/45065.htm
- http://m.blog.gqskj.cn/nnews/0827197.htm
- http://m.blog.gqskj.cn/nnews/286318.htm
- http://m.blog.gqskj.cn/nnews/47058.htm
- http://m.blog.gqskj.cn/nnews/0049724.htm
- http://m.blog.gqskj.cn/nnews/6061.htm
- http://m.blog.gqskj.cn/nnews/7059795.htm
- http://m.blog.gqskj.cn/nnews/9753465.htm
- http://m.blog.gqskj.cn/nnews/750646.htm
- http://m.blog.gqskj.cn/nnews/6453172.htm
- http://m.blog.gqskj.cn/nnews/04236.htm
- http://m.blog.gqskj.cn/nnews/733367.htm
- http://m.blog.gqskj.cn/nnews/29950.htm
- http://m.blog.gqskj.cn/nnews/62064.htm
- http://m.blog.gqskj.cn/nnews/17042.htm
- http://m.blog.gqskj.cn/nnews/0145161.htm
- http://m.blog.gqskj.cn/nnews/2085259.htm
- http://m.blog.gqskj.cn/nnews/6680.htm
- http://m.blog.gqskj.cn/nnews/267953.htm
- http://m.blog.gqskj.cn/nnews/7783.htm
- http://m.blog.gqskj.cn/nnews/8568.htm
- http://m.blog.gqskj.cn/nnews/2079.htm
- http://m.blog.gqskj.cn/nnews/2372407.htm
- http://m.blog.gqskj.cn/nnews/537840.htm
- http://m.blog.gqskj.cn/nnews/93313.htm
- http://m.blog.gqskj.cn/nnews/1798.htm
- http://m.blog.gqskj.cn/nnews/50254.htm
- http://m.blog.gqskj.cn/nnews/911152.htm
- http://m.blog.gqskj.cn/nnews/55349.htm
- http://m.blog.gqskj.cn/nnews/7512.htm
- http://m.blog.gqskj.cn/nnews/366266.htm
- http://m.blog.gqskj.cn/nnews/3610.htm
- http://m.blog.gqskj.cn/nnews/181871.htm
- http://m.blog.gqskj.cn/nnews/2299587.htm
- http://m.blog.gqskj.cn/nnews/3814.htm
- http://m.blog.gqskj.cn/nnews/1628.htm
- http://m.blog.gqskj.cn/nnews/9941.htm
- http://m.blog.gqskj.cn/nnews/967244.htm
- http://m.blog.gqskj.cn/nnews/5841.htm
- http://m.blog.gqskj.cn/nnews/845294.htm
- http://m.blog.gqskj.cn/nnews/80030.htm
- http://m.blog.gqskj.cn/nnews/396203.htm
- http://m.blog.gqskj.cn/nnews/2426923.htm
- http://m.blog.gqskj.cn/nnews/04435.htm
- http://m.blog.gqskj.cn/nnews/7315389.htm
- http://m.blog.gqskj.cn/nnews/18539.htm
- http://m.blog.gqskj.cn/nnews/5528463.htm
- http://m.blog.gqskj.cn/nnews/5605475.htm
- http://m.blog.gqskj.cn/nnews/16977.htm
- http://m.blog.gqskj.cn/nnews/242325.htm
- http://m.blog.gqskj.cn/nnews/988905.htm
- http://m.blog.gqskj.cn/nnews/12081.htm
- http://m.blog.gqskj.cn/nnews/98009.htm
- http://m.blog.gqskj.cn/nnews/6611021.htm
- http://m.blog.gqskj.cn/nnews/1581.htm
- http://m.blog.gqskj.cn/nnews/33142.htm
- http://m.blog.gqskj.cn/nnews/3664138.htm
- http://m.blog.gqskj.cn/nnews/469055.htm
- http://m.blog.gqskj.cn/nnews/74853.htm
- http://m.blog.gqskj.cn/nnews/0830.htm
- http://m.blog.gqskj.cn/nnews/257882.htm
- http://m.blog.gqskj.cn/nnews/97151.htm
- http://m.blog.gqskj.cn/nnews/171983.htm
- http://m.blog.gqskj.cn/nnews/4056656.htm
- http://m.blog.gqskj.cn/nnews/18149.htm
- http://m.blog.gqskj.cn/nnews/6918.htm
- http://m.blog.gqskj.cn/nnews/75601.htm
- http://m.blog.gqskj.cn/nnews/2478958.htm
- http://m.blog.gqskj.cn/nnews/477655.htm
- http://m.blog.gqskj.cn/nnews/7282230.htm
- http://m.blog.gqskj.cn/nnews/649954.htm
- http://m.blog.gqskj.cn/nnews/341155.htm
- http://m.blog.gqskj.cn/nnews/91616.htm
- http://m.blog.gqskj.cn/nnews/0092.htm
- http://m.blog.gqskj.cn/nnews/139448.htm
- http://m.blog.gqskj.cn/nnews/47856.htm
- http://m.blog.gqskj.cn/nnews/1950422.htm
- http://m.blog.gqskj.cn/nnews/8557947.htm
- http://m.blog.gqskj.cn/nnews/9886228.htm
- http://m.blog.gqskj.cn/nnews/8968.htm
- http://m.blog.gqskj.cn/nnews/40330.htm
- http://m.blog.gqskj.cn/nnews/4159.htm
- http://m.blog.gqskj.cn/nnews/0705251.htm
- http://m.blog.gqskj.cn/nnews/1510259.htm
- http://m.blog.gqskj.cn/nnews/024762.htm
- http://m.blog.gqskj.cn/nnews/97661.htm
- http://m.blog.gqskj.cn/nnews/0666767.htm
- http://m.blog.gqskj.cn/nnews/0097.htm
- http://m.blog.gqskj.cn/nnews/36432.htm
- http://m.blog.gqskj.cn/nnews/321576.htm
- http://m.blog.gqskj.cn/nnews/7683469.htm
- http://m.blog.gqskj.cn/nnews/928451.htm
- http://m.blog.gqskj.cn/nnews/07901.htm
- http://m.blog.gqskj.cn/nnews/9428429.htm
- http://m.blog.gqskj.cn/nnews/3080389.htm
- http://m.blog.gqskj.cn/nnews/5212.htm
- http://m.blog.gqskj.cn/nnews/223226.htm
- http://m.blog.gqskj.cn/nnews/354667.htm
- http://m.blog.gqskj.cn/nnews/28392.htm
- http://m.blog.gqskj.cn/nnews/785856.htm
- http://m.blog.gqskj.cn/nnews/01804.htm
- http://m.blog.gqskj.cn/nnews/8356596.htm
- http://m.blog.gqskj.cn/nnews/2530164.htm
- http://m.blog.gqskj.cn/nnews/041861.htm
- http://m.blog.gqskj.cn/nnews/32918.htm
- http://m.blog.gqskj.cn/nnews/0340247.htm
- http://m.blog.gqskj.cn/nnews/3356713.htm
- http://m.blog.gqskj.cn/nnews/386133.htm
- http://m.blog.gqskj.cn/nnews/681717.htm
- http://m.blog.gqskj.cn/nnews/40762.htm
- http://m.blog.gqskj.cn/nnews/21887.htm
- http://m.blog.gqskj.cn/nnews/8013.htm
- http://m.blog.gqskj.cn/nnews/55963.htm
- http://m.blog.gqskj.cn/nnews/5845.htm
- http://m.blog.gqskj.cn/nnews/804047.htm
- http://m.blog.gqskj.cn/nnews/5843.htm
- http://m.blog.gqskj.cn/nnews/8017.htm
- http://m.blog.gqskj.cn/nnews/986560.htm
- http://m.blog.gqskj.cn/nnews/0727.htm
- http://m.blog.gqskj.cn/nnews/535236.htm
- http://m.blog.gqskj.cn/nnews/30193.htm
- http://m.blog.gqskj.cn/nnews/275922.htm
- http://m.blog.gqskj.cn/nnews/98829.htm
- http://m.blog.gqskj.cn/nnews/1098023.htm
- http://m.blog.gqskj.cn/nnews/2646.htm
- http://m.blog.gqskj.cn/nnews/6337.htm
- http://m.blog.gqskj.cn/nnews/59662.htm
- http://m.blog.gqskj.cn/nnews/575909.htm
- http://m.blog.gqskj.cn/nnews/6428.htm
- http://m.blog.gqskj.cn/nnews/5131658.htm
- http://m.blog.gqskj.cn/nnews/708615.htm
- http://m.blog.gqskj.cn/nnews/664235.htm
- http://m.blog.gqskj.cn/nnews/466390.htm
- http://m.blog.gqskj.cn/nnews/4358.htm
- http://m.blog.gqskj.cn/nnews/3112191.htm
- http://m.blog.gqskj.cn/nnews/609683.htm
- http://m.blog.gqskj.cn/nnews/4601538.htm
- http://m.blog.gqskj.cn/nnews/9771.htm
- http://m.blog.gqskj.cn/nnews/9304687.htm
- http://m.blog.gqskj.cn/nnews/44443.htm
- http://m.blog.gqskj.cn/nnews/291062.htm
- http://m.blog.gqskj.cn/nnews/5970595.htm
- http://m.blog.gqskj.cn/nnews/62087.htm
- http://m.blog.gqskj.cn/nnews/98241.htm
- http://m.blog.gqskj.cn/nnews/1307671.htm
- http://m.blog.gqskj.cn/nnews/678013.htm
- http://m.blog.gqskj.cn/nnews/00745.htm
- http://m.blog.gqskj.cn/nnews/37127.htm
- http://m.blog.gqskj.cn/nnews/2241.htm
- http://m.blog.gqskj.cn/nnews/778889.htm
- http://m.blog.gqskj.cn/nnews/836740.htm
- http://m.blog.gqskj.cn/nnews/590818.htm
- http://m.blog.gqskj.cn/nnews/08978.htm
- http://m.blog.gqskj.cn/nnews/3440.htm
- http://m.blog.gqskj.cn/nnews/6811363.htm
- http://m.blog.gqskj.cn/nnews/78206.htm
- http://m.blog.gqskj.cn/nnews/3989639.htm
- http://m.blog.gqskj.cn/nnews/542126.htm
- http://m.blog.gqskj.cn/nnews/6370.htm
- http://m.blog.gqskj.cn/nnews/6414.htm
- http://m.blog.gqskj.cn/nnews/2049387.htm
- http://m.blog.gqskj.cn/nnews/98311.htm
- http://m.blog.gqskj.cn/nnews/53570.htm
- http://m.blog.gqskj.cn/nnews/448441.htm
- http://m.blog.gqskj.cn/nnews/4930.htm
- http://m.blog.gqskj.cn/nnews/988661.htm
- http://m.blog.gqskj.cn/nnews/658429.htm
- http://m.blog.gqskj.cn/nnews/26416.htm
- http://m.blog.gqskj.cn/nnews/1062214.htm
- http://m.blog.gqskj.cn/nnews/29088.htm
- http://m.blog.gqskj.cn/nnews/357142.htm
- http://m.blog.gqskj.cn/nnews/0584.htm
- http://m.blog.gqskj.cn/nnews/0797.htm
- http://m.blog.gqskj.cn/nnews/14981.htm
- http://m.blog.gqskj.cn/nnews/324460.htm
- http://m.blog.gqskj.cn/nnews/637987.htm
- http://m.blog.gqskj.cn/nnews/78533.htm
- http://m.blog.gqskj.cn/nnews/61713.htm

## 项目结构

```
weblink-navigator/
├── app/                                  # 后端核心应用目录
│   ├── api/                              # API 路由层，定义所有 RESTful 端点
│   │   ├── endpoints/                    # 按资源划分的路由模块（links, tags, batches）
│   │   └── dependencies.py               # 依赖注入（数据库会话、认证等）
│   ├── core/                             # 核心业务逻辑与配置
│   │   ├── config.py                     # 全局配置（数据库连接、抓取参数、批次编号）
│   │   ├── link_processor.py             # 链接解析、校验、元数据提取核心类
│   │   └── batch_manager.py              # 批次创建、状态追踪、导出逻辑
│   ├── models/                           # 数据模型（SQLAlchemy ORM 实体）
│   │   ├── link.py                       # Link 表模型（url, domain, status, batch_id）
│   │   ├── batch.py                      # Batch 表模型（batch_no, created_at, count）
│   │   └── tag.py                        # Tag 与 LinkTag 关联表模型
│   ├── services/                         # 外部服务集成层
│   │   ├── fetcher.py                    # 基于 aiohttp 的异步页面抓取与标题解析
│   │   └── checker.py                    # 链接状态检测服务（并发 HEAD 请求）
│   └── main.py                           # FastAPI 应用入口，挂载路由与中间件
├── frontend/                             # 前端单页应用目录（Vue 3 + Vite）
│   ├── src/                              # 源代码目录
│   │   ├── components/                   # 可复用 UI 组件（链接列表、标签管理器、导入向导）
│   │   ├── views/                        # 页面级视图（Dashboard、BatchDetail、Settings）
│   │   ├── stores/                       # Pinia 状态管理（链接数据、筛选条件、用户偏好）
│   │   └── utils/                        # 前端工具函数（日期格式化、请求封装）
│   ├── public/                           # 静态资源（favicon、robots.txt）
│   └── package.json                      # 前端依赖与脚本定义
├── docs/                                 # 项目文档目录
│   ├── user-guide/                       # 用户手册（导入、管理、导出）
│   ├── developer-guide/                  # 开发者指南（扩展抓取器、更换数据库）
│   ├── api-reference/                    # API 接口文档（OpenAPI 生成）
│   └── operations/                       # 运维部署文档（Docker、systemd）
├── scripts/                              # 辅助脚本与工具
│   ├── import_links.py                   # 命令行批量导入工具（支持文本文件输入）
│   ├── health_check.py                   # 定时状态检测任务脚本
│   └── export_batch.py                   # 按批次导出链接为 JSON/CSV
├── tests/                                # 单元测试与集成测试
│   ├── test_api/                         # API 端点测试（pytest + httpx）
│   └── test_services/                    # 抓取器与检测器模拟测试
├── requirements.txt                      # Python 后端依赖清单
├── Dockerfile                            # 容器化构建文件（多阶段构建）
├── docker-compose.yml                    # 本地开发环境编排（后端 + 前端 + Redis 可选）
├── .env.example                          # 环境变量配置模板
└── README.md                             # 项目说明文档（本文件）
```

## 贡献指南

1. 查阅问题追踪列表：访问 GitHub Issues 页面，查找标注为 `good first issue` 或 `help wanted` 的待解决问题，评论表明认领意向后等待分配。
2. 派生并克隆仓库：将项目派生至个人账户，使用 `git clone` 获取代码，并添加 upstream 远程源以便同步主仓库更新。
3. 创建功能分支：基于 `main` 分支创建新的开发分支，分支命名建议使用 `feature/` 或 `fix/` 前缀，例如 `feature/add-csv-export`。
4. 编写测试与代码：针对新增功能或修复编写对应的单元测试，确保所有测试通过（运行 `pytest`），并遵循项目既有的代码风格（Python 使用 Black 格式化，前端使用 Prettier）。
5. 提交拉取请求：推送分支至派生仓库后，向主仓库的 `main` 分支发起 Pull Request，描述变更内容、关联问题编号并提供测试结果截图或日志。

## 常见问题

**问：如何导入用户提供的海量链接列表？**

答：您可以将所有 URL 逐行保存为一个纯文本文件（例如 `links.txt`），然后使用项目根目录下的命令行工具 `scripts/import_links.py` 执行导入：`python scripts/import_links.py --file links.txt --batch 210`。系统会自动为这批链接创建批次记录并逐条入库。若链接数量极大，建议分批导入或调整脚本中的提交间隔以减少数据库压力。

**问：链接状态检测显示大量超时或失败，是否正常？**

答：链接状态检测依赖于目标服务器的响应。若短时间内发起大量并发检测请求，可能被目标站点限流或触发防火墙规则，导致超时。建议在 `app/core/config.py` 中调低 `CHECKER_CONCURRENCY`（并发数）和 `CHECKER_TIMEOUT`（超时秒数），并启用 `CHECKER_INTERVAL` 参数进行间隔请求。对于明确返回 404 或 410 的链接，系统会自动标记为失效。

**问：本项目是否支持从列表中自动提取文章标题和发布时间？**

答：支持基础元数据提取。系统内置了针对常见新闻类 HTML 结构的解析规则（基于正则和 CSS 选择器）。但由于目标站点结构可能变化，建议在 `app/services/fetcher.py` 中根据实际返回的 HTML 结构调整 `TITLE_SELECTORS` 和 `DATE_SELECTORS` 列表。您也可以选择禁用自动抓取，仅保留链接管理功能，通过配置 `FETCH_METADATA_ENABLED = False` 实现。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:33
