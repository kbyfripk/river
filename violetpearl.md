# WebLink Navigator

WebLink Navigator 是一个面向技术研究者与信息分析人员的结构化外链资源聚合与导航系统。该项目不提供内容存储或代理服务，专注于对分散于互联网各处的信息页面进行编目、分类与快速检索，帮助用户从海量外链中定位高价值技术文档、行业动态与数据源。

项目定位为轻量级、可自托管的链接枢纽站，适用于个人知识库构建、团队技术周报素材采集、以及自动化信息采集管道的前端索引层。目标用户包括开发者、数据分析师、运维工程师与技术写作人员。

## 功能概览

批量链接导入与自动规范化解析 系统支持从文本文件、CSV 或指定目录批量导入原始链接，自动识别协议头与域名格式，对不符合规范的条目输出警告日志。

多维度标签分类引擎 内置基于关键词匹配与正则表达式的自动打标模块，可将链接按技术领域、内容类型、来源站点等维度标记，支持用户自定义标签规则。

链接可用性健康检查 集成异步HTTP探测任务，定时检测每个外链的状态码、响应时间与重定向链，生成可用性报告，标记失效或超时链接。

全文元数据提取 对目标页面进行非侵入式元数据抓取，获取标题、描述、发布时间、正文摘要等关键字段，用于生成导航卡片与检索索引。

自定义视图与筛选面板 提供按标签、状态码、更新时间、域名等条件的多级筛选界面，支持保存常用筛选组合为视图模板，便于重复使用。

RSS与JSON订阅输出 支持将任意筛选视图生成为RSS feed或JSON接口，供外部阅读器或自动化脚本调用，实现导航数据的二次分发。

操作审计日志 记录所有链接的增删改查操作、健康检查结果变更与用户登录行为，支持导出日志文件用于合规审查。

## 应用场景

技术团队内部知识库索引构建 技术团队在维护内部文档系统时，可将日常查阅的官方文档链接、社区讨论帖、技术博客等统一纳入WebLink Navigator管理，通过标签区分前端、后端、运维等方向，成员按需订阅对应视图，减少重复检索时间。

自动化信息采集管道的预处理环节 在数据采集流程中，WebLink Navigator可作为种子链接管理模块，由健康检查功能定期验证种子有效性，剔除失效链接后再交由下游爬虫处理，提升采集管道稳定性。

技术周报素材快速汇编 技术编辑或社区运营人员将一周内关注的资讯链接导入系统，利用元数据提取生成统一格式的条目摘要，通过筛选面板快速过滤出高优先级内容，直接导出为周报草稿。

个人技术阅读流统一入口 开发者可将分散在浏览器书签、笔记软件、即时通讯收藏夹中的技术链接集中迁移至WebLink Navigator，按学习计划自定义视图，每日通过RSS订阅接收更新提醒，构建专注的技术阅读流。

## 快速开始

以下指令适用于Linux/macOS环境，Windows用户可使用WSL或Git Bash执行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装Python依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化SQLite数据库与默认配置
python manage.py initdb
python manage.py migrate

