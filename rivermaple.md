# WebFront Collective

WebFront Collective 是一个面向技术内容聚合与结构化导航的开源项目。它旨在解决技术文档、教程资源、行业资讯以及开发工具链中信息分散、检索效率低下的问题，通过建立统一的资源索引规范和轻量级元数据管理框架，帮助开发者、技术作者以及研究团队高效地组织和复用网络上的优质内容。本项目不提供爬虫或自动化采集功能，而是提供一套标准化的资源描述结构与静态站点生成工具，使用户能够以最低的维护成本构建私有的、可共享的技术外链知识库。

本项目定位于中小型技术团队、开源社区文档组以及个人知识管理爱好者。其核心输出为可静态部署的 HTML 索引页面，同时支持导出为 JSON 或 CSV 格式以供其他系统消费。通过批次化管理模式，本项目目前已完成第 105 至 240 批次的内容收录，总计涵盖超过 250 个经过人工筛选的技术资源链接。

## 功能概览

批次化资源导入：支持按批次组织资源条目，每批次可包含任意数量的 URL 及对应的标签与备注，便于追溯内容来源与更新周期。

多格式数据导出：内置模板引擎，可将资源列表渲染为响应式 HTML 文档，同时提供 JSON 和 CSV 格式的导出能力，满足不同应用场景的数据消费需求。

元数据扩展字段：每条资源记录除 URL 外，可附加标题、分类、重要性评分以及状态标记，方便用户构建个性化的筛选与排序视图。

静态站点生成：基于配置的目录结构与模板文件，一键生成完整的静态网站，包含索引页、分类页以及按时间排列的更新日志。

内容校验与去重：提供命令行工具对导入的资源列表进行格式校验、重复 URL 检测以及协议一致性检查，确保数据的准确性与规范性。

标签与分类管理：支持用户自定义标签体系与分类层级，可将不同批次的资源按主题进行归类，提升浏览与检索的体验。

增量更新机制：支持通过追加新批次的方式更新资源库，自动合并历史数据并重新生成输出文件，无需全量重建。

## 应用场景

技术文档团队整合碎片化参考链接：技术写作团队在编写产品文档时，需要引用大量外部规范、教程和 API 参考。使用 WebFront Collective 可以将这些零散的链接按主题批次集中管理，并在文档构建流程中自动生成统一的参考附录，减少手动维护链接列表的工作量。

开源项目维护 README 外链资源池：开源项目维护者通常需要在 README 或 Wiki 中列出相关生态项目、学习资料和社区论坛。通过本项目，维护者可以单独维护一个资源列表仓库，利用批次化更新功能定期同步最新资源，并自动生成格式化的 Markdown 引用块，避免频繁手动编辑文档。

技术研究团队构建领域知识导航：高校实验室或企业研究院的研究人员需要跟踪特定技术领域的最新动态。团队可将收集到的论文链接、博客文章、视频教程等按批次录入，利用分类与标签功能构建领域知识导航站，并导出为 JSON 格式供内部知识图谱系统调用。

个人开发者搭建定制化技术书签站：个人开发者可以将日常浏览中发现的优质技术文章、工具站点和在线课程通过本项目集中管理，利用静态站点生成功能部署到个人服务器或 GitHub Pages，形成长期可用的个人技术收藏夹，并支持按时间或分类回溯历史内容。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并运行首次构建。

```bash
# 克隆项目仓库
git clone https://github.com/webfront-collective/webfront-collective.git
cd webfront-collective

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行初次构建，生成静态站点到 output 目录
python build.py --batch 105-240 --output ./output
```

执行上述命令后，`./output` 目录下将生成包含所有资源索引的 `index.html` 文件以及对应的 `data.json` 和 `data.csv` 文件。您可以使用任意静态 HTTP 服务器预览结果，例如：

```bash
python -m http.server -d ./output 8080
```

