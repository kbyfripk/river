# WebResource Indexer

WebResource Indexer 是一个面向技术文档、新闻资讯与数据快照的轻量级外链索引与导航系统。该项目定位于为开发者、技术研究者及内容运营人员提供一套可自托管的 URL 聚合与分类管理工具，用于将分散在不同来源的链接资源按照批次、主题或时间维度进行结构化存储与展示，并通过统一的 Web 界面实现快速检索与访问。其核心价值在于降低大规模外链管理过程中的重复劳动成本，帮助用户从杂乱的收藏夹或文档碎片中抽离出可维护、可共享、可版本化的链接资产库。

本项目不依赖复杂的数据库引擎，采用纯文件目录结构配合静态站点生成逻辑，适合部署在各类低成本虚拟主机、对象存储或云函数环境。目标用户包括开源文档维护者、技术博客作者、数据采集工程师以及需要定期整理外部参考资料的研究人员。通过将原始链接列表转化为带元数据索引的导航页面，WebResource Indexer 使链接资源的长期保存与团队协作变得更加规范且可追溯。

## 功能概览

**批量链接导入** 支持通过纯文本列表或 CSV 格式一次性导入大量 URL，自动解析目标页面的标题与元描述，减少手动录入工作量。

**多维度分类标签** 允许为每条链接分配自定义标签与所属批次编号，便于按项目周期或主题领域进行筛选和分组展示。

**快照信息提取** 自动抓取链接指向页面的生成时间、内容摘要及关键头信息，形成本地缓存索引，即使原始页面发生变更或下线仍保留基础元数据。

**全文检索与过滤** 内置基于标题、描述和标签的简单关键词搜索功能，并支持按批次号、来源域名和收录时间进行多条件过滤排序。

**静态页面生成** 将索引数据渲染为纯 HTML 静态导航站点，无需动态后端即可直接部署至 Nginx、Apache 或 CDN 服务，满足高并发访问场景。

**增量更新机制** 支持增量导入新链接并自动合并已有索引，避免重复录入，同时记录每次更新的时间戳与变动条目数量。

**导出与备份接口** 提供 JSON 格式的完整索引导出功能，方便用户进行本地归档或迁移至其他数据处理流水线。

**响应式展示布局** 前端界面自动适配桌面端与移动端屏幕，确保在手机、平板与各类浏览器环境下均能获得一致的浏览体验。

## 应用场景

技术文档团队的日常外链整理
技术文档撰写过程中，编辑人员需要频繁引用外部规范、RFC 文档、开源项目仓库及技术博客。WebResource Indexer 可作为内部知识库的补充模块，将零散的参考链接按文档版本或模块分类存放，团队成员可在同一索引体系中快速查找历史引用记录，减少重复搜索时间。

数据采集项目的资源追溯管理
在数据采集与爬虫工程实践中，工程师往往需要保存大量目标网站入口、API 文档地址及数据样例页面。本系统能够将采集任务相关的 URL 按执行批次进行归档，并记录每次采集的时间窗口，便于后续问题排查与数据溯源审计。

开源社区的学习资源导航站建设
开源社区的技术布道者可以利用本工具构建面向特定技术栈的学习资源导航站点，例如将教程、视频课程、官方文档和社区论坛链接按难度等级或主题分类呈现，降低新手入门的信息筛选成本。

个人知识管理体系的补充环节
独立开发者或技术研究者可将本系统作为自身知识管理流程的补充，将阅读过的技术文章、工具站点和在线实验环境入口进行统一登记，配合标签体系实现个人技术成长轨迹的可视化记录。

## 快速开始

以下步骤指导您在本地环境快速启动 WebResource Indexer 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webresource-indexer/webresource-indexer.git

# 进入项目根目录
cd webresource-indexer

# 安装 Python 依赖包（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 执行初始化导入脚本，将原始链接列表导入索引（示例数据位于 data/raw/batch_40.txt）
python scripts/import_batch.py --batch 40 --source data/raw/batch_40.txt

# 生成静态站点页面，输出至 public 目录
python scripts/build_static.py --output public

