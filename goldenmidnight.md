# WapLink Bridge

WapLink Bridge 是一个面向移动端网页链接聚合与结构化转发的开源网关项目。该项目定位于将分散的、以数字 ID 标识的移动端新闻或信息页面（如 m.wap.fcful.cn 域名下的 nnews 路径资源）统一纳入可检索、可分类、可监控的链接管理体系中。主要目标用户包括个人站长、内容聚合开发者、舆情监控研究人员以及需要批量管理移动端短链或动态链接的技术运维人员。

该项目通过提供标准化的链接导入接口、状态检测工具以及元数据提取脚本，解决了移动端动态页面链接易失效、缺乏上下文信息、难以批量维护的核心痛点。WapLink Bridge 不生产内容，而是为内容链接提供结构化的"桥接"能力，使开发者能够高效处理第 56/240 批次的链接资源，并支持后续批次的持续扩展。

## 功能概览

**批量链接导入** 支持通过 CSV 或纯文本列表批量导入 URL，自动解析路径参数与数字 ID。

**链接可达性检测** 定时对导入的链接发起 HEAD 与 GET 请求，检测 HTTP 状态码与响应时间。

**元数据自动提取** 从目标页面中提取标题、字符集、关键词与移动端视口设置等元信息。

**分类标签管理** 允许用户为不同链接添加自定义标签（如新闻、公告、归档），并支持按标签过滤。

**导出与转发接口** 提供 RESTful API 与 JSON 导出功能，便于将链接数据同步至其他系统或前端展示。

**状态变更通知** 当链接状态从可用变为不可用或反之，支持通过 Webhook 发送变更告警。

## 应用场景

**移动端内容聚合站点的链接维护** 内容聚合站运营者可以使用 WapLink Bridge 批量导入数千条移动端链接，系统自动检测其中失效或重定向的链接，从而及时更新内容库，避免用户访问到死链。

**舆情监控系统的数据源管理** 舆情分析团队可将特定域名下的动态链接纳入监控范围，利用 WapLink Bridge 的元数据提取功能定期抓取页面标题与发布时间，为后续的情绪分析或趋势判断提供结构化输入。

**CDN 或网关产品的链路测试** 网络运维人员可将一批移动端页面 URL 作为测试样本，通过 WapLink Bridge 的批量检测功能定期验证不同区域节点的访问质量，生成可用性报表。

**个人开发者快速搭建导航站** 独立开发者可以利用 WapLink Bridge 的导入与分类能力，将大量链接快速组织为带分类的导航页面，省去重复编写爬虫与解析逻辑的麻烦。

## 快速开始

以下指令演示了如何从 GitHub 克隆项目、安装依赖并启动开发服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/waplink-bridge.git

# 进入项目目录
cd waplink-bridge

# 安装依赖（使用 npm）
npm install

# 复制环境变量配置文件
cp .env.example .env

# 启动开发服务器（默认监听 3000 端口）
npm run dev
```

启动成功后，访问 `http://localhost:3000` 即可进入管理界面。首次启动会自动创建 SQLite 数据库文件并运行迁移脚本。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 18.x 或 20.x LTS | 项目基于 Node.js 运行时，推荐使用 20.11.0 以上版本 |
| npm | 9.x 或 10.x | 用于安装和管理项目依赖包 |
| SQLite3 | 3.x (内置) | 项目默认使用 SQLite 作为轻量级数据库，无需额外安装 |
| PM2 | 5.x (可选) | 生产环境推荐使用 PM2 进行进程守护和日志管理 |
| Git | 2.x 以上 | 用于克隆仓库和管理版本更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | `/docs/getting-started.md` | 如何在一小时内完成安装并导入第一批链接？ |
| 操作 | `/docs/import-guide.md` | 支持哪些导入格式？如何处理导入失败？ |
| 运维 | `/docs/monitoring.md` | 如何配置检测频率？如何接入告警通道？ |
| 开发 | `/docs/api-reference.md` | 有哪些可用的内部 API 接口？如何扩展新的元数据提取器？ |

