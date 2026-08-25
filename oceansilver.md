# XNews 移动端资讯聚合平台

XNews 是一个面向移动端的内容聚合与导航系统，专注于从特定信息源采集、整理和展示结构化新闻数据。该项目为开发者、数据分析师和信息爱好者提供了一套轻量级的内容索引框架，通过预定义的资源定位符集合，实现对目标站点的定向内容抓取与展示。项目定位为技术验证型信息枢纽，不涉及内容存储与二次分发，仅提供公开可访问资源的组织化导航服务。

## 功能概览

**多源内容索引**：系统内置超过两百个经过验证的内容定位符，覆盖多个资讯分类维度，支持按批次、按来源进行内容聚合展示。

**移动端适配视图**：前端展示层针对移动设备屏幕尺寸进行优化，采用响应式布局策略，确保在手机和平板设备上获得一致的浏览体验。

**批次化资源管理**：采用分批导入机制，当前批次为第152/240批，总计管理250个独立资源链接，支持批次间的切换与筛选。

**结构化数据解析**：对目标页面进行元数据提取，包括标题、发布时间、正文摘要等关键字段，输出为统一的JSON格式数据结构。

**离线缓存机制**：客户端支持对已访问内容进行本地缓存，减少重复网络请求，提升弱网环境下的可用性。

**定时更新触发器**：后端集成定时任务调度器，按预设频率自动检测目标资源的状态变更，确保导航链接的有效性。

## 应用场景

**移动端资讯快速浏览**：用户通过手机浏览器访问XNews聚合页面，无需逐一打开各新闻站点，即可在统一界面中浏览来自多个来源的资讯标题和摘要，大幅提升信息获取效率。

**内容可用性监控**：运维人员利用XNews的链接状态检测功能，定期验证资源列表中各URL的可访问性，及时发现失效链接并生成报告，便于上游数据源维护。

**数据分析样本采集**：数据研究人员将XNews作为样本入口，批量获取特定域名的页面结构特征，用于构建内容分类模型或进行网络信息分布规律的研究。

**嵌入式信息组件**：开发者在自有移动应用或小程序中嵌入XNews的轻量级数据接口，将外部资讯内容作为补充信息模块展示，丰富自身产品的信息维度。

## 快速开始

以下指令适用于Linux/macOS环境，Windows用户建议使用WSL或Git Bash执行。

```bash
# 克隆项目仓库
git clone https://github.com/xnews-aggregator/xnews-platform.git

# 进入项目目录
cd xnews-platform

# 安装项目依赖（使用npm）
npm install

# 启动开发服务器（默认监听端口3000）
npm run dev
```

