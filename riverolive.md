# NewsIndexer

NewsIndexer 是一个面向技术资讯聚合与外部资源索引的开源工具，定位于帮助开发者、研究员与技术内容消费者从分散的新闻源、博客平台与行业动态中快速提取结构化元数据，构建可检索、可追踪的外部链接知识库。该项目并非传统 RSS 阅读器或爬虫框架，而是一个轻量级的链接资产管理中间件，专门处理海量外链的归一化清洗、有效性预检、标签化分类与批次管理，适用于需要长期维护大量外部 URL 引用的文档站点、技术周报生成器或行业舆情看板。

NewsIndexer 当前批次承载第 184/300 批资源链接，共计 300 个原始条目，覆盖技术博客、行业新闻、开发者社区等多类来源。项目提供命令行接口与 HTTP API 两种交互方式，支持单条或批量导入链接，自动完成去重、协议归一化、域名黑名单过滤与响应状态码探测，最终输出结构化的 JSON 报告与 Markdown 索引表。对于需要定期更新外部链接列表且要求输出格式严格可控的团队，NewsIndexer 提供了开箱即用的批次处理流水线。

## 功能概览

批量链接导入：支持从纯文本文件、CSV 或标准输入流中一次性导入大量 URL，自动解析每行条目并跳过空行与无效协议。

智能归一化清洗：对输入的 URL 执行强制去除末尾斜杠、大小写统一、协议补全（HTTP/HTTPS 自动识别）以及冗余查询参数剥离，确保存储格式一致。

存活状态预检：通过可配置的超时与重试策略，对每条链接发起 HEAD 请求，返回状态码类别（2xx/4xx/5xx）并标记不可达条目，支持并发探测以提升吞吐。

标签分类引擎：基于域名白名单、路径关键词正则匹配与自定义规则文件，为每条链接自动生成技术栈、行业领域或内容类型标签，便于后续按主题筛选。

批次元数据管理：记录每批资源的导入时间戳、来源文件哈希、处理耗时与失败条目数，支持按批次版本回溯历史索引状态。

导出格式灵活：内置 Markdown 列表、JSON 数组、CSV 表格三种导出模板，并允许用户自定义字段分隔符与排序规则，适配不同下游系统的输入要求。

增量更新支持：对比新旧批次链接集合，自动计算新增、删除与未变动条目，输出差异报告，避免全量重建索引。

## 应用场景

技术周报自动化生成：编辑团队每周收集约 200 条技术新闻链接，使用 NewsIndexer 批量导入后自动完成去重与分类，再根据标签筛选出前端、后端、AI 等板块，直接输出 Markdown 格式的周报草稿，减少手工整理时间。

行业舆情监控数据清洗：舆情分析系统每日从多个渠道抓取数千条新闻 URL，原始数据包含大量重复、失效或无关链接。NewsIndexer 作为预处理前置节点，在数据进入存储层之前完成归一化与存活检测，确保下游分析模型仅处理有效且唯一的外部引用。

开源文档外链维护：技术文档仓库往往包含大量外部参考链接，随着时间推移部分链接会失效或跳转。NewsIndexer 可定期扫描文档目录下的 Markdown 文件，提取所有外链并进行批量状态检查，生成失效链接报告供维护者修复。

竞品动态追踪：产品团队维护一份竞品公司官方博客与媒体报道的链接清单，通过 NewsIndexer 的标签分类引擎自动标记来源类型（官方公告/第三方评测/论坛讨论），并用批次差异对比功能监控每周新增的竞品相关链接。

## 快速开始

以下命令演示了从克隆仓库到运行一次完整批次处理的完整流程，请确保系统已安装 Git 与 Python 3.9 以上版本。

```bash
git clone https://github.com/newsindexer/newsindexer.git
cd newsindexer
pip install -r requirements.txt
python cli.py import --input ./samples/batch_184.txt --output ./reports/batch_184.json --format json
python cli.py export --input ./reports/batch_184.json --output ./reports/batch_184.md --format markdown
```