# 启动开发服务器（默认监听127.0.0.1:8000）
python manage.py runserver
```

访问 http://127.0.0.1:8000 进入导航面板首页，默认管理员账号为 admin 密码为 admin123，首次登录后请立即修改密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，低于3.9版本将导致类型注解解析错误 |
| SQLite | 3.35.0 或更高 | 内置于Python标准库，无需额外安装，用于存储链接元数据与标签 |
| requests | 2.31.0 或更高 | HTTP健康检查与元数据提取的底层库，需支持SSL验证 |
| beautifulsoup4 | 4.12.0 或更高 | HTML解析与元数据提取，依赖lxml或html5lib作为解析后端 |
| lxml | 4.9.0 或更高 | 高性能XML/HTML解析器，beautifulsoup4的推荐后端 |
| redis | 6.0 或更高 | 可选依赖，用于分布式部署时的缓存与任务队列，单机模式可不安装 |
| uWSGI | 2.0.21 或更高 | 生产环境部署所需，开发环境可使用内置runserver替代 |
| nodejs | 18.0 或更高 | 仅当启用前端资产编译时需要，用于处理CSS与JavaScript打包 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何5分钟内完成首次部署并导入第一批链接；如何理解仪表盘的核心指标 |
| 操作手册 | docs/user-guide/ | 如何创建标签规则、如何配置健康检查策略、如何导出RSS订阅源 |
| 管理指南 | docs/admin-guide/ | 如何备份数据库、如何迁移至生产服务器、如何配置反向代理 |
| 开发者文档 | docs/developer/ | 如何扩展元数据提取器、如何新增筛选字段、如何编写自定义视图插件 |

完整文档索引请参阅 docs/README.md，API接口参考文档位于 docs/api/ 目录下，以OpenAPI 3.0格式提供。

## 资源列表

- http://m.3g.fcful.cn/snews/7372.htm
- http://m.3g.fcful.cn/snews/21334.htm
- http://m.3g.fcful.cn/snews/85300.htm
- http://m.3g.fcful.cn/snews/729781.htm
- http://m.3g.fcful.cn/snews/48683.htm
- http://m.3g.fcful.cn/snews/339651.htm
- http://m.3g.fcful.cn/snews/1384.htm
- http://m.3g.fcful.cn/snews/07653.htm
- http://m.3g.fcful.cn/snews/7331.htm
- http://m.3g.fcful.cn/snews/929941.htm
- http://m.3g.fcful.cn/snews/3424.htm
- http://m.3g.fcful.cn/snews/7401.htm
- http://m.3g.fcful.cn/snews/1674456.htm
- http://m.3g.fcful.cn/snews/1649.htm
- http://m.3g.fcful.cn/snews/79996.htm
- http://m.3g.fcful.cn/snews/98165.htm
- http://m.3g.fcful.cn/snews/86394.htm
- http://m.3g.fcful.cn/snews/236652.htm
- http://m.3g.fcful.cn/snews/7832.htm
- http://m.3g.fcful.cn/snews/567353.htm
- http://m.3g.fcful.cn/snews/1792.htm
- http://m.3g.fcful.cn/snews/98384.htm
- http://m.3g.fcful.cn/snews/19584.htm
- http://m.3g.fcful.cn/snews/98543.htm
- http://m.3g.fcful.cn/snews/9692706.htm
- http://m.3g.fcful.cn/snews/0040546.htm
- http://m.3g.fcful.cn/snews/277410.htm
- http://m.3g.fcful.cn/snews/573112.htm
- http://m.3g.fcful.cn/snews/5221.htm
- http://m.3g.fcful.cn/snews/076984.htm
- http://m.3g.fcful.cn/snews/97332.htm
- http://m.3g.fcful.cn/snews/60554.htm
- http://m.3g.fcful.cn/snews/65424.htm
- http://m.3g.fcful.cn/snews/7433435.htm
- http://m.3g.fcful.cn/snews/7641.htm
- http://m.3g.fcful.cn/snews/9823303.htm
- http://m.3g.fcful.cn/snews/9079900.htm
- http://m.3g.fcful.cn/snews/54388.htm
- http://m.3g.fcful.cn/snews/70509.htm
- http://m.3g.fcful.cn/snews/568465.htm
- http://m.3g.fcful.cn/snews/36229.htm
- http://m.3g.fcful.cn/snews/49376.htm
- http://m.3g.fcful.cn/snews/9758520.htm
- http://m.3g.fcful.cn/snews/6563741.htm
- http://m.3g.fcful.cn/snews/08628.htm
- http://m.3g.fcful.cn/snews/51270.htm
- http://m.3g.fcful.cn/snews/84914.htm
- http://m.3g.fcful.cn/snews/6916743.htm
- http://m.3g.fcful.cn/snews/2084182.htm
- http://m.3g.fcful.cn/snews/534647.htm
- http://m.3g.fcful.cn/snews/9906106.htm
- http://m.3g.fcful.cn/snews/530708.htm
- http://m.3g.fcful.cn/snews/33651.htm
- http://m.3g.fcful.cn/snews/4919664.htm
- http://m.3g.fcful.cn/snews/27071.htm
- http://m.3g.fcful.cn/snews/4655.htm
- http://m.3g.fcful.cn/snews/87546.htm
- http://m.3g.fcful.cn/snews/717423.htm
- http://m.3g.fcful.cn/snews/889051.htm
- http://m.3g.fcful.cn/snews/38987.htm
- http://m.3g.fcful.cn/snews/430469.htm
- http://m.3g.fcful.cn/snews/692778.htm
- http://m.3g.fcful.cn/snews/901826.htm
- http://m.3g.fcful.cn/snews/41137.htm
- http://m.3g.fcful.cn/snews/875784.htm
- http://m.3g.fcful.cn/snews/632538.htm
- http://m.3g.fcful.cn/snews/2926001.htm
- http://m.3g.fcful.cn/snews/6591.htm
- http://m.3g.fcful.cn/snews/1591155.htm
- http://m.3g.fcful.cn/snews/99051.htm
- http://m.3g.fcful.cn/snews/76442.htm
- http://m.3g.fcful.cn/snews/42888.htm
- http://m.3g.fcful.cn/snews/4923338.htm
- http://m.3g.fcful.cn/snews/5860.htm
- http://m.3g.fcful.cn/snews/882138.htm
- http://m.3g.fcful.cn/snews/262779.htm
- http://m.3g.fcful.cn/snews/18424.htm
- http://m.3g.fcful.cn/snews/596755.htm
- http://m.3g.fcful.cn/snews/1695903.htm
- http://m.3g.fcful.cn/snews/152495.htm
- http://m.3g.fcful.cn/snews/550360.htm
- http://m.3g.fcful.cn/snews/69590.htm
- http://m.3g.fcful.cn/snews/5955770.htm
- http://m.3g.fcful.cn/snews/22326.htm
- http://m.3g.fcful.cn/snews/61517.htm
- http://m.3g.fcful.cn/snews/568383.htm
- http://m.3g.fcful.cn/snews/786743.htm
- http://m.3g.fcful.cn/snews/25992.htm
- http://m.3g.fcful.cn/snews/28068.htm
- http://m.3g.fcful.cn/snews/7667087.htm
- http://m.3g.fcful.cn/snews/9981410.htm
- http://m.3g.fcful.cn/snews/82714.htm
- http://m.3g.fcful.cn/snews/8595.htm
- http://m.3g.fcful.cn/snews/6677514.htm
- http://m.3g.fcful.cn/snews/6681412.htm
- http://m.3g.fcful.cn/snews/30639.htm
- http://m.3g.fcful.cn/snews/5467.htm
- http://m.3g.fcful.cn/snews/292940.htm
- http://m.3g.fcful.cn/snews/63579.htm
- http://m.3g.fcful.cn/snews/5665527.htm
- http://m.3g.fcful.cn/snews/75282.htm
- http://m.3g.fcful.cn/snews/20269.htm
- http://m.3g.fcful.cn/snews/4630136.htm
- http://m.3g.fcful.cn/snews/5229.htm
- http://m.3g.fcful.cn/snews/9600668.htm
- http://m.3g.fcful.cn/snews/4788842.htm
- http://m.3g.fcful.cn/snews/41112.htm
- http://m.3g.fcful.cn/snews/99522.htm
- http://m.3g.fcful.cn/snews/979361.htm
- http://m.3g.fcful.cn/snews/112646.htm
- http://m.3g.fcful.cn/snews/638985.htm
- http://m.3g.fcful.cn/snews/93762.htm
- http://m.3g.fcful.cn/snews/0354.htm
- http://m.3g.fcful.cn/snews/1239883.htm
- http://m.3g.fcful.cn/snews/4062562.htm
- http://m.3g.fcful.cn/snews/4631.htm
- http://m.3g.fcful.cn/snews/956307.htm
- http://m.3g.fcful.cn/snews/13108.htm
- http://m.3g.fcful.cn/snews/015829.htm
- http://m.3g.fcful.cn/snews/7635.htm
- http://m.3g.fcful.cn/snews/4920422.htm
- http://m.3g.fcful.cn/snews/9511260.htm
- http://m.3g.fcful.cn/snews/8810773.htm
- http://m.3g.fcful.cn/snews/715968.htm
- http://m.3g.fcful.cn/snews/05439.htm
- http://m.3g.fcful.cn/snews/0292.htm
- http://m.3g.fcful.cn/snews/2551.htm
- http://m.3g.fcful.cn/snews/65553.htm
- http://m.3g.fcful.cn/snews/459486.htm
- http://m.3g.fcful.cn/snews/814296.htm
- http://m.3g.fcful.cn/snews/2072.htm
- http://m.3g.fcful.cn/snews/84235.htm
- http://m.3g.fcful.cn/snews/93103.htm
- http://m.3g.fcful.cn/snews/891441.htm
- http://m.3g.fcful.cn/snews/930485.htm
- http://m.3g.fcful.cn/snews/094147.htm
- http://m.3g.fcful.cn/snews/01704.htm
- http://m.3g.fcful.cn/snews/778542.htm
- http://m.3g.fcful.cn/snews/056492.htm
- http://m.3g.fcful.cn/snews/0241234.htm
- http://m.3g.fcful.cn/snews/6527.htm
- http://m.3g.fcful.cn/snews/727608.htm
- http://m.3g.fcful.cn/snews/272461.htm
- http://m.3g.fcful.cn/snews/6123.htm
- http://m.3g.fcful.cn/snews/62227.htm
- http://m.3g.fcful.cn/snews/3221.htm
- http://m.3g.fcful.cn/snews/336948.htm
- http://m.3g.fcful.cn/snews/6909106.htm
- http://m.3g.fcful.cn/snews/926531.htm
- http://m.3g.fcful.cn/snews/489330.htm
- http://m.3g.fcful.cn/snews/2220.htm
- http://m.3g.fcful.cn/snews/8099487.htm
- http://m.3g.fcful.cn/snews/04514.htm
- http://m.3g.fcful.cn/snews/343677.htm
- http://m.3g.fcful.cn/snews/1476.htm
- http://m.3g.fcful.cn/snews/43626.htm
- http://m.3g.fcful.cn/snews/66383.htm
- http://m.3g.fcful.cn/snews/734350.htm
- http://m.3g.fcful.cn/snews/4343352.htm
- http://m.3g.fcful.cn/snews/3995637.htm
- http://m.3g.fcful.cn/snews/87745.htm
- http://m.3g.fcful.cn/snews/6224902.htm
- http://m.3g.fcful.cn/snews/03965.htm
- http://m.3g.fcful.cn/snews/0285.htm
- http://m.3g.fcful.cn/snews/317047.htm
- http://m.3g.fcful.cn/snews/0559.htm
- http://m.3g.fcful.cn/snews/0626802.htm
- http://m.3g.fcful.cn/snews/4206461.htm
- http://m.3g.fcful.cn/snews/333339.htm
- http://m.3g.fcful.cn/snews/74219.htm
- http://m.3g.fcful.cn/snews/2758245.htm
- http://m.3g.fcful.cn/snews/68858.htm
- http://m.3g.fcful.cn/snews/2247.htm
- http://m.3g.fcful.cn/snews/003784.htm
- http://m.3g.fcful.cn/snews/440583.htm
- http://m.3g.fcful.cn/snews/1404853.htm
- http://m.3g.fcful.cn/snews/3932251.htm
- http://m.3g.fcful.cn/snews/5487.htm
- http://m.3g.fcful.cn/snews/876266.htm
- http://m.3g.fcful.cn/snews/112775.htm
- http://m.3g.fcful.cn/snews/0268214.htm
- http://m.3g.fcful.cn/snews/56738.htm
- http://m.3g.fcful.cn/snews/1125.htm
- http://m.3g.fcful.cn/snews/2310845.htm
- http://m.3g.fcful.cn/snews/9184.htm
- http://m.3g.fcful.cn/snews/061255.htm
- http://m.3g.fcful.cn/snews/08848.htm
- http://m.3g.fcful.cn/snews/1408759.htm
- http://m.3g.fcful.cn/snews/8799.htm
- http://m.3g.fcful.cn/snews/11283.htm
- http://m.3g.fcful.cn/snews/52320.htm
- http://m.3g.fcful.cn/snews/9252.htm
- http://m.3g.fcful.cn/snews/5101694.htm
- http://m.3g.fcful.cn/snews/721447.htm
- http://m.3g.fcful.cn/snews/4575129.htm
- http://m.3g.fcful.cn/snews/35673.htm
- http://m.3g.fcful.cn/snews/270898.htm
- http://m.3g.fcful.cn/snews/5020.htm
- http://m.3g.fcful.cn/snews/0013101.htm
- http://m.3g.fcful.cn/snews/4902499.htm
- http://m.3g.fcful.cn/snews/070464.htm
- http://m.3g.fcful.cn/snews/2965521.htm
- http://m.3g.fcful.cn/snews/29220.htm
- http://m.3g.fcful.cn/snews/6847360.htm
- http://m.3g.fcful.cn/snews/453232.htm
- http://m.3g.fcful.cn/snews/6895.htm
- http://m.3g.fcful.cn/snews/8621.htm
- http://m.3g.fcful.cn/snews/6887.htm
- http://m.3g.fcful.cn/snews/13356.htm
- http://m.3g.fcful.cn/snews/71929.htm
- http://m.3g.fcful.cn/snews/011088.htm
- http://m.3g.fcful.cn/snews/44462.htm
- http://m.3g.fcful.cn/snews/15086.htm
- http://m.3g.fcful.cn/snews/996866.htm
- http://m.3g.fcful.cn/snews/721487.htm
- http://m.3g.fcful.cn/snews/93786.htm
- http://m.3g.fcful.cn/snews/6833250.htm
- http://m.3g.fcful.cn/snews/4572013.htm
- http://m.3g.fcful.cn/snews/2285.htm
- http://m.3g.fcful.cn/snews/79193.htm
- http://m.3g.fcful.cn/snews/2596.htm
- http://m.3g.fcful.cn/snews/76129.htm
- http://m.3g.fcful.cn/snews/9703968.htm
- http://m.3g.fcful.cn/snews/84258.htm
- http://m.3g.fcful.cn/snews/5365490.htm
- http://m.3g.fcful.cn/snews/3727269.htm
- http://m.3g.fcful.cn/snews/7651.htm
- http://m.3g.fcful.cn/snews/855996.htm
- http://m.3g.fcful.cn/snews/885195.htm
- http://m.3g.fcful.cn/snews/1649015.htm
- http://m.3g.fcful.cn/snews/2810494.htm
- http://m.3g.fcful.cn/snews/047471.htm
- http://m.3g.fcful.cn/snews/291159.htm
- http://m.3g.fcful.cn/snews/120402.htm
- http://m.3g.fcful.cn/snews/348713.htm
- http://m.3g.fcful.cn/snews/99461.htm
- http://m.3g.fcful.cn/snews/1229.htm
- http://m.3g.fcful.cn/snews/5028.htm
- http://m.3g.fcful.cn/snews/6744540.htm
- http://m.3g.fcful.cn/snews/27309.htm
- http://m.3g.fcful.cn/snews/9265.htm
- http://m.3g.fcful.cn/snews/80445.htm
- http://m.3g.fcful.cn/snews/84514.htm
- http://m.3g.fcful.cn/snews/5753198.htm
- http://m.3g.fcful.cn/snews/4667189.htm
- http://m.3g.fcful.cn/snews/1953333.htm
- http://m.3g.fcful.cn/snews/249582.htm
- http://m.3g.fcful.cn/snews/748133.htm
- http://m.3g.fcful.cn/snews/8865116.htm
- http://m.3g.fcful.cn/snews/0669.htm

## 项目结构

```
weblink-navigator/
├── manage.py                  # 项目管理入口，集成数据库迁移、服务器启动、任务调度
├── requirements.txt           # Python生产依赖清单，锁定所有第三方库版本
├── config/
│   ├── settings.py            # 主配置文件，包含数据库连接、缓存、日志级别、安全密钥
│   ├── settings_dev.py        # 开发环境覆盖配置，开启调试模式与热重载
│   └── settings_prod.py       # 生产环境覆盖配置，关闭调试，配置uWSGI参数与静态文件服务
├── core/
│   ├── __init__.py
│   ├── models.py              # 数据模型定义：Link, Tag, CheckRecord, ViewTemplate, AuditLog
│   ├── link_parser.py         # 链接解析与规范化模块，处理各种畸形输入格式
│   ├── health_checker.py      # 异步健康检查任务实现，包含超时控制与重试策略
│   ├── metadata_extractor.py  # 元数据提取器，依赖beautifulsoup4实现标题与摘要解析
│   ├── tag_engine.py          # 自动标签引擎，基于规则库与正则表达式进行匹配
│   └── audit_logger.py        # 审计日志记录器，支持同步写入与异步批量刷盘
├── web/
│   ├── __init__.py
│   ├── routes.py              # 主路由定义，包含面板、API、订阅端点的URL映射
│   ├── views.py               # 视图控制器，处理请求参数校验、数据查询与模板渲染
│   ├── api_v1.py              # RESTful API v1 实现，支持链接CRUD、标签管理、查询筛选
│   └── templates/             # Jinja2模板目录，包含仪表盘、列表页、详情页、设置页
├── worker/
│   ├── __init__.py
│   ├── scheduler.py           # 定时任务调度器，基于apscheduler实现周期性健康检查
│   ├── tasks.py               # 具体任务函数：批量探测、元数据刷新、过期链接清理
│   └── queue.py               # 任务队列封装，支持Redis或内存队列两种后端
├── tests/
│   ├── __init__.py
│   ├── test_models.py         # 数据模型单元测试，覆盖创建、更新、查询与索引性能
│   ├── test_parser.py         # 链接解析器测试，包含大量异常格式用例
│   └── test_api.py            # API端点集成测试，使用pytest与临时数据库
├── scripts/
│   ├── import_links.py        # 批量导入脚本，支持从CSV、JSON、纯文本读取链接列表
│   ├── export_feed.py         # 导出RSS/JSON订阅文件的命令行工具
│   └── migrate_legacy.py      # 从旧版本数据库迁移数据的辅助脚本
└── docs/
    ├── README.md              # 文档索引页，指引用户按需查阅不同模块说明
    ├── quickstart.md          # 快速入门指南，包含图文步骤与首次配置建议
    ├── user-guide/            # 用户操作手册分章节存放
    ├── admin-guide/           # 管理员部署与运维指南
    ├── developer/             # 开发者扩展文档与API参考
    └── api/                   # OpenAPI规范文件与接口调用示例
