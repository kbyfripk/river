# WapNav 移动端外链资源聚合系统

WapNav 是一个面向移动端网页资源的外链汇总与导航系统，专为需要快速检索、分类管理与批量访问移动端新闻页、信息页的技术人员与内容研究者设计。该项目通过结构化方式收录并索引大量移动端 URL 资源，提供统一的资源视图与可扩展的检索接口，适用于个人知识库构建、移动端页面归档、外链有效性监控等场景。

目标用户包括前端开发者、内容运营人员、信息安全分析员以及需要批量处理移动端链接的自动化运维工程师。WapNav 不依赖复杂框架，以轻量级脚本和静态数据为核心，可在数分钟内完成部署并开始收录资源。

## 功能概览

批量外链导入与去重 系统支持从文本文件、CSV 或标准输入流中批量导入 URL 列表，自动执行语法校验与去重处理，避免重复收录。

资源分类标签管理 每条外链可关联多个自定义标签（如“新闻”、“公告”、“归档”），支持按标签快速筛选与分组统计。

链接可达性健康检查 内置异步 HTTP 探测模块，可定期检测已收录链接的状态码与响应时间，标记异常链接并生成报告。

全文元数据提取 对目标页面自动提取标题、字符编码、最后修改时间等基础元数据，为后续检索提供结构化字段。

灵活的数据导出接口 支持将资源列表导出为 JSON、CSV 或纯文本格式，便于与其他数据处理工具或监控系统集成。

命令行与配置文件双模式 提供 CLI 工具与 YAML 配置文件两种操作方式，满足自动化脚本与人工维护的不同需求。

增量更新与版本追踪 每次导入或修改资源时记录变更日志，支持回滚至任意历史版本，保障资源库的可追溯性。

## 应用场景

移动端新闻聚合分析 内容研究人员可通过 WapNav 批量收录指定来源的移动端新闻页，结合元数据提取功能进行时间线梳理与关键词频分析，辅助趋势研判。

外链有效性监控 运维人员配置定时任务，定期对收录的移动端链接进行 HTTP 探测，自动生成失效链接报表，减少人工巡检成本。

移动端页面归档与备份 运营团队可将重要移动端公告页或信息页的链接集中纳入 WapNav 管理，配合外部归档工具实现批量快照保存。

开发环境测试数据构建 前端开发者在构建移动端适配测试环境时，使用 WapNav 导出的链接列表作为种子数据，快速填充测试页面库。

## 快速开始

以下命令演示从克隆仓库到启动服务的完整流程：

```bash
git clone https://github.com/example/wapnav.git
cd wapnav
pip install -r requirements.txt
cp config.example.yaml config.yaml
python wapnav.py init
python wapnav.py import --input urls.txt
python wapnav.py serve --port 8080
```

若使用 Docker 方式运行，可执行：

