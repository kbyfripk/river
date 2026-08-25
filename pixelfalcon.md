# LinkCatalog

LinkCatalog 是一个面向技术社区与内容创作者的轻量化外链聚合与导航系统。该项目定位于将分散的、有价值的网络资源（如技术文章、工具站点、教程文档）进行集中化管理，并提供清晰、可维护的展示界面。LinkCatalog 并非一个简单的收藏夹，而是一套具备分类索引、快速检索与状态监控能力的资源管理工具，适用于个人开发者、技术团队及内容运营者。

LinkCatalog 的目标用户包括：需要整理日常查阅资料的技术人员、希望为项目文档构建快速外链索引的开源维护者、以及运营技术类博客或社区网站的内容管理员。通过 LinkCatalog，用户可以告别杂乱无章的浏览器书签，将资源纳入结构化的本地或云端系统中，实现高效率的访问与分享。

## 功能概览

**分层分类索引体系**：支持无限层级的目录与标签系统，用户可根据技术领域、资源类型或使用频次自定义分类逻辑，实现多维度资源划分。

**全文与元数据检索**：内置基于标题、描述、标签及 URL 片段的快速搜索功能，帮助用户在海量链接中秒级定位目标资源。

**资源健康状态监测**：后台定时任务对已收录的链接进行可达性检查，标记失效或响应超时的资源，辅助用户清理或更新条目。

**批量导入与导出**：支持从标准格式（如 CSV、JSON、HTML 书签）批量导入链接数据，并支持将当前库导出为可移植的静态页面或数据文件，便于备份与迁移。

**访问统计与热度分析**：记录每个外链的点击次数与最近访问时间，提供简单的热度排行，帮助识别高价值或高频使用的资源。

**响应式管理面板**：提供适配桌面与移动设备的管理界面，用户可在不同终端下完成资源的增删改查操作，无需依赖特定客户端。

**开放 API 接口**：提供基于 RESTful 风格的 API，允许第三方工具或脚本对资源库进行读写操作，便于集成至现有工作流。

## 应用场景

**技术文档站的外链附录**：当技术团队维护产品文档或 API 参考时，可使用 LinkCatalog 生成一份动态更新的外部参考资源列表，替代静态的纯文本附录。读者可在文档中直接跳转至相关社区讨论、扩展工具或标准规范页面。

**个人知识库的输入源**：知识管理爱好者可将 LinkCatalog 作为知识库的前端入口，将日常阅读的技术博客、视频教程、开源项目仓库统一收录，并通过标签与分类与本地笔记体系（如 Logseq、Obsidian）进行双向关联。

**社区内容聚合页**：技术社区或新闻资讯站点可在侧边栏或独立页面嵌入 LinkCatalog 生成的链接排行模块，向访客展示近期热门或编辑推荐的外部资源，降低内容发现成本。

**项目协作的共享书签集**：开发团队可使用 LinkCatalog 搭建内部共享书签服务，将项目依赖的文档地址、运维面板、日志系统入口集中管理，并利用状态监测功能及时获知关键服务的可用性变化。

## 快速开始

以下指令适用于 Linux 与 macOS 环境。Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/linkcatalog.git

# 进入项目工作目录
cd linkcatalog

# 安装项目依赖（使用 npm，若使用 yarn 可替换为 yarn install）
npm install

