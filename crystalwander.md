# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的轻量级外链聚合与导航系统。该项目专注于对分散在各类资讯源中的深度长文、技术报道和行业分析进行结构化收集与索引，提供基于元数据的快速检索和分类浏览能力。项目本身不存储任何内容全文，仅维护指向原始出处的链接与基础属性信息，适用于个人知识管理辅助、行业动态追踪以及自动化信息聚合等场景。

## 功能概览

- 批量链接导入与自动元数据提取：支持从文本列表、RSS 订阅源及站点地图批量导入外部链接，并自动提取标题、发布时间、内容摘要等关键元数据。

- 多维度标签与分类体系：允许用户自定义标签树，对链接进行多级分类标注，支持一对多标签关联，便于构建个性化知识分类系统。

- 全文检索与高级筛选：基于倒排索引提供标题与摘要级别的关键词检索，同时支持按时间区间、来源域名、标签组合等多条件筛选。

- 定期健康检查与失效链接报告：后台定时任务对已收录链接进行可用性探测，自动标记访问异常链接，并生成可导出的失效报告。

- 导入导出与数据迁移接口：支持 JSON、CSV 和 OPML 格式的数据导入导出，提供标准 RESTful API 接口，便于与其他知识管理工具集成。

- 用户自定义视图与仪表盘：支持将常用筛选条件保存为视图，在仪表盘上集中展示特定分类或标签下的最新链接动态。

- 浏览器扩展快速收藏：提供 Chrome 与 Firefox 浏览器扩展，支持在浏览过程中一键将当前页面链接保存至 Navigator 系统，并自动填充页面元数据。

## 应用场景

- 技术资讯日常聚合：技术团队或研究人员每日需要阅读大量技术博客、安全公告和论文预印本。WebLink Navigator 可将分散在数十个不同来源的链接汇总至统一仪表盘，按时间倒序呈现，大幅降低信息获取成本。

- 专题知识库构建：针对特定技术领域，如云原生架构、机器学习部署或区块链底层协议，用户可建立独立标签空间，将有价值的外部分析文章和案例研究集中收录，并附加个人批注与评分，形成可检索的专题知识库。

- 合规审计与来源追溯：企业内部合规或审计团队需要记录决策依据的外部引用来源。Navigator 的导入日志和元数据版本控制功能可完整保留链接收录时间、操作人和原始来源信息，满足内部审计追溯要求。

- 自动化监控与预警：结合健康检查功能，用户可对关键依赖的文档或公告链接设置监控频率，一旦目标页面发生变更或不可访问，系统将通过邮件或 Webhook 发送预警通知。

## 快速开始

以下指令适用于 Linux 及 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/navigator.git
cd navigator

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库与配置模板
python scripts/init_db.py
cp config/application.example.yml config/application.yml