访问 `http://localhost:8080` 即可查看生成的资源导航页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 项目核心运行环境，用于执行构建脚本与数据处理 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装 requirements.txt 中列出的依赖库 |
| Git | 2.30 及以上 | 用于克隆仓库以及后续通过 git pull 获取批次更新 |
| 操作系统 | Linux / macOS / Windows (WSL2) | 项目在主流操作系统上均通过测试，推荐使用 Linux 或 macOS 以获得最佳性能 |
| 磁盘空间 | 50 MB 以上 | 用于存储源码、资源索引缓存以及生成的静态文件 |
| 内存 | 1 GB 以上 | 构建过程主要消耗内存用于模板渲染和数据序列化，建议至少 1 GB 可用内存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速安装、配置并生成第一个静态资源导航页 |
| 批次管理 | docs/batch-management.md | 如何创建新批次、添加资源链接以及执行增量更新操作 |
| 模板定制 | docs/template-customization.md | 如何修改 HTML 模板样式、调整页面布局以及自定义导出格式 |
| 命令行参考 | docs/cli-reference.md | 详细解释 build.py 脚本的所有命令行参数及其使用示例 |

## 资源列表

- http://m.blog.fcful.cn/bnews/01267.htm
- http://m.blog.fcful.cn/bnews/7119.htm
- http://m.blog.fcful.cn/bnews/215104.htm
- http://m.blog.fcful.cn/bnews/24148.htm
- http://m.blog.fcful.cn/bnews/3922.htm
- http://m.blog.fcful.cn/bnews/6130172.htm
- http://m.blog.fcful.cn/bnews/47523.htm
- http://m.blog.fcful.cn/bnews/46998.htm
- http://m.blog.fcful.cn/bnews/01809.htm
- http://m.blog.fcful.cn/bnews/50640.htm
- http://m.blog.fcful.cn/bnews/737145.htm
- http://m.blog.fcful.cn/bnews/9807.htm
- http://m.blog.fcful.cn/bnews/5821.htm
- http://m.blog.fcful.cn/bnews/501456.htm
- http://m.blog.fcful.cn/bnews/3528679.htm
- http://m.blog.fcful.cn/bnews/7356039.htm
- http://m.blog.fcful.cn/bnews/2210.htm
- http://m.blog.fcful.cn/bnews/9961.htm
- http://m.blog.fcful.cn/bnews/2481819.htm
- http://m.blog.fcful.cn/bnews/0306298.htm
- http://m.blog.fcful.cn/bnews/3679495.htm
- http://m.blog.fcful.cn/bnews/50208.htm
- http://m.blog.fcful.cn/bnews/991476.htm
- http://m.blog.fcful.cn/bnews/7795533.htm
- http://m.blog.fcful.cn/bnews/2732753.htm
- http://m.blog.fcful.cn/bnews/42995.htm
- http://m.blog.fcful.cn/bnews/7513.htm
- http://m.blog.fcful.cn/bnews/276372.htm
- http://m.blog.fcful.cn/bnews/617142.htm
- http://m.blog.fcful.cn/bnews/45196.htm
- http://m.blog.fcful.cn/bnews/1149.htm
- http://m.blog.fcful.cn/bnews/666728.htm
- http://m.blog.fcful.cn/bnews/19152.htm
- http://m.blog.fcful.cn/bnews/6970249.htm
- http://m.blog.fcful.cn/bnews/05310.htm
- http://m.blog.fcful.cn/bnews/7563566.htm
- http://m.blog.fcful.cn/bnews/098133.htm
- http://m.blog.fcful.cn/bnews/5408678.htm
- http://m.blog.fcful.cn/bnews/74467.htm
- http://m.blog.fcful.cn/bnews/829566.htm
- http://m.blog.fcful.cn/bnews/1597399.htm
- http://m.blog.fcful.cn/bnews/373167.htm
- http://m.blog.fcful.cn/bnews/8431000.htm
- http://m.blog.fcful.cn/bnews/844192.htm
- http://m.blog.fcful.cn/bnews/572121.htm
- http://m.blog.fcful.cn/bnews/8910.htm
- http://m.blog.fcful.cn/bnews/0677198.htm
- http://m.blog.fcful.cn/bnews/71839.htm
- http://m.blog.fcful.cn/bnews/4517665.htm
- http://m.blog.fcful.cn/bnews/94588.htm
- http://m.blog.fcful.cn/bnews/02683.htm
- http://m.blog.fcful.cn/bnews/6686.htm
- http://m.blog.fcful.cn/bnews/694168.htm
- http://m.blog.fcful.cn/bnews/82445.htm
- http://m.blog.fcful.cn/bnews/5868120.htm
- http://m.blog.fcful.cn/bnews/39080.htm
- http://m.blog.fcful.cn/bnews/0974.htm
- http://m.blog.fcful.cn/bnews/5472154.htm
- http://m.blog.fcful.cn/bnews/28872.htm
- http://m.blog.fcful.cn/bnews/7249.htm
- http://m.blog.fcful.cn/bnews/5934.htm
- http://m.blog.fcful.cn/bnews/54714.htm
- http://m.blog.fcful.cn/bnews/8759.htm
- http://m.blog.fcful.cn/bnews/03563.htm
- http://m.blog.fcful.cn/bnews/4662007.htm
- http://m.blog.fcful.cn/bnews/1518339.htm
- http://m.blog.fcful.cn/bnews/8971.htm
- http://m.blog.fcful.cn/bnews/36210.htm
- http://m.blog.fcful.cn/bnews/23960.htm
- http://m.blog.fcful.cn/bnews/713679.htm
- http://m.blog.fcful.cn/bnews/084225.htm
- http://m.blog.fcful.cn/bnews/6540922.htm
- http://m.blog.fcful.cn/bnews/81348.htm
- http://m.blog.fcful.cn/bnews/7025.htm
- http://m.blog.fcful.cn/bnews/2125012.htm
- http://m.blog.fcful.cn/bnews/964706.htm
- http://m.blog.fcful.cn/bnews/09511.htm
- http://m.blog.fcful.cn/bnews/265842.htm
- http://m.blog.fcful.cn/bnews/4150.htm
- http://m.blog.fcful.cn/bnews/93380.htm
- http://m.blog.fcful.cn/bnews/81225.htm
- http://m.blog.fcful.cn/bnews/6559.htm
- http://m.blog.fcful.cn/bnews/0704.htm
- http://m.blog.fcful.cn/bnews/140622.htm
- http://m.blog.fcful.cn/bnews/735528.htm
- http://m.blog.fcful.cn/bnews/17463.htm
- http://m.blog.fcful.cn/bnews/8152786.htm
- http://m.blog.fcful.cn/bnews/27129.htm
- http://m.blog.fcful.cn/bnews/5754201.htm
- http://m.blog.fcful.cn/bnews/6428.htm
- http://m.blog.fcful.cn/bnews/129307.htm
- http://m.blog.fcful.cn/bnews/8432.htm
- http://m.blog.fcful.cn/bnews/00984.htm
- http://m.blog.fcful.cn/bnews/599662.htm
- http://m.blog.fcful.cn/bnews/2458807.htm
- http://m.blog.fcful.cn/bnews/20501.htm
- http://m.blog.fcful.cn/bnews/293916.htm
- http://m.blog.fcful.cn/bnews/8671584.htm
- http://m.blog.fcful.cn/bnews/1952.htm
- http://m.blog.fcful.cn/bnews/6387896.htm
- http://m.blog.fcful.cn/bnews/218546.htm
- http://m.blog.fcful.cn/bnews/90159.htm
- http://m.blog.fcful.cn/bnews/5295134.htm
- http://m.blog.fcful.cn/bnews/5466215.htm
- http://m.blog.fcful.cn/bnews/022799.htm
- http://m.blog.fcful.cn/bnews/63068.htm
- http://m.blog.fcful.cn/bnews/054179.htm
- http://m.blog.fcful.cn/bnews/54539.htm
- http://m.blog.fcful.cn/bnews/999214.htm
- http://m.blog.fcful.cn/bnews/3808.htm
- http://m.blog.fcful.cn/bnews/7112.htm
- http://m.blog.fcful.cn/bnews/974367.htm
- http://m.blog.fcful.cn/bnews/16463.htm
- http://m.blog.fcful.cn/bnews/3810829.htm
- http://m.blog.fcful.cn/bnews/832859.htm
- http://m.blog.fcful.cn/bnews/30385.htm
- http://m.blog.fcful.cn/bnews/513781.htm
- http://m.blog.fcful.cn/bnews/19236.htm
- http://m.blog.fcful.cn/bnews/331233.htm
- http://m.blog.fcful.cn/bnews/677738.htm
- http://m.blog.fcful.cn/bnews/0188396.htm
- http://m.blog.fcful.cn/bnews/6599.htm
- http://m.blog.fcful.cn/bnews/36143.htm
- http://m.blog.fcful.cn/bnews/773221.htm
- http://m.blog.fcful.cn/bnews/32840.htm
- http://m.blog.fcful.cn/bnews/2222.htm
- http://m.blog.fcful.cn/bnews/3015910.htm
- http://m.blog.fcful.cn/bnews/8181.htm
- http://m.blog.fcful.cn/bnews/8684859.htm
- http://m.blog.fcful.cn/bnews/606478.htm
- http://m.blog.fcful.cn/bnews/4858250.htm
- http://m.blog.fcful.cn/bnews/9682492.htm
- http://m.blog.fcful.cn/bnews/19386.htm
- http://m.blog.fcful.cn/bnews/092655.htm
- http://m.blog.fcful.cn/bnews/5113.htm
- http://m.blog.fcful.cn/bnews/48264.htm
- http://m.blog.fcful.cn/bnews/1839.htm
- http://m.blog.fcful.cn/bnews/5405350.htm
- http://m.blog.fcful.cn/bnews/8125.htm
- http://m.blog.fcful.cn/bnews/5435.htm
- http://m.blog.fcful.cn/bnews/2652050.htm
- http://m.blog.fcful.cn/bnews/1359.htm
- http://m.blog.fcful.cn/bnews/9965.htm
- http://m.blog.fcful.cn/bnews/5848353.htm
- http://m.blog.fcful.cn/bnews/734225.htm
- http://m.blog.fcful.cn/bnews/98466.htm
- http://m.blog.fcful.cn/bnews/9452.htm
- http://m.blog.fcful.cn/bnews/4711.htm
- http://m.blog.fcful.cn/bnews/44186.htm
- http://m.blog.fcful.cn/bnews/6202.htm
- http://m.blog.fcful.cn/bnews/0952.htm
- http://m.blog.fcful.cn/bnews/109772.htm
- http://m.blog.fcful.cn/bnews/7670.htm
- http://m.blog.fcful.cn/bnews/50055.htm
- http://m.blog.fcful.cn/bnews/226012.htm
- http://m.blog.fcful.cn/bnews/8689366.htm
- http://m.blog.fcful.cn/bnews/726895.htm
- http://m.blog.fcful.cn/bnews/628458.htm
- http://m.blog.fcful.cn/bnews/8440055.htm
- http://m.blog.fcful.cn/bnews/3686780.htm
- http://m.blog.fcful.cn/bnews/7323158.htm
- http://m.blog.fcful.cn/bnews/88718.htm
- http://m.blog.fcful.cn/bnews/9227.htm
- http://m.blog.fcful.cn/bnews/223138.htm
- http://m.blog.fcful.cn/bnews/45648.htm
- http://m.blog.fcful.cn/bnews/0995357.htm
- http://m.blog.fcful.cn/bnews/734301.htm
- http://m.blog.fcful.cn/bnews/067990.htm
- http://m.blog.fcful.cn/bnews/8542551.htm
- http://m.blog.fcful.cn/bnews/113075.htm
- http://m.blog.fcful.cn/bnews/7052183.htm
- http://m.blog.fcful.cn/bnews/1807.htm
- http://m.blog.fcful.cn/bnews/9367743.htm
- http://m.blog.fcful.cn/bnews/063309.htm
- http://m.blog.fcful.cn/bnews/945174.htm
- http://m.blog.fcful.cn/bnews/234894.htm
- http://m.blog.fcful.cn/bnews/5958615.htm
- http://m.blog.fcful.cn/bnews/710528.htm
- http://m.blog.fcful.cn/bnews/2781.htm
- http://m.blog.fcful.cn/bnews/8857079.htm
- http://m.blog.fcful.cn/bnews/829523.htm
- http://m.blog.fcful.cn/bnews/222463.htm
- http://m.blog.fcful.cn/bnews/342996.htm
- http://m.blog.fcful.cn/bnews/9193044.htm
- http://m.blog.fcful.cn/bnews/1565506.htm
- http://m.blog.fcful.cn/bnews/2352.htm
- http://m.blog.fcful.cn/bnews/1437.htm
- http://m.blog.fcful.cn/bnews/1345.htm
- http://m.blog.fcful.cn/bnews/180590.htm
- http://m.blog.fcful.cn/bnews/3383247.htm
- http://m.blog.fcful.cn/bnews/5257223.htm
- http://m.blog.fcful.cn/bnews/3880154.htm
- http://m.blog.fcful.cn/bnews/13558.htm
- http://m.blog.fcful.cn/bnews/114568.htm
- http://m.blog.fcful.cn/bnews/504035.htm
- http://m.blog.fcful.cn/bnews/8786557.htm
- http://m.blog.fcful.cn/bnews/5586350.htm
- http://m.blog.fcful.cn/bnews/225729.htm
- http://m.blog.fcful.cn/bnews/2749969.htm
- http://m.blog.fcful.cn/bnews/115898.htm
- http://m.blog.fcful.cn/bnews/66389.htm
- http://m.blog.fcful.cn/bnews/41404.htm
- http://m.blog.fcful.cn/bnews/309325.htm
- http://m.blog.fcful.cn/bnews/9925.htm
- http://m.blog.fcful.cn/bnews/39321.htm
- http://m.blog.fcful.cn/bnews/73544.htm
- http://m.blog.fcful.cn/bnews/00542.htm
- http://m.blog.fcful.cn/bnews/20619.htm
- http://m.blog.fcful.cn/bnews/42230.htm
- http://m.blog.fcful.cn/bnews/7948208.htm
- http://m.blog.fcful.cn/bnews/02690.htm
- http://m.blog.fcful.cn/bnews/211595.htm
- http://m.blog.fcful.cn/bnews/71107.htm
- http://m.blog.fcful.cn/bnews/228438.htm
- http://m.blog.fcful.cn/bnews/0346290.htm
- http://m.blog.fcful.cn/bnews/2574092.htm
- http://m.blog.fcful.cn/bnews/09493.htm
- http://m.blog.fcful.cn/bnews/9138330.htm
- http://m.blog.fcful.cn/bnews/7468630.htm
- http://m.blog.fcful.cn/bnews/16193.htm
- http://m.blog.fcful.cn/bnews/2819.htm
- http://m.blog.fcful.cn/bnews/7829.htm
- http://m.blog.fcful.cn/bnews/9152364.htm
- http://m.blog.fcful.cn/bnews/81670.htm
- http://m.blog.fcful.cn/bnews/9680.htm
- http://m.blog.fcful.cn/bnews/549614.htm
- http://m.blog.fcful.cn/bnews/23318.htm
- http://m.blog.fcful.cn/bnews/47532.htm
- http://m.blog.fcful.cn/bnews/423923.htm
- http://m.blog.fcful.cn/bnews/53112.htm
- http://m.blog.fcful.cn/bnews/822024.htm
- http://m.blog.fcful.cn/bnews/885713.htm
- http://m.blog.fcful.cn/bnews/700297.htm
- http://m.blog.fcful.cn/bnews/809506.htm
- http://m.blog.fcful.cn/bnews/121415.htm
- http://m.blog.fcful.cn/bnews/2481.htm
- http://m.blog.fcful.cn/bnews/72022.htm
- http://m.blog.fcful.cn/bnews/426104.htm
- http://m.blog.fcful.cn/bnews/9052.htm
- http://m.blog.fcful.cn/bnews/4211076.htm
- http://m.blog.fcful.cn/bnews/516499.htm
- http://m.blog.fcful.cn/bnews/5732700.htm
- http://m.blog.fcful.cn/bnews/7739.htm
- http://m.blog.fcful.cn/bnews/5904.htm
- http://m.blog.fcful.cn/bnews/8738218.htm
- http://m.blog.fcful.cn/bnews/33658.htm
- http://m.blog.fcful.cn/bnews/242693.htm
- http://m.blog.fcful.cn/bnews/0433.htm
- http://m.blog.fcful.cn/bnews/68977.htm
- http://m.blog.fcful.cn/bnews/6219.htm

