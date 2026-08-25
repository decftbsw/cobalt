# WebLink Catalog Aggregate

WebLink Catalog Aggregate 是一个面向技术内容聚合与外部链接治理的开源工具集。该项目定位于帮助开发者、技术内容运营者以及个人知识库维护者，对分散在多个来源的链接资源进行统一的解析、分类、健康检查与元数据提取。WebLink Catalog Aggregate 不依赖特定商业平台，完全基于开源生态构建，适用于需要长期维护大量外链引用列表的场景，例如技术博客的参考文献管理、开源项目的外部依赖溯源、以及企业内部技术周报的链接资产梳理。

该项目通过可编排的管道处理模式，将原始链接集合转化为结构化、可查询、可监控的链接资产清单，并提供基础的 Web 展示与检索能力。项目本身不预设链接的具体内容类型，而是以链接的元数据（状态码、响应时间、内容类型、标题、关键词密度等）作为统一处理维度，因此无论链接指向技术文档、新闻资讯、学术论文还是视频资源，均可纳入同一治理框架。

## 功能概览

**批量链接解析**：支持一次性导入数千条原始 URL，自动完成去重、规范化与协议补全检测，输出标准化的链接对象列表。

**健康状态监控**：对每条链接执行定期的 HTTP 探测，记录状态码、响应时间、重定向链及 SSL 证书有效期，生成健康度评分。

**元数据智能抽取**：从链接目标页面中自动提取标题、描述、主要正文关键词、发布时间及语言编码，形成丰富的链接档案。

**分类标签体系**：基于规则引擎与简单的贝叶斯分类器，为链接自动打上技术、新闻、文档、视频、学术等分类标签，支持用户自定义标签规则。

**检索与过滤接口**：提供 RESTful API 与命令行工具，支持按域名、状态码、分类标签、更新时间等多维度组合过滤与排序。

**增量同步与变更追踪**：记录每次链接扫描的结果差异，对新增失效、内容变更或重定向的链接生成变更报告，便于运营人员及时处理。

## 应用场景

技术博客与文档站的参考文献链接维护。技术作者在撰写文章时引用大量外部链接，随着时间推移部分链接可能失效或内容迁移。WebLink Catalog Aggregate 可定期扫描所有参考文献链接，自动标记失效链接并生成告警，帮助作者在发布前或定期维护中更新链接，提升文档质量。

企业内部技术周报与知识库的链接资产管理。企业技术团队每周汇总行业动态时涉及数十个外部资讯源，使用本工具可统一收拢这些链接，监控每个资讯源的可用性，并在资讯源改版或关闭时及时调整采集策略，确保内部知识库的引用可靠性。

开源项目的外部依赖与文档引用溯源。开源项目在 README、文档或代码注释中常引用第三方资源，这些外部链接的稳定性直接影响项目的可访问性。通过本工具提供的链接健康监控，项目维护者可快速发现失效链接并提交修复，提升项目的专业形象与用户体验。

个人知识库与书签系统的整理与增强。个人开发者或研究员积累的大量书签与收藏链接往往缺乏有效管理。本工具可批量导入浏览器导出的书签文件或 Markdown 中的链接列表，自动补充页面标题、描述与分类，并提供检索接口，帮助用户快速找回有价值的资源。

## 快速开始

以下步骤帮助您在本地环境中快速启动 WebLink Catalog Aggregate 服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-catalog/aggregate.git
cd aggregate

# 安装 Python 依赖（推荐使用 Python 3.10 及以上版本）
pip install -r requirements.txt

# 初始化配置文件（复制示例配置）
cp config.example.yaml config.yaml

# 运行数据迁移与索引构建
python manage.py migrate
python manage.py build_index

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

