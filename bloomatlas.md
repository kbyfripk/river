# WebLink Navigator

WebLink Navigator 是一个面向技术研究、信息检索与内容聚合场景的高质量外链导航系统。项目定位于将分散在互联网各处的技术文章、新闻资讯、数据报告与行业动态通过统一的索引机制进行汇聚、分类与快速访问，帮助开发者、技术决策者与信息分析师在信息过载的环境中高效定位高价值内容。

本项目不提供内容存储，仅提供结构化链接索引与元数据增强服务，确保原始资源的所有权与来源清晰可溯。当前批次覆盖第 191/240 批，共计 250 个经过筛选的外部资源链接，涉及技术实践、行业观察、数据分析等多个维度。

## 功能概览

**批量链接聚合索引**：支持一次性导入数千条外部链接，自动生成带时间戳与批次标记的索引记录，便于回溯与增量更新。

**多维度分类标注**：根据 URL 路径模式、来源域名与内容特征自动或手动为每条链接附加分类标签，支持技术栈、行业领域、内容类型等维度。

**快速检索与过滤**：基于关键词、批次号、来源域名、收录时间等多条件组合过滤，在海量链接中秒级定位目标资源。

**访问状态健康检查**：定期对已收录链接进行 HTTP 状态码探测，自动标记失效、重定向或异常链接，保证索引库的鲜活度。

**外部资源预览嵌入**：对于支持标准 OEmbed 或 Open Graph 协议的页面，自动提取标题、描述与缩略图，在导航界面中生成预览卡片。

**导入导出互操作**：支持 CSV、JSON、Markdown 表格等多种格式的链接数据导入导出，便于与其他工具链（如 Notion、Airtable、静态站点生成器）集成。

**访问热度统计**：记录每条链接在本系统内的点击次数与最近访问时间，辅助判断内容热度与用户关注趋势。

## 应用场景

**技术团队内部知识库外链管理**：技术团队在日常调研中积累大量外部分档与博客链接，使用 WebLink Navigator 可统一归档、分类并共享给团队成员，避免重复查找与信息孤岛。

**开源项目文档的参考资料索引**：开源项目的 README 或文档中需引用大量外部规范、论文或工具链接，通过本系统生成结构化的资源列表，保证引用格式统一且可批量更新。

**行业周报或月刊的素材采集**：内容编辑或社区运营人员定期收集行业动态与技术文章，利用本系统的批次管理功能，可快速整理出当期的链接清单，并导出为 Markdown 或 HTML 格式直接发布。

**个人技术阅读工作流的中转站**：开发者每天浏览数十篇技术文章，可将有价值的链接即时存入系统，后续通过标签与检索功能进行深度阅读或整理成知识图谱。

**数据驱动的内容质量评估**：通过访问热度统计与健康检查，分析哪些外部资源持续受到关注，哪些链接已失效，从而优化内容推荐策略或更新文档引用。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebLink Navigator 服务。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/weblink-navigator.git
cd weblink-navigator

# 安装项目依赖（使用 npm 或 yarn）
npm install

# 执行数据库初始化与种子数据加载
npm run db:init

