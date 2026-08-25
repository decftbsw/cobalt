# OEXNR News Aggregator

OEXNR News Aggregator 是一个面向移动端的技术资讯与行业动态聚合平台，专注于从互联网海量信息中筛选、归类并呈现高价值的技术新闻报道。项目定位为技术决策者、研发工程师及产品经理提供一站式新闻聚合服务，通过自动化采集与人工审核相结合的方式，解决技术资讯分散、阅读成本高、信息过载等问题。

本项目为第 7/300 批次资源收录计划，总计收录 300 个新闻链接资源，当前批次已完成 300 个条目的结构化归档。项目提供完整的新闻索引、分类检索与历史回溯能力，适用于个人阅读、团队知识库建设及第三方数据集成场景。

## 功能概览

**多维度新闻索引**：支持按发布时间、新闻类别、关键词标签对收录链接进行索引与筛选，提供高效的信息定位能力。

**移动端优先阅读体验**：所有收录链接均针对移动设备浏览进行适配优化，确保在手机端获得流畅的阅读体验。

**自动化采集流水线**：集成定时抓取脚本，可对指定源站进行增量式新闻采集，自动识别新发布内容并纳入索引。

**全文检索与高级过滤**：内置标题与摘要全文检索功能，支持按日期范围、来源域名、内容类型进行组合过滤查询。

**历史归档与版本追溯**：对已收录新闻链接进行持久化归档，保留采集时间戳与内容摘要，支持历史数据导出。

**开放数据 API 接口**：提供 RESTful API 接口，允许第三方应用获取新闻列表、详情数据及增量更新内容。

**标签化分类体系**：为每篇新闻自动生成技术领域标签，包括但不限于人工智能、云计算、前端开发、安全运维、产品设计等。

## 应用场景

个人技术阅读者每日获取行业动态。开发人员或技术管理者可在每日晨间通过 OEXNR News Aggregator 快速浏览过去 24 小时内的技术新闻摘要，通过链接直达原文，节省自主搜索与筛选的时间成本。

技术团队构建内部知识库。团队可将项目作为新闻数据源，通过 API 接口将精选新闻导入团队 Wiki 或协作平台，形成长期积累的技术资讯知识库，用于新人培训与方案参考。

第三方数据服务商进行内容集成。自媒体平台、数据分析公司或舆情监测系统可通过项目提供的结构化数据输出，将新闻链接与元数据整合到自身业务流程中，扩展数据维度。

学术研究人员进行媒体趋势分析。研究人员可导出历史新闻列表进行内容分析、关键词频次统计与主题演化研究，支撑传播学或科技社会学方向的课题。

## 快速开始

以下命令展示如何从 GitHub 克隆项目、安装依赖并启动本地开发服务。

```bash
git clone https://github.com/oexnr/news-aggregator.git
cd news-aggregator
npm install
npm run dev
```

