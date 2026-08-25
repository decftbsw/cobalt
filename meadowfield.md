# NewsLink Hub

NewsLink Hub 是一个面向技术信息聚合与新闻外链管理的开源工具集，专注于从移动端新闻源（m.3g.oexnr.cn）批量采集、归档和展示新闻条目。项目定位为技术研究与内容聚合场景下的轻量级外链数据中台，服务于需要快速构建新闻概览、历史记录回溯或 URL 归集能力的技术人员与内容运营者。

项目本身不提供新闻正文渲染或全文检索，而是以原始链接为最小操作单元，提供链接去重、批量导入、状态检测与导出等基础能力。目标用户包括开源情报分析人员、新闻聚合站点开发者、以及有批量 URL 管理需求的运维工程师。

## 功能概览

- 批量链接导入：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入新闻链接，自动解析域名与路径参数。
- 链接状态批量检测：并发检测每个新闻链接的 HTTP 状态码，快速识别死链、重定向或可访问资源。
- 元数据自动提取：从链接路径中提取新闻 ID 与发布时间戳，生成可排序的索引字段。
- 去重与冲突处理：基于新闻 ID 和完整 URL 双重去重，支持覆盖或跳过策略。
- 标签与分类管理：允许用户为链接打上自定义标签（如“技术”、“社会”、“国际”），便于后续筛选。
- 数据导出为结构化格式：支持将链接列表导出为 JSON、CSV 或纯文本格式，兼容主流数据分析工具。
- 定时任务调度：内置简单的 cron 表达式支持，可定时执行链接状态刷新与报告生成。
- RESTful API 接口：提供只读 API 供外部系统查询链接列表、状态与元数据。

## 应用场景

- 新闻聚合站点后端数据采集：作为爬虫下游模块，接收爬取到的新闻 URL，进行去重和状态验证，再交由渲染层展示。
- 历史新闻链接归档与审计：运营人员定期将一批新闻链接导入系统，系统自动记录导入时间与状态变化，形成可追溯的审计日志。
- 技术研究中的数据集构建：研究人员收集特定时间段内的新闻链接作为样本集，通过本工具导出结构化元数据，用于后续内容分析或趋势研究。
- 运维监控告警联动：配合监控系统，当大量新闻链接返回 4xx 或 5xx 状态时触发告警，提示源站或网络异常。
- 个人知识库外链管理：个人用户可将分散的新闻链接集中管理，添加备注与分类，避免链接遗失或遗忘。

## 快速开始

以下步骤帮助您在本地环境快速启动 NewsLink Hub。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newslink-hub.git

# 进入项目目录
cd newslink-hub

# 安装依赖（基于 Python 3.10+，使用 pip）
pip install -r requirements.txt

# 初始化数据库（SQLite）
python scripts/init_db.py