启动成功后，访问 http://localhost:8080 可查看 Web 管理界面。使用 `weblink-cli import --file links.txt` 命令可导入包含原始 URL 的文本文件，每行一个 URL。导入后的链接将自动进入解析与健康检查队列。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 及以上 | 核心运行环境，推荐使用 3.11 或 3.12 以获得更好的性能 |
| SQLite | 3.35 及以上 | 默认内置数据库，用于存储链接元数据与扫描历史，生产环境可切换至 PostgreSQL |
| Redis | 6.0 及以上 | 用于任务队列缓存与临时结果存储，如不使用可配置为内存模式但性能会下降 |
| lxml | 4.9 及以上 | HTML 解析依赖，用于从链接页面中抽取元数据，需编译安装或使用预编译轮子 |
| httpx | 0.24 及以上 | 异步 HTTP 客户端，用于并发链接探测，支持 HTTP/2 与连接池复用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/quickstart.md | 如何快速安装并运行第一个链接导入任务？系统的基本概念与工作流程是什么？ |
| 配置手册 | docs/configuration.md | 如何配置链接探测的超时时间、并发数、重试策略及分类规则？各类参数的具体含义与调优建议有哪些？ |
| API 参考 | docs/api_reference.md | 如何通过 RESTful API 进行链接导入、查询、更新与删除？各接口的请求格式与响应字段说明是什么？ |
| 运维指南 | docs/operations.md | 如何部署到生产环境？如何进行数据备份、日志轮转与性能监控？常见的异常情况如何处理？ |

## 资源列表