首次运行时会自动在项目根目录下创建 `data/` 和 `reports/` 两个文件夹，所有中间结果与最终报告均落盘于此。若需启用并发探测，可在 `config.yaml` 中调整 `probe_workers` 参数。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，低于 3.9 将无法使用类型注解与异步特性 |
| aiohttp | 3.9.0 及以上 | 用于异步 HTTP 请求，支撑并发存活探测功能 |
| pandas | 2.0.0 及以上 | 仅在 CSV 导出与数据透视统计时使用，核心导入流程可无 pandas 运行 |
| pyyaml | 6.0 及以上 | 解析 `config.yaml` 配置文件，若缺失则回退至默认参数 |
| click | 8.1.0 及以上 | 命令行交互框架，提供子命令分组与参数校验能力 |
| pytest | 7.4.0 及以上 | 仅在开发与测试环境中使用，生产环境可不安装 |

所有依赖均可通过 `pip install -r requirements.txt` 一次性完成安装。若使用 Docker 部署，则无需单独安装上述依赖，镜像已预置完整环境。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | `docs/user_guide.md` | 如何安装、配置与运行基础导入导出命令；命令行参数含义与示例 |
| 配置参考 | `docs/config_reference.md` | `config.yaml` 中每个字段的作用、默认值与可取值范围 |
| 开发指南 | `docs/development.md` | 项目代码结构、单元测试编写方式、PR 提交流程与代码风格规范 |
| API 参考 | `docs/api_reference.md` | HTTP 服务模式下所有端点、请求体格式、响应码与错误处理细则 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/3652072.htm
- http://m.blog.ghtkgg.cn/nnews/855187.htm
- http://m.blog.ghtkgg.cn/nnews/06258.htm
- http://m.blog.ghtkgg.cn/nnews/05932.htm
- http://m.blog.ghtkgg.cn/nnews/574988.htm
- http://m.blog.ghtkgg.cn/nnews/3332.htm
- http://m.blog.ghtkgg.cn/nnews/1707292.htm
- http://m.blog.ghtkgg.cn/nnews/1932.htm
- http://m.blog.ghtkgg.cn/nnews/0897681.htm
- http://m.blog.ghtkgg.cn/nnews/623203.htm
- http://m.blog.ghtkgg.cn/nnews/88641.htm
- http://m.blog.ghtkgg.cn/nnews/2770.htm
- http://m.blog.ghtkgg.cn/nnews/76168.htm
- http://m.blog.ghtkgg.cn/nnews/1411363.htm
- http://m.blog.ghtkgg.cn/nnews/658324.htm
- http://m.blog.ghtkgg.cn/nnews/7428940.htm
- http://m.blog.ghtkgg.cn/nnews/8980.htm
- http://m.blog.ghtkgg.cn/nnews/24947.htm
- http://m.blog.ghtkgg.cn/nnews/32164.htm
- http://m.blog.ghtkgg.cn/nnews/125948.htm
- http://m.blog.ghtkgg.cn/nnews/3570.htm
- http://m.blog.ghtkgg.cn/nnews/062375.htm
- http://m.blog.ghtkgg.cn/nnews/4658.htm
- http://m.blog.ghtkgg.cn/nnews/578088.htm
- http://m.blog.ghtkgg.cn/nnews/1421610.htm
- http://m.blog.ghtkgg.cn/nnews/0016.htm
- http://m.blog.ghtkgg.cn/nnews/66688.htm
- http://m.blog.ghtkgg.cn/nnews/62241.htm
- http://m.blog.ghtkgg.cn/nnews/055535.htm
- http://m.blog.ghtkgg.cn/nnews/2161941.htm
- http://m.blog.ghtkgg.cn/nnews/8774109.htm
- http://m.blog.ghtkgg.cn/nnews/2759.htm
- http://m.blog.ghtkgg.cn/nnews/0482545.htm
- http://m.blog.ghtkgg.cn/nnews/2137.htm
- http://m.blog.ghtkgg.cn/nnews/639408.htm
- http://m.blog.ghtkgg.cn/nnews/8190.htm
- http://m.blog.ghtkgg.cn/nnews/742848.htm
- http://m.blog.ghtkgg.cn/nnews/2695.htm
- http://m.blog.ghtkgg.cn/nnews/8199.htm
- http://m.blog.ghtkgg.cn/nnews/6034.htm
- http://m.blog.ghtkgg.cn/nnews/08484.htm
- http://m.blog.ghtkgg.cn/nnews/8276.htm
- http://m.blog.ghtkgg.cn/nnews/8287.htm
- http://m.blog.ghtkgg.cn/nnews/2394729.htm
- http://m.blog.ghtkgg.cn/nnews/782131.htm
- http://m.blog.ghtkgg.cn/nnews/1234.htm
- http://m.blog.ghtkgg.cn/nnews/587559.htm
- http://m.blog.ghtkgg.cn/nnews/4750960.htm
- http://m.blog.ghtkgg.cn/nnews/73794.htm
- http://m.blog.ghtkgg.cn/nnews/750367.htm
- http://m.blog.ghtkgg.cn/nnews/5053721.htm
- http://m.blog.ghtkgg.cn/nnews/8177.htm
- http://m.blog.ghtkgg.cn/nnews/4268989.htm
- http://m.blog.ghtkgg.cn/nnews/9132017.htm
- http://m.blog.ghtkgg.cn/nnews/9288900.htm
- http://m.blog.ghtkgg.cn/nnews/8542.htm
- http://m.blog.ghtkgg.cn/nnews/0501990.htm
- http://m.blog.ghtkgg.cn/nnews/6279.htm
- http://m.blog.ghtkgg.cn/nnews/49160.htm
- http://m.blog.ghtkgg.cn/nnews/78971.htm
- http://m.blog.ghtkgg.cn/nnews/64777.htm
- http://m.blog.ghtkgg.cn/nnews/2864.htm
- http://m.blog.ghtkgg.cn/nnews/8557.htm
- http://m.blog.ghtkgg.cn/nnews/1297.htm
- http://m.blog.ghtkgg.cn/nnews/0735.htm
- http://m.blog.ghtkgg.cn/nnews/85642.htm
- http://m.blog.ghtkgg.cn/nnews/8722523.htm
- http://m.blog.ghtkgg.cn/nnews/9689258.htm
- http://m.blog.ghtkgg.cn/nnews/9549.htm
- http://m.blog.ghtkgg.cn/nnews/63674.htm
- http://m.blog.ghtkgg.cn/nnews/160444.htm
- http://m.blog.ghtkgg.cn/nnews/4512.htm
- http://m.blog.ghtkgg.cn/nnews/2635476.htm
- http://m.blog.ghtkgg.cn/nnews/273167.htm
- http://m.blog.ghtkgg.cn/nnews/0568.htm
- http://m.blog.ghtkgg.cn/nnews/4481129.htm
- http://m.blog.ghtkgg.cn/nnews/4214.htm
- http://m.blog.ghtkgg.cn/nnews/334616.htm
- http://m.blog.ghtkgg.cn/nnews/3708.htm
- http://m.blog.ghtkgg.cn/nnews/21482.htm
- http://m.blog.ghtkgg.cn/nnews/10806.htm
- http://m.blog.ghtkgg.cn/nnews/7561.htm
- http://m.blog.ghtkgg.cn/nnews/038543.htm
- http://m.blog.ghtkgg.cn/nnews/5348533.htm
- http://m.blog.ghtkgg.cn/nnews/29429.htm
- http://m.blog.ghtkgg.cn/nnews/8461565.htm
- http://m.blog.ghtkgg.cn/nnews/0096.htm
- http://m.blog.ghtkgg.cn/nnews/91767.htm
- http://m.blog.ghtkgg.cn/nnews/2513.htm
- http://m.blog.ghtkgg.cn/nnews/61843.htm
- http://m.blog.ghtkgg.cn/nnews/67602.htm
- http://m.blog.ghtkgg.cn/nnews/1630.htm
- http://m.blog.ghtkgg.cn/nnews/1553546.htm
- http://m.blog.ghtkgg.cn/nnews/1152.htm
- http://m.blog.ghtkgg.cn/nnews/39038.htm
- http://m.blog.ghtkgg.cn/nnews/1215.htm
- http://m.blog.ghtkgg.cn/nnews/369214.htm
- http://m.blog.ghtkgg.cn/nnews/3269926.htm
- http://m.blog.ghtkgg.cn/nnews/81726.htm
- http://m.blog.ghtkgg.cn/nnews/8604984.htm
- http://m.blog.ghtkgg.cn/nnews/80475.htm
- http://m.blog.ghtkgg.cn/nnews/1017569.htm
- http://m.blog.ghtkgg.cn/nnews/4575996.htm
- http://m.blog.ghtkgg.cn/nnews/2126.htm
- http://m.blog.ghtkgg.cn/nnews/04276.htm
- http://m.blog.ghtkgg.cn/nnews/1763.htm
- http://m.blog.ghtkgg.cn/nnews/9838.htm
- http://m.blog.ghtkgg.cn/nnews/513134.htm
- http://m.blog.ghtkgg.cn/nnews/6735776.htm
- http://m.blog.ghtkgg.cn/nnews/7230710.htm
- http://m.blog.ghtkgg.cn/nnews/190972.htm
- http://m.blog.ghtkgg.cn/nnews/3465.htm
- http://m.blog.ghtkgg.cn/nnews/7856996.htm
- http://m.blog.ghtkgg.cn/nnews/368128.htm
- http://m.blog.ghtkgg.cn/nnews/53385.htm
- http://m.blog.ghtkgg.cn/nnews/504525.htm
- http://m.blog.ghtkgg.cn/nnews/256514.htm
- http://m.blog.ghtkgg.cn/nnews/96061.htm
- http://m.blog.ghtkgg.cn/nnews/542514.htm
- http://m.blog.ghtkgg.cn/nnews/0277185.htm
- http://m.blog.ghtkgg.cn/nnews/824617.htm
- http://m.blog.ghtkgg.cn/nnews/366742.htm
- http://m.blog.ghtkgg.cn/nnews/831377.htm
- http://m.blog.ghtkgg.cn/nnews/6141518.htm
- http://m.blog.ghtkgg.cn/nnews/8530158.htm
- http://m.blog.ghtkgg.cn/nnews/799418.htm
- http://m.blog.ghtkgg.cn/nnews/269238.htm
- http://m.blog.ghtkgg.cn/nnews/304724.htm
- http://m.blog.ghtkgg.cn/nnews/903020.htm
- http://m.blog.ghtkgg.cn/nnews/552207.htm
- http://m.blog.ghtkgg.cn/nnews/74758.htm
- http://m.blog.ghtkgg.cn/nnews/2191.htm
- http://m.blog.ghtkgg.cn/nnews/0764562.htm
- http://m.blog.ghtkgg.cn/nnews/17119.htm
- http://m.blog.ghtkgg.cn/nnews/8866402.htm
- http://m.blog.ghtkgg.cn/nnews/259943.htm
- http://m.blog.ghtkgg.cn/nnews/23742.htm
- http://m.blog.ghtkgg.cn/nnews/31666.htm
- http://m.blog.ghtkgg.cn/nnews/0559.htm
- http://m.blog.ghtkgg.cn/nnews/24611.htm
- http://m.blog.ghtkgg.cn/nnews/4132.htm
- http://m.blog.ghtkgg.cn/nnews/134084.htm
- http://m.blog.ghtkgg.cn/nnews/611424.htm
- http://m.blog.ghtkgg.cn/nnews/24120.htm
- http://m.blog.ghtkgg.cn/nnews/135313.htm
- http://m.blog.ghtkgg.cn/nnews/56072.htm
- http://m.blog.ghtkgg.cn/nnews/61771.htm
- http://m.blog.ghtkgg.cn/nnews/0756485.htm
- http://m.blog.ghtkgg.cn/nnews/6467.htm
- http://m.blog.ghtkgg.cn/nnews/2763.htm
- http://m.blog.ghtkgg.cn/nnews/7184824.htm
- http://m.blog.ghtkgg.cn/nnews/8356.htm
- http://m.blog.ghtkgg.cn/nnews/9577.htm
- http://m.blog.ghtkgg.cn/nnews/06743.htm
- http://m.blog.ghtkgg.cn/nnews/8987.htm
- http://m.blog.ghtkgg.cn/nnews/3409.htm
- http://m.blog.ghtkgg.cn/nnews/5492.htm
- http://m.blog.ghtkgg.cn/nnews/8919436.htm
- http://m.blog.ghtkgg.cn/nnews/4743894.htm
- http://m.blog.ghtkgg.cn/nnews/9658.htm
- http://m.blog.ghtkgg.cn/nnews/2169853.htm
- http://m.blog.ghtkgg.cn/nnews/6745150.htm
- http://m.blog.ghtkgg.cn/nnews/53299.htm
- http://m.blog.ghtkgg.cn/nnews/9511203.htm
- http://m.blog.ghtkgg.cn/nnews/004679.htm
- http://m.blog.ghtkgg.cn/nnews/481326.htm
- http://m.blog.ghtkgg.cn/nnews/3536.htm
- http://m.blog.ghtkgg.cn/nnews/21561.htm
- http://m.blog.ghtkgg.cn/nnews/2032643.htm
- http://m.blog.ghtkgg.cn/nnews/55919.htm
- http://m.blog.ghtkgg.cn/nnews/118944.htm
- http://m.blog.ghtkgg.cn/nnews/415819.htm
- http://m.blog.ghtkgg.cn/nnews/4814247.htm
- http://m.blog.ghtkgg.cn/nnews/8224.htm
- http://m.blog.ghtkgg.cn/nnews/7988029.htm
- http://m.blog.ghtkgg.cn/nnews/0486234.htm
- http://m.blog.ghtkgg.cn/nnews/187694.htm
- http://m.blog.ghtkgg.cn/nnews/9272.htm
- http://m.blog.ghtkgg.cn/nnews/383206.htm
- http://m.blog.ghtkgg.cn/nnews/802474.htm
- http://m.blog.ghtkgg.cn/nnews/594962.htm
- http://m.blog.ghtkgg.cn/nnews/82903.htm
- http://m.blog.ghtkgg.cn/nnews/106510.htm
- http://m.blog.ghtkgg.cn/nnews/420817.htm
- http://m.blog.ghtkgg.cn/nnews/5706341.htm
- http://m.blog.ghtkgg.cn/nnews/4321.htm
- http://m.blog.ghtkgg.cn/nnews/4174384.htm
- http://m.blog.ghtkgg.cn/nnews/382826.htm
- http://m.blog.ghtkgg.cn/nnews/2460.htm
- http://m.blog.ghtkgg.cn/nnews/2448666.htm
- http://m.blog.ghtkgg.cn/nnews/1867848.htm
- http://m.blog.ghtkgg.cn/nnews/01573.htm
- http://m.blog.ghtkgg.cn/nnews/080012.htm
- http://m.blog.ghtkgg.cn/nnews/0364313.htm
- http://m.blog.ghtkgg.cn/nnews/184770.htm
- http://m.blog.ghtkgg.cn/nnews/255704.htm
- http://m.blog.ghtkgg.cn/nnews/56577.htm
- http://m.blog.ghtkgg.cn/nnews/4325.htm
- http://m.blog.ghtkgg.cn/nnews/8015473.htm
- http://m.blog.ghtkgg.cn/nnews/9086.htm
- http://m.blog.ghtkgg.cn/nnews/1816023.htm
- http://m.blog.ghtkgg.cn/nnews/7110668.htm
- http://m.blog.ghtkgg.cn/nnews/410928.htm
- http://m.blog.ghtkgg.cn/nnews/10959.htm
- http://m.blog.ghtkgg.cn/nnews/0548.htm
- http://m.blog.ghtkgg.cn/nnews/7325651.htm
- http://m.blog.ghtkgg.cn/nnews/82506.htm
- http://m.blog.ghtkgg.cn/nnews/634174.htm
- http://m.blog.ghtkgg.cn/nnews/0883.htm
- http://m.blog.ghtkgg.cn/nnews/0928.htm
- http://m.blog.ghtkgg.cn/nnews/6273.htm
- http://m.blog.ghtkgg.cn/nnews/8579289.htm
- http://m.blog.ghtkgg.cn/nnews/80717.htm
- http://m.blog.ghtkgg.cn/nnews/611451.htm
- http://m.blog.ghtkgg.cn/nnews/7047.htm
- http://m.blog.ghtkgg.cn/nnews/05544.htm
- http://m.blog.ghtkgg.cn/nnews/391159.htm
- http://m.blog.ghtkgg.cn/nnews/025006.htm
- http://m.blog.ghtkgg.cn/nnews/93530.htm
- http://m.blog.ghtkgg.cn/nnews/06509.htm
- http://m.blog.ghtkgg.cn/nnews/4441803.htm
- http://m.blog.ghtkgg.cn/nnews/997816.htm
- http://m.blog.ghtkgg.cn/nnews/9239.htm
- http://m.blog.ghtkgg.cn/nnews/678646.htm
- http://m.blog.ghtkgg.cn/nnews/71431.htm
- http://m.blog.ghtkgg.cn/nnews/57816.htm
- http://m.blog.ghtkgg.cn/nnews/91442.htm
- http://m.blog.ghtkgg.cn/nnews/98839.htm
- http://m.blog.ghtkgg.cn/nnews/63716.htm
- http://m.blog.ghtkgg.cn/nnews/720694.htm
- http://m.blog.ghtkgg.cn/nnews/220170.htm
- http://m.blog.ghtkgg.cn/nnews/7437713.htm
- http://m.blog.ghtkgg.cn/nnews/207017.htm
- http://m.blog.ghtkgg.cn/nnews/73602.htm
- http://m.blog.ghtkgg.cn/nnews/2264.htm
- http://m.blog.ghtkgg.cn/nnews/2675.htm
- http://m.blog.ghtkgg.cn/nnews/694749.htm
- http://m.blog.ghtkgg.cn/nnews/4587.htm
- http://m.blog.ghtkgg.cn/nnews/35073.htm
- http://m.blog.ghtkgg.cn/nnews/7473.htm
- http://m.blog.ghtkgg.cn/nnews/4262999.htm
- http://m.blog.ghtkgg.cn/nnews/0889694.htm
- http://m.blog.ghtkgg.cn/nnews/501596.htm
- http://m.blog.ghtkgg.cn/nnews/0295.htm
- http://m.blog.ghtkgg.cn/nnews/28227.htm
- http://m.blog.ghtkgg.cn/nnews/228029.htm
- http://m.blog.ghtkgg.cn/nnews/90865.htm
- http://m.blog.ghtkgg.cn/nnews/6882.htm
- http://m.blog.ghtkgg.cn/nnews/008247.htm
- http://m.blog.ghtkgg.cn/nnews/5252899.htm
- http://m.blog.ghtkgg.cn/nnews/311735.htm
- http://m.blog.ghtkgg.cn/nnews/388142.htm
- http://m.blog.ghtkgg.cn/nnews/131051.htm
- http://m.blog.ghtkgg.cn/nnews/80355.htm
- http://m.blog.ghtkgg.cn/nnews/1983542.htm
- http://m.blog.ghtkgg.cn/nnews/677616.htm
- http://m.blog.ghtkgg.cn/nnews/532835.htm
- http://m.blog.ghtkgg.cn/nnews/906645.htm
- http://m.blog.ghtkgg.cn/nnews/86780.htm
- http://m.blog.ghtkgg.cn/nnews/7854697.htm
- http://m.blog.ghtkgg.cn/nnews/83940.htm
- http://m.blog.ghtkgg.cn/nnews/356363.htm
- http://m.blog.ghtkgg.cn/nnews/748476.htm
- http://m.blog.ghtkgg.cn/nnews/933289.htm
- http://m.blog.ghtkgg.cn/nnews/452780.htm
- http://m.blog.ghtkgg.cn/nnews/35332.htm
- http://m.blog.ghtkgg.cn/nnews/4819273.htm
- http://m.blog.ghtkgg.cn/nnews/920301.htm
- http://m.blog.ghtkgg.cn/nnews/587362.htm
- http://m.blog.ghtkgg.cn/nnews/46010.htm
- http://m.blog.ghtkgg.cn/nnews/4058.htm
- http://m.blog.ghtkgg.cn/nnews/90152.htm
- http://m.blog.ghtkgg.cn/nnews/8651226.htm
- http://m.blog.ghtkgg.cn/nnews/092703.htm
- http://m.blog.ghtkgg.cn/nnews/0049066.htm
- http://m.blog.ghtkgg.cn/nnews/532543.htm
- http://m.blog.ghtkgg.cn/nnews/4601396.htm
- http://m.blog.ghtkgg.cn/nnews/6776068.htm
- http://m.blog.ghtkgg.cn/nnews/428964.htm
- http://m.blog.ghtkgg.cn/nnews/75706.htm
- http://m.blog.ghtkgg.cn/nnews/9085526.htm
- http://m.blog.ghtkgg.cn/nnews/0007.htm
- http://m.blog.ghtkgg.cn/nnews/223854.htm
- http://m.blog.ghtkgg.cn/nnews/446449.htm
- http://m.blog.ghtkgg.cn/nnews/08998.htm
- http://m.blog.ghtkgg.cn/nnews/5692.htm
- http://m.blog.ghtkgg.cn/nnews/635300.htm
- http://m.blog.ghtkgg.cn/nnews/8428039.htm
- http://m.blog.ghtkgg.cn/nnews/116560.htm
- http://m.blog.ghtkgg.cn/nnews/861352.htm
- http://m.blog.ghtkgg.cn/nnews/701397.htm
- http://m.blog.ghtkgg.cn/nnews/722577.htm
- http://m.blog.ghtkgg.cn/nnews/10337.htm
- http://m.blog.ghtkgg.cn/nnews/74471.htm
- http://m.blog.ghtkgg.cn/nnews/6997691.htm
- http://m.blog.ghtkgg.cn/nnews/4895900.htm
- http://m.blog.ghtkgg.cn/nnews/0291852.htm
- http://m.blog.ghtkgg.cn/nnews/5140.htm
- http://m.blog.ghtkgg.cn/nnews/7056352.htm
- http://m.blog.ghtkgg.cn/nnews/4731.htm

