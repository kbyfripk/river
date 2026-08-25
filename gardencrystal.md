# WebLink Navigator

WebLink Navigator 是一个面向开发人员、技术研究者与内容策展人的轻量级外链资源归集与导航系统。该项目定位于将分散的、来源多样的技术文章、新闻动态与参考手册以可检索、可分类、可版本化的方式进行统一管理，并通过简洁的 Web 界面或 API 对外提供访问入口。目标用户包括技术团队内部的知识库维护者、开源社区的内容贡献者以及个人技术博主。

本项目不提供爬虫或自动采集功能，而是以人工或半人工方式录入经过筛选的链接资源，并辅以标签、时间戳与来源标记。通过结构化的数据存储和清晰的目录组织，用户可以快速定位到特定主题的参考资料，避免在杂乱无章的书签或零散笔记中反复检索。当前批次收录链接数量为 240/250，涵盖技术博客、行业资讯、开源项目发布页等多种类型。

## 功能概览

链接入库与分类管理：支持将单个 URL 录入系统并分配类别、标签和优先级，所有条目存储在本地 JSON 或 SQLite 数据源中，便于后续扩展。

多维度检索过滤：按标题关键词、URL 域名、录入时间段、标签组合进行筛选，检索结果支持分页与排序。

批次化导入导出：针对批量链接（如本批次 250 条）提供 CSV 或纯文本列表的导入接口，并支持导出为 Markdown 表格或 JSON 结构。

本地化 Web 展示界面：内置基于 Flask 或 Express 的轻量服务端，提供响应式 HTML 页面，展示最新入库链接与热门标签云。

RESTful API 端点：暴露 /api/links、/api/tags、/api/search 等标准接口，方便与其他工具（如自动化脚本、浏览器插件）集成。

数据快照与回滚：每次批量操作自动生成数据快照文件，支持回退至上一个稳定版本，防止误操作导致数据丢失。

静态站点生成模式：支持将当前链接库一键导出为纯静态 HTML 文件，适合部署在 GitHub Pages 或任何静态托管服务上。

## 应用场景

技术团队内部知识库维护：开发团队可将日常遇到的有价值的外部技术博客、故障排查记录或官方文档链接统一录入 WebLink Navigator，并按项目或模块分类，新成员入职时可快速查阅相关领域的历史参考资源。

开源项目外部依赖与参考资料整理：开源项目维护者可将项目依赖的第三方库文档、设计参考规范、相关 RFC 文档等集中存放，并在 README 或项目 Wiki 中引用导航页，减少用户在多个站点间跳转的耗时。

个人技术博主的内容素材管理：技术写作人员可使用该系统收集写作素材，针对不同写作主题（如性能优化、框架对比、安全漏洞分析）建立独立标签，在撰写系列文章时能够快速回溯原始信息来源。

社区活动与会议资料归档：技术社区组织者可将线上或线下活动的演讲幻灯片链接、视频回放地址、相关讨论帖统一归入导航库，生成活动专属页面并分享给参会者，提升活动后续的可访问性。

自动化监控与失效链接检测：结合定时任务，系统可对已入库链接进行可用性检查，标记返回 4xx 或 5xx 状态的 URL，帮助管理员及时发现并清理或更新失效资源。

## 快速开始

以下步骤适用于开发环境快速启动 WebLink Navigator 服务。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装依赖（以 Python 版本为例，使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化数据库并导入示例数据
python scripts/init_db.py
python scripts/import_batch.py --file data/batch_240.txt

