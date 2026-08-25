# WAP Knowledge Base Aggregator

WAP Knowledge Base Aggregator 是一个面向移动端资讯聚合与结构化知识库管理的开源工具集，专为需要从移动端 WAP 站点批量采集、归档、检索新闻类内容的技术团队设计。该项目定位于轻量级数据管道，能够将散落在各级目录路径下的 HTML 文档资源统一纳入本地索引体系，并提供基础的全文检索与元数据提取能力。

目标用户包括数据调研工程师、内容运营支撑人员以及个人知识管理爱好者。项目本身不依赖复杂分布式框架，单机即可运行，适合作为数据预处理环节的中间层组件，也适用于中小规模站点的内容镜像与快照管理。

## 功能概览

**批量链接导入** 支持从外部文件或标准输入一次性导入大量资源 URL，自动完成去重与合法性校验。

**结构化元数据提取** 从 URL 路径中自动解析文章编号、发布时间等关键字段，并支持自定义正则表达式规则。

**本地化内容缓存** 将远程 WAP 页面内容下载并存储为本地 HTML 快照，支持增量更新与过期检查。

**全文检索引擎集成** 基于轻量级倒排索引库，提供标题与正文的模糊搜索及精确匹配功能。

**分类标签生成** 根据 URL 目录层级与内容关键词自动生成分类标签，辅助后续聚类分析。

**导出格式多样** 支持将归档数据导出为 JSON、CSV 以及标准 Markdown 表格格式，便于第三方工具消费。

## 应用场景

**竞品内容监控** 市场调研团队可定期抓取指定 WAP 站点的新闻栏目，通过本工具构建历史内容库，用于对比自身产品与竞品的宣传节奏差异。

**个人知识库搭建** 个人开发者可将在移动端浏览到的优质技术文章或行业动态链接统一导入系统，生成带摘要的本地阅读列表，避免遗忘或链接失效。

**历史数据迁移辅助** 当旧版 WAP 站点需要改版或下线时，利用本工具批量导出所有文章元数据与正文内容，作为数据迁移前的备份与校验基准。

**舆情关键词追踪** 运营人员可通过本工具对特定 ID 段落的文章进行高频词统计，快速感知近期热点话题分布情况。

## 快速开始

以下操作基于 Linux/macOS 环境，Windows 用户可通过 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/example/wap-knowledge-aggregator.git
cd wap-knowledge-aggregator

# 安装 Python 依赖（Python 3.8+）
pip install -r requirements.txt

# 初始化本地数据库与索引目录
python scripts/init_db.py --db-path ./data/articles.db --cache-dir ./cache

# 导入资源列表（假设 URL 列表保存在 urls.txt 中，一行一个）
python scripts/import_urls.py --input ./urls.txt --source wap.gqskj.cn

# 启动本地 Web 检索服务（默认端口 8080）
python app.py --port 8080 --debug false
```

访问 `http://127.0.0.1:8080` 即可进入检索界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 ~ 3.11 | 核心运行环境，3.12 及以上版本暂未完成兼容性测试 |
| SQLite | 3.31+ | 内置轻量级关系型数据库，用于存储文章元数据及索引状态 |
| requests | 2.28.0+ | HTTP 客户端库，用于发送 WAP 页面请求及处理重定向 |
| beautifulsoup4 | 4.11.0+ | HTML 解析库，用于从页面正文中提取标题、发布时间等结构化信息 |
| lxml | 4.9.0+ | 作为 beautifulsoup4 的解析引擎，提升大文档处理性能 |
| whoosh | 2.7.4+ | 纯 Python 实现的全文检索引擎，无需额外服务进程 |
| flask | 2.2.0+ | Web 服务框架，仅用于提供检索界面，可独立关闭 |
| tqdm | 4.64.0+ | 进度条显示工具，用于长耗时批量操作时的用户反馈 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何导入自定义 URL 列表、如何执行批量下载、如何通过 Web 界面检索 |
| 运维指南 | docs/ops_guide.md | 如何配置代理、如何调整并发数、如何清理过期缓存文件 |
| 开发者文档 | docs/dev_guide.md | 如何扩展自定义元数据提取器、如何替换全文检索引擎后端 |
| API 参考 | docs/api_reference.md | 各核心模块的函数签名、参数说明及异常类型定义 |
| 设计概述 | docs/design_overview.md | 整体架构图、数据流转路径、各模块职责边界及扩展点设计 |

