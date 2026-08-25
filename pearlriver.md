# GQSKJ Navigator

GQSKJ Navigator 是一个面向移动端资讯聚合与深度链接导航的开源项目，专注于对 gqskj.cn 域名下分散的短篇新闻、公告及专题页面进行结构化整理与快速检索。项目定位于为开发者、内容运营者及终端用户提供一套可自部署的轻量级资讯索引方案，通过自动化采集与静态索引生成，将大量无规律的 .htm 链接转化为可分类、可搜索、可归档的知识库入口。

本项目不依赖任何第三方 CMS 框架，完全基于原生 JavaScript 与静态 HTML 构建，适合对页面加载速度、隐私保护及离线可用性有要求的场景。目标用户包括个人站长、技术文档维护者、企业内部知识库管理员以及需要批量管理短链资源的运维人员。通过本项目提供的索引生成工具，用户可以一键解析指定域名下的批量链接，自动提取标题、发布时间及内容摘要，并生成响应式导航页面，极大降低海量碎片化资讯的管理成本。

## 功能概览

批量链接解析引擎 支持从纯文本列表或远程数据源导入数百个 .htm 链接，自动完成去重、排序及合法性校验。

智能摘要抽取 针对 gqskj.cn 域名下的页面结构，内置多种选择器规则，可自适应提取正文首段、发布时间及分类标签。

静态导航站生成 基于解析结果生成移动优先的响应式 HTML 页面，支持按日期、按编号范围、按关键词的多维筛选与排序。

离线数据缓存 所有索引数据以 JSON 格式存储于本地，支持浏览器 IndexedDB 缓存，二次访问无需重复解析。

自定义主题系统 提供 CSS 变量与基础布局模板，允许用户自定义导航站配色、字体及卡片样式，适配不同品牌视觉。

增量更新机制 支持定时任务或 Webhook 触发增量扫描，仅处理新增或变更的链接，避免全量重建的资源浪费。

RESTful 查询接口 内置简易 HTTP 服务模块，提供 `/api/links`、`/api/search` 等标准接口，便于与其他系统集成。

多端适配输出 除标准 Web 页面外，支持导出为 Markdown 表格、CSV 清单及 JSON Feed 格式，满足不同消费端需求。

## 应用场景

企业内部知识库索引管理
企业运维团队可将散布在内部资讯平台上的数千条通知、变更记录、故障报告链接统一纳入 GQSKJ Navigator 管理，通过定时增量更新保持索引实时性，员工仅需访问一个导航页即可检索全部历史公告。

个人开发者的技术文档归档
技术博主或开源作者可利用本项目整理个人网站上的系列教程、API 文档或版本发布说明链接，生成按时间线排列的文档导航站，提升读者查阅体验，同时降低手动维护目录的负担。

内容运营团队的短链监控
新媒体运营人员可定期导入合作方提供的短链列表，利用本项目的摘要抽取功能快速核对各链接对应内容是否有效、是否与预期主题一致，及时发现死链或内容异常。

学术研究中的网络资源编目
研究人员在收集网络问卷、开源数据集或论文附录链接时，可使用 GQSKJ Navigator 对大量 URL 进行批量归档与元数据提取，生成结构化的资源清单，便于后续引用与核查。

## 快速开始

以下步骤指导您在本地环境中快速启动 GQSKJ Navigator 实例。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/gqskj-navigator.git

# 进入项目根目录
cd gqskj-navigator

# 安装依赖（项目仅依赖 Node.js 标准库与 npm 开发工具）
npm install

# 执行链接解析与索引构建（默认扫描 data/links.txt 中的链接列表）
npm run build

# 启动本地预览服务，默认监听端口 3000
npm start
```

执行完成后，访问 `http://localhost:3000` 即可查看生成的导航页面。如需导入用户提供的原始链接列表，请将链接逐行放入 `data/links.txt` 文件后重新执行 `npm run build`。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 16.x 或更高 | 用于运行构建脚本、HTTP 服务及工具链 |
| npm | 8.x 或更高 | 依赖管理及脚本执行环境 |
| 现代浏览器 | Chrome 90+, Firefox 88+, Safari 14+ | 用于访问生成的导航页面，支持 ES2020 特性 |
| 磁盘空间 | 至少 50 MB | 用于存储索引 JSON 文件及静态资源缓存 |
| 网络访问 | 外网或内网可达 gqskj.cn | 解析链接时需要访问原始页面以抽取摘要信息 |
| 操作系统 | Linux, macOS, Windows (WSL2 推荐) | 跨平台支持，但生产部署建议使用 Linux 环境 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户指南 | docs/user-guide.md | 如何配置链接列表、如何自定义主题、如何导出不同格式的索引数据 |
| 开发文档 | docs/developer-guide.md | 解析器扩展方式、新增选择器规则、API 接口详细定义及单元测试编写 |
| 部署手册 | docs/deployment.md | 生产环境下的 Nginx/Caddy 反向代理配置、系统服务注册、日志轮转策略 |
| 设计原理 | docs/design-principles.md | 索引数据结构设计、缓存失效策略、并发解析控制及性能优化依据 |

