# NavBridge 聚合导航

NavBridge 是一个面向技术调研、内容聚合与批量外链管理的轻量级静态导航站点，专为需要快速整理、分类和展示大量外部链接的团队或个人设计。该项目通过结构化的数据组织方式，将分散的 URL 资源整合为可检索、可分类、可分享的导航目录，适用于内部知识库、行业资讯汇总、开源工具索引等多种场景。

目标用户包括技术文档工程师、开源社区维护者、产品经理、数据分析师以及任何需要频繁管理和分发外部链接资源的从业者。NavBridge 不依赖数据库，所有链接数据以 Markdown 和 YAML 格式存储，便于版本控制和静态部署，同时支持通过 GitHub Actions 实现自动化更新与发布。

## 功能概览

**批量链接导入与去重**：支持从 CSV、JSON 或纯文本列表中批量导入 URL，自动检测并移除重复条目，保留原始来源标识。

**多级分类与标签系统**：每个链接可归属多个分类和标签，支持无限层级的目录结构，便于按主题、来源、日期或优先级进行组织。

**全文检索与模糊匹配**：基于 Lunr.js 或 MiniSearch 实现前端全文搜索，支持标题、描述、标签和 URL 片段的模糊匹配，响应时间小于 200 毫秒。

**链接状态健康检查**：集成定时任务，对已收录链接进行 HTTP 状态码检测，自动标记失效链接（4xx、5xx）并生成健康报告。

**自定义元数据扩展**：每条链接可附加自定义字段，如作者、发布日期、所属项目、阅读时长、重要等级等，满足个性化管理需求。

**响应式网格与列表视图**：提供卡片网格和紧凑列表两种展示模式，适配桌面端与移动端浏览，用户可自由切换布局风格。

**一键导出与分享**：支持将当前筛选结果导出为 Markdown 表格、JSON 或 CSV 格式，便于嵌入文档、邮件或第三方工具。

## 应用场景

**技术团队内部知识库导航**：研发团队可将常用的 API 文档、设计规范、监控面板、代码仓库地址统一收录，按项目或技术栈分类，新成员入职时即可一键访问全部核心资源。

**开源项目生态链接聚合**：开源项目维护者可在 README 或项目官网中嵌入 NavBridge 构建的生态导航页，集中展示相关工具、插件、教程、社区论坛和贡献者博客，降低生态入门门槛。

**行业资讯与竞品动态监控**：市场分析师或产品经理可每日批量导入竞品官网、行业报告、新闻稿等链接，通过标签标记关注领域，定期健康检查确保链接有效性，避免调研时遇到死链。

**教育课程参考资料汇总**：讲师或培训师可将课程涉及的扩展阅读、视频教程、在线工具、习题答案链接整理为导航站，学生可按章节或难度筛选，提升学习效率。

## 快速开始

以下指令可在本地快速启动 NavBridge 开发环境，默认监听 3000 端口。