## 资源列表

- http://m.wap.gqskj.cn/snews/5041805.htm
- http://m.wap.gqskj.cn/snews/6609606.htm
- http://m.wap.gqskj.cn/snews/51538.htm
- http://m.wap.gqskj.cn/snews/1633236.htm
- http://m.wap.gqskj.cn/snews/0650.htm
- http://m.wap.gqskj.cn/snews/7811234.htm
- http://m.wap.gqskj.cn/snews/4969533.htm
- http://m.wap.gqskj.cn/snews/21801.htm
- http://m.wap.gqskj.cn/snews/755444.htm
- http://m.wap.gqskj.cn/snews/80534.htm
- http://m.wap.gqskj.cn/snews/6634414.htm
- http://m.wap.gqskj.cn/snews/65445.htm
- http://m.wap.gqskj.cn/snews/3852623.htm
- http://m.wap.gqskj.cn/snews/01432.htm
- http://m.wap.gqskj.cn/snews/4356.htm
- http://m.wap.gqskj.cn/snews/55092.htm
- http://m.wap.gqskj.cn/snews/7620.htm
- http://m.wap.gqskj.cn/snews/61283.htm
- http://m.wap.gqskj.cn/snews/0397362.htm
- http://m.wap.gqskj.cn/snews/8896830.htm
- http://m.wap.gqskj.cn/snews/6329.htm
- http://m.wap.gqskj.cn/snews/715697.htm
- http://m.wap.gqskj.cn/snews/3465358.htm
- http://m.wap.gqskj.cn/snews/7357.htm
- http://m.wap.gqskj.cn/snews/2298.htm
- http://m.wap.gqskj.cn/snews/1239416.htm
- http://m.wap.gqskj.cn/snews/242410.htm
- http://m.wap.gqskj.cn/snews/89642.htm
- http://m.wap.gqskj.cn/snews/312011.htm
- http://m.wap.gqskj.cn/snews/300968.htm
- http://m.wap.gqskj.cn/snews/323155.htm
- http://m.wap.gqskj.cn/snews/51050.htm
- http://m.wap.gqskj.cn/snews/1692.htm
- http://m.wap.gqskj.cn/snews/357298.htm
- http://m.wap.gqskj.cn/snews/4806139.htm
- http://m.wap.gqskj.cn/snews/1678471.htm
- http://m.wap.gqskj.cn/snews/5892.htm
- http://m.wap.gqskj.cn/snews/84248.htm
- http://m.wap.gqskj.cn/snews/098314.htm
- http://m.wap.gqskj.cn/snews/7255.htm
- http://m.wap.gqskj.cn/snews/657282.htm
- http://m.wap.gqskj.cn/snews/43965.htm
- http://m.wap.gqskj.cn/snews/204285.htm
- http://m.wap.gqskj.cn/snews/445371.htm
- http://m.wap.gqskj.cn/snews/6762645.htm
- http://m.wap.gqskj.cn/snews/639034.htm
- http://m.wap.gqskj.cn/snews/633504.htm
- http://m.wap.gqskj.cn/snews/50161.htm
- http://m.wap.gqskj.cn/snews/8381321.htm
- http://m.wap.gqskj.cn/snews/6552397.htm
- http://m.wap.gqskj.cn/snews/187162.htm
- http://m.wap.gqskj.cn/snews/9284397.htm
- http://m.wap.gqskj.cn/snews/69740.htm
- http://m.wap.gqskj.cn/snews/7079490.htm
- http://m.wap.gqskj.cn/snews/5794271.htm
- http://m.wap.gqskj.cn/snews/6663.htm
- http://m.wap.gqskj.cn/snews/843968.htm
- http://m.wap.gqskj.cn/snews/099088.htm
- http://m.wap.gqskj.cn/snews/672120.htm
- http://m.wap.gqskj.cn/snews/3046919.htm
- http://m.wap.gqskj.cn/snews/88040.htm
- http://m.wap.gqskj.cn/snews/2505411.htm
- http://m.wap.gqskj.cn/snews/8133441.htm
- http://m.wap.gqskj.cn/snews/82469.htm
- http://m.wap.gqskj.cn/snews/1162498.htm
- http://m.wap.gqskj.cn/snews/513436.htm
- http://m.wap.gqskj.cn/snews/79918.htm
- http://m.wap.gqskj.cn/snews/39134.htm
- http://m.wap.gqskj.cn/snews/2963820.htm
- http://m.wap.gqskj.cn/snews/181791.htm
- http://m.wap.gqskj.cn/snews/48537.htm
- http://m.wap.gqskj.cn/snews/20087.htm
- http://m.wap.gqskj.cn/snews/5214.htm
- http://m.wap.gqskj.cn/snews/94075.htm
- http://m.wap.gqskj.cn/snews/48451.htm
- http://m.wap.gqskj.cn/snews/640482.htm
- http://m.wap.gqskj.cn/snews/0695401.htm
- http://m.wap.gqskj.cn/snews/2689951.htm
- http://m.wap.gqskj.cn/snews/2649482.htm
- http://m.wap.gqskj.cn/snews/6289.htm
- http://m.wap.gqskj.cn/snews/9184737.htm
- http://m.wap.gqskj.cn/snews/677589.htm
- http://m.wap.gqskj.cn/snews/9719631.htm
- http://m.wap.gqskj.cn/snews/7894977.htm
- http://m.wap.gqskj.cn/snews/2036.htm
- http://m.wap.gqskj.cn/snews/13198.htm
- http://m.wap.gqskj.cn/snews/3076.htm
- http://m.wap.gqskj.cn/snews/9825.htm
- http://m.wap.gqskj.cn/snews/61037.htm
- http://m.wap.gqskj.cn/snews/465279.htm
- http://m.wap.gqskj.cn/snews/8501.htm
- http://m.wap.gqskj.cn/snews/12240.htm
- http://m.wap.gqskj.cn/snews/8276535.htm
- http://m.wap.gqskj.cn/snews/962814.htm
- http://m.wap.gqskj.cn/snews/767779.htm
- http://m.wap.gqskj.cn/snews/0088272.htm
- http://m.wap.gqskj.cn/snews/92591.htm
- http://m.wap.gqskj.cn/snews/90220.htm
- http://m.wap.gqskj.cn/snews/6958048.htm
- http://m.wap.gqskj.cn/snews/89838.htm
- http://m.wap.gqskj.cn/snews/5379.htm
- http://m.wap.gqskj.cn/snews/60710.htm
- http://m.wap.gqskj.cn/snews/8730.htm
- http://m.wap.gqskj.cn/snews/3468100.htm
- http://m.wap.gqskj.cn/snews/6735272.htm
- http://m.wap.gqskj.cn/snews/3358.htm
- http://m.wap.gqskj.cn/snews/756413.htm
- http://m.wap.gqskj.cn/snews/56132.htm
- http://m.wap.gqskj.cn/snews/7895.htm
- http://m.wap.gqskj.cn/snews/9449510.htm
- http://m.wap.gqskj.cn/snews/6878.htm
- http://m.wap.gqskj.cn/snews/163217.htm
- http://m.wap.gqskj.cn/snews/9388318.htm
- http://m.wap.gqskj.cn/snews/9156110.htm
- http://m.wap.gqskj.cn/snews/456992.htm
- http://m.wap.gqskj.cn/snews/058366.htm
- http://m.wap.gqskj.cn/snews/1487.htm
- http://m.wap.gqskj.cn/snews/1163.htm
- http://m.wap.gqskj.cn/snews/01844.htm
- http://m.wap.gqskj.cn/snews/2308.htm
- http://m.wap.gqskj.cn/snews/77638.htm
- http://m.wap.gqskj.cn/snews/61080.htm
- http://m.wap.gqskj.cn/snews/100826.htm
- http://m.wap.gqskj.cn/snews/64231.htm
- http://m.wap.gqskj.cn/snews/4222631.htm
- http://m.wap.gqskj.cn/snews/2096.htm
- http://m.wap.gqskj.cn/snews/12874.htm
- http://m.wap.gqskj.cn/snews/3406123.htm
- http://m.wap.gqskj.cn/snews/8662.htm
- http://m.wap.gqskj.cn/snews/30819.htm
- http://m.wap.gqskj.cn/snews/1572.htm
- http://m.wap.gqskj.cn/snews/372775.htm
- http://m.wap.gqskj.cn/snews/8053311.htm
- http://m.wap.gqskj.cn/snews/6194085.htm
- http://m.wap.gqskj.cn/snews/852171.htm
- http://m.wap.gqskj.cn/snews/117198.htm
- http://m.wap.gqskj.cn/snews/7882.htm
- http://m.wap.gqskj.cn/snews/02312.htm
- http://m.wap.gqskj.cn/snews/948638.htm
- http://m.wap.gqskj.cn/snews/6410.htm
- http://m.wap.gqskj.cn/snews/9564.htm
- http://m.wap.gqskj.cn/snews/99333.htm
- http://m.wap.gqskj.cn/snews/3559.htm
- http://m.wap.gqskj.cn/snews/603667.htm
- http://m.wap.gqskj.cn/snews/0870.htm
- http://m.wap.gqskj.cn/snews/2762228.htm
- http://m.wap.gqskj.cn/snews/785443.htm
- http://m.wap.gqskj.cn/snews/529883.htm
- http://m.wap.gqskj.cn/snews/0743889.htm
- http://m.wap.gqskj.cn/snews/1946372.htm
- http://m.wap.gqskj.cn/snews/6918.htm
- http://m.wap.gqskj.cn/snews/0981329.htm
- http://m.wap.gqskj.cn/snews/9006.htm
- http://m.wap.gqskj.cn/snews/0089.htm
- http://m.wap.gqskj.cn/snews/5950784.htm
- http://m.wap.gqskj.cn/snews/3087.htm
- http://m.wap.gqskj.cn/snews/9011184.htm
- http://m.wap.gqskj.cn/snews/65856.htm
- http://m.wap.gqskj.cn/snews/0430.htm
- http://m.wap.gqskj.cn/snews/8740881.htm
- http://m.wap.gqskj.cn/snews/333729.htm
- http://m.wap.gqskj.cn/snews/0186741.htm
- http://m.wap.gqskj.cn/snews/088208.htm
- http://m.wap.gqskj.cn/snews/153999.htm
- http://m.wap.gqskj.cn/snews/8740262.htm
- http://m.wap.gqskj.cn/snews/246763.htm
- http://m.wap.gqskj.cn/snews/75189.htm
- http://m.wap.gqskj.cn/snews/2790106.htm
- http://m.wap.gqskj.cn/snews/6041554.htm
- http://m.wap.gqskj.cn/snews/9932.htm
- http://m.wap.gqskj.cn/snews/05859.htm
- http://m.wap.gqskj.cn/snews/86606.htm
- http://m.wap.gqskj.cn/snews/333490.htm
- http://m.wap.gqskj.cn/snews/740851.htm
- http://m.wap.gqskj.cn/snews/627771.htm
- http://m.wap.gqskj.cn/snews/1282.htm
- http://m.wap.gqskj.cn/snews/1530286.htm
- http://m.wap.gqskj.cn/snews/750394.htm
- http://m.wap.gqskj.cn/snews/147476.htm
- http://m.wap.gqskj.cn/snews/83528.htm
- http://m.wap.gqskj.cn/snews/99861.htm
- http://m.wap.gqskj.cn/snews/6640869.htm
- http://m.wap.gqskj.cn/snews/6617622.htm
- http://m.wap.gqskj.cn/snews/3520.htm
- http://m.wap.gqskj.cn/snews/84128.htm
- http://m.wap.gqskj.cn/snews/29080.htm
- http://m.wap.gqskj.cn/snews/7333778.htm
- http://m.wap.gqskj.cn/snews/25348.htm
- http://m.wap.gqskj.cn/snews/224401.htm
- http://m.wap.gqskj.cn/snews/69325.htm
- http://m.wap.gqskj.cn/snews/90937.htm
- http://m.wap.gqskj.cn/snews/5466.htm
- http://m.wap.gqskj.cn/snews/20491.htm
- http://m.wap.gqskj.cn/snews/3453.htm
- http://m.wap.gqskj.cn/snews/78802.htm
- http://m.wap.gqskj.cn/snews/3033.htm
- http://m.wap.gqskj.cn/snews/70564.htm
- http://m.wap.gqskj.cn/snews/358762.htm
- http://m.wap.gqskj.cn/snews/26009.htm
- http://m.wap.gqskj.cn/snews/62497.htm
- http://m.wap.gqskj.cn/snews/03551.htm
- http://m.wap.gqskj.cn/snews/2458403.htm
- http://m.wap.gqskj.cn/snews/722545.htm
- http://m.wap.gqskj.cn/snews/208937.htm
- http://m.wap.gqskj.cn/snews/9019321.htm
- http://m.wap.gqskj.cn/snews/50689.htm
- http://m.wap.gqskj.cn/snews/6728.htm
- http://m.wap.gqskj.cn/snews/0342.htm
- http://m.wap.gqskj.cn/snews/04327.htm
- http://m.wap.gqskj.cn/snews/775439.htm
- http://m.wap.gqskj.cn/snews/7003224.htm
- http://m.wap.gqskj.cn/snews/0962.htm
- http://m.wap.gqskj.cn/snews/7214526.htm
- http://m.wap.gqskj.cn/snews/6209.htm
- http://m.wap.gqskj.cn/snews/46392.htm
- http://m.wap.gqskj.cn/snews/5591997.htm
- http://m.wap.gqskj.cn/snews/5702015.htm
- http://m.wap.gqskj.cn/snews/3645.htm
- http://m.wap.gqskj.cn/snews/5696.htm
- http://m.wap.gqskj.cn/snews/15325.htm
- http://m.wap.gqskj.cn/snews/069582.htm
- http://m.wap.gqskj.cn/snews/53677.htm
- http://m.wap.gqskj.cn/snews/41461.htm
- http://m.wap.gqskj.cn/snews/4509.htm
- http://m.wap.gqskj.cn/snews/12786.htm
- http://m.wap.gqskj.cn/snews/716452.htm
- http://m.wap.gqskj.cn/snews/32165.htm
- http://m.wap.gqskj.cn/snews/262311.htm
- http://m.wap.gqskj.cn/snews/45969.htm
- http://m.wap.gqskj.cn/snews/6184.htm
- http://m.wap.gqskj.cn/snews/1331980.htm
- http://m.wap.gqskj.cn/snews/51879.htm
- http://m.wap.gqskj.cn/snews/0330934.htm
- http://m.wap.gqskj.cn/snews/40458.htm
- http://m.wap.gqskj.cn/snews/307518.htm
- http://m.wap.gqskj.cn/snews/50433.htm
- http://m.wap.gqskj.cn/snews/0276859.htm
- http://m.wap.gqskj.cn/snews/260258.htm
- http://m.wap.gqskj.cn/snews/517105.htm
- http://m.wap.gqskj.cn/snews/853520.htm
- http://m.wap.gqskj.cn/snews/6062355.htm
- http://m.wap.gqskj.cn/snews/0369942.htm
- http://m.wap.gqskj.cn/snews/918998.htm
- http://m.wap.gqskj.cn/snews/968400.htm
- http://m.wap.gqskj.cn/snews/3616210.htm
- http://m.wap.gqskj.cn/snews/37287.htm
- http://m.wap.gqskj.cn/snews/5621.htm
- http://m.wap.gqskj.cn/snews/2215.htm
- http://m.wap.gqskj.cn/snews/93088.htm
- http://m.wap.gqskj.cn/snews/16938.htm

