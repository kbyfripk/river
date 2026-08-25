# WebIndex 轻量级外链资源聚合站

WebIndex 是一个面向技术内容聚合与快速访问的轻量级外链资源索引项目。项目定位为技术团队、个人开发者与内容研究者的外链资源汇总工具，用于集中管理分散在多个来源的新闻、技术文档、行业动态与参考链接。项目不提供内容存储或代理转发，仅作为结构化索引层，将原始 URL 按照批次与分类规则进行归集，便于使用者进行批量访问、内容筛选与长期存档。

目标用户包括运维工程师、技术调研人员、数据采集工程师以及需要定期跟进大量外链资源的项目管理者。WebIndex 解决的核心问题是外链分散、缺乏统一入口、难以追溯批次来源以及手动整理效率低下的痛点，通过标准化目录结构与批次标识，使每个资源链接在项目中具有明确的坐标与上下文。

## 功能概览

批量外链导入与解析 项目支持按批次导入原始 URL 列表，自动完成格式校验与重复检测，生成批次编号与导入时间戳，确保每一批资源可追溯。

结构化目录树生成 根据资源来源域名与路径层级，自动生成多级目录树视图，便于快速定位特定来源或特定路径前缀下的所有链接。

资源状态标记与筛选 为每个链接提供未读、已读、待归档、已失效四种状态标记，支持按状态过滤输出视图，适配不同工作阶段的使用需求。

元信息自动补全 通过可配置的请求头与超时策略，对导入的 URL 执行轻量级 HEAD 请求，自动补全资源类型、最后修改时间与内容长度，辅助后续内容分类。

批次报告导出 每个批次支持生成 Markdown 与 CSV 两种格式的汇总报告，包含链接总数、有效数、失效数、域名分布与状态统计，便于存档或分享。

搜索与快速跳转 内置基于链接路径与编号的模糊搜索功能，支持按编号段、域名关键字、状态组合进行检索，结果支持一键复制完整 URL。

配置持久化与多环境支持 项目配置文件采用 YAML 格式，支持开发、测试、生产三套环境变量覆盖，便于在不同部署环境下保持一致的资源索引行为。

## 应用场景

技术文档归档与团队共享 技术团队在日常调研中收集大量外部参考链接，包括官方文档、社区讨论、技术博客与视频教程。使用 WebIndex 按批次导入后，团队成员可通过统一的项目仓库获取最新资源索引，避免链接散落在聊天记录或邮件中。

数据采集任务的前置资源准备 数据采集工程师在启动采集任务前，需要整理一批目标来源 URL 并进行可用性预检。WebIndex 的批量导入与状态标记功能可快速完成资源筛选，将失效链接提前剔除，减少采集任务中的异常中断。

个人知识库的外链补充层 个人知识库通常以笔记或文档为主，外链资源分散在多个笔记文件中，难以统一维护。WebIndex 作为独立的索引层，按时间批次组织外链，并与笔记系统通过链接编号建立引用关系，提升知识库的完整性与可维护性。

合规审查与链接生命周期管理 内容合规团队需要定期审查对外引用链接的有效性与内容合规性。WebIndex 提供状态标记与导出报告，支持按批次导出待审查链接列表，审查完成后批量更新状态，形成闭环管理。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装项目依赖（Python 3.9+ 环境）
pip install -r requirements.txt

# 运行导入脚本，将用户提供的 URL 列表导入为第 159/240 批次
python scripts/import_batch.py --batch 159 --source data/urls_batch_159.txt

# 启动本地预览服务
python app.py --port 8080

