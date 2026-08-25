# XNews Resource Aggregator

XNews Resource Aggregator 是一个面向技术信息采集与新闻聚合场景的开源外链管理工具，定位于对大量离散新闻条目进行批量导入、结构化存储与分类导航。该项目主要服务于个人开发者、内容运营团队以及小型新闻聚合站点，用于解决海量 URL 的手动整理效率低下、缺乏版本追踪以及难以快速回溯特定条目等问题。通过提供统一的条目索引机制与轻量级元数据管理能力，本项目能够将原始新闻链接转化为可检索、可归档、可审计的结构化资源库，降低信息碎片化带来的维护成本。

## 功能概览

批量导入与解析 支持以文本列表或 CSV 格式批量导入新闻 URL，自动提取 ID 与来源域名，生成内部唯一标识。

条目元数据补全 对每条导入链接自动补全采集时间、条目状态（未读/已读/已归档）以及基础校验状态。

多级标签分类 允许用户为每个条目附加一个或多个自定义标签，支持按标签组合进行快速筛选与统计。

全文检索与过滤 基于条目 ID、标题关键词或时间范围进行检索，支持正则表达式过滤模式。

外部链接可用性检测 内置异步 HTTP 探测模块，定时检测目标链接的可访问性，标记失效链接并生成报告。

数据导入导出 支持 JSON、CSV 与 Markdown 表格格式的导出，便于与其他数据处理工具集成。

审计日志记录 记录每次导入、修改、删除操作的操作者与时间戳，满足小型团队协作场景下的追溯需求。

## 应用场景

个人技术博主的每日新闻归档 独立开发者或技术写作者每日需要浏览大量技术资讯，可利用本项目将分散的新闻链接集中管理，按日期或主题打标，后续撰写周报或月报时可直接检索引用。

内容运营团队的素材池管理 运营团队可从多个信息源批量采集新闻链接，导入后通过标签区分领域（如前端、后端、AI、安全），编辑人员根据标签快速筛选素材，避免重复收集。

小型新闻聚合站的后台数据源维护 聚合站需要定期更新稿件来源列表，使用本项目可统一管理数百个外部链接，通过可用性检测自动剔除失效源，保证前端展示的链接质量。

开源项目文档中的参考资料整理 开源项目维护者可将相关技术讨论、社区公告或版本发布声明等外部链接纳入资源库，便于后续查阅或生成附录。

## 快速开始

```bash
git clone https://github.com/example/xnews-aggregator.git
cd xnews-aggregator
pip install -r requirements.txt
python scripts/import.py --input samples/urls.txt --output data/index.json
```

