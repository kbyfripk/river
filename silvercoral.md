# WebLink Collective Archive

WebLink Collective Archive 是一个面向技术研究者、内容聚合者与信息管理从业者的结构化外链归档系统。项目定位于对分散于互联网各处的技术博文、新闻动态与参考文档进行系统性采集、分类存储与元数据化管理，解决个人或团队在信息收集过程中面临的链接失效、上下文丢失与检索困难等核心问题。目标用户包括开源社区维护者、技术内容编辑、数据标注团队以及各类需要长期保存外链资源的知识工作者。项目本身不提供爬虫或自动化采集功能，而是提供标准化的链接录入规范、目录组织模板与元数据字段定义，帮助用户以最低成本建立自己的外链仓库。

## 功能概览

**批量链接导入** 支持通过 CSV 或 JSON 格式批量录入链接数据，系统自动解析 URL 结构并提取域名、路径与扩展名信息。

**元数据自动补全** 对每条链接自动发起 HEAD 请求获取响应头信息，记录内容类型、内容长度与最后修改时间，辅助判断资源可用性。

**分类标签管理** 允许用户为每一条链接添加多个自定义标签，并基于标签组合进行快速筛选与统计。

**失效检测与报告** 定期对已归档链接进行可用性检查，生成失效链接清单并支持导出为文本报告。

**全文检索与过滤** 基于链接 URL、标题、描述、标签与录入时间构建多字段联合检索，支持模糊匹配与精确查询。

**数据导入导出** 提供标准格式的批量导出功能，支持 JSON、CSV 与 Markdown 列表三种输出格式，便于与其他工具链集成。

**访问频率统计** 记录每条链接的查阅次数与最后访问时间，辅助判断内容热度与优先级。

## 应用场景

技术博客归档管理 技术团队在日常阅读中积累大量博文与教程链接，使用本系统按主题分类存储，并定期检测失效链接，确保知识库的长期可用性。

开源项目参考文献整理 开源项目维护者在编写文档或 RFC 时需要引用外部资源，通过本系统统一管理所有引用链接，并在版本发布前进行批量可用性验证。

内容聚合站点运维 内容聚合类网站需要定期更新推荐链接列表，本系统提供标签筛选与格式导出功能，可快速生成符合站点模板的链接清单。

数据标注任务资源索引 数据标注团队在标注过程中需要参考大量规范文档与样例页面，通过本系统集中管理这些资源链接，并为标注平台提供结构化的索引接口。

个人知识库外链备份 个人知识管理爱好者利用本系统为笔记中的外链建立独立档案，避免因原始页面删除或迁移导致的引用断裂。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/weblink-collective/archive.git

# 进入项目目录
cd archive

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 初始化本地数据库
python manage.py initdb

# 导入示例链接数据
python manage.py import --source samples/links.csv

# 启动本地 Web 服务
python manage.py runserver --port 8080
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.10 或更高 | 核心运行环境，低于此版本将导致类型注解解析异常 |
| SQLite | 3.35 或更高 | 内嵌数据库，用于存储链接元数据与标签关系 |
| requests | 2.28.0 或更高 | 用于 HTTP 请求发送与响应头解析 |
| click | 8.1.0 或更高 | 命令行交互框架，提供子命令解析能力 |
| jinja2 | 3.1.0 或更高 | 模板引擎，用于导出 Markdown 列表与 HTML 报告 |
| pytest | 7.2.0 或更高 | 单元测试框架，仅在开发环境中必需 |
| black | 22.10.0 或更高 | 代码格式化工具，仅在代码提交前使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | docs/quickstart.md | 如何安装、初始化并导入第一批链接；首次使用需要执行哪些命令 |
| 操作 | docs/usage.md | 如何添加标签、执行检索、导出清单以及更新元数据 |
| 维护 | docs/maintenance.md | 如何配置失效检测周期、处理失效链接以及备份数据库 |
| 扩展 | docs/development.md | 如何新增导入格式、自定义元数据字段以及编写插件 |

## 资源列表

