# LinkIndex Core

LinkIndex Core 是一个面向技术文档聚合与外部资源链接管理的轻量级静态站点生成工具。该项目主要服务于需要批量整理、分类展示和快速检索大量外部 URL 的技术内容运营团队、开源文档维护者以及个人知识库构建者。LinkIndex Core 不提供数据库或后端服务，完全基于 Markdown 源文件与配置文件生成纯静态 HTML 页面，可部署于任何支持 HTTP 服务的托管平台。

该项目解决的核心问题是技术文档中外部链接分散、分类模糊、无法批量校验可用性以及缺乏统一索引视图的痛点。通过约定优于配置的目录结构和基于元数据的渲染流水线，LinkIndex Core 能够将数千条外链资源在数秒内组织为具备多维度筛选能力的信息导航站点。

## 功能概览

- 批量 URL 导入与规范化：支持从纯文本列表、CSV 和 JSON 格式批量导入外部链接，自动完成 URL 去重、协议补全检测以及非法字符过滤。

- 多级分类与标签系统：每个资源条目可绑定多个分类标签，支持无限级分类嵌套，分类定义独立存储于配置文件，便于跨项目复用。

- 链接状态健康检查：内置异步 HTTP 状态码检测器，可定期对全部或指定分类下的外部链接执行可达性验证，输出失效链接报告。

- 全文检索与过滤：生成静态页面时内置基于 Lunr.js 的客户端全文检索引擎，支持按标题、描述、分类、标签和 URL 关键字快速过滤。

- 响应式列表视图与卡片视图：提供两种资源展示布局，列表视图适合快速扫读，卡片视图适合展示富文本描述与缩略图预览，自动适配移动端。

- 元数据模板化渲染：支持 YAML 或 JSON 格式的元数据扩展字段，用户可在链接条目中自定义键值对，并在生成页面时通过模板引擎渲染为自定义区块。

- 增量构建与缓存机制：仅对变更的源文件重新生成对应页面，未变更内容直接复用缓存，显著降低大规模资源站点的构建耗时。

## 应用场景

技术文档站点的外部引用管理：企业技术文档中心通常包含大量指向第三方规范、SDK 下载页、API 参考手册的外部链接。LinkIndex Core 可作为文档站点的子模块独立运行，维护这些外部引用的最新状态，并自动生成引用关系图谱。

开源项目社区资源汇总：开源项目维护者可使用 LinkIndex Core 构建社区插件、工具链和教程资源的导航页，替代静态 README 中冗长且难以维护的列表，社区贡献者可通过 Pull Request 更新资源条目而无需重新构建整个站点。

个人技术收藏夹的知识化管理：开发者可将多年积累的技术博文、在线工具、学术论文和视频教程等收藏链接导入 LinkIndex Core，通过自定义标签和分类进行深度整理，并利用内置的全文检索功能快速定位历史收藏内容。

## 快速开始

以下指令演示如何在本地环境获取源码、安装依赖并启动开发服务器。

```bash
# 克隆项目仓库
git clone https://github.com/linkindex/core.git linkindex-core

# 进入项目目录
cd linkindex-core

# 安装依赖（使用 npm）
npm install

# 运行开发构建与本地预览服务
npm run dev
```

执行上述命令后，终端将输出本地预览地址，默认监听 8080 端口。开发者可在 `./content/links` 目录下添加或修改 `.md` 资源文件，保存后页面将自动热重载。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.0.0 或更高 | 运行时环境与包管理基础 |
| npm | 9.0.0 或更高 | 依赖安装与脚本执行工具 |
| Git | 2.30.0 或更高 | 源码克隆与版本控制 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 需启用 WSL 或使用 PowerShell 7 |
| 网络带宽 | 不低于 1 Mbps | 用于链接健康检查时的并发 HTTP 请求，离线构建无需网络 |
| 内存 | 建议 512 MB 以上 | 处理超过 1 万条资源条目时的最低建议配置 |
| 硬盘空间 | 200 MB 以上 | 包含源码、依赖及构建缓存，不包含用户生成的静态页面输出 |
| Python 3 | 可选（3.8+） | 仅当启用外部链接截图缩略图生成功能时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/guide/ | 如何安装、配置、运行和部署 LinkIndex Core 站点 |
| 配置参考 | /docs/config/ | 所有配置文件字段的含义、默认值和合法取值范围 |
| 内容格式 | /docs/content/ | 资源条目 Markdown 的 frontmatter 头部字段、正文格式和示例 |
| 开发指南 | /docs/developer/ | 插件扩展、主题定制、构建流水线改造和 API 接口说明 |

