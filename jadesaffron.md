# WebLink Navigator

WebLink Navigator 是一个面向技术调研、信息聚合与内容归档场景的轻量级外链资源导航系统。该项目定位于帮助开发者、研究员与内容运营人员高效管理大量分散的网页链接，通过结构化的索引机制与可扩展的元数据体系，将原始 URL 资产转化为可检索、可分类、可追溯的知识库基础构件。项目本身不依赖复杂的前端框架或数据库服务，以纯静态文件与脚本工具为核心，适用于个人知识管理、团队共享书签库以及自动化信息采集管道中的链接治理环节。

## 功能概览

- 批量链接导入与去重：支持从文本文件、CSV 或直接粘贴的原始 URL 列表中批量导入链接，自动检测并移除重复条目，保留首次出现的记录。

- 自定义标签与分类体系：用户可为每条链接添加多个自定义标签，并支持创建层级分类目录，便于按主题、领域或紧急程度对资源进行多维度组织。

- 全文与元数据检索：内置基于标题、描述、标签及 URL 片段的轻量级搜索功能，支持布尔运算符与通配符匹配，快速定位目标链接。

- 快照与状态监控：自动记录每条链接的添加时间、最后访问时间及 HTTP 状态码，支持周期性检测链接有效性，标记失效或重定向的资源。

- 导入导出与备份恢复：提供 JSON、CSV 及 Markdown 列表格式的导出功能，支持全量备份与增量导入，便于在不同设备或团队之间同步数据。

- 静态站点生成：一键将当前链接库渲染为响应式 HTML 静态页面，可直接部署至任意 Web 服务器或托管平台，实现公开或私有的资源门户。

- 命令行与交互式双模式：既提供面向脚本自动化场景的命令行参数接口，也提供面向日常管理任务的交互式终端菜单，满足不同使用习惯。

## 应用场景

- 技术调研与竞品分析：研发团队在开展新技术选型或竞品功能对标时，通常需要收集大量官方文档、技术博客、社区讨论与性能测试报告。WebLink Navigator 能够帮助团队系统化归档这些分散的链接，并通过标签体系按产品、功能模块或评估维度进行分组，便于后续撰写调研报告时快速引用原始出处。

- 内容创作与参考文献管理：技术博主、开源文档撰写者或学术研究人员在创作过程中需引用大量外部资源。使用本工具可以构建个人参考文献库，为每篇稿件独立维护一组链接集合，输出时自动生成符合规范的引用列表，避免手动整理带来的遗漏或格式错误。

- 运维故障排查知识库：运维工程师在处理线上事故时，常需查阅内部 Wiki、监控面板、日志分析工具及厂商技术支持文档。通过将相关链接按故障类型、服务组件或严重等级分类归档，可逐步积累形成团队内部的故障排查知识索引，缩短平均修复时间。

- 自动化信息采集管道治理：在运行定时爬虫或 RSS 聚合服务时，系统会产生大量待处理或已处理的外链。WebLink Navigator 可作为管道中的中间治理节点，对原始链接进行去重、标注状态、记录抓取时间，并为下游分析模块提供规范化的输入数据。

## 快速开始

以下操作基于 Linux 或 macOS 环境，Windows 用户建议使用 WSL 或 Git Bash。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装 Python 依赖（Python 3.8 及以上）
pip install -r requirements.txt

# 初始化本地链接数据库（SQLite）
python scripts/init_db.py --force

# 导入示例链接列表（或替换为自己的 data/raw_links.txt）
python scripts/import_links.py --input data/sample_links.txt --tag sample

# 启动交互式终端管理界面
python main.py --interactive

