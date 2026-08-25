# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的结构化外链资源聚合与导航系统。该项目针对当前网络中技术文章、新闻动态和行业报告分散、难以系统化追踪的问题，提供了一套基于分类索引和元数据标记的资源管理方案。项目通过将大量分散的 URL 资源进行统一入库、标签化处理和状态监控，帮助用户从信息过载中解脱出来，快速定位到特定主题或时间段的可用资料。

本项目定位于中大规模外链资源的自动化采集、归档和健康度检查，适用于需要定期跟踪特定网站内容更新的运维团队、进行互联网信息分析的研究机构以及搭建个性化知识库的开发者。项目本身不生产内容，而是提供一套工具链，将用户给定的原始链接转化为可查询、可筛选、可监控的结构化数据集。

## 功能概览

批量链接导入与解析 系统支持从纯文本列表、CSV 文件或数据库查询结果中批量导入 URL，自动解析协议、域名、路径和查询参数，并生成唯一的内容指纹。

资源状态实时监测 内置的调度器可按照用户设定的频率（每小时、每日或每周）对已入库的链接进行 HTTP 请求测试，记录响应状态码、内容长度和加载耗时，及时发现失效或异常链接。

多维度标签分类引擎 允许用户为每个链接添加自定义标签（如“技术博客”、“行业新闻”、“产品文档”），并支持基于标签的快速筛选和聚合统计。

全文元数据检索 对每个链接的页面标题、描述关键词和正文前 500 个字符进行提取和索引，支持高效的布尔查询和模糊匹配，帮助用户在海量链接中快速找到相关内容。

自定义视图与仪表盘 提供可配置的仪表盘组件，用户可以将常用筛选条件（如“近 7 天新增”、“响应超时”）保存为独立视图，实现个性化监控。

数据导入导出接口 提供 RESTful API 和命令行工具，支持将链接数据导出为 JSON、CSV 或 Markdown 表格格式，便于与其他数据分析工具集成。

扩展插件机制 预留钩子函数和事件监听接口，允许开发者编写自定义插件，例如在检测到链接状态变化时发送邮件通知或调用外部 Webhook。

## 应用场景

技术博客的日常监控与归档 技术团队可以使用 WebLink Navigator 将团队内部订阅的数十个外部技术博客链接统一管理，每日自动检查更新，当检测到页面内容发生变化时，系统会记录变更时间并生成摘要报告，帮助团队紧跟前沿技术动态。

行业报告与白皮书的追踪 研究机构可以将多个行业网站的报告发布页面链接导入系统，通过标签分类（如“人工智能”、“云计算”、“信息安全”）进行组织。当某个报告页面无法访问时，系统会立即发出预警，确保研究人员能够及时寻找替代来源或存档副本。

个人知识库的链接健康度检查 知识管理爱好者可以使用本工具对自己笔记软件或个人网站中引用的上千个外部链接进行定期巡检。系统生成的失效链接报告可以辅助用户快速修复或替换已失效的引用，保证知识库的长期可用性。

互联网信息采集任务的预处理 数据采集工程师可以将目标网站列表导入本系统，利用状态监测功能筛选出当前可稳定访问的链接，剔除频繁超时或重定向的地址，从而提高采集任务的成功率和执行效率。

## 快速开始

以下命令演示了如何在 Linux 或 macOS 环境下从源码安装并启动 WebLink Navigator 的核心服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装 Python 依赖包（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库并创建默认表结构
python scripts/init_db.py

