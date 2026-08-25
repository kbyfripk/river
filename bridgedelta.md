# WebRes Navigator

WebRes Navigator 是一个面向技术调研、信息聚合与深度阅读场景的轻量级外链资源导航系统。该项目定位于帮助开发者、技术研究员与内容策展人高效管理、分类展示与快速访问分散于互联网各处的信息型 URL 资源，尤其适用于处理大批量、多批次、来源固定的外链数据集。WebRes Navigator 不提供爬虫或数据抓取功能，而是作为人工筛选后 URL 的索引与展示层，强调结构化呈现与可维护性。

目标用户包括需要整理技术新闻存档的运维工程师、维护行业资讯聚合页的内容运营人员、以及进行纵向信息比对的研究型开发者。WebRes Navigator 通过统一的资源列表抽象、扁平化的项目结构与零外部依赖的静态部署方案，解决外链资源易失散、难分类、不便共享的问题。项目本身不依赖数据库或后端服务，所有资源记录以纯文本形式维护于项目仓库中，支持版本追踪与协作编辑。

## 功能概览

**批量资源导入** 支持将用户提供的原始 URL 列表直接复制至指定数据目录，项目内置脚本可自动完成格式校验与去重。

**分类标签生成** 基于 URL 路径特征与文件名模式自动生成建议性分类标签，辅助人工整理。

**静态索引页面构建** 通过命令行工具一键生成响应式 HTML 索引页，包含资源标题、来源域名与更新时间。

**资源状态检测** 提供可选的连通性检查模块，支持超时与重试配置，输出失效链接报告。

**多批次数据管理** 针对分批交付的资源列表（如第 66/240 批），提供批次标识与合并功能，便于增量更新。

**原始 URL 保真输出** 系统核心约束为完整保留用户所提供的每一个 URL 的原始字符串形态，不添加协议前缀、不修改域名大小写、不附加尾部斜杠，确保链接精确可用。

**Markdown 文档自动生成** 基于预设模板与资源列表自动生成符合开源社区规范的 README 文档，减少维护成本。

## 应用场景

**技术资讯周报整理** 技术团队每周收集数十篇行业动态与安全公告链接，使用 WebRes Navigator 统一录入并生成周报索引页，团队成员可一键访问原始文章，无需反复检索。

**开源项目外部引用归档** 开源项目维护者需要记录项目文档中引用的外部规范、标准或参考实现链接。WebRes Navigator 可按照批次组织这些引用，并随项目仓库一同版本化管理，避免链接失效后无处追溯。

**多源数据对比研究** 研究人员从不同渠道采集同一主题下的信息页面链接（如不同厂商的产品发布公告），利用 WebRes Navigator 的批次与标签功能对链接进行分组，辅助横向对比分析。

**离线文档资源映射** 在内网或离线环境中，运维人员可将允许访问的外部资源链接预先整理至 WebRes Navigator，生成离线可用的索引页面，供内部用户按需申请开通网络访问。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/example/webres-navigator.git
cd webres-navigator

# 安装依赖（项目依赖 Python 3.8+ 与 pip）
pip install -r requirements.txt

