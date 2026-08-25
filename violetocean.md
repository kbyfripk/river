# NewsNav 移动端新闻导航聚合系统

NewsNav 是一个面向移动端新闻聚合与内容导航的开源工具，专为需要快速整合分散新闻来源、构建轻量级内容索引的开发者与内容运营者设计。该项目以移动优先为原则，通过统一的数据采集与分类机制，将海量分散的新闻链接转化为结构化、可检索的知识库，适用于个人知识管理、垂直领域资讯监控以及新闻存档分析等场景。NewsNav 不依赖重型框架，以纯静态页面为核心，兼顾性能与可维护性，旨在成为新闻数据整理工作流的中间层基础设施。

## 功能概览

- 移动端自适应内容索引：自动适配各类屏幕尺寸，在移动设备上提供流畅的新闻条目浏览与检索体验，支持触屏手势操作。

- 结构化链接分类与标签系统：对采集的新闻链接按来源、主题、时间等多维度自动打标，支持自定义分类规则，便于后期快速筛选与聚合。

- 增量式数据更新机制：通过脚本实现新闻链接的增量拉取与去重，每次运行仅处理新增或变更条目，显著降低服务器与带宽开销。

- 本地全文检索接口：内置轻量级倒排索引，支持对标题、摘要、关键词的模糊匹配搜索，响应时间控制在毫秒级，无需外部搜索引擎依赖。

- 自定义主题与样式扩展：采用 CSS 变量与模块化样式表，允许开发者通过修改少量配置文件即可调整整体视觉风格，适配不同品牌或使用场景。

- 批量导入与导出能力：支持 CSV、JSON 格式的链接批量导入，同时可将索引数据导出为标准交换格式，便于迁移至其他分析工具或发布系统。

- 访问统计与热度标记：自动记录每个新闻链接的点击频次与访问时间，在列表中以视觉标记形式展示热度趋势，辅助用户识别当前关注焦点。

## 应用场景

个人知识工作者可利用 NewsNav 构建专属的新闻阅读聚合器，将日常关注的行业媒体、博客与公告源集中管理，每日通过移动端快速浏览更新，避免信息碎片化带来的效率损耗。系统提供的分类与搜索功能可帮助用户在数秒内定位到特定主题的历史新闻，大幅提升信息回溯效率。

垂直领域的内容运营团队可将 NewsNav 作为内部资讯监控看板，针对特定关键词或来源配置采集规则，实时获取竞争对手动态、政策变动或市场舆情。通过热度标记功能，运营人员能迅速识别潜在热点，为内容策划提供数据支撑。

学术研究者与数据分析师可利用 NewsNav 的批量导出接口，将长期积累的新闻索引数据导出至外部分析环境，进行时间序列分析、情感倾向判断或主题建模研究。系统轻量化的设计使其可在本地或边缘设备上运行，满足数据隐私与合规性要求。

开发者在搭建演示项目或快速原型时，可将 NewsNav 作为内容填充工具，利用其内置的示例数据与分类模板快速生成具备真实感的新闻列表页面，节省手动构造测试数据的时间成本。

## 快速开始

以下命令序列适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/newsnav/newsnav-core.git
cd newsnav-core

# 安装项目依赖（需要 Node.js 18.x 及以上版本）
npm install

# 执行初始数据采集与索引构建
npm run build:index

# 启动本地开发服务器，默认监听 3000 端口
npm start

