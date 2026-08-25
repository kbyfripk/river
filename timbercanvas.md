# WebLink Navigator

WebLink Navigator 是一个面向技术研究、信息聚合与内容归档场景的轻量级外链资源汇总平台。该项目旨在解决个人开发者、技术内容创作者以及小型研究团队在信息检索过程中面临的链接分散、管理成本高、上下文缺失等问题，通过结构化的资源收录体系与简洁的导航界面，将碎片化的网络信息转化为可复用、可追溯的知识资产。

本项目定位为技术辅助工具，不依赖外部数据库或复杂后端服务，所有资源索引通过静态配置与版本管理进行维护，适合部署在各类低成本服务器或 PaaS 环境中。目标用户包括需要持续跟踪特定行业动态的技术研究人员、希望建立私有知识库的内容策展人，以及希望以轻量化方式分享资源列表的社区运营者。

## 功能概览

- **资源清单结构化呈现**：系统按照既定分类与标签体系，将收录的 URL 资源以层级化列表进行展示，支持按批次、按领域或按收录时间进行筛选与排序。

- **快速检索与过滤**：内置轻量级前端检索逻辑，用户可通过关键词对资源标题、描述或关联标签进行实时过滤，快速定位所需链接。

- **资源状态标识**：对每个收录链接自动附加收录批次、编号及状态标记，便于用户识别资源的新旧程度与可用性预期。

- **可扩展的配置体系**：所有资源列表及元数据均通过独立的配置文件进行管理，用户无需修改核心代码即可完成新增、删除或更新资源条目。

- **静态页面生成机制**：项目在构建阶段将配置数据渲染为纯静态 HTML 页面，无需运行时数据库查询，显著降低服务器负载与响应延迟。

- **响应式布局适配**：前端界面针对桌面端与移动端浏览器进行适配优化，确保在手机、平板及各类屏幕尺寸下均获得一致的浏览体验。

- **访问日志与统计埋点**：提供基础访问日志记录能力，支持用户自定义统计脚本注入，便于分析资源被访问的热度与频次。

## 应用场景

- **技术研究素材库**：技术团队在研究某一前沿领域时，可将收集到的论文链接、代码仓库、技术博客等资源通过 WebLink Navigator 进行统一归档，团队成员可随时查阅与补充，避免重复检索与信息遗漏。

- **内容创作参考索引**：技术作者或自媒体人在撰写深度文章或制作教程视频时，需要引用大量外部资料作为支撑。通过本平台对参考资料进行系统性管理，可有效提升创作流程的条理性与可追溯性。

- **开源项目生态导航**：开源社区维护者可将项目周边生态中的相关工具、插件、示例项目等资源整理为导航页面，降低新贡献者的学习成本，同时扩大社区资源的可见度。

- **企业内部知识沉淀**：企业内部可将分散在 Wiki、邮件、即时通讯中的业务相关链接通过本平台进行集中收纳，形成部门级或公司级的知识索引，减少信息孤岛现象。

## 快速开始

以下步骤指导您在本地环境中快速启动 WebLink Navigator 服务。

```bash
# 克隆代码仓库至本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 安装项目依赖（基于 Node.js 环境）
npm install

# 执行构建流程，生成静态站点文件
npm run build

# 启动本地开发服务器，默认监听端口 8080
npm start
```

完成上述操作后，在浏览器中访问 `http://localhost:8080` 即可查看资源导航页面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >= 16.0.0 | 运行时环境，用于执行构建脚本与启动服务 |
| npm | >= 8.0.0 | 包管理工具，用于安装项目依赖 |
| Git | >= 2.25.0 | 版本控制工具，用于克隆仓库与管理代码更新 |
| 操作系统 | Linux / macOS / Windows (WSL2 推荐) | 项目可在主流操作系统上运行，Windows 用户建议使用 WSL2 以获取更好的兼容性 |
| 浏览器 | 支持 ES6 的现代浏览器（Chrome 90+ / Firefox 88+ / Edge 90+） | 前端渲染依赖现代 JavaScript 特性，不兼容 IE11 及更早版本 |
| 服务器内存 | >= 512 MB | 静态站点运行内存要求极低，512 MB 可满足大多数使用场景 |
| 磁盘空间 | >= 100 MB | 包含源代码、依赖包及构建产物在内的总占用空间 |
| 网络环境 | 可访问外网（用于安装依赖及获取资源内容） | 构建过程中需要从 npm 仓库下载依赖包 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `docs/getting-started.md` | 如何快速部署本项目到生产环境？如何修改站点标题与徽标？ |
| 配置手册 | `docs/configuration.md` | 资源列表配置文件位于何处？字段含义是什么？如何新增一个资源分类？ |
| 开发指南 | `docs/development.md` | 项目采用何种技术栈？如何修改前端样式？如何扩展新的构建插件？ |
| 运维参考 | `docs/operations.md` | 如何通过 Nginx 反向代理部署？如何配置 HTTPS 证书？日志文件存储在哪里？ |

