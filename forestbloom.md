# NewsLink Navigator

NewsLink Navigator 是一个面向技术内容聚合与新闻外链管理的开源工具集，专为需要批量处理、归档和展示来自移动端新闻源（如 3g 门户站点）的链接资源而设计。该项目定位为技术资源与外链汇总中间件，提供从原始 URL 采集、规范化存储到前端展示的完整工作流，适用于个人开发者、内容运营团队以及开源文档站点的外链治理场景。

该项目解决的核心问题包括：海量散乱 URL 的结构化整理、链接可访问性探测、元信息自动抽取以及基于分类标签的快速检索。通过将原始新闻链接转化为可维护的数据资产，NewsLink Navigator 帮助用户节省手工整理时间，提升外链复用效率，并为后续的数据分析或内容推荐提供基础数据支撑。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接记录，自动解析 URL 结构并提取域名、路径、查询参数等关键字段。

**元信息自动补全** 对每条链接执行可配置的元数据抓取任务，包括页面标题、响应状态码、内容类型、字符集以及最后修改时间，补全结果存入本地 SQLite 数据库。

**链接健康检查** 周期性对已存储的链接发起 HTTP 请求，检测响应状态、重定向链及加载耗时，标记失效或异常链接并生成报表。

**分类标签系统** 支持用户自定义标签库，对链接进行多标签标注，并提供标签筛选、组合查询和标签使用频次统计功能。

**全文检索与过滤** 基于 SQLite FTS5 扩展实现链接标题、描述及 URL 自身的全文搜索，同时支持按域名、状态码、标签组合等维度进行过滤。

**数据导出与分享** 将选定的链接集合导出为 JSON、CSV 或 Markdown 列表格式，便于嵌入文档、Wiki 或用于外部系统对接。

**定时任务编排** 内置基于 cron 表达式的调度器，可自动执行导入、健康检查、元数据更新等周期性任务，减少人工干预。

**RESTful API 接口** 提供轻量级 HTTP API，允许第三方系统远程调用链接查询、新增、更新和删除操作，支持 JSON 格式交互。

## 应用场景

**开源文档站点的外链治理** 开源项目维护者可以使用 NewsLink Navigator 统一管理项目文档中引用的所有外部链接，定期检查链接可用性，避免文档中出现死链，提升用户阅读体验。

**技术资讯聚合与归档** 技术博主或信息聚合平台运营者可将来自移动端新闻源的大量链接导入系统，自动抓取标题和摘要，构建可检索的技术资讯库，用于后续的内容策划或数据分析。

**数据迁移前的链接盘点** 在进行网站改版或域名迁移时，通过该工具批量导入旧站点的所有外链，分析链接分布和状态，制定合理的重定向或替换策略，降低迁移风险。

**研究数据集的构建** 学术研究人员或数据分析师可利用该工具从指定来源收集大量链接样本，导出结构化数据集，用于网络分析、链接生命周期研究或机器学习模型的训练语料构建。

## 快速开始

以下命令演示了如何获取项目源码、安装依赖并启动开发服务器。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newslink-navigator.git

# 进入项目目录
cd newslink-navigator

# 创建并激活 Python 虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate

# 安装核心依赖
pip install -r requirements.txt

# 初始化数据库（包含表结构和 FTS5 索引）
python scripts/init_db.py

# 导入示例链接列表（使用项目自带的 sample_links.txt）
python scripts/import_links.py --input sample_links.txt --source "3g-news"