# 启动开发服务器（默认监听 127.0.0.1:8000）
python app.py
```

启动后，访问 http://127.0.0.1:8000/docs 可查看自动生成的 API 文档。您也可以通过命令行工具直接导入 URL 列表：

```bash
python cli.py import --file urls.txt --source "news-batch-9"
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 或更高 | 核心运行环境，低于此版本将无法使用异步特性 |
| SQLite | 3.35.0 或更高 | 默认内置数据库，用于存储链接元数据与状态 |
| aiohttp | 3.9.0 或更高 | 用于异步 HTTP 请求，执行批量状态检测 |
| pandas | 2.0.0 或更高 | 可选，用于高级数据导出与统计分析 |
| pytest | 7.4.0 或更高 | 仅开发测试需要，生产环境可不安装 |
| requests | 2.31.0 或更高 | 同步 HTTP 客户端，用于部分兼容性接口 |
| python-dotenv | 1.0.0 或更高 | 环境变量加载，用于配置 API 密钥或代理 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/quickstart.md | 如何安装、配置并运行第一个导入任务？API 密钥如何生成？ |
| API 参考 | docs/api_reference.md | 每个 RESTful 接口的请求参数、返回结构与错误码说明。 |
| 命令行工具 | docs/cli_usage.md | 所有 CLI 子命令（import、check、export、schedule）的完整用法与示例。 |
| 部署指南 | docs/deployment.md | 如何将系统部署到生产环境（Nginx + Gunicorn、Docker 容器化、环境变量配置）。 |
| 数据模型 | docs/data_model.md | 链接表、标签表、任务表的字段定义、索引策略与迁移脚本说明。 |
| 性能调优 | docs/performance.md | 并发数调整、数据库连接池配置、缓存策略建议。 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/6839232.htm
- http://m.3g.oexnr.cn/nnews/530489.htm
- http://m.3g.oexnr.cn/nnews/2702.htm
- http://m.3g.oexnr.cn/nnews/5302.htm
- http://m.3g.oexnr.cn/nnews/2979386.htm
- http://m.3g.oexnr.cn/nnews/5018.htm
- http://m.3g.oexnr.cn/nnews/9545185.htm
- http://m.3g.oexnr.cn/nnews/7691876.htm
- http://m.3g.oexnr.cn/nnews/8194.htm
- http://m.3g.oexnr.cn/nnews/17696.htm
- http://m.3g.oexnr.cn/nnews/0722.htm
- http://m.3g.oexnr.cn/nnews/4348.htm
- http://m.3g.oexnr.cn/nnews/372576.htm
- http://m.3g.oexnr.cn/nnews/28504.htm
- http://m.3g.oexnr.cn/nnews/8181586.htm
- http://m.3g.oexnr.cn/nnews/57400.htm
- http://m.3g.oexnr.cn/nnews/034713.htm
- http://m.3g.oexnr.cn/nnews/1272718.htm
- http://m.3g.oexnr.cn/nnews/5047.htm
- http://m.3g.oexnr.cn/nnews/8631115.htm
- http://m.3g.oexnr.cn/nnews/626245.htm
- http://m.3g.oexnr.cn/nnews/596887.htm
- http://m.3g.oexnr.cn/nnews/28626.htm
- http://m.3g.oexnr.cn/nnews/81029.htm
- http://m.3g.oexnr.cn/nnews/7884030.htm
- http://m.3g.oexnr.cn/nnews/359448.htm
- http://m.3g.oexnr.cn/nnews/7420434.htm
- http://m.3g.oexnr.cn/nnews/29808.htm
- http://m.3g.oexnr.cn/nnews/14645.htm
- http://m.3g.oexnr.cn/nnews/101906.htm
- http://m.3g.oexnr.cn/nnews/551408.htm
- http://m.3g.oexnr.cn/nnews/2203733.htm
- http://m.3g.oexnr.cn/nnews/9977.htm
- http://m.3g.oexnr.cn/nnews/33682.htm
- http://m.3g.oexnr.cn/nnews/7986265.htm
- http://m.3g.oexnr.cn/nnews/9332.htm
- http://m.3g.oexnr.cn/nnews/0677946.htm
- http://m.3g.oexnr.cn/nnews/900369.htm
- http://m.3g.oexnr.cn/nnews/618673.htm
- http://m.3g.oexnr.cn/nnews/28828.htm
- http://m.3g.oexnr.cn/nnews/317125.htm
- http://m.3g.oexnr.cn/nnews/0600.htm
- http://m.3g.oexnr.cn/nnews/74975.htm
- http://m.3g.oexnr.cn/nnews/12891.htm
- http://m.3g.oexnr.cn/nnews/48459.htm
- http://m.3g.oexnr.cn/nnews/30793.htm
- http://m.3g.oexnr.cn/nnews/19079.htm
- http://m.3g.oexnr.cn/nnews/149188.htm
- http://m.3g.oexnr.cn/nnews/2089.htm
- http://m.3g.oexnr.cn/nnews/7293693.htm
- http://m.3g.oexnr.cn/nnews/9058958.htm
- http://m.3g.oexnr.cn/nnews/201293.htm
- http://m.3g.oexnr.cn/nnews/213704.htm
- http://m.3g.oexnr.cn/nnews/527143.htm
- http://m.3g.oexnr.cn/nnews/8887.htm
- http://m.3g.oexnr.cn/nnews/0364808.htm
- http://m.3g.oexnr.cn/nnews/561768.htm
- http://m.3g.oexnr.cn/nnews/408830.htm
- http://m.3g.oexnr.cn/nnews/27863.htm
- http://m.3g.oexnr.cn/nnews/89038.htm
- http://m.3g.oexnr.cn/nnews/37128.htm
- http://m.3g.oexnr.cn/nnews/466063.htm
- http://m.3g.oexnr.cn/nnews/6495265.htm
- http://m.3g.oexnr.cn/nnews/39825.htm
- http://m.3g.oexnr.cn/nnews/359483.htm
- http://m.3g.oexnr.cn/nnews/41030.htm
- http://m.3g.oexnr.cn/nnews/2476.htm
- http://m.3g.oexnr.cn/nnews/1497.htm
- http://m.3g.oexnr.cn/nnews/7878.htm
- http://m.3g.oexnr.cn/nnews/57524.htm
- http://m.3g.oexnr.cn/nnews/807199.htm
- http://m.3g.oexnr.cn/nnews/886790.htm
- http://m.3g.oexnr.cn/nnews/45998.htm
- http://m.3g.oexnr.cn/nnews/474587.htm
- http://m.3g.oexnr.cn/nnews/24142.htm
- http://m.3g.oexnr.cn/nnews/1504.htm
- http://m.3g.oexnr.cn/nnews/553430.htm
- http://m.3g.oexnr.cn/nnews/182454.htm
- http://m.3g.oexnr.cn/nnews/0059798.htm
- http://m.3g.oexnr.cn/nnews/4297139.htm
- http://m.3g.oexnr.cn/nnews/8965526.htm
- http://m.3g.oexnr.cn/nnews/832045.htm
- http://m.3g.oexnr.cn/nnews/8984445.htm
- http://m.3g.oexnr.cn/nnews/9721891.htm
- http://m.3g.oexnr.cn/nnews/357676.htm
- http://m.3g.oexnr.cn/nnews/49891.htm
- http://m.3g.oexnr.cn/nnews/61467.htm
- http://m.3g.oexnr.cn/nnews/4278334.htm
- http://m.3g.oexnr.cn/nnews/84802.htm
- http://m.3g.oexnr.cn/nnews/9445.htm
- http://m.3g.oexnr.cn/nnews/9355776.htm
- http://m.3g.oexnr.cn/nnews/517796.htm
- http://m.3g.oexnr.cn/nnews/390939.htm
- http://m.3g.oexnr.cn/nnews/3908.htm
- http://m.3g.oexnr.cn/nnews/9253.htm
- http://m.3g.oexnr.cn/nnews/1507.htm
- http://m.3g.oexnr.cn/nnews/7642791.htm
- http://m.3g.oexnr.cn/nnews/477320.htm
- http://m.3g.oexnr.cn/nnews/2028.htm
- http://m.3g.oexnr.cn/nnews/741113.htm
- http://m.3g.oexnr.cn/nnews/4097441.htm
- http://m.3g.oexnr.cn/nnews/1379274.htm
- http://m.3g.oexnr.cn/nnews/6157.htm
- http://m.3g.oexnr.cn/nnews/098061.htm
- http://m.3g.oexnr.cn/nnews/392027.htm
- http://m.3g.oexnr.cn/nnews/774475.htm
- http://m.3g.oexnr.cn/nnews/57401.htm
- http://m.3g.oexnr.cn/nnews/96114.htm
- http://m.3g.oexnr.cn/nnews/552871.htm
- http://m.3g.oexnr.cn/nnews/29988.htm
- http://m.3g.oexnr.cn/nnews/1690877.htm
- http://m.3g.oexnr.cn/nnews/145517.htm
- http://m.3g.oexnr.cn/nnews/9868976.htm
- http://m.3g.oexnr.cn/nnews/4101.htm
- http://m.3g.oexnr.cn/nnews/4260.htm
- http://m.3g.oexnr.cn/nnews/8329725.htm
- http://m.3g.oexnr.cn/nnews/987625.htm
- http://m.3g.oexnr.cn/nnews/7771.htm
- http://m.3g.oexnr.cn/nnews/10124.htm
- http://m.3g.oexnr.cn/nnews/327144.htm
- http://m.3g.oexnr.cn/nnews/855598.htm
- http://m.3g.oexnr.cn/nnews/00033.htm
- http://m.3g.oexnr.cn/nnews/8339.htm
- http://m.3g.oexnr.cn/nnews/7290.htm
- http://m.3g.oexnr.cn/nnews/2676728.htm
- http://m.3g.oexnr.cn/nnews/1769380.htm
- http://m.3g.oexnr.cn/nnews/944375.htm
- http://m.3g.oexnr.cn/nnews/8405.htm
- http://m.3g.oexnr.cn/nnews/9544.htm
- http://m.3g.oexnr.cn/nnews/97541.htm
- http://m.3g.oexnr.cn/nnews/2367.htm
- http://m.3g.oexnr.cn/nnews/2736014.htm
- http://m.3g.oexnr.cn/nnews/0728.htm
- http://m.3g.oexnr.cn/nnews/6951951.htm
- http://m.3g.oexnr.cn/nnews/77357.htm
- http://m.3g.oexnr.cn/nnews/50308.htm
- http://m.3g.oexnr.cn/nnews/0378938.htm
- http://m.3g.oexnr.cn/nnews/559210.htm
- http://m.3g.oexnr.cn/nnews/1053107.htm
- http://m.3g.oexnr.cn/nnews/7859798.htm
- http://m.3g.oexnr.cn/nnews/9656.htm
- http://m.3g.oexnr.cn/nnews/9738511.htm
- http://m.3g.oexnr.cn/nnews/419860.htm
- http://m.3g.oexnr.cn/nnews/2397.htm
- http://m.3g.oexnr.cn/nnews/83610.htm
- http://m.3g.oexnr.cn/nnews/03826.htm
- http://m.3g.oexnr.cn/nnews/12685.htm
- http://m.3g.oexnr.cn/nnews/8919.htm
- http://m.3g.oexnr.cn/nnews/355903.htm
- http://m.3g.oexnr.cn/nnews/6402544.htm
- http://m.3g.oexnr.cn/nnews/049231.htm
- http://m.3g.oexnr.cn/nnews/527710.htm
- http://m.3g.oexnr.cn/nnews/3986.htm
- http://m.3g.oexnr.cn/nnews/8418920.htm
- http://m.3g.oexnr.cn/nnews/4086.htm
- http://m.3g.oexnr.cn/nnews/610092.htm
- http://m.3g.oexnr.cn/nnews/0650365.htm
- http://m.3g.oexnr.cn/nnews/2860.htm
- http://m.3g.oexnr.cn/nnews/67150.htm
- http://m.3g.oexnr.cn/nnews/7821030.htm
- http://m.3g.oexnr.cn/nnews/747782.htm
- http://m.3g.oexnr.cn/nnews/8808363.htm
- http://m.3g.oexnr.cn/nnews/4719248.htm
- http://m.3g.oexnr.cn/nnews/8974439.htm
- http://m.3g.oexnr.cn/nnews/9496290.htm
- http://m.3g.oexnr.cn/nnews/1430057.htm
- http://m.3g.oexnr.cn/nnews/260936.htm
- http://m.3g.oexnr.cn/nnews/2434.htm
- http://m.3g.oexnr.cn/nnews/52256.htm
- http://m.3g.oexnr.cn/nnews/450428.htm
- http://m.3g.oexnr.cn/nnews/0111976.htm
- http://m.3g.oexnr.cn/nnews/1966.htm
- http://m.3g.oexnr.cn/nnews/54820.htm
- http://m.3g.oexnr.cn/nnews/733302.htm
- http://m.3g.oexnr.cn/nnews/6352.htm
- http://m.3g.oexnr.cn/nnews/61514.htm
- http://m.3g.oexnr.cn/nnews/625962.htm
- http://m.3g.oexnr.cn/nnews/760681.htm
- http://m.3g.oexnr.cn/nnews/1246241.htm
- http://m.3g.oexnr.cn/nnews/791758.htm
- http://m.3g.oexnr.cn/nnews/2599.htm
- http://m.3g.oexnr.cn/nnews/117247.htm
- http://m.3g.oexnr.cn/nnews/989750.htm
- http://m.3g.oexnr.cn/nnews/809401.htm
- http://m.3g.oexnr.cn/nnews/092221.htm
- http://m.3g.oexnr.cn/nnews/5701066.htm
- http://m.3g.oexnr.cn/nnews/25298.htm
- http://m.3g.oexnr.cn/nnews/1403856.htm
- http://m.3g.oexnr.cn/nnews/81514.htm
- http://m.3g.oexnr.cn/nnews/26901.htm
- http://m.3g.oexnr.cn/nnews/201871.htm
- http://m.3g.oexnr.cn/nnews/739746.htm
- http://m.3g.oexnr.cn/nnews/4097.htm
- http://m.3g.oexnr.cn/nnews/22752.htm
- http://m.3g.oexnr.cn/nnews/42376.htm
- http://m.3g.oexnr.cn/nnews/6209.htm
- http://m.3g.oexnr.cn/nnews/4618.htm
- http://m.3g.oexnr.cn/nnews/559530.htm
- http://m.3g.oexnr.cn/nnews/9644.htm
- http://m.3g.oexnr.cn/nnews/75027.htm
- http://m.3g.oexnr.cn/nnews/08458.htm
- http://m.3g.oexnr.cn/nnews/7275870.htm
- http://m.3g.oexnr.cn/nnews/5074.htm
- http://m.3g.oexnr.cn/nnews/4606727.htm
- http://m.3g.oexnr.cn/nnews/11817.htm
- http://m.3g.oexnr.cn/nnews/5992460.htm
- http://m.3g.oexnr.cn/nnews/07009.htm
- http://m.3g.oexnr.cn/nnews/7225569.htm
- http://m.3g.oexnr.cn/nnews/2156.htm
- http://m.3g.oexnr.cn/nnews/59936.htm
- http://m.3g.oexnr.cn/nnews/599063.htm
- http://m.3g.oexnr.cn/nnews/9119904.htm
- http://m.3g.oexnr.cn/nnews/0510.htm
- http://m.3g.oexnr.cn/nnews/148413.htm
- http://m.3g.oexnr.cn/nnews/240776.htm
- http://m.3g.oexnr.cn/nnews/9957.htm
- http://m.3g.oexnr.cn/nnews/3773207.htm
- http://m.3g.oexnr.cn/nnews/8891519.htm
- http://m.3g.oexnr.cn/nnews/276713.htm
- http://m.3g.oexnr.cn/nnews/0902431.htm
- http://m.3g.oexnr.cn/nnews/0865936.htm
- http://m.3g.oexnr.cn/nnews/90872.htm
- http://m.3g.oexnr.cn/nnews/7420965.htm
- http://m.3g.oexnr.cn/nnews/3784.htm
- http://m.3g.oexnr.cn/nnews/1053254.htm
- http://m.3g.oexnr.cn/nnews/126611.htm
- http://m.3g.oexnr.cn/nnews/96759.htm
- http://m.3g.oexnr.cn/nnews/00802.htm
- http://m.3g.oexnr.cn/nnews/8702.htm
- http://m.3g.oexnr.cn/nnews/7948.htm
- http://m.3g.oexnr.cn/nnews/0020369.htm
- http://m.3g.oexnr.cn/nnews/98736.htm
- http://m.3g.oexnr.cn/nnews/4581.htm
- http://m.3g.oexnr.cn/nnews/109552.htm
- http://m.3g.oexnr.cn/nnews/879155.htm
- http://m.3g.oexnr.cn/nnews/8335.htm
- http://m.3g.oexnr.cn/nnews/4034.htm
- http://m.3g.oexnr.cn/nnews/56852.htm
- http://m.3g.oexnr.cn/nnews/411759.htm
- http://m.3g.oexnr.cn/nnews/31159.htm
- http://m.3g.oexnr.cn/nnews/32759.htm
- http://m.3g.oexnr.cn/nnews/1693243.htm
- http://m.3g.oexnr.cn/nnews/67953.htm
- http://m.3g.oexnr.cn/nnews/577251.htm
- http://m.3g.oexnr.cn/nnews/0936737.htm
- http://m.3g.oexnr.cn/nnews/60243.htm
- http://m.3g.oexnr.cn/nnews/66052.htm
- http://m.3g.oexnr.cn/nnews/8587938.htm
- http://m.3g.oexnr.cn/nnews/3736593.htm
- http://m.3g.oexnr.cn/nnews/0288634.htm
- http://m.3g.oexnr.cn/nnews/74720.htm
- http://m.3g.oexnr.cn/nnews/9480759.htm
- http://m.3g.oexnr.cn/nnews/4393265.htm
- http://m.3g.oexnr.cn/nnews/9154861.htm
- http://m.3g.oexnr.cn/nnews/184188.htm
- http://m.3g.oexnr.cn/nnews/248926.htm
- http://m.3g.oexnr.cn/nnews/51642.htm
- http://m.3g.oexnr.cn/nnews/001708.htm
- http://m.3g.oexnr.cn/nnews/3838.htm
- http://m.3g.oexnr.cn/nnews/2804557.htm
- http://m.3g.oexnr.cn/nnews/871750.htm
- http://m.3g.oexnr.cn/nnews/7412951.htm
- http://m.3g.oexnr.cn/nnews/260556.htm
- http://m.3g.oexnr.cn/nnews/94254.htm
- http://m.3g.oexnr.cn/nnews/198740.htm
- http://m.3g.oexnr.cn/nnews/6690060.htm
- http://m.3g.oexnr.cn/nnews/0412473.htm
- http://m.3g.oexnr.cn/nnews/9633.htm
- http://m.3g.oexnr.cn/nnews/884646.htm
- http://m.3g.oexnr.cn/nnews/9018.htm
- http://m.3g.oexnr.cn/nnews/8020.htm
- http://m.3g.oexnr.cn/nnews/0971419.htm
- http://m.3g.oexnr.cn/nnews/4016249.htm
- http://m.3g.oexnr.cn/nnews/4148074.htm
- http://m.3g.oexnr.cn/nnews/40541.htm
- http://m.3g.oexnr.cn/nnews/3768695.htm
- http://m.3g.oexnr.cn/nnews/3983.htm
- http://m.3g.oexnr.cn/nnews/9660.htm
- http://m.3g.oexnr.cn/nnews/756100.htm
- http://m.3g.oexnr.cn/nnews/124200.htm
- http://m.3g.oexnr.cn/nnews/37950.htm
- http://m.3g.oexnr.cn/nnews/453893.htm
- http://m.3g.oexnr.cn/nnews/833685.htm
- http://m.3g.oexnr.cn/nnews/351835.htm
- http://m.3g.oexnr.cn/nnews/37133.htm
- http://m.3g.oexnr.cn/nnews/430599.htm
- http://m.3g.oexnr.cn/nnews/2704.htm
- http://m.3g.oexnr.cn/nnews/9267.htm
- http://m.3g.oexnr.cn/nnews/989112.htm
- http://m.3g.oexnr.cn/nnews/9342759.htm
- http://m.3g.oexnr.cn/nnews/93265.htm
- http://m.3g.oexnr.cn/nnews/0976107.htm
- http://m.3g.oexnr.cn/nnews/70698.htm
- http://m.3g.oexnr.cn/nnews/9347.htm
- http://m.3g.oexnr.cn/nnews/22986.htm
- http://m.3g.oexnr.cn/nnews/7986005.htm
- http://m.3g.oexnr.cn/nnews/45695.htm
- http://m.3g.oexnr.cn/nnews/5065381.htm
- http://m.3g.oexnr.cn/nnews/222853.htm
- http://m.3g.oexnr.cn/nnews/1018.htm

