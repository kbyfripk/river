# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研与信息采集场景的轻量级外链聚合与分类导航系统。该项目定位于帮助个人开发者、技术内容运营团队以及小型研究机构，以低成本、低维护复杂度的方式，将零散的优质外部资源按照自定义分类进行统一归集、展示与快速检索。

WebIndex 不提供内容生产功能，专注于链接的整理、标签化、状态监控与快速跳转。目标用户是那些日常需要维护大量书签、行业报告链接、开源工具主页或新闻资讯入口，但不愿依赖复杂 CMS 或商业书签服务的群体。WebIndex 可作为团队内部知识导航页的基础框架，也可作为个人浏览器起始页的替代方案。

## 功能概览

批量链接导入与结构化存储 支持通过命令行脚本或 Web 表单批量导入链接数据，自动解析标题、域名信息并生成唯一标识。

自定义分类与多级标签体系 允许用户为每条链接分配多个标签，并基于标签动态生成导航视图，支持无限级分类嵌套。

链接可用性主动探测 内置定时任务，对已收录链接发起 HEAD 请求，检测响应状态码并标记异常链接，便于定期清理失效资源。

全文检索与快速定位 基于标题、描述、标签和域名关键词提供轻量级全文搜索，支持拼音首字母模糊匹配。

响应式栅格展示布局 前端采用 CSS Grid 与 Flexbox 混合布局，在桌面端、平板和移动设备下自动适配卡片密度。

数据导入导出标准化 支持 JSON 与 CSV 格式的完整数据导出，便于迁移至其他工具或进行二次分析。

访客点击行为统计 记录每个外部链接的点击次数与最近点击时间，为导航排序提供热度参考依据。

单页面应用无刷新跳转 采用 History API 实现分类切换时的无刷新内容渲染，减少页面重载，提升浏览流畅度。

## 应用场景

技术团队内部文档导航门户 开发团队可将日常使用的代码仓库地址、CI/CD 工具后台、监控面板、云服务控制台以及内部 Wiki 统一收录，按项目或环境分类，作为团队浏览器起始页。

行业资讯与政策信息聚合站 市场分析人员可批量收录行业媒体专栏、政策发布页面、统计数据库入口，通过标签区分地域、领域和时间范围，实现信息的集中化入口管理。

开源项目生态导航页 开源社区维护者可将周边生态工具、插件列表、示例项目、讨论区地址整理为导航站点，方便新参与者快速了解项目全貌。

个人知识管理辅助入口 研究人员可将各类文献数据库、学术搜索引擎、在线工具、数据可视化平台集中管理，结合检索功能快速唤起所需资源。

## 快速开始

以下命令将在本地 8000 端口启动 WebIndex 开发实例，使用 SQLite 作为默认数据存储。

```bash
git clone https://github.com/webindex/webindex-core.git
cd webindex-core
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py loaddata initial_categories.json
python manage.py runserver 0.0.0.0:8000
```

