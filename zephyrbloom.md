# NewsIndexer

NewsIndexer 是一个面向技术资讯聚合与历史新闻存档检索的开源工具集，专为需要从结构化或半结构化新闻源中批量抓取、解析、索引并对外提供查询能力的开发者与数据团队设计。该项目不提供前端展示界面，而是提供一套完整的后端数据处理流水线，涵盖 HTTP 请求调度、HTML 内容解析、元数据提取、关键词标注、增量索引更新以及结果导出等核心环节。目标用户包括独立开发者、垂直领域的内容聚合平台运维人员、搜索引擎优化工程师以及从事网络内容分析的研究人员。

NewsIndexer 解决的核心问题是：当面对大量来源固定、URL 模式规律但内容布局多样化的新闻页面时，如何以最低的维护成本实现稳定的数据采集与结构化存储。项目内置了基于配置的解析规则引擎，允许用户通过 YAML 文件定义不同来源的字段映射关系，并支持通过简单的 RESTful API 触发抓取任务。同时，项目提供命令行工具用于批量处理历史链接，支持断点续传与失败重试机制，能够显著提升大规模历史数据回溯的效率。

## 功能概览

批量链接导入与去重：支持从文本文件或标准输入中批量导入 URL 列表，自动进行 MD5 哈希去重，避免重复处理相同链接。

可配置的解析规则引擎：通过 YAML 配置文件定义每个来源站点的标题、发布时间、正文内容、作者等字段的 CSS 选择器或 XPath 提取规则，支持正则表达式后处理。

增量索引更新机制：基于本地 SQLite 数据库记录每次抓取的状态与内容指纹，仅当页面内容发生变更时才更新索引，减少不必要的网络请求与计算开销。

多线程并发抓取控制：提供可调节的并发工作线程数与请求间隔延迟，支持随机 User-Agent 轮换与代理服务器配置，降低被目标站点限制访问的风险。

结构化数据导出功能：支持将解析后的数据导出为 JSON Lines、CSV 或 Parquet 格式，便于后续导入数据分析工具或数据仓库。

任务状态监控与日志记录：内置基于 logrus 的日志系统，支持输出级别动态调整，并可通过 HTTP 管理端点查看当前任务队列长度、成功率与平均响应时间。

命令行交互与守护进程模式：既支持单次运行的命令行任务模式，也支持以守护进程方式运行并定时触发增量抓取任务，适应不同的运维场景。

## 应用场景

历史新闻数据回溯分析：研究人员或数据分析师需要针对某一时间段内的特定主题新闻进行内容分析时，可以使用 NewsIndexer 批量导入该时间段的 URL 列表，通过配置解析规则自动提取标题、发布时间和正文，最终导出结构化数据集供后续自然语言处理或统计分析使用。

垂直领域内容聚合平台构建：运营科技、财经或体育等垂直领域资讯站点的团队，可以使用 NewsIndexer 作为后端数据采集引擎，定期抓取多个来源的最新文章，并将标准化后的数据推送到消息队列或直接写入数据库，为前端应用提供统一的内容源。

搜索引擎索引数据补充：搜索引擎优化团队或搜索引擎自身运维人员，可以利用 NewsIndexer 对特定站点的历史页面进行深度抓取与内容提取，将获取的纯文本内容作为站内搜索或外部搜索索引的补充数据源，提升搜索召回率。

内容管理系统批量迁移辅助：在进行网站改版或内容管理系统迁移时，运维人员可以使用 NewsIndexer 从旧站点的新闻存档页面中批量提取关键字段，并映射到新系统的数据结构中，降低人工整理成本并减少数据遗漏风险。

## 快速开始

以下命令演示了从克隆代码到运行首个抓取任务的标准流程。请确保系统已安装 Git 与 Go 1.21 及以上版本。

