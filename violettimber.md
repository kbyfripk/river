# WebWap 技术外链归档系统 (WebWap Link Archive)

WebWap 是一个面向移动端资讯聚合与技术文档外链管理的开源归档系统。该项目旨在解决技术社区中优质外链资源分散、移动端访问适配性差以及链接失效追踪困难等问题。系统通过结构化的数据抓取与索引机制，将分散在移动互联网各处的技术文章、新闻动态及开发文档进行统一归档与分类管理，为开发者、技术研究员及内容策展人提供可靠的外链数据中台。

本项目并非传统意义上的爬虫框架，而是一套完整的链接状态监控与元数据提取解决方案。它内置了移动端页面适配解析引擎，能够自动识别 wap 站点的内容结构，提取标题、发布时间、正文摘要及关联标签。通过批次化管理模式（当前为第 52/240 批），用户可以清晰地追踪每一批新增资源链接的存活状态与内容变更情况，从而在海量的网络信息中构建有序的知识索引。

## 功能概览

**批量链接导入与解析**：支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入外链，系统自动去重并识别域名归属。

**移动站点内容适配**：针对 wap 域名及移动端页面特征进行模板化解析，自动处理分页、重定向及反爬策略，提取核心文本内容。

**链接状态健康监测**：周期性检查已归档链接的 HTTP 状态码、响应时间及页面哈希值变更，及时发现 404、302 跳转或内容篡改。

**元数据智能标签生成**：基于标题与正文内容利用 TF-IDF 算法自动生成分类标签，支持手动修正标签层级以建立知识图谱。

**全文检索与高级筛选**：提供针对标题、URL、批次号、状态码及时间范围的多条件组合检索，支持搜索结果导出为 JSON 或 Markdown 格式。

**批次管理与版本对比**：每一批导入的链接作为独立版本存储，支持对比不同批次之间链接的重叠度与状态变化趋势。

**数据可视化看板**：提供链接状态分布饼图、每日新增趋势折线图以及来源域名 Top 10 排行榜，辅助运维决策。

**开放 API 接口**：基于 RESTful 风格提供外部调用接口，允许第三方系统拉取归档数据或推送新链接。

## 应用场景

**技术文档版本追踪**：当技术团队需要长期追踪特定框架或工具的官方文档更新时，可将文档入口链接录入系统。WebWap 会定期检查页面变动，一旦检测到版本号或内容区块更新，立即通过邮件通知订阅者，确保团队始终基于最新文档进行开发。

**移动端资讯聚合站后端**：内容创作者或自媒体运营者可以使用该项目作为数据源管理后台。将分散在不同移动资讯站点的参考链接统一入库，利用系统的标签分类功能快速筛选出相关主题素材，自动生成带原文链接与摘要的每日简报。

**网站迁移与重构验证**：在进行网站域名更换或前后端架构升级时，运维人员将旧站所有 URL 导入 WebWap，系统持续监测旧链接的 301/302 跳转目标以及最终的 200 状态码。通过对比批次报告，确保所有流量入口均正确指向新站对应页面，避免 SEO 权丢失。

**学术研究与数据溯源**：研究人员在进行网络传播学或舆论分析课题时，需要保存特定时间段内移动端文章的原始链接与快照。WebWap 提供批次冻结功能，可将某一批次的链接状态与摘要固定为只读版本，作为论文附录的数据支撑材料。

## 快速开始

以下步骤将指导您在三分钟内于本地环境启动 WebWap 服务。

