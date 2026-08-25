# LinkVault 外链资源聚合系统

LinkVault 是一个面向技术内容创作者、SEO 研究人员和数字营销从业者的外链资源聚合与导航工具。该项目定位于对分散在各类资讯站点中的深层页面进行结构化收录、分类索引与周期性可用性检测，解决人工维护书签效率低下、链接失效无法感知、检索困难等实际问题。通过统一入口对大批量外链资源进行集中管理，帮助用户快速定位特定 ID 或主题相关的历史资讯页面，提升信息复用效率。

## 功能概览

批量链接导入与自动规范化 支持从文本文件、CSV 或直接粘贴的原始链接列表中批量导入 URL，系统自动识别协议头并执行格式校验。

自定义标签与分类体系 用户可为每条链接附加多级标签（如“行业动态”“技术文档”“案例研究”），并基于标签树进行快速筛选。

链接存活状态监控 内置定时任务（默认每 24 小时）对全部收录链接发起 HEAD 请求，检测 HTTP 状态码，标记异常链接并生成报表。

全文元数据提取 对可访问的链接页面自动抽取标题、描述、发布时间等元信息，支持对历史内容进行离线检索。

高级筛选与模糊检索 支持按链接 ID、域名、状态码、标签组合、更新时间范围等多条件联合查询，检索结果支持导出为 JSON 或 CSV。

收藏与备注系统 用户可为任意链接添加个人备注、星级评分及收藏标记，便于团队协作或私有知识库构建。

开放 RESTful API 所有核心功能通过 JSON API 暴露，支持第三方系统集成，便于将外链资源导入到其他分析工具中。

## 应用场景

内容运营团队的历史素材回溯 运营人员在策划专题时，通过 LinkVault 按 ID 范围或发布时间检索收录的历史资讯链接，快速获取背景素材与参考案例，避免重复搜索。

SEO 外链质量审计 网站管理员定期导出全量外链清单，结合状态监控功能批量检查外部站点是否仍有效，及时发现并处理 404 或降权页面，维护搜索引擎评价。

技术研究人员的文献管理 研究人员可将分散在多个资讯站点的技术文章链接统一收录，利用标签和备注功能进行分类整理，在撰写综述或报告时高效引用。

私有化书签服务 个人用户可将本系统部署为私有的云端书签管理工具，无论在何处工作，均可通过 Web 界面访问自己长期积累的链接库，不受浏览器同步限制。

## 快速开始

以下步骤指导您在本地环境快速启动 LinkVault 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkvault.git

# 进入项目目录
cd linkvault

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库
python scripts/init_db.py

# 导入示例链接列表（使用提供的原始数据）
python scripts/import_links.py --file samples/links_216.txt

# 启动开发服务器
python app.py
```

服务启动后将监听 `http://127.0.0.1:5000`，访问该地址即可进入 LinkVault 仪表板。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，低于此版本不支持类型注解语法 |
| SQLite | 3.35 及以上 | 内置数据库，用于存储链接元数据及标签体系 |
| requests | 2.31.0 | 处理 HTTP 请求，用于链接存活检测与元数据抓取 |
| flask | 2.3.0 | Web 服务框架，提供 RESTful API 及管理界面 |
| beautifulsoup4 | 4.12.0 | HTML 解析库，用于提取页面标题与描述信息 |
| apscheduler | 3.10.0 | 定时任务调度，驱动周期性链接状态检查 |
| pandas | 2.1.0 | 数据导出功能，支持将检索结果转换为 DataFrame 格式 |
| gunicorn | 21.2.0 | 生产环境 WSGI 服务器，用于高并发部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide/ | 如何导入链接、设置标签、执行检索、导出结果？ |
| 管理指南 | /docs/admin-guide/ | 如何调整检测频率、配置邮件告警、备份数据库？ |
| API 参考 | /docs/api-reference/ | 各端点参数说明、请求示例、错误码含义是什么？ |
| 开发文档 | /docs/developer-guide/ | 如何扩展自定义解析器、贡献新的监控插件？ |

## 资源列表

