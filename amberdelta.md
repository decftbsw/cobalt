# OEXNR News Resource Aggregator

OEXNR News Resource Aggregator 是一个面向移动端新闻资讯聚合的开源工具集，专注于从 oexnr.cn 域名下采集、解析和归档移动端新闻页面。该项目为内容研究者、数据分析师和新闻归档开发者提供标准化的数据获取接口，支持批量提取新闻标题、正文、发布时间及分类标签等核心元数据。

项目定位为轻量级新闻数据中间层，通过可复用的解析规则与缓存策略，降低开发者对单一新闻源的数据抓取与维护成本。适用于需要持续跟踪特定新闻来源的内容分析系统、舆情监控原型或学术研究数据集构建场景。

## 功能概览

**移动端页面自适应解析** - 针对 oexnr.cn 移动端页面结构优化的 HTML 解析器，自动识别移动端新闻模板的正文容器与元数据字段。

**批量 URL 导入与队列管理** - 支持从文本文件或标准输入流批量导入新闻链接，内置请求队列控制器，可配置并发数与请求间隔。

**结构化数据输出** - 将解析结果标准化为 JSON、CSV 或 SQLite 格式输出，便于后续导入数据库或数据分析工具。

**增量更新与去重机制** - 基于新闻 ID 和发布时间戳的增量抓取策略，避免重复处理已归档的新闻条目。

**请求重试与容错降级** - 网络请求失败时自动执行指数退避重试，对响应超时或状态码异常的请求进行日志记录并跳过。

**数据校验与清洗** - 对提取的文本内容进行空白字符压缩、HTML 实体解码和敏感字符过滤，确保输出数据的整洁性。

**命令行交互与配置文件支持** - 提供 CLI 工具，支持通过命令行参数或 YAML 配置文件指定运行模式、输出路径和过滤条件。

## 应用场景

**新闻内容归档与备份** - 研究人员或机构可使用本工具对指定新闻源定期执行全量或增量抓取，建立本地化的新闻资料库，防止源站内容删除或链接失效导致的数据损失。

**舆情分析与趋势监测** - 通过批量提取新闻标题和发布时间，结合外部 NLP 工具进行关键词频次统计与情感分析，辅助构建特定话题的热度变化趋势图谱。

**数据集构建与学术研究** - 高校实验室或社会科学研究者可利用该工具快速采集大规模新闻语料，用于训练文本分类模型、事件抽取系统或新闻推荐算法的评测数据集。

**新闻源健康度监控** - 运维人员可配置定时任务检测各新闻链接的可访问性、响应时间及内容更新频率，及时发现源站故障或内容异常。

## 快速开始

