# GQSKJ News Aggregator

GQSKJ News Aggregator 是一个面向移动端的信息聚合与导航系统，专注于对 gqskj.cn 域名下分散的新闻与资讯条目进行统一索引、分类整理与快速检索。该项目主要服务于需要从大量非结构化短新闻链接中提取有效信息的研究人员、内容运营团队以及自动化采集系统开发者。

本项目不提供内容抓取与存储功能，而是作为链接资源的组织与分发层，通过清晰的目录结构和标准化的访问方式，帮助用户高效管理第 162/240 批次的 250 个目标资源。项目核心定位为轻量级外链索引服务，适用于个人知识库构建、垂直领域资讯监控以及第三方系统的数据源接入场景。

## 功能概览

**批量链接导入** 支持通过命令行工具一次性导入用户提供的全部 URL 列表，自动完成去重与格式校验。

**分类标签生成** 基于 URL 路径中的数字标识符，自动为每个链接生成分类标签，便于按主题分组浏览。

**移动端自适应索引页** 提供针对手机屏幕优化的 HTML 索引页面，支持按发布时间、标题关键词和分类筛选。

**定时健康检查** 内置链接可用性检测模块，可配置定时任务检查每个资源是否仍可访问，并生成异常报告。

**导出为多种格式** 支持将索引数据导出为 JSON、CSV 和 RSS 订阅源格式，方便对接第三方阅读器或数据分析工具。

**本地搜索接口** 提供基于关键词的本地搜索功能，支持模糊匹配和布尔运算符组合查询。

**增量更新机制** 当新增资源链接时，仅更新变更部分而不重建全量索引，提升维护效率。

## 应用场景

**垂直领域资讯监控** 内容运营人员可将本系统作为中间层，定期导入特定主题的链接列表，通过分类标签快速筛选出感兴趣的文章，无需逐个点开原始页面查看。

**自动化采集系统的种子库** 数据采集工程师可将本系统导出的 RSS 或 JSON 数据作为爬虫的起始 URL 池，配合健康检查功能自动剔除死链，提高采集任务的稳定性。

**个人知识库的引用源管理** 研究人员在整理文献或技术笔记时，可通过本项目的导出功能将外部链接统一归档，并利用本地搜索接口快速检索已收录的资源。

**团队协作的链接共享平台** 小型团队可在内网部署本系统，成员各自导入发现的资源链接，系统自动合并并生成统一的索引页，减少信息孤岛。

## 快速开始

以下命令适用于 Linux 和 macOS 环境，Windows 用户可使用 Git Bash 或 WSL 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/gqskj-news-aggregator.git
cd gqskj-news-aggregator

# 安装依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 初始化数据库并导入示例数据
python scripts/init_db.py
python scripts/import_urls.py --input data/urls_162.txt