生产环境部署请参考 `docs/deployment.md` 文档，使用 `npm run build` 构建静态资源，并通过 `pm2 start ecosystem.config.js` 启动持久化服务。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 运行时环境，建议使用LTS版本 |
| npm | >= 9.0.0 | 包管理器，用于安装项目依赖 |
| SQLite3 | >= 3.40.0 | 内置数据库，用于资源状态记录 |
| PM2 | >= 5.0.0 | 生产环境进程守护（可选，开发环境可忽略） |
| Nginx | >= 1.20.0 | 反向代理与静态资源服务（生产环境推荐） |
| Git | >= 2.30.0 | 版本控制工具，用于克隆和更新代码 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建开发环境并进行首次内容加载 |
| 架构设计 | docs/architecture.md | 项目的整体模块划分、数据流走向和扩展点设计 |
| API参考 | docs/api-reference.md | 后端提供的RESTful接口定义、请求参数与返回示例 |
| 部署运维 | docs/deployment.md | 生产环境部署步骤、配置参数调优和监控方案 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/9739.htm
- http://m.3g.gqskj.cn/xnews/65483.htm
- http://m.3g.gqskj.cn/xnews/3889963.htm
- http://m.3g.gqskj.cn/xnews/6823810.htm
- http://m.3g.gqskj.cn/xnews/413926.htm
- http://m.3g.gqskj.cn/xnews/300290.htm
- http://m.3g.gqskj.cn/xnews/760958.htm
- http://m.3g.gqskj.cn/xnews/56198.htm
- http://m.3g.gqskj.cn/xnews/0552.htm
- http://m.3g.gqskj.cn/xnews/240714.htm
- http://m.3g.gqskj.cn/xnews/958987.htm
- http://m.3g.gqskj.cn/xnews/5243992.htm
- http://m.3g.gqskj.cn/xnews/6533.htm
- http://m.3g.gqskj.cn/xnews/842568.htm
- http://m.3g.gqskj.cn/xnews/5424.htm
- http://m.3g.gqskj.cn/xnews/505728.htm
- http://m.3g.gqskj.cn/xnews/3109559.htm
- http://m.3g.gqskj.cn/xnews/5010670.htm
- http://m.3g.gqskj.cn/xnews/911163.htm
- http://m.3g.gqskj.cn/xnews/0051133.htm
- http://m.3g.gqskj.cn/xnews/3264939.htm
- http://m.3g.gqskj.cn/xnews/90859.htm
- http://m.3g.gqskj.cn/xnews/8331131.htm
- http://m.3g.gqskj.cn/xnews/88049.htm
- http://m.3g.gqskj.cn/xnews/8286.htm
- http://m.3g.gqskj.cn/xnews/3501767.htm
- http://m.3g.gqskj.cn/xnews/2347.htm
- http://m.3g.gqskj.cn/xnews/0565545.htm
- http://m.3g.gqskj.cn/xnews/9981.htm
- http://m.3g.gqskj.cn/xnews/197556.htm
- http://m.3g.gqskj.cn/xnews/87394.htm
- http://m.3g.gqskj.cn/xnews/04158.htm
- http://m.3g.gqskj.cn/xnews/7653.htm
- http://m.3g.gqskj.cn/xnews/764678.htm
- http://m.3g.gqskj.cn/xnews/1889004.htm
- http://m.3g.gqskj.cn/xnews/31519.htm
- http://m.3g.gqskj.cn/xnews/107582.htm
- http://m.3g.gqskj.cn/xnews/5676773.htm
- http://m.3g.gqskj.cn/xnews/6753.htm
- http://m.3g.gqskj.cn/xnews/8383.htm
- http://m.3g.gqskj.cn/xnews/4070399.htm
- http://m.3g.gqskj.cn/xnews/5903.htm
- http://m.3g.gqskj.cn/xnews/1505942.htm
- http://m.3g.gqskj.cn/xnews/38331.htm
- http://m.3g.gqskj.cn/xnews/20221.htm
- http://m.3g.gqskj.cn/xnews/43506.htm
- http://m.3g.gqskj.cn/xnews/5352.htm
- http://m.3g.gqskj.cn/xnews/74820.htm
- http://m.3g.gqskj.cn/xnews/4658087.htm
- http://m.3g.gqskj.cn/xnews/4835290.htm
- http://m.3g.gqskj.cn/xnews/8107.htm
- http://m.3g.gqskj.cn/xnews/1202.htm
- http://m.3g.gqskj.cn/xnews/760923.htm
- http://m.3g.gqskj.cn/xnews/02795.htm
- http://m.3g.gqskj.cn/xnews/8620086.htm
- http://m.3g.gqskj.cn/xnews/5025.htm
- http://m.3g.gqskj.cn/xnews/0145.htm
- http://m.3g.gqskj.cn/xnews/7762729.htm
- http://m.3g.gqskj.cn/xnews/54592.htm
- http://m.3g.gqskj.cn/xnews/4260.htm
- http://m.3g.gqskj.cn/xnews/82004.htm
- http://m.3g.gqskj.cn/xnews/4477122.htm
- http://m.3g.gqskj.cn/xnews/167034.htm
- http://m.3g.gqskj.cn/xnews/893888.htm
- http://m.3g.gqskj.cn/xnews/098796.htm
- http://m.3g.gqskj.cn/xnews/4024830.htm
- http://m.3g.gqskj.cn/xnews/7056.htm
- http://m.3g.gqskj.cn/xnews/4508.htm
- http://m.3g.gqskj.cn/xnews/770731.htm
- http://m.3g.gqskj.cn/xnews/835797.htm
- http://m.3g.gqskj.cn/xnews/8496.htm
- http://m.3g.gqskj.cn/xnews/73481.htm
- http://m.3g.gqskj.cn/xnews/64113.htm
- http://m.3g.gqskj.cn/xnews/32421.htm
- http://m.3g.gqskj.cn/xnews/6019.htm
- http://m.3g.gqskj.cn/xnews/81043.htm
- http://m.3g.gqskj.cn/xnews/112248.htm
- http://m.3g.gqskj.cn/xnews/2295376.htm
- http://m.3g.gqskj.cn/xnews/33868.htm
- http://m.3g.gqskj.cn/xnews/5630663.htm
- http://m.3g.gqskj.cn/xnews/1299.htm
- http://m.3g.gqskj.cn/xnews/3794534.htm
- http://m.3g.gqskj.cn/xnews/462047.htm
- http://m.3g.gqskj.cn/xnews/47186.htm
- http://m.3g.gqskj.cn/xnews/92478.htm
- http://m.3g.gqskj.cn/xnews/87728.htm
- http://m.3g.gqskj.cn/xnews/7665.htm
- http://m.3g.gqskj.cn/xnews/1452341.htm
- http://m.3g.gqskj.cn/xnews/7218.htm
- http://m.3g.gqskj.cn/xnews/543831.htm
- http://m.3g.gqskj.cn/xnews/8881.htm
- http://m.3g.gqskj.cn/xnews/32239.htm
- http://m.3g.gqskj.cn/xnews/0026.htm
- http://m.3g.gqskj.cn/xnews/494216.htm
- http://m.3g.gqskj.cn/xnews/3288.htm
- http://m.3g.gqskj.cn/xnews/35520.htm
- http://m.3g.gqskj.cn/xnews/433216.htm
- http://m.3g.gqskj.cn/xnews/926299.htm
- http://m.3g.gqskj.cn/xnews/3138.htm
- http://m.3g.gqskj.cn/xnews/782408.htm
- http://m.3g.gqskj.cn/xnews/387647.htm
- http://m.3g.gqskj.cn/xnews/0750911.htm
- http://m.3g.gqskj.cn/xnews/1253.htm
- http://m.3g.gqskj.cn/xnews/7436.htm
- http://m.3g.gqskj.cn/xnews/586651.htm
- http://m.3g.gqskj.cn/xnews/7122.htm
- http://m.3g.gqskj.cn/xnews/57719.htm
- http://m.3g.gqskj.cn/xnews/31433.htm
- http://m.3g.gqskj.cn/xnews/458623.htm
- http://m.3g.gqskj.cn/xnews/72721.htm
- http://m.3g.gqskj.cn/xnews/986081.htm
- http://m.3g.gqskj.cn/xnews/699244.htm
- http://m.3g.gqskj.cn/xnews/77356.htm
- http://m.3g.gqskj.cn/xnews/49155.htm
- http://m.3g.gqskj.cn/xnews/6224352.htm
- http://m.3g.gqskj.cn/xnews/814949.htm
- http://m.3g.gqskj.cn/xnews/8374429.htm
- http://m.3g.gqskj.cn/xnews/855290.htm
- http://m.3g.gqskj.cn/xnews/0294768.htm
- http://m.3g.gqskj.cn/xnews/774621.htm
- http://m.3g.gqskj.cn/xnews/04207.htm
- http://m.3g.gqskj.cn/xnews/19088.htm
- http://m.3g.gqskj.cn/xnews/3954082.htm
- http://m.3g.gqskj.cn/xnews/744642.htm
- http://m.3g.gqskj.cn/xnews/5156.htm
- http://m.3g.gqskj.cn/xnews/02603.htm
- http://m.3g.gqskj.cn/xnews/6906.htm
- http://m.3g.gqskj.cn/xnews/46484.htm
- http://m.3g.gqskj.cn/xnews/9131689.htm
- http://m.3g.gqskj.cn/xnews/3155196.htm
- http://m.3g.gqskj.cn/xnews/844261.htm
- http://m.3g.gqskj.cn/xnews/52411.htm
- http://m.3g.gqskj.cn/xnews/2455768.htm
- http://m.3g.gqskj.cn/xnews/3976834.htm
- http://m.3g.gqskj.cn/xnews/59701.htm
- http://m.3g.gqskj.cn/xnews/6585.htm
- http://m.3g.gqskj.cn/xnews/19337.htm
- http://m.3g.gqskj.cn/xnews/3630323.htm
- http://m.3g.gqskj.cn/xnews/319893.htm
- http://m.3g.gqskj.cn/xnews/1510115.htm
- http://m.3g.gqskj.cn/xnews/73301.htm
- http://m.3g.gqskj.cn/xnews/5018402.htm
- http://m.3g.gqskj.cn/xnews/254531.htm
- http://m.3g.gqskj.cn/xnews/473975.htm
- http://m.3g.gqskj.cn/xnews/2260675.htm
- http://m.3g.gqskj.cn/xnews/40404.htm
- http://m.3g.gqskj.cn/xnews/1369777.htm
- http://m.3g.gqskj.cn/xnews/764925.htm
- http://m.3g.gqskj.cn/xnews/81566.htm
- http://m.3g.gqskj.cn/xnews/4254.htm
- http://m.3g.gqskj.cn/xnews/0267.htm
- http://m.3g.gqskj.cn/xnews/5600184.htm
- http://m.3g.gqskj.cn/xnews/1032598.htm
- http://m.3g.gqskj.cn/xnews/4582.htm
- http://m.3g.gqskj.cn/xnews/6927.htm
- http://m.3g.gqskj.cn/xnews/1515.htm
- http://m.3g.gqskj.cn/xnews/9186.htm
- http://m.3g.gqskj.cn/xnews/045559.htm
- http://m.3g.gqskj.cn/xnews/0422.htm
- http://m.3g.gqskj.cn/xnews/8032147.htm
- http://m.3g.gqskj.cn/xnews/165560.htm
- http://m.3g.gqskj.cn/xnews/2374.htm
- http://m.3g.gqskj.cn/xnews/712728.htm
- http://m.3g.gqskj.cn/xnews/331394.htm
- http://m.3g.gqskj.cn/xnews/57016.htm
- http://m.3g.gqskj.cn/xnews/2649757.htm
- http://m.3g.gqskj.cn/xnews/4571.htm
- http://m.3g.gqskj.cn/xnews/4037.htm
- http://m.3g.gqskj.cn/xnews/61402.htm
- http://m.3g.gqskj.cn/xnews/70768.htm
- http://m.3g.gqskj.cn/xnews/7392.htm
- http://m.3g.gqskj.cn/xnews/16567.htm
- http://m.3g.gqskj.cn/xnews/549830.htm
- http://m.3g.gqskj.cn/xnews/862805.htm
- http://m.3g.gqskj.cn/xnews/8498449.htm
- http://m.3g.gqskj.cn/xnews/534024.htm
- http://m.3g.gqskj.cn/xnews/9054616.htm
- http://m.3g.gqskj.cn/xnews/4430.htm
- http://m.3g.gqskj.cn/xnews/08386.htm
- http://m.3g.gqskj.cn/xnews/791080.htm
- http://m.3g.gqskj.cn/xnews/460173.htm
- http://m.3g.gqskj.cn/xnews/08753.htm
- http://m.3g.gqskj.cn/xnews/6168.htm
- http://m.3g.gqskj.cn/xnews/7150033.htm
- http://m.3g.gqskj.cn/xnews/1028705.htm
- http://m.3g.gqskj.cn/xnews/4279.htm
- http://m.3g.gqskj.cn/xnews/7639641.htm
- http://m.3g.gqskj.cn/xnews/655458.htm
- http://m.3g.gqskj.cn/xnews/898239.htm
- http://m.3g.gqskj.cn/xnews/3192345.htm
- http://m.3g.gqskj.cn/xnews/068785.htm
- http://m.3g.gqskj.cn/xnews/83685.htm
- http://m.3g.gqskj.cn/xnews/232993.htm
- http://m.3g.gqskj.cn/xnews/3324743.htm
- http://m.3g.gqskj.cn/xnews/020394.htm
- http://m.3g.gqskj.cn/xnews/1478485.htm
- http://m.3g.gqskj.cn/xnews/777913.htm
- http://m.3g.gqskj.cn/xnews/394542.htm
- http://m.3g.gqskj.cn/xnews/43173.htm
- http://m.3g.gqskj.cn/xnews/4479712.htm
- http://m.3g.gqskj.cn/xnews/9485255.htm
- http://m.3g.gqskj.cn/xnews/902038.htm
- http://m.3g.gqskj.cn/xnews/2215187.htm
- http://m.3g.gqskj.cn/xnews/4473229.htm
- http://m.3g.gqskj.cn/xnews/06941.htm
- http://m.3g.gqskj.cn/xnews/76757.htm
- http://m.3g.gqskj.cn/xnews/71288.htm
- http://m.3g.gqskj.cn/xnews/775123.htm
- http://m.3g.gqskj.cn/xnews/8033.htm
- http://m.3g.gqskj.cn/xnews/470892.htm
- http://m.3g.gqskj.cn/xnews/79583.htm
- http://m.3g.gqskj.cn/xnews/276182.htm
- http://m.3g.gqskj.cn/xnews/70181.htm
- http://m.3g.gqskj.cn/xnews/8395.htm
- http://m.3g.gqskj.cn/xnews/480300.htm
- http://m.3g.gqskj.cn/xnews/06744.htm
- http://m.3g.gqskj.cn/xnews/1260.htm
- http://m.3g.gqskj.cn/xnews/1777340.htm
- http://m.3g.gqskj.cn/xnews/8617.htm
- http://m.3g.gqskj.cn/xnews/31293.htm
- http://m.3g.gqskj.cn/xnews/057948.htm
- http://m.3g.gqskj.cn/xnews/2370.htm
- http://m.3g.gqskj.cn/xnews/9934.htm
- http://m.3g.gqskj.cn/xnews/398909.htm
- http://m.3g.gqskj.cn/xnews/4838.htm
- http://m.3g.gqskj.cn/xnews/2929342.htm
- http://m.3g.gqskj.cn/xnews/20301.htm
- http://m.3g.gqskj.cn/xnews/09637.htm
- http://m.3g.gqskj.cn/xnews/6780237.htm
- http://m.3g.gqskj.cn/xnews/158935.htm
- http://m.3g.gqskj.cn/xnews/3795286.htm
- http://m.3g.gqskj.cn/xnews/5951387.htm
- http://m.3g.gqskj.cn/xnews/929280.htm
- http://m.3g.gqskj.cn/xnews/773997.htm
- http://m.3g.gqskj.cn/xnews/1018166.htm
- http://m.3g.gqskj.cn/xnews/0453.htm
- http://m.3g.gqskj.cn/xnews/2354.htm
- http://m.3g.gqskj.cn/xnews/098049.htm
- http://m.3g.gqskj.cn/xnews/5583169.htm
- http://m.3g.gqskj.cn/xnews/7516038.htm
- http://m.3g.gqskj.cn/xnews/6614.htm
- http://m.3g.gqskj.cn/xnews/5596065.htm
- http://m.3g.gqskj.cn/xnews/5770.htm
- http://m.3g.gqskj.cn/xnews/39986.htm
- http://m.3g.gqskj.cn/xnews/856425.htm
- http://m.3g.gqskj.cn/xnews/9122850.htm
- http://m.3g.gqskj.cn/xnews/600103.htm
- http://m.3g.gqskj.cn/xnews/0807631.htm
- http://m.3g.gqskj.cn/xnews/17523.htm
- http://m.3g.gqskj.cn/xnews/4981.htm

