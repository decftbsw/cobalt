# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与新闻外链管理的开源工具集，定位于为开发者、技术内容运营者以及信息聚合平台提供标准化的新闻链接采集、分类、存储与分发能力。该项目并非一个简单的链接列表，而是一套围绕新闻 URL 资源构建的数据处理脚手架，包含链接有效性检测、元信息提取、内容摘要生成以及多格式输出等核心模块，适用于每日处理数百至数千条新闻外链的中等规模场景。

本项目重点关注三个核心问题：第一，如何从杂乱的新闻 URL 中快速提取可用的结构化信息；第二，如何对批量链接进行健康检查与状态监控；第三，如何将外链资源以统一格式输出供下游系统消费。项目本身不依赖任何商业 API，完全基于开源生态构建，可部署于 Linux 服务器、容器环境或边缘计算节点。

## 功能概览

- **批量链接解析**：支持从文本文件、CSV 或标准输入中读取大量新闻 URL，自动解析协议、域名、路径及查询参数，并生成结构化记录。
- **HTTP 状态检查**：对每条链接执行 HEAD 或 GET 请求，检测响应状态码、内容类型、内容长度及最后修改时间，用于判断链接可用性。
- **元信息提取**：从 HTML 页面中提取标题、发布时间、作者、关键词及正文摘要，支持常见新闻 CMS 系统的模板适配。
- **去重与过滤**：基于 URL 指纹和内容哈希实现链接去重，支持黑名单域名过滤和关键词白名单筛选。
- **多格式导出**：支持将处理结果导出为 JSON、CSV、Markdown 表格以及 RSS 2.0 格式，便于集成到静态站点生成器或 CMS 中。
- **定时任务支持**：内置 Cron 表达式调度器，可定时拉取指定来源的新闻链接并执行全流程处理，输出结果自动归档。
- **日志与监控**：记录每次运行的详细日志，包括成功数、失败数、平均响应时间及错误分类统计，便于排查问题。

## 应用场景

- **技术资讯每日简报生成**：运营人员可将多个技术博客、新闻站点的链接汇总后导入本系统，每日定时生成 Markdown 格式的简报文件，直接发布至团队内部知识库或邮件列表。
- **新闻链接健康度巡检**：对于已发布的内容平台，可使用本工具定期巡检所有外链，自动标记失效链接（如 404、500）并生成报告，帮助维护者及时修复或替换。
- **内容聚合站数据预处理**：在将外部新闻链接导入自建 CMS 或数据库之前，使用本工具完成链接清洗、元信息补全和去重操作，确保入库数据质量，减少后续人工编辑成本。
- **学术或行业动态跟踪**：研究人员可配置特定域名或关键词白名单，系统每日自动抓取相关新闻链接并提取摘要，生成带时间戳的研究素材库，支持后续文献回顾。

## 快速开始

以下命令演示了从克隆代码到运行一次完整链接处理流程的步骤。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/newslink-aggregator.git
cd newslink-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 请使用 venv\Scripts\activate
pip install -r requirements.txt

# 准备链接文件 links.txt，每行一个 URL
# 运行基础处理（检查状态 + 提取标题）
python run.py --input links.txt --output result.json --check-status
```

若需定时执行，可使用以下示例配置：

```bash
# 每日凌晨 2 点执行，输出至 archive 目录
python scheduler.py --cron "0 2 * * *" --input sources.txt --output-dir ./archive
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，低于此版本将无法使用类型注解和异步特性 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与响应，支持连接池和重试策略 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析与元素提取，用于元信息抓取 |
| lxml | 4.9.0 及以上 | 作为 BeautifulSoup 的解析器后端，性能优于 html.parser |
| python-dateutil | 2.8.0 及以上 | 解析新闻页面中的多种日期格式 |
| pyyaml | 6.0 及以上 | 读取配置文件（YAML 格式），用于用户自定义规则 |
| aiofiles | 0.8.0 及以上 | 异步文件读写，提升大规模链接处理时的 I/O 效率 |
| click | 8.0.0 及以上 | 命令行交互框架，提供子命令和参数解析 |
| pytest | 7.0.0 （开发依赖） | 单元测试框架，用于贡献者验证代码改动 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何安装、配置、运行以及调试常见问题？输入输出格式有何要求？ |
| 配置参考 | docs/config-reference.md | 配置文件中的每个字段（如超时时间、重试次数、过滤器规则）分别控制什么行为？ |
| API 文档 | docs/api-reference.md | 各模块的类和方法签名、参数说明及返回值结构，供二次开发时查阅。 |
| 贡献指南 | CONTRIBUTING.md | 如何提交代码、编写测试用例、更新文档以及遵守代码风格规范？ |

