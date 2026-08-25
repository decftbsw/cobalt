# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端新闻资讯索引的轻量级外链资源汇总平台，专注于对分散在互联网各处的深度报道、行业分析及即时新闻进行结构化收录与分类导航。项目定位为技术资讯聚合中间件，服务于内容聚合开发者、舆情分析人员以及需要批量获取新闻源链接的研究者。

项目本身不存储任何新闻正文或用户数据，仅提供 URL 索引与元信息标记能力，配合定时抓取脚本可构建完整的新闻流处理管道。当前批次为第 225/300 批资源收录，共计 300 个条目，已完成基础校验与分类标记。

## 功能概览

**批量链接导入** 支持从 CSV、JSON 及纯文本列表批量导入 URL 资源，自动去重并生成内部唯一标识。

**分类标签管理** 允许为每个链接添加多级分类标签，支持自定义标签体系，便于按主题、地域或时间维度筛选。

**链接健康检查** 内置异步 HTTP 探活机制，可周期性检测链接可用性并标记失效或重定向状态。

**元数据智能补全** 通过请求头分析与页面 Title 提取，自动补全资源标题、描述及内容类型，减少人工录入成本。

**RESTful API 输出** 提供标准 JSON API 接口，支持分页、排序及条件过滤，方便第三方系统集成调用。

**导出与备份** 支持将索引数据导出为 Markdown 表格、JSON 数组或纯文本列表格式，便于迁移或离线分析。

**访问统计看板** 记录每个链接的点击频次与最近访问时间，辅助评估资源热度与长期价值。

## 应用场景

内容聚合系统数据源管理：内容采集系统可通过本平台维护稳定的新闻源列表，定时拉取链接并分发给爬虫节点，避免爬虫配置散落在各配置文件中的维护难题。

舆情监测初始种子构建：舆情分析团队可使用本项目的批量导入功能快速建立初始监测链接库，配合健康检查自动剔除失效源，保障监测覆盖面的持续性。

研究机构新闻趋势分析：高校或研究机构在进行媒体传播趋势研究时，可利用本平台提供的结构化链接索引，按时间批次采样新闻样本，减少人工检索成本。

个人开发者快速原型搭建：独立开发者可通过 API 接口获取现成的新闻链接数据集，用于测试推荐算法或信息流排序逻辑，无需从零收集测试数据。

## 快速开始

以下命令演示如何在本地环境中克隆并启动 JNews Link Aggregator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/jnews-link-aggregator.git

# 进入项目目录
cd jnews-link-aggregator

# 安装依赖（基于 Python 3.10 + pip）
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python scripts/init_db.py

# 导入当前批次资源列表（资源文件位于 data/batch_225_300.txt）
python scripts/import_links.py --source data/batch_225_300.txt --batch 225

