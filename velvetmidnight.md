# JNews Resource Aggregator

JNews Resource Aggregator 是一个面向移动端新闻资讯聚合与内容索引的开源工具集，专注于对特定新闻源的结构化采集、链接管理和内容元数据提取。该项目主要服务于需要批量处理新闻链接、构建自定义新闻流或进行轻量级内容分析的个人开发者、研究人员及小型内容团队。

项目核心定位为技术资源与外链汇总中间件，不提供完整的新闻阅读客户端，而是提供一组可组合的脚本与配置模板，帮助用户快速将分散的新闻条目链接转化为可查询、可过滤、可导出的结构化数据集。通过统一的数据管道设计，用户能够将原始链接列表与标题、发布时间、摘要等元信息关联，并输出为 JSON、CSV 或 SQLite 数据库格式，便于后续接入搜索引擎、推荐系统或静态站点生成器。

本仓库包含完整的采集调度示例、链接去重策略、User-Agent 轮换配置以及错误重试机制，适用于教育研究、个人兴趣聚合或内部数据看板建设。所有核心模块均以 Python 3.9+ 编写，依赖轻量，可运行于各类 Linux 服务器、树莓派或云函数环境。

## 功能概览

批量链接导入与规范化 支持从纯文本、CSV 或 JSON 文件批量导入原始 URL，自动识别协议缺失项并补全，对域名进行一致性校验。

可配置的请求调度器 内置基于 asyncio 的异步请求池，支持并发数限制、单域名 QPS 控制、自动重试与退避策略，降低被目标服务器拒绝的风险。

内容元数据提取管道 提供可扩展的 HTML 解析器基类，默认集成 lxml 和 BeautifulSoup4 适配器，能够从新闻详情页提取标题、正文前 200 字符、发布时间与作者字段。

多格式数据导出 支持将处理后的链接与元数据导出为 JSON Lines、CSV 以及 SQLite 关系表，便于下游数据可视化或全文检索索引构建。

去重与变更检测模块 基于 URL 路径哈希与内容指纹的双重去重机制，支持增量更新模式，仅对新增或变更的链接发起请求，节省带宽与计算资源。

日志与监控接口 记录每次请求的状态码、响应时间与异常类型，提供 Prometheus 风格的关键指标暴露端点，方便接入 Grafana 等监控面板。

Docker 容器化交付 提供生产级 Dockerfile 与 docker-compose 示例，支持一键启动采集任务或定时调度容器，降低环境配置成本。

## 应用场景

个人兴趣资讯聚合 用户可将每日收集的数十至数百个新闻链接导入系统，由调度器自动抓取标题与摘要，生成自定义的 HTML 简报或 RSS 源，供个人阅读或订阅。

研究数据采集 社会科学研究者或数据分析师可使用本工具对特定新闻站点的历史文章链接进行结构化采集，导出 CSV 数据集用于文本分析、情感分析或主题建模实验。

内部仪表盘数据源 企业内部团队可将本工具作为数据采集层，定期将最新新闻元数据写入公司内部数据库，供运营看板或竞品监测系统使用，无需依赖第三方付费 API。

静态站点生成器内容源 静态博客或文档站点的维护者可将采集到的新闻链接列表与元数据作为内容原料，通过 Hugo 或 Jekyll 的 data 文件功能生成按时间排序的新闻归档页面。

## 快速开始

以下命令演示了从克隆仓库到运行首个采集任务的全流程。

