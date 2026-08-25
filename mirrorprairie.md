# WebIndex 统一资源导航系统

WebIndex 是一个面向技术研究、数据采集与信息监控领域的轻量级统一资源导航系统，旨在将分散的互联网信息条目以结构化方式聚合、索引并提供快速检索入口。本项目专注于处理大规模外链资源的整理与呈现，适用于需要高效管理数百至数千条外部引用链接的技术团队、研究机构与个人开发者。

本项目第 131/300 批次收录了共计 300 个资源链接，覆盖新闻资讯、技术文档、数据公告等多种信息类型。WebIndex 不依赖复杂的后端框架，基于静态站点生成机制，可部署于任何支持 HTTP 服务的环境，同时提供可扩展的元数据标注接口，便于用户根据自身需求对资源条目进行二次分类与优先级标记。

## 功能概览

**批量资源收录与去重**：系统内置基于 URL 哈希与源站点域名的双重去重机制，确保同一资源条目不会被重复索引，同时支持手动白名单覆盖。

**多级分类与标签体系**：每个资源条目可关联多个分类标签，系统预置新闻、技术文档、公告、数据报表、学术参考五类基础标签，用户亦可自定义扩展标签。

**全文检索与高级过滤**：基于资源标题、来源域名、发布时间、标签组合等维度提供复合检索能力，支持布尔表达式与正则表达式过滤。

**定时抓取与状态监控**：周期性检测资源链接的可访问性，自动标记失效链接并生成状态报告，支持邮件与 Webhook 告警通知。

**元数据自动补全**：对未提供完整元数据的资源条目，系统自动尝试从 HTML 头部信息、Open Graph 协议、Schema.org 结构化数据中提取标题、描述与发布时间。

**访问统计与热度分析**：记录每个资源的点击次数、引用来源与访问时段分布，生成可视化热度趋势图表，辅助用户识别高价值信息源。

**数据导入导出兼容性**：支持 CSV、JSON、XML 三种格式的批量导入导出，方便与其他数据管理工具或内部系统进行数据交换。

## 应用场景

技术团队内部知识库建设：企业研发团队可将 WebIndex 部署为内部技术文档与外部参考资料的统一入口，将零散的官方文档链接、社区讨论帖、技术博客和 API 变更公告整合为可检索的知识库，减少团队成员查找资料的时间成本。

信息监控与舆情跟踪：运营或公关人员可利用 WebIndex 的定时抓取与状态监控功能，持续跟踪特定域名下的新闻页面和公告页面的更新状态，及时获取内容变更通知，避免遗漏关键信息。

数据采集管道前置管理：数据工程师可将 WebIndex 作为数据采集任务的前置资源管理模块，将待采集的 URL 清单按优先级、频率和来源分类存储，并通过导出接口与爬虫调度系统对接，实现采集任务的配置化管理。

个人研究资料归档：研究人员在阅读文献或浏览行业动态时，可将有价值的网页链接快速收录至 WebIndex，通过标签和检索功能构建个人研究资料库，并利用访问统计功能识别高频参考资源。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，请确保系统已安装 Git 与 Python 3.8 及以上版本。

```bash
git clone https://github.com/webindex/webindex-core.git
cd webindex-core
pip install -r requirements.txt
python scripts/init_db.py
python scripts/import_batch.py --batch 131 --source ./data/batch_131.json
python app.py --host 0.0.0.0 --port 8080
```

