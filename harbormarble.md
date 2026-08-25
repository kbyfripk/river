# XNews Link Aggregator

XNews Link Aggregator 是一个面向移动端资讯聚合场景的轻量级外链资源管理与导航系统。本项目定位于为开发者、内容运营者以及资讯研究员提供一套结构化的历史新闻外链索引库，通过标准化的 URL 收录与分类体系，解决碎片化资讯源难以追溯、难以批量检索、难以长期归档的问题。项目本身不存储具体新闻内容，仅作为资源定位与导航层，适用于个人知识管理、历史内容回溯分析以及第三方资讯平台的后台链接补充。

## 功能概览

**批量外链导入** 支持一次性导入大量原始资讯 URL，自动识别域名与路径结构，完成初步合法性校验。

**链接去重与归一化** 基于 URL 完整字符串进行精确去重，并对同一域名下的不同路径进行归类统计，便于后续人工审核。

**分类标记体系** 允许用户对每条链接添加自定义标签（如行业、时间、地域），支持多标签组合筛选。

**状态追踪机制** 记录每条链接的最后检查时间、HTTP 状态码及响应时长，辅助判断资源是否仍可访问。

**导出与订阅接口** 提供按标签或按时间范围的链接列表导出功能（JSON / CSV 格式），并支持生成静态导航页面供内部使用。

**检索与过滤** 提供基于 URL 关键词、域名、文件类型（.htm）的实时搜索能力，支持结果排序与分页。

## 应用场景

**历史资讯归档与复查** 内容审核团队可将本系统作为中间层，对大量历史新闻链接进行统一收录、状态检查与分类标记，替代零散的浏览器收藏夹或本地文档记录。

**舆情分析前期数据准备** 数据分析师可批量导入原始链接，利用系统的导出功能获取结构化链接清单，再结合第三方爬虫或 API 进行内容抓取与情感分析，无需手动整理繁杂的 URL 列表。

**个人知识库外链管理** 研究员或开发者可将本项目作为个人知识体系的补充模块，对阅读过的资讯链接进行长期存档，并通过标签与检索功能快速回溯特定主题的历史资料。

**第三方平台内容补全** 中小型内容聚合应用的后台运营人员可定期将本系统生成的链接清单作为内容源补充，经筛选后用于填充自身平台的资讯板块。

## 快速开始

以下步骤适用于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/xnews-link-aggregator.git

# 进入项目目录
cd xnews-link-aggregator

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 初始化本地数据库
python scripts/init_db.py

# 启动开发服务器（默认监听 8000 端口）
python app.py runserver
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.10 及以上 | 核心运行环境，低于此版本可能导致异步模块异常 |
| SQLite | 3.35 及以上 | 内置轻量数据库，用于存储链接索引与状态信息 |
| pip | 22.0 及以上 | Python 包管理器，用于安装项目依赖项 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库和后续更新 |
| 网络连接 | 稳定访问外网 | 用于首次启动时检测链接可用性，非必须但推荐 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何在 5 分钟内完成部署并导入第一批链接？ |
| API 参考 | docs/api.md | 系统提供了哪些 RESTful 接口用于链接增删改查？ |
| 运维手册 | docs/operations.md | 如何进行数据库备份、链接状态批量刷新与日志轮转？ |
| 数据模型 | docs/schema.md | 链接表、标签表、状态历史表的字段设计与关联关系是什么？ |

## 资源列表

