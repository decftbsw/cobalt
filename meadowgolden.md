# Oexnr News Resource Aggregator

Oexnr News Resource Aggregator 是一个面向移动端新闻资讯聚合的开源工具集，旨在为开发者、数据分析师和内容研究者提供系统化的新闻页面采集、解析与元数据提取能力。该项目围绕 m.wap.oexnr.cn 域名下的新闻资源构建，通过结构化的 URL 模式与轻量级抓取框架，帮助用户高效获取海量新闻条目并纳入自有工作流。

本项目定位于技术资源与外链汇总中间件，不对新闻内容本身进行存储或改写，而是提供标准化的访问入口、采集脚本示例和元数据结构定义。目标用户包括从事舆情分析、新闻聚合应用开发、内容推荐算法研究的工程师与研究人员。通过本项目的工具链，用户可以在数分钟内完成从 URL 列表导入到结构化数据输出的完整流程，显著降低新闻数据采集的初始门槛。

## 功能概览

批量 URL 导入与校验 提供基于文本文件和 CSV 格式的批量 URL 输入接口，自动校验链接可达性与响应状态码。

结构化元数据提取 从新闻页面中提取标题、发布时间、正文摘要、来源等核心字段，输出 JSON 与 CSV 格式。

请求频率控制与重试机制 内置可配置的请求间隔、并发上限和指数退避重试策略，避免对源站造成压力。

移动端页面适配解析 针对移动端 HTML 结构进行针对性解析，支持常见移动端广告与冗余元素过滤。

数据导出与管道集成 支持将采集结果导出至本地文件系统、标准输出或通过 HTTP 回调推送至指定端点。

日志与监控接口 提供结构化日志输出和关键指标计数器，便于集成到 Prometheus 或 ELK 等监控体系。

扩展插件系统 支持通过 Python 脚本或 Lua 钩子自定义解析逻辑、字段映射和输出格式。

## 应用场景

舆情监控与热点追踪 研究人员可利用本工具定期抓取指定新闻 URL 列表，提取标题与发布时间，构建时间序列热词分析模型，实时掌握特定领域的话题趋势。

新闻推荐系统数据源构建 推荐算法工程师可将本工具作为冷启动数据管道的一部分，批量获取新闻元数据，结合内容标签系统生成用户兴趣特征向量。

移动端内容聚合应用开发 移动应用开发者可使用本工具提供的解析模板，快速集成第三方新闻内容展示模块，减少针对不同移动站点的适配工作量。

历史新闻归档与回溯分析 数据分析师可借助批量 URL 导入功能，对历史新闻条目进行系统性采集和归档，用于长周期内容演变研究或事件追溯。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/oexnr-news-aggregator.git

# 进入项目目录
cd oexnr-news-aggregator