# 启动 Web 服务（默认监听 8000 端口）
python app.py
```

访问 http://127.0.0.1:8000 即可进入链接管理面板。生产环境部署建议使用 gunicorn 或 uwsgi 作为 WSGI 服务器。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，低于 3.9 版本将无法使用类型注解和部分标准库特性 |
| SQLite | 3.35.0 及以上 | 内置数据库引擎，要求支持 FTS5 全文搜索扩展和 JSON1 扩展 |
| requests | 2.28.0 及以上 | 用于发送 HTTP 请求以获取链接元信息和进行健康检查 |
| beautifulsoup4 | 4.11.0 及以上 | 解析 HTML 页面内容，提取标题、描述等元数据 |
| apscheduler | 3.10.0 及以上 | 提供定时任务调度能力，支持 cron 表达式配置 |
| flask | 2.2.0 及以上 | Web 界面和 RESTful API 的基础框架 |
| flask-cors | 4.0.0 及以上 | 处理跨域资源共享，便于前端独立部署时调用 API |
| pytest | 7.0.0 及以上 | 单元测试和集成测试框架（仅开发环境需要） |
| black | 22.0.0 及以上 | 代码格式化工具（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户指南 | docs/user-guide/ | 如何安装配置、导入链接、使用标签系统和检索功能 |
| 运维手册 | docs/ops-guide/ | 如何部署生产环境、配置定时任务、备份恢复数据 |
| API 参考 | docs/api-reference/ | 每个 RESTful 端点的请求参数、响应格式和错误码含义 |
| 开发者指南 | docs/developer-guide/ | 项目架构设计、核心模块说明、如何提交代码和扩展功能 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/5773.htm
- http://m.3g.oexnr.cn/nnews/070122.htm
- http://m.3g.oexnr.cn/nnews/218871.htm
- http://m.3g.oexnr.cn/nnews/18752.htm
- http://m.3g.oexnr.cn/nnews/287671.htm
- http://m.3g.oexnr.cn/nnews/925484.htm
- http://m.3g.oexnr.cn/nnews/45921.htm
- http://m.3g.oexnr.cn/nnews/0759.htm
- http://m.3g.oexnr.cn/nnews/61672.htm
- http://m.3g.oexnr.cn/nnews/8692.htm
- http://m.3g.oexnr.cn/nnews/68806.htm
- http://m.3g.oexnr.cn/nnews/1928.htm
- http://m.3g.oexnr.cn/nnews/7376355.htm
- http://m.3g.oexnr.cn/nnews/4005883.htm
- http://m.3g.oexnr.cn/nnews/1273.htm
- http://m.3g.oexnr.cn/nnews/6295.htm
- http://m.3g.oexnr.cn/nnews/031140.htm
- http://m.3g.oexnr.cn/nnews/8593361.htm
- http://m.3g.oexnr.cn/nnews/5744665.htm
- http://m.3g.oexnr.cn/nnews/7595689.htm
- http://m.3g.oexnr.cn/nnews/5898724.htm
- http://m.3g.oexnr.cn/nnews/85689.htm
- http://m.3g.oexnr.cn/nnews/40256.htm
- http://m.3g.oexnr.cn/nnews/225359.htm
- http://m.3g.oexnr.cn/nnews/6223.htm
- http://m.3g.oexnr.cn/nnews/0391411.htm
- http://m.3g.oexnr.cn/nnews/0489727.htm
- http://m.3g.oexnr.cn/nnews/0285073.htm
- http://m.3g.oexnr.cn/nnews/395565.htm
- http://m.3g.oexnr.cn/nnews/725917.htm
- http://m.3g.oexnr.cn/nnews/6610.htm
- http://m.3g.oexnr.cn/nnews/6556.htm
- http://m.3g.oexnr.cn/nnews/2782770.htm
- http://m.3g.oexnr.cn/nnews/5652617.htm
- http://m.3g.oexnr.cn/nnews/408112.htm
- http://m.3g.oexnr.cn/nnews/8434148.htm
- http://m.3g.oexnr.cn/nnews/4220551.htm
- http://m.3g.oexnr.cn/nnews/8673756.htm
- http://m.3g.oexnr.cn/nnews/8833.htm
- http://m.3g.oexnr.cn/nnews/30559.htm
- http://m.3g.oexnr.cn/nnews/19493.htm
- http://m.3g.oexnr.cn/nnews/72837.htm
- http://m.3g.oexnr.cn/nnews/5616.htm
- http://m.3g.oexnr.cn/nnews/86543.htm
- http://m.3g.oexnr.cn/nnews/0233728.htm
- http://m.3g.oexnr.cn/nnews/1638.htm
- http://m.3g.oexnr.cn/nnews/6099696.htm
- http://m.3g.oexnr.cn/nnews/835199.htm
- http://m.3g.oexnr.cn/nnews/65516.htm
- http://m.3g.oexnr.cn/nnews/9268.htm
- http://m.3g.oexnr.cn/nnews/5315.htm
- http://m.3g.oexnr.cn/nnews/01735.htm
- http://m.3g.oexnr.cn/nnews/53642.htm
- http://m.3g.oexnr.cn/nnews/57101.htm
- http://m.3g.oexnr.cn/nnews/6646.htm
- http://m.3g.oexnr.cn/nnews/14448.htm
- http://m.3g.oexnr.cn/nnews/7356.htm
- http://m.3g.oexnr.cn/nnews/98245.htm
- http://m.3g.oexnr.cn/nnews/3757828.htm
- http://m.3g.oexnr.cn/nnews/5804969.htm
- http://m.3g.oexnr.cn/nnews/9294.htm
- http://m.3g.oexnr.cn/nnews/354576.htm
- http://m.3g.oexnr.cn/nnews/509183.htm
- http://m.3g.oexnr.cn/nnews/5005595.htm
- http://m.3g.oexnr.cn/nnews/42276.htm
- http://m.3g.oexnr.cn/nnews/9653.htm
- http://m.3g.oexnr.cn/nnews/95434.htm
- http://m.3g.oexnr.cn/nnews/7422741.htm
- http://m.3g.oexnr.cn/nnews/9846.htm
- http://m.3g.oexnr.cn/nnews/2650922.htm
- http://m.3g.oexnr.cn/nnews/1806985.htm
- http://m.3g.oexnr.cn/nnews/2683.htm
- http://m.3g.oexnr.cn/nnews/7402.htm
- http://m.3g.oexnr.cn/nnews/279539.htm
- http://m.3g.oexnr.cn/nnews/027671.htm
- http://m.3g.oexnr.cn/nnews/014018.htm
- http://m.3g.oexnr.cn/nnews/7277.htm
- http://m.3g.oexnr.cn/nnews/7953416.htm
- http://m.3g.oexnr.cn/nnews/4548.htm
- http://m.3g.oexnr.cn/nnews/361067.htm
- http://m.3g.oexnr.cn/nnews/596641.htm
- http://m.3g.oexnr.cn/nnews/25616.htm
- http://m.3g.oexnr.cn/nnews/0938434.htm
- http://m.3g.oexnr.cn/nnews/94069.htm
- http://m.3g.oexnr.cn/nnews/76204.htm
- http://m.3g.oexnr.cn/nnews/47369.htm
- http://m.3g.oexnr.cn/nnews/31444.htm
- http://m.3g.oexnr.cn/nnews/329930.htm
- http://m.3g.oexnr.cn/nnews/4120.htm
- http://m.3g.oexnr.cn/nnews/441113.htm
- http://m.3g.oexnr.cn/nnews/62096.htm
- http://m.3g.oexnr.cn/nnews/3865.htm
- http://m.3g.oexnr.cn/nnews/4028.htm
- http://m.3g.oexnr.cn/nnews/1777604.htm
- http://m.3g.oexnr.cn/nnews/9666.htm
- http://m.3g.oexnr.cn/nnews/436994.htm
- http://m.3g.oexnr.cn/nnews/32313.htm
- http://m.3g.oexnr.cn/nnews/1244.htm
- http://m.3g.oexnr.cn/nnews/0297614.htm
- http://m.3g.oexnr.cn/nnews/7053501.htm
- http://m.3g.oexnr.cn/nnews/08054.htm
- http://m.3g.oexnr.cn/nnews/02337.htm
- http://m.3g.oexnr.cn/nnews/4321.htm
- http://m.3g.oexnr.cn/nnews/288555.htm
- http://m.3g.oexnr.cn/nnews/9007344.htm
- http://m.3g.oexnr.cn/nnews/869003.htm
- http://m.3g.oexnr.cn/nnews/58446.htm
- http://m.3g.oexnr.cn/nnews/9344.htm
- http://m.3g.oexnr.cn/nnews/96099.htm
- http://m.3g.oexnr.cn/nnews/47230.htm
- http://m.3g.oexnr.cn/nnews/5434.htm
- http://m.3g.oexnr.cn/nnews/6510690.htm
- http://m.3g.oexnr.cn/nnews/9553.htm
- http://m.3g.oexnr.cn/nnews/0132986.htm
- http://m.3g.oexnr.cn/nnews/203915.htm
- http://m.3g.oexnr.cn/nnews/4399888.htm
- http://m.3g.oexnr.cn/nnews/3481378.htm
- http://m.3g.oexnr.cn/nnews/7437.htm
- http://m.3g.oexnr.cn/nnews/17828.htm
- http://m.3g.oexnr.cn/nnews/60101.htm
- http://m.3g.oexnr.cn/nnews/9978026.htm
- http://m.3g.oexnr.cn/nnews/68784.htm
- http://m.3g.oexnr.cn/nnews/5350471.htm
- http://m.3g.oexnr.cn/nnews/4155.htm
- http://m.3g.oexnr.cn/nnews/68524.htm
- http://m.3g.oexnr.cn/nnews/38586.htm
- http://m.3g.oexnr.cn/nnews/612844.htm
- http://m.3g.oexnr.cn/nnews/50803.htm
- http://m.3g.oexnr.cn/nnews/7612454.htm
- http://m.3g.oexnr.cn/nnews/8700.htm
- http://m.3g.oexnr.cn/nnews/0525471.htm
- http://m.3g.oexnr.cn/nnews/9620194.htm
- http://m.3g.oexnr.cn/nnews/283997.htm
- http://m.3g.oexnr.cn/nnews/834496.htm
- http://m.3g.oexnr.cn/nnews/06098.htm
- http://m.3g.oexnr.cn/nnews/0626.htm
- http://m.3g.oexnr.cn/nnews/60985.htm
- http://m.3g.oexnr.cn/nnews/4448184.htm
- http://m.3g.oexnr.cn/nnews/511458.htm
- http://m.3g.oexnr.cn/nnews/942829.htm
- http://m.3g.oexnr.cn/nnews/76246.htm
- http://m.3g.oexnr.cn/nnews/6107.htm
- http://m.3g.oexnr.cn/nnews/2089982.htm
- http://m.3g.oexnr.cn/nnews/419556.htm
- http://m.3g.oexnr.cn/nnews/9016965.htm
- http://m.3g.oexnr.cn/nnews/558134.htm
- http://m.3g.oexnr.cn/nnews/44456.htm
- http://m.3g.oexnr.cn/nnews/96340.htm
- http://m.3g.oexnr.cn/nnews/28135.htm
- http://m.3g.oexnr.cn/nnews/0311.htm
- http://m.3g.oexnr.cn/nnews/27363.htm
- http://m.3g.oexnr.cn/nnews/9581379.htm
- http://m.3g.oexnr.cn/nnews/3300802.htm
- http://m.3g.oexnr.cn/nnews/54891.htm
- http://m.3g.oexnr.cn/nnews/9587179.htm
- http://m.3g.oexnr.cn/nnews/9252.htm
- http://m.3g.oexnr.cn/nnews/736933.htm
- http://m.3g.oexnr.cn/nnews/808278.htm
- http://m.3g.oexnr.cn/nnews/9909.htm
- http://m.3g.oexnr.cn/nnews/8697.htm
- http://m.3g.oexnr.cn/nnews/057044.htm
- http://m.3g.oexnr.cn/nnews/00489.htm
- http://m.3g.oexnr.cn/nnews/1814980.htm
- http://m.3g.oexnr.cn/nnews/9632855.htm
- http://m.3g.oexnr.cn/nnews/9954.htm
- http://m.3g.oexnr.cn/nnews/655804.htm
- http://m.3g.oexnr.cn/nnews/6825.htm
- http://m.3g.oexnr.cn/nnews/233097.htm
- http://m.3g.oexnr.cn/nnews/2514.htm
- http://m.3g.oexnr.cn/nnews/283809.htm
- http://m.3g.oexnr.cn/nnews/25546.htm
- http://m.3g.oexnr.cn/nnews/841640.htm
- http://m.3g.oexnr.cn/nnews/5331.htm
- http://m.3g.oexnr.cn/nnews/0662726.htm
- http://m.3g.oexnr.cn/nnews/859855.htm
- http://m.3g.oexnr.cn/nnews/072024.htm
- http://m.3g.oexnr.cn/nnews/7949379.htm
- http://m.3g.oexnr.cn/nnews/7879247.htm
- http://m.3g.oexnr.cn/nnews/6774.htm
- http://m.3g.oexnr.cn/nnews/3749120.htm
- http://m.3g.oexnr.cn/nnews/77478.htm
- http://m.3g.oexnr.cn/nnews/9585.htm
- http://m.3g.oexnr.cn/nnews/445123.htm
- http://m.3g.oexnr.cn/nnews/53820.htm
- http://m.3g.oexnr.cn/nnews/69052.htm
- http://m.3g.oexnr.cn/nnews/8810.htm
- http://m.3g.oexnr.cn/nnews/889770.htm
- http://m.3g.oexnr.cn/nnews/25366.htm
- http://m.3g.oexnr.cn/nnews/98576.htm
- http://m.3g.oexnr.cn/nnews/3956449.htm
- http://m.3g.oexnr.cn/nnews/298669.htm
- http://m.3g.oexnr.cn/nnews/170320.htm
- http://m.3g.oexnr.cn/nnews/10619.htm
- http://m.3g.oexnr.cn/nnews/0007090.htm
- http://m.3g.oexnr.cn/nnews/60323.htm
- http://m.3g.oexnr.cn/nnews/7301.htm
- http://m.3g.oexnr.cn/nnews/3972.htm
- http://m.3g.oexnr.cn/nnews/9324164.htm
- http://m.3g.oexnr.cn/nnews/741947.htm
- http://m.3g.oexnr.cn/nnews/3875955.htm
- http://m.3g.oexnr.cn/nnews/364192.htm
- http://m.3g.oexnr.cn/nnews/59831.htm
- http://m.3g.oexnr.cn/nnews/7730.htm
- http://m.3g.oexnr.cn/nnews/202608.htm
- http://m.3g.oexnr.cn/nnews/93750.htm
- http://m.3g.oexnr.cn/nnews/062789.htm
- http://m.3g.oexnr.cn/nnews/9043.htm
- http://m.3g.oexnr.cn/nnews/881076.htm
- http://m.3g.oexnr.cn/nnews/3384897.htm
- http://m.3g.oexnr.cn/nnews/53706.htm
- http://m.3g.oexnr.cn/nnews/82405.htm
- http://m.3g.oexnr.cn/nnews/788167.htm
- http://m.3g.oexnr.cn/nnews/711104.htm
- http://m.3g.oexnr.cn/nnews/29619.htm
- http://m.3g.oexnr.cn/nnews/871619.htm
- http://m.3g.oexnr.cn/nnews/3395.htm
- http://m.3g.oexnr.cn/nnews/3694.htm
- http://m.3g.oexnr.cn/nnews/2823144.htm
- http://m.3g.oexnr.cn/nnews/1193495.htm
- http://m.3g.oexnr.cn/nnews/726314.htm
- http://m.3g.oexnr.cn/nnews/0709337.htm
- http://m.3g.oexnr.cn/nnews/77976.htm
- http://m.3g.oexnr.cn/nnews/5703.htm
- http://m.3g.oexnr.cn/nnews/35886.htm
- http://m.3g.oexnr.cn/nnews/8599002.htm
- http://m.3g.oexnr.cn/nnews/574539.htm
- http://m.3g.oexnr.cn/nnews/41301.htm
- http://m.3g.oexnr.cn/nnews/897217.htm
- http://m.3g.oexnr.cn/nnews/747168.htm
- http://m.3g.oexnr.cn/nnews/7524.htm
- http://m.3g.oexnr.cn/nnews/156817.htm
- http://m.3g.oexnr.cn/nnews/3321.htm
- http://m.3g.oexnr.cn/nnews/32843.htm
- http://m.3g.oexnr.cn/nnews/5492699.htm
- http://m.3g.oexnr.cn/nnews/7401.htm
- http://m.3g.oexnr.cn/nnews/8075841.htm
- http://m.3g.oexnr.cn/nnews/2800509.htm
- http://m.3g.oexnr.cn/nnews/847707.htm
- http://m.3g.oexnr.cn/nnews/21990.htm
- http://m.3g.oexnr.cn/nnews/3856438.htm
- http://m.3g.oexnr.cn/nnews/7382592.htm
- http://m.3g.oexnr.cn/nnews/6286169.htm
- http://m.3g.oexnr.cn/nnews/6226013.htm
- http://m.3g.oexnr.cn/nnews/53364.htm
- http://m.3g.oexnr.cn/nnews/01007.htm
- http://m.3g.oexnr.cn/nnews/6979535.htm
- http://m.3g.oexnr.cn/nnews/96844.htm
- http://m.3g.oexnr.cn/nnews/62717.htm
- http://m.3g.oexnr.cn/nnews/3408.htm
- http://m.3g.oexnr.cn/nnews/3989142.htm
- http://m.3g.oexnr.cn/nnews/2412.htm
- http://m.3g.oexnr.cn/nnews/4739.htm
- http://m.3g.oexnr.cn/nnews/305361.htm
- http://m.3g.oexnr.cn/nnews/1465523.htm
- http://m.3g.oexnr.cn/nnews/0320.htm
- http://m.3g.oexnr.cn/nnews/1893.htm
- http://m.3g.oexnr.cn/nnews/2945231.htm
- http://m.3g.oexnr.cn/nnews/9858.htm
- http://m.3g.oexnr.cn/nnews/3923844.htm
- http://m.3g.oexnr.cn/nnews/674711.htm
- http://m.3g.oexnr.cn/nnews/118857.htm
- http://m.3g.oexnr.cn/nnews/702664.htm
- http://m.3g.oexnr.cn/nnews/7322.htm
- http://m.3g.oexnr.cn/nnews/5300.htm
- http://m.3g.oexnr.cn/nnews/0167054.htm
- http://m.3g.oexnr.cn/nnews/1905.htm
- http://m.3g.oexnr.cn/nnews/64143.htm
- http://m.3g.oexnr.cn/nnews/7992603.htm
- http://m.3g.oexnr.cn/nnews/1131.htm
- http://m.3g.oexnr.cn/nnews/8478.htm
- http://m.3g.oexnr.cn/nnews/11766.htm
- http://m.3g.oexnr.cn/nnews/5155.htm
- http://m.3g.oexnr.cn/nnews/72283.htm
- http://m.3g.oexnr.cn/nnews/71295.htm
- http://m.3g.oexnr.cn/nnews/320406.htm
- http://m.3g.oexnr.cn/nnews/837987.htm
- http://m.3g.oexnr.cn/nnews/22446.htm
- http://m.3g.oexnr.cn/nnews/6522113.htm
- http://m.3g.oexnr.cn/nnews/380774.htm
- http://m.3g.oexnr.cn/nnews/99920.htm
- http://m.3g.oexnr.cn/nnews/46819.htm
- http://m.3g.oexnr.cn/nnews/9222.htm
- http://m.3g.oexnr.cn/nnews/9188130.htm
- http://m.3g.oexnr.cn/nnews/7461068.htm
- http://m.3g.oexnr.cn/nnews/519374.htm
- http://m.3g.oexnr.cn/nnews/0941638.htm
- http://m.3g.oexnr.cn/nnews/0100335.htm
- http://m.3g.oexnr.cn/nnews/33228.htm
- http://m.3g.oexnr.cn/nnews/481249.htm
- http://m.3g.oexnr.cn/nnews/4749.htm
- http://m.3g.oexnr.cn/nnews/04376.htm
- http://m.3g.oexnr.cn/nnews/777470.htm
- http://m.3g.oexnr.cn/nnews/1567850.htm
- http://m.3g.oexnr.cn/nnews/7828716.htm
- http://m.3g.oexnr.cn/nnews/2237.htm
- http://m.3g.oexnr.cn/nnews/3006827.htm
- http://m.3g.oexnr.cn/nnews/4654070.htm
- http://m.3g.oexnr.cn/nnews/52186.htm
- http://m.3g.oexnr.cn/nnews/7060.htm
- http://m.3g.oexnr.cn/nnews/0375.htm

## 项目结构

```
newslink-navigator/
├── app/                            # 主应用模块
│   ├── __init__.py                 # 应用工厂函数，创建 Flask 实例
│   ├── routes/                     # 路由控制器层
│   │   ├── api.py                  # RESTful API 端点实现（查询、新增、更新、删除）
│   │   └── web.py                  # Web 界面路由（仪表盘、列表、详情页）
│   ├── models/                     # 数据模型与 ORM 映射
│   │   ├── link.py                 # Link 模型定义，包含字段、索引和 FTS5 映射
│   │   ├── tag.py                  # Tag 模型定义，支持多对多关联
│   │   └── task.py                 # 定时任务模型，存储 cron 配置和运行日志
│   ├── services/                   # 业务逻辑服务层
│   │   ├── fetcher.py              # 元信息抓取服务（HTTP 请求、HTML 解析）
│   │   ├── health.py               # 健康检查服务（批量检测、状态更新）
│   │   └── scheduler.py            # 定时任务调度服务（基于 apscheduler）
│   └── utils/                      # 工具函数集合
│       ├── validators.py           # URL 格式校验、域名白名单检查
│       └── exporters.py            # 数据导出器（JSON、CSV、Markdown 格式）
├── scripts/                        # 独立运维脚本
│   ├── init_db.py                  # 数据库初始化脚本（建表、创建索引）
│   ├── import_links.py             # 批量导入脚本，支持多种输入格式
│   └── export_links.py             # 批量导出脚本，支持过滤条件和输出格式
├── tests/                          # 测试用例目录
│   ├── unit/                       # 单元测试（模型、工具函数）
│   └── integration/                # 集成测试（API 端点、服务调用）
├── docs/                           # 文档源文件（Markdown 格式）
│   ├── user-guide/                 # 用户指南各章节
│   ├── ops-guide/                  # 运维手册各章节
│   └── api-reference/              # API 参考文档（由 OpenAPI 生成）
├── data/                           # 数据存储目录
│   └── newslink.db                 # SQLite 数据库文件（默认路径）
├── logs/                           # 日志文件存储目录
│   └── app.log                     # 应用运行日志（按天轮转）
├── config.py                       # 全局配置文件（数据库路径、超时设置、调度参数）
├── requirements.txt                # 生产环境依赖列表
├── requirements-dev.txt            # 开发环境额外依赖（测试、代码检查工具）
├── app.py                          # 应用入口文件（开发服务器启动脚本）
├── setup.py                        # 打包安装配置文件
└── README.md                       # 项目说明文档（本文件）
```

## 贡献指南

我们欢迎并鼓励社区贡献。无论是报告问题、提交代码还是完善文档，您的参与都将使项目变得更好。

**提交问题报告** 在 GitHub Issues 中提交新问题时，请使用提供的模板，清晰描述复现步骤、预期行为与实际行为，并附上相关的日志片段或截图。对于链接处理相关的异常，请提供原始 URL 以及您所使用的配置参数。

**实现新功能或修复缺陷** 在开始较大规模的代码修改前，建议先在 Issues 中创建讨论帖，与维护者沟通设计思路，避免重复劳动或方向偏差。对于缺陷修复，请先编写能够复现问题的测试用例，再着手修改代码，确保修复后测试通过。

**遵循代码规范** 项目使用 Black 作为代码格式化工具，行宽限制为 88 字符。提交前请运行 `black .` 和 `pytest tests/` 确保格式正确且所有测试通过。Commit 信息请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`refactor:` 等前缀。

**完善文档与示例** 如果发现文档中存在错漏或表述不清之处，欢迎提交 Pull Request 进行修正。对于新增功能，请同步更新对应的用户指南或 API 参考文档，并在 `sample_links.txt` 中添加示例数据以便其他开发者理解用法。

**参与代码审查** 活跃贡献者将被邀请参与 Pull Request 的代码审查工作，帮助维护代码质量并分享知识。审查时请保持友善和建设性，指出问题的同时给出改进建议。

## 常见问题

**导入大量链接时出现超时或内存不足错误**

批量导入操作默认每批次处理 500 条记录，若您的数据集超过 10000 条，建议使用 `--batch-size` 参数调低每批次数量（例如 200 条）。同时，元信息抓取阶段默认并发数为 10，可通过修改 `config.py` 中的 `FETCHER_CONCURRENCY` 调整并发度，避免对目标服务器造成过大压力。如果内存仍不足，考虑使用 SQLite 的 WAL 模式并定期执行 `VACUUM` 命令回收空间。

**健康检查任务总是报告大量链接超时**

健康检查的超时阈值默认为 10 秒，对于响应较慢的移动端新闻源，可适当调整 `config.py` 中的 `HEALTH_CHECK_TIMEOUT` 至 20 或 30 秒。此外，部分新闻站点可能对频繁请求有反爬限制，建议在 `config.py` 中配置 `REQUEST_HEADERS` 模拟移动端 User-Agent，并启用 `HEALTH_CHECK_DELAY` 在每次请求间增加随机延迟。

**如何迁移数据库到 PostgreSQL 或其他关系型数据库**

项目默认使用 SQLite 以降低部署门槛，但若您需要多用户并发写入或更高级的权限管理，可通过修改 `config.py` 中的 `DATABASE_URL` 切换至 PostgreSQL。注意 PostgreSQL 需要启用 `pg_trgm` 扩展以替代 SQLite 的 FTS5 全文搜索功能，相关迁移脚本位于 `scripts/migrate

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