# 执行开发服务器（默认监听 127.0.0.1:8080）
python app.py
```

访问 http://127.0.0.1:8080 即可进入 Web 管理界面，默认管理员账号为 admin，初始密码在首次启动时输出于终端日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 - 3.11 | 核心运行环境，3.12 暂未完成兼容性测试 |
| SQLite | 3.35.0 及以上 | 默认内嵌数据库，用于元数据存储与检索 |
| Redis | 6.2 及以上 | 可选，用于提升健康检查任务队列性能和缓存命中率 |
| Node.js | 18.17 及以上 | 仅前端构建时需要，生产环境若使用预编译资源可不安装 |
| Nginx | 1.22 及以上 | 生产环境反向代理与静态资源服务推荐使用 |
| supervisor | 4.2 及以上 | 生产环境进程守护工具，非强制但建议配置 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | docs/user-guide/ | 如何导入链接、配置标签、设置仪表盘视图和导出数据？ |
| 管理员指南 | docs/admin-guide/ | 如何配置健康检查周期、管理用户权限和进行数据库备份？ |
| 开发文档 | docs/developer-guide/ | API 接口规范、插件扩展机制和前端组件开发流程是什么？ |
| 部署手册 | docs/deployment/ | 如何将项目部署至生产服务器，配置 HTTPS 和负载均衡？ |

## 资源列表

- http://m.3g.fcful.cn/snews/980916.htm
- http://m.3g.fcful.cn/snews/8164.htm
- http://m.3g.fcful.cn/snews/8494709.htm
- http://m.3g.fcful.cn/snews/35350.htm
- http://m.3g.fcful.cn/snews/30334.htm
- http://m.3g.fcful.cn/snews/922395.htm
- http://m.3g.fcful.cn/snews/4214.htm
- http://m.3g.fcful.cn/snews/44260.htm
- http://m.3g.fcful.cn/snews/790596.htm
- http://m.3g.fcful.cn/snews/08348.htm
- http://m.3g.fcful.cn/snews/431401.htm
- http://m.3g.fcful.cn/snews/4759301.htm
- http://m.3g.fcful.cn/snews/445654.htm
- http://m.3g.fcful.cn/snews/371317.htm
- http://m.3g.fcful.cn/snews/4200.htm
- http://m.3g.fcful.cn/snews/718686.htm
- http://m.3g.fcful.cn/snews/9344211.htm
- http://m.3g.fcful.cn/snews/3997.htm
- http://m.3g.fcful.cn/snews/1746544.htm
- http://m.3g.fcful.cn/snews/452832.htm
- http://m.3g.fcful.cn/snews/47954.htm
- http://m.3g.fcful.cn/snews/918722.htm
- http://m.3g.fcful.cn/snews/2268207.htm
- http://m.3g.fcful.cn/snews/496210.htm
- http://m.3g.fcful.cn/snews/4658.htm
- http://m.3g.fcful.cn/snews/7004156.htm
- http://m.3g.fcful.cn/snews/3257412.htm
- http://m.3g.fcful.cn/snews/194247.htm
- http://m.3g.fcful.cn/snews/12584.htm
- http://m.3g.fcful.cn/snews/423655.htm
- http://m.3g.fcful.cn/snews/526589.htm
- http://m.3g.fcful.cn/snews/1547.htm
- http://m.3g.fcful.cn/snews/8902.htm
- http://m.3g.fcful.cn/snews/11691.htm
- http://m.3g.fcful.cn/snews/91055.htm
- http://m.3g.fcful.cn/snews/0134221.htm
- http://m.3g.fcful.cn/snews/2521046.htm
- http://m.3g.fcful.cn/snews/1501.htm
- http://m.3g.fcful.cn/snews/8540436.htm
- http://m.3g.fcful.cn/snews/710352.htm
- http://m.3g.fcful.cn/snews/416005.htm
- http://m.3g.fcful.cn/snews/3028907.htm
- http://m.3g.fcful.cn/snews/5763343.htm
- http://m.3g.fcful.cn/snews/6899.htm
- http://m.3g.fcful.cn/snews/9473466.htm
- http://m.3g.fcful.cn/snews/8826.htm
- http://m.3g.fcful.cn/snews/5833.htm
- http://m.3g.fcful.cn/snews/7970.htm
- http://m.3g.fcful.cn/snews/9682054.htm
- http://m.3g.fcful.cn/snews/4636.htm
- http://m.3g.fcful.cn/snews/956626.htm
- http://m.3g.fcful.cn/snews/03957.htm
- http://m.3g.fcful.cn/snews/62140.htm
- http://m.3g.fcful.cn/snews/23413.htm
- http://m.3g.fcful.cn/snews/33915.htm
- http://m.3g.fcful.cn/snews/9810043.htm
- http://m.3g.fcful.cn/snews/19690.htm
- http://m.3g.fcful.cn/snews/06487.htm
- http://m.3g.fcful.cn/snews/697818.htm
- http://m.3g.fcful.cn/snews/884935.htm
- http://m.3g.fcful.cn/snews/694447.htm
- http://m.3g.fcful.cn/snews/415369.htm
- http://m.3g.fcful.cn/snews/361540.htm
- http://m.3g.fcful.cn/snews/94303.htm
- http://m.3g.fcful.cn/snews/1753680.htm
- http://m.3g.fcful.cn/snews/014926.htm
- http://m.3g.fcful.cn/snews/62723.htm
- http://m.3g.fcful.cn/snews/43399.htm
- http://m.3g.fcful.cn/snews/30906.htm
- http://m.3g.fcful.cn/snews/6424515.htm
- http://m.3g.fcful.cn/snews/2965.htm
- http://m.3g.fcful.cn/snews/6282.htm
- http://m.3g.fcful.cn/snews/1626180.htm
- http://m.3g.fcful.cn/snews/66765.htm
- http://m.3g.fcful.cn/snews/7636343.htm
- http://m.3g.fcful.cn/snews/4135324.htm
- http://m.3g.fcful.cn/snews/201071.htm
- http://m.3g.fcful.cn/snews/7706520.htm
- http://m.3g.fcful.cn/snews/0175.htm
- http://m.3g.fcful.cn/snews/9243291.htm
- http://m.3g.fcful.cn/snews/2379267.htm
- http://m.3g.fcful.cn/snews/762942.htm
- http://m.3g.fcful.cn/snews/014828.htm
- http://m.3g.fcful.cn/snews/5268918.htm
- http://m.3g.fcful.cn/snews/463908.htm
- http://m.3g.fcful.cn/snews/557556.htm
- http://m.3g.fcful.cn/snews/5022784.htm
- http://m.3g.fcful.cn/snews/873447.htm
- http://m.3g.fcful.cn/snews/58671.htm
- http://m.3g.fcful.cn/snews/502960.htm
- http://m.3g.fcful.cn/snews/2248.htm
- http://m.3g.fcful.cn/snews/284868.htm
- http://m.3g.fcful.cn/snews/3369483.htm
- http://m.3g.fcful.cn/snews/88033.htm
- http://m.3g.fcful.cn/snews/1581.htm
- http://m.3g.fcful.cn/snews/8705.htm
- http://m.3g.fcful.cn/snews/5367618.htm
- http://m.3g.fcful.cn/snews/9087.htm
- http://m.3g.fcful.cn/snews/89231.htm
- http://m.3g.fcful.cn/snews/424237.htm
- http://m.3g.fcful.cn/snews/421386.htm
- http://m.3g.fcful.cn/snews/165337.htm
- http://m.3g.fcful.cn/snews/5226.htm
- http://m.3g.fcful.cn/snews/0321.htm
- http://m.3g.fcful.cn/snews/23255.htm
- http://m.3g.fcful.cn/snews/11801.htm
- http://m.3g.fcful.cn/snews/0410380.htm
- http://m.3g.fcful.cn/snews/7351748.htm
- http://m.3g.fcful.cn/snews/712063.htm
- http://m.3g.fcful.cn/snews/491104.htm
- http://m.3g.fcful.cn/snews/4549.htm
- http://m.3g.fcful.cn/snews/11193.htm
- http://m.3g.fcful.cn/snews/2474.htm
- http://m.3g.fcful.cn/snews/93357.htm
- http://m.3g.fcful.cn/snews/106101.htm
- http://m.3g.fcful.cn/snews/6170.htm
- http://m.3g.fcful.cn/snews/108062.htm
- http://m.3g.fcful.cn/snews/301296.htm
- http://m.3g.fcful.cn/snews/7760.htm
- http://m.3g.fcful.cn/snews/700940.htm
- http://m.3g.fcful.cn/snews/09190.htm
- http://m.3g.fcful.cn/snews/7288336.htm
- http://m.3g.fcful.cn/snews/19556.htm
- http://m.3g.fcful.cn/snews/5750.htm
- http://m.3g.fcful.cn/snews/67440.htm
- http://m.3g.fcful.cn/snews/7878.htm
- http://m.3g.fcful.cn/snews/2649230.htm
- http://m.3g.fcful.cn/snews/6414398.htm
- http://m.3g.fcful.cn/snews/15018.htm
- http://m.3g.fcful.cn/snews/1948.htm
- http://m.3g.fcful.cn/snews/01894.htm
- http://m.3g.fcful.cn/snews/3804441.htm
- http://m.3g.fcful.cn/snews/2718.htm
- http://m.3g.fcful.cn/snews/481708.htm
- http://m.3g.fcful.cn/snews/6525915.htm
- http://m.3g.fcful.cn/snews/9400964.htm
- http://m.3g.fcful.cn/snews/38591.htm
- http://m.3g.fcful.cn/snews/150748.htm
- http://m.3g.fcful.cn/snews/2861671.htm
- http://m.3g.fcful.cn/snews/7238734.htm
- http://m.3g.fcful.cn/snews/8892279.htm
- http://m.3g.fcful.cn/snews/618268.htm
- http://m.3g.fcful.cn/snews/70944.htm
- http://m.3g.fcful.cn/snews/48305.htm
- http://m.3g.fcful.cn/snews/4374758.htm
- http://m.3g.fcful.cn/snews/0211.htm
- http://m.3g.fcful.cn/snews/7090.htm
- http://m.3g.fcful.cn/snews/85599.htm
- http://m.3g.fcful.cn/snews/0495.htm
- http://m.3g.fcful.cn/snews/7630962.htm
- http://m.3g.fcful.cn/snews/0567.htm
- http://m.3g.fcful.cn/snews/07550.htm
- http://m.3g.fcful.cn/snews/8694.htm
- http://m.3g.fcful.cn/snews/2620.htm
- http://m.3g.fcful.cn/snews/3495766.htm
- http://m.3g.fcful.cn/snews/3100.htm
- http://m.3g.fcful.cn/snews/33670.htm
- http://m.3g.fcful.cn/snews/7876341.htm
- http://m.3g.fcful.cn/snews/074363.htm
- http://m.3g.fcful.cn/snews/2394.htm
- http://m.3g.fcful.cn/snews/0172612.htm
- http://m.3g.fcful.cn/snews/1140005.htm
- http://m.3g.fcful.cn/snews/455855.htm
- http://m.3g.fcful.cn/snews/4429593.htm
- http://m.3g.fcful.cn/snews/4346133.htm
- http://m.3g.fcful.cn/snews/259024.htm
- http://m.3g.fcful.cn/snews/7129.htm
- http://m.3g.fcful.cn/snews/5810.htm
- http://m.3g.fcful.cn/snews/1060.htm
- http://m.3g.fcful.cn/snews/1994500.htm
- http://m.3g.fcful.cn/snews/69969.htm
- http://m.3g.fcful.cn/snews/2823.htm
- http://m.3g.fcful.cn/snews/63134.htm
- http://m.3g.fcful.cn/snews/0744.htm
- http://m.3g.fcful.cn/snews/300238.htm
- http://m.3g.fcful.cn/snews/9319.htm
- http://m.3g.fcful.cn/snews/4007.htm
- http://m.3g.fcful.cn/snews/31748.htm
- http://m.3g.fcful.cn/snews/6903140.htm
- http://m.3g.fcful.cn/snews/151238.htm
- http://m.3g.fcful.cn/snews/14007.htm
- http://m.3g.fcful.cn/snews/54948.htm
- http://m.3g.fcful.cn/snews/5333.htm
- http://m.3g.fcful.cn/snews/4366351.htm
- http://m.3g.fcful.cn/snews/9887223.htm
- http://m.3g.fcful.cn/snews/1203250.htm
- http://m.3g.fcful.cn/snews/3934278.htm
- http://m.3g.fcful.cn/snews/35275.htm
- http://m.3g.fcful.cn/snews/6332.htm
- http://m.3g.fcful.cn/snews/627920.htm
- http://m.3g.fcful.cn/snews/33604.htm
- http://m.3g.fcful.cn/snews/7490.htm
- http://m.3g.fcful.cn/snews/1044.htm
- http://m.3g.fcful.cn/snews/18846.htm
- http://m.3g.fcful.cn/snews/71871.htm
- http://m.3g.fcful.cn/snews/48336.htm
- http://m.3g.fcful.cn/snews/409685.htm
- http://m.3g.fcful.cn/snews/5046.htm
- http://m.3g.fcful.cn/snews/6675065.htm
- http://m.3g.fcful.cn/snews/9016219.htm
- http://m.3g.fcful.cn/snews/4534.htm
- http://m.3g.fcful.cn/snews/6118756.htm
- http://m.3g.fcful.cn/snews/926446.htm
- http://m.3g.fcful.cn/snews/4543.htm
- http://m.3g.fcful.cn/snews/1816706.htm
- http://m.3g.fcful.cn/snews/5659106.htm
- http://m.3g.fcful.cn/snews/2882059.htm
- http://m.3g.fcful.cn/snews/939172.htm
- http://m.3g.fcful.cn/snews/3170922.htm
- http://m.3g.fcful.cn/snews/3306631.htm
- http://m.3g.fcful.cn/snews/11654.htm
- http://m.3g.fcful.cn/snews/1408230.htm
- http://m.3g.fcful.cn/snews/5190.htm
- http://m.3g.fcful.cn/snews/8293.htm
- http://m.3g.fcful.cn/snews/15477.htm
- http://m.3g.fcful.cn/snews/57404.htm
- http://m.3g.fcful.cn/snews/34744.htm
- http://m.3g.fcful.cn/snews/379912.htm
- http://m.3g.fcful.cn/snews/6056401.htm
- http://m.3g.fcful.cn/snews/56003.htm
- http://m.3g.fcful.cn/snews/5109.htm
- http://m.3g.fcful.cn/snews/2199444.htm
- http://m.3g.fcful.cn/snews/2158329.htm
- http://m.3g.fcful.cn/snews/523391.htm
- http://m.3g.fcful.cn/snews/326279.htm
- http://m.3g.fcful.cn/snews/5174.htm
- http://m.3g.fcful.cn/snews/3885939.htm
- http://m.3g.fcful.cn/snews/64488.htm
- http://m.3g.fcful.cn/snews/0365663.htm
- http://m.3g.fcful.cn/snews/4475.htm
- http://m.3g.fcful.cn/snews/5154671.htm
- http://m.3g.fcful.cn/snews/4263860.htm
- http://m.3g.fcful.cn/snews/5232594.htm
- http://m.3g.fcful.cn/snews/6321.htm
- http://m.3g.fcful.cn/snews/144489.htm
- http://m.3g.fcful.cn/snews/3028061.htm
- http://m.3g.fcful.cn/snews/1433637.htm
- http://m.3g.fcful.cn/snews/1650.htm
- http://m.3g.fcful.cn/snews/3920520.htm
- http://m.3g.fcful.cn/snews/3557.htm
- http://m.3g.fcful.cn/snews/4471124.htm
- http://m.3g.fcful.cn/snews/6299313.htm
- http://m.3g.fcful.cn/snews/95098.htm
- http://m.3g.fcful.cn/snews/9664.htm
- http://m.3g.fcful.cn/snews/3415.htm
- http://m.3g.fcful.cn/snews/5658071.htm
- http://m.3g.fcful.cn/snews/503682.htm
- http://m.3g.fcful.cn/snews/2892277.htm
- http://m.3g.fcful.cn/snews/1760040.htm
- http://m.3g.fcful.cn/snews/3467.htm

## 项目结构

```
navigator/
├── app/                                    # 核心应用模块
│   ├── api/                                # RESTful API 路由与控制器
│   │   ├── v1/                             # API v1 版本实现
│   │   │   ├── links.py                    # 链接资源 CRUD 端点
│   │   │   ├── tags.py                     # 标签管理端点
│   │   │   └── health.py                   # 健康检查与状态端点
│   │   └── __init__.py
│   ├── core/                               # 核心业务逻辑层
│   │   ├── crawler.py                      # 元数据提取与页面抓取引擎
│   │   ├── checker.py                      # 链接可用性异步检查器
│   │   ├── indexer.py                      # 倒排索引构建与检索核心
│   │   └── scheduler.py                    # 定时任务调度管理器
│   ├── models/                             # 数据模型与 ORM 映射
│   │   ├── link.py                         # 链接实体模型
│   │   ├── tag.py                          # 标签实体模型
│   │   └── user.py                         # 用户与权限模型
│   ├── services/                           # 外部服务集成层
│   │   ├── redis_client.py                 # Redis 连接与缓存服务
│   │   └── mail_service.py                 # 邮件通知服务封装
│   └── utils/                              # 通用工具函数库
│       ├── validators.py                   # URL 校验与格式化工具
│       └── converters.py                   # 数据格式转换器
├── config/                                 # 配置文件夹
│   ├── application.example.yml             # 主配置文件示例
│   ├── logging.yml                         # 日志级别与输出配置
│   └── scheduler.yml                       # 后台任务周期配置
├── frontend/                               # 前端资源目录
│   ├── src/                                # 源码目录
│   │   ├── pages/                          # 页面组件
│   │   └── components/                     # 通用 UI 组件
│   └── dist/                               # 生产构建输出目录
├── scripts/                                # 运维与开发辅助脚本
│   ├── init_db.py                          # 数据库初始化脚本
│   └── migrate.py                          # 数据库结构迁移工具
├── tests/                                  # 单元测试与集成测试
│   ├── unit/                               # 单元测试用例
│   └── integration/                        # 接口集成测试
├── docs/                                   # 项目文档
│   ├── user-guide/                         # 用户手册
│   └── developer-guide/                    # 开发文档
├── requirements.txt                        # Python 生产依赖列表
├── requirements-dev.txt                    # 开发环境额外依赖
├── Dockerfile                              # 容器化构建定义
├── docker-compose.yml                      # 本地开发服务编排
└── README.md                               # 项目说明文档
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并 clone 至本地开发环境。建议在 dev 分支基础上创建新的功能分支，分支命名遵循 feat/xxx 或 fix/xxx 格式。

