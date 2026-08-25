# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的结构化外链资源聚合平台。该项目专注于对分散在互联网各处的深层网页资源进行系统性采集、分类和索引，帮助用户从大量原始链接中快速定位具有特定主题或数据特征的文档。WebLink Navigator 不生产内容，而是通过严格的链接管理和元数据标注机制，为后续的数据挖掘、趋势分析和知识图谱构建提供干净、可追溯的输入数据。

本项目诞生于第 179/240 批次资源整理工作，目前已经完成对超过 250 个信息源的结构化收录。通过标准化的链接采集流程和自动化分类脚本，WebLink Navigator 能够将原本零散的 URL 转化为可供检索和过滤的结构化数据表。项目面向数据科学家、学术研究者、舆情监测工程师以及任何需要系统化管理外链资源的专业人士。

## 功能概览

批量链接导入与去重：支持从纯文本文件、CSV 和 JSON 格式批量导入原始 URL 列表，自动检测并移除重复条目，保留首次出现的有效链接。

资源状态健康检查：内置 HTTP 状态码探测模块，定期对已收录的链接进行可用性验证，标记失效链接并生成异常报告。

分类标签自动标注：基于 URL 路径特征、查询参数和页面标题模式，使用轻量级规则引擎为每个链接自动生成候选分类标签。

全文元数据提取：对于可访问的链接，抓取页面标题、描述、关键词和最后修改时间，并将这些信息与原始 URL 关联存储。

黑名单与白名单过滤：允许用户定义域名级或路径级的访问控制规则，在采集阶段过滤非目标来源，提升资源池的纯度。

增量更新与版本记录：每次运行采集任务时仅处理新增或变更的链接，保留历史版本记录，支持回滚到任意先前的资源状态。

导出接口多样化：支持将索引结果导出为 JSON Lines、SQLite 数据库文件或 Pandas DataFrame 格式，方便下游分析工具直接读取。

## 应用场景

技术文档归档与检索：研发团队可以使用 WebLink Navigator 将分散在各技术博客、官方文档站和论坛中的参考链接统一归档，通过标签快速检索与特定框架或库相关的资料。

舆情信息跟踪：舆情分析师可以导入包含新闻稿、公告页和社交媒体帖子的链接列表，项目定期检查页面更新状态并记录变更时间，辅助追踪事件发展脉络。

学术文献辅助管理：研究人员在收集论文预印本、数据集页面和项目主页时，可以使用本项目的元数据提取功能快速生成引用所需的标题、作者和发布日期信息，减少手工整理时间。

网站迁移与改版验证：运维人员在执行网站域名迁移或页面结构改版后，可将旧 URL 列表导入项目，利用健康检查模块验证新地址的可用性并生成重定向映射表。

数据湖入湖前置处理：数据工程师在将外链资源导入数据湖之前，可以使用本项目的分类和过滤功能进行初步清洗，确保入湖数据符合统一的格式和质量标准。

## 快速开始

以下命令演示了如何在本地环境中获取 WebLink Navigator 源码、安装核心依赖并启动基础采集服务。

