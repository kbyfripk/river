# LinkVault 聚合资源索引系统

LinkVault 是一个面向技术内容聚合与知识导航的开源资源索引系统，旨在帮助开发者、技术研究人员以及内容运营团队高效管理、分类检索和快速访问分布在各类来源中的外部技术链接。系统以轻量化 Markdown 数据源为核心，提供结构化的链接入库、标签过滤、快照备份与访问可用性检测能力，适用于构建个人书签库、团队技术周报素材源、自动化外链监控节点以及第三方内容聚合服务的基础数据层。

目标用户包括需要维护大量外链资源的独立开发者、技术内容编辑、开源社区文档维护者以及企业知识管理团队。LinkVault 不提供全文爬取或内容存储功能，仅对链接元数据（标题、来源域名、抓取时间、状态码、内容摘要哈希）进行索引与管理，符合开源项目合规使用规范。

## 功能概览

批量链接导入与去重：支持通过 CSV、JSON Lines 以及纯文本列表批量提交 URL，系统自动基于标准化域名与路径指纹执行去重，避免重复入库。

多维度标签分类体系：每个链接可附加多个层级标签（如 language / python、type / tutorial、status / archived），支持按标签组合进行布尔过滤与聚合统计。

可用性健康检查：内置可配置的定时巡检任务，对索引中的链接发起 HEAD 与 GET 请求，记录响应状态、响应时间与内容哈希变更，标记失效或内容变动节点。

快照元数据存储：存储每个链接的标题、描述片段、最后修改时间以及内容长度，支持内容变更追踪与版本比对，提供历史变化时间线。

RESTful API 查询接口：提供基于 JSON 的查询接口，支持分页、排序、字段投影以及基于正则表达式的域名过滤，便于集成至现有仪表盘或自动化脚本。

静态站点生成模式：支持将整个链接索引导出为静态 HTML 目录树，生成按标签、域名、更新时间组织的导航页面，适用于内网文档站点或 GitHub Pages 部署。

导入导出互操作性：支持导入浏览器书签 HTML 文件、Feedly OPML 订阅列表，并支持导出为 JSON、Markdown 表格以及纯文本列表，满足不同平台的迁移与备份需求。

## 应用场景

个人技术书签库的集中管理：开发者可将分散在浏览器收藏夹、笔记软件和即时通讯记录中的技术文章、工具站点、API 文档链接统一导入 LinkVault，通过自定义标签与搜索快速定位，避免收藏失效或重复存储。

技术团队周报素材自动化收集：内容编辑或技术运营人员可利用 LinkVault 的标签过滤与定期巡检功能，每周自动拉取指定标签下的新增或更新链接，生成 Markdown 格式的周报素材列表，减少手动筛选时间。

第三方依赖文档镜像监控：企业基础架构团队可将外部依赖的官方文档、镜像站地址、发布公告页面纳入 LinkVault 索引，通过可用性检测与内容变更通知及时感知外部资源变动，提前应对访问异常或文档更新。

