# LinkIndex Core

LinkIndex Core 是一个面向技术团队与内容运营者的轻量级外链资源聚合与导航系统。项目定位于解决分散在不同文档、聊天记录、浏览器书签中的高价值外链难以统一管理与快速检索的问题，提供基于静态标记与分类索引的集中式链接仓库。目标用户包括开源项目维护者、技术文档工程师、运维人员以及需要长期跟踪特定领域信息源的研究者。通过将零散 URL 纳入结构化目录并辅以元信息标注，本项目能够显著降低链接丢失与重复查找的认知负担，提升团队协作中的信息共享效率。

## 功能概览

**批量链接导入与去重校验**：支持从纯文本、CSV 及 Markdown 列表中批量导入原始 URL，自动执行协议归一化与重复项检测，生成唯一内容指纹。

**层级化分类目录体系**：允许用户按技术领域、来源域名、采集批次或自定义标签建立多级分类树，每个链接可归属至多个分类节点。

**全文元数据提取与缓存**：对每条链接自动发起异步 HEAD 请求与内容摘要分析，提取页面标题、描述、关键词及最后修改时间，并将结果缓存至本地 SQLite 数据库。

**静态站点生成输出**：内置模板引擎可将链接数据与分类索引渲染为纯静态 HTML 页面，支持响应式布局与深色模式，便于通过 Nginx 或 GitHub Pages 直接托管。

**定时巡检与可用性监控**：后台调度器支持按小时或日维度对已收录链接执行可达性探测，记录响应状态码与耗时，异常结果通过日志文件告警。

**RESTful 管理接口**：提供基于 JSON 的 HTTP API，支持链接的增删改查、分类绑定与批量状态更新，便于集成至 CI/CD 或内部运维平台。

**全量数据导入导出**：支持将整个链接库导出为 JSON、YAML 或 Markdown 表格格式，也支持从上述格式恢复数据，满足备份与迁移需求。

**访问统计与热度排序**：记录每条链接的点击次数与最后访问时间，支持按 PV 或最近访问日期进行降序排列，辅助识别高频资源。

## 应用场景

**技术文档团队维护外部参考索引**：当编写系统设计文档或操作手册时，需要引用大量外部规范、论文或开源仓库。LinkIndex Core 可作为内部参考库，按主题分类存储这些 URL，并自动抓取标题与摘要，确保引用信息始终可追溯。

**运维值班日志中的故障排查链接归档**：运维人员在处理线上事故时，常会搜索到临时性的诊断工具或补丁说明。将这些链接集中录入 LinkIndex Core，并标记故障类型与日期，后续同类问题可直接查询历史索引，减少重复排查时间。

**开源项目 README 与 Wiki 的外部资源补充**：开源项目通常需要在文档中列出依赖项目、学习教程或社区论坛。通过 LinkIndex Core 管理这些外链，可以批量生成格式统一的 Markdown 列表，避免手动维护时格式混乱或链接失效。

**技术研究者的文献与博客跟踪系统**：研究人员需要长期跟踪 arXiv、学术博客、技术大会演讲视频等资源。LinkIndex Core 的定时巡检功能可以监测链接是否仍可访问，配合热度排序，帮助研究者优先关注活跃度高的信息源。

**多团队共享的链接知识库**：在跨部门协作中，前端、后端与测试团队各自积累了大量外部工具链接。LinkIndex Core 的多级分类与 API 接口可支撑构建统一的门户页面，各团队仅需维护自己的分类子树，整体形成公司级别的外部资源地图。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/linkindex/core.git linkindex-core
cd linkindex-core

# 安装项目依赖（需要 Python 3.9 及以上版本）
pip install -r requirements.txt

# 执行数据库初始化与静态站点生成
python manage.py initdb
python manage.py build --output ./dist

