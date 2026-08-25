# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与历史新闻存档检索的轻量级数据桥接工具。该项目定位于为开发者、数据分析师及内容研究者提供一套标准化的新闻链接采集、清洗与持久化存储方案，解决分散式新闻源难以统一管理和历史链接易失效的核心痛点。通过声明式配置与可扩展的解析引擎，用户可将非结构化的新闻页面转化为结构化数据集，适用于舆情监控、事件回溯及知识图谱构建等场景。

## 功能概览

**批量链接提取与标准化**：支持从指定域名路径下批量提取新闻链接，自动识别并补全相对路径，输出统一格式的 URL 列表，减少人工干预成本。

**增量更新与去重机制**：内置基于 URL 哈希与发布时间戳的增量更新逻辑，避免重复抓取，确保数据集的唯一性与时效性，适用于长期运行的自动化采集任务。

**多格式数据导出**：提供 JSON、CSV、SQLite 三种导出格式，满足不同下游系统的数据接入需求，可直接导入数据分析工具或关系型数据库。

**用户代理轮换与请求重试**：集成随机 User-Agent 池与指数退避重试策略，有效规避反爬机制，提高大规模采集任务的成功率与稳定性。

**链接健康状态检查**：对已采集的链接进行定期可用性探测，返回 HTTP 状态码与响应时间，辅助识别失效链接，为数据清洗提供依据。

**可配置的过滤规则引擎**：允许用户自定义关键词黑白名单及正则表达式过滤规则，精准筛选符合业务需求的新闻链接，剔除广告或无关内容。

**任务编排与调度接口**：提供 RESTful API 和命令行工具双重调用方式，支持与 Cron 或 Airflow 等调度系统集成，实现全自动化的数据流水线。

## 应用场景

舆情监测系统数据接入：企业公关部门或舆情服务商可通过 NewsLink Aggregator 定期采集特定新闻源站点的最新文章链接，结合 NLP 情感分析模块，实时追踪品牌提及率与舆论倾向变化，为危机预警提供原始数据支撑。

历史新闻数据集构建：学术研究机构在进行媒介演变或事件传播路径分析时，需大规模收集历史新闻页面。该项目可批量提取指定时段内的新闻链接，并配合归档工具生成标准数据集，减少人工整理时间。

个人化新闻聚合阅读器：技术爱好者或自媒体运营者可利用该项目自建轻量级新闻聚合服务，将多个新闻源的链接统一汇总至 RSS 阅读器或个人仪表盘，实现跨站点的信息整合，避免频繁切换不同网页。

自动化链接失效巡检：大型门户网站或内容管理系统维护人员可使用链接健康检查功能，定期扫描站内引用的外部新闻链接，及时发现并修复 404 或 500 错误链接，提升用户体验与 SEO 评分。

## 快速开始

以下命令将在本地克隆项目仓库、安装依赖并启动一个最小化的采集任务，以验证基础功能。

