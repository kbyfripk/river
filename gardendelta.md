# WebIndex 聚合导航系统

WebIndex 是一个面向技术研究者和信息分析人员的轻量级外链聚合与导航系统。项目定位于将分散在多个来源的优质外链资源进行统一收集、分类存储与快速检索，帮助用户在信息过载环境中建立高效的知识获取通道。目标用户包括开源社区维护者、技术文档编写人员、网络安全研究人员以及日常需要处理大量外链信息的运营人员。

本系统不依赖数据库，采用纯静态文件存储结构，通过约定式目录分类与索引文件生成机制，实现对海量外链资源的有序管理。项目核心解决三个问题：外链散落难以追溯、分类标准不统一导致检索效率低下、以及团队协作时资源同步成本过高。WebIndex 通过扁平化的目录结构和自动化的索引更新流程，将上述问题收敛为可维护的技术方案。

## 功能概览

**多层级分类存储** 系统内置五级分类目录，涵盖技术文档、资讯快报、数据看板、工具资源与归档仓库，每一级目录均配有独立的索引清单文件，方便按类别浏览。

**自动索引生成** 每次新增资源链接后，通过脚本自动更新根目录与子目录下的索引文件，确保全站导航数据的实时一致性，无需手动编辑汇总列表。

**Markdown 原生渲染** 所有资源条目均以 Markdown 格式存储，与主流代码托管平台和文档站点兼容，支持在 GitHub、GitLab 或本地编辑器内直接预览。

**模糊检索支持** 内置基于文件名与分类标签的轻量级检索逻辑，用户可通过关键词匹配快速定位目标资源，检索范围覆盖全部已收录链接。

**导入导出接口** 提供标准化的 CSV 与 JSON 格式数据导入导出功能，便于与其他信息管理工具（如 Airtable、Notion、本地数据库）进行数据迁移或备份。

**版本追踪与审计** 依托底层版本控制系统，每次资源增删改操作均生成变更记录，支持回溯任意历史状态，满足团队协作下的操作审计需求。

**访问状态检测** 集成定时检测模块，可对已收录链接进行可达性检查，输出异常状态报告，辅助用户及时清理或更新失效资源。

**权限分级控制** 支持基于配置文件的读写权限分离，允许设置管理员与访客两种角色，访客仅拥有浏览与检索权限，管理员可执行资源管理操作。

## 应用场景

**技术文档团队的外链资产沉淀** 技术写作团队在撰写文档时需引用大量外部规范、API 参考和社区讨论帖。WebIndex 可作为团队内部的外链中转站，将散落在邮件、即时通讯和临时笔记中的链接统一收录，并按技术领域分类，减少重复查找时间。

**网络安全研究员的威胁情报整理** 安全研究人员每日需跟踪多个威胁情报源、漏洞公告和黑客论坛讨论帖。通过 WebIndex 的分类存储与状态检测功能，可快速建立个人化的威胁情报链接库，定期检测情报源可用性，确保应急响应时信息渠道畅通。

**开源项目社区的贡献导航** 开源项目维护者可利用 WebIndex 搭建社区贡献导航页，将代码仓库、设计稿、翻译平台、讨论区等资源统一列出，降低新贡献者的上手门槛。同时通过索引自动生成功能，确保导航页与资源实际变更保持同步。

**运营团队的活动素材汇总** 线上活动运营过程中需要收集报名表单、宣传物料、嘉宾简介、直播回放等多个外部链接。WebIndex 提供按时间线或活动主题维度的分类存储方案，运营人员可快速生成活动专属资源汇总页，提升内部协作效率。

**个人知识管理的信息入口整合** 知识管理爱好者可将 WebIndex 作为个人信息聚合入口，将常读的技术博客、在线课程、API 文档、数据源等链接统一管理，配合检索功能实现个人知识库的高速访问。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebIndex 服务。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git

# 进入项目目录
cd webindex

# 安装依赖（基于 Python 3.9+ 与 pip）
pip install -r requirements.txt

# 执行初始化构建，生成目录结构与索引文件
python build.py --init

