# LinkSentry 聚合导航系统

LinkSentry 是一个面向技术团队与内容研究者的轻量级外链聚合与健康监控平台。该项目不对原始链接做任何内容改写或摘要提取，仅提供结构化索引、访问可达性探测与基础元数据归档能力，适用于需要批量管理、定期验证或迁移大量外部引用链接的场景。目标用户包括文档维护者、运维工程师、SEO 分析师以及依赖外部资料站的知识库管理员。

## 功能概览

**批量链接导入与持久化存储**：支持通过文本文件或标准输入一次性导入数千条 URL，所有记录以原始形态存入 SQLite 本地数据库，保留协议、大小写及路径参数。

**定时可达性探测**：基于可配置的 cron 表达式，对每条链接发起 HEAD 请求，记录响应状态码、响应时间与重定向链，超时阈值与重试次数可调。

**状态变更通知**：当链接从可达变为不可达，或状态码发生非预期变化时，可通过 Webhook 或邮件发送差异报告，便于及时清理或更新失效引用。

**标签与分组管理**：允许用户为每条链接附加多个自定义标签（如 "官方文档"、"API 参考"、"博客转载"），并基于标签组合进行快速过滤与统计。

**全文检索与高级筛选**：针对 URL 本身以及用户备注字段提供前缀匹配、后缀匹配与正则表达式检索，支持按协议类型、状态码范围、最后检测时间区间进行组合筛选。

**数据导入导出**：提供 CSV 与 JSON 格式的批量导出功能，导出字段包含原始 URL、首次导入时间、最近检测状态、备注标签等元信息，便于迁移至其他系统。

**访问日志审计**：记录每次检测任务的详细执行日志，包括每个 URL 的检测耗时、异常堆栈与网络环境快照，便于排查网络策略或防火墙导致的误判。

## 应用场景

**文档站点外链巡检**：技术博客或开源项目文档中常包含大量外部参考链接。每周自动运行一次 LinkSentry 扫描，生成失效链接清单，维护者可据此快速修复或替换已迁移的文档引用。

**合规审查与链接备案**：金融或政务类知识库需要定期审计所有外部跳转目标。LinkSentry 提供完整的链接清单与访问记录导出功能，配合标签体系可标记 "已审核" 或 "需人工复核" 状态，满足内控要求。

**资源迁移前影响评估**：当某外部域名计划停用或更换 CDN 服务商时，运维团队可利用 LinkSentry 的标签筛选功能，快速找出所有指向该域名的链接，评估变更影响范围并提前通知相关方。

**数据管道健康监控**：在 ETL 流程中，若上游数据源依赖外部静态资源地址，可将这些地址录入 LinkSentry 并设置高频探测（如每 5 分钟一次）。一旦资源不可用，立即触发告警，避免下游任务大面积失败。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆仓库
git clone https://github.com/linksentry/linksentry.git
cd linksentry

# 安装依赖（使用 Python 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化数据库与配置
cp config.example.yaml config.yaml
python scripts/init_db.py

# 启动 Web 控制台（默认监听 127.0.0.1:8080）
python app.py