# 执行构建命令，生成索引页面与更新 README
python build.py --batch 66 --input data/batch_66.txt --output docs/index.html
```

上述命令中，`data/batch_66.txt` 为用户提供的原始 URL 列表文件，每行一个 URL。执行成功后，`docs/` 目录下将生成对应的索引页，同时项目根目录下的 README.md 将自动更新资源列表章节。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心脚本运行环境，低于 3.8 版本将无法解析类型注解 |
| pip | 20.0 及以上 | 用于安装 requirements.txt 中列出的第三方库 |
| Git | 2.25 及以上 | 用于克隆仓库与版本管理，旧版本可能不支持部分提交哈希显示 |
| Markdown 解析库 | markdown 3.3.0 | 用于生成 README 中的表格与列表，必须精确匹配此版本 |
| 网络请求库 | requests 2.25.0 | 仅在启用连通性检查时需要，可选依赖 |
| 操作系统 | Linux / macOS / Windows WSL | 文件路径分隔符需符合 POSIX 规范，Windows 原生环境未充分测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何录入新批次资源、如何生成索引页、如何更新 README |
| 管理员指南 | docs/admin_guide.md | 如何配置连通性检查参数、如何合并多个批次、如何处理失效链接 |
| 开发参考 | docs/dev_reference.md | 项目模块划分、核心类与函数签名、扩展自定义分类器的接口说明 |
| 常见工作流 | docs/workflows.md | 从收到原始数据到完成部署的完整操作步骤，含故障排查提示 |

## 资源列表

- http://m.wap.fcful.cn/nnews/1201026.htm
- http://m.wap.fcful.cn/nnews/95685.htm
- http://m.wap.fcful.cn/nnews/1733966.htm
- http://m.wap.fcful.cn/nnews/2346560.htm
- http://m.wap.fcful.cn/nnews/32447.htm
- http://m.wap.fcful.cn/nnews/04610.htm
- http://m.wap.fcful.cn/nnews/466845.htm
- http://m.wap.fcful.cn/nnews/094041.htm
- http://m.wap.fcful.cn/nnews/1779.htm
- http://m.wap.fcful.cn/nnews/01487.htm
- http://m.wap.fcful.cn/nnews/3029.htm
- http://m.wap.fcful.cn/nnews/946507.htm
- http://m.wap.fcful.cn/nnews/9088600.htm
- http://m.wap.fcful.cn/nnews/3409185.htm
- http://m.wap.fcful.cn/nnews/064003.htm
- http://m.wap.fcful.cn/nnews/87434.htm
- http://m.wap.fcful.cn/nnews/95289.htm
- http://m.wap.fcful.cn/nnews/666963.htm
- http://m.wap.fcful.cn/nnews/6098895.htm
- http://m.wap.fcful.cn/nnews/222783.htm
- http://m.wap.fcful.cn/nnews/7504.htm
- http://m.wap.fcful.cn/nnews/56516.htm
- http://m.wap.fcful.cn/nnews/8624.htm
- http://m.wap.fcful.cn/nnews/421652.htm
- http://m.wap.fcful.cn/nnews/130810.htm
- http://m.wap.fcful.cn/nnews/994989.htm
- http://m.wap.fcful.cn/nnews/18518.htm
- http://m.wap.fcful.cn/nnews/8155.htm
- http://m.wap.fcful.cn/nnews/6205846.htm
- http://m.wap.fcful.cn/nnews/56035.htm
- http://m.wap.fcful.cn/nnews/243905.htm
- http://m.wap.fcful.cn/nnews/635682.htm
- http://m.wap.fcful.cn/nnews/0923.htm
- http://m.wap.fcful.cn/nnews/0788.htm
- http://m.wap.fcful.cn/nnews/74437.htm
- http://m.wap.fcful.cn/nnews/233765.htm
- http://m.wap.fcful.cn/nnews/5985.htm
- http://m.wap.fcful.cn/nnews/74065.htm
- http://m.wap.fcful.cn/nnews/35241.htm
- http://m.wap.fcful.cn/nnews/9460.htm
- http://m.wap.fcful.cn/nnews/17043.htm
- http://m.wap.fcful.cn/nnews/0354.htm
- http://m.wap.fcful.cn/nnews/2465.htm
- http://m.wap.fcful.cn/nnews/81636.htm
- http://m.wap.fcful.cn/nnews/38766.htm
- http://m.wap.fcful.cn/nnews/04202.htm
- http://m.wap.fcful.cn/nnews/9857.htm
- http://m.wap.fcful.cn/nnews/654888.htm
- http://m.wap.fcful.cn/nnews/5218399.htm
- http://m.wap.fcful.cn/nnews/187468.htm
- http://m.wap.fcful.cn/nnews/75490.htm
- http://m.wap.fcful.cn/nnews/1759361.htm
- http://m.wap.fcful.cn/nnews/8877.htm
- http://m.wap.fcful.cn/nnews/114017.htm
- http://m.wap.fcful.cn/nnews/1244864.htm
- http://m.wap.fcful.cn/nnews/0403700.htm
- http://m.wap.fcful.cn/nnews/27027.htm
- http://m.wap.fcful.cn/nnews/836590.htm
- http://m.wap.fcful.cn/nnews/6317040.htm
- http://m.wap.fcful.cn/nnews/408944.htm
- http://m.wap.fcful.cn/nnews/13898.htm
- http://m.wap.fcful.cn/nnews/17709.htm
- http://m.wap.fcful.cn/nnews/4958414.htm
- http://m.wap.fcful.cn/nnews/3440176.htm
- http://m.wap.fcful.cn/nnews/426223.htm
- http://m.wap.fcful.cn/nnews/05958.htm
- http://m.wap.fcful.cn/nnews/19302.htm
- http://m.wap.fcful.cn/nnews/00916.htm
- http://m.wap.fcful.cn/nnews/11846.htm
- http://m.wap.fcful.cn/nnews/0695602.htm
- http://m.wap.fcful.cn/nnews/116748.htm
- http://m.wap.fcful.cn/nnews/1038.htm
- http://m.wap.fcful.cn/nnews/7602384.htm
- http://m.wap.fcful.cn/nnews/1733.htm
- http://m.wap.fcful.cn/nnews/823349.htm
- http://m.wap.fcful.cn/nnews/942700.htm
- http://m.wap.fcful.cn/nnews/2978.htm
- http://m.wap.fcful.cn/nnews/430268.htm
- http://m.wap.fcful.cn/nnews/198720.htm
- http://m.wap.fcful.cn/nnews/7930738.htm
- http://m.wap.fcful.cn/nnews/0995531.htm
- http://m.wap.fcful.cn/nnews/1222963.htm
- http://m.wap.fcful.cn/nnews/5020.htm
- http://m.wap.fcful.cn/nnews/44921.htm
- http://m.wap.fcful.cn/nnews/2244638.htm
- http://m.wap.fcful.cn/nnews/7881568.htm
- http://m.wap.fcful.cn/nnews/1089542.htm
- http://m.wap.fcful.cn/nnews/2009121.htm
- http://m.wap.fcful.cn/nnews/0884499.htm
- http://m.wap.fcful.cn/nnews/3909050.htm
- http://m.wap.fcful.cn/nnews/20435.htm
- http://m.wap.fcful.cn/nnews/961896.htm
- http://m.wap.fcful.cn/nnews/8904903.htm
- http://m.wap.fcful.cn/nnews/975379.htm
- http://m.wap.fcful.cn/nnews/226150.htm
- http://m.wap.fcful.cn/nnews/44158.htm
- http://m.wap.fcful.cn/nnews/6463.htm
- http://m.wap.fcful.cn/nnews/91297.htm
- http://m.wap.fcful.cn/nnews/6855.htm
- http://m.wap.fcful.cn/nnews/69220.htm
- http://m.wap.fcful.cn/nnews/283119.htm
- http://m.wap.fcful.cn/nnews/883738.htm
- http://m.wap.fcful.cn/nnews/5710800.htm
- http://m.wap.fcful.cn/nnews/869714.htm
- http://m.wap.fcful.cn/nnews/37271.htm
- http://m.wap.fcful.cn/nnews/14393.htm
- http://m.wap.fcful.cn/nnews/2007159.htm
- http://m.wap.fcful.cn/nnews/5570960.htm
- http://m.wap.fcful.cn/nnews/554801.htm
- http://m.wap.fcful.cn/nnews/8617.htm
- http://m.wap.fcful.cn/nnews/69664.htm
- http://m.wap.fcful.cn/nnews/8047600.htm
- http://m.wap.fcful.cn/nnews/3535552.htm
- http://m.wap.fcful.cn/nnews/5878.htm
- http://m.wap.fcful.cn/nnews/829680.htm
- http://m.wap.fcful.cn/nnews/4550639.htm
- http://m.wap.fcful.cn/nnews/6718878.htm
- http://m.wap.fcful.cn/nnews/1339489.htm
- http://m.wap.fcful.cn/nnews/790234.htm
- http://m.wap.fcful.cn/nnews/4392525.htm
- http://m.wap.fcful.cn/nnews/0979.htm
- http://m.wap.fcful.cn/nnews/73022.htm
- http://m.wap.fcful.cn/nnews/9977197.htm
- http://m.wap.fcful.cn/nnews/8915734.htm
- http://m.wap.fcful.cn/nnews/12175.htm
- http://m.wap.fcful.cn/nnews/42547.htm
- http://m.wap.fcful.cn/nnews/7724.htm
- http://m.wap.fcful.cn/nnews/75748.htm
- http://m.wap.fcful.cn/nnews/0432.htm
- http://m.wap.fcful.cn/nnews/3445856.htm
- http://m.wap.fcful.cn/nnews/5971.htm
- http://m.wap.fcful.cn/nnews/2236.htm
- http://m.wap.fcful.cn/nnews/28054.htm
- http://m.wap.fcful.cn/nnews/843836.htm
- http://m.wap.fcful.cn/nnews/5995570.htm
- http://m.wap.fcful.cn/nnews/529039.htm
- http://m.wap.fcful.cn/nnews/9633310.htm
- http://m.wap.fcful.cn/nnews/4162861.htm
- http://m.wap.fcful.cn/nnews/7328.htm
- http://m.wap.fcful.cn/nnews/1672210.htm
- http://m.wap.fcful.cn/nnews/87958.htm
- http://m.wap.fcful.cn/nnews/9461206.htm
- http://m.wap.fcful.cn/nnews/22147.htm
- http://m.wap.fcful.cn/nnews/645213.htm
- http://m.wap.fcful.cn/nnews/5540336.htm
- http://m.wap.fcful.cn/nnews/55658.htm
- http://m.wap.fcful.cn/nnews/3613715.htm
- http://m.wap.fcful.cn/nnews/8070722.htm
- http://m.wap.fcful.cn/nnews/01452.htm
- http://m.wap.fcful.cn/nnews/6096.htm
- http://m.wap.fcful.cn/nnews/5082477.htm
- http://m.wap.fcful.cn/nnews/48405.htm
- http://m.wap.fcful.cn/nnews/73396.htm
- http://m.wap.fcful.cn/nnews/72973.htm
- http://m.wap.fcful.cn/nnews/5211592.htm
- http://m.wap.fcful.cn/nnews/590174.htm
- http://m.wap.fcful.cn/nnews/5839682.htm
- http://m.wap.fcful.cn/nnews/587729.htm
- http://m.wap.fcful.cn/nnews/83397.htm
- http://m.wap.fcful.cn/nnews/075335.htm
- http://m.wap.fcful.cn/nnews/18112.htm
- http://m.wap.fcful.cn/nnews/0518.htm
- http://m.wap.fcful.cn/nnews/386695.htm
- http://m.wap.fcful.cn/nnews/0290183.htm
- http://m.wap.fcful.cn/nnews/64547.htm
- http://m.wap.fcful.cn/nnews/2186.htm
- http://m.wap.fcful.cn/nnews/9676759.htm
- http://m.wap.fcful.cn/nnews/4658974.htm
- http://m.wap.fcful.cn/nnews/600080.htm
- http://m.wap.fcful.cn/nnews/7638.htm
- http://m.wap.fcful.cn/nnews/540760.htm
- http://m.wap.fcful.cn/nnews/968713.htm
- http://m.wap.fcful.cn/nnews/17514.htm
- http://m.wap.fcful.cn/nnews/5490.htm
- http://m.wap.fcful.cn/nnews/911726.htm
- http://m.wap.fcful.cn/nnews/1046.htm
- http://m.wap.fcful.cn/nnews/63577.htm
- http://m.wap.fcful.cn/nnews/4758207.htm
- http://m.wap.fcful.cn/nnews/39888.htm
- http://m.wap.fcful.cn/nnews/73956.htm
- http://m.wap.fcful.cn/nnews/33970.htm
- http://m.wap.fcful.cn/nnews/827802.htm
- http://m.wap.fcful.cn/nnews/5892673.htm
- http://m.wap.fcful.cn/nnews/589957.htm
- http://m.wap.fcful.cn/nnews/0070.htm
- http://m.wap.fcful.cn/nnews/784013.htm
- http://m.wap.fcful.cn/nnews/64375.htm
- http://m.wap.fcful.cn/nnews/38103.htm
- http://m.wap.fcful.cn/nnews/013073.htm
- http://m.wap.fcful.cn/nnews/816994.htm
- http://m.wap.fcful.cn/nnews/08334.htm
- http://m.wap.fcful.cn/nnews/1743914.htm
- http://m.wap.fcful.cn/nnews/2026035.htm
- http://m.wap.fcful.cn/nnews/0360.htm
- http://m.wap.fcful.cn/nnews/8544644.htm
- http://m.wap.fcful.cn/nnews/95705.htm
- http://m.wap.fcful.cn/nnews/6266.htm
- http://m.wap.fcful.cn/nnews/475469.htm
- http://m.wap.fcful.cn/nnews/88183.htm
- http://m.wap.fcful.cn/nnews/3649347.htm
- http://m.wap.fcful.cn/nnews/1921835.htm
- http://m.wap.fcful.cn/nnews/05141.htm
- http://m.wap.fcful.cn/nnews/4403129.htm
- http://m.wap.fcful.cn/nnews/7066.htm
- http://m.wap.fcful.cn/nnews/5040980.htm
- http://m.wap.fcful.cn/nnews/0263909.htm
- http://m.wap.fcful.cn/nnews/5686.htm
- http://m.wap.fcful.cn/nnews/09510.htm
- http://m.wap.fcful.cn/nnews/1190.htm
- http://m.wap.fcful.cn/nnews/3352.htm
- http://m.wap.fcful.cn/nnews/8387.htm
- http://m.wap.fcful.cn/nnews/4318.htm
- http://m.wap.fcful.cn/nnews/9794.htm
- http://m.wap.fcful.cn/nnews/85992.htm
- http://m.wap.fcful.cn/nnews/9650.htm
- http://m.wap.fcful.cn/nnews/9106.htm
- http://m.wap.fcful.cn/nnews/6905.htm
- http://m.wap.fcful.cn/nnews/768257.htm
- http://m.wap.fcful.cn/nnews/742339.htm
- http://m.wap.fcful.cn/nnews/92488.htm
- http://m.wap.fcful.cn/nnews/13572.htm
- http://m.wap.fcful.cn/nnews/2912010.htm
- http://m.wap.fcful.cn/nnews/24389.htm
- http://m.wap.fcful.cn/nnews/64666.htm
- http://m.wap.fcful.cn/nnews/615456.htm
- http://m.wap.fcful.cn/nnews/725463.htm
- http://m.wap.fcful.cn/nnews/0626.htm
- http://m.wap.fcful.cn/nnews/4491572.htm
- http://m.wap.fcful.cn/nnews/6546.htm
- http://m.wap.fcful.cn/nnews/552303.htm
- http://m.wap.fcful.cn/nnews/482884.htm
- http://m.wap.fcful.cn/nnews/8141.htm
- http://m.wap.fcful.cn/nnews/1929165.htm
- http://m.wap.fcful.cn/nnews/0800813.htm
- http://m.wap.fcful.cn/nnews/0649.htm
- http://m.wap.fcful.cn/nnews/47912.htm
- http://m.wap.fcful.cn/nnews/31125.htm
- http://m.wap.fcful.cn/nnews/11318.htm
- http://m.wap.fcful.cn/nnews/2404048.htm
- http://m.wap.fcful.cn/nnews/2923404.htm
- http://m.wap.fcful.cn/nnews/8485.htm
- http://m.wap.fcful.cn/nnews/06280.htm
- http://m.wap.fcful.cn/nnews/6705349.htm
- http://m.wap.fcful.cn/nnews/382811.htm
- http://m.wap.fcful.cn/nnews/051124.htm
- http://m.wap.fcful.cn/nnews/47981.htm
- http://m.wap.fcful.cn/nnews/99715.htm
- http://m.wap.fcful.cn/nnews/84579.htm
- http://m.wap.fcful.cn/nnews/629190.htm
- http://m.wap.fcful.cn/nnews/6828.htm

## 项目结构

```
webres-navigator/
├── build.py                 # 主构建脚本，负责解析输入、生成索引页与更新 README
├── requirements.txt         # Python 依赖声明，包含 markdown 与 requests 库
├── README.md                # 项目说明文档，资源列表由此文件自动维护
├── data/                    # 存放原始资源列表文件的目录
│   ├── batch_66.txt         # 第 66 批原始 URL 列表，每行一个 URL
│   ├── batch_67.txt         # 后续批次示例文件
│   └── archive/             # 已处理批次的归档目录
│       └── batch_65.txt
├── docs/                    # 生成的静态文档输出目录
│   ├── index.html           # 资源索引页，包含所有 URL 的列表与分类标签
│   ├── user_guide.md        # 用户手册，详细说明日常操作流程
│   └── admin_guide.md       # 管理员指南，涵盖配置与故障排查
├── src/                     # 核心源代码目录
│   ├── parser.py            # URL 解析与校验模块，负责提取文件名与路径
│   ├── generator.py         # HTML 与 Markdown 生成器，负责渲染输出
│   ├── checker.py           # 连通性检查模块，可选功能，依赖 requests
│   └── utils.py             # 通用工具函数，包括日志与文件操作
├── tests/                   # 单元测试目录
│   ├── test_parser.py       # 针对 parser.py 的测试用例
│   └── test_generator.py    # 针对 generator.py 的测试用例
└── .gitignore               # Git 忽略规则，排除临时文件与本地配置
```

## 贡献指南

1. 在 GitHub 或 Gitee 上 Fork 本仓库至个人账号，随后克隆至本地开发环境。请确保使用主分支的最新提交作为基准。

2. 新建功能分支，分支命名建议采用 `feature/描述` 或 `fix/描述` 格式。例如 `feature/batch-67-support`。所有开发工作均在该分支上进行。

3. 修改代码或文档后，运行测试套件确保现有功能未被破坏。测试命令为 `python -m unittest discover tests`。若新增功能，请同步添加对应的测试用例。

4. 提交变更时使用清晰且语义化的提交信息，推荐遵循 Conventional Commits 规范。例如 `feat: 增加对 Windows 路径分隔符的兼容处理`。

5. 将分支推送至远程仓库，随后通过平台界面发起 Pull Request。PR 描述中应说明变更目的、实现方式与影响范围，等待项目维护者审阅。

## 常见问题

**问：资源列表中的部分 URL 无法访问，应如何处理？**

答：WebRes Navigator 本身不负责保证外部链接的可访问性。但项目提供可选的连通性检查模块，用户可执行 `python src/checker.py --input data/batch_66.txt --report unreachable.log` 生成失效链接报告。对于确认失效的链接，建议人工核实后从列表中移除或替换为有效地址。

**问：如何将多批次的 URL 合并至同一个索引页？**

答：将多个批次文件放置于 `data/` 目录下，然后执行 `python build.py --merge --output docs/index.html`。构建脚本会自动读取所有以 `batch_` 开头的文件，去重后生成统一的索引页。合并顺序按文件名自然排序。

**问：生成的 README 中资源列表章节被覆盖或格式错乱怎么办？**

答：README.md 中资源列表章节由构建脚本自动维护。如需手动编辑，请修改 `src/generator.py` 中关于 `## 资源列表` 部分的生成逻辑。若仅需更新列表内容，应直接修改对应的批次文件，然后重新运行构建脚本，不可手动修改 README 中由脚本生成的列表段落。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