## 资源列表

- http://m.wap.gqskj.cn/snews/566807.htm
- http://m.wap.gqskj.cn/snews/28715.htm
- http://m.wap.gqskj.cn/snews/837993.htm
- http://m.wap.gqskj.cn/snews/16312.htm
- http://m.wap.gqskj.cn/snews/53122.htm
- http://m.wap.gqskj.cn/snews/3353818.htm
- http://m.wap.gqskj.cn/snews/257692.htm
- http://m.wap.gqskj.cn/snews/1685409.htm
- http://m.wap.gqskj.cn/snews/92561.htm
- http://m.wap.gqskj.cn/snews/8394.htm
- http://m.wap.gqskj.cn/snews/58519.htm
- http://m.wap.gqskj.cn/snews/1445353.htm
- http://m.wap.gqskj.cn/snews/212943.htm
- http://m.wap.gqskj.cn/snews/7348237.htm
- http://m.wap.gqskj.cn/snews/22114.htm
- http://m.wap.gqskj.cn/snews/580584.htm
- http://m.wap.gqskj.cn/snews/0648560.htm
- http://m.wap.gqskj.cn/snews/5668529.htm
- http://m.wap.gqskj.cn/snews/583701.htm
- http://m.wap.gqskj.cn/snews/2887.htm
- http://m.wap.gqskj.cn/snews/8200107.htm
- http://m.wap.gqskj.cn/snews/0909484.htm
- http://m.wap.gqskj.cn/snews/8256.htm
- http://m.wap.gqskj.cn/snews/251076.htm
- http://m.wap.gqskj.cn/snews/74742.htm
- http://m.wap.gqskj.cn/snews/6796426.htm
- http://m.wap.gqskj.cn/snews/60330.htm
- http://m.wap.gqskj.cn/snews/9528.htm
- http://m.wap.gqskj.cn/snews/0924013.htm
- http://m.wap.gqskj.cn/snews/72566.htm
- http://m.wap.gqskj.cn/snews/1506079.htm
- http://m.wap.gqskj.cn/snews/408599.htm
- http://m.wap.gqskj.cn/snews/2399.htm
- http://m.wap.gqskj.cn/snews/98885.htm
- http://m.wap.gqskj.cn/snews/9993.htm
- http://m.wap.gqskj.cn/snews/135769.htm
- http://m.wap.gqskj.cn/snews/236397.htm
- http://m.wap.gqskj.cn/snews/16401.htm
- http://m.wap.gqskj.cn/snews/3472.htm
- http://m.wap.gqskj.cn/snews/899145.htm
- http://m.wap.gqskj.cn/snews/13474.htm
- http://m.wap.gqskj.cn/snews/07689.htm
- http://m.wap.gqskj.cn/snews/40890.htm
- http://m.wap.gqskj.cn/snews/562827.htm
- http://m.wap.gqskj.cn/snews/7051.htm
- http://m.wap.gqskj.cn/snews/2286.htm
- http://m.wap.gqskj.cn/snews/28067.htm
- http://m.wap.gqskj.cn/snews/8768504.htm
- http://m.wap.gqskj.cn/snews/77609.htm
- http://m.wap.gqskj.cn/snews/5648.htm
- http://m.wap.gqskj.cn/snews/8600512.htm
- http://m.wap.gqskj.cn/snews/54254.htm
- http://m.wap.gqskj.cn/snews/646528.htm
- http://m.wap.gqskj.cn/snews/1148.htm
- http://m.wap.gqskj.cn/snews/239597.htm
- http://m.wap.gqskj.cn/snews/471192.htm
- http://m.wap.gqskj.cn/snews/753525.htm
- http://m.wap.gqskj.cn/snews/3251.htm
- http://m.wap.gqskj.cn/snews/16181.htm
- http://m.wap.gqskj.cn/snews/2536.htm
- http://m.wap.gqskj.cn/snews/11043.htm
- http://m.wap.gqskj.cn/snews/12048.htm
- http://m.wap.gqskj.cn/snews/5255.htm
- http://m.wap.gqskj.cn/snews/1983.htm
- http://m.wap.gqskj.cn/snews/5306271.htm
- http://m.wap.gqskj.cn/snews/91968.htm
- http://m.wap.gqskj.cn/snews/159843.htm
- http://m.wap.gqskj.cn/snews/5579992.htm
- http://m.wap.gqskj.cn/snews/585757.htm
- http://m.wap.gqskj.cn/snews/0146470.htm
- http://m.wap.gqskj.cn/snews/8289.htm
- http://m.wap.gqskj.cn/snews/296918.htm
- http://m.wap.gqskj.cn/snews/056995.htm
- http://m.wap.gqskj.cn/snews/701455.htm
- http://m.wap.gqskj.cn/snews/5462400.htm
- http://m.wap.gqskj.cn/snews/822009.htm
- http://m.wap.gqskj.cn/snews/8783087.htm
- http://m.wap.gqskj.cn/snews/39878.htm
- http://m.wap.gqskj.cn/snews/1288503.htm
- http://m.wap.gqskj.cn/snews/4077.htm
- http://m.wap.gqskj.cn/snews/88429.htm
- http://m.wap.gqskj.cn/snews/328223.htm
- http://m.wap.gqskj.cn/snews/608828.htm
- http://m.wap.gqskj.cn/snews/3260875.htm
- http://m.wap.gqskj.cn/snews/7445.htm
- http://m.wap.gqskj.cn/snews/5022687.htm
- http://m.wap.gqskj.cn/snews/98597.htm
- http://m.wap.gqskj.cn/snews/0709790.htm
- http://m.wap.gqskj.cn/snews/6229286.htm
- http://m.wap.gqskj.cn/snews/3422803.htm
- http://m.wap.gqskj.cn/snews/0917.htm
- http://m.wap.gqskj.cn/snews/06538.htm
- http://m.wap.gqskj.cn/snews/2180994.htm
- http://m.wap.gqskj.cn/snews/9904.htm
- http://m.wap.gqskj.cn/snews/2847530.htm
- http://m.wap.gqskj.cn/snews/636593.htm
- http://m.wap.gqskj.cn/snews/89323.htm
- http://m.wap.gqskj.cn/snews/200340.htm
- http://m.wap.gqskj.cn/snews/2597.htm
- http://m.wap.gqskj.cn/snews/9431.htm
- http://m.wap.gqskj.cn/snews/30352.htm
- http://m.wap.gqskj.cn/snews/81429.htm
- http://m.wap.gqskj.cn/snews/5879.htm
- http://m.wap.gqskj.cn/snews/173756.htm
- http://m.wap.gqskj.cn/snews/6689794.htm
- http://m.wap.gqskj.cn/snews/6841.htm
- http://m.wap.gqskj.cn/snews/537856.htm
- http://m.wap.gqskj.cn/snews/07847.htm
- http://m.wap.gqskj.cn/snews/9042.htm
- http://m.wap.gqskj.cn/snews/353950.htm
- http://m.wap.gqskj.cn/snews/40524.htm
- http://m.wap.gqskj.cn/snews/97925.htm
- http://m.wap.gqskj.cn/snews/62731.htm
- http://m.wap.gqskj.cn/snews/0431.htm
- http://m.wap.gqskj.cn/snews/06162.htm
- http://m.wap.gqskj.cn/snews/69364.htm
- http://m.wap.gqskj.cn/snews/02838.htm
- http://m.wap.gqskj.cn/snews/68662.htm
- http://m.wap.gqskj.cn/snews/4343.htm
- http://m.wap.gqskj.cn/snews/70530.htm
- http://m.wap.gqskj.cn/snews/16363.htm
- http://m.wap.gqskj.cn/snews/275941.htm
- http://m.wap.gqskj.cn/snews/594662.htm
- http://m.wap.gqskj.cn/snews/7868823.htm
- http://m.wap.gqskj.cn/snews/3783.htm
- http://m.wap.gqskj.cn/snews/44028.htm
- http://m.wap.gqskj.cn/snews/33477.htm
- http://m.wap.gqskj.cn/snews/757730.htm
- http://m.wap.gqskj.cn/snews/28401.htm
- http://m.wap.gqskj.cn/snews/0703721.htm
- http://m.wap.gqskj.cn/snews/0032.htm
- http://m.wap.gqskj.cn/snews/641053.htm
- http://m.wap.gqskj.cn/snews/63740.htm
- http://m.wap.gqskj.cn/snews/189874.htm
- http://m.wap.gqskj.cn/snews/523769.htm
- http://m.wap.gqskj.cn/snews/897060.htm
- http://m.wap.gqskj.cn/snews/8920.htm
- http://m.wap.gqskj.cn/snews/2238.htm
- http://m.wap.gqskj.cn/snews/56591.htm
- http://m.wap.gqskj.cn/snews/26524.htm
- http://m.wap.gqskj.cn/snews/0267.htm
- http://m.wap.gqskj.cn/snews/953967.htm
- http://m.wap.gqskj.cn/snews/17318.htm
- http://m.wap.gqskj.cn/snews/639255.htm
- http://m.wap.gqskj.cn/snews/68504.htm
- http://m.wap.gqskj.cn/snews/9685235.htm
- http://m.wap.gqskj.cn/snews/5781246.htm
- http://m.wap.gqskj.cn/snews/091048.htm
- http://m.wap.gqskj.cn/snews/0423.htm
- http://m.wap.gqskj.cn/snews/10587.htm
- http://m.wap.gqskj.cn/snews/69615.htm
- http://m.wap.gqskj.cn/snews/1009983.htm
- http://m.wap.gqskj.cn/snews/5920.htm
- http://m.wap.gqskj.cn/snews/1481359.htm
- http://m.wap.gqskj.cn/snews/876720.htm
- http://m.wap.gqskj.cn/snews/64866.htm
- http://m.wap.gqskj.cn/snews/7211640.htm
- http://m.wap.gqskj.cn/snews/6167.htm
- http://m.wap.gqskj.cn/snews/4921054.htm
- http://m.wap.gqskj.cn/snews/1330446.htm
- http://m.wap.gqskj.cn/snews/6002.htm
- http://m.wap.gqskj.cn/snews/7606.htm
- http://m.wap.gqskj.cn/snews/93710.htm
- http://m.wap.gqskj.cn/snews/1162.htm
- http://m.wap.gqskj.cn/snews/498178.htm
- http://m.wap.gqskj.cn/snews/350044.htm
- http://m.wap.gqskj.cn/snews/709195.htm
- http://m.wap.gqskj.cn/snews/6697250.htm
- http://m.wap.gqskj.cn/snews/5465.htm
- http://m.wap.gqskj.cn/snews/2365.htm
- http://m.wap.gqskj.cn/snews/62367.htm
- http://m.wap.gqskj.cn/snews/32606.htm
- http://m.wap.gqskj.cn/snews/1466.htm
- http://m.wap.gqskj.cn/snews/3775563.htm
- http://m.wap.gqskj.cn/snews/079368.htm
- http://m.wap.gqskj.cn/snews/369178.htm
- http://m.wap.gqskj.cn/snews/435732.htm
- http://m.wap.gqskj.cn/snews/0850.htm
- http://m.wap.gqskj.cn/snews/4357.htm
- http://m.wap.gqskj.cn/snews/846880.htm
- http://m.wap.gqskj.cn/snews/70104.htm
- http://m.wap.gqskj.cn/snews/0316.htm
- http://m.wap.gqskj.cn/snews/2703819.htm
- http://m.wap.gqskj.cn/snews/90231.htm
- http://m.wap.gqskj.cn/snews/335038.htm
- http://m.wap.gqskj.cn/snews/2482.htm
- http://m.wap.gqskj.cn/snews/307681.htm
- http://m.wap.gqskj.cn/snews/33099.htm
- http://m.wap.gqskj.cn/snews/1640316.htm
- http://m.wap.gqskj.cn/snews/4599860.htm
- http://m.wap.gqskj.cn/snews/03578.htm
- http://m.wap.gqskj.cn/snews/6439316.htm
- http://m.wap.gqskj.cn/snews/92377.htm
- http://m.wap.gqskj.cn/snews/5120452.htm
- http://m.wap.gqskj.cn/snews/170991.htm
- http://m.wap.gqskj.cn/snews/88708.htm
- http://m.wap.gqskj.cn/snews/9499950.htm
- http://m.wap.gqskj.cn/snews/2001.htm
- http://m.wap.gqskj.cn/snews/3184768.htm
- http://m.wap.gqskj.cn/snews/081230.htm
- http://m.wap.gqskj.cn/snews/100305.htm
- http://m.wap.gqskj.cn/snews/701190.htm
- http://m.wap.gqskj.cn/snews/7982.htm
- http://m.wap.gqskj.cn/snews/27783.htm
- http://m.wap.gqskj.cn/snews/87581.htm
- http://m.wap.gqskj.cn/snews/0146397.htm
- http://m.wap.gqskj.cn/snews/8568630.htm
- http://m.wap.gqskj.cn/snews/6447.htm
- http://m.wap.gqskj.cn/snews/3914.htm
- http://m.wap.gqskj.cn/snews/222407.htm
- http://m.wap.gqskj.cn/snews/25927.htm
- http://m.wap.gqskj.cn/snews/94536.htm
- http://m.wap.gqskj.cn/snews/619555.htm
- http://m.wap.gqskj.cn/snews/0038986.htm
- http://m.wap.gqskj.cn/snews/0664.htm
- http://m.wap.gqskj.cn/snews/7180188.htm
- http://m.wap.gqskj.cn/snews/652214.htm
- http://m.wap.gqskj.cn/snews/82868.htm
- http://m.wap.gqskj.cn/snews/1881089.htm
- http://m.wap.gqskj.cn/snews/3232.htm
- http://m.wap.gqskj.cn/snews/1751.htm
- http://m.wap.gqskj.cn/snews/124347.htm
- http://m.wap.gqskj.cn/snews/196577.htm
- http://m.wap.gqskj.cn/snews/5599860.htm
- http://m.wap.gqskj.cn/snews/27692.htm
- http://m.wap.gqskj.cn/snews/722117.htm
- http://m.wap.gqskj.cn/snews/0560975.htm
- http://m.wap.gqskj.cn/snews/79502.htm
- http://m.wap.gqskj.cn/snews/975017.htm
- http://m.wap.gqskj.cn/snews/80692.htm
- http://m.wap.gqskj.cn/snews/123014.htm
- http://m.wap.gqskj.cn/snews/3226895.htm
- http://m.wap.gqskj.cn/snews/4893.htm
- http://m.wap.gqskj.cn/snews/7039.htm
- http://m.wap.gqskj.cn/snews/79838.htm
- http://m.wap.gqskj.cn/snews/76867.htm
- http://m.wap.gqskj.cn/snews/517069.htm
- http://m.wap.gqskj.cn/snews/6963989.htm
- http://m.wap.gqskj.cn/snews/2253358.htm
- http://m.wap.gqskj.cn/snews/77190.htm
- http://m.wap.gqskj.cn/snews/83354.htm
- http://m.wap.gqskj.cn/snews/6374.htm
- http://m.wap.gqskj.cn/snews/26420.htm
- http://m.wap.gqskj.cn/snews/563363.htm
- http://m.wap.gqskj.cn/snews/02314.htm
- http://m.wap.gqskj.cn/snews/7354527.htm
- http://m.wap.gqskj.cn/snews/9749548.htm
- http://m.wap.gqskj.cn/snews/2781.htm
- http://m.wap.gqskj.cn/snews/008746.htm
- http://m.wap.gqskj.cn/snews/99302.htm

