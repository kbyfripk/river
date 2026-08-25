# WebIndex 聚合导航系统

WebIndex 是一个面向技术研究、数据归档与信息安全分析领域的轻量级外链资源聚合与导航系统。该项目定位于为安全研究员、威胁情报分析师、渗透测试工程师以及数据采集开发者提供结构化的历史页面索引与快捷访问能力。WebIndex 并不直接托管内容，而是通过可维护的索引机制对分散在互联网各处的信息页面进行编目与引用，帮助用户在复杂网络环境中快速定位特定页面片段。

项目采用纯静态架构，基于 Markdown 与 YAML 前端元数据驱动，支持一键生成全量站点地图与分类索引视图。用户可通过本地命令行工具完成链接入库、标签标注、过期检测与 HTML 快照归档提示，从而构建私有或团队共享的外链知识库。WebIndex 适用于需要长期跟踪特定域名路径变化、批量整理历史资料或建立轻量级漏洞验证页面备忘录的场景，其设计兼顾了极低运维成本与高度可扩展性。

## 功能概览

- 批量链接导入与去重 支持通过文本文件或标准输入流批量添加链接，自动识别重复条目并基于响应头状态码进行存活校验。

- 标签分类与全文检索 每个索引条目可绑定多个层级标签，内置基于倒排索引的轻量级检索引擎，支持标题与 URL 关键词模糊匹配。

- 定时健康检查 可配置周期性 HEAD 请求任务，标记异常链接并生成可用性报表，输出格式支持 JSON 与 CSV。

- 静态站点生成器 内置模板引擎将索引数据渲染为响应式 HTML 导航页，支持暗色主题与移动端适配，输出纯静态文件便于部署至 CDN 或对象存储。

- 元数据扩展字段 支持为每个链接自定义键值对元数据，包括但不限于发现日期、归档批次、关联漏洞编号或内部备注，便于团队协作。

- 导入导出兼容性 数据存储采用 JSON 与 YAML 双格式，兼容主流数据处理工具，支持导出为 Markdown 表格或结构化日志格式。

- 命令行交互界面 提供完整的 CLI 工具链，涵盖增删改查、标签管理、快照生成与配置初始化，所有操作均支持非交互模式与脚本调用。

- 访问控制白名单 支持配置域名与 IP 段白名单，限制索引范围仅包含可信来源，降低意外引用恶意域名的风险。

## 应用场景

- 威胁情报历史页面归档 安全团队使用 WebIndex 跟踪特定 IP 或域名下的历史页面变更，通过定期拉取与快照对比，发现恶意内容投放或钓鱼页面迁移痕迹。每条链接可关联发现时间与响应摘要，为溯源分析提供结构化数据支撑。

- 渗透测试备忘录管理 测试人员利用 WebIndex 整理漏洞验证页面（如 POC 演示链接、公开漏洞报告），按 CVE 编号或资产分类，支持快速检索与状态标记，提升复测与报告编写效率。

- 数据采集任务导航 数据工程师将分散在不同子域名下的数据接口或公开数据页面统一收录至 WebIndex，结合标签与元数据字段进行批次管理，避免采集任务遗漏关键页面或重复抓取已失效链接。

- 开源情报信息汇聚 研究人员对特定行业或地区的公开信息页面进行长期跟踪，通过 WebIndex 建立分类导航目录，定期导出健康状态报表，辅助判断信息来源的持续可用性与更新频率。

## 快速开始

以下命令演示了从代码仓库克隆、安装依赖并启动本地开发服务的完整流程。

```bash
git clone https://github.com/webindex/webindex-core.git
cd webindex-core
pip install -r requirements.txt
python setup.py install
webindex init --project my_index
cd my_index
webindex add --batch urls.txt
webindex build --output ./public
webindex serve --port 8080
```