# 或者直接运行一次探测任务（使用示例链接文件）
python scripts/run_probe.py --input sample_links.txt --output report.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时，需支持 asyncio 与 httpx |
| SQLite | 3.35 及以上 | 内置数据库，用于存储链接记录与检测历史 |
| httpx | 0.27.0 及以上 | 异步 HTTP 客户端，负责所有探测请求 |
| pyyaml | 6.0 及以上 | 解析 config.yaml 配置文件 |
| apscheduler | 3.10.0 及以上 | 定时任务调度器，支持 cron 表达式 |
| jinja2 | 3.1.0 及以上 | 渲染邮件通知模板与简易 Web 界面 |
| pytest | 7.0.0 及以上 | 仅开发测试环境需要，生产环境可不安装 |
| docker | 20.10 及以上 | 若使用容器化部署方式，需安装 Docker Engine |
| redis | 6.2 及以上 | 可选，用于分布式部署时的任务队列锁 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何 5 分钟内完成首次安装并导入第一批链接？ |
| 配置参考 | docs/configuration.md | config.yaml 中每个字段的含义、默认值与可选项是什么？ |
| 探测引擎 | docs/probe_engine.md | 探测超时、重试策略、重定向处理与状态码判断逻辑如何调整？ |
| 通知集成 | docs/notifications.md | 支持哪些通知渠道？如何自定义 Webhook 请求体格式？ |
| 标签体系 | docs/tagging.md | 如何批量添加、删除或合并标签？标签筛选语法规则是什么？ |
| API 手册 | docs/api_reference.md | 所有 RESTful 接口的请求参数、响应结构与错误码说明 |
| 运维指南 | docs/operations.md | 如何备份数据库、轮转日志、升级版本与迁移数据？ |
| 故障排查 | docs/troubleshooting.md | 常见启动失败、探测超时、数据库锁异常问题的解决步骤 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/3495.htm
- http://m.blog.gqskj.cn/nnews/0375.htm
- http://m.blog.gqskj.cn/nnews/5581606.htm
- http://m.blog.gqskj.cn/nnews/0036.htm
- http://m.blog.gqskj.cn/nnews/790428.htm
- http://m.blog.gqskj.cn/nnews/1528386.htm
- http://m.blog.gqskj.cn/nnews/9424326.htm
- http://m.blog.gqskj.cn/nnews/9399.htm
- http://m.blog.gqskj.cn/nnews/9274673.htm
- http://m.blog.gqskj.cn/nnews/43246.htm
- http://m.blog.gqskj.cn/nnews/28249.htm
- http://m.blog.gqskj.cn/nnews/105183.htm
- http://m.blog.gqskj.cn/nnews/5735227.htm
- http://m.blog.gqskj.cn/nnews/6516056.htm
- http://m.blog.gqskj.cn/nnews/706103.htm
- http://m.blog.gqskj.cn/nnews/6939373.htm
- http://m.blog.gqskj.cn/nnews/52487.htm
- http://m.blog.gqskj.cn/nnews/379606.htm
- http://m.blog.gqskj.cn/nnews/82731.htm
- http://m.blog.gqskj.cn/nnews/05218.htm
- http://m.blog.gqskj.cn/nnews/7304.htm
- http://m.blog.gqskj.cn/nnews/7851950.htm
- http://m.blog.gqskj.cn/nnews/9917121.htm
- http://m.blog.gqskj.cn/nnews/0900.htm
- http://m.blog.gqskj.cn/nnews/023618.htm
- http://m.blog.gqskj.cn/nnews/8600900.htm
- http://m.blog.gqskj.cn/nnews/86305.htm
- http://m.blog.gqskj.cn/nnews/89600.htm
- http://m.blog.gqskj.cn/nnews/2149.htm
- http://m.blog.gqskj.cn/nnews/402974.htm
- http://m.blog.gqskj.cn/nnews/627333.htm
- http://m.blog.gqskj.cn/nnews/9226335.htm
- http://m.blog.gqskj.cn/nnews/244915.htm
- http://m.blog.gqskj.cn/nnews/127172.htm
- http://m.blog.gqskj.cn/nnews/95548.htm
- http://m.blog.gqskj.cn/nnews/278215.htm
- http://m.blog.gqskj.cn/nnews/6812016.htm
- http://m.blog.gqskj.cn/nnews/06663.htm
- http://m.blog.gqskj.cn/nnews/4517.htm
- http://m.blog.gqskj.cn/nnews/6364.htm
- http://m.blog.gqskj.cn/nnews/9827.htm
- http://m.blog.gqskj.cn/nnews/20695.htm
- http://m.blog.gqskj.cn/nnews/791925.htm
- http://m.blog.gqskj.cn/nnews/618140.htm
- http://m.blog.gqskj.cn/nnews/9504522.htm
- http://m.blog.gqskj.cn/nnews/0315832.htm
- http://m.blog.gqskj.cn/nnews/0673878.htm
- http://m.blog.gqskj.cn/nnews/3070359.htm
- http://m.blog.gqskj.cn/nnews/29794.htm
- http://m.blog.gqskj.cn/nnews/6523837.htm
- http://m.blog.gqskj.cn/nnews/90721.htm
- http://m.blog.gqskj.cn/nnews/9469579.htm
- http://m.blog.gqskj.cn/nnews/5226650.htm
- http://m.blog.gqskj.cn/nnews/7139.htm
- http://m.blog.gqskj.cn/nnews/8533462.htm
- http://m.blog.gqskj.cn/nnews/61135.htm
- http://m.blog.gqskj.cn/nnews/808003.htm
- http://m.blog.gqskj.cn/nnews/699355.htm
- http://m.blog.gqskj.cn/nnews/614007.htm
- http://m.blog.gqskj.cn/nnews/152942.htm
- http://m.blog.gqskj.cn/nnews/6594.htm
- http://m.blog.gqskj.cn/nnews/953536.htm
- http://m.blog.gqskj.cn/nnews/9262167.htm
- http://m.blog.gqskj.cn/nnews/1288860.htm
- http://m.blog.gqskj.cn/nnews/821406.htm
- http://m.blog.gqskj.cn/nnews/80847.htm
- http://m.blog.gqskj.cn/nnews/54355.htm
- http://m.blog.gqskj.cn/nnews/9790382.htm
- http://m.blog.gqskj.cn/nnews/4580.htm
- http://m.blog.gqskj.cn/nnews/53505.htm
- http://m.blog.gqskj.cn/nnews/9313.htm
- http://m.blog.gqskj.cn/nnews/781532.htm
- http://m.blog.gqskj.cn/nnews/9181.htm
- http://m.blog.gqskj.cn/nnews/2022.htm
- http://m.blog.gqskj.cn/nnews/7672.htm
- http://m.blog.gqskj.cn/nnews/43563.htm
- http://m.blog.gqskj.cn/nnews/84570.htm
- http://m.blog.gqskj.cn/nnews/8718182.htm
- http://m.blog.gqskj.cn/nnews/14258.htm
- http://m.blog.gqskj.cn/nnews/5284752.htm
- http://m.blog.gqskj.cn/nnews/160715.htm
- http://m.blog.gqskj.cn/nnews/7712778.htm
- http://m.blog.gqskj.cn/nnews/2711.htm
- http://m.blog.gqskj.cn/nnews/16818.htm
- http://m.blog.gqskj.cn/nnews/0733.htm
- http://m.blog.gqskj.cn/nnews/645185.htm
- http://m.blog.gqskj.cn/nnews/358958.htm
- http://m.blog.gqskj.cn/nnews/8559.htm
- http://m.blog.gqskj.cn/nnews/8778427.htm
- http://m.blog.gqskj.cn/nnews/1253.htm
- http://m.blog.gqskj.cn/nnews/264611.htm
- http://m.blog.gqskj.cn/nnews/11899.htm
- http://m.blog.gqskj.cn/nnews/20019.htm
- http://m.blog.gqskj.cn/nnews/25034.htm
- http://m.blog.gqskj.cn/nnews/3172983.htm
- http://m.blog.gqskj.cn/nnews/2910327.htm
- http://m.blog.gqskj.cn/nnews/720124.htm
- http://m.blog.gqskj.cn/nnews/966685.htm
- http://m.blog.gqskj.cn/nnews/1629.htm
- http://m.blog.gqskj.cn/nnews/78916.htm
- http://m.blog.gqskj.cn/nnews/98379.htm
- http://m.blog.gqskj.cn/nnews/8862.htm
- http://m.blog.gqskj.cn/nnews/7392.htm
- http://m.blog.gqskj.cn/nnews/4206939.htm
- http://m.blog.gqskj.cn/nnews/3383137.htm
- http://m.blog.gqskj.cn/nnews/992399.htm
- http://m.blog.gqskj.cn/nnews/351482.htm
- http://m.blog.gqskj.cn/nnews/9655.htm
- http://m.blog.gqskj.cn/nnews/5410120.htm
- http://m.blog.gqskj.cn/nnews/57890.htm
- http://m.blog.gqskj.cn/nnews/67756.htm
- http://m.blog.gqskj.cn/nnews/224562.htm
- http://m.blog.gqskj.cn/nnews/503080.htm
- http://m.blog.gqskj.cn/nnews/345813.htm
- http://m.blog.gqskj.cn/nnews/29773.htm
- http://m.blog.gqskj.cn/nnews/0138.htm
- http://m.blog.gqskj.cn/nnews/4598727.htm
- http://m.blog.gqskj.cn/nnews/7971953.htm
- http://m.blog.gqskj.cn/nnews/7609.htm
- http://m.blog.gqskj.cn/nnews/026857.htm
- http://m.blog.gqskj.cn/nnews/365918.htm
- http://m.blog.gqskj.cn/nnews/667345.htm
- http://m.blog.gqskj.cn/nnews/84501.htm
- http://m.blog.gqskj.cn/nnews/83486.htm
- http://m.blog.gqskj.cn/nnews/6878442.htm
- http://m.blog.gqskj.cn/nnews/202337.htm
- http://m.blog.gqskj.cn/nnews/15503.htm
- http://m.blog.gqskj.cn/nnews/1966.htm
- http://m.blog.gqskj.cn/nnews/7946.htm
- http://m.blog.gqskj.cn/nnews/317712.htm
- http://m.blog.gqskj.cn/nnews/4944729.htm
- http://m.blog.gqskj.cn/nnews/4915637.htm
- http://m.blog.gqskj.cn/nnews/7480786.htm
- http://m.blog.gqskj.cn/nnews/511095.htm
- http://m.blog.gqskj.cn/nnews/8450509.htm
- http://m.blog.gqskj.cn/nnews/0152.htm
- http://m.blog.gqskj.cn/nnews/0890.htm
- http://m.blog.gqskj.cn/nnews/2372045.htm
- http://m.blog.gqskj.cn/nnews/752087.htm
- http://m.blog.gqskj.cn/nnews/25138.htm
- http://m.blog.gqskj.cn/nnews/877407.htm
- http://m.blog.gqskj.cn/nnews/42790.htm
- http://m.blog.gqskj.cn/nnews/740706.htm
- http://m.blog.gqskj.cn/nnews/3043.htm
- http://m.blog.gqskj.cn/nnews/057328.htm
- http://m.blog.gqskj.cn/nnews/7333024.htm
- http://m.blog.gqskj.cn/nnews/786590.htm
- http://m.blog.gqskj.cn/nnews/4190.htm
- http://m.blog.gqskj.cn/nnews/6934164.htm
- http://m.blog.gqskj.cn/nnews/8499.htm
- http://m.blog.gqskj.cn/nnews/33627.htm
- http://m.blog.gqskj.cn/nnews/45472.htm
- http://m.blog.gqskj.cn/nnews/01607.htm
- http://m.blog.gqskj.cn/nnews/27653.htm
- http://m.blog.gqskj.cn/nnews/32667.htm
- http://m.blog.gqskj.cn/nnews/7952.htm
- http://m.blog.gqskj.cn/nnews/6030.htm
- http://m.blog.gqskj.cn/nnews/5851682.htm
- http://m.blog.gqskj.cn/nnews/42774.htm
- http://m.blog.gqskj.cn/nnews/45675.htm
- http://m.blog.gqskj.cn/nnews/8157281.htm
- http://m.blog.gqskj.cn/nnews/00767.htm
- http://m.blog.gqskj.cn/nnews/139169.htm
- http://m.blog.gqskj.cn/nnews/717794.htm
- http://m.blog.gqskj.cn/nnews/75820.htm
- http://m.blog.gqskj.cn/nnews/0330.htm
- http://m.blog.gqskj.cn/nnews/405066.htm
- http://m.blog.gqskj.cn/nnews/4969938.htm
- http://m.blog.gqskj.cn/nnews/3298126.htm
- http://m.blog.gqskj.cn/nnews/560112.htm
- http://m.blog.gqskj.cn/nnews/2662126.htm
- http://m.blog.gqskj.cn/nnews/18528.htm
- http://m.blog.gqskj.cn/nnews/47598.htm
- http://m.blog.gqskj.cn/nnews/884415.htm
- http://m.blog.gqskj.cn/nnews/92666.htm
- http://m.blog.gqskj.cn/nnews/8123587.htm
- http://m.blog.gqskj.cn/nnews/2706.htm
- http://m.blog.gqskj.cn/nnews/6912599.htm
- http://m.blog.gqskj.cn/nnews/10206.htm
- http://m.blog.gqskj.cn/nnews/81363.htm
- http://m.blog.gqskj.cn/nnews/7474.htm
- http://m.blog.gqskj.cn/nnews/7276.htm
- http://m.blog.gqskj.cn/nnews/2477377.htm
- http://m.blog.gqskj.cn/nnews/605930.htm
- http://m.blog.gqskj.cn/nnews/1475.htm
- http://m.blog.gqskj.cn/nnews/851256.htm
- http://m.blog.gqskj.cn/nnews/542251.htm
- http://m.blog.gqskj.cn/nnews/5773.htm
- http://m.blog.gqskj.cn/nnews/4505.htm
- http://m.blog.gqskj.cn/nnews/8250.htm
- http://m.blog.gqskj.cn/nnews/275016.htm
- http://m.blog.gqskj.cn/nnews/3488028.htm
- http://m.blog.gqskj.cn/nnews/3554.htm
- http://m.blog.gqskj.cn/nnews/2184.htm
- http://m.blog.gqskj.cn/nnews/1099.htm
- http://m.blog.gqskj.cn/nnews/03438.htm
- http://m.blog.gqskj.cn/nnews/977548.htm
- http://m.blog.gqskj.cn/nnews/51483.htm
- http://m.blog.gqskj.cn/nnews/77026.htm
- http://m.blog.gqskj.cn/nnews/465166.htm
- http://m.blog.gqskj.cn/nnews/6215288.htm
- http://m.blog.gqskj.cn/nnews/047601.htm
- http://m.blog.gqskj.cn/nnews/387565.htm
- http://m.blog.gqskj.cn/nnews/532464.htm
- http://m.blog.gqskj.cn/nnews/303722.htm
- http://m.blog.gqskj.cn/nnews/1041.htm
- http://m.blog.gqskj.cn/nnews/278293.htm
- http://m.blog.gqskj.cn/nnews/20405.htm
- http://m.blog.gqskj.cn/nnews/29843.htm
- http://m.blog.gqskj.cn/nnews/5191.htm
- http://m.blog.gqskj.cn/nnews/428111.htm
- http://m.blog.gqskj.cn/nnews/1826.htm
- http://m.blog.gqskj.cn/nnews/9065.htm
- http://m.blog.gqskj.cn/nnews/0266264.htm
- http://m.blog.gqskj.cn/nnews/690597.htm
- http://m.blog.gqskj.cn/nnews/7522361.htm
- http://m.blog.gqskj.cn/nnews/132633.htm
- http://m.blog.gqskj.cn/nnews/431432.htm
- http://m.blog.gqskj.cn/nnews/34756.htm
- http://m.blog.gqskj.cn/nnews/6936128.htm
- http://m.blog.gqskj.cn/nnews/419330.htm
- http://m.blog.gqskj.cn/nnews/43762.htm
- http://m.blog.gqskj.cn/nnews/09700.htm
- http://m.blog.gqskj.cn/nnews/31589.htm
- http://m.blog.gqskj.cn/nnews/972964.htm
- http://m.blog.gqskj.cn/nnews/16023.htm
- http://m.blog.gqskj.cn/nnews/2418564.htm
- http://m.blog.gqskj.cn/nnews/45023.htm
- http://m.blog.gqskj.cn/nnews/7602.htm
- http://m.blog.gqskj.cn/nnews/390853.htm
- http://m.blog.gqskj.cn/nnews/455814.htm
- http://m.blog.gqskj.cn/nnews/6555.htm
- http://m.blog.gqskj.cn/nnews/10815.htm
- http://m.blog.gqskj.cn/nnews/99707.htm
- http://m.blog.gqskj.cn/nnews/902878.htm
- http://m.blog.gqskj.cn/nnews/52857.htm
- http://m.blog.gqskj.cn/nnews/8625702.htm
- http://m.blog.gqskj.cn/nnews/8495.htm
- http://m.blog.gqskj.cn/nnews/979549.htm
- http://m.blog.gqskj.cn/nnews/1256031.htm
- http://m.blog.gqskj.cn/nnews/6631.htm
- http://m.blog.gqskj.cn/nnews/85787.htm
- http://m.blog.gqskj.cn/nnews/30625.htm
- http://m.blog.gqskj.cn/nnews/540746.htm
- http://m.blog.gqskj.cn/nnews/146386.htm
- http://m.blog.gqskj.cn/nnews/13726.htm
- http://m.blog.gqskj.cn/nnews/4596.htm
- http://m.blog.gqskj.cn/nnews/2912170.htm
- http://m.blog.gqskj.cn/nnews/4872274.htm
- http://m.blog.gqskj.cn/nnews/6760.htm

