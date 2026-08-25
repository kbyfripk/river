# NewsLink Archive

NewsLink Archive 是一个面向数据采集、内容聚合与历史新闻资源归档的开源外链管理工具。该项目旨在为研究人员、数据分析师以及内容运营团队提供一套标准化的新闻链接收集、清洗、分类与持久化存储方案。通过将分散的移动端新闻页面索引化为结构化的外链资源池，NewsLink Archive 帮助用户构建可追溯、可审计、可二次分发的内容资产库。

本项目聚焦于处理以移动端新闻门户为代表的高频更新内容源，提供从 URL 规范化、去重校验到元数据抽取的完整工具链。项目本身不提供具体新闻内容的渲染或展示，而是作为上游数据供应链的基础设施层，专注于链接层面的资源治理。

## 功能概览

批量链接导入与解析：支持从文本文件、CSV 或标准输入流中批量导入原始新闻链接，自动完成协议校验、域名白名单过滤及路径规格化，降低人工整理成本。

递归内容指纹计算：对每个导入链接执行基于响应头与摘要内容块的指纹生成算法，用于后续的变更检测与重复判定，确保资源池的唯一性。

元数据抽取与索引：从目标页面中抽取发布时间、内容摘要、信息分类等元数据字段，并写入本地 SQLite 索引库，供查询与导出使用。

多格式导出管线：支持将已归档的链接资源导出为 JSON、CSV 或纯文本列表格式，便于接入下游数据分析流水线或静态站点生成器。

增量更新与状态追踪：自动记录每次采集任务的时间戳、成功数、失败数及失败原因，支持按日期范围检索历史采集记录，实现采集进度的可视化追踪。

自定义过滤规则引擎：提供基于正则表达式的灵活过滤配置，允许用户按路径前缀、文件扩展名或自定义关键词对链接进行包含或排除操作。

本地 Web 管理界面：内置基于 Flask 的轻量级管理面板，提供链接列表浏览、条件筛选、手动添加与删除等基本操作能力，无需依赖外部数据库。

## 应用场景

移动端新闻内容聚合平台的初始化数据采集：团队在搭建新的新闻聚合服务时，可使用 NewsLink Archive 对指定的移动端新闻站点进行全量链接扫描，快速建立初始的内容索引库，并作为后续增量更新的基础。

历史新闻链接的合规性审计与归档：企业法务或合规部门需要对过往发布的新闻链接进行来源追溯与内容留存验证时，可通过本工具将所有链接导出为带有时间戳的审计清单，便于与原始发布系统进行交叉比对。

学术研究中的新闻传播分析数据准备：社会科学研究人员在分析特定事件的媒体报道扩散路径时，可利用本工具将多个新闻站点的链接汇总为统一的语料索引，进而配合爬虫框架进行更深层次的内容抓取与语义分析。

内容管理系统（CMS）的数据迁移辅助：在将旧版 CMS 迁移至新平台时，可使用 NewsLink Archive 对旧系统中的外部新闻链接进行批量梳理，剔除失效链接并生成迁移所需的映射表，有效降低迁移过程中的数据丢失风险。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动本地开发服务器。

```bash
git clone https://github.com/newsarchive/news-link-archive.git
cd news-link-archive
pip install -r requirements.txt
python scripts/init_db.py
python app.py
```

执行上述命令后，本地 Web 服务将在 http://127.0.0.1:5000 启动。用户可通过浏览器访问管理界面，或使用命令行工具 `cli.py` 进行批量操作：