# 启动调度器与 Web 仪表盘（默认监听 127.0.0.1:8080）
python app.py
```

启动成功后，打开浏览器访问 `http://127.0.0.1:8080` 即可进入仪表盘界面。首次启动时系统会自动创建示例数据，用户可通过界面中的“导入链接”功能将原始 URL 列表批量提交至系统。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行调度器、API 服务和命令行工具 |
| SQLite | 3.28 及以上 | 默认内置数据库，用于存储链接元数据、标签和状态历史 |
| requests | 2.25.0 及以上 | 用于发送 HTTP 请求以检测链接状态和抓取页面标题 |
| beautifulsoup4 | 4.9.0 及以上 | 用于解析 HTML 页面，提取元数据和正文预览片段 |
| Flask | 2.0.0 及以上 | 提供 Web 仪表盘和 RESTful API 服务 |
| APScheduler | 3.8.0 及以上 | 管理定时任务，实现周期性链接状态检测 |
| pytest | 6.0.0 及以上 | 可选依赖，用于运行单元测试和集成测试 |
| gunicorn | 20.1.0 及以上 | 可选依赖，用于生产环境下的 WSGI 服务部署 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide/ | 如何安装、配置、启动仪表盘；如何导入链接、创建标签和设置监控频率；如何导出数据和生成报告 |
| 开发指南 | docs/developer-guide/ | 如何理解项目代码结构；如何编写自定义插件；如何扩展新的元数据提取器；如何贡献代码 |
| API 参考 | docs/api-reference/ | 列出所有 RESTful 接口的请求方法、参数说明、返回格式和状态码；包含认证机制和速率限制说明 |
| 运维手册 | docs/operations/ | 如何将系统部署至生产环境；如何配置反向代理；如何迁移数据库；如何备份和恢复数据 |

## 资源列表