```bash
git clone https://github.com/example/newsindexer.git
cd newsindexer
go mod download
go build -o newsindexer ./cmd/newsindexer
./newsindexer crawl --input urls.txt --output data.jsonl --config configs/example.yaml
```

上述命令中，`urls.txt` 为每行一个 URL 的文本文件，`configs/example.yaml` 为解析规则配置文件，`data.jsonl` 为输出的结构化数据文件。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Go | 1.21 或更高 | 核心编程语言与编译环境 |
| Git | 2.25 或更高 | 用于克隆代码仓库与版本管理 |
| SQLite | 3.35 或更高 | 内置数据库引擎，用于存储抓取状态与内容指纹 |
| Make | 3.82 或更高 | 可选，用于自动化构建与测试任务 |
| gcc | 7.5 或更高 | 用于支持 SQLite 驱动编译的 C 编译器 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何安装、配置、运行抓取任务以及导出数据 |
| 规则配置 | docs/config_spec.md | 如何编写 YAML 解析规则文件，包括选择器语法与字段映射 |
| API 参考 | docs/api_reference.md | 提供的 HTTP 管理接口定义，包括任务提交与状态查询 |
| 开发指南 | docs/development.md | 项目代码结构、贡献流程、测试规范与调试方法 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/65638.htm
- http://m.blog.ghtkgg.cn/nnews/12832.htm
- http://m.blog.ghtkgg.cn/nnews/8029.htm
- http://m.blog.ghtkgg.cn/nnews/6673537.htm
- http://m.blog.ghtkgg.cn/nnews/78746.htm
- http://m.blog.ghtkgg.cn/nnews/0343967.htm
- http://m.blog.ghtkgg.cn/nnews/57745.htm
- http://m.blog.ghtkgg.cn/nnews/05323.htm
- http://m.blog.ghtkgg.cn/nnews/1638.htm
- http://m.blog.ghtkgg.cn/nnews/8603169.htm
- http://m.blog.ghtkgg.cn/nnews/72811.htm
- http://m.blog.ghtkgg.cn/nnews/1701.htm
- http://m.blog.ghtkgg.cn/nnews/3229.htm
- http://m.blog.ghtkgg.cn/nnews/513500.htm
- http://m.blog.ghtkgg.cn/nnews/92991.htm
- http://m.blog.ghtkgg.cn/nnews/66541.htm
- http://m.blog.ghtkgg.cn/nnews/850993.htm
- http://m.blog.ghtkgg.cn/nnews/9828.htm
- http://m.blog.ghtkgg.cn/nnews/2545363.htm
- http://m.blog.ghtkgg.cn/nnews/8375589.htm
- http://m.blog.ghtkgg.cn/nnews/808750.htm
- http://m.blog.ghtkgg.cn/nnews/7878.htm
- http://m.blog.ghtkgg.cn/nnews/67528.htm
- http://m.blog.ghtkgg.cn/nnews/94453.htm
- http://m.blog.ghtkgg.cn/nnews/5634439.htm
- http://m.blog.ghtkgg.cn/nnews/5329.htm
- http://m.blog.ghtkgg.cn/nnews/5629632.htm
- http://m.blog.ghtkgg.cn/nnews/751502.htm
- http://m.blog.ghtkgg.cn/nnews/9466298.htm
- http://m.blog.ghtkgg.cn/nnews/936829.htm
- http://m.blog.ghtkgg.cn/nnews/35625.htm
- http://m.blog.ghtkgg.cn/nnews/1970.htm
- http://m.blog.ghtkgg.cn/nnews/84651.htm
- http://m.blog.ghtkgg.cn/nnews/7257037.htm
- http://m.blog.ghtkgg.cn/nnews/0989.htm
- http://m.blog.ghtkgg.cn/nnews/8572104.htm
- http://m.blog.ghtkgg.cn/nnews/5163.htm
- http://m.blog.ghtkgg.cn/nnews/656955.htm
- http://m.blog.ghtkgg.cn/nnews/4060.htm
- http://m.blog.ghtkgg.cn/nnews/2797117.htm
- http://m.blog.ghtkgg.cn/nnews/15288.htm
- http://m.blog.ghtkgg.cn/nnews/8541.htm
- http://m.blog.ghtkgg.cn/nnews/292628.htm
- http://m.blog.ghtkgg.cn/nnews/416608.htm
- http://m.blog.ghtkgg.cn/nnews/1795796.htm
- http://m.blog.ghtkgg.cn/nnews/797819.htm
- http://m.blog.ghtkgg.cn/nnews/8709.htm
- http://m.blog.ghtkgg.cn/nnews/40984.htm
- http://m.blog.ghtkgg.cn/nnews/157144.htm
- http://m.blog.ghtkgg.cn/nnews/260524.htm
- http://m.blog.ghtkgg.cn/nnews/214625.htm
- http://m.blog.ghtkgg.cn/nnews/8171.htm
- http://m.blog.ghtkgg.cn/nnews/0164317.htm
- http://m.blog.ghtkgg.cn/nnews/7836084.htm
- http://m.blog.ghtkgg.cn/nnews/5752874.htm
- http://m.blog.ghtkgg.cn/nnews/146332.htm
- http://m.blog.ghtkgg.cn/nnews/512927.htm
- http://m.blog.ghtkgg.cn/nnews/687508.htm
- http://m.blog.ghtkgg.cn/nnews/283170.htm
- http://m.blog.ghtkgg.cn/nnews/6307.htm
- http://m.blog.ghtkgg.cn/nnews/2982701.htm
- http://m.blog.ghtkgg.cn/nnews/153938.htm
- http://m.blog.ghtkgg.cn/nnews/1603.htm
- http://m.blog.ghtkgg.cn/nnews/0232.htm
- http://m.blog.ghtkgg.cn/nnews/2440.htm
- http://m.blog.ghtkgg.cn/nnews/24225.htm
- http://m.blog.ghtkgg.cn/nnews/6665.htm
- http://m.blog.ghtkgg.cn/nnews/4568717.htm
- http://m.blog.ghtkgg.cn/nnews/9202.htm
- http://m.blog.ghtkgg.cn/nnews/6766.htm
- http://m.blog.ghtkgg.cn/nnews/51642.htm
- http://m.blog.ghtkgg.cn/nnews/7231.htm
- http://m.blog.ghtkgg.cn/nnews/059353.htm
- http://m.blog.ghtkgg.cn/nnews/45868.htm
- http://m.blog.ghtkgg.cn/nnews/8599607.htm
- http://m.blog.ghtkgg.cn/nnews/19021.htm
- http://m.blog.ghtkgg.cn/nnews/775071.htm
- http://m.blog.ghtkgg.cn/nnews/4923845.htm
- http://m.blog.ghtkgg.cn/nnews/6907.htm
- http://m.blog.ghtkgg.cn/nnews/79678.htm
- http://m.blog.ghtkgg.cn/nnews/391515.htm
- http://m.blog.ghtkgg.cn/nnews/6445195.htm
- http://m.blog.ghtkgg.cn/nnews/495232.htm
- http://m.blog.ghtkgg.cn/nnews/3990906.htm
- http://m.blog.ghtkgg.cn/nnews/0056.htm
- http://m.blog.ghtkgg.cn/nnews/96072.htm
- http://m.blog.ghtkgg.cn/nnews/535279.htm
- http://m.blog.ghtkgg.cn/nnews/3150088.htm
- http://m.blog.ghtkgg.cn/nnews/08792.htm
- http://m.blog.ghtkgg.cn/nnews/1169.htm
- http://m.blog.ghtkgg.cn/nnews/061018.htm
- http://m.blog.ghtkgg.cn/nnews/93166.htm
- http://m.blog.ghtkgg.cn/nnews/64459.htm
- http://m.blog.ghtkgg.cn/nnews/8242.htm
- http://m.blog.ghtkgg.cn/nnews/6682778.htm
- http://m.blog.ghtkgg.cn/nnews/679698.htm
- http://m.blog.ghtkgg.cn/nnews/302945.htm
- http://m.blog.ghtkgg.cn/nnews/1242.htm
- http://m.blog.ghtkgg.cn/nnews/3825937.htm
- http://m.blog.ghtkgg.cn/nnews/4625942.htm
- http://m.blog.ghtkgg.cn/nnews/603979.htm
- http://m.blog.ghtkgg.cn/nnews/8950427.htm
- http://m.blog.ghtkgg.cn/nnews/2753.htm
- http://m.blog.ghtkgg.cn/nnews/9440717.htm
- http://m.blog.ghtkgg.cn/nnews/191806.htm
- http://m.blog.ghtkgg.cn/nnews/1873023.htm
- http://m.blog.ghtkgg.cn/nnews/4471936.htm
- http://m.blog.ghtkgg.cn/nnews/547026.htm
- http://m.blog.ghtkgg.cn/nnews/5575.htm
- http://m.blog.ghtkgg.cn/nnews/446528.htm
- http://m.blog.ghtkgg.cn/nnews/6445185.htm
- http://m.blog.ghtkgg.cn/nnews/8659442.htm
- http://m.blog.ghtkgg.cn/nnews/74530.htm
- http://m.blog.ghtkgg.cn/nnews/087557.htm
- http://m.blog.ghtkgg.cn/nnews/0837.htm
- http://m.blog.ghtkgg.cn/nnews/3084.htm
- http://m.blog.ghtkgg.cn/nnews/0798.htm
- http://m.blog.ghtkgg.cn/nnews/2940.htm
- http://m.blog.ghtkgg.cn/nnews/0164733.htm
- http://m.blog.ghtkgg.cn/nnews/4583075.htm
- http://m.blog.ghtkgg.cn/nnews/50285.htm
- http://m.blog.ghtkgg.cn/nnews/7868811.htm
- http://m.blog.ghtkgg.cn/nnews/845767.htm
- http://m.blog.ghtkgg.cn/nnews/725461.htm
- http://m.blog.ghtkgg.cn/nnews/6820.htm
- http://m.blog.ghtkgg.cn/nnews/620466.htm
- http://m.blog.ghtkgg.cn/nnews/0851.htm
- http://m.blog.ghtkgg.cn/nnews/350054.htm
- http://m.blog.ghtkgg.cn/nnews/73046.htm
- http://m.blog.ghtkgg.cn/nnews/6424.htm
- http://m.blog.ghtkgg.cn/nnews/7994524.htm
- http://m.blog.ghtkgg.cn/nnews/21023.htm
- http://m.blog.ghtkgg.cn/nnews/053212.htm
- http://m.blog.ghtkgg.cn/nnews/0819.htm
- http://m.blog.ghtkgg.cn/nnews/53408.htm
- http://m.blog.ghtkgg.cn/nnews/502504.htm
- http://m.blog.ghtkgg.cn/nnews/4002362.htm
- http://m.blog.ghtkgg.cn/nnews/78497.htm
- http://m.blog.ghtkgg.cn/nnews/12315.htm
- http://m.blog.ghtkgg.cn/nnews/8127.htm
- http://m.blog.ghtkgg.cn/nnews/5708001.htm
- http://m.blog.ghtkgg.cn/nnews/1529324.htm
- http://m.blog.ghtkgg.cn/nnews/7422.htm
- http://m.blog.ghtkgg.cn/nnews/06907.htm
- http://m.blog.ghtkgg.cn/nnews/8687.htm
- http://m.blog.ghtkgg.cn/nnews/33464.htm
- http://m.blog.ghtkgg.cn/nnews/51759.htm
- http://m.blog.ghtkgg.cn/nnews/11407.htm
- http://m.blog.ghtkgg.cn/nnews/278233.htm
- http://m.blog.ghtkgg.cn/nnews/9913.htm
- http://m.blog.ghtkgg.cn/nnews/2454117.htm
- http://m.blog.ghtkgg.cn/nnews/2698091.htm
- http://m.blog.ghtkgg.cn/nnews/79649.htm
- http://m.blog.ghtkgg.cn/nnews/02562.htm
- http://m.blog.ghtkgg.cn/nnews/68542.htm
- http://m.blog.ghtkgg.cn/nnews/18900.htm
- http://m.blog.ghtkgg.cn/nnews/25554.htm
- http://m.blog.ghtkgg.cn/nnews/87028.htm
- http://m.blog.ghtkgg.cn/nnews/11352.htm
- http://m.blog.ghtkgg.cn/nnews/8169.htm
- http://m.blog.ghtkgg.cn/nnews/084846.htm
- http://m.blog.ghtkgg.cn/nnews/4190.htm
- http://m.blog.ghtkgg.cn/nnews/710377.htm
- http://m.blog.ghtkgg.cn/nnews/8710.htm
- http://m.blog.ghtkgg.cn/nnews/32654.htm
- http://m.blog.ghtkgg.cn/nnews/50324.htm
- http://m.blog.ghtkgg.cn/nnews/99040.htm
- http://m.blog.ghtkgg.cn/nnews/073082.htm
- http://m.blog.ghtkgg.cn/nnews/39531.htm
- http://m.blog.ghtkgg.cn/nnews/18609.htm
- http://m.blog.ghtkgg.cn/nnews/9151770.htm
- http://m.blog.ghtkgg.cn/nnews/0980296.htm
- http://m.blog.ghtkgg.cn/nnews/81951.htm
- http://m.blog.ghtkgg.cn/nnews/4001.htm
- http://m.blog.ghtkgg.cn/nnews/63647.htm
- http://m.blog.ghtkgg.cn/nnews/0546.htm
- http://m.blog.ghtkgg.cn/nnews/0363.htm
- http://m.blog.ghtkgg.cn/nnews/60807.htm
- http://m.blog.ghtkgg.cn/nnews/385952.htm
- http://m.blog.ghtkgg.cn/nnews/8536310.htm
- http://m.blog.ghtkgg.cn/nnews/6285124.htm
- http://m.blog.ghtkgg.cn/nnews/34388.htm
- http://m.blog.ghtkgg.cn/nnews/881120.htm
- http://m.blog.ghtkgg.cn/nnews/957793.htm
- http://m.blog.ghtkgg.cn/nnews/8859.htm
- http://m.blog.ghtkgg.cn/nnews/8351824.htm
- http://m.blog.ghtkgg.cn/nnews/99474.htm
- http://m.blog.ghtkgg.cn/nnews/60717.htm
- http://m.blog.ghtkgg.cn/nnews/7427134.htm
- http://m.blog.ghtkgg.cn/nnews/3218163.htm
- http://m.blog.ghtkgg.cn/nnews/4504177.htm
- http://m.blog.ghtkgg.cn/nnews/1362.htm
- http://m.blog.ghtkgg.cn/nnews/6251650.htm
- http://m.blog.ghtkgg.cn/nnews/9409890.htm
- http://m.blog.ghtkgg.cn/nnews/5766547.htm
- http://m.blog.ghtkgg.cn/nnews/94645.htm
- http://m.blog.ghtkgg.cn/nnews/792319.htm
- http://m.blog.ghtkgg.cn/nnews/908355.htm
- http://m.blog.ghtkgg.cn/nnews/717387.htm
- http://m.blog.ghtkgg.cn/nnews/0209937.htm
- http://m.blog.ghtkgg.cn/nnews/4889662.htm
- http://m.blog.ghtkgg.cn/nnews/9897445.htm
- http://m.blog.ghtkgg.cn/nnews/463055.htm
- http://m.blog.ghtkgg.cn/nnews/92906.htm
- http://m.blog.ghtkgg.cn/nnews/47933.htm
- http://m.blog.ghtkgg.cn/nnews/68620.htm
- http://m.blog.ghtkgg.cn/nnews/46896.htm
- http://m.blog.ghtkgg.cn/nnews/94866.htm
- http://m.blog.ghtkgg.cn/nnews/7659357.htm
- http://m.blog.ghtkgg.cn/nnews/71956.htm
- http://m.blog.ghtkgg.cn/nnews/37348.htm
- http://m.blog.ghtkgg.cn/nnews/700751.htm
- http://m.blog.ghtkgg.cn/nnews/117617.htm
- http://m.blog.ghtkgg.cn/nnews/0509674.htm
- http://m.blog.ghtkgg.cn/nnews/04242.htm
- http://m.blog.ghtkgg.cn/nnews/54218.htm
- http://m.blog.ghtkgg.cn/nnews/70085.htm
- http://m.blog.ghtkgg.cn/nnews/62668.htm
- http://m.blog.ghtkgg.cn/nnews/4992512.htm
- http://m.blog.ghtkgg.cn/nnews/122201.htm
- http://m.blog.ghtkgg.cn/nnews/0100760.htm
- http://m.blog.ghtkgg.cn/nnews/5292673.htm
- http://m.blog.ghtkgg.cn/nnews/92764.htm
- http://m.blog.ghtkgg.cn/nnews/25406.htm
- http://m.blog.ghtkgg.cn/nnews/05531.htm
- http://m.blog.ghtkgg.cn/nnews/5768.htm
- http://m.blog.ghtkgg.cn/nnews/14022.htm
- http://m.blog.ghtkgg.cn/nnews/36119.htm
- http://m.blog.ghtkgg.cn/nnews/5599.htm
- http://m.blog.ghtkgg.cn/nnews/066310.htm
- http://m.blog.ghtkgg.cn/nnews/8034.htm
- http://m.blog.ghtkgg.cn/nnews/4124186.htm
- http://m.blog.ghtkgg.cn/nnews/7359468.htm
- http://m.blog.ghtkgg.cn/nnews/0280.htm
- http://m.blog.ghtkgg.cn/nnews/267968.htm
- http://m.blog.ghtkgg.cn/nnews/57449.htm
- http://m.blog.ghtkgg.cn/nnews/824123.htm
- http://m.blog.ghtkgg.cn/nnews/3973.htm
- http://m.blog.ghtkgg.cn/nnews/4999725.htm
- http://m.blog.ghtkgg.cn/nnews/518740.htm
- http://m.blog.ghtkgg.cn/nnews/24195.htm
- http://m.blog.ghtkgg.cn/nnews/84407.htm
- http://m.blog.ghtkgg.cn/nnews/8499.htm
- http://m.blog.ghtkgg.cn/nnews/2083.htm
- http://m.blog.ghtkgg.cn/nnews/7654.htm
- http://m.blog.ghtkgg.cn/nnews/42115.htm
- http://m.blog.ghtkgg.cn/nnews/53939.htm
- http://m.blog.ghtkgg.cn/nnews/0710.htm
- http://m.blog.ghtkgg.cn/nnews/06454.htm
- http://m.blog.ghtkgg.cn/nnews/7481.htm
- http://m.blog.ghtkgg.cn/nnews/296007.htm
- http://m.blog.ghtkgg.cn/nnews/72053.htm
- http://m.blog.ghtkgg.cn/nnews/4022.htm
- http://m.blog.ghtkgg.cn/nnews/6724.htm
- http://m.blog.ghtkgg.cn/nnews/1821458.htm
- http://m.blog.ghtkgg.cn/nnews/2658590.htm
- http://m.blog.ghtkgg.cn/nnews/94038.htm
- http://m.blog.ghtkgg.cn/nnews/1812528.htm
- http://m.blog.ghtkgg.cn/nnews/11459.htm
- http://m.blog.ghtkgg.cn/nnews/6903.htm
- http://m.blog.ghtkgg.cn/nnews/6800512.htm
- http://m.blog.ghtkgg.cn/nnews/948035.htm
- http://m.blog.ghtkgg.cn/nnews/2815783.htm
- http://m.blog.ghtkgg.cn/nnews/199529.htm
- http://m.blog.ghtkgg.cn/nnews/779869.htm
- http://m.blog.ghtkgg.cn/nnews/47544.htm
- http://m.blog.ghtkgg.cn/nnews/53431.htm
- http://m.blog.ghtkgg.cn/nnews/59037.htm
- http://m.blog.ghtkgg.cn/nnews/08984.htm
- http://m.blog.ghtkgg.cn/nnews/379902.htm
- http://m.blog.ghtkgg.cn/nnews/7426182.htm
- http://m.blog.ghtkgg.cn/nnews/9990006.htm
- http://m.blog.ghtkgg.cn/nnews/2137174.htm
- http://m.blog.ghtkgg.cn/nnews/56483.htm
- http://m.blog.ghtkgg.cn/nnews/74918.htm
- http://m.blog.ghtkgg.cn/nnews/71721.htm
- http://m.blog.ghtkgg.cn/nnews/2232763.htm
- http://m.blog.ghtkgg.cn/nnews/74752.htm
- http://m.blog.ghtkgg.cn/nnews/87280.htm
- http://m.blog.ghtkgg.cn/nnews/5430035.htm
- http://m.blog.ghtkgg.cn/nnews/583221.htm
- http://m.blog.ghtkgg.cn/nnews/6787000.htm
- http://m.blog.ghtkgg.cn/nnews/2504.htm
- http://m.blog.ghtkgg.cn/nnews/25544.htm
- http://m.blog.ghtkgg.cn/nnews/0375.htm
- http://m.blog.ghtkgg.cn/nnews/30351.htm
- http://m.blog.ghtkgg.cn/nnews/913040.htm
- http://m.blog.ghtkgg.cn/nnews/53057.htm
- http://m.blog.ghtkgg.cn/nnews/2171.htm
- http://m.blog.ghtkgg.cn/nnews/347713.htm
- http://m.blog.ghtkgg.cn/nnews/91157.htm
- http://m.blog.ghtkgg.cn/nnews/1206680.htm
- http://m.blog.ghtkgg.cn/nnews/6331578.htm
- http://m.blog.ghtkgg.cn/nnews/189209.htm
- http://m.blog.ghtkgg.cn/nnews/1027088.htm
- http://m.blog.ghtkgg.cn/nnews/0675.htm
- http://m.blog.ghtkgg.cn/nnews/1932206.htm
- http://m.blog.ghtkgg.cn/nnews/363654.htm
- http://m.blog.ghtkgg.cn/nnews/7191.htm
- http://m.blog.ghtkgg.cn/nnews/028168.htm

