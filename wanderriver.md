# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的结构化外链资源聚合系统。该项目不对原始内容做二次加工，仅提供统一的索引入口与分类导航，帮助用户从大量分散的移动端资讯页面中快速定位特定编号的文章。项目定位为技术资源的外链汇总站，适用于需要批量管理、检索和归档外部链接的运维场景。

## 功能概览

**批量链接导入** 支持一次性录入上千条外部链接，自动解析域名与路径结构。

**多维度筛选检索** 基于 URL 中的数字编号、日期特征或路径层级进行快速过滤。

**链接状态监测** 周期性探测每个外链的可访问性，标注异常链接便于人工复核。

**分类标签管理** 允许用户为每条链接添加自定义标签，实现按主题或项目维度分组。

**导出与备份** 支持将链接列表导出为 CSV、JSON 或纯文本格式，便于离线存档或迁移。

**访问统计看板** 展示链接被点击的次数、最近访问时间以及来源渠道分布。

**权限分级控制** 支持多用户环境下的只读、编辑和管理员三级权限设置。

**API 接口开放** 提供 RESTful API 供第三方工具批量拉取链接数据或提交新链接。

## 应用场景

技术文档归档整理 技术团队在撰写周报或项目总结时，需要引用大量外部参考文章。通过 WebLink Navigator 可以快速检索到此前收集的链接，并按编号或主题归类，显著提升文档编写的效率。

资讯监控与信息流聚合 内容运营人员需要跟踪特定领域的最新动态，每日从移动端资讯站点采集大量文章链接。本项目提供统一入口，支持按日期或编号范围筛选，帮助运营者快速浏览新增内容。

外部链接健康度巡检 运维工程师负责维护公司官网或知识库中的外链有效性。利用本项目的链接状态监测功能，可以定期扫描所有外链，及时发现 404 或超时异常，并生成报告供修复参考。

数据迁移前的链接梳理 在进行网站改版或 CMS 系统迁移时，需要完整梳理所有外部引用链接。本项目支持批量导出链接列表，方便迁移前做备份，迁移后做对比校验。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装依赖（使用 npm 或 yarn）
npm install

# 启动开发服务器
npm run dev