# 启动本地开发服务器，默认监听 127.0.0.1:8080
python server.py --port 8080
```

执行完成后，使用浏览器访问 `http://127.0.0.1:8080` 即可进入系统主界面。如需导入用户提供的初始资源链接，可将链接列表保存为 `data/raw_links.txt` 后执行 `python import.py --source data/raw_links.txt`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高版本 | 核心运行环境，用于索引生成、服务器启动与检测脚本执行 |
| pip | 20.0 或更高版本 | Python 包管理工具，用于安装 requirements.txt 中声明的第三方库 |
| Git | 2.25 或更高版本 | 版本控制工具，用于克隆仓库以及后续的变更提交与回溯 |
| Markdown 解析库 | mistune 2.0+ | 用于将资源描述与分类信息渲染为 HTML 预览页 |
| 网络连接 | 稳定公网访问 | 用于首次启动时检查依赖更新，以及定时执行外链可达性检测任务 |
| 磁盘空间 | 至少 50 MB | 用于存储目录结构、索引文件及变更日志；实际占用随资源条目数线性增长 |
| 操作系统 | Linux / macOS / Windows (WSL2 推荐) | 跨平台支持，但生产部署建议使用 Linux 环境以获得最佳性能 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何快速完成安装并生成第一个资源索引页 |
| 分类规范 | docs/category_spec.md | 系统内置的五级分类定义、命名规则与扩展方法 |
| 脚本手册 | docs/scripts_reference.md | 各命令行工具（build、import、check、export）的参数说明与使用示例 |
| API 接口 | docs/api_endpoints.md | 服务端提供的 REST 风格查询接口、状态码含义与返回数据结构 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/7450.htm
- http://m.blog.gqskj.cn/nnews/82339.htm
- http://m.blog.gqskj.cn/nnews/57145.htm
- http://m.blog.gqskj.cn/nnews/99736.htm
- http://m.blog.gqskj.cn/nnews/9790475.htm
- http://m.blog.gqskj.cn/nnews/275506.htm
- http://m.blog.gqskj.cn/nnews/2721072.htm
- http://m.blog.gqskj.cn/nnews/7088885.htm
- http://m.blog.gqskj.cn/nnews/364749.htm
- http://m.blog.gqskj.cn/nnews/8254.htm
- http://m.blog.gqskj.cn/nnews/3260.htm
- http://m.blog.gqskj.cn/nnews/59234.htm
- http://m.blog.gqskj.cn/nnews/1517409.htm
- http://m.blog.gqskj.cn/nnews/662572.htm
- http://m.blog.gqskj.cn/nnews/996098.htm
- http://m.blog.gqskj.cn/nnews/156674.htm
- http://m.blog.gqskj.cn/nnews/71559.htm
- http://m.blog.gqskj.cn/nnews/5485190.htm
- http://m.blog.gqskj.cn/nnews/3557075.htm
- http://m.blog.gqskj.cn/nnews/71364.htm
- http://m.blog.gqskj.cn/nnews/28142.htm
- http://m.blog.gqskj.cn/nnews/48372.htm
- http://m.blog.gqskj.cn/nnews/89044.htm
- http://m.blog.gqskj.cn/nnews/5270.htm
- http://m.blog.gqskj.cn/nnews/48707.htm
- http://m.blog.gqskj.cn/nnews/01583.htm
- http://m.blog.gqskj.cn/nnews/3762.htm
- http://m.blog.gqskj.cn/nnews/013770.htm
- http://m.blog.gqskj.cn/nnews/6801.htm
- http://m.blog.gqskj.cn/nnews/959446.htm
- http://m.blog.gqskj.cn/nnews/47033.htm
- http://m.blog.gqskj.cn/nnews/705850.htm
- http://m.blog.gqskj.cn/nnews/0442.htm
- http://m.blog.gqskj.cn/nnews/9716551.htm
- http://m.blog.gqskj.cn/nnews/7990.htm
- http://m.blog.gqskj.cn/nnews/327540.htm
- http://m.blog.gqskj.cn/nnews/4272984.htm
- http://m.blog.gqskj.cn/nnews/002750.htm
- http://m.blog.gqskj.cn/nnews/06214.htm
- http://m.blog.gqskj.cn/nnews/40829.htm
- http://m.blog.gqskj.cn/nnews/7055.htm
- http://m.blog.gqskj.cn/nnews/16174.htm
- http://m.blog.gqskj.cn/nnews/141166.htm
- http://m.blog.gqskj.cn/nnews/936603.htm
- http://m.blog.gqskj.cn/nnews/1994.htm
- http://m.blog.gqskj.cn/nnews/521658.htm
- http://m.blog.gqskj.cn/nnews/5092168.htm
- http://m.blog.gqskj.cn/nnews/33055.htm
- http://m.blog.gqskj.cn/nnews/5611.htm
- http://m.blog.gqskj.cn/nnews/377590.htm
- http://m.blog.gqskj.cn/nnews/8627043.htm
- http://m.blog.gqskj.cn/nnews/6889298.htm
- http://m.blog.gqskj.cn/nnews/5127.htm
- http://m.blog.gqskj.cn/nnews/7901.htm
- http://m.blog.gqskj.cn/nnews/8858.htm
- http://m.blog.gqskj.cn/nnews/89684.htm
- http://m.blog.gqskj.cn/nnews/26912.htm
- http://m.blog.gqskj.cn/nnews/705318.htm
- http://m.blog.gqskj.cn/nnews/54956.htm
- http://m.blog.gqskj.cn/nnews/0601662.htm
- http://m.blog.gqskj.cn/nnews/888307.htm
- http://m.blog.gqskj.cn/nnews/1308115.htm
- http://m.blog.gqskj.cn/nnews/8291.htm
- http://m.blog.gqskj.cn/nnews/04384.htm
- http://m.blog.gqskj.cn/nnews/3193.htm
- http://m.blog.gqskj.cn/nnews/24207.htm
- http://m.blog.gqskj.cn/nnews/8976.htm
- http://m.blog.gqskj.cn/nnews/9148.htm
- http://m.blog.gqskj.cn/nnews/5977.htm
- http://m.blog.gqskj.cn/nnews/90226.htm
- http://m.blog.gqskj.cn/nnews/8450.htm
- http://m.blog.gqskj.cn/nnews/9818.htm
- http://m.blog.gqskj.cn/nnews/8087.htm
- http://m.blog.gqskj.cn/nnews/4583180.htm
- http://m.blog.gqskj.cn/nnews/98149.htm
- http://m.blog.gqskj.cn/nnews/3706.htm
- http://m.blog.gqskj.cn/nnews/7240174.htm
- http://m.blog.gqskj.cn/nnews/954074.htm
- http://m.blog.gqskj.cn/nnews/3989.htm
- http://m.blog.gqskj.cn/nnews/9727084.htm
- http://m.blog.gqskj.cn/nnews/0749.htm
- http://m.blog.gqskj.cn/nnews/1017408.htm
- http://m.blog.gqskj.cn/nnews/0704.htm
- http://m.blog.gqskj.cn/nnews/7800490.htm
- http://m.blog.gqskj.cn/nnews/98406.htm
- http://m.blog.gqskj.cn/nnews/483304.htm
- http://m.blog.gqskj.cn/nnews/46845.htm
- http://m.blog.gqskj.cn/nnews/0988748.htm
- http://m.blog.gqskj.cn/nnews/2594280.htm
- http://m.blog.gqskj.cn/nnews/0990.htm
- http://m.blog.gqskj.cn/nnews/133356.htm
- http://m.blog.gqskj.cn/nnews/461923.htm
- http://m.blog.gqskj.cn/nnews/03621.htm
- http://m.blog.gqskj.cn/nnews/178537.htm
- http://m.blog.gqskj.cn/nnews/4400066.htm
- http://m.blog.gqskj.cn/nnews/485012.htm
- http://m.blog.gqskj.cn/nnews/9754089.htm
- http://m.blog.gqskj.cn/nnews/1770828.htm
- http://m.blog.gqskj.cn/nnews/6359.htm
- http://m.blog.gqskj.cn/nnews/296171.htm
- http://m.blog.gqskj.cn/nnews/71845.htm
- http://m.blog.gqskj.cn/nnews/38328.htm
- http://m.blog.gqskj.cn/nnews/836878.htm
- http://m.blog.gqskj.cn/nnews/98633.htm
- http://m.blog.gqskj.cn/nnews/140453.htm
- http://m.blog.gqskj.cn/nnews/56774.htm
- http://m.blog.gqskj.cn/nnews/3702456.htm
- http://m.blog.gqskj.cn/nnews/546832.htm
- http://m.blog.gqskj.cn/nnews/8982044.htm
- http://m.blog.gqskj.cn/nnews/71328.htm
- http://m.blog.gqskj.cn/nnews/351181.htm
- http://m.blog.gqskj.cn/nnews/1051.htm
- http://m.blog.gqskj.cn/nnews/755082.htm
- http://m.blog.gqskj.cn/nnews/845664.htm
- http://m.blog.gqskj.cn/nnews/7592.htm
- http://m.blog.gqskj.cn/nnews/04819.htm
- http://m.blog.gqskj.cn/nnews/35109.htm
- http://m.blog.gqskj.cn/nnews/419190.htm
- http://m.blog.gqskj.cn/nnews/48046.htm
- http://m.blog.gqskj.cn/nnews/3344.htm
- http://m.blog.gqskj.cn/nnews/8869.htm
- http://m.blog.gqskj.cn/nnews/4603791.htm
- http://m.blog.gqskj.cn/nnews/640103.htm
- http://m.blog.gqskj.cn/nnews/835042.htm
- http://m.blog.gqskj.cn/nnews/073371.htm
- http://m.blog.gqskj.cn/nnews/32657.htm
- http://m.blog.gqskj.cn/nnews/469132.htm
- http://m.blog.gqskj.cn/nnews/008318.htm
- http://m.blog.gqskj.cn/nnews/00300.htm
- http://m.blog.gqskj.cn/nnews/7987.htm
- http://m.blog.gqskj.cn/nnews/8033853.htm
- http://m.blog.gqskj.cn/nnews/51340.htm
- http://m.blog.gqskj.cn/nnews/7011444.htm
- http://m.blog.gqskj.cn/nnews/484709.htm
- http://m.blog.gqskj.cn/nnews/44511.htm
- http://m.blog.gqskj.cn/nnews/368130.htm
- http://m.blog.gqskj.cn/nnews/9940734.htm
- http://m.blog.gqskj.cn/nnews/6334203.htm
- http://m.blog.gqskj.cn/nnews/304942.htm
- http://m.blog.gqskj.cn/nnews/1354898.htm
- http://m.blog.gqskj.cn/nnews/0131.htm
- http://m.blog.gqskj.cn/nnews/5983249.htm
- http://m.blog.gqskj.cn/nnews/5651629.htm
- http://m.blog.gqskj.cn/nnews/5094394.htm
- http://m.blog.gqskj.cn/nnews/7603686.htm
- http://m.blog.gqskj.cn/nnews/9852700.htm
- http://m.blog.gqskj.cn/nnews/048840.htm
- http://m.blog.gqskj.cn/nnews/6622032.htm
- http://m.blog.gqskj.cn/nnews/158629.htm
- http://m.blog.gqskj.cn/nnews/2636125.htm
- http://m.blog.gqskj.cn/nnews/028958.htm
- http://m.blog.gqskj.cn/nnews/25290.htm
- http://m.blog.gqskj.cn/nnews/7181.htm
- http://m.blog.gqskj.cn/nnews/7162922.htm
- http://m.blog.gqskj.cn/nnews/50013.htm
- http://m.blog.gqskj.cn/nnews/18196.htm
- http://m.blog.gqskj.cn/nnews/4419883.htm
- http://m.blog.gqskj.cn/nnews/4596513.htm
- http://m.blog.gqskj.cn/nnews/74646.htm
- http://m.blog.gqskj.cn/nnews/4144308.htm
- http://m.blog.gqskj.cn/nnews/4166521.htm
- http://m.blog.gqskj.cn/nnews/3482893.htm
- http://m.blog.gqskj.cn/nnews/132759.htm
- http://m.blog.gqskj.cn/nnews/5020399.htm
- http://m.blog.gqskj.cn/nnews/398383.htm
- http://m.blog.gqskj.cn/nnews/15902.htm
- http://m.blog.gqskj.cn/nnews/699976.htm
- http://m.blog.gqskj.cn/nnews/601100.htm
- http://m.blog.gqskj.cn/nnews/2374160.htm
- http://m.blog.gqskj.cn/nnews/864494.htm
- http://m.blog.gqskj.cn/nnews/3370688.htm
- http://m.blog.gqskj.cn/nnews/9589077.htm
- http://m.blog.gqskj.cn/nnews/7364.htm
- http://m.blog.gqskj.cn/nnews/3015151.htm
- http://m.blog.gqskj.cn/nnews/047130.htm
- http://m.blog.gqskj.cn/nnews/02596.htm
- http://m.blog.gqskj.cn/nnews/66789.htm
- http://m.blog.gqskj.cn/nnews/62824.htm
- http://m.blog.gqskj.cn/nnews/200912.htm
- http://m.blog.gqskj.cn/nnews/4019.htm
- http://m.blog.gqskj.cn/nnews/17910.htm
- http://m.blog.gqskj.cn/nnews/6444743.htm
- http://m.blog.gqskj.cn/nnews/6757.htm
- http://m.blog.gqskj.cn/nnews/26720.htm
- http://m.blog.gqskj.cn/nnews/50826.htm
- http://m.blog.gqskj.cn/nnews/24971.htm
- http://m.blog.gqskj.cn/nnews/855982.htm
- http://m.blog.gqskj.cn/nnews/16816.htm
- http://m.blog.gqskj.cn/nnews/688871.htm
- http://m.blog.gqskj.cn/nnews/286779.htm
- http://m.blog.gqskj.cn/nnews/1946.htm
- http://m.blog.gqskj.cn/nnews/81747.htm
- http://m.blog.gqskj.cn/nnews/9698.htm
- http://m.blog.gqskj.cn/nnews/096104.htm
- http://m.blog.gqskj.cn/nnews/58150.htm
- http://m.blog.gqskj.cn/nnews/2901146.htm
- http://m.blog.gqskj.cn/nnews/980030.htm
- http://m.blog.gqskj.cn/nnews/13588.htm
- http://m.blog.gqskj.cn/nnews/017963.htm
- http://m.blog.gqskj.cn/nnews/839422.htm
- http://m.blog.gqskj.cn/nnews/2092.htm
- http://m.blog.gqskj.cn/nnews/9745.htm
- http://m.blog.gqskj.cn/nnews/278529.htm
- http://m.blog.gqskj.cn/nnews/7725.htm
- http://m.blog.gqskj.cn/nnews/1022776.htm
- http://m.blog.gqskj.cn/nnews/160252.htm
- http://m.blog.gqskj.cn/nnews/876330.htm
- http://m.blog.gqskj.cn/nnews/520109.htm
- http://m.blog.gqskj.cn/nnews/5497.htm
- http://m.blog.gqskj.cn/nnews/423416.htm
- http://m.blog.gqskj.cn/nnews/487687.htm
- http://m.blog.gqskj.cn/nnews/4272.htm
- http://m.blog.gqskj.cn/nnews/6781232.htm
- http://m.blog.gqskj.cn/nnews/379384.htm
- http://m.blog.gqskj.cn/nnews/95113.htm
- http://m.blog.gqskj.cn/nnews/73437.htm
- http://m.blog.gqskj.cn/nnews/4713.htm
- http://m.blog.gqskj.cn/nnews/397632.htm
- http://m.blog.gqskj.cn/nnews/6666322.htm
- http://m.blog.gqskj.cn/nnews/3104929.htm
- http://m.blog.gqskj.cn/nnews/915384.htm
- http://m.blog.gqskj.cn/nnews/92294.htm
- http://m.blog.gqskj.cn/nnews/2498115.htm
- http://m.blog.gqskj.cn/nnews/59919.htm
- http://m.blog.gqskj.cn/nnews/93706.htm
- http://m.blog.gqskj.cn/nnews/5135.htm
- http://m.blog.gqskj.cn/nnews/432857.htm
- http://m.blog.gqskj.cn/nnews/3024559.htm
- http://m.blog.gqskj.cn/nnews/445904.htm
- http://m.blog.gqskj.cn/nnews/5700.htm
- http://m.blog.gqskj.cn/nnews/5139757.htm
- http://m.blog.gqskj.cn/nnews/284414.htm
- http://m.blog.gqskj.cn/nnews/5504.htm
- http://m.blog.gqskj.cn/nnews/811925.htm
- http://m.blog.gqskj.cn/nnews/1791417.htm
- http://m.blog.gqskj.cn/nnews/9196513.htm
- http://m.blog.gqskj.cn/nnews/5225379.htm
- http://m.blog.gqskj.cn/nnews/6915632.htm
- http://m.blog.gqskj.cn/nnews/41367.htm
- http://m.blog.gqskj.cn/nnews/2745579.htm
- http://m.blog.gqskj.cn/nnews/568874.htm
- http://m.blog.gqskj.cn/nnews/9720.htm
- http://m.blog.gqskj.cn/nnews/0418081.htm
- http://m.blog.gqskj.cn/nnews/1158626.htm
- http://m.blog.gqskj.cn/nnews/6214.htm
- http://m.blog.gqskj.cn/nnews/994132.htm
- http://m.blog.gqskj.cn/nnews/111489.htm
- http://m.blog.gqskj.cn/nnews/383082.htm
- http://m.blog.gqskj.cn/nnews/4384162.htm
- http://m.blog.gqskj.cn/nnews/104938.htm

