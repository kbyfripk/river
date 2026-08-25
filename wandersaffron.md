# fcful-bnews-archive

fcful-bnews-archive 是一个面向技术研究人员、数据挖掘工程师和信息分析从业者的结构化新闻链接归档与检索工具。该项目专注于采集、索引和提供对 fcful.cn 域名下 /bnews/ 路径中历史新闻资源的稳定访问，解决因源站内容滚动更新或链接失效导致的历史信息追溯困难问题。项目定位为只读型新闻元数据缓存层，不对原始内容进行任何修改或二次分发，仅提供链接级别的持久化引用与分类导航，帮助用户在批量数据分析、趋势回溯或事件追踪场景中快速定位特定时间段的新闻条目。

## 功能概览

批量链接归档：支持将指定批次内的所有新闻链接统一收录至本地索引数据库，保留原始 URL 路径结构及访问协议，确保链接可被后续自动化脚本批量调用。

时间戳映射：根据链接 URL 中的数字标识自动解析并映射对应的发布年份与月份，为每条记录生成可排序的时间维度元数据。

状态码检测：内置 HTTP 状态码检测模块，可定期对已归档链接进行可用性验证，自动标记返回 4xx 或 5xx 状态码的失效链接，便于用户及时剔除无效数据。

分类标签生成：基于链接 ID 数值区间与路径深度规则，自动为每条新闻链接生成初步的分类标签（如技术、财经、社会、国际等），辅助用户进行粗粒度筛选。

结构化导出：支持将归档数据导出为 JSON Lines、CSV 或纯文本列表格式，方便下游数据管道（如 ETL 流程、统计分析脚本或可视化面板）直接消费。

查询过滤接口：提供轻量级命令行查询接口，支持按日期范围、状态码、分类标签或原始 ID 前缀进行过滤检索，快速定位目标链接子集。

增量更新机制：支持以追加模式导入新增链接，避免全量重建，同时自动去重，确保同一 URL 不会重复入库。

## 应用场景

历史新闻趋势回溯分析：研究机构或高校学者可通过该归档项目快速获取过去数年内特定时间段（如某季度或某事件前后）的新闻链接集合，配合第三方内容抽取工具进行关键词频次与情感倾向的纵向对比研究。

数据管道测试与验证：数据工程师在构建新闻聚合或推荐系统原型时，可将本归档作为稳定测试数据源，无需依赖实时爬虫或第三方 API，避免因源站反爬策略变更导致开发中断。

信息丢失应急恢复：当原始新闻页面因源站改版、数据库迁移或意外删除而无法直接访问时，已归档的链接列表可作为线索记录，帮助用户通过互联网档案馆（如 Wayback Machine）或本地缓存进行补救性查阅。

内容审核样本构建：内容安全团队可基于本项目的批量导出功能，从归档链接中随机抽样构建审核样本集，用于训练分类模型或评估现有过滤规则的覆盖率与误判率。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 与 Python 3.8 及以上版本。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/fcful-bnews-archive.git
cd fcful-bnews-archive

# 安装项目依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate     # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行初始导入（将资源列表中的链接写入本地数据库）
python archive.py --import --source list --input ./data/seed_urls.txt
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 核心运行环境，用于执行归档脚本与依赖管理 |
| Git | 2.25 或更高 | 用于克隆仓库及后续版本更新 |
| SQLite3 | 系统内置 | 轻量级本地数据库引擎，用于存储链接元数据及状态记录 |
| requests | 2.28.0 或更高 | 发送 HTTP 请求，用于检测链接状态码及获取响应头信息 |
| click | 8.1.0 或更高 | 命令行交互框架，提供子命令解析与参数校验功能 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何进行链接导入、状态检测、过滤查询与数据导出等日常操作 |
| 开发者指南 | docs/developer-guide.md | 数据库表结构设计、新增数据源适配器的方法及单元测试编写规范 |
| 运维参考 | docs/operations.md | 如何设置定时任务自动刷新链接状态、如何备份 SQLite 数据库文件 |
| 设计说明 | docs/design.md | 项目模块划分、链接 ID 解析算法原理及分类标签生成策略的详细解释 |

