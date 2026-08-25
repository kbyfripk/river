# WapLink Hub

WapLink Hub 是一个面向移动端资讯聚合与深度链接导航的开源工具集，专注于将散落在移动 WAP 站点中的碎片化新闻、公告与长尾内容，通过结构化索引与轻量级代理，转化为可检索、可订阅、可追溯的标准化数据流。项目目标用户包括个人开发者、内容聚合服务商、移动端 SEO 研究人员以及自建资讯流的小型团队，帮助其在无需维护完整爬虫集群的前提下，快速构建基于 WAP 内容的次级入口。

项目通过提供统一的 URL 规范化处理器、内容摘要抽取模板与失效链接检测模块，将原本离散的移动页面资源整合为稳定的外链资产清单。配合本项目附带的 250 个精选 WAP 新闻入口，使用者可立即获得一个覆盖多领域、多时间跨度的移动端内容索引基底，显著降低内容发现与链路维护成本。

## 功能概览

- 移动 WAP 链接归一化与去重：自动识别不同参数变体，保留最短有效路径，剔除重复条目，输出纯净链接清单。
- 批量存活检测与状态标记：支持 HTTP 头快速检查与超时重试，对每个链接返回可达性、重定向链与响应时间。
- 内容摘要规则配置：提供基于 XPath 与正则表达式的标题、发布时间、正文首段抽取模板，适配多种 WAP 页面结构。
- 定时任务与变更通知：内置轮询调度器，可设置按小时或每日扫描链接列表，当页面状态或标题发生变化时生成差异报告。
- 数据导出与接口服务：支持 JSON、CSV、RSS 三种导出格式，并提供只读 RESTful API 供上游系统按分类、日期或关键词查询。
- 静态前端演示面板：附带最小化单页应用，用于可视化浏览链接列表、筛选失效条目并查看摘要快照。
- 外链资产版本管理：每次全量扫描结果自动归档至 `snapshots/` 目录，支持回滚与历史对比。
- 资源黑名单与白名单过滤：允许用户自定义域名或路径正则，批量屏蔽广告页或非新闻类内容。

## 应用场景

1. 个人每日移动资讯简报生成：用户可将本项目的 250 个 WAP 链接作为初始种子，配合定时任务每日自动抓取标题与摘要，生成一份适合手机阅读的纯文本或 HTML 简报邮件。

2. 小规模垂直领域舆情监控：运营者只需从资源列表中筛选与特定行业相关的链接（例如科技、财经或地方新闻），配置关键词过滤规则，即可获得低成本的舆情变动提醒，无需购买商用爬虫服务。

3. WAP 站点迁移或改版期间的链接审计：当目标移动站点调整 URL 结构时，项目提供的批量检测功能可帮助管理员快速识别新旧地址映射关系，避免内容丢失或流量流失。

4. 开源内容聚合演示站搭建：开发者可使用本项目提供的 API 与前端面板，在几分钟内部署一个展示移动 WAP 内容热点的 demo 站点，用于技术演示或内部培训。

## 快速开始

以下命令将完整克隆项目、安装依赖并启动开发服务器。

```bash
git clone https://github.com/example/waplink-hub.git
cd waplink-hub
npm install
cp .env.example .env
npm run build
npm start
```

若使用 Docker 方式运行，可执行：

```bash
docker build -t waplink-hub .
docker run -p 3000:3000 -v $(pwd)/data:/app/data waplink-hub
```

访问 `http://localhost:3000` 即可看到默认的链接列表看板。首次启动时，系统会自动加载 `resources/seed.txt` 中的初始 URL 列表（即本项目资源列表章节所收录的全部链接），并执行首次存活检测。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 运行时环境，需支持 ES2022 特性 |
| npm | >= 9.0.0 | 包管理工具，用于安装依赖项 |
| SQLite3 | 内置（无需额外安装） | 本地元数据缓存与历史记录存储 |
| curl | >= 7.68.0（Linux/macOS） | 用于备用的 HTTP 探测回退策略 |
| 系统内存 | >= 512 MB（推荐 1 GB） | 运行定时任务及处理 250+ 并发检测时的最低要求 |
| 磁盘空间 | >= 200 MB | 存放快照、日志及 SQLite 数据库 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `docs/getting-started.md` | 如何从零开始配置并运行第一次扫描任务 |
| 链接管理 | `docs/link-management.md` | 如何增删改查链接、导入外部列表以及处理失效地址 |
| API 参考 | `docs/api-reference.md` | REST 接口的完整端点、请求参数与返回示例 |
| 部署运维 | `docs/deployment.md` | 生产环境下的进程守护、日志轮转与性能调优建议 |