## 项目结构

```
newslink-hub/
├── app/                            # 主应用模块
│   ├── __init__.py                 # 应用工厂与配置加载
│   ├── main.py                     # FastAPI 入口，路由注册与中间件
│   ├── models.py                   # SQLAlchemy 数据模型（Link, Tag, Task）
│   ├── schemas.py                  # Pydantic 请求/响应结构定义
│   ├── dependencies.py             # 依赖注入（数据库会话、配置对象）
│   └── routers/                    # API 路由子模块
│       ├── links.py                # 链接 CRUD 与批量操作接口
│       ├── status.py               # 状态检测与刷新接口
│       └── export.py               # 导出接口（JSON/CSV）
├── core/                           # 核心业务逻辑层
│   ├── __init__.py
│   ├── fetcher.py                  # 异步 HTTP 抓取与状态判断
│   ├── parser.py                   # URL 路径解析与 ID 提取
│   ├── dedup.py                    # 去重算法（布隆过滤器 + 哈希表）
│   └── scheduler.py                # 定时任务调度器（基于 asyncio + cron）
├── cli/                            # 命令行工具子模块
│   ├── __init__.py
│   ├── import_cmd.py               # 导入命令实现
│   ├── check_cmd.py                # 状态检测命令实现
│   ├── export_cmd.py               # 导出命令实现
│   └── schedule_cmd.py             # 调度管理命令
├── scripts/                        # 辅助脚本与运维工具
│   ├── init_db.py                  # 初始化数据库表与索引
│   ├── migrate_v1_to_v2.py         # 数据迁移脚本（示例）
│   └── seed_test_data.py           # 生成测试数据
├── tests/                          # 单元测试与集成测试
│   ├── conftest.py                 # pytest 配置与夹具
│   ├── test_fetcher.py             # 异步抓取逻辑测试
│   ├── test_dedup.py               # 去重算法测试
│   └── test_api_links.py           # API 接口测试
├── docs/                           # 文档源文件（Markdown）
│   ├── quickstart.md
│   ├── api_reference.md
│   ├── cli_usage.md
│   └── deployment.md
├── config/                         # 配置文件目录
│   ├── default.yaml                # 默认配置（开发环境）
│   ├── production.yaml             # 生产环境覆盖配置
│   └── logging.conf                # 日志格式与级别配置
├── data/                           # 数据存储目录（默认 SQLite 文件存放处）
│   └── newslink.db                 # SQLite 数据库文件（运行时生成）
├── logs/                           # 应用日志目录
│   └── app.log                     # 滚动日志文件
├── requirements.txt                # Python 依赖列表（生产）
├── requirements-dev.txt            # 开发与测试额外依赖
├── Dockerfile                      # 容器化构建文件（基于 Python 3.10-slim）
├── docker-compose.yml              # 本地容器编排（含 Redis 可选缓存）
├── .env.example                    # 环境变量示例（API_KEY, DATABASE_URL）
├── .gitignore
├── LICENSE                         # MIT 许可证
└── README.md                       # 本文件
```