## 资源列表

- http://m.blog.fcful.cn/bnews/81011.htm
- http://m.blog.fcful.cn/bnews/3783777.htm
- http://m.blog.fcful.cn/bnews/996890.htm
- http://m.blog.fcful.cn/bnews/0121.htm
- http://m.blog.fcful.cn/bnews/3441.htm
- http://m.blog.fcful.cn/bnews/390115.htm
- http://m.blog.fcful.cn/bnews/995704.htm
- http://m.blog.fcful.cn/bnews/8012.htm
- http://m.blog.fcful.cn/bnews/7068.htm
- http://m.blog.fcful.cn/bnews/6824970.htm
- http://m.blog.fcful.cn/bnews/0513929.htm
- http://m.blog.fcful.cn/bnews/8367630.htm
- http://m.blog.fcful.cn/bnews/9136.htm
- http://m.blog.fcful.cn/bnews/6618005.htm
- http://m.blog.fcful.cn/bnews/7351.htm
- http://m.blog.fcful.cn/bnews/5391792.htm
- http://m.blog.fcful.cn/bnews/4671934.htm
- http://m.blog.fcful.cn/bnews/8819.htm
- http://m.blog.fcful.cn/bnews/9367.htm
- http://m.blog.fcful.cn/bnews/70662.htm
- http://m.blog.fcful.cn/bnews/4521.htm
- http://m.blog.fcful.cn/bnews/3012.htm
- http://m.blog.fcful.cn/bnews/909903.htm
- http://m.blog.fcful.cn/bnews/65148.htm
- http://m.blog.fcful.cn/bnews/6543400.htm
- http://m.blog.fcful.cn/bnews/9286403.htm
- http://m.blog.fcful.cn/bnews/600885.htm
- http://m.blog.fcful.cn/bnews/24175.htm
- http://m.blog.fcful.cn/bnews/52458.htm
- http://m.blog.fcful.cn/bnews/8706.htm
- http://m.blog.fcful.cn/bnews/11018.htm
- http://m.blog.fcful.cn/bnews/199900.htm
- http://m.blog.fcful.cn/bnews/2414098.htm
- http://m.blog.fcful.cn/bnews/06671.htm
- http://m.blog.fcful.cn/bnews/06702.htm
- http://m.blog.fcful.cn/bnews/082050.htm
- http://m.blog.fcful.cn/bnews/32047.htm
- http://m.blog.fcful.cn/bnews/644772.htm
- http://m.blog.fcful.cn/bnews/2810.htm
- http://m.blog.fcful.cn/bnews/1638172.htm
- http://m.blog.fcful.cn/bnews/658800.htm
- http://m.blog.fcful.cn/bnews/050654.htm
- http://m.blog.fcful.cn/bnews/4748.htm
- http://m.blog.fcful.cn/bnews/165990.htm
- http://m.blog.fcful.cn/bnews/772262.htm
- http://m.blog.fcful.cn/bnews/29825.htm
- http://m.blog.fcful.cn/bnews/05201.htm
- http://m.blog.fcful.cn/bnews/77913.htm
- http://m.blog.fcful.cn/bnews/4667195.htm
- http://m.blog.fcful.cn/bnews/9353.htm
- http://m.blog.fcful.cn/bnews/29937.htm
- http://m.blog.fcful.cn/bnews/4944651.htm
- http://m.blog.fcful.cn/bnews/0825414.htm
- http://m.blog.fcful.cn/bnews/5196.htm
- http://m.blog.fcful.cn/bnews/6489485.htm
- http://m.blog.fcful.cn/bnews/67164.htm
- http://m.blog.fcful.cn/bnews/389877.htm
- http://m.blog.fcful.cn/bnews/816651.htm
- http://m.blog.fcful.cn/bnews/0613564.htm
- http://m.blog.fcful.cn/bnews/78784.htm
- http://m.blog.fcful.cn/bnews/24700.htm
- http://m.blog.fcful.cn/bnews/68018.htm
- http://m.blog.fcful.cn/bnews/3915504.htm
- http://m.blog.fcful.cn/bnews/5162515.htm
- http://m.blog.fcful.cn/bnews/60231.htm
- http://m.blog.fcful.cn/bnews/0776840.htm
- http://m.blog.fcful.cn/bnews/5955841.htm
- http://m.blog.fcful.cn/bnews/069453.htm
- http://m.blog.fcful.cn/bnews/2081206.htm
- http://m.blog.fcful.cn/bnews/1719.htm
- http://m.blog.fcful.cn/bnews/7191901.htm
- http://m.blog.fcful.cn/bnews/1424621.htm
- http://m.blog.fcful.cn/bnews/24691.htm
- http://m.blog.fcful.cn/bnews/75572.htm
- http://m.blog.fcful.cn/bnews/002197.htm
- http://m.blog.fcful.cn/bnews/35385.htm
- http://m.blog.fcful.cn/bnews/073576.htm
- http://m.blog.fcful.cn/bnews/6481683.htm
- http://m.blog.fcful.cn/bnews/11242.htm
- http://m.blog.fcful.cn/bnews/8063.htm
- http://m.blog.fcful.cn/bnews/15155.htm
- http://m.blog.fcful.cn/bnews/3924402.htm
- http://m.blog.fcful.cn/bnews/2224866.htm
- http://m.blog.fcful.cn/bnews/395557.htm
- http://m.blog.fcful.cn/bnews/126123.htm
- http://m.blog.fcful.cn/bnews/586039.htm
- http://m.blog.fcful.cn/bnews/878327.htm
- http://m.blog.fcful.cn/bnews/73370.htm
- http://m.blog.fcful.cn/bnews/9093.htm
- http://m.blog.fcful.cn/bnews/9676.htm
- http://m.blog.fcful.cn/bnews/9917.htm
- http://m.blog.fcful.cn/bnews/003724.htm
- http://m.blog.fcful.cn/bnews/06705.htm
- http://m.blog.fcful.cn/bnews/350423.htm
- http://m.blog.fcful.cn/bnews/79744.htm
- http://m.blog.fcful.cn/bnews/1962.htm
- http://m.blog.fcful.cn/bnews/2991193.htm
- http://m.blog.fcful.cn/bnews/38457.htm
- http://m.blog.fcful.cn/bnews/45251.htm
- http://m.blog.fcful.cn/bnews/9486454.htm
- http://m.blog.fcful.cn/bnews/58658.htm
- http://m.blog.fcful.cn/bnews/527129.htm
- http://m.blog.fcful.cn/bnews/148262.htm
- http://m.blog.fcful.cn/bnews/2524.htm
- http://m.blog.fcful.cn/bnews/6808161.htm
- http://m.blog.fcful.cn/bnews/70919.htm
- http://m.blog.fcful.cn/bnews/7052078.htm
- http://m.blog.fcful.cn/bnews/3532.htm
- http://m.blog.fcful.cn/bnews/9645949.htm
- http://m.blog.fcful.cn/bnews/2482.htm
- http://m.blog.fcful.cn/bnews/064298.htm
- http://m.blog.fcful.cn/bnews/0054990.htm
- http://m.blog.fcful.cn/bnews/52699.htm
- http://m.blog.fcful.cn/bnews/26696.htm
- http://m.blog.fcful.cn/bnews/3189428.htm
- http://m.blog.fcful.cn/bnews/6938.htm
- http://m.blog.fcful.cn/bnews/5046.htm
- http://m.blog.fcful.cn/bnews/27917.htm
- http://m.blog.fcful.cn/bnews/000299.htm
- http://m.blog.fcful.cn/bnews/43552.htm
- http://m.blog.fcful.cn/bnews/4176095.htm
- http://m.blog.fcful.cn/bnews/48841.htm
- http://m.blog.fcful.cn/bnews/479296.htm
- http://m.blog.fcful.cn/bnews/548948.htm
- http://m.blog.fcful.cn/bnews/6593.htm
- http://m.blog.fcful.cn/bnews/16328.htm
- http://m.blog.fcful.cn/bnews/4135831.htm
- http://m.blog.fcful.cn/bnews/8893.htm
- http://m.blog.fcful.cn/bnews/3511.htm
- http://m.blog.fcful.cn/bnews/3876.htm
- http://m.blog.fcful.cn/bnews/8310.htm
- http://m.blog.fcful.cn/bnews/0807275.htm
- http://m.blog.fcful.cn/bnews/1704.htm
- http://m.blog.fcful.cn/bnews/354164.htm
- http://m.blog.fcful.cn/bnews/992365.htm
- http://m.blog.fcful.cn/bnews/3677318.htm
- http://m.blog.fcful.cn/bnews/7873207.htm
- http://m.blog.fcful.cn/bnews/02849.htm
- http://m.blog.fcful.cn/bnews/5321.htm
- http://m.blog.fcful.cn/bnews/9420.htm
- http://m.blog.fcful.cn/bnews/199341.htm
- http://m.blog.fcful.cn/bnews/4224162.htm
- http://m.blog.fcful.cn/bnews/1444.htm
- http://m.blog.fcful.cn/bnews/183775.htm
- http://m.blog.fcful.cn/bnews/5851994.htm
- http://m.blog.fcful.cn/bnews/941114.htm
- http://m.blog.fcful.cn/bnews/03208.htm
- http://m.blog.fcful.cn/bnews/27599.htm
- http://m.blog.fcful.cn/bnews/2892054.htm
- http://m.blog.fcful.cn/bnews/1244025.htm
- http://m.blog.fcful.cn/bnews/49961.htm
- http://m.blog.fcful.cn/bnews/12989.htm
- http://m.blog.fcful.cn/bnews/991493.htm
- http://m.blog.fcful.cn/bnews/1742.htm
- http://m.blog.fcful.cn/bnews/350335.htm
- http://m.blog.fcful.cn/bnews/28891.htm
- http://m.blog.fcful.cn/bnews/6208.htm
- http://m.blog.fcful.cn/bnews/900533.htm
- http://m.blog.fcful.cn/bnews/1030052.htm
- http://m.blog.fcful.cn/bnews/8656632.htm
- http://m.blog.fcful.cn/bnews/480051.htm
- http://m.blog.fcful.cn/bnews/7064.htm
- http://m.blog.fcful.cn/bnews/552616.htm
- http://m.blog.fcful.cn/bnews/431710.htm
- http://m.blog.fcful.cn/bnews/6806148.htm
- http://m.blog.fcful.cn/bnews/6776.htm
- http://m.blog.fcful.cn/bnews/8055.htm
- http://m.blog.fcful.cn/bnews/7580008.htm
- http://m.blog.fcful.cn/bnews/31306.htm
- http://m.blog.fcful.cn/bnews/338450.htm
- http://m.blog.fcful.cn/bnews/747282.htm
- http://m.blog.fcful.cn/bnews/6245400.htm
- http://m.blog.fcful.cn/bnews/4187.htm
- http://m.blog.fcful.cn/bnews/9303976.htm
- http://m.blog.fcful.cn/bnews/13292.htm
- http://m.blog.fcful.cn/bnews/70135.htm
- http://m.blog.fcful.cn/bnews/180398.htm
- http://m.blog.fcful.cn/bnews/92884.htm
- http://m.blog.fcful.cn/bnews/3731.htm
- http://m.blog.fcful.cn/bnews/3605.htm
- http://m.blog.fcful.cn/bnews/926046.htm
- http://m.blog.fcful.cn/bnews/36991.htm
- http://m.blog.fcful.cn/bnews/7287.htm
- http://m.blog.fcful.cn/bnews/814910.htm
- http://m.blog.fcful.cn/bnews/9725360.htm
- http://m.blog.fcful.cn/bnews/4302845.htm
- http://m.blog.fcful.cn/bnews/8577.htm
- http://m.blog.fcful.cn/bnews/08266.htm
- http://m.blog.fcful.cn/bnews/6151.htm
- http://m.blog.fcful.cn/bnews/8909894.htm
- http://m.blog.fcful.cn/bnews/659339.htm
- http://m.blog.fcful.cn/bnews/7435.htm
- http://m.blog.fcful.cn/bnews/4881665.htm
- http://m.blog.fcful.cn/bnews/59640.htm
- http://m.blog.fcful.cn/bnews/3534321.htm
- http://m.blog.fcful.cn/bnews/7745057.htm
- http://m.blog.fcful.cn/bnews/81665.htm
- http://m.blog.fcful.cn/bnews/2131.htm
- http://m.blog.fcful.cn/bnews/273878.htm
- http://m.blog.fcful.cn/bnews/939586.htm
- http://m.blog.fcful.cn/bnews/61905.htm
- http://m.blog.fcful.cn/bnews/1863696.htm
- http://m.blog.fcful.cn/bnews/49193.htm
- http://m.blog.fcful.cn/bnews/653418.htm
- http://m.blog.fcful.cn/bnews/32853.htm
- http://m.blog.fcful.cn/bnews/644010.htm
- http://m.blog.fcful.cn/bnews/738921.htm
- http://m.blog.fcful.cn/bnews/78343.htm
- http://m.blog.fcful.cn/bnews/0708.htm
- http://m.blog.fcful.cn/bnews/705561.htm
- http://m.blog.fcful.cn/bnews/3590491.htm
- http://m.blog.fcful.cn/bnews/7752833.htm
- http://m.blog.fcful.cn/bnews/637264.htm
- http://m.blog.fcful.cn/bnews/59332.htm
- http://m.blog.fcful.cn/bnews/120086.htm
- http://m.blog.fcful.cn/bnews/3027.htm
- http://m.blog.fcful.cn/bnews/5218.htm
- http://m.blog.fcful.cn/bnews/188098.htm
- http://m.blog.fcful.cn/bnews/1644.htm
- http://m.blog.fcful.cn/bnews/5681.htm
- http://m.blog.fcful.cn/bnews/4816.htm
- http://m.blog.fcful.cn/bnews/0627.htm
- http://m.blog.fcful.cn/bnews/023561.htm
- http://m.blog.fcful.cn/bnews/8880.htm
- http://m.blog.fcful.cn/bnews/76664.htm
- http://m.blog.fcful.cn/bnews/991338.htm
- http://m.blog.fcful.cn/bnews/585262.htm
- http://m.blog.fcful.cn/bnews/8425.htm
- http://m.blog.fcful.cn/bnews/0711.htm
- http://m.blog.fcful.cn/bnews/637115.htm
- http://m.blog.fcful.cn/bnews/3919015.htm
- http://m.blog.fcful.cn/bnews/087939.htm
- http://m.blog.fcful.cn/bnews/45049.htm
- http://m.blog.fcful.cn/bnews/2661.htm
- http://m.blog.fcful.cn/bnews/097969.htm
- http://m.blog.fcful.cn/bnews/06888.htm
- http://m.blog.fcful.cn/bnews/83765.htm
- http://m.blog.fcful.cn/bnews/933548.htm
- http://m.blog.fcful.cn/bnews/685287.htm
- http://m.blog.fcful.cn/bnews/600293.htm
- http://m.blog.fcful.cn/bnews/4923.htm
- http://m.blog.fcful.cn/bnews/5714489.htm
- http://m.blog.fcful.cn/bnews/2670940.htm
- http://m.blog.fcful.cn/bnews/08704.htm
- http://m.blog.fcful.cn/bnews/90149.htm
- http://m.blog.fcful.cn/bnews/8364.htm
- http://m.blog.fcful.cn/bnews/65733.htm
- http://m.blog.fcful.cn/bnews/181831.htm
- http://m.blog.fcful.cn/bnews/3494.htm
- http://m.blog.fcful.cn/bnews/765584.htm

