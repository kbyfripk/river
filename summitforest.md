# FCPortal

FCPortal 是一个轻量级的技术资讯与外部资源导航聚合平台，面向开发人员、运维工程师与技术研究者，用于集中管理、分类检索和快速访问来自互联网的高价值技术文档、行业动态与工程实践参考链接。项目本身不生产内容，而是提供结构化的外链索引体系，配套标签过滤、全文检索与访问频次统计能力，帮助技术团队在信息过载的环境中高效定位有效资源。

## 功能概览

**结构化外链目录**：按技术领域、文档类型与来源站点对链接进行多级分类，支持自定义标签体系。

**全文元数据检索**：基于链接标题、来源域名、摘要描述与标签组合进行关键词匹配，响应时间控制在 200 毫秒以内。

**访问热度统计**：记录每个外链的点击次数与最后访问时间，自动生成周/月维度的热门资源排行榜。

**链接可用性监控**：定时对已收录链接发起 HEAD 请求检测，标记失效或重定向资源，支持手动重新验证。

**批量导入与导出**：支持通过 CSV 或 JSON 格式批量新增链接，也可将当前索引完整导出为 Markdown 表格或结构化数据文件。

**用户自定义收藏夹**：注册用户可将常用链接加入个人收藏列表，支持分组管理与备注添加。

**RSS 订阅源生成**：按标签或分类生成 RSS 2.0 格式订阅源，便于集成至第三方阅读器。

## 应用场景

技术团队内部知识库构建：团队 Leader 可将部门常用的技术规范、API 文档、运维手册与故障排查案例集中收录至 FCPortal，新成员入职时通过该平台快速了解团队技术栈与常用工具链。

个人开发者学习路径管理：独立开发者可使用 FCPortal 整理从各类技术博客、在线课程与开源项目仓库中收集的学习资料，按编程语言或框架分类，配合检索功能减少重复搜索时间。

技术社区资源共建共享：开源社区或技术沙龙组织者可部署 FCPortal 作为社区资源门户，成员共同提交优质外链，通过投票与热度机制筛选出高价值内容，降低信息筛选成本。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/fcportal.git
cd fcportal

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库结构
python manage.py migrate

# 从示例数据导入首批外链索引
python manage.py loaddata fixtures/initial_links.json

# 启动开发服务器
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 即可进入 FCPortal 首页。管理员后台地址为 /admin，默认账号 admin 密码 admin123（首次启动后请立即修改）。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.11 LTS |
| SQLite | 3.35 及以上 | 内置数据库，生产环境建议切换至 PostgreSQL 14+ |
| Django | 4.2 LTS | Web 框架，用于路由、ORM 与后台管理 |
| django-filter | 23.5 | 提供链接列表的过滤与排序能力 |
| requests | 2.31 | 用于可用性监控中的 HTTP 探测 |
| redis | 7.0 及以上 | 可选依赖，用于访问热度统计的缓存层 |
| uWSGI / Gunicorn | 任意稳定版 | 生产环境 WSGI 服务器，二选一 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何注册账号、添加链接、使用检索与收藏功能 |
| 管理员指南 | /docs/admin-guide/ | 如何配置监控频率、管理用户权限与审核提交 |
| API 参考 | /docs/api-reference/ | 如何通过 RESTful API 进行链接的增删改查与批量操作 |
| 部署运维 | /docs/deployment/ | 如何配置 PostgreSQL、Nginx 反向代理与 systemd 服务 |

完整文档位于项目根目录下的 docs/ 文件夹，亦可在启动服务后访问 /docs/ 路径在线浏览。

## 资源列表

