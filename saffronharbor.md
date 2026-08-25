# LinkVault 结构化外链资源聚合系统

LinkVault 是一个面向技术内容聚合场景的轻量化外链管理与导航系统，专为需要快速收录、分类、检索大量分散 URL 资源的开发团队、内容运营者和个人知识库维护者设计。该项目本质上是一个结构化的 URL 资源索引层，将原本散落在各类源中的链接以统一 schema 进行重组，辅以基础元数据标记和分类视图，从而显著提升大规模外链集合的可维护性与可读性。目标用户包括技术文档编写者、开源项目维护者、数据采集工程师以及需要定期整理阅读清单或参考来源的研究人员。LinkVault 不提供爬虫或自动化采集能力，而是聚焦于人工 curated 链路的组织与呈现，确保每一条资源均可被准确追踪与回溯。

## 功能概览

**多级分类标签系统**：支持为每条 URL 分配所属领域、来源站点、内容类型等多维度标签，便于后续按主题筛选和批量操作。

**原始 URL 完整留存机制**：系统强制保留每条链接的完整原始地址字符串，包括协议前缀、域名层级、路径参数和文件扩展名，杜绝任何形式的自动补全或规范化改写，确保引用准确性。

**批次化导入与版本追踪**：以批次为单位导入 URL 集合，每批次包含批次编号、总条目数、导入时间戳和自定义备注，支持按批次回滚或导出。

**Markdown 原生渲染输出**：所有资源列表以纯 Markdown 无序列表形式呈现，每行严格容纳一条 URL，不嵌入任何 HTML 标签或链接语法，保证与各类静态站点生成器和文档平台的最大兼容性。

**依赖与环境自检报告**：启动时自动检测运行环境中的必需依赖版本，输出兼容性表格，提示缺失或过旧的组件，减少因环境不一致导致的运行时错误。

**轻量级本地 Web 预览服务**：内置基于 Python HTTP 服务器的预览模式，允许用户在本地启动一个只读站点，实时查看资源列表的渲染效果，方便校对和审阅。

**结构化元数据扩展接口**：提供 JSON Schema 定义的可扩展元数据字段，允许用户为每条链接追加备注、优先级、阅读状态或自定义键值对，满足个性化管理需求。

## 应用场景

技术文档团队整理外部参考链接。当编写一份涉及多个第三方库、规范文档和社区讨论的技术方案时，团队成员可使用 LinkVault 统一收录所有引用链接，并按章节或主题打标，确保最终文档中的超链接列表整齐有序且可追溯，避免出现断链或重复引用。

开源项目维护 README 中的外部资源节。开源项目的 README 通常需要列举大量依赖项目、学习资料或相关工具。维护者可将所有外链导入 LinkVault，按功能分类后批量生成符合规范的 Markdown 列表，直接嵌入 README 的指定章节，大幅减少手动排版出错率。

个人知识库的阅读清单管理。研究员或工程师在阅读技术博客、论文或新闻时，可将感兴趣的文章链接统一存入 LinkVault，利用批次字段按周或按月归档，配合元数据标记阅读进度和重要程度，形成长期可检索的个人知识索引。

数据采集链路的源头记录。在进行数据采集或 API 调用时，工程师常需记录数据来源地址。LinkVault 可作为来源管理模块，记录每个数据源的完整 URL 及其采集时间、状态备注，方便后续审计和数据溯源。

## 快速开始

以下指令适用于 Linux / macOS / Windows WSL 环境，确保已安装 Python 3.8 及以上版本和 Git。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkvault.git
cd linkvault

# 安装 Python 依赖（使用 venv 推荐）
python3 -m venv .venv
source .venv/bin/activate  # Windows 下使用 .venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt

# 初始化本地资源数据库（生成示例数据）
python scripts/init_db.py --sample

# 启动本地预览服务（默认端口 8080）
python app.py --port 8080

