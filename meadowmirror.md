# WebLink Collective Archive

WebLink Collective Archive 是一个面向技术调研、内容聚合与历史数据追溯的轻量化外链管理工具。该项目定位于个人开发者、技术内容创作者以及小型研究团队，用于对分散在网络中的各类新闻页面、技术文档与信息公告进行统一索引、本地缓存与快速检索。不同于传统的书签管理工具，WebLink Collective Archive 专注于对原始链接的元数据抽取与结构化存储，并提供基于关键词、时间范围和来源域名的多维度查询能力。

该项目解决的核心问题在于：技术资料在传播过程中经常面临链接失效、内容迁移或页面改版，导致历史参考信息难以追溯。通过将链接地址、抓取时间、页面标题、摘要信息及原始 URL 一并纳入本地 SQLite 数据库，用户可以构建一份可持续维护的外链资产清单。本项目不对原始页面内容做全文存储，仅保留必要的定位信息与状态标记，从而在轻量化与实用性之间取得平衡。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的多行 URL 列表中批量解析并入库，自动去重。

**元数据自动抽取** 对每个导入的链接发起轻量级 HEAD 请求与基础 HTML 标题解析，记录响应状态码、内容类型与最后修改时间。

**多维度检索过滤** 提供基于域名、路径关键词、导入批次、状态码范围及时间段的组合筛选条件。

**状态监控与失效检测** 支持定期重新检测已入库链接的可访问性，并更新状态标记，便于用户及时发现失效资源。

**标签与备注系统** 允许用户为每个链接添加自定义标签和备注文本，便于分类管理与上下文记录。

**数据导入导出** 支持将当前库中的链接列表导出为 JSON、CSV 或纯文本 URL 列表，便于迁移或与其他工具集成。

**批次管理** 针对大规模外链汇总场景，支持按批次编号组织链接，本项目即属于第 150/300 批。

## 应用场景

技术调研过程中的参考资料归档。当开发者围绕某一技术主题查阅大量在线文档、博客与新闻时，可使用本项目将分散的 URL 统一入库，并附加调研主题标签，后续撰写技术方案或复盘报告时可快速回溯。

历史新闻链接的可用性监控。内容运营人员或舆情分析团队可将历史发布的新闻链接导入系统，通过定时检测及时发现死链，便于进行链接修复或内容迁移决策。

多来源信息汇总与交叉验证。在研究某一事件或技术演进路径时，研究人员可从多个站点收集相关报道链接，利用本项目的标签和批次功能区分不同来源，并通过元数据比对验证信息发布时间与可靠性。

个人知识库的外链索引层。知识管理爱好者可在本地搭建轻量级外链索引，与本地 Markdown 笔记或文档系统配合，形成“笔记内容 + 外链定位”的双层信息架构。

## 快速开始

以下命令演示了如何在 Linux 或 macOS 环境下从源码启动 WebLink Collective Archive。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-collective/weblink-archive.git

# 进入项目根目录
cd weblink-archive

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地 SQLite 数据库
python scripts/init_db.py

