# WebLink Archive Collector

WebLink Archive Collector 是一个面向技术文档归档、外链资源聚合与历史内容回溯的开源工具集。该项目定位于帮助开发者、研究员与内容运营人员系统化地收集、校验和呈现来自特定内容源的历史文章链接，并提供结构化的元数据提取与快照管理能力。目标用户包括需要长期保存参考链接的技术博主、进行网络内容变迁研究的学术人员，以及构建内部知识库时需批量导入外链资源的工程团队。通过本工具，用户能够将分散的 URL 资源转化为可检索、可版本化、可导出的结构化数据集，有效解决链接失效、内容分散和手工整理效率低下等问题。

## 功能概览

批量链接抓取与去重 提供基于 HTTP 请求的链接状态检查与内容摘要抽取，支持对大批量 URL 进行并发探测，自动标记不可达链接并生成健康报告。

自定义元数据标注 允许用户为每条链接添加自定义标签、分类层级和备注说明，支持通过 YAML 或 JSON 配置文件批量导入标注规则。

多格式数据导出 支持将整理后的链接数据导出为 CSV、JSON、Markdown 表格或 HTML 索引页，便于嵌入现有文档系统或静态站点。

增量更新与变更追踪 通过记录每次扫描的时间戳与状态变化，生成链接变更日志，帮助用户掌握目标源的内容更新频率与链接生命周期。

本地快照存储 支持将目标页面内容保存为本地 HTML 或 Markdown 文件，形成离线可用的镜像副本，并保留原始 URL 与保存路径的映射关系。

正则表达式过滤与匹配 内置基于正则表达式的链接筛选引擎，用户可定义包含或排除规则，精准锁定特定路径、文件类型或参数格式的资源。

任务编排与定时执行 提供命令行任务调度接口，支持通过 cron 表达式或系统定时器自动执行链接收集与状态刷新流程。

## 应用场景

技术博客历史文章归档 当技术博客平台发生迁移或内容改版时，用户可通过本工具批量抓取指定域名下的历史文章链接，生成完整的文章索引表，并自动下载每篇文章的正文快照，防止原始内容丢失。

学术研究中的网络引用追踪 学术工作者在分析某类网络内容的传播路径或引用关系时，可利用本工具定期采集特定来源的链接列表，结合时间戳与状态码变化，量化分析内容的存续率与更新模式。

企业内部知识库外链管理 企业知识库管理员在整合团队收藏的参考链接时，可使用本工具的批量导入与标注功能，统一补充分类标签、负责人信息和校验日期，生成可公开查阅的外链资源目录，并周期性检查链接可用性。

## 快速开始

以下命令演示了从克隆仓库到执行首次链接收集的完整流程。请确保系统已安装 Git 与 Python 3.9 及以上版本。