## 项目结构

```
webfront-collective/
├── build.py                 # 主构建脚本，负责解析批次数据、渲染模板并输出静态文件
├── requirements.txt         # Python 依赖列表，包含 Jinja2、Markdown 和 click 等库
├── config.yaml              # 全局配置文件，定义站点标题、导出格式、分页大小等参数
├── data/
│   ├── batches/             # 按批次存放资源数据，每个批次为一个 JSON 文件
│   │   ├── batch_105_240.json   # 当前批次（105-240）的资源列表及元数据
│   │   └── batch_241_300.json   # 后续批次示例文件
│   ├── tags.json            # 全局标签定义及颜色映射
│   └── categories.json      # 分类层级结构定义
├── templates/
│   ├── base.html            # 基础 HTML 模板，包含头部、导航和底部公共区域
│   ├── index.html           # 资源索引页模板，循环渲染资源卡片列表
│   └── category.html        # 分类视图模板，按分类筛选并展示资源
├── output/                  # 构建输出目录（由 build.py 自动生成）
│   ├── index.html           # 生成的首页 HTML 文件
│   ├── data.json            # 所有资源的 JSON 格式导出
│   ├── data.csv             # 所有资源的 CSV 格式导出
│   └── assets/              # 静态资源目录（CSS、JS 文件）
│       ├── style.css
│       └── app.js
├── tests/                   # 单元测试与集成测试脚本
│   ├── test_parser.py       # 测试批次数据解析逻辑
│   └── test_renderer.py     # 测试模板渲染与输出一致性
├── docs/                    # 详细文档目录
│   ├── getting-started.md
│   ├── batch-management.md
│   ├── template-customization.md
│   └── cli-reference.md
└── LICENSE                  # MIT 许可证文件
```

