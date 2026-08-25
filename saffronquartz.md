# LinkVault 聚合资源索引系统

LinkVault 是一个面向技术内容聚合与知识库管理的静态资源索引系统，专门用于批量处理、分类归档和快速检索海量外链数据。系统以轻量级 Markdown 结构为核心，配合元数据标签体系，提供可扩展的链接仓库管理能力。项目适用于技术文档站点运维、信息流聚合平台、企业内部知识库建设等场景，帮助用户在高频更新的资源流中建立可维护的索引目录。目标用户包括技术内容运营人员、开源文档维护者、个人知识管理实践者以及需要批量处理 URL 资源的自动化脚本开发者。

## 功能概览

**批量链接导入与去重校验**：支持通过文本流或 CSV 文件批量导入 URL，自动检测重复条目并进行格式规范化处理，内置基于哈希值的重复检测机制，确保资源库内唯一性。

**层级化目录分类系统**：提供四级分类维度，包含来源域名、内容主题、文件类型、时效性标签，用户可自定义分类规则，每个链接允许同时归属多个分类节点。

**全文检索与正则过滤**：基于 URL 路径和查询参数的关键词检索，支持正则表达式模式匹配，能够快速筛选出符合特定命名规范或编号规则的资源条目，便于定向提取。

**资源状态监测与断链标记**：集成 HTTP 状态码探测模块，定期检查链接可访问性，对返回 4xx 或 5xx 状态的链接自动标记为失效并记录检测时间，生成断链报告。

**动态标签引擎**：依据 URL 中的路径特征、文件扩展名、数字编号区间等规则自动生成标签，用户也可手动添加或删除标签，支持标签组合筛选与权重排序。

**导出与集成接口**：支持将索引数据导出为 JSON、CSV、纯文本列表三种格式，同时提供 HTTP API 接口供外部系统调用，便于集成到 CI/CD 流水线或文档生成工具中。

## 应用场景

技术博客站点的外链资源归档：技术博客作者在撰写文章时需要引用大量外部参考来源，使用 LinkVault 可以为每篇文章建立独立的引用索引表，自动检测引用链接的有效性，避免文章发布后出现死链影响阅读体验。

开源项目文档的依赖与参考管理：开源项目的 README 或用户手册中通常需要列出相关的依赖库、工具链、学习资料等外部链接，LinkVault 能够将这些链接结构化存储，并在项目版本更新时快速对比链接变化，确保文档中的参考资源始终与当前版本匹配。

企业内部知识库的批量链接清洗：企业内网知识库积累了大量历史文章，其中包含许多已失效或迁移的内部链接，运维团队可借助 LinkVault 的批量导入和状态监测功能，对全库链接进行系统性扫描，生成失效链接清单并批量替换为目标地址。

数据采集管道的原始 URL 暂存与预处理：在数据采集流程中，爬虫程序会生成大量中间态 URL 需要暂存和初步分类，LinkVault 可作为轻量级 URL 暂存池，对原始链接进行去重、打标和分类后再转入下游处理环节，简化数据管道的架构设计。

个人知识管理中的书签库迁移与整合：从浏览器书签、Pocket、Instapaper 等不同平台导出的书签数据格式各异，LinkVault 提供了统一的数据导入格式和分类模型，帮助用户将分散的书签整合为一个可检索、可维护的单一索引库。

## 快速开始

以下命令演示如何在本地环境中获取 LinkVault 源码、安装依赖并启动索引服务。

