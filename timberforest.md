# JNews Archive Aggregator

JNews Archive Aggregator 是一个面向移动端新闻资源聚合与历史内容检索的开源工具集，专为需要批量归档、索引和快速查询来自特定内容源的新闻页面而设计。该项目定位为技术资源与外链汇总中间件，不直接生产内容，而是提供标准化的采集、去重、存储与展示方案，帮助研究人员、数据分析师和内容运营人员高效管理大量分散的新闻链接。

目标用户包括学术研究机构中的媒体分析团队、企业市场部门的竞品情报组、以及独立开发者构建个人知识库或舆情监控系统。通过对目标域名下大量随机编号的新闻页面进行结构化处理，本项目解决了人工逐一保存、分类和检索效率低下的问题，同时提供了可扩展的插件机制以适应不同来源的页面结构变化。

## 功能概览

**批量链接导入与解析**：支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别并提取页面中的元数据（标题、发布时间、正文摘要）。

**分布式去重与指纹计算**：基于 Simhash 算法对页面内容进行指纹提取，实现百万级链接的近似去重，避免同一新闻内容因不同 URL 被重复收录。

**自定义元数据抽取规则**：提供基于 XPath 和正则表达式的可配置抽取模板，用户无需修改核心代码即可适配新的页面布局或 DOM 结构变更。

**增量更新与变更检测**：定期扫描已收录链接的页面状态，检测内容更新、删除或重定向，维护归档数据的完整性与时效性。

**全文检索引擎集成**：内置对 Elasticsearch 和 Meilisearch 的适配器，支持分词搜索、短语匹配和按时间范围过滤，检索响应时间在百万级数据下低于 200 毫秒。

**数据导出与报表生成**：支持将归档结果导出为 JSON、CSV 和 Parquet 格式，并可生成按日、周、月的链接数量统计报表，用于趋势分析。

**RESTful API 服务**：提供基于 FastAPI 的 HTTP 接口，涵盖链接提交、状态查询、内容检索和统计汇总等核心操作，方便与其他系统集成。

**容器化部署支持**：提供完整的 Dockerfile 和 docker-compose 编排文件，支持 Redis 缓存、PostgreSQL 元数据存储和 MinIO 对象存储的快速启动。

## 应用场景

学术研究中的媒体框架分析：研究机构使用本工具对特定新闻域名下的全部可访问页面进行批量抓取与元数据提取，构建用于内容分析、框架理论和议程设置研究的结构化数据集，替代人工手动采集的低效流程。

企业竞品情报监控：市场部门将竞品相关的新闻链接列表导入系统，通过变更检测功能及时发现新发布的报道或已有内容的修改，结合全文检索快速定位涉及自身品牌的关键段落，为决策提供依据。

个人知识库与阅读存档：独立开发者或博客作者将日常阅读中积累的散乱链接集中托管于本系统，利用去重和分类功能整理成个人数字图书馆，并通过 API 集成到笔记软件或 RSS 阅读器中实现统一检索。

舆情应急响应演练：公关团队在模拟舆情事件中，利用本工具对历史新闻数据进行快速检索与统计分析，训练团队在高压环境下从大量信息中提取关键时间线和观点分布的能力。

数据迁移与格式标准化：数据工程师将本系统作为中间层，从非标准化的新闻页面中抽取统一字段，输出为 Parquet 或 Avro 格式供下游数据湖或数仓使用，减少重复编写解析脚本的工作量。

## 快速开始

以下命令演示了从克隆仓库到启动开发环境并运行第一个链接导入任务的完整流程。