## 项目结构

```
webindex/
├── build.py                 # 主构建脚本，负责生成索引文件和目录树
├── server.py                # 轻量级 HTTP 服务，提供本地预览与检索接口
├── import.py                # 批量导入工具，支持从文本文件读取链接并分类
├── check.py                 # 外链可达性检测脚本，输出健康报告
├── export.py                # 数据导出工具，支持 CSV / JSON 格式输出
├── requirements.txt         # Python 依赖清单
├── config.yaml              # 系统配置文件，含端口、分类映射、权限等设定
├── data/                    # 数据存储根目录
│   ├── raw_links.txt        # 原始链接导入缓存文件
│   ├── index.json           # 全局索引主文件，记录所有条目的元数据
│   └── changelog.log        # 操作审计日志，记录每次增删改及时间戳
├── categories/              # 分类目录根节点
│   ├── tech/                # 技术文档类（含 API 手册、架构设计、开发规范等）
│   ├── news/                # 资讯快报类（含行业动态、版本发布、安全通告等）
│   ├── dashboard/           # 数据看板类（含实时监控、统计报表、可视化大屏等）
│   ├── tools/               # 工具资源类（含在线编辑器、调试工具、性能分析等）
│   └── archive/             # 归档仓库类（含历史版本、过时参考、备份链接等）
├── scripts/                 # 辅助脚本集合
│   ├── gen_toc.py           # 自动生成每个分类目录下的 TOC 索引文件
│   ├── dedup.py             # 链接去重工具，基于 URL 哈希对比
│   └── migrate.py           # 分类迁移工具，支持批量调整资源所属目录
├── templates/               # HTML 渲染模板目录
│   ├── base.html            # 基础页面框架
│   ├── index.html           # 首页模板，展示分类概览与检索入口
│   └── detail.html          # 详情页模板，展示单条资源的完整信息
├── static/                  # 静态资源目录
│   ├── style.css            # 全局样式表
│   └── app.js               # 前端交互逻辑（检索、过滤、分页）
└── tests/                   # 单元测试与集成测试目录
    ├── test_build.py
    ├── test_import.py
    └── test_check.py
```

