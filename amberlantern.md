# WebLink Navigator

WebLink Navigator 是一个面向技术研究与信息聚合场景的轻量级外链资源导航系统。该项目定位于为开发者、技术研究人员以及内容策展人提供一套结构化的外部链接收录、分类与快速检索方案，解决散落于不同会话、文档或书签中的大量 URL 难以统一管理与高效复用的问题。

项目核心设计思想为“链接即数据”，所有外链资源以纯文本形态存储于可版本控制的配置目录中，配合自动化索引与静态站点生成逻辑，可快速构建为内部团队共享的知识路由表。WebLink Navigator 不依赖外部数据库，不采集用户行为数据，仅作为原始 URL 的整理与呈现层，适用于个人知识库、团队技术周报底稿或开源项目外部引用清单的标准化输出。

## 功能概览

**多源链接批量导入** 支持以纯文本或简单表格形式一次性录入上百条外链，自动识别常见 URL 格式并剔除无效空白行。

**字段化元数据标注** 每条链接可附加来源批次、收录时间、所属主题标签以及简短备注，便于后续按条件过滤。

**静态页面路由生成** 基于链接列表自动生成适配桌面与移动端的索引页面，支持按批次分组展示，无需动态后端服务。

**模糊搜索与快速定位** 提供关键词模糊匹配功能，可针对 URL 中的路径片段或自定义备注进行实时检索，返回高亮结果。

**导入导出互通** 链接数据支持导出为 CSV 与 JSON 格式，方便迁移至其他分析工具或进行离线备份。

**状态标记与复核机制** 为每条链接提供“待审核”“已验证”“已失效”三种状态标记，支持单人复核或多人协作场景下的状态流转。

**命令行交互工具** 内置 CLI 接口，可在终端中执行链接新增、列表刷新、状态批量修改等操作，便于集成至自动化脚本。

## 应用场景

**技术周报素材整理** 团队成员在日常浏览中收集的参考文章、工具站点或视频教程，可统一录入 WebLink Navigator，在周报撰写时按批次导出为规范列表，避免重复检索与链接遗失。

**开源项目外部引用清单** 维护开源项目时，对 README 或文档中引用的所有第三方资源进行集中登记，确保引用可追溯，并在外部链接变更时快速定位影响范围。

**个人知识库外链索引** 个人研究者可将不同主题（如机器学习、系统设计、编程语言）的外部分散链接按项目或时间批次归档，形成可检索的个人外链知识图谱。

**团队内部培训材料聚合** 培训组织者将线上课程入口、案例源码仓库、演示文稿地址等资源统一纳入导航系统，生成专属培训门户页面，供学员一站式访问。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动本地开发服务。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行本地开发服务器
python serve.py --port 8000
```

启动后，在浏览器中访问 `http://127.0.0.1:8000` 即可看到默认的链接索引页面。将待收录的 URL 列表放入 `data/raw/` 目录下的 `.txt` 或 `.csv` 文件中，执行 `python manage.py import` 即可完成导入。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于 CLI 工具与本地服务 |
| pip | 21.0 及以上 | Python 包管理器，用于安装依赖库 |
| Markdown | 3.4 及以上 | 用于将链接备注渲染为富文本描述 |
| PyYAML | 6.0 及以上 | 解析项目配置文件与元数据映射 |
| Jinja2 | 3.1 及以上 | 模板引擎，用于生成静态索引页面 |
| Watchdog | 3.0 及以上 | 可选依赖，用于开发模式下的文件变更自动重载 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、如何修改状态、如何生成静态页面 |
| 配置参考 | docs/configuration.md | 项目配置文件中的每一项参数含义及默认值 |
| 命令行工具 | docs/cli-reference.md | 所有可用 CLI 命令的完整语法与示例 |
| 数据格式规范 | docs/data-format.md | 链接列表文件应遵循的字段结构与编码要求 |

## 资源列表

