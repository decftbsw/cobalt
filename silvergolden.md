# WebLink Hub

WebLink Hub 是一个面向技术研究者、信息聚合开发者与内容管理团队的高密度外链资源归集与分发平台。本项目定位于将分散在多个数据源中的新闻类、公告类与信息类 URL 进行集中化整理、分类存储与快速检索，解决信息碎片化导致的资源查找效率低下问题。通过结构化的目录设计与标准化的文档输出，WebLink Hub 可作为静态站点生成器的数据源，也可嵌入现有 CMS 或知识库系统作为外链模块使用。目标用户包括技术文档工程师、开源社区维护者、数据采集与清洗工程师以及需要定期跟踪大量信息源的分析人员。

## 功能概览

- **批量链接归集**：支持将大批量 URL 按来源、批次或时间维度进行统一收录与归档，本项目第 154/300 批次已完成 300 个资源链接的标准化入库。

- **链接状态标记**：每条资源均包含访问协议、域名路径与资源标识三段式结构，便于二次开发时进行存活检测与状态标注。

- **分类层级索引**：按 /jnews/ 路径前缀下的数字 ID 进行自动分类，支持按 ID 范围或正则表达式进行快速筛选与提取。

- **纯静态输出**：项目文档与资源列表全部采用 Markdown 格式输出，无需数据库支持，可无缝集成至 GitHub Pages、VitePress、Docsify 等静态站点工具。

- **版本化批次管理**：每批次资源独立成档，支持按批次号回滚、对比与增量更新，适合长期运营的链接库项目。

- **多维度检索支持**：通过文档中的表格与目录树结构，用户可依据依赖类型、应用场景或目录层级快速定位所需资源。

- **扩展接口预留**：项目结构中的 scripts 与 data 目录提供可插拔的脚本模板与数据缓存层，便于接入自动更新管道或定时抓取任务。

## 应用场景

- **技术文档外链管理**：技术团队在编写产品文档或 API 参考时，需引用大量外部新闻公告与版本发布信息。WebLink Hub 提供统一的链接挂载点，避免文档中散落不可控的外部地址，提升文档的长期可维护性。

- **数据采集管道测试**：数据工程师在构建爬虫或 API 采集流程时，需要大量真实 URL 作为测试样本。本项目的资源列表可作为样本池，用于验证链接提取、去重与规范化逻辑的健壮性。

- **信息监控仪表盘数据源**：运维或安全团队可定期拉取本项目的资源列表，与内部监控系统对接，对指定域名下的路径进行可用性与内容变更检测，生成态势感知报表。

- **开源项目 README 引用仓库**：开源作者可将 WebLink Hub 作为子模块引入自身项目，用于存放外部参考链接或致谢列表，避免主仓库文档臃肿，同时保持引用记录的独立版本管理。

- **知识库初始化种子数据**：企业知识库或团队 Wiki 新建时，需填充初始外链数据以测试分类与搜索功能。本项目提供的结构化列表可直接导入作为种子数据，降低环境搭建成本。

## 快速开始

以下命令将项目克隆至本地、安装基础依赖并启动本地预览服务。请确保系统已安装 Git 与 Node.js 环境。

```bash
git clone https://github.com/weblink-hub/weblink-hub.git
cd weblink-hub
npm install
npm run build
```

