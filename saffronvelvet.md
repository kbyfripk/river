# WapNav 移动端外链导航系统

WapNav 是一个面向移动端的外链资源聚合与导航系统，专为需要快速检索、分类管理和批量分发外部链接资源的开发团队、内容运营者及研究机构设计。该项目将大量分散的移动端资讯链接、数据页面和文档资源统一纳入可检索、可监控、可扩展的导航框架，解决外链管理过程中链接散落、失效不可知、分类混乱的核心痛点。

WapNav 并非简单的书签集合，而是一套带有元数据提取、链接状态检测、访问频率统计和分类标签生成能力的轻量级导航引擎。目标用户包括技术文档维护人员、移动端内容聚合平台运营方、学术研究中的文献链接管理团队，以及任何需要系统化处理大量外链资源的个人或组织。

## 功能概览

批量外链导入与自动规范化处理：系统提供标准化导入接口，支持按批次、按来源域、按文件类型等多维度批量录入链接，并在入库时自动完成 URL 格式校验、去重和协议规范化建议。

链接状态主动检测与健康度标记：内置异步检测队列，周期性对已收录链接进行 HTTP 状态码检查、响应时间测量和页面标题抓取，将结果以健康度标签形式呈现。

多维分类标签与全文检索：每条链接可附加多个自定义标签，支持按域名、文件扩展名、预期内容类型和入库时间范围进行组合筛选，同时提供基于标题和 URL 关键词的全文检索。

访问热度统计与排序策略配置：记录每条链接的被访问次数、最后访问时间和平均响应耗时，支持按热度、新增时间或自定义权重进行列表排序。

外链数据快照与版本对比：每次检测任务执行时自动保存链接响应摘要，支持查看特定链接在不同时间点的状态变化，便于追踪资源迁移或内容更新。

开放数据导出与订阅机制：支持将筛选后的链接列表导出为 JSON、CSV 或纯文本格式，并提供简易的订阅端点，允许外部系统按标签或批次拉取最新链接清单。

移动端自适应展示视图：前端展示层针对手机屏幕优化，采用卡片式布局和触控友好的交互方式，确保在移动浏览器中浏览和检索链接的体验流畅。

访问日志与异常告警：记录每次链接被外部请求的详细日志，当单条链接连续多次检测失败或响应时间超过阈值时，通过日志文件和控制台输出告警提示。

## 应用场景

移动端内容聚合平台的日常链接维护：运营人员每日需要从多个来源收集资讯链接并分发至不同频道。WapNav 提供统一的导入入口和标签管理能力，使运营团队能够快速将新链接归类至对应频道，同时通过健康度检测自动筛选失效链接，减少人工巡检成本。

技术文档库的外链引用管理：技术文档中往往包含大量指向外部规范、工具仓库和参考文章的超链接。WapNav 可用于定期扫描文档项目中引用的所有外链，生成健康度报告，帮助文档维护者在发布前或定期巡检时发现并替换失效引用。

学术研究中的文献链接归档与共享：研究团队在文献综述阶段会收集大量论文链接、数据页面和项目主页。WapNav 支持按研究主题、文献类型和收录时间组织这些链接，并允许团队成员通过订阅机制获取最新的链接变更状态，避免因链接失效导致研究材料不可追溯。

个人开发者的知识库外链管理：独立开发者或技术博主在积累技术文章、工具站点和在线教程时，常面临链接散落在各处的问题。WapNav 可作为个人知识库的外链中枢，通过标签和检索快速定位所需资源，同时通过状态检测及时清理失效书签。

企业内部的合规性外链审计：部分企业需要对对外发布的内容中包含的外部链接进行合规性审查。WapNav 的访问日志和状态快照功能可记录每次检测的详细结果，为审计提供可追溯的链接状态数据。

## 快速开始

以下指令适用于 Linux 及 macOS 环境，Windows 用户可通过 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/example/wapnav.git

# 进入项目目录
cd wapnav

# 安装依赖（使用 pip 进行 Python 依赖安装）
pip install -r requirements.txt

# 初始化本地数据库和配置
python manage.py init --db sqlite

# 导入示例链接数据（用户提供的首批外链）
python manage.py import --batch 45 --source data/links_45.txt

# 启动本地开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