2. 安装开发依赖并配置 pre-commit 钩子，确保代码风格符合 PEP 8 规范且通过 flake8 与 mypy 类型检查。运行 `make setup-dev` 可一键完成环境准备。

3. 编写或修改代码后，须补充对应的单元测试，确保测试覆盖率达到 80% 以上。使用 `pytest tests/` 执行全部测试用例。

4. 提交 Pull Request 前，请同步上游主分支的最新代码并解决冲突。PR 描述中需清晰说明变更目的、影响范围以及测试验证情况。

5. 文档类变更需同步更新 docs 目录下的对应手册，并确保 README 中的快速开始示例仍然可运行。

## 常见问题

Q: 导入大量链接后，Web 界面响应明显变慢，如何优化？

A: 首先检查是否启用了 Redis 缓存服务。若未配置 Redis，系统将使用内存缓存，数据量超过万级后性能会显著下降。建议按照部署文档配置 Redis 并调整缓存过期策略。此外，可在管理后台关闭实时全文索引，改为定时增量索引构建。

Q: 健康检查任务报告大量链接超时，但这些链接在浏览器中可正常访问。

A: 健康检查默认使用 requests 库的默认超时配置（连接超时 3 秒，读取超时 5 秒）。部分目标站点响应较慢或存在防火墙限流策略，会导致探测失败。请在 config/scheduler.yml 中调整 timeout 参数，或为特定域名配置白名单跳过检查。

Q: 如何从旧版本迁移数据至当前版本？

A: 项目提供了 migrate.py 脚本，支持从 v1.x 版本的 SQLite 数据库结构迁移至 v2.x。执行 `python scripts/migrate.py --source old_data.db --target current.db` 即可。迁移前请务必对原数据库文件进行完整备份。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
