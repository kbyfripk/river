# WapLink Aggregate Service

WapLink Aggregate Service 是一个面向移动端资讯聚合与短链解析的开源基础设施项目，专注于对以 `m.wap.gqskj.cn` 为代表的移动站点内容进行结构化采集、归一化处理和批量外链管理。项目定位为技术资源与外部链接汇总中间件，适用于需要批量维护短链资源、定期同步移动端内容快照、或对特定域名下大量离散 URL 进行健康度巡检与元数据提取的开发团队与运维人员。

项目本身不提供最终用户界面，而是以可嵌入的 Go 模块与命令行工具形式交付，支持通过配置文件定义抓取规则、输出格式与存储后端。目标用户包括从事内容聚合平台研发的工程师、负责大规模外链治理的 SRE 团队，以及需要将移动端短链资源转化为结构化数据集的数据分析人员。

## 功能概览

**批量 URL 导入与标准化**
支持从纯文本文件、CSV 或 JSON 清单中批量导入原始 URL，自动去除重复项、校验协议格式，并生成内部唯一资源标识符。

**可配置的并发抓取引擎**
基于工作池模型实现可调节并发度的 HTTP 请求调度，支持分别设置单域名最大连接数、全局请求超时和重试策略，避免对目标源站造成压力。

**响应内容摘要提取**
对每个抓取到的 HTML 页面自动提取标题、meta 描述、正文首段文本以及全部外链，输出为结构化 JSON 字段，便于后续索引或分析。

**资源状态巡检与告警**
周期性执行可用性检查，记录 HTTP 状态码、响应时间与内容哈希变化，当连续失败次数超过阈值时触发本地日志告警或向外部 Webhook 发送通知。

**多格式数据导出**
内置 JSON Lines、NDJSON 和 CSV 三种导出格式，支持按时间范围过滤，方便对接大数据流水线或导入 Elasticsearch、ClickHouse 等分析引擎。

**增量同步与断点续传**
维护本地轻量级 SQLite 元数据表，记录每次抓取的任务指纹与完成状态，支持中断后从上次进度继续执行，避免全量重复处理。

**可插拔的存储后端**
通过接口抽象支持文件系统、SQLite 和内存三种存储方式，用户可根据数据规模选择合适后端，亦可自行扩展实现 Redis 或 S3 兼容对象存储适配器。

## 应用场景

**移动端内容镜像库构建**
内容聚合平台需要长期保存特定域名下的历史页面快照，以供离线分析或合规审计。WapLink Aggregate Service 可配置为每日定时任务，自动抓取指定 URL 列表，将标题、发布时间和正文特征写入本地数据库，形成可持续积累的内容资产。

**外链健康度监控**
运营团队维护的落地页链接可能因源站调整而失效。项目巡检功能可对数百个短链资源执行周期性 HEAD 请求，生成可用性报表，帮助运维人员快速定位异常 URL，并在连续故障时发送企业微信或钉钉机器人告警。

**数据结构化清洗**
数据分析师需要从大量杂乱 HTML 中提取结构化字段。本项目提供可编程的提取规则，支持基于 CSS 选择器或 XPath 的正则抽取，将非结构化页面转换为干净 JSON，可直接用于下游分析或模型训练。

**归档迁移前的资源盘点**
在域名切换或 CDN 配置变更前，需对现有外链进行全面摸底。项目批量导出功能可一键生成包含 URL、最终跳转目标、状态码和内容类型的完整清单，为迁移决策提供数据支撑。

## 快速开始