```

## 贡献指南

提交问题报告与功能请求 在GitHub Issues页面新建issue，使用提供的模板填写复现步骤、环境信息与预期行为。对于功能请求，请清晰描述使用场景与期望的接口变化。

代码贡献流程 从main分支创建功能分支，命名规范为feature/功能简述或fix/问题简述。确保所有现有测试通过，并为新增代码编写对应的单元测试与集成测试。提交前运行代码格式化工具black与静态检查flake8。

文档改进 文档采用Markdown格式编写，存放于docs目录。改进文档时请保持与技术实现一致，更新API示例与配置参数说明。重大变更需在docs/developer/中记录迁移指南。

本地测试验证 使用pytest运行完整测试套件，确保覆盖率不低于85%。测试数据库使用独立的test_weblink.db文件，不会影响开发或生产数据。提交前执行python manage.py check检查配置完整性。

翻译与本地化 欢迎提供多语言界面翻译，翻译文件位于web/locales/目录下，遵循gettext标准。新增语言时请同时更新config/settings.py中的LANGUAGES配置。

## 常见问题

Q: 健康检查功能对目标服务器会造成多大的请求压力？

A: 系统默认采用间隔探测策略，每个链接的检查间隔不低于30分钟，且并发请求数限制为5个，避免对源站造成突发流量。用户可在配置文件中调整max_concurrent_checks与check_interval参数，对于内部网络链路可适当缩短间隔。所有探测请求携带User-Agent标识为WebLinkNavigator/版本号，方便源站识别。

Q: 元数据提取是否会存储目标页面的完整内容？

A: 不会。系统仅提取并存储标题、meta描述、h1标题、发布时间与正文前200个字符作为摘要，不保留完整HTML或图片资源。所有提取操作均在服务器端内存中完成，原始页面内容不会写入数据库或日志文件，符合数据最小化原则。

Q: 如何将现有的浏览器书签批量导入系统？

A: 主流浏览器（Chrome、Firefox、Edge）均支持导出书签为HTML文件。系统scripts目录下提供了import_bookmarks.py脚本，可解析该HTML文件并自动识别书签文件夹名称作为标签，一键导入。对于其他格式如JSON或CSV，可使用import_links.py脚本指定格式参数。导入前建议先预览解析结果，确认无误后再执行写入。

## 许可证

MIT License

Copyright (c) 2026 Weblink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