执行上述命令后，本地服务将在 8080 端口启动。访问 http://localhost:8080 即可查看生成的导航站点首页。若需自定义主题或调整索引规则，请修改项目目录下的 config.yaml 文件与 templates 子目录中的模板内容。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS 版本以获得最佳兼容性 |
| pip | 21.0 及以上 | 用于安装项目依赖包及命令行工具 |
| Git | 2.25 及以上 | 用于克隆仓库及版本管理，Windows 用户需确保 Git Bash 可用 |
| curl | 7.68 及以上 | 健康检查模块依赖的外部请求工具，用于发送 HEAD 与 GET 请求 |
| make | 3.82 及以上 | 可选组件，用于自动化任务执行，Linux 与 macOS 默认安装 |
| pyyaml | 5.4.1 | 解析 YAML 格式的配置文件与元数据，核心依赖 |
| jinja2 | 3.0.0 | 模板渲染引擎，用于生成 HTML 静态页面 |
| click | 8.0.0 | 命令行交互框架，提供子命令解析与参数校验 |
| requests | 2.25.0 | 备用 HTTP 请求库，当 curl 不可用时自动降级使用 |
| pytest | 7.0.0 | 仅开发与测试环境需要，用于执行单元测试与集成测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何初始化索引库、添加链接、生成站点以及配置健康检查策略 |
| 开发指南 | /docs/developer-guide.md | 如何扩展自定义解析器、新增元数据字段或修改渲染模板逻辑 |
| API 参考 | /docs/api-reference.md | 各核心模块（索引器、检查器、生成器）的类与方法签名说明 |
| 运维手册 | /docs/operations.md | 如何部署至生产环境、配置 Nginx 反向代理以及设置定时任务 |

## 资源列表

