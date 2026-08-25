# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端资讯聚合与深度内容导航的开源工具，专为需要从海量信息源中快速提取、整理、分发新闻链接的开发者、内容运营者及研究机构设计。该项目提供了一套轻量级的链接采集与结构化输出框架，能够将分散在各级域名下的原始新闻条目转化为可检索、可分类、可追溯的规范化资源列表，适用于构建自定义新闻聚合流、舆情监控数据源或学术研究语料库。

项目核心定位为“外链编排引擎”，不存储任何内容副本，仅对原始链接进行去重、时效性标记与分类归档，完全遵守 robots 协议及站点资源使用规范。通过本工具，用户可以以极低的运维成本建立起一套面向特定域名（如 m.wap.ghtkgg.cn）的深度链接索引体系，并支持批量导出、定时刷新与自定义标签注入，极大提升移动端新闻资源的二次利用效率。

## 功能概览

**批量链接抽取与规范化**：支持从指定域名下批量提取 .htm 后缀的新闻链接，自动补全相对路径并生成标准化 URL 输出，确保每条链接格式一致且可直接访问。

**递归深度遍历与并发控制**：提供可配置的递归爬取深度（默认 3 层）与并发请求数（默认 5 并发），在保证采集效率的同时避免对目标站点造成过大压力。

**结构化元数据生成**：为每条链接自动生成采集时间戳、来源域名校验、内容哈希指纹以及状态码记录，便于后续数据清洗与去重。

**多格式资源清单导出**：内置 Markdown 列表、JSON 数组、纯文本三種导出模板，适配不同下游系统（如静态站点生成器、数据管道、人工审阅表）的输入要求。

**增量更新与变更日志**：维护本地 SQLite 索引库，支持仅拉取新增或更新状态的链接，并生成变更差异报告，显著降低重复采集成本。

**域名白名单与请求头伪装**：允许用户自定义允许抓取的域名列表及 User-Agent 轮换策略，提升采集过程的隐蔽性与合规性。

## 应用场景

**移动端新闻聚合站点构建**：运营者可使用本工具定期同步 m.wap.ghtkgg.cn 下的最新资讯链接，自动生成每日更新列表，再配合静态生成器产出轻量级新闻门户，无需维护复杂后端数据库。

**舆情监控与话题追踪**：研究机构或媒体监测团队可将本工具集成至数据流水线，定时拉取指定域名的新闻链接并交由 NLP 模块进行情感分析与热点词提取，辅助生成舆情周报。

**学术研究语料采集**：高校新闻传播学科研团队可利用本工具批量采集特定时段内的新闻链接元数据，构建基于 URL 时序变化的传播路径分析数据集，支撑量化研究。

**个人知识库资讯源补充**：知识管理爱好者可将导出的链接清单导入到 Obsidian、Notion 等工具中，配合自动化脚本实现每日早报聚合，形成个性化的信息输入闭环。

## 快速开始

以下指令将在本地克隆项目仓库、安装生产依赖并启动一个最小化的采集任务，默认目标域名为 m.wap.ghtkgg.cn，采集深度为 2 层，输出 Markdown 格式的资源列表至 ./output 目录。

```bash
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator
npm install
npm run build
node dist/cli.js --domain m.wap.ghtkgg.cn --depth 2 --format markdown --output ./output
```

若使用 Python 版（项目同时维护 Python 3.9+ 运行时），可执行以下等效命令：

