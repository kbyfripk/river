# LinkVault Core

LinkVault Core 是一个面向技术内容聚合与结构化外链管理的开源静态资源导航系统。本项目定位于为开发者、技术博主、运维工程师以及研究分析人员提供一套可本地部署、可定制、高性能的外链数据托管与检索框架。其核心价值在于将分散、易失效的外部参考链接进行集中化、语义化与版本化管理，解决技术文档中“引用漂移”与“资源散落”两大痛点。系统设计上遵循约定优于配置原则，兼容 Markdown 内容驱动，支持无数据库全静态化运行，亦可对接 JSON API 实现动态索引更新，适用于个人知识库、团队技术周报、项目文档站等多种内容生态。

## 功能概览

批量外链导入与结构化存储：支持通过 CSV 或 JSON 批量导入链接元数据，自动识别 URL 参数与路径层级，生成统一资源标识符映射表。

多维度标签分类体系：内置轻量级标签引擎，允许对每个外链附加领域、用途、可信度、更新周期等自定义标签，支持多标签交集检索。

全文本标题与摘要索引：基于 Bleve 或 Zinc 实现毫秒级全文检索，索引内容涵盖链接标题、页面摘要及人工批注，支持中英文混合查询。

定时可用性健康检查：集成链接存活检测模块，可配置定时任务（cron 表达式）对全部外链发起 HEAD 请求，自动标记失效链接并生成报告。

静态站点生成器兼容层：提供 Hugo、VuePress、Astro 等流行 SSG 的 data 文件导出接口，使得外链数据可直接挂载为静态站点的数据源。

私有化部署与权限分级：支持基于 .htaccess 或 JWT 的只读/管理双模式访问控制，适用于团队内部共享链接库，避免资源被非授权爬取。

CLI 工具链全生命周期管理：提供 linkvault 命令行工具，涵盖 init、import、check、export、serve 五个子命令，支持脚本化运维与 CI/CD 集成。

## 应用场景

技术团队内部周报与文档归档：团队技术负责人每周汇总项目进展、踩坑记录、外部参考文章时，可使用 LinkVault Core 快速收录所有外链，并自动生成带摘要的链接清单，直接嵌入 Confluence 或 Notion 周报模板。

开源项目 README 与官网资源导航：开源项目维护者可将项目依赖的规范文档、API 参考、社区讨论、镜像地址等外链统一托管于 LinkVault，通过静态导出功能生成资源列表页，避免在 README 中堆砌过长裸链接。

个人技术博客与知识库引用管理：技术博主在写作过程中引用大量外部资料时，可先将链接录入 LinkVault，利用其标签分类和检索功能进行整理，写作时仅需引用资源 ID，系统自动渲染为带脚注的引用列表，提升文章可维护性。

安全研究信息聚合与 IOC 共享：安全分析人员可每日采集威胁情报报告、CVE 详情页、POC 代码仓库等链接，通过 LinkVault 的定时健康检查功能监控这些关键资源的可访问性，一旦失效及时发出告警。

## 快速开始

以下命令演示了从源码克隆到启动开发服务的完整流程。

```bash
git clone https://github.com/linkvault/core.git linkvault-core
cd linkvault-core
make setup
# 或直接使用 go install 安装 CLI
go install ./cmd/linkvault
linkvault init --config config.example.yaml
linkvault import --source data/links.json
linkvault check --workers 10
linkvault serve --port 8080
```

生产环境部署建议使用 release 页面提供的预编译二进制文件，并配合 systemd 或 supervisor 进行进程守护。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Go 编译器 | 1.21 及以上 | 用于从源码编译 CLI 工具与核心服务 |
| make | 3.81 及以上 | 构建脚本与自动化任务执行器 |
| git | 2.30 及以上 | 克隆仓库及版本控制 |
| SQLite | 3.35 及以上（嵌入式） | 默认元数据存储引擎，无需额外安装 |
| Redis（可选） | 6.2 及以上 | 启用分布式缓存或任务队列时需配置 |
| Node.js（可选） | 18.x LTS | 仅当使用前端仪表盘或 SSG 导出功能时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/ | 如何安装、配置、导入链接、执行健康检查、导出数据？ |
| 开发者指南 | /docs/developer-guide/ | 如何二次开发、扩展标签引擎、替换存储后端、编写自定义检查器？ |
| 运维参考 | /docs/operations/ | 如何设置定时任务、配置反向代理、调优并发检查性能、迁移数据库？ |
| API 规范 | /docs/api/ | RESTful API 端点定义、请求/响应格式、鉴权方式、分页与过滤参数说明？ |
| 设计文档 | /docs/design/ | 系统整体架构、数据模型 ER 图、检索算法原理、插件化设计思路？ |

