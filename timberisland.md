# Bnews Resource Aggregator

Bnews Resource Aggregator 是一个面向技术内容聚合与结构化导航的开源外链汇总系统，专注于将分散于互联网各处的技术文章、新闻动态与数据源进行统一采集、分类存储与检索呈现。该项目定位于技术团队、内容运营者以及独立研究者，帮助其从大量原始链接中快速提取有效信息，构建可维护的知识资源库。

本项目通过轻量级后端服务与静态前端界面，将输入的批量 URL 资源转化为可查询、可标签化、可按时间线浏览的结构化数据。系统内置定期健康检查机制，自动识别失效链接并生成报表，确保资源库的长期可用性。Bnews Resource Aggregator 不生产内容，而是提供高效的内容发现与组织工具，让用户从链接管理琐事中解放出来，专注于价值阅读与分析。

## 功能概览

- **批量链接导入与解析**：支持通过文本文件、API 请求或手动输入批量提交 URL，系统自动提取页面标题、元描述及发布时间等关键字段。

- **智能分类与标签体系**：基于规则引擎与关键词匹配算法，对入库链接自动打标分类，支持自定义标签层级与重分类规则。

- **全文检索与高级过滤器**：提供标题、正文摘要、来源域名、时间范围、标签组合等多维度检索能力，返回结果按相关度或时间排序。

- **资源健康度监控**：定时探测已收录链接的可访问状态，记录 HTTP 状态码变化，对连续失效链接进行分级告警并支持批量导出异常列表。

- **个性化订阅与快照生成**：支持用户收藏特定分类或标签资源，系统每日生成个性化更新快照，通过邮件或 Webhook 推送变更通知。

- **开放 API 与数据导出**：提供 RESTful API 接口供第三方集成，支持 JSON、CSV、RSS 三种格式的数据导出，便于二次开发或迁移。

- **访问统计与热度分析**：记录链接被点击、收藏、分享的次数，生成热度趋势图，辅助用户判断内容价值。

## 应用场景

- **技术团队内部知识库构建**：研发团队可将日常查阅的技术博客、官方文档、问题修复记录等链接统一录入系统，通过标签分类形成团队共享的知识索引，减少重复搜索成本。

- **行业资讯监控与竞品分析**：市场分析师或产品经理可订阅特定领域的关键词与来源站点，系统自动聚合最新动态，辅助快速掌握行业风向与竞品动向。

- **学术研究文献管理**：研究人员在文献调研阶段，将预印本、期刊论文链接、数据集页面等资源入库，利用时间线视图和标签筛选快速定位相关文献，提升综述撰写效率。

- **个人阅读队列整理**：独立开发者或技术爱好者可将待读文章、教程视频、工具站点等链接集中托管，通过健康监控功能自动剔除失效资源，保持阅读队列整洁有效。

## 快速开始

以下步骤指导您在本地环境中快速启动 Bnews Resource Aggregator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/bnews-io/bnews-aggregator.git
cd bnews-aggregator

# 安装依赖（使用 pip 与 npm）
pip install -r requirements.txt
npm install --prefix frontend

# 初始化数据库并执行迁移
python manage.py migrate
python manage.py loaddata initial_categories

# 构建前端静态资源
npm run build --prefix frontend

