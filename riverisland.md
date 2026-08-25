# xnews-link-index

xnews-link-index 是一个面向移动端技术资讯与数据聚合的开源外链索引系统。该项目定位为技术资源与行业动态的轻量级导航中枢，服务于开发者、技术研究者以及信息聚合平台运维人员。xnews-link-index 不生产内容，而是通过结构化索引机制，将分散于互联网各处的技术文章、新闻快讯与数据报告以标准化条目形式归集，并提供统一的访问入口与元数据标记能力，从而降低信息发现成本，提升技术调研与竞品分析效率。

本项目由第 150/240 批资源导入驱动，当前索引容量超过 250 条外部链接，覆盖移动互联网、软件开发、数据科学、IT 基础设施等多个垂直领域。xnews-link-index 采用静态索引设计，无需运行时数据库，所有链接数据以纯文本格式存储，便于版本控制、差异比对与自动化流水线处理。

## 功能概览

- **批量链接导入**：支持以纯文本列表形式批量导入外部 URL，每行一条，自动去重并生成唯一条目标识。
- **分类标签生成**：基于 URL 路径特征与域名信息自动推断内容类别，如技术文章、新闻快讯、数据报告、产品发布等。
- **索引状态标记**：为每条链接记录索引时间、来源批次与校验状态，支持后续可用性检测与失效链接过滤。
- **静态站点生成**：内置简易模板引擎，可将索引数据渲染为静态 HTML 目录页，适合部署于 CDN 或对象存储。
- **元数据扩展接口**：提供 JSON 格式的元数据输出接口，允许外部工具读取链接列表并附加自定义字段，如阅读时长、关键词权重或重要性评分。
- **变更日志追踪**：每次索引更新自动生成变更摘要文件，记录新增、删除与修改的链接条目，便于审计与回滚。
- **多格式导出**：支持将索引数据导出为 CSV、JSON Lines 与 Markdown 表格三种格式，适配不同下游系统的数据消费需求。
- **健康检查脚本**：附带轻量级链接可达性检测工具，支持并发 HEAD 请求与超时控制，输出可达性报告。

## 应用场景

1. **技术团队日常资讯聚合**：开发团队可使用 xnews-link-index 汇总每日关注的技术博客、版本发布公告与安全预警链接，通过静态页面在团队内部共享，减少重复检索时间。

2. **竞品动态监测**：市场分析与产品团队可将竞争对手的官方公告、媒体报道与用户评价链接纳入索引，结合批次标记追踪信息变化趋势，辅助决策。

3. **开源项目文档外链管理**：开源项目维护者可将项目相关的参考文档、社区讨论帖与第三方评测文章统一收录，作为项目 Wiki 或 README 的外部延伸，方便贡献者快速获取背景信息。

4. **数据采集管道前置环节**：数据工程师可将 xnews-link-index 作为采集任务的目标源列表，定期导出待采集 URL，配合爬虫框架执行内容抓取，实现采集任务的配置化管理。

5. **个人知识库构建**：技术写作者或独立研究者可将日常阅读中发现的高质量外链导入索引，按批次与分类组织，构建个人化的技术资料参照体系。

## 快速开始

以下命令演示如何克隆仓库、安装依赖并运行索引构建流程。

```bash
git clone https://github.com/your-org/xnews-link-index.git
cd xnews-link-index
pip install -r requirements.txt
python build_index.py --input data/links_150.txt --output dist/index.html
```

