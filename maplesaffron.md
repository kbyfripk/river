# News Index Aggregator

News Index Aggregator 是一个面向技术信息采集与新闻外链管理的开源工具集，专注于对来自指定内容源的文章索引进行统一归档、分类检索与批量导出。该项目适用于需要定期整理大量新闻链接、构建自定义新闻聚合页或进行内容趋势分析的开发者与研究人员。

项目本身不提供内容抓取与渲染能力，而是围绕外链数据的结构化存储与查询接口提供一套轻量级管理方案。用户可通过命令行工具批量导入链接、添加元数据标签、按条件筛选导出，并生成静态目录页。该项目的核心价值在于将分散的新闻索引链接转化为可检索、可审计、可持久化的本地数据集，适用于个人知识库构建、企业内部资讯周报自动化以及学术领域的媒体传播研究。

## 功能概览

批量链接导入：支持从纯文本文件、CSV 或标准输入中读取大量 URL，自动去重并校验协议格式，默认过滤非 HTTP/HTTPS 链接。

元数据标注系统：每条链接可附加自定义键值对元数据，包括但不限于来源站点、抓取时间、内容摘要、分类标签和重要等级，元数据以 JSON 格式存储于同目录索引文件中。

多条件组合检索：提供结构化查询接口，支持按域名、时间范围、标签组合、ID 区间等条件进行筛选，返回匹配的链接列表或计数统计。

静态目录生成：内置模板引擎，可将筛选结果渲染为 HTML 目录页，支持自定义模板路径和输出文件名，便于快速发布为内部资讯看板。

导入导出兼容性：支持导入导出为 JSON、CSV 和 Markdown 列表格式，导出文件可直接用于其他文档工具或静态站点生成器。

链接状态检查：集成轻量级 HTTP 头探测功能，可批量检查链接可达性并记录状态码，便于清理失效资源。

增量更新机制：支持基于已有索引文件的增量导入，自动合并新链接并标记重复项，避免全量重建。

命令行交互与脚本化：所有功能均通过命令行子命令提供，支持 Shell 脚本批量调用，便于集成至每日定时任务或 CI 流水线。

## 应用场景

内部资讯周报自动化：企业技术团队可使用该项目每日导入外部新闻链接，按标签筛选后生成周报目录页，减少人工整理成本。

学术研究媒体采样：传播学或社会学研究者可利用该工具定期采集特定域名的新闻索引，构建时间序列数据集用于内容分析。

个人知识库外链管理：个人开发者或博主可将日常阅读的新闻链接统一导入，按主题分类并生成静态页面，作为个人资讯聚合站。

运维监控信息汇总：运维团队可将不同监控系统产生的告警文档链接汇总至统一索引，结合状态检查功能快速定位不可达的故障报告。

数据迁移与归档辅助：在内容平台迁移过程中，可使用该工具批量导出旧平台的文章链接列表，作为迁移清单或备份索引。

## 快速开始

以下命令演示了从克隆仓库到运行基础导入流程的完整步骤。

