# XNews 移动端资讯聚合系统

XNews 是一个面向移动端的高性能资讯聚合与分发平台，专为从零构建轻量级新闻聚合服务的设计者提供完整的技术落地方案。该项目定位于中小型内容站点、垂直领域资讯运营团队以及个人开发者，解决多源内容采集、移动端适配呈现、访问统计与热点追踪等实际生产环境中的核心痛点。XNews 采用前后端分离架构，以低于 50MB 的内存占用支撑日均十万级请求，在 2G 网络条件下仍能保持首屏加载时间低于 1.2 秒。

## 功能概览

- **多源内容聚合引擎**：内置可扩展的爬虫调度器，支持 RSS、JSON API、HTML 解析三种数据源接入方式，通过配置化管道实现数据清洗与字段映射。
- **移动端自适应渲染**：基于响应式 CSS 框架构建，针对 320px 至 768px 视口宽度进行精细调优，支持手势滑动、下拉刷新等移动原生交互体验。
- **热点文章智能排行**：综合访问量、评论数、发布时间三个维度计算内容热度分数，支持自定义衰减系数与时间窗口，每小时自动更新排行榜单。
- **分类标签动态管理**：提供树形分类结构，支持无限级子分类嵌套，每篇文章可绑定多个标签，通过倒排索引实现毫秒级分类检索。
- **访客行为轻量分析**：集成页面停留时长、跳出率、来源渠道三项核心指标，数据聚合颗粒度为小时，提供趋势折线图与对比柱状图展示。
- **管理后台一站式操作**：提供文章审核、定时发布、置顶管理、URL 屏蔽与白名单配置等运营工具，所有操作均记录操作日志以支持审计追溯。
- **开放 API 网关**：提供 RESTful 风格的数据输出接口，支持 JSON 与 JSONP 两种响应格式，API 调用频率限制为每 IP 每分钟 60 次。

## 应用场景

- **垂直行业资讯站点运营**：面向科技、财经、健康、教育等垂直领域的内容运营团队，XNews 可每日自动聚合来自数十个源站的最新文章，运营人员只需在后台进行二次筛选与人工复核，即可快速完成内容更新，无需手动编辑每一条稿件。
- **个人开发者快速搭建内容产品**：独立开发者可利用 XNews 在 30 分钟内完成一个移动端资讯产品的初始部署，将精力集中于内容选品与用户增长，而非重复开发内容管理、移动适配等通用基础模块。
- **企业内部信息聚合看板**：企业可将 XNews 部署于内网环境，聚合来自各部门公告、行业资讯、竞品动态等多个数据源，生成统一的信息看板，供管理层与一线员工实时查阅关键动态。
- **学术文献与技术文档聚合**：研究机构或技术社区可将 XNews 改造为文献聚合工具，通过配置 RSS 源与 DOI 解析器，实现论文预印本、技术博客、会议通知的集中呈现与分类浏览。

## 快速开始

以下步骤适用于 Ubuntu 22.04 LTS / Debian 12 环境，其他 Linux 发行版需根据包管理器调整对应命令。

```bash
# 步骤 1: 克隆项目代码仓库
git clone https://github.com/xnews-project/xnews-core.git
cd xnews-core

# 步骤 2: 安装项目依赖（使用 pip 与 npm）
pip install -r requirements.txt
npm install --production

# 步骤 3: 执行数据库迁移并启动服务
python manage.py migrate
python manage.py init_cache
python manage.py runserver 0.0.0.0:8000
```

生产环境部署建议使用 Gunicorn + Nginx 组合，具体配置参考 `deploy/` 目录下的示例文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或以上 | 核心后端运行环境，推荐使用 3.11 以获得性能优化 |
| Node.js | 18.x LTS | 前端构建工具与资产编译依赖 |
| PostgreSQL | 14 或以上 | 主数据库，用于存储文章、用户、分类等结构化数据 |
| Redis | 7.0 或以上 | 缓存与消息队列，用于热点排行更新与异步任务调度 |
| Nginx | 1.22 或以上 | 生产环境反向代理与静态资源服务（开发环境可省略） |
| Git | 2.30 或以上 | 版本控制与代码拉取工具 |
| 系统内存 | 最低 512MB | 生产环境建议 1GB 以上以保证并发处理能力 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | `docs/quickstart.md` | 如何在 10 分钟内完成首次部署？如何配置第一个数据源？ |
| 架构设计 | `docs/architecture.md` | 系统由哪些模块构成？数据流在各层之间如何传递？扩展性如何保证？ |
| API 参考 | `docs/api_reference.md` | 开放接口有哪些？请求参数与响应结构是什么？鉴权机制如何工作？ |
| 运维手册 | `docs/operations.md` | 如何配置日志轮转？如何监控服务健康状态？备份与恢复策略是什么？ |