# 启动本地开发服务器，监听 8000 端口
python manage.py serve --host 127.0.0.1 --port 8000
```

完成上述步骤后，在浏览器中访问 http://127.0.0.1:8000 即可查看生成的链接导航页面。如需导入用户原始 URL 数据，可将链接列表保存为 urls.txt（每行一个 URL），然后执行：

```bash
python manage.py import --file urls.txt --batch 87
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 至 3.11 | 核心运行环境，3.12 及以上版本暂不支持部分异步库 |
| SQLite | 3.35.0 或更高 | 内置数据库引擎，用于存储链接元数据与分类关系 |
| pip | 21.0 或更高 | Python 包管理工具，用于安装 requirements.txt 中列出的第三方库 |
| Git | 2.25 或更高 | 用于克隆仓库及后续拉取更新 |
| 网络连接 | 出站 80/443 端口开放 | 用于首次采集链接标题与摘要，以及定时巡检外链可达性 |
| 磁盘空间 | 至少 200 MB 可用 | 用于存放数据库文件、缓存页面摘要及生成的静态页面 |
| 操作系统 | Linux、macOS、Windows WSL2 | 生产环境推荐 Debian/Ubuntu LTS 或 CentOS 7 以上 |
| 可选依赖 | Redis 6.0 或更高 | 如启用分布式任务队列或共享缓存，需额外安装并配置 Redis 服务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何快速安装、初始配置并导入第一批链接；如何理解核心概念如批次、分类与标签 |
| 配置手册 | /docs/configuration.md | 环境变量、配置文件与命令行参数详解，涵盖数据库路径、调度间隔与输出目录定制 |
| API 参考 | /docs/api-reference.md | RESTful 接口的完整端点列表、请求体格式、状态码说明及分页规则 |
| 运维部署 | /docs/deployment.md | 生产环境下的 Nginx 反向代理配置、systemd 服务单元文件、日志轮转与备份策略 |
| 数据格式 | /docs/data-format.md | 导入导出所用 JSON/YAML 的结构定义，包括链接对象、分类对象与索引映射的 Schema |
| 性能调优 | /docs/performance.md | 大规模链接库（超过 5000 条）时的数据库索引优化、异步并发数调整与缓存策略 |
| 贡献指南 | /CONTRIBUTING.md | 面向开发者的代码风格、提交规范、测试流程与 PR 评审标准（与本 README 贡献指南章节互补） |

## 资源列表

