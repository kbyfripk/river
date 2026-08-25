# WebLink Navigator

WebLink Navigator 是一个面向技术研究、信息聚合与内容归档的开源外链管理工具，专为需要系统化整理大量分散 URL 资源的开发者、数据分析师与内容策展人设计。该项目不提供爬虫功能，不存储用户数据，仅提供一套标准化的 URL 索引结构与元数据标注框架，帮助用户将原始链接集合转化为可检索、可分类、可版本控制的知识资产。

项目定位为轻量级链接治理中间件，适用于个人书签库迁移、团队共享资源池构建、公开情报源归档等场景。通过统一的前端面板与命令行接口，用户可批量导入原始 URL，自动提取域名、路径层级、文件类型等特征，并支持自定义标签与备注字段。WebLink Navigator 不依赖第三方 API，所有处理逻辑在本地执行，确保链接数据的隐私性与可控性。

## 功能概览

**批量导入与去重** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动检测并合并重复条目，保留首次导入时间戳。

**智能特征提取** 对每条 URL 自动解析协议类型、二级域名、路径深度、查询参数与文件扩展名，生成可用于筛选的结构化字段。

**多级标签体系** 允许用户创建无限层级的标签分类树，每条链接可绑定多个标签，支持基于标签的快速过滤与统计。

**全文检索与过滤** 基于 URL 字符串、备注内容、导入时间范围与标签组合进行多条件布尔检索，检索结果支持排序与导出。

**链接可用性检测** 提供可选的定时任务模块，通过 HEAD 请求检测链接是否可访问，并记录状态码与响应时间，辅助用户清理失效资源。

**数据快照与回滚** 每次修改操作自动生成 JSON 格式的快照文件，存储于 .snapshots 目录，支持按时间点回滚至任意历史状态。

**导出与集成** 支持将当前链接集合导出为纯文本列表、CSV 表格或 JSON 结构化数据，便于导入其他工具或用于自动化流水线。

## 应用场景

**技术文档聚合** 技术团队可将分散在多个内部 Wiki、代码仓库 Issue 与在线教程中的参考链接统一纳入 WebLink Navigator，通过标签区分环境（开发/测试/生产）与主题（数据库/网络/安全），构建团队共享的知识索引。

**公开情报源管理** 安全研究人员或舆情分析师可使用本工具对大量情报源 URL 进行分类归档，结合备注字段记录每个来源的覆盖范围与更新频率，定期运行可用性检测以剔除失效源。

**个人书签库重构** 浏览器导出的书签 HTML 文件通常缺乏灵活的筛选与批处理能力。用户可将书签链接导入 WebLink Navigator，利用多级标签重新组织，再按需导出为结构化数据供其他应用消费。

