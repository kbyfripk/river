# NewsLink Hub

NewsLink Hub 是一个面向内容聚合与新闻外链管理的轻量级开源工具，专为需要批量处理、分类存储和快速检索移动端新闻资源（.htm 静态页）的开发者与内容运营人员设计。项目定位为技术资源与新闻外链的辅助管理平台，不提供新闻内容本身，而是围绕 URL 元数据构建索引、快照标记与访问监控能力，帮助用户在大量历史新闻链接中建立可维护的数据台账。

目标用户包括小型新闻聚合站运维者、舆情数据采集工程师、开源情报（OSINT）学习爱好者以及需要批量管理 .htm 落地页链接的运营人员。项目核心解决三个问题：一是分散的 .htm 链接缺乏统一登记入口，二是链接可用性无法批量感知，三是链接对应的主题分类与批次信息丢失后难以还原。NewsLink Hub 通过本地化的 URL 登记、状态标记与静态索引生成，使这些链接从无结构的文本变为可查询、可归档的结构化资源。

## 功能概览

批量 URL 导入与解析：支持将大量以 .htm 结尾的新闻外链一次性导入系统，自动解析 URL 中的路径层级、文件名与数字编号，并提取可用的元数据字段。

链接状态健康检查：定时对已登记的 URL 执行 HTTP 请求测试，记录响应状态码与响应时间，标记异常链接（超时、404、5xx），辅助运维人员清理失效资源。

批次管理与标签系统：每批导入的链接自动归属到对应批次（如第 75/240 批），支持自定义标签（如“财经”“科技”“地方新闻”），便于按主题或来源分类检索。

静态索引生成器：将登记后的链接列表输出为静态 HTML 目录页或 Markdown 索引表格，不依赖数据库即可生成可浏览的导航结构，降低部署成本。

元数据补充与备注字段：支持对每个链接添加备注信息（如抓取时间、摘要关键词、页面标题快照），防止仅有裸 URL 时丢失上下文。

本地化全文检索：基于 SQLite 或纯文本 JSON 索引，提供针对 URL 中的数字编号、文件名关键词的模糊搜索，快速定位特定链接。

导入导出兼容性：支持 CSV、JSON 和纯文本列表三种格式的链接批量导出，方便对接其他数据处理管道或存档备份。

## 应用场景

历史新闻链接归档与检索：内容运营团队收到大量带编号的 .htm 新闻链接（如 m.wap.fcful.cn/nnews/3816.htm），需要按发布时间或批次分类保存，后续通过编号或关键词快速查找特定稿件。NewsLink Hub 提供批量登记和编号检索能力，降低人工维护 Excel 的出错率。

舆情监控系统的外链前置处理：在舆情采集流程中，爬虫产出大量 .htm 链接后，先经过 NewsLink Hub 完成去重、状态预检和标签分组，再将健康的链接分发至下游渲染或分析模块，减少无效请求对下游系统的压力。

开源情报链接库建设：研究人员从不同渠道收集到大量新闻页面链接，需要建立带备注和状态监控的私有链接库。NewsLink Hub 以轻量级 SQLite 存储和静态索引输出，满足单机或内网环境下的数据管理需求。

静态站点导航页生成：个人站长或博客作者将关注的新闻外链通过 NewsLink Hub 生成静态导航页，嵌入个人网站作为“常用信息源”板块，无需动态后端支持。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 和 Python 3.9 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newslink-hub.git
cd newslink-hub

# 安装依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate     # Windows 请使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化本地数据库和配置
python scripts/init_db.py