- http://m.3g.fcful.cn/snews/69332.htm
- http://m.3g.fcful.cn/snews/748149.htm
- http://m.3g.fcful.cn/snews/63999.htm
- http://m.3g.fcful.cn/snews/5271.htm
- http://m.3g.fcful.cn/snews/6284037.htm
- http://m.3g.fcful.cn/snews/8287.htm
- http://m.3g.fcful.cn/snews/36680.htm
- http://m.3g.fcful.cn/snews/4876608.htm
- http://m.3g.fcful.cn/snews/9378.htm
- http://m.3g.fcful.cn/snews/8669151.htm
- http://m.3g.fcful.cn/snews/80075.htm
- http://m.3g.fcful.cn/snews/0785.htm
- http://m.3g.fcful.cn/snews/5173.htm
- http://m.3g.fcful.cn/snews/5177274.htm
- http://m.3g.fcful.cn/snews/8156633.htm
- http://m.3g.fcful.cn/snews/6714.htm
- http://m.3g.fcful.cn/snews/8103742.htm
- http://m.3g.fcful.cn/snews/805607.htm
- http://m.3g.fcful.cn/snews/49306.htm
- http://m.3g.fcful.cn/snews/6558.htm
- http://m.3g.fcful.cn/snews/1571269.htm
- http://m.3g.fcful.cn/snews/3192.htm
- http://m.3g.fcful.cn/snews/4522510.htm
- http://m.3g.fcful.cn/snews/4826807.htm
- http://m.3g.fcful.cn/snews/9758.htm
- http://m.3g.fcful.cn/snews/26716.htm
- http://m.3g.fcful.cn/snews/3981433.htm
- http://m.3g.fcful.cn/snews/4604.htm
- http://m.3g.fcful.cn/snews/5327522.htm
- http://m.3g.fcful.cn/snews/339471.htm
- http://m.3g.fcful.cn/snews/09161.htm
- http://m.3g.fcful.cn/snews/2629.htm
- http://m.3g.fcful.cn/snews/5513.htm
- http://m.3g.fcful.cn/snews/30985.htm
- http://m.3g.fcful.cn/snews/70881.htm
- http://m.3g.fcful.cn/snews/667331.htm
- http://m.3g.fcful.cn/snews/909785.htm
- http://m.3g.fcful.cn/snews/98882.htm
- http://m.3g.fcful.cn/snews/041152.htm
- http://m.3g.fcful.cn/snews/5253076.htm
- http://m.3g.fcful.cn/snews/705526.htm
- http://m.3g.fcful.cn/snews/582428.htm
- http://m.3g.fcful.cn/snews/74610.htm
- http://m.3g.fcful.cn/snews/63588.htm
- http://m.3g.fcful.cn/snews/3532812.htm
- http://m.3g.fcful.cn/snews/038353.htm
- http://m.3g.fcful.cn/snews/2140.htm
- http://m.3g.fcful.cn/snews/447474.htm
- http://m.3g.fcful.cn/snews/400991.htm
- http://m.3g.fcful.cn/snews/131249.htm
- http://m.3g.fcful.cn/snews/8898009.htm
- http://m.3g.fcful.cn/snews/3638818.htm
- http://m.3g.fcful.cn/snews/88194.htm
- http://m.3g.fcful.cn/snews/28978.htm
- http://m.3g.fcful.cn/snews/5095.htm
- http://m.3g.fcful.cn/snews/67366.htm
- http://m.3g.fcful.cn/snews/921521.htm
- http://m.3g.fcful.cn/snews/6759.htm
- http://m.3g.fcful.cn/snews/139150.htm
- http://m.3g.fcful.cn/snews/7175.htm
- http://m.3g.fcful.cn/snews/8579841.htm
- http://m.3g.fcful.cn/snews/555422.htm
- http://m.3g.fcful.cn/snews/488027.htm
- http://m.3g.fcful.cn/snews/4757.htm
- http://m.3g.fcful.cn/snews/1089421.htm
- http://m.3g.fcful.cn/snews/968468.htm
- http://m.3g.fcful.cn/snews/7164275.htm
- http://m.3g.fcful.cn/snews/5117.htm
- http://m.3g.fcful.cn/snews/74912.htm
- http://m.3g.fcful.cn/snews/5534.htm
- http://m.3g.fcful.cn/snews/137741.htm
- http://m.3g.fcful.cn/snews/0530.htm
- http://m.3g.fcful.cn/snews/4112835.htm
- http://m.3g.fcful.cn/snews/32334.htm
- http://m.3g.fcful.cn/snews/36832.htm
- http://m.3g.fcful.cn/snews/6711.htm
- http://m.3g.fcful.cn/snews/756318.htm
- http://m.3g.fcful.cn/snews/5743654.htm
- http://m.3g.fcful.cn/snews/8828459.htm
- http://m.3g.fcful.cn/snews/0001.htm
- http://m.3g.fcful.cn/snews/8414121.htm
- http://m.3g.fcful.cn/snews/5020056.htm
- http://m.3g.fcful.cn/snews/8319.htm
- http://m.3g.fcful.cn/snews/4638243.htm
- http://m.3g.fcful.cn/snews/2125528.htm
- http://m.3g.fcful.cn/snews/1010871.htm
- http://m.3g.fcful.cn/snews/8347626.htm
- http://m.3g.fcful.cn/snews/106999.htm
- http://m.3g.fcful.cn/snews/42320.htm
- http://m.3g.fcful.cn/snews/1939088.htm
- http://m.3g.fcful.cn/snews/0026.htm
- http://m.3g.fcful.cn/snews/1600.htm
- http://m.3g.fcful.cn/snews/882840.htm
- http://m.3g.fcful.cn/snews/09341.htm
- http://m.3g.fcful.cn/snews/027346.htm
- http://m.3g.fcful.cn/snews/325967.htm
- http://m.3g.fcful.cn/snews/089953.htm
- http://m.3g.fcful.cn/snews/9735.htm
- http://m.3g.fcful.cn/snews/7716.htm
- http://m.3g.fcful.cn/snews/5364755.htm
- http://m.3g.fcful.cn/snews/682231.htm
- http://m.3g.fcful.cn/snews/2978.htm
- http://m.3g.fcful.cn/snews/151813.htm
- http://m.3g.fcful.cn/snews/038371.htm
- http://m.3g.fcful.cn/snews/539544.htm
- http://m.3g.fcful.cn/snews/81222.htm
- http://m.3g.fcful.cn/snews/5140982.htm
- http://m.3g.fcful.cn/snews/9828711.htm
- http://m.3g.fcful.cn/snews/279697.htm
- http://m.3g.fcful.cn/snews/8475079.htm
- http://m.3g.fcful.cn/snews/9974068.htm
- http://m.3g.fcful.cn/snews/8432320.htm
- http://m.3g.fcful.cn/snews/8588.htm
- http://m.3g.fcful.cn/snews/63821.htm
- http://m.3g.fcful.cn/snews/311781.htm
- http://m.3g.fcful.cn/snews/251249.htm
- http://m.3g.fcful.cn/snews/283926.htm
- http://m.3g.fcful.cn/snews/21730.htm
- http://m.3g.fcful.cn/snews/5543535.htm
- http://m.3g.fcful.cn/snews/9790546.htm
- http://m.3g.fcful.cn/snews/6834635.htm
- http://m.3g.fcful.cn/snews/4138.htm
- http://m.3g.fcful.cn/snews/2486.htm
- http://m.3g.fcful.cn/snews/221806.htm
- http://m.3g.fcful.cn/snews/94301.htm
- http://m.3g.fcful.cn/snews/4563.htm
- http://m.3g.fcful.cn/snews/4741.htm
- http://m.3g.fcful.cn/snews/26949.htm
- http://m.3g.fcful.cn/snews/5255.htm
- http://m.3g.fcful.cn/snews/838698.htm
- http://m.3g.fcful.cn/snews/331301.htm
- http://m.3g.fcful.cn/snews/375592.htm
- http://m.3g.fcful.cn/snews/6877.htm
- http://m.3g.fcful.cn/snews/9038.htm
- http://m.3g.fcful.cn/snews/260031.htm
- http://m.3g.fcful.cn/snews/2462.htm
- http://m.3g.fcful.cn/snews/8675.htm
- http://m.3g.fcful.cn/snews/70276.htm
- http://m.3g.fcful.cn/snews/1501596.htm
- http://m.3g.fcful.cn/snews/2307053.htm
- http://m.3g.fcful.cn/snews/553007.htm
- http://m.3g.fcful.cn/snews/3157.htm
- http://m.3g.fcful.cn/snews/63805.htm
- http://m.3g.fcful.cn/snews/93673.htm
- http://m.3g.fcful.cn/snews/985042.htm
- http://m.3g.fcful.cn/snews/91186.htm
- http://m.3g.fcful.cn/snews/2517993.htm
- http://m.3g.fcful.cn/snews/39008.htm
- http://m.3g.fcful.cn/snews/7347.htm
- http://m.3g.fcful.cn/snews/6728308.htm
- http://m.3g.fcful.cn/snews/3575980.htm
- http://m.3g.fcful.cn/snews/669287.htm
- http://m.3g.fcful.cn/snews/021012.htm
- http://m.3g.fcful.cn/snews/4291.htm
- http://m.3g.fcful.cn/snews/89499.htm
- http://m.3g.fcful.cn/snews/47047.htm
- http://m.3g.fcful.cn/snews/0416658.htm
- http://m.3g.fcful.cn/snews/2591284.htm
- http://m.3g.fcful.cn/snews/8941486.htm
- http://m.3g.fcful.cn/snews/1388591.htm
- http://m.3g.fcful.cn/snews/401349.htm
- http://m.3g.fcful.cn/snews/677731.htm
- http://m.3g.fcful.cn/snews/9727208.htm
- http://m.3g.fcful.cn/snews/57956.htm
- http://m.3g.fcful.cn/snews/95838.htm
- http://m.3g.fcful.cn/snews/5600526.htm
- http://m.3g.fcful.cn/snews/216107.htm
- http://m.3g.fcful.cn/snews/8651906.htm
- http://m.3g.fcful.cn/snews/625414.htm
- http://m.3g.fcful.cn/snews/7277.htm
- http://m.3g.fcful.cn/snews/407584.htm
- http://m.3g.fcful.cn/snews/94952.htm
- http://m.3g.fcful.cn/snews/1483.htm
- http://m.3g.fcful.cn/snews/95349.htm
- http://m.3g.fcful.cn/snews/25177.htm
- http://m.3g.fcful.cn/snews/41511.htm
- http://m.3g.fcful.cn/snews/440487.htm
- http://m.3g.fcful.cn/snews/224227.htm
- http://m.3g.fcful.cn/snews/948736.htm
- http://m.3g.fcful.cn/snews/9044157.htm
- http://m.3g.fcful.cn/snews/91317.htm
- http://m.3g.fcful.cn/snews/53723.htm
- http://m.3g.fcful.cn/snews/76772.htm
- http://m.3g.fcful.cn/snews/8852087.htm
- http://m.3g.fcful.cn/snews/1425.htm
- http://m.3g.fcful.cn/snews/853698.htm
- http://m.3g.fcful.cn/snews/6837.htm
- http://m.3g.fcful.cn/snews/58712.htm
- http://m.3g.fcful.cn/snews/159272.htm
- http://m.3g.fcful.cn/snews/097931.htm
- http://m.3g.fcful.cn/snews/71312.htm
- http://m.3g.fcful.cn/snews/922568.htm
- http://m.3g.fcful.cn/snews/50207.htm
- http://m.3g.fcful.cn/snews/9856.htm
- http://m.3g.fcful.cn/snews/6474894.htm
- http://m.3g.fcful.cn/snews/4837846.htm
- http://m.3g.fcful.cn/snews/6890196.htm
- http://m.3g.fcful.cn/snews/3278307.htm
- http://m.3g.fcful.cn/snews/4472.htm
- http://m.3g.fcful.cn/snews/12044.htm
- http://m.3g.fcful.cn/snews/8829.htm
- http://m.3g.fcful.cn/snews/3242785.htm
- http://m.3g.fcful.cn/snews/114388.htm
- http://m.3g.fcful.cn/snews/27789.htm
- http://m.3g.fcful.cn/snews/645923.htm
- http://m.3g.fcful.cn/snews/9251.htm
- http://m.3g.fcful.cn/snews/0719.htm
- http://m.3g.fcful.cn/snews/9075.htm
- http://m.3g.fcful.cn/snews/343826.htm
- http://m.3g.fcful.cn/snews/7848.htm
- http://m.3g.fcful.cn/snews/121748.htm
- http://m.3g.fcful.cn/snews/833610.htm
- http://m.3g.fcful.cn/snews/91295.htm
- http://m.3g.fcful.cn/snews/4946.htm
- http://m.3g.fcful.cn/snews/3294.htm
- http://m.3g.fcful.cn/snews/3445.htm
- http://m.3g.fcful.cn/snews/3048075.htm
- http://m.3g.fcful.cn/snews/8839.htm
- http://m.3g.fcful.cn/snews/01456.htm
- http://m.3g.fcful.cn/snews/0280.htm
- http://m.3g.fcful.cn/snews/0203.htm
- http://m.3g.fcful.cn/snews/8426544.htm
- http://m.3g.fcful.cn/snews/437739.htm
- http://m.3g.fcful.cn/snews/813787.htm
- http://m.3g.fcful.cn/snews/1891.htm
- http://m.3g.fcful.cn/snews/650727.htm
- http://m.3g.fcful.cn/snews/0620913.htm
- http://m.3g.fcful.cn/snews/6309154.htm
- http://m.3g.fcful.cn/snews/7590.htm
- http://m.3g.fcful.cn/snews/2807.htm
- http://m.3g.fcful.cn/snews/93535.htm
- http://m.3g.fcful.cn/snews/118521.htm
- http://m.3g.fcful.cn/snews/70902.htm
- http://m.3g.fcful.cn/snews/88672.htm
- http://m.3g.fcful.cn/snews/667525.htm
- http://m.3g.fcful.cn/snews/2208.htm
- http://m.3g.fcful.cn/snews/21746.htm
- http://m.3g.fcful.cn/snews/15865.htm
- http://m.3g.fcful.cn/snews/40557.htm
- http://m.3g.fcful.cn/snews/68676.htm
- http://m.3g.fcful.cn/snews/69271.htm
- http://m.3g.fcful.cn/snews/876113.htm
- http://m.3g.fcful.cn/snews/878224.htm
- http://m.3g.fcful.cn/snews/1598032.htm
- http://m.3g.fcful.cn/snews/7484519.htm
- http://m.3g.fcful.cn/snews/1151.htm
- http://m.3g.fcful.cn/snews/1593271.htm
- http://m.3g.fcful.cn/snews/01039.htm
- http://m.3g.fcful.cn/snews/0458.htm
- http://m.3g.fcful.cn/snews/7803907.htm

