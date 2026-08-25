# NewsLink Navigator

NewsLink Navigator 是一个面向技术信息聚合与外部资源导航的开源工具，专为需要批量管理、分类展示和快速检索分散式新闻链接的开发者与内容运营团队设计。该项目将原始来源中的大量新闻链接（涵盖行业动态、技术公告、项目发布等）转化为可结构化浏览、可标签过滤、可定期更新的轻量级导航门户，解决人工收集后难以整理、分享与二次分发的痛点。

NewsLink Navigator 不依赖复杂后端，基于静态站点生成逻辑，将输入的 URL 列表自动转化为带元数据索引的导航页面。它适用于个人知识库构建、团队内部信息共享、开源项目外部参考链接归档等场景，尤其适合需要长期维护数百乃至上千条外链引用关系的技术文档项目。

## 功能概览

- **批量链接导入与结构化存储** 支持从纯文本列表、CSV 或 JSON 批量导入 URL，自动解析并存入本地 SQLite 或 JSON 数据源，保留原始顺序与分组标记。

- **元数据自动补全与编辑** 对每条链接可添加标题、描述、标签、重要等级、更新日期等自定义字段，支持手动编辑与批量修改。

- **多维度筛选与全文搜索** 基于标签、关键词、日期范围、来源域名等维度快速过滤链接列表，内置轻量级全文检索引擎，支持对标题与描述字段的模糊匹配。

- **响应式导航页面生成** 根据数据源自动生成移动端适配的 HTML 导航页面，支持列表视图与卡片视图切换，页面样式可通过 CSS 变量自定义。

- **链接状态健康检查** 内置定时或手动触发的 HTTP 状态检测机制，标记失效链接或重定向链接，便于维护人员及时清理或更新。

- **增量更新与去重保护** 在新增链接时自动检测重复 URL，支持按域名、路径或完整 URL 的严格去重策略，避免数据冗余。

- **导入导出兼容多种格式** 支持导出为 Markdown 表格、JSON、CSV 格式，便于与其他文档工具或静态站点生成器（如 Hugo、VuePress）集成。

- **外部资源白名单与分类模板** 提供可配置的分类模板（如「官方公告」「技术博客」「社区讨论」「活动报名」），快速为链接分配预设类别，并支持自定义分类扩展。

## 应用场景

**技术团队内部资讯看板**  
技术负责人或 DevOps 工程师可使用 NewsLink Navigator 汇总每日行业安全通告、框架发布日志、云服务状态更新等外部资源，生成团队内部共享的资讯页面，减少重复查找时间。

**开源项目外部参考附录维护**  
开源项目维护者需要在文档中保留大量外部参考链接（如 RFC 文档、相关项目地址、技术规范来源），通过 NewsLink Navigator 管理这些链接的变更与分类，确保文档引用长期可追溯。

**个人技术知识库的外链中心**  
技术博主或研究员可将日常阅读中积累的数百篇技术文章、工具网站、在线演示链接集中管理，按主题生成个人导航站，便于跨设备访问和周期性回顾。

**内容聚合站点的数据预处理**  
内容运营人员可利用该工具对采集到的原始链接列表进行清洗、去重、分类标注，再将处理后的结构化数据导出至 CMS 或社交媒体发布系统，提升内容生产效率。

**离线文档的外链资源打包**  
在需要生成离线技术手册或培训教材时，可通过 NewsLink Navigator 导出所有外链的元数据表格，一并打包为资源索引附录，提升离线文档的完整性和可用性。

## 快速开始

以下步骤帮助您在本地环境中快速启动 NewsLink Navigator 并导入示例链接列表。