- http://m.3g.fcful.cn/snews/0724.htm
- http://m.3g.fcful.cn/snews/02918.htm
- http://m.3g.fcful.cn/snews/14780.htm
- http://m.3g.fcful.cn/snews/02471.htm
- http://m.3g.fcful.cn/snews/1758.htm
- http://m.3g.fcful.cn/snews/4260494.htm
- http://m.3g.fcful.cn/snews/931417.htm
- http://m.3g.fcful.cn/snews/87784.htm
- http://m.3g.fcful.cn/snews/48141.htm
- http://m.3g.fcful.cn/snews/16011.htm
- http://m.3g.fcful.cn/snews/0623.htm
- http://m.3g.fcful.cn/snews/0370.htm
- http://m.3g.fcful.cn/snews/42938.htm
- http://m.3g.fcful.cn/snews/242454.htm
- http://m.3g.fcful.cn/snews/37196.htm
- http://m.3g.fcful.cn/snews/7570798.htm
- http://m.3g.fcful.cn/snews/053224.htm
- http://m.3g.fcful.cn/snews/49645.htm
- http://m.3g.fcful.cn/snews/831016.htm
- http://m.3g.fcful.cn/snews/8468480.htm
- http://m.3g.fcful.cn/snews/1879.htm
- http://m.3g.fcful.cn/snews/409136.htm
- http://m.3g.fcful.cn/snews/1220392.htm
- http://m.3g.fcful.cn/snews/8495264.htm
- http://m.3g.fcful.cn/snews/540069.htm
- http://m.3g.fcful.cn/snews/6797217.htm
- http://m.3g.fcful.cn/snews/4219.htm
- http://m.3g.fcful.cn/snews/8285790.htm
- http://m.3g.fcful.cn/snews/44556.htm
- http://m.3g.fcful.cn/snews/5423252.htm
- http://m.3g.fcful.cn/snews/1663.htm
- http://m.3g.fcful.cn/snews/6356124.htm
- http://m.3g.fcful.cn/snews/1735.htm
- http://m.3g.fcful.cn/snews/792613.htm
- http://m.3g.fcful.cn/snews/79244.htm
- http://m.3g.fcful.cn/snews/1256122.htm
- http://m.3g.fcful.cn/snews/5095801.htm
- http://m.3g.fcful.cn/snews/5164.htm
- http://m.3g.fcful.cn/snews/842509.htm
- http://m.3g.fcful.cn/snews/10491.htm
- http://m.3g.fcful.cn/snews/8143.htm
- http://m.3g.fcful.cn/snews/3774.htm
- http://m.3g.fcful.cn/snews/4280853.htm
- http://m.3g.fcful.cn/snews/78093.htm
- http://m.3g.fcful.cn/snews/471424.htm
- http://m.3g.fcful.cn/snews/308161.htm
- http://m.3g.fcful.cn/snews/496318.htm
- http://m.3g.fcful.cn/snews/75591.htm
- http://m.3g.fcful.cn/snews/28658.htm
- http://m.3g.fcful.cn/snews/04204.htm
- http://m.3g.fcful.cn/snews/65785.htm
- http://m.3g.fcful.cn/snews/176453.htm
- http://m.3g.fcful.cn/snews/1988777.htm
- http://m.3g.fcful.cn/snews/4140.htm
- http://m.3g.fcful.cn/snews/6918.htm
- http://m.3g.fcful.cn/snews/38751.htm
- http://m.3g.fcful.cn/snews/0865476.htm
- http://m.3g.fcful.cn/snews/2277.htm
- http://m.3g.fcful.cn/snews/966702.htm
- http://m.3g.fcful.cn/snews/231627.htm
- http://m.3g.fcful.cn/snews/0969072.htm
- http://m.3g.fcful.cn/snews/1726.htm
- http://m.3g.fcful.cn/snews/74070.htm
- http://m.3g.fcful.cn/snews/939880.htm
- http://m.3g.fcful.cn/snews/82066.htm
- http://m.3g.fcful.cn/snews/113865.htm
- http://m.3g.fcful.cn/snews/01112.htm
- http://m.3g.fcful.cn/snews/984020.htm
- http://m.3g.fcful.cn/snews/068149.htm
- http://m.3g.fcful.cn/snews/041860.htm
- http://m.3g.fcful.cn/snews/6947101.htm
- http://m.3g.fcful.cn/snews/0660.htm
- http://m.3g.fcful.cn/snews/29770.htm
- http://m.3g.fcful.cn/snews/3025359.htm
- http://m.3g.fcful.cn/snews/606845.htm
- http://m.3g.fcful.cn/snews/3578983.htm
- http://m.3g.fcful.cn/snews/4747715.htm
- http://m.3g.fcful.cn/snews/143262.htm
- http://m.3g.fcful.cn/snews/1064133.htm
- http://m.3g.fcful.cn/snews/0070084.htm
- http://m.3g.fcful.cn/snews/6217461.htm
- http://m.3g.fcful.cn/snews/1132.htm
- http://m.3g.fcful.cn/snews/53025.htm
- http://m.3g.fcful.cn/snews/8733.htm
- http://m.3g.fcful.cn/snews/24804.htm
- http://m.3g.fcful.cn/snews/2423.htm
- http://m.3g.fcful.cn/snews/5411183.htm
- http://m.3g.fcful.cn/snews/8312.htm
- http://m.3g.fcful.cn/snews/540080.htm
- http://m.3g.fcful.cn/snews/665561.htm
- http://m.3g.fcful.cn/snews/0685.htm
- http://m.3g.fcful.cn/snews/6023746.htm
- http://m.3g.fcful.cn/snews/367396.htm
- http://m.3g.fcful.cn/snews/06424.htm
- http://m.3g.fcful.cn/snews/771760.htm
- http://m.3g.fcful.cn/snews/6948.htm
- http://m.3g.fcful.cn/snews/946049.htm
- http://m.3g.fcful.cn/snews/76426.htm
- http://m.3g.fcful.cn/snews/57583.htm
- http://m.3g.fcful.cn/snews/01002.htm
- http://m.3g.fcful.cn/snews/80325.htm
- http://m.3g.fcful.cn/snews/97291.htm
- http://m.3g.fcful.cn/snews/85008.htm
- http://m.3g.fcful.cn/snews/1037253.htm
- http://m.3g.fcful.cn/snews/4620871.htm
- http://m.3g.fcful.cn/snews/285141.htm
- http://m.3g.fcful.cn/snews/6629.htm
- http://m.3g.fcful.cn/snews/75465.htm
- http://m.3g.fcful.cn/snews/6263.htm
- http://m.3g.fcful.cn/snews/645296.htm
- http://m.3g.fcful.cn/snews/3170.htm
- http://m.3g.fcful.cn/snews/4679.htm
- http://m.3g.fcful.cn/snews/943780.htm
- http://m.3g.fcful.cn/snews/7437.htm
- http://m.3g.fcful.cn/snews/971562.htm
- http://m.3g.fcful.cn/snews/6625.htm
- http://m.3g.fcful.cn/snews/01272.htm
- http://m.3g.fcful.cn/snews/6207.htm
- http://m.3g.fcful.cn/snews/9608151.htm
- http://m.3g.fcful.cn/snews/33111.htm
- http://m.3g.fcful.cn/snews/3986.htm
- http://m.3g.fcful.cn/snews/8729316.htm
- http://m.3g.fcful.cn/snews/1484475.htm
- http://m.3g.fcful.cn/snews/8421791.htm
- http://m.3g.fcful.cn/snews/2294087.htm
- http://m.3g.fcful.cn/snews/09943.htm
- http://m.3g.fcful.cn/snews/32965.htm
- http://m.3g.fcful.cn/snews/69641.htm
- http://m.3g.fcful.cn/snews/884007.htm
- http://m.3g.fcful.cn/snews/8017551.htm
- http://m.3g.fcful.cn/snews/6844390.htm
- http://m.3g.fcful.cn/snews/6708.htm
- http://m.3g.fcful.cn/snews/98584.htm
- http://m.3g.fcful.cn/snews/212733.htm
- http://m.3g.fcful.cn/snews/4962.htm
- http://m.3g.fcful.cn/snews/5126.htm
- http://m.3g.fcful.cn/snews/2276647.htm
- http://m.3g.fcful.cn/snews/85961.htm
- http://m.3g.fcful.cn/snews/58664.htm
- http://m.3g.fcful.cn/snews/310384.htm
- http://m.3g.fcful.cn/snews/2465.htm
- http://m.3g.fcful.cn/snews/305383.htm
- http://m.3g.fcful.cn/snews/19309.htm
- http://m.3g.fcful.cn/snews/5536.htm
- http://m.3g.fcful.cn/snews/9140.htm
- http://m.3g.fcful.cn/snews/573938.htm
- http://m.3g.fcful.cn/snews/76265.htm
- http://m.3g.fcful.cn/snews/0309.htm
- http://m.3g.fcful.cn/snews/9532165.htm
- http://m.3g.fcful.cn/snews/1640264.htm
- http://m.3g.fcful.cn/snews/257569.htm
- http://m.3g.fcful.cn/snews/343121.htm
- http://m.3g.fcful.cn/snews/37249.htm
- http://m.3g.fcful.cn/snews/059999.htm
- http://m.3g.fcful.cn/snews/0029778.htm
- http://m.3g.fcful.cn/snews/9805.htm
- http://m.3g.fcful.cn/snews/3664.htm
- http://m.3g.fcful.cn/snews/2389.htm
- http://m.3g.fcful.cn/snews/38520.htm
- http://m.3g.fcful.cn/snews/96366.htm
- http://m.3g.fcful.cn/snews/0743103.htm
- http://m.3g.fcful.cn/snews/917277.htm
- http://m.3g.fcful.cn/snews/0560110.htm
- http://m.3g.fcful.cn/snews/232244.htm
- http://m.3g.fcful.cn/snews/89193.htm
- http://m.3g.fcful.cn/snews/8827293.htm
- http://m.3g.fcful.cn/snews/668145.htm
- http://m.3g.fcful.cn/snews/9915341.htm
- http://m.3g.fcful.cn/snews/626887.htm
- http://m.3g.fcful.cn/snews/4547.htm
- http://m.3g.fcful.cn/snews/6843.htm
- http://m.3g.fcful.cn/snews/922123.htm
- http://m.3g.fcful.cn/snews/599189.htm
- http://m.3g.fcful.cn/snews/126988.htm
- http://m.3g.fcful.cn/snews/85023.htm
- http://m.3g.fcful.cn/snews/84485.htm
- http://m.3g.fcful.cn/snews/8104.htm
- http://m.3g.fcful.cn/snews/04124.htm
- http://m.3g.fcful.cn/snews/054828.htm
- http://m.3g.fcful.cn/snews/9575.htm
- http://m.3g.fcful.cn/snews/2306.htm
- http://m.3g.fcful.cn/snews/69695.htm
- http://m.3g.fcful.cn/snews/9580953.htm
- http://m.3g.fcful.cn/snews/055098.htm
- http://m.3g.fcful.cn/snews/866258.htm
- http://m.3g.fcful.cn/snews/3375.htm
- http://m.3g.fcful.cn/snews/36122.htm
- http://m.3g.fcful.cn/snews/0304.htm
- http://m.3g.fcful.cn/snews/3540021.htm
- http://m.3g.fcful.cn/snews/22496.htm
- http://m.3g.fcful.cn/snews/0784026.htm
- http://m.3g.fcful.cn/snews/2303.htm
- http://m.3g.fcful.cn/snews/74742.htm
- http://m.3g.fcful.cn/snews/580109.htm
- http://m.3g.fcful.cn/snews/5549854.htm
- http://m.3g.fcful.cn/snews/310343.htm
- http://m.3g.fcful.cn/snews/333907.htm
- http://m.3g.fcful.cn/snews/1414182.htm
- http://m.3g.fcful.cn/snews/12525.htm
- http://m.3g.fcful.cn/snews/626292.htm
- http://m.3g.fcful.cn/snews/7656555.htm
- http://m.3g.fcful.cn/snews/6098.htm
- http://m.3g.fcful.cn/snews/2799.htm
- http://m.3g.fcful.cn/snews/391474.htm
- http://m.3g.fcful.cn/snews/20428.htm
- http://m.3g.fcful.cn/snews/01944.htm
- http://m.3g.fcful.cn/snews/183590.htm
- http://m.3g.fcful.cn/snews/05430.htm
- http://m.3g.fcful.cn/snews/312402.htm
- http://m.3g.fcful.cn/snews/8326.htm
- http://m.3g.fcful.cn/snews/538217.htm
- http://m.3g.fcful.cn/snews/7414972.htm
- http://m.3g.fcful.cn/snews/35721.htm
- http://m.3g.fcful.cn/snews/8935484.htm
- http://m.3g.fcful.cn/snews/5417.htm
- http://m.3g.fcful.cn/snews/7466041.htm
- http://m.3g.fcful.cn/snews/611750.htm
- http://m.3g.fcful.cn/snews/2472.htm
- http://m.3g.fcful.cn/snews/8290851.htm
- http://m.3g.fcful.cn/snews/785334.htm
- http://m.3g.fcful.cn/snews/6956570.htm
- http://m.3g.fcful.cn/snews/5415.htm
- http://m.3g.fcful.cn/snews/9153595.htm
- http://m.3g.fcful.cn/snews/24785.htm
- http://m.3g.fcful.cn/snews/723652.htm
- http://m.3g.fcful.cn/snews/431630.htm
- http://m.3g.fcful.cn/snews/62451.htm
- http://m.3g.fcful.cn/snews/53265.htm
- http://m.3g.fcful.cn/snews/6083.htm
- http://m.3g.fcful.cn/snews/684486.htm
- http://m.3g.fcful.cn/snews/6398.htm
- http://m.3g.fcful.cn/snews/62741.htm
- http://m.3g.fcful.cn/snews/333862.htm
- http://m.3g.fcful.cn/snews/9683.htm
- http://m.3g.fcful.cn/snews/6049386.htm
- http://m.3g.fcful.cn/snews/179722.htm
- http://m.3g.fcful.cn/snews/6559.htm
- http://m.3g.fcful.cn/snews/7938.htm
- http://m.3g.fcful.cn/snews/76031.htm
- http://m.3g.fcful.cn/snews/62172.htm
- http://m.3g.fcful.cn/snews/97284.htm
- http://m.3g.fcful.cn/snews/2322.htm
- http://m.3g.fcful.cn/snews/968768.htm
- http://m.3g.fcful.cn/snews/09442.htm
- http://m.3g.fcful.cn/snews/5634.htm
- http://m.3g.fcful.cn/snews/8662.htm
- http://m.3g.fcful.cn/snews/0435970.htm
- http://m.3g.fcful.cn/snews/43050.htm
- http://m.3g.fcful.cn/snews/75693.htm
- http://m.3g.fcful.cn/snews/858545.htm

