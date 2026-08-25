# WebIndex 移动端资讯聚合索引

WebIndex 是一个面向移动端资讯聚合场景的轻量级索引网关项目，专注于将分散的新闻资讯内容通过统一的索引层进行组织与呈现。项目定位于为中小型内容平台、个人站长以及移动端应用开发者提供一套开箱即用的资讯外链索引管理方案，解决移动端环境下内容发现效率低、外链管理混乱、索引更新滞后等核心问题。

项目本身不存储任何原始内容，而是通过对结构化外链的收集、分类与时效性标记，帮助用户在最短时间内定位到所需信息源。WebIndex 适用于日活一万以下的轻量级内容站点，也支持作为个人知识库的外链补充模块嵌入现有系统。

## 功能概览

**移动端自适应索引展示** 针对移动屏幕尺寸优化索引列表渲染，支持触屏滑动与点击跳转，无需额外适配。

**按批次分类的资源聚合** 以批次为单位对资讯外链进行分组管理，当前为第 153/240 批，便于追溯与增量更新。

**裸链接直出模式** 所有外链以原始 URL 形式呈现，不经过重定向或中间页跳转，确保访问路径最短。

**基础元信息抽取** 自动解析目标页面的标题与摘要信息，供索引列表展示，减少用户点击试错成本。

**定时索引刷新机制** 支持按小时或天级别的定时任务触发外链可用性检查，自动标记失效链接。

**访问统计与热度标记** 记录每条外链的点击次数，按热度对索引项进行排序，优先展示高频访问资源。

**标签分类过滤** 允许为每条外链打上最多三个自定义标签，支持按标签组合筛选索引列表。

**导出与备份功能** 支持将当前批次索引导出为 JSON 或 CSV 格式，便于迁移或离线分析。

## 应用场景

**移动端资讯聚合站点** 面向手机端用户的轻量级新闻聚合网站，利用 WebIndex 将分散的新闻外链按批次整理为索引目录，用户通过浏览索引标题即可快速判断内容相关性，点击直接跳转至原始新闻页面，极大缩短信息检索路径。

**个人知识库外链管理模块** 知识管理爱好者使用 WebIndex 作为其个人维基站点的外链补充模块，将日常阅读中积累的参考文章、技术文档、行业报告等外链资源按批次归档，配合标签分类实现快速回溯。

**内容平台的推荐流补充** 中小型内容平台在算法推荐流之外嵌入 WebIndex 的索引区块，以人工筛选或半自动化的方式为用户提供高质量的外部资讯入口，丰富平台内容生态的同时降低内容审核成本。

**运营活动资讯汇集页** 企业运营团队利用 WebIndex 快速搭建短期活动相关的资讯汇集页，将活动中涉及的媒体报道、用户生成内容、官方公告等外链统一收纳，活动结束后直接归档为历史批次。

**开发者文档的外部参考索引** 开源项目或技术产品的文档站点使用 WebIndex 整理外部参考链接，包括相关论文、技术博客、视频教程等，帮助用户在学习产品的同时获得更广阔的技术上下文。

## 快速开始

以下步骤指导您在本地环境快速启动 WebIndex 服务。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git

# 进入项目目录
cd webindex

# 安装项目依赖（使用 npm）
npm install

# 配置环境变量（复制示例配置并修改）
cp .env.example .env

# 初始化数据库（SQLite）
npm run db:init

# 导入当前批次索引数据
npm run import -- --batch=153

