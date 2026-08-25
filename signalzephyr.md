# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研与信息挖掘的轻量级外链聚合与导航系统，专注于将分散在多个内容源中的高质量技术文章、行业动态、开发笔记与运维日志进行统一收录、分类索引与快速检索。项目定位于个人开发者、技术团队以及研究机构在信息过载环境下构建内部知识导航站，通过结构化的外链管理降低信息损耗，提升内容复用效率。

WebIndex 不提供内容存储服务，仅作为链接元数据的索引层，配合标签体系、全文检索与访问频率统计，帮助用户在数万条外链中快速定位有价值的信息源。项目采用纯静态架构，支持一键生成可部署的导航首页与分类目录，适用于技术博客聚合、项目文档外链整理、行业报告索引以及团队内部周报链接归档等场景。

## 功能概览

**批量链接导入与清洗** 支持从文本文件、CSV 或直接粘贴的URL列表中批量导入链接，自动识别协议头并进行格式规范化，过滤重复条目与无效协议。

**自动标签生成与分类** 基于URL路径、域名关键词以及页面标题模式，为每条链接自动生成候选标签，用户可手动修正并建立多级分类体系。

**全文检索与模糊匹配** 内置倒排索引引擎，支持对链接标题、描述、标签以及来源域名进行全文检索，提供拼写容错与拼音首字母快速定位。

**访问频率统计与热度排序** 记录每条外链的点击次数与最后访问时间，支持按周、月、季度生成热度排行榜，辅助识别长期有价值的内容源。

**导航页面模板系统** 提供多套响应式导航页面模板，支持自定义Logo、配色与布局，一键生成可部署的静态HTML首页与分类子页面。

**元数据扩展字段管理** 允许用户为每条链接添加自定义扩展字段，如阅读耗时、适用技术水平、关联项目编号、审核状态等，满足团队协作场景下的信息标注需求。

**数据快照与导入导出** 支持将全部索引数据导出为JSON或YAML格式快照，便于版本备份、跨设备迁移以及与其他工具链的数据交换。

## 应用场景

技术团队内部知识库外链管理 开发团队在日常调研中积累大量技术博客、官方文档、GitHub仓库与RFC草案，WebIndex可将这些分散链接统一归档，按技术栈分类并添加内部评审备注，新成员入职时可快速了解团队关注的技术资源分布。

个人开发者技术阅读工作流优化 独立开发者订阅数十个技术资讯源，每日产生大量待阅读文章。WebIndex帮助记录未读链接，标记阅读优先级，通过热度排序过滤低质量内容，将阅读时间集中在高价值信息上。

行业报告与政策文件索引整理 研究机构或咨询团队需要长期跟踪特定行业的政策动态与市场报告，WebIndex可建立按时间、地域、主题组织的外链索引，配合扩展字段记录报告摘要与关键数据，提升调研材料的检索效率。

开源项目文档外链体系构建 开源项目维护者可在项目Wiki中嵌入WebIndex生成的导航页面，将外部依赖文档、社区教程、视频讲解、相关工具链等链接统一整理，降低社区用户的学习门槛。

## 快速开始

以下命令演示了如何从GitHub克隆项目、安装依赖并启动开发服务器。WebIndex依赖Node.js运行环境，建议使用LTS版本。

```bash
git clone https://github.com/webindex/webindex-core.git
cd webindex-core
npm install --production=false
npm run build
npm start
```