# 启动本地服务
python app.py --host 0.0.0.0 --port 8080
```

启动成功后，访问 http://localhost:8080 即可查看索引页面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9.0 或更高 | 核心运行环境，建议使用 3.11 以上以获得性能提升 |
| SQLite | 3.35.0 或更高 | 内置轻量级数据库，用于存储链接元数据和索引状态 |
| requests | 2.28.0 或更高 | 用于健康检查模块的 HTTP 请求发送 |
| beautifulsoup4 | 4.11.0 或更高 | 可选依赖，用于解析索引页生成时的标题提取 |
| Flask | 2.2.0 或更高 | Web 服务框架，仅在启用可视化索引页时需要 |
| tqdm | 4.64.0 或更高 | 用于批量导入时的进度条显示 |
| pytest | 7.1.0 或更高 | 仅开发测试环境需要 |
| black | 22.3.0 或更高 | 仅代码格式化时需要 |
| flake8 | 5.0.0 或更高 | 仅代码风格检查时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何导入链接、如何生成索引页、如何使用搜索功能 |
| 部署指南 | docs/deployment.md | 如何在生产环境部署、如何配置定时健康检查、如何设置反向代理 |
| 开发者文档 | docs/developer.md | 项目代码结构、核心模块说明、如何扩展新的导出格式 |
| 运维参考 | docs/operations.md | 数据库备份策略、日志管理、性能调优参数说明 |

## 资源列表

- http://m.wap.gqskj.cn/snews/2992.htm
- http://m.wap.gqskj.cn/snews/329871.htm
- http://m.wap.gqskj.cn/snews/10821.htm
- http://m.wap.gqskj.cn/snews/3426.htm
- http://m.wap.gqskj.cn/snews/9997372.htm
- http://m.wap.gqskj.cn/snews/8816538.htm
- http://m.wap.gqskj.cn/snews/664676.htm
- http://m.wap.gqskj.cn/snews/41520.htm
- http://m.wap.gqskj.cn/snews/6599.htm
- http://m.wap.gqskj.cn/snews/5540.htm
- http://m.wap.gqskj.cn/snews/399285.htm
- http://m.wap.gqskj.cn/snews/4087.htm
- http://m.wap.gqskj.cn/snews/648847.htm
- http://m.wap.gqskj.cn/snews/5284936.htm
- http://m.wap.gqskj.cn/snews/14123.htm
- http://m.wap.gqskj.cn/snews/5186.htm
- http://m.wap.gqskj.cn/snews/304888.htm
- http://m.wap.gqskj.cn/snews/1339636.htm
- http://m.wap.gqskj.cn/snews/7138343.htm
- http://m.wap.gqskj.cn/snews/178403.htm
- http://m.wap.gqskj.cn/snews/670028.htm
- http://m.wap.gqskj.cn/snews/6111.htm
- http://m.wap.gqskj.cn/snews/807636.htm
- http://m.wap.gqskj.cn/snews/6381.htm
- http://m.wap.gqskj.cn/snews/16615.htm
- http://m.wap.gqskj.cn/snews/681167.htm
- http://m.wap.gqskj.cn/snews/0682718.htm
- http://m.wap.gqskj.cn/snews/12893.htm
- http://m.wap.gqskj.cn/snews/881589.htm
- http://m.wap.gqskj.cn/snews/77526.htm
- http://m.wap.gqskj.cn/snews/733822.htm
- http://m.wap.gqskj.cn/snews/13867.htm
- http://m.wap.gqskj.cn/snews/81521.htm
- http://m.wap.gqskj.cn/snews/032677.htm
- http://m.wap.gqskj.cn/snews/80961.htm
- http://m.wap.gqskj.cn/snews/938754.htm
- http://m.wap.gqskj.cn/snews/518305.htm
- http://m.wap.gqskj.cn/snews/9126514.htm
- http://m.wap.gqskj.cn/snews/9676.htm
- http://m.wap.gqskj.cn/snews/827814.htm
- http://m.wap.gqskj.cn/snews/5550.htm
- http://m.wap.gqskj.cn/snews/31095.htm
- http://m.wap.gqskj.cn/snews/4148636.htm
- http://m.wap.gqskj.cn/snews/1578.htm
- http://m.wap.gqskj.cn/snews/554500.htm
- http://m.wap.gqskj.cn/snews/38180.htm
- http://m.wap.gqskj.cn/snews/37041.htm
- http://m.wap.gqskj.cn/snews/4618.htm
- http://m.wap.gqskj.cn/snews/57519.htm
- http://m.wap.gqskj.cn/snews/382835.htm
- http://m.wap.gqskj.cn/snews/175011.htm
- http://m.wap.gqskj.cn/snews/8960.htm
- http://m.wap.gqskj.cn/snews/211856.htm
- http://m.wap.gqskj.cn/snews/9565370.htm
- http://m.wap.gqskj.cn/snews/6126327.htm
- http://m.wap.gqskj.cn/snews/7005.htm
- http://m.wap.gqskj.cn/snews/8325734.htm
- http://m.wap.gqskj.cn/snews/71009.htm
- http://m.wap.gqskj.cn/snews/1926056.htm
- http://m.wap.gqskj.cn/snews/754987.htm
- http://m.wap.gqskj.cn/snews/36969.htm
- http://m.wap.gqskj.cn/snews/141496.htm
- http://m.wap.gqskj.cn/snews/52015.htm
- http://m.wap.gqskj.cn/snews/14380.htm
- http://m.wap.gqskj.cn/snews/1432679.htm
- http://m.wap.gqskj.cn/snews/4730.htm
- http://m.wap.gqskj.cn/snews/6264250.htm
- http://m.wap.gqskj.cn/snews/9004738.htm
- http://m.wap.gqskj.cn/snews/07305.htm
- http://m.wap.gqskj.cn/snews/97031.htm
- http://m.wap.gqskj.cn/snews/0248.htm
- http://m.wap.gqskj.cn/snews/6884.htm
- http://m.wap.gqskj.cn/snews/5383.htm
- http://m.wap.gqskj.cn/snews/9276483.htm
- http://m.wap.gqskj.cn/snews/1484945.htm
- http://m.wap.gqskj.cn/snews/00242.htm
- http://m.wap.gqskj.cn/snews/90993.htm
- http://m.wap.gqskj.cn/snews/0162.htm
- http://m.wap.gqskj.cn/snews/4878.htm
- http://m.wap.gqskj.cn/snews/0984001.htm
- http://m.wap.gqskj.cn/snews/2566.htm
- http://m.wap.gqskj.cn/snews/9368.htm
- http://m.wap.gqskj.cn/snews/7415005.htm
- http://m.wap.gqskj.cn/snews/0996040.htm
- http://m.wap.gqskj.cn/snews/1150.htm
- http://m.wap.gqskj.cn/snews/41951.htm
- http://m.wap.gqskj.cn/snews/89011.htm
- http://m.wap.gqskj.cn/snews/0910.htm
- http://m.wap.gqskj.cn/snews/0529413.htm
- http://m.wap.gqskj.cn/snews/3213398.htm
- http://m.wap.gqskj.cn/snews/60620.htm
- http://m.wap.gqskj.cn/snews/9840613.htm
- http://m.wap.gqskj.cn/snews/105149.htm
- http://m.wap.gqskj.cn/snews/5845565.htm
- http://m.wap.gqskj.cn/snews/2145222.htm
- http://m.wap.gqskj.cn/snews/5166.htm
- http://m.wap.gqskj.cn/snews/5495350.htm
- http://m.wap.gqskj.cn/snews/8598454.htm
- http://m.wap.gqskj.cn/snews/38850.htm
- http://m.wap.gqskj.cn/snews/8747337.htm
- http://m.wap.gqskj.cn/snews/738422.htm
- http://m.wap.gqskj.cn/snews/96712.htm
- http://m.wap.gqskj.cn/snews/549050.htm
- http://m.wap.gqskj.cn/snews/4805736.htm
- http://m.wap.gqskj.cn/snews/40637.htm
- http://m.wap.gqskj.cn/snews/52778.htm
- http://m.wap.gqskj.cn/snews/38035.htm
- http://m.wap.gqskj.cn/snews/2195512.htm
- http://m.wap.gqskj.cn/snews/417617.htm
- http://m.wap.gqskj.cn/snews/10142.htm
- http://m.wap.gqskj.cn/snews/856182.htm
- http://m.wap.gqskj.cn/snews/02377.htm
- http://m.wap.gqskj.cn/snews/35301.htm
- http://m.wap.gqskj.cn/snews/7479164.htm
- http://m.wap.gqskj.cn/snews/1627.htm
- http://m.wap.gqskj.cn/snews/17498.htm
- http://m.wap.gqskj.cn/snews/02577.htm
- http://m.wap.gqskj.cn/snews/0656006.htm
- http://m.wap.gqskj.cn/snews/12638.htm
- http://m.wap.gqskj.cn/snews/064655.htm
- http://m.wap.gqskj.cn/snews/791596.htm
- http://m.wap.gqskj.cn/snews/708135.htm
- http://m.wap.gqskj.cn/snews/3155.htm
- http://m.wap.gqskj.cn/snews/62552.htm
- http://m.wap.gqskj.cn/snews/6664.htm
- http://m.wap.gqskj.cn/snews/178723.htm
- http://m.wap.gqskj.cn/snews/311930.htm
- http://m.wap.gqskj.cn/snews/842744.htm
- http://m.wap.gqskj.cn/snews/051387.htm
- http://m.wap.gqskj.cn/snews/14963.htm
- http://m.wap.gqskj.cn/snews/81975.htm
- http://m.wap.gqskj.cn/snews/46082.htm
- http://m.wap.gqskj.cn/snews/5912020.htm
- http://m.wap.gqskj.cn/snews/0077050.htm
- http://m.wap.gqskj.cn/snews/59112.htm
- http://m.wap.gqskj.cn/snews/3070647.htm
- http://m.wap.gqskj.cn/snews/797922.htm
- http://m.wap.gqskj.cn/snews/1051563.htm
- http://m.wap.gqskj.cn/snews/4645770.htm
- http://m.wap.gqskj.cn/snews/205768.htm
- http://m.wap.gqskj.cn/snews/404405.htm
- http://m.wap.gqskj.cn/snews/08098.htm
- http://m.wap.gqskj.cn/snews/7528.htm
- http://m.wap.gqskj.cn/snews/1604986.htm
- http://m.wap.gqskj.cn/snews/62891.htm
- http://m.wap.gqskj.cn/snews/4137.htm
- http://m.wap.gqskj.cn/snews/5193.htm
- http://m.wap.gqskj.cn/snews/0966680.htm
- http://m.wap.gqskj.cn/snews/482436.htm
- http://m.wap.gqskj.cn/snews/29561.htm
- http://m.wap.gqskj.cn/snews/910607.htm
- http://m.wap.gqskj.cn/snews/2583.htm
- http://m.wap.gqskj.cn/snews/0167.htm
- http://m.wap.gqskj.cn/snews/6552.htm
- http://m.wap.gqskj.cn/snews/1867763.htm
- http://m.wap.gqskj.cn/snews/1756.htm
- http://m.wap.gqskj.cn/snews/6789.htm
- http://m.wap.gqskj.cn/snews/5748150.htm
- http://m.wap.gqskj.cn/snews/789632.htm
- http://m.wap.gqskj.cn/snews/55890.htm
- http://m.wap.gqskj.cn/snews/2462493.htm
- http://m.wap.gqskj.cn/snews/195960.htm
- http://m.wap.gqskj.cn/snews/41599.htm
- http://m.wap.gqskj.cn/snews/1501668.htm
- http://m.wap.gqskj.cn/snews/4050.htm
- http://m.wap.gqskj.cn/snews/268020.htm
- http://m.wap.gqskj.cn/snews/2072.htm
- http://m.wap.gqskj.cn/snews/9403.htm
- http://m.wap.gqskj.cn/snews/68283.htm
- http://m.wap.gqskj.cn/snews/21992.htm
- http://m.wap.gqskj.cn/snews/694636.htm
- http://m.wap.gqskj.cn/snews/3533704.htm
- http://m.wap.gqskj.cn/snews/7999.htm
- http://m.wap.gqskj.cn/snews/4653349.htm
- http://m.wap.gqskj.cn/snews/138393.htm
- http://m.wap.gqskj.cn/snews/7262.htm
- http://m.wap.gqskj.cn/snews/1058201.htm
- http://m.wap.gqskj.cn/snews/3583.htm
- http://m.wap.gqskj.cn/snews/7121.htm
- http://m.wap.gqskj.cn/snews/158464.htm
- http://m.wap.gqskj.cn/snews/5090.htm
- http://m.wap.gqskj.cn/snews/7362525.htm
- http://m.wap.gqskj.cn/snews/03418.htm
- http://m.wap.gqskj.cn/snews/08194.htm
- http://m.wap.gqskj.cn/snews/1796.htm
- http://m.wap.gqskj.cn/snews/0432312.htm
- http://m.wap.gqskj.cn/snews/8728.htm
- http://m.wap.gqskj.cn/snews/678693.htm
- http://m.wap.gqskj.cn/snews/08000.htm
- http://m.wap.gqskj.cn/snews/31631.htm
- http://m.wap.gqskj.cn/snews/66151.htm
- http://m.wap.gqskj.cn/snews/771782.htm
- http://m.wap.gqskj.cn/snews/225358.htm
- http://m.wap.gqskj.cn/snews/34755.htm
- http://m.wap.gqskj.cn/snews/8851254.htm
- http://m.wap.gqskj.cn/snews/4990.htm
- http://m.wap.gqskj.cn/snews/9893830.htm
- http://m.wap.gqskj.cn/snews/03734.htm
- http://m.wap.gqskj.cn/snews/87620.htm
- http://m.wap.gqskj.cn/snews/5953.htm
- http://m.wap.gqskj.cn/snews/38821.htm
- http://m.wap.gqskj.cn/snews/696161.htm
- http://m.wap.gqskj.cn/snews/50458.htm
- http://m.wap.gqskj.cn/snews/8428.htm
- http://m.wap.gqskj.cn/snews/9424148.htm
- http://m.wap.gqskj.cn/snews/93537.htm
- http://m.wap.gqskj.cn/snews/7997736.htm
- http://m.wap.gqskj.cn/snews/206455.htm
- http://m.wap.gqskj.cn/snews/0427.htm
- http://m.wap.gqskj.cn/snews/8325660.htm
- http://m.wap.gqskj.cn/snews/495396.htm
- http://m.wap.gqskj.cn/snews/5703.htm
- http://m.wap.gqskj.cn/snews/37814.htm
- http://m.wap.gqskj.cn/snews/7665169.htm
- http://m.wap.gqskj.cn/snews/5362.htm
- http://m.wap.gqskj.cn/snews/000492.htm
- http://m.wap.gqskj.cn/snews/45248.htm
- http://m.wap.gqskj.cn/snews/463396.htm
- http://m.wap.gqskj.cn/snews/9937.htm
- http://m.wap.gqskj.cn/snews/38973.htm
- http://m.wap.gqskj.cn/snews/03723.htm
- http://m.wap.gqskj.cn/snews/1513.htm
- http://m.wap.gqskj.cn/snews/3019425.htm
- http://m.wap.gqskj.cn/snews/48326.htm
- http://m.wap.gqskj.cn/snews/8006.htm
- http://m.wap.gqskj.cn/snews/79559.htm
- http://m.wap.gqskj.cn/snews/8900.htm
- http://m.wap.gqskj.cn/snews/5943.htm
- http://m.wap.gqskj.cn/snews/5782709.htm
- http://m.wap.gqskj.cn/snews/42789.htm
- http://m.wap.gqskj.cn/snews/9375478.htm
- http://m.wap.gqskj.cn/snews/54585.htm
- http://m.wap.gqskj.cn/snews/120406.htm
- http://m.wap.gqskj.cn/snews/888025.htm
- http://m.wap.gqskj.cn/snews/0324.htm
- http://m.wap.gqskj.cn/snews/5744982.htm
- http://m.wap.gqskj.cn/snews/87147.htm
- http://m.wap.gqskj.cn/snews/521732.htm
- http://m.wap.gqskj.cn/snews/53969.htm
- http://m.wap.gqskj.cn/snews/494468.htm
- http://m.wap.gqskj.cn/snews/1717380.htm
- http://m.wap.gqskj.cn/snews/314135.htm
- http://m.wap.gqskj.cn/snews/56794.htm
- http://m.wap.gqskj.cn/snews/482240.htm
- http://m.wap.gqskj.cn/snews/87903.htm
- http://m.wap.gqskj.cn/snews/25157.htm
- http://m.wap.gqskj.cn/snews/3023.htm
- http://m.wap.gqskj.cn/snews/6523389.htm
- http://m.wap.gqskj.cn/snews/99397.htm
- http://m.wap.gqskj.cn/snews/0503951.htm

## 项目结构

```
gqskj-news-aggregator/
├── app.py                     # Web 服务主入口，启动 Flask 应用
├── requirements.txt           # Python 依赖声明文件
├── config/
│   ├── default.py             # 默认配置参数，包含端口、数据库路径等
│   └── production.py          # 生产环境覆盖配置，可独立调整
├── core/
│   ├── __init__.py
│   ├── importer.py            # 批量导入模块，解析文本列表并写入数据库
│   ├── indexer.py             # 索引生成模块，构建分类和搜索倒排表
│   ├── checker.py             # 健康检查模块，异步验证链接可用性
│   └── exporter.py            # 导出模块，支持 JSON / CSV / RSS 格式
├── data/
│   ├── urls_162.txt           # 第 162 批原始链接列表文件
│   └── index.db               # SQLite 数据库文件，自动创建
├── scripts/
│   ├── init_db.py             # 初始化数据库表结构
│   ├── import_urls.py         # 命令行导入脚本，接受 --input 参数
│   └── run_checker.py         # 手动触发健康检查的脚本
├── templates/
│   └── index.html             # 移动端自适应索引页模板
├── static/
│   └── style.css              # 索引页配套样式文件
├── tests/
│   ├── test_importer.py       # 导入模块的单元测试
│   ├── test_checker.py        # 健康检查模块的单元测试
│   └── test_exporter.py       # 导出模块的单元测试
└── docs/
    ├── user_guide.md          # 用户手册
    ├── deployment.md          # 部署指南
    ├── developer.md           # 开发者文档
    └── operations.md          # 运维参考