# 启动开发服务器
npm run dev
```

访问 `http://localhost:3000` 即可查看索引首页。生产环境部署请参考文档导航中的部署指南。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 | 包管理器，用于安装项目依赖 |
| SQLite | 3.0 内置 | 默认数据库引擎，无需额外安装，生产环境可切换至 PostgreSQL |
| Redis | >= 6.0（可选） | 用于缓存与会话存储，非必需但推荐 |
| Nginx | >= 1.20（生产推荐） | 反向代理与静态资源服务，生产环境部署建议使用 |
| PM2 | >= 5.0（生产推荐） | Node.js 进程管理，保障服务持续运行 |
| Git | >= 2.30 | 版本控制工具，用于克隆与更新项目 |
| curl / wget | 任意版本 | 用于外链可用性检查脚本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `/docs/quick-start.md` | 如何在一小时内完成部署并导入第一批索引数据 |
| 部署手册 | `/docs/deployment.md` | 生产环境如何配置 Nginx、PM2 与 PostgreSQL 集群 |
| API 参考 | `/docs/api-reference.md` | 索引查询、批次管理、统计接口的请求与响应格式 |
| 运维指南 | `/docs/operations.md` | 定时任务配置、日志轮转、备份恢复与性能调优 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/22377.htm
- http://m.3g.gqskj.cn/xnews/509276.htm
- http://m.3g.gqskj.cn/xnews/42435.htm
- http://m.3g.gqskj.cn/xnews/1846359.htm
- http://m.3g.gqskj.cn/xnews/90294.htm
- http://m.3g.gqskj.cn/xnews/329710.htm
- http://m.3g.gqskj.cn/xnews/807994.htm
- http://m.3g.gqskj.cn/xnews/954493.htm
- http://m.3g.gqskj.cn/xnews/95389.htm
- http://m.3g.gqskj.cn/xnews/692911.htm
- http://m.3g.gqskj.cn/xnews/7426788.htm
- http://m.3g.gqskj.cn/xnews/23706.htm
- http://m.3g.gqskj.cn/xnews/18650.htm
- http://m.3g.gqskj.cn/xnews/7749.htm
- http://m.3g.gqskj.cn/xnews/36227.htm
- http://m.3g.gqskj.cn/xnews/58410.htm
- http://m.3g.gqskj.cn/xnews/1229773.htm
- http://m.3g.gqskj.cn/xnews/55455.htm
- http://m.3g.gqskj.cn/xnews/8729.htm
- http://m.3g.gqskj.cn/xnews/1212.htm
- http://m.3g.gqskj.cn/xnews/8434498.htm
- http://m.3g.gqskj.cn/xnews/63181.htm
- http://m.3g.gqskj.cn/xnews/977667.htm
- http://m.3g.gqskj.cn/xnews/3219.htm
- http://m.3g.gqskj.cn/xnews/1192.htm
- http://m.3g.gqskj.cn/xnews/7701.htm
- http://m.3g.gqskj.cn/xnews/714111.htm
- http://m.3g.gqskj.cn/xnews/39008.htm
- http://m.3g.gqskj.cn/xnews/45762.htm
- http://m.3g.gqskj.cn/xnews/067670.htm
- http://m.3g.gqskj.cn/xnews/9152.htm
- http://m.3g.gqskj.cn/xnews/9811.htm
- http://m.3g.gqskj.cn/xnews/1531.htm
- http://m.3g.gqskj.cn/xnews/6472.htm
- http://m.3g.gqskj.cn/xnews/9893955.htm
- http://m.3g.gqskj.cn/xnews/2910059.htm
- http://m.3g.gqskj.cn/xnews/4372616.htm
- http://m.3g.gqskj.cn/xnews/1812615.htm
- http://m.3g.gqskj.cn/xnews/9725.htm
- http://m.3g.gqskj.cn/xnews/090649.htm
- http://m.3g.gqskj.cn/xnews/97665.htm
- http://m.3g.gqskj.cn/xnews/5065.htm
- http://m.3g.gqskj.cn/xnews/2178003.htm
- http://m.3g.gqskj.cn/xnews/622401.htm
- http://m.3g.gqskj.cn/xnews/0712704.htm
- http://m.3g.gqskj.cn/xnews/0590.htm
- http://m.3g.gqskj.cn/xnews/51642.htm
- http://m.3g.gqskj.cn/xnews/99210.htm
- http://m.3g.gqskj.cn/xnews/8717024.htm
- http://m.3g.gqskj.cn/xnews/1956.htm
- http://m.3g.gqskj.cn/xnews/6985309.htm
- http://m.3g.gqskj.cn/xnews/2377709.htm
- http://m.3g.gqskj.cn/xnews/0811931.htm
- http://m.3g.gqskj.cn/xnews/4653.htm
- http://m.3g.gqskj.cn/xnews/0960.htm
- http://m.3g.gqskj.cn/xnews/7285985.htm
- http://m.3g.gqskj.cn/xnews/4184.htm
- http://m.3g.gqskj.cn/xnews/847683.htm
- http://m.3g.gqskj.cn/xnews/5537.htm
- http://m.3g.gqskj.cn/xnews/6746.htm
- http://m.3g.gqskj.cn/xnews/264323.htm
- http://m.3g.gqskj.cn/xnews/04476.htm
- http://m.3g.gqskj.cn/xnews/0194766.htm
- http://m.3g.gqskj.cn/xnews/9175.htm
- http://m.3g.gqskj.cn/xnews/395368.htm
- http://m.3g.gqskj.cn/xnews/331305.htm
- http://m.3g.gqskj.cn/xnews/7855759.htm
- http://m.3g.gqskj.cn/xnews/109043.htm
- http://m.3g.gqskj.cn/xnews/2437607.htm
- http://m.3g.gqskj.cn/xnews/67556.htm
- http://m.3g.gqskj.cn/xnews/9243357.htm
- http://m.3g.gqskj.cn/xnews/6537533.htm
- http://m.3g.gqskj.cn/xnews/29236.htm
- http://m.3g.gqskj.cn/xnews/29176.htm
- http://m.3g.gqskj.cn/xnews/58038.htm
- http://m.3g.gqskj.cn/xnews/88877.htm
- http://m.3g.gqskj.cn/xnews/016274.htm
- http://m.3g.gqskj.cn/xnews/1958341.htm
- http://m.3g.gqskj.cn/xnews/329012.htm
- http://m.3g.gqskj.cn/xnews/20762.htm
- http://m.3g.gqskj.cn/xnews/1656.htm
- http://m.3g.gqskj.cn/xnews/0119.htm
- http://m.3g.gqskj.cn/xnews/19927.htm
- http://m.3g.gqskj.cn/xnews/315955.htm
- http://m.3g.gqskj.cn/xnews/0295.htm
- http://m.3g.gqskj.cn/xnews/4846.htm
- http://m.3g.gqskj.cn/xnews/879844.htm
- http://m.3g.gqskj.cn/xnews/3871072.htm
- http://m.3g.gqskj.cn/xnews/39369.htm
- http://m.3g.gqskj.cn/xnews/052079.htm
- http://m.3g.gqskj.cn/xnews/6288137.htm
- http://m.3g.gqskj.cn/xnews/4776322.htm
- http://m.3g.gqskj.cn/xnews/77439.htm
- http://m.3g.gqskj.cn/xnews/6264.htm
- http://m.3g.gqskj.cn/xnews/2253463.htm
- http://m.3g.gqskj.cn/xnews/07024.htm
- http://m.3g.gqskj.cn/xnews/71360.htm
- http://m.3g.gqskj.cn/xnews/2669.htm
- http://m.3g.gqskj.cn/xnews/8738.htm
- http://m.3g.gqskj.cn/xnews/831496.htm
- http://m.3g.gqskj.cn/xnews/0429395.htm
- http://m.3g.gqskj.cn/xnews/7800.htm
- http://m.3g.gqskj.cn/xnews/0620051.htm
- http://m.3g.gqskj.cn/xnews/937944.htm
- http://m.3g.gqskj.cn/xnews/4986.htm
- http://m.3g.gqskj.cn/xnews/4759585.htm
- http://m.3g.gqskj.cn/xnews/0132953.htm
- http://m.3g.gqskj.cn/xnews/618535.htm
- http://m.3g.gqskj.cn/xnews/5245638.htm
- http://m.3g.gqskj.cn/xnews/6418694.htm
- http://m.3g.gqskj.cn/xnews/7981185.htm
- http://m.3g.gqskj.cn/xnews/5198.htm
- http://m.3g.gqskj.cn/xnews/9054.htm
- http://m.3g.gqskj.cn/xnews/7129823.htm
- http://m.3g.gqskj.cn/xnews/8337447.htm
- http://m.3g.gqskj.cn/xnews/31683.htm
- http://m.3g.gqskj.cn/xnews/7680856.htm
- http://m.3g.gqskj.cn/xnews/89621.htm
- http://m.3g.gqskj.cn/xnews/1777.htm
- http://m.3g.gqskj.cn/xnews/4156324.htm
- http://m.3g.gqskj.cn/xnews/3398475.htm
- http://m.3g.gqskj.cn/xnews/6391.htm
- http://m.3g.gqskj.cn/xnews/4505252.htm
- http://m.3g.gqskj.cn/xnews/669707.htm
- http://m.3g.gqskj.cn/xnews/35833.htm
- http://m.3g.gqskj.cn/xnews/8919302.htm
- http://m.3g.gqskj.cn/xnews/01033.htm
- http://m.3g.gqskj.cn/xnews/61583.htm
- http://m.3g.gqskj.cn/xnews/20926.htm
- http://m.3g.gqskj.cn/xnews/520451.htm
- http://m.3g.gqskj.cn/xnews/12034.htm
- http://m.3g.gqskj.cn/xnews/28072.htm
- http://m.3g.gqskj.cn/xnews/597823.htm
- http://m.3g.gqskj.cn/xnews/6478.htm
- http://m.3g.gqskj.cn/xnews/589089.htm
- http://m.3g.gqskj.cn/xnews/5599.htm
- http://m.3g.gqskj.cn/xnews/554493.htm
- http://m.3g.gqskj.cn/xnews/8330815.htm
- http://m.3g.gqskj.cn/xnews/0983.htm
- http://m.3g.gqskj.cn/xnews/33799.htm
- http://m.3g.gqskj.cn/xnews/1345734.htm
- http://m.3g.gqskj.cn/xnews/47845.htm
- http://m.3g.gqskj.cn/xnews/4154547.htm
- http://m.3g.gqskj.cn/xnews/4519.htm
- http://m.3g.gqskj.cn/xnews/508044.htm
- http://m.3g.gqskj.cn/xnews/8400.htm
- http://m.3g.gqskj.cn/xnews/5657587.htm
- http://m.3g.gqskj.cn/xnews/652344.htm
- http://m.3g.gqskj.cn/xnews/8945278.htm
- http://m.3g.gqskj.cn/xnews/5840.htm
- http://m.3g.gqskj.cn/xnews/414441.htm
- http://m.3g.gqskj.cn/xnews/14065.htm
- http://m.3g.gqskj.cn/xnews/062353.htm
- http://m.3g.gqskj.cn/xnews/8849.htm
- http://m.3g.gqskj.cn/xnews/3083.htm
- http://m.3g.gqskj.cn/xnews/424846.htm
- http://m.3g.gqskj.cn/xnews/4959.htm
- http://m.3g.gqskj.cn/xnews/940016.htm
- http://m.3g.gqskj.cn/xnews/5397.htm
- http://m.3g.gqskj.cn/xnews/4273.htm
- http://m.3g.gqskj.cn/xnews/7334877.htm
- http://m.3g.gqskj.cn/xnews/1720662.htm
- http://m.3g.gqskj.cn/xnews/82296.htm
- http://m.3g.gqskj.cn/xnews/06419.htm
- http://m.3g.gqskj.cn/xnews/673207.htm
- http://m.3g.gqskj.cn/xnews/73088.htm
- http://m.3g.gqskj.cn/xnews/6828562.htm
- http://m.3g.gqskj.cn/xnews/00549.htm
- http://m.3g.gqskj.cn/xnews/026652.htm
- http://m.3g.gqskj.cn/xnews/595210.htm
- http://m.3g.gqskj.cn/xnews/74530.htm
- http://m.3g.gqskj.cn/xnews/0035369.htm
- http://m.3g.gqskj.cn/xnews/66481.htm
- http://m.3g.gqskj.cn/xnews/043617.htm
- http://m.3g.gqskj.cn/xnews/52840.htm
- http://m.3g.gqskj.cn/xnews/68045.htm
- http://m.3g.gqskj.cn/xnews/4103.htm
- http://m.3g.gqskj.cn/xnews/020822.htm
- http://m.3g.gqskj.cn/xnews/86461.htm
- http://m.3g.gqskj.cn/xnews/143322.htm
- http://m.3g.gqskj.cn/xnews/35875.htm
- http://m.3g.gqskj.cn/xnews/3727319.htm
- http://m.3g.gqskj.cn/xnews/7110347.htm
- http://m.3g.gqskj.cn/xnews/5696.htm
- http://m.3g.gqskj.cn/xnews/4672.htm
- http://m.3g.gqskj.cn/xnews/1223.htm
- http://m.3g.gqskj.cn/xnews/204047.htm
- http://m.3g.gqskj.cn/xnews/655417.htm
- http://m.3g.gqskj.cn/xnews/536206.htm
- http://m.3g.gqskj.cn/xnews/3679254.htm
- http://m.3g.gqskj.cn/xnews/1565828.htm
- http://m.3g.gqskj.cn/xnews/3482.htm
- http://m.3g.gqskj.cn/xnews/4976.htm
- http://m.3g.gqskj.cn/xnews/8192.htm
- http://m.3g.gqskj.cn/xnews/0197784.htm
- http://m.3g.gqskj.cn/xnews/93527.htm
- http://m.3g.gqskj.cn/xnews/02897.htm
- http://m.3g.gqskj.cn/xnews/494599.htm
- http://m.3g.gqskj.cn/xnews/050893.htm
- http://m.3g.gqskj.cn/xnews/701976.htm
- http://m.3g.gqskj.cn/xnews/4850186.htm
- http://m.3g.gqskj.cn/xnews/6311.htm
- http://m.3g.gqskj.cn/xnews/4602064.htm
- http://m.3g.gqskj.cn/xnews/84302.htm
- http://m.3g.gqskj.cn/xnews/996185.htm
- http://m.3g.gqskj.cn/xnews/0015515.htm
- http://m.3g.gqskj.cn/xnews/686543.htm
- http://m.3g.gqskj.cn/xnews/005777.htm
- http://m.3g.gqskj.cn/xnews/95018.htm
- http://m.3g.gqskj.cn/xnews/07923.htm
- http://m.3g.gqskj.cn/xnews/3243225.htm
- http://m.3g.gqskj.cn/xnews/826744.htm
- http://m.3g.gqskj.cn/xnews/092799.htm
- http://m.3g.gqskj.cn/xnews/1550522.htm
- http://m.3g.gqskj.cn/xnews/690660.htm
- http://m.3g.gqskj.cn/xnews/5568.htm
- http://m.3g.gqskj.cn/xnews/00347.htm
- http://m.3g.gqskj.cn/xnews/13842.htm
- http://m.3g.gqskj.cn/xnews/16423.htm
- http://m.3g.gqskj.cn/xnews/769452.htm
- http://m.3g.gqskj.cn/xnews/653736.htm
- http://m.3g.gqskj.cn/xnews/7337.htm
- http://m.3g.gqskj.cn/xnews/9234.htm
- http://m.3g.gqskj.cn/xnews/2238209.htm
- http://m.3g.gqskj.cn/xnews/5233.htm
- http://m.3g.gqskj.cn/xnews/794532.htm
- http://m.3g.gqskj.cn/xnews/5580278.htm
- http://m.3g.gqskj.cn/xnews/1850.htm
- http://m.3g.gqskj.cn/xnews/751222.htm
- http://m.3g.gqskj.cn/xnews/6671230.htm
- http://m.3g.gqskj.cn/xnews/3603.htm
- http://m.3g.gqskj.cn/xnews/6927653.htm
- http://m.3g.gqskj.cn/xnews/2628.htm
- http://m.3g.gqskj.cn/xnews/35587.htm
- http://m.3g.gqskj.cn/xnews/232785.htm
- http://m.3g.gqskj.cn/xnews/271120.htm
- http://m.3g.gqskj.cn/xnews/51418.htm
- http://m.3g.gqskj.cn/xnews/6609.htm
- http://m.3g.gqskj.cn/xnews/914150.htm
- http://m.3g.gqskj.cn/xnews/630546.htm
- http://m.3g.gqskj.cn/xnews/2729.htm
- http://m.3g.gqskj.cn/xnews/948415.htm
- http://m.3g.gqskj.cn/xnews/07667.htm
- http://m.3g.gqskj.cn/xnews/066225.htm
- http://m.3g.gqskj.cn/xnews/9418339.htm
- http://m.3g.gqskj.cn/xnews/3437602.htm
- http://m.3g.gqskj.cn/xnews/6931.htm
- http://m.3g.gqskj.cn/xnews/5538.htm
- http://m.3g.gqskj.cn/xnews/9186266.htm
- http://m.3g.gqskj.cn/xnews/107712.htm

