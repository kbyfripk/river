# SNews Indexer

SNews Indexer 是一个面向移动端资讯聚合与结构化存储的开源索引系统，专为从非标准 HTML 页面中批量抽取、清洗和归档新闻类内容而设计。该项目主要服务于数据采集工程师、内容运营人员以及个人知识库管理者，帮助其将零散分布的动态新闻页面转化为可检索、可分析的结构化数据集。

项目通过可配置的选择器引擎与去重策略，能够在不依赖站点 API 的情况下，对大量来源不固定的页面进行内容抓取和元数据提取。同时内置了轻量级任务队列和失败重试机制，确保在弱网环境或站点临时变动时仍能保持较高的采集完成率。SNews Indexer 并非一个通用爬虫框架，而是一个聚焦于单站点内容结构稳定但链接模式多变场景的专用工具。

## 功能概览

**批量链接导入与校验**：支持从文本文件、CSV 或直接粘贴的链接列表中批量导入待处理 URL，自动执行去重与格式校验，剔除非法或重复条目。

**可编程选择器配置**：提供基于 CSS 选择器与 XPath 的混合抽取规则定义，允许用户为不同页面模式编写独立的字段映射配置，无需修改核心代码。

**增量式内容存储**：采用增量更新策略，对已抓取页面依据内容哈希判断是否发生变更，仅当内容变化时才更新数据库记录，显著降低存储与索引开销。

**失败重试与指数退避**：内置指数退避重试机制，对超时、连接中断、返回非预期状态码的请求自动进行最多 3 次重试，并提供详细失败日志便于排查。

**结构化元数据输出**：每条记录输出标题、发布时间、正文摘要、原始 URL 及抓取时间戳，支持 JSON、CSV 和 SQLite 三种导出格式。

**任务进度持久化**：任务队列支持断点续跑，进程意外终止后重启可从上次中断点继续，避免重复抓取已完成的链接。

## 应用场景

**移动端新闻站点镜像归档**：对于依赖动态加载或分页参数复杂的移动新闻站点，SNews Indexer 可配置固定入口链接模板，周期性抓取最新文章列表并保存全文快照，用于离线阅读或长期存档。

**多源资讯聚合去重**：当运营团队需要从多个子频道或不同发布时间段的页面中收集素材时，可通过导入大量原始链接，由系统自动识别重复内容并保留最早版本，减少人工筛选工作量。

**历史数据批量补采**：在数据迁移或知识库初始化阶段，用户提供一批历史文章链接，系统自动按优先级队列逐条抓取，并将结果统一入库，支持断点续传以适应长时间运行任务。

**内容变更监控与通知**：结合增量存储特性，定期运行索引任务后可对比前后两次抓取结果的差异，生成新增、修改、删除记录报告，适用于内容更新频繁的监控场景。

## 快速开始

以下命令演示了从克隆仓库到运行一次基础索引任务的完整流程。

```bash
git clone https://github.com/your-org/snews-indexer.git
cd snews-indexer

pip install -r requirements.txt

cp config.example.yaml config.yaml
# 编辑 config.yaml 填写基础抓取参数

python cli.py import --input links.txt --queue task_queue.db
python cli.py run --workers 4 --db output.sqlite
```

其中 `links.txt` 为每行一个 URL 的文本文件，`cli.py run` 将启动工作进程依次处理队列中的链接。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与会话管理，支持重定向和超时配置 |
| lxml | 4.9.0 及以上 | 用于 XPath 和 CSS 选择器解析，提升 HTML 抽取性能 |
| pyyaml | 6.0 及以上 | 解析配置文件，支持环境变量占位符替换 |
| apsw | 3.40.0 及以上 | SQLite 驱动扩展，提供更细致的并发控制和备份接口 |
| tqdm | 4.64.0 及以上 | 显示进度条，便于监控长时间任务执行状态 |
| pytest | 7.2.0 及以上 | 仅开发测试时需要，用于运行单元测试与集成测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting_started.md | 如何安装、配置第一个抓取任务并成功运行一次索引流程 |
| 配置参考 | docs/configuration.md | 所有可用的配置项说明，包括选择器定义、重试策略与存储路径 |
| 选择器编写 | docs/selector_guide.md | 针对不同页面结构如何编写稳定的 CSS/XPath 抽取规则 |
| 任务管理 | docs/task_management.md | 如何创建、暂停、恢复和清理任务队列，以及查看任务状态 |

