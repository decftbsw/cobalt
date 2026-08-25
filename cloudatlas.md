# OEXNR News Indexer

OEXNR News Indexer 是一个面向移动端新闻资讯的轻量级索引与归档工具，专注于对 oexnr.cn 域名下发布的新闻条目进行结构化采集、元数据提取与本地检索。该项目主要服务于需要批量分析新闻发布规律、内容分类及时间序列特征的研究者、数据分析师以及资讯聚合平台开发者。

通过 OEXNR News Indexer，用户可以快速获取指定新闻编号对应的原始页面信息，并将其整理为结构化数据以供后续分析。项目本身不包含爬虫框架或分布式调度系统，而是以轻量级脚本形式提供可扩展的解析接口，便于集成至现有数据处理流水线。项目定位为技术辅助工具，不涉及内容存储与分发，仅提供索引与元数据映射能力。

## 功能概览

批量新闻编号解析：支持一次性导入数百个新闻编号，自动解析对应页面的元数据字段，包括标题、发布时间、来源及正文摘要。

本地索引构建：基于解析结果生成 JSON 格式的索引文件，支持按时间、编号范围及关键词进行快速筛选与排序。

可配置的请求限速：内置请求间隔控制参数，避免高频访问对源站造成压力，适用于大规模批次处理场景。

结构化日志输出：每次解析任务均生成详细的操作日志，包含成功记录、失败记录及错误类型分类，便于问题追溯。

命令行交互界面：提供简洁的命令行参数体系，支持单次解析、批次重试及索引导出功能，无需编写额外代码即可完成常见操作。

插件式字段映射：允许用户自定义字段提取规则，通过简单的正则表达式或 XPath 配置适应页面结构的非预期变动。

兼容 Python 3.8 及以上环境：使用标准库及少量第三方依赖，降低部署与迁移成本。

## 应用场景

资讯发布规律分析：研究人员可利用该工具定期拉取新闻编号列表，统计每日发布数量及发布时间分布，从而识别内容发布的高峰时段与周期性模式。

多源聚合平台数据对接：资讯聚合服务商可将该索引器作为前置模块，将解析后的结构化数据推送至自身数据库，实现外部新闻资源的统一管理与展示。

历史数据回溯整理：对于需要整理历史新闻归档的团队，该工具可批量处理过去数年的编号记录，快速生成可用于数据分析的初始数据集。

内容监控与异常检测：通过定时执行索引任务并比对历史记录，可及时发现编号缺失或页面异常等情况，辅助运维人员定位内容发布链路中的潜在问题。

## 快速开始

以下命令演示了从代码仓库克隆、安装依赖到执行首次解析任务的全过程。