# 或使用 Docker 快速启动
docker-compose up -d
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >= 18.0.0 | 运行时环境，用于执行核心服务与构建工具链 |
| npm 或 yarn | >= 8.0.0 | 包管理器，用于安装项目依赖 |
| PostgreSQL | >= 14.0 | 主数据库，存储链接元数据与用户配置 |
| Redis | >= 6.2 | 缓存与会话存储，提升高频查询响应速度 |
| Nginx | >= 1.20 | 反向代理服务器，用于生产环境的负载均衡与静态资源分发 |
| Docker 与 Docker Compose | >= 20.10 | 容器化部署方案，简化环境配置（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide/ | 如何注册账号、导入链接、使用检索功能以及导出数据 |
| 运维指南 | /docs/ops-guide/ | 如何部署服务、配置数据库连接、设置定时任务与备份策略 |
| 开发者文档 | /docs/dev-guide/ | 如何二次开发、API 接口规范、代码结构与单元测试编写 |
| 设计文档 | /docs/design/ | 系统架构图、数据模型设计、权限模型与扩展性说明 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/9718355.htm
- http://m.blog.gqskj.cn/nnews/6742.htm
- http://m.blog.gqskj.cn/nnews/510207.htm
- http://m.blog.gqskj.cn/nnews/614887.htm
- http://m.blog.gqskj.cn/nnews/5982.htm
- http://m.blog.gqskj.cn/nnews/9779343.htm
- http://m.blog.gqskj.cn/nnews/5946601.htm
- http://m.blog.gqskj.cn/nnews/3686757.htm
- http://m.blog.gqskj.cn/nnews/56369.htm
- http://m.blog.gqskj.cn/nnews/7139023.htm
- http://m.blog.gqskj.cn/nnews/9202368.htm
- http://m.blog.gqskj.cn/nnews/0362680.htm
- http://m.blog.gqskj.cn/nnews/047187.htm
- http://m.blog.gqskj.cn/nnews/4608666.htm
- http://m.blog.gqskj.cn/nnews/9372112.htm
- http://m.blog.gqskj.cn/nnews/7177706.htm
- http://m.blog.gqskj.cn/nnews/55243.htm
- http://m.blog.gqskj.cn/nnews/29550.htm
- http://m.blog.gqskj.cn/nnews/7999.htm
- http://m.blog.gqskj.cn/nnews/942545.htm
- http://m.blog.gqskj.cn/nnews/2971.htm
- http://m.blog.gqskj.cn/nnews/8100457.htm
- http://m.blog.gqskj.cn/nnews/5757.htm
- http://m.blog.gqskj.cn/nnews/6681.htm
- http://m.blog.gqskj.cn/nnews/5872182.htm
- http://m.blog.gqskj.cn/nnews/772496.htm
- http://m.blog.gqskj.cn/nnews/4643.htm
- http://m.blog.gqskj.cn/nnews/74187.htm
- http://m.blog.gqskj.cn/nnews/6998070.htm
- http://m.blog.gqskj.cn/nnews/2271538.htm
- http://m.blog.gqskj.cn/nnews/67849.htm
- http://m.blog.gqskj.cn/nnews/99061.htm
- http://m.blog.gqskj.cn/nnews/8747.htm
- http://m.blog.gqskj.cn/nnews/7851826.htm
- http://m.blog.gqskj.cn/nnews/0491730.htm
- http://m.blog.gqskj.cn/nnews/2270.htm
- http://m.blog.gqskj.cn/nnews/0885.htm
- http://m.blog.gqskj.cn/nnews/9865854.htm
- http://m.blog.gqskj.cn/nnews/91425.htm
- http://m.blog.gqskj.cn/nnews/8955.htm
- http://m.blog.gqskj.cn/nnews/4723525.htm
- http://m.blog.gqskj.cn/nnews/5517.htm
- http://m.blog.gqskj.cn/nnews/835103.htm
- http://m.blog.gqskj.cn/nnews/2059762.htm
- http://m.blog.gqskj.cn/nnews/3799645.htm
- http://m.blog.gqskj.cn/nnews/805091.htm
- http://m.blog.gqskj.cn/nnews/0377150.htm
- http://m.blog.gqskj.cn/nnews/2414.htm
- http://m.blog.gqskj.cn/nnews/678819.htm
- http://m.blog.gqskj.cn/nnews/743518.htm
- http://m.blog.gqskj.cn/nnews/525221.htm
- http://m.blog.gqskj.cn/nnews/9274239.htm
- http://m.blog.gqskj.cn/nnews/6361.htm
- http://m.blog.gqskj.cn/nnews/2316.htm
- http://m.blog.gqskj.cn/nnews/388062.htm
- http://m.blog.gqskj.cn/nnews/7783476.htm
- http://m.blog.gqskj.cn/nnews/717647.htm
- http://m.blog.gqskj.cn/nnews/4789.htm
- http://m.blog.gqskj.cn/nnews/4258.htm
- http://m.blog.gqskj.cn/nnews/51575.htm
- http://m.blog.gqskj.cn/nnews/28175.htm
- http://m.blog.gqskj.cn/nnews/423751.htm
- http://m.blog.gqskj.cn/nnews/9915923.htm
- http://m.blog.gqskj.cn/nnews/0112.htm
- http://m.blog.gqskj.cn/nnews/00512.htm
- http://m.blog.gqskj.cn/nnews/1101.htm
- http://m.blog.gqskj.cn/nnews/5474326.htm
- http://m.blog.gqskj.cn/nnews/5764908.htm
- http://m.blog.gqskj.cn/nnews/6628028.htm
- http://m.blog.gqskj.cn/nnews/1005.htm
- http://m.blog.gqskj.cn/nnews/51754.htm
- http://m.blog.gqskj.cn/nnews/41471.htm
- http://m.blog.gqskj.cn/nnews/9035.htm
- http://m.blog.gqskj.cn/nnews/4422760.htm
- http://m.blog.gqskj.cn/nnews/49666.htm
- http://m.blog.gqskj.cn/nnews/31980.htm
- http://m.blog.gqskj.cn/nnews/430155.htm
- http://m.blog.gqskj.cn/nnews/3330.htm
- http://m.blog.gqskj.cn/nnews/09028.htm
- http://m.blog.gqskj.cn/nnews/4495746.htm
- http://m.blog.gqskj.cn/nnews/622870.htm
- http://m.blog.gqskj.cn/nnews/124317.htm
- http://m.blog.gqskj.cn/nnews/0587.htm
- http://m.blog.gqskj.cn/nnews/4423436.htm
- http://m.blog.gqskj.cn/nnews/578609.htm
- http://m.blog.gqskj.cn/nnews/083185.htm
- http://m.blog.gqskj.cn/nnews/9845355.htm
- http://m.blog.gqskj.cn/nnews/3928792.htm
- http://m.blog.gqskj.cn/nnews/904508.htm
- http://m.blog.gqskj.cn/nnews/532346.htm
- http://m.blog.gqskj.cn/nnews/3627.htm
- http://m.blog.gqskj.cn/nnews/8362096.htm
- http://m.blog.gqskj.cn/nnews/176185.htm
- http://m.blog.gqskj.cn/nnews/0894941.htm
- http://m.blog.gqskj.cn/nnews/72521.htm
- http://m.blog.gqskj.cn/nnews/1441620.htm
- http://m.blog.gqskj.cn/nnews/2173119.htm
- http://m.blog.gqskj.cn/nnews/2367.htm
- http://m.blog.gqskj.cn/nnews/629924.htm
- http://m.blog.gqskj.cn/nnews/98237.htm
- http://m.blog.gqskj.cn/nnews/963732.htm
- http://m.blog.gqskj.cn/nnews/454689.htm
- http://m.blog.gqskj.cn/nnews/023639.htm
- http://m.blog.gqskj.cn/nnews/3065553.htm
- http://m.blog.gqskj.cn/nnews/0694409.htm
- http://m.blog.gqskj.cn/nnews/27164.htm
- http://m.blog.gqskj.cn/nnews/365694.htm
- http://m.blog.gqskj.cn/nnews/023342.htm
- http://m.blog.gqskj.cn/nnews/449592.htm
- http://m.blog.gqskj.cn/nnews/617396.htm
- http://m.blog.gqskj.cn/nnews/44199.htm
- http://m.blog.gqskj.cn/nnews/179358.htm
- http://m.blog.gqskj.cn/nnews/8330962.htm
- http://m.blog.gqskj.cn/nnews/4506392.htm
- http://m.blog.gqskj.cn/nnews/4399.htm
- http://m.blog.gqskj.cn/nnews/3384272.htm
- http://m.blog.gqskj.cn/nnews/9901.htm
- http://m.blog.gqskj.cn/nnews/75195.htm
- http://m.blog.gqskj.cn/nnews/549475.htm
- http://m.blog.gqskj.cn/nnews/740996.htm
- http://m.blog.gqskj.cn/nnews/5473563.htm
- http://m.blog.gqskj.cn/nnews/6162.htm
- http://m.blog.gqskj.cn/nnews/321113.htm
- http://m.blog.gqskj.cn/nnews/021798.htm
- http://m.blog.gqskj.cn/nnews/15716.htm
- http://m.blog.gqskj.cn/nnews/87766.htm
- http://m.blog.gqskj.cn/nnews/7795660.htm
- http://m.blog.gqskj.cn/nnews/515213.htm
- http://m.blog.gqskj.cn/nnews/8810500.htm
- http://m.blog.gqskj.cn/nnews/0669250.htm
- http://m.blog.gqskj.cn/nnews/687783.htm
- http://m.blog.gqskj.cn/nnews/075890.htm
- http://m.blog.gqskj.cn/nnews/3488.htm
- http://m.blog.gqskj.cn/nnews/938839.htm
- http://m.blog.gqskj.cn/nnews/6694130.htm
- http://m.blog.gqskj.cn/nnews/4313677.htm
- http://m.blog.gqskj.cn/nnews/493685.htm
- http://m.blog.gqskj.cn/nnews/75154.htm
- http://m.blog.gqskj.cn/nnews/5270750.htm
- http://m.blog.gqskj.cn/nnews/67241.htm
- http://m.blog.gqskj.cn/nnews/1358.htm
- http://m.blog.gqskj.cn/nnews/960428.htm
- http://m.blog.gqskj.cn/nnews/8693.htm
- http://m.blog.gqskj.cn/nnews/4977441.htm
- http://m.blog.gqskj.cn/nnews/741799.htm
- http://m.blog.gqskj.cn/nnews/5937.htm
- http://m.blog.gqskj.cn/nnews/3818626.htm
- http://m.blog.gqskj.cn/nnews/9914396.htm
- http://m.blog.gqskj.cn/nnews/288885.htm
- http://m.blog.gqskj.cn/nnews/4158246.htm
- http://m.blog.gqskj.cn/nnews/1597.htm
- http://m.blog.gqskj.cn/nnews/7995.htm
- http://m.blog.gqskj.cn/nnews/5362.htm
- http://m.blog.gqskj.cn/nnews/0662481.htm
- http://m.blog.gqskj.cn/nnews/9604.htm
- http://m.blog.gqskj.cn/nnews/83980.htm
- http://m.blog.gqskj.cn/nnews/622807.htm
- http://m.blog.gqskj.cn/nnews/553062.htm
- http://m.blog.gqskj.cn/nnews/383419.htm
- http://m.blog.gqskj.cn/nnews/282563.htm
- http://m.blog.gqskj.cn/nnews/2225013.htm
- http://m.blog.gqskj.cn/nnews/614581.htm
- http://m.blog.gqskj.cn/nnews/398042.htm
- http://m.blog.gqskj.cn/nnews/1723065.htm
- http://m.blog.gqskj.cn/nnews/82295.htm
- http://m.blog.gqskj.cn/nnews/0415163.htm
- http://m.blog.gqskj.cn/nnews/75285.htm
- http://m.blog.gqskj.cn/nnews/1378.htm
- http://m.blog.gqskj.cn/nnews/073091.htm
- http://m.blog.gqskj.cn/nnews/38109.htm
- http://m.blog.gqskj.cn/nnews/96946.htm
- http://m.blog.gqskj.cn/nnews/108255.htm
- http://m.blog.gqskj.cn/nnews/2367451.htm
- http://m.blog.gqskj.cn/nnews/10875.htm
- http://m.blog.gqskj.cn/nnews/9388.htm
- http://m.blog.gqskj.cn/nnews/404224.htm
- http://m.blog.gqskj.cn/nnews/832235.htm
- http://m.blog.gqskj.cn/nnews/4612909.htm
- http://m.blog.gqskj.cn/nnews/6649915.htm
- http://m.blog.gqskj.cn/nnews/450832.htm
- http://m.blog.gqskj.cn/nnews/9597.htm
- http://m.blog.gqskj.cn/nnews/550246.htm
- http://m.blog.gqskj.cn/nnews/88726.htm
- http://m.blog.gqskj.cn/nnews/6088.htm
- http://m.blog.gqskj.cn/nnews/0235.htm
- http://m.blog.gqskj.cn/nnews/3678414.htm
- http://m.blog.gqskj.cn/nnews/400920.htm
- http://m.blog.gqskj.cn/nnews/4059268.htm
- http://m.blog.gqskj.cn/nnews/2969649.htm
- http://m.blog.gqskj.cn/nnews/2509777.htm
- http://m.blog.gqskj.cn/nnews/7880.htm
- http://m.blog.gqskj.cn/nnews/1790.htm
- http://m.blog.gqskj.cn/nnews/9249.htm
- http://m.blog.gqskj.cn/nnews/878262.htm
- http://m.blog.gqskj.cn/nnews/3795300.htm
- http://m.blog.gqskj.cn/nnews/5547633.htm
- http://m.blog.gqskj.cn/nnews/47047.htm
- http://m.blog.gqskj.cn/nnews/2014916.htm
- http://m.blog.gqskj.cn/nnews/44086.htm
- http://m.blog.gqskj.cn/nnews/232078.htm
- http://m.blog.gqskj.cn/nnews/40664.htm
- http://m.blog.gqskj.cn/nnews/7978324.htm
- http://m.blog.gqskj.cn/nnews/194330.htm
- http://m.blog.gqskj.cn/nnews/751991.htm
- http://m.blog.gqskj.cn/nnews/1082613.htm
- http://m.blog.gqskj.cn/nnews/5912548.htm
- http://m.blog.gqskj.cn/nnews/83330.htm
- http://m.blog.gqskj.cn/nnews/3010.htm
- http://m.blog.gqskj.cn/nnews/82495.htm
- http://m.blog.gqskj.cn/nnews/72298.htm
- http://m.blog.gqskj.cn/nnews/921851.htm
- http://m.blog.gqskj.cn/nnews/7943.htm
- http://m.blog.gqskj.cn/nnews/3030571.htm
- http://m.blog.gqskj.cn/nnews/9619.htm
- http://m.blog.gqskj.cn/nnews/178259.htm
- http://m.blog.gqskj.cn/nnews/48117.htm
- http://m.blog.gqskj.cn/nnews/659093.htm
- http://m.blog.gqskj.cn/nnews/89420.htm
- http://m.blog.gqskj.cn/nnews/832321.htm
- http://m.blog.gqskj.cn/nnews/2353559.htm
- http://m.blog.gqskj.cn/nnews/9852.htm
- http://m.blog.gqskj.cn/nnews/272365.htm
- http://m.blog.gqskj.cn/nnews/9317307.htm
- http://m.blog.gqskj.cn/nnews/959501.htm
- http://m.blog.gqskj.cn/nnews/9624758.htm
- http://m.blog.gqskj.cn/nnews/44765.htm
- http://m.blog.gqskj.cn/nnews/627941.htm
- http://m.blog.gqskj.cn/nnews/3422796.htm
- http://m.blog.gqskj.cn/nnews/95215.htm
- http://m.blog.gqskj.cn/nnews/4026.htm
- http://m.blog.gqskj.cn/nnews/514738.htm
- http://m.blog.gqskj.cn/nnews/69808.htm
- http://m.blog.gqskj.cn/nnews/601772.htm
- http://m.blog.gqskj.cn/nnews/4107009.htm
- http://m.blog.gqskj.cn/nnews/62780.htm
- http://m.blog.gqskj.cn/nnews/15376.htm
- http://m.blog.gqskj.cn/nnews/4189.htm
- http://m.blog.gqskj.cn/nnews/0448920.htm
- http://m.blog.gqskj.cn/nnews/5504485.htm
- http://m.blog.gqskj.cn/nnews/8696.htm
- http://m.blog.gqskj.cn/nnews/42933.htm
- http://m.blog.gqskj.cn/nnews/81804.htm
- http://m.blog.gqskj.cn/nnews/0045872.htm
- http://m.blog.gqskj.cn/nnews/25803.htm
- http://m.blog.gqskj.cn/nnews/9434628.htm
- http://m.blog.gqskj.cn/nnews/68823.htm
- http://m.blog.gqskj.cn/nnews/503157.htm
- http://m.blog.gqskj.cn/nnews/2688956.htm
- http://m.blog.gqskj.cn/nnews/4271.htm
- http://m.blog.gqskj.cn/nnews/50714.htm