首次启动后，访问 http://127.0.0.1:8000/admin 使用默认管理员账号 admin / admin123 登录，随后可在管理后台执行链接导入。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，3.12 存在部分依赖兼容问题 |
| Django | 4.2.x LTS | Web 框架，用于路由、ORM 及管理后台 |
| SQLite | 3.31 及以上 | 默认数据库，亦支持 PostgreSQL 13+ 用于生产环境 |
| Redis | 6.0 及以上 | 可选，用于缓存分类树与计数统计，提升高并发性能 |
| Node.js | 16.x 或 18.x | 仅用于前端静态资源构建，生产环境可复用已构建产物 |
| uWSGI | 2.0.x | 生产环境部署推荐，与 Nginx 配合使用 |
| Celery | 5.2.x | 用于调度链接探测任务，需配合 Redis 或 RabbitMQ 作为 Broker |
| gunicorn | 20.1.x | 备选 WSGI 服务器，适用于容器化部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quick-start.md | 如何添加第一条链接、如何创建分类、如何调整卡片排序 |
| 运维指南 | /docs/ops/deployment.md | 如何配置 Nginx 反向代理、如何设置定时探测任务、如何备份数据库 |
| 开发者文档 | /docs/dev/api-design.md | 后端 API 路由结构、序列化器规范、自定义标签扩展接口 |
| 设计说明 | /docs/design/ui-ux.md | 卡片尺寸规范、颜色变量定义、响应式断点逻辑 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/423614.htm
- http://m.blog.gqskj.cn/nnews/5969311.htm
- http://m.blog.gqskj.cn/nnews/92179.htm
- http://m.blog.gqskj.cn/nnews/926694.htm
- http://m.blog.gqskj.cn/nnews/309035.htm
- http://m.blog.gqskj.cn/nnews/303798.htm
- http://m.blog.gqskj.cn/nnews/80467.htm
- http://m.blog.gqskj.cn/nnews/4463615.htm
- http://m.blog.gqskj.cn/nnews/9840.htm
- http://m.blog.gqskj.cn/nnews/0434991.htm
- http://m.blog.gqskj.cn/nnews/2283202.htm
- http://m.blog.gqskj.cn/nnews/07547.htm
- http://m.blog.gqskj.cn/nnews/048945.htm
- http://m.blog.gqskj.cn/nnews/37997.htm
- http://m.blog.gqskj.cn/nnews/1766.htm
- http://m.blog.gqskj.cn/nnews/72295.htm
- http://m.blog.gqskj.cn/nnews/7573510.htm
- http://m.blog.gqskj.cn/nnews/09675.htm
- http://m.blog.gqskj.cn/nnews/4705919.htm
- http://m.blog.gqskj.cn/nnews/9581282.htm
- http://m.blog.gqskj.cn/nnews/3115.htm
- http://m.blog.gqskj.cn/nnews/29678.htm
- http://m.blog.gqskj.cn/nnews/505799.htm
- http://m.blog.gqskj.cn/nnews/7357298.htm
- http://m.blog.gqskj.cn/nnews/691934.htm
- http://m.blog.gqskj.cn/nnews/2338.htm
- http://m.blog.gqskj.cn/nnews/69626.htm
- http://m.blog.gqskj.cn/nnews/569067.htm
- http://m.blog.gqskj.cn/nnews/8273835.htm
- http://m.blog.gqskj.cn/nnews/2239733.htm
- http://m.blog.gqskj.cn/nnews/47418.htm
- http://m.blog.gqskj.cn/nnews/8173.htm
- http://m.blog.gqskj.cn/nnews/48390.htm
- http://m.blog.gqskj.cn/nnews/90815.htm
- http://m.blog.gqskj.cn/nnews/38025.htm
- http://m.blog.gqskj.cn/nnews/6797722.htm
- http://m.blog.gqskj.cn/nnews/3337738.htm
- http://m.blog.gqskj.cn/nnews/333631.htm
- http://m.blog.gqskj.cn/nnews/622169.htm
- http://m.blog.gqskj.cn/nnews/129901.htm
- http://m.blog.gqskj.cn/nnews/8006.htm
- http://m.blog.gqskj.cn/nnews/20275.htm
- http://m.blog.gqskj.cn/nnews/1000923.htm
- http://m.blog.gqskj.cn/nnews/6113050.htm
- http://m.blog.gqskj.cn/nnews/30215.htm
- http://m.blog.gqskj.cn/nnews/60642.htm
- http://m.blog.gqskj.cn/nnews/90542.htm
- http://m.blog.gqskj.cn/nnews/0007003.htm
- http://m.blog.gqskj.cn/nnews/19270.htm
- http://m.blog.gqskj.cn/nnews/1048701.htm
- http://m.blog.gqskj.cn/nnews/4335739.htm
- http://m.blog.gqskj.cn/nnews/61176.htm
- http://m.blog.gqskj.cn/nnews/65010.htm
- http://m.blog.gqskj.cn/nnews/7829.htm
- http://m.blog.gqskj.cn/nnews/36459.htm
- http://m.blog.gqskj.cn/nnews/730545.htm
- http://m.blog.gqskj.cn/nnews/4496268.htm
- http://m.blog.gqskj.cn/nnews/918262.htm
- http://m.blog.gqskj.cn/nnews/3925.htm
- http://m.blog.gqskj.cn/nnews/656344.htm
- http://m.blog.gqskj.cn/nnews/8738130.htm
- http://m.blog.gqskj.cn/nnews/4208113.htm
- http://m.blog.gqskj.cn/nnews/26128.htm
- http://m.blog.gqskj.cn/nnews/1254370.htm
- http://m.blog.gqskj.cn/nnews/9397414.htm
- http://m.blog.gqskj.cn/nnews/9092544.htm
- http://m.blog.gqskj.cn/nnews/4539533.htm
- http://m.blog.gqskj.cn/nnews/48414.htm
- http://m.blog.gqskj.cn/nnews/70106.htm
- http://m.blog.gqskj.cn/nnews/729361.htm
- http://m.blog.gqskj.cn/nnews/22067.htm
- http://m.blog.gqskj.cn/nnews/409591.htm
- http://m.blog.gqskj.cn/nnews/93694.htm
- http://m.blog.gqskj.cn/nnews/03182.htm
- http://m.blog.gqskj.cn/nnews/0772.htm
- http://m.blog.gqskj.cn/nnews/9069.htm
- http://m.blog.gqskj.cn/nnews/006036.htm
- http://m.blog.gqskj.cn/nnews/76892.htm
- http://m.blog.gqskj.cn/nnews/827175.htm
- http://m.blog.gqskj.cn/nnews/6644992.htm
- http://m.blog.gqskj.cn/nnews/9371082.htm
- http://m.blog.gqskj.cn/nnews/311840.htm
- http://m.blog.gqskj.cn/nnews/4021053.htm
- http://m.blog.gqskj.cn/nnews/5753.htm
- http://m.blog.gqskj.cn/nnews/05828.htm
- http://m.blog.gqskj.cn/nnews/696912.htm
- http://m.blog.gqskj.cn/nnews/5163.htm
- http://m.blog.gqskj.cn/nnews/78654.htm
- http://m.blog.gqskj.cn/nnews/04533.htm
- http://m.blog.gqskj.cn/nnews/5631180.htm
- http://m.blog.gqskj.cn/nnews/248925.htm
- http://m.blog.gqskj.cn/nnews/995471.htm
- http://m.blog.gqskj.cn/nnews/0986124.htm
- http://m.blog.gqskj.cn/nnews/1325.htm
- http://m.blog.gqskj.cn/nnews/20946.htm
- http://m.blog.gqskj.cn/nnews/9347978.htm
- http://m.blog.gqskj.cn/nnews/54116.htm
- http://m.blog.gqskj.cn/nnews/799983.htm
- http://m.blog.gqskj.cn/nnews/419373.htm
- http://m.blog.gqskj.cn/nnews/8388.htm
- http://m.blog.gqskj.cn/nnews/6917650.htm
- http://m.blog.gqskj.cn/nnews/78014.htm
- http://m.blog.gqskj.cn/nnews/484771.htm
- http://m.blog.gqskj.cn/nnews/4602.htm
- http://m.blog.gqskj.cn/nnews/87617.htm
- http://m.blog.gqskj.cn/nnews/14712.htm
- http://m.blog.gqskj.cn/nnews/1716.htm
- http://m.blog.gqskj.cn/nnews/979167.htm
- http://m.blog.gqskj.cn/nnews/7135.htm
- http://m.blog.gqskj.cn/nnews/26042.htm
- http://m.blog.gqskj.cn/nnews/405207.htm
- http://m.blog.gqskj.cn/nnews/66703.htm
- http://m.blog.gqskj.cn/nnews/8882.htm
- http://m.blog.gqskj.cn/nnews/2345332.htm
- http://m.blog.gqskj.cn/nnews/875869.htm
- http://m.blog.gqskj.cn/nnews/0879030.htm
- http://m.blog.gqskj.cn/nnews/518390.htm
- http://m.blog.gqskj.cn/nnews/3430.htm
- http://m.blog.gqskj.cn/nnews/80262.htm
- http://m.blog.gqskj.cn/nnews/10076.htm
- http://m.blog.gqskj.cn/nnews/530353.htm
- http://m.blog.gqskj.cn/nnews/7244735.htm
- http://m.blog.gqskj.cn/nnews/280719.htm
- http://m.blog.gqskj.cn/nnews/3080.htm
- http://m.blog.gqskj.cn/nnews/0248.htm
- http://m.blog.gqskj.cn/nnews/0935.htm
- http://m.blog.gqskj.cn/nnews/97373.htm
- http://m.blog.gqskj.cn/nnews/2511747.htm
- http://m.blog.gqskj.cn/nnews/9856.htm
- http://m.blog.gqskj.cn/nnews/214755.htm
- http://m.blog.gqskj.cn/nnews/920860.htm
- http://m.blog.gqskj.cn/nnews/134567.htm
- http://m.blog.gqskj.cn/nnews/5149219.htm
- http://m.blog.gqskj.cn/nnews/38814.htm
- http://m.blog.gqskj.cn/nnews/2687200.htm
- http://m.blog.gqskj.cn/nnews/805047.htm
- http://m.blog.gqskj.cn/nnews/3933.htm
- http://m.blog.gqskj.cn/nnews/896316.htm
- http://m.blog.gqskj.cn/nnews/268834.htm
- http://m.blog.gqskj.cn/nnews/9695698.htm
- http://m.blog.gqskj.cn/nnews/67321.htm
- http://m.blog.gqskj.cn/nnews/02884.htm
- http://m.blog.gqskj.cn/nnews/9329.htm
- http://m.blog.gqskj.cn/nnews/359872.htm
- http://m.blog.gqskj.cn/nnews/492981.htm
- http://m.blog.gqskj.cn/nnews/017760.htm
- http://m.blog.gqskj.cn/nnews/9979.htm
- http://m.blog.gqskj.cn/nnews/90035.htm
- http://m.blog.gqskj.cn/nnews/74610.htm
- http://m.blog.gqskj.cn/nnews/6120.htm
- http://m.blog.gqskj.cn/nnews/920032.htm
- http://m.blog.gqskj.cn/nnews/715463.htm
- http://m.blog.gqskj.cn/nnews/2352994.htm
- http://m.blog.gqskj.cn/nnews/8098.htm
- http://m.blog.gqskj.cn/nnews/1120.htm
- http://m.blog.gqskj.cn/nnews/5970.htm
- http://m.blog.gqskj.cn/nnews/75957.htm
- http://m.blog.gqskj.cn/nnews/45775.htm
- http://m.blog.gqskj.cn/nnews/07867.htm
- http://m.blog.gqskj.cn/nnews/0188.htm
- http://m.blog.gqskj.cn/nnews/83806.htm
- http://m.blog.gqskj.cn/nnews/322818.htm
- http://m.blog.gqskj.cn/nnews/004455.htm
- http://m.blog.gqskj.cn/nnews/753503.htm
- http://m.blog.gqskj.cn/nnews/8412.htm
- http://m.blog.gqskj.cn/nnews/74654.htm
- http://m.blog.gqskj.cn/nnews/0099525.htm
- http://m.blog.gqskj.cn/nnews/4204184.htm
- http://m.blog.gqskj.cn/nnews/3464.htm
- http://m.blog.gqskj.cn/nnews/2746404.htm
- http://m.blog.gqskj.cn/nnews/1894.htm
- http://m.blog.gqskj.cn/nnews/19578.htm
- http://m.blog.gqskj.cn/nnews/178135.htm
- http://m.blog.gqskj.cn/nnews/406998.htm
- http://m.blog.gqskj.cn/nnews/7878535.htm
- http://m.blog.gqskj.cn/nnews/8458800.htm
- http://m.blog.gqskj.cn/nnews/991752.htm
- http://m.blog.gqskj.cn/nnews/5451082.htm
- http://m.blog.gqskj.cn/nnews/421578.htm
- http://m.blog.gqskj.cn/nnews/98382.htm
- http://m.blog.gqskj.cn/nnews/96673.htm
- http://m.blog.gqskj.cn/nnews/0844.htm
- http://m.blog.gqskj.cn/nnews/28299.htm
- http://m.blog.gqskj.cn/nnews/26609.htm
- http://m.blog.gqskj.cn/nnews/3952.htm
- http://m.blog.gqskj.cn/nnews/54732.htm
- http://m.blog.gqskj.cn/nnews/0889.htm
- http://m.blog.gqskj.cn/nnews/10527.htm
- http://m.blog.gqskj.cn/nnews/255179.htm
- http://m.blog.gqskj.cn/nnews/264023.htm
- http://m.blog.gqskj.cn/nnews/0150561.htm
- http://m.blog.gqskj.cn/nnews/89365.htm
- http://m.blog.gqskj.cn/nnews/4093.htm
- http://m.blog.gqskj.cn/nnews/0620.htm
- http://m.blog.gqskj.cn/nnews/1641.htm
- http://m.blog.gqskj.cn/nnews/0870628.htm
- http://m.blog.gqskj.cn/nnews/7715.htm
- http://m.blog.gqskj.cn/nnews/761540.htm
- http://m.blog.gqskj.cn/nnews/68661.htm
- http://m.blog.gqskj.cn/nnews/202506.htm
- http://m.blog.gqskj.cn/nnews/00699.htm
- http://m.blog.gqskj.cn/nnews/29359.htm
- http://m.blog.gqskj.cn/nnews/4124523.htm
- http://m.blog.gqskj.cn/nnews/99756.htm
- http://m.blog.gqskj.cn/nnews/3821479.htm
- http://m.blog.gqskj.cn/nnews/2203120.htm
- http://m.blog.gqskj.cn/nnews/6106083.htm
- http://m.blog.gqskj.cn/nnews/1377.htm
- http://m.blog.gqskj.cn/nnews/70866.htm
- http://m.blog.gqskj.cn/nnews/492867.htm
- http://m.blog.gqskj.cn/nnews/50383.htm
- http://m.blog.gqskj.cn/nnews/163561.htm
- http://m.blog.gqskj.cn/nnews/703757.htm
- http://m.blog.gqskj.cn/nnews/94746.htm
- http://m.blog.gqskj.cn/nnews/24972.htm
- http://m.blog.gqskj.cn/nnews/1596.htm
- http://m.blog.gqskj.cn/nnews/581810.htm
- http://m.blog.gqskj.cn/nnews/5737.htm
- http://m.blog.gqskj.cn/nnews/6199665.htm
- http://m.blog.gqskj.cn/nnews/418093.htm
- http://m.blog.gqskj.cn/nnews/065740.htm
- http://m.blog.gqskj.cn/nnews/030699.htm
- http://m.blog.gqskj.cn/nnews/685706.htm
- http://m.blog.gqskj.cn/nnews/1125979.htm
- http://m.blog.gqskj.cn/nnews/320590.htm
- http://m.blog.gqskj.cn/nnews/6360.htm
- http://m.blog.gqskj.cn/nnews/995570.htm
- http://m.blog.gqskj.cn/nnews/8256569.htm
- http://m.blog.gqskj.cn/nnews/505547.htm
- http://m.blog.gqskj.cn/nnews/158487.htm
- http://m.blog.gqskj.cn/nnews/5544.htm
- http://m.blog.gqskj.cn/nnews/7304224.htm
- http://m.blog.gqskj.cn/nnews/615283.htm
- http://m.blog.gqskj.cn/nnews/951609.htm
- http://m.blog.gqskj.cn/nnews/1135.htm
- http://m.blog.gqskj.cn/nnews/7309537.htm
- http://m.blog.gqskj.cn/nnews/9288968.htm
- http://m.blog.gqskj.cn/nnews/8564.htm
- http://m.blog.gqskj.cn/nnews/44553.htm
- http://m.blog.gqskj.cn/nnews/28906.htm
- http://m.blog.gqskj.cn/nnews/498790.htm
- http://m.blog.gqskj.cn/nnews/3359507.htm
- http://m.blog.gqskj.cn/nnews/4027.htm
- http://m.blog.gqskj.cn/nnews/3129287.htm
- http://m.blog.gqskj.cn/nnews/8087315.htm
- http://m.blog.gqskj.cn/nnews/0678628.htm
- http://m.blog.gqskj.cn/nnews/772632.htm
- http://m.blog.gqskj.cn/nnews/2719.htm
- http://m.blog.gqskj.cn/nnews/8322.htm
- http://m.blog.gqskj.cn/nnews/423495.htm