## 项目结构

```
newsindexer/
├── cli.py                      # 命令行入口，注册 import/export/check 子命令
├── config.yaml                 # 主配置文件，含探测超时、并发数、标签规则路径
├── requirements.txt            # 生产环境依赖列表，锁定主要版本号
├── data/                       # 数据存储目录，存放原始导入文件与中间缓存
│   ├── raw/                    # 未经处理的原始输入批次文件
│   ├── normalized/             # 经过归一化清洗后的链接集合 (JSON Lines)
│   └── cache/                  # 存活探测结果缓存，避免重复请求同一 URL
├── reports/                    # 导出报告输出目录
│   ├── json/                   # JSON 格式的结构化索引报告
│   └── markdown/               # Markdown 列表与表格形式的可读报告
├── src/                        # 核心源代码目录
│   ├── importer.py             # 批量导入解析器，支持 txt/csv 与标准输入
│   ├── normalizer.py           # URL 归一化模块，处理大小写、斜杠与协议补全
│   ├── probe.py                # 异步存活探测引擎，基于 aiohttp 实现并发 HEAD 请求
│   ├── classifier.py           # 标签分类引擎，加载规则文件并匹配正则
│   ├── differ.py               # 批次差异对比器，输出新增/删除/未变条目
│   └── exporter.py             # 多格式导出器，含 markdown/json/csv 模板
├── tests/                      # 单元测试与集成测试目录
│   ├── test_normalizer.py      # 归一化函数测试用例，覆盖边界输入
│   ├── test_probe.py           # 探测引擎模拟测试，含超时与重试策略验证
│   └── fixtures/               # 测试用的固定样本数据
├── docs/                       # 完整文档目录，包含用户手册与 API 参考
│   ├── user_guide.md           # 面向终端用户的详细操作指南
│   ├── config_reference.md     # 配置文件逐字段说明与示例
│   ├── development.md          # 开发者指南，含环境搭建与测试流程
│   └── api_reference.md        # HTTP API 端点的完整规格说明
└── docker/                     # Docker 镜像构建上下文
    ├── Dockerfile              # 基于 python:3.9-slim 的轻量镜像定义
    └── entrypoint.sh           # 容器启动脚本，传递命令行参数
```

