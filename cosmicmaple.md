# WebResource Aggregator

WebResource Aggregator 是一个面向技术调研、内容聚合与批量链接管理场景的轻量级资源导航工具。该项目定位于帮助开发者、运营人员与研究人员高效收集、分类、检索与导出大规模外链数据，尤其适用于处理批次化、高密度、多域名的原始链接素材。

本项目不依赖数据库，基于文件系统与静态索引机制运行，支持千级链接的快速导入、去重、标签标记与多格式导出。目标用户包括开源文档维护者、网络爬虫数据清洗人员、SEO 内容策略师以及知识库构建工程师。

## 功能概览

**批量链接导入与解析**：支持从纯文本、CSV 及 Markdown 列表中批量读取 URL，自动识别协议头与域名结构，剔除无效或畸形条目。

**多维度标签分类**：允许用户为每条链接添加自定义标签（如“技术文档”、“新闻资讯”、“视频资源”），并基于标签进行快速筛选与统计。

**去重与归一化检查**：基于 URL 完整字符串与域名 + 路径哈希两种策略进行重复检测，输出重复报告供人工审核。

**索引状态可视化**：为每条链接记录导入时间、最后访问状态码与响应时长，便于判断资源可用性。

**灵活导出管线**：支持导出为纯 URL 列表、带标签的 CSV 表格以及按分类拆分的多文件 Markdown 索引。

**检索与过滤引擎**：提供基于子串、域名后缀与标签组合的即时过滤能力，结果可排序并支持复制到剪贴板。

**批次管理元数据**：记录当前批次编号（如第 19/240 批）、总链接数与各分类占比，方便项目级进度追踪。

## 应用场景

**技术文档外链整理**：开源项目维护者可将散落在多个 Issue 或 PR 中的参考链接统一导入，按模块分类后生成结构化的 RESOURCES.md，供团队共享。

**爬虫数据初筛**：数据采集工程师在完成一轮抓取后，将原始 URL 列表导入本工具，快速去重并标记异常状态码，筛选出有效候选链接进行深度爬取。

**竞品动态监测**：运营人员定期将竞品官网、媒体报道与论坛讨论链接汇总，通过标签区分渠道，观察各渠道内容更新频率与话题分布。

**学术文献补充材料管理**：研究人员在撰写综述时，将参考文献的在线来源链接集中管理，导出为符合期刊要求的引用格式，避免遗漏或重复。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/webresource-dev/webresource-aggregator.git
cd webresource-aggregator
pip install -r requirements.txt
python app.py --input ./samples/batch_19_raw.txt --output ./output/batch_19_index.md
```

如需启用 Web 界面，可在执行后访问 `http://127.0.0.1:5000` 进行交互式操作。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 稳定版 |
| Flask | 2.2.x | Web 界面服务框架，仅在使用可视化模式时需要 |
| pandas | 1.5.x | 用于数据表格处理与 CSV 导出功能 |
| requests | 2.28.x | 用于链接可用性探测与状态码检测 |
| click | 8.1.x | 提供命令行交互接口，用于参数解析 |
| pytest | 7.2.x | 单元测试框架，仅开发环境需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门 | docs/quickstart.md | 如何最快上手使用本工具处理第一批链接？ |
| 功能 | docs/features/batch_management.md | 如何创建新批次、追加链接、切换当前批次？ |
| 运维 | docs/administration/export_formats.md | 支持哪些导出格式？如何自定义输出模板？ |
| 参考 | docs/reference/api_cli.md | 所有命令行参数与 Flask 路由接口的完整说明 |

## 资源列表