```bash
python cli.py import --file samples/links.txt
python cli.py list --limit 20
python cli.py export --format json --output archive.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，低于 3.9 版本将不兼容类型注解语法 |
| SQLite3 | 3.35.0 及以上 | 内置于 Python 标准库，用于存储链接索引与采集元数据 |
| Flask | 2.2.5 | Web 管理界面依赖的轻量级服务框架 |
| requests | 2.28.2 | 发送 HTTP 请求以获取页面响应头及摘要内容 |
| lxml | 4.9.2 | 用于解析 HTML 文档并提取元数据字段，性能优于内置 html.parser |
| pytest | 7.2.0 | 单元测试与集成测试框架，仅开发环境需要 |
| black | 22.12.0 | 代码格式化工具，仅贡献代码时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何导入链接、配置过滤规则、执行导出以及使用 Web 界面进行日常管理 |
| 开发者指南 | docs/developer_guide.md | 项目整体架构设计、核心模块职责划分、自定义过滤器的编写规范与单元测试编写建议 |
| API 参考 | docs/api_reference.md | 各 Python 模块的公开函数签名、类定义、异常类型及使用示例 |
| 部署说明 | docs/deployment.md | 在生产环境中使用 Gunicorn 或 uWSGI 部署 Web 服务，以及使用 systemd 实现开机自启的配置模板 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/471986.htm
- http://m.3g.gqskj.cn/xnews/88282.htm
- http://m.3g.gqskj.cn/xnews/6311711.htm
- http://m.3g.gqskj.cn/xnews/1288.htm
- http://m.3g.gqskj.cn/xnews/37137.htm
- http://m.3g.gqskj.cn/xnews/3950560.htm
- http://m.3g.gqskj.cn/xnews/0046.htm
- http://m.3g.gqskj.cn/xnews/6827.htm
- http://m.3g.gqskj.cn/xnews/226742.htm
- http://m.3g.gqskj.cn/xnews/204667.htm
- http://m.3g.gqskj.cn/xnews/1805605.htm
- http://m.3g.gqskj.cn/xnews/637104.htm
- http://m.3g.gqskj.cn/xnews/462507.htm
- http://m.3g.gqskj.cn/xnews/8898300.htm
- http://m.3g.gqskj.cn/xnews/5255.htm
- http://m.3g.gqskj.cn/xnews/3451204.htm
- http://m.3g.gqskj.cn/xnews/117781.htm
- http://m.3g.gqskj.cn/xnews/5111257.htm
- http://m.3g.gqskj.cn/xnews/81265.htm
- http://m.3g.gqskj.cn/xnews/8922.htm
- http://m.3g.gqskj.cn/xnews/8843.htm
- http://m.3g.gqskj.cn/xnews/9215196.htm
- http://m.3g.gqskj.cn/xnews/97978.htm
- http://m.3g.gqskj.cn/xnews/959918.htm
- http://m.3g.gqskj.cn/xnews/241598.htm
- http://m.3g.gqskj.cn/xnews/290470.htm
- http://m.3g.gqskj.cn/xnews/18658.htm
- http://m.3g.gqskj.cn/xnews/18485.htm
- http://m.3g.gqskj.cn/xnews/8781.htm
- http://m.3g.gqskj.cn/xnews/639557.htm
- http://m.3g.gqskj.cn/xnews/00022.htm
- http://m.3g.gqskj.cn/xnews/49729.htm
- http://m.3g.gqskj.cn/xnews/9262021.htm
- http://m.3g.gqskj.cn/xnews/479797.htm
- http://m.3g.gqskj.cn/xnews/894599.htm
- http://m.3g.gqskj.cn/xnews/6594.htm
- http://m.3g.gqskj.cn/xnews/6641.htm
- http://m.3g.gqskj.cn/xnews/59668.htm
- http://m.3g.gqskj.cn/xnews/8984.htm
- http://m.3g.gqskj.cn/xnews/6142.htm
- http://m.3g.gqskj.cn/xnews/1574465.htm
- http://m.3g.gqskj.cn/xnews/3019.htm
- http://m.3g.gqskj.cn/xnews/7383650.htm
- http://m.3g.gqskj.cn/xnews/5541139.htm
- http://m.3g.gqskj.cn/xnews/8107743.htm
- http://m.3g.gqskj.cn/xnews/0323.htm
- http://m.3g.gqskj.cn/xnews/934000.htm
- http://m.3g.gqskj.cn/xnews/8915815.htm
- http://m.3g.gqskj.cn/xnews/1037640.htm
- http://m.3g.gqskj.cn/xnews/537904.htm
- http://m.3g.gqskj.cn/xnews/37632.htm
- http://m.3g.gqskj.cn/xnews/1274.htm
- http://m.3g.gqskj.cn/xnews/8209661.htm
- http://m.3g.gqskj.cn/xnews/966224.htm
- http://m.3g.gqskj.cn/xnews/661257.htm
- http://m.3g.gqskj.cn/xnews/4097329.htm
- http://m.3g.gqskj.cn/xnews/326918.htm
- http://m.3g.gqskj.cn/xnews/7691.htm
- http://m.3g.gqskj.cn/xnews/37256.htm
- http://m.3g.gqskj.cn/xnews/995283.htm
- http://m.3g.gqskj.cn/xnews/40883.htm
- http://m.3g.gqskj.cn/xnews/45590.htm
- http://m.3g.gqskj.cn/xnews/0539323.htm
- http://m.3g.gqskj.cn/xnews/3693034.htm
- http://m.3g.gqskj.cn/xnews/9654.htm
- http://m.3g.gqskj.cn/xnews/4083975.htm
- http://m.3g.gqskj.cn/xnews/271089.htm
- http://m.3g.gqskj.cn/xnews/940824.htm
- http://m.3g.gqskj.cn/xnews/3888.htm
- http://m.3g.gqskj.cn/xnews/72036.htm
- http://m.3g.gqskj.cn/xnews/151622.htm
- http://m.3g.gqskj.cn/xnews/38430.htm
- http://m.3g.gqskj.cn/xnews/4220.htm
- http://m.3g.gqskj.cn/xnews/708011.htm
- http://m.3g.gqskj.cn/xnews/8484609.htm
- http://m.3g.gqskj.cn/xnews/87972.htm
- http://m.3g.gqskj.cn/xnews/8393583.htm
- http://m.3g.gqskj.cn/xnews/2571.htm
- http://m.3g.gqskj.cn/xnews/861972.htm
- http://m.3g.gqskj.cn/xnews/3987.htm
- http://m.3g.gqskj.cn/xnews/827586.htm
- http://m.3g.gqskj.cn/xnews/5883123.htm
- http://m.3g.gqskj.cn/xnews/109429.htm
- http://m.3g.gqskj.cn/xnews/3496.htm
- http://m.3g.gqskj.cn/xnews/3951689.htm
- http://m.3g.gqskj.cn/xnews/713625.htm
- http://m.3g.gqskj.cn/xnews/5663265.htm
- http://m.3g.gqskj.cn/xnews/7692033.htm
- http://m.3g.gqskj.cn/xnews/062772.htm
- http://m.3g.gqskj.cn/xnews/8418.htm
- http://m.3g.gqskj.cn/xnews/79042.htm
- http://m.3g.gqskj.cn/xnews/318371.htm
- http://m.3g.gqskj.cn/xnews/8679.htm
- http://m.3g.gqskj.cn/xnews/96182.htm
- http://m.3g.gqskj.cn/xnews/1315931.htm
- http://m.3g.gqskj.cn/xnews/4604.htm
- http://m.3g.gqskj.cn/xnews/90529.htm
- http://m.3g.gqskj.cn/xnews/499454.htm
- http://m.3g.gqskj.cn/xnews/392566.htm
- http://m.3g.gqskj.cn/xnews/564076.htm
- http://m.3g.gqskj.cn/xnews/00122.htm
- http://m.3g.gqskj.cn/xnews/726070.htm
- http://m.3g.gqskj.cn/xnews/1549360.htm
- http://m.3g.gqskj.cn/xnews/03970.htm
- http://m.3g.gqskj.cn/xnews/94983.htm
- http://m.3g.gqskj.cn/xnews/851472.htm
- http://m.3g.gqskj.cn/xnews/60529.htm
- http://m.3g.gqskj.cn/xnews/14193.htm
- http://m.3g.gqskj.cn/xnews/49625.htm
- http://m.3g.gqskj.cn/xnews/5134.htm
- http://m.3g.gqskj.cn/xnews/9402.htm
- http://m.3g.gqskj.cn/xnews/5965237.htm
- http://m.3g.gqskj.cn/xnews/7592980.htm
- http://m.3g.gqskj.cn/xnews/6985243.htm
- http://m.3g.gqskj.cn/xnews/4837867.htm
- http://m.3g.gqskj.cn/xnews/2067671.htm
- http://m.3g.gqskj.cn/xnews/3904632.htm
- http://m.3g.gqskj.cn/xnews/175016.htm
- http://m.3g.gqskj.cn/xnews/9255.htm
- http://m.3g.gqskj.cn/xnews/335646.htm
- http://m.3g.gqskj.cn/xnews/5230954.htm
- http://m.3g.gqskj.cn/xnews/24389.htm
- http://m.3g.gqskj.cn/xnews/377801.htm
- http://m.3g.gqskj.cn/xnews/71141.htm
- http://m.3g.gqskj.cn/xnews/1301089.htm
- http://m.3g.gqskj.cn/xnews/1890530.htm
- http://m.3g.gqskj.cn/xnews/297521.htm
- http://m.3g.gqskj.cn/xnews/594265.htm
- http://m.3g.gqskj.cn/xnews/096080.htm
- http://m.3g.gqskj.cn/xnews/11502.htm
- http://m.3g.gqskj.cn/xnews/6026912.htm
- http://m.3g.gqskj.cn/xnews/007079.htm
- http://m.3g.gqskj.cn/xnews/37732.htm
- http://m.3g.gqskj.cn/xnews/632613.htm
- http://m.3g.gqskj.cn/xnews/8581555.htm
- http://m.3g.gqskj.cn/xnews/4266573.htm
- http://m.3g.gqskj.cn/xnews/5570195.htm
- http://m.3g.gqskj.cn/xnews/3978.htm
- http://m.3g.gqskj.cn/xnews/779180.htm
- http://m.3g.gqskj.cn/xnews/9456809.htm
- http://m.3g.gqskj.cn/xnews/37151.htm
- http://m.3g.gqskj.cn/xnews/7114.htm
- http://m.3g.gqskj.cn/xnews/7836.htm
- http://m.3g.gqskj.cn/xnews/91763.htm
- http://m.3g.gqskj.cn/xnews/24387.htm
- http://m.3g.gqskj.cn/xnews/45808.htm
- http://m.3g.gqskj.cn/xnews/6297735.htm
- http://m.3g.gqskj.cn/xnews/7612406.htm
- http://m.3g.gqskj.cn/xnews/3878670.htm
- http://m.3g.gqskj.cn/xnews/1032.htm
- http://m.3g.gqskj.cn/xnews/095472.htm
- http://m.3g.gqskj.cn/xnews/35139.htm
- http://m.3g.gqskj.cn/xnews/9270862.htm
- http://m.3g.gqskj.cn/xnews/21832.htm
- http://m.3g.gqskj.cn/xnews/7741678.htm
- http://m.3g.gqskj.cn/xnews/24616.htm
- http://m.3g.gqskj.cn/xnews/2538.htm
- http://m.3g.gqskj.cn/xnews/18340.htm
- http://m.3g.gqskj.cn/xnews/9040.htm
- http://m.3g.gqskj.cn/xnews/6523340.htm
- http://m.3g.gqskj.cn/xnews/438892.htm
- http://m.3g.gqskj.cn/xnews/099495.htm
- http://m.3g.gqskj.cn/xnews/4497343.htm
- http://m.3g.gqskj.cn/xnews/930650.htm
- http://m.3g.gqskj.cn/xnews/0679744.htm
- http://m.3g.gqskj.cn/xnews/5404.htm
- http://m.3g.gqskj.cn/xnews/606059.htm
- http://m.3g.gqskj.cn/xnews/7990494.htm
- http://m.3g.gqskj.cn/xnews/7225515.htm
- http://m.3g.gqskj.cn/xnews/8597493.htm
- http://m.3g.gqskj.cn/xnews/3380.htm
- http://m.3g.gqskj.cn/xnews/2160462.htm
- http://m.3g.gqskj.cn/xnews/255227.htm
- http://m.3g.gqskj.cn/xnews/5916510.htm
- http://m.3g.gqskj.cn/xnews/5973733.htm
- http://m.3g.gqskj.cn/xnews/47103.htm
- http://m.3g.gqskj.cn/xnews/58888.htm
- http://m.3g.gqskj.cn/xnews/5498466.htm
- http://m.3g.gqskj.cn/xnews/18762.htm
- http://m.3g.gqskj.cn/xnews/2583.htm
- http://m.3g.gqskj.cn/xnews/3880.htm
- http://m.3g.gqskj.cn/xnews/39014.htm
- http://m.3g.gqskj.cn/xnews/5538629.htm
- http://m.3g.gqskj.cn/xnews/336506.htm
- http://m.3g.gqskj.cn/xnews/015376.htm
- http://m.3g.gqskj.cn/xnews/153935.htm
- http://m.3g.gqskj.cn/xnews/80019.htm
- http://m.3g.gqskj.cn/xnews/915682.htm
- http://m.3g.gqskj.cn/xnews/5864286.htm
- http://m.3g.gqskj.cn/xnews/5692238.htm
- http://m.3g.gqskj.cn/xnews/376441.htm
- http://m.3g.gqskj.cn/xnews/9688.htm
- http://m.3g.gqskj.cn/xnews/3967032.htm
- http://m.3g.gqskj.cn/xnews/202641.htm
- http://m.3g.gqskj.cn/xnews/0014915.htm
- http://m.3g.gqskj.cn/xnews/52057.htm
- http://m.3g.gqskj.cn/xnews/9243.htm
- http://m.3g.gqskj.cn/xnews/1173069.htm
- http://m.3g.gqskj.cn/xnews/7181.htm
- http://m.3g.gqskj.cn/xnews/2313207.htm
- http://m.3g.gqskj.cn/xnews/9501572.htm
- http://m.3g.gqskj.cn/xnews/5655446.htm
- http://m.3g.gqskj.cn/xnews/219466.htm
- http://m.3g.gqskj.cn/xnews/95867.htm
- http://m.3g.gqskj.cn/xnews/2621816.htm
- http://m.3g.gqskj.cn/xnews/8724.htm
- http://m.3g.gqskj.cn/xnews/5255832.htm
- http://m.3g.gqskj.cn/xnews/63833.htm
- http://m.3g.gqskj.cn/xnews/9945.htm
- http://m.3g.gqskj.cn/xnews/7276.htm
- http://m.3g.gqskj.cn/xnews/9084.htm
- http://m.3g.gqskj.cn/xnews/82846.htm
- http://m.3g.gqskj.cn/xnews/196922.htm
- http://m.3g.gqskj.cn/xnews/27078.htm
- http://m.3g.gqskj.cn/xnews/9547945.htm
- http://m.3g.gqskj.cn/xnews/58067.htm
- http://m.3g.gqskj.cn/xnews/1241715.htm
- http://m.3g.gqskj.cn/xnews/924657.htm
- http://m.3g.gqskj.cn/xnews/8138.htm
- http://m.3g.gqskj.cn/xnews/92396.htm
- http://m.3g.gqskj.cn/xnews/6010799.htm
- http://m.3g.gqskj.cn/xnews/0934.htm
- http://m.3g.gqskj.cn/xnews/582895.htm
- http://m.3g.gqskj.cn/xnews/870286.htm
- http://m.3g.gqskj.cn/xnews/922293.htm
- http://m.3g.gqskj.cn/xnews/2861080.htm
- http://m.3g.gqskj.cn/xnews/24485.htm
- http://m.3g.gqskj.cn/xnews/8221.htm
- http://m.3g.gqskj.cn/xnews/18410.htm
- http://m.3g.gqskj.cn/xnews/269725.htm
- http://m.3g.gqskj.cn/xnews/96019.htm
- http://m.3g.gqskj.cn/xnews/840785.htm
- http://m.3g.gqskj.cn/xnews/8953246.htm
- http://m.3g.gqskj.cn/xnews/702636.htm
- http://m.3g.gqskj.cn/xnews/48690.htm
- http://m.3g.gqskj.cn/xnews/6326804.htm
- http://m.3g.gqskj.cn/xnews/51873.htm
- http://m.3g.gqskj.cn/xnews/1353589.htm
- http://m.3g.gqskj.cn/xnews/797433.htm
- http://m.3g.gqskj.cn/xnews/55589.htm
- http://m.3g.gqskj.cn/xnews/4741.htm
- http://m.3g.gqskj.cn/xnews/897055.htm
- http://m.3g.gqskj.cn/xnews/792956.htm
- http://m.3g.gqskj.cn/xnews/297122.htm
- http://m.3g.gqskj.cn/xnews/64044.htm
- http://m.3g.gqskj.cn/xnews/67697.htm
- http://m.3g.gqskj.cn/xnews/9528.htm
- http://m.3g.gqskj.cn/xnews/11854.htm
- http://m.3g.gqskj.cn/xnews/2562134.htm
- http://m.3g.gqskj.cn/xnews/6040.htm

## 项目结构

```
news-link-archive/
├── app.py                      # Flask Web 管理界面入口，包含路由定义与上下文处理器
├── cli.py                      # 命令行工具入口，提供导入、导出、列表等子命令
├── requirements.txt            # 生产环境依赖列表，锁定关键库版本
├── config.py                   # 全局配置项，包含数据库路径、请求超时、分页大小等
├── scripts/
│   ├── init_db.py              # 初始化 SQLite 数据库表结构，创建索引
│   ├── migrate_v1_to_v2.py     # 数据库迁移脚本，用于版本升级时的结构变更
│   └── sample_links.txt        # 示例链接文件，供测试导入功能使用
├── core/
│   ├── __init__.py
│   ├── fetcher.py              # 封装 requests 会话，负责获取页面响应头与部分正文
│   ├── parser.py               # 基于 lxml 的元数据抽取器，提取时间、标题、分类等
│   ├── fingerprint.py          # 计算内容指纹，用于去重与变更检测
│   ├── filter_engine.py        # 正则表达式过滤规则引擎，支持包含/排除模式
│   └── exporter.py             # 导出管线实现，支持 JSON、CSV、纯文本三种格式
├── storage/
│   ├── __init__.py
│   ├── connection.py           # SQLite 数据库连接池与上下文管理器
│   ├── repository.py           # 链接记录的 CRUD 操作，封装所有 SQL 语句
│   └── models.py               # 数据类定义，映射 link 表与 task 表结构
├── web/
│   ├── __init__.py
│   ├── templates/              # Jinja2 模板目录，包含列表页、详情页、任务页
│   │   ├── base.html
│   │   ├── index.html
│   │   ├── links.html
│   │   └── tasks.html
│   └── static/                 # CSS 样式表与前端交互脚本
│       ├── style.css
│       └── app.js
├── tests/
│   ├── test_fetcher.py         # 模拟 HTTP 响应的单元测试，覆盖超时与重试逻辑
│   ├── test_parser.py          # 使用预置 HTML 样本验证元数据抽取准确性
│   ├── test_fingerprint.py     # 校验指纹算法的一致性与碰撞概率
│   └── test_integration.py     # 端到端集成测试，覆盖导入、查询、导出完整流程
└── docs/                       # 详细文档目录，与文档导航章节对应
    ├── user_guide.md
    ├── developer_guide.md
    ├── api_reference.md
    └── deployment.md