# 启动开发服务器，默认监听 http://localhost:3000
npm run dev
```

生产环境部署请参考 `docs/deployment.md` 文档，使用 `npm run build` 进行静态构建，并结合 Nginx 或 Caddy 提供最终服务。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Node.js | >= 18.0.0 | 项目运行时与构建工具链的基础环境 |
| npm | >= 9.0.0 或 yarn >= 1.22.0 | 包管理器，用于安装第三方依赖库 |
| SQLite3 | 系统内置或通过 npm 安装 | 默认嵌入式数据库，用于存储链接元数据与统计信息 |
| Git | >= 2.25.0 | 版本控制工具，用于克隆仓库及获取更新 |
| 现代浏览器 | 最新两个主要版本（Chrome, Firefox, Edge, Safari） | 管理面板及展示页面的客户端运行环境 |
| 可选：Redis | >= 6.2.0 | 用于提升高并发场景下的缓存与会话存储性能，非必需 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 入门指南 | `docs/getting-started.md` | 如何快速启动项目、首次配置数据库、创建第一个资源条目？ |
| 配置参考 | `docs/configuration.md` | 有哪些环境变量与配置文件选项？如何调整端口、数据库路径与监测间隔？ |
| API 手册 | `docs/api-reference.md` | 提供了哪些开放接口？如何进行资源的增删改查与批量操作？ |
| 部署运维 | `docs/deployment.md` | 如何构建生产版本、配置反向代理、使用 Docker 容器化运行？ |

## 资源列表

- http://m.blog.fcful.cn/bnews/613588.htm
- http://m.blog.fcful.cn/bnews/7558.htm
- http://m.blog.fcful.cn/bnews/209236.htm
- http://m.blog.fcful.cn/bnews/7232.htm
- http://m.blog.fcful.cn/bnews/624951.htm
- http://m.blog.fcful.cn/bnews/4523678.htm
- http://m.blog.fcful.cn/bnews/9794.htm
- http://m.blog.fcful.cn/bnews/58904.htm
- http://m.blog.fcful.cn/bnews/675358.htm
- http://m.blog.fcful.cn/bnews/76205.htm
- http://m.blog.fcful.cn/bnews/84009.htm
- http://m.blog.fcful.cn/bnews/3942.htm
- http://m.blog.fcful.cn/bnews/45846.htm
- http://m.blog.fcful.cn/bnews/60247.htm
- http://m.blog.fcful.cn/bnews/213507.htm
- http://m.blog.fcful.cn/bnews/332999.htm
- http://m.blog.fcful.cn/bnews/53432.htm
- http://m.blog.fcful.cn/bnews/57969.htm
- http://m.blog.fcful.cn/bnews/40611.htm
- http://m.blog.fcful.cn/bnews/14850.htm
- http://m.blog.fcful.cn/bnews/396198.htm
- http://m.blog.fcful.cn/bnews/525494.htm
- http://m.blog.fcful.cn/bnews/0089.htm
- http://m.blog.fcful.cn/bnews/37758.htm
- http://m.blog.fcful.cn/bnews/515616.htm
- http://m.blog.fcful.cn/bnews/9939.htm
- http://m.blog.fcful.cn/bnews/729520.htm
- http://m.blog.fcful.cn/bnews/9921.htm
- http://m.blog.fcful.cn/bnews/13272.htm
- http://m.blog.fcful.cn/bnews/076484.htm
- http://m.blog.fcful.cn/bnews/184619.htm
- http://m.blog.fcful.cn/bnews/5081729.htm
- http://m.blog.fcful.cn/bnews/5039689.htm
- http://m.blog.fcful.cn/bnews/53084.htm
- http://m.blog.fcful.cn/bnews/87164.htm
- http://m.blog.fcful.cn/bnews/849534.htm
- http://m.blog.fcful.cn/bnews/12485.htm
- http://m.blog.fcful.cn/bnews/09299.htm
- http://m.blog.fcful.cn/bnews/78512.htm
- http://m.blog.fcful.cn/bnews/168045.htm
- http://m.blog.fcful.cn/bnews/20623.htm
- http://m.blog.fcful.cn/bnews/58621.htm
- http://m.blog.fcful.cn/bnews/3926238.htm
- http://m.blog.fcful.cn/bnews/42599.htm
- http://m.blog.fcful.cn/bnews/9996.htm
- http://m.blog.fcful.cn/bnews/2629485.htm
- http://m.blog.fcful.cn/bnews/4045943.htm
- http://m.blog.fcful.cn/bnews/24237.htm
- http://m.blog.fcful.cn/bnews/41079.htm
- http://m.blog.fcful.cn/bnews/80997.htm
- http://m.blog.fcful.cn/bnews/4353.htm
- http://m.blog.fcful.cn/bnews/5559556.htm
- http://m.blog.fcful.cn/bnews/3213.htm
- http://m.blog.fcful.cn/bnews/0201218.htm
- http://m.blog.fcful.cn/bnews/76619.htm
- http://m.blog.fcful.cn/bnews/476079.htm
- http://m.blog.fcful.cn/bnews/77081.htm
- http://m.blog.fcful.cn/bnews/535711.htm
- http://m.blog.fcful.cn/bnews/5911.htm
- http://m.blog.fcful.cn/bnews/2316.htm
- http://m.blog.fcful.cn/bnews/3870958.htm
- http://m.blog.fcful.cn/bnews/720621.htm
- http://m.blog.fcful.cn/bnews/7662676.htm
- http://m.blog.fcful.cn/bnews/0882198.htm
- http://m.blog.fcful.cn/bnews/729360.htm
- http://m.blog.fcful.cn/bnews/6109.htm
- http://m.blog.fcful.cn/bnews/8944928.htm
- http://m.blog.fcful.cn/bnews/93398.htm
- http://m.blog.fcful.cn/bnews/279410.htm
- http://m.blog.fcful.cn/bnews/5354.htm
- http://m.blog.fcful.cn/bnews/6263.htm
- http://m.blog.fcful.cn/bnews/20012.htm
- http://m.blog.fcful.cn/bnews/090802.htm
- http://m.blog.fcful.cn/bnews/9619991.htm
- http://m.blog.fcful.cn/bnews/196706.htm
- http://m.blog.fcful.cn/bnews/0310.htm
- http://m.blog.fcful.cn/bnews/64544.htm
- http://m.blog.fcful.cn/bnews/73051.htm
- http://m.blog.fcful.cn/bnews/0323.htm
- http://m.blog.fcful.cn/bnews/00207.htm
- http://m.blog.fcful.cn/bnews/6309406.htm
- http://m.blog.fcful.cn/bnews/2914.htm
- http://m.blog.fcful.cn/bnews/5191.htm
- http://m.blog.fcful.cn/bnews/966348.htm
- http://m.blog.fcful.cn/bnews/0975.htm
- http://m.blog.fcful.cn/bnews/6597336.htm
- http://m.blog.fcful.cn/bnews/71961.htm
- http://m.blog.fcful.cn/bnews/339479.htm
- http://m.blog.fcful.cn/bnews/8902684.htm
- http://m.blog.fcful.cn/bnews/3875875.htm
- http://m.blog.fcful.cn/bnews/486247.htm
- http://m.blog.fcful.cn/bnews/2292826.htm
- http://m.blog.fcful.cn/bnews/9804.htm
- http://m.blog.fcful.cn/bnews/330977.htm
- http://m.blog.fcful.cn/bnews/81874.htm
- http://m.blog.fcful.cn/bnews/97572.htm
- http://m.blog.fcful.cn/bnews/036430.htm
- http://m.blog.fcful.cn/bnews/3437986.htm
- http://m.blog.fcful.cn/bnews/4262202.htm
- http://m.blog.fcful.cn/bnews/834603.htm
- http://m.blog.fcful.cn/bnews/9458.htm
- http://m.blog.fcful.cn/bnews/78123.htm
- http://m.blog.fcful.cn/bnews/7078576.htm
- http://m.blog.fcful.cn/bnews/348341.htm
- http://m.blog.fcful.cn/bnews/975709.htm
- http://m.blog.fcful.cn/bnews/1195.htm
- http://m.blog.fcful.cn/bnews/2965.htm
- http://m.blog.fcful.cn/bnews/244879.htm
- http://m.blog.fcful.cn/bnews/269993.htm
- http://m.blog.fcful.cn/bnews/44923.htm
- http://m.blog.fcful.cn/bnews/7476.htm
- http://m.blog.fcful.cn/bnews/64433.htm
- http://m.blog.fcful.cn/bnews/77035.htm
- http://m.blog.fcful.cn/bnews/9933.htm
- http://m.blog.fcful.cn/bnews/1738.htm
- http://m.blog.fcful.cn/bnews/083469.htm
- http://m.blog.fcful.cn/bnews/5049.htm
- http://m.blog.fcful.cn/bnews/0838076.htm
- http://m.blog.fcful.cn/bnews/84915.htm
- http://m.blog.fcful.cn/bnews/7746822.htm
- http://m.blog.fcful.cn/bnews/5276679.htm
- http://m.blog.fcful.cn/bnews/4056138.htm
- http://m.blog.fcful.cn/bnews/79277.htm
- http://m.blog.fcful.cn/bnews/8557055.htm
- http://m.blog.fcful.cn/bnews/53172.htm
- http://m.blog.fcful.cn/bnews/25913.htm
- http://m.blog.fcful.cn/bnews/1272.htm
- http://m.blog.fcful.cn/bnews/4442064.htm
- http://m.blog.fcful.cn/bnews/387390.htm
- http://m.blog.fcful.cn/bnews/3195572.htm
- http://m.blog.fcful.cn/bnews/0907230.htm
- http://m.blog.fcful.cn/bnews/81707.htm
- http://m.blog.fcful.cn/bnews/49881.htm
- http://m.blog.fcful.cn/bnews/2555.htm
- http://m.blog.fcful.cn/bnews/99528.htm
- http://m.blog.fcful.cn/bnews/626004.htm
- http://m.blog.fcful.cn/bnews/326631.htm
- http://m.blog.fcful.cn/bnews/9840.htm
- http://m.blog.fcful.cn/bnews/9277590.htm
- http://m.blog.fcful.cn/bnews/191748.htm
- http://m.blog.fcful.cn/bnews/64118.htm
- http://m.blog.fcful.cn/bnews/35256.htm
- http://m.blog.fcful.cn/bnews/83670.htm
- http://m.blog.fcful.cn/bnews/1250370.htm
- http://m.blog.fcful.cn/bnews/814770.htm
- http://m.blog.fcful.cn/bnews/46673.htm
- http://m.blog.fcful.cn/bnews/1720.htm
- http://m.blog.fcful.cn/bnews/3153880.htm
- http://m.blog.fcful.cn/bnews/1734303.htm
- http://m.blog.fcful.cn/bnews/347135.htm
- http://m.blog.fcful.cn/bnews/4689000.htm
- http://m.blog.fcful.cn/bnews/15412.htm
- http://m.blog.fcful.cn/bnews/37897.htm
- http://m.blog.fcful.cn/bnews/2455.htm
- http://m.blog.fcful.cn/bnews/221098.htm
- http://m.blog.fcful.cn/bnews/6848639.htm
- http://m.blog.fcful.cn/bnews/0822602.htm
- http://m.blog.fcful.cn/bnews/070404.htm
- http://m.blog.fcful.cn/bnews/7791658.htm
- http://m.blog.fcful.cn/bnews/1595376.htm
- http://m.blog.fcful.cn/bnews/9134.htm
- http://m.blog.fcful.cn/bnews/7642073.htm
- http://m.blog.fcful.cn/bnews/800171.htm
- http://m.blog.fcful.cn/bnews/7821033.htm
- http://m.blog.fcful.cn/bnews/432966.htm
- http://m.blog.fcful.cn/bnews/3283357.htm
- http://m.blog.fcful.cn/bnews/84605.htm
- http://m.blog.fcful.cn/bnews/6935.htm
- http://m.blog.fcful.cn/bnews/69231.htm
- http://m.blog.fcful.cn/bnews/29748.htm
- http://m.blog.fcful.cn/bnews/9543009.htm
- http://m.blog.fcful.cn/bnews/623961.htm
- http://m.blog.fcful.cn/bnews/26560.htm
- http://m.blog.fcful.cn/bnews/922783.htm
- http://m.blog.fcful.cn/bnews/2079163.htm
- http://m.blog.fcful.cn/bnews/7377495.htm
- http://m.blog.fcful.cn/bnews/038759.htm
- http://m.blog.fcful.cn/bnews/0881000.htm
- http://m.blog.fcful.cn/bnews/82243.htm
- http://m.blog.fcful.cn/bnews/1973012.htm
- http://m.blog.fcful.cn/bnews/0074359.htm
- http://m.blog.fcful.cn/bnews/4237.htm
- http://m.blog.fcful.cn/bnews/7255577.htm
- http://m.blog.fcful.cn/bnews/5974526.htm
- http://m.blog.fcful.cn/bnews/698421.htm
- http://m.blog.fcful.cn/bnews/2423838.htm
- http://m.blog.fcful.cn/bnews/932904.htm
- http://m.blog.fcful.cn/bnews/41329.htm
- http://m.blog.fcful.cn/bnews/4341882.htm
- http://m.blog.fcful.cn/bnews/473752.htm
- http://m.blog.fcful.cn/bnews/3454447.htm
- http://m.blog.fcful.cn/bnews/922941.htm
- http://m.blog.fcful.cn/bnews/24073.htm
- http://m.blog.fcful.cn/bnews/8709.htm
- http://m.blog.fcful.cn/bnews/35996.htm
- http://m.blog.fcful.cn/bnews/891777.htm
- http://m.blog.fcful.cn/bnews/047451.htm
- http://m.blog.fcful.cn/bnews/55397.htm
- http://m.blog.fcful.cn/bnews/0857.htm
- http://m.blog.fcful.cn/bnews/0534.htm
- http://m.blog.fcful.cn/bnews/366153.htm
- http://m.blog.fcful.cn/bnews/6637.htm
- http://m.blog.fcful.cn/bnews/91793.htm
- http://m.blog.fcful.cn/bnews/1389005.htm
- http://m.blog.fcful.cn/bnews/52222.htm
- http://m.blog.fcful.cn/bnews/0358.htm
- http://m.blog.fcful.cn/bnews/220377.htm
- http://m.blog.fcful.cn/bnews/54310.htm
- http://m.blog.fcful.cn/bnews/5579.htm
- http://m.blog.fcful.cn/bnews/0157675.htm
- http://m.blog.fcful.cn/bnews/4576267.htm
- http://m.blog.fcful.cn/bnews/18784.htm
- http://m.blog.fcful.cn/bnews/28024.htm
- http://m.blog.fcful.cn/bnews/94038.htm
- http://m.blog.fcful.cn/bnews/66776.htm
- http://m.blog.fcful.cn/bnews/52380.htm
- http://m.blog.fcful.cn/bnews/0245226.htm
- http://m.blog.fcful.cn/bnews/679964.htm
- http://m.blog.fcful.cn/bnews/4031090.htm
- http://m.blog.fcful.cn/bnews/1175.htm
- http://m.blog.fcful.cn/bnews/61641.htm
- http://m.blog.fcful.cn/bnews/152038.htm
- http://m.blog.fcful.cn/bnews/7673992.htm
- http://m.blog.fcful.cn/bnews/504060.htm
- http://m.blog.fcful.cn/bnews/5541.htm
- http://m.blog.fcful.cn/bnews/804513.htm
- http://m.blog.fcful.cn/bnews/4622062.htm
- http://m.blog.fcful.cn/bnews/8610709.htm
- http://m.blog.fcful.cn/bnews/7815.htm
- http://m.blog.fcful.cn/bnews/474811.htm
- http://m.blog.fcful.cn/bnews/5065611.htm
- http://m.blog.fcful.cn/bnews/7849436.htm
- http://m.blog.fcful.cn/bnews/3666895.htm
- http://m.blog.fcful.cn/bnews/785563.htm
- http://m.blog.fcful.cn/bnews/2325799.htm
- http://m.blog.fcful.cn/bnews/2789893.htm
- http://m.blog.fcful.cn/bnews/6143647.htm
- http://m.blog.fcful.cn/bnews/018813.htm
- http://m.blog.fcful.cn/bnews/8308.htm
- http://m.blog.fcful.cn/bnews/08543.htm
- http://m.blog.fcful.cn/bnews/19953.htm
- http://m.blog.fcful.cn/bnews/461782.htm
- http://m.blog.fcful.cn/bnews/4913003.htm
- http://m.blog.fcful.cn/bnews/0437248.htm
- http://m.blog.fcful.cn/bnews/1305655.htm
- http://m.blog.fcful.cn/bnews/746265.htm
- http://m.blog.fcful.cn/bnews/1813760.htm
- http://m.blog.fcful.cn/bnews/49955.htm
- http://m.blog.fcful.cn/bnews/63618.htm
- http://m.blog.fcful.cn/bnews/6933.htm

## 项目结构

项目采用标准的前后端分离目录组织方式，核心代码与资源文件分类清晰，便于维护与扩展。

```
linkcatalog/
├── backend/                        # 后端服务源代码目录
│   ├── src/
│   │   ├── controllers/            # 请求控制器，处理路由入参及响应封装
│   │   ├── models/                 # 数据模型层，定义资源条目、标签、访问日志等数据结构
│   │   ├── services/               # 业务逻辑层，包含检索、状态监测、统计聚合等核心服务
│   │   ├── middlewares/            # 中间件，包含身份验证、日志记录、跨域处理等
│   │   ├── routes/                 # 路由定义，映射 API 端点至对应控制器方法
│   │   ├── utils/                  # 通用工具函数，如 URL 解析、时间格式化、加密哈希
│   │   └── app.js                  # 后端应用入口，初始化 Express 应用与中间件链
│   ├── tests/                      # 单元测试与集成测试用例，基于 Jest 框架
│   ├── package.json                # 后端依赖声明与脚本配置
│   └── .env.example                # 环境变量示例文件，包含数据库连接与端口配置
├── frontend/                       # 前端展示与管理界面源码目录
│   ├── public/                     # 静态资源，如 favicon 与 robots.txt
│   ├── src/
│   │   ├── components/             # 可复用的 UI 组件，包括链接卡片、搜索栏、分类树
│   │   ├── pages/                  # 路由页面组件，如首页、分类视图、管理后台面板
│   │   ├── hooks/                  # 自定义 React Hooks，封装数据请求与状态逻辑
│   │   ├── services/               # API 调用封装，与后端接口进行通信
│   │   ├── stores/                 # 全局状态管理（基于 Zustand 或 Redux），维护用户偏好与缓存
│   │   ├── styles/                 # 全局样式表与主题变量，基于 CSS Modules
│   │   ├── App.jsx                 # 根组件，配置路由与全局布局
│   │   └── main.jsx                # 前端入口文件，渲染根组件至 DOM
│   ├── index.html                  # 主页面模板
│   ├── package.json                # 前端依赖声明与构建脚本
│   └── vite.config.js              # Vite 构建工具配置文件
├── docs/                           # 项目文档目录
│   ├── getting-started.md          # 快速入门指南
│   ├── configuration.md            # 配置参数详解
│   ├── api-reference.md            # 完整 API 接口文档
│   └── deployment.md               # 生产环境部署说明
├── scripts/                        # 辅助脚本目录
│   ├── seed-db.js                  # 初始化数据库并填充示例数据
│   ├── health-check.js             # 手动触发链接状态检测的脚本
│   └── migrate-db.js               # 数据库迁移与版本升级工具
├── data/                           # 本地数据存储目录（默认被 .gitignore 忽略）
│   └── linkcatalog.db              # SQLite 数据库文件（首次启动时自动生成）
├── logs/                           # 应用日志目录（默认被 .gitignore 忽略）
│   ├── access.log                  # HTTP 请求访问日志
│   └── error.log                   # 应用错误与异常堆栈日志
├── .gitignore                      # Git 版本控制忽略文件配置
├── LICENSE                         # 项目许可证文件（MIT）
├── README.md                       # 项目概览与说明文档（即本文档）
├── package.json                    # 根目录 package.json，用于管理整体项目脚本（如同时启动前后端）
└── docker-compose.yml              # Docker Compose 编排文件，用于快速启动完整服务栈（含 Redis 可选）
```

## 贡献指南

我们欢迎并感谢任何形式的贡献，包括但不限于提交问题报告、功能请求、代码修复与文档改进。请遵循以下步骤参与本项目。

**提交 Issue 前进行检索**：在新建 Issue 之前，请先浏览已有的 Issues 列表（包括已关闭的），确认您遇到的现象或建议的功能尚未被他人提及。若存在类似议题，可在该议题下补充您的上下文信息。

**Fork 仓库并创建特性分支**：将本仓库 Fork 至您的个人账户，然后基于 `main` 分支创建一个新的分支用于开发，分支命名建议采用 `feature/功能简述` 或 `fix/问题简述` 格式，以便识别。

**遵循代码风格与测试规范**：提交代码前，请确保已运行 ESLint 与 Prettier 进行格式化，并通过所有单元测试（`npm test`）。对于新增功能，需编写对应的测试用例覆盖核心逻辑。

**编写清晰规范的提交信息**：提交信息应使用英文，采用语义化格式，首行概括变更内容（不超过 72 字符），后续可补充详细说明。推荐参考 Conventional Commits 规范。

**发起 Pull Request 并描述变更**：完成开发后，将您的特性分支推送至 Fork 仓库，并向本仓库的 `main` 分支发起 Pull Request。请在 PR 描述中清晰说明变更目的、影响范围以及测试情况，并关联相关的 Issue 编号。

## 常见问题

**问：LinkCatalog 支持 HTTPS 协议的外链吗？对于混合内容是否有安全策略？**

答：LinkCatalog 对收录的外链协议无限制，支持 HTTP 与 HTTPS 资源。在管理面板中添加链接时，系统不会强制转换协议，完全保留用户输入的原始 URL。前端展示页面在加载外部资源时，会遵循现代浏览器的混合内容策略，若主站通过 HTTPS 访问，则自动阻止非安全（HTTP）的被动内容（如图片、脚本），但链接跳转本身不受影响。如需强制所有链接使用 HTTPS，可在配置文件中开启 `normalize_https` 选项。

**问：如何备份与恢复数据库中的数据？**

答：LinkCatalog 默认使用 SQLite 作为存储引擎，其数据库文件位于 `data/linkcatalog.db`。您可直接复制该文件实现全量备份。恢复时，停止应用服务，将备份文件覆盖至原位置，然后重启服务即可。若使用 MySQL 或 PostgreSQL 作为生产数据库，可使用对应数据库的原生工具（如 `mysqldump` 或 `pg_dump`）进行逻辑备份。项目也提供了 `scripts/seed-db.js` 与 `scripts/migrate-db.js` 辅助数据导入与结构迁移。

**问：状态监测任务对网络环境有何要求？如何调整监测频率？**

答：状态监测模块依赖运行主机的网络出站能力，需确保可访问公网或目标内网地址。默认监测间隔为 6 小时，每次检测超时时间为 5 秒。您可在 `backend/src/services/healthCheckService.js` 中调整 `CHECK_INTERVAL_MS` 与 `TIMEOUT_MS` 常量，或通过环境变量 `HEALTH_CHECK_INTERVAL` 与 `HEALTH_TIMEOUT` 进行运行时配置。对于数量庞大的资源库，建议适当延长间隔以避免触发目标站点的访问频率限制。

## 许可证

MIT License。详见项目根目录下的 LICENSE 文件。

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
