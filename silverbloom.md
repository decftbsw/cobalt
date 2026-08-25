# NewsLink Aggregate Hub

NewsLink Aggregate Hub 是一个面向技术资讯聚合与历史新闻存档检索的开源外链汇总系统。项目定位于为开发者、数据分析师以及资讯研究者提供结构化的历史新闻链接资源池，通过统一的条目索引机制，将散落的新闻页面整合为可被检索、归类与二次处理的标准化数据集。本项目的目标用户包括需要批量获取新闻语料的自然语言处理工程师、搭建资讯看板的全栈开发者，以及对特定时间点事件进行回溯调查的研究人员。

该项目不提供新闻内容的重写或存储，而是作为高质量外链的导航与组织工具，解决从零散 URL 中高效定位和筛选有效信息的问题。通过本项目的索引结构，用户可以快速获取第 29/300 批次的全部外链资源，并结合项目提供的辅助工具完成链接有效性检测、分类标注与导出等操作。

## 功能概览

**批量链接导入**：支持一次性导入大批量 URL 条目，自动解析并提取文件名与扩展名信息，建立基础索引。

**去重与有效性检测**：内置基于 URL 路径和域名指纹的重复检测算法，可标记状态码异常的链接并生成报告。

**自定义标签分类**：允许用户为每条外链添加多个自定义标签，实现基于主题、来源或时间维度的灵活分类。

**全文元数据提取**：对于可访问的 HTML 页面，自动提取标题、meta description 以及正文前 200 字符作为摘要信息。

**索引导出与集成**：支持将索引数据导出为 CSV、JSON 或 Markdown 表格格式，便于嵌入其他文档或导入数据库。

**定时更新机制**：提供可配置的定时任务，定期重新检测已收录链接的可用性，并更新元数据缓存。

## 应用场景

**历史事件资料整理**：研究人员在回溯特定时间段（如某年某月的突发事件）时，可通过本项目的批次索引快速定位到当日的新闻外链集合，无需手动翻阅大量归档页面，显著提升资料收集效率。

**新闻语料采集管道**：自然语言处理团队构建新闻预训练语料时，利用本项目的链接池作为数据源的起始节点，配合自动化采集脚本批量下载页面内容，再经过清洗和格式化后注入语料库。

**个人资讯监控看板**：开发者基于本项目提供的链接列表，构建轻量级监控面板，定时检测外链的可访问性并抓取页面标题更新，形成个人化的信息流展示页面，避免频繁手动访问源站。

**链接资源归档备份**：内容管理员使用本项目的导出功能，将外链列表整合到企业内部的文档系统中，配合 Web 归档工具（如 Wayback Machine 集成）对重要新闻页面进行多版本备份。

## 快速开始

以下步骤指导您在本地环境中快速启动 NewsLink Aggregate Hub 的基础服务。

```bash
# 克隆项目仓库
git clone https://github.com/example/newslink-hub.git

# 进入项目目录
cd newslink-hub

# 安装项目依赖（使用 pip 安装 Python 后端依赖）
pip install -r requirements.txt

# 初始化本地 SQLite 索引数据库
python scripts/init_db.py

# 导入本批次（第29批）的链接列表
python scripts/import_batch.py --batch 29 --file ./data/batch_29_urls.txt

# 启动本地开发服务器（默认监听 127.0.0.1:8000）
python app.py
```

访问 `http://127.0.0.1:8000` 即可查看本批次链接的索引概览页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 后端服务运行环境，用于 API 和索引管理 |
| SQLite | 3.31.0 及以上 | 默认轻量级索引数据库，无需额外配置 |
| requests | 2.25.0 及以上 | 用于链接有效性检测和元数据提取的 HTTP 客户端库 |
| beautifulsoup4 | 4.9.0 及以上 | HTML 页面解析依赖，用于提取标题和摘要信息 |
| lxml | 4.6.0 及以上 | BeautifulSoup 的底层解析器，提供高性能 HTML 解析能力 |
| cron | 系统内置（Linux/macOS） | 定时任务调度器，用于自动化链接更新检测（Windows 用户需自行配置任务计划程序） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | `docs/getting-started.md` | 如何快速完成安装并导入第一批链接索引？ |
| 数据导入手册 | `docs/import-guide.md` | 支持哪些导入格式？如何自定义批次编号和标签规则？ |
| API 参考文档 | `docs/api-reference.md` | 如何通过 RESTful API 程序化查询链接状态、更新元数据？ |
| 运维与调优 | `docs/operations.md` | 如何配置定时检测频率？如何处理大规模链接池的性能瓶颈？ |

