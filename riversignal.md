# WebJunction News Archive Gateway

WebJunction News Archive Gateway 是一个面向内容聚合与历史新闻资源检索的开源网关工具，专为需要系统化访问、备份和重分发移动端新闻页面（基于 oexnr.cn 域名下的 jnews 目录资源）的研究者、数据分析师与内容归档开发者设计。该项目的核心目标是将散落在大量无规律数字编号 URL 下的新闻条目，通过本地索引、元数据提取和结构化输出，转化为可被脚本、爬虫或静态站点生成器二次处理的标准化数据源。

本项目并不重新托管任何新闻内容，而是提供一个透明、可审计的访问路由与元数据映射层，帮助用户在高频访问、批量下载或内容解析时维持稳定的本地缓存与请求调度。适用于新闻站点镜像、舆情分析预处理、历史页面结构演变追踪等场景。项目本身采用 MIT 许可证，鼓励社区贡献解析插件与输出格式扩展。

## 功能概览

**基于模式的 URL 路由映射**：根据 oexnr.cn 域名下 jnews 路径的数字 ID 模式，提供可配置的请求重写与本地缓存键生成规则，避免重复网络请求。

**增量元数据抽取管道**：内置轻量级 HTML 解析器，可从每个新闻页面抽取标题、发布时间、正文段落首句、图片 alt 文本等核心字段，输出为 JSON Lines 格式。

**批量任务调度器**：支持从文本文件或标准输入读取 URL 列表，自动控制并发请求数（默认 5 并发）、重试机制（指数退避）与超时设置，适合大规模回访任务。

**多格式导出适配器**：原生支持输出为 CSV、JSON、SQLite 数据库表以及 Markdown 索引文件，便于接入数据分析工具（如 Pandas、Elasticsearch）或静态站点生成器。

**本地缓存与快照管理**：对每个成功请求的页面内容进行压缩存储，并提供基于时间戳的快照标记，允许用户回退到特定日期的页面状态。

**可插拔的验证器钩子**：允许用户定义自定义校验函数（如检查页面是否包含特定关键词、响应状态码是否符合预期），用于过滤无效或重定向条目。

**资源健康度看板**：提供简单的命令行统计输出，显示总 URL 数、成功/失败/重试次数、平均响应时间，辅助用户评估数据源可用性。

## 应用场景

**历史新闻数据集的构建与清洗**：研究人员可将本工具作为前置处理器，对指定批次（如第 46/300 批）的 URL 进行自动化访问和元数据抽取，生成结构化的研究数据集，用于趋势分析或自然语言处理训练。

**个人知识库的新闻链接永久化备份**：内容创作者或信息收集者可使用本工具定期抓取关注的新闻条目，生成带本地快照的 Markdown 索引文件，避免源链接失效导致的信息丢失。

**新闻页面改版监控与对比**：通过定期运行本工具并保存页面快照，开发人员或产品经理可以对比同一 URL 在不同时间点的页面结构差异，辅助前端兼容性测试或内容变更追踪。

**轻量级舆情聚合原型验证**：数据分析师可利用本工具快速搭建一个小型爬虫原型，从分散的新闻编号中提取标题和发布时间，为后续的舆情分析仪表板提供数据接入层。

## 快速开始

以下步骤帮助您在 5 分钟内启动项目并运行一次基本的 URL 列表处理任务。

```bash
# 克隆项目仓库
git clone https://github.com/webjunction/webjunction-archive-gateway.git
cd webjunction-archive-gateway

# 安装 Python 虚拟环境与依赖
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install --upgrade pip
pip install -r requirements.txt

# 准备一个包含待处理 URL 的文本文件，每行一个 URL
# 此处使用 example_urls.txt 作为示例，您可以直接替换为真实 URL 列表
echo "http://m.wap.oexnr.cn/jnews/4797.htm" > example_urls.txt
echo "http://m.wap.oexnr.cn/jnews/980577.htm" >> example_urls.txt

# 运行单次处理任务（输出 JSON 到控制台）
python gateway.py process --input example_urls.txt --output result.json --format json

# 若需启用本地缓存，添加 --cache 参数
python gateway.py process --input example_urls.txt --output result_with_cache.json --format json --cache
```

