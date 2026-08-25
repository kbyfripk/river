# NewsArchive Gateway

NewsArchive Gateway 是一个面向移动端新闻资源聚合与结构化访问的开源网关中间件。该项目定位为技术资源与外链汇总站，主要服务于需要批量采集、归档、检索移动端新闻页面（.htm）的开发者、数据研究员以及内容聚合平台运维人员。通过提供稳定的URL映射规则与轻量级元数据缓存层，本项目解决了移动新闻资源分散、原始链接缺乏语义描述以及采集过程中链接失效难以追溯等核心痛点。

## 功能概览

批量新闻链接导入与规范化存储 提供标准化的URL导入接口，支持将形如 http://m.3g.gqskj.cn/xnews/*.htm 的海量链接纳入统一管理池。

资源状态健康检查 内置异步检测任务，定时对已收录的新闻链接进行可达性与响应时间探测，自动标记异常链接。

轻量级标签分类引擎 基于URL路径与ID数值区间，自动为新闻资源打上预定义分类标签（如科技、社会、财经等），便于后续筛选。

全文元数据提取 支持通过可配置的XPath或正则表达式规则，从目标页面提取标题、发布时间、正文摘要等关键字段。

只读镜像缓存模式 提供可选的本地缓存层，对已访问的新闻页面生成静态HTML快照，减少源站压力并提升重复访问速度。

RESTful查询接口 提供基于时间范围、标签类型、链接状态等多条件组合的查询API，返回结构化JSON数据。

管理控制台面板 内置简易Web管理界面，可视化展示资源总数、健康率、分类分布及最新采集日志。

## 应用场景

移动端新闻聚合应用后端 开发者可基于本项目构建新闻聚合类App的后端数据源，通过定期拉取和解析指定的新闻链接，为前端提供结构化的文章列表与详情内容，无需自行维护爬虫调度与链接管理逻辑。

学术研究与舆情分析 数据研究员可利用本项目的批量导入与元数据提取功能，快速建立特定时间段或主题的新闻语料库，用于自然语言处理、情感分析或热点事件追踪等研究任务。

企业内部知识库归档 企业运维人员可将本项目部署为内部新闻情报归档系统，定期收录与业务相关的行业新闻链接，并通过标签分类功能建立可检索的企业新闻知识库。

个人开发者自建书签导航 个人开发者可利用本项目的链接管理与健康检查功能，替代传统浏览器书签，构建一个带有自动失效检测的专属新闻资源导航页面。

## 快速开始

以下步骤将引导您在本地环境快速启动 NewsArchive Gateway 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newsarchive-gateway.git

# 进入项目目录
cd newsarchive-gateway

# 安装项目依赖（基于Python 3.9+）
pip install -r requirements.txt

# 初始化本地配置与数据库
python scripts/init_config.py
python scripts/migrate_db.py