# 生成静态站点至 output/ 目录
python main.py --generate-site --output-dir ./output
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 或更高 | 核心运行环境，用于执行所有脚本与管理逻辑 |
| SQLite | 3.28 或更高 | 内置轻量级关系数据库，用于存储链接元数据与索引 |
| Git | 2.20 或更高 | 用于克隆仓库及版本控制，非运行时强制依赖 |
| pip | 20.0 或更高 | Python 包管理工具，用于安装第三方依赖库 |
| requests | 2.25.0 或更高 | 用于发送 HTTP 请求检测链接状态与获取页面标题 |
| beautifulsoup4 | 4.9.0 或更高 | 用于解析 HTML 页面提取标题与描述元信息 |
| markdown | 3.3.0 或更高 | 用于将 Markdown 格式的注释渲染为 HTML 描述 |
| jinja2 | 3.0.0 或更高 | 静态站点生成时使用的模板引擎 |
| pytest | 6.0.0 或更高 | 仅开发与测试环境需要，用于运行单元测试套件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | docs/getting_started.md | 如何安装、配置并运行第一次链接导入；如何理解核心数据模型 |
| 功能 | docs/features.md | 每个功能模块的详细操作说明，包括标签管理、搜索语法与状态监控 |
| 配置 | docs/configuration.md | 环境变量配置项、数据库连接参数、静态站点生成选项 |
| API | docs/api_reference.md | 命令行接口的完整参数列表、Python 内部模块的调用示例与事件钩子 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/4612397.htm
- http://m.blog.gqskj.cn/nnews/9574465.htm
- http://m.blog.gqskj.cn/nnews/07750.htm
- http://m.blog.gqskj.cn/nnews/0734.htm
- http://m.blog.gqskj.cn/nnews/7917.htm
- http://m.blog.gqskj.cn/nnews/14049.htm
- http://m.blog.gqskj.cn/nnews/067308.htm
- http://m.blog.gqskj.cn/nnews/845487.htm
- http://m.blog.gqskj.cn/nnews/2480.htm
- http://m.blog.gqskj.cn/nnews/217958.htm
- http://m.blog.gqskj.cn/nnews/406983.htm
- http://m.blog.gqskj.cn/nnews/376932.htm
- http://m.blog.gqskj.cn/nnews/27693.htm
- http://m.blog.gqskj.cn/nnews/3949269.htm
- http://m.blog.gqskj.cn/nnews/199588.htm
- http://m.blog.gqskj.cn/nnews/8449783.htm
- http://m.blog.gqskj.cn/nnews/9054996.htm
- http://m.blog.gqskj.cn/nnews/5431936.htm
- http://m.blog.gqskj.cn/nnews/8308.htm
- http://m.blog.gqskj.cn/nnews/0491849.htm
- http://m.blog.gqskj.cn/nnews/5344.htm
- http://m.blog.gqskj.cn/nnews/4034149.htm
- http://m.blog.gqskj.cn/nnews/7904215.htm
- http://m.blog.gqskj.cn/nnews/1025.htm
- http://m.blog.gqskj.cn/nnews/3506440.htm
- http://m.blog.gqskj.cn/nnews/4234608.htm
- http://m.blog.gqskj.cn/nnews/1712370.htm
- http://m.blog.gqskj.cn/nnews/7248283.htm
- http://m.blog.gqskj.cn/nnews/6350520.htm
- http://m.blog.gqskj.cn/nnews/083143.htm
- http://m.blog.gqskj.cn/nnews/836158.htm
- http://m.blog.gqskj.cn/nnews/0201.htm
- http://m.blog.gqskj.cn/nnews/2710829.htm
- http://m.blog.gqskj.cn/nnews/2548336.htm
- http://m.blog.gqskj.cn/nnews/9049452.htm
- http://m.blog.gqskj.cn/nnews/3124.htm
- http://m.blog.gqskj.cn/nnews/751135.htm
- http://m.blog.gqskj.cn/nnews/51254.htm
- http://m.blog.gqskj.cn/nnews/6042.htm
- http://m.blog.gqskj.cn/nnews/6945.htm
- http://m.blog.gqskj.cn/nnews/32970.htm
- http://m.blog.gqskj.cn/nnews/87078.htm
- http://m.blog.gqskj.cn/nnews/079231.htm
- http://m.blog.gqskj.cn/nnews/0605172.htm
- http://m.blog.gqskj.cn/nnews/9937.htm
- http://m.blog.gqskj.cn/nnews/35421.htm
- http://m.blog.gqskj.cn/nnews/592942.htm
- http://m.blog.gqskj.cn/nnews/67313.htm
- http://m.blog.gqskj.cn/nnews/3987.htm
- http://m.blog.gqskj.cn/nnews/8977419.htm
- http://m.blog.gqskj.cn/nnews/8588366.htm
- http://m.blog.gqskj.cn/nnews/5058.htm
- http://m.blog.gqskj.cn/nnews/16684.htm
- http://m.blog.gqskj.cn/nnews/848373.htm
- http://m.blog.gqskj.cn/nnews/0819.htm
- http://m.blog.gqskj.cn/nnews/074931.htm
- http://m.blog.gqskj.cn/nnews/69099.htm
- http://m.blog.gqskj.cn/nnews/6326.htm
- http://m.blog.gqskj.cn/nnews/65604.htm
- http://m.blog.gqskj.cn/nnews/1986.htm
- http://m.blog.gqskj.cn/nnews/09656.htm
- http://m.blog.gqskj.cn/nnews/39856.htm
- http://m.blog.gqskj.cn/nnews/1572.htm
- http://m.blog.gqskj.cn/nnews/603548.htm
- http://m.blog.gqskj.cn/nnews/8554247.htm
- http://m.blog.gqskj.cn/nnews/2848.htm
- http://m.blog.gqskj.cn/nnews/1863618.htm
- http://m.blog.gqskj.cn/nnews/5925561.htm
- http://m.blog.gqskj.cn/nnews/11192.htm
- http://m.blog.gqskj.cn/nnews/379852.htm
- http://m.blog.gqskj.cn/nnews/279179.htm
- http://m.blog.gqskj.cn/nnews/9944828.htm
- http://m.blog.gqskj.cn/nnews/02562.htm
- http://m.blog.gqskj.cn/nnews/9394.htm
- http://m.blog.gqskj.cn/nnews/1222.htm
- http://m.blog.gqskj.cn/nnews/8222.htm
- http://m.blog.gqskj.cn/nnews/1477.htm
- http://m.blog.gqskj.cn/nnews/13308.htm
- http://m.blog.gqskj.cn/nnews/075416.htm
- http://m.blog.gqskj.cn/nnews/26542.htm
- http://m.blog.gqskj.cn/nnews/3822.htm
- http://m.blog.gqskj.cn/nnews/051501.htm
- http://m.blog.gqskj.cn/nnews/9979351.htm
- http://m.blog.gqskj.cn/nnews/9633021.htm
- http://m.blog.gqskj.cn/nnews/7558.htm
- http://m.blog.gqskj.cn/nnews/2100256.htm
- http://m.blog.gqskj.cn/nnews/111233.htm
- http://m.blog.gqskj.cn/nnews/8903.htm
- http://m.blog.gqskj.cn/nnews/56214.htm
- http://m.blog.gqskj.cn/nnews/56018.htm
- http://m.blog.gqskj.cn/nnews/921386.htm
- http://m.blog.gqskj.cn/nnews/05835.htm
- http://m.blog.gqskj.cn/nnews/7801700.htm
- http://m.blog.gqskj.cn/nnews/329122.htm
- http://m.blog.gqskj.cn/nnews/6585102.htm
- http://m.blog.gqskj.cn/nnews/3186322.htm
- http://m.blog.gqskj.cn/nnews/058013.htm
- http://m.blog.gqskj.cn/nnews/18368.htm
- http://m.blog.gqskj.cn/nnews/729094.htm
- http://m.blog.gqskj.cn/nnews/9762161.htm
- http://m.blog.gqskj.cn/nnews/2196.htm
- http://m.blog.gqskj.cn/nnews/4855850.htm
- http://m.blog.gqskj.cn/nnews/4155.htm
- http://m.blog.gqskj.cn/nnews/2098.htm
- http://m.blog.gqskj.cn/nnews/6971439.htm
- http://m.blog.gqskj.cn/nnews/9613.htm
- http://m.blog.gqskj.cn/nnews/1152.htm
- http://m.blog.gqskj.cn/nnews/6463080.htm
- http://m.blog.gqskj.cn/nnews/6490326.htm
- http://m.blog.gqskj.cn/nnews/3427913.htm
- http://m.blog.gqskj.cn/nnews/656649.htm
- http://m.blog.gqskj.cn/nnews/248298.htm
- http://m.blog.gqskj.cn/nnews/3951.htm
- http://m.blog.gqskj.cn/nnews/1490.htm
- http://m.blog.gqskj.cn/nnews/0337844.htm
- http://m.blog.gqskj.cn/nnews/1127.htm
- http://m.blog.gqskj.cn/nnews/3525478.htm
- http://m.blog.gqskj.cn/nnews/1537368.htm
- http://m.blog.gqskj.cn/nnews/6887324.htm
- http://m.blog.gqskj.cn/nnews/294364.htm
- http://m.blog.gqskj.cn/nnews/18728.htm
- http://m.blog.gqskj.cn/nnews/013309.htm
- http://m.blog.gqskj.cn/nnews/4175499.htm
- http://m.blog.gqskj.cn/nnews/83311.htm
- http://m.blog.gqskj.cn/nnews/4846109.htm
- http://m.blog.gqskj.cn/nnews/9535406.htm
- http://m.blog.gqskj.cn/nnews/0440607.htm
- http://m.blog.gqskj.cn/nnews/41895.htm
- http://m.blog.gqskj.cn/nnews/4013.htm
- http://m.blog.gqskj.cn/nnews/1296468.htm
- http://m.blog.gqskj.cn/nnews/94155.htm
- http://m.blog.gqskj.cn/nnews/571989.htm
- http://m.blog.gqskj.cn/nnews/9813.htm
- http://m.blog.gqskj.cn/nnews/970308.htm
- http://m.blog.gqskj.cn/nnews/4998766.htm
- http://m.blog.gqskj.cn/nnews/8762180.htm
- http://m.blog.gqskj.cn/nnews/4319052.htm
- http://m.blog.gqskj.cn/nnews/0145.htm
- http://m.blog.gqskj.cn/nnews/54036.htm
- http://m.blog.gqskj.cn/nnews/230724.htm
- http://m.blog.gqskj.cn/nnews/6560.htm
- http://m.blog.gqskj.cn/nnews/3185.htm
- http://m.blog.gqskj.cn/nnews/82411.htm
- http://m.blog.gqskj.cn/nnews/9427.htm
- http://m.blog.gqskj.cn/nnews/038964.htm
- http://m.blog.gqskj.cn/nnews/006466.htm
- http://m.blog.gqskj.cn/nnews/00656.htm
- http://m.blog.gqskj.cn/nnews/1068.htm
- http://m.blog.gqskj.cn/nnews/7792.htm
- http://m.blog.gqskj.cn/nnews/9146517.htm
- http://m.blog.gqskj.cn/nnews/6931.htm
- http://m.blog.gqskj.cn/nnews/95781.htm
- http://m.blog.gqskj.cn/nnews/53053.htm
- http://m.blog.gqskj.cn/nnews/164979.htm
- http://m.blog.gqskj.cn/nnews/9062836.htm
- http://m.blog.gqskj.cn/nnews/0846505.htm
- http://m.blog.gqskj.cn/nnews/98109.htm
- http://m.blog.gqskj.cn/nnews/243650.htm
- http://m.blog.gqskj.cn/nnews/7342745.htm
- http://m.blog.gqskj.cn/nnews/389987.htm
- http://m.blog.gqskj.cn/nnews/398113.htm
- http://m.blog.gqskj.cn/nnews/3882669.htm
- http://m.blog.gqskj.cn/nnews/6206341.htm
- http://m.blog.gqskj.cn/nnews/817393.htm
- http://m.blog.gqskj.cn/nnews/6223737.htm
- http://m.blog.gqskj.cn/nnews/26608.htm
- http://m.blog.gqskj.cn/nnews/2229842.htm
- http://m.blog.gqskj.cn/nnews/930659.htm
- http://m.blog.gqskj.cn/nnews/8197.htm
- http://m.blog.gqskj.cn/nnews/22667.htm
- http://m.blog.gqskj.cn/nnews/2740903.htm
- http://m.blog.gqskj.cn/nnews/2351.htm
- http://m.blog.gqskj.cn/nnews/893445.htm
- http://m.blog.gqskj.cn/nnews/6712622.htm
- http://m.blog.gqskj.cn/nnews/302317.htm
- http://m.blog.gqskj.cn/nnews/2397490.htm
- http://m.blog.gqskj.cn/nnews/0694007.htm
- http://m.blog.gqskj.cn/nnews/943263.htm
- http://m.blog.gqskj.cn/nnews/0948226.htm
- http://m.blog.gqskj.cn/nnews/0074925.htm
- http://m.blog.gqskj.cn/nnews/8442.htm
- http://m.blog.gqskj.cn/nnews/714645.htm
- http://m.blog.gqskj.cn/nnews/34280.htm
- http://m.blog.gqskj.cn/nnews/86944.htm
- http://m.blog.gqskj.cn/nnews/4531.htm
- http://m.blog.gqskj.cn/nnews/9535916.htm
- http://m.blog.gqskj.cn/nnews/559470.htm
- http://m.blog.gqskj.cn/nnews/7595588.htm
- http://m.blog.gqskj.cn/nnews/67007.htm
- http://m.blog.gqskj.cn/nnews/838614.htm
- http://m.blog.gqskj.cn/nnews/2324.htm
- http://m.blog.gqskj.cn/nnews/7845.htm
- http://m.blog.gqskj.cn/nnews/96156.htm
- http://m.blog.gqskj.cn/nnews/75852.htm
- http://m.blog.gqskj.cn/nnews/377832.htm
- http://m.blog.gqskj.cn/nnews/6151081.htm
- http://m.blog.gqskj.cn/nnews/36613.htm
- http://m.blog.gqskj.cn/nnews/5814.htm
- http://m.blog.gqskj.cn/nnews/5197.htm
- http://m.blog.gqskj.cn/nnews/1426.htm
- http://m.blog.gqskj.cn/nnews/23067.htm
- http://m.blog.gqskj.cn/nnews/602114.htm
- http://m.blog.gqskj.cn/nnews/6386.htm
- http://m.blog.gqskj.cn/nnews/9090497.htm
- http://m.blog.gqskj.cn/nnews/5420.htm
- http://m.blog.gqskj.cn/nnews/389667.htm
- http://m.blog.gqskj.cn/nnews/8077093.htm
- http://m.blog.gqskj.cn/nnews/042626.htm
- http://m.blog.gqskj.cn/nnews/215565.htm
- http://m.blog.gqskj.cn/nnews/2709594.htm
- http://m.blog.gqskj.cn/nnews/125769.htm
- http://m.blog.gqskj.cn/nnews/090144.htm
- http://m.blog.gqskj.cn/nnews/7444865.htm
- http://m.blog.gqskj.cn/nnews/0468196.htm
- http://m.blog.gqskj.cn/nnews/3368.htm
- http://m.blog.gqskj.cn/nnews/38265.htm
- http://m.blog.gqskj.cn/nnews/3415197.htm
- http://m.blog.gqskj.cn/nnews/2666201.htm
- http://m.blog.gqskj.cn/nnews/02897.htm
- http://m.blog.gqskj.cn/nnews/8988200.htm
- http://m.blog.gqskj.cn/nnews/32828.htm
- http://m.blog.gqskj.cn/nnews/67605.htm
- http://m.blog.gqskj.cn/nnews/3352197.htm
- http://m.blog.gqskj.cn/nnews/9366695.htm
- http://m.blog.gqskj.cn/nnews/3653.htm
- http://m.blog.gqskj.cn/nnews/4002.htm
- http://m.blog.gqskj.cn/nnews/15384.htm
- http://m.blog.gqskj.cn/nnews/847530.htm
- http://m.blog.gqskj.cn/nnews/42160.htm
- http://m.blog.gqskj.cn/nnews/62385.htm
- http://m.blog.gqskj.cn/nnews/4609.htm
- http://m.blog.gqskj.cn/nnews/6838890.htm
- http://m.blog.gqskj.cn/nnews/27468.htm
- http://m.blog.gqskj.cn/nnews/87467.htm
- http://m.blog.gqskj.cn/nnews/177457.htm
- http://m.blog.gqskj.cn/nnews/22099.htm
- http://m.blog.gqskj.cn/nnews/72711.htm
- http://m.blog.gqskj.cn/nnews/9123852.htm
- http://m.blog.gqskj.cn/nnews/5771139.htm
- http://m.blog.gqskj.cn/nnews/6667782.htm
- http://m.blog.gqskj.cn/nnews/37535.htm
- http://m.blog.gqskj.cn/nnews/7275125.htm
- http://m.blog.gqskj.cn/nnews/8890218.htm
- http://m.blog.gqskj.cn/nnews/885921.htm
- http://m.blog.gqskj.cn/nnews/4869.htm
- http://m.blog.gqskj.cn/nnews/7589602.htm
- http://m.blog.gqskj.cn/nnews/7680325.htm
- http://m.blog.gqskj.cn/nnews/7213.htm
- http://m.blog.gqskj.cn/nnews/09999.htm
- http://m.blog.gqskj.cn/nnews/80677.htm

