# WebLink Navigator

WebLink Navigator 是一个轻量级的技术资源导航与外部链接聚合服务，专注于将分散于各类技术博客、新闻资讯、文档站点中的优质外链进行结构化收录与分类展示。该项目面向开发者、技术研究者以及内容策展人，帮助其从海量信息中快速定位具有参考价值的文章、工具与案例。

项目核心定位为"链接即数据"，通过标准化的 URL 收录流程、标签化分类机制以及简洁的浏览界面，降低技术信息的发现成本。WebLink Navigator 不生产内容，而是通过人工筛选与社区贡献相结合的方式，维护一份高信噪比的外链索引表。当前批次为第 214/240 批，共计收录 250 个资源链接，覆盖技术博客、行业动态、开发工具、学术论文等多个子类。

## 功能概览

**链接收录与持久化存储** 系统提供标准化的 URL 录入接口，支持单条添加与批量导入，所有链接以纯文本形式持久化存储，确保数据不丢失。

**分类标签与模糊检索** 每条链接可关联多个自定义标签，支持按标签筛选、按关键词模糊匹配标题与描述，帮助用户快速缩小查找范围。

**访问状态健康检查** 内置定时任务对已收录链接进行 HTTP 状态码检测，自动标记失效链接（404、500 等），并生成异常报告供管理员处理。

**浏览计数与热度排序** 记录每条链接的点击次数，支持按热度、收录时间、字母序等多种方式排序，突出高频访问资源。

**Markdown 格式数据导出** 支持将当前筛选结果或全量数据导出为 Markdown 列表格式，便于嵌入其他文档或静态站点生成器。

**响应式 Web 管理界面** 基于 Bootstrap 构建的管理后台适配桌面与移动设备，支持链接的增删改查、标签管理、批量操作等日常维护任务。

**开放 API 接口** 提供 RESTful API 用于第三方工具集成，支持链接查询、新增、状态更新等操作，方便构建自动化工作流。

## 应用场景

**技术团队内部知识库建设** 开发团队可将日常阅读中发现的优秀技术文章、开源项目、调试工具等链接统一收录至 WebLink Navigator，形成团队共享的知识索引，减少重复搜索时间。

**个人开发者学习路径管理** 独立开发者可利用本系统整理不同技术栈的学习资料，按阶段（入门、进阶、实战）打标签，构建清晰的学习路线图，避免收藏夹杂乱无章。

**技术社区内容聚合与推荐** 技术社区运营方可基于 WebLink Navigator 搭建外链推荐板块，由社区成员共同提交优质内容，经审核后展示，提升社区内容生态的丰富度。

**技术文档站点的参考链接附录** 开源项目文档或技术书籍的配套站点可使用本系统管理"延伸阅读"或"参考资料"章节的外链，确保链接可维护、可更新，避免文档中死链过多。

## 快速开始

以下步骤帮助您在本地环境中快速启动 WebLink Navigator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装依赖（基于 Python 3.10 + pip）
pip install -r requirements.txt

# 初始化数据库（SQLite）
python scripts/init_db.py