访问 http://localhost:8080 即可进入导航系统的管理界面。首次启动将自动创建默认管理员账户，用户名 admin，密码在启动日志中打印。生产环境部署请参考 docs/deployment.md。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，推荐使用 3.11 以获得最佳性能 |
| SQLite | 3.35.0 及以上 | 内置数据库引擎，用于存储链接元数据和检测结果；生产环境可切换至 PostgreSQL |
| requests | 2.31.0 及以上 | 用于执行外链 HTTP 检测和响应内容抓取 |
| beautifulsoup4 | 4.12.0 及以上 | 用于解析检测返回的 HTML 页面，提取标题和 meta 信息 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析后端，提供更快的 HTML 解析速度 |
| aiohttp | 3.8.0 及以上 | 用于并发执行大量链接的状态检测任务，提升检测效率 |
| click | 8.1.0 及以上 | 提供命令行交互接口，用于导入、导出和检测等管理操作 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、设置标签、执行检测和查看统计结果 |
| 运维指南 | docs/operations.md | 如何配置检测周期、调整并发数、切换生产数据库和备份数据 |
| API 参考 | docs/api-reference.md | 提供哪些外部调用接口、认证方式和数据格式规范 |
| 架构设计 | docs/architecture.md | 系统的模块划分、数据流转路径和扩展点设计说明 |

## 资源列表