## 资源列表

- http://m.wap.gqskj.cn/snews/9665562.htm
- http://m.wap.gqskj.cn/snews/630280.htm
- http://m.wap.gqskj.cn/snews/6902293.htm
- http://m.wap.gqskj.cn/snews/08111.htm
- http://m.wap.gqskj.cn/snews/339856.htm
- http://m.wap.gqskj.cn/snews/15086.htm
- http://m.wap.gqskj.cn/snews/6526392.htm
- http://m.wap.gqskj.cn/snews/7246945.htm
- http://m.wap.gqskj.cn/snews/470317.htm
- http://m.wap.gqskj.cn/snews/6634711.htm
- http://m.wap.gqskj.cn/snews/1859925.htm
- http://m.wap.gqskj.cn/snews/400107.htm
- http://m.wap.gqskj.cn/snews/23130.htm
- http://m.wap.gqskj.cn/snews/99521.htm
- http://m.wap.gqskj.cn/snews/6845242.htm
- http://m.wap.gqskj.cn/snews/609216.htm
- http://m.wap.gqskj.cn/snews/9583.htm
- http://m.wap.gqskj.cn/snews/61891.htm
- http://m.wap.gqskj.cn/snews/024404.htm
- http://m.wap.gqskj.cn/snews/42710.htm
- http://m.wap.gqskj.cn/snews/97482.htm
- http://m.wap.gqskj.cn/snews/00358.htm
- http://m.wap.gqskj.cn/snews/7142.htm
- http://m.wap.gqskj.cn/snews/53242.htm
- http://m.wap.gqskj.cn/snews/171305.htm
- http://m.wap.gqskj.cn/snews/4844.htm
- http://m.wap.gqskj.cn/snews/458881.htm
- http://m.wap.gqskj.cn/snews/0185588.htm
- http://m.wap.gqskj.cn/snews/7474.htm
- http://m.wap.gqskj.cn/snews/53616.htm
- http://m.wap.gqskj.cn/snews/0960.htm
- http://m.wap.gqskj.cn/snews/7764973.htm
- http://m.wap.gqskj.cn/snews/2197.htm
- http://m.wap.gqskj.cn/snews/1258069.htm
- http://m.wap.gqskj.cn/snews/0172589.htm
- http://m.wap.gqskj.cn/snews/2453.htm
- http://m.wap.gqskj.cn/snews/8865845.htm
- http://m.wap.gqskj.cn/snews/979020.htm
- http://m.wap.gqskj.cn/snews/401306.htm
- http://m.wap.gqskj.cn/snews/039269.htm
- http://m.wap.gqskj.cn/snews/916382.htm
- http://m.wap.gqskj.cn/snews/97214.htm
- http://m.wap.gqskj.cn/snews/02041.htm
- http://m.wap.gqskj.cn/snews/1712.htm
- http://m.wap.gqskj.cn/snews/154550.htm
- http://m.wap.gqskj.cn/snews/6155.htm
- http://m.wap.gqskj.cn/snews/8795526.htm
- http://m.wap.gqskj.cn/snews/2329424.htm
- http://m.wap.gqskj.cn/snews/2851.htm
- http://m.wap.gqskj.cn/snews/184844.htm
- http://m.wap.gqskj.cn/snews/6876436.htm
- http://m.wap.gqskj.cn/snews/82639.htm
- http://m.wap.gqskj.cn/snews/74575.htm
- http://m.wap.gqskj.cn/snews/7283807.htm
- http://m.wap.gqskj.cn/snews/95424.htm
- http://m.wap.gqskj.cn/snews/4973408.htm
- http://m.wap.gqskj.cn/snews/4780.htm
- http://m.wap.gqskj.cn/snews/34319.htm
- http://m.wap.gqskj.cn/snews/0175.htm
- http://m.wap.gqskj.cn/snews/4903365.htm
- http://m.wap.gqskj.cn/snews/961134.htm
- http://m.wap.gqskj.cn/snews/3477.htm
- http://m.wap.gqskj.cn/snews/548502.htm
- http://m.wap.gqskj.cn/snews/8729.htm
- http://m.wap.gqskj.cn/snews/30768.htm
- http://m.wap.gqskj.cn/snews/8793.htm
- http://m.wap.gqskj.cn/snews/3247.htm
- http://m.wap.gqskj.cn/snews/8187921.htm
- http://m.wap.gqskj.cn/snews/2305.htm
- http://m.wap.gqskj.cn/snews/0719.htm
- http://m.wap.gqskj.cn/snews/478542.htm
- http://m.wap.gqskj.cn/snews/9449839.htm
- http://m.wap.gqskj.cn/snews/28496.htm
- http://m.wap.gqskj.cn/snews/2121958.htm
- http://m.wap.gqskj.cn/snews/82930.htm
- http://m.wap.gqskj.cn/snews/72504.htm
- http://m.wap.gqskj.cn/snews/156864.htm
- http://m.wap.gqskj.cn/snews/53237.htm
- http://m.wap.gqskj.cn/snews/1992.htm
- http://m.wap.gqskj.cn/snews/57943.htm
- http://m.wap.gqskj.cn/snews/92505.htm
- http://m.wap.gqskj.cn/snews/68717.htm
- http://m.wap.gqskj.cn/snews/36307.htm
- http://m.wap.gqskj.cn/snews/5579499.htm
- http://m.wap.gqskj.cn/snews/7083.htm
- http://m.wap.gqskj.cn/snews/6548209.htm
- http://m.wap.gqskj.cn/snews/49579.htm
- http://m.wap.gqskj.cn/snews/426839.htm
- http://m.wap.gqskj.cn/snews/926581.htm
- http://m.wap.gqskj.cn/snews/6490.htm
- http://m.wap.gqskj.cn/snews/787611.htm
- http://m.wap.gqskj.cn/snews/0706571.htm
- http://m.wap.gqskj.cn/snews/763730.htm
- http://m.wap.gqskj.cn/snews/116724.htm
- http://m.wap.gqskj.cn/snews/127877.htm
- http://m.wap.gqskj.cn/snews/636751.htm
- http://m.wap.gqskj.cn/snews/81022.htm
- http://m.wap.gqskj.cn/snews/3594817.htm
- http://m.wap.gqskj.cn/snews/3704432.htm
- http://m.wap.gqskj.cn/snews/2041755.htm
- http://m.wap.gqskj.cn/snews/8504470.htm
- http://m.wap.gqskj.cn/snews/112838.htm
- http://m.wap.gqskj.cn/snews/38325.htm
- http://m.wap.gqskj.cn/snews/1189.htm
- http://m.wap.gqskj.cn/snews/5907010.htm
- http://m.wap.gqskj.cn/snews/0657863.htm
- http://m.wap.gqskj.cn/snews/9374729.htm
- http://m.wap.gqskj.cn/snews/7433996.htm
- http://m.wap.gqskj.cn/snews/4542905.htm
- http://m.wap.gqskj.cn/snews/8318336.htm
- http://m.wap.gqskj.cn/snews/500882.htm
- http://m.wap.gqskj.cn/snews/9384.htm
- http://m.wap.gqskj.cn/snews/2697534.htm
- http://m.wap.gqskj.cn/snews/912267.htm
- http://m.wap.gqskj.cn/snews/0744.htm
- http://m.wap.gqskj.cn/snews/93414.htm
- http://m.wap.gqskj.cn/snews/119649.htm
- http://m.wap.gqskj.cn/snews/8477.htm
- http://m.wap.gqskj.cn/snews/74712.htm
- http://m.wap.gqskj.cn/snews/5351971.htm
- http://m.wap.gqskj.cn/snews/276488.htm
- http://m.wap.gqskj.cn/snews/8565624.htm
- http://m.wap.gqskj.cn/snews/26904.htm
- http://m.wap.gqskj.cn/snews/36695.htm
- http://m.wap.gqskj.cn/snews/87553.htm
- http://m.wap.gqskj.cn/snews/0265.htm
- http://m.wap.gqskj.cn/snews/7866375.htm
- http://m.wap.gqskj.cn/snews/6453549.htm
- http://m.wap.gqskj.cn/snews/6320.htm
- http://m.wap.gqskj.cn/snews/285244.htm
- http://m.wap.gqskj.cn/snews/224442.htm
- http://m.wap.gqskj.cn/snews/994215.htm
- http://m.wap.gqskj.cn/snews/61000.htm
- http://m.wap.gqskj.cn/snews/7785.htm
- http://m.wap.gqskj.cn/snews/0540050.htm
- http://m.wap.gqskj.cn/snews/11172.htm
- http://m.wap.gqskj.cn/snews/60336.htm
- http://m.wap.gqskj.cn/snews/44126.htm
- http://m.wap.gqskj.cn/snews/486206.htm
- http://m.wap.gqskj.cn/snews/664845.htm
- http://m.wap.gqskj.cn/snews/281202.htm
- http://m.wap.gqskj.cn/snews/87169.htm
- http://m.wap.gqskj.cn/snews/1035070.htm
- http://m.wap.gqskj.cn/snews/2422014.htm
- http://m.wap.gqskj.cn/snews/63539.htm
- http://m.wap.gqskj.cn/snews/9110894.htm
- http://m.wap.gqskj.cn/snews/1651896.htm
- http://m.wap.gqskj.cn/snews/6989984.htm
- http://m.wap.gqskj.cn/snews/4359064.htm
- http://m.wap.gqskj.cn/snews/9961221.htm
- http://m.wap.gqskj.cn/snews/94311.htm
- http://m.wap.gqskj.cn/snews/2868955.htm
- http://m.wap.gqskj.cn/snews/877816.htm
- http://m.wap.gqskj.cn/snews/275294.htm
- http://m.wap.gqskj.cn/snews/39717.htm
- http://m.wap.gqskj.cn/snews/01615.htm
- http://m.wap.gqskj.cn/snews/6320141.htm
- http://m.wap.gqskj.cn/snews/0581739.htm
- http://m.wap.gqskj.cn/snews/220852.htm
- http://m.wap.gqskj.cn/snews/578969.htm
- http://m.wap.gqskj.cn/snews/2806.htm
- http://m.wap.gqskj.cn/snews/45463.htm
- http://m.wap.gqskj.cn/snews/01511.htm
- http://m.wap.gqskj.cn/snews/56635.htm
- http://m.wap.gqskj.cn/snews/0404096.htm
- http://m.wap.gqskj.cn/snews/8670.htm
- http://m.wap.gqskj.cn/snews/52666.htm
- http://m.wap.gqskj.cn/snews/80386.htm
- http://m.wap.gqskj.cn/snews/635256.htm
- http://m.wap.gqskj.cn/snews/670400.htm
- http://m.wap.gqskj.cn/snews/66374.htm
- http://m.wap.gqskj.cn/snews/8846284.htm
- http://m.wap.gqskj.cn/snews/552166.htm
- http://m.wap.gqskj.cn/snews/6179757.htm
- http://m.wap.gqskj.cn/snews/45576.htm
- http://m.wap.gqskj.cn/snews/97759.htm
- http://m.wap.gqskj.cn/snews/0104.htm
- http://m.wap.gqskj.cn/snews/3073.htm
- http://m.wap.gqskj.cn/snews/8359466.htm
- http://m.wap.gqskj.cn/snews/0174.htm
- http://m.wap.gqskj.cn/snews/88554.htm
- http://m.wap.gqskj.cn/snews/3723854.htm
- http://m.wap.gqskj.cn/snews/2989.htm
- http://m.wap.gqskj.cn/snews/907167.htm
- http://m.wap.gqskj.cn/snews/46441.htm
- http://m.wap.gqskj.cn/snews/226379.htm
- http://m.wap.gqskj.cn/snews/552323.htm
- http://m.wap.gqskj.cn/snews/3974194.htm
- http://m.wap.gqskj.cn/snews/7810511.htm
- http://m.wap.gqskj.cn/snews/148475.htm
- http://m.wap.gqskj.cn/snews/5612.htm
- http://m.wap.gqskj.cn/snews/5625377.htm
- http://m.wap.gqskj.cn/snews/8363155.htm
- http://m.wap.gqskj.cn/snews/64836.htm
- http://m.wap.gqskj.cn/snews/29035.htm
- http://m.wap.gqskj.cn/snews/8656173.htm
- http://m.wap.gqskj.cn/snews/0318378.htm
- http://m.wap.gqskj.cn/snews/040759.htm
- http://m.wap.gqskj.cn/snews/111031.htm
- http://m.wap.gqskj.cn/snews/7126.htm
- http://m.wap.gqskj.cn/snews/4229880.htm
- http://m.wap.gqskj.cn/snews/5205904.htm
- http://m.wap.gqskj.cn/snews/0052664.htm
- http://m.wap.gqskj.cn/snews/7291.htm
- http://m.wap.gqskj.cn/snews/26875.htm
- http://m.wap.gqskj.cn/snews/3578670.htm
- http://m.wap.gqskj.cn/snews/3707551.htm
- http://m.wap.gqskj.cn/snews/86829.htm
- http://m.wap.gqskj.cn/snews/7562.htm
- http://m.wap.gqskj.cn/snews/4170.htm
- http://m.wap.gqskj.cn/snews/1101785.htm
- http://m.wap.gqskj.cn/snews/0767503.htm
- http://m.wap.gqskj.cn/snews/7107.htm
- http://m.wap.gqskj.cn/snews/64838.htm
- http://m.wap.gqskj.cn/snews/1637.htm
- http://m.wap.gqskj.cn/snews/57892.htm
- http://m.wap.gqskj.cn/snews/7079.htm
- http://m.wap.gqskj.cn/snews/9967989.htm
- http://m.wap.gqskj.cn/snews/8685210.htm
- http://m.wap.gqskj.cn/snews/8399806.htm
- http://m.wap.gqskj.cn/snews/4965.htm
- http://m.wap.gqskj.cn/snews/330646.htm
- http://m.wap.gqskj.cn/snews/28610.htm
- http://m.wap.gqskj.cn/snews/2861596.htm
- http://m.wap.gqskj.cn/snews/8616253.htm
- http://m.wap.gqskj.cn/snews/3500377.htm
- http://m.wap.gqskj.cn/snews/40420.htm
- http://m.wap.gqskj.cn/snews/8182.htm
- http://m.wap.gqskj.cn/snews/1556825.htm
- http://m.wap.gqskj.cn/snews/084380.htm
- http://m.wap.gqskj.cn/snews/26388.htm
- http://m.wap.gqskj.cn/snews/7442959.htm
- http://m.wap.gqskj.cn/snews/6487916.htm
- http://m.wap.gqskj.cn/snews/0871.htm
- http://m.wap.gqskj.cn/snews/2229149.htm
- http://m.wap.gqskj.cn/snews/15779.htm
- http://m.wap.gqskj.cn/snews/9730028.htm
- http://m.wap.gqskj.cn/snews/1170960.htm
- http://m.wap.gqskj.cn/snews/4984719.htm
- http://m.wap.gqskj.cn/snews/32096.htm
- http://m.wap.gqskj.cn/snews/7903747.htm
- http://m.wap.gqskj.cn/snews/7956.htm
- http://m.wap.gqskj.cn/snews/5201354.htm
- http://m.wap.gqskj.cn/snews/98946.htm
- http://m.wap.gqskj.cn/snews/6462796.htm
- http://m.wap.gqskj.cn/snews/61155.htm
- http://m.wap.gqskj.cn/snews/0272956.htm
- http://m.wap.gqskj.cn/snews/192844.htm
- http://m.wap.gqskj.cn/snews/4053110.htm
- http://m.wap.gqskj.cn/snews/4032.htm