```

## 贡献指南

1. 从 GitHub Issues 页面认领尚未分配的任务，或提交新的 Issue 描述你发现的问题或建议的新功能。在开始编码前，建议先与维护者沟通确认需求方向。

2. 派生本项目到你的个人账户，然后在本地创建特性分支。分支命名建议采用 `feature/功能简述` 或 `fix/问题编号` 的格式，以便于追踪。

3. 提交代码前，请确保运行 `pytest tests/` 通过所有已有测试用例，并为新增功能补充对应的单元测试。同时使用 `black` 和 `flake8` 格式化代码并检查风格。

4. 提交 Pull Request 时，请清晰描述改动内容、关联的 Issue 编号以及测试覆盖情况。PR 描述中应包含足够的信息供维护者审阅。

5. 文档更新要求：任何新增功能或接口变更，必须同步更新对应的用户手册或开发者文档。纯文档类修改可直接提交 PR，无需关联代码变更。

## 常见问题

**问：导入时提示重复链接，系统会如何处理？**

答：导入模块会自动检测数据库中已存在的 URL。对于重复链接，系统默认跳过并记录警告日志，不会覆盖已有记录。如需强制更新已有链接的元数据，可在导入命令中添加 `--overwrite` 参数。

**问：健康检查模块的检测频率如何配置？**

答：健康检查的默认检测间隔为 24 小时，可在 `config/default.py` 中修改 `CHECK_INTERVAL_HOURS` 变量。生产环境建议通过系统的定时任务工具（如 cron 或 systemd timer）调用 `scripts/run_checker.py`，以获得更精确的调度控制。

**问：索引页的搜索功能支持哪些查询语法？**

答：本地搜索接口支持多个关键词以空格分隔的 AND 查询，输入 `关键词A 关键词B` 表示同时包含两者。使用 `|` 符号分隔表示 OR 查询，例如 `关键词A | 关键词B`。同时支持前缀匹配，输入 `技术*` 可以匹配以"技术"开头的所有条目。纯数字查询会优先匹配 URL 中的数字标识符。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
