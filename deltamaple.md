# WebIndex Gateway

WebIndex Gateway 是一个面向技术研究人员与信息分析人员的轻量级外链导航与结构化资源聚合工具。该项目定位于将零散分布的行业资讯、技术笔记与参考文档按批次进行集中收录，并提供统一的访问入口，解决信息碎片化导致的检索效率低下与参考源流失问题。项目本身不存储任何实体内容，仅提供链接索引与基础分类框架，适用于个人知识库补充、团队技术周报素材采集以及自动化信息归集流水线。

## 功能概览

批量外链导入与结构化存储：支持以批次为单位导入大量URL，自动识别来源域名并生成索引记录，便于后续按批次或按来源进行筛选与回溯。

原始链接直出模式：所有收录链接在展示层均保持用户提交时的原始形态，不进行协议补全、域名规范化或地址重写，确保资源引用的真实性与可追溯性。

轻量级分类标签系统：允许用户为每条外链记录附加自定义标签，实现按技术领域、内容类型或紧急程度进行多维度分类管理。

访问状态监测：内置基础HTTP状态码检测模块，可定期检查已收录链接的可达性，并在管理界面中标注异常状态，辅助用户清理失效资源。

全量批次导出：支持将任意批次下的所有链接以纯文本或结构化格式导出，便于集成至其他文档系统或自动化脚本中。

暗色主题与响应式界面：管理面板提供暗色与亮色两种显示模式，并针对移动设备进行适配，满足不同使用环境下的操作需求。

## 应用场景

技术团队周报素材汇总：团队技术负责人每周需收集组内成员推荐的行业文章与技术博客，使用WebIndex Gateway可将推荐链接按周次批次导入，生成统一的周报参考附录，减少邮件与即时通讯中的链接散落。

个人知识库外链归档：独立开发者或研究员在阅读技术文档时积累大量分散的书签，通过本项目的批次导入功能，可将这些外链按主题或时间进行结构化存档，并与本地笔记系统协同使用。

自动化信息归集流水线：结合定时脚本或CI任务，可将RSS订阅源或邮件简报中的新链接自动导入指定批次，形成持续更新的外部信息池，供后续人工筛选与分析。

失效链接批量清理：站点维护人员可利用内置的访问状态监测功能，定期扫描存量外链，快速定位返回4xx或5xx状态的资源，并集中进行替换或移除操作。

## 快速开始

以下步骤指导您在本地环境中完成项目的克隆、安装与初次运行。

```bash
# 克隆项目仓库
git clone https://github.com/webindex-gateway/webindex-gateway.git

# 进入项目目录
cd webindex-gateway

# 安装项目依赖（使用 npm）
npm install

# 以开发模式启动本地服务
npm run dev
```

执行上述命令后，本地服务默认监听在 3000 端口。访问 http://localhost:3000 即可进入管理面板，开始创建批次并导入链接。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Node.js | 18.x 或更高 | 项目运行时环境，推荐使用最新的 LTS 版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 系统自带或通过 npm 安装 | 默认本地数据库引擎，无需额外配置 |
| Git | 2.x 或更高 | 用于克隆仓库及版本控制 |
| 现代浏览器 | 最近两个版本 | 管理界面需要支持 ES6+ 与 CSS Grid 的浏览器 |
| 网络连接 | 稳定 | 用于安装依赖包及访问收录的外链资源 |
| 磁盘空间 | 至少 200 MB | 用于存放项目代码、依赖包及本地数据库文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何创建批次、导入链接、使用标签分类以及导出数据 |
| 运维指南 | /docs/operations.md | 如何配置访问状态监测的定时任务、备份本地数据库及迁移服务 |
| 开发者文档 | /docs/development.md | 项目目录结构说明、核心模块职责、API 接口规范及本地调试流程 |
| 常见问题 | /docs/faq.md | 收录链接显示异常、状态码检测失败、导入速度慢等问题的排查方法 |
| 版本记录 | /docs/changelog.md | 每个版本的新增功能、修复内容及已知限制 |

## 资源列表