```bash
# 克隆项目仓库至本地
git clone https://github.com/oexnr/news-aggregator.git

# 进入项目根目录
cd news-aggregator

# 安装项目依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 执行示例抓取任务（使用项目内置的测试 URL 列表）
python cli.py --input sample_urls.txt --output result.json --format json --concurrency 5
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行时环境，建议使用 3.11 或 3.12 获得更好性能 |
| requests | 2.31.0 及以上 | HTTP 请求库，用于发送 GET 请求获取新闻页面 HTML |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，用于定位和提取新闻正文及元数据 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 的解析后端 |
| sqlite3 | 系统内置 | SQLite 数据库驱动，用于支持本地数据持久化存储 |
| pyyaml | 6.0 及以上 | YAML 配置文件解析库，用于读取用户自定义配置 |
| urllib3 | 2.0.0 及以上 | HTTP 连接池管理，由 requests 间接依赖，需确保版本兼容 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速安装并运行第一个抓取任务；命令行参数的基本用法 |
| 配置说明 | docs/configuration.md | YAML 配置文件中各字段的含义与可选值；如何自定义请求头与代理 |
| 解析规则 | docs/parsing_rules.md | 针对 oexnr.cn 移动端页面的 CSS 选择器与 XPath 规则；如何适配页面改版 |
| 数据输出 | docs/output_formats.md | JSON、CSV、SQLite 三种输出格式的字段定义与使用示例 |
| API 参考 | docs/api_reference.md | 核心模块与函数的接口文档，供二次开发与集成调用 |
| 故障排查 | docs/troubleshooting.md | 常见网络错误、解析失败与数据异常的诊断与解决方法 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/937333.htm
- http://m.wap.oexnr.cn/jnews/4574.htm
- http://m.wap.oexnr.cn/jnews/7381792.htm
- http://m.wap.oexnr.cn/jnews/309127.htm
- http://m.wap.oexnr.cn/jnews/5356485.htm
- http://m.wap.oexnr.cn/jnews/6448518.htm
- http://m.wap.oexnr.cn/jnews/2001078.htm
- http://m.wap.oexnr.cn/jnews/4404709.htm
- http://m.wap.oexnr.cn/jnews/99380.htm
- http://m.wap.oexnr.cn/jnews/5255.htm
- http://m.wap.oexnr.cn/jnews/3172.htm
- http://m.wap.oexnr.cn/jnews/298509.htm
- http://m.wap.oexnr.cn/jnews/8167014.htm
- http://m.wap.oexnr.cn/jnews/976399.htm
- http://m.wap.oexnr.cn/jnews/4126554.htm
- http://m.wap.oexnr.cn/jnews/3889.htm
- http://m.wap.oexnr.cn/jnews/10743.htm
- http://m.wap.oexnr.cn/jnews/5083413.htm
- http://m.wap.oexnr.cn/jnews/2299.htm
- http://m.wap.oexnr.cn/jnews/1026084.htm
- http://m.wap.oexnr.cn/jnews/207080.htm
- http://m.wap.oexnr.cn/jnews/1353365.htm
- http://m.wap.oexnr.cn/jnews/986855.htm
- http://m.wap.oexnr.cn/jnews/282021.htm
- http://m.wap.oexnr.cn/jnews/232288.htm
- http://m.wap.oexnr.cn/jnews/70927.htm
- http://m.wap.oexnr.cn/jnews/6538260.htm
- http://m.wap.oexnr.cn/jnews/4409.htm
- http://m.wap.oexnr.cn/jnews/06833.htm
- http://m.wap.oexnr.cn/jnews/21571.htm
- http://m.wap.oexnr.cn/jnews/61103.htm
- http://m.wap.oexnr.cn/jnews/4167488.htm
- http://m.wap.oexnr.cn/jnews/71001.htm
- http://m.wap.oexnr.cn/jnews/89549.htm
- http://m.wap.oexnr.cn/jnews/8550838.htm
- http://m.wap.oexnr.cn/jnews/387979.htm
- http://m.wap.oexnr.cn/jnews/88490.htm
- http://m.wap.oexnr.cn/jnews/6000.htm
- http://m.wap.oexnr.cn/jnews/7728.htm
- http://m.wap.oexnr.cn/jnews/0822415.htm
- http://m.wap.oexnr.cn/jnews/1514.htm
- http://m.wap.oexnr.cn/jnews/23714.htm
- http://m.wap.oexnr.cn/jnews/364364.htm
- http://m.wap.oexnr.cn/jnews/8279636.htm
- http://m.wap.oexnr.cn/jnews/46305.htm
- http://m.wap.oexnr.cn/jnews/2304032.htm
- http://m.wap.oexnr.cn/jnews/47660.htm
- http://m.wap.oexnr.cn/jnews/934813.htm
- http://m.wap.oexnr.cn/jnews/75354.htm
- http://m.wap.oexnr.cn/jnews/8289.htm
- http://m.wap.oexnr.cn/jnews/330246.htm
- http://m.wap.oexnr.cn/jnews/67236.htm
- http://m.wap.oexnr.cn/jnews/058325.htm
- http://m.wap.oexnr.cn/jnews/824081.htm
- http://m.wap.oexnr.cn/jnews/5163231.htm
- http://m.wap.oexnr.cn/jnews/2153951.htm
- http://m.wap.oexnr.cn/jnews/8881774.htm
- http://m.wap.oexnr.cn/jnews/127837.htm
- http://m.wap.oexnr.cn/jnews/474446.htm
- http://m.wap.oexnr.cn/jnews/9373329.htm
- http://m.wap.oexnr.cn/jnews/7190382.htm
- http://m.wap.oexnr.cn/jnews/952907.htm
- http://m.wap.oexnr.cn/jnews/395860.htm
- http://m.wap.oexnr.cn/jnews/50687.htm
- http://m.wap.oexnr.cn/jnews/091405.htm
- http://m.wap.oexnr.cn/jnews/6190.htm
- http://m.wap.oexnr.cn/jnews/4006.htm
- http://m.wap.oexnr.cn/jnews/8743.htm
- http://m.wap.oexnr.cn/jnews/9972.htm
- http://m.wap.oexnr.cn/jnews/59870.htm
- http://m.wap.oexnr.cn/jnews/1746.htm
- http://m.wap.oexnr.cn/jnews/2772599.htm
- http://m.wap.oexnr.cn/jnews/8139226.htm
- http://m.wap.oexnr.cn/jnews/371643.htm
- http://m.wap.oexnr.cn/jnews/6125110.htm
- http://m.wap.oexnr.cn/jnews/9351.htm
- http://m.wap.oexnr.cn/jnews/56531.htm
- http://m.wap.oexnr.cn/jnews/594477.htm
- http://m.wap.oexnr.cn/jnews/05661.htm
- http://m.wap.oexnr.cn/jnews/8144.htm
- http://m.wap.oexnr.cn/jnews/677378.htm
- http://m.wap.oexnr.cn/jnews/3754782.htm
- http://m.wap.oexnr.cn/jnews/501696.htm
- http://m.wap.oexnr.cn/jnews/1294.htm
- http://m.wap.oexnr.cn/jnews/87004.htm
- http://m.wap.oexnr.cn/jnews/975054.htm
- http://m.wap.oexnr.cn/jnews/54261.htm
- http://m.wap.oexnr.cn/jnews/102136.htm
- http://m.wap.oexnr.cn/jnews/8821.htm
- http://m.wap.oexnr.cn/jnews/5050.htm
- http://m.wap.oexnr.cn/jnews/2328.htm
- http://m.wap.oexnr.cn/jnews/1501063.htm
- http://m.wap.oexnr.cn/jnews/714263.htm
- http://m.wap.oexnr.cn/jnews/1543056.htm
- http://m.wap.oexnr.cn/jnews/82032.htm
- http://m.wap.oexnr.cn/jnews/4300650.htm
- http://m.wap.oexnr.cn/jnews/48944.htm
- http://m.wap.oexnr.cn/jnews/3407727.htm
- http://m.wap.oexnr.cn/jnews/9131557.htm
- http://m.wap.oexnr.cn/jnews/4060924.htm
- http://m.wap.oexnr.cn/jnews/15257.htm
- http://m.wap.oexnr.cn/jnews/2811148.htm
- http://m.wap.oexnr.cn/jnews/8816030.htm
- http://m.wap.oexnr.cn/jnews/5683.htm
- http://m.wap.oexnr.cn/jnews/705471.htm
- http://m.wap.oexnr.cn/jnews/98832.htm
- http://m.wap.oexnr.cn/jnews/6048986.htm
- http://m.wap.oexnr.cn/jnews/504532.htm
- http://m.wap.oexnr.cn/jnews/847552.htm
- http://m.wap.oexnr.cn/jnews/524558.htm
- http://m.wap.oexnr.cn/jnews/07345.htm
- http://m.wap.oexnr.cn/jnews/1232.htm
- http://m.wap.oexnr.cn/jnews/628671.htm
- http://m.wap.oexnr.cn/jnews/8669786.htm
- http://m.wap.oexnr.cn/jnews/1961196.htm
- http://m.wap.oexnr.cn/jnews/798100.htm
- http://m.wap.oexnr.cn/jnews/0437552.htm
- http://m.wap.oexnr.cn/jnews/54980.htm
- http://m.wap.oexnr.cn/jnews/6944107.htm
- http://m.wap.oexnr.cn/jnews/847758.htm
- http://m.wap.oexnr.cn/jnews/38773.htm
- http://m.wap.oexnr.cn/jnews/5198527.htm
- http://m.wap.oexnr.cn/jnews/23841.htm
- http://m.wap.oexnr.cn/jnews/0474.htm
- http://m.wap.oexnr.cn/jnews/750783.htm
- http://m.wap.oexnr.cn/jnews/3501.htm
- http://m.wap.oexnr.cn/jnews/585584.htm
- http://m.wap.oexnr.cn/jnews/45452.htm
- http://m.wap.oexnr.cn/jnews/0955529.htm
- http://m.wap.oexnr.cn/jnews/69350.htm
- http://m.wap.oexnr.cn/jnews/1710833.htm
- http://m.wap.oexnr.cn/jnews/4986846.htm
- http://m.wap.oexnr.cn/jnews/6254.htm
- http://m.wap.oexnr.cn/jnews/31793.htm
- http://m.wap.oexnr.cn/jnews/008870.htm
- http://m.wap.oexnr.cn/jnews/622882.htm
- http://m.wap.oexnr.cn/jnews/1915.htm
- http://m.wap.oexnr.cn/jnews/103694.htm
- http://m.wap.oexnr.cn/jnews/06797.htm
- http://m.wap.oexnr.cn/jnews/2134405.htm
- http://m.wap.oexnr.cn/jnews/591701.htm
- http://m.wap.oexnr.cn/jnews/97514.htm
- http://m.wap.oexnr.cn/jnews/0443865.htm
- http://m.wap.oexnr.cn/jnews/4376579.htm
- http://m.wap.oexnr.cn/jnews/473986.htm
- http://m.wap.oexnr.cn/jnews/2830494.htm
- http://m.wap.oexnr.cn/jnews/2972.htm
- http://m.wap.oexnr.cn/jnews/502485.htm
- http://m.wap.oexnr.cn/jnews/9883.htm
- http://m.wap.oexnr.cn/jnews/07334.htm
- http://m.wap.oexnr.cn/jnews/796626.htm
- http://m.wap.oexnr.cn/jnews/2750.htm
- http://m.wap.oexnr.cn/jnews/30905.htm
- http://m.wap.oexnr.cn/jnews/8942.htm
- http://m.wap.oexnr.cn/jnews/3259.htm
- http://m.wap.oexnr.cn/jnews/2732.htm
- http://m.wap.oexnr.cn/jnews/4530579.htm
- http://m.wap.oexnr.cn/jnews/460940.htm
- http://m.wap.oexnr.cn/jnews/6521277.htm
- http://m.wap.oexnr.cn/jnews/6652332.htm
- http://m.wap.oexnr.cn/jnews/7655.htm
- http://m.wap.oexnr.cn/jnews/0905.htm
- http://m.wap.oexnr.cn/jnews/3457027.htm
- http://m.wap.oexnr.cn/jnews/605569.htm
- http://m.wap.oexnr.cn/jnews/178766.htm
- http://m.wap.oexnr.cn/jnews/492334.htm
- http://m.wap.oexnr.cn/jnews/0668.htm
- http://m.wap.oexnr.cn/jnews/65039.htm
- http://m.wap.oexnr.cn/jnews/072894.htm
- http://m.wap.oexnr.cn/jnews/7959.htm
- http://m.wap.oexnr.cn/jnews/53797.htm
- http://m.wap.oexnr.cn/jnews/4238535.htm
- http://m.wap.oexnr.cn/jnews/92204.htm
- http://m.wap.oexnr.cn/jnews/67471.htm
- http://m.wap.oexnr.cn/jnews/87158.htm
- http://m.wap.oexnr.cn/jnews/8163940.htm
- http://m.wap.oexnr.cn/jnews/5406811.htm
- http://m.wap.oexnr.cn/jnews/45226.htm
- http://m.wap.oexnr.cn/jnews/6007.htm
- http://m.wap.oexnr.cn/jnews/7409964.htm
- http://m.wap.oexnr.cn/jnews/01366.htm
- http://m.wap.oexnr.cn/jnews/01410.htm
- http://m.wap.oexnr.cn/jnews/9264694.htm
- http://m.wap.oexnr.cn/jnews/17174.htm
- http://m.wap.oexnr.cn/jnews/1980868.htm
- http://m.wap.oexnr.cn/jnews/708663.htm
- http://m.wap.oexnr.cn/jnews/44523.htm
- http://m.wap.oexnr.cn/jnews/1880226.htm
- http://m.wap.oexnr.cn/jnews/6418.htm
- http://m.wap.oexnr.cn/jnews/2229.htm
- http://m.wap.oexnr.cn/jnews/76913.htm
- http://m.wap.oexnr.cn/jnews/1201.htm
- http://m.wap.oexnr.cn/jnews/437091.htm
- http://m.wap.oexnr.cn/jnews/054550.htm
- http://m.wap.oexnr.cn/jnews/3816.htm
- http://m.wap.oexnr.cn/jnews/21649.htm
- http://m.wap.oexnr.cn/jnews/334156.htm
- http://m.wap.oexnr.cn/jnews/729086.htm
- http://m.wap.oexnr.cn/jnews/0869.htm
- http://m.wap.oexnr.cn/jnews/18052.htm
- http://m.wap.oexnr.cn/jnews/046891.htm
- http://m.wap.oexnr.cn/jnews/80599.htm
- http://m.wap.oexnr.cn/jnews/41697.htm
- http://m.wap.oexnr.cn/jnews/680496.htm
- http://m.wap.oexnr.cn/jnews/7183.htm
- http://m.wap.oexnr.cn/jnews/3421847.htm
- http://m.wap.oexnr.cn/jnews/5884.htm
- http://m.wap.oexnr.cn/jnews/01071.htm
- http://m.wap.oexnr.cn/jnews/339433.htm
- http://m.wap.oexnr.cn/jnews/31127.htm
- http://m.wap.oexnr.cn/jnews/0595.htm
- http://m.wap.oexnr.cn/jnews/53931.htm
- http://m.wap.oexnr.cn/jnews/1220.htm
- http://m.wap.oexnr.cn/jnews/4828768.htm
- http://m.wap.oexnr.cn/jnews/5623467.htm
- http://m.wap.oexnr.cn/jnews/8721642.htm
- http://m.wap.oexnr.cn/jnews/96240.htm
- http://m.wap.oexnr.cn/jnews/7096.htm
- http://m.wap.oexnr.cn/jnews/958994.htm
- http://m.wap.oexnr.cn/jnews/2207200.htm
- http://m.wap.oexnr.cn/jnews/6806.htm
- http://m.wap.oexnr.cn/jnews/8905.htm
- http://m.wap.oexnr.cn/jnews/7929730.htm
- http://m.wap.oexnr.cn/jnews/78212.htm
- http://m.wap.oexnr.cn/jnews/5390.htm
- http://m.wap.oexnr.cn/jnews/4010897.htm
- http://m.wap.oexnr.cn/jnews/007553.htm
- http://m.wap.oexnr.cn/jnews/8773237.htm
- http://m.wap.oexnr.cn/jnews/34300.htm
- http://m.wap.oexnr.cn/jnews/819435.htm
- http://m.wap.oexnr.cn/jnews/1850035.htm
- http://m.wap.oexnr.cn/jnews/564472.htm
- http://m.wap.oexnr.cn/jnews/940575.htm
- http://m.wap.oexnr.cn/jnews/7302.htm
- http://m.wap.oexnr.cn/jnews/6954240.htm
- http://m.wap.oexnr.cn/jnews/3087159.htm
- http://m.wap.oexnr.cn/jnews/556728.htm
- http://m.wap.oexnr.cn/jnews/517835.htm
- http://m.wap.oexnr.cn/jnews/15625.htm
- http://m.wap.oexnr.cn/jnews/01384.htm
- http://m.wap.oexnr.cn/jnews/898814.htm
- http://m.wap.oexnr.cn/jnews/29238.htm
- http://m.wap.oexnr.cn/jnews/260216.htm
- http://m.wap.oexnr.cn/jnews/721851.htm
- http://m.wap.oexnr.cn/jnews/318550.htm
- http://m.wap.oexnr.cn/jnews/0710005.htm
- http://m.wap.oexnr.cn/jnews/1693.htm
- http://m.wap.oexnr.cn/jnews/5941223.htm
- http://m.wap.oexnr.cn/jnews/1936384.htm
- http://m.wap.oexnr.cn/jnews/857540.htm
- http://m.wap.oexnr.cn/jnews/9434.htm
- http://m.wap.oexnr.cn/jnews/2073.htm
- http://m.wap.oexnr.cn/jnews/6422341.htm
- http://m.wap.oexnr.cn/jnews/0246787.htm
- http://m.wap.oexnr.cn/jnews/48027.htm
- http://m.wap.oexnr.cn/jnews/3661443.htm
- http://m.wap.oexnr.cn/jnews/971023.htm
- http://m.wap.oexnr.cn/jnews/5691579.htm
- http://m.wap.oexnr.cn/jnews/4640870.htm
- http://m.wap.oexnr.cn/jnews/1459430.htm
- http://m.wap.oexnr.cn/jnews/0609292.htm
- http://m.wap.oexnr.cn/jnews/688181.htm
- http://m.wap.oexnr.cn/jnews/07364.htm
- http://m.wap.oexnr.cn/jnews/82735.htm
- http://m.wap.oexnr.cn/jnews/3161.htm
- http://m.wap.oexnr.cn/jnews/0453.htm
- http://m.wap.oexnr.cn/jnews/332899.htm
- http://m.wap.oexnr.cn/jnews/346653.htm
- http://m.wap.oexnr.cn/jnews/5321849.htm
- http://m.wap.oexnr.cn/jnews/93839.htm
- http://m.wap.oexnr.cn/jnews/5885769.htm
- http://m.wap.oexnr.cn/jnews/5874241.htm
- http://m.wap.oexnr.cn/jnews/849320.htm
- http://m.wap.oexnr.cn/jnews/9807730.htm
- http://m.wap.oexnr.cn/jnews/291476.htm
- http://m.wap.oexnr.cn/jnews/9303421.htm
- http://m.wap.oexnr.cn/jnews/980908.htm
- http://m.wap.oexnr.cn/jnews/89543.htm
- http://m.wap.oexnr.cn/jnews/0929.htm
- http://m.wap.oexnr.cn/jnews/0828761.htm
- http://m.wap.oexnr.cn/jnews/543032.htm
- http://m.wap.oexnr.cn/jnews/7615288.htm
- http://m.wap.oexnr.cn/jnews/11330.htm
- http://m.wap.oexnr.cn/jnews/07105.htm
- http://m.wap.oexnr.cn/jnews/8132.htm
- http://m.wap.oexnr.cn/jnews/893804.htm
- http://m.wap.oexnr.cn/jnews/83461.htm
- http://m.wap.oexnr.cn/jnews/3988453.htm
- http://m.wap.oexnr.cn/jnews/800147.htm
- http://m.wap.oexnr.cn/jnews/869326.htm
- http://m.wap.oexnr.cn/jnews/022743.htm
- http://m.wap.oexnr.cn/jnews/9434676.htm
- http://m.wap.oexnr.cn/jnews/5528.htm
- http://m.wap.oexnr.cn/jnews/147137.htm
- http://m.wap.oexnr.cn/jnews/25361.htm
- http://m.wap.oexnr.cn/jnews/4448414.htm
- http://m.wap.oexnr.cn/jnews/337246.htm
- http://m.wap.oexnr.cn/jnews/297964.htm
- http://m.wap.oexnr.cn/jnews/50661.htm
- http://m.wap.oexnr.cn/jnews/1092663.htm

## 项目结构

```
news-aggregator/
├── cli.py                      # 命令行入口，解析用户参数并调度核心流程
├── config/
│   ├── default.yaml            # 默认配置文件，包含请求头、超时、重试等参数
│   └── logging.conf            # 日志格式与输出级别配置
├── core/
│   ├── __init__.py
│   ├── fetcher.py              # HTTP 请求模块，封装 requests 会话与重试逻辑
│   ├── parser.py               # HTML 解析模块，基于 BeautifulSoup 提取新闻字段
│   ├── validator.py            # 数据校验模块，检查必填字段与内容完整性
│   └── exporter.py             # 数据导出模块，支持 JSON / CSV / SQLite 格式
├── models/
│   ├── __init__.py
│   ├── news_item.py            # 新闻条目数据类定义
│   └── task_queue.py           # 任务队列模型，管理待抓取 URL 列表
├── utils/
│   ├── __init__.py
│   ├── url_utils.py            # URL 解析、拼接与合法性检查工具函数
│   ├── text_utils.py           # 文本清洗、HTML 实体解码与空白压缩
│   └── file_utils.py           # 文件读写、目录创建与路径规范化
├── tests/
│   ├── test_fetcher.py         # 请求模块单元测试
│   ├── test_parser.py          # 解析模块单元测试，覆盖多种页面模板
│   └── test_validator.py       # 校验模块单元测试
├── docs/
│   ├── quickstart.md           # 快速入门指南
│   ├── configuration.md        # 完整配置参数说明
│   ├── parsing_rules.md        # 解析规则维护文档
│   ├── output_formats.md       # 输出格式详细说明
│   ├── api_reference.md        # API 接口文档
│   └── troubleshooting.md      # 故障排查与常见问题解决方案
├── sample_urls.txt             # 示例 URL 列表，用于快速测试
├── requirements.txt            # Python 依赖清单
├── setup.py                    # 项目安装脚本
└── README.md                   # 项目说明文档
```

## 贡献指南

1. 复刻项目仓库至个人账号，在本地创建功能分支，分支命名遵循 feature/功能简述 或 fix/问题简述 的格式。

2. 编写或修改代码后，确保所有单元测试通过，并在 tests 目录下为新增功能补充对应的测试用例，测试覆盖率不低于百分之八十。

3. 提交代码前执行代码风格检查工具 flake8 和格式化工具 black，确保代码符合 PEP 8 规范且无语法警告。

4. 发起合并请求至主仓库的 develop 分支，在合并请求描述中清晰说明变更目的、实现方式及影响范围，并关联相关 issue 编号。

5. 项目维护者会在三个工作日内进行代码审查，如需修改会标注具体行数并反馈修改建议，审查通过后合并至主分支。

## 常见问题

**Q: 抓取过程中部分 URL 返回 403 或 429 状态码，应如何解决？**

A: 此类状态码通常表示源站启用了反爬机制或限流策略。建议调整配置文件中的请求间隔时间，将 concurrency 参数降低至 2 或 3，同时增加 User-Agent 的轮换列表。项目提供了代理配置选项，可通过 proxies 字段接入代理服务池。如持续出现 403，可检查请求头中的 Referer 和 Origin 字段是否与目标域名匹配。

**Q: 解析结果中部分新闻正文内容缺失或包含大量 HTML 标签，如何优化？**

A: 正文缺失通常是因为页面模板结构发生变化，导致原有 CSS 选择器失效。可在 docs/parsing_rules.md 中查看当前规则定义，并自行调整 parser.py 中的选择器配置。对于包含 HTML 标签的内容，项目已集成 text_utils 模块中的清洗函数，可递归提取纯文本并压缩连续空白字符，确保输出内容干净。

**Q: 项目是否支持自定义新闻字段的提取？**

A: 支持。您可以在 models/news_item.py 中扩展 NewsItem 类的字段定义，并在 parser.py 的 parse_article 方法中追加对应的提取逻辑。若需新增输出字段，同步修改 exporter.py 中各格式导出函数的字段映射表即可，无需改动核心调度流程。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