## 项目结构

```
webindex/
├── src/
│   ├── core/                           # 核心模块
│   │   ├── indexer.js                  # 索引引擎，处理外链解析与存储
│   │   ├── crawler.js                  # 轻量级爬虫，抽取页面元信息
│   │   └── scheduler.js                # 定时任务调度器，管理索引刷新
│   ├── routes/                         # 路由层
│   │   ├── index.js                    # 首页索引列表路由
│   │   ├── batch.js                    # 批次管理路由
│   │   └── stats.js                    # 统计接口路由
│   ├── models/                         # 数据模型
│   │   ├── link.js                     # 外链数据模型定义
│   │   ├── batch.js                    # 批次数据模型
│   │   └── tag.js                      # 标签数据模型
│   ├── services/                       # 业务服务层
│   │   ├── fetchService.js             # 外链抓取服务
│   │   ├── cacheService.js             # Redis 缓存封装
│   │   └── exportService.js            # 数据导出服务
│   ├── middleware/                     # 中间件
│   │   ├── auth.js                     # 简易认证中间件
│   │   ├── logger.js                   # 请求日志中间件
│   │   └── rateLimiter.js              # 限流中间件
│   └── utils/                          # 工具函数
│       ├── validator.js                # URL 校验工具
│       ├── parser.js                   # HTML 元信息解析器
│       └── formatter.js                # 响应格式化工具
├── config/                             # 配置文件
│   ├── default.json                    # 默认配置
│   ├── production.json                 # 生产环境配置
│   └── development.json                # 开发环境配置
├── scripts/                            # 运维脚本
│   ├── importBatch.js                  # 批次数据导入脚本
│   ├── checkLinks.js                   # 外链可用性检查脚本
│   └── backupDb.js                     # 数据库备份脚本
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 单元测试用例
│   └── integration/                    # 集成测试用例
├── public/                             # 静态资源目录
│   ├── css/                            # 样式表文件
│   └── js/                             # 前端 JavaScript 文件
├── views/                              # 模板视图
│   ├── index.ejs                       # 首页模板
│   └── batch.ejs                       # 批次详情页模板
├── logs/                               # 日志目录（运行时生成）
├── data/                               # 数据库文件与临时数据
├── .env.example                        # 环境变量示例文件
├── .gitignore                          # Git 忽略规则
├── package.json                        # 项目依赖与脚本定义
├── package-lock.json                   # 依赖锁定文件
├── README.md                           # 项目说明文档
└── LICENSE                             # 许可证文件
```