```bash
# 克隆项目仓库到本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 创建并激活 Python 虚拟环境
python3 -m venv venv
source venv/bin/activate

# 安装所有必需的依赖包
pip install -r requirements.txt

# 复制示例配置文件并修改数据库连接参数
cp config.example.yaml config.yaml

# 运行资源采集示例任务
python cli.py collect --input samples/url_list.txt --output data/index.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，推荐使用 3.10 版本以获得最佳兼容性 |
| SQLite | 3.35.0 及以上 | 用于存储链接元数据和任务状态，Python 标准库自带 |
| requests | 2.28.0 及以上 | 执行 HTTP 请求和健康检查的核心库 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 页面标题和元数据标签 |
| PyYAML | 6.0 及以上 | 读取 YAML 格式的配置文件 |
| pandas | 1.5.0 及以上 | 可选依赖，用于 DataFrame 格式的数据导出 |
| lxml | 4.9.0 及以上 | 可选依赖，提供更高效的 HTML 解析后端 |
| aiohttp | 3.8.0 及以上 | 可选依赖，用于异步批量请求提升采集效率 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何快速配置第一个采集任务并查看输出结果 |
| 配置手册 | docs/configuration.md | config.yaml 中每个字段的含义以及如何调优采集参数 |
| 接口参考 | docs/api_reference.md | 各核心模块的函数签名、参数说明和返回值结构 |
| 任务编排 | docs/workflow.md | 如何创建定时任务、组合多个采集流程以及处理失败重试 |
| 数据字典 | docs/data_dictionary.md | 索引文件中每个字段的命名规范、数据类型和取值范围 |
| 故障排查 | docs/troubleshooting.md | 常见报错信息的含义以及对应的解决方案 |

## 资源列表

- http://m.wap.gqskj.cn/snews/808537.htm
- http://m.wap.gqskj.cn/snews/8031.htm
- http://m.wap.gqskj.cn/snews/730051.htm
- http://m.wap.gqskj.cn/snews/5229690.htm
- http://m.wap.gqskj.cn/snews/9632920.htm
- http://m.wap.gqskj.cn/snews/9838.htm
- http://m.wap.gqskj.cn/snews/4462196.htm
- http://m.wap.gqskj.cn/snews/0887921.htm
- http://m.wap.gqskj.cn/snews/4135013.htm
- http://m.wap.gqskj.cn/snews/1732.htm
- http://m.wap.gqskj.cn/snews/7509407.htm
- http://m.wap.gqskj.cn/snews/953614.htm
- http://m.wap.gqskj.cn/snews/55354.htm
- http://m.wap.gqskj.cn/snews/3340.htm
- http://m.wap.gqskj.cn/snews/0681275.htm
- http://m.wap.gqskj.cn/snews/1389.htm
- http://m.wap.gqskj.cn/snews/510311.htm
- http://m.wap.gqskj.cn/snews/62728.htm
- http://m.wap.gqskj.cn/snews/10886.htm
- http://m.wap.gqskj.cn/snews/28246.htm
- http://m.wap.gqskj.cn/snews/62754.htm
- http://m.wap.gqskj.cn/snews/032932.htm
- http://m.wap.gqskj.cn/snews/2270.htm
- http://m.wap.gqskj.cn/snews/60193.htm
- http://m.wap.gqskj.cn/snews/0554749.htm
- http://m.wap.gqskj.cn/snews/2687396.htm
- http://m.wap.gqskj.cn/snews/8018427.htm
- http://m.wap.gqskj.cn/snews/1094186.htm
- http://m.wap.gqskj.cn/snews/280014.htm
- http://m.wap.gqskj.cn/snews/7158.htm
- http://m.wap.gqskj.cn/snews/2304946.htm
- http://m.wap.gqskj.cn/snews/2300251.htm
- http://m.wap.gqskj.cn/snews/00685.htm
- http://m.wap.gqskj.cn/snews/5973.htm
- http://m.wap.gqskj.cn/snews/203391.htm
- http://m.wap.gqskj.cn/snews/691682.htm
- http://m.wap.gqskj.cn/snews/33107.htm
- http://m.wap.gqskj.cn/snews/0860.htm
- http://m.wap.gqskj.cn/snews/37472.htm
- http://m.wap.gqskj.cn/snews/888724.htm
- http://m.wap.gqskj.cn/snews/8113.htm
- http://m.wap.gqskj.cn/snews/03990.htm
- http://m.wap.gqskj.cn/snews/4612508.htm
- http://m.wap.gqskj.cn/snews/3090.htm
- http://m.wap.gqskj.cn/snews/10516.htm
- http://m.wap.gqskj.cn/snews/6022.htm
- http://m.wap.gqskj.cn/snews/7007479.htm
- http://m.wap.gqskj.cn/snews/7809456.htm
- http://m.wap.gqskj.cn/snews/8363.htm
- http://m.wap.gqskj.cn/snews/7709445.htm
- http://m.wap.gqskj.cn/snews/0843.htm
- http://m.wap.gqskj.cn/snews/23334.htm
- http://m.wap.gqskj.cn/snews/1963.htm
- http://m.wap.gqskj.cn/snews/25085.htm
- http://m.wap.gqskj.cn/snews/5116.htm
- http://m.wap.gqskj.cn/snews/98942.htm
- http://m.wap.gqskj.cn/snews/2459558.htm
- http://m.wap.gqskj.cn/snews/05712.htm
- http://m.wap.gqskj.cn/snews/85543.htm
- http://m.wap.gqskj.cn/snews/1355.htm
- http://m.wap.gqskj.cn/snews/7777195.htm
- http://m.wap.gqskj.cn/snews/926142.htm
- http://m.wap.gqskj.cn/snews/818017.htm
- http://m.wap.gqskj.cn/snews/9576.htm
- http://m.wap.gqskj.cn/snews/53095.htm
- http://m.wap.gqskj.cn/snews/2538.htm
- http://m.wap.gqskj.cn/snews/61426.htm
- http://m.wap.gqskj.cn/snews/7032.htm
- http://m.wap.gqskj.cn/snews/8065925.htm
- http://m.wap.gqskj.cn/snews/4918718.htm
- http://m.wap.gqskj.cn/snews/60997.htm
- http://m.wap.gqskj.cn/snews/0718.htm
- http://m.wap.gqskj.cn/snews/9485508.htm
- http://m.wap.gqskj.cn/snews/434456.htm
- http://m.wap.gqskj.cn/snews/0177659.htm
- http://m.wap.gqskj.cn/snews/85156.htm
- http://m.wap.gqskj.cn/snews/2928.htm
- http://m.wap.gqskj.cn/snews/8912.htm
- http://m.wap.gqskj.cn/snews/1054.htm
- http://m.wap.gqskj.cn/snews/1102426.htm
- http://m.wap.gqskj.cn/snews/9577856.htm
- http://m.wap.gqskj.cn/snews/52315.htm
- http://m.wap.gqskj.cn/snews/9950624.htm
- http://m.wap.gqskj.cn/snews/92923.htm
- http://m.wap.gqskj.cn/snews/2887539.htm
- http://m.wap.gqskj.cn/snews/622433.htm
- http://m.wap.gqskj.cn/snews/78314.htm
- http://m.wap.gqskj.cn/snews/58758.htm
- http://m.wap.gqskj.cn/snews/6311511.htm
- http://m.wap.gqskj.cn/snews/5848.htm
- http://m.wap.gqskj.cn/snews/329252.htm
- http://m.wap.gqskj.cn/snews/26554.htm
- http://m.wap.gqskj.cn/snews/6473480.htm
- http://m.wap.gqskj.cn/snews/50242.htm
- http://m.wap.gqskj.cn/snews/568870.htm
- http://m.wap.gqskj.cn/snews/23975.htm
- http://m.wap.gqskj.cn/snews/8498206.htm
- http://m.wap.gqskj.cn/snews/072402.htm
- http://m.wap.gqskj.cn/snews/7407103.htm
- http://m.wap.gqskj.cn/snews/1716189.htm
- http://m.wap.gqskj.cn/snews/9529180.htm
- http://m.wap.gqskj.cn/snews/8469516.htm
- http://m.wap.gqskj.cn/snews/651216.htm
- http://m.wap.gqskj.cn/snews/364012.htm
- http://m.wap.gqskj.cn/snews/927153.htm
- http://m.wap.gqskj.cn/snews/207648.htm
- http://m.wap.gqskj.cn/snews/0037490.htm
- http://m.wap.gqskj.cn/snews/250788.htm
- http://m.wap.gqskj.cn/snews/586828.htm
- http://m.wap.gqskj.cn/snews/03486.htm
- http://m.wap.gqskj.cn/snews/026677.htm
- http://m.wap.gqskj.cn/snews/990606.htm
- http://m.wap.gqskj.cn/snews/595562.htm
- http://m.wap.gqskj.cn/snews/654682.htm
- http://m.wap.gqskj.cn/snews/389454.htm
- http://m.wap.gqskj.cn/snews/1419.htm
- http://m.wap.gqskj.cn/snews/763941.htm
- http://m.wap.gqskj.cn/snews/5310.htm
- http://m.wap.gqskj.cn/snews/85221.htm
- http://m.wap.gqskj.cn/snews/824425.htm
- http://m.wap.gqskj.cn/snews/3795632.htm
- http://m.wap.gqskj.cn/snews/3586508.htm
- http://m.wap.gqskj.cn/snews/210734.htm
- http://m.wap.gqskj.cn/snews/0612295.htm
- http://m.wap.gqskj.cn/snews/2981.htm
- http://m.wap.gqskj.cn/snews/738922.htm
- http://m.wap.gqskj.cn/snews/51812.htm
- http://m.wap.gqskj.cn/snews/25781.htm
- http://m.wap.gqskj.cn/snews/81800.htm
- http://m.wap.gqskj.cn/snews/456067.htm
- http://m.wap.gqskj.cn/snews/5490121.htm
- http://m.wap.gqskj.cn/snews/440797.htm
- http://m.wap.gqskj.cn/snews/58035.htm
- http://m.wap.gqskj.cn/snews/55940.htm
- http://m.wap.gqskj.cn/snews/4920154.htm
- http://m.wap.gqskj.cn/snews/8647.htm
- http://m.wap.gqskj.cn/snews/664943.htm
- http://m.wap.gqskj.cn/snews/9472346.htm
- http://m.wap.gqskj.cn/snews/846542.htm
- http://m.wap.gqskj.cn/snews/523873.htm
- http://m.wap.gqskj.cn/snews/156935.htm
- http://m.wap.gqskj.cn/snews/9473585.htm
- http://m.wap.gqskj.cn/snews/6715.htm
- http://m.wap.gqskj.cn/snews/0498220.htm
- http://m.wap.gqskj.cn/snews/937963.htm
- http://m.wap.gqskj.cn/snews/568009.htm
- http://m.wap.gqskj.cn/snews/3189.htm
- http://m.wap.gqskj.cn/snews/474835.htm
- http://m.wap.gqskj.cn/snews/4088303.htm
- http://m.wap.gqskj.cn/snews/326926.htm
- http://m.wap.gqskj.cn/snews/79623.htm
- http://m.wap.gqskj.cn/snews/50660.htm
- http://m.wap.gqskj.cn/snews/8095654.htm
- http://m.wap.gqskj.cn/snews/418347.htm
- http://m.wap.gqskj.cn/snews/893666.htm
- http://m.wap.gqskj.cn/snews/37640.htm
- http://m.wap.gqskj.cn/snews/43726.htm
- http://m.wap.gqskj.cn/snews/698935.htm
- http://m.wap.gqskj.cn/snews/575384.htm
- http://m.wap.gqskj.cn/snews/8266.htm
- http://m.wap.gqskj.cn/snews/95699.htm
- http://m.wap.gqskj.cn/snews/886753.htm
- http://m.wap.gqskj.cn/snews/71368.htm
- http://m.wap.gqskj.cn/snews/299089.htm
- http://m.wap.gqskj.cn/snews/590788.htm
- http://m.wap.gqskj.cn/snews/8163314.htm
- http://m.wap.gqskj.cn/snews/5488423.htm
- http://m.wap.gqskj.cn/snews/6654.htm
- http://m.wap.gqskj.cn/snews/25106.htm
- http://m.wap.gqskj.cn/snews/4288145.htm
- http://m.wap.gqskj.cn/snews/83987.htm
- http://m.wap.gqskj.cn/snews/114024.htm
- http://m.wap.gqskj.cn/snews/4868.htm
- http://m.wap.gqskj.cn/snews/8385115.htm
- http://m.wap.gqskj.cn/snews/18404.htm
- http://m.wap.gqskj.cn/snews/863250.htm
- http://m.wap.gqskj.cn/snews/677646.htm
- http://m.wap.gqskj.cn/snews/3537635.htm
- http://m.wap.gqskj.cn/snews/1040701.htm
- http://m.wap.gqskj.cn/snews/144518.htm
- http://m.wap.gqskj.cn/snews/8458.htm
- http://m.wap.gqskj.cn/snews/8164547.htm
- http://m.wap.gqskj.cn/snews/895447.htm
- http://m.wap.gqskj.cn/snews/25410.htm
- http://m.wap.gqskj.cn/snews/4266538.htm
- http://m.wap.gqskj.cn/snews/9247428.htm
- http://m.wap.gqskj.cn/snews/6401.htm
- http://m.wap.gqskj.cn/snews/56287.htm
- http://m.wap.gqskj.cn/snews/7199.htm
- http://m.wap.gqskj.cn/snews/84069.htm
- http://m.wap.gqskj.cn/snews/798262.htm
- http://m.wap.gqskj.cn/snews/00866.htm
- http://m.wap.gqskj.cn/snews/39150.htm
- http://m.wap.gqskj.cn/snews/64434.htm
- http://m.wap.gqskj.cn/snews/791150.htm
- http://m.wap.gqskj.cn/snews/0544033.htm
- http://m.wap.gqskj.cn/snews/203507.htm
- http://m.wap.gqskj.cn/snews/788750.htm
- http://m.wap.gqskj.cn/snews/122315.htm
- http://m.wap.gqskj.cn/snews/56952.htm
- http://m.wap.gqskj.cn/snews/5337.htm
- http://m.wap.gqskj.cn/snews/6853.htm
- http://m.wap.gqskj.cn/snews/7241.htm
- http://m.wap.gqskj.cn/snews/96267.htm
- http://m.wap.gqskj.cn/snews/760643.htm
- http://m.wap.gqskj.cn/snews/5516478.htm
- http://m.wap.gqskj.cn/snews/4571.htm
- http://m.wap.gqskj.cn/snews/565680.htm
- http://m.wap.gqskj.cn/snews/9745.htm
- http://m.wap.gqskj.cn/snews/172540.htm
- http://m.wap.gqskj.cn/snews/94602.htm
- http://m.wap.gqskj.cn/snews/529073.htm
- http://m.wap.gqskj.cn/snews/3804620.htm
- http://m.wap.gqskj.cn/snews/2321203.htm
- http://m.wap.gqskj.cn/snews/29523.htm
- http://m.wap.gqskj.cn/snews/02899.htm
- http://m.wap.gqskj.cn/snews/9199.htm
- http://m.wap.gqskj.cn/snews/43216.htm
- http://m.wap.gqskj.cn/snews/3892955.htm
- http://m.wap.gqskj.cn/snews/65885.htm
- http://m.wap.gqskj.cn/snews/8306668.htm
- http://m.wap.gqskj.cn/snews/083580.htm
- http://m.wap.gqskj.cn/snews/38355.htm
- http://m.wap.gqskj.cn/snews/7846890.htm
- http://m.wap.gqskj.cn/snews/8465492.htm
- http://m.wap.gqskj.cn/snews/830045.htm
- http://m.wap.gqskj.cn/snews/8194.htm
- http://m.wap.gqskj.cn/snews/148192.htm
- http://m.wap.gqskj.cn/snews/980122.htm
- http://m.wap.gqskj.cn/snews/2946531.htm
- http://m.wap.gqskj.cn/snews/404264.htm
- http://m.wap.gqskj.cn/snews/7267007.htm
- http://m.wap.gqskj.cn/snews/1685217.htm
- http://m.wap.gqskj.cn/snews/0692889.htm
- http://m.wap.gqskj.cn/snews/8502055.htm
- http://m.wap.gqskj.cn/snews/3858417.htm
- http://m.wap.gqskj.cn/snews/3892864.htm
- http://m.wap.gqskj.cn/snews/951994.htm
- http://m.wap.gqskj.cn/snews/7232.htm
- http://m.wap.gqskj.cn/snews/6279693.htm
- http://m.wap.gqskj.cn/snews/4143.htm
- http://m.wap.gqskj.cn/snews/9429.htm
- http://m.wap.gqskj.cn/snews/56431.htm
- http://m.wap.gqskj.cn/snews/318798.htm
- http://m.wap.gqskj.cn/snews/4115.htm
- http://m.wap.gqskj.cn/snews/0254196.htm
- http://m.wap.gqskj.cn/snews/67272.htm
- http://m.wap.gqskj.cn/snews/05025.htm
- http://m.wap.gqskj.cn/snews/056976.htm
- http://m.wap.gqskj.cn/snews/4077509.htm

## 项目结构

```
weblink-navigator/
├── cli.py                      # 命令行入口，注册所有子命令
├── config.example.yaml         # 示例配置文件，包含数据库和采集参数模板
├── requirements.txt            # Python 依赖声明，锁定主要版本号
├── src/                        # 核心源码目录
│   ├── collector/              # 采集模块：负责链接抓取和状态检查
│   │   ├── fetcher.py          # 封装 requests/aiohttp 的异步请求池
│   │   └── parser.py           # 使用 BeautifulSoup 提取页面元数据
│   ├── storage/                # 存储模块：处理数据持久化
│   │   ├── database.py         # SQLite 连接池与 CRUD 操作封装
│   │   └── serializer.py       # 导出为 JSON / CSV / Parquet 格式
│   ├── rules/                  # 规则引擎：分类标签与过滤逻辑
│   │   ├── classifier.py       # 基于路径和关键词的自动打标器
│   │   └── filter.py           # 黑白名单匹配与作用域判定
│   └── utils/                  # 通用工具函数
│       ├── logger.py           # 结构化日志配置，支持文件与控制台双输出
│       └── validator.py        # URL 合法性校验与协议规范化
├── tests/                      # 单元测试与集成测试用例
│   ├── test_fetcher.py         # 模拟 HTTP 响应的请求层测试
│   └── test_classifier.py      # 分类规则覆盖率和准确性测试
├── data/                       # 数据目录（自动生成，默认存放索引文件）
│   └── index.json              # 主索引输出文件示例
├── docs/                       # 完整文档目录，涵盖入门到高级主题
│   ├── getting_started.md
│   ├── configuration.md
│   ├── api_reference.md
│   ├── workflow.md
│   ├── data_dictionary.md
│   └── troubleshooting.md
└── scripts/                    # 运维辅助脚本
    ├── migrate_db.py           # 数据库版本迁移工具
    └── health_check.py         # 定时健康检查的独立运行脚本