上述命令使用 `data/links_150.txt` 作为输入文件，生成静态索引页面至 `dist/index.html`。如需导出 JSON 格式元数据，可追加 `--format json --output dist/index.json` 参数。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心脚本运行环境，用于索引构建与数据转换 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装依赖库 |
| requests | 2.28.0 及以上 | 健康检查脚本所需的 HTTP 客户端库 |
| beautifulsoup4 | 4.12.0 及以上 | 可选依赖，用于解析链接页面标题生成摘要 |
| lxml | 4.9.0 及以上 | 解析器后端，与 beautifulsoup4 配合使用 |
| pytest | 7.0.0 及以上 | 开发依赖，用于运行单元测试与集成测试 |
| black | 23.0.0 及以上 | 开发依赖，用于代码格式化 |
| pre-commit | 3.0.0 及以上 | 开发依赖，用于 Git 提交前自动检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/usage.md | 如何导入链接、生成索引页、导出不同格式数据以及执行健康检查 |
| 配置参考 | docs/configuration.md | 环境变量、命令行参数与配置文件字段的完整说明 |
| 开发指南 | docs/development.md | 代码结构、测试编写、提交规范与 PR 流程 |
| 设计说明 | docs/design.md | 索引数据模型、分类策略与静态生成架构的详细设计 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/4087620.htm
- http://m.3g.gqskj.cn/xnews/37316.htm
- http://m.3g.gqskj.cn/xnews/1552034.htm
- http://m.3g.gqskj.cn/xnews/48145.htm
- http://m.3g.gqskj.cn/xnews/89881.htm
- http://m.3g.gqskj.cn/xnews/606544.htm
- http://m.3g.gqskj.cn/xnews/964687.htm
- http://m.3g.gqskj.cn/xnews/14978.htm
- http://m.3g.gqskj.cn/xnews/436275.htm
- http://m.3g.gqskj.cn/xnews/261312.htm
- http://m.3g.gqskj.cn/xnews/646206.htm
- http://m.3g.gqskj.cn/xnews/871330.htm
- http://m.3g.gqskj.cn/xnews/26284.htm
- http://m.3g.gqskj.cn/xnews/926246.htm
- http://m.3g.gqskj.cn/xnews/339533.htm
- http://m.3g.gqskj.cn/xnews/070946.htm
- http://m.3g.gqskj.cn/xnews/0300.htm
- http://m.3g.gqskj.cn/xnews/93391.htm
- http://m.3g.gqskj.cn/xnews/4885.htm
- http://m.3g.gqskj.cn/xnews/17521.htm
- http://m.3g.gqskj.cn/xnews/771821.htm
- http://m.3g.gqskj.cn/xnews/77495.htm
- http://m.3g.gqskj.cn/xnews/30437.htm
- http://m.3g.gqskj.cn/xnews/7466648.htm
- http://m.3g.gqskj.cn/xnews/7684.htm
- http://m.3g.gqskj.cn/xnews/459280.htm
- http://m.3g.gqskj.cn/xnews/41125.htm
- http://m.3g.gqskj.cn/xnews/682245.htm
- http://m.3g.gqskj.cn/xnews/37956.htm
- http://m.3g.gqskj.cn/xnews/000770.htm
- http://m.3g.gqskj.cn/xnews/5240.htm
- http://m.3g.gqskj.cn/xnews/8698455.htm
- http://m.3g.gqskj.cn/xnews/51762.htm
- http://m.3g.gqskj.cn/xnews/90416.htm
- http://m.3g.gqskj.cn/xnews/4359608.htm
- http://m.3g.gqskj.cn/xnews/26329.htm
- http://m.3g.gqskj.cn/xnews/34372.htm
- http://m.3g.gqskj.cn/xnews/7303758.htm
- http://m.3g.gqskj.cn/xnews/36831.htm
- http://m.3g.gqskj.cn/xnews/781078.htm
- http://m.3g.gqskj.cn/xnews/1708850.htm
- http://m.3g.gqskj.cn/xnews/468368.htm
- http://m.3g.gqskj.cn/xnews/549428.htm
- http://m.3g.gqskj.cn/xnews/92604.htm
- http://m.3g.gqskj.cn/xnews/8643525.htm
- http://m.3g.gqskj.cn/xnews/7506.htm
- http://m.3g.gqskj.cn/xnews/0405.htm
- http://m.3g.gqskj.cn/xnews/238690.htm
- http://m.3g.gqskj.cn/xnews/617150.htm
- http://m.3g.gqskj.cn/xnews/42497.htm
- http://m.3g.gqskj.cn/xnews/018982.htm
- http://m.3g.gqskj.cn/xnews/54958.htm
- http://m.3g.gqskj.cn/xnews/915509.htm
- http://m.3g.gqskj.cn/xnews/61768.htm
- http://m.3g.gqskj.cn/xnews/698768.htm
- http://m.3g.gqskj.cn/xnews/556783.htm
- http://m.3g.gqskj.cn/xnews/886797.htm
- http://m.3g.gqskj.cn/xnews/580300.htm
- http://m.3g.gqskj.cn/xnews/9935.htm
- http://m.3g.gqskj.cn/xnews/8732.htm
- http://m.3g.gqskj.cn/xnews/7874.htm
- http://m.3g.gqskj.cn/xnews/8659301.htm
- http://m.3g.gqskj.cn/xnews/2966.htm
- http://m.3g.gqskj.cn/xnews/191647.htm
- http://m.3g.gqskj.cn/xnews/26417.htm
- http://m.3g.gqskj.cn/xnews/3253811.htm
- http://m.3g.gqskj.cn/xnews/14273.htm
- http://m.3g.gqskj.cn/xnews/1904.htm
- http://m.3g.gqskj.cn/xnews/15712.htm
- http://m.3g.gqskj.cn/xnews/24832.htm
- http://m.3g.gqskj.cn/xnews/96008.htm
- http://m.3g.gqskj.cn/xnews/707482.htm
- http://m.3g.gqskj.cn/xnews/7473.htm
- http://m.3g.gqskj.cn/xnews/7050465.htm
- http://m.3g.gqskj.cn/xnews/07066.htm
- http://m.3g.gqskj.cn/xnews/4385398.htm
- http://m.3g.gqskj.cn/xnews/88038.htm
- http://m.3g.gqskj.cn/xnews/7334.htm
- http://m.3g.gqskj.cn/xnews/868533.htm
- http://m.3g.gqskj.cn/xnews/67670.htm
- http://m.3g.gqskj.cn/xnews/6659.htm
- http://m.3g.gqskj.cn/xnews/65554.htm
- http://m.3g.gqskj.cn/xnews/18133.htm
- http://m.3g.gqskj.cn/xnews/51241.htm
- http://m.3g.gqskj.cn/xnews/02359.htm
- http://m.3g.gqskj.cn/xnews/0770.htm
- http://m.3g.gqskj.cn/xnews/2097987.htm
- http://m.3g.gqskj.cn/xnews/862664.htm
- http://m.3g.gqskj.cn/xnews/7094171.htm
- http://m.3g.gqskj.cn/xnews/09278.htm
- http://m.3g.gqskj.cn/xnews/6642590.htm
- http://m.3g.gqskj.cn/xnews/711335.htm
- http://m.3g.gqskj.cn/xnews/37909.htm
- http://m.3g.gqskj.cn/xnews/22740.htm
- http://m.3g.gqskj.cn/xnews/9992181.htm
- http://m.3g.gqskj.cn/xnews/88616.htm
- http://m.3g.gqskj.cn/xnews/791952.htm
- http://m.3g.gqskj.cn/xnews/9817096.htm
- http://m.3g.gqskj.cn/xnews/183194.htm
- http://m.3g.gqskj.cn/xnews/8387381.htm
- http://m.3g.gqskj.cn/xnews/858895.htm
- http://m.3g.gqskj.cn/xnews/1132.htm
- http://m.3g.gqskj.cn/xnews/871629.htm
- http://m.3g.gqskj.cn/xnews/4534821.htm
- http://m.3g.gqskj.cn/xnews/95887.htm
- http://m.3g.gqskj.cn/xnews/554610.htm
- http://m.3g.gqskj.cn/xnews/4171.htm
- http://m.3g.gqskj.cn/xnews/1836617.htm
- http://m.3g.gqskj.cn/xnews/4927793.htm
- http://m.3g.gqskj.cn/xnews/455875.htm
- http://m.3g.gqskj.cn/xnews/46283.htm
- http://m.3g.gqskj.cn/xnews/9662729.htm
- http://m.3g.gqskj.cn/xnews/992330.htm
- http://m.3g.gqskj.cn/xnews/2016663.htm
- http://m.3g.gqskj.cn/xnews/95451.htm
- http://m.3g.gqskj.cn/xnews/7106225.htm
- http://m.3g.gqskj.cn/xnews/7748.htm
- http://m.3g.gqskj.cn/xnews/8184702.htm
- http://m.3g.gqskj.cn/xnews/0779106.htm
- http://m.3g.gqskj.cn/xnews/636403.htm
- http://m.3g.gqskj.cn/xnews/114326.htm
- http://m.3g.gqskj.cn/xnews/7842091.htm
- http://m.3g.gqskj.cn/xnews/3922.htm
- http://m.3g.gqskj.cn/xnews/94762.htm
- http://m.3g.gqskj.cn/xnews/0694.htm
- http://m.3g.gqskj.cn/xnews/0019388.htm
- http://m.3g.gqskj.cn/xnews/8555.htm
- http://m.3g.gqskj.cn/xnews/746358.htm
- http://m.3g.gqskj.cn/xnews/3236.htm
- http://m.3g.gqskj.cn/xnews/795111.htm
- http://m.3g.gqskj.cn/xnews/299271.htm
- http://m.3g.gqskj.cn/xnews/14655.htm
- http://m.3g.gqskj.cn/xnews/57745.htm
- http://m.3g.gqskj.cn/xnews/73401.htm
- http://m.3g.gqskj.cn/xnews/3541.htm
- http://m.3g.gqskj.cn/xnews/95281.htm
- http://m.3g.gqskj.cn/xnews/4628918.htm
- http://m.3g.gqskj.cn/xnews/82931.htm
- http://m.3g.gqskj.cn/xnews/7801.htm
- http://m.3g.gqskj.cn/xnews/57180.htm
- http://m.3g.gqskj.cn/xnews/49350.htm
- http://m.3g.gqskj.cn/xnews/859087.htm
- http://m.3g.gqskj.cn/xnews/92278.htm
- http://m.3g.gqskj.cn/xnews/07557.htm
- http://m.3g.gqskj.cn/xnews/1504986.htm
- http://m.3g.gqskj.cn/xnews/8278034.htm
- http://m.3g.gqskj.cn/xnews/094707.htm
- http://m.3g.gqskj.cn/xnews/2045688.htm
- http://m.3g.gqskj.cn/xnews/1784336.htm
- http://m.3g.gqskj.cn/xnews/3234.htm
- http://m.3g.gqskj.cn/xnews/68623.htm
- http://m.3g.gqskj.cn/xnews/5251851.htm
- http://m.3g.gqskj.cn/xnews/835811.htm
- http://m.3g.gqskj.cn/xnews/830594.htm
- http://m.3g.gqskj.cn/xnews/95750.htm
- http://m.3g.gqskj.cn/xnews/1479982.htm
- http://m.3g.gqskj.cn/xnews/849511.htm
- http://m.3g.gqskj.cn/xnews/3057502.htm
- http://m.3g.gqskj.cn/xnews/7028765.htm
- http://m.3g.gqskj.cn/xnews/57427.htm
- http://m.3g.gqskj.cn/xnews/1420.htm
- http://m.3g.gqskj.cn/xnews/450949.htm
- http://m.3g.gqskj.cn/xnews/5007597.htm
- http://m.3g.gqskj.cn/xnews/3147610.htm
- http://m.3g.gqskj.cn/xnews/7402.htm
- http://m.3g.gqskj.cn/xnews/2237.htm
- http://m.3g.gqskj.cn/xnews/9741187.htm
- http://m.3g.gqskj.cn/xnews/3672.htm
- http://m.3g.gqskj.cn/xnews/13199.htm
- http://m.3g.gqskj.cn/xnews/506350.htm
- http://m.3g.gqskj.cn/xnews/5553.htm
- http://m.3g.gqskj.cn/xnews/359003.htm
- http://m.3g.gqskj.cn/xnews/8483163.htm
- http://m.3g.gqskj.cn/xnews/6081.htm
- http://m.3g.gqskj.cn/xnews/72433.htm
- http://m.3g.gqskj.cn/xnews/79177.htm
- http://m.3g.gqskj.cn/xnews/36185.htm
- http://m.3g.gqskj.cn/xnews/9754099.htm
- http://m.3g.gqskj.cn/xnews/33944.htm
- http://m.3g.gqskj.cn/xnews/96151.htm
- http://m.3g.gqskj.cn/xnews/3506308.htm
- http://m.3g.gqskj.cn/xnews/255253.htm
- http://m.3g.gqskj.cn/xnews/5698698.htm
- http://m.3g.gqskj.cn/xnews/2967998.htm
- http://m.3g.gqskj.cn/xnews/236719.htm
- http://m.3g.gqskj.cn/xnews/49557.htm
- http://m.3g.gqskj.cn/xnews/7760868.htm
- http://m.3g.gqskj.cn/xnews/6795.htm
- http://m.3g.gqskj.cn/xnews/402545.htm
- http://m.3g.gqskj.cn/xnews/3773703.htm
- http://m.3g.gqskj.cn/xnews/15014.htm
- http://m.3g.gqskj.cn/xnews/53823.htm
- http://m.3g.gqskj.cn/xnews/84110.htm
- http://m.3g.gqskj.cn/xnews/0782.htm
- http://m.3g.gqskj.cn/xnews/51577.htm
- http://m.3g.gqskj.cn/xnews/44929.htm
- http://m.3g.gqskj.cn/xnews/9120.htm
- http://m.3g.gqskj.cn/xnews/9300947.htm
- http://m.3g.gqskj.cn/xnews/21531.htm
- http://m.3g.gqskj.cn/xnews/475072.htm
- http://m.3g.gqskj.cn/xnews/05339.htm
- http://m.3g.gqskj.cn/xnews/5385785.htm
- http://m.3g.gqskj.cn/xnews/4320.htm
- http://m.3g.gqskj.cn/xnews/696318.htm
- http://m.3g.gqskj.cn/xnews/4021177.htm
- http://m.3g.gqskj.cn/xnews/055897.htm
- http://m.3g.gqskj.cn/xnews/67108.htm
- http://m.3g.gqskj.cn/xnews/4606172.htm
- http://m.3g.gqskj.cn/xnews/301421.htm
- http://m.3g.gqskj.cn/xnews/4561970.htm
- http://m.3g.gqskj.cn/xnews/516543.htm
- http://m.3g.gqskj.cn/xnews/214535.htm
- http://m.3g.gqskj.cn/xnews/0138.htm
- http://m.3g.gqskj.cn/xnews/9253328.htm
- http://m.3g.gqskj.cn/xnews/2050.htm
- http://m.3g.gqskj.cn/xnews/28325.htm
- http://m.3g.gqskj.cn/xnews/63521.htm
- http://m.3g.gqskj.cn/xnews/1141093.htm
- http://m.3g.gqskj.cn/xnews/7298924.htm
- http://m.3g.gqskj.cn/xnews/486072.htm
- http://m.3g.gqskj.cn/xnews/9553286.htm
- http://m.3g.gqskj.cn/xnews/13447.htm
- http://m.3g.gqskj.cn/xnews/57269.htm
- http://m.3g.gqskj.cn/xnews/030213.htm
- http://m.3g.gqskj.cn/xnews/703790.htm
- http://m.3g.gqskj.cn/xnews/63745.htm
- http://m.3g.gqskj.cn/xnews/8664984.htm
- http://m.3g.gqskj.cn/xnews/0009.htm
- http://m.3g.gqskj.cn/xnews/38336.htm
- http://m.3g.gqskj.cn/xnews/214522.htm
- http://m.3g.gqskj.cn/xnews/3930.htm
- http://m.3g.gqskj.cn/xnews/69865.htm
- http://m.3g.gqskj.cn/xnews/3898305.htm
- http://m.3g.gqskj.cn/xnews/38553.htm
- http://m.3g.gqskj.cn/xnews/24118.htm
- http://m.3g.gqskj.cn/xnews/2544032.htm
- http://m.3g.gqskj.cn/xnews/110792.htm
- http://m.3g.gqskj.cn/xnews/9396079.htm
- http://m.3g.gqskj.cn/xnews/1025.htm
- http://m.3g.gqskj.cn/xnews/4268.htm
- http://m.3g.gqskj.cn/xnews/699322.htm
- http://m.3g.gqskj.cn/xnews/7919431.htm
- http://m.3g.gqskj.cn/xnews/80114.htm
- http://m.3g.gqskj.cn/xnews/31199.htm
- http://m.3g.gqskj.cn/xnews/9795908.htm
- http://m.3g.gqskj.cn/xnews/53138.htm
- http://m.3g.gqskj.cn/xnews/4905023.htm
- http://m.3g.gqskj.cn/xnews/5687.htm
- http://m.3g.gqskj.cn/xnews/728381.htm
- http://m.3g.gqskj.cn/xnews/32032.htm

