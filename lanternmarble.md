# LinkMaster Pro

LinkMaster Pro 是一个面向技术内容聚合与外部链接治理的开源工具集，旨在帮助开发团队、内容运营者及技术文档维护者系统化地管理、校验和归档大规模外部 URL 资源。该项目定位于中大型开源项目文档站、企业技术博客聚合页以及知识库链接资产的维护场景，解决人工管理海量链接时存在的重复劳动、链接失效、格式混乱与可追溯性缺失等核心问题。

LinkMaster Pro 不依赖特定前端框架，以纯脚本和结构化数据驱动，提供链接批量导入、元信息抓取、健康状态巡检以及 Markdown 格式输出等全链路能力，适用于批次链接数量超过 200 条的规模化资源管理任务。当前版本针对第 164/240 批共 250 个资源链接提供完整处理模板。

## 功能概览

批量链接导入解析 支持从纯文本、CSV 及 JSON Lines 格式读取原始 URL 列表，自动识别协议头与域名结构，对裸域名自动补齐标准化占位标记。

链接健康状态巡检 对每条 URL 执行 GET 请求超时检测与状态码校验，输出可达性报告，标记 4xx/5xx 异常链接，并记录响应时间。

元数据智能抓取 从目标页面提取标题、meta description 与 content-type，生成资源摘要表，辅助人工判断链接内容相关性。

结构化输出生成 将处理后的链接数据按指定章节格式渲染为 Markdown 列表、表格或 JSON 导出文件，支持自定义模板字段映射。

批次管理与历史追踪 内置批次编号机制（如 164/240），记录每批资源的导入时间、校验状态与变更日志，支持多批次增量合并。

去重与规范校验 对 URL 进行去重检测，自动识别大小写差异、尾部斜杠及协议变体（http/https），并给出规范化建议。

插件式扩展接口 提供 Python 钩子函数，允许开发者自定义链接预处理规则（如过滤特定域名、添加 UTM 参数）或对接第三方安全检测 API。

命令行交互与配置文件 支持通过 CLI 参数传入输入文件路径、输出目录及并发数，同时支持 YAML 配置文件持久化常用运行参数。

## 应用场景

开源项目文档站链接资产盘点 当开源项目文档包含数百个外部引用链接（如 API 参考、社区教程、依赖仓库）时，使用 LinkMaster Pro 定期扫描所有链接，自动生成健康报告，帮助维护者快速修复失效引用，提升文档可靠性。

企业技术博客聚合页运维 技术团队每月发布多篇博客并附带外部资源推荐，运营人员利用本工具将新批次链接导入系统，自动提取每个链接的标题与摘要，统一生成格式规范的资源推荐列表，减少手动复制粘贴错误。

知识库迁移前的链接审计 在将旧版 Confluence 或 Wiki 内容迁移至新平台前，使用 LinkMaster Pro 对所有历史遗留外部链接进行可达性与安全性检查，筛选出高危域名或过期站点，保障迁移后知识库的访问质量。

第三方依赖镜像站监控 内部镜像站维护团队通过本工具定时监控上游仓库发布页的下载链接，当检测到链接状态异常时触发告警，提前规避构建流水线因外部资源不可用而失败的风险。

## 快速开始

以下步骤演示如何使用 LinkMaster Pro 处理一批 URL 列表并生成标准 Markdown 资源清单。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/linkmaster-pro.git
cd linkmaster-pro

# 安装依赖（建议使用 Python 3.9+ 虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 请使用 venv\Scripts\activate
pip install -r requirements.txt