执行上述命令后，开发服务器默认监听本机3000端口，访问 http://127.0.0.1:3000 即可进入WebIndex管理界面。首次启动将自动生成示例数据，包含若干预设分类与演示链接，便于快速体验完整功能。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >=18.0.0 | 运行时环境，建议使用LTS版本，依赖V8引擎的ES2022特性支持 |
| npm | >=9.0.0 | 包管理工具，用于安装项目依赖及执行构建脚本 |
| SQLite3 | 内置集成 | 轻量级嵌入式数据库，用于存储链接元数据与索引，无需额外安装 |
| 磁盘空间 | >=200MB | 用于存放数据库文件、静态资源及构建产物，实际占用随索引量增长 |
| 内存 | >=512MB | 运行内存要求，索引10万条链接时建议分配1GB以上堆内存 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows下建议使用WSL2或Git Bash执行脚本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | /docs/quick-start.md | 如何从零开始搭建WebIndex实例，完成首次数据导入并生成导航页面 |
| 配置 | /docs/configuration.md | 如何修改站点名称、分类预设、标签规则、模板参数及性能调优选项 |
| 开发 | /docs/development.md | 如何扩展自定义解析器、增加元数据字段、替换检索算法及贡献代码规范 |
| 运维 | /docs/operations.md | 如何备份数据快照、迁移数据库、配置自动清理策略及监控访问日志 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/3943895.htm
- http://m.blog.gqskj.cn/nnews/704868.htm
- http://m.blog.gqskj.cn/nnews/27338.htm
- http://m.blog.gqskj.cn/nnews/14233.htm
- http://m.blog.gqskj.cn/nnews/57349.htm
- http://m.blog.gqskj.cn/nnews/2834024.htm
- http://m.blog.gqskj.cn/nnews/5117.htm
- http://m.blog.gqskj.cn/nnews/44798.htm
- http://m.blog.gqskj.cn/nnews/605629.htm
- http://m.blog.gqskj.cn/nnews/428935.htm
- http://m.blog.gqskj.cn/nnews/6449659.htm
- http://m.blog.gqskj.cn/nnews/6633934.htm
- http://m.blog.gqskj.cn/nnews/744627.htm
- http://m.blog.gqskj.cn/nnews/3174748.htm
- http://m.blog.gqskj.cn/nnews/985685.htm
- http://m.blog.gqskj.cn/nnews/97718.htm
- http://m.blog.gqskj.cn/nnews/8848803.htm
- http://m.blog.gqskj.cn/nnews/5319355.htm
- http://m.blog.gqskj.cn/nnews/9415252.htm
- http://m.blog.gqskj.cn/nnews/817367.htm
- http://m.blog.gqskj.cn/nnews/99869.htm
- http://m.blog.gqskj.cn/nnews/5388764.htm
- http://m.blog.gqskj.cn/nnews/649268.htm
- http://m.blog.gqskj.cn/nnews/1434638.htm
- http://m.blog.gqskj.cn/nnews/204158.htm
- http://m.blog.gqskj.cn/nnews/4688596.htm
- http://m.blog.gqskj.cn/nnews/9935802.htm
- http://m.blog.gqskj.cn/nnews/523612.htm
- http://m.blog.gqskj.cn/nnews/2146.htm
- http://m.blog.gqskj.cn/nnews/7220.htm
- http://m.blog.gqskj.cn/nnews/2559.htm
- http://m.blog.gqskj.cn/nnews/3237517.htm
- http://m.blog.gqskj.cn/nnews/721221.htm
- http://m.blog.gqskj.cn/nnews/7076.htm
- http://m.blog.gqskj.cn/nnews/82508.htm
- http://m.blog.gqskj.cn/nnews/83652.htm
- http://m.blog.gqskj.cn/nnews/9626206.htm
- http://m.blog.gqskj.cn/nnews/5646750.htm
- http://m.blog.gqskj.cn/nnews/35484.htm
- http://m.blog.gqskj.cn/nnews/02609.htm
- http://m.blog.gqskj.cn/nnews/8451.htm
- http://m.blog.gqskj.cn/nnews/4625.htm
- http://m.blog.gqskj.cn/nnews/4319949.htm
- http://m.blog.gqskj.cn/nnews/8433000.htm
- http://m.blog.gqskj.cn/nnews/688799.htm
- http://m.blog.gqskj.cn/nnews/8787308.htm
- http://m.blog.gqskj.cn/nnews/36583.htm
- http://m.blog.gqskj.cn/nnews/68151.htm
- http://m.blog.gqskj.cn/nnews/82784.htm
- http://m.blog.gqskj.cn/nnews/57804.htm
- http://m.blog.gqskj.cn/nnews/54370.htm
- http://m.blog.gqskj.cn/nnews/8850.htm
- http://m.blog.gqskj.cn/nnews/591861.htm
- http://m.blog.gqskj.cn/nnews/67553.htm
- http://m.blog.gqskj.cn/nnews/78427.htm
- http://m.blog.gqskj.cn/nnews/77651.htm
- http://m.blog.gqskj.cn/nnews/1050742.htm
- http://m.blog.gqskj.cn/nnews/417209.htm
- http://m.blog.gqskj.cn/nnews/7559.htm
- http://m.blog.gqskj.cn/nnews/0861.htm
- http://m.blog.gqskj.cn/nnews/55927.htm
- http://m.blog.gqskj.cn/nnews/223993.htm
- http://m.blog.gqskj.cn/nnews/0565783.htm
- http://m.blog.gqskj.cn/nnews/44830.htm
- http://m.blog.gqskj.cn/nnews/642864.htm
- http://m.blog.gqskj.cn/nnews/8261.htm
- http://m.blog.gqskj.cn/nnews/854072.htm
- http://m.blog.gqskj.cn/nnews/610128.htm
- http://m.blog.gqskj.cn/nnews/012810.htm
- http://m.blog.gqskj.cn/nnews/4482098.htm
- http://m.blog.gqskj.cn/nnews/52843.htm
- http://m.blog.gqskj.cn/nnews/6265.htm
- http://m.blog.gqskj.cn/nnews/9931912.htm
- http://m.blog.gqskj.cn/nnews/12880.htm
- http://m.blog.gqskj.cn/nnews/0732366.htm
- http://m.blog.gqskj.cn/nnews/90217.htm
- http://m.blog.gqskj.cn/nnews/803103.htm
- http://m.blog.gqskj.cn/nnews/769270.htm
- http://m.blog.gqskj.cn/nnews/45676.htm
- http://m.blog.gqskj.cn/nnews/8190644.htm
- http://m.blog.gqskj.cn/nnews/4722.htm
- http://m.blog.gqskj.cn/nnews/84459.htm
- http://m.blog.gqskj.cn/nnews/2687298.htm
- http://m.blog.gqskj.cn/nnews/2350.htm
- http://m.blog.gqskj.cn/nnews/0764.htm
- http://m.blog.gqskj.cn/nnews/97821.htm
- http://m.blog.gqskj.cn/nnews/7797031.htm
- http://m.blog.gqskj.cn/nnews/0200.htm
- http://m.blog.gqskj.cn/nnews/5625545.htm
- http://m.blog.gqskj.cn/nnews/73089.htm
- http://m.blog.gqskj.cn/nnews/0210.htm
- http://m.blog.gqskj.cn/nnews/27674.htm
- http://m.blog.gqskj.cn/nnews/0891.htm
- http://m.blog.gqskj.cn/nnews/51930.htm
- http://m.blog.gqskj.cn/nnews/2529744.htm
- http://m.blog.gqskj.cn/nnews/91644.htm
- http://m.blog.gqskj.cn/nnews/8843100.htm
- http://m.blog.gqskj.cn/nnews/768784.htm
- http://m.blog.gqskj.cn/nnews/32043.htm
- http://m.blog.gqskj.cn/nnews/58763.htm
- http://m.blog.gqskj.cn/nnews/9205.htm
- http://m.blog.gqskj.cn/nnews/14007.htm
- http://m.blog.gqskj.cn/nnews/2181458.htm
- http://m.blog.gqskj.cn/nnews/9838.htm
- http://m.blog.gqskj.cn/nnews/9928444.htm
- http://m.blog.gqskj.cn/nnews/15452.htm
- http://m.blog.gqskj.cn/nnews/81766.htm
- http://m.blog.gqskj.cn/nnews/8788.htm
- http://m.blog.gqskj.cn/nnews/58354.htm
- http://m.blog.gqskj.cn/nnews/2797485.htm
- http://m.blog.gqskj.cn/nnews/8090.htm
- http://m.blog.gqskj.cn/nnews/282549.htm
- http://m.blog.gqskj.cn/nnews/9806.htm
- http://m.blog.gqskj.cn/nnews/4239.htm
- http://m.blog.gqskj.cn/nnews/4746863.htm
- http://m.blog.gqskj.cn/nnews/80348.htm
- http://m.blog.gqskj.cn/nnews/0391.htm
- http://m.blog.gqskj.cn/nnews/30508.htm
- http://m.blog.gqskj.cn/nnews/12523.htm
- http://m.blog.gqskj.cn/nnews/3732654.htm
- http://m.blog.gqskj.cn/nnews/7590419.htm
- http://m.blog.gqskj.cn/nnews/2010100.htm
- http://m.blog.gqskj.cn/nnews/4628.htm
- http://m.blog.gqskj.cn/nnews/85297.htm
- http://m.blog.gqskj.cn/nnews/167178.htm
- http://m.blog.gqskj.cn/nnews/977552.htm
- http://m.blog.gqskj.cn/nnews/091813.htm
- http://m.blog.gqskj.cn/nnews/7199222.htm
- http://m.blog.gqskj.cn/nnews/232581.htm
- http://m.blog.gqskj.cn/nnews/65175.htm
- http://m.blog.gqskj.cn/nnews/51515.htm
- http://m.blog.gqskj.cn/nnews/6844.htm
- http://m.blog.gqskj.cn/nnews/93215.htm
- http://m.blog.gqskj.cn/nnews/5427251.htm
- http://m.blog.gqskj.cn/nnews/95245.htm
- http://m.blog.gqskj.cn/nnews/2721.htm
- http://m.blog.gqskj.cn/nnews/03297.htm
- http://m.blog.gqskj.cn/nnews/8034.htm
- http://m.blog.gqskj.cn/nnews/6754991.htm
- http://m.blog.gqskj.cn/nnews/922265.htm
- http://m.blog.gqskj.cn/nnews/55537.htm
- http://m.blog.gqskj.cn/nnews/998726.htm
- http://m.blog.gqskj.cn/nnews/9184056.htm
- http://m.blog.gqskj.cn/nnews/9838193.htm
- http://m.blog.gqskj.cn/nnews/076928.htm
- http://m.blog.gqskj.cn/nnews/60959.htm
- http://m.blog.gqskj.cn/nnews/874247.htm
- http://m.blog.gqskj.cn/nnews/218072.htm
- http://m.blog.gqskj.cn/nnews/681790.htm
- http://m.blog.gqskj.cn/nnews/5701.htm
- http://m.blog.gqskj.cn/nnews/60292.htm
- http://m.blog.gqskj.cn/nnews/707782.htm
- http://m.blog.gqskj.cn/nnews/41828.htm
- http://m.blog.gqskj.cn/nnews/11420.htm
- http://m.blog.gqskj.cn/nnews/82828.htm
- http://m.blog.gqskj.cn/nnews/1428.htm
- http://m.blog.gqskj.cn/nnews/1411.htm
- http://m.blog.gqskj.cn/nnews/3598.htm
- http://m.blog.gqskj.cn/nnews/7681.htm
- http://m.blog.gqskj.cn/nnews/5677.htm
- http://m.blog.gqskj.cn/nnews/52006.htm
- http://m.blog.gqskj.cn/nnews/7689449.htm
- http://m.blog.gqskj.cn/nnews/5713950.htm
- http://m.blog.gqskj.cn/nnews/1015.htm
- http://m.blog.gqskj.cn/nnews/8932.htm
- http://m.blog.gqskj.cn/nnews/9525.htm
- http://m.blog.gqskj.cn/nnews/276268.htm
- http://m.blog.gqskj.cn/nnews/59371.htm
- http://m.blog.gqskj.cn/nnews/12613.htm
- http://m.blog.gqskj.cn/nnews/4854.htm
- http://m.blog.gqskj.cn/nnews/8041423.htm
- http://m.blog.gqskj.cn/nnews/40486.htm
- http://m.blog.gqskj.cn/nnews/626536.htm
- http://m.blog.gqskj.cn/nnews/370535.htm
- http://m.blog.gqskj.cn/nnews/9400.htm
- http://m.blog.gqskj.cn/nnews/906776.htm
- http://m.blog.gqskj.cn/nnews/4007955.htm
- http://m.blog.gqskj.cn/nnews/099112.htm
- http://m.blog.gqskj.cn/nnews/5980383.htm
- http://m.blog.gqskj.cn/nnews/278709.htm
- http://m.blog.gqskj.cn/nnews/96550.htm
- http://m.blog.gqskj.cn/nnews/1080315.htm
- http://m.blog.gqskj.cn/nnews/7443787.htm
- http://m.blog.gqskj.cn/nnews/40483.htm
- http://m.blog.gqskj.cn/nnews/0896.htm
- http://m.blog.gqskj.cn/nnews/0083.htm
- http://m.blog.gqskj.cn/nnews/59602.htm
- http://m.blog.gqskj.cn/nnews/8962.htm
- http://m.blog.gqskj.cn/nnews/80191.htm
- http://m.blog.gqskj.cn/nnews/260974.htm
- http://m.blog.gqskj.cn/nnews/0517368.htm
- http://m.blog.gqskj.cn/nnews/71056.htm
- http://m.blog.gqskj.cn/nnews/23494.htm
- http://m.blog.gqskj.cn/nnews/0568.htm
- http://m.blog.gqskj.cn/nnews/6676634.htm
- http://m.blog.gqskj.cn/nnews/79919.htm
- http://m.blog.gqskj.cn/nnews/8722.htm
- http://m.blog.gqskj.cn/nnews/746500.htm
- http://m.blog.gqskj.cn/nnews/37517.htm
- http://m.blog.gqskj.cn/nnews/6745012.htm
- http://m.blog.gqskj.cn/nnews/7499254.htm
- http://m.blog.gqskj.cn/nnews/1369.htm
- http://m.blog.gqskj.cn/nnews/175396.htm
- http://m.blog.gqskj.cn/nnews/900304.htm
- http://m.blog.gqskj.cn/nnews/1290.htm
- http://m.blog.gqskj.cn/nnews/59800.htm
- http://m.blog.gqskj.cn/nnews/87207.htm
- http://m.blog.gqskj.cn/nnews/0908.htm
- http://m.blog.gqskj.cn/nnews/168266.htm
- http://m.blog.gqskj.cn/nnews/1739.htm
- http://m.blog.gqskj.cn/nnews/13295.htm
- http://m.blog.gqskj.cn/nnews/22708.htm
- http://m.blog.gqskj.cn/nnews/00861.htm
- http://m.blog.gqskj.cn/nnews/049058.htm
- http://m.blog.gqskj.cn/nnews/0477.htm
- http://m.blog.gqskj.cn/nnews/4879.htm
- http://m.blog.gqskj.cn/nnews/5664687.htm
- http://m.blog.gqskj.cn/nnews/051465.htm
- http://m.blog.gqskj.cn/nnews/99045.htm
- http://m.blog.gqskj.cn/nnews/6608.htm
- http://m.blog.gqskj.cn/nnews/94028.htm
- http://m.blog.gqskj.cn/nnews/7817.htm
- http://m.blog.gqskj.cn/nnews/020034.htm
- http://m.blog.gqskj.cn/nnews/411765.htm
- http://m.blog.gqskj.cn/nnews/5210343.htm
- http://m.blog.gqskj.cn/nnews/60474.htm
- http://m.blog.gqskj.cn/nnews/782974.htm
- http://m.blog.gqskj.cn/nnews/9145971.htm
- http://m.blog.gqskj.cn/nnews/74652.htm
- http://m.blog.gqskj.cn/nnews/325253.htm
- http://m.blog.gqskj.cn/nnews/908320.htm
- http://m.blog.gqskj.cn/nnews/915123.htm
- http://m.blog.gqskj.cn/nnews/8308248.htm
- http://m.blog.gqskj.cn/nnews/4533830.htm
- http://m.blog.gqskj.cn/nnews/428324.htm
- http://m.blog.gqskj.cn/nnews/29347.htm
- http://m.blog.gqskj.cn/nnews/8023233.htm
- http://m.blog.gqskj.cn/nnews/64019.htm
- http://m.blog.gqskj.cn/nnews/9819.htm
- http://m.blog.gqskj.cn/nnews/72672.htm
- http://m.blog.gqskj.cn/nnews/2524610.htm
- http://m.blog.gqskj.cn/nnews/520166.htm
- http://m.blog.gqskj.cn/nnews/8019170.htm
- http://m.blog.gqskj.cn/nnews/8442217.htm
- http://m.blog.gqskj.cn/nnews/870489.htm
- http://m.blog.gqskj.cn/nnews/269658.htm
- http://m.blog.gqskj.cn/nnews/859753.htm
- http://m.blog.gqskj.cn/nnews/5918913.htm
- http://m.blog.gqskj.cn/nnews/7182322.htm
- http://m.blog.gqskj.cn/nnews/64170.htm

