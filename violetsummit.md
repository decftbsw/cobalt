# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端新闻资讯聚合的开源外链管理工具，专注于对 http://m.wap.ghtkgg.cn 域名下的新闻条目进行批量采集、分类存储与快速检索。该项目主要服务于需要从特定新闻源抓取大量文章链接并进行结构化整理的内容运营人员、数据分析师以及研究移动端新闻分发模式的学术工作者。系统提供从链接抓取、元数据提取到本地索引构建的完整工作流，支持每日数百条新闻链接的增量更新与历史回溯查询。

本项目不提供新闻内容渲染或全文代理服务，仅作为公开链接的整理与导航工具，所有原始内容版权归对应新闻发布方所有。使用者可通过本项目快速定位到目标新闻页面，减少人工整理链接的时间成本。

## 功能概览

**批量链接导入** 支持从文本文件、CSV 或直接通过标准输入一次性导入数百条形如 http://m.wap.ghtkgg.cn/jnews/*.htm 的新闻链接，自动去重并校验链接可访问性。

**分类标签生成** 基于链接 URL 路径中的数字 ID 段，结合可配置的正则规则自动生成内容分类标签，支持按发布时间、ID 区间或自定义关键词进行归类。

**本地索引构建** 将导入的链接存储为 SQLite 本地数据库，建立基于 ID、导入时间、访问状态的多字段索引，实现毫秒级查询响应。

**链接状态监控** 定时检测已收录链接的 HTTP 状态码，标记失效链接（404、500 等），并生成状态报告，便于及时清理或更新资源。

**导出与分享** 支持将筛选后的链接列表导出为 JSON、CSV 或纯文本格式，方便与其他数据处理工具或团队协作平台对接。

**命令行交互界面** 提供完整的 CLI 工具集，涵盖链接添加、列表查看、状态刷新、分类统计等常用操作，无需图形界面即可完成所有管理任务。

**可扩展插件系统** 允许开发者编写自定义解析器，针对特定 ID 段或 URL 模式执行额外的元数据提取逻辑，例如从目标页面标题或 meta 描述中抓取摘要信息。

## 应用场景

**移动端新闻链接归档** 内容运营人员每天从 http://m.wap.ghtkgg.cn 采集大量新闻链接，使用本项目的批量导入和索引功能，可以快速建立按日期和 ID 排序的本地档案库，替代手工维护 Excel 表格的低效方式。

**新闻源可用性监控** 数据分析师需要持续跟踪特定新闻域名的响应稳定性。本项目内置的链接状态监控模块可定期检查收录的所有链接，生成可用性报表，帮助判断新闻源服务健康状况。

**历史链接检索与回溯** 研究人员需要回溯某一时间段内发布的新闻条目。通过项目的 ID 区间查询和导入时间过滤功能，可快速定位到特定批次的所有链接，无需逐页翻阅原始网站。

**数据迁移与格式转换** 当需要将链接列表导入第三方 CMS 或数据分析平台时，本项目的多格式导出功能（JSON、CSV、TXT）可无缝衔接不同系统的数据格式要求，减少手工转换工作量。

## 快速开始

以下命令演示了从克隆仓库到完成首批链接导入的完整流程。