## 项目结构

```
xnews-platform/
├── src/
│   ├── core/                     # 核心功能模块
│   │   ├── fetcher.js            # HTTP请求封装与重试策略
│   │   ├── parser.js             # HTML内容解析与元数据提取
│   │   └── cache.js              # 内存与磁盘双层缓存管理
│   ├── routes/                   # 路由定义层
│   │   ├── api.js                # RESTful API端点实现
│   │   └── web.js                # 服务端渲染页面路由
│   ├── services/                 # 业务逻辑服务层
│   │   ├── aggregator.js         # 多源内容聚合调度服务
│   │   ├── validator.js          # 链接状态验证与健康检查
│   │   └── scheduler.js          # 定时任务编排与执行
│   ├── models/                   # 数据模型定义
│   │   ├── resource.js           # 资源链接实体模型
│   │   └── batch.js              # 批次记录与进度追踪模型
│   └── utils/                    # 通用工具函数集
│       ├── logger.js             # 分级日志记录工具
│       └── config.js             # 环境变量与配置加载
├── public/                       # 前端静态资源目录
│   ├── css/                      # 样式表文件
│   ├── js/                       # 客户端JavaScript脚本
│   └── assets/                   # 图片、字体等静态资产
├── docs/                         # 项目文档目录
├── tests/                        # 单元测试与集成测试
├── scripts/                      # 运维辅助脚本
├── .env.example                  # 环境变量配置模板
├── package.json                  # 项目依赖清单
└── README.md                     # 项目说明文档
```