- http://m.3g.fcful.cn/snews/87493.htm
- http://m.3g.fcful.cn/snews/0548.htm
- http://m.3g.fcful.cn/snews/070066.htm
- http://m.3g.fcful.cn/snews/7349273.htm
- http://m.3g.fcful.cn/snews/6550.htm
- http://m.3g.fcful.cn/snews/29435.htm
- http://m.3g.fcful.cn/snews/5757079.htm
- http://m.3g.fcful.cn/snews/2704114.htm
- http://m.3g.fcful.cn/snews/698487.htm
- http://m.3g.fcful.cn/snews/778358.htm
- http://m.3g.fcful.cn/snews/7346583.htm
- http://m.3g.fcful.cn/snews/3955.htm
- http://m.3g.fcful.cn/snews/1435896.htm
- http://m.3g.fcful.cn/snews/35013.htm
- http://m.3g.fcful.cn/snews/03071.htm
- http://m.3g.fcful.cn/snews/0401.htm
- http://m.3g.fcful.cn/snews/24491.htm
- http://m.3g.fcful.cn/snews/8420.htm
- http://m.3g.fcful.cn/snews/59240.htm
- http://m.3g.fcful.cn/snews/2532021.htm
- http://m.3g.fcful.cn/snews/4471777.htm
- http://m.3g.fcful.cn/snews/226723.htm
- http://m.3g.fcful.cn/snews/458845.htm
- http://m.3g.fcful.cn/snews/295181.htm
- http://m.3g.fcful.cn/snews/4528364.htm
- http://m.3g.fcful.cn/snews/7540216.htm
- http://m.3g.fcful.cn/snews/89877.htm
- http://m.3g.fcful.cn/snews/575537.htm
- http://m.3g.fcful.cn/snews/0814380.htm
- http://m.3g.fcful.cn/snews/6078461.htm
- http://m.3g.fcful.cn/snews/1788.htm
- http://m.3g.fcful.cn/snews/6180.htm
- http://m.3g.fcful.cn/snews/1382.htm
- http://m.3g.fcful.cn/snews/340915.htm
- http://m.3g.fcful.cn/snews/59326.htm
- http://m.3g.fcful.cn/snews/7669484.htm
- http://m.3g.fcful.cn/snews/4152537.htm
- http://m.3g.fcful.cn/snews/106581.htm
- http://m.3g.fcful.cn/snews/39795.htm
- http://m.3g.fcful.cn/snews/05201.htm
- http://m.3g.fcful.cn/snews/371573.htm
- http://m.3g.fcful.cn/snews/8010222.htm
- http://m.3g.fcful.cn/snews/14481.htm
- http://m.3g.fcful.cn/snews/2284528.htm
- http://m.3g.fcful.cn/snews/567645.htm
- http://m.3g.fcful.cn/snews/836014.htm
- http://m.3g.fcful.cn/snews/3599.htm
- http://m.3g.fcful.cn/snews/6808.htm
- http://m.3g.fcful.cn/snews/4088.htm
- http://m.3g.fcful.cn/snews/3493.htm
- http://m.3g.fcful.cn/snews/81185.htm
- http://m.3g.fcful.cn/snews/04394.htm
- http://m.3g.fcful.cn/snews/1410.htm
- http://m.3g.fcful.cn/snews/1437.htm
- http://m.3g.fcful.cn/snews/5625.htm
- http://m.3g.fcful.cn/snews/0382.htm
- http://m.3g.fcful.cn/snews/532956.htm
- http://m.3g.fcful.cn/snews/39177.htm
- http://m.3g.fcful.cn/snews/647875.htm
- http://m.3g.fcful.cn/snews/2556604.htm
- http://m.3g.fcful.cn/snews/9404448.htm
- http://m.3g.fcful.cn/snews/5315497.htm
- http://m.3g.fcful.cn/snews/2455.htm
- http://m.3g.fcful.cn/snews/0235591.htm
- http://m.3g.fcful.cn/snews/866665.htm
- http://m.3g.fcful.cn/snews/8598540.htm
- http://m.3g.fcful.cn/snews/26100.htm
- http://m.3g.fcful.cn/snews/5679592.htm
- http://m.3g.fcful.cn/snews/8578.htm
- http://m.3g.fcful.cn/snews/6342883.htm
- http://m.3g.fcful.cn/snews/0072657.htm
- http://m.3g.fcful.cn/snews/086020.htm
- http://m.3g.fcful.cn/snews/406442.htm
- http://m.3g.fcful.cn/snews/6720826.htm
- http://m.3g.fcful.cn/snews/64303.htm
- http://m.3g.fcful.cn/snews/07166.htm
- http://m.3g.fcful.cn/snews/7353971.htm
- http://m.3g.fcful.cn/snews/6512878.htm
- http://m.3g.fcful.cn/snews/15970.htm
- http://m.3g.fcful.cn/snews/70148.htm
- http://m.3g.fcful.cn/snews/9030.htm
- http://m.3g.fcful.cn/snews/899172.htm
- http://m.3g.fcful.cn/snews/476356.htm
- http://m.3g.fcful.cn/snews/2340401.htm
- http://m.3g.fcful.cn/snews/6572643.htm
- http://m.3g.fcful.cn/snews/3835.htm
- http://m.3g.fcful.cn/snews/04685.htm
- http://m.3g.fcful.cn/snews/81552.htm
- http://m.3g.fcful.cn/snews/65562.htm
- http://m.3g.fcful.cn/snews/89815.htm
- http://m.3g.fcful.cn/snews/83003.htm
- http://m.3g.fcful.cn/snews/7460107.htm
- http://m.3g.fcful.cn/snews/14691.htm
- http://m.3g.fcful.cn/snews/14000.htm
- http://m.3g.fcful.cn/snews/36797.htm
- http://m.3g.fcful.cn/snews/33683.htm
- http://m.3g.fcful.cn/snews/31555.htm
- http://m.3g.fcful.cn/snews/540577.htm
- http://m.3g.fcful.cn/snews/4258564.htm
- http://m.3g.fcful.cn/snews/7074594.htm
- http://m.3g.fcful.cn/snews/2571405.htm
- http://m.3g.fcful.cn/snews/50881.htm
- http://m.3g.fcful.cn/snews/5219.htm
- http://m.3g.fcful.cn/snews/4377432.htm
- http://m.3g.fcful.cn/snews/4235669.htm
- http://m.3g.fcful.cn/snews/1167104.htm
- http://m.3g.fcful.cn/snews/649197.htm
- http://m.3g.fcful.cn/snews/9113.htm
- http://m.3g.fcful.cn/snews/65231.htm
- http://m.3g.fcful.cn/snews/5862571.htm
- http://m.3g.fcful.cn/snews/89267.htm
- http://m.3g.fcful.cn/snews/4640.htm
- http://m.3g.fcful.cn/snews/4745122.htm
- http://m.3g.fcful.cn/snews/8398201.htm
- http://m.3g.fcful.cn/snews/666774.htm
- http://m.3g.fcful.cn/snews/3707122.htm
- http://m.3g.fcful.cn/snews/347446.htm
- http://m.3g.fcful.cn/snews/71501.htm
- http://m.3g.fcful.cn/snews/963007.htm
- http://m.3g.fcful.cn/snews/7925173.htm
- http://m.3g.fcful.cn/snews/8366694.htm
- http://m.3g.fcful.cn/snews/9164.htm
- http://m.3g.fcful.cn/snews/895493.htm
- http://m.3g.fcful.cn/snews/9301197.htm
- http://m.3g.fcful.cn/snews/684939.htm
- http://m.3g.fcful.cn/snews/870823.htm
- http://m.3g.fcful.cn/snews/582301.htm
- http://m.3g.fcful.cn/snews/463164.htm
- http://m.3g.fcful.cn/snews/37872.htm
- http://m.3g.fcful.cn/snews/13870.htm
- http://m.3g.fcful.cn/snews/622138.htm
- http://m.3g.fcful.cn/snews/787221.htm
- http://m.3g.fcful.cn/snews/23770.htm
- http://m.3g.fcful.cn/snews/98807.htm
- http://m.3g.fcful.cn/snews/1564195.htm
- http://m.3g.fcful.cn/snews/9022628.htm
- http://m.3g.fcful.cn/snews/9660723.htm
- http://m.3g.fcful.cn/snews/5959.htm
- http://m.3g.fcful.cn/snews/0222804.htm
- http://m.3g.fcful.cn/snews/981652.htm
- http://m.3g.fcful.cn/snews/453043.htm
- http://m.3g.fcful.cn/snews/5092210.htm
- http://m.3g.fcful.cn/snews/5554.htm
- http://m.3g.fcful.cn/snews/991891.htm
- http://m.3g.fcful.cn/snews/375635.htm
- http://m.3g.fcful.cn/snews/0355606.htm
- http://m.3g.fcful.cn/snews/5196.htm
- http://m.3g.fcful.cn/snews/1024.htm
- http://m.3g.fcful.cn/snews/0358.htm
- http://m.3g.fcful.cn/snews/529143.htm
- http://m.3g.fcful.cn/snews/977192.htm
- http://m.3g.fcful.cn/snews/461849.htm
- http://m.3g.fcful.cn/snews/0763014.htm
- http://m.3g.fcful.cn/snews/325531.htm
- http://m.3g.fcful.cn/snews/7976997.htm
- http://m.3g.fcful.cn/snews/6904862.htm
- http://m.3g.fcful.cn/snews/669745.htm
- http://m.3g.fcful.cn/snews/2307.htm
- http://m.3g.fcful.cn/snews/4569879.htm
- http://m.3g.fcful.cn/snews/04697.htm
- http://m.3g.fcful.cn/snews/5947.htm
- http://m.3g.fcful.cn/snews/3187.htm
- http://m.3g.fcful.cn/snews/4317137.htm
- http://m.3g.fcful.cn/snews/62773.htm
- http://m.3g.fcful.cn/snews/632381.htm
- http://m.3g.fcful.cn/snews/6980928.htm
- http://m.3g.fcful.cn/snews/88087.htm
- http://m.3g.fcful.cn/snews/452937.htm
- http://m.3g.fcful.cn/snews/68168.htm
- http://m.3g.fcful.cn/snews/19929.htm
- http://m.3g.fcful.cn/snews/0780.htm
- http://m.3g.fcful.cn/snews/73457.htm
- http://m.3g.fcful.cn/snews/9168322.htm
- http://m.3g.fcful.cn/snews/6806970.htm
- http://m.3g.fcful.cn/snews/7797.htm
- http://m.3g.fcful.cn/snews/361255.htm
- http://m.3g.fcful.cn/snews/782724.htm
- http://m.3g.fcful.cn/snews/5963394.htm
- http://m.3g.fcful.cn/snews/7275.htm
- http://m.3g.fcful.cn/snews/2626057.htm
- http://m.3g.fcful.cn/snews/62316.htm
- http://m.3g.fcful.cn/snews/6878.htm
- http://m.3g.fcful.cn/snews/589737.htm
- http://m.3g.fcful.cn/snews/8149812.htm
- http://m.3g.fcful.cn/snews/7956798.htm
- http://m.3g.fcful.cn/snews/54112.htm
- http://m.3g.fcful.cn/snews/1920.htm
- http://m.3g.fcful.cn/snews/549004.htm
- http://m.3g.fcful.cn/snews/5716702.htm
- http://m.3g.fcful.cn/snews/3091.htm
- http://m.3g.fcful.cn/snews/13085.htm
- http://m.3g.fcful.cn/snews/23294.htm
- http://m.3g.fcful.cn/snews/783651.htm
- http://m.3g.fcful.cn/snews/976056.htm
- http://m.3g.fcful.cn/snews/7925.htm
- http://m.3g.fcful.cn/snews/975748.htm
- http://m.3g.fcful.cn/snews/21539.htm
- http://m.3g.fcful.cn/snews/4611683.htm
- http://m.3g.fcful.cn/snews/5712.htm
- http://m.3g.fcful.cn/snews/847164.htm
- http://m.3g.fcful.cn/snews/44588.htm
- http://m.3g.fcful.cn/snews/2521629.htm
- http://m.3g.fcful.cn/snews/74654.htm
- http://m.3g.fcful.cn/snews/4892.htm
- http://m.3g.fcful.cn/snews/098310.htm
- http://m.3g.fcful.cn/snews/182208.htm
- http://m.3g.fcful.cn/snews/570201.htm
- http://m.3g.fcful.cn/snews/6809454.htm
- http://m.3g.fcful.cn/snews/083784.htm
- http://m.3g.fcful.cn/snews/145516.htm
- http://m.3g.fcful.cn/snews/40355.htm
- http://m.3g.fcful.cn/snews/898016.htm
- http://m.3g.fcful.cn/snews/959303.htm
- http://m.3g.fcful.cn/snews/11775.htm
- http://m.3g.fcful.cn/snews/9439997.htm
- http://m.3g.fcful.cn/snews/0597.htm
- http://m.3g.fcful.cn/snews/84941.htm
- http://m.3g.fcful.cn/snews/8228787.htm
- http://m.3g.fcful.cn/snews/1026.htm
- http://m.3g.fcful.cn/snews/3804.htm
- http://m.3g.fcful.cn/snews/8856.htm
- http://m.3g.fcful.cn/snews/7991.htm
- http://m.3g.fcful.cn/snews/08492.htm
- http://m.3g.fcful.cn/snews/4408.htm
- http://m.3g.fcful.cn/snews/4768287.htm
- http://m.3g.fcful.cn/snews/556496.htm
- http://m.3g.fcful.cn/snews/89449.htm
- http://m.3g.fcful.cn/snews/220797.htm
- http://m.3g.fcful.cn/snews/2830891.htm
- http://m.3g.fcful.cn/snews/5633995.htm
- http://m.3g.fcful.cn/snews/7767751.htm
- http://m.3g.fcful.cn/snews/4363.htm
- http://m.3g.fcful.cn/snews/4391923.htm
- http://m.3g.fcful.cn/snews/67512.htm
- http://m.3g.fcful.cn/snews/2120.htm
- http://m.3g.fcful.cn/snews/948686.htm
- http://m.3g.fcful.cn/snews/282020.htm
- http://m.3g.fcful.cn/snews/28451.htm
- http://m.3g.fcful.cn/snews/940221.htm
- http://m.3g.fcful.cn/snews/1018701.htm
- http://m.3g.fcful.cn/snews/51956.htm
- http://m.3g.fcful.cn/snews/7865.htm
- http://m.3g.fcful.cn/snews/5204186.htm
- http://m.3g.fcful.cn/snews/8118.htm
- http://m.3g.fcful.cn/snews/5267.htm
- http://m.3g.fcful.cn/snews/559799.htm
- http://m.3g.fcful.cn/snews/97557.htm
- http://m.3g.fcful.cn/snews/20333.htm
- http://m.3g.fcful.cn/snews/4863203.htm
- http://m.3g.fcful.cn/snews/235594.htm