```

## 贡献指南

我们欢迎社区提交各类贡献，包括但不限于新功能开发、文档完善、缺陷修复和用例补充。请遵循以下流程以保证协作效率。

首先，在 GitHub 上 Fork 本仓库，并将您的 Fork 克隆到本地开发环境中。请确保您的主分支与上游仓库保持同步。

其次，对于任何非琐碎的变更，请先在我们的 Issue 列表中搜索是否已有相关讨论。如果没有，请新建一个 Issue 描述您要解决的问题或提议的新特性，等待维护者反馈后再开始编码。

第三，所有代码变更必须通过现有的单元测试，并且如果引入新功能，请补充对应的测试用例。代码风格应遵循 PEP 8 规范，并且所有公共函数和类必须包含文档字符串。

第四，提交 Pull Request 时，请填写完整的模板内容，包括变更摘要、测试覆盖情况以及是否影响现有配置格式。PR 标题应使用简洁的动词开头，例如 "Add retry mechanism for failed requests"。

最后，文档更新与代码变更同等重要。如果您的改动影响了配置项、命令行参数或输出数据结构，请同步更新 docs 目录下的对应文档。

## 常见问题

问题：采集任务执行过程中频繁超时，如何调整超时阈值？

答：可以在 config.yaml 文件的 collector 部分设置 timeout 字段，单位为秒。默认值为 30 秒。对于响应较慢的源站，建议将该值调至 60 至 120 秒。同时可以启用 aiohttp 的限速参数，减少并发数以降低网络拥塞概率。

问题：数据库文件不断增长，是否有自动清理机制？

答：项目提供了 data_retention_days 配置项，默认为 90 天。在每次运行采集任务时，系统会自动清除最后修改时间早于该天数的链接记录。您也可以手动执行 scripts/cleanup.py 脚本进行按需清理。注意该操作不可逆，建议提前导出历史数据。

问题：如何自定义分类标签的规则？

答：规则定义位于 src/rules/classifier.py 中的 PATTERN_MAP 字典。每个条目由一个正则表达式模式和一个对应的标签列表组成。您可以根据需要添加或修改条目，然后重新运行采集任务。修改后建议执行 tests/test_classifier.py 验证规则覆盖率是否符合预期。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