完整文档位于项目根目录下的 docs 文件夹，也可在线访问 https://docs.newslink-aggregator.example 获取最新版本（该地址仅为示例，实际文档托管于项目 Wiki）。

## 资源列表

- http://m.3g.oexnr.cn/nnews/86685.htm
- http://m.3g.oexnr.cn/nnews/2741704.htm
- http://m.3g.oexnr.cn/nnews/492380.htm
- http://m.3g.oexnr.cn/nnews/37858.htm
- http://m.3g.oexnr.cn/nnews/62357.htm
- http://m.3g.oexnr.cn/nnews/4323.htm
- http://m.3g.oexnr.cn/nnews/7439.htm
- http://m.3g.oexnr.cn/nnews/8296.htm
- http://m.3g.oexnr.cn/nnews/91859.htm
- http://m.3g.oexnr.cn/nnews/4704.htm
- http://m.3g.oexnr.cn/nnews/428136.htm
- http://m.3g.oexnr.cn/nnews/4868250.htm
- http://m.3g.oexnr.cn/nnews/454202.htm
- http://m.3g.oexnr.cn/nnews/66113.htm
- http://m.3g.oexnr.cn/nnews/628738.htm
- http://m.3g.oexnr.cn/nnews/593072.htm
- http://m.3g.oexnr.cn/nnews/1916.htm
- http://m.3g.oexnr.cn/nnews/6478276.htm
- http://m.3g.oexnr.cn/nnews/987118.htm
- http://m.3g.oexnr.cn/nnews/0296.htm
- http://m.3g.oexnr.cn/nnews/586521.htm
- http://m.3g.oexnr.cn/nnews/887819.htm
- http://m.3g.oexnr.cn/nnews/6166921.htm
- http://m.3g.oexnr.cn/nnews/565531.htm
- http://m.3g.oexnr.cn/nnews/3026.htm
- http://m.3g.oexnr.cn/nnews/014172.htm
- http://m.3g.oexnr.cn/nnews/3415.htm
- http://m.3g.oexnr.cn/nnews/3342375.htm
- http://m.3g.oexnr.cn/nnews/96509.htm
- http://m.3g.oexnr.cn/nnews/65872.htm
- http://m.3g.oexnr.cn/nnews/3543764.htm
- http://m.3g.oexnr.cn/nnews/8096.htm
- http://m.3g.oexnr.cn/nnews/47161.htm
- http://m.3g.oexnr.cn/nnews/72754.htm
- http://m.3g.oexnr.cn/nnews/4108.htm
- http://m.3g.oexnr.cn/nnews/8222706.htm
- http://m.3g.oexnr.cn/nnews/94603.htm
- http://m.3g.oexnr.cn/nnews/884465.htm
- http://m.3g.oexnr.cn/nnews/21611.htm
- http://m.3g.oexnr.cn/nnews/44869.htm
- http://m.3g.oexnr.cn/nnews/86992.htm
- http://m.3g.oexnr.cn/nnews/442373.htm
- http://m.3g.oexnr.cn/nnews/9994.htm
- http://m.3g.oexnr.cn/nnews/9655975.htm
- http://m.3g.oexnr.cn/nnews/35127.htm
- http://m.3g.oexnr.cn/nnews/329396.htm
- http://m.3g.oexnr.cn/nnews/782820.htm
- http://m.3g.oexnr.cn/nnews/1446780.htm
- http://m.3g.oexnr.cn/nnews/277118.htm
- http://m.3g.oexnr.cn/nnews/59958.htm
- http://m.3g.oexnr.cn/nnews/337558.htm
- http://m.3g.oexnr.cn/nnews/6000.htm
- http://m.3g.oexnr.cn/nnews/1123104.htm
- http://m.3g.oexnr.cn/nnews/5831595.htm
- http://m.3g.oexnr.cn/nnews/17630.htm
- http://m.3g.oexnr.cn/nnews/564350.htm
- http://m.3g.oexnr.cn/nnews/9940457.htm
- http://m.3g.oexnr.cn/nnews/097355.htm
- http://m.3g.oexnr.cn/nnews/94166.htm
- http://m.3g.oexnr.cn/nnews/3744263.htm
- http://m.3g.oexnr.cn/nnews/3351522.htm
- http://m.3g.oexnr.cn/nnews/35704.htm
- http://m.3g.oexnr.cn/nnews/5569.htm
- http://m.3g.oexnr.cn/nnews/42089.htm
- http://m.3g.oexnr.cn/nnews/1581975.htm
- http://m.3g.oexnr.cn/nnews/501296.htm
- http://m.3g.oexnr.cn/nnews/1976705.htm
- http://m.3g.oexnr.cn/nnews/88940.htm
- http://m.3g.oexnr.cn/nnews/9879.htm
- http://m.3g.oexnr.cn/nnews/1800520.htm
- http://m.3g.oexnr.cn/nnews/2396529.htm
- http://m.3g.oexnr.cn/nnews/6267789.htm
- http://m.3g.oexnr.cn/nnews/87178.htm
- http://m.3g.oexnr.cn/nnews/7169110.htm
- http://m.3g.oexnr.cn/nnews/403080.htm
- http://m.3g.oexnr.cn/nnews/415905.htm
- http://m.3g.oexnr.cn/nnews/03893.htm
- http://m.3g.oexnr.cn/nnews/9835.htm
- http://m.3g.oexnr.cn/nnews/645749.htm
- http://m.3g.oexnr.cn/nnews/270950.htm
- http://m.3g.oexnr.cn/nnews/3891680.htm
- http://m.3g.oexnr.cn/nnews/8801.htm
- http://m.3g.oexnr.cn/nnews/4879451.htm
- http://m.3g.oexnr.cn/nnews/38285.htm
- http://m.3g.oexnr.cn/nnews/917367.htm
- http://m.3g.oexnr.cn/nnews/6735867.htm
- http://m.3g.oexnr.cn/nnews/945400.htm
- http://m.3g.oexnr.cn/nnews/110458.htm
- http://m.3g.oexnr.cn/nnews/2502.htm
- http://m.3g.oexnr.cn/nnews/928935.htm
- http://m.3g.oexnr.cn/nnews/1044.htm
- http://m.3g.oexnr.cn/nnews/1451251.htm
- http://m.3g.oexnr.cn/nnews/69270.htm
- http://m.3g.oexnr.cn/nnews/2043.htm
- http://m.3g.oexnr.cn/nnews/0417.htm
- http://m.3g.oexnr.cn/nnews/4845235.htm
- http://m.3g.oexnr.cn/nnews/3867742.htm
- http://m.3g.oexnr.cn/nnews/52348.htm
- http://m.3g.oexnr.cn/nnews/06553.htm
- http://m.3g.oexnr.cn/nnews/12226.htm
- http://m.3g.oexnr.cn/nnews/77838.htm
- http://m.3g.oexnr.cn/nnews/760972.htm
- http://m.3g.oexnr.cn/nnews/0628182.htm
- http://m.3g.oexnr.cn/nnews/2545558.htm
- http://m.3g.oexnr.cn/nnews/0225.htm
- http://m.3g.oexnr.cn/nnews/16056.htm
- http://m.3g.oexnr.cn/nnews/50574.htm
- http://m.3g.oexnr.cn/nnews/00652.htm
- http://m.3g.oexnr.cn/nnews/0056759.htm
- http://m.3g.oexnr.cn/nnews/243879.htm
- http://m.3g.oexnr.cn/nnews/64754.htm
- http://m.3g.oexnr.cn/nnews/5658846.htm
- http://m.3g.oexnr.cn/nnews/11347.htm
- http://m.3g.oexnr.cn/nnews/511414.htm
- http://m.3g.oexnr.cn/nnews/4757658.htm
- http://m.3g.oexnr.cn/nnews/8399043.htm
- http://m.3g.oexnr.cn/nnews/40434.htm
- http://m.3g.oexnr.cn/nnews/92868.htm
- http://m.3g.oexnr.cn/nnews/890304.htm
- http://m.3g.oexnr.cn/nnews/1305335.htm
- http://m.3g.oexnr.cn/nnews/301502.htm
- http://m.3g.oexnr.cn/nnews/570450.htm
- http://m.3g.oexnr.cn/nnews/801953.htm
- http://m.3g.oexnr.cn/nnews/2096838.htm
- http://m.3g.oexnr.cn/nnews/2668.htm
- http://m.3g.oexnr.cn/nnews/00785.htm
- http://m.3g.oexnr.cn/nnews/668841.htm
- http://m.3g.oexnr.cn/nnews/312006.htm
- http://m.3g.oexnr.cn/nnews/9044.htm
- http://m.3g.oexnr.cn/nnews/0713.htm
- http://m.3g.oexnr.cn/nnews/7755.htm
- http://m.3g.oexnr.cn/nnews/0111956.htm
- http://m.3g.oexnr.cn/nnews/54097.htm
- http://m.3g.oexnr.cn/nnews/5104.htm
- http://m.3g.oexnr.cn/nnews/16405.htm
- http://m.3g.oexnr.cn/nnews/7774798.htm
- http://m.3g.oexnr.cn/nnews/54547.htm
- http://m.3g.oexnr.cn/nnews/55883.htm
- http://m.3g.oexnr.cn/nnews/6946148.htm
- http://m.3g.oexnr.cn/nnews/378867.htm
- http://m.3g.oexnr.cn/nnews/995256.htm
- http://m.3g.oexnr.cn/nnews/84327.htm
- http://m.3g.oexnr.cn/nnews/081420.htm
- http://m.3g.oexnr.cn/nnews/514753.htm
- http://m.3g.oexnr.cn/nnews/0991.htm
- http://m.3g.oexnr.cn/nnews/387791.htm
- http://m.3g.oexnr.cn/nnews/222385.htm
- http://m.3g.oexnr.cn/nnews/82455.htm
- http://m.3g.oexnr.cn/nnews/6596959.htm
- http://m.3g.oexnr.cn/nnews/2943.htm
- http://m.3g.oexnr.cn/nnews/4435.htm
- http://m.3g.oexnr.cn/nnews/7939.htm
- http://m.3g.oexnr.cn/nnews/400880.htm
- http://m.3g.oexnr.cn/nnews/647904.htm
- http://m.3g.oexnr.cn/nnews/4364.htm
- http://m.3g.oexnr.cn/nnews/1978.htm
- http://m.3g.oexnr.cn/nnews/6484.htm
- http://m.3g.oexnr.cn/nnews/897411.htm
- http://m.3g.oexnr.cn/nnews/50303.htm
- http://m.3g.oexnr.cn/nnews/6685031.htm
- http://m.3g.oexnr.cn/nnews/6804251.htm
- http://m.3g.oexnr.cn/nnews/6212738.htm
- http://m.3g.oexnr.cn/nnews/3756084.htm
- http://m.3g.oexnr.cn/nnews/8368614.htm
- http://m.3g.oexnr.cn/nnews/68255.htm
- http://m.3g.oexnr.cn/nnews/309284.htm
- http://m.3g.oexnr.cn/nnews/277413.htm
- http://m.3g.oexnr.cn/nnews/7801347.htm
- http://m.3g.oexnr.cn/nnews/5666955.htm
- http://m.3g.oexnr.cn/nnews/9393.htm
- http://m.3g.oexnr.cn/nnews/9259958.htm
- http://m.3g.oexnr.cn/nnews/1609471.htm
- http://m.3g.oexnr.cn/nnews/5834703.htm
- http://m.3g.oexnr.cn/nnews/1907.htm
- http://m.3g.oexnr.cn/nnews/48876.htm
- http://m.3g.oexnr.cn/nnews/75835.htm
- http://m.3g.oexnr.cn/nnews/61534.htm
- http://m.3g.oexnr.cn/nnews/202043.htm
- http://m.3g.oexnr.cn/nnews/1755947.htm
- http://m.3g.oexnr.cn/nnews/35274.htm
- http://m.3g.oexnr.cn/nnews/111800.htm
- http://m.3g.oexnr.cn/nnews/048791.htm
- http://m.3g.oexnr.cn/nnews/24434.htm
- http://m.3g.oexnr.cn/nnews/9861.htm
- http://m.3g.oexnr.cn/nnews/511363.htm
- http://m.3g.oexnr.cn/nnews/12350.htm
- http://m.3g.oexnr.cn/nnews/3425593.htm
- http://m.3g.oexnr.cn/nnews/5462.htm
- http://m.3g.oexnr.cn/nnews/825569.htm
- http://m.3g.oexnr.cn/nnews/8466884.htm
- http://m.3g.oexnr.cn/nnews/51726.htm
- http://m.3g.oexnr.cn/nnews/5706704.htm
- http://m.3g.oexnr.cn/nnews/23855.htm
- http://m.3g.oexnr.cn/nnews/009137.htm
- http://m.3g.oexnr.cn/nnews/4792035.htm
- http://m.3g.oexnr.cn/nnews/885351.htm
- http://m.3g.oexnr.cn/nnews/330782.htm
- http://m.3g.oexnr.cn/nnews/52757.htm
- http://m.3g.oexnr.cn/nnews/48046.htm
- http://m.3g.oexnr.cn/nnews/55143.htm
- http://m.3g.oexnr.cn/nnews/7328.htm
- http://m.3g.oexnr.cn/nnews/5460647.htm
- http://m.3g.oexnr.cn/nnews/126641.htm
- http://m.3g.oexnr.cn/nnews/4628389.htm
- http://m.3g.oexnr.cn/nnews/3510.htm
- http://m.3g.oexnr.cn/nnews/810671.htm
- http://m.3g.oexnr.cn/nnews/762514.htm
- http://m.3g.oexnr.cn/nnews/41790.htm
- http://m.3g.oexnr.cn/nnews/083838.htm
- http://m.3g.oexnr.cn/nnews/8371.htm
- http://m.3g.oexnr.cn/nnews/936023.htm
- http://m.3g.oexnr.cn/nnews/5397.htm
- http://m.3g.oexnr.cn/nnews/9246.htm
- http://m.3g.oexnr.cn/nnews/4833.htm
- http://m.3g.oexnr.cn/nnews/07545.htm
- http://m.3g.oexnr.cn/nnews/183892.htm
- http://m.3g.oexnr.cn/nnews/824363.htm
- http://m.3g.oexnr.cn/nnews/45552.htm
- http://m.3g.oexnr.cn/nnews/569065.htm
- http://m.3g.oexnr.cn/nnews/800553.htm
- http://m.3g.oexnr.cn/nnews/98617.htm
- http://m.3g.oexnr.cn/nnews/1326989.htm
- http://m.3g.oexnr.cn/nnews/0208.htm
- http://m.3g.oexnr.cn/nnews/7222.htm
- http://m.3g.oexnr.cn/nnews/357649.htm
- http://m.3g.oexnr.cn/nnews/09027.htm
- http://m.3g.oexnr.cn/nnews/2039.htm
- http://m.3g.oexnr.cn/nnews/8515.htm
- http://m.3g.oexnr.cn/nnews/48385.htm
- http://m.3g.oexnr.cn/nnews/8333.htm
- http://m.3g.oexnr.cn/nnews/0583720.htm
- http://m.3g.oexnr.cn/nnews/493006.htm
- http://m.3g.oexnr.cn/nnews/98753.htm
- http://m.3g.oexnr.cn/nnews/87213.htm
- http://m.3g.oexnr.cn/nnews/96197.htm
- http://m.3g.oexnr.cn/nnews/10711.htm
- http://m.3g.oexnr.cn/nnews/8264487.htm
- http://m.3g.oexnr.cn/nnews/84714.htm
- http://m.3g.oexnr.cn/nnews/6395303.htm
- http://m.3g.oexnr.cn/nnews/0922.htm
- http://m.3g.oexnr.cn/nnews/878603.htm
- http://m.3g.oexnr.cn/nnews/9103261.htm
- http://m.3g.oexnr.cn/nnews/718701.htm
- http://m.3g.oexnr.cn/nnews/838968.htm
- http://m.3g.oexnr.cn/nnews/4907146.htm
- http://m.3g.oexnr.cn/nnews/6451226.htm
- http://m.3g.oexnr.cn/nnews/915953.htm
- http://m.3g.oexnr.cn/nnews/8959903.htm
- http://m.3g.oexnr.cn/nnews/1195.htm
- http://m.3g.oexnr.cn/nnews/3773.htm
- http://m.3g.oexnr.cn/nnews/4671238.htm
- http://m.3g.oexnr.cn/nnews/26054.htm
- http://m.3g.oexnr.cn/nnews/549580.htm
- http://m.3g.oexnr.cn/nnews/642563.htm
- http://m.3g.oexnr.cn/nnews/916929.htm
- http://m.3g.oexnr.cn/nnews/1555.htm
- http://m.3g.oexnr.cn/nnews/32686.htm
- http://m.3g.oexnr.cn/nnews/9026211.htm
- http://m.3g.oexnr.cn/nnews/77440.htm
- http://m.3g.oexnr.cn/nnews/05832.htm
- http://m.3g.oexnr.cn/nnews/3186207.htm
- http://m.3g.oexnr.cn/nnews/28288.htm
- http://m.3g.oexnr.cn/nnews/5212005.htm
- http://m.3g.oexnr.cn/nnews/93730.htm
- http://m.3g.oexnr.cn/nnews/538183.htm
- http://m.3g.oexnr.cn/nnews/355516.htm
- http://m.3g.oexnr.cn/nnews/437102.htm
- http://m.3g.oexnr.cn/nnews/37553.htm
- http://m.3g.oexnr.cn/nnews/385596.htm
- http://m.3g.oexnr.cn/nnews/53275.htm
- http://m.3g.oexnr.cn/nnews/407472.htm
- http://m.3g.oexnr.cn/nnews/05009.htm
- http://m.3g.oexnr.cn/nnews/68586.htm
- http://m.3g.oexnr.cn/nnews/4731783.htm
- http://m.3g.oexnr.cn/nnews/7681427.htm
- http://m.3g.oexnr.cn/nnews/2144.htm
- http://m.3g.oexnr.cn/nnews/1496049.htm
- http://m.3g.oexnr.cn/nnews/0605310.htm
- http://m.3g.oexnr.cn/nnews/380262.htm
- http://m.3g.oexnr.cn/nnews/83447.htm
- http://m.3g.oexnr.cn/nnews/710602.htm
- http://m.3g.oexnr.cn/nnews/1735465.htm
- http://m.3g.oexnr.cn/nnews/606245.htm
- http://m.3g.oexnr.cn/nnews/2404811.htm
- http://m.3g.oexnr.cn/nnews/98640.htm
- http://m.3g.oexnr.cn/nnews/1880056.htm
- http://m.3g.oexnr.cn/nnews/6835.htm
- http://m.3g.oexnr.cn/nnews/18214.htm
- http://m.3g.oexnr.cn/nnews/8932.htm
- http://m.3g.oexnr.cn/nnews/2152857.htm
- http://m.3g.oexnr.cn/nnews/880911.htm
- http://m.3g.oexnr.cn/nnews/2280.htm
- http://m.3g.oexnr.cn/nnews/61235.htm
- http://m.3g.oexnr.cn/nnews/72742.htm
- http://m.3g.oexnr.cn/nnews/599770.htm
- http://m.3g.oexnr.cn/nnews/82485.htm
- http://m.3g.oexnr.cn/nnews/185245.htm
- http://m.3g.oexnr.cn/nnews/5606189.htm
- http://m.3g.oexnr.cn/nnews/3913.htm
- http://m.3g.oexnr.cn/nnews/173299.htm