# 生成批次报告
python scripts/export_report.py --batch 159 --format markdown --output reports/batch_159.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 至 3.11 | 项目核心运行环境，3.12 及以上版本暂未进行充分测试 |
| pip | 21.0 以上 | Python 包管理器，用于安装项目依赖 |
| Git | 2.25 以上 | 用于克隆仓库与版本管理 |
| 网络连接 | 稳定出站 | 执行 HEAD 请求补全元信息时需要访问外链域名 |
| 磁盘空间 | 至少 50 MB | 用于存储索引文件、日志与导出报告 |
| 操作系统 | Linux / macOS / Windows WSL | 生产环境推荐 Linux 内核 4.0 以上 |
| make | 3.81 以上 | 可选，用于执行自动化任务脚本 |
| curl | 7.68 以上 | 可选，用于外部健康检查脚本 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user_guide.md | 如何导入批次、管理状态、导出报告以及配置环境变量 |
| 开发者指南 | docs/developer_guide.md | 项目架构、核心模块说明、自定义解析器扩展方式 |
| 运维部署 | docs/deployment.md | 生产环境部署步骤、日志配置、健康检查与备份策略 |
| 常见工作流 | docs/workflows.md | 按角色和场景划分的典型操作流程，包括团队协作与单人维护模式 |
| API 参考 | docs/api_reference.md | 导入接口、搜索接口、报告生成接口的参数说明与返回格式 |
| 变更日志 | CHANGELOG.md | 各版本的功能新增、修复与已知问题记录 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/1938028.htm
- http://m.3g.gqskj.cn/xnews/615673.htm
- http://m.3g.gqskj.cn/xnews/06123.htm
- http://m.3g.gqskj.cn/xnews/842386.htm
- http://m.3g.gqskj.cn/xnews/8976.htm
- http://m.3g.gqskj.cn/xnews/4575546.htm
- http://m.3g.gqskj.cn/xnews/8516.htm
- http://m.3g.gqskj.cn/xnews/2284445.htm
- http://m.3g.gqskj.cn/xnews/837561.htm
- http://m.3g.gqskj.cn/xnews/1626.htm
- http://m.3g.gqskj.cn/xnews/05644.htm
- http://m.3g.gqskj.cn/xnews/4388215.htm
- http://m.3g.gqskj.cn/xnews/6206.htm
- http://m.3g.gqskj.cn/xnews/9941.htm
- http://m.3g.gqskj.cn/xnews/3696.htm
- http://m.3g.gqskj.cn/xnews/8391.htm
- http://m.3g.gqskj.cn/xnews/4019.htm
- http://m.3g.gqskj.cn/xnews/50407.htm
- http://m.3g.gqskj.cn/xnews/8200.htm
- http://m.3g.gqskj.cn/xnews/07606.htm
- http://m.3g.gqskj.cn/xnews/224414.htm
- http://m.3g.gqskj.cn/xnews/62413.htm
- http://m.3g.gqskj.cn/xnews/61439.htm
- http://m.3g.gqskj.cn/xnews/536865.htm
- http://m.3g.gqskj.cn/xnews/3391513.htm
- http://m.3g.gqskj.cn/xnews/2991.htm
- http://m.3g.gqskj.cn/xnews/77708.htm
- http://m.3g.gqskj.cn/xnews/3275.htm
- http://m.3g.gqskj.cn/xnews/55696.htm
- http://m.3g.gqskj.cn/xnews/540393.htm
- http://m.3g.gqskj.cn/xnews/6025.htm
- http://m.3g.gqskj.cn/xnews/7881.htm
- http://m.3g.gqskj.cn/xnews/7213256.htm
- http://m.3g.gqskj.cn/xnews/665741.htm
- http://m.3g.gqskj.cn/xnews/8728.htm
- http://m.3g.gqskj.cn/xnews/781179.htm
- http://m.3g.gqskj.cn/xnews/123020.htm
- http://m.3g.gqskj.cn/xnews/87440.htm
- http://m.3g.gqskj.cn/xnews/34589.htm
- http://m.3g.gqskj.cn/xnews/210459.htm
- http://m.3g.gqskj.cn/xnews/383089.htm
- http://m.3g.gqskj.cn/xnews/043012.htm
- http://m.3g.gqskj.cn/xnews/6896.htm
- http://m.3g.gqskj.cn/xnews/867784.htm
- http://m.3g.gqskj.cn/xnews/482731.htm
- http://m.3g.gqskj.cn/xnews/328721.htm
- http://m.3g.gqskj.cn/xnews/68606.htm
- http://m.3g.gqskj.cn/xnews/2343.htm
- http://m.3g.gqskj.cn/xnews/753914.htm
- http://m.3g.gqskj.cn/xnews/9365.htm
- http://m.3g.gqskj.cn/xnews/4901127.htm
- http://m.3g.gqskj.cn/xnews/0557.htm
- http://m.3g.gqskj.cn/xnews/737509.htm
- http://m.3g.gqskj.cn/xnews/93007.htm
- http://m.3g.gqskj.cn/xnews/339750.htm
- http://m.3g.gqskj.cn/xnews/3174410.htm
- http://m.3g.gqskj.cn/xnews/595691.htm
- http://m.3g.gqskj.cn/xnews/6607.htm
- http://m.3g.gqskj.cn/xnews/115895.htm
- http://m.3g.gqskj.cn/xnews/16254.htm
- http://m.3g.gqskj.cn/xnews/74508.htm
- http://m.3g.gqskj.cn/xnews/715498.htm
- http://m.3g.gqskj.cn/xnews/50483.htm
- http://m.3g.gqskj.cn/xnews/427747.htm
- http://m.3g.gqskj.cn/xnews/37349.htm
- http://m.3g.gqskj.cn/xnews/7557807.htm
- http://m.3g.gqskj.cn/xnews/5337.htm
- http://m.3g.gqskj.cn/xnews/150914.htm
- http://m.3g.gqskj.cn/xnews/1125607.htm
- http://m.3g.gqskj.cn/xnews/3744.htm
- http://m.3g.gqskj.cn/xnews/552433.htm
- http://m.3g.gqskj.cn/xnews/4690502.htm
- http://m.3g.gqskj.cn/xnews/8164383.htm
- http://m.3g.gqskj.cn/xnews/6536.htm
- http://m.3g.gqskj.cn/xnews/6465568.htm
- http://m.3g.gqskj.cn/xnews/750716.htm
- http://m.3g.gqskj.cn/xnews/8503532.htm
- http://m.3g.gqskj.cn/xnews/48835.htm
- http://m.3g.gqskj.cn/xnews/4479.htm
- http://m.3g.gqskj.cn/xnews/0521017.htm
- http://m.3g.gqskj.cn/xnews/23765.htm
- http://m.3g.gqskj.cn/xnews/19023.htm
- http://m.3g.gqskj.cn/xnews/6050.htm
- http://m.3g.gqskj.cn/xnews/79238.htm
- http://m.3g.gqskj.cn/xnews/04713.htm
- http://m.3g.gqskj.cn/xnews/2736.htm
- http://m.3g.gqskj.cn/xnews/921460.htm
- http://m.3g.gqskj.cn/xnews/287542.htm
- http://m.3g.gqskj.cn/xnews/4532103.htm
- http://m.3g.gqskj.cn/xnews/631356.htm
- http://m.3g.gqskj.cn/xnews/617576.htm
- http://m.3g.gqskj.cn/xnews/00725.htm
- http://m.3g.gqskj.cn/xnews/3929439.htm
- http://m.3g.gqskj.cn/xnews/0973.htm
- http://m.3g.gqskj.cn/xnews/44183.htm
- http://m.3g.gqskj.cn/xnews/44565.htm
- http://m.3g.gqskj.cn/xnews/607606.htm
- http://m.3g.gqskj.cn/xnews/2062.htm
- http://m.3g.gqskj.cn/xnews/7697384.htm
- http://m.3g.gqskj.cn/xnews/68056.htm
- http://m.3g.gqskj.cn/xnews/49197.htm
- http://m.3g.gqskj.cn/xnews/62163.htm
- http://m.3g.gqskj.cn/xnews/1664.htm
- http://m.3g.gqskj.cn/xnews/5903769.htm
- http://m.3g.gqskj.cn/xnews/7273.htm
- http://m.3g.gqskj.cn/xnews/34717.htm
- http://m.3g.gqskj.cn/xnews/9389085.htm
- http://m.3g.gqskj.cn/xnews/930134.htm
- http://m.3g.gqskj.cn/xnews/82958.htm
- http://m.3g.gqskj.cn/xnews/1703.htm
- http://m.3g.gqskj.cn/xnews/270264.htm
- http://m.3g.gqskj.cn/xnews/05655.htm
- http://m.3g.gqskj.cn/xnews/67870.htm
- http://m.3g.gqskj.cn/xnews/4489419.htm
- http://m.3g.gqskj.cn/xnews/39977.htm
- http://m.3g.gqskj.cn/xnews/0252.htm
- http://m.3g.gqskj.cn/xnews/96525.htm
- http://m.3g.gqskj.cn/xnews/00490.htm
- http://m.3g.gqskj.cn/xnews/28172.htm
- http://m.3g.gqskj.cn/xnews/492168.htm
- http://m.3g.gqskj.cn/xnews/86925.htm
- http://m.3g.gqskj.cn/xnews/8812640.htm
- http://m.3g.gqskj.cn/xnews/5431985.htm
- http://m.3g.gqskj.cn/xnews/49172.htm
- http://m.3g.gqskj.cn/xnews/73108.htm
- http://m.3g.gqskj.cn/xnews/989703.htm
- http://m.3g.gqskj.cn/xnews/9594.htm
- http://m.3g.gqskj.cn/xnews/1492572.htm
- http://m.3g.gqskj.cn/xnews/4406677.htm
- http://m.3g.gqskj.cn/xnews/8590384.htm
- http://m.3g.gqskj.cn/xnews/2653818.htm
- http://m.3g.gqskj.cn/xnews/82542.htm
- http://m.3g.gqskj.cn/xnews/717947.htm
- http://m.3g.gqskj.cn/xnews/5895.htm
- http://m.3g.gqskj.cn/xnews/03503.htm
- http://m.3g.gqskj.cn/xnews/50140.htm
- http://m.3g.gqskj.cn/xnews/9604.htm
- http://m.3g.gqskj.cn/xnews/073419.htm
- http://m.3g.gqskj.cn/xnews/64327.htm
- http://m.3g.gqskj.cn/xnews/371546.htm
- http://m.3g.gqskj.cn/xnews/0851.htm
- http://m.3g.gqskj.cn/xnews/5456680.htm
- http://m.3g.gqskj.cn/xnews/3254.htm
- http://m.3g.gqskj.cn/xnews/8645748.htm
- http://m.3g.gqskj.cn/xnews/4238751.htm
- http://m.3g.gqskj.cn/xnews/3008020.htm
- http://m.3g.gqskj.cn/xnews/43595.htm
- http://m.3g.gqskj.cn/xnews/6676372.htm
- http://m.3g.gqskj.cn/xnews/00472.htm
- http://m.3g.gqskj.cn/xnews/1639310.htm
- http://m.3g.gqskj.cn/xnews/8658.htm
- http://m.3g.gqskj.cn/xnews/8807867.htm
- http://m.3g.gqskj.cn/xnews/7599087.htm
- http://m.3g.gqskj.cn/xnews/423101.htm
- http://m.3g.gqskj.cn/xnews/2101381.htm
- http://m.3g.gqskj.cn/xnews/755069.htm
- http://m.3g.gqskj.cn/xnews/057170.htm
- http://m.3g.gqskj.cn/xnews/56857.htm
- http://m.3g.gqskj.cn/xnews/093082.htm
- http://m.3g.gqskj.cn/xnews/723399.htm
- http://m.3g.gqskj.cn/xnews/7566844.htm
- http://m.3g.gqskj.cn/xnews/6159.htm
- http://m.3g.gqskj.cn/xnews/1958538.htm
- http://m.3g.gqskj.cn/xnews/1242876.htm
- http://m.3g.gqskj.cn/xnews/5067.htm
- http://m.3g.gqskj.cn/xnews/4613.htm
- http://m.3g.gqskj.cn/xnews/180161.htm
- http://m.3g.gqskj.cn/xnews/6121135.htm
- http://m.3g.gqskj.cn/xnews/5916.htm
- http://m.3g.gqskj.cn/xnews/7850.htm
- http://m.3g.gqskj.cn/xnews/0390298.htm
- http://m.3g.gqskj.cn/xnews/5821.htm
- http://m.3g.gqskj.cn/xnews/4318464.htm
- http://m.3g.gqskj.cn/xnews/84562.htm
- http://m.3g.gqskj.cn/xnews/155912.htm
- http://m.3g.gqskj.cn/xnews/01407.htm
- http://m.3g.gqskj.cn/xnews/89483.htm
- http://m.3g.gqskj.cn/xnews/31752.htm
- http://m.3g.gqskj.cn/xnews/2410002.htm
- http://m.3g.gqskj.cn/xnews/313711.htm
- http://m.3g.gqskj.cn/xnews/5271.htm
- http://m.3g.gqskj.cn/xnews/5561.htm
- http://m.3g.gqskj.cn/xnews/237635.htm
- http://m.3g.gqskj.cn/xnews/6599.htm
- http://m.3g.gqskj.cn/xnews/47693.htm
- http://m.3g.gqskj.cn/xnews/08964.htm
- http://m.3g.gqskj.cn/xnews/2504.htm
- http://m.3g.gqskj.cn/xnews/74022.htm
- http://m.3g.gqskj.cn/xnews/7697844.htm
- http://m.3g.gqskj.cn/xnews/3848.htm
- http://m.3g.gqskj.cn/xnews/01736.htm
- http://m.3g.gqskj.cn/xnews/4176783.htm
- http://m.3g.gqskj.cn/xnews/1781113.htm
- http://m.3g.gqskj.cn/xnews/035884.htm
- http://m.3g.gqskj.cn/xnews/5643887.htm
- http://m.3g.gqskj.cn/xnews/257947.htm
- http://m.3g.gqskj.cn/xnews/5027.htm
- http://m.3g.gqskj.cn/xnews/2517.htm
- http://m.3g.gqskj.cn/xnews/644123.htm
- http://m.3g.gqskj.cn/xnews/468346.htm
- http://m.3g.gqskj.cn/xnews/2677.htm
- http://m.3g.gqskj.cn/xnews/69765.htm
- http://m.3g.gqskj.cn/xnews/947929.htm
- http://m.3g.gqskj.cn/xnews/7537.htm
- http://m.3g.gqskj.cn/xnews/2993.htm
- http://m.3g.gqskj.cn/xnews/2796658.htm
- http://m.3g.gqskj.cn/xnews/493070.htm
- http://m.3g.gqskj.cn/xnews/862887.htm
- http://m.3g.gqskj.cn/xnews/9352.htm
- http://m.3g.gqskj.cn/xnews/025808.htm
- http://m.3g.gqskj.cn/xnews/2579.htm
- http://m.3g.gqskj.cn/xnews/29122.htm
- http://m.3g.gqskj.cn/xnews/414625.htm
- http://m.3g.gqskj.cn/xnews/8669.htm
- http://m.3g.gqskj.cn/xnews/211040.htm
- http://m.3g.gqskj.cn/xnews/02840.htm
- http://m.3g.gqskj.cn/xnews/7147.htm
- http://m.3g.gqskj.cn/xnews/8197737.htm
- http://m.3g.gqskj.cn/xnews/951119.htm
- http://m.3g.gqskj.cn/xnews/0913.htm
- http://m.3g.gqskj.cn/xnews/96246.htm
- http://m.3g.gqskj.cn/xnews/967768.htm
- http://m.3g.gqskj.cn/xnews/034972.htm
- http://m.3g.gqskj.cn/xnews/5931655.htm
- http://m.3g.gqskj.cn/xnews/6139.htm
- http://m.3g.gqskj.cn/xnews/95080.htm
- http://m.3g.gqskj.cn/xnews/0369892.htm
- http://m.3g.gqskj.cn/xnews/52585.htm
- http://m.3g.gqskj.cn/xnews/4725947.htm
- http://m.3g.gqskj.cn/xnews/83431.htm
- http://m.3g.gqskj.cn/xnews/91760.htm
- http://m.3g.gqskj.cn/xnews/165929.htm
- http://m.3g.gqskj.cn/xnews/49101.htm
- http://m.3g.gqskj.cn/xnews/2835.htm
- http://m.3g.gqskj.cn/xnews/044499.htm
- http://m.3g.gqskj.cn/xnews/58408.htm
- http://m.3g.gqskj.cn/xnews/659095.htm
- http://m.3g.gqskj.cn/xnews/5300178.htm
- http://m.3g.gqskj.cn/xnews/302984.htm
- http://m.3g.gqskj.cn/xnews/582652.htm
- http://m.3g.gqskj.cn/xnews/084126.htm
- http://m.3g.gqskj.cn/xnews/086752.htm
- http://m.3g.gqskj.cn/xnews/2038779.htm
- http://m.3g.gqskj.cn/xnews/1092.htm
- http://m.3g.gqskj.cn/xnews/993974.htm
- http://m.3g.gqskj.cn/xnews/662974.htm
- http://m.3g.gqskj.cn/xnews/5501.htm
- http://m.3g.gqskj.cn/xnews/9724.htm
- http://m.3g.gqskj.cn/xnews/77264.htm
- http://m.3g.gqskj.cn/xnews/653186.htm