- http://m.blog.bwbkj.cn/snews/856480.htm
- http://m.blog.bwbkj.cn/snews/13531.htm
- http://m.blog.bwbkj.cn/snews/96620.htm
- http://m.blog.bwbkj.cn/snews/53547.htm
- http://m.blog.bwbkj.cn/snews/0934.htm
- http://m.blog.bwbkj.cn/snews/917381.htm
- http://m.blog.bwbkj.cn/snews/77078.htm
- http://m.blog.bwbkj.cn/snews/0742.htm
- http://m.blog.bwbkj.cn/snews/2268.htm
- http://m.blog.bwbkj.cn/snews/2636.htm
- http://m.blog.bwbkj.cn/snews/62554.htm
- http://m.blog.bwbkj.cn/snews/187014.htm
- http://m.blog.bwbkj.cn/snews/13051.htm
- http://m.blog.bwbkj.cn/snews/8325192.htm
- http://m.blog.bwbkj.cn/snews/83474.htm
- http://m.blog.bwbkj.cn/snews/0987.htm
- http://m.blog.bwbkj.cn/snews/088554.htm
- http://m.blog.bwbkj.cn/snews/26518.htm
- http://m.blog.bwbkj.cn/snews/266227.htm
- http://m.blog.bwbkj.cn/snews/220160.htm
- http://m.blog.bwbkj.cn/snews/5273346.htm
- http://m.blog.bwbkj.cn/snews/1969.htm
- http://m.blog.bwbkj.cn/snews/299596.htm
- http://m.blog.bwbkj.cn/snews/848257.htm
- http://m.blog.bwbkj.cn/snews/08426.htm
- http://m.blog.bwbkj.cn/snews/082024.htm
- http://m.blog.bwbkj.cn/snews/639867.htm
- http://m.blog.bwbkj.cn/snews/420453.htm
- http://m.blog.bwbkj.cn/snews/24041.htm
- http://m.blog.bwbkj.cn/snews/5185044.htm
- http://m.blog.bwbkj.cn/snews/0754131.htm
- http://m.blog.bwbkj.cn/snews/4804438.htm
- http://m.blog.bwbkj.cn/snews/74965.htm
- http://m.blog.bwbkj.cn/snews/176728.htm
- http://m.blog.bwbkj.cn/snews/2273.htm
- http://m.blog.bwbkj.cn/snews/2657.htm
- http://m.blog.bwbkj.cn/snews/05047.htm
- http://m.blog.bwbkj.cn/snews/6839668.htm
- http://m.blog.bwbkj.cn/snews/62750.htm
- http://m.blog.bwbkj.cn/snews/41930.htm
- http://m.blog.bwbkj.cn/snews/8490936.htm
- http://m.blog.bwbkj.cn/snews/69818.htm
- http://m.blog.bwbkj.cn/snews/581092.htm
- http://m.blog.bwbkj.cn/snews/275237.htm
- http://m.blog.bwbkj.cn/snews/224072.htm
- http://m.blog.bwbkj.cn/snews/68871.htm
- http://m.blog.bwbkj.cn/snews/7824614.htm
- http://m.blog.bwbkj.cn/snews/2355093.htm
- http://m.blog.bwbkj.cn/snews/07066.htm
- http://m.blog.bwbkj.cn/snews/93403.htm
- http://m.blog.bwbkj.cn/snews/942598.htm
- http://m.blog.bwbkj.cn/snews/9319.htm
- http://m.blog.bwbkj.cn/snews/2316.htm
- http://m.blog.bwbkj.cn/snews/9068474.htm
- http://m.blog.bwbkj.cn/snews/50241.htm
- http://m.blog.bwbkj.cn/snews/18877.htm
- http://m.blog.bwbkj.cn/snews/9855.htm
- http://m.blog.bwbkj.cn/snews/639914.htm
- http://m.blog.bwbkj.cn/snews/62584.htm
- http://m.blog.bwbkj.cn/snews/6940291.htm
- http://m.blog.bwbkj.cn/snews/9251795.htm
- http://m.blog.bwbkj.cn/snews/8745.htm
- http://m.blog.bwbkj.cn/snews/9657165.htm
- http://m.blog.bwbkj.cn/snews/894161.htm
- http://m.blog.bwbkj.cn/snews/6571678.htm
- http://m.blog.bwbkj.cn/snews/9034197.htm
- http://m.blog.bwbkj.cn/snews/8066.htm
- http://m.blog.bwbkj.cn/snews/1465.htm
- http://m.blog.bwbkj.cn/snews/0414562.htm
- http://m.blog.bwbkj.cn/snews/74562.htm
- http://m.blog.bwbkj.cn/snews/70351.htm
- http://m.blog.bwbkj.cn/snews/96550.htm
- http://m.blog.bwbkj.cn/snews/9607.htm
- http://m.blog.bwbkj.cn/snews/0441131.htm
- http://m.blog.bwbkj.cn/snews/1761.htm
- http://m.blog.bwbkj.cn/snews/07776.htm
- http://m.blog.bwbkj.cn/snews/25522.htm
- http://m.blog.bwbkj.cn/snews/882829.htm
- http://m.blog.bwbkj.cn/snews/36511.htm
- http://m.blog.bwbkj.cn/snews/9501777.htm
- http://m.blog.bwbkj.cn/snews/69260.htm
- http://m.blog.bwbkj.cn/snews/535797.htm
- http://m.blog.bwbkj.cn/snews/6236.htm
- http://m.blog.bwbkj.cn/snews/6583.htm
- http://m.blog.bwbkj.cn/snews/8389.htm
- http://m.blog.bwbkj.cn/snews/2536.htm
- http://m.blog.bwbkj.cn/snews/787259.htm
- http://m.blog.bwbkj.cn/snews/821272.htm
- http://m.blog.bwbkj.cn/snews/230382.htm
- http://m.blog.bwbkj.cn/snews/969344.htm
- http://m.blog.bwbkj.cn/snews/80477.htm
- http://m.blog.bwbkj.cn/snews/5132609.htm
- http://m.blog.bwbkj.cn/snews/16577.htm
- http://m.blog.bwbkj.cn/snews/342405.htm
- http://m.blog.bwbkj.cn/snews/41065.htm
- http://m.blog.bwbkj.cn/snews/0383626.htm
- http://m.blog.bwbkj.cn/snews/942305.htm
- http://m.blog.bwbkj.cn/snews/08270.htm
- http://m.blog.bwbkj.cn/snews/23924.htm
- http://m.blog.bwbkj.cn/snews/4517747.htm
- http://m.blog.bwbkj.cn/snews/4723.htm
- http://m.blog.bwbkj.cn/snews/364807.htm
- http://m.blog.bwbkj.cn/snews/7563.htm
- http://m.blog.bwbkj.cn/snews/685105.htm
- http://m.blog.bwbkj.cn/snews/221406.htm
- http://m.blog.bwbkj.cn/snews/634938.htm
- http://m.blog.bwbkj.cn/snews/8826.htm
- http://m.blog.bwbkj.cn/snews/936129.htm
- http://m.blog.bwbkj.cn/snews/54832.htm
- http://m.blog.bwbkj.cn/snews/1443.htm
- http://m.blog.bwbkj.cn/snews/44393.htm
- http://m.blog.bwbkj.cn/snews/1302.htm
- http://m.blog.bwbkj.cn/snews/5039597.htm
- http://m.blog.bwbkj.cn/snews/3345220.htm
- http://m.blog.bwbkj.cn/snews/314327.htm
- http://m.blog.bwbkj.cn/snews/7190.htm
- http://m.blog.bwbkj.cn/snews/8760184.htm
- http://m.blog.bwbkj.cn/snews/741047.htm
- http://m.blog.bwbkj.cn/snews/67822.htm
- http://m.blog.bwbkj.cn/snews/6665383.htm
- http://m.blog.bwbkj.cn/snews/64401.htm
- http://m.blog.bwbkj.cn/snews/26435.htm
- http://m.blog.bwbkj.cn/snews/301815.htm
- http://m.blog.bwbkj.cn/snews/6551072.htm
- http://m.blog.bwbkj.cn/snews/52056.htm
- http://m.blog.bwbkj.cn/snews/01981.htm
- http://m.blog.bwbkj.cn/snews/4893.htm
- http://m.blog.bwbkj.cn/snews/451780.htm
- http://m.blog.bwbkj.cn/snews/25364.htm
- http://m.blog.bwbkj.cn/snews/58372.htm
- http://m.blog.bwbkj.cn/snews/58246.htm
- http://m.blog.bwbkj.cn/snews/208042.htm
- http://m.blog.bwbkj.cn/snews/4936.htm
- http://m.blog.bwbkj.cn/snews/7500111.htm
- http://m.blog.bwbkj.cn/snews/17574.htm
- http://m.blog.bwbkj.cn/snews/1357.htm
- http://m.blog.bwbkj.cn/snews/658365.htm
- http://m.blog.bwbkj.cn/snews/5942137.htm
- http://m.blog.bwbkj.cn/snews/1632822.htm
- http://m.blog.bwbkj.cn/snews/7023289.htm
- http://m.blog.bwbkj.cn/snews/964489.htm
- http://m.blog.bwbkj.cn/snews/0288702.htm
- http://m.blog.bwbkj.cn/snews/61379.htm
- http://m.blog.bwbkj.cn/snews/0334.htm
- http://m.blog.bwbkj.cn/snews/43332.htm
- http://m.blog.bwbkj.cn/snews/5405.htm
- http://m.blog.bwbkj.cn/snews/0227.htm
- http://m.blog.bwbkj.cn/snews/9046.htm
- http://m.blog.bwbkj.cn/snews/375660.htm
- http://m.blog.bwbkj.cn/snews/247553.htm
- http://m.blog.bwbkj.cn/snews/8331.htm
- http://m.blog.bwbkj.cn/snews/159612.htm
- http://m.blog.bwbkj.cn/snews/543963.htm
- http://m.blog.bwbkj.cn/snews/2917114.htm
- http://m.blog.bwbkj.cn/snews/6277140.htm
- http://m.blog.bwbkj.cn/snews/6553.htm
- http://m.blog.bwbkj.cn/snews/5992212.htm
- http://m.blog.bwbkj.cn/snews/0935.htm
- http://m.blog.bwbkj.cn/snews/78074.htm
- http://m.blog.bwbkj.cn/snews/83614.htm
- http://m.blog.bwbkj.cn/snews/2252747.htm
- http://m.blog.bwbkj.cn/snews/28051.htm
- http://m.blog.bwbkj.cn/snews/705073.htm
- http://m.blog.bwbkj.cn/snews/43761.htm
- http://m.blog.bwbkj.cn/snews/9147956.htm
- http://m.blog.bwbkj.cn/snews/906497.htm
- http://m.blog.bwbkj.cn/snews/86392.htm
- http://m.blog.bwbkj.cn/snews/7570.htm
- http://m.blog.bwbkj.cn/snews/2329957.htm
- http://m.blog.bwbkj.cn/snews/636945.htm
- http://m.blog.bwbkj.cn/snews/3808.htm
- http://m.blog.bwbkj.cn/snews/5290062.htm
- http://m.blog.bwbkj.cn/snews/70807.htm
- http://m.blog.bwbkj.cn/snews/2827058.htm
- http://m.blog.bwbkj.cn/snews/422850.htm
- http://m.blog.bwbkj.cn/snews/321024.htm
- http://m.blog.bwbkj.cn/snews/724088.htm
- http://m.blog.bwbkj.cn/snews/221990.htm
- http://m.blog.bwbkj.cn/snews/70491.htm
- http://m.blog.bwbkj.cn/snews/72174.htm
- http://m.blog.bwbkj.cn/snews/8170883.htm
- http://m.blog.bwbkj.cn/snews/0407.htm
- http://m.blog.bwbkj.cn/snews/2711996.htm
- http://m.blog.bwbkj.cn/snews/2086387.htm
- http://m.blog.bwbkj.cn/snews/94078.htm
- http://m.blog.bwbkj.cn/snews/2309.htm
- http://m.blog.bwbkj.cn/snews/419587.htm
- http://m.blog.bwbkj.cn/snews/313454.htm
- http://m.blog.bwbkj.cn/snews/590140.htm
- http://m.blog.bwbkj.cn/snews/5909206.htm
- http://m.blog.bwbkj.cn/snews/379657.htm
- http://m.blog.bwbkj.cn/snews/3060742.htm
- http://m.blog.bwbkj.cn/snews/519022.htm
- http://m.blog.bwbkj.cn/snews/38081.htm
- http://m.blog.bwbkj.cn/snews/003802.htm
- http://m.blog.bwbkj.cn/snews/8515691.htm
- http://m.blog.bwbkj.cn/snews/7106172.htm
- http://m.blog.bwbkj.cn/snews/8421.htm
- http://m.blog.bwbkj.cn/snews/868011.htm
- http://m.blog.bwbkj.cn/snews/47187.htm
- http://m.blog.bwbkj.cn/snews/38047.htm
- http://m.blog.bwbkj.cn/snews/91783.htm
- http://m.blog.bwbkj.cn/snews/108925.htm
- http://m.blog.bwbkj.cn/snews/50161.htm
- http://m.blog.bwbkj.cn/snews/41120.htm
- http://m.blog.bwbkj.cn/snews/772522.htm
- http://m.blog.bwbkj.cn/snews/350730.htm
- http://m.blog.bwbkj.cn/snews/5065.htm
- http://m.blog.bwbkj.cn/snews/2821419.htm
- http://m.blog.bwbkj.cn/snews/7265.htm
- http://m.blog.bwbkj.cn/snews/50466.htm
- http://m.blog.bwbkj.cn/snews/7912259.htm
- http://m.blog.bwbkj.cn/snews/9249302.htm
- http://m.blog.bwbkj.cn/snews/355577.htm
- http://m.blog.bwbkj.cn/snews/8423288.htm
- http://m.blog.bwbkj.cn/snews/670958.htm
- http://m.blog.bwbkj.cn/snews/4903795.htm
- http://m.blog.bwbkj.cn/snews/72405.htm
- http://m.blog.bwbkj.cn/snews/331847.htm
- http://m.blog.bwbkj.cn/snews/63808.htm
- http://m.blog.bwbkj.cn/snews/671048.htm
- http://m.blog.bwbkj.cn/snews/534186.htm
- http://m.blog.bwbkj.cn/snews/7092.htm
- http://m.blog.bwbkj.cn/snews/1966.htm
- http://m.blog.bwbkj.cn/snews/90240.htm
- http://m.blog.bwbkj.cn/snews/2131366.htm
- http://m.blog.bwbkj.cn/snews/589338.htm
- http://m.blog.bwbkj.cn/snews/8696.htm
- http://m.blog.bwbkj.cn/snews/0563.htm
- http://m.blog.bwbkj.cn/snews/480668.htm
- http://m.blog.bwbkj.cn/snews/3259.htm
- http://m.blog.bwbkj.cn/snews/494075.htm
- http://m.blog.bwbkj.cn/snews/4013.htm
- http://m.blog.bwbkj.cn/snews/0909132.htm
- http://m.blog.bwbkj.cn/snews/383703.htm
- http://m.blog.bwbkj.cn/snews/725530.htm
- http://m.blog.bwbkj.cn/snews/7491.htm
- http://m.blog.bwbkj.cn/snews/6688.htm
- http://m.blog.bwbkj.cn/snews/5464.htm
- http://m.blog.bwbkj.cn/snews/0496080.htm
- http://m.blog.bwbkj.cn/snews/75465.htm
- http://m.blog.bwbkj.cn/snews/1522.htm
- http://m.blog.bwbkj.cn/snews/1888048.htm
- http://m.blog.bwbkj.cn/snews/8159126.htm
- http://m.blog.bwbkj.cn/snews/11861.htm
- http://m.blog.bwbkj.cn/snews/979060.htm
- http://m.blog.bwbkj.cn/snews/11118.htm
- http://m.blog.bwbkj.cn/snews/5002.htm
- http://m.blog.bwbkj.cn/snews/60601.htm
- http://m.blog.bwbkj.cn/snews/78093.htm
- http://m.blog.bwbkj.cn/snews/9797.htm
- http://m.blog.bwbkj.cn/snews/751861.htm
- http://m.blog.bwbkj.cn/snews/200253.htm
- http://m.blog.bwbkj.cn/snews/3329535.htm
- http://m.blog.bwbkj.cn/snews/8676430.htm
- http://m.blog.bwbkj.cn/snews/381139.htm
- http://m.blog.bwbkj.cn/snews/76489.htm
- http://m.blog.bwbkj.cn/snews/9366477.htm
- http://m.blog.bwbkj.cn/snews/180109.htm
- http://m.blog.bwbkj.cn/snews/3976.htm
- http://m.blog.bwbkj.cn/snews/664106.htm
- http://m.blog.bwbkj.cn/snews/01109.htm
- http://m.blog.bwbkj.cn/snews/61678.htm
- http://m.blog.bwbkj.cn/snews/7102788.htm
- http://m.blog.bwbkj.cn/snews/5792.htm
- http://m.blog.bwbkj.cn/snews/8741.htm
- http://m.blog.bwbkj.cn/snews/1304741.htm
- http://m.blog.bwbkj.cn/snews/2093882.htm
- http://m.blog.bwbkj.cn/snews/4301463.htm
- http://m.blog.bwbkj.cn/snews/4500.htm
- http://m.blog.bwbkj.cn/snews/95985.htm
- http://m.blog.bwbkj.cn/snews/6424.htm
- http://m.blog.bwbkj.cn/snews/8991.htm
- http://m.blog.bwbkj.cn/snews/6325297.htm
- http://m.blog.bwbkj.cn/snews/83854.htm
- http://m.blog.bwbkj.cn/snews/4578565.htm
- http://m.blog.bwbkj.cn/snews/2557.htm
- http://m.blog.bwbkj.cn/snews/08707.htm
- http://m.blog.bwbkj.cn/snews/196722.htm
- http://m.blog.bwbkj.cn/snews/5765621.htm
- http://m.blog.bwbkj.cn/snews/35807.htm
- http://m.blog.bwbkj.cn/snews/61931.htm
- http://m.blog.bwbkj.cn/snews/768964.htm
- http://m.blog.bwbkj.cn/snews/98766.htm
- http://m.blog.bwbkj.cn/snews/5108667.htm
- http://m.blog.bwbkj.cn/snews/72655.htm
- http://m.blog.bwbkj.cn/snews/70439.htm
- http://m.blog.bwbkj.cn/snews/6995965.htm
- http://m.blog.bwbkj.cn/snews/7586803.htm
- http://m.blog.bwbkj.cn/snews/6755.htm
- http://m.blog.bwbkj.cn/snews/44693.htm
- http://m.blog.bwbkj.cn/snews/075327.htm
- http://m.blog.bwbkj.cn/snews/39697.htm
- http://m.blog.bwbkj.cn/snews/706317.htm
- http://m.blog.bwbkj.cn/snews/6049.htm
- http://m.blog.bwbkj.cn/snews/18055.htm
- http://m.blog.bwbkj.cn/snews/9156038.htm
- http://m.blog.bwbkj.cn/snews/491502.htm
- http://m.blog.bwbkj.cn/snews/2561750.htm
- http://m.blog.bwbkj.cn/snews/66810.htm

