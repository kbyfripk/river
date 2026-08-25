# XNews 聚合网关

XNews 聚合网关是一个轻量级的技术资讯与新闻外链统一收束系统，面向开发团队、技术内容运营者以及个人研究者，用于将散落在移动端资讯源中的高质量技术报道、版本发布、安全通告与行业分析进行集中化收录与结构化暴露。该项目不提供内容存储，仅作为 URL 索引与元信息标注层，通过确定性路由规则将原始移动端新闻页（xnews）映射为可被持续集成的外链资源池，适用于构建企业内部技术情报看板、日报自动聚合服务或第三方新闻订阅源的中转节点。

系统核心定位为“只做索引，不落内容；保持原链，不做改写”，所有原始 URL 在进入系统后即被锁定为不可变条目，确保下游消费方始终获得与源站一致的访问路径。项目面向已有移动端资讯阅读习惯但缺乏统一组织手段的团队，提供一套基于文件系统约定的目录化资源管理方案，使数百乃至上千条外链能够以可维护、可追溯的方式纳入版本控制体系。

## 功能概览

- **原始链接不可变收录**：所有提交的 xnews 类 URL 保持原始协议、域名、路径及查询参数，系统不进行任何形式的协议升级、域名规范化或路径改写，确保源站访问语义不被破坏。

- **批量导入与去重校验**：支持通过文本流或标准输入批量导入 URL 清单，自动执行基于完整 URL 字符串的精确去重，并对同批次内重复提交、路径参数变异进行标记提示。

- **确定性路由生成**：依据文件名与路径层级自动生成稳定且可预测的访问路由，便于下游脚本、爬虫或监控程序直接构造目标地址，无需额外查询接口。

- **元信息标注扩展**：每条外链可附加可选的标签（tag）、状态标记（有效/失效）及更新周期说明，这些标注信息存储于独立的元数据目录中，与原始链接列表解耦。

- **定期健康检查钩子**：内置简单的 HTTP HEAD 请求预检能力，可对收录链接进行批量可达性探测，并将超时、非 2xx 响应、证书异常等结果输出为结构化日志，辅助运维人员清理无效资源。

- **静态站点生成适配**：项目目录结构设计天然兼容静态站点生成器（如 Hugo、Jekyll），可快速将外链列表渲染为带分类索引的 HTML 页面，适合发布为内部技术导航站。

## 应用场景

**企业内部技术日报自动化**：运维或研发效能团队每日定时拉取本系统收录的最新 xnews 链接，结合元信息中的分类标签，自动生成 Markdown 格式的日报并推送至企业即时通讯群组，减少人工筛选成本。

**开源项目外部依赖追踪**：开源项目维护者可将与自身依赖库相关的版本发布新闻、安全漏洞通告等 xnews 链接集中收录于本系统，通过定期对比收录时间戳与外部公告发布时间，及时发现依赖风险。

**移动端资讯转存为结构化归档**：内容运营人员将日常在移动端浏览到的有价值技术资讯逐条提交至本系统，系统保留原始移动页面链接的同时，允许在元数据中记录摘要、推荐等级与阅读状态，形成个人或团队的技术阅读清单。

**技术会议或活动资源整理**：在筹备技术沙龙或内部分享会时，组织者可将参考材料、往期视频回放、嘉宾博客等外链通过本系统统一管理，并按主题分目录存放，便于会前准备与会后资料沉淀。

## 快速开始

以下指令演示了如何从代码仓库获取项目、安装基础依赖并启动本地预览服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/xnews-gateway.git

# 进入项目根目录
cd xnews-gateway

# 安装 Python 运行时依赖（需 Python 3.8+）
pip install -r requirements.txt

# 执行收录脚本，导入示例 URL 清单
python scripts/ingest.py --input samples/urls.txt --output data/manifest.json