完成上述步骤后，访问 http://localhost:8080 即可进入 WebIndex 系统主界面。首次启动将自动创建默认管理员账户，初始密码输出于终端日志中，请及时修改。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 - 3.11 | 核心运行环境，3.12 版本暂未完成兼容性测试 |
| SQLite | 3.28.0 及以上 | 系统默认元数据存储引擎，支持并发读取但写入锁粒度较高，生产环境建议迁移至 PostgreSQL |
| Redis | 6.0 及以上 | 用于缓存检索结果与访问计数，非必须但强烈推荐，可显著提升高并发场景下的响应速度 |
| requests | 2.28.0 及以上 | HTTP 抓取与状态检测依赖库，需支持 SSL/TLS 1.2 以上协议 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析与元数据提取核心库，依赖 lxml 或 html5lib 解析器 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，若安装失败可回退至 html5lib 但解析速度将下降约 40% |
| cron / systemd timer | 任意版本 | 定时任务调度器，用于自动化执行抓取更新与状态检查，非必须但建议配置 |
| 磁盘空间 | 至少 500 MB | 用于存储 SQLite 数据库、日志文件及缓存数据，实际占用随收录条目数量线性增长 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide/quick-start.md | 如何快速收录第一批资源、如何检索已有条目、如何导出数据报表 |
| 管理员指南 | /docs/admin/deployment.md | 如何配置生产环境部署、如何设置定时抓取任务、如何迁移至 PostgreSQL |
| 开发者文档 | /docs/developer/api-reference.md | 如何扩展自定义元数据提取器、如何接入外部告警通道、如何修改前端页面模板 |
| 配置参考 | /docs/config/options.md | 所有环境变量与配置文件的完整说明，包括抓取超时、重试策略、缓存时长等参数 |
| 架构设计 | /docs/architecture/data-flow.md | 数据从导入、解析、索引到展示的完整流转路径，以及各模块的接口契约 |
| 故障排查 | /docs/troubleshooting/common-issues.md | 遇到检索无结果、抓取超时、数据库锁异常等常见问题时的诊断步骤与解决方案 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/9165320.htm
- http://m.3g.ghtkgg.cn/nnews/4627354.htm
- http://m.3g.ghtkgg.cn/nnews/785615.htm
- http://m.3g.ghtkgg.cn/nnews/9101647.htm
- http://m.3g.ghtkgg.cn/nnews/42194.htm
- http://m.3g.ghtkgg.cn/nnews/1393352.htm
- http://m.3g.ghtkgg.cn/nnews/8560.htm
- http://m.3g.ghtkgg.cn/nnews/761127.htm
- http://m.3g.ghtkgg.cn/nnews/070716.htm
- http://m.3g.ghtkgg.cn/nnews/3622.htm
- http://m.3g.ghtkgg.cn/nnews/88427.htm
- http://m.3g.ghtkgg.cn/nnews/11472.htm
- http://m.3g.ghtkgg.cn/nnews/5567450.htm
- http://m.3g.ghtkgg.cn/nnews/5219.htm
- http://m.3g.ghtkgg.cn/nnews/2053.htm
- http://m.3g.ghtkgg.cn/nnews/1740.htm
- http://m.3g.ghtkgg.cn/nnews/9606578.htm
- http://m.3g.ghtkgg.cn/nnews/098953.htm
- http://m.3g.ghtkgg.cn/nnews/712554.htm
- http://m.3g.ghtkgg.cn/nnews/5293.htm
- http://m.3g.ghtkgg.cn/nnews/2496445.htm
- http://m.3g.ghtkgg.cn/nnews/803563.htm
- http://m.3g.ghtkgg.cn/nnews/1110703.htm
- http://m.3g.ghtkgg.cn/nnews/5871.htm
- http://m.3g.ghtkgg.cn/nnews/697345.htm
- http://m.3g.ghtkgg.cn/nnews/80370.htm
- http://m.3g.ghtkgg.cn/nnews/6531909.htm
- http://m.3g.ghtkgg.cn/nnews/9067.htm
- http://m.3g.ghtkgg.cn/nnews/002612.htm
- http://m.3g.ghtkgg.cn/nnews/0863.htm
- http://m.3g.ghtkgg.cn/nnews/2369.htm
- http://m.3g.ghtkgg.cn/nnews/3084.htm
- http://m.3g.ghtkgg.cn/nnews/0231285.htm
- http://m.3g.ghtkgg.cn/nnews/062988.htm
- http://m.3g.ghtkgg.cn/nnews/48718.htm
- http://m.3g.ghtkgg.cn/nnews/8623.htm
- http://m.3g.ghtkgg.cn/nnews/5270147.htm
- http://m.3g.ghtkgg.cn/nnews/11223.htm
- http://m.3g.ghtkgg.cn/nnews/945731.htm
- http://m.3g.ghtkgg.cn/nnews/64711.htm
- http://m.3g.ghtkgg.cn/nnews/79409.htm
- http://m.3g.ghtkgg.cn/nnews/7670.htm
- http://m.3g.ghtkgg.cn/nnews/1161.htm
- http://m.3g.ghtkgg.cn/nnews/3839.htm
- http://m.3g.ghtkgg.cn/nnews/3961213.htm
- http://m.3g.ghtkgg.cn/nnews/8655.htm
- http://m.3g.ghtkgg.cn/nnews/9908.htm
- http://m.3g.ghtkgg.cn/nnews/52240.htm
- http://m.3g.ghtkgg.cn/nnews/33203.htm
- http://m.3g.ghtkgg.cn/nnews/965029.htm
- http://m.3g.ghtkgg.cn/nnews/64423.htm
- http://m.3g.ghtkgg.cn/nnews/21417.htm
- http://m.3g.ghtkgg.cn/nnews/49519.htm
- http://m.3g.ghtkgg.cn/nnews/96256.htm
- http://m.3g.ghtkgg.cn/nnews/4861292.htm
- http://m.3g.ghtkgg.cn/nnews/272020.htm
- http://m.3g.ghtkgg.cn/nnews/4639.htm
- http://m.3g.ghtkgg.cn/nnews/311006.htm
- http://m.3g.ghtkgg.cn/nnews/340573.htm
- http://m.3g.ghtkgg.cn/nnews/3196032.htm
- http://m.3g.ghtkgg.cn/nnews/10013.htm
- http://m.3g.ghtkgg.cn/nnews/0279722.htm
- http://m.3g.ghtkgg.cn/nnews/763797.htm
- http://m.3g.ghtkgg.cn/nnews/4235.htm
- http://m.3g.ghtkgg.cn/nnews/1094508.htm
- http://m.3g.ghtkgg.cn/nnews/6976120.htm
- http://m.3g.ghtkgg.cn/nnews/40600.htm
- http://m.3g.ghtkgg.cn/nnews/30046.htm
- http://m.3g.ghtkgg.cn/nnews/783496.htm
- http://m.3g.ghtkgg.cn/nnews/24306.htm
- http://m.3g.ghtkgg.cn/nnews/1404.htm
- http://m.3g.ghtkgg.cn/nnews/8687.htm
- http://m.3g.ghtkgg.cn/nnews/077867.htm
- http://m.3g.ghtkgg.cn/nnews/150243.htm
- http://m.3g.ghtkgg.cn/nnews/7488.htm
- http://m.3g.ghtkgg.cn/nnews/1489.htm
- http://m.3g.ghtkgg.cn/nnews/551092.htm
- http://m.3g.ghtkgg.cn/nnews/9397.htm
- http://m.3g.ghtkgg.cn/nnews/598218.htm
- http://m.3g.ghtkgg.cn/nnews/2621.htm
- http://m.3g.ghtkgg.cn/nnews/677706.htm
- http://m.3g.ghtkgg.cn/nnews/64896.htm
- http://m.3g.ghtkgg.cn/nnews/7279819.htm
- http://m.3g.ghtkgg.cn/nnews/443725.htm
- http://m.3g.ghtkgg.cn/nnews/7687.htm
- http://m.3g.ghtkgg.cn/nnews/6615.htm
- http://m.3g.ghtkgg.cn/nnews/04988.htm
- http://m.3g.ghtkgg.cn/nnews/9062344.htm
- http://m.3g.ghtkgg.cn/nnews/943762.htm
- http://m.3g.ghtkgg.cn/nnews/4509.htm
- http://m.3g.ghtkgg.cn/nnews/6590804.htm
- http://m.3g.ghtkgg.cn/nnews/487498.htm
- http://m.3g.ghtkgg.cn/nnews/1714.htm
- http://m.3g.ghtkgg.cn/nnews/881867.htm
- http://m.3g.ghtkgg.cn/nnews/057182.htm
- http://m.3g.ghtkgg.cn/nnews/26079.htm
- http://m.3g.ghtkgg.cn/nnews/3569970.htm
- http://m.3g.ghtkgg.cn/nnews/71538.htm
- http://m.3g.ghtkgg.cn/nnews/70518.htm
- http://m.3g.ghtkgg.cn/nnews/7585.htm
- http://m.3g.ghtkgg.cn/nnews/32312.htm
- http://m.3g.ghtkgg.cn/nnews/04708.htm
- http://m.3g.ghtkgg.cn/nnews/5026733.htm
- http://m.3g.ghtkgg.cn/nnews/232385.htm
- http://m.3g.ghtkgg.cn/nnews/025385.htm
- http://m.3g.ghtkgg.cn/nnews/8674130.htm
- http://m.3g.ghtkgg.cn/nnews/939832.htm
- http://m.3g.ghtkgg.cn/nnews/8380409.htm
- http://m.3g.ghtkgg.cn/nnews/65802.htm
- http://m.3g.ghtkgg.cn/nnews/2457.htm
- http://m.3g.ghtkgg.cn/nnews/941877.htm
- http://m.3g.ghtkgg.cn/nnews/6323767.htm
- http://m.3g.ghtkgg.cn/nnews/1203.htm
- http://m.3g.ghtkgg.cn/nnews/7215853.htm
- http://m.3g.ghtkgg.cn/nnews/8856.htm
- http://m.3g.ghtkgg.cn/nnews/021483.htm
- http://m.3g.ghtkgg.cn/nnews/6585412.htm
- http://m.3g.ghtkgg.cn/nnews/2662911.htm
- http://m.3g.ghtkgg.cn/nnews/41212.htm
- http://m.3g.ghtkgg.cn/nnews/172912.htm
- http://m.3g.ghtkgg.cn/nnews/7425031.htm
- http://m.3g.ghtkgg.cn/nnews/8346329.htm
- http://m.3g.ghtkgg.cn/nnews/2783314.htm
- http://m.3g.ghtkgg.cn/nnews/8214651.htm
- http://m.3g.ghtkgg.cn/nnews/35154.htm
- http://m.3g.ghtkgg.cn/nnews/0175.htm
- http://m.3g.ghtkgg.cn/nnews/457441.htm
- http://m.3g.ghtkgg.cn/nnews/569359.htm
- http://m.3g.ghtkgg.cn/nnews/63668.htm
- http://m.3g.ghtkgg.cn/nnews/1167216.htm
- http://m.3g.ghtkgg.cn/nnews/0440844.htm
- http://m.3g.ghtkgg.cn/nnews/204780.htm
- http://m.3g.ghtkgg.cn/nnews/9500849.htm
- http://m.3g.ghtkgg.cn/nnews/7705360.htm
- http://m.3g.ghtkgg.cn/nnews/431102.htm
- http://m.3g.ghtkgg.cn/nnews/79102.htm
- http://m.3g.ghtkgg.cn/nnews/703619.htm
- http://m.3g.ghtkgg.cn/nnews/2202.htm
- http://m.3g.ghtkgg.cn/nnews/8851.htm
- http://m.3g.ghtkgg.cn/nnews/658251.htm
- http://m.3g.ghtkgg.cn/nnews/92824.htm
- http://m.3g.ghtkgg.cn/nnews/4912902.htm
- http://m.3g.ghtkgg.cn/nnews/700385.htm
- http://m.3g.ghtkgg.cn/nnews/69328.htm
- http://m.3g.ghtkgg.cn/nnews/235049.htm
- http://m.3g.ghtkgg.cn/nnews/7440914.htm
- http://m.3g.ghtkgg.cn/nnews/422193.htm
- http://m.3g.ghtkgg.cn/nnews/464433.htm
- http://m.3g.ghtkgg.cn/nnews/72826.htm
- http://m.3g.ghtkgg.cn/nnews/3660.htm
- http://m.3g.ghtkgg.cn/nnews/4424.htm
- http://m.3g.ghtkgg.cn/nnews/9823740.htm
- http://m.3g.ghtkgg.cn/nnews/4653.htm
- http://m.3g.ghtkgg.cn/nnews/8524.htm
- http://m.3g.ghtkgg.cn/nnews/4670767.htm
- http://m.3g.ghtkgg.cn/nnews/14444.htm
- http://m.3g.ghtkgg.cn/nnews/065821.htm
- http://m.3g.ghtkgg.cn/nnews/250907.htm
- http://m.3g.ghtkgg.cn/nnews/048516.htm
- http://m.3g.ghtkgg.cn/nnews/6799521.htm
- http://m.3g.ghtkgg.cn/nnews/623672.htm
- http://m.3g.ghtkgg.cn/nnews/0743963.htm
- http://m.3g.ghtkgg.cn/nnews/94732.htm
- http://m.3g.ghtkgg.cn/nnews/3450057.htm
- http://m.3g.ghtkgg.cn/nnews/8375.htm
- http://m.3g.ghtkgg.cn/nnews/23029.htm
- http://m.3g.ghtkgg.cn/nnews/4600912.htm
- http://m.3g.ghtkgg.cn/nnews/9310671.htm
- http://m.3g.ghtkgg.cn/nnews/778247.htm
- http://m.3g.ghtkgg.cn/nnews/43299.htm
- http://m.3g.ghtkgg.cn/nnews/9824243.htm
- http://m.3g.ghtkgg.cn/nnews/9591.htm
- http://m.3g.ghtkgg.cn/nnews/2310.htm
- http://m.3g.ghtkgg.cn/nnews/6257.htm
- http://m.3g.ghtkgg.cn/nnews/87182.htm
- http://m.3g.ghtkgg.cn/nnews/555834.htm
- http://m.3g.ghtkgg.cn/nnews/6236.htm
- http://m.3g.ghtkgg.cn/nnews/6000531.htm
- http://m.3g.ghtkgg.cn/nnews/9168.htm
- http://m.3g.ghtkgg.cn/nnews/0829751.htm
- http://m.3g.ghtkgg.cn/nnews/7617614.htm
- http://m.3g.ghtkgg.cn/nnews/4883610.htm
- http://m.3g.ghtkgg.cn/nnews/3228.htm
- http://m.3g.ghtkgg.cn/nnews/738776.htm
- http://m.3g.ghtkgg.cn/nnews/6466.htm
- http://m.3g.ghtkgg.cn/nnews/8137560.htm
- http://m.3g.ghtkgg.cn/nnews/032181.htm
- http://m.3g.ghtkgg.cn/nnews/4041.htm
- http://m.3g.ghtkgg.cn/nnews/8852.htm
- http://m.3g.ghtkgg.cn/nnews/07312.htm
- http://m.3g.ghtkgg.cn/nnews/6898.htm
- http://m.3g.ghtkgg.cn/nnews/867601.htm
- http://m.3g.ghtkgg.cn/nnews/4259.htm
- http://m.3g.ghtkgg.cn/nnews/1904.htm
- http://m.3g.ghtkgg.cn/nnews/47876.htm
- http://m.3g.ghtkgg.cn/nnews/587272.htm
- http://m.3g.ghtkgg.cn/nnews/8213.htm
- http://m.3g.ghtkgg.cn/nnews/85478.htm
- http://m.3g.ghtkgg.cn/nnews/058039.htm
- http://m.3g.ghtkgg.cn/nnews/34559.htm
- http://m.3g.ghtkgg.cn/nnews/91682.htm
- http://m.3g.ghtkgg.cn/nnews/641362.htm
- http://m.3g.ghtkgg.cn/nnews/466404.htm
- http://m.3g.ghtkgg.cn/nnews/12264.htm
- http://m.3g.ghtkgg.cn/nnews/1431.htm
- http://m.3g.ghtkgg.cn/nnews/5570502.htm
- http://m.3g.ghtkgg.cn/nnews/6763.htm
- http://m.3g.ghtkgg.cn/nnews/982486.htm
- http://m.3g.ghtkgg.cn/nnews/485354.htm
- http://m.3g.ghtkgg.cn/nnews/1061.htm
- http://m.3g.ghtkgg.cn/nnews/318213.htm
- http://m.3g.ghtkgg.cn/nnews/0726.htm
- http://m.3g.ghtkgg.cn/nnews/36490.htm
- http://m.3g.ghtkgg.cn/nnews/84094.htm
- http://m.3g.ghtkgg.cn/nnews/716070.htm
- http://m.3g.ghtkgg.cn/nnews/0121658.htm
- http://m.3g.ghtkgg.cn/nnews/714499.htm
- http://m.3g.ghtkgg.cn/nnews/385178.htm
- http://m.3g.ghtkgg.cn/nnews/0283.htm
- http://m.3g.ghtkgg.cn/nnews/3251781.htm
- http://m.3g.ghtkgg.cn/nnews/043328.htm
- http://m.3g.ghtkgg.cn/nnews/795312.htm
- http://m.3g.ghtkgg.cn/nnews/957736.htm
- http://m.3g.ghtkgg.cn/nnews/392745.htm
- http://m.3g.ghtkgg.cn/nnews/0645.htm
- http://m.3g.ghtkgg.cn/nnews/4095893.htm
- http://m.3g.ghtkgg.cn/nnews/8691466.htm
- http://m.3g.ghtkgg.cn/nnews/63425.htm
- http://m.3g.ghtkgg.cn/nnews/26001.htm
- http://m.3g.ghtkgg.cn/nnews/7410948.htm
- http://m.3g.ghtkgg.cn/nnews/744016.htm
- http://m.3g.ghtkgg.cn/nnews/945211.htm
- http://m.3g.ghtkgg.cn/nnews/6210.htm
- http://m.3g.ghtkgg.cn/nnews/7807344.htm
- http://m.3g.ghtkgg.cn/nnews/5201124.htm
- http://m.3g.ghtkgg.cn/nnews/4297341.htm
- http://m.3g.ghtkgg.cn/nnews/20381.htm
- http://m.3g.ghtkgg.cn/nnews/488903.htm
- http://m.3g.ghtkgg.cn/nnews/66735.htm
- http://m.3g.ghtkgg.cn/nnews/64981.htm
- http://m.3g.ghtkgg.cn/nnews/3534886.htm
- http://m.3g.ghtkgg.cn/nnews/015106.htm
- http://m.3g.ghtkgg.cn/nnews/1365.htm
- http://m.3g.ghtkgg.cn/nnews/185327.htm
- http://m.3g.ghtkgg.cn/nnews/7556.htm
- http://m.3g.ghtkgg.cn/nnews/4503.htm
- http://m.3g.ghtkgg.cn/nnews/22082.htm
- http://m.3g.ghtkgg.cn/nnews/73689.htm
- http://m.3g.ghtkgg.cn/nnews/397518.htm
- http://m.3g.ghtkgg.cn/nnews/45660.htm
- http://m.3g.ghtkgg.cn/nnews/63408.htm
- http://m.3g.ghtkgg.cn/nnews/78427.htm
- http://m.3g.ghtkgg.cn/nnews/071697.htm
- http://m.3g.ghtkgg.cn/nnews/209675.htm
- http://m.3g.ghtkgg.cn/nnews/595357.htm
- http://m.3g.ghtkgg.cn/nnews/70143.htm
- http://m.3g.ghtkgg.cn/nnews/28737.htm
- http://m.3g.ghtkgg.cn/nnews/9244.htm
- http://m.3g.ghtkgg.cn/nnews/8105.htm
- http://m.3g.ghtkgg.cn/nnews/2896.htm
- http://m.3g.ghtkgg.cn/nnews/45759.htm
- http://m.3g.ghtkgg.cn/nnews/8538.htm
- http://m.3g.ghtkgg.cn/nnews/513042.htm
- http://m.3g.ghtkgg.cn/nnews/39517.htm
- http://m.3g.ghtkgg.cn/nnews/35622.htm
- http://m.3g.ghtkgg.cn/nnews/1657.htm
- http://m.3g.ghtkgg.cn/nnews/5540.htm
- http://m.3g.ghtkgg.cn/nnews/39362.htm
- http://m.3g.ghtkgg.cn/nnews/254965.htm
- http://m.3g.ghtkgg.cn/nnews/3118216.htm
- http://m.3g.ghtkgg.cn/nnews/793485.htm
- http://m.3g.ghtkgg.cn/nnews/11632.htm
- http://m.3g.ghtkgg.cn/nnews/7307420.htm
- http://m.3g.ghtkgg.cn/nnews/040589.htm
- http://m.3g.ghtkgg.cn/nnews/55889.htm
- http://m.3g.ghtkgg.cn/nnews/0648330.htm
- http://m.3g.ghtkgg.cn/nnews/078681.htm
- http://m.3g.ghtkgg.cn/nnews/4220061.htm
- http://m.3g.ghtkgg.cn/nnews/7355605.htm
- http://m.3g.ghtkgg.cn/nnews/379278.htm
- http://m.3g.ghtkgg.cn/nnews/2614872.htm
- http://m.3g.ghtkgg.cn/nnews/099841.htm
- http://m.3g.ghtkgg.cn/nnews/2455465.htm
- http://m.3g.ghtkgg.cn/nnews/46545.htm
- http://m.3g.ghtkgg.cn/nnews/1109.htm
- http://m.3g.ghtkgg.cn/nnews/94035.htm
- http://m.3g.ghtkgg.cn/nnews/8998491.htm
- http://m.3g.ghtkgg.cn/nnews/816654.htm
- http://m.3g.ghtkgg.cn/nnews/45964.htm
- http://m.3g.ghtkgg.cn/nnews/5413406.htm
- http://m.3g.ghtkgg.cn/nnews/5318720.htm
- http://m.3g.ghtkgg.cn/nnews/18199.htm
- http://m.3g.ghtkgg.cn/nnews/63093.htm
- http://m.3g.ghtkgg.cn/nnews/90533.htm
- http://m.3g.ghtkgg.cn/nnews/5687933.htm
- http://m.3g.ghtkgg.cn/nnews/963642.htm
- http://m.3g.ghtkgg.cn/nnews/592243.htm
- http://m.3g.ghtkgg.cn/nnews/13946.htm
- http://m.3g.ghtkgg.cn/nnews/66860.htm
- http://m.3g.ghtkgg.cn/nnews/0963829.htm