执行完成后，资源列表将输出至 dist/links.md 文件，用户可通过任意 Markdown 阅读器查看或将其复制至目标项目中。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 16.x 或更高 | 用于运行构建脚本与链接格式化工具 |
| npm | 8.x 或更高 | 依赖管理与任务脚本执行 |
| Git | 2.30 或更高 | 用于克隆仓库与版本控制 |
| Markdown 解析器 | 任意兼容 CommonMark 的解析器 | 用于本地预览文档内容 |
| 网络连接 | 访问外网能力 | 仅在验证链接存活状态时需要，本地构建无需网络 |
| 磁盘空间 | 至少 10 MB | 用于存储源码与构建产物 |
| 操作系统 | Linux / macOS / Windows (WSL 推荐) | 跨平台支持，脚本中无平台特定命令 |
| 文本编辑器 | UTF-8 编码支持 | 用于查看或修改资源列表与文档 |
| 时区设置 | UTC+8 推荐 | 用于批次时间戳记录，非强制 |
| 权限 | 对项目目录的读写权限 | 用于生成输出文件与日志 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 项目概览 | README.md | 项目是什么、谁该使用、核心功能与如何开始 |
| 资源列表 | docs/links.md | 当前批次收录的全部 URL 详细清单 |
| 批次说明 | docs/batches/154.md | 第 154/300 批次的采集时间、来源说明与字段映射规则 |
| 贡献流程 | CONTRIBUTING.md | 如何新增批次、更新链接或提交修复补丁 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/24533.htm
- http://m.wap.ghtkgg.cn/jnews/88243.htm
- http://m.wap.ghtkgg.cn/jnews/66577.htm
- http://m.wap.ghtkgg.cn/jnews/01044.htm
- http://m.wap.ghtkgg.cn/jnews/85946.htm
- http://m.wap.ghtkgg.cn/jnews/1661.htm
- http://m.wap.ghtkgg.cn/jnews/8810.htm
- http://m.wap.ghtkgg.cn/jnews/1214.htm
- http://m.wap.ghtkgg.cn/jnews/2528.htm
- http://m.wap.ghtkgg.cn/jnews/12434.htm
- http://m.wap.ghtkgg.cn/jnews/23215.htm
- http://m.wap.ghtkgg.cn/jnews/184144.htm
- http://m.wap.ghtkgg.cn/jnews/0171.htm
- http://m.wap.ghtkgg.cn/jnews/11157.htm
- http://m.wap.ghtkgg.cn/jnews/0270909.htm
- http://m.wap.ghtkgg.cn/jnews/729047.htm
- http://m.wap.ghtkgg.cn/jnews/3504292.htm
- http://m.wap.ghtkgg.cn/jnews/6302073.htm
- http://m.wap.ghtkgg.cn/jnews/29334.htm
- http://m.wap.ghtkgg.cn/jnews/4580.htm
- http://m.wap.ghtkgg.cn/jnews/254017.htm
- http://m.wap.ghtkgg.cn/jnews/2141.htm
- http://m.wap.ghtkgg.cn/jnews/9460.htm
- http://m.wap.ghtkgg.cn/jnews/063751.htm
- http://m.wap.ghtkgg.cn/jnews/38933.htm
- http://m.wap.ghtkgg.cn/jnews/0068130.htm
- http://m.wap.ghtkgg.cn/jnews/1667220.htm
- http://m.wap.ghtkgg.cn/jnews/75025.htm
- http://m.wap.ghtkgg.cn/jnews/45817.htm
- http://m.wap.ghtkgg.cn/jnews/286838.htm
- http://m.wap.ghtkgg.cn/jnews/7475.htm
- http://m.wap.ghtkgg.cn/jnews/38802.htm
- http://m.wap.ghtkgg.cn/jnews/023279.htm
- http://m.wap.ghtkgg.cn/jnews/441546.htm
- http://m.wap.ghtkgg.cn/jnews/1202736.htm
- http://m.wap.ghtkgg.cn/jnews/565642.htm
- http://m.wap.ghtkgg.cn/jnews/460877.htm
- http://m.wap.ghtkgg.cn/jnews/34946.htm
- http://m.wap.ghtkgg.cn/jnews/73135.htm
- http://m.wap.ghtkgg.cn/jnews/978918.htm
- http://m.wap.ghtkgg.cn/jnews/273379.htm
- http://m.wap.ghtkgg.cn/jnews/72847.htm
- http://m.wap.ghtkgg.cn/jnews/2804.htm
- http://m.wap.ghtkgg.cn/jnews/077798.htm
- http://m.wap.ghtkgg.cn/jnews/7061738.htm
- http://m.wap.ghtkgg.cn/jnews/6963413.htm
- http://m.wap.ghtkgg.cn/jnews/0039183.htm
- http://m.wap.ghtkgg.cn/jnews/2748.htm
- http://m.wap.ghtkgg.cn/jnews/61609.htm
- http://m.wap.ghtkgg.cn/jnews/285891.htm
- http://m.wap.ghtkgg.cn/jnews/1689541.htm
- http://m.wap.ghtkgg.cn/jnews/024588.htm
- http://m.wap.ghtkgg.cn/jnews/0904231.htm
- http://m.wap.ghtkgg.cn/jnews/376010.htm
- http://m.wap.ghtkgg.cn/jnews/49209.htm
- http://m.wap.ghtkgg.cn/jnews/638769.htm
- http://m.wap.ghtkgg.cn/jnews/4288952.htm
- http://m.wap.ghtkgg.cn/jnews/4352.htm
- http://m.wap.ghtkgg.cn/jnews/5780991.htm
- http://m.wap.ghtkgg.cn/jnews/7578.htm
- http://m.wap.ghtkgg.cn/jnews/9446706.htm
- http://m.wap.ghtkgg.cn/jnews/897204.htm
- http://m.wap.ghtkgg.cn/jnews/89228.htm
- http://m.wap.ghtkgg.cn/jnews/562433.htm
- http://m.wap.ghtkgg.cn/jnews/43781.htm
- http://m.wap.ghtkgg.cn/jnews/8858.htm
- http://m.wap.ghtkgg.cn/jnews/39669.htm
- http://m.wap.ghtkgg.cn/jnews/550140.htm
- http://m.wap.ghtkgg.cn/jnews/7755.htm
- http://m.wap.ghtkgg.cn/jnews/5610382.htm
- http://m.wap.ghtkgg.cn/jnews/33004.htm
- http://m.wap.ghtkgg.cn/jnews/847073.htm
- http://m.wap.ghtkgg.cn/jnews/91827.htm
- http://m.wap.ghtkgg.cn/jnews/8335588.htm
- http://m.wap.ghtkgg.cn/jnews/0280589.htm
- http://m.wap.ghtkgg.cn/jnews/050691.htm
- http://m.wap.ghtkgg.cn/jnews/230092.htm
- http://m.wap.ghtkgg.cn/jnews/0228157.htm
- http://m.wap.ghtkgg.cn/jnews/747264.htm
- http://m.wap.ghtkgg.cn/jnews/3548.htm
- http://m.wap.ghtkgg.cn/jnews/5847.htm
- http://m.wap.ghtkgg.cn/jnews/407394.htm
- http://m.wap.ghtkgg.cn/jnews/673630.htm
- http://m.wap.ghtkgg.cn/jnews/7327498.htm
- http://m.wap.ghtkgg.cn/jnews/2919163.htm
- http://m.wap.ghtkgg.cn/jnews/570878.htm
- http://m.wap.ghtkgg.cn/jnews/5589577.htm
- http://m.wap.ghtkgg.cn/jnews/91527.htm
- http://m.wap.ghtkgg.cn/jnews/8317.htm
- http://m.wap.ghtkgg.cn/jnews/449897.htm
- http://m.wap.ghtkgg.cn/jnews/60470.htm
- http://m.wap.ghtkgg.cn/jnews/6787.htm
- http://m.wap.ghtkgg.cn/jnews/7093.htm
- http://m.wap.ghtkgg.cn/jnews/0213.htm
- http://m.wap.ghtkgg.cn/jnews/7410760.htm
- http://m.wap.ghtkgg.cn/jnews/7013.htm
- http://m.wap.ghtkgg.cn/jnews/7103.htm
- http://m.wap.ghtkgg.cn/jnews/2883.htm
- http://m.wap.ghtkgg.cn/jnews/7323456.htm
- http://m.wap.ghtkgg.cn/jnews/89466.htm
- http://m.wap.ghtkgg.cn/jnews/4614.htm
- http://m.wap.ghtkgg.cn/jnews/30963.htm
- http://m.wap.ghtkgg.cn/jnews/1643.htm
- http://m.wap.ghtkgg.cn/jnews/1103936.htm
- http://m.wap.ghtkgg.cn/jnews/8519247.htm
- http://m.wap.ghtkgg.cn/jnews/54279.htm
- http://m.wap.ghtkgg.cn/jnews/98001.htm
- http://m.wap.ghtkgg.cn/jnews/9502822.htm
- http://m.wap.ghtkgg.cn/jnews/2535984.htm
- http://m.wap.ghtkgg.cn/jnews/01904.htm
- http://m.wap.ghtkgg.cn/jnews/0238905.htm
- http://m.wap.ghtkgg.cn/jnews/98396.htm
- http://m.wap.ghtkgg.cn/jnews/0160246.htm
- http://m.wap.ghtkgg.cn/jnews/8449.htm
- http://m.wap.ghtkgg.cn/jnews/06679.htm
- http://m.wap.ghtkgg.cn/jnews/9362553.htm
- http://m.wap.ghtkgg.cn/jnews/4060231.htm
- http://m.wap.ghtkgg.cn/jnews/01518.htm
- http://m.wap.ghtkgg.cn/jnews/9961991.htm
- http://m.wap.ghtkgg.cn/jnews/2436.htm
- http://m.wap.ghtkgg.cn/jnews/15106.htm
- http://m.wap.ghtkgg.cn/jnews/3394.htm
- http://m.wap.ghtkgg.cn/jnews/5607078.htm
- http://m.wap.ghtkgg.cn/jnews/1484992.htm
- http://m.wap.ghtkgg.cn/jnews/48527.htm
- http://m.wap.ghtkgg.cn/jnews/414902.htm
- http://m.wap.ghtkgg.cn/jnews/0906051.htm
- http://m.wap.ghtkgg.cn/jnews/2429237.htm
- http://m.wap.ghtkgg.cn/jnews/4220.htm
- http://m.wap.ghtkgg.cn/jnews/9070.htm
- http://m.wap.ghtkgg.cn/jnews/8129.htm
- http://m.wap.ghtkgg.cn/jnews/5554528.htm
- http://m.wap.ghtkgg.cn/jnews/30187.htm
- http://m.wap.ghtkgg.cn/jnews/9620811.htm
- http://m.wap.ghtkgg.cn/jnews/78296.htm
- http://m.wap.ghtkgg.cn/jnews/9102906.htm
- http://m.wap.ghtkgg.cn/jnews/34428.htm
- http://m.wap.ghtkgg.cn/jnews/9097504.htm
- http://m.wap.ghtkgg.cn/jnews/401809.htm
- http://m.wap.ghtkgg.cn/jnews/001007.htm
- http://m.wap.ghtkgg.cn/jnews/7156.htm
- http://m.wap.ghtkgg.cn/jnews/94964.htm
- http://m.wap.ghtkgg.cn/jnews/1014.htm
- http://m.wap.ghtkgg.cn/jnews/8037.htm
- http://m.wap.ghtkgg.cn/jnews/0149717.htm
- http://m.wap.ghtkgg.cn/jnews/665931.htm
- http://m.wap.ghtkgg.cn/jnews/148681.htm
- http://m.wap.ghtkgg.cn/jnews/762757.htm
- http://m.wap.ghtkgg.cn/jnews/65301.htm
- http://m.wap.ghtkgg.cn/jnews/3283.htm
- http://m.wap.ghtkgg.cn/jnews/229430.htm
- http://m.wap.ghtkgg.cn/jnews/554621.htm
- http://m.wap.ghtkgg.cn/jnews/8576481.htm
- http://m.wap.ghtkgg.cn/jnews/73099.htm
- http://m.wap.ghtkgg.cn/jnews/4914263.htm
- http://m.wap.ghtkgg.cn/jnews/79579.htm
- http://m.wap.ghtkgg.cn/jnews/145294.htm
- http://m.wap.ghtkgg.cn/jnews/8361113.htm
- http://m.wap.ghtkgg.cn/jnews/2243.htm
- http://m.wap.ghtkgg.cn/jnews/0019246.htm
- http://m.wap.ghtkgg.cn/jnews/466379.htm
- http://m.wap.ghtkgg.cn/jnews/0530783.htm
- http://m.wap.ghtkgg.cn/jnews/53024.htm
- http://m.wap.ghtkgg.cn/jnews/1621.htm
- http://m.wap.ghtkgg.cn/jnews/761668.htm
- http://m.wap.ghtkgg.cn/jnews/0889518.htm
- http://m.wap.ghtkgg.cn/jnews/2349.htm
- http://m.wap.ghtkgg.cn/jnews/0243.htm
- http://m.wap.ghtkgg.cn/jnews/216876.htm
- http://m.wap.ghtkgg.cn/jnews/257249.htm
- http://m.wap.ghtkgg.cn/jnews/59741.htm
- http://m.wap.ghtkgg.cn/jnews/5947.htm
- http://m.wap.ghtkgg.cn/jnews/74566.htm
- http://m.wap.ghtkgg.cn/jnews/2072517.htm
- http://m.wap.ghtkgg.cn/jnews/0159.htm
- http://m.wap.ghtkgg.cn/jnews/2631913.htm
- http://m.wap.ghtkgg.cn/jnews/5691.htm
- http://m.wap.ghtkgg.cn/jnews/820482.htm
- http://m.wap.ghtkgg.cn/jnews/9780.htm
- http://m.wap.ghtkgg.cn/jnews/2158.htm
- http://m.wap.ghtkgg.cn/jnews/09816.htm
- http://m.wap.ghtkgg.cn/jnews/9380.htm
- http://m.wap.ghtkgg.cn/jnews/42796.htm
- http://m.wap.ghtkgg.cn/jnews/809914.htm
- http://m.wap.ghtkgg.cn/jnews/65280.htm
- http://m.wap.ghtkgg.cn/jnews/64584.htm
- http://m.wap.ghtkgg.cn/jnews/850951.htm
- http://m.wap.ghtkgg.cn/jnews/65818.htm
- http://m.wap.ghtkgg.cn/jnews/304733.htm
- http://m.wap.ghtkgg.cn/jnews/3036379.htm
- http://m.wap.ghtkgg.cn/jnews/5595130.htm
- http://m.wap.ghtkgg.cn/jnews/223649.htm
- http://m.wap.ghtkgg.cn/jnews/2485.htm
- http://m.wap.ghtkgg.cn/jnews/444661.htm
- http://m.wap.ghtkgg.cn/jnews/3977487.htm
- http://m.wap.ghtkgg.cn/jnews/28763.htm
- http://m.wap.ghtkgg.cn/jnews/40914.htm
- http://m.wap.ghtkgg.cn/jnews/2845.htm
- http://m.wap.ghtkgg.cn/jnews/9453.htm
- http://m.wap.ghtkgg.cn/jnews/8159104.htm
- http://m.wap.ghtkgg.cn/jnews/16227.htm
- http://m.wap.ghtkgg.cn/jnews/597771.htm
- http://m.wap.ghtkgg.cn/jnews/3074430.htm
- http://m.wap.ghtkgg.cn/jnews/97621.htm
- http://m.wap.ghtkgg.cn/jnews/4926547.htm
- http://m.wap.ghtkgg.cn/jnews/08076.htm
- http://m.wap.ghtkgg.cn/jnews/924539.htm
- http://m.wap.ghtkgg.cn/jnews/93158.htm
- http://m.wap.ghtkgg.cn/jnews/762160.htm
- http://m.wap.ghtkgg.cn/jnews/97786.htm
- http://m.wap.ghtkgg.cn/jnews/671559.htm
- http://m.wap.ghtkgg.cn/jnews/63397.htm
- http://m.wap.ghtkgg.cn/jnews/0781900.htm
- http://m.wap.ghtkgg.cn/jnews/2138.htm
- http://m.wap.ghtkgg.cn/jnews/42267.htm
- http://m.wap.ghtkgg.cn/jnews/44041.htm
- http://m.wap.ghtkgg.cn/jnews/450907.htm
- http://m.wap.ghtkgg.cn/jnews/92020.htm
- http://m.wap.ghtkgg.cn/jnews/554550.htm
- http://m.wap.ghtkgg.cn/jnews/63083.htm
- http://m.wap.ghtkgg.cn/jnews/4632968.htm
- http://m.wap.ghtkgg.cn/jnews/053587.htm
- http://m.wap.ghtkgg.cn/jnews/425202.htm
- http://m.wap.ghtkgg.cn/jnews/84188.htm
- http://m.wap.ghtkgg.cn/jnews/1300924.htm
- http://m.wap.ghtkgg.cn/jnews/2322222.htm
- http://m.wap.ghtkgg.cn/jnews/80082.htm
- http://m.wap.ghtkgg.cn/jnews/2198990.htm
- http://m.wap.ghtkgg.cn/jnews/904510.htm
- http://m.wap.ghtkgg.cn/jnews/2828282.htm
- http://m.wap.ghtkgg.cn/jnews/1483223.htm
- http://m.wap.ghtkgg.cn/jnews/2909490.htm
- http://m.wap.ghtkgg.cn/jnews/3471966.htm
- http://m.wap.ghtkgg.cn/jnews/8477686.htm
- http://m.wap.ghtkgg.cn/jnews/516807.htm
- http://m.wap.ghtkgg.cn/jnews/5377.htm
- http://m.wap.ghtkgg.cn/jnews/8045714.htm
- http://m.wap.ghtkgg.cn/jnews/1530.htm
- http://m.wap.ghtkgg.cn/jnews/7490230.htm
- http://m.wap.ghtkgg.cn/jnews/48178.htm
- http://m.wap.ghtkgg.cn/jnews/068993.htm
- http://m.wap.ghtkgg.cn/jnews/9951.htm
- http://m.wap.ghtkgg.cn/jnews/28017.htm
- http://m.wap.ghtkgg.cn/jnews/0413082.htm
- http://m.wap.ghtkgg.cn/jnews/22763.htm
- http://m.wap.ghtkgg.cn/jnews/099587.htm
- http://m.wap.ghtkgg.cn/jnews/545205.htm
- http://m.wap.ghtkgg.cn/jnews/94307.htm
- http://m.wap.ghtkgg.cn/jnews/2524.htm
- http://m.wap.ghtkgg.cn/jnews/19294.htm
- http://m.wap.ghtkgg.cn/jnews/340656.htm
- http://m.wap.ghtkgg.cn/jnews/78178.htm
- http://m.wap.ghtkgg.cn/jnews/2433.htm
- http://m.wap.ghtkgg.cn/jnews/9199271.htm
- http://m.wap.ghtkgg.cn/jnews/7785.htm
- http://m.wap.ghtkgg.cn/jnews/953131.htm
- http://m.wap.ghtkgg.cn/jnews/28105.htm
- http://m.wap.ghtkgg.cn/jnews/78454.htm
- http://m.wap.ghtkgg.cn/jnews/76498.htm
- http://m.wap.ghtkgg.cn/jnews/570318.htm
- http://m.wap.ghtkgg.cn/jnews/7829981.htm
- http://m.wap.ghtkgg.cn/jnews/50251.htm
- http://m.wap.ghtkgg.cn/jnews/3957769.htm
- http://m.wap.ghtkgg.cn/jnews/45905.htm
- http://m.wap.ghtkgg.cn/jnews/1212.htm
- http://m.wap.ghtkgg.cn/jnews/1432.htm
- http://m.wap.ghtkgg.cn/jnews/8387.htm
- http://m.wap.ghtkgg.cn/jnews/98177.htm
- http://m.wap.ghtkgg.cn/jnews/008025.htm
- http://m.wap.ghtkgg.cn/jnews/85454.htm
- http://m.wap.ghtkgg.cn/jnews/92070.htm
- http://m.wap.ghtkgg.cn/jnews/005521.htm
- http://m.wap.ghtkgg.cn/jnews/3693718.htm
- http://m.wap.ghtkgg.cn/jnews/80980.htm
- http://m.wap.ghtkgg.cn/jnews/7537.htm
- http://m.wap.ghtkgg.cn/jnews/48131.htm
- http://m.wap.ghtkgg.cn/jnews/2785109.htm
- http://m.wap.ghtkgg.cn/jnews/66502.htm
- http://m.wap.ghtkgg.cn/jnews/363112.htm
- http://m.wap.ghtkgg.cn/jnews/813991.htm
- http://m.wap.ghtkgg.cn/jnews/7591229.htm
- http://m.wap.ghtkgg.cn/jnews/671352.htm
- http://m.wap.ghtkgg.cn/jnews/48576.htm
- http://m.wap.ghtkgg.cn/jnews/057191.htm
- http://m.wap.ghtkgg.cn/jnews/541840.htm
- http://m.wap.ghtkgg.cn/jnews/640788.htm
- http://m.wap.ghtkgg.cn/jnews/3001597.htm
- http://m.wap.ghtkgg.cn/jnews/4999813.htm
- http://m.wap.ghtkgg.cn/jnews/656561.htm
- http://m.wap.ghtkgg.cn/jnews/0583.htm
- http://m.wap.ghtkgg.cn/jnews/72926.htm
- http://m.wap.ghtkgg.cn/jnews/655898.htm
- http://m.wap.ghtkgg.cn/jnews/7276.htm
- http://m.wap.ghtkgg.cn/jnews/306427.htm
- http://m.wap.ghtkgg.cn/jnews/10188.htm
- http://m.wap.ghtkgg.cn/jnews/1130576.htm
- http://m.wap.ghtkgg.cn/jnews/05369.htm
- http://m.wap.ghtkgg.cn/jnews/2573.htm
- http://m.wap.ghtkgg.cn/jnews/0946.htm
- http://m.wap.ghtkgg.cn/jnews/78251.htm