## 项目结构

```
linksentry/
├── app.py                         # Web 控制台入口，注册路由与中间件
├── config.yaml                    # 主配置文件，含数据库路径、探测参数、通知渠道
├── requirements.txt               # Python 依赖列表，锁定主要版本号
├── docker-compose.yml             # 容器编排文件，包含 app + redis + optional prometheus
├── Dockerfile                     # 多阶段构建文件，基于 python:3.11-slim
├── docs/                          # 完整文档目录
│   ├── quickstart.md              # 5分钟快速上手指南
│   ├── configuration.md           # 所有配置项详解与示例
│   ├── probe_engine.md            # 探测引擎设计原理与调优参数
│   ├── notifications.md           # 通知集成（邮件、飞书、自定义 webhook）
│   ├── tagging.md                 # 标签管理 CLI 与 API 用法
│   ├── api_reference.md           # REST API 完整参考手册
│   └── operations.md              # 生产环境运维 checklist
├── src/                           # 核心源代码目录
│   ├── core/                      # 基础组件
│   │   ├── database.py            # SQLite 连接池与 ORM 映射类
│   │   ├── config_loader.py       # YAML 配置解析与校验
│   │   └── logger.py              # 结构化日志（JSON 格式，支持 ELK 集成）
│   ├── probe/                     # 探测引擎模块
│   │   ├── http_client.py         # 异步 HTTP 客户端封装，含超时与重试逻辑
│   │   ├── scheduler.py           # 基于 apscheduler 的任务调度器
│   │   ├── worker.py              # 单次探测任务执行单元
│   │   └── result_handler.py      # 探测结果持久化与状态变更判定
│   ├── web/                       # Web 控制台相关
│   │   ├── routes/                # Blueprint 路由分组
│   │   │   ├── links.py           # 链接增删改查接口
│   │   │   ├── tags.py            # 标签管理接口
│   │   │   └── reports.py         # 报告导出与历史查询接口
│   │   ├── templates/             # Jinja2 模板文件
│   │   └── static/                # 基础 CSS 与 JavaScript 前端资源
│   ├── notifier/                  # 通知发送模块
│   │   ├── email.py               # SMTP 邮件发送器
│   │   ├── webhook.py             # 通用 Webhook 发送器（支持自定义 header）
│   │   └── template_renderer.py   # 通知内容模板渲染
│   └── cli/                       # 命令行工具集
│       ├── import_cmd.py          # 批量导入链接子命令
│       ├── export_cmd.py          # 导出 CSV/JSON 子命令
│       └── probe_cmd.py           # 手动触发探测子命令
├── scripts/                       # 运维与辅助脚本
│   ├── init_db.py                 # 初始化数据库表结构与索引
│   ├── sample_links.txt           # 示例链接文件，供快速测试使用
│   └── migration/                 # 数据库迁移脚本（版本递增）
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 针对各模块的独立测试用例
│   └── integration/               # 端到端探测流程与 Web API 测试
├── .github/                       # GitHub Actions 工作流定义
│   └── workflows/
│       ├── ci.yml                 # 提交时运行 pytest 与代码风格检查
│       └── release.yml            # 打 tag 时自动构建 Docker 镜像并推送
└── .gitignore                     # 忽略 venv、.pyc、.env、日志文件等
```