## 项目结构

```
webindex-core/
├── app/                                # 主应用模块
│   ├── __init__.py                     # 应用工厂与配置加载入口
│   ├── routes/                         # 路由层，处理 HTTP 请求与响应
│   │   ├── index.py                    # 首页检索与资源列表展示路由
│   │   ├── resource.py                 # 单个资源详情与状态操作路由
│   │   └── admin.py                    # 后台管理界面与批量操作路由
│   ├── services/                       # 业务逻辑层，封装核心功能
│   │   ├── fetcher.py                  # HTTP 抓取与链接状态检测服务
│   │   ├── parser.py                   # HTML 元数据提取与结构化解析
│   │   ├── indexer.py                  # 倒排索引构建与检索服务
│   │   └── stats.py                    # 访问统计与热度计算服务
│   └── templates/                      # Jinja2 前端模板文件
│       ├── base.html                   # 基础布局模板，含导航栏与页脚
│       ├── resource_list.html          # 资源列表与分页展示模板
│       └── resource_detail.html        # 单个资源详情与元数据显示模板
├── scripts/                            # 运维与数据管理脚本
│   ├── init_db.py                      # 初始化 SQLite 数据库表结构
│   ├── import_batch.py                 # 批量导入资源条目，支持批次号参数
│   ├── export_csv.py                   # 导出全量资源数据为 CSV 格式
│   └── check_links.py                  # 批量检测所有链接可用性并生成报告
├── data/                               # 数据存储目录
│   ├── batch_131.json                  # 第 131 批次原始数据，JSON 格式
│   ├── cache/                          # 页面抓取缓存目录，按域名分片存储
│   └── logs/                           # 应用日志与抓取任务日志
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置，含抓取超时、重试次数等
│   ├── production.yaml                 # 生产环境覆盖配置
│   └── schema.json                     # 配置字段的 JSON Schema 校验定义
├── tests/                              # 单元测试与集成测试
│   ├── test_fetcher.py                 # 抓取服务单元测试
│   ├── test_parser.py                  # 解析服务单元测试
│   └── fixtures/                       # 测试用静态 HTML 样本文件
├── requirements.txt                    # Python 依赖清单，含版本锁定
├── setup.py                            # 打包安装脚本，支持 pip install -e .
├── app.py                              # 应用启动入口，含命令行参数解析
└── README.md                           # 本文档
```