```bash
git clone https://github.com/your-org/linkvault.git
cd linkvault
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py import --input ./samples/links.txt
python manage.py serve --host 127.0.0.1 --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时环境，用于执行索引引擎和 API 服务 |
| SQLite | 3.35 及以上 | 默认元数据存储引擎，支持 JSON 字段类型用于标签存储 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于链接状态探测和资源抓取 |
| click | 8.1.0 及以上 | 命令行交互框架，提供子命令解析和参数校验 |
| pytest | 7.2.0 及以上 | 单元测试框架，用于开发和维护阶段的功能验证 |
| gunicorn | 20.1.0 及以上 | WSGI HTTP 服务器，用于生产环境的 API 服务部署 |
| python-dotenv | 0.21.0 及以上 | 环境变量管理，支持从 .env 文件加载配置参数 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速启动服务、导入第一批链接、生成索引页面 |
| 分类体系说明 | docs/taxonomy.md | 系统内置的分类维度有哪些，如何自定义分类规则和标签策略 |
| API 参考手册 | docs/api_reference.md | HTTP API 各个端点的请求格式、参数说明、返回结构及错误码 |
| 运维与调优 | docs/operations.md | 如何执行批量链接检测、生成断链报告、进行数据备份与迁移 |

## 资源列表

- http://m.wap.gqskj.cn/snews/23340.htm
- http://m.wap.gqskj.cn/snews/564698.htm
- http://m.wap.gqskj.cn/snews/79271.htm
- http://m.wap.gqskj.cn/snews/3876803.htm
- http://m.wap.gqskj.cn/snews/71454.htm
- http://m.wap.gqskj.cn/snews/8625302.htm
- http://m.wap.gqskj.cn/snews/300194.htm
- http://m.wap.gqskj.cn/snews/8356201.htm
- http://m.wap.gqskj.cn/snews/66232.htm
- http://m.wap.gqskj.cn/snews/6948048.htm
- http://m.wap.gqskj.cn/snews/3666502.htm
- http://m.wap.gqskj.cn/snews/0893278.htm
- http://m.wap.gqskj.cn/snews/5598519.htm
- http://m.wap.gqskj.cn/snews/293215.htm
- http://m.wap.gqskj.cn/snews/401870.htm
- http://m.wap.gqskj.cn/snews/1441.htm
- http://m.wap.gqskj.cn/snews/7195.htm
- http://m.wap.gqskj.cn/snews/6068065.htm
- http://m.wap.gqskj.cn/snews/35032.htm
- http://m.wap.gqskj.cn/snews/126123.htm
- http://m.wap.gqskj.cn/snews/6236045.htm
- http://m.wap.gqskj.cn/snews/273566.htm
- http://m.wap.gqskj.cn/snews/040370.htm
- http://m.wap.gqskj.cn/snews/12808.htm
- http://m.wap.gqskj.cn/snews/6200373.htm
- http://m.wap.gqskj.cn/snews/39062.htm
- http://m.wap.gqskj.cn/snews/5027.htm
- http://m.wap.gqskj.cn/snews/4093.htm
- http://m.wap.gqskj.cn/snews/9673.htm
- http://m.wap.gqskj.cn/snews/8961.htm
- http://m.wap.gqskj.cn/snews/2247.htm
- http://m.wap.gqskj.cn/snews/2683379.htm
- http://m.wap.gqskj.cn/snews/0756.htm
- http://m.wap.gqskj.cn/snews/16750.htm
- http://m.wap.gqskj.cn/snews/0238.htm
- http://m.wap.gqskj.cn/snews/454915.htm
- http://m.wap.gqskj.cn/snews/06957.htm
- http://m.wap.gqskj.cn/snews/45144.htm
- http://m.wap.gqskj.cn/snews/8497088.htm
- http://m.wap.gqskj.cn/snews/3372308.htm
- http://m.wap.gqskj.cn/snews/3181174.htm
- http://m.wap.gqskj.cn/snews/3542619.htm
- http://m.wap.gqskj.cn/snews/936204.htm
- http://m.wap.gqskj.cn/snews/4780975.htm
- http://m.wap.gqskj.cn/snews/8918.htm
- http://m.wap.gqskj.cn/snews/7325364.htm
- http://m.wap.gqskj.cn/snews/682843.htm
- http://m.wap.gqskj.cn/snews/7608.htm
- http://m.wap.gqskj.cn/snews/3222347.htm
- http://m.wap.gqskj.cn/snews/95988.htm
- http://m.wap.gqskj.cn/snews/190912.htm
- http://m.wap.gqskj.cn/snews/05983.htm
- http://m.wap.gqskj.cn/snews/494508.htm
- http://m.wap.gqskj.cn/snews/58511.htm
- http://m.wap.gqskj.cn/snews/9398528.htm
- http://m.wap.gqskj.cn/snews/2482309.htm
- http://m.wap.gqskj.cn/snews/2598279.htm
- http://m.wap.gqskj.cn/snews/01332.htm
- http://m.wap.gqskj.cn/snews/748664.htm
- http://m.wap.gqskj.cn/snews/15220.htm
- http://m.wap.gqskj.cn/snews/1341.htm
- http://m.wap.gqskj.cn/snews/8005.htm
- http://m.wap.gqskj.cn/snews/1523049.htm
- http://m.wap.gqskj.cn/snews/801265.htm
- http://m.wap.gqskj.cn/snews/1804.htm
- http://m.wap.gqskj.cn/snews/6836.htm
- http://m.wap.gqskj.cn/snews/513808.htm
- http://m.wap.gqskj.cn/snews/3473207.htm
- http://m.wap.gqskj.cn/snews/70995.htm
- http://m.wap.gqskj.cn/snews/5512.htm
- http://m.wap.gqskj.cn/snews/39517.htm
- http://m.wap.gqskj.cn/snews/5753.htm
- http://m.wap.gqskj.cn/snews/7413.htm
- http://m.wap.gqskj.cn/snews/02221.htm
- http://m.wap.gqskj.cn/snews/9723686.htm
- http://m.wap.gqskj.cn/snews/2322.htm
- http://m.wap.gqskj.cn/snews/95513.htm
- http://m.wap.gqskj.cn/snews/5192307.htm
- http://m.wap.gqskj.cn/snews/579173.htm
- http://m.wap.gqskj.cn/snews/543075.htm
- http://m.wap.gqskj.cn/snews/645650.htm
- http://m.wap.gqskj.cn/snews/19696.htm
- http://m.wap.gqskj.cn/snews/27472.htm
- http://m.wap.gqskj.cn/snews/13609.htm
- http://m.wap.gqskj.cn/snews/3005757.htm
- http://m.wap.gqskj.cn/snews/9098.htm
- http://m.wap.gqskj.cn/snews/4818934.htm
- http://m.wap.gqskj.cn/snews/2405653.htm
- http://m.wap.gqskj.cn/snews/6130761.htm
- http://m.wap.gqskj.cn/snews/0339457.htm
- http://m.wap.gqskj.cn/snews/01690.htm
- http://m.wap.gqskj.cn/snews/668946.htm
- http://m.wap.gqskj.cn/snews/5620928.htm
- http://m.wap.gqskj.cn/snews/8427231.htm
- http://m.wap.gqskj.cn/snews/895338.htm
- http://m.wap.gqskj.cn/snews/15140.htm
- http://m.wap.gqskj.cn/snews/1360.htm
- http://m.wap.gqskj.cn/snews/81971.htm
- http://m.wap.gqskj.cn/snews/9954.htm
- http://m.wap.gqskj.cn/snews/2355238.htm
- http://m.wap.gqskj.cn/snews/40285.htm
- http://m.wap.gqskj.cn/snews/738716.htm
- http://m.wap.gqskj.cn/snews/317485.htm
- http://m.wap.gqskj.cn/snews/92177.htm
- http://m.wap.gqskj.cn/snews/50283.htm
- http://m.wap.gqskj.cn/snews/29692.htm
- http://m.wap.gqskj.cn/snews/5462824.htm
- http://m.wap.gqskj.cn/snews/3714806.htm
- http://m.wap.gqskj.cn/snews/7501.htm
- http://m.wap.gqskj.cn/snews/623772.htm
- http://m.wap.gqskj.cn/snews/40041.htm
- http://m.wap.gqskj.cn/snews/61583.htm
- http://m.wap.gqskj.cn/snews/3265.htm
- http://m.wap.gqskj.cn/snews/1555.htm
- http://m.wap.gqskj.cn/snews/35710.htm
- http://m.wap.gqskj.cn/snews/2965845.htm
- http://m.wap.gqskj.cn/snews/43138.htm
- http://m.wap.gqskj.cn/snews/94465.htm
- http://m.wap.gqskj.cn/snews/89629.htm
- http://m.wap.gqskj.cn/snews/8149.htm
- http://m.wap.gqskj.cn/snews/495223.htm
- http://m.wap.gqskj.cn/snews/9584516.htm
- http://m.wap.gqskj.cn/snews/5068948.htm
- http://m.wap.gqskj.cn/snews/55719.htm
- http://m.wap.gqskj.cn/snews/6156348.htm
- http://m.wap.gqskj.cn/snews/3911.htm
- http://m.wap.gqskj.cn/snews/44682.htm
- http://m.wap.gqskj.cn/snews/7645.htm
- http://m.wap.gqskj.cn/snews/7212.htm
- http://m.wap.gqskj.cn/snews/416997.htm
- http://m.wap.gqskj.cn/snews/7162.htm
- http://m.wap.gqskj.cn/snews/52090.htm
- http://m.wap.gqskj.cn/snews/866158.htm
- http://m.wap.gqskj.cn/snews/1526459.htm
- http://m.wap.gqskj.cn/snews/8237414.htm
- http://m.wap.gqskj.cn/snews/3174538.htm
- http://m.wap.gqskj.cn/snews/7507329.htm
- http://m.wap.gqskj.cn/snews/9710162.htm
- http://m.wap.gqskj.cn/snews/183540.htm
- http://m.wap.gqskj.cn/snews/2836.htm
- http://m.wap.gqskj.cn/snews/22340.htm
- http://m.wap.gqskj.cn/snews/91261.htm
- http://m.wap.gqskj.cn/snews/67644.htm
- http://m.wap.gqskj.cn/snews/047648.htm
- http://m.wap.gqskj.cn/snews/947961.htm
- http://m.wap.gqskj.cn/snews/884903.htm
- http://m.wap.gqskj.cn/snews/33600.htm
- http://m.wap.gqskj.cn/snews/9757254.htm
- http://m.wap.gqskj.cn/snews/9552297.htm
- http://m.wap.gqskj.cn/snews/078168.htm
- http://m.wap.gqskj.cn/snews/1265.htm
- http://m.wap.gqskj.cn/snews/88659.htm
- http://m.wap.gqskj.cn/snews/664300.htm
- http://m.wap.gqskj.cn/snews/38109.htm
- http://m.wap.gqskj.cn/snews/8707936.htm
- http://m.wap.gqskj.cn/snews/5856596.htm
- http://m.wap.gqskj.cn/snews/2945514.htm
- http://m.wap.gqskj.cn/snews/4822879.htm
- http://m.wap.gqskj.cn/snews/516548.htm
- http://m.wap.gqskj.cn/snews/3673.htm
- http://m.wap.gqskj.cn/snews/859315.htm
- http://m.wap.gqskj.cn/snews/392178.htm
- http://m.wap.gqskj.cn/snews/37221.htm
- http://m.wap.gqskj.cn/snews/3404515.htm
- http://m.wap.gqskj.cn/snews/5631.htm
- http://m.wap.gqskj.cn/snews/6649.htm
- http://m.wap.gqskj.cn/snews/7531551.htm
- http://m.wap.gqskj.cn/snews/93858.htm
- http://m.wap.gqskj.cn/snews/7191764.htm
- http://m.wap.gqskj.cn/snews/931533.htm
- http://m.wap.gqskj.cn/snews/05484.htm
- http://m.wap.gqskj.cn/snews/8010799.htm
- http://m.wap.gqskj.cn/snews/79615.htm
- http://m.wap.gqskj.cn/snews/71849.htm
- http://m.wap.gqskj.cn/snews/44495.htm
- http://m.wap.gqskj.cn/snews/703939.htm
- http://m.wap.gqskj.cn/snews/615922.htm
- http://m.wap.gqskj.cn/snews/20889.htm
- http://m.wap.gqskj.cn/snews/89469.htm
- http://m.wap.gqskj.cn/snews/546270.htm
- http://m.wap.gqskj.cn/snews/7043.htm
- http://m.wap.gqskj.cn/snews/50254.htm
- http://m.wap.gqskj.cn/snews/09287.htm
- http://m.wap.gqskj.cn/snews/8000.htm
- http://m.wap.gqskj.cn/snews/0753658.htm
- http://m.wap.gqskj.cn/snews/53760.htm
- http://m.wap.gqskj.cn/snews/876518.htm
- http://m.wap.gqskj.cn/snews/8513.htm
- http://m.wap.gqskj.cn/snews/67051.htm
- http://m.wap.gqskj.cn/snews/6982295.htm
- http://m.wap.gqskj.cn/snews/217232.htm
- http://m.wap.gqskj.cn/snews/278698.htm
- http://m.wap.gqskj.cn/snews/458116.htm
- http://m.wap.gqskj.cn/snews/89018.htm
- http://m.wap.gqskj.cn/snews/5053.htm
- http://m.wap.gqskj.cn/snews/027012.htm
- http://m.wap.gqskj.cn/snews/26276.htm
- http://m.wap.gqskj.cn/snews/2694.htm
- http://m.wap.gqskj.cn/snews/5380.htm
- http://m.wap.gqskj.cn/snews/2679815.htm
- http://m.wap.gqskj.cn/snews/0969.htm
- http://m.wap.gqskj.cn/snews/4677313.htm
- http://m.wap.gqskj.cn/snews/94298.htm
- http://m.wap.gqskj.cn/snews/3109.htm
- http://m.wap.gqskj.cn/snews/394879.htm
- http://m.wap.gqskj.cn/snews/253869.htm
- http://m.wap.gqskj.cn/snews/962687.htm
- http://m.wap.gqskj.cn/snews/1299.htm
- http://m.wap.gqskj.cn/snews/65832.htm
- http://m.wap.gqskj.cn/snews/2426.htm
- http://m.wap.gqskj.cn/snews/93777.htm
- http://m.wap.gqskj.cn/snews/5707954.htm
- http://m.wap.gqskj.cn/snews/519587.htm
- http://m.wap.gqskj.cn/snews/246411.htm
- http://m.wap.gqskj.cn/snews/374172.htm
- http://m.wap.gqskj.cn/snews/982985.htm
- http://m.wap.gqskj.cn/snews/3439164.htm
- http://m.wap.gqskj.cn/snews/984163.htm
- http://m.wap.gqskj.cn/snews/56027.htm
- http://m.wap.gqskj.cn/snews/74745.htm
- http://m.wap.gqskj.cn/snews/20560.htm
- http://m.wap.gqskj.cn/snews/89657.htm
- http://m.wap.gqskj.cn/snews/420403.htm
- http://m.wap.gqskj.cn/snews/38307.htm
- http://m.wap.gqskj.cn/snews/0197.htm
- http://m.wap.gqskj.cn/snews/1428.htm
- http://m.wap.gqskj.cn/snews/14844.htm
- http://m.wap.gqskj.cn/snews/1189080.htm
- http://m.wap.gqskj.cn/snews/326417.htm
- http://m.wap.gqskj.cn/snews/414070.htm
- http://m.wap.gqskj.cn/snews/34189.htm
- http://m.wap.gqskj.cn/snews/2786.htm
- http://m.wap.gqskj.cn/snews/209082.htm
- http://m.wap.gqskj.cn/snews/5498.htm
- http://m.wap.gqskj.cn/snews/663899.htm
- http://m.wap.gqskj.cn/snews/522795.htm
- http://m.wap.gqskj.cn/snews/3215243.htm
- http://m.wap.gqskj.cn/snews/097358.htm
- http://m.wap.gqskj.cn/snews/9517.htm
- http://m.wap.gqskj.cn/snews/5654739.htm
- http://m.wap.gqskj.cn/snews/078766.htm
- http://m.wap.gqskj.cn/snews/9777772.htm
- http://m.wap.gqskj.cn/snews/8565.htm
- http://m.wap.gqskj.cn/snews/6638083.htm
- http://m.wap.gqskj.cn/snews/105576.htm
- http://m.wap.gqskj.cn/snews/851143.htm
- http://m.wap.gqskj.cn/snews/434390.htm
- http://m.wap.gqskj.cn/snews/33717.htm
- http://m.wap.gqskj.cn/snews/9700.htm
- http://m.wap.gqskj.cn/snews/322138.htm

## 项目结构

```
linkvault/
├── cmd/                                命令行入口与子命令定义
│   ├── __init__.py
│   ├── cli.py                          click 主入口，注册所有子命令
│   ├── import_cmd.py                   import 子命令，负责批量导入链接
│   ├── serve_cmd.py                    serve 子命令，启动 HTTP API 服务
│   └── check_cmd.py                    check 子命令，执行链接状态探测
├── core/                              核心业务逻辑模块
│   ├── __init__.py
│   ├── indexer.py                      链接索引引擎，实现增删改查与去重
│   ├── classifier.py                  分类器模块，处理标签生成与分类规则
│   ├── checker.py                     链接状态检测器，封装 HTTP 探测逻辑
│   └── exporter.py                    数据导出器，支持 JSON / CSV / TXT 格式
├── storage/                           数据持久化层
│   ├── __init__.py
│   ├── database.py                    SQLite 数据库连接与基础 CRUD 操作
│   ├── models.py                      ORM 模型定义，包含 Link、Tag、Category 等表
│   └── migrations/                    数据库迁移脚本目录
│       ├── 001_initial_schema.sql     初始表结构定义
│       └── 002_add_checked_at.sql     添加链接检测时间字段的增量迁移
├── api/                               HTTP API 路由与中间件
│   ├── __init__.py
│   ├── routes.py                      Flask / FastAPI 风格路由注册
│   ├── handlers.py                    各端点请求处理函数
│   └── schemas.py                     请求与响应的 Pydantic 数据模型
├── docs/                              项目文档目录
│   ├── quickstart.md                  快速入门指南
│   ├── taxonomy.md                    分类体系与标签策略说明
│   ├── api_reference.md               API 接口详细参考
│   └── operations.md                  运维手册，含部署、备份、监控指南
├── tests/                             单元测试与集成测试
│   ├── test_indexer.py                索引引擎单元测试
│   ├── test_classifier.py             分类器逻辑测试
│   ├── test_checker.py                链接检测模块测试
│   └── fixtures/                      测试数据夹具，包含样例链接列表
├── scripts/                           运维辅助脚本
│   ├── batch_import.sh                批量导入 shell 封装脚本
│   └── backup_db.sh                   数据库定时备份脚本
├── .env.example                       环境变量配置模板
├── requirements.txt                   Python 依赖清单
├── setup.py                           项目打包与分发配置
└── README.md                          项目总览文档（本文件）
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库到个人账户，然后 clone 到本地开发环境，确保使用 Python 3.9 及以上版本，并创建独立的虚拟环境用于隔离依赖。

