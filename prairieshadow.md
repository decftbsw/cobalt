# NewsDigest Index

NewsDigest Index 是一个面向技术信息检索与新闻聚合场景的轻量化外部链接索引系统。该项目定位于为开发者、数据分析师与信息聚合服务提供稳定的新闻条目引用源，通过结构化存储与分类索引机制，将分散的外部新闻链接转换为可编程访问的资源目录。项目本身不存储新闻正文，仅维护链接元数据与分类标签，适用于构建自定义新闻聚合页、舆情监控系统的数据源层，或作为静态站点生成器的内容引用后端。

## 功能概览

**链接索引存储** 以扁平化结构存储外部新闻链接，每条记录保留原始 URL、抓取时间与内容摘要哈希，支持快速查重与批量导入。

**分类标签系统** 基于 URL 路径与内容特征自动生成分类标签，支持人工覆写，便于按主题聚合展示。

**元数据提取管线** 对每个链接执行可配置的元数据提取流程，包括标题抽取、正文摘要生成与发布时间推断。

**批量导入导出** 支持 CSV 与 JSON 格式的链接批量导入，导出功能兼容主流数据处理工具与静态站点生成器。

**去重与更新检测** 基于内容哈希比对实现增量更新，避免重复收录，同时标记内容发生变更的历史链接。

**查询过滤接口** 提供按时间范围、分类标签、域名过滤的查询接口，返回结果支持分页与排序。

**健康状态监控** 定期检查每个链接的可达性，标记失效链接并记录 HTTP 状态码变化趋势。

**访问统计聚合** 统计每个链接的引用次数、最后访问时间与来源 IP 分布，用于热度分析。

## 应用场景

**技术新闻每日汇总** 运维人员可将该项目部署为内部新闻聚合器的后端，每日定时抓取指定链接列表，生成包含标题、摘要与原文链接的日报邮件。

**舆情监控系统数据源** 数据分析团队利用该项目维护的索引表，结合外部 NLP 服务对链接内容进行情感分析与实体识别，构建轻量级舆情看板。

**静态博客引用管理** 博客作者使用该项目管理外部引用链接，在文章发布前通过 API 校验链接有效性，避免生成包含死链的页面。

**竞品动态追踪** 产品经理将竞品官方新闻页面的链接纳入索引，通过变更检测功能及时发现内容更新，辅助决策分析。

## 快速开始

以下命令演示了从克隆仓库到启动服务的完整流程。