# 启动开发服务（默认监听 127.0.0.1:5000）
python app.py run
```

访问 http://127.0.0.1:5000 即可进入 Web 管理界面。首次启动时会自动创建示例批次（第 75/240 批）的占位数据，您可以通过界面或 CLI 工具导入自己的链接列表。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 - 3.12 | 核心运行环境，低于 3.9 不支持类型注解语法 |
| SQLite | 3.35 以上 | 内置数据库，用于存储链接元数据和批次信息，无需额外安装 |
| requests | 2.28 以上 | 用于链接健康检查的 HTTP 客户端库 |
| click | 8.1 以上 | CLI 命令行工具框架，用于管理脚本交互 |
| python-dotenv | 1.0 以上 | 环境变量配置加载，用于区分开发/生产模式 |
| gunicorn | 20.1 以上 | 生产环境 WSGI 服务器（Linux 部署必需） |
| pytest | 7.0 以上 | 单元测试框架（仅开发环境需要） |
| black | 22.0 以上 | 代码格式化工具（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何导入链接、如何执行健康检查、如何生成静态索引、如何导出数据 |
| 开发者指南 | /docs/developer-guide/ | 项目模块划分、如何扩展自定义标签解析器、如何集成新的 URL 源 |
| API 参考 | /docs/api-reference/ | RESTful API 端点说明、请求/响应示例、鉴权方式 |
| 部署运维 | /docs/deployment/ | 使用 Gunicorn + Nginx 部署生产环境、SQLite 备份策略、日志配置 |

## 资源列表

- http://m.wap.fcful.cn/nnews/3816.htm
- http://m.wap.fcful.cn/nnews/0182.htm
- http://m.wap.fcful.cn/nnews/158925.htm
- http://m.wap.fcful.cn/nnews/0256.htm
- http://m.wap.fcful.cn/nnews/872337.htm
- http://m.wap.fcful.cn/nnews/864580.htm
- http://m.wap.fcful.cn/nnews/82876.htm
- http://m.wap.fcful.cn/nnews/68129.htm
- http://m.wap.fcful.cn/nnews/95258.htm
- http://m.wap.fcful.cn/nnews/994446.htm
- http://m.wap.fcful.cn/nnews/5028.htm
- http://m.wap.fcful.cn/nnews/91680.htm
- http://m.wap.fcful.cn/nnews/4223216.htm
- http://m.wap.fcful.cn/nnews/58310.htm
- http://m.wap.fcful.cn/nnews/22845.htm
- http://m.wap.fcful.cn/nnews/74455.htm
- http://m.wap.fcful.cn/nnews/7591.htm
- http://m.wap.fcful.cn/nnews/71934.htm
- http://m.wap.fcful.cn/nnews/4328.htm
- http://m.wap.fcful.cn/nnews/15831.htm
- http://m.wap.fcful.cn/nnews/36058.htm
- http://m.wap.fcful.cn/nnews/564497.htm
- http://m.wap.fcful.cn/nnews/7987781.htm
- http://m.wap.fcful.cn/nnews/3456125.htm
- http://m.wap.fcful.cn/nnews/6493.htm
- http://m.wap.fcful.cn/nnews/766262.htm
- http://m.wap.fcful.cn/nnews/0592671.htm
- http://m.wap.fcful.cn/nnews/3107977.htm
- http://m.wap.fcful.cn/nnews/8682.htm
- http://m.wap.fcful.cn/nnews/731988.htm
- http://m.wap.fcful.cn/nnews/8738.htm
- http://m.wap.fcful.cn/nnews/6554.htm
- http://m.wap.fcful.cn/nnews/08305.htm
- http://m.wap.fcful.cn/nnews/5863.htm
- http://m.wap.fcful.cn/nnews/39952.htm
- http://m.wap.fcful.cn/nnews/9948642.htm
- http://m.wap.fcful.cn/nnews/04962.htm
- http://m.wap.fcful.cn/nnews/57457.htm
- http://m.wap.fcful.cn/nnews/194173.htm
- http://m.wap.fcful.cn/nnews/5025.htm
- http://m.wap.fcful.cn/nnews/06189.htm
- http://m.wap.fcful.cn/nnews/2376.htm
- http://m.wap.fcful.cn/nnews/0316508.htm
- http://m.wap.fcful.cn/nnews/1761360.htm
- http://m.wap.fcful.cn/nnews/1001680.htm
- http://m.wap.fcful.cn/nnews/7165073.htm
- http://m.wap.fcful.cn/nnews/1884.htm
- http://m.wap.fcful.cn/nnews/7312.htm
- http://m.wap.fcful.cn/nnews/0621.htm
- http://m.wap.fcful.cn/nnews/3932.htm
- http://m.wap.fcful.cn/nnews/5082.htm
- http://m.wap.fcful.cn/nnews/0089.htm
- http://m.wap.fcful.cn/nnews/30197.htm
- http://m.wap.fcful.cn/nnews/7142.htm
- http://m.wap.fcful.cn/nnews/65492.htm
- http://m.wap.fcful.cn/nnews/3780257.htm
- http://m.wap.fcful.cn/nnews/68675.htm
- http://m.wap.fcful.cn/nnews/51901.htm
- http://m.wap.fcful.cn/nnews/4738.htm
- http://m.wap.fcful.cn/nnews/0343486.htm
- http://m.wap.fcful.cn/nnews/0474359.htm
- http://m.wap.fcful.cn/nnews/56658.htm
- http://m.wap.fcful.cn/nnews/5408948.htm
- http://m.wap.fcful.cn/nnews/968091.htm
- http://m.wap.fcful.cn/nnews/3073.htm
- http://m.wap.fcful.cn/nnews/41566.htm
- http://m.wap.fcful.cn/nnews/5165082.htm
- http://m.wap.fcful.cn/nnews/255372.htm
- http://m.wap.fcful.cn/nnews/00492.htm
- http://m.wap.fcful.cn/nnews/118291.htm
- http://m.wap.fcful.cn/nnews/76863.htm
- http://m.wap.fcful.cn/nnews/3302536.htm
- http://m.wap.fcful.cn/nnews/23605.htm
- http://m.wap.fcful.cn/nnews/640625.htm
- http://m.wap.fcful.cn/nnews/6719840.htm
- http://m.wap.fcful.cn/nnews/6468359.htm
- http://m.wap.fcful.cn/nnews/3404949.htm
- http://m.wap.fcful.cn/nnews/0790812.htm
- http://m.wap.fcful.cn/nnews/64185.htm
- http://m.wap.fcful.cn/nnews/809536.htm
- http://m.wap.fcful.cn/nnews/533699.htm
- http://m.wap.fcful.cn/nnews/6235002.htm
- http://m.wap.fcful.cn/nnews/47171.htm
- http://m.wap.fcful.cn/nnews/535254.htm
- http://m.wap.fcful.cn/nnews/107308.htm
- http://m.wap.fcful.cn/nnews/85946.htm
- http://m.wap.fcful.cn/nnews/9698.htm
- http://m.wap.fcful.cn/nnews/287497.htm
- http://m.wap.fcful.cn/nnews/8140.htm
- http://m.wap.fcful.cn/nnews/247045.htm
- http://m.wap.fcful.cn/nnews/114621.htm
- http://m.wap.fcful.cn/nnews/2531.htm
- http://m.wap.fcful.cn/nnews/2813609.htm
- http://m.wap.fcful.cn/nnews/914744.htm
- http://m.wap.fcful.cn/nnews/04009.htm
- http://m.wap.fcful.cn/nnews/3207217.htm
- http://m.wap.fcful.cn/nnews/9484189.htm
- http://m.wap.fcful.cn/nnews/522531.htm
- http://m.wap.fcful.cn/nnews/8583924.htm
- http://m.wap.fcful.cn/nnews/0241.htm
- http://m.wap.fcful.cn/nnews/87388.htm
- http://m.wap.fcful.cn/nnews/1881.htm
- http://m.wap.fcful.cn/nnews/9202282.htm
- http://m.wap.fcful.cn/nnews/275447.htm
- http://m.wap.fcful.cn/nnews/61783.htm
- http://m.wap.fcful.cn/nnews/26912.htm
- http://m.wap.fcful.cn/nnews/327442.htm
- http://m.wap.fcful.cn/nnews/691958.htm
- http://m.wap.fcful.cn/nnews/0399354.htm
- http://m.wap.fcful.cn/nnews/2203.htm
- http://m.wap.fcful.cn/nnews/625760.htm
- http://m.wap.fcful.cn/nnews/5351.htm
- http://m.wap.fcful.cn/nnews/613789.htm
- http://m.wap.fcful.cn/nnews/05171.htm
- http://m.wap.fcful.cn/nnews/7944419.htm
- http://m.wap.fcful.cn/nnews/2664.htm
- http://m.wap.fcful.cn/nnews/1382.htm
- http://m.wap.fcful.cn/nnews/02759.htm
- http://m.wap.fcful.cn/nnews/19638.htm
- http://m.wap.fcful.cn/nnews/794628.htm
- http://m.wap.fcful.cn/nnews/1351245.htm
- http://m.wap.fcful.cn/nnews/4723406.htm
- http://m.wap.fcful.cn/nnews/399112.htm
- http://m.wap.fcful.cn/nnews/4505223.htm
- http://m.wap.fcful.cn/nnews/8025041.htm
- http://m.wap.fcful.cn/nnews/7094330.htm
- http://m.wap.fcful.cn/nnews/02466.htm
- http://m.wap.fcful.cn/nnews/52312.htm
- http://m.wap.fcful.cn/nnews/790093.htm
- http://m.wap.fcful.cn/nnews/180135.htm
- http://m.wap.fcful.cn/nnews/654971.htm
- http://m.wap.fcful.cn/nnews/2802700.htm
- http://m.wap.fcful.cn/nnews/5382109.htm
- http://m.wap.fcful.cn/nnews/721734.htm
- http://m.wap.fcful.cn/nnews/943525.htm
- http://m.wap.fcful.cn/nnews/437360.htm
- http://m.wap.fcful.cn/nnews/5177.htm
- http://m.wap.fcful.cn/nnews/45580.htm
- http://m.wap.fcful.cn/nnews/4298.htm
- http://m.wap.fcful.cn/nnews/39018.htm
- http://m.wap.fcful.cn/nnews/7554.htm
- http://m.wap.fcful.cn/nnews/45773.htm
- http://m.wap.fcful.cn/nnews/2794.htm
- http://m.wap.fcful.cn/nnews/25736.htm
- http://m.wap.fcful.cn/nnews/5189470.htm
- http://m.wap.fcful.cn/nnews/1457346.htm
- http://m.wap.fcful.cn/nnews/2581.htm
- http://m.wap.fcful.cn/nnews/3528.htm
- http://m.wap.fcful.cn/nnews/9565.htm
- http://m.wap.fcful.cn/nnews/61688.htm
- http://m.wap.fcful.cn/nnews/4210591.htm
- http://m.wap.fcful.cn/nnews/1542466.htm
- http://m.wap.fcful.cn/nnews/70079.htm
- http://m.wap.fcful.cn/nnews/7177.htm
- http://m.wap.fcful.cn/nnews/0951563.htm
- http://m.wap.fcful.cn/nnews/7495.htm
- http://m.wap.fcful.cn/nnews/167712.htm
- http://m.wap.fcful.cn/nnews/5455389.htm
- http://m.wap.fcful.cn/nnews/3872.htm
- http://m.wap.fcful.cn/nnews/9763.htm
- http://m.wap.fcful.cn/nnews/123039.htm
- http://m.wap.fcful.cn/nnews/1323.htm
- http://m.wap.fcful.cn/nnews/17833.htm
- http://m.wap.fcful.cn/nnews/8432453.htm
- http://m.wap.fcful.cn/nnews/295282.htm
- http://m.wap.fcful.cn/nnews/2143385.htm
- http://m.wap.fcful.cn/nnews/72118.htm
- http://m.wap.fcful.cn/nnews/6874606.htm
- http://m.wap.fcful.cn/nnews/8336757.htm
- http://m.wap.fcful.cn/nnews/49456.htm
- http://m.wap.fcful.cn/nnews/576356.htm
- http://m.wap.fcful.cn/nnews/71119.htm
- http://m.wap.fcful.cn/nnews/2923.htm
- http://m.wap.fcful.cn/nnews/31776.htm
- http://m.wap.fcful.cn/nnews/3269.htm
- http://m.wap.fcful.cn/nnews/63018.htm
- http://m.wap.fcful.cn/nnews/87668.htm
- http://m.wap.fcful.cn/nnews/7297.htm
- http://m.wap.fcful.cn/nnews/3065.htm
- http://m.wap.fcful.cn/nnews/774032.htm
- http://m.wap.fcful.cn/nnews/458194.htm
- http://m.wap.fcful.cn/nnews/398075.htm
- http://m.wap.fcful.cn/nnews/86511.htm
- http://m.wap.fcful.cn/nnews/3251721.htm
- http://m.wap.fcful.cn/nnews/9791543.htm
- http://m.wap.fcful.cn/nnews/3045584.htm
- http://m.wap.fcful.cn/nnews/3884497.htm
- http://m.wap.fcful.cn/nnews/8436.htm
- http://m.wap.fcful.cn/nnews/3317644.htm
- http://m.wap.fcful.cn/nnews/825438.htm
- http://m.wap.fcful.cn/nnews/938821.htm
- http://m.wap.fcful.cn/nnews/18388.htm
- http://m.wap.fcful.cn/nnews/134658.htm
- http://m.wap.fcful.cn/nnews/160629.htm
- http://m.wap.fcful.cn/nnews/40613.htm
- http://m.wap.fcful.cn/nnews/0224622.htm
- http://m.wap.fcful.cn/nnews/61558.htm
- http://m.wap.fcful.cn/nnews/52795.htm
- http://m.wap.fcful.cn/nnews/8160.htm
- http://m.wap.fcful.cn/nnews/6175135.htm
- http://m.wap.fcful.cn/nnews/0245.htm
- http://m.wap.fcful.cn/nnews/250797.htm
- http://m.wap.fcful.cn/nnews/99116.htm
- http://m.wap.fcful.cn/nnews/8434909.htm
- http://m.wap.fcful.cn/nnews/549973.htm
- http://m.wap.fcful.cn/nnews/54512.htm
- http://m.wap.fcful.cn/nnews/943764.htm
- http://m.wap.fcful.cn/nnews/4003274.htm
- http://m.wap.fcful.cn/nnews/338043.htm
- http://m.wap.fcful.cn/nnews/3121.htm
- http://m.wap.fcful.cn/nnews/233317.htm
- http://m.wap.fcful.cn/nnews/716585.htm
- http://m.wap.fcful.cn/nnews/5367094.htm
- http://m.wap.fcful.cn/nnews/530502.htm
- http://m.wap.fcful.cn/nnews/7065.htm
- http://m.wap.fcful.cn/nnews/8167963.htm
- http://m.wap.fcful.cn/nnews/8518300.htm
- http://m.wap.fcful.cn/nnews/0049598.htm
- http://m.wap.fcful.cn/nnews/049870.htm
- http://m.wap.fcful.cn/nnews/7863.htm
- http://m.wap.fcful.cn/nnews/2673543.htm
- http://m.wap.fcful.cn/nnews/3511151.htm
- http://m.wap.fcful.cn/nnews/9005931.htm
- http://m.wap.fcful.cn/nnews/3379564.htm
- http://m.wap.fcful.cn/nnews/28645.htm
- http://m.wap.fcful.cn/nnews/48830.htm
- http://m.wap.fcful.cn/nnews/19662.htm
- http://m.wap.fcful.cn/nnews/9394711.htm
- http://m.wap.fcful.cn/nnews/32653.htm
- http://m.wap.fcful.cn/nnews/8329235.htm
- http://m.wap.fcful.cn/nnews/3040551.htm
- http://m.wap.fcful.cn/nnews/47842.htm
- http://m.wap.fcful.cn/nnews/100649.htm
- http://m.wap.fcful.cn/nnews/100910.htm
- http://m.wap.fcful.cn/nnews/6017258.htm
- http://m.wap.fcful.cn/nnews/5647395.htm
- http://m.wap.fcful.cn/nnews/74891.htm
- http://m.wap.fcful.cn/nnews/28075.htm
- http://m.wap.fcful.cn/nnews/206939.htm
- http://m.wap.fcful.cn/nnews/1035340.htm
- http://m.wap.fcful.cn/nnews/18590.htm
- http://m.wap.fcful.cn/nnews/236535.htm
- http://m.wap.fcful.cn/nnews/06608.htm
- http://m.wap.fcful.cn/nnews/9597.htm
- http://m.wap.fcful.cn/nnews/729804.htm
- http://m.wap.fcful.cn/nnews/3433.htm
- http://m.wap.fcful.cn/nnews/6579988.htm
- http://m.wap.fcful.cn/nnews/0350723.htm
- http://m.wap.fcful.cn/nnews/0065.htm
- http://m.wap.fcful.cn/nnews/98332.htm

## 项目结构

```
newslink-hub/
├── app/
│   ├── __init__.py                 # Flask 应用工厂，注册蓝图和扩展
│   ├── routes/
│   │   ├── __init__.py             # 路由蓝图汇总
│   │   ├── batch.py                # 批次管理路由（创建、列表、删除）
│   │   ├── links.py                # 链接 CRUD 路由（导入、编辑、状态查询）
│   │   └── health.py               # 健康检查触发与结果展示路由
│   ├── models/
│   │   ├── __init__.py             # ORM 模型基类
│   │   ├── batch.py                # Batch 表模型（批次名称、创建时间、标签）
│   │   └── link.py                 # Link 表模型（URL、状态码、备注、批次外键）
│   ├── services/
│   │   ├── __init__.py             # 服务层导出
│   │   ├── importer.py             # 批量导入服务（支持 CSV/JSON/纯文本）
│   │   ├── checker.py              # 健康检查服务（异步请求池）
│   │   └── indexer.py              # 静态索引生成服务（输出 HTML/Markdown）
│   └── utils/
│       ├── __init__.py             # 工具函数导出
│       ├── validators.py           # URL 格式校验、编号提取
│       └── file_handlers.py        # 文件读写辅助（JSON/CSV 解析）
├── scripts/
│   ├── init_db.py                  # 初始化 SQLite 数据库表结构
│   ├── seed_demo.py                # 填充演示数据（含第 75/240 批占位）
│   └── run_checker.py              # 命令行单独运行健康检查
├── tests/
│   ├── unit/
│   │   ├── test_models.py          # 模型层单元测试
│   │   └── test_services.py        # 服务层单元测试
│   └── integration/
│       └── test_routes.py          # API 路由集成测试
├── docs/                            # 完整文档目录（参见文档导航章节）
├── data/
│   └── newslink.db                 # SQLite 数据库文件（首次初始化后生成）
├── static_index/                    # 静态索引输出目录（由 indexer 服务生成）
├── config.py                        # 应用配置（环境变量映射、默认参数）
├── requirements.txt                 # 生产依赖列表
├── requirements-dev.txt             # 开发额外依赖（pytest, black, flake8）
├── .env.example                     # 环境变量示例文件
├── app.py                           # 应用入口（CLI 与 WSGI 共用）
└── README.md                        # 本文件
```

## 贡献指南

1. 阅读项目行为准则（CODE_OF_CONDUCT.md）并签署贡献者许可协议（CLA），然后从主分支 fork 项目到个人仓库。
2. 在本地创建功能分支（如 feature/batch-import-csv），确保开发环境已安装所有开发依赖（pip install -r requirements-dev.txt）。
3. 编写或修改代码后，运行 black 和 flake8 进行代码格式化和静态检查，并补充对应的单元测试（tests/unit/ 下），确保测试覆盖率不低于 80%。
4. 提交前执行 pytest 确认所有测试通过，并更新相关文档（如 docstring 或用户手册中的对应章节）。
5. 发起 Pull Request 到主分支，描述变更目的、影响范围以及测试结果，等待至少一名维护者审核。

## 常见问题

Q: 导入大量链接时界面响应变慢，如何优化？
A: 推荐使用 CLI 方式进行批量导入（python scripts/importer_cli.py --file links.csv），该方式绕过了 Web 请求超时限制。同时可以将 SQLite 的 journal 模式改为 WAL（Write-Ahead Logging）以提升并发写入性能，具体参考 docs/deployment/sqlite_tuning.md。

Q: 健康检查显示大量链接超时，但浏览器可以直接访问，是什么原因？
A: 健康检查默认超时时间为 3 秒，且不跟随重定向。部分新闻站点可能存在较慢的服务端响应或需要特定的 User-Agent 头。您可以在 config.py 中调整 CHECKER_TIMEOUT 和 CHECKER_HEADERS 参数，或使用 scripts/run_checker.py --timeout 10 临时增加超时阈值。

Q: 如何将现有 Excel 中的链接列表导入系统？
A: 将 Excel 中的 URL 列导出为纯文本文件（每行一个 URL），或保存为 CSV 文件（第一列为 URL）。然后在 Web 界面中进入“批量导入”页面，选择文件类型并上传；也可以使用 CLI 工具：python scripts/importer_cli.py --type csv --file links.csv。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
