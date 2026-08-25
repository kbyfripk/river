# WebLink Navigator

WebLink Navigator 是一个面向技术信息聚合与外部资源导航的开源项目，专为需要批量管理、分类展示和快速检索海量外链资源的开发者与内容运营者设计。该项目将分散的 URL 资源统一纳入结构化目录，通过本地化的索引机制与轻量级 Web 界面，帮助用户高效组织和访问来自不同来源的外部链接，适用于个人书签管理、团队知识库外链整合以及内容聚合站点的底层数据构建。

## 功能概览

批量导入与解析 支持从纯文本、CSV 或 Markdown 列表批量导入 URL，自动解析协议、域名与路径参数，生成标准化条目。

分类标签管理 允许用户为每个链接自定义标签与分类，支持多级目录树结构，便于按主题或业务线归集资源。

全文检索与过滤 内置基于关键词的标题与 URL 模糊搜索，同时支持按域名、文件类型或更新时间范围进行多维度筛选。

外链健康检查 定时对已收录的 URL 发起 HEAD 请求，检测响应状态码，标记失效或重定向链接，生成异常报告。

访问统计看板 记录每个链接的点击次数与最近访问时间，提供热度排名与访问趋势图表，辅助内容价值评估。

数据导入导出 支持 JSON、YAML 和 Markdown 格式的完整数据导出，便于备份、迁移或与其他系统对接。

响应式 Web 界面 提供适配桌面与移动设备的轻量管理面板，无需额外客户端即可完成日常维护操作。

## 应用场景

个人技术书签库 开发者可将日常阅读中积累的技术文档、API 参考、开源仓库链接统一收录，通过标签分类与搜索快速定位所需资料，替代浏览器自带的碎片化书签管理。

团队知识库外链中心 技术团队可将项目依赖的文档站、设计规范、内部工具地址集中托管于 WebLink Navigator，新成员入职时一键获取所有必备外部资源，减少信息传递成本。

内容聚合站点数据源 内容运营者可将分散在不同平台的文章、视频、工具页面链接导入系统，通过分类目录生成导航页面或站点地图，为上层内容聚合平台提供结构化的外链数据支撑。

归档与审计辅助 运维人员利用外链健康检查功能定期扫描历史文档中的外部引用，及时发现失效链接并更新，保障技术文档或产品官网中引用资源的可用性。

## 快速开始

以下操作基于 Linux/macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库
python scripts/init_db.py

