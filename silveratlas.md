# NavCentral

NavCentral 是一个轻量级、可自托管的网络资源导航与信息聚合系统，旨在为技术团队、内容研究者及信息管理人员提供一套结构清晰的外部链接管理与快速访问方案。项目定位于中大型外链集合的整理、归档与展示，特别适合需要批量维护外部参考链接、技术文档索引或新闻简报归档的场景。

项目核心价值在于将分散的、无结构的 URL 列表转化为具备分类视角、快速检索与状态可观测的集中式导航页。NavCentral 不依赖外部数据库，采用纯静态生成策略，可部署于任何支持 HTTP 服务的环境，同时保留动态过滤与标签筛选能力，便于用户在海量链接中精准定位目标内容。目标用户包括技术文档维护者、科研助理、运营编辑以及任何需要高频访问固定外链集合的从业人员。


## 功能概览

批量链接导入与自动规范化：支持从纯文本列表、CSV 或简易 JSON 格式批量导入 URL，系统自动完成去重、协议补全检测与格式校验，减少人工整理成本。

多维度标签分类体系：允许用户为每个链接赋予多个自定义标签，并基于标签组合进行快速筛选，支持层级分类结构，便于构建复杂知识体系。

全文检索与即时过滤：内置标题与摘要的模糊搜索能力，配合标签过滤器，实现毫秒级链接定位，无需逐页翻阅。

链接可用性健康检查：后台定时任务对已收录链接发起 HEAD 请求，标记异常状态码与响应超时记录，并在管理面板高亮展示失效链接。

响应式网格与列表双视图：提供卡片网格与紧凑列表两种展示模式，适配桌面端与移动端浏览习惯，用户可按需切换。

访问统计与点击追踪：记录每个链接的点击次数与最近访问时间，支持按热度排序，帮助识别高频使用资源。

数据导入导出与备份机制：支持完整数据导出为 JSON 或 CSV 格式，便于迁移、二次处理或版本回溯，同时内置自动备份功能。


## 应用场景

技术文档团队的外部参考库管理：技术写作人员与文档工程师可将大量 API 规范、第三方库文档、社区讨论帖等外链统一收录至 NavCentral，按技术领域或产品模块分类，并在编写过程中快速检索引用，避免重复查找与链接失效问题。

行业资讯与研究素材归档：研究员或市场分析人员可将每日阅读的行业报告、新闻分析、数据看板等链接集中存储，结合标签体系标注主题、日期与重要性，形成可追溯的研究素材库，支持后续复盘与报告撰写。

运营编辑的选题与内容源管理：内容运营团队可利用 NavCentral 维护选题参考源、竞品动态监测列表以及社交媒体热点链接，通过健康检查功能及时发现失效来源，确保内容跟进不中断。

个人开发者与极客的阅读清单整理：开发者可将技术博客、开源项目、在线工具、学习教程等分散链接统一收纳，借助检索与分类功能快速调取，打造个人专属的知识导航入口。


## 快速开始

以下步骤指导您在本地快速启动 NavCentral 开发或部署实例。

```bash
# 克隆项目仓库
git clone https://github.com/navcentral/navcentral.git

# 进入项目目录
cd navcentral

# 安装项目依赖（基于 Node.js 环境）
npm install

# 复制环境变量配置文件
cp .env.example .env

# 执行数据库初始化与种子数据填充
npm run setup

# 启动开发服务器，默认监听端口 3000
npm run dev
```

访问 http://localhost:3000 即可进入 NavCentral 主界面。生产环境部署请参考 `docs/deployment.md` 文档使用 `npm run build` 构建静态输出。


## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用最新 LTS 版本以获取完整特性支持 |
| npm | 9.x 或以上 | 包管理器，用于安装项目依赖及执行脚本命令 |
| SQLite3 | 系统内置（无需额外安装） | 默认嵌入式数据库，适用于单机部署与数据持久化 |
| Git | 2.30 或以上 | 版本控制工具，用于克隆仓库及拉取更新 |
| 操作系统 | Linux / macOS / Windows 10+ | 跨平台支持，Windows 建议使用 WSL2 环境以提升性能 |
| 内存 | 最低 512 MB，推荐 1 GB | 生产环境建议 2 GB 以上以支持健康检查并发任务 |
| 存储空间 | 最低 200 MB | 用于存放程序文件、数据库及日志，实际需求随链接数量增长 |


## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | /docs/user-guide/ | 如何使用分类、标签、检索与视图切换，以及日常操作流程 |
| 管理员手册 | /docs/admin/ | 链接批量导入、健康检查配置、用户权限管理与数据备份恢复 |
| 开发者文档 | /docs/developer/ | 项目架构、API 接口规范、插件扩展机制与前端构建流程 |
| 部署参考 | /docs/deployment/ | 生产环境构建、反向代理配置、HTTPS 启用与容器化部署方案 |
| 常见问题 | /docs/faq/ | 高频问题收录，涵盖安装报错、性能调优与数据迁移疑问 |
| 更新日志 | /CHANGELOG.md | 版本迭代记录、新功能说明、破坏性变更与废弃特性公告 |


## 资源列表

- http://m.3g.fcful.cn/snews/884912.htm
- http://m.3g.fcful.cn/snews/735814.htm
- http://m.3g.fcful.cn/snews/9723.htm
- http://m.3g.fcful.cn/snews/17213.htm
- http://m.3g.fcful.cn/snews/0110673.htm
- http://m.3g.fcful.cn/snews/117519.htm
- http://m.3g.fcful.cn/snews/0197153.htm
- http://m.3g.fcful.cn/snews/11833.htm
- http://m.3g.fcful.cn/snews/8077.htm
- http://m.3g.fcful.cn/snews/3587417.htm
- http://m.3g.fcful.cn/snews/0808.htm
- http://m.3g.fcful.cn/snews/8246.htm
- http://m.3g.fcful.cn/snews/5556927.htm
- http://m.3g.fcful.cn/snews/5144.htm
- http://m.3g.fcful.cn/snews/704219.htm
- http://m.3g.fcful.cn/snews/123146.htm
- http://m.3g.fcful.cn/snews/046772.htm
- http://m.3g.fcful.cn/snews/3605950.htm
- http://m.3g.fcful.cn/snews/0112948.htm
- http://m.3g.fcful.cn/snews/0082.htm
- http://m.3g.fcful.cn/snews/62562.htm
- http://m.3g.fcful.cn/snews/2658.htm
- http://m.3g.fcful.cn/snews/188293.htm
- http://m.3g.fcful.cn/snews/1317.htm
- http://m.3g.fcful.cn/snews/1567245.htm
- http://m.3g.fcful.cn/snews/37247.htm
- http://m.3g.fcful.cn/snews/7354.htm
- http://m.3g.fcful.cn/snews/2753985.htm
- http://m.3g.fcful.cn/snews/8108.htm
- http://m.3g.fcful.cn/snews/1363.htm
- http://m.3g.fcful.cn/snews/242499.htm
- http://m.3g.fcful.cn/snews/1663381.htm
- http://m.3g.fcful.cn/snews/47037.htm
- http://m.3g.fcful.cn/snews/679515.htm
- http://m.3g.fcful.cn/snews/8725.htm
- http://m.3g.fcful.cn/snews/754635.htm
- http://m.3g.fcful.cn/snews/494338.htm
- http://m.3g.fcful.cn/snews/3899.htm
- http://m.3g.fcful.cn/snews/03453.htm
- http://m.3g.fcful.cn/snews/916313.htm
- http://m.3g.fcful.cn/snews/532817.htm
- http://m.3g.fcful.cn/snews/088182.htm
- http://m.3g.fcful.cn/snews/63996.htm
- http://m.3g.fcful.cn/snews/9534838.htm
- http://m.3g.fcful.cn/snews/203405.htm
- http://m.3g.fcful.cn/snews/183408.htm
- http://m.3g.fcful.cn/snews/0284.htm
- http://m.3g.fcful.cn/snews/3559467.htm
- http://m.3g.fcful.cn/snews/6053.htm
- http://m.3g.fcful.cn/snews/340480.htm
- http://m.3g.fcful.cn/snews/79002.htm
- http://m.3g.fcful.cn/snews/576619.htm
- http://m.3g.fcful.cn/snews/8412.htm
- http://m.3g.fcful.cn/snews/3438148.htm
- http://m.3g.fcful.cn/snews/3786.htm
- http://m.3g.fcful.cn/snews/6344.htm
- http://m.3g.fcful.cn/snews/7531.htm
- http://m.3g.fcful.cn/snews/097165.htm
- http://m.3g.fcful.cn/snews/461208.htm
- http://m.3g.fcful.cn/snews/6292860.htm
- http://m.3g.fcful.cn/snews/52846.htm
- http://m.3g.fcful.cn/snews/0571462.htm
- http://m.3g.fcful.cn/snews/41466.htm
- http://m.3g.fcful.cn/snews/8375229.htm
- http://m.3g.fcful.cn/snews/19738.htm
- http://m.3g.fcful.cn/snews/29614.htm
- http://m.3g.fcful.cn/snews/577335.htm
- http://m.3g.fcful.cn/snews/80039.htm
- http://m.3g.fcful.cn/snews/6676721.htm
- http://m.3g.fcful.cn/snews/68957.htm
- http://m.3g.fcful.cn/snews/64659.htm
- http://m.3g.fcful.cn/snews/8167255.htm
- http://m.3g.fcful.cn/snews/1949022.htm
- http://m.3g.fcful.cn/snews/261260.htm
- http://m.3g.fcful.cn/snews/8284.htm
- http://m.3g.fcful.cn/snews/365884.htm
- http://m.3g.fcful.cn/snews/34793.htm
- http://m.3g.fcful.cn/snews/339712.htm
- http://m.3g.fcful.cn/snews/5909412.htm
- http://m.3g.fcful.cn/snews/93679.htm
- http://m.3g.fcful.cn/snews/47309.htm
- http://m.3g.fcful.cn/snews/0410007.htm
- http://m.3g.fcful.cn/snews/1839.htm
- http://m.3g.fcful.cn/snews/4085.htm
- http://m.3g.fcful.cn/snews/8193476.htm
- http://m.3g.fcful.cn/snews/1033012.htm
- http://m.3g.fcful.cn/snews/6486.htm
- http://m.3g.fcful.cn/snews/24733.htm
- http://m.3g.fcful.cn/snews/9685.htm
- http://m.3g.fcful.cn/snews/3849764.htm
- http://m.3g.fcful.cn/snews/6908145.htm
- http://m.3g.fcful.cn/snews/5715535.htm
- http://m.3g.fcful.cn/snews/94488.htm
- http://m.3g.fcful.cn/snews/2181.htm
- http://m.3g.fcful.cn/snews/86014.htm
- http://m.3g.fcful.cn/snews/856125.htm
- http://m.3g.fcful.cn/snews/6637.htm
- http://m.3g.fcful.cn/snews/0954.htm
- http://m.3g.fcful.cn/snews/17448.htm
- http://m.3g.fcful.cn/snews/55694.htm
- http://m.3g.fcful.cn/snews/523001.htm
- http://m.3g.fcful.cn/snews/18814.htm
- http://m.3g.fcful.cn/snews/0270.htm
- http://m.3g.fcful.cn/snews/9390895.htm
- http://m.3g.fcful.cn/snews/94993.htm
- http://m.3g.fcful.cn/snews/7441.htm
- http://m.3g.fcful.cn/snews/17072.htm
- http://m.3g.fcful.cn/snews/92806.htm
- http://m.3g.fcful.cn/snews/7026.htm
- http://m.3g.fcful.cn/snews/288816.htm
- http://m.3g.fcful.cn/snews/424414.htm
- http://m.3g.fcful.cn/snews/4465529.htm
- http://m.3g.fcful.cn/snews/628272.htm
- http://m.3g.fcful.cn/snews/57924.htm
- http://m.3g.fcful.cn/snews/8358.htm
- http://m.3g.fcful.cn/snews/88761.htm
- http://m.3g.fcful.cn/snews/00348.htm
- http://m.3g.fcful.cn/snews/6720393.htm
- http://m.3g.fcful.cn/snews/7002785.htm
- http://m.3g.fcful.cn/snews/3257227.htm
- http://m.3g.fcful.cn/snews/860981.htm
- http://m.3g.fcful.cn/snews/519652.htm
- http://m.3g.fcful.cn/snews/075207.htm
- http://m.3g.fcful.cn/snews/0561.htm
- http://m.3g.fcful.cn/snews/53525.htm
- http://m.3g.fcful.cn/snews/27346.htm
- http://m.3g.fcful.cn/snews/3727500.htm
- http://m.3g.fcful.cn/snews/98733.htm
- http://m.3g.fcful.cn/snews/219436.htm
- http://m.3g.fcful.cn/snews/026736.htm
- http://m.3g.fcful.cn/snews/8536.htm
- http://m.3g.fcful.cn/snews/7389.htm
- http://m.3g.fcful.cn/snews/8045.htm
- http://m.3g.fcful.cn/snews/77482.htm
- http://m.3g.fcful.cn/snews/6502411.htm
- http://m.3g.fcful.cn/snews/2714.htm
- http://m.3g.fcful.cn/snews/0998701.htm
- http://m.3g.fcful.cn/snews/192034.htm
- http://m.3g.fcful.cn/snews/64565.htm
- http://m.3g.fcful.cn/snews/09515.htm
- http://m.3g.fcful.cn/snews/7417.htm
- http://m.3g.fcful.cn/snews/505107.htm
- http://m.3g.fcful.cn/snews/61317.htm
- http://m.3g.fcful.cn/snews/9500118.htm
- http://m.3g.fcful.cn/snews/3309169.htm
- http://m.3g.fcful.cn/snews/7206906.htm
- http://m.3g.fcful.cn/snews/38754.htm
- http://m.3g.fcful.cn/snews/4398065.htm
- http://m.3g.fcful.cn/snews/4531828.htm
- http://m.3g.fcful.cn/snews/3182226.htm
- http://m.3g.fcful.cn/snews/2961.htm
- http://m.3g.fcful.cn/snews/75113.htm
- http://m.3g.fcful.cn/snews/554596.htm
- http://m.3g.fcful.cn/snews/838089.htm
- http://m.3g.fcful.cn/snews/3525.htm
- http://m.3g.fcful.cn/snews/92016.htm
- http://m.3g.fcful.cn/snews/041195.htm
- http://m.3g.fcful.cn/snews/40751.htm
- http://m.3g.fcful.cn/snews/352023.htm
- http://m.3g.fcful.cn/snews/9994.htm
- http://m.3g.fcful.cn/snews/1289677.htm
- http://m.3g.fcful.cn/snews/6536764.htm
- http://m.3g.fcful.cn/snews/268317.htm
- http://m.3g.fcful.cn/snews/4759.htm
- http://m.3g.fcful.cn/snews/135106.htm
- http://m.3g.fcful.cn/snews/9324130.htm
- http://m.3g.fcful.cn/snews/3617885.htm
- http://m.3g.fcful.cn/snews/9426446.htm
- http://m.3g.fcful.cn/snews/8552164.htm
- http://m.3g.fcful.cn/snews/0866.htm
- http://m.3g.fcful.cn/snews/5932.htm
- http://m.3g.fcful.cn/snews/236047.htm
- http://m.3g.fcful.cn/snews/1135258.htm
- http://m.3g.fcful.cn/snews/3237119.htm
- http://m.3g.fcful.cn/snews/2228.htm
- http://m.3g.fcful.cn/snews/9012684.htm
- http://m.3g.fcful.cn/snews/4683.htm
- http://m.3g.fcful.cn/snews/358423.htm
- http://m.3g.fcful.cn/snews/159078.htm
- http://m.3g.fcful.cn/snews/84490.htm
- http://m.3g.fcful.cn/snews/3033880.htm
- http://m.3g.fcful.cn/snews/5405.htm
- http://m.3g.fcful.cn/snews/5739.htm
- http://m.3g.fcful.cn/snews/4165014.htm
- http://m.3g.fcful.cn/snews/7580901.htm
- http://m.3g.fcful.cn/snews/92648.htm
- http://m.3g.fcful.cn/snews/9390.htm
- http://m.3g.fcful.cn/snews/284121.htm
- http://m.3g.fcful.cn/snews/222472.htm
- http://m.3g.fcful.cn/snews/24027.htm
- http://m.3g.fcful.cn/snews/4376.htm
- http://m.3g.fcful.cn/snews/21297.htm
- http://m.3g.fcful.cn/snews/2024.htm
- http://m.3g.fcful.cn/snews/4464960.htm
- http://m.3g.fcful.cn/snews/648437.htm
- http://m.3g.fcful.cn/snews/0415649.htm
- http://m.3g.fcful.cn/snews/912108.htm
- http://m.3g.fcful.cn/snews/7439.htm
- http://m.3g.fcful.cn/snews/827799.htm
- http://m.3g.fcful.cn/snews/8041.htm
- http://m.3g.fcful.cn/snews/02322.htm
- http://m.3g.fcful.cn/snews/0871774.htm
- http://m.3g.fcful.cn/snews/308777.htm
- http://m.3g.fcful.cn/snews/310298.htm
- http://m.3g.fcful.cn/snews/1390.htm
- http://m.3g.fcful.cn/snews/9771709.htm
- http://m.3g.fcful.cn/snews/12660.htm
- http://m.3g.fcful.cn/snews/33310.htm
- http://m.3g.fcful.cn/snews/0343418.htm
- http://m.3g.fcful.cn/snews/9674.htm
- http://m.3g.fcful.cn/snews/807226.htm
- http://m.3g.fcful.cn/snews/0122.htm
- http://m.3g.fcful.cn/snews/7359551.htm
- http://m.3g.fcful.cn/snews/7326.htm
- http://m.3g.fcful.cn/snews/2069.htm
- http://m.3g.fcful.cn/snews/8491.htm
- http://m.3g.fcful.cn/snews/3799.htm
- http://m.3g.fcful.cn/snews/3639132.htm
- http://m.3g.fcful.cn/snews/929907.htm
- http://m.3g.fcful.cn/snews/8183350.htm
- http://m.3g.fcful.cn/snews/4217053.htm
- http://m.3g.fcful.cn/snews/2134759.htm
- http://m.3g.fcful.cn/snews/590916.htm
- http://m.3g.fcful.cn/snews/534037.htm
- http://m.3g.fcful.cn/snews/23555.htm
- http://m.3g.fcful.cn/snews/8951.htm
- http://m.3g.fcful.cn/snews/876565.htm
- http://m.3g.fcful.cn/snews/130438.htm
- http://m.3g.fcful.cn/snews/3593.htm
- http://m.3g.fcful.cn/snews/3030488.htm
- http://m.3g.fcful.cn/snews/1431188.htm
- http://m.3g.fcful.cn/snews/62837.htm
- http://m.3g.fcful.cn/snews/48657.htm
- http://m.3g.fcful.cn/snews/552508.htm
- http://m.3g.fcful.cn/snews/5191179.htm
- http://m.3g.fcful.cn/snews/9122.htm
- http://m.3g.fcful.cn/snews/6336668.htm
- http://m.3g.fcful.cn/snews/2433.htm
- http://m.3g.fcful.cn/snews/8264.htm
- http://m.3g.fcful.cn/snews/82180.htm
- http://m.3g.fcful.cn/snews/7524423.htm
- http://m.3g.fcful.cn/snews/36351.htm
- http://m.3g.fcful.cn/snews/3577975.htm
- http://m.3g.fcful.cn/snews/5679.htm
- http://m.3g.fcful.cn/snews/75758.htm
- http://m.3g.fcful.cn/snews/2720565.htm
- http://m.3g.fcful.cn/snews/8563.htm
- http://m.3g.fcful.cn/snews/9687779.htm
- http://m.3g.fcful.cn/snews/624975.htm
- http://m.3g.fcful.cn/snews/171346.htm