## 贡献指南

1. 阅读项目行为准则（CODE_OF_CONDUCT.md）与安全政策（SECURITY.md），确认自身遵守开源社区协作规范。所有贡献者需签署开发者原创声明（DCO），提交 PR 时附带 Signed-off-by 签名。

2. 从 issue 列表中选择标记为 "good first issue" 或 "help wanted" 的任务，或在讨论区发起新提案。重大功能变更建议先创建设计文档（docs/design/）并与维护者沟通，避免无效开发。

3. 克隆仓库并创建特性分支（feature/xxx 或 fix/xxx），确保本地开发环境已安装所有开发依赖（参考 requirements-dev.txt）。编写代码时需遵循 PEP 8 规范，并使用 black + isort 自动格式化。

4. 为新增功能或修复编写对应的单元测试，确保测试覆盖率达到 80% 以上。所有测试用例须在本地通过 pytest 验证，且不得破坏现有 API 的向后兼容性。

5. 提交 PR 时填写完整模板，包括变更动机、实现方案、测试结果与文档更新情况。PR 需要至少两位维护者审核通过后合并，合并后自动触发 CI 构建与 Docker 镜像发布。

## 常见问题

**问：探测任务是否会对目标服务器造成压力？**

系统默认采用单线程异步并发，并发数可通过 config.yaml 中的 max_concurrent 参数控制（默认 10）。HEAD 请求不会下载响应体，且超时默认设置为 10 秒，对大多数标准 Web 服务器的影响可忽略。若需探测高频访问的内部服务，建议调整探测间隔至 5 分钟以上，并启用 rate_limit 选项（每秒最大请求数）。

**问：数据库记录增长过快如何处理？**

SQLite 数据库体积主要受检测历史记录影响。系统内置自动清理策略：默认保留最近 90 天的检测历史，超出部分在每次调度任务执行前异步归档或删除。用户也可通过 CLI 命令 `python scripts/cleanup.py --keep-days 30` 手动收紧保留周期。若链接总数超过 10 万条，建议迁移至 PostgreSQL 生产环境。

**问：如何验证导入的链接是否被正确记录？**

Web 控制台提供实时查询功能，访问 `/links` 页面可查看所有记录的分页列表，支持按导入时间、状态、标签过滤。也可使用 CLI 导出功能：`python scripts/export_cmd.py --format json --output verify.json`，然后检查 JSON 文件中是否包含预期数量的原始 URL 字段。系统不会对 URL 进行任何规范化或编码转换，导入时原样存储，因此可通过字符级别对比确认完整性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:32