## 资源列表

- http://m.wap.fcful.cn/nnews/729716.htm
- http://m.wap.fcful.cn/nnews/7441.htm
- http://m.wap.fcful.cn/nnews/928348.htm
- http://m.wap.fcful.cn/nnews/9064046.htm
- http://m.wap.fcful.cn/nnews/00381.htm
- http://m.wap.fcful.cn/nnews/1577445.htm
- http://m.wap.fcful.cn/nnews/0959.htm
- http://m.wap.fcful.cn/nnews/955909.htm
- http://m.wap.fcful.cn/nnews/504031.htm
- http://m.wap.fcful.cn/nnews/0609078.htm
- http://m.wap.fcful.cn/nnews/2353928.htm
- http://m.wap.fcful.cn/nnews/493537.htm
- http://m.wap.fcful.cn/nnews/664969.htm
- http://m.wap.fcful.cn/nnews/2671.htm
- http://m.wap.fcful.cn/nnews/4024.htm
- http://m.wap.fcful.cn/nnews/51756.htm
- http://m.wap.fcful.cn/nnews/9189180.htm
- http://m.wap.fcful.cn/nnews/001543.htm
- http://m.wap.fcful.cn/nnews/5012.htm
- http://m.wap.fcful.cn/nnews/132075.htm
- http://m.wap.fcful.cn/nnews/26162.htm
- http://m.wap.fcful.cn/nnews/665640.htm
- http://m.wap.fcful.cn/nnews/0774767.htm
- http://m.wap.fcful.cn/nnews/88754.htm
- http://m.wap.fcful.cn/nnews/0026.htm
- http://m.wap.fcful.cn/nnews/6557159.htm
- http://m.wap.fcful.cn/nnews/2741.htm
- http://m.wap.fcful.cn/nnews/4551889.htm
- http://m.wap.fcful.cn/nnews/3313.htm
- http://m.wap.fcful.cn/nnews/85922.htm
- http://m.wap.fcful.cn/nnews/22473.htm
- http://m.wap.fcful.cn/nnews/7594445.htm
- http://m.wap.fcful.cn/nnews/40082.htm
- http://m.wap.fcful.cn/nnews/796783.htm
- http://m.wap.fcful.cn/nnews/014071.htm
- http://m.wap.fcful.cn/nnews/9569021.htm
- http://m.wap.fcful.cn/nnews/0521.htm
- http://m.wap.fcful.cn/nnews/5986147.htm
- http://m.wap.fcful.cn/nnews/7115710.htm
- http://m.wap.fcful.cn/nnews/523940.htm
- http://m.wap.fcful.cn/nnews/3385.htm
- http://m.wap.fcful.cn/nnews/04583.htm
- http://m.wap.fcful.cn/nnews/8085282.htm
- http://m.wap.fcful.cn/nnews/4823399.htm
- http://m.wap.fcful.cn/nnews/107106.htm
- http://m.wap.fcful.cn/nnews/8451197.htm
- http://m.wap.fcful.cn/nnews/2603.htm
- http://m.wap.fcful.cn/nnews/836124.htm
- http://m.wap.fcful.cn/nnews/8216599.htm
- http://m.wap.fcful.cn/nnews/2137244.htm
- http://m.wap.fcful.cn/nnews/5209.htm
- http://m.wap.fcful.cn/nnews/0607240.htm
- http://m.wap.fcful.cn/nnews/0327931.htm
- http://m.wap.fcful.cn/nnews/74253.htm
- http://m.wap.fcful.cn/nnews/90670.htm
- http://m.wap.fcful.cn/nnews/92343.htm
- http://m.wap.fcful.cn/nnews/9943.htm
- http://m.wap.fcful.cn/nnews/90993.htm
- http://m.wap.fcful.cn/nnews/7630.htm
- http://m.wap.fcful.cn/nnews/3488.htm
- http://m.wap.fcful.cn/nnews/7303.htm
- http://m.wap.fcful.cn/nnews/944964.htm
- http://m.wap.fcful.cn/nnews/3182346.htm
- http://m.wap.fcful.cn/nnews/4090.htm
- http://m.wap.fcful.cn/nnews/8107.htm
- http://m.wap.fcful.cn/nnews/400496.htm
- http://m.wap.fcful.cn/nnews/8136163.htm
- http://m.wap.fcful.cn/nnews/5211471.htm
- http://m.wap.fcful.cn/nnews/70511.htm
- http://m.wap.fcful.cn/nnews/5158.htm
- http://m.wap.fcful.cn/nnews/9193959.htm
- http://m.wap.fcful.cn/nnews/775998.htm
- http://m.wap.fcful.cn/nnews/735226.htm
- http://m.wap.fcful.cn/nnews/88467.htm
- http://m.wap.fcful.cn/nnews/163280.htm
- http://m.wap.fcful.cn/nnews/4466780.htm
- http://m.wap.fcful.cn/nnews/4178209.htm
- http://m.wap.fcful.cn/nnews/0379671.htm
- http://m.wap.fcful.cn/nnews/8104590.htm
- http://m.wap.fcful.cn/nnews/4480828.htm
- http://m.wap.fcful.cn/nnews/206540.htm
- http://m.wap.fcful.cn/nnews/8112.htm
- http://m.wap.fcful.cn/nnews/3655.htm
- http://m.wap.fcful.cn/nnews/4457598.htm
- http://m.wap.fcful.cn/nnews/2163.htm
- http://m.wap.fcful.cn/nnews/8615.htm
- http://m.wap.fcful.cn/nnews/569177.htm
- http://m.wap.fcful.cn/nnews/89417.htm
- http://m.wap.fcful.cn/nnews/0391150.htm
- http://m.wap.fcful.cn/nnews/6010230.htm
- http://m.wap.fcful.cn/nnews/70623.htm
- http://m.wap.fcful.cn/nnews/3028591.htm
- http://m.wap.fcful.cn/nnews/40950.htm
- http://m.wap.fcful.cn/nnews/939074.htm
- http://m.wap.fcful.cn/nnews/6658187.htm
- http://m.wap.fcful.cn/nnews/1327776.htm
- http://m.wap.fcful.cn/nnews/5805413.htm
- http://m.wap.fcful.cn/nnews/573918.htm
- http://m.wap.fcful.cn/nnews/631588.htm
- http://m.wap.fcful.cn/nnews/9672.htm
- http://m.wap.fcful.cn/nnews/344805.htm
- http://m.wap.fcful.cn/nnews/0960.htm
- http://m.wap.fcful.cn/nnews/8868.htm
- http://m.wap.fcful.cn/nnews/6325765.htm
- http://m.wap.fcful.cn/nnews/6668198.htm
- http://m.wap.fcful.cn/nnews/6045143.htm
- http://m.wap.fcful.cn/nnews/37996.htm
- http://m.wap.fcful.cn/nnews/8145815.htm
- http://m.wap.fcful.cn/nnews/807516.htm
- http://m.wap.fcful.cn/nnews/8394883.htm
- http://m.wap.fcful.cn/nnews/1689838.htm
- http://m.wap.fcful.cn/nnews/0266.htm
- http://m.wap.fcful.cn/nnews/58699.htm
- http://m.wap.fcful.cn/nnews/928641.htm
- http://m.wap.fcful.cn/nnews/3256035.htm
- http://m.wap.fcful.cn/nnews/035236.htm
- http://m.wap.fcful.cn/nnews/59852.htm
- http://m.wap.fcful.cn/nnews/846163.htm
- http://m.wap.fcful.cn/nnews/8941909.htm
- http://m.wap.fcful.cn/nnews/6868772.htm
- http://m.wap.fcful.cn/nnews/2045847.htm
- http://m.wap.fcful.cn/nnews/7440.htm
- http://m.wap.fcful.cn/nnews/89751.htm
- http://m.wap.fcful.cn/nnews/4425.htm
- http://m.wap.fcful.cn/nnews/322273.htm
- http://m.wap.fcful.cn/nnews/0217.htm
- http://m.wap.fcful.cn/nnews/0515.htm
- http://m.wap.fcful.cn/nnews/70162.htm
- http://m.wap.fcful.cn/nnews/8926188.htm
- http://m.wap.fcful.cn/nnews/85226.htm
- http://m.wap.fcful.cn/nnews/0923711.htm
- http://m.wap.fcful.cn/nnews/731827.htm
- http://m.wap.fcful.cn/nnews/6906.htm
- http://m.wap.fcful.cn/nnews/681910.htm
- http://m.wap.fcful.cn/nnews/5824.htm
- http://m.wap.fcful.cn/nnews/304599.htm
- http://m.wap.fcful.cn/nnews/3906.htm
- http://m.wap.fcful.cn/nnews/0019.htm
- http://m.wap.fcful.cn/nnews/3436.htm
- http://m.wap.fcful.cn/nnews/3714197.htm
- http://m.wap.fcful.cn/nnews/6007.htm
- http://m.wap.fcful.cn/nnews/85590.htm
- http://m.wap.fcful.cn/nnews/684501.htm
- http://m.wap.fcful.cn/nnews/15291.htm
- http://m.wap.fcful.cn/nnews/0435.htm
- http://m.wap.fcful.cn/nnews/028426.htm
- http://m.wap.fcful.cn/nnews/269665.htm
- http://m.wap.fcful.cn/nnews/46349.htm
- http://m.wap.fcful.cn/nnews/9638.htm
- http://m.wap.fcful.cn/nnews/0374.htm
- http://m.wap.fcful.cn/nnews/3571185.htm
- http://m.wap.fcful.cn/nnews/498430.htm
- http://m.wap.fcful.cn/nnews/46947.htm
- http://m.wap.fcful.cn/nnews/90288.htm
- http://m.wap.fcful.cn/nnews/1949247.htm
- http://m.wap.fcful.cn/nnews/353327.htm
- http://m.wap.fcful.cn/nnews/7489940.htm
- http://m.wap.fcful.cn/nnews/166950.htm
- http://m.wap.fcful.cn/nnews/496217.htm
- http://m.wap.fcful.cn/nnews/26820.htm
- http://m.wap.fcful.cn/nnews/214429.htm
- http://m.wap.fcful.cn/nnews/78378.htm
- http://m.wap.fcful.cn/nnews/81298.htm
- http://m.wap.fcful.cn/nnews/6873.htm
- http://m.wap.fcful.cn/nnews/202816.htm
- http://m.wap.fcful.cn/nnews/9886.htm
- http://m.wap.fcful.cn/nnews/7798611.htm
- http://m.wap.fcful.cn/nnews/045510.htm
- http://m.wap.fcful.cn/nnews/87267.htm
- http://m.wap.fcful.cn/nnews/501878.htm
- http://m.wap.fcful.cn/nnews/70354.htm
- http://m.wap.fcful.cn/nnews/4844.htm
- http://m.wap.fcful.cn/nnews/380159.htm
- http://m.wap.fcful.cn/nnews/89891.htm
- http://m.wap.fcful.cn/nnews/0666.htm
- http://m.wap.fcful.cn/nnews/94321.htm
- http://m.wap.fcful.cn/nnews/285735.htm
- http://m.wap.fcful.cn/nnews/7136818.htm
- http://m.wap.fcful.cn/nnews/37574.htm
- http://m.wap.fcful.cn/nnews/52164.htm
- http://m.wap.fcful.cn/nnews/7835.htm
- http://m.wap.fcful.cn/nnews/29639.htm
- http://m.wap.fcful.cn/nnews/1794782.htm
- http://m.wap.fcful.cn/nnews/389069.htm
- http://m.wap.fcful.cn/nnews/1495466.htm
- http://m.wap.fcful.cn/nnews/67438.htm
- http://m.wap.fcful.cn/nnews/7774641.htm
- http://m.wap.fcful.cn/nnews/679374.htm
- http://m.wap.fcful.cn/nnews/13007.htm
- http://m.wap.fcful.cn/nnews/26301.htm
- http://m.wap.fcful.cn/nnews/272731.htm
- http://m.wap.fcful.cn/nnews/85728.htm
- http://m.wap.fcful.cn/nnews/761207.htm
- http://m.wap.fcful.cn/nnews/7730744.htm
- http://m.wap.fcful.cn/nnews/8682207.htm
- http://m.wap.fcful.cn/nnews/84194.htm
- http://m.wap.fcful.cn/nnews/6565254.htm
- http://m.wap.fcful.cn/nnews/887496.htm
- http://m.wap.fcful.cn/nnews/69785.htm
- http://m.wap.fcful.cn/nnews/5950661.htm
- http://m.wap.fcful.cn/nnews/938390.htm
- http://m.wap.fcful.cn/nnews/25226.htm
- http://m.wap.fcful.cn/nnews/580338.htm
- http://m.wap.fcful.cn/nnews/8142996.htm
- http://m.wap.fcful.cn/nnews/3088077.htm
- http://m.wap.fcful.cn/nnews/5558.htm
- http://m.wap.fcful.cn/nnews/0067141.htm
- http://m.wap.fcful.cn/nnews/6789.htm
- http://m.wap.fcful.cn/nnews/476590.htm
- http://m.wap.fcful.cn/nnews/84980.htm
- http://m.wap.fcful.cn/nnews/7023.htm
- http://m.wap.fcful.cn/nnews/635027.htm
- http://m.wap.fcful.cn/nnews/47497.htm
- http://m.wap.fcful.cn/nnews/501994.htm
- http://m.wap.fcful.cn/nnews/711936.htm
- http://m.wap.fcful.cn/nnews/98655.htm
- http://m.wap.fcful.cn/nnews/8363567.htm
- http://m.wap.fcful.cn/nnews/91602.htm
- http://m.wap.fcful.cn/nnews/596782.htm
- http://m.wap.fcful.cn/nnews/000820.htm
- http://m.wap.fcful.cn/nnews/207840.htm
- http://m.wap.fcful.cn/nnews/9366.htm
- http://m.wap.fcful.cn/nnews/33013.htm
- http://m.wap.fcful.cn/nnews/5820349.htm
- http://m.wap.fcful.cn/nnews/6217170.htm
- http://m.wap.fcful.cn/nnews/89570.htm
- http://m.wap.fcful.cn/nnews/7645945.htm
- http://m.wap.fcful.cn/nnews/7019347.htm
- http://m.wap.fcful.cn/nnews/393256.htm
- http://m.wap.fcful.cn/nnews/136968.htm
- http://m.wap.fcful.cn/nnews/484580.htm
- http://m.wap.fcful.cn/nnews/83388.htm
- http://m.wap.fcful.cn/nnews/46412.htm
- http://m.wap.fcful.cn/nnews/2983.htm
- http://m.wap.fcful.cn/nnews/3917.htm
- http://m.wap.fcful.cn/nnews/5590.htm
- http://m.wap.fcful.cn/nnews/362551.htm
- http://m.wap.fcful.cn/nnews/4300.htm
- http://m.wap.fcful.cn/nnews/73729.htm
- http://m.wap.fcful.cn/nnews/40728.htm
- http://m.wap.fcful.cn/nnews/259491.htm
- http://m.wap.fcful.cn/nnews/28419.htm
- http://m.wap.fcful.cn/nnews/750303.htm
- http://m.wap.fcful.cn/nnews/5687806.htm
- http://m.wap.fcful.cn/nnews/98803.htm
- http://m.wap.fcful.cn/nnews/71545.htm
- http://m.wap.fcful.cn/nnews/57608.htm
- http://m.wap.fcful.cn/nnews/7175876.htm
- http://m.wap.fcful.cn/nnews/8773.htm
- http://m.wap.fcful.cn/nnews/22103.htm