```bash
# 克隆项目仓库
git clone https://github.com/example/jnews-link-aggregator.git
cd jnews-link-aggregator

# 安装依赖（使用 pip 和系统级工具）
pip install -r requirements.txt
sudo apt-get install sqlite3 curl  # Debian/Ubuntu 系

# 运行初始导入（将待导入链接放入 data/raw_links.txt，每行一个 URL）
python bin/import_links.py --input data/raw_links.txt --db data/jnews.db

# 查看已导入链接统计
python bin/list_links.py --db data/jnews.db --count

# 检查所有链接状态
python bin/check_status.py --db data/jnews.db --timeout 5 --workers 10
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行所有管理脚本 |
| SQLite | 3.31 及以上 | 本地索引数据库引擎，支持 JSON1 扩展以优化元数据存储 |
| curl | 7.68 及以上 | 用于链接状态检测时的 HTTP 请求发送，支持 HTTPS 和重定向跟踪 |
| pip | 20.0 及以上 | Python 包管理器，用于安装 requests、click、tinydb 等第三方库 |
| Git | 2.25 及以上 | 版本控制工具，用于克隆仓库和后续更新拉取 |
| GNU Make | 3.81 及以上 | 可选，用于自动化常见任务（如 make import、make check） |
| bash | 4.4 及以上 | 用于运行提供的 Shell 辅助脚本（如 utils/batch_check.sh） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何导入链接、如何查看列表、如何导出数据、如何进行日常维护 |
| 配置参考 | docs/configuration.md | 配置文件格式、各参数含义、自定义分类规则写法、数据库路径设置 |
| 开发者指南 | docs/developer-guide.md | 插件开发接口、数据库表结构、单元测试编写、PR 提交规范 |
| 运维手册 | docs/operations.md | 定时任务配置、日志轮转策略、数据库备份恢复、大规模导入性能调优 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/4134891.htm
- http://m.wap.ghtkgg.cn/jnews/546601.htm
- http://m.wap.ghtkgg.cn/jnews/67052.htm
- http://m.wap.ghtkgg.cn/jnews/46424.htm
- http://m.wap.ghtkgg.cn/jnews/1456884.htm
- http://m.wap.ghtkgg.cn/jnews/438033.htm
- http://m.wap.ghtkgg.cn/jnews/937525.htm
- http://m.wap.ghtkgg.cn/jnews/7155734.htm
- http://m.wap.ghtkgg.cn/jnews/1710.htm
- http://m.wap.ghtkgg.cn/jnews/09064.htm
- http://m.wap.ghtkgg.cn/jnews/4494722.htm
- http://m.wap.ghtkgg.cn/jnews/7412134.htm
- http://m.wap.ghtkgg.cn/jnews/17653.htm
- http://m.wap.ghtkgg.cn/jnews/36826.htm
- http://m.wap.ghtkgg.cn/jnews/4564.htm
- http://m.wap.ghtkgg.cn/jnews/76738.htm
- http://m.wap.ghtkgg.cn/jnews/8045684.htm
- http://m.wap.ghtkgg.cn/jnews/711147.htm
- http://m.wap.ghtkgg.cn/jnews/6553666.htm
- http://m.wap.ghtkgg.cn/jnews/5594746.htm
- http://m.wap.ghtkgg.cn/jnews/254919.htm
- http://m.wap.ghtkgg.cn/jnews/145634.htm
- http://m.wap.ghtkgg.cn/jnews/8930.htm
- http://m.wap.ghtkgg.cn/jnews/6427235.htm
- http://m.wap.ghtkgg.cn/jnews/8057.htm
- http://m.wap.ghtkgg.cn/jnews/0301.htm
- http://m.wap.ghtkgg.cn/jnews/353935.htm
- http://m.wap.ghtkgg.cn/jnews/5468.htm
- http://m.wap.ghtkgg.cn/jnews/517980.htm
- http://m.wap.ghtkgg.cn/jnews/1200.htm
- http://m.wap.ghtkgg.cn/jnews/4141.htm
- http://m.wap.ghtkgg.cn/jnews/47589.htm
- http://m.wap.ghtkgg.cn/jnews/2800.htm
- http://m.wap.ghtkgg.cn/jnews/9041497.htm
- http://m.wap.ghtkgg.cn/jnews/0724.htm
- http://m.wap.ghtkgg.cn/jnews/2970.htm
- http://m.wap.ghtkgg.cn/jnews/1972325.htm
- http://m.wap.ghtkgg.cn/jnews/06260.htm
- http://m.wap.ghtkgg.cn/jnews/2925340.htm
- http://m.wap.ghtkgg.cn/jnews/82022.htm
- http://m.wap.ghtkgg.cn/jnews/585445.htm
- http://m.wap.ghtkgg.cn/jnews/9919974.htm
- http://m.wap.ghtkgg.cn/jnews/3474.htm
- http://m.wap.ghtkgg.cn/jnews/683615.htm
- http://m.wap.ghtkgg.cn/jnews/915435.htm
- http://m.wap.ghtkgg.cn/jnews/43314.htm
- http://m.wap.ghtkgg.cn/jnews/2557083.htm
- http://m.wap.ghtkgg.cn/jnews/66490.htm
- http://m.wap.ghtkgg.cn/jnews/117623.htm
- http://m.wap.ghtkgg.cn/jnews/722962.htm
- http://m.wap.ghtkgg.cn/jnews/126971.htm
- http://m.wap.ghtkgg.cn/jnews/8444734.htm
- http://m.wap.ghtkgg.cn/jnews/0890239.htm
- http://m.wap.ghtkgg.cn/jnews/03759.htm
- http://m.wap.ghtkgg.cn/jnews/4546.htm
- http://m.wap.ghtkgg.cn/jnews/7749238.htm
- http://m.wap.ghtkgg.cn/jnews/17745.htm
- http://m.wap.ghtkgg.cn/jnews/382801.htm
- http://m.wap.ghtkgg.cn/jnews/959955.htm
- http://m.wap.ghtkgg.cn/jnews/0180166.htm
- http://m.wap.ghtkgg.cn/jnews/5880.htm
- http://m.wap.ghtkgg.cn/jnews/03927.htm
- http://m.wap.ghtkgg.cn/jnews/6171.htm
- http://m.wap.ghtkgg.cn/jnews/9971591.htm
- http://m.wap.ghtkgg.cn/jnews/0602.htm
- http://m.wap.ghtkgg.cn/jnews/0654.htm
- http://m.wap.ghtkgg.cn/jnews/55252.htm
- http://m.wap.ghtkgg.cn/jnews/1605596.htm
- http://m.wap.ghtkgg.cn/jnews/5864.htm
- http://m.wap.ghtkgg.cn/jnews/7547480.htm
- http://m.wap.ghtkgg.cn/jnews/341998.htm
- http://m.wap.ghtkgg.cn/jnews/3763303.htm
- http://m.wap.ghtkgg.cn/jnews/660337.htm
- http://m.wap.ghtkgg.cn/jnews/8562.htm
- http://m.wap.ghtkgg.cn/jnews/502695.htm
- http://m.wap.ghtkgg.cn/jnews/629611.htm
- http://m.wap.ghtkgg.cn/jnews/248784.htm
- http://m.wap.ghtkgg.cn/jnews/36505.htm
- http://m.wap.ghtkgg.cn/jnews/7448.htm
- http://m.wap.ghtkgg.cn/jnews/3256152.htm
- http://m.wap.ghtkgg.cn/jnews/5370730.htm
- http://m.wap.ghtkgg.cn/jnews/6272.htm
- http://m.wap.ghtkgg.cn/jnews/22692.htm
- http://m.wap.ghtkgg.cn/jnews/8760.htm
- http://m.wap.ghtkgg.cn/jnews/57467.htm
- http://m.wap.ghtkgg.cn/jnews/795407.htm
- http://m.wap.ghtkgg.cn/jnews/74756.htm
- http://m.wap.ghtkgg.cn/jnews/5926.htm
- http://m.wap.ghtkgg.cn/jnews/0147522.htm
- http://m.wap.ghtkgg.cn/jnews/6954.htm
- http://m.wap.ghtkgg.cn/jnews/6249.htm
- http://m.wap.ghtkgg.cn/jnews/49693.htm
- http://m.wap.ghtkgg.cn/jnews/705793.htm
- http://m.wap.ghtkgg.cn/jnews/4343165.htm
- http://m.wap.ghtkgg.cn/jnews/1588580.htm
- http://m.wap.ghtkgg.cn/jnews/903915.htm
- http://m.wap.ghtkgg.cn/jnews/307355.htm
- http://m.wap.ghtkgg.cn/jnews/7609.htm
- http://m.wap.ghtkgg.cn/jnews/895532.htm
- http://m.wap.ghtkgg.cn/jnews/0675641.htm
- http://m.wap.ghtkgg.cn/jnews/793816.htm
- http://m.wap.ghtkgg.cn/jnews/14694.htm
- http://m.wap.ghtkgg.cn/jnews/07981.htm
- http://m.wap.ghtkgg.cn/jnews/760763.htm
- http://m.wap.ghtkgg.cn/jnews/235912.htm
- http://m.wap.ghtkgg.cn/jnews/8962870.htm
- http://m.wap.ghtkgg.cn/jnews/619385.htm
- http://m.wap.ghtkgg.cn/jnews/3606878.htm
- http://m.wap.ghtkgg.cn/jnews/5453.htm
- http://m.wap.ghtkgg.cn/jnews/4227.htm
- http://m.wap.ghtkgg.cn/jnews/25001.htm
- http://m.wap.ghtkgg.cn/jnews/1961689.htm
- http://m.wap.ghtkgg.cn/jnews/643958.htm
- http://m.wap.ghtkgg.cn/jnews/865451.htm
- http://m.wap.ghtkgg.cn/jnews/2939275.htm
- http://m.wap.ghtkgg.cn/jnews/5483784.htm
- http://m.wap.ghtkgg.cn/jnews/6904958.htm
- http://m.wap.ghtkgg.cn/jnews/448453.htm
- http://m.wap.ghtkgg.cn/jnews/6461617.htm
- http://m.wap.ghtkgg.cn/jnews/8724617.htm
- http://m.wap.ghtkgg.cn/jnews/40641.htm
- http://m.wap.ghtkgg.cn/jnews/3522.htm
- http://m.wap.ghtkgg.cn/jnews/1745698.htm
- http://m.wap.ghtkgg.cn/jnews/079051.htm
- http://m.wap.ghtkgg.cn/jnews/54554.htm
- http://m.wap.ghtkgg.cn/jnews/81780.htm
- http://m.wap.ghtkgg.cn/jnews/2126194.htm
- http://m.wap.ghtkgg.cn/jnews/5457076.htm
- http://m.wap.ghtkgg.cn/jnews/8509548.htm
- http://m.wap.ghtkgg.cn/jnews/03537.htm
- http://m.wap.ghtkgg.cn/jnews/767350.htm
- http://m.wap.ghtkgg.cn/jnews/9143.htm
- http://m.wap.ghtkgg.cn/jnews/66085.htm
- http://m.wap.ghtkgg.cn/jnews/3824.htm
- http://m.wap.ghtkgg.cn/jnews/91779.htm
- http://m.wap.ghtkgg.cn/jnews/7763264.htm
- http://m.wap.ghtkgg.cn/jnews/3091910.htm
- http://m.wap.ghtkgg.cn/jnews/38084.htm
- http://m.wap.ghtkgg.cn/jnews/8050841.htm
- http://m.wap.ghtkgg.cn/jnews/9145.htm
- http://m.wap.ghtkgg.cn/jnews/76610.htm
- http://m.wap.ghtkgg.cn/jnews/4299503.htm
- http://m.wap.ghtkgg.cn/jnews/1632634.htm
- http://m.wap.ghtkgg.cn/jnews/82770.htm
- http://m.wap.ghtkgg.cn/jnews/7311842.htm
- http://m.wap.ghtkgg.cn/jnews/2140.htm
- http://m.wap.ghtkgg.cn/jnews/34051.htm
- http://m.wap.ghtkgg.cn/jnews/0914940.htm
- http://m.wap.ghtkgg.cn/jnews/46706.htm
- http://m.wap.ghtkgg.cn/jnews/556971.htm
- http://m.wap.ghtkgg.cn/jnews/35168.htm
- http://m.wap.ghtkgg.cn/jnews/879150.htm
- http://m.wap.ghtkgg.cn/jnews/8542737.htm
- http://m.wap.ghtkgg.cn/jnews/811126.htm
- http://m.wap.ghtkgg.cn/jnews/0070.htm
- http://m.wap.ghtkgg.cn/jnews/1417233.htm
- http://m.wap.ghtkgg.cn/jnews/187488.htm
- http://m.wap.ghtkgg.cn/jnews/8987.htm
- http://m.wap.ghtkgg.cn/jnews/0023915.htm
- http://m.wap.ghtkgg.cn/jnews/3231171.htm
- http://m.wap.ghtkgg.cn/jnews/78670.htm
- http://m.wap.ghtkgg.cn/jnews/872914.htm
- http://m.wap.ghtkgg.cn/jnews/7950.htm
- http://m.wap.ghtkgg.cn/jnews/855766.htm
- http://m.wap.ghtkgg.cn/jnews/311416.htm
- http://m.wap.ghtkgg.cn/jnews/5385158.htm
- http://m.wap.ghtkgg.cn/jnews/1160.htm
- http://m.wap.ghtkgg.cn/jnews/3880611.htm
- http://m.wap.ghtkgg.cn/jnews/6631.htm
- http://m.wap.ghtkgg.cn/jnews/49573.htm
- http://m.wap.ghtkgg.cn/jnews/66410.htm
- http://m.wap.ghtkgg.cn/jnews/453062.htm
- http://m.wap.ghtkgg.cn/jnews/245835.htm
- http://m.wap.ghtkgg.cn/jnews/91679.htm
- http://m.wap.ghtkgg.cn/jnews/9494.htm
- http://m.wap.ghtkgg.cn/jnews/12463.htm
- http://m.wap.ghtkgg.cn/jnews/21075.htm
- http://m.wap.ghtkgg.cn/jnews/91285.htm
- http://m.wap.ghtkgg.cn/jnews/343692.htm
- http://m.wap.ghtkgg.cn/jnews/6871865.htm
- http://m.wap.ghtkgg.cn/jnews/8295.htm
- http://m.wap.ghtkgg.cn/jnews/54801.htm
- http://m.wap.ghtkgg.cn/jnews/176917.htm
- http://m.wap.ghtkgg.cn/jnews/5069236.htm
- http://m.wap.ghtkgg.cn/jnews/872547.htm
- http://m.wap.ghtkgg.cn/jnews/882843.htm
- http://m.wap.ghtkgg.cn/jnews/4016586.htm
- http://m.wap.ghtkgg.cn/jnews/91796.htm
- http://m.wap.ghtkgg.cn/jnews/6350.htm
- http://m.wap.ghtkgg.cn/jnews/7451338.htm
- http://m.wap.ghtkgg.cn/jnews/46747.htm
- http://m.wap.ghtkgg.cn/jnews/67450.htm
- http://m.wap.ghtkgg.cn/jnews/70691.htm
- http://m.wap.ghtkgg.cn/jnews/1822.htm
- http://m.wap.ghtkgg.cn/jnews/017886.htm
- http://m.wap.ghtkgg.cn/jnews/07035.htm
- http://m.wap.ghtkgg.cn/jnews/42727.htm
- http://m.wap.ghtkgg.cn/jnews/2265.htm
- http://m.wap.ghtkgg.cn/jnews/7175.htm
- http://m.wap.ghtkgg.cn/jnews/5625.htm
- http://m.wap.ghtkgg.cn/jnews/6838183.htm
- http://m.wap.ghtkgg.cn/jnews/7328.htm
- http://m.wap.ghtkgg.cn/jnews/219487.htm
- http://m.wap.ghtkgg.cn/jnews/2080.htm
- http://m.wap.ghtkgg.cn/jnews/99090.htm
- http://m.wap.ghtkgg.cn/jnews/081630.htm
- http://m.wap.ghtkgg.cn/jnews/878135.htm
- http://m.wap.ghtkgg.cn/jnews/111010.htm
- http://m.wap.ghtkgg.cn/jnews/1832282.htm
- http://m.wap.ghtkgg.cn/jnews/1013.htm
- http://m.wap.ghtkgg.cn/jnews/729626.htm
- http://m.wap.ghtkgg.cn/jnews/18390.htm
- http://m.wap.ghtkgg.cn/jnews/50972.htm
- http://m.wap.ghtkgg.cn/jnews/318714.htm
- http://m.wap.ghtkgg.cn/jnews/2382976.htm
- http://m.wap.ghtkgg.cn/jnews/9694.htm
- http://m.wap.ghtkgg.cn/jnews/266886.htm
- http://m.wap.ghtkgg.cn/jnews/071695.htm
- http://m.wap.ghtkgg.cn/jnews/2848325.htm
- http://m.wap.ghtkgg.cn/jnews/312785.htm
- http://m.wap.ghtkgg.cn/jnews/5037389.htm
- http://m.wap.ghtkgg.cn/jnews/628095.htm
- http://m.wap.ghtkgg.cn/jnews/9149772.htm
- http://m.wap.ghtkgg.cn/jnews/3055.htm
- http://m.wap.ghtkgg.cn/jnews/17142.htm
- http://m.wap.ghtkgg.cn/jnews/630346.htm
- http://m.wap.ghtkgg.cn/jnews/351749.htm
- http://m.wap.ghtkgg.cn/jnews/94019.htm
- http://m.wap.ghtkgg.cn/jnews/740264.htm
- http://m.wap.ghtkgg.cn/jnews/0863.htm
- http://m.wap.ghtkgg.cn/jnews/1073320.htm
- http://m.wap.ghtkgg.cn/jnews/2364787.htm
- http://m.wap.ghtkgg.cn/jnews/6271911.htm
- http://m.wap.ghtkgg.cn/jnews/9326.htm
- http://m.wap.ghtkgg.cn/jnews/08962.htm
- http://m.wap.ghtkgg.cn/jnews/1706318.htm
- http://m.wap.ghtkgg.cn/jnews/966142.htm
- http://m.wap.ghtkgg.cn/jnews/7227477.htm
- http://m.wap.ghtkgg.cn/jnews/2220052.htm
- http://m.wap.ghtkgg.cn/jnews/44488.htm
- http://m.wap.ghtkgg.cn/jnews/02711.htm
- http://m.wap.ghtkgg.cn/jnews/183154.htm
- http://m.wap.ghtkgg.cn/jnews/7265.htm
- http://m.wap.ghtkgg.cn/jnews/2004600.htm
- http://m.wap.ghtkgg.cn/jnews/15011.htm
- http://m.wap.ghtkgg.cn/jnews/77380.htm
- http://m.wap.ghtkgg.cn/jnews/7372937.htm
- http://m.wap.ghtkgg.cn/jnews/5823.htm
- http://m.wap.ghtkgg.cn/jnews/44181.htm
- http://m.wap.ghtkgg.cn/jnews/127570.htm
- http://m.wap.ghtkgg.cn/jnews/914623.htm
- http://m.wap.ghtkgg.cn/jnews/08080.htm
- http://m.wap.ghtkgg.cn/jnews/2319009.htm
- http://m.wap.ghtkgg.cn/jnews/5057210.htm
- http://m.wap.ghtkgg.cn/jnews/041485.htm
- http://m.wap.ghtkgg.cn/jnews/8273421.htm
- http://m.wap.ghtkgg.cn/jnews/37313.htm
- http://m.wap.ghtkgg.cn/jnews/7005811.htm
- http://m.wap.ghtkgg.cn/jnews/0380.htm
- http://m.wap.ghtkgg.cn/jnews/6667.htm
- http://m.wap.ghtkgg.cn/jnews/94697.htm
- http://m.wap.ghtkgg.cn/jnews/2093.htm
- http://m.wap.ghtkgg.cn/jnews/45436.htm
- http://m.wap.ghtkgg.cn/jnews/22865.htm
- http://m.wap.ghtkgg.cn/jnews/89890.htm
- http://m.wap.ghtkgg.cn/jnews/130011.htm
- http://m.wap.ghtkgg.cn/jnews/005696.htm
- http://m.wap.ghtkgg.cn/jnews/6615.htm
- http://m.wap.ghtkgg.cn/jnews/87914.htm
- http://m.wap.ghtkgg.cn/jnews/92427.htm
- http://m.wap.ghtkgg.cn/jnews/6956401.htm
- http://m.wap.ghtkgg.cn/jnews/058038.htm
- http://m.wap.ghtkgg.cn/jnews/68065.htm
- http://m.wap.ghtkgg.cn/jnews/0848.htm
- http://m.wap.ghtkgg.cn/jnews/849840.htm
- http://m.wap.ghtkgg.cn/jnews/49968.htm
- http://m.wap.ghtkgg.cn/jnews/9915996.htm
- http://m.wap.ghtkgg.cn/jnews/52391.htm
- http://m.wap.ghtkgg.cn/jnews/2811704.htm
- http://m.wap.ghtkgg.cn/jnews/3398822.htm
- http://m.wap.ghtkgg.cn/jnews/13248.htm
- http://m.wap.ghtkgg.cn/jnews/3657883.htm
- http://m.wap.ghtkgg.cn/jnews/99350.htm
- http://m.wap.ghtkgg.cn/jnews/886783.htm
- http://m.wap.ghtkgg.cn/jnews/6758.htm
- http://m.wap.ghtkgg.cn/jnews/5449611.htm
- http://m.wap.ghtkgg.cn/jnews/80450.htm
- http://m.wap.ghtkgg.cn/jnews/514932.htm
- http://m.wap.ghtkgg.cn/jnews/357107.htm
- http://m.wap.ghtkgg.cn/jnews/58445.htm
- http://m.wap.ghtkgg.cn/jnews/653171.htm
- http://m.wap.ghtkgg.cn/jnews/65072.htm
- http://m.wap.ghtkgg.cn/jnews/665930.htm
- http://m.wap.ghtkgg.cn/jnews/1904.htm
- http://m.wap.ghtkgg.cn/jnews/9435439.htm
- http://m.wap.ghtkgg.cn/jnews/7160.htm
- http://m.wap.ghtkgg.cn/jnews/610509.htm
- http://m.wap.ghtkgg.cn/jnews/6985435.htm
- http://m.wap.ghtkgg.cn/jnews/755650.htm
- http://m.wap.ghtkgg.cn/jnews/36311.htm

## 项目结构

```
jnews-link-aggregator/
├── bin/                                # 可执行脚本目录
│   ├── import_links.py                 # 批量导入链接主程序，支持 stdin 和文件输入
│   ├── list_links.py                   # 链接列表查看器，支持按 ID、日期、状态过滤
│   ├── check_status.py                 # 批量状态检测工具，支持并发请求
│   └── export_links.py                 # 导出为 JSON/CSV/TXT 格式
├── lib/                                # 核心库代码
│   ├── storage.py                      # SQLite 数据库连接与 CRUD 操作封装
│   ├── fetcher.py                      # 基于 requests 和 curl 的 HTTP 请求模块
│   ├── classifier.py                   # 基于正则和规则的自动标签生成器
│   └── plugins/                        # 插件目录
│       ├── __init__.py                 # 插件加载器
│       └── sample_parser.py            # 示例解析器，展示如何从标题提取关键词
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认配置（数据库路径、并发数、超时时间）
│   └── rules.yaml                      # 分类规则定义（ID 区间到标签的映射）
├── data/                               # 数据存储目录（运行时生成）
│   ├── jnews.db                        # SQLite 主数据库文件
│   ├── raw_links.txt                   # 待导入的原始链接列表（用户放入）
│   └── archives/                       # 历史导入批次归档（按日期存放）
├── docs/                               # 完整文档
│   ├── user-guide.md                   # 用户手册：安装、配置、日常操作
│   ├── developer-guide.md              # 开发者指南：API 说明、插件编写、测试
│   ├── operations.md                   # 运维手册：备份、监控、性能调优
│   └── configuration.md                # 配置参数详解
├── tests/                              # 单元测试与集成测试
│   ├── test_storage.py                 # 数据库模块测试
│   ├── test_fetcher.py                 # 请求模块测试（含 mock）
│   └── test_classifier.py              # 分类器逻辑测试
├── utils/                              # 辅助工具脚本
│   ├── batch_check.sh                  # 批量检查链接状态的 Shell 包装器
│   └── dedup_links.py                  # 去重工具，合并多个列表文件
├── Makefile                            # 常用任务自动化（import, check, export, clean）
├── requirements.txt                    # Python 依赖列表（requests==2.28.2, click==8.1.3, tinydb==4.8.0）
└── README.md                           # 本文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并克隆到本地开发环境。确保使用 Python 3.8+ 虚拟环境，并执行 `pip install -r requirements-dev.txt` 安装开发依赖（包含 pytest、black、flake8）。