# 访问预览页面
# 浏览器打开 http://localhost:8080
```

生产环境部署建议使用 gunicorn 或 uWSGI 作为 WSGI 服务器，并在前端配置 Nginx 反向代理。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 - 3.11 | 核心运行环境，3.12 及以上暂未全面测试 |
| pip | 22.0 及以上 | Python 包管理器，用于安装依赖库 |
| Git | 2.30 及以上 | 用于克隆仓库和版本管理 |
| Markdown | 3.4.0 及以上 | 用于解析和渲染 Markdown 内容 |
| PyYAML | 6.0 及以上 | 用于读取和写入配置文件（YAML 格式） |
| Flask | 2.2.0 - 2.3.x | 可选依赖，仅本地预览服务需要 |
| pytest | 7.0 及以上 | 开发测试依赖，生产环境可不安装 |
| black | 23.0 及以上 | 代码格式化工具，仅开发阶段使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门 | docs/quickstart.md | 如何最快上手使用 LinkVault 导入第一批资源？ |
| 配置 | docs/configuration.md | 如何调整标签体系、元数据模板和预览服务端口？ |
| 数据管理 | docs/data-management.md | 如何导入、导出、备份和批量更新已有资源条目？ |
| 集成 | docs/integration.md | 如何将 LinkVault 生成的 Markdown 列表嵌入现有文档或 CI 流程？ |
| 架构 | docs/architecture.md | 系统的模块划分、数据流向和扩展接口设计是怎样的？ |

## 资源列表

- http://m.wap.gqskj.cn/snews/194522.htm
- http://m.wap.gqskj.cn/snews/9538.htm
- http://m.wap.gqskj.cn/snews/133843.htm
- http://m.wap.gqskj.cn/snews/4899793.htm
- http://m.wap.gqskj.cn/snews/850602.htm
- http://m.wap.gqskj.cn/snews/3077902.htm
- http://m.wap.gqskj.cn/snews/4445934.htm
- http://m.wap.gqskj.cn/snews/7736040.htm
- http://m.wap.gqskj.cn/snews/31618.htm
- http://m.wap.gqskj.cn/snews/6222.htm
- http://m.wap.gqskj.cn/snews/21581.htm
- http://m.wap.gqskj.cn/snews/0095277.htm
- http://m.wap.gqskj.cn/snews/93573.htm
- http://m.wap.gqskj.cn/snews/8742.htm
- http://m.wap.gqskj.cn/snews/4328934.htm
- http://m.wap.gqskj.cn/snews/7710482.htm
- http://m.wap.gqskj.cn/snews/25846.htm
- http://m.wap.gqskj.cn/snews/517103.htm
- http://m.wap.gqskj.cn/snews/80699.htm
- http://m.wap.gqskj.cn/snews/6312274.htm
- http://m.wap.gqskj.cn/snews/889015.htm
- http://m.wap.gqskj.cn/snews/5314.htm
- http://m.wap.gqskj.cn/snews/30079.htm
- http://m.wap.gqskj.cn/snews/94064.htm
- http://m.wap.gqskj.cn/snews/727664.htm
- http://m.wap.gqskj.cn/snews/5180436.htm
- http://m.wap.gqskj.cn/snews/3125.htm
- http://m.wap.gqskj.cn/snews/47250.htm
- http://m.wap.gqskj.cn/snews/8583.htm
- http://m.wap.gqskj.cn/snews/3464072.htm
- http://m.wap.gqskj.cn/snews/9320479.htm
- http://m.wap.gqskj.cn/snews/6849060.htm
- http://m.wap.gqskj.cn/snews/9598192.htm
- http://m.wap.gqskj.cn/snews/3151138.htm
- http://m.wap.gqskj.cn/snews/4630887.htm
- http://m.wap.gqskj.cn/snews/994832.htm
- http://m.wap.gqskj.cn/snews/97629.htm
- http://m.wap.gqskj.cn/snews/99775.htm
- http://m.wap.gqskj.cn/snews/051336.htm
- http://m.wap.gqskj.cn/snews/88489.htm
- http://m.wap.gqskj.cn/snews/1675.htm
- http://m.wap.gqskj.cn/snews/34711.htm
- http://m.wap.gqskj.cn/snews/4212714.htm
- http://m.wap.gqskj.cn/snews/8113433.htm
- http://m.wap.gqskj.cn/snews/1110071.htm
- http://m.wap.gqskj.cn/snews/721975.htm
- http://m.wap.gqskj.cn/snews/6018021.htm
- http://m.wap.gqskj.cn/snews/4189082.htm
- http://m.wap.gqskj.cn/snews/691585.htm
- http://m.wap.gqskj.cn/snews/33940.htm
- http://m.wap.gqskj.cn/snews/58149.htm
- http://m.wap.gqskj.cn/snews/07677.htm
- http://m.wap.gqskj.cn/snews/272984.htm
- http://m.wap.gqskj.cn/snews/4961259.htm
- http://m.wap.gqskj.cn/snews/1729.htm
- http://m.wap.gqskj.cn/snews/31601.htm
- http://m.wap.gqskj.cn/snews/709308.htm
- http://m.wap.gqskj.cn/snews/8732488.htm
- http://m.wap.gqskj.cn/snews/812236.htm
- http://m.wap.gqskj.cn/snews/9327229.htm
- http://m.wap.gqskj.cn/snews/3268.htm
- http://m.wap.gqskj.cn/snews/06013.htm
- http://m.wap.gqskj.cn/snews/3913572.htm
- http://m.wap.gqskj.cn/snews/7718819.htm
- http://m.wap.gqskj.cn/snews/091277.htm
- http://m.wap.gqskj.cn/snews/804752.htm
- http://m.wap.gqskj.cn/snews/18703.htm
- http://m.wap.gqskj.cn/snews/8059.htm
- http://m.wap.gqskj.cn/snews/596002.htm
- http://m.wap.gqskj.cn/snews/8003.htm
- http://m.wap.gqskj.cn/snews/0947592.htm
- http://m.wap.gqskj.cn/snews/283245.htm
- http://m.wap.gqskj.cn/snews/151504.htm
- http://m.wap.gqskj.cn/snews/45997.htm
- http://m.wap.gqskj.cn/snews/471570.htm
- http://m.wap.gqskj.cn/snews/0387.htm
- http://m.wap.gqskj.cn/snews/138762.htm
- http://m.wap.gqskj.cn/snews/437922.htm
- http://m.wap.gqskj.cn/snews/21444.htm
- http://m.wap.gqskj.cn/snews/8604123.htm
- http://m.wap.gqskj.cn/snews/70805.htm
- http://m.wap.gqskj.cn/snews/229487.htm
- http://m.wap.gqskj.cn/snews/0939455.htm
- http://m.wap.gqskj.cn/snews/94609.htm
- http://m.wap.gqskj.cn/snews/08269.htm
- http://m.wap.gqskj.cn/snews/4605.htm
- http://m.wap.gqskj.cn/snews/29716.htm
- http://m.wap.gqskj.cn/snews/67809.htm
- http://m.wap.gqskj.cn/snews/465484.htm
- http://m.wap.gqskj.cn/snews/94622.htm
- http://m.wap.gqskj.cn/snews/42148.htm
- http://m.wap.gqskj.cn/snews/4198998.htm
- http://m.wap.gqskj.cn/snews/11829.htm
- http://m.wap.gqskj.cn/snews/330237.htm
- http://m.wap.gqskj.cn/snews/4664.htm
- http://m.wap.gqskj.cn/snews/647349.htm
- http://m.wap.gqskj.cn/snews/8052.htm
- http://m.wap.gqskj.cn/snews/7019459.htm
- http://m.wap.gqskj.cn/snews/1253.htm
- http://m.wap.gqskj.cn/snews/9894.htm
- http://m.wap.gqskj.cn/snews/9910.htm
- http://m.wap.gqskj.cn/snews/4201.htm
- http://m.wap.gqskj.cn/snews/9165.htm
- http://m.wap.gqskj.cn/snews/53226.htm
- http://m.wap.gqskj.cn/snews/15474.htm
- http://m.wap.gqskj.cn/snews/7722.htm
- http://m.wap.gqskj.cn/snews/7747130.htm
- http://m.wap.gqskj.cn/snews/6716819.htm
- http://m.wap.gqskj.cn/snews/7794.htm
- http://m.wap.gqskj.cn/snews/38111.htm
- http://m.wap.gqskj.cn/snews/9931.htm
- http://m.wap.gqskj.cn/snews/82244.htm
- http://m.wap.gqskj.cn/snews/7417216.htm
- http://m.wap.gqskj.cn/snews/9621.htm
- http://m.wap.gqskj.cn/snews/3010.htm
- http://m.wap.gqskj.cn/snews/805773.htm
- http://m.wap.gqskj.cn/snews/045060.htm
- http://m.wap.gqskj.cn/snews/8475.htm
- http://m.wap.gqskj.cn/snews/8898070.htm
- http://m.wap.gqskj.cn/snews/65335.htm
- http://m.wap.gqskj.cn/snews/196815.htm
- http://m.wap.gqskj.cn/snews/7895420.htm
- http://m.wap.gqskj.cn/snews/837252.htm
- http://m.wap.gqskj.cn/snews/74592.htm
- http://m.wap.gqskj.cn/snews/3958131.htm
- http://m.wap.gqskj.cn/snews/08130.htm
- http://m.wap.gqskj.cn/snews/983866.htm
- http://m.wap.gqskj.cn/snews/04402.htm
- http://m.wap.gqskj.cn/snews/8078193.htm
- http://m.wap.gqskj.cn/snews/2995359.htm
- http://m.wap.gqskj.cn/snews/1813.htm
- http://m.wap.gqskj.cn/snews/6262.htm
- http://m.wap.gqskj.cn/snews/52373.htm
- http://m.wap.gqskj.cn/snews/820762.htm
- http://m.wap.gqskj.cn/snews/35343.htm
- http://m.wap.gqskj.cn/snews/26914.htm
- http://m.wap.gqskj.cn/snews/77324.htm
- http://m.wap.gqskj.cn/snews/61568.htm
- http://m.wap.gqskj.cn/snews/1889198.htm
- http://m.wap.gqskj.cn/snews/1713.htm
- http://m.wap.gqskj.cn/snews/8993288.htm
- http://m.wap.gqskj.cn/snews/612503.htm
- http://m.wap.gqskj.cn/snews/9311.htm
- http://m.wap.gqskj.cn/snews/6809.htm
- http://m.wap.gqskj.cn/snews/2737238.htm
- http://m.wap.gqskj.cn/snews/6163013.htm
- http://m.wap.gqskj.cn/snews/154721.htm
- http://m.wap.gqskj.cn/snews/34574.htm
- http://m.wap.gqskj.cn/snews/188003.htm
- http://m.wap.gqskj.cn/snews/8376937.htm
- http://m.wap.gqskj.cn/snews/99995.htm
- http://m.wap.gqskj.cn/snews/093383.htm
- http://m.wap.gqskj.cn/snews/2384651.htm
- http://m.wap.gqskj.cn/snews/6998.htm
- http://m.wap.gqskj.cn/snews/7703832.htm
- http://m.wap.gqskj.cn/snews/3350421.htm
- http://m.wap.gqskj.cn/snews/20209.htm
- http://m.wap.gqskj.cn/snews/94603.htm
- http://m.wap.gqskj.cn/snews/6097262.htm
- http://m.wap.gqskj.cn/snews/3095.htm
- http://m.wap.gqskj.cn/snews/019123.htm
- http://m.wap.gqskj.cn/snews/20179.htm
- http://m.wap.gqskj.cn/snews/53350.htm
- http://m.wap.gqskj.cn/snews/02070.htm
- http://m.wap.gqskj.cn/snews/2174.htm
- http://m.wap.gqskj.cn/snews/16982.htm
- http://m.wap.gqskj.cn/snews/6562204.htm
- http://m.wap.gqskj.cn/snews/09606.htm
- http://m.wap.gqskj.cn/snews/5921996.htm
- http://m.wap.gqskj.cn/snews/394028.htm
- http://m.wap.gqskj.cn/snews/4394878.htm
- http://m.wap.gqskj.cn/snews/53002.htm
- http://m.wap.gqskj.cn/snews/526512.htm
- http://m.wap.gqskj.cn/snews/2540.htm
- http://m.wap.gqskj.cn/snews/62936.htm
- http://m.wap.gqskj.cn/snews/7743.htm
- http://m.wap.gqskj.cn/snews/1342947.htm
- http://m.wap.gqskj.cn/snews/323184.htm
- http://m.wap.gqskj.cn/snews/5524.htm
- http://m.wap.gqskj.cn/snews/2856695.htm
- http://m.wap.gqskj.cn/snews/40819.htm
- http://m.wap.gqskj.cn/snews/0348.htm
- http://m.wap.gqskj.cn/snews/464890.htm
- http://m.wap.gqskj.cn/snews/0937.htm
- http://m.wap.gqskj.cn/snews/5131.htm
- http://m.wap.gqskj.cn/snews/37631.htm
- http://m.wap.gqskj.cn/snews/5605.htm
- http://m.wap.gqskj.cn/snews/3960110.htm
- http://m.wap.gqskj.cn/snews/3915607.htm
- http://m.wap.gqskj.cn/snews/1486.htm
- http://m.wap.gqskj.cn/snews/9522.htm
- http://m.wap.gqskj.cn/snews/36616.htm
- http://m.wap.gqskj.cn/snews/6580.htm
- http://m.wap.gqskj.cn/snews/894177.htm
- http://m.wap.gqskj.cn/snews/99482.htm
- http://m.wap.gqskj.cn/snews/5317.htm
- http://m.wap.gqskj.cn/snews/7093766.htm
- http://m.wap.gqskj.cn/snews/062016.htm
- http://m.wap.gqskj.cn/snews/08349.htm
- http://m.wap.gqskj.cn/snews/67865.htm
- http://m.wap.gqskj.cn/snews/198678.htm
- http://m.wap.gqskj.cn/snews/03276.htm
- http://m.wap.gqskj.cn/snews/727264.htm
- http://m.wap.gqskj.cn/snews/65802.htm
- http://m.wap.gqskj.cn/snews/172311.htm
- http://m.wap.gqskj.cn/snews/612847.htm
- http://m.wap.gqskj.cn/snews/42994.htm
- http://m.wap.gqskj.cn/snews/9196415.htm
- http://m.wap.gqskj.cn/snews/670937.htm
- http://m.wap.gqskj.cn/snews/4389.htm
- http://m.wap.gqskj.cn/snews/929645.htm
- http://m.wap.gqskj.cn/snews/215177.htm
- http://m.wap.gqskj.cn/snews/2546.htm
- http://m.wap.gqskj.cn/snews/5092.htm
- http://m.wap.gqskj.cn/snews/56537.htm
- http://m.wap.gqskj.cn/snews/08618.htm
- http://m.wap.gqskj.cn/snews/544232.htm
- http://m.wap.gqskj.cn/snews/6365.htm
- http://m.wap.gqskj.cn/snews/772338.htm
- http://m.wap.gqskj.cn/snews/3277806.htm
- http://m.wap.gqskj.cn/snews/2276185.htm
- http://m.wap.gqskj.cn/snews/87633.htm
- http://m.wap.gqskj.cn/snews/44915.htm
- http://m.wap.gqskj.cn/snews/34586.htm
- http://m.wap.gqskj.cn/snews/2064466.htm
- http://m.wap.gqskj.cn/snews/109105.htm
- http://m.wap.gqskj.cn/snews/6945820.htm
- http://m.wap.gqskj.cn/snews/23001.htm
- http://m.wap.gqskj.cn/snews/601284.htm
- http://m.wap.gqskj.cn/snews/7303.htm
- http://m.wap.gqskj.cn/snews/653002.htm
- http://m.wap.gqskj.cn/snews/9594508.htm
- http://m.wap.gqskj.cn/snews/227784.htm
- http://m.wap.gqskj.cn/snews/40193.htm
- http://m.wap.gqskj.cn/snews/794474.htm
- http://m.wap.gqskj.cn/snews/8788.htm
- http://m.wap.gqskj.cn/snews/563067.htm
- http://m.wap.gqskj.cn/snews/555163.htm
- http://m.wap.gqskj.cn/snews/3295.htm
- http://m.wap.gqskj.cn/snews/0822.htm
- http://m.wap.gqskj.cn/snews/82804.htm
- http://m.wap.gqskj.cn/snews/075398.htm
- http://m.wap.gqskj.cn/snews/11151.htm
- http://m.wap.gqskj.cn/snews/05742.htm
- http://m.wap.gqskj.cn/snews/8412273.htm
- http://m.wap.gqskj.cn/snews/478987.htm
- http://m.wap.gqskj.cn/snews/6456507.htm
- http://m.wap.gqskj.cn/snews/9949.htm
- http://m.wap.gqskj.cn/snews/026814.htm
- http://m.wap.gqskj.cn/snews/2045.htm

## 项目结构

```
linkvault/
├── app.py                      # 本地预览服务入口（Flask 应用）
├── requirements.txt            # Python 依赖声明
├── README.md                   # 项目说明文档（本文件）
├── .gitignore                  # Git 忽略规则
├── config/
│   ├── default.yaml            # 默认配置（标签预设、端口、分页大小）
│   └── schema.json             # 元数据扩展字段的 JSON Schema 定义
├── data/
│   ├── raw/                    # 原始导入文件存放目录（CSV / JSON / 纯文本列表）
│   ├── curated/                # 经过清洗和分类后的资源主数据（YAML 格式）
│   └── batches/                # 按批次归档的导入记录，包含批次清单和统计摘要
├── scripts/
│   ├── init_db.py              # 初始化数据库结构并生成示例数据
│   ├── import_links.py         # 从外部文件批量导入 URL 的核心脚本
│   ├── export_markdown.py      # 将当前资源列表导出为纯 Markdown 无序列表
│   └── validate_urls.py        # 校验 URL 格式完整性，检查重复条目和协议一致性
├── templates/
│   └── preview.html            # 本地预览服务的 HTML 模板
├── docs/                       # 完整文档目录（快速开始、配置、数据管理、集成、架构）
│   ├── quickstart.md
│   ├── configuration.md
│   ├── data-management.md
│   ├── integration.md
│   └── architecture.md
├── tests/                      # 单元测试与集成测试用例
│   ├── test_import.py
│   ├── test_export.py
│   └── test_validation.py
└── utils/                      # 通用工具函数模块
    ├── validators.py           # URL 校验与规范化辅助函数（但不自动改写原始值）
    ├── formatters.py           # Markdown 列表生成器与表格渲染器
    └── file_handlers.py        # 多格式文件读取与写入支持（CSV, JSON, YAML）
