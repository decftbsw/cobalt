# NewsLink Archive Aggregator

NewsLink Archive Aggregator 是一个面向技术资讯聚合与历史新闻条目归档的开源工具集，专门用于批量采集、结构化存储和快速检索来自移动端新闻源的内容条目。该项目定位于需要长期维护新闻链接库的研究人员、数据分析师以及内容运营团队，提供从原始链接抓取到元数据清洗、索引构建的完整工作流。

该项目不提供新闻内容的渲染或全文展示，而是聚焦于链接层面的规范化管理与可用性监控。通过可复用的采集调度模块和持久化存储方案，用户能够构建自定义的新闻条目知识库，并基于条目 ID、发布时间、来源域名等多维属性进行过滤与统计。

## 功能概览

批量链接采集调度：支持基于输入文件或标准输入的多线程并发请求，自动处理 HTTP 重定向与超时重试，并提供请求失败日志记录。

链接规范化与去重：内置 URL 标准化处理器，自动移除冗余查询参数、统一协议格式（用户可配置是否强制 HTTPS），并基于 URL 完整字符串进行布隆过滤器去重。

元数据抽取与清洗：从目标 HTML 页面中抽取标题、发布时间、正文摘要前 200 字符，并利用正则表达式库提取页面内的其他外链，生成结构化 JSON 记录。

增量归档存储：采用按日期分区的文件系统存储方案，每日生成一个独立的 JSON Lines 文件，支持追加写入与按日期范围读取。

离线索引构建：基于归档文件构建倒排索引，支持对标题和摘要字段进行中文分词检索，索引文件以 LevelDB 格式持久化。

健康检查与失效检测：定期对已归档链接发起 HEAD 请求，检测 HTTP 状态码变化，生成链接有效性报告（CSV 格式），标记 4xx/5xx 响应。

命令行交互界面：提供统一的 CLI 入口，包含 `collect`、`clean`、`index`、`check`、`export` 五个子命令，支持通过环境变量或配置文件覆盖默认参数。

## 应用场景

历史新闻条目回溯分析：研究人员可借助该工具批量采集指定日期范围内的新闻链接，抽取元数据后用于趋势分析或事件追踪。例如，针对某一突发事件，用户可快速归档数百条相关报道链接，并按时间线排序。

新闻网站链接结构探查：内容运营团队可通过链接抽取功能，分析竞品网站的內链布局与栏目更新频率，辅助自身内容策略制定。工具提供的出链统计报告可直接输出各栏目的链接数量占比。

长期链接可用性监控：对于依赖外部新闻引用作为证据材料的法律或政务场景，定期执行链接检查功能可及时发现内容下线或域名过期情况，避免引用失效风险。

多源数据融合前的清洗预处理：在将新闻数据导入大型数据仓库或 BI 系统之前，使用本工具的规范化与去重模块可有效降低数据噪声，减少后续 ETL 流程的异常处理成本。

## 快速开始

以下命令演示了从克隆仓库到执行首次采集任务的完整流程。

```bash
git clone https://github.com/example/newslink-archive.git
cd newslink-archive
pip install -r requirements.txt
cp config.example.yaml config.yaml
python -m newslink.cli collect --input urls.txt --output ./data --concurrency 5
```

其中 `urls.txt` 为每行一个 URL 的文本文件，采集结果将以 JSON Lines 格式写入 `./data/YYYY-MM-DD.jsonl`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行时，类型注解依赖 3.9+ 的特性 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于链接采集与健康检查 |
| leveldb | 0.201 及以上 | 索引存储后端，需安装系统级 LevelDB 库 |
| jieba | 0.42.1 及以上 | 中文分词器，用于索引构建时的分词处理 |
| pyyaml | 6.0 及以上 | 配置文件解析，支持 YAML 1.2 语法 |
| pytest | 7.0 及以上 | 单元测试框架，仅开发环境需要 |
| flake8 | 5.0 及以上 | 代码风格检查，仅开发环境需要 |