## 项目结构

```
aggregate/
├── cmd/                                   # 命令行入口与子命令实现
│   ├── weblink-cli/                       # 主 CLI 程序入口
│   │   ├── main.go                        # 参数解析与命令路由
│   │   └── commands/                      # 各子命令实现
│   │       ├── import.go                  # 导入链接子命令
│   │       ├── scan.go                    # 扫描探测子命令
│   │       ├── query.go                   # 查询检索子命令
│   │       └── report.go                  # 报告生成子命令
│   └── server/                            # Web 服务启动入口
│       └── main.go                        # HTTP 服务器初始化
├── internal/                              # 内部核心逻辑，不对外暴露
│   ├── crawler/                           # 链接探测与内容抓取模块
│   │   ├── fetcher.go                     # HTTP 请求封装与重试策略
│   │   ├── parser.go                      # HTML 元数据解析逻辑
│   │   └── checker.go                     # 链接状态与健康度检查
│   ├── classifier/                        # 分类标签引擎
│   │   ├── rules.go                       # 基于规则的分类器
│   │   └── bayesian.go                    # 贝叶斯分类器实现
│   ├── storage/                           # 数据持久化层
│   │   ├── sqlite.go                      # SQLite 适配器
│   │   ├── postgres.go                    # PostgreSQL 适配器
│   │   └── migrations/                    # 数据库迁移脚本
│   ├── queue/                             # 任务队列与调度
│   │   ├── redis.go                       # Redis 队列适配器
│   │   └── memory.go                      # 内存队列（开发测试用）
│   └── model/                             # 数据模型定义
│       ├── link.go                        # 链接实体结构与状态枚举
│       └── snapshot.go                    # 扫描快照与变更记录
├── pkg/                                   # 可被外部引用的公共库
│   ├── httpclient/                        # 可复用的 HTTP 客户端工具
│   ├── logger/                            # 结构化日志封装
│   ├── config/                            # 配置文件加载与校验
│   └── utils/                             # 通用辅助函数（去重、时间处理等）
├── web/                                   # Web 界面相关资源
│   ├── templates/                         # HTML 模板文件
│   │   ├── index.html                     # 仪表板页面
│   │   ├── links.html                     # 链接列表与详情页
│   │   └── reports.html                   # 扫描报告查看页
│   └── static/                            # 静态资源（CSS、JavaScript、图标）
├── test/                                  # 测试套件
│   ├── integration/                       # 集成测试用例
│   └── mock/                              # 模拟服务与测试数据
├── docs/                                  # 文档源码
│   ├── quickstart.md                      # 快速入门指南
│   ├── configuration.md                   # 配置参数详解
│   ├── api_reference.md                   # API 接口文档
│   └── operations.md                      # 生产部署与运维手册
├── config.example.yaml                    # 示例配置文件
├── go.mod                                 # Go 模块依赖定义
├── go.sum                                 # 依赖版本锁定文件
├── Makefile                               # 编译与测试自动化脚本
└── README.md                              # 项目主文档（本文件）
```