上述命令完成仓库克隆、依赖安装与示例数据导入。如需启动本地 Web 管理界面，请执行 `python app.py` 并访问 `http://127.0.0.1:5000`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于解析、导入及 Web 服务 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| SQLite | 3.35 及以上 | 本地轻量级数据库，用于存储条目元数据与审计日志 |
| requests | 2.28.0 及以上 | HTTP 客户端库，用于外部链接可用性检测 |
| flask | 2.2.0 及以上 | Web 框架，用于提供管理界面与 REST API（可选） |
| pytest | 7.0 及以上 | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何导入链接、打标签、导出数据以及使用检索功能 |
| 运维参考 | docs/operations.md | 如何配置定时检测任务、备份数据库以及迁移数据 |
| API 文档 | docs/api_reference.md | 如何通过 REST API 进行批量导入、查询和状态更新 |
| 开发指南 | docs/development.md | 如何扩展解析器、添加新的检测策略以及运行测试套件 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/5815.htm
- http://m.3g.gqskj.cn/xnews/37109.htm
- http://m.3g.gqskj.cn/xnews/4530.htm
- http://m.3g.gqskj.cn/xnews/35831.htm
- http://m.3g.gqskj.cn/xnews/959285.htm
- http://m.3g.gqskj.cn/xnews/7094.htm
- http://m.3g.gqskj.cn/xnews/1619506.htm
- http://m.3g.gqskj.cn/xnews/95541.htm
- http://m.3g.gqskj.cn/xnews/28289.htm
- http://m.3g.gqskj.cn/xnews/195649.htm
- http://m.3g.gqskj.cn/xnews/718748.htm
- http://m.3g.gqskj.cn/xnews/971916.htm
- http://m.3g.gqskj.cn/xnews/829879.htm
- http://m.3g.gqskj.cn/xnews/1485438.htm
- http://m.3g.gqskj.cn/xnews/083419.htm
- http://m.3g.gqskj.cn/xnews/0975943.htm
- http://m.3g.gqskj.cn/xnews/5482.htm
- http://m.3g.gqskj.cn/xnews/0634.htm
- http://m.3g.gqskj.cn/xnews/1157.htm
- http://m.3g.gqskj.cn/xnews/6037224.htm
- http://m.3g.gqskj.cn/xnews/401949.htm
- http://m.3g.gqskj.cn/xnews/296280.htm
- http://m.3g.gqskj.cn/xnews/5450.htm
- http://m.3g.gqskj.cn/xnews/1643890.htm
- http://m.3g.gqskj.cn/xnews/922810.htm
- http://m.3g.gqskj.cn/xnews/015093.htm
- http://m.3g.gqskj.cn/xnews/1615462.htm
- http://m.3g.gqskj.cn/xnews/92634.htm
- http://m.3g.gqskj.cn/xnews/168465.htm
- http://m.3g.gqskj.cn/xnews/693842.htm
- http://m.3g.gqskj.cn/xnews/0415888.htm
- http://m.3g.gqskj.cn/xnews/525150.htm
- http://m.3g.gqskj.cn/xnews/4885690.htm
- http://m.3g.gqskj.cn/xnews/92745.htm
- http://m.3g.gqskj.cn/xnews/444805.htm
- http://m.3g.gqskj.cn/xnews/0284537.htm
- http://m.3g.gqskj.cn/xnews/2657449.htm
- http://m.3g.gqskj.cn/xnews/0086293.htm
- http://m.3g.gqskj.cn/xnews/201713.htm
- http://m.3g.gqskj.cn/xnews/7851.htm
- http://m.3g.gqskj.cn/xnews/8105.htm
- http://m.3g.gqskj.cn/xnews/4298983.htm
- http://m.3g.gqskj.cn/xnews/94420.htm
- http://m.3g.gqskj.cn/xnews/1758.htm
- http://m.3g.gqskj.cn/xnews/6336043.htm
- http://m.3g.gqskj.cn/xnews/70721.htm
- http://m.3g.gqskj.cn/xnews/863589.htm
- http://m.3g.gqskj.cn/xnews/4741923.htm
- http://m.3g.gqskj.cn/xnews/05232.htm
- http://m.3g.gqskj.cn/xnews/2329.htm
- http://m.3g.gqskj.cn/xnews/528562.htm
- http://m.3g.gqskj.cn/xnews/385387.htm
- http://m.3g.gqskj.cn/xnews/4191.htm
- http://m.3g.gqskj.cn/xnews/3572.htm
- http://m.3g.gqskj.cn/xnews/28486.htm
- http://m.3g.gqskj.cn/xnews/1841.htm
- http://m.3g.gqskj.cn/xnews/69500.htm
- http://m.3g.gqskj.cn/xnews/4683260.htm
- http://m.3g.gqskj.cn/xnews/49068.htm
- http://m.3g.gqskj.cn/xnews/196010.htm
- http://m.3g.gqskj.cn/xnews/7237.htm
- http://m.3g.gqskj.cn/xnews/5571935.htm
- http://m.3g.gqskj.cn/xnews/522851.htm
- http://m.3g.gqskj.cn/xnews/03830.htm
- http://m.3g.gqskj.cn/xnews/731862.htm
- http://m.3g.gqskj.cn/xnews/0707526.htm
- http://m.3g.gqskj.cn/xnews/24392.htm
- http://m.3g.gqskj.cn/xnews/953669.htm
- http://m.3g.gqskj.cn/xnews/14362.htm
- http://m.3g.gqskj.cn/xnews/64209.htm
- http://m.3g.gqskj.cn/xnews/1467687.htm
- http://m.3g.gqskj.cn/xnews/7166096.htm
- http://m.3g.gqskj.cn/xnews/8318.htm
- http://m.3g.gqskj.cn/xnews/7086.htm
- http://m.3g.gqskj.cn/xnews/7298.htm
- http://m.3g.gqskj.cn/xnews/3188510.htm
- http://m.3g.gqskj.cn/xnews/706136.htm
- http://m.3g.gqskj.cn/xnews/2974.htm
- http://m.3g.gqskj.cn/xnews/569455.htm
- http://m.3g.gqskj.cn/xnews/641109.htm
- http://m.3g.gqskj.cn/xnews/81354.htm
- http://m.3g.gqskj.cn/xnews/899528.htm
- http://m.3g.gqskj.cn/xnews/7513.htm
- http://m.3g.gqskj.cn/xnews/642756.htm
- http://m.3g.gqskj.cn/xnews/22034.htm
- http://m.3g.gqskj.cn/xnews/8268.htm
- http://m.3g.gqskj.cn/xnews/80864.htm
- http://m.3g.gqskj.cn/xnews/5043884.htm
- http://m.3g.gqskj.cn/xnews/3033.htm
- http://m.3g.gqskj.cn/xnews/3475.htm
- http://m.3g.gqskj.cn/xnews/5580922.htm
- http://m.3g.gqskj.cn/xnews/70129.htm
- http://m.3g.gqskj.cn/xnews/7069.htm
- http://m.3g.gqskj.cn/xnews/99767.htm
- http://m.3g.gqskj.cn/xnews/793322.htm
- http://m.3g.gqskj.cn/xnews/1203.htm
- http://m.3g.gqskj.cn/xnews/2890636.htm
- http://m.3g.gqskj.cn/xnews/0079.htm
- http://m.3g.gqskj.cn/xnews/4542.htm
- http://m.3g.gqskj.cn/xnews/2444448.htm
- http://m.3g.gqskj.cn/xnews/5614857.htm
- http://m.3g.gqskj.cn/xnews/55132.htm
- http://m.3g.gqskj.cn/xnews/44894.htm
- http://m.3g.gqskj.cn/xnews/085090.htm
- http://m.3g.gqskj.cn/xnews/1432.htm
- http://m.3g.gqskj.cn/xnews/1725969.htm
- http://m.3g.gqskj.cn/xnews/8954942.htm
- http://m.3g.gqskj.cn/xnews/340416.htm
- http://m.3g.gqskj.cn/xnews/0655504.htm
- http://m.3g.gqskj.cn/xnews/6833054.htm
- http://m.3g.gqskj.cn/xnews/5467.htm
- http://m.3g.gqskj.cn/xnews/67279.htm
- http://m.3g.gqskj.cn/xnews/89782.htm
- http://m.3g.gqskj.cn/xnews/834924.htm
- http://m.3g.gqskj.cn/xnews/313091.htm
- http://m.3g.gqskj.cn/xnews/639028.htm
- http://m.3g.gqskj.cn/xnews/83868.htm
- http://m.3g.gqskj.cn/xnews/8911665.htm
- http://m.3g.gqskj.cn/xnews/51396.htm
- http://m.3g.gqskj.cn/xnews/4643160.htm
- http://m.3g.gqskj.cn/xnews/3268.htm
- http://m.3g.gqskj.cn/xnews/87921.htm
- http://m.3g.gqskj.cn/xnews/6553724.htm
- http://m.3g.gqskj.cn/xnews/7979024.htm
- http://m.3g.gqskj.cn/xnews/1392798.htm
- http://m.3g.gqskj.cn/xnews/1898.htm
- http://m.3g.gqskj.cn/xnews/1452423.htm
- http://m.3g.gqskj.cn/xnews/87551.htm
- http://m.3g.gqskj.cn/xnews/5730.htm
- http://m.3g.gqskj.cn/xnews/61115.htm
- http://m.3g.gqskj.cn/xnews/24123.htm
- http://m.3g.gqskj.cn/xnews/8508798.htm
- http://m.3g.gqskj.cn/xnews/5634.htm
- http://m.3g.gqskj.cn/xnews/042183.htm
- http://m.3g.gqskj.cn/xnews/621784.htm
- http://m.3g.gqskj.cn/xnews/8823.htm
- http://m.3g.gqskj.cn/xnews/22029.htm
- http://m.3g.gqskj.cn/xnews/6907958.htm
- http://m.3g.gqskj.cn/xnews/992178.htm
- http://m.3g.gqskj.cn/xnews/63497.htm
- http://m.3g.gqskj.cn/xnews/9090.htm
- http://m.3g.gqskj.cn/xnews/7576233.htm
- http://m.3g.gqskj.cn/xnews/477842.htm
- http://m.3g.gqskj.cn/xnews/7016.htm
- http://m.3g.gqskj.cn/xnews/227590.htm
- http://m.3g.gqskj.cn/xnews/856912.htm
- http://m.3g.gqskj.cn/xnews/0909.htm
- http://m.3g.gqskj.cn/xnews/0433707.htm
- http://m.3g.gqskj.cn/xnews/8535.htm
- http://m.3g.gqskj.cn/xnews/30689.htm
- http://m.3g.gqskj.cn/xnews/0968017.htm
- http://m.3g.gqskj.cn/xnews/94446.htm
- http://m.3g.gqskj.cn/xnews/9843.htm
- http://m.3g.gqskj.cn/xnews/5893512.htm
- http://m.3g.gqskj.cn/xnews/6905783.htm
- http://m.3g.gqskj.cn/xnews/7315587.htm
- http://m.3g.gqskj.cn/xnews/38372.htm
- http://m.3g.gqskj.cn/xnews/8267563.htm
- http://m.3g.gqskj.cn/xnews/2265.htm
- http://m.3g.gqskj.cn/xnews/5386.htm
- http://m.3g.gqskj.cn/xnews/76614.htm
- http://m.3g.gqskj.cn/xnews/50176.htm
- http://m.3g.gqskj.cn/xnews/37215.htm
- http://m.3g.gqskj.cn/xnews/6810835.htm
- http://m.3g.gqskj.cn/xnews/015150.htm
- http://m.3g.gqskj.cn/xnews/5254.htm
- http://m.3g.gqskj.cn/xnews/160113.htm
- http://m.3g.gqskj.cn/xnews/629113.htm
- http://m.3g.gqskj.cn/xnews/079322.htm
- http://m.3g.gqskj.cn/xnews/36547.htm
- http://m.3g.gqskj.cn/xnews/2875.htm
- http://m.3g.gqskj.cn/xnews/263472.htm
- http://m.3g.gqskj.cn/xnews/0052.htm
- http://m.3g.gqskj.cn/xnews/761227.htm
- http://m.3g.gqskj.cn/xnews/2631468.htm
- http://m.3g.gqskj.cn/xnews/4694702.htm
- http://m.3g.gqskj.cn/xnews/3600.htm
- http://m.3g.gqskj.cn/xnews/0911795.htm
- http://m.3g.gqskj.cn/xnews/4350.htm
- http://m.3g.gqskj.cn/xnews/38276.htm
- http://m.3g.gqskj.cn/xnews/57577.htm
- http://m.3g.gqskj.cn/xnews/92586.htm
- http://m.3g.gqskj.cn/xnews/1565.htm
- http://m.3g.gqskj.cn/xnews/1940447.htm
- http://m.3g.gqskj.cn/xnews/3810.htm
- http://m.3g.gqskj.cn/xnews/11799.htm
- http://m.3g.gqskj.cn/xnews/1809.htm
- http://m.3g.gqskj.cn/xnews/8118610.htm
- http://m.3g.gqskj.cn/xnews/3558049.htm
- http://m.3g.gqskj.cn/xnews/8924.htm
- http://m.3g.gqskj.cn/xnews/7867595.htm
- http://m.3g.gqskj.cn/xnews/7885.htm
- http://m.3g.gqskj.cn/xnews/5091.htm
- http://m.3g.gqskj.cn/xnews/36559.htm
- http://m.3g.gqskj.cn/xnews/0149.htm
- http://m.3g.gqskj.cn/xnews/8895452.htm
- http://m.3g.gqskj.cn/xnews/5943.htm
- http://m.3g.gqskj.cn/xnews/1569.htm
- http://m.3g.gqskj.cn/xnews/4125.htm
- http://m.3g.gqskj.cn/xnews/6069.htm
- http://m.3g.gqskj.cn/xnews/522655.htm
- http://m.3g.gqskj.cn/xnews/5616.htm
- http://m.3g.gqskj.cn/xnews/8630.htm
- http://m.3g.gqskj.cn/xnews/6087.htm
- http://m.3g.gqskj.cn/xnews/36458.htm
- http://m.3g.gqskj.cn/xnews/8021.htm
- http://m.3g.gqskj.cn/xnews/725952.htm
- http://m.3g.gqskj.cn/xnews/6416401.htm
- http://m.3g.gqskj.cn/xnews/8195844.htm
- http://m.3g.gqskj.cn/xnews/031614.htm
- http://m.3g.gqskj.cn/xnews/3756181.htm
- http://m.3g.gqskj.cn/xnews/6248.htm
- http://m.3g.gqskj.cn/xnews/11196.htm
- http://m.3g.gqskj.cn/xnews/7989487.htm
- http://m.3g.gqskj.cn/xnews/094444.htm
- http://m.3g.gqskj.cn/xnews/0495.htm
- http://m.3g.gqskj.cn/xnews/139633.htm
- http://m.3g.gqskj.cn/xnews/149373.htm
- http://m.3g.gqskj.cn/xnews/4565.htm
- http://m.3g.gqskj.cn/xnews/304715.htm
- http://m.3g.gqskj.cn/xnews/4372691.htm
- http://m.3g.gqskj.cn/xnews/573878.htm
- http://m.3g.gqskj.cn/xnews/182154.htm
- http://m.3g.gqskj.cn/xnews/04871.htm
- http://m.3g.gqskj.cn/xnews/0683982.htm
- http://m.3g.gqskj.cn/xnews/949283.htm
- http://m.3g.gqskj.cn/xnews/9461854.htm
- http://m.3g.gqskj.cn/xnews/2645926.htm
- http://m.3g.gqskj.cn/xnews/6979.htm
- http://m.3g.gqskj.cn/xnews/3682.htm
- http://m.3g.gqskj.cn/xnews/620657.htm
- http://m.3g.gqskj.cn/xnews/06518.htm
- http://m.3g.gqskj.cn/xnews/9846174.htm
- http://m.3g.gqskj.cn/xnews/7282.htm
- http://m.3g.gqskj.cn/xnews/0455800.htm
- http://m.3g.gqskj.cn/xnews/40036.htm
- http://m.3g.gqskj.cn/xnews/612779.htm
- http://m.3g.gqskj.cn/xnews/654736.htm
- http://m.3g.gqskj.cn/xnews/0264.htm
- http://m.3g.gqskj.cn/xnews/774472.htm
- http://m.3g.gqskj.cn/xnews/6943.htm
- http://m.3g.gqskj.cn/xnews/2692939.htm
- http://m.3g.gqskj.cn/xnews/18196.htm
- http://m.3g.gqskj.cn/xnews/609681.htm
- http://m.3g.gqskj.cn/xnews/7688.htm
- http://m.3g.gqskj.cn/xnews/04250.htm
- http://m.3g.gqskj.cn/xnews/6136.htm
- http://m.3g.gqskj.cn/xnews/3121.htm
- http://m.3g.gqskj.cn/xnews/2057.htm
- http://m.3g.gqskj.cn/xnews/7122841.htm