- http://m.blog.bwbkj.cn/snews/6691730.htm
- http://m.blog.bwbkj.cn/snews/9872742.htm
- http://m.blog.bwbkj.cn/snews/2922078.htm
- http://m.blog.bwbkj.cn/snews/12345.htm
- http://m.blog.bwbkj.cn/snews/6839259.htm
- http://m.blog.bwbkj.cn/snews/27663.htm
- http://m.blog.bwbkj.cn/snews/2462028.htm
- http://m.blog.bwbkj.cn/snews/65206.htm
- http://m.blog.bwbkj.cn/snews/2317206.htm
- http://m.blog.bwbkj.cn/snews/328251.htm
- http://m.blog.bwbkj.cn/snews/0474822.htm
- http://m.blog.bwbkj.cn/snews/6987.htm
- http://m.blog.bwbkj.cn/snews/2818438.htm
- http://m.blog.bwbkj.cn/snews/892860.htm
- http://m.blog.bwbkj.cn/snews/399690.htm
- http://m.blog.bwbkj.cn/snews/6269.htm
- http://m.blog.bwbkj.cn/snews/1547.htm
- http://m.blog.bwbkj.cn/snews/2429518.htm
- http://m.blog.bwbkj.cn/snews/1974317.htm
- http://m.blog.bwbkj.cn/snews/6740.htm
- http://m.blog.bwbkj.cn/snews/5996.htm
- http://m.blog.bwbkj.cn/snews/0325736.htm
- http://m.blog.bwbkj.cn/snews/04549.htm
- http://m.blog.bwbkj.cn/snews/9666196.htm
- http://m.blog.bwbkj.cn/snews/30943.htm
- http://m.blog.bwbkj.cn/snews/8491493.htm
- http://m.blog.bwbkj.cn/snews/4740330.htm
- http://m.blog.bwbkj.cn/snews/598090.htm
- http://m.blog.bwbkj.cn/snews/34587.htm
- http://m.blog.bwbkj.cn/snews/12602.htm
- http://m.blog.bwbkj.cn/snews/479045.htm
- http://m.blog.bwbkj.cn/snews/4082117.htm
- http://m.blog.bwbkj.cn/snews/157925.htm
- http://m.blog.bwbkj.cn/snews/6960.htm
- http://m.blog.bwbkj.cn/snews/05683.htm
- http://m.blog.bwbkj.cn/snews/13375.htm
- http://m.blog.bwbkj.cn/snews/8502354.htm
- http://m.blog.bwbkj.cn/snews/3745303.htm
- http://m.blog.bwbkj.cn/snews/6139139.htm
- http://m.blog.bwbkj.cn/snews/662867.htm
- http://m.blog.bwbkj.cn/snews/02769.htm
- http://m.blog.bwbkj.cn/snews/010575.htm
- http://m.blog.bwbkj.cn/snews/0207.htm
- http://m.blog.bwbkj.cn/snews/5307355.htm
- http://m.blog.bwbkj.cn/snews/3764.htm
- http://m.blog.bwbkj.cn/snews/5519.htm
- http://m.blog.bwbkj.cn/snews/714651.htm
- http://m.blog.bwbkj.cn/snews/87110.htm
- http://m.blog.bwbkj.cn/snews/9994376.htm
- http://m.blog.bwbkj.cn/snews/13315.htm
- http://m.blog.bwbkj.cn/snews/147407.htm
- http://m.blog.bwbkj.cn/snews/03880.htm
- http://m.blog.bwbkj.cn/snews/7740609.htm
- http://m.blog.bwbkj.cn/snews/287330.htm
- http://m.blog.bwbkj.cn/snews/008054.htm
- http://m.blog.bwbkj.cn/snews/45346.htm
- http://m.blog.bwbkj.cn/snews/3780.htm
- http://m.blog.bwbkj.cn/snews/7796.htm
- http://m.blog.bwbkj.cn/snews/08235.htm
- http://m.blog.bwbkj.cn/snews/3033280.htm
- http://m.blog.bwbkj.cn/snews/3637691.htm
- http://m.blog.bwbkj.cn/snews/21907.htm
- http://m.blog.bwbkj.cn/snews/900793.htm
- http://m.blog.bwbkj.cn/snews/974742.htm
- http://m.blog.bwbkj.cn/snews/1367.htm
- http://m.blog.bwbkj.cn/snews/0999.htm
- http://m.blog.bwbkj.cn/snews/9342.htm
- http://m.blog.bwbkj.cn/snews/6871919.htm
- http://m.blog.bwbkj.cn/snews/64975.htm
- http://m.blog.bwbkj.cn/snews/3462.htm
- http://m.blog.bwbkj.cn/snews/30442.htm
- http://m.blog.bwbkj.cn/snews/076155.htm
- http://m.blog.bwbkj.cn/snews/336185.htm
- http://m.blog.bwbkj.cn/snews/9885556.htm
- http://m.blog.bwbkj.cn/snews/510054.htm
- http://m.blog.bwbkj.cn/snews/0048715.htm
- http://m.blog.bwbkj.cn/snews/13743.htm
- http://m.blog.bwbkj.cn/snews/369435.htm
- http://m.blog.bwbkj.cn/snews/93184.htm
- http://m.blog.bwbkj.cn/snews/8540.htm
- http://m.blog.bwbkj.cn/snews/75050.htm
- http://m.blog.bwbkj.cn/snews/9916.htm
- http://m.blog.bwbkj.cn/snews/9525770.htm
- http://m.blog.bwbkj.cn/snews/1682400.htm
- http://m.blog.bwbkj.cn/snews/08605.htm
- http://m.blog.bwbkj.cn/snews/514842.htm
- http://m.blog.bwbkj.cn/snews/40033.htm
- http://m.blog.bwbkj.cn/snews/4042336.htm
- http://m.blog.bwbkj.cn/snews/648632.htm
- http://m.blog.bwbkj.cn/snews/8887.htm
- http://m.blog.bwbkj.cn/snews/699823.htm
- http://m.blog.bwbkj.cn/snews/40056.htm
- http://m.blog.bwbkj.cn/snews/88136.htm
- http://m.blog.bwbkj.cn/snews/85421.htm
- http://m.blog.bwbkj.cn/snews/7011.htm
- http://m.blog.bwbkj.cn/snews/4456.htm
- http://m.blog.bwbkj.cn/snews/589915.htm
- http://m.blog.bwbkj.cn/snews/552300.htm
- http://m.blog.bwbkj.cn/snews/211612.htm
- http://m.blog.bwbkj.cn/snews/25499.htm
- http://m.blog.bwbkj.cn/snews/760039.htm
- http://m.blog.bwbkj.cn/snews/0479522.htm
- http://m.blog.bwbkj.cn/snews/4287762.htm
- http://m.blog.bwbkj.cn/snews/5199972.htm
- http://m.blog.bwbkj.cn/snews/56945.htm
- http://m.blog.bwbkj.cn/snews/374657.htm
- http://m.blog.bwbkj.cn/snews/6379.htm
- http://m.blog.bwbkj.cn/snews/45593.htm
- http://m.blog.bwbkj.cn/snews/376274.htm
- http://m.blog.bwbkj.cn/snews/8828664.htm
- http://m.blog.bwbkj.cn/snews/707986.htm
- http://m.blog.bwbkj.cn/snews/8792790.htm
- http://m.blog.bwbkj.cn/snews/109575.htm
- http://m.blog.bwbkj.cn/snews/237701.htm
- http://m.blog.bwbkj.cn/snews/986090.htm
- http://m.blog.bwbkj.cn/snews/0236.htm
- http://m.blog.bwbkj.cn/snews/7231851.htm
- http://m.blog.bwbkj.cn/snews/654713.htm
- http://m.blog.bwbkj.cn/snews/879276.htm
- http://m.blog.bwbkj.cn/snews/2859.htm
- http://m.blog.bwbkj.cn/snews/57885.htm
- http://m.blog.bwbkj.cn/snews/77305.htm
- http://m.blog.bwbkj.cn/snews/2871207.htm
- http://m.blog.bwbkj.cn/snews/1429.htm
- http://m.blog.bwbkj.cn/snews/240716.htm
- http://m.blog.bwbkj.cn/snews/244687.htm
- http://m.blog.bwbkj.cn/snews/383541.htm
- http://m.blog.bwbkj.cn/snews/540374.htm
- http://m.blog.bwbkj.cn/snews/84693.htm
- http://m.blog.bwbkj.cn/snews/089141.htm
- http://m.blog.bwbkj.cn/snews/67483.htm
- http://m.blog.bwbkj.cn/snews/2301.htm
- http://m.blog.bwbkj.cn/snews/5250121.htm
- http://m.blog.bwbkj.cn/snews/14943.htm
- http://m.blog.bwbkj.cn/snews/627493.htm
- http://m.blog.bwbkj.cn/snews/462240.htm
- http://m.blog.bwbkj.cn/snews/6687742.htm
- http://m.blog.bwbkj.cn/snews/658824.htm
- http://m.blog.bwbkj.cn/snews/2915520.htm
- http://m.blog.bwbkj.cn/snews/177051.htm
- http://m.blog.bwbkj.cn/snews/200987.htm
- http://m.blog.bwbkj.cn/snews/9376.htm
- http://m.blog.bwbkj.cn/snews/9749586.htm
- http://m.blog.bwbkj.cn/snews/3080825.htm
- http://m.blog.bwbkj.cn/snews/512077.htm
- http://m.blog.bwbkj.cn/snews/8878.htm
- http://m.blog.bwbkj.cn/snews/9736.htm
- http://m.blog.bwbkj.cn/snews/14073.htm
- http://m.blog.bwbkj.cn/snews/376020.htm
- http://m.blog.bwbkj.cn/snews/88616.htm
- http://m.blog.bwbkj.cn/snews/4816.htm
- http://m.blog.bwbkj.cn/snews/9348593.htm
- http://m.blog.bwbkj.cn/snews/5673857.htm
- http://m.blog.bwbkj.cn/snews/24678.htm
- http://m.blog.bwbkj.cn/snews/833569.htm
- http://m.blog.bwbkj.cn/snews/6969481.htm
- http://m.blog.bwbkj.cn/snews/3130369.htm
- http://m.blog.bwbkj.cn/snews/309655.htm
- http://m.blog.bwbkj.cn/snews/91342.htm
- http://m.blog.bwbkj.cn/snews/398428.htm
- http://m.blog.bwbkj.cn/snews/22045.htm
- http://m.blog.bwbkj.cn/snews/0118.htm
- http://m.blog.bwbkj.cn/snews/1166022.htm
- http://m.blog.bwbkj.cn/snews/29523.htm
- http://m.blog.bwbkj.cn/snews/98357.htm
- http://m.blog.bwbkj.cn/snews/566412.htm
- http://m.blog.bwbkj.cn/snews/54877.htm
- http://m.blog.bwbkj.cn/snews/52651.htm
- http://m.blog.bwbkj.cn/snews/7887.htm
- http://m.blog.bwbkj.cn/snews/0588720.htm
- http://m.blog.bwbkj.cn/snews/2774.htm
- http://m.blog.bwbkj.cn/snews/1933.htm
- http://m.blog.bwbkj.cn/snews/9646789.htm
- http://m.blog.bwbkj.cn/snews/77914.htm
- http://m.blog.bwbkj.cn/snews/8892057.htm
- http://m.blog.bwbkj.cn/snews/8341371.htm
- http://m.blog.bwbkj.cn/snews/089973.htm
- http://m.blog.bwbkj.cn/snews/961071.htm
- http://m.blog.bwbkj.cn/snews/2753407.htm
- http://m.blog.bwbkj.cn/snews/6698486.htm
- http://m.blog.bwbkj.cn/snews/1286502.htm
- http://m.blog.bwbkj.cn/snews/1016.htm
- http://m.blog.bwbkj.cn/snews/959391.htm
- http://m.blog.bwbkj.cn/snews/7249717.htm
- http://m.blog.bwbkj.cn/snews/1632718.htm
- http://m.blog.bwbkj.cn/snews/64123.htm
- http://m.blog.bwbkj.cn/snews/359636.htm
- http://m.blog.bwbkj.cn/snews/9710.htm
- http://m.blog.bwbkj.cn/snews/7875.htm
- http://m.blog.bwbkj.cn/snews/4098.htm
- http://m.blog.bwbkj.cn/snews/720314.htm
- http://m.blog.bwbkj.cn/snews/14247.htm
- http://m.blog.bwbkj.cn/snews/0628.htm
- http://m.blog.bwbkj.cn/snews/2009.htm
- http://m.blog.bwbkj.cn/snews/959211.htm
- http://m.blog.bwbkj.cn/snews/8796825.htm
- http://m.blog.bwbkj.cn/snews/1273.htm
- http://m.blog.bwbkj.cn/snews/202587.htm
- http://m.blog.bwbkj.cn/snews/7640485.htm
- http://m.blog.bwbkj.cn/snews/476357.htm
- http://m.blog.bwbkj.cn/snews/9801500.htm
- http://m.blog.bwbkj.cn/snews/3915766.htm
- http://m.blog.bwbkj.cn/snews/9024802.htm
- http://m.blog.bwbkj.cn/snews/5215.htm
- http://m.blog.bwbkj.cn/snews/789002.htm
- http://m.blog.bwbkj.cn/snews/595223.htm
- http://m.blog.bwbkj.cn/snews/2551417.htm
- http://m.blog.bwbkj.cn/snews/77009.htm
- http://m.blog.bwbkj.cn/snews/5743534.htm
- http://m.blog.bwbkj.cn/snews/7772.htm
- http://m.blog.bwbkj.cn/snews/97090.htm
- http://m.blog.bwbkj.cn/snews/270258.htm
- http://m.blog.bwbkj.cn/snews/25669.htm
- http://m.blog.bwbkj.cn/snews/1246.htm
- http://m.blog.bwbkj.cn/snews/827575.htm
- http://m.blog.bwbkj.cn/snews/39222.htm
- http://m.blog.bwbkj.cn/snews/6766008.htm
- http://m.blog.bwbkj.cn/snews/76071.htm
- http://m.blog.bwbkj.cn/snews/3560.htm
- http://m.blog.bwbkj.cn/snews/03193.htm
- http://m.blog.bwbkj.cn/snews/577445.htm
- http://m.blog.bwbkj.cn/snews/1822.htm
- http://m.blog.bwbkj.cn/snews/22354.htm
- http://m.blog.bwbkj.cn/snews/7545.htm
- http://m.blog.bwbkj.cn/snews/46127.htm
- http://m.blog.bwbkj.cn/snews/220563.htm
- http://m.blog.bwbkj.cn/snews/892066.htm
- http://m.blog.bwbkj.cn/snews/4487144.htm
- http://m.blog.bwbkj.cn/snews/68451.htm
- http://m.blog.bwbkj.cn/snews/64032.htm
- http://m.blog.bwbkj.cn/snews/9638.htm
- http://m.blog.bwbkj.cn/snews/56865.htm
- http://m.blog.bwbkj.cn/snews/246897.htm
- http://m.blog.bwbkj.cn/snews/7384720.htm
- http://m.blog.bwbkj.cn/snews/468724.htm
- http://m.blog.bwbkj.cn/snews/120313.htm
- http://m.blog.bwbkj.cn/snews/686117.htm
- http://m.blog.bwbkj.cn/snews/17717.htm
- http://m.blog.bwbkj.cn/snews/38133.htm
- http://m.blog.bwbkj.cn/snews/21216.htm
- http://m.blog.bwbkj.cn/snews/493408.htm
- http://m.blog.bwbkj.cn/snews/3182.htm
- http://m.blog.bwbkj.cn/snews/4777333.htm
- http://m.blog.bwbkj.cn/snews/375966.htm
- http://m.blog.bwbkj.cn/snews/4780916.htm
- http://m.blog.bwbkj.cn/snews/9710202.htm
- http://m.blog.bwbkj.cn/snews/390100.htm
- http://m.blog.bwbkj.cn/snews/8232.htm
- http://m.blog.bwbkj.cn/snews/303336.htm
- http://m.blog.bwbkj.cn/snews/763258.htm
- http://m.blog.bwbkj.cn/snews/4572.htm
- http://m.blog.bwbkj.cn/snews/5275104.htm
- http://m.blog.bwbkj.cn/snews/90687.htm
- http://m.blog.bwbkj.cn/snews/733859.htm
- http://m.blog.bwbkj.cn/snews/6022499.htm
- http://m.blog.bwbkj.cn/snews/7613.htm
- http://m.blog.bwbkj.cn/snews/89280.htm
- http://m.blog.bwbkj.cn/snews/81140.htm
- http://m.blog.bwbkj.cn/snews/6206.htm
- http://m.blog.bwbkj.cn/snews/0027098.htm
- http://m.blog.bwbkj.cn/snews/881593.htm
- http://m.blog.bwbkj.cn/snews/8159.htm
- http://m.blog.bwbkj.cn/snews/423211.htm
- http://m.blog.bwbkj.cn/snews/5482.htm
- http://m.blog.bwbkj.cn/snews/332117.htm
- http://m.blog.bwbkj.cn/snews/63788.htm
- http://m.blog.bwbkj.cn/snews/44464.htm
- http://m.blog.bwbkj.cn/snews/9416540.htm
- http://m.blog.bwbkj.cn/snews/3043834.htm
- http://m.blog.bwbkj.cn/snews/900471.htm
- http://m.blog.bwbkj.cn/snews/63987.htm
- http://m.blog.bwbkj.cn/snews/6630.htm
- http://m.blog.bwbkj.cn/snews/49938.htm
- http://m.blog.bwbkj.cn/snews/034672.htm
- http://m.blog.bwbkj.cn/snews/181490.htm
- http://m.blog.bwbkj.cn/snews/41090.htm
- http://m.blog.bwbkj.cn/snews/7269.htm
- http://m.blog.bwbkj.cn/snews/2692.htm
- http://m.blog.bwbkj.cn/snews/982174.htm
- http://m.blog.bwbkj.cn/snews/6609.htm
- http://m.blog.bwbkj.cn/snews/240899.htm
- http://m.blog.bwbkj.cn/snews/4121924.htm
- http://m.blog.bwbkj.cn/snews/0611.htm
- http://m.blog.bwbkj.cn/snews/35428.htm
- http://m.blog.bwbkj.cn/snews/2836746.htm
- http://m.blog.bwbkj.cn/snews/3666.htm
- http://m.blog.bwbkj.cn/snews/5893.htm
- http://m.blog.bwbkj.cn/snews/3538.htm
- http://m.blog.bwbkj.cn/snews/732816.htm
- http://m.blog.bwbkj.cn/snews/2922.htm
- http://m.blog.bwbkj.cn/snews/9445.htm
- http://m.blog.bwbkj.cn/snews/47629.htm
- http://m.blog.bwbkj.cn/snews/5578701.htm
- http://m.blog.bwbkj.cn/snews/15654.htm
- http://m.blog.bwbkj.cn/snews/7152367.htm
- http://m.blog.bwbkj.cn/snews/9351036.htm
- http://m.blog.bwbkj.cn/snews/47712.htm
- http://m.blog.bwbkj.cn/snews/56916.htm
- http://m.blog.bwbkj.cn/snews/4608885.htm
- http://m.blog.bwbkj.cn/snews/53552.htm