## 资源列表

- http://m.3g.fcful.cn/snews/581311.htm
- http://m.3g.fcful.cn/snews/5937.htm
- http://m.3g.fcful.cn/snews/8608487.htm
- http://m.3g.fcful.cn/snews/0901.htm
- http://m.3g.fcful.cn/snews/637694.htm
- http://m.3g.fcful.cn/snews/046029.htm
- http://m.3g.fcful.cn/snews/8487.htm
- http://m.3g.fcful.cn/snews/59656.htm
- http://m.3g.fcful.cn/snews/3397500.htm
- http://m.3g.fcful.cn/snews/71422.htm
- http://m.3g.fcful.cn/snews/30205.htm
- http://m.3g.fcful.cn/snews/621724.htm
- http://m.3g.fcful.cn/snews/915609.htm
- http://m.3g.fcful.cn/snews/8054308.htm
- http://m.3g.fcful.cn/snews/5468781.htm
- http://m.3g.fcful.cn/snews/3259.htm
- http://m.3g.fcful.cn/snews/6537891.htm
- http://m.3g.fcful.cn/snews/4080462.htm
- http://m.3g.fcful.cn/snews/30060.htm
- http://m.3g.fcful.cn/snews/52651.htm
- http://m.3g.fcful.cn/snews/1882158.htm
- http://m.3g.fcful.cn/snews/867077.htm
- http://m.3g.fcful.cn/snews/817084.htm
- http://m.3g.fcful.cn/snews/153879.htm
- http://m.3g.fcful.cn/snews/64037.htm
- http://m.3g.fcful.cn/snews/2708.htm
- http://m.3g.fcful.cn/snews/4319.htm
- http://m.3g.fcful.cn/snews/93728.htm
- http://m.3g.fcful.cn/snews/0037.htm
- http://m.3g.fcful.cn/snews/2078799.htm
- http://m.3g.fcful.cn/snews/3452.htm
- http://m.3g.fcful.cn/snews/83650.htm
- http://m.3g.fcful.cn/snews/617648.htm
- http://m.3g.fcful.cn/snews/14952.htm
- http://m.3g.fcful.cn/snews/6748986.htm
- http://m.3g.fcful.cn/snews/34488.htm
- http://m.3g.fcful.cn/snews/4514.htm
- http://m.3g.fcful.cn/snews/6167426.htm
- http://m.3g.fcful.cn/snews/9648405.htm
- http://m.3g.fcful.cn/snews/7035.htm
- http://m.3g.fcful.cn/snews/650745.htm
- http://m.3g.fcful.cn/snews/5087.htm
- http://m.3g.fcful.cn/snews/598575.htm
- http://m.3g.fcful.cn/snews/6295872.htm
- http://m.3g.fcful.cn/snews/0722.htm
- http://m.3g.fcful.cn/snews/789982.htm
- http://m.3g.fcful.cn/snews/75160.htm
- http://m.3g.fcful.cn/snews/58356.htm
- http://m.3g.fcful.cn/snews/8078.htm
- http://m.3g.fcful.cn/snews/308238.htm
- http://m.3g.fcful.cn/snews/8849.htm
- http://m.3g.fcful.cn/snews/0596291.htm
- http://m.3g.fcful.cn/snews/1849.htm
- http://m.3g.fcful.cn/snews/642573.htm
- http://m.3g.fcful.cn/snews/07845.htm
- http://m.3g.fcful.cn/snews/3033685.htm
- http://m.3g.fcful.cn/snews/9375.htm
- http://m.3g.fcful.cn/snews/0983406.htm
- http://m.3g.fcful.cn/snews/50640.htm
- http://m.3g.fcful.cn/snews/2988208.htm
- http://m.3g.fcful.cn/snews/4883089.htm
- http://m.3g.fcful.cn/snews/4274513.htm
- http://m.3g.fcful.cn/snews/85156.htm
- http://m.3g.fcful.cn/snews/2813.htm
- http://m.3g.fcful.cn/snews/7447759.htm
- http://m.3g.fcful.cn/snews/6357.htm
- http://m.3g.fcful.cn/snews/4148905.htm
- http://m.3g.fcful.cn/snews/5787144.htm
- http://m.3g.fcful.cn/snews/7556108.htm
- http://m.3g.fcful.cn/snews/2587401.htm
- http://m.3g.fcful.cn/snews/3589938.htm
- http://m.3g.fcful.cn/snews/825598.htm
- http://m.3g.fcful.cn/snews/490832.htm
- http://m.3g.fcful.cn/snews/98835.htm
- http://m.3g.fcful.cn/snews/63249.htm
- http://m.3g.fcful.cn/snews/7887.htm
- http://m.3g.fcful.cn/snews/5236.htm
- http://m.3g.fcful.cn/snews/723944.htm
- http://m.3g.fcful.cn/snews/5218080.htm
- http://m.3g.fcful.cn/snews/396518.htm
- http://m.3g.fcful.cn/snews/581121.htm
- http://m.3g.fcful.cn/snews/49762.htm
- http://m.3g.fcful.cn/snews/866749.htm
- http://m.3g.fcful.cn/snews/7205254.htm
- http://m.3g.fcful.cn/snews/367574.htm
- http://m.3g.fcful.cn/snews/8634.htm
- http://m.3g.fcful.cn/snews/7718.htm
- http://m.3g.fcful.cn/snews/0237180.htm
- http://m.3g.fcful.cn/snews/240067.htm
- http://m.3g.fcful.cn/snews/485548.htm
- http://m.3g.fcful.cn/snews/24604.htm
- http://m.3g.fcful.cn/snews/9975021.htm
- http://m.3g.fcful.cn/snews/901977.htm
- http://m.3g.fcful.cn/snews/4051107.htm
- http://m.3g.fcful.cn/snews/7934.htm
- http://m.3g.fcful.cn/snews/4268.htm
- http://m.3g.fcful.cn/snews/0133.htm
- http://m.3g.fcful.cn/snews/5157213.htm
- http://m.3g.fcful.cn/snews/2948.htm
- http://m.3g.fcful.cn/snews/8365271.htm
- http://m.3g.fcful.cn/snews/5093631.htm
- http://m.3g.fcful.cn/snews/9208384.htm
- http://m.3g.fcful.cn/snews/734103.htm
- http://m.3g.fcful.cn/snews/7906783.htm
- http://m.3g.fcful.cn/snews/7395.htm
- http://m.3g.fcful.cn/snews/8238.htm
- http://m.3g.fcful.cn/snews/89697.htm
- http://m.3g.fcful.cn/snews/21683.htm
- http://m.3g.fcful.cn/snews/09464.htm
- http://m.3g.fcful.cn/snews/499415.htm
- http://m.3g.fcful.cn/snews/433024.htm
- http://m.3g.fcful.cn/snews/2481.htm
- http://m.3g.fcful.cn/snews/0404.htm
- http://m.3g.fcful.cn/snews/5688.htm
- http://m.3g.fcful.cn/snews/594196.htm
- http://m.3g.fcful.cn/snews/1066649.htm
- http://m.3g.fcful.cn/snews/302902.htm
- http://m.3g.fcful.cn/snews/4202.htm
- http://m.3g.fcful.cn/snews/0315.htm
- http://m.3g.fcful.cn/snews/2108.htm
- http://m.3g.fcful.cn/snews/78486.htm
- http://m.3g.fcful.cn/snews/27303.htm
- http://m.3g.fcful.cn/snews/660039.htm
- http://m.3g.fcful.cn/snews/0923.htm
- http://m.3g.fcful.cn/snews/7672.htm
- http://m.3g.fcful.cn/snews/917722.htm
- http://m.3g.fcful.cn/snews/7632.htm
- http://m.3g.fcful.cn/snews/643177.htm
- http://m.3g.fcful.cn/snews/6330846.htm
- http://m.3g.fcful.cn/snews/0438133.htm
- http://m.3g.fcful.cn/snews/903546.htm
- http://m.3g.fcful.cn/snews/2344123.htm
- http://m.3g.fcful.cn/snews/33859.htm
- http://m.3g.fcful.cn/snews/80059.htm
- http://m.3g.fcful.cn/snews/9733.htm
- http://m.3g.fcful.cn/snews/28662.htm
- http://m.3g.fcful.cn/snews/5149952.htm
- http://m.3g.fcful.cn/snews/320353.htm
- http://m.3g.fcful.cn/snews/5604.htm
- http://m.3g.fcful.cn/snews/3598357.htm
- http://m.3g.fcful.cn/snews/54432.htm
- http://m.3g.fcful.cn/snews/4762.htm
- http://m.3g.fcful.cn/snews/7495354.htm
- http://m.3g.fcful.cn/snews/04742.htm
- http://m.3g.fcful.cn/snews/0040370.htm
- http://m.3g.fcful.cn/snews/271267.htm
- http://m.3g.fcful.cn/snews/30936.htm
- http://m.3g.fcful.cn/snews/7732760.htm
- http://m.3g.fcful.cn/snews/10290.htm
- http://m.3g.fcful.cn/snews/1904.htm
- http://m.3g.fcful.cn/snews/868725.htm
- http://m.3g.fcful.cn/snews/8187.htm
- http://m.3g.fcful.cn/snews/80607.htm
- http://m.3g.fcful.cn/snews/5220.htm
- http://m.3g.fcful.cn/snews/2192.htm
- http://m.3g.fcful.cn/snews/14008.htm
- http://m.3g.fcful.cn/snews/62502.htm
- http://m.3g.fcful.cn/snews/982038.htm
- http://m.3g.fcful.cn/snews/995563.htm
- http://m.3g.fcful.cn/snews/0091322.htm
- http://m.3g.fcful.cn/snews/8466584.htm
- http://m.3g.fcful.cn/snews/8092496.htm
- http://m.3g.fcful.cn/snews/9793997.htm
- http://m.3g.fcful.cn/snews/076766.htm
- http://m.3g.fcful.cn/snews/8336.htm
- http://m.3g.fcful.cn/snews/6638.htm
- http://m.3g.fcful.cn/snews/8331050.htm
- http://m.3g.fcful.cn/snews/387107.htm
- http://m.3g.fcful.cn/snews/311918.htm
- http://m.3g.fcful.cn/snews/495401.htm
- http://m.3g.fcful.cn/snews/7028847.htm
- http://m.3g.fcful.cn/snews/6050505.htm
- http://m.3g.fcful.cn/snews/26305.htm
- http://m.3g.fcful.cn/snews/724261.htm
- http://m.3g.fcful.cn/snews/899726.htm
- http://m.3g.fcful.cn/snews/3376208.htm
- http://m.3g.fcful.cn/snews/14290.htm
- http://m.3g.fcful.cn/snews/94048.htm
- http://m.3g.fcful.cn/snews/3602.htm
- http://m.3g.fcful.cn/snews/094409.htm
- http://m.3g.fcful.cn/snews/26500.htm
- http://m.3g.fcful.cn/snews/68109.htm
- http://m.3g.fcful.cn/snews/91150.htm
- http://m.3g.fcful.cn/snews/2841742.htm
- http://m.3g.fcful.cn/snews/81563.htm
- http://m.3g.fcful.cn/snews/546213.htm
- http://m.3g.fcful.cn/snews/176030.htm
- http://m.3g.fcful.cn/snews/448226.htm
- http://m.3g.fcful.cn/snews/450701.htm
- http://m.3g.fcful.cn/snews/117342.htm
- http://m.3g.fcful.cn/snews/87731.htm
- http://m.3g.fcful.cn/snews/04760.htm
- http://m.3g.fcful.cn/snews/8015918.htm
- http://m.3g.fcful.cn/snews/73844.htm
- http://m.3g.fcful.cn/snews/23943.htm
- http://m.3g.fcful.cn/snews/80040.htm
- http://m.3g.fcful.cn/snews/6351227.htm
- http://m.3g.fcful.cn/snews/7647.htm
- http://m.3g.fcful.cn/snews/7598.htm
- http://m.3g.fcful.cn/snews/9348.htm
- http://m.3g.fcful.cn/snews/86420.htm
- http://m.3g.fcful.cn/snews/18577.htm
- http://m.3g.fcful.cn/snews/228631.htm
- http://m.3g.fcful.cn/snews/3995.htm
- http://m.3g.fcful.cn/snews/5229310.htm
- http://m.3g.fcful.cn/snews/1569.htm
- http://m.3g.fcful.cn/snews/0260.htm
- http://m.3g.fcful.cn/snews/1159906.htm
- http://m.3g.fcful.cn/snews/521933.htm
- http://m.3g.fcful.cn/snews/115082.htm
- http://m.3g.fcful.cn/snews/6362080.htm
- http://m.3g.fcful.cn/snews/7918279.htm
- http://m.3g.fcful.cn/snews/00277.htm
- http://m.3g.fcful.cn/snews/65791.htm
- http://m.3g.fcful.cn/snews/58579.htm
- http://m.3g.fcful.cn/snews/455901.htm
- http://m.3g.fcful.cn/snews/3120917.htm
- http://m.3g.fcful.cn/snews/3779.htm
- http://m.3g.fcful.cn/snews/2321.htm
- http://m.3g.fcful.cn/snews/88175.htm
- http://m.3g.fcful.cn/snews/8548.htm
- http://m.3g.fcful.cn/snews/62626.htm
- http://m.3g.fcful.cn/snews/26232.htm
- http://m.3g.fcful.cn/snews/918544.htm
- http://m.3g.fcful.cn/snews/5312818.htm
- http://m.3g.fcful.cn/snews/294142.htm
- http://m.3g.fcful.cn/snews/7086.htm
- http://m.3g.fcful.cn/snews/7062837.htm
- http://m.3g.fcful.cn/snews/6134541.htm
- http://m.3g.fcful.cn/snews/306025.htm
- http://m.3g.fcful.cn/snews/398919.htm
- http://m.3g.fcful.cn/snews/678782.htm
- http://m.3g.fcful.cn/snews/7264377.htm
- http://m.3g.fcful.cn/snews/2242.htm
- http://m.3g.fcful.cn/snews/25820.htm
- http://m.3g.fcful.cn/snews/06549.htm
- http://m.3g.fcful.cn/snews/257592.htm
- http://m.3g.fcful.cn/snews/2653317.htm
- http://m.3g.fcful.cn/snews/0905221.htm
- http://m.3g.fcful.cn/snews/592781.htm
- http://m.3g.fcful.cn/snews/56626.htm
- http://m.3g.fcful.cn/snews/721781.htm
- http://m.3g.fcful.cn/snews/3015.htm
- http://m.3g.fcful.cn/snews/164032.htm
- http://m.3g.fcful.cn/snews/725918.htm
- http://m.3g.fcful.cn/snews/5111722.htm
- http://m.3g.fcful.cn/snews/659977.htm
- http://m.3g.fcful.cn/snews/8968604.htm
- http://m.3g.fcful.cn/snews/94476.htm
- http://m.3g.fcful.cn/snews/6437602.htm