```bash
# 克隆项目仓库至本地
git clone https://github.com/example/news-aggregator.git

# 进入项目根目录
cd news-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行示例采集任务（采集指定域名下的新闻链接并输出 JSON 文件）
python cli.py collect --source http://m.3g.ghtkgg.cn/nnews/ --output data/links.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，提供异步 IO 支持与类型注解特性 |
| aiohttp | 3.8.4 及以上 | 异步 HTTP 客户端，用于高并发链接请求与响应处理 |
| beautifulsoup4 | 4.11.1 及以上 | HTML 解析库，用于新闻页面 DOM 结构分析与数据提取 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的后端加速引擎 |
| pandas | 1.5.0 及以上 | 数据分析库，用于数据清洗、转换及 CSV/JSON 格式输出 |
| sqlite3 | Python 内置模块 | 轻量级关系型数据库，用于持久化存储采集结果及去重管理 |
| pytest | 7.2.0 及以上 | 单元测试框架，用于执行项目自带测试套件验证环境正确性 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速安装并运行第一个采集任务？如何配置目标源和输出路径？ |
| 配置参考 | docs/configuration.md | 有哪些可用的配置项？过滤规则和请求参数如何设置？ |
| API 手册 | docs/api_reference.md | RESTful API 各端点的请求/响应格式是什么？认证方式如何实现？ |
| 开发指南 | docs/development.md | 如何扩展自定义解析器？如何贡献代码并提交 Pull Request？ |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/65674.htm
- http://m.3g.ghtkgg.cn/nnews/67388.htm
- http://m.3g.ghtkgg.cn/nnews/6993578.htm
- http://m.3g.ghtkgg.cn/nnews/073011.htm
- http://m.3g.ghtkgg.cn/nnews/01163.htm
- http://m.3g.ghtkgg.cn/nnews/8521351.htm
- http://m.3g.ghtkgg.cn/nnews/2836128.htm
- http://m.3g.ghtkgg.cn/nnews/188837.htm
- http://m.3g.ghtkgg.cn/nnews/47222.htm
- http://m.3g.ghtkgg.cn/nnews/4223328.htm
- http://m.3g.ghtkgg.cn/nnews/532149.htm
- http://m.3g.ghtkgg.cn/nnews/45060.htm
- http://m.3g.ghtkgg.cn/nnews/0076.htm
- http://m.3g.ghtkgg.cn/nnews/918323.htm
- http://m.3g.ghtkgg.cn/nnews/417891.htm
- http://m.3g.ghtkgg.cn/nnews/6880.htm
- http://m.3g.ghtkgg.cn/nnews/2403046.htm
- http://m.3g.ghtkgg.cn/nnews/3937.htm
- http://m.3g.ghtkgg.cn/nnews/059184.htm
- http://m.3g.ghtkgg.cn/nnews/2149067.htm
- http://m.3g.ghtkgg.cn/nnews/85158.htm
- http://m.3g.ghtkgg.cn/nnews/972016.htm
- http://m.3g.ghtkgg.cn/nnews/6530.htm
- http://m.3g.ghtkgg.cn/nnews/311039.htm
- http://m.3g.ghtkgg.cn/nnews/9568649.htm
- http://m.3g.ghtkgg.cn/nnews/4806.htm
- http://m.3g.ghtkgg.cn/nnews/5584.htm
- http://m.3g.ghtkgg.cn/nnews/9569209.htm
- http://m.3g.ghtkgg.cn/nnews/257862.htm
- http://m.3g.ghtkgg.cn/nnews/061505.htm
- http://m.3g.ghtkgg.cn/nnews/0981260.htm
- http://m.3g.ghtkgg.cn/nnews/3854838.htm
- http://m.3g.ghtkgg.cn/nnews/09399.htm
- http://m.3g.ghtkgg.cn/nnews/83061.htm
- http://m.3g.ghtkgg.cn/nnews/9355366.htm
- http://m.3g.ghtkgg.cn/nnews/3523908.htm
- http://m.3g.ghtkgg.cn/nnews/1995.htm
- http://m.3g.ghtkgg.cn/nnews/79647.htm
- http://m.3g.ghtkgg.cn/nnews/450665.htm
- http://m.3g.ghtkgg.cn/nnews/8278242.htm
- http://m.3g.ghtkgg.cn/nnews/6358.htm
- http://m.3g.ghtkgg.cn/nnews/9155.htm
- http://m.3g.ghtkgg.cn/nnews/4902.htm
- http://m.3g.ghtkgg.cn/nnews/4935304.htm
- http://m.3g.ghtkgg.cn/nnews/5257257.htm
- http://m.3g.ghtkgg.cn/nnews/650754.htm
- http://m.3g.ghtkgg.cn/nnews/592221.htm
- http://m.3g.ghtkgg.cn/nnews/3464558.htm
- http://m.3g.ghtkgg.cn/nnews/0456.htm
- http://m.3g.ghtkgg.cn/nnews/734602.htm
- http://m.3g.ghtkgg.cn/nnews/54206.htm
- http://m.3g.ghtkgg.cn/nnews/284609.htm
- http://m.3g.ghtkgg.cn/nnews/759506.htm
- http://m.3g.ghtkgg.cn/nnews/7107315.htm
- http://m.3g.ghtkgg.cn/nnews/8744.htm
- http://m.3g.ghtkgg.cn/nnews/012358.htm
- http://m.3g.ghtkgg.cn/nnews/67573.htm
- http://m.3g.ghtkgg.cn/nnews/1062309.htm
- http://m.3g.ghtkgg.cn/nnews/2134316.htm
- http://m.3g.ghtkgg.cn/nnews/2413459.htm
- http://m.3g.ghtkgg.cn/nnews/76205.htm
- http://m.3g.ghtkgg.cn/nnews/5288.htm
- http://m.3g.ghtkgg.cn/nnews/0537.htm
- http://m.3g.ghtkgg.cn/nnews/75424.htm
- http://m.3g.ghtkgg.cn/nnews/48804.htm
- http://m.3g.ghtkgg.cn/nnews/30402.htm
- http://m.3g.ghtkgg.cn/nnews/1114.htm
- http://m.3g.ghtkgg.cn/nnews/8542317.htm
- http://m.3g.ghtkgg.cn/nnews/296744.htm
- http://m.3g.ghtkgg.cn/nnews/8225.htm
- http://m.3g.ghtkgg.cn/nnews/4734226.htm
- http://m.3g.ghtkgg.cn/nnews/5457.htm
- http://m.3g.ghtkgg.cn/nnews/4882.htm
- http://m.3g.ghtkgg.cn/nnews/5237.htm
- http://m.3g.ghtkgg.cn/nnews/512303.htm
- http://m.3g.ghtkgg.cn/nnews/972479.htm
- http://m.3g.ghtkgg.cn/nnews/1410362.htm
- http://m.3g.ghtkgg.cn/nnews/4042233.htm
- http://m.3g.ghtkgg.cn/nnews/00680.htm
- http://m.3g.ghtkgg.cn/nnews/3968665.htm
- http://m.3g.ghtkgg.cn/nnews/6427569.htm
- http://m.3g.ghtkgg.cn/nnews/226321.htm
- http://m.3g.ghtkgg.cn/nnews/38710.htm
- http://m.3g.ghtkgg.cn/nnews/1328.htm
- http://m.3g.ghtkgg.cn/nnews/84223.htm
- http://m.3g.ghtkgg.cn/nnews/04688.htm
- http://m.3g.ghtkgg.cn/nnews/6432079.htm
- http://m.3g.ghtkgg.cn/nnews/3255562.htm
- http://m.3g.ghtkgg.cn/nnews/4433166.htm
- http://m.3g.ghtkgg.cn/nnews/359572.htm
- http://m.3g.ghtkgg.cn/nnews/2930862.htm
- http://m.3g.ghtkgg.cn/nnews/7532365.htm
- http://m.3g.ghtkgg.cn/nnews/3139681.htm
- http://m.3g.ghtkgg.cn/nnews/6803875.htm
- http://m.3g.ghtkgg.cn/nnews/7073.htm
- http://m.3g.ghtkgg.cn/nnews/2058983.htm
- http://m.3g.ghtkgg.cn/nnews/779303.htm
- http://m.3g.ghtkgg.cn/nnews/248087.htm
- http://m.3g.ghtkgg.cn/nnews/3038.htm
- http://m.3g.ghtkgg.cn/nnews/86068.htm
- http://m.3g.ghtkgg.cn/nnews/6463713.htm
- http://m.3g.ghtkgg.cn/nnews/373125.htm
- http://m.3g.ghtkgg.cn/nnews/6034.htm
- http://m.3g.ghtkgg.cn/nnews/2331646.htm
- http://m.3g.ghtkgg.cn/nnews/5248539.htm
- http://m.3g.ghtkgg.cn/nnews/3623.htm
- http://m.3g.ghtkgg.cn/nnews/446092.htm
- http://m.3g.ghtkgg.cn/nnews/6252257.htm
- http://m.3g.ghtkgg.cn/nnews/753608.htm
- http://m.3g.ghtkgg.cn/nnews/79287.htm
- http://m.3g.ghtkgg.cn/nnews/8394133.htm
- http://m.3g.ghtkgg.cn/nnews/8870555.htm
- http://m.3g.ghtkgg.cn/nnews/376108.htm
- http://m.3g.ghtkgg.cn/nnews/9850960.htm
- http://m.3g.ghtkgg.cn/nnews/70942.htm
- http://m.3g.ghtkgg.cn/nnews/31060.htm
- http://m.3g.ghtkgg.cn/nnews/594584.htm
- http://m.3g.ghtkgg.cn/nnews/1425.htm
- http://m.3g.ghtkgg.cn/nnews/4838342.htm
- http://m.3g.ghtkgg.cn/nnews/4433.htm
- http://m.3g.ghtkgg.cn/nnews/4598.htm
- http://m.3g.ghtkgg.cn/nnews/57223.htm
- http://m.3g.ghtkgg.cn/nnews/933868.htm
- http://m.3g.ghtkgg.cn/nnews/519466.htm
- http://m.3g.ghtkgg.cn/nnews/707309.htm
- http://m.3g.ghtkgg.cn/nnews/0426042.htm
- http://m.3g.ghtkgg.cn/nnews/2032.htm
- http://m.3g.ghtkgg.cn/nnews/375131.htm
- http://m.3g.ghtkgg.cn/nnews/67263.htm
- http://m.3g.ghtkgg.cn/nnews/8707427.htm
- http://m.3g.ghtkgg.cn/nnews/130006.htm
- http://m.3g.ghtkgg.cn/nnews/0549.htm
- http://m.3g.ghtkgg.cn/nnews/98154.htm
- http://m.3g.ghtkgg.cn/nnews/9428654.htm
- http://m.3g.ghtkgg.cn/nnews/2338.htm
- http://m.3g.ghtkgg.cn/nnews/56124.htm
- http://m.3g.ghtkgg.cn/nnews/77803.htm
- http://m.3g.ghtkgg.cn/nnews/848068.htm
- http://m.3g.ghtkgg.cn/nnews/5419.htm
- http://m.3g.ghtkgg.cn/nnews/376146.htm
- http://m.3g.ghtkgg.cn/nnews/454416.htm
- http://m.3g.ghtkgg.cn/nnews/094321.htm
- http://m.3g.ghtkgg.cn/nnews/571113.htm
- http://m.3g.ghtkgg.cn/nnews/3396261.htm
- http://m.3g.ghtkgg.cn/nnews/5940.htm
- http://m.3g.ghtkgg.cn/nnews/89820.htm
- http://m.3g.ghtkgg.cn/nnews/4300240.htm
- http://m.3g.ghtkgg.cn/nnews/3666.htm
- http://m.3g.ghtkgg.cn/nnews/88997.htm
- http://m.3g.ghtkgg.cn/nnews/4638870.htm
- http://m.3g.ghtkgg.cn/nnews/6305214.htm
- http://m.3g.ghtkgg.cn/nnews/4788.htm
- http://m.3g.ghtkgg.cn/nnews/05922.htm
- http://m.3g.ghtkgg.cn/nnews/5013475.htm
- http://m.3g.ghtkgg.cn/nnews/3813.htm
- http://m.3g.ghtkgg.cn/nnews/7827.htm
- http://m.3g.ghtkgg.cn/nnews/93244.htm
- http://m.3g.ghtkgg.cn/nnews/6622.htm
- http://m.3g.ghtkgg.cn/nnews/9999.htm
- http://m.3g.ghtkgg.cn/nnews/49547.htm
- http://m.3g.ghtkgg.cn/nnews/5424.htm
- http://m.3g.ghtkgg.cn/nnews/085964.htm
- http://m.3g.ghtkgg.cn/nnews/810222.htm
- http://m.3g.ghtkgg.cn/nnews/2352.htm
- http://m.3g.ghtkgg.cn/nnews/59965.htm
- http://m.3g.ghtkgg.cn/nnews/4133.htm
- http://m.3g.ghtkgg.cn/nnews/76305.htm
- http://m.3g.ghtkgg.cn/nnews/5553.htm
- http://m.3g.ghtkgg.cn/nnews/550156.htm
- http://m.3g.ghtkgg.cn/nnews/372730.htm
- http://m.3g.ghtkgg.cn/nnews/4708.htm
- http://m.3g.ghtkgg.cn/nnews/5856.htm
- http://m.3g.ghtkgg.cn/nnews/9918535.htm
- http://m.3g.ghtkgg.cn/nnews/35914.htm
- http://m.3g.ghtkgg.cn/nnews/5197250.htm
- http://m.3g.ghtkgg.cn/nnews/199427.htm
- http://m.3g.ghtkgg.cn/nnews/88776.htm
- http://m.3g.ghtkgg.cn/nnews/86173.htm
- http://m.3g.ghtkgg.cn/nnews/119440.htm
- http://m.3g.ghtkgg.cn/nnews/768151.htm
- http://m.3g.ghtkgg.cn/nnews/594264.htm
- http://m.3g.ghtkgg.cn/nnews/56966.htm
- http://m.3g.ghtkgg.cn/nnews/6146.htm
- http://m.3g.ghtkgg.cn/nnews/662176.htm
- http://m.3g.ghtkgg.cn/nnews/6590762.htm
- http://m.3g.ghtkgg.cn/nnews/6727.htm
- http://m.3g.ghtkgg.cn/nnews/3921864.htm
- http://m.3g.ghtkgg.cn/nnews/9940.htm
- http://m.3g.ghtkgg.cn/nnews/40184.htm
- http://m.3g.ghtkgg.cn/nnews/55906.htm
- http://m.3g.ghtkgg.cn/nnews/868074.htm
- http://m.3g.ghtkgg.cn/nnews/85794.htm
- http://m.3g.ghtkgg.cn/nnews/068496.htm
- http://m.3g.ghtkgg.cn/nnews/77404.htm
- http://m.3g.ghtkgg.cn/nnews/3026692.htm
- http://m.3g.ghtkgg.cn/nnews/097257.htm
- http://m.3g.ghtkgg.cn/nnews/679650.htm
- http://m.3g.ghtkgg.cn/nnews/8941658.htm
- http://m.3g.ghtkgg.cn/nnews/5072883.htm
- http://m.3g.ghtkgg.cn/nnews/4542.htm
- http://m.3g.ghtkgg.cn/nnews/0888472.htm
- http://m.3g.ghtkgg.cn/nnews/9090756.htm
- http://m.3g.ghtkgg.cn/nnews/3610.htm
- http://m.3g.ghtkgg.cn/nnews/7909065.htm
- http://m.3g.ghtkgg.cn/nnews/44889.htm
- http://m.3g.ghtkgg.cn/nnews/0913.htm
- http://m.3g.ghtkgg.cn/nnews/83838.htm
- http://m.3g.ghtkgg.cn/nnews/14940.htm
- http://m.3g.ghtkgg.cn/nnews/69323.htm
- http://m.3g.ghtkgg.cn/nnews/2230.htm
- http://m.3g.ghtkgg.cn/nnews/405701.htm
- http://m.3g.ghtkgg.cn/nnews/8777718.htm
- http://m.3g.ghtkgg.cn/nnews/134270.htm
- http://m.3g.ghtkgg.cn/nnews/35377.htm
- http://m.3g.ghtkgg.cn/nnews/1676137.htm
- http://m.3g.ghtkgg.cn/nnews/8306915.htm
- http://m.3g.ghtkgg.cn/nnews/84544.htm
- http://m.3g.ghtkgg.cn/nnews/310564.htm
- http://m.3g.ghtkgg.cn/nnews/6224415.htm
- http://m.3g.ghtkgg.cn/nnews/2232.htm
- http://m.3g.ghtkgg.cn/nnews/480399.htm
- http://m.3g.ghtkgg.cn/nnews/8420991.htm
- http://m.3g.ghtkgg.cn/nnews/47348.htm
- http://m.3g.ghtkgg.cn/nnews/5163.htm
- http://m.3g.ghtkgg.cn/nnews/95256.htm
- http://m.3g.ghtkgg.cn/nnews/5371.htm
- http://m.3g.ghtkgg.cn/nnews/370780.htm
- http://m.3g.ghtkgg.cn/nnews/153755.htm
- http://m.3g.ghtkgg.cn/nnews/068143.htm
- http://m.3g.ghtkgg.cn/nnews/0523.htm
- http://m.3g.ghtkgg.cn/nnews/094565.htm
- http://m.3g.ghtkgg.cn/nnews/4950868.htm
- http://m.3g.ghtkgg.cn/nnews/969274.htm
- http://m.3g.ghtkgg.cn/nnews/0666662.htm
- http://m.3g.ghtkgg.cn/nnews/0932059.htm
- http://m.3g.ghtkgg.cn/nnews/16056.htm
- http://m.3g.ghtkgg.cn/nnews/64067.htm
- http://m.3g.ghtkgg.cn/nnews/8509880.htm
- http://m.3g.ghtkgg.cn/nnews/078185.htm
- http://m.3g.ghtkgg.cn/nnews/251093.htm
- http://m.3g.ghtkgg.cn/nnews/221957.htm
- http://m.3g.ghtkgg.cn/nnews/088045.htm
- http://m.3g.ghtkgg.cn/nnews/4741663.htm
- http://m.3g.ghtkgg.cn/nnews/95724.htm
- http://m.3g.ghtkgg.cn/nnews/7277.htm
- http://m.3g.ghtkgg.cn/nnews/494960.htm
- http://m.3g.ghtkgg.cn/nnews/7547.htm
- http://m.3g.ghtkgg.cn/nnews/6499289.htm
- http://m.3g.ghtkgg.cn/nnews/4451.htm
- http://m.3g.ghtkgg.cn/nnews/6990078.htm
- http://m.3g.ghtkgg.cn/nnews/231087.htm
- http://m.3g.ghtkgg.cn/nnews/5488.htm
- http://m.3g.ghtkgg.cn/nnews/16494.htm
- http://m.3g.ghtkgg.cn/nnews/74227.htm
- http://m.3g.ghtkgg.cn/nnews/50509.htm
- http://m.3g.ghtkgg.cn/nnews/8039323.htm
- http://m.3g.ghtkgg.cn/nnews/8430127.htm
- http://m.3g.ghtkgg.cn/nnews/09988.htm
- http://m.3g.ghtkgg.cn/nnews/5292.htm
- http://m.3g.ghtkgg.cn/nnews/9958657.htm
- http://m.3g.ghtkgg.cn/nnews/4518457.htm
- http://m.3g.ghtkgg.cn/nnews/55961.htm
- http://m.3g.ghtkgg.cn/nnews/456492.htm
- http://m.3g.ghtkgg.cn/nnews/154262.htm
- http://m.3g.ghtkgg.cn/nnews/31158.htm
- http://m.3g.ghtkgg.cn/nnews/9066602.htm
- http://m.3g.ghtkgg.cn/nnews/0587.htm
- http://m.3g.ghtkgg.cn/nnews/02610.htm
- http://m.3g.ghtkgg.cn/nnews/1017.htm
- http://m.3g.ghtkgg.cn/nnews/50859.htm
- http://m.3g.ghtkgg.cn/nnews/04714.htm
- http://m.3g.ghtkgg.cn/nnews/98150.htm
- http://m.3g.ghtkgg.cn/nnews/8321.htm
- http://m.3g.ghtkgg.cn/nnews/69882.htm
- http://m.3g.ghtkgg.cn/nnews/4551251.htm
- http://m.3g.ghtkgg.cn/nnews/7791.htm
- http://m.3g.ghtkgg.cn/nnews/5882556.htm
- http://m.3g.ghtkgg.cn/nnews/2990.htm
- http://m.3g.ghtkgg.cn/nnews/17134.htm
- http://m.3g.ghtkgg.cn/nnews/0805.htm
- http://m.3g.ghtkgg.cn/nnews/95271.htm
- http://m.3g.ghtkgg.cn/nnews/18288.htm
- http://m.3g.ghtkgg.cn/nnews/53236.htm
- http://m.3g.ghtkgg.cn/nnews/1791.htm
- http://m.3g.ghtkgg.cn/nnews/305723.htm
- http://m.3g.ghtkgg.cn/nnews/4682.htm
- http://m.3g.ghtkgg.cn/nnews/8966523.htm
- http://m.3g.ghtkgg.cn/nnews/7098.htm
- http://m.3g.ghtkgg.cn/nnews/0445990.htm
- http://m.3g.ghtkgg.cn/nnews/4971.htm
- http://m.3g.ghtkgg.cn/nnews/0015068.htm
- http://m.3g.ghtkgg.cn/nnews/29971.htm
- http://m.3g.ghtkgg.cn/nnews/8706.htm
- http://m.3g.ghtkgg.cn/nnews/2027270.htm
- http://m.3g.ghtkgg.cn/nnews/2604.htm
- http://m.3g.ghtkgg.cn/nnews/5230.htm
- http://m.3g.ghtkgg.cn/nnews/339242.htm
- http://m.3g.ghtkgg.cn/nnews/25839.htm
- http://m.3g.ghtkgg.cn/nnews/201767.htm
- http://m.3g.ghtkgg.cn/nnews/70809.htm

## 项目结构

```
news-aggregator/
├── cli.py                  # 命令行入口，解析用户参数并调度采集、导出、检查等子命令
├── config.yaml             # 主配置文件，定义目标源列表、过滤规则、并发数及日志级别
├── requirements.txt        # Python 依赖清单，锁定所有第三方库版本号
├── src/                    # 核心源码目录
│   ├── core/               # 核心引擎模块
│   │   ├── collector.py    # 采集器实现，负责链接提取与页面抓取
│   │   ├── parser.py       # 解析器基类及 HTML 结构化数据提取逻辑
│   │   └── scheduler.py    # 任务调度器，管理增量更新与定时执行
│   ├── utils/              # 工具函数集
│   │   ├── http_client.py  # 异步 HTTP 客户端封装，含重试与代理支持
│   │   ├── filters.py      # 过滤规则引擎，支持正则、关键词及黑白名单
│   │   └── exporters.py    # 数据导出器，支持 JSON, CSV, SQLite 格式
│   ├── models/             # 数据模型定义
│   │   ├── link.py         # Link 实体类，包含 URL、标题、发布时间、状态码等字段
│   │   └── task.py         # Task 实体类，记录采集任务参数与执行状态
│   └── storage/            # 持久化层
│       ├── database.py     # SQLite 数据库连接与 ORM 映射
│       └── cache.py        # 内存缓存与 Redis 适配器，用于去重加速
├── tests/                  # 测试套件
│   ├── unit/               # 单元测试用例
│   └── integration/        # 集成测试，验证端到端采集流程
├── docs/                   # 文档目录
│   ├── quickstart.md       # 快速入门指南
│   ├── configuration.md    # 配置参数详解
│   ├── api_reference.md    # RESTful API 接口文档
│   └── development.md      # 开发环境搭建与贡献规范
├── scripts/                # 运维辅助脚本
│   ├── setup_db.sh         # 初始化数据库表结构
│   └── clean_links.py      # 清理过期或无效链接的维护脚本
└── LICENSE                 # MIT 许可证文件
```

## 贡献指南

开发者需遵循以下流程参与项目贡献，确保代码质量与协作效率。

首先，在 GitHub 上 Fork 本仓库至个人命名空间，并将 Fork 后的仓库克隆至本地开发环境。建议在开发前创建独立的功能分支，分支命名遵循 `feature/` 或 `fix/` 前缀加简要描述，例如 `feature/add-xpath-parser`。

其次，本地开发需通过 `pytest` 运行全部单元测试与集成测试，确保新增代码未破坏既有功能。所有对外接口或核心逻辑变更应同步更新对应的文档模块，包括 docstring 与 docs/ 目录下的 Markdown 文件。

完成功能开发后，提交代码需遵循语义化提交规范，提交信息格式为 `<type>(<scope>): <subject>`，其中 type 包括 feat, fix, docs, style, refactor, test, chore。提交前需通过 pre-commit 钩子进行代码格式检查。

最后，向主仓库的 develop 分支发起 Pull Request，PR 描述中需明确说明改动目的、实现方案及测试覆盖情况。至少一位项目维护者审核通过后方可合并。重大功能更新或破坏性变更需提前在 Issue 中讨论并获得共识。

## 常见问题

**问：采集任务运行时出现大量超时错误，应如何优化？**

答：超时错误通常由目标服务器响应缓慢或网络波动引起。建议首先调整 config.yaml 中的 timeout 参数（默认 10 秒），可适当增加至 30 秒。同时降低并发数 concurrency 避免对目标服务器造成过大压力。若问题持续，可启用代理列表功能，通过 proxy_rotation 配置项轮换出口 IP。对于持续不可达的链接，系统会自动记录并跳过，不影响整体任务进度。

**问：如何自定义新闻链接的解析规则，以适配不同的目标站点？**

答：项目内置了基于通用 DOM 结构的解析器，但对于结构特殊的站点，用户可继承 src/core/parser.py 中的 BaseParser 类，重写 parse_links 和 parse_metadata 方法。在新类中可使用 XPath 或 CSS 选择器定位特定元素。完成自定义解析器后，需在 config.yaml 的 parsers 映射中注册该站点域名与对应解析器类的路径，系统将在采集时自动加载。

**问：数据导出时能否按时间范围筛选，只导出最近一周的链接？**

答：支持通过命令行参数进行时间范围过滤。在执行导出命令时，添加 --start-date 和 --end-date 选项，格式为 YYYY-MM-DD，例如 `python cli.py export --format json --start-date 2026-08-18` 将仅导出该日期之后采集的链接。若需在配置文件中预设默认过滤条件，可在 config.yaml 的 export 章节下设置 default_date_range 字段。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:54