## 项目结构

```
fcportal/
├── manage.py                         # Django 项目入口脚本
├── requirements.txt                  # Python 依赖声明文件
├── fcportal/                         # 项目配置目录
│   ├── __init__.py
│   ├── settings.py                   # 基础配置（数据库、时区、中间件）
│   ├── settings_prod.py              # 生产环境覆盖配置（敏感信息从环境变量读取）
│   ├── urls.py                       # 根路由映射
│   └── wsgi.py                       # 生产环境 WSGI 入口
├── apps/                             # 所有自定义应用
│   ├── links/                        # 外链核心应用
│   │   ├── models.py                 # Link, Category, Tag, ClickLog 数据模型
│   │   ├── views.py                  # 列表、详情、检索、统计视图
│   │   ├── filters.py                # django-filter 过滤类
│   │   ├── admin.py                  # 后台管理定制
│   │   └── utils/                    # 辅助函数
│   │       ├── monitor.py            # 可用性探测调度
│   │       └── rss_generator.py      # RSS 订阅源生成
│   ├── accounts/                     # 用户认证与个人收藏
│   │   ├── models.py                 # 扩展用户模型，收藏关系表
│   │   └── views.py                  # 注册、登录、收藏管理
│   └── api/                          # RESTful API 应用
│       ├── serializers.py            # 序列化器
│       └── viewsets.py               # 针对 Link 的 CRUD 视图集
├── static/                           # 静态资源（CSS, JS, 图片）
│   ├── css/
│   ├── js/
│   └── images/
├── templates/                        # Django 模板文件
│   ├── base.html                     # 基础骨架模板
│   ├── links/                        # 链接相关页面模板
│   └── accounts/                     # 认证相关页面模板
├── docs/                             # 项目文档
│   ├── user-guide.md
│   ├── admin-guide.md
│   ├── api-reference.md
│   └── deployment.md
├── fixtures/                         # 初始数据加载文件
│   └── initial_links.json            # 包含预置分类与示例链接
├── scripts/                          # 运维与辅助脚本
│   ├── import_csv.py                 # CSV 批量导入工具
│   └── export_json.py                # JSON 全量导出工具
└── tests/                            # 单元测试与集成测试
    ├── test_models.py
    ├── test_views.py
    └── test_monitor.py
```