# 运行本地服务（默认监听 127.0.0.1:8080）
python app.py
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，用于后端服务与命令行工具 |
| SQLite3 | 3.31.0 及以上 | 嵌入式数据库，用于存储链接元数据与状态信息 |
| requests | 2.25.0 及以上 | 用于发起 HTTP 请求，执行链接状态检测与元数据抽取 |
| beautifulsoup4 | 4.9.0 及以上 | 可选依赖，用于解析 HTML 页面标题与摘要信息 |
| tqdm | 4.50.0 及以上 | 用于批量导入时的进度显示，提升命令行交互体验 |
| pytest | 6.0.0 及以上 | 开发测试依赖，用于运行单元测试与集成测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何导入链接、执行检索、配置检测任务以及导出数据 |
| 命令行工具参考 | docs/cli-reference.md | 每条 CLI 命令的详细参数、使用示例与输出格式说明 |
| 配置说明 | docs/configuration.md | 环境变量、配置文件项以及各运行参数的含义与默认值 |
| 开发指南 | docs/development.md | 项目结构说明、代码规范、测试流程与提交准则 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/9584.htm
- http://m.wap.ghtkgg.cn/jnews/9432.htm
- http://m.wap.ghtkgg.cn/jnews/5138.htm
- http://m.wap.ghtkgg.cn/jnews/840009.htm
- http://m.wap.ghtkgg.cn/jnews/128658.htm
- http://m.wap.ghtkgg.cn/jnews/6550040.htm
- http://m.wap.ghtkgg.cn/jnews/1493.htm
- http://m.wap.ghtkgg.cn/jnews/6084015.htm
- http://m.wap.ghtkgg.cn/jnews/1525243.htm
- http://m.wap.ghtkgg.cn/jnews/21497.htm
- http://m.wap.ghtkgg.cn/jnews/56661.htm
- http://m.wap.ghtkgg.cn/jnews/6491806.htm
- http://m.wap.ghtkgg.cn/jnews/3859321.htm
- http://m.wap.ghtkgg.cn/jnews/5858544.htm
- http://m.wap.ghtkgg.cn/jnews/63237.htm
- http://m.wap.ghtkgg.cn/jnews/3615.htm
- http://m.wap.ghtkgg.cn/jnews/602169.htm
- http://m.wap.ghtkgg.cn/jnews/40866.htm
- http://m.wap.ghtkgg.cn/jnews/9067673.htm
- http://m.wap.ghtkgg.cn/jnews/25101.htm
- http://m.wap.ghtkgg.cn/jnews/40447.htm
- http://m.wap.ghtkgg.cn/jnews/796386.htm
- http://m.wap.ghtkgg.cn/jnews/16040.htm
- http://m.wap.ghtkgg.cn/jnews/561916.htm
- http://m.wap.ghtkgg.cn/jnews/303617.htm
- http://m.wap.ghtkgg.cn/jnews/9423291.htm
- http://m.wap.ghtkgg.cn/jnews/8037798.htm
- http://m.wap.ghtkgg.cn/jnews/0297028.htm
- http://m.wap.ghtkgg.cn/jnews/3491406.htm
- http://m.wap.ghtkgg.cn/jnews/362685.htm
- http://m.wap.ghtkgg.cn/jnews/3352.htm
- http://m.wap.ghtkgg.cn/jnews/05382.htm
- http://m.wap.ghtkgg.cn/jnews/7174.htm
- http://m.wap.ghtkgg.cn/jnews/11702.htm
- http://m.wap.ghtkgg.cn/jnews/97826.htm
- http://m.wap.ghtkgg.cn/jnews/1700.htm
- http://m.wap.ghtkgg.cn/jnews/88554.htm
- http://m.wap.ghtkgg.cn/jnews/3006.htm
- http://m.wap.ghtkgg.cn/jnews/6940139.htm
- http://m.wap.ghtkgg.cn/jnews/109002.htm
- http://m.wap.ghtkgg.cn/jnews/76942.htm
- http://m.wap.ghtkgg.cn/jnews/0090.htm
- http://m.wap.ghtkgg.cn/jnews/0517.htm
- http://m.wap.ghtkgg.cn/jnews/955592.htm
- http://m.wap.ghtkgg.cn/jnews/6019.htm
- http://m.wap.ghtkgg.cn/jnews/4858595.htm
- http://m.wap.ghtkgg.cn/jnews/31509.htm
- http://m.wap.ghtkgg.cn/jnews/556998.htm
- http://m.wap.ghtkgg.cn/jnews/115622.htm
- http://m.wap.ghtkgg.cn/jnews/99652.htm
- http://m.wap.ghtkgg.cn/jnews/57315.htm
- http://m.wap.ghtkgg.cn/jnews/61626.htm
- http://m.wap.ghtkgg.cn/jnews/2928.htm
- http://m.wap.ghtkgg.cn/jnews/0739.htm
- http://m.wap.ghtkgg.cn/jnews/9820060.htm
- http://m.wap.ghtkgg.cn/jnews/604417.htm
- http://m.wap.ghtkgg.cn/jnews/6863.htm
- http://m.wap.ghtkgg.cn/jnews/9084.htm
- http://m.wap.ghtkgg.cn/jnews/8386.htm
- http://m.wap.ghtkgg.cn/jnews/9183.htm
- http://m.wap.ghtkgg.cn/jnews/138919.htm
- http://m.wap.ghtkgg.cn/jnews/47314.htm
- http://m.wap.ghtkgg.cn/jnews/9446777.htm
- http://m.wap.ghtkgg.cn/jnews/6978.htm
- http://m.wap.ghtkgg.cn/jnews/313329.htm
- http://m.wap.ghtkgg.cn/jnews/8461.htm
- http://m.wap.ghtkgg.cn/jnews/6394308.htm
- http://m.wap.ghtkgg.cn/jnews/1682.htm
- http://m.wap.ghtkgg.cn/jnews/7008600.htm
- http://m.wap.ghtkgg.cn/jnews/7278981.htm
- http://m.wap.ghtkgg.cn/jnews/641073.htm
- http://m.wap.ghtkgg.cn/jnews/4300562.htm
- http://m.wap.ghtkgg.cn/jnews/844738.htm
- http://m.wap.ghtkgg.cn/jnews/776504.htm
- http://m.wap.ghtkgg.cn/jnews/838695.htm
- http://m.wap.ghtkgg.cn/jnews/6355.htm
- http://m.wap.ghtkgg.cn/jnews/05861.htm
- http://m.wap.ghtkgg.cn/jnews/1072.htm
- http://m.wap.ghtkgg.cn/jnews/82570.htm
- http://m.wap.ghtkgg.cn/jnews/0720973.htm
- http://m.wap.ghtkgg.cn/jnews/186078.htm
- http://m.wap.ghtkgg.cn/jnews/183720.htm
- http://m.wap.ghtkgg.cn/jnews/86570.htm
- http://m.wap.ghtkgg.cn/jnews/5844.htm
- http://m.wap.ghtkgg.cn/jnews/37134.htm
- http://m.wap.ghtkgg.cn/jnews/32857.htm
- http://m.wap.ghtkgg.cn/jnews/3195.htm
- http://m.wap.ghtkgg.cn/jnews/0964.htm
- http://m.wap.ghtkgg.cn/jnews/744187.htm
- http://m.wap.ghtkgg.cn/jnews/91934.htm
- http://m.wap.ghtkgg.cn/jnews/8472.htm
- http://m.wap.ghtkgg.cn/jnews/3735429.htm
- http://m.wap.ghtkgg.cn/jnews/3424.htm
- http://m.wap.ghtkgg.cn/jnews/3884224.htm
- http://m.wap.ghtkgg.cn/jnews/728769.htm
- http://m.wap.ghtkgg.cn/jnews/0890.htm
- http://m.wap.ghtkgg.cn/jnews/671160.htm
- http://m.wap.ghtkgg.cn/jnews/5835477.htm
- http://m.wap.ghtkgg.cn/jnews/15624.htm
- http://m.wap.ghtkgg.cn/jnews/9520039.htm
- http://m.wap.ghtkgg.cn/jnews/4730663.htm
- http://m.wap.ghtkgg.cn/jnews/4810.htm
- http://m.wap.ghtkgg.cn/jnews/8061.htm
- http://m.wap.ghtkgg.cn/jnews/989121.htm
- http://m.wap.ghtkgg.cn/jnews/62952.htm
- http://m.wap.ghtkgg.cn/jnews/7912.htm
- http://m.wap.ghtkgg.cn/jnews/7623.htm
- http://m.wap.ghtkgg.cn/jnews/724626.htm
- http://m.wap.ghtkgg.cn/jnews/6777019.htm
- http://m.wap.ghtkgg.cn/jnews/7930.htm
- http://m.wap.ghtkgg.cn/jnews/984796.htm
- http://m.wap.ghtkgg.cn/jnews/746152.htm
- http://m.wap.ghtkgg.cn/jnews/132261.htm
- http://m.wap.ghtkgg.cn/jnews/46062.htm
- http://m.wap.ghtkgg.cn/jnews/9758314.htm
- http://m.wap.ghtkgg.cn/jnews/42097.htm
- http://m.wap.ghtkgg.cn/jnews/6109838.htm
- http://m.wap.ghtkgg.cn/jnews/2162.htm
- http://m.wap.ghtkgg.cn/jnews/68458.htm
- http://m.wap.ghtkgg.cn/jnews/18272.htm
- http://m.wap.ghtkgg.cn/jnews/8155808.htm
- http://m.wap.ghtkgg.cn/jnews/2726290.htm
- http://m.wap.ghtkgg.cn/jnews/74835.htm
- http://m.wap.ghtkgg.cn/jnews/156456.htm
- http://m.wap.ghtkgg.cn/jnews/4367554.htm
- http://m.wap.ghtkgg.cn/jnews/389624.htm
- http://m.wap.ghtkgg.cn/jnews/749704.htm
- http://m.wap.ghtkgg.cn/jnews/3639233.htm
- http://m.wap.ghtkgg.cn/jnews/519890.htm
- http://m.wap.ghtkgg.cn/jnews/1997.htm
- http://m.wap.ghtkgg.cn/jnews/05966.htm
- http://m.wap.ghtkgg.cn/jnews/495917.htm
- http://m.wap.ghtkgg.cn/jnews/010899.htm
- http://m.wap.ghtkgg.cn/jnews/2031.htm
- http://m.wap.ghtkgg.cn/jnews/9411881.htm
- http://m.wap.ghtkgg.cn/jnews/89553.htm
- http://m.wap.ghtkgg.cn/jnews/407292.htm
- http://m.wap.ghtkgg.cn/jnews/602955.htm
- http://m.wap.ghtkgg.cn/jnews/2045.htm
- http://m.wap.ghtkgg.cn/jnews/6294.htm
- http://m.wap.ghtkgg.cn/jnews/9637716.htm
- http://m.wap.ghtkgg.cn/jnews/6674.htm
- http://m.wap.ghtkgg.cn/jnews/6227.htm
- http://m.wap.ghtkgg.cn/jnews/316851.htm
- http://m.wap.ghtkgg.cn/jnews/2000.htm
- http://m.wap.ghtkgg.cn/jnews/07286.htm
- http://m.wap.ghtkgg.cn/jnews/005059.htm
- http://m.wap.ghtkgg.cn/jnews/5976.htm
- http://m.wap.ghtkgg.cn/jnews/4828.htm
- http://m.wap.ghtkgg.cn/jnews/406558.htm
- http://m.wap.ghtkgg.cn/jnews/0564.htm
- http://m.wap.ghtkgg.cn/jnews/90071.htm
- http://m.wap.ghtkgg.cn/jnews/1453.htm
- http://m.wap.ghtkgg.cn/jnews/31460.htm
- http://m.wap.ghtkgg.cn/jnews/16808.htm
- http://m.wap.ghtkgg.cn/jnews/596816.htm
- http://m.wap.ghtkgg.cn/jnews/7760.htm
- http://m.wap.ghtkgg.cn/jnews/68963.htm
- http://m.wap.ghtkgg.cn/jnews/5145607.htm
- http://m.wap.ghtkgg.cn/jnews/4368.htm
- http://m.wap.ghtkgg.cn/jnews/75549.htm
- http://m.wap.ghtkgg.cn/jnews/64659.htm
- http://m.wap.ghtkgg.cn/jnews/0629.htm
- http://m.wap.ghtkgg.cn/jnews/7844688.htm
- http://m.wap.ghtkgg.cn/jnews/60248.htm
- http://m.wap.ghtkgg.cn/jnews/170275.htm
- http://m.wap.ghtkgg.cn/jnews/0821690.htm
- http://m.wap.ghtkgg.cn/jnews/987560.htm
- http://m.wap.ghtkgg.cn/jnews/94779.htm
- http://m.wap.ghtkgg.cn/jnews/5516375.htm
- http://m.wap.ghtkgg.cn/jnews/2103.htm
- http://m.wap.ghtkgg.cn/jnews/6869410.htm
- http://m.wap.ghtkgg.cn/jnews/0276.htm
- http://m.wap.ghtkgg.cn/jnews/7700.htm
- http://m.wap.ghtkgg.cn/jnews/94180.htm
- http://m.wap.ghtkgg.cn/jnews/10186.htm
- http://m.wap.ghtkgg.cn/jnews/7905.htm
- http://m.wap.ghtkgg.cn/jnews/5229684.htm
- http://m.wap.ghtkgg.cn/jnews/470790.htm
- http://m.wap.ghtkgg.cn/jnews/2360177.htm
- http://m.wap.ghtkgg.cn/jnews/6878318.htm
- http://m.wap.ghtkgg.cn/jnews/02105.htm
- http://m.wap.ghtkgg.cn/jnews/95180.htm
- http://m.wap.ghtkgg.cn/jnews/056103.htm
- http://m.wap.ghtkgg.cn/jnews/934465.htm
- http://m.wap.ghtkgg.cn/jnews/3153.htm
- http://m.wap.ghtkgg.cn/jnews/977280.htm
- http://m.wap.ghtkgg.cn/jnews/2557.htm
- http://m.wap.ghtkgg.cn/jnews/310615.htm
- http://m.wap.ghtkgg.cn/jnews/6922820.htm
- http://m.wap.ghtkgg.cn/jnews/3209788.htm
- http://m.wap.ghtkgg.cn/jnews/60807.htm
- http://m.wap.ghtkgg.cn/jnews/510013.htm
- http://m.wap.ghtkgg.cn/jnews/0824950.htm
- http://m.wap.ghtkgg.cn/jnews/1209.htm
- http://m.wap.ghtkgg.cn/jnews/6570615.htm
- http://m.wap.ghtkgg.cn/jnews/879421.htm
- http://m.wap.ghtkgg.cn/jnews/869962.htm
- http://m.wap.ghtkgg.cn/jnews/8980075.htm
- http://m.wap.ghtkgg.cn/jnews/890379.htm
- http://m.wap.ghtkgg.cn/jnews/6471412.htm
- http://m.wap.ghtkgg.cn/jnews/2197646.htm
- http://m.wap.ghtkgg.cn/jnews/00655.htm
- http://m.wap.ghtkgg.cn/jnews/196936.htm
- http://m.wap.ghtkgg.cn/jnews/1382.htm
- http://m.wap.ghtkgg.cn/jnews/9809.htm
- http://m.wap.ghtkgg.cn/jnews/6479226.htm
- http://m.wap.ghtkgg.cn/jnews/0655.htm
- http://m.wap.ghtkgg.cn/jnews/4990002.htm
- http://m.wap.ghtkgg.cn/jnews/4783249.htm
- http://m.wap.ghtkgg.cn/jnews/0776771.htm
- http://m.wap.ghtkgg.cn/jnews/5774.htm
- http://m.wap.ghtkgg.cn/jnews/6223.htm
- http://m.wap.ghtkgg.cn/jnews/494418.htm
- http://m.wap.ghtkgg.cn/jnews/517065.htm
- http://m.wap.ghtkgg.cn/jnews/724831.htm
- http://m.wap.ghtkgg.cn/jnews/0970993.htm
- http://m.wap.ghtkgg.cn/jnews/37790.htm
- http://m.wap.ghtkgg.cn/jnews/6816352.htm
- http://m.wap.ghtkgg.cn/jnews/831143.htm
- http://m.wap.ghtkgg.cn/jnews/382462.htm
- http://m.wap.ghtkgg.cn/jnews/60631.htm
- http://m.wap.ghtkgg.cn/jnews/3027.htm
- http://m.wap.ghtkgg.cn/jnews/5647096.htm
- http://m.wap.ghtkgg.cn/jnews/769993.htm
- http://m.wap.ghtkgg.cn/jnews/567323.htm
- http://m.wap.ghtkgg.cn/jnews/198023.htm
- http://m.wap.ghtkgg.cn/jnews/5801813.htm
- http://m.wap.ghtkgg.cn/jnews/4753362.htm
- http://m.wap.ghtkgg.cn/jnews/6547.htm
- http://m.wap.ghtkgg.cn/jnews/7092.htm
- http://m.wap.ghtkgg.cn/jnews/247508.htm
- http://m.wap.ghtkgg.cn/jnews/4370.htm
- http://m.wap.ghtkgg.cn/jnews/0702.htm
- http://m.wap.ghtkgg.cn/jnews/5292.htm
- http://m.wap.ghtkgg.cn/jnews/277607.htm
- http://m.wap.ghtkgg.cn/jnews/1125.htm
- http://m.wap.ghtkgg.cn/jnews/18493.htm
- http://m.wap.ghtkgg.cn/jnews/87312.htm
- http://m.wap.ghtkgg.cn/jnews/197348.htm
- http://m.wap.ghtkgg.cn/jnews/3678.htm
- http://m.wap.ghtkgg.cn/jnews/8349869.htm
- http://m.wap.ghtkgg.cn/jnews/1607185.htm
- http://m.wap.ghtkgg.cn/jnews/409747.htm
- http://m.wap.ghtkgg.cn/jnews/5222.htm
- http://m.wap.ghtkgg.cn/jnews/83963.htm
- http://m.wap.ghtkgg.cn/jnews/801152.htm
- http://m.wap.ghtkgg.cn/jnews/6498.htm
- http://m.wap.ghtkgg.cn/jnews/0679201.htm
- http://m.wap.ghtkgg.cn/jnews/157551.htm
- http://m.wap.ghtkgg.cn/jnews/583667.htm
- http://m.wap.ghtkgg.cn/jnews/3579.htm
- http://m.wap.ghtkgg.cn/jnews/3393.htm
- http://m.wap.ghtkgg.cn/jnews/9248.htm
- http://m.wap.ghtkgg.cn/jnews/63557.htm
- http://m.wap.ghtkgg.cn/jnews/519928.htm
- http://m.wap.ghtkgg.cn/jnews/256064.htm
- http://m.wap.ghtkgg.cn/jnews/5902700.htm
- http://m.wap.ghtkgg.cn/jnews/220169.htm
- http://m.wap.ghtkgg.cn/jnews/0524048.htm
- http://m.wap.ghtkgg.cn/jnews/687030.htm
- http://m.wap.ghtkgg.cn/jnews/865642.htm
- http://m.wap.ghtkgg.cn/jnews/188574.htm
- http://m.wap.ghtkgg.cn/jnews/05421.htm
- http://m.wap.ghtkgg.cn/jnews/788441.htm
- http://m.wap.ghtkgg.cn/jnews/0397.htm
- http://m.wap.ghtkgg.cn/jnews/41250.htm
- http://m.wap.ghtkgg.cn/jnews/3697818.htm
- http://m.wap.ghtkgg.cn/jnews/3150407.htm
- http://m.wap.ghtkgg.cn/jnews/06305.htm
- http://m.wap.ghtkgg.cn/jnews/74805.htm
- http://m.wap.ghtkgg.cn/jnews/471768.htm
- http://m.wap.ghtkgg.cn/jnews/38237.htm
- http://m.wap.ghtkgg.cn/jnews/69531.htm
- http://m.wap.ghtkgg.cn/jnews/241253.htm
- http://m.wap.ghtkgg.cn/jnews/31000.htm
- http://m.wap.ghtkgg.cn/jnews/01708.htm
- http://m.wap.ghtkgg.cn/jnews/35457.htm
- http://m.wap.ghtkgg.cn/jnews/36209.htm
- http://m.wap.ghtkgg.cn/jnews/4998.htm
- http://m.wap.ghtkgg.cn/jnews/30577.htm
- http://m.wap.ghtkgg.cn/jnews/3940.htm
- http://m.wap.ghtkgg.cn/jnews/076238.htm
- http://m.wap.ghtkgg.cn/jnews/0223.htm
- http://m.wap.ghtkgg.cn/jnews/4960.htm
- http://m.wap.ghtkgg.cn/jnews/823624.htm
- http://m.wap.ghtkgg.cn/jnews/705548.htm
- http://m.wap.ghtkgg.cn/jnews/601265.htm
- http://m.wap.ghtkgg.cn/jnews/452221.htm
- http://m.wap.ghtkgg.cn/jnews/32626.htm
- http://m.wap.ghtkgg.cn/jnews/6428105.htm
- http://m.wap.ghtkgg.cn/jnews/2223195.htm
- http://m.wap.ghtkgg.cn/jnews/6069709.htm
- http://m.wap.ghtkgg.cn/jnews/210869.htm
- http://m.wap.ghtkgg.cn/jnews/55932.htm
- http://m.wap.ghtkgg.cn/jnews/3605.htm
- http://m.wap.ghtkgg.cn/jnews/787081.htm
- http://m.wap.ghtkgg.cn/jnews/33955.htm
- http://m.wap.ghtkgg.cn/jnews/7886845.htm
- http://m.wap.ghtkgg.cn/jnews/810129.htm