## 资源列表

- http://m.wap.gqskj.cn/snews/2528118.htm
- http://m.wap.gqskj.cn/snews/511681.htm
- http://m.wap.gqskj.cn/snews/217209.htm
- http://m.wap.gqskj.cn/snews/8948942.htm
- http://m.wap.gqskj.cn/snews/6824.htm
- http://m.wap.gqskj.cn/snews/1797507.htm
- http://m.wap.gqskj.cn/snews/05779.htm
- http://m.wap.gqskj.cn/snews/264636.htm
- http://m.wap.gqskj.cn/snews/2712.htm
- http://m.wap.gqskj.cn/snews/929780.htm
- http://m.wap.gqskj.cn/snews/4848.htm
- http://m.wap.gqskj.cn/snews/890511.htm
- http://m.wap.gqskj.cn/snews/819022.htm
- http://m.wap.gqskj.cn/snews/5760789.htm
- http://m.wap.gqskj.cn/snews/3591001.htm
- http://m.wap.gqskj.cn/snews/8036.htm
- http://m.wap.gqskj.cn/snews/7544685.htm
- http://m.wap.gqskj.cn/snews/35399.htm
- http://m.wap.gqskj.cn/snews/031834.htm
- http://m.wap.gqskj.cn/snews/896927.htm
- http://m.wap.gqskj.cn/snews/8080.htm
- http://m.wap.gqskj.cn/snews/39396.htm
- http://m.wap.gqskj.cn/snews/1541.htm
- http://m.wap.gqskj.cn/snews/10849.htm
- http://m.wap.gqskj.cn/snews/3964008.htm
- http://m.wap.gqskj.cn/snews/6386.htm
- http://m.wap.gqskj.cn/snews/6775707.htm
- http://m.wap.gqskj.cn/snews/219601.htm
- http://m.wap.gqskj.cn/snews/71915.htm
- http://m.wap.gqskj.cn/snews/0388.htm
- http://m.wap.gqskj.cn/snews/5494.htm
- http://m.wap.gqskj.cn/snews/459840.htm
- http://m.wap.gqskj.cn/snews/6755.htm
- http://m.wap.gqskj.cn/snews/5083141.htm
- http://m.wap.gqskj.cn/snews/6284.htm
- http://m.wap.gqskj.cn/snews/02177.htm
- http://m.wap.gqskj.cn/snews/514651.htm
- http://m.wap.gqskj.cn/snews/949157.htm
- http://m.wap.gqskj.cn/snews/5868.htm
- http://m.wap.gqskj.cn/snews/7840.htm
- http://m.wap.gqskj.cn/snews/9709981.htm
- http://m.wap.gqskj.cn/snews/0910768.htm
- http://m.wap.gqskj.cn/snews/3011310.htm
- http://m.wap.gqskj.cn/snews/6909516.htm
- http://m.wap.gqskj.cn/snews/9356.htm
- http://m.wap.gqskj.cn/snews/4980.htm
- http://m.wap.gqskj.cn/snews/870870.htm
- http://m.wap.gqskj.cn/snews/3700.htm
- http://m.wap.gqskj.cn/snews/5340739.htm
- http://m.wap.gqskj.cn/snews/5555677.htm
- http://m.wap.gqskj.cn/snews/160793.htm
- http://m.wap.gqskj.cn/snews/05290.htm
- http://m.wap.gqskj.cn/snews/731659.htm
- http://m.wap.gqskj.cn/snews/1945.htm
- http://m.wap.gqskj.cn/snews/402917.htm
- http://m.wap.gqskj.cn/snews/759475.htm
- http://m.wap.gqskj.cn/snews/1629573.htm
- http://m.wap.gqskj.cn/snews/009663.htm
- http://m.wap.gqskj.cn/snews/839032.htm
- http://m.wap.gqskj.cn/snews/5532.htm
- http://m.wap.gqskj.cn/snews/10569.htm
- http://m.wap.gqskj.cn/snews/328131.htm
- http://m.wap.gqskj.cn/snews/70072.htm
- http://m.wap.gqskj.cn/snews/1744373.htm
- http://m.wap.gqskj.cn/snews/053908.htm
- http://m.wap.gqskj.cn/snews/1849641.htm
- http://m.wap.gqskj.cn/snews/29375.htm
- http://m.wap.gqskj.cn/snews/86449.htm
- http://m.wap.gqskj.cn/snews/697894.htm
- http://m.wap.gqskj.cn/snews/462659.htm
- http://m.wap.gqskj.cn/snews/8765688.htm
- http://m.wap.gqskj.cn/snews/5722669.htm
- http://m.wap.gqskj.cn/snews/9913693.htm
- http://m.wap.gqskj.cn/snews/02803.htm
- http://m.wap.gqskj.cn/snews/921242.htm
- http://m.wap.gqskj.cn/snews/931990.htm
- http://m.wap.gqskj.cn/snews/098167.htm
- http://m.wap.gqskj.cn/snews/27320.htm
- http://m.wap.gqskj.cn/snews/5619522.htm
- http://m.wap.gqskj.cn/snews/670739.htm
- http://m.wap.gqskj.cn/snews/07210.htm
- http://m.wap.gqskj.cn/snews/4328.htm
- http://m.wap.gqskj.cn/snews/668011.htm
- http://m.wap.gqskj.cn/snews/93050.htm
- http://m.wap.gqskj.cn/snews/416550.htm
- http://m.wap.gqskj.cn/snews/1478901.htm
- http://m.wap.gqskj.cn/snews/0783.htm
- http://m.wap.gqskj.cn/snews/9013.htm
- http://m.wap.gqskj.cn/snews/4330.htm
- http://m.wap.gqskj.cn/snews/1805.htm
- http://m.wap.gqskj.cn/snews/50691.htm
- http://m.wap.gqskj.cn/snews/61437.htm
- http://m.wap.gqskj.cn/snews/9262.htm
- http://m.wap.gqskj.cn/snews/218187.htm
- http://m.wap.gqskj.cn/snews/137936.htm
- http://m.wap.gqskj.cn/snews/7266728.htm
- http://m.wap.gqskj.cn/snews/0371.htm
- http://m.wap.gqskj.cn/snews/73059.htm
- http://m.wap.gqskj.cn/snews/2815.htm
- http://m.wap.gqskj.cn/snews/43410.htm
- http://m.wap.gqskj.cn/snews/4627387.htm
- http://m.wap.gqskj.cn/snews/727930.htm
- http://m.wap.gqskj.cn/snews/41003.htm
- http://m.wap.gqskj.cn/snews/26220.htm
- http://m.wap.gqskj.cn/snews/869818.htm
- http://m.wap.gqskj.cn/snews/7009969.htm
- http://m.wap.gqskj.cn/snews/29746.htm
- http://m.wap.gqskj.cn/snews/071024.htm
- http://m.wap.gqskj.cn/snews/18230.htm
- http://m.wap.gqskj.cn/snews/590297.htm
- http://m.wap.gqskj.cn/snews/3910744.htm
- http://m.wap.gqskj.cn/snews/0939.htm
- http://m.wap.gqskj.cn/snews/27817.htm
- http://m.wap.gqskj.cn/snews/748776.htm
- http://m.wap.gqskj.cn/snews/8172688.htm
- http://m.wap.gqskj.cn/snews/0780.htm
- http://m.wap.gqskj.cn/snews/571425.htm
- http://m.wap.gqskj.cn/snews/367500.htm
- http://m.wap.gqskj.cn/snews/86743.htm
- http://m.wap.gqskj.cn/snews/2740.htm
- http://m.wap.gqskj.cn/snews/226272.htm
- http://m.wap.gqskj.cn/snews/96752.htm
- http://m.wap.gqskj.cn/snews/8313471.htm
- http://m.wap.gqskj.cn/snews/69768.htm
- http://m.wap.gqskj.cn/snews/75758.htm
- http://m.wap.gqskj.cn/snews/74351.htm
- http://m.wap.gqskj.cn/snews/32864.htm
- http://m.wap.gqskj.cn/snews/655551.htm
- http://m.wap.gqskj.cn/snews/1094754.htm
- http://m.wap.gqskj.cn/snews/3237.htm
- http://m.wap.gqskj.cn/snews/40766.htm
- http://m.wap.gqskj.cn/snews/10062.htm
- http://m.wap.gqskj.cn/snews/009282.htm
- http://m.wap.gqskj.cn/snews/1980456.htm
- http://m.wap.gqskj.cn/snews/492867.htm
- http://m.wap.gqskj.cn/snews/18539.htm
- http://m.wap.gqskj.cn/snews/99815.htm
- http://m.wap.gqskj.cn/snews/8254.htm
- http://m.wap.gqskj.cn/snews/741875.htm
- http://m.wap.gqskj.cn/snews/3585.htm
- http://m.wap.gqskj.cn/snews/8408.htm
- http://m.wap.gqskj.cn/snews/640088.htm
- http://m.wap.gqskj.cn/snews/2591.htm
- http://m.wap.gqskj.cn/snews/649827.htm
- http://m.wap.gqskj.cn/snews/107586.htm
- http://m.wap.gqskj.cn/snews/963793.htm
- http://m.wap.gqskj.cn/snews/4765363.htm
- http://m.wap.gqskj.cn/snews/21113.htm
- http://m.wap.gqskj.cn/snews/6900177.htm
- http://m.wap.gqskj.cn/snews/89157.htm
- http://m.wap.gqskj.cn/snews/518754.htm
- http://m.wap.gqskj.cn/snews/8908.htm
- http://m.wap.gqskj.cn/snews/42626.htm
- http://m.wap.gqskj.cn/snews/1345.htm
- http://m.wap.gqskj.cn/snews/465884.htm
- http://m.wap.gqskj.cn/snews/013197.htm
- http://m.wap.gqskj.cn/snews/3188.htm
- http://m.wap.gqskj.cn/snews/8375.htm
- http://m.wap.gqskj.cn/snews/208873.htm
- http://m.wap.gqskj.cn/snews/8063.htm
- http://m.wap.gqskj.cn/snews/32737.htm
- http://m.wap.gqskj.cn/snews/2929.htm
- http://m.wap.gqskj.cn/snews/7097957.htm
- http://m.wap.gqskj.cn/snews/8446021.htm
- http://m.wap.gqskj.cn/snews/967026.htm
- http://m.wap.gqskj.cn/snews/7289000.htm
- http://m.wap.gqskj.cn/snews/5371893.htm
- http://m.wap.gqskj.cn/snews/1425.htm
- http://m.wap.gqskj.cn/snews/6274764.htm
- http://m.wap.gqskj.cn/snews/8858668.htm
- http://m.wap.gqskj.cn/snews/76013.htm
- http://m.wap.gqskj.cn/snews/114472.htm
- http://m.wap.gqskj.cn/snews/727491.htm
- http://m.wap.gqskj.cn/snews/6652448.htm
- http://m.wap.gqskj.cn/snews/3606.htm
- http://m.wap.gqskj.cn/snews/654513.htm
- http://m.wap.gqskj.cn/snews/29438.htm
- http://m.wap.gqskj.cn/snews/92054.htm
- http://m.wap.gqskj.cn/snews/4362.htm
- http://m.wap.gqskj.cn/snews/0817.htm
- http://m.wap.gqskj.cn/snews/0018451.htm
- http://m.wap.gqskj.cn/snews/50837.htm
- http://m.wap.gqskj.cn/snews/5800.htm
- http://m.wap.gqskj.cn/snews/3873.htm
- http://m.wap.gqskj.cn/snews/2900100.htm
- http://m.wap.gqskj.cn/snews/4872.htm
- http://m.wap.gqskj.cn/snews/593815.htm
- http://m.wap.gqskj.cn/snews/1631.htm
- http://m.wap.gqskj.cn/snews/699648.htm
- http://m.wap.gqskj.cn/snews/41447.htm
- http://m.wap.gqskj.cn/snews/5068419.htm
- http://m.wap.gqskj.cn/snews/1223.htm
- http://m.wap.gqskj.cn/snews/2899.htm
- http://m.wap.gqskj.cn/snews/3147.htm
- http://m.wap.gqskj.cn/snews/6484.htm
- http://m.wap.gqskj.cn/snews/53698.htm
- http://m.wap.gqskj.cn/snews/8782.htm
- http://m.wap.gqskj.cn/snews/4677944.htm
- http://m.wap.gqskj.cn/snews/7030.htm
- http://m.wap.gqskj.cn/snews/869594.htm
- http://m.wap.gqskj.cn/snews/8314960.htm
- http://m.wap.gqskj.cn/snews/231792.htm
- http://m.wap.gqskj.cn/snews/86314.htm
- http://m.wap.gqskj.cn/snews/3546358.htm
- http://m.wap.gqskj.cn/snews/74376.htm
- http://m.wap.gqskj.cn/snews/8696072.htm
- http://m.wap.gqskj.cn/snews/080107.htm
- http://m.wap.gqskj.cn/snews/3114064.htm
- http://m.wap.gqskj.cn/snews/2152.htm
- http://m.wap.gqskj.cn/snews/275822.htm
- http://m.wap.gqskj.cn/snews/08051.htm
- http://m.wap.gqskj.cn/snews/335734.htm
- http://m.wap.gqskj.cn/snews/985514.htm
- http://m.wap.gqskj.cn/snews/0215478.htm
- http://m.wap.gqskj.cn/snews/7002408.htm
- http://m.wap.gqskj.cn/snews/8617.htm
- http://m.wap.gqskj.cn/snews/65311.htm
- http://m.wap.gqskj.cn/snews/31278.htm
- http://m.wap.gqskj.cn/snews/278747.htm
- http://m.wap.gqskj.cn/snews/10600.htm
- http://m.wap.gqskj.cn/snews/935787.htm
- http://m.wap.gqskj.cn/snews/037717.htm
- http://m.wap.gqskj.cn/snews/6631.htm
- http://m.wap.gqskj.cn/snews/3330.htm
- http://m.wap.gqskj.cn/snews/1318408.htm
- http://m.wap.gqskj.cn/snews/7517.htm
- http://m.wap.gqskj.cn/snews/8258765.htm
- http://m.wap.gqskj.cn/snews/50706.htm
- http://m.wap.gqskj.cn/snews/999356.htm
- http://m.wap.gqskj.cn/snews/3495751.htm
- http://m.wap.gqskj.cn/snews/201211.htm
- http://m.wap.gqskj.cn/snews/9409.htm
- http://m.wap.gqskj.cn/snews/5063.htm
- http://m.wap.gqskj.cn/snews/0617650.htm
- http://m.wap.gqskj.cn/snews/9589681.htm
- http://m.wap.gqskj.cn/snews/596776.htm
- http://m.wap.gqskj.cn/snews/3002094.htm
- http://m.wap.gqskj.cn/snews/88014.htm
- http://m.wap.gqskj.cn/snews/042006.htm
- http://m.wap.gqskj.cn/snews/7856.htm
- http://m.wap.gqskj.cn/snews/4595.htm
- http://m.wap.gqskj.cn/snews/1233313.htm
- http://m.wap.gqskj.cn/snews/4340235.htm
- http://m.wap.gqskj.cn/snews/61444.htm
- http://m.wap.gqskj.cn/snews/666205.htm
- http://m.wap.gqskj.cn/snews/46451.htm
- http://m.wap.gqskj.cn/snews/503303.htm
- http://m.wap.gqskj.cn/snews/146244.htm
- http://m.wap.gqskj.cn/snews/19627.htm
- http://m.wap.gqskj.cn/snews/4757.htm