- http://m.blog.gqskj.cn/nnews/97011.htm
- http://m.blog.gqskj.cn/nnews/91508.htm
- http://m.blog.gqskj.cn/nnews/9093043.htm
- http://m.blog.gqskj.cn/nnews/7643998.htm
- http://m.blog.gqskj.cn/nnews/489275.htm
- http://m.blog.gqskj.cn/nnews/3499378.htm
- http://m.blog.gqskj.cn/nnews/208649.htm
- http://m.blog.gqskj.cn/nnews/6442684.htm
- http://m.blog.gqskj.cn/nnews/22453.htm
- http://m.blog.gqskj.cn/nnews/416848.htm
- http://m.blog.gqskj.cn/nnews/499938.htm
- http://m.blog.gqskj.cn/nnews/45966.htm
- http://m.blog.gqskj.cn/nnews/8092.htm
- http://m.blog.gqskj.cn/nnews/322418.htm
- http://m.blog.gqskj.cn/nnews/578550.htm
- http://m.blog.gqskj.cn/nnews/2649.htm
- http://m.blog.gqskj.cn/nnews/98520.htm
- http://m.blog.gqskj.cn/nnews/676407.htm
- http://m.blog.gqskj.cn/nnews/25063.htm
- http://m.blog.gqskj.cn/nnews/9495729.htm
- http://m.blog.gqskj.cn/nnews/06293.htm
- http://m.blog.gqskj.cn/nnews/21406.htm
- http://m.blog.gqskj.cn/nnews/15061.htm
- http://m.blog.gqskj.cn/nnews/5618258.htm
- http://m.blog.gqskj.cn/nnews/3031.htm
- http://m.blog.gqskj.cn/nnews/916545.htm
- http://m.blog.gqskj.cn/nnews/0669117.htm
- http://m.blog.gqskj.cn/nnews/3993534.htm
- http://m.blog.gqskj.cn/nnews/5585720.htm
- http://m.blog.gqskj.cn/nnews/3699.htm
- http://m.blog.gqskj.cn/nnews/6760065.htm
- http://m.blog.gqskj.cn/nnews/799155.htm
- http://m.blog.gqskj.cn/nnews/3520728.htm
- http://m.blog.gqskj.cn/nnews/531959.htm
- http://m.blog.gqskj.cn/nnews/1218.htm
- http://m.blog.gqskj.cn/nnews/11905.htm
- http://m.blog.gqskj.cn/nnews/067414.htm
- http://m.blog.gqskj.cn/nnews/40573.htm
- http://m.blog.gqskj.cn/nnews/3755112.htm
- http://m.blog.gqskj.cn/nnews/7953715.htm
- http://m.blog.gqskj.cn/nnews/130985.htm
- http://m.blog.gqskj.cn/nnews/5784585.htm
- http://m.blog.gqskj.cn/nnews/8236.htm
- http://m.blog.gqskj.cn/nnews/03605.htm
- http://m.blog.gqskj.cn/nnews/5663.htm
- http://m.blog.gqskj.cn/nnews/40035.htm
- http://m.blog.gqskj.cn/nnews/204949.htm
- http://m.blog.gqskj.cn/nnews/5760.htm
- http://m.blog.gqskj.cn/nnews/6702478.htm
- http://m.blog.gqskj.cn/nnews/26340.htm
- http://m.blog.gqskj.cn/nnews/900712.htm
- http://m.blog.gqskj.cn/nnews/725619.htm
- http://m.blog.gqskj.cn/nnews/3075.htm
- http://m.blog.gqskj.cn/nnews/7115909.htm
- http://m.blog.gqskj.cn/nnews/1371935.htm
- http://m.blog.gqskj.cn/nnews/232282.htm
- http://m.blog.gqskj.cn/nnews/412179.htm
- http://m.blog.gqskj.cn/nnews/0443639.htm
- http://m.blog.gqskj.cn/nnews/2999687.htm
- http://m.blog.gqskj.cn/nnews/894549.htm
- http://m.blog.gqskj.cn/nnews/3574962.htm
- http://m.blog.gqskj.cn/nnews/9429.htm
- http://m.blog.gqskj.cn/nnews/69523.htm
- http://m.blog.gqskj.cn/nnews/2347516.htm
- http://m.blog.gqskj.cn/nnews/2069.htm
- http://m.blog.gqskj.cn/nnews/053656.htm
- http://m.blog.gqskj.cn/nnews/4058851.htm
- http://m.blog.gqskj.cn/nnews/8630.htm
- http://m.blog.gqskj.cn/nnews/4742.htm
- http://m.blog.gqskj.cn/nnews/6638.htm
- http://m.blog.gqskj.cn/nnews/8578444.htm
- http://m.blog.gqskj.cn/nnews/7427151.htm
- http://m.blog.gqskj.cn/nnews/2610.htm
- http://m.blog.gqskj.cn/nnews/573610.htm
- http://m.blog.gqskj.cn/nnews/46614.htm
- http://m.blog.gqskj.cn/nnews/8784977.htm
- http://m.blog.gqskj.cn/nnews/102342.htm
- http://m.blog.gqskj.cn/nnews/9320.htm
- http://m.blog.gqskj.cn/nnews/2527.htm
- http://m.blog.gqskj.cn/nnews/4500.htm
- http://m.blog.gqskj.cn/nnews/591776.htm
- http://m.blog.gqskj.cn/nnews/35495.htm
- http://m.blog.gqskj.cn/nnews/9885.htm
- http://m.blog.gqskj.cn/nnews/4033.htm
- http://m.blog.gqskj.cn/nnews/622765.htm
- http://m.blog.gqskj.cn/nnews/578411.htm
- http://m.blog.gqskj.cn/nnews/0962160.htm
- http://m.blog.gqskj.cn/nnews/5614125.htm
- http://m.blog.gqskj.cn/nnews/9296890.htm
- http://m.blog.gqskj.cn/nnews/4226.htm
- http://m.blog.gqskj.cn/nnews/4630.htm
- http://m.blog.gqskj.cn/nnews/791396.htm
- http://m.blog.gqskj.cn/nnews/64406.htm
- http://m.blog.gqskj.cn/nnews/52731.htm
- http://m.blog.gqskj.cn/nnews/5841607.htm
- http://m.blog.gqskj.cn/nnews/3252.htm
- http://m.blog.gqskj.cn/nnews/7923.htm
- http://m.blog.gqskj.cn/nnews/486803.htm
- http://m.blog.gqskj.cn/nnews/8624.htm
- http://m.blog.gqskj.cn/nnews/60203.htm
- http://m.blog.gqskj.cn/nnews/1791946.htm
- http://m.blog.gqskj.cn/nnews/122993.htm
- http://m.blog.gqskj.cn/nnews/2262436.htm
- http://m.blog.gqskj.cn/nnews/026072.htm
- http://m.blog.gqskj.cn/nnews/302881.htm
- http://m.blog.gqskj.cn/nnews/64733.htm
- http://m.blog.gqskj.cn/nnews/94543.htm
- http://m.blog.gqskj.cn/nnews/4923011.htm
- http://m.blog.gqskj.cn/nnews/3644.htm
- http://m.blog.gqskj.cn/nnews/1040.htm
- http://m.blog.gqskj.cn/nnews/7451856.htm
- http://m.blog.gqskj.cn/nnews/668967.htm
- http://m.blog.gqskj.cn/nnews/8210989.htm
- http://m.blog.gqskj.cn/nnews/5804.htm
- http://m.blog.gqskj.cn/nnews/8391890.htm
- http://m.blog.gqskj.cn/nnews/74265.htm
- http://m.blog.gqskj.cn/nnews/2786703.htm
- http://m.blog.gqskj.cn/nnews/029869.htm
- http://m.blog.gqskj.cn/nnews/962145.htm
- http://m.blog.gqskj.cn/nnews/4203319.htm
- http://m.blog.gqskj.cn/nnews/7952427.htm
- http://m.blog.gqskj.cn/nnews/6949677.htm
- http://m.blog.gqskj.cn/nnews/36329.htm
- http://m.blog.gqskj.cn/nnews/1851773.htm
- http://m.blog.gqskj.cn/nnews/031472.htm
- http://m.blog.gqskj.cn/nnews/94250.htm
- http://m.blog.gqskj.cn/nnews/327276.htm
- http://m.blog.gqskj.cn/nnews/0971195.htm
- http://m.blog.gqskj.cn/nnews/1805.htm
- http://m.blog.gqskj.cn/nnews/75865.htm
- http://m.blog.gqskj.cn/nnews/8871591.htm
- http://m.blog.gqskj.cn/nnews/03410.htm
- http://m.blog.gqskj.cn/nnews/4554.htm
- http://m.blog.gqskj.cn/nnews/604426.htm
- http://m.blog.gqskj.cn/nnews/837826.htm
- http://m.blog.gqskj.cn/nnews/75772.htm
- http://m.blog.gqskj.cn/nnews/518805.htm
- http://m.blog.gqskj.cn/nnews/1392991.htm
- http://m.blog.gqskj.cn/nnews/83811.htm
- http://m.blog.gqskj.cn/nnews/386869.htm
- http://m.blog.gqskj.cn/nnews/8104.htm
- http://m.blog.gqskj.cn/nnews/95172.htm
- http://m.blog.gqskj.cn/nnews/274931.htm
- http://m.blog.gqskj.cn/nnews/24921.htm
- http://m.blog.gqskj.cn/nnews/8726383.htm
- http://m.blog.gqskj.cn/nnews/513524.htm
- http://m.blog.gqskj.cn/nnews/2037.htm
- http://m.blog.gqskj.cn/nnews/22934.htm
- http://m.blog.gqskj.cn/nnews/0640820.htm
- http://m.blog.gqskj.cn/nnews/9385.htm
- http://m.blog.gqskj.cn/nnews/7059.htm
- http://m.blog.gqskj.cn/nnews/4331120.htm
- http://m.blog.gqskj.cn/nnews/960439.htm
- http://m.blog.gqskj.cn/nnews/25620.htm
- http://m.blog.gqskj.cn/nnews/6199301.htm
- http://m.blog.gqskj.cn/nnews/9800000.htm
- http://m.blog.gqskj.cn/nnews/7826.htm
- http://m.blog.gqskj.cn/nnews/8331527.htm
- http://m.blog.gqskj.cn/nnews/85471.htm
- http://m.blog.gqskj.cn/nnews/178379.htm
- http://m.blog.gqskj.cn/nnews/5470926.htm
- http://m.blog.gqskj.cn/nnews/143746.htm
- http://m.blog.gqskj.cn/nnews/9796.htm
- http://m.blog.gqskj.cn/nnews/990741.htm
- http://m.blog.gqskj.cn/nnews/308430.htm
- http://m.blog.gqskj.cn/nnews/437624.htm
- http://m.blog.gqskj.cn/nnews/5815191.htm
- http://m.blog.gqskj.cn/nnews/0362551.htm
- http://m.blog.gqskj.cn/nnews/4215048.htm
- http://m.blog.gqskj.cn/nnews/559220.htm
- http://m.blog.gqskj.cn/nnews/20600.htm
- http://m.blog.gqskj.cn/nnews/9605318.htm
- http://m.blog.gqskj.cn/nnews/7959.htm
- http://m.blog.gqskj.cn/nnews/3881.htm
- http://m.blog.gqskj.cn/nnews/7324.htm
- http://m.blog.gqskj.cn/nnews/80499.htm
- http://m.blog.gqskj.cn/nnews/0352.htm
- http://m.blog.gqskj.cn/nnews/4558.htm
- http://m.blog.gqskj.cn/nnews/2455869.htm
- http://m.blog.gqskj.cn/nnews/8240382.htm
- http://m.blog.gqskj.cn/nnews/866788.htm
- http://m.blog.gqskj.cn/nnews/9339834.htm
- http://m.blog.gqskj.cn/nnews/2215.htm
- http://m.blog.gqskj.cn/nnews/574934.htm
- http://m.blog.gqskj.cn/nnews/0229.htm
- http://m.blog.gqskj.cn/nnews/0724657.htm
- http://m.blog.gqskj.cn/nnews/551201.htm
- http://m.blog.gqskj.cn/nnews/72716.htm
- http://m.blog.gqskj.cn/nnews/2898.htm
- http://m.blog.gqskj.cn/nnews/77441.htm
- http://m.blog.gqskj.cn/nnews/886625.htm
- http://m.blog.gqskj.cn/nnews/7880224.htm
- http://m.blog.gqskj.cn/nnews/8777675.htm
- http://m.blog.gqskj.cn/nnews/70861.htm
- http://m.blog.gqskj.cn/nnews/0750.htm
- http://m.blog.gqskj.cn/nnews/37732.htm
- http://m.blog.gqskj.cn/nnews/82988.htm
- http://m.blog.gqskj.cn/nnews/06140.htm
- http://m.blog.gqskj.cn/nnews/50235.htm
- http://m.blog.gqskj.cn/nnews/693393.htm
- http://m.blog.gqskj.cn/nnews/1441.htm
- http://m.blog.gqskj.cn/nnews/222636.htm
- http://m.blog.gqskj.cn/nnews/78580.htm
- http://m.blog.gqskj.cn/nnews/35405.htm
- http://m.blog.gqskj.cn/nnews/7273691.htm
- http://m.blog.gqskj.cn/nnews/9160.htm
- http://m.blog.gqskj.cn/nnews/294303.htm
- http://m.blog.gqskj.cn/nnews/87212.htm
- http://m.blog.gqskj.cn/nnews/0804592.htm
- http://m.blog.gqskj.cn/nnews/69972.htm
- http://m.blog.gqskj.cn/nnews/8805.htm
- http://m.blog.gqskj.cn/nnews/5263.htm
- http://m.blog.gqskj.cn/nnews/2034967.htm
- http://m.blog.gqskj.cn/nnews/641577.htm
- http://m.blog.gqskj.cn/nnews/0738371.htm
- http://m.blog.gqskj.cn/nnews/13381.htm
- http://m.blog.gqskj.cn/nnews/9760519.htm
- http://m.blog.gqskj.cn/nnews/1760.htm
- http://m.blog.gqskj.cn/nnews/2158735.htm
- http://m.blog.gqskj.cn/nnews/6853630.htm
- http://m.blog.gqskj.cn/nnews/28804.htm
- http://m.blog.gqskj.cn/nnews/0738420.htm
- http://m.blog.gqskj.cn/nnews/0562.htm
- http://m.blog.gqskj.cn/nnews/791853.htm
- http://m.blog.gqskj.cn/nnews/9212023.htm
- http://m.blog.gqskj.cn/nnews/4073858.htm
- http://m.blog.gqskj.cn/nnews/53139.htm
- http://m.blog.gqskj.cn/nnews/4503761.htm
- http://m.blog.gqskj.cn/nnews/0678.htm
- http://m.blog.gqskj.cn/nnews/94025.htm
- http://m.blog.gqskj.cn/nnews/186416.htm
- http://m.blog.gqskj.cn/nnews/6646.htm
- http://m.blog.gqskj.cn/nnews/862419.htm
- http://m.blog.gqskj.cn/nnews/9088.htm
- http://m.blog.gqskj.cn/nnews/0570.htm
- http://m.blog.gqskj.cn/nnews/11339.htm
- http://m.blog.gqskj.cn/nnews/4375.htm
- http://m.blog.gqskj.cn/nnews/043767.htm
- http://m.blog.gqskj.cn/nnews/2106.htm
- http://m.blog.gqskj.cn/nnews/1307338.htm
- http://m.blog.gqskj.cn/nnews/9999.htm
- http://m.blog.gqskj.cn/nnews/68809.htm
- http://m.blog.gqskj.cn/nnews/594122.htm
- http://m.blog.gqskj.cn/nnews/7355.htm
- http://m.blog.gqskj.cn/nnews/970136.htm
- http://m.blog.gqskj.cn/nnews/8891.htm
- http://m.blog.gqskj.cn/nnews/0714.htm
- http://m.blog.gqskj.cn/nnews/3098583.htm
- http://m.blog.gqskj.cn/nnews/303616.htm
- http://m.blog.gqskj.cn/nnews/362048.htm