执行完毕后，访问本地端口 3000 即可看到新闻聚合首页，所有已收录链接将按照时间倒序排列展示。如需构建生产环境静态文件，请使用 `npm run build` 命令。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 18.0.0 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 | 包管理器，用于安装第三方依赖库 |
| SQLite 3 | >= 3.35.0 | 默认数据库引擎，用于存储新闻索引数据 |
| TypeScript | >= 5.0.0 | 开发时依赖，项目采用 TypeScript 编写 |
| Playwright | >= 1.32.0 | 浏览器自动化框架，用于新闻内容采集 |
| node-cron | >= 3.0.0 | 任务调度库，用于配置定时采集策略 |
| dotenv | >= 16.0.0 | 环境变量管理，用于敏感配置项隔离 |
| express | >= 4.18.0 | Web 服务器框架，提供 API 与静态服务 |
| marked | >= 4.3.0 | Markdown 解析器，用于渲染新闻内容摘要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门 | docs/quick-start.md | 如何在一分钟内启动项目并看到效果；如何配置环境变量与端口 |
| 开发 | docs/development-guide.md | 如何参与项目开发；代码结构与编码规范；提交 PR 的流程 |
| 运维 | docs/deployment.md | 如何部署到生产服务器；如何配置定时采集任务与日志轮转 |
| API | docs/api-reference.md | 有哪些公开接口；请求参数与返回结构；如何调用 API 获取新闻数据 |
| 数据 | docs/data-schema.md | 数据库表结构设计；字段含义与索引策略；数据迁移方法 |
| 贡献 | docs/contributing.md | 如何提交新闻源建议；如何改进采集规则；翻译与文档贡献方式 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/91497.htm
- http://m.3g.oexnr.cn/nnews/848981.htm
- http://m.3g.oexnr.cn/nnews/3327915.htm
- http://m.3g.oexnr.cn/nnews/5205913.htm
- http://m.3g.oexnr.cn/nnews/0848171.htm
- http://m.3g.oexnr.cn/nnews/644619.htm
- http://m.3g.oexnr.cn/nnews/9869611.htm
- http://m.3g.oexnr.cn/nnews/9773.htm
- http://m.3g.oexnr.cn/nnews/5271.htm
- http://m.3g.oexnr.cn/nnews/1628.htm
- http://m.3g.oexnr.cn/nnews/310850.htm
- http://m.3g.oexnr.cn/nnews/95014.htm
- http://m.3g.oexnr.cn/nnews/6782982.htm
- http://m.3g.oexnr.cn/nnews/360743.htm
- http://m.3g.oexnr.cn/nnews/8380.htm
- http://m.3g.oexnr.cn/nnews/6591831.htm
- http://m.3g.oexnr.cn/nnews/9674.htm
- http://m.3g.oexnr.cn/nnews/047348.htm
- http://m.3g.oexnr.cn/nnews/1226969.htm
- http://m.3g.oexnr.cn/nnews/2628.htm
- http://m.3g.oexnr.cn/nnews/24848.htm
- http://m.3g.oexnr.cn/nnews/791990.htm
- http://m.3g.oexnr.cn/nnews/877737.htm
- http://m.3g.oexnr.cn/nnews/4699458.htm
- http://m.3g.oexnr.cn/nnews/5625960.htm
- http://m.3g.oexnr.cn/nnews/5408304.htm
- http://m.3g.oexnr.cn/nnews/58141.htm
- http://m.3g.oexnr.cn/nnews/138799.htm
- http://m.3g.oexnr.cn/nnews/9812407.htm
- http://m.3g.oexnr.cn/nnews/811285.htm
- http://m.3g.oexnr.cn/nnews/357581.htm
- http://m.3g.oexnr.cn/nnews/17094.htm
- http://m.3g.oexnr.cn/nnews/07502.htm
- http://m.3g.oexnr.cn/nnews/750473.htm
- http://m.3g.oexnr.cn/nnews/48665.htm
- http://m.3g.oexnr.cn/nnews/5230144.htm
- http://m.3g.oexnr.cn/nnews/38765.htm
- http://m.3g.oexnr.cn/nnews/313202.htm
- http://m.3g.oexnr.cn/nnews/337839.htm
- http://m.3g.oexnr.cn/nnews/0264.htm
- http://m.3g.oexnr.cn/nnews/2954.htm
- http://m.3g.oexnr.cn/nnews/9624295.htm
- http://m.3g.oexnr.cn/nnews/8687.htm
- http://m.3g.oexnr.cn/nnews/44109.htm
- http://m.3g.oexnr.cn/nnews/471487.htm
- http://m.3g.oexnr.cn/nnews/9995.htm
- http://m.3g.oexnr.cn/nnews/62026.htm
- http://m.3g.oexnr.cn/nnews/57055.htm
- http://m.3g.oexnr.cn/nnews/05028.htm
- http://m.3g.oexnr.cn/nnews/183847.htm
- http://m.3g.oexnr.cn/nnews/4656304.htm
- http://m.3g.oexnr.cn/nnews/43713.htm
- http://m.3g.oexnr.cn/nnews/26961.htm
- http://m.3g.oexnr.cn/nnews/5384815.htm
- http://m.3g.oexnr.cn/nnews/044165.htm
- http://m.3g.oexnr.cn/nnews/73759.htm
- http://m.3g.oexnr.cn/nnews/92321.htm
- http://m.3g.oexnr.cn/nnews/223306.htm
- http://m.3g.oexnr.cn/nnews/470289.htm
- http://m.3g.oexnr.cn/nnews/75133.htm
- http://m.3g.oexnr.cn/nnews/248711.htm
- http://m.3g.oexnr.cn/nnews/6199.htm
- http://m.3g.oexnr.cn/nnews/2319.htm
- http://m.3g.oexnr.cn/nnews/314110.htm
- http://m.3g.oexnr.cn/nnews/87326.htm
- http://m.3g.oexnr.cn/nnews/8854881.htm
- http://m.3g.oexnr.cn/nnews/5853677.htm
- http://m.3g.oexnr.cn/nnews/577611.htm
- http://m.3g.oexnr.cn/nnews/7166350.htm
- http://m.3g.oexnr.cn/nnews/13989.htm
- http://m.3g.oexnr.cn/nnews/512493.htm
- http://m.3g.oexnr.cn/nnews/52935.htm
- http://m.3g.oexnr.cn/nnews/31232.htm
- http://m.3g.oexnr.cn/nnews/2585.htm
- http://m.3g.oexnr.cn/nnews/21447.htm
- http://m.3g.oexnr.cn/nnews/9106646.htm
- http://m.3g.oexnr.cn/nnews/665854.htm
- http://m.3g.oexnr.cn/nnews/2615.htm
- http://m.3g.oexnr.cn/nnews/10044.htm
- http://m.3g.oexnr.cn/nnews/2292294.htm
- http://m.3g.oexnr.cn/nnews/04124.htm
- http://m.3g.oexnr.cn/nnews/2221019.htm
- http://m.3g.oexnr.cn/nnews/45099.htm
- http://m.3g.oexnr.cn/nnews/1441.htm
- http://m.3g.oexnr.cn/nnews/833505.htm
- http://m.3g.oexnr.cn/nnews/6796522.htm
- http://m.3g.oexnr.cn/nnews/6054.htm
- http://m.3g.oexnr.cn/nnews/1568717.htm
- http://m.3g.oexnr.cn/nnews/2468.htm
- http://m.3g.oexnr.cn/nnews/21330.htm
- http://m.3g.oexnr.cn/nnews/5740477.htm
- http://m.3g.oexnr.cn/nnews/87484.htm
- http://m.3g.oexnr.cn/nnews/90034.htm
- http://m.3g.oexnr.cn/nnews/507147.htm
- http://m.3g.oexnr.cn/nnews/3536.htm
- http://m.3g.oexnr.cn/nnews/8883.htm
- http://m.3g.oexnr.cn/nnews/06358.htm
- http://m.3g.oexnr.cn/nnews/7536220.htm
- http://m.3g.oexnr.cn/nnews/37879.htm
- http://m.3g.oexnr.cn/nnews/58560.htm
- http://m.3g.oexnr.cn/nnews/89967.htm
- http://m.3g.oexnr.cn/nnews/24543.htm
- http://m.3g.oexnr.cn/nnews/558420.htm
- http://m.3g.oexnr.cn/nnews/79907.htm
- http://m.3g.oexnr.cn/nnews/3197.htm
- http://m.3g.oexnr.cn/nnews/559798.htm
- http://m.3g.oexnr.cn/nnews/03186.htm
- http://m.3g.oexnr.cn/nnews/9011607.htm
- http://m.3g.oexnr.cn/nnews/92504.htm
- http://m.3g.oexnr.cn/nnews/54944.htm
- http://m.3g.oexnr.cn/nnews/6128856.htm
- http://m.3g.oexnr.cn/nnews/606965.htm
- http://m.3g.oexnr.cn/nnews/1941699.htm
- http://m.3g.oexnr.cn/nnews/3450.htm
- http://m.3g.oexnr.cn/nnews/0835.htm
- http://m.3g.oexnr.cn/nnews/938858.htm
- http://m.3g.oexnr.cn/nnews/126870.htm
- http://m.3g.oexnr.cn/nnews/4367063.htm
- http://m.3g.oexnr.cn/nnews/32701.htm
- http://m.3g.oexnr.cn/nnews/96687.htm
- http://m.3g.oexnr.cn/nnews/8610.htm
- http://m.3g.oexnr.cn/nnews/55565.htm
- http://m.3g.oexnr.cn/nnews/77861.htm
- http://m.3g.oexnr.cn/nnews/45050.htm
- http://m.3g.oexnr.cn/nnews/188923.htm
- http://m.3g.oexnr.cn/nnews/869224.htm
- http://m.3g.oexnr.cn/nnews/708871.htm
- http://m.3g.oexnr.cn/nnews/42227.htm
- http://m.3g.oexnr.cn/nnews/8748471.htm
- http://m.3g.oexnr.cn/nnews/9260.htm
- http://m.3g.oexnr.cn/nnews/6879.htm
- http://m.3g.oexnr.cn/nnews/49547.htm
- http://m.3g.oexnr.cn/nnews/888778.htm
- http://m.3g.oexnr.cn/nnews/298573.htm
- http://m.3g.oexnr.cn/nnews/53755.htm
- http://m.3g.oexnr.cn/nnews/16416.htm
- http://m.3g.oexnr.cn/nnews/0880.htm
- http://m.3g.oexnr.cn/nnews/6943.htm
- http://m.3g.oexnr.cn/nnews/6458865.htm
- http://m.3g.oexnr.cn/nnews/0693050.htm
- http://m.3g.oexnr.cn/nnews/5997.htm
- http://m.3g.oexnr.cn/nnews/2865.htm
- http://m.3g.oexnr.cn/nnews/3325.htm
- http://m.3g.oexnr.cn/nnews/0184260.htm
- http://m.3g.oexnr.cn/nnews/96137.htm
- http://m.3g.oexnr.cn/nnews/1141.htm
- http://m.3g.oexnr.cn/nnews/74822.htm
- http://m.3g.oexnr.cn/nnews/4448921.htm
- http://m.3g.oexnr.cn/nnews/7005930.htm
- http://m.3g.oexnr.cn/nnews/129424.htm
- http://m.3g.oexnr.cn/nnews/1145733.htm
- http://m.3g.oexnr.cn/nnews/5387.htm
- http://m.3g.oexnr.cn/nnews/8351763.htm
- http://m.3g.oexnr.cn/nnews/5266990.htm
- http://m.3g.oexnr.cn/nnews/745854.htm
- http://m.3g.oexnr.cn/nnews/931801.htm
- http://m.3g.oexnr.cn/nnews/251592.htm
- http://m.3g.oexnr.cn/nnews/098663.htm
- http://m.3g.oexnr.cn/nnews/07428.htm
- http://m.3g.oexnr.cn/nnews/6812184.htm
- http://m.3g.oexnr.cn/nnews/059631.htm
- http://m.3g.oexnr.cn/nnews/504138.htm
- http://m.3g.oexnr.cn/nnews/0902301.htm
- http://m.3g.oexnr.cn/nnews/18720.htm
- http://m.3g.oexnr.cn/nnews/1768.htm
- http://m.3g.oexnr.cn/nnews/6893.htm
- http://m.3g.oexnr.cn/nnews/78203.htm
- http://m.3g.oexnr.cn/nnews/9856.htm
- http://m.3g.oexnr.cn/nnews/839644.htm
- http://m.3g.oexnr.cn/nnews/96515.htm
- http://m.3g.oexnr.cn/nnews/4726344.htm
- http://m.3g.oexnr.cn/nnews/4819923.htm
- http://m.3g.oexnr.cn/nnews/0892522.htm
- http://m.3g.oexnr.cn/nnews/86719.htm
- http://m.3g.oexnr.cn/nnews/200345.htm
- http://m.3g.oexnr.cn/nnews/55651.htm
- http://m.3g.oexnr.cn/nnews/7909812.htm
- http://m.3g.oexnr.cn/nnews/206182.htm
- http://m.3g.oexnr.cn/nnews/822716.htm
- http://m.3g.oexnr.cn/nnews/7980.htm
- http://m.3g.oexnr.cn/nnews/027498.htm
- http://m.3g.oexnr.cn/nnews/0001811.htm
- http://m.3g.oexnr.cn/nnews/65893.htm
- http://m.3g.oexnr.cn/nnews/160432.htm
- http://m.3g.oexnr.cn/nnews/6437.htm
- http://m.3g.oexnr.cn/nnews/8410.htm
- http://m.3g.oexnr.cn/nnews/5577.htm
- http://m.3g.oexnr.cn/nnews/637395.htm
- http://m.3g.oexnr.cn/nnews/3643.htm
- http://m.3g.oexnr.cn/nnews/5934127.htm
- http://m.3g.oexnr.cn/nnews/099926.htm
- http://m.3g.oexnr.cn/nnews/5036503.htm
- http://m.3g.oexnr.cn/nnews/530219.htm
- http://m.3g.oexnr.cn/nnews/1061.htm
- http://m.3g.oexnr.cn/nnews/63750.htm
- http://m.3g.oexnr.cn/nnews/61992.htm
- http://m.3g.oexnr.cn/nnews/8226.htm
- http://m.3g.oexnr.cn/nnews/1164278.htm
- http://m.3g.oexnr.cn/nnews/4075.htm
- http://m.3g.oexnr.cn/nnews/5962.htm
- http://m.3g.oexnr.cn/nnews/109229.htm
- http://m.3g.oexnr.cn/nnews/98448.htm
- http://m.3g.oexnr.cn/nnews/1851453.htm
- http://m.3g.oexnr.cn/nnews/116544.htm
- http://m.3g.oexnr.cn/nnews/766494.htm
- http://m.3g.oexnr.cn/nnews/961963.htm
- http://m.3g.oexnr.cn/nnews/9396.htm
- http://m.3g.oexnr.cn/nnews/7010.htm
- http://m.3g.oexnr.cn/nnews/5154011.htm
- http://m.3g.oexnr.cn/nnews/3538337.htm
- http://m.3g.oexnr.cn/nnews/3052100.htm
- http://m.3g.oexnr.cn/nnews/3740684.htm
- http://m.3g.oexnr.cn/nnews/4148.htm
- http://m.3g.oexnr.cn/nnews/7650.htm
- http://m.3g.oexnr.cn/nnews/2907809.htm
- http://m.3g.oexnr.cn/nnews/36196.htm
- http://m.3g.oexnr.cn/nnews/6861.htm
- http://m.3g.oexnr.cn/nnews/01138.htm
- http://m.3g.oexnr.cn/nnews/532457.htm
- http://m.3g.oexnr.cn/nnews/7467.htm
- http://m.3g.oexnr.cn/nnews/8126069.htm
- http://m.3g.oexnr.cn/nnews/4593.htm
- http://m.3g.oexnr.cn/nnews/9144.htm
- http://m.3g.oexnr.cn/nnews/07788.htm
- http://m.3g.oexnr.cn/nnews/2131783.htm
- http://m.3g.oexnr.cn/nnews/332123.htm
- http://m.3g.oexnr.cn/nnews/7703.htm
- http://m.3g.oexnr.cn/nnews/336254.htm
- http://m.3g.oexnr.cn/nnews/1376.htm
- http://m.3g.oexnr.cn/nnews/9041397.htm
- http://m.3g.oexnr.cn/nnews/74391.htm
- http://m.3g.oexnr.cn/nnews/1030.htm
- http://m.3g.oexnr.cn/nnews/28202.htm
- http://m.3g.oexnr.cn/nnews/564820.htm
- http://m.3g.oexnr.cn/nnews/30633.htm
- http://m.3g.oexnr.cn/nnews/97250.htm
- http://m.3g.oexnr.cn/nnews/28336.htm
- http://m.3g.oexnr.cn/nnews/873521.htm
- http://m.3g.oexnr.cn/nnews/4354668.htm
- http://m.3g.oexnr.cn/nnews/74908.htm
- http://m.3g.oexnr.cn/nnews/5157689.htm
- http://m.3g.oexnr.cn/nnews/3249.htm
- http://m.3g.oexnr.cn/nnews/942223.htm
- http://m.3g.oexnr.cn/nnews/8242083.htm
- http://m.3g.oexnr.cn/nnews/35166.htm
- http://m.3g.oexnr.cn/nnews/754154.htm
- http://m.3g.oexnr.cn/nnews/2914076.htm
- http://m.3g.oexnr.cn/nnews/68689.htm
- http://m.3g.oexnr.cn/nnews/302358.htm
- http://m.3g.oexnr.cn/nnews/3832.htm
- http://m.3g.oexnr.cn/nnews/9561361.htm
- http://m.3g.oexnr.cn/nnews/5344.htm
- http://m.3g.oexnr.cn/nnews/125524.htm
- http://m.3g.oexnr.cn/nnews/1542962.htm
- http://m.3g.oexnr.cn/nnews/954172.htm
- http://m.3g.oexnr.cn/nnews/411604.htm
- http://m.3g.oexnr.cn/nnews/067358.htm
- http://m.3g.oexnr.cn/nnews/52123.htm
- http://m.3g.oexnr.cn/nnews/7951.htm
- http://m.3g.oexnr.cn/nnews/533261.htm
- http://m.3g.oexnr.cn/nnews/689101.htm
- http://m.3g.oexnr.cn/nnews/2324669.htm
- http://m.3g.oexnr.cn/nnews/3294014.htm
- http://m.3g.oexnr.cn/nnews/4025.htm
- http://m.3g.oexnr.cn/nnews/577999.htm
- http://m.3g.oexnr.cn/nnews/6898.htm
- http://m.3g.oexnr.cn/nnews/978813.htm
- http://m.3g.oexnr.cn/nnews/634513.htm
- http://m.3g.oexnr.cn/nnews/8872.htm
- http://m.3g.oexnr.cn/nnews/22518.htm
- http://m.3g.oexnr.cn/nnews/94224.htm
- http://m.3g.oexnr.cn/nnews/3316.htm
- http://m.3g.oexnr.cn/nnews/75096.htm
- http://m.3g.oexnr.cn/nnews/435956.htm
- http://m.3g.oexnr.cn/nnews/80318.htm
- http://m.3g.oexnr.cn/nnews/2540428.htm
- http://m.3g.oexnr.cn/nnews/099238.htm
- http://m.3g.oexnr.cn/nnews/4868.htm
- http://m.3g.oexnr.cn/nnews/6201554.htm
- http://m.3g.oexnr.cn/nnews/996509.htm
- http://m.3g.oexnr.cn/nnews/5169726.htm
- http://m.3g.oexnr.cn/nnews/936671.htm
- http://m.3g.oexnr.cn/nnews/6823750.htm
- http://m.3g.oexnr.cn/nnews/608602.htm
- http://m.3g.oexnr.cn/nnews/19167.htm
- http://m.3g.oexnr.cn/nnews/944804.htm
- http://m.3g.oexnr.cn/nnews/8394.htm
- http://m.3g.oexnr.cn/nnews/761958.htm
- http://m.3g.oexnr.cn/nnews/5636.htm
- http://m.3g.oexnr.cn/nnews/4638.htm
- http://m.3g.oexnr.cn/nnews/2478.htm
- http://m.3g.oexnr.cn/nnews/4953333.htm
- http://m.3g.oexnr.cn/nnews/8965007.htm
- http://m.3g.oexnr.cn/nnews/653697.htm
- http://m.3g.oexnr.cn/nnews/5214.htm
- http://m.3g.oexnr.cn/nnews/2835.htm
- http://m.3g.oexnr.cn/nnews/4196.htm
- http://m.3g.oexnr.cn/nnews/527747.htm
- http://m.3g.oexnr.cn/nnews/67352.htm
- http://m.3g.oexnr.cn/nnews/065440.htm