## 贡献指南

提交资源推荐或改进建议：您可以通过 GitHub Issues 提交新的资源链接或对现有资源分类的调整建议。提交时请注明资源所属的批次编号以及简要的推荐理由，以便维护团队进行评估与合并。

完善项目文档与翻译：项目文档支持中英文双语。如果您发现文档中存在表述不清、错别字或希望增加新的使用示例，欢迎通过 Pull Request 提交修改。对于非中文内容的翻译贡献，请在 PR 描述中注明翻译对照。

开发新功能或修复缺陷：在开始较大规模的代码改动之前，建议先在 Issues 中创建讨论帖，说明您计划解决的问题或新增的功能点。获得维护者反馈后，请从 `main` 分支创建特性分支进行开发，并在 PR 中附上相关的测试用例。

优化模板样式与用户体验：如果您擅长前端设计，可以针对默认的 HTML 模板提出视觉改进方案。请确保样式修改在不同屏幕尺寸下均保持可用性，并附上修改前后的截图对比。

## 常见问题

构建过程中提示 "Batch ID format invalid" 应如何解决？

该错误通常表示您在命令行中传入的批次编号格式不符合预期。请确保使用 `--batch` 参数时，批次编号为数字范围或单个数字，例如 `105-240` 或 `105`。同时请检查 `data/batches/` 目录下是否存在对应的 JSON 文件。如果问题仍然存在，可以运行 `python build.py --list-batches` 查看当前可用的所有批次列表。

如何将导出的 JSON 数据导入到其他应用程序？

项目在每次构建时会在 `output/` 目录下生成 `data.json` 文件，该文件采用标准的 JSON 数组格式，每条记录包含 `url`、`title`、`category`、`tags` 和 `batch` 字段。您可以直接使用任何支持 JSON 解析的编程语言读取该文件，或利用 `data.csv` 文件导入到 Excel 或 Google Sheets 中进行进一步处理。

静态站点页面加载速度较慢，有无优化建议？

如果生成的 `index.html` 页面包含大量资源条目，可能导致首次加载时间较长。您可以在 `config.yaml` 中调整 `page_size` 参数启用分页功能，默认每页显示 50 条记录。同时建议使用 Nginx 或 Caddy 等高性能 HTTP 服务器部署输出目录，并开启 gzip 压缩以减小传输体积。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:23