## 项目结构

```
weblink-hub/
├── README.md                  # 项目概览与使用说明
├── CONTRIBUTING.md            # 贡献者指南与流程规范
├── LICENSE                    # MIT 许可证文件
├── package.json               # npm 项目配置与脚本定义
├── .gitignore                 # Git 忽略规则
├── docs/                      # 文档根目录
│   ├── links.md               # 当前全部资源列表的汇总文件
│   ├── batches/               # 按批次存放独立资源清单
│   │   └── 154.md             # 第 154/300 批次的详细记录
│   └── templates/             # 新批次或新文档的 Markdown 模板
│       └── batch_template.md  # 批次文档的标准结构模板
├── scripts/                   # 辅助脚本目录
│   ├── format.js              # URL 格式化与校验工具
│   ├── validate.js            # 链接重复性、协议一致性检查
│   └── build.js               # 构建入口，合并批次生成完整列表
├── data/                      # 数据缓存与中间产物
│   ├── raw/                   # 原始采集数据存放区
│   │   └── 154_raw.json       # 第 154 批原始数据 JSON 文件
│   └── cache/                 # 构建过程中生成的临时缓存
│       └── .last_build        # 最近一次构建时间戳记录
├── dist/                      # 构建输出目录
│   ├── links.md               # 最终生成的完整链接列表
│   └── stats.json             # 批次统计信息，含总数、协议分布等
└── tests/                     # 单元测试与集成测试
    ├── format.test.js         # 格式化函数的测试用例
    └── validate.test.js       # 校验逻辑的测试用例
```