```bash
git clone https://github.com/weblink-archive/collector.git
cd collector
pip install -r requirements.txt
cp config.example.yaml config.yaml
python cli.py collect --source list.txt --output report.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，推荐使用 3.10 以获得最佳兼容性 |
| requests | 2.28.0 或更高 | 用于发起 HTTP 请求并处理响应状态码与头部信息 |
| beautifulsoup4 | 4.11.0 或更高 | 解析 HTML 页面，提取标题、正文摘要与元数据 |
| pyyaml | 6.0 或更高 | 加载配置文件与自定义标注规则 |
| pandas | 1.5.0 或更高 | 用于数据表格的批量处理与导出操作（可选，但强烈建议安装） |
| lxml | 4.9.0 或更高 | 作为 beautifulsoup4 的解析器后端，提升解析性能与容错性 |
| pytest | 7.0.0 或更高 | 仅开发与测试时需要，用于运行单元测试用例 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置并首次运行本工具；配置文件各字段的含义与示例 |
| 命令参考 | docs/commands.md | 所有可用子命令（collect, check, export, snapshot）的参数说明与用法范例 |
| 标注规范 | docs/annotation-guide.md | 如何编写标签规则文件，支持哪些元数据字段，以及如何应用分类模板 |
| 架构设计 | docs/architecture.md | 核心模块（抓取器、解析器、存储层、导出器）的职责划分与数据流向 |

## 资源列表

- http://m.blog.fcful.cn/bnews/042454.htm
- http://m.blog.fcful.cn/bnews/0139.htm
- http://m.blog.fcful.cn/bnews/793220.htm
- http://m.blog.fcful.cn/bnews/9696704.htm
- http://m.blog.fcful.cn/bnews/610766.htm
- http://m.blog.fcful.cn/bnews/4744.htm
- http://m.blog.fcful.cn/bnews/2857727.htm
- http://m.blog.fcful.cn/bnews/790005.htm
- http://m.blog.fcful.cn/bnews/2219207.htm
- http://m.blog.fcful.cn/bnews/79227.htm
- http://m.blog.fcful.cn/bnews/8961590.htm
- http://m.blog.fcful.cn/bnews/497958.htm
- http://m.blog.fcful.cn/bnews/4642.htm
- http://m.blog.fcful.cn/bnews/83899.htm
- http://m.blog.fcful.cn/bnews/5397558.htm
- http://m.blog.fcful.cn/bnews/78233.htm
- http://m.blog.fcful.cn/bnews/2030.htm
- http://m.blog.fcful.cn/bnews/2135282.htm
- http://m.blog.fcful.cn/bnews/0725755.htm
- http://m.blog.fcful.cn/bnews/407700.htm
- http://m.blog.fcful.cn/bnews/6427629.htm
- http://m.blog.fcful.cn/bnews/5875.htm
- http://m.blog.fcful.cn/bnews/601405.htm
- http://m.blog.fcful.cn/bnews/0431.htm
- http://m.blog.fcful.cn/bnews/914099.htm
- http://m.blog.fcful.cn/bnews/5502.htm
- http://m.blog.fcful.cn/bnews/6595.htm
- http://m.blog.fcful.cn/bnews/9310331.htm
- http://m.blog.fcful.cn/bnews/1892.htm
- http://m.blog.fcful.cn/bnews/8267.htm
- http://m.blog.fcful.cn/bnews/567152.htm
- http://m.blog.fcful.cn/bnews/1854.htm
- http://m.blog.fcful.cn/bnews/9642.htm
- http://m.blog.fcful.cn/bnews/232230.htm
- http://m.blog.fcful.cn/bnews/2813744.htm
- http://m.blog.fcful.cn/bnews/083027.htm
- http://m.blog.fcful.cn/bnews/97485.htm
- http://m.blog.fcful.cn/bnews/910721.htm
- http://m.blog.fcful.cn/bnews/781663.htm
- http://m.blog.fcful.cn/bnews/60216.htm
- http://m.blog.fcful.cn/bnews/3358644.htm
- http://m.blog.fcful.cn/bnews/939174.htm
- http://m.blog.fcful.cn/bnews/82075.htm
- http://m.blog.fcful.cn/bnews/3427.htm
- http://m.blog.fcful.cn/bnews/240426.htm
- http://m.blog.fcful.cn/bnews/7338482.htm
- http://m.blog.fcful.cn/bnews/00496.htm
- http://m.blog.fcful.cn/bnews/8372872.htm
- http://m.blog.fcful.cn/bnews/24643.htm
- http://m.blog.fcful.cn/bnews/959581.htm
- http://m.blog.fcful.cn/bnews/165782.htm
- http://m.blog.fcful.cn/bnews/5850.htm
- http://m.blog.fcful.cn/bnews/4867043.htm
- http://m.blog.fcful.cn/bnews/993782.htm
- http://m.blog.fcful.cn/bnews/3733802.htm
- http://m.blog.fcful.cn/bnews/0814798.htm
- http://m.blog.fcful.cn/bnews/0443933.htm
- http://m.blog.fcful.cn/bnews/80926.htm
- http://m.blog.fcful.cn/bnews/315248.htm
- http://m.blog.fcful.cn/bnews/68897.htm
- http://m.blog.fcful.cn/bnews/80896.htm
- http://m.blog.fcful.cn/bnews/13628.htm
- http://m.blog.fcful.cn/bnews/437770.htm
- http://m.blog.fcful.cn/bnews/2434252.htm
- http://m.blog.fcful.cn/bnews/5056499.htm
- http://m.blog.fcful.cn/bnews/8733.htm
- http://m.blog.fcful.cn/bnews/818549.htm
- http://m.blog.fcful.cn/bnews/62274.htm
- http://m.blog.fcful.cn/bnews/835638.htm
- http://m.blog.fcful.cn/bnews/444048.htm
- http://m.blog.fcful.cn/bnews/6201032.htm
- http://m.blog.fcful.cn/bnews/7088.htm
- http://m.blog.fcful.cn/bnews/4192345.htm
- http://m.blog.fcful.cn/bnews/8866.htm
- http://m.blog.fcful.cn/bnews/242673.htm
- http://m.blog.fcful.cn/bnews/9888982.htm
- http://m.blog.fcful.cn/bnews/2063596.htm
- http://m.blog.fcful.cn/bnews/4113275.htm
- http://m.blog.fcful.cn/bnews/04467.htm
- http://m.blog.fcful.cn/bnews/409851.htm
- http://m.blog.fcful.cn/bnews/11223.htm
- http://m.blog.fcful.cn/bnews/5225.htm
- http://m.blog.fcful.cn/bnews/534676.htm
- http://m.blog.fcful.cn/bnews/401924.htm
- http://m.blog.fcful.cn/bnews/893059.htm
- http://m.blog.fcful.cn/bnews/7225.htm
- http://m.blog.fcful.cn/bnews/718641.htm
- http://m.blog.fcful.cn/bnews/41238.htm
- http://m.blog.fcful.cn/bnews/86490.htm
- http://m.blog.fcful.cn/bnews/408218.htm
- http://m.blog.fcful.cn/bnews/48094.htm
- http://m.blog.fcful.cn/bnews/0954.htm
- http://m.blog.fcful.cn/bnews/7532201.htm
- http://m.blog.fcful.cn/bnews/73243.htm
- http://m.blog.fcful.cn/bnews/2930.htm
- http://m.blog.fcful.cn/bnews/739482.htm
- http://m.blog.fcful.cn/bnews/8593.htm
- http://m.blog.fcful.cn/bnews/2387.htm
- http://m.blog.fcful.cn/bnews/14402.htm
- http://m.blog.fcful.cn/bnews/185025.htm
- http://m.blog.fcful.cn/bnews/929075.htm
- http://m.blog.fcful.cn/bnews/5882.htm
- http://m.blog.fcful.cn/bnews/19495.htm
- http://m.blog.fcful.cn/bnews/0301.htm
- http://m.blog.fcful.cn/bnews/31807.htm
- http://m.blog.fcful.cn/bnews/5244.htm
- http://m.blog.fcful.cn/bnews/34714.htm
- http://m.blog.fcful.cn/bnews/6761317.htm
- http://m.blog.fcful.cn/bnews/0578850.htm
- http://m.blog.fcful.cn/bnews/14423.htm
- http://m.blog.fcful.cn/bnews/18777.htm
- http://m.blog.fcful.cn/bnews/1864.htm
- http://m.blog.fcful.cn/bnews/916826.htm
- http://m.blog.fcful.cn/bnews/8915.htm
- http://m.blog.fcful.cn/bnews/08357.htm
- http://m.blog.fcful.cn/bnews/6528809.htm
- http://m.blog.fcful.cn/bnews/86965.htm
- http://m.blog.fcful.cn/bnews/92396.htm
- http://m.blog.fcful.cn/bnews/7353.htm
- http://m.blog.fcful.cn/bnews/76263.htm
- http://m.blog.fcful.cn/bnews/2071.htm
- http://m.blog.fcful.cn/bnews/1579.htm
- http://m.blog.fcful.cn/bnews/975518.htm
- http://m.blog.fcful.cn/bnews/9236.htm
- http://m.blog.fcful.cn/bnews/0759.htm
- http://m.blog.fcful.cn/bnews/397236.htm
- http://m.blog.fcful.cn/bnews/29061.htm
- http://m.blog.fcful.cn/bnews/434683.htm
- http://m.blog.fcful.cn/bnews/101930.htm
- http://m.blog.fcful.cn/bnews/57839.htm
- http://m.blog.fcful.cn/bnews/67600.htm
- http://m.blog.fcful.cn/bnews/7920.htm
- http://m.blog.fcful.cn/bnews/9771894.htm
- http://m.blog.fcful.cn/bnews/8348614.htm
- http://m.blog.fcful.cn/bnews/148592.htm
- http://m.blog.fcful.cn/bnews/7858.htm
- http://m.blog.fcful.cn/bnews/11409.htm
- http://m.blog.fcful.cn/bnews/95270.htm
- http://m.blog.fcful.cn/bnews/5964.htm
- http://m.blog.fcful.cn/bnews/545535.htm
- http://m.blog.fcful.cn/bnews/7114075.htm
- http://m.blog.fcful.cn/bnews/3696571.htm
- http://m.blog.fcful.cn/bnews/5709.htm
- http://m.blog.fcful.cn/bnews/0801.htm
- http://m.blog.fcful.cn/bnews/03192.htm
- http://m.blog.fcful.cn/bnews/36798.htm
- http://m.blog.fcful.cn/bnews/66332.htm
- http://m.blog.fcful.cn/bnews/16033.htm
- http://m.blog.fcful.cn/bnews/29870.htm
- http://m.blog.fcful.cn/bnews/362704.htm
- http://m.blog.fcful.cn/bnews/497933.htm
- http://m.blog.fcful.cn/bnews/39436.htm
- http://m.blog.fcful.cn/bnews/179644.htm
- http://m.blog.fcful.cn/bnews/9696.htm
- http://m.blog.fcful.cn/bnews/937731.htm
- http://m.blog.fcful.cn/bnews/765754.htm
- http://m.blog.fcful.cn/bnews/86406.htm
- http://m.blog.fcful.cn/bnews/5023.htm
- http://m.blog.fcful.cn/bnews/057568.htm
- http://m.blog.fcful.cn/bnews/3221061.htm
- http://m.blog.fcful.cn/bnews/14975.htm
- http://m.blog.fcful.cn/bnews/19786.htm
- http://m.blog.fcful.cn/bnews/2239331.htm
- http://m.blog.fcful.cn/bnews/679629.htm
- http://m.blog.fcful.cn/bnews/795813.htm
- http://m.blog.fcful.cn/bnews/458123.htm
- http://m.blog.fcful.cn/bnews/56018.htm
- http://m.blog.fcful.cn/bnews/7140461.htm
- http://m.blog.fcful.cn/bnews/21371.htm
- http://m.blog.fcful.cn/bnews/092872.htm
- http://m.blog.fcful.cn/bnews/98593.htm
- http://m.blog.fcful.cn/bnews/901512.htm
- http://m.blog.fcful.cn/bnews/322768.htm
- http://m.blog.fcful.cn/bnews/13500.htm
- http://m.blog.fcful.cn/bnews/419620.htm
- http://m.blog.fcful.cn/bnews/8056.htm
- http://m.blog.fcful.cn/bnews/541199.htm
- http://m.blog.fcful.cn/bnews/505771.htm
- http://m.blog.fcful.cn/bnews/23177.htm
- http://m.blog.fcful.cn/bnews/8044.htm
- http://m.blog.fcful.cn/bnews/671058.htm
- http://m.blog.fcful.cn/bnews/33238.htm
- http://m.blog.fcful.cn/bnews/460011.htm
- http://m.blog.fcful.cn/bnews/695467.htm
- http://m.blog.fcful.cn/bnews/4143218.htm
- http://m.blog.fcful.cn/bnews/9281365.htm
- http://m.blog.fcful.cn/bnews/4819.htm
- http://m.blog.fcful.cn/bnews/5829414.htm
- http://m.blog.fcful.cn/bnews/9186517.htm
- http://m.blog.fcful.cn/bnews/0467.htm
- http://m.blog.fcful.cn/bnews/150379.htm
- http://m.blog.fcful.cn/bnews/9305646.htm
- http://m.blog.fcful.cn/bnews/2855604.htm
- http://m.blog.fcful.cn/bnews/89196.htm
- http://m.blog.fcful.cn/bnews/8580.htm
- http://m.blog.fcful.cn/bnews/0017137.htm
- http://m.blog.fcful.cn/bnews/14062.htm
- http://m.blog.fcful.cn/bnews/098590.htm
- http://m.blog.fcful.cn/bnews/81095.htm
- http://m.blog.fcful.cn/bnews/8966724.htm
- http://m.blog.fcful.cn/bnews/175482.htm
- http://m.blog.fcful.cn/bnews/4276.htm
- http://m.blog.fcful.cn/bnews/0908869.htm
- http://m.blog.fcful.cn/bnews/82914.htm
- http://m.blog.fcful.cn/bnews/1968343.htm
- http://m.blog.fcful.cn/bnews/5667277.htm
- http://m.blog.fcful.cn/bnews/8165657.htm
- http://m.blog.fcful.cn/bnews/3055.htm
- http://m.blog.fcful.cn/bnews/708366.htm
- http://m.blog.fcful.cn/bnews/650459.htm
- http://m.blog.fcful.cn/bnews/173744.htm
- http://m.blog.fcful.cn/bnews/7679.htm
- http://m.blog.fcful.cn/bnews/926958.htm
- http://m.blog.fcful.cn/bnews/619178.htm
- http://m.blog.fcful.cn/bnews/9241433.htm
- http://m.blog.fcful.cn/bnews/76667.htm
- http://m.blog.fcful.cn/bnews/3952892.htm
- http://m.blog.fcful.cn/bnews/90279.htm
- http://m.blog.fcful.cn/bnews/50623.htm
- http://m.blog.fcful.cn/bnews/2842862.htm
- http://m.blog.fcful.cn/bnews/490682.htm
- http://m.blog.fcful.cn/bnews/9778.htm
- http://m.blog.fcful.cn/bnews/8473596.htm
- http://m.blog.fcful.cn/bnews/319475.htm
- http://m.blog.fcful.cn/bnews/665770.htm
- http://m.blog.fcful.cn/bnews/0099819.htm
- http://m.blog.fcful.cn/bnews/87689.htm
- http://m.blog.fcful.cn/bnews/5569.htm
- http://m.blog.fcful.cn/bnews/326056.htm
- http://m.blog.fcful.cn/bnews/548798.htm
- http://m.blog.fcful.cn/bnews/8460.htm
- http://m.blog.fcful.cn/bnews/254933.htm
- http://m.blog.fcful.cn/bnews/53813.htm
- http://m.blog.fcful.cn/bnews/30837.htm
- http://m.blog.fcful.cn/bnews/86380.htm
- http://m.blog.fcful.cn/bnews/13663.htm
- http://m.blog.fcful.cn/bnews/9299698.htm
- http://m.blog.fcful.cn/bnews/78065.htm
- http://m.blog.fcful.cn/bnews/3575896.htm
- http://m.blog.fcful.cn/bnews/6712.htm
- http://m.blog.fcful.cn/bnews/8188.htm
- http://m.blog.fcful.cn/bnews/880605.htm
- http://m.blog.fcful.cn/bnews/803801.htm
- http://m.blog.fcful.cn/bnews/622070.htm
- http://m.blog.fcful.cn/bnews/288463.htm
- http://m.blog.fcful.cn/bnews/5761177.htm
- http://m.blog.fcful.cn/bnews/9459012.htm
- http://m.blog.fcful.cn/bnews/7227.htm
- http://m.blog.fcful.cn/bnews/8722838.htm
- http://m.blog.fcful.cn/bnews/5345216.htm

## 项目结构

```
collector/
├── cli.py                         # 命令行入口，注册所有子命令并解析参数
├── config.example.yaml            # 示例配置文件，包含抓取并发数、超时时间与输出路径
├── requirements.txt               # Python 依赖列表，固定版本号以保障环境一致性
├── collector/
│   ├── __init__.py                # 包初始化，暴露核心 API：Collector, Exporter, Snapshot
│   ├── fetcher.py                 # 抓取器模块：管理 HTTP 会话、重试策略与 robots.txt 遵守逻辑
│   ├── parser.py                  # 解析器模块：基于 beautifulsoup4 提取标题、正文与 meta 信息
│   ├── storage.py                 # 存储模块：提供内存缓存、SQLite 持久化与文件系统快照写入
│   ├── exporter.py                # 导出器模块：将数据集转换为 CSV、JSON、Markdown 或 HTML 格式
│   └── utils.py                   # 工具函数：日期格式化、URL 规范化、正则匹配辅助等
├── tests/
│   ├── test_fetcher.py            # 抓取器单元测试，包含 mock 服务与异常场景覆盖
│   ├── test_parser.py             # 解析器单元测试，使用固定 HTML 样本验证提取逻辑
│   └── test_exporter.py           # 导出器单元测试，校验各输出格式的字段完整性与编码正确性
├── docs/
│   ├── getting-started.md         # 入门指南：安装、配置与首次运行步骤详解
│   ├── commands.md                # 命令参考：所有子命令的参数、选项与使用示例
│   ├── annotation-guide.md        # 标注规范：标签语法、分类模板与批量导入说明
│   └── architecture.md            # 架构设计：模块职责、数据流与扩展点说明
├── examples/
│   ├── sample_list.txt            # 示例输入文件，包含用于测试的 URL 列表
│   └── custom_tags.yaml           # 自定义标注规则示例，展示标签层级与匹配模式
└── .github/
    └── workflows/
        └── ci.yml                 # GitHub Actions 持续集成配置，运行测试与代码风格检查