# 启动开发服务器
python app.py runserver --host=0.0.0.0 --port=8080
```

启动成功后，访问 http://localhost:8080 即可进入管理界面。默认管理员账户为 admin，密码在首次启动时由初始化脚本生成并打印在终端日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10.x 或 3.11.x | 核心运行环境，低于 3.10 将导致类型注解语法错误 |
| SQLite | 3.35.0 及以上 | 内置数据库，用于存储链接元数据与标签关系 |
| Flask | 2.2.3 及以上 | Web 框架，提供路由、模板渲染及请求处理能力 |
| requests | 2.28.0 及以上 | 用于链接健康检查中的 HTTP 请求发送 |
| APScheduler | 3.10.0 及以上 | 定时任务调度器，驱动链接状态巡检 |
| gunicorn | 20.1.0 及以上 | 生产环境推荐部署的 WSGI 服务器（Linux 环境） |
| nodejs | 18.x 及以上 | 仅当需要构建前端资源时必需，开发环境可选 |
| npm | 9.x 及以上 | 配合 nodejs 管理前端构建工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何浏览链接、使用搜索与筛选、查看链接详情？ |
| 管理员手册 | /docs/admin-guide.md | 如何添加/编辑/删除链接、管理标签、查看健康报告？ |
| API 参考 | /docs/api-reference.md | 对外开放了哪些接口、请求参数与响应格式是什么？ |
| 部署指南 | /docs/deployment.md | 如何在 Linux 服务器上使用 gunicorn + nginx 部署生产环境？ |
| 贡献规范 | /docs/contributing.md | 外部贡献者如何提交新链接、如何报告失效链接、代码提交流程？ |
| 设计说明 | /docs/design.md | 数据库表结构设计、定时任务机制、前端交互逻辑的决策依据 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/4683.htm
- http://m.blog.gqskj.cn/nnews/6583.htm
- http://m.blog.gqskj.cn/nnews/9775421.htm
- http://m.blog.gqskj.cn/nnews/3741.htm
- http://m.blog.gqskj.cn/nnews/9083377.htm
- http://m.blog.gqskj.cn/nnews/76932.htm
- http://m.blog.gqskj.cn/nnews/76222.htm
- http://m.blog.gqskj.cn/nnews/99402.htm
- http://m.blog.gqskj.cn/nnews/5816466.htm
- http://m.blog.gqskj.cn/nnews/5010992.htm
- http://m.blog.gqskj.cn/nnews/5884310.htm
- http://m.blog.gqskj.cn/nnews/18011.htm
- http://m.blog.gqskj.cn/nnews/62561.htm
- http://m.blog.gqskj.cn/nnews/1147217.htm
- http://m.blog.gqskj.cn/nnews/82430.htm
- http://m.blog.gqskj.cn/nnews/55100.htm
- http://m.blog.gqskj.cn/nnews/26954.htm
- http://m.blog.gqskj.cn/nnews/3351246.htm
- http://m.blog.gqskj.cn/nnews/33952.htm
- http://m.blog.gqskj.cn/nnews/9031349.htm
- http://m.blog.gqskj.cn/nnews/1486.htm
- http://m.blog.gqskj.cn/nnews/4504469.htm
- http://m.blog.gqskj.cn/nnews/452935.htm
- http://m.blog.gqskj.cn/nnews/94826.htm
- http://m.blog.gqskj.cn/nnews/6561.htm
- http://m.blog.gqskj.cn/nnews/006061.htm
- http://m.blog.gqskj.cn/nnews/7352295.htm
- http://m.blog.gqskj.cn/nnews/551303.htm
- http://m.blog.gqskj.cn/nnews/2965627.htm
- http://m.blog.gqskj.cn/nnews/58519.htm
- http://m.blog.gqskj.cn/nnews/786885.htm
- http://m.blog.gqskj.cn/nnews/651398.htm
- http://m.blog.gqskj.cn/nnews/22116.htm
- http://m.blog.gqskj.cn/nnews/08867.htm
- http://m.blog.gqskj.cn/nnews/12998.htm
- http://m.blog.gqskj.cn/nnews/6534877.htm
- http://m.blog.gqskj.cn/nnews/8340.htm
- http://m.blog.gqskj.cn/nnews/9905.htm
- http://m.blog.gqskj.cn/nnews/9641.htm
- http://m.blog.gqskj.cn/nnews/67745.htm
- http://m.blog.gqskj.cn/nnews/073479.htm
- http://m.blog.gqskj.cn/nnews/2214851.htm
- http://m.blog.gqskj.cn/nnews/2317079.htm
- http://m.blog.gqskj.cn/nnews/1465469.htm
- http://m.blog.gqskj.cn/nnews/95180.htm
- http://m.blog.gqskj.cn/nnews/6474.htm
- http://m.blog.gqskj.cn/nnews/9465.htm
- http://m.blog.gqskj.cn/nnews/836312.htm
- http://m.blog.gqskj.cn/nnews/58157.htm
- http://m.blog.gqskj.cn/nnews/0189205.htm
- http://m.blog.gqskj.cn/nnews/28397.htm
- http://m.blog.gqskj.cn/nnews/2000.htm
- http://m.blog.gqskj.cn/nnews/535943.htm
- http://m.blog.gqskj.cn/nnews/4801037.htm
- http://m.blog.gqskj.cn/nnews/13609.htm
- http://m.blog.gqskj.cn/nnews/2428464.htm
- http://m.blog.gqskj.cn/nnews/5372.htm
- http://m.blog.gqskj.cn/nnews/1240036.htm
- http://m.blog.gqskj.cn/nnews/3658088.htm
- http://m.blog.gqskj.cn/nnews/991915.htm
- http://m.blog.gqskj.cn/nnews/1091778.htm
- http://m.blog.gqskj.cn/nnews/3735457.htm
- http://m.blog.gqskj.cn/nnews/0881.htm
- http://m.blog.gqskj.cn/nnews/24798.htm
- http://m.blog.gqskj.cn/nnews/7658.htm
- http://m.blog.gqskj.cn/nnews/64141.htm
- http://m.blog.gqskj.cn/nnews/4070.htm
- http://m.blog.gqskj.cn/nnews/0792702.htm
- http://m.blog.gqskj.cn/nnews/25194.htm
- http://m.blog.gqskj.cn/nnews/8625.htm
- http://m.blog.gqskj.cn/nnews/3139195.htm
- http://m.blog.gqskj.cn/nnews/09247.htm
- http://m.blog.gqskj.cn/nnews/1737169.htm
- http://m.blog.gqskj.cn/nnews/291425.htm
- http://m.blog.gqskj.cn/nnews/134261.htm
- http://m.blog.gqskj.cn/nnews/3567.htm
- http://m.blog.gqskj.cn/nnews/124094.htm
- http://m.blog.gqskj.cn/nnews/97849.htm
- http://m.blog.gqskj.cn/nnews/2832.htm
- http://m.blog.gqskj.cn/nnews/9931362.htm
- http://m.blog.gqskj.cn/nnews/3274.htm
- http://m.blog.gqskj.cn/nnews/3029.htm
- http://m.blog.gqskj.cn/nnews/005563.htm
- http://m.blog.gqskj.cn/nnews/0804335.htm
- http://m.blog.gqskj.cn/nnews/1272089.htm
- http://m.blog.gqskj.cn/nnews/23585.htm
- http://m.blog.gqskj.cn/nnews/6911.htm
- http://m.blog.gqskj.cn/nnews/824062.htm
- http://m.blog.gqskj.cn/nnews/868784.htm
- http://m.blog.gqskj.cn/nnews/401374.htm
- http://m.blog.gqskj.cn/nnews/9442869.htm
- http://m.blog.gqskj.cn/nnews/0905.htm
- http://m.blog.gqskj.cn/nnews/9893.htm
- http://m.blog.gqskj.cn/nnews/93138.htm
- http://m.blog.gqskj.cn/nnews/4081.htm
- http://m.blog.gqskj.cn/nnews/6272845.htm
- http://m.blog.gqskj.cn/nnews/09780.htm
- http://m.blog.gqskj.cn/nnews/2342.htm
- http://m.blog.gqskj.cn/nnews/6514.htm
- http://m.blog.gqskj.cn/nnews/505500.htm
- http://m.blog.gqskj.cn/nnews/98850.htm
- http://m.blog.gqskj.cn/nnews/42346.htm
- http://m.blog.gqskj.cn/nnews/798882.htm
- http://m.blog.gqskj.cn/nnews/5556087.htm
- http://m.blog.gqskj.cn/nnews/9662.htm
- http://m.blog.gqskj.cn/nnews/0303643.htm
- http://m.blog.gqskj.cn/nnews/713826.htm
- http://m.blog.gqskj.cn/nnews/846297.htm
- http://m.blog.gqskj.cn/nnews/80787.htm
- http://m.blog.gqskj.cn/nnews/921906.htm
- http://m.blog.gqskj.cn/nnews/664747.htm
- http://m.blog.gqskj.cn/nnews/6211813.htm
- http://m.blog.gqskj.cn/nnews/7173911.htm
- http://m.blog.gqskj.cn/nnews/8706.htm
- http://m.blog.gqskj.cn/nnews/2309.htm
- http://m.blog.gqskj.cn/nnews/1173.htm
- http://m.blog.gqskj.cn/nnews/4736400.htm
- http://m.blog.gqskj.cn/nnews/0640521.htm
- http://m.blog.gqskj.cn/nnews/5068285.htm
- http://m.blog.gqskj.cn/nnews/1207.htm
- http://m.blog.gqskj.cn/nnews/270389.htm
- http://m.blog.gqskj.cn/nnews/632741.htm
- http://m.blog.gqskj.cn/nnews/4225566.htm
- http://m.blog.gqskj.cn/nnews/4274655.htm
- http://m.blog.gqskj.cn/nnews/0605289.htm
- http://m.blog.gqskj.cn/nnews/8524.htm
- http://m.blog.gqskj.cn/nnews/6910.htm
- http://m.blog.gqskj.cn/nnews/19543.htm
- http://m.blog.gqskj.cn/nnews/37156.htm
- http://m.blog.gqskj.cn/nnews/50619.htm
- http://m.blog.gqskj.cn/nnews/716511.htm
- http://m.blog.gqskj.cn/nnews/0998364.htm
- http://m.blog.gqskj.cn/nnews/16241.htm
- http://m.blog.gqskj.cn/nnews/0726.htm
- http://m.blog.gqskj.cn/nnews/0109.htm
- http://m.blog.gqskj.cn/nnews/819450.htm
- http://m.blog.gqskj.cn/nnews/4264.htm
- http://m.blog.gqskj.cn/nnews/112444.htm
- http://m.blog.gqskj.cn/nnews/827324.htm
- http://m.blog.gqskj.cn/nnews/4619.htm
- http://m.blog.gqskj.cn/nnews/0198135.htm
- http://m.blog.gqskj.cn/nnews/519016.htm
- http://m.blog.gqskj.cn/nnews/7277.htm
- http://m.blog.gqskj.cn/nnews/48488.htm
- http://m.blog.gqskj.cn/nnews/05603.htm
- http://m.blog.gqskj.cn/nnews/8142908.htm
- http://m.blog.gqskj.cn/nnews/359734.htm
- http://m.blog.gqskj.cn/nnews/644744.htm
- http://m.blog.gqskj.cn/nnews/929012.htm
- http://m.blog.gqskj.cn/nnews/63837.htm
- http://m.blog.gqskj.cn/nnews/508866.htm
- http://m.blog.gqskj.cn/nnews/703900.htm
- http://m.blog.gqskj.cn/nnews/67499.htm
- http://m.blog.gqskj.cn/nnews/2596627.htm
- http://m.blog.gqskj.cn/nnews/493918.htm
- http://m.blog.gqskj.cn/nnews/577053.htm
- http://m.blog.gqskj.cn/nnews/5926.htm
- http://m.blog.gqskj.cn/nnews/6556500.htm
- http://m.blog.gqskj.cn/nnews/923000.htm
- http://m.blog.gqskj.cn/nnews/62625.htm
- http://m.blog.gqskj.cn/nnews/84740.htm
- http://m.blog.gqskj.cn/nnews/3590396.htm
- http://m.blog.gqskj.cn/nnews/871985.htm
- http://m.blog.gqskj.cn/nnews/83906.htm
- http://m.blog.gqskj.cn/nnews/3359.htm
- http://m.blog.gqskj.cn/nnews/659712.htm
- http://m.blog.gqskj.cn/nnews/73362.htm
- http://m.blog.gqskj.cn/nnews/9283.htm
- http://m.blog.gqskj.cn/nnews/6506.htm
- http://m.blog.gqskj.cn/nnews/439364.htm
- http://m.blog.gqskj.cn/nnews/8681251.htm
- http://m.blog.gqskj.cn/nnews/8163466.htm
- http://m.blog.gqskj.cn/nnews/63471.htm
- http://m.blog.gqskj.cn/nnews/48078.htm
- http://m.blog.gqskj.cn/nnews/2255.htm
- http://m.blog.gqskj.cn/nnews/5830.htm
- http://m.blog.gqskj.cn/nnews/026514.htm
- http://m.blog.gqskj.cn/nnews/7157032.htm
- http://m.blog.gqskj.cn/nnews/4186539.htm
- http://m.blog.gqskj.cn/nnews/470587.htm
- http://m.blog.gqskj.cn/nnews/994059.htm
- http://m.blog.gqskj.cn/nnews/2845699.htm
- http://m.blog.gqskj.cn/nnews/6429186.htm
- http://m.blog.gqskj.cn/nnews/22629.htm
- http://m.blog.gqskj.cn/nnews/60473.htm
- http://m.blog.gqskj.cn/nnews/4951.htm
- http://m.blog.gqskj.cn/nnews/075706.htm
- http://m.blog.gqskj.cn/nnews/1220826.htm
- http://m.blog.gqskj.cn/nnews/319039.htm
- http://m.blog.gqskj.cn/nnews/5022.htm
- http://m.blog.gqskj.cn/nnews/329985.htm
- http://m.blog.gqskj.cn/nnews/97111.htm
- http://m.blog.gqskj.cn/nnews/514754.htm
- http://m.blog.gqskj.cn/nnews/6526900.htm
- http://m.blog.gqskj.cn/nnews/6806500.htm
- http://m.blog.gqskj.cn/nnews/1014.htm
- http://m.blog.gqskj.cn/nnews/6812.htm
- http://m.blog.gqskj.cn/nnews/801221.htm
- http://m.blog.gqskj.cn/nnews/10326.htm
- http://m.blog.gqskj.cn/nnews/04926.htm
- http://m.blog.gqskj.cn/nnews/83525.htm
- http://m.blog.gqskj.cn/nnews/5495.htm
- http://m.blog.gqskj.cn/nnews/320517.htm
- http://m.blog.gqskj.cn/nnews/69178.htm
- http://m.blog.gqskj.cn/nnews/067908.htm
- http://m.blog.gqskj.cn/nnews/2651703.htm
- http://m.blog.gqskj.cn/nnews/47238.htm
- http://m.blog.gqskj.cn/nnews/01584.htm
- http://m.blog.gqskj.cn/nnews/96759.htm
- http://m.blog.gqskj.cn/nnews/275776.htm
- http://m.blog.gqskj.cn/nnews/3993742.htm
- http://m.blog.gqskj.cn/nnews/307875.htm
- http://m.blog.gqskj.cn/nnews/283808.htm
- http://m.blog.gqskj.cn/nnews/942717.htm
- http://m.blog.gqskj.cn/nnews/73971.htm
- http://m.blog.gqskj.cn/nnews/554014.htm
- http://m.blog.gqskj.cn/nnews/40337.htm
- http://m.blog.gqskj.cn/nnews/63274.htm
- http://m.blog.gqskj.cn/nnews/81208.htm
- http://m.blog.gqskj.cn/nnews/485296.htm
- http://m.blog.gqskj.cn/nnews/95526.htm
- http://m.blog.gqskj.cn/nnews/4076451.htm
- http://m.blog.gqskj.cn/nnews/8481407.htm
- http://m.blog.gqskj.cn/nnews/2539008.htm
- http://m.blog.gqskj.cn/nnews/82573.htm
- http://m.blog.gqskj.cn/nnews/0815.htm
- http://m.blog.gqskj.cn/nnews/3555.htm
- http://m.blog.gqskj.cn/nnews/10416.htm
- http://m.blog.gqskj.cn/nnews/297998.htm
- http://m.blog.gqskj.cn/nnews/7197.htm
- http://m.blog.gqskj.cn/nnews/0292.htm
- http://m.blog.gqskj.cn/nnews/78133.htm
- http://m.blog.gqskj.cn/nnews/789303.htm
- http://m.blog.gqskj.cn/nnews/1746.htm
- http://m.blog.gqskj.cn/nnews/586974.htm
- http://m.blog.gqskj.cn/nnews/2263.htm
- http://m.blog.gqskj.cn/nnews/69852.htm
- http://m.blog.gqskj.cn/nnews/83601.htm
- http://m.blog.gqskj.cn/nnews/9092.htm
- http://m.blog.gqskj.cn/nnews/930074.htm
- http://m.blog.gqskj.cn/nnews/5796924.htm
- http://m.blog.gqskj.cn/nnews/6669418.htm
- http://m.blog.gqskj.cn/nnews/78626.htm
- http://m.blog.gqskj.cn/nnews/530980.htm
- http://m.blog.gqskj.cn/nnews/7490.htm
- http://m.blog.gqskj.cn/nnews/8886496.htm
- http://m.blog.gqskj.cn/nnews/0438882.htm
- http://m.blog.gqskj.cn/nnews/9901236.htm
- http://m.blog.gqskj.cn/nnews/9139.htm
- http://m.blog.gqskj.cn/nnews/5290.htm

## 项目结构

```
weblink-navigator/
├── app/
│   ├── __init__.py               # Flask 应用工厂，注册蓝图与扩展
│   ├── routes/
│   │   ├── __init__.py           # 路由聚合，导入各模块路由
│   │   ├── link.py               # 链接 CRUD 相关路由（增删改查、批量操作）
│   │   ├── tag.py                # 标签管理路由（新增、重命名、合并、删除）
│   │   ├── health.py             # 健康检查报告查看与手动触发路由
│   │   └── api.py                # RESTful API 端点（查询、新增、状态更新）
│   ├── models/
│   │   ├── __init__.py           # 数据模型导入与 ORM 初始化
│   │   ├── link.py               # Link 模型定义（url, title, description, status_code, click_count）
│   │   ├── tag.py                # Tag 模型定义（name, slug, created_at）
│   │   └── link_tag.py           # 链接-标签多对多关联表模型
│   ├── services/
│   │   ├── __init__.py           # 服务层导入
│   │   ├── health_checker.py     # 链接状态检测服务（并发请求、超时处理、状态更新）
│   │   ├── scheduler.py          # APScheduler 配置与定时任务注册（每小时巡检）
│   │   └── exporter.py           # 数据导出服务（Markdown 列表、JSON 格式）
│   ├── templates/
│   │   ├── base.html             # 基础模板，包含导航栏与页脚
│   │   ├── index.html            # 首页，展示搜索框、标签云、最新链接列表
│   │   ├── link_list.html        # 链接列表页，支持分页与排序切换
│   │   ├── link_detail.html      # 链接详情页，展示完整元数据与点击跳转
│   │   ├── link_edit.html        # 链接新增/编辑表单页面
│   │   └── health_report.html    # 健康检查报告页面（异常链接列表与统计）
│   └── static/
│       ├── css/
│       │   └── style.css         # 自定义样式覆盖（Bootstrap 主题调整）
│       └── js/
│           └── main.js           # 前端交互逻辑（表单验证、实时搜索、分页控制）
├── scripts/
│   ├── init_db.py                # 数据库初始化脚本（建表、创建默认标签、管理员账户）
│   └── import_links.py           # 批量导入链接脚本（从 CSV 或纯文本文件读取）
├── tests/
│   ├── test_models.py            # 数据模型单元测试（增删改查、关联操作）
│   ├── test_routes.py            # 路由功能测试（状态码、重定向、表单提交）
│   └── test_health_checker.py    # 健康检查服务测试（模拟 HTTP 响应）
├── config/
│   ├── __init__.py               # 配置类导入
│   ├── development.py            # 开发环境配置（DEBUG=True, SQLite 路径）
│   └── production.py             # 生产环境配置（DEBUG=False, 可配置 PostgreSQL URI）
├── logs/
│   └── app.log                   # 应用日志文件（包含请求日志、错误追踪、定时任务执行记录）
├── requirements.txt              # Python 依赖清单（Flask, requests, APScheduler, pytest 等）
├── .env.example                  # 环境变量示例（SECRET_KEY, DATABASE_URL, SCHEDULER_INTERVAL）
├── .gitignore                    # Git 忽略文件配置（排除日志、本地数据库、虚拟环境）
├── README.md                     # 项目说明文档（即本文档）
├── LICENSE                       # MIT 许可证全文
└── docker-compose.yml            # Docker Compose 编排文件（用于快速部署全套服务）
```

## 贡献指南

**提交新链接** 通过管理界面或 API 提交您认为具有技术参考价值的 URL，需提供标题、简要描述及至少一个分类标签。提交后链接状态默认为"待审核"，经维护者确认后正式收录。

**报告失效链接** 若发现已收录链接返回 404、超时或跳转至无关页面，请通过 GitHub Issues 提交失效报告，附上链接 ID 或完整 URL。系统健康检查也会自动标记，但人工反馈可加速处理。

**改进代码或文档** Fork 本仓库，在本地分支进行修改，确保所有单元测试通过后提交 Pull Request。代码请遵循 PEP 8 规范，文档更新请同步修改 /docs 目录下对应文件。

**参与标签体系优化** 若发现标签命名不清晰或存在冗余，可提交标签合并或重命名建议。标签体系的设计原则是"一个概念，一个标签"，避免同义词并存。

**本地测试与验证** 在提交 Pull Request 前，请运行 pytest 执行全部测试用例，并手动验证管理界面核心流程（新增、编辑、删除、搜索）运行正常。

## 常见问题

**Q: 系统支持哪些数据库后端？**

默认使用 SQLite 以降低部署门槛，生产环境可切换至 PostgreSQL 或 MySQL。只需修改环境变量 DATABASE_URL，系统会自动适配对应的 SQLAlchemy 方言。迁移现有数据时请使用 scripts/export_links.py 导出为 JSON 后再导入新库。

**Q: 链接健康检查的频率是多少？是否会频繁请求目标站点导致被屏蔽？**

默认每小时执行一次全量巡检，并发请求数限制为 10 个，超时时间设为 5 秒，避免对目标服务器造成压力。若目标站点有反爬机制，可在配置文件中调整 USER_AGENT 或增加请求间隔。对于明确返回 429 状态码的站点，系统会将其加入临时冷却名单，24 小时内不再检测。

**Q: 如何将现有收藏夹（书签）批量导入系统？**

支持导入 Netscape 格式的 HTML 书签导出文件（多数浏览器支持此格式），以及纯文本 URL 列表（每行一个 URL）。使用 scripts/import_links.py 并指定 --format 参数即可完成导入。导入后需手动补充标题和标签，系统会根据 URL 中的域名自动生成推荐标签。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:35