系统级依赖：Linux 或 macOS 操作系统，建议使用 x86_64 架构；Windows 用户可通过 WSL2 运行。需要安装 gcc 和 make 以编译 LevelDB 的 Python 绑定。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user/quickstart.md | 如何快速开始采集任务？配置文件各字段的含义是什么？ |
| 用户手册 | docs/user/checker.md | 如何设置定期链接检查？检查报告如何解读？ |
| 开发者指南 | docs/dev/architecture.md | 项目的模块划分与数据流向是怎样的？如何扩展一个新的采集源？ |
| 开发者指南 | docs/dev/api_reference.md | 核心类与函数的参数说明及调用示例，面向二次开发者 |
| 运维手册 | docs/ops/deployment.md | 如何部署为长期运行的定时任务？日志轮转如何配置？ |
| 运维手册 | docs/ops/troubleshooting.md | 常见报错信息及对应的排查步骤，例如 LevelDB 锁冲突或请求超时 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/22591.htm
- http://m.3g.oexnr.cn/nnews/1255.htm
- http://m.3g.oexnr.cn/nnews/852858.htm
- http://m.3g.oexnr.cn/nnews/88767.htm
- http://m.3g.oexnr.cn/nnews/0448402.htm
- http://m.3g.oexnr.cn/nnews/738613.htm
- http://m.3g.oexnr.cn/nnews/2109046.htm
- http://m.3g.oexnr.cn/nnews/26580.htm
- http://m.3g.oexnr.cn/nnews/2686.htm
- http://m.3g.oexnr.cn/nnews/90122.htm
- http://m.3g.oexnr.cn/nnews/4936.htm
- http://m.3g.oexnr.cn/nnews/6238553.htm
- http://m.3g.oexnr.cn/nnews/2704965.htm
- http://m.3g.oexnr.cn/nnews/6294449.htm
- http://m.3g.oexnr.cn/nnews/4104121.htm
- http://m.3g.oexnr.cn/nnews/041803.htm
- http://m.3g.oexnr.cn/nnews/804959.htm
- http://m.3g.oexnr.cn/nnews/40331.htm
- http://m.3g.oexnr.cn/nnews/487161.htm
- http://m.3g.oexnr.cn/nnews/24169.htm
- http://m.3g.oexnr.cn/nnews/41001.htm
- http://m.3g.oexnr.cn/nnews/24618.htm
- http://m.3g.oexnr.cn/nnews/4923687.htm
- http://m.3g.oexnr.cn/nnews/94558.htm
- http://m.3g.oexnr.cn/nnews/3371.htm
- http://m.3g.oexnr.cn/nnews/37165.htm
- http://m.3g.oexnr.cn/nnews/3260.htm
- http://m.3g.oexnr.cn/nnews/7560.htm
- http://m.3g.oexnr.cn/nnews/050939.htm
- http://m.3g.oexnr.cn/nnews/88976.htm
- http://m.3g.oexnr.cn/nnews/06310.htm
- http://m.3g.oexnr.cn/nnews/35218.htm
- http://m.3g.oexnr.cn/nnews/30539.htm
- http://m.3g.oexnr.cn/nnews/4523.htm
- http://m.3g.oexnr.cn/nnews/663573.htm
- http://m.3g.oexnr.cn/nnews/1287.htm
- http://m.3g.oexnr.cn/nnews/864231.htm
- http://m.3g.oexnr.cn/nnews/4092.htm
- http://m.3g.oexnr.cn/nnews/52723.htm
- http://m.3g.oexnr.cn/nnews/77518.htm
- http://m.3g.oexnr.cn/nnews/88260.htm
- http://m.3g.oexnr.cn/nnews/37191.htm
- http://m.3g.oexnr.cn/nnews/10897.htm
- http://m.3g.oexnr.cn/nnews/38249.htm
- http://m.3g.oexnr.cn/nnews/7423127.htm
- http://m.3g.oexnr.cn/nnews/0597.htm
- http://m.3g.oexnr.cn/nnews/4798.htm
- http://m.3g.oexnr.cn/nnews/0203.htm
- http://m.3g.oexnr.cn/nnews/4465531.htm
- http://m.3g.oexnr.cn/nnews/84236.htm
- http://m.3g.oexnr.cn/nnews/2762295.htm
- http://m.3g.oexnr.cn/nnews/54703.htm
- http://m.3g.oexnr.cn/nnews/5072007.htm
- http://m.3g.oexnr.cn/nnews/0480648.htm
- http://m.3g.oexnr.cn/nnews/8962907.htm
- http://m.3g.oexnr.cn/nnews/6140.htm
- http://m.3g.oexnr.cn/nnews/578097.htm
- http://m.3g.oexnr.cn/nnews/3412.htm
- http://m.3g.oexnr.cn/nnews/1078.htm
- http://m.3g.oexnr.cn/nnews/69350.htm
- http://m.3g.oexnr.cn/nnews/266080.htm
- http://m.3g.oexnr.cn/nnews/6667219.htm
- http://m.3g.oexnr.cn/nnews/0742710.htm
- http://m.3g.oexnr.cn/nnews/91852.htm
- http://m.3g.oexnr.cn/nnews/8426.htm
- http://m.3g.oexnr.cn/nnews/330670.htm
- http://m.3g.oexnr.cn/nnews/52784.htm
- http://m.3g.oexnr.cn/nnews/62634.htm
- http://m.3g.oexnr.cn/nnews/10269.htm
- http://m.3g.oexnr.cn/nnews/0838172.htm
- http://m.3g.oexnr.cn/nnews/29995.htm
- http://m.3g.oexnr.cn/nnews/984535.htm
- http://m.3g.oexnr.cn/nnews/3984954.htm
- http://m.3g.oexnr.cn/nnews/3049.htm
- http://m.3g.oexnr.cn/nnews/8520674.htm
- http://m.3g.oexnr.cn/nnews/19397.htm
- http://m.3g.oexnr.cn/nnews/0805.htm
- http://m.3g.oexnr.cn/nnews/4969010.htm
- http://m.3g.oexnr.cn/nnews/276162.htm
- http://m.3g.oexnr.cn/nnews/280930.htm
- http://m.3g.oexnr.cn/nnews/0058202.htm
- http://m.3g.oexnr.cn/nnews/927850.htm
- http://m.3g.oexnr.cn/nnews/555322.htm
- http://m.3g.oexnr.cn/nnews/339583.htm
- http://m.3g.oexnr.cn/nnews/8753.htm
- http://m.3g.oexnr.cn/nnews/2952.htm
- http://m.3g.oexnr.cn/nnews/2030.htm
- http://m.3g.oexnr.cn/nnews/35426.htm
- http://m.3g.oexnr.cn/nnews/3428908.htm
- http://m.3g.oexnr.cn/nnews/620036.htm
- http://m.3g.oexnr.cn/nnews/676100.htm
- http://m.3g.oexnr.cn/nnews/3703.htm
- http://m.3g.oexnr.cn/nnews/13729.htm
- http://m.3g.oexnr.cn/nnews/6844.htm
- http://m.3g.oexnr.cn/nnews/72148.htm
- http://m.3g.oexnr.cn/nnews/3589097.htm
- http://m.3g.oexnr.cn/nnews/432527.htm
- http://m.3g.oexnr.cn/nnews/6750781.htm
- http://m.3g.oexnr.cn/nnews/2607978.htm
- http://m.3g.oexnr.cn/nnews/05565.htm
- http://m.3g.oexnr.cn/nnews/0561516.htm
- http://m.3g.oexnr.cn/nnews/0053386.htm
- http://m.3g.oexnr.cn/nnews/58520.htm
- http://m.3g.oexnr.cn/nnews/83640.htm
- http://m.3g.oexnr.cn/nnews/7940.htm
- http://m.3g.oexnr.cn/nnews/276169.htm
- http://m.3g.oexnr.cn/nnews/8507662.htm
- http://m.3g.oexnr.cn/nnews/34806.htm
- http://m.3g.oexnr.cn/nnews/8960142.htm
- http://m.3g.oexnr.cn/nnews/915764.htm
- http://m.3g.oexnr.cn/nnews/35608.htm
- http://m.3g.oexnr.cn/nnews/9848.htm
- http://m.3g.oexnr.cn/nnews/903897.htm
- http://m.3g.oexnr.cn/nnews/3767233.htm
- http://m.3g.oexnr.cn/nnews/9529.htm
- http://m.3g.oexnr.cn/nnews/1982299.htm
- http://m.3g.oexnr.cn/nnews/5221731.htm
- http://m.3g.oexnr.cn/nnews/436783.htm
- http://m.3g.oexnr.cn/nnews/06913.htm
- http://m.3g.oexnr.cn/nnews/815509.htm
- http://m.3g.oexnr.cn/nnews/8062.htm
- http://m.3g.oexnr.cn/nnews/895848.htm
- http://m.3g.oexnr.cn/nnews/991588.htm
- http://m.3g.oexnr.cn/nnews/0474951.htm
- http://m.3g.oexnr.cn/nnews/55345.htm
- http://m.3g.oexnr.cn/nnews/476437.htm
- http://m.3g.oexnr.cn/nnews/6775535.htm
- http://m.3g.oexnr.cn/nnews/572097.htm
- http://m.3g.oexnr.cn/nnews/3754840.htm
- http://m.3g.oexnr.cn/nnews/2116.htm
- http://m.3g.oexnr.cn/nnews/8617.htm
- http://m.3g.oexnr.cn/nnews/2574.htm
- http://m.3g.oexnr.cn/nnews/115274.htm
- http://m.3g.oexnr.cn/nnews/2924.htm
- http://m.3g.oexnr.cn/nnews/161706.htm
- http://m.3g.oexnr.cn/nnews/5873.htm
- http://m.3g.oexnr.cn/nnews/61290.htm
- http://m.3g.oexnr.cn/nnews/1837918.htm
- http://m.3g.oexnr.cn/nnews/22967.htm
- http://m.3g.oexnr.cn/nnews/2741145.htm
- http://m.3g.oexnr.cn/nnews/7505360.htm
- http://m.3g.oexnr.cn/nnews/2456107.htm
- http://m.3g.oexnr.cn/nnews/56790.htm
- http://m.3g.oexnr.cn/nnews/66735.htm
- http://m.3g.oexnr.cn/nnews/5576727.htm
- http://m.3g.oexnr.cn/nnews/201731.htm
- http://m.3g.oexnr.cn/nnews/682511.htm
- http://m.3g.oexnr.cn/nnews/3896.htm
- http://m.3g.oexnr.cn/nnews/50017.htm
- http://m.3g.oexnr.cn/nnews/7294344.htm
- http://m.3g.oexnr.cn/nnews/586043.htm
- http://m.3g.oexnr.cn/nnews/9134420.htm
- http://m.3g.oexnr.cn/nnews/1350123.htm
- http://m.3g.oexnr.cn/nnews/3486.htm
- http://m.3g.oexnr.cn/nnews/8676792.htm
- http://m.3g.oexnr.cn/nnews/48526.htm
- http://m.3g.oexnr.cn/nnews/99858.htm
- http://m.3g.oexnr.cn/nnews/85182.htm
- http://m.3g.oexnr.cn/nnews/1719.htm
- http://m.3g.oexnr.cn/nnews/4871.htm
- http://m.3g.oexnr.cn/nnews/56027.htm
- http://m.3g.oexnr.cn/nnews/0676929.htm
- http://m.3g.oexnr.cn/nnews/266063.htm
- http://m.3g.oexnr.cn/nnews/52629.htm
- http://m.3g.oexnr.cn/nnews/324688.htm
- http://m.3g.oexnr.cn/nnews/0217.htm
- http://m.3g.oexnr.cn/nnews/0681.htm
- http://m.3g.oexnr.cn/nnews/6090.htm
- http://m.3g.oexnr.cn/nnews/9672202.htm
- http://m.3g.oexnr.cn/nnews/7543.htm
- http://m.3g.oexnr.cn/nnews/847847.htm
- http://m.3g.oexnr.cn/nnews/45657.htm
- http://m.3g.oexnr.cn/nnews/4354577.htm
- http://m.3g.oexnr.cn/nnews/5375877.htm
- http://m.3g.oexnr.cn/nnews/540080.htm
- http://m.3g.oexnr.cn/nnews/39034.htm
- http://m.3g.oexnr.cn/nnews/6314.htm
- http://m.3g.oexnr.cn/nnews/7132817.htm
- http://m.3g.oexnr.cn/nnews/77978.htm
- http://m.3g.oexnr.cn/nnews/28977.htm
- http://m.3g.oexnr.cn/nnews/4537166.htm
- http://m.3g.oexnr.cn/nnews/7348014.htm
- http://m.3g.oexnr.cn/nnews/58682.htm
- http://m.3g.oexnr.cn/nnews/89660.htm
- http://m.3g.oexnr.cn/nnews/67661.htm
- http://m.3g.oexnr.cn/nnews/00960.htm
- http://m.3g.oexnr.cn/nnews/75219.htm
- http://m.3g.oexnr.cn/nnews/2105.htm
- http://m.3g.oexnr.cn/nnews/744795.htm
- http://m.3g.oexnr.cn/nnews/517148.htm
- http://m.3g.oexnr.cn/nnews/56018.htm
- http://m.3g.oexnr.cn/nnews/7541285.htm
- http://m.3g.oexnr.cn/nnews/37206.htm
- http://m.3g.oexnr.cn/nnews/9537.htm
- http://m.3g.oexnr.cn/nnews/22660.htm
- http://m.3g.oexnr.cn/nnews/8159999.htm
- http://m.3g.oexnr.cn/nnews/894374.htm
- http://m.3g.oexnr.cn/nnews/35957.htm
- http://m.3g.oexnr.cn/nnews/6425336.htm
- http://m.3g.oexnr.cn/nnews/0762.htm
- http://m.3g.oexnr.cn/nnews/925737.htm
- http://m.3g.oexnr.cn/nnews/8837.htm
- http://m.3g.oexnr.cn/nnews/7579.htm
- http://m.3g.oexnr.cn/nnews/67751.htm
- http://m.3g.oexnr.cn/nnews/1618597.htm
- http://m.3g.oexnr.cn/nnews/9286.htm
- http://m.3g.oexnr.cn/nnews/9199.htm
- http://m.3g.oexnr.cn/nnews/0986213.htm
- http://m.3g.oexnr.cn/nnews/37086.htm
- http://m.3g.oexnr.cn/nnews/968810.htm
- http://m.3g.oexnr.cn/nnews/46460.htm
- http://m.3g.oexnr.cn/nnews/88247.htm
- http://m.3g.oexnr.cn/nnews/5258.htm
- http://m.3g.oexnr.cn/nnews/3678392.htm
- http://m.3g.oexnr.cn/nnews/59089.htm
- http://m.3g.oexnr.cn/nnews/5452962.htm
- http://m.3g.oexnr.cn/nnews/038052.htm
- http://m.3g.oexnr.cn/nnews/555349.htm
- http://m.3g.oexnr.cn/nnews/9276.htm
- http://m.3g.oexnr.cn/nnews/6719.htm
- http://m.3g.oexnr.cn/nnews/3368316.htm
- http://m.3g.oexnr.cn/nnews/54340.htm
- http://m.3g.oexnr.cn/nnews/851286.htm
- http://m.3g.oexnr.cn/nnews/28869.htm
- http://m.3g.oexnr.cn/nnews/54578.htm
- http://m.3g.oexnr.cn/nnews/6808.htm
- http://m.3g.oexnr.cn/nnews/39149.htm
- http://m.3g.oexnr.cn/nnews/1550385.htm
- http://m.3g.oexnr.cn/nnews/65181.htm
- http://m.3g.oexnr.cn/nnews/2140919.htm
- http://m.3g.oexnr.cn/nnews/7826.htm
- http://m.3g.oexnr.cn/nnews/857195.htm
- http://m.3g.oexnr.cn/nnews/554143.htm
- http://m.3g.oexnr.cn/nnews/808417.htm
- http://m.3g.oexnr.cn/nnews/119227.htm
- http://m.3g.oexnr.cn/nnews/2079.htm
- http://m.3g.oexnr.cn/nnews/841099.htm
- http://m.3g.oexnr.cn/nnews/5151378.htm
- http://m.3g.oexnr.cn/nnews/9598537.htm
- http://m.3g.oexnr.cn/nnews/45878.htm
- http://m.3g.oexnr.cn/nnews/38043.htm
- http://m.3g.oexnr.cn/nnews/03618.htm
- http://m.3g.oexnr.cn/nnews/44397.htm
- http://m.3g.oexnr.cn/nnews/910827.htm
- http://m.3g.oexnr.cn/nnews/978446.htm
- http://m.3g.oexnr.cn/nnews/7756.htm
- http://m.3g.oexnr.cn/nnews/6494.htm
- http://m.3g.oexnr.cn/nnews/752109.htm
- http://m.3g.oexnr.cn/nnews/239719.htm
- http://m.3g.oexnr.cn/nnews/970840.htm
- http://m.3g.oexnr.cn/nnews/6063.htm
- http://m.3g.oexnr.cn/nnews/4867.htm
- http://m.3g.oexnr.cn/nnews/123409.htm
- http://m.3g.oexnr.cn/nnews/4905.htm
- http://m.3g.oexnr.cn/nnews/1146294.htm
- http://m.3g.oexnr.cn/nnews/0253.htm
- http://m.3g.oexnr.cn/nnews/837330.htm
- http://m.3g.oexnr.cn/nnews/33985.htm
- http://m.3g.oexnr.cn/nnews/987530.htm
- http://m.3g.oexnr.cn/nnews/2731.htm
- http://m.3g.oexnr.cn/nnews/028858.htm
- http://m.3g.oexnr.cn/nnews/0101575.htm
- http://m.3g.oexnr.cn/nnews/199559.htm
- http://m.3g.oexnr.cn/nnews/72621.htm
- http://m.3g.oexnr.cn/nnews/272258.htm
- http://m.3g.oexnr.cn/nnews/8020667.htm
- http://m.3g.oexnr.cn/nnews/2429.htm
- http://m.3g.oexnr.cn/nnews/55466.htm
- http://m.3g.oexnr.cn/nnews/9033720.htm
- http://m.3g.oexnr.cn/nnews/0280942.htm
- http://m.3g.oexnr.cn/nnews/6182.htm
- http://m.3g.oexnr.cn/nnews/6912571.htm
- http://m.3g.oexnr.cn/nnews/9650708.htm
- http://m.3g.oexnr.cn/nnews/3864948.htm
- http://m.3g.oexnr.cn/nnews/2440582.htm
- http://m.3g.oexnr.cn/nnews/98801.htm
- http://m.3g.oexnr.cn/nnews/3840342.htm
- http://m.3g.oexnr.cn/nnews/548358.htm
- http://m.3g.oexnr.cn/nnews/3576356.htm
- http://m.3g.oexnr.cn/nnews/6861952.htm
- http://m.3g.oexnr.cn/nnews/36656.htm
- http://m.3g.oexnr.cn/nnews/209422.htm
- http://m.3g.oexnr.cn/nnews/613486.htm
- http://m.3g.oexnr.cn/nnews/9405.htm
- http://m.3g.oexnr.cn/nnews/07690.htm
- http://m.3g.oexnr.cn/nnews/29998.htm
- http://m.3g.oexnr.cn/nnews/8731491.htm
- http://m.3g.oexnr.cn/nnews/6815040.htm
- http://m.3g.oexnr.cn/nnews/882562.htm
- http://m.3g.oexnr.cn/nnews/666612.htm
- http://m.3g.oexnr.cn/nnews/1556.htm
- http://m.3g.oexnr.cn/nnews/1739193.htm
- http://m.3g.oexnr.cn/nnews/54109.htm
- http://m.3g.oexnr.cn/nnews/5711834.htm
- http://m.3g.oexnr.cn/nnews/70403.htm
- http://m.3g.oexnr.cn/nnews/05491.htm
- http://m.3g.oexnr.cn/nnews/14670.htm
- http://m.3g.oexnr.cn/nnews/13058.htm
- http://m.3g.oexnr.cn/nnews/3979071.htm
- http://m.3g.oexnr.cn/nnews/0640.htm

