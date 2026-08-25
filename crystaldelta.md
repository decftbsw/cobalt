# NewsFetch Link Aggregator

NewsFetch Link Aggregator 是一个面向技术内容聚合与新闻外链管理的开源工具集，专注于从指定的新闻源列表（m.3g.ghtkgg.cn）中抓取、解析和归档 HTML 页面内容。该项目适用于需要批量处理移动端新闻页面的开发者、数据研究人员以及内容聚合平台运维人员，提供从链接清洗、内容提取到结构化输出的完整工作流。项目本身不存储任何内容，仅提供抓取与解析框架，所有原始数据均指向用户配置的源站资源。

## 功能概览

**批量链接抓取** 支持从给定的 URL 列表中并发请求 HTML 页面，自动处理移动端 UA 与超时重试策略。

**智能内容解析** 基于正则与 DOM 树双重解析模式，提取新闻标题、正文段落、发布时间及来源字段。

**自动去重与过滤** 对重复 URL 和无效响应进行过滤，仅保留状态码 200 且内容长度大于 1KB 的有效页面。

**结构化数据导出** 支持将解析结果输出为 JSON、CSV 或 SQLite 数据库格式，便于下游数据分析。

**定时增量更新** 内置 cron 风格的调度器，可配置每日或每小时增量拉取最新新闻链接。

**错误日志与监控** 记录每次抓取的失败原因、响应时间与重试次数，提供 Prometheus 兼容的 metrics 端点。

**代理与隧道支持** 支持 HTTP/HTTPS 代理以及 SOCKS5 隧道，适用于需要绕过地域限制的采集场景。

## 应用场景

**技术新闻聚合站运维** 运维人员可利用 NewsFetch 定时拉取指定新闻源的最新文章，将解析后的结构化数据存入 Elasticsearch，供前端聚合站展示实时热点。

**舆情数据分析** 数据研究人员可批量导出指定时间段内的新闻标题与正文，进行词频分析、情感打分或热点事件追踪，所有原始链接均来自用户配置的资源列表。

**内容归档与备份** 对于需要长期保存新闻内容的团队，可结合 NewsFetch 的增量拉取与 SQLite 存储功能，构建本地化的新闻归档库，避免源站内容下线导致信息丢失。

**移动端页面适配测试** 前端开发者可使用该项目批量请求移动端页面，检测响应式布局状态、加载时间与资源完整性，作为性能监控的辅助工具。

## 快速开始