# 启动本地开发服务器
python app.py runserver --host 0.0.0.0 --port 8080
```

启动成功后，访问 http://localhost:8080 即可进入管理界面。默认管理员账号为 admin，密码在首次启动时由控制台输出，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.12 | 核心运行环境，低于 3.9 不支持类型注解语法 |
| SQLite | 3.35.0 以上 | 内置数据库，用于存储链接元数据与索引 |
| Flask | 2.3.x | Web 框架，提供路由与模板渲染能力 |
| requests | 2.31.x | 用于外链健康检查的 HTTP 客户端 |
| pytest | 8.0.x | 单元测试框架（仅开发环境需要） |
| nodejs | 18.x 以上 | 仅当需要构建前端静态资源时使用（可选） |
| redis | 7.0 以上 | 缓存与任务队列（生产环境推荐，开发可忽略） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何最短时间内完成安装并导入第一批链接？ |
| 操作手册 | docs/usage.md | 如何批量导入、编辑标签、执行健康检查以及导出数据？ |
| 架构设计 | docs/architecture.md | 系统采用什么数据模型？前后端如何通信？索引机制如何工作？ |
| API 参考 | docs/api_reference.md | 外部系统如何通过 RESTful API 读写链接数据？有哪些端点与鉴权方式？ |
| 部署指南 | docs/deployment.md | 如何配置生产环境（Nginx + gunicorn + Redis）以及 SSL 证书？ |
| 常见任务 | docs/recipes.md | 如何定时清理失效链接？如何迁移数据库？如何自定义分类模板？ |

## 资源列表

- http://m.wap.gqskj.cn/snews/46126.htm
- http://m.wap.gqskj.cn/snews/775279.htm
- http://m.wap.gqskj.cn/snews/9452471.htm
- http://m.wap.gqskj.cn/snews/9914630.htm
- http://m.wap.gqskj.cn/snews/901770.htm
- http://m.wap.gqskj.cn/snews/9243296.htm
- http://m.wap.gqskj.cn/snews/9319325.htm
- http://m.wap.gqskj.cn/snews/31670.htm
- http://m.wap.gqskj.cn/snews/1872.htm
- http://m.wap.gqskj.cn/snews/35512.htm
- http://m.wap.gqskj.cn/snews/46858.htm
- http://m.wap.gqskj.cn/snews/2557.htm
- http://m.wap.gqskj.cn/snews/94917.htm
- http://m.wap.gqskj.cn/snews/83088.htm
- http://m.wap.gqskj.cn/snews/37722.htm
- http://m.wap.gqskj.cn/snews/8467.htm
- http://m.wap.gqskj.cn/snews/325676.htm
- http://m.wap.gqskj.cn/snews/668416.htm
- http://m.wap.gqskj.cn/snews/484738.htm
- http://m.wap.gqskj.cn/snews/19528.htm
- http://m.wap.gqskj.cn/snews/5377320.htm
- http://m.wap.gqskj.cn/snews/675561.htm
- http://m.wap.gqskj.cn/snews/963838.htm
- http://m.wap.gqskj.cn/snews/180326.htm
- http://m.wap.gqskj.cn/snews/7518759.htm
- http://m.wap.gqskj.cn/snews/3847362.htm
- http://m.wap.gqskj.cn/snews/449891.htm
- http://m.wap.gqskj.cn/snews/0963302.htm
- http://m.wap.gqskj.cn/snews/68253.htm
- http://m.wap.gqskj.cn/snews/4341.htm
- http://m.wap.gqskj.cn/snews/978775.htm
- http://m.wap.gqskj.cn/snews/62501.htm
- http://m.wap.gqskj.cn/snews/0502.htm
- http://m.wap.gqskj.cn/snews/9150.htm
- http://m.wap.gqskj.cn/snews/550396.htm
- http://m.wap.gqskj.cn/snews/57760.htm
- http://m.wap.gqskj.cn/snews/5177547.htm
- http://m.wap.gqskj.cn/snews/198258.htm
- http://m.wap.gqskj.cn/snews/8331.htm
- http://m.wap.gqskj.cn/snews/6990.htm
- http://m.wap.gqskj.cn/snews/23408.htm
- http://m.wap.gqskj.cn/snews/3622.htm
- http://m.wap.gqskj.cn/snews/3617.htm
- http://m.wap.gqskj.cn/snews/55072.htm
- http://m.wap.gqskj.cn/snews/6760464.htm
- http://m.wap.gqskj.cn/snews/6140.htm
- http://m.wap.gqskj.cn/snews/104103.htm
- http://m.wap.gqskj.cn/snews/46746.htm
- http://m.wap.gqskj.cn/snews/133670.htm
- http://m.wap.gqskj.cn/snews/723390.htm
- http://m.wap.gqskj.cn/snews/15647.htm
- http://m.wap.gqskj.cn/snews/219755.htm
- http://m.wap.gqskj.cn/snews/50679.htm
- http://m.wap.gqskj.cn/snews/0779.htm
- http://m.wap.gqskj.cn/snews/244355.htm
- http://m.wap.gqskj.cn/snews/7748.htm
- http://m.wap.gqskj.cn/snews/19637.htm
- http://m.wap.gqskj.cn/snews/8293.htm
- http://m.wap.gqskj.cn/snews/89312.htm
- http://m.wap.gqskj.cn/snews/4400635.htm
- http://m.wap.gqskj.cn/snews/2225509.htm
- http://m.wap.gqskj.cn/snews/716951.htm
- http://m.wap.gqskj.cn/snews/2275706.htm
- http://m.wap.gqskj.cn/snews/90660.htm
- http://m.wap.gqskj.cn/snews/5984529.htm
- http://m.wap.gqskj.cn/snews/76184.htm
- http://m.wap.gqskj.cn/snews/82321.htm
- http://m.wap.gqskj.cn/snews/352685.htm
- http://m.wap.gqskj.cn/snews/239588.htm
- http://m.wap.gqskj.cn/snews/5910003.htm
- http://m.wap.gqskj.cn/snews/439086.htm
- http://m.wap.gqskj.cn/snews/0447247.htm
- http://m.wap.gqskj.cn/snews/39636.htm
- http://m.wap.gqskj.cn/snews/70402.htm
- http://m.wap.gqskj.cn/snews/92127.htm
- http://m.wap.gqskj.cn/snews/942760.htm
- http://m.wap.gqskj.cn/snews/985694.htm
- http://m.wap.gqskj.cn/snews/501668.htm
- http://m.wap.gqskj.cn/snews/0173025.htm
- http://m.wap.gqskj.cn/snews/5791270.htm
- http://m.wap.gqskj.cn/snews/00996.htm
- http://m.wap.gqskj.cn/snews/49054.htm
- http://m.wap.gqskj.cn/snews/80943.htm
- http://m.wap.gqskj.cn/snews/26960.htm
- http://m.wap.gqskj.cn/snews/1862.htm
- http://m.wap.gqskj.cn/snews/1588345.htm
- http://m.wap.gqskj.cn/snews/7078.htm
- http://m.wap.gqskj.cn/snews/275596.htm
- http://m.wap.gqskj.cn/snews/3465248.htm
- http://m.wap.gqskj.cn/snews/1674414.htm
- http://m.wap.gqskj.cn/snews/142033.htm
- http://m.wap.gqskj.cn/snews/80210.htm
- http://m.wap.gqskj.cn/snews/703394.htm
- http://m.wap.gqskj.cn/snews/9409297.htm
- http://m.wap.gqskj.cn/snews/84480.htm
- http://m.wap.gqskj.cn/snews/6744.htm
- http://m.wap.gqskj.cn/snews/9069795.htm
- http://m.wap.gqskj.cn/snews/302824.htm
- http://m.wap.gqskj.cn/snews/143788.htm
- http://m.wap.gqskj.cn/snews/790780.htm
- http://m.wap.gqskj.cn/snews/5595340.htm
- http://m.wap.gqskj.cn/snews/4026994.htm
- http://m.wap.gqskj.cn/snews/994067.htm
- http://m.wap.gqskj.cn/snews/26200.htm
- http://m.wap.gqskj.cn/snews/5707403.htm
- http://m.wap.gqskj.cn/snews/1666028.htm
- http://m.wap.gqskj.cn/snews/0755.htm
- http://m.wap.gqskj.cn/snews/4252.htm
- http://m.wap.gqskj.cn/snews/69490.htm
- http://m.wap.gqskj.cn/snews/538193.htm
- http://m.wap.gqskj.cn/snews/281343.htm
- http://m.wap.gqskj.cn/snews/2194.htm
- http://m.wap.gqskj.cn/snews/2338795.htm
- http://m.wap.gqskj.cn/snews/8007.htm
- http://m.wap.gqskj.cn/snews/6977766.htm
- http://m.wap.gqskj.cn/snews/00730.htm
- http://m.wap.gqskj.cn/snews/0482127.htm
- http://m.wap.gqskj.cn/snews/19200.htm
- http://m.wap.gqskj.cn/snews/24967.htm
- http://m.wap.gqskj.cn/snews/8363931.htm
- http://m.wap.gqskj.cn/snews/4996258.htm
- http://m.wap.gqskj.cn/snews/7209.htm
- http://m.wap.gqskj.cn/snews/3379604.htm
- http://m.wap.gqskj.cn/snews/79729.htm
- http://m.wap.gqskj.cn/snews/0569.htm
- http://m.wap.gqskj.cn/snews/3188590.htm
- http://m.wap.gqskj.cn/snews/286300.htm
- http://m.wap.gqskj.cn/snews/594331.htm
- http://m.wap.gqskj.cn/snews/63091.htm
- http://m.wap.gqskj.cn/snews/2404078.htm
- http://m.wap.gqskj.cn/snews/765043.htm
- http://m.wap.gqskj.cn/snews/64011.htm
- http://m.wap.gqskj.cn/snews/8602679.htm
- http://m.wap.gqskj.cn/snews/916195.htm
- http://m.wap.gqskj.cn/snews/8878511.htm
- http://m.wap.gqskj.cn/snews/24509.htm
- http://m.wap.gqskj.cn/snews/307223.htm
- http://m.wap.gqskj.cn/snews/0686.htm
- http://m.wap.gqskj.cn/snews/1725181.htm
- http://m.wap.gqskj.cn/snews/5593.htm
- http://m.wap.gqskj.cn/snews/1811776.htm
- http://m.wap.gqskj.cn/snews/0365.htm
- http://m.wap.gqskj.cn/snews/6822.htm
- http://m.wap.gqskj.cn/snews/505379.htm
- http://m.wap.gqskj.cn/snews/1231.htm
- http://m.wap.gqskj.cn/snews/251583.htm
- http://m.wap.gqskj.cn/snews/653688.htm
- http://m.wap.gqskj.cn/snews/639709.htm
- http://m.wap.gqskj.cn/snews/04776.htm
- http://m.wap.gqskj.cn/snews/0929594.htm
- http://m.wap.gqskj.cn/snews/417798.htm
- http://m.wap.gqskj.cn/snews/6627.htm
- http://m.wap.gqskj.cn/snews/0875.htm
- http://m.wap.gqskj.cn/snews/1228.htm
- http://m.wap.gqskj.cn/snews/0173968.htm
- http://m.wap.gqskj.cn/snews/2761.htm
- http://m.wap.gqskj.cn/snews/74024.htm
- http://m.wap.gqskj.cn/snews/071744.htm
- http://m.wap.gqskj.cn/snews/7897841.htm
- http://m.wap.gqskj.cn/snews/0452459.htm
- http://m.wap.gqskj.cn/snews/7348621.htm
- http://m.wap.gqskj.cn/snews/97230.htm
- http://m.wap.gqskj.cn/snews/95804.htm
- http://m.wap.gqskj.cn/snews/6177.htm
- http://m.wap.gqskj.cn/snews/20659.htm
- http://m.wap.gqskj.cn/snews/9322.htm
- http://m.wap.gqskj.cn/snews/928481.htm
- http://m.wap.gqskj.cn/snews/3495.htm
- http://m.wap.gqskj.cn/snews/8079.htm
- http://m.wap.gqskj.cn/snews/791402.htm
- http://m.wap.gqskj.cn/snews/05775.htm
- http://m.wap.gqskj.cn/snews/0813196.htm
- http://m.wap.gqskj.cn/snews/04912.htm
- http://m.wap.gqskj.cn/snews/3970631.htm
- http://m.wap.gqskj.cn/snews/9302.htm
- http://m.wap.gqskj.cn/snews/524414.htm
- http://m.wap.gqskj.cn/snews/221283.htm
- http://m.wap.gqskj.cn/snews/5509.htm
- http://m.wap.gqskj.cn/snews/65476.htm
- http://m.wap.gqskj.cn/snews/8652.htm
- http://m.wap.gqskj.cn/snews/3170302.htm
- http://m.wap.gqskj.cn/snews/1083823.htm
- http://m.wap.gqskj.cn/snews/59591.htm
- http://m.wap.gqskj.cn/snews/370264.htm
- http://m.wap.gqskj.cn/snews/3963340.htm
- http://m.wap.gqskj.cn/snews/451226.htm
- http://m.wap.gqskj.cn/snews/29379.htm
- http://m.wap.gqskj.cn/snews/384255.htm
- http://m.wap.gqskj.cn/snews/22649.htm
- http://m.wap.gqskj.cn/snews/195500.htm
- http://m.wap.gqskj.cn/snews/82475.htm
- http://m.wap.gqskj.cn/snews/6442.htm
- http://m.wap.gqskj.cn/snews/971586.htm
- http://m.wap.gqskj.cn/snews/7397.htm
- http://m.wap.gqskj.cn/snews/837728.htm
- http://m.wap.gqskj.cn/snews/79287.htm
- http://m.wap.gqskj.cn/snews/7568.htm
- http://m.wap.gqskj.cn/snews/3413750.htm
- http://m.wap.gqskj.cn/snews/0437.htm
- http://m.wap.gqskj.cn/snews/72965.htm
- http://m.wap.gqskj.cn/snews/9988.htm
- http://m.wap.gqskj.cn/snews/54751.htm
- http://m.wap.gqskj.cn/snews/6594486.htm
- http://m.wap.gqskj.cn/snews/632569.htm
- http://m.wap.gqskj.cn/snews/408559.htm
- http://m.wap.gqskj.cn/snews/0890.htm
- http://m.wap.gqskj.cn/snews/4436.htm
- http://m.wap.gqskj.cn/snews/37479.htm
- http://m.wap.gqskj.cn/snews/3979.htm
- http://m.wap.gqskj.cn/snews/3899.htm
- http://m.wap.gqskj.cn/snews/3820.htm
- http://m.wap.gqskj.cn/snews/1874.htm
- http://m.wap.gqskj.cn/snews/231071.htm
- http://m.wap.gqskj.cn/snews/1007782.htm
- http://m.wap.gqskj.cn/snews/165410.htm
- http://m.wap.gqskj.cn/snews/12490.htm
- http://m.wap.gqskj.cn/snews/5534.htm
- http://m.wap.gqskj.cn/snews/95452.htm
- http://m.wap.gqskj.cn/snews/61115.htm
- http://m.wap.gqskj.cn/snews/699386.htm
- http://m.wap.gqskj.cn/snews/3014.htm
- http://m.wap.gqskj.cn/snews/38412.htm
- http://m.wap.gqskj.cn/snews/349486.htm
- http://m.wap.gqskj.cn/snews/724340.htm
- http://m.wap.gqskj.cn/snews/757410.htm
- http://m.wap.gqskj.cn/snews/2920873.htm
- http://m.wap.gqskj.cn/snews/78769.htm
- http://m.wap.gqskj.cn/snews/2608.htm
- http://m.wap.gqskj.cn/snews/05944.htm
- http://m.wap.gqskj.cn/snews/93144.htm
- http://m.wap.gqskj.cn/snews/3772.htm
- http://m.wap.gqskj.cn/snews/81153.htm
- http://m.wap.gqskj.cn/snews/796921.htm
- http://m.wap.gqskj.cn/snews/4472.htm
- http://m.wap.gqskj.cn/snews/30217.htm
- http://m.wap.gqskj.cn/snews/465951.htm
- http://m.wap.gqskj.cn/snews/1174130.htm
- http://m.wap.gqskj.cn/snews/1391.htm
- http://m.wap.gqskj.cn/snews/4384.htm
- http://m.wap.gqskj.cn/snews/4192.htm
- http://m.wap.gqskj.cn/snews/90108.htm
- http://m.wap.gqskj.cn/snews/563230.htm
- http://m.wap.gqskj.cn/snews/90646.htm
- http://m.wap.gqskj.cn/snews/8144165.htm
- http://m.wap.gqskj.cn/snews/42509.htm
- http://m.wap.gqskj.cn/snews/818739.htm
- http://m.wap.gqskj.cn/snews/651556.htm
- http://m.wap.gqskj.cn/snews/88097.htm
- http://m.wap.gqskj.cn/snews/575955.htm
- http://m.wap.gqskj.cn/snews/9215152.htm

## 项目结构

```
weblink-navigator/
├── app/                            # 主应用包
│   ├── __init__.py                 # Flask 工厂函数与扩展初始化
│   ├── routes/                     # 路由蓝图目录
│   │   ├── auth.py                 # 登录、登出与鉴权接口
│   │   ├── links.py                # 链接 CRUD 与批量操作端点
│   │   ├── categories.py           # 分类树管理接口
│   │   └── health.py               # 健康检查触发与状态查询
│   ├── models/                     # 数据模型层
│   │   ├── link.py                 # Link 表定义（URL、标题、状态码、点击量）
│   │   ├── category.py             # Category 表定义（名称、父级 ID、排序）
│   │   └── user.py                 # User 表定义（用户名、密码哈希）
│   ├── services/                   # 业务逻辑层
│   │   ├── importer.py             # 批量导入解析器（支持 txt / csv / md）
│   │   ├── checker.py              # 异步健康检查调度器（基于 threading + queue）
│   │   └── exporter.py             # 数据导出器（JSON / YAML / Markdown）
│   ├── static/                     # 前端静态资源
│   │   ├── css/                    # 基础样式与响应式布局
│   │   └── js/                     # 列表渲染、搜索防抖、图表绘制（ECharts）
│   └── templates/                  # Jinja2 模板
│       ├── base.html               # 基础布局模板
│       ├── dashboard.html          # 统计看板页面
│       ├── link_list.html          # 链接列表与搜索页面
│       └── import_export.html      # 批量导入导出操作页面
├── scripts/                        # 运维与辅助脚本
│   ├── init_db.py                  # 初始化数据库表结构与默认分类
│   ├── seed_demo.py                # 填充示例数据用于测试
│   └── health_cron.py              # 可定时执行的健康检查命令行脚本
├── tests/                          # 单元测试与集成测试
│   ├── test_models.py              # 数据模型层测试（SQLite 内存模式）
│   ├── test_services.py            # 导入、检查、导出服务测试
│   └── test_routes.py              # API 端点测试（使用 Flask test client）
├── config/                         # 配置文件目录
│   ├── development.py              # 开发环境配置（调试开启、SQLite 路径）
│   ├── production.py               # 生产环境配置（Redis 地址、日志级别）
│   └── testing.py                  # 测试环境配置（内存数据库、禁用缓存）
├── docs/                           # 文档目录（对应文档导航章节）
│   ├── quickstart.md
│   ├── usage.md
│   ├── architecture.md
│   ├── api_reference.md
│   ├── deployment.md
│   └── recipes.md
├── requirements.txt                # Python 生产依赖列表
├── requirements-dev.txt            # 开发与测试额外依赖
├── app.py                          # 应用入口脚本（开发服务器启动）
├── wsgi.py                         # 生产环境 WSGI 入口（gunicorn 使用）
└── README.md                       # 本文件
```

## 贡献指南

1. 查阅问题追踪清单 访问 GitHub Issues 页面，查找标记为 help-wanted 或 good-first-issue 的任务，确认无其他人正在处理后留言认领。

2. 派生仓库并创建特性分支 将主仓库派生至个人账户，克隆本地后执行 git checkout -b feature/your-feature-name，分支命名建议包含功能简述。

3. 编写代码与单元测试 新增功能或修复缺陷时，需在 tests/ 目录下补充对应的测试用例，确保 pytest 全部通过。代码风格遵循 PEP 8，并建议使用 black 格式化。

4. 更新相关文档 若修改了用户可见的行为（如新增配置项、修改 API 响应格式），需同步更新 docs/ 中对应文档，并在 README 的文档导航章节中反映变化。

5. 提交拉取请求 推送分支至派生仓库后，向主仓库的 main 分支发起 Pull Request，描述中需说明变更动机、实现方式及测试覆盖情况。至少一位维护者审核通过后合并。

## 常见问题

Q: 导入大量 URL 时页面出现超时或卡顿，应如何优化？

A: 单次导入超过 500 条链接时，建议使用命令行脚本 scripts/batch_import.py 而非 Web 界面上传。该脚本直接操作数据库，绕过了 HTTP 请求的超时限制。若仍需通过 Web 导入，可修改配置中的 MAX_IMPORT_SIZE 并调整 nginx 的 client_max_body_size 参数。

Q: 健康检查报告显示大量链接为 403 或 429 状态，是否意味着资源不可用？

A: 并非绝对。部分网站会拒绝非浏览器的 HEAD 请求，或对同一 IP 的请求频率有限制。建议在配置文件中调整 CHECK_USER_AGENT 模拟主流浏览器，并设置 CHECK_INTERVAL 为 24 小时以上，避免触发反爬机制。对于确定有效的链接，可手动将其加入白名单跳过检查。

Q: 如何将现有浏览器书签（如 Chrome 导出的 HTML）迁移至 WebLink Navigator？

A: 项目暂不直接支持 HTML 书签解析，但可借助第三方工具将书签转换为 CSV 格式（例如使用 Bookmarks Export 插件）。CSV 文件需包含 title 和 url 两列，然后通过 Web 界面的 CSV 导入功能完成迁移。后续版本将考虑增加 Netscape 书签格式的原生支持。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