- http://m.wap.fcful.cn/nnews/3678.htm
- http://m.wap.fcful.cn/nnews/0039771.htm
- http://m.wap.fcful.cn/nnews/76641.htm
- http://m.wap.fcful.cn/nnews/91092.htm
- http://m.wap.fcful.cn/nnews/9854.htm
- http://m.wap.fcful.cn/nnews/2905697.htm
- http://m.wap.fcful.cn/nnews/893382.htm
- http://m.wap.fcful.cn/nnews/9834.htm
- http://m.wap.fcful.cn/nnews/76187.htm
- http://m.wap.fcful.cn/nnews/32741.htm
- http://m.wap.fcful.cn/nnews/151426.htm
- http://m.wap.fcful.cn/nnews/662115.htm
- http://m.wap.fcful.cn/nnews/8828220.htm
- http://m.wap.fcful.cn/nnews/11697.htm
- http://m.wap.fcful.cn/nnews/9481.htm
- http://m.wap.fcful.cn/nnews/305424.htm
- http://m.wap.fcful.cn/nnews/4137.htm
- http://m.wap.fcful.cn/nnews/131623.htm
- http://m.wap.fcful.cn/nnews/6492015.htm
- http://m.wap.fcful.cn/nnews/676230.htm
- http://m.wap.fcful.cn/nnews/1550500.htm
- http://m.wap.fcful.cn/nnews/60439.htm
- http://m.wap.fcful.cn/nnews/525627.htm
- http://m.wap.fcful.cn/nnews/844326.htm
- http://m.wap.fcful.cn/nnews/0805115.htm
- http://m.wap.fcful.cn/nnews/2426167.htm
- http://m.wap.fcful.cn/nnews/781830.htm
- http://m.wap.fcful.cn/nnews/1446.htm
- http://m.wap.fcful.cn/nnews/1827059.htm
- http://m.wap.fcful.cn/nnews/8328684.htm
- http://m.wap.fcful.cn/nnews/114787.htm
- http://m.wap.fcful.cn/nnews/02164.htm
- http://m.wap.fcful.cn/nnews/3935.htm
- http://m.wap.fcful.cn/nnews/7823.htm
- http://m.wap.fcful.cn/nnews/875022.htm
- http://m.wap.fcful.cn/nnews/8360.htm
- http://m.wap.fcful.cn/nnews/151613.htm
- http://m.wap.fcful.cn/nnews/8377229.htm
- http://m.wap.fcful.cn/nnews/445656.htm
- http://m.wap.fcful.cn/nnews/528186.htm
- http://m.wap.fcful.cn/nnews/987258.htm
- http://m.wap.fcful.cn/nnews/4927.htm
- http://m.wap.fcful.cn/nnews/43300.htm
- http://m.wap.fcful.cn/nnews/7064.htm
- http://m.wap.fcful.cn/nnews/525793.htm
- http://m.wap.fcful.cn/nnews/4847.htm
- http://m.wap.fcful.cn/nnews/7353.htm
- http://m.wap.fcful.cn/nnews/5369.htm
- http://m.wap.fcful.cn/nnews/80473.htm
- http://m.wap.fcful.cn/nnews/9243849.htm
- http://m.wap.fcful.cn/nnews/0954.htm
- http://m.wap.fcful.cn/nnews/80604.htm
- http://m.wap.fcful.cn/nnews/9091126.htm
- http://m.wap.fcful.cn/nnews/4990.htm
- http://m.wap.fcful.cn/nnews/3147.htm
- http://m.wap.fcful.cn/nnews/62298.htm
- http://m.wap.fcful.cn/nnews/428938.htm
- http://m.wap.fcful.cn/nnews/6299.htm
- http://m.wap.fcful.cn/nnews/12030.htm
- http://m.wap.fcful.cn/nnews/50019.htm
- http://m.wap.fcful.cn/nnews/7487046.htm
- http://m.wap.fcful.cn/nnews/6912559.htm
- http://m.wap.fcful.cn/nnews/6221136.htm
- http://m.wap.fcful.cn/nnews/6607861.htm
- http://m.wap.fcful.cn/nnews/6253.htm
- http://m.wap.fcful.cn/nnews/1069.htm
- http://m.wap.fcful.cn/nnews/8492537.htm
- http://m.wap.fcful.cn/nnews/8446687.htm
- http://m.wap.fcful.cn/nnews/9783148.htm
- http://m.wap.fcful.cn/nnews/14410.htm
- http://m.wap.fcful.cn/nnews/42712.htm
- http://m.wap.fcful.cn/nnews/4500.htm
- http://m.wap.fcful.cn/nnews/24646.htm
- http://m.wap.fcful.cn/nnews/7805623.htm
- http://m.wap.fcful.cn/nnews/73173.htm
- http://m.wap.fcful.cn/nnews/12927.htm
- http://m.wap.fcful.cn/nnews/0968.htm
- http://m.wap.fcful.cn/nnews/084827.htm
- http://m.wap.fcful.cn/nnews/3423.htm
- http://m.wap.fcful.cn/nnews/75285.htm
- http://m.wap.fcful.cn/nnews/646779.htm
- http://m.wap.fcful.cn/nnews/291444.htm
- http://m.wap.fcful.cn/nnews/7143956.htm
- http://m.wap.fcful.cn/nnews/14801.htm
- http://m.wap.fcful.cn/nnews/917309.htm
- http://m.wap.fcful.cn/nnews/3738.htm
- http://m.wap.fcful.cn/nnews/85783.htm
- http://m.wap.fcful.cn/nnews/8639953.htm
- http://m.wap.fcful.cn/nnews/6639.htm
- http://m.wap.fcful.cn/nnews/5101.htm
- http://m.wap.fcful.cn/nnews/820054.htm
- http://m.wap.fcful.cn/nnews/42318.htm
- http://m.wap.fcful.cn/nnews/415001.htm
- http://m.wap.fcful.cn/nnews/642624.htm
- http://m.wap.fcful.cn/nnews/3494.htm
- http://m.wap.fcful.cn/nnews/618747.htm
- http://m.wap.fcful.cn/nnews/3471.htm
- http://m.wap.fcful.cn/nnews/2466.htm
- http://m.wap.fcful.cn/nnews/34674.htm
- http://m.wap.fcful.cn/nnews/767139.htm
- http://m.wap.fcful.cn/nnews/5299544.htm
- http://m.wap.fcful.cn/nnews/797289.htm
- http://m.wap.fcful.cn/nnews/318702.htm
- http://m.wap.fcful.cn/nnews/2352940.htm
- http://m.wap.fcful.cn/nnews/3755013.htm
- http://m.wap.fcful.cn/nnews/9117.htm
- http://m.wap.fcful.cn/nnews/2958.htm
- http://m.wap.fcful.cn/nnews/5419093.htm
- http://m.wap.fcful.cn/nnews/62559.htm
- http://m.wap.fcful.cn/nnews/8289473.htm
- http://m.wap.fcful.cn/nnews/56852.htm
- http://m.wap.fcful.cn/nnews/746362.htm
- http://m.wap.fcful.cn/nnews/0937569.htm
- http://m.wap.fcful.cn/nnews/254806.htm
- http://m.wap.fcful.cn/nnews/7140650.htm
- http://m.wap.fcful.cn/nnews/1706753.htm
- http://m.wap.fcful.cn/nnews/4386658.htm
- http://m.wap.fcful.cn/nnews/65070.htm
- http://m.wap.fcful.cn/nnews/169287.htm
- http://m.wap.fcful.cn/nnews/0353457.htm
- http://m.wap.fcful.cn/nnews/899920.htm
- http://m.wap.fcful.cn/nnews/43581.htm
- http://m.wap.fcful.cn/nnews/028843.htm
- http://m.wap.fcful.cn/nnews/3540.htm
- http://m.wap.fcful.cn/nnews/918846.htm
- http://m.wap.fcful.cn/nnews/593142.htm
- http://m.wap.fcful.cn/nnews/34505.htm
- http://m.wap.fcful.cn/nnews/344863.htm
- http://m.wap.fcful.cn/nnews/38935.htm
- http://m.wap.fcful.cn/nnews/364114.htm
- http://m.wap.fcful.cn/nnews/86377.htm
- http://m.wap.fcful.cn/nnews/6814399.htm
- http://m.wap.fcful.cn/nnews/70803.htm
- http://m.wap.fcful.cn/nnews/88177.htm
- http://m.wap.fcful.cn/nnews/479003.htm
- http://m.wap.fcful.cn/nnews/8390.htm
- http://m.wap.fcful.cn/nnews/2399.htm
- http://m.wap.fcful.cn/nnews/45286.htm
- http://m.wap.fcful.cn/nnews/25100.htm
- http://m.wap.fcful.cn/nnews/4607673.htm
- http://m.wap.fcful.cn/nnews/16006.htm
- http://m.wap.fcful.cn/nnews/933744.htm
- http://m.wap.fcful.cn/nnews/28734.htm
- http://m.wap.fcful.cn/nnews/0458.htm
- http://m.wap.fcful.cn/nnews/915966.htm
- http://m.wap.fcful.cn/nnews/4429.htm
- http://m.wap.fcful.cn/nnews/25449.htm
- http://m.wap.fcful.cn/nnews/70946.htm
- http://m.wap.fcful.cn/nnews/1148257.htm
- http://m.wap.fcful.cn/nnews/38704.htm
- http://m.wap.fcful.cn/nnews/5220341.htm
- http://m.wap.fcful.cn/nnews/1623192.htm
- http://m.wap.fcful.cn/nnews/8372287.htm
- http://m.wap.fcful.cn/nnews/3465755.htm
- http://m.wap.fcful.cn/nnews/9761.htm
- http://m.wap.fcful.cn/nnews/1159484.htm
- http://m.wap.fcful.cn/nnews/0414.htm
- http://m.wap.fcful.cn/nnews/368161.htm
- http://m.wap.fcful.cn/nnews/5929.htm
- http://m.wap.fcful.cn/nnews/74569.htm
- http://m.wap.fcful.cn/nnews/20240.htm
- http://m.wap.fcful.cn/nnews/2215254.htm
- http://m.wap.fcful.cn/nnews/925276.htm
- http://m.wap.fcful.cn/nnews/3017397.htm
- http://m.wap.fcful.cn/nnews/5110566.htm
- http://m.wap.fcful.cn/nnews/8181497.htm
- http://m.wap.fcful.cn/nnews/6313527.htm
- http://m.wap.fcful.cn/nnews/8038.htm
- http://m.wap.fcful.cn/nnews/3836703.htm
- http://m.wap.fcful.cn/nnews/9816.htm
- http://m.wap.fcful.cn/nnews/350971.htm
- http://m.wap.fcful.cn/nnews/2976.htm
- http://m.wap.fcful.cn/nnews/296001.htm
- http://m.wap.fcful.cn/nnews/801013.htm
- http://m.wap.fcful.cn/nnews/68322.htm
- http://m.wap.fcful.cn/nnews/1628606.htm
- http://m.wap.fcful.cn/nnews/0156.htm
- http://m.wap.fcful.cn/nnews/35990.htm
- http://m.wap.fcful.cn/nnews/886322.htm
- http://m.wap.fcful.cn/nnews/8123.htm
- http://m.wap.fcful.cn/nnews/3594320.htm
- http://m.wap.fcful.cn/nnews/4852275.htm
- http://m.wap.fcful.cn/nnews/19413.htm
- http://m.wap.fcful.cn/nnews/469149.htm
- http://m.wap.fcful.cn/nnews/0139062.htm
- http://m.wap.fcful.cn/nnews/53356.htm
- http://m.wap.fcful.cn/nnews/08794.htm
- http://m.wap.fcful.cn/nnews/665516.htm
- http://m.wap.fcful.cn/nnews/11863.htm
- http://m.wap.fcful.cn/nnews/4481438.htm
- http://m.wap.fcful.cn/nnews/9244227.htm
- http://m.wap.fcful.cn/nnews/4401112.htm
- http://m.wap.fcful.cn/nnews/3336.htm
- http://m.wap.fcful.cn/nnews/785042.htm
- http://m.wap.fcful.cn/nnews/8771.htm
- http://m.wap.fcful.cn/nnews/02267.htm
- http://m.wap.fcful.cn/nnews/673355.htm
- http://m.wap.fcful.cn/nnews/627396.htm
- http://m.wap.fcful.cn/nnews/7406912.htm
- http://m.wap.fcful.cn/nnews/9152.htm
- http://m.wap.fcful.cn/nnews/1673530.htm
- http://m.wap.fcful.cn/nnews/604464.htm
- http://m.wap.fcful.cn/nnews/9267928.htm
- http://m.wap.fcful.cn/nnews/70396.htm
- http://m.wap.fcful.cn/nnews/6459.htm
- http://m.wap.fcful.cn/nnews/1924.htm
- http://m.wap.fcful.cn/nnews/35223.htm
- http://m.wap.fcful.cn/nnews/52972.htm
- http://m.wap.fcful.cn/nnews/9007830.htm
- http://m.wap.fcful.cn/nnews/6621.htm
- http://m.wap.fcful.cn/nnews/41290.htm
- http://m.wap.fcful.cn/nnews/0998.htm
- http://m.wap.fcful.cn/nnews/7274034.htm
- http://m.wap.fcful.cn/nnews/9288.htm
- http://m.wap.fcful.cn/nnews/26373.htm
- http://m.wap.fcful.cn/nnews/036382.htm
- http://m.wap.fcful.cn/nnews/842889.htm
- http://m.wap.fcful.cn/nnews/297276.htm
- http://m.wap.fcful.cn/nnews/4350.htm
- http://m.wap.fcful.cn/nnews/334593.htm
- http://m.wap.fcful.cn/nnews/748066.htm
- http://m.wap.fcful.cn/nnews/36060.htm
- http://m.wap.fcful.cn/nnews/881684.htm
- http://m.wap.fcful.cn/nnews/6390770.htm
- http://m.wap.fcful.cn/nnews/345998.htm
- http://m.wap.fcful.cn/nnews/4838.htm
- http://m.wap.fcful.cn/nnews/9504.htm
- http://m.wap.fcful.cn/nnews/063310.htm
- http://m.wap.fcful.cn/nnews/177858.htm
- http://m.wap.fcful.cn/nnews/009186.htm
- http://m.wap.fcful.cn/nnews/389158.htm
- http://m.wap.fcful.cn/nnews/0616843.htm
- http://m.wap.fcful.cn/nnews/3973053.htm
- http://m.wap.fcful.cn/nnews/78884.htm
- http://m.wap.fcful.cn/nnews/297595.htm
- http://m.wap.fcful.cn/nnews/1655746.htm
- http://m.wap.fcful.cn/nnews/5508.htm
- http://m.wap.fcful.cn/nnews/172816.htm
- http://m.wap.fcful.cn/nnews/2277.htm
- http://m.wap.fcful.cn/nnews/3916760.htm
- http://m.wap.fcful.cn/nnews/6231417.htm
- http://m.wap.fcful.cn/nnews/38393.htm
- http://m.wap.fcful.cn/nnews/9674740.htm
- http://m.wap.fcful.cn/nnews/672139.htm
- http://m.wap.fcful.cn/nnews/4077108.htm
- http://m.wap.fcful.cn/nnews/64890.htm
- http://m.wap.fcful.cn/nnews/2757.htm
- http://m.wap.fcful.cn/nnews/6854.htm
- http://m.wap.fcful.cn/nnews/4963.htm
- http://m.wap.fcful.cn/nnews/2208077.htm