## 项目结构

项目采用模块化分层设计，各目录职责清晰，便于维护与扩展。

```
gqskj-navigator/
├── bin/                                # 可执行脚本与 CLI 入口
│   ├── build.js                        # 构建主流程：读取链接、解析、生成索引
│   └── serve.js                        # 开发服务器启动脚本
├── src/                                # 核心源代码目录
│   ├── core/                           # 核心引擎模块
│   │   ├── fetcher.js                  # 负责 HTTP 请求与重试逻辑，含超时控制
│   │   ├── parser.js                   # 针对 gqskj.cn 的 HTML 解析与摘要抽取
│   │   ├── indexer.js                  # 构建倒排索引与分类聚合
│   │   └── cache.js                    # 基于 Node.js 文件系统的 JSON 缓存管理
│   ├── api/                            # RESTful 接口实现
│   │   ├── routes.js                   # 路由注册与请求参数校验
│   │   └── handlers.js                 # 各接口的业务逻辑处理函数
│   ├── web/                            # 前端资源文件
│   │   ├── assets/                     # 静态资源（图标、字体、默认图片）
│   │   ├── styles/                     # CSS 样式模块，含主题变量与响应式布局
│   │   └── scripts/                    # 前端交互脚本，实现筛选、排序与本地缓存
│   └── templates/                      # 页面模板引擎
│       ├── index.ejs                   # 导航首页模板，渲染链接列表与筛选器
│       └── detail.ejs                  # 单链接详情页模板（预留）
├── data/                               # 数据存储目录
│   ├── links.txt                       # 用户提供的原始链接列表（每行一个 URL）
│   ├── index.json                      # 构建后生成的完整索引数据
│   └── meta.json                       # 元数据记录（最后构建时间、链接总数等）
├── tests/                              # 单元测试与集成测试
│   ├── fetcher.test.js                 # 对 fetcher 模块的模拟请求测试
│   ├── parser.test.js                  # 对不同结构页面的解析覆盖率测试
│   └── indexer.test.js                 # 索引构建与查询的准确性测试
├── config/                             # 项目配置文件目录
│   ├── default.json                    # 默认配置（端口、超时、解析规则）
│   └── production.json                 # 生产环境覆盖配置（日志级别、缓存路径）
├── docs/                               # 完整项目文档（详见文档导航章节）
├── .github/                            # GitHub 相关自动化
│   └── workflows/                      # CI/CD 流水线配置（自动构建与静态部署）
├── package.json                        # npm 依赖清单与脚本定义
├── README.md                           # 项目介绍与快速入门（本文件）
└── LICENSE                             # MIT 许可证文本
```