- http://m.blog.fcful.cn/bnews/216293.htm
- http://m.blog.fcful.cn/bnews/871862.htm
- http://m.blog.fcful.cn/bnews/967745.htm
- http://m.blog.fcful.cn/bnews/404234.htm
- http://m.blog.fcful.cn/bnews/96976.htm
- http://m.blog.fcful.cn/bnews/771318.htm
- http://m.blog.fcful.cn/bnews/9445439.htm
- http://m.blog.fcful.cn/bnews/44051.htm
- http://m.blog.fcful.cn/bnews/301133.htm
- http://m.blog.fcful.cn/bnews/8462.htm
- http://m.blog.fcful.cn/bnews/210315.htm
- http://m.blog.fcful.cn/bnews/847833.htm
- http://m.blog.fcful.cn/bnews/88212.htm
- http://m.blog.fcful.cn/bnews/824570.htm
- http://m.blog.fcful.cn/bnews/0674088.htm
- http://m.blog.fcful.cn/bnews/348261.htm
- http://m.blog.fcful.cn/bnews/77584.htm
- http://m.blog.fcful.cn/bnews/26221.htm
- http://m.blog.fcful.cn/bnews/8040041.htm
- http://m.blog.fcful.cn/bnews/5963588.htm
- http://m.blog.fcful.cn/bnews/973923.htm
- http://m.blog.fcful.cn/bnews/0558100.htm
- http://m.blog.fcful.cn/bnews/35848.htm
- http://m.blog.fcful.cn/bnews/62925.htm
- http://m.blog.fcful.cn/bnews/426878.htm
- http://m.blog.fcful.cn/bnews/1378.htm
- http://m.blog.fcful.cn/bnews/430576.htm
- http://m.blog.fcful.cn/bnews/5476.htm
- http://m.blog.fcful.cn/bnews/12332.htm
- http://m.blog.fcful.cn/bnews/71541.htm
- http://m.blog.fcful.cn/bnews/784178.htm
- http://m.blog.fcful.cn/bnews/67020.htm
- http://m.blog.fcful.cn/bnews/6974.htm
- http://m.blog.fcful.cn/bnews/130299.htm
- http://m.blog.fcful.cn/bnews/9406999.htm
- http://m.blog.fcful.cn/bnews/0761866.htm
- http://m.blog.fcful.cn/bnews/39186.htm
- http://m.blog.fcful.cn/bnews/99954.htm
- http://m.blog.fcful.cn/bnews/74361.htm
- http://m.blog.fcful.cn/bnews/1069.htm
- http://m.blog.fcful.cn/bnews/460220.htm
- http://m.blog.fcful.cn/bnews/3767257.htm
- http://m.blog.fcful.cn/bnews/50697.htm
- http://m.blog.fcful.cn/bnews/0726.htm
- http://m.blog.fcful.cn/bnews/1375403.htm
- http://m.blog.fcful.cn/bnews/02940.htm
- http://m.blog.fcful.cn/bnews/1594316.htm
- http://m.blog.fcful.cn/bnews/9969569.htm
- http://m.blog.fcful.cn/bnews/46430.htm
- http://m.blog.fcful.cn/bnews/809677.htm
- http://m.blog.fcful.cn/bnews/66893.htm
- http://m.blog.fcful.cn/bnews/5112.htm
- http://m.blog.fcful.cn/bnews/92429.htm
- http://m.blog.fcful.cn/bnews/0700287.htm
- http://m.blog.fcful.cn/bnews/4773950.htm
- http://m.blog.fcful.cn/bnews/614764.htm
- http://m.blog.fcful.cn/bnews/76088.htm
- http://m.blog.fcful.cn/bnews/125693.htm
- http://m.blog.fcful.cn/bnews/6735096.htm
- http://m.blog.fcful.cn/bnews/7549042.htm
- http://m.blog.fcful.cn/bnews/6218420.htm
- http://m.blog.fcful.cn/bnews/77551.htm
- http://m.blog.fcful.cn/bnews/8670.htm
- http://m.blog.fcful.cn/bnews/10284.htm
- http://m.blog.fcful.cn/bnews/7734027.htm
- http://m.blog.fcful.cn/bnews/423826.htm
- http://m.blog.fcful.cn/bnews/624316.htm
- http://m.blog.fcful.cn/bnews/9819232.htm
- http://m.blog.fcful.cn/bnews/4989.htm
- http://m.blog.fcful.cn/bnews/6304652.htm
- http://m.blog.fcful.cn/bnews/1824.htm
- http://m.blog.fcful.cn/bnews/70220.htm
- http://m.blog.fcful.cn/bnews/70044.htm
- http://m.blog.fcful.cn/bnews/3306.htm
- http://m.blog.fcful.cn/bnews/41026.htm
- http://m.blog.fcful.cn/bnews/064884.htm
- http://m.blog.fcful.cn/bnews/4041438.htm
- http://m.blog.fcful.cn/bnews/9688605.htm
- http://m.blog.fcful.cn/bnews/513535.htm
- http://m.blog.fcful.cn/bnews/007459.htm
- http://m.blog.fcful.cn/bnews/715846.htm
- http://m.blog.fcful.cn/bnews/1830387.htm
- http://m.blog.fcful.cn/bnews/4767166.htm
- http://m.blog.fcful.cn/bnews/317190.htm
- http://m.blog.fcful.cn/bnews/263254.htm
- http://m.blog.fcful.cn/bnews/5260042.htm
- http://m.blog.fcful.cn/bnews/4473029.htm
- http://m.blog.fcful.cn/bnews/2772.htm
- http://m.blog.fcful.cn/bnews/1167.htm
- http://m.blog.fcful.cn/bnews/91320.htm
- http://m.blog.fcful.cn/bnews/0791.htm
- http://m.blog.fcful.cn/bnews/2146561.htm
- http://m.blog.fcful.cn/bnews/578040.htm
- http://m.blog.fcful.cn/bnews/095616.htm
- http://m.blog.fcful.cn/bnews/2181238.htm
- http://m.blog.fcful.cn/bnews/5363132.htm
- http://m.blog.fcful.cn/bnews/681047.htm
- http://m.blog.fcful.cn/bnews/8745.htm
- http://m.blog.fcful.cn/bnews/42045.htm
- http://m.blog.fcful.cn/bnews/2796.htm
- http://m.blog.fcful.cn/bnews/120005.htm
- http://m.blog.fcful.cn/bnews/48801.htm
- http://m.blog.fcful.cn/bnews/71091.htm
- http://m.blog.fcful.cn/bnews/0668879.htm
- http://m.blog.fcful.cn/bnews/8879.htm
- http://m.blog.fcful.cn/bnews/00301.htm
- http://m.blog.fcful.cn/bnews/5600470.htm
- http://m.blog.fcful.cn/bnews/879985.htm
- http://m.blog.fcful.cn/bnews/513973.htm
- http://m.blog.fcful.cn/bnews/9031304.htm
- http://m.blog.fcful.cn/bnews/0352.htm
- http://m.blog.fcful.cn/bnews/1584.htm
- http://m.blog.fcful.cn/bnews/8196.htm
- http://m.blog.fcful.cn/bnews/4761908.htm
- http://m.blog.fcful.cn/bnews/2310.htm
- http://m.blog.fcful.cn/bnews/63588.htm
- http://m.blog.fcful.cn/bnews/5951683.htm
- http://m.blog.fcful.cn/bnews/785133.htm
- http://m.blog.fcful.cn/bnews/7479.htm
- http://m.blog.fcful.cn/bnews/3638.htm
- http://m.blog.fcful.cn/bnews/1074717.htm
- http://m.blog.fcful.cn/bnews/0882.htm
- http://m.blog.fcful.cn/bnews/5336436.htm
- http://m.blog.fcful.cn/bnews/60507.htm
- http://m.blog.fcful.cn/bnews/7336057.htm
- http://m.blog.fcful.cn/bnews/712949.htm
- http://m.blog.fcful.cn/bnews/59365.htm
- http://m.blog.fcful.cn/bnews/0120701.htm
- http://m.blog.fcful.cn/bnews/98783.htm
- http://m.blog.fcful.cn/bnews/4956543.htm
- http://m.blog.fcful.cn/bnews/845344.htm
- http://m.blog.fcful.cn/bnews/224049.htm
- http://m.blog.fcful.cn/bnews/23680.htm
- http://m.blog.fcful.cn/bnews/8856663.htm
- http://m.blog.fcful.cn/bnews/683888.htm
- http://m.blog.fcful.cn/bnews/75681.htm
- http://m.blog.fcful.cn/bnews/01762.htm
- http://m.blog.fcful.cn/bnews/182208.htm
- http://m.blog.fcful.cn/bnews/0653.htm
- http://m.blog.fcful.cn/bnews/544806.htm
- http://m.blog.fcful.cn/bnews/485767.htm
- http://m.blog.fcful.cn/bnews/27078.htm
- http://m.blog.fcful.cn/bnews/6148195.htm
- http://m.blog.fcful.cn/bnews/101822.htm
- http://m.blog.fcful.cn/bnews/43447.htm
- http://m.blog.fcful.cn/bnews/89783.htm
- http://m.blog.fcful.cn/bnews/68613.htm
- http://m.blog.fcful.cn/bnews/44612.htm
- http://m.blog.fcful.cn/bnews/6220342.htm
- http://m.blog.fcful.cn/bnews/89382.htm
- http://m.blog.fcful.cn/bnews/48931.htm
- http://m.blog.fcful.cn/bnews/3277.htm
- http://m.blog.fcful.cn/bnews/7874529.htm
- http://m.blog.fcful.cn/bnews/3354.htm
- http://m.blog.fcful.cn/bnews/285806.htm
- http://m.blog.fcful.cn/bnews/462875.htm
- http://m.blog.fcful.cn/bnews/5167.htm
- http://m.blog.fcful.cn/bnews/99573.htm
- http://m.blog.fcful.cn/bnews/0593361.htm
- http://m.blog.fcful.cn/bnews/6213.htm
- http://m.blog.fcful.cn/bnews/47885.htm
- http://m.blog.fcful.cn/bnews/75543.htm
- http://m.blog.fcful.cn/bnews/43565.htm
- http://m.blog.fcful.cn/bnews/8058.htm
- http://m.blog.fcful.cn/bnews/9974.htm
- http://m.blog.fcful.cn/bnews/348433.htm
- http://m.blog.fcful.cn/bnews/4370145.htm
- http://m.blog.fcful.cn/bnews/1317.htm
- http://m.blog.fcful.cn/bnews/52634.htm
- http://m.blog.fcful.cn/bnews/3142509.htm
- http://m.blog.fcful.cn/bnews/0643.htm
- http://m.blog.fcful.cn/bnews/5304.htm
- http://m.blog.fcful.cn/bnews/72710.htm
- http://m.blog.fcful.cn/bnews/8855307.htm
- http://m.blog.fcful.cn/bnews/4328.htm
- http://m.blog.fcful.cn/bnews/00714.htm
- http://m.blog.fcful.cn/bnews/34279.htm
- http://m.blog.fcful.cn/bnews/3352341.htm
- http://m.blog.fcful.cn/bnews/19012.htm
- http://m.blog.fcful.cn/bnews/28942.htm
- http://m.blog.fcful.cn/bnews/4539172.htm
- http://m.blog.fcful.cn/bnews/8472950.htm
- http://m.blog.fcful.cn/bnews/696306.htm
- http://m.blog.fcful.cn/bnews/9340105.htm
- http://m.blog.fcful.cn/bnews/0096485.htm
- http://m.blog.fcful.cn/bnews/640849.htm
- http://m.blog.fcful.cn/bnews/1662543.htm
- http://m.blog.fcful.cn/bnews/61568.htm
- http://m.blog.fcful.cn/bnews/6434867.htm
- http://m.blog.fcful.cn/bnews/035316.htm
- http://m.blog.fcful.cn/bnews/4211361.htm
- http://m.blog.fcful.cn/bnews/296531.htm
- http://m.blog.fcful.cn/bnews/187864.htm
- http://m.blog.fcful.cn/bnews/8524.htm
- http://m.blog.fcful.cn/bnews/797676.htm
- http://m.blog.fcful.cn/bnews/42234.htm
- http://m.blog.fcful.cn/bnews/0857491.htm
- http://m.blog.fcful.cn/bnews/980653.htm
- http://m.blog.fcful.cn/bnews/1813205.htm
- http://m.blog.fcful.cn/bnews/8543916.htm
- http://m.blog.fcful.cn/bnews/9496324.htm
- http://m.blog.fcful.cn/bnews/5078.htm
- http://m.blog.fcful.cn/bnews/1034846.htm
- http://m.blog.fcful.cn/bnews/2825006.htm
- http://m.blog.fcful.cn/bnews/45338.htm
- http://m.blog.fcful.cn/bnews/7686480.htm
- http://m.blog.fcful.cn/bnews/728284.htm
- http://m.blog.fcful.cn/bnews/4565631.htm
- http://m.blog.fcful.cn/bnews/059788.htm
- http://m.blog.fcful.cn/bnews/7530.htm
- http://m.blog.fcful.cn/bnews/888098.htm
- http://m.blog.fcful.cn/bnews/78647.htm
- http://m.blog.fcful.cn/bnews/9016544.htm
- http://m.blog.fcful.cn/bnews/904279.htm
- http://m.blog.fcful.cn/bnews/5615181.htm
- http://m.blog.fcful.cn/bnews/17064.htm
- http://m.blog.fcful.cn/bnews/480202.htm
- http://m.blog.fcful.cn/bnews/796911.htm
- http://m.blog.fcful.cn/bnews/2319265.htm
- http://m.blog.fcful.cn/bnews/69720.htm
- http://m.blog.fcful.cn/bnews/0849152.htm
- http://m.blog.fcful.cn/bnews/0073779.htm
- http://m.blog.fcful.cn/bnews/5917749.htm
- http://m.blog.fcful.cn/bnews/6634359.htm
- http://m.blog.fcful.cn/bnews/964333.htm
- http://m.blog.fcful.cn/bnews/85437.htm
- http://m.blog.fcful.cn/bnews/1232291.htm
- http://m.blog.fcful.cn/bnews/93049.htm
- http://m.blog.fcful.cn/bnews/5416903.htm
- http://m.blog.fcful.cn/bnews/443011.htm
- http://m.blog.fcful.cn/bnews/80605.htm
- http://m.blog.fcful.cn/bnews/6420271.htm
- http://m.blog.fcful.cn/bnews/19993.htm
- http://m.blog.fcful.cn/bnews/2495.htm
- http://m.blog.fcful.cn/bnews/6235.htm
- http://m.blog.fcful.cn/bnews/50556.htm
- http://m.blog.fcful.cn/bnews/8140900.htm
- http://m.blog.fcful.cn/bnews/6018175.htm
- http://m.blog.fcful.cn/bnews/36399.htm
- http://m.blog.fcful.cn/bnews/991932.htm
- http://m.blog.fcful.cn/bnews/15515.htm
- http://m.blog.fcful.cn/bnews/68147.htm
- http://m.blog.fcful.cn/bnews/0470206.htm
- http://m.blog.fcful.cn/bnews/80457.htm
- http://m.blog.fcful.cn/bnews/0883079.htm
- http://m.blog.fcful.cn/bnews/021104.htm
- http://m.blog.fcful.cn/bnews/760674.htm
- http://m.blog.fcful.cn/bnews/116292.htm
- http://m.blog.fcful.cn/bnews/3846542.htm
- http://m.blog.fcful.cn/bnews/5293.htm