- http://m.3g.gqskj.cn/xnews/0691063.htm
- http://m.3g.gqskj.cn/xnews/459420.htm
- http://m.3g.gqskj.cn/xnews/626033.htm
- http://m.3g.gqskj.cn/xnews/9531027.htm
- http://m.3g.gqskj.cn/xnews/726370.htm
- http://m.3g.gqskj.cn/xnews/492674.htm
- http://m.3g.gqskj.cn/xnews/17013.htm
- http://m.3g.gqskj.cn/xnews/85527.htm
- http://m.3g.gqskj.cn/xnews/60536.htm
- http://m.3g.gqskj.cn/xnews/15659.htm
- http://m.3g.gqskj.cn/xnews/827559.htm
- http://m.3g.gqskj.cn/xnews/2249.htm
- http://m.3g.gqskj.cn/xnews/84685.htm
- http://m.3g.gqskj.cn/xnews/8625767.htm
- http://m.3g.gqskj.cn/xnews/928740.htm
- http://m.3g.gqskj.cn/xnews/673284.htm
- http://m.3g.gqskj.cn/xnews/271945.htm
- http://m.3g.gqskj.cn/xnews/95898.htm
- http://m.3g.gqskj.cn/xnews/66713.htm
- http://m.3g.gqskj.cn/xnews/6706.htm
- http://m.3g.gqskj.cn/xnews/76164.htm
- http://m.3g.gqskj.cn/xnews/55005.htm
- http://m.3g.gqskj.cn/xnews/640195.htm
- http://m.3g.gqskj.cn/xnews/8889.htm
- http://m.3g.gqskj.cn/xnews/0932.htm
- http://m.3g.gqskj.cn/xnews/4955816.htm
- http://m.3g.gqskj.cn/xnews/39818.htm
- http://m.3g.gqskj.cn/xnews/531826.htm
- http://m.3g.gqskj.cn/xnews/3448473.htm
- http://m.3g.gqskj.cn/xnews/367744.htm
- http://m.3g.gqskj.cn/xnews/61199.htm
- http://m.3g.gqskj.cn/xnews/9595269.htm
- http://m.3g.gqskj.cn/xnews/143458.htm
- http://m.3g.gqskj.cn/xnews/4211.htm
- http://m.3g.gqskj.cn/xnews/6850.htm
- http://m.3g.gqskj.cn/xnews/78910.htm
- http://m.3g.gqskj.cn/xnews/728310.htm
- http://m.3g.gqskj.cn/xnews/2956.htm
- http://m.3g.gqskj.cn/xnews/5878622.htm
- http://m.3g.gqskj.cn/xnews/3993.htm
- http://m.3g.gqskj.cn/xnews/4749.htm
- http://m.3g.gqskj.cn/xnews/5281986.htm
- http://m.3g.gqskj.cn/xnews/89122.htm
- http://m.3g.gqskj.cn/xnews/6960045.htm
- http://m.3g.gqskj.cn/xnews/238116.htm
- http://m.3g.gqskj.cn/xnews/80684.htm
- http://m.3g.gqskj.cn/xnews/705504.htm
- http://m.3g.gqskj.cn/xnews/2167970.htm
- http://m.3g.gqskj.cn/xnews/535589.htm
- http://m.3g.gqskj.cn/xnews/9241667.htm
- http://m.3g.gqskj.cn/xnews/649222.htm
- http://m.3g.gqskj.cn/xnews/20758.htm
- http://m.3g.gqskj.cn/xnews/3079458.htm
- http://m.3g.gqskj.cn/xnews/477324.htm
- http://m.3g.gqskj.cn/xnews/5833.htm
- http://m.3g.gqskj.cn/xnews/746304.htm
- http://m.3g.gqskj.cn/xnews/677232.htm
- http://m.3g.gqskj.cn/xnews/5974597.htm
- http://m.3g.gqskj.cn/xnews/5149.htm
- http://m.3g.gqskj.cn/xnews/01101.htm
- http://m.3g.gqskj.cn/xnews/7584176.htm
- http://m.3g.gqskj.cn/xnews/6829.htm
- http://m.3g.gqskj.cn/xnews/6374.htm
- http://m.3g.gqskj.cn/xnews/573295.htm
- http://m.3g.gqskj.cn/xnews/1331.htm
- http://m.3g.gqskj.cn/xnews/340681.htm
- http://m.3g.gqskj.cn/xnews/59748.htm
- http://m.3g.gqskj.cn/xnews/96385.htm
- http://m.3g.gqskj.cn/xnews/6220.htm
- http://m.3g.gqskj.cn/xnews/020936.htm
- http://m.3g.gqskj.cn/xnews/25502.htm
- http://m.3g.gqskj.cn/xnews/10332.htm
- http://m.3g.gqskj.cn/xnews/8173641.htm
- http://m.3g.gqskj.cn/xnews/9368473.htm
- http://m.3g.gqskj.cn/xnews/5186869.htm
- http://m.3g.gqskj.cn/xnews/586591.htm
- http://m.3g.gqskj.cn/xnews/3134356.htm
- http://m.3g.gqskj.cn/xnews/4731.htm
- http://m.3g.gqskj.cn/xnews/859306.htm
- http://m.3g.gqskj.cn/xnews/7424.htm
- http://m.3g.gqskj.cn/xnews/35978.htm
- http://m.3g.gqskj.cn/xnews/929464.htm
- http://m.3g.gqskj.cn/xnews/9456.htm
- http://m.3g.gqskj.cn/xnews/40132.htm
- http://m.3g.gqskj.cn/xnews/0844.htm
- http://m.3g.gqskj.cn/xnews/1042.htm
- http://m.3g.gqskj.cn/xnews/773133.htm
- http://m.3g.gqskj.cn/xnews/4727674.htm
- http://m.3g.gqskj.cn/xnews/886078.htm
- http://m.3g.gqskj.cn/xnews/84841.htm
- http://m.3g.gqskj.cn/xnews/3058442.htm
- http://m.3g.gqskj.cn/xnews/5360.htm
- http://m.3g.gqskj.cn/xnews/1409.htm
- http://m.3g.gqskj.cn/xnews/0169.htm
- http://m.3g.gqskj.cn/xnews/3377.htm
- http://m.3g.gqskj.cn/xnews/18781.htm
- http://m.3g.gqskj.cn/xnews/547066.htm
- http://m.3g.gqskj.cn/xnews/7119.htm
- http://m.3g.gqskj.cn/xnews/7516168.htm
- http://m.3g.gqskj.cn/xnews/816221.htm
- http://m.3g.gqskj.cn/xnews/1674.htm
- http://m.3g.gqskj.cn/xnews/3969959.htm
- http://m.3g.gqskj.cn/xnews/4452.htm
- http://m.3g.gqskj.cn/xnews/5004270.htm
- http://m.3g.gqskj.cn/xnews/6669.htm
- http://m.3g.gqskj.cn/xnews/25499.htm
- http://m.3g.gqskj.cn/xnews/569431.htm
- http://m.3g.gqskj.cn/xnews/7936570.htm
- http://m.3g.gqskj.cn/xnews/158563.htm
- http://m.3g.gqskj.cn/xnews/8316838.htm
- http://m.3g.gqskj.cn/xnews/650191.htm
- http://m.3g.gqskj.cn/xnews/574684.htm
- http://m.3g.gqskj.cn/xnews/9750.htm
- http://m.3g.gqskj.cn/xnews/8205285.htm
- http://m.3g.gqskj.cn/xnews/306512.htm
- http://m.3g.gqskj.cn/xnews/91337.htm
- http://m.3g.gqskj.cn/xnews/38060.htm
- http://m.3g.gqskj.cn/xnews/65317.htm
- http://m.3g.gqskj.cn/xnews/9396281.htm
- http://m.3g.gqskj.cn/xnews/49467.htm
- http://m.3g.gqskj.cn/xnews/57677.htm
- http://m.3g.gqskj.cn/xnews/5836.htm
- http://m.3g.gqskj.cn/xnews/9146371.htm
- http://m.3g.gqskj.cn/xnews/586588.htm
- http://m.3g.gqskj.cn/xnews/9447912.htm
- http://m.3g.gqskj.cn/xnews/0567242.htm
- http://m.3g.gqskj.cn/xnews/821563.htm
- http://m.3g.gqskj.cn/xnews/2958.htm
- http://m.3g.gqskj.cn/xnews/28209.htm
- http://m.3g.gqskj.cn/xnews/77340.htm
- http://m.3g.gqskj.cn/xnews/187361.htm
- http://m.3g.gqskj.cn/xnews/457895.htm
- http://m.3g.gqskj.cn/xnews/3324.htm
- http://m.3g.gqskj.cn/xnews/6486749.htm
- http://m.3g.gqskj.cn/xnews/46717.htm
- http://m.3g.gqskj.cn/xnews/85163.htm
- http://m.3g.gqskj.cn/xnews/3133314.htm
- http://m.3g.gqskj.cn/xnews/931363.htm
- http://m.3g.gqskj.cn/xnews/93280.htm
- http://m.3g.gqskj.cn/xnews/796220.htm
- http://m.3g.gqskj.cn/xnews/5549.htm
- http://m.3g.gqskj.cn/xnews/790236.htm
- http://m.3g.gqskj.cn/xnews/2855.htm
- http://m.3g.gqskj.cn/xnews/8503140.htm
- http://m.3g.gqskj.cn/xnews/618889.htm
- http://m.3g.gqskj.cn/xnews/292688.htm
- http://m.3g.gqskj.cn/xnews/06064.htm
- http://m.3g.gqskj.cn/xnews/822175.htm
- http://m.3g.gqskj.cn/xnews/3347.htm
- http://m.3g.gqskj.cn/xnews/09270.htm
- http://m.3g.gqskj.cn/xnews/70629.htm
- http://m.3g.gqskj.cn/xnews/713600.htm
- http://m.3g.gqskj.cn/xnews/7072033.htm
- http://m.3g.gqskj.cn/xnews/18044.htm
- http://m.3g.gqskj.cn/xnews/02281.htm
- http://m.3g.gqskj.cn/xnews/433758.htm
- http://m.3g.gqskj.cn/xnews/47983.htm
- http://m.3g.gqskj.cn/xnews/81423.htm
- http://m.3g.gqskj.cn/xnews/7696247.htm
- http://m.3g.gqskj.cn/xnews/3301.htm
- http://m.3g.gqskj.cn/xnews/9125946.htm
- http://m.3g.gqskj.cn/xnews/33060.htm
- http://m.3g.gqskj.cn/xnews/4676.htm
- http://m.3g.gqskj.cn/xnews/2089.htm
- http://m.3g.gqskj.cn/xnews/800771.htm
- http://m.3g.gqskj.cn/xnews/66483.htm
- http://m.3g.gqskj.cn/xnews/41854.htm
- http://m.3g.gqskj.cn/xnews/6121.htm
- http://m.3g.gqskj.cn/xnews/5563223.htm
- http://m.3g.gqskj.cn/xnews/8785.htm
- http://m.3g.gqskj.cn/xnews/2105836.htm
- http://m.3g.gqskj.cn/xnews/19881.htm
- http://m.3g.gqskj.cn/xnews/2655.htm
- http://m.3g.gqskj.cn/xnews/501080.htm
- http://m.3g.gqskj.cn/xnews/0628881.htm
- http://m.3g.gqskj.cn/xnews/725832.htm
- http://m.3g.gqskj.cn/xnews/429970.htm
- http://m.3g.gqskj.cn/xnews/978817.htm
- http://m.3g.gqskj.cn/xnews/99268.htm
- http://m.3g.gqskj.cn/xnews/658936.htm
- http://m.3g.gqskj.cn/xnews/922154.htm
- http://m.3g.gqskj.cn/xnews/7969065.htm
- http://m.3g.gqskj.cn/xnews/8993068.htm
- http://m.3g.gqskj.cn/xnews/3162937.htm
- http://m.3g.gqskj.cn/xnews/6634712.htm
- http://m.3g.gqskj.cn/xnews/8661.htm
- http://m.3g.gqskj.cn/xnews/9280422.htm
- http://m.3g.gqskj.cn/xnews/89962.htm
- http://m.3g.gqskj.cn/xnews/819466.htm
- http://m.3g.gqskj.cn/xnews/238556.htm
- http://m.3g.gqskj.cn/xnews/3842.htm
- http://m.3g.gqskj.cn/xnews/6212635.htm
- http://m.3g.gqskj.cn/xnews/9092594.htm
- http://m.3g.gqskj.cn/xnews/130214.htm
- http://m.3g.gqskj.cn/xnews/34475.htm
- http://m.3g.gqskj.cn/xnews/3332136.htm
- http://m.3g.gqskj.cn/xnews/0224019.htm
- http://m.3g.gqskj.cn/xnews/4880.htm
- http://m.3g.gqskj.cn/xnews/2122.htm
- http://m.3g.gqskj.cn/xnews/8495385.htm
- http://m.3g.gqskj.cn/xnews/774079.htm
- http://m.3g.gqskj.cn/xnews/4698.htm
- http://m.3g.gqskj.cn/xnews/4420.htm
- http://m.3g.gqskj.cn/xnews/1744.htm
- http://m.3g.gqskj.cn/xnews/971481.htm
- http://m.3g.gqskj.cn/xnews/0322.htm
- http://m.3g.gqskj.cn/xnews/7524561.htm
- http://m.3g.gqskj.cn/xnews/6844.htm
- http://m.3g.gqskj.cn/xnews/12656.htm
- http://m.3g.gqskj.cn/xnews/408491.htm
- http://m.3g.gqskj.cn/xnews/65563.htm
- http://m.3g.gqskj.cn/xnews/949371.htm
- http://m.3g.gqskj.cn/xnews/169972.htm
- http://m.3g.gqskj.cn/xnews/2048145.htm
- http://m.3g.gqskj.cn/xnews/988707.htm
- http://m.3g.gqskj.cn/xnews/1361532.htm
- http://m.3g.gqskj.cn/xnews/8290615.htm
- http://m.3g.gqskj.cn/xnews/3238853.htm
- http://m.3g.gqskj.cn/xnews/08215.htm
- http://m.3g.gqskj.cn/xnews/05579.htm
- http://m.3g.gqskj.cn/xnews/8709.htm
- http://m.3g.gqskj.cn/xnews/08442.htm
- http://m.3g.gqskj.cn/xnews/9000.htm
- http://m.3g.gqskj.cn/xnews/3125202.htm
- http://m.3g.gqskj.cn/xnews/416040.htm
- http://m.3g.gqskj.cn/xnews/53927.htm
- http://m.3g.gqskj.cn/xnews/17482.htm
- http://m.3g.gqskj.cn/xnews/4212.htm
- http://m.3g.gqskj.cn/xnews/23659.htm
- http://m.3g.gqskj.cn/xnews/29739.htm
- http://m.3g.gqskj.cn/xnews/25298.htm
- http://m.3g.gqskj.cn/xnews/835644.htm
- http://m.3g.gqskj.cn/xnews/26555.htm
- http://m.3g.gqskj.cn/xnews/7649963.htm
- http://m.3g.gqskj.cn/xnews/291576.htm
- http://m.3g.gqskj.cn/xnews/01333.htm
- http://m.3g.gqskj.cn/xnews/8112595.htm
- http://m.3g.gqskj.cn/xnews/34775.htm
- http://m.3g.gqskj.cn/xnews/45312.htm
- http://m.3g.gqskj.cn/xnews/3441.htm
- http://m.3g.gqskj.cn/xnews/13516.htm
- http://m.3g.gqskj.cn/xnews/719025.htm
- http://m.3g.gqskj.cn/xnews/85913.htm
- http://m.3g.gqskj.cn/xnews/5372290.htm
- http://m.3g.gqskj.cn/xnews/14914.htm
- http://m.3g.gqskj.cn/xnews/7387.htm
- http://m.3g.gqskj.cn/xnews/29153.htm
- http://m.3g.gqskj.cn/xnews/2743.htm
- http://m.3g.gqskj.cn/xnews/655509.htm
- http://m.3g.gqskj.cn/xnews/824706.htm