```bash
# 1. 克隆项目仓库至本地
git clone https://github.com/webwap-archive/webwap-system.git
cd webwap-system

# 2. 安装 Python 依赖项（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 环境请使用 venv\Scripts\activate
pip install -r requirements.txt

# 3. 初始化 SQLite 数据库并运行服务
python manage.py migrate
python manage.py runserver --batch=52 --port=8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 及以上 | 核心运行环境，用于异步任务调度与数据处理 |
| SQLite | 3.35.0 及以上 | 默认轻量级数据库，用于存储链接元数据及批次信息 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于执行外链状态检测与页面内容拉取 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于移动端页面正文提取与标签清理 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析引擎，作为 BeautifulSoup 的底层解析器 |
| redis | 6.2.0 及以上 | 可选组件，用于分布式任务队列缓存（生产环境推荐） |
| gunicorn | 20.1.0 及以上 | 生产环境 WSGI 服务器，用于并发处理 API 请求 |
| nodejs | 16.0.0 及以上 | 仅当启用前端仪表盘构建时需要，用于编译静态资源 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | /docs/user-guide/ | 如何导入第一批链接？状态监测报告在哪里查看？如何配置邮件通知？ |
| 运维指南 | /docs/ops-guide/ | 如何更换数据库为 PostgreSQL？定时任务如何设置？如何扩容工作节点？ |
| 开发文档 | /docs/dev-guide/ | 如何编写新的站点适配器？API 鉴权机制是怎样的？如何提交 Pull Request？ |
| 设计概述 | /docs/design/ | 系统架构图是怎样的？批次快照的实现原理？标签生成算法选型依据？ |

## 资源列表

- http://m.wap.fcful.cn/nnews/857158.htm
- http://m.wap.fcful.cn/nnews/33283.htm
- http://m.wap.fcful.cn/nnews/7036.htm
- http://m.wap.fcful.cn/nnews/9269.htm
- http://m.wap.fcful.cn/nnews/8736158.htm
- http://m.wap.fcful.cn/nnews/342882.htm
- http://m.wap.fcful.cn/nnews/540586.htm
- http://m.wap.fcful.cn/nnews/942103.htm
- http://m.wap.fcful.cn/nnews/44263.htm
- http://m.wap.fcful.cn/nnews/71147.htm
- http://m.wap.fcful.cn/nnews/1795.htm
- http://m.wap.fcful.cn/nnews/0569811.htm
- http://m.wap.fcful.cn/nnews/9056.htm
- http://m.wap.fcful.cn/nnews/8494631.htm
- http://m.wap.fcful.cn/nnews/930862.htm
- http://m.wap.fcful.cn/nnews/0382.htm
- http://m.wap.fcful.cn/nnews/186813.htm
- http://m.wap.fcful.cn/nnews/87905.htm
- http://m.wap.fcful.cn/nnews/416717.htm
- http://m.wap.fcful.cn/nnews/738557.htm
- http://m.wap.fcful.cn/nnews/81947.htm
- http://m.wap.fcful.cn/nnews/0002719.htm
- http://m.wap.fcful.cn/nnews/37914.htm
- http://m.wap.fcful.cn/nnews/69361.htm
- http://m.wap.fcful.cn/nnews/470588.htm
- http://m.wap.fcful.cn/nnews/6521.htm
- http://m.wap.fcful.cn/nnews/23190.htm
- http://m.wap.fcful.cn/nnews/6845802.htm
- http://m.wap.fcful.cn/nnews/80158.htm
- http://m.wap.fcful.cn/nnews/1172.htm
- http://m.wap.fcful.cn/nnews/7019668.htm
- http://m.wap.fcful.cn/nnews/8320.htm
- http://m.wap.fcful.cn/nnews/3578672.htm
- http://m.wap.fcful.cn/nnews/893549.htm
- http://m.wap.fcful.cn/nnews/7525.htm
- http://m.wap.fcful.cn/nnews/2486530.htm
- http://m.wap.fcful.cn/nnews/08149.htm
- http://m.wap.fcful.cn/nnews/91244.htm
- http://m.wap.fcful.cn/nnews/5142.htm
- http://m.wap.fcful.cn/nnews/251619.htm
- http://m.wap.fcful.cn/nnews/1499929.htm
- http://m.wap.fcful.cn/nnews/07503.htm
- http://m.wap.fcful.cn/nnews/86894.htm
- http://m.wap.fcful.cn/nnews/60550.htm
- http://m.wap.fcful.cn/nnews/21845.htm
- http://m.wap.fcful.cn/nnews/4746.htm
- http://m.wap.fcful.cn/nnews/6450.htm
- http://m.wap.fcful.cn/nnews/0463.htm
- http://m.wap.fcful.cn/nnews/66610.htm
- http://m.wap.fcful.cn/nnews/2755.htm
- http://m.wap.fcful.cn/nnews/6290600.htm
- http://m.wap.fcful.cn/nnews/86001.htm
- http://m.wap.fcful.cn/nnews/5242216.htm
- http://m.wap.fcful.cn/nnews/3519590.htm
- http://m.wap.fcful.cn/nnews/65771.htm
- http://m.wap.fcful.cn/nnews/9309249.htm
- http://m.wap.fcful.cn/nnews/7860.htm
- http://m.wap.fcful.cn/nnews/90298.htm
- http://m.wap.fcful.cn/nnews/455146.htm
- http://m.wap.fcful.cn/nnews/10756.htm
- http://m.wap.fcful.cn/nnews/151958.htm
- http://m.wap.fcful.cn/nnews/6823317.htm
- http://m.wap.fcful.cn/nnews/89980.htm
- http://m.wap.fcful.cn/nnews/4688147.htm
- http://m.wap.fcful.cn/nnews/491183.htm
- http://m.wap.fcful.cn/nnews/2696.htm
- http://m.wap.fcful.cn/nnews/8475.htm
- http://m.wap.fcful.cn/nnews/438610.htm
- http://m.wap.fcful.cn/nnews/06685.htm
- http://m.wap.fcful.cn/nnews/7494797.htm
- http://m.wap.fcful.cn/nnews/237132.htm
- http://m.wap.fcful.cn/nnews/906117.htm
- http://m.wap.fcful.cn/nnews/86341.htm
- http://m.wap.fcful.cn/nnews/9518.htm
- http://m.wap.fcful.cn/nnews/6542752.htm
- http://m.wap.fcful.cn/nnews/926045.htm
- http://m.wap.fcful.cn/nnews/9134546.htm
- http://m.wap.fcful.cn/nnews/43206.htm
- http://m.wap.fcful.cn/nnews/4306.htm
- http://m.wap.fcful.cn/nnews/279477.htm
- http://m.wap.fcful.cn/nnews/798587.htm
- http://m.wap.fcful.cn/nnews/1776694.htm
- http://m.wap.fcful.cn/nnews/561889.htm
- http://m.wap.fcful.cn/nnews/280122.htm
- http://m.wap.fcful.cn/nnews/167186.htm
- http://m.wap.fcful.cn/nnews/10709.htm
- http://m.wap.fcful.cn/nnews/42119.htm
- http://m.wap.fcful.cn/nnews/402563.htm
- http://m.wap.fcful.cn/nnews/93712.htm
- http://m.wap.fcful.cn/nnews/0633.htm
- http://m.wap.fcful.cn/nnews/5230.htm
- http://m.wap.fcful.cn/nnews/54334.htm
- http://m.wap.fcful.cn/nnews/540818.htm
- http://m.wap.fcful.cn/nnews/8549.htm
- http://m.wap.fcful.cn/nnews/071035.htm
- http://m.wap.fcful.cn/nnews/8081.htm
- http://m.wap.fcful.cn/nnews/3284251.htm
- http://m.wap.fcful.cn/nnews/7345479.htm
- http://m.wap.fcful.cn/nnews/98391.htm
- http://m.wap.fcful.cn/nnews/7134.htm
- http://m.wap.fcful.cn/nnews/4357764.htm
- http://m.wap.fcful.cn/nnews/969449.htm
- http://m.wap.fcful.cn/nnews/66184.htm
- http://m.wap.fcful.cn/nnews/40078.htm
- http://m.wap.fcful.cn/nnews/5305884.htm
- http://m.wap.fcful.cn/nnews/9678357.htm
- http://m.wap.fcful.cn/nnews/0818511.htm
- http://m.wap.fcful.cn/nnews/8573.htm
- http://m.wap.fcful.cn/nnews/9705.htm
- http://m.wap.fcful.cn/nnews/9191995.htm
- http://m.wap.fcful.cn/nnews/4867.htm
- http://m.wap.fcful.cn/nnews/9306108.htm
- http://m.wap.fcful.cn/nnews/7124143.htm
- http://m.wap.fcful.cn/nnews/391844.htm
- http://m.wap.fcful.cn/nnews/9337786.htm
- http://m.wap.fcful.cn/nnews/172831.htm
- http://m.wap.fcful.cn/nnews/3551.htm
- http://m.wap.fcful.cn/nnews/028303.htm
- http://m.wap.fcful.cn/nnews/21320.htm
- http://m.wap.fcful.cn/nnews/2558647.htm
- http://m.wap.fcful.cn/nnews/09018.htm
- http://m.wap.fcful.cn/nnews/4227485.htm
- http://m.wap.fcful.cn/nnews/0905.htm
- http://m.wap.fcful.cn/nnews/9602576.htm
- http://m.wap.fcful.cn/nnews/591467.htm
- http://m.wap.fcful.cn/nnews/68409.htm
- http://m.wap.fcful.cn/nnews/310820.htm
- http://m.wap.fcful.cn/nnews/2085602.htm
- http://m.wap.fcful.cn/nnews/567416.htm
- http://m.wap.fcful.cn/nnews/6525110.htm
- http://m.wap.fcful.cn/nnews/2669.htm
- http://m.wap.fcful.cn/nnews/9165.htm
- http://m.wap.fcful.cn/nnews/688801.htm
- http://m.wap.fcful.cn/nnews/16236.htm
- http://m.wap.fcful.cn/nnews/3965.htm
- http://m.wap.fcful.cn/nnews/2652047.htm
- http://m.wap.fcful.cn/nnews/75466.htm
- http://m.wap.fcful.cn/nnews/4666.htm
- http://m.wap.fcful.cn/nnews/98572.htm
- http://m.wap.fcful.cn/nnews/8507409.htm
- http://m.wap.fcful.cn/nnews/78497.htm
- http://m.wap.fcful.cn/nnews/487175.htm
- http://m.wap.fcful.cn/nnews/9873031.htm
- http://m.wap.fcful.cn/nnews/4259.htm
- http://m.wap.fcful.cn/nnews/1087170.htm
- http://m.wap.fcful.cn/nnews/9917.htm
- http://m.wap.fcful.cn/nnews/80272.htm
- http://m.wap.fcful.cn/nnews/736729.htm
- http://m.wap.fcful.cn/nnews/831768.htm
- http://m.wap.fcful.cn/nnews/7595.htm
- http://m.wap.fcful.cn/nnews/652666.htm
- http://m.wap.fcful.cn/nnews/913778.htm
- http://m.wap.fcful.cn/nnews/394213.htm
- http://m.wap.fcful.cn/nnews/32489.htm
- http://m.wap.fcful.cn/nnews/1896.htm
- http://m.wap.fcful.cn/nnews/9393236.htm
- http://m.wap.fcful.cn/nnews/1345484.htm
- http://m.wap.fcful.cn/nnews/969475.htm
- http://m.wap.fcful.cn/nnews/5404988.htm
- http://m.wap.fcful.cn/nnews/3248.htm
- http://m.wap.fcful.cn/nnews/085790.htm
- http://m.wap.fcful.cn/nnews/4804473.htm
- http://m.wap.fcful.cn/nnews/6249275.htm
- http://m.wap.fcful.cn/nnews/279473.htm
- http://m.wap.fcful.cn/nnews/8247200.htm
- http://m.wap.fcful.cn/nnews/9595914.htm
- http://m.wap.fcful.cn/nnews/5292.htm
- http://m.wap.fcful.cn/nnews/5912.htm
- http://m.wap.fcful.cn/nnews/3414654.htm
- http://m.wap.fcful.cn/nnews/6145450.htm
- http://m.wap.fcful.cn/nnews/6809.htm
- http://m.wap.fcful.cn/nnews/27934.htm
- http://m.wap.fcful.cn/nnews/21847.htm
- http://m.wap.fcful.cn/nnews/8446522.htm
- http://m.wap.fcful.cn/nnews/59070.htm
- http://m.wap.fcful.cn/nnews/9398536.htm
- http://m.wap.fcful.cn/nnews/32439.htm
- http://m.wap.fcful.cn/nnews/75023.htm
- http://m.wap.fcful.cn/nnews/4554778.htm
- http://m.wap.fcful.cn/nnews/5713126.htm
- http://m.wap.fcful.cn/nnews/6528075.htm
- http://m.wap.fcful.cn/nnews/8022.htm
- http://m.wap.fcful.cn/nnews/3649.htm
- http://m.wap.fcful.cn/nnews/4640555.htm
- http://m.wap.fcful.cn/nnews/158790.htm
- http://m.wap.fcful.cn/nnews/245334.htm
- http://m.wap.fcful.cn/nnews/5040.htm
- http://m.wap.fcful.cn/nnews/74129.htm
- http://m.wap.fcful.cn/nnews/0978.htm
- http://m.wap.fcful.cn/nnews/1258.htm
- http://m.wap.fcful.cn/nnews/14481.htm
- http://m.wap.fcful.cn/nnews/4062.htm
- http://m.wap.fcful.cn/nnews/79166.htm
- http://m.wap.fcful.cn/nnews/405582.htm
- http://m.wap.fcful.cn/nnews/7841.htm
- http://m.wap.fcful.cn/nnews/9820335.htm
- http://m.wap.fcful.cn/nnews/22843.htm
- http://m.wap.fcful.cn/nnews/5125.htm
- http://m.wap.fcful.cn/nnews/9051.htm
- http://m.wap.fcful.cn/nnews/55053.htm
- http://m.wap.fcful.cn/nnews/7497.htm
- http://m.wap.fcful.cn/nnews/0233.htm
- http://m.wap.fcful.cn/nnews/2708789.htm
- http://m.wap.fcful.cn/nnews/91427.htm
- http://m.wap.fcful.cn/nnews/4022.htm
- http://m.wap.fcful.cn/nnews/3993.htm
- http://m.wap.fcful.cn/nnews/00347.htm
- http://m.wap.fcful.cn/nnews/57181.htm
- http://m.wap.fcful.cn/nnews/0834.htm
- http://m.wap.fcful.cn/nnews/3700.htm
- http://m.wap.fcful.cn/nnews/31859.htm
- http://m.wap.fcful.cn/nnews/393213.htm
- http://m.wap.fcful.cn/nnews/574142.htm
- http://m.wap.fcful.cn/nnews/89281.htm
- http://m.wap.fcful.cn/nnews/13501.htm
- http://m.wap.fcful.cn/nnews/66165.htm
- http://m.wap.fcful.cn/nnews/20829.htm
- http://m.wap.fcful.cn/nnews/5191947.htm
- http://m.wap.fcful.cn/nnews/078335.htm
- http://m.wap.fcful.cn/nnews/8723129.htm
- http://m.wap.fcful.cn/nnews/4527.htm
- http://m.wap.fcful.cn/nnews/39712.htm
- http://m.wap.fcful.cn/nnews/888772.htm
- http://m.wap.fcful.cn/nnews/4478258.htm
- http://m.wap.fcful.cn/nnews/5425.htm
- http://m.wap.fcful.cn/nnews/03238.htm
- http://m.wap.fcful.cn/nnews/7601973.htm
- http://m.wap.fcful.cn/nnews/67463.htm
- http://m.wap.fcful.cn/nnews/8314748.htm
- http://m.wap.fcful.cn/nnews/613320.htm
- http://m.wap.fcful.cn/nnews/5987368.htm
- http://m.wap.fcful.cn/nnews/315871.htm
- http://m.wap.fcful.cn/nnews/8519.htm
- http://m.wap.fcful.cn/nnews/1911.htm
- http://m.wap.fcful.cn/nnews/5345442.htm
- http://m.wap.fcful.cn/nnews/4217455.htm
- http://m.wap.fcful.cn/nnews/73990.htm
- http://m.wap.fcful.cn/nnews/1854.htm
- http://m.wap.fcful.cn/nnews/4011616.htm
- http://m.wap.fcful.cn/nnews/91398.htm
- http://m.wap.fcful.cn/nnews/3606573.htm
- http://m.wap.fcful.cn/nnews/12911.htm
- http://m.wap.fcful.cn/nnews/78828.htm
- http://m.wap.fcful.cn/nnews/203736.htm
- http://m.wap.fcful.cn/nnews/579428.htm
- http://m.wap.fcful.cn/nnews/6032.htm
- http://m.wap.fcful.cn/nnews/838266.htm
- http://m.wap.fcful.cn/nnews/0781906.htm
- http://m.wap.fcful.cn/nnews/84221.htm
- http://m.wap.fcful.cn/nnews/85648.htm

## 项目结构

```text
webwap-system/
├── archive/                            # 核心归档引擎模块
│   ├── adapters/                       # 站点适配器目录
│   │   ├── wap_base.py                 # Wap 站点基础适配类，定义通用解析流程
│   │   └── fcful.py                    # fcful.cn 域名特定解析规则与字段映射
│   ├── fetcher.py                      # 异步请求调度器，控制并发与超时重试
│   └── parser.py                       # HTML 内容解析管道，集成 lxml 与正则提取
├── batches/                            # 批次管理子系统
│   ├── manager.py                      # 批次生命周期控制（创建、冻结、对比）
│   └── v52/                            # 第 52 批数据隔离目录（含快照与摘要）
│       ├── manifest.json               # 批次元数据（导入时间、总数、状态）
│       └── raw_links.txt               # 原始链接列表备份
├── core/                               # 系统核心配置与通用工具
│   ├── settings.py                     # 全局配置（数据库连接、监测间隔、邮件服务器）
│   ├── models.py                       # SQLAlchemy 数据模型定义（Link, Batch, Tag）
│   └── utils.py                        # 通用辅助函数（哈希计算、日期格式化）
├── dashboard/                          # 可视化前端仪表盘模块（可选）
│   ├── static/                         # 静态资源目录（CSS, JS, 图表库）
│   └── templates/                      # Jinja2 模板文件，用于渲染看板页面
├── tests/                              # 单元测试与集成测试套件
│   ├── test_adapters.py                # 针对不同站点适配器的解析准确性测试
│   └── test_fetcher.py                 # 模拟 HTTP 请求与超时场景的测试用例
├── docs/                               # 完整项目文档（用户手册、运维指南、API 参考）
├── scripts/                            # 运维辅助脚本
│   └── batch_import.py                 # 命令行批量导入工具，支持 CSV 与纯文本格式
├── requirements.txt                    # Python 依赖清单
└── manage.py                           # 项目统一命令行入口（启动、迁移、生成报告）
```

## 贡献指南

我们欢迎开发者以多种形式参与 WebWap 项目的改进与生态建设。请遵循以下流程提交贡献：

1. 查阅项目看板中的待办事项或已知问题列表，选择您感兴趣的任务。对于较大规模的功能提议，建议先创建一个议题（Issue）描述您的设计方案，以避免重复劳动或偏离项目主旨。

2. 将项目仓库复刻（Fork）至您的个人账户，并在本地新建一个具有描述性的功能分支。分支命名建议采用 `feature/功能简述` 或 `fix/问题编号` 的格式。

3. 编写代码时请严格遵循项目根目录下的 `.flake8` 及 `.pylintrc` 配置文件中的代码规范。所有新增的 API 接口或核心函数必须包含完整的 docstring 说明，且需为关键逻辑补充对应的单元测试用例。

4. 提交代码前，请确保本地测试套件全部通过（执行 `python manage.py test`）。若您的修改涉及数据库迁移，请一并提交迁移脚本。

5. 发起合并请求（Pull Request）至主仓库的 `develop` 分支。请求描述中需清晰列出变更点、关联的议题编号以及手动测试的步骤说明。项目维护者将在两个工作日内进行代码审查与反馈。

## 常见问题

**问：系统如何处理目标站点反爬限制或频繁封禁 IP 的情况？**

答：WebWap 提供了可配置的请求间隔与用户代理轮换策略。用户可以在 `core/settings.py` 中调整 `REQUEST_DELAY` 参数（默认 1.5 秒）以降低请求频率。对于严格限制的站点，推荐启用代理池扩展（需额外安装 `proxy-rotator` 插件）。此外，系统支持手动标记某个批次或域名为“低优先级”，以减少其检测次数。

**问：如果原始链接返回 302 跳转或内容发生变更，系统如何记录和通知？**

答：对于 302 临时跳转，系统会跟随重定向直至获取最终 200 状态码，并将整个跳转链路记录在 `link.redirect_chain` 字段中。对于内容变更的检测，系统在每次抓取时计算页面主体的 SHA-256 哈希值，若与上一次记录的哈希值不一致，则触发内容变更告警。告警方式支持邮件、Webhook 及标准日志输出，具体配置位于 `core/settings.py` 的 `NOTIFICATION` 区块。

**问：系统是否支持对历史批次中的链接进行重新分类或标签修正？**

答：支持。用户可以通过 Web 仪表盘或 API 接口对已归档的链接批量更新标签。系统在修正标签时会自动保留原始标签作为备选，并记录操作日志以便追溯。若需要基于修正后的标签重建索引，可运行 `python manage.py reindex --batch=52` 命令，该操作不会影响链接的原始状态数据。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
