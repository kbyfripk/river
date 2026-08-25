# NewsLink Index

NewsLink Index 是一个面向技术资讯聚合与新闻资源导航的开源工具，专为需要快速检索、分类管理和批量引用新闻链接的开发者、内容运营者及数据分析人员设计。该项目将大量分散的新闻入口链接转化为结构化、可检索的索引体系，便于用户构建自定义新闻流、进行舆情监控或开展内容分析。

本项目并非一个新闻阅读器，而是一个链接资源的组织框架。它提供标准化的元数据描述方案、链接状态检测机制以及灵活的标签分类接口，帮助用户从海量新闻链接中高效定位目标资源。项目本身不存储任何新闻内容，仅提供链接的采集、分类与输出能力。

## 功能概览

**批量链接导入与解析**：支持从纯文本、CSV 或 JSON 文件批量导入新闻链接，自动解析 URL 结构并提取域名、路径、文件扩展名等关键信息。

**自定义标签分类系统**：允许用户为每个链接添加多级标签，支持基于标签的快速筛选与分组统计，便于构建个性化新闻分类目录。

**链接状态健康检测**：内置 HTTP 状态码检查模块，可定期检测链接可用性，标记失效链接并生成检测报告，确保索引库的时效性。

**元数据扩展字段管理**：每条链接支持标题、来源、发布时间、摘要、关键词等扩展字段，用户可根据需要启用或禁用字段显示。

**全文检索与过滤语法**：提供轻量级检索语法，支持按域名、路径关键词、标签组合、状态码范围等多维度条件进行联合查询。

**索引数据导入导出**：支持将索引数据导出为 JSON、CSV、Markdown 表格等格式，也支持从外部数据源导入更新索引内容。

**定时任务与自动化脚本**：内置 cron 风格的定时调度接口，可配置每日自动检测链接状态并生成变更日志。

## 应用场景

**技术内容运营**：内容运营人员可使用 NewsLink Index 管理每日需审核的新闻链接池，通过标签标记“已读”、“待审”、“已发布”等状态，配合检索语法快速筛选当日新增链接，提升内容处理效率。

**舆情监控系统前置处理**：在接入专业舆情分析平台之前，使用本工具对原始新闻链接进行去重、分类和可用性预检，过滤无效链接后输出干净的数据集供下游分析模块使用。

**个人化新闻阅读流构建**：开发者或研究人员可通过标签系统将新闻链接按领域（如人工智能、云计算、开源社区）分类，配合导出功能生成自定义的新闻摘要页面，替代通用 RSS 阅读器的单一时间线模式。

**链接资源库归档与审计**：针对需要长期保存新闻引用记录的场景（如法律合规、学术研究），使用本工具建立带时间戳的链接索引库，定期检测链接状态并记录变更，确保引用资源的可追溯性。

## 快速开始

以下命令演示了从克隆仓库到启动本地索引服务的完整流程。

```bash
git clone https://github.com/yourorg/newslink-index.git
cd newslink-index
pip install -r requirements.txt
python manage.py initdb
python manage.py import --file samples/links.csv
python manage.py serve --port 8080
```

执行上述命令后，本地服务将在 8080 端口启动，可通过浏览器访问管理界面进行链接检索与分类操作。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.11 长期支持版本 |
| SQLite | 3.35 及以上 | 内置索引存储引擎，支持 JSON 扩展函数 |
| requests | 2.28.0 及以上 | 用于链接状态检测的 HTTP 客户端库 |
| click | 8.1.0 及以上 | 命令行交互接口框架 |
| pytest | 7.2.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| nodejs | 18.0 及以上 | 前端管理界面的构建工具链依赖（仅构建前端时需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速安装、导入第一批链接并启动服务？ |
| 使用手册 | docs/usage.md | 标签系统如何工作？检索语法支持哪些操作符？如何配置定时检测？ |
| 开发参考 | docs/development.md | 项目模块划分是怎样的？如何扩展新的链接解析器？如何编写自定义检测插件？ |
| API 文档 | docs/api.md | 管理接口提供了哪些 REST API？请求与响应的数据格式是什么？ |

## 资源列表