## 项目结构

```
fcful-bnews-archive/
├── archive.py                  # 主入口脚本，协调导入、检测、导出与查询子命令
├── requirements.txt            # Python 依赖清单，固定版本以保证环境一致性
├── config.yaml                 # 可配置参数文件，含数据库路径、请求超时与重试策略
├── data/
│   ├── seed_urls.txt           # 初始种子链接列表，每行一个 URL，供首次导入使用
│   └── archive.db              # SQLite 数据库文件，存储所有归档链接及其元数据
├── src/
│   ├── __init__.py             # 包标识文件
│   ├── fetcher.py              # HTTP 请求封装模块，含状态码检测与响应头解析
│   ├── parser.py               # URL 解析器，提取数字 ID 并映射时间戳与分类标签
│   ├── storage.py              # 数据库读写接口，实现插入、更新、去重与查询逻辑
│   └── exporter.py             # 数据导出模块，支持 JSON Lines / CSV / 纯文本格式
├── tests/
│   ├── test_fetcher.py         # fetcher 模块的单元测试，覆盖正常与异常请求场景
│   ├── test_parser.py          # parser 模块的测试用例，验证 ID 提取与分类规则
│   └── test_storage.py         # storage 模块的内存数据库测试，检查事务与约束
├── docs/
│   ├── user-guide.md           # 用户手册，包含安装配置与日常操作详细说明
│   ├── developer-guide.md      # 开发者指南，描述模块接口与扩展开发流程
│   ├── operations.md           # 运维参考，给出定时任务配置与备份恢复方案
│   └── design.md               # 设计说明，阐述架构决策与算法细节
└── scripts/
    ├── daily_refresh.sh        # 每日定时刷新脚本，调用 archive.py 更新状态码
    └── export_latest.sh        # 导出最新批次链接为 CSV 文件的辅助脚本
```