## 贡献指南

我们欢迎并鼓励社区贡献，无论是问题报告、功能建议还是代码提交。请遵循以下步骤参与本项目。

1. 查阅现有 Issue 与 Pull Request
在提交新内容前，请先访问 GitHub Issues 与 Pull Requests 页面，确认是否已有类似讨论或进行中的工作，避免重复劳动。

2. Fork 仓库并创建功能分支
将本项目 Fork 至个人账户，然后基于 main 分支创建新的功能分支（例如 feature/add-custom-selector），在该分支上进行所有修改。

3. 编写或修改代码并补充测试
所有新增功能或 bug 修复均应附带相应的单元测试用例，确保测试覆盖率达到 80% 以上。运行 `npm test` 验证本地所有测试通过。

4. 更新文档与示例
若修改涉及用户可见行为（如配置项变更、API 接口调整），请同步更新 docs/ 目录下的相关文档，并在 README 中补充必要的说明。

5. 提交 Pull Request
推送分支至个人 Fork 仓库后，向主仓库的 main 分支提交 Pull Request。描述中请清晰说明修改目的、实现方式及测试结果，等待维护者审核。

## 常见问题

**问：项目是否必须联网才能运行？解析过程是否会大量消耗源站资源？**

答：首次构建索引时，由于需要抓取 gqskj.cn 下每个 .htm 页面的标题与摘要，因此必须保持网络通畅。项目内置了请求间隔控制（默认 500ms 延迟）与并发限制（最多 5 个并行请求），以避免对源站造成压力。构建完成后，所有数据缓存于本地，后续访问导航页面无需再次联网。如需增量更新，可通过配置 `--since` 参数仅抓取指定时间之后的新链接。

**问：如果 gqskj.cn 的页面结构发生变化，导致解析失败，应该如何处理？**

答：项目将解析规则抽象至 `src/core/parser.js` 中的 `selectors` 配置对象，用户可根据实际页面结构调整其中的 CSS 选择器或正则表达式。若结构变动较大，可参考 `docs/developer-guide.md` 中的“自定义解析器”章节，通过继承基础 Parser 类并重写 `extractFields` 方法来适配新结构，无需修改核心代码。

**问：导航页面的搜索功能是否支持模糊匹配或中文分词？**

答：当前版本支持基于关键词的全文检索，采用简单的三元组倒排索引实现，匹配规则为包含关系（子串匹配）。中文分词尚未内置，但项目已预留 `tokenizer` 扩展接口，用户可接入 `nodejieba` 或 `segment` 等第三方分词库以提升中文搜索精度。具体集成方式请参考 `docs/developer-guide.md` 中的“搜索增强”章节。

## 许可证

MIT License

Copyright (c) 2026 GQSKJ Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