## 贡献指南

提交问题报告与功能请求。请使用 GitHub Issues 提交您遇到的问题或希望增加的功能，提交前请搜索已有议题以避免重复。报告问题时请附带完整的错误日志、配置文件脱敏版本以及能够复现问题的示例链接列表。

代码贡献流程。从 main 分支创建新的特性分支，遵循项目的代码风格规范（使用 gofmt 与 golint），为新增或修改的代码编写对应的单元测试，确保所有测试通过后提交 Pull Request。PR 描述中请清晰说明改动目的、实现方案及影响范围。

文档完善与翻译。欢迎对项目文档进行修正、补充或翻译。文档采用 Markdown 格式编写，图表使用 Mermaid 语法。翻译时请保持术语一致性，并同步更新中文与英文版本。

## 常见问题

启动时提示 Redis 连接失败，但我不想使用 Redis 怎么办？

系统默认启用 Redis 作为任务队列后端。如果您的环境中没有 Redis，可以在配置文件中将 `queue.backend` 设置为 `memory`，系统将使用内存队列作为替代。但请注意，内存模式不支持多进程并发消费，且在服务重启后会丢失队列中未处理的任务，仅建议在开发测试场景下使用。

导入包含大量链接的文件后，为什么扫描进度停滞不前？

系统默认的并发探测数量为 20，且每个请求的超时时间为 30 秒。如果您的网络环境访问某些域名较慢，或目标服务器响应延迟较高，整体扫描时间会显著延长。您可以通过配置文件调整 `scanner.concurrency` 和 `scanner.timeout` 参数。另外，请检查您的网络出口是否对目标域名有访问限制，必要时配置代理。

如何迁移 SQLite 数据到 PostgreSQL 生产环境？

项目提供了数据导出导入脚本 `manage.py dump` 和 `manage.py load`。首先在 SQLite 环境下执行 `python manage.py dump --format json --output data.json` 导出所有数据，然后在 PostgreSQL 环境下初始化数据库结构，最后执行 `python manage.py load --input data.json` 完成数据导入。导入前请确保 PostgreSQL 的 schema 与 SQLite 版本对齐，建议使用相同版本的迁移脚本。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:13
