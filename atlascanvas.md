# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端资讯聚合与深度内容导航的开源工具集，专注于从 m.wap.ghtkgg.cn 域名下批量采集、解析和归档新闻类页面资源。项目定位为技术研究辅助与内容索引系统，帮助开发者、数据分析师和内容运营人员高效提取结构化新闻条目，构建自定义的资讯流或历史数据回溯通道。

目标用户包括需要定期抓取垂直领域新闻的爬虫开发者、对特定编号区间新闻内容进行统计分析的舆情研究员，以及希望快速搭建新闻推荐系统原型的数据科学团队。本仓库不提供新闻内容本身，而是提供一套可复用的索引清单和配套解析脚手架，让用户能够以标准化方式访问这批共 300 个新闻资源地址。

## 功能概览

批量资源索引管理：提供固定批次共 300 个新闻页面 URL 的清单，所有链接均以原始格式存储，支持按编号、日期或状态进行筛选与导出。

轻量级页面抓取模板：内置基于 Python 的请求与解析示例代码，演示如何从 m.wap.ghtkgg.cn 域名下批量获取 HTML 内容并提取标题、发布时间与正文摘要。

结构化元数据抽取：针对新闻类页面常见 DOM 结构设计可配置的选择器，支持将半结构化网页内容转换为 JSON 格式的元数据记录。

去重与增量更新机制：记录已抓取 URL 的哈希指纹，避免重复处理相同编号的新闻页面，适用于定期增量执行的任务流。

异常重试与日志记录：集成网络请求失败自动重试策略（默认 3 次退避重试），并输出分级日志文件，便于排查链接失效或解析异常。

可扩展输出格式：支持将解析结果输出为 CSV、JSON Lines 或 SQLite 数据库文件，适配不同下游数据处理工具链。

命令行与配置文件双模式：既可通过命令行参数直接指定批次范围和输出路径，也可通过 YAML 配置文件设置抓取频率、并发数等高级选项。

## 应用场景

周期性新闻摘要生成：运营人员可配置每日定时任务，抓取最新一批新闻链接的标题和摘要，自动生成邮件简报或站内公告列表，减少人工复制粘贴的工作量。

历史链接有效性审计：当上游新闻站点调整域名或路径规则时，利用本索引清单批量检测链接响应状态码，快速定位已失效或重定向的页面，及时更新对外引用。

垂直领域舆情数据集构建：研究人员将这批新闻编号视为样本池，结合外部 NLP 工具对抓取到的正文进行分词、情感分析和主题建模，形成针对特定行业或地域的舆情变化趋势报告。

多源新闻聚合原型验证：开发者可直接复用本项目的 URL 列表作为种子数据，快速搭建一个简单的新闻聚合器前端原型，验证界面布局和缓存策略，无需从零开始收集测试链接。

## 快速开始