## 项目结构

```
weblink-navigator/
├── main.py                  # 主入口脚本，支持命令行参数与交互式模式
├── requirements.txt         # Python 依赖清单，包含 requests、beautifulsoup4 等
├── config.yaml              # 全局配置文件，含数据库路径、日志级别与站点生成选项
├── data/
│   ├── raw_links.txt        # 用户导入的原始链接列表（每行一个 URL）
│   ├── sample_links.txt     # 示例数据，用于首次运行演示
│   └── backup/              # 自动备份目录，存放 JSON 格式的历史快照
├── src/
│   ├── core/
│   │   ├── db.py            # SQLite 数据库连接与基础 CRUD 操作
│   │   ├── importer.py      # 链接导入逻辑，含去重与元数据抽取
│   │   └── validator.py     # URL 格式校验与状态码检测
│   ├── models/
│   │   ├── link.py          # 链接数据模型定义（属性、序列化方法）
│   │   └── tag.py           # 标签与分类数据模型
│   ├── cli/
│   │   ├── commands.py      # 所有命令行子命令实现
│   │   └── interactive.py   # 交互式终端菜单会话管理
│   └── generators/
│       ├── static_site.py   # 静态 HTML 站点生成引擎
│       └── markdown_export.py # Markdown 列表导出功能
├── tests/
│   ├── unit/
│   │   ├── test_db.py       # 数据库操作单元测试
│   │   └── test_importer.py # 导入流程单元测试
│   └── fixtures/
│       └── test_links.txt   # 测试用固定链接数据集
├── templates/               # Jinja2 模板文件，用于静态站点渲染
│   ├── base.html
│   ├── index.html
│   └── detail.html
├── output/                  # 静态站点默认输出目录（gitignored）
├── docs/                    # 用户文档与 API 参考
│   ├── getting_started.md
│   ├── features.md
│   ├── configuration.md
│   └── api_reference.md
└── LICENSE                  # MIT 许可证文件
```