## 贡献指南

提交问题报告与功能请求：请在 GitHub Issues 中使用提供的模板描述问题或建议，务必附带最小复现步骤、预期行为与实际行为对比。对于功能请求，请说明使用场景与优先级。

代码贡献流程：Fork 仓库后创建以 `feature/` 或 `fix/` 为前缀的分支，确保代码通过所有单元测试（`pytest tests/`）并保持测试覆盖率不低于 85%。提交前运行 `black` 与 `isort` 进行代码格式化，并确保无 flake8 警告。

文档完善与翻译：欢迎补充用户手册中的示例、修正配置参考中的错误描述，或添加新的语言支持。文档变更需与代码变更保持同步，避免过时内容。

规则文件扩充：标签分类引擎依赖 `rules/` 目录下的正则规则文件，若您维护特定技术栈或行业领域的链接清单，欢迎提交新增规则条目以提升分类准确率。

## 常见问题

导入时出现 `ConnectionRefusedError` 或超时错误如何处理？

此类错误通常源于网络环境限制或目标服务器拒绝 HEAD 请求。可尝试在 `config.yaml` 中调低 `probe_workers` 并发数（如设为 5），并增加 `probe_timeout` 至 15 秒。若目标站点明确屏蔽 HEAD 方法，可将 `probe_method` 改为 `GET` 并启用 `probe_follow_redirects`。企业内网环境建议配置 HTTP 代理，通过 `config.yaml` 中的 `proxy` 字段指定。

导出的 Markdown 列表排序与预期不符，如何自定义？

导出器默认按照导入顺序输出条目。若需按域名、状态码或标签排序，可在导出命令中添加 `--sort-by` 参数，支持 `domain`、`status`、`tag` 三个选项。例如 `python cli.py export --input report.json --format markdown --sort-by domain` 将按域名升序排列。若需多级排序，可多次指定 `--sort-by`，优先级从左至右递减。

如何仅导出当前批次中新增的链接，而不包含历史已存在的条目？

使用 `differ` 子命令结合历史批次文件进行对比。首先确保历史批次报告以 JSON 格式保存在 `reports/json/` 目录下，然后运行 `python cli.py diff --old reports/json/batch_183.json --new reports/json/batch_184.json --output reports/diff_184.md --format markdown`，输出将仅包含新增与删除条目，便于人工审阅。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