- http://m.blog.gqskj.cn/nnews/2533080.htm
- http://m.blog.gqskj.cn/nnews/172054.htm
- http://m.blog.gqskj.cn/nnews/087135.htm
- http://m.blog.gqskj.cn/nnews/8049.htm
- http://m.blog.gqskj.cn/nnews/8373.htm
- http://m.blog.gqskj.cn/nnews/58289.htm
- http://m.blog.gqskj.cn/nnews/22821.htm
- http://m.blog.gqskj.cn/nnews/2682974.htm
- http://m.blog.gqskj.cn/nnews/4057.htm
- http://m.blog.gqskj.cn/nnews/658184.htm
- http://m.blog.gqskj.cn/nnews/6190673.htm
- http://m.blog.gqskj.cn/nnews/19173.htm
- http://m.blog.gqskj.cn/nnews/482498.htm
- http://m.blog.gqskj.cn/nnews/700408.htm
- http://m.blog.gqskj.cn/nnews/09551.htm
- http://m.blog.gqskj.cn/nnews/8146909.htm
- http://m.blog.gqskj.cn/nnews/618438.htm
- http://m.blog.gqskj.cn/nnews/3594.htm
- http://m.blog.gqskj.cn/nnews/3685.htm
- http://m.blog.gqskj.cn/nnews/6574.htm
- http://m.blog.gqskj.cn/nnews/770679.htm
- http://m.blog.gqskj.cn/nnews/5230380.htm
- http://m.blog.gqskj.cn/nnews/04742.htm
- http://m.blog.gqskj.cn/nnews/2952.htm
- http://m.blog.gqskj.cn/nnews/358202.htm
- http://m.blog.gqskj.cn/nnews/7907.htm
- http://m.blog.gqskj.cn/nnews/801752.htm
- http://m.blog.gqskj.cn/nnews/8463.htm
- http://m.blog.gqskj.cn/nnews/76903.htm
- http://m.blog.gqskj.cn/nnews/2947674.htm
- http://m.blog.gqskj.cn/nnews/9572006.htm
- http://m.blog.gqskj.cn/nnews/8589497.htm
- http://m.blog.gqskj.cn/nnews/4768408.htm
- http://m.blog.gqskj.cn/nnews/665081.htm
- http://m.blog.gqskj.cn/nnews/02328.htm
- http://m.blog.gqskj.cn/nnews/528318.htm
- http://m.blog.gqskj.cn/nnews/406733.htm
- http://m.blog.gqskj.cn/nnews/84575.htm
- http://m.blog.gqskj.cn/nnews/483007.htm
- http://m.blog.gqskj.cn/nnews/023757.htm
- http://m.blog.gqskj.cn/nnews/258991.htm
- http://m.blog.gqskj.cn/nnews/37875.htm
- http://m.blog.gqskj.cn/nnews/7145.htm
- http://m.blog.gqskj.cn/nnews/0067718.htm
- http://m.blog.gqskj.cn/nnews/9566710.htm
- http://m.blog.gqskj.cn/nnews/893319.htm
- http://m.blog.gqskj.cn/nnews/7041.htm
- http://m.blog.gqskj.cn/nnews/87023.htm
- http://m.blog.gqskj.cn/nnews/237492.htm
- http://m.blog.gqskj.cn/nnews/469442.htm
- http://m.blog.gqskj.cn/nnews/92215.htm
- http://m.blog.gqskj.cn/nnews/57860.htm
- http://m.blog.gqskj.cn/nnews/0940132.htm
- http://m.blog.gqskj.cn/nnews/69572.htm
- http://m.blog.gqskj.cn/nnews/203191.htm
- http://m.blog.gqskj.cn/nnews/371081.htm
- http://m.blog.gqskj.cn/nnews/611140.htm
- http://m.blog.gqskj.cn/nnews/7418869.htm
- http://m.blog.gqskj.cn/nnews/22812.htm
- http://m.blog.gqskj.cn/nnews/622753.htm
- http://m.blog.gqskj.cn/nnews/27292.htm
- http://m.blog.gqskj.cn/nnews/787322.htm
- http://m.blog.gqskj.cn/nnews/98770.htm
- http://m.blog.gqskj.cn/nnews/961698.htm
- http://m.blog.gqskj.cn/nnews/46242.htm
- http://m.blog.gqskj.cn/nnews/1879.htm
- http://m.blog.gqskj.cn/nnews/02021.htm
- http://m.blog.gqskj.cn/nnews/70477.htm
- http://m.blog.gqskj.cn/nnews/06562.htm
- http://m.blog.gqskj.cn/nnews/8802393.htm
- http://m.blog.gqskj.cn/nnews/141224.htm
- http://m.blog.gqskj.cn/nnews/31520.htm
- http://m.blog.gqskj.cn/nnews/8840454.htm
- http://m.blog.gqskj.cn/nnews/6458.htm
- http://m.blog.gqskj.cn/nnews/54710.htm
- http://m.blog.gqskj.cn/nnews/9654461.htm
- http://m.blog.gqskj.cn/nnews/2334.htm
- http://m.blog.gqskj.cn/nnews/403860.htm
- http://m.blog.gqskj.cn/nnews/8202.htm
- http://m.blog.gqskj.cn/nnews/18537.htm
- http://m.blog.gqskj.cn/nnews/4803.htm
- http://m.blog.gqskj.cn/nnews/54094.htm
- http://m.blog.gqskj.cn/nnews/29327.htm
- http://m.blog.gqskj.cn/nnews/83974.htm
- http://m.blog.gqskj.cn/nnews/4890.htm
- http://m.blog.gqskj.cn/nnews/7112.htm
- http://m.blog.gqskj.cn/nnews/2821.htm
- http://m.blog.gqskj.cn/nnews/96281.htm
- http://m.blog.gqskj.cn/nnews/173947.htm
- http://m.blog.gqskj.cn/nnews/118805.htm
- http://m.blog.gqskj.cn/nnews/805605.htm
- http://m.blog.gqskj.cn/nnews/4264009.htm
- http://m.blog.gqskj.cn/nnews/756131.htm
- http://m.blog.gqskj.cn/nnews/6803.htm
- http://m.blog.gqskj.cn/nnews/604632.htm
- http://m.blog.gqskj.cn/nnews/374814.htm
- http://m.blog.gqskj.cn/nnews/230062.htm
- http://m.blog.gqskj.cn/nnews/2577686.htm
- http://m.blog.gqskj.cn/nnews/3674410.htm
- http://m.blog.gqskj.cn/nnews/42708.htm
- http://m.blog.gqskj.cn/nnews/321158.htm
- http://m.blog.gqskj.cn/nnews/198078.htm
- http://m.blog.gqskj.cn/nnews/33187.htm
- http://m.blog.gqskj.cn/nnews/79962.htm
- http://m.blog.gqskj.cn/nnews/8260491.htm
- http://m.blog.gqskj.cn/nnews/30272.htm
- http://m.blog.gqskj.cn/nnews/310811.htm
- http://m.blog.gqskj.cn/nnews/081198.htm
- http://m.blog.gqskj.cn/nnews/6709979.htm
- http://m.blog.gqskj.cn/nnews/4934082.htm
- http://m.blog.gqskj.cn/nnews/58628.htm
- http://m.blog.gqskj.cn/nnews/0849.htm
- http://m.blog.gqskj.cn/nnews/4971.htm
- http://m.blog.gqskj.cn/nnews/4528682.htm
- http://m.blog.gqskj.cn/nnews/345805.htm
- http://m.blog.gqskj.cn/nnews/29601.htm
- http://m.blog.gqskj.cn/nnews/72041.htm
- http://m.blog.gqskj.cn/nnews/9871.htm
- http://m.blog.gqskj.cn/nnews/568630.htm
- http://m.blog.gqskj.cn/nnews/1590086.htm
- http://m.blog.gqskj.cn/nnews/445048.htm
- http://m.blog.gqskj.cn/nnews/055141.htm
- http://m.blog.gqskj.cn/nnews/61498.htm
- http://m.blog.gqskj.cn/nnews/03493.htm
- http://m.blog.gqskj.cn/nnews/1274796.htm
- http://m.blog.gqskj.cn/nnews/37852.htm
- http://m.blog.gqskj.cn/nnews/778117.htm
- http://m.blog.gqskj.cn/nnews/695122.htm
- http://m.blog.gqskj.cn/nnews/721210.htm
- http://m.blog.gqskj.cn/nnews/8894062.htm
- http://m.blog.gqskj.cn/nnews/5574.htm
- http://m.blog.gqskj.cn/nnews/959492.htm
- http://m.blog.gqskj.cn/nnews/00506.htm
- http://m.blog.gqskj.cn/nnews/740400.htm
- http://m.blog.gqskj.cn/nnews/9758.htm
- http://m.blog.gqskj.cn/nnews/478753.htm
- http://m.blog.gqskj.cn/nnews/2812.htm
- http://m.blog.gqskj.cn/nnews/1114350.htm
- http://m.blog.gqskj.cn/nnews/729763.htm
- http://m.blog.gqskj.cn/nnews/657485.htm
- http://m.blog.gqskj.cn/nnews/475405.htm
- http://m.blog.gqskj.cn/nnews/7689776.htm
- http://m.blog.gqskj.cn/nnews/463574.htm
- http://m.blog.gqskj.cn/nnews/19065.htm
- http://m.blog.gqskj.cn/nnews/843692.htm
- http://m.blog.gqskj.cn/nnews/28564.htm
- http://m.blog.gqskj.cn/nnews/4360414.htm
- http://m.blog.gqskj.cn/nnews/7961368.htm
- http://m.blog.gqskj.cn/nnews/8093.htm
- http://m.blog.gqskj.cn/nnews/37768.htm
- http://m.blog.gqskj.cn/nnews/263524.htm
- http://m.blog.gqskj.cn/nnews/937896.htm
- http://m.blog.gqskj.cn/nnews/127094.htm
- http://m.blog.gqskj.cn/nnews/3611153.htm
- http://m.blog.gqskj.cn/nnews/1320.htm
- http://m.blog.gqskj.cn/nnews/2867575.htm
- http://m.blog.gqskj.cn/nnews/553018.htm
- http://m.blog.gqskj.cn/nnews/1679605.htm
- http://m.blog.gqskj.cn/nnews/9899591.htm
- http://m.blog.gqskj.cn/nnews/9480.htm
- http://m.blog.gqskj.cn/nnews/1951.htm
- http://m.blog.gqskj.cn/nnews/207702.htm
- http://m.blog.gqskj.cn/nnews/5182399.htm
- http://m.blog.gqskj.cn/nnews/8402011.htm
- http://m.blog.gqskj.cn/nnews/810834.htm
- http://m.blog.gqskj.cn/nnews/8627726.htm
- http://m.blog.gqskj.cn/nnews/157468.htm
- http://m.blog.gqskj.cn/nnews/00151.htm
- http://m.blog.gqskj.cn/nnews/2540.htm
- http://m.blog.gqskj.cn/nnews/3580.htm
- http://m.blog.gqskj.cn/nnews/73119.htm
- http://m.blog.gqskj.cn/nnews/2356655.htm
- http://m.blog.gqskj.cn/nnews/0840.htm
- http://m.blog.gqskj.cn/nnews/7939660.htm
- http://m.blog.gqskj.cn/nnews/33941.htm
- http://m.blog.gqskj.cn/nnews/818526.htm
- http://m.blog.gqskj.cn/nnews/7729147.htm
- http://m.blog.gqskj.cn/nnews/9769759.htm
- http://m.blog.gqskj.cn/nnews/0260.htm
- http://m.blog.gqskj.cn/nnews/39313.htm
- http://m.blog.gqskj.cn/nnews/9897770.htm
- http://m.blog.gqskj.cn/nnews/224116.htm
- http://m.blog.gqskj.cn/nnews/290012.htm
- http://m.blog.gqskj.cn/nnews/9219.htm
- http://m.blog.gqskj.cn/nnews/7982396.htm
- http://m.blog.gqskj.cn/nnews/0722.htm
- http://m.blog.gqskj.cn/nnews/9308.htm
- http://m.blog.gqskj.cn/nnews/149714.htm
- http://m.blog.gqskj.cn/nnews/507811.htm
- http://m.blog.gqskj.cn/nnews/3805.htm
- http://m.blog.gqskj.cn/nnews/2463.htm
- http://m.blog.gqskj.cn/nnews/3438721.htm
- http://m.blog.gqskj.cn/nnews/7951.htm
- http://m.blog.gqskj.cn/nnews/4266017.htm
- http://m.blog.gqskj.cn/nnews/4004409.htm
- http://m.blog.gqskj.cn/nnews/68949.htm
- http://m.blog.gqskj.cn/nnews/9666303.htm
- http://m.blog.gqskj.cn/nnews/22732.htm
- http://m.blog.gqskj.cn/nnews/2339892.htm
- http://m.blog.gqskj.cn/nnews/300409.htm
- http://m.blog.gqskj.cn/nnews/7822565.htm
- http://m.blog.gqskj.cn/nnews/45789.htm
- http://m.blog.gqskj.cn/nnews/2132255.htm
- http://m.blog.gqskj.cn/nnews/702891.htm
- http://m.blog.gqskj.cn/nnews/9130.htm
- http://m.blog.gqskj.cn/nnews/714588.htm
- http://m.blog.gqskj.cn/nnews/6326028.htm
- http://m.blog.gqskj.cn/nnews/8316223.htm
- http://m.blog.gqskj.cn/nnews/6234428.htm
- http://m.blog.gqskj.cn/nnews/79906.htm
- http://m.blog.gqskj.cn/nnews/9255081.htm
- http://m.blog.gqskj.cn/nnews/9295141.htm
- http://m.blog.gqskj.cn/nnews/6957400.htm
- http://m.blog.gqskj.cn/nnews/22654.htm
- http://m.blog.gqskj.cn/nnews/323691.htm
- http://m.blog.gqskj.cn/nnews/1859050.htm
- http://m.blog.gqskj.cn/nnews/68471.htm
- http://m.blog.gqskj.cn/nnews/33012.htm
- http://m.blog.gqskj.cn/nnews/9283420.htm
- http://m.blog.gqskj.cn/nnews/2392515.htm
- http://m.blog.gqskj.cn/nnews/4215198.htm
- http://m.blog.gqskj.cn/nnews/6710.htm
- http://m.blog.gqskj.cn/nnews/987362.htm
- http://m.blog.gqskj.cn/nnews/276167.htm
- http://m.blog.gqskj.cn/nnews/4429.htm
- http://m.blog.gqskj.cn/nnews/9767.htm
- http://m.blog.gqskj.cn/nnews/799164.htm
- http://m.blog.gqskj.cn/nnews/4882045.htm
- http://m.blog.gqskj.cn/nnews/434703.htm
- http://m.blog.gqskj.cn/nnews/21252.htm
- http://m.blog.gqskj.cn/nnews/61979.htm
- http://m.blog.gqskj.cn/nnews/293555.htm
- http://m.blog.gqskj.cn/nnews/535436.htm
- http://m.blog.gqskj.cn/nnews/022538.htm
- http://m.blog.gqskj.cn/nnews/7887.htm
- http://m.blog.gqskj.cn/nnews/8607.htm
- http://m.blog.gqskj.cn/nnews/047441.htm
- http://m.blog.gqskj.cn/nnews/236834.htm
- http://m.blog.gqskj.cn/nnews/53027.htm
- http://m.blog.gqskj.cn/nnews/75592.htm
- http://m.blog.gqskj.cn/nnews/22296.htm
- http://m.blog.gqskj.cn/nnews/33133.htm
- http://m.blog.gqskj.cn/nnews/91231.htm
- http://m.blog.gqskj.cn/nnews/75441.htm
- http://m.blog.gqskj.cn/nnews/6517.htm
- http://m.blog.gqskj.cn/nnews/487222.htm
- http://m.blog.gqskj.cn/nnews/9153.htm
- http://m.blog.gqskj.cn/nnews/53720.htm
- http://m.blog.gqskj.cn/nnews/0025.htm
- http://m.blog.gqskj.cn/nnews/43815.htm

