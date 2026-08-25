# WebIndex Content Aggregator

WebIndex Content Aggregator 是一个面向技术内容聚合与导航的开源工具集，专门用于采集、整理和展示来自移动端资讯源的结构化数据。该项目定位于为开发者、数据分析师和内容运营人员提供一套轻量级的资讯链接管理方案，能够将散落的移动端 HTML 资讯页面转化为可检索、可分类、可监控的统一资源索引。

项目采用模块化设计，核心功能围绕移动端资讯页面的元数据抽取、链接去重、时效性标记和静态站点生成展开。通过配置化的采集规则和模板渲染机制，使用者可以在不编写复杂爬虫代码的情况下，快速建立起针对特定域名下资讯内容的自动化整理流程。项目天然适配个人知识库构建、垂直领域资讯监控、以及轻量级内容聚合站点的搭建需求。

## 功能概览

**批量链接采集与去重**：支持从指定域名前缀下递归采集 HTML 页面链接，基于 URL 特征库自动过滤非资讯类路径，并对采集结果进行 MD5 哈希去重，确保索引库的整洁性。

**元数据智能抽取**：内置针对移动端资讯页面的元数据解析引擎，可自动抽取标题、发布时间、正文摘要、来源标识等信息，支持常见移动端 HTML 结构模板的自适应匹配。

**分类标签自动生成**：基于 URL 路径中的数字特征和页面内容关键词，自动为每条链接生成一级分类和二级标签，便于后续按主题维度进行筛选和展示。

**静态站点渲染引擎**：内置基于 Go Template 的静态页面生成器，可将采集并整理后的链接数据渲染为完整的 HTML 站点，支持首页列表、分类归档、详情页三种视图模式。

**增量更新与变更监控**：支持设定定时任务对目标域名进行增量采集，自动检测新增链接和失效链接，并通过生成变更报告的方式通知使用者，保持索引数据的时效性。

**命令行交互工具**：提供完整的 CLI 工具链，涵盖采集、解析、去重、渲染、校验等子命令，支持通过配置文件批量管理多个采集源，适合集成到 CI/CD 或定时任务体系中。

## 应用场景

个人技术博客的资讯聚合板块：技术博主可以使用 WebIndex 自动采集特定移动资讯站点上与自己关注领域相关的文章链接，生成一个持续更新的推荐阅读列表，嵌入到个人博客的侧边栏或独立页面中，为访客提供额外的内容延伸。

垂直领域舆情监控看板：产品经理或市场运营人员可以配置针对竞品关键词或行业动态的采集规则，将 WebIndex 生成的静态站点部署到内网服务器，作为团队内部的每日资讯速览看板，减少人工检索成本。

开源项目文档站的外部参考索引：开源项目维护者可以在项目文档中集成 WebIndex 生成的链接索引页，用于推荐外部相关的技术讨论、案例分析和社区动态，丰富项目生态的参考资料体系。

个人知识管理系统的输入源：知识管理爱好者可以将 WebIndex 作为信息输入管道的一部分，定时采集并导出链接列表，再配合标签系统导入到个人的笔记软件或知识库中，形成从信息发现到知识沉淀的完整链路。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/webindex-aggregator.git

# 进入项目目录
cd webindex-aggregator

# 安装依赖（基于 Go Modules）
go mod download

# 复制示例配置文件并进行必要修改
cp config.example.yaml config.yaml

# 执行采集与渲染命令
./webindex collect --config config.yaml
./webindex render --config config.yaml