# 访问 http://localhost:3000 查看生成的新闻导航界面
```

完成上述步骤后，系统将自动拉取预设的新闻源数据并构建初始索引。如需自定义数据源，请编辑 `config/sources.json` 文件后重新执行 `npm run build:index`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或更高 | 运行时环境，用于执行构建脚本与开发服务器 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与管理补丁 |
| 操作系统 | Linux / macOS / WSL2 | 推荐在 Unix-like 环境下运行以获得最佳性能 |
| 磁盘空间 | 至少 200 MB | 用于存放源码、索引文件与本地缓存数据 |
| 内存 | 至少 512 MB | 构建索引与运行开发服务器时的最低内存要求 |
| 网络连接 | 稳定外网访问 | 首次构建需要拉取预设新闻源内容 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何配置新闻源、管理分类、使用搜索与导出功能 |
| 开发者指南 | docs/developer-guide.md | 如何扩展采集器、自定义索引字段、调整构建流程 |
| API 参考 | docs/api-reference.md | 各内部模块的接口定义、参数说明与回调示例 |
| 运维部署 | docs/deployment.md | 如何将系统部署至生产环境、配置反向代理与定时任务 |

## 资源列表

- http://m.wap.fcful.cn/nnews/106440.htm
- http://m.wap.fcful.cn/nnews/26491.htm
- http://m.wap.fcful.cn/nnews/16621.htm
- http://m.wap.fcful.cn/nnews/9549.htm
- http://m.wap.fcful.cn/nnews/1849074.htm
- http://m.wap.fcful.cn/nnews/8067.htm
- http://m.wap.fcful.cn/nnews/01273.htm
- http://m.wap.fcful.cn/nnews/63674.htm
- http://m.wap.fcful.cn/nnews/241565.htm
- http://m.wap.fcful.cn/nnews/13560.htm
- http://m.wap.fcful.cn/nnews/70472.htm
- http://m.wap.fcful.cn/nnews/365548.htm
- http://m.wap.fcful.cn/nnews/916891.htm
- http://m.wap.fcful.cn/nnews/8771735.htm
- http://m.wap.fcful.cn/nnews/997947.htm
- http://m.wap.fcful.cn/nnews/5873.htm
- http://m.wap.fcful.cn/nnews/92643.htm
- http://m.wap.fcful.cn/nnews/4786346.htm
- http://m.wap.fcful.cn/nnews/2662.htm
- http://m.wap.fcful.cn/nnews/7264.htm
- http://m.wap.fcful.cn/nnews/5158771.htm
- http://m.wap.fcful.cn/nnews/6475070.htm
- http://m.wap.fcful.cn/nnews/04101.htm
- http://m.wap.fcful.cn/nnews/1525703.htm
- http://m.wap.fcful.cn/nnews/7487.htm
- http://m.wap.fcful.cn/nnews/91334.htm
- http://m.wap.fcful.cn/nnews/2751146.htm
- http://m.wap.fcful.cn/nnews/97909.htm
- http://m.wap.fcful.cn/nnews/633687.htm
- http://m.wap.fcful.cn/nnews/41366.htm
- http://m.wap.fcful.cn/nnews/31850.htm
- http://m.wap.fcful.cn/nnews/23845.htm
- http://m.wap.fcful.cn/nnews/9325993.htm
- http://m.wap.fcful.cn/nnews/4612009.htm
- http://m.wap.fcful.cn/nnews/8925.htm
- http://m.wap.fcful.cn/nnews/4225.htm
- http://m.wap.fcful.cn/nnews/6446.htm
- http://m.wap.fcful.cn/nnews/07319.htm
- http://m.wap.fcful.cn/nnews/836183.htm
- http://m.wap.fcful.cn/nnews/190926.htm
- http://m.wap.fcful.cn/nnews/225997.htm
- http://m.wap.fcful.cn/nnews/001766.htm
- http://m.wap.fcful.cn/nnews/53121.htm
- http://m.wap.fcful.cn/nnews/1093267.htm
- http://m.wap.fcful.cn/nnews/085507.htm
- http://m.wap.fcful.cn/nnews/889847.htm
- http://m.wap.fcful.cn/nnews/775727.htm
- http://m.wap.fcful.cn/nnews/0820.htm
- http://m.wap.fcful.cn/nnews/038236.htm
- http://m.wap.fcful.cn/nnews/7542188.htm
- http://m.wap.fcful.cn/nnews/370032.htm
- http://m.wap.fcful.cn/nnews/80480.htm
- http://m.wap.fcful.cn/nnews/926982.htm
- http://m.wap.fcful.cn/nnews/5938099.htm
- http://m.wap.fcful.cn/nnews/71234.htm
- http://m.wap.fcful.cn/nnews/1289732.htm
- http://m.wap.fcful.cn/nnews/350411.htm
- http://m.wap.fcful.cn/nnews/08664.htm
- http://m.wap.fcful.cn/nnews/2255.htm
- http://m.wap.fcful.cn/nnews/114037.htm
- http://m.wap.fcful.cn/nnews/6560.htm
- http://m.wap.fcful.cn/nnews/070511.htm
- http://m.wap.fcful.cn/nnews/87852.htm
- http://m.wap.fcful.cn/nnews/4124.htm
- http://m.wap.fcful.cn/nnews/51403.htm
- http://m.wap.fcful.cn/nnews/2602499.htm
- http://m.wap.fcful.cn/nnews/0765724.htm
- http://m.wap.fcful.cn/nnews/1433.htm
- http://m.wap.fcful.cn/nnews/807777.htm
- http://m.wap.fcful.cn/nnews/965926.htm
- http://m.wap.fcful.cn/nnews/30169.htm
- http://m.wap.fcful.cn/nnews/87378.htm
- http://m.wap.fcful.cn/nnews/8054.htm
- http://m.wap.fcful.cn/nnews/77213.htm
- http://m.wap.fcful.cn/nnews/80472.htm
- http://m.wap.fcful.cn/nnews/9117307.htm
- http://m.wap.fcful.cn/nnews/67971.htm
- http://m.wap.fcful.cn/nnews/7749898.htm
- http://m.wap.fcful.cn/nnews/4582.htm
- http://m.wap.fcful.cn/nnews/039324.htm
- http://m.wap.fcful.cn/nnews/0333.htm
- http://m.wap.fcful.cn/nnews/7955855.htm
- http://m.wap.fcful.cn/nnews/1543831.htm
- http://m.wap.fcful.cn/nnews/4463.htm
- http://m.wap.fcful.cn/nnews/386452.htm
- http://m.wap.fcful.cn/nnews/600944.htm
- http://m.wap.fcful.cn/nnews/7709222.htm
- http://m.wap.fcful.cn/nnews/4365687.htm
- http://m.wap.fcful.cn/nnews/8690518.htm
- http://m.wap.fcful.cn/nnews/3769.htm
- http://m.wap.fcful.cn/nnews/2908.htm
- http://m.wap.fcful.cn/nnews/6165.htm
- http://m.wap.fcful.cn/nnews/81254.htm
- http://m.wap.fcful.cn/nnews/793089.htm
- http://m.wap.fcful.cn/nnews/7448917.htm
- http://m.wap.fcful.cn/nnews/8274.htm
- http://m.wap.fcful.cn/nnews/6900.htm
- http://m.wap.fcful.cn/nnews/4475875.htm
- http://m.wap.fcful.cn/nnews/388372.htm
- http://m.wap.fcful.cn/nnews/4610.htm
- http://m.wap.fcful.cn/nnews/355975.htm
- http://m.wap.fcful.cn/nnews/9805714.htm
- http://m.wap.fcful.cn/nnews/980583.htm
- http://m.wap.fcful.cn/nnews/5249.htm
- http://m.wap.fcful.cn/nnews/1116224.htm
- http://m.wap.fcful.cn/nnews/442883.htm
- http://m.wap.fcful.cn/nnews/60022.htm
- http://m.wap.fcful.cn/nnews/7862751.htm
- http://m.wap.fcful.cn/nnews/7196.htm
- http://m.wap.fcful.cn/nnews/6709323.htm
- http://m.wap.fcful.cn/nnews/10888.htm
- http://m.wap.fcful.cn/nnews/4423152.htm
- http://m.wap.fcful.cn/nnews/0574.htm
- http://m.wap.fcful.cn/nnews/6477.htm
- http://m.wap.fcful.cn/nnews/1531608.htm
- http://m.wap.fcful.cn/nnews/966233.htm
- http://m.wap.fcful.cn/nnews/085551.htm
- http://m.wap.fcful.cn/nnews/8779917.htm
- http://m.wap.fcful.cn/nnews/84434.htm
- http://m.wap.fcful.cn/nnews/418960.htm
- http://m.wap.fcful.cn/nnews/0538515.htm
- http://m.wap.fcful.cn/nnews/2386.htm
- http://m.wap.fcful.cn/nnews/819793.htm
- http://m.wap.fcful.cn/nnews/31779.htm
- http://m.wap.fcful.cn/nnews/100004.htm
- http://m.wap.fcful.cn/nnews/9802800.htm
- http://m.wap.fcful.cn/nnews/7652772.htm
- http://m.wap.fcful.cn/nnews/82183.htm
- http://m.wap.fcful.cn/nnews/039843.htm
- http://m.wap.fcful.cn/nnews/413193.htm
- http://m.wap.fcful.cn/nnews/578178.htm
- http://m.wap.fcful.cn/nnews/0764189.htm
- http://m.wap.fcful.cn/nnews/7229.htm
- http://m.wap.fcful.cn/nnews/4341973.htm
- http://m.wap.fcful.cn/nnews/12555.htm
- http://m.wap.fcful.cn/nnews/9668696.htm
- http://m.wap.fcful.cn/nnews/0163403.htm
- http://m.wap.fcful.cn/nnews/03905.htm
- http://m.wap.fcful.cn/nnews/0594.htm
- http://m.wap.fcful.cn/nnews/224951.htm
- http://m.wap.fcful.cn/nnews/6430.htm
- http://m.wap.fcful.cn/nnews/6222799.htm
- http://m.wap.fcful.cn/nnews/007236.htm
- http://m.wap.fcful.cn/nnews/6963.htm
- http://m.wap.fcful.cn/nnews/9113820.htm
- http://m.wap.fcful.cn/nnews/833703.htm
- http://m.wap.fcful.cn/nnews/69421.htm
- http://m.wap.fcful.cn/nnews/244887.htm
- http://m.wap.fcful.cn/nnews/42671.htm
- http://m.wap.fcful.cn/nnews/2018555.htm
- http://m.wap.fcful.cn/nnews/5020954.htm
- http://m.wap.fcful.cn/nnews/5247.htm
- http://m.wap.fcful.cn/nnews/0400700.htm
- http://m.wap.fcful.cn/nnews/9100.htm
- http://m.wap.fcful.cn/nnews/6441990.htm
- http://m.wap.fcful.cn/nnews/4679264.htm
- http://m.wap.fcful.cn/nnews/3581913.htm
- http://m.wap.fcful.cn/nnews/01671.htm
- http://m.wap.fcful.cn/nnews/50537.htm
- http://m.wap.fcful.cn/nnews/7526109.htm
- http://m.wap.fcful.cn/nnews/474593.htm
- http://m.wap.fcful.cn/nnews/39236.htm
- http://m.wap.fcful.cn/nnews/2803222.htm
- http://m.wap.fcful.cn/nnews/3891.htm
- http://m.wap.fcful.cn/nnews/5046.htm
- http://m.wap.fcful.cn/nnews/022790.htm
- http://m.wap.fcful.cn/nnews/299422.htm
- http://m.wap.fcful.cn/nnews/615218.htm
- http://m.wap.fcful.cn/nnews/606212.htm
- http://m.wap.fcful.cn/nnews/6095691.htm
- http://m.wap.fcful.cn/nnews/0686.htm
- http://m.wap.fcful.cn/nnews/617479.htm
- http://m.wap.fcful.cn/nnews/661989.htm
- http://m.wap.fcful.cn/nnews/16391.htm
- http://m.wap.fcful.cn/nnews/34785.htm
- http://m.wap.fcful.cn/nnews/8791.htm
- http://m.wap.fcful.cn/nnews/5724700.htm
- http://m.wap.fcful.cn/nnews/55870.htm
- http://m.wap.fcful.cn/nnews/6321661.htm
- http://m.wap.fcful.cn/nnews/7634.htm
- http://m.wap.fcful.cn/nnews/3658201.htm
- http://m.wap.fcful.cn/nnews/7087464.htm
- http://m.wap.fcful.cn/nnews/7763331.htm
- http://m.wap.fcful.cn/nnews/36979.htm
- http://m.wap.fcful.cn/nnews/993734.htm
- http://m.wap.fcful.cn/nnews/69295.htm
- http://m.wap.fcful.cn/nnews/24858.htm
- http://m.wap.fcful.cn/nnews/1177464.htm
- http://m.wap.fcful.cn/nnews/2214.htm
- http://m.wap.fcful.cn/nnews/36838.htm
- http://m.wap.fcful.cn/nnews/9421770.htm
- http://m.wap.fcful.cn/nnews/1838879.htm
- http://m.wap.fcful.cn/nnews/4621.htm
- http://m.wap.fcful.cn/nnews/88510.htm
- http://m.wap.fcful.cn/nnews/13356.htm
- http://m.wap.fcful.cn/nnews/441200.htm
- http://m.wap.fcful.cn/nnews/0247081.htm
- http://m.wap.fcful.cn/nnews/0666452.htm
- http://m.wap.fcful.cn/nnews/3442661.htm
- http://m.wap.fcful.cn/nnews/72554.htm
- http://m.wap.fcful.cn/nnews/2221631.htm
- http://m.wap.fcful.cn/nnews/700454.htm
- http://m.wap.fcful.cn/nnews/793608.htm
- http://m.wap.fcful.cn/nnews/800881.htm
- http://m.wap.fcful.cn/nnews/333118.htm
- http://m.wap.fcful.cn/nnews/79605.htm
- http://m.wap.fcful.cn/nnews/1054978.htm
- http://m.wap.fcful.cn/nnews/13296.htm
- http://m.wap.fcful.cn/nnews/9525904.htm
- http://m.wap.fcful.cn/nnews/432409.htm
- http://m.wap.fcful.cn/nnews/15091.htm
- http://m.wap.fcful.cn/nnews/663012.htm
- http://m.wap.fcful.cn/nnews/914952.htm
- http://m.wap.fcful.cn/nnews/4922.htm
- http://m.wap.fcful.cn/nnews/9701.htm
- http://m.wap.fcful.cn/nnews/440085.htm
- http://m.wap.fcful.cn/nnews/8188.htm
- http://m.wap.fcful.cn/nnews/7949.htm
- http://m.wap.fcful.cn/nnews/4268.htm
- http://m.wap.fcful.cn/nnews/58603.htm
- http://m.wap.fcful.cn/nnews/7463.htm
- http://m.wap.fcful.cn/nnews/4542.htm
- http://m.wap.fcful.cn/nnews/43094.htm
- http://m.wap.fcful.cn/nnews/160085.htm
- http://m.wap.fcful.cn/nnews/5271096.htm
- http://m.wap.fcful.cn/nnews/5460921.htm
- http://m.wap.fcful.cn/nnews/0883.htm
- http://m.wap.fcful.cn/nnews/63056.htm
- http://m.wap.fcful.cn/nnews/31641.htm
- http://m.wap.fcful.cn/nnews/463924.htm
- http://m.wap.fcful.cn/nnews/95069.htm
- http://m.wap.fcful.cn/nnews/3046.htm
- http://m.wap.fcful.cn/nnews/939766.htm
- http://m.wap.fcful.cn/nnews/355334.htm
- http://m.wap.fcful.cn/nnews/1811.htm
- http://m.wap.fcful.cn/nnews/3189692.htm
- http://m.wap.fcful.cn/nnews/17099.htm
- http://m.wap.fcful.cn/nnews/6985.htm
- http://m.wap.fcful.cn/nnews/78466.htm
- http://m.wap.fcful.cn/nnews/206487.htm
- http://m.wap.fcful.cn/nnews/774191.htm
- http://m.wap.fcful.cn/nnews/5873910.htm
- http://m.wap.fcful.cn/nnews/750072.htm
- http://m.wap.fcful.cn/nnews/632990.htm
- http://m.wap.fcful.cn/nnews/8233536.htm
- http://m.wap.fcful.cn/nnews/11293.htm
- http://m.wap.fcful.cn/nnews/04500.htm
- http://m.wap.fcful.cn/nnews/0438178.htm
- http://m.wap.fcful.cn/nnews/78803.htm
- http://m.wap.fcful.cn/nnews/88658.htm

## 项目结构

```
newsnav-core/
├── bin/                                 # 可执行脚本与命令行入口
│   ├── build-index.js                   # 索引构建脚本，触发全量或增量构建
│   └── serve.js                         # 开发服务器启动入口
├── config/                              # 全局配置目录
│   ├── sources.json                     # 新闻源定义，含 URL 模板与更新频率
│   ├── categories.yaml                  # 分类映射规则，定义标签与关键词对应关系
│   └── theme.css                        # 主题变量文件，控制颜色、字体与间距
├── src/                                 # 核心源码目录
│   ├── crawler/                         # 采集模块，负责拉取源数据与解析
│   │   ├── fetcher.js                   # HTTP 请求封装，含重试与超时逻辑
│   │   └── parser.js                    # HTML 与 JSON 解析器，提取标题与摘要
│   ├── indexer/                         # 索引模块，构建倒排索引与持久化
│   │   ├── builder.js                   # 索引构建主流程，调用分词与写入
│   │   └── store.js                     # 索引存储接口，基于 LevelDB 或内存
│   ├── search/                          # 检索模块，提供查询接口与结果排序
│   │   ├── query.js                     # 查询解析器，支持短语与布尔操作
│   │   └── ranker.js                    # 相关性排序算法，基于 TF-IDF 变体
│   ├── ui/                              # 前端界面相关源码
│   │   ├── app.js                       # 主应用逻辑，控制路由与视图切换
│   │   └── renderer.js                  # 列表与详情渲染函数，使用模板字符串
│   └── utils/                           # 通用工具函数
│       ├── logger.js                    # 日志输出，支持级别控制与文件写入
│       └── validator.js                 # URL 与数据类型校验工具
├── data/                                # 运行时数据目录（自动生成）
│   ├── index.db                         # 索引数据库文件
│   └── cache/                           # 原始响应缓存，用于增量对比
├── docs/                                # 完整文档目录，对应文档导航中各章节
│   ├── user-guide.md
│   ├── developer-guide.md
│   ├── api-reference.md
│   └── deployment.md
├── test/                                # 单元测试与集成测试目录
│   ├── crawler.test.js                  # 采集模块测试用例
│   └── indexer.test.js                  # 索引模块性能与正确性测试
├── .gitignore                           # Git 忽略规则，排除 data/ 与 node_modules
├── package.json                         # npm 项目配置文件，含依赖与脚本定义
├── README.md                            # 项目入口文档（本文件）
└── LICENSE                              # MIT 许可证文本
```

## 贡献指南

欢迎各类形式的贡献，包括但不限于代码提交、文档改进、问题报告与功能建议。请遵循以下流程以确保协作顺畅。

首先，在 GitHub 上 Fork 本仓库至个人账户，然后将 Fork 后的仓库克隆至本地开发环境。建议在新建的功能分支上进行修改，分支命名格式为 `feature/简述改动内容` 或 `fix/简述修复问题`，以便于后续追踪与审阅。

其次，确保本地已安装所有开发依赖，并通过 `npm test` 命令运行现有测试套件，确认环境配置正确且所有用例通过。若新增功能或修复缺陷，请同步编写对应的测试用例，保持测试覆盖率不低于现有水平。

第三，提交代码时请遵循 Conventional Commits 规范，提交信息格式为 `<类型>: <简短描述>`，其中类型包括 feat、fix、docs、style、refactor、perf、test、chore 等。提交前运行 `npm run lint` 进行代码风格检查，并修复所有报告的问题。

第四，完成修改后，将本地分支推送至个人远程仓库，并通过 GitHub 界面发起 Pull Request 至本仓库的 main 分支。请在 PR 描述中清晰说明改动目的、实现方式与测试结果，若关联已有 Issue 请一并引用。

最后，项目维护者将在收到 PR 后的五个工作日内进行审阅，可能会提出修改意见或进一步讨论。待所有反馈得到妥善处理后，PR 将被合并至主分支。对于重大功能或架构调整，建议先通过 Issue 发起讨论，确认方向后再进行开发。

## 常见问题

**问：构建索引时提示内存不足，应如何优化？**

答：当新闻源数量较大时，索引构建可能消耗较多内存。建议通过 `npm run build:index -- --batch-size 100` 参数控制批处理大小，每次仅处理 100 条记录，减少内存峰值。若仍无法满足，可调整 `config/sources.json` 中的 `concurrency` 字段，降低并行采集数量。此外，确保 Node.js 的 `--max-old-space-size` 参数已设置为适当值，例如 `node --max-old-space-size=1024 bin/build-index.js`。

**问：如何添加自定义新闻源或更新现有源？**

答：所有新闻源定义位于 `config/sources.json` 文件中，每个源包含 `name`、`url`、`category` 与 `updateInterval` 字段。添加新源时，复制已有条目并修改相应字段即可。新增或修改后，执行 `npm run build:index -- --full` 触发全量重建，使变更生效。请注意，URL 模板中的 `{id}` 占位符会在运行时被实际编号替换，请确保您的源地址遵循相同模式。

**问：系统是否支持部署到公网环境，并对外提供服务？**

答：可以。开发服务器 `npm start` 默认绑定至 `127.0.0.1`，仅限本地访问。若需对外服务，建议使用 `npm run serve -- --host 0.0.0.0 --port 8080` 启动，并在前端配置反向代理（如 Nginx）处理 HTTPS 终止与静态资源缓存。生产环境部署请参阅 `docs/deployment.md`，其中包含 systemd 服务配置、日志轮转与监控告警的详细说明。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