- http://m.blog.oexnr.cn/snews/277344.htm
- http://m.blog.oexnr.cn/snews/9578.htm
- http://m.blog.oexnr.cn/snews/860565.htm
- http://m.blog.oexnr.cn/snews/91258.htm
- http://m.blog.oexnr.cn/snews/7709704.htm
- http://m.blog.oexnr.cn/snews/0857.htm
- http://m.blog.oexnr.cn/snews/5618308.htm
- http://m.blog.oexnr.cn/snews/78103.htm
- http://m.blog.oexnr.cn/snews/74984.htm
- http://m.blog.oexnr.cn/snews/19141.htm
- http://m.blog.oexnr.cn/snews/8627342.htm
- http://m.blog.oexnr.cn/snews/2673934.htm
- http://m.blog.oexnr.cn/snews/3461.htm
- http://m.blog.oexnr.cn/snews/30366.htm
- http://m.blog.oexnr.cn/snews/425052.htm
- http://m.blog.oexnr.cn/snews/660277.htm
- http://m.blog.oexnr.cn/snews/110107.htm
- http://m.blog.oexnr.cn/snews/2551217.htm
- http://m.blog.oexnr.cn/snews/5084.htm
- http://m.blog.oexnr.cn/snews/8078911.htm
- http://m.blog.oexnr.cn/snews/5469.htm
- http://m.blog.oexnr.cn/snews/85783.htm
- http://m.blog.oexnr.cn/snews/62000.htm
- http://m.blog.oexnr.cn/snews/2796394.htm
- http://m.blog.oexnr.cn/snews/8128665.htm
- http://m.blog.oexnr.cn/snews/8787671.htm
- http://m.blog.oexnr.cn/snews/372496.htm
- http://m.blog.oexnr.cn/snews/81566.htm
- http://m.blog.oexnr.cn/snews/297148.htm
- http://m.blog.oexnr.cn/snews/057322.htm
- http://m.blog.oexnr.cn/snews/8123888.htm
- http://m.blog.oexnr.cn/snews/51565.htm
- http://m.blog.oexnr.cn/snews/9769.htm
- http://m.blog.oexnr.cn/snews/23458.htm
- http://m.blog.oexnr.cn/snews/1780536.htm
- http://m.blog.oexnr.cn/snews/9077.htm
- http://m.blog.oexnr.cn/snews/5602.htm
- http://m.blog.oexnr.cn/snews/250493.htm
- http://m.blog.oexnr.cn/snews/659275.htm
- http://m.blog.oexnr.cn/snews/7493716.htm
- http://m.blog.oexnr.cn/snews/8018158.htm
- http://m.blog.oexnr.cn/snews/36189.htm
- http://m.blog.oexnr.cn/snews/19999.htm
- http://m.blog.oexnr.cn/snews/11455.htm
- http://m.blog.oexnr.cn/snews/668029.htm
- http://m.blog.oexnr.cn/snews/60397.htm
- http://m.blog.oexnr.cn/snews/719908.htm
- http://m.blog.oexnr.cn/snews/0142.htm
- http://m.blog.oexnr.cn/snews/0794.htm
- http://m.blog.oexnr.cn/snews/2414770.htm
- http://m.blog.oexnr.cn/snews/509218.htm
- http://m.blog.oexnr.cn/snews/2037073.htm
- http://m.blog.oexnr.cn/snews/85769.htm
- http://m.blog.oexnr.cn/snews/8524.htm
- http://m.blog.oexnr.cn/snews/3994190.htm
- http://m.blog.oexnr.cn/snews/125007.htm
- http://m.blog.oexnr.cn/snews/3100.htm
- http://m.blog.oexnr.cn/snews/1359837.htm
- http://m.blog.oexnr.cn/snews/2151.htm
- http://m.blog.oexnr.cn/snews/07299.htm
- http://m.blog.oexnr.cn/snews/5787712.htm
- http://m.blog.oexnr.cn/snews/7110724.htm
- http://m.blog.oexnr.cn/snews/166040.htm
- http://m.blog.oexnr.cn/snews/831006.htm
- http://m.blog.oexnr.cn/snews/2834622.htm
- http://m.blog.oexnr.cn/snews/4033.htm
- http://m.blog.oexnr.cn/snews/7104.htm
- http://m.blog.oexnr.cn/snews/14751.htm
- http://m.blog.oexnr.cn/snews/2594.htm
- http://m.blog.oexnr.cn/snews/1337966.htm
- http://m.blog.oexnr.cn/snews/42060.htm
- http://m.blog.oexnr.cn/snews/1888442.htm
- http://m.blog.oexnr.cn/snews/439235.htm
- http://m.blog.oexnr.cn/snews/1403.htm
- http://m.blog.oexnr.cn/snews/1235271.htm
- http://m.blog.oexnr.cn/snews/30652.htm
- http://m.blog.oexnr.cn/snews/7296389.htm
- http://m.blog.oexnr.cn/snews/49550.htm
- http://m.blog.oexnr.cn/snews/0784744.htm
- http://m.blog.oexnr.cn/snews/300750.htm
- http://m.blog.oexnr.cn/snews/7625792.htm
- http://m.blog.oexnr.cn/snews/6076899.htm
- http://m.blog.oexnr.cn/snews/67992.htm
- http://m.blog.oexnr.cn/snews/8706.htm
- http://m.blog.oexnr.cn/snews/1066576.htm
- http://m.blog.oexnr.cn/snews/080126.htm
- http://m.blog.oexnr.cn/snews/4194597.htm
- http://m.blog.oexnr.cn/snews/721732.htm
- http://m.blog.oexnr.cn/snews/55397.htm
- http://m.blog.oexnr.cn/snews/0445313.htm
- http://m.blog.oexnr.cn/snews/01852.htm
- http://m.blog.oexnr.cn/snews/51963.htm
- http://m.blog.oexnr.cn/snews/3497007.htm
- http://m.blog.oexnr.cn/snews/3081.htm
- http://m.blog.oexnr.cn/snews/0420.htm
- http://m.blog.oexnr.cn/snews/9600043.htm
- http://m.blog.oexnr.cn/snews/453506.htm
- http://m.blog.oexnr.cn/snews/143055.htm
- http://m.blog.oexnr.cn/snews/94439.htm
- http://m.blog.oexnr.cn/snews/3365.htm
- http://m.blog.oexnr.cn/snews/49124.htm
- http://m.blog.oexnr.cn/snews/93751.htm
- http://m.blog.oexnr.cn/snews/5005149.htm
- http://m.blog.oexnr.cn/snews/888682.htm
- http://m.blog.oexnr.cn/snews/7984.htm
- http://m.blog.oexnr.cn/snews/37731.htm
- http://m.blog.oexnr.cn/snews/17453.htm
- http://m.blog.oexnr.cn/snews/66877.htm
- http://m.blog.oexnr.cn/snews/37580.htm
- http://m.blog.oexnr.cn/snews/179799.htm
- http://m.blog.oexnr.cn/snews/19477.htm
- http://m.blog.oexnr.cn/snews/0954402.htm
- http://m.blog.oexnr.cn/snews/9360.htm
- http://m.blog.oexnr.cn/snews/2564522.htm
- http://m.blog.oexnr.cn/snews/4721541.htm
- http://m.blog.oexnr.cn/snews/7571.htm
- http://m.blog.oexnr.cn/snews/4216984.htm
- http://m.blog.oexnr.cn/snews/2311740.htm
- http://m.blog.oexnr.cn/snews/0276.htm
- http://m.blog.oexnr.cn/snews/30317.htm
- http://m.blog.oexnr.cn/snews/8754919.htm
- http://m.blog.oexnr.cn/snews/2456821.htm
- http://m.blog.oexnr.cn/snews/378368.htm
- http://m.blog.oexnr.cn/snews/42107.htm
- http://m.blog.oexnr.cn/snews/3532570.htm
- http://m.blog.oexnr.cn/snews/82940.htm
- http://m.blog.oexnr.cn/snews/20313.htm
- http://m.blog.oexnr.cn/snews/32722.htm
- http://m.blog.oexnr.cn/snews/5475.htm
- http://m.blog.oexnr.cn/snews/285802.htm
- http://m.blog.oexnr.cn/snews/27402.htm
- http://m.blog.oexnr.cn/snews/5399.htm
- http://m.blog.oexnr.cn/snews/30223.htm
- http://m.blog.oexnr.cn/snews/7222.htm
- http://m.blog.oexnr.cn/snews/18746.htm
- http://m.blog.oexnr.cn/snews/074311.htm
- http://m.blog.oexnr.cn/snews/43324.htm
- http://m.blog.oexnr.cn/snews/06797.htm
- http://m.blog.oexnr.cn/snews/045985.htm
- http://m.blog.oexnr.cn/snews/07103.htm
- http://m.blog.oexnr.cn/snews/77279.htm
- http://m.blog.oexnr.cn/snews/452100.htm
- http://m.blog.oexnr.cn/snews/5203027.htm
- http://m.blog.oexnr.cn/snews/1681.htm
- http://m.blog.oexnr.cn/snews/03508.htm
- http://m.blog.oexnr.cn/snews/8431760.htm
- http://m.blog.oexnr.cn/snews/823287.htm
- http://m.blog.oexnr.cn/snews/5434.htm
- http://m.blog.oexnr.cn/snews/19417.htm
- http://m.blog.oexnr.cn/snews/122856.htm
- http://m.blog.oexnr.cn/snews/26876.htm
- http://m.blog.oexnr.cn/snews/58872.htm
- http://m.blog.oexnr.cn/snews/4045715.htm
- http://m.blog.oexnr.cn/snews/4032.htm
- http://m.blog.oexnr.cn/snews/116357.htm
- http://m.blog.oexnr.cn/snews/4728368.htm
- http://m.blog.oexnr.cn/snews/68307.htm
- http://m.blog.oexnr.cn/snews/255878.htm
- http://m.blog.oexnr.cn/snews/8762.htm
- http://m.blog.oexnr.cn/snews/25491.htm
- http://m.blog.oexnr.cn/snews/785813.htm
- http://m.blog.oexnr.cn/snews/83291.htm
- http://m.blog.oexnr.cn/snews/517905.htm
- http://m.blog.oexnr.cn/snews/6451626.htm
- http://m.blog.oexnr.cn/snews/498001.htm
- http://m.blog.oexnr.cn/snews/3468903.htm
- http://m.blog.oexnr.cn/snews/487585.htm
- http://m.blog.oexnr.cn/snews/997597.htm
- http://m.blog.oexnr.cn/snews/4120317.htm
- http://m.blog.oexnr.cn/snews/7033425.htm
- http://m.blog.oexnr.cn/snews/3496.htm
- http://m.blog.oexnr.cn/snews/32312.htm
- http://m.blog.oexnr.cn/snews/998774.htm
- http://m.blog.oexnr.cn/snews/61474.htm
- http://m.blog.oexnr.cn/snews/5114.htm
- http://m.blog.oexnr.cn/snews/6341337.htm
- http://m.blog.oexnr.cn/snews/56670.htm
- http://m.blog.oexnr.cn/snews/0078.htm
- http://m.blog.oexnr.cn/snews/1967.htm
- http://m.blog.oexnr.cn/snews/1909819.htm
- http://m.blog.oexnr.cn/snews/8136.htm
- http://m.blog.oexnr.cn/snews/20332.htm
- http://m.blog.oexnr.cn/snews/75034.htm
- http://m.blog.oexnr.cn/snews/5933.htm
- http://m.blog.oexnr.cn/snews/12795.htm
- http://m.blog.oexnr.cn/snews/1588569.htm
- http://m.blog.oexnr.cn/snews/87242.htm
- http://m.blog.oexnr.cn/snews/285119.htm
- http://m.blog.oexnr.cn/snews/51076.htm
- http://m.blog.oexnr.cn/snews/989909.htm
- http://m.blog.oexnr.cn/snews/5442.htm
- http://m.blog.oexnr.cn/snews/458400.htm
- http://m.blog.oexnr.cn/snews/821710.htm
- http://m.blog.oexnr.cn/snews/93200.htm
- http://m.blog.oexnr.cn/snews/2430329.htm
- http://m.blog.oexnr.cn/snews/91519.htm
- http://m.blog.oexnr.cn/snews/62491.htm
- http://m.blog.oexnr.cn/snews/8430.htm
- http://m.blog.oexnr.cn/snews/025968.htm
- http://m.blog.oexnr.cn/snews/60068.htm
- http://m.blog.oexnr.cn/snews/4988.htm
- http://m.blog.oexnr.cn/snews/1609.htm
- http://m.blog.oexnr.cn/snews/8023570.htm
- http://m.blog.oexnr.cn/snews/45280.htm
- http://m.blog.oexnr.cn/snews/9786.htm
- http://m.blog.oexnr.cn/snews/41610.htm
- http://m.blog.oexnr.cn/snews/36729.htm
- http://m.blog.oexnr.cn/snews/4120339.htm
- http://m.blog.oexnr.cn/snews/91398.htm
- http://m.blog.oexnr.cn/snews/249455.htm
- http://m.blog.oexnr.cn/snews/91685.htm
- http://m.blog.oexnr.cn/snews/2922635.htm
- http://m.blog.oexnr.cn/snews/2821.htm
- http://m.blog.oexnr.cn/snews/7627384.htm
- http://m.blog.oexnr.cn/snews/7137548.htm
- http://m.blog.oexnr.cn/snews/700835.htm
- http://m.blog.oexnr.cn/snews/8153.htm
- http://m.blog.oexnr.cn/snews/4095.htm
- http://m.blog.oexnr.cn/snews/418664.htm
- http://m.blog.oexnr.cn/snews/3961017.htm
- http://m.blog.oexnr.cn/snews/5367.htm
- http://m.blog.oexnr.cn/snews/6776712.htm
- http://m.blog.oexnr.cn/snews/1116.htm
- http://m.blog.oexnr.cn/snews/5893419.htm
- http://m.blog.oexnr.cn/snews/7646606.htm
- http://m.blog.oexnr.cn/snews/8016009.htm
- http://m.blog.oexnr.cn/snews/574867.htm
- http://m.blog.oexnr.cn/snews/438802.htm
- http://m.blog.oexnr.cn/snews/2560.htm
- http://m.blog.oexnr.cn/snews/5583603.htm
- http://m.blog.oexnr.cn/snews/8403.htm
- http://m.blog.oexnr.cn/snews/4083.htm
- http://m.blog.oexnr.cn/snews/8620.htm
- http://m.blog.oexnr.cn/snews/891822.htm
- http://m.blog.oexnr.cn/snews/8812.htm
- http://m.blog.oexnr.cn/snews/851537.htm
- http://m.blog.oexnr.cn/snews/4457.htm
- http://m.blog.oexnr.cn/snews/5968.htm
- http://m.blog.oexnr.cn/snews/48284.htm
- http://m.blog.oexnr.cn/snews/46276.htm
- http://m.blog.oexnr.cn/snews/16384.htm
- http://m.blog.oexnr.cn/snews/0065.htm
- http://m.blog.oexnr.cn/snews/9434.htm
- http://m.blog.oexnr.cn/snews/869685.htm
- http://m.blog.oexnr.cn/snews/6618756.htm
- http://m.blog.oexnr.cn/snews/0485.htm
- http://m.blog.oexnr.cn/snews/103084.htm
- http://m.blog.oexnr.cn/snews/57494.htm
- http://m.blog.oexnr.cn/snews/6691675.htm
- http://m.blog.oexnr.cn/snews/5213.htm
- http://m.blog.oexnr.cn/snews/8235.htm
- http://m.blog.oexnr.cn/snews/4768.htm
- http://m.blog.oexnr.cn/snews/740974.htm
- http://m.blog.oexnr.cn/snews/1928623.htm
- http://m.blog.oexnr.cn/snews/46098.htm
- http://m.blog.oexnr.cn/snews/554757.htm
- http://m.blog.oexnr.cn/snews/1064577.htm
- http://m.blog.oexnr.cn/snews/13360.htm
- http://m.blog.oexnr.cn/snews/686475.htm
- http://m.blog.oexnr.cn/snews/9016464.htm
- http://m.blog.oexnr.cn/snews/8607.htm
- http://m.blog.oexnr.cn/snews/73826.htm
- http://m.blog.oexnr.cn/snews/539438.htm
- http://m.blog.oexnr.cn/snews/102183.htm
- http://m.blog.oexnr.cn/snews/44298.htm
- http://m.blog.oexnr.cn/snews/64583.htm
- http://m.blog.oexnr.cn/snews/53373.htm
- http://m.blog.oexnr.cn/snews/1816.htm
- http://m.blog.oexnr.cn/snews/9751912.htm
- http://m.blog.oexnr.cn/snews/96206.htm
- http://m.blog.oexnr.cn/snews/3663416.htm
- http://m.blog.oexnr.cn/snews/70512.htm
- http://m.blog.oexnr.cn/snews/62205.htm
- http://m.blog.oexnr.cn/snews/180838.htm
- http://m.blog.oexnr.cn/snews/027149.htm
- http://m.blog.oexnr.cn/snews/96942.htm
- http://m.blog.oexnr.cn/snews/57046.htm
- http://m.blog.oexnr.cn/snews/627113.htm
- http://m.blog.oexnr.cn/snews/8307.htm
- http://m.blog.oexnr.cn/snews/64237.htm
- http://m.blog.oexnr.cn/snews/3917.htm
- http://m.blog.oexnr.cn/snews/9875961.htm
- http://m.blog.oexnr.cn/snews/924217.htm
- http://m.blog.oexnr.cn/snews/88516.htm
- http://m.blog.oexnr.cn/snews/74640.htm
- http://m.blog.oexnr.cn/snews/538442.htm
- http://m.blog.oexnr.cn/snews/0168246.htm
- http://m.blog.oexnr.cn/snews/1817.htm
- http://m.blog.oexnr.cn/snews/74584.htm
- http://m.blog.oexnr.cn/snews/966857.htm
- http://m.blog.oexnr.cn/snews/894075.htm
- http://m.blog.oexnr.cn/snews/5744477.htm
- http://m.blog.oexnr.cn/snews/3926.htm
- http://m.blog.oexnr.cn/snews/54365.htm
- http://m.blog.oexnr.cn/snews/4655019.htm
- http://m.blog.oexnr.cn/snews/633106.htm
- http://m.blog.oexnr.cn/snews/63749.htm
- http://m.blog.oexnr.cn/snews/1137.htm
- http://m.blog.oexnr.cn/snews/12669.htm
- http://m.blog.oexnr.cn/snews/3167.htm