# 生成的静态站点默认输出到 ./dist 目录，可直接使用浏览器打开 index.html
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Go 语言环境 | 1.21 及以上 | 项目核心开发语言，用于编译 CLI 工具和运行采集引擎 |
| Git | 2.30 及以上 | 用于克隆仓库和管理版本依赖 |
| GNU Make | 3.81 及以上 | 提供构建脚本和任务编排能力，简化编译流程 |
| SQLite 3 | 3.35 及以上 | 作为默认的链接索引存储引擎，支持并发读写和轻量级查询 |
| Chroma 语法高亮库 | 最新稳定版 | 用于渲染代码块时提供语法高亮支持，增强页面可读性 |
| 系统内存 | 512MB 以上 | 采集大规模链接时需保证足够的内存用于缓存和去重计算 |
| 存储空间 | 200MB 以上 | 用于存放 SQLite 数据库文件和生成的静态 HTML 页面 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 入门指南 | docs/getting-started.md | 如何从零开始配置采集源并生成第一个索引站点；配置文件中的必填项和可选插件说明 |
| 采集规则 | docs/collection-rules.md | 如何编写匹配移动端资讯 URL 的规则表达式；如何处理反爬策略和动态加载内容 |
| 元数据配置 | docs/metadata-config.md | 如何针对不同页面结构定制标题和摘要的抽取模板；如何使用 CSS 选择器定位关键信息 |
| 部署与运维 | docs/deployment.md | 如何将生成的静态站点部署到 Nginx、CDN 或对象存储；如何设置定时采集任务 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/66665.htm
- http://m.3g.gqskj.cn/xnews/00599.htm
- http://m.3g.gqskj.cn/xnews/9842.htm
- http://m.3g.gqskj.cn/xnews/110554.htm
- http://m.3g.gqskj.cn/xnews/9080168.htm
- http://m.3g.gqskj.cn/xnews/807934.htm
- http://m.3g.gqskj.cn/xnews/2737735.htm
- http://m.3g.gqskj.cn/xnews/0790.htm
- http://m.3g.gqskj.cn/xnews/09051.htm
- http://m.3g.gqskj.cn/xnews/321862.htm
- http://m.3g.gqskj.cn/xnews/052646.htm
- http://m.3g.gqskj.cn/xnews/2131.htm
- http://m.3g.gqskj.cn/xnews/06305.htm
- http://m.3g.gqskj.cn/xnews/972094.htm
- http://m.3g.gqskj.cn/xnews/84614.htm
- http://m.3g.gqskj.cn/xnews/008318.htm
- http://m.3g.gqskj.cn/xnews/24428.htm
- http://m.3g.gqskj.cn/xnews/9745975.htm
- http://m.3g.gqskj.cn/xnews/15706.htm
- http://m.3g.gqskj.cn/xnews/8722782.htm
- http://m.3g.gqskj.cn/xnews/8980495.htm
- http://m.3g.gqskj.cn/xnews/9805.htm
- http://m.3g.gqskj.cn/xnews/307210.htm
- http://m.3g.gqskj.cn/xnews/92679.htm
- http://m.3g.gqskj.cn/xnews/8507594.htm
- http://m.3g.gqskj.cn/xnews/0154.htm
- http://m.3g.gqskj.cn/xnews/62094.htm
- http://m.3g.gqskj.cn/xnews/2822580.htm
- http://m.3g.gqskj.cn/xnews/4524.htm
- http://m.3g.gqskj.cn/xnews/2537208.htm
- http://m.3g.gqskj.cn/xnews/9676.htm
- http://m.3g.gqskj.cn/xnews/2608122.htm
- http://m.3g.gqskj.cn/xnews/1554432.htm
- http://m.3g.gqskj.cn/xnews/575090.htm
- http://m.3g.gqskj.cn/xnews/84123.htm
- http://m.3g.gqskj.cn/xnews/9490.htm
- http://m.3g.gqskj.cn/xnews/6540.htm
- http://m.3g.gqskj.cn/xnews/13465.htm
- http://m.3g.gqskj.cn/xnews/74264.htm
- http://m.3g.gqskj.cn/xnews/98161.htm
- http://m.3g.gqskj.cn/xnews/83198.htm
- http://m.3g.gqskj.cn/xnews/7211.htm
- http://m.3g.gqskj.cn/xnews/10380.htm
- http://m.3g.gqskj.cn/xnews/8422626.htm
- http://m.3g.gqskj.cn/xnews/67655.htm
- http://m.3g.gqskj.cn/xnews/3037.htm
- http://m.3g.gqskj.cn/xnews/9478281.htm
- http://m.3g.gqskj.cn/xnews/667400.htm
- http://m.3g.gqskj.cn/xnews/88171.htm
- http://m.3g.gqskj.cn/xnews/9813.htm
- http://m.3g.gqskj.cn/xnews/1431.htm
- http://m.3g.gqskj.cn/xnews/92813.htm
- http://m.3g.gqskj.cn/xnews/9908240.htm
- http://m.3g.gqskj.cn/xnews/4563.htm
- http://m.3g.gqskj.cn/xnews/35964.htm
- http://m.3g.gqskj.cn/xnews/111736.htm
- http://m.3g.gqskj.cn/xnews/770555.htm
- http://m.3g.gqskj.cn/xnews/5159809.htm
- http://m.3g.gqskj.cn/xnews/923761.htm
- http://m.3g.gqskj.cn/xnews/037401.htm
- http://m.3g.gqskj.cn/xnews/597811.htm
- http://m.3g.gqskj.cn/xnews/655800.htm
- http://m.3g.gqskj.cn/xnews/1718812.htm
- http://m.3g.gqskj.cn/xnews/245686.htm
- http://m.3g.gqskj.cn/xnews/2389.htm
- http://m.3g.gqskj.cn/xnews/4738.htm
- http://m.3g.gqskj.cn/xnews/7000077.htm
- http://m.3g.gqskj.cn/xnews/142140.htm
- http://m.3g.gqskj.cn/xnews/9381.htm
- http://m.3g.gqskj.cn/xnews/0166201.htm
- http://m.3g.gqskj.cn/xnews/461076.htm
- http://m.3g.gqskj.cn/xnews/2243.htm
- http://m.3g.gqskj.cn/xnews/9708.htm
- http://m.3g.gqskj.cn/xnews/97102.htm
- http://m.3g.gqskj.cn/xnews/3354813.htm
- http://m.3g.gqskj.cn/xnews/2566426.htm
- http://m.3g.gqskj.cn/xnews/0865.htm
- http://m.3g.gqskj.cn/xnews/5944605.htm
- http://m.3g.gqskj.cn/xnews/213672.htm
- http://m.3g.gqskj.cn/xnews/7462467.htm
- http://m.3g.gqskj.cn/xnews/12874.htm
- http://m.3g.gqskj.cn/xnews/1930.htm
- http://m.3g.gqskj.cn/xnews/3512.htm
- http://m.3g.gqskj.cn/xnews/9667.htm
- http://m.3g.gqskj.cn/xnews/73142.htm
- http://m.3g.gqskj.cn/xnews/656574.htm
- http://m.3g.gqskj.cn/xnews/8270942.htm
- http://m.3g.gqskj.cn/xnews/6380.htm
- http://m.3g.gqskj.cn/xnews/776538.htm
- http://m.3g.gqskj.cn/xnews/2285674.htm
- http://m.3g.gqskj.cn/xnews/490556.htm
- http://m.3g.gqskj.cn/xnews/789225.htm
- http://m.3g.gqskj.cn/xnews/8132677.htm
- http://m.3g.gqskj.cn/xnews/952258.htm
- http://m.3g.gqskj.cn/xnews/583497.htm
- http://m.3g.gqskj.cn/xnews/7423826.htm
- http://m.3g.gqskj.cn/xnews/143162.htm
- http://m.3g.gqskj.cn/xnews/8062.htm
- http://m.3g.gqskj.cn/xnews/2422.htm
- http://m.3g.gqskj.cn/xnews/5359505.htm
- http://m.3g.gqskj.cn/xnews/3024.htm
- http://m.3g.gqskj.cn/xnews/5055620.htm
- http://m.3g.gqskj.cn/xnews/278420.htm
- http://m.3g.gqskj.cn/xnews/883521.htm
- http://m.3g.gqskj.cn/xnews/4172143.htm
- http://m.3g.gqskj.cn/xnews/391936.htm
- http://m.3g.gqskj.cn/xnews/838194.htm
- http://m.3g.gqskj.cn/xnews/39450.htm
- http://m.3g.gqskj.cn/xnews/6306204.htm
- http://m.3g.gqskj.cn/xnews/646365.htm
- http://m.3g.gqskj.cn/xnews/32265.htm
- http://m.3g.gqskj.cn/xnews/0786315.htm
- http://m.3g.gqskj.cn/xnews/49624.htm
- http://m.3g.gqskj.cn/xnews/53085.htm
- http://m.3g.gqskj.cn/xnews/182249.htm
- http://m.3g.gqskj.cn/xnews/7360613.htm
- http://m.3g.gqskj.cn/xnews/0429314.htm
- http://m.3g.gqskj.cn/xnews/235550.htm
- http://m.3g.gqskj.cn/xnews/4687.htm
- http://m.3g.gqskj.cn/xnews/753245.htm
- http://m.3g.gqskj.cn/xnews/224142.htm
- http://m.3g.gqskj.cn/xnews/76182.htm
- http://m.3g.gqskj.cn/xnews/7047.htm
- http://m.3g.gqskj.cn/xnews/88596.htm
- http://m.3g.gqskj.cn/xnews/4555379.htm
- http://m.3g.gqskj.cn/xnews/2959028.htm
- http://m.3g.gqskj.cn/xnews/503984.htm
- http://m.3g.gqskj.cn/xnews/559103.htm
- http://m.3g.gqskj.cn/xnews/360401.htm
- http://m.3g.gqskj.cn/xnews/701132.htm
- http://m.3g.gqskj.cn/xnews/6028200.htm
- http://m.3g.gqskj.cn/xnews/79264.htm
- http://m.3g.gqskj.cn/xnews/2993559.htm
- http://m.3g.gqskj.cn/xnews/3048617.htm
- http://m.3g.gqskj.cn/xnews/182469.htm
- http://m.3g.gqskj.cn/xnews/1133.htm
- http://m.3g.gqskj.cn/xnews/37559.htm
- http://m.3g.gqskj.cn/xnews/176724.htm
- http://m.3g.gqskj.cn/xnews/4398005.htm
- http://m.3g.gqskj.cn/xnews/883293.htm
- http://m.3g.gqskj.cn/xnews/73099.htm
- http://m.3g.gqskj.cn/xnews/2491034.htm
- http://m.3g.gqskj.cn/xnews/1070.htm
- http://m.3g.gqskj.cn/xnews/4633291.htm
- http://m.3g.gqskj.cn/xnews/50624.htm
- http://m.3g.gqskj.cn/xnews/213842.htm
- http://m.3g.gqskj.cn/xnews/911618.htm
- http://m.3g.gqskj.cn/xnews/0327545.htm
- http://m.3g.gqskj.cn/xnews/35196.htm
- http://m.3g.gqskj.cn/xnews/755694.htm
- http://m.3g.gqskj.cn/xnews/3019132.htm
- http://m.3g.gqskj.cn/xnews/955659.htm
- http://m.3g.gqskj.cn/xnews/380340.htm
- http://m.3g.gqskj.cn/xnews/8833.htm
- http://m.3g.gqskj.cn/xnews/2889972.htm
- http://m.3g.gqskj.cn/xnews/504301.htm
- http://m.3g.gqskj.cn/xnews/6496306.htm
- http://m.3g.gqskj.cn/xnews/01830.htm
- http://m.3g.gqskj.cn/xnews/1089042.htm
- http://m.3g.gqskj.cn/xnews/4437517.htm
- http://m.3g.gqskj.cn/xnews/5715.htm
- http://m.3g.gqskj.cn/xnews/5776.htm
- http://m.3g.gqskj.cn/xnews/9290426.htm
- http://m.3g.gqskj.cn/xnews/6438.htm
- http://m.3g.gqskj.cn/xnews/469458.htm
- http://m.3g.gqskj.cn/xnews/829517.htm
- http://m.3g.gqskj.cn/xnews/0861.htm
- http://m.3g.gqskj.cn/xnews/396773.htm
- http://m.3g.gqskj.cn/xnews/9071712.htm
- http://m.3g.gqskj.cn/xnews/77784.htm
- http://m.3g.gqskj.cn/xnews/38978.htm
- http://m.3g.gqskj.cn/xnews/76088.htm
- http://m.3g.gqskj.cn/xnews/975823.htm
- http://m.3g.gqskj.cn/xnews/4263.htm
- http://m.3g.gqskj.cn/xnews/02151.htm
- http://m.3g.gqskj.cn/xnews/1088881.htm
- http://m.3g.gqskj.cn/xnews/627067.htm
- http://m.3g.gqskj.cn/xnews/320298.htm
- http://m.3g.gqskj.cn/xnews/770112.htm
- http://m.3g.gqskj.cn/xnews/06548.htm
- http://m.3g.gqskj.cn/xnews/90909.htm
- http://m.3g.gqskj.cn/xnews/5349.htm
- http://m.3g.gqskj.cn/xnews/5514.htm
- http://m.3g.gqskj.cn/xnews/3025.htm
- http://m.3g.gqskj.cn/xnews/728804.htm
- http://m.3g.gqskj.cn/xnews/4028979.htm
- http://m.3g.gqskj.cn/xnews/4547929.htm
- http://m.3g.gqskj.cn/xnews/59403.htm
- http://m.3g.gqskj.cn/xnews/1687727.htm
- http://m.3g.gqskj.cn/xnews/2706.htm
- http://m.3g.gqskj.cn/xnews/1082265.htm
- http://m.3g.gqskj.cn/xnews/59764.htm
- http://m.3g.gqskj.cn/xnews/18550.htm
- http://m.3g.gqskj.cn/xnews/4820353.htm
- http://m.3g.gqskj.cn/xnews/20958.htm
- http://m.3g.gqskj.cn/xnews/4300.htm
- http://m.3g.gqskj.cn/xnews/1249420.htm
- http://m.3g.gqskj.cn/xnews/8082419.htm
- http://m.3g.gqskj.cn/xnews/92328.htm
- http://m.3g.gqskj.cn/xnews/00148.htm
- http://m.3g.gqskj.cn/xnews/8198257.htm
- http://m.3g.gqskj.cn/xnews/9585.htm
- http://m.3g.gqskj.cn/xnews/2018334.htm
- http://m.3g.gqskj.cn/xnews/60007.htm
- http://m.3g.gqskj.cn/xnews/002993.htm
- http://m.3g.gqskj.cn/xnews/0838.htm
- http://m.3g.gqskj.cn/xnews/99967.htm
- http://m.3g.gqskj.cn/xnews/3196575.htm
- http://m.3g.gqskj.cn/xnews/779958.htm
- http://m.3g.gqskj.cn/xnews/9883792.htm
- http://m.3g.gqskj.cn/xnews/7263807.htm
- http://m.3g.gqskj.cn/xnews/5042984.htm
- http://m.3g.gqskj.cn/xnews/891152.htm
- http://m.3g.gqskj.cn/xnews/533944.htm
- http://m.3g.gqskj.cn/xnews/2572083.htm
- http://m.3g.gqskj.cn/xnews/730756.htm
- http://m.3g.gqskj.cn/xnews/7491.htm
- http://m.3g.gqskj.cn/xnews/538464.htm
- http://m.3g.gqskj.cn/xnews/874955.htm
- http://m.3g.gqskj.cn/xnews/049992.htm
- http://m.3g.gqskj.cn/xnews/46365.htm
- http://m.3g.gqskj.cn/xnews/923066.htm
- http://m.3g.gqskj.cn/xnews/63898.htm
- http://m.3g.gqskj.cn/xnews/30430.htm
- http://m.3g.gqskj.cn/xnews/342552.htm
- http://m.3g.gqskj.cn/xnews/40521.htm
- http://m.3g.gqskj.cn/xnews/8500480.htm
- http://m.3g.gqskj.cn/xnews/9327954.htm
- http://m.3g.gqskj.cn/xnews/2095309.htm
- http://m.3g.gqskj.cn/xnews/5857591.htm
- http://m.3g.gqskj.cn/xnews/98395.htm
- http://m.3g.gqskj.cn/xnews/8590.htm
- http://m.3g.gqskj.cn/xnews/026136.htm
- http://m.3g.gqskj.cn/xnews/932165.htm
- http://m.3g.gqskj.cn/xnews/3596768.htm
- http://m.3g.gqskj.cn/xnews/9789013.htm
- http://m.3g.gqskj.cn/xnews/8296630.htm
- http://m.3g.gqskj.cn/xnews/6714.htm
- http://m.3g.gqskj.cn/xnews/47458.htm
- http://m.3g.gqskj.cn/xnews/5998523.htm
- http://m.3g.gqskj.cn/xnews/710318.htm
- http://m.3g.gqskj.cn/xnews/96850.htm
- http://m.3g.gqskj.cn/xnews/17899.htm
- http://m.3g.gqskj.cn/xnews/1859057.htm
- http://m.3g.gqskj.cn/xnews/4511939.htm
- http://m.3g.gqskj.cn/xnews/963921.htm
- http://m.3g.gqskj.cn/xnews/34915.htm
- http://m.3g.gqskj.cn/xnews/974382.htm
- http://m.3g.gqskj.cn/xnews/556775.htm
- http://m.3g.gqskj.cn/xnews/147144.htm