# 启动开发服务器（默认监听 8000 端口）
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 即可进入系统首页。首次启动时，系统会自动创建管理员账户（用户名: admin，密码: bnews2026），请在登录后立即修改密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 后端运行环境，推荐使用 3.11 以上版本获得性能优化 |
| Node.js | 18.x 或 20.x LTS | 前端构建工具链依赖，用于编译 React 与 SCSS 资源 |
| PostgreSQL | 14.x 或更高 | 生产环境推荐主数据库，支持 JSONB 类型以存储元数据 |
| Redis | 6.2 或更高 | 缓存与消息队列后端，用于任务调度与临时数据存储 |
| Nginx | 1.22 或更高 | 生产环境反向代理与静态资源服务（可选但推荐） |
| Git | 2.30 或更高 | 版本控制工具，用于拉取与更新项目代码 |
| Docker | 20.10 或更高 | 容器化部署方案依赖（可选，仅当使用 Docker Compose 时） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/installation.md | 如何在不同操作系统上安装与配置服务？如何设置管理员账户？ |
| 用户指南 | /docs/user-guide/importing.md | 支持哪些批量导入方式？如何定义导入规则与去重策略？ |
| 开发手册 | /docs/developer/api-reference.md | API 端点详细说明、请求/响应格式、认证方式及错误码含义 |
| 开发手册 | /docs/developer/architecture.md | 系统整体架构图、模块划分、数据流转及扩展点设计说明 |
| 运维手册 | /docs/operator/deployment.md | 生产环境部署流程（Docker Compose / K8s），配置参数与环境变量 |
| 运维手册 | /docs/operator/monitoring.md | 如何接入 Prometheus 监控，配置健康检查与告警规则 |
| 贡献指南 | /CONTRIBUTING.md | 代码规范、提交信息格式、测试要求及 PR 评审流程 |

## 资源列表