```bash
# 克隆项目仓库
git clone https://github.com/newsnav/newslink-navigator.git

# 进入项目目录
cd newslink-navigator

# 安装依赖（使用 pip 或 poetry）
pip install -r requirements.txt
# 或 poetry install

# 执行初始数据迁移（创建本地数据库与配置文件）
python scripts/init_db.py

# 导入示例链接列表（将原始链接保存为 links.txt 后执行）
python scripts/import_links.py --file /path/to/links.txt --source raw

# 生成静态导航页面（输出至 ./output 目录）
python builder/generate.py --output ./output --template default

# 启动本地开发服务器预览
python -m http.server --directory ./output 8080
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，用于数据导入、处理与生成逻辑 |
| SQLite | 3.35 及以上 | 默认嵌入式数据库，用于存储链接元数据及索引 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| Git | 2.30 及以上 | 用于克隆仓库及版本管理（非运行时必需） |
| 操作系统 | Linux / macOS / Windows (WSL2) | 跨平台支持，推荐使用 Linux 或 macOS 以获得最佳性能 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速安装、配置第一个数据源并生成导航页面？ |
| 数据管理 | docs/data-management.md | 如何批量导入、编辑、删除链接？去重策略和标签系统如何使用？ |
| 页面定制 | docs/customization.md | 如何修改导航页面的标题、Logo、配色方案及卡片布局？ |
| 运维参考 | docs/operations.md | 如何配置链接健康检查定时任务、数据备份与迁移步骤？ |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/9145131.htm
- http://m.blog.ghtkgg.cn/nnews/971819.htm
- http://m.blog.ghtkgg.cn/nnews/748151.htm
- http://m.blog.ghtkgg.cn/nnews/832682.htm
- http://m.blog.ghtkgg.cn/nnews/5184857.htm
- http://m.blog.ghtkgg.cn/nnews/4024339.htm
- http://m.blog.ghtkgg.cn/nnews/81664.htm
- http://m.blog.ghtkgg.cn/nnews/3208.htm
- http://m.blog.ghtkgg.cn/nnews/31843.htm
- http://m.blog.ghtkgg.cn/nnews/5962046.htm
- http://m.blog.ghtkgg.cn/nnews/14500.htm
- http://m.blog.ghtkgg.cn/nnews/1409.htm
- http://m.blog.ghtkgg.cn/nnews/28085.htm
- http://m.blog.ghtkgg.cn/nnews/71835.htm
- http://m.blog.ghtkgg.cn/nnews/6757290.htm
- http://m.blog.ghtkgg.cn/nnews/5941997.htm
- http://m.blog.ghtkgg.cn/nnews/1668.htm
- http://m.blog.ghtkgg.cn/nnews/43062.htm
- http://m.blog.ghtkgg.cn/nnews/3184.htm
- http://m.blog.ghtkgg.cn/nnews/788618.htm
- http://m.blog.ghtkgg.cn/nnews/473078.htm
- http://m.blog.ghtkgg.cn/nnews/907039.htm
- http://m.blog.ghtkgg.cn/nnews/1557.htm
- http://m.blog.ghtkgg.cn/nnews/4142965.htm
- http://m.blog.ghtkgg.cn/nnews/8584.htm
- http://m.blog.ghtkgg.cn/nnews/392768.htm
- http://m.blog.ghtkgg.cn/nnews/910263.htm
- http://m.blog.ghtkgg.cn/nnews/662000.htm
- http://m.blog.ghtkgg.cn/nnews/0945.htm
- http://m.blog.ghtkgg.cn/nnews/428855.htm
- http://m.blog.ghtkgg.cn/nnews/9604.htm
- http://m.blog.ghtkgg.cn/nnews/6691.htm
- http://m.blog.ghtkgg.cn/nnews/09221.htm
- http://m.blog.ghtkgg.cn/nnews/1895.htm
- http://m.blog.ghtkgg.cn/nnews/13831.htm
- http://m.blog.ghtkgg.cn/nnews/8363008.htm
- http://m.blog.ghtkgg.cn/nnews/4718126.htm
- http://m.blog.ghtkgg.cn/nnews/9191606.htm
- http://m.blog.ghtkgg.cn/nnews/5547987.htm
- http://m.blog.ghtkgg.cn/nnews/5741790.htm
- http://m.blog.ghtkgg.cn/nnews/167309.htm
- http://m.blog.ghtkgg.cn/nnews/715224.htm
- http://m.blog.ghtkgg.cn/nnews/4322613.htm
- http://m.blog.ghtkgg.cn/nnews/2897.htm
- http://m.blog.ghtkgg.cn/nnews/3655140.htm
- http://m.blog.ghtkgg.cn/nnews/7225.htm
- http://m.blog.ghtkgg.cn/nnews/0125.htm
- http://m.blog.ghtkgg.cn/nnews/815967.htm
- http://m.blog.ghtkgg.cn/nnews/4691321.htm
- http://m.blog.ghtkgg.cn/nnews/5572.htm
- http://m.blog.ghtkgg.cn/nnews/9185329.htm
- http://m.blog.ghtkgg.cn/nnews/36003.htm
- http://m.blog.ghtkgg.cn/nnews/66948.htm
- http://m.blog.ghtkgg.cn/nnews/789564.htm
- http://m.blog.ghtkgg.cn/nnews/1441809.htm
- http://m.blog.ghtkgg.cn/nnews/108904.htm
- http://m.blog.ghtkgg.cn/nnews/9122.htm
- http://m.blog.ghtkgg.cn/nnews/07856.htm
- http://m.blog.ghtkgg.cn/nnews/389528.htm
- http://m.blog.ghtkgg.cn/nnews/5351009.htm
- http://m.blog.ghtkgg.cn/nnews/65963.htm
- http://m.blog.ghtkgg.cn/nnews/9948967.htm
- http://m.blog.ghtkgg.cn/nnews/923151.htm
- http://m.blog.ghtkgg.cn/nnews/612630.htm
- http://m.blog.ghtkgg.cn/nnews/5522.htm
- http://m.blog.ghtkgg.cn/nnews/8421.htm
- http://m.blog.ghtkgg.cn/nnews/77680.htm
- http://m.blog.ghtkgg.cn/nnews/16241.htm
- http://m.blog.ghtkgg.cn/nnews/4522409.htm
- http://m.blog.ghtkgg.cn/nnews/4979.htm
- http://m.blog.ghtkgg.cn/nnews/475949.htm
- http://m.blog.ghtkgg.cn/nnews/4784.htm
- http://m.blog.ghtkgg.cn/nnews/1289.htm
- http://m.blog.ghtkgg.cn/nnews/4518371.htm
- http://m.blog.ghtkgg.cn/nnews/2574.htm
- http://m.blog.ghtkgg.cn/nnews/6265.htm
- http://m.blog.ghtkgg.cn/nnews/1706.htm
- http://m.blog.ghtkgg.cn/nnews/1334966.htm
- http://m.blog.ghtkgg.cn/nnews/4024421.htm
- http://m.blog.ghtkgg.cn/nnews/999950.htm
- http://m.blog.ghtkgg.cn/nnews/429202.htm
- http://m.blog.ghtkgg.cn/nnews/8742368.htm
- http://m.blog.ghtkgg.cn/nnews/738267.htm
- http://m.blog.ghtkgg.cn/nnews/15986.htm
- http://m.blog.ghtkgg.cn/nnews/5466902.htm
- http://m.blog.ghtkgg.cn/nnews/5045.htm
- http://m.blog.ghtkgg.cn/nnews/8920994.htm
- http://m.blog.ghtkgg.cn/nnews/3431.htm
- http://m.blog.ghtkgg.cn/nnews/2207679.htm
- http://m.blog.ghtkgg.cn/nnews/0415448.htm
- http://m.blog.ghtkgg.cn/nnews/648581.htm
- http://m.blog.ghtkgg.cn/nnews/6027.htm
- http://m.blog.ghtkgg.cn/nnews/4539937.htm
- http://m.blog.ghtkgg.cn/nnews/0208761.htm
- http://m.blog.ghtkgg.cn/nnews/41937.htm
- http://m.blog.ghtkgg.cn/nnews/7461383.htm
- http://m.blog.ghtkgg.cn/nnews/8759856.htm
- http://m.blog.ghtkgg.cn/nnews/172998.htm
- http://m.blog.ghtkgg.cn/nnews/7678.htm
- http://m.blog.ghtkgg.cn/nnews/430052.htm
- http://m.blog.ghtkgg.cn/nnews/71192.htm
- http://m.blog.ghtkgg.cn/nnews/16378.htm
- http://m.blog.ghtkgg.cn/nnews/4196802.htm
- http://m.blog.ghtkgg.cn/nnews/421524.htm
- http://m.blog.ghtkgg.cn/nnews/975837.htm
- http://m.blog.ghtkgg.cn/nnews/603592.htm
- http://m.blog.ghtkgg.cn/nnews/43449.htm
- http://m.blog.ghtkgg.cn/nnews/925142.htm
- http://m.blog.ghtkgg.cn/nnews/623701.htm
- http://m.blog.ghtkgg.cn/nnews/4610.htm
- http://m.blog.ghtkgg.cn/nnews/3319.htm
- http://m.blog.ghtkgg.cn/nnews/338853.htm
- http://m.blog.ghtkgg.cn/nnews/61515.htm
- http://m.blog.ghtkgg.cn/nnews/40716.htm
- http://m.blog.ghtkgg.cn/nnews/6649927.htm
- http://m.blog.ghtkgg.cn/nnews/30168.htm
- http://m.blog.ghtkgg.cn/nnews/3295161.htm
- http://m.blog.ghtkgg.cn/nnews/8948679.htm
- http://m.blog.ghtkgg.cn/nnews/5905.htm
- http://m.blog.ghtkgg.cn/nnews/3657298.htm
- http://m.blog.ghtkgg.cn/nnews/9381.htm
- http://m.blog.ghtkgg.cn/nnews/2135541.htm
- http://m.blog.ghtkgg.cn/nnews/135000.htm
- http://m.blog.ghtkgg.cn/nnews/3454.htm
- http://m.blog.ghtkgg.cn/nnews/258706.htm
- http://m.blog.ghtkgg.cn/nnews/684008.htm
- http://m.blog.ghtkgg.cn/nnews/7133.htm
- http://m.blog.ghtkgg.cn/nnews/7947.htm
- http://m.blog.ghtkgg.cn/nnews/28819.htm
- http://m.blog.ghtkgg.cn/nnews/830504.htm
- http://m.blog.ghtkgg.cn/nnews/310030.htm
- http://m.blog.ghtkgg.cn/nnews/73755.htm
- http://m.blog.ghtkgg.cn/nnews/872473.htm
- http://m.blog.ghtkgg.cn/nnews/2031.htm
- http://m.blog.ghtkgg.cn/nnews/5129624.htm
- http://m.blog.ghtkgg.cn/nnews/6773848.htm
- http://m.blog.ghtkgg.cn/nnews/4435092.htm
- http://m.blog.ghtkgg.cn/nnews/4128151.htm
- http://m.blog.ghtkgg.cn/nnews/2519.htm
- http://m.blog.ghtkgg.cn/nnews/549635.htm
- http://m.blog.ghtkgg.cn/nnews/0985.htm
- http://m.blog.ghtkgg.cn/nnews/0137523.htm
- http://m.blog.ghtkgg.cn/nnews/69235.htm
- http://m.blog.ghtkgg.cn/nnews/8669223.htm
- http://m.blog.ghtkgg.cn/nnews/7751537.htm
- http://m.blog.ghtkgg.cn/nnews/57472.htm
- http://m.blog.ghtkgg.cn/nnews/106072.htm
- http://m.blog.ghtkgg.cn/nnews/0222.htm
- http://m.blog.ghtkgg.cn/nnews/752602.htm
- http://m.blog.ghtkgg.cn/nnews/45116.htm
- http://m.blog.ghtkgg.cn/nnews/8095833.htm
- http://m.blog.ghtkgg.cn/nnews/5684232.htm
- http://m.blog.ghtkgg.cn/nnews/4421.htm
- http://m.blog.ghtkgg.cn/nnews/1362243.htm
- http://m.blog.ghtkgg.cn/nnews/58762.htm
- http://m.blog.ghtkgg.cn/nnews/31725.htm
- http://m.blog.ghtkgg.cn/nnews/38606.htm
- http://m.blog.ghtkgg.cn/nnews/1946893.htm
- http://m.blog.ghtkgg.cn/nnews/6384149.htm
- http://m.blog.ghtkgg.cn/nnews/879240.htm
- http://m.blog.ghtkgg.cn/nnews/5536.htm
- http://m.blog.ghtkgg.cn/nnews/4692.htm
- http://m.blog.ghtkgg.cn/nnews/192328.htm
- http://m.blog.ghtkgg.cn/nnews/15355.htm
- http://m.blog.ghtkgg.cn/nnews/1638082.htm
- http://m.blog.ghtkgg.cn/nnews/15152.htm
- http://m.blog.ghtkgg.cn/nnews/4913.htm
- http://m.blog.ghtkgg.cn/nnews/0029919.htm
- http://m.blog.ghtkgg.cn/nnews/446732.htm
- http://m.blog.ghtkgg.cn/nnews/72594.htm
- http://m.blog.ghtkgg.cn/nnews/73138.htm
- http://m.blog.ghtkgg.cn/nnews/4282.htm
- http://m.blog.ghtkgg.cn/nnews/5030621.htm
- http://m.blog.ghtkgg.cn/nnews/6730.htm
- http://m.blog.ghtkgg.cn/nnews/03060.htm
- http://m.blog.ghtkgg.cn/nnews/8414.htm
- http://m.blog.ghtkgg.cn/nnews/7532.htm
- http://m.blog.ghtkgg.cn/nnews/38062.htm
- http://m.blog.ghtkgg.cn/nnews/1260262.htm
- http://m.blog.ghtkgg.cn/nnews/3224346.htm
- http://m.blog.ghtkgg.cn/nnews/7618.htm
- http://m.blog.ghtkgg.cn/nnews/8292708.htm
- http://m.blog.ghtkgg.cn/nnews/535888.htm
- http://m.blog.ghtkgg.cn/nnews/1787.htm
- http://m.blog.ghtkgg.cn/nnews/1786988.htm
- http://m.blog.ghtkgg.cn/nnews/551492.htm
- http://m.blog.ghtkgg.cn/nnews/18858.htm
- http://m.blog.ghtkgg.cn/nnews/54230.htm
- http://m.blog.ghtkgg.cn/nnews/5791.htm
- http://m.blog.ghtkgg.cn/nnews/05369.htm
- http://m.blog.ghtkgg.cn/nnews/562363.htm
- http://m.blog.ghtkgg.cn/nnews/1597.htm
- http://m.blog.ghtkgg.cn/nnews/3941085.htm
- http://m.blog.ghtkgg.cn/nnews/0370198.htm
- http://m.blog.ghtkgg.cn/nnews/83041.htm
- http://m.blog.ghtkgg.cn/nnews/2513135.htm
- http://m.blog.ghtkgg.cn/nnews/35867.htm
- http://m.blog.ghtkgg.cn/nnews/47290.htm
- http://m.blog.ghtkgg.cn/nnews/7463.htm
- http://m.blog.ghtkgg.cn/nnews/71650.htm
- http://m.blog.ghtkgg.cn/nnews/1512.htm
- http://m.blog.ghtkgg.cn/nnews/4270.htm
- http://m.blog.ghtkgg.cn/nnews/4920.htm
- http://m.blog.ghtkgg.cn/nnews/379957.htm
- http://m.blog.ghtkgg.cn/nnews/1930.htm
- http://m.blog.ghtkgg.cn/nnews/83868.htm
- http://m.blog.ghtkgg.cn/nnews/5488.htm
- http://m.blog.ghtkgg.cn/nnews/6618208.htm
- http://m.blog.ghtkgg.cn/nnews/078589.htm
- http://m.blog.ghtkgg.cn/nnews/226154.htm
- http://m.blog.ghtkgg.cn/nnews/0668657.htm
- http://m.blog.ghtkgg.cn/nnews/5215.htm
- http://m.blog.ghtkgg.cn/nnews/142141.htm
- http://m.blog.ghtkgg.cn/nnews/7761122.htm
- http://m.blog.ghtkgg.cn/nnews/0141797.htm
- http://m.blog.ghtkgg.cn/nnews/10242.htm
- http://m.blog.ghtkgg.cn/nnews/31546.htm
- http://m.blog.ghtkgg.cn/nnews/72747.htm
- http://m.blog.ghtkgg.cn/nnews/5941.htm
- http://m.blog.ghtkgg.cn/nnews/586382.htm
- http://m.blog.ghtkgg.cn/nnews/870938.htm
- http://m.blog.ghtkgg.cn/nnews/9152.htm
- http://m.blog.ghtkgg.cn/nnews/6748.htm
- http://m.blog.ghtkgg.cn/nnews/611999.htm
- http://m.blog.ghtkgg.cn/nnews/762254.htm
- http://m.blog.ghtkgg.cn/nnews/72685.htm
- http://m.blog.ghtkgg.cn/nnews/0282967.htm
- http://m.blog.ghtkgg.cn/nnews/4294.htm
- http://m.blog.ghtkgg.cn/nnews/3645.htm
- http://m.blog.ghtkgg.cn/nnews/5756927.htm
- http://m.blog.ghtkgg.cn/nnews/42059.htm
- http://m.blog.ghtkgg.cn/nnews/7202654.htm
- http://m.blog.ghtkgg.cn/nnews/1836.htm
- http://m.blog.ghtkgg.cn/nnews/94392.htm
- http://m.blog.ghtkgg.cn/nnews/095321.htm
- http://m.blog.ghtkgg.cn/nnews/6338728.htm
- http://m.blog.ghtkgg.cn/nnews/747690.htm
- http://m.blog.ghtkgg.cn/nnews/3883953.htm
- http://m.blog.ghtkgg.cn/nnews/74084.htm
- http://m.blog.ghtkgg.cn/nnews/5365.htm
- http://m.blog.ghtkgg.cn/nnews/9578217.htm
- http://m.blog.ghtkgg.cn/nnews/015373.htm
- http://m.blog.ghtkgg.cn/nnews/0304438.htm
- http://m.blog.ghtkgg.cn/nnews/64543.htm
- http://m.blog.ghtkgg.cn/nnews/2876.htm
- http://m.blog.ghtkgg.cn/nnews/988870.htm
- http://m.blog.ghtkgg.cn/nnews/94798.htm
- http://m.blog.ghtkgg.cn/nnews/835052.htm
- http://m.blog.ghtkgg.cn/nnews/151003.htm
- http://m.blog.ghtkgg.cn/nnews/873312.htm
- http://m.blog.ghtkgg.cn/nnews/70112.htm
- http://m.blog.ghtkgg.cn/nnews/9480.htm
- http://m.blog.ghtkgg.cn/nnews/5694408.htm
- http://m.blog.ghtkgg.cn/nnews/455446.htm
- http://m.blog.ghtkgg.cn/nnews/569850.htm
- http://m.blog.ghtkgg.cn/nnews/4901.htm
- http://m.blog.ghtkgg.cn/nnews/7740.htm
- http://m.blog.ghtkgg.cn/nnews/02799.htm
- http://m.blog.ghtkgg.cn/nnews/1551.htm
- http://m.blog.ghtkgg.cn/nnews/5097689.htm
- http://m.blog.ghtkgg.cn/nnews/26526.htm
- http://m.blog.ghtkgg.cn/nnews/474751.htm
- http://m.blog.ghtkgg.cn/nnews/8172.htm
- http://m.blog.ghtkgg.cn/nnews/3336280.htm
- http://m.blog.ghtkgg.cn/nnews/42449.htm
- http://m.blog.ghtkgg.cn/nnews/9731.htm
- http://m.blog.ghtkgg.cn/nnews/8004.htm
- http://m.blog.ghtkgg.cn/nnews/3667541.htm
- http://m.blog.ghtkgg.cn/nnews/479246.htm
- http://m.blog.ghtkgg.cn/nnews/60467.htm
- http://m.blog.ghtkgg.cn/nnews/2536.htm
- http://m.blog.ghtkgg.cn/nnews/51404.htm
- http://m.blog.ghtkgg.cn/nnews/5910610.htm
- http://m.blog.ghtkgg.cn/nnews/9106.htm
- http://m.blog.ghtkgg.cn/nnews/9671419.htm
- http://m.blog.ghtkgg.cn/nnews/9164179.htm
- http://m.blog.ghtkgg.cn/nnews/3236.htm
- http://m.blog.ghtkgg.cn/nnews/3140.htm
- http://m.blog.ghtkgg.cn/nnews/7874.htm
- http://m.blog.ghtkgg.cn/nnews/03333.htm
- http://m.blog.ghtkgg.cn/nnews/04941.htm
- http://m.blog.ghtkgg.cn/nnews/944209.htm
- http://m.blog.ghtkgg.cn/nnews/45790.htm
- http://m.blog.ghtkgg.cn/nnews/35463.htm
- http://m.blog.ghtkgg.cn/nnews/813445.htm
- http://m.blog.ghtkgg.cn/nnews/6226.htm
- http://m.blog.ghtkgg.cn/nnews/7794.htm
- http://m.blog.ghtkgg.cn/nnews/6379.htm
- http://m.blog.ghtkgg.cn/nnews/758939.htm
- http://m.blog.ghtkgg.cn/nnews/62168.htm
- http://m.blog.ghtkgg.cn/nnews/420098.htm
- http://m.blog.ghtkgg.cn/nnews/3014.htm
- http://m.blog.ghtkgg.cn/nnews/9629.htm
- http://m.blog.ghtkgg.cn/nnews/084904.htm
- http://m.blog.ghtkgg.cn/nnews/834792.htm
- http://m.blog.ghtkgg.cn/nnews/762648.htm
- http://m.blog.ghtkgg.cn/nnews/4390624.htm
- http://m.blog.ghtkgg.cn/nnews/87577.htm
- http://m.blog.ghtkgg.cn/nnews/2266425.htm
- http://m.blog.ghtkgg.cn/nnews/784947.htm

## 项目结构

```
newslink-navigator/
├── builder/                         # 静态页面生成核心模块
│   ├── __init__.py                  # 模块初始化，导出主要构建类
│   ├── generator.py                 # 主生成器，协调数据读取与模板渲染
│   ├── filters.py                   # 筛选器实现，支持标签、日期等多维度过滤
│   └── health_check.py              # 链接状态检测逻辑，并发请求与超时控制
├── data/                            # 数据存储与迁移目录
│   ├── source/                      # 原始输入数据存放位置（links.txt 等）
│   ├── db/                          # SQLite 数据库文件目录
│   │   └── newslink.db              # 默认数据库文件，包含 links 和 tags 表
│   └── migrations/                  # 数据库结构变更脚本
│       ├── 001_initial_schema.sql   # 初始化建表语句
│       └── 002_add_health_status.sql # 增加健康状态字段
├── scripts/                         # 运维与辅助脚本
│   ├── init_db.py                   # 初始化数据库与默认配置
│   ├── import_links.py              # 批量导入链接，支持去重与元数据补全
│   └── export_markdown.py           # 导出为 Markdown 表格格式
├── templates/                       # 页面模板目录
│   ├── default/                     # 默认模板主题
│   │   ├── index.html               # 导航主页模板
│   │   ├── card.html                # 卡片视图局部模板
│   │   └── list.html                # 列表视图局部模板
│   └── custom/                      # 用户自定义模板示例
│       └── dark_theme.css           # 暗色主题覆盖样式
├── output/                          # 生成的静态页面输出目录（可配置）
├── tests/                           # 单元测试与集成测试
│   ├── test_import.py               # 导入功能测试
│   ├── test_filters.py              # 筛选器单元测试
│   └── test_health.py               # 健康检查模块测试
├── docs/                            # 完整项目文档
│   ├── getting-started.md           # 入门指南
│   ├── data-management.md           # 数据管理详细说明
│   ├── customization.md             # 自定义与主题配置
│   └── operations.md                # 运维与故障排查
├── requirements.txt                 # Python 生产依赖列表
├── dev-requirements.txt             # 开发与测试额外依赖
├── pyproject.toml                   # 项目元数据与构建配置（Poetry）
├── README.md                        # 本文件
└── LICENSE                          # MIT 许可证文件
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并在本地克隆您 Fork 后的副本。创建新的功能分支（例如 `feature/improve-importer`）进行开发，避免直接修改主分支。