# 安装依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行基础采集示例（使用默认 URL 列表）
python cli.py --input urls.txt --output data.json --format json --delay 0.5
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 LTS |
| requests | 2.28.0 及以上 | HTTP 请求库，用于页面抓取 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于移动端页面结构分析 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，作为 BeautifulSoup 后端 |
| pandas | 1.5.0 及以上 | 可选依赖，用于 CSV 导出和数据分析辅助 |
| pytest | 7.0.0 及以上 | 开发依赖，用于单元测试和集成测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何安装、配置并运行第一个采集任务 |
| 配置参考 | docs/configuration.md | 所有命令行参数、环境变量和配置文件选项的详细说明 |
| 解析器开发 | docs/parser_development.md | 如何为新的新闻站点编写自定义解析插件 |
| API 接口 | docs/api_reference.md | 核心模块的函数签名、类结构和调用示例 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/8933.htm
- http://m.wap.oexnr.cn/jnews/6224.htm
- http://m.wap.oexnr.cn/jnews/7956.htm
- http://m.wap.oexnr.cn/jnews/841317.htm
- http://m.wap.oexnr.cn/jnews/978102.htm
- http://m.wap.oexnr.cn/jnews/8764906.htm
- http://m.wap.oexnr.cn/jnews/140974.htm
- http://m.wap.oexnr.cn/jnews/71738.htm
- http://m.wap.oexnr.cn/jnews/141502.htm
- http://m.wap.oexnr.cn/jnews/4433.htm
- http://m.wap.oexnr.cn/jnews/07687.htm
- http://m.wap.oexnr.cn/jnews/1688356.htm
- http://m.wap.oexnr.cn/jnews/45171.htm
- http://m.wap.oexnr.cn/jnews/99640.htm
- http://m.wap.oexnr.cn/jnews/1799.htm
- http://m.wap.oexnr.cn/jnews/7466137.htm
- http://m.wap.oexnr.cn/jnews/993897.htm
- http://m.wap.oexnr.cn/jnews/492074.htm
- http://m.wap.oexnr.cn/jnews/5677766.htm
- http://m.wap.oexnr.cn/jnews/5881.htm
- http://m.wap.oexnr.cn/jnews/8279.htm
- http://m.wap.oexnr.cn/jnews/43649.htm
- http://m.wap.oexnr.cn/jnews/6611341.htm
- http://m.wap.oexnr.cn/jnews/3429.htm
- http://m.wap.oexnr.cn/jnews/0472838.htm
- http://m.wap.oexnr.cn/jnews/915792.htm
- http://m.wap.oexnr.cn/jnews/14611.htm
- http://m.wap.oexnr.cn/jnews/7768751.htm
- http://m.wap.oexnr.cn/jnews/7104.htm
- http://m.wap.oexnr.cn/jnews/652877.htm
- http://m.wap.oexnr.cn/jnews/9945823.htm
- http://m.wap.oexnr.cn/jnews/6415912.htm
- http://m.wap.oexnr.cn/jnews/02251.htm
- http://m.wap.oexnr.cn/jnews/78160.htm
- http://m.wap.oexnr.cn/jnews/1905.htm
- http://m.wap.oexnr.cn/jnews/2856968.htm
- http://m.wap.oexnr.cn/jnews/63280.htm
- http://m.wap.oexnr.cn/jnews/73973.htm
- http://m.wap.oexnr.cn/jnews/0720870.htm
- http://m.wap.oexnr.cn/jnews/1206762.htm
- http://m.wap.oexnr.cn/jnews/5708.htm
- http://m.wap.oexnr.cn/jnews/57155.htm
- http://m.wap.oexnr.cn/jnews/56649.htm
- http://m.wap.oexnr.cn/jnews/603393.htm
- http://m.wap.oexnr.cn/jnews/10853.htm
- http://m.wap.oexnr.cn/jnews/7749.htm
- http://m.wap.oexnr.cn/jnews/4763.htm
- http://m.wap.oexnr.cn/jnews/8474.htm
- http://m.wap.oexnr.cn/jnews/765145.htm
- http://m.wap.oexnr.cn/jnews/4834.htm
- http://m.wap.oexnr.cn/jnews/8346.htm
- http://m.wap.oexnr.cn/jnews/875281.htm
- http://m.wap.oexnr.cn/jnews/996325.htm
- http://m.wap.oexnr.cn/jnews/33883.htm
- http://m.wap.oexnr.cn/jnews/040293.htm
- http://m.wap.oexnr.cn/jnews/94255.htm
- http://m.wap.oexnr.cn/jnews/287507.htm
- http://m.wap.oexnr.cn/jnews/8206.htm
- http://m.wap.oexnr.cn/jnews/860486.htm
- http://m.wap.oexnr.cn/jnews/836455.htm
- http://m.wap.oexnr.cn/jnews/5848.htm
- http://m.wap.oexnr.cn/jnews/0825.htm
- http://m.wap.oexnr.cn/jnews/0860.htm
- http://m.wap.oexnr.cn/jnews/771405.htm
- http://m.wap.oexnr.cn/jnews/5480620.htm
- http://m.wap.oexnr.cn/jnews/9948.htm
- http://m.wap.oexnr.cn/jnews/6217956.htm
- http://m.wap.oexnr.cn/jnews/357853.htm
- http://m.wap.oexnr.cn/jnews/53263.htm
- http://m.wap.oexnr.cn/jnews/3138.htm
- http://m.wap.oexnr.cn/jnews/1690.htm
- http://m.wap.oexnr.cn/jnews/3317476.htm
- http://m.wap.oexnr.cn/jnews/51973.htm
- http://m.wap.oexnr.cn/jnews/0501629.htm
- http://m.wap.oexnr.cn/jnews/7212389.htm
- http://m.wap.oexnr.cn/jnews/9051453.htm
- http://m.wap.oexnr.cn/jnews/0650894.htm
- http://m.wap.oexnr.cn/jnews/2236.htm
- http://m.wap.oexnr.cn/jnews/12315.htm
- http://m.wap.oexnr.cn/jnews/07911.htm
- http://m.wap.oexnr.cn/jnews/1317.htm
- http://m.wap.oexnr.cn/jnews/23630.htm
- http://m.wap.oexnr.cn/jnews/2795.htm
- http://m.wap.oexnr.cn/jnews/3132762.htm
- http://m.wap.oexnr.cn/jnews/1825.htm
- http://m.wap.oexnr.cn/jnews/42002.htm
- http://m.wap.oexnr.cn/jnews/91901.htm
- http://m.wap.oexnr.cn/jnews/26346.htm
- http://m.wap.oexnr.cn/jnews/35010.htm
- http://m.wap.oexnr.cn/jnews/5593809.htm
- http://m.wap.oexnr.cn/jnews/5639075.htm
- http://m.wap.oexnr.cn/jnews/9793335.htm
- http://m.wap.oexnr.cn/jnews/6741.htm
- http://m.wap.oexnr.cn/jnews/64316.htm
- http://m.wap.oexnr.cn/jnews/28631.htm
- http://m.wap.oexnr.cn/jnews/9704159.htm
- http://m.wap.oexnr.cn/jnews/8652832.htm
- http://m.wap.oexnr.cn/jnews/08352.htm
- http://m.wap.oexnr.cn/jnews/422295.htm
- http://m.wap.oexnr.cn/jnews/2017057.htm
- http://m.wap.oexnr.cn/jnews/68661.htm
- http://m.wap.oexnr.cn/jnews/31466.htm
- http://m.wap.oexnr.cn/jnews/5001.htm
- http://m.wap.oexnr.cn/jnews/0659.htm
- http://m.wap.oexnr.cn/jnews/65086.htm
- http://m.wap.oexnr.cn/jnews/42869.htm
- http://m.wap.oexnr.cn/jnews/432207.htm
- http://m.wap.oexnr.cn/jnews/2489016.htm
- http://m.wap.oexnr.cn/jnews/9099721.htm
- http://m.wap.oexnr.cn/jnews/743890.htm
- http://m.wap.oexnr.cn/jnews/659625.htm
- http://m.wap.oexnr.cn/jnews/363858.htm
- http://m.wap.oexnr.cn/jnews/81314.htm
- http://m.wap.oexnr.cn/jnews/44797.htm
- http://m.wap.oexnr.cn/jnews/3224121.htm
- http://m.wap.oexnr.cn/jnews/032734.htm
- http://m.wap.oexnr.cn/jnews/1411562.htm
- http://m.wap.oexnr.cn/jnews/6970093.htm
- http://m.wap.oexnr.cn/jnews/911218.htm
- http://m.wap.oexnr.cn/jnews/9529.htm
- http://m.wap.oexnr.cn/jnews/1425.htm
- http://m.wap.oexnr.cn/jnews/82236.htm
- http://m.wap.oexnr.cn/jnews/917000.htm
- http://m.wap.oexnr.cn/jnews/783098.htm
- http://m.wap.oexnr.cn/jnews/286065.htm
- http://m.wap.oexnr.cn/jnews/165285.htm
- http://m.wap.oexnr.cn/jnews/9471.htm
- http://m.wap.oexnr.cn/jnews/9668803.htm
- http://m.wap.oexnr.cn/jnews/9497827.htm
- http://m.wap.oexnr.cn/jnews/4004805.htm
- http://m.wap.oexnr.cn/jnews/4805.htm
- http://m.wap.oexnr.cn/jnews/63951.htm
- http://m.wap.oexnr.cn/jnews/5217327.htm
- http://m.wap.oexnr.cn/jnews/93319.htm
- http://m.wap.oexnr.cn/jnews/2002.htm
- http://m.wap.oexnr.cn/jnews/4430.htm
- http://m.wap.oexnr.cn/jnews/4761.htm
- http://m.wap.oexnr.cn/jnews/6756356.htm
- http://m.wap.oexnr.cn/jnews/17905.htm
- http://m.wap.oexnr.cn/jnews/2666619.htm
- http://m.wap.oexnr.cn/jnews/865895.htm
- http://m.wap.oexnr.cn/jnews/808631.htm
- http://m.wap.oexnr.cn/jnews/115003.htm
- http://m.wap.oexnr.cn/jnews/4971444.htm
- http://m.wap.oexnr.cn/jnews/68140.htm
- http://m.wap.oexnr.cn/jnews/18312.htm
- http://m.wap.oexnr.cn/jnews/6828.htm
- http://m.wap.oexnr.cn/jnews/60434.htm
- http://m.wap.oexnr.cn/jnews/397843.htm
- http://m.wap.oexnr.cn/jnews/2383598.htm
- http://m.wap.oexnr.cn/jnews/2855.htm
- http://m.wap.oexnr.cn/jnews/240367.htm
- http://m.wap.oexnr.cn/jnews/0292621.htm
- http://m.wap.oexnr.cn/jnews/8757.htm
- http://m.wap.oexnr.cn/jnews/245844.htm
- http://m.wap.oexnr.cn/jnews/307092.htm
- http://m.wap.oexnr.cn/jnews/20981.htm
- http://m.wap.oexnr.cn/jnews/48353.htm
- http://m.wap.oexnr.cn/jnews/987100.htm
- http://m.wap.oexnr.cn/jnews/955827.htm
- http://m.wap.oexnr.cn/jnews/71313.htm
- http://m.wap.oexnr.cn/jnews/29395.htm
- http://m.wap.oexnr.cn/jnews/100696.htm
- http://m.wap.oexnr.cn/jnews/4004617.htm
- http://m.wap.oexnr.cn/jnews/0323000.htm
- http://m.wap.oexnr.cn/jnews/2954.htm
- http://m.wap.oexnr.cn/jnews/0878.htm
- http://m.wap.oexnr.cn/jnews/37509.htm
- http://m.wap.oexnr.cn/jnews/3540673.htm
- http://m.wap.oexnr.cn/jnews/94829.htm
- http://m.wap.oexnr.cn/jnews/6279.htm
- http://m.wap.oexnr.cn/jnews/2655.htm
- http://m.wap.oexnr.cn/jnews/4586.htm
- http://m.wap.oexnr.cn/jnews/8108.htm
- http://m.wap.oexnr.cn/jnews/46391.htm
- http://m.wap.oexnr.cn/jnews/7485092.htm
- http://m.wap.oexnr.cn/jnews/253848.htm
- http://m.wap.oexnr.cn/jnews/6921115.htm
- http://m.wap.oexnr.cn/jnews/10775.htm
- http://m.wap.oexnr.cn/jnews/7348.htm
- http://m.wap.oexnr.cn/jnews/96164.htm
- http://m.wap.oexnr.cn/jnews/133062.htm
- http://m.wap.oexnr.cn/jnews/4209.htm
- http://m.wap.oexnr.cn/jnews/4145936.htm
- http://m.wap.oexnr.cn/jnews/29647.htm
- http://m.wap.oexnr.cn/jnews/8091.htm
- http://m.wap.oexnr.cn/jnews/3693.htm
- http://m.wap.oexnr.cn/jnews/8244.htm
- http://m.wap.oexnr.cn/jnews/46700.htm
- http://m.wap.oexnr.cn/jnews/067072.htm
- http://m.wap.oexnr.cn/jnews/1185.htm
- http://m.wap.oexnr.cn/jnews/1581449.htm
- http://m.wap.oexnr.cn/jnews/0463.htm
- http://m.wap.oexnr.cn/jnews/86400.htm
- http://m.wap.oexnr.cn/jnews/6085.htm
- http://m.wap.oexnr.cn/jnews/998025.htm
- http://m.wap.oexnr.cn/jnews/54434.htm
- http://m.wap.oexnr.cn/jnews/736012.htm
- http://m.wap.oexnr.cn/jnews/0282.htm
- http://m.wap.oexnr.cn/jnews/0959.htm
- http://m.wap.oexnr.cn/jnews/1570724.htm
- http://m.wap.oexnr.cn/jnews/762201.htm
- http://m.wap.oexnr.cn/jnews/89669.htm
- http://m.wap.oexnr.cn/jnews/6585.htm
- http://m.wap.oexnr.cn/jnews/4540581.htm
- http://m.wap.oexnr.cn/jnews/0044756.htm
- http://m.wap.oexnr.cn/jnews/4988680.htm
- http://m.wap.oexnr.cn/jnews/2566.htm
- http://m.wap.oexnr.cn/jnews/077014.htm
- http://m.wap.oexnr.cn/jnews/59962.htm
- http://m.wap.oexnr.cn/jnews/4019.htm
- http://m.wap.oexnr.cn/jnews/3037.htm
- http://m.wap.oexnr.cn/jnews/8725.htm
- http://m.wap.oexnr.cn/jnews/403815.htm
- http://m.wap.oexnr.cn/jnews/73401.htm
- http://m.wap.oexnr.cn/jnews/4602036.htm
- http://m.wap.oexnr.cn/jnews/483451.htm
- http://m.wap.oexnr.cn/jnews/2944285.htm
- http://m.wap.oexnr.cn/jnews/56022.htm
- http://m.wap.oexnr.cn/jnews/004132.htm
- http://m.wap.oexnr.cn/jnews/496969.htm
- http://m.wap.oexnr.cn/jnews/5426.htm
- http://m.wap.oexnr.cn/jnews/1447489.htm
- http://m.wap.oexnr.cn/jnews/473306.htm
- http://m.wap.oexnr.cn/jnews/2604476.htm
- http://m.wap.oexnr.cn/jnews/333238.htm
- http://m.wap.oexnr.cn/jnews/9383604.htm
- http://m.wap.oexnr.cn/jnews/584488.htm
- http://m.wap.oexnr.cn/jnews/176691.htm
- http://m.wap.oexnr.cn/jnews/3310773.htm
- http://m.wap.oexnr.cn/jnews/4039051.htm
- http://m.wap.oexnr.cn/jnews/8613.htm
- http://m.wap.oexnr.cn/jnews/22357.htm
- http://m.wap.oexnr.cn/jnews/2333536.htm
- http://m.wap.oexnr.cn/jnews/3385.htm
- http://m.wap.oexnr.cn/jnews/3546082.htm
- http://m.wap.oexnr.cn/jnews/7884.htm
- http://m.wap.oexnr.cn/jnews/7771.htm
- http://m.wap.oexnr.cn/jnews/34899.htm
- http://m.wap.oexnr.cn/jnews/0404.htm
- http://m.wap.oexnr.cn/jnews/705060.htm
- http://m.wap.oexnr.cn/jnews/025323.htm
- http://m.wap.oexnr.cn/jnews/8705.htm
- http://m.wap.oexnr.cn/jnews/25390.htm
- http://m.wap.oexnr.cn/jnews/996118.htm
- http://m.wap.oexnr.cn/jnews/0239642.htm
- http://m.wap.oexnr.cn/jnews/146417.htm
- http://m.wap.oexnr.cn/jnews/4529877.htm
- http://m.wap.oexnr.cn/jnews/3907758.htm
- http://m.wap.oexnr.cn/jnews/656681.htm
- http://m.wap.oexnr.cn/jnews/960357.htm
- http://m.wap.oexnr.cn/jnews/560559.htm
- http://m.wap.oexnr.cn/jnews/70500.htm
- http://m.wap.oexnr.cn/jnews/9918338.htm
- http://m.wap.oexnr.cn/jnews/081241.htm
- http://m.wap.oexnr.cn/jnews/4294.htm
- http://m.wap.oexnr.cn/jnews/3122.htm
- http://m.wap.oexnr.cn/jnews/230084.htm
- http://m.wap.oexnr.cn/jnews/8418233.htm
- http://m.wap.oexnr.cn/jnews/19751.htm
- http://m.wap.oexnr.cn/jnews/0765.htm
- http://m.wap.oexnr.cn/jnews/8914.htm
- http://m.wap.oexnr.cn/jnews/4612.htm
- http://m.wap.oexnr.cn/jnews/9993584.htm
- http://m.wap.oexnr.cn/jnews/4373144.htm
- http://m.wap.oexnr.cn/jnews/9451507.htm
- http://m.wap.oexnr.cn/jnews/426363.htm
- http://m.wap.oexnr.cn/jnews/108182.htm
- http://m.wap.oexnr.cn/jnews/4254652.htm
- http://m.wap.oexnr.cn/jnews/9989584.htm
- http://m.wap.oexnr.cn/jnews/78223.htm
- http://m.wap.oexnr.cn/jnews/89536.htm
- http://m.wap.oexnr.cn/jnews/0948169.htm
- http://m.wap.oexnr.cn/jnews/5239.htm
- http://m.wap.oexnr.cn/jnews/5934390.htm
- http://m.wap.oexnr.cn/jnews/75589.htm
- http://m.wap.oexnr.cn/jnews/528671.htm
- http://m.wap.oexnr.cn/jnews/88098.htm
- http://m.wap.oexnr.cn/jnews/069859.htm
- http://m.wap.oexnr.cn/jnews/0216.htm
- http://m.wap.oexnr.cn/jnews/46592.htm
- http://m.wap.oexnr.cn/jnews/9272.htm
- http://m.wap.oexnr.cn/jnews/654631.htm
- http://m.wap.oexnr.cn/jnews/0417034.htm
- http://m.wap.oexnr.cn/jnews/0940.htm
- http://m.wap.oexnr.cn/jnews/5737.htm
- http://m.wap.oexnr.cn/jnews/3073.htm
- http://m.wap.oexnr.cn/jnews/65851.htm
- http://m.wap.oexnr.cn/jnews/1480176.htm
- http://m.wap.oexnr.cn/jnews/2319.htm
- http://m.wap.oexnr.cn/jnews/198709.htm
- http://m.wap.oexnr.cn/jnews/8356.htm
- http://m.wap.oexnr.cn/jnews/73723.htm
- http://m.wap.oexnr.cn/jnews/0697239.htm
- http://m.wap.oexnr.cn/jnews/3007886.htm
- http://m.wap.oexnr.cn/jnews/3997.htm
- http://m.wap.oexnr.cn/jnews/491744.htm
- http://m.wap.oexnr.cn/jnews/4000035.htm
- http://m.wap.oexnr.cn/jnews/57795.htm
- http://m.wap.oexnr.cn/jnews/3947.htm