## 项目结构

```
webindex/
├── app.py                         # 应用主入口，启动预览服务与路由注册
├── requirements.txt               # Python 依赖声明，包含 Flask、requests、pyyaml
├── config/
│   ├── default.yaml               # 默认配置，含超时、重试、状态枚举定义
│   ├── development.yaml           # 开发环境覆盖配置，开启调试日志
│   └── production.yaml            # 生产环境覆盖配置，关闭调试、调整并发
├── scripts/
│   ├── import_batch.py            # 批次导入脚本，支持 txt / csv 格式输入
│   ├── export_report.py           # 报告导出脚本，输出 Markdown / CSV
│   └── health_check.py            # 外链健康检查脚本，批量执行 HEAD 请求
├── core/
│   ├── indexer.py                 # 核心索引引擎，管理批次与链接映射关系
│   ├── validator.py               # URL 格式校验与去重逻辑
│   ├── metadata.py                # 元信息补全模块，封装 requests 调用
│   └── state.py                   # 状态机定义与状态转换规则
├── storage/
│   ├── batches/                   # 按批次存储原始导入文件
│   │   └── 159/                   # 第 159 批次目录（当前批次）
│   ├── reports/                   # 导出报告存放目录
│   └── cache/                     # HEAD 请求结果缓存，减少重复网络调用
├── templates/
│   ├── index.html                 # 列表页模板，展示当前批次所有链接
│   └── detail.html                # 详情页模板，展示单个链接的元信息
├── tests/
│   ├── test_indexer.py            # 索引引擎单元测试
│   ├── test_validator.py          # 校验器单元测试
│   └── test_metadata.py           # 元信息补全单元测试
├── docs/                          # 完整文档目录，含用户手册与开发者指南
├── CHANGELOG.md                   # 版本变更历史
└── README.md                      # 项目介绍文档（当前文件）
```