## 项目结构

```
weblink-navigator/
├── app/                             # 主应用模块
│   ├── __init__.py                  # 应用工厂函数与配置初始化
│   ├── routes.py                    # 定义 Web 仪表盘和 API 的路由与视图函数
│   └── models.py                    # 定义 Link, Tag, StatusRecord 等 ORM 模型
├── core/                            # 核心业务逻辑层
│   ├── fetcher.py                   # 封装 requests 请求逻辑，处理重定向和超时
│   ├── parser.py                    # 使用 BeautifulSoup 提取页面标题和元数据
│   ├── scheduler.py                 # 基于 APScheduler 的定时任务调度器
│   └── monitor.py                   # 执行批量链接状态检测并记录结果
├── scripts/                         # 运维和辅助脚本
│   ├── init_db.py                   # 创建 SQLite 数据库表和默认配置
│   ├── import_links.py              # 从外部文件批量导入 URL 列表
│   └── export_report.py             # 将状态记录导出为 CSV 或 JSON 格式
├── tests/                           # 单元测试与集成测试目录
│   ├── test_fetcher.py              # 测试 HTTP 请求模块的各类边界条件
│   ├── test_parser.py               # 测试 HTML 解析和元数据提取的正确性
│   └── test_scheduler.py            # 测试定时任务的创建、执行和销毁流程
├── static/                          # Web 静态资源
│   ├── css/                         # 仪表盘样式表 (基于 Bootstrap 定制)
│   └── js/                          # 前端交互脚本 (AJAX 请求与动态表格渲染)
├── templates/                       # Jinja2 模板文件
│   ├── dashboard.html               # 主仪表盘页面
│   ├── links.html                   # 链接列表与筛选界面
│   └── detail.html                  # 单个链接的状态历史详情页
├── docs/                            # 完整项目文档
│   ├── user-guide/                  # 用户手册分章节
│   ├── developer-guide/             # 开发指南与插件编写教程
│   └── api-reference/               # 接口文档由 Sphinx 自动生成
├── requirements.txt                 # 生产环境依赖清单
├── requirements-dev.txt             # 开发环境额外依赖 (pytest, flake8, mypy)
├── app.py                           # 应用入口，用于开发环境启动
├── wsgi.py                          # 生产环境 WSGI 网关入口
└── README.md                        # 项目概览与快速入门说明
```