```bash
# 克隆项目仓库
git clone https://github.com/example/oexnr-news-indexer.git

# 进入项目目录
cd oexnr-news-indexer

# 创建并激活虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate

# 安装所需依赖
pip install -r requirements.txt

# 执行示例解析任务（使用内置测试编号列表）
python indexer.py --input samples/ids.txt --output data/index.json --delay 1.0
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，低于此版本将导致类型注解与异步特性无法使用 |
| requests | 2.25.0 及以上 | 用于发起 HTTP 请求并获取页面内容，支持连接池与超时控制 |
| lxml | 4.6.0 及以上 | 提供高性能的 HTML 解析与 XPath 查询能力，替代内置 html.parser |
| click | 8.0.0 及以上 | 构建命令行界面，实现参数解析与子命令组织 |
| pytest | 7.0.0 及以上 | 单元测试框架，仅在开发环境中使用，不影响生产部署 |
| loguru | 0.6.0 及以上 | 结构化日志输出库，支持日志分级与文件轮转 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何安装、配置参数、执行解析任务以及导出结果 |
| 开发者指南 | docs/developer-guide.md | 如何扩展字段映射器、添加新的输出格式以及编写测试用例 |
| API 参考 | docs/api-reference.md | 核心类与函数的详细接口说明，包含参数类型与返回值定义 |
| 常见任务 | docs/recipes.md | 针对批量重试、自定义限速策略及索引合并的实操示例 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/1410406.htm
- http://m.wap.oexnr.cn/jnews/3827.htm
- http://m.wap.oexnr.cn/jnews/0098894.htm
- http://m.wap.oexnr.cn/jnews/07005.htm
- http://m.wap.oexnr.cn/jnews/348346.htm
- http://m.wap.oexnr.cn/jnews/0685398.htm
- http://m.wap.oexnr.cn/jnews/92759.htm
- http://m.wap.oexnr.cn/jnews/934205.htm
- http://m.wap.oexnr.cn/jnews/101544.htm
- http://m.wap.oexnr.cn/jnews/5577313.htm
- http://m.wap.oexnr.cn/jnews/74288.htm
- http://m.wap.oexnr.cn/jnews/0426561.htm
- http://m.wap.oexnr.cn/jnews/6348.htm
- http://m.wap.oexnr.cn/jnews/636928.htm
- http://m.wap.oexnr.cn/jnews/0545911.htm
- http://m.wap.oexnr.cn/jnews/463874.htm
- http://m.wap.oexnr.cn/jnews/2871132.htm
- http://m.wap.oexnr.cn/jnews/542118.htm
- http://m.wap.oexnr.cn/jnews/225094.htm
- http://m.wap.oexnr.cn/jnews/065269.htm
- http://m.wap.oexnr.cn/jnews/275906.htm
- http://m.wap.oexnr.cn/jnews/8238555.htm
- http://m.wap.oexnr.cn/jnews/03906.htm
- http://m.wap.oexnr.cn/jnews/66886.htm
- http://m.wap.oexnr.cn/jnews/0874558.htm
- http://m.wap.oexnr.cn/jnews/6632193.htm
- http://m.wap.oexnr.cn/jnews/7597.htm
- http://m.wap.oexnr.cn/jnews/6349370.htm
- http://m.wap.oexnr.cn/jnews/855813.htm
- http://m.wap.oexnr.cn/jnews/14749.htm
- http://m.wap.oexnr.cn/jnews/189564.htm
- http://m.wap.oexnr.cn/jnews/777304.htm
- http://m.wap.oexnr.cn/jnews/34246.htm
- http://m.wap.oexnr.cn/jnews/9126380.htm
- http://m.wap.oexnr.cn/jnews/5870.htm
- http://m.wap.oexnr.cn/jnews/9846.htm
- http://m.wap.oexnr.cn/jnews/95567.htm
- http://m.wap.oexnr.cn/jnews/61811.htm
- http://m.wap.oexnr.cn/jnews/5036159.htm
- http://m.wap.oexnr.cn/jnews/1748773.htm
- http://m.wap.oexnr.cn/jnews/191510.htm
- http://m.wap.oexnr.cn/jnews/0217315.htm
- http://m.wap.oexnr.cn/jnews/3320487.htm
- http://m.wap.oexnr.cn/jnews/035251.htm
- http://m.wap.oexnr.cn/jnews/341482.htm
- http://m.wap.oexnr.cn/jnews/2144583.htm
- http://m.wap.oexnr.cn/jnews/44549.htm
- http://m.wap.oexnr.cn/jnews/2684002.htm
- http://m.wap.oexnr.cn/jnews/5720.htm
- http://m.wap.oexnr.cn/jnews/684112.htm
- http://m.wap.oexnr.cn/jnews/99612.htm
- http://m.wap.oexnr.cn/jnews/4489.htm
- http://m.wap.oexnr.cn/jnews/1920324.htm
- http://m.wap.oexnr.cn/jnews/35123.htm
- http://m.wap.oexnr.cn/jnews/8087.htm
- http://m.wap.oexnr.cn/jnews/441546.htm
- http://m.wap.oexnr.cn/jnews/881325.htm
- http://m.wap.oexnr.cn/jnews/295373.htm
- http://m.wap.oexnr.cn/jnews/5891953.htm
- http://m.wap.oexnr.cn/jnews/774158.htm
- http://m.wap.oexnr.cn/jnews/82023.htm
- http://m.wap.oexnr.cn/jnews/171110.htm
- http://m.wap.oexnr.cn/jnews/085290.htm
- http://m.wap.oexnr.cn/jnews/0612.htm
- http://m.wap.oexnr.cn/jnews/364337.htm
- http://m.wap.oexnr.cn/jnews/2300.htm
- http://m.wap.oexnr.cn/jnews/9076111.htm
- http://m.wap.oexnr.cn/jnews/56347.htm
- http://m.wap.oexnr.cn/jnews/57925.htm
- http://m.wap.oexnr.cn/jnews/9322.htm
- http://m.wap.oexnr.cn/jnews/371189.htm
- http://m.wap.oexnr.cn/jnews/12326.htm
- http://m.wap.oexnr.cn/jnews/4247067.htm
- http://m.wap.oexnr.cn/jnews/608992.htm
- http://m.wap.oexnr.cn/jnews/445147.htm
- http://m.wap.oexnr.cn/jnews/522644.htm
- http://m.wap.oexnr.cn/jnews/8272.htm
- http://m.wap.oexnr.cn/jnews/1955.htm
- http://m.wap.oexnr.cn/jnews/5383937.htm
- http://m.wap.oexnr.cn/jnews/75028.htm
- http://m.wap.oexnr.cn/jnews/430080.htm
- http://m.wap.oexnr.cn/jnews/1603.htm
- http://m.wap.oexnr.cn/jnews/81586.htm
- http://m.wap.oexnr.cn/jnews/5692.htm
- http://m.wap.oexnr.cn/jnews/1352.htm
- http://m.wap.oexnr.cn/jnews/336346.htm
- http://m.wap.oexnr.cn/jnews/8954.htm
- http://m.wap.oexnr.cn/jnews/187796.htm
- http://m.wap.oexnr.cn/jnews/78621.htm
- http://m.wap.oexnr.cn/jnews/793730.htm
- http://m.wap.oexnr.cn/jnews/85727.htm
- http://m.wap.oexnr.cn/jnews/1945815.htm
- http://m.wap.oexnr.cn/jnews/4167523.htm
- http://m.wap.oexnr.cn/jnews/68326.htm
- http://m.wap.oexnr.cn/jnews/049345.htm
- http://m.wap.oexnr.cn/jnews/1069.htm
- http://m.wap.oexnr.cn/jnews/74517.htm
- http://m.wap.oexnr.cn/jnews/43377.htm
- http://m.wap.oexnr.cn/jnews/2508426.htm
- http://m.wap.oexnr.cn/jnews/5137.htm
- http://m.wap.oexnr.cn/jnews/2131.htm
- http://m.wap.oexnr.cn/jnews/3358.htm
- http://m.wap.oexnr.cn/jnews/912004.htm
- http://m.wap.oexnr.cn/jnews/72363.htm
- http://m.wap.oexnr.cn/jnews/98183.htm
- http://m.wap.oexnr.cn/jnews/1184047.htm
- http://m.wap.oexnr.cn/jnews/9763.htm
- http://m.wap.oexnr.cn/jnews/58261.htm
- http://m.wap.oexnr.cn/jnews/4549531.htm
- http://m.wap.oexnr.cn/jnews/7085239.htm
- http://m.wap.oexnr.cn/jnews/20796.htm
- http://m.wap.oexnr.cn/jnews/6496752.htm
- http://m.wap.oexnr.cn/jnews/991262.htm
- http://m.wap.oexnr.cn/jnews/62699.htm
- http://m.wap.oexnr.cn/jnews/22882.htm
- http://m.wap.oexnr.cn/jnews/4962.htm
- http://m.wap.oexnr.cn/jnews/04286.htm
- http://m.wap.oexnr.cn/jnews/99831.htm
- http://m.wap.oexnr.cn/jnews/05428.htm
- http://m.wap.oexnr.cn/jnews/5253385.htm
- http://m.wap.oexnr.cn/jnews/342292.htm
- http://m.wap.oexnr.cn/jnews/5822.htm
- http://m.wap.oexnr.cn/jnews/377124.htm
- http://m.wap.oexnr.cn/jnews/0118751.htm
- http://m.wap.oexnr.cn/jnews/6984.htm
- http://m.wap.oexnr.cn/jnews/710340.htm
- http://m.wap.oexnr.cn/jnews/613362.htm
- http://m.wap.oexnr.cn/jnews/2102270.htm
- http://m.wap.oexnr.cn/jnews/767684.htm
- http://m.wap.oexnr.cn/jnews/9930.htm
- http://m.wap.oexnr.cn/jnews/0885916.htm
- http://m.wap.oexnr.cn/jnews/8656.htm
- http://m.wap.oexnr.cn/jnews/4667159.htm
- http://m.wap.oexnr.cn/jnews/42192.htm
- http://m.wap.oexnr.cn/jnews/0816575.htm
- http://m.wap.oexnr.cn/jnews/05596.htm
- http://m.wap.oexnr.cn/jnews/40078.htm
- http://m.wap.oexnr.cn/jnews/614449.htm
- http://m.wap.oexnr.cn/jnews/4729952.htm
- http://m.wap.oexnr.cn/jnews/05703.htm
- http://m.wap.oexnr.cn/jnews/444797.htm
- http://m.wap.oexnr.cn/jnews/928109.htm
- http://m.wap.oexnr.cn/jnews/92140.htm
- http://m.wap.oexnr.cn/jnews/73459.htm
- http://m.wap.oexnr.cn/jnews/25049.htm
- http://m.wap.oexnr.cn/jnews/60006.htm
- http://m.wap.oexnr.cn/jnews/3338.htm
- http://m.wap.oexnr.cn/jnews/05955.htm
- http://m.wap.oexnr.cn/jnews/18215.htm
- http://m.wap.oexnr.cn/jnews/5772.htm
- http://m.wap.oexnr.cn/jnews/95723.htm
- http://m.wap.oexnr.cn/jnews/38522.htm
- http://m.wap.oexnr.cn/jnews/4636435.htm
- http://m.wap.oexnr.cn/jnews/0563615.htm
- http://m.wap.oexnr.cn/jnews/6804410.htm
- http://m.wap.oexnr.cn/jnews/57297.htm
- http://m.wap.oexnr.cn/jnews/2252.htm
- http://m.wap.oexnr.cn/jnews/93060.htm
- http://m.wap.oexnr.cn/jnews/9457.htm
- http://m.wap.oexnr.cn/jnews/3502706.htm
- http://m.wap.oexnr.cn/jnews/3646.htm
- http://m.wap.oexnr.cn/jnews/2378166.htm
- http://m.wap.oexnr.cn/jnews/267016.htm
- http://m.wap.oexnr.cn/jnews/082810.htm
- http://m.wap.oexnr.cn/jnews/6544.htm
- http://m.wap.oexnr.cn/jnews/847304.htm
- http://m.wap.oexnr.cn/jnews/279355.htm
- http://m.wap.oexnr.cn/jnews/7685.htm
- http://m.wap.oexnr.cn/jnews/7400.htm
- http://m.wap.oexnr.cn/jnews/3955.htm
- http://m.wap.oexnr.cn/jnews/4460151.htm
- http://m.wap.oexnr.cn/jnews/1020.htm
- http://m.wap.oexnr.cn/jnews/215587.htm
- http://m.wap.oexnr.cn/jnews/8264.htm
- http://m.wap.oexnr.cn/jnews/2727.htm
- http://m.wap.oexnr.cn/jnews/4369.htm
- http://m.wap.oexnr.cn/jnews/41091.htm
- http://m.wap.oexnr.cn/jnews/49811.htm
- http://m.wap.oexnr.cn/jnews/9290412.htm
- http://m.wap.oexnr.cn/jnews/6485867.htm
- http://m.wap.oexnr.cn/jnews/091895.htm
- http://m.wap.oexnr.cn/jnews/156556.htm
- http://m.wap.oexnr.cn/jnews/4751324.htm
- http://m.wap.oexnr.cn/jnews/1671384.htm
- http://m.wap.oexnr.cn/jnews/2592.htm
- http://m.wap.oexnr.cn/jnews/3869.htm
- http://m.wap.oexnr.cn/jnews/48351.htm
- http://m.wap.oexnr.cn/jnews/42705.htm
- http://m.wap.oexnr.cn/jnews/4066814.htm
- http://m.wap.oexnr.cn/jnews/1181021.htm
- http://m.wap.oexnr.cn/jnews/5318187.htm
- http://m.wap.oexnr.cn/jnews/378440.htm
- http://m.wap.oexnr.cn/jnews/2894817.htm
- http://m.wap.oexnr.cn/jnews/78909.htm
- http://m.wap.oexnr.cn/jnews/6657048.htm
- http://m.wap.oexnr.cn/jnews/6597.htm
- http://m.wap.oexnr.cn/jnews/4398.htm
- http://m.wap.oexnr.cn/jnews/709503.htm
- http://m.wap.oexnr.cn/jnews/685347.htm
- http://m.wap.oexnr.cn/jnews/997310.htm
- http://m.wap.oexnr.cn/jnews/874294.htm
- http://m.wap.oexnr.cn/jnews/4487954.htm
- http://m.wap.oexnr.cn/jnews/99691.htm
- http://m.wap.oexnr.cn/jnews/0323.htm
- http://m.wap.oexnr.cn/jnews/12855.htm
- http://m.wap.oexnr.cn/jnews/617419.htm
- http://m.wap.oexnr.cn/jnews/0443328.htm
- http://m.wap.oexnr.cn/jnews/1801.htm
- http://m.wap.oexnr.cn/jnews/7499.htm
- http://m.wap.oexnr.cn/jnews/2190.htm
- http://m.wap.oexnr.cn/jnews/831936.htm
- http://m.wap.oexnr.cn/jnews/752918.htm
- http://m.wap.oexnr.cn/jnews/5953272.htm
- http://m.wap.oexnr.cn/jnews/8663.htm
- http://m.wap.oexnr.cn/jnews/398167.htm
- http://m.wap.oexnr.cn/jnews/594376.htm
- http://m.wap.oexnr.cn/jnews/5313.htm
- http://m.wap.oexnr.cn/jnews/0777827.htm
- http://m.wap.oexnr.cn/jnews/7030.htm
- http://m.wap.oexnr.cn/jnews/21582.htm
- http://m.wap.oexnr.cn/jnews/53148.htm
- http://m.wap.oexnr.cn/jnews/981909.htm
- http://m.wap.oexnr.cn/jnews/3963.htm
- http://m.wap.oexnr.cn/jnews/1132.htm
- http://m.wap.oexnr.cn/jnews/210584.htm
- http://m.wap.oexnr.cn/jnews/1431.htm
- http://m.wap.oexnr.cn/jnews/2952.htm
- http://m.wap.oexnr.cn/jnews/68710.htm
- http://m.wap.oexnr.cn/jnews/88916.htm
- http://m.wap.oexnr.cn/jnews/8853.htm
- http://m.wap.oexnr.cn/jnews/0662.htm
- http://m.wap.oexnr.cn/jnews/863591.htm
- http://m.wap.oexnr.cn/jnews/62452.htm
- http://m.wap.oexnr.cn/jnews/01797.htm
- http://m.wap.oexnr.cn/jnews/48003.htm
- http://m.wap.oexnr.cn/jnews/6175703.htm
- http://m.wap.oexnr.cn/jnews/69173.htm
- http://m.wap.oexnr.cn/jnews/04042.htm
- http://m.wap.oexnr.cn/jnews/4132568.htm
- http://m.wap.oexnr.cn/jnews/002520.htm
- http://m.wap.oexnr.cn/jnews/5646.htm
- http://m.wap.oexnr.cn/jnews/15454.htm
- http://m.wap.oexnr.cn/jnews/5144.htm
- http://m.wap.oexnr.cn/jnews/225860.htm
- http://m.wap.oexnr.cn/jnews/269224.htm
- http://m.wap.oexnr.cn/jnews/83921.htm
- http://m.wap.oexnr.cn/jnews/3894774.htm
- http://m.wap.oexnr.cn/jnews/3617.htm
- http://m.wap.oexnr.cn/jnews/796654.htm
- http://m.wap.oexnr.cn/jnews/012117.htm
- http://m.wap.oexnr.cn/jnews/3108246.htm
- http://m.wap.oexnr.cn/jnews/131047.htm
- http://m.wap.oexnr.cn/jnews/6222.htm
- http://m.wap.oexnr.cn/jnews/6740937.htm
- http://m.wap.oexnr.cn/jnews/4533457.htm
- http://m.wap.oexnr.cn/jnews/93676.htm
- http://m.wap.oexnr.cn/jnews/385110.htm
- http://m.wap.oexnr.cn/jnews/7362919.htm
- http://m.wap.oexnr.cn/jnews/9910774.htm
- http://m.wap.oexnr.cn/jnews/886127.htm
- http://m.wap.oexnr.cn/jnews/9266145.htm
- http://m.wap.oexnr.cn/jnews/84652.htm
- http://m.wap.oexnr.cn/jnews/8915.htm
- http://m.wap.oexnr.cn/jnews/024639.htm
- http://m.wap.oexnr.cn/jnews/8670553.htm
- http://m.wap.oexnr.cn/jnews/0933312.htm
- http://m.wap.oexnr.cn/jnews/20605.htm
- http://m.wap.oexnr.cn/jnews/5077.htm
- http://m.wap.oexnr.cn/jnews/9066.htm
- http://m.wap.oexnr.cn/jnews/7874318.htm
- http://m.wap.oexnr.cn/jnews/2637.htm
- http://m.wap.oexnr.cn/jnews/7540679.htm
- http://m.wap.oexnr.cn/jnews/4420.htm
- http://m.wap.oexnr.cn/jnews/364669.htm
- http://m.wap.oexnr.cn/jnews/44682.htm
- http://m.wap.oexnr.cn/jnews/235220.htm
- http://m.wap.oexnr.cn/jnews/4404.htm
- http://m.wap.oexnr.cn/jnews/2289181.htm
- http://m.wap.oexnr.cn/jnews/69569.htm
- http://m.wap.oexnr.cn/jnews/4238.htm
- http://m.wap.oexnr.cn/jnews/380427.htm
- http://m.wap.oexnr.cn/jnews/776849.htm
- http://m.wap.oexnr.cn/jnews/91448.htm
- http://m.wap.oexnr.cn/jnews/87303.htm
- http://m.wap.oexnr.cn/jnews/6431.htm
- http://m.wap.oexnr.cn/jnews/9393.htm
- http://m.wap.oexnr.cn/jnews/3064.htm
- http://m.wap.oexnr.cn/jnews/576869.htm
- http://m.wap.oexnr.cn/jnews/094977.htm
- http://m.wap.oexnr.cn/jnews/4549.htm
- http://m.wap.oexnr.cn/jnews/0706319.htm
- http://m.wap.oexnr.cn/jnews/3905.htm
- http://m.wap.oexnr.cn/jnews/8825547.htm
- http://m.wap.oexnr.cn/jnews/8118147.htm
- http://m.wap.oexnr.cn/jnews/953219.htm
- http://m.wap.oexnr.cn/jnews/2611.htm
- http://m.wap.oexnr.cn/jnews/1775.htm
- http://m.wap.oexnr.cn/jnews/5373451.htm
- http://m.wap.oexnr.cn/jnews/949816.htm
- http://m.wap.oexnr.cn/jnews/9422134.htm

## 项目结构

```
oexnr-news-indexer/
├── indexer.py                 # 主入口脚本，负责命令行参数解析与任务调度
├── requirements.txt           # 生产环境依赖列表，固定版本号以保障可复现性
├── config.yaml                # 全局配置文件，包含请求头、超时时间与重试策略
├── src/                       # 核心源码目录
│   ├── parser/                # 页面解析模块
│   │   ├── base.py            # 定义抽象解析器基类与通用字段映射接口
│   │   └── oexnr_parser.py    # 针对 oexnr.cn 页面结构的专用解析实现
│   ├── fetcher/               # 网络请求模块
│   │   ├── client.py          # 封装 requests.Session，管理连接池与 cookie
│   │   └── limiter.py         # 实现请求速率控制器，支持令牌桶算法
│   ├── exporter/              # 索引导出模块
│   │   ├── json_exporter.py   # 将解析结果序列化为 JSON 格式文件
│   │   └── csv_exporter.py    # 输出 CSV 格式，兼容电子表格软件
│   ├── logger/                # 日志模块
│   │   └── logger_factory.py  # 基于 loguru 的日志工厂，支持多级别输出
│   └── utils/                 # 通用工具函数
│       ├── validators.py      # 编号格式校验与类型转换
│       └── file_helpers.py    # 文件读取、写入及路径处理辅助
├── tests/                     # 单元测试目录
│   ├── test_parser.py         # 解析器功能测试，覆盖正常与异常输入
│   ├── test_fetcher.py        # 请求客户端与限速器单元测试
│   └── fixtures/              # 测试用静态页面样本
├── samples/                   # 示例输入输出
│   ├── ids.txt                # 示例新闻编号列表，每行一个编号
│   └── expected/              # 预期的解析结果样例
└── docs/                      # 文档目录
    ├── user-guide.md          # 用户手册
    ├── developer-guide.md     # 开发者指南
    ├── api-reference.md       # API 参考文档
    └── recipes.md             # 常见任务解决方案
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账号，并克隆至本地开发环境。建议在 dev 分支基础上创建功能分支，命名格式为 feature/简述修改内容。

