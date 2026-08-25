# NewsLink Archive Indexer

NewsLink Archive Indexer 是一个面向技术内容聚合与持久化存档的轻量级索引工具。该项目定位于帮助开发者、研究人员与内容管理者对分散在多个数据源中的新闻型 HTML 资源进行统一采集、元数据提取与结构化索引。目标用户包括需要构建自定义新闻监控系统的运维工程师、从事信息检索研究的学术人员以及希望将外部新闻数据集成至内部知识库的软件团队。NewsLink Archive Indexer 解决的核心问题在于：当大量新闻条目仅以原始 HTML 文件形式存在于不同路径或子域名下时，如何通过一个可编程的索引层实现批量扫描、状态校验、标题抽取与链接归档，从而避免手工整理的低效与遗漏。

## 功能概览

批量资源扫描 通过递归遍历指定目录或 URL 前缀列表，自动发现符合 `.htm` 后缀的新闻文件，并生成待索引队列。

元数据智能抽取 从 HTML 文档中自动提取发布日期、内容摘要、关键词及正文段落，支持多字符集自动检测与纠错。

增量索引更新 基于文件修改时间与内容哈希值，仅对新增或变更的文档执行重新索引，显著降低重复计算开销。

多格式索引导出 支持将索引结果输出为 JSON Lines、CSV 或 SQLite 数据库文件，便于下游数据分析工具直接使用。

校验与报告生成 对每个链接执行可达性检测与响应时间记录，生成包含失效链接、重定向链与异常状态的完整性报告。

查询过滤器 内置基于正则表达式的时间范围、来源域名与标题关键词过滤，支持快速筛选特定批次或主题的资源。

插件化处理器 提供标准处理器接口，允许用户针对特定新闻源编写自定义解析规则，以适配非标准 HTML 结构。

任务编排支持 通过配置文件定义扫描计划、通知规则与输出目的地，可与 cron 或 systemd timer 集成实现全自动索引流水线。

## 应用场景

内部知识库的新闻素材采集 企业技术文档团队可使用 NewsLink Archive Indexer 定期扫描指定路径下的新闻存档，抽取标题与发布时间，生成可供内部搜索系统使用的结构化元数据，减少人工录入工作量。

学术研究中的网页数据集构建 社会科学或计算传播学研究人员可借助该工具对大量新闻 HTML 文件进行批量特征提取，输出 CSV 格式的数据集，用于后续的内容分析、话题建模或趋势预测。

运维监控系统的链接健康检查 运维人员可将 NewsLink Archive Indexer 配置为定时任务，对所有记录的新闻链接执行可用性探测，自动生成失效链接清单，便于及时修复或移除不可访问的资源。

历史新闻归档项目的迁移辅助 在将旧版新闻系统迁移至新平台时，该工具可对存量 HTML 文件进行全量扫描与索引导出，为数据迁移提供清晰的资源清单与结构映射参考。

## 快速开始