2. 安装开发依赖包，包括 pytest、black、flake8 等代码质量工具，运行 `pip install -r requirements-dev.txt` 完成安装，并执行 `pre-commit install` 启用提交前自动检查。

3. 在 `core/` 或 `storage/` 目录下新增或修改代码时，需同步编写对应的单元测试用例，放置于 `tests/` 目录下，确保所有测试通过后再提交，运行 `pytest --cov=core --cov=storage` 检查覆盖率。

4. 提交代码前执行 `black .` 和 `flake8 .` 进行代码格式统一和静态检查，提交信息需遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:` 等前缀描述变更内容。

5. 发起 Pull Request 到主仓库的 develop 分支，在 PR 描述中说明变更目的、影响范围和测试结果，等待维护者评审，如有反馈意见及时补充修改并推送更新。

## 常见问题

**Q：导入包含大量 URL 的文件时，系统提示内存不足或处理速度极慢，应如何优化？**

A：对于超过 5000 条 URL 的批量导入，建议使用 `--chunk-size` 参数将文件分块处理，每批处理 1000 条并提交事务。同时可在 `.env` 中调整 `SQLITE_CACHE_SIZE` 和 `SQLITE_MMAP_SIZE` 参数提升 SQLite 写入性能。若仍无法满足需求，可考虑切换至 PostgreSQL 作为后端存储引擎。

**Q：链接状态检测模块是否支持代理环境和自定义超时时间？**

A：支持。在 `.env` 文件中配置 `HTTP_PROXY` 和 `HTTPS_PROXY` 环境变量即可启用代理。检测超时时间通过 `CHECK_TIMEOUT` 参数设置，单位为秒，默认值为 10 秒。对于响应较慢的服务端，可适当增加该值，但建议不超过 30 秒以免阻塞检测队列。

**Q：如何将现有浏览器书签或 Pocket 导出的数据迁移到 LinkVault 中？**

A：LinkVault 提供了转换适配器，位于 `scripts/adapters/` 目录下。对于 Chrome 书签，先通过浏览器导出为 HTML 文件，然后运行 `python scripts/adapters/chrome_bookmark.py --input bookmarks.html --output links.txt` 转换为标准导入格式。对于 Pocket 导出的 CSV 文件，使用 `pocket_csv.py` 脚本进行转换。转换后即可使用 `import` 子命令批量导入。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:58