## 资源列表

- http://m.3g.fcful.cn/snews/58686.htm
- http://m.3g.fcful.cn/snews/50173.htm
- http://m.3g.fcful.cn/snews/855275.htm
- http://m.3g.fcful.cn/snews/51617.htm
- http://m.3g.fcful.cn/snews/051921.htm
- http://m.3g.fcful.cn/snews/7803953.htm
- http://m.3g.fcful.cn/snews/70761.htm
- http://m.3g.fcful.cn/snews/175630.htm
- http://m.3g.fcful.cn/snews/3304.htm
- http://m.3g.fcful.cn/snews/4961858.htm
- http://m.3g.fcful.cn/snews/2165741.htm
- http://m.3g.fcful.cn/snews/250561.htm
- http://m.3g.fcful.cn/snews/382946.htm
- http://m.3g.fcful.cn/snews/27660.htm
- http://m.3g.fcful.cn/snews/165679.htm
- http://m.3g.fcful.cn/snews/85695.htm
- http://m.3g.fcful.cn/snews/0000776.htm
- http://m.3g.fcful.cn/snews/077399.htm
- http://m.3g.fcful.cn/snews/99132.htm
- http://m.3g.fcful.cn/snews/5873324.htm
- http://m.3g.fcful.cn/snews/509157.htm
- http://m.3g.fcful.cn/snews/2875465.htm
- http://m.3g.fcful.cn/snews/49358.htm
- http://m.3g.fcful.cn/snews/139793.htm
- http://m.3g.fcful.cn/snews/59183.htm
- http://m.3g.fcful.cn/snews/89106.htm
- http://m.3g.fcful.cn/snews/4134.htm
- http://m.3g.fcful.cn/snews/1160.htm
- http://m.3g.fcful.cn/snews/5019944.htm
- http://m.3g.fcful.cn/snews/5317.htm
- http://m.3g.fcful.cn/snews/943889.htm
- http://m.3g.fcful.cn/snews/3319.htm
- http://m.3g.fcful.cn/snews/6064.htm
- http://m.3g.fcful.cn/snews/65525.htm
- http://m.3g.fcful.cn/snews/860015.htm
- http://m.3g.fcful.cn/snews/6799792.htm
- http://m.3g.fcful.cn/snews/2991.htm
- http://m.3g.fcful.cn/snews/72688.htm
- http://m.3g.fcful.cn/snews/67109.htm
- http://m.3g.fcful.cn/snews/32525.htm
- http://m.3g.fcful.cn/snews/480802.htm
- http://m.3g.fcful.cn/snews/2955766.htm
- http://m.3g.fcful.cn/snews/6331435.htm
- http://m.3g.fcful.cn/snews/40016.htm
- http://m.3g.fcful.cn/snews/6168725.htm
- http://m.3g.fcful.cn/snews/86021.htm
- http://m.3g.fcful.cn/snews/6062.htm
- http://m.3g.fcful.cn/snews/6216474.htm
- http://m.3g.fcful.cn/snews/098723.htm
- http://m.3g.fcful.cn/snews/4056.htm
- http://m.3g.fcful.cn/snews/9314475.htm
- http://m.3g.fcful.cn/snews/81420.htm
- http://m.3g.fcful.cn/snews/72788.htm
- http://m.3g.fcful.cn/snews/2223.htm
- http://m.3g.fcful.cn/snews/5412297.htm
- http://m.3g.fcful.cn/snews/5650.htm
- http://m.3g.fcful.cn/snews/7976831.htm
- http://m.3g.fcful.cn/snews/85984.htm
- http://m.3g.fcful.cn/snews/1013.htm
- http://m.3g.fcful.cn/snews/9945452.htm
- http://m.3g.fcful.cn/snews/549565.htm
- http://m.3g.fcful.cn/snews/4063.htm
- http://m.3g.fcful.cn/snews/0393686.htm
- http://m.3g.fcful.cn/snews/53985.htm
- http://m.3g.fcful.cn/snews/1579504.htm
- http://m.3g.fcful.cn/snews/7543118.htm
- http://m.3g.fcful.cn/snews/8091744.htm
- http://m.3g.fcful.cn/snews/07498.htm
- http://m.3g.fcful.cn/snews/3683801.htm
- http://m.3g.fcful.cn/snews/1974680.htm
- http://m.3g.fcful.cn/snews/864191.htm
- http://m.3g.fcful.cn/snews/26380.htm
- http://m.3g.fcful.cn/snews/9995718.htm
- http://m.3g.fcful.cn/snews/959442.htm
- http://m.3g.fcful.cn/snews/6613581.htm
- http://m.3g.fcful.cn/snews/2244839.htm
- http://m.3g.fcful.cn/snews/454134.htm
- http://m.3g.fcful.cn/snews/0918.htm
- http://m.3g.fcful.cn/snews/37113.htm
- http://m.3g.fcful.cn/snews/63216.htm
- http://m.3g.fcful.cn/snews/113228.htm
- http://m.3g.fcful.cn/snews/6425.htm
- http://m.3g.fcful.cn/snews/77331.htm
- http://m.3g.fcful.cn/snews/58961.htm
- http://m.3g.fcful.cn/snews/72528.htm
- http://m.3g.fcful.cn/snews/317597.htm
- http://m.3g.fcful.cn/snews/6773.htm
- http://m.3g.fcful.cn/snews/33471.htm
- http://m.3g.fcful.cn/snews/00490.htm
- http://m.3g.fcful.cn/snews/6236.htm
- http://m.3g.fcful.cn/snews/3985121.htm
- http://m.3g.fcful.cn/snews/871540.htm
- http://m.3g.fcful.cn/snews/667900.htm
- http://m.3g.fcful.cn/snews/1327.htm
- http://m.3g.fcful.cn/snews/0562036.htm
- http://m.3g.fcful.cn/snews/419352.htm
- http://m.3g.fcful.cn/snews/7396.htm
- http://m.3g.fcful.cn/snews/4132.htm
- http://m.3g.fcful.cn/snews/6072891.htm
- http://m.3g.fcful.cn/snews/2305853.htm
- http://m.3g.fcful.cn/snews/1679.htm
- http://m.3g.fcful.cn/snews/4713.htm
- http://m.3g.fcful.cn/snews/5411.htm
- http://m.3g.fcful.cn/snews/1606069.htm
- http://m.3g.fcful.cn/snews/91101.htm
- http://m.3g.fcful.cn/snews/699462.htm
- http://m.3g.fcful.cn/snews/12177.htm
- http://m.3g.fcful.cn/snews/153260.htm
- http://m.3g.fcful.cn/snews/4883923.htm
- http://m.3g.fcful.cn/snews/6103300.htm
- http://m.3g.fcful.cn/snews/54692.htm
- http://m.3g.fcful.cn/snews/0805936.htm
- http://m.3g.fcful.cn/snews/959405.htm
- http://m.3g.fcful.cn/snews/10676.htm
- http://m.3g.fcful.cn/snews/3093934.htm
- http://m.3g.fcful.cn/snews/938758.htm
- http://m.3g.fcful.cn/snews/580049.htm
- http://m.3g.fcful.cn/snews/8917986.htm
- http://m.3g.fcful.cn/snews/8633621.htm
- http://m.3g.fcful.cn/snews/525832.htm
- http://m.3g.fcful.cn/snews/41392.htm
- http://m.3g.fcful.cn/snews/76713.htm
- http://m.3g.fcful.cn/snews/51777.htm
- http://m.3g.fcful.cn/snews/8884311.htm
- http://m.3g.fcful.cn/snews/966588.htm
- http://m.3g.fcful.cn/snews/0015118.htm
- http://m.3g.fcful.cn/snews/1605.htm
- http://m.3g.fcful.cn/snews/4263668.htm
- http://m.3g.fcful.cn/snews/171176.htm
- http://m.3g.fcful.cn/snews/3462492.htm
- http://m.3g.fcful.cn/snews/2747.htm
- http://m.3g.fcful.cn/snews/44822.htm
- http://m.3g.fcful.cn/snews/5011.htm
- http://m.3g.fcful.cn/snews/9746032.htm
- http://m.3g.fcful.cn/snews/5191.htm
- http://m.3g.fcful.cn/snews/5665255.htm
- http://m.3g.fcful.cn/snews/92763.htm
- http://m.3g.fcful.cn/snews/2638710.htm
- http://m.3g.fcful.cn/snews/42534.htm
- http://m.3g.fcful.cn/snews/8649595.htm
- http://m.3g.fcful.cn/snews/1429026.htm
- http://m.3g.fcful.cn/snews/3460.htm
- http://m.3g.fcful.cn/snews/63177.htm
- http://m.3g.fcful.cn/snews/5597598.htm
- http://m.3g.fcful.cn/snews/075131.htm
- http://m.3g.fcful.cn/snews/93760.htm
- http://m.3g.fcful.cn/snews/8121399.htm
- http://m.3g.fcful.cn/snews/147812.htm
- http://m.3g.fcful.cn/snews/4340.htm
- http://m.3g.fcful.cn/snews/56343.htm
- http://m.3g.fcful.cn/snews/88442.htm
- http://m.3g.fcful.cn/snews/1629040.htm
- http://m.3g.fcful.cn/snews/041609.htm
- http://m.3g.fcful.cn/snews/85646.htm
- http://m.3g.fcful.cn/snews/87402.htm
- http://m.3g.fcful.cn/snews/720097.htm
- http://m.3g.fcful.cn/snews/1048135.htm
- http://m.3g.fcful.cn/snews/8222.htm
- http://m.3g.fcful.cn/snews/53658.htm
- http://m.3g.fcful.cn/snews/6539453.htm
- http://m.3g.fcful.cn/snews/039344.htm
- http://m.3g.fcful.cn/snews/90173.htm
- http://m.3g.fcful.cn/snews/379996.htm
- http://m.3g.fcful.cn/snews/35770.htm
- http://m.3g.fcful.cn/snews/36798.htm
- http://m.3g.fcful.cn/snews/6879.htm
- http://m.3g.fcful.cn/snews/597007.htm
- http://m.3g.fcful.cn/snews/7507.htm
- http://m.3g.fcful.cn/snews/500691.htm
- http://m.3g.fcful.cn/snews/222941.htm
- http://m.3g.fcful.cn/snews/321419.htm
- http://m.3g.fcful.cn/snews/707162.htm
- http://m.3g.fcful.cn/snews/77062.htm
- http://m.3g.fcful.cn/snews/779461.htm
- http://m.3g.fcful.cn/snews/7568567.htm
- http://m.3g.fcful.cn/snews/8915.htm
- http://m.3g.fcful.cn/snews/9839.htm
- http://m.3g.fcful.cn/snews/26524.htm
- http://m.3g.fcful.cn/snews/442745.htm
- http://m.3g.fcful.cn/snews/637568.htm
- http://m.3g.fcful.cn/snews/02612.htm
- http://m.3g.fcful.cn/snews/7275511.htm
- http://m.3g.fcful.cn/snews/9149.htm
- http://m.3g.fcful.cn/snews/1009489.htm
- http://m.3g.fcful.cn/snews/22472.htm
- http://m.3g.fcful.cn/snews/3119.htm
- http://m.3g.fcful.cn/snews/300246.htm
- http://m.3g.fcful.cn/snews/168076.htm
- http://m.3g.fcful.cn/snews/75878.htm
- http://m.3g.fcful.cn/snews/533245.htm
- http://m.3g.fcful.cn/snews/6377.htm
- http://m.3g.fcful.cn/snews/498836.htm
- http://m.3g.fcful.cn/snews/4826.htm
- http://m.3g.fcful.cn/snews/8191927.htm
- http://m.3g.fcful.cn/snews/9802.htm
- http://m.3g.fcful.cn/snews/3025.htm
- http://m.3g.fcful.cn/snews/0842.htm
- http://m.3g.fcful.cn/snews/928523.htm
- http://m.3g.fcful.cn/snews/668702.htm
- http://m.3g.fcful.cn/snews/72178.htm
- http://m.3g.fcful.cn/snews/1668.htm
- http://m.3g.fcful.cn/snews/5717319.htm
- http://m.3g.fcful.cn/snews/2468.htm
- http://m.3g.fcful.cn/snews/9933.htm
- http://m.3g.fcful.cn/snews/0841.htm
- http://m.3g.fcful.cn/snews/799367.htm
- http://m.3g.fcful.cn/snews/3521.htm
- http://m.3g.fcful.cn/snews/286463.htm
- http://m.3g.fcful.cn/snews/7425.htm
- http://m.3g.fcful.cn/snews/126015.htm
- http://m.3g.fcful.cn/snews/3838384.htm
- http://m.3g.fcful.cn/snews/2044817.htm
- http://m.3g.fcful.cn/snews/4443772.htm
- http://m.3g.fcful.cn/snews/3504163.htm
- http://m.3g.fcful.cn/snews/573821.htm
- http://m.3g.fcful.cn/snews/7855.htm
- http://m.3g.fcful.cn/snews/4474357.htm
- http://m.3g.fcful.cn/snews/2406.htm
- http://m.3g.fcful.cn/snews/4677.htm
- http://m.3g.fcful.cn/snews/075374.htm
- http://m.3g.fcful.cn/snews/70539.htm
- http://m.3g.fcful.cn/snews/3578136.htm
- http://m.3g.fcful.cn/snews/017441.htm
- http://m.3g.fcful.cn/snews/33760.htm
- http://m.3g.fcful.cn/snews/6334.htm
- http://m.3g.fcful.cn/snews/8251173.htm
- http://m.3g.fcful.cn/snews/0657.htm
- http://m.3g.fcful.cn/snews/516136.htm
- http://m.3g.fcful.cn/snews/698477.htm
- http://m.3g.fcful.cn/snews/87162.htm
- http://m.3g.fcful.cn/snews/548556.htm
- http://m.3g.fcful.cn/snews/4534452.htm
- http://m.3g.fcful.cn/snews/2978062.htm
- http://m.3g.fcful.cn/snews/99876.htm
- http://m.3g.fcful.cn/snews/1263.htm
- http://m.3g.fcful.cn/snews/8395027.htm
- http://m.3g.fcful.cn/snews/874042.htm
- http://m.3g.fcful.cn/snews/80014.htm
- http://m.3g.fcful.cn/snews/1987747.htm
- http://m.3g.fcful.cn/snews/928435.htm
- http://m.3g.fcful.cn/snews/996326.htm
- http://m.3g.fcful.cn/snews/9058.htm
- http://m.3g.fcful.cn/snews/0811.htm
- http://m.3g.fcful.cn/snews/602349.htm
- http://m.3g.fcful.cn/snews/996027.htm
- http://m.3g.fcful.cn/snews/0089.htm
- http://m.3g.fcful.cn/snews/33069.htm
- http://m.3g.fcful.cn/snews/51864.htm
- http://m.3g.fcful.cn/snews/299180.htm
- http://m.3g.fcful.cn/snews/509310.htm

