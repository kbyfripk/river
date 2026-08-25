# WebLink Navigator

WebLink Navigator 是一个面向技术研究者与内容策展人的轻量级外链资源归集与导航系统。该项目以结构化方式管理大规模分散链接，提供分类标签、状态标记与快速检索能力，适用于需要长期维护外部参考资料集合的工作流。目标用户包括开源文档维护者、技术编辑、数据采集工程师以及个人知识管理实践者。

本系统不对链接内容进行爬取或缓存，仅提供用户自定义元数据的附加层，包括手动标注的类别、优先级、有效性状态与备注。所有数据存储于本地 SQLite 数据库，支持导出为 JSON 或 CSV 格式，便于集成至其他管道。项目当前处于积极维护状态，已用于管理超过两万个外部参考链接。

## 功能概览

批量导入与去重：支持从纯文本列表、CSV 或浏览器书签导出文件批量导入链接，自动检测并合并重复条目，保留最早导入时间与最新更新时间。

自定义标签体系：用户可创建无限层级标签，为每个链接分配多个标签，支持基于标签组合的快速筛选与统计。

链接状态监控：内置 HTTP 状态检查器，可定时或手动触发对存储链接的可达性检测，返回状态码与响应时间，标记失效或重定向链接。

全文检索与过滤：基于 SQLite FTS5 扩展提供链接标题、备注与自定义字段的全文搜索，同时支持按标签、状态、导入时间范围等多维度过滤。

数据导入导出：支持单向导出完整链接库为 JSON、CSV 或 HTML 书签格式，便于备份或迁移至其他工具，导入时自动识别字段结构。

命令行交互界面：提供完整的 CLI 工具，包含子命令用于添加、列出、搜索、更新和删除链接，适合服务器端或自动化脚本调用。

本地 Web 仪表板：内置基于 Flask 的轻量级 Web 界面，提供链接列表浏览、标签管理、状态概览与快速编辑功能，默认监听本地 127.0.0.1。

## 应用场景

技术文档外部参考管理：开源项目维护者可使用本系统整理文档中引用的所有外部链接，统一检查有效性，并在版本发布前生成链接状态报告，避免文档中出现死链。

数据采集任务链接暂存：数据工程师在开展定向采集前，可将候选 URL 批量导入系统，按采集主题打标签，标记已处理与待处理状态，协调多台采集节点的工作进度。

个人技术博客参考资料库：技术写作者在撰写文章或教程时，可将调研过程中发现的优质资源统一存入系统，按主题分类，写作时通过标签快速检索相关引用材料。

团队内部知识库外链聚合：企业或开源社区团队可将分散在邮件、聊天记录和文档中的外部参考链接集中归入系统，标注推荐人、所属项目及重要程度，形成团队共享的外链资产。

迁移与备份前链接盘点：在进行网站改版或静态站点生成器迁移时，使用本系统导出所有嵌入链接并检查状态，确保新站点上线前所有外部引用均为有效。

## 快速开始