## 项目结构

```
wapnav/
├── manage.py                 # 项目统一管理入口，集成初始化、导入、检测和导出命令
├── requirements.txt          # Python 依赖声明文件，锁定所有必需库的版本范围
├── config/                   # 全局配置目录
│   ├── settings.py           # 主配置文件，包含数据库连接、检测超时、并发数等参数
│   ├── logging.conf          # 日志格式、输出级别和滚动策略配置
│   └── schema.sql            # 数据库表结构定义，用于手动初始化或迁移参考
├── core/                     # 核心业务逻辑模块
│   ├── engine.py             # 检测引擎实现，负责调度异步请求和结果聚合
│   ├── parser.py             # 页面解析器，从响应中提取标题、编码和元数据
│   ├── classifier.py         # 分类器，基于 URL 特征和响应内容生成标签建议
│   └── storage.py            # 数据库访问抽象层，封装增删改查及批量操作
├── web/                      # Web 界面与 API 模块
│   ├── app.py                # Flask 应用工厂，注册路由和中间件
│   ├── routes/               # 路由蓝图集合
│   │   ├── index.py          # 主页面及链接列表展示路由
│   │   ├── detail.py         # 单条链接详情及历史状态展示路由
│   │   ├── import_export.py  # 批量导入与导出接口路由
│   │   └── api.py            # 对外 REST API，支持查询、订阅和状态回调
│   └── static/               # 前端静态资源
│       ├── css/              # 移动端自适应样式表
│       └── js/               # 前端交互逻辑，包含列表筛选和排序功能
├── scripts/                  # 运维与辅助脚本
│   ├── batch_check.py        # 批量检测任务触发脚本，支持 cron 定时调用
│   ├── export_snapshot.py    # 导出指定批次或标签的全量数据快照
│   └── migrate_db.py         # 数据库版本迁移脚本，用于结构升级
├── data/                     # 数据目录
│   ├── links_45.txt          # 第 45 批次导入的原始链接列表
│   ├── cache/                # 检测结果缓存，用于加速重复查询
│   └── logs/                 # 运行日志、访问日志和检测异常日志
└── tests/                    # 单元测试与集成测试
    ├── test_engine.py        # 检测引擎各分支逻辑的测试用例
    ├── test_parser.py        # 解析器对不同 HTML 结构的适应性测试
    └── test_api.py           # API 接口的请求响应正确性测试
```