## 项目结构

```
linkvault/
├── app/                            # 主应用模块
│   ├── __init__.py                 # 应用工厂函数，初始化 Flask 及扩展
│   ├── routes/                     # 路由控制器层
│   │   ├── api.py                  # RESTful API 端点定义（链接增删改查、状态检测）
│   │   └── web.py                  # Web UI 路由（仪表板、检索页面、详情视图）
│   ├── models/                     # 数据模型与 ORM 映射
│   │   ├── link.py                 # Link 实体，包含 URL、状态码、元数据字段
│   │   ├── tag.py                  # Tag 实体，实现多对多关联
│   │   └── annotation.py           # 备注与收藏模型
│   ├── services/                   # 业务逻辑服务层
│   │   ├── checker.py              # 链接存活检测服务，支持并发 HEAD 请求
│   │   ├── parser.py               # 元数据解析服务（标题、描述、发布时间抽取）
│   │   └── exporter.py             # 数据导出服务（JSON / CSV 格式转换）
│   ├── scheduler/                  # 定时任务配置
│   │   └── jobs.py                 # APScheduler 任务定义（周期性检测、报表生成）
│   └── utils/                      # 通用工具函数
│       ├── validators.py           # URL 格式校验与规范化
│       └── helpers.py              # 日期处理、日志装饰器等杂项辅助
├── scripts/                        # 运维与开发脚本
│   ├── init_db.py                  # 初始化数据库表结构
│   ├── import_links.py             # 从文本文件批量导入链接
│   └── export_backup.py            # 全量数据备份导出
├── tests/                          # 单元测试与集成测试
│   ├── test_checker.py             # 链接检测服务测试
│   ├── test_parser.py              # 元数据解析测试
│   └── conftest.py                 # pytest 全局夹具配置
├── docs/                           # 项目文档源文件
│   ├── user-guide/                 # 用户手册章节
│   ├── admin-guide/                # 管理员部署与运维指南
│   └── api-reference/              # API 接口详细文档
├── samples/                        # 示例数据文件
│   └── links_216.txt               # 第 216 批示例链接列表（含 250 条 URL）
├── requirements.txt                # Python 依赖清单
├── app.py                          # 应用启动入口
└── README.md                       # 项目介绍文档（本文件）
```

