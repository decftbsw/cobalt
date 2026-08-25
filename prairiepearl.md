# WebLink Nexus

WebLink Nexus 是一个面向技术内容聚合与结构化导航的开源项目，旨在解决技术文档、教程资源、开发工具链相关信息碎片化、难以追溯与归类的问题。项目定位为轻量级、可自托管的链接枢纽站，核心目标用户为开发者、技术写作人员、开源社区维护者以及技术内容研究者。WebLink Nexus 不提供内容存储，而是通过标准化元数据描述与分类体系，将原始资源链接转化为可检索、可归档、可审计的知识索引结构。

## 功能概览

- **批量链接导入与去重**：支持从纯文本、CSV、Markdown 列表中批量导入原始 URL，自动识别协议与域名格式，执行严格去重与格式校验，保留原始链接字面值不做任何自动补全或改写。

- **多级分类标签系统**：每个链接可绑定多个自定义标签（如 #tutorial、#api、#blog、#security），支持标签层级嵌套与继承，便于按主题或技术栈快速筛选。

- **元数据提取与缓存**：对导入的链接自动发起 HEAD 请求获取响应头与内容类型信息，缓存状态码、最后修改时间、内容长度等元数据，减少重复网络开销。

- **全文检索与过滤**：基于标题、描述、标签、来源域名等字段构建倒排索引，支持布尔查询与正则表达式过滤，结果可按时间、域名、相关性排序。

- **定期健康检查**：内置定时任务，对已收录链接执行周期性可用性检测，标记失效链接并生成报告，支持通过 Webhook 推送异常通知。

- **数据导出与迁移**：支持将整个链接索引导出为 JSON、YAML 或 SQLite 文件，方便迁移至其他平台或进行离线分析。

- **只读 API 接口**：提供 RESTful 风格的只读 API，支持按标签、域名、关键词查询链接列表，便于集成到第三方工具或静态站点生成器。

- **操作审计日志**：记录所有链接的增删改查操作，包含操作人、时间戳、变更前后值，满足团队协作场景下的追溯需求。

## 应用场景

- **技术文档团队维护外部参考链接库**：文档编写过程中需要引用大量外部规范、SDK 文档、博客文章。WebLink Nexus 可作为内部参考链接管理系统，统一收录并定期检查链接有效性，避免文档中出现死链。

- **开源项目 README 资源汇总**：开源项目维护者可将项目依赖的教程、示例、相关工具链接通过 WebLink Nexus 进行集中管理，再自动生成资源列表章节，减少手动维护 README 的工作量。

- **技术社区内容审核与归档**：社区运营人员可将用户投稿的外部链接导入系统，经过标签分类与元数据审核后，形成公开可查询的社区资源导航页，提升内容可发现性。

- **个人知识库外链管理**：研究员或开发者使用 WebLink Nexus 管理个人博客、笔记系统中引用的外部链接，配合健康检查功能及时发现失效资源，保持知识库的可靠性。

- **离线环境下的链接镜像规划**：在内网隔离环境中，运维人员可先在外网使用 WebLink Nexus 收集所需资源链接，导出清单后批量申请镜像或缓存，减少人工整理成本。

## 快速开始

以下命令演示了从源码克隆、安装依赖到启动开发服务的完整流程。

```bash
git clone https://github.com/weblink-nexus/weblink-nexus.git
cd weblink-nexus
npm install
npm run build
npm start
```

执行完毕后，服务默认监听 3000 端口，访问 http://127.0.0.1:3000 可打开 Web 管理界面。首次启动会自动创建 SQLite 数据库文件与默认管理员账户，初始密码在控制台日志中输出，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用官方二进制或 nvm 安装 |
| npm | 9.x 或更高 | 包管理器，随 Node.js 一同安装 |
| SQLite3 | 3.39 或更高 | 嵌入式数据库，生产环境可选 PostgreSQL 15+ 替代 |
| curl / wget | 任意稳定版 | 用于健康检查模块的外部探测工具，需在 PATH 中可用 |
| git | 2.30 或更高 | 用于克隆仓库与版本管理，仅开发时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何首次启动、配置管理员账户、导入第一批链接 |
| 配置手册 | docs/configuration.md | 环境变量、配置文件格式、数据库连接字符串、日志级别等详细参数说明 |
| API 参考 | docs/api-reference.md | 所有只读接口的路径、请求参数、响应结构、错误码定义 |
| 运维指南 | docs/operations.md | 健康检查调度配置、数据备份策略、迁移步骤、性能调优建议 |