## 项目结构

```
xnews-link-index/
├── build_index.py          # 主构建脚本，负责读取链接列表并生成索引页面
├── config.yaml              # 运行时配置文件，包含输出路径、分类规则与模板参数
├── requirements.txt         # Python 依赖声明文件
├── pyproject.toml           # 项目元数据与构建工具配置
├── data/                    # 数据目录，存放批次链接文件
│   ├── links_150.txt        # 第 150 批次原始链接列表，共 250 条
│   ├── links_149.txt        # 上一批次链接列表，用于变更对比
│   └── manifest.json        # 所有批次的索引清单，记录导入时间与条目数
├── src/                     # 源代码主目录
│   ├── parser.py            # 链接解析模块，处理 URL 校验与分类推断
│   ├── generator.py         # 静态页面生成器，渲染 HTML 与 JSON 输出
│   ├── exporter.py          # 多格式导出模块，支持 CSV、JSONL 与 Markdown
│   ├── health.py            # 链接可达性检测脚本，支持并发请求
│   └── utils.py             # 通用工具函数，包括日期处理与文件操作
├── templates/               # 模板目录，存放 Jinja2 模板文件
│   ├── index.html.j2        # 主索引页模板，包含分类导航与链接表格
│   └── detail.html.j2       # 单条链接详情模板，预留扩展
├── tests/                   # 测试目录
│   ├── test_parser.py       # 解析器单元测试
│   ├── test_generator.py    # 生成器单元测试
│   └── fixtures/            # 测试固定数据
│       └── sample_links.txt # 示例链接文件
├── dist/                    # 构建输出目录，存放生成的静态页面与数据文件
│   ├── index.html           # 默认生成的索引页面
│   └── index.json           # 默认生成的 JSON 元数据
├── docs/                    # 文档目录，包含用户手册与设计说明
│   ├── usage.md             # 使用手册
│   ├── configuration.md     # 配置参考
│   ├── development.md       # 开发指南
│   └── design.md            # 设计说明
├── .pre-commit-config.yaml  # pre-commit 钩子配置，用于代码提交前自动检查
└── LICENSE                  # MIT 许可证文件
```

