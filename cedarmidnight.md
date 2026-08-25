# NewsLink Aggregator

NewsLink Aggregator 是一个面向移动端新闻资源整合与分发的高性能链接聚合系统，专门服务于需要从分散来源中快速采集、分类、检索新闻链接的技术团队与内容运营人员。该项目将来自多个渠道的新闻条目进行统一归集，提供结构化的链接索引、全文元数据提取、标签自动生成与批量导出能力，帮助用户在信息过载时代高效定位高价值新闻线索。NewsLink Aggregator 定位于新闻聚合中间件，不直接存储新闻正文，仅维护链接索引与基础元信息，适用于个人研究者、小型媒体团队、舆情监控系统前端以及大数据平台的新闻源接入层。

## 功能概览

批量链接导入 支持从文本文件、CSV、JSON Line 及常用订阅源格式中批量导入新闻链接，自动去重并校验 URL 有效性。

元数据智能提取 对每条新闻链接自动发起 HTTP 请求，解析目标页面标题、发布时间、正文摘要、作者与来源站点，提取结果以结构化 JSON 输出。

自定义标签引擎 基于规则引擎与轻量级关键词匹配，为每条链接自动生成分类标签，用户可自定义标签词库与权重规则，实现按主题、地域、情感倾向等多维度标记。

全文检索与过滤 内置基于倒排索引的检索模块，支持按标题、摘要、标签、时间范围、来源域名进行组合过滤，检索结果可排序并分页展示。

导出与订阅集成 支持将筛选后的链接列表导出为 CSV、RSS、JSON Feed 及 HTML 简报格式，同时提供 Webhook 回调机制，便于与第三方通知或内容管理系统对接。

状态监控与重试机制 对失效链接或超时请求自动记录状态并纳入重试队列，支持自定义重试次数与间隔策略，确保采集过程的容错性。

命令行与 API 双模式 提供功能完整的 CLI 工具用于日常运维与脚本集成，同时暴露 RESTful API 供前端或微服务调用，满足开发与生产环境的不同需求。

## 应用场景

舆情监控日报生成 运营人员每日早间通过命令行导入前一日产生的新闻链接列表，系统自动提取标题与来源后按预设标签分类，并导出为结构化 CSV 文件，直接用于日报数据透视分析，整体流程可在 5 分钟内完成。

垂直领域资讯聚合 科技、金融或医疗等垂直领域的自媒体团队可以将多个 RSS 订阅源导出的链接汇总后导入 NewsLink Aggregator，标签引擎根据自定义领域关键词进行细粒度归类，最终生成按细分方向分组的简报，供编辑团队选稿使用。

历史数据清洗与归档 研究人员在研究特定事件的时间线时，可从历史日志或第三方导出大量无序新闻链接，使用本系统的批量导入与元数据提取功能快速补齐每条链接的发布时间和摘要，随后按时间区间过滤导出用于后续统计建模。

轻量级新闻订阅中转服务 小型开发团队可利用 NewsLink Aggregator 的 API 将不同来源的新闻链接统一封装为内部 JSON Feed，再供给公司内网的门户系统或聊天机器人订阅模块，避免直接依赖多个外部接口。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整过程。

```bash
git clone https://github.com/example/newslink-aggregator.git
cd newslink-aggregator
npm install
cp .env.example .env
# 编辑 .env 文件配置数据库连接与监听端口
npm run build
npm start
```

执行完成后，可通过默认端口 3000 访问 API 文档，或使用 CLI 工具执行链接导入测试：