```

## 贡献指南

1. 阅读项目行为准则与贡献守则，确保理解代码提交规范、测试覆盖率要求以及文档同步更新的义务。所有贡献者需签署开发者原产地证书以表明代码原创性。

2. 在 GitHub Issues 中查找或创建与您的修改相关的工单，简要描述所解决的问题或希望增加的功能。建议在开始实质性编码前与维护者沟通设计思路，避免不必要的返工。

3. 从主分支派生个人副本，并在本地新建功能分支进行开发。分支命名建议采用 feature/功能简述 或 fix/问题简述 格式，确保每次提交包含清晰且原子化的变更说明。

4. 完成代码修改后，运行完整的测试套件（pytest tests/）并确保所有已有测试通过。若新增功能或修复缺陷，需同步添加对应的单元测试用例，且新代码的行覆盖率不低于百分之八十五。

5. 提交拉取请求时，在描述中引用关联的 Issue 编号，并附上修改前后的行为对比或测试结果截图。请求将经过至少一名维护者的代码审查，审查通过后合并至主分支。

## 常见问题

问：收集过程中遇到大量 HTTP 超时或连接拒绝错误应如何排查？

答：首先检查目标站点是否可公开访问，以及是否存在防火墙或反爬策略。本工具默认使用 10 秒超时和最多 3 次重试，您可以在配置文件中调整 timeout 和 max_retries 参数。若目标站点需使用特定 User-Agent 或 Cookie，请在配置文件的 headers 字段中设置。另外，建议适当降低并发数以避免被目标服务器限流。

问：如何将收集到的链接数据与现有文档系统（如 VuePress、Docusaurus）集成？

答：本工具的导出器支持生成 Markdown 表格格式和 JSON 格式。对于静态站点生成器，您可以将 JSON 导出文件放置在站点数据目录下，并通过模板脚本渲染为自定义页面。对于 Markdown 表格输出，可直接将其内容复制或通过脚本插入到现有文档页面的指定位置。项目文档中的命令参考章节详细说明了每种导出格式的字段映射与定制选项。

问：增量更新时如何避免重复记录同一链接的历史快照？

答：存储模块基于 URL 的规范化形式（去除尾部斜杠、统一协议为小写）作为主键，并记录首次发现时间和最后校验时间。在增量扫描时，若链接已存在于数据库中，则只更新状态码、响应时间和内容摘要字段，不会重复保存页面全文。如果您希望保留每次扫描的完整快照版本，可在配置中启用 versioned_snapshot 选项，此时存储模块会按时间戳创建目录分层保存。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