# 启动开发服务器
python app.py --port 8080 --debug
```

服务启动后，访问 http://localhost:8080/admin 即可进入管理控制面板。使用默认账号 admin / admin123 完成首次登录，建议在生产环境中立即修改默认密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.9 至 3.11 | 核心运行环境，推荐使用3.10版本以保证最佳兼容性 |
| SQLite | 3.35.0 以上 | 默认嵌入式数据库，用于存储链接元数据与状态信息 |
| Redis | 6.2 以上 | 可选依赖，用于缓存层与分布式任务队列（生产环境推荐） |
| lxml | 4.9.0 以上 | HTML解析核心库，用于XPath与正则表达式数据提取 |
| requests | 2.28.0 以上 | HTTP客户端库，用于执行链接健康检查与页面抓取 |
| apscheduler | 3.9.0 以上 | 后台任务调度库，用于定时执行资源状态检测 |
| flask | 2.2.0 以上 | Web管理界面与REST API服务框架 |
| pytest | 7.0.0 以上 | 单元测试与集成测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 用户手册 | /docs/user-guide/import.md | 如何批量导入新闻链接？支持哪些导入格式？ |
| 用户手册 | /docs/user-guide/query.md | 如何使用REST API查询已归档的新闻资源？ |
| 运维指南 | /docs/ops/deployment.md | 如何将服务部署至生产环境？有哪些推荐的部署策略？ |
| 运维指南 | /docs/ops/monitoring.md | 如何监控服务运行状态与资源健康检查任务？ |
| 开发指南 | /docs/dev/extract-rules.md | 如何为新的新闻源编写自定义元数据提取规则？ |
| 开发指南 | /docs/dev/api-contract.md | 内部模块之间的接口契约与数据流定义是什么？ |

## 资源列表

- http://m.3g.gqskj.cn/xnews/8539.htm
- http://m.3g.gqskj.cn/xnews/5162.htm
- http://m.3g.gqskj.cn/xnews/772211.htm
- http://m.3g.gqskj.cn/xnews/679470.htm
- http://m.3g.gqskj.cn/xnews/5896.htm
- http://m.3g.gqskj.cn/xnews/5778.htm
- http://m.3g.gqskj.cn/xnews/737491.htm
- http://m.3g.gqskj.cn/xnews/007293.htm
- http://m.3g.gqskj.cn/xnews/155663.htm
- http://m.3g.gqskj.cn/xnews/27927.htm
- http://m.3g.gqskj.cn/xnews/09783.htm
- http://m.3g.gqskj.cn/xnews/8772539.htm
- http://m.3g.gqskj.cn/xnews/51987.htm
- http://m.3g.gqskj.cn/xnews/4153928.htm
- http://m.3g.gqskj.cn/xnews/4851369.htm
- http://m.3g.gqskj.cn/xnews/8714.htm
- http://m.3g.gqskj.cn/xnews/3468582.htm
- http://m.3g.gqskj.cn/xnews/358829.htm
- http://m.3g.gqskj.cn/xnews/756934.htm
- http://m.3g.gqskj.cn/xnews/636543.htm
- http://m.3g.gqskj.cn/xnews/89317.htm
- http://m.3g.gqskj.cn/xnews/7873083.htm
- http://m.3g.gqskj.cn/xnews/08182.htm
- http://m.3g.gqskj.cn/xnews/526512.htm
- http://m.3g.gqskj.cn/xnews/8701311.htm
- http://m.3g.gqskj.cn/xnews/340687.htm
- http://m.3g.gqskj.cn/xnews/9754.htm
- http://m.3g.gqskj.cn/xnews/1199921.htm
- http://m.3g.gqskj.cn/xnews/04034.htm
- http://m.3g.gqskj.cn/xnews/6249497.htm
- http://m.3g.gqskj.cn/xnews/7617.htm
- http://m.3g.gqskj.cn/xnews/606268.htm
- http://m.3g.gqskj.cn/xnews/7295.htm
- http://m.3g.gqskj.cn/xnews/0627311.htm
- http://m.3g.gqskj.cn/xnews/029201.htm
- http://m.3g.gqskj.cn/xnews/11908.htm
- http://m.3g.gqskj.cn/xnews/864191.htm
- http://m.3g.gqskj.cn/xnews/3194.htm
- http://m.3g.gqskj.cn/xnews/038050.htm
- http://m.3g.gqskj.cn/xnews/606681.htm
- http://m.3g.gqskj.cn/xnews/0868.htm
- http://m.3g.gqskj.cn/xnews/425189.htm
- http://m.3g.gqskj.cn/xnews/64462.htm
- http://m.3g.gqskj.cn/xnews/2435046.htm
- http://m.3g.gqskj.cn/xnews/70392.htm
- http://m.3g.gqskj.cn/xnews/885825.htm
- http://m.3g.gqskj.cn/xnews/2121506.htm
- http://m.3g.gqskj.cn/xnews/83477.htm
- http://m.3g.gqskj.cn/xnews/0803439.htm
- http://m.3g.gqskj.cn/xnews/6171.htm
- http://m.3g.gqskj.cn/xnews/17811.htm
- http://m.3g.gqskj.cn/xnews/2366155.htm
- http://m.3g.gqskj.cn/xnews/9378.htm
- http://m.3g.gqskj.cn/xnews/96326.htm
- http://m.3g.gqskj.cn/xnews/2454084.htm
- http://m.3g.gqskj.cn/xnews/8781060.htm
- http://m.3g.gqskj.cn/xnews/975753.htm
- http://m.3g.gqskj.cn/xnews/60733.htm
- http://m.3g.gqskj.cn/xnews/33460.htm
- http://m.3g.gqskj.cn/xnews/082296.htm
- http://m.3g.gqskj.cn/xnews/21632.htm
- http://m.3g.gqskj.cn/xnews/4874.htm
- http://m.3g.gqskj.cn/xnews/5736.htm
- http://m.3g.gqskj.cn/xnews/90399.htm
- http://m.3g.gqskj.cn/xnews/2851637.htm
- http://m.3g.gqskj.cn/xnews/32158.htm
- http://m.3g.gqskj.cn/xnews/009875.htm
- http://m.3g.gqskj.cn/xnews/0959765.htm
- http://m.3g.gqskj.cn/xnews/369008.htm
- http://m.3g.gqskj.cn/xnews/57045.htm
- http://m.3g.gqskj.cn/xnews/82920.htm
- http://m.3g.gqskj.cn/xnews/820281.htm
- http://m.3g.gqskj.cn/xnews/52718.htm
- http://m.3g.gqskj.cn/xnews/248615.htm
- http://m.3g.gqskj.cn/xnews/387009.htm
- http://m.3g.gqskj.cn/xnews/6435997.htm
- http://m.3g.gqskj.cn/xnews/68679.htm
- http://m.3g.gqskj.cn/xnews/6751699.htm
- http://m.3g.gqskj.cn/xnews/7195968.htm
- http://m.3g.gqskj.cn/xnews/41351.htm
- http://m.3g.gqskj.cn/xnews/98748.htm
- http://m.3g.gqskj.cn/xnews/4892425.htm
- http://m.3g.gqskj.cn/xnews/5466.htm
- http://m.3g.gqskj.cn/xnews/34162.htm
- http://m.3g.gqskj.cn/xnews/6738.htm
- http://m.3g.gqskj.cn/xnews/3358716.htm
- http://m.3g.gqskj.cn/xnews/6397181.htm
- http://m.3g.gqskj.cn/xnews/0878.htm
- http://m.3g.gqskj.cn/xnews/181180.htm
- http://m.3g.gqskj.cn/xnews/0586.htm
- http://m.3g.gqskj.cn/xnews/715714.htm
- http://m.3g.gqskj.cn/xnews/8646663.htm
- http://m.3g.gqskj.cn/xnews/0121.htm
- http://m.3g.gqskj.cn/xnews/70759.htm
- http://m.3g.gqskj.cn/xnews/6810708.htm
- http://m.3g.gqskj.cn/xnews/336691.htm
- http://m.3g.gqskj.cn/xnews/62498.htm
- http://m.3g.gqskj.cn/xnews/8875.htm
- http://m.3g.gqskj.cn/xnews/5541.htm
- http://m.3g.gqskj.cn/xnews/6049457.htm
- http://m.3g.gqskj.cn/xnews/75949.htm
- http://m.3g.gqskj.cn/xnews/17848.htm
- http://m.3g.gqskj.cn/xnews/474920.htm
- http://m.3g.gqskj.cn/xnews/965673.htm
- http://m.3g.gqskj.cn/xnews/1767.htm
- http://m.3g.gqskj.cn/xnews/6924.htm
- http://m.3g.gqskj.cn/xnews/62034.htm
- http://m.3g.gqskj.cn/xnews/46554.htm
- http://m.3g.gqskj.cn/xnews/65653.htm
- http://m.3g.gqskj.cn/xnews/95458.htm
- http://m.3g.gqskj.cn/xnews/235368.htm
- http://m.3g.gqskj.cn/xnews/3079422.htm
- http://m.3g.gqskj.cn/xnews/1277.htm
- http://m.3g.gqskj.cn/xnews/75759.htm
- http://m.3g.gqskj.cn/xnews/9150.htm
- http://m.3g.gqskj.cn/xnews/2309.htm
- http://m.3g.gqskj.cn/xnews/7326753.htm
- http://m.3g.gqskj.cn/xnews/9060865.htm
- http://m.3g.gqskj.cn/xnews/9777.htm
- http://m.3g.gqskj.cn/xnews/1150.htm
- http://m.3g.gqskj.cn/xnews/5500638.htm
- http://m.3g.gqskj.cn/xnews/79327.htm
- http://m.3g.gqskj.cn/xnews/686746.htm
- http://m.3g.gqskj.cn/xnews/09455.htm
- http://m.3g.gqskj.cn/xnews/0352.htm
- http://m.3g.gqskj.cn/xnews/3844.htm
- http://m.3g.gqskj.cn/xnews/412932.htm
- http://m.3g.gqskj.cn/xnews/8335.htm
- http://m.3g.gqskj.cn/xnews/6343229.htm
- http://m.3g.gqskj.cn/xnews/80194.htm
- http://m.3g.gqskj.cn/xnews/8853.htm
- http://m.3g.gqskj.cn/xnews/816904.htm
- http://m.3g.gqskj.cn/xnews/940805.htm
- http://m.3g.gqskj.cn/xnews/528007.htm
- http://m.3g.gqskj.cn/xnews/9171.htm
- http://m.3g.gqskj.cn/xnews/0433.htm
- http://m.3g.gqskj.cn/xnews/8746127.htm
- http://m.3g.gqskj.cn/xnews/7590.htm
- http://m.3g.gqskj.cn/xnews/4321182.htm
- http://m.3g.gqskj.cn/xnews/779219.htm
- http://m.3g.gqskj.cn/xnews/137908.htm
- http://m.3g.gqskj.cn/xnews/84825.htm
- http://m.3g.gqskj.cn/xnews/8196.htm
- http://m.3g.gqskj.cn/xnews/85898.htm
- http://m.3g.gqskj.cn/xnews/193733.htm
- http://m.3g.gqskj.cn/xnews/9492.htm
- http://m.3g.gqskj.cn/xnews/49762.htm
- http://m.3g.gqskj.cn/xnews/7731.htm
- http://m.3g.gqskj.cn/xnews/1193308.htm
- http://m.3g.gqskj.cn/xnews/619768.htm
- http://m.3g.gqskj.cn/xnews/11391.htm
- http://m.3g.gqskj.cn/xnews/804440.htm
- http://m.3g.gqskj.cn/xnews/33001.htm
- http://m.3g.gqskj.cn/xnews/901386.htm
- http://m.3g.gqskj.cn/xnews/6201.htm
- http://m.3g.gqskj.cn/xnews/5488711.htm
- http://m.3g.gqskj.cn/xnews/79195.htm
- http://m.3g.gqskj.cn/xnews/646735.htm
- http://m.3g.gqskj.cn/xnews/7978815.htm
- http://m.3g.gqskj.cn/xnews/616880.htm
- http://m.3g.gqskj.cn/xnews/063469.htm
- http://m.3g.gqskj.cn/xnews/2578661.htm
- http://m.3g.gqskj.cn/xnews/02177.htm
- http://m.3g.gqskj.cn/xnews/8425666.htm
- http://m.3g.gqskj.cn/xnews/0001850.htm
- http://m.3g.gqskj.cn/xnews/06475.htm
- http://m.3g.gqskj.cn/xnews/101086.htm
- http://m.3g.gqskj.cn/xnews/95108.htm
- http://m.3g.gqskj.cn/xnews/321443.htm
- http://m.3g.gqskj.cn/xnews/158409.htm
- http://m.3g.gqskj.cn/xnews/5599444.htm
- http://m.3g.gqskj.cn/xnews/12622.htm
- http://m.3g.gqskj.cn/xnews/6545.htm
- http://m.3g.gqskj.cn/xnews/680780.htm
- http://m.3g.gqskj.cn/xnews/0317608.htm
- http://m.3g.gqskj.cn/xnews/65569.htm
- http://m.3g.gqskj.cn/xnews/7118.htm
- http://m.3g.gqskj.cn/xnews/72230.htm
- http://m.3g.gqskj.cn/xnews/8048308.htm
- http://m.3g.gqskj.cn/xnews/4504173.htm
- http://m.3g.gqskj.cn/xnews/6241.htm
- http://m.3g.gqskj.cn/xnews/4734.htm
- http://m.3g.gqskj.cn/xnews/9797.htm
- http://m.3g.gqskj.cn/xnews/2341.htm
- http://m.3g.gqskj.cn/xnews/5803505.htm
- http://m.3g.gqskj.cn/xnews/239270.htm
- http://m.3g.gqskj.cn/xnews/068494.htm
- http://m.3g.gqskj.cn/xnews/164492.htm
- http://m.3g.gqskj.cn/xnews/9429.htm
- http://m.3g.gqskj.cn/xnews/3462.htm
- http://m.3g.gqskj.cn/xnews/555788.htm
- http://m.3g.gqskj.cn/xnews/2040301.htm
- http://m.3g.gqskj.cn/xnews/53721.htm
- http://m.3g.gqskj.cn/xnews/051149.htm
- http://m.3g.gqskj.cn/xnews/0895.htm
- http://m.3g.gqskj.cn/xnews/47233.htm
- http://m.3g.gqskj.cn/xnews/07008.htm
- http://m.3g.gqskj.cn/xnews/3002.htm
- http://m.3g.gqskj.cn/xnews/405347.htm
- http://m.3g.gqskj.cn/xnews/1523998.htm
- http://m.3g.gqskj.cn/xnews/8873.htm
- http://m.3g.gqskj.cn/xnews/5551526.htm
- http://m.3g.gqskj.cn/xnews/18755.htm
- http://m.3g.gqskj.cn/xnews/5834974.htm
- http://m.3g.gqskj.cn/xnews/0705467.htm
- http://m.3g.gqskj.cn/xnews/257484.htm
- http://m.3g.gqskj.cn/xnews/10677.htm
- http://m.3g.gqskj.cn/xnews/9838748.htm
- http://m.3g.gqskj.cn/xnews/24882.htm
- http://m.3g.gqskj.cn/xnews/0938.htm
- http://m.3g.gqskj.cn/xnews/05989.htm
- http://m.3g.gqskj.cn/xnews/842946.htm
- http://m.3g.gqskj.cn/xnews/9923.htm
- http://m.3g.gqskj.cn/xnews/840713.htm
- http://m.3g.gqskj.cn/xnews/597314.htm
- http://m.3g.gqskj.cn/xnews/091337.htm
- http://m.3g.gqskj.cn/xnews/1232966.htm
- http://m.3g.gqskj.cn/xnews/2654609.htm
- http://m.3g.gqskj.cn/xnews/0490.htm
- http://m.3g.gqskj.cn/xnews/1164.htm
- http://m.3g.gqskj.cn/xnews/668429.htm
- http://m.3g.gqskj.cn/xnews/41964.htm
- http://m.3g.gqskj.cn/xnews/2015.htm
- http://m.3g.gqskj.cn/xnews/4765.htm
- http://m.3g.gqskj.cn/xnews/441541.htm
- http://m.3g.gqskj.cn/xnews/590069.htm
- http://m.3g.gqskj.cn/xnews/23190.htm
- http://m.3g.gqskj.cn/xnews/2729742.htm
- http://m.3g.gqskj.cn/xnews/481134.htm
- http://m.3g.gqskj.cn/xnews/865115.htm
- http://m.3g.gqskj.cn/xnews/78090.htm
- http://m.3g.gqskj.cn/xnews/6400355.htm
- http://m.3g.gqskj.cn/xnews/423738.htm
- http://m.3g.gqskj.cn/xnews/39161.htm
- http://m.3g.gqskj.cn/xnews/3576.htm
- http://m.3g.gqskj.cn/xnews/9113692.htm
- http://m.3g.gqskj.cn/xnews/8323.htm
- http://m.3g.gqskj.cn/xnews/2212006.htm
- http://m.3g.gqskj.cn/xnews/802652.htm
- http://m.3g.gqskj.cn/xnews/93785.htm
- http://m.3g.gqskj.cn/xnews/45629.htm
- http://m.3g.gqskj.cn/xnews/6373840.htm
- http://m.3g.gqskj.cn/xnews/78309.htm
- http://m.3g.gqskj.cn/xnews/314978.htm
- http://m.3g.gqskj.cn/xnews/4285.htm
- http://m.3g.gqskj.cn/xnews/3587.htm
- http://m.3g.gqskj.cn/xnews/7308947.htm
- http://m.3g.gqskj.cn/xnews/331691.htm
- http://m.3g.gqskj.cn/xnews/78497.htm
- http://m.3g.gqskj.cn/xnews/33235.htm

## 项目结构

```
newsarchive-gateway/
├── app/                                    # 核心应用主目录
│   ├── __init__.py                         # 应用工厂模式初始化
│   ├── routes/                             # 路由与视图控制器层
│   │   ├── api.py                          # RESTful API接口定义
│   │   ├── admin.py                        # 管理控制台路由
│   │   └── health.py                       # 健康检查与探针接口
│   ├── models/                             # 数据模型与ORM映射
│   │   ├── link.py                         # 新闻链接实体模型
│   │   ├── tag.py                          # 标签分类模型
│   │   └── task.py                         # 异步任务记录模型
│   ├── services/                           # 业务逻辑服务层
│   │   ├── fetcher.py                      # 页面抓取与解析服务
│   │   ├── checker.py                      # 链接状态检测服务
│   │   ├── cache.py                        # 缓存读写服务（Redis）
│   │   └── scheduler.py                    # 定时任务调度服务
│   └── utils/                              # 通用工具函数集
│       ├── extractors.py                   # XPath/正则提取器工具箱
│       ├── validators.py                   # URL与数据校验器
│       └── converters.py                   # 数据格式转换工具
├── config/                                 # 配置文件目录
│   ├── default.py                          # 默认配置项
│   ├── production.py                       # 生产环境配置覆盖
│   └── development.py                      # 开发环境配置覆盖
├── scripts/                                # 运维与辅助脚本
│   ├── init_config.py                      # 初始化配置文件
│   ├── migrate_db.py                       # 数据库迁移与建表
│   └── import_links.py                     # 批量链接导入命令行工具
├── tests/                                  # 测试代码目录
│   ├── unit/                               # 单元测试用例
│   ├── integration/                        # 集成测试用例
│   └── fixtures/                           # 测试数据与固定响应
├── static/                                 # 前端静态资源
│   ├── css/                                # 管理界面样式表
│   └── js/                                 # 管理界面交互脚本
├── templates/                              # Jinja2模板文件
│   ├── dashboard.html                      # 管理控制台主面板
│   └── link_list.html                      # 链接列表与查询页面
├── logs/                                   # 日志文件存储目录（运行时生成）
├── requirements.txt                        # Python依赖清单
├── app.py                                  # 应用启动入口脚本
├── README.md                               # 项目说明文档（本文件）
└── LICENSE                                 # MIT许可证文件
```

## 贡献指南

我们欢迎社区开发者提交贡献。请遵循以下步骤参与项目开发。

提交Issue报告缺陷或新特性需求 在GitHub Issues页面提交详细的缺陷复现步骤或新特性描述，并附上相关的日志片段或使用场景说明。

Fork项目并创建特性分支 将本项目Fork至个人账户，然后基于最新的main分支创建命名规范的功能分支（如 feature/improve-extractor 或 fix/checker-timeout）。

编写代码与单元测试 遵循项目代码风格（PEP 8），为新增或修改的代码编写对应的单元测试用例，确保测试覆盖率达到现有标准。

签署开发者贡献许可协议 首次提交Pull Request前，需在PR评论中明确声明同意本项目的开发者贡献许可协议，表明您有权且自愿贡献代码。

发起Pull Request并等待代码审查 将特性分支推送至个人Fork仓库，然后向本项目的main分支发起Pull Request。PR描述需清晰说明变更内容、影响范围以及测试结果。项目维护者将在三个工作日内进行审查。

## 常见问题

Q: 导入大量链接后，健康检查任务多久执行一次？如何调整检查频率？

A: 默认情况下，健康检查任务每60分钟执行一次，每次并发检查100个链接。您可以通过修改配置文件中的 CHECK_INTERVAL_MINUTES 和 CHECK_BATCH_SIZE 参数来调整检查频率与并发数。修改后重启服务即可生效。

Q: 部分新闻链接返回403或404状态码，系统如何处理这些异常链接？

A: 系统会将连续三次检查失败的链接标记为 DEAD 状态，并记录最后一次失败的HTTP状态码与时间戳。被标记为 DEAD 的链接将不再参与后续的自动检查任务，但仍可通过管理界面手动重新触发单次检查。您也可以设置自动清理策略，定期移除长期处于 DEAD 状态的链接。

Q: 是否支持自定义元数据提取规则？规则编写复杂度如何？

A: 支持。您可以在管理控制台的「规则管理」页面添加新的提取规则。规则采用JSON格式定义，包含目标字段名称、提取类型（xpath或regex）以及对应的表达式。对于常见的新闻页面结构，我们提供了预置模板。若您对XPath或正则表达式不熟悉，建议参考我们提供的示例规则进行修改，或直接在社区讨论区提出具体需求。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:47