2. 确保开发环境已安装 Python 3.9 及以上版本，并使用 `pip install -r dev-requirements.txt` 安装开发依赖（包括 pytest、black、flake8）。所有新增代码应通过现有的单元测试，并为新增功能编写对应的测试用例。

3. 在提交 Pull Request 之前，请运行 `black .` 与 `flake8` 进行代码格式化与静态检查，确保代码风格与项目保持一致。提交信息应遵循 Conventional Commits 规范（如 `feat: add batch tag editor` 或 `fix: correct deduplication logic`）。

4. 若您希望新增模板主题或扩展数据导入格式，请先在 `docs/` 目录下更新对应的文档章节，并在 Pull Request 中附带简要的功能说明和使用示例。

5. 提交 Pull Request 至主仓库的 `main` 分支，并在描述中关联相关 Issue（如有）。项目维护者将在 2 个工作日内进行 Review，并给出合并或修改建议。

## 常见问题

**Q: 导入大量链接后，生成页面速度明显变慢，如何优化？**

A: 当链接数量超过 2000 条时，建议启用分页功能（在 `config.yaml` 中设置 `pagination: true` 并指定每页大小）。此外，可定期运行 `scripts/cleanup_duplicates.py` 清理冗余数据，并对数据库中的 `links` 表的 `title` 和 `tags` 字段建立索引以提升筛选速度。

**Q: 如何定期自动更新链接健康状态？**

A: 可使用系统 cron 任务（Linux/macOS）或计划任务（Windows）定时执行 `python builder/health_check.py --update-all`，并将结果输出至日志文件。项目也提供了 Prometheus 格式的指标暴露接口（参见 `docs/operations.md`），可接入监控告警系统。

**Q: 是否支持多用户编辑或 Web 管理界面？**

A: 当前版本为静态生成器，不包含 Web 管理后端。若需要多用户协作，建议将数据源（JSON 或 SQLite 文件）放置于 Nextcloud、Seafile 等同步盘，或使用 Git 进行版本控制，通过合并请求方式协同维护链接列表。计划在 v2.0 版本中提供基于 FastAPI 的轻量管理 API。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