## 项目结构

```
xnews-link-aggregator/
├── app.py                      # 应用主入口，初始化 Flask 服务器与路由注册
├── requirements.txt            # Python 依赖清单，包含 requests、flask、sqlalchemy 等
├── config/
│   ├── settings.py             # 全局配置项（端口、数据库路径、日志级别）
│   └── logging.conf            # 日志格式与输出目标配置
├── models/
│   ├── __init__.py             # 数据模型包初始化
│   ├── link.py                 # Link 表定义（URL、状态码、最后检查时间）
│   ├── tag.py                  # Tag 表定义（标签名称、创建时间）
│   └── history.py              # 状态变更历史表（记录每次检查的响应信息）
├── services/
│   ├── __init__.py             # 服务层包初始化
│   ├── importer.py             # 批量导入服务（解析原始 URL 列表并入库）
│   ├── checker.py              # 链接可用性检查服务（异步并发请求）
│   └── exporter.py             # 导出服务（支持 JSON / CSV 格式输出）
├── routes/
│   ├── __init__.py             # 路由蓝图层初始化
│   ├── api_v1.py               # RESTful API 端点实现（增删改查、状态刷新）
│   └── web.py                  # 简易 Web 管理界面路由（调试用）
├── scripts/
│   ├── init_db.py              # 数据库初始化脚本（创建表结构与索引）
│   └── seed_data.py            # 示例数据填充（用于开发测试）
├── tests/
│   ├── test_models.py          # 数据模型单元测试
│   └── test_services.py        # 服务层功能测试（导入、检查、导出）
└── docs/
    ├── quickstart.md           # 快速入门指南
    ├── api.md                  # API 参考文档
    ├── operations.md           # 运维与监控手册
    └── schema.md               # 数据库实体关系图与字段说明
```