## 项目结构

```
webindex-core/
├── src/                                 # 核心源代码目录
│   ├── cli/                            # 命令行接口模块，包含子命令解析与路由
│   │   ├── add.py                     # 实现链接添加与去重逻辑
│   │   ├── build.py                   # 静态站点生成与模板渲染入口
│   │   └── health.py                  # 健康检查调度器与状态报告生成
│   ├── core/                           # 核心数据模型与索引引擎
│   │   ├── index.py                   # 倒排索引构建与检索实现
│   │   ├── models.py                  # 链接条目、标签、元数据的数据类定义
│   │   └── storage.py                 # JSON/YAML 读写与版本迁移工具
│   ├── parser/                         # 链接解析与规范化子模块
│   │   ├── url_normalizer.py          # URL 去重键生成与协议补全判断
│   │   └── metadata_extractor.py      # 从响应头或页面片段提取自动标注信息
│   └── renderer/                       # 渲染引擎，负责输出 HTML 与报表
│       ├── templates/                  # Jinja2 模板目录，含首页、分类页、详情页
│       ├── static/                     # CSS、JavaScript 与字体资源
│       └── site_generator.py           # 递归构建全站静态页面的主控流程
├── tests/                              # 单元测试与集成测试目录
│   ├── test_cli/                       # 对应 cli 模块的测试用例
│   ├── test_core/                      # 核心索引与存储的边界测试
│   └── fixtures/                       # 测试用的示例数据与模拟响应体
├── docs/                               # 项目文档源文件，采用 Markdown 编写
│   ├── user-guide.md                   # 用户手册，涵盖日常操作流程
│   ├── developer-guide.md              # 开发指南，说明扩展点与编码规范
│   └── operations.md                   # 运维部署与监控配置指南
├── scripts/                            # 辅助脚本与自动化任务
│   ├── daily_health_check.sh          # 定时健康检查的 cron 包装脚本
│   └── import_batch.sh                # 批量导入外部数据源的转换工具
├── config.yaml                         # 主配置文件，包含白名单、标签别名与输出路径
├── requirements.txt                    # Python 依赖清单，锁定主版本号
├── setup.py                            # 安装脚本，声明入口点与控制台命令
├── Makefile                            # 常用任务快捷命令，如 test、clean、build
└── README.md                           # 项目概述与快速入门（即本文档）
```