```bash
docker build -t wapnav:latest .
docker run -d -p 8080:8080 -v ./data:/app/data wapnav:latest
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS |
| requests | 2.25.0 及以上 | HTTP 探测与页面获取依赖库 |
| pyyaml | 5.4.0 及以上 | 配置文件解析与序列化支持 |
| click | 8.0.0 及以上 | 命令行界面交互框架 |
| aiohttp | 3.8.0 及以上 | 异步并发链接健康检查加速模块 |
| lxml | 4.9.0 及以上 | HTML 元数据提取与解析引擎 |
| sqlite3 | 内置模块 | 本地资源索引数据库，无需额外安装 |

操作系统支持 Linux（glibc 2.17+）、macOS 10.15+ 及 Windows 10（WSL 环境推荐）。硬件最低要求为 512MB 内存与 1GB 可用磁盘空间，生产环境建议 2GB 内存以上。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、管理标签、执行健康检查与导出数据 |
| 配置参考 | docs/config-reference.md | config.yaml 中每一项配置参数的含义与示例 |
| API 开发文档 | docs/api-development.md | 如何扩展自定义导入器、元数据提取器或通知插件 |
| 运维部署指南 | docs/deployment.md | 如何在生产环境中使用 systemd 或容器编排工具运行 WapNav |
| 常见问题集 | docs/faq.md | 包含网络超时、数据库锁、编码异常等典型问题的解决方案 |
| 变更日志 | CHANGELOG.md | 记录每个版本的功能增删、性能优化与缺陷修复 |

## 资源列表

- http://m.wap.fcful.cn/nnews/199640.htm
- http://m.wap.fcful.cn/nnews/5380.htm
- http://m.wap.fcful.cn/nnews/3879.htm
- http://m.wap.fcful.cn/nnews/426237.htm
- http://m.wap.fcful.cn/nnews/42964.htm
- http://m.wap.fcful.cn/nnews/9387409.htm
- http://m.wap.fcful.cn/nnews/75876.htm
- http://m.wap.fcful.cn/nnews/7675.htm
- http://m.wap.fcful.cn/nnews/501822.htm
- http://m.wap.fcful.cn/nnews/32292.htm
- http://m.wap.fcful.cn/nnews/9053202.htm
- http://m.wap.fcful.cn/nnews/5731691.htm
- http://m.wap.fcful.cn/nnews/226050.htm
- http://m.wap.fcful.cn/nnews/02427.htm
- http://m.wap.fcful.cn/nnews/000319.htm
- http://m.wap.fcful.cn/nnews/8431339.htm
- http://m.wap.fcful.cn/nnews/58378.htm
- http://m.wap.fcful.cn/nnews/9329.htm
- http://m.wap.fcful.cn/nnews/9095807.htm
- http://m.wap.fcful.cn/nnews/0114261.htm
- http://m.wap.fcful.cn/nnews/3861.htm
- http://m.wap.fcful.cn/nnews/1291.htm
- http://m.wap.fcful.cn/nnews/23294.htm
- http://m.wap.fcful.cn/nnews/51982.htm
- http://m.wap.fcful.cn/nnews/0717930.htm
- http://m.wap.fcful.cn/nnews/395728.htm
- http://m.wap.fcful.cn/nnews/8517.htm
- http://m.wap.fcful.cn/nnews/5631.htm
- http://m.wap.fcful.cn/nnews/356146.htm
- http://m.wap.fcful.cn/nnews/25073.htm
- http://m.wap.fcful.cn/nnews/982027.htm
- http://m.wap.fcful.cn/nnews/5298616.htm
- http://m.wap.fcful.cn/nnews/634058.htm
- http://m.wap.fcful.cn/nnews/9359.htm
- http://m.wap.fcful.cn/nnews/7437760.htm
- http://m.wap.fcful.cn/nnews/78022.htm
- http://m.wap.fcful.cn/nnews/7510269.htm
- http://m.wap.fcful.cn/nnews/94241.htm
- http://m.wap.fcful.cn/nnews/192515.htm
- http://m.wap.fcful.cn/nnews/5708.htm
- http://m.wap.fcful.cn/nnews/255265.htm
- http://m.wap.fcful.cn/nnews/53812.htm
- http://m.wap.fcful.cn/nnews/088199.htm
- http://m.wap.fcful.cn/nnews/7344311.htm
- http://m.wap.fcful.cn/nnews/92383.htm
- http://m.wap.fcful.cn/nnews/70016.htm
- http://m.wap.fcful.cn/nnews/2694768.htm
- http://m.wap.fcful.cn/nnews/787375.htm
- http://m.wap.fcful.cn/nnews/1513.htm
- http://m.wap.fcful.cn/nnews/403822.htm
- http://m.wap.fcful.cn/nnews/147641.htm
- http://m.wap.fcful.cn/nnews/6695574.htm
- http://m.wap.fcful.cn/nnews/942771.htm
- http://m.wap.fcful.cn/nnews/4631040.htm
- http://m.wap.fcful.cn/nnews/2331.htm
- http://m.wap.fcful.cn/nnews/31002.htm
- http://m.wap.fcful.cn/nnews/6234.htm
- http://m.wap.fcful.cn/nnews/186023.htm
- http://m.wap.fcful.cn/nnews/1000537.htm
- http://m.wap.fcful.cn/nnews/6007719.htm
- http://m.wap.fcful.cn/nnews/6323.htm
- http://m.wap.fcful.cn/nnews/3350215.htm
- http://m.wap.fcful.cn/nnews/938921.htm
- http://m.wap.fcful.cn/nnews/9239027.htm
- http://m.wap.fcful.cn/nnews/6567325.htm
- http://m.wap.fcful.cn/nnews/8762170.htm
- http://m.wap.fcful.cn/nnews/5022498.htm
- http://m.wap.fcful.cn/nnews/9009.htm
- http://m.wap.fcful.cn/nnews/7969.htm
- http://m.wap.fcful.cn/nnews/7770.htm
- http://m.wap.fcful.cn/nnews/3931102.htm
- http://m.wap.fcful.cn/nnews/46591.htm
- http://m.wap.fcful.cn/nnews/2469783.htm
- http://m.wap.fcful.cn/nnews/65484.htm
- http://m.wap.fcful.cn/nnews/435568.htm
- http://m.wap.fcful.cn/nnews/9816210.htm
- http://m.wap.fcful.cn/nnews/3422.htm
- http://m.wap.fcful.cn/nnews/8146569.htm
- http://m.wap.fcful.cn/nnews/5127.htm
- http://m.wap.fcful.cn/nnews/604152.htm
- http://m.wap.fcful.cn/nnews/47775.htm
- http://m.wap.fcful.cn/nnews/783596.htm
- http://m.wap.fcful.cn/nnews/82248.htm
- http://m.wap.fcful.cn/nnews/417630.htm
- http://m.wap.fcful.cn/nnews/4189523.htm
- http://m.wap.fcful.cn/nnews/719361.htm
- http://m.wap.fcful.cn/nnews/13522.htm
- http://m.wap.fcful.cn/nnews/5030528.htm
- http://m.wap.fcful.cn/nnews/84458.htm
- http://m.wap.fcful.cn/nnews/6509.htm
- http://m.wap.fcful.cn/nnews/33049.htm
- http://m.wap.fcful.cn/nnews/8397000.htm
- http://m.wap.fcful.cn/nnews/786051.htm
- http://m.wap.fcful.cn/nnews/0046.htm
- http://m.wap.fcful.cn/nnews/908554.htm
- http://m.wap.fcful.cn/nnews/2863931.htm
- http://m.wap.fcful.cn/nnews/75585.htm
- http://m.wap.fcful.cn/nnews/7259810.htm
- http://m.wap.fcful.cn/nnews/115411.htm
- http://m.wap.fcful.cn/nnews/4525.htm
- http://m.wap.fcful.cn/nnews/800937.htm
- http://m.wap.fcful.cn/nnews/7624.htm
- http://m.wap.fcful.cn/nnews/214665.htm
- http://m.wap.fcful.cn/nnews/3771290.htm
- http://m.wap.fcful.cn/nnews/715649.htm
- http://m.wap.fcful.cn/nnews/8929297.htm
- http://m.wap.fcful.cn/nnews/8623231.htm
- http://m.wap.fcful.cn/nnews/06165.htm
- http://m.wap.fcful.cn/nnews/6169.htm
- http://m.wap.fcful.cn/nnews/70597.htm
- http://m.wap.fcful.cn/nnews/558736.htm
- http://m.wap.fcful.cn/nnews/69049.htm
- http://m.wap.fcful.cn/nnews/25162.htm
- http://m.wap.fcful.cn/nnews/8758063.htm
- http://m.wap.fcful.cn/nnews/1765.htm
- http://m.wap.fcful.cn/nnews/4149.htm
- http://m.wap.fcful.cn/nnews/6709.htm
- http://m.wap.fcful.cn/nnews/04248.htm
- http://m.wap.fcful.cn/nnews/41002.htm
- http://m.wap.fcful.cn/nnews/6723412.htm
- http://m.wap.fcful.cn/nnews/5831.htm
- http://m.wap.fcful.cn/nnews/47008.htm
- http://m.wap.fcful.cn/nnews/10770.htm
- http://m.wap.fcful.cn/nnews/4353.htm
- http://m.wap.fcful.cn/nnews/88700.htm
- http://m.wap.fcful.cn/nnews/0788394.htm
- http://m.wap.fcful.cn/nnews/6078939.htm
- http://m.wap.fcful.cn/nnews/9735.htm
- http://m.wap.fcful.cn/nnews/27264.htm
- http://m.wap.fcful.cn/nnews/8827.htm
- http://m.wap.fcful.cn/nnews/63611.htm
- http://m.wap.fcful.cn/nnews/457335.htm
- http://m.wap.fcful.cn/nnews/614980.htm
- http://m.wap.fcful.cn/nnews/41894.htm
- http://m.wap.fcful.cn/nnews/7839219.htm
- http://m.wap.fcful.cn/nnews/2675330.htm
- http://m.wap.fcful.cn/nnews/5099005.htm
- http://m.wap.fcful.cn/nnews/5969.htm
- http://m.wap.fcful.cn/nnews/563491.htm
- http://m.wap.fcful.cn/nnews/2235.htm
- http://m.wap.fcful.cn/nnews/07653.htm
- http://m.wap.fcful.cn/nnews/17093.htm
- http://m.wap.fcful.cn/nnews/5614879.htm
- http://m.wap.fcful.cn/nnews/4078469.htm
- http://m.wap.fcful.cn/nnews/0934.htm
- http://m.wap.fcful.cn/nnews/1808.htm
- http://m.wap.fcful.cn/nnews/702571.htm
- http://m.wap.fcful.cn/nnews/0032.htm
- http://m.wap.fcful.cn/nnews/456370.htm
- http://m.wap.fcful.cn/nnews/4595388.htm
- http://m.wap.fcful.cn/nnews/31044.htm
- http://m.wap.fcful.cn/nnews/05375.htm
- http://m.wap.fcful.cn/nnews/3034.htm
- http://m.wap.fcful.cn/nnews/886011.htm
- http://m.wap.fcful.cn/nnews/8266529.htm
- http://m.wap.fcful.cn/nnews/0329.htm
- http://m.wap.fcful.cn/nnews/91266.htm
- http://m.wap.fcful.cn/nnews/6507764.htm
- http://m.wap.fcful.cn/nnews/70687.htm
- http://m.wap.fcful.cn/nnews/3131959.htm
- http://m.wap.fcful.cn/nnews/8505818.htm
- http://m.wap.fcful.cn/nnews/52054.htm
- http://m.wap.fcful.cn/nnews/19155.htm
- http://m.wap.fcful.cn/nnews/6238.htm
- http://m.wap.fcful.cn/nnews/065253.htm
- http://m.wap.fcful.cn/nnews/60936.htm
- http://m.wap.fcful.cn/nnews/5485.htm
- http://m.wap.fcful.cn/nnews/141738.htm
- http://m.wap.fcful.cn/nnews/73378.htm
- http://m.wap.fcful.cn/nnews/96331.htm
- http://m.wap.fcful.cn/nnews/60882.htm
- http://m.wap.fcful.cn/nnews/9261163.htm
- http://m.wap.fcful.cn/nnews/8816886.htm
- http://m.wap.fcful.cn/nnews/2644.htm
- http://m.wap.fcful.cn/nnews/295976.htm
- http://m.wap.fcful.cn/nnews/42855.htm
- http://m.wap.fcful.cn/nnews/0130.htm
- http://m.wap.fcful.cn/nnews/3751313.htm
- http://m.wap.fcful.cn/nnews/19021.htm
- http://m.wap.fcful.cn/nnews/8029.htm
- http://m.wap.fcful.cn/nnews/12635.htm
- http://m.wap.fcful.cn/nnews/1493584.htm
- http://m.wap.fcful.cn/nnews/5595.htm
- http://m.wap.fcful.cn/nnews/9084694.htm
- http://m.wap.fcful.cn/nnews/0033862.htm
- http://m.wap.fcful.cn/nnews/748585.htm
- http://m.wap.fcful.cn/nnews/00708.htm
- http://m.wap.fcful.cn/nnews/54624.htm
- http://m.wap.fcful.cn/nnews/9728524.htm
- http://m.wap.fcful.cn/nnews/0131.htm
- http://m.wap.fcful.cn/nnews/52326.htm
- http://m.wap.fcful.cn/nnews/568476.htm
- http://m.wap.fcful.cn/nnews/6516.htm
- http://m.wap.fcful.cn/nnews/5939.htm
- http://m.wap.fcful.cn/nnews/39451.htm
- http://m.wap.fcful.cn/nnews/950439.htm
- http://m.wap.fcful.cn/nnews/0104.htm
- http://m.wap.fcful.cn/nnews/045379.htm
- http://m.wap.fcful.cn/nnews/8708.htm
- http://m.wap.fcful.cn/nnews/26344.htm
- http://m.wap.fcful.cn/nnews/650845.htm
- http://m.wap.fcful.cn/nnews/8089857.htm
- http://m.wap.fcful.cn/nnews/4805886.htm
- http://m.wap.fcful.cn/nnews/835907.htm
- http://m.wap.fcful.cn/nnews/05357.htm
- http://m.wap.fcful.cn/nnews/5580568.htm
- http://m.wap.fcful.cn/nnews/40912.htm
- http://m.wap.fcful.cn/nnews/3821.htm
- http://m.wap.fcful.cn/nnews/4893.htm
- http://m.wap.fcful.cn/nnews/0664.htm
- http://m.wap.fcful.cn/nnews/060007.htm
- http://m.wap.fcful.cn/nnews/946166.htm
- http://m.wap.fcful.cn/nnews/155860.htm
- http://m.wap.fcful.cn/nnews/01270.htm
- http://m.wap.fcful.cn/nnews/742660.htm
- http://m.wap.fcful.cn/nnews/8291809.htm
- http://m.wap.fcful.cn/nnews/98669.htm
- http://m.wap.fcful.cn/nnews/141856.htm
- http://m.wap.fcful.cn/nnews/80968.htm
- http://m.wap.fcful.cn/nnews/694975.htm
- http://m.wap.fcful.cn/nnews/5744.htm
- http://m.wap.fcful.cn/nnews/847349.htm
- http://m.wap.fcful.cn/nnews/724309.htm
- http://m.wap.fcful.cn/nnews/538818.htm
- http://m.wap.fcful.cn/nnews/4663760.htm
- http://m.wap.fcful.cn/nnews/19265.htm
- http://m.wap.fcful.cn/nnews/3795.htm
- http://m.wap.fcful.cn/nnews/4084.htm
- http://m.wap.fcful.cn/nnews/1929477.htm
- http://m.wap.fcful.cn/nnews/630564.htm
- http://m.wap.fcful.cn/nnews/365155.htm
- http://m.wap.fcful.cn/nnews/1347.htm
- http://m.wap.fcful.cn/nnews/1503449.htm
- http://m.wap.fcful.cn/nnews/55534.htm
- http://m.wap.fcful.cn/nnews/554505.htm
- http://m.wap.fcful.cn/nnews/81082.htm
- http://m.wap.fcful.cn/nnews/3420572.htm
- http://m.wap.fcful.cn/nnews/717473.htm
- http://m.wap.fcful.cn/nnews/5835.htm
- http://m.wap.fcful.cn/nnews/7195217.htm
- http://m.wap.fcful.cn/nnews/7342909.htm
- http://m.wap.fcful.cn/nnews/6125.htm
- http://m.wap.fcful.cn/nnews/70128.htm
- http://m.wap.fcful.cn/nnews/4362.htm
- http://m.wap.fcful.cn/nnews/25752.htm
- http://m.wap.fcful.cn/nnews/2236121.htm
- http://m.wap.fcful.cn/nnews/35680.htm
- http://m.wap.fcful.cn/nnews/207805.htm
- http://m.wap.fcful.cn/nnews/3306.htm
- http://m.wap.fcful.cn/nnews/66241.htm

## 项目结构

```
wapnav/
├── wapnav.py                 # 主入口程序，整合 CLI 与核心调度逻辑
├── config.example.yaml        # 示例配置文件，含日志级别、并发数、存储路径等
├── requirements.txt           # Python 依赖清单，固定版本号以保证可复现构建
├── data/
│   ├── urls.db               # SQLite 资源索引库，存储所有链接与元数据
│   ├── imports/              # 存放历史导入的原始文件副本，用于追溯
│   └── logs/                 # 按日期滚动的运行日志，记录操作与异常
├── src/
│   ├── core/                 # 核心业务模块
│   │   ├── fetcher.py        # 异步 HTTP 探测与页面获取实现
│   │   ├── parser.py         # HTML 元数据提取与清洗逻辑
│   │   ├── storage.py        # 数据库增删改查接口与事务管理
│   │   └── validator.py      # URL 语法校验与规范化工具函数
│   ├── cli/                  # 命令行子命令模块
│   │   ├── import_cmd.py     # 导入链接及标签绑定命令
│   │   ├── check_cmd.py      # 健康检查执行与报告生成命令
│   │   ├── export_cmd.py     # 导出为 JSON/CSV/文本命令
│   │   └── serve_cmd.py      # 启动内置简易 Web 服务用于浏览
│   ├── plugins/              # 插件接口与官方扩展
│   │   ├── notifier.py       # 异常链接邮件/Webhook 通知插件
│   │   └── dedupe.py         # 基于模糊匹配的重复链接检测扩展
│   └── utils/                # 通用工具函数集
│       ├── time_utils.py     # 时间格式化与时区转换
│       ├── file_utils.py     # 文件读写与目录初始化辅助
│       └── network_utils.py  # 代理配置与重试策略实现
├── tests/                    # 单元测试与集成测试用例
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── test_storage.py
├── docs/                     # 完整文档源文件（Markdown 格式）
├── scripts/                  # 运维辅助脚本，如定时任务模板、数据迁移工具
├── Dockerfile                # 基于 Python 3.10-slim 的多阶段构建文件
└── LICENSE                   # MIT 许可证文本
```

## 贡献指南

欢迎社区开发者提交问题报告、功能建议或代码贡献。请遵循以下流程以确保协作顺畅：

1. 查阅 issue 列表与 project board，确认当前版本路线图，避免重复工作。新功能建议请先通过 issue 讨论获得初步共识后再行实现。

2. 派生仓库至个人账号，在本地 dev 分支上开发。代码风格遵循 PEP 8 规范，提交前执行 pre-commit 钩子进行基础格式检查。

3. 编写或更新对应的单元测试用例，确保新增代码的测试覆盖率不低于 80%。所有测试须在本地 Python 3.8、3.9、3.10 环境下均通过。

4. 提交 Pull Request 至 main 分支，PR 标题使用约定式提交格式（如 feat: 或 fix:），描述中清楚说明改动动机、实现方案及影响范围。

5. 文档更新同步：涉及用户可见的功能变动时，需同时更新 docs/ 下对应的手册章节，并确保示例代码片段可执行。

## 常见问题

Q: 导入大量 URL 时出现超时或内存占用过高怎么办？

A: 可在 config.yaml 中调整 fetcher.batch_size 参数降低并发批次大小，默认 50 条/批。同时可增大 fetcher.timeout 值至 30 秒以上以应对网络延迟较高的站点。若内存受限，建议使用 sqlite3 而非内存模式运行。

Q: 健康检查报告中的状态码 0 表示什么？

A: 状态码 0 表示请求未能完成，通常原因为 DNS 解析失败、连接被拒绝或 SSL 证书验证错误。可检查网络代理配置或目标站点是否支持 HTTP 协议访问。部分移动端页面可能仅支持 HTTPS，但本系统按原始协议发起请求，若需升级协议可在 fetcher 中配置 allow_redirects 跟踪。

Q: 如何迁移资源库到另一台服务器？

A: 直接将 data/urls.db 文件复制至新服务器的对应 data/ 目录下即可。若需同时迁移配置文件与日志，建议整体拷贝 data/ 与 config.yaml。迁移后执行 wapnav.py check --all 验证所有链接在新环境中的可达性。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