## 资源列表

- http://m.wap.fcful.cn/nnews/189126.htm
- http://m.wap.fcful.cn/nnews/1234841.htm
- http://m.wap.fcful.cn/nnews/7478880.htm
- http://m.wap.fcful.cn/nnews/34591.htm
- http://m.wap.fcful.cn/nnews/3905276.htm
- http://m.wap.fcful.cn/nnews/8263.htm
- http://m.wap.fcful.cn/nnews/184503.htm
- http://m.wap.fcful.cn/nnews/4814906.htm
- http://m.wap.fcful.cn/nnews/37701.htm
- http://m.wap.fcful.cn/nnews/90681.htm
- http://m.wap.fcful.cn/nnews/6394.htm
- http://m.wap.fcful.cn/nnews/71327.htm
- http://m.wap.fcful.cn/nnews/443949.htm
- http://m.wap.fcful.cn/nnews/5417998.htm
- http://m.wap.fcful.cn/nnews/955733.htm
- http://m.wap.fcful.cn/nnews/7185022.htm
- http://m.wap.fcful.cn/nnews/87636.htm
- http://m.wap.fcful.cn/nnews/844293.htm
- http://m.wap.fcful.cn/nnews/7639.htm
- http://m.wap.fcful.cn/nnews/539085.htm
- http://m.wap.fcful.cn/nnews/854843.htm
- http://m.wap.fcful.cn/nnews/854004.htm
- http://m.wap.fcful.cn/nnews/727465.htm
- http://m.wap.fcful.cn/nnews/55996.htm
- http://m.wap.fcful.cn/nnews/8801508.htm
- http://m.wap.fcful.cn/nnews/83652.htm
- http://m.wap.fcful.cn/nnews/75807.htm
- http://m.wap.fcful.cn/nnews/2292.htm
- http://m.wap.fcful.cn/nnews/680360.htm
- http://m.wap.fcful.cn/nnews/2191.htm
- http://m.wap.fcful.cn/nnews/594600.htm
- http://m.wap.fcful.cn/nnews/7032.htm
- http://m.wap.fcful.cn/nnews/3927435.htm
- http://m.wap.fcful.cn/nnews/6220648.htm
- http://m.wap.fcful.cn/nnews/4352.htm
- http://m.wap.fcful.cn/nnews/1534565.htm
- http://m.wap.fcful.cn/nnews/6119238.htm
- http://m.wap.fcful.cn/nnews/4227.htm
- http://m.wap.fcful.cn/nnews/5885.htm
- http://m.wap.fcful.cn/nnews/5478.htm
- http://m.wap.fcful.cn/nnews/0665807.htm
- http://m.wap.fcful.cn/nnews/2057799.htm
- http://m.wap.fcful.cn/nnews/1688449.htm
- http://m.wap.fcful.cn/nnews/50015.htm
- http://m.wap.fcful.cn/nnews/5976.htm
- http://m.wap.fcful.cn/nnews/5447.htm
- http://m.wap.fcful.cn/nnews/044449.htm
- http://m.wap.fcful.cn/nnews/082432.htm
- http://m.wap.fcful.cn/nnews/711621.htm
- http://m.wap.fcful.cn/nnews/4758.htm
- http://m.wap.fcful.cn/nnews/9217898.htm
- http://m.wap.fcful.cn/nnews/3043113.htm
- http://m.wap.fcful.cn/nnews/92210.htm
- http://m.wap.fcful.cn/nnews/7834030.htm
- http://m.wap.fcful.cn/nnews/444515.htm
- http://m.wap.fcful.cn/nnews/6078697.htm
- http://m.wap.fcful.cn/nnews/5096431.htm
- http://m.wap.fcful.cn/nnews/12529.htm
- http://m.wap.fcful.cn/nnews/744542.htm
- http://m.wap.fcful.cn/nnews/623900.htm
- http://m.wap.fcful.cn/nnews/16369.htm
- http://m.wap.fcful.cn/nnews/2962997.htm
- http://m.wap.fcful.cn/nnews/151945.htm
- http://m.wap.fcful.cn/nnews/63546.htm
- http://m.wap.fcful.cn/nnews/5206.htm
- http://m.wap.fcful.cn/nnews/18275.htm
- http://m.wap.fcful.cn/nnews/941692.htm
- http://m.wap.fcful.cn/nnews/650153.htm
- http://m.wap.fcful.cn/nnews/0451064.htm
- http://m.wap.fcful.cn/nnews/487813.htm
- http://m.wap.fcful.cn/nnews/7077.htm
- http://m.wap.fcful.cn/nnews/38502.htm
- http://m.wap.fcful.cn/nnews/2087407.htm
- http://m.wap.fcful.cn/nnews/784309.htm
- http://m.wap.fcful.cn/nnews/90540.htm
- http://m.wap.fcful.cn/nnews/3046622.htm
- http://m.wap.fcful.cn/nnews/38745.htm
- http://m.wap.fcful.cn/nnews/1075419.htm
- http://m.wap.fcful.cn/nnews/3841115.htm
- http://m.wap.fcful.cn/nnews/8141651.htm
- http://m.wap.fcful.cn/nnews/4906.htm
- http://m.wap.fcful.cn/nnews/09727.htm
- http://m.wap.fcful.cn/nnews/92781.htm
- http://m.wap.fcful.cn/nnews/718916.htm
- http://m.wap.fcful.cn/nnews/3438.htm
- http://m.wap.fcful.cn/nnews/1443.htm
- http://m.wap.fcful.cn/nnews/004844.htm
- http://m.wap.fcful.cn/nnews/043835.htm
- http://m.wap.fcful.cn/nnews/4458.htm
- http://m.wap.fcful.cn/nnews/965370.htm
- http://m.wap.fcful.cn/nnews/18802.htm
- http://m.wap.fcful.cn/nnews/9394.htm
- http://m.wap.fcful.cn/nnews/9270.htm
- http://m.wap.fcful.cn/nnews/5047056.htm
- http://m.wap.fcful.cn/nnews/9432.htm
- http://m.wap.fcful.cn/nnews/52189.htm
- http://m.wap.fcful.cn/nnews/3375510.htm
- http://m.wap.fcful.cn/nnews/111525.htm
- http://m.wap.fcful.cn/nnews/23989.htm
- http://m.wap.fcful.cn/nnews/67584.htm
- http://m.wap.fcful.cn/nnews/9966530.htm
- http://m.wap.fcful.cn/nnews/18417.htm
- http://m.wap.fcful.cn/nnews/65411.htm
- http://m.wap.fcful.cn/nnews/3559161.htm
- http://m.wap.fcful.cn/nnews/96269.htm
- http://m.wap.fcful.cn/nnews/5081230.htm
- http://m.wap.fcful.cn/nnews/78604.htm
- http://m.wap.fcful.cn/nnews/108310.htm
- http://m.wap.fcful.cn/nnews/5437193.htm
- http://m.wap.fcful.cn/nnews/0892270.htm
- http://m.wap.fcful.cn/nnews/7628.htm
- http://m.wap.fcful.cn/nnews/6737.htm
- http://m.wap.fcful.cn/nnews/8364.htm
- http://m.wap.fcful.cn/nnews/590777.htm
- http://m.wap.fcful.cn/nnews/56878.htm
- http://m.wap.fcful.cn/nnews/82567.htm
- http://m.wap.fcful.cn/nnews/2080.htm
- http://m.wap.fcful.cn/nnews/263796.htm
- http://m.wap.fcful.cn/nnews/45115.htm
- http://m.wap.fcful.cn/nnews/3627084.htm
- http://m.wap.fcful.cn/nnews/77946.htm
- http://m.wap.fcful.cn/nnews/4166.htm
- http://m.wap.fcful.cn/nnews/731275.htm
- http://m.wap.fcful.cn/nnews/1605.htm
- http://m.wap.fcful.cn/nnews/1252.htm
- http://m.wap.fcful.cn/nnews/5931896.htm
- http://m.wap.fcful.cn/nnews/24608.htm
- http://m.wap.fcful.cn/nnews/170733.htm
- http://m.wap.fcful.cn/nnews/3372854.htm
- http://m.wap.fcful.cn/nnews/447106.htm
- http://m.wap.fcful.cn/nnews/4467.htm
- http://m.wap.fcful.cn/nnews/686015.htm
- http://m.wap.fcful.cn/nnews/029888.htm
- http://m.wap.fcful.cn/nnews/45541.htm
- http://m.wap.fcful.cn/nnews/1164410.htm
- http://m.wap.fcful.cn/nnews/6651.htm
- http://m.wap.fcful.cn/nnews/1005.htm
- http://m.wap.fcful.cn/nnews/931357.htm
- http://m.wap.fcful.cn/nnews/75709.htm
- http://m.wap.fcful.cn/nnews/2368.htm
- http://m.wap.fcful.cn/nnews/3151.htm
- http://m.wap.fcful.cn/nnews/6614394.htm
- http://m.wap.fcful.cn/nnews/4426196.htm
- http://m.wap.fcful.cn/nnews/172667.htm
- http://m.wap.fcful.cn/nnews/4120375.htm
- http://m.wap.fcful.cn/nnews/501448.htm
- http://m.wap.fcful.cn/nnews/4135.htm
- http://m.wap.fcful.cn/nnews/577171.htm
- http://m.wap.fcful.cn/nnews/54963.htm
- http://m.wap.fcful.cn/nnews/731687.htm
- http://m.wap.fcful.cn/nnews/61184.htm
- http://m.wap.fcful.cn/nnews/5311.htm
- http://m.wap.fcful.cn/nnews/2748.htm
- http://m.wap.fcful.cn/nnews/3731244.htm
- http://m.wap.fcful.cn/nnews/9776294.htm
- http://m.wap.fcful.cn/nnews/1786072.htm
- http://m.wap.fcful.cn/nnews/6833967.htm
- http://m.wap.fcful.cn/nnews/29756.htm
- http://m.wap.fcful.cn/nnews/4602.htm
- http://m.wap.fcful.cn/nnews/53682.htm
- http://m.wap.fcful.cn/nnews/098570.htm
- http://m.wap.fcful.cn/nnews/816486.htm
- http://m.wap.fcful.cn/nnews/13542.htm
- http://m.wap.fcful.cn/nnews/60961.htm
- http://m.wap.fcful.cn/nnews/45243.htm
- http://m.wap.fcful.cn/nnews/407457.htm
- http://m.wap.fcful.cn/nnews/9846666.htm
- http://m.wap.fcful.cn/nnews/8440093.htm
- http://m.wap.fcful.cn/nnews/961781.htm
- http://m.wap.fcful.cn/nnews/5755.htm
- http://m.wap.fcful.cn/nnews/36943.htm
- http://m.wap.fcful.cn/nnews/1322837.htm
- http://m.wap.fcful.cn/nnews/2483.htm
- http://m.wap.fcful.cn/nnews/00310.htm
- http://m.wap.fcful.cn/nnews/3864274.htm
- http://m.wap.fcful.cn/nnews/65043.htm
- http://m.wap.fcful.cn/nnews/2980.htm
- http://m.wap.fcful.cn/nnews/7060.htm
- http://m.wap.fcful.cn/nnews/285059.htm
- http://m.wap.fcful.cn/nnews/3333067.htm
- http://m.wap.fcful.cn/nnews/8811.htm
- http://m.wap.fcful.cn/nnews/922186.htm
- http://m.wap.fcful.cn/nnews/8184.htm
- http://m.wap.fcful.cn/nnews/70780.htm
- http://m.wap.fcful.cn/nnews/99905.htm
- http://m.wap.fcful.cn/nnews/1454968.htm
- http://m.wap.fcful.cn/nnews/98102.htm
- http://m.wap.fcful.cn/nnews/1345292.htm
- http://m.wap.fcful.cn/nnews/7492.htm
- http://m.wap.fcful.cn/nnews/8391.htm
- http://m.wap.fcful.cn/nnews/5192412.htm
- http://m.wap.fcful.cn/nnews/0571.htm
- http://m.wap.fcful.cn/nnews/14519.htm
- http://m.wap.fcful.cn/nnews/72286.htm
- http://m.wap.fcful.cn/nnews/0557.htm
- http://m.wap.fcful.cn/nnews/7674.htm
- http://m.wap.fcful.cn/nnews/3189.htm
- http://m.wap.fcful.cn/nnews/6145908.htm
- http://m.wap.fcful.cn/nnews/390391.htm
- http://m.wap.fcful.cn/nnews/0745.htm
- http://m.wap.fcful.cn/nnews/15951.htm
- http://m.wap.fcful.cn/nnews/05025.htm
- http://m.wap.fcful.cn/nnews/649524.htm
- http://m.wap.fcful.cn/nnews/157949.htm
- http://m.wap.fcful.cn/nnews/9645.htm
- http://m.wap.fcful.cn/nnews/513882.htm
- http://m.wap.fcful.cn/nnews/17555.htm
- http://m.wap.fcful.cn/nnews/9571.htm
- http://m.wap.fcful.cn/nnews/73216.htm
- http://m.wap.fcful.cn/nnews/5756.htm
- http://m.wap.fcful.cn/nnews/36017.htm
- http://m.wap.fcful.cn/nnews/8115400.htm
- http://m.wap.fcful.cn/nnews/1970.htm
- http://m.wap.fcful.cn/nnews/0507.htm
- http://m.wap.fcful.cn/nnews/8831.htm
- http://m.wap.fcful.cn/nnews/1600876.htm
- http://m.wap.fcful.cn/nnews/6701.htm
- http://m.wap.fcful.cn/nnews/3349924.htm
- http://m.wap.fcful.cn/nnews/3452567.htm
- http://m.wap.fcful.cn/nnews/3118.htm
- http://m.wap.fcful.cn/nnews/384852.htm
- http://m.wap.fcful.cn/nnews/68005.htm
- http://m.wap.fcful.cn/nnews/6485.htm
- http://m.wap.fcful.cn/nnews/96446.htm
- http://m.wap.fcful.cn/nnews/03707.htm
- http://m.wap.fcful.cn/nnews/28296.htm
- http://m.wap.fcful.cn/nnews/479765.htm
- http://m.wap.fcful.cn/nnews/3098306.htm
- http://m.wap.fcful.cn/nnews/883715.htm
- http://m.wap.fcful.cn/nnews/42411.htm
- http://m.wap.fcful.cn/nnews/1571254.htm
- http://m.wap.fcful.cn/nnews/9827044.htm
- http://m.wap.fcful.cn/nnews/4581.htm
- http://m.wap.fcful.cn/nnews/141764.htm
- http://m.wap.fcful.cn/nnews/49794.htm
- http://m.wap.fcful.cn/nnews/231157.htm
- http://m.wap.fcful.cn/nnews/6755.htm
- http://m.wap.fcful.cn/nnews/943265.htm
- http://m.wap.fcful.cn/nnews/300277.htm
- http://m.wap.fcful.cn/nnews/994347.htm
- http://m.wap.fcful.cn/nnews/3199.htm
- http://m.wap.fcful.cn/nnews/2947.htm
- http://m.wap.fcful.cn/nnews/1937085.htm
- http://m.wap.fcful.cn/nnews/6203755.htm
- http://m.wap.fcful.cn/nnews/428689.htm
- http://m.wap.fcful.cn/nnews/2783772.htm
- http://m.wap.fcful.cn/nnews/8541.htm
- http://m.wap.fcful.cn/nnews/14648.htm
- http://m.wap.fcful.cn/nnews/13064.htm
- http://m.wap.fcful.cn/nnews/875744.htm