开源项目 README 外链质量维护：开源项目维护者可利用 LinkVault 导出功能定期校验项目文档中引用的所有外部链接状态，生成失效链接报告，确保项目文档中的引用资源长期有效。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
git clone https://github.com/your-org/linkvault.git
cd linkvault
pip install -r requirements.txt
cp config.example.yml config.yml
python scripts/init_db.py
python app.py --port 8080
```

执行完成后，访问 http://localhost:8080 可查看内置的简易仪表盘，通过 `cli.py` 工具可进行批量导入与巡检操作。详细命令行参数请参考文档导航章节。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，低于 3.9 将无法使用类型注解与异步特性 |
| SQLite | 3.35 及以上 | 默认元数据存储引擎，支持 JSON 函数与窗口函数 |
| Redis | 6.2 及以上 | 可选组件，用于缓存巡检结果与分布式锁，单机模式可禁用 |
| curl | 7.68 及以上 | 健康检查模块依赖外部 curl 进行 TLS 指纹模拟，需安装系统包 |
| git | 2.25 及以上 | 用于版本管理及从远程仓库拉取配置模板 |
| make | 3.81 及以上 | 用于执行自动化任务脚本（迁移、测试、打包） |
| openssl | 1.1.1 及以上 | 用于生成链接指纹哈希与签名校验 |
| tzdata | 最新稳定版 | 时区解析依赖，Linux 环境需安装系统时区数据包 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何导入链接、配置标签、执行巡检以及导出结果 |
| API 参考 | /docs/api-reference/ | 各 REST 端点的请求参数、响应结构、错误码与分页规范 |
| 运维指南 | /docs/operations/ | 如何配置巡检周期、调整缓存策略、备份元数据库及迁移 |
| 贡献者指南 | /docs/contributing/ | 代码风格检查、测试用例编写、提交流程与 PR 模板说明 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/186036.htm
- http://m.3g.gqskj.cn/xnews/40557.htm
- http://m.3g.gqskj.cn/xnews/4626189.htm
- http://m.3g.gqskj.cn/xnews/32190.htm
- http://m.3g.gqskj.cn/xnews/18359.htm
- http://m.3g.gqskj.cn/xnews/6275.htm
- http://m.3g.gqskj.cn/xnews/2743183.htm
- http://m.3g.gqskj.cn/xnews/6093.htm
- http://m.3g.gqskj.cn/xnews/1596.htm
- http://m.3g.gqskj.cn/xnews/725250.htm
- http://m.3g.gqskj.cn/xnews/087970.htm
- http://m.3g.gqskj.cn/xnews/98076.htm
- http://m.3g.gqskj.cn/xnews/430656.htm
- http://m.3g.gqskj.cn/xnews/325267.htm
- http://m.3g.gqskj.cn/xnews/81595.htm
- http://m.3g.gqskj.cn/xnews/17395.htm
- http://m.3g.gqskj.cn/xnews/799807.htm
- http://m.3g.gqskj.cn/xnews/296842.htm
- http://m.3g.gqskj.cn/xnews/371517.htm
- http://m.3g.gqskj.cn/xnews/4581.htm
- http://m.3g.gqskj.cn/xnews/7322926.htm
- http://m.3g.gqskj.cn/xnews/92575.htm
- http://m.3g.gqskj.cn/xnews/2251258.htm
- http://m.3g.gqskj.cn/xnews/29941.htm
- http://m.3g.gqskj.cn/xnews/387470.htm
- http://m.3g.gqskj.cn/xnews/109322.htm
- http://m.3g.gqskj.cn/xnews/450002.htm
- http://m.3g.gqskj.cn/xnews/2945.htm
- http://m.3g.gqskj.cn/xnews/336964.htm
- http://m.3g.gqskj.cn/xnews/84454.htm
- http://m.3g.gqskj.cn/xnews/1008.htm
- http://m.3g.gqskj.cn/xnews/194163.htm
- http://m.3g.gqskj.cn/xnews/4859928.htm
- http://m.3g.gqskj.cn/xnews/154114.htm
- http://m.3g.gqskj.cn/xnews/34581.htm
- http://m.3g.gqskj.cn/xnews/6243448.htm
- http://m.3g.gqskj.cn/xnews/6718.htm
- http://m.3g.gqskj.cn/xnews/2470.htm
- http://m.3g.gqskj.cn/xnews/10233.htm
- http://m.3g.gqskj.cn/xnews/8886.htm
- http://m.3g.gqskj.cn/xnews/08882.htm
- http://m.3g.gqskj.cn/xnews/19046.htm
- http://m.3g.gqskj.cn/xnews/1029072.htm
- http://m.3g.gqskj.cn/xnews/37331.htm
- http://m.3g.gqskj.cn/xnews/7751660.htm
- http://m.3g.gqskj.cn/xnews/04923.htm
- http://m.3g.gqskj.cn/xnews/885325.htm
- http://m.3g.gqskj.cn/xnews/23149.htm
- http://m.3g.gqskj.cn/xnews/3882724.htm
- http://m.3g.gqskj.cn/xnews/243399.htm
- http://m.3g.gqskj.cn/xnews/6419.htm
- http://m.3g.gqskj.cn/xnews/0291211.htm
- http://m.3g.gqskj.cn/xnews/2518096.htm
- http://m.3g.gqskj.cn/xnews/578109.htm
- http://m.3g.gqskj.cn/xnews/802911.htm
- http://m.3g.gqskj.cn/xnews/119275.htm
- http://m.3g.gqskj.cn/xnews/2553.htm
- http://m.3g.gqskj.cn/xnews/1520.htm
- http://m.3g.gqskj.cn/xnews/1462.htm
- http://m.3g.gqskj.cn/xnews/9020.htm
- http://m.3g.gqskj.cn/xnews/40862.htm
- http://m.3g.gqskj.cn/xnews/0988743.htm
- http://m.3g.gqskj.cn/xnews/63305.htm
- http://m.3g.gqskj.cn/xnews/5623851.htm
- http://m.3g.gqskj.cn/xnews/0439.htm
- http://m.3g.gqskj.cn/xnews/6439.htm
- http://m.3g.gqskj.cn/xnews/685604.htm
- http://m.3g.gqskj.cn/xnews/2112.htm
- http://m.3g.gqskj.cn/xnews/470307.htm
- http://m.3g.gqskj.cn/xnews/71835.htm
- http://m.3g.gqskj.cn/xnews/618445.htm
- http://m.3g.gqskj.cn/xnews/43005.htm
- http://m.3g.gqskj.cn/xnews/6891938.htm
- http://m.3g.gqskj.cn/xnews/964901.htm
- http://m.3g.gqskj.cn/xnews/113969.htm
- http://m.3g.gqskj.cn/xnews/108876.htm
- http://m.3g.gqskj.cn/xnews/6685717.htm
- http://m.3g.gqskj.cn/xnews/664995.htm
- http://m.3g.gqskj.cn/xnews/05401.htm
- http://m.3g.gqskj.cn/xnews/2701.htm
- http://m.3g.gqskj.cn/xnews/163011.htm
- http://m.3g.gqskj.cn/xnews/9796.htm
- http://m.3g.gqskj.cn/xnews/8039054.htm
- http://m.3g.gqskj.cn/xnews/7393.htm
- http://m.3g.gqskj.cn/xnews/7418364.htm
- http://m.3g.gqskj.cn/xnews/62975.htm
- http://m.3g.gqskj.cn/xnews/967556.htm
- http://m.3g.gqskj.cn/xnews/69435.htm
- http://m.3g.gqskj.cn/xnews/6191.htm
- http://m.3g.gqskj.cn/xnews/0103.htm
- http://m.3g.gqskj.cn/xnews/9631.htm
- http://m.3g.gqskj.cn/xnews/14860.htm
- http://m.3g.gqskj.cn/xnews/32317.htm
- http://m.3g.gqskj.cn/xnews/83011.htm
- http://m.3g.gqskj.cn/xnews/396784.htm
- http://m.3g.gqskj.cn/xnews/03887.htm
- http://m.3g.gqskj.cn/xnews/258677.htm
- http://m.3g.gqskj.cn/xnews/8458.htm
- http://m.3g.gqskj.cn/xnews/67181.htm
- http://m.3g.gqskj.cn/xnews/376357.htm
- http://m.3g.gqskj.cn/xnews/844356.htm
- http://m.3g.gqskj.cn/xnews/0315.htm
- http://m.3g.gqskj.cn/xnews/17843.htm
- http://m.3g.gqskj.cn/xnews/7937177.htm
- http://m.3g.gqskj.cn/xnews/460207.htm
- http://m.3g.gqskj.cn/xnews/98753.htm
- http://m.3g.gqskj.cn/xnews/92851.htm
- http://m.3g.gqskj.cn/xnews/0626282.htm
- http://m.3g.gqskj.cn/xnews/5980.htm
- http://m.3g.gqskj.cn/xnews/89553.htm
- http://m.3g.gqskj.cn/xnews/86113.htm
- http://m.3g.gqskj.cn/xnews/055226.htm
- http://m.3g.gqskj.cn/xnews/0144.htm
- http://m.3g.gqskj.cn/xnews/9442794.htm
- http://m.3g.gqskj.cn/xnews/101667.htm
- http://m.3g.gqskj.cn/xnews/3195.htm
- http://m.3g.gqskj.cn/xnews/7063605.htm
- http://m.3g.gqskj.cn/xnews/5004.htm
- http://m.3g.gqskj.cn/xnews/859068.htm
- http://m.3g.gqskj.cn/xnews/566229.htm
- http://m.3g.gqskj.cn/xnews/267065.htm
- http://m.3g.gqskj.cn/xnews/6214713.htm
- http://m.3g.gqskj.cn/xnews/26031.htm
- http://m.3g.gqskj.cn/xnews/953890.htm
- http://m.3g.gqskj.cn/xnews/55740.htm
- http://m.3g.gqskj.cn/xnews/472254.htm
- http://m.3g.gqskj.cn/xnews/2792366.htm
- http://m.3g.gqskj.cn/xnews/126681.htm
- http://m.3g.gqskj.cn/xnews/485082.htm
- http://m.3g.gqskj.cn/xnews/611239.htm
- http://m.3g.gqskj.cn/xnews/4071.htm
- http://m.3g.gqskj.cn/xnews/05801.htm
- http://m.3g.gqskj.cn/xnews/7761537.htm
- http://m.3g.gqskj.cn/xnews/017126.htm
- http://m.3g.gqskj.cn/xnews/8319.htm
- http://m.3g.gqskj.cn/xnews/1093343.htm
- http://m.3g.gqskj.cn/xnews/1265.htm
- http://m.3g.gqskj.cn/xnews/9288350.htm
- http://m.3g.gqskj.cn/xnews/063622.htm
- http://m.3g.gqskj.cn/xnews/073427.htm
- http://m.3g.gqskj.cn/xnews/947623.htm
- http://m.3g.gqskj.cn/xnews/860651.htm
- http://m.3g.gqskj.cn/xnews/97471.htm
- http://m.3g.gqskj.cn/xnews/2775.htm
- http://m.3g.gqskj.cn/xnews/7403687.htm
- http://m.3g.gqskj.cn/xnews/66631.htm
- http://m.3g.gqskj.cn/xnews/815319.htm
- http://m.3g.gqskj.cn/xnews/01841.htm
- http://m.3g.gqskj.cn/xnews/5959.htm
- http://m.3g.gqskj.cn/xnews/827812.htm
- http://m.3g.gqskj.cn/xnews/5828.htm
- http://m.3g.gqskj.cn/xnews/876304.htm
- http://m.3g.gqskj.cn/xnews/8351.htm
- http://m.3g.gqskj.cn/xnews/51808.htm
- http://m.3g.gqskj.cn/xnews/2280067.htm
- http://m.3g.gqskj.cn/xnews/121353.htm
- http://m.3g.gqskj.cn/xnews/9332823.htm
- http://m.3g.gqskj.cn/xnews/2499083.htm
- http://m.3g.gqskj.cn/xnews/112801.htm
- http://m.3g.gqskj.cn/xnews/1593.htm
- http://m.3g.gqskj.cn/xnews/106115.htm
- http://m.3g.gqskj.cn/xnews/28567.htm
- http://m.3g.gqskj.cn/xnews/7271.htm
- http://m.3g.gqskj.cn/xnews/289703.htm
- http://m.3g.gqskj.cn/xnews/0819225.htm
- http://m.3g.gqskj.cn/xnews/28377.htm
- http://m.3g.gqskj.cn/xnews/763135.htm
- http://m.3g.gqskj.cn/xnews/3228918.htm
- http://m.3g.gqskj.cn/xnews/52264.htm
- http://m.3g.gqskj.cn/xnews/603232.htm
- http://m.3g.gqskj.cn/xnews/1460743.htm
- http://m.3g.gqskj.cn/xnews/996275.htm
- http://m.3g.gqskj.cn/xnews/7577701.htm
- http://m.3g.gqskj.cn/xnews/9545.htm
- http://m.3g.gqskj.cn/xnews/2961.htm
- http://m.3g.gqskj.cn/xnews/783790.htm
- http://m.3g.gqskj.cn/xnews/485363.htm
- http://m.3g.gqskj.cn/xnews/8361574.htm
- http://m.3g.gqskj.cn/xnews/5600.htm
- http://m.3g.gqskj.cn/xnews/4213585.htm
- http://m.3g.gqskj.cn/xnews/83560.htm
- http://m.3g.gqskj.cn/xnews/56464.htm
- http://m.3g.gqskj.cn/xnews/7224.htm
- http://m.3g.gqskj.cn/xnews/7096644.htm
- http://m.3g.gqskj.cn/xnews/3162.htm
- http://m.3g.gqskj.cn/xnews/8639.htm
- http://m.3g.gqskj.cn/xnews/6243.htm
- http://m.3g.gqskj.cn/xnews/9730002.htm
- http://m.3g.gqskj.cn/xnews/174926.htm
- http://m.3g.gqskj.cn/xnews/40062.htm
- http://m.3g.gqskj.cn/xnews/3509903.htm
- http://m.3g.gqskj.cn/xnews/3314.htm
- http://m.3g.gqskj.cn/xnews/548618.htm
- http://m.3g.gqskj.cn/xnews/6581.htm
- http://m.3g.gqskj.cn/xnews/439394.htm
- http://m.3g.gqskj.cn/xnews/594234.htm
- http://m.3g.gqskj.cn/xnews/6014.htm
- http://m.3g.gqskj.cn/xnews/613683.htm
- http://m.3g.gqskj.cn/xnews/285467.htm
- http://m.3g.gqskj.cn/xnews/00620.htm
- http://m.3g.gqskj.cn/xnews/47979.htm
- http://m.3g.gqskj.cn/xnews/2225.htm
- http://m.3g.gqskj.cn/xnews/07171.htm
- http://m.3g.gqskj.cn/xnews/73724.htm
- http://m.3g.gqskj.cn/xnews/2201.htm
- http://m.3g.gqskj.cn/xnews/574636.htm
- http://m.3g.gqskj.cn/xnews/5371.htm
- http://m.3g.gqskj.cn/xnews/097995.htm
- http://m.3g.gqskj.cn/xnews/6613656.htm
- http://m.3g.gqskj.cn/xnews/3342139.htm
- http://m.3g.gqskj.cn/xnews/205138.htm
- http://m.3g.gqskj.cn/xnews/088132.htm
- http://m.3g.gqskj.cn/xnews/2980.htm
- http://m.3g.gqskj.cn/xnews/650042.htm
- http://m.3g.gqskj.cn/xnews/146155.htm
- http://m.3g.gqskj.cn/xnews/97271.htm
- http://m.3g.gqskj.cn/xnews/8158.htm
- http://m.3g.gqskj.cn/xnews/7652661.htm
- http://m.3g.gqskj.cn/xnews/51205.htm
- http://m.3g.gqskj.cn/xnews/766730.htm
- http://m.3g.gqskj.cn/xnews/3786.htm
- http://m.3g.gqskj.cn/xnews/00339.htm
- http://m.3g.gqskj.cn/xnews/8016855.htm
- http://m.3g.gqskj.cn/xnews/343541.htm
- http://m.3g.gqskj.cn/xnews/470912.htm
- http://m.3g.gqskj.cn/xnews/0123983.htm
- http://m.3g.gqskj.cn/xnews/7067887.htm
- http://m.3g.gqskj.cn/xnews/427971.htm
- http://m.3g.gqskj.cn/xnews/16612.htm
- http://m.3g.gqskj.cn/xnews/2150715.htm
- http://m.3g.gqskj.cn/xnews/993136.htm
- http://m.3g.gqskj.cn/xnews/8938932.htm
- http://m.3g.gqskj.cn/xnews/0793985.htm
- http://m.3g.gqskj.cn/xnews/49652.htm
- http://m.3g.gqskj.cn/xnews/2568776.htm
- http://m.3g.gqskj.cn/xnews/77111.htm
- http://m.3g.gqskj.cn/xnews/5423.htm
- http://m.3g.gqskj.cn/xnews/2852699.htm
- http://m.3g.gqskj.cn/xnews/181933.htm
- http://m.3g.gqskj.cn/xnews/6275083.htm
- http://m.3g.gqskj.cn/xnews/44235.htm
- http://m.3g.gqskj.cn/xnews/0780.htm
- http://m.3g.gqskj.cn/xnews/2594869.htm
- http://m.3g.gqskj.cn/xnews/221024.htm
- http://m.3g.gqskj.cn/xnews/0482683.htm
- http://m.3g.gqskj.cn/xnews/12738.htm
- http://m.3g.gqskj.cn/xnews/021604.htm
- http://m.3g.gqskj.cn/xnews/5478.htm
- http://m.3g.gqskj.cn/xnews/887338.htm
- http://m.3g.gqskj.cn/xnews/091697.htm

## 项目结构

```
linkvault/
├── app/                                # 核心应用包
│   ├── api/                            # RESTful 路由与控制器
│   │   ├── v1/                         # API 版本 v1 端点实现
│   │   │   ├── links.py                # 链接增删改查及批量导入接口
│   │   │   ├── checks.py               # 健康检查触发与历史查询接口
│   │   │   └── tags.py                 # 标签管理与聚合统计接口
│   │   └── middleware/                 # 鉴权、限流、日志中间件
│   ├── core/                           # 核心业务逻辑层
│   │   ├── indexer.py                  # 链接解析、标准化与指纹计算
│   │   ├── dedup.py                    # 去重算法与相似度比对
│   │   └── snapshot.py                 # 元数据快照生成与差异比对
│   ├── scheduler/                      # 定时任务调度模块
│   │   ├── scanner.py                  # 巡检任务队列管理与分发
│   │   ├── worker.py                   # 实际执行 HTTP 请求的工作进程
│   │   └── notifier.py                 # 状态变更通知（邮件/Webhook）
│   ├── storage/                        # 存储抽象层
│   │   ├── sqlite.py                   # SQLite 适配器（默认实现）
│   │   ├── redis.py                    # Redis 缓存与分布式锁适配器
│   │   └── models.py                   # 数据表 ORM 映射与迁移脚本
│   └── exporter/                       # 导出与静态生成模块
│       ├── static.py                   # 静态 HTML 站点生成器
│       ├── markdown.py                 # Markdown 表格与列表导出
│       └── jsonlines.py                # JSON Lines 流式导出
├── scripts/                            # 运维与开发辅助脚本
│   ├── init_db.py                      # 初始化数据库表结构与默认标签
│   ├── import_bookmarks.py             # 导入浏览器书签 HTML 文件
│   └── export_snapshot.py              # 导出全量快照至外部存储
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 单模块单元测试
│   └── integration/                    # API 与调度流程集成测试
├── config.example.yml                  # 配置文件模板（含巡检周期、缓存设置）
├── requirements.txt                    # Python 依赖清单
├── Makefile                            # 自动化构建与测试命令集
└── README.md                           # 本文件
```

## 贡献指南

提交 Issue 描述缺陷或改进建议：使用 GitHub Issue 模板，明确标注操作系统版本、Python 版本、错误日志或期望行为，缺陷报告需提供可复现的最小输入示例。

创建功能分支并遵循代码风格：从 `main` 分支切出 `feature/xxx` 或 `fix/xxx` 分支，提交前运行 `make lint` 检查 PEP 8 规范，所有公开函数需包含 docstring 与类型注解。

编写或更新单元测试：新增功能或修复缺陷需同步添加测试用例至 `tests/` 对应目录，确保 `make test` 覆盖率不低于 85%。

提交 Pull Request 并关联 Issue：PR 标题采用 `<type>(<scope>): <summary>` 格式，内容需描述改动动机、实现方案及兼容性影响，并关联相关 Issue 编号。

更新文档与示例：涉及配置项变更或 API 变动时，同步更新 `docs/` 下对应文档及 `config.example.yml`，确保新用户可无障碍上手。

## 常见问题

系统启动时报错 `sqlite3.OperationalError: no such function: json_extract` 如何解决？

该错误表明当前 SQLite 版本未编译 JSON1 扩展。请升级 SQLite 至 3.35 以上版本，或重新编译 SQLite 启用 `-DSQLITE_ENABLE_JSON1` 选项。若无法升级，可在 `config.yml` 中设置 `storage.sqlite.disable_json: true` 回退至纯文本标签存储模式，但会损失部分查询性能与聚合功能。

巡检任务始终返回超时，如何调整超时阈值与重试策略？

巡检超时由 `config.yml` 中 `scanner.timeout_seconds` 与 `scanner.retry.max_attempts` 控制。默认超时为 10 秒，重试 2 次。若目标站点响应较慢，可适当调高超时值至 30 秒，并增加重试次数至 3。对于大批量巡检，建议配合 Redis 队列将并发度 `scanner.concurrency` 调整为 5 以下，避免源站触发访问限流。

如何将现有浏览器书签一次性导入 LinkVault？

使用 `scripts/import_bookmarks.py` 脚本，支持 Chrome 导出的 HTML 书签文件、Firefox 的 JSON 备份以及 Edge 的收藏夹文件。执行 `python scripts/import_bookmarks.py --input bookmarks.html --tag browser-import` 即可将链接入库并统一打上 `browser-import` 标签。导入后可通过 API 或仪表盘进行标签补充与去重清理。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:46