## 安装要求

项目基于 Python 3.9+ 开发，依赖主流开源库，以下为完整的运行环境与依赖说明。

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.10 或 3.11 以获得最佳性能 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于发送 GET 请求并处理响应 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 内容解析，用于从新闻页面中提取元数据 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析器后端，提供更快的解析速度 |
| pandas | 1.5.0 及以上 | 仅当使用 CSV 或 Excel 导出格式时需要，用于数据帧转换 |
| sqlite3 | 内置于 Python 标准库 | 用于 SQLite 导出功能，无需额外安装 |
| jsonschema | 4.17.0 及以上 | 用于验证元数据输出格式是否符合 JSON Schema 定义 |
| pytest | 7.2.0 及以上 | 仅开发测试时需要，用于运行单元测试与集成测试 |
| click | 8.1.0 及以上 | 命令行界面框架，用于解析子命令与参数 |
| python-dotenv | 1.0.0 及以上 | 用于加载 .env 配置文件中的环境变量（如超时、重试次数） |
| tqdm | 4.64.0 及以上 | 用于在批量处理时显示进度条，提升用户交互体验 |

## 文档导航

项目文档按照使用者角色与关注点进行分层组织，下表列出各文档的定位与核心内容。

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/quickstart.md | 如何安装、配置并运行第一次处理任务？基本参数有哪些？ |
| 用户手册 | docs/user/configuration.md | 如何通过环境变量或配置文件调整并发数、重试策略、缓存路径？ |
| 用户手册 | docs/user/output_formats.md | 各导出格式（JSON、CSV、SQLite、Markdown）的字段映射与使用场景是什么？ |
| 开发指南 | docs/development/architecture.md | 项目的模块划分、数据流走向、核心类图与扩展点设计 |
| 开发指南 | docs/development/writing_plugins.md | 如何编写自定义的元数据抽取插件或响应验证器？ |
| 开发指南 | docs/development/testing.md | 如何运行单元测试、编写新的测试用例以及使用 Mock 数据 |
| 运维参考 | docs/operations/deployment.md | 如何在服务器上长期运行批量任务、日志轮转与监控建议 |
| 运维参考 | docs/operations/troubleshooting.md | 常见错误码含义、网络超时处理、缓存损坏恢复方法 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/4797.htm
- http://m.wap.oexnr.cn/jnews/980577.htm
- http://m.wap.oexnr.cn/jnews/3393908.htm
- http://m.wap.oexnr.cn/jnews/2014299.htm
- http://m.wap.oexnr.cn/jnews/570626.htm
- http://m.wap.oexnr.cn/jnews/819212.htm
- http://m.wap.oexnr.cn/jnews/36960.htm
- http://m.wap.oexnr.cn/jnews/2478791.htm
- http://m.wap.oexnr.cn/jnews/6978.htm
- http://m.wap.oexnr.cn/jnews/3142427.htm
- http://m.wap.oexnr.cn/jnews/0095.htm
- http://m.wap.oexnr.cn/jnews/76786.htm
- http://m.wap.oexnr.cn/jnews/360451.htm
- http://m.wap.oexnr.cn/jnews/2249485.htm
- http://m.wap.oexnr.cn/jnews/52766.htm
- http://m.wap.oexnr.cn/jnews/88840.htm
- http://m.wap.oexnr.cn/jnews/1888835.htm
- http://m.wap.oexnr.cn/jnews/26643.htm
- http://m.wap.oexnr.cn/jnews/8763623.htm
- http://m.wap.oexnr.cn/jnews/46094.htm
- http://m.wap.oexnr.cn/jnews/9643369.htm
- http://m.wap.oexnr.cn/jnews/412976.htm
- http://m.wap.oexnr.cn/jnews/8542.htm
- http://m.wap.oexnr.cn/jnews/51245.htm
- http://m.wap.oexnr.cn/jnews/15504.htm
- http://m.wap.oexnr.cn/jnews/482648.htm
- http://m.wap.oexnr.cn/jnews/74693.htm
- http://m.wap.oexnr.cn/jnews/1582262.htm
- http://m.wap.oexnr.cn/jnews/1632.htm
- http://m.wap.oexnr.cn/jnews/7859021.htm
- http://m.wap.oexnr.cn/jnews/093900.htm
- http://m.wap.oexnr.cn/jnews/378066.htm
- http://m.wap.oexnr.cn/jnews/576702.htm
- http://m.wap.oexnr.cn/jnews/3707.htm
- http://m.wap.oexnr.cn/jnews/6961590.htm
- http://m.wap.oexnr.cn/jnews/87630.htm
- http://m.wap.oexnr.cn/jnews/52056.htm
- http://m.wap.oexnr.cn/jnews/62568.htm
- http://m.wap.oexnr.cn/jnews/671662.htm
- http://m.wap.oexnr.cn/jnews/22601.htm
- http://m.wap.oexnr.cn/jnews/2534.htm
- http://m.wap.oexnr.cn/jnews/3332713.htm
- http://m.wap.oexnr.cn/jnews/117554.htm
- http://m.wap.oexnr.cn/jnews/95094.htm
- http://m.wap.oexnr.cn/jnews/95381.htm
- http://m.wap.oexnr.cn/jnews/49283.htm
- http://m.wap.oexnr.cn/jnews/0790495.htm
- http://m.wap.oexnr.cn/jnews/2994068.htm
- http://m.wap.oexnr.cn/jnews/81616.htm
- http://m.wap.oexnr.cn/jnews/634377.htm
- http://m.wap.oexnr.cn/jnews/8106712.htm
- http://m.wap.oexnr.cn/jnews/95566.htm
- http://m.wap.oexnr.cn/jnews/8153.htm
- http://m.wap.oexnr.cn/jnews/96571.htm
- http://m.wap.oexnr.cn/jnews/7284595.htm
- http://m.wap.oexnr.cn/jnews/2973.htm
- http://m.wap.oexnr.cn/jnews/15027.htm
- http://m.wap.oexnr.cn/jnews/2206.htm
- http://m.wap.oexnr.cn/jnews/768131.htm
- http://m.wap.oexnr.cn/jnews/990494.htm
- http://m.wap.oexnr.cn/jnews/3317.htm
- http://m.wap.oexnr.cn/jnews/4040077.htm
- http://m.wap.oexnr.cn/jnews/1491791.htm
- http://m.wap.oexnr.cn/jnews/033197.htm
- http://m.wap.oexnr.cn/jnews/70610.htm
- http://m.wap.oexnr.cn/jnews/008908.htm
- http://m.wap.oexnr.cn/jnews/062020.htm
- http://m.wap.oexnr.cn/jnews/176505.htm
- http://m.wap.oexnr.cn/jnews/14503.htm
- http://m.wap.oexnr.cn/jnews/22022.htm
- http://m.wap.oexnr.cn/jnews/4625079.htm
- http://m.wap.oexnr.cn/jnews/40042.htm
- http://m.wap.oexnr.cn/jnews/554876.htm
- http://m.wap.oexnr.cn/jnews/193251.htm
- http://m.wap.oexnr.cn/jnews/684728.htm
- http://m.wap.oexnr.cn/jnews/56855.htm
- http://m.wap.oexnr.cn/jnews/576579.htm
- http://m.wap.oexnr.cn/jnews/9521133.htm
- http://m.wap.oexnr.cn/jnews/885795.htm
- http://m.wap.oexnr.cn/jnews/0854229.htm
- http://m.wap.oexnr.cn/jnews/0039119.htm
- http://m.wap.oexnr.cn/jnews/72401.htm
- http://m.wap.oexnr.cn/jnews/9751990.htm
- http://m.wap.oexnr.cn/jnews/0267.htm
- http://m.wap.oexnr.cn/jnews/331030.htm
- http://m.wap.oexnr.cn/jnews/525241.htm
- http://m.wap.oexnr.cn/jnews/7646.htm
- http://m.wap.oexnr.cn/jnews/8775910.htm
- http://m.wap.oexnr.cn/jnews/9690.htm
- http://m.wap.oexnr.cn/jnews/71511.htm
- http://m.wap.oexnr.cn/jnews/73905.htm
- http://m.wap.oexnr.cn/jnews/6231901.htm
- http://m.wap.oexnr.cn/jnews/52937.htm
- http://m.wap.oexnr.cn/jnews/933736.htm
- http://m.wap.oexnr.cn/jnews/5474118.htm
- http://m.wap.oexnr.cn/jnews/243624.htm
- http://m.wap.oexnr.cn/jnews/9952.htm
- http://m.wap.oexnr.cn/jnews/91487.htm
- http://m.wap.oexnr.cn/jnews/1503659.htm
- http://m.wap.oexnr.cn/jnews/596508.htm
- http://m.wap.oexnr.cn/jnews/629475.htm
- http://m.wap.oexnr.cn/jnews/6553.htm
- http://m.wap.oexnr.cn/jnews/0721589.htm
- http://m.wap.oexnr.cn/jnews/38737.htm
- http://m.wap.oexnr.cn/jnews/41796.htm
- http://m.wap.oexnr.cn/jnews/542081.htm
- http://m.wap.oexnr.cn/jnews/4595.htm
- http://m.wap.oexnr.cn/jnews/39950.htm
- http://m.wap.oexnr.cn/jnews/0098.htm
- http://m.wap.oexnr.cn/jnews/0444347.htm
- http://m.wap.oexnr.cn/jnews/1566.htm
- http://m.wap.oexnr.cn/jnews/9198749.htm
- http://m.wap.oexnr.cn/jnews/5837573.htm
- http://m.wap.oexnr.cn/jnews/902612.htm
- http://m.wap.oexnr.cn/jnews/7988.htm
- http://m.wap.oexnr.cn/jnews/5547.htm
- http://m.wap.oexnr.cn/jnews/77491.htm
- http://m.wap.oexnr.cn/jnews/75008.htm
- http://m.wap.oexnr.cn/jnews/6268312.htm
- http://m.wap.oexnr.cn/jnews/0208058.htm
- http://m.wap.oexnr.cn/jnews/0932031.htm
- http://m.wap.oexnr.cn/jnews/4638.htm
- http://m.wap.oexnr.cn/jnews/36454.htm
- http://m.wap.oexnr.cn/jnews/46101.htm
- http://m.wap.oexnr.cn/jnews/0827984.htm
- http://m.wap.oexnr.cn/jnews/07356.htm
- http://m.wap.oexnr.cn/jnews/17847.htm
- http://m.wap.oexnr.cn/jnews/1006384.htm
- http://m.wap.oexnr.cn/jnews/2601.htm
- http://m.wap.oexnr.cn/jnews/72261.htm
- http://m.wap.oexnr.cn/jnews/815703.htm
- http://m.wap.oexnr.cn/jnews/82573.htm
- http://m.wap.oexnr.cn/jnews/1461048.htm
- http://m.wap.oexnr.cn/jnews/36552.htm
- http://m.wap.oexnr.cn/jnews/660997.htm
- http://m.wap.oexnr.cn/jnews/632781.htm
- http://m.wap.oexnr.cn/jnews/7220.htm
- http://m.wap.oexnr.cn/jnews/0716803.htm
- http://m.wap.oexnr.cn/jnews/703914.htm
- http://m.wap.oexnr.cn/jnews/43909.htm
- http://m.wap.oexnr.cn/jnews/85827.htm
- http://m.wap.oexnr.cn/jnews/8296.htm
- http://m.wap.oexnr.cn/jnews/01860.htm
- http://m.wap.oexnr.cn/jnews/4065539.htm
- http://m.wap.oexnr.cn/jnews/445308.htm
- http://m.wap.oexnr.cn/jnews/93335.htm
- http://m.wap.oexnr.cn/jnews/49031.htm
- http://m.wap.oexnr.cn/jnews/014912.htm
- http://m.wap.oexnr.cn/jnews/337055.htm
- http://m.wap.oexnr.cn/jnews/8614518.htm
- http://m.wap.oexnr.cn/jnews/3556.htm
- http://m.wap.oexnr.cn/jnews/6149567.htm
- http://m.wap.oexnr.cn/jnews/05356.htm
- http://m.wap.oexnr.cn/jnews/8062682.htm
- http://m.wap.oexnr.cn/jnews/557935.htm
- http://m.wap.oexnr.cn/jnews/4003.htm
- http://m.wap.oexnr.cn/jnews/74972.htm
- http://m.wap.oexnr.cn/jnews/9917.htm
- http://m.wap.oexnr.cn/jnews/8618.htm
- http://m.wap.oexnr.cn/jnews/8422.htm
- http://m.wap.oexnr.cn/jnews/0032.htm
- http://m.wap.oexnr.cn/jnews/01603.htm
- http://m.wap.oexnr.cn/jnews/4175538.htm
- http://m.wap.oexnr.cn/jnews/713348.htm
- http://m.wap.oexnr.cn/jnews/449246.htm
- http://m.wap.oexnr.cn/jnews/02694.htm
- http://m.wap.oexnr.cn/jnews/89540.htm
- http://m.wap.oexnr.cn/jnews/8770.htm
- http://m.wap.oexnr.cn/jnews/3904.htm
- http://m.wap.oexnr.cn/jnews/213684.htm
- http://m.wap.oexnr.cn/jnews/8410.htm
- http://m.wap.oexnr.cn/jnews/161582.htm
- http://m.wap.oexnr.cn/jnews/0751.htm
- http://m.wap.oexnr.cn/jnews/0005381.htm
- http://m.wap.oexnr.cn/jnews/8753.htm
- http://m.wap.oexnr.cn/jnews/12191.htm
- http://m.wap.oexnr.cn/jnews/5355586.htm
- http://m.wap.oexnr.cn/jnews/871404.htm
- http://m.wap.oexnr.cn/jnews/49987.htm
- http://m.wap.oexnr.cn/jnews/6370.htm
- http://m.wap.oexnr.cn/jnews/5909328.htm
- http://m.wap.oexnr.cn/jnews/9067.htm
- http://m.wap.oexnr.cn/jnews/219602.htm
- http://m.wap.oexnr.cn/jnews/1943922.htm
- http://m.wap.oexnr.cn/jnews/785096.htm
- http://m.wap.oexnr.cn/jnews/2090.htm
- http://m.wap.oexnr.cn/jnews/2597129.htm
- http://m.wap.oexnr.cn/jnews/108293.htm
- http://m.wap.oexnr.cn/jnews/0714.htm
- http://m.wap.oexnr.cn/jnews/7159.htm
- http://m.wap.oexnr.cn/jnews/058433.htm
- http://m.wap.oexnr.cn/jnews/2907351.htm
- http://m.wap.oexnr.cn/jnews/719399.htm
- http://m.wap.oexnr.cn/jnews/6566460.htm
- http://m.wap.oexnr.cn/jnews/777761.htm
- http://m.wap.oexnr.cn/jnews/65555.htm
- http://m.wap.oexnr.cn/jnews/8891.htm
- http://m.wap.oexnr.cn/jnews/926759.htm
- http://m.wap.oexnr.cn/jnews/3068754.htm
- http://m.wap.oexnr.cn/jnews/8250.htm
- http://m.wap.oexnr.cn/jnews/7486372.htm
- http://m.wap.oexnr.cn/jnews/40044.htm
- http://m.wap.oexnr.cn/jnews/62901.htm
- http://m.wap.oexnr.cn/jnews/04341.htm
- http://m.wap.oexnr.cn/jnews/2737626.htm
- http://m.wap.oexnr.cn/jnews/07511.htm
- http://m.wap.oexnr.cn/jnews/76573.htm
- http://m.wap.oexnr.cn/jnews/76745.htm
- http://m.wap.oexnr.cn/jnews/7511.htm
- http://m.wap.oexnr.cn/jnews/9735.htm
- http://m.wap.oexnr.cn/jnews/008377.htm
- http://m.wap.oexnr.cn/jnews/9766531.htm
- http://m.wap.oexnr.cn/jnews/723295.htm
- http://m.wap.oexnr.cn/jnews/2171.htm
- http://m.wap.oexnr.cn/jnews/247572.htm
- http://m.wap.oexnr.cn/jnews/59918.htm
- http://m.wap.oexnr.cn/jnews/385803.htm
- http://m.wap.oexnr.cn/jnews/558238.htm
- http://m.wap.oexnr.cn/jnews/3542.htm
- http://m.wap.oexnr.cn/jnews/1769069.htm
- http://m.wap.oexnr.cn/jnews/453759.htm
- http://m.wap.oexnr.cn/jnews/2521164.htm
- http://m.wap.oexnr.cn/jnews/818155.htm
- http://m.wap.oexnr.cn/jnews/59814.htm
- http://m.wap.oexnr.cn/jnews/5720724.htm
- http://m.wap.oexnr.cn/jnews/43589.htm
- http://m.wap.oexnr.cn/jnews/61379.htm
- http://m.wap.oexnr.cn/jnews/1089.htm
- http://m.wap.oexnr.cn/jnews/716173.htm
- http://m.wap.oexnr.cn/jnews/48276.htm
- http://m.wap.oexnr.cn/jnews/1888.htm
- http://m.wap.oexnr.cn/jnews/9274.htm
- http://m.wap.oexnr.cn/jnews/1083900.htm
- http://m.wap.oexnr.cn/jnews/9612.htm
- http://m.wap.oexnr.cn/jnews/67761.htm
- http://m.wap.oexnr.cn/jnews/9684.htm
- http://m.wap.oexnr.cn/jnews/9453337.htm
- http://m.wap.oexnr.cn/jnews/564651.htm
- http://m.wap.oexnr.cn/jnews/24383.htm
- http://m.wap.oexnr.cn/jnews/8995364.htm
- http://m.wap.oexnr.cn/jnews/2705254.htm
- http://m.wap.oexnr.cn/jnews/606831.htm
- http://m.wap.oexnr.cn/jnews/6322.htm
- http://m.wap.oexnr.cn/jnews/87177.htm
- http://m.wap.oexnr.cn/jnews/456564.htm
- http://m.wap.oexnr.cn/jnews/4964633.htm
- http://m.wap.oexnr.cn/jnews/1362228.htm
- http://m.wap.oexnr.cn/jnews/6422479.htm
- http://m.wap.oexnr.cn/jnews/12503.htm
- http://m.wap.oexnr.cn/jnews/5259.htm
- http://m.wap.oexnr.cn/jnews/1006.htm
- http://m.wap.oexnr.cn/jnews/61172.htm
- http://m.wap.oexnr.cn/jnews/320830.htm
- http://m.wap.oexnr.cn/jnews/4325243.htm
- http://m.wap.oexnr.cn/jnews/1400.htm
- http://m.wap.oexnr.cn/jnews/3387.htm
- http://m.wap.oexnr.cn/jnews/7370578.htm
- http://m.wap.oexnr.cn/jnews/0336882.htm
- http://m.wap.oexnr.cn/jnews/6620.htm
- http://m.wap.oexnr.cn/jnews/9513.htm
- http://m.wap.oexnr.cn/jnews/761383.htm
- http://m.wap.oexnr.cn/jnews/7756.htm
- http://m.wap.oexnr.cn/jnews/07233.htm
- http://m.wap.oexnr.cn/jnews/2023.htm
- http://m.wap.oexnr.cn/jnews/5186416.htm
- http://m.wap.oexnr.cn/jnews/510901.htm
- http://m.wap.oexnr.cn/jnews/2474384.htm
- http://m.wap.oexnr.cn/jnews/915551.htm
- http://m.wap.oexnr.cn/jnews/896383.htm
- http://m.wap.oexnr.cn/jnews/6503.htm
- http://m.wap.oexnr.cn/jnews/550985.htm
- http://m.wap.oexnr.cn/jnews/6197.htm
- http://m.wap.oexnr.cn/jnews/96617.htm
- http://m.wap.oexnr.cn/jnews/9198410.htm
- http://m.wap.oexnr.cn/jnews/8101.htm
- http://m.wap.oexnr.cn/jnews/3744222.htm
- http://m.wap.oexnr.cn/jnews/2130.htm
- http://m.wap.oexnr.cn/jnews/6320231.htm
- http://m.wap.oexnr.cn/jnews/2999851.htm
- http://m.wap.oexnr.cn/jnews/2875018.htm
- http://m.wap.oexnr.cn/jnews/43272.htm
- http://m.wap.oexnr.cn/jnews/6372.htm
- http://m.wap.oexnr.cn/jnews/7398.htm
- http://m.wap.oexnr.cn/jnews/41252.htm
- http://m.wap.oexnr.cn/jnews/9489.htm
- http://m.wap.oexnr.cn/jnews/187072.htm
- http://m.wap.oexnr.cn/jnews/948302.htm
- http://m.wap.oexnr.cn/jnews/1973.htm
- http://m.wap.oexnr.cn/jnews/1505168.htm
- http://m.wap.oexnr.cn/jnews/423509.htm
- http://m.wap.oexnr.cn/jnews/845015.htm
- http://m.wap.oexnr.cn/jnews/3769.htm
- http://m.wap.oexnr.cn/jnews/0694.htm
- http://m.wap.oexnr.cn/jnews/528443.htm
- http://m.wap.oexnr.cn/jnews/75013.htm
- http://m.wap.oexnr.cn/jnews/8861017.htm
- http://m.wap.oexnr.cn/jnews/75686.htm
- http://m.wap.oexnr.cn/jnews/519113.htm
- http://m.wap.oexnr.cn/jnews/8065.htm
- http://m.wap.oexnr.cn/jnews/661542.htm