## 项目结构

```
newsindexer/
├── cmd/
│   └── newsindexer/                # 主程序入口，包含命令行参数解析与命令路由
│       └── main.go                 # 初始化日志、加载配置、启动任务调度
├── internal/
│   ├── crawler/                    # 抓取器核心模块，负责 HTTP 请求与重试策略
│   │   ├── client.go               # 封装 http.Client，支持代理与超时设置
│   │   └── dispatcher.go           # 任务分发器，管理并发工作池与队列
│   ├── parser/                     # 解析器模块，实现基于配置的字段提取
│   │   ├── engine.go               # 解析引擎主逻辑，调用选择器与后处理函数
│   │   └── rules.go                # 规则加载与验证，支持 YAML 文件读取
│   ├── storage/                    # 存储模块，负责 SQLite 数据库操作与状态管理
│   │   ├── database.go             # 数据库连接初始化与迁移
│   │   └── fingerprint.go          # 内容指纹计算与变更检测
│   └── exporter/                   # 导出模块，支持多种输出格式序列化
│       ├── jsonl.go                # JSON Lines 格式导出器
│       └── csv.go                  # CSV 格式导出器，支持自定义分隔符
├── pkg/
│   └── logger/                     # 公共日志包，基于 logrus 封装
│       └── logger.go               # 日志级别、输出格式与挂钩配置
├── configs/                        # 配置文件目录，存放 YAML 解析规则与全局设置
│   ├── example.yaml                # 示例规则文件，展示字段映射与选择器写法
│   └── sites/                      # 按站点分拆的规则子目录
│       └── default.yaml            # 默认回退规则
├── docs/                           # 文档目录，包含用户手册与 API 参考
│   ├── user_guide.md               # 完整使用指南，包含安装、配置与故障排查
│   └── config_spec.md              # 规则配置规范，详细说明每个字段的含义与合法取值
├── scripts/                        # 辅助脚本，用于测试数据生成与性能基准测试
│   ├── bench.sh                    # 运行基准测试的 shell 脚本
│   └── sample_urls.txt             # 示例 URL 列表，用于快速验证功能
├── testdata/                       # 测试数据目录，包含模拟的 HTML 响应体
│   └── mock/                       # 模拟站点响应，用于单元测试解析规则
├── go.mod                          # Go 模块依赖定义文件
├── go.sum                          # 依赖校验和文件
├── Makefile                        # 构建自动化脚本，支持 build、test、clean 等目标
└── README.md                       # 项目自述文档
```