## 贡献指南

1. 复刻项目仓库至个人账号，并克隆到本地开发环境。确保本地 Python 版本为 3.10 或更高，且已安装 requirements-dev.txt 中的开发依赖。
2. 创建新的功能分支，分支命名遵循 feat/功能简述 或 fix/问题简述 的格式。例如 feat/export-json-streaming。
3. 编写或修改代码后，请确保所有现有单元测试通过，并为新增功能补充对应的测试用例（位于 tests/ 目录下）。运行 pytest 进行全量测试。
4. 提交代码前，请执行代码风格检查（使用 black 与 flake8）并修复所有警告。提交信息使用英文，采用 Conventional Commits 规范（如 feat: 或 fix: 开头）。
5. 发起 Pull Request 到主仓库的 main 分支，并在 PR 描述中关联相关 Issue（若有），说明改动内容、测试覆盖情况以及潜在影响范围。

## 常见问题

Q: 导入大批量 URL 时系统响应缓慢，如何优化？

A: 对于超过 1000 条的批量导入，建议使用 CLI 工具的 --chunk-size 参数控制单次提交数量（默认 500）。同时可调整 core/fetcher.py 中的并发数（MAX_CONCURRENT_REQUESTS）以平衡系统资源。生产环境建议配置 Redis 作为缓存层，减少重复数据库查询。

Q: 链接状态检测返回 403 或 429 错误，如何处理？

A: 部分新闻源可能对自动化请求有限制。可在 .env 中配置 USER_AGENT 和 REQUEST_HEADERS 模拟移动端浏览器。若仍被限制，可通过 scheduler 模块配置检测重试策略（指数退避），并适当增大 RETRY_INTERVAL 与 MAX_RETRIES 参数。

Q: 如何迁移已有数据到新版本数据库？

A: 项目提供了 scripts/migrate_v1_to_v2.py 脚本。执行前请备份原数据库文件。该脚本会读取原表结构，映射新字段，并处理数据转换。若自定义了字段映射，请提前修改迁移脚本中的 column_mapping 字典。

Q: 是否支持 PostgreSQL 替代 SQLite？

A: 支持。项目使用 SQLAlchemy ORM，只需在 DATABASE_URL 环境变量中填写 PostgreSQL 连接字符串（如 postgresql://user:pass@localhost/dbname），并安装 psycopg2-binary 依赖即可。部分 SQLite 特有的函数（如 date()）在 PostgreSQL 中需对应调整为 NOW()，请参考 docs/deployment.md 中的适配说明。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