- http://m.blog.fcful.cn/bnews/854195.htm
- http://m.blog.fcful.cn/bnews/69642.htm
- http://m.blog.fcful.cn/bnews/6073528.htm
- http://m.blog.fcful.cn/bnews/915916.htm
- http://m.blog.fcful.cn/bnews/391690.htm
- http://m.blog.fcful.cn/bnews/4634.htm
- http://m.blog.fcful.cn/bnews/461086.htm
- http://m.blog.fcful.cn/bnews/21165.htm
- http://m.blog.fcful.cn/bnews/2219566.htm
- http://m.blog.fcful.cn/bnews/19022.htm
- http://m.blog.fcful.cn/bnews/32876.htm
- http://m.blog.fcful.cn/bnews/8444.htm
- http://m.blog.fcful.cn/bnews/4283.htm
- http://m.blog.fcful.cn/bnews/4579341.htm
- http://m.blog.fcful.cn/bnews/381080.htm
- http://m.blog.fcful.cn/bnews/396862.htm
- http://m.blog.fcful.cn/bnews/7048980.htm
- http://m.blog.fcful.cn/bnews/0766.htm
- http://m.blog.fcful.cn/bnews/7642479.htm
- http://m.blog.fcful.cn/bnews/5272692.htm
- http://m.blog.fcful.cn/bnews/924545.htm
- http://m.blog.fcful.cn/bnews/0668.htm
- http://m.blog.fcful.cn/bnews/502671.htm
- http://m.blog.fcful.cn/bnews/352990.htm
- http://m.blog.fcful.cn/bnews/540826.htm
- http://m.blog.fcful.cn/bnews/6436.htm
- http://m.blog.fcful.cn/bnews/0027983.htm
- http://m.blog.fcful.cn/bnews/76206.htm
- http://m.blog.fcful.cn/bnews/8766458.htm
- http://m.blog.fcful.cn/bnews/4352435.htm
- http://m.blog.fcful.cn/bnews/05527.htm
- http://m.blog.fcful.cn/bnews/7305806.htm
- http://m.blog.fcful.cn/bnews/1678111.htm
- http://m.blog.fcful.cn/bnews/98146.htm
- http://m.blog.fcful.cn/bnews/3992.htm
- http://m.blog.fcful.cn/bnews/88137.htm
- http://m.blog.fcful.cn/bnews/07800.htm
- http://m.blog.fcful.cn/bnews/424430.htm
- http://m.blog.fcful.cn/bnews/879879.htm
- http://m.blog.fcful.cn/bnews/9870354.htm
- http://m.blog.fcful.cn/bnews/574167.htm
- http://m.blog.fcful.cn/bnews/157859.htm
- http://m.blog.fcful.cn/bnews/1467338.htm
- http://m.blog.fcful.cn/bnews/718619.htm
- http://m.blog.fcful.cn/bnews/8279.htm
- http://m.blog.fcful.cn/bnews/2191765.htm
- http://m.blog.fcful.cn/bnews/8694873.htm
- http://m.blog.fcful.cn/bnews/180237.htm
- http://m.blog.fcful.cn/bnews/41434.htm
- http://m.blog.fcful.cn/bnews/4418377.htm
- http://m.blog.fcful.cn/bnews/8177751.htm
- http://m.blog.fcful.cn/bnews/88588.htm
- http://m.blog.fcful.cn/bnews/659929.htm
- http://m.blog.fcful.cn/bnews/2667.htm
- http://m.blog.fcful.cn/bnews/3348381.htm
- http://m.blog.fcful.cn/bnews/649745.htm
- http://m.blog.fcful.cn/bnews/0430.htm
- http://m.blog.fcful.cn/bnews/81303.htm
- http://m.blog.fcful.cn/bnews/7151.htm
- http://m.blog.fcful.cn/bnews/5480.htm
- http://m.blog.fcful.cn/bnews/235816.htm
- http://m.blog.fcful.cn/bnews/1536781.htm
- http://m.blog.fcful.cn/bnews/0095.htm
- http://m.blog.fcful.cn/bnews/22987.htm
- http://m.blog.fcful.cn/bnews/129314.htm
- http://m.blog.fcful.cn/bnews/550558.htm
- http://m.blog.fcful.cn/bnews/5867.htm
- http://m.blog.fcful.cn/bnews/996162.htm
- http://m.blog.fcful.cn/bnews/2469318.htm
- http://m.blog.fcful.cn/bnews/607845.htm
- http://m.blog.fcful.cn/bnews/60254.htm
- http://m.blog.fcful.cn/bnews/1113979.htm
- http://m.blog.fcful.cn/bnews/334083.htm
- http://m.blog.fcful.cn/bnews/64820.htm
- http://m.blog.fcful.cn/bnews/2784.htm
- http://m.blog.fcful.cn/bnews/797672.htm
- http://m.blog.fcful.cn/bnews/245853.htm
- http://m.blog.fcful.cn/bnews/84665.htm
- http://m.blog.fcful.cn/bnews/1898083.htm
- http://m.blog.fcful.cn/bnews/37928.htm
- http://m.blog.fcful.cn/bnews/79118.htm
- http://m.blog.fcful.cn/bnews/34167.htm
- http://m.blog.fcful.cn/bnews/0941.htm
- http://m.blog.fcful.cn/bnews/0496.htm
- http://m.blog.fcful.cn/bnews/11504.htm
- http://m.blog.fcful.cn/bnews/0168680.htm
- http://m.blog.fcful.cn/bnews/8837609.htm
- http://m.blog.fcful.cn/bnews/946242.htm
- http://m.blog.fcful.cn/bnews/03505.htm
- http://m.blog.fcful.cn/bnews/2527362.htm
- http://m.blog.fcful.cn/bnews/41316.htm
- http://m.blog.fcful.cn/bnews/6736632.htm
- http://m.blog.fcful.cn/bnews/8396.htm
- http://m.blog.fcful.cn/bnews/5611992.htm
- http://m.blog.fcful.cn/bnews/296209.htm
- http://m.blog.fcful.cn/bnews/154685.htm
- http://m.blog.fcful.cn/bnews/0035.htm
- http://m.blog.fcful.cn/bnews/81869.htm
- http://m.blog.fcful.cn/bnews/1517.htm
- http://m.blog.fcful.cn/bnews/7415.htm
- http://m.blog.fcful.cn/bnews/4599.htm
- http://m.blog.fcful.cn/bnews/69585.htm
- http://m.blog.fcful.cn/bnews/9033632.htm
- http://m.blog.fcful.cn/bnews/3058230.htm
- http://m.blog.fcful.cn/bnews/36250.htm
- http://m.blog.fcful.cn/bnews/6172.htm
- http://m.blog.fcful.cn/bnews/924047.htm
- http://m.blog.fcful.cn/bnews/948518.htm
- http://m.blog.fcful.cn/bnews/0369508.htm
- http://m.blog.fcful.cn/bnews/2340.htm
- http://m.blog.fcful.cn/bnews/42531.htm
- http://m.blog.fcful.cn/bnews/9525198.htm
- http://m.blog.fcful.cn/bnews/941422.htm
- http://m.blog.fcful.cn/bnews/922903.htm
- http://m.blog.fcful.cn/bnews/80255.htm
- http://m.blog.fcful.cn/bnews/853978.htm
- http://m.blog.fcful.cn/bnews/8928.htm
- http://m.blog.fcful.cn/bnews/6852471.htm
- http://m.blog.fcful.cn/bnews/2869744.htm
- http://m.blog.fcful.cn/bnews/8051356.htm
- http://m.blog.fcful.cn/bnews/76825.htm
- http://m.blog.fcful.cn/bnews/8211.htm
- http://m.blog.fcful.cn/bnews/18464.htm
- http://m.blog.fcful.cn/bnews/60573.htm
- http://m.blog.fcful.cn/bnews/924011.htm
- http://m.blog.fcful.cn/bnews/6492453.htm
- http://m.blog.fcful.cn/bnews/8413.htm
- http://m.blog.fcful.cn/bnews/675383.htm
- http://m.blog.fcful.cn/bnews/718677.htm
- http://m.blog.fcful.cn/bnews/948571.htm
- http://m.blog.fcful.cn/bnews/336931.htm
- http://m.blog.fcful.cn/bnews/352985.htm
- http://m.blog.fcful.cn/bnews/1807388.htm
- http://m.blog.fcful.cn/bnews/414612.htm
- http://m.blog.fcful.cn/bnews/23812.htm
- http://m.blog.fcful.cn/bnews/9308.htm
- http://m.blog.fcful.cn/bnews/6510896.htm
- http://m.blog.fcful.cn/bnews/777122.htm
- http://m.blog.fcful.cn/bnews/9997.htm
- http://m.blog.fcful.cn/bnews/889646.htm
- http://m.blog.fcful.cn/bnews/651599.htm
- http://m.blog.fcful.cn/bnews/8980966.htm
- http://m.blog.fcful.cn/bnews/2579.htm
- http://m.blog.fcful.cn/bnews/62541.htm
- http://m.blog.fcful.cn/bnews/4522.htm
- http://m.blog.fcful.cn/bnews/6662.htm
- http://m.blog.fcful.cn/bnews/4520366.htm
- http://m.blog.fcful.cn/bnews/6314.htm
- http://m.blog.fcful.cn/bnews/7548951.htm
- http://m.blog.fcful.cn/bnews/20198.htm
- http://m.blog.fcful.cn/bnews/857095.htm
- http://m.blog.fcful.cn/bnews/0627703.htm
- http://m.blog.fcful.cn/bnews/3363947.htm
- http://m.blog.fcful.cn/bnews/1219.htm
- http://m.blog.fcful.cn/bnews/940074.htm
- http://m.blog.fcful.cn/bnews/49672.htm
- http://m.blog.fcful.cn/bnews/9125.htm
- http://m.blog.fcful.cn/bnews/12484.htm
- http://m.blog.fcful.cn/bnews/7925134.htm
- http://m.blog.fcful.cn/bnews/14311.htm
- http://m.blog.fcful.cn/bnews/76364.htm
- http://m.blog.fcful.cn/bnews/286160.htm
- http://m.blog.fcful.cn/bnews/875540.htm
- http://m.blog.fcful.cn/bnews/99839.htm
- http://m.blog.fcful.cn/bnews/3669.htm
- http://m.blog.fcful.cn/bnews/8467856.htm
- http://m.blog.fcful.cn/bnews/84817.htm
- http://m.blog.fcful.cn/bnews/24429.htm
- http://m.blog.fcful.cn/bnews/02505.htm
- http://m.blog.fcful.cn/bnews/3054667.htm
- http://m.blog.fcful.cn/bnews/71135.htm
- http://m.blog.fcful.cn/bnews/56214.htm
- http://m.blog.fcful.cn/bnews/735545.htm
- http://m.blog.fcful.cn/bnews/701675.htm
- http://m.blog.fcful.cn/bnews/6053412.htm
- http://m.blog.fcful.cn/bnews/3079754.htm
- http://m.blog.fcful.cn/bnews/19754.htm
- http://m.blog.fcful.cn/bnews/352307.htm
- http://m.blog.fcful.cn/bnews/87688.htm
- http://m.blog.fcful.cn/bnews/25373.htm
- http://m.blog.fcful.cn/bnews/839929.htm
- http://m.blog.fcful.cn/bnews/64275.htm
- http://m.blog.fcful.cn/bnews/3440426.htm
- http://m.blog.fcful.cn/bnews/7242571.htm
- http://m.blog.fcful.cn/bnews/18174.htm
- http://m.blog.fcful.cn/bnews/3901.htm
- http://m.blog.fcful.cn/bnews/48955.htm
- http://m.blog.fcful.cn/bnews/53248.htm
- http://m.blog.fcful.cn/bnews/586439.htm
- http://m.blog.fcful.cn/bnews/941302.htm
- http://m.blog.fcful.cn/bnews/388299.htm
- http://m.blog.fcful.cn/bnews/6697668.htm
- http://m.blog.fcful.cn/bnews/55441.htm
- http://m.blog.fcful.cn/bnews/020847.htm
- http://m.blog.fcful.cn/bnews/945489.htm
- http://m.blog.fcful.cn/bnews/0260076.htm
- http://m.blog.fcful.cn/bnews/60820.htm
- http://m.blog.fcful.cn/bnews/3499.htm
- http://m.blog.fcful.cn/bnews/92829.htm
- http://m.blog.fcful.cn/bnews/7660297.htm
- http://m.blog.fcful.cn/bnews/70665.htm
- http://m.blog.fcful.cn/bnews/262823.htm
- http://m.blog.fcful.cn/bnews/8237.htm
- http://m.blog.fcful.cn/bnews/27653.htm
- http://m.blog.fcful.cn/bnews/9140085.htm
- http://m.blog.fcful.cn/bnews/459893.htm
- http://m.blog.fcful.cn/bnews/37058.htm
- http://m.blog.fcful.cn/bnews/574418.htm
- http://m.blog.fcful.cn/bnews/4724.htm
- http://m.blog.fcful.cn/bnews/60066.htm
- http://m.blog.fcful.cn/bnews/511913.htm
- http://m.blog.fcful.cn/bnews/148553.htm
- http://m.blog.fcful.cn/bnews/6829.htm
- http://m.blog.fcful.cn/bnews/0970727.htm
- http://m.blog.fcful.cn/bnews/48355.htm
- http://m.blog.fcful.cn/bnews/97091.htm
- http://m.blog.fcful.cn/bnews/4691408.htm
- http://m.blog.fcful.cn/bnews/1212121.htm
- http://m.blog.fcful.cn/bnews/1124.htm
- http://m.blog.fcful.cn/bnews/679351.htm
- http://m.blog.fcful.cn/bnews/1405.htm
- http://m.blog.fcful.cn/bnews/4292.htm
- http://m.blog.fcful.cn/bnews/674145.htm
- http://m.blog.fcful.cn/bnews/813029.htm
- http://m.blog.fcful.cn/bnews/9232949.htm
- http://m.blog.fcful.cn/bnews/6759.htm
- http://m.blog.fcful.cn/bnews/6511.htm
- http://m.blog.fcful.cn/bnews/994585.htm
- http://m.blog.fcful.cn/bnews/8941200.htm
- http://m.blog.fcful.cn/bnews/269495.htm
- http://m.blog.fcful.cn/bnews/925982.htm
- http://m.blog.fcful.cn/bnews/2654659.htm
- http://m.blog.fcful.cn/bnews/15811.htm
- http://m.blog.fcful.cn/bnews/181441.htm
- http://m.blog.fcful.cn/bnews/7851275.htm
- http://m.blog.fcful.cn/bnews/0830.htm
- http://m.blog.fcful.cn/bnews/15075.htm
- http://m.blog.fcful.cn/bnews/301977.htm
- http://m.blog.fcful.cn/bnews/541908.htm
- http://m.blog.fcful.cn/bnews/74495.htm
- http://m.blog.fcful.cn/bnews/19732.htm
- http://m.blog.fcful.cn/bnews/297839.htm
- http://m.blog.fcful.cn/bnews/8710.htm
- http://m.blog.fcful.cn/bnews/56731.htm
- http://m.blog.fcful.cn/bnews/84719.htm
- http://m.blog.fcful.cn/bnews/7856173.htm
- http://m.blog.fcful.cn/bnews/7705362.htm
- http://m.blog.fcful.cn/bnews/606468.htm
- http://m.blog.fcful.cn/bnews/5028.htm
- http://m.blog.fcful.cn/bnews/0104.htm