```bash
# 克隆项目仓库
git clone https://github.com/navbridge/navbridge.git

# 进入项目目录
cd navbridge

# 安装依赖（使用 npm 或 yarn）
npm install

# 启动开发服务器
npm run dev
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 NVM 管理版本 |
| npm | 8.x 或 9.x | 包管理器，也可使用 yarn 1.22+ 替代 |
| Git | 2.30 及以上 | 用于克隆仓库和版本控制 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 开发调试与最终用户访问均需支持 ES2020 语法 |
| 可选：Docker | 20.10 及以上 | 用于容器化部署，生产环境推荐 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速搭建实例、导入第一批链接、自定义站点名称和 Logo |
| 数据规范 | /docs/data-schema.md | 链接数据采用什么格式、分类和标签如何定义、元数据字段有哪些 |
| 部署运维 | /docs/deployment.md | 如何部署到 Vercel、Netlify、云服务器或 Docker 容器，环境变量如何配置 |
| 开发扩展 | /docs/development.md | 如何新增主题、修改搜索逻辑、编写自定义插件或 Hook |

## 资源列表

- http://m.wap.fcful.cn/nnews/271056.htm
- http://m.wap.fcful.cn/nnews/2045614.htm
- http://m.wap.fcful.cn/nnews/5940256.htm
- http://m.wap.fcful.cn/nnews/9584260.htm
- http://m.wap.fcful.cn/nnews/02822.htm
- http://m.wap.fcful.cn/nnews/14437.htm
- http://m.wap.fcful.cn/nnews/3520380.htm
- http://m.wap.fcful.cn/nnews/4662.htm
- http://m.wap.fcful.cn/nnews/13934.htm
- http://m.wap.fcful.cn/nnews/36775.htm
- http://m.wap.fcful.cn/nnews/3496.htm
- http://m.wap.fcful.cn/nnews/20292.htm
- http://m.wap.fcful.cn/nnews/248478.htm
- http://m.wap.fcful.cn/nnews/61977.htm
- http://m.wap.fcful.cn/nnews/0452639.htm
- http://m.wap.fcful.cn/nnews/191591.htm
- http://m.wap.fcful.cn/nnews/2069.htm
- http://m.wap.fcful.cn/nnews/89739.htm
- http://m.wap.fcful.cn/nnews/4799.htm
- http://m.wap.fcful.cn/nnews/9233.htm
- http://m.wap.fcful.cn/nnews/1504179.htm
- http://m.wap.fcful.cn/nnews/1266188.htm
- http://m.wap.fcful.cn/nnews/70290.htm
- http://m.wap.fcful.cn/nnews/1364.htm
- http://m.wap.fcful.cn/nnews/97785.htm
- http://m.wap.fcful.cn/nnews/0891.htm
- http://m.wap.fcful.cn/nnews/2366.htm
- http://m.wap.fcful.cn/nnews/36900.htm
- http://m.wap.fcful.cn/nnews/04247.htm
- http://m.wap.fcful.cn/nnews/1907310.htm
- http://m.wap.fcful.cn/nnews/40042.htm
- http://m.wap.fcful.cn/nnews/78231.htm
- http://m.wap.fcful.cn/nnews/7912414.htm
- http://m.wap.fcful.cn/nnews/78276.htm
- http://m.wap.fcful.cn/nnews/995064.htm
- http://m.wap.fcful.cn/nnews/735729.htm
- http://m.wap.fcful.cn/nnews/87881.htm
- http://m.wap.fcful.cn/nnews/2074922.htm
- http://m.wap.fcful.cn/nnews/390866.htm
- http://m.wap.fcful.cn/nnews/3809516.htm
- http://m.wap.fcful.cn/nnews/6976538.htm
- http://m.wap.fcful.cn/nnews/8737.htm
- http://m.wap.fcful.cn/nnews/112630.htm
- http://m.wap.fcful.cn/nnews/786728.htm
- http://m.wap.fcful.cn/nnews/9567.htm
- http://m.wap.fcful.cn/nnews/6977570.htm
- http://m.wap.fcful.cn/nnews/8396.htm
- http://m.wap.fcful.cn/nnews/899379.htm
- http://m.wap.fcful.cn/nnews/6987.htm
- http://m.wap.fcful.cn/nnews/1502241.htm
- http://m.wap.fcful.cn/nnews/42167.htm
- http://m.wap.fcful.cn/nnews/87856.htm
- http://m.wap.fcful.cn/nnews/39431.htm
- http://m.wap.fcful.cn/nnews/034744.htm
- http://m.wap.fcful.cn/nnews/3512803.htm
- http://m.wap.fcful.cn/nnews/087255.htm
- http://m.wap.fcful.cn/nnews/3541698.htm
- http://m.wap.fcful.cn/nnews/73486.htm
- http://m.wap.fcful.cn/nnews/1799059.htm
- http://m.wap.fcful.cn/nnews/1759.htm
- http://m.wap.fcful.cn/nnews/3502.htm
- http://m.wap.fcful.cn/nnews/49005.htm
- http://m.wap.fcful.cn/nnews/0208.htm
- http://m.wap.fcful.cn/nnews/676170.htm
- http://m.wap.fcful.cn/nnews/4656.htm
- http://m.wap.fcful.cn/nnews/8750.htm
- http://m.wap.fcful.cn/nnews/4239.htm
- http://m.wap.fcful.cn/nnews/4526.htm
- http://m.wap.fcful.cn/nnews/9190144.htm
- http://m.wap.fcful.cn/nnews/0417016.htm
- http://m.wap.fcful.cn/nnews/8624981.htm
- http://m.wap.fcful.cn/nnews/0133.htm
- http://m.wap.fcful.cn/nnews/6387.htm
- http://m.wap.fcful.cn/nnews/508940.htm
- http://m.wap.fcful.cn/nnews/192701.htm
- http://m.wap.fcful.cn/nnews/03914.htm
- http://m.wap.fcful.cn/nnews/2968.htm
- http://m.wap.fcful.cn/nnews/4849282.htm
- http://m.wap.fcful.cn/nnews/217893.htm
- http://m.wap.fcful.cn/nnews/0003582.htm
- http://m.wap.fcful.cn/nnews/251088.htm
- http://m.wap.fcful.cn/nnews/7609.htm
- http://m.wap.fcful.cn/nnews/4079.htm
- http://m.wap.fcful.cn/nnews/1391.htm
- http://m.wap.fcful.cn/nnews/305050.htm
- http://m.wap.fcful.cn/nnews/8989.htm
- http://m.wap.fcful.cn/nnews/6682.htm
- http://m.wap.fcful.cn/nnews/4373.htm
- http://m.wap.fcful.cn/nnews/44920.htm
- http://m.wap.fcful.cn/nnews/44977.htm
- http://m.wap.fcful.cn/nnews/63883.htm
- http://m.wap.fcful.cn/nnews/63874.htm
- http://m.wap.fcful.cn/nnews/2513084.htm
- http://m.wap.fcful.cn/nnews/4485.htm
- http://m.wap.fcful.cn/nnews/9412859.htm
- http://m.wap.fcful.cn/nnews/661190.htm
- http://m.wap.fcful.cn/nnews/15965.htm
- http://m.wap.fcful.cn/nnews/441096.htm
- http://m.wap.fcful.cn/nnews/7289.htm
- http://m.wap.fcful.cn/nnews/727219.htm
- http://m.wap.fcful.cn/nnews/8128.htm
- http://m.wap.fcful.cn/nnews/3711821.htm
- http://m.wap.fcful.cn/nnews/82478.htm
- http://m.wap.fcful.cn/nnews/80318.htm
- http://m.wap.fcful.cn/nnews/9555.htm
- http://m.wap.fcful.cn/nnews/2242.htm
- http://m.wap.fcful.cn/nnews/8418128.htm
- http://m.wap.fcful.cn/nnews/035501.htm
- http://m.wap.fcful.cn/nnews/764928.htm
- http://m.wap.fcful.cn/nnews/535382.htm
- http://m.wap.fcful.cn/nnews/34363.htm
- http://m.wap.fcful.cn/nnews/8997.htm
- http://m.wap.fcful.cn/nnews/59800.htm
- http://m.wap.fcful.cn/nnews/939660.htm
- http://m.wap.fcful.cn/nnews/053813.htm
- http://m.wap.fcful.cn/nnews/25769.htm
- http://m.wap.fcful.cn/nnews/71654.htm
- http://m.wap.fcful.cn/nnews/59901.htm
- http://m.wap.fcful.cn/nnews/543317.htm
- http://m.wap.fcful.cn/nnews/7020994.htm
- http://m.wap.fcful.cn/nnews/95432.htm
- http://m.wap.fcful.cn/nnews/6749115.htm
- http://m.wap.fcful.cn/nnews/0937446.htm
- http://m.wap.fcful.cn/nnews/2779.htm
- http://m.wap.fcful.cn/nnews/08024.htm
- http://m.wap.fcful.cn/nnews/8621674.htm
- http://m.wap.fcful.cn/nnews/19623.htm
- http://m.wap.fcful.cn/nnews/51241.htm
- http://m.wap.fcful.cn/nnews/4715447.htm
- http://m.wap.fcful.cn/nnews/7369.htm
- http://m.wap.fcful.cn/nnews/2430.htm
- http://m.wap.fcful.cn/nnews/315395.htm
- http://m.wap.fcful.cn/nnews/2262.htm
- http://m.wap.fcful.cn/nnews/66830.htm
- http://m.wap.fcful.cn/nnews/92331.htm
- http://m.wap.fcful.cn/nnews/323552.htm
- http://m.wap.fcful.cn/nnews/8154430.htm
- http://m.wap.fcful.cn/nnews/4816.htm
- http://m.wap.fcful.cn/nnews/796949.htm
- http://m.wap.fcful.cn/nnews/7505.htm
- http://m.wap.fcful.cn/nnews/7030362.htm
- http://m.wap.fcful.cn/nnews/6205.htm
- http://m.wap.fcful.cn/nnews/04108.htm
- http://m.wap.fcful.cn/nnews/717439.htm
- http://m.wap.fcful.cn/nnews/45980.htm
- http://m.wap.fcful.cn/nnews/26291.htm
- http://m.wap.fcful.cn/nnews/989402.htm
- http://m.wap.fcful.cn/nnews/801555.htm
- http://m.wap.fcful.cn/nnews/9534.htm
- http://m.wap.fcful.cn/nnews/8207.htm
- http://m.wap.fcful.cn/nnews/38773.htm
- http://m.wap.fcful.cn/nnews/865813.htm
- http://m.wap.fcful.cn/nnews/2146.htm
- http://m.wap.fcful.cn/nnews/153888.htm
- http://m.wap.fcful.cn/nnews/3690.htm
- http://m.wap.fcful.cn/nnews/52366.htm
- http://m.wap.fcful.cn/nnews/76347.htm
- http://m.wap.fcful.cn/nnews/4229.htm
- http://m.wap.fcful.cn/nnews/227770.htm
- http://m.wap.fcful.cn/nnews/36208.htm
- http://m.wap.fcful.cn/nnews/072546.htm
- http://m.wap.fcful.cn/nnews/1868109.htm
- http://m.wap.fcful.cn/nnews/677045.htm
- http://m.wap.fcful.cn/nnews/2548064.htm
- http://m.wap.fcful.cn/nnews/8659.htm
- http://m.wap.fcful.cn/nnews/5086375.htm
- http://m.wap.fcful.cn/nnews/3265.htm
- http://m.wap.fcful.cn/nnews/216627.htm
- http://m.wap.fcful.cn/nnews/902957.htm
- http://m.wap.fcful.cn/nnews/373828.htm
- http://m.wap.fcful.cn/nnews/0612283.htm
- http://m.wap.fcful.cn/nnews/752623.htm
- http://m.wap.fcful.cn/nnews/52287.htm
- http://m.wap.fcful.cn/nnews/1213447.htm
- http://m.wap.fcful.cn/nnews/87893.htm
- http://m.wap.fcful.cn/nnews/5788542.htm
- http://m.wap.fcful.cn/nnews/3601.htm
- http://m.wap.fcful.cn/nnews/41312.htm
- http://m.wap.fcful.cn/nnews/15875.htm
- http://m.wap.fcful.cn/nnews/025350.htm
- http://m.wap.fcful.cn/nnews/08321.htm
- http://m.wap.fcful.cn/nnews/22434.htm
- http://m.wap.fcful.cn/nnews/8669936.htm
- http://m.wap.fcful.cn/nnews/50022.htm
- http://m.wap.fcful.cn/nnews/883795.htm
- http://m.wap.fcful.cn/nnews/2218.htm
- http://m.wap.fcful.cn/nnews/3090.htm
- http://m.wap.fcful.cn/nnews/9067.htm
- http://m.wap.fcful.cn/nnews/7921561.htm
- http://m.wap.fcful.cn/nnews/436689.htm
- http://m.wap.fcful.cn/nnews/5661399.htm
- http://m.wap.fcful.cn/nnews/57775.htm
- http://m.wap.fcful.cn/nnews/3090824.htm
- http://m.wap.fcful.cn/nnews/4616.htm
- http://m.wap.fcful.cn/nnews/22205.htm
- http://m.wap.fcful.cn/nnews/220028.htm
- http://m.wap.fcful.cn/nnews/975333.htm
- http://m.wap.fcful.cn/nnews/5047.htm
- http://m.wap.fcful.cn/nnews/7007.htm
- http://m.wap.fcful.cn/nnews/0780525.htm
- http://m.wap.fcful.cn/nnews/961228.htm
- http://m.wap.fcful.cn/nnews/12978.htm
- http://m.wap.fcful.cn/nnews/619431.htm
- http://m.wap.fcful.cn/nnews/56973.htm
- http://m.wap.fcful.cn/nnews/487539.htm
- http://m.wap.fcful.cn/nnews/4879281.htm
- http://m.wap.fcful.cn/nnews/1275.htm
- http://m.wap.fcful.cn/nnews/69891.htm
- http://m.wap.fcful.cn/nnews/743209.htm
- http://m.wap.fcful.cn/nnews/56198.htm
- http://m.wap.fcful.cn/nnews/02325.htm
- http://m.wap.fcful.cn/nnews/014091.htm
- http://m.wap.fcful.cn/nnews/5291404.htm
- http://m.wap.fcful.cn/nnews/6193.htm
- http://m.wap.fcful.cn/nnews/78182.htm
- http://m.wap.fcful.cn/nnews/763982.htm
- http://m.wap.fcful.cn/nnews/71676.htm
- http://m.wap.fcful.cn/nnews/03263.htm
- http://m.wap.fcful.cn/nnews/0349.htm
- http://m.wap.fcful.cn/nnews/708717.htm
- http://m.wap.fcful.cn/nnews/3358212.htm
- http://m.wap.fcful.cn/nnews/450916.htm
- http://m.wap.fcful.cn/nnews/50962.htm
- http://m.wap.fcful.cn/nnews/9328.htm
- http://m.wap.fcful.cn/nnews/99252.htm
- http://m.wap.fcful.cn/nnews/23958.htm
- http://m.wap.fcful.cn/nnews/80577.htm
- http://m.wap.fcful.cn/nnews/71209.htm
- http://m.wap.fcful.cn/nnews/40083.htm
- http://m.wap.fcful.cn/nnews/963050.htm
- http://m.wap.fcful.cn/nnews/057680.htm
- http://m.wap.fcful.cn/nnews/0151781.htm
- http://m.wap.fcful.cn/nnews/2229771.htm
- http://m.wap.fcful.cn/nnews/00497.htm
- http://m.wap.fcful.cn/nnews/3992361.htm
- http://m.wap.fcful.cn/nnews/0596.htm
- http://m.wap.fcful.cn/nnews/3463431.htm
- http://m.wap.fcful.cn/nnews/995313.htm
- http://m.wap.fcful.cn/nnews/7561.htm
- http://m.wap.fcful.cn/nnews/9718001.htm
- http://m.wap.fcful.cn/nnews/8653032.htm
- http://m.wap.fcful.cn/nnews/948565.htm
- http://m.wap.fcful.cn/nnews/78243.htm
- http://m.wap.fcful.cn/nnews/1535.htm
- http://m.wap.fcful.cn/nnews/565606.htm
- http://m.wap.fcful.cn/nnews/70585.htm
- http://m.wap.fcful.cn/nnews/221048.htm
- http://m.wap.fcful.cn/nnews/2306.htm
- http://m.wap.fcful.cn/nnews/1877737.htm
- http://m.wap.fcful.cn/nnews/781665.htm

## 项目结构

```
navbridge/
├── .github/                         # GitHub 工作流配置
│   └── workflows/
│       ├── deploy.yml               # 主分支自动部署到生产环境
│       └── health-check.yml         # 定时执行链接状态检查（每周一 09:00）
├── src/                             # 源代码主目录
│   ├── assets/                      # 静态资源（图片、字体、图标）
│   │   ├── icons/                   # SVG 图标库，按分类存放
│   │   └── logos/                   # 站点 Logo 和品牌标识
│   ├── components/                  # Vue/React 组件（根据框架选型）
│   │   ├── LinkCard.vue             # 卡片视图组件，展示链接标题、描述和标签
│   │   ├── LinkTable.vue            # 列表视图组件，支持排序和筛选
│   │   └── SearchBar.vue            # 搜索框组件，含自动补全建议
│   ├── data/                        # 数据层
│   │   ├── links.yaml               # 主链接数据文件，包含全部 250 条收录
│   │   ├── categories.yaml          # 分类定义（层级、显示名称、图标）
│   │   └── tags.yaml                # 标签定义（名称、颜色、描述）
│   ├── hooks/                       # 自定义 React Hooks 或 Vue Composables
│   │   ├── useSearch.ts             # 封装搜索逻辑，含防抖和索引更新
│   │   └── useFilter.ts             # 封装分类和标签过滤逻辑
│   ├── layouts/                     # 页面布局模板
│   │   ├── default.vue              # 默认布局（含导航栏和页脚）
│   │   └── fullscreen.vue           # 全屏布局，用于嵌入场景
│   ├── pages/                       # 路由页面
│   │   ├── index.vue                # 首页，默认展示全部链接
│   │   ├── category/[id].vue        # 分类筛选页，动态路由
│   │   ├── tag/[id].vue             # 标签筛选页，动态路由
│   │   └── about.vue                # 关于页，含项目说明和版本信息
│   ├── styles/                      # 全局样式
│   │   ├── variables.css            # CSS 变量（主题色、字体、间距）
│   │   └── reset.css                # 浏览器样式重置
│   ├── utils/                       # 工具函数库
│   │   ├── validator.ts             # URL 校验和格式化工具
│   │   ├── healthCheck.ts           # 链接状态检测核心逻辑（axios + 超时控制）
│   │   └── exporter.ts              # 数据导出模块（JSON/CSV/Markdown）
│   └── main.ts                      # 应用入口，挂载根组件
├── tests/                           # 单元测试和集成测试
│   ├── unit/
│   │   └── validator.spec.ts        # URL 校验工具测试用例
│   └── e2e/
│       └── search.spec.ts           # 搜索功能端到端测试（Playwright）
├── docs/                            # 项目文档（详见文档导航章节）
├── scripts/                         # 维护脚本
│   ├── import-csv.ts                # 从 CSV 批量导入链接
│   └── deduplicate.ts               # 链接去重脚本，基于 URL 和标题相似度
├── config/                          # 配置文件目录
│   ├── site.config.js               # 站点配置（名称、描述、导航菜单）
│   └── build.config.js              # 构建工具配置（Vite/Webpack）
├── .env.example                     # 环境变量模板（含 API 密钥占位）
├── .gitignore                       # Git 忽略规则
├── package.json                     # 项目依赖和脚本定义
├── README.md                        # 项目入口文档（即本文档）
├── LICENSE                          # MIT 许可证文件
└── index.html                       # HTML 入口模板
```

## 贡献指南

我们欢迎并鼓励社区贡献，无论是提交问题报告、改进文档、新增功能还是优化性能。请遵循以下步骤参与贡献：

1. 查阅现有 Issue 和 Pull Request，确认没有重复提交。在 GitHub Issues 中搜索关键词，若未找到相关讨论，请新建 Issue 并详细描述您发现的问题或建议的新特性。

2. Fork 本仓库到您的 GitHub 账户，并克隆到本地开发环境。建议使用 `git clone --depth=1` 加速克隆，然后通过 `npm install` 安装全部依赖。

3. 创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。在开发前请运行 `npm run test` 确认现有测试全部通过，确保您的修改不会引入回归问题。

4. 完成代码修改后，请补充对应的单元测试或文档说明，并确保代码风格符合 ESLint 和 Prettier 配置。提交信息请使用语义化格式，例如 `feat: add batch import from JSON` 或 `docs: update deployment guide`。

5. 推送到您的远程仓库，然后通过 GitHub 界面发起 Pull Request 到主仓库的 main 分支。PR 描述中请引用相关 Issue 编号，并简要说明修改内容和测试结果。核心维护者会在 3 个工作日内进行 Code Review。

## 常见问题

**Q：导入大量链接时页面变得卡顿，如何优化？**

A：当链接数量超过 500 条时，建议启用虚拟滚动（virtual-scroll）组件来优化渲染性能。您可以在 `src/components/LinkTable.vue` 中将 `virtual-scroll` 属性设置为 `true`，并调整 `item-height` 参数以匹配实际行高。此外，可以启用搜索索引的懒加载，仅在用户首次输入搜索词时构建 Lunr 索引，减少初始加载开销。

**Q：链接健康检查任务报错，提示超时或连接拒绝，如何处理？**

A：健康检查依赖外网访问和目标的响应策略。请首先检查 `.env` 文件中的 `HEALTH_CHECK_TIMEOUT` 和 `MAX_RETRIES` 配置，适当增加超时时间（如 10000 毫秒）和重试次数（如 3 次）。对于部分反爬严格的站点，可以在 `src/utils/healthCheck.ts` 中配置自定义 User-Agent 和请求头。若大量链接位于内网环境，建议在 GitHub Actions 中配置 self-hosted runner 以确保网络可达。

**Q：如何自定义站点主题色和布局，是否支持多主题切换？**

A：所有样式变量集中在 `src/styles/variables.css` 中，您可以通过修改 `--primary-color`、`--bg-color`、`--font-family` 等 CSS 变量快速调整主题。如需支持多套主题（如暗色模式），请参考 `src/hooks/useTheme.ts` 中的实现，该 Hook 已提供 `toggleTheme` 和 `setTheme` 方法，您只需在布局组件中添加切换按钮即可。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