## 贡献指南

提交问题报告或功能请求 请在 GitHub Issues 页面搜索现有议题，避免重复。新建议题时请使用提供的模板，清晰描述复现步骤、预期行为和实际结果，并附上相关的日志片段或截图。

本地开发环境搭建 克隆仓库后，请先安装开发依赖 (`pip install -r requirements-dev.txt`)，并运行 `pre-commit install` 启用代码风格检查工具（black 和 flake8）。所有新代码必须通过现有的单元测试，并为新增功能编写对应的测试用例。

提交代码变更 请从 `main` 分支创建新的特性分支，命名格式为 `feature/简短描述` 或 `fix/问题编号`。提交信息应遵循约定式提交规范，以 `type(scope): subject` 格式书写，例如 `feat(parser): add support for Open Graph meta tags`。

发起拉取请求 在完成本地测试并确保所有检查通过后，将分支推送至远程仓库并发起 Pull Request。PR 描述中应关联相关议题，并详细说明变更内容、测试覆盖情况以及可能的影响范围。至少需要一名项目维护者审核通过后方可合并。

文档与示例更新 任何影响用户使用方式的功能变更都必须同步更新对应的用户手册或 API 文档。新增配置项或命令行参数时，请同时在示例配置文件和快速入门指南中添加说明。