- http://m.3g.fcful.cn/snews/288118.htm
- http://m.3g.fcful.cn/snews/06393.htm
- http://m.3g.fcful.cn/snews/63606.htm
- http://m.3g.fcful.cn/snews/8950.htm
- http://m.3g.fcful.cn/snews/18159.htm
- http://m.3g.fcful.cn/snews/3785653.htm
- http://m.3g.fcful.cn/snews/267446.htm
- http://m.3g.fcful.cn/snews/4057682.htm
- http://m.3g.fcful.cn/snews/0060084.htm
- http://m.3g.fcful.cn/snews/6305859.htm
- http://m.3g.fcful.cn/snews/3878.htm
- http://m.3g.fcful.cn/snews/6816909.htm
- http://m.3g.fcful.cn/snews/0847723.htm
- http://m.3g.fcful.cn/snews/34483.htm
- http://m.3g.fcful.cn/snews/435893.htm
- http://m.3g.fcful.cn/snews/701110.htm
- http://m.3g.fcful.cn/snews/8883744.htm
- http://m.3g.fcful.cn/snews/591965.htm
- http://m.3g.fcful.cn/snews/37574.htm
- http://m.3g.fcful.cn/snews/76042.htm
- http://m.3g.fcful.cn/snews/62641.htm
- http://m.3g.fcful.cn/snews/0529.htm
- http://m.3g.fcful.cn/snews/1068527.htm
- http://m.3g.fcful.cn/snews/39389.htm
- http://m.3g.fcful.cn/snews/2398004.htm
- http://m.3g.fcful.cn/snews/45241.htm
- http://m.3g.fcful.cn/snews/2735.htm
- http://m.3g.fcful.cn/snews/82960.htm
- http://m.3g.fcful.cn/snews/443840.htm
- http://m.3g.fcful.cn/snews/1639.htm
- http://m.3g.fcful.cn/snews/33449.htm
- http://m.3g.fcful.cn/snews/10403.htm
- http://m.3g.fcful.cn/snews/68337.htm
- http://m.3g.fcful.cn/snews/211062.htm
- http://m.3g.fcful.cn/snews/338676.htm
- http://m.3g.fcful.cn/snews/4259075.htm
- http://m.3g.fcful.cn/snews/9071489.htm
- http://m.3g.fcful.cn/snews/3833778.htm
- http://m.3g.fcful.cn/snews/5422.htm
- http://m.3g.fcful.cn/snews/441658.htm
- http://m.3g.fcful.cn/snews/3667661.htm
- http://m.3g.fcful.cn/snews/190622.htm
- http://m.3g.fcful.cn/snews/36817.htm
- http://m.3g.fcful.cn/snews/04737.htm
- http://m.3g.fcful.cn/snews/08824.htm
- http://m.3g.fcful.cn/snews/697202.htm
- http://m.3g.fcful.cn/snews/8581.htm
- http://m.3g.fcful.cn/snews/3616559.htm
- http://m.3g.fcful.cn/snews/9433227.htm
- http://m.3g.fcful.cn/snews/3665367.htm
- http://m.3g.fcful.cn/snews/455519.htm
- http://m.3g.fcful.cn/snews/0896851.htm
- http://m.3g.fcful.cn/snews/345655.htm
- http://m.3g.fcful.cn/snews/779950.htm
- http://m.3g.fcful.cn/snews/320938.htm
- http://m.3g.fcful.cn/snews/5745262.htm
- http://m.3g.fcful.cn/snews/497573.htm
- http://m.3g.fcful.cn/snews/216789.htm
- http://m.3g.fcful.cn/snews/017746.htm
- http://m.3g.fcful.cn/snews/9692842.htm
- http://m.3g.fcful.cn/snews/62820.htm
- http://m.3g.fcful.cn/snews/41526.htm
- http://m.3g.fcful.cn/snews/0394.htm
- http://m.3g.fcful.cn/snews/5007.htm
- http://m.3g.fcful.cn/snews/88843.htm
- http://m.3g.fcful.cn/snews/1913.htm
- http://m.3g.fcful.cn/snews/45217.htm
- http://m.3g.fcful.cn/snews/6839.htm
- http://m.3g.fcful.cn/snews/2707739.htm
- http://m.3g.fcful.cn/snews/23072.htm
- http://m.3g.fcful.cn/snews/566188.htm
- http://m.3g.fcful.cn/snews/2695550.htm
- http://m.3g.fcful.cn/snews/8455521.htm
- http://m.3g.fcful.cn/snews/1211.htm
- http://m.3g.fcful.cn/snews/638839.htm
- http://m.3g.fcful.cn/snews/46694.htm
- http://m.3g.fcful.cn/snews/734611.htm
- http://m.3g.fcful.cn/snews/78911.htm
- http://m.3g.fcful.cn/snews/7529215.htm
- http://m.3g.fcful.cn/snews/1143.htm
- http://m.3g.fcful.cn/snews/6069264.htm
- http://m.3g.fcful.cn/snews/8318909.htm
- http://m.3g.fcful.cn/snews/337241.htm
- http://m.3g.fcful.cn/snews/1350.htm
- http://m.3g.fcful.cn/snews/91685.htm
- http://m.3g.fcful.cn/snews/1681.htm
- http://m.3g.fcful.cn/snews/174674.htm
- http://m.3g.fcful.cn/snews/726661.htm
- http://m.3g.fcful.cn/snews/331004.htm
- http://m.3g.fcful.cn/snews/5194.htm
- http://m.3g.fcful.cn/snews/926087.htm
- http://m.3g.fcful.cn/snews/9739952.htm
- http://m.3g.fcful.cn/snews/3090507.htm
- http://m.3g.fcful.cn/snews/451023.htm
- http://m.3g.fcful.cn/snews/28758.htm
- http://m.3g.fcful.cn/snews/0111.htm
- http://m.3g.fcful.cn/snews/394383.htm
- http://m.3g.fcful.cn/snews/45586.htm
- http://m.3g.fcful.cn/snews/046843.htm
- http://m.3g.fcful.cn/snews/4971988.htm
- http://m.3g.fcful.cn/snews/780390.htm
- http://m.3g.fcful.cn/snews/04314.htm
- http://m.3g.fcful.cn/snews/7856806.htm
- http://m.3g.fcful.cn/snews/5499.htm
- http://m.3g.fcful.cn/snews/89744.htm
- http://m.3g.fcful.cn/snews/5140576.htm
- http://m.3g.fcful.cn/snews/4541.htm
- http://m.3g.fcful.cn/snews/0822.htm
- http://m.3g.fcful.cn/snews/73685.htm
- http://m.3g.fcful.cn/snews/6826.htm
- http://m.3g.fcful.cn/snews/49270.htm
- http://m.3g.fcful.cn/snews/2742417.htm
- http://m.3g.fcful.cn/snews/3473.htm
- http://m.3g.fcful.cn/snews/825324.htm
- http://m.3g.fcful.cn/snews/913929.htm
- http://m.3g.fcful.cn/snews/9621.htm
- http://m.3g.fcful.cn/snews/79403.htm
- http://m.3g.fcful.cn/snews/82254.htm
- http://m.3g.fcful.cn/snews/20633.htm
- http://m.3g.fcful.cn/snews/8760059.htm
- http://m.3g.fcful.cn/snews/97419.htm
- http://m.3g.fcful.cn/snews/726492.htm
- http://m.3g.fcful.cn/snews/58301.htm
- http://m.3g.fcful.cn/snews/81224.htm
- http://m.3g.fcful.cn/snews/32192.htm
- http://m.3g.fcful.cn/snews/9319938.htm
- http://m.3g.fcful.cn/snews/0632524.htm
- http://m.3g.fcful.cn/snews/2073.htm
- http://m.3g.fcful.cn/snews/1312.htm
- http://m.3g.fcful.cn/snews/6806614.htm
- http://m.3g.fcful.cn/snews/84771.htm
- http://m.3g.fcful.cn/snews/8701.htm
- http://m.3g.fcful.cn/snews/69859.htm
- http://m.3g.fcful.cn/snews/95385.htm
- http://m.3g.fcful.cn/snews/8040.htm
- http://m.3g.fcful.cn/snews/37596.htm
- http://m.3g.fcful.cn/snews/8652.htm
- http://m.3g.fcful.cn/snews/46613.htm
- http://m.3g.fcful.cn/snews/746886.htm
- http://m.3g.fcful.cn/snews/9129.htm
- http://m.3g.fcful.cn/snews/840406.htm
- http://m.3g.fcful.cn/snews/6056.htm
- http://m.3g.fcful.cn/snews/85875.htm
- http://m.3g.fcful.cn/snews/6122.htm
- http://m.3g.fcful.cn/snews/734731.htm
- http://m.3g.fcful.cn/snews/8397.htm
- http://m.3g.fcful.cn/snews/9212667.htm
- http://m.3g.fcful.cn/snews/3703946.htm
- http://m.3g.fcful.cn/snews/30579.htm
- http://m.3g.fcful.cn/snews/2426929.htm
- http://m.3g.fcful.cn/snews/6223.htm
- http://m.3g.fcful.cn/snews/92068.htm
- http://m.3g.fcful.cn/snews/25712.htm
- http://m.3g.fcful.cn/snews/6867.htm
- http://m.3g.fcful.cn/snews/53648.htm
- http://m.3g.fcful.cn/snews/0570434.htm
- http://m.3g.fcful.cn/snews/095475.htm
- http://m.3g.fcful.cn/snews/242755.htm
- http://m.3g.fcful.cn/snews/50493.htm
- http://m.3g.fcful.cn/snews/93806.htm
- http://m.3g.fcful.cn/snews/4866.htm
- http://m.3g.fcful.cn/snews/26806.htm
- http://m.3g.fcful.cn/snews/009434.htm
- http://m.3g.fcful.cn/snews/71697.htm
- http://m.3g.fcful.cn/snews/8285189.htm
- http://m.3g.fcful.cn/snews/170519.htm
- http://m.3g.fcful.cn/snews/490528.htm
- http://m.3g.fcful.cn/snews/509900.htm
- http://m.3g.fcful.cn/snews/8030606.htm
- http://m.3g.fcful.cn/snews/786015.htm
- http://m.3g.fcful.cn/snews/7074553.htm
- http://m.3g.fcful.cn/snews/267425.htm
- http://m.3g.fcful.cn/snews/323668.htm
- http://m.3g.fcful.cn/snews/6809545.htm
- http://m.3g.fcful.cn/snews/7196112.htm
- http://m.3g.fcful.cn/snews/043022.htm
- http://m.3g.fcful.cn/snews/2080489.htm
- http://m.3g.fcful.cn/snews/67309.htm
- http://m.3g.fcful.cn/snews/2676065.htm
- http://m.3g.fcful.cn/snews/741159.htm
- http://m.3g.fcful.cn/snews/0773108.htm
- http://m.3g.fcful.cn/snews/790192.htm
- http://m.3g.fcful.cn/snews/42822.htm
- http://m.3g.fcful.cn/snews/28278.htm
- http://m.3g.fcful.cn/snews/8165734.htm
- http://m.3g.fcful.cn/snews/0843854.htm
- http://m.3g.fcful.cn/snews/1827.htm
- http://m.3g.fcful.cn/snews/11922.htm
- http://m.3g.fcful.cn/snews/4242658.htm
- http://m.3g.fcful.cn/snews/4601.htm
- http://m.3g.fcful.cn/snews/741390.htm
- http://m.3g.fcful.cn/snews/3200.htm
- http://m.3g.fcful.cn/snews/6117265.htm
- http://m.3g.fcful.cn/snews/453449.htm
- http://m.3g.fcful.cn/snews/3545.htm
- http://m.3g.fcful.cn/snews/4775.htm
- http://m.3g.fcful.cn/snews/9637377.htm
- http://m.3g.fcful.cn/snews/224430.htm
- http://m.3g.fcful.cn/snews/25816.htm
- http://m.3g.fcful.cn/snews/304671.htm
- http://m.3g.fcful.cn/snews/52092.htm
- http://m.3g.fcful.cn/snews/815953.htm
- http://m.3g.fcful.cn/snews/397275.htm
- http://m.3g.fcful.cn/snews/93813.htm
- http://m.3g.fcful.cn/snews/6525018.htm
- http://m.3g.fcful.cn/snews/6668585.htm
- http://m.3g.fcful.cn/snews/5777479.htm
- http://m.3g.fcful.cn/snews/966397.htm
- http://m.3g.fcful.cn/snews/469779.htm
- http://m.3g.fcful.cn/snews/731547.htm
- http://m.3g.fcful.cn/snews/0732598.htm
- http://m.3g.fcful.cn/snews/3415423.htm
- http://m.3g.fcful.cn/snews/2405336.htm
- http://m.3g.fcful.cn/snews/7730.htm
- http://m.3g.fcful.cn/snews/691113.htm
- http://m.3g.fcful.cn/snews/2007339.htm
- http://m.3g.fcful.cn/snews/8697133.htm
- http://m.3g.fcful.cn/snews/2604303.htm
- http://m.3g.fcful.cn/snews/708034.htm
- http://m.3g.fcful.cn/snews/6437022.htm
- http://m.3g.fcful.cn/snews/5348894.htm
- http://m.3g.fcful.cn/snews/2133232.htm
- http://m.3g.fcful.cn/snews/7938059.htm
- http://m.3g.fcful.cn/snews/1204244.htm
- http://m.3g.fcful.cn/snews/5615.htm
- http://m.3g.fcful.cn/snews/8952576.htm
- http://m.3g.fcful.cn/snews/11617.htm
- http://m.3g.fcful.cn/snews/7619908.htm
- http://m.3g.fcful.cn/snews/29597.htm
- http://m.3g.fcful.cn/snews/3584.htm
- http://m.3g.fcful.cn/snews/4038.htm
- http://m.3g.fcful.cn/snews/351359.htm
- http://m.3g.fcful.cn/snews/58815.htm
- http://m.3g.fcful.cn/snews/30465.htm
- http://m.3g.fcful.cn/snews/32310.htm
- http://m.3g.fcful.cn/snews/227886.htm
- http://m.3g.fcful.cn/snews/7010723.htm
- http://m.3g.fcful.cn/snews/386410.htm
- http://m.3g.fcful.cn/snews/1927.htm
- http://m.3g.fcful.cn/snews/446818.htm
- http://m.3g.fcful.cn/snews/4842747.htm
- http://m.3g.fcful.cn/snews/4184.htm
- http://m.3g.fcful.cn/snews/6637012.htm
- http://m.3g.fcful.cn/snews/438543.htm
- http://m.3g.fcful.cn/snews/8339.htm
- http://m.3g.fcful.cn/snews/4327.htm
- http://m.3g.fcful.cn/snews/4823.htm
- http://m.3g.fcful.cn/snews/684449.htm
- http://m.3g.fcful.cn/snews/660619.htm
- http://m.3g.fcful.cn/snews/56087.htm