## 贡献指南

1. **报告问题**：请在 GitHub Issues 中提交问题报告，描述问题现象、复现步骤与预期行为，并附上相关日志或截图。对于链接失效或分类错误，请提供具体条目标识。

2. **提交链接批次**：如需新增链接批次，请将链接列表按纯文本格式存放于 `data/` 目录下，文件名遵循 `links_<批次号>.txt` 规范，并更新 `data/manifest.json` 中的批次记录。提交前请运行去重检测与格式校验。

3. **代码改进**：Fork 本项目后，在本地开发分支上进行修改。代码风格需符合 Black 格式化规范，所有新增功能需附带单元测试，测试覆盖率不低于百分之八十。提交前运行 pre-commit 钩子进行自动检查。

4. **文档更新**：对于功能变更或新增配置项，请同步更新 `docs/` 目录下的对应文档。用户手册需包含使用示例与命令行参数说明，设计说明需阐述变更对现有架构的影响。

5. **Pull Request 流程**：向主仓库的 `main` 分支提交 Pull Request，描述变更内容、关联的 Issue 编号以及测试结果。PR 需要至少一名项目维护者审核通过后方可合并。

## 常见问题

**Q：如何检测索引中的链接是否仍然有效？**

A：项目提供了健康检查脚本 `src/health.py`，可通过以下命令运行：

```bash
python src/health.py --input data/links_150.txt --output health_report.json --timeout 5 --concurrency 10
```

该脚本发送 HTTP HEAD 请求，将无法访问的链接记录到报告中。建议定期执行并清理失效条目。

**Q：导入链接后生成的分类标签不符合预期，如何调整？**

A：分类逻辑位于 `src/parser.py` 中的 `infer_category` 函数。您可以根据域名特征或路径关键字修改分类规则。若希望完全自定义，可在输入文件中为每条链接追加分类标记，格式为 `URL,分类名称`，构建脚本将优先使用该标记。

**Q：构建出的静态页面样式如何修改？**

A：模板文件位于 `templates/` 目录，使用 Jinja2 模板引擎。您可以直接编辑 `index.html.j2` 中的 HTML 结构与 CSS 样式，或替换为自定义模板文件，并在 `config.yaml` 中指定模板路径。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:49