## 资源列表

- http://m.3g.oexnr.cn/nnews/7573510.htm
- http://m.3g.oexnr.cn/nnews/1038103.htm
- http://m.3g.oexnr.cn/nnews/08876.htm
- http://m.3g.oexnr.cn/nnews/3760420.htm
- http://m.3g.oexnr.cn/nnews/05320.htm
- http://m.3g.oexnr.cn/nnews/4874001.htm
- http://m.3g.oexnr.cn/nnews/289329.htm
- http://m.3g.oexnr.cn/nnews/14299.htm
- http://m.3g.oexnr.cn/nnews/53776.htm
- http://m.3g.oexnr.cn/nnews/08024.htm
- http://m.3g.oexnr.cn/nnews/7123270.htm
- http://m.3g.oexnr.cn/nnews/6489.htm
- http://m.3g.oexnr.cn/nnews/545817.htm
- http://m.3g.oexnr.cn/nnews/60281.htm
- http://m.3g.oexnr.cn/nnews/0912.htm
- http://m.3g.oexnr.cn/nnews/2611151.htm
- http://m.3g.oexnr.cn/nnews/390441.htm
- http://m.3g.oexnr.cn/nnews/65386.htm
- http://m.3g.oexnr.cn/nnews/80402.htm
- http://m.3g.oexnr.cn/nnews/2022.htm
- http://m.3g.oexnr.cn/nnews/606979.htm
- http://m.3g.oexnr.cn/nnews/37061.htm
- http://m.3g.oexnr.cn/nnews/072527.htm
- http://m.3g.oexnr.cn/nnews/1764491.htm
- http://m.3g.oexnr.cn/nnews/248493.htm
- http://m.3g.oexnr.cn/nnews/0061.htm
- http://m.3g.oexnr.cn/nnews/2929.htm
- http://m.3g.oexnr.cn/nnews/41440.htm
- http://m.3g.oexnr.cn/nnews/155039.htm
- http://m.3g.oexnr.cn/nnews/487900.htm
- http://m.3g.oexnr.cn/nnews/1495.htm
- http://m.3g.oexnr.cn/nnews/8375298.htm
- http://m.3g.oexnr.cn/nnews/392714.htm
- http://m.3g.oexnr.cn/nnews/1846.htm
- http://m.3g.oexnr.cn/nnews/5772.htm
- http://m.3g.oexnr.cn/nnews/0235532.htm
- http://m.3g.oexnr.cn/nnews/925549.htm
- http://m.3g.oexnr.cn/nnews/5744.htm
- http://m.3g.oexnr.cn/nnews/7042945.htm
- http://m.3g.oexnr.cn/nnews/44010.htm
- http://m.3g.oexnr.cn/nnews/042973.htm
- http://m.3g.oexnr.cn/nnews/437415.htm
- http://m.3g.oexnr.cn/nnews/9951.htm
- http://m.3g.oexnr.cn/nnews/505302.htm
- http://m.3g.oexnr.cn/nnews/0341996.htm
- http://m.3g.oexnr.cn/nnews/8090127.htm
- http://m.3g.oexnr.cn/nnews/7891.htm
- http://m.3g.oexnr.cn/nnews/8293581.htm
- http://m.3g.oexnr.cn/nnews/553427.htm
- http://m.3g.oexnr.cn/nnews/798374.htm
- http://m.3g.oexnr.cn/nnews/9520.htm
- http://m.3g.oexnr.cn/nnews/6545.htm
- http://m.3g.oexnr.cn/nnews/22529.htm
- http://m.3g.oexnr.cn/nnews/79142.htm
- http://m.3g.oexnr.cn/nnews/8884354.htm
- http://m.3g.oexnr.cn/nnews/089637.htm
- http://m.3g.oexnr.cn/nnews/500735.htm
- http://m.3g.oexnr.cn/nnews/827562.htm
- http://m.3g.oexnr.cn/nnews/168211.htm
- http://m.3g.oexnr.cn/nnews/6046.htm
- http://m.3g.oexnr.cn/nnews/8033816.htm
- http://m.3g.oexnr.cn/nnews/2054563.htm
- http://m.3g.oexnr.cn/nnews/82935.htm
- http://m.3g.oexnr.cn/nnews/3600519.htm
- http://m.3g.oexnr.cn/nnews/25263.htm
- http://m.3g.oexnr.cn/nnews/873331.htm
- http://m.3g.oexnr.cn/nnews/55023.htm
- http://m.3g.oexnr.cn/nnews/885416.htm
- http://m.3g.oexnr.cn/nnews/684555.htm
- http://m.3g.oexnr.cn/nnews/86347.htm
- http://m.3g.oexnr.cn/nnews/285089.htm
- http://m.3g.oexnr.cn/nnews/8838.htm
- http://m.3g.oexnr.cn/nnews/0944047.htm
- http://m.3g.oexnr.cn/nnews/1103639.htm
- http://m.3g.oexnr.cn/nnews/5025940.htm
- http://m.3g.oexnr.cn/nnews/899165.htm
- http://m.3g.oexnr.cn/nnews/290455.htm
- http://m.3g.oexnr.cn/nnews/2939.htm
- http://m.3g.oexnr.cn/nnews/8916.htm
- http://m.3g.oexnr.cn/nnews/4871931.htm
- http://m.3g.oexnr.cn/nnews/5953418.htm
- http://m.3g.oexnr.cn/nnews/6435008.htm
- http://m.3g.oexnr.cn/nnews/03259.htm
- http://m.3g.oexnr.cn/nnews/97161.htm
- http://m.3g.oexnr.cn/nnews/45456.htm
- http://m.3g.oexnr.cn/nnews/7979.htm
- http://m.3g.oexnr.cn/nnews/07718.htm
- http://m.3g.oexnr.cn/nnews/2222.htm
- http://m.3g.oexnr.cn/nnews/10437.htm
- http://m.3g.oexnr.cn/nnews/643696.htm
- http://m.3g.oexnr.cn/nnews/29986.htm
- http://m.3g.oexnr.cn/nnews/40076.htm
- http://m.3g.oexnr.cn/nnews/6064328.htm
- http://m.3g.oexnr.cn/nnews/2449.htm
- http://m.3g.oexnr.cn/nnews/304757.htm
- http://m.3g.oexnr.cn/nnews/59392.htm
- http://m.3g.oexnr.cn/nnews/103178.htm
- http://m.3g.oexnr.cn/nnews/414025.htm
- http://m.3g.oexnr.cn/nnews/1580.htm
- http://m.3g.oexnr.cn/nnews/1881.htm
- http://m.3g.oexnr.cn/nnews/3823.htm
- http://m.3g.oexnr.cn/nnews/52936.htm
- http://m.3g.oexnr.cn/nnews/56264.htm
- http://m.3g.oexnr.cn/nnews/413807.htm
- http://m.3g.oexnr.cn/nnews/9709.htm
- http://m.3g.oexnr.cn/nnews/1627422.htm
- http://m.3g.oexnr.cn/nnews/3199.htm
- http://m.3g.oexnr.cn/nnews/3156.htm
- http://m.3g.oexnr.cn/nnews/898659.htm
- http://m.3g.oexnr.cn/nnews/5748603.htm
- http://m.3g.oexnr.cn/nnews/1370.htm
- http://m.3g.oexnr.cn/nnews/288569.htm
- http://m.3g.oexnr.cn/nnews/3770.htm
- http://m.3g.oexnr.cn/nnews/21067.htm
- http://m.3g.oexnr.cn/nnews/6219136.htm
- http://m.3g.oexnr.cn/nnews/9806.htm
- http://m.3g.oexnr.cn/nnews/4315.htm
- http://m.3g.oexnr.cn/nnews/6022215.htm
- http://m.3g.oexnr.cn/nnews/5449.htm
- http://m.3g.oexnr.cn/nnews/7328538.htm
- http://m.3g.oexnr.cn/nnews/751381.htm
- http://m.3g.oexnr.cn/nnews/394689.htm
- http://m.3g.oexnr.cn/nnews/60871.htm
- http://m.3g.oexnr.cn/nnews/7642272.htm
- http://m.3g.oexnr.cn/nnews/774835.htm
- http://m.3g.oexnr.cn/nnews/25667.htm
- http://m.3g.oexnr.cn/nnews/639693.htm
- http://m.3g.oexnr.cn/nnews/8774603.htm
- http://m.3g.oexnr.cn/nnews/8411492.htm
- http://m.3g.oexnr.cn/nnews/342003.htm
- http://m.3g.oexnr.cn/nnews/115508.htm
- http://m.3g.oexnr.cn/nnews/0855229.htm
- http://m.3g.oexnr.cn/nnews/3045.htm
- http://m.3g.oexnr.cn/nnews/8769726.htm
- http://m.3g.oexnr.cn/nnews/1094586.htm
- http://m.3g.oexnr.cn/nnews/85105.htm
- http://m.3g.oexnr.cn/nnews/8606.htm
- http://m.3g.oexnr.cn/nnews/5932.htm
- http://m.3g.oexnr.cn/nnews/4882.htm
- http://m.3g.oexnr.cn/nnews/2121669.htm
- http://m.3g.oexnr.cn/nnews/931600.htm
- http://m.3g.oexnr.cn/nnews/29504.htm
- http://m.3g.oexnr.cn/nnews/863400.htm
- http://m.3g.oexnr.cn/nnews/263763.htm
- http://m.3g.oexnr.cn/nnews/832370.htm
- http://m.3g.oexnr.cn/nnews/2534.htm
- http://m.3g.oexnr.cn/nnews/4333098.htm
- http://m.3g.oexnr.cn/nnews/2452889.htm
- http://m.3g.oexnr.cn/nnews/3940.htm
- http://m.3g.oexnr.cn/nnews/638957.htm
- http://m.3g.oexnr.cn/nnews/514207.htm
- http://m.3g.oexnr.cn/nnews/11513.htm
- http://m.3g.oexnr.cn/nnews/664911.htm
- http://m.3g.oexnr.cn/nnews/01545.htm
- http://m.3g.oexnr.cn/nnews/492513.htm
- http://m.3g.oexnr.cn/nnews/665330.htm
- http://m.3g.oexnr.cn/nnews/4697.htm
- http://m.3g.oexnr.cn/nnews/27622.htm
- http://m.3g.oexnr.cn/nnews/89251.htm
- http://m.3g.oexnr.cn/nnews/74773.htm
- http://m.3g.oexnr.cn/nnews/182788.htm
- http://m.3g.oexnr.cn/nnews/722273.htm
- http://m.3g.oexnr.cn/nnews/6921346.htm
- http://m.3g.oexnr.cn/nnews/03978.htm
- http://m.3g.oexnr.cn/nnews/7141.htm
- http://m.3g.oexnr.cn/nnews/14672.htm
- http://m.3g.oexnr.cn/nnews/284254.htm
- http://m.3g.oexnr.cn/nnews/60194.htm
- http://m.3g.oexnr.cn/nnews/38083.htm
- http://m.3g.oexnr.cn/nnews/376712.htm
- http://m.3g.oexnr.cn/nnews/4351859.htm
- http://m.3g.oexnr.cn/nnews/36188.htm
- http://m.3g.oexnr.cn/nnews/891634.htm
- http://m.3g.oexnr.cn/nnews/74361.htm
- http://m.3g.oexnr.cn/nnews/176007.htm
- http://m.3g.oexnr.cn/nnews/09121.htm
- http://m.3g.oexnr.cn/nnews/00835.htm
- http://m.3g.oexnr.cn/nnews/7767.htm
- http://m.3g.oexnr.cn/nnews/3577102.htm
- http://m.3g.oexnr.cn/nnews/66063.htm
- http://m.3g.oexnr.cn/nnews/122892.htm
- http://m.3g.oexnr.cn/nnews/2900256.htm
- http://m.3g.oexnr.cn/nnews/179141.htm
- http://m.3g.oexnr.cn/nnews/3505969.htm
- http://m.3g.oexnr.cn/nnews/3613.htm
- http://m.3g.oexnr.cn/nnews/387762.htm
- http://m.3g.oexnr.cn/nnews/3992.htm
- http://m.3g.oexnr.cn/nnews/88825.htm
- http://m.3g.oexnr.cn/nnews/3442076.htm
- http://m.3g.oexnr.cn/nnews/709002.htm
- http://m.3g.oexnr.cn/nnews/861042.htm
- http://m.3g.oexnr.cn/nnews/0407918.htm
- http://m.3g.oexnr.cn/nnews/46310.htm
- http://m.3g.oexnr.cn/nnews/927056.htm
- http://m.3g.oexnr.cn/nnews/307005.htm
- http://m.3g.oexnr.cn/nnews/0008096.htm
- http://m.3g.oexnr.cn/nnews/554219.htm
- http://m.3g.oexnr.cn/nnews/37857.htm
- http://m.3g.oexnr.cn/nnews/492825.htm
- http://m.3g.oexnr.cn/nnews/8071794.htm
- http://m.3g.oexnr.cn/nnews/1956592.htm
- http://m.3g.oexnr.cn/nnews/4894.htm
- http://m.3g.oexnr.cn/nnews/66761.htm
- http://m.3g.oexnr.cn/nnews/76496.htm
- http://m.3g.oexnr.cn/nnews/4004261.htm
- http://m.3g.oexnr.cn/nnews/300966.htm
- http://m.3g.oexnr.cn/nnews/8285296.htm
- http://m.3g.oexnr.cn/nnews/988220.htm
- http://m.3g.oexnr.cn/nnews/6981.htm
- http://m.3g.oexnr.cn/nnews/62583.htm
- http://m.3g.oexnr.cn/nnews/236805.htm
- http://m.3g.oexnr.cn/nnews/7419.htm
- http://m.3g.oexnr.cn/nnews/2065412.htm
- http://m.3g.oexnr.cn/nnews/15309.htm
- http://m.3g.oexnr.cn/nnews/1594340.htm
- http://m.3g.oexnr.cn/nnews/9172.htm
- http://m.3g.oexnr.cn/nnews/98027.htm
- http://m.3g.oexnr.cn/nnews/7843.htm
- http://m.3g.oexnr.cn/nnews/7719023.htm
- http://m.3g.oexnr.cn/nnews/15376.htm
- http://m.3g.oexnr.cn/nnews/89202.htm
- http://m.3g.oexnr.cn/nnews/4236.htm
- http://m.3g.oexnr.cn/nnews/6118.htm
- http://m.3g.oexnr.cn/nnews/9132185.htm
- http://m.3g.oexnr.cn/nnews/5953608.htm
- http://m.3g.oexnr.cn/nnews/2612889.htm
- http://m.3g.oexnr.cn/nnews/74547.htm
- http://m.3g.oexnr.cn/nnews/16006.htm
- http://m.3g.oexnr.cn/nnews/9136502.htm
- http://m.3g.oexnr.cn/nnews/1129672.htm
- http://m.3g.oexnr.cn/nnews/5072226.htm
- http://m.3g.oexnr.cn/nnews/4030331.htm
- http://m.3g.oexnr.cn/nnews/51742.htm
- http://m.3g.oexnr.cn/nnews/5515.htm
- http://m.3g.oexnr.cn/nnews/0138.htm
- http://m.3g.oexnr.cn/nnews/6786215.htm
- http://m.3g.oexnr.cn/nnews/5313.htm
- http://m.3g.oexnr.cn/nnews/466194.htm
- http://m.3g.oexnr.cn/nnews/808982.htm
- http://m.3g.oexnr.cn/nnews/0890.htm
- http://m.3g.oexnr.cn/nnews/7951599.htm
- http://m.3g.oexnr.cn/nnews/8386913.htm
- http://m.3g.oexnr.cn/nnews/702534.htm
- http://m.3g.oexnr.cn/nnews/490102.htm
- http://m.3g.oexnr.cn/nnews/531116.htm
- http://m.3g.oexnr.cn/nnews/4950550.htm
- http://m.3g.oexnr.cn/nnews/3808106.htm
- http://m.3g.oexnr.cn/nnews/804227.htm
- http://m.3g.oexnr.cn/nnews/3310.htm
- http://m.3g.oexnr.cn/nnews/1713059.htm
- http://m.3g.oexnr.cn/nnews/254365.htm
- http://m.3g.oexnr.cn/nnews/471091.htm
- http://m.3g.oexnr.cn/nnews/3836732.htm
- http://m.3g.oexnr.cn/nnews/072632.htm
- http://m.3g.oexnr.cn/nnews/61159.htm
- http://m.3g.oexnr.cn/nnews/49730.htm
- http://m.3g.oexnr.cn/nnews/490865.htm
- http://m.3g.oexnr.cn/nnews/7631.htm
- http://m.3g.oexnr.cn/nnews/6840483.htm
- http://m.3g.oexnr.cn/nnews/598732.htm
- http://m.3g.oexnr.cn/nnews/038182.htm
- http://m.3g.oexnr.cn/nnews/04091.htm
- http://m.3g.oexnr.cn/nnews/202519.htm
- http://m.3g.oexnr.cn/nnews/361470.htm
- http://m.3g.oexnr.cn/nnews/94161.htm
- http://m.3g.oexnr.cn/nnews/229098.htm
- http://m.3g.oexnr.cn/nnews/20441.htm
- http://m.3g.oexnr.cn/nnews/8867.htm
- http://m.3g.oexnr.cn/nnews/09012.htm
- http://m.3g.oexnr.cn/nnews/732518.htm
- http://m.3g.oexnr.cn/nnews/81338.htm
- http://m.3g.oexnr.cn/nnews/02880.htm
- http://m.3g.oexnr.cn/nnews/6533.htm
- http://m.3g.oexnr.cn/nnews/09474.htm
- http://m.3g.oexnr.cn/nnews/13482.htm
- http://m.3g.oexnr.cn/nnews/017546.htm
- http://m.3g.oexnr.cn/nnews/404604.htm
- http://m.3g.oexnr.cn/nnews/6842217.htm
- http://m.3g.oexnr.cn/nnews/05193.htm
- http://m.3g.oexnr.cn/nnews/403282.htm
- http://m.3g.oexnr.cn/nnews/142342.htm
- http://m.3g.oexnr.cn/nnews/9045105.htm
- http://m.3g.oexnr.cn/nnews/22006.htm
- http://m.3g.oexnr.cn/nnews/832642.htm
- http://m.3g.oexnr.cn/nnews/57767.htm
- http://m.3g.oexnr.cn/nnews/1546.htm
- http://m.3g.oexnr.cn/nnews/5453.htm
- http://m.3g.oexnr.cn/nnews/7055.htm
- http://m.3g.oexnr.cn/nnews/6902629.htm
- http://m.3g.oexnr.cn/nnews/8132370.htm
- http://m.3g.oexnr.cn/nnews/073054.htm
- http://m.3g.oexnr.cn/nnews/804103.htm
- http://m.3g.oexnr.cn/nnews/2510758.htm
- http://m.3g.oexnr.cn/nnews/387874.htm
- http://m.3g.oexnr.cn/nnews/90661.htm
- http://m.3g.oexnr.cn/nnews/59338.htm
- http://m.3g.oexnr.cn/nnews/134138.htm
- http://m.3g.oexnr.cn/nnews/1452264.htm
- http://m.3g.oexnr.cn/nnews/3069970.htm
- http://m.3g.oexnr.cn/nnews/3925525.htm