## 项目结构

```
webresource-aggregator/
├── app.py                     # 主入口，整合 CLI 与 Web 模式
├── requirements.txt           # Python 依赖声明
├── config.yaml                # 运行时配置，含批次编号与输出路径
├── core/
│   ├── loader.py              # 从文本/CSV 加载原始链接列表，支持编码探测
│   ├── dedup.py               # 基于完整 URL 与域名哈希的双重去重引擎
│   ├── classifier.py          # 标签管理、自动标签建议与分类统计
│   └── exporter.py            # 导出为 Markdown、CSV、纯文本等格式
├── web/
│   ├── routes.py              # Flask 路由定义，含首页、上传、筛选与导出接口
│   ├── static/                # CSS 与 JavaScript 静态资源
│   └── templates/             # Jinja2 模板文件，用于渲染操作界面
├── tests/
│   ├── test_loader.py         # 测试不同格式输入文件的解析正确性
│   ├── test_dedup.py          # 去重逻辑的单元测试，覆盖边界情况
│   └── test_exporter.py       # 验证各类导出输出的格式合规性
├── docs/                      # 完整文档目录，含快速开始与功能详解
└── samples/
    └── batch_19_raw.txt       # 第 19 批原始链接样本，用于演示与回归测试
```

## 贡献指南