## 贡献指南

1. 复刻项目仓库至个人账号，并在本地创建功能分支。分支命名建议采用 `feature/` 或 `fix/` 前缀，例如 `feature/batch-import-optimization`。

2. 按照项目根目录下的 `CONTRIBUTING.md` 文件中的编码规范进行开发，确保新增代码包含对应的单元测试，测试覆盖率不低于百分之八十。

3. 提交代码前执行完整的测试套件，命令为 `make test` 或 `pytest tests/`，并确保所有测试用例通过。同时执行 `make lint` 检查代码风格是否符合 PEP 8 标准。

4. 提交 Pull Request 时填写标准模板，包括变更摘要、测试结果、影响范围以及是否涉及破坏性变更。PR 描述中应引用相关 Issue 编号。

5. 项目维护者会在两个工作日内进行 Code Review，并根据反馈进行修改。合并后贡献者名称将自动添加到 `CONTRIBUTORS.md` 文件中。

## 常见问题

Q: 导入大量 URL 时出现超时或连接重置，应如何处理？

A: 这通常是由于网络环境或目标服务器响应较慢导致。建议在配置文件中调整 `head_request_timeout` 参数，默认值为 5 秒，可适当增加至 10 或 15 秒。同时可启用 `cache` 功能避免重复请求同一域名。若仍无法解决，可使用 `health_check.py` 脚本单独重试失败的链接。

Q: 项目是否支持多用户并发写入同一批次？

A: 当前版本为单机单进程设计，不提供内置的分布式锁或并发写入控制。如需多人协作维护同一批次，建议采用串行操作或使用外部版本控制系统（如 Git）对 `storage/batches/` 目录下的 JSON 索引文件进行合并管理。后续版本计划引入基于 SQLite 的并发支持。

Q: 如何迁移已存在的资源链接到新的项目实例？

A: 将原项目 `storage/batches/` 目录下的所有批次文件夹完整复制到新实例的对应目录下，同时复制 `config/` 目录中的自定义配置。启动新实例后，索引引擎会自动加载现有批次。注意保持 Python 版本与依赖版本的一致性，避免序列化兼容问题。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:55