## 项目结构

```
webindex-aggregator/
├── cmd/                                 # 命令行入口模块
│   ├── root.go                          # 根命令定义，整合所有子命令的启动入口
│   ├── collect.go                       # 采集子命令，负责链接获取与持久化
│   └── render.go                        # 渲染子命令，负责从数据库生成静态页面
├── internal/                            # 内部私有包，不对外暴露
│   ├── collector/                       # 采集引擎核心逻辑，包含 HTTP 客户端与 HTML 解析器
│   ├── dedup/                           # 基于布隆过滤器的链接去重模块
│   ├── metadata/                        # 元数据抽取器，包含针对移动端资讯的多种抽取策略
│   ├── storage/                         # SQLite 存储层，提供链接索引的增删改查接口
│   └── renderer/                        # 页面渲染引擎，管理模板加载和静态文件输出
├── pkg/                                 # 可被外部项目引用的公共库
│   ├── types/                           # 核心数据结构定义，如 LinkInfo、Category 等
│   └── utils/                           # 通用工具函数，包含时间处理、哈希计算等
├── templates/                           # 静态站点生成所用的 Go Template 模板文件
│   ├── index.html.tmpl                  # 首页列表视图模板，展示最新链接和分类导航
│   ├── category.html.tmpl               # 分类归档视图模板，按标签聚合链接
│   └── detail.html.tmpl                 # 详情页视图模板，展示完整元数据信息
├── configs/                             # 配置文件存放目录
│   ├── config.example.yaml              # 示例配置文件，包含采集源、字段映射等完整示例
│   └── schema.json                      # 配置文件的 JSON Schema 校验定义
├── scripts/                             # 辅助脚本集合
│   ├── setup.sh                         # 开发环境一键初始化脚本
│   └── cron-collect.sh                  # 定时采集任务的 Shell 包装脚本
├── testdata/                            # 测试数据目录，用于单元测试和集成测试
│   ├── sample.html                      # 模拟的移动端资讯 HTML 样本
│   └── expected.json                    # 样本对应的期望元数据输出
├── docs/                                # 完整项目文档
│   ├── getting-started.md               # 新手入门指南，从安装到首次运行完成
│   ├── collection-rules.md              # 采集规则编写参考，包含正则示例和调试方法
│   ├── metadata-config.md               # 元数据配置详解，含 CSS 选择器写法与测试工具
│   └── deployment.md                    # 生产环境部署说明，涵盖 Nginx 配置和 CI 集成
├── go.mod                               # Go 模块依赖定义文件
├── go.sum                               # Go 模块依赖校验文件
├── Makefile                             # 项目构建脚本，包含编译、测试、打包等任务
└── README.md                            # 项目概览文档（即本文档）
```