## 贡献指南

1. 在 GitHub 或 Gitee 上 fork 本项目仓库，并 clone 到本地开发环境。建议在 dev 分支上基于最新 main 分支创建功能分支，分支命名采用 feat/xxx 或 fix/xxx 格式。

2. 完成代码修改后，运行 tests 目录下的全部测试用例确保无回归问题。新增功能需附带对应的单元测试，测试覆盖率不低于 80%。提交前执行 make lint 进行代码风格检查，本项目遵循 PEP 8 规范。

3. 提交 pull request 时请填写清晰的变更说明，包括解决的问题、涉及的功能模块和测试结果摘要。对于影响现有配置或数据库结构的变更，需在说明中标注兼容性处理方式。

4. 文档更新随代码提交一同进行，用户手册、API 参考和架构说明需同步反映功能变更。所有新增配置项必须在 settings.py 和对应的文档中同时添加注释和说明。

5. 贡献者需遵守项目行为准则，尊重已有代码风格和模块边界。对于大规模重构或新增独立模块的建议，建议先在 issue 中发起讨论，获得核心维护者反馈后再投入开发。

## 常见问题

Q: 检测引擎是否支持 HTTPS 站点？导入的链接全是 HTTP 协议，但实际目标可能支持 HTTPS，系统如何处理？