## 贡献指南

1. 在GitHub Issues中查阅现有任务列表，选择未被认领且与自身技能匹配的任务，或提交新需求说明等待审核。
2. 从主分支派生个人副本，创建以 `feature/` 或 `fix/` 为前缀的功能分支，遵循语义化命名规范。
3. 编写或修改代码时，确保通过全部现有单元测试，并为新增功能补充对应的测试用例，覆盖率不低于85%。
4. 提交前执行 `npm run lint` 和 `npm run format` 统一代码风格，提交信息采用 `类型(范围): 简短描述` 格式。
5. 向主分支发起合并请求，至少获得一名核心维护者的代码审查批准后，由项目维护者执行合并操作。

## 常见问题

**Q: 启动服务后，资源列表无法加载任何数据，应如何排查？**

A: 请依次检查以下环节：确认网络环境能够正常访问 `m.3g.gqskj.cn` 域名；检查 `.env` 文件中 `FETCH_TIMEOUT` 和 `MAX_RETRIES` 参数是否合理；查看服务日志 `logs/error.log` 中是否有超时或连接拒绝记录；使用 `npm run validate` 命令手动验证单个链接状态。

**Q: 项目是否支持添加自定义资源来源，而不局限于预设列表？**

A: 支持。在 `src/config/sources.js` 中定义新的来源对象，包含 `domain` 和 `pathPattern` 字段，然后运行 `npm run migrate` 更新数据库结构。新增来源的资源会由调度器自动纳入后续抓取队列。注意自定义来源需符合项目的内容采集规范，不得违反目标站点的 robots.txt 约定。

**Q: 定时任务未能按预期时间触发，可能的原因是什么？**

A: 首先确认服务器时区设置与 `SCHEDULER_TIMEZONE` 环境变量一致；检查 PM2 进程是否处于正常运行状态；查看 `scheduler.log` 中是否有未捕获的异常堆栈；如果使用 SQLite 作为任务队列存储，需确保数据库文件具有读写权限且磁盘剩余空间充足。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:50