```bash
# 克隆代码仓库
git clone https://github.com/your-org/newsfetch-link-aggregator.git
cd newsfetch-link-aggregator

# 安装项目依赖（使用 pipenv 或 virtualenv）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行初始抓取任务，使用项目内置的资源列表（见资源列表章节）
python main.py --fetch --output ./data/output.json
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.11 以获得最佳性能 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与会话管理 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析与 DOM 树遍历 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的底层解析器，提供更快的解析速度 |
| apscheduler | 3.10.0 及以上 | 定时任务调度，用于增量更新配置 |
| prometheus-client | 0.16.0 及以上 | 可选，用于暴露监控指标端点 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速安装并首次运行抓取任务；如何配置源站 URL 列表 |
| 配置说明 | docs/configuration.md | 如何调整并发数、超时时间、代理设置和日志级别 |
| 解析规则 | docs/parsing-rules.md | 项目默认的标题、正文、时间提取规则，以及如何自定义解析器 |
| 输出格式 | docs/output-formats.md | 支持的所有导出格式（JSON、CSV、SQLite）及其字段映射关系 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/4634942.htm
- http://m.3g.ghtkgg.cn/nnews/1856.htm
- http://m.3g.ghtkgg.cn/nnews/9756.htm
- http://m.3g.ghtkgg.cn/nnews/66710.htm
- http://m.3g.ghtkgg.cn/nnews/968153.htm
- http://m.3g.ghtkgg.cn/nnews/82191.htm
- http://m.3g.ghtkgg.cn/nnews/6115213.htm
- http://m.3g.ghtkgg.cn/nnews/7885.htm
- http://m.3g.ghtkgg.cn/nnews/612967.htm
- http://m.3g.ghtkgg.cn/nnews/301575.htm
- http://m.3g.ghtkgg.cn/nnews/7974743.htm
- http://m.3g.ghtkgg.cn/nnews/74121.htm
- http://m.3g.ghtkgg.cn/nnews/999120.htm
- http://m.3g.ghtkgg.cn/nnews/8676.htm
- http://m.3g.ghtkgg.cn/nnews/796974.htm
- http://m.3g.ghtkgg.cn/nnews/86641.htm
- http://m.3g.ghtkgg.cn/nnews/6550711.htm
- http://m.3g.ghtkgg.cn/nnews/92146.htm
- http://m.3g.ghtkgg.cn/nnews/354871.htm
- http://m.3g.ghtkgg.cn/nnews/4213764.htm
- http://m.3g.ghtkgg.cn/nnews/7877925.htm
- http://m.3g.ghtkgg.cn/nnews/13780.htm
- http://m.3g.ghtkgg.cn/nnews/5158676.htm
- http://m.3g.ghtkgg.cn/nnews/04842.htm
- http://m.3g.ghtkgg.cn/nnews/26214.htm
- http://m.3g.ghtkgg.cn/nnews/00263.htm
- http://m.3g.ghtkgg.cn/nnews/4872.htm
- http://m.3g.ghtkgg.cn/nnews/313370.htm
- http://m.3g.ghtkgg.cn/nnews/782619.htm
- http://m.3g.ghtkgg.cn/nnews/9681.htm
- http://m.3g.ghtkgg.cn/nnews/05176.htm
- http://m.3g.ghtkgg.cn/nnews/46548.htm
- http://m.3g.ghtkgg.cn/nnews/7943.htm
- http://m.3g.ghtkgg.cn/nnews/687540.htm
- http://m.3g.ghtkgg.cn/nnews/0348274.htm
- http://m.3g.ghtkgg.cn/nnews/8074.htm
- http://m.3g.ghtkgg.cn/nnews/9201198.htm
- http://m.3g.ghtkgg.cn/nnews/93604.htm
- http://m.3g.ghtkgg.cn/nnews/672019.htm
- http://m.3g.ghtkgg.cn/nnews/4734685.htm
- http://m.3g.ghtkgg.cn/nnews/5392.htm
- http://m.3g.ghtkgg.cn/nnews/9602.htm
- http://m.3g.ghtkgg.cn/nnews/65174.htm
- http://m.3g.ghtkgg.cn/nnews/9434940.htm
- http://m.3g.ghtkgg.cn/nnews/1873555.htm
- http://m.3g.ghtkgg.cn/nnews/71618.htm
- http://m.3g.ghtkgg.cn/nnews/488559.htm
- http://m.3g.ghtkgg.cn/nnews/5905.htm
- http://m.3g.ghtkgg.cn/nnews/034887.htm
- http://m.3g.ghtkgg.cn/nnews/78399.htm
- http://m.3g.ghtkgg.cn/nnews/017311.htm
- http://m.3g.ghtkgg.cn/nnews/31566.htm
- http://m.3g.ghtkgg.cn/nnews/5312920.htm
- http://m.3g.ghtkgg.cn/nnews/356659.htm
- http://m.3g.ghtkgg.cn/nnews/6704911.htm
- http://m.3g.ghtkgg.cn/nnews/482935.htm
- http://m.3g.ghtkgg.cn/nnews/5618155.htm
- http://m.3g.ghtkgg.cn/nnews/8264.htm
- http://m.3g.ghtkgg.cn/nnews/7905915.htm
- http://m.3g.ghtkgg.cn/nnews/758739.htm
- http://m.3g.ghtkgg.cn/nnews/66165.htm
- http://m.3g.ghtkgg.cn/nnews/6161.htm
- http://m.3g.ghtkgg.cn/nnews/5592030.htm
- http://m.3g.ghtkgg.cn/nnews/2710898.htm
- http://m.3g.ghtkgg.cn/nnews/05089.htm
- http://m.3g.ghtkgg.cn/nnews/2838.htm
- http://m.3g.ghtkgg.cn/nnews/60438.htm
- http://m.3g.ghtkgg.cn/nnews/50158.htm
- http://m.3g.ghtkgg.cn/nnews/53529.htm
- http://m.3g.ghtkgg.cn/nnews/57030.htm
- http://m.3g.ghtkgg.cn/nnews/42515.htm
- http://m.3g.ghtkgg.cn/nnews/363778.htm
- http://m.3g.ghtkgg.cn/nnews/865313.htm
- http://m.3g.ghtkgg.cn/nnews/060198.htm
- http://m.3g.ghtkgg.cn/nnews/9025794.htm
- http://m.3g.ghtkgg.cn/nnews/2334356.htm
- http://m.3g.ghtkgg.cn/nnews/923193.htm
- http://m.3g.ghtkgg.cn/nnews/12305.htm
- http://m.3g.ghtkgg.cn/nnews/20819.htm
- http://m.3g.ghtkgg.cn/nnews/4878.htm
- http://m.3g.ghtkgg.cn/nnews/7548.htm
- http://m.3g.ghtkgg.cn/nnews/556804.htm
- http://m.3g.ghtkgg.cn/nnews/84101.htm
- http://m.3g.ghtkgg.cn/nnews/7822.htm
- http://m.3g.ghtkgg.cn/nnews/5656139.htm
- http://m.3g.ghtkgg.cn/nnews/5787.htm
- http://m.3g.ghtkgg.cn/nnews/51480.htm
- http://m.3g.ghtkgg.cn/nnews/57475.htm
- http://m.3g.ghtkgg.cn/nnews/15583.htm
- http://m.3g.ghtkgg.cn/nnews/9479643.htm
- http://m.3g.ghtkgg.cn/nnews/5606046.htm
- http://m.3g.ghtkgg.cn/nnews/4157567.htm
- http://m.3g.ghtkgg.cn/nnews/7592555.htm
- http://m.3g.ghtkgg.cn/nnews/843713.htm
- http://m.3g.ghtkgg.cn/nnews/6922235.htm
- http://m.3g.ghtkgg.cn/nnews/0637386.htm
- http://m.3g.ghtkgg.cn/nnews/31425.htm
- http://m.3g.ghtkgg.cn/nnews/3208607.htm
- http://m.3g.ghtkgg.cn/nnews/4804.htm
- http://m.3g.ghtkgg.cn/nnews/917628.htm
- http://m.3g.ghtkgg.cn/nnews/867089.htm
- http://m.3g.ghtkgg.cn/nnews/45013.htm
- http://m.3g.ghtkgg.cn/nnews/907041.htm
- http://m.3g.ghtkgg.cn/nnews/1957412.htm
- http://m.3g.ghtkgg.cn/nnews/9087.htm
- http://m.3g.ghtkgg.cn/nnews/038232.htm
- http://m.3g.ghtkgg.cn/nnews/7565.htm
- http://m.3g.ghtkgg.cn/nnews/7574231.htm
- http://m.3g.ghtkgg.cn/nnews/4719582.htm
- http://m.3g.ghtkgg.cn/nnews/5178.htm
- http://m.3g.ghtkgg.cn/nnews/9147589.htm
- http://m.3g.ghtkgg.cn/nnews/92551.htm
- http://m.3g.ghtkgg.cn/nnews/3284005.htm
- http://m.3g.ghtkgg.cn/nnews/4013268.htm
- http://m.3g.ghtkgg.cn/nnews/69355.htm
- http://m.3g.ghtkgg.cn/nnews/8510167.htm
- http://m.3g.ghtkgg.cn/nnews/042320.htm
- http://m.3g.ghtkgg.cn/nnews/3420620.htm
- http://m.3g.ghtkgg.cn/nnews/680486.htm
- http://m.3g.ghtkgg.cn/nnews/3632200.htm
- http://m.3g.ghtkgg.cn/nnews/6948961.htm
- http://m.3g.ghtkgg.cn/nnews/98688.htm
- http://m.3g.ghtkgg.cn/nnews/275875.htm
- http://m.3g.ghtkgg.cn/nnews/463969.htm
- http://m.3g.ghtkgg.cn/nnews/7001035.htm
- http://m.3g.ghtkgg.cn/nnews/6264.htm
- http://m.3g.ghtkgg.cn/nnews/215231.htm
- http://m.3g.ghtkgg.cn/nnews/01769.htm
- http://m.3g.ghtkgg.cn/nnews/12529.htm
- http://m.3g.ghtkgg.cn/nnews/66235.htm
- http://m.3g.ghtkgg.cn/nnews/4805.htm
- http://m.3g.ghtkgg.cn/nnews/0395651.htm
- http://m.3g.ghtkgg.cn/nnews/0174833.htm
- http://m.3g.ghtkgg.cn/nnews/0697.htm
- http://m.3g.ghtkgg.cn/nnews/9611.htm
- http://m.3g.ghtkgg.cn/nnews/2721207.htm
- http://m.3g.ghtkgg.cn/nnews/92950.htm
- http://m.3g.ghtkgg.cn/nnews/92332.htm
- http://m.3g.ghtkgg.cn/nnews/9208479.htm
- http://m.3g.ghtkgg.cn/nnews/96544.htm
- http://m.3g.ghtkgg.cn/nnews/7483.htm
- http://m.3g.ghtkgg.cn/nnews/944048.htm
- http://m.3g.ghtkgg.cn/nnews/7061729.htm
- http://m.3g.ghtkgg.cn/nnews/0702.htm
- http://m.3g.ghtkgg.cn/nnews/7529.htm
- http://m.3g.ghtkgg.cn/nnews/5391578.htm
- http://m.3g.ghtkgg.cn/nnews/0567383.htm
- http://m.3g.ghtkgg.cn/nnews/6025409.htm
- http://m.3g.ghtkgg.cn/nnews/7177184.htm
- http://m.3g.ghtkgg.cn/nnews/77026.htm
- http://m.3g.ghtkgg.cn/nnews/16915.htm
- http://m.3g.ghtkgg.cn/nnews/5146.htm
- http://m.3g.ghtkgg.cn/nnews/0346.htm
- http://m.3g.ghtkgg.cn/nnews/62776.htm
- http://m.3g.ghtkgg.cn/nnews/851193.htm
- http://m.3g.ghtkgg.cn/nnews/5165.htm
- http://m.3g.ghtkgg.cn/nnews/434043.htm
- http://m.3g.ghtkgg.cn/nnews/013710.htm
- http://m.3g.ghtkgg.cn/nnews/55614.htm
- http://m.3g.ghtkgg.cn/nnews/8779024.htm
- http://m.3g.ghtkgg.cn/nnews/3889.htm
- http://m.3g.ghtkgg.cn/nnews/417831.htm
- http://m.3g.ghtkgg.cn/nnews/4806246.htm
- http://m.3g.ghtkgg.cn/nnews/705489.htm
- http://m.3g.ghtkgg.cn/nnews/3528.htm
- http://m.3g.ghtkgg.cn/nnews/0469.htm
- http://m.3g.ghtkgg.cn/nnews/86724.htm
- http://m.3g.ghtkgg.cn/nnews/9937787.htm
- http://m.3g.ghtkgg.cn/nnews/25469.htm
- http://m.3g.ghtkgg.cn/nnews/7225.htm
- http://m.3g.ghtkgg.cn/nnews/175995.htm
- http://m.3g.ghtkgg.cn/nnews/73674.htm
- http://m.3g.ghtkgg.cn/nnews/1145562.htm
- http://m.3g.ghtkgg.cn/nnews/16358.htm
- http://m.3g.ghtkgg.cn/nnews/1999439.htm
- http://m.3g.ghtkgg.cn/nnews/0904.htm
- http://m.3g.ghtkgg.cn/nnews/665420.htm
- http://m.3g.ghtkgg.cn/nnews/4527223.htm
- http://m.3g.ghtkgg.cn/nnews/97289.htm
- http://m.3g.ghtkgg.cn/nnews/9671.htm
- http://m.3g.ghtkgg.cn/nnews/5118564.htm
- http://m.3g.ghtkgg.cn/nnews/25682.htm
- http://m.3g.ghtkgg.cn/nnews/8250979.htm
- http://m.3g.ghtkgg.cn/nnews/62835.htm
- http://m.3g.ghtkgg.cn/nnews/133329.htm
- http://m.3g.ghtkgg.cn/nnews/55736.htm
- http://m.3g.ghtkgg.cn/nnews/1771.htm
- http://m.3g.ghtkgg.cn/nnews/07572.htm
- http://m.3g.ghtkgg.cn/nnews/8234903.htm
- http://m.3g.ghtkgg.cn/nnews/0401.htm
- http://m.3g.ghtkgg.cn/nnews/7352.htm
- http://m.3g.ghtkgg.cn/nnews/53805.htm
- http://m.3g.ghtkgg.cn/nnews/076491.htm
- http://m.3g.ghtkgg.cn/nnews/22410.htm
- http://m.3g.ghtkgg.cn/nnews/779369.htm
- http://m.3g.ghtkgg.cn/nnews/133803.htm
- http://m.3g.ghtkgg.cn/nnews/43593.htm
- http://m.3g.ghtkgg.cn/nnews/20053.htm
- http://m.3g.ghtkgg.cn/nnews/0811614.htm
- http://m.3g.ghtkgg.cn/nnews/9034.htm
- http://m.3g.ghtkgg.cn/nnews/36282.htm
- http://m.3g.ghtkgg.cn/nnews/3779.htm
- http://m.3g.ghtkgg.cn/nnews/7630348.htm
- http://m.3g.ghtkgg.cn/nnews/51611.htm
- http://m.3g.ghtkgg.cn/nnews/36238.htm
- http://m.3g.ghtkgg.cn/nnews/34561.htm
- http://m.3g.ghtkgg.cn/nnews/421509.htm
- http://m.3g.ghtkgg.cn/nnews/2377831.htm
- http://m.3g.ghtkgg.cn/nnews/045254.htm
- http://m.3g.ghtkgg.cn/nnews/2115.htm
- http://m.3g.ghtkgg.cn/nnews/495369.htm
- http://m.3g.ghtkgg.cn/nnews/4315.htm
- http://m.3g.ghtkgg.cn/nnews/5114.htm
- http://m.3g.ghtkgg.cn/nnews/315979.htm
- http://m.3g.ghtkgg.cn/nnews/95363.htm
- http://m.3g.ghtkgg.cn/nnews/95405.htm
- http://m.3g.ghtkgg.cn/nnews/335107.htm
- http://m.3g.ghtkgg.cn/nnews/4472434.htm
- http://m.3g.ghtkgg.cn/nnews/79818.htm
- http://m.3g.ghtkgg.cn/nnews/40652.htm
- http://m.3g.ghtkgg.cn/nnews/4552307.htm
- http://m.3g.ghtkgg.cn/nnews/72025.htm
- http://m.3g.ghtkgg.cn/nnews/62384.htm
- http://m.3g.ghtkgg.cn/nnews/2215858.htm
- http://m.3g.ghtkgg.cn/nnews/04549.htm
- http://m.3g.ghtkgg.cn/nnews/8987723.htm
- http://m.3g.ghtkgg.cn/nnews/0817686.htm
- http://m.3g.ghtkgg.cn/nnews/993758.htm
- http://m.3g.ghtkgg.cn/nnews/7048281.htm
- http://m.3g.ghtkgg.cn/nnews/8905126.htm
- http://m.3g.ghtkgg.cn/nnews/856437.htm
- http://m.3g.ghtkgg.cn/nnews/07146.htm
- http://m.3g.ghtkgg.cn/nnews/727873.htm
- http://m.3g.ghtkgg.cn/nnews/398084.htm
- http://m.3g.ghtkgg.cn/nnews/7221723.htm
- http://m.3g.ghtkgg.cn/nnews/314669.htm
- http://m.3g.ghtkgg.cn/nnews/3110180.htm
- http://m.3g.ghtkgg.cn/nnews/21215.htm
- http://m.3g.ghtkgg.cn/nnews/2087802.htm
- http://m.3g.ghtkgg.cn/nnews/1354.htm
- http://m.3g.ghtkgg.cn/nnews/653424.htm
- http://m.3g.ghtkgg.cn/nnews/728602.htm
- http://m.3g.ghtkgg.cn/nnews/5267.htm
- http://m.3g.ghtkgg.cn/nnews/000333.htm
- http://m.3g.ghtkgg.cn/nnews/25916.htm
- http://m.3g.ghtkgg.cn/nnews/169494.htm
- http://m.3g.ghtkgg.cn/nnews/5773.htm
- http://m.3g.ghtkgg.cn/nnews/63502.htm
- http://m.3g.ghtkgg.cn/nnews/822879.htm
- http://m.3g.ghtkgg.cn/nnews/605710.htm
- http://m.3g.ghtkgg.cn/nnews/622558.htm
- http://m.3g.ghtkgg.cn/nnews/4964.htm
- http://m.3g.ghtkgg.cn/nnews/1728.htm
- http://m.3g.ghtkgg.cn/nnews/7842273.htm
- http://m.3g.ghtkgg.cn/nnews/58828.htm
- http://m.3g.ghtkgg.cn/nnews/519757.htm
- http://m.3g.ghtkgg.cn/nnews/1447.htm
- http://m.3g.ghtkgg.cn/nnews/2912.htm
- http://m.3g.ghtkgg.cn/nnews/930735.htm
- http://m.3g.ghtkgg.cn/nnews/934077.htm
- http://m.3g.ghtkgg.cn/nnews/250748.htm
- http://m.3g.ghtkgg.cn/nnews/598679.htm
- http://m.3g.ghtkgg.cn/nnews/5471888.htm
- http://m.3g.ghtkgg.cn/nnews/95520.htm
- http://m.3g.ghtkgg.cn/nnews/948655.htm
- http://m.3g.ghtkgg.cn/nnews/12710.htm
- http://m.3g.ghtkgg.cn/nnews/8205.htm
- http://m.3g.ghtkgg.cn/nnews/0675955.htm
- http://m.3g.ghtkgg.cn/nnews/91727.htm
- http://m.3g.ghtkgg.cn/nnews/11637.htm
- http://m.3g.ghtkgg.cn/nnews/6280.htm
- http://m.3g.ghtkgg.cn/nnews/67972.htm
- http://m.3g.ghtkgg.cn/nnews/14034.htm
- http://m.3g.ghtkgg.cn/nnews/5703.htm
- http://m.3g.ghtkgg.cn/nnews/49830.htm
- http://m.3g.ghtkgg.cn/nnews/320030.htm
- http://m.3g.ghtkgg.cn/nnews/11200.htm
- http://m.3g.ghtkgg.cn/nnews/1893958.htm
- http://m.3g.ghtkgg.cn/nnews/173486.htm
- http://m.3g.ghtkgg.cn/nnews/42569.htm
- http://m.3g.ghtkgg.cn/nnews/025523.htm
- http://m.3g.ghtkgg.cn/nnews/4333.htm
- http://m.3g.ghtkgg.cn/nnews/1225326.htm
- http://m.3g.ghtkgg.cn/nnews/7373.htm
- http://m.3g.ghtkgg.cn/nnews/8970.htm
- http://m.3g.ghtkgg.cn/nnews/924252.htm
- http://m.3g.ghtkgg.cn/nnews/5721640.htm
- http://m.3g.ghtkgg.cn/nnews/0492.htm
- http://m.3g.ghtkgg.cn/nnews/08432.htm
- http://m.3g.ghtkgg.cn/nnews/74998.htm
- http://m.3g.ghtkgg.cn/nnews/37035.htm
- http://m.3g.ghtkgg.cn/nnews/01668.htm
- http://m.3g.ghtkgg.cn/nnews/66916.htm
- http://m.3g.ghtkgg.cn/nnews/285305.htm
- http://m.3g.ghtkgg.cn/nnews/2869.htm
- http://m.3g.ghtkgg.cn/nnews/1488.htm
- http://m.3g.ghtkgg.cn/nnews/698782.htm
- http://m.3g.ghtkgg.cn/nnews/7200635.htm
- http://m.3g.ghtkgg.cn/nnews/63409.htm
- http://m.3g.ghtkgg.cn/nnews/0008.htm

## 项目结构

```
newsfetch-link-aggregator/
├── main.py                          # 项目入口，解析命令行参数并启动抓取或调度模式
├── requirements.txt                 # Python 依赖声明文件，锁定所有第三方库版本
├── config/
│   ├── settings.yaml               # 主配置文件，包含并发数、超时、重试策略及代理设置
│   ├── sources.list                # 用户自定义源站 URL 列表，每行一个链接（本项目的默认列表见资源列表章节）
│   └── logging.conf                # 日志级别与输出格式配置，支持 file 和 console 双输出
├── core/
│   ├── fetcher.py                  # 核心抓取模块，封装 requests 会话与重试机制，支持异步协程
│   ├── parser.py                   # 解析器工厂，根据 content-type 动态选择 HTML 或 JSON 解析策略
│   ├── deduplicator.py             # 基于布隆过滤器的 URL 去重模块，支持内存与 Redis 两种后端
│   └── exporter.py                 # 导出模块，支持 JSON、CSV、SQLite 三种格式，支持流式写入大文件
├── scheduler/
│   ├── cron_runner.py              # 基于 apscheduler 的定时任务启动器，读取 settings.yaml 中的调度表达式
│   └── task_queue.py               # 简单内存队列，用于在定时任务与抓取线程之间传递待处理 URL
├── utils/
│   ├── http_utils.py               # 辅助函数：UA 轮换、cookies 管理、响应时间计算
│   ├── text_cleaner.py             # 文本清洗工具：去除 HTML 标签、多余空白、提取纯文本
│   └── metrics.py                  # Prometheus 指标定义与注册，包含请求总数、失败率、响应时间直方图
├── data/
│   ├── archive/                    # 归档目录，按日期 YYYY-MM-DD 子目录存放原始响应 HTML
│   └── output/                     # 解析后的结构化输出目录，文件名格式为 output_YYYYMMDD_HHMMSS.json
├── tests/
│   ├── test_fetcher.py             # 单元测试：模拟 HTTP 请求与异常处理场景
│   ├── test_parser.py              # 单元测试：使用样本 HTML 验证解析规则的准确性
│   └── fixtures/                   # 测试用例的样本数据目录，包含静态 HTML 与期望的 JSON 输出
├── docs/
│   ├── getting-started.md          # 入门指南，覆盖安装、首次运行与常见问题排查
│   ├── configuration.md            # 配置项完整说明，附带示例 YAML 片段
│   ├── parsing-rules.md            # 内置解析规则详解，以及如何编写自定义 XPath 或正则解析器
│   └── output-formats.md           # 每种输出格式的字段映射、类型说明与示例数据
└── LICENSE                         # MIT 许可证文件，包含版权声明与免责条款
```

## 贡献指南

1. 复刻项目仓库并创建本地开发分支，建议分支命名格式为 `feature/your-feature-name` 或 `fix/issue-number`。所有新功能提交前需确保本地测试通过。

2. 安装开发依赖，包括 pytest、black、flake8 和 mypy，运行 `pip install -r requirements-dev.txt`。代码提交前必须执行 `black .` 进行格式化，并通过 `flake8` 和 `mypy` 静态检查。

3. 编写或更新单元测试，测试覆盖率不得低于 80%。对于新增的解析规则，需在 `tests/fixtures` 中添加对应的样本 HTML 文件，并在测试中验证解析结果与预期一致。

4. 更新文档，包括但不限于 `docs/` 目录下的相关说明、配置示例以及本 README 中的功能概览或安装要求。若变更涉及配置文件字段，需同步更新 `config/settings.yaml.example`。

5. 提交 Pull Request 到主仓库的 develop 分支，在 PR 描述中清晰说明变更目的、测试结果以及是否涉及破坏性变更。PR 需要至少一位项目维护者审核通过后方可合并。

## 常见问题

**Q: 抓取过程中出现大量 403 或 429 状态码，如何解决？**

A: 该项目默认使用移动端 UA 并启用了自动重试机制，但源站可能对单 IP 请求频率敏感。建议在 `config/settings.yaml` 中调低并发数（如从 10 降至 3），并启用 `request_delay` 参数（单位秒）。若仍无法解决，可配置代理池或使用 `utils/http_utils.py` 中的轮换 UA 列表。

**Q: 解析出的标题或正文内容不完整，包含大量 HTML 标签或乱码？**

A: 请检查源站是否使用了动态加载（如 AJAX 或客户端渲染）。当前 `core/parser.py` 基于静态 HTML 解析，若页面依赖 JavaScript 渲染，则需结合 Selenium 或 Playwright 进行改造。另外，可尝试在 `config/settings.yaml` 中调整 `encoding` 字段为 `utf-8` 或 `gbk`，以适配不同字符集。

**Q: 如何将抓取结果导入外部数据库或消息队列？**

A: 项目内置的 exporter 支持输出 JSON 和 CSV，可配合外部工具（如 `jq`、`logstash`、`filebeat`）进行二次处理。若需要直接写入 MySQL 或 MongoDB，建议在 `core/exporter.py` 中继承 `BaseExporter` 并实现自定义 `write_record` 方法。社区贡献者正在开发 Kafka 和 RabbitMQ 插件，预计下个版本合并。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:54