## 项目结构

```
weblink-navigator/
├── src/
│   ├── api/                     # RESTful API 路由与控制器
│   │   ├── v1/                  # API 版本 v1 实现
│   │   │   ├── links.js         # 链接增删改查接口
│   │   │   ├── tags.js          # 标签管理接口
│   │   │   └── stats.js         # 统计信息接口
│   │   └── middleware/          # 鉴权、日志、限流中间件
│   ├── core/                    # 核心业务逻辑层
│   │   ├── link-service.js      # 链接处理与状态机
│   │   ├── crawler.js           # 外链状态探测引擎
│   │   └── cache-manager.js     # Redis 缓存封装
│   ├── models/                  # 数据库模型定义 (ORM)
│   │   ├── Link.js              # 链接实体模型
│   │   ├── User.js              # 用户实体模型
│   │   └── Tag.js               # 标签实体模型
│   ├── utils/                   # 通用工具函数
│   │   ├── validator.js         # URL 格式校验
│   │   ├── logger.js            # 日志记录器
│   │   └── exporter.js          # CSV/JSON 导出工具
│   └── app.js                   # 应用主入口
├── config/                      # 环境配置文件
│   ├── default.json             # 默认配置
│   ├── production.json          # 生产环境配置
│   └── development.json         # 开发环境配置
├── scripts/                     # 运维与工具脚本
│   ├── migrate-db.js            # 数据库迁移脚本
│   ├── seed-links.js            # 初始链接导入脚本
│   └── health-check.js          # 定时健康检查任务
├── tests/                       # 单元测试与集成测试
│   ├── unit/                    # 单元测试用例
│   └── integration/             # API 集成测试
├── docs/                        # 项目文档 (参考文档导航章节)
├── docker-compose.yml           # Docker 编排文件
├── Dockerfile                   # 容器构建文件
├── package.json                 # npm 依赖清单
├── .env.example                 # 环境变量示例
└── README.md                    # 项目说明文档 (本文件)
```