## 项目结构

```
weblink-archive/
├── app.py                      # 主入口，启动 Flask 开发服务器
├── config.py                   # 配置文件，包含数据库路径、检测间隔等参数
├── requirements.txt            # Python 依赖清单
├── README.md                   # 项目说明文档
├── LICENSE                     # MIT 许可证文件
├── docs/                       # 文档目录
│   ├── user-guide.md           # 用户手册
│   ├── cli-reference.md        # 命令行工具完整参考
│   ├── configuration.md        # 配置项详解
│   └── development.md          # 开发环境搭建与贡献指南
├── weblink/                    # 核心模块包
│   ├── __init__.py
│   ├── models.py               # SQLite 数据表定义与 ORM 映射
│   ├── crawler.py              # 链接元数据抽取与状态检测逻辑
│   ├── importer.py             # 批量导入、去重与批次管理
│   ├── exporter.py             # JSON/CSV/纯文本导出功能
│   ├── query.py                # 多维度检索与过滤实现
│   └── utils.py                # 通用工具函数，包含日期处理与校验
├── scripts/                    # 辅助脚本目录
│   ├── init_db.py              # 初始化数据库表结构
│   ├── batch_import.py         # 命令行批量导入脚本
│   └── check_status.py         # 批量状态检测脚本
├── tests/                      # 测试目录
│   ├── test_models.py          # 数据模型单元测试
│   ├── test_crawler.py         # 爬取逻辑单元测试
│   └── test_query.py           # 查询接口单元测试
├── data/                       # 数据存储目录
│   └── weblink.db              # SQLite 数据库文件（首次运行时生成）
└── logs/                       # 日志目录
    └── app.log                 # 应用运行日志
```