## 项目结构

```
waplink-hub/
├── src/
│   ├── core/                     # 核心引擎模块
│   │   ├── fetcher.js            # 并发HTTP请求与重试逻辑
│   │   ├── parser.js             # 基于模板的内容抽取器
│   │   └── dedup.js              # URL归一化与布隆过滤器去重
│   ├── scheduler/                # 定时任务调度层
│   │   ├── cron.js               # 基于node-cron的轮询配置
│   │   └── worker.js             # 任务执行上下文与错误处理
│   ├── api/                      # RESTful接口实现
│   │   ├── routes/               # 按资源版本路由
│   │   └── middleware/           # 日志与限流中间件
│   ├── storage/                  # 数据持久化层
│   │   ├── sqlite.js             # 数据库初始化与CRUD操作
│   │   └── snapshot.js           # 快照归档与版本管理
│   └── ui/                       # 静态演示面板源文件
│       ├── index.html            # 主看板页面
│       └── app.js                # 前端状态管理与API调用
├── config/                       # 环境配置文件
│   ├── default.yaml              # 默认超时、并发数、重试策略
│   └── custom/                   # 用户自定义配置样例
├── docs/                         # 完整文档目录
├── tests/                        # 单元测试与集成测试
│   ├── fetcher.test.js
│   ├── parser.test.js
│   └── api.test.js
├── scripts/                      # 运维辅助脚本
│   ├── import-seed.js            # 导入初始资源列表
│   └── export-snapshot.js        # 导出指定日期的快照
├── resources/                    # 静态资源与种子数据
│   └── seed.txt                  # 包含全部250个初始链接
├── snapshots/                    # 自动生成的扫描历史快照
├── logs/                         # 应用日志与错误栈
├── package.json
├── Dockerfile
└── README.md
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆至本地开发环境。确保 Node.js 版本符合安装要求，运行 `npm install` 安装所有开发依赖。

2. 创建新的功能分支，分支命名遵循 `feature/简要描述` 或 `fix/问题编号` 格式。所有代码变更需通过 ESLint 检查，并补充对应的单元测试文件至 `tests/` 目录。

3. 若新增链接资源或修改已有种子列表，请同时更新 `resources/seed.txt` 并运行 `npm run validate-seed` 校验 URL 格式合法性。

4. 提交前执行 `npm run test` 确保全部测试用例通过，并撰写清晰的 commit message，说明变更动机与影响范围。

5. 发起 Pull Request 至主仓库的 `main` 分支，等待项目维护者审核。若涉及架构调整或新增依赖，请提前在 Issue 中讨论。

## 常见问题

**Q: 为什么资源列表中的链接无法全部访问？**

A: 移动 WAP 站点存在内容更新、临时下线或域名迁移的可能。本项目内置的链接检测模块会在首次运行时标记状态，并在后续定时任务中持续追踪。建议用户根据业务需要，定期运行 `npm run check-links` 生成最新存活报告，并剔除长期失效的条目。

**Q: 如何扩展摘要抽取规则以适配新的 WAP 页面结构？**

A: 您可以在 `config/custom/` 目录下创建新的模板文件，参照 `src/core/parser.js` 中已有的 XPath 示例进行配置。项目支持热加载模板，修改后无需重启服务即可生效。若需要更复杂的逻辑，可继承 `BaseParser` 类并注册至解析器工厂。

**Q: 项目是否支持多用户或多租户场景？**

A: 当前版本以单机单用户模式设计，未内置用户认证与权限管理。但 API 层已预留 `X-API-Key` 请求头拦截钩子，您可结合反向代理（如 Nginx）实现基础的访问控制。多租户数据隔离需自行扩展 `storage` 层，项目本身不提供此类高级特性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