# 启动本地静态预览服务（默认监听 8000 端口）
python -m http.server --directory public
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心收录脚本与工具链运行环境 |
| pip | 20.0 及以上 | Python 包管理器，用于安装依赖库 |
| Git | 2.25 及以上 | 用于克隆仓库与版本管理 |
| curl | 7.68 及以上 | 健康检查脚本中的 HTTP 探测工具 |
| make | 3.81 及以上 | 可选，用于执行自动化任务（构建、测试） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何首次运行、导入链接并生成预览页面 |
| 元数据规范 | docs/metadata-spec.md | 标签、状态、更新周期等字段的定义与格式要求 |
| 路由设计 | docs/routing-design.md | 链接到本地路径的映射规则及冲突解决策略 |
| 运维手册 | docs/operations.md | 健康检查、日志轮转、数据备份与恢复方法 |

## 资源列表

- http://m.3g.gqskj.cn/xnews/31655.htm
- http://m.3g.gqskj.cn/xnews/6065741.htm
- http://m.3g.gqskj.cn/xnews/5935.htm
- http://m.3g.gqskj.cn/xnews/9722.htm
- http://m.3g.gqskj.cn/xnews/9216.htm
- http://m.3g.gqskj.cn/xnews/77579.htm
- http://m.3g.gqskj.cn/xnews/704971.htm
- http://m.3g.gqskj.cn/xnews/573101.htm
- http://m.3g.gqskj.cn/xnews/1043750.htm
- http://m.3g.gqskj.cn/xnews/755684.htm
- http://m.3g.gqskj.cn/xnews/140845.htm
- http://m.3g.gqskj.cn/xnews/44768.htm
- http://m.3g.gqskj.cn/xnews/9913.htm
- http://m.3g.gqskj.cn/xnews/3133.htm
- http://m.3g.gqskj.cn/xnews/673598.htm
- http://m.3g.gqskj.cn/xnews/8069.htm
- http://m.3g.gqskj.cn/xnews/9296509.htm
- http://m.3g.gqskj.cn/xnews/0918.htm
- http://m.3g.gqskj.cn/xnews/5166022.htm
- http://m.3g.gqskj.cn/xnews/2533866.htm
- http://m.3g.gqskj.cn/xnews/94238.htm
- http://m.3g.gqskj.cn/xnews/5534998.htm
- http://m.3g.gqskj.cn/xnews/4627718.htm
- http://m.3g.gqskj.cn/xnews/1475.htm
- http://m.3g.gqskj.cn/xnews/2229.htm
- http://m.3g.gqskj.cn/xnews/9081.htm
- http://m.3g.gqskj.cn/xnews/7864798.htm
- http://m.3g.gqskj.cn/xnews/875713.htm
- http://m.3g.gqskj.cn/xnews/0593.htm
- http://m.3g.gqskj.cn/xnews/3959292.htm
- http://m.3g.gqskj.cn/xnews/3071716.htm
- http://m.3g.gqskj.cn/xnews/9207.htm
- http://m.3g.gqskj.cn/xnews/221815.htm
- http://m.3g.gqskj.cn/xnews/5955.htm
- http://m.3g.gqskj.cn/xnews/101474.htm
- http://m.3g.gqskj.cn/xnews/7044175.htm
- http://m.3g.gqskj.cn/xnews/56782.htm
- http://m.3g.gqskj.cn/xnews/58515.htm
- http://m.3g.gqskj.cn/xnews/6055.htm
- http://m.3g.gqskj.cn/xnews/040284.htm
- http://m.3g.gqskj.cn/xnews/61499.htm
- http://m.3g.gqskj.cn/xnews/724741.htm
- http://m.3g.gqskj.cn/xnews/84291.htm
- http://m.3g.gqskj.cn/xnews/4645811.htm
- http://m.3g.gqskj.cn/xnews/422752.htm
- http://m.3g.gqskj.cn/xnews/4967396.htm
- http://m.3g.gqskj.cn/xnews/8579.htm
- http://m.3g.gqskj.cn/xnews/4394458.htm
- http://m.3g.gqskj.cn/xnews/9912305.htm
- http://m.3g.gqskj.cn/xnews/003832.htm
- http://m.3g.gqskj.cn/xnews/6640857.htm
- http://m.3g.gqskj.cn/xnews/1291914.htm
- http://m.3g.gqskj.cn/xnews/3281864.htm
- http://m.3g.gqskj.cn/xnews/8659767.htm
- http://m.3g.gqskj.cn/xnews/97467.htm
- http://m.3g.gqskj.cn/xnews/4049.htm
- http://m.3g.gqskj.cn/xnews/3147951.htm
- http://m.3g.gqskj.cn/xnews/46331.htm
- http://m.3g.gqskj.cn/xnews/837012.htm
- http://m.3g.gqskj.cn/xnews/46967.htm
- http://m.3g.gqskj.cn/xnews/101053.htm
- http://m.3g.gqskj.cn/xnews/6341930.htm
- http://m.3g.gqskj.cn/xnews/271903.htm
- http://m.3g.gqskj.cn/xnews/3885861.htm
- http://m.3g.gqskj.cn/xnews/6165.htm
- http://m.3g.gqskj.cn/xnews/41665.htm
- http://m.3g.gqskj.cn/xnews/88002.htm
- http://m.3g.gqskj.cn/xnews/47464.htm
- http://m.3g.gqskj.cn/xnews/905197.htm
- http://m.3g.gqskj.cn/xnews/77301.htm
- http://m.3g.gqskj.cn/xnews/805338.htm
- http://m.3g.gqskj.cn/xnews/9045044.htm
- http://m.3g.gqskj.cn/xnews/420355.htm
- http://m.3g.gqskj.cn/xnews/215142.htm
- http://m.3g.gqskj.cn/xnews/7812779.htm
- http://m.3g.gqskj.cn/xnews/12713.htm
- http://m.3g.gqskj.cn/xnews/150787.htm
- http://m.3g.gqskj.cn/xnews/30109.htm
- http://m.3g.gqskj.cn/xnews/1733.htm
- http://m.3g.gqskj.cn/xnews/9493912.htm
- http://m.3g.gqskj.cn/xnews/319241.htm
- http://m.3g.gqskj.cn/xnews/0527483.htm
- http://m.3g.gqskj.cn/xnews/3755696.htm
- http://m.3g.gqskj.cn/xnews/8595390.htm
- http://m.3g.gqskj.cn/xnews/8636.htm
- http://m.3g.gqskj.cn/xnews/624366.htm
- http://m.3g.gqskj.cn/xnews/108015.htm
- http://m.3g.gqskj.cn/xnews/331794.htm
- http://m.3g.gqskj.cn/xnews/7136664.htm
- http://m.3g.gqskj.cn/xnews/2086.htm
- http://m.3g.gqskj.cn/xnews/00979.htm
- http://m.3g.gqskj.cn/xnews/75264.htm
- http://m.3g.gqskj.cn/xnews/273877.htm
- http://m.3g.gqskj.cn/xnews/5678.htm
- http://m.3g.gqskj.cn/xnews/600062.htm
- http://m.3g.gqskj.cn/xnews/84503.htm
- http://m.3g.gqskj.cn/xnews/19456.htm
- http://m.3g.gqskj.cn/xnews/44297.htm
- http://m.3g.gqskj.cn/xnews/8449338.htm
- http://m.3g.gqskj.cn/xnews/119060.htm
- http://m.3g.gqskj.cn/xnews/1016110.htm
- http://m.3g.gqskj.cn/xnews/7005438.htm
- http://m.3g.gqskj.cn/xnews/906740.htm
- http://m.3g.gqskj.cn/xnews/6401644.htm
- http://m.3g.gqskj.cn/xnews/8667392.htm
- http://m.3g.gqskj.cn/xnews/3454.htm
- http://m.3g.gqskj.cn/xnews/66643.htm
- http://m.3g.gqskj.cn/xnews/7727.htm
- http://m.3g.gqskj.cn/xnews/66986.htm
- http://m.3g.gqskj.cn/xnews/320049.htm
- http://m.3g.gqskj.cn/xnews/91670.htm
- http://m.3g.gqskj.cn/xnews/832577.htm
- http://m.3g.gqskj.cn/xnews/85649.htm
- http://m.3g.gqskj.cn/xnews/4536785.htm
- http://m.3g.gqskj.cn/xnews/397760.htm
- http://m.3g.gqskj.cn/xnews/5249.htm
- http://m.3g.gqskj.cn/xnews/789280.htm
- http://m.3g.gqskj.cn/xnews/13391.htm
- http://m.3g.gqskj.cn/xnews/9907.htm
- http://m.3g.gqskj.cn/xnews/403070.htm
- http://m.3g.gqskj.cn/xnews/065917.htm
- http://m.3g.gqskj.cn/xnews/01727.htm
- http://m.3g.gqskj.cn/xnews/57843.htm
- http://m.3g.gqskj.cn/xnews/749095.htm
- http://m.3g.gqskj.cn/xnews/2682.htm
- http://m.3g.gqskj.cn/xnews/493276.htm
- http://m.3g.gqskj.cn/xnews/4741587.htm
- http://m.3g.gqskj.cn/xnews/16412.htm
- http://m.3g.gqskj.cn/xnews/1389.htm
- http://m.3g.gqskj.cn/xnews/182603.htm
- http://m.3g.gqskj.cn/xnews/97951.htm
- http://m.3g.gqskj.cn/xnews/1801390.htm
- http://m.3g.gqskj.cn/xnews/13908.htm
- http://m.3g.gqskj.cn/xnews/750693.htm
- http://m.3g.gqskj.cn/xnews/2918424.htm
- http://m.3g.gqskj.cn/xnews/007914.htm
- http://m.3g.gqskj.cn/xnews/95033.htm
- http://m.3g.gqskj.cn/xnews/4696043.htm
- http://m.3g.gqskj.cn/xnews/9729706.htm
- http://m.3g.gqskj.cn/xnews/5319.htm
- http://m.3g.gqskj.cn/xnews/6137664.htm
- http://m.3g.gqskj.cn/xnews/8790.htm
- http://m.3g.gqskj.cn/xnews/90344.htm
- http://m.3g.gqskj.cn/xnews/70345.htm
- http://m.3g.gqskj.cn/xnews/542336.htm
- http://m.3g.gqskj.cn/xnews/4026657.htm
- http://m.3g.gqskj.cn/xnews/74676.htm
- http://m.3g.gqskj.cn/xnews/1741.htm
- http://m.3g.gqskj.cn/xnews/058508.htm
- http://m.3g.gqskj.cn/xnews/8670165.htm
- http://m.3g.gqskj.cn/xnews/9783.htm
- http://m.3g.gqskj.cn/xnews/1473.htm
- http://m.3g.gqskj.cn/xnews/356701.htm
- http://m.3g.gqskj.cn/xnews/929379.htm
- http://m.3g.gqskj.cn/xnews/113643.htm
- http://m.3g.gqskj.cn/xnews/5749.htm
- http://m.3g.gqskj.cn/xnews/2415470.htm
- http://m.3g.gqskj.cn/xnews/8063643.htm
- http://m.3g.gqskj.cn/xnews/8259.htm
- http://m.3g.gqskj.cn/xnews/3649071.htm
- http://m.3g.gqskj.cn/xnews/17043.htm
- http://m.3g.gqskj.cn/xnews/230893.htm
- http://m.3g.gqskj.cn/xnews/6455461.htm
- http://m.3g.gqskj.cn/xnews/65294.htm
- http://m.3g.gqskj.cn/xnews/67819.htm
- http://m.3g.gqskj.cn/xnews/0247366.htm
- http://m.3g.gqskj.cn/xnews/698934.htm
- http://m.3g.gqskj.cn/xnews/900878.htm
- http://m.3g.gqskj.cn/xnews/2977149.htm
- http://m.3g.gqskj.cn/xnews/0640.htm
- http://m.3g.gqskj.cn/xnews/688546.htm
- http://m.3g.gqskj.cn/xnews/4817.htm
- http://m.3g.gqskj.cn/xnews/8584635.htm
- http://m.3g.gqskj.cn/xnews/0615.htm
- http://m.3g.gqskj.cn/xnews/5747336.htm
- http://m.3g.gqskj.cn/xnews/61695.htm
- http://m.3g.gqskj.cn/xnews/70102.htm
- http://m.3g.gqskj.cn/xnews/241375.htm
- http://m.3g.gqskj.cn/xnews/4494.htm
- http://m.3g.gqskj.cn/xnews/840764.htm
- http://m.3g.gqskj.cn/xnews/93729.htm
- http://m.3g.gqskj.cn/xnews/943419.htm
- http://m.3g.gqskj.cn/xnews/1514439.htm
- http://m.3g.gqskj.cn/xnews/8409400.htm
- http://m.3g.gqskj.cn/xnews/0030049.htm
- http://m.3g.gqskj.cn/xnews/22068.htm
- http://m.3g.gqskj.cn/xnews/343169.htm
- http://m.3g.gqskj.cn/xnews/12896.htm
- http://m.3g.gqskj.cn/xnews/593981.htm
- http://m.3g.gqskj.cn/xnews/08101.htm
- http://m.3g.gqskj.cn/xnews/3088286.htm
- http://m.3g.gqskj.cn/xnews/3681964.htm
- http://m.3g.gqskj.cn/xnews/37568.htm
- http://m.3g.gqskj.cn/xnews/480045.htm
- http://m.3g.gqskj.cn/xnews/1824.htm
- http://m.3g.gqskj.cn/xnews/176014.htm
- http://m.3g.gqskj.cn/xnews/2605.htm
- http://m.3g.gqskj.cn/xnews/7997.htm
- http://m.3g.gqskj.cn/xnews/69537.htm
- http://m.3g.gqskj.cn/xnews/9462419.htm
- http://m.3g.gqskj.cn/xnews/99510.htm
- http://m.3g.gqskj.cn/xnews/51841.htm
- http://m.3g.gqskj.cn/xnews/0238326.htm
- http://m.3g.gqskj.cn/xnews/4308370.htm
- http://m.3g.gqskj.cn/xnews/65769.htm
- http://m.3g.gqskj.cn/xnews/650486.htm
- http://m.3g.gqskj.cn/xnews/26057.htm
- http://m.3g.gqskj.cn/xnews/1578.htm
- http://m.3g.gqskj.cn/xnews/776985.htm
- http://m.3g.gqskj.cn/xnews/94072.htm
- http://m.3g.gqskj.cn/xnews/831819.htm
- http://m.3g.gqskj.cn/xnews/3850.htm
- http://m.3g.gqskj.cn/xnews/4329709.htm
- http://m.3g.gqskj.cn/xnews/830960.htm
- http://m.3g.gqskj.cn/xnews/859466.htm
- http://m.3g.gqskj.cn/xnews/0985.htm
- http://m.3g.gqskj.cn/xnews/8141042.htm
- http://m.3g.gqskj.cn/xnews/61688.htm
- http://m.3g.gqskj.cn/xnews/0280.htm
- http://m.3g.gqskj.cn/xnews/23854.htm
- http://m.3g.gqskj.cn/xnews/25310.htm
- http://m.3g.gqskj.cn/xnews/5236.htm
- http://m.3g.gqskj.cn/xnews/13762.htm
- http://m.3g.gqskj.cn/xnews/7532058.htm
- http://m.3g.gqskj.cn/xnews/33662.htm
- http://m.3g.gqskj.cn/xnews/602082.htm
- http://m.3g.gqskj.cn/xnews/9439.htm
- http://m.3g.gqskj.cn/xnews/63025.htm
- http://m.3g.gqskj.cn/xnews/2610.htm
- http://m.3g.gqskj.cn/xnews/7153.htm
- http://m.3g.gqskj.cn/xnews/3940361.htm
- http://m.3g.gqskj.cn/xnews/7300030.htm
- http://m.3g.gqskj.cn/xnews/0733.htm
- http://m.3g.gqskj.cn/xnews/4566867.htm
- http://m.3g.gqskj.cn/xnews/4509.htm
- http://m.3g.gqskj.cn/xnews/0726.htm
- http://m.3g.gqskj.cn/xnews/7512962.htm
- http://m.3g.gqskj.cn/xnews/944553.htm
- http://m.3g.gqskj.cn/xnews/63864.htm
- http://m.3g.gqskj.cn/xnews/7782577.htm
- http://m.3g.gqskj.cn/xnews/02763.htm
- http://m.3g.gqskj.cn/xnews/2892763.htm
- http://m.3g.gqskj.cn/xnews/62681.htm
- http://m.3g.gqskj.cn/xnews/602200.htm
- http://m.3g.gqskj.cn/xnews/222317.htm
- http://m.3g.gqskj.cn/xnews/101655.htm
- http://m.3g.gqskj.cn/xnews/02471.htm
- http://m.3g.gqskj.cn/xnews/976855.htm
- http://m.3g.gqskj.cn/xnews/6491.htm
- http://m.3g.gqskj.cn/xnews/513979.htm