## 项目结构

```
linkvault-core/
├── cmd/                                # 命令行入口目录
│   └── linkvault/                      # 主 CLI 程序入口
│       └── main.go                     # 初始化 cobra 根命令，注册子命令
├── internal/                           # 内部私有包，不对外暴露 API
│   ├── importer/                       # 导入引擎：解析 CSV/JSON，数据清洗与校验
│   │   ├── parser.go                   # 格式解析器，支持自动检测文件类型
│   │   └── validator.go                # URL 合法性校验与去重逻辑
│   ├── health/                         # 健康检查模块：并发探测与状态记录
│   │   ├── checker.go                  # 基于 http.Client 的 HEAD/GET 探测实现
│   │   └── scheduler.go                # cron 调度器，管理周期性检查任务
│   ├── indexer/                        # 索引构建模块：对接 Bleve 或内存倒排索引
│   │   ├── bleve_adapter.go            # Bleve 索引适配器，含分词与查询解析
│   │   └── memory_index.go             # 内存索引实现，用于轻量级快速启动
│   └── storage/                        # 存储抽象层：支持 SQLite 及未来扩展
│       ├── sqlite_repo.go              # SQLite 元数据仓库实现，含表结构迁移
│       └── cache.go                    # 可选 Redis 缓存装饰器，加速热点查询
├── pkg/                                # 可被外部引用的公共库
│   ├── model/                          # 数据模型定义：Link, Tag, CheckResult 等
│   │   └── link.go                     # Link 结构体及 JSON/DB 标签映射
│   └── utils/                          # 通用工具函数：时间处理、随机数、字符串操作
│       └── url_utils.go                # URL 规范化、域名提取、路径安全校验
├── configs/                            # 配置文件模板与示例
│   ├── config.example.yaml             # 完整配置示例，含注释说明每个字段
│   └── config.prod.yaml                # 生产环境推荐配置（调优参数）
├── docs/                               # 项目文档源文件
│   ├── user-guide/                     # 用户手册分章节 Markdown 文件
│   ├── developer-guide/                # 开发者指南与插件编写教程
│   └── api/                            # OpenAPI 规范（swagger.yaml）及接口说明
├── scripts/                            # 辅助脚本：构建、打包、发布
│   ├── build.sh                        # 多平台交叉编译脚本
│   ├── release.sh                      # GitHub Release 自动化上传与 CHANGELOG 生成
│   └── docker/                         # Dockerfile 及容器编排配置
│       └── Dockerfile                  # 基于 Alpine 的轻量镜像构建文件
├── testdata/                           # 测试数据集与模拟链接列表
│   ├── sample_links.json               # 100 条示例链接用于功能测试
│   └── broken_links.csv                # 包含失效链接的测试集
├── go.mod                              # Go 模块定义，含所有依赖版本锁定
├── go.sum                              # 依赖校验和文件
├── Makefile                            # 统一构建入口：setup, build, test, clean
└── README.md                           # 本文档
```