```bash
git clone https://github.com/example/jnews-aggregator.git
cd jnews-aggregator

python -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

cp config.example.yaml config.yaml
python cli.py import --input samples/links.txt
python cli.py fetch --concurrency 5 --output data/output.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9, 3.10, 3.11 | 核心运行环境，推荐使用 pyenv 管理版本 |
| lxml | 4.9.0+ | HTML 解析加速库，依赖 libxml2 系统库 |
| aiohttp | 3.8.0+ | 异步 HTTP 客户端，支持连接池与 SSL 上下文配置 |
| beautifulsoup4 | 4.11.0+ | 备用 HTML 解析器，提供更宽松的容错能力 |
| click | 8.1.0+ | 命令行交互框架，用于子命令路由与参数校验 |
| PyYAML | 6.0+ | 配置文件解析，支持 YAML 1.2 规范 |
| sqlite3 | 系统自带 | 轻量级关系存储，用于数据持久化与去重表维护 |
| pytest | 7.2.0+ | 单元测试与集成测试框架（仅开发环境依赖） |
| docker | 20.10+ | 容器运行时（仅容器部署模式需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门 | docs/quickstart.md | 如何用最小配置在 5 分钟内运行一次采集任务？ |
| 配置 | docs/configuration.md | config.yaml 中每个字段的含义是什么？如何针对不同场景调整 QPS 和超时？ |
| 开发 | docs/development.md | 如何编写自定义解析器插件？如何扩展导出格式？ |
| 运维 | docs/operations.md | 如何以 systemd 服务或 Kubernetes CronJob 方式部署定时任务？ |
| API | docs/api_reference.md | 各模块的公开类与方法签名、参数类型和返回值结构是什么？ |
| 故障 | docs/troubleshooting.md | 常见报错信息（如 SSL 错误、连接超时）的原因与解决方案 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/3787171.htm
- http://m.3g.bwbkj.cn/jnews/69638.htm
- http://m.3g.bwbkj.cn/jnews/717115.htm
- http://m.3g.bwbkj.cn/jnews/69383.htm
- http://m.3g.bwbkj.cn/jnews/7170377.htm
- http://m.3g.bwbkj.cn/jnews/9854.htm
- http://m.3g.bwbkj.cn/jnews/0929.htm
- http://m.3g.bwbkj.cn/jnews/6650897.htm
- http://m.3g.bwbkj.cn/jnews/1380.htm
- http://m.3g.bwbkj.cn/jnews/3627.htm
- http://m.3g.bwbkj.cn/jnews/768448.htm
- http://m.3g.bwbkj.cn/jnews/4637158.htm
- http://m.3g.bwbkj.cn/jnews/212280.htm
- http://m.3g.bwbkj.cn/jnews/146187.htm
- http://m.3g.bwbkj.cn/jnews/52699.htm
- http://m.3g.bwbkj.cn/jnews/7599.htm
- http://m.3g.bwbkj.cn/jnews/6847.htm
- http://m.3g.bwbkj.cn/jnews/79251.htm
- http://m.3g.bwbkj.cn/jnews/202424.htm
- http://m.3g.bwbkj.cn/jnews/02957.htm
- http://m.3g.bwbkj.cn/jnews/979547.htm
- http://m.3g.bwbkj.cn/jnews/1573.htm
- http://m.3g.bwbkj.cn/jnews/0607.htm
- http://m.3g.bwbkj.cn/jnews/0736687.htm
- http://m.3g.bwbkj.cn/jnews/5725231.htm
- http://m.3g.bwbkj.cn/jnews/945067.htm
- http://m.3g.bwbkj.cn/jnews/431106.htm
- http://m.3g.bwbkj.cn/jnews/5062686.htm
- http://m.3g.bwbkj.cn/jnews/70629.htm
- http://m.3g.bwbkj.cn/jnews/99648.htm
- http://m.3g.bwbkj.cn/jnews/53112.htm
- http://m.3g.bwbkj.cn/jnews/9116.htm
- http://m.3g.bwbkj.cn/jnews/6117743.htm
- http://m.3g.bwbkj.cn/jnews/007505.htm
- http://m.3g.bwbkj.cn/jnews/07402.htm
- http://m.3g.bwbkj.cn/jnews/1886.htm
- http://m.3g.bwbkj.cn/jnews/325561.htm
- http://m.3g.bwbkj.cn/jnews/5332.htm
- http://m.3g.bwbkj.cn/jnews/201592.htm
- http://m.3g.bwbkj.cn/jnews/919418.htm
- http://m.3g.bwbkj.cn/jnews/63555.htm
- http://m.3g.bwbkj.cn/jnews/491237.htm
- http://m.3g.bwbkj.cn/jnews/03240.htm
- http://m.3g.bwbkj.cn/jnews/17378.htm
- http://m.3g.bwbkj.cn/jnews/682954.htm
- http://m.3g.bwbkj.cn/jnews/950183.htm
- http://m.3g.bwbkj.cn/jnews/993151.htm
- http://m.3g.bwbkj.cn/jnews/783786.htm
- http://m.3g.bwbkj.cn/jnews/0012.htm
- http://m.3g.bwbkj.cn/jnews/31305.htm
- http://m.3g.bwbkj.cn/jnews/8751151.htm
- http://m.3g.bwbkj.cn/jnews/91376.htm
- http://m.3g.bwbkj.cn/jnews/29519.htm
- http://m.3g.bwbkj.cn/jnews/7702822.htm
- http://m.3g.bwbkj.cn/jnews/2617688.htm
- http://m.3g.bwbkj.cn/jnews/246709.htm
- http://m.3g.bwbkj.cn/jnews/7569.htm
- http://m.3g.bwbkj.cn/jnews/01572.htm
- http://m.3g.bwbkj.cn/jnews/9184.htm
- http://m.3g.bwbkj.cn/jnews/0374.htm
- http://m.3g.bwbkj.cn/jnews/18970.htm
- http://m.3g.bwbkj.cn/jnews/8905.htm
- http://m.3g.bwbkj.cn/jnews/851492.htm
- http://m.3g.bwbkj.cn/jnews/72436.htm
- http://m.3g.bwbkj.cn/jnews/8403.htm
- http://m.3g.bwbkj.cn/jnews/1746.htm
- http://m.3g.bwbkj.cn/jnews/51827.htm
- http://m.3g.bwbkj.cn/jnews/22414.htm
- http://m.3g.bwbkj.cn/jnews/8221895.htm
- http://m.3g.bwbkj.cn/jnews/8140.htm
- http://m.3g.bwbkj.cn/jnews/5570770.htm
- http://m.3g.bwbkj.cn/jnews/67007.htm
- http://m.3g.bwbkj.cn/jnews/86979.htm
- http://m.3g.bwbkj.cn/jnews/534770.htm
- http://m.3g.bwbkj.cn/jnews/5692526.htm
- http://m.3g.bwbkj.cn/jnews/3508931.htm
- http://m.3g.bwbkj.cn/jnews/9167424.htm
- http://m.3g.bwbkj.cn/jnews/6623.htm
- http://m.3g.bwbkj.cn/jnews/029788.htm
- http://m.3g.bwbkj.cn/jnews/807459.htm
- http://m.3g.bwbkj.cn/jnews/8779408.htm
- http://m.3g.bwbkj.cn/jnews/7855.htm
- http://m.3g.bwbkj.cn/jnews/9266.htm
- http://m.3g.bwbkj.cn/jnews/2474122.htm
- http://m.3g.bwbkj.cn/jnews/86236.htm
- http://m.3g.bwbkj.cn/jnews/80916.htm
- http://m.3g.bwbkj.cn/jnews/483213.htm
- http://m.3g.bwbkj.cn/jnews/05449.htm
- http://m.3g.bwbkj.cn/jnews/4763.htm
- http://m.3g.bwbkj.cn/jnews/0538597.htm
- http://m.3g.bwbkj.cn/jnews/6741797.htm
- http://m.3g.bwbkj.cn/jnews/6434706.htm
- http://m.3g.bwbkj.cn/jnews/9108002.htm
- http://m.3g.bwbkj.cn/jnews/51168.htm
- http://m.3g.bwbkj.cn/jnews/3747.htm
- http://m.3g.bwbkj.cn/jnews/5926754.htm
- http://m.3g.bwbkj.cn/jnews/690662.htm
- http://m.3g.bwbkj.cn/jnews/2925.htm
- http://m.3g.bwbkj.cn/jnews/581770.htm
- http://m.3g.bwbkj.cn/jnews/733273.htm
- http://m.3g.bwbkj.cn/jnews/1549.htm
- http://m.3g.bwbkj.cn/jnews/0972.htm
- http://m.3g.bwbkj.cn/jnews/5367478.htm
- http://m.3g.bwbkj.cn/jnews/4137112.htm
- http://m.3g.bwbkj.cn/jnews/99858.htm
- http://m.3g.bwbkj.cn/jnews/88781.htm
- http://m.3g.bwbkj.cn/jnews/15859.htm
- http://m.3g.bwbkj.cn/jnews/17136.htm
- http://m.3g.bwbkj.cn/jnews/74456.htm
- http://m.3g.bwbkj.cn/jnews/5179.htm
- http://m.3g.bwbkj.cn/jnews/1921189.htm
- http://m.3g.bwbkj.cn/jnews/9919396.htm
- http://m.3g.bwbkj.cn/jnews/10682.htm
- http://m.3g.bwbkj.cn/jnews/1126.htm
- http://m.3g.bwbkj.cn/jnews/7811959.htm
- http://m.3g.bwbkj.cn/jnews/2354401.htm
- http://m.3g.bwbkj.cn/jnews/66470.htm
- http://m.3g.bwbkj.cn/jnews/319009.htm
- http://m.3g.bwbkj.cn/jnews/904020.htm
- http://m.3g.bwbkj.cn/jnews/193497.htm
- http://m.3g.bwbkj.cn/jnews/85808.htm
- http://m.3g.bwbkj.cn/jnews/6863885.htm
- http://m.3g.bwbkj.cn/jnews/074838.htm
- http://m.3g.bwbkj.cn/jnews/5164336.htm
- http://m.3g.bwbkj.cn/jnews/49934.htm
- http://m.3g.bwbkj.cn/jnews/9049.htm
- http://m.3g.bwbkj.cn/jnews/4783069.htm
- http://m.3g.bwbkj.cn/jnews/5091.htm
- http://m.3g.bwbkj.cn/jnews/6140.htm
- http://m.3g.bwbkj.cn/jnews/379138.htm
- http://m.3g.bwbkj.cn/jnews/5075230.htm
- http://m.3g.bwbkj.cn/jnews/1509531.htm
- http://m.3g.bwbkj.cn/jnews/136202.htm
- http://m.3g.bwbkj.cn/jnews/36430.htm
- http://m.3g.bwbkj.cn/jnews/765396.htm
- http://m.3g.bwbkj.cn/jnews/4436534.htm
- http://m.3g.bwbkj.cn/jnews/324922.htm
- http://m.3g.bwbkj.cn/jnews/83562.htm
- http://m.3g.bwbkj.cn/jnews/6759.htm
- http://m.3g.bwbkj.cn/jnews/679332.htm
- http://m.3g.bwbkj.cn/jnews/8158064.htm
- http://m.3g.bwbkj.cn/jnews/075327.htm
- http://m.3g.bwbkj.cn/jnews/3936.htm
- http://m.3g.bwbkj.cn/jnews/5661131.htm
- http://m.3g.bwbkj.cn/jnews/14461.htm
- http://m.3g.bwbkj.cn/jnews/295223.htm
- http://m.3g.bwbkj.cn/jnews/232614.htm
- http://m.3g.bwbkj.cn/jnews/4834550.htm
- http://m.3g.bwbkj.cn/jnews/5347.htm
- http://m.3g.bwbkj.cn/jnews/0953961.htm
- http://m.3g.bwbkj.cn/jnews/959196.htm
- http://m.3g.bwbkj.cn/jnews/3863.htm
- http://m.3g.bwbkj.cn/jnews/56152.htm
- http://m.3g.bwbkj.cn/jnews/48006.htm
- http://m.3g.bwbkj.cn/jnews/949155.htm
- http://m.3g.bwbkj.cn/jnews/322184.htm
- http://m.3g.bwbkj.cn/jnews/9496.htm
- http://m.3g.bwbkj.cn/jnews/5722938.htm
- http://m.3g.bwbkj.cn/jnews/0116.htm
- http://m.3g.bwbkj.cn/jnews/8728521.htm
- http://m.3g.bwbkj.cn/jnews/2883.htm
- http://m.3g.bwbkj.cn/jnews/724928.htm
- http://m.3g.bwbkj.cn/jnews/335180.htm
- http://m.3g.bwbkj.cn/jnews/22663.htm
- http://m.3g.bwbkj.cn/jnews/64786.htm
- http://m.3g.bwbkj.cn/jnews/0199.htm
- http://m.3g.bwbkj.cn/jnews/50723.htm
- http://m.3g.bwbkj.cn/jnews/93874.htm
- http://m.3g.bwbkj.cn/jnews/2534333.htm
- http://m.3g.bwbkj.cn/jnews/803458.htm
- http://m.3g.bwbkj.cn/jnews/006591.htm
- http://m.3g.bwbkj.cn/jnews/4683.htm
- http://m.3g.bwbkj.cn/jnews/645938.htm
- http://m.3g.bwbkj.cn/jnews/17184.htm
- http://m.3g.bwbkj.cn/jnews/5677006.htm
- http://m.3g.bwbkj.cn/jnews/3650098.htm
- http://m.3g.bwbkj.cn/jnews/318696.htm
- http://m.3g.bwbkj.cn/jnews/1368757.htm
- http://m.3g.bwbkj.cn/jnews/2611.htm
- http://m.3g.bwbkj.cn/jnews/7672.htm
- http://m.3g.bwbkj.cn/jnews/160777.htm
- http://m.3g.bwbkj.cn/jnews/2184.htm
- http://m.3g.bwbkj.cn/jnews/9312429.htm
- http://m.3g.bwbkj.cn/jnews/4279.htm
- http://m.3g.bwbkj.cn/jnews/0086.htm
- http://m.3g.bwbkj.cn/jnews/6889.htm
- http://m.3g.bwbkj.cn/jnews/05073.htm
- http://m.3g.bwbkj.cn/jnews/308216.htm
- http://m.3g.bwbkj.cn/jnews/46963.htm
- http://m.3g.bwbkj.cn/jnews/46869.htm
- http://m.3g.bwbkj.cn/jnews/50424.htm
- http://m.3g.bwbkj.cn/jnews/555271.htm
- http://m.3g.bwbkj.cn/jnews/193283.htm
- http://m.3g.bwbkj.cn/jnews/7770.htm
- http://m.3g.bwbkj.cn/jnews/97070.htm
- http://m.3g.bwbkj.cn/jnews/4616131.htm
- http://m.3g.bwbkj.cn/jnews/5197651.htm
- http://m.3g.bwbkj.cn/jnews/50938.htm
- http://m.3g.bwbkj.cn/jnews/96641.htm
- http://m.3g.bwbkj.cn/jnews/61585.htm
- http://m.3g.bwbkj.cn/jnews/02303.htm
- http://m.3g.bwbkj.cn/jnews/3026717.htm
- http://m.3g.bwbkj.cn/jnews/4472.htm
- http://m.3g.bwbkj.cn/jnews/977944.htm
- http://m.3g.bwbkj.cn/jnews/097801.htm
- http://m.3g.bwbkj.cn/jnews/309337.htm
- http://m.3g.bwbkj.cn/jnews/965266.htm
- http://m.3g.bwbkj.cn/jnews/27794.htm
- http://m.3g.bwbkj.cn/jnews/0810093.htm
- http://m.3g.bwbkj.cn/jnews/39795.htm
- http://m.3g.bwbkj.cn/jnews/55255.htm
- http://m.3g.bwbkj.cn/jnews/8600.htm
- http://m.3g.bwbkj.cn/jnews/75351.htm
- http://m.3g.bwbkj.cn/jnews/2954.htm
- http://m.3g.bwbkj.cn/jnews/7173323.htm
- http://m.3g.bwbkj.cn/jnews/18398.htm
- http://m.3g.bwbkj.cn/jnews/8527.htm
- http://m.3g.bwbkj.cn/jnews/24052.htm
- http://m.3g.bwbkj.cn/jnews/2419.htm
- http://m.3g.bwbkj.cn/jnews/105351.htm
- http://m.3g.bwbkj.cn/jnews/972498.htm
- http://m.3g.bwbkj.cn/jnews/144968.htm
- http://m.3g.bwbkj.cn/jnews/957215.htm
- http://m.3g.bwbkj.cn/jnews/6394947.htm
- http://m.3g.bwbkj.cn/jnews/8060.htm
- http://m.3g.bwbkj.cn/jnews/60066.htm
- http://m.3g.bwbkj.cn/jnews/68125.htm
- http://m.3g.bwbkj.cn/jnews/8167879.htm
- http://m.3g.bwbkj.cn/jnews/0293.htm
- http://m.3g.bwbkj.cn/jnews/463559.htm
- http://m.3g.bwbkj.cn/jnews/775262.htm
- http://m.3g.bwbkj.cn/jnews/7199.htm
- http://m.3g.bwbkj.cn/jnews/4415537.htm
- http://m.3g.bwbkj.cn/jnews/548932.htm
- http://m.3g.bwbkj.cn/jnews/5558069.htm
- http://m.3g.bwbkj.cn/jnews/2529.htm
- http://m.3g.bwbkj.cn/jnews/4085.htm
- http://m.3g.bwbkj.cn/jnews/0455.htm
- http://m.3g.bwbkj.cn/jnews/0656039.htm
- http://m.3g.bwbkj.cn/jnews/8926.htm
- http://m.3g.bwbkj.cn/jnews/8257529.htm
- http://m.3g.bwbkj.cn/jnews/233670.htm
- http://m.3g.bwbkj.cn/jnews/9768.htm
- http://m.3g.bwbkj.cn/jnews/2634664.htm
- http://m.3g.bwbkj.cn/jnews/2123.htm
- http://m.3g.bwbkj.cn/jnews/8477.htm
- http://m.3g.bwbkj.cn/jnews/057208.htm
- http://m.3g.bwbkj.cn/jnews/0703.htm
- http://m.3g.bwbkj.cn/jnews/555359.htm
- http://m.3g.bwbkj.cn/jnews/80924.htm
- http://m.3g.bwbkj.cn/jnews/3031072.htm
- http://m.3g.bwbkj.cn/jnews/06809.htm
- http://m.3g.bwbkj.cn/jnews/4575.htm
- http://m.3g.bwbkj.cn/jnews/027473.htm
- http://m.3g.bwbkj.cn/jnews/81896.htm
- http://m.3g.bwbkj.cn/jnews/8340.htm
- http://m.3g.bwbkj.cn/jnews/1327.htm
- http://m.3g.bwbkj.cn/jnews/6705467.htm
- http://m.3g.bwbkj.cn/jnews/503459.htm
- http://m.3g.bwbkj.cn/jnews/3395.htm
- http://m.3g.bwbkj.cn/jnews/319825.htm
- http://m.3g.bwbkj.cn/jnews/4784.htm
- http://m.3g.bwbkj.cn/jnews/25171.htm
- http://m.3g.bwbkj.cn/jnews/111802.htm
- http://m.3g.bwbkj.cn/jnews/3397.htm
- http://m.3g.bwbkj.cn/jnews/411225.htm
- http://m.3g.bwbkj.cn/jnews/1794467.htm
- http://m.3g.bwbkj.cn/jnews/967438.htm
- http://m.3g.bwbkj.cn/jnews/19126.htm
- http://m.3g.bwbkj.cn/jnews/9188.htm
- http://m.3g.bwbkj.cn/jnews/9000626.htm
- http://m.3g.bwbkj.cn/jnews/4179.htm
- http://m.3g.bwbkj.cn/jnews/2092.htm
- http://m.3g.bwbkj.cn/jnews/82528.htm
- http://m.3g.bwbkj.cn/jnews/1397.htm
- http://m.3g.bwbkj.cn/jnews/3491957.htm
- http://m.3g.bwbkj.cn/jnews/79348.htm
- http://m.3g.bwbkj.cn/jnews/85606.htm
- http://m.3g.bwbkj.cn/jnews/098181.htm
- http://m.3g.bwbkj.cn/jnews/854774.htm
- http://m.3g.bwbkj.cn/jnews/3944823.htm
- http://m.3g.bwbkj.cn/jnews/4677857.htm
- http://m.3g.bwbkj.cn/jnews/923051.htm
- http://m.3g.bwbkj.cn/jnews/6964.htm
- http://m.3g.bwbkj.cn/jnews/1547424.htm
- http://m.3g.bwbkj.cn/jnews/8914.htm
- http://m.3g.bwbkj.cn/jnews/11897.htm
- http://m.3g.bwbkj.cn/jnews/9226087.htm
- http://m.3g.bwbkj.cn/jnews/362054.htm
- http://m.3g.bwbkj.cn/jnews/9784.htm
- http://m.3g.bwbkj.cn/jnews/18780.htm
- http://m.3g.bwbkj.cn/jnews/715074.htm
- http://m.3g.bwbkj.cn/jnews/85454.htm
- http://m.3g.bwbkj.cn/jnews/0685016.htm
- http://m.3g.bwbkj.cn/jnews/942003.htm
- http://m.3g.bwbkj.cn/jnews/510340.htm
- http://m.3g.bwbkj.cn/jnews/1899.htm
- http://m.3g.bwbkj.cn/jnews/0446.htm
- http://m.3g.bwbkj.cn/jnews/6383460.htm
- http://m.3g.bwbkj.cn/jnews/510177.htm

## 项目结构

```
jnews-aggregator/
├── cli.py                     # 命令行入口，注册 import/fetch/export 子命令
├── config.example.yaml        # 示例配置文件，含并发数、超时、重试策略
├── requirements.txt           # 生产环境依赖列表（固定版本）
├── requirements-dev.txt       # 开发环境额外依赖（测试、lint、格式化）
├── docker-compose.yml         # 容器编排示例，含调度器与数据库服务
├── Dockerfile                 # 多阶段构建文件，最终镜像约 120MB
│
├── src/                       # 核心源码目录
│   ├── __init__.py
│   ├── fetcher/               # 请求调度与网络层
│   │   ├── client.py          # aiohttp 会话封装，含自动重试与代理支持
│   │   └── middleware.py      # 请求钩子：日志、限速、UA 轮换
│   ├── parser/                # 解析器模块
│   │   ├── base.py            # 抽象解析器接口，定义 parse() 契约
│   │   ├── lxml_adapter.py    # 基于 lxml 的高性能解析实现
│   │   └── bs4_adapter.py     # 基于 BeautifulSoup4 的容错解析实现
│   ├── pipeline/              # 数据处理管道
│   │   ├── deduplicator.py    # 基于路径哈希与内容指纹的去重器
│   │   ├── exporter.py        # 多格式导出器（JSONL/CSV/SQLite）
│   │   └── transformer.py     # 字段映射、日期标准化、摘要截断
│   ├── storage/               # 持久化层
│   │   ├── sqlite_store.py    # SQLite 连接池与表结构初始化
│   │   └── schema.sql         # 建表语句（urls, metadata, logs）
│   └── utils/                 # 通用工具
│       ├── logger.py          # 结构化日志配置（JSON 格式输出）
│       └── validators.py      # URL 校验、域名白名单匹配
│
├── tests/                     # 单元测试与集成测试
│   ├── test_fetcher.py        # 模拟请求与重试逻辑测试
│   ├── test_parser.py         # 各解析器适配器的覆盖率测试
│   └── fixtures/              # 测试用样本数据（HTML 片段）
│
├── docs/                      # 完整文档目录（参见上方文档导航）
│   ├── quickstart.md
│   ├── configuration.md
│   ├── development.md
│   ├── operations.md
│   ├── api_reference.md
│   └── troubleshooting.md
│
├── scripts/                   # 运维辅助脚本
│   ├── daily_cron.sh          # crontab 入口脚本，带环境变量加载
│   └── migrate_db.py          # 数据库迁移工具（增删字段）
│
└── samples/                   # 示例数据
    ├── links.txt              # 纯文本链接列表样例（每行一个 URL）
    └── sample_output.jsonl    # 预期输出格式示例