- http://m.blog.gqskj.cn/nnews/81397.htm
- http://m.blog.gqskj.cn/nnews/25334.htm
- http://m.blog.gqskj.cn/nnews/021095.htm
- http://m.blog.gqskj.cn/nnews/549152.htm
- http://m.blog.gqskj.cn/nnews/34585.htm
- http://m.blog.gqskj.cn/nnews/996402.htm
- http://m.blog.gqskj.cn/nnews/4875882.htm
- http://m.blog.gqskj.cn/nnews/456697.htm
- http://m.blog.gqskj.cn/nnews/07659.htm
- http://m.blog.gqskj.cn/nnews/0577.htm
- http://m.blog.gqskj.cn/nnews/35131.htm
- http://m.blog.gqskj.cn/nnews/8326.htm
- http://m.blog.gqskj.cn/nnews/9367577.htm
- http://m.blog.gqskj.cn/nnews/7138.htm
- http://m.blog.gqskj.cn/nnews/662993.htm
- http://m.blog.gqskj.cn/nnews/1681.htm
- http://m.blog.gqskj.cn/nnews/4781.htm
- http://m.blog.gqskj.cn/nnews/0106118.htm
- http://m.blog.gqskj.cn/nnews/9114.htm
- http://m.blog.gqskj.cn/nnews/300871.htm
- http://m.blog.gqskj.cn/nnews/963525.htm
- http://m.blog.gqskj.cn/nnews/7305.htm
- http://m.blog.gqskj.cn/nnews/070836.htm
- http://m.blog.gqskj.cn/nnews/9897087.htm
- http://m.blog.gqskj.cn/nnews/27943.htm
- http://m.blog.gqskj.cn/nnews/1699.htm
- http://m.blog.gqskj.cn/nnews/318591.htm
- http://m.blog.gqskj.cn/nnews/981543.htm
- http://m.blog.gqskj.cn/nnews/3482446.htm
- http://m.blog.gqskj.cn/nnews/56060.htm
- http://m.blog.gqskj.cn/nnews/979919.htm
- http://m.blog.gqskj.cn/nnews/1191.htm
- http://m.blog.gqskj.cn/nnews/250328.htm
- http://m.blog.gqskj.cn/nnews/810038.htm
- http://m.blog.gqskj.cn/nnews/742971.htm
- http://m.blog.gqskj.cn/nnews/17380.htm
- http://m.blog.gqskj.cn/nnews/68402.htm
- http://m.blog.gqskj.cn/nnews/496859.htm
- http://m.blog.gqskj.cn/nnews/471822.htm
- http://m.blog.gqskj.cn/nnews/1977.htm
- http://m.blog.gqskj.cn/nnews/90120.htm
- http://m.blog.gqskj.cn/nnews/5252.htm
- http://m.blog.gqskj.cn/nnews/256822.htm
- http://m.blog.gqskj.cn/nnews/572624.htm
- http://m.blog.gqskj.cn/nnews/8867.htm
- http://m.blog.gqskj.cn/nnews/535421.htm
- http://m.blog.gqskj.cn/nnews/476111.htm
- http://m.blog.gqskj.cn/nnews/3298.htm
- http://m.blog.gqskj.cn/nnews/1064.htm
- http://m.blog.gqskj.cn/nnews/4812703.htm
- http://m.blog.gqskj.cn/nnews/1776969.htm
- http://m.blog.gqskj.cn/nnews/8823212.htm
- http://m.blog.gqskj.cn/nnews/0167787.htm
- http://m.blog.gqskj.cn/nnews/526319.htm
- http://m.blog.gqskj.cn/nnews/1092.htm
- http://m.blog.gqskj.cn/nnews/411784.htm
- http://m.blog.gqskj.cn/nnews/7839.htm
- http://m.blog.gqskj.cn/nnews/60207.htm
- http://m.blog.gqskj.cn/nnews/13946.htm
- http://m.blog.gqskj.cn/nnews/95349.htm
- http://m.blog.gqskj.cn/nnews/7676.htm
- http://m.blog.gqskj.cn/nnews/1877.htm
- http://m.blog.gqskj.cn/nnews/741404.htm
- http://m.blog.gqskj.cn/nnews/0225307.htm
- http://m.blog.gqskj.cn/nnews/6000.htm
- http://m.blog.gqskj.cn/nnews/613949.htm
- http://m.blog.gqskj.cn/nnews/17725.htm
- http://m.blog.gqskj.cn/nnews/37914.htm
- http://m.blog.gqskj.cn/nnews/66132.htm
- http://m.blog.gqskj.cn/nnews/43284.htm
- http://m.blog.gqskj.cn/nnews/0555.htm
- http://m.blog.gqskj.cn/nnews/830776.htm
- http://m.blog.gqskj.cn/nnews/561972.htm
- http://m.blog.gqskj.cn/nnews/52758.htm
- http://m.blog.gqskj.cn/nnews/298973.htm
- http://m.blog.gqskj.cn/nnews/09982.htm
- http://m.blog.gqskj.cn/nnews/3089654.htm
- http://m.blog.gqskj.cn/nnews/3304.htm
- http://m.blog.gqskj.cn/nnews/1539.htm
- http://m.blog.gqskj.cn/nnews/0717057.htm
- http://m.blog.gqskj.cn/nnews/264228.htm
- http://m.blog.gqskj.cn/nnews/4529.htm
- http://m.blog.gqskj.cn/nnews/1385.htm
- http://m.blog.gqskj.cn/nnews/3012.htm
- http://m.blog.gqskj.cn/nnews/26704.htm
- http://m.blog.gqskj.cn/nnews/052147.htm
- http://m.blog.gqskj.cn/nnews/01462.htm
- http://m.blog.gqskj.cn/nnews/5280380.htm
- http://m.blog.gqskj.cn/nnews/568272.htm
- http://m.blog.gqskj.cn/nnews/0954577.htm
- http://m.blog.gqskj.cn/nnews/2340.htm
- http://m.blog.gqskj.cn/nnews/9860.htm
- http://m.blog.gqskj.cn/nnews/9615.htm
- http://m.blog.gqskj.cn/nnews/1456.htm
- http://m.blog.gqskj.cn/nnews/2209.htm
- http://m.blog.gqskj.cn/nnews/896208.htm
- http://m.blog.gqskj.cn/nnews/7285502.htm
- http://m.blog.gqskj.cn/nnews/01319.htm
- http://m.blog.gqskj.cn/nnews/92977.htm
- http://m.blog.gqskj.cn/nnews/0337.htm
- http://m.blog.gqskj.cn/nnews/8959.htm
- http://m.blog.gqskj.cn/nnews/2784.htm
- http://m.blog.gqskj.cn/nnews/6187460.htm
- http://m.blog.gqskj.cn/nnews/0186612.htm
- http://m.blog.gqskj.cn/nnews/3542755.htm
- http://m.blog.gqskj.cn/nnews/5977238.htm
- http://m.blog.gqskj.cn/nnews/11716.htm
- http://m.blog.gqskj.cn/nnews/72398.htm
- http://m.blog.gqskj.cn/nnews/459235.htm
- http://m.blog.gqskj.cn/nnews/001399.htm
- http://m.blog.gqskj.cn/nnews/8370361.htm
- http://m.blog.gqskj.cn/nnews/5241746.htm
- http://m.blog.gqskj.cn/nnews/997582.htm
- http://m.blog.gqskj.cn/nnews/9963947.htm
- http://m.blog.gqskj.cn/nnews/7560.htm
- http://m.blog.gqskj.cn/nnews/65720.htm
- http://m.blog.gqskj.cn/nnews/73084.htm
- http://m.blog.gqskj.cn/nnews/5028625.htm
- http://m.blog.gqskj.cn/nnews/165236.htm
- http://m.blog.gqskj.cn/nnews/7020.htm
- http://m.blog.gqskj.cn/nnews/0511.htm
- http://m.blog.gqskj.cn/nnews/5711655.htm
- http://m.blog.gqskj.cn/nnews/24517.htm
- http://m.blog.gqskj.cn/nnews/75634.htm
- http://m.blog.gqskj.cn/nnews/07399.htm
- http://m.blog.gqskj.cn/nnews/01124.htm
- http://m.blog.gqskj.cn/nnews/2089072.htm
- http://m.blog.gqskj.cn/nnews/34427.htm
- http://m.blog.gqskj.cn/nnews/4537.htm
- http://m.blog.gqskj.cn/nnews/49447.htm
- http://m.blog.gqskj.cn/nnews/342573.htm
- http://m.blog.gqskj.cn/nnews/5130207.htm
- http://m.blog.gqskj.cn/nnews/317567.htm
- http://m.blog.gqskj.cn/nnews/8726593.htm
- http://m.blog.gqskj.cn/nnews/8989.htm
- http://m.blog.gqskj.cn/nnews/82797.htm
- http://m.blog.gqskj.cn/nnews/51671.htm
- http://m.blog.gqskj.cn/nnews/138031.htm
- http://m.blog.gqskj.cn/nnews/437057.htm
- http://m.blog.gqskj.cn/nnews/113224.htm
- http://m.blog.gqskj.cn/nnews/062219.htm
- http://m.blog.gqskj.cn/nnews/05932.htm
- http://m.blog.gqskj.cn/nnews/45491.htm
- http://m.blog.gqskj.cn/nnews/316177.htm
- http://m.blog.gqskj.cn/nnews/551640.htm
- http://m.blog.gqskj.cn/nnews/5508.htm
- http://m.blog.gqskj.cn/nnews/3087.htm
- http://m.blog.gqskj.cn/nnews/4131.htm
- http://m.blog.gqskj.cn/nnews/821469.htm
- http://m.blog.gqskj.cn/nnews/198293.htm
- http://m.blog.gqskj.cn/nnews/484905.htm
- http://m.blog.gqskj.cn/nnews/348685.htm
- http://m.blog.gqskj.cn/nnews/935123.htm
- http://m.blog.gqskj.cn/nnews/5123.htm
- http://m.blog.gqskj.cn/nnews/6230.htm
- http://m.blog.gqskj.cn/nnews/38339.htm
- http://m.blog.gqskj.cn/nnews/9346.htm
- http://m.blog.gqskj.cn/nnews/5729.htm
- http://m.blog.gqskj.cn/nnews/097441.htm
- http://m.blog.gqskj.cn/nnews/86089.htm
- http://m.blog.gqskj.cn/nnews/4166755.htm
- http://m.blog.gqskj.cn/nnews/801672.htm
- http://m.blog.gqskj.cn/nnews/694400.htm
- http://m.blog.gqskj.cn/nnews/789072.htm
- http://m.blog.gqskj.cn/nnews/5177.htm
- http://m.blog.gqskj.cn/nnews/0859.htm
- http://m.blog.gqskj.cn/nnews/3489669.htm
- http://m.blog.gqskj.cn/nnews/21267.htm
- http://m.blog.gqskj.cn/nnews/4799.htm
- http://m.blog.gqskj.cn/nnews/4815213.htm
- http://m.blog.gqskj.cn/nnews/2398.htm
- http://m.blog.gqskj.cn/nnews/53335.htm
- http://m.blog.gqskj.cn/nnews/5557.htm
- http://m.blog.gqskj.cn/nnews/2642.htm
- http://m.blog.gqskj.cn/nnews/377215.htm
- http://m.blog.gqskj.cn/nnews/0130402.htm
- http://m.blog.gqskj.cn/nnews/3060.htm
- http://m.blog.gqskj.cn/nnews/3777.htm
- http://m.blog.gqskj.cn/nnews/963832.htm
- http://m.blog.gqskj.cn/nnews/6645.htm
- http://m.blog.gqskj.cn/nnews/40472.htm
- http://m.blog.gqskj.cn/nnews/4363.htm
- http://m.blog.gqskj.cn/nnews/8961099.htm
- http://m.blog.gqskj.cn/nnews/3641.htm
- http://m.blog.gqskj.cn/nnews/480630.htm
- http://m.blog.gqskj.cn/nnews/41518.htm
- http://m.blog.gqskj.cn/nnews/17594.htm
- http://m.blog.gqskj.cn/nnews/72379.htm
- http://m.blog.gqskj.cn/nnews/2287.htm
- http://m.blog.gqskj.cn/nnews/30942.htm
- http://m.blog.gqskj.cn/nnews/8930135.htm
- http://m.blog.gqskj.cn/nnews/051698.htm
- http://m.blog.gqskj.cn/nnews/9093.htm
- http://m.blog.gqskj.cn/nnews/599157.htm
- http://m.blog.gqskj.cn/nnews/13050.htm
- http://m.blog.gqskj.cn/nnews/423544.htm
- http://m.blog.gqskj.cn/nnews/070121.htm
- http://m.blog.gqskj.cn/nnews/9985187.htm
- http://m.blog.gqskj.cn/nnews/11117.htm
- http://m.blog.gqskj.cn/nnews/29848.htm
- http://m.blog.gqskj.cn/nnews/7168078.htm
- http://m.blog.gqskj.cn/nnews/8757.htm
- http://m.blog.gqskj.cn/nnews/18719.htm
- http://m.blog.gqskj.cn/nnews/2377.htm
- http://m.blog.gqskj.cn/nnews/5218472.htm
- http://m.blog.gqskj.cn/nnews/9307509.htm
- http://m.blog.gqskj.cn/nnews/2352368.htm
- http://m.blog.gqskj.cn/nnews/525735.htm
- http://m.blog.gqskj.cn/nnews/2321021.htm
- http://m.blog.gqskj.cn/nnews/4906295.htm
- http://m.blog.gqskj.cn/nnews/8889822.htm
- http://m.blog.gqskj.cn/nnews/217770.htm
- http://m.blog.gqskj.cn/nnews/92158.htm
- http://m.blog.gqskj.cn/nnews/405477.htm
- http://m.blog.gqskj.cn/nnews/882011.htm
- http://m.blog.gqskj.cn/nnews/0164384.htm
- http://m.blog.gqskj.cn/nnews/174023.htm
- http://m.blog.gqskj.cn/nnews/1912293.htm
- http://m.blog.gqskj.cn/nnews/533920.htm
- http://m.blog.gqskj.cn/nnews/785057.htm
- http://m.blog.gqskj.cn/nnews/2402.htm
- http://m.blog.gqskj.cn/nnews/4261.htm
- http://m.blog.gqskj.cn/nnews/4622.htm
- http://m.blog.gqskj.cn/nnews/3743862.htm
- http://m.blog.gqskj.cn/nnews/97681.htm
- http://m.blog.gqskj.cn/nnews/9222.htm
- http://m.blog.gqskj.cn/nnews/6374.htm
- http://m.blog.gqskj.cn/nnews/6552.htm
- http://m.blog.gqskj.cn/nnews/25905.htm
- http://m.blog.gqskj.cn/nnews/34842.htm
- http://m.blog.gqskj.cn/nnews/651364.htm
- http://m.blog.gqskj.cn/nnews/385190.htm
- http://m.blog.gqskj.cn/nnews/57588.htm
- http://m.blog.gqskj.cn/nnews/319928.htm
- http://m.blog.gqskj.cn/nnews/3976248.htm
- http://m.blog.gqskj.cn/nnews/1674.htm
- http://m.blog.gqskj.cn/nnews/62556.htm
- http://m.blog.gqskj.cn/nnews/41872.htm
- http://m.blog.gqskj.cn/nnews/1310.htm
- http://m.blog.gqskj.cn/nnews/1192.htm
- http://m.blog.gqskj.cn/nnews/6190266.htm
- http://m.blog.gqskj.cn/nnews/3265659.htm
- http://m.blog.gqskj.cn/nnews/5102.htm
- http://m.blog.gqskj.cn/nnews/8325.htm
- http://m.blog.gqskj.cn/nnews/001016.htm
- http://m.blog.gqskj.cn/nnews/6848298.htm
- http://m.blog.gqskj.cn/nnews/46385.htm
- http://m.blog.gqskj.cn/nnews/0626503.htm
- http://m.blog.gqskj.cn/nnews/20687.htm
- http://m.blog.gqskj.cn/nnews/3175577.htm