## 项目结构

```
newslink-hub/
├── app.py                         # 应用主入口，启动 Flask 后端服务
├── requirements.txt               # Python 依赖清单
├── config/
│   ├── __init__.py                # 配置模块初始化
│   ├── settings.py                # 环境变量与全局配置（含数据库路径、超时阈值）
│   └── batch_manifest.json        # 批次元数据配置文件（记录批次号、导入时间、链接总数）
├── data/
│   ├── batch_29_urls.txt          # 第29批次原始 URL 列表文件
│   ├── index.db                   # SQLite 索引数据库文件（含 links 表和 tags 表）
│   └── cache/                     # 页面元数据缓存目录（按 URL 哈希存储 JSON 摘要）
├── scripts/
│   ├── init_db.py                 # 初始化数据库表结构脚本
│   ├── import_batch.py            # 批量导入命令行工具（支持 --batch 和 --file 参数）
│   ├── check_links.py             # 链接有效性检测脚本（支持多线程并发检测）
│   └── export_index.py            # 索引导出脚本（支持 csv/json/markdown 格式）
├── src/
│   ├── __init__.py                # 源码模块初始化
│   ├── fetcher.py                 # 页面抓取与元数据提取核心逻辑（基于 requests 和 BeautifulSoup）
│   ├── deduplicator.py            # 基于路径指纹的重复检测算法实现
│   ├── scheduler.py               # 定时任务调度器（基于 cron 表达式）
│   └── formatter.py               # 导出数据格式化工具（CSV/JSON/Markdown 渲染器）
├── tests/
│   ├── test_fetcher.py            # 元数据提取单元测试（含模拟 HTTP 响应）
│   ├── test_deduplicator.py       # 去重算法测试用例
│   └── test_import.py             # 批量导入流程集成测试
├── docs/
│   ├── getting-started.md         # 入门指南文档
│   ├── import-guide.md            # 数据导入详细手册
│   ├── api-reference.md           # RESTful API 完整参考文档
│   └── operations.md              # 生产环境运维与调优指南
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

1.  **派生项目并创建特性分支**：在 GitHub 上派生本项目至个人账户，然后克隆派生后的仓库到本地，并基于主分支创建新的特性分支（如 `feature/add-batch-validator`）。所有开发工作请在特性分支上进行，避免直接提交至主分支。

2.  **编写或更新测试用例**：在 `tests/` 目录下为新增功能或修复的缺陷编写对应的单元测试或集成测试。确保测试覆盖率达到 80% 以上，所有测试用例在提交前必须全部通过。

3.  **提交代码并附上规范信息**：提交信息需遵循约定式提交格式（如 `feat: 添加批量链接状态导出接口` 或 `fix: 修复长 URL 解析时路径截断异常`）。提交前执行代码格式化工具（如 `black`）和静态检查工具（如 `pylint`）。

4.  **发起合并请求**：将特性分支推送至派生仓库后，向主仓库的主分支发起合并请求。在合并请求描述中详细说明变更目的、实现方案以及测试结果，并关联相关 Issue 编号。

5.  **文档同步更新**：若本次变更涉及用户可见的功能或配置项变更，须同步更新 `docs/` 目录下的对应文档，并确保 `README.md` 中的功能描述与最新实现保持一致。

## 常见问题

**问：导入链接时提示部分 URL 不可访问，是否影响整体导入流程？**

答：不影响。导入流程默认采用宽松模式，对于返回 4xx 或 5xx 状态码的链接，系统会将其状态标记为 "unreachable" 并继续处理后续条目。您可以在导入完成后运行 `scripts/check_links.py --retry` 对失败链接进行重试。如需严格模式（遇错即停止），可在配置文件中将 `STRICT_IMPORT` 参数设置为 `true`。

**问：如何将索引数据迁移至 MySQL 或 PostgreSQL 生产数据库？**

答：项目默认使用 SQLite 作为轻量级存储，便于快速启动和测试。若需迁移至生产级数据库，您可以在 `config/settings.py` 中修改 `DATABASE_URI` 配置项，将其指向 MySQL 或 PostgreSQL 的连接字符串（如 `mysql+pymysql://user:pass@host/db`）。项目依赖 SQLAlchemy ORM 框架，理论兼容主流关系型数据库，但建议在迁移前执行 `scripts/migrate_db.py` 进行 Schema 适配检查。

**问：定时检测任务的执行日志在哪里查看？**

答：所有定时任务（如链接有效性更新、元数据缓存刷新）的执行日志默认写入 `logs/scheduler.log` 文件。您可以通过在配置文件中调整 `LOG_LEVEL` 参数（可选值：DEBUG、INFO、WARNING、ERROR）来控制日志详细程度。若需将日志输出至标准输出流以便集成到容器日志系统，可将 `LOG_TO_STDOUT` 设置为 `true`。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