## 贡献指南

提交问题报告：在 GitHub Issues 页面新建工单，使用项目提供的 Bug 报告模板，详细描述复现步骤、预期行为与实际结果，并附上相关日志片段或截图。

实现功能增强：从 Issues 列表中挑选未被认领的功能请求或优化建议，在本地创建功能分支进行开发，完成后提交 Pull Request，并在描述中引用对应的 Issue 编号。

完善文档内容：对 docs/ 目录下的任何文档进行勘误、补充或翻译改进，提交单独的 Pull Request 并标注文档变更类型（勘误/补充/翻译）。

补充测试用例：针对现有模块中未被覆盖的边缘条件或异常路径，编写新的单元测试方法，确保新增代码的行覆盖率不低于 80%。

## 常见问题

问题：导入链接时提示 "URL already exists" 但实际数据库中并未找到该记录。

回答：此提示通常是由于链接 ID 被误判为重复。项目去重逻辑基于 URL 完整字符串进行精确匹配，请检查待导入文件中是否包含不可见字符（如多余的空格、换行符或 BOM 头）。建议使用 hexdump 或 od 命令检查文件编码，确保为纯 UTF-8 文本。若确认无重复仍出现该提示，可运行 archive.py --dedup-reset 强制重建唯一索引。

问题：状态码检测命令执行极慢或大量返回超时。

回答：部分历史链接对应的源站服务器可能已下线或存在严格的访问频率限制。项目默认超时时间为 10 秒，并采用 5 并发线程池。用户可通过修改 config.yaml 中的 timeout 和 max_workers 参数调整行为。对于持续超时的链接，系统会自动标记为 STATUS_UNREACHABLE 并跳过后续重试，避免阻塞整体流程。

问题：导出的 CSV 文件中日期列为空或格式异常。

回答：日期解析依赖于 URL 末尾的数字 ID 长度与预设的解析规则表。若某条链接的 ID 长度不在已知映射范围内（例如小于 4 位或大于 10 位），解析器会将其归为未知并留空日期列。用户可手动在数据库的 fallback_date 字段补充正确日期，或扩展 parser.py 中的 ID_PATTERN_MAP 字典以支持新的 ID 格式。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