## 项目结构

```
news-aggregator/
├── src/
│   ├── core/                     # 核心业务逻辑模块
│   │   ├── collector.ts          # 新闻采集器主控流程
│   │   ├── parser.ts             # HTML 内容解析与摘要生成
│   │   └── indexer.ts            # 新闻索引管理
│   ├── api/                      # RESTful API 接口层
│   │   ├── routes.ts             # 路由定义与挂载
│   │   ├── controllers.ts        # 请求控制器
│   │   └── validators.ts         # 请求参数校验
│   ├── db/                       # 数据库层
│   │   ├── client.ts             # SQLite 连接与池管理
│   │   ├── migrations/           # 数据库迁移脚本
│   │   └── repositories/         # 数据访问对象
│   ├── scheduler/                # 定时任务模块
│   │   ├── cron.ts               # 任务调度配置
│   │   └── jobs/                 # 具体任务实现
│   ├── utils/                    # 通用工具函数
│   │   ├── logger.ts             # 日志记录器
│   │   ├── config.ts             # 配置加载器
│   │   └── validator.ts          # 数据验证工具
│   └── types/                    # TypeScript 类型定义
│       ├── news.ts               # 新闻实体类型
│       └── api.ts                # API 请求响应类型
├── tests/                        # 单元测试与集成测试
├── docs/                         # 项目文档目录
├── scripts/                      # 运维辅助脚本
│   ├── seed.ts                   # 初始数据填充
│   └── backup.ts                 # 数据库备份脚本
├── public/                       # 静态资源目录
├── .env.example                  # 环境变量模板
├── package.json                  # 依赖管理文件
├── tsconfig.json                 # TypeScript 编译配置
├── docker-compose.yml            # Docker 编排文件
└── README.md                     # 项目说明文档
```