## 常见问题

系统对单个链接的状态检测频率是否有上限？
系统默认每个链接至少间隔 1 小时才会再次发起 HTTP 请求，以避免对目标服务器造成不必要的压力。用户可以通过配置文件中的 `CHECK_INTERVAL_MINUTES` 参数调整此间隔，但建议不要低于 15 分钟。对于需要更高实时性的场景，可以单独在仪表盘中手动触发检测。

如何处理目标页面需要登录或验证码的情况？
当前版本的链接检测仅针对页面基础可达性（HTTP 状态码）和基本元数据提取，不支持交互式登录或验证码识别。对于此类页面，系统会记录其响应状态，但不会尝试获取完整页面内容。用户可以通过标签功能将这类链接归类为“需登录”，并在筛选时忽略其内容变更状态。

数据库文件会占用多少存储空间，如何维护？
SQLite 数据库的大小主要取决于链接数量和每次检测记录的历史条目数。以 300 个链接为例，若每天检测一次并保留 30 天记录，数据库文件大小约为 5-8 MB。用户可以通过执行 `scripts/cleanup_history.py --keep-days 30` 命令定期清理过期历史记录，以控制存储空间。生产环境建议启用 WAL 模式以提升并发读写性能。

## 许可证

MIT License

Copyright (c) 2026 WebLink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:12