# 启动开发服务器，默认监听端口 3000
npm run dev
```

启动成功后，访问 http://localhost:3000 即可进入导航面板。首次启动会自动创建管理员账户，默认用户名与密码请查看 `.env.example` 文件中的说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装依赖与执行脚本 |
| PostgreSQL | >= 14.0 | 主数据库，存储链接索引、用户与元数据 |
| Redis | >= 6.0 | 缓存与会话存储，用于提升检索性能与速率控制 |
| TypeScript | >= 5.0 | 开发依赖，项目使用 TypeScript 编写，编译时需要 |
| PM2 | >= 5.0（生产环境可选） | 进程守护工具，用于生产环境的服务持久化运行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `docs/getting-started.md` | 如何快速部署、首次配置与登录系统？有哪些默认设置需要修改？ |
| 链接管理 | `docs/link-management.md` | 如何添加、编辑、删除链接？如何批量导入导出？分类标签如何自定义？ |
| 系统运维 | `docs/operations.md` | 如何执行健康检查？如何备份数据库？如何升级版本？日志在哪里查看？ |
| 集成扩展 | `docs/integration.md` | 如何通过 REST API 或 Webhook 与其他系统集成？是否支持 SSO 或 LDAP？ |

## 资源列表

- http://m.wap.gqskj.cn/snews/9657.htm
- http://m.wap.gqskj.cn/snews/49026.htm
- http://m.wap.gqskj.cn/snews/1658.htm
- http://m.wap.gqskj.cn/snews/29005.htm
- http://m.wap.gqskj.cn/snews/167873.htm
- http://m.wap.gqskj.cn/snews/2267.htm
- http://m.wap.gqskj.cn/snews/3752712.htm
- http://m.wap.gqskj.cn/snews/7470026.htm
- http://m.wap.gqskj.cn/snews/66436.htm
- http://m.wap.gqskj.cn/snews/273930.htm
- http://m.wap.gqskj.cn/snews/818470.htm
- http://m.wap.gqskj.cn/snews/274540.htm
- http://m.wap.gqskj.cn/snews/9162.htm
- http://m.wap.gqskj.cn/snews/0859907.htm
- http://m.wap.gqskj.cn/snews/6191622.htm
- http://m.wap.gqskj.cn/snews/175197.htm
- http://m.wap.gqskj.cn/snews/61572.htm
- http://m.wap.gqskj.cn/snews/55592.htm
- http://m.wap.gqskj.cn/snews/789973.htm
- http://m.wap.gqskj.cn/snews/953793.htm
- http://m.wap.gqskj.cn/snews/9274171.htm
- http://m.wap.gqskj.cn/snews/03917.htm
- http://m.wap.gqskj.cn/snews/1734.htm
- http://m.wap.gqskj.cn/snews/34184.htm
- http://m.wap.gqskj.cn/snews/8174.htm
- http://m.wap.gqskj.cn/snews/78970.htm
- http://m.wap.gqskj.cn/snews/534859.htm
- http://m.wap.gqskj.cn/snews/631233.htm
- http://m.wap.gqskj.cn/snews/93469.htm
- http://m.wap.gqskj.cn/snews/787857.htm
- http://m.wap.gqskj.cn/snews/416545.htm
- http://m.wap.gqskj.cn/snews/80953.htm
- http://m.wap.gqskj.cn/snews/61669.htm
- http://m.wap.gqskj.cn/snews/117447.htm
- http://m.wap.gqskj.cn/snews/34142.htm
- http://m.wap.gqskj.cn/snews/4193.htm
- http://m.wap.gqskj.cn/snews/4446471.htm
- http://m.wap.gqskj.cn/snews/98758.htm
- http://m.wap.gqskj.cn/snews/4639.htm
- http://m.wap.gqskj.cn/snews/16367.htm
- http://m.wap.gqskj.cn/snews/20879.htm
- http://m.wap.gqskj.cn/snews/9258475.htm
- http://m.wap.gqskj.cn/snews/86067.htm
- http://m.wap.gqskj.cn/snews/6810.htm
- http://m.wap.gqskj.cn/snews/8243.htm
- http://m.wap.gqskj.cn/snews/9669.htm
- http://m.wap.gqskj.cn/snews/68293.htm
- http://m.wap.gqskj.cn/snews/2210.htm
- http://m.wap.gqskj.cn/snews/7436.htm
- http://m.wap.gqskj.cn/snews/448220.htm
- http://m.wap.gqskj.cn/snews/0068.htm
- http://m.wap.gqskj.cn/snews/68849.htm
- http://m.wap.gqskj.cn/snews/39652.htm
- http://m.wap.gqskj.cn/snews/7540609.htm
- http://m.wap.gqskj.cn/snews/1266.htm
- http://m.wap.gqskj.cn/snews/11182.htm
- http://m.wap.gqskj.cn/snews/9158450.htm
- http://m.wap.gqskj.cn/snews/8415574.htm
- http://m.wap.gqskj.cn/snews/73644.htm
- http://m.wap.gqskj.cn/snews/9943.htm
- http://m.wap.gqskj.cn/snews/699565.htm
- http://m.wap.gqskj.cn/snews/5855.htm
- http://m.wap.gqskj.cn/snews/4361147.htm
- http://m.wap.gqskj.cn/snews/59049.htm
- http://m.wap.gqskj.cn/snews/13975.htm
- http://m.wap.gqskj.cn/snews/3731.htm
- http://m.wap.gqskj.cn/snews/5561.htm
- http://m.wap.gqskj.cn/snews/0148695.htm
- http://m.wap.gqskj.cn/snews/115837.htm
- http://m.wap.gqskj.cn/snews/83442.htm
- http://m.wap.gqskj.cn/snews/442808.htm
- http://m.wap.gqskj.cn/snews/71351.htm
- http://m.wap.gqskj.cn/snews/0786936.htm
- http://m.wap.gqskj.cn/snews/0813.htm
- http://m.wap.gqskj.cn/snews/1534629.htm
- http://m.wap.gqskj.cn/snews/8578496.htm
- http://m.wap.gqskj.cn/snews/1682583.htm
- http://m.wap.gqskj.cn/snews/50898.htm
- http://m.wap.gqskj.cn/snews/444171.htm
- http://m.wap.gqskj.cn/snews/0711.htm
- http://m.wap.gqskj.cn/snews/8397239.htm
- http://m.wap.gqskj.cn/snews/296147.htm
- http://m.wap.gqskj.cn/snews/6757638.htm
- http://m.wap.gqskj.cn/snews/1127400.htm
- http://m.wap.gqskj.cn/snews/4066.htm
- http://m.wap.gqskj.cn/snews/846497.htm
- http://m.wap.gqskj.cn/snews/5508.htm
- http://m.wap.gqskj.cn/snews/8629306.htm
- http://m.wap.gqskj.cn/snews/15720.htm
- http://m.wap.gqskj.cn/snews/8272.htm
- http://m.wap.gqskj.cn/snews/356299.htm
- http://m.wap.gqskj.cn/snews/444999.htm
- http://m.wap.gqskj.cn/snews/38858.htm
- http://m.wap.gqskj.cn/snews/8339.htm
- http://m.wap.gqskj.cn/snews/89436.htm
- http://m.wap.gqskj.cn/snews/3656726.htm
- http://m.wap.gqskj.cn/snews/535143.htm
- http://m.wap.gqskj.cn/snews/2103.htm
- http://m.wap.gqskj.cn/snews/47599.htm
- http://m.wap.gqskj.cn/snews/9706018.htm
- http://m.wap.gqskj.cn/snews/5332.htm
- http://m.wap.gqskj.cn/snews/7692.htm
- http://m.wap.gqskj.cn/snews/597772.htm
- http://m.wap.gqskj.cn/snews/81716.htm
- http://m.wap.gqskj.cn/snews/288995.htm
- http://m.wap.gqskj.cn/snews/328744.htm
- http://m.wap.gqskj.cn/snews/85823.htm
- http://m.wap.gqskj.cn/snews/23304.htm
- http://m.wap.gqskj.cn/snews/2462.htm
- http://m.wap.gqskj.cn/snews/13851.htm
- http://m.wap.gqskj.cn/snews/64406.htm
- http://m.wap.gqskj.cn/snews/23752.htm
- http://m.wap.gqskj.cn/snews/80009.htm
- http://m.wap.gqskj.cn/snews/474616.htm
- http://m.wap.gqskj.cn/snews/3150.htm
- http://m.wap.gqskj.cn/snews/2984457.htm
- http://m.wap.gqskj.cn/snews/93140.htm
- http://m.wap.gqskj.cn/snews/897082.htm
- http://m.wap.gqskj.cn/snews/288544.htm
- http://m.wap.gqskj.cn/snews/267152.htm
- http://m.wap.gqskj.cn/snews/0544634.htm
- http://m.wap.gqskj.cn/snews/7466212.htm
- http://m.wap.gqskj.cn/snews/7785059.htm
- http://m.wap.gqskj.cn/snews/1792892.htm
- http://m.wap.gqskj.cn/snews/5358.htm
- http://m.wap.gqskj.cn/snews/322785.htm
- http://m.wap.gqskj.cn/snews/48770.htm
- http://m.wap.gqskj.cn/snews/1706.htm
- http://m.wap.gqskj.cn/snews/88904.htm
- http://m.wap.gqskj.cn/snews/995601.htm
- http://m.wap.gqskj.cn/snews/85574.htm
- http://m.wap.gqskj.cn/snews/1927249.htm
- http://m.wap.gqskj.cn/snews/44077.htm
- http://m.wap.gqskj.cn/snews/4706.htm
- http://m.wap.gqskj.cn/snews/84815.htm
- http://m.wap.gqskj.cn/snews/780475.htm
- http://m.wap.gqskj.cn/snews/1905.htm
- http://m.wap.gqskj.cn/snews/6648889.htm
- http://m.wap.gqskj.cn/snews/78423.htm
- http://m.wap.gqskj.cn/snews/2988.htm
- http://m.wap.gqskj.cn/snews/38854.htm
- http://m.wap.gqskj.cn/snews/9461.htm
- http://m.wap.gqskj.cn/snews/8948.htm
- http://m.wap.gqskj.cn/snews/324342.htm
- http://m.wap.gqskj.cn/snews/100314.htm
- http://m.wap.gqskj.cn/snews/011129.htm
- http://m.wap.gqskj.cn/snews/95205.htm
- http://m.wap.gqskj.cn/snews/81307.htm
- http://m.wap.gqskj.cn/snews/8912433.htm
- http://m.wap.gqskj.cn/snews/697314.htm
- http://m.wap.gqskj.cn/snews/0524270.htm
- http://m.wap.gqskj.cn/snews/32667.htm
- http://m.wap.gqskj.cn/snews/141843.htm
- http://m.wap.gqskj.cn/snews/5818.htm
- http://m.wap.gqskj.cn/snews/538816.htm
- http://m.wap.gqskj.cn/snews/48324.htm
- http://m.wap.gqskj.cn/snews/6958.htm
- http://m.wap.gqskj.cn/snews/80079.htm
- http://m.wap.gqskj.cn/snews/825388.htm
- http://m.wap.gqskj.cn/snews/4808539.htm
- http://m.wap.gqskj.cn/snews/092319.htm
- http://m.wap.gqskj.cn/snews/1022404.htm
- http://m.wap.gqskj.cn/snews/8780372.htm
- http://m.wap.gqskj.cn/snews/5286.htm
- http://m.wap.gqskj.cn/snews/1559.htm
- http://m.wap.gqskj.cn/snews/720379.htm
- http://m.wap.gqskj.cn/snews/3982535.htm
- http://m.wap.gqskj.cn/snews/7354.htm
- http://m.wap.gqskj.cn/snews/31898.htm
- http://m.wap.gqskj.cn/snews/15513.htm
- http://m.wap.gqskj.cn/snews/6788.htm
- http://m.wap.gqskj.cn/snews/699899.htm
- http://m.wap.gqskj.cn/snews/76709.htm
- http://m.wap.gqskj.cn/snews/7532.htm
- http://m.wap.gqskj.cn/snews/33030.htm
- http://m.wap.gqskj.cn/snews/7466.htm
- http://m.wap.gqskj.cn/snews/2451.htm
- http://m.wap.gqskj.cn/snews/28140.htm
- http://m.wap.gqskj.cn/snews/858430.htm
- http://m.wap.gqskj.cn/snews/778596.htm
- http://m.wap.gqskj.cn/snews/72148.htm
- http://m.wap.gqskj.cn/snews/2385.htm
- http://m.wap.gqskj.cn/snews/19153.htm
- http://m.wap.gqskj.cn/snews/156249.htm
- http://m.wap.gqskj.cn/snews/89246.htm
- http://m.wap.gqskj.cn/snews/0484133.htm
- http://m.wap.gqskj.cn/snews/2137971.htm
- http://m.wap.gqskj.cn/snews/87958.htm
- http://m.wap.gqskj.cn/snews/9565.htm
- http://m.wap.gqskj.cn/snews/3392.htm
- http://m.wap.gqskj.cn/snews/890141.htm
- http://m.wap.gqskj.cn/snews/8578055.htm
- http://m.wap.gqskj.cn/snews/0942.htm
- http://m.wap.gqskj.cn/snews/658857.htm
- http://m.wap.gqskj.cn/snews/7914.htm
- http://m.wap.gqskj.cn/snews/620606.htm
- http://m.wap.gqskj.cn/snews/0400.htm
- http://m.wap.gqskj.cn/snews/4564614.htm
- http://m.wap.gqskj.cn/snews/77223.htm
- http://m.wap.gqskj.cn/snews/69474.htm
- http://m.wap.gqskj.cn/snews/437285.htm
- http://m.wap.gqskj.cn/snews/3997.htm
- http://m.wap.gqskj.cn/snews/9441.htm
- http://m.wap.gqskj.cn/snews/9651.htm
- http://m.wap.gqskj.cn/snews/0609.htm
- http://m.wap.gqskj.cn/snews/825989.htm
- http://m.wap.gqskj.cn/snews/8753.htm
- http://m.wap.gqskj.cn/snews/8114.htm
- http://m.wap.gqskj.cn/snews/243900.htm
- http://m.wap.gqskj.cn/snews/4782677.htm
- http://m.wap.gqskj.cn/snews/602060.htm
- http://m.wap.gqskj.cn/snews/6075383.htm
- http://m.wap.gqskj.cn/snews/2469262.htm
- http://m.wap.gqskj.cn/snews/03976.htm
- http://m.wap.gqskj.cn/snews/32634.htm
- http://m.wap.gqskj.cn/snews/710516.htm
- http://m.wap.gqskj.cn/snews/0409061.htm
- http://m.wap.gqskj.cn/snews/668585.htm
- http://m.wap.gqskj.cn/snews/09918.htm
- http://m.wap.gqskj.cn/snews/956791.htm
- http://m.wap.gqskj.cn/snews/28590.htm
- http://m.wap.gqskj.cn/snews/2489927.htm
- http://m.wap.gqskj.cn/snews/66023.htm
- http://m.wap.gqskj.cn/snews/8712.htm
- http://m.wap.gqskj.cn/snews/818046.htm
- http://m.wap.gqskj.cn/snews/3708.htm
- http://m.wap.gqskj.cn/snews/7686.htm
- http://m.wap.gqskj.cn/snews/21644.htm
- http://m.wap.gqskj.cn/snews/000402.htm
- http://m.wap.gqskj.cn/snews/89077.htm
- http://m.wap.gqskj.cn/snews/077558.htm
- http://m.wap.gqskj.cn/snews/0450.htm
- http://m.wap.gqskj.cn/snews/20078.htm
- http://m.wap.gqskj.cn/snews/6909566.htm
- http://m.wap.gqskj.cn/snews/3059.htm
- http://m.wap.gqskj.cn/snews/806821.htm
- http://m.wap.gqskj.cn/snews/6329796.htm
- http://m.wap.gqskj.cn/snews/69612.htm
- http://m.wap.gqskj.cn/snews/10360.htm
- http://m.wap.gqskj.cn/snews/7709174.htm
- http://m.wap.gqskj.cn/snews/3425565.htm
- http://m.wap.gqskj.cn/snews/94154.htm
- http://m.wap.gqskj.cn/snews/64415.htm
- http://m.wap.gqskj.cn/snews/1365.htm
- http://m.wap.gqskj.cn/snews/727472.htm
- http://m.wap.gqskj.cn/snews/2946887.htm
- http://m.wap.gqskj.cn/snews/6354681.htm
- http://m.wap.gqskj.cn/snews/242911.htm
- http://m.wap.gqskj.cn/snews/30550.htm
- http://m.wap.gqskj.cn/snews/707782.htm

## 项目结构

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── api/                            # RESTful API 路由定义
│   │   ├── v1/                         # API 版本 v1 端点
│   │   │   ├── links.ts                # 链接的增删改查接口
│   │   │   ├── batches.ts              # 批次管理与导入导出接口
│   │   │   └── health.ts               # 健康检查与状态探测接口
│   │   └── middleware/                 # 认证、日志、速率限制中间件
│   ├── core/                           # 核心业务逻辑层
│   │   ├── link-indexer.ts             # 链接索引构建与更新引擎
│   │   ├── classifier.ts               # 基于规则与机器学习的分类器
│   │   ├── health-checker.ts           # 链接可达性与状态码检查
│   │   └── stats-collector.ts          # 点击热度与访问统计聚合
│   ├── models/                         # 数据模型与 ORM 映射
│   │   ├── Link.ts                     # 链接实体模型
│   │   ├── Batch.ts                    # 批次实体模型
│   │   └── User.ts                     # 用户与权限模型
│   ├── services/                       # 外部服务适配器
│   │   ├── database.ts                 # PostgreSQL 连接池与查询构造
│   │   ├── cache.ts                    # Redis 缓存封装
│   │   └── fetcher.ts                  # HTTP 请求与重试策略
│   ├── ui/                             # 前端界面组件（React + Tailwind）
│   │   ├── pages/                      # 路由页面：首页、列表、详情、管理
│   │   ├── components/                 # 可复用组件：表格、卡片、过滤器
│   │   └── hooks/                      # 自定义 React Hooks 用于数据请求
│   └── utils/                          # 通用工具函数
│       ├── validators.ts               # URL 格式校验与规范化
│       ├── exporters.ts                # CSV / JSON / Markdown 导出生成
│       └── logger.ts                   # 结构化日志（winston）
├── config/                             # 环境配置与默认参数
│   ├── default.yaml                    # 默认配置项
│   ├── production.yaml                 # 生产环境覆盖配置
│   └── schema.ts                       # 配置类型定义与校验
├── migrations/                         # 数据库迁移脚本（Knex）
│   ├── 20250101000000_init.sql         # 初始表结构
│   └── 20250115000001_add_indexes.sql  # 索引优化迁移
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 核心逻辑单元测试（Jest）
│   └── integration/                    # API 与数据库集成测试
├── scripts/                            # 运维与开发辅助脚本
│   ├── seed-links.ts                   # 批量种子链接导入脚本
│   ├── health-scan.ts                  # 手动触发全量健康检查
│   └── backup-db.sh                    # 数据库备份脚本
├── docs/                               # 详细文档（见文档导航）
├── .env.example                        # 环境变量模板
├── package.json                        # 项目依赖与脚本定义
├── tsconfig.json                       # TypeScript 编译配置
├── docker-compose.yml                  # 本地开发容器编排
└── README.md                           # 本文件
```