## 项目结构

```
webindex-gateway/
├── backend/                        # 后端服务模块
│   ├── api/                        # RESTful API 路由定义
│   │   ├── batches.js              # 批次创建、查询与删除接口
│   │   ├── links.js                # 链接导入、编辑与状态监测接口
│   │   └── tags.js                 # 标签增删改查接口
│   ├── core/                       # 核心业务逻辑
│   │   ├── importer.js             # 批量链接解析与入库处理器
│   │   ├── checker.js              # HTTP 状态码异步检测调度器
│   │   └── exporter.js             # 全量批次导出格式化器
│   ├── models/                     # 数据模型层
│   │   ├── batch.js                # 批次数据模型定义
│   │   ├── link.js                 # 链接记录数据模型定义
│   │   └── tag.js                  # 标签数据模型定义
│   └── utils/                      # 辅助工具集
│       ├── database.js             # SQLite3 连接与初始化脚本
│       └── validator.js            # URL 格式校验与重复检测
├── frontend/                       # 前端管理界面模块
│   ├── pages/                      # 页面级组件
│   │   ├── Dashboard.jsx           # 总览面板，展示批次统计与近期活动
│   │   ├── BatchView.jsx           # 批次详情页，展示批次内全部链接
│   │   └── Settings.jsx            # 用户偏好设置与主题切换
│   ├── components/                 # 可复用 UI 组件
│   │   ├── LinkTable.jsx           # 链接列表表格，支持排序与筛选
│   │   ├── ImportModal.jsx         # 批量导入弹窗，支持文本粘贴与文件上传
│   │   └── StatusBadge.jsx         # 链接状态标签组件
│   └── styles/                     # 样式与主题配置
│       ├── global.css              # 全局基础样式
│       └── theme.js                # 亮色/暗色主题变量定义
├── docs/                           # 项目文档目录
│   ├── user-guide.md               # 用户操作手册
│   ├── operations.md               # 运维部署指南
│   ├── development.md              # 开发者贡献指南
│   └── faq.md                      # 常见问题集
├── scripts/                        # 辅助脚本
│   ├── seed.js                     # 本地开发环境初始数据填充
│   └── health-check.js             # 手动触发链接状态全量检测
├── tests/                          # 单元测试与集成测试目录
│   ├── unit/                       # 核心函数单元测试
│   └── integration/                # API 接口集成测试
├── .env.example                    # 环境变量配置模板
├── package.json                    # 项目依赖清单与脚本定义
├── README.md                       # 项目说明文档（即本文档）
└── LICENSE                         # MIT 许可证文件
```