## 资源列表

- http://m.blog.oexnr.cn/snews/5444989.htm
- http://m.blog.oexnr.cn/snews/473577.htm
- http://m.blog.oexnr.cn/snews/5231.htm
- http://m.blog.oexnr.cn/snews/4364.htm
- http://m.blog.oexnr.cn/snews/35841.htm
- http://m.blog.oexnr.cn/snews/3804.htm
- http://m.blog.oexnr.cn/snews/0742271.htm
- http://m.blog.oexnr.cn/snews/7498.htm
- http://m.blog.oexnr.cn/snews/058629.htm
- http://m.blog.oexnr.cn/snews/38188.htm
- http://m.blog.oexnr.cn/snews/2449.htm
- http://m.blog.oexnr.cn/snews/6275.htm
- http://m.blog.oexnr.cn/snews/462723.htm
- http://m.blog.oexnr.cn/snews/199357.htm
- http://m.blog.oexnr.cn/snews/8461192.htm
- http://m.blog.oexnr.cn/snews/5578459.htm
- http://m.blog.oexnr.cn/snews/0223694.htm
- http://m.blog.oexnr.cn/snews/8859.htm
- http://m.blog.oexnr.cn/snews/61055.htm
- http://m.blog.oexnr.cn/snews/218900.htm
- http://m.blog.oexnr.cn/snews/9533.htm
- http://m.blog.oexnr.cn/snews/0513727.htm
- http://m.blog.oexnr.cn/snews/8181969.htm
- http://m.blog.oexnr.cn/snews/2453.htm
- http://m.blog.oexnr.cn/snews/60621.htm
- http://m.blog.oexnr.cn/snews/5506.htm
- http://m.blog.oexnr.cn/snews/7791464.htm
- http://m.blog.oexnr.cn/snews/5851.htm
- http://m.blog.oexnr.cn/snews/504442.htm
- http://m.blog.oexnr.cn/snews/7976.htm
- http://m.blog.oexnr.cn/snews/3694419.htm
- http://m.blog.oexnr.cn/snews/1922.htm
- http://m.blog.oexnr.cn/snews/9108.htm
- http://m.blog.oexnr.cn/snews/4123074.htm
- http://m.blog.oexnr.cn/snews/3807.htm
- http://m.blog.oexnr.cn/snews/5449.htm
- http://m.blog.oexnr.cn/snews/261835.htm
- http://m.blog.oexnr.cn/snews/78617.htm
- http://m.blog.oexnr.cn/snews/6821036.htm
- http://m.blog.oexnr.cn/snews/4781874.htm
- http://m.blog.oexnr.cn/snews/047090.htm
- http://m.blog.oexnr.cn/snews/8254528.htm
- http://m.blog.oexnr.cn/snews/620473.htm
- http://m.blog.oexnr.cn/snews/129563.htm
- http://m.blog.oexnr.cn/snews/386240.htm
- http://m.blog.oexnr.cn/snews/2085.htm
- http://m.blog.oexnr.cn/snews/3987.htm
- http://m.blog.oexnr.cn/snews/41001.htm
- http://m.blog.oexnr.cn/snews/44553.htm
- http://m.blog.oexnr.cn/snews/6096378.htm
- http://m.blog.oexnr.cn/snews/7260021.htm
- http://m.blog.oexnr.cn/snews/663954.htm
- http://m.blog.oexnr.cn/snews/603748.htm
- http://m.blog.oexnr.cn/snews/1165954.htm
- http://m.blog.oexnr.cn/snews/41489.htm
- http://m.blog.oexnr.cn/snews/8529222.htm
- http://m.blog.oexnr.cn/snews/68762.htm
- http://m.blog.oexnr.cn/snews/5891.htm
- http://m.blog.oexnr.cn/snews/3759.htm
- http://m.blog.oexnr.cn/snews/692424.htm
- http://m.blog.oexnr.cn/snews/2681.htm
- http://m.blog.oexnr.cn/snews/36590.htm
- http://m.blog.oexnr.cn/snews/4643121.htm
- http://m.blog.oexnr.cn/snews/2362161.htm
- http://m.blog.oexnr.cn/snews/34548.htm
- http://m.blog.oexnr.cn/snews/9796.htm
- http://m.blog.oexnr.cn/snews/32905.htm
- http://m.blog.oexnr.cn/snews/6795.htm
- http://m.blog.oexnr.cn/snews/410251.htm
- http://m.blog.oexnr.cn/snews/17781.htm
- http://m.blog.oexnr.cn/snews/0035891.htm
- http://m.blog.oexnr.cn/snews/221270.htm
- http://m.blog.oexnr.cn/snews/1266.htm
- http://m.blog.oexnr.cn/snews/0881.htm
- http://m.blog.oexnr.cn/snews/7828645.htm
- http://m.blog.oexnr.cn/snews/60039.htm
- http://m.blog.oexnr.cn/snews/44111.htm
- http://m.blog.oexnr.cn/snews/1368177.htm
- http://m.blog.oexnr.cn/snews/0795073.htm
- http://m.blog.oexnr.cn/snews/24263.htm
- http://m.blog.oexnr.cn/snews/3211619.htm
- http://m.blog.oexnr.cn/snews/747388.htm
- http://m.blog.oexnr.cn/snews/5187653.htm
- http://m.blog.oexnr.cn/snews/869932.htm
- http://m.blog.oexnr.cn/snews/1702.htm
- http://m.blog.oexnr.cn/snews/3411.htm
- http://m.blog.oexnr.cn/snews/6124.htm
- http://m.blog.oexnr.cn/snews/7375.htm
- http://m.blog.oexnr.cn/snews/8239693.htm
- http://m.blog.oexnr.cn/snews/1173.htm
- http://m.blog.oexnr.cn/snews/8911351.htm
- http://m.blog.oexnr.cn/snews/47722.htm
- http://m.blog.oexnr.cn/snews/38786.htm
- http://m.blog.oexnr.cn/snews/7030.htm
- http://m.blog.oexnr.cn/snews/55797.htm
- http://m.blog.oexnr.cn/snews/15452.htm
- http://m.blog.oexnr.cn/snews/05075.htm
- http://m.blog.oexnr.cn/snews/2214.htm
- http://m.blog.oexnr.cn/snews/92597.htm
- http://m.blog.oexnr.cn/snews/1074.htm
- http://m.blog.oexnr.cn/snews/19123.htm
- http://m.blog.oexnr.cn/snews/0996740.htm
- http://m.blog.oexnr.cn/snews/9287.htm
- http://m.blog.oexnr.cn/snews/2625.htm
- http://m.blog.oexnr.cn/snews/6318200.htm
- http://m.blog.oexnr.cn/snews/58735.htm
- http://m.blog.oexnr.cn/snews/4790947.htm
- http://m.blog.oexnr.cn/snews/9959314.htm
- http://m.blog.oexnr.cn/snews/608251.htm
- http://m.blog.oexnr.cn/snews/8938772.htm
- http://m.blog.oexnr.cn/snews/4037607.htm
- http://m.blog.oexnr.cn/snews/455737.htm
- http://m.blog.oexnr.cn/snews/907800.htm
- http://m.blog.oexnr.cn/snews/1230.htm
- http://m.blog.oexnr.cn/snews/238122.htm
- http://m.blog.oexnr.cn/snews/109146.htm
- http://m.blog.oexnr.cn/snews/9896094.htm
- http://m.blog.oexnr.cn/snews/0576.htm
- http://m.blog.oexnr.cn/snews/337266.htm
- http://m.blog.oexnr.cn/snews/2455414.htm
- http://m.blog.oexnr.cn/snews/9510.htm
- http://m.blog.oexnr.cn/snews/94417.htm
- http://m.blog.oexnr.cn/snews/5191.htm
- http://m.blog.oexnr.cn/snews/0417375.htm
- http://m.blog.oexnr.cn/snews/87641.htm
- http://m.blog.oexnr.cn/snews/9873.htm
- http://m.blog.oexnr.cn/snews/5356764.htm
- http://m.blog.oexnr.cn/snews/8179401.htm
- http://m.blog.oexnr.cn/snews/9822141.htm
- http://m.blog.oexnr.cn/snews/7124858.htm
- http://m.blog.oexnr.cn/snews/0997378.htm
- http://m.blog.oexnr.cn/snews/77718.htm
- http://m.blog.oexnr.cn/snews/770982.htm
- http://m.blog.oexnr.cn/snews/07867.htm
- http://m.blog.oexnr.cn/snews/7464833.htm
- http://m.blog.oexnr.cn/snews/021295.htm
- http://m.blog.oexnr.cn/snews/5292.htm
- http://m.blog.oexnr.cn/snews/52882.htm
- http://m.blog.oexnr.cn/snews/6151150.htm
- http://m.blog.oexnr.cn/snews/3046031.htm
- http://m.blog.oexnr.cn/snews/0821320.htm
- http://m.blog.oexnr.cn/snews/90885.htm
- http://m.blog.oexnr.cn/snews/7767628.htm
- http://m.blog.oexnr.cn/snews/286729.htm
- http://m.blog.oexnr.cn/snews/804096.htm
- http://m.blog.oexnr.cn/snews/27519.htm
- http://m.blog.oexnr.cn/snews/6099828.htm
- http://m.blog.oexnr.cn/snews/33339.htm
- http://m.blog.oexnr.cn/snews/710368.htm
- http://m.blog.oexnr.cn/snews/9860.htm
- http://m.blog.oexnr.cn/snews/9297757.htm
- http://m.blog.oexnr.cn/snews/965196.htm
- http://m.blog.oexnr.cn/snews/2116.htm
- http://m.blog.oexnr.cn/snews/1108.htm
- http://m.blog.oexnr.cn/snews/74430.htm
- http://m.blog.oexnr.cn/snews/95441.htm
- http://m.blog.oexnr.cn/snews/176238.htm
- http://m.blog.oexnr.cn/snews/1983.htm
- http://m.blog.oexnr.cn/snews/52662.htm
- http://m.blog.oexnr.cn/snews/5159.htm
- http://m.blog.oexnr.cn/snews/7333195.htm
- http://m.blog.oexnr.cn/snews/0717076.htm
- http://m.blog.oexnr.cn/snews/81036.htm
- http://m.blog.oexnr.cn/snews/86301.htm
- http://m.blog.oexnr.cn/snews/63048.htm
- http://m.blog.oexnr.cn/snews/9792882.htm
- http://m.blog.oexnr.cn/snews/02073.htm
- http://m.blog.oexnr.cn/snews/7092.htm
- http://m.blog.oexnr.cn/snews/067993.htm
- http://m.blog.oexnr.cn/snews/3851095.htm
- http://m.blog.oexnr.cn/snews/4411258.htm
- http://m.blog.oexnr.cn/snews/571004.htm
- http://m.blog.oexnr.cn/snews/4368658.htm
- http://m.blog.oexnr.cn/snews/011896.htm
- http://m.blog.oexnr.cn/snews/787186.htm
- http://m.blog.oexnr.cn/snews/241357.htm
- http://m.blog.oexnr.cn/snews/30518.htm
- http://m.blog.oexnr.cn/snews/65034.htm
- http://m.blog.oexnr.cn/snews/8102790.htm
- http://m.blog.oexnr.cn/snews/3426821.htm
- http://m.blog.oexnr.cn/snews/02222.htm
- http://m.blog.oexnr.cn/snews/08621.htm
- http://m.blog.oexnr.cn/snews/34789.htm
- http://m.blog.oexnr.cn/snews/498069.htm
- http://m.blog.oexnr.cn/snews/39762.htm
- http://m.blog.oexnr.cn/snews/7557.htm
- http://m.blog.oexnr.cn/snews/00986.htm
- http://m.blog.oexnr.cn/snews/69980.htm
- http://m.blog.oexnr.cn/snews/3692.htm
- http://m.blog.oexnr.cn/snews/6440473.htm
- http://m.blog.oexnr.cn/snews/491855.htm
- http://m.blog.oexnr.cn/snews/51870.htm
- http://m.blog.oexnr.cn/snews/51995.htm
- http://m.blog.oexnr.cn/snews/586196.htm
- http://m.blog.oexnr.cn/snews/7893738.htm
- http://m.blog.oexnr.cn/snews/29223.htm
- http://m.blog.oexnr.cn/snews/6529691.htm
- http://m.blog.oexnr.cn/snews/8434768.htm
- http://m.blog.oexnr.cn/snews/6368058.htm
- http://m.blog.oexnr.cn/snews/79340.htm
- http://m.blog.oexnr.cn/snews/6038330.htm
- http://m.blog.oexnr.cn/snews/0234663.htm
- http://m.blog.oexnr.cn/snews/177932.htm
- http://m.blog.oexnr.cn/snews/9848064.htm
- http://m.blog.oexnr.cn/snews/207033.htm
- http://m.blog.oexnr.cn/snews/896153.htm
- http://m.blog.oexnr.cn/snews/3017248.htm
- http://m.blog.oexnr.cn/snews/276997.htm
- http://m.blog.oexnr.cn/snews/7109.htm
- http://m.blog.oexnr.cn/snews/9462632.htm
- http://m.blog.oexnr.cn/snews/9006.htm
- http://m.blog.oexnr.cn/snews/49538.htm
- http://m.blog.oexnr.cn/snews/160986.htm
- http://m.blog.oexnr.cn/snews/76353.htm
- http://m.blog.oexnr.cn/snews/8150688.htm
- http://m.blog.oexnr.cn/snews/3202.htm
- http://m.blog.oexnr.cn/snews/4396.htm
- http://m.blog.oexnr.cn/snews/1876.htm
- http://m.blog.oexnr.cn/snews/820456.htm
- http://m.blog.oexnr.cn/snews/17475.htm
- http://m.blog.oexnr.cn/snews/37401.htm
- http://m.blog.oexnr.cn/snews/0373.htm
- http://m.blog.oexnr.cn/snews/87009.htm
- http://m.blog.oexnr.cn/snews/4755560.htm
- http://m.blog.oexnr.cn/snews/62426.htm
- http://m.blog.oexnr.cn/snews/269982.htm
- http://m.blog.oexnr.cn/snews/0789.htm
- http://m.blog.oexnr.cn/snews/283653.htm
- http://m.blog.oexnr.cn/snews/06960.htm
- http://m.blog.oexnr.cn/snews/5323590.htm
- http://m.blog.oexnr.cn/snews/904860.htm
- http://m.blog.oexnr.cn/snews/704385.htm
- http://m.blog.oexnr.cn/snews/3733140.htm
- http://m.blog.oexnr.cn/snews/53629.htm
- http://m.blog.oexnr.cn/snews/0835839.htm
- http://m.blog.oexnr.cn/snews/7866.htm
- http://m.blog.oexnr.cn/snews/22781.htm
- http://m.blog.oexnr.cn/snews/3898.htm
- http://m.blog.oexnr.cn/snews/6744539.htm
- http://m.blog.oexnr.cn/snews/88561.htm
- http://m.blog.oexnr.cn/snews/6700711.htm
- http://m.blog.oexnr.cn/snews/659469.htm
- http://m.blog.oexnr.cn/snews/36088.htm
- http://m.blog.oexnr.cn/snews/6671747.htm
- http://m.blog.oexnr.cn/snews/9081.htm
- http://m.blog.oexnr.cn/snews/172649.htm
- http://m.blog.oexnr.cn/snews/1507.htm
- http://m.blog.oexnr.cn/snews/6911009.htm
- http://m.blog.oexnr.cn/snews/4168899.htm
- http://m.blog.oexnr.cn/snews/9711245.htm
- http://m.blog.oexnr.cn/snews/88531.htm
- http://m.blog.oexnr.cn/snews/215124.htm
- http://m.blog.oexnr.cn/snews/8803294.htm
- http://m.blog.oexnr.cn/snews/4745646.htm
- http://m.blog.oexnr.cn/snews/929729.htm
- http://m.blog.oexnr.cn/snews/557718.htm
- http://m.blog.oexnr.cn/snews/13363.htm
- http://m.blog.oexnr.cn/snews/6292.htm
- http://m.blog.oexnr.cn/snews/3303.htm
- http://m.blog.oexnr.cn/snews/6874459.htm
- http://m.blog.oexnr.cn/snews/1767.htm
- http://m.blog.oexnr.cn/snews/1524.htm
- http://m.blog.oexnr.cn/snews/725660.htm
- http://m.blog.oexnr.cn/snews/5411.htm
- http://m.blog.oexnr.cn/snews/2985.htm
- http://m.blog.oexnr.cn/snews/94564.htm
- http://m.blog.oexnr.cn/snews/908741.htm
- http://m.blog.oexnr.cn/snews/7855083.htm
- http://m.blog.oexnr.cn/snews/7093069.htm
- http://m.blog.oexnr.cn/snews/35269.htm
- http://m.blog.oexnr.cn/snews/7145908.htm
- http://m.blog.oexnr.cn/snews/9728745.htm
- http://m.blog.oexnr.cn/snews/434874.htm
- http://m.blog.oexnr.cn/snews/5120059.htm
- http://m.blog.oexnr.cn/snews/785598.htm
- http://m.blog.oexnr.cn/snews/63289.htm
- http://m.blog.oexnr.cn/snews/964542.htm
- http://m.blog.oexnr.cn/snews/12420.htm
- http://m.blog.oexnr.cn/snews/3782954.htm
- http://m.blog.oexnr.cn/snews/0357477.htm
- http://m.blog.oexnr.cn/snews/5965032.htm
- http://m.blog.oexnr.cn/snews/756969.htm
- http://m.blog.oexnr.cn/snews/16457.htm
- http://m.blog.oexnr.cn/snews/16363.htm
- http://m.blog.oexnr.cn/snews/13689.htm
- http://m.blog.oexnr.cn/snews/9931.htm
- http://m.blog.oexnr.cn/snews/7559.htm
- http://m.blog.oexnr.cn/snews/323596.htm
- http://m.blog.oexnr.cn/snews/809624.htm
- http://m.blog.oexnr.cn/snews/583691.htm
- http://m.blog.oexnr.cn/snews/1140112.htm
- http://m.blog.oexnr.cn/snews/956591.htm
- http://m.blog.oexnr.cn/snews/216354.htm
- http://m.blog.oexnr.cn/snews/496776.htm
- http://m.blog.oexnr.cn/snews/29483.htm
- http://m.blog.oexnr.cn/snews/5050327.htm
- http://m.blog.oexnr.cn/snews/99417.htm
- http://m.blog.oexnr.cn/snews/7317433.htm
- http://m.blog.oexnr.cn/snews/908941.htm
- http://m.blog.oexnr.cn/snews/3961.htm