## 贡献指南

**问题报告与功能建议**：请使用 GitHub Issues 提交。报告缺陷时需包含系统版本、复现步骤、预期与实际行为，并附上相关的日志片段或截图。功能建议请清晰描述使用场景与期望的交互方式。

**代码贡献流程**：Fork 本仓库并创建特性分支，遵循项目现有的 TypeScript 代码风格与 ESLint 规则。提交前需通过所有单元测试（`npm run test`）并确保新功能有对应的测试覆盖。提交信息请使用约定式提交格式（Conventional Commits）。

**文档完善与翻译**：欢迎改进文档的准确性、完整性与可读性。文档位于 `docs/` 目录，使用 Markdown 编写。若添加新的文档页面，请同时在 `README.md` 的文档导航表格中更新链接。

**链接资源推荐**：如果您发现高质量的技术资源链接，欢迎通过系统的导入功能提交推荐，或通过 Issues 提供链接与简要分类建议。项目维护者会定期审核并纳入后续批次。

**本地开发环境搭建**：参考快速开始步骤及 `docs/getting-started.md` 中的详细说明。如需使用 Docker 快速启动全部依赖服务，可执行 `docker-compose up -d`。

## 常见问题

**问：系统支持多少条链接的索引与管理？是否有性能瓶颈？**

答：系统设计目标为单实例支持 10 万条链接的索引与检索，检索响应时间在 200ms 以内。性能瓶颈主要取决于数据库查询优化与缓存命中率。推荐对 `url`、`batch_id`、`category` 等字段建立索引，并配置 Redis 缓存热点查询。对于超过 10 万条的大型部署，建议采用读写分离或分库分表策略。

**问：健康检查功能是否会频繁请求外部站点，导致被目标服务器屏蔽？**

答：健康检查默认采用低频率轮询策略，每个链接的检查间隔不低于 24 小时，且并发请求数限制为每秒 5 个。同时支持设置 `User-Agent` 与 `Referer` 头以模拟正常浏览器访问。用户可在配置文件中调整检查频率与超时时间，或手动暂停对特定域名的检查。

**问：如何迁移已有书签或链接库到本系统？**

答：系统支持从浏览器书签导出文件（HTML 格式）、Raindrop.io 导出 CSV、以及通用 JSON 格式导入。导入时系统会自动去重并尝试解析页面标题与描述。具体操作请参考 `docs/link-management.md` 中的导入章节。若需对接其他平台，可基于 REST API 开发自定义导入脚本。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:57