## 项目结构

```
navcentral/
├── src/                           # 核心源代码目录
│   ├── api/                       # RESTful API 路由与控制器
│   │   ├── links.js               # 链接增删改查接口
│   │   ├── tags.js                # 标签管理接口
│   │   └── health.js              # 健康检查与状态上报接口
│   ├── core/                      # 核心业务逻辑层
│   │   ├── linker.js              # 链接解析、规范化与去重引擎
│   │   ├── scanner.js             # 批量导入与文件扫描处理器
│   │   └── checker.js             # 可用性探测与超时重试机制
│   ├── db/                        # 数据库模型与迁移脚本
│   │   ├── models/                # 数据表结构定义（Link, Tag, Click）
│   │   └── migrations/            # 版本化数据库变更脚本
│   ├── ui/                        # 前端界面组件与静态资源
│   │   ├── views/                 # EJS 模板页面（主页、详情、管理）
│   │   ├── static/                # CSS 样式、JavaScript 脚本与图片
│   │   └── components/            # 可复用的前端 UI 组件（筛选栏、卡片）
│   └── utils/                     # 通用工具函数与辅助库
│       ├── validator.js           # URL 格式校验与安全过滤
│       └── logger.js              # 日志分级记录与轮转配置
├── config/                        # 环境配置文件与常量定义
│   ├── default.json               # 默认配置项（端口、超时、分页大小）
│   └── production.json            # 生产环境覆盖配置
├── data/                          # 数据存储目录
│   ├── sqlite.db                  # SQLite 数据库文件（自动生成）
│   └── backups/                   # 定时备份存档目录
├── tests/                         # 单元测试与集成测试脚本
│   ├── unit/                      # 核心函数与工具类测试
│   └── integration/               # API 端到端测试与数据库操作测试
├── docs/                          # 项目文档（用户手册、开发者指南）
├── scripts/                       # 运维辅助脚本（备份、迁移、种子填充）
├── .env.example                   # 环境变量模板文件
├── package.json                   # Node.js 项目清单与依赖声明
├── README.md                      # 项目介绍与快速入门文档
└── LICENSE                        # MIT 许可证文本
```