```

## 贡献指南

1. 查阅现有 Issues 和 Projects 面板，确认当前开发优先级，避免重复工作。新功能提议或缺陷报告请先通过 Issue 模板提交，获得维护者反馈后再着手实现。

2. Fork 本仓库并创建以 feature/ 或 fix/ 为前缀的分支，例如 feature/add-tag-filter。所有代码变更需保持与项目现有代码风格一致，使用 black 进行格式化，并通过 pre-commit 钩子检查。

3. 编写或更新对应模块的单元测试，确保测试覆盖率达到 80% 以上。所有新增对外接口或配置项必须在 docs/ 目录下补充对应文档说明，并更新文档导航表格中的链接。

4. 提交 Pull Request 时请填写完整模板，包括变更动机、实现方案、测试结果和影响范围。PR 需要至少一名核心维护者审核通过后方可合并，合并前需解决所有对话线程和 CI 检查失败项。

5. 重大架构调整或数据模型变更需提前在 Discussion 中发起设计讨论，获得共识后再进入开发阶段。批次导入和资源列表导出功能涉及的数据格式变更需保持向后兼容至少两个小版本。

## 常见问题

**问：导入的 URL 是否会被自动补全协议或规范化域名？**

答：不会。LinkVault 核心设计原则之一是原始 URL 完整留存。系统在导入、存储和导出全流程中均不会对用户提供的 URL 字符串做任何自动补全、大小写转换、协议升降级或结尾斜杠增删操作。每条链接以纯文本形式原样保存在数据文件中，导出时亦原样输出。用户如需统一格式，应在导入前自行预处理。

**问：资源列表支持哪些导入格式？批次号如何管理？**

答：目前支持纯文本列表（每行一条 URL）、CSV 文件（需包含 url 列）和 JSON 数组格式。批次号由系统自动生成，格式为 YYYYMMDD-三位序号，例如 20260825-001。用户也可在导入时通过 --batch 参数自定义批次名称。每个批次的导入记录会独立存储在 data/batches/ 目录下，便于后续追溯和回滚。

**问：预览服务能否在生产环境长期运行？**

答：内置的 Flask 预览服务仅用于本地开发和内容校对，其单进程服务器性能和安全性不足以支撑生产级流量。生产环境部署建议使用 gunicorn + Nginx 组合，并将静态资源交由 CDN 或对象存储托管。如需在生产环境中提供资源列表访问能力，可参考 docs/integration.md 中的部署指南进行配置。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