## 项目结构

```
weblink-navigator/
├── cli/                                 # 命令行工具模块
│   ├── commands/                        # 子命令实现
│   │   ├── import.py                    # 导入链接列表（支持 txt / csv）
│   │   ├── export.py                    # 导出为 JSON / CSV 格式
│   │   ├── status.py                    # 批量修改链接状态
│   │   └── search.py                    # 命令行下的关键词搜索
│   ├── parser.py                        # 原始链接解析与校验逻辑
│   └── formatter.py                     # 终端输出格式化（表格 / 列表）
├── core/                                # 核心数据处理层
│   ├── loader.py                        # 从 data/raw 读取文件并解析
│   ├── indexer.py                       # 构建内存索引与倒排表
│   ├── models.py                        # Link 数据类定义与状态枚举
│   └── validator.py                     # URL 合法性检查与去重
├── web/                                 # 静态站点生成与预览服务
│   ├── templates/                       # Jinja2 模板文件
│   │   ├── index.html                   # 批次列表首页
│   │   ├── batch.html                   # 单批次详细视图
│   │   └── search.html                  # 搜索结果页
│   ├── static/                          # 编译后的 CSS / JS 资源
│   │   ├── style.css                    # 基础布局与响应式样式
│   │   └── search.js                    # 前端模糊搜索与高亮逻辑
│   ├── generator.py                     # 将索引数据渲染为静态 HTML
│   └── server.py                        # 基于 http.server 的开发预览服务
├── data/                                # 数据存储目录（不纳入版本控制示例）
│   ├── raw/                             # 放置原始导入文件（.txt / .csv）
│   ├── parsed/                          # 解析后的结构化 JSON 缓存
│   └── export/                          # 导出文件输出目录
├── docs/                                # 项目文档
│   ├── user-guide.md                    # 用户操作手册
│   ├── configuration.md                 # 配置文件详解
│   ├── cli-reference.md                 # 完整 CLI 命令参考
│   └── data-format.md                   # 导入文件字段规范
├── tests/                               # 单元测试与集成测试
│   ├── test_loader.py                   # 数据加载器测试用例
│   ├── test_indexer.py                  # 索引构建测试用例
│   └── test_cli.py                      # 命令行子命令测试用例
├── config.yaml                          # 主配置文件（站点标题、分页大小等）
├── requirements.txt                     # Python 依赖清单
├── manage.py                            # 全局管理入口（CLI 统一调度）
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻代码仓库至个人账户，并在本地创建功能分支，分支命名建议采用 `feature/` 或 `fix/` 前缀，例如 `feature/add-rss-export`。

2. 在 `data/raw/` 目录下放入至少一条测试链接，运行 `python manage.py import` 验证数据加载流程是否正常工作，并确保所有现有单元测试通过（执行 `pytest tests/`）。

3. 若新增或修改 CLI 子命令，请在 `docs/cli-reference.md` 中同步更新对应的命令语法与示例，并补充至少一个端到端测试用例至 `tests/test_cli.py`。

4. 提交代码前执行代码风格检查（`flake8 .` 与 `black .`），确保无语法警告且格式符合项目规范。提交信息请采用语义化格式，例如 `feat: add batch delete command` 或 `fix: handle empty line in csv import`。

5. 发起 Pull Request 至主仓库的 `main` 分支，描述中需说明变更目的、影响范围以及是否包含破坏性改动。项目维护者将在 48 小时内进行审阅。

## 常见问题

**Q：导入大量链接时出现内存占用过高怎么办？**

A：项目默认采用流式读取解析大文件，单次导入 1000 条链接的内存增量约在 50 MB 以内。如果链接数量超过 5000 条，建议将原始文件拆分为多个小于 2 MB 的批次文件，分次执行 `import` 命令。同时可在 `config.yaml` 中调整 `batch_size` 参数控制单次加载的记录数。

**Q：如何自定义静态页面的品牌标识与配色？**

A：所有页面样式变量定义在 `web/static/style.css` 的 `:root` 伪类中，包括主色调、字体族、间距单位等。如需深度定制，可直接修改该 CSS 文件，或替换 `web/templates/` 下的 Jinja2 模板布局文件。修改后重新运行 `python manage.py generate` 即可刷新所有静态页面。

**Q：能否与持续集成工具结合，实现定时自动导入？**

A：可以。项目提供无交互的 CLI 模式，所有命令均支持 `--non-interactive` 标志，可在 CI 脚本中组合使用。例如在 Jenkins 或 GitHub Actions 中，可配置定时任务执行 `python manage.py import --path ./data/raw/latest.csv && python manage.py generate --output ./public`，生成的静态页面可直接部署至对象存储服务。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