## 贡献指南

1. 在 GitHub 仓库的 Issues 区域查找已标记为 "help wanted" 或 "good first issue" 的任务，或自行提交新的需求建议与缺陷报告。提交 Issue 时请使用提供的模板，清楚描述问题背景、复现步骤与预期行为。

2. 派生项目仓库至个人账号，在派生副本中创建功能分支，分支命名遵循 feature/xxx 或 fix/xxx 格式。提交代码前请运行现有单元测试套件确保无回归问题，并为新增功能补充对应的测试用例。

3. 开发过程中遵循项目代码风格规范（PEP 8 与 ESLint 配置），提交信息使用语义化格式（类型: 简短描述），类型包括 feat、fix、docs、style、refactor、test、chore 等。提交前通过 pre-commit 钩子进行静态检查。

4. 完成开发后从功能分支向主仓库的 develop 分支发起 Pull Request，PR 描述中关联对应的 Issue 编号，并简要说明实现方案与测试覆盖情况。至少一名项目维护者审阅通过后合并。

5. 参与文档完善工作，包括但不限于修正错漏、补充示例、翻译多语言版本。文档贡献同样视为有效贡献，合并后贡献者名单将记录于 CONTRIBUTORS.md 文件中。

## 常见问题

问：启动服务后访问首页，左侧分类列表显示为空，但数据已经通过 fixtures 导入。如何排查？