## 项目结构

```
newslink-archive/
├── config/                          # 配置文件目录
│   ├── default.yaml                 # 默认参数（并发数、超时、重试策略等）
│   └── logging.conf                 # 日志格式与输出级别配置
├── newslink/                        # 核心源码包
│   ├── __init__.py                  # 包版本声明与导出接口
│   ├── cli.py                       # 命令行入口，注册子命令与参数解析
│   ├── collector/                   # 采集子模块
│   │   ├── __init__.py
│   │   ├── fetcher.py               # 异步请求调度器，含连接池与重试逻辑
│   │   └── parser.py                # HTML 解析器，基于 lxml 抽取元数据
│   ├── storage/                     # 存储子模块
│   │   ├── __init__.py
│   │   ├── writer.py                # JSON Lines 写入器，支持按日期分片
│   │   └── reader.py                # 按日期范围读取归档文件的迭代器
│   ├── index/                       # 索引子模块
│   │   ├── __init__.py
│   │   ├── tokenizer.py             # jieba 分词封装，支持停用词过滤
│   │   └── leveldb_store.py         # LevelDB 的读写封装，支持批量插入
│   └── checker/                     # 健康检查子模块
│       ├── __init__.py
│       └── validator.py             # 并发 HEAD 请求器，生成 CSV 报告
├── tests/                           # 单元测试目录
│   ├── test_fetcher.py              # 模拟 HTTP 响应的采集测试
│   ├── test_parser.py               # 针对不同 HTML 结构的解析测试
│   └── test_storage.py              # 写入与读取的 I/O 测试
├── scripts/                         # 运维辅助脚本
│   ├── daily_cron.sh                # 每日定时采集的 cron 包装脚本
│   └── migrate_v1_to_v2.py          # 旧版数据格式迁移工具
├── docs/                            # 文档目录（见上方文档导航）
├── requirements.txt                 # 生产环境依赖列表
├── requirements-dev.txt             # 开发环境额外依赖（测试、lint）
├── setup.py                         # setuptools 安装脚本
└── README.md                        # 本文件
```