## 项目结构

```
webindex-core/
├── backend/                         # Django 后端核心代码
│   ├── apps/
│   │   ├── links/                   # 链接管理模块，包含模型、序列化器与视图
│   │   │   ├── models.py            # Link, Category, Tag, ClickLog 定义
│   │   │   ├── serializers.py       # 链接导入导出序列化逻辑
│   │   │   └── tasks.py             # 链接可用性探测 Celery 任务
│   │   ├── users/                   # 用户认证与权限模块
│   │   │   ├── auth.py              # JWT 与 Session 双重认证适配
│   │   │   └── permissions.py       # 基于角色的分类编辑权限
│   │   └── search/                  # 搜索模块，基于 SQLite FTS5 或 PostgreSQL 全文检索
│   │       └── indexes.py           # 索引构建与查询分词配置
│   ├── core/                        # 项目配置与通用工具
│   │   ├── settings/                # 环境拆分配置（development, production, testing）
│   │   ├── celery.py                # Celery 应用实例与周期性任务注册
│   │   └── storage.py               # 自定义存储后端（本地文件 / S3 兼容）
│   └── manage.py                    # Django 管理入口
├── frontend/                        # 前端静态资源（非构建型，原生 JS + CSS）
│   ├── assets/
│   │   ├── css/
│   │   │   ├── grid.css             # 卡片栅格系统与响应式断点
│   │   │   └── theme.css            # CSS 变量定义与暗色模式适配
│   │   ├── js/
│   │   │   ├── router.js            # 前端无刷新路由与 History API 控制
│   │   │   ├── fetch.js             # 封装后端 API 请求与错误处理
│   │   │   └── widgets.js           # 搜索框、分类树、点击计数更新组件
│   │   └── images/                  # 默认图标与占位图
│   └── templates/                   # Django 模板文件
│       └── index.html               # 单页入口，包含骨架结构与初始化脚本
├── scripts/                         # 运维与数据迁移辅助脚本
│   ├── batch_import.py              # 从 CSV / JSON 批量导入链接
│   ├── health_check.py              # 手动触发全量链接探测
│   └── export_static.sh             # 构建并导出完全静态 HTML 版本
├── tests/                           # 单元测试与集成测试
│   ├── test_models.py               # 模型字段约束与信号测试
│   ├── test_api.py                  # API 路由响应与权限测试
│   └── test_tasks.py                # Celery 任务执行与重试逻辑测试
├── docs/                            # 完整文档目录（对应文档导航章节）
├── requirements.txt                 # Python 依赖列表
├── .env.example                     # 环境变量示例（数据库 URL、Redis 地址、密钥）
├── docker-compose.yml               # 本地开发容器编排（PostgreSQL + Redis + app）
├── Dockerfile                       # 多阶段构建镜像定义
└── README.md                        # 本文件
```