## 贡献指南

1. 复刻本仓库至个人账户，并在本地创建功能分支。分支命名建议采用 feat/batch-{批次号} 或 fix/description 格式，以保持提交历史的清晰可溯。

2. 在 data/raw 目录下新增批次 JSON 文件，文件命名遵循 {批次号}_raw.json 规范。文件内部需包含 source、collected_at 与 entries 字段，其中 entries 为 URL 数组。新增的 URL 需确保协议与现有列表一致，且不包含重复项。

3. 执行 npm run validate 对新增数据进行格式与重复性校验，确保所有 URL 符合规范。若校验失败，请根据控制台输出修正数据文件后重新提交。

4. 提交变更时，请在 commit message 中注明批次号与操作类型，例如 "add: 第 155 批次资源入库" 或 "fix: 修正第 154 批次中格式错误的条目"。

5. 向本仓库主分支发起 Pull Request，等待维护者审核。审核通过后，变更将被合并，并自动触发构建流程更新 dist 目录下的输出文件。

## 常见问题

**问：资源列表中的 URL 为何全部采用 http 协议而非 https？**

答：本项目作为外链归集平台，严格保留原始数据的协议字段，以确保与上游数据源的字段映射关系完全一致，避免因协议变更导致的采集链路校验失败。用户在实际引用时，可根据自身需求通过脚本做协议归一化处理。

**问：如何获取第 154 批之外的其它批次资源？**

答：本项目采用分批管理策略，每批资源独立存放于 docs/batches/ 目录下。用户可通过查看该目录获取全部历史批次文件。若某批次尚未收录，欢迎按照贡献指南提交新增批次数据。

**问：项目中的 npm run build 具体执行了什么操作？**

答：build 脚本依次执行以下步骤：读取 data/raw 下所有 JSON 文件、校验字段完整性、按批次号排序、去重合并、生成带时间戳的统计信息，最后将完整链接列表写入 dist/links.md，并同步更新 docs/links.md 作为对外展示的稳定入口。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
