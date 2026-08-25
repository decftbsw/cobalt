# NavIndex Resource Aggregator

NavIndex is a high-performance, statically generated resource navigation and external link aggregation system designed for technical documentation teams, developer communities, and content curation workflows. It processes large batches of structured URL datasets—such as the 300-link batch presented in this release—and renders them into a searchable, categorizable, and maintainable knowledge index.

The project targets system administrators, technical writers, and DevOps engineers who need to publish, organize, and share curated lists of external references, news items, or documentation anchors without relying on dynamic databases or third-party CMS platforms. NavIndex consumes plain Markdown configuration and outputs a fully static HTML site that can be deployed to any web server, CDN, or cloud storage bucket.

## 功能概览

**Bulk URL ingestion** – Accepts plain-text or Markdown-formatted URL lists of arbitrary length, normalizes entries, and validates protocol consistency without altering the original user-supplied strings.

**Hierarchical categorization** – Supports multi-level tagging and directory-based classification, enabling users to group related resources by topic, domain, or usage context.

**Static site generation** – Produces a self-contained HTML output with zero runtime dependencies, ensuring fast load times and high compatibility with all major browsers.

**Search and filter** – Implements client-side full-text search and prefix-based filtering over titles, descriptions, and URL paths, with debounced input handling for large datasets.

**Batch metadata annotation** – Allows attaching custom metadata fields (such as status, priority, or source batch ID) to each URL entry via an external YAML sidecar file, without modifying the original list.

**Responsive presentation** – Renders the resource list in a mobile-friendly table layout with sortable columns, sticky headers, and pagination controls for datasets exceeding 50 items.

**Integrity preservation** – Enforces strict pass-through of user-provided URL strings, preventing automatic protocol upgrades, www prefix additions, or trailing slash insertions.

**Export and interoperability** – Provides export functions to CSV, JSON, and plain-text formats, facilitating integration with external data pipelines or monitoring tools.

## 应用场景

Technical documentation teams maintaining large reference sections can use NavIndex to publish external API endpoints, SDK download links, and specification documents in a single, version-controlled repository. The static generation model ensures that every commit produces a consistent, auditable snapshot of all referenced resources.

Developer community portals often need to aggregate forum threads, issue tracker links, and third-party tutorials. NavIndex enables community managers to curate these resources offline, review changes via pull requests, and deploy updated indexes without manual HTML editing.

Internal enterprise knowledge bases frequently contain hundreds of internal tool URLs, policy documents, and training materials. With NavIndex, these links can be organized by department, project, or compliance category, and the entire index can be served from an internal static hosting service with minimal infrastructure overhead.

Content researchers and data journalists compiling source material from multiple domains benefit from NavIndex's batch processing capabilities. The system can ingest large URL dumps, deduplicate entries, and produce a clean, navigable reference page that can be shared with collaborators or embedded in research publications.

## 快速开始

The following commands will clone the repository, install dependencies, and start the development server on localhost:8080.

```bash
git clone https://github.com/navindex/navindex.git
cd navindex
npm install
npm run build -- --input ./data/batch_174_300.txt --output ./dist
npm start
```

For production deployment, replace the build command with the production flag to enable minification and cache busting.

```bash
npm run build:prod -- --input ./data/batch_174_300.txt --output ./public
```