## 贡献指南

贡献者请先阅读项目行为准则并在提交前签署贡献者许可协议。所有贡献需遵循以下流程：

首先，在 GitHub 上 fork 本仓库并克隆到本地开发环境。确保本地 Go 版本不低于 1.21，并执行 make setup 命令完成开发依赖的安装和预提交钩子的配置。

其次，在开发新功能或修复缺陷前，请先在 issues 列表中查找是否存在相关讨论。若无，建议先创建一个 issue 说明意图，避免与其他贡献者的工作产生冲突。所有代码变更需对应新增或更新测试用例，并确保现有测试套件全部通过。

第三，提交代码时请遵循 Conventional Commits 规范，使用 feat:、fix:、docs:、refactor: 等类型前缀，并在提交信息中详细描述变更原因和影响范围。每个 pull request 应聚焦于单一主题，避免将不相关的改动混合在同一个请求中。

第四，对于涉及采集规则或元数据抽取模板的改动，需在 testdata 目录下补充对应的样本页面和期望输出，并在 pull request 描述中附上测试截图或日志，以便维护者验证改动效果。

最后，文档类贡献同样重要。若新增功能或修改接口行为，请同步更新 docs 目录下的相关文档和 README 中的功能概览。项目维护者会在每周五统一处理合并请求，请耐心等待审核反馈。