## 项目结构

```
wap-knowledge-aggregator/
├── app.py                      # Web 服务主入口，包含路由注册与全局异常处理器
├── requirements.txt            # 第三方依赖清单，固定版本号以确保环境一致性
├── config/
│   ├── settings.py             # 全局配置项：数据库路径、并发数、超时阈值、代理设置
│   └── logging.conf            # 日志级别及输出格式配置（按天滚动）
├── core/
│   ├── __init__.py
│   ├── fetcher.py              # 异步 HTTP 请求封装，含重试与熔断逻辑
│   ├── parser.py               # HTML 解析器，基于 BeautifulSoup 实现元数据抽取
│   ├── indexer.py              # Whoosh 索引管理，含建立、更新、删除及查询接口
│   └── storage.py              # SQLite 存储层，封装 CRUD 及批量插入事务
├── scripts/
│   ├── init_db.py              # 首次运行初始化脚本：建表、建索引目录、创建管理员账户
│   ├── import_urls.py          # 批量导入入口，支持去重校验及进度显示
│   └── export_data.py          # 导出模块，支持 JSON/CSV/Markdown 三种格式
├── tests/
│   ├── test_fetcher.py         # 模拟 HTTP 服务的单元测试，覆盖超时与异常路径
│   ├── test_parser.py          # 针对不同 HTML 结构样本的解析正确性验证
│   └── test_indexer.py         # 全文检索的相关性评分与排序逻辑测试
├── docs/
│   ├── user_guide.md           # 面向最终用户的详细操作手册
│   ├── ops_guide.md            # 面向运维人员的部署与监控指南
│   └── dev_guide.md            # 面向贡献者的代码规范与模块设计说明
├── cache/                      # 本地 HTML 快照存储目录（默认为空，运行时自动填充）
├── data/                       # SQLite 数据库文件及 Whoosh 索引文件存放路径
└── logs/                       # 应用运行日志存储目录（按日切割，保留 30 天）
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账户，并 clone 到本地开发环境。确保本地 Python 版本符合要求，推荐使用虚拟环境隔离依赖。

2. 选取未被分配的 issue 或自行创建新 issue 说明拟解决的问题或新增功能，等待核心维护者确认范围与方案可行性。

3. 基于 main 分支创建以 feature/ 或 fix/ 为前缀的命名分支，例如 `feature/add-rss-output` 或 `fix/parser-encoding-error`。分支内提交应保持原子化，每条提交信息需以动词开头，简明描述变更内容。

4. 编写或更新对应的单元测试用例，确保新增代码的测试覆盖率达到 85% 以上。运行 `pytest tests/` 验证全部用例通过且无回归问题。

5. 提交 pull request 至 upstream 仓库的 main 分支，并在 PR 描述中关联对应的 issue 编号。CI 流水线将自动执行代码风格检查（flake8）及全套测试用例。至少两位核心维护者 review 通过后即可合并。

## 常见问题

**问：导入大量 URL 时出现超时或连接拒绝错误如何处理？**

答：网络环境不稳定时，fetcher 模块默认启用指数退避重试机制（初始间隔 1 秒，最大间隔 30 秒，最多重试 3 次）。若仍频繁失败，建议检查代理配置，在 `config/settings.py` 中设置 `HTTP_PROXY` 与 `HTTPS_PROXY` 环境变量。也可通过 `--concurrency` 参数降低并发数（默认 10），以减少对目标服务器的压力。

**问：全文检索返回的结果不完整或排序不符合预期？**

答：Whoosh 索引默认对标题字段赋予较高权重，正文次之。如果检索效果不理想，可手动调整 `core/indexer.py` 中的 `Field` 权重参数。此外，索引更新并非实时生效，导入新数据后需调用 `indexer.commit()` 或重启 Web 服务触发索引刷新。若数据量巨大，可考虑改用 Elasticsearch 作为后端，项目已预留扩展接口。

**问：如何迁移数据库及缓存文件到另一台服务器？**

答：迁移时需一并打包 `data/` 目录下的 `articles.db` 文件及 `whoosh_index/` 子目录，以及 `cache/` 下的所有 HTML 快照文件。在目标服务器上解压至相同相对路径，或修改 `config/settings.py` 中的 `DB_PATH`、`INDEX_PATH`、`CACHE_DIR` 三个配置项指向新位置。确保目标环境已安装相同版本的依赖库，否则可能出现序列化兼容性问题。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