# 启动本地开发服务器预览站点
python -m http.server --directory public 8000
```

访问 http://localhost:8000 即可浏览索引后的导航页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于导入脚本与静态生成逻辑 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| requests | 2.25.0 及以上 | 用于发送 HTTP 请求获取目标链接的元数据信息 |
| beautifulsoup4 | 4.9.0 及以上 | 解析目标页面 HTML，提取标题与摘要内容 |
| lxml | 4.6.0 及以上 | 作为 beautifulsoup4 的解析器后端，提升解析效率 |
| markdown | 3.3.0 及以上 | 将 Markdown 格式的说明文档渲染为 HTML 页面内容 |
| jinja2 | 3.0.0 及以上 | 模板引擎，用于生成静态导航页面的 HTML 结构 |
| click | 8.0.0 及以上 | 命令行接口框架，提供子命令解析与帮助信息 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何进行链接导入、分类编辑与静态站点生成操作 |
| 配置参考 | docs/configuration.md | 各环境变量与配置文件的参数含义及默认值说明 |
| 开发指南 | docs/development.md | 二次开发时的模块划分、代码规范与调试方法 |
| API 接口 | docs/api_reference.md | 导入脚本、构建脚本及工具函数暴露的接口签名与返回值格式 |

## 资源列表

- http://m.3g.fcful.cn/snews/135569.htm
- http://m.3g.fcful.cn/snews/9144104.htm
- http://m.3g.fcful.cn/snews/89626.htm
- http://m.3g.fcful.cn/snews/933461.htm
- http://m.3g.fcful.cn/snews/453931.htm
- http://m.3g.fcful.cn/snews/09096.htm
- http://m.3g.fcful.cn/snews/836183.htm
- http://m.3g.fcful.cn/snews/727400.htm
- http://m.3g.fcful.cn/snews/4144976.htm
- http://m.3g.fcful.cn/snews/5867735.htm
- http://m.3g.fcful.cn/snews/3362111.htm
- http://m.3g.fcful.cn/snews/1111.htm
- http://m.3g.fcful.cn/snews/0984.htm
- http://m.3g.fcful.cn/snews/9374283.htm
- http://m.3g.fcful.cn/snews/5006779.htm
- http://m.3g.fcful.cn/snews/90865.htm
- http://m.3g.fcful.cn/snews/4361546.htm
- http://m.3g.fcful.cn/snews/226856.htm
- http://m.3g.fcful.cn/snews/79881.htm
- http://m.3g.fcful.cn/snews/7129893.htm
- http://m.3g.fcful.cn/snews/8553058.htm
- http://m.3g.fcful.cn/snews/2078581.htm
- http://m.3g.fcful.cn/snews/7857282.htm
- http://m.3g.fcful.cn/snews/6668923.htm
- http://m.3g.fcful.cn/snews/7428618.htm
- http://m.3g.fcful.cn/snews/136011.htm
- http://m.3g.fcful.cn/snews/6195301.htm
- http://m.3g.fcful.cn/snews/6471310.htm
- http://m.3g.fcful.cn/snews/9151.htm
- http://m.3g.fcful.cn/snews/1899.htm
- http://m.3g.fcful.cn/snews/073424.htm
- http://m.3g.fcful.cn/snews/6754531.htm
- http://m.3g.fcful.cn/snews/219137.htm
- http://m.3g.fcful.cn/snews/6451502.htm
- http://m.3g.fcful.cn/snews/129814.htm
- http://m.3g.fcful.cn/snews/431645.htm
- http://m.3g.fcful.cn/snews/16304.htm
- http://m.3g.fcful.cn/snews/9663.htm
- http://m.3g.fcful.cn/snews/7091286.htm
- http://m.3g.fcful.cn/snews/4026.htm
- http://m.3g.fcful.cn/snews/393814.htm
- http://m.3g.fcful.cn/snews/32361.htm
- http://m.3g.fcful.cn/snews/7627293.htm
- http://m.3g.fcful.cn/snews/8198.htm
- http://m.3g.fcful.cn/snews/22595.htm
- http://m.3g.fcful.cn/snews/0070064.htm
- http://m.3g.fcful.cn/snews/2295568.htm
- http://m.3g.fcful.cn/snews/2763.htm
- http://m.3g.fcful.cn/snews/1579.htm
- http://m.3g.fcful.cn/snews/5488596.htm
- http://m.3g.fcful.cn/snews/100014.htm
- http://m.3g.fcful.cn/snews/8553.htm
- http://m.3g.fcful.cn/snews/098134.htm
- http://m.3g.fcful.cn/snews/7967784.htm
- http://m.3g.fcful.cn/snews/9571886.htm
- http://m.3g.fcful.cn/snews/865537.htm
- http://m.3g.fcful.cn/snews/3830737.htm
- http://m.3g.fcful.cn/snews/5116390.htm
- http://m.3g.fcful.cn/snews/49382.htm
- http://m.3g.fcful.cn/snews/769424.htm
- http://m.3g.fcful.cn/snews/6626.htm
- http://m.3g.fcful.cn/snews/7948.htm
- http://m.3g.fcful.cn/snews/827839.htm
- http://m.3g.fcful.cn/snews/0463.htm
- http://m.3g.fcful.cn/snews/5776.htm
- http://m.3g.fcful.cn/snews/96901.htm
- http://m.3g.fcful.cn/snews/0675711.htm
- http://m.3g.fcful.cn/snews/7265904.htm
- http://m.3g.fcful.cn/snews/4569396.htm
- http://m.3g.fcful.cn/snews/26394.htm
- http://m.3g.fcful.cn/snews/83761.htm
- http://m.3g.fcful.cn/snews/9643.htm
- http://m.3g.fcful.cn/snews/307643.htm
- http://m.3g.fcful.cn/snews/44978.htm
- http://m.3g.fcful.cn/snews/0872401.htm
- http://m.3g.fcful.cn/snews/84557.htm
- http://m.3g.fcful.cn/snews/3565941.htm
- http://m.3g.fcful.cn/snews/8747469.htm
- http://m.3g.fcful.cn/snews/1862857.htm
- http://m.3g.fcful.cn/snews/5925152.htm
- http://m.3g.fcful.cn/snews/03714.htm
- http://m.3g.fcful.cn/snews/232197.htm
- http://m.3g.fcful.cn/snews/9158.htm
- http://m.3g.fcful.cn/snews/2656585.htm
- http://m.3g.fcful.cn/snews/73229.htm
- http://m.3g.fcful.cn/snews/826719.htm
- http://m.3g.fcful.cn/snews/4766543.htm
- http://m.3g.fcful.cn/snews/4298245.htm
- http://m.3g.fcful.cn/snews/0949933.htm
- http://m.3g.fcful.cn/snews/901531.htm
- http://m.3g.fcful.cn/snews/326920.htm
- http://m.3g.fcful.cn/snews/40795.htm
- http://m.3g.fcful.cn/snews/8644566.htm
- http://m.3g.fcful.cn/snews/7927.htm
- http://m.3g.fcful.cn/snews/629256.htm
- http://m.3g.fcful.cn/snews/320291.htm
- http://m.3g.fcful.cn/snews/811446.htm
- http://m.3g.fcful.cn/snews/9205764.htm
- http://m.3g.fcful.cn/snews/63350.htm
- http://m.3g.fcful.cn/snews/165373.htm
- http://m.3g.fcful.cn/snews/53245.htm
- http://m.3g.fcful.cn/snews/2356008.htm
- http://m.3g.fcful.cn/snews/012343.htm
- http://m.3g.fcful.cn/snews/65327.htm
- http://m.3g.fcful.cn/snews/2360.htm
- http://m.3g.fcful.cn/snews/4756.htm
- http://m.3g.fcful.cn/snews/578772.htm
- http://m.3g.fcful.cn/snews/9785.htm
- http://m.3g.fcful.cn/snews/34444.htm
- http://m.3g.fcful.cn/snews/636558.htm
- http://m.3g.fcful.cn/snews/1669708.htm
- http://m.3g.fcful.cn/snews/0814.htm
- http://m.3g.fcful.cn/snews/528984.htm
- http://m.3g.fcful.cn/snews/9115.htm
- http://m.3g.fcful.cn/snews/66186.htm
- http://m.3g.fcful.cn/snews/796359.htm
- http://m.3g.fcful.cn/snews/1137.htm
- http://m.3g.fcful.cn/snews/9743.htm
- http://m.3g.fcful.cn/snews/38559.htm
- http://m.3g.fcful.cn/snews/0896027.htm
- http://m.3g.fcful.cn/snews/5259.htm
- http://m.3g.fcful.cn/snews/4611.htm
- http://m.3g.fcful.cn/snews/84734.htm
- http://m.3g.fcful.cn/snews/403391.htm
- http://m.3g.fcful.cn/snews/90547.htm
- http://m.3g.fcful.cn/snews/4929.htm
- http://m.3g.fcful.cn/snews/9474.htm
- http://m.3g.fcful.cn/snews/4487829.htm
- http://m.3g.fcful.cn/snews/619079.htm
- http://m.3g.fcful.cn/snews/045793.htm
- http://m.3g.fcful.cn/snews/2501.htm
- http://m.3g.fcful.cn/snews/6031022.htm
- http://m.3g.fcful.cn/snews/005310.htm
- http://m.3g.fcful.cn/snews/60346.htm
- http://m.3g.fcful.cn/snews/8724.htm
- http://m.3g.fcful.cn/snews/235430.htm
- http://m.3g.fcful.cn/snews/85962.htm
- http://m.3g.fcful.cn/snews/494489.htm
- http://m.3g.fcful.cn/snews/87130.htm
- http://m.3g.fcful.cn/snews/7109.htm
- http://m.3g.fcful.cn/snews/7434.htm
- http://m.3g.fcful.cn/snews/06515.htm
- http://m.3g.fcful.cn/snews/0904071.htm
- http://m.3g.fcful.cn/snews/84306.htm
- http://m.3g.fcful.cn/snews/284021.htm
- http://m.3g.fcful.cn/snews/727457.htm
- http://m.3g.fcful.cn/snews/650391.htm
- http://m.3g.fcful.cn/snews/60407.htm
- http://m.3g.fcful.cn/snews/6658.htm
- http://m.3g.fcful.cn/snews/9898.htm
- http://m.3g.fcful.cn/snews/8934.htm
- http://m.3g.fcful.cn/snews/065260.htm
- http://m.3g.fcful.cn/snews/496824.htm
- http://m.3g.fcful.cn/snews/94047.htm
- http://m.3g.fcful.cn/snews/5456.htm
- http://m.3g.fcful.cn/snews/3707834.htm
- http://m.3g.fcful.cn/snews/9411875.htm
- http://m.3g.fcful.cn/snews/0320.htm
- http://m.3g.fcful.cn/snews/0584.htm
- http://m.3g.fcful.cn/snews/538106.htm
- http://m.3g.fcful.cn/snews/495711.htm
- http://m.3g.fcful.cn/snews/10053.htm
- http://m.3g.fcful.cn/snews/4570.htm
- http://m.3g.fcful.cn/snews/091589.htm
- http://m.3g.fcful.cn/snews/5920.htm
- http://m.3g.fcful.cn/snews/3591.htm
- http://m.3g.fcful.cn/snews/175831.htm
- http://m.3g.fcful.cn/snews/061583.htm
- http://m.3g.fcful.cn/snews/1015.htm
- http://m.3g.fcful.cn/snews/0249858.htm
- http://m.3g.fcful.cn/snews/831660.htm
- http://m.3g.fcful.cn/snews/441489.htm
- http://m.3g.fcful.cn/snews/61992.htm
- http://m.3g.fcful.cn/snews/58744.htm
- http://m.3g.fcful.cn/snews/09424.htm
- http://m.3g.fcful.cn/snews/4180.htm
- http://m.3g.fcful.cn/snews/7593.htm
- http://m.3g.fcful.cn/snews/595570.htm
- http://m.3g.fcful.cn/snews/394895.htm
- http://m.3g.fcful.cn/snews/09555.htm
- http://m.3g.fcful.cn/snews/6330.htm
- http://m.3g.fcful.cn/snews/1206337.htm
- http://m.3g.fcful.cn/snews/8307.htm
- http://m.3g.fcful.cn/snews/1776.htm
- http://m.3g.fcful.cn/snews/5228463.htm
- http://m.3g.fcful.cn/snews/053757.htm
- http://m.3g.fcful.cn/snews/942793.htm
- http://m.3g.fcful.cn/snews/70595.htm
- http://m.3g.fcful.cn/snews/92403.htm
- http://m.3g.fcful.cn/snews/274360.htm
- http://m.3g.fcful.cn/snews/649407.htm
- http://m.3g.fcful.cn/snews/4225703.htm
- http://m.3g.fcful.cn/snews/34173.htm
- http://m.3g.fcful.cn/snews/27969.htm
- http://m.3g.fcful.cn/snews/61409.htm
- http://m.3g.fcful.cn/snews/6158547.htm
- http://m.3g.fcful.cn/snews/34135.htm
- http://m.3g.fcful.cn/snews/85839.htm
- http://m.3g.fcful.cn/snews/536067.htm
- http://m.3g.fcful.cn/snews/2242313.htm
- http://m.3g.fcful.cn/snews/1500.htm
- http://m.3g.fcful.cn/snews/4794.htm
- http://m.3g.fcful.cn/snews/708333.htm
- http://m.3g.fcful.cn/snews/72582.htm
- http://m.3g.fcful.cn/snews/150271.htm
- http://m.3g.fcful.cn/snews/481744.htm
- http://m.3g.fcful.cn/snews/8279.htm
- http://m.3g.fcful.cn/snews/427207.htm
- http://m.3g.fcful.cn/snews/3563342.htm
- http://m.3g.fcful.cn/snews/353945.htm
- http://m.3g.fcful.cn/snews/1795.htm
- http://m.3g.fcful.cn/snews/873042.htm
- http://m.3g.fcful.cn/snews/3865682.htm
- http://m.3g.fcful.cn/snews/806564.htm
- http://m.3g.fcful.cn/snews/22839.htm
- http://m.3g.fcful.cn/snews/848803.htm
- http://m.3g.fcful.cn/snews/84900.htm
- http://m.3g.fcful.cn/snews/816636.htm
- http://m.3g.fcful.cn/snews/9681.htm
- http://m.3g.fcful.cn/snews/2623451.htm
- http://m.3g.fcful.cn/snews/69500.htm
- http://m.3g.fcful.cn/snews/2284761.htm
- http://m.3g.fcful.cn/snews/90751.htm
- http://m.3g.fcful.cn/snews/320760.htm
- http://m.3g.fcful.cn/snews/5780.htm
- http://m.3g.fcful.cn/snews/560912.htm
- http://m.3g.fcful.cn/snews/165950.htm
- http://m.3g.fcful.cn/snews/182657.htm
- http://m.3g.fcful.cn/snews/524111.htm
- http://m.3g.fcful.cn/snews/58829.htm
- http://m.3g.fcful.cn/snews/8169763.htm
- http://m.3g.fcful.cn/snews/48800.htm
- http://m.3g.fcful.cn/snews/98102.htm
- http://m.3g.fcful.cn/snews/921098.htm
- http://m.3g.fcful.cn/snews/0413.htm
- http://m.3g.fcful.cn/snews/1622548.htm
- http://m.3g.fcful.cn/snews/9948312.htm
- http://m.3g.fcful.cn/snews/2262.htm
- http://m.3g.fcful.cn/snews/90449.htm
- http://m.3g.fcful.cn/snews/5299.htm
- http://m.3g.fcful.cn/snews/3797.htm
- http://m.3g.fcful.cn/snews/91111.htm
- http://m.3g.fcful.cn/snews/842334.htm
- http://m.3g.fcful.cn/snews/1642.htm
- http://m.3g.fcful.cn/snews/76170.htm
- http://m.3g.fcful.cn/snews/828029.htm
- http://m.3g.fcful.cn/snews/261869.htm
- http://m.3g.fcful.cn/snews/2107513.htm
- http://m.3g.fcful.cn/snews/5334.htm
- http://m.3g.fcful.cn/snews/49644.htm

## 项目结构

```
webresource-indexer/
├── scripts/                          # 可执行脚本与命令行工具
│   ├── import_batch.py               # 批量导入链接的核心脚本，接收批次编号与源文件路径
│   ├── build_static.py               # 静态站点生成器，渲染 HTML 页面输出至 public 目录
│   └── export_json.py                # 将当前索引导出为标准 JSON 格式文件
├── indexer/                          # 索引核心逻辑模块
│   ├── __init__.py                   # 包初始化文件，暴露主要接口类
│   ├── fetcher.py                    # 负责发送 HTTP 请求并解析目标页面元数据
│   ├── parser.py                     # 基于 beautifulsoup4 实现标题与摘要提取逻辑
│   ├── storage.py                    # 管理本地 JSON 索引文件的读写与合并操作
│   └── models.py                     # 定义链接条目、标签和批次的数据结构
├── templates/                        # Jinja2 模板文件，用于生成各类静态页面
│   ├── base.html                     # 基础模板，包含全局导航栏与页脚结构
│   ├── index.html                    # 首页模板，展示总览统计与最近更新条目
│   └── detail.html                   # 单条链接详情页模板，展示完整元数据与标签
├── static/                           # 前端静态资源，包括样式表与 JavaScript 脚本
│   ├── css/
│   │   └── style.css                 # 响应式布局样式，覆盖桌面与移动端显示
│   └── js/
│       └── filter.js                 # 前端过滤与搜索交互逻辑
├── data/                             # 数据存储目录，存放索引文件与原始导入数据
│   ├── index.json                    # 主索引文件，存储所有已导入链接的结构化信息
│   ├── raw/                          # 原始导入数据归档，按批次存放纯文本链接列表
│   │   └── batch_40.txt              # 第 40 批次的原始 URL 列表
│   └── cache/                        # 元数据缓存目录，避免重复抓取同一页面
│       └── url_metadata_cache.db     # SQLite 缓存数据库，存储已抓取页面的摘要信息
├── tests/                            # 单元测试与集成测试代码
│   ├── test_fetcher.py               # 测试 fetcher 模块的 HTTP 请求与重试逻辑
│   ├── test_parser.py                # 测试 parser 模块对不同 HTML 结构的解析鲁棒性
│   └── test_storage.py               # 测试 storage 模块的读写与合并功能
├── docs/                             # 项目文档，包含用户手册与开发指南
│   ├── user_guide.md                 # 面向最终用户的完整操作手册
│   ├── configuration.md              # 环境变量与配置项详细说明
│   ├── development.md                # 面向贡献者的开发环境搭建与调试指引
│   └── api_reference.md              # 各模块接口的详细签名与返回值说明
├── requirements.txt                  # Python 依赖声明文件，固定各库版本号
├── setup.py                          # 项目安装脚本，支持 pip install -e . 开发模式安装
├── LICENSE                           # MIT 许可证文件
└── README.md                         # 项目概述文档（即本文件）
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账户，并克隆至本地开发环境。确保本地 Python 版本符合要求并已创建虚拟环境。
2. 创建独立的功能分支，分支名称需体现本次变更的简要内容，例如 `fix-import-timeout` 或 `add-tag-filter`。
3. 在开发过程中，请遵循项目已有的代码风格（PEP 8 规范），并为新增函数或类编写相应的单元测试，保证测试覆盖率不低于现有水平。
4. 提交代码前，运行完整的测试套件，确保所有已有测试用例通过，且无新增警告或错误。测试命令为 `pytest tests/`。
5. 通过 Pull Request 提交变更，并在请求描述中清晰说明本次修改的目的、实现方式及影响范围。PR 需要至少一位项目维护者审核通过后方可合并。