```bash
# 克隆项目仓库
git clone https://github.com/yourorg/news-index-aggregator.git
cd news-index-aggregator

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 准备链接文件 links.txt，每行一个 URL
# 执行导入命令，生成初始索引
nia-cli import --input links.txt --output index.json

# 按域名筛选并导出为 Markdown 列表
nia-cli filter --domain blog.gqskj.cn --format markdown --output filtered.md

# 生成静态 HTML 目录页
nia-cli render --template templates/default.html --data index.json --output index.html
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 及以上 | 核心运行环境，低于此版本将无法解析类型注解 |
| pip | 22.0 及以上 | 依赖安装工具，旧版本可能无法正确解析 pyproject.toml |
| requests | 2.28.0 及以上 | 用于链接状态检查中的 HTTP 请求发送 |
| click | 8.1.0 及以上 | 命令行接口框架，提供子命令与参数解析 |
| jinja2 | 3.1.0 及以上 | 静态目录页渲染所使用的模板引擎 |
| pytest | 7.0.0 及以上 | 仅开发测试需要，生产环境可不安装 |
| black | 22.0.0 及以上 | 仅代码格式化需要，非运行时依赖 |
| mypy | 0.990 及以上 | 仅类型检查需要，非运行时依赖 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何安装、初次配置以及执行第一个导入任务 |
| 命令参考 | docs/commands.md | 每个子命令的完整参数列表与使用示例 |
| 索引格式规范 | docs/index-schema.md | 索引 JSON 文件的字段定义、数据类型与扩展约定 |
| 模板开发指南 | docs/template-guide.md | 如何编写自定义渲染模板及可用的上下文变量 |
| 配置说明 | docs/configuration.md | 环境变量、配置文件路径与默认行为调整方式 |
| 性能调优 | docs/performance.md | 大规模链接导入与状态检查的并发参数建议 |
| 迁移指南 | docs/migration.md | 不同版本间索引格式变更与数据迁移步骤 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/763762.htm
- http://m.blog.gqskj.cn/nnews/589528.htm
- http://m.blog.gqskj.cn/nnews/900939.htm
- http://m.blog.gqskj.cn/nnews/8897.htm
- http://m.blog.gqskj.cn/nnews/7178708.htm
- http://m.blog.gqskj.cn/nnews/76803.htm
- http://m.blog.gqskj.cn/nnews/482907.htm
- http://m.blog.gqskj.cn/nnews/971191.htm
- http://m.blog.gqskj.cn/nnews/774079.htm
- http://m.blog.gqskj.cn/nnews/4534382.htm
- http://m.blog.gqskj.cn/nnews/74287.htm
- http://m.blog.gqskj.cn/nnews/7812484.htm
- http://m.blog.gqskj.cn/nnews/57946.htm
- http://m.blog.gqskj.cn/nnews/5256.htm
- http://m.blog.gqskj.cn/nnews/0264.htm
- http://m.blog.gqskj.cn/nnews/754171.htm
- http://m.blog.gqskj.cn/nnews/6049.htm
- http://m.blog.gqskj.cn/nnews/917442.htm
- http://m.blog.gqskj.cn/nnews/6124.htm
- http://m.blog.gqskj.cn/nnews/8834.htm
- http://m.blog.gqskj.cn/nnews/61492.htm
- http://m.blog.gqskj.cn/nnews/59119.htm
- http://m.blog.gqskj.cn/nnews/6289942.htm
- http://m.blog.gqskj.cn/nnews/7205.htm
- http://m.blog.gqskj.cn/nnews/8942349.htm
- http://m.blog.gqskj.cn/nnews/5132.htm
- http://m.blog.gqskj.cn/nnews/62988.htm
- http://m.blog.gqskj.cn/nnews/7809593.htm
- http://m.blog.gqskj.cn/nnews/736468.htm
- http://m.blog.gqskj.cn/nnews/4947.htm
- http://m.blog.gqskj.cn/nnews/6565.htm
- http://m.blog.gqskj.cn/nnews/1664500.htm
- http://m.blog.gqskj.cn/nnews/06253.htm
- http://m.blog.gqskj.cn/nnews/83480.htm
- http://m.blog.gqskj.cn/nnews/1846.htm
- http://m.blog.gqskj.cn/nnews/0932.htm
- http://m.blog.gqskj.cn/nnews/1551.htm
- http://m.blog.gqskj.cn/nnews/642861.htm
- http://m.blog.gqskj.cn/nnews/5071.htm
- http://m.blog.gqskj.cn/nnews/848254.htm
- http://m.blog.gqskj.cn/nnews/339391.htm
- http://m.blog.gqskj.cn/nnews/28195.htm
- http://m.blog.gqskj.cn/nnews/25622.htm
- http://m.blog.gqskj.cn/nnews/6663832.htm
- http://m.blog.gqskj.cn/nnews/529469.htm
- http://m.blog.gqskj.cn/nnews/67068.htm
- http://m.blog.gqskj.cn/nnews/159877.htm
- http://m.blog.gqskj.cn/nnews/5778434.htm
- http://m.blog.gqskj.cn/nnews/49881.htm
- http://m.blog.gqskj.cn/nnews/75166.htm
- http://m.blog.gqskj.cn/nnews/05704.htm
- http://m.blog.gqskj.cn/nnews/6279784.htm
- http://m.blog.gqskj.cn/nnews/411220.htm
- http://m.blog.gqskj.cn/nnews/80015.htm
- http://m.blog.gqskj.cn/nnews/44721.htm
- http://m.blog.gqskj.cn/nnews/791979.htm
- http://m.blog.gqskj.cn/nnews/75540.htm
- http://m.blog.gqskj.cn/nnews/4968.htm
- http://m.blog.gqskj.cn/nnews/8655674.htm
- http://m.blog.gqskj.cn/nnews/663457.htm
- http://m.blog.gqskj.cn/nnews/36817.htm
- http://m.blog.gqskj.cn/nnews/0414.htm
- http://m.blog.gqskj.cn/nnews/8581.htm
- http://m.blog.gqskj.cn/nnews/375409.htm
- http://m.blog.gqskj.cn/nnews/832736.htm
- http://m.blog.gqskj.cn/nnews/5844.htm
- http://m.blog.gqskj.cn/nnews/648736.htm
- http://m.blog.gqskj.cn/nnews/12614.htm
- http://m.blog.gqskj.cn/nnews/5695.htm
- http://m.blog.gqskj.cn/nnews/0159190.htm
- http://m.blog.gqskj.cn/nnews/88633.htm
- http://m.blog.gqskj.cn/nnews/489966.htm
- http://m.blog.gqskj.cn/nnews/6890.htm
- http://m.blog.gqskj.cn/nnews/919714.htm
- http://m.blog.gqskj.cn/nnews/9010.htm
- http://m.blog.gqskj.cn/nnews/61632.htm
- http://m.blog.gqskj.cn/nnews/620980.htm
- http://m.blog.gqskj.cn/nnews/488966.htm
- http://m.blog.gqskj.cn/nnews/102015.htm
- http://m.blog.gqskj.cn/nnews/00573.htm
- http://m.blog.gqskj.cn/nnews/457596.htm
- http://m.blog.gqskj.cn/nnews/8269180.htm
- http://m.blog.gqskj.cn/nnews/25171.htm
- http://m.blog.gqskj.cn/nnews/7671.htm
- http://m.blog.gqskj.cn/nnews/573813.htm
- http://m.blog.gqskj.cn/nnews/56855.htm
- http://m.blog.gqskj.cn/nnews/2302508.htm
- http://m.blog.gqskj.cn/nnews/6413.htm
- http://m.blog.gqskj.cn/nnews/29863.htm
- http://m.blog.gqskj.cn/nnews/0523.htm
- http://m.blog.gqskj.cn/nnews/54449.htm
- http://m.blog.gqskj.cn/nnews/3041.htm
- http://m.blog.gqskj.cn/nnews/1013124.htm
- http://m.blog.gqskj.cn/nnews/884043.htm
- http://m.blog.gqskj.cn/nnews/614327.htm
- http://m.blog.gqskj.cn/nnews/5251.htm
- http://m.blog.gqskj.cn/nnews/761233.htm
- http://m.blog.gqskj.cn/nnews/82960.htm
- http://m.blog.gqskj.cn/nnews/1800.htm
- http://m.blog.gqskj.cn/nnews/3073.htm
- http://m.blog.gqskj.cn/nnews/0634400.htm
- http://m.blog.gqskj.cn/nnews/04451.htm
- http://m.blog.gqskj.cn/nnews/9971.htm
- http://m.blog.gqskj.cn/nnews/8142066.htm
- http://m.blog.gqskj.cn/nnews/507704.htm
- http://m.blog.gqskj.cn/nnews/03943.htm
- http://m.blog.gqskj.cn/nnews/238184.htm
- http://m.blog.gqskj.cn/nnews/64638.htm
- http://m.blog.gqskj.cn/nnews/27666.htm
- http://m.blog.gqskj.cn/nnews/6595450.htm
- http://m.blog.gqskj.cn/nnews/6549492.htm
- http://m.blog.gqskj.cn/nnews/896719.htm
- http://m.blog.gqskj.cn/nnews/5324.htm
- http://m.blog.gqskj.cn/nnews/4594.htm
- http://m.blog.gqskj.cn/nnews/5445606.htm
- http://m.blog.gqskj.cn/nnews/646559.htm
- http://m.blog.gqskj.cn/nnews/8094.htm
- http://m.blog.gqskj.cn/nnews/185259.htm
- http://m.blog.gqskj.cn/nnews/268356.htm
- http://m.blog.gqskj.cn/nnews/963983.htm
- http://m.blog.gqskj.cn/nnews/4034031.htm
- http://m.blog.gqskj.cn/nnews/1535574.htm
- http://m.blog.gqskj.cn/nnews/6550.htm
- http://m.blog.gqskj.cn/nnews/58341.htm
- http://m.blog.gqskj.cn/nnews/719035.htm
- http://m.blog.gqskj.cn/nnews/914408.htm
- http://m.blog.gqskj.cn/nnews/03258.htm
- http://m.blog.gqskj.cn/nnews/0623859.htm
- http://m.blog.gqskj.cn/nnews/18974.htm
- http://m.blog.gqskj.cn/nnews/6625115.htm
- http://m.blog.gqskj.cn/nnews/97584.htm
- http://m.blog.gqskj.cn/nnews/800130.htm
- http://m.blog.gqskj.cn/nnews/3606.htm
- http://m.blog.gqskj.cn/nnews/67866.htm
- http://m.blog.gqskj.cn/nnews/79045.htm
- http://m.blog.gqskj.cn/nnews/8486241.htm
- http://m.blog.gqskj.cn/nnews/8326997.htm
- http://m.blog.gqskj.cn/nnews/0196125.htm
- http://m.blog.gqskj.cn/nnews/2816812.htm
- http://m.blog.gqskj.cn/nnews/2477.htm
- http://m.blog.gqskj.cn/nnews/609302.htm
- http://m.blog.gqskj.cn/nnews/743807.htm
- http://m.blog.gqskj.cn/nnews/500904.htm
- http://m.blog.gqskj.cn/nnews/3811800.htm
- http://m.blog.gqskj.cn/nnews/946668.htm
- http://m.blog.gqskj.cn/nnews/564174.htm
- http://m.blog.gqskj.cn/nnews/2657660.htm
- http://m.blog.gqskj.cn/nnews/39487.htm
- http://m.blog.gqskj.cn/nnews/8089.htm
- http://m.blog.gqskj.cn/nnews/13933.htm
- http://m.blog.gqskj.cn/nnews/2664412.htm
- http://m.blog.gqskj.cn/nnews/7420.htm
- http://m.blog.gqskj.cn/nnews/2536688.htm
- http://m.blog.gqskj.cn/nnews/55280.htm
- http://m.blog.gqskj.cn/nnews/9345.htm
- http://m.blog.gqskj.cn/nnews/321873.htm
- http://m.blog.gqskj.cn/nnews/36286.htm
- http://m.blog.gqskj.cn/nnews/9524.htm
- http://m.blog.gqskj.cn/nnews/2700205.htm
- http://m.blog.gqskj.cn/nnews/8031278.htm
- http://m.blog.gqskj.cn/nnews/13117.htm
- http://m.blog.gqskj.cn/nnews/991833.htm
- http://m.blog.gqskj.cn/nnews/7186854.htm
- http://m.blog.gqskj.cn/nnews/74603.htm
- http://m.blog.gqskj.cn/nnews/2967572.htm
- http://m.blog.gqskj.cn/nnews/414010.htm
- http://m.blog.gqskj.cn/nnews/187911.htm
- http://m.blog.gqskj.cn/nnews/677889.htm
- http://m.blog.gqskj.cn/nnews/40493.htm
- http://m.blog.gqskj.cn/nnews/35909.htm
- http://m.blog.gqskj.cn/nnews/5928070.htm
- http://m.blog.gqskj.cn/nnews/0854.htm
- http://m.blog.gqskj.cn/nnews/200209.htm
- http://m.blog.gqskj.cn/nnews/641491.htm
- http://m.blog.gqskj.cn/nnews/9651.htm
- http://m.blog.gqskj.cn/nnews/9939382.htm
- http://m.blog.gqskj.cn/nnews/0551024.htm
- http://m.blog.gqskj.cn/nnews/44561.htm
- http://m.blog.gqskj.cn/nnews/626464.htm
- http://m.blog.gqskj.cn/nnews/845180.htm
- http://m.blog.gqskj.cn/nnews/1142.htm
- http://m.blog.gqskj.cn/nnews/310436.htm
- http://m.blog.gqskj.cn/nnews/4621181.htm
- http://m.blog.gqskj.cn/nnews/709184.htm
- http://m.blog.gqskj.cn/nnews/5181.htm
- http://m.blog.gqskj.cn/nnews/4242946.htm
- http://m.blog.gqskj.cn/nnews/5633.htm
- http://m.blog.gqskj.cn/nnews/399296.htm
- http://m.blog.gqskj.cn/nnews/9864570.htm
- http://m.blog.gqskj.cn/nnews/256546.htm
- http://m.blog.gqskj.cn/nnews/37407.htm
- http://m.blog.gqskj.cn/nnews/118391.htm
- http://m.blog.gqskj.cn/nnews/028834.htm
- http://m.blog.gqskj.cn/nnews/53394.htm
- http://m.blog.gqskj.cn/nnews/19433.htm
- http://m.blog.gqskj.cn/nnews/54279.htm
- http://m.blog.gqskj.cn/nnews/8077588.htm
- http://m.blog.gqskj.cn/nnews/9515352.htm
- http://m.blog.gqskj.cn/nnews/63865.htm
- http://m.blog.gqskj.cn/nnews/0470689.htm
- http://m.blog.gqskj.cn/nnews/142893.htm
- http://m.blog.gqskj.cn/nnews/6425167.htm
- http://m.blog.gqskj.cn/nnews/349703.htm
- http://m.blog.gqskj.cn/nnews/276559.htm
- http://m.blog.gqskj.cn/nnews/5481630.htm
- http://m.blog.gqskj.cn/nnews/53116.htm
- http://m.blog.gqskj.cn/nnews/8571351.htm
- http://m.blog.gqskj.cn/nnews/289727.htm
- http://m.blog.gqskj.cn/nnews/340021.htm
- http://m.blog.gqskj.cn/nnews/157143.htm
- http://m.blog.gqskj.cn/nnews/6467.htm
- http://m.blog.gqskj.cn/nnews/162565.htm
- http://m.blog.gqskj.cn/nnews/1286527.htm
- http://m.blog.gqskj.cn/nnews/147677.htm
- http://m.blog.gqskj.cn/nnews/017690.htm
- http://m.blog.gqskj.cn/nnews/45290.htm
- http://m.blog.gqskj.cn/nnews/19279.htm
- http://m.blog.gqskj.cn/nnews/6209.htm
- http://m.blog.gqskj.cn/nnews/4753.htm
- http://m.blog.gqskj.cn/nnews/36721.htm
- http://m.blog.gqskj.cn/nnews/144136.htm
- http://m.blog.gqskj.cn/nnews/09710.htm
- http://m.blog.gqskj.cn/nnews/2703115.htm
- http://m.blog.gqskj.cn/nnews/78794.htm
- http://m.blog.gqskj.cn/nnews/18418.htm
- http://m.blog.gqskj.cn/nnews/94118.htm
- http://m.blog.gqskj.cn/nnews/638259.htm
- http://m.blog.gqskj.cn/nnews/69975.htm
- http://m.blog.gqskj.cn/nnews/1976.htm
- http://m.blog.gqskj.cn/nnews/4148.htm
- http://m.blog.gqskj.cn/nnews/073743.htm
- http://m.blog.gqskj.cn/nnews/82551.htm
- http://m.blog.gqskj.cn/nnews/902321.htm
- http://m.blog.gqskj.cn/nnews/3786208.htm
- http://m.blog.gqskj.cn/nnews/485440.htm
- http://m.blog.gqskj.cn/nnews/570906.htm
- http://m.blog.gqskj.cn/nnews/480944.htm
- http://m.blog.gqskj.cn/nnews/942793.htm
- http://m.blog.gqskj.cn/nnews/7185.htm
- http://m.blog.gqskj.cn/nnews/315957.htm
- http://m.blog.gqskj.cn/nnews/21025.htm
- http://m.blog.gqskj.cn/nnews/817607.htm
- http://m.blog.gqskj.cn/nnews/198516.htm
- http://m.blog.gqskj.cn/nnews/05829.htm
- http://m.blog.gqskj.cn/nnews/74434.htm
- http://m.blog.gqskj.cn/nnews/01030.htm
- http://m.blog.gqskj.cn/nnews/67557.htm
- http://m.blog.gqskj.cn/nnews/29640.htm
- http://m.blog.gqskj.cn/nnews/4489.htm
- http://m.blog.gqskj.cn/nnews/657971.htm

## 项目结构

```
news-index-aggregator/
├── src/                                # 核心源代码目录
│   ├── cli/                            # 命令行接口实现
│   │   ├── __init__.py                 # 包初始化，导出主命令组
│   │   ├── import_cmd.py               # import 子命令：链接导入与去重逻辑
│   │   ├── filter_cmd.py               # filter 子命令：多条件筛选与计数
│   │   ├── render_cmd.py               # render 子命令：静态目录页渲染
│   │   └── check_cmd.py                # check 子命令：HTTP 状态检查
│   ├── core/                           # 核心数据模型与索引操作
│   │   ├── __init__.py                 # 导出 Index 和 LinkEntry 类
│   │   ├── index.py                    # 索引加载、合并、序列化与反序列化
│   │   ├── link.py                     # 链接实体类，含校验与规范化方法
│   │   └── metadata.py                 # 元数据字典操作与标签解析工具
│   ├── utils/                          # 通用工具函数
│   │   ├── __init__.py                 # 导出 HTTP 客户端与文件工具
│   │   ├── http.py                     # requests 会话封装与重试策略
│   │   ├── fileio.py                   # 多格式文件读写（JSON/CSV/TXT）
│   │   └── validators.py               # URL 协议校验与域名提取
│   └── templates/                      # 内置渲染模板
│       ├── default.html                # 默认目录页模板，含分页与标签过滤
│       └── minimal.html                # 极简列表模板，仅输出链接与标题
├── tests/                              # 单元测试与集成测试
│   ├── test_cli/                       # 各子命令的 CLI 测试用例
│   ├── test_core/                      # 核心模型与索引操作测试
│   └── fixtures/                       # 测试用样本数据（links.txt / index.json）
├── docs/                               # 完整文档源文件
│   ├── getting-started.md              # 入门指南
│   ├── commands.md                     # 命令参考手册
│   ├── index-schema.md                 # 索引 JSON Schema 说明
│   ├── template-guide.md               # 模板开发指南
│   ├── configuration.md                # 配置项与环境变量
│   ├── performance.md                  # 性能调优建议
│   └── migration.md                    # 版本迁移指南
├── scripts/                            # 辅助运维脚本
│   ├── daily_import.sh                 # 每日定时导入示例脚本
│   └── export_all_formats.sh           # 批量导出为所有支持格式
├── pyproject.toml                      # 项目元数据与依赖定义（PEP 621）
├── requirements.txt                    # 运行时依赖锁定列表
├── requirements-dev.txt                # 开发时额外依赖（测试/格式化/类型检查）
├── Makefile                            # 常用命令快捷方式（install/test/lint）
├── README.md                           # 项目简介与快速开始（本文件）
└── LICENSE                             # MIT 许可证全文
```

## 贡献指南

贡献者需遵循以下流程以确保代码质量和文档一致性。

1. 查阅现有 Issue 与 Pull Request，确认无重复工作。对于新功能或较大改动，建议先创建 Issue 讨论设计方案。
2. 派生项目仓库至个人账号，在派生副本中创建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。
3. 编写代码时遵循项目已配置的 black 和 mypy 规则，提交前执行 `make lint` 与 `make test` 确保所有检查通过。
4. 更新或新增文档以反映代码变更，尤其是命令参数、配置项和索引 Schema 的调整。
5. 提交 Pull Request 至主仓库的 main 分支，描述中需明确关联 Issue 编号、变更内容及测试覆盖情况。

## 常见问题

**导入时提示 URL 格式无效，但链接在浏览器中可正常访问**

项目默认仅接受 HTTP 和 HTTPS 协议，且要求 URL 中包含有效域名。检查链接是否包含协议头，若为相对路径或协议缺失，请补全为完整 URL。此外，链接中的中文或特殊字符需进行百分号编码，否则校验会失败。

**筛选后导出的 Markdown 列表顺序与导入时不一致**

索引内部使用哈希表存储链接，默认迭代顺序不保留输入顺序。如需按导入顺序输出，可在 filter 命令中添加 `--preserve-order` 参数，此时将按首次出现的 ID 顺序排序。

**静态目录页渲染后部分链接显示为不可达，但实际服务正常**

状态检查功能默认使用超时 5 秒且不跟随重定向。若目标服务器响应较慢或使用严格的反爬机制，可能被误标记为不可达。可调整 `--timeout` 参数增大超时时间，或使用 `--no-check` 跳过状态检查仅生成目录。

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:15