以下命令序列展示从克隆仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python scripts/init_db.py
python cli.py import --file sample_links.txt
python web.py
```

执行上述命令后，Web 仪表板将在 http://127.0.0.1:5000 启动。首次导入可使用 sample_links.txt 中的测试数据，或通过 `cli.py add --url <URL>` 逐个添加链接。

## 安装要求

| 依赖组件 | 版本要求 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 或 3.12 以获得更好性能 |
| SQLite | 3.35 及以上 | 内嵌数据库，需支持 FTS5 全文搜索扩展 |
| Flask | 2.3.x 或 3.0.x | Web 仪表板依赖，仅在使用 Web 界面时需要 |
| requests | 2.31.x 及以上 | 用于链接状态检查与 HTTP 请求模拟 |
| click | 8.1.x 及以上 | CLI 命令行框架，用于子命令解析与交互提示 |
| pytest | 8.0.x 及以上 | 仅开发与测试环境需要，用于运行单元测试 |

系统不依赖外部数据库服务或缓存中间件，所有数据存储于项目目录下的 `data/links.db` 文件中。建议定期手动备份该文件。操作系统方面，支持 Linux、macOS 与 Windows 10/11，其中 Windows 下建议使用 PowerShell 或 WSL 环境运行 CLI 命令。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何安装、配置并首次导入链接？如何启动 Web 界面？ |
| 命令参考 | docs/cli_commands.md | 每个 CLI 子命令的完整参数列表与使用示例 |
| 标签与分类 | docs/tagging_system.md | 如何创建标签层级？如何批量分配标签？如何按标签统计？ |
| 状态监控 | docs/health_check.md | 状态检查的调度机制、超时设置、重试策略与报告格式 |
| 数据迁移 | docs/export_import.md | 支持的导入导出格式、字段映射规则与编码注意事项 |
| 架构设计 | docs/architecture.md | 数据库表结构、核心类图、扩展点与插件开发接口 |

## 资源列表

- http://m.blog.fcful.cn/bnews/1184.htm
- http://m.blog.fcful.cn/bnews/3867387.htm
- http://m.blog.fcful.cn/bnews/8270060.htm
- http://m.blog.fcful.cn/bnews/652944.htm
- http://m.blog.fcful.cn/bnews/7270447.htm
- http://m.blog.fcful.cn/bnews/5341715.htm
- http://m.blog.fcful.cn/bnews/2109430.htm
- http://m.blog.fcful.cn/bnews/20454.htm
- http://m.blog.fcful.cn/bnews/36840.htm
- http://m.blog.fcful.cn/bnews/89235.htm
- http://m.blog.fcful.cn/bnews/8840174.htm
- http://m.blog.fcful.cn/bnews/23074.htm
- http://m.blog.fcful.cn/bnews/723257.htm
- http://m.blog.fcful.cn/bnews/4769022.htm
- http://m.blog.fcful.cn/bnews/83044.htm
- http://m.blog.fcful.cn/bnews/4210.htm
- http://m.blog.fcful.cn/bnews/2348.htm
- http://m.blog.fcful.cn/bnews/179103.htm
- http://m.blog.fcful.cn/bnews/80769.htm
- http://m.blog.fcful.cn/bnews/607764.htm
- http://m.blog.fcful.cn/bnews/596336.htm
- http://m.blog.fcful.cn/bnews/102027.htm
- http://m.blog.fcful.cn/bnews/9394.htm
- http://m.blog.fcful.cn/bnews/0241558.htm
- http://m.blog.fcful.cn/bnews/6089.htm
- http://m.blog.fcful.cn/bnews/26425.htm
- http://m.blog.fcful.cn/bnews/2488.htm
- http://m.blog.fcful.cn/bnews/13860.htm
- http://m.blog.fcful.cn/bnews/46745.htm
- http://m.blog.fcful.cn/bnews/4744815.htm
- http://m.blog.fcful.cn/bnews/9664561.htm
- http://m.blog.fcful.cn/bnews/77754.htm
- http://m.blog.fcful.cn/bnews/0350494.htm
- http://m.blog.fcful.cn/bnews/286349.htm
- http://m.blog.fcful.cn/bnews/0764999.htm
- http://m.blog.fcful.cn/bnews/827244.htm
- http://m.blog.fcful.cn/bnews/5962.htm
- http://m.blog.fcful.cn/bnews/34595.htm
- http://m.blog.fcful.cn/bnews/7879651.htm
- http://m.blog.fcful.cn/bnews/6789.htm
- http://m.blog.fcful.cn/bnews/331294.htm
- http://m.blog.fcful.cn/bnews/17070.htm
- http://m.blog.fcful.cn/bnews/260086.htm
- http://m.blog.fcful.cn/bnews/36912.htm
- http://m.blog.fcful.cn/bnews/5629.htm
- http://m.blog.fcful.cn/bnews/1624073.htm
- http://m.blog.fcful.cn/bnews/52786.htm
- http://m.blog.fcful.cn/bnews/006683.htm
- http://m.blog.fcful.cn/bnews/9677.htm
- http://m.blog.fcful.cn/bnews/0423.htm
- http://m.blog.fcful.cn/bnews/282444.htm
- http://m.blog.fcful.cn/bnews/106611.htm
- http://m.blog.fcful.cn/bnews/45415.htm
- http://m.blog.fcful.cn/bnews/49915.htm
- http://m.blog.fcful.cn/bnews/7502.htm
- http://m.blog.fcful.cn/bnews/7171906.htm
- http://m.blog.fcful.cn/bnews/274683.htm
- http://m.blog.fcful.cn/bnews/612463.htm
- http://m.blog.fcful.cn/bnews/58664.htm
- http://m.blog.fcful.cn/bnews/4434647.htm
- http://m.blog.fcful.cn/bnews/30745.htm
- http://m.blog.fcful.cn/bnews/97133.htm
- http://m.blog.fcful.cn/bnews/4429.htm
- http://m.blog.fcful.cn/bnews/0160574.htm
- http://m.blog.fcful.cn/bnews/0571414.htm
- http://m.blog.fcful.cn/bnews/3457.htm
- http://m.blog.fcful.cn/bnews/625905.htm
- http://m.blog.fcful.cn/bnews/2310043.htm
- http://m.blog.fcful.cn/bnews/17352.htm
- http://m.blog.fcful.cn/bnews/53587.htm
- http://m.blog.fcful.cn/bnews/582102.htm
- http://m.blog.fcful.cn/bnews/500320.htm
- http://m.blog.fcful.cn/bnews/067766.htm
- http://m.blog.fcful.cn/bnews/504065.htm
- http://m.blog.fcful.cn/bnews/5327.htm
- http://m.blog.fcful.cn/bnews/633981.htm
- http://m.blog.fcful.cn/bnews/88691.htm
- http://m.blog.fcful.cn/bnews/3507648.htm
- http://m.blog.fcful.cn/bnews/74881.htm
- http://m.blog.fcful.cn/bnews/3897747.htm
- http://m.blog.fcful.cn/bnews/8399.htm
- http://m.blog.fcful.cn/bnews/9279138.htm
- http://m.blog.fcful.cn/bnews/3248.htm
- http://m.blog.fcful.cn/bnews/7714.htm
- http://m.blog.fcful.cn/bnews/290905.htm
- http://m.blog.fcful.cn/bnews/470740.htm
- http://m.blog.fcful.cn/bnews/2210451.htm
- http://m.blog.fcful.cn/bnews/4123852.htm
- http://m.blog.fcful.cn/bnews/3549722.htm
- http://m.blog.fcful.cn/bnews/013529.htm
- http://m.blog.fcful.cn/bnews/7284.htm
- http://m.blog.fcful.cn/bnews/71283.htm
- http://m.blog.fcful.cn/bnews/21689.htm
- http://m.blog.fcful.cn/bnews/548967.htm
- http://m.blog.fcful.cn/bnews/3885307.htm
- http://m.blog.fcful.cn/bnews/77529.htm
- http://m.blog.fcful.cn/bnews/134006.htm
- http://m.blog.fcful.cn/bnews/5601.htm
- http://m.blog.fcful.cn/bnews/461426.htm
- http://m.blog.fcful.cn/bnews/44451.htm
- http://m.blog.fcful.cn/bnews/87175.htm
- http://m.blog.fcful.cn/bnews/71154.htm
- http://m.blog.fcful.cn/bnews/250215.htm
- http://m.blog.fcful.cn/bnews/7448280.htm
- http://m.blog.fcful.cn/bnews/2926106.htm
- http://m.blog.fcful.cn/bnews/4390.htm
- http://m.blog.fcful.cn/bnews/7439826.htm
- http://m.blog.fcful.cn/bnews/8791403.htm
- http://m.blog.fcful.cn/bnews/146743.htm
- http://m.blog.fcful.cn/bnews/2801.htm
- http://m.blog.fcful.cn/bnews/079037.htm
- http://m.blog.fcful.cn/bnews/700033.htm
- http://m.blog.fcful.cn/bnews/661513.htm
- http://m.blog.fcful.cn/bnews/35413.htm
- http://m.blog.fcful.cn/bnews/534175.htm
- http://m.blog.fcful.cn/bnews/8786763.htm
- http://m.blog.fcful.cn/bnews/53844.htm
- http://m.blog.fcful.cn/bnews/556447.htm
- http://m.blog.fcful.cn/bnews/5833936.htm
- http://m.blog.fcful.cn/bnews/00324.htm
- http://m.blog.fcful.cn/bnews/008004.htm
- http://m.blog.fcful.cn/bnews/0868480.htm
- http://m.blog.fcful.cn/bnews/745792.htm
- http://m.blog.fcful.cn/bnews/130080.htm
- http://m.blog.fcful.cn/bnews/749911.htm
- http://m.blog.fcful.cn/bnews/8717489.htm
- http://m.blog.fcful.cn/bnews/130341.htm
- http://m.blog.fcful.cn/bnews/49702.htm
- http://m.blog.fcful.cn/bnews/66788.htm
- http://m.blog.fcful.cn/bnews/602618.htm
- http://m.blog.fcful.cn/bnews/67577.htm
- http://m.blog.fcful.cn/bnews/2937.htm
- http://m.blog.fcful.cn/bnews/609693.htm
- http://m.blog.fcful.cn/bnews/3588816.htm
- http://m.blog.fcful.cn/bnews/2453.htm
- http://m.blog.fcful.cn/bnews/667883.htm
- http://m.blog.fcful.cn/bnews/1697946.htm
- http://m.blog.fcful.cn/bnews/3582.htm
- http://m.blog.fcful.cn/bnews/972408.htm
- http://m.blog.fcful.cn/bnews/086463.htm
- http://m.blog.fcful.cn/bnews/9510004.htm
- http://m.blog.fcful.cn/bnews/0976548.htm
- http://m.blog.fcful.cn/bnews/0370077.htm
- http://m.blog.fcful.cn/bnews/430986.htm
- http://m.blog.fcful.cn/bnews/960787.htm
- http://m.blog.fcful.cn/bnews/67074.htm
- http://m.blog.fcful.cn/bnews/989815.htm
- http://m.blog.fcful.cn/bnews/36453.htm
- http://m.blog.fcful.cn/bnews/70538.htm
- http://m.blog.fcful.cn/bnews/418627.htm
- http://m.blog.fcful.cn/bnews/016604.htm
- http://m.blog.fcful.cn/bnews/65224.htm
- http://m.blog.fcful.cn/bnews/59060.htm
- http://m.blog.fcful.cn/bnews/9021.htm
- http://m.blog.fcful.cn/bnews/5806116.htm
- http://m.blog.fcful.cn/bnews/735482.htm
- http://m.blog.fcful.cn/bnews/818778.htm
- http://m.blog.fcful.cn/bnews/5409.htm
- http://m.blog.fcful.cn/bnews/96686.htm
- http://m.blog.fcful.cn/bnews/85342.htm
- http://m.blog.fcful.cn/bnews/168641.htm
- http://m.blog.fcful.cn/bnews/66716.htm
- http://m.blog.fcful.cn/bnews/46558.htm
- http://m.blog.fcful.cn/bnews/8020.htm
- http://m.blog.fcful.cn/bnews/8588906.htm
- http://m.blog.fcful.cn/bnews/681404.htm
- http://m.blog.fcful.cn/bnews/93579.htm
- http://m.blog.fcful.cn/bnews/77434.htm
- http://m.blog.fcful.cn/bnews/9584929.htm
- http://m.blog.fcful.cn/bnews/3269580.htm
- http://m.blog.fcful.cn/bnews/68410.htm
- http://m.blog.fcful.cn/bnews/36844.htm
- http://m.blog.fcful.cn/bnews/940603.htm
- http://m.blog.fcful.cn/bnews/197450.htm
- http://m.blog.fcful.cn/bnews/1570.htm
- http://m.blog.fcful.cn/bnews/7231375.htm
- http://m.blog.fcful.cn/bnews/05428.htm
- http://m.blog.fcful.cn/bnews/561177.htm
- http://m.blog.fcful.cn/bnews/21977.htm
- http://m.blog.fcful.cn/bnews/35084.htm
- http://m.blog.fcful.cn/bnews/6438.htm
- http://m.blog.fcful.cn/bnews/7631483.htm
- http://m.blog.fcful.cn/bnews/81405.htm
- http://m.blog.fcful.cn/bnews/6546.htm
- http://m.blog.fcful.cn/bnews/12252.htm
- http://m.blog.fcful.cn/bnews/832116.htm
- http://m.blog.fcful.cn/bnews/717126.htm
- http://m.blog.fcful.cn/bnews/56426.htm
- http://m.blog.fcful.cn/bnews/21006.htm
- http://m.blog.fcful.cn/bnews/8350.htm
- http://m.blog.fcful.cn/bnews/6648.htm
- http://m.blog.fcful.cn/bnews/428132.htm
- http://m.blog.fcful.cn/bnews/9993.htm
- http://m.blog.fcful.cn/bnews/1229.htm
- http://m.blog.fcful.cn/bnews/0634961.htm
- http://m.blog.fcful.cn/bnews/574922.htm
- http://m.blog.fcful.cn/bnews/73352.htm
- http://m.blog.fcful.cn/bnews/30560.htm
- http://m.blog.fcful.cn/bnews/6651.htm
- http://m.blog.fcful.cn/bnews/699987.htm
- http://m.blog.fcful.cn/bnews/18780.htm
- http://m.blog.fcful.cn/bnews/05242.htm
- http://m.blog.fcful.cn/bnews/58633.htm
- http://m.blog.fcful.cn/bnews/877255.htm
- http://m.blog.fcful.cn/bnews/3358968.htm
- http://m.blog.fcful.cn/bnews/2303.htm
- http://m.blog.fcful.cn/bnews/97922.htm
- http://m.blog.fcful.cn/bnews/598144.htm
- http://m.blog.fcful.cn/bnews/041790.htm
- http://m.blog.fcful.cn/bnews/585192.htm
- http://m.blog.fcful.cn/bnews/19927.htm
- http://m.blog.fcful.cn/bnews/68687.htm
- http://m.blog.fcful.cn/bnews/0790296.htm
- http://m.blog.fcful.cn/bnews/1320.htm
- http://m.blog.fcful.cn/bnews/0320113.htm
- http://m.blog.fcful.cn/bnews/74741.htm
- http://m.blog.fcful.cn/bnews/242016.htm
- http://m.blog.fcful.cn/bnews/873727.htm
- http://m.blog.fcful.cn/bnews/005077.htm
- http://m.blog.fcful.cn/bnews/7788765.htm
- http://m.blog.fcful.cn/bnews/376775.htm
- http://m.blog.fcful.cn/bnews/230439.htm
- http://m.blog.fcful.cn/bnews/547798.htm
- http://m.blog.fcful.cn/bnews/5863.htm
- http://m.blog.fcful.cn/bnews/39377.htm
- http://m.blog.fcful.cn/bnews/335259.htm
- http://m.blog.fcful.cn/bnews/6246.htm
- http://m.blog.fcful.cn/bnews/2300641.htm
- http://m.blog.fcful.cn/bnews/56509.htm
- http://m.blog.fcful.cn/bnews/32779.htm
- http://m.blog.fcful.cn/bnews/8271230.htm
- http://m.blog.fcful.cn/bnews/3406.htm
- http://m.blog.fcful.cn/bnews/8216.htm
- http://m.blog.fcful.cn/bnews/1661.htm
- http://m.blog.fcful.cn/bnews/9580200.htm
- http://m.blog.fcful.cn/bnews/972452.htm
- http://m.blog.fcful.cn/bnews/8424.htm
- http://m.blog.fcful.cn/bnews/1631.htm
- http://m.blog.fcful.cn/bnews/3404646.htm
- http://m.blog.fcful.cn/bnews/126781.htm
- http://m.blog.fcful.cn/bnews/6775.htm
- http://m.blog.fcful.cn/bnews/882112.htm
- http://m.blog.fcful.cn/bnews/5333502.htm
- http://m.blog.fcful.cn/bnews/064065.htm
- http://m.blog.fcful.cn/bnews/6414732.htm
- http://m.blog.fcful.cn/bnews/2406462.htm
- http://m.blog.fcful.cn/bnews/4693.htm
- http://m.blog.fcful.cn/bnews/8525369.htm
- http://m.blog.fcful.cn/bnews/4914.htm
- http://m.blog.fcful.cn/bnews/26716.htm

## 项目结构

```
weblink-navigator/
├── cli.py                      # CLI 入口，注册所有子命令
├── web.py                      # Flask Web 仪表板启动脚本
├── requirements.txt            # 生产环境依赖列表
├── setup.py                    # 项目打包与安装配置
├── pyproject.toml              # 项目元数据与构建工具配置
├── data/                       # 数据存储目录
│   ├── links.db                # 主 SQLite 数据库文件
│   └── imports/                # 导入历史存档与临时文件
├── src/                        # 核心源码包
│   ├── __init__.py
│   ├── database.py             # 数据库连接、表初始化与 CRUD 操作
│   ├── models.py               # 链接、标签、状态记录的数据类定义
│   ├── importer.py             # 批量导入逻辑，支持多种格式解析
│   ├── exporter.py             # 导出为 JSON / CSV / HTML 书签
│   ├── health.py               # HTTP 状态检查器，含超时与重试
│   ├── search.py               # FTS5 全文搜索与过滤构建器
│   └── tags.py                 # 标签层级管理与统计
├── tests/                      # 单元测试与集成测试
│   ├── test_database.py
│   ├── test_importer.py
│   ├── test_health.py
│   └── fixtures/               # 测试用样本数据
├── docs/                       # 文档源文件
│   ├── getting_started.md
│   ├── cli_commands.md
│   ├── tagging_system.md
│   ├── health_check.md
│   ├── export_import.md
│   └── architecture.md
├── templates/                  # Web 仪表板 Jinja2 模板
│   ├── base.html
│   ├── index.html              # 链接列表与分页
│   ├── tags.html               # 标签管理界面
│   └── status.html             # 状态检查结果展示
├── static/                     # CSS 与 JavaScript 静态资源
│   ├── style.css
│   └── dashboard.js
└── scripts/                    # 辅助维护脚本
    ├── init_db.py              # 初始化数据库表结构与 FTS 虚拟表
    └── migrate_v1_to_v2.py     # 版本升级迁移脚本