## 项目结构

```
bnews-aggregator/
├── backend/                          # 后端服务主目录
│   ├── api/                          # RESTful API 路由与视图集
│   │   ├── endpoints/                # 按资源类型划分的端点模块 (links, tags, users, reports)
│   │   └── serializers/              # DRF 序列化器，定义输入输出数据格式
│   ├── core/                         # 核心业务逻辑层
│   │   ├── crawler/                  # 链接抓取与解析引擎 (requests + BeautifulSoup)
│   │   ├── classifier/               # 基于规则与机器学习的标签分类器
│   │   ├── health/                   # 健康探测调度器 (apscheduler + httpx)
│   │   └── search/                   # 全文检索引擎封装 (whoosh / elasticsearch 适配)
│   ├── models/                       # 数据库模型定义 (Django ORM)
│   │   ├── link.py                   # Link 模型：存储 URL、标题、摘要、元数据
│   │   ├── tag.py                    # Tag 模型与 Link-Tag 多对多关联
│   │   └── snapshot.py               # 快照与订阅记录模型
│   ├── tasks/                        # 异步任务队列 (Celery)
│   │   ├── import_tasks.py           # 批量导入与解析任务
│   │   └── health_tasks.py           # 定时健康检查与告警任务
│   └── utils/                        # 通用工具函数 (日志、缓存、验证码、加密)
├── frontend/                         # 前端单页应用 (React + TypeScript)
│   ├── src/
│   │   ├── components/               # 可复用 UI 组件 (表格、过滤器、图表、导入面板)
│   │   ├── pages/                    # 页面级组件 (仪表盘、资源列表、详情、设置)
│   │   ├── hooks/                    # 自定义 React Hooks (useFetch, usePagination)
│   │   └── stores/                   # Zustand 状态管理 (用户偏好、筛选条件、缓存)
│   └── public/                       # 静态资源 (favicon, manifest, 默认封面图)
├── deployment/                       # 部署与运维配置
│   ├── docker/                       # Dockerfile 与 Compose 编排文件
│   │   ├── Dockerfile.backend
│   │   ├── Dockerfile.frontend
│   │   └── docker-compose.prod.yml
│   ├── nginx/                        # Nginx 站点配置模板 (gzip, 缓存策略, 反向代理)
│   └── supervisor/                   # Supervisor 进程管理配置 (celery, beat, gunicorn)
├── docs/                             # 完整项目文档 (Sphinx / MkDocs)
│   ├── user-guide/                   # 面向使用者的操作指南
│   ├── developer/                    # 面向开发者的接口文档与架构说明
│   └── operator/                     # 面向运维人员的部署与监控手册
├── scripts/                          # 辅助脚本 (数据迁移、测试数据生成、备份)
├── tests/                            # 单元测试与集成测试 (pytest + django.test)
│   ├── unit/                         # 后端单元测试 (模型、序列化器、工具函数)
│   └── integration/                  # API 端到端测试与爬虫模拟测试
├── .env.example                      # 环境变量配置模板 (数据库连接、Redis、密钥)
├── .gitignore                        # Git 忽略规则 (venv, node_modules, .pyc, .log)
├── LICENSE                           # MIT 许可证全文
├── README.md                         # 本文件
├── requirements.txt                  # Python 后端依赖列表 (Django, DRF, Celery, etc.)
├── package.json                      # Node.js 前端依赖与构建脚本
└── pyproject.toml                    # 项目元数据与黑盒测试配置 (pytest, black, isort)
```