贡献者请先阅读项目行为准则并签署贡献者许可协议。所有提交均需通过单元测试与代码风格检查。

1. 从 GitHub 仓库派生项目至个人账号，克隆派生仓库到本地开发环境。
2. 创建新的功能分支，分支名需体现变更类型与简要描述，例如 `feat/csv-export-encoding`。
3. 在核心模块或 Web 界面中实现新增功能或修复缺陷，并同步更新对应单元测试用例。
4. 执行完整测试套件与代码规范检查，确保无回归错误与语法警告。
5. 提交包含清晰变更说明的 pull request，等待项目维护者审阅与合并。

## 常见问题

**问：导入链接时提示“无效 URL”或“格式错误”，但链接本身看起来正常。**

答：本工具要求每条链接独占一行，且必须包含协议头（http:// 或 https://）。请检查原始文件是否存在前导空白字符、换行符不统一或多余的分隔符。若链接包含中文或特殊字符，建议先进行 URL 编码后再导入。

**问：去重功能是否区分大小写？如何处理同一资源的不同协议版本？**

答：去重第一步基于完整 URL 字符串的比较，该步骤区分大小写。第二步基于域名 + 路径的归一化哈希，此步骤会自动将域名转为小写并忽略末尾斜杠，因此 http://example.com/page 与 https://example.com/page/ 会被视为不同资源，但 http://example.com/page 与 http://example.com/page/ 会被识别为重复。

**问：如何将当前批次的所有链接导出为一份独立的 HTML 报告？**

答：当前版本原生支持 Markdown 与 CSV 导出。如需 HTML 格式，建议使用导出 CSV 后再通过第三方工具转换，或调用 Web 界面中的“打印视图”功能，利用浏览器另存为 HTML。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:29:44