## 贡献指南

提交 Issue 报告缺陷 访问 GitHub Issues 页面，使用提供的模板详细描述遇到的问题，包括复现步骤、预期结果与实际结果。对于链接探测异常，请附上目标 URL 和发生时间。

发起 Pull Request 修改代码 从 main 分支创建新的功能分支，遵循项目的代码风格与 ESLint 规则。提交前请确保所有单元测试通过，并针对新增功能补充对应的测试用例。

完善文档与示例 鼓励改进文档中的错误描述、补充缺失的 API 示例或增加新的应用场景说明。文档修改可直接在 docs 目录下编辑 Markdown 文件后提交 PR。

参与讨论与需求反馈 在 GitHub Discussions 板块参与技术交流，分享使用心得或提出新功能建议。项目维护者会定期回复并评估需求的可行性。

本地构建与自测 克隆代码后运行 npm install 安装依赖，使用 npm run test 执行测试套件，确保本地环境通过全部测试后再提交变更。

## 常见问题

Q: 系统能处理多少条链接？是否有性能瓶颈？
A: 系统设计支持十万级链接的索引与检索。PostgreSQL 数据库配合 Redis 缓存，在默认配置下可稳定处理每秒约 500 次查询请求。若链接数量超过十万，建议启用分页机制并配置读写分离。

Q: 链接状态探测会影响目标网站吗？
A: 探测引擎默认采用 HEAD 请求，仅获取响应头信息，不会下载完整页面内容。探测间隔默认设为 24 小时，且每个目标域名有并发限制，避免对源站造成压力。用户可在配置文件中调整探测频率与并发数。

Q: 如何从旧系统迁移数据到 WebLink Navigator？
A: 项目提供了导入脚本 scripts/seed-links.js，支持 CSV 和 JSON 格式。用户只需将旧系统的链接列表按指定字段（url, tags, created_at）整理成 JSON 数组，然后运行 npm run seed -- --file=data.json 即可完成导入。导入前建议先备份数据库。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:47