## 项目结构

```
waplink-bridge/
├── src/
│   ├── core/                     # 核心逻辑模块
│   │   ├── linkManager.js        # 链接增删改查与状态管理
│   │   ├── fetcher.js            # 基于 node-fetch 的请求封装，支持超时与重试
│   │   └── metadataExtractor.js  # 使用 cheerio 提取页面标题与 meta 信息
│   ├── routes/                   # API 路由层
│   │   ├── importRoutes.js       # 批量导入与解析接口
│   │   ├── statusRoutes.js       # 状态查询与统计接口
│   │   └── exportRoutes.js       # JSON/CSV 导出接口
│   ├── services/                 # 业务服务层
│   │   ├── detectionScheduler.js # 基于 node-cron 的定时检测调度服务
│   │   ├── tagService.js         # 标签增删改查与关联逻辑
│   │   └── webhookService.js     # 状态变更时的 Webhook 分发服务
│   ├── db/                       # 数据库相关
│   │   ├── migrations/           # 迁移脚本（按时间戳命名）
│   │   ├── models/               # 数据模型定义（Link, Tag, Log）
│   │   └── sqliteClient.js       # SQLite 连接与查询封装
│   ├── utils/                    # 通用工具函数
│   │   ├── urlValidator.js       # URL 格式校验与规范化
│   │   ├── logger.js             # 基于 winston 的日志记录器
│   │   └── configLoader.js       # 环境变量加载与默认值合并
│   └── app.js                    # Express 应用入口
├── tests/                        # 单元测试与集成测试
│   ├── unit/                     # 针对核心模块的独立测试
│   └── integration/              # 针对 API 路由的端到端测试
├── docs/                         # 文档目录（入门指南、API 参考、运维手册）
├── scripts/                      # 运维辅助脚本
│   ├── seed.js                   # 初始化测试数据
│   └── exportSnapshot.js         # 手动导出链接快照
├── .env.example                  # 环境变量模板
├── package.json                  # npm 依赖与脚本定义
├── README.md                     # 项目说明文档（本文件）
└── LICENSE                       # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。建议使用 Node.js 20.x 版本，并开启 Corepack 以匹配包管理器版本。

2. 创建新的功能分支，分支名称请遵循 `feature/功能简述` 或 `fix/问题简述` 的格式。提交代码前请运行 `npm run lint` 与 `npm run test` 确保代码风格与测试用例全部通过。

3. 为新增的功能或修复的缺陷编写对应的单元测试，测试文件放置于 `tests/unit/` 目录下，命名与源文件对应。

4. 提交 Pull Request 时请在描述中清晰说明变更目的、影响范围以及测试覆盖情况。涉及数据库迁移的变更，需同时提供回滚方案。

5. 文档更新与代码变更需同步提交。若新增了配置项或 API 接口，请同步更新 `/docs` 目录下的对应文档。

## 常见问题

**问：导入包含大量 URL 的文件时，系统出现超时或卡顿，应如何优化？**

答：建议将单次导入的文件大小控制在 5000 条以内。若需导入超过此数量的链接，可启用 `config/config.js` 中的分批导入功能，每批处理 500 条并间隔 2 秒。同时可调整 PM2 的 `max_memory_restart` 参数至 1024M 以应对大文件解析。

**问：检测模块如何区分链接是临时不可用还是永久失效？**

答：检测模块会根据 HTTP 状态码进行分级处理。状态码 503 或 429 会被标记为临时不可用，并在后续检测周期中继续重试。状态码 404、410 或连接超时超过 30 秒会被标记为永久失效。用户可在 `src/core/fetcher.js` 中调整 `RETRY_STATUSES` 与 `MAX_RETRY` 变量以自定义判定逻辑。

**问：项目是否支持 PostgreSQL 或 MySQL 作为生产数据库？**

答：当前版本仅内置 SQLite 驱动以降低起步门槛。从 `v2.0.0` 版本开始，项目通过 Knex.js 构建查询构建器，用户可自行安装 `pg` 或 `mysql2` 驱动，并在 `.env` 文件中修改 `DB_CLIENT` 与 `DB_CONNECTION_STRING` 配置来切换数据库。官方文档的运维章节提供了详细的切换步骤。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