```bash
git clone https://github.com/example/newslink-archive-indexer.git
cd newslink-archive-indexer
pip install -r requirements.txt
python indexer.py --source /var/news/archive --output index.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，用于执行索引器及所有处理器 |
| lxml | 4.9.0 及以上 | HTML 解析引擎，提供高性能的 DOM 树遍历与 XPath 支持 |
| requests | 2.28.0 及以上 | 用于远程链接可达性检测与 HTTP 状态码获取 |
| charset-normalizer | 3.0.0 及以上 | 自动检测并转换非 UTF-8 编码的 HTML 文档内容 |
| cryptography | 39.0.0 及以上 | 用于生成资源哈希值及可选的索引签名验证 |
| pytest | 7.2.0 及以上 | 仅开发环境必需，用于运行单元测试与集成测试套件 |
| sqlite3 | 系统内置 | 用于本地索引缓存与增量更新记录存储 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置首次扫描任务并生成第一份索引报告 |
| 配置参考 | docs/configuration.md | 所有可用的命令行参数、配置文件字段及其默认值说明 |
| 处理器开发 | docs/processor-api.md | 如何编写自定义处理器以适配新的新闻源或 HTML 结构变体 |
| 常见工作流 | docs/workflows.md | 涵盖定时索引、差异备份与异常告警等典型运维场景的详细操作步骤 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/9135.htm
- http://m.3g.ghtkgg.cn/nnews/7830.htm
- http://m.3g.ghtkgg.cn/nnews/663162.htm
- http://m.3g.ghtkgg.cn/nnews/313317.htm
- http://m.3g.ghtkgg.cn/nnews/36784.htm
- http://m.3g.ghtkgg.cn/nnews/84968.htm
- http://m.3g.ghtkgg.cn/nnews/4500765.htm
- http://m.3g.ghtkgg.cn/nnews/69491.htm
- http://m.3g.ghtkgg.cn/nnews/30888.htm
- http://m.3g.ghtkgg.cn/nnews/1026.htm
- http://m.3g.ghtkgg.cn/nnews/906015.htm
- http://m.3g.ghtkgg.cn/nnews/91183.htm
- http://m.3g.ghtkgg.cn/nnews/4340656.htm
- http://m.3g.ghtkgg.cn/nnews/78189.htm
- http://m.3g.ghtkgg.cn/nnews/4792064.htm
- http://m.3g.ghtkgg.cn/nnews/21765.htm
- http://m.3g.ghtkgg.cn/nnews/8808457.htm
- http://m.3g.ghtkgg.cn/nnews/52873.htm
- http://m.3g.ghtkgg.cn/nnews/0330.htm
- http://m.3g.ghtkgg.cn/nnews/1402844.htm
- http://m.3g.ghtkgg.cn/nnews/6906.htm
- http://m.3g.ghtkgg.cn/nnews/13787.htm
- http://m.3g.ghtkgg.cn/nnews/3185.htm
- http://m.3g.ghtkgg.cn/nnews/3500204.htm
- http://m.3g.ghtkgg.cn/nnews/547979.htm
- http://m.3g.ghtkgg.cn/nnews/72901.htm
- http://m.3g.ghtkgg.cn/nnews/397775.htm
- http://m.3g.ghtkgg.cn/nnews/8865.htm
- http://m.3g.ghtkgg.cn/nnews/99109.htm
- http://m.3g.ghtkgg.cn/nnews/1245001.htm
- http://m.3g.ghtkgg.cn/nnews/981422.htm
- http://m.3g.ghtkgg.cn/nnews/6791134.htm
- http://m.3g.ghtkgg.cn/nnews/159676.htm
- http://m.3g.ghtkgg.cn/nnews/26517.htm
- http://m.3g.ghtkgg.cn/nnews/6988802.htm
- http://m.3g.ghtkgg.cn/nnews/9437713.htm
- http://m.3g.ghtkgg.cn/nnews/33135.htm
- http://m.3g.ghtkgg.cn/nnews/626138.htm
- http://m.3g.ghtkgg.cn/nnews/1758985.htm
- http://m.3g.ghtkgg.cn/nnews/0214743.htm
- http://m.3g.ghtkgg.cn/nnews/847097.htm
- http://m.3g.ghtkgg.cn/nnews/860873.htm
- http://m.3g.ghtkgg.cn/nnews/5953.htm
- http://m.3g.ghtkgg.cn/nnews/928865.htm
- http://m.3g.ghtkgg.cn/nnews/7368.htm
- http://m.3g.ghtkgg.cn/nnews/3306497.htm
- http://m.3g.ghtkgg.cn/nnews/10448.htm
- http://m.3g.ghtkgg.cn/nnews/549476.htm
- http://m.3g.ghtkgg.cn/nnews/6639.htm
- http://m.3g.ghtkgg.cn/nnews/283789.htm
- http://m.3g.ghtkgg.cn/nnews/300376.htm
- http://m.3g.ghtkgg.cn/nnews/452549.htm
- http://m.3g.ghtkgg.cn/nnews/935693.htm
- http://m.3g.ghtkgg.cn/nnews/82805.htm
- http://m.3g.ghtkgg.cn/nnews/580790.htm
- http://m.3g.ghtkgg.cn/nnews/7446499.htm
- http://m.3g.ghtkgg.cn/nnews/4481390.htm
- http://m.3g.ghtkgg.cn/nnews/0043603.htm
- http://m.3g.ghtkgg.cn/nnews/5863386.htm
- http://m.3g.ghtkgg.cn/nnews/5071.htm
- http://m.3g.ghtkgg.cn/nnews/769464.htm
- http://m.3g.ghtkgg.cn/nnews/31385.htm
- http://m.3g.ghtkgg.cn/nnews/3078871.htm
- http://m.3g.ghtkgg.cn/nnews/7355005.htm
- http://m.3g.ghtkgg.cn/nnews/9269880.htm
- http://m.3g.ghtkgg.cn/nnews/91385.htm
- http://m.3g.ghtkgg.cn/nnews/13613.htm
- http://m.3g.ghtkgg.cn/nnews/0962.htm
- http://m.3g.ghtkgg.cn/nnews/9570.htm
- http://m.3g.ghtkgg.cn/nnews/7371.htm
- http://m.3g.ghtkgg.cn/nnews/9252.htm
- http://m.3g.ghtkgg.cn/nnews/9315.htm
- http://m.3g.ghtkgg.cn/nnews/8832366.htm
- http://m.3g.ghtkgg.cn/nnews/096109.htm
- http://m.3g.ghtkgg.cn/nnews/9309.htm
- http://m.3g.ghtkgg.cn/nnews/1336.htm
- http://m.3g.ghtkgg.cn/nnews/757622.htm
- http://m.3g.ghtkgg.cn/nnews/240920.htm
- http://m.3g.ghtkgg.cn/nnews/87567.htm
- http://m.3g.ghtkgg.cn/nnews/2255933.htm
- http://m.3g.ghtkgg.cn/nnews/7371182.htm
- http://m.3g.ghtkgg.cn/nnews/1684371.htm
- http://m.3g.ghtkgg.cn/nnews/15463.htm
- http://m.3g.ghtkgg.cn/nnews/13739.htm
- http://m.3g.ghtkgg.cn/nnews/08429.htm
- http://m.3g.ghtkgg.cn/nnews/9776.htm
- http://m.3g.ghtkgg.cn/nnews/44930.htm
- http://m.3g.ghtkgg.cn/nnews/866137.htm
- http://m.3g.ghtkgg.cn/nnews/8234286.htm
- http://m.3g.ghtkgg.cn/nnews/561965.htm
- http://m.3g.ghtkgg.cn/nnews/6939.htm
- http://m.3g.ghtkgg.cn/nnews/95444.htm
- http://m.3g.ghtkgg.cn/nnews/43373.htm
- http://m.3g.ghtkgg.cn/nnews/8277852.htm
- http://m.3g.ghtkgg.cn/nnews/06696.htm
- http://m.3g.ghtkgg.cn/nnews/5129510.htm
- http://m.3g.ghtkgg.cn/nnews/2569618.htm
- http://m.3g.ghtkgg.cn/nnews/1981979.htm
- http://m.3g.ghtkgg.cn/nnews/90141.htm
- http://m.3g.ghtkgg.cn/nnews/64882.htm
- http://m.3g.ghtkgg.cn/nnews/6380976.htm
- http://m.3g.ghtkgg.cn/nnews/92417.htm
- http://m.3g.ghtkgg.cn/nnews/15259.htm
- http://m.3g.ghtkgg.cn/nnews/2920.htm
- http://m.3g.ghtkgg.cn/nnews/745002.htm
- http://m.3g.ghtkgg.cn/nnews/1084.htm
- http://m.3g.ghtkgg.cn/nnews/16586.htm
- http://m.3g.ghtkgg.cn/nnews/862290.htm
- http://m.3g.ghtkgg.cn/nnews/03718.htm
- http://m.3g.ghtkgg.cn/nnews/07070.htm
- http://m.3g.ghtkgg.cn/nnews/85010.htm
- http://m.3g.ghtkgg.cn/nnews/28753.htm
- http://m.3g.ghtkgg.cn/nnews/262352.htm
- http://m.3g.ghtkgg.cn/nnews/3554786.htm
- http://m.3g.ghtkgg.cn/nnews/635060.htm
- http://m.3g.ghtkgg.cn/nnews/6352452.htm
- http://m.3g.ghtkgg.cn/nnews/59097.htm
- http://m.3g.ghtkgg.cn/nnews/62370.htm
- http://m.3g.ghtkgg.cn/nnews/9831.htm
- http://m.3g.ghtkgg.cn/nnews/006512.htm
- http://m.3g.ghtkgg.cn/nnews/971999.htm
- http://m.3g.ghtkgg.cn/nnews/13557.htm
- http://m.3g.ghtkgg.cn/nnews/1359.htm
- http://m.3g.ghtkgg.cn/nnews/85053.htm
- http://m.3g.ghtkgg.cn/nnews/2528571.htm
- http://m.3g.ghtkgg.cn/nnews/412835.htm
- http://m.3g.ghtkgg.cn/nnews/4655750.htm
- http://m.3g.ghtkgg.cn/nnews/3988.htm
- http://m.3g.ghtkgg.cn/nnews/05600.htm
- http://m.3g.ghtkgg.cn/nnews/108566.htm
- http://m.3g.ghtkgg.cn/nnews/4122712.htm
- http://m.3g.ghtkgg.cn/nnews/3690718.htm
- http://m.3g.ghtkgg.cn/nnews/6799.htm
- http://m.3g.ghtkgg.cn/nnews/4638739.htm
- http://m.3g.ghtkgg.cn/nnews/364953.htm
- http://m.3g.ghtkgg.cn/nnews/2082354.htm
- http://m.3g.ghtkgg.cn/nnews/14976.htm
- http://m.3g.ghtkgg.cn/nnews/43475.htm
- http://m.3g.ghtkgg.cn/nnews/6302630.htm
- http://m.3g.ghtkgg.cn/nnews/6306992.htm
- http://m.3g.ghtkgg.cn/nnews/630912.htm
- http://m.3g.ghtkgg.cn/nnews/3235.htm
- http://m.3g.ghtkgg.cn/nnews/7231220.htm
- http://m.3g.ghtkgg.cn/nnews/16731.htm
- http://m.3g.ghtkgg.cn/nnews/182476.htm
- http://m.3g.ghtkgg.cn/nnews/790041.htm
- http://m.3g.ghtkgg.cn/nnews/8605850.htm
- http://m.3g.ghtkgg.cn/nnews/8147.htm
- http://m.3g.ghtkgg.cn/nnews/2455639.htm
- http://m.3g.ghtkgg.cn/nnews/23417.htm
- http://m.3g.ghtkgg.cn/nnews/8405912.htm
- http://m.3g.ghtkgg.cn/nnews/73996.htm
- http://m.3g.ghtkgg.cn/nnews/5337.htm
- http://m.3g.ghtkgg.cn/nnews/91517.htm
- http://m.3g.ghtkgg.cn/nnews/15580.htm
- http://m.3g.ghtkgg.cn/nnews/663488.htm
- http://m.3g.ghtkgg.cn/nnews/50916.htm
- http://m.3g.ghtkgg.cn/nnews/7434768.htm
- http://m.3g.ghtkgg.cn/nnews/4844.htm
- http://m.3g.ghtkgg.cn/nnews/8340723.htm
- http://m.3g.ghtkgg.cn/nnews/078450.htm
- http://m.3g.ghtkgg.cn/nnews/6117262.htm
- http://m.3g.ghtkgg.cn/nnews/23428.htm
- http://m.3g.ghtkgg.cn/nnews/8262.htm
- http://m.3g.ghtkgg.cn/nnews/44975.htm
- http://m.3g.ghtkgg.cn/nnews/045187.htm
- http://m.3g.ghtkgg.cn/nnews/049102.htm
- http://m.3g.ghtkgg.cn/nnews/599150.htm
- http://m.3g.ghtkgg.cn/nnews/83130.htm
- http://m.3g.ghtkgg.cn/nnews/4336684.htm
- http://m.3g.ghtkgg.cn/nnews/9132.htm
- http://m.3g.ghtkgg.cn/nnews/9876.htm
- http://m.3g.ghtkgg.cn/nnews/65527.htm
- http://m.3g.ghtkgg.cn/nnews/8997.htm
- http://m.3g.ghtkgg.cn/nnews/93206.htm
- http://m.3g.ghtkgg.cn/nnews/159169.htm
- http://m.3g.ghtkgg.cn/nnews/702013.htm
- http://m.3g.ghtkgg.cn/nnews/8753.htm
- http://m.3g.ghtkgg.cn/nnews/2326.htm
- http://m.3g.ghtkgg.cn/nnews/4068834.htm
- http://m.3g.ghtkgg.cn/nnews/01385.htm
- http://m.3g.ghtkgg.cn/nnews/5081428.htm
- http://m.3g.ghtkgg.cn/nnews/3274.htm
- http://m.3g.ghtkgg.cn/nnews/68530.htm
- http://m.3g.ghtkgg.cn/nnews/0568635.htm
- http://m.3g.ghtkgg.cn/nnews/2953.htm
- http://m.3g.ghtkgg.cn/nnews/0797800.htm
- http://m.3g.ghtkgg.cn/nnews/154874.htm
- http://m.3g.ghtkgg.cn/nnews/9755.htm
- http://m.3g.ghtkgg.cn/nnews/2779.htm
- http://m.3g.ghtkgg.cn/nnews/635702.htm
- http://m.3g.ghtkgg.cn/nnews/636903.htm
- http://m.3g.ghtkgg.cn/nnews/7590944.htm
- http://m.3g.ghtkgg.cn/nnews/04741.htm
- http://m.3g.ghtkgg.cn/nnews/2152859.htm
- http://m.3g.ghtkgg.cn/nnews/414390.htm
- http://m.3g.ghtkgg.cn/nnews/564172.htm
- http://m.3g.ghtkgg.cn/nnews/8253.htm
- http://m.3g.ghtkgg.cn/nnews/94626.htm
- http://m.3g.ghtkgg.cn/nnews/1176.htm
- http://m.3g.ghtkgg.cn/nnews/0021.htm
- http://m.3g.ghtkgg.cn/nnews/407551.htm
- http://m.3g.ghtkgg.cn/nnews/3092.htm
- http://m.3g.ghtkgg.cn/nnews/4961.htm
- http://m.3g.ghtkgg.cn/nnews/0119030.htm
- http://m.3g.ghtkgg.cn/nnews/1065834.htm
- http://m.3g.ghtkgg.cn/nnews/191520.htm
- http://m.3g.ghtkgg.cn/nnews/4319721.htm
- http://m.3g.ghtkgg.cn/nnews/82663.htm
- http://m.3g.ghtkgg.cn/nnews/5623.htm
- http://m.3g.ghtkgg.cn/nnews/0553411.htm
- http://m.3g.ghtkgg.cn/nnews/2484.htm
- http://m.3g.ghtkgg.cn/nnews/029821.htm
- http://m.3g.ghtkgg.cn/nnews/7816.htm
- http://m.3g.ghtkgg.cn/nnews/22142.htm
- http://m.3g.ghtkgg.cn/nnews/794778.htm
- http://m.3g.ghtkgg.cn/nnews/2756768.htm
- http://m.3g.ghtkgg.cn/nnews/190350.htm
- http://m.3g.ghtkgg.cn/nnews/7619569.htm
- http://m.3g.ghtkgg.cn/nnews/29168.htm
- http://m.3g.ghtkgg.cn/nnews/3257.htm
- http://m.3g.ghtkgg.cn/nnews/99343.htm
- http://m.3g.ghtkgg.cn/nnews/5804.htm
- http://m.3g.ghtkgg.cn/nnews/6105.htm
- http://m.3g.ghtkgg.cn/nnews/7279885.htm
- http://m.3g.ghtkgg.cn/nnews/8463318.htm
- http://m.3g.ghtkgg.cn/nnews/7485.htm
- http://m.3g.ghtkgg.cn/nnews/799316.htm
- http://m.3g.ghtkgg.cn/nnews/783984.htm
- http://m.3g.ghtkgg.cn/nnews/905106.htm
- http://m.3g.ghtkgg.cn/nnews/7778211.htm
- http://m.3g.ghtkgg.cn/nnews/555766.htm
- http://m.3g.ghtkgg.cn/nnews/72942.htm
- http://m.3g.ghtkgg.cn/nnews/7022079.htm
- http://m.3g.ghtkgg.cn/nnews/095217.htm
- http://m.3g.ghtkgg.cn/nnews/1853532.htm
- http://m.3g.ghtkgg.cn/nnews/13910.htm
- http://m.3g.ghtkgg.cn/nnews/201872.htm
- http://m.3g.ghtkgg.cn/nnews/4911.htm
- http://m.3g.ghtkgg.cn/nnews/1032.htm
- http://m.3g.ghtkgg.cn/nnews/4665689.htm
- http://m.3g.ghtkgg.cn/nnews/939650.htm
- http://m.3g.ghtkgg.cn/nnews/1151119.htm
- http://m.3g.ghtkgg.cn/nnews/7853.htm
- http://m.3g.ghtkgg.cn/nnews/66116.htm
- http://m.3g.ghtkgg.cn/nnews/5188237.htm
- http://m.3g.ghtkgg.cn/nnews/53930.htm
- http://m.3g.ghtkgg.cn/nnews/0849.htm
- http://m.3g.ghtkgg.cn/nnews/8173.htm
- http://m.3g.ghtkgg.cn/nnews/1260.htm
- http://m.3g.ghtkgg.cn/nnews/8696734.htm
- http://m.3g.ghtkgg.cn/nnews/4949430.htm
- http://m.3g.ghtkgg.cn/nnews/758683.htm
- http://m.3g.ghtkgg.cn/nnews/350988.htm
- http://m.3g.ghtkgg.cn/nnews/228015.htm
- http://m.3g.ghtkgg.cn/nnews/7122.htm
- http://m.3g.ghtkgg.cn/nnews/69732.htm
- http://m.3g.ghtkgg.cn/nnews/13711.htm
- http://m.3g.ghtkgg.cn/nnews/770968.htm
- http://m.3g.ghtkgg.cn/nnews/9714926.htm
- http://m.3g.ghtkgg.cn/nnews/12564.htm
- http://m.3g.ghtkgg.cn/nnews/8563.htm
- http://m.3g.ghtkgg.cn/nnews/5518.htm
- http://m.3g.ghtkgg.cn/nnews/7661266.htm
- http://m.3g.ghtkgg.cn/nnews/0244316.htm
- http://m.3g.ghtkgg.cn/nnews/01162.htm
- http://m.3g.ghtkgg.cn/nnews/881355.htm
- http://m.3g.ghtkgg.cn/nnews/61343.htm
- http://m.3g.ghtkgg.cn/nnews/59594.htm
- http://m.3g.ghtkgg.cn/nnews/8576673.htm
- http://m.3g.ghtkgg.cn/nnews/207839.htm
- http://m.3g.ghtkgg.cn/nnews/042436.htm
- http://m.3g.ghtkgg.cn/nnews/5301853.htm
- http://m.3g.ghtkgg.cn/nnews/0512256.htm
- http://m.3g.ghtkgg.cn/nnews/1238.htm
- http://m.3g.ghtkgg.cn/nnews/055242.htm
- http://m.3g.ghtkgg.cn/nnews/18621.htm
- http://m.3g.ghtkgg.cn/nnews/682233.htm
- http://m.3g.ghtkgg.cn/nnews/6185249.htm
- http://m.3g.ghtkgg.cn/nnews/135242.htm
- http://m.3g.ghtkgg.cn/nnews/2347147.htm
- http://m.3g.ghtkgg.cn/nnews/33278.htm
- http://m.3g.ghtkgg.cn/nnews/502937.htm
- http://m.3g.ghtkgg.cn/nnews/02126.htm
- http://m.3g.ghtkgg.cn/nnews/46974.htm
- http://m.3g.ghtkgg.cn/nnews/644134.htm
- http://m.3g.ghtkgg.cn/nnews/9590846.htm
- http://m.3g.ghtkgg.cn/nnews/74989.htm
- http://m.3g.ghtkgg.cn/nnews/0040.htm
- http://m.3g.ghtkgg.cn/nnews/1866.htm
- http://m.3g.ghtkgg.cn/nnews/4661.htm
- http://m.3g.ghtkgg.cn/nnews/2602169.htm
- http://m.3g.ghtkgg.cn/nnews/17449.htm
- http://m.3g.ghtkgg.cn/nnews/099226.htm
- http://m.3g.ghtkgg.cn/nnews/351269.htm
- http://m.3g.ghtkgg.cn/nnews/95500.htm
- http://m.3g.ghtkgg.cn/nnews/425389.htm
- http://m.3g.ghtkgg.cn/nnews/9542.htm
- http://m.3g.ghtkgg.cn/nnews/153076.htm
- http://m.3g.ghtkgg.cn/nnews/4084863.htm

## 项目结构

```
newslink-archive-indexer/
├── indexer.py                # 主入口脚本，负责解析命令行参数并调度扫描流程
├── config.yaml               # 全局配置文件，定义扫描路径、输出格式与过滤规则
├── core/
│   ├── scanner.py            # 递归扫描器，实现目录遍历与文件发现逻辑
│   ├── parser.py             # HTML 解析器，封装 lxml 并暴露统一的抽取接口
│   ├── hasher.py             # 哈希计算模块，用于生成文件内容指纹与增量判断
│   └── reporter.py           # 报告生成器，输出 JSON/CSV/SQLite 格式的索引结果
├── processors/
│   ├── base.py               # 处理器基类，定义所有自定义处理器必须实现的方法
│   ├── standard.py           # 标准处理器，适用于大多数常见新闻 HTML 结构
│   └── custom_example.py     # 自定义处理器示例，展示如何针对特殊页面编写规则
├── utils/
│   ├── http_client.py        # HTTP 客户端封装，支持超时、重试与代理配置
│   ├── charset_detector.py   # 字符集自动检测工具，基于 charset-normalizer
│   └── logger.py             # 日志模块，提供分级日志输出与文件轮转功能
├── tests/
│   ├── test_scanner.py       # 扫描器单元的测试用例
│   ├── test_parser.py        # 解析器单元的测试用例
│   └── fixtures/             # 测试用的 HTML 样本文件目录
├── docs/
│   ├── getting-started.md    # 入门指南，包含安装与首次运行演示
│   ├── configuration.md      # 配置参考手册，逐项说明所有可调参数
│   ├── processor-api.md      # 处理器开发文档，包含接口定义与最佳实践
│   └── workflows.md          # 工作流示例，涵盖定时索引与异常处理
├── scripts/
│   ├── setup_cron.sh         # 用于配置定时任务的辅助脚本
│   └── export_history.py     # 历史索引记录的导出工具
├── requirements.txt          # Python 依赖清单，包含所有必需与可选库
└── LICENSE                   # MIT 许可证文件
```

## 贡献指南

1. 从 GitHub 仓库派生项目副本至个人账户，并在本地克隆派生后的代码库。创建新的功能分支时，请使用 `feature/` 或 `fix/` 前缀以及简洁的描述性名称，例如 `feature/add-xpath-processor`。

2. 在开发新功能或修复缺陷之前，请先在 `tests/` 目录下补充对应的测试用例，确保所有现有测试均能通过。运行测试套件时使用 `pytest -v` 命令，并确认测试覆盖率达到 80% 以上。

3. 代码风格遵循 PEP 8 规范，提交前使用 `black` 与 `isort` 进行自动格式化。所有公共函数与类必须包含完整的 docstring，说明参数、返回值和可能引发的异常类型。

4. 提交变更时，使用清晰且规范的提交信息格式：首行概括变更内容（不超过 72 字符），随后空一行再详细描述修改背景与实现方式。提交前确保本地通过所有单元测试与静态检查。

5. 向主分支发起合并请求时，请在描述中关联对应的议题编号，并附上变更摘要、测试结果截图或命令行输出。合并请求需要至少一位项目维护者的代码审阅，通过后方可合并。

## 常见问题

问：索引过程中遇到非 UTF-8 编码的 HTML 文件时如何处理？
答：系统内置的字符集自动检测模块会在解析前对每个文件进行编码探测。若探测失败或误判，用户可通过配置文件中 `fallback_encoding` 字段指定默认编码，例如 `gbk` 或 `big5`。此外，处理器接口中允许重写 `detect_encoding` 方法以提供自定义检测逻辑。

问：如何对大量历史文件进行首次全量索引，以避免超时或内存溢出？
答：推荐使用分批处理模式。在配置文件中设置 `batch_size` 参数，系统将按指定数量分批读取文件并逐批提交索引任务。同时，可启用 `resume` 模式，在中断后从上次完成的批次继续，无需重新开始。对于极大数量的文件，建议结合 `--max-files` 命令行参数进行小规模试运行，确认配置正确后再执行全量操作。

问：索引报告中出现的不可达链接是否会自动重试？
答：默认情况下，每个链接仅执行一次可达性检测。用户可通过配置 `retry_count` 与 `retry_delay` 参数启用自动重试机制，系统会对返回 5xx 状态码或超时的链接按指定次数与间隔进行重试。最终仍失败的链接会在报告中被标记为 `unreachable`，并记录最后一次尝试的响应详情。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:59