答：首先确认 SQLite 数据库文件是否存在且可写，检查 manage.py migrate 命令执行输出是否包含迁移错误。若迁移成功，进入 Django shell 执行 from apps.links.models import Category; print(Category.objects.count()) 查看分类数量。如果返回 0，说明 fixtures 加载未生效，可尝试 python manage.py loaddata fixtures/initial_links.json --app links 重新导入。若分类存在但前端不显示，检查浏览器开发者工具控制台是否存在 JavaScript 错误，并确认模板中遍历分类对象的变量名与视图上下文一致。

问：可用性监控任务如何调整检测间隔？生产环境是否需要单独部署监控进程？

答：监控间隔通过 settings.py 中的 MONITOR_INTERVAL_HOURS 变量控制，默认值为 24 小时。开发环境下监控由 django-cron 或 celery beat 在请求周期中触发，不适合生产环境。生产环境建议部署独立的 systemd timer 或 crontab 任务，周期调用 python manage.py check_links 命令。该命令会遍历所有状态为 active 的链接并发 HEAD 请求，超时时间可在 settings.py 中通过 MONITOR_TIMEOUT_SECONDS 调整。

问：FCPortal 支持从其他导航站迁移数据吗？是否有现成的转换脚本？

答：项目目前未内置针对特定第三方导航站的迁移工具，但提供了通用的 CSV 与 JSON 导入导出功能。用户可参照 scripts/import_csv.py 中定义的列映射关系，将其他来源的链接数据整理为符合格式的 CSV 文件进行导入。若涉及自定义字段，可通过 Django 后台的数据导出功能先导出一份样例，再按样例结构编排源数据。对于大规模迁移场景，建议先在测试环境中试导入，验证字段映射无误后再操作生产数据库。

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