## 项目结构

```
linkindex-core/
├── manage.py                 # 命令行入口，聚合 initdb / import / build / serve 等子命令
├── requirements.txt          # Python 依赖声明，包含 aiohttp、jinja2、click、sqlalchemy 等
├── .env.example              # 环境变量模板，用于配置数据库路径、日志级别与监控开关
├── linkindex/
│   ├── __init__.py           # 包初始化，定义版本号与公开接口
│   ├── app.py                # 核心应用工厂，注册路由、中间件与异常处理器
│   ├── config.py             # 配置加载逻辑，支持从环境变量、.env 与 YAML 文件读取
│   ├── models/               # 数据模型层
│   │   ├── base.py           # SQLAlchemy 基类与数据库会话管理
│   │   ├── link.py           # Link 表定义：url、title、fingerprint、status_code、last_checked
│   │   ├── category.py       # Category 表定义：name、slug、parent_id、sort_order
│   │   └── tag.py            # Tag 表与 link_tag 关联表，支持多对多标签体系
│   ├── services/             # 业务逻辑服务层
│   │   ├── fetcher.py        # 异步 HTTP 抓取器，含超时重试与 User-Agent 轮换
│   │   ├── parser.py         # HTML 元数据解析，提取 title、meta description 与 keywords
│   │   ├── dedup.py          # 基于 url 归一化与 sha256 内容的去重引擎
│   │   └── monitor.py        # 定时巡检调度器，基于 apscheduler 实现，记录可用性趋势
│   ├── api/                  # RESTful API 路由层
│   │   ├── v1/
│   │   │   ├── links.py      # /api/v1/links 的 GET/POST/PUT/DELETE 实现
│   │   │   ├── categories.py # /api/v1/categories 的树形查询与批量更新
│   │   │   └── stats.py      # /api/v1/stats 提供汇总计数与热度排行
│   ├── static/               # 前端静态资源（CSS、JavaScript、图标）
│   │   ├── css/              # 基于 Tailwind 的响应式样式，支持亮色/暗色主题切换
│   │   └── js/               # 交互脚本：侧边栏折叠、搜索即时过滤、链接点击埋点
│   ├── templates/            # Jinja2 模板目录
│   │   ├── base.html         # 基础布局模板，包含导航栏与全局 footer
│   │   ├── index.html        # 首页展示分类树与最新添加的 20 条链接
│   │   ├── category.html     # 单个分类详情页，展示该分类下所有链接分页列表
│   │   └── detail.html       # 单条链接详情页，展示完整元数据与访问统计
│   ├── utils/                # 通用工具函数
│   │   ├── logger.py         # 日志配置，按日期轮转，支持 JSON 格式输出
│   │   ├── validators.py     # URL 校验、域名黑名单检查、协议白名单过滤
│   │   └── exporters.py      # JSON/YAML/Markdown 导出器，支持流式写入大文件
│   ├── cli/                  # 命令行子命令实现
│   │   ├── initdb.py         # 初始化数据库表与创建默认分类（如“未分类”“第87批”）
│   │   ├── import.py         # 批量导入逻辑，支持--file、--batch、--category 参数
│   │   ├── build.py          # 静态站点生成器，将模板渲染至 --output 目录
│   │   └── serve.py          # 基于 uvicorn 的开发服务器启动器
│   └── migrations/           # Alembic 数据库迁移脚本
│       ├── versions/         # 按时间戳命名的迁移文件，记录表结构变更历史
│       └── alembic.ini       # Alembic 配置文件，指向 SQLite 数据库路径
├── tests/                    # 单元测试与集成测试目录
│   ├── conftest.py           # pytest 固定装置，包含测试数据库与模拟 HTTP 响应
│   ├── test_models.py        # Link 与 Category 模型的增删改查测试
│   ├── test_fetcher.py       # 异步抓取器的超时重试与异常处理测试
│   └── test_api.py           # API 端点状态码与响应结构验证测试
├── docs/                     # 详细文档源文件（参见上文文档导航）
│   ├── getting-started.md
│   ├── configuration.md
│   ├── api-reference.md
│   └── deployment.md
├── scripts/                  # 运维辅助脚本
│   ├── backup.sh             # 数据库与配置文件打包备份脚本
│   └── healthcheck.py        # 用于监控系统可用性的外部探测脚本
└── dist/                     # 静态站点默认输出目录（由 build 命令生成，不纳入版本控制）
    ├── index.html
    ├── categories/
    └── links/
```