## 项目结构

```
weblink-navigator/
├── config/                           # 项目配置与资源索引目录
│   ├── resources.json                # 核心资源列表配置文件，包含所有收录链接及元数据
│   ├── categories.json               # 资源分类体系定义，维护分类名称与层级关系
│   └── settings.json                 # 站点全局设置，包含标题、描述、导航菜单等
├── src/                              # 源代码目录
│   ├── assets/                       # 静态资源文件
│   │   ├── styles/                   # CSS 样式文件目录
│   │   │   ├── main.css              # 全局主样式表
│   │   │   └── responsive.css        # 响应式布局样式适配
│   │   └── scripts/                  # JavaScript 脚本文件目录
│   │       ├── app.js                # 应用主逻辑，包含渲染与交互控制
│   │       └── search.js             # 检索过滤功能实现
│   ├── templates/                    # 页面模板文件
│   │   ├── index.template.html       # 首页模板，定义页面骨架与布局结构
│   │   └── partials/                 # 可复用的模板片段，如头部、脚部、列表项等
│   └── utils/                        # 工具函数模块
│       ├── builder.js                # 构建工具入口，负责将配置与模板合成为静态页面
│       └── validator.js              # 资源条目格式校验，确保配置数据完整性
├── dist/                             # 构建输出目录（生成后部署此目录内容）
│   ├── index.html                    # 最终生成的静态首页
│   ├── assets/                       # 经过打包压缩的静态资源副本
│   └── resources/                    # 资源详情页或分类聚合页（按需生成）
├── scripts/                          # 辅助脚本目录
│   ├── deploy.sh                     # 部署脚本，可用于自动化发布流程
│   └── update-resources.js           # 资源更新辅助脚本，支持批量导入或校验
├── docs/                             # 项目文档目录
│   ├── getting-started.md            # 入门指南
│   ├── configuration.md              # 配置手册
│   ├── development.md                # 开发指南
│   └── operations.md                 # 运维参考
├── tests/                            # 单元测试与集成测试目录
│   ├── builder.test.js               # 构建流程测试用例
│   └── validator.test.js             # 校验逻辑测试用例
├── .gitignore                        # Git 版本控制忽略文件配置
├── package.json                      # npm 依赖与脚本定义文件
├── package-lock.json                 # 依赖版本锁定文件
└── README.md                         # 项目说明文档（当前文件）
```