The generated static assets in the output directory can be copied directly to any web server or CDN origin.

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或更高 | 运行时环境，用于执行构建脚本和开发服务器 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Python | 3.9 或更高 | 仅在启用高级元数据解析插件时需要 |
| Git | 2.30 或更高 | 版本控制，用于克隆仓库和管理提交 |
| curl | 7.68 或更高 | 用于测试生成站点的链接可用性（可选） |
| 磁盘空间 | 至少 200 MB | 存放源码、依赖包和生成的静态文件 |
| 内存 | 至少 1 GB | 处理 300+ 条目的批处理构建所需的最小内存 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | /docs/user-guide/installation.md | 如何在不同操作系统上安装和配置 NavIndex |
| 用户指南 | /docs/user-guide/usage.md | 如何准备输入数据、运行构建和部署输出 |
| 开发者文档 | /docs/developer/api.md | 插件系统的接口定义和自定义扩展方法 |
| 开发者文档 | /docs/developer/contributing.md | 代码风格、测试要求和提交规范 |
| 运维手册 | /docs/operations/deployment.md | 如何配置 Nginx、S3 或 Cloudflare 托管生成的文件 |
| 运维手册 | /docs/operations/monitoring.md | 链接有效性检查、日志收集和性能调优 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/196021.htm
- http://m.blog.ghtkgg.cn/nnews/2230361.htm
- http://m.blog.ghtkgg.cn/nnews/20617.htm
- http://m.blog.ghtkgg.cn/nnews/21297.htm
- http://m.blog.ghtkgg.cn/nnews/4555.htm
- http://m.blog.ghtkgg.cn/nnews/63167.htm
- http://m.blog.ghtkgg.cn/nnews/051376.htm
- http://m.blog.ghtkgg.cn/nnews/7235.htm
- http://m.blog.ghtkgg.cn/nnews/3981.htm
- http://m.blog.ghtkgg.cn/nnews/331164.htm
- http://m.blog.ghtkgg.cn/nnews/0536971.htm
- http://m.blog.ghtkgg.cn/nnews/9168333.htm
- http://m.blog.ghtkgg.cn/nnews/9768.htm
- http://m.blog.ghtkgg.cn/nnews/149268.htm
- http://m.blog.ghtkgg.cn/nnews/1906939.htm
- http://m.blog.ghtkgg.cn/nnews/52118.htm
- http://m.blog.ghtkgg.cn/nnews/5157.htm
- http://m.blog.ghtkgg.cn/nnews/300005.htm
- http://m.blog.ghtkgg.cn/nnews/276173.htm
- http://m.blog.ghtkgg.cn/nnews/8398053.htm
- http://m.blog.ghtkgg.cn/nnews/9854455.htm
- http://m.blog.ghtkgg.cn/nnews/34269.htm
- http://m.blog.ghtkgg.cn/nnews/8114363.htm
- http://m.blog.ghtkgg.cn/nnews/33931.htm
- http://m.blog.ghtkgg.cn/nnews/13884.htm
- http://m.blog.ghtkgg.cn/nnews/9397318.htm
- http://m.blog.ghtkgg.cn/nnews/3052296.htm
- http://m.blog.ghtkgg.cn/nnews/7309826.htm
- http://m.blog.ghtkgg.cn/nnews/590859.htm
- http://m.blog.ghtkgg.cn/nnews/368753.htm
- http://m.blog.ghtkgg.cn/nnews/0679.htm
- http://m.blog.ghtkgg.cn/nnews/811521.htm
- http://m.blog.ghtkgg.cn/nnews/4844.htm
- http://m.blog.ghtkgg.cn/nnews/4271.htm
- http://m.blog.ghtkgg.cn/nnews/648095.htm
- http://m.blog.ghtkgg.cn/nnews/680822.htm
- http://m.blog.ghtkgg.cn/nnews/5131.htm
- http://m.blog.ghtkgg.cn/nnews/0162467.htm
- http://m.blog.ghtkgg.cn/nnews/714990.htm
- http://m.blog.ghtkgg.cn/nnews/2598550.htm
- http://m.blog.ghtkgg.cn/nnews/082306.htm
- http://m.blog.ghtkgg.cn/nnews/2228318.htm
- http://m.blog.ghtkgg.cn/nnews/8042982.htm
- http://m.blog.ghtkgg.cn/nnews/583731.htm
- http://m.blog.ghtkgg.cn/nnews/476670.htm
- http://m.blog.ghtkgg.cn/nnews/277358.htm
- http://m.blog.ghtkgg.cn/nnews/4597.htm
- http://m.blog.ghtkgg.cn/nnews/0581373.htm
- http://m.blog.ghtkgg.cn/nnews/0356.htm
- http://m.blog.ghtkgg.cn/nnews/0225.htm
- http://m.blog.ghtkgg.cn/nnews/440143.htm
- http://m.blog.ghtkgg.cn/nnews/895384.htm
- http://m.blog.ghtkgg.cn/nnews/18829.htm
- http://m.blog.ghtkgg.cn/nnews/330361.htm
- http://m.blog.ghtkgg.cn/nnews/4865173.htm
- http://m.blog.ghtkgg.cn/nnews/3299386.htm
- http://m.blog.ghtkgg.cn/nnews/7081841.htm
- http://m.blog.ghtkgg.cn/nnews/17305.htm
- http://m.blog.ghtkgg.cn/nnews/4927.htm
- http://m.blog.ghtkgg.cn/nnews/63404.htm
- http://m.blog.ghtkgg.cn/nnews/481751.htm
- http://m.blog.ghtkgg.cn/nnews/6339.htm
- http://m.blog.ghtkgg.cn/nnews/134474.htm
- http://m.blog.ghtkgg.cn/nnews/18614.htm
- http://m.blog.ghtkgg.cn/nnews/6622598.htm
- http://m.blog.ghtkgg.cn/nnews/734500.htm
- http://m.blog.ghtkgg.cn/nnews/3301.htm
- http://m.blog.ghtkgg.cn/nnews/81401.htm
- http://m.blog.ghtkgg.cn/nnews/4559624.htm
- http://m.blog.ghtkgg.cn/nnews/835856.htm
- http://m.blog.ghtkgg.cn/nnews/63281.htm
- http://m.blog.ghtkgg.cn/nnews/5573.htm
- http://m.blog.ghtkgg.cn/nnews/319288.htm
- http://m.blog.ghtkgg.cn/nnews/80342.htm
- http://m.blog.ghtkgg.cn/nnews/1884316.htm
- http://m.blog.ghtkgg.cn/nnews/331531.htm
- http://m.blog.ghtkgg.cn/nnews/38841.htm
- http://m.blog.ghtkgg.cn/nnews/013070.htm
- http://m.blog.ghtkgg.cn/nnews/6230323.htm
- http://m.blog.ghtkgg.cn/nnews/325993.htm
- http://m.blog.ghtkgg.cn/nnews/5790.htm
- http://m.blog.ghtkgg.cn/nnews/1361.htm
- http://m.blog.ghtkgg.cn/nnews/20601.htm
- http://m.blog.ghtkgg.cn/nnews/099603.htm
- http://m.blog.ghtkgg.cn/nnews/5270054.htm
- http://m.blog.ghtkgg.cn/nnews/38178.htm
- http://m.blog.ghtkgg.cn/nnews/7410264.htm
- http://m.blog.ghtkgg.cn/nnews/7606247.htm
- http://m.blog.ghtkgg.cn/nnews/0042532.htm
- http://m.blog.ghtkgg.cn/nnews/7721.htm
- http://m.blog.ghtkgg.cn/nnews/1488.htm
- http://m.blog.ghtkgg.cn/nnews/0858.htm
- http://m.blog.ghtkgg.cn/nnews/9001.htm
- http://m.blog.ghtkgg.cn/nnews/9615.htm
- http://m.blog.ghtkgg.cn/nnews/0922.htm
- http://m.blog.ghtkgg.cn/nnews/99111.htm
- http://m.blog.ghtkgg.cn/nnews/88570.htm
- http://m.blog.ghtkgg.cn/nnews/5067.htm
- http://m.blog.ghtkgg.cn/nnews/140092.htm
- http://m.blog.ghtkgg.cn/nnews/0464528.htm
- http://m.blog.ghtkgg.cn/nnews/3389.htm
- http://m.blog.ghtkgg.cn/nnews/5955427.htm
- http://m.blog.ghtkgg.cn/nnews/05816.htm
- http://m.blog.ghtkgg.cn/nnews/67020.htm
- http://m.blog.ghtkgg.cn/nnews/76692.htm
- http://m.blog.ghtkgg.cn/nnews/949663.htm
- http://m.blog.ghtkgg.cn/nnews/9801.htm
- http://m.blog.ghtkgg.cn/nnews/7810.htm
- http://m.blog.ghtkgg.cn/nnews/12799.htm
- http://m.blog.ghtkgg.cn/nnews/62231.htm
- http://m.blog.ghtkgg.cn/nnews/3560.htm
- http://m.blog.ghtkgg.cn/nnews/4164163.htm
- http://m.blog.ghtkgg.cn/nnews/04687.htm
- http://m.blog.ghtkgg.cn/nnews/069293.htm
- http://m.blog.ghtkgg.cn/nnews/0998333.htm
- http://m.blog.ghtkgg.cn/nnews/2770522.htm
- http://m.blog.ghtkgg.cn/nnews/39250.htm
- http://m.blog.ghtkgg.cn/nnews/6789049.htm
- http://m.blog.ghtkgg.cn/nnews/1891163.htm
- http://m.blog.ghtkgg.cn/nnews/387164.htm
- http://m.blog.ghtkgg.cn/nnews/11645.htm
- http://m.blog.ghtkgg.cn/nnews/5525.htm
- http://m.blog.ghtkgg.cn/nnews/33316.htm
- http://m.blog.ghtkgg.cn/nnews/1435.htm
- http://m.blog.ghtkgg.cn/nnews/7971.htm
- http://m.blog.ghtkgg.cn/nnews/4951210.htm
- http://m.blog.ghtkgg.cn/nnews/9675.htm
- http://m.blog.ghtkgg.cn/nnews/313469.htm
- http://m.blog.ghtkgg.cn/nnews/8652.htm
- http://m.blog.ghtkgg.cn/nnews/959068.htm
- http://m.blog.ghtkgg.cn/nnews/4650.htm
- http://m.blog.ghtkgg.cn/nnews/6852.htm
- http://m.blog.ghtkgg.cn/nnews/8105.htm
- http://m.blog.ghtkgg.cn/nnews/2779752.htm
- http://m.blog.ghtkgg.cn/nnews/301788.htm
- http://m.blog.ghtkgg.cn/nnews/148243.htm
- http://m.blog.ghtkgg.cn/nnews/92419.htm
- http://m.blog.ghtkgg.cn/nnews/355054.htm
- http://m.blog.ghtkgg.cn/nnews/6854701.htm
- http://m.blog.ghtkgg.cn/nnews/7551.htm
- http://m.blog.ghtkgg.cn/nnews/273705.htm
- http://m.blog.ghtkgg.cn/nnews/24725.htm
- http://m.blog.ghtkgg.cn/nnews/1892326.htm
- http://m.blog.ghtkgg.cn/nnews/12936.htm
- http://m.blog.ghtkgg.cn/nnews/8240101.htm
- http://m.blog.ghtkgg.cn/nnews/10976.htm
- http://m.blog.ghtkgg.cn/nnews/35319.htm
- http://m.blog.ghtkgg.cn/nnews/7150.htm
- http://m.blog.ghtkgg.cn/nnews/24188.htm
- http://m.blog.ghtkgg.cn/nnews/1141770.htm
- http://m.blog.ghtkgg.cn/nnews/5417.htm
- http://m.blog.ghtkgg.cn/nnews/67697.htm
- http://m.blog.ghtkgg.cn/nnews/0114274.htm
- http://m.blog.ghtkgg.cn/nnews/512731.htm
- http://m.blog.ghtkgg.cn/nnews/2447.htm
- http://m.blog.ghtkgg.cn/nnews/1915.htm
- http://m.blog.ghtkgg.cn/nnews/1001248.htm
- http://m.blog.ghtkgg.cn/nnews/6996.htm
- http://m.blog.ghtkgg.cn/nnews/24201.htm
- http://m.blog.ghtkgg.cn/nnews/7630369.htm
- http://m.blog.ghtkgg.cn/nnews/33553.htm
- http://m.blog.ghtkgg.cn/nnews/85216.htm
- http://m.blog.ghtkgg.cn/nnews/44996.htm
- http://m.blog.ghtkgg.cn/nnews/4776959.htm
- http://m.blog.ghtkgg.cn/nnews/7143722.htm
- http://m.blog.ghtkgg.cn/nnews/317511.htm
- http://m.blog.ghtkgg.cn/nnews/08660.htm
- http://m.blog.ghtkgg.cn/nnews/190961.htm
- http://m.blog.ghtkgg.cn/nnews/22355.htm
- http://m.blog.ghtkgg.cn/nnews/9134.htm
- http://m.blog.ghtkgg.cn/nnews/125348.htm
- http://m.blog.ghtkgg.cn/nnews/64515.htm
- http://m.blog.ghtkgg.cn/nnews/25831.htm
- http://m.blog.ghtkgg.cn/nnews/24247.htm
- http://m.blog.ghtkgg.cn/nnews/1181874.htm
- http://m.blog.ghtkgg.cn/nnews/980747.htm
- http://m.blog.ghtkgg.cn/nnews/5379452.htm
- http://m.blog.ghtkgg.cn/nnews/26360.htm
- http://m.blog.ghtkgg.cn/nnews/3134.htm
- http://m.blog.ghtkgg.cn/nnews/962447.htm
- http://m.blog.ghtkgg.cn/nnews/1074.htm
- http://m.blog.ghtkgg.cn/nnews/43489.htm
- http://m.blog.ghtkgg.cn/nnews/860103.htm
- http://m.blog.ghtkgg.cn/nnews/5578802.htm
- http://m.blog.ghtkgg.cn/nnews/3927.htm
- http://m.blog.ghtkgg.cn/nnews/3978.htm
- http://m.blog.ghtkgg.cn/nnews/397869.htm
- http://m.blog.ghtkgg.cn/nnews/3166.htm
- http://m.blog.ghtkgg.cn/nnews/9082.htm
- http://m.blog.ghtkgg.cn/nnews/031948.htm
- http://m.blog.ghtkgg.cn/nnews/140517.htm
- http://m.blog.ghtkgg.cn/nnews/1251986.htm
- http://m.blog.ghtkgg.cn/nnews/3545163.htm
- http://m.blog.ghtkgg.cn/nnews/43332.htm
- http://m.blog.ghtkgg.cn/nnews/4687540.htm
- http://m.blog.ghtkgg.cn/nnews/686679.htm
- http://m.blog.ghtkgg.cn/nnews/6646.htm
- http://m.blog.ghtkgg.cn/nnews/321452.htm
- http://m.blog.ghtkgg.cn/nnews/73811.htm
- http://m.blog.ghtkgg.cn/nnews/6790214.htm
- http://m.blog.ghtkgg.cn/nnews/23156.htm
- http://m.blog.ghtkgg.cn/nnews/4286.htm
- http://m.blog.ghtkgg.cn/nnews/7813455.htm
- http://m.blog.ghtkgg.cn/nnews/34916.htm
- http://m.blog.ghtkgg.cn/nnews/9331.htm
- http://m.blog.ghtkgg.cn/nnews/5756.htm
- http://m.blog.ghtkgg.cn/nnews/8193.htm
- http://m.blog.ghtkgg.cn/nnews/7570.htm
- http://m.blog.ghtkgg.cn/nnews/16195.htm
- http://m.blog.ghtkgg.cn/nnews/12855.htm
- http://m.blog.ghtkgg.cn/nnews/7323717.htm
- http://m.blog.ghtkgg.cn/nnews/1579.htm
- http://m.blog.ghtkgg.cn/nnews/15282.htm
- http://m.blog.ghtkgg.cn/nnews/633331.htm
- http://m.blog.ghtkgg.cn/nnews/848359.htm
- http://m.blog.ghtkgg.cn/nnews/4452230.htm
- http://m.blog.ghtkgg.cn/nnews/55377.htm
- http://m.blog.ghtkgg.cn/nnews/0086640.htm
- http://m.blog.ghtkgg.cn/nnews/37156.htm
- http://m.blog.ghtkgg.cn/nnews/542893.htm
- http://m.blog.ghtkgg.cn/nnews/2547236.htm
- http://m.blog.ghtkgg.cn/nnews/7525990.htm
- http://m.blog.ghtkgg.cn/nnews/6473.htm
- http://m.blog.ghtkgg.cn/nnews/9355201.htm
- http://m.blog.ghtkgg.cn/nnews/999042.htm
- http://m.blog.ghtkgg.cn/nnews/9844446.htm
- http://m.blog.ghtkgg.cn/nnews/314138.htm
- http://m.blog.ghtkgg.cn/nnews/5128525.htm
- http://m.blog.ghtkgg.cn/nnews/1353.htm
- http://m.blog.ghtkgg.cn/nnews/631424.htm
- http://m.blog.ghtkgg.cn/nnews/67977.htm
- http://m.blog.ghtkgg.cn/nnews/0459467.htm
- http://m.blog.ghtkgg.cn/nnews/83920.htm
- http://m.blog.ghtkgg.cn/nnews/1897.htm
- http://m.blog.ghtkgg.cn/nnews/2489273.htm
- http://m.blog.ghtkgg.cn/nnews/185614.htm
- http://m.blog.ghtkgg.cn/nnews/2534.htm
- http://m.blog.ghtkgg.cn/nnews/0281.htm
- http://m.blog.ghtkgg.cn/nnews/9405133.htm
- http://m.blog.ghtkgg.cn/nnews/261243.htm
- http://m.blog.ghtkgg.cn/nnews/38446.htm
- http://m.blog.ghtkgg.cn/nnews/4608.htm
- http://m.blog.ghtkgg.cn/nnews/9944640.htm
- http://m.blog.ghtkgg.cn/nnews/7063833.htm
- http://m.blog.ghtkgg.cn/nnews/118894.htm
- http://m.blog.ghtkgg.cn/nnews/829851.htm
- http://m.blog.ghtkgg.cn/nnews/1321102.htm
- http://m.blog.ghtkgg.cn/nnews/5083429.htm
- http://m.blog.ghtkgg.cn/nnews/492521.htm
- http://m.blog.ghtkgg.cn/nnews/6044.htm
- http://m.blog.ghtkgg.cn/nnews/0986065.htm
- http://m.blog.ghtkgg.cn/nnews/1201748.htm
- http://m.blog.ghtkgg.cn/nnews/8527.htm
- http://m.blog.ghtkgg.cn/nnews/45999.htm
- http://m.blog.ghtkgg.cn/nnews/729779.htm
- http://m.blog.ghtkgg.cn/nnews/41658.htm
- http://m.blog.ghtkgg.cn/nnews/0156712.htm
- http://m.blog.ghtkgg.cn/nnews/48019.htm
- http://m.blog.ghtkgg.cn/nnews/7397478.htm
- http://m.blog.ghtkgg.cn/nnews/479040.htm
- http://m.blog.ghtkgg.cn/nnews/1823.htm
- http://m.blog.ghtkgg.cn/nnews/0277.htm
- http://m.blog.ghtkgg.cn/nnews/8241.htm
- http://m.blog.ghtkgg.cn/nnews/277582.htm
- http://m.blog.ghtkgg.cn/nnews/670477.htm
- http://m.blog.ghtkgg.cn/nnews/200009.htm
- http://m.blog.ghtkgg.cn/nnews/7700.htm
- http://m.blog.ghtkgg.cn/nnews/4294510.htm
- http://m.blog.ghtkgg.cn/nnews/8591892.htm
- http://m.blog.ghtkgg.cn/nnews/88031.htm
- http://m.blog.ghtkgg.cn/nnews/092523.htm
- http://m.blog.ghtkgg.cn/nnews/708031.htm
- http://m.blog.ghtkgg.cn/nnews/499086.htm
- http://m.blog.ghtkgg.cn/nnews/8157884.htm
- http://m.blog.ghtkgg.cn/nnews/49317.htm
- http://m.blog.ghtkgg.cn/nnews/4234557.htm
- http://m.blog.ghtkgg.cn/nnews/970803.htm
- http://m.blog.ghtkgg.cn/nnews/62223.htm
- http://m.blog.ghtkgg.cn/nnews/8632.htm
- http://m.blog.ghtkgg.cn/nnews/7674921.htm
- http://m.blog.ghtkgg.cn/nnews/5812.htm
- http://m.blog.ghtkgg.cn/nnews/77996.htm
- http://m.blog.ghtkgg.cn/nnews/0455812.htm
- http://m.blog.ghtkgg.cn/nnews/980463.htm
- http://m.blog.ghtkgg.cn/nnews/951316.htm
- http://m.blog.ghtkgg.cn/nnews/3347515.htm
- http://m.blog.ghtkgg.cn/nnews/068973.htm
- http://m.blog.ghtkgg.cn/nnews/1045529.htm
- http://m.blog.ghtkgg.cn/nnews/062924.htm
- http://m.blog.ghtkgg.cn/nnews/819040.htm
- http://m.blog.ghtkgg.cn/nnews/4011.htm
- http://m.blog.ghtkgg.cn/nnews/688781.htm
- http://m.blog.ghtkgg.cn/nnews/86386.htm
- http://m.blog.ghtkgg.cn/nnews/2617846.htm
- http://m.blog.ghtkgg.cn/nnews/695822.htm
- http://m.blog.ghtkgg.cn/nnews/27067.htm
- http://m.blog.ghtkgg.cn/nnews/1858.htm
- http://m.blog.ghtkgg.cn/nnews/2439.htm
- http://m.blog.ghtkgg.cn/nnews/53051.htm
- http://m.blog.ghtkgg.cn/nnews/829943.htm