## 贡献指南

**提交问题报告** 在 GitHub Issues 中提交您遇到的问题或改进建议，请使用项目提供的 Issue 模板，并详细描述复现步骤、环境信息与预期行为。

**代码分支管理** 从 `main` 分支切出新的功能分支，命名格式为 `feature/功能简述` 或 `fix/问题简述`，完成开发后提交 Pull Request 到 `develop` 分支。

**代码风格规范** 遵循项目配置的 ESLint 与 Prettier 规则，提交前执行 `npm run lint` 与 `npm run test` 确保代码质量与测试通过率。

**文档同步更新** 任何新增功能或接口变更必须同步更新对应的文档文件，包括 API 参考与部署手册，确保文档与代码保持一致。

**审核与合并流程** Pull Request 至少需要一名项目维护者审核通过，且所有 CI 检查通过后方可合并，合并后自动触发测试环境部署。

## 常见问题

**问：项目是否支持 PostgreSQL 作为生产数据库？**

答：支持。项目使用 Knex.js 作为查询构建器，默认配置为 SQLite，您可以在 `config/production.json` 中将 `client` 字段修改为 `pg`，并配置对应的连接池参数与数据库地址。迁移脚本会自动适配不同数据库方言。

**问：如何导入新的外链批次数据？**

答：使用 `npm run import -- --batch=批次号 --file=数据文件路径` 命令。数据文件需为 JSON 格式，每一条包含 `url`、`title`、`tags` 等字段。项目也支持从 CSV 文件导入，需额外指定 `--format=csv` 参数。

**问：定时检查外链可用性的频率如何调整？**

答：在 `config/default.json` 中修改 `scheduler.interval` 字段，单位为分钟。默认值为 1440（每日一次）。您也可以直接在 `src/core/scheduler.js` 中调整 cron 表达式以实现更精细的调度策略，例如每小时执行一次。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:50