## 项目结构

```
snews-indexer/
├── cli.py                      # 命令行入口，解析子命令并调度核心流程
├── config.example.yaml         # 示例配置文件，包含所有可调参数及说明
├── requirements.txt            # Python 依赖清单，锁定主要版本范围
├── src/
│   ├── core/
│   │   ├── engine.py           # 抓取引擎主循环，协调队列、请求与存储
│   │   ├── queue.py            # 基于 SQLite 的持久化任务队列实现
│   │   └── state.py            # 任务状态机定义（待处理、处理中、成功、失败）
│   ├── fetcher/
│   │   ├── client.py           # HTTP 客户端封装，配置超时、重试与请求头
│   │   ├── parser.py           # 内容抽取器，应用选择器规则提取字段
│   │   └── middleware.py       # 请求预处理与响应后处理钩子
│   ├── storage/
│   │   ├── writer.py           # 将结构化结果写入 SQLite / JSON / CSV
│   │   ├── schema.py           # 数据库表结构定义与迁移脚本
│   │   └── hash.py             # 内容哈希计算，用于增量变更检测
│   ├── utils/
│   │   ├── logger.py           # 日志配置，支持文件轮转与不同级别输出
│   │   ├── validator.py        # URL 校验、字段类型检查工具
│   │   └── timer.py            # 运行时长统计与进度估算辅助
│   └── plugins/
│       ├── builtin/            # 内置选择器模板，覆盖常见页面布局
│       └── custom/             # 用户自定义选择器存放目录（可热加载）
├── tests/
│   ├── unit/                   # 单元测试，覆盖核心工具与抽取逻辑
│   └── integration/            # 集成测试，使用本地 mock 服务验证完整流程
├── docs/                       # 文档源码，包含入门、配置与选择器编写指南
├── scripts/
│   ├── export.py               # 独立导出脚本，将 SQLite 转为其他格式
│   └── cleanup.py              # 清理过期任务记录与临时文件
└── LICENSE                     # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制到个人账户下，然后克隆到本地开发环境。建议在 dev 分支上进行所有修改，避免直接操作主分支。

2. 运行测试套件确保现有功能通过，使用 `pytest tests/unit` 执行单元测试。新增功能或修复缺陷时，需同步编写对应的测试用例，覆盖正常路径与边界条件。

3. 若涉及选择器引擎或配置格式变更，请在 `docs/` 目录下更新相应文档，并确保示例配置文件的注释足够清晰。提交前执行 `python scripts/format.py` 统一代码风格。

4. 提交 Pull Request 时描述变更目的、影响范围以及测试结果。若为性能优化或 API 变更，需提供基准测试数据或迁移说明。PR 至少需要一名核心维护者审核通过方可合并。

5. 报告问题或提议新功能时请使用 Issue 模板，包含运行环境版本、配置文件关键项和完整错误堆栈，以便快速定位问题。

## 常见问题

**Q1：抓取过程中部分链接始终返回 404 或超时，应如何处理？**

A1：首先检查网络环境与目标站点可用性。若确认站点正常，可调整 `config.yaml` 中的 `timeout` 和 `max_retries` 参数增加等待时长和重试次数。对于永久失效的链接，可使用 `cli.py remove --failed` 命令从队列中清除，或将其导出至单独文件以便后续人工核查。

**Q2：如何为不同页面结构编写自定义选择器？**

A2：在 `config.yaml` 的 `selectors` 字段中按域名或 URL 前缀定义映射关系，支持 CSS 选择器和 XPath 混合编写。具体语法参考 `docs/selector_guide.md` 中的示例模板。若多个页面共享同一结构，可继承基础配置减少重复定义。

**Q3：任务运行中途被终止，重启后会重复抓取已完成的链接吗？**

A3：不会。任务队列使用 SQLite 持久化存储每条记录的状态，已标记为 `success` 的链接在重启后会被自动跳过。若需强制重新抓取，可使用 `cli.py reset --url <target>` 将特定链接状态重置为 `pending`。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