## 项目结构

```
archive/
├── data/                                 # 数据存储目录
│   ├── db/                               # SQLite 数据库文件与迁移脚本
│   │   ├── schema.sql                    # 数据库表结构定义
│   │   └── migrations/                   # 版本迁移脚本存放位置
│   └── cache/                            # HTTP 响应缓存与临时文件
│       └── head_cache.db                 # HEAD 请求响应缓存数据库
├── src/                                  # 核心源代码目录
│   ├── core/                             # 核心业务逻辑模块
│   │   ├── link.py                       # Link 数据类与元数据解析器
│   │   ├── tag.py                        # 标签管理与统计逻辑
│   │   └── validator.py                  # URL 格式校验与规范化工具
│   ├── storage/                          # 存储适配器层
│   │   ├── sqlite_adapter.py             # SQLite 数据库操作封装
│   │   └── export.py                     # 导出格式生成器
│   └── cli/                              # 命令行接口模块
│       ├── main.py                       # 命令入口与参数解析
│       ├── import_cmd.py                 # import 子命令实现
│       ├── export_cmd.py                 # export 子命令实现
│       └── check_cmd.py                  # check 子命令实现
├── tests/                                # 单元测试与集成测试
│   ├── unit/                             # 单模块测试用例
│   └── integration/                      # 跨模块集成测试
├── docs/                                 # 项目文档目录
│   ├── quickstart.md                     # 快速入门指南
│   ├── usage.md                          # 详细使用手册
│   ├── maintenance.md                    # 运维与故障处理
│   └── development.md                    # 开发者指南与贡献规范
├── samples/                              # 示例数据文件
│   ├── links.csv                         # CSV 格式示例导入文件
│   └── links.json                        # JSON 格式示例导入文件
├── scripts/                              # 辅助运维脚本
│   ├── backup.sh                         # 数据库备份脚本
│   └── clean_cache.sh                    # 缓存清理脚本
├── requirements.txt                      # Python 依赖声明文件
├── setup.py                              # 包安装与分发配置
├── pyproject.toml                        # 项目元数据与工具配置
├── .gitignore                            # Git 版本控制忽略清单
├── LICENSE                               # MIT 许可证全文
└── README.md                             # 项目说明文档（本文件）
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账户，然后 clone 到本地开发环境，确保本地 Python 版本符合要求。

2. 创建新的功能分支，分支命名格式为 feature/简述功能名称 或 fix/简述问题名称，避免在主干分支直接修改。

3. 编写代码时遵循项目已定义的代码风格，使用 black 进行自动格式化，并确保所有现有单元测试通过，新增功能需附带对应测试用例。

4. 提交代码前运行 pytest 执行完整测试套件，确认无回归问题；同时运行 python manage.py check 验证链接处理相关功能正常。

5. 推送分支至远程仓库并创建 Pull Request，在 PR 描述中清晰说明变更目的、影响范围及测试情况，等待项目维护者审核。

## 常见问题

问：导入链接时提示 URL 格式不合法，但该链接在浏览器中可以正常访问。

答：系统对 URL 进行严格格式校验，要求必须包含协议头。若链接为裸域名或省略协议，请补全 http:// 或 https:// 后再导入。此外，部分链接包含不可见字符或编码问题，建议先使用 URL 编码工具处理后再尝试。

问：失效检测报告显示大量链接不可访问，但手动打开浏览器却能正常加载。

答：失效检测模块默认使用 HEAD 请求方法，部分服务器对 HEAD 请求不响应或返回错误状态码，但实际支持 GET 请求。可调整配置将检测方法切换为 GET，或增加请求头模拟浏览器指纹。若仍存在问题，建议检查网络代理设置或目标站点的访问限频策略。

问：如何迁移数据库到另一台服务器，导出和导入的最佳流程是什么。

答：首先在源服务器上使用 export 命令导出完整数据为 JSON 格式，将生成的 JSON 文件与 SQLite 数据库文件一并传输至目标服务器。然后在目标服务器执行 import 命令导入 JSON 文件，系统会自动合并数据并重建索引。若数据库文件结构一致，也可直接复制 .db 文件，但需确保目标环境 SQLite 版本不低于源环境。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