## 贡献指南

1. 阅读项目行为准则（CODE_OF_CONDUCT.md）与贡献者许可协议，确保认同项目社区规范。所有贡献者需签署开发者原创声明，确认所提交代码为本人原创且未侵犯第三方权益。

2. 在 GitHub Issues 中查找未被认领的任务，或提交新 Issue 描述建议的新功能或缺陷。涉及重大架构调整时，建议先通过 Discussion 发起设计提案，获得核心维护者反馈后再着手实现。

3. Fork 项目仓库，在个人分支上基于 develop 分支创建功能或修复分支。分支命名建议采用 `feature/功能简述` 或 `fix/问题编号-简述` 格式，确保提交历史清晰可追溯。

4. 编写或更新对应的单元测试用例，确保新代码的测试覆盖率达到 80% 以上。运行 `pytest tests/` 验证全部用例通过，且不引入回归问题。代码风格需符合 PEP 8 规范，可使用 black 或 flake8 进行自动检查和格式化。

5. 提交 Pull Request 至 develop 分支，在 PR 描述中清晰说明改动目的、实现方案及测试结果。PR 至少需要两名项目维护者审阅批准后方可合并。合并后 CI 流水线将自动构建并部署最新文档站点。

## 常见问题

Q: 导入的链接数量较大时，性能表现如何？
A: 系统采用分批提交策略，单次导入一万条链接的耗时约为 12 至 18 秒（取决于网络请求超时设置）。元数据抽取（如获取页面标题）默认启用异步并发请求，可通过 `--threads` 参数调节并发度。若仅需快速入库而不抓取页面信息，可启用 `--no-fetch` 模式跳过网络请求，此时导入速度可提升至每秒 2000 条以上。

Q: 静态站点生成后，如何实现私有化部署与访问控制？
A: 生成的站点为纯静态 HTML 文件，不包含任何后端逻辑或用户认证机制。若需限制访问，建议搭配 HTTP 基础认证（如 Nginx 的 auth_basic 模块）或部署在具备 IP 白名单功能的托管平台（如 GitHub Pages 配合企业版私有仓库）。项目本身不存储任何用户身份信息，所有数据完全本地化。

Q: 如何迁移已有书签或收藏夹数据到本系统？
A: 主流浏览器（Chrome、Firefox、Edge）支持将书签导出为 HTML 文件。项目中提供了 `scripts/convert_bookmarks.py` 转换脚本，可将此类 HTML 书签文件解析为系统支持的纯 URL 列表格式。对于其他格式（如 Pocket 导出 CSV、Raindrop.io JSON），建议先通过外部工具转换为每行一个 URL 的文本文件，再使用 `import_links.py` 导入。项目文档中提供了针对五种常见书签服务的数据迁移示例。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:46