# 准备输入文件 urls.txt，每行一个 URL，然后运行处理命令
python linkmaster.py process --input urls.txt --batch 164/240 --output ./output
```

执行完毕后，输出目录将包含 `resource_list.md`、`health_report.json` 和 `metadata_cache.db` 三个文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，类型注解依赖 3.9+ 语法 |
| requests | 2.28.0 及以上 | 发送 HTTP 请求，用于链接健康检查与元数据抓取 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 页面，提取 title 与 meta 标签内容 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析器后端，提供高性能 HTML 解析 |
| click | 8.1.0 及以上 | 构建命令行交互界面，支持子命令与参数解析 |
| pyyaml | 6.0 及以上 | 读取 YAML 格式的配置文件，支持复杂参数结构化定义 |
| pytest | 7.2.0 及以上 | 仅开发依赖，用于单元测试与集成测试执行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/usage.md | 如何安装、配置参数、执行批量处理以及解读输出报告 |
| 配置参考 | docs/config.md | YAML 配置文件中每个字段的含义、默认值及可选范围 |
| 插件开发 | docs/plugins.md | 如何编写自定义钩子函数，扩展链接预处理或后处理逻辑 |
| API 接口 | docs/api.md | 核心模块的类与方法签名，供二次开发或脚本化调用参考 |
| 常见任务 | docs/recipes.md | 针对特定场景（如镜像站监控、文档站审计）的操作范例 |
| 变更日志 | CHANGELOG.md | 每个版本的更新摘要、兼容性变更与已修复问题列表 |

## 资源列表

- http://m.wap.gqskj.cn/snews/2016485.htm
- http://m.wap.gqskj.cn/snews/765669.htm
- http://m.wap.gqskj.cn/snews/1643.htm
- http://m.wap.gqskj.cn/snews/1103957.htm
- http://m.wap.gqskj.cn/snews/7543592.htm
- http://m.wap.gqskj.cn/snews/9797976.htm
- http://m.wap.gqskj.cn/snews/9678030.htm
- http://m.wap.gqskj.cn/snews/938038.htm
- http://m.wap.gqskj.cn/snews/2216.htm
- http://m.wap.gqskj.cn/snews/68303.htm
- http://m.wap.gqskj.cn/snews/272693.htm
- http://m.wap.gqskj.cn/snews/06868.htm
- http://m.wap.gqskj.cn/snews/4657.htm
- http://m.wap.gqskj.cn/snews/8487291.htm
- http://m.wap.gqskj.cn/snews/7087271.htm
- http://m.wap.gqskj.cn/snews/9457966.htm
- http://m.wap.gqskj.cn/snews/6274.htm
- http://m.wap.gqskj.cn/snews/038054.htm
- http://m.wap.gqskj.cn/snews/847258.htm
- http://m.wap.gqskj.cn/snews/17978.htm
- http://m.wap.gqskj.cn/snews/7627810.htm
- http://m.wap.gqskj.cn/snews/2217486.htm
- http://m.wap.gqskj.cn/snews/6648.htm
- http://m.wap.gqskj.cn/snews/0703.htm
- http://m.wap.gqskj.cn/snews/19172.htm
- http://m.wap.gqskj.cn/snews/711312.htm
- http://m.wap.gqskj.cn/snews/821714.htm
- http://m.wap.gqskj.cn/snews/7875.htm
- http://m.wap.gqskj.cn/snews/4340275.htm
- http://m.wap.gqskj.cn/snews/72542.htm
- http://m.wap.gqskj.cn/snews/1728.htm
- http://m.wap.gqskj.cn/snews/51937.htm
- http://m.wap.gqskj.cn/snews/2515442.htm
- http://m.wap.gqskj.cn/snews/054437.htm
- http://m.wap.gqskj.cn/snews/71203.htm
- http://m.wap.gqskj.cn/snews/3188933.htm
- http://m.wap.gqskj.cn/snews/22552.htm
- http://m.wap.gqskj.cn/snews/225931.htm
- http://m.wap.gqskj.cn/snews/8369373.htm
- http://m.wap.gqskj.cn/snews/084227.htm
- http://m.wap.gqskj.cn/snews/4569.htm
- http://m.wap.gqskj.cn/snews/1949763.htm
- http://m.wap.gqskj.cn/snews/216151.htm
- http://m.wap.gqskj.cn/snews/7904.htm
- http://m.wap.gqskj.cn/snews/536527.htm
- http://m.wap.gqskj.cn/snews/8050253.htm
- http://m.wap.gqskj.cn/snews/216157.htm
- http://m.wap.gqskj.cn/snews/6430220.htm
- http://m.wap.gqskj.cn/snews/9853607.htm
- http://m.wap.gqskj.cn/snews/37335.htm
- http://m.wap.gqskj.cn/snews/0673171.htm
- http://m.wap.gqskj.cn/snews/963179.htm
- http://m.wap.gqskj.cn/snews/300250.htm
- http://m.wap.gqskj.cn/snews/3743295.htm
- http://m.wap.gqskj.cn/snews/9267.htm
- http://m.wap.gqskj.cn/snews/8506.htm
- http://m.wap.gqskj.cn/snews/43922.htm
- http://m.wap.gqskj.cn/snews/35423.htm
- http://m.wap.gqskj.cn/snews/147302.htm
- http://m.wap.gqskj.cn/snews/97675.htm
- http://m.wap.gqskj.cn/snews/45982.htm
- http://m.wap.gqskj.cn/snews/4228.htm
- http://m.wap.gqskj.cn/snews/417555.htm
- http://m.wap.gqskj.cn/snews/56891.htm
- http://m.wap.gqskj.cn/snews/853895.htm
- http://m.wap.gqskj.cn/snews/66116.htm
- http://m.wap.gqskj.cn/snews/834595.htm
- http://m.wap.gqskj.cn/snews/968517.htm
- http://m.wap.gqskj.cn/snews/9604386.htm
- http://m.wap.gqskj.cn/snews/356215.htm
- http://m.wap.gqskj.cn/snews/289157.htm
- http://m.wap.gqskj.cn/snews/3352904.htm
- http://m.wap.gqskj.cn/snews/7287017.htm
- http://m.wap.gqskj.cn/snews/592179.htm
- http://m.wap.gqskj.cn/snews/4942.htm
- http://m.wap.gqskj.cn/snews/55783.htm
- http://m.wap.gqskj.cn/snews/96158.htm
- http://m.wap.gqskj.cn/snews/176328.htm
- http://m.wap.gqskj.cn/snews/383793.htm
- http://m.wap.gqskj.cn/snews/78009.htm
- http://m.wap.gqskj.cn/snews/0691520.htm
- http://m.wap.gqskj.cn/snews/040130.htm
- http://m.wap.gqskj.cn/snews/6457558.htm
- http://m.wap.gqskj.cn/snews/8663089.htm
- http://m.wap.gqskj.cn/snews/8272483.htm
- http://m.wap.gqskj.cn/snews/612535.htm
- http://m.wap.gqskj.cn/snews/30600.htm
- http://m.wap.gqskj.cn/snews/8816.htm
- http://m.wap.gqskj.cn/snews/626313.htm
- http://m.wap.gqskj.cn/snews/352659.htm
- http://m.wap.gqskj.cn/snews/5196595.htm
- http://m.wap.gqskj.cn/snews/625257.htm
- http://m.wap.gqskj.cn/snews/0306.htm
- http://m.wap.gqskj.cn/snews/6712.htm
- http://m.wap.gqskj.cn/snews/26977.htm
- http://m.wap.gqskj.cn/snews/337004.htm
- http://m.wap.gqskj.cn/snews/17465.htm
- http://m.wap.gqskj.cn/snews/5711374.htm
- http://m.wap.gqskj.cn/snews/8545.htm
- http://m.wap.gqskj.cn/snews/0992040.htm
- http://m.wap.gqskj.cn/snews/2457107.htm
- http://m.wap.gqskj.cn/snews/21200.htm
- http://m.wap.gqskj.cn/snews/13152.htm
- http://m.wap.gqskj.cn/snews/4142.htm
- http://m.wap.gqskj.cn/snews/76475.htm
- http://m.wap.gqskj.cn/snews/55065.htm
- http://m.wap.gqskj.cn/snews/32450.htm
- http://m.wap.gqskj.cn/snews/873711.htm
- http://m.wap.gqskj.cn/snews/390145.htm
- http://m.wap.gqskj.cn/snews/67134.htm
- http://m.wap.gqskj.cn/snews/969703.htm
- http://m.wap.gqskj.cn/snews/3455.htm
- http://m.wap.gqskj.cn/snews/0513.htm
- http://m.wap.gqskj.cn/snews/49183.htm
- http://m.wap.gqskj.cn/snews/9577741.htm
- http://m.wap.gqskj.cn/snews/9708.htm
- http://m.wap.gqskj.cn/snews/73378.htm
- http://m.wap.gqskj.cn/snews/805591.htm
- http://m.wap.gqskj.cn/snews/2563.htm
- http://m.wap.gqskj.cn/snews/2627543.htm
- http://m.wap.gqskj.cn/snews/8845337.htm
- http://m.wap.gqskj.cn/snews/87489.htm
- http://m.wap.gqskj.cn/snews/691149.htm
- http://m.wap.gqskj.cn/snews/4055.htm
- http://m.wap.gqskj.cn/snews/90028.htm
- http://m.wap.gqskj.cn/snews/9218.htm
- http://m.wap.gqskj.cn/snews/689402.htm
- http://m.wap.gqskj.cn/snews/6151800.htm
- http://m.wap.gqskj.cn/snews/78796.htm
- http://m.wap.gqskj.cn/snews/673297.htm
- http://m.wap.gqskj.cn/snews/7081.htm
- http://m.wap.gqskj.cn/snews/52691.htm
- http://m.wap.gqskj.cn/snews/56171.htm
- http://m.wap.gqskj.cn/snews/0406319.htm
- http://m.wap.gqskj.cn/snews/42494.htm
- http://m.wap.gqskj.cn/snews/3202308.htm
- http://m.wap.gqskj.cn/snews/7215.htm
- http://m.wap.gqskj.cn/snews/56166.htm
- http://m.wap.gqskj.cn/snews/05836.htm
- http://m.wap.gqskj.cn/snews/8402122.htm
- http://m.wap.gqskj.cn/snews/674104.htm
- http://m.wap.gqskj.cn/snews/3012.htm
- http://m.wap.gqskj.cn/snews/332264.htm
- http://m.wap.gqskj.cn/snews/0449.htm
- http://m.wap.gqskj.cn/snews/3979314.htm
- http://m.wap.gqskj.cn/snews/27184.htm
- http://m.wap.gqskj.cn/snews/9253055.htm
- http://m.wap.gqskj.cn/snews/931983.htm
- http://m.wap.gqskj.cn/snews/585445.htm
- http://m.wap.gqskj.cn/snews/2594679.htm
- http://m.wap.gqskj.cn/snews/9552.htm
- http://m.wap.gqskj.cn/snews/8860636.htm
- http://m.wap.gqskj.cn/snews/1794968.htm
- http://m.wap.gqskj.cn/snews/69665.htm
- http://m.wap.gqskj.cn/snews/0670809.htm
- http://m.wap.gqskj.cn/snews/13023.htm
- http://m.wap.gqskj.cn/snews/38026.htm
- http://m.wap.gqskj.cn/snews/554418.htm
- http://m.wap.gqskj.cn/snews/16993.htm
- http://m.wap.gqskj.cn/snews/907389.htm
- http://m.wap.gqskj.cn/snews/8802241.htm
- http://m.wap.gqskj.cn/snews/59789.htm
- http://m.wap.gqskj.cn/snews/45192.htm
- http://m.wap.gqskj.cn/snews/03719.htm
- http://m.wap.gqskj.cn/snews/66127.htm
- http://m.wap.gqskj.cn/snews/58507.htm
- http://m.wap.gqskj.cn/snews/384786.htm
- http://m.wap.gqskj.cn/snews/103122.htm
- http://m.wap.gqskj.cn/snews/86871.htm
- http://m.wap.gqskj.cn/snews/276278.htm
- http://m.wap.gqskj.cn/snews/495154.htm
- http://m.wap.gqskj.cn/snews/0327.htm
- http://m.wap.gqskj.cn/snews/14553.htm
- http://m.wap.gqskj.cn/snews/82377.htm
- http://m.wap.gqskj.cn/snews/188512.htm
- http://m.wap.gqskj.cn/snews/0827.htm
- http://m.wap.gqskj.cn/snews/9261724.htm
- http://m.wap.gqskj.cn/snews/0810078.htm
- http://m.wap.gqskj.cn/snews/8588.htm
- http://m.wap.gqskj.cn/snews/778753.htm
- http://m.wap.gqskj.cn/snews/594083.htm
- http://m.wap.gqskj.cn/snews/900367.htm
- http://m.wap.gqskj.cn/snews/8632689.htm
- http://m.wap.gqskj.cn/snews/7058.htm
- http://m.wap.gqskj.cn/snews/3179989.htm
- http://m.wap.gqskj.cn/snews/0594233.htm
- http://m.wap.gqskj.cn/snews/2355766.htm
- http://m.wap.gqskj.cn/snews/3738110.htm
- http://m.wap.gqskj.cn/snews/5876.htm
- http://m.wap.gqskj.cn/snews/3531.htm
- http://m.wap.gqskj.cn/snews/2124.htm
- http://m.wap.gqskj.cn/snews/2827.htm
- http://m.wap.gqskj.cn/snews/15059.htm
- http://m.wap.gqskj.cn/snews/65986.htm
- http://m.wap.gqskj.cn/snews/3966797.htm
- http://m.wap.gqskj.cn/snews/3868.htm
- http://m.wap.gqskj.cn/snews/4954.htm
- http://m.wap.gqskj.cn/snews/527925.htm
- http://m.wap.gqskj.cn/snews/5239.htm
- http://m.wap.gqskj.cn/snews/8926.htm
- http://m.wap.gqskj.cn/snews/539742.htm
- http://m.wap.gqskj.cn/snews/3948070.htm
- http://m.wap.gqskj.cn/snews/2167788.htm
- http://m.wap.gqskj.cn/snews/1209.htm
- http://m.wap.gqskj.cn/snews/9043.htm
- http://m.wap.gqskj.cn/snews/1090.htm
- http://m.wap.gqskj.cn/snews/08304.htm
- http://m.wap.gqskj.cn/snews/07161.htm
- http://m.wap.gqskj.cn/snews/3670.htm
- http://m.wap.gqskj.cn/snews/4554071.htm
- http://m.wap.gqskj.cn/snews/10666.htm
- http://m.wap.gqskj.cn/snews/719188.htm
- http://m.wap.gqskj.cn/snews/258328.htm
- http://m.wap.gqskj.cn/snews/25555.htm
- http://m.wap.gqskj.cn/snews/0901093.htm
- http://m.wap.gqskj.cn/snews/854334.htm
- http://m.wap.gqskj.cn/snews/708541.htm
- http://m.wap.gqskj.cn/snews/9873991.htm
- http://m.wap.gqskj.cn/snews/0767567.htm
- http://m.wap.gqskj.cn/snews/25344.htm
- http://m.wap.gqskj.cn/snews/1621.htm
- http://m.wap.gqskj.cn/snews/1428731.htm
- http://m.wap.gqskj.cn/snews/4665.htm
- http://m.wap.gqskj.cn/snews/53091.htm
- http://m.wap.gqskj.cn/snews/336505.htm
- http://m.wap.gqskj.cn/snews/1724.htm
- http://m.wap.gqskj.cn/snews/166228.htm
- http://m.wap.gqskj.cn/snews/8667239.htm
- http://m.wap.gqskj.cn/snews/3207.htm
- http://m.wap.gqskj.cn/snews/40418.htm
- http://m.wap.gqskj.cn/snews/3395.htm
- http://m.wap.gqskj.cn/snews/4762914.htm
- http://m.wap.gqskj.cn/snews/0413.htm
- http://m.wap.gqskj.cn/snews/1171.htm
- http://m.wap.gqskj.cn/snews/4475.htm
- http://m.wap.gqskj.cn/snews/426218.htm
- http://m.wap.gqskj.cn/snews/966430.htm
- http://m.wap.gqskj.cn/snews/0924.htm
- http://m.wap.gqskj.cn/snews/97049.htm
- http://m.wap.gqskj.cn/snews/723066.htm
- http://m.wap.gqskj.cn/snews/1136.htm
- http://m.wap.gqskj.cn/snews/9576851.htm
- http://m.wap.gqskj.cn/snews/406226.htm
- http://m.wap.gqskj.cn/snews/811738.htm
- http://m.wap.gqskj.cn/snews/6864.htm
- http://m.wap.gqskj.cn/snews/3642809.htm
- http://m.wap.gqskj.cn/snews/2531.htm
- http://m.wap.gqskj.cn/snews/5670659.htm
- http://m.wap.gqskj.cn/snews/39252.htm
- http://m.wap.gqskj.cn/snews/91594.htm

## 项目结构

```
linkmaster-pro/
├── linkmaster.py                # 命令行入口，注册 click 子命令，解析 argv 并调度核心流程
├── requirements.txt             # 生产环境依赖列表，固定版本号以保证可复现安装
├── setup.py                     # 打包与分发配置，定义 entry_points 控制台脚本
├── config/
│   ├── default.yaml             # 默认配置模板，包含超时阈值、并发数、输出格式等
│   └── schema.json              # 配置文件 JSON Schema，用于 IDE 补全与校验
├── src/
│   ├── __init__.py              # 包初始化，暴露核心类 LinkProcessor 与 BatchManager
│   ├── parser.py                # 输入解析模块，支持 txt / csv / jsonl 格式读取
│   ├── checker.py               # 健康检查模块，实现异步 HTTP 请求与状态码统计
│   ├── metadata.py              # 元数据抓取模块，使用 beautifulsoup4 提取页面信息
│   ├── renderer.py              # 输出渲染模块，生成 Markdown / JSON / HTML 格式报告
│   ├── dedup.py                 # 去重与规范化模块，处理大小写、斜杠与协议变体
│   └── hooks.py                 # 插件钩子定义，提供预处理与后处理扩展点
├── tests/
│   ├── unit/                    # 单元测试目录，按模块拆分 test_parser.py 等
│   ├── integration/             # 集成测试目录，测试端到端命令行流程
│   └── fixtures/                # 测试固定数据，包含样例 urls.txt 与预期输出
├── docs/
│   ├── usage.md                 # 用户手册，涵盖安装、基础用法与常见参数
│   ├── config.md                # 完整配置参考，逐项说明所有 YAML 字段
│   ├── plugins.md               # 插件开发指南，包含钩子签名与注册方式
│   ├── api.md                   # API 文档，由 docstring 自动生成
│   └── recipes.md               # 场景化操作范例，包含镜像站监控与文档审计示例
├── output/                      # 默认输出目录，存放生成的报告与缓存文件（被 .gitignore 忽略）
├── logs/                        # 日志存储目录，按日期滚动记录运行日志
└── .github/
    └── workflows/
        └── ci.yml               # GitHub Actions CI 配置，每次提交执行测试与 lint 检查
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 访问 GitHub Issues 页面，选择对应模板填写，缺陷报告需附上可复现的输入文件片段、运行命令及完整错误堆栈，功能请求需说明使用场景与预期行为变化。