## 贡献指南

我们欢迎并鼓励社区贡献者参与 Bnews Resource Aggregator 的开发与改进。请遵循以下流程提交贡献：

1. **查找或创建 Issue**：在 GitHub Issues 页面搜索已有任务，或创建新 Issue 描述您发现的问题或期望新增的功能。建议先与维护者沟通确认需求合理性，避免无效工作。

2. **派生仓库并创建特性分支**：将主仓库 Fork 至个人账户，然后克隆派生仓库到本地，基于 `main` 分支创建一个新的特性分支，分支命名遵循 `feature/简要描述` 或 `fix/问题编号` 格式。

3. **编写代码并补充测试**：确保代码风格符合项目配置（Black + isort），为新逻辑编写单元测试，保证测试覆盖率不低于 80%。若涉及 API 变更，请同步更新 Swagger 文档注释。

4. **提交变更并签署 DCO**：提交信息采用约定式提交格式（如 `feat: 添加批量导入进度通知` 或 `fix: 修复健康检查超时导致任务堆积`）。提交时需签署开发者原创声明（Developer Certificate of Origin），即使用 `git commit -s` 选项。

5. **发起 Pull Request**：推送分支到派生仓库，然后向主仓库的 `main` 分支发起 Pull Request。PR 描述中须关联相关 Issue 编号，并简要说明变更内容与测试结果。维护者将在 3 个工作日内进行评审，必要时会提出修改建议。