## 贡献指南

提交问题报告与功能请求 请在 GitHub Issues 中使用提供的模板填写，明确标注复现步骤、环境信息及期望行为。对于功能请求，需说明使用场景与预期收益。

代码提交规范 所有 Pull Request 必须基于 develop 分支创建，提交信息遵循 Conventional Commits 格式（feat / fix / docs / refactor / test / chore）。每次提交前需确保现有单元测试通过，并为新增功能补充对应测试用例。

本地开发环境准备 克隆仓库后，执行 scripts/setup_dev.sh 脚本自动安装依赖、初始化数据库并加载示例数据。推荐使用 Python 虚拟环境或 Docker Compose 一键启动整套依赖服务。

文档补充要求 任何新增 API 接口或配置项，必须同步更新 /docs 目录下的对应文档，并在 Pull Request 描述中列出文档变更路径。

审查与合并流程 至少需一位项目维护者批准后方可合并。对于破坏性变更或数据结构调整，需在 PR 中提供迁移计划与回滚方案。

## 常见问题

Q: 导入大量链接时页面响应缓慢，如何优化？

A: 建议通过命令行脚本 scripts/batch_import.py 进行异步导入，该脚本会绕过 HTTP 请求限制直接操作数据库。若需通过 Web 界面导入，单次建议不超过 200 条，并确保 Redis 缓存已开启。此外，可调整 Django 的 DATA_UPLOAD_MAX_NUMBER_FIELDS 配置以适应大表单提交。

Q: 链接可用性探测任务未按预期执行，如何排查？

A: 首先检查 Celery Worker 是否正常运行，执行 celery -A core status 查看节点状态。其次确认 Redis 或 RabbitMQ 服务可达。若任务处于 pending 状态，检查 beat_schedule 配置中的 crontab 表达式是否正确。探测任务日志位于 logs/health_check.log，可查看具体超时或拒绝连接的域名。

Q: 如何将现有浏览器书签导入 WebIndex？

A: 目前支持从 Chrome 或 Firefox 导出的 HTML 书签文件（Bookmarks.html）进行转换。使用 scripts/convert_bookmarks.py --input bookmarks.html --output links.json 生成中间文件，再通过后台管理界面的导入功能上传该 JSON。若需保留原始文件夹层级结构，可在导入时勾选“自动创建分类”选项。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:36