## 项目结构

```
weblink-nexus/
├── src/
│   ├── core/                        # 核心业务逻辑层
│   │   ├── linkValidator.js         # 链接格式校验、去重、规范化（但不改写原始值）
│   │   ├── metadataFetcher.js       # 并发获取链接元数据，含超时与重试策略
│   │   └── healthChecker.js         # 定时健康检查调度器，支持 cron 表达式配置
│   ├── api/                         # RESTful API 路由与控制器
│   │   ├── v1/
│   │   │   ├── routes.js            # 路由聚合，挂载 /api/v1/links 等端点
│   │   │   └── linkController.js    # 请求参数解析、调用 core 层、返回 JSON 响应
│   ├── ui/                          # Web 管理界面（嵌入式静态资源）
│   │   ├── dashboard.html           # 概览面板，展示链接总数、健康率、最近导入记录
│   │   ├── import.html              # 批量导入页面，支持粘贴文本或上传 CSV 文件
│   │   └── search.html              # 高级搜索与过滤界面，动态生成标签筛选器
│   ├── db/                          # 数据库适配层
│   │   ├── sqliteAdapter.js         # SQLite3 连接池、建表语句、CRUD 操作封装
│   │   └── postgresAdapter.js       # PostgreSQL 适配器（可选，通过环境变量切换）
│   ├── scheduler/                   # 后台任务调度
│   │   ├── index.js                 # 启动时注册所有定时任务，依赖 node-cron
│   │   └── healthJob.js             # 健康检查任务的具体执行逻辑与结果持久化
│   ├── lib/                         # 通用工具函数
│   │   ├── logger.js                # 基于 winston 的日志系统，支持按级别输出到文件与控制台
│   │   └── config.js                # 集中读取环境变量，提供默认值及类型转换
│   └── app.js                       # 应用入口，初始化数据库、加载中间件、启动 HTTP 服务
├── tests/                           # 单元测试与集成测试
│   ├── unit/
│   │   └── linkValidator.test.js    # 校验去重逻辑的边界用例（含裸域名、带协议、大小写）
│   └── integration/
│       └── api.test.js              # 对 /api/v1/links 端点进行完整请求-响应测试
├── docs/                            # 文档源文件（对应文档导航章节）
│   ├── getting-started.md
│   ├── configuration.md
│   ├── api-reference.md
│   └── operations.md
├── scripts/                         # 运维辅助脚本
│   ├── backup.sh                    # 备份 SQLite 数据库文件到指定目录
│   └── migrate-to-postgres.sh       # 从 SQLite 导出数据并导入 PostgreSQL
├── package.json                     # npm 依赖声明、scripts 命令（build、start、test）
├── .env.example                     # 环境变量配置模板（数据库 URL、调度间隔、端口）
├── .gitignore                       # 忽略 node_modules、日志文件、本地数据库文件
└── README.md                        # 本文档
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。确保本地 Node.js 版本符合安装要求，执行 `npm install` 安装所有依赖。

2. 创建新的功能分支，分支名称遵循 `feature/描述` 或 `fix/描述` 格式。所有代码变更需包含对应的单元测试，保证测试覆盖率达到 80% 以上。

3. 完成开发后，执行 `npm run lint` 检查代码风格，执行 `npm test` 确保所有测试通过。提交信息请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`chore:` 等前缀。

4. 推送分支到个人 Fork 仓库，然后通过 GitHub UI 发起 Pull Request 到主仓库的 main 分支。PR 描述中请清晰说明变更目的、影响范围以及测试情况。

5. 项目维护者会在 3 个工作日内进行代码审查，可能会提出修改意见。合并后您的贡献将被列入贡献者列表，并出现在后续版本的发布说明中。

## 常见问题

**问：导入链接时，系统是否会修改原始 URL 的协议或域名格式？**

答：不会。WebLink Nexus 在存储层完全保留用户输入的原始 URL 字面值，不做任何自动补全（如添加 http://、https://、www. 前缀）、不修改协议类型、不改变大小写、不增加或删除结尾斜杠。所有校验仅用于检测重复与格式合法性，但存储值始终为原始输入。

**问：健康检查如何判断一个链接是否失效？**

答：健康检查模块默认发送 HTTP HEAD 请求，若返回状态码在 200 至 399 范围内视为有效；若返回 404、410 或连接超时（默认 5 秒）则标记为失效。对于不支持 HEAD 的资源，系统自动降级为 GET 请求并仅读取响应头，不下载完整内容。用户可在配置文件中调整超时时间与重试次数。

**问：能否将 WebLink Nexus 部署到内网环境且不访问外网？**

答：可以。项目的核心功能（导入、分类、检索、导出）完全不依赖外网访问。健康检查模块默认会对外链发起网络请求，但在内网环境下您可以选择禁用该功能，或将其配置为仅检测内网资源。数据库与 Web 界面均可在完全隔离的网络中正常运行。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