## 项目结构

```
linkindex-core/
├── bin/                                 # 命令行入口与可执行脚本
│   └── linkindex.js                     # CLI 主入口，解析命令参数并调度构建流程
├── src/                                 # 核心源码目录
│   ├── core/                            # 核心流水线模块
│   │   ├── parser.js                    # Markdown frontmatter 与正文解析器
│   │   ├── collector.js                 # 递归收集 content/links 下所有源文件
│   │   ├── builder.js                   # 页面生成器，协调渲染与输出
│   │   └── cache.js                     # 增量构建缓存读写与管理
│   ├── health/                          # 链接健康检查模块
│   │   ├── checker.js                   # 并发 HTTP 状态码请求与超时控制
│   │   └── reporter.js                  # 生成失效链接报告（JSON/CSV/Markdown）
│   ├── render/                          # 模板渲染引擎
│   │   ├── engine.js                    # 基于 EJS 的模板引擎封装
│   │   ├── filters.js                   # 自定义过滤器（日期格式化、截断等）
│   │   └── helpers.js                   # 视图辅助函数（分页、分类树构建）
│   └── server/                          # 开发与预览服务器
│       ├── dev.js                       # 热重载开发服务器配置
│       └── static.js                    # 静态资源（CSS/JS）托管路由
├── templates/                           # 页面模板目录
│   ├── layouts/                         # 基础布局模板
│   │   ├── default.ejs                  # 默认页面骨架
│   │   └── minimal.ejs                  # 无侧栏简约布局
│   ├── partials/                        # 可复用组件
│   │   ├── header.ejs                   # 站点导航栏
│   │   ├── footer.ejs                   # 页脚与许可证信息
│   │   ├── card.ejs                     # 卡片视图单元
│   │   └── list-item.ejs                # 列表视图单元
│   └── pages/                           # 页面级模板
│       ├── index.ejs                    # 首页资源列表
│       ├── category.ejs                 # 分类筛选页
│       ├── tag.ejs                      # 标签筛选页
│       └── detail.ejs                   # 单条资源详情页
├── content/                             # 用户内容源文件目录
│   ├── links/                           # 资源条目存放位置，每个 .md 文件对应一条资源
│   │   ├── 2026/                        # 按年份归档的子目录（可选）
│   │   └── pending/                     # 待审核条目暂存区
│   └── meta/                            # 站点元数据配置
│       ├── categories.yaml              # 分类定义（名称、描述、父级关系）
│       ├── tags.yaml                    # 标签定义（名称、颜色标识）
│       └── site.yaml                    # 站点名称、描述、导航菜单等全局配置
├── public/                              # 构建输出的静态站点根目录（生成内容不纳入版本控制）
│   ├── assets/                          # 编译后的 CSS、JavaScript、图片资源
│   └── index.html                       # 生成的首页入口文件
├── config/                              # 构建工具与运行环境配置
│   ├── build.js                         # 生产构建配置（输出路径、压缩选项）
│   └── dev.js                           # 开发环境配置（端口、热更新参数）
├── scripts/                             # 辅助脚本
│   ├── import-csv.js                    # 从 CSV 批量导入链接条目
│   └── validate-urls.js                 # 校验 content/links 下所有条目的 URL 格式
├── test/                                # 单元测试与集成测试
│   ├── parser.test.js                   # 解析器测试用例
│   └── collector.test.js                # 收集器测试用例
├── .eslintrc.js                         # ESLint 代码规范配置
├── .gitignore                           # 版本控制忽略文件列表
├── package.json                         # npm 项目清单与依赖声明
├── README.md                            # 项目说明文档（即本文档）
└── LICENSE                              # MIT 许可证全文
```