```bash
# 克隆仓库到本地
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator

# 安装所需依赖（建议使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install requests beautifulsoup4 lxml pandas

# 运行示例抓取脚本，将输出结果保存至 output/ 目录
python scripts/fetch_batch.py --batch 144 --output-dir ./output --format json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 或更高 | 核心脚本运行环境，低于此版本可能不支持类型注解语法 |
| requests | 2.25.0+ | 发送 HTTP 请求获取页面内容，处理重定向和超时 |
| beautifulsoup4 | 4.9.0+ | 解析 HTML 文档，提取标题、正文等元素 |
| lxml | 4.6.0+ | 作为 beautifulsoup4 的解析器，提高解析速度和容错性 |
| pandas | 1.2.0+ | 仅用于输出 DataFrame 格式数据，若使用 JSON 输出可跳过 |
| pytest | 6.0.0+ | 可选，用于运行单元测试验证选择器配置正确性 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | docs/usage.md | 如何配置抓取参数、调整输出格式、处理认证和代理 |
| 开发者指南 | docs/development.md | 如何扩展新的解析器、添加自定义字段、编写单元测试 |
| 架构说明 | docs/architecture.md | 项目模块划分、数据流向、缓存策略和异常处理链路 |
| API 参考 | docs/api_reference.md | 核心类和函数的签名、参数说明及调用示例 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/669727.htm
- http://m.wap.ghtkgg.cn/jnews/787717.htm
- http://m.wap.ghtkgg.cn/jnews/7846.htm
- http://m.wap.ghtkgg.cn/jnews/7432319.htm
- http://m.wap.ghtkgg.cn/jnews/176799.htm
- http://m.wap.ghtkgg.cn/jnews/7275.htm
- http://m.wap.ghtkgg.cn/jnews/4393010.htm
- http://m.wap.ghtkgg.cn/jnews/9041.htm
- http://m.wap.ghtkgg.cn/jnews/8069139.htm
- http://m.wap.ghtkgg.cn/jnews/054574.htm
- http://m.wap.ghtkgg.cn/jnews/25394.htm
- http://m.wap.ghtkgg.cn/jnews/04547.htm
- http://m.wap.ghtkgg.cn/jnews/4000386.htm
- http://m.wap.ghtkgg.cn/jnews/5362817.htm
- http://m.wap.ghtkgg.cn/jnews/44241.htm
- http://m.wap.ghtkgg.cn/jnews/25481.htm
- http://m.wap.ghtkgg.cn/jnews/435757.htm
- http://m.wap.ghtkgg.cn/jnews/840232.htm
- http://m.wap.ghtkgg.cn/jnews/2162782.htm
- http://m.wap.ghtkgg.cn/jnews/2746.htm
- http://m.wap.ghtkgg.cn/jnews/686050.htm
- http://m.wap.ghtkgg.cn/jnews/3860261.htm
- http://m.wap.ghtkgg.cn/jnews/8022519.htm
- http://m.wap.ghtkgg.cn/jnews/415186.htm
- http://m.wap.ghtkgg.cn/jnews/24466.htm
- http://m.wap.ghtkgg.cn/jnews/35707.htm
- http://m.wap.ghtkgg.cn/jnews/672511.htm
- http://m.wap.ghtkgg.cn/jnews/7481.htm
- http://m.wap.ghtkgg.cn/jnews/685112.htm
- http://m.wap.ghtkgg.cn/jnews/756275.htm
- http://m.wap.ghtkgg.cn/jnews/9053.htm
- http://m.wap.ghtkgg.cn/jnews/00058.htm
- http://m.wap.ghtkgg.cn/jnews/22575.htm
- http://m.wap.ghtkgg.cn/jnews/4423950.htm
- http://m.wap.ghtkgg.cn/jnews/302209.htm
- http://m.wap.ghtkgg.cn/jnews/46734.htm
- http://m.wap.ghtkgg.cn/jnews/39862.htm
- http://m.wap.ghtkgg.cn/jnews/254967.htm
- http://m.wap.ghtkgg.cn/jnews/52846.htm
- http://m.wap.ghtkgg.cn/jnews/41941.htm
- http://m.wap.ghtkgg.cn/jnews/2427936.htm
- http://m.wap.ghtkgg.cn/jnews/08111.htm
- http://m.wap.ghtkgg.cn/jnews/81597.htm
- http://m.wap.ghtkgg.cn/jnews/3182377.htm
- http://m.wap.ghtkgg.cn/jnews/1114.htm
- http://m.wap.ghtkgg.cn/jnews/40156.htm
- http://m.wap.ghtkgg.cn/jnews/88294.htm
- http://m.wap.ghtkgg.cn/jnews/3199673.htm
- http://m.wap.ghtkgg.cn/jnews/0324535.htm
- http://m.wap.ghtkgg.cn/jnews/132114.htm
- http://m.wap.ghtkgg.cn/jnews/1805548.htm
- http://m.wap.ghtkgg.cn/jnews/542112.htm
- http://m.wap.ghtkgg.cn/jnews/89061.htm
- http://m.wap.ghtkgg.cn/jnews/34913.htm
- http://m.wap.ghtkgg.cn/jnews/720907.htm
- http://m.wap.ghtkgg.cn/jnews/572186.htm
- http://m.wap.ghtkgg.cn/jnews/4232.htm
- http://m.wap.ghtkgg.cn/jnews/78568.htm
- http://m.wap.ghtkgg.cn/jnews/5542409.htm
- http://m.wap.ghtkgg.cn/jnews/6614.htm
- http://m.wap.ghtkgg.cn/jnews/713348.htm
- http://m.wap.ghtkgg.cn/jnews/69226.htm
- http://m.wap.ghtkgg.cn/jnews/222532.htm
- http://m.wap.ghtkgg.cn/jnews/7200.htm
- http://m.wap.ghtkgg.cn/jnews/99953.htm
- http://m.wap.ghtkgg.cn/jnews/72670.htm
- http://m.wap.ghtkgg.cn/jnews/5512711.htm
- http://m.wap.ghtkgg.cn/jnews/6635.htm
- http://m.wap.ghtkgg.cn/jnews/430473.htm
- http://m.wap.ghtkgg.cn/jnews/128027.htm
- http://m.wap.ghtkgg.cn/jnews/84798.htm
- http://m.wap.ghtkgg.cn/jnews/9853852.htm
- http://m.wap.ghtkgg.cn/jnews/098687.htm
- http://m.wap.ghtkgg.cn/jnews/5400.htm
- http://m.wap.ghtkgg.cn/jnews/883526.htm
- http://m.wap.ghtkgg.cn/jnews/132530.htm
- http://m.wap.ghtkgg.cn/jnews/54849.htm
- http://m.wap.ghtkgg.cn/jnews/90463.htm
- http://m.wap.ghtkgg.cn/jnews/96864.htm
- http://m.wap.ghtkgg.cn/jnews/4758.htm
- http://m.wap.ghtkgg.cn/jnews/9635.htm
- http://m.wap.ghtkgg.cn/jnews/56303.htm
- http://m.wap.ghtkgg.cn/jnews/5965734.htm
- http://m.wap.ghtkgg.cn/jnews/262289.htm
- http://m.wap.ghtkgg.cn/jnews/4917744.htm
- http://m.wap.ghtkgg.cn/jnews/4590104.htm
- http://m.wap.ghtkgg.cn/jnews/062818.htm
- http://m.wap.ghtkgg.cn/jnews/243972.htm
- http://m.wap.ghtkgg.cn/jnews/0528663.htm
- http://m.wap.ghtkgg.cn/jnews/4364167.htm
- http://m.wap.ghtkgg.cn/jnews/8742.htm
- http://m.wap.ghtkgg.cn/jnews/17478.htm
- http://m.wap.ghtkgg.cn/jnews/230322.htm
- http://m.wap.ghtkgg.cn/jnews/5946.htm
- http://m.wap.ghtkgg.cn/jnews/98429.htm
- http://m.wap.ghtkgg.cn/jnews/6022.htm
- http://m.wap.ghtkgg.cn/jnews/4414.htm
- http://m.wap.ghtkgg.cn/jnews/5060.htm
- http://m.wap.ghtkgg.cn/jnews/50420.htm
- http://m.wap.ghtkgg.cn/jnews/0328600.htm
- http://m.wap.ghtkgg.cn/jnews/4191.htm
- http://m.wap.ghtkgg.cn/jnews/152749.htm
- http://m.wap.ghtkgg.cn/jnews/5332.htm
- http://m.wap.ghtkgg.cn/jnews/28702.htm
- http://m.wap.ghtkgg.cn/jnews/5509773.htm
- http://m.wap.ghtkgg.cn/jnews/9545059.htm
- http://m.wap.ghtkgg.cn/jnews/947945.htm
- http://m.wap.ghtkgg.cn/jnews/0369492.htm
- http://m.wap.ghtkgg.cn/jnews/0326.htm
- http://m.wap.ghtkgg.cn/jnews/44861.htm
- http://m.wap.ghtkgg.cn/jnews/6774512.htm
- http://m.wap.ghtkgg.cn/jnews/12839.htm
- http://m.wap.ghtkgg.cn/jnews/01969.htm
- http://m.wap.ghtkgg.cn/jnews/9445.htm
- http://m.wap.ghtkgg.cn/jnews/7506315.htm
- http://m.wap.ghtkgg.cn/jnews/2460139.htm
- http://m.wap.ghtkgg.cn/jnews/0989287.htm
- http://m.wap.ghtkgg.cn/jnews/2066.htm
- http://m.wap.ghtkgg.cn/jnews/6083.htm
- http://m.wap.ghtkgg.cn/jnews/722888.htm
- http://m.wap.ghtkgg.cn/jnews/16413.htm
- http://m.wap.ghtkgg.cn/jnews/60383.htm
- http://m.wap.ghtkgg.cn/jnews/829288.htm
- http://m.wap.ghtkgg.cn/jnews/502724.htm
- http://m.wap.ghtkgg.cn/jnews/7095240.htm
- http://m.wap.ghtkgg.cn/jnews/10157.htm
- http://m.wap.ghtkgg.cn/jnews/69202.htm
- http://m.wap.ghtkgg.cn/jnews/6818969.htm
- http://m.wap.ghtkgg.cn/jnews/0901005.htm
- http://m.wap.ghtkgg.cn/jnews/3957971.htm
- http://m.wap.ghtkgg.cn/jnews/8728.htm
- http://m.wap.ghtkgg.cn/jnews/0674.htm
- http://m.wap.ghtkgg.cn/jnews/8612688.htm
- http://m.wap.ghtkgg.cn/jnews/05921.htm
- http://m.wap.ghtkgg.cn/jnews/445916.htm
- http://m.wap.ghtkgg.cn/jnews/14618.htm
- http://m.wap.ghtkgg.cn/jnews/438255.htm
- http://m.wap.ghtkgg.cn/jnews/336531.htm
- http://m.wap.ghtkgg.cn/jnews/93582.htm
- http://m.wap.ghtkgg.cn/jnews/697309.htm
- http://m.wap.ghtkgg.cn/jnews/32290.htm
- http://m.wap.ghtkgg.cn/jnews/3514991.htm
- http://m.wap.ghtkgg.cn/jnews/6207.htm
- http://m.wap.ghtkgg.cn/jnews/45732.htm
- http://m.wap.ghtkgg.cn/jnews/429718.htm
- http://m.wap.ghtkgg.cn/jnews/333935.htm
- http://m.wap.ghtkgg.cn/jnews/961693.htm
- http://m.wap.ghtkgg.cn/jnews/33818.htm
- http://m.wap.ghtkgg.cn/jnews/04953.htm
- http://m.wap.ghtkgg.cn/jnews/1940587.htm
- http://m.wap.ghtkgg.cn/jnews/11563.htm
- http://m.wap.ghtkgg.cn/jnews/6288852.htm
- http://m.wap.ghtkgg.cn/jnews/932659.htm
- http://m.wap.ghtkgg.cn/jnews/74792.htm
- http://m.wap.ghtkgg.cn/jnews/6611.htm
- http://m.wap.ghtkgg.cn/jnews/024025.htm
- http://m.wap.ghtkgg.cn/jnews/1733.htm
- http://m.wap.ghtkgg.cn/jnews/0275.htm
- http://m.wap.ghtkgg.cn/jnews/924778.htm
- http://m.wap.ghtkgg.cn/jnews/8016279.htm
- http://m.wap.ghtkgg.cn/jnews/9338.htm
- http://m.wap.ghtkgg.cn/jnews/198082.htm
- http://m.wap.ghtkgg.cn/jnews/580784.htm
- http://m.wap.ghtkgg.cn/jnews/9299.htm
- http://m.wap.ghtkgg.cn/jnews/02139.htm
- http://m.wap.ghtkgg.cn/jnews/28248.htm
- http://m.wap.ghtkgg.cn/jnews/222399.htm
- http://m.wap.ghtkgg.cn/jnews/64747.htm
- http://m.wap.ghtkgg.cn/jnews/8618.htm
- http://m.wap.ghtkgg.cn/jnews/9272.htm
- http://m.wap.ghtkgg.cn/jnews/740290.htm
- http://m.wap.ghtkgg.cn/jnews/9292.htm
- http://m.wap.ghtkgg.cn/jnews/533894.htm
- http://m.wap.ghtkgg.cn/jnews/59011.htm
- http://m.wap.ghtkgg.cn/jnews/72241.htm
- http://m.wap.ghtkgg.cn/jnews/9995703.htm
- http://m.wap.ghtkgg.cn/jnews/82378.htm
- http://m.wap.ghtkgg.cn/jnews/97196.htm
- http://m.wap.ghtkgg.cn/jnews/8206.htm
- http://m.wap.ghtkgg.cn/jnews/1971.htm
- http://m.wap.ghtkgg.cn/jnews/3323.htm
- http://m.wap.ghtkgg.cn/jnews/1617.htm
- http://m.wap.ghtkgg.cn/jnews/13686.htm
- http://m.wap.ghtkgg.cn/jnews/6027.htm
- http://m.wap.ghtkgg.cn/jnews/30274.htm
- http://m.wap.ghtkgg.cn/jnews/5520941.htm
- http://m.wap.ghtkgg.cn/jnews/0468.htm
- http://m.wap.ghtkgg.cn/jnews/34214.htm
- http://m.wap.ghtkgg.cn/jnews/817611.htm
- http://m.wap.ghtkgg.cn/jnews/8212.htm
- http://m.wap.ghtkgg.cn/jnews/0069617.htm
- http://m.wap.ghtkgg.cn/jnews/12657.htm
- http://m.wap.ghtkgg.cn/jnews/92595.htm
- http://m.wap.ghtkgg.cn/jnews/2022.htm
- http://m.wap.ghtkgg.cn/jnews/50197.htm
- http://m.wap.ghtkgg.cn/jnews/5024283.htm
- http://m.wap.ghtkgg.cn/jnews/6803.htm
- http://m.wap.ghtkgg.cn/jnews/55838.htm
- http://m.wap.ghtkgg.cn/jnews/0340836.htm
- http://m.wap.ghtkgg.cn/jnews/839289.htm
- http://m.wap.ghtkgg.cn/jnews/62903.htm
- http://m.wap.ghtkgg.cn/jnews/33640.htm
- http://m.wap.ghtkgg.cn/jnews/1637.htm
- http://m.wap.ghtkgg.cn/jnews/720940.htm
- http://m.wap.ghtkgg.cn/jnews/7495956.htm
- http://m.wap.ghtkgg.cn/jnews/963186.htm
- http://m.wap.ghtkgg.cn/jnews/8407.htm
- http://m.wap.ghtkgg.cn/jnews/119077.htm
- http://m.wap.ghtkgg.cn/jnews/14744.htm
- http://m.wap.ghtkgg.cn/jnews/7266.htm
- http://m.wap.ghtkgg.cn/jnews/032965.htm
- http://m.wap.ghtkgg.cn/jnews/49727.htm
- http://m.wap.ghtkgg.cn/jnews/6204021.htm
- http://m.wap.ghtkgg.cn/jnews/578614.htm
- http://m.wap.ghtkgg.cn/jnews/1531383.htm
- http://m.wap.ghtkgg.cn/jnews/31137.htm
- http://m.wap.ghtkgg.cn/jnews/5842.htm
- http://m.wap.ghtkgg.cn/jnews/51769.htm
- http://m.wap.ghtkgg.cn/jnews/42521.htm
- http://m.wap.ghtkgg.cn/jnews/66923.htm
- http://m.wap.ghtkgg.cn/jnews/129051.htm
- http://m.wap.ghtkgg.cn/jnews/247869.htm
- http://m.wap.ghtkgg.cn/jnews/06697.htm
- http://m.wap.ghtkgg.cn/jnews/70899.htm
- http://m.wap.ghtkgg.cn/jnews/3938.htm
- http://m.wap.ghtkgg.cn/jnews/4932.htm
- http://m.wap.ghtkgg.cn/jnews/1855.htm
- http://m.wap.ghtkgg.cn/jnews/8487.htm
- http://m.wap.ghtkgg.cn/jnews/1288.htm
- http://m.wap.ghtkgg.cn/jnews/5615.htm
- http://m.wap.ghtkgg.cn/jnews/1947708.htm
- http://m.wap.ghtkgg.cn/jnews/0483.htm
- http://m.wap.ghtkgg.cn/jnews/674249.htm
- http://m.wap.ghtkgg.cn/jnews/6704.htm
- http://m.wap.ghtkgg.cn/jnews/3021232.htm
- http://m.wap.ghtkgg.cn/jnews/96903.htm
- http://m.wap.ghtkgg.cn/jnews/8765441.htm
- http://m.wap.ghtkgg.cn/jnews/4547617.htm
- http://m.wap.ghtkgg.cn/jnews/07343.htm
- http://m.wap.ghtkgg.cn/jnews/8629796.htm
- http://m.wap.ghtkgg.cn/jnews/744590.htm
- http://m.wap.ghtkgg.cn/jnews/333369.htm
- http://m.wap.ghtkgg.cn/jnews/3682.htm
- http://m.wap.ghtkgg.cn/jnews/201802.htm
- http://m.wap.ghtkgg.cn/jnews/03696.htm
- http://m.wap.ghtkgg.cn/jnews/7117.htm
- http://m.wap.ghtkgg.cn/jnews/8355209.htm
- http://m.wap.ghtkgg.cn/jnews/233244.htm
- http://m.wap.ghtkgg.cn/jnews/442062.htm
- http://m.wap.ghtkgg.cn/jnews/602477.htm
- http://m.wap.ghtkgg.cn/jnews/6285047.htm
- http://m.wap.ghtkgg.cn/jnews/3150.htm
- http://m.wap.ghtkgg.cn/jnews/6103557.htm
- http://m.wap.ghtkgg.cn/jnews/6690148.htm
- http://m.wap.ghtkgg.cn/jnews/1217.htm
- http://m.wap.ghtkgg.cn/jnews/2593689.htm
- http://m.wap.ghtkgg.cn/jnews/4885.htm
- http://m.wap.ghtkgg.cn/jnews/913818.htm
- http://m.wap.ghtkgg.cn/jnews/327901.htm
- http://m.wap.ghtkgg.cn/jnews/59973.htm
- http://m.wap.ghtkgg.cn/jnews/9297018.htm
- http://m.wap.ghtkgg.cn/jnews/47747.htm
- http://m.wap.ghtkgg.cn/jnews/45278.htm
- http://m.wap.ghtkgg.cn/jnews/0683714.htm
- http://m.wap.ghtkgg.cn/jnews/1130166.htm
- http://m.wap.ghtkgg.cn/jnews/85610.htm
- http://m.wap.ghtkgg.cn/jnews/5227.htm
- http://m.wap.ghtkgg.cn/jnews/621258.htm
- http://m.wap.ghtkgg.cn/jnews/51517.htm
- http://m.wap.ghtkgg.cn/jnews/194891.htm
- http://m.wap.ghtkgg.cn/jnews/5318.htm
- http://m.wap.ghtkgg.cn/jnews/8457020.htm
- http://m.wap.ghtkgg.cn/jnews/9609177.htm
- http://m.wap.ghtkgg.cn/jnews/477001.htm
- http://m.wap.ghtkgg.cn/jnews/5998.htm
- http://m.wap.ghtkgg.cn/jnews/9318909.htm
- http://m.wap.ghtkgg.cn/jnews/078965.htm
- http://m.wap.ghtkgg.cn/jnews/06458.htm
- http://m.wap.ghtkgg.cn/jnews/74270.htm
- http://m.wap.ghtkgg.cn/jnews/6903.htm
- http://m.wap.ghtkgg.cn/jnews/43241.htm
- http://m.wap.ghtkgg.cn/jnews/0739692.htm
- http://m.wap.ghtkgg.cn/jnews/6920189.htm
- http://m.wap.ghtkgg.cn/jnews/059773.htm
- http://m.wap.ghtkgg.cn/jnews/0614897.htm
- http://m.wap.ghtkgg.cn/jnews/9750.htm
- http://m.wap.ghtkgg.cn/jnews/9348.htm
- http://m.wap.ghtkgg.cn/jnews/75007.htm
- http://m.wap.ghtkgg.cn/jnews/971670.htm
- http://m.wap.ghtkgg.cn/jnews/5434.htm
- http://m.wap.ghtkgg.cn/jnews/796519.htm
- http://m.wap.ghtkgg.cn/jnews/443873.htm
- http://m.wap.ghtkgg.cn/jnews/5924.htm
- http://m.wap.ghtkgg.cn/jnews/5238.htm
- http://m.wap.ghtkgg.cn/jnews/8263.htm
- http://m.wap.ghtkgg.cn/jnews/3388.htm
- http://m.wap.ghtkgg.cn/jnews/122700.htm
- http://m.wap.ghtkgg.cn/jnews/2950529.htm
- http://m.wap.ghtkgg.cn/jnews/396696.htm
- http://m.wap.ghtkgg.cn/jnews/419572.htm

## 项目结构

```
jnews-link-aggregator/
├── README.md                        # 项目总览与快速入门
├── LICENSE                          # MIT 许可证文件
├── requirements.txt                 # Python 依赖列表（requests, bs4, lxml, pandas）
├── setup.py                         # 安装脚本，支持 pip install -e .
├── config/
│   ├── default.yaml                 # 默认抓取配置（并发数、超时、重试次数）
│   └── schema.json                  # 输出元数据 JSON Schema 定义
├── scripts/
│   ├── fetch_batch.py               # 主入口脚本，按批次抓取并输出结果
│   ├── deduplicate.py               # 基于 URL 哈希的增量去重工具
│   └── export_to_db.py              # 将 CSV/JSON 结果导入 SQLite 数据库
├── src/
│   ├── __init__.py
│   ├── fetcher.py                   # 封装 requests 会话与重试逻辑
│   ├── parser.py                    # 针对 m.wap.ghtkgg.cn 的新闻页解析器
│   ├── pipeline.py                  # 抓取-解析-输出流水线编排
│   └── utils.py                     # 日志、文件操作、哈希计算等辅助函数
├── tests/
│   ├── test_fetcher.py              # 模拟网络请求的单元测试
│   ├── test_parser.py               # 使用本地 HTML 样本验证解析规则
│   └── fixtures/
│       └── sample_news.html         # 固定的测试用新闻页面片段
├── docs/                            # 详细文档目录（见文档导航章节）
│   ├── usage.md
│   ├── development.md
│   ├── architecture.md
│   └── api_reference.md
└── output/                          # 默认输出目录（脚本自动创建）
    ├── batch_144.json
    ├── batch_144.csv
    └── logs/
        └── fetch_2026-08-25.log