## 贡献指南

我们欢迎并鼓励社区提交各类贡献，包括但不限于功能建议、代码修复、文档改进和测试用例补充。请遵循以下步骤参与项目开发。

1. 在 GitHub 上 Fork 本仓库至个人账户，并在本地克隆 Fork 后的副本，同时将 upstream 指向原仓库以保持同步。

2. 创建新的功能分支（如 `feature/add-batch-tagging` 或 `fix/checker-timeout`），所有开发工作应在此分支上进行，避免直接修改主分支。

3. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例。测试文件需放置在 `tests/` 目录下，命名遵循 `test_*.py` 规范。

4. 提交代码前，运行代码格式化工具（如 `black`）和静态检查（如 `flake8`）以保证代码风格一致性。提交信息应使用简洁的英文描述，格式为 `<type>: <short description>`（例如 `feat: add retry mechanism for link checker`）。

5. 通过 Pull Request 提交变更，在描述中清晰说明解决的问题或实现的功能，并关联相关 Issue（如有）。PR 至少需要一位维护者审核通过后方可合并。

## 常见问题

**Q: 系统支持的最大链接管理数量是多少？是否存在性能瓶颈？**

A: 系统本身对链接数量没有硬性上限。在 SQLite 默认配置下，单表记录数超过 50 万条时，检索性能可能出现下降。建议在生产环境中部署 PostgreSQL 以支持更大规模的数据集。对于定期状态检测任务，建议将并发数调整为 20 至 50 之间，避免对目标站点造成过大压力，同时可配置随机延时以降低封禁风险。

**Q: 导入链接时是否会自动去重？如何处理已失效的历史链接？**

A: 系统在导入过程中会自动比对 URL 的标准化形式（移除末尾斜杠及空锚点），检测到重复条目时会跳过并记录日志。对于已失效的链接（状态码非 2xx/3xx），系统不会自动删除，而是标记为 `inactive` 状态并保留历史元数据。用户可在管理界面按状态筛选，批量导出失效列表后决定是否清理或更新。

**Q: 能否将 LinkVault 部署到公网并支持多用户使用？**

A: 可以。当前版本已支持基于 Flask-Login 的会话管理，但未内置细粒度权限控制（如 RBAC）。若需多用户隔离，建议为每个用户单独部署实例，或基于 Nginx 进行路径转发。后续版本计划引入团队空间功能，届时将原生支持多租户数据隔离。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:36