## 贡献指南

请先阅读项目行为准则（CODE_OF_CONDUCT.md）。所有贡献均需通过 GitHub Pull Request 流程提交，并在提交前签署开发者原产地证书（DCO）。

开发环境准备：Fork 本仓库至个人账号，克隆到本地后执行 make setup 安装所有开发依赖（golangci-lint、goimports、mockgen 等）。确保本地 Go 版本不低于 1.21。

代码规范要求：所有 Go 源码必须通过 golangci-lint 检查（使用项目根目录的 .golangci.yml 配置），并遵循 Google Go 代码风格指南。提交前请运行 make fmt 自动格式化代码。

测试覆盖标准：新增功能或修复缺陷必须附带单元测试，测试文件置于对应包下的 *_test.go 中。关键路径（如导入引擎、健康检查并发控制）的行覆盖率不得低于 85%。运行 make test 执行全部测试用例。

提交信息格式：遵循 Conventional Commits 规范，提交信息首行必须包含 type(scope): subject 格式，例如 feat(importer): add CSV header auto-detection。PR 描述中需关联对应 issue 编号。

文档同步要求：任何影响用户使用方式或配置格式的变更，必须同步更新 /docs 下对应章节以及 README 中的快速开始示例。API 变更需同步更新 OpenAPI 规范文件。