```bash
node dist/cli.js import --file ./samples/links.txt --tags demo
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用官方预编译二进制版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| PostgreSQL | 14.x 或更高 | 主数据库，用于存储链接索引、标签与元数据 |
| Redis | 7.x 或更高 | 缓存与任务队列后端，用于管理重试队列与限流 |
| PM2 | 5.x 或更高 | 生产环境进程守护工具，可选但推荐 |
| curl / wget | 最新稳定版 | 用于健康检查与脚本调用，仅运维场景需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | /docs/user-guide.md | 如何安装、配置、日常使用 CLI 与 API，以及常见操作流程 |
| 开发指南 | /docs/developer-guide.md | 项目目录结构说明、核心模块职责、如何添加新的标签规则或导出格式 |
| API 参考 | /docs/api-reference.md | 完整 RESTful 端点列表、请求参数、响应示例与错误码定义 |
| 运维手册 | /docs/operations-manual.md | 生产环境部署策略、日志管理、备份恢复、性能调优与监控指标 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/056241.htm
- http://m.wap.oexnr.cn/jnews/805553.htm
- http://m.wap.oexnr.cn/jnews/38256.htm
- http://m.wap.oexnr.cn/jnews/7807.htm
- http://m.wap.oexnr.cn/jnews/16867.htm
- http://m.wap.oexnr.cn/jnews/4666.htm
- http://m.wap.oexnr.cn/jnews/90464.htm
- http://m.wap.oexnr.cn/jnews/5731377.htm
- http://m.wap.oexnr.cn/jnews/0977.htm
- http://m.wap.oexnr.cn/jnews/4270.htm
- http://m.wap.oexnr.cn/jnews/5730.htm
- http://m.wap.oexnr.cn/jnews/820833.htm
- http://m.wap.oexnr.cn/jnews/120242.htm
- http://m.wap.oexnr.cn/jnews/048908.htm
- http://m.wap.oexnr.cn/jnews/6305986.htm
- http://m.wap.oexnr.cn/jnews/8892.htm
- http://m.wap.oexnr.cn/jnews/426107.htm
- http://m.wap.oexnr.cn/jnews/1969046.htm
- http://m.wap.oexnr.cn/jnews/0756429.htm
- http://m.wap.oexnr.cn/jnews/2458909.htm
- http://m.wap.oexnr.cn/jnews/729019.htm
- http://m.wap.oexnr.cn/jnews/4791398.htm
- http://m.wap.oexnr.cn/jnews/320115.htm
- http://m.wap.oexnr.cn/jnews/73781.htm
- http://m.wap.oexnr.cn/jnews/11663.htm
- http://m.wap.oexnr.cn/jnews/6579.htm
- http://m.wap.oexnr.cn/jnews/876718.htm
- http://m.wap.oexnr.cn/jnews/4987304.htm
- http://m.wap.oexnr.cn/jnews/84715.htm
- http://m.wap.oexnr.cn/jnews/6447.htm
- http://m.wap.oexnr.cn/jnews/5927.htm
- http://m.wap.oexnr.cn/jnews/32094.htm
- http://m.wap.oexnr.cn/jnews/603461.htm
- http://m.wap.oexnr.cn/jnews/89409.htm
- http://m.wap.oexnr.cn/jnews/727667.htm
- http://m.wap.oexnr.cn/jnews/7876080.htm
- http://m.wap.oexnr.cn/jnews/7052.htm
- http://m.wap.oexnr.cn/jnews/109013.htm
- http://m.wap.oexnr.cn/jnews/1211903.htm
- http://m.wap.oexnr.cn/jnews/865988.htm
- http://m.wap.oexnr.cn/jnews/30749.htm
- http://m.wap.oexnr.cn/jnews/8073558.htm
- http://m.wap.oexnr.cn/jnews/8138112.htm
- http://m.wap.oexnr.cn/jnews/9278636.htm
- http://m.wap.oexnr.cn/jnews/866702.htm
- http://m.wap.oexnr.cn/jnews/01178.htm
- http://m.wap.oexnr.cn/jnews/59605.htm
- http://m.wap.oexnr.cn/jnews/622170.htm
- http://m.wap.oexnr.cn/jnews/8248062.htm
- http://m.wap.oexnr.cn/jnews/975735.htm
- http://m.wap.oexnr.cn/jnews/8263911.htm
- http://m.wap.oexnr.cn/jnews/5898379.htm
- http://m.wap.oexnr.cn/jnews/2964678.htm
- http://m.wap.oexnr.cn/jnews/5370571.htm
- http://m.wap.oexnr.cn/jnews/18728.htm
- http://m.wap.oexnr.cn/jnews/242907.htm
- http://m.wap.oexnr.cn/jnews/771113.htm
- http://m.wap.oexnr.cn/jnews/77990.htm
- http://m.wap.oexnr.cn/jnews/11982.htm
- http://m.wap.oexnr.cn/jnews/8161.htm
- http://m.wap.oexnr.cn/jnews/70554.htm
- http://m.wap.oexnr.cn/jnews/4074546.htm
- http://m.wap.oexnr.cn/jnews/2395210.htm
- http://m.wap.oexnr.cn/jnews/3135.htm
- http://m.wap.oexnr.cn/jnews/2297402.htm
- http://m.wap.oexnr.cn/jnews/534334.htm
- http://m.wap.oexnr.cn/jnews/87490.htm
- http://m.wap.oexnr.cn/jnews/04556.htm
- http://m.wap.oexnr.cn/jnews/03423.htm
- http://m.wap.oexnr.cn/jnews/2292744.htm
- http://m.wap.oexnr.cn/jnews/408890.htm
- http://m.wap.oexnr.cn/jnews/9362.htm
- http://m.wap.oexnr.cn/jnews/735303.htm
- http://m.wap.oexnr.cn/jnews/800235.htm
- http://m.wap.oexnr.cn/jnews/2081894.htm
- http://m.wap.oexnr.cn/jnews/395190.htm
- http://m.wap.oexnr.cn/jnews/693366.htm
- http://m.wap.oexnr.cn/jnews/35920.htm
- http://m.wap.oexnr.cn/jnews/719745.htm
- http://m.wap.oexnr.cn/jnews/7559.htm
- http://m.wap.oexnr.cn/jnews/449916.htm
- http://m.wap.oexnr.cn/jnews/37985.htm
- http://m.wap.oexnr.cn/jnews/140380.htm
- http://m.wap.oexnr.cn/jnews/1578.htm
- http://m.wap.oexnr.cn/jnews/8577.htm
- http://m.wap.oexnr.cn/jnews/39925.htm
- http://m.wap.oexnr.cn/jnews/6228.htm
- http://m.wap.oexnr.cn/jnews/17483.htm
- http://m.wap.oexnr.cn/jnews/9447528.htm
- http://m.wap.oexnr.cn/jnews/5419.htm
- http://m.wap.oexnr.cn/jnews/1278.htm
- http://m.wap.oexnr.cn/jnews/5294432.htm
- http://m.wap.oexnr.cn/jnews/6986.htm
- http://m.wap.oexnr.cn/jnews/726931.htm
- http://m.wap.oexnr.cn/jnews/1662583.htm
- http://m.wap.oexnr.cn/jnews/97450.htm
- http://m.wap.oexnr.cn/jnews/2097.htm
- http://m.wap.oexnr.cn/jnews/2297.htm
- http://m.wap.oexnr.cn/jnews/7475470.htm
- http://m.wap.oexnr.cn/jnews/357506.htm
- http://m.wap.oexnr.cn/jnews/5158895.htm
- http://m.wap.oexnr.cn/jnews/8453.htm
- http://m.wap.oexnr.cn/jnews/4730.htm
- http://m.wap.oexnr.cn/jnews/606029.htm
- http://m.wap.oexnr.cn/jnews/870848.htm
- http://m.wap.oexnr.cn/jnews/7407709.htm
- http://m.wap.oexnr.cn/jnews/3881702.htm
- http://m.wap.oexnr.cn/jnews/10241.htm
- http://m.wap.oexnr.cn/jnews/0285.htm
- http://m.wap.oexnr.cn/jnews/2527536.htm
- http://m.wap.oexnr.cn/jnews/1348.htm
- http://m.wap.oexnr.cn/jnews/1750287.htm
- http://m.wap.oexnr.cn/jnews/6205.htm
- http://m.wap.oexnr.cn/jnews/79648.htm
- http://m.wap.oexnr.cn/jnews/296141.htm
- http://m.wap.oexnr.cn/jnews/673212.htm
- http://m.wap.oexnr.cn/jnews/685897.htm
- http://m.wap.oexnr.cn/jnews/780777.htm
- http://m.wap.oexnr.cn/jnews/6358.htm
- http://m.wap.oexnr.cn/jnews/0998400.htm
- http://m.wap.oexnr.cn/jnews/83768.htm
- http://m.wap.oexnr.cn/jnews/250465.htm
- http://m.wap.oexnr.cn/jnews/9433.htm
- http://m.wap.oexnr.cn/jnews/4048032.htm
- http://m.wap.oexnr.cn/jnews/211987.htm
- http://m.wap.oexnr.cn/jnews/40474.htm
- http://m.wap.oexnr.cn/jnews/266756.htm
- http://m.wap.oexnr.cn/jnews/11793.htm
- http://m.wap.oexnr.cn/jnews/9625.htm
- http://m.wap.oexnr.cn/jnews/23816.htm
- http://m.wap.oexnr.cn/jnews/19163.htm
- http://m.wap.oexnr.cn/jnews/11664.htm
- http://m.wap.oexnr.cn/jnews/9080.htm
- http://m.wap.oexnr.cn/jnews/4684280.htm
- http://m.wap.oexnr.cn/jnews/954078.htm
- http://m.wap.oexnr.cn/jnews/3199472.htm
- http://m.wap.oexnr.cn/jnews/2301.htm
- http://m.wap.oexnr.cn/jnews/0182763.htm
- http://m.wap.oexnr.cn/jnews/8009382.htm
- http://m.wap.oexnr.cn/jnews/5205791.htm
- http://m.wap.oexnr.cn/jnews/330040.htm
- http://m.wap.oexnr.cn/jnews/6262.htm
- http://m.wap.oexnr.cn/jnews/922001.htm
- http://m.wap.oexnr.cn/jnews/98578.htm
- http://m.wap.oexnr.cn/jnews/8347.htm
- http://m.wap.oexnr.cn/jnews/9313031.htm
- http://m.wap.oexnr.cn/jnews/3344.htm
- http://m.wap.oexnr.cn/jnews/72887.htm
- http://m.wap.oexnr.cn/jnews/31937.htm
- http://m.wap.oexnr.cn/jnews/8003.htm
- http://m.wap.oexnr.cn/jnews/4727461.htm
- http://m.wap.oexnr.cn/jnews/37687.htm
- http://m.wap.oexnr.cn/jnews/63087.htm
- http://m.wap.oexnr.cn/jnews/5622654.htm
- http://m.wap.oexnr.cn/jnews/219115.htm
- http://m.wap.oexnr.cn/jnews/247520.htm
- http://m.wap.oexnr.cn/jnews/0510.htm
- http://m.wap.oexnr.cn/jnews/4719354.htm
- http://m.wap.oexnr.cn/jnews/3059.htm
- http://m.wap.oexnr.cn/jnews/2165.htm
- http://m.wap.oexnr.cn/jnews/9309351.htm
- http://m.wap.oexnr.cn/jnews/75716.htm
- http://m.wap.oexnr.cn/jnews/6149334.htm
- http://m.wap.oexnr.cn/jnews/751888.htm
- http://m.wap.oexnr.cn/jnews/3028.htm
- http://m.wap.oexnr.cn/jnews/7105157.htm
- http://m.wap.oexnr.cn/jnews/16884.htm
- http://m.wap.oexnr.cn/jnews/736916.htm
- http://m.wap.oexnr.cn/jnews/032728.htm
- http://m.wap.oexnr.cn/jnews/780472.htm
- http://m.wap.oexnr.cn/jnews/11163.htm
- http://m.wap.oexnr.cn/jnews/983599.htm
- http://m.wap.oexnr.cn/jnews/652350.htm
- http://m.wap.oexnr.cn/jnews/89193.htm
- http://m.wap.oexnr.cn/jnews/93629.htm
- http://m.wap.oexnr.cn/jnews/006876.htm
- http://m.wap.oexnr.cn/jnews/82133.htm
- http://m.wap.oexnr.cn/jnews/6851507.htm
- http://m.wap.oexnr.cn/jnews/7208754.htm
- http://m.wap.oexnr.cn/jnews/98298.htm
- http://m.wap.oexnr.cn/jnews/006986.htm
- http://m.wap.oexnr.cn/jnews/813809.htm
- http://m.wap.oexnr.cn/jnews/57004.htm
- http://m.wap.oexnr.cn/jnews/74390.htm
- http://m.wap.oexnr.cn/jnews/952722.htm
- http://m.wap.oexnr.cn/jnews/0047.htm
- http://m.wap.oexnr.cn/jnews/5134548.htm
- http://m.wap.oexnr.cn/jnews/98856.htm
- http://m.wap.oexnr.cn/jnews/6438.htm
- http://m.wap.oexnr.cn/jnews/6884183.htm
- http://m.wap.oexnr.cn/jnews/138206.htm
- http://m.wap.oexnr.cn/jnews/478560.htm
- http://m.wap.oexnr.cn/jnews/93953.htm
- http://m.wap.oexnr.cn/jnews/020462.htm
- http://m.wap.oexnr.cn/jnews/5675.htm
- http://m.wap.oexnr.cn/jnews/18270.htm
- http://m.wap.oexnr.cn/jnews/93294.htm
- http://m.wap.oexnr.cn/jnews/8975.htm
- http://m.wap.oexnr.cn/jnews/521553.htm
- http://m.wap.oexnr.cn/jnews/32782.htm
- http://m.wap.oexnr.cn/jnews/32168.htm
- http://m.wap.oexnr.cn/jnews/19508.htm
- http://m.wap.oexnr.cn/jnews/1800.htm
- http://m.wap.oexnr.cn/jnews/24894.htm
- http://m.wap.oexnr.cn/jnews/8274.htm
- http://m.wap.oexnr.cn/jnews/0356.htm
- http://m.wap.oexnr.cn/jnews/61402.htm
- http://m.wap.oexnr.cn/jnews/569937.htm
- http://m.wap.oexnr.cn/jnews/047023.htm
- http://m.wap.oexnr.cn/jnews/674499.htm
- http://m.wap.oexnr.cn/jnews/6990.htm
- http://m.wap.oexnr.cn/jnews/862362.htm
- http://m.wap.oexnr.cn/jnews/52902.htm
- http://m.wap.oexnr.cn/jnews/103391.htm
- http://m.wap.oexnr.cn/jnews/9673.htm
- http://m.wap.oexnr.cn/jnews/6990565.htm
- http://m.wap.oexnr.cn/jnews/02724.htm
- http://m.wap.oexnr.cn/jnews/99145.htm
- http://m.wap.oexnr.cn/jnews/40251.htm
- http://m.wap.oexnr.cn/jnews/3081.htm
- http://m.wap.oexnr.cn/jnews/9049735.htm
- http://m.wap.oexnr.cn/jnews/4583570.htm
- http://m.wap.oexnr.cn/jnews/6888979.htm
- http://m.wap.oexnr.cn/jnews/086192.htm
- http://m.wap.oexnr.cn/jnews/9519.htm
- http://m.wap.oexnr.cn/jnews/373982.htm
- http://m.wap.oexnr.cn/jnews/6421843.htm
- http://m.wap.oexnr.cn/jnews/7536.htm
- http://m.wap.oexnr.cn/jnews/474872.htm
- http://m.wap.oexnr.cn/jnews/601563.htm
- http://m.wap.oexnr.cn/jnews/7244980.htm
- http://m.wap.oexnr.cn/jnews/9539.htm
- http://m.wap.oexnr.cn/jnews/3318411.htm
- http://m.wap.oexnr.cn/jnews/9990.htm
- http://m.wap.oexnr.cn/jnews/586534.htm
- http://m.wap.oexnr.cn/jnews/052998.htm
- http://m.wap.oexnr.cn/jnews/17087.htm
- http://m.wap.oexnr.cn/jnews/9927.htm
- http://m.wap.oexnr.cn/jnews/986343.htm
- http://m.wap.oexnr.cn/jnews/6432.htm
- http://m.wap.oexnr.cn/jnews/1139250.htm
- http://m.wap.oexnr.cn/jnews/377715.htm
- http://m.wap.oexnr.cn/jnews/0598228.htm
- http://m.wap.oexnr.cn/jnews/8483.htm
- http://m.wap.oexnr.cn/jnews/89307.htm
- http://m.wap.oexnr.cn/jnews/96511.htm
- http://m.wap.oexnr.cn/jnews/429135.htm
- http://m.wap.oexnr.cn/jnews/80997.htm
- http://m.wap.oexnr.cn/jnews/13720.htm
- http://m.wap.oexnr.cn/jnews/59467.htm
- http://m.wap.oexnr.cn/jnews/8722.htm
- http://m.wap.oexnr.cn/jnews/691747.htm
- http://m.wap.oexnr.cn/jnews/4707.htm
- http://m.wap.oexnr.cn/jnews/410338.htm
- http://m.wap.oexnr.cn/jnews/3496268.htm
- http://m.wap.oexnr.cn/jnews/717090.htm
- http://m.wap.oexnr.cn/jnews/8000463.htm
- http://m.wap.oexnr.cn/jnews/2156620.htm
- http://m.wap.oexnr.cn/jnews/859098.htm
- http://m.wap.oexnr.cn/jnews/1601973.htm
- http://m.wap.oexnr.cn/jnews/6721423.htm
- http://m.wap.oexnr.cn/jnews/7654.htm
- http://m.wap.oexnr.cn/jnews/9247545.htm
- http://m.wap.oexnr.cn/jnews/6976.htm
- http://m.wap.oexnr.cn/jnews/349752.htm
- http://m.wap.oexnr.cn/jnews/33466.htm
- http://m.wap.oexnr.cn/jnews/85090.htm
- http://m.wap.oexnr.cn/jnews/64068.htm
- http://m.wap.oexnr.cn/jnews/1219416.htm
- http://m.wap.oexnr.cn/jnews/2496238.htm
- http://m.wap.oexnr.cn/jnews/52647.htm
- http://m.wap.oexnr.cn/jnews/508083.htm
- http://m.wap.oexnr.cn/jnews/5866.htm
- http://m.wap.oexnr.cn/jnews/84673.htm
- http://m.wap.oexnr.cn/jnews/1986893.htm
- http://m.wap.oexnr.cn/jnews/28725.htm
- http://m.wap.oexnr.cn/jnews/8629.htm
- http://m.wap.oexnr.cn/jnews/0174922.htm
- http://m.wap.oexnr.cn/jnews/367941.htm
- http://m.wap.oexnr.cn/jnews/4413668.htm
- http://m.wap.oexnr.cn/jnews/0462448.htm
- http://m.wap.oexnr.cn/jnews/6281.htm
- http://m.wap.oexnr.cn/jnews/7612423.htm
- http://m.wap.oexnr.cn/jnews/855191.htm
- http://m.wap.oexnr.cn/jnews/3369006.htm
- http://m.wap.oexnr.cn/jnews/8911702.htm
- http://m.wap.oexnr.cn/jnews/089473.htm
- http://m.wap.oexnr.cn/jnews/583163.htm
- http://m.wap.oexnr.cn/jnews/1037603.htm
- http://m.wap.oexnr.cn/jnews/5690608.htm
- http://m.wap.oexnr.cn/jnews/1551.htm
- http://m.wap.oexnr.cn/jnews/92542.htm
- http://m.wap.oexnr.cn/jnews/7286626.htm
- http://m.wap.oexnr.cn/jnews/258670.htm
- http://m.wap.oexnr.cn/jnews/1443.htm
- http://m.wap.oexnr.cn/jnews/4593537.htm
- http://m.wap.oexnr.cn/jnews/98082.htm
- http://m.wap.oexnr.cn/jnews/1123943.htm
- http://m.wap.oexnr.cn/jnews/6257.htm
- http://m.wap.oexnr.cn/jnews/8797.htm

## 项目结构

```
newslink-aggregator/
├── src/
│   ├── core/                      # 核心调度与生命周期管理
│   │   ├── index.ts               # 主入口，初始化各模块并启动服务
│   │   └── lifecycle.ts           # 启动、停止、重载流程控制
│   ├── collector/                 # 链接采集与HTTP请求模块
│   │   ├── fetcher.ts             # 基于axios的页面请求与超时控制
│   │   ├── parser.ts              # HTML元数据解析与摘要提取
│   │   └── queue.ts               # 基于Redis的请求队列与重试逻辑
│   ├── storage/                   # 数据持久化层
│   │   ├── postgres.ts            # PostgreSQL连接池与CRUD操作
│   │   ├── redis.ts               # Redis客户端与缓存策略
│   │   └── migrations/            # 数据库迁移脚本（按版本排序）
│   ├── indexer/                   # 倒排索引与检索引擎
│   │   ├── inverted-index.ts      # 索引构建与更新
│   │   └── search.ts              # 查询解析、排序与分页
│   ├── tagging/                   # 标签规则引擎
│   │   ├── rule-engine.ts         # 基于关键词与正则的规则匹配
│   │   └── dictionary.ts          # 可热更新的标签词库
│   ├── api/                       # RESTful API 路由与控制器
│   │   ├── routes/                # 按资源划分的路由定义（links, tags, export）
│   │   └── middleware/            # 鉴权、限流、日志中间件
│   ├── cli/                       # 命令行工具实现
│   │   ├── commands/              # 各子命令（import, export, status, retry）
│   │   └── runner.ts              # CLI命令解析与分发
│   └── types/                     # TypeScript类型声明与接口定义
├── config/                        # 配置文件目录
│   ├── default.json               # 默认配置（端口、超时、并发数）
│   ├── production.json            # 生产环境覆盖配置
│   └── custom-rules.json          # 用户自定义标签规则示例
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 各模块独立测试用例
│   └── integration/               # API与数据库端到端测试
├── docs/                          # 完整文档（用户指南、开发指南、API参考、运维手册）
├── scripts/                       # 辅助脚本（数据迁移、性能测试、示例数据生成）
├── .env.example                   # 环境变量模板
├── package.json                   # npm 依赖与脚本定义
├── tsconfig.json                  # TypeScript 编译配置
├── docker-compose.yml             # 本地开发环境（PostgreSQL + Redis）
└── README.md                      # 本文件
```

## 贡献指南

提交 Issue 与功能请求 在提交新 Issue 前，请先检索已有议题避免重复。Bug 报告需包含完整环境信息、可复现的最小步骤及预期与实际行为对比；功能请求请说明使用场景与期望接口设计。

代码风格与测试 所有提交的代码必须通过 ESLint 与 Prettier 检查，并为新增或修改的功能编写对应的单元测试或集成测试。测试覆盖率不得低于 85%。

拉取请求流程 从 main 分支创建特性分支，完成开发后发起 Pull Request，并在 PR 描述中关联相关 Issue。至少需要一位项目维护者审核通过后方可合并。提交信息请遵循 Conventional Commits 规范。

文档更新 任何影响用户使用行为或部署方式的变更，必须同步更新 docs 目录下对应的文档，并在 PR 中说明文档改动点。API 变更需同步更新 API 参考文档中的示例。

本地开发环境 使用 docker-compose up -d 启动本地数据库与缓存服务，运行 npm run dev 进入热重载开发模式。所有新增依赖需在 package.json 中明确版本并提交锁文件。

## 常见问题

系统对单次导入的链接数量有何限制？
单次导入没有硬性数量上限，实际受可用内存与数据库连接超时时间影响。默认 CLI 导入采用批量提交策略，每 500 条执行一次事务提交。若单次导入超过 50000 条，建议使用 --batch-size 参数调整批次大小，或通过 API 分片上传。

元数据提取失败时如何排查？
首先检查目标站点是否可访问及 robots.txt 是否允许抓取。系统返回的元数据对象中包含 status 字段，若为 failed 则同时提供 error 原因摘要。可通过 CLI 的 retry 命令对失败条目重新发起请求，或调整 .env 中的 FETCH_TIMEOUT 与 USER_AGENT 值。

如何将系统部署到生产环境？
推荐使用 PM2 管理进程，结合 Nginx 反向代理提供 TLS 终止。数据库与缓存需单独部署高可用集群。参考 docs/operations-manual.md 中的 checklist 完成环境变量配置、日志轮转、监控告警与定期备份策略。对于日均处理超过 10 万条链接的场景，建议增加 Worker 数量并调高 Redis 最大内存。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