```bash
# 克隆代码仓库
git clone https://github.com/waplink/aggregate-service.git
cd aggregate-service

# 安装依赖（使用 Go Modules）
go mod download

# 使用示例配置运行批量抓取任务
go run cmd/waplink/main.go -config configs/example.yaml -input urls.txt -output result.jsonl
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Go 编译器 | 1.21 或更高 | 项目使用泛型及标准库 slog，需较新版本支持 |
| SQLite3 | 3.35 以上 | 仅在使用 SQLite 存储后端时需要，提供嵌入式元数据管理 |
| GNU Make | 3.81 或更高 | 用于执行构建脚本与测试套件，非 Windows 环境默认自带 |
| Git | 2.25 以上 | 克隆仓库及管理子模块，Windows 用户需单独安装 |
| 可用磁盘空间 | 至少 500 MB | 用于存储日志、元数据及抓取内容缓存，实际需求视数据量而定 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/ | 如何编写配置文件、定义输入格式、选择输出类型和运行任务 |
| 开发指南 | docs/development/ | 项目模块划分、接口设计原则、新增存储后端或提取器的实现步骤 |
| 运维参考 | docs/operations/ | 生产环境部署建议、监控指标说明、日志级别调优与故障排查流程 |
| API 规范 | docs/api/ | 内部 Go 包公开函数的调用约定、配置结构体字段释义及示例代码 |

## 资源列表

- http://m.wap.gqskj.cn/snews/176808.htm
- http://m.wap.gqskj.cn/snews/154411.htm
- http://m.wap.gqskj.cn/snews/3792.htm
- http://m.wap.gqskj.cn/snews/5565597.htm
- http://m.wap.gqskj.cn/snews/5804451.htm
- http://m.wap.gqskj.cn/snews/9734.htm
- http://m.wap.gqskj.cn/snews/10772.htm
- http://m.wap.gqskj.cn/snews/3389762.htm
- http://m.wap.gqskj.cn/snews/9053968.htm
- http://m.wap.gqskj.cn/snews/19593.htm
- http://m.wap.gqskj.cn/snews/239325.htm
- http://m.wap.gqskj.cn/snews/6703.htm
- http://m.wap.gqskj.cn/snews/786456.htm
- http://m.wap.gqskj.cn/snews/220424.htm
- http://m.wap.gqskj.cn/snews/586827.htm
- http://m.wap.gqskj.cn/snews/2555.htm
- http://m.wap.gqskj.cn/snews/34181.htm
- http://m.wap.gqskj.cn/snews/03777.htm
- http://m.wap.gqskj.cn/snews/2955198.htm
- http://m.wap.gqskj.cn/snews/8862521.htm
- http://m.wap.gqskj.cn/snews/95807.htm
- http://m.wap.gqskj.cn/snews/0394.htm
- http://m.wap.gqskj.cn/snews/93629.htm
- http://m.wap.gqskj.cn/snews/436520.htm
- http://m.wap.gqskj.cn/snews/35071.htm
- http://m.wap.gqskj.cn/snews/52030.htm
- http://m.wap.gqskj.cn/snews/9739992.htm
- http://m.wap.gqskj.cn/snews/1969.htm
- http://m.wap.gqskj.cn/snews/8859160.htm
- http://m.wap.gqskj.cn/snews/310196.htm
- http://m.wap.gqskj.cn/snews/43721.htm
- http://m.wap.gqskj.cn/snews/7648.htm
- http://m.wap.gqskj.cn/snews/898901.htm
- http://m.wap.gqskj.cn/snews/9072.htm
- http://m.wap.gqskj.cn/snews/261952.htm
- http://m.wap.gqskj.cn/snews/0202351.htm
- http://m.wap.gqskj.cn/snews/6564031.htm
- http://m.wap.gqskj.cn/snews/051214.htm
- http://m.wap.gqskj.cn/snews/0547.htm
- http://m.wap.gqskj.cn/snews/6102.htm
- http://m.wap.gqskj.cn/snews/7944824.htm
- http://m.wap.gqskj.cn/snews/853813.htm
- http://m.wap.gqskj.cn/snews/310658.htm
- http://m.wap.gqskj.cn/snews/168729.htm
- http://m.wap.gqskj.cn/snews/297484.htm
- http://m.wap.gqskj.cn/snews/5421271.htm
- http://m.wap.gqskj.cn/snews/951453.htm
- http://m.wap.gqskj.cn/snews/3633713.htm
- http://m.wap.gqskj.cn/snews/4333022.htm
- http://m.wap.gqskj.cn/snews/8804362.htm
- http://m.wap.gqskj.cn/snews/8178.htm
- http://m.wap.gqskj.cn/snews/04582.htm
- http://m.wap.gqskj.cn/snews/116466.htm
- http://m.wap.gqskj.cn/snews/11870.htm
- http://m.wap.gqskj.cn/snews/2536877.htm
- http://m.wap.gqskj.cn/snews/847734.htm
- http://m.wap.gqskj.cn/snews/6811062.htm
- http://m.wap.gqskj.cn/snews/6218.htm
- http://m.wap.gqskj.cn/snews/098301.htm
- http://m.wap.gqskj.cn/snews/0945.htm
- http://m.wap.gqskj.cn/snews/667837.htm
- http://m.wap.gqskj.cn/snews/92870.htm
- http://m.wap.gqskj.cn/snews/182295.htm
- http://m.wap.gqskj.cn/snews/34283.htm
- http://m.wap.gqskj.cn/snews/3082527.htm
- http://m.wap.gqskj.cn/snews/7253.htm
- http://m.wap.gqskj.cn/snews/5584.htm
- http://m.wap.gqskj.cn/snews/994306.htm
- http://m.wap.gqskj.cn/snews/9382.htm
- http://m.wap.gqskj.cn/snews/9862.htm
- http://m.wap.gqskj.cn/snews/8693.htm
- http://m.wap.gqskj.cn/snews/0581141.htm
- http://m.wap.gqskj.cn/snews/4705291.htm
- http://m.wap.gqskj.cn/snews/17835.htm
- http://m.wap.gqskj.cn/snews/223592.htm
- http://m.wap.gqskj.cn/snews/7437.htm
- http://m.wap.gqskj.cn/snews/491998.htm
- http://m.wap.gqskj.cn/snews/808273.htm
- http://m.wap.gqskj.cn/snews/583531.htm
- http://m.wap.gqskj.cn/snews/1737086.htm
- http://m.wap.gqskj.cn/snews/9095587.htm
- http://m.wap.gqskj.cn/snews/69923.htm
- http://m.wap.gqskj.cn/snews/3126986.htm
- http://m.wap.gqskj.cn/snews/381470.htm
- http://m.wap.gqskj.cn/snews/61340.htm
- http://m.wap.gqskj.cn/snews/79789.htm
- http://m.wap.gqskj.cn/snews/75788.htm
- http://m.wap.gqskj.cn/snews/9750.htm
- http://m.wap.gqskj.cn/snews/601473.htm
- http://m.wap.gqskj.cn/snews/9131670.htm
- http://m.wap.gqskj.cn/snews/092819.htm
- http://m.wap.gqskj.cn/snews/7547827.htm
- http://m.wap.gqskj.cn/snews/621769.htm
- http://m.wap.gqskj.cn/snews/823805.htm
- http://m.wap.gqskj.cn/snews/518321.htm
- http://m.wap.gqskj.cn/snews/406289.htm
- http://m.wap.gqskj.cn/snews/188482.htm
- http://m.wap.gqskj.cn/snews/8015.htm
- http://m.wap.gqskj.cn/snews/171226.htm
- http://m.wap.gqskj.cn/snews/84073.htm
- http://m.wap.gqskj.cn/snews/6751036.htm
- http://m.wap.gqskj.cn/snews/04253.htm
- http://m.wap.gqskj.cn/snews/2176537.htm
- http://m.wap.gqskj.cn/snews/3908.htm
- http://m.wap.gqskj.cn/snews/298812.htm
- http://m.wap.gqskj.cn/snews/618649.htm
- http://m.wap.gqskj.cn/snews/4345691.htm
- http://m.wap.gqskj.cn/snews/03812.htm
- http://m.wap.gqskj.cn/snews/5347.htm
- http://m.wap.gqskj.cn/snews/8134745.htm
- http://m.wap.gqskj.cn/snews/278763.htm
- http://m.wap.gqskj.cn/snews/24189.htm
- http://m.wap.gqskj.cn/snews/445890.htm
- http://m.wap.gqskj.cn/snews/9180410.htm
- http://m.wap.gqskj.cn/snews/6149.htm
- http://m.wap.gqskj.cn/snews/916391.htm
- http://m.wap.gqskj.cn/snews/8925.htm
- http://m.wap.gqskj.cn/snews/857166.htm
- http://m.wap.gqskj.cn/snews/4008085.htm
- http://m.wap.gqskj.cn/snews/178328.htm
- http://m.wap.gqskj.cn/snews/82388.htm
- http://m.wap.gqskj.cn/snews/44941.htm
- http://m.wap.gqskj.cn/snews/6700097.htm
- http://m.wap.gqskj.cn/snews/80938.htm
- http://m.wap.gqskj.cn/snews/2050.htm
- http://m.wap.gqskj.cn/snews/0913965.htm
- http://m.wap.gqskj.cn/snews/639283.htm
- http://m.wap.gqskj.cn/snews/7335.htm
- http://m.wap.gqskj.cn/snews/9667090.htm
- http://m.wap.gqskj.cn/snews/6234.htm
- http://m.wap.gqskj.cn/snews/3608.htm
- http://m.wap.gqskj.cn/snews/9619.htm
- http://m.wap.gqskj.cn/snews/995758.htm
- http://m.wap.gqskj.cn/snews/59394.htm
- http://m.wap.gqskj.cn/snews/3441417.htm
- http://m.wap.gqskj.cn/snews/976258.htm
- http://m.wap.gqskj.cn/snews/666439.htm
- http://m.wap.gqskj.cn/snews/4233639.htm
- http://m.wap.gqskj.cn/snews/6129.htm
- http://m.wap.gqskj.cn/snews/06885.htm
- http://m.wap.gqskj.cn/snews/898308.htm
- http://m.wap.gqskj.cn/snews/1097888.htm
- http://m.wap.gqskj.cn/snews/9056725.htm
- http://m.wap.gqskj.cn/snews/30149.htm
- http://m.wap.gqskj.cn/snews/86337.htm
- http://m.wap.gqskj.cn/snews/883860.htm
- http://m.wap.gqskj.cn/snews/064896.htm
- http://m.wap.gqskj.cn/snews/3944.htm
- http://m.wap.gqskj.cn/snews/6636313.htm
- http://m.wap.gqskj.cn/snews/65923.htm
- http://m.wap.gqskj.cn/snews/718938.htm
- http://m.wap.gqskj.cn/snews/45588.htm
- http://m.wap.gqskj.cn/snews/2611.htm
- http://m.wap.gqskj.cn/snews/504078.htm
- http://m.wap.gqskj.cn/snews/88774.htm
- http://m.wap.gqskj.cn/snews/7120474.htm
- http://m.wap.gqskj.cn/snews/2617.htm
- http://m.wap.gqskj.cn/snews/8515445.htm
- http://m.wap.gqskj.cn/snews/6855781.htm
- http://m.wap.gqskj.cn/snews/5042.htm
- http://m.wap.gqskj.cn/snews/29971.htm
- http://m.wap.gqskj.cn/snews/5182467.htm
- http://m.wap.gqskj.cn/snews/8835.htm
- http://m.wap.gqskj.cn/snews/179607.htm
- http://m.wap.gqskj.cn/snews/36743.htm
- http://m.wap.gqskj.cn/snews/7746.htm
- http://m.wap.gqskj.cn/snews/385309.htm
- http://m.wap.gqskj.cn/snews/4654368.htm
- http://m.wap.gqskj.cn/snews/0247.htm
- http://m.wap.gqskj.cn/snews/8110.htm
- http://m.wap.gqskj.cn/snews/7359378.htm
- http://m.wap.gqskj.cn/snews/2458.htm
- http://m.wap.gqskj.cn/snews/3246523.htm
- http://m.wap.gqskj.cn/snews/56565.htm
- http://m.wap.gqskj.cn/snews/95622.htm
- http://m.wap.gqskj.cn/snews/85802.htm
- http://m.wap.gqskj.cn/snews/5259.htm
- http://m.wap.gqskj.cn/snews/7487.htm
- http://m.wap.gqskj.cn/snews/32552.htm
- http://m.wap.gqskj.cn/snews/4353.htm
- http://m.wap.gqskj.cn/snews/8279.htm
- http://m.wap.gqskj.cn/snews/9096752.htm
- http://m.wap.gqskj.cn/snews/55505.htm
- http://m.wap.gqskj.cn/snews/4960068.htm
- http://m.wap.gqskj.cn/snews/5315421.htm
- http://m.wap.gqskj.cn/snews/8677.htm
- http://m.wap.gqskj.cn/snews/5450760.htm
- http://m.wap.gqskj.cn/snews/034957.htm
- http://m.wap.gqskj.cn/snews/9491942.htm
- http://m.wap.gqskj.cn/snews/0402135.htm
- http://m.wap.gqskj.cn/snews/365383.htm
- http://m.wap.gqskj.cn/snews/274696.htm
- http://m.wap.gqskj.cn/snews/95416.htm
- http://m.wap.gqskj.cn/snews/24754.htm
- http://m.wap.gqskj.cn/snews/8577.htm
- http://m.wap.gqskj.cn/snews/365528.htm
- http://m.wap.gqskj.cn/snews/230023.htm
- http://m.wap.gqskj.cn/snews/74591.htm
- http://m.wap.gqskj.cn/snews/2803116.htm
- http://m.wap.gqskj.cn/snews/3672.htm
- http://m.wap.gqskj.cn/snews/9226.htm
- http://m.wap.gqskj.cn/snews/072026.htm
- http://m.wap.gqskj.cn/snews/7550.htm
- http://m.wap.gqskj.cn/snews/5936837.htm
- http://m.wap.gqskj.cn/snews/6367347.htm
- http://m.wap.gqskj.cn/snews/4240.htm
- http://m.wap.gqskj.cn/snews/4724896.htm
- http://m.wap.gqskj.cn/snews/792927.htm
- http://m.wap.gqskj.cn/snews/4861.htm
- http://m.wap.gqskj.cn/snews/6153.htm
- http://m.wap.gqskj.cn/snews/3159.htm
- http://m.wap.gqskj.cn/snews/626917.htm
- http://m.wap.gqskj.cn/snews/4989122.htm
- http://m.wap.gqskj.cn/snews/028218.htm
- http://m.wap.gqskj.cn/snews/0536667.htm
- http://m.wap.gqskj.cn/snews/1521.htm
- http://m.wap.gqskj.cn/snews/995028.htm
- http://m.wap.gqskj.cn/snews/7289.htm
- http://m.wap.gqskj.cn/snews/4482027.htm
- http://m.wap.gqskj.cn/snews/4268185.htm
- http://m.wap.gqskj.cn/snews/821154.htm
- http://m.wap.gqskj.cn/snews/2789376.htm
- http://m.wap.gqskj.cn/snews/0232.htm
- http://m.wap.gqskj.cn/snews/7482900.htm
- http://m.wap.gqskj.cn/snews/0987590.htm
- http://m.wap.gqskj.cn/snews/7066.htm
- http://m.wap.gqskj.cn/snews/66463.htm
- http://m.wap.gqskj.cn/snews/3279425.htm
- http://m.wap.gqskj.cn/snews/7752.htm
- http://m.wap.gqskj.cn/snews/3672538.htm
- http://m.wap.gqskj.cn/snews/1116.htm
- http://m.wap.gqskj.cn/snews/08649.htm
- http://m.wap.gqskj.cn/snews/628574.htm
- http://m.wap.gqskj.cn/snews/64173.htm
- http://m.wap.gqskj.cn/snews/6226.htm
- http://m.wap.gqskj.cn/snews/0087778.htm
- http://m.wap.gqskj.cn/snews/918170.htm
- http://m.wap.gqskj.cn/snews/614338.htm
- http://m.wap.gqskj.cn/snews/3573.htm
- http://m.wap.gqskj.cn/snews/344656.htm
- http://m.wap.gqskj.cn/snews/196640.htm
- http://m.wap.gqskj.cn/snews/3682854.htm
- http://m.wap.gqskj.cn/snews/950514.htm
- http://m.wap.gqskj.cn/snews/65914.htm
- http://m.wap.gqskj.cn/snews/23882.htm
- http://m.wap.gqskj.cn/snews/9435304.htm
- http://m.wap.gqskj.cn/snews/9558.htm
- http://m.wap.gqskj.cn/snews/821606.htm
- http://m.wap.gqskj.cn/snews/089402.htm
- http://m.wap.gqskj.cn/snews/29266.htm

## 项目结构

```
aggregate-service/
├── cmd/                                 # 可执行程序入口
│   └── waplink/                         # 主命令行工具
│       └── main.go                      # 解析参数、加载配置、启动任务
├── internal/                            # 内部包，不对外暴露
│   ├── collector/                       # 抓取调度核心
│   │   ├── pool.go                      # 工作池与并发控制
│   │   └── scheduler.go                 # 任务队列与进度管理
│   ├── extractor/                       # 内容提取模块
│   │   ├── html.go                      # HTML 解析与标签清洗
│   │   └── field.go                     # 基于选择器的字段抽取
│   ├── storage/                         # 存储后端实现
│   │   ├── sqlite.go                    # SQLite 元数据存储
│   │   └── file.go                      # 文件系统持久化
│   └── monitor/                         # 健康检查与告警
│       ├── probe.go                     # HTTP 探测与状态记录
│       └── alert.go                     # 告警条件评估与 Webhook 发送
├── pkg/                                 # 可被外部引用的公共库
│   ├── config/                          # 配置定义与加载
│   │   └── schema.go                    # YAML 配置结构体及默认值
│   └── model/                           # 数据模型
│       └── resource.go                  # URL 资源、抓取结果、状态枚举
├── configs/                             # 示例配置文件
│   ├── example.yaml                     # 基础抓取配置
│   └── production.yaml                  # 生产环境推荐配置（含告警）
├── docs/                                # 完整文档
│   ├── user-guide/                      # 用户手册分章节
│   ├── development/                     # 开发指南与贡献规范
│   └── operations/                      # 运维部署与监控
├── scripts/                             # 辅助脚本
│   ├── setup.sh                         # 初始化开发环境
│   └── benchmark.sh                     # 性能测试脚本
├── test/                                # 测试套件
│   ├── integration/                     # 集成测试用例
│   └── fixtures/                        # 测试用固定数据（模拟 HTML）
├── go.mod                               # Go 模块依赖声明
├── go.sum                               # 依赖校验和
├── Makefile                             # 构建与测试快捷命令
└── README.md                            # 项目介绍与快速入口（本文件）
```

## 贡献指南

1. 查阅 issue 列表，选择未被指派的 bug 修复或功能增强任务，在对应 issue 下回复确认认领，避免多人重复工作。新功能提议请先创建 issue 并获得维护者反馈后再开始编码。

2. 派生项目仓库至个人账户，创建以 `feature/` 或 `fix/` 为前缀的分支，分支名应简要描述变更内容，例如 `feature/add-retry-backoff`。

3. 编写代码时遵循项目既定的代码风格，运行 `make lint` 检查静态错误，确保新增或修改的公开函数包含完整的 godoc 注释。单元测试需覆盖核心逻辑，测试文件放置于对应包下的 `*_test.go` 中。

4. 提交 commit 时使用约定式提交格式，如 `feat: 增加指数退避重试策略`、`fix: 修复 SQLite 连接泄漏问题`，并在 PR 描述中关联相关 issue 编号。

5. 发起 Pull Request 到主仓库的 main 分支，等待持续集成通过及至少一位维护者的 code review。根据反馈进行调整，合并后即成为项目贡献者。

## 常见问题

**Q: 项目是否支持 HTTPS 协议的源站抓取？**

A: 支持。项目底层 HTTP 客户端完全兼容 TLS，无论输入 URL 是 http 还是 https，均按标准协议发起请求。若目标站点存在证书校验问题，可通过配置跳过 insecure 验证，但生产环境不推荐开启。

**Q: 抓取大量 URL 时如何避免被源站封禁？**

A: 项目提供两个关键控制参数：全局并发数限制和单域名请求间隔。建议将并发数设为 5 至 10，并开启 `domain_interval` 选项（单位毫秒），使同一域名下的请求均匀分散。此外，可自定义 User-Agent 和请求头，模拟移动端浏览器行为以降低封禁风险。

**Q: 输出结果中部分字段为空，如何排查？**

A: 首先检查配置文件中的提取规则是否匹配页面实际 DOM 结构。建议开启 `debug` 日志模式，查看每个 URL 的原始响应体前 500 字符。若页面为动态渲染内容，需结合项目提供的 headless 浏览器扩展模块（独立子项目）进行预渲染后再抽取。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:57