## 项目结构

```
newslink-index/
├── cmd/                                # 命令行入口模块
│   ├── cli.py                          # 主命令分发器，注册所有子命令
│   └── commands/                       # 各子命令实现
│       ├── import.py                   # 链接导入命令实现
│       ├── export.py                   # 链接导出命令实现
│       ├── check.py                    # 链接状态检测命令实现
│       └── serve.py                    # 本地服务启动命令实现
├── core/                               # 核心业务逻辑模块
│   ├── indexer.py                      # 索引引擎，管理链接的增删改查
│   ├── parser.py                       # URL 解析器，提取域名、路径、参数
│   ├── tagger.py                       # 标签管理系统，处理标签的增删与关联
│   ├── checker.py                      # 链接状态检测器，并发检测 HTTP 状态
│   └── serializer.py                   # 序列化器，支持多种数据格式的导入导出
├── storage/                            # 数据持久化层
│   ├── database.py                     # SQLite 数据库连接与基础 CRUD 操作
│   ├── models.py                       # 数据模型定义（链接、标签、检测记录）
│   └── migrations/                     # 数据库迁移脚本
│       ├── 001_initial_schema.sql      # 初始化表结构
│       └── 002_add_check_history.sql   # 增加检测历史表
├── web/                                # Web 管理界面模块
│   ├── static/                         # 静态资源文件（CSS、JavaScript）
│   ├── templates/                      # Jinja2 模板文件
│   │   ├── index.html                  # 主页面模板
│   │   ├── search.html                 # 搜索结果页模板
│   │   └── detail.html                 # 链接详情页模板
│   └── routes.py                       # Flask 路由定义与请求处理
├── scripts/                            # 辅助脚本与工具
│   ├── cron_check.py                   # 定时检测脚本，可由 crontab 调用
│   ├── batch_import.py                 # 批量导入优化脚本
│   └── export_report.py                # 生成检测报告脚本
├── tests/                              # 测试套件
│   ├── unit/                           # 单元测试
│   │   ├── test_parser.py              # 解析器单元测试
│   │   └── test_tagger.py              # 标签系统单元测试
│   └── integration/                    # 集成测试
│       ├── test_import_flow.py         # 导入流程集成测试
│       └── test_check_flow.py          # 检测流程集成测试
├── samples/                            # 示例数据文件
│   ├── links.csv                       # 示例链接导入文件
│   └── config.yaml                     # 示例配置文件
├── docs/                               # 项目文档目录
│   ├── quickstart.md                   # 快速入门指南
│   ├── usage.md                        # 详细使用手册
│   ├── development.md                  # 开发与扩展指南
│   └── api.md                          # REST API 参考文档
├── requirements.txt                    # Python 依赖清单
├── setup.py                            # 项目安装脚本
├── Makefile                            # 常用命令快捷方式
└── README.md                           # 项目概述与入口文档
```

