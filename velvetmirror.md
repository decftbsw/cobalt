# WebLink Navigator

WebLink Navigator 是一个面向技术文档聚合与外部资源导航的开源工具，专注于将大量零散的链接资源转化为可检索、可分类、可维护的结构化知识库。该项目主要服务于需要频繁查阅外部技术资料、博客文章及行业动态的开发者、技术写作人员与研究机构。通过提供统一的索引框架与轻量级元数据管理能力，WebLink Navigator 帮助用户从海量 URL 中快速定位有价值的信息，减少重复检索成本，并支持团队内共享资源池的构建。

## 功能概览

**批量链接导入与解析**：支持从纯文本、CSV 及 Markdown 列表中批量导入 URL，自动提取域名、路径层级与文件扩展名，生成基础索引记录。

**多维度标签分类**：允许用户为每个链接赋予自定义标签（如「前端」「后端」「DevOps」「论文」「教程」），并支持标签层级嵌套与别名管理。

**全文检索与过滤**：基于 SQLite 或 Elasticsearch 后端，提供对 URL、标题、描述、标签及注释字段的全文检索，同时支持按域名、文件类型、时间范围等条件过滤。

**定期可用性检测**：内置链接健康检查模块，可配置定时任务（每日/每周）对已收录链接发起 HTTP HEAD 请求，标记失效链接并生成报告。

**元数据自动补全**：对缺失标题或描述的链接，自动抓取目标页面的 title 与 meta description 字段，减少手动录入负担。

**数据导入导出**：支持将整个链接库导出为 JSON、YAML 或标准 HTML 书签格式，方便迁移至其他工具或进行离线备份。

**访问统计与热度排序**：记录每个链接的点击次数与最近访问时间，支持按热度、添加时间或字母序排列，辅助用户识别高频资源。

**协同编辑与版本记录**：提供基于操作的简单日志系统，记录每条链接的创建者、修改时间与变更历史，适用于多人维护场景。

## 应用场景

技术团队内部知识库构建：开发团队可将日常调研中发现的优秀博客、官方文档、开源仓库及问题排查帖子统一收录至 WebLink Navigator，并按项目或技术栈分类，新成员入职时可快速了解团队常用资源池。

个人技术阅读工作流管理：技术爱好者订阅大量 RSS 或社交媒体信息流后，可使用本工具将值得深读的文章链接保存下来，添加阅读优先级与笔记，形成个人阅读队列与知识沉淀。

技术文档撰写参考索引：当撰写技术方案、架构设计文档或技术博客时，作者可预先将需要引用的外部资料录入系统，通过标签与检索功能快速组织参考文献列表，确保引用准确性与可追溯性。

开源项目外部依赖追踪：开源项目维护者可将项目依赖的第三方库文档、社区论坛、问题跟踪系统等链接集中管理，便于贡献者快速找到相关资源，降低参与门槛。

## 快速开始

以下操作基于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地数据库（默认使用 SQLite）
python scripts/init_db.py --db-path ./data/links.db

# 导入示例链接列表（支持 CSV / 纯文本 / Markdown）
python scripts/import_links.py --input ./samples/sample_links.txt --tags "sample,test"