## 贡献指南

1. 查阅 Issue 列表与项目看板，确认当前优先级最高的待办事项，避免重复工作。新功能建议先创建讨论议题，与维护者沟通设计思路后再投入开发。

2. 克隆代码仓库并创建特性分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。开发环境推荐使用 Python 虚拟环境，并通过 `pip install -e .` 安装可编辑模式的本包。

3. 编写代码时请遵守 PEP 8 编码规范，并为新增函数或类添加完整的 docstring 与类型注解。所有对外接口的变更需同步更新对应的文档页面。

4. 提交前执行 `make test` 确保所有现有测试用例通过，并为新增功能补充对应的单元测试。若涉及命令行接口变更，需更新 `tests/test_cli` 下的交互模拟用例。

5. 发起 Pull Request 至主分支，描述中需注明关联议题编号、变更范围与测试结果。维护者将在 48 小时内进行审查，并提出修改意见。

## 常见问题

Q: 添加链接时提示去重命中，但我确认这是新的页面，如何强制加入？

A: 系统默认基于 URL 的规范化形式（移除末尾斜杠、统一协议为小写）生成去重键。若确认需要强制加入，可修改 config.yaml 中的 dedup_strict 为 false，或使用 `webindex add --force` 选项跳过去重检查。请注意强制加入可能导致同一 URL 的多个条目共存，影响检索准确性。

Q: 健康检查模块显示大量链接超时，但浏览器中访问正常，是什么原因？

A: 健康检查默认使用 HEAD 请求并设置 5 秒超时。部分服务器对 HEAD 请求响应较慢或直接拒绝，可修改 config.yaml 中的 health_check_method 为 GET，并调整 timeout 参数至 10 秒以上。同时检查网络环境是否对出口 IP 有访问限制。

Q: 生成的静态站点首页分类不完整，部分标签未显示，如何解决？

A: 请检查 config.yaml 中的 display_tags 白名单配置，未列入白名单的标签不会出现在首页分类导航中。若希望显示所有标签，可将 display_tags 设为空列表或注释该字段。此外，确保标签对应的链接条目状态为 active，已标记为 expired 或 archived 的条目默认不在首页聚合统计中显示。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