## 项目结构

```
webindex-core/
├── src/                           # 核心源代码目录
│   ├── core/                      # 核心引擎模块
│   │   ├── indexer.js             # 倒排索引构建与检索实现
│   │   ├── parser.js              # URL解析与标题抽取器
│   │   └── tags.js                # 自动标签生成与分类逻辑
│   ├── db/                        # 数据库访问层
│   │   ├── sqlite.js              # SQLite3连接池与CRUD操作
│   │   ├── migrations/            # 数据库结构迁移脚本
│   │   └── seed.js                # 示例数据填充脚本
│   ├── api/                       # HTTP接口层
│   │   ├── routes.js              # 路由定义与中间件配置
│   │   ├── controllers/           # 请求控制器
│   │   └── validators/            # 输入参数校验器
│   ├── templates/                 # 页面模板引擎
│   │   ├── layouts/               # 基础布局模板
│   │   ├── partials/              # 可复用组件模板
│   │   └── pages/                 # 独立页面模板
│   └── utils/                     # 通用工具函数
│       ├── logger.js              # 日志记录器
│       ├── config.js              # 配置加载与合并
│       └── validator.js           # URL格式与数据类型校验
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认配置参数
│   ├── production.yaml            # 生产环境覆盖配置
│   └── schema.json                # 配置项的JSON Schema定义
├── test/                          # 测试套件
│   ├── unit/                      # 单元测试用例
│   ├── integration/               # 集成测试用例
│   └── fixtures/                  # 测试固定数据
├── dist/                          # 构建输出目录（自动生成）
│   ├── bundle.js                  # 打包后的服务端代码
│   └── assets/                    # 静态资源副本
├── docs/                          # 文档目录
│   ├── quick-start.md             # 快速入门指南
│   ├── configuration.md           # 完整配置参数说明
│   ├── development.md             # 开发环境搭建与贡献规范
│   └── operations.md              # 运维部署与监控指南
├── scripts/                       # 辅助脚本
│   ├── backup.js                  # 数据库备份工具
│   ├── import-csv.js              # CSV批量导入脚本
│   └── generate-nav.js            # 导航页面生成器
├── .github/                       # GitHub社区配置
│   ├── ISSUE_TEMPLATE/            # 问题报告模板
│   └── workflows/                 # CI/CD流水线定义
├── package.json                   # 项目元数据与依赖声明
├── package-lock.json              # 依赖版本锁定文件
├── README.md                      # 项目说明文档（本文件）
└── LICENSE                        # MIT许可证文本
```