**数据迁移前校验** 在进行站点迁移或 CDN 切换时，运维人员可将涉及的所有资源 URL 导入工具，统一审查协议一致性、路径规范性与域名归属，避免迁移过程中出现遗漏或错误引用。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 与 Node.js 18.x 及以上版本。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run build
npm start
```

执行完成后，终端将输出本地服务地址（默认 http://127.0.0.1:3000），打开浏览器访问该地址即可进入 Web 管理面板。首次启动会自动生成配置文件 config.yml 与空数据库文件 data/db.json。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 用于克隆仓库与版本管理 |
| 磁盘空间 | 至少 200 MB 可用 | 存储数据库、快照与日志文件 |
| 内存 | 建议 512 MB 以上 | 处理超过 10 万条链接时建议增加内存至 1 GB |
| 操作系统 | Linux / macOS / Windows 10+ | Windows 用户需启用 WSL 或使用 PowerShell 7 |
| 数据库引擎 | 内置 JSON 存储（无需外部数据库） | 生产环境可替换为 PostgreSQL，通过环境变量 DATABASE_URL 配置 |
| 定时任务依赖 | node-cron（自动安装） | 用于可用性检测模块，可禁用 |
| 浏览器 | 现代浏览器（Chrome / Firefox / Edge） | 管理面板前端无需额外插件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|----------|
| 用户手册 | /docs/user-guide/ | 如何导入链接、如何创建标签、如何执行检索与导出操作 |
| 配置参考 | /docs/config-reference/ | config.yml 中每个字段的含义、默认值与可选项 |
| 开发指南 | /docs/development/ | 项目架构图、插件扩展机制、新增特征提取器的步骤 |
| API 接口 | /docs/api/ | RESTful API 端点列表、请求示例、错误码说明、速率限制策略 |
| 运维手册 | /docs/operations/ | 日志配置、快照策略、性能调优参数、备份与恢复流程 |
| 常见问题 | /docs/faq/ | 高频问题集锦，涵盖安装报错、中文乱码、端口冲突等 |

## 资源列表

- http://m.wap.fcful.cn/nnews/42490.htm
- http://m.wap.fcful.cn/nnews/784738.htm
- http://m.wap.fcful.cn/nnews/7047.htm
- http://m.wap.fcful.cn/nnews/0524.htm
- http://m.wap.fcful.cn/nnews/0164.htm
- http://m.wap.fcful.cn/nnews/984680.htm
- http://m.wap.fcful.cn/nnews/79095.htm
- http://m.wap.fcful.cn/nnews/1061.htm
- http://m.wap.fcful.cn/nnews/6774085.htm
- http://m.wap.fcful.cn/nnews/6777763.htm
- http://m.wap.fcful.cn/nnews/524057.htm
- http://m.wap.fcful.cn/nnews/585658.htm
- http://m.wap.fcful.cn/nnews/933463.htm
- http://m.wap.fcful.cn/nnews/755915.htm
- http://m.wap.fcful.cn/nnews/4246.htm
- http://m.wap.fcful.cn/nnews/8316771.htm
- http://m.wap.fcful.cn/nnews/122823.htm
- http://m.wap.fcful.cn/nnews/6883.htm
- http://m.wap.fcful.cn/nnews/8688296.htm
- http://m.wap.fcful.cn/nnews/0416158.htm
- http://m.wap.fcful.cn/nnews/442075.htm
- http://m.wap.fcful.cn/nnews/8024.htm
- http://m.wap.fcful.cn/nnews/3798814.htm
- http://m.wap.fcful.cn/nnews/6952.htm
- http://m.wap.fcful.cn/nnews/2777.htm
- http://m.wap.fcful.cn/nnews/1128892.htm
- http://m.wap.fcful.cn/nnews/196190.htm
- http://m.wap.fcful.cn/nnews/4023103.htm
- http://m.wap.fcful.cn/nnews/688559.htm
- http://m.wap.fcful.cn/nnews/58347.htm
- http://m.wap.fcful.cn/nnews/6066.htm
- http://m.wap.fcful.cn/nnews/1783.htm
- http://m.wap.fcful.cn/nnews/92531.htm
- http://m.wap.fcful.cn/nnews/40742.htm
- http://m.wap.fcful.cn/nnews/7803195.htm
- http://m.wap.fcful.cn/nnews/5470995.htm
- http://m.wap.fcful.cn/nnews/5772.htm
- http://m.wap.fcful.cn/nnews/6762.htm
- http://m.wap.fcful.cn/nnews/1695.htm
- http://m.wap.fcful.cn/nnews/3346639.htm
- http://m.wap.fcful.cn/nnews/704592.htm
- http://m.wap.fcful.cn/nnews/960235.htm
- http://m.wap.fcful.cn/nnews/46300.htm
- http://m.wap.fcful.cn/nnews/1831.htm
- http://m.wap.fcful.cn/nnews/536427.htm
- http://m.wap.fcful.cn/nnews/29226.htm
- http://m.wap.fcful.cn/nnews/6248187.htm
- http://m.wap.fcful.cn/nnews/34395.htm
- http://m.wap.fcful.cn/nnews/257452.htm
- http://m.wap.fcful.cn/nnews/56705.htm
- http://m.wap.fcful.cn/nnews/264863.htm
- http://m.wap.fcful.cn/nnews/44182.htm
- http://m.wap.fcful.cn/nnews/5653831.htm
- http://m.wap.fcful.cn/nnews/254904.htm
- http://m.wap.fcful.cn/nnews/13950.htm
- http://m.wap.fcful.cn/nnews/90883.htm
- http://m.wap.fcful.cn/nnews/371054.htm
- http://m.wap.fcful.cn/nnews/8924.htm
- http://m.wap.fcful.cn/nnews/00177.htm
- http://m.wap.fcful.cn/nnews/9546.htm
- http://m.wap.fcful.cn/nnews/2701.htm
- http://m.wap.fcful.cn/nnews/346897.htm
- http://m.wap.fcful.cn/nnews/76038.htm
- http://m.wap.fcful.cn/nnews/3670.htm
- http://m.wap.fcful.cn/nnews/5569221.htm
- http://m.wap.fcful.cn/nnews/120500.htm
- http://m.wap.fcful.cn/nnews/220830.htm
- http://m.wap.fcful.cn/nnews/54258.htm
- http://m.wap.fcful.cn/nnews/502828.htm
- http://m.wap.fcful.cn/nnews/714635.htm
- http://m.wap.fcful.cn/nnews/228304.htm
- http://m.wap.fcful.cn/nnews/01445.htm
- http://m.wap.fcful.cn/nnews/3244445.htm
- http://m.wap.fcful.cn/nnews/04814.htm
- http://m.wap.fcful.cn/nnews/6772503.htm
- http://m.wap.fcful.cn/nnews/99857.htm
- http://m.wap.fcful.cn/nnews/758352.htm
- http://m.wap.fcful.cn/nnews/3212.htm
- http://m.wap.fcful.cn/nnews/2457698.htm
- http://m.wap.fcful.cn/nnews/1139015.htm
- http://m.wap.fcful.cn/nnews/801000.htm
- http://m.wap.fcful.cn/nnews/3808.htm
- http://m.wap.fcful.cn/nnews/621001.htm
- http://m.wap.fcful.cn/nnews/3249060.htm
- http://m.wap.fcful.cn/nnews/4920.htm
- http://m.wap.fcful.cn/nnews/2045260.htm
- http://m.wap.fcful.cn/nnews/524508.htm
- http://m.wap.fcful.cn/nnews/5424128.htm
- http://m.wap.fcful.cn/nnews/103495.htm
- http://m.wap.fcful.cn/nnews/985837.htm
- http://m.wap.fcful.cn/nnews/8010222.htm
- http://m.wap.fcful.cn/nnews/65126.htm
- http://m.wap.fcful.cn/nnews/0618845.htm
- http://m.wap.fcful.cn/nnews/52038.htm
- http://m.wap.fcful.cn/nnews/780225.htm
- http://m.wap.fcful.cn/nnews/20612.htm
- http://m.wap.fcful.cn/nnews/075013.htm
- http://m.wap.fcful.cn/nnews/089573.htm
- http://m.wap.fcful.cn/nnews/0734.htm
- http://m.wap.fcful.cn/nnews/82037.htm
- http://m.wap.fcful.cn/nnews/3133931.htm
- http://m.wap.fcful.cn/nnews/6459362.htm
- http://m.wap.fcful.cn/nnews/083490.htm
- http://m.wap.fcful.cn/nnews/66534.htm
- http://m.wap.fcful.cn/nnews/0752278.htm
- http://m.wap.fcful.cn/nnews/7529.htm
- http://m.wap.fcful.cn/nnews/720663.htm
- http://m.wap.fcful.cn/nnews/0343.htm
- http://m.wap.fcful.cn/nnews/429224.htm
- http://m.wap.fcful.cn/nnews/582543.htm
- http://m.wap.fcful.cn/nnews/88205.htm
- http://m.wap.fcful.cn/nnews/137279.htm
- http://m.wap.fcful.cn/nnews/34432.htm
- http://m.wap.fcful.cn/nnews/55884.htm
- http://m.wap.fcful.cn/nnews/054565.htm
- http://m.wap.fcful.cn/nnews/7175335.htm
- http://m.wap.fcful.cn/nnews/0588000.htm
- http://m.wap.fcful.cn/nnews/36701.htm
- http://m.wap.fcful.cn/nnews/3736.htm
- http://m.wap.fcful.cn/nnews/55571.htm
- http://m.wap.fcful.cn/nnews/9615.htm
- http://m.wap.fcful.cn/nnews/19043.htm
- http://m.wap.fcful.cn/nnews/38636.htm
- http://m.wap.fcful.cn/nnews/2062.htm
- http://m.wap.fcful.cn/nnews/965598.htm
- http://m.wap.fcful.cn/nnews/8645.htm
- http://m.wap.fcful.cn/nnews/2823664.htm
- http://m.wap.fcful.cn/nnews/5727812.htm
- http://m.wap.fcful.cn/nnews/11652.htm
- http://m.wap.fcful.cn/nnews/860829.htm
- http://m.wap.fcful.cn/nnews/882487.htm
- http://m.wap.fcful.cn/nnews/8359.htm
- http://m.wap.fcful.cn/nnews/5544.htm
- http://m.wap.fcful.cn/nnews/7405.htm
- http://m.wap.fcful.cn/nnews/7419.htm
- http://m.wap.fcful.cn/nnews/0735.htm
- http://m.wap.fcful.cn/nnews/63291.htm
- http://m.wap.fcful.cn/nnews/3627095.htm
- http://m.wap.fcful.cn/nnews/8511.htm
- http://m.wap.fcful.cn/nnews/0614.htm
- http://m.wap.fcful.cn/nnews/991387.htm
- http://m.wap.fcful.cn/nnews/7545490.htm
- http://m.wap.fcful.cn/nnews/381698.htm
- http://m.wap.fcful.cn/nnews/2597.htm
- http://m.wap.fcful.cn/nnews/1036666.htm
- http://m.wap.fcful.cn/nnews/731898.htm
- http://m.wap.fcful.cn/nnews/1653.htm
- http://m.wap.fcful.cn/nnews/19023.htm
- http://m.wap.fcful.cn/nnews/22220.htm
- http://m.wap.fcful.cn/nnews/7325222.htm
- http://m.wap.fcful.cn/nnews/01751.htm
- http://m.wap.fcful.cn/nnews/8352658.htm
- http://m.wap.fcful.cn/nnews/1131014.htm
- http://m.wap.fcful.cn/nnews/706638.htm
- http://m.wap.fcful.cn/nnews/3479785.htm
- http://m.wap.fcful.cn/nnews/693479.htm
- http://m.wap.fcful.cn/nnews/2730.htm
- http://m.wap.fcful.cn/nnews/8556420.htm
- http://m.wap.fcful.cn/nnews/9164235.htm
- http://m.wap.fcful.cn/nnews/5455139.htm
- http://m.wap.fcful.cn/nnews/7462.htm
- http://m.wap.fcful.cn/nnews/295055.htm
- http://m.wap.fcful.cn/nnews/5078535.htm
- http://m.wap.fcful.cn/nnews/5280.htm
- http://m.wap.fcful.cn/nnews/2253.htm
- http://m.wap.fcful.cn/nnews/51665.htm
- http://m.wap.fcful.cn/nnews/7377.htm
- http://m.wap.fcful.cn/nnews/452089.htm
- http://m.wap.fcful.cn/nnews/033716.htm
- http://m.wap.fcful.cn/nnews/79503.htm
- http://m.wap.fcful.cn/nnews/6183241.htm
- http://m.wap.fcful.cn/nnews/011903.htm
- http://m.wap.fcful.cn/nnews/0822797.htm
- http://m.wap.fcful.cn/nnews/93805.htm
- http://m.wap.fcful.cn/nnews/24240.htm
- http://m.wap.fcful.cn/nnews/57861.htm
- http://m.wap.fcful.cn/nnews/4177.htm
- http://m.wap.fcful.cn/nnews/2324496.htm
- http://m.wap.fcful.cn/nnews/8670243.htm
- http://m.wap.fcful.cn/nnews/6350.htm
- http://m.wap.fcful.cn/nnews/0181.htm
- http://m.wap.fcful.cn/nnews/5223.htm
- http://m.wap.fcful.cn/nnews/5233.htm
- http://m.wap.fcful.cn/nnews/1632.htm
- http://m.wap.fcful.cn/nnews/083933.htm
- http://m.wap.fcful.cn/nnews/5491.htm
- http://m.wap.fcful.cn/nnews/0314472.htm
- http://m.wap.fcful.cn/nnews/43463.htm
- http://m.wap.fcful.cn/nnews/75268.htm
- http://m.wap.fcful.cn/nnews/125877.htm
- http://m.wap.fcful.cn/nnews/3043268.htm
- http://m.wap.fcful.cn/nnews/48959.htm
- http://m.wap.fcful.cn/nnews/292363.htm
- http://m.wap.fcful.cn/nnews/01614.htm
- http://m.wap.fcful.cn/nnews/4939421.htm
- http://m.wap.fcful.cn/nnews/5319515.htm
- http://m.wap.fcful.cn/nnews/2486608.htm
- http://m.wap.fcful.cn/nnews/872492.htm
- http://m.wap.fcful.cn/nnews/2555.htm
- http://m.wap.fcful.cn/nnews/2872.htm
- http://m.wap.fcful.cn/nnews/3294902.htm
- http://m.wap.fcful.cn/nnews/1092.htm
- http://m.wap.fcful.cn/nnews/443345.htm
- http://m.wap.fcful.cn/nnews/157653.htm
- http://m.wap.fcful.cn/nnews/1420938.htm
- http://m.wap.fcful.cn/nnews/6382.htm
- http://m.wap.fcful.cn/nnews/0793607.htm
- http://m.wap.fcful.cn/nnews/03812.htm
- http://m.wap.fcful.cn/nnews/443795.htm
- http://m.wap.fcful.cn/nnews/373401.htm
- http://m.wap.fcful.cn/nnews/4797.htm
- http://m.wap.fcful.cn/nnews/5082954.htm
- http://m.wap.fcful.cn/nnews/8505.htm
- http://m.wap.fcful.cn/nnews/13201.htm
- http://m.wap.fcful.cn/nnews/8589711.htm
- http://m.wap.fcful.cn/nnews/0773236.htm
- http://m.wap.fcful.cn/nnews/8890955.htm
- http://m.wap.fcful.cn/nnews/2754.htm
- http://m.wap.fcful.cn/nnews/15263.htm
- http://m.wap.fcful.cn/nnews/258763.htm
- http://m.wap.fcful.cn/nnews/3730792.htm
- http://m.wap.fcful.cn/nnews/75308.htm
- http://m.wap.fcful.cn/nnews/2698133.htm
- http://m.wap.fcful.cn/nnews/518312.htm
- http://m.wap.fcful.cn/nnews/69540.htm
- http://m.wap.fcful.cn/nnews/07007.htm
- http://m.wap.fcful.cn/nnews/70417.htm
- http://m.wap.fcful.cn/nnews/2893562.htm
- http://m.wap.fcful.cn/nnews/76868.htm
- http://m.wap.fcful.cn/nnews/315587.htm
- http://m.wap.fcful.cn/nnews/3125098.htm
- http://m.wap.fcful.cn/nnews/5199448.htm
- http://m.wap.fcful.cn/nnews/388715.htm
- http://m.wap.fcful.cn/nnews/7113.htm
- http://m.wap.fcful.cn/nnews/19660.htm
- http://m.wap.fcful.cn/nnews/357196.htm
- http://m.wap.fcful.cn/nnews/898415.htm
- http://m.wap.fcful.cn/nnews/97252.htm
- http://m.wap.fcful.cn/nnews/31154.htm
- http://m.wap.fcful.cn/nnews/46471.htm
- http://m.wap.fcful.cn/nnews/66457.htm
- http://m.wap.fcful.cn/nnews/68623.htm
- http://m.wap.fcful.cn/nnews/93718.htm
- http://m.wap.fcful.cn/nnews/014970.htm
- http://m.wap.fcful.cn/nnews/5554.htm
- http://m.wap.fcful.cn/nnews/50112.htm
- http://m.wap.fcful.cn/nnews/6292041.htm
- http://m.wap.fcful.cn/nnews/44036.htm
- http://m.wap.fcful.cn/nnews/06662.htm
- http://m.wap.fcful.cn/nnews/19621.htm

## 项目结构

```
weblink-navigator/
├── src/                                 # 核心源代码目录
│   ├── core/                            # 核心业务逻辑模块
│   │   ├── importer.js                  # 批量导入与去重引擎
│   │   ├── extractor.js                 # URL 特征提取器（协议/域名/路径/参数）
│   │   ├── tagger.js                    # 标签管理及层级树维护
│   │   └── snapshot.js                  # 快照生成与回滚控制器
│   ├── server/                          # HTTP 服务与路由层
│   │   ├── app.js                       # Express 应用主入口
│   │   ├── routes/                      # RESTful API 路由定义
│   │   │   ├── links.js                 # 链接 CRUD 与检索端点
│   │   │   ├── tags.js                  # 标签管理端点
│   │   │   └── system.js                # 健康检查与快照操作端点
│   │   └── middleware/                  # 请求日志、跨域、速率限制中间件
│   ├── frontend/                        # 浏览器端管理面板（纯静态）
│   │   ├── index.html                   # 主页面模板
│   │   ├── assets/                      # CSS 样式与 JavaScript 脚本
│   │   └── components/                  # 可复用的 UI 组件（筛选栏、标签树、结果表格）
│   ├── scheduler/                       # 定时任务模块
│   │   ├── health-check.js              # 链接可用性检测任务
│   │   └── cleanup.js                   # 过期快照自动清理任务
│   └── utils/                           # 通用工具函数
│       ├── logger.js                    # 日志输出格式化
│       ├── validator.js                 # URL 格式校验与规范化
│       └── file-helper.js               # 文件读写与目录操作封装
├── data/                                # 数据存储目录（运行时生成）
│   ├── db.json                          # 主数据库文件（JSON 格式）
│   └── imports/                         # 导入历史记录存档
├── .snapshots/                          # 快照存档目录（每次修改自动生成）
│   ├── 2026-08-25T10-30-00.json         # 示例快照文件（时间戳命名）
│   └── 2026-08-25T11-15-22.json
├── config.yml                           # 项目配置文件（端口、标签预设、定时任务开关）
├── package.json                         # npm 依赖清单与脚本定义
├── README.md                            # 项目说明文档（即本文档）
├── LICENSE                              # MIT 许可证文本
└── .gitignore                           # Git 版本忽略规则（排除 data/ 与 .snapshots/）
```

## 贡献指南

1. 复刻主仓库至个人账号，克隆复刻版本到本地，并新建一个功能分支，分支名称需简要描述所修改的功能或修复的问题，例如 feature/support-ipv6-import 或 fix/duplicate-detection-error。

2. 在本地环境完成代码修改后，运行 npm run test 执行现有测试用例，确保未破坏已有功能；若新增功能，请同步添加对应的单元测试文件至 tests/ 目录。

3. 提交变更时使用语义化提交信息格式，即 type(scope): subject，其中 type 可选 feat / fix / docs / style / refactor / test / chore，scope 为影响的模块名称，subject 为简短描述。

4. 推送分支至个人复刻仓库，并通过 GitHub 界面发起 Pull Request 至主仓库的 main 分支，PR 描述中需说明变更目的、实现方式与测试覆盖情况。

5. 项目维护者将在 3 个工作日内进行 Code Review，如有修改意见将在 PR 评论区沟通，所有反馈处理完毕后由维护者合并或关闭 PR。

## 常见问题

**问：导入时提示“URL 格式无效”，但链接在浏览器中可正常访问，如何解决？**

答：本工具默认对 URL 进行严格格式校验，要求必须包含协议头（http:// 或 https://）。部分来源的链接可能缺失协议头，或包含不可见字符（如零宽空格）。请检查原始数据是否包含多余空白字符，或使用 --force 参数跳过校验（仅限命令行导入模式）。若问题持续，可将原始 URL 片段提交至 GitHub Issue 附注，以便我们分析并优化校验规则。

**问：可用性检测模块误报大量链接为“不可访问”，实际手动打开正常，是何原因？**

答：可用性检测基于 HEAD 请求且默认超时时间为 5 秒，部分服务器可能对 HEAD 请求响应缓慢或直接拒绝，但允许 GET 请求。此外，某些 CDN 节点会针对无 User-Agent 头或特定 IP 段的请求返回 403。您可在 config.yml 中调整 timeout 参数至 10 秒，并开启 simulate-browser 选项以伪造常见浏览器 User-Agent。若仍存在误报，建议将该批链接加入检测白名单或关闭定时检测，改为手动抽查。

**问：数据快照占用了大量磁盘空间，能否限制快照数量？**

答：系统默认保留最近 50 次快照，超出部分自动清理。您可在 config.yml 的 snapshot.retainCount 字段中调整此数值（例如设为 20）。若希望按时间而非数量清理，可启用 snapshot.maxAgeDays 字段，设定保留最近 N 天的快照。两种策略可同时生效，系统将取两者交集保留。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