## 贡献指南

1. 在 GitHub 上 fork 本项目仓库，并将 fork 后的仓库克隆至本地开发环境。创建新的功能分支，分支名称应反映本次变更的概要，例如 `feat/batch-tag-update` 或 `fix/importer-memory-issue`。

2. 编写代码时遵循项目已有的编码风格，Python 代码应通过 flake8 和 pylint 的基本规则检查。新增功能或修复缺陷时，需在 `tests/` 目录下补充对应的单元测试用例，确保测试覆盖率达到合理水平。

3. 提交代码前运行完整的测试套件，确保所有既有测试通过。提交信息应使用语义化格式，首行为简短摘要，后续可附详细说明。提交信息示例：`importer: add retry mechanism for failed HEAD requests`。

4. 向原仓库发起 pull request，并在描述中清晰说明本次变更的目的、实现方式以及影响范围。项目维护者会在数个工作日内进行评审，如有修改意见将通过评论形式反馈。

5. 若需报告缺陷或提出新功能建议，请使用 GitHub Issues 进行跟踪。提交 Issue 时请附上完整的环境信息、复现步骤及预期行为，以便快速定位问题。

## 常见问题

**问：批量导入大量链接时，程序是否会因为网络请求失败而中断？**

答：不会。批量导入过程中的网络请求均带有异常捕获机制，单条链接的 HEAD 请求或标题解析失败不会影响整体导入流程。失败记录会被标记为“检测异常”状态，并在日志中输出具体错误原因。用户可在导入完成后通过查询接口筛选出异常状态的链接，单独进行重试或手动修正。

**问：如何迁移数据库到另一台机器？**

答：本项目使用 SQLite 作为后端数据库，所有数据存储于 `data/weblink.db` 文件中。迁移时只需将该文件复制到目标机器的相同相对路径下，并确保目标环境已安装兼容版本的 SQLite3 与 Python 依赖即可。若需跨操作系统迁移，SQLite 数据库文件本身具有跨平台兼容性，无需额外转换。

**问：链接状态检测的频率是否会影响源站服务器？**

答：状态检测模块默认使用 `requests` 库的 HEAD 方法，仅获取响应头部信息，不下载页面正文内容，对源站服务器的负载影响极小。同时，检测任务采用单线程顺序执行，并内置了 1 秒的请求间隔延时，避免在短时间内对同一域名发起大量并发请求。用户也可在配置文件中自定义检测间隔与并发控制参数。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