## 贡献指南

首先，请在 GitHub 仓库中提交 Issue 说明您希望解决的问题或新增的功能，等待维护者确认后再开始编码工作，避免重复劳动或不必要的代码改动。

其次，Fork 本仓库到您的个人账号下，创建以 `feature/` 或 `fix/` 为前缀的功能分支进行开发，提交代码时请遵循项目的代码规范与提交信息格式要求。

第三，编写或更新相应的单元测试用例，确保代码覆盖率达到 80% 以上，并在本地运行 `npm test` 通过全部测试套件后方可提交 Pull Request。

第四，提交 Pull Request 时请填写完整的模板信息，包括变更摘要、测试情况、相关 Issue 编号，并等待至少一位维护者进行 Code Review 与合并。

第五，如您希望长期参与项目维护，可申请加入 Contributors 团队，获得直接推送权限并参与版本发布决策。

## 常见问题

**问：项目是否支持添加自定义新闻源？**

答：支持。您可以在 `src/core/collector.ts` 中扩展新闻源配置数组，添加新的源站 URL 与对应的解析规则。对于结构较为复杂的源站，可能需要编写自定义解析函数。欢迎通过 Pull Request 提交通用性较强的源站适配器。

**问：定时采集任务如何配置执行频率？**

答：定时任务使用 node-cron 表达式进行配置，您可以在 `.env` 文件中设置 `CRON_SCHEDULE` 变量，默认值为 `0 8,12,18 * * *` 表示每天 8 点、12 点、18 点执行采集。修改后重启服务即可生效。

**问：项目是否支持 PostgreSQL 或 MySQL？**

答：当前版本默认使用 SQLite 作为数据库，适合单机部署与开发测试。如需使用 PostgreSQL 或 MySQL，可自行修改 `src/db/client.ts` 中的数据库连接适配器，项目已预留数据库抽象层接口，欢迎贡献对应数据库的适配实现。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