2. 安装开发依赖：执行 `pip install -r requirements-dev.txt`，该文件包含 pytest、black、flake8 及 mypy 等代码质量工具。运行 `pre-commit install` 启用提交前自动检查。

3. 编写或修改代码时，请遵循项目约定的代码风格（black 默认配置）与类型注解规范。新增解析器或导出器时，需在对应模块的 `__init__.py` 中注册类名。

4. 编写单元测试覆盖新增功能或修复的缺陷，确保 `pytest tests/` 全部通过且测试覆盖率不低于 85%。测试用例需包含正向验证与边界条件。

5. 提交 pull request 前，请更新相关文档（用户手册或 API 参考），并在 PR 描述中明确说明修改目的、影响范围及测试结果。等待至少一位维护者审核通过后合并。

## 常见问题

**Q: 解析任务执行过程中出现超时错误，应如何处理？**

A: 超时通常由网络波动或源站响应缓慢引起。建议首先检查 `config.yaml` 中的 `timeout` 字段，默认值为 10 秒，可适当增加至 30 秒。同时确保 `delay` 参数不低于 1.0 秒，避免并发过高导致请求被拒绝。若问题持续存在，可使用 `--retry` 参数启用自动重试机制，重试次数可通过 `--max-retries` 调整。

**Q: 索引文件中的部分字段为空或解析结果不符合预期，如何调试？**

A: 首先检查日志输出中的 WARNING 或 ERROR 级别信息，日志会记录解析失败的具体原因。若页面结构发生变动，需调整解析器中的 XPath 或正则表达式规则。建议使用 `--debug` 参数运行任务，该模式会输出每个页面的原始 HTML 摘要与解析中间结果。用户也可在 `src/parser/oexnr_parser.py` 中自定义 `extract` 方法的实现以适配新的页面布局。

**Q: 项目是否支持分布式部署或大规模并发解析？**

A: 当前版本定位为单机轻量级工具，未内置分布式调度能力。对于大规模批次（超过 10000 个编号），建议将输入列表分批，并在不同机器或进程间独立执行，最后通过 `exporter` 模块提供的 `merge` 功能合并索引文件。未来版本计划引入消息队列集成，以支持更灵活的水平扩展。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