## 项目结构

```
newslink-aggregator/
├── run.py                  # 命令行入口，支持子命令（process, check, export）
├── scheduler.py            # 定时调度入口，读取 cron 配置并触发任务
├── requirements.txt        # 生产环境依赖列表（固定版本）
├── dev-requirements.txt    # 开发环境额外依赖（测试、代码检查、文档构建）
├── pyproject.toml          # 项目元数据与构建配置（PEP 621）
│
├── src/                    # 核心源代码目录
│   ├── __init__.py
│   ├── core/               # 核心处理模块
│   │   ├── __init__.py
│   │   ├── fetcher.py      # 异步 HTTP 获取、重试、超时控制
│   │   ├── parser.py       # HTML 解析、标题/时间/正文提取
│   │   ├── checker.py      # 状态码检测、重定向跟踪、链接可用性评分
│   │   └── dedup.py        # 基于布隆过滤器的 URL 去重
│   ├── io/                 # 输入输出适配层
│   │   ├── __init__.py
│   │   ├── reader.py       # 从文件、stdin、数据库读取链接列表
│   │   └── writer.py       # 导出 JSON/CSV/Markdown/RSS
│   ├── utils/              # 通用工具函数
│   │   ├── __init__.py
│   │   ├── logger.py       # 日志格式化、分级输出、日志轮转
│   │   ├── config.py       # YAML 配置加载与合并默认值
│   │   └── time_utils.py   # 时区转换、日期解析辅助
│   └── scheduler/          # 调度器实现
│       ├── __init__.py
│       └── cron_runner.py  # Cron 表达式解析与子进程管理
│
├── tests/                  # 单元测试与集成测试
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── test_dedup.py
│
├── docs/                   # 用户文档和 API 文档源文件
│   ├── user-guide.md
│   ├── config-reference.md
│   └── api-reference.md
│
├── examples/               # 示例配置与输入输出样本
│   ├── sample_links.txt
│   ├── sample_config.yaml
│   └── sample_output.json
│
└── scripts/                # 辅助脚本（安装钩子、数据迁移等）
    ├── setup_hooks.sh
    └── migrate_db.py
```