```

## 贡献指南

1. 查阅开发者指南与 API 参考文档，了解项目的整体架构设计、模块职责划分以及现有的测试覆盖范围，确保对代码库有全局认知后再着手修改。

2. 在 GitHub 上 fork 本仓库并创建特性分支，分支命名遵循 `feature/简短描述` 或 `fix/问题编号` 的格式。提交代码前请运行 `black` 进行代码格式化，并通过 `pytest` 确保所有测试用例通过。

3. 为新增功能编写对应的单元测试或集成测试，测试用例应覆盖正常路径、边界条件以及异常处理路径。对于涉及外部 HTTP 请求的代码，优先使用 `requests-mock` 库进行模拟，避免在测试过程中产生真实的网络流量。

4. 提交 pull request 时，请在描述中清晰说明本次变更的目的、实现方式以及影响范围。若修复了已登记的 issue，请使用 `Closes #issue号` 的语法进行关联。PR 需要至少一名维护者审核后方可合并。

5. 若发现安全漏洞或敏感数据泄露风险，请勿公开提交 issue，而是通过项目邮箱 newsarchive@example.org 进行私下报告，我们将在 48 小时内响应并处理。

## 常见问题

Q: 导入大量链接时出现超时或连接被重置错误，如何处理？

A: 这是由于目标服务器对单 IP 的并发请求数有限制所致。建议使用 `cli.py import` 命令的 `--delay` 参数设置请求间隔（单位毫秒），默认值为 500 毫秒。若问题依旧存在，可在 `config.py` 中调整 `REQUEST_TIMEOUT` 与 `MAX_RETRIES` 参数。对于大规模导入任务，推荐将链接列表拆分为多个小批次，分时段执行。

Q: 如何自定义元数据抽取规则以适配不同结构的新闻页面？

A: 项目在 `core/parser.py` 中提供了基于 XPath 和 CSS 选择器的可配置抽取器。用户无需修改核心代码，只需在项目根目录创建 `extract_rules.yaml` 文件，按域名配置不同的标题、时间、正文摘要的提取路径即可。具体配置格式请参考 `docs/user_guide.md` 中的自定义抽取规则章节。

Q: 导出的 JSON 文件中包含哪些字段，能否增加自定义字段？

A: 默认导出的 JSON 包含 `url`、`fingerprint`、`title`、`published_at`、`category`、`first_seen`、`last_checked` 和 `status_code` 共八个字段。若需要增加额外字段，可在 `core/parser.py` 的 `extract_metadata` 函数中扩展返回字典的键值对，并在 `storage/models.py` 的 `LinkRecord` 数据类中添加对应的属性定义。扩展后请同步更新 `docs/api_reference.md` 中的相关说明。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:53