## 贡献指南

**问题报告与功能建议**：请先在 GitHub Issues 中搜索是否已有类似问题或建议。若未找到，请提交新的 Issue，使用提供的模板详细描述问题复现步骤或功能需求描述。

**代码贡献流程**：Fork 本仓库至个人账户，在 dev 分支上创建特性分支进行开发。提交代码前请确保所有单元测试通过，并为新增功能编写对应的测试用例。完成后向主仓库的 dev 分支提交 Pull Request。

**文档改进**：欢迎对文档进行修订与补充。文档使用 Markdown 格式编写，修改后请确保渲染效果正确。涉及 API 文档的变更需同步更新对应的代码注释。

**链接资源扩展**：若您有优质的新闻链接资源希望纳入示例数据集，请按照 samples/links.csv 的格式整理后提交 Pull Request，或通过 Issue 提供资源列表。

**本地开发环境设置**：建议使用虚拟环境进行开发。运行 make dev 命令可自动创建虚拟环境并安装开发依赖。运行 make test 可执行完整测试套件。

## 常见问题

**问：导入链接时提示格式错误，应该如何处理？**

答：请检查导入文件是否符合预期的格式规范。对于 CSV 格式，必须包含 title 和 url 两列，且 url 列的值需为完整的 HTTP/HTTPS 链接。对于 JSON 格式，应确保为对象数组，每个对象至少包含 title 和 url 字段。您可以使用 samples/links.csv 作为格式参考模板。

**问：链接状态检测任务执行时间过长，能否优化？**

答：链接检测模块默认使用多线程并发检测，并发数量可通过配置文件中的 checker.threads 参数调整。建议根据网络环境和机器性能将并发数设置在 10 至 50 之间。同时，检测超时时间可通过 checker.timeout 参数设置，默认 10 秒，可根据目标站点的响应速度适当调整。

**问：如何将索引数据迁移至其他数据库系统？**

答：当前版本内置的存储引擎为 SQLite。若需迁移至 PostgreSQL 或 MySQL，您可以通过修改 storage/database.py 中的数据库连接字符串切换驱动，并执行对应的迁移脚本。项目暂不提供官方迁移工具，但您可以使用导出功能将数据导出为 JSON 或 CSV 格式后手动导入目标数据库。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:46