```bash
git clone -b python-runtime https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator
pip install -r requirements.txt
python -m jnews_aggregator --domain m.wap.ghtkgg.cn --depth 2 --format markdown --output ./output
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 用于运行 TypeScript 编译后的主程序，建议使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 依赖包管理器，用于安装 axios、cheerio、sqlite3 等核心库 |
| Python 3.9+（可选） | 3.9.0 及以上 | 仅当使用 Python 运行时分支时需要，需包含 pip 和 venv 模块 |
| SQLite 3 | 3.31.0 及以上 | 用于本地索引库的持久化存储，系统自带或通过 apt/brew 安装 |
| 网络访问权限 | 出方向 80/443 | 需要能够访问目标域名 m.wap.ghtkgg.cn 的 HTTP 服务，建议配置稳定 DNS |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何配置采集参数、调整输出格式、处理常见采集报错 |
| 运维指南 | /docs/ops-guide.md | 如何部署定时任务、监控采集状态、备份 SQLite 索引库 |
| 开发者文档 | /docs/developer-guide.md | 如何扩展自定义解析器、替换存储后端、编写单元测试 |
| API 参考 | /docs/api-reference.md | CLI 命令行参数详解、Node.js 模块导出接口、Python 包调用示例 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/38834.htm
- http://m.wap.ghtkgg.cn/jnews/218153.htm
- http://m.wap.ghtkgg.cn/jnews/8518999.htm
- http://m.wap.ghtkgg.cn/jnews/4397039.htm
- http://m.wap.ghtkgg.cn/jnews/5393.htm
- http://m.wap.ghtkgg.cn/jnews/8314450.htm
- http://m.wap.ghtkgg.cn/jnews/659972.htm
- http://m.wap.ghtkgg.cn/jnews/868467.htm
- http://m.wap.ghtkgg.cn/jnews/329257.htm
- http://m.wap.ghtkgg.cn/jnews/1875815.htm
- http://m.wap.ghtkgg.cn/jnews/4228.htm
- http://m.wap.ghtkgg.cn/jnews/6186474.htm
- http://m.wap.ghtkgg.cn/jnews/7041.htm
- http://m.wap.ghtkgg.cn/jnews/9154647.htm
- http://m.wap.ghtkgg.cn/jnews/1835.htm
- http://m.wap.ghtkgg.cn/jnews/10333.htm
- http://m.wap.ghtkgg.cn/jnews/69313.htm
- http://m.wap.ghtkgg.cn/jnews/063302.htm
- http://m.wap.ghtkgg.cn/jnews/8446.htm
- http://m.wap.ghtkgg.cn/jnews/3096051.htm
- http://m.wap.ghtkgg.cn/jnews/72379.htm
- http://m.wap.ghtkgg.cn/jnews/9024.htm
- http://m.wap.ghtkgg.cn/jnews/7695.htm
- http://m.wap.ghtkgg.cn/jnews/3414148.htm
- http://m.wap.ghtkgg.cn/jnews/0758.htm
- http://m.wap.ghtkgg.cn/jnews/5313.htm
- http://m.wap.ghtkgg.cn/jnews/55238.htm
- http://m.wap.ghtkgg.cn/jnews/7614534.htm
- http://m.wap.ghtkgg.cn/jnews/0723.htm
- http://m.wap.ghtkgg.cn/jnews/8589.htm
- http://m.wap.ghtkgg.cn/jnews/6552025.htm
- http://m.wap.ghtkgg.cn/jnews/94512.htm
- http://m.wap.ghtkgg.cn/jnews/163521.htm
- http://m.wap.ghtkgg.cn/jnews/7105.htm
- http://m.wap.ghtkgg.cn/jnews/780046.htm
- http://m.wap.ghtkgg.cn/jnews/7334.htm
- http://m.wap.ghtkgg.cn/jnews/0936593.htm
- http://m.wap.ghtkgg.cn/jnews/008184.htm
- http://m.wap.ghtkgg.cn/jnews/7565.htm
- http://m.wap.ghtkgg.cn/jnews/5156678.htm
- http://m.wap.ghtkgg.cn/jnews/110896.htm
- http://m.wap.ghtkgg.cn/jnews/194453.htm
- http://m.wap.ghtkgg.cn/jnews/4921.htm
- http://m.wap.ghtkgg.cn/jnews/231850.htm
- http://m.wap.ghtkgg.cn/jnews/2391274.htm
- http://m.wap.ghtkgg.cn/jnews/822582.htm
- http://m.wap.ghtkgg.cn/jnews/4833.htm
- http://m.wap.ghtkgg.cn/jnews/15979.htm
- http://m.wap.ghtkgg.cn/jnews/29580.htm
- http://m.wap.ghtkgg.cn/jnews/8560.htm
- http://m.wap.ghtkgg.cn/jnews/591879.htm
- http://m.wap.ghtkgg.cn/jnews/4334316.htm
- http://m.wap.ghtkgg.cn/jnews/110842.htm
- http://m.wap.ghtkgg.cn/jnews/8274288.htm
- http://m.wap.ghtkgg.cn/jnews/687051.htm
- http://m.wap.ghtkgg.cn/jnews/7397.htm
- http://m.wap.ghtkgg.cn/jnews/4286495.htm
- http://m.wap.ghtkgg.cn/jnews/7786704.htm
- http://m.wap.ghtkgg.cn/jnews/1756659.htm
- http://m.wap.ghtkgg.cn/jnews/0150302.htm
- http://m.wap.ghtkgg.cn/jnews/692280.htm
- http://m.wap.ghtkgg.cn/jnews/11369.htm
- http://m.wap.ghtkgg.cn/jnews/870767.htm
- http://m.wap.ghtkgg.cn/jnews/9439812.htm
- http://m.wap.ghtkgg.cn/jnews/8077.htm
- http://m.wap.ghtkgg.cn/jnews/6525487.htm
- http://m.wap.ghtkgg.cn/jnews/6579.htm
- http://m.wap.ghtkgg.cn/jnews/84307.htm
- http://m.wap.ghtkgg.cn/jnews/31729.htm
- http://m.wap.ghtkgg.cn/jnews/519359.htm
- http://m.wap.ghtkgg.cn/jnews/637217.htm
- http://m.wap.ghtkgg.cn/jnews/6867.htm
- http://m.wap.ghtkgg.cn/jnews/479157.htm
- http://m.wap.ghtkgg.cn/jnews/3972930.htm
- http://m.wap.ghtkgg.cn/jnews/60670.htm
- http://m.wap.ghtkgg.cn/jnews/8795991.htm
- http://m.wap.ghtkgg.cn/jnews/8376333.htm
- http://m.wap.ghtkgg.cn/jnews/08150.htm
- http://m.wap.ghtkgg.cn/jnews/283542.htm
- http://m.wap.ghtkgg.cn/jnews/4966.htm
- http://m.wap.ghtkgg.cn/jnews/9443934.htm
- http://m.wap.ghtkgg.cn/jnews/1575842.htm
- http://m.wap.ghtkgg.cn/jnews/407354.htm
- http://m.wap.ghtkgg.cn/jnews/0213859.htm
- http://m.wap.ghtkgg.cn/jnews/4830.htm
- http://m.wap.ghtkgg.cn/jnews/3424153.htm
- http://m.wap.ghtkgg.cn/jnews/7670194.htm
- http://m.wap.ghtkgg.cn/jnews/9307364.htm
- http://m.wap.ghtkgg.cn/jnews/5527392.htm
- http://m.wap.ghtkgg.cn/jnews/9674.htm
- http://m.wap.ghtkgg.cn/jnews/454402.htm
- http://m.wap.ghtkgg.cn/jnews/0158428.htm
- http://m.wap.ghtkgg.cn/jnews/73019.htm
- http://m.wap.ghtkgg.cn/jnews/0923.htm
- http://m.wap.ghtkgg.cn/jnews/34390.htm
- http://m.wap.ghtkgg.cn/jnews/22163.htm
- http://m.wap.ghtkgg.cn/jnews/78344.htm
- http://m.wap.ghtkgg.cn/jnews/14949.htm
- http://m.wap.ghtkgg.cn/jnews/645066.htm
- http://m.wap.ghtkgg.cn/jnews/294551.htm
- http://m.wap.ghtkgg.cn/jnews/259663.htm
- http://m.wap.ghtkgg.cn/jnews/79591.htm
- http://m.wap.ghtkgg.cn/jnews/192705.htm
- http://m.wap.ghtkgg.cn/jnews/5505.htm
- http://m.wap.ghtkgg.cn/jnews/896946.htm
- http://m.wap.ghtkgg.cn/jnews/4418.htm
- http://m.wap.ghtkgg.cn/jnews/1401492.htm
- http://m.wap.ghtkgg.cn/jnews/476235.htm
- http://m.wap.ghtkgg.cn/jnews/32760.htm
- http://m.wap.ghtkgg.cn/jnews/28952.htm
- http://m.wap.ghtkgg.cn/jnews/91707.htm
- http://m.wap.ghtkgg.cn/jnews/0756502.htm
- http://m.wap.ghtkgg.cn/jnews/364157.htm
- http://m.wap.ghtkgg.cn/jnews/06077.htm
- http://m.wap.ghtkgg.cn/jnews/985627.htm
- http://m.wap.ghtkgg.cn/jnews/776686.htm
- http://m.wap.ghtkgg.cn/jnews/70991.htm
- http://m.wap.ghtkgg.cn/jnews/498421.htm
- http://m.wap.ghtkgg.cn/jnews/6843.htm
- http://m.wap.ghtkgg.cn/jnews/3243.htm
- http://m.wap.ghtkgg.cn/jnews/77813.htm
- http://m.wap.ghtkgg.cn/jnews/69166.htm
- http://m.wap.ghtkgg.cn/jnews/67138.htm
- http://m.wap.ghtkgg.cn/jnews/52108.htm
- http://m.wap.ghtkgg.cn/jnews/255968.htm
- http://m.wap.ghtkgg.cn/jnews/65548.htm
- http://m.wap.ghtkgg.cn/jnews/9019.htm
- http://m.wap.ghtkgg.cn/jnews/681346.htm
- http://m.wap.ghtkgg.cn/jnews/9740746.htm
- http://m.wap.ghtkgg.cn/jnews/8083.htm
- http://m.wap.ghtkgg.cn/jnews/0203.htm
- http://m.wap.ghtkgg.cn/jnews/4632651.htm
- http://m.wap.ghtkgg.cn/jnews/049634.htm
- http://m.wap.ghtkgg.cn/jnews/986229.htm
- http://m.wap.ghtkgg.cn/jnews/5786795.htm
- http://m.wap.ghtkgg.cn/jnews/85290.htm
- http://m.wap.ghtkgg.cn/jnews/8946467.htm
- http://m.wap.ghtkgg.cn/jnews/0949757.htm
- http://m.wap.ghtkgg.cn/jnews/3919.htm
- http://m.wap.ghtkgg.cn/jnews/3609485.htm
- http://m.wap.ghtkgg.cn/jnews/3507.htm
- http://m.wap.ghtkgg.cn/jnews/5461986.htm
- http://m.wap.ghtkgg.cn/jnews/725229.htm
- http://m.wap.ghtkgg.cn/jnews/39428.htm
- http://m.wap.ghtkgg.cn/jnews/6891663.htm
- http://m.wap.ghtkgg.cn/jnews/43930.htm
- http://m.wap.ghtkgg.cn/jnews/6845.htm
- http://m.wap.ghtkgg.cn/jnews/9709433.htm
- http://m.wap.ghtkgg.cn/jnews/0870745.htm
- http://m.wap.ghtkgg.cn/jnews/16392.htm
- http://m.wap.ghtkgg.cn/jnews/6999.htm
- http://m.wap.ghtkgg.cn/jnews/0110.htm
- http://m.wap.ghtkgg.cn/jnews/78501.htm
- http://m.wap.ghtkgg.cn/jnews/339571.htm
- http://m.wap.ghtkgg.cn/jnews/6303061.htm
- http://m.wap.ghtkgg.cn/jnews/0476140.htm
- http://m.wap.ghtkgg.cn/jnews/4316619.htm
- http://m.wap.ghtkgg.cn/jnews/678851.htm
- http://m.wap.ghtkgg.cn/jnews/843029.htm
- http://m.wap.ghtkgg.cn/jnews/6174.htm
- http://m.wap.ghtkgg.cn/jnews/7708789.htm
- http://m.wap.ghtkgg.cn/jnews/92156.htm
- http://m.wap.ghtkgg.cn/jnews/22642.htm
- http://m.wap.ghtkgg.cn/jnews/3360222.htm
- http://m.wap.ghtkgg.cn/jnews/2627.htm
- http://m.wap.ghtkgg.cn/jnews/3934.htm
- http://m.wap.ghtkgg.cn/jnews/974599.htm
- http://m.wap.ghtkgg.cn/jnews/0498402.htm
- http://m.wap.ghtkgg.cn/jnews/691254.htm
- http://m.wap.ghtkgg.cn/jnews/897324.htm
- http://m.wap.ghtkgg.cn/jnews/47762.htm
- http://m.wap.ghtkgg.cn/jnews/8173.htm
- http://m.wap.ghtkgg.cn/jnews/753735.htm
- http://m.wap.ghtkgg.cn/jnews/457009.htm
- http://m.wap.ghtkgg.cn/jnews/912515.htm
- http://m.wap.ghtkgg.cn/jnews/0873.htm
- http://m.wap.ghtkgg.cn/jnews/91463.htm
- http://m.wap.ghtkgg.cn/jnews/45004.htm
- http://m.wap.ghtkgg.cn/jnews/4803.htm
- http://m.wap.ghtkgg.cn/jnews/603372.htm
- http://m.wap.ghtkgg.cn/jnews/5316.htm
- http://m.wap.ghtkgg.cn/jnews/56669.htm
- http://m.wap.ghtkgg.cn/jnews/5135066.htm
- http://m.wap.ghtkgg.cn/jnews/06568.htm
- http://m.wap.ghtkgg.cn/jnews/1544120.htm
- http://m.wap.ghtkgg.cn/jnews/1239720.htm
- http://m.wap.ghtkgg.cn/jnews/2787.htm
- http://m.wap.ghtkgg.cn/jnews/46080.htm
- http://m.wap.ghtkgg.cn/jnews/94226.htm
- http://m.wap.ghtkgg.cn/jnews/85847.htm
- http://m.wap.ghtkgg.cn/jnews/4453778.htm
- http://m.wap.ghtkgg.cn/jnews/870196.htm
- http://m.wap.ghtkgg.cn/jnews/98275.htm
- http://m.wap.ghtkgg.cn/jnews/19310.htm
- http://m.wap.ghtkgg.cn/jnews/38294.htm
- http://m.wap.ghtkgg.cn/jnews/8822284.htm
- http://m.wap.ghtkgg.cn/jnews/4222999.htm
- http://m.wap.ghtkgg.cn/jnews/72827.htm
- http://m.wap.ghtkgg.cn/jnews/954742.htm
- http://m.wap.ghtkgg.cn/jnews/3974.htm
- http://m.wap.ghtkgg.cn/jnews/206557.htm
- http://m.wap.ghtkgg.cn/jnews/43206.htm
- http://m.wap.ghtkgg.cn/jnews/8885.htm
- http://m.wap.ghtkgg.cn/jnews/299711.htm
- http://m.wap.ghtkgg.cn/jnews/779708.htm
- http://m.wap.ghtkgg.cn/jnews/8940.htm
- http://m.wap.ghtkgg.cn/jnews/22183.htm
- http://m.wap.ghtkgg.cn/jnews/7587440.htm
- http://m.wap.ghtkgg.cn/jnews/22214.htm
- http://m.wap.ghtkgg.cn/jnews/917360.htm
- http://m.wap.ghtkgg.cn/jnews/40946.htm
- http://m.wap.ghtkgg.cn/jnews/0683.htm
- http://m.wap.ghtkgg.cn/jnews/7682.htm
- http://m.wap.ghtkgg.cn/jnews/3704.htm
- http://m.wap.ghtkgg.cn/jnews/7508028.htm
- http://m.wap.ghtkgg.cn/jnews/7355277.htm
- http://m.wap.ghtkgg.cn/jnews/658971.htm
- http://m.wap.ghtkgg.cn/jnews/83136.htm
- http://m.wap.ghtkgg.cn/jnews/825929.htm
- http://m.wap.ghtkgg.cn/jnews/7338060.htm
- http://m.wap.ghtkgg.cn/jnews/6637082.htm
- http://m.wap.ghtkgg.cn/jnews/605850.htm
- http://m.wap.ghtkgg.cn/jnews/1272.htm
- http://m.wap.ghtkgg.cn/jnews/75508.htm
- http://m.wap.ghtkgg.cn/jnews/3897947.htm
- http://m.wap.ghtkgg.cn/jnews/154337.htm
- http://m.wap.ghtkgg.cn/jnews/8879.htm
- http://m.wap.ghtkgg.cn/jnews/5516308.htm
- http://m.wap.ghtkgg.cn/jnews/8691.htm
- http://m.wap.ghtkgg.cn/jnews/121661.htm
- http://m.wap.ghtkgg.cn/jnews/413043.htm
- http://m.wap.ghtkgg.cn/jnews/40898.htm
- http://m.wap.ghtkgg.cn/jnews/1338584.htm
- http://m.wap.ghtkgg.cn/jnews/823154.htm
- http://m.wap.ghtkgg.cn/jnews/16207.htm
- http://m.wap.ghtkgg.cn/jnews/852178.htm
- http://m.wap.ghtkgg.cn/jnews/1417487.htm
- http://m.wap.ghtkgg.cn/jnews/4130196.htm
- http://m.wap.ghtkgg.cn/jnews/9325101.htm
- http://m.wap.ghtkgg.cn/jnews/3112.htm
- http://m.wap.ghtkgg.cn/jnews/7749818.htm
- http://m.wap.ghtkgg.cn/jnews/2663.htm
- http://m.wap.ghtkgg.cn/jnews/1660533.htm
- http://m.wap.ghtkgg.cn/jnews/78968.htm
- http://m.wap.ghtkgg.cn/jnews/8082.htm
- http://m.wap.ghtkgg.cn/jnews/80781.htm
- http://m.wap.ghtkgg.cn/jnews/84474.htm
- http://m.wap.ghtkgg.cn/jnews/97882.htm
- http://m.wap.ghtkgg.cn/jnews/9598134.htm
- http://m.wap.ghtkgg.cn/jnews/257611.htm
- http://m.wap.ghtkgg.cn/jnews/7054656.htm
- http://m.wap.ghtkgg.cn/jnews/32789.htm
- http://m.wap.ghtkgg.cn/jnews/22272.htm
- http://m.wap.ghtkgg.cn/jnews/49616.htm
- http://m.wap.ghtkgg.cn/jnews/731890.htm
- http://m.wap.ghtkgg.cn/jnews/9548161.htm
- http://m.wap.ghtkgg.cn/jnews/3123503.htm
- http://m.wap.ghtkgg.cn/jnews/8762877.htm
- http://m.wap.ghtkgg.cn/jnews/303895.htm
- http://m.wap.ghtkgg.cn/jnews/9853320.htm
- http://m.wap.ghtkgg.cn/jnews/188845.htm
- http://m.wap.ghtkgg.cn/jnews/43410.htm
- http://m.wap.ghtkgg.cn/jnews/6899.htm
- http://m.wap.ghtkgg.cn/jnews/840773.htm
- http://m.wap.ghtkgg.cn/jnews/572099.htm
- http://m.wap.ghtkgg.cn/jnews/11827.htm
- http://m.wap.ghtkgg.cn/jnews/3247645.htm
- http://m.wap.ghtkgg.cn/jnews/6803530.htm
- http://m.wap.ghtkgg.cn/jnews/241781.htm
- http://m.wap.ghtkgg.cn/jnews/1885913.htm
- http://m.wap.ghtkgg.cn/jnews/6722.htm
- http://m.wap.ghtkgg.cn/jnews/5620884.htm
- http://m.wap.ghtkgg.cn/jnews/67182.htm
- http://m.wap.ghtkgg.cn/jnews/048735.htm
- http://m.wap.ghtkgg.cn/jnews/96326.htm
- http://m.wap.ghtkgg.cn/jnews/397386.htm
- http://m.wap.ghtkgg.cn/jnews/08397.htm
- http://m.wap.ghtkgg.cn/jnews/04261.htm
- http://m.wap.ghtkgg.cn/jnews/0150689.htm
- http://m.wap.ghtkgg.cn/jnews/1252.htm
- http://m.wap.ghtkgg.cn/jnews/1381230.htm
- http://m.wap.ghtkgg.cn/jnews/178329.htm
- http://m.wap.ghtkgg.cn/jnews/6340529.htm
- http://m.wap.ghtkgg.cn/jnews/71203.htm
- http://m.wap.ghtkgg.cn/jnews/627580.htm
- http://m.wap.ghtkgg.cn/jnews/8922.htm
- http://m.wap.ghtkgg.cn/jnews/7723.htm
- http://m.wap.ghtkgg.cn/jnews/3806732.htm
- http://m.wap.ghtkgg.cn/jnews/249085.htm
- http://m.wap.ghtkgg.cn/jnews/066872.htm
- http://m.wap.ghtkgg.cn/jnews/384639.htm
- http://m.wap.ghtkgg.cn/jnews/7903241.htm
- http://m.wap.ghtkgg.cn/jnews/310417.htm
- http://m.wap.ghtkgg.cn/jnews/473151.htm
- http://m.wap.ghtkgg.cn/jnews/1886.htm
- http://m.wap.ghtkgg.cn/jnews/914620.htm
- http://m.wap.ghtkgg.cn/jnews/416238.htm
- http://m.wap.ghtkgg.cn/jnews/2707315.htm
- http://m.wap.ghtkgg.cn/jnews/3189.htm
- http://m.wap.ghtkgg.cn/jnews/8290.htm

## 项目结构

```
jnews-link-aggregator/
├── src/                                # TypeScript 源代码主目录
│   ├── cli/                            # 命令行入口与参数解析模块
│   │   ├── index.ts                    # CLI 主入口，整合 commander 与日志初始化
│   │   └── options.ts                  # 定义 domain、depth、format、output 等选项
│   ├── core/                           # 核心采集引擎
│   │   ├── crawler.ts                  # 递归爬取器，实现深度遍历与并发控制
│   │   ├── parser.ts                   # HTML 解析器，基于 cheerio 提取链接
│   │   └── validator.ts                # URL 规范化与域名白名单校验
│   ├── storage/                        # 存储与索引层
│   │   ├── database.ts                 # SQLite 连接池与表结构初始化
│   │   ├── repository.ts               # 链接增删改查及增量更新逻辑
│   │   └── migration.ts                # 索引库版本迁移脚本
│   ├── export/                         # 导出格式化模块
│   │   ├── markdown.ts                 # 生成 Markdown 无序列表输出
│   │   ├── json.ts                     # 输出 JSON 数组格式，含元数据字段
│   │   └── plaintext.ts                # 纯文本每行一条链接的简约输出
│   ├── utils/                          # 通用工具函数集
│   │   ├── http.ts                     # axios 实例封装，含重试与超时策略
│   │   ├── hash.ts                     # 计算链接内容哈希指纹，用于去重
│   │   └── logger.ts                   # 分级日志输出（info/warn/error）
│   └── types/                          # TypeScript 类型定义
│       ├── link.ts                     # Link 接口定义（url、timestamp、status 等）
│       └── config.ts                   # 全局配置类型（并发数、超时、重试次数）
├── tests/                              # 单元测试与集成测试目录
│   ├── crawler.test.ts                 # 爬取器模块的模拟测试用例
│   ├── parser.test.ts                  # 解析器对各类 HTML 结构的覆盖测试
│   └── fixtures/                       # 测试用的静态 HTML 样本文件
├── docs/                               # 完整文档体系（用户手册、运维指南、开发者文档）
│   ├── user-guide.md                   # 面向最终用户的使用说明
│   ├── ops-guide.md                    # 面向运维人员的部署与监控指南
│   └── developer-guide.md              # 面向贡献者的架构设计与扩展点说明
├── scripts/                            # 辅助运维脚本
│   ├── backup.sh                       # 定时备份 SQLite 索引库的 shell 脚本
│   └── clean-logs.sh                   # 日志轮转与过期清理脚本
├── config/                             # 环境配置文件
│   ├── default.json                    # 默认采集参数（并发 5、深度 3）
│   └── production.json                 # 生产环境覆盖配置（日志级别、超时时间）
├── .github/                            # GitHub 社区规范
│   ├── workflows/                      # CI 流水线配置（构建、测试、代码扫描）
│   └── ISSUE_TEMPLATE/                 # 问题报告与功能请求模板
├── package.json                        # npm 依赖管理、构建脚本与元信息
├── tsconfig.json                       # TypeScript 编译配置（目标 ES2020）
├── README.md                           # 项目主文档（即当前文档）
└── LICENSE                             # MIT 许可证全文
```

## 贡献指南

**提交问题报告**：在 GitHub Issues 中使用提供的模板提交问题，需附上完整的运行日志、Node.js 版本号、操作系统信息以及可复现的最小命令示例。对于采集异常，请同时提供目标 URL 样例。

**代码贡献流程**：Fork 本仓库后创建功能分支，遵循 Conventional Commits 规范撰写提交信息。提交前请确保通过全部单元测试（npm test）并新增对应测试用例覆盖改动。发起 Pull Request 时需关联相关 Issue 编号。

**文档改进**：欢迎修正错别字、翻译优化或补充更详细的使用案例。文档位于 /docs 目录，采用 Markdown 格式，修改后需确保本地预览渲染正常。对于新增功能，必须同步更新用户手册与 API 参考。

**性能测试与反馈**：若您在实际生产环境中使用了本工具，并针对大规模链接采集（超过 10 万条）有性能优化建议，欢迎分享您的配置参数、服务器规格及压测报告，这对项目演进极具价值。

## 常见问题

**采集过程中出现 403 或 429 状态码如何解决？**

这通常表明目标站点启用了反爬机制或频率限制。建议降低并发数（--concurrency 1）、增加请求间隔（--delay 2000 毫秒），并检查是否配置了合法的 User-Agent。若仍然受阻，可尝试使用代理池或联系站点运营方申请白名单。

**增量更新模式如何判断链接是否有新增内容？**

本工具默认基于 URL 字符串完全匹配进行去重，不主动拉取页面内容。若需要检测内容更新，可开启 --checksum 模式，该模式会额外请求 HEAD 或 GET 并计算响应体哈希，但会显著增加采集耗时与带宽消耗。建议仅在关键数据源开启。

**是否支持除了 SQLite 以外的存储后端？**

当前主线版本仅内置 SQLite 支持，原因在于其零配置、单文件特性与轻量级定位高度契合。若需对接 MySQL 或 PostgreSQL，可参考 /docs/developer-guide.md 中的存储接口抽象，自行实现 Repository 类并通过配置注入即可。社区已贡献的实验性 PG 适配器位于 /contrib 目录。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