## 项目结构

```
navindex/
├── src/                                  # 核心源代码目录
│   ├── cli/                              # 命令行入口与参数解析模块
│   │   ├── index.ts                      # 主 CLI 调度器
│   │   └── commands/                     # 各子命令实现 (build, serve, validate)
│   ├── core/                             # 核心处理逻辑
│   │   ├── ingester/                     # URL 列表解析与规范化管道
│   │   ├── catalog/                      # 层级分类与标签引擎
│   │   └── renderer/                     # 静态 HTML 与 JSON 输出生成器
│   ├── plugins/                          # 可插拔扩展系统
│   │   ├── metadata/                     # YAML 元数据合并插件
│   │   ├── checker/                      # 链接可达性预检插件
│   │   └── exporter/                     # CSV/JSON 导出插件
│   ├── templates/                        # 输出模板与样式主题
│   │   ├── default/                      # 默认响应式布局模板
│   │   └── minimal/                      # 极简无样式模板
│   └── utils/                            # 公共工具函数与常量定义
├── tests/                                # 单元测试与集成测试套件
│   ├── unit/                             # 独立模块测试
│   └── fixtures/                         # 测试用样例数据与预期输出
├── docs/                                 # 项目文档（见文档导航章节）
├── data/                                 # 用户输入数据存放目录
│   └── batch_174_300.txt                 # 当前批次 300 条 URL 原始列表
├── dist/                                 # 构建输出目录（默认）
├── package.json                          # npm 项目配置与依赖声明
├── tsconfig.json                         # TypeScript 编译配置
├── .eslintrc.yml                         # 代码风格检查配置
└── README.md                             # 本文件
```