```

## 贡献指南

1. 阅读项目行为准则与贡献者公约，确保遵守基本协作规范。所有提交需附带清晰的 commit message，遵循 Conventional Commits 格式（feat/fix/docs/style/refactor 等作用域标签）。

2. 在 Issues 列表中认领或创建新的功能需求或缺陷报告，等待维护者确认后再进行开发。对于较大规模的改动（如新增解析器引擎或支持新导出格式），建议先创建 Discussion 进行方案讨论。

3. 派生仓库到个人账号，创建特性分支（feature/ 或 fix/ 前缀）。开发过程中请确保新增代码包含对应的单元测试，且通过现有全部测试套件（pytest -v）。代码风格需通过 black 和 flake8 检查。

4. 提交 Pull Request 时请填写标准模板，包含改动摘要、测试结果、文档更新情况以及是否影响已有配置兼容性。PR 需要至少一位维护者审核通过后方可合并。

5. 欢迎提交新的链接资源批次（符合格式要求的 .txt 或 .json 文件），需附带来源说明与采集日期。资源文件应置于 samples/extra/ 目录下，并在 PR 描述中注明链接总数与去重情况。

## 常见问题

问题：采集任务运行一段时间后出现大量超时或连接被重置，如何解决？

回答：这通常是因为目标服务器对高频请求实施了连接数限制或 IP 临时封禁。建议采取以下措施：降低 config.yaml 中的 concurrency 参数至 3 以下；增大 request_timeout 至 30 秒以上；启用 `enable_retry` 并设置 `max_retries` 为 3；若持续出现，可在 middleware 中配置 `proxy` 字段使用代理池轮换出口 IP。

问题：解析器提取的标题或发布时间字段为空，但浏览器中正常显示，原因是什么？

回答：大部分新闻站点对移动端和桌面端返回的 HTML 结构不同，可能使用不同的 class 或 data 属性。本项目的默认解析规则基于常见结构（如 article 标签、h1 标题、time 元素）设计，若目标站点使用非标准结构，请复制 src/parser/base.py 并重写 extract_title 与 extract_pubtime 方法，然后在 config.yaml 的 parser_map 中为域名指定自定义解析器类路径。

问题：如何只采集新增链接而不重复处理已有数据？

回答：项目内置去重模块默认基于 URL 路径的 SHA256 哈希作为主键。首次运行后会生成 SQLite 数据库文件（默认为 data/cache.db），后续运行 fetch 命令时添加 `--incremental` 标志即可启用增量模式，调度器会先查询数据库，仅对未收录的链接发起请求。如需强制刷新，可删除 cache.db 文件或使用 `--force` 参数。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:05