## 贡献指南

提交问题报告与功能请求：请使用 GitHub Issues 模板详细描述复现步骤、预期行为与实际表现，对于功能请求需说明使用场景与预期收益。提交前请检索已有议题避免重复。

代码贡献流程：Fork 本仓库至个人账号，在 dev 分支基础上创建特性分支，遵循 ESLint 与 Prettier 代码规范，确保所有单元测试通过且新增功能附带对应测试用例。

提交信息规范：使用约定式提交格式，即 type(scope): subject 结构，类型包括 feat、fix、docs、style、refactor、perf、test、chore，scope 填写影响模块名称。

文档完善与翻译：欢迎补充或修订用户文档、API 注释及示例代码，文档变更需与代码变更保持同步，翻译工作请基于 en 目录下的原始文件进行。

社区行为准则：参与者需遵守贡献者公约，保持友善与专业，维护开放包容的协作环境，项目维护者保留对不当行为的处理权。


## 常见问题

问：导入大量链接时界面出现卡顿或超时，如何优化？

答：建议分批次导入，每批次不超过 200 条。同时可在环境变量中调整 NODE_MAX_OLD_SPACE_SIZE 增加内存限制，或使用命令行工具 `npm run import:batch -- --file=links.json --chunk=100` 进行后台批量处理。健康检查功能建议在低峰时段启用，避免并发请求过多影响主线程响应。

问：SQLite 数据库是否支持多进程或多服务器部署？

答：SQLite 默认不支持高并发写入场景下的多进程访问。对于多实例部署或分布式环境，推荐将数据源切换为 PostgreSQL，项目已提供 `config/database.pg.js` 配置文件模板，修改数据库连接串后重启服务即可完成迁移。单机多进程场景建议使用 pkg 打包为独立进程并启用读写锁。

问：如何自定义链接卡片展示的元信息字段？

答：编辑 `src/ui/views/partials/link-card.ejs` 模板文件，可增删显示的字段，包括标题、描述、标签、最后检查时间等。若需新增自定义字段，需同步修改 `src/db/models/Link.js` 中的 schema 定义，并执行数据库迁移脚本 `npm run migrate:add-field -- --name=custom_field`。


## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