## 常见问题

**问：系统支持导入的链接数量上限是多少？单次批量导入建议最大条数是多少？**

答：系统本身不设硬性数量上限，实际吞吐量取决于服务器内存与数据库性能。根据生产环境测试，单次批量导入建议不超过 5000 条，以保证解析任务在合理时间内完成。若需导入更大规模数据，建议分割为多个批次，或使用后台异步导入功能（通过 Celery 队列串行处理），避免前端请求超时。

**问：已入库的链接如果源站删除了内容，系统会如何处理？**

答：健康监控模块会按可配置的周期（默认每 7 天）对所有链接发起 HEAD 请求检查可访问性。当检测到连续 3 次返回 4xx 或 5xx 状态码时，该链接会被标记为「失效」并移出默认搜索结果列表。用户可在「失效链接」视图中查看所有异常记录，并批量导出为 CSV 文件。系统不会自动删除失效链接的记录，以便用户追溯历史数据。

**问：能否将系统部署到内网环境，完全不访问公网？**

答：可以。Bnews Resource Aggregator 的核心功能（入库、检索、分类、统计）完全依赖本地数据库与搜索引擎，无需对外部 API 发起调用。唯一依赖公网的操作是链接健康检查（需要向目标站点发起请求），但您可以在配置文件中将健康检查功能关闭，或设定为仅检查内网 IP 段。静态资源（前端框架、字体图标）也支持离线打包，构建时使用 `--offline` 参数即可生成完全自包含的部署包。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