## 贡献指南

本项目建设遵循开源协作规范，欢迎各类形式的贡献，包括但不限于功能建议、缺陷报告、代码提交与文档完善。请遵循以下步骤参与贡献：

1. 在 GitHub 仓库页面点击 Fork 按钮，将本仓库复制至个人账号下，随后将 Fork 后的仓库克隆至本地开发环境。建议在克隆前检查本地 Git 版本是否为 2.25 及以上，以避免子模块处理异常。

2. 新建功能分支或缺陷修复分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式，描述部分使用英文小写与连字符，例如 `feature/batch-import-optimize`。请在分支上完成代码编写与本地自测，确保所有现有单元测试通过。

3. 编写或更新与本次变更对应的单元测试用例，测试文件置于 `tests/` 目录下，命名与被测模块保持对应。新增功能应达到 80% 以上的行覆盖率，缺陷修复应附带可复现的测试用例。

4. 提交代码前运行代码格式检查与静态分析工具，本项目使用 black 作为代码格式化工具，flake8 作为静态检查工具，提交前执行 `make lint` 或 `tox -e lint` 确保无风格告警。提交信息遵循 Conventional Commits 规范，格式为 `<type>(<scope>): <subject>`。

5. 将分支推送至个人远程仓库，随后在 GitHub 页面发起 Pull Request 至本仓库的 main 分支。PR 描述中需清晰说明变更目的、实现方式与测试结果，并关联相关 Issue 编号。项目维护者将在 5 个工作日内完成审核与合并。

## 常见问题

**Q: 导入批量资源时提示 JSON 格式校验失败，应如何排查？**

A:

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:01