## 资源列表

- http://m.3g.gqskj.cn/xnews/985435.htm
- http://m.3g.gqskj.cn/xnews/643591.htm
- http://m.3g.gqskj.cn/xnews/345373.htm
- http://m.3g.gqskj.cn/xnews/5602322.htm
- http://m.3g.gqskj.cn/xnews/50890.htm
- http://m.3g.gqskj.cn/xnews/7340997.htm
- http://m.3g.gqskj.cn/xnews/6516810.htm
- http://m.3g.gqskj.cn/xnews/848291.htm
- http://m.3g.gqskj.cn/xnews/307815.htm
- http://m.3g.gqskj.cn/xnews/0407.htm
- http://m.3g.gqskj.cn/xnews/0053033.htm
- http://m.3g.gqskj.cn/xnews/08711.htm
- http://m.3g.gqskj.cn/xnews/1490.htm
- http://m.3g.gqskj.cn/xnews/4712.htm
- http://m.3g.gqskj.cn/xnews/352073.htm
- http://m.3g.gqskj.cn/xnews/45472.htm
- http://m.3g.gqskj.cn/xnews/9105272.htm
- http://m.3g.gqskj.cn/xnews/14665.htm
- http://m.3g.gqskj.cn/xnews/30142.htm
- http://m.3g.gqskj.cn/xnews/7652457.htm
- http://m.3g.gqskj.cn/xnews/1971610.htm
- http://m.3g.gqskj.cn/xnews/71406.htm
- http://m.3g.gqskj.cn/xnews/153526.htm
- http://m.3g.gqskj.cn/xnews/5291093.htm
- http://m.3g.gqskj.cn/xnews/06837.htm
- http://m.3g.gqskj.cn/xnews/5941.htm
- http://m.3g.gqskj.cn/xnews/8758636.htm
- http://m.3g.gqskj.cn/xnews/974508.htm
- http://m.3g.gqskj.cn/xnews/41250.htm
- http://m.3g.gqskj.cn/xnews/1715.htm
- http://m.3g.gqskj.cn/xnews/0421.htm
- http://m.3g.gqskj.cn/xnews/0957889.htm
- http://m.3g.gqskj.cn/xnews/7343.htm
- http://m.3g.gqskj.cn/xnews/66578.htm
- http://m.3g.gqskj.cn/xnews/649568.htm
- http://m.3g.gqskj.cn/xnews/908720.htm
- http://m.3g.gqskj.cn/xnews/9862.htm
- http://m.3g.gqskj.cn/xnews/068141.htm
- http://m.3g.gqskj.cn/xnews/28030.htm
- http://m.3g.gqskj.cn/xnews/114541.htm
- http://m.3g.gqskj.cn/xnews/2506.htm
- http://m.3g.gqskj.cn/xnews/9183205.htm
- http://m.3g.gqskj.cn/xnews/2891365.htm
- http://m.3g.gqskj.cn/xnews/5326.htm
- http://m.3g.gqskj.cn/xnews/4210.htm
- http://m.3g.gqskj.cn/xnews/9783554.htm
- http://m.3g.gqskj.cn/xnews/55102.htm
- http://m.3g.gqskj.cn/xnews/4886467.htm
- http://m.3g.gqskj.cn/xnews/0920833.htm
- http://m.3g.gqskj.cn/xnews/6122.htm
- http://m.3g.gqskj.cn/xnews/97420.htm
- http://m.3g.gqskj.cn/xnews/1632.htm
- http://m.3g.gqskj.cn/xnews/22084.htm
- http://m.3g.gqskj.cn/xnews/3851009.htm
- http://m.3g.gqskj.cn/xnews/7848164.htm
- http://m.3g.gqskj.cn/xnews/1784941.htm
- http://m.3g.gqskj.cn/xnews/9878563.htm
- http://m.3g.gqskj.cn/xnews/7109832.htm
- http://m.3g.gqskj.cn/xnews/53560.htm
- http://m.3g.gqskj.cn/xnews/9869.htm
- http://m.3g.gqskj.cn/xnews/341108.htm
- http://m.3g.gqskj.cn/xnews/84194.htm
- http://m.3g.gqskj.cn/xnews/6907699.htm
- http://m.3g.gqskj.cn/xnews/2760.htm
- http://m.3g.gqskj.cn/xnews/4059.htm
- http://m.3g.gqskj.cn/xnews/6290248.htm
- http://m.3g.gqskj.cn/xnews/2947.htm
- http://m.3g.gqskj.cn/xnews/84327.htm
- http://m.3g.gqskj.cn/xnews/5702388.htm
- http://m.3g.gqskj.cn/xnews/5440.htm
- http://m.3g.gqskj.cn/xnews/28093.htm
- http://m.3g.gqskj.cn/xnews/6886.htm
- http://m.3g.gqskj.cn/xnews/0421886.htm
- http://m.3g.gqskj.cn/xnews/440695.htm
- http://m.3g.gqskj.cn/xnews/1862.htm
- http://m.3g.gqskj.cn/xnews/434648.htm
- http://m.3g.gqskj.cn/xnews/2132274.htm
- http://m.3g.gqskj.cn/xnews/10534.htm
- http://m.3g.gqskj.cn/xnews/537168.htm
- http://m.3g.gqskj.cn/xnews/35258.htm
- http://m.3g.gqskj.cn/xnews/668188.htm
- http://m.3g.gqskj.cn/xnews/0351.htm
- http://m.3g.gqskj.cn/xnews/39048.htm
- http://m.3g.gqskj.cn/xnews/9442790.htm
- http://m.3g.gqskj.cn/xnews/908194.htm
- http://m.3g.gqskj.cn/xnews/7272657.htm
- http://m.3g.gqskj.cn/xnews/5513.htm
- http://m.3g.gqskj.cn/xnews/00161.htm
- http://m.3g.gqskj.cn/xnews/4294.htm
- http://m.3g.gqskj.cn/xnews/47911.htm
- http://m.3g.gqskj.cn/xnews/53495.htm
- http://m.3g.gqskj.cn/xnews/88863.htm
- http://m.3g.gqskj.cn/xnews/9948980.htm
- http://m.3g.gqskj.cn/xnews/4536.htm
- http://m.3g.gqskj.cn/xnews/0197820.htm
- http://m.3g.gqskj.cn/xnews/878418.htm
- http://m.3g.gqskj.cn/xnews/1607.htm
- http://m.3g.gqskj.cn/xnews/7389.htm
- http://m.3g.gqskj.cn/xnews/1179536.htm
- http://m.3g.gqskj.cn/xnews/31069.htm
- http://m.3g.gqskj.cn/xnews/67211.htm
- http://m.3g.gqskj.cn/xnews/3215102.htm
- http://m.3g.gqskj.cn/xnews/547686.htm
- http://m.3g.gqskj.cn/xnews/738065.htm
- http://m.3g.gqskj.cn/xnews/02501.htm
- http://m.3g.gqskj.cn/xnews/174890.htm
- http://m.3g.gqskj.cn/xnews/8973858.htm
- http://m.3g.gqskj.cn/xnews/6405093.htm
- http://m.3g.gqskj.cn/xnews/4979690.htm
- http://m.3g.gqskj.cn/xnews/1673376.htm
- http://m.3g.gqskj.cn/xnews/79091.htm
- http://m.3g.gqskj.cn/xnews/606311.htm
- http://m.3g.gqskj.cn/xnews/17958.htm
- http://m.3g.gqskj.cn/xnews/53394.htm
- http://m.3g.gqskj.cn/xnews/248100.htm
- http://m.3g.gqskj.cn/xnews/3310436.htm
- http://m.3g.gqskj.cn/xnews/87555.htm
- http://m.3g.gqskj.cn/xnews/7300.htm
- http://m.3g.gqskj.cn/xnews/0072.htm
- http://m.3g.gqskj.cn/xnews/00687.htm
- http://m.3g.gqskj.cn/xnews/707025.htm
- http://m.3g.gqskj.cn/xnews/72718.htm
- http://m.3g.gqskj.cn/xnews/7077.htm
- http://m.3g.gqskj.cn/xnews/166901.htm
- http://m.3g.gqskj.cn/xnews/1167.htm
- http://m.3g.gqskj.cn/xnews/156671.htm
- http://m.3g.gqskj.cn/xnews/72263.htm
- http://m.3g.gqskj.cn/xnews/0660904.htm
- http://m.3g.gqskj.cn/xnews/28897.htm
- http://m.3g.gqskj.cn/xnews/7195342.htm
- http://m.3g.gqskj.cn/xnews/56964.htm
- http://m.3g.gqskj.cn/xnews/61833.htm
- http://m.3g.gqskj.cn/xnews/99298.htm
- http://m.3g.gqskj.cn/xnews/642159.htm
- http://m.3g.gqskj.cn/xnews/56645.htm
- http://m.3g.gqskj.cn/xnews/0361722.htm
- http://m.3g.gqskj.cn/xnews/6505.htm
- http://m.3g.gqskj.cn/xnews/838840.htm
- http://m.3g.gqskj.cn/xnews/64428.htm
- http://m.3g.gqskj.cn/xnews/9429166.htm
- http://m.3g.gqskj.cn/xnews/31565.htm
- http://m.3g.gqskj.cn/xnews/5335.htm
- http://m.3g.gqskj.cn/xnews/5937165.htm
- http://m.3g.gqskj.cn/xnews/293899.htm
- http://m.3g.gqskj.cn/xnews/50164.htm
- http://m.3g.gqskj.cn/xnews/67833.htm
- http://m.3g.gqskj.cn/xnews/698519.htm
- http://m.3g.gqskj.cn/xnews/8911.htm
- http://m.3g.gqskj.cn/xnews/6952.htm
- http://m.3g.gqskj.cn/xnews/75602.htm
- http://m.3g.gqskj.cn/xnews/8772.htm
- http://m.3g.gqskj.cn/xnews/996976.htm
- http://m.3g.gqskj.cn/xnews/54091.htm
- http://m.3g.gqskj.cn/xnews/715532.htm
- http://m.3g.gqskj.cn/xnews/840661.htm
- http://m.3g.gqskj.cn/xnews/8454735.htm
- http://m.3g.gqskj.cn/xnews/50705.htm
- http://m.3g.gqskj.cn/xnews/5646166.htm
- http://m.3g.gqskj.cn/xnews/653809.htm
- http://m.3g.gqskj.cn/xnews/092813.htm
- http://m.3g.gqskj.cn/xnews/8347279.htm
- http://m.3g.gqskj.cn/xnews/55769.htm
- http://m.3g.gqskj.cn/xnews/85864.htm
- http://m.3g.gqskj.cn/xnews/1415287.htm
- http://m.3g.gqskj.cn/xnews/9310.htm
- http://m.3g.gqskj.cn/xnews/8824403.htm
- http://m.3g.gqskj.cn/xnews/5172.htm
- http://m.3g.gqskj.cn/xnews/6262.htm
- http://m.3g.gqskj.cn/xnews/1954839.htm
- http://m.3g.gqskj.cn/xnews/3828.htm
- http://m.3g.gqskj.cn/xnews/423636.htm
- http://m.3g.gqskj.cn/xnews/45672.htm
- http://m.3g.gqskj.cn/xnews/50373.htm
- http://m.3g.gqskj.cn/xnews/46710.htm
- http://m.3g.gqskj.cn/xnews/267849.htm
- http://m.3g.gqskj.cn/xnews/1833932.htm
- http://m.3g.gqskj.cn/xnews/6765.htm
- http://m.3g.gqskj.cn/xnews/09284.htm
- http://m.3g.gqskj.cn/xnews/940909.htm
- http://m.3g.gqskj.cn/xnews/87011.htm
- http://m.3g.gqskj.cn/xnews/650182.htm
- http://m.3g.gqskj.cn/xnews/6363.htm
- http://m.3g.gqskj.cn/xnews/2152.htm
- http://m.3g.gqskj.cn/xnews/4972.htm
- http://m.3g.gqskj.cn/xnews/5325418.htm
- http://m.3g.gqskj.cn/xnews/0423.htm
- http://m.3g.gqskj.cn/xnews/2241046.htm
- http://m.3g.gqskj.cn/xnews/8602802.htm
- http://m.3g.gqskj.cn/xnews/509130.htm
- http://m.3g.gqskj.cn/xnews/0191.htm
- http://m.3g.gqskj.cn/xnews/06722.htm
- http://m.3g.gqskj.cn/xnews/2144255.htm
- http://m.3g.gqskj.cn/xnews/9427957.htm
- http://m.3g.gqskj.cn/xnews/6022.htm
- http://m.3g.gqskj.cn/xnews/91350.htm
- http://m.3g.gqskj.cn/xnews/1759798.htm
- http://m.3g.gqskj.cn/xnews/746964.htm
- http://m.3g.gqskj.cn/xnews/341214.htm
- http://m.3g.gqskj.cn/xnews/280713.htm
- http://m.3g.gqskj.cn/xnews/318039.htm
- http://m.3g.gqskj.cn/xnews/4711536.htm
- http://m.3g.gqskj.cn/xnews/7881813.htm
- http://m.3g.gqskj.cn/xnews/4396.htm
- http://m.3g.gqskj.cn/xnews/2156090.htm
- http://m.3g.gqskj.cn/xnews/1234.htm
- http://m.3g.gqskj.cn/xnews/54861.htm
- http://m.3g.gqskj.cn/xnews/0434914.htm
- http://m.3g.gqskj.cn/xnews/751078.htm
- http://m.3g.gqskj.cn/xnews/01740.htm
- http://m.3g.gqskj.cn/xnews/648497.htm
- http://m.3g.gqskj.cn/xnews/369220.htm
- http://m.3g.gqskj.cn/xnews/6488579.htm
- http://m.3g.gqskj.cn/xnews/3998.htm
- http://m.3g.gqskj.cn/xnews/4935408.htm
- http://m.3g.gqskj.cn/xnews/3653.htm
- http://m.3g.gqskj.cn/xnews/616679.htm
- http://m.3g.gqskj.cn/xnews/822470.htm
- http://m.3g.gqskj.cn/xnews/9961591.htm
- http://m.3g.gqskj.cn/xnews/497997.htm
- http://m.3g.gqskj.cn/xnews/377220.htm
- http://m.3g.gqskj.cn/xnews/7738845.htm
- http://m.3g.gqskj.cn/xnews/480901.htm
- http://m.3g.gqskj.cn/xnews/27415.htm
- http://m.3g.gqskj.cn/xnews/307416.htm
- http://m.3g.gqskj.cn/xnews/89770.htm
- http://m.3g.gqskj.cn/xnews/5051.htm
- http://m.3g.gqskj.cn/xnews/1386.htm
- http://m.3g.gqskj.cn/xnews/54102.htm
- http://m.3g.gqskj.cn/xnews/228829.htm
- http://m.3g.gqskj.cn/xnews/03602.htm
- http://m.3g.gqskj.cn/xnews/1885459.htm
- http://m.3g.gqskj.cn/xnews/81930.htm
- http://m.3g.gqskj.cn/xnews/0192.htm
- http://m.3g.gqskj.cn/xnews/91962.htm
- http://m.3g.gqskj.cn/xnews/5900642.htm
- http://m.3g.gqskj.cn/xnews/2085141.htm
- http://m.3g.gqskj.cn/xnews/54765.htm
- http://m.3g.gqskj.cn/xnews/6083.htm
- http://m.3g.gqskj.cn/xnews/7960670.htm
- http://m.3g.gqskj.cn/xnews/64633.htm
- http://m.3g.gqskj.cn/xnews/823767.htm
- http://m.3g.gqskj.cn/xnews/6865815.htm
- http://m.3g.gqskj.cn/xnews/786134.htm
- http://m.3g.gqskj.cn/xnews/143738.htm
- http://m.3g.gqskj.cn/xnews/7505.htm
- http://m.3g.gqskj.cn/xnews/49949.htm
- http://m.3g.gqskj.cn/xnews/86115.htm
- http://m.3g.gqskj.cn/xnews/929497.htm
- http://m.3g.gqskj.cn/xnews/895246.htm
- http://m.3g.gqskj.cn/xnews/83038.htm