A: 检测引擎默认使用导入时记录的协议进行请求。若链接实际支持 HTTPS 且 HTTP 请求返回重定向或状态码异常，系统会在检测日志中记录建议协议升级的提示。用户可在管理界面手动将单条链接切换为 HTTPS 协议，或通过批量更新命令将所有指向同一域名的链接统一升级。系统不会自动改写协议，以避免非预期行为。

Q: 导入 250 条链接后，检测任务需要多长时间完成？是否会影响浏览器端的访问速度？

A: 单次全量检测的耗时取决于网络状况和并发数配置。默认配置下，250 条链接的首次检测通常在 30 至 60 秒内完成。检测引擎运行在独立的后台进程或异步任务队列中，与 Web 前端响应线程隔离，不会阻塞管理界面的正常访问。用户可通过 config/settings.py 中的 CHECK_CONCURRENCY 参数调整并发数，以平衡检测速度和系统资源占用。

Q: 如何迁移现有的 SQLite 数据到生产环境的 PostgreSQL 数据库？

A: 项目提供了 migrate_db 脚本，支持从 SQLite 导出全量数据并导入至 PostgreSQL。执行前需在 config/settings.py 中将 DATABASE_URL 修改为 PostgreSQL 的连接字符串，然后运行 python scripts/migrate_db.py --export sqlite:///wapnav.db --import postgresql://user:pass@host/dbname。迁移完成后建议手动核对链接总数和最新检测时间，确保数据完整。迁移过程中原有 SQLite 数据不会被自动删除，可作为备份保留。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