## 项目结构

```
xnews-gateway/
├── data/                                # 核心数据目录，存放收录清单及元信息
│   ├── manifest.json                    # 主索引文件，记录所有外链的完整 URL 与收录时间戳
│   ├── metadata/                        # 元数据扩展目录，每个 URL 对应一个 .meta 文件
│   │   ├── 31655.meta                   # 示例元数据文件，记录标签、状态、备注
│   │   └── ...
│   └── checksums/                       # 校验和目录，用于检测清单变动与去重
│       └── sha256.txt                   # 所有收录 URL 的哈希快照
├── scripts/                             # 运维与工具脚本
│   ├── ingest.py                        # 核心收录脚本，支持从文件或标准输入导入 URL
│   ├── health_check.py                  # 健康检查脚本，并发探测 URL 可达性
│   └── render_static.py                 # 静态页面生成器，将清单渲染为 HTML 导航
├── public/                              # 静态站点输出目录，可直接部署至 Web 服务器
│   ├── index.html                       # 首页，展示分类索引与最新收录
│   └── assets/                          # 样式与前端资源
│       ├── style.css
│       └── app.js
├── docs/                                # 项目文档源码
│   ├── getting-started.md
│   ├── metadata-spec.md
│   ├── routing-design.md
│   └── operations.md
├── tests/                               # 单元测试与集成测试用例
│   ├── test_ingest.py                   # 测试收录逻辑与去重算法
│   └── test_routing.py                  # 测试路由生成与路径规范化
├── .github/                             # GitHub Actions 工作流配置
│   └── workflows/
│       └── ci.yml                       # 持续集成：提交时运行测试与静态检查
├── requirements.txt                     # Python 依赖清单
├── Makefile                             # 自动化任务入口（构建、测试、清理）
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

1. 阅读项目文档中的元数据规范与路由设计文档，确认您要提交的 URL 符合收录范围，并理解标签体系与状态字段的含义。

2. 从主分支 fork 项目仓库，在本地新建一个以 `feature/` 或 `fix/` 为前缀的分支，避免直接向主分支提交。

3. 在 `data/manifest.json` 中追加新的 URL 条目，若需附加元信息，请在 `data/metadata/` 目录下创建对应的 `.meta` 文件，遵循 JSON 格式填写标签、状态与备注字段。

4. 运行测试套件确保现有功能未被破坏：执行 `make test` 或 `pytest tests/`，并检查健康检查脚本对新加入的 URL 是否产生异常日志。

5. 提交 pull request，在描述中简要说明新增 URL 的来源或用途，等待项目维护者审阅。合并后，CI 流水线将自动更新静态站点并重新生成索引快照。

## 常见问题

**Q：为什么必须保持原始 URL 完全不变，不能进行协议升级或域名规范化？**

A：本项目定位为纯粹的索引与转发层，不对源站内容做任何假设。源站可能基于特定协议或域名路径进行访问控制、日志统计或业务路由，任何改写都可能导致用户访问失败或源站统计数据失真。保持原始 URL 是确保链路可追溯性与源站语义完整性的基本前提。

**Q：收录的 URL 数量很大时，健康检查会不会对源站造成压力？**

A：健康检查脚本默认采用并发控制（并发数可通过 `--concurrency` 参数调节），并内置随机抖动延迟以避免请求集中在同一时间窗口。此外，检查仅发送 HTTP HEAD 请求，不下载响应体，对源站负载影响极小。建议在生产环境中将健康检查频率设置为每日一次或每周两次，避免高频探测。

**Q：元数据文件丢失或格式错误会怎样？**

A：系统会忽略无法解析的元数据文件，并在日志中输出警告信息，但不会影响主清单的正常加载与页面渲染。您可以通过 `scripts/validate_metadata.py` 工具对元数据目录进行批量校验，定位格式错误的文件并修复。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:47
