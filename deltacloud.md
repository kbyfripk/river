# GQSKJ Navigation Index

GQSKJ Navigation Index 是一个面向移动端资讯聚合与深度内容检索的开源导航工具，专注于对 gqskj.cn 域名下海量动态新闻页面进行结构化整理与分类索引。该项目服务于需要快速检索特定编号新闻内容、追踪行业动态或进行历史资讯回溯的技术人员、内容运营者与研究人员，通过提供清晰的资源清单与本地化的检索环境，降低对第三方搜索引擎的依赖，提升内容定位效率。

该项目定位为轻量级、可自部署的资讯导航站点，核心功能围绕 URL 资源的分类展示与快速跳转展开。项目本身不存储任何新闻内容，仅提供索引与导航能力，所有原始内容均实时指向源站。通过本项目，用户可以在本地快速搭建一套属于自己的资讯入口，避免在冗长的历史记录中反复查找特定编号的新闻页面。

## 功能概览

海量资讯链接索引：内置超过两百条 gqskj.cn 域名下的新闻页面链接，覆盖多批次、多主题的资讯内容，形成可长期维护的导航列表。

按编号快速检索：所有资源链接均以新闻编号为区分，用户可通过编号快速定位目标内容，无需记忆完整 URL 路径。

本地化部署支持：项目提供完整的本地运行环境配置方案，用户可在内网或本地主机上快速启动导航服务，实现私有化资讯入口。

移动端优先适配：所有链接均来源于移动端页面（m.wap 子域名），项目整体针对移动设备浏览体验进行优化，确保在手机与平板上操作流畅。

纯净无冗余设计：项目不包含广告模块、用户追踪脚本或第三方统计代码，仅提供纯粹的导航与跳转功能，保障用户访问隐私。

定期维护机制：项目维护者会根据源站内容更新情况，定期核对链接可用性，并清理失效条目，确保资源列表的长期有效性。

可扩展分类体系：内置的资源列表支持按主题、时间或编号范围进行二次分类，用户可根据自身需求调整索引结构。

零外部依赖运行：项目核心功能不依赖任何外部 API 或数据库服务，仅需基本的 Web 服务器环境即可完整运行。

## 应用场景

个人知识管理辅助：研究人员或内容收集者可将本项目作为资讯入口，配合本地笔记工具，对特定编号的新闻内容进行标注、摘录与归档，构建个人化的行业知识库。

团队内部资讯共享：小型团队或部门可在内网部署本项目，使所有成员通过统一入口访问行业动态，避免各自使用搜索引擎导致的信息源不一致问题。

历史内容回溯检索：当需要查找某一时间段或某一主题相关的历史新闻时，用户可通过项目提供的编号索引快速定位到对应的 gqskj.cn 页面，大幅提升回溯效率。

离线环境下的导航替代：在无法使用公共搜索引擎的内部网络或离线环境中，本项目可作为预先配置好的资讯导航页，提供有限但明确的资源指向。

内容运营参考工具：内容运营人员可通过定期浏览本项目收录的新闻编号分布，了解 gqskj.cn 平台的内容发布频率与主题趋势，为自身内容策划提供参考。

## 快速开始

以下操作步骤适用于 Linux / macOS / Windows 系统，需提前安装 Git 与 Node.js 环境。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/gqskj-navigation-index.git

# 进入项目根目录
cd gqskj-navigation-index

# 安装项目依赖（使用 npm）
npm install