```

## 贡献指南

提交问题报告：使用 GitHub Issues 提交 bug 或功能请求，请附上详细的复现步骤、系统环境与相关日志输出。对于状态检查失败或导入异常，请提供示例链接或文件片段。

代码贡献流程：Fork 本仓库，创建以 `feature/` 或 `fix/` 为前缀的特性分支。确保所有新增代码均包含对应的单元测试，且通过现有测试套件。提交前运行 `pytest tests/` 确认无回归。

文档改进：欢迎修正文档中的拼写错误、补充命令示例或完善架构说明。文档使用 Markdown 编写，遵循 80 字符换行规则，代码块需标注语言类型。

本地开发环境：建议使用 `pip install -e .[dev]` 安装开发依赖，包含 pytest、black 与 flake8。提交前使用 `black src/ tests/` 格式化代码，并通过 `flake8 src/` 检查风格。

评审与合并：所有合并请求需至少一名维护者批准。重大功能变更或数据库结构改动需在 `docs/architecture.md` 中同步更新设计说明。

## 常见问题

数据库文件损坏或无法打开应如何恢复？
系统在每次写入操作前会自动备份 `links.db` 至 `data/backups/` 目录，按时间戳命名。如遇损坏，可停止服务，将最近的备份文件复制为 `links.db` 后重新启动。若备份文件同样不可用，可使用 `scripts/repair_db.py` 尝试导出可读数据至新数据库。

导入包含大量链接的 CSV 文件时进度缓慢或超时？
对于超过 5000 行的批量导入，建议使用 `cli.py import --chunk-size 500` 参数启用分块提交，每 500 条记录执行一次事务提交，避免单次事务过大导致的锁等待。同时确保 CSV 文件编码为 UTF-8，字段顺序与预期一致。若需跳过重复检查，可添加 `--no-dedupe` 标志以加速导入。

状态检查器报告大量连接超时，但手动访问链接正常？
状态检查器的默认超时设置为 3 秒，对于响应较慢的服务器可能不足。可通过 `cli.py health --timeout 10` 增加超时阈值。同时，检查器默认使用 Python `requests` 库的默认 User-Agent，部分站点可能拦截非浏览器请求，可尝试 `--user-agent "Mozilla/5.0"` 模拟常见浏览器标识。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