## 贡献指南

1. 复刻项目仓库至个人账号，在本地克隆复刻后的代码库，创建新的功能分支进行开发。分支命名建议遵循 `feature/功能简述` 或 `fix/问题描述` 的格式。

2. 在 `config/resources.json` 中按既定格式新增或修改资源条目，确保所有字段完整且符合校验规则。新增条目建议附带简要描述与分类标签，便于后续检索与展示。

3. 执行本地构建命令 `npm run build` 验证修改是否正确，同时运行单元测试 `npm test` 确保未破坏现有功能。若前端界面有调整，需在主流浏览器中进行兼容性确认。

4. 提交变更时遵循语义化提交信息规范，例如 `feat: 新增一批技术博客资源` 或 `fix: 修复资源列表在移动端显示错位的问题`。提交后推送到复刻仓库。

5. 通过 GitHub 平台发起 Pull Request 至主仓库的 `main` 分支，在 PR 描述中明确说明变更内容、测试结果以及是否涉及破坏性改动。等待项目维护者进行代码审查与合并。

## 常见问题

**问：项目是否支持动态添加资源而不重新构建？**

答：项目设计为静态站点生成模式，所有资源在构建阶段被渲染为 HTML 文件，因此新增、删除或修改资源后需要执行 `npm run build` 重新构建并重新部署 `dist` 目录内容才能生效。若需要动态管理资源，可参考本项目架构自行扩展后端 API 接口，但官方版本不提供运行时动态写入能力。

**问：部署到生产环境时，如何自定义站点的标题、Logo 与导航菜单？**

答：站点标题、描述、Logo 路径以及导航菜单项均在 `config/settings.json` 文件中集中管理。修改该文件后重新构建即可生效。Logo 图片需放置在 `src/assets/images/` 目录下，并在 `settings.json` 中填写相对路径。无需修改任何模板代码。

**问：资源列表中的链接如果失效或变更，平台如何处理？**

答：本项目仅提供资源索引功能，不代理或缓存外部链接内容。当外部链接失效或变更时，平台本身不会自动检测或拦截。建议维护者定期通过第三方链接检测工具对收录资源进行可用性检查，并在确认失效后及时从配置文件中移除或更新对应条目。平台可在资源条目中增加 `status` 字段用于手动标记链接状态，但该功能需用户自行扩展。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:57