2. 在 `lib/plugins/` 目录下创建新的解析器插件，继承基类 `BaseParser` 并实现 `parse(link_id, html)` 方法。请一并编写对应的单元测试，放入 `tests/test_plugins/` 目录。

3. 运行 `make lint` 检查代码风格（遵循 PEP 8），执行 `make test` 确保所有现有测试通过且覆盖率不低于 85%。新增功能请补充文档字符串和用户手册对应章节。

4. 提交 pull request 时，请描述清晰的问题背景、解决方案和测试结果。若涉及配置格式变更，需要同时更新 `config/default.yaml` 和 `docs/configuration.md` 中的对应说明。

5. 对于较大的特性或架构调整，建议先在 Issues 中提出设计讨论，获得核心维护者反馈后再投入开发，以避免方向偏离。所有 PR 需要至少一名维护者 approve 后方可合并。

## 常见问题

**Q: 导入链接时提示 "duplicate entry" 错误，如何处理？**

A: 这表示该链接已经存在于数据库中。系统默认会拒绝重复导入以防止数据冗余。如需强制重新导入覆盖元数据，可使用 `--force` 选项（例如 `python bin/import_links.py --force`）。若需查看已存在的链接列表，可使用 `python bin/list_links.py --id <数字ID>` 进行查询。

**Q: 链接状态检测非常慢，能否提高速度？**

A: 状态检测模块支持多线程并发，可以通过 `--workers` 参数调整并发数。默认值为 10，建议根据网络环境和目标服务器负载调节至 20-50。同时可使用 `--timeout` 缩短单个请求等待时间（默认 5 秒）。若检测对象多为内网或稳定域名，可将超时设为 3 秒以提升整体速度。

**Q: 如何清理 6 个月前的失效链接？**

A: 可以使用 `bin/export_links.py --status dead --before "6 months ago"` 先导出失效链接列表进行人工确认，再执行 `bin/import_links.py --purge --input <导出文件>` 来删除对应的数据库记录。注意该操作不可逆，建议执行前备份 `data/jnews.db` 文件。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:05