```bash
git clone https://github.com/jnews-archive/jnews-aggregator.git
cd jnews-aggregator

python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -e .

cp .env.example .env
# 编辑 .env 文件，配置数据库连接和缓存地址

python scripts/import_links.py --input sample_links.txt --source jnews
python scripts/run_indexer.py --start-date 2026-01-01 --end-date 2026-08-25
uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
| :--- | :--- | :--- |
| Python | 3.10 或更高 | 核心运行环境，低于此版本将导致类型注解和异步特性兼容性问题 |
| PostgreSQL | 14.0 或更高 | 存储链接元数据、任务状态和用户配置信息，需启用 pg_trgm 扩展 |
| Redis | 6.2 或更高 | 用于分布式锁、任务队列缓存和 API 限流计数器 |
| Elasticsearch | 8.0 或更高 | 可选依赖，仅在使用全文检索功能时需要；推荐 8.5 以上版本 |
| MinIO | RELEASE.2023-12-09 或更高 | 可选依赖，用于存储原始 HTML 快照和导出的报表文件 |
| Docker Compose | 2.20 或更高 | 仅容器化部署方式需要，用于编排多服务启动顺序 |
| Git | 2.30 或更高 | 代码克隆和版本管理，推荐使用 SSH 方式克隆 |
| make | 3.81 或更高 | 用于执行 Makefile 中定义的快捷命令（可选但推荐） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
| :--- | :--- | :--- |
| 入门指南 | docs/getting-started.md | 如何安装、配置并在一小时内完成第一个链接归档任务 |
| 架构设计 | docs/architecture.md | 系统的整体模块划分、数据流向和各组件之间的通信协议 |
| 开发指南 | docs/development.md | 如何编写自定义抽取插件、提交代码变更以及运行测试套件 |
| API 参考 | docs/api-reference.md | 所有 RESTful 接口的请求参数、响应格式和状态码说明 |
| 运维手册 | docs/operations.md | 生产环境部署、监控指标、日志管理和备份恢复策略 |
| 常见问题 | docs/faq.md | 社区积累的典型问题与对应解决方案，持续更新 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/0564042.htm
- http://m.3g.bwbkj.cn/jnews/0653889.htm
- http://m.3g.bwbkj.cn/jnews/3381.htm
- http://m.3g.bwbkj.cn/jnews/903548.htm
- http://m.3g.bwbkj.cn/jnews/8558532.htm
- http://m.3g.bwbkj.cn/jnews/61125.htm
- http://m.3g.bwbkj.cn/jnews/71979.htm
- http://m.3g.bwbkj.cn/jnews/1583523.htm
- http://m.3g.bwbkj.cn/jnews/297034.htm
- http://m.3g.bwbkj.cn/jnews/921343.htm
- http://m.3g.bwbkj.cn/jnews/6054014.htm
- http://m.3g.bwbkj.cn/jnews/22803.htm
- http://m.3g.bwbkj.cn/jnews/2602.htm
- http://m.3g.bwbkj.cn/jnews/10231.htm
- http://m.3g.bwbkj.cn/jnews/5088.htm
- http://m.3g.bwbkj.cn/jnews/38126.htm
- http://m.3g.bwbkj.cn/jnews/4032.htm
- http://m.3g.bwbkj.cn/jnews/356571.htm
- http://m.3g.bwbkj.cn/jnews/116980.htm
- http://m.3g.bwbkj.cn/jnews/52690.htm
- http://m.3g.bwbkj.cn/jnews/31871.htm
- http://m.3g.bwbkj.cn/jnews/60399.htm
- http://m.3g.bwbkj.cn/jnews/4936.htm
- http://m.3g.bwbkj.cn/jnews/4095104.htm
- http://m.3g.bwbkj.cn/jnews/0629.htm
- http://m.3g.bwbkj.cn/jnews/5306084.htm
- http://m.3g.bwbkj.cn/jnews/409247.htm
- http://m.3g.bwbkj.cn/jnews/95170.htm
- http://m.3g.bwbkj.cn/jnews/8106307.htm
- http://m.3g.bwbkj.cn/jnews/8594.htm
- http://m.3g.bwbkj.cn/jnews/57437.htm
- http://m.3g.bwbkj.cn/jnews/466376.htm
- http://m.3g.bwbkj.cn/jnews/174284.htm
- http://m.3g.bwbkj.cn/jnews/81538.htm
- http://m.3g.bwbkj.cn/jnews/8202.htm
- http://m.3g.bwbkj.cn/jnews/7360730.htm
- http://m.3g.bwbkj.cn/jnews/6618972.htm
- http://m.3g.bwbkj.cn/jnews/264207.htm
- http://m.3g.bwbkj.cn/jnews/5446.htm
- http://m.3g.bwbkj.cn/jnews/0460203.htm
- http://m.3g.bwbkj.cn/jnews/3336.htm
- http://m.3g.bwbkj.cn/jnews/750895.htm
- http://m.3g.bwbkj.cn/jnews/5626035.htm
- http://m.3g.bwbkj.cn/jnews/4321575.htm
- http://m.3g.bwbkj.cn/jnews/98942.htm
- http://m.3g.bwbkj.cn/jnews/9625.htm
- http://m.3g.bwbkj.cn/jnews/6432607.htm
- http://m.3g.bwbkj.cn/jnews/560937.htm
- http://m.3g.bwbkj.cn/jnews/4288.htm
- http://m.3g.bwbkj.cn/jnews/342916.htm
- http://m.3g.bwbkj.cn/jnews/729702.htm
- http://m.3g.bwbkj.cn/jnews/750158.htm
- http://m.3g.bwbkj.cn/jnews/76447.htm
- http://m.3g.bwbkj.cn/jnews/9196550.htm
- http://m.3g.bwbkj.cn/jnews/0505.htm
- http://m.3g.bwbkj.cn/jnews/191618.htm
- http://m.3g.bwbkj.cn/jnews/491440.htm
- http://m.3g.bwbkj.cn/jnews/57226.htm
- http://m.3g.bwbkj.cn/jnews/0145.htm
- http://m.3g.bwbkj.cn/jnews/497280.htm
- http://m.3g.bwbkj.cn/jnews/9619.htm
- http://m.3g.bwbkj.cn/jnews/24107.htm
- http://m.3g.bwbkj.cn/jnews/24214.htm
- http://m.3g.bwbkj.cn/jnews/0974301.htm
- http://m.3g.bwbkj.cn/jnews/0386647.htm
- http://m.3g.bwbkj.cn/jnews/5980.htm
- http://m.3g.bwbkj.cn/jnews/068270.htm
- http://m.3g.bwbkj.cn/jnews/785571.htm
- http://m.3g.bwbkj.cn/jnews/5380875.htm
- http://m.3g.bwbkj.cn/jnews/0353946.htm
- http://m.3g.bwbkj.cn/jnews/8851.htm
- http://m.3g.bwbkj.cn/jnews/6890.htm
- http://m.3g.bwbkj.cn/jnews/910211.htm
- http://m.3g.bwbkj.cn/jnews/171621.htm
- http://m.3g.bwbkj.cn/jnews/30247.htm
- http://m.3g.bwbkj.cn/jnews/7415.htm
- http://m.3g.bwbkj.cn/jnews/921171.htm
- http://m.3g.bwbkj.cn/jnews/26812.htm
- http://m.3g.bwbkj.cn/jnews/73276.htm
- http://m.3g.bwbkj.cn/jnews/2116767.htm
- http://m.3g.bwbkj.cn/jnews/1640.htm
- http://m.3g.bwbkj.cn/jnews/8024900.htm
- http://m.3g.bwbkj.cn/jnews/8314904.htm
- http://m.3g.bwbkj.cn/jnews/868950.htm
- http://m.3g.bwbkj.cn/jnews/62218.htm
- http://m.3g.bwbkj.cn/jnews/755795.htm
- http://m.3g.bwbkj.cn/jnews/97826.htm
- http://m.3g.bwbkj.cn/jnews/9773.htm
- http://m.3g.bwbkj.cn/jnews/6465936.htm
- http://m.3g.bwbkj.cn/jnews/4641.htm
- http://m.3g.bwbkj.cn/jnews/0202015.htm
- http://m.3g.bwbkj.cn/jnews/610717.htm
- http://m.3g.bwbkj.cn/jnews/928724.htm
- http://m.3g.bwbkj.cn/jnews/73140.htm
- http://m.3g.bwbkj.cn/jnews/6722488.htm
- http://m.3g.bwbkj.cn/jnews/554045.htm
- http://m.3g.bwbkj.cn/jnews/7122.htm
- http://m.3g.bwbkj.cn/jnews/015091.htm
- http://m.3g.bwbkj.cn/jnews/70606.htm
- http://m.3g.bwbkj.cn/jnews/8611833.htm
- http://m.3g.bwbkj.cn/jnews/677440.htm
- http://m.3g.bwbkj.cn/jnews/0065.htm
- http://m.3g.bwbkj.cn/jnews/1096.htm
- http://m.3g.bwbkj.cn/jnews/5482.htm
- http://m.3g.bwbkj.cn/jnews/260841.htm
- http://m.3g.bwbkj.cn/jnews/172061.htm
- http://m.3g.bwbkj.cn/jnews/5883750.htm
- http://m.3g.bwbkj.cn/jnews/7414.htm
- http://m.3g.bwbkj.cn/jnews/8352776.htm
- http://m.3g.bwbkj.cn/jnews/4719.htm
- http://m.3g.bwbkj.cn/jnews/285222.htm
- http://m.3g.bwbkj.cn/jnews/7517.htm
- http://m.3g.bwbkj.cn/jnews/20358.htm
- http://m.3g.bwbkj.cn/jnews/0225604.htm
- http://m.3g.bwbkj.cn/jnews/213910.htm
- http://m.3g.bwbkj.cn/jnews/66063.htm
- http://m.3g.bwbkj.cn/jnews/2478156.htm
- http://m.3g.bwbkj.cn/jnews/6194.htm
- http://m.3g.bwbkj.cn/jnews/3049.htm
- http://m.3g.bwbkj.cn/jnews/124409.htm
- http://m.3g.bwbkj.cn/jnews/825002.htm
- http://m.3g.bwbkj.cn/jnews/6369716.htm
- http://m.3g.bwbkj.cn/jnews/212254.htm
- http://m.3g.bwbkj.cn/jnews/96835.htm
- http://m.3g.bwbkj.cn/jnews/6943742.htm
- http://m.3g.bwbkj.cn/jnews/1927224.htm
- http://m.3g.bwbkj.cn/jnews/6892.htm
- http://m.3g.bwbkj.cn/jnews/1875987.htm
- http://m.3g.bwbkj.cn/jnews/1191.htm
- http://m.3g.bwbkj.cn/jnews/04437.htm
- http://m.3g.bwbkj.cn/jnews/5299838.htm
- http://m.3g.bwbkj.cn/jnews/151266.htm
- http://m.3g.bwbkj.cn/jnews/25200.htm
- http://m.3g.bwbkj.cn/jnews/93423.htm
- http://m.3g.bwbkj.cn/jnews/27527.htm
- http://m.3g.bwbkj.cn/jnews/486431.htm
- http://m.3g.bwbkj.cn/jnews/766387.htm
- http://m.3g.bwbkj.cn/jnews/428504.htm
- http://m.3g.bwbkj.cn/jnews/0591666.htm
- http://m.3g.bwbkj.cn/jnews/230094.htm
- http://m.3g.bwbkj.cn/jnews/852394.htm
- http://m.3g.bwbkj.cn/jnews/060272.htm
- http://m.3g.bwbkj.cn/jnews/118450.htm
- http://m.3g.bwbkj.cn/jnews/308204.htm
- http://m.3g.bwbkj.cn/jnews/1260.htm
- http://m.3g.bwbkj.cn/jnews/6444113.htm
- http://m.3g.bwbkj.cn/jnews/4630710.htm
- http://m.3g.bwbkj.cn/jnews/06455.htm
- http://m.3g.bwbkj.cn/jnews/9159.htm
- http://m.3g.bwbkj.cn/jnews/253485.htm
- http://m.3g.bwbkj.cn/jnews/6750.htm
- http://m.3g.bwbkj.cn/jnews/1097.htm
- http://m.3g.bwbkj.cn/jnews/44382.htm
- http://m.3g.bwbkj.cn/jnews/7137.htm
- http://m.3g.bwbkj.cn/jnews/3826.htm
- http://m.3g.bwbkj.cn/jnews/929709.htm
- http://m.3g.bwbkj.cn/jnews/8825.htm
- http://m.3g.bwbkj.cn/jnews/6799.htm
- http://m.3g.bwbkj.cn/jnews/2167.htm
- http://m.3g.bwbkj.cn/jnews/5196.htm
- http://m.3g.bwbkj.cn/jnews/88600.htm
- http://m.3g.bwbkj.cn/jnews/4830.htm
- http://m.3g.bwbkj.cn/jnews/4003.htm
- http://m.3g.bwbkj.cn/jnews/31379.htm
- http://m.3g.bwbkj.cn/jnews/8043782.htm
- http://m.3g.bwbkj.cn/jnews/9560.htm
- http://m.3g.bwbkj.cn/jnews/6236549.htm
- http://m.3g.bwbkj.cn/jnews/04251.htm
- http://m.3g.bwbkj.cn/jnews/70255.htm
- http://m.3g.bwbkj.cn/jnews/6800480.htm
- http://m.3g.bwbkj.cn/jnews/241268.htm
- http://m.3g.bwbkj.cn/jnews/8061795.htm
- http://m.3g.bwbkj.cn/jnews/8847.htm
- http://m.3g.bwbkj.cn/jnews/20809.htm
- http://m.3g.bwbkj.cn/jnews/7760050.htm
- http://m.3g.bwbkj.cn/jnews/305755.htm
- http://m.3g.bwbkj.cn/jnews/1355358.htm
- http://m.3g.bwbkj.cn/jnews/2319.htm
- http://m.3g.bwbkj.cn/jnews/70540.htm
- http://m.3g.bwbkj.cn/jnews/3966.htm
- http://m.3g.bwbkj.cn/jnews/5851998.htm
- http://m.3g.bwbkj.cn/jnews/1507085.htm
- http://m.3g.bwbkj.cn/jnews/6234477.htm
- http://m.3g.bwbkj.cn/jnews/1457075.htm
- http://m.3g.bwbkj.cn/jnews/89108.htm
- http://m.3g.bwbkj.cn/jnews/7338637.htm
- http://m.3g.bwbkj.cn/jnews/23690.htm
- http://m.3g.bwbkj.cn/jnews/8972.htm
- http://m.3g.bwbkj.cn/jnews/13238.htm
- http://m.3g.bwbkj.cn/jnews/94741.htm
- http://m.3g.bwbkj.cn/jnews/4940.htm
- http://m.3g.bwbkj.cn/jnews/94278.htm
- http://m.3g.bwbkj.cn/jnews/2147.htm
- http://m.3g.bwbkj.cn/jnews/7809.htm
- http://m.3g.bwbkj.cn/jnews/017992.htm
- http://m.3g.bwbkj.cn/jnews/2297.htm
- http://m.3g.bwbkj.cn/jnews/3723.htm
- http://m.3g.bwbkj.cn/jnews/5439.htm
- http://m.3g.bwbkj.cn/jnews/9142166.htm
- http://m.3g.bwbkj.cn/jnews/2357.htm
- http://m.3g.bwbkj.cn/jnews/5507.htm
- http://m.3g.bwbkj.cn/jnews/6042.htm
- http://m.3g.bwbkj.cn/jnews/680706.htm
- http://m.3g.bwbkj.cn/jnews/53077.htm
- http://m.3g.bwbkj.cn/jnews/4725.htm
- http://m.3g.bwbkj.cn/jnews/319964.htm
- http://m.3g.bwbkj.cn/jnews/2198.htm
- http://m.3g.bwbkj.cn/jnews/05957.htm
- http://m.3g.bwbkj.cn/jnews/67271.htm
- http://m.3g.bwbkj.cn/jnews/7640.htm
- http://m.3g.bwbkj.cn/jnews/47244.htm
- http://m.3g.bwbkj.cn/jnews/25883.htm
- http://m.3g.bwbkj.cn/jnews/782634.htm
- http://m.3g.bwbkj.cn/jnews/8800.htm
- http://m.3g.bwbkj.cn/jnews/131212.htm
- http://m.3g.bwbkj.cn/jnews/95368.htm
- http://m.3g.bwbkj.cn/jnews/6204.htm
- http://m.3g.bwbkj.cn/jnews/0828.htm
- http://m.3g.bwbkj.cn/jnews/98138.htm
- http://m.3g.bwbkj.cn/jnews/4824500.htm
- http://m.3g.bwbkj.cn/jnews/1527934.htm
- http://m.3g.bwbkj.cn/jnews/969395.htm
- http://m.3g.bwbkj.cn/jnews/7136164.htm
- http://m.3g.bwbkj.cn/jnews/5543.htm
- http://m.3g.bwbkj.cn/jnews/4599367.htm
- http://m.3g.bwbkj.cn/jnews/70809.htm
- http://m.3g.bwbkj.cn/jnews/1128.htm
- http://m.3g.bwbkj.cn/jnews/532226.htm
- http://m.3g.bwbkj.cn/jnews/2396841.htm
- http://m.3g.bwbkj.cn/jnews/4429.htm
- http://m.3g.bwbkj.cn/jnews/735349.htm
- http://m.3g.bwbkj.cn/jnews/12003.htm
- http://m.3g.bwbkj.cn/jnews/3266271.htm
- http://m.3g.bwbkj.cn/jnews/911045.htm
- http://m.3g.bwbkj.cn/jnews/309310.htm
- http://m.3g.bwbkj.cn/jnews/1972553.htm
- http://m.3g.bwbkj.cn/jnews/2284222.htm
- http://m.3g.bwbkj.cn/jnews/4332.htm
- http://m.3g.bwbkj.cn/jnews/343077.htm
- http://m.3g.bwbkj.cn/jnews/9106014.htm
- http://m.3g.bwbkj.cn/jnews/51863.htm
- http://m.3g.bwbkj.cn/jnews/6281.htm
- http://m.3g.bwbkj.cn/jnews/2961059.htm
- http://m.3g.bwbkj.cn/jnews/78568.htm
- http://m.3g.bwbkj.cn/jnews/172524.htm
- http://m.3g.bwbkj.cn/jnews/182711.htm
- http://m.3g.bwbkj.cn/jnews/8355.htm
- http://m.3g.bwbkj.cn/jnews/759387.htm
- http://m.3g.bwbkj.cn/jnews/81477.htm
- http://m.3g.bwbkj.cn/jnews/0871.htm
- http://m.3g.bwbkj.cn/jnews/15851.htm
- http://m.3g.bwbkj.cn/jnews/2416554.htm
- http://m.3g.bwbkj.cn/jnews/5919898.htm
- http://m.3g.bwbkj.cn/jnews/7149.htm
- http://m.3g.bwbkj.cn/jnews/734484.htm
- http://m.3g.bwbkj.cn/jnews/9699.htm
- http://m.3g.bwbkj.cn/jnews/95411.htm
- http://m.3g.bwbkj.cn/jnews/0615.htm
- http://m.3g.bwbkj.cn/jnews/693101.htm
- http://m.3g.bwbkj.cn/jnews/0705182.htm
- http://m.3g.bwbkj.cn/jnews/104153.htm
- http://m.3g.bwbkj.cn/jnews/3242.htm
- http://m.3g.bwbkj.cn/jnews/7259.htm
- http://m.3g.bwbkj.cn/jnews/8466856.htm
- http://m.3g.bwbkj.cn/jnews/8526658.htm
- http://m.3g.bwbkj.cn/jnews/79328.htm
- http://m.3g.bwbkj.cn/jnews/538590.htm
- http://m.3g.bwbkj.cn/jnews/2464.htm
- http://m.3g.bwbkj.cn/jnews/386848.htm
- http://m.3g.bwbkj.cn/jnews/1365.htm
- http://m.3g.bwbkj.cn/jnews/3696.htm
- http://m.3g.bwbkj.cn/jnews/075201.htm
- http://m.3g.bwbkj.cn/jnews/9920.htm
- http://m.3g.bwbkj.cn/jnews/3080.htm
- http://m.3g.bwbkj.cn/jnews/7535.htm
- http://m.3g.bwbkj.cn/jnews/36487.htm
- http://m.3g.bwbkj.cn/jnews/6022.htm
- http://m.3g.bwbkj.cn/jnews/0377.htm
- http://m.3g.bwbkj.cn/jnews/2043.htm
- http://m.3g.bwbkj.cn/jnews/5607.htm
- http://m.3g.bwbkj.cn/jnews/8119939.htm
- http://m.3g.bwbkj.cn/jnews/0532.htm
- http://m.3g.bwbkj.cn/jnews/71620.htm
- http://m.3g.bwbkj.cn/jnews/580603.htm
- http://m.3g.bwbkj.cn/jnews/95457.htm
- http://m.3g.bwbkj.cn/jnews/9567616.htm
- http://m.3g.bwbkj.cn/jnews/6192.htm
- http://m.3g.bwbkj.cn/jnews/5482227.htm
- http://m.3g.bwbkj.cn/jnews/2673.htm
- http://m.3g.bwbkj.cn/jnews/4225.htm
- http://m.3g.bwbkj.cn/jnews/0111.htm
- http://m.3g.bwbkj.cn/jnews/4573.htm
- http://m.3g.bwbkj.cn/jnews/66623.htm
- http://m.3g.bwbkj.cn/jnews/1785161.htm
- http://m.3g.bwbkj.cn/jnews/5161389.htm
- http://m.3g.bwbkj.cn/jnews/94240.htm
- http://m.3g.bwbkj.cn/jnews/95218.htm
- http://m.3g.bwbkj.cn/jnews/9162408.htm
- http://m.3g.bwbkj.cn/jnews/9246960.htm
- http://m.3g.bwbkj.cn/jnews/3080435.htm

## 项目结构

```
jnews-aggregator/
├── app/                                # 核心应用模块
│   ├── api/                            # RESTful API 路由定义
│   │   ├── endpoints/                  # 各功能端点（links, search, stats）
│   │   └── dependencies.py             # 依赖注入与鉴权中间件
│   ├── core/                           # 核心业务逻辑
│   │   ├── crawler/                    # 爬取调度与请求限速器
│   │   ├── dedup/                      # Simhash 去重引擎
│   │   ├── extractor/                  # XPath/正则抽取器与模板注册表
│   │   └── indexer/                    # 索引更新与变更检测工作流
│   ├── models/                         # SQLAlchemy 和 Pydantic 数据模型
│   ├── services/                       # 外部服务适配器（DB, ES, Redis, MinIO）
│   └── utils/                          # 日志、配置、重试、时间处理工具
├── scripts/                            # 运维与数据迁移脚本
│   ├── import_links.py                 # 批量链接导入命令行工具
│   ├── run_indexer.py                  # 手动触发索引任务
│   └── export_report.py                # 导出统计报表为 CSV/Parquet
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 细粒度模块测试
│   └── integration/                    # 端到端流程测试（需外部依赖）
├── docker/                             # 容器化相关文件
│   ├── Dockerfile                      # 多阶段构建定义
│   └── docker-compose.yml              # 全服务编排（app, db, redis, es, minio）
├── docs/                               # 完整文档源文件
│   ├── getting-started.md
│   ├── architecture.md
│   ├── development.md
│   ├── api-reference.md
│   ├── operations.md
│   └── faq.md
├── config/                             # 环境配置模板与默认设置
│   ├── .env.example                    # 环境变量示例
│   └── logging.conf                    # 日志格式与级别配置
├── data/                               # 本地开发用的样例数据与缓存目录
│   └── samples/                        # 示例链接列表文件
├── .github/                            # GitHub 工作流定义
│   └── workflows/                      # CI/CD 流水线（测试、构建、发布）
├── Makefile                            # 常用命令快捷方式（install, test, run）
├── requirements.txt                    # 生产环境依赖列表
├── requirements-dev.txt                # 开发与测试额外依赖
└── pyproject.toml                      # 项目元数据与构建配置
```

## 贡献指南

本项目的开发遵循标准的分支管理模型，所有贡献均通过 Pull Request 流程合入主分支。请按照以下步骤提交您的贡献。

第一步：查找或创建议题。在提交任何代码之前，请先在 Issues 列表中搜索是否已有相关议题。若无，请新建一个议题描述您要修复的问题或新增的功能，等待维护者确认方向后再开始工作，避免无效劳动。

第二步：派生仓库并创建功能分支。将本项目派生到您自己的 GitHub 账户下，然后基于 main 分支创建一个新的分支，分支命名规则为 `feature/简短描述` 或 `fix/议题编号`。请确保您的分支与上游 main 分支保持同步。

第三步：编写代码与测试。所有新增功能必须包含对应的单元测试，测试覆盖率不得低于 80%。代码风格应符合 PEP 8 规范，并使用 black 和 isort 进行格式化。提交前请运行 `make lint` 和 `make test` 确保本地检查全部通过。

第四步：提交 Pull Request。推送到您的派生仓库后，向本仓库的 main 分支提交 PR。PR 描述中应清晰关联议题编号、列出变更摘要、说明测试结果和影响范围。维护者将在 3 个工作日内进行代码审查并提出修改意见。

第五步：签署开发者贡献许可协议。首次提交 PR 时，您需要在 PR 评论中明确声明同意本项目的开发者贡献许可协议，即您授予项目团队永久、不可撤销、免版税的使用、修改和分发您所贡献代码的权利。

## 常见问题

问：导入包含数百个链接的文本文件时，系统提示内存不足或超时，应如何优化？

答：这是由于默认的同步导入模式在单次请求中加载了全部链接并逐条处理。请改用异步批量导入方式，将链接文件上传至 MinIO 对象存储，然后通过 `POST /api/v1/imports` 接口提交导入任务，系统将以后台队列方式分批次处理，每批 1000 条，避免内存溢出。您也可以调整 `config/.env` 中的 `BATCH_SIZE` 和 `WORKER_CONCURRENCY` 参数来控制并发度。

问：全文检索返回的结果中，部分明显包含关键词的文档未能被命中，如何诊断？

答：这通常与索引映射的分析器配置有关。请检查 Elasticsearch 索引设置中的 `analyzer` 字段是否使用了适合中文的分词器（如 `ik_smart` 或 `hanlp`）。若未配置，系统默认使用 `standard` 分析器，对中文分词效果不佳。您可以在 `app/services/es_client.py` 中修改索引模板，将 `analyzer` 改为 `ik_max_word`，然后执行 `python scripts/reindex.py --rebuild` 重建索引。另外，请确认检索时使用的查询语法是否正确，模糊匹配应使用 `match` 而非 `term`。

问：生产环境部署后，定时任务未能按时触发索引更新，该如何排查？

答：请优先检查 Redis 中存储的分布式锁状态。若某个任务因异常退出而未释放

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:04