# 启动 Web 服务（默认监听 127.0.0.1:8080）
python app.py run --host 127.0.0.1 --port 8080
```

访问 http://127.0.0.1:8080 即可进入检索与管理工作台。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 或 3.11 以获得更好性能 |
| SQLite | 3.28 及以上 | 默认元数据存储引擎，支持 JSON 扩展和全文搜索（FTS5） |
| requests | 2.28.0 及以上 | 用于 HTTP 请求发送，实现链接健康检查与元数据抓取 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于提取页面标题和描述信息 |
| Flask | 2.2.0 及以上 | 可选 Web 界面依赖，若不使用图形界面可仅安装核心库 |
| elasticsearch | 8.0.0 及以上 | 可选，用于替换 SQLite 实现更高性能的全文检索（生产环境推荐） |
| pytest | 7.0.0 及以上 | 开发测试依赖，运行单元测试与集成测试所需 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide/ | 如何添加链接、管理标签、执行检索、导入导出数据及配置健康检查策略 |
| 管理员指南 | docs/admin-guide/ | 如何部署生产环境、配置 Elasticsearch 后端、调优检索性能及备份恢复数据库 |
| 开发者文档 | docs/developer-guide/ | 项目整体架构说明、核心模块接口定义、自定义解析器扩展方法及提交补丁流程 |
| API 参考 | docs/api-reference/ | RESTful API 端点列表、请求参数格式、返回数据结构及错误码说明 |

## 资源列表

- http://m.blog.bwbkj.cn/snews/1091.htm
- http://m.blog.bwbkj.cn/snews/57028.htm
- http://m.blog.bwbkj.cn/snews/77465.htm
- http://m.blog.bwbkj.cn/snews/071282.htm
- http://m.blog.bwbkj.cn/snews/9833635.htm
- http://m.blog.bwbkj.cn/snews/264520.htm
- http://m.blog.bwbkj.cn/snews/9285976.htm
- http://m.blog.bwbkj.cn/snews/0150577.htm
- http://m.blog.bwbkj.cn/snews/48824.htm
- http://m.blog.bwbkj.cn/snews/386444.htm
- http://m.blog.bwbkj.cn/snews/6891669.htm
- http://m.blog.bwbkj.cn/snews/0680.htm
- http://m.blog.bwbkj.cn/snews/948519.htm
- http://m.blog.bwbkj.cn/snews/9430259.htm
- http://m.blog.bwbkj.cn/snews/1644924.htm
- http://m.blog.bwbkj.cn/snews/952507.htm
- http://m.blog.bwbkj.cn/snews/60840.htm
- http://m.blog.bwbkj.cn/snews/715750.htm
- http://m.blog.bwbkj.cn/snews/68135.htm
- http://m.blog.bwbkj.cn/snews/97765.htm
- http://m.blog.bwbkj.cn/snews/111629.htm
- http://m.blog.bwbkj.cn/snews/6149770.htm
- http://m.blog.bwbkj.cn/snews/0866.htm
- http://m.blog.bwbkj.cn/snews/7590.htm
- http://m.blog.bwbkj.cn/snews/076925.htm
- http://m.blog.bwbkj.cn/snews/566624.htm
- http://m.blog.bwbkj.cn/snews/7455.htm
- http://m.blog.bwbkj.cn/snews/922184.htm
- http://m.blog.bwbkj.cn/snews/9233975.htm
- http://m.blog.bwbkj.cn/snews/376111.htm
- http://m.blog.bwbkj.cn/snews/7804.htm
- http://m.blog.bwbkj.cn/snews/679683.htm
- http://m.blog.bwbkj.cn/snews/393188.htm
- http://m.blog.bwbkj.cn/snews/7474.htm
- http://m.blog.bwbkj.cn/snews/3737680.htm
- http://m.blog.bwbkj.cn/snews/14254.htm
- http://m.blog.bwbkj.cn/snews/3488.htm
- http://m.blog.bwbkj.cn/snews/4405703.htm
- http://m.blog.bwbkj.cn/snews/35293.htm
- http://m.blog.bwbkj.cn/snews/61474.htm
- http://m.blog.bwbkj.cn/snews/81672.htm
- http://m.blog.bwbkj.cn/snews/9096446.htm
- http://m.blog.bwbkj.cn/snews/3226.htm
- http://m.blog.bwbkj.cn/snews/095245.htm
- http://m.blog.bwbkj.cn/snews/73781.htm
- http://m.blog.bwbkj.cn/snews/0516429.htm
- http://m.blog.bwbkj.cn/snews/387941.htm
- http://m.blog.bwbkj.cn/snews/61179.htm
- http://m.blog.bwbkj.cn/snews/87887.htm
- http://m.blog.bwbkj.cn/snews/97475.htm
- http://m.blog.bwbkj.cn/snews/7110546.htm
- http://m.blog.bwbkj.cn/snews/84252.htm
- http://m.blog.bwbkj.cn/snews/73048.htm
- http://m.blog.bwbkj.cn/snews/3420.htm
- http://m.blog.bwbkj.cn/snews/7541.htm
- http://m.blog.bwbkj.cn/snews/39959.htm
- http://m.blog.bwbkj.cn/snews/0673477.htm
- http://m.blog.bwbkj.cn/snews/50969.htm
- http://m.blog.bwbkj.cn/snews/35921.htm
- http://m.blog.bwbkj.cn/snews/8828.htm
- http://m.blog.bwbkj.cn/snews/767662.htm
- http://m.blog.bwbkj.cn/snews/2316707.htm
- http://m.blog.bwbkj.cn/snews/524434.htm
- http://m.blog.bwbkj.cn/snews/0198133.htm
- http://m.blog.bwbkj.cn/snews/7071.htm
- http://m.blog.bwbkj.cn/snews/103397.htm
- http://m.blog.bwbkj.cn/snews/6213.htm
- http://m.blog.bwbkj.cn/snews/0981668.htm
- http://m.blog.bwbkj.cn/snews/9517959.htm
- http://m.blog.bwbkj.cn/snews/232769.htm
- http://m.blog.bwbkj.cn/snews/07508.htm
- http://m.blog.bwbkj.cn/snews/9084966.htm
- http://m.blog.bwbkj.cn/snews/67359.htm
- http://m.blog.bwbkj.cn/snews/67005.htm
- http://m.blog.bwbkj.cn/snews/1204.htm
- http://m.blog.bwbkj.cn/snews/81904.htm
- http://m.blog.bwbkj.cn/snews/5527740.htm
- http://m.blog.bwbkj.cn/snews/0493.htm
- http://m.blog.bwbkj.cn/snews/867153.htm
- http://m.blog.bwbkj.cn/snews/69553.htm
- http://m.blog.bwbkj.cn/snews/8392335.htm
- http://m.blog.bwbkj.cn/snews/68512.htm
- http://m.blog.bwbkj.cn/snews/3808538.htm
- http://m.blog.bwbkj.cn/snews/6637.htm
- http://m.blog.bwbkj.cn/snews/6644895.htm
- http://m.blog.bwbkj.cn/snews/37929.htm
- http://m.blog.bwbkj.cn/snews/803249.htm
- http://m.blog.bwbkj.cn/snews/68391.htm
- http://m.blog.bwbkj.cn/snews/399388.htm
- http://m.blog.bwbkj.cn/snews/3495.htm
- http://m.blog.bwbkj.cn/snews/863897.htm
- http://m.blog.bwbkj.cn/snews/0552303.htm
- http://m.blog.bwbkj.cn/snews/66447.htm
- http://m.blog.bwbkj.cn/snews/6185.htm
- http://m.blog.bwbkj.cn/snews/24706.htm
- http://m.blog.bwbkj.cn/snews/210764.htm
- http://m.blog.bwbkj.cn/snews/3061392.htm
- http://m.blog.bwbkj.cn/snews/0644212.htm
- http://m.blog.bwbkj.cn/snews/175492.htm
- http://m.blog.bwbkj.cn/snews/9958916.htm
- http://m.blog.bwbkj.cn/snews/56002.htm
- http://m.blog.bwbkj.cn/snews/7400.htm
- http://m.blog.bwbkj.cn/snews/28092.htm
- http://m.blog.bwbkj.cn/snews/876066.htm
- http://m.blog.bwbkj.cn/snews/406262.htm
- http://m.blog.bwbkj.cn/snews/94066.htm
- http://m.blog.bwbkj.cn/snews/490331.htm
- http://m.blog.bwbkj.cn/snews/8852.htm
- http://m.blog.bwbkj.cn/snews/8860779.htm
- http://m.blog.bwbkj.cn/snews/7622999.htm
- http://m.blog.bwbkj.cn/snews/0836.htm
- http://m.blog.bwbkj.cn/snews/74891.htm
- http://m.blog.bwbkj.cn/snews/7367484.htm
- http://m.blog.bwbkj.cn/snews/7106.htm
- http://m.blog.bwbkj.cn/snews/6814.htm
- http://m.blog.bwbkj.cn/snews/265042.htm
- http://m.blog.bwbkj.cn/snews/3601.htm
- http://m.blog.bwbkj.cn/snews/165642.htm
- http://m.blog.bwbkj.cn/snews/279285.htm
- http://m.blog.bwbkj.cn/snews/4385.htm
- http://m.blog.bwbkj.cn/snews/5454.htm
- http://m.blog.bwbkj.cn/snews/2489.htm
- http://m.blog.bwbkj.cn/snews/67642.htm
- http://m.blog.bwbkj.cn/snews/239150.htm
- http://m.blog.bwbkj.cn/snews/885808.htm
- http://m.blog.bwbkj.cn/snews/71319.htm
- http://m.blog.bwbkj.cn/snews/4261090.htm
- http://m.blog.bwbkj.cn/snews/338862.htm
- http://m.blog.bwbkj.cn/snews/9365288.htm
- http://m.blog.bwbkj.cn/snews/3407883.htm
- http://m.blog.bwbkj.cn/snews/6785496.htm
- http://m.blog.bwbkj.cn/snews/68739.htm
- http://m.blog.bwbkj.cn/snews/50313.htm
- http://m.blog.bwbkj.cn/snews/356034.htm
- http://m.blog.bwbkj.cn/snews/01555.htm
- http://m.blog.bwbkj.cn/snews/70140.htm
- http://m.blog.bwbkj.cn/snews/8396100.htm
- http://m.blog.bwbkj.cn/snews/1767.htm
- http://m.blog.bwbkj.cn/snews/37941.htm
- http://m.blog.bwbkj.cn/snews/7302.htm
- http://m.blog.bwbkj.cn/snews/5789407.htm
- http://m.blog.bwbkj.cn/snews/18880.htm
- http://m.blog.bwbkj.cn/snews/5416.htm
- http://m.blog.bwbkj.cn/snews/720574.htm
- http://m.blog.bwbkj.cn/snews/7191244.htm
- http://m.blog.bwbkj.cn/snews/435329.htm
- http://m.blog.bwbkj.cn/snews/2632997.htm
- http://m.blog.bwbkj.cn/snews/40242.htm
- http://m.blog.bwbkj.cn/snews/7646865.htm
- http://m.blog.bwbkj.cn/snews/0918638.htm
- http://m.blog.bwbkj.cn/snews/13044.htm
- http://m.blog.bwbkj.cn/snews/7131.htm
- http://m.blog.bwbkj.cn/snews/5737003.htm
- http://m.blog.bwbkj.cn/snews/0430377.htm
- http://m.blog.bwbkj.cn/snews/6346.htm
- http://m.blog.bwbkj.cn/snews/0311410.htm
- http://m.blog.bwbkj.cn/snews/5065458.htm
- http://m.blog.bwbkj.cn/snews/6546.htm
- http://m.blog.bwbkj.cn/snews/926824.htm
- http://m.blog.bwbkj.cn/snews/94445.htm
- http://m.blog.bwbkj.cn/snews/13550.htm
- http://m.blog.bwbkj.cn/snews/520182.htm
- http://m.blog.bwbkj.cn/snews/717867.htm
- http://m.blog.bwbkj.cn/snews/413901.htm
- http://m.blog.bwbkj.cn/snews/4058684.htm
- http://m.blog.bwbkj.cn/snews/1370.htm
- http://m.blog.bwbkj.cn/snews/8364649.htm
- http://m.blog.bwbkj.cn/snews/9211.htm
- http://m.blog.bwbkj.cn/snews/3993.htm
- http://m.blog.bwbkj.cn/snews/683596.htm
- http://m.blog.bwbkj.cn/snews/3374.htm
- http://m.blog.bwbkj.cn/snews/6859941.htm
- http://m.blog.bwbkj.cn/snews/90859.htm
- http://m.blog.bwbkj.cn/snews/1857.htm
- http://m.blog.bwbkj.cn/snews/9584626.htm
- http://m.blog.bwbkj.cn/snews/6067.htm
- http://m.blog.bwbkj.cn/snews/4466697.htm
- http://m.blog.bwbkj.cn/snews/922256.htm
- http://m.blog.bwbkj.cn/snews/56878.htm
- http://m.blog.bwbkj.cn/snews/301002.htm
- http://m.blog.bwbkj.cn/snews/645462.htm
- http://m.blog.bwbkj.cn/snews/594446.htm
- http://m.blog.bwbkj.cn/snews/71025.htm
- http://m.blog.bwbkj.cn/snews/1067.htm
- http://m.blog.bwbkj.cn/snews/0056470.htm
- http://m.blog.bwbkj.cn/snews/1413.htm
- http://m.blog.bwbkj.cn/snews/6257661.htm
- http://m.blog.bwbkj.cn/snews/0739032.htm
- http://m.blog.bwbkj.cn/snews/6000.htm
- http://m.blog.bwbkj.cn/snews/15496.htm
- http://m.blog.bwbkj.cn/snews/9994280.htm
- http://m.blog.bwbkj.cn/snews/7879.htm
- http://m.blog.bwbkj.cn/snews/38798.htm
- http://m.blog.bwbkj.cn/snews/084794.htm
- http://m.blog.bwbkj.cn/snews/036317.htm
- http://m.blog.bwbkj.cn/snews/76992.htm
- http://m.blog.bwbkj.cn/snews/00417.htm
- http://m.blog.bwbkj.cn/snews/81488.htm
- http://m.blog.bwbkj.cn/snews/44640.htm
- http://m.blog.bwbkj.cn/snews/8286360.htm
- http://m.blog.bwbkj.cn/snews/1725326.htm
- http://m.blog.bwbkj.cn/snews/2975.htm
- http://m.blog.bwbkj.cn/snews/8619436.htm
- http://m.blog.bwbkj.cn/snews/7095.htm
- http://m.blog.bwbkj.cn/snews/44774.htm
- http://m.blog.bwbkj.cn/snews/8927.htm
- http://m.blog.bwbkj.cn/snews/055270.htm
- http://m.blog.bwbkj.cn/snews/3855835.htm
- http://m.blog.bwbkj.cn/snews/8545963.htm
- http://m.blog.bwbkj.cn/snews/1965574.htm
- http://m.blog.bwbkj.cn/snews/3136365.htm
- http://m.blog.bwbkj.cn/snews/138589.htm
- http://m.blog.bwbkj.cn/snews/58397.htm
- http://m.blog.bwbkj.cn/snews/3622558.htm
- http://m.blog.bwbkj.cn/snews/80001.htm
- http://m.blog.bwbkj.cn/snews/8008.htm
- http://m.blog.bwbkj.cn/snews/31470.htm
- http://m.blog.bwbkj.cn/snews/577784.htm
- http://m.blog.bwbkj.cn/snews/21882.htm
- http://m.blog.bwbkj.cn/snews/876936.htm
- http://m.blog.bwbkj.cn/snews/523983.htm
- http://m.blog.bwbkj.cn/snews/38189.htm
- http://m.blog.bwbkj.cn/snews/362031.htm
- http://m.blog.bwbkj.cn/snews/845320.htm
- http://m.blog.bwbkj.cn/snews/086725.htm
- http://m.blog.bwbkj.cn/snews/483770.htm
- http://m.blog.bwbkj.cn/snews/7534267.htm
- http://m.blog.bwbkj.cn/snews/759613.htm
- http://m.blog.bwbkj.cn/snews/7270534.htm
- http://m.blog.bwbkj.cn/snews/4488966.htm
- http://m.blog.bwbkj.cn/snews/74851.htm
- http://m.blog.bwbkj.cn/snews/20849.htm
- http://m.blog.bwbkj.cn/snews/4289598.htm
- http://m.blog.bwbkj.cn/snews/698455.htm
- http://m.blog.bwbkj.cn/snews/960642.htm
- http://m.blog.bwbkj.cn/snews/06985.htm
- http://m.blog.bwbkj.cn/snews/02492.htm
- http://m.blog.bwbkj.cn/snews/89211.htm
- http://m.blog.bwbkj.cn/snews/00230.htm
- http://m.blog.bwbkj.cn/snews/3419.htm
- http://m.blog.bwbkj.cn/snews/7824.htm
- http://m.blog.bwbkj.cn/snews/534256.htm
- http://m.blog.bwbkj.cn/snews/4232.htm
- http://m.blog.bwbkj.cn/snews/326139.htm
- http://m.blog.bwbkj.cn/snews/38310.htm
- http://m.blog.bwbkj.cn/snews/097808.htm
- http://m.blog.bwbkj.cn/snews/123362.htm
- http://m.blog.bwbkj.cn/snews/2122013.htm
- http://m.blog.bwbkj.cn/snews/00229.htm
- http://m.blog.bwbkj.cn/snews/095050.htm
- http://m.blog.bwbkj.cn/snews/1219.htm
- http://m.blog.bwbkj.cn/snews/40990.htm
- http://m.blog.bwbkj.cn/snews/7685.htm
- http://m.blog.bwbkj.cn/snews/185656.htm
- http://m.blog.bwbkj.cn/snews/1027.htm
- http://m.blog.bwbkj.cn/snews/3722.htm
- http://m.blog.bwbkj.cn/snews/1424.htm
- http://m.blog.bwbkj.cn/snews/42785.htm
- http://m.blog.bwbkj.cn/snews/634648.htm
- http://m.blog.bwbkj.cn/snews/85319.htm
- http://m.blog.bwbkj.cn/snews/685056.htm
- http://m.blog.bwbkj.cn/snews/7924095.htm
- http://m.blog.bwbkj.cn/snews/3599075.htm
- http://m.blog.bwbkj.cn/snews/8965.htm
- http://m.blog.bwbkj.cn/snews/49218.htm
- http://m.blog.bwbkj.cn/snews/46946.htm
- http://m.blog.bwbkj.cn/snews/9024.htm
- http://m.blog.bwbkj.cn/snews/8977.htm
- http://m.blog.bwbkj.cn/snews/9791718.htm
- http://m.blog.bwbkj.cn/snews/8313439.htm
- http://m.blog.bwbkj.cn/snews/509119.htm
- http://m.blog.bwbkj.cn/snews/007586.htm
- http://m.blog.bwbkj.cn/snews/6005276.htm
- http://m.blog.bwbkj.cn/snews/1073971.htm
- http://m.blog.bwbkj.cn/snews/252364.htm
- http://m.blog.bwbkj.cn/snews/6373669.htm
- http://m.blog.bwbkj.cn/snews/6156.htm
- http://m.blog.bwbkj.cn/snews/6373063.htm
- http://m.blog.bwbkj.cn/snews/63980.htm
- http://m.blog.bwbkj.cn/snews/48312.htm
- http://m.blog.bwbkj.cn/snews/2918900.htm
- http://m.blog.bwbkj.cn/snews/703947.htm
- http://m.blog.bwbkj.cn/snews/55439.htm
- http://m.blog.bwbkj.cn/snews/62340.htm
- http://m.blog.bwbkj.cn/snews/0360065.htm
- http://m.blog.bwbkj.cn/snews/5445.htm
- http://m.blog.bwbkj.cn/snews/2478971.htm
- http://m.blog.bwbkj.cn/snews/549878.htm
- http://m.blog.bwbkj.cn/snews/9299447.htm
- http://m.blog.bwbkj.cn/snews/8801452.htm
- http://m.blog.bwbkj.cn/snews/67362.htm
- http://m.blog.bwbkj.cn/snews/94560.htm
- http://m.blog.bwbkj.cn/snews/408168.htm
- http://m.blog.bwbkj.cn/snews/028511.htm
- http://m.blog.bwbkj.cn/snews/17832.htm
- http://m.blog.bwbkj.cn/snews/7022953.htm
- http://m.blog.bwbkj.cn/snews/50677.htm
- http://m.blog.bwbkj.cn/snews/4006.htm
- http://m.blog.bwbkj.cn/snews/422291.htm
- http://m.blog.bwbkj.cn/snews/0027366.htm

## 项目结构

```
weblink-navigator/
├── app/                           # 核心应用模块
│   ├── api/                       # RESTful API 路由与控制器
│   │   ├── v1/                    # API 版本 v1 端点
│   │   │   ├── links.py           # 链接资源的 CRUD 操作
│   │   │   └── health.py          # 健康检查与状态报告接口
│   │   └── __init__.py
│   ├── core/                      # 核心业务逻辑
│   │   ├── indexer.py             # 链接索引与解析引擎
│   │   ├── checker.py             # 链接可用性检测器
│   │   ├── fetcher.py             # 页面元数据抓取器
│   │   └── tags.py                # 标签管理与层级结构处理
│   ├── storage/                   # 数据持久化层
│   │   ├── sqlite_repo.py         # SQLite 数据库操作实现
│   │   ├── es_repo.py             # Elasticsearch 适配器实现
│   │   └── models.py              # 数据模型定义（Pydantic / dataclass）
│   ├── web/                       # Web 界面（Flask）
│   │   ├── templates/             # Jinja2 模板文件
│   │   ├── static/                # CSS、JavaScript 与图片资源
│   │   └── views.py               # 页面路由与渲染逻辑
│   └── utils/                     # 通用工具函数
│       ├── url_parser.py          # URL 规范化与解析工具
│       ├── time_utils.py          # 时间戳与日期格式化辅助
│       └── logger.py              # 日志配置与封装
├── scripts/                       # 运维与辅助脚本
│   ├── init_db.py                 # 数据库初始化脚本
│   ├── import_links.py            # 批量链接导入工具
│   ├── export_links.py            # 数据导出工具（JSON/YAML/HTML）
│   └── scheduled_check.py         # 定时健康检查执行脚本
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单元测试用例
│   └── integration/               # 集成测试用例（需真实数据库）
├── docs/                          # 项目文档（见上文文档导航）
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认配置（数据库路径、超时、重试策略）
│   └── production.yaml.example    # 生产环境配置示例
├── data/                          # 本地数据存储目录（默认 SQLite 文件存放处）
├── requirements.txt               # Python 依赖列表
├── setup.py                       # 安装打包脚本
└── README.md                      # 本文件
```

## 贡献指南

首先，请阅读项目行为准则与贡献者协议。所有贡献均需通过 GitHub Pull Request 流程提交，并在提交前确保代码风格符合 PEP 8 规范且通过全部单元测试。

其次，建议在提交较大改动前先创建 Issue 进行讨论，以避免重复劳动或设计方向分歧。对于缺陷修复，请提供可复现的测试用例或详细的问题描述。

第三，代码提交应遵循 Conventional Commits 规范（如 feat: 添加批量删除接口、fix: 修复标签层级显示错误），并确保每次提交保持逻辑独立、可回溯。

第四，文档更新与代码变更同等重要。若新增功能或修改 API 行为，必须同步更新 docs/ 下对应的用户手册或 API 参考文档。鼓励补充更丰富的使用示例与故障排查章节。

最后，所有 Pull Request 需要至少一位项目维护者审查通过后方可合并。审查过程中请积极回应反馈意见，并在必要时补充测试覆盖或调整实现细节。

## 常见问题

问：项目是否支持 Windows 操作系统？部署时需要注意哪些差异？

答：WebLink Navigator 核心逻辑基于 Python 标准库与跨平台第三方库，理论上支持 Windows 10/11 及 Windows Server 2019 以上版本。但需要注意文件路径分隔符（建议使用 os.path.join 或 pathlib）、默认数据库路径权限以及定时任务配置方式（Windows 可使用任务计划程序替代 cron）。快速开始中的脚本命令需在 PowerShell 或 Git Bash 中执行，并确保 Python 已加入系统 PATH。

问：当收录的链接数量超过十万条时，SQLite 后端是否仍然适用？

答：SQLite 在单机场景下可支撑数十万条记录的常规检索与写入操作，但全文搜索性能会随数据量增长而下降。若预期链接总量超过 20 万条或并发查询 QPS 高于 50，建议切换至 Elasticsearch 后端以获得更稳定的检索性能。项目提供了 es_repo.py 适配器，可通过修改配置文件中的 storage.backend 参数切换。

问：能否将 WebLink Navigator 部署为 Docker 容器，以便快速迁移或扩缩容？

答：官方目前尚未提供预构建 Docker 镜像，但项目根目录下提供了 Dockerfile 示例（位于 contrib/docker/ 目录），用户可基于该文件自行构建镜像。构建时需注意挂载数据目录以持久化 SQLite 文件或配置文件，并暴露 8080 端口。对于使用 Elasticsearch 的场景，建议通过 docker-compose 编排 WebLink Navigator 与 Elasticsearch 服务。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:15