## 贡献指南

提交问题报告：在 GitHub Issues 页面中新建问题，请使用项目提供的模板，清晰描述问题现象、复现步骤、运行环境及日志截图。若为功能请求，请说明使用场景与预期行为。

代码贡献流程：Fork 本仓库至个人账号，在本地新建功能分支进行开发。提交代码前请运行现有测试套件，确保无回归问题，并为新功能补充相应的单元测试或集成测试。

提交拉取请求：完成开发后，向主仓库的 main 分支提交 Pull Request。PR 描述中请关联相关 Issue 编号，并简要说明改动内容与测试覆盖情况。项目维护者将在 3 个工作日内进行评审。

文档改进：文档目录位于 /docs 下，接受拼写修正、表述优化与内容扩充。提交文档改动时请遵循现有的格式规范，并确保中英文之间保留适当空格。

本地开发环境设置：参考 /docs/development.md 中的步骤配置本地开发环境，包括依赖安装、数据库初始化与测试数据填充。建议使用 Node.js 18 LTS 版本。

## 常见问题

Q: 导入大量链接时页面出现卡顿或超时，应如何解决？

A: 单次导入建议不超过 500 条链接。若需导入更大批次，可在 /backend/core/importer.js 中调整批量写入的阈值，或通过命令行脚本 scripts/bulk-import.js 进行异步导入。同时检查本地 SQLite3 数据库的 WAL 模式是否启用，以提升写入并发性能。

Q: 状态监测模块报告大量链接为不可达，但浏览器中可正常访问，如何处理？

A: 状态监测默认使用 Node.js 的 http/https 模块发送 HEAD 请求，部分站点可能屏蔽此类请求或响应较慢。可在 /backend/core/checker.js 中将请求方法改为 GET 并设置合适的超时时间（建议 5000ms 以上）。同时检查本地网络环境是否存在代理或防火墙限制。

Q: 如何将本地数据迁移至其他服务器或与团队成员共享？

A: 本地数据库文件位于 /data/webindex.db，直接复制该文件至目标环境的相同相对路径即可完成迁移。若需导出纯数据，可使用项目内置的 exporter 模块输出为 JSON 或 CSV 格式。跨版本迁移时请先对比数据库 schema 变更，必要时运行迁移脚本。

## 许可证

MIT

> 外链数量: 250 | 生成时间: 2026-08-25 17:31:47