## 贡献指南

1. 阅读项目开发文档 docs/development.md 了解代码风格、测试要求与提交规范，确保本地环境已安装 golangci-lint 静态检查工具。

2. 在 GitHub 仓库的 Issue 列表中查找标记为 good-first-issue 或 help-wanted 的未解决问题，或在讨论区提出新功能建议并等待维护者确认。

3. Fork 代码仓库至个人账户，创建以 feature/ 或 fix/ 为前缀的分支，在本地完成功能开发或缺陷修复，并确保所有现有单元测试与新编写的测试用例均能通过。

4. 提交代码前运行 make lint 与 make test 进行本地质量检查，修复所有报告的错误与警告，确保代码覆盖率不下降。

5. 发起 Pull Request 到主仓库的 main 分支，在描述中清晰说明改动内容、关联的 Issue 编号以及测试覆盖情况，等待维护者进行代码审查。

## 常见问题

问：抓取任务执行过程中出现大量 HTTP 429 状态码，应如何调整？

答：该状态码表示目标站点实施了请求频率限制。建议降低配置文件中的并发工作线程数（worker-count 参数），同时增大请求间隔延迟（delay-seconds 参数）。若目标站点提供标准的 Retry-After 响应头，项目会自动识别并等待相应时长后重试。此外，可以配置代理池轮换出口 IP 以分散请求来源。

问：解析规则文件更新后，是否需要重新索引已有的历史数据？

答：不需要。解析规则仅影响新抓取页面的字段提取方式。若需要将新规则应用于已存储的原始 HTML 内容，可以启用 force-reparse 命令行标志，该模式会跳过网络请求，直接对数据库中保存的原始响应体重新执行解析逻辑并更新结构化字段，大幅节省网络资源消耗。

问：项目是否支持分布式部署以应对更大规模的抓取需求？

答：当前版本为单机架构，但数据库层使用 SQLite 支持读写锁，不适用于网络共享存储。对于大规模分布式场景，建议将任务队列与状态存储迁移至 Redis 或 PostgreSQL，并自行实现调度器协调多个实例。项目内部的核心抓取与解析模块设计为无状态，可被轻松封装为独立服务。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