## 贡献指南

1. 在 GitHub 或自建 Git 平台上复刻项目仓库，将复刻版本克隆至本地开发环境。建议在独立功能分支上进行修改，分支命名遵循 `feature/描述` 或 `fix/描述` 的格式。

2. 安装项目依赖后，运行 `npm run test` 确保现有测试用例全部通过。新增功能或修复缺陷时，需在 `test/` 目录下补充对应的单元测试或集成测试用例。

3. 对于资源列表的增删改操作，统一通过 `content/links/` 目录下的 Markdown 文件实现，每个文件头部必须包含 `title`、`url`、`category` 和 `tags` 字段。修改完成后执行 `npm run validate` 校验数据格式合法性。

4. 提交代码前运行 `npm run lint` 和 `npm run format` 统一代码风格，提交信息采用约定式提交格式，类型包括 `feat`、`fix`、`docs`、`chore` 等，正文说明修改原因与影响范围。

5. 向主仓库发起 Pull Request，描述中需包含修改的动机、测试结果以及相关文档更新情况。核心维护者将在 48 小时内进行评审，通过后合并至主分支并触发自动化构建与部署。

## 常见问题

问：构建过程中出现 "ENOENT: no such file or directory" 错误，如何处理？

答：该错误通常源于 `content/meta/site.yaml` 或 `content/links` 目录缺失。请检查项目根目录下是否存在 `content` 文件夹及其子结构。若使用 `npm run init` 命令可自动生成初始目录骨架。若手动创建，请确保 `links` 目录下至少包含一个有效的 `.md` 资源文件，否则构建流水线将因无输入而中止。

问：链接健康检查报告显示大量超时，但浏览器中这些网站可正常访问，原因是什么？

答：LinkIndex Core 默认健康检查的超时阈值为 3 秒，并发请求数为 10。部分网站响应较慢或启用了防火墙限流策略，会导致检测器判定为不可达。开发者可在 `config/health.js` 中调整 `timeout` 和 `concurrency` 参数，适当增大超时值并降低并发数。若网站强制要求特定的 User-Agent 头部，也可在同一配置文件中添加自定义请求头。

问：如何将现有的 HTML 链接列表批量导入 LinkIndex Core？

答：项目根目录下的 `scripts/import-csv.js` 脚本支持从 CSV 文件导入。CSV 文件首行必须包含列名：`title`、`url`、`category`、`tags`、`description`。运行 `node scripts/import-csv.js ./path/to/links.csv` 后，脚本会为每一行生成对应的 Markdown 文件并保存至 `content/links/imported/` 目录。若需自定义字段映射，可修改脚本中的 `columnMapping` 对象。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:30:56