## 项目结构

```
xnews-aggregator/
├── app/                                 # Web 服务与 API 核心模块
│   ├── __init__.py                      # 应用工厂与蓝图注册
│   ├── routes.py                        # 路由与视图函数定义
│   ├── models.py                        # SQLAlchemy 数据模型（条目、标签、日志）
│   └── templates/                       # 管理界面 HTML 模板文件
├── core/                                # 业务逻辑与数据处理层
│   ├── importer.py                      # 批量导入解析器，支持 CSV/TXT 格式
│   ├── indexer.py                       # 条目索引构建与更新逻辑
│   ├── detector.py                      # 异步 HTTP 可用性检测任务调度
│   └── exporter.py                      # 数据导出为 JSON/CSV/Markdown
├── scripts/                             # 命令行工具与运维脚本
│   ├── import.py                        # 导入入口脚本（用户直接调用）
│   ├── check_links.py                   # 手动触发链接检测脚本
│   └── migrate_db.py                    # 数据库迁移与版本升级脚本
├── tests/                               # 单元测试与集成测试套件
│   ├── test_importer.py                 # 导入器边界条件与异常测试
│   ├── test_detector.py                 # 检测器并发与超时策略测试
│   └── fixtures/                        # 测试用样本数据文件
├── data/                                # 本地存储目录（默认 SQLite 数据库与缓存）
│   ├── index.db                         # 主数据库文件（自动生成）
│   └── logs/                            # 审计日志与检测报告存储位置
├── docs/                                # 项目文档源文件
│   ├── user_guide.md                    # 用户手册
│   ├── operations.md                    # 运维参考
│   ├── api_reference.md                 # API 文档
│   └── development.md                   # 开发指南
├── requirements.txt                     # 生产环境依赖列表
├── requirements-dev.txt                 # 开发环境额外依赖（测试、代码检查）
├── setup.py                             # 包安装与分发配置
└── README.md                            # 项目概览与快速入门（当前文件）
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并 clone 到本地开发环境，确保使用 Python 3.9 及以上版本。
2. 创建新的功能分支，分支名称应简要描述所解决的问题或新增功能，例如 `feature/add-rss-parser`。
3. 在 `core/` 或 `app/` 目录下编写代码，并补充对应的单元测试到 `tests/` 目录，确保所有测试通过。
4. 更新 `docs/` 下相关文档，若引入新的配置项或 API 变更，需同步修改 `user_guide.md` 或 `api_reference.md`。
5. 提交 pull request，在描述中明确说明改动范围、测试结果以及是否影响现有接口。

## 常见问题

Q: 导入大量 URL 时出现内存不足错误如何解决？
A: 默认导入器采用流式读取，但若单次导入条目超过 10 万条，建议使用 `--batch-size` 参数分批处理，或通过 `--no-check` 关闭即时链接检测以降低内存占用。

Q: 链接可用性检测任务无法正常执行，日志显示超时错误。
A: 检测模块默认超时时间为 10 秒，可通过配置文件修改 `DETECTOR_TIMEOUT` 值。若目标站点存在反爬策略，建议启用 `--user-agent` 参数或配置代理。

Q: 如何迁移已有数据到新版本数据库结构？
A: 执行 `scripts/migrate_db.py --target-version latest` 脚本，该工具会自动备份旧数据库并执行增量迁移。迁移前请确保 `data/` 目录有足够的磁盘空间。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:48