Fork 仓库并创建功能分支 从主分支 checkout 出新分支，命名规范为 `feature/简短描述` 或 `fix/问题编号`，确保分支基于最新 main 分支代码。

编写单元测试覆盖新增或修改逻辑 在 `tests/unit/` 下对应模块文件中追加测试用例，使用 pytest 断言，确保所有测试通过且覆盖率不低于 90%。

提交 Pull Request 并关联 Issue 推送分支后创建 PR，描述中写明变更目的、实现方式及测试结果，至少邀请一位维护者评审，根据反馈意见修改直至合并。

遵守代码风格与提交规范 使用 Black 格式化 Python 代码，isort 管理导入顺序，commit message 遵循 Conventional Commits 格式（如 feat: 添加链接去重缓存机制）。

## 常见问题

Q: 处理大量链接时出现超时或连接错误，如何调整并发参数？
A: 可在命令行使用 `--concurrency 5` 降低并发数，或在配置文件中修改 `checker.concurrency` 字段。默认并发为 20，若目标服务器有访问频率限制，建议降至 5 至 10 之间。同时可调整 `checker.timeout` 增加单次请求等待时间，默认 10 秒。

Q: 工具能否识别和跳过已失效的重复链接？
A: 可以。LinkMaster Pro 内置去重模块，会基于完整 URL 字符串及规范化后的形式（移除尾部斜杠、统一协议为 http）进行双重去重。去重记录会保存在 `output/dedup_cache.json` 中，跨批次持久化，避免重复检查已知失效链接。

Q: 如何将处理结果集成到现有的 CI/CD 流水线中？
A: 推荐使用命令行非交互模式，通过 `--output-format json` 生成结构化报告，然后由下游脚本解析 JSON 中的 `unreachable` 列表。若链接不可用率超过阈值（如 5%），可通过 shell 判断退出码触发流水线告警。工具提供了 `--exit-on-unreachable` 参数，当存在不可达链接时返回非零退出码。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