## 贡献指南

**提交 Issue 报告问题** 请在 GitHub Issues 页面描述您遇到的问题，包括运行环境版本、复现步骤以及预期的行为。若涉及特定链接导入异常，请附上完整的错误日志。

**发起 Pull Request 修复或新增功能** 派生本仓库到您的个人账号，在本地创建新的功能分支进行开发。完成代码编写后，运行现有测试套件确保无回归问题，并提交 PR 至主仓库的 develop 分支。

**完善文档与示例** 欢迎对文档中的错误进行修正，或补充新的使用场景示例。文档采用 Markdown 格式编写，修改后请确保排版一致且无断链。

**反馈资源列表状态** 若您在使用过程中发现资源列表中的链接出现大规模失效或域名变更，请通过 Issue 或邮件方式通知维护团队，以便及时更新索引。

**提出功能建议** 如果您有新的功能需求或改进思路，请先查阅现有文档和 Issues 列表，确认无人提出过类似建议后再新建 Issue 进行详细说明。

## 常见问题

**问：项目启动后导入链接时提示连接超时，应如何处理？**

答：首次导入大量链接时，系统会默认对每个 URL 进行可达性检查。若网络环境较差或目标服务器响应缓慢，可修改 config/settings.py 中的 CHECK_TIMEOUT 参数（单位秒），将其调大至 10 或 15。同时，您也可以在导入时使用 --skip-check 参数跳过初始检查，仅将链接存入数据库。

**问：数据库文件体积增长过快，如何优化存储？**

答：系统默认使用 SQLite 作为存储引擎，历史状态表（history）会记录每次检查的详细信息。建议定期执行 scripts/cleanup_history.py 脚本清理 30 天之前的旧记录，或修改配置中的 HISTORY_RETENTION_DAYS 参数来调整保留周期。对于大规模生产环境，推荐迁移至 PostgreSQL 以获得更好的并发与维护支持。

**问：如何批量更新已有链接的状态？**

答：您可以通过调用 API 端点 /api/v1/links/refresh 并传入需要刷新的链接 ID 列表，或使用 services/checker.py 中的 batch_check 函数。若需刷新全部链接，可运行 python scripts/refresh_all.py 命令，该脚本将自动分页遍历所有记录并异步发起检查请求。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:46