## 常见问题

问：采集过程中遇到目标站点返回 HTTP 403 或 429 状态码，应如何解决？

答：目标站点可能启用了反爬机制。建议在配置文件中调整采集频率，设置合理的请求间隔（如 500ms 以上），并配置 User-Agent 轮换列表。如果站点要求 Cookie 或特定请求头，可以在 config.yaml 的 collector 字段下添加 headers 映射。对于持续性的访问限制，可考虑使用代理池或增加采集任务的时间分散度。项目本身不提供绕过合法反爬手段的功能，请遵守目标站点的 robots.txt 和服务条款。

问：生成的静态站点中部分链接无法访问，显示为失效链接，如何自动检测和清理？

答：项目提供了 link-check 子命令，可对索引库中的链接进行批量可用性探测。该命令支持配置并发数、超时时间和重试策略。建议定期执行该命令并配合 render 子命令重新生成站点，将失效链接标记为已过期或直接移除。在配置文件中可启用 auto_prune 选项，使采集任务在每次运行后自动清理连续三次检测失败的链接。

问：能否扩展采集源至多个不同的移动资讯域名，而不仅限于当前配置的单一域名？

答：可以。配置文件中的 sources 字段接受数组类型，您可以在其中定义多个采集源，每个采集源独立配置域名、路径规则、采集深度和请求参数。采集引擎会按顺序遍历所有源，并将结果统一存入同一个索引库。需要注意的是，不同域名的页面结构可能存在差异，您需要为每个源单独配置 metadata_extractors 规则，以确保元数据抽取的准确性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:47