## 贡献指南

提交问题报告与功能请求 通过GitHub Issues提交问题报告时，请使用提供的模板填写系统版本、Node.js版本、错误日志及可复现的最小操作步骤。功能请求请明确描述使用场景与预期行为。

代码提交与分支管理 项目采用Git Flow分支模型，主分支为main，开发分支为develop。所有功能开发请从develop分支派生新分支，命名格式为feature/功能简述。提交信息请遵循Conventional Commits规范。

测试用例编写与覆盖 新增功能或修复缺陷时，需同步编写对应的单元测试或集成测试用例。测试文件放置于test目录下，命名与源文件对应。提交前请确保全部测试通过且覆盖率不低于现有基线。

文档更新与示例完善 涉及用户可见的行为变更时，请同步更新docs目录下的相关文档，并在必要处补充代码示例或配置片段。文档风格保持技术化、精确、无歧义。

代码审查与合并流程 所有合并至develop或main分支的请求均需通过至少一名核心维护者的代码审查。审查要点包括逻辑正确性、性能影响、安全风险及代码风格一致性。

## 常见问题

Q: 导入大量链接时页面响应缓慢或超时如何处理
A: 单次导入建议不超过5000条链接。若需批量导入更大规模数据，请使用scripts/import-csv.js脚本进行命令行导入，该脚本支持分批提交事务并输出实时进度。同时可在配置文件中调整db.batchSize参数以匹配机器性能。

Q: 如何迁移WebIndex实例到另一台服务器
A: 使用内置备份脚本执行npm run backup生成数据快照文件，快照包含完整的SQLite数据库与配置文件。将快照文件传输至目标服务器后，执行npm run restore 快照文件名即可完成恢复。注意恢复前需确保目标服务器的Node.js版本与源服务器一致。

Q: 自动生成的标签不准确，能否完全手动控制
A: 可以。在配置文件中将autoTag.enabled设置为false即可关闭自动标签生成功能。之后所有标签操作需通过管理界面或API手动添加、修改或删除。已自动生成的标签在关闭功能后不会自动清除，可通过管理界面的批量编辑功能进行清理。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:00