```bash
git clone https://github.com/your-org/newsdigest-index.git
cd newsdigest-index
pip install -r requirements.txt
cp .env.example .env
python scripts/init_db.py
python app.py
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高 | 核心运行环境，类型提示与异步特性依赖 |
| SQLite | 3.35 或更高 | 内置数据库，用于存储链接索引与元数据 |
| aiohttp | 3.8.4 或更高 | 异步 HTTP 客户端，用于并发抓取链接内容 |
| beautifulsoup4 | 4.12.0 或更高 | HTML 解析器，用于提取页面标题与正文 |
| lxml | 4.9.0 或更高 | 底层 XML/HTML 解析引擎，提升解析性能 |
| python-dotenv | 1.0.0 或更高 | 环境变量加载，用于配置敏感参数 |
| pytest | 7.4.0 或更高 | 单元测试框架，仅在开发模式下需要 |
| redis | 5.0.0 或更高 | 可选缓存组件，用于提升查询响应速度 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何配置抓取规则、管理链接列表、查看统计报表 |
| 开发指南 | docs/development.md | 如何扩展新的元数据提取器、修改分类逻辑、编写测试用例 |
| 运维手册 | docs/operations.md | 如何部署到生产环境、配置定时任务、备份与恢复数据 |
| API 参考 | docs/api-reference.md | 查询接口的请求参数与响应格式、错误码含义 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/9463.htm
- http://m.3g.oexnr.cn/nnews/4844.htm
- http://m.3g.oexnr.cn/nnews/1240.htm
- http://m.3g.oexnr.cn/nnews/8168156.htm
- http://m.3g.oexnr.cn/nnews/50034.htm
- http://m.3g.oexnr.cn/nnews/1896282.htm
- http://m.3g.oexnr.cn/nnews/7389544.htm
- http://m.3g.oexnr.cn/nnews/5852.htm
- http://m.3g.oexnr.cn/nnews/76188.htm
- http://m.3g.oexnr.cn/nnews/5560.htm
- http://m.3g.oexnr.cn/nnews/84878.htm
- http://m.3g.oexnr.cn/nnews/00719.htm
- http://m.3g.oexnr.cn/nnews/759181.htm
- http://m.3g.oexnr.cn/nnews/0935530.htm
- http://m.3g.oexnr.cn/nnews/6207014.htm
- http://m.3g.oexnr.cn/nnews/7660.htm
- http://m.3g.oexnr.cn/nnews/351172.htm
- http://m.3g.oexnr.cn/nnews/5539.htm
- http://m.3g.oexnr.cn/nnews/3765.htm
- http://m.3g.oexnr.cn/nnews/1284.htm
- http://m.3g.oexnr.cn/nnews/9231.htm
- http://m.3g.oexnr.cn/nnews/9756492.htm
- http://m.3g.oexnr.cn/nnews/08594.htm
- http://m.3g.oexnr.cn/nnews/110503.htm
- http://m.3g.oexnr.cn/nnews/1671.htm
- http://m.3g.oexnr.cn/nnews/141700.htm
- http://m.3g.oexnr.cn/nnews/38564.htm
- http://m.3g.oexnr.cn/nnews/20691.htm
- http://m.3g.oexnr.cn/nnews/79063.htm
- http://m.3g.oexnr.cn/nnews/5269069.htm
- http://m.3g.oexnr.cn/nnews/626830.htm
- http://m.3g.oexnr.cn/nnews/574505.htm
- http://m.3g.oexnr.cn/nnews/761051.htm
- http://m.3g.oexnr.cn/nnews/1655.htm
- http://m.3g.oexnr.cn/nnews/8841508.htm
- http://m.3g.oexnr.cn/nnews/66883.htm
- http://m.3g.oexnr.cn/nnews/673305.htm
- http://m.3g.oexnr.cn/nnews/00504.htm
- http://m.3g.oexnr.cn/nnews/5785833.htm
- http://m.3g.oexnr.cn/nnews/1540.htm
- http://m.3g.oexnr.cn/nnews/4563.htm
- http://m.3g.oexnr.cn/nnews/902455.htm
- http://m.3g.oexnr.cn/nnews/63327.htm
- http://m.3g.oexnr.cn/nnews/3687028.htm
- http://m.3g.oexnr.cn/nnews/21083.htm
- http://m.3g.oexnr.cn/nnews/80230.htm
- http://m.3g.oexnr.cn/nnews/8145.htm
- http://m.3g.oexnr.cn/nnews/941350.htm
- http://m.3g.oexnr.cn/nnews/119061.htm
- http://m.3g.oexnr.cn/nnews/5086357.htm
- http://m.3g.oexnr.cn/nnews/449273.htm
- http://m.3g.oexnr.cn/nnews/544041.htm
- http://m.3g.oexnr.cn/nnews/9530937.htm
- http://m.3g.oexnr.cn/nnews/525571.htm
- http://m.3g.oexnr.cn/nnews/8641.htm
- http://m.3g.oexnr.cn/nnews/3249271.htm
- http://m.3g.oexnr.cn/nnews/4785529.htm
- http://m.3g.oexnr.cn/nnews/72730.htm
- http://m.3g.oexnr.cn/nnews/6740598.htm
- http://m.3g.oexnr.cn/nnews/6969.htm
- http://m.3g.oexnr.cn/nnews/50245.htm
- http://m.3g.oexnr.cn/nnews/807660.htm
- http://m.3g.oexnr.cn/nnews/6127046.htm
- http://m.3g.oexnr.cn/nnews/619273.htm
- http://m.3g.oexnr.cn/nnews/1221.htm
- http://m.3g.oexnr.cn/nnews/2430.htm
- http://m.3g.oexnr.cn/nnews/177095.htm
- http://m.3g.oexnr.cn/nnews/72737.htm
- http://m.3g.oexnr.cn/nnews/5031.htm
- http://m.3g.oexnr.cn/nnews/2317.htm
- http://m.3g.oexnr.cn/nnews/5466.htm
- http://m.3g.oexnr.cn/nnews/5211.htm
- http://m.3g.oexnr.cn/nnews/271506.htm
- http://m.3g.oexnr.cn/nnews/902200.htm
- http://m.3g.oexnr.cn/nnews/97292.htm
- http://m.3g.oexnr.cn/nnews/2703.htm
- http://m.3g.oexnr.cn/nnews/4969.htm
- http://m.3g.oexnr.cn/nnews/645747.htm
- http://m.3g.oexnr.cn/nnews/8899966.htm
- http://m.3g.oexnr.cn/nnews/77327.htm
- http://m.3g.oexnr.cn/nnews/6389.htm
- http://m.3g.oexnr.cn/nnews/320657.htm
- http://m.3g.oexnr.cn/nnews/39797.htm
- http://m.3g.oexnr.cn/nnews/2728293.htm
- http://m.3g.oexnr.cn/nnews/4073.htm
- http://m.3g.oexnr.cn/nnews/19273.htm
- http://m.3g.oexnr.cn/nnews/7334199.htm
- http://m.3g.oexnr.cn/nnews/09443.htm
- http://m.3g.oexnr.cn/nnews/29793.htm
- http://m.3g.oexnr.cn/nnews/98132.htm
- http://m.3g.oexnr.cn/nnews/6030.htm
- http://m.3g.oexnr.cn/nnews/285592.htm
- http://m.3g.oexnr.cn/nnews/951542.htm
- http://m.3g.oexnr.cn/nnews/141143.htm
- http://m.3g.oexnr.cn/nnews/390561.htm
- http://m.3g.oexnr.cn/nnews/9923078.htm
- http://m.3g.oexnr.cn/nnews/888684.htm
- http://m.3g.oexnr.cn/nnews/07631.htm
- http://m.3g.oexnr.cn/nnews/8885.htm
- http://m.3g.oexnr.cn/nnews/56147.htm
- http://m.3g.oexnr.cn/nnews/61260.htm
- http://m.3g.oexnr.cn/nnews/1735163.htm
- http://m.3g.oexnr.cn/nnews/96898.htm
- http://m.3g.oexnr.cn/nnews/0989374.htm
- http://m.3g.oexnr.cn/nnews/5540.htm
- http://m.3g.oexnr.cn/nnews/82264.htm
- http://m.3g.oexnr.cn/nnews/4848.htm
- http://m.3g.oexnr.cn/nnews/8243746.htm
- http://m.3g.oexnr.cn/nnews/98334.htm
- http://m.3g.oexnr.cn/nnews/86610.htm
- http://m.3g.oexnr.cn/nnews/0724.htm
- http://m.3g.oexnr.cn/nnews/7812.htm
- http://m.3g.oexnr.cn/nnews/71236.htm
- http://m.3g.oexnr.cn/nnews/0870.htm
- http://m.3g.oexnr.cn/nnews/3588.htm
- http://m.3g.oexnr.cn/nnews/5323.htm
- http://m.3g.oexnr.cn/nnews/215869.htm
- http://m.3g.oexnr.cn/nnews/9742131.htm
- http://m.3g.oexnr.cn/nnews/70119.htm
- http://m.3g.oexnr.cn/nnews/674325.htm
- http://m.3g.oexnr.cn/nnews/519145.htm
- http://m.3g.oexnr.cn/nnews/2652940.htm
- http://m.3g.oexnr.cn/nnews/167827.htm
- http://m.3g.oexnr.cn/nnews/5639.htm
- http://m.3g.oexnr.cn/nnews/8760629.htm
- http://m.3g.oexnr.cn/nnews/72223.htm
- http://m.3g.oexnr.cn/nnews/54882.htm
- http://m.3g.oexnr.cn/nnews/12736.htm
- http://m.3g.oexnr.cn/nnews/2747458.htm
- http://m.3g.oexnr.cn/nnews/261810.htm
- http://m.3g.oexnr.cn/nnews/0323.htm
- http://m.3g.oexnr.cn/nnews/135912.htm
- http://m.3g.oexnr.cn/nnews/828792.htm
- http://m.3g.oexnr.cn/nnews/6611276.htm
- http://m.3g.oexnr.cn/nnews/3725603.htm
- http://m.3g.oexnr.cn/nnews/54248.htm
- http://m.3g.oexnr.cn/nnews/145658.htm
- http://m.3g.oexnr.cn/nnews/0339627.htm
- http://m.3g.oexnr.cn/nnews/2294.htm
- http://m.3g.oexnr.cn/nnews/3110749.htm
- http://m.3g.oexnr.cn/nnews/5668929.htm
- http://m.3g.oexnr.cn/nnews/8690089.htm
- http://m.3g.oexnr.cn/nnews/2323.htm
- http://m.3g.oexnr.cn/nnews/978589.htm
- http://m.3g.oexnr.cn/nnews/5880.htm
- http://m.3g.oexnr.cn/nnews/8446642.htm
- http://m.3g.oexnr.cn/nnews/9466.htm
- http://m.3g.oexnr.cn/nnews/45404.htm
- http://m.3g.oexnr.cn/nnews/963354.htm
- http://m.3g.oexnr.cn/nnews/298522.htm
- http://m.3g.oexnr.cn/nnews/572582.htm
- http://m.3g.oexnr.cn/nnews/8983.htm
- http://m.3g.oexnr.cn/nnews/926614.htm
- http://m.3g.oexnr.cn/nnews/90363.htm
- http://m.3g.oexnr.cn/nnews/1507539.htm
- http://m.3g.oexnr.cn/nnews/08068.htm
- http://m.3g.oexnr.cn/nnews/329161.htm
- http://m.3g.oexnr.cn/nnews/258964.htm
- http://m.3g.oexnr.cn/nnews/9275355.htm
- http://m.3g.oexnr.cn/nnews/383005.htm
- http://m.3g.oexnr.cn/nnews/032450.htm
- http://m.3g.oexnr.cn/nnews/935535.htm
- http://m.3g.oexnr.cn/nnews/74088.htm
- http://m.3g.oexnr.cn/nnews/3536500.htm
- http://m.3g.oexnr.cn/nnews/013202.htm
- http://m.3g.oexnr.cn/nnews/0365672.htm
- http://m.3g.oexnr.cn/nnews/1789.htm
- http://m.3g.oexnr.cn/nnews/355436.htm
- http://m.3g.oexnr.cn/nnews/67700.htm
- http://m.3g.oexnr.cn/nnews/7339.htm
- http://m.3g.oexnr.cn/nnews/67743.htm
- http://m.3g.oexnr.cn/nnews/9535082.htm
- http://m.3g.oexnr.cn/nnews/53296.htm
- http://m.3g.oexnr.cn/nnews/139303.htm
- http://m.3g.oexnr.cn/nnews/0821.htm
- http://m.3g.oexnr.cn/nnews/77361.htm
- http://m.3g.oexnr.cn/nnews/76935.htm
- http://m.3g.oexnr.cn/nnews/369809.htm
- http://m.3g.oexnr.cn/nnews/9694.htm
- http://m.3g.oexnr.cn/nnews/59250.htm
- http://m.3g.oexnr.cn/nnews/484533.htm
- http://m.3g.oexnr.cn/nnews/3892644.htm
- http://m.3g.oexnr.cn/nnews/8461.htm
- http://m.3g.oexnr.cn/nnews/4354.htm
- http://m.3g.oexnr.cn/nnews/539433.htm
- http://m.3g.oexnr.cn/nnews/3211184.htm
- http://m.3g.oexnr.cn/nnews/12428.htm
- http://m.3g.oexnr.cn/nnews/51383.htm
- http://m.3g.oexnr.cn/nnews/388667.htm
- http://m.3g.oexnr.cn/nnews/3692.htm
- http://m.3g.oexnr.cn/nnews/77494.htm
- http://m.3g.oexnr.cn/nnews/8949851.htm
- http://m.3g.oexnr.cn/nnews/2718614.htm
- http://m.3g.oexnr.cn/nnews/320028.htm
- http://m.3g.oexnr.cn/nnews/082206.htm
- http://m.3g.oexnr.cn/nnews/5663589.htm
- http://m.3g.oexnr.cn/nnews/68644.htm
- http://m.3g.oexnr.cn/nnews/940705.htm
- http://m.3g.oexnr.cn/nnews/30055.htm
- http://m.3g.oexnr.cn/nnews/795226.htm
- http://m.3g.oexnr.cn/nnews/86915.htm
- http://m.3g.oexnr.cn/nnews/1639628.htm
- http://m.3g.oexnr.cn/nnews/344672.htm
- http://m.3g.oexnr.cn/nnews/7151629.htm
- http://m.3g.oexnr.cn/nnews/8706951.htm
- http://m.3g.oexnr.cn/nnews/55313.htm
- http://m.3g.oexnr.cn/nnews/50910.htm
- http://m.3g.oexnr.cn/nnews/63791.htm
- http://m.3g.oexnr.cn/nnews/773796.htm
- http://m.3g.oexnr.cn/nnews/00103.htm
- http://m.3g.oexnr.cn/nnews/09629.htm
- http://m.3g.oexnr.cn/nnews/1135.htm
- http://m.3g.oexnr.cn/nnews/9996.htm
- http://m.3g.oexnr.cn/nnews/58889.htm
- http://m.3g.oexnr.cn/nnews/025548.htm
- http://m.3g.oexnr.cn/nnews/46884.htm
- http://m.3g.oexnr.cn/nnews/65853.htm
- http://m.3g.oexnr.cn/nnews/493512.htm
- http://m.3g.oexnr.cn/nnews/70368.htm
- http://m.3g.oexnr.cn/nnews/99780.htm
- http://m.3g.oexnr.cn/nnews/3928612.htm
- http://m.3g.oexnr.cn/nnews/024504.htm
- http://m.3g.oexnr.cn/nnews/6863668.htm
- http://m.3g.oexnr.cn/nnews/305416.htm
- http://m.3g.oexnr.cn/nnews/8640579.htm
- http://m.3g.oexnr.cn/nnews/73876.htm
- http://m.3g.oexnr.cn/nnews/781985.htm
- http://m.3g.oexnr.cn/nnews/0067293.htm
- http://m.3g.oexnr.cn/nnews/80596.htm
- http://m.3g.oexnr.cn/nnews/98477.htm
- http://m.3g.oexnr.cn/nnews/94843.htm
- http://m.3g.oexnr.cn/nnews/3593.htm
- http://m.3g.oexnr.cn/nnews/0262282.htm
- http://m.3g.oexnr.cn/nnews/2759317.htm
- http://m.3g.oexnr.cn/nnews/8549.htm
- http://m.3g.oexnr.cn/nnews/577526.htm
- http://m.3g.oexnr.cn/nnews/024653.htm
- http://m.3g.oexnr.cn/nnews/5403424.htm
- http://m.3g.oexnr.cn/nnews/715004.htm
- http://m.3g.oexnr.cn/nnews/7308721.htm
- http://m.3g.oexnr.cn/nnews/590574.htm
- http://m.3g.oexnr.cn/nnews/88300.htm
- http://m.3g.oexnr.cn/nnews/3685.htm
- http://m.3g.oexnr.cn/nnews/48370.htm
- http://m.3g.oexnr.cn/nnews/975567.htm
- http://m.3g.oexnr.cn/nnews/65099.htm
- http://m.3g.oexnr.cn/nnews/8598.htm
- http://m.3g.oexnr.cn/nnews/0275447.htm
- http://m.3g.oexnr.cn/nnews/2040255.htm
- http://m.3g.oexnr.cn/nnews/9754890.htm
- http://m.3g.oexnr.cn/nnews/9354.htm
- http://m.3g.oexnr.cn/nnews/77771.htm
- http://m.3g.oexnr.cn/nnews/1223695.htm
- http://m.3g.oexnr.cn/nnews/1364.htm
- http://m.3g.oexnr.cn/nnews/2041.htm
- http://m.3g.oexnr.cn/nnews/2964938.htm
- http://m.3g.oexnr.cn/nnews/5075446.htm
- http://m.3g.oexnr.cn/nnews/88959.htm
- http://m.3g.oexnr.cn/nnews/5319.htm
- http://m.3g.oexnr.cn/nnews/560328.htm
- http://m.3g.oexnr.cn/nnews/181262.htm
- http://m.3g.oexnr.cn/nnews/9572.htm
- http://m.3g.oexnr.cn/nnews/4035182.htm
- http://m.3g.oexnr.cn/nnews/89375.htm
- http://m.3g.oexnr.cn/nnews/342588.htm
- http://m.3g.oexnr.cn/nnews/4221004.htm
- http://m.3g.oexnr.cn/nnews/9193898.htm
- http://m.3g.oexnr.cn/nnews/23551.htm
- http://m.3g.oexnr.cn/nnews/8422754.htm
- http://m.3g.oexnr.cn/nnews/2643503.htm
- http://m.3g.oexnr.cn/nnews/4382.htm
- http://m.3g.oexnr.cn/nnews/5782498.htm
- http://m.3g.oexnr.cn/nnews/150263.htm
- http://m.3g.oexnr.cn/nnews/3061.htm
- http://m.3g.oexnr.cn/nnews/1804.htm
- http://m.3g.oexnr.cn/nnews/4230.htm
- http://m.3g.oexnr.cn/nnews/55731.htm
- http://m.3g.oexnr.cn/nnews/136471.htm
- http://m.3g.oexnr.cn/nnews/4906194.htm
- http://m.3g.oexnr.cn/nnews/7848.htm
- http://m.3g.oexnr.cn/nnews/3794.htm
- http://m.3g.oexnr.cn/nnews/5133.htm
- http://m.3g.oexnr.cn/nnews/05926.htm
- http://m.3g.oexnr.cn/nnews/8048217.htm
- http://m.3g.oexnr.cn/nnews/941451.htm
- http://m.3g.oexnr.cn/nnews/2101199.htm
- http://m.3g.oexnr.cn/nnews/0218.htm
- http://m.3g.oexnr.cn/nnews/1472162.htm
- http://m.3g.oexnr.cn/nnews/80496.htm
- http://m.3g.oexnr.cn/nnews/9434010.htm
- http://m.3g.oexnr.cn/nnews/9454.htm
- http://m.3g.oexnr.cn/nnews/8960913.htm
- http://m.3g.oexnr.cn/nnews/35092.htm
- http://m.3g.oexnr.cn/nnews/7227.htm
- http://m.3g.oexnr.cn/nnews/64503.htm
- http://m.3g.oexnr.cn/nnews/8403.htm
- http://m.3g.oexnr.cn/nnews/74920.htm
- http://m.3g.oexnr.cn/nnews/6160410.htm
- http://m.3g.oexnr.cn/nnews/9477711.htm
- http://m.3g.oexnr.cn/nnews/4827.htm

## 项目结构

```
newsdigest-index/
├── app/                           # 核心应用模块
│   ├── __init__.py               # 包初始化与工厂函数
│   ├── routes.py                 # HTTP 路由定义，包含查询与导入接口
│   ├── models.py                 # SQLAlchemy 数据模型，定义 Link 与 Tag 表
│   └── schemas.py                # Pydantic 请求与响应校验模型
├── core/                          # 核心业务逻辑层
│   ├── fetcher.py                # 异步抓取器，管理连接池与重试策略
│   ├── parser.py                 # 解析器，集成 beautifulsoup4 提取元数据
│   ├── deduplicator.py           # 去重引擎，基于内容哈希比对
│   └── health_checker.py         # 健康检查器，定期探测链接可达性
├── scripts/                       # 运维与辅助脚本
│   ├── init_db.py                # 初始化 SQLite 数据库表结构
│   ├── import_links.py           # 从 CSV/JSON 批量导入链接
│   └── export_stats.py           # 导出访问统计报表
├── tests/                         # 单元测试与集成测试
│   ├── test_fetcher.py           # 抓取器模拟测试
│   ├── test_parser.py            # 解析器覆盖率测试
│   └── conftest.py               # pytest 共用 fixtures
├── config/                        # 配置文件目录
│   ├── settings.py               # 全局配置加载，支持环境变量覆盖
│   └── logging.conf              # 日志格式与级别配置
├── static/                        # 静态资源（仅用于内置管理界面）
│   ├── css/                      # 基础样式表
│   └── js/                       # 前端交互脚本
├── .env.example                   # 环境变量示例文件
├── requirements.txt              # 生产环境依赖列表
├── requirements-dev.txt          # 开发环境额外依赖
├── Dockerfile                    # 容器化部署定义
├── docker-compose.yml            # 本地开发服务编排
└── README.md                     # 项目说明文档
```

## 贡献指南

1. 复刻仓库并在本地创建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。确保所有代码变更通过 pre-commit 钩子检查。

2. 编写或更新单元测试，确保新增代码的测试覆盖率达到 80% 以上。运行 `pytest tests/` 验证所有测试用例通过。

3. 更新文档对应章节，包括用户手册与 API 参考。若新增配置项，需同步更新 `.env.example` 文件。

4. 提交 Pull Request 时，在描述中清晰说明变更目的、影响范围与测试结果。维护者将在 48 小时内给出评审意见。

## 常见问题

**问：索引链接的内容是否会永久存储在本项目中？**

答：本项目仅存储链接的 URL、元数据与内容哈希，不存储完整的新闻正文。所有正文内容均通过实时抓取获取，抓取结果不会写入持久化存储，仅在内存中完成解析后即释放。

**问：如何更换为 PostgreSQL 或 MySQL 数据库？**

答：修改 `config/settings.py` 中的 `DATABASE_URL` 环境变量，使用对应的连接字符串即可。项目使用 SQLAlchemy ORM，支持主流关系型数据库。注意 PostgreSQL 需要安装 `psycopg2` 驱动，MySQL 需要安装 `pymysql`。

**问：定时抓取任务如何配置？**

答：项目本身不包含调度器，推荐结合系统 cron 或 Celery 周期性任务实现。`scripts/` 目录下提供了 `fetch_all.py` 脚本，可直接被外部调度程序调用。生产环境可参考 `docs/operations.md` 中的 systemd timer 配置示例。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