## 常见问题

问：启动时提示 "database schema version mismatch" 如何解决？
答：此错误表明当前二进制文件的预期数据库版本与实际 SQLite 文件的结构版本不一致。通常发生在升级版本后未执行迁移。请运行 linkvault migrate --up 命令自动执行增量迁移脚本。如果迁移失败，请备份 data/linkvault.db 文件后重新运行 linkvault init --force 重建数据库，再通过 linkvault import 重新导入链接数据。

问：健康检查模块检测大量链接时出现超时或文件描述符耗尽，如何优化？
答：健康检查默认使用每主机 2 个并发连接的限制，并通过全局 worker 池控制总并发数。若遇到超时，可调大 config.yaml 中的 check.timeout 字段（单位秒）以及 check.max_workers 字段。若出现文件描述符不足，请调整操作系统 ulimit -n 上限，或在配置中启用 check.http_keep_alive 为 false 以关闭连接复用。对于大规模链接（超过 5000 条），建议将 check.batch_size 设为 200 并启用 check.random_delay 避免被目标服务器限流。

问：如何将 LinkVault Core 部署为 systemd 守护进程以实现开机自启？
答：在 releases 页面下载对应平台的预编译二进制文件，放置于 /usr/local/bin/linkvault。创建系统用户 linkvault，并将配置文件置于 /etc/linkvault/config.yaml。然后编写 systemd unit 文件 /etc/systemd/system/linkvault.service，内容包含 ExecStart=/usr/local/bin/linkvault serve --config /etc/linkvault/config.yaml，以及 Restart=always 和 User=linkvault。执行 systemctl daemon-reload，随后 systemctl enable linkvault 与 systemctl start linkvault 即可。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