## 项目结构

项目采用模块化分层架构，核心代码位于 gateway 包下，辅助目录用于配置、测试与文档。

```
webjunction-archive-gateway/
├── gateway/                           # 核心 Python 包
│   ├── __init__.py                    # 包初始化，导出主要接口类
│   ├── cli.py                         # 命令行入口，定义 click 命令组
│   ├── runner.py                      # 任务运行器，控制并发、重试与生命周期
│   ├── fetcher.py                     # HTTP 请求封装，含超时、重试、会话管理
│   ├── parser.py                      # HTML 元数据抽取器，基于 beautifulsoup4
│   ├── cache.py                       # 本地磁盘缓存管理，支持压缩与 TTL
│   ├── exporters/                     # 输出格式适配器子包
│   │   ├── __init__.py
│   │   ├── json_exporter.py           # 输出为 JSON Lines 格式
│   │   ├── csv_exporter.py            # 输出为 CSV 表格（依赖 pandas）
│   │   ├── sqlite_exporter.py         # 写入 SQLite 数据库表
│   │   └── markdown_exporter.py       # 生成 Markdown 索引列表
│   ├── validators/                    # 响应验证钩子子包
│   │   ├── __init__.py
│   │   ├── status_validator.py        # 检查 HTTP 状态码是否为 200
│   │   └── keyword_validator.py       # 检查页面是否包含指定关键词
│   └── utils/                         # 通用工具函数
│       ├── __init__.py
│       ├── url_utils.py               # URL 解析、模式匹配、缓存键生成
│       └── logging_utils.py           # 日志格式化与轮转配置
├── tests/                             # 单元测试与集成测试目录
│   ├── conftest.py                    # pytest 共享 fixture 配置
│   ├── test_fetcher.py                # 测试 HTTP 请求与重试逻辑
│   ├── test_parser.py                 # 测试元数据抽取准确性
│   └── test_runner.py                 # 测试任务调度与并发控制
├── docs/                              # 完整文档源码（Markdown 格式）
│   ├── user/                          # 用户手册
│   │   ├── quickstart.md
│   │   ├── configuration.md
│   │   └── output_formats.md
│   └── development/                   # 开发与贡献文档
│       ├── architecture.md
│       ├── writing_plugins.md
│       └── testing.md
├── scripts/                           # 运维与辅助脚本
│   ├── batch_process.sh               # 批量处理多批 URL 文件的 shell 示例
│   └── clean_cache.py                 # 清理过期缓存文件的独立脚本
├── config/                            # 配置文件模板
│   ├── default.env                    # 默认环境变量示例（含超时、并发数）
│   └── logging.conf                   # 日志格式与输出路径配置
├── requirements.txt                   # 生产环境依赖列表
├── requirements-dev.txt               # 开发环境额外依赖（pytest, black, mypy）
├── setup.py                           # 项目安装脚本（setuptools）
├── README.md                          # 本文件
├── LICENSE                            # MIT 许可证全文
└── .gitignore                         # Git 忽略规则（缓存目录、虚拟环境等）
```