## 贡献指南

Fork 本仓库并创建一个功能分支，分支名称应遵循 `feature/` 或 `fix/` 前缀加简短描述的模式，例如 `feature/add-yaml-metadata-support`。所有提交必须通过 ESLint 和 TypeScript 类型检查。

在提交 Pull Request 之前，请确保所有现有单元测试通过，并为新增功能或修复编写相应的测试用例。测试覆盖率不得低于百分之八十。运行 `npm run test:coverage` 可查看当前覆盖率报告。

更新文档以反映任何用户可见的变化，包括修改命令行参数、配置文件格式或输出结构。文档变更应与代码变更在同一个 Pull Request 中提交。

提交信息应遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`chore:` 等类型前缀，并包含清晰的变更描述。对于破坏性变更，必须在提交信息中标注 `BREAKING CHANGE:`。

## 常见问题

**问：构建过程提示 "Input file not found" 错误，如何解决？**

答：请检查 `--input` 参数指定的文件路径是否正确，并确认该文件具有可读权限。如果使用相对路径，请确保从项目根目录执行命令。你也可以将输入文件放在 `data/` 目录下，然后使用 `--input ./data/your_file.txt` 格式引用。

**问：生成的静态页面中，部分链接显示为纯文本而非可点击的超链接，原因是什么？**

答：NavIndex 默认将资源列表渲染为表格，URL 列默认显示为可点击的链接。如果链接显示为纯文本，请检查输入文件中该条目是否包含非打印字符或格式异常。建议使用 `npm run validate` 命令对输入文件进行预检，该命令会报告格式错误的具体行号。

**问：如何处理包含特殊字符或中文的 URL？**

答：NavIndex 对所有 URL 字符串进行百分号编码（percent-encoding）后再写入 HTML 属性，以符合 HTML 规范。输入文件中的 URL 应当已经是有效的 URI 格式，如果包含未编码的中文字符或空格，系统会在构建时自动进行安全转义，但推荐在输入前自行完成编码以确保一致性。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