## 常见问题

**Q：导入大量链接时出现超时或失败，应如何排查？**

A：首先检查网络环境是否能够正常访问目标域名。若网络通畅，可适当调整 `fetcher.py` 中的 `REQUEST_TIMEOUT` 参数（默认值为 10 秒）。此外，系统会为每个目标页面自动生成缓存记录，重新运行导入脚本时会优先读取缓存，避免重复发送请求。若仍存在大量失败条目，建议检查目标站点是否启用了反爬机制，并考虑在请求头中添加常见的 User-Agent 字段。

**Q：如何迁移索引数据至另一台服务器？**

A：直接复制整个 `data/` 目录至新服务器的对应位置即可。索引文件 `index.json` 采用纯文本格式存储所有链接元数据，缓存数据库 `url_metadata_cache.db` 为 SQLite 文件，两者均具备良好的跨平台兼容性。若希望仅迁移链接列表而不保留缓存，可只复制 `data/index.json` 和 `data/raw/` 目录，并在新环境重新执行导入脚本以重建缓存。

**Q：生成的静态页面能否部署到对象存储服务（如 AWS S3 或阿里云 OSS）？**

A：完全可以。`build_static.py` 脚本输出的 `public` 目录内全部为静态 HTML、CSS 和 JavaScript 文件，不依赖任何后端服务。您可以将该目录下的所有文件上传至任意支持静态网站托管的对象存储桶中，并配置默认首页为 `index.html`。同时，项目中的资源链接均为绝对路径引用，部署时无需修改内部链接地址。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