## 贡献指南

1. 阅读项目行为准则与贡献者许可协议，确认遵守开源社区协作规范。所有贡献者需在首次提交 PR 时签署 CLA。

2. 在 GitHub Issues 中查找标记为 help-wanted 或 good-first-issue 的任务，或提交新 Issue 描述你发现的缺陷或希望新增的功能，等待维护者确认后再开始编码。

3. 从 develop 分支创建特性分支，分支命名遵循 feature/描述性名称 或 fix/问题编号 格式。确保本地通过所有单元测试与 lint 检查（使用 flake8 与 mypy）。

4. 提交代码时遵循常规提交规范，使用 feat、fix、docs、refactor、perf 等前缀，并附上简短的变更说明。提交信息需使用英文，但注释与文档可使用中文。

5. 发起 Pull Request 至 develop 分支，PR 描述中需说明变更动机、实现方式以及是否包含破坏性变动。至少两位维护者审核通过后，由核心提交者合并至 main 分支并打 tag 发布。

## 常见问题

**问：导入大量 URL 时出现超时或卡顿，应如何优化？**

答：导入性能主要受网络抓取阶段影响。建议先使用 --no-fetch 选项仅入库 URL 而不抓取元数据，完成导入后再通过 monitor 命令手动触发批量更新。此外，可将并发数调低至 10 以内，避免触发目标站点的反爬策略。对于超过 1000 条的批次，推荐拆分文件分次导入。

**问：生成的静态页面中链接标题显示为原始 URL，未能正确抓取页面标题，是什么原因？**

答：目标站点可能屏蔽了无用户代理或特定来源的请求。可在配置文件中修改抓取器的 User-Agent 为常见浏览器字符串，并启用 cookie 持久化。部分站点需要 JavaScript 渲染才能生成标题，此类页面当前版本无法支持，建议通过编辑链接元数据接口手动补充标题字段。

**问：如何将本系统迁移至另一台服务器，包括所有分类与自定义标签？**

答：执行 manage.py export --format json --output full_backup.json 即可导出完整数据。在目标服务器上完成安装后，执行 manage.py import --file full_backup.json --mode replace 即可恢复全部数据。注意替换模式会清空目标数据库现有内容，请提前备份。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