# 启动开发服务器（默认监听 127.0.0.1:8000）
python app.py
```

访问 http://127.0.0.1:8000/api/links 可查看已导入的链接列表 JSON 响应。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 或更高 | 核心运行环境，低于 3.10 将不支持某些类型注解特性 |
| SQLite | 3.35 或更高 | 默认嵌入式数据库，用于存储链接索引与元数据 |
| requests | 2.28.0 或更高 | 用于发起 HTTP 请求进行健康检查与元数据补全 |
| beautifulsoup4 | 4.11.0 或更高 | HTML 解析依赖，用于提取页面标题与描述 |
| flask | 2.2.0 或更高 | Web API 服务框架，提供 RESTful 接口 |
| pytest | 7.0.0 或更高 | 单元测试框架，仅在开发环境中需要 |
| gunicorn | 20.1.0 或更高 | 生产环境 WSGI 服务器，非开发环境必需 |
| python-dotenv | 0.21.0 或更高 | 环境变量管理，用于区分开发与生产配置 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/quickstart.md | 如何快速部署并导入第一批链接？API 服务默认端口是多少？ |
| API 参考 | docs/api_reference.md | 各接口的请求参数、响应结构与错误码如何定义？如何过滤特定分类的链接？ |
| 运维手册 | docs/operations.md | 如何配置定时健康检查任务？如何迁移数据库到 PostgreSQL？如何备份索引数据？ |
| 贡献规范 | docs/contributing.md | 提交代码的流程是什么？测试覆盖率要求多少？Commit Message 格式有何规定？ |
| 设计文档 | docs/design.md | 系统整体架构如何设计？数据库表关系是怎样的？分类标签体系如何扩展？ |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/51178.htm
- http://m.3g.bwbkj.cn/jnews/357923.htm
- http://m.3g.bwbkj.cn/jnews/738497.htm
- http://m.3g.bwbkj.cn/jnews/1206.htm
- http://m.3g.bwbkj.cn/jnews/12122.htm
- http://m.3g.bwbkj.cn/jnews/6155.htm
- http://m.3g.bwbkj.cn/jnews/5852.htm
- http://m.3g.bwbkj.cn/jnews/571009.htm
- http://m.3g.bwbkj.cn/jnews/4893196.htm
- http://m.3g.bwbkj.cn/jnews/438740.htm
- http://m.3g.bwbkj.cn/jnews/43217.htm
- http://m.3g.bwbkj.cn/jnews/28723.htm
- http://m.3g.bwbkj.cn/jnews/81290.htm
- http://m.3g.bwbkj.cn/jnews/07507.htm
- http://m.3g.bwbkj.cn/jnews/639283.htm
- http://m.3g.bwbkj.cn/jnews/575569.htm
- http://m.3g.bwbkj.cn/jnews/3581006.htm
- http://m.3g.bwbkj.cn/jnews/5666.htm
- http://m.3g.bwbkj.cn/jnews/619340.htm
- http://m.3g.bwbkj.cn/jnews/88782.htm
- http://m.3g.bwbkj.cn/jnews/454458.htm
- http://m.3g.bwbkj.cn/jnews/622414.htm
- http://m.3g.bwbkj.cn/jnews/90843.htm
- http://m.3g.bwbkj.cn/jnews/230030.htm
- http://m.3g.bwbkj.cn/jnews/3620748.htm
- http://m.3g.bwbkj.cn/jnews/63548.htm
- http://m.3g.bwbkj.cn/jnews/6401264.htm
- http://m.3g.bwbkj.cn/jnews/2838.htm
- http://m.3g.bwbkj.cn/jnews/0891.htm
- http://m.3g.bwbkj.cn/jnews/0658646.htm
- http://m.3g.bwbkj.cn/jnews/8873737.htm
- http://m.3g.bwbkj.cn/jnews/9057649.htm
- http://m.3g.bwbkj.cn/jnews/642392.htm
- http://m.3g.bwbkj.cn/jnews/7346.htm
- http://m.3g.bwbkj.cn/jnews/24850.htm
- http://m.3g.bwbkj.cn/jnews/58576.htm
- http://m.3g.bwbkj.cn/jnews/020321.htm
- http://m.3g.bwbkj.cn/jnews/7831.htm
- http://m.3g.bwbkj.cn/jnews/285762.htm
- http://m.3g.bwbkj.cn/jnews/5244515.htm
- http://m.3g.bwbkj.cn/jnews/96614.htm
- http://m.3g.bwbkj.cn/jnews/00244.htm
- http://m.3g.bwbkj.cn/jnews/3303617.htm
- http://m.3g.bwbkj.cn/jnews/8973052.htm
- http://m.3g.bwbkj.cn/jnews/897908.htm
- http://m.3g.bwbkj.cn/jnews/1777977.htm
- http://m.3g.bwbkj.cn/jnews/526189.htm
- http://m.3g.bwbkj.cn/jnews/530846.htm
- http://m.3g.bwbkj.cn/jnews/2272614.htm
- http://m.3g.bwbkj.cn/jnews/36914.htm
- http://m.3g.bwbkj.cn/jnews/0058.htm
- http://m.3g.bwbkj.cn/jnews/7636627.htm
- http://m.3g.bwbkj.cn/jnews/55667.htm
- http://m.3g.bwbkj.cn/jnews/9423235.htm
- http://m.3g.bwbkj.cn/jnews/983081.htm
- http://m.3g.bwbkj.cn/jnews/89780.htm
- http://m.3g.bwbkj.cn/jnews/8752.htm
- http://m.3g.bwbkj.cn/jnews/081379.htm
- http://m.3g.bwbkj.cn/jnews/570937.htm
- http://m.3g.bwbkj.cn/jnews/03983.htm
- http://m.3g.bwbkj.cn/jnews/0954.htm
- http://m.3g.bwbkj.cn/jnews/4241.htm
- http://m.3g.bwbkj.cn/jnews/8504.htm
- http://m.3g.bwbkj.cn/jnews/11048.htm
- http://m.3g.bwbkj.cn/jnews/7404.htm
- http://m.3g.bwbkj.cn/jnews/343274.htm
- http://m.3g.bwbkj.cn/jnews/9550.htm
- http://m.3g.bwbkj.cn/jnews/64574.htm
- http://m.3g.bwbkj.cn/jnews/8771.htm
- http://m.3g.bwbkj.cn/jnews/0124.htm
- http://m.3g.bwbkj.cn/jnews/48701.htm
- http://m.3g.bwbkj.cn/jnews/20113.htm
- http://m.3g.bwbkj.cn/jnews/8912958.htm
- http://m.3g.bwbkj.cn/jnews/9026.htm
- http://m.3g.bwbkj.cn/jnews/070461.htm
- http://m.3g.bwbkj.cn/jnews/566006.htm
- http://m.3g.bwbkj.cn/jnews/546756.htm
- http://m.3g.bwbkj.cn/jnews/398681.htm
- http://m.3g.bwbkj.cn/jnews/221580.htm
- http://m.3g.bwbkj.cn/jnews/69366.htm
- http://m.3g.bwbkj.cn/jnews/1862.htm
- http://m.3g.bwbkj.cn/jnews/09866.htm
- http://m.3g.bwbkj.cn/jnews/2920.htm
- http://m.3g.bwbkj.cn/jnews/17877.htm
- http://m.3g.bwbkj.cn/jnews/1460.htm
- http://m.3g.bwbkj.cn/jnews/738774.htm
- http://m.3g.bwbkj.cn/jnews/4189.htm
- http://m.3g.bwbkj.cn/jnews/311600.htm
- http://m.3g.bwbkj.cn/jnews/8384.htm
- http://m.3g.bwbkj.cn/jnews/521629.htm
- http://m.3g.bwbkj.cn/jnews/95768.htm
- http://m.3g.bwbkj.cn/jnews/1894.htm
- http://m.3g.bwbkj.cn/jnews/9842259.htm
- http://m.3g.bwbkj.cn/jnews/8054050.htm
- http://m.3g.bwbkj.cn/jnews/3477.htm
- http://m.3g.bwbkj.cn/jnews/900541.htm
- http://m.3g.bwbkj.cn/jnews/4209.htm
- http://m.3g.bwbkj.cn/jnews/5732.htm
- http://m.3g.bwbkj.cn/jnews/8444451.htm
- http://m.3g.bwbkj.cn/jnews/88113.htm
- http://m.3g.bwbkj.cn/jnews/8610729.htm
- http://m.3g.bwbkj.cn/jnews/2500.htm
- http://m.3g.bwbkj.cn/jnews/4543089.htm
- http://m.3g.bwbkj.cn/jnews/8670.htm
- http://m.3g.bwbkj.cn/jnews/9866799.htm
- http://m.3g.bwbkj.cn/jnews/930191.htm
- http://m.3g.bwbkj.cn/jnews/091442.htm
- http://m.3g.bwbkj.cn/jnews/9898.htm
- http://m.3g.bwbkj.cn/jnews/5300661.htm
- http://m.3g.bwbkj.cn/jnews/266101.htm
- http://m.3g.bwbkj.cn/jnews/1102412.htm
- http://m.3g.bwbkj.cn/jnews/67832.htm
- http://m.3g.bwbkj.cn/jnews/2494452.htm
- http://m.3g.bwbkj.cn/jnews/53405.htm
- http://m.3g.bwbkj.cn/jnews/329941.htm
- http://m.3g.bwbkj.cn/jnews/23667.htm
- http://m.3g.bwbkj.cn/jnews/8366.htm
- http://m.3g.bwbkj.cn/jnews/7988.htm
- http://m.3g.bwbkj.cn/jnews/59881.htm
- http://m.3g.bwbkj.cn/jnews/4993.htm
- http://m.3g.bwbkj.cn/jnews/31390.htm
- http://m.3g.bwbkj.cn/jnews/77937.htm
- http://m.3g.bwbkj.cn/jnews/1204720.htm
- http://m.3g.bwbkj.cn/jnews/596820.htm
- http://m.3g.bwbkj.cn/jnews/6917497.htm
- http://m.3g.bwbkj.cn/jnews/8240.htm
- http://m.3g.bwbkj.cn/jnews/01686.htm
- http://m.3g.bwbkj.cn/jnews/674910.htm
- http://m.3g.bwbkj.cn/jnews/4910.htm
- http://m.3g.bwbkj.cn/jnews/20013.htm
- http://m.3g.bwbkj.cn/jnews/8394.htm
- http://m.3g.bwbkj.cn/jnews/7105940.htm
- http://m.3g.bwbkj.cn/jnews/076780.htm
- http://m.3g.bwbkj.cn/jnews/217767.htm
- http://m.3g.bwbkj.cn/jnews/2655815.htm
- http://m.3g.bwbkj.cn/jnews/3095911.htm
- http://m.3g.bwbkj.cn/jnews/2777878.htm
- http://m.3g.bwbkj.cn/jnews/4324.htm
- http://m.3g.bwbkj.cn/jnews/8157.htm
- http://m.3g.bwbkj.cn/jnews/8897136.htm
- http://m.3g.bwbkj.cn/jnews/1423104.htm
- http://m.3g.bwbkj.cn/jnews/3140255.htm
- http://m.3g.bwbkj.cn/jnews/5711.htm
- http://m.3g.bwbkj.cn/jnews/2963648.htm
- http://m.3g.bwbkj.cn/jnews/4313949.htm
- http://m.3g.bwbkj.cn/jnews/01782.htm
- http://m.3g.bwbkj.cn/jnews/4879.htm
- http://m.3g.bwbkj.cn/jnews/643425.htm
- http://m.3g.bwbkj.cn/jnews/10380.htm
- http://m.3g.bwbkj.cn/jnews/0546.htm
- http://m.3g.bwbkj.cn/jnews/39150.htm
- http://m.3g.bwbkj.cn/jnews/5439314.htm
- http://m.3g.bwbkj.cn/jnews/3273.htm
- http://m.3g.bwbkj.cn/jnews/3766659.htm
- http://m.3g.bwbkj.cn/jnews/7537.htm
- http://m.3g.bwbkj.cn/jnews/644684.htm
- http://m.3g.bwbkj.cn/jnews/40751.htm
- http://m.3g.bwbkj.cn/jnews/3153.htm
- http://m.3g.bwbkj.cn/jnews/6518442.htm
- http://m.3g.bwbkj.cn/jnews/009382.htm
- http://m.3g.bwbkj.cn/jnews/81669.htm
- http://m.3g.bwbkj.cn/jnews/44429.htm
- http://m.3g.bwbkj.cn/jnews/870705.htm
- http://m.3g.bwbkj.cn/jnews/576659.htm
- http://m.3g.bwbkj.cn/jnews/8380139.htm
- http://m.3g.bwbkj.cn/jnews/709850.htm
- http://m.3g.bwbkj.cn/jnews/91426.htm
- http://m.3g.bwbkj.cn/jnews/6584923.htm
- http://m.3g.bwbkj.cn/jnews/836229.htm
- http://m.3g.bwbkj.cn/jnews/45324.htm
- http://m.3g.bwbkj.cn/jnews/158027.htm
- http://m.3g.bwbkj.cn/jnews/6040.htm
- http://m.3g.bwbkj.cn/jnews/3590.htm
- http://m.3g.bwbkj.cn/jnews/3910.htm
- http://m.3g.bwbkj.cn/jnews/2006.htm
- http://m.3g.bwbkj.cn/jnews/13321.htm
- http://m.3g.bwbkj.cn/jnews/62887.htm
- http://m.3g.bwbkj.cn/jnews/9476123.htm
- http://m.3g.bwbkj.cn/jnews/76528.htm
- http://m.3g.bwbkj.cn/jnews/3054.htm
- http://m.3g.bwbkj.cn/jnews/9383.htm
- http://m.3g.bwbkj.cn/jnews/02416.htm
- http://m.3g.bwbkj.cn/jnews/6510659.htm
- http://m.3g.bwbkj.cn/jnews/00782.htm
- http://m.3g.bwbkj.cn/jnews/852452.htm
- http://m.3g.bwbkj.cn/jnews/767686.htm
- http://m.3g.bwbkj.cn/jnews/1612097.htm
- http://m.3g.bwbkj.cn/jnews/95269.htm
- http://m.3g.bwbkj.cn/jnews/2778.htm
- http://m.3g.bwbkj.cn/jnews/2589806.htm
- http://m.3g.bwbkj.cn/jnews/7275063.htm
- http://m.3g.bwbkj.cn/jnews/6687257.htm
- http://m.3g.bwbkj.cn/jnews/43306.htm
- http://m.3g.bwbkj.cn/jnews/2064506.htm
- http://m.3g.bwbkj.cn/jnews/7885.htm
- http://m.3g.bwbkj.cn/jnews/48812.htm
- http://m.3g.bwbkj.cn/jnews/57172.htm
- http://m.3g.bwbkj.cn/jnews/4247024.htm
- http://m.3g.bwbkj.cn/jnews/589265.htm
- http://m.3g.bwbkj.cn/jnews/32117.htm
- http://m.3g.bwbkj.cn/jnews/781052.htm
- http://m.3g.bwbkj.cn/jnews/5394230.htm
- http://m.3g.bwbkj.cn/jnews/028234.htm
- http://m.3g.bwbkj.cn/jnews/6081845.htm
- http://m.3g.bwbkj.cn/jnews/89670.htm
- http://m.3g.bwbkj.cn/jnews/6135435.htm
- http://m.3g.bwbkj.cn/jnews/24646.htm
- http://m.3g.bwbkj.cn/jnews/08541.htm
- http://m.3g.bwbkj.cn/jnews/540439.htm
- http://m.3g.bwbkj.cn/jnews/181629.htm
- http://m.3g.bwbkj.cn/jnews/60532.htm
- http://m.3g.bwbkj.cn/jnews/89088.htm
- http://m.3g.bwbkj.cn/jnews/022176.htm
- http://m.3g.bwbkj.cn/jnews/1113.htm
- http://m.3g.bwbkj.cn/jnews/76724.htm
- http://m.3g.bwbkj.cn/jnews/9219.htm
- http://m.3g.bwbkj.cn/jnews/3887792.htm
- http://m.3g.bwbkj.cn/jnews/227013.htm
- http://m.3g.bwbkj.cn/jnews/44652.htm
- http://m.3g.bwbkj.cn/jnews/103039.htm
- http://m.3g.bwbkj.cn/jnews/0301922.htm
- http://m.3g.bwbkj.cn/jnews/5316.htm
- http://m.3g.bwbkj.cn/jnews/163187.htm
- http://m.3g.bwbkj.cn/jnews/57723.htm
- http://m.3g.bwbkj.cn/jnews/67815.htm
- http://m.3g.bwbkj.cn/jnews/4352160.htm
- http://m.3g.bwbkj.cn/jnews/2203937.htm
- http://m.3g.bwbkj.cn/jnews/87466.htm
- http://m.3g.bwbkj.cn/jnews/7669.htm
- http://m.3g.bwbkj.cn/jnews/222492.htm
- http://m.3g.bwbkj.cn/jnews/946656.htm
- http://m.3g.bwbkj.cn/jnews/1907.htm
- http://m.3g.bwbkj.cn/jnews/7844031.htm
- http://m.3g.bwbkj.cn/jnews/51644.htm
- http://m.3g.bwbkj.cn/jnews/80837.htm
- http://m.3g.bwbkj.cn/jnews/052429.htm
- http://m.3g.bwbkj.cn/jnews/9553.htm
- http://m.3g.bwbkj.cn/jnews/70409.htm
- http://m.3g.bwbkj.cn/jnews/0287285.htm
- http://m.3g.bwbkj.cn/jnews/173225.htm
- http://m.3g.bwbkj.cn/jnews/56962.htm
- http://m.3g.bwbkj.cn/jnews/15269.htm
- http://m.3g.bwbkj.cn/jnews/427824.htm
- http://m.3g.bwbkj.cn/jnews/34556.htm
- http://m.3g.bwbkj.cn/jnews/867806.htm
- http://m.3g.bwbkj.cn/jnews/1056835.htm
- http://m.3g.bwbkj.cn/jnews/598675.htm
- http://m.3g.bwbkj.cn/jnews/528475.htm
- http://m.3g.bwbkj.cn/jnews/8830188.htm
- http://m.3g.bwbkj.cn/jnews/8666588.htm
- http://m.3g.bwbkj.cn/jnews/53376.htm
- http://m.3g.bwbkj.cn/jnews/70690.htm
- http://m.3g.bwbkj.cn/jnews/1258085.htm
- http://m.3g.bwbkj.cn/jnews/7668345.htm
- http://m.3g.bwbkj.cn/jnews/650806.htm
- http://m.3g.bwbkj.cn/jnews/6747790.htm
- http://m.3g.bwbkj.cn/jnews/02061.htm
- http://m.3g.bwbkj.cn/jnews/1823.htm
- http://m.3g.bwbkj.cn/jnews/0058456.htm
- http://m.3g.bwbkj.cn/jnews/4166229.htm
- http://m.3g.bwbkj.cn/jnews/8133.htm
- http://m.3g.bwbkj.cn/jnews/1358.htm
- http://m.3g.bwbkj.cn/jnews/7260147.htm
- http://m.3g.bwbkj.cn/jnews/4284016.htm
- http://m.3g.bwbkj.cn/jnews/48844.htm
- http://m.3g.bwbkj.cn/jnews/050812.htm
- http://m.3g.bwbkj.cn/jnews/049199.htm
- http://m.3g.bwbkj.cn/jnews/370745.htm
- http://m.3g.bwbkj.cn/jnews/612442.htm
- http://m.3g.bwbkj.cn/jnews/4822281.htm
- http://m.3g.bwbkj.cn/jnews/715471.htm
- http://m.3g.bwbkj.cn/jnews/4927.htm
- http://m.3g.bwbkj.cn/jnews/7519.htm
- http://m.3g.bwbkj.cn/jnews/3331472.htm
- http://m.3g.bwbkj.cn/jnews/136523.htm
- http://m.3g.bwbkj.cn/jnews/9208999.htm
- http://m.3g.bwbkj.cn/jnews/5626188.htm
- http://m.3g.bwbkj.cn/jnews/108131.htm
- http://m.3g.bwbkj.cn/jnews/0579.htm
- http://m.3g.bwbkj.cn/jnews/454699.htm
- http://m.3g.bwbkj.cn/jnews/81103.htm
- http://m.3g.bwbkj.cn/jnews/3637.htm
- http://m.3g.bwbkj.cn/jnews/6022355.htm
- http://m.3g.bwbkj.cn/jnews/9278.htm
- http://m.3g.bwbkj.cn/jnews/1227.htm
- http://m.3g.bwbkj.cn/jnews/4593617.htm
- http://m.3g.bwbkj.cn/jnews/3987.htm
- http://m.3g.bwbkj.cn/jnews/6933304.htm
- http://m.3g.bwbkj.cn/jnews/05640.htm
- http://m.3g.bwbkj.cn/jnews/83774.htm
- http://m.3g.bwbkj.cn/jnews/318655.htm
- http://m.3g.bwbkj.cn/jnews/03075.htm
- http://m.3g.bwbkj.cn/jnews/86041.htm
- http://m.3g.bwbkj.cn/jnews/5319135.htm
- http://m.3g.bwbkj.cn/jnews/7900656.htm
- http://m.3g.bwbkj.cn/jnews/33045.htm
- http://m.3g.bwbkj.cn/jnews/282952.htm
- http://m.3g.bwbkj.cn/jnews/0878582.htm
- http://m.3g.bwbkj.cn/jnews/6124.htm
- http://m.3g.bwbkj.cn/jnews/9178.htm

## 项目结构

```
jnews-link-aggregator/
├── app/
│   ├── __init__.py               # Flask 应用工厂与配置加载
│   ├── routes/                   # API 路由模块
│   │   ├── links.py              # 链接资源 CRUD 接口
│   │   ├── tags.py               # 分类标签管理接口
│   │   └── stats.py              # 访问统计与健康状态接口
│   ├── models/                   # 数据模型与 ORM 映射
│   │   ├── link.py               # Link 实体定义与校验逻辑
│   │   ├── tag.py                # Tag 实体定义
│   │   └── audit_log.py          # 操作审计日志实体
│   ├── services/                 # 业务逻辑层
│   │   ├── fetcher.py            # 链接元数据异步抓取服务
│   │   ├── health_check.py       # 链接可用性周期检查调度器
│   │   └── exporter.py           # 数据导出为多种格式
│   └── utils/                    # 通用工具函数
│       ├── http_client.py        # 带超时与重试的 HTTP 请求封装
│       ├── parser.py             # HTML 标题与描述提取器
│       └── validators.py         # URL 格式校验与标准化
├── scripts/                      # 运维与辅助脚本
│   ├── init_db.py                # 初始化 SQLite 数据库表结构
│   ├── import_links.py           # 批量导入链接列表（支持 txt/csv/json）
│   └── export_batch.py           # 导出指定批次为 Markdown 格式
├── tests/                        # 单元测试与集成测试
│   ├── test_models.py            # 数据模型层测试用例
│   ├── test_services.py          # 业务逻辑层测试用例
│   └── test_routes.py            # API 接口端到端测试
├── data/                         # 数据存储目录
│   ├── batch_225_300.txt         # 当前批次原始资源列表（纯文本）
│   └── link_index.db             # SQLite 数据库文件（运行时生成）
├── config/                       # 配置文件目录
│   ├── development.py            # 开发环境配置（调试模式、本地数据库）
│   └── production.py             # 生产环境配置（外部数据库、日志级别）
├── docs/                         # 完整文档体系
│   ├── quickstart.md             # 快速入门指南
│   ├── api_reference.md          # API 详细参考
│   ├── operations.md             # 运维与部署手册
│   └── contributing.md           # 贡献者指南
├── requirements.txt              # Python 依赖声明（pip 安装）
├── .env.example                  # 环境变量模板文件
├── app.py                        # 应用入口文件（开发服务器启动）
├── wsgi.py                       # 生产环境 WSGI 入口
└── README.md                     # 本文档
```

## 贡献指南

**问题报告与功能建议** 请先在 Issues 列表中搜索是否已有相同议题，若不存在则新建 Issue，使用提供的模板详细描述复现步骤或需求场景。

**代码提交准备** 克隆仓库后创建独立的功能分支，分支命名遵循 feature/xxx 或 fix/xxx 格式。在提交前确保所有单元测试通过，并新增至少一个测试用例覆盖你的改动。

**Commit Message 规范** 采用 Conventional Commits 格式，即 `<type>(<scope>): <subject>`，其中 type 可选 feat/fix/docs/style/refactor/test/chore，scope 填写影响的模块名称。

**Pull Request 流程** 将功能分支推送到远程仓库后发起 PR，在 PR 描述中关联对应的 Issue 编号，并说明改动点与测试结果。代码审查通过后由项目维护者合并。

**文档同步更新** 任何功能性变更或新增配置项，须同步更新 README.md 中对应的章节内容，确保文档与代码始终保持一致。

## 常见问题

**问：导入链接时提示重复记录，如何处理？**

导入脚本默认对完整 URL 进行去重校验。若提示重复，可通过 `--skip-duplicates` 参数跳过已存在的记录，或使用 `--update-existing` 参数更新已有记录的元数据字段。重复判断依据为 URL 字符串的完全匹配，不进行模糊去重。

**问：健康检查标记为失效的链接多久会被重试？**

系统默认每 24 小时执行一次全量健康检查，标记为失效的链接会在下次周期检查时自动重试。若连续三次检查均失败，链接状态将变更为 `dead` 并停止后续检查。可通过修改 `config/production.py` 中的 `HEALTH_CHECK_INTERVAL` 和 `MAX_RETRY_FAILURES` 变量调整此行为。

**问：生产环境如何从 SQLite 迁移到 PostgreSQL？**

在 `config/production.py` 中将 `SQLALCHEMY_DATABASE_URI` 修改为 PostgreSQL 连接字符串，格式为 `postgresql://user:password@host/dbname`。项目使用 SQLAlchemy 作为 ORM，迁移时无需修改模型定义。建议使用 `pg_dump` 或 `sqlite3 .dump` 管道配合 `psql` 进行数据迁移，需注意 SQLite 与 PostgreSQL 在布尔类型和自增主键上的差异。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:06