## 贡献指南

1. 从 GitHub 仓库 fork 本项目，并在本地创建特性分支（如 feature/your-feature-name），确保分支名称简洁且描述改动目的。所有开发工作应在分支上完成，禁止直接提交至 main 分支。

2. 编写或修改代码后，请运行测试套件（pytest tests/）确保无回归故障，并尽量为新增功能补充对应的单元测试用例，测试覆盖率不低于 80%。若涉及文档改动，请同步更新 docs 目录下的相关文档。

3. 提交前执行代码格式化（black .）和导入排序（isort .），并确保通过静态检查（flake8 和 mypy）。项目根目录下已包含配置文件，可直接调用。

4. 提交信息使用约定式提交格式（如 feat: 添加重试机制、fix: 修复日期解析时区错误），并在 PR 描述中清晰说明改动内容、动机以及影响范围。所有 PR 需至少一名维护者审阅后方可合并。

5. 若发现缺陷或希望提出新功能，请先在 Issues 列表搜索是否已有类似讨论，若无则新建 Issue 并填写完整模板（包含环境信息、复现步骤、期望行为与当前行为对比）。

## 常见问题

**问：如何处理单个页面请求超时或临时失败？**

系统内置了指数退避重试机制，默认最多重试 3 次，首次超时时间为 10 秒，后续每次重试超时时间加倍。用户可在配置文件中调整 max_retries 和 timeout_base 参数。对于持续失败的链接，最终结果中会标记为 unreachable 并记录错误原因（如超时、连接拒绝、SSL 错误等），便于后续人工介入。

**问：系统能否处理需要登录或带有反爬机制的新闻站点？**

当前版本不支持 Cookie 会话管理和 JavaScript 渲染，仅适用于可直接通过 GET 请求获取 HTML 内容的公开新闻页面。若目标站点具有反爬策略（如 User-Agent 校验、频率限制），用户可通过配置自定义请求头（headers）和请求间隔（delay）来规避基础限制。对于复杂场景，建议结合外部代理池或使用 Selenium 等工具作为数据采集前置层，本项目仅作为后处理链路。

**问：如何处理不同新闻站点日期格式不一致的问题？**

项目内置了一个可扩展的日期解析器，支持常见的 RFC 822、ISO 8601、中文数字日期以及多数国内新闻站点自定义格式。若遇到未覆盖的格式，用户可在配置文件的 date_formats 字段中添加自定义正则或格式字符串，系统将按顺序尝试匹配。若全部失败，则记录原始字符串并标记为 parse_failed，同时保留页面中的其他元信息。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