```

## 贡献指南

贡献者请先阅读 docs/development.md 了解整体架构和编码规范，然后按照以下步骤提交变更。

提交 Issue 报告问题：在 GitHub Issues 页面选择对应的模板（Bug 报告或功能请求），详细描述复现步骤、环境信息和预期行为，并附上相关日志片段。

创建功能分支：从 main 分支签出新的分支，分支命名遵循 feature/xxx 或 fix/xxx 格式，确保分支名称简要概括改动内容。

编写或更新单元测试：所有新增的解析逻辑或网络处理函数必须附带对应的测试用例，测试覆盖率不低于 80%。运行 pytest 确保现有测试全部通过。

更新文档和示例：若修改了配置文件结构或命令行参数，同步更新 docs/usage.md 和 README 中的快速开始部分。添加新的解析字段时，需在 schema.json 中补充定义。

提交 Pull Request：推送分支后，在 GitHub 上创建 Pull Request，填写变更摘要、测试结果和影响范围。至少需要一名维护者审核通过后方可合并。

## 常见问题

问题：抓取脚本返回大量 HTTP 403 状态码，如何解决？

回答：m.wap.ghtkgg.cn 可能对 User-Agent 或 Referer 头有校验。请在 config/default.yaml 中更新 headers 字段，将 User-Agent 设置为常见移动端浏览器值，例如 Mozilla/5.0 (Linux; Android 11; SM-G960F) AppleWebKit/537.36。同时检查请求频率是否过高，建议将并发数调整为 1 并增加 sleep_interval 配置项。

问题：解析器无法提取到某些页面的标题，输出文件中 title 字段为空。

回答：不同编号的新闻页面可能使用略有差异的 DOM 结构。请使用浏览器开发者工具查看对应页面的实际 HTML，定位标题所在元素的选择器，然后在 src/parser.py 的 TITLE_SELECTORS 列表中添加新的选择器优先级。修改后运行 tests/test_parser.py 验证是否所有样本页面都能正确提取。

问题：如何只抓取特定编号范围的新闻链接，而不是全部 300 个？

回答：执行 fetch_batch.py 时可以使用 --start 和 --end 参数指定编号区间，例如 python scripts/fetch_batch.py --start 1000 --end 2000。参数值对应 URL 中 /jnews/ 后面的数字部分。若不指定区间，则默认处理资源列表中的所有链接。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