## 项目结构

```
oexnr-news-aggregator/
├── cli.py                         # 命令行入口，解析参数并调度核心流程
├── requirements.txt               # 生产环境依赖列表
├── setup.py                       # 项目安装与打包配置
├── config/
│   ├── default.yaml               # 默认配置（请求间隔、超时、并发数）
│   └── parser_rules.json          # 站点解析规则模板
├── src/
│   ├── core/
│   │   ├── fetcher.py             # HTTP 请求封装，含重试与错误处理
│   │   ├── parser.py              # 通用 HTML 解析与字段提取逻辑
│   │   └── exporter.py            # JSON/CSV/HTTP 导出模块
│   ├── plugins/
│   │   ├── base.py                # 解析插件基类定义
│   │   └── oexnr_mobile.py        # 针对 m.wap.oexnr.cn 的定制解析器
│   └── utils/
│       ├── logger.py              # 日志初始化与格式化
│       └── validators.py          # URL 校验与规范化工具
├── tests/
│   ├── test_fetcher.py            # 请求模块单元测试
│   ├── test_parser.py             # 解析模块单元测试
│   └── fixtures/
│       └── sample_pages/          # 模拟 HTML 页面供测试使用
├── docs/
│   ├── getting_started.md         # 快速入门指南
│   ├── configuration.md           # 完整配置参考
│   ├── parser_development.md      # 自定义解析器开发教程
│   └── api_reference.md           # 自动生成的 API 文档
├── examples/
│   ├── batch_import.py            # 批量 URL 导入示例脚本
│   └── custom_export.py           # 自定义输出格式示例
└── .github/
    └── workflows/
        └── ci.yml                 # 持续集成流水线配置
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 在提交前请搜索已有 Issue 避免重复，使用项目提供的 Issue 模板填写操作系统版本、Python 版本和完整错误堆栈。

Fork 仓库并创建功能分支 从 main 分支签出新的分支，命名格式为 feature/简短描述 或 fix/问题编号，确保分支名称具有描述性。

编写或更新单元测试 所有新增功能或缺陷修复必须包含对应的测试用例，测试覆盖率不得低于 80%，使用 pytest 运行全部测试。

提交 Pull Request 并描述变更 在 PR 描述中详细说明改动内容、测试结果和影响范围，关联相关 Issue 编号，等待至少一名维护者审核。

遵守代码风格规范 使用 Black 格式化 Python 代码，导入语句按标准库、第三方库、本地模块分组，所有公共函数需包含 docstring。

## 常见问题

Q: 采集过程中遇到 HTTP 429 或 503 错误如何处理？
A: 项目内置了指数退避重试机制，默认最多重试 3 次。如果频繁出现此类错误，建议通过命令行参数 --delay 增加请求间隔（例如 --delay 1.5），或修改 config/default.yaml 中的 request_interval 字段。同时可启用 --random-delay 选项在间隔中加入随机抖动，进一步降低被限流的概率。

Q: 如何添加对其它新闻站点的支持？
A: 您需要继承 src/plugins/base.py 中的 BaseParser 类，实现 parse_title、parse_publish_time、parse_content 等抽象方法。然后在 config/parser_rules.json 中注册新站点的主机名与对应解析器类名。具体开发流程请参考 docs/parser_development.md 中的完整示例。

Q: 采集结果中的时间字段为何有时为空或格式不一致？
A: 不同新闻页面的时间表示方式可能存在差异。项目默认尝试解析常见的日期时间格式，但无法覆盖所有变体。您可以通过自定义解析器中的 parse_publish_time 方法，针对特定站点编写专用解析逻辑。也可以使用 --time-format 参数指定统一的输出时区。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