## 贡献指南

项目采用 GitHub Flow 协作模式，所有贡献均通过 Pull Request 合并，主分支为 main。请确保在提交前通过所有测试与代码风格检查。

第一步：选择或创建 Issue。在 GitHub Issues 页面查找现有任务，或新建 Issue 描述您希望修复的缺陷或新增的功能，等待维护者回复确认。

第二步：派生仓库并创建功能分支。将主仓库 Fork 到个人账户下，然后克隆到本地，基于 main 分支创建一个具有描述性名称的新分支，例如 feature/add-xml-exporter。

第三步：编写代码与单元测试。在相应模块中实现您的改动，同时在 tests 目录下补充对应的测试用例，确保测试覆盖率达到 80% 以上。运行 pytest 验证所有测试通过。

第四步：更新文档与示例。如果您的改动涉及用户可见的行为（如新增命令行参数或导出格式），请同步更新 docs 目录下的相关文档，并在 README 的功能概览或快速开始中补充说明。

第五步：提交 Pull Request。将您的分支推送到 GitHub，然后向主仓库的 main 分支发起 Pull Request，在描述中关联相关 Issue 编号，并简要说明改动内容与测试结果。等待维护者进行 Code Review 并合并。

## 常见问题

**问题：处理大量 URL 时出现 “ConnectionError” 或超时错误，如何提高稳定性？**

回答：建议优先启用本地缓存（--cache 参数），避免重复请求。同时可通过环境变量或 .env 文件调整请求超时时间（DEFAULT_TIMEOUT=30，单位秒）和最大重试次数（MAX_RETRIES=5）。若目标服务器限制并发，可降低并发数（CONCURRENT_WORKERS=2）。此外，可使用 --delay 参数在每次请求后增加固定延迟（单位毫秒），模拟人类浏览行为。

**问题：导出的 JSON 文件中，部分条目缺少标题或发布时间字段，如何排查？**

回答：这通常是因为目标页面结构发生变动或页面返回了非预期内容（如重定向、错误页）。首先检查该条目的 status 字段是否为 success，若为 failure 则查看 error_message。若状态成功但字段为空，则可能是页面布局与内置解析器不匹配。您可以通过自定义解析器插件（参考 docs/development/writing_plugins.md）覆盖默认抽取逻辑，或使用 --dump-raw 参数保存原始 HTML 进行人工分析。

**问题：项目能否处理除 oexnr.cn 之外的其他域名？**

回答：可以。虽然项目名称和示例数据围绕 oexnr.cn 设计，但核心路由、缓存和解析模块与域名无关

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