## 项目结构

```
xnews-core/
├── api/                                # RESTful API 模块
│   ├── endpoints/                      # 各资源端点实现
│   │   ├── articles.py                 # 文章列表、详情、搜索接口
│   │   ├── categories.py               # 分类树与标签接口
│   │   └── analytics.py                # 访问统计与热度数据接口
│   ├── middleware/                     # 请求拦截与处理中间件
│   │   ├── ratelimit.py                # 基于令牌桶的 IP 限流中间件
│   │   └── cors.py                     # 跨域资源共享配置
│   └── validators/                     # 请求参数校验器
│       ├── article_validator.py        # 文章新增与更新校验规则
│       └── query_validator.py          # 分页与排序参数校验
├── core/                               # 核心业务逻辑层
│   ├── aggregator/                     # 多源内容聚合引擎
│   │   ├── fetcher.py                  # 基于 aiohttp 的异步 HTTP 获取器
│   │   ├── parser.py                   # 可插拔的解析器注册与调度
│   │   └── pipeline.py                 # 清洗、去重、入库流水线
│   ├── ranking/                        # 热点排行计算模块
│   │   ├── scorer.py                   # 多因子加权热度评分算法
│   │   └── cache_updater.py            # 定时刷新 Redis 排行缓存
│   └── models/                         # 数据模型定义（SQLAlchemy ORM）
│       ├── article.py                  # 文章表映射与关联关系
│       ├── category.py                 # 分类表及嵌套集合树结构
│       └── visit_log.py                # 访问日志聚合模型
├── web/                                # 移动端前端呈现
│   ├── static/                         # 编译后静态资产
│   │   ├── css/                        # 响应式样式表（移动优先）
│   │   └── js/                         # 交互逻辑与懒加载实现
│   ├── templates/                      # Jinja2 模板文件
│   │   ├── layout.html                 # 基础骨架模板
│   │   ├── index.html                  # 首页信息流聚合
│   │   └── detail.html                 # 文章详情页
│   └── assets/                         # 源素材（SCSS / ES6 源码）
├── manage/                             # 管理后台模块
│   ├── dashboard/                      # 运营仪表盘视图
│   ├── audit/                          # 文章审核工作流
│   └── settings/                       # 系统配置项管理界面
├── deploy/                             # 部署与运维脚本
│   ├── docker/                         # Docker Compose 与 Dockerfile
│   ├── nginx/                          # Nginx 站点配置模板
│   └── systemd/                        # Systemd 服务单元文件
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 各模块单元测试用例
│   └── integration/                    # 端到端 API 测试脚本
├── requirements.txt                    # Python 后端依赖清单
├── package.json                        # Node.js 前端构建依赖
├── manage.py                           # Django 风格管理命令行入口
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

1. 查阅 `docs/contributing.md` 了解完整的贡献流程与代码规范，签署贡献者许可协议后即可参与开发。所有贡献需通过 GitHub Pull Request 流程提交，目标分支为 `develop`。

2. 在本地环境运行完整的测试套件 `pytest tests/`，确保所有已有测试用例通过，并为新增功能或修复补丁编写对应的测试用例，测试覆盖率不得低于 85%。

3. 提交信息遵循 Conventional Commits 规范（格式为 `<type>(<scope>): <subject>`），类型包括 feat、fix、docs、refactor、perf、test 等，scope 填写影响的模块名称。

4. 若涉及前端界面变更，需附上移动端（iPhone SE / Pixel 5）的截图或录屏，以验证响应式适配效果；后端变更需在 PR 描述中说明数据库迁移脚本的版本号与回滚步骤。

5. 代码审查通过后，由核心维护者合并至 `main` 分支并触发 CI/CD 自动构建与部署至预发布环境，经过 24 小时稳定性观察后正式上线。

## 常见问题

**问：XNews 是否支持 HTTPS 协议访问资源？**

答：XNews 的后端服务本身不强制要求 HTTPS，但生产环境强烈建议在 Nginx 层面配置 SSL 证书以启用 HTTPS。项目提供的 Nginx 配置模板中包含了 HTTP 到 HTTPS 的强制重定向规则，您只需将证书文件放置于指定目录并解除注释即可。对于资源列表中包含的 HTTP 外部链接，XNews 通过内容代理模式进行获取，不会因协议不一致导致混合内容错误。

**问：如何增加新的内容源？是否支持自定义字段映射？**

答：新增内容源只需在 `core/aggregator/fetcher.py` 中注册一个新的源配置项，包含源类型（rss / json / html）、请求头、更新频率等参数。对于非标准格式的数据源，您可以在 `parser.py` 中实现一个自定义解析器类，重写 `parse()` 方法来完成字段映射。项目提供了腾讯新闻、微博热点、知乎热榜等常见源的内置示例，可作为参照模板。

**问：XNews 在低配置服务器上运行缓慢，如何优化性能？**

答：首先检查 Redis 缓存是否正常工作，热点排行与分类树数据应全部缓存于 Redis 中，避免重复查询 PostgreSQL。其次可调整 `scorer.py` 中的热度计算频率，从默认的每小时改为每四小时运行，减少后台任务负载。最后建议启用 Nginx 的 gzip 压缩与静态资源缓存，将 CSS 与 JavaScript 文件的缓存时间设置为 7 天。若流量持续增长，可考虑增加 Gunicorn worker 数量至 CPU 核心数的 2 倍。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:45