# 启动开发服务器
python app.py
```

启动成功后，访问 http://localhost:5000 即可查看导航首页。默认管理员账户为 admin / admin123，首次登录后请及时修改密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，用于后端服务和数据管理脚本 |
| SQLite3 | 3.35 及以上 | 默认内嵌数据库，用于存储链接元数据和标签关系 |
| pip | 21.0 及以上 | Python 包依赖管理工具 |
| Node.js | 16.x 及以上 | 仅当启用前端构建功能时必需（用于静态站点生成） |
| Git | 2.25 及以上 | 用于克隆仓库及版本管理，非强制但推荐 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 官方支持环境，Windows 原生可能遇到路径兼容问题 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ | 如何添加链接、如何创建标签、如何导入导出批次数据 |
| 开发者指南 | docs/developer-guide/ | API 接口详细说明、数据模型设计、自定义前端界面方法 |
| 部署运维 | docs/deployment/ | 生产环境部署（Nginx + Gunicorn）、Docker 镜像构建、数据备份策略 |
| 常见任务 | docs/recipes/ | 定时检测失效链接、生成静态站点、迁移至 PostgreSQL 的操作示例 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/61783.htm
- http://m.blog.gqskj.cn/nnews/7271609.htm
- http://m.blog.gqskj.cn/nnews/926718.htm
- http://m.blog.gqskj.cn/nnews/500601.htm
- http://m.blog.gqskj.cn/nnews/78074.htm
- http://m.blog.gqskj.cn/nnews/4871474.htm
- http://m.blog.gqskj.cn/nnews/560250.htm
- http://m.blog.gqskj.cn/nnews/5220.htm
- http://m.blog.gqskj.cn/nnews/478169.htm
- http://m.blog.gqskj.cn/nnews/7958210.htm
- http://m.blog.gqskj.cn/nnews/945621.htm
- http://m.blog.gqskj.cn/nnews/76345.htm
- http://m.blog.gqskj.cn/nnews/9692091.htm
- http://m.blog.gqskj.cn/nnews/454105.htm
- http://m.blog.gqskj.cn/nnews/74001.htm
- http://m.blog.gqskj.cn/nnews/2133.htm
- http://m.blog.gqskj.cn/nnews/838214.htm
- http://m.blog.gqskj.cn/nnews/656673.htm
- http://m.blog.gqskj.cn/nnews/767141.htm
- http://m.blog.gqskj.cn/nnews/5430797.htm
- http://m.blog.gqskj.cn/nnews/614639.htm
- http://m.blog.gqskj.cn/nnews/08027.htm
- http://m.blog.gqskj.cn/nnews/50342.htm
- http://m.blog.gqskj.cn/nnews/176737.htm
- http://m.blog.gqskj.cn/nnews/1737546.htm
- http://m.blog.gqskj.cn/nnews/8528208.htm
- http://m.blog.gqskj.cn/nnews/652498.htm
- http://m.blog.gqskj.cn/nnews/798314.htm
- http://m.blog.gqskj.cn/nnews/6809291.htm
- http://m.blog.gqskj.cn/nnews/229947.htm
- http://m.blog.gqskj.cn/nnews/018278.htm
- http://m.blog.gqskj.cn/nnews/866902.htm
- http://m.blog.gqskj.cn/nnews/37419.htm
- http://m.blog.gqskj.cn/nnews/6210.htm
- http://m.blog.gqskj.cn/nnews/7312.htm
- http://m.blog.gqskj.cn/nnews/678310.htm
- http://m.blog.gqskj.cn/nnews/340955.htm
- http://m.blog.gqskj.cn/nnews/18230.htm
- http://m.blog.gqskj.cn/nnews/7481.htm
- http://m.blog.gqskj.cn/nnews/59397.htm
- http://m.blog.gqskj.cn/nnews/242708.htm
- http://m.blog.gqskj.cn/nnews/906400.htm
- http://m.blog.gqskj.cn/nnews/8950966.htm
- http://m.blog.gqskj.cn/nnews/7930670.htm
- http://m.blog.gqskj.cn/nnews/18760.htm
- http://m.blog.gqskj.cn/nnews/670763.htm
- http://m.blog.gqskj.cn/nnews/7056.htm
- http://m.blog.gqskj.cn/nnews/6379696.htm
- http://m.blog.gqskj.cn/nnews/5601.htm
- http://m.blog.gqskj.cn/nnews/1847197.htm
- http://m.blog.gqskj.cn/nnews/19167.htm
- http://m.blog.gqskj.cn/nnews/86665.htm
- http://m.blog.gqskj.cn/nnews/663627.htm
- http://m.blog.gqskj.cn/nnews/7168147.htm
- http://m.blog.gqskj.cn/nnews/9137.htm
- http://m.blog.gqskj.cn/nnews/260507.htm
- http://m.blog.gqskj.cn/nnews/66710.htm
- http://m.blog.gqskj.cn/nnews/9845820.htm
- http://m.blog.gqskj.cn/nnews/674978.htm
- http://m.blog.gqskj.cn/nnews/78356.htm
- http://m.blog.gqskj.cn/nnews/12341.htm
- http://m.blog.gqskj.cn/nnews/842671.htm
- http://m.blog.gqskj.cn/nnews/4617715.htm
- http://m.blog.gqskj.cn/nnews/45022.htm
- http://m.blog.gqskj.cn/nnews/2885500.htm
- http://m.blog.gqskj.cn/nnews/1468232.htm
- http://m.blog.gqskj.cn/nnews/9858.htm
- http://m.blog.gqskj.cn/nnews/223648.htm
- http://m.blog.gqskj.cn/nnews/4749.htm
- http://m.blog.gqskj.cn/nnews/40237.htm
- http://m.blog.gqskj.cn/nnews/2183.htm
- http://m.blog.gqskj.cn/nnews/7387431.htm
- http://m.blog.gqskj.cn/nnews/969070.htm
- http://m.blog.gqskj.cn/nnews/986294.htm
- http://m.blog.gqskj.cn/nnews/38831.htm
- http://m.blog.gqskj.cn/nnews/4644893.htm
- http://m.blog.gqskj.cn/nnews/4165.htm
- http://m.blog.gqskj.cn/nnews/4800388.htm
- http://m.blog.gqskj.cn/nnews/653673.htm
- http://m.blog.gqskj.cn/nnews/59598.htm
- http://m.blog.gqskj.cn/nnews/5741.htm
- http://m.blog.gqskj.cn/nnews/7740.htm
- http://m.blog.gqskj.cn/nnews/319835.htm
- http://m.blog.gqskj.cn/nnews/0469503.htm
- http://m.blog.gqskj.cn/nnews/5866461.htm
- http://m.blog.gqskj.cn/nnews/71880.htm
- http://m.blog.gqskj.cn/nnews/53761.htm
- http://m.blog.gqskj.cn/nnews/9120.htm
- http://m.blog.gqskj.cn/nnews/359643.htm
- http://m.blog.gqskj.cn/nnews/0586073.htm
- http://m.blog.gqskj.cn/nnews/03396.htm
- http://m.blog.gqskj.cn/nnews/62507.htm
- http://m.blog.gqskj.cn/nnews/81981.htm
- http://m.blog.gqskj.cn/nnews/1020.htm
- http://m.blog.gqskj.cn/nnews/600374.htm
- http://m.blog.gqskj.cn/nnews/16486.htm
- http://m.blog.gqskj.cn/nnews/12827.htm
- http://m.blog.gqskj.cn/nnews/1289.htm
- http://m.blog.gqskj.cn/nnews/4809.htm
- http://m.blog.gqskj.cn/nnews/86458.htm
- http://m.blog.gqskj.cn/nnews/1550371.htm
- http://m.blog.gqskj.cn/nnews/3047797.htm
- http://m.blog.gqskj.cn/nnews/919771.htm
- http://m.blog.gqskj.cn/nnews/4355026.htm
- http://m.blog.gqskj.cn/nnews/26293.htm
- http://m.blog.gqskj.cn/nnews/539185.htm
- http://m.blog.gqskj.cn/nnews/4345.htm
- http://m.blog.gqskj.cn/nnews/6737538.htm
- http://m.blog.gqskj.cn/nnews/1608920.htm
- http://m.blog.gqskj.cn/nnews/318880.htm
- http://m.blog.gqskj.cn/nnews/7036.htm
- http://m.blog.gqskj.cn/nnews/65385.htm
- http://m.blog.gqskj.cn/nnews/382509.htm
- http://m.blog.gqskj.cn/nnews/603420.htm
- http://m.blog.gqskj.cn/nnews/1569.htm
- http://m.blog.gqskj.cn/nnews/95933.htm
- http://m.blog.gqskj.cn/nnews/40269.htm
- http://m.blog.gqskj.cn/nnews/97950.htm
- http://m.blog.gqskj.cn/nnews/8645945.htm
- http://m.blog.gqskj.cn/nnews/473317.htm
- http://m.blog.gqskj.cn/nnews/0405591.htm
- http://m.blog.gqskj.cn/nnews/07268.htm
- http://m.blog.gqskj.cn/nnews/0137.htm
- http://m.blog.gqskj.cn/nnews/11685.htm
- http://m.blog.gqskj.cn/nnews/37326.htm
- http://m.blog.gqskj.cn/nnews/3093089.htm
- http://m.blog.gqskj.cn/nnews/1570851.htm
- http://m.blog.gqskj.cn/nnews/130070.htm
- http://m.blog.gqskj.cn/nnews/95081.htm
- http://m.blog.gqskj.cn/nnews/73390.htm
- http://m.blog.gqskj.cn/nnews/045748.htm
- http://m.blog.gqskj.cn/nnews/9416922.htm
- http://m.blog.gqskj.cn/nnews/3137473.htm
- http://m.blog.gqskj.cn/nnews/71156.htm
- http://m.blog.gqskj.cn/nnews/5303.htm
- http://m.blog.gqskj.cn/nnews/3432.htm
- http://m.blog.gqskj.cn/nnews/063017.htm
- http://m.blog.gqskj.cn/nnews/659160.htm
- http://m.blog.gqskj.cn/nnews/4813859.htm
- http://m.blog.gqskj.cn/nnews/489661.htm
- http://m.blog.gqskj.cn/nnews/12135.htm
- http://m.blog.gqskj.cn/nnews/1772.htm
- http://m.blog.gqskj.cn/nnews/56113.htm
- http://m.blog.gqskj.cn/nnews/75311.htm
- http://m.blog.gqskj.cn/nnews/411646.htm
- http://m.blog.gqskj.cn/nnews/1327.htm
- http://m.blog.gqskj.cn/nnews/0343447.htm
- http://m.blog.gqskj.cn/nnews/4479.htm
- http://m.blog.gqskj.cn/nnews/74761.htm
- http://m.blog.gqskj.cn/nnews/4119.htm
- http://m.blog.gqskj.cn/nnews/5232604.htm
- http://m.blog.gqskj.cn/nnews/158651.htm
- http://m.blog.gqskj.cn/nnews/332486.htm
- http://m.blog.gqskj.cn/nnews/09387.htm
- http://m.blog.gqskj.cn/nnews/9192.htm
- http://m.blog.gqskj.cn/nnews/2290.htm
- http://m.blog.gqskj.cn/nnews/99210.htm
- http://m.blog.gqskj.cn/nnews/59173.htm
- http://m.blog.gqskj.cn/nnews/4944.htm
- http://m.blog.gqskj.cn/nnews/657194.htm
- http://m.blog.gqskj.cn/nnews/8756115.htm
- http://m.blog.gqskj.cn/nnews/3125101.htm
- http://m.blog.gqskj.cn/nnews/01979.htm
- http://m.blog.gqskj.cn/nnews/7293414.htm
- http://m.blog.gqskj.cn/nnews/9924587.htm
- http://m.blog.gqskj.cn/nnews/8586.htm
- http://m.blog.gqskj.cn/nnews/661025.htm
- http://m.blog.gqskj.cn/nnews/1344660.htm
- http://m.blog.gqskj.cn/nnews/247049.htm
- http://m.blog.gqskj.cn/nnews/20881.htm
- http://m.blog.gqskj.cn/nnews/23472.htm
- http://m.blog.gqskj.cn/nnews/2386.htm
- http://m.blog.gqskj.cn/nnews/25146.htm
- http://m.blog.gqskj.cn/nnews/201441.htm
- http://m.blog.gqskj.cn/nnews/80202.htm
- http://m.blog.gqskj.cn/nnews/0105.htm
- http://m.blog.gqskj.cn/nnews/6383186.htm
- http://m.blog.gqskj.cn/nnews/66847.htm
- http://m.blog.gqskj.cn/nnews/599445.htm
- http://m.blog.gqskj.cn/nnews/8707.htm
- http://m.blog.gqskj.cn/nnews/11197.htm
- http://m.blog.gqskj.cn/nnews/7995493.htm
- http://m.blog.gqskj.cn/nnews/90817.htm
- http://m.blog.gqskj.cn/nnews/468972.htm
- http://m.blog.gqskj.cn/nnews/82102.htm
- http://m.blog.gqskj.cn/nnews/6021.htm
- http://m.blog.gqskj.cn/nnews/8118990.htm
- http://m.blog.gqskj.cn/nnews/374823.htm
- http://m.blog.gqskj.cn/nnews/1816241.htm
- http://m.blog.gqskj.cn/nnews/6293541.htm
- http://m.blog.gqskj.cn/nnews/3626.htm
- http://m.blog.gqskj.cn/nnews/5139.htm
- http://m.blog.gqskj.cn/nnews/2180.htm
- http://m.blog.gqskj.cn/nnews/5827358.htm
- http://m.blog.gqskj.cn/nnews/71253.htm
- http://m.blog.gqskj.cn/nnews/618577.htm
- http://m.blog.gqskj.cn/nnews/70979.htm
- http://m.blog.gqskj.cn/nnews/451173.htm
- http://m.blog.gqskj.cn/nnews/23960.htm
- http://m.blog.gqskj.cn/nnews/1361071.htm
- http://m.blog.gqskj.cn/nnews/1354535.htm
- http://m.blog.gqskj.cn/nnews/28469.htm
- http://m.blog.gqskj.cn/nnews/997502.htm
- http://m.blog.gqskj.cn/nnews/193517.htm
- http://m.blog.gqskj.cn/nnews/9411766.htm
- http://m.blog.gqskj.cn/nnews/4755414.htm
- http://m.blog.gqskj.cn/nnews/78181.htm
- http://m.blog.gqskj.cn/nnews/653529.htm
- http://m.blog.gqskj.cn/nnews/9350.htm
- http://m.blog.gqskj.cn/nnews/85161.htm
- http://m.blog.gqskj.cn/nnews/71903.htm
- http://m.blog.gqskj.cn/nnews/03589.htm
- http://m.blog.gqskj.cn/nnews/93672.htm
- http://m.blog.gqskj.cn/nnews/6898964.htm
- http://m.blog.gqskj.cn/nnews/9664.htm
- http://m.blog.gqskj.cn/nnews/94275.htm
- http://m.blog.gqskj.cn/nnews/7952332.htm
- http://m.blog.gqskj.cn/nnews/72150.htm
- http://m.blog.gqskj.cn/nnews/3911.htm
- http://m.blog.gqskj.cn/nnews/4925746.htm
- http://m.blog.gqskj.cn/nnews/8020.htm
- http://m.blog.gqskj.cn/nnews/5846.htm
- http://m.blog.gqskj.cn/nnews/8718972.htm
- http://m.blog.gqskj.cn/nnews/7703193.htm
- http://m.blog.gqskj.cn/nnews/217963.htm
- http://m.blog.gqskj.cn/nnews/993904.htm
- http://m.blog.gqskj.cn/nnews/10692.htm
- http://m.blog.gqskj.cn/nnews/5700476.htm
- http://m.blog.gqskj.cn/nnews/9665143.htm
- http://m.blog.gqskj.cn/nnews/35040.htm
- http://m.blog.gqskj.cn/nnews/4861170.htm
- http://m.blog.gqskj.cn/nnews/5743962.htm
- http://m.blog.gqskj.cn/nnews/88891.htm
- http://m.blog.gqskj.cn/nnews/40941.htm
- http://m.blog.gqskj.cn/nnews/3849.htm
- http://m.blog.gqskj.cn/nnews/6628.htm
- http://m.blog.gqskj.cn/nnews/27623.htm
- http://m.blog.gqskj.cn/nnews/7453.htm
- http://m.blog.gqskj.cn/nnews/4785.htm
- http://m.blog.gqskj.cn/nnews/247678.htm
- http://m.blog.gqskj.cn/nnews/837749.htm
- http://m.blog.gqskj.cn/nnews/6029916.htm
- http://m.blog.gqskj.cn/nnews/3770384.htm
- http://m.blog.gqskj.cn/nnews/067663.htm
- http://m.blog.gqskj.cn/nnews/7928403.htm
- http://m.blog.gqskj.cn/nnews/3246197.htm
- http://m.blog.gqskj.cn/nnews/9366.htm
- http://m.blog.gqskj.cn/nnews/7035953.htm
- http://m.blog.gqskj.cn/nnews/6003.htm
- http://m.blog.gqskj.cn/nnews/45992.htm

## 项目结构

```
weblink-navigator/
├── app/                            # 核心应用模块
│   ├── __init__.py                 # 应用工厂函数，注册蓝图与扩展
│   ├── routes/                     # 路由层，按功能拆分
│   │   ├── api.py                  # RESTful API 端点，包含链接增删改查与标签接口
│   │   ├── web.py                  # 前端页面渲染路由，处理首页、分类页与详情页
│   │   └── admin.py                # 后台管理路由，用于批量导入与系统配置
│   ├── models/                     # 数据模型与 ORM 映射
│   │   ├── link.py                 # Link 实体，定义字段与序列化方法
│   │   ├── tag.py                  # Tag 实体，关联 Link 的多对多关系
│   │   └── batch.py                # Batch 实体，记录每次导入的元信息与快照路径
│   └── services/                   # 业务逻辑服务层
│       ├── importer.py             # 批量导入服务，支持 TXT / CSV / JSON 格式解析
│       ├── exporter.py             # 导出服务，支持 Markdown / JSON / HTML 静态生成
│       └── health_check.py         # 链接可用性检测服务，支持异步并发检测
├── scripts/                        # 运维与开发辅助脚本
│   ├── init_db.py                  # 初始化数据库表结构与默认标签
│   ├── import_batch.py             # 命令行批量导入工具，接受文件路径参数
│   └── backup.py                   # 数据快照创建与恢复脚本
├── static/                         # 静态资源（CSS / JS / 图片）
│   ├── css/
│   │   └── style.css               # 基于 Flexbox 的响应式布局样式
│   └── js/
│       └── app.js                  # 前端交互逻辑，包含搜索即时过滤与分页控件
├── templates/                      # Jinja2 模板目录
│   ├── base.html                   # 基础布局模板，包含导航栏与页脚
│   ├── index.html                  # 首页模板，展示最新链接与标签云
│   └── detail.html                 # 单个链接详情页模板
├── data/                           # 数据存储目录（默认使用 SQLite，快照存放于此）
│   ├── weblink.db                  # SQLite 主数据库文件
│   └── snapshots/                  # 每次批量导入或手动备份生成的 JSON 快照
├── tests/                          # 单元测试与集成测试
│   ├── test_models.py              # 数据模型层测试，覆盖 CRUD 操作
│   ├── test_services.py            # 服务层测试，覆盖导入导出与健康检查逻辑
│   └── conftest.py                 # pytest 配置文件与共享 fixture
├── config.py                       # 应用配置（开发、测试、生产三套环境）
├── requirements.txt                # Python 依赖列表（Flask, SQLAlchemy, pytest 等）
├── Dockerfile                      # 多阶段构建 Docker 镜像文件
├── docker-compose.yml              # 本地开发环境编排，含应用与 Redis 缓存
└── README.md                       # 本文件
```

## 贡献指南

提交问题报告：请在 GitHub Issues 中使用提供的模板描述问题，包括操作系统版本、Python 版本、复现步骤和完整错误日志。对于链接检测相关的功能问题，请附带受影响的 URL 示例。

代码贡献流程：Fork 主仓库至个人账号，在 dev 分支上创建功能分支（命名格式为 feature/简述或 fix/简述），完成代码编写后确保所有单元测试通过（pytest tests/），随后提交 Pull Request 至主仓库的 dev 分支。

文档完善与翻译：鼓励对用户手册和 API 文档进行补充或修订。文档源文件位于 docs/ 目录下，使用 Markdown 编写。如有新增功能，请同步更新对应的文档章节。

本地调试与测试：运行前请复制 config.example.py 为 config.py 并根据本地环境调整数据库路径。使用 python scripts/init_db.py 初始化测试数据，随后执行 pytest tests/ 验证所有用例通过后再行提交。

社区沟通渠道：普通使用问题可在 GitHub Discussions 中发起，开发相关讨论可使用 Gitter 或 Matrix 即时通讯频道（链接见仓库首页）。提交 Pull Request 前建议先在 Discussions 中简述改动计划，避免重复劳动。

## 常见问题

升级现有数据到新版本时如何处理数据库迁移？

项目使用 Flask-Migrate 管理数据库版本变更。执行 flask db upgrade 即可自动应用迁移脚本。迁移脚本位于 migrations/versions/ 目录下，每次发布版本会包含对应的升级与降级脚本。建议在执行升级前使用 scripts/backup.py 创建完整数据快照。

导入大批量链接时页面响应缓慢或超时怎么办？

批量导入操作默认采用事务批量提交方式，每 500 条提交一次。若链接数量超过 5000，建议使用命令行脚本 scripts/import_batch.py 而非 Web 界面导入，并增加 --batch-size 参数控制单次提交数量。同时可调整 config.py 中 SQLALCHEMY_POOL_SIZE 连接池大小以提升并发写入能力。

如何自定义链接列表的排序规则或显示字段？

前端列表排序默认按创建时间降序。如需按点击量、标题字母序或标签优先级排序，可在界面右上角下拉菜单中选择排序方式。若需增加自定义排序字段，请修改 models/link.py 中的 order_by 逻辑，并在 templates/index.html 中对应的下拉菜单中添加选项。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:47