## 贡献指南

1. 查阅 issue 列表与项目看板，选择未被指派的 bug 或 feature 任务，在对应 issue 下评论说明认领意图，等待维护者确认避免重复工作。

2. 从主分支创建功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题编号` 格式，例如 `feature/add-json-export`。提交信息使用约定式提交规范（如 `feat: 增加导出子命令` 或 `fix: 修复空指针异常`）。

3. 编写或更新对应的单元测试，确保新增代码的测试覆盖率达到 80% 以上。运行 `pytest tests/` 验证所有测试通过，并执行 `flake8 newslink/` 检查代码风格。

4. 更新相关文档，包括用户手册中对应的使用说明、配置参数说明，以及 API 参考中的函数签名变更。若涉及配置项增删，需同步修改 `config/default.yaml` 的注释。

5. 发起 Pull Request 到主分支，在 PR 描述中关联对应的 issue 编号，并附上手动测试的日志片段或截图。等待至少一位维护者审阅通过后合并。

## 常见问题

Q: 采集过程中出现大量 HTTP 429 或 403 响应，如何调整策略？

A: 该响应通常表示目标服务器实施了频率限制或反爬机制。建议首先降低并发数（通过 `--concurrency 1` 或 2 运行），并增加单次请求的超时时间（`--timeout 30`）。配置文件中的 `request_delay` 参数可用于设置每次请求后的固定休眠间隔（单位秒）。若仍被限制，可考虑更换代理池或使用 `--user-agent` 参数随机切换 User-Agent。

Q: 索引构建失败，报错 `LevelDB: IO error: lock held by another process` 是什么原因？

A: 该错误表示索引目录正被另一个进程占用。最常见的情况是之前运行的 `index` 子命令未正常退出（如被 SIGKILL 杀死），导致锁文件残留。解决方案为删除索引目录下的 `LOCK` 文件（默认位于 `./index_data/`），然后重新执行索引命令。若需多进程并发访问，可配置 `index_use_shm` 参数改用共享内存模式，但生产环境不推荐。

Q: 如何迁移数据到新的存储路径或文件系统？

A: 项目提供 `scripts/migrate_v1_to_v2.py` 脚本，支持将旧路径下的全部 JSON Lines 文件复制或硬链接到新路径，并自动更新配置文件中 `storage.path` 字段。对于跨文件系统迁移，建议使用 `--copy-mode hard` 选项以节省磁盘空间，但需注意硬链接不支持跨设备。迁移完成后，建议手动运行一次 `check` 子命令验证归档文件的完整性。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