# 启动本地开发服务器
npm run dev
```

启动成功后，终端将输出本地访问地址，默认为 http://localhost:3000 。在浏览器中打开该地址即可查看导航页面并访问所有收录的资讯链接。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.x 或更高 | 项目运行时的 JavaScript 运行时环境，用于启动开发服务器与构建工具链 |
| npm | 8.x 或更高 | Node.js 包管理器，用于安装项目依赖与执行脚本命令 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与管理代码版本 |
| 现代浏览器 | 最近两个主要版本 | 推荐使用 Chrome、Firefox、Safari 或 Edge 的最新稳定版，以确保页面渲染正常 |
| 网络连接 | 需要访问外网 | 项目本身运行于本地，但所有导航链接指向外部源站，需保证网络可达 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速部署本项目、如何修改导航页面标题与描述 |
| 资源管理 | /docs/resource-management.md | 如何增删改资源链接、如何对链接进行分类与排序 |
| 部署手册 | /docs/deployment.md | 如何将项目部署到生产环境、支持哪些部署平台 |
| 维护指引 | /docs/maintenance.md | 如何定期检查链接有效性、如何提交链接更新请求 |

## 资源列表

- http://m.wap.gqskj.cn/snews/40299.htm
- http://m.wap.gqskj.cn/snews/43864.htm
- http://m.wap.gqskj.cn/snews/4779253.htm
- http://m.wap.gqskj.cn/snews/20548.htm
- http://m.wap.gqskj.cn/snews/4248712.htm
- http://m.wap.gqskj.cn/snews/566546.htm
- http://m.wap.gqskj.cn/snews/087315.htm
- http://m.wap.gqskj.cn/snews/1101891.htm
- http://m.wap.gqskj.cn/snews/1164740.htm
- http://m.wap.gqskj.cn/snews/0629.htm
- http://m.wap.gqskj.cn/snews/212071.htm
- http://m.wap.gqskj.cn/snews/1177796.htm
- http://m.wap.gqskj.cn/snews/8814757.htm
- http://m.wap.gqskj.cn/snews/29775.htm
- http://m.wap.gqskj.cn/snews/21842.htm
- http://m.wap.gqskj.cn/snews/503614.htm
- http://m.wap.gqskj.cn/snews/084351.htm
- http://m.wap.gqskj.cn/snews/79581.htm
- http://m.wap.gqskj.cn/snews/2676948.htm
- http://m.wap.gqskj.cn/snews/70611.htm
- http://m.wap.gqskj.cn/snews/3202266.htm
- http://m.wap.gqskj.cn/snews/097377.htm
- http://m.wap.gqskj.cn/snews/87703.htm
- http://m.wap.gqskj.cn/snews/2386867.htm
- http://m.wap.gqskj.cn/snews/1168428.htm
- http://m.wap.gqskj.cn/snews/5107.htm
- http://m.wap.gqskj.cn/snews/096492.htm
- http://m.wap.gqskj.cn/snews/6485.htm
- http://m.wap.gqskj.cn/snews/653797.htm
- http://m.wap.gqskj.cn/snews/538520.htm
- http://m.wap.gqskj.cn/snews/6677.htm
- http://m.wap.gqskj.cn/snews/340689.htm
- http://m.wap.gqskj.cn/snews/9477.htm
- http://m.wap.gqskj.cn/snews/656896.htm
- http://m.wap.gqskj.cn/snews/5779076.htm
- http://m.wap.gqskj.cn/snews/2970067.htm
- http://m.wap.gqskj.cn/snews/629169.htm
- http://m.wap.gqskj.cn/snews/7266.htm
- http://m.wap.gqskj.cn/snews/988722.htm
- http://m.wap.gqskj.cn/snews/74698.htm
- http://m.wap.gqskj.cn/snews/453083.htm
- http://m.wap.gqskj.cn/snews/73817.htm
- http://m.wap.gqskj.cn/snews/636654.htm
- http://m.wap.gqskj.cn/snews/12078.htm
- http://m.wap.gqskj.cn/snews/7196.htm
- http://m.wap.gqskj.cn/snews/5120.htm
- http://m.wap.gqskj.cn/snews/648578.htm
- http://m.wap.gqskj.cn/snews/850117.htm
- http://m.wap.gqskj.cn/snews/9296.htm
- http://m.wap.gqskj.cn/snews/2932161.htm
- http://m.wap.gqskj.cn/snews/6146.htm
- http://m.wap.gqskj.cn/snews/5601876.htm
- http://m.wap.gqskj.cn/snews/9636.htm
- http://m.wap.gqskj.cn/snews/8863.htm
- http://m.wap.gqskj.cn/snews/402346.htm
- http://m.wap.gqskj.cn/snews/6550384.htm
- http://m.wap.gqskj.cn/snews/3733394.htm
- http://m.wap.gqskj.cn/snews/313649.htm
- http://m.wap.gqskj.cn/snews/2573.htm
- http://m.wap.gqskj.cn/snews/2883.htm
- http://m.wap.gqskj.cn/snews/2139.htm
- http://m.wap.gqskj.cn/snews/1709.htm
- http://m.wap.gqskj.cn/snews/15430.htm
- http://m.wap.gqskj.cn/snews/16052.htm
- http://m.wap.gqskj.cn/snews/85700.htm
- http://m.wap.gqskj.cn/snews/6653755.htm
- http://m.wap.gqskj.cn/snews/98810.htm
- http://m.wap.gqskj.cn/snews/187337.htm
- http://m.wap.gqskj.cn/snews/0510668.htm
- http://m.wap.gqskj.cn/snews/720822.htm
- http://m.wap.gqskj.cn/snews/8793814.htm
- http://m.wap.gqskj.cn/snews/79319.htm
- http://m.wap.gqskj.cn/snews/8283.htm
- http://m.wap.gqskj.cn/snews/3951.htm
- http://m.wap.gqskj.cn/snews/557086.htm
- http://m.wap.gqskj.cn/snews/6035457.htm
- http://m.wap.gqskj.cn/snews/257614.htm
- http://m.wap.gqskj.cn/snews/1484961.htm
- http://m.wap.gqskj.cn/snews/9818.htm
- http://m.wap.gqskj.cn/snews/007547.htm
- http://m.wap.gqskj.cn/snews/380761.htm
- http://m.wap.gqskj.cn/snews/6771.htm
- http://m.wap.gqskj.cn/snews/469440.htm
- http://m.wap.gqskj.cn/snews/09621.htm
- http://m.wap.gqskj.cn/snews/7795.htm
- http://m.wap.gqskj.cn/snews/9560703.htm
- http://m.wap.gqskj.cn/snews/1786.htm
- http://m.wap.gqskj.cn/snews/8446296.htm
- http://m.wap.gqskj.cn/snews/415710.htm
- http://m.wap.gqskj.cn/snews/1575624.htm
- http://m.wap.gqskj.cn/snews/4301497.htm
- http://m.wap.gqskj.cn/snews/3957.htm
- http://m.wap.gqskj.cn/snews/7874.htm
- http://m.wap.gqskj.cn/snews/1101842.htm
- http://m.wap.gqskj.cn/snews/57677.htm
- http://m.wap.gqskj.cn/snews/16995.htm
- http://m.wap.gqskj.cn/snews/8412095.htm
- http://m.wap.gqskj.cn/snews/9980463.htm
- http://m.wap.gqskj.cn/snews/623522.htm
- http://m.wap.gqskj.cn/snews/8827.htm
- http://m.wap.gqskj.cn/snews/5814.htm
- http://m.wap.gqskj.cn/snews/993644.htm
- http://m.wap.gqskj.cn/snews/7033320.htm
- http://m.wap.gqskj.cn/snews/3521647.htm
- http://m.wap.gqskj.cn/snews/8378.htm
- http://m.wap.gqskj.cn/snews/4440.htm
- http://m.wap.gqskj.cn/snews/0804.htm
- http://m.wap.gqskj.cn/snews/478635.htm
- http://m.wap.gqskj.cn/snews/479568.htm
- http://m.wap.gqskj.cn/snews/37503.htm
- http://m.wap.gqskj.cn/snews/338115.htm
- http://m.wap.gqskj.cn/snews/4225409.htm
- http://m.wap.gqskj.cn/snews/0851486.htm
- http://m.wap.gqskj.cn/snews/6282.htm
- http://m.wap.gqskj.cn/snews/7010397.htm
- http://m.wap.gqskj.cn/snews/424279.htm
- http://m.wap.gqskj.cn/snews/9780.htm
- http://m.wap.gqskj.cn/snews/4321455.htm
- http://m.wap.gqskj.cn/snews/640432.htm
- http://m.wap.gqskj.cn/snews/3811.htm
- http://m.wap.gqskj.cn/snews/4482.htm
- http://m.wap.gqskj.cn/snews/51802.htm
- http://m.wap.gqskj.cn/snews/864624.htm
- http://m.wap.gqskj.cn/snews/1180.htm
- http://m.wap.gqskj.cn/snews/552596.htm
- http://m.wap.gqskj.cn/snews/23386.htm
- http://m.wap.gqskj.cn/snews/726877.htm
- http://m.wap.gqskj.cn/snews/92797.htm
- http://m.wap.gqskj.cn/snews/88008.htm
- http://m.wap.gqskj.cn/snews/642516.htm
- http://m.wap.gqskj.cn/snews/6336.htm
- http://m.wap.gqskj.cn/snews/85975.htm
- http://m.wap.gqskj.cn/snews/5627.htm
- http://m.wap.gqskj.cn/snews/94960.htm
- http://m.wap.gqskj.cn/snews/5678.htm
- http://m.wap.gqskj.cn/snews/5191.htm
- http://m.wap.gqskj.cn/snews/1778359.htm
- http://m.wap.gqskj.cn/snews/0068850.htm
- http://m.wap.gqskj.cn/snews/0237982.htm
- http://m.wap.gqskj.cn/snews/0953758.htm
- http://m.wap.gqskj.cn/snews/105313.htm
- http://m.wap.gqskj.cn/snews/8341908.htm
- http://m.wap.gqskj.cn/snews/8119.htm
- http://m.wap.gqskj.cn/snews/298309.htm
- http://m.wap.gqskj.cn/snews/6745.htm
- http://m.wap.gqskj.cn/snews/3412962.htm
- http://m.wap.gqskj.cn/snews/94354.htm
- http://m.wap.gqskj.cn/snews/79737.htm
- http://m.wap.gqskj.cn/snews/9351277.htm
- http://m.wap.gqskj.cn/snews/282225.htm
- http://m.wap.gqskj.cn/snews/45625.htm
- http://m.wap.gqskj.cn/snews/2278.htm
- http://m.wap.gqskj.cn/snews/5971.htm
- http://m.wap.gqskj.cn/snews/195518.htm
- http://m.wap.gqskj.cn/snews/02966.htm
- http://m.wap.gqskj.cn/snews/4120.htm
- http://m.wap.gqskj.cn/snews/702094.htm
- http://m.wap.gqskj.cn/snews/166606.htm
- http://m.wap.gqskj.cn/snews/493521.htm
- http://m.wap.gqskj.cn/snews/558320.htm
- http://m.wap.gqskj.cn/snews/156877.htm
- http://m.wap.gqskj.cn/snews/166360.htm
- http://m.wap.gqskj.cn/snews/10674.htm
- http://m.wap.gqskj.cn/snews/685150.htm
- http://m.wap.gqskj.cn/snews/09346.htm
- http://m.wap.gqskj.cn/snews/4867196.htm
- http://m.wap.gqskj.cn/snews/9313105.htm
- http://m.wap.gqskj.cn/snews/3949.htm
- http://m.wap.gqskj.cn/snews/43924.htm
- http://m.wap.gqskj.cn/snews/456904.htm
- http://m.wap.gqskj.cn/snews/16037.htm
- http://m.wap.gqskj.cn/snews/2874556.htm
- http://m.wap.gqskj.cn/snews/7105.htm
- http://m.wap.gqskj.cn/snews/8740138.htm
- http://m.wap.gqskj.cn/snews/1698228.htm
- http://m.wap.gqskj.cn/snews/3986.htm
- http://m.wap.gqskj.cn/snews/5638.htm
- http://m.wap.gqskj.cn/snews/1021908.htm
- http://m.wap.gqskj.cn/snews/584967.htm
- http://m.wap.gqskj.cn/snews/3055968.htm
- http://m.wap.gqskj.cn/snews/569723.htm
- http://m.wap.gqskj.cn/snews/348183.htm
- http://m.wap.gqskj.cn/snews/1917627.htm
- http://m.wap.gqskj.cn/snews/208699.htm
- http://m.wap.gqskj.cn/snews/5336422.htm
- http://m.wap.gqskj.cn/snews/926370.htm
- http://m.wap.gqskj.cn/snews/2270393.htm
- http://m.wap.gqskj.cn/snews/0730.htm
- http://m.wap.gqskj.cn/snews/74131.htm
- http://m.wap.gqskj.cn/snews/60643.htm
- http://m.wap.gqskj.cn/snews/5312.htm
- http://m.wap.gqskj.cn/snews/2393148.htm
- http://m.wap.gqskj.cn/snews/4510.htm
- http://m.wap.gqskj.cn/snews/4024945.htm
- http://m.wap.gqskj.cn/snews/0301.htm
- http://m.wap.gqskj.cn/snews/1058032.htm
- http://m.wap.gqskj.cn/snews/8784290.htm
- http://m.wap.gqskj.cn/snews/29876.htm
- http://m.wap.gqskj.cn/snews/19597.htm
- http://m.wap.gqskj.cn/snews/94043.htm
- http://m.wap.gqskj.cn/snews/54521.htm
- http://m.wap.gqskj.cn/snews/3007.htm
- http://m.wap.gqskj.cn/snews/8083386.htm
- http://m.wap.gqskj.cn/snews/58654.htm
- http://m.wap.gqskj.cn/snews/7489.htm
- http://m.wap.gqskj.cn/snews/620414.htm
- http://m.wap.gqskj.cn/snews/71177.htm
- http://m.wap.gqskj.cn/snews/73069.htm
- http://m.wap.gqskj.cn/snews/4897581.htm
- http://m.wap.gqskj.cn/snews/80679.htm
- http://m.wap.gqskj.cn/snews/7026384.htm
- http://m.wap.gqskj.cn/snews/228784.htm
- http://m.wap.gqskj.cn/snews/0630.htm
- http://m.wap.gqskj.cn/snews/4284306.htm
- http://m.wap.gqskj.cn/snews/4712.htm
- http://m.wap.gqskj.cn/snews/60675.htm
- http://m.wap.gqskj.cn/snews/73161.htm
- http://m.wap.gqskj.cn/snews/8336097.htm
- http://m.wap.gqskj.cn/snews/01229.htm
- http://m.wap.gqskj.cn/snews/5848209.htm
- http://m.wap.gqskj.cn/snews/70532.htm
- http://m.wap.gqskj.cn/snews/18274.htm
- http://m.wap.gqskj.cn/snews/28731.htm
- http://m.wap.gqskj.cn/snews/898368.htm
- http://m.wap.gqskj.cn/snews/61247.htm
- http://m.wap.gqskj.cn/snews/71358.htm
- http://m.wap.gqskj.cn/snews/175196.htm
- http://m.wap.gqskj.cn/snews/85628.htm
- http://m.wap.gqskj.cn/snews/2554.htm
- http://m.wap.gqskj.cn/snews/539170.htm
- http://m.wap.gqskj.cn/snews/9538701.htm
- http://m.wap.gqskj.cn/snews/260272.htm
- http://m.wap.gqskj.cn/snews/5206494.htm
- http://m.wap.gqskj.cn/snews/7685.htm
- http://m.wap.gqskj.cn/snews/8947670.htm
- http://m.wap.gqskj.cn/snews/9080.htm
- http://m.wap.gqskj.cn/snews/2725.htm
- http://m.wap.gqskj.cn/snews/534375.htm
- http://m.wap.gqskj.cn/snews/890877.htm
- http://m.wap.gqskj.cn/snews/6366.htm
- http://m.wap.gqskj.cn/snews/987480.htm
- http://m.wap.gqskj.cn/snews/818508.htm
- http://m.wap.gqskj.cn/snews/5459.htm
- http://m.wap.gqskj.cn/snews/71651.htm
- http://m.wap.gqskj.cn/snews/552117.htm
- http://m.wap.gqskj.cn/snews/44695.htm
- http://m.wap.gqskj.cn/snews/9120.htm
- http://m.wap.gqskj.cn/snews/2336.htm
- http://m.wap.gqskj.cn/snews/880544.htm
- http://m.wap.gqskj.cn/snews/8876.htm

## 项目结构

```
gqskj-navigation-index/
├── public/                         # 静态资源目录
│   ├── index.html                  # 导航页面主入口 HTML 模板
│   └── favicon.ico                 # 站点图标文件
├── src/                            # 源代码主目录
│   ├── assets/                     # 资源文件目录，存放图片、字体等
│   │   └── logo.svg                # 项目标识图形文件
│   ├── components/                 # 前端组件目录，存放可复用 UI 组件
│   │   ├── NavList.vue             # 导航列表渲染组件，负责展示所有资源链接
│   │   ├── SearchBar.vue           # 搜索栏组件，提供按编号过滤功能
│   │   └── Footer.vue              # 页脚组件，显示版本与版权信息
│   ├── data/                       # 数据目录，存放资源列表与配置
│   │   ├── links.json              # 所有导航链接的 JSON 数据文件
│   │   └── categories.json         # 链接分类映射配置文件
│   ├── styles/                     # 样式目录
│   │   ├── main.css                # 全局基础样式定义
│   │   └── mobile.css              # 移动端响应式样式覆盖
│   └── utils/                      # 工具函数目录
│       └── linkValidator.js        # 链接有效性校验工具模块
├── docs/                           # 项目文档目录
│   ├── getting-started.md          # 入门指南文档
│   ├── resource-management.md      # 资源管理操作文档
│   ├── deployment.md               # 生产环境部署文档
│   └── maintenance.md              # 项目长期维护指引
├── scripts/                        # 辅助脚本目录
│   ├── check-links.js              # 批量检查链接可用性的脚本
│   └── generate-sitemap.js         # 生成站点地图的脚本
├── tests/                          # 测试目录
│   └── linkValidator.test.js       # 链接校验工具单元测试
├── .gitignore                      # Git 版本控制忽略文件配置
├── package.json                    # npm 项目配置文件，声明依赖与脚本
├── package-lock.json               # npm 依赖锁定文件
└── README.md                       # 项目说明文档（本文件）
```

## 贡献指南

提交 Issue 报告问题：如果你发现某个导航链接无法访问，或者项目运行过程中出现异常，请在 GitHub Issues 中提交详细的问题报告，包含操作系统版本、Node.js 版本以及完整的错误日志。

发起 Pull Request 改进代码：欢迎对项目代码进行优化或新增功能。请先从主分支创建新的功能分支，完成开发后提交 Pull Request，并在描述中说明改动内容与测试结果。

补充或更新资源链接：如果你发现 gqskj.cn 域名下有新的有价值新闻页面，或者某些已有链接已失效，请按照资源管理文档中的格式要求，提交链接增删改的请求。

完善项目文档：帮助改进 README、入门指南或部署手册中的描述不清晰之处，或翻译文档至其他语言，均属于有效贡献。

参与链接可用性巡检：定期运行项目内置的链接检查脚本，并将检测到的失效链接列表提交至 Issues，协助维护资源列表的健康度。

## 常见问题

问题：启动开发服务器后，页面能正常打开，但点击导航链接无法跳转，浏览器提示“无法访问此网站”。

回答：此情况通常由网络环境导致。项目本身仅提供链接跳转功能，所有导航链接指向外部源站 m.wap.gqskj.cn 。请检查当前设备是否能够正常访问该域名，必要时切换网络环境或配置代理。同时可运行 scripts/check-links.js 脚本确认目标链接是否仍然有效。

问题：我想在导航页面中新增或删除资源链接，应该如何操作？

回答：所有导航链接统一存储在 src/data/links.json 文件中。你只需按照该文件既有的 JSON 格式，在数组中新增或移除对应的 URL 字符串即可。修改保存后，开发服务器将自动热重载，页面会同步更新。如需批量修改，建议使用脚本处理。

问题：项目是否支持部署到静态托管平台，如 Vercel 或 Netlify？

回答：支持。本项目构建后输出纯静态文件，你可以运行 npm run build 命令生成 dist 目录，然后将该目录下的所有文件上传至任何支持静态网站托管的平台。具体部署步骤请参考文档中的部署手册章节。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