## 贡献指南

1. 在 GitHub 上 Fork 本项目仓库，并克隆到本地开发环境。请确保本地 Python 版本与项目要求一致，建议使用虚拟环境隔离依赖。

2. 新建功能分支或修复分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。所有代码变更需附带对应的单元测试，测试文件放置在 `tests/` 目录下。

3. 提交代码前执行 `python check.py --precommit` 进行基础检查，包括语法规范、索引文件完整性以及链接格式校验。检查通过后方可提交。

4. 提交 Pull Request 时请填写标准模板，说明变更动机、实现方案以及影响范围。PR 描述中需附带执行 `build.py` 后的索引生成日志截图，以证明构建流程未受破坏。

5. 项目维护者将在 3 个工作日内进行 Review。如需修改，请及时更新分支并回复评论。合并后您的贡献将被记录在 `CONTRIBUTORS.md` 文件中。

## 常见问题

**问：系统能够处理的最大链接数量是多少？**

答：在纯静态存储模式下，系统性能主要受限于文件系统的目录项数量和单个索引文件的解析开销。实际测试中，单目录下存储 5000 条链接仍可保持索引生成时间在 2 秒以内。建议按分类子目录分散存储，每个子目录不超过 2000 条。如需存储更大规模的数据，可考虑启用分片存储模式，该模式在 `config.yaml` 中通过 `shard_size` 参数开启。

**问：导入链接后索引文件没有自动更新怎么办？**

答：首先确认是否执行了 `build.py` 脚本。该脚本不会自动触发，需在每次导入或手动增删后主动运行。若已执行但仍未更新，请检查 `data/index.json` 的文件写入权限。在 Linux 环境下常见于目录权限设置为只读，执行 `chmod 664 data/index.json` 可解决。如果问题仍然存在，可查看 `data/changelog.log` 中的错误堆栈信息定位具体原因。

**问：如何将系统部署到公网环境供团队使用？**

答：项目内置的 `server.py` 适用于开发测试，不建议直接用于生产环境。推荐使用 Gunicorn 或 uWSGI 作为 WSGI 服务器，并搭配 Nginx 进行反向代理。具体部署模板参见 `docs/deployment.md`。若需启用 HTTPS，可配置 Nginx 的 SSL 证书路径，并将 `config.yaml` 中的 `force_https` 开关设置为 `true`。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:41
