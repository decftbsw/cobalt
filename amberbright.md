# NewsLink Harvest

NewsLink Harvest 是一个面向技术资讯聚合与历史新闻存档检索的轻量化链接管理工具。项目定位为技术团队、内容研究者与个人知识管理者的外链数据中台，用于对批量新闻链接进行结构化存储、有效性检测、元数据提取与分类浏览。该项目解决的核心问题在于：大量散乱的新闻 URL 缺乏统一的整理入口，导致检索困难、链接失效不可知、无法按来源或时间维度进行二次分析。NewsLink Harvest 提供标准化的导入导出接口、定时健康检查机制以及标签化分类体系，帮助用户在三百级乃至更大批次的链接集合中维持数据整洁度与可用性。

## 功能概览

**批量链接导入与去重**：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，系统自动识别重复条目并生成去重报告。

**定时可用性检测**：内置异步任务调度器，可对已入库链接进行周期性 HTTP 状态码检查，标记失效链接并记录响应时间与重定向链。

**元数据自动提取**：对于新闻类链接，自动尝试提取标题、发布时间、正文摘要与来源站点信息，填充至数据库对应字段。

**标签与分类体系**：允许用户创建自定义标签树，对链接进行多维度标注，支持按标签组合进行快速筛选与统计。

**检索与过滤引擎**：提供基于标题、URL 片段、时间范围、状态码等多条件组合的查询接口，支持结果排序与分页。

**数据导入导出**：支持 JSON、CSV、Markdown 表格三种导出格式，方便对接其他分析工具或生成文档报告。

**状态看板与统计**：提供简洁的管理仪表盘，展示链接总数、失效比例、各来源站点分布、每日新增趋势等关键指标。

## 应用场景

技术团队内部知识库维护：团队可将日常阅读的技术新闻、产品更新公告、竞品动态链接统一录入 NewsLink Harvest，并标注所属项目或模块。后续复盘或撰写周报时，通过标签筛选即可快速定位特定时间段的全部参考资料。

历史新闻存档与溯源分析：内容研究者或媒体分析师可将大量历史新闻链接导入系统，利用元数据提取功能构建小型档案库。当需要追溯某一事件的时间线或报道来源时，可通过时间范围过滤和站点聚合功能快速生成分析清单。

个人阅读清单的定期健康检查：个人用户可将收藏的博客文章、教程链接或新闻评论存入系统。每周自动运行的可用性检测会标记出已失效的链接，用户可据此及时更新书签或寻找替代来源，避免长期积累的链接库变成死链坟场。

数据迁移前的链接盘点：在进行站点改版、CMS 迁移或静态站点生成器重构时，运维人员可先将所有旧站新闻链接导入 NewsLink Harvest，利用导出功能生成完整的链接清单与状态报告，便于规划重定向规则或校验新站链接覆盖率。

## 快速开始

以下步骤帮助您在本地环境中快速启动 NewsLink Harvest 实例。

```bash
# 克隆项目仓库至本地
git clone https://github.com/example/newslink-harvest.git

# 进入项目根目录
cd newslink-harvest

# 安装项目依赖（使用 pip 和 requirements.txt）
pip install -r requirements.txt

# 初始化 SQLite 数据库表结构
python manage.py migrate

# 启动开发服务器，默认监听 127.0.0.1:8000
python manage.py runserver
```

访问 http://127.0.0.1:8000/admin 即可进入管理后台，首次使用需通过 `python manage.py createsuperuser` 创建管理员账户。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 或更高 | 核心运行环境，低于此版本将无法解析类型注解与异步语法 |
| SQLite | 3.25 或更高 | 默认内嵌数据库，用于存储链接元数据与状态记录 |
| requests | 2.25.0 或更高 | 用于执行 HTTP 可用性检测与元数据提取中的页面抓取 |
| beautifulsoup4 | 4.9.0 或更高 | 用于解析新闻页面的 HTML 结构，提取标题与正文摘要 |
| lxml | 4.6.0 或更高 | 作为 beautifulsoup4 的解析器后端，提供更高效的 HTML 解析性能 |
| apscheduler | 3.7.0 或更高 | 提供定时任务调度能力，用于周期性执行链接健康检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何安装、配置并运行第一个链接导入任务 |
| 操作手册 | docs/usage.md | 如何进行链接导入、标签管理、检测任务配置与数据导出 |
| 接口参考 | docs/api.md | 提供哪些 RESTful API 端点，请求与响应格式为何 |
| 架构设计 | docs/architecture.md | 系统模块划分、数据流走向、异步任务队列设计思路 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/1183.htm
- http://m.3g.oexnr.cn/nnews/987662.htm
- http://m.3g.oexnr.cn/nnews/1252245.htm
- http://m.3g.oexnr.cn/nnews/9840814.htm
- http://m.3g.oexnr.cn/nnews/539354.htm
- http://m.3g.oexnr.cn/nnews/2585251.htm
- http://m.3g.oexnr.cn/nnews/179848.htm
- http://m.3g.oexnr.cn/nnews/5572054.htm
- http://m.3g.oexnr.cn/nnews/249879.htm
- http://m.3g.oexnr.cn/nnews/025424.htm
- http://m.3g.oexnr.cn/nnews/0882.htm
- http://m.3g.oexnr.cn/nnews/00394.htm
- http://m.3g.oexnr.cn/nnews/9759.htm
- http://m.3g.oexnr.cn/nnews/656164.htm
- http://m.3g.oexnr.cn/nnews/015388.htm
- http://m.3g.oexnr.cn/nnews/5482095.htm
- http://m.3g.oexnr.cn/nnews/465053.htm
- http://m.3g.oexnr.cn/nnews/83327.htm
- http://m.3g.oexnr.cn/nnews/344106.htm
- http://m.3g.oexnr.cn/nnews/6427.htm
- http://m.3g.oexnr.cn/nnews/25407.htm
- http://m.3g.oexnr.cn/nnews/818582.htm
- http://m.3g.oexnr.cn/nnews/2996.htm
- http://m.3g.oexnr.cn/nnews/6556613.htm
- http://m.3g.oexnr.cn/nnews/482588.htm
- http://m.3g.oexnr.cn/nnews/5721463.htm
- http://m.3g.oexnr.cn/nnews/1953.htm
- http://m.3g.oexnr.cn/nnews/66434.htm
- http://m.3g.oexnr.cn/nnews/4233.htm
- http://m.3g.oexnr.cn/nnews/7124.htm
- http://m.3g.oexnr.cn/nnews/0462.htm
- http://m.3g.oexnr.cn/nnews/8088893.htm
- http://m.3g.oexnr.cn/nnews/61916.htm
- http://m.3g.oexnr.cn/nnews/736863.htm
- http://m.3g.oexnr.cn/nnews/3465006.htm
- http://m.3g.oexnr.cn/nnews/6027.htm
- http://m.3g.oexnr.cn/nnews/5875.htm
- http://m.3g.oexnr.cn/nnews/6510809.htm
- http://m.3g.oexnr.cn/nnews/113925.htm
- http://m.3g.oexnr.cn/nnews/27985.htm
- http://m.3g.oexnr.cn/nnews/4135.htm
- http://m.3g.oexnr.cn/nnews/9845.htm
- http://m.3g.oexnr.cn/nnews/043544.htm
- http://m.3g.oexnr.cn/nnews/6685.htm
- http://m.3g.oexnr.cn/nnews/444099.htm
- http://m.3g.oexnr.cn/nnews/142329.htm
- http://m.3g.oexnr.cn/nnews/8003.htm
- http://m.3g.oexnr.cn/nnews/65263.htm
- http://m.3g.oexnr.cn/nnews/65418.htm
- http://m.3g.oexnr.cn/nnews/38072.htm
- http://m.3g.oexnr.cn/nnews/170008.htm
- http://m.3g.oexnr.cn/nnews/133375.htm
- http://m.3g.oexnr.cn/nnews/9244.htm
- http://m.3g.oexnr.cn/nnews/722131.htm
- http://m.3g.oexnr.cn/nnews/6292297.htm
- http://m.3g.oexnr.cn/nnews/6932949.htm
- http://m.3g.oexnr.cn/nnews/9364.htm
- http://m.3g.oexnr.cn/nnews/56985.htm
- http://m.3g.oexnr.cn/nnews/7171379.htm
- http://m.3g.oexnr.cn/nnews/1461083.htm
- http://m.3g.oexnr.cn/nnews/73178.htm
- http://m.3g.oexnr.cn/nnews/999219.htm
- http://m.3g.oexnr.cn/nnews/5692.htm
- http://m.3g.oexnr.cn/nnews/5365341.htm
- http://m.3g.oexnr.cn/nnews/9568224.htm
- http://m.3g.oexnr.cn/nnews/54867.htm
- http://m.3g.oexnr.cn/nnews/990723.htm
- http://m.3g.oexnr.cn/nnews/0775305.htm
- http://m.3g.oexnr.cn/nnews/2966696.htm
- http://m.3g.oexnr.cn/nnews/3350620.htm
- http://m.3g.oexnr.cn/nnews/960688.htm
- http://m.3g.oexnr.cn/nnews/27377.htm
- http://m.3g.oexnr.cn/nnews/25187.htm
- http://m.3g.oexnr.cn/nnews/1629.htm
- http://m.3g.oexnr.cn/nnews/834383.htm
- http://m.3g.oexnr.cn/nnews/829207.htm
- http://m.3g.oexnr.cn/nnews/4392868.htm
- http://m.3g.oexnr.cn/nnews/6357641.htm
- http://m.3g.oexnr.cn/nnews/6527040.htm
- http://m.3g.oexnr.cn/nnews/2259.htm
- http://m.3g.oexnr.cn/nnews/51034.htm
- http://m.3g.oexnr.cn/nnews/4136561.htm
- http://m.3g.oexnr.cn/nnews/5464727.htm
- http://m.3g.oexnr.cn/nnews/59985.htm
- http://m.3g.oexnr.cn/nnews/5617505.htm
- http://m.3g.oexnr.cn/nnews/381624.htm
- http://m.3g.oexnr.cn/nnews/338005.htm
- http://m.3g.oexnr.cn/nnews/4035.htm
- http://m.3g.oexnr.cn/nnews/1257987.htm
- http://m.3g.oexnr.cn/nnews/893940.htm
- http://m.3g.oexnr.cn/nnews/729294.htm
- http://m.3g.oexnr.cn/nnews/50619.htm
- http://m.3g.oexnr.cn/nnews/3553600.htm
- http://m.3g.oexnr.cn/nnews/7277298.htm
- http://m.3g.oexnr.cn/nnews/86304.htm
- http://m.3g.oexnr.cn/nnews/938306.htm
- http://m.3g.oexnr.cn/nnews/1236871.htm
- http://m.3g.oexnr.cn/nnews/6277347.htm
- http://m.3g.oexnr.cn/nnews/865647.htm
- http://m.3g.oexnr.cn/nnews/21977.htm
- http://m.3g.oexnr.cn/nnews/1632794.htm
- http://m.3g.oexnr.cn/nnews/203997.htm
- http://m.3g.oexnr.cn/nnews/1223.htm
- http://m.3g.oexnr.cn/nnews/5165.htm
- http://m.3g.oexnr.cn/nnews/4174.htm
- http://m.3g.oexnr.cn/nnews/8732790.htm
- http://m.3g.oexnr.cn/nnews/81810.htm
- http://m.3g.oexnr.cn/nnews/636174.htm
- http://m.3g.oexnr.cn/nnews/45067.htm
- http://m.3g.oexnr.cn/nnews/0167298.htm
- http://m.3g.oexnr.cn/nnews/5054288.htm
- http://m.3g.oexnr.cn/nnews/318550.htm
- http://m.3g.oexnr.cn/nnews/5192974.htm
- http://m.3g.oexnr.cn/nnews/6540154.htm
- http://m.3g.oexnr.cn/nnews/81287.htm
- http://m.3g.oexnr.cn/nnews/8616095.htm
- http://m.3g.oexnr.cn/nnews/2773.htm
- http://m.3g.oexnr.cn/nnews/085790.htm
- http://m.3g.oexnr.cn/nnews/6212.htm
- http://m.3g.oexnr.cn/nnews/720815.htm
- http://m.3g.oexnr.cn/nnews/5833851.htm
- http://m.3g.oexnr.cn/nnews/2628161.htm
- http://m.3g.oexnr.cn/nnews/9457.htm
- http://m.3g.oexnr.cn/nnews/4696.htm
- http://m.3g.oexnr.cn/nnews/7707478.htm
- http://m.3g.oexnr.cn/nnews/1727.htm
- http://m.3g.oexnr.cn/nnews/67223.htm
- http://m.3g.oexnr.cn/nnews/17393.htm
- http://m.3g.oexnr.cn/nnews/81093.htm
- http://m.3g.oexnr.cn/nnews/1161.htm
- http://m.3g.oexnr.cn/nnews/1590.htm
- http://m.3g.oexnr.cn/nnews/7646.htm
- http://m.3g.oexnr.cn/nnews/274907.htm
- http://m.3g.oexnr.cn/nnews/548316.htm
- http://m.3g.oexnr.cn/nnews/9085.htm
- http://m.3g.oexnr.cn/nnews/3599491.htm
- http://m.3g.oexnr.cn/nnews/08979.htm
- http://m.3g.oexnr.cn/nnews/9671.htm
- http://m.3g.oexnr.cn/nnews/3208423.htm
- http://m.3g.oexnr.cn/nnews/60228.htm
- http://m.3g.oexnr.cn/nnews/35504.htm
- http://m.3g.oexnr.cn/nnews/14357.htm
- http://m.3g.oexnr.cn/nnews/624510.htm
- http://m.3g.oexnr.cn/nnews/5144752.htm
- http://m.3g.oexnr.cn/nnews/742516.htm
- http://m.3g.oexnr.cn/nnews/3042.htm
- http://m.3g.oexnr.cn/nnews/1103881.htm
- http://m.3g.oexnr.cn/nnews/2099792.htm
- http://m.3g.oexnr.cn/nnews/07934.htm
- http://m.3g.oexnr.cn/nnews/444038.htm
- http://m.3g.oexnr.cn/nnews/03380.htm
- http://m.3g.oexnr.cn/nnews/8143.htm
- http://m.3g.oexnr.cn/nnews/9927.htm
- http://m.3g.oexnr.cn/nnews/5122.htm
- http://m.3g.oexnr.cn/nnews/728702.htm
- http://m.3g.oexnr.cn/nnews/1401802.htm
- http://m.3g.oexnr.cn/nnews/41498.htm
- http://m.3g.oexnr.cn/nnews/91858.htm
- http://m.3g.oexnr.cn/nnews/85322.htm
- http://m.3g.oexnr.cn/nnews/7832.htm
- http://m.3g.oexnr.cn/nnews/0181915.htm
- http://m.3g.oexnr.cn/nnews/7876622.htm
- http://m.3g.oexnr.cn/nnews/762067.htm
- http://m.3g.oexnr.cn/nnews/8344666.htm
- http://m.3g.oexnr.cn/nnews/95342.htm
- http://m.3g.oexnr.cn/nnews/409912.htm
- http://m.3g.oexnr.cn/nnews/6875870.htm
- http://m.3g.oexnr.cn/nnews/780754.htm
- http://m.3g.oexnr.cn/nnews/1883760.htm
- http://m.3g.oexnr.cn/nnews/8712.htm
- http://m.3g.oexnr.cn/nnews/89741.htm
- http://m.3g.oexnr.cn/nnews/97949.htm
- http://m.3g.oexnr.cn/nnews/99632.htm
- http://m.3g.oexnr.cn/nnews/78621.htm
- http://m.3g.oexnr.cn/nnews/89358.htm
- http://m.3g.oexnr.cn/nnews/6247.htm
- http://m.3g.oexnr.cn/nnews/6915046.htm
- http://m.3g.oexnr.cn/nnews/7402873.htm
- http://m.3g.oexnr.cn/nnews/38289.htm
- http://m.3g.oexnr.cn/nnews/39220.htm
- http://m.3g.oexnr.cn/nnews/33015.htm
- http://m.3g.oexnr.cn/nnews/2797.htm
- http://m.3g.oexnr.cn/nnews/5289388.htm
- http://m.3g.oexnr.cn/nnews/19791.htm
- http://m.3g.oexnr.cn/nnews/4462.htm
- http://m.3g.oexnr.cn/nnews/9862.htm
- http://m.3g.oexnr.cn/nnews/8714.htm
- http://m.3g.oexnr.cn/nnews/066899.htm
- http://m.3g.oexnr.cn/nnews/6141895.htm
- http://m.3g.oexnr.cn/nnews/989007.htm
- http://m.3g.oexnr.cn/nnews/9179748.htm
- http://m.3g.oexnr.cn/nnews/4154.htm
- http://m.3g.oexnr.cn/nnews/236128.htm
- http://m.3g.oexnr.cn/nnews/06779.htm
- http://m.3g.oexnr.cn/nnews/39351.htm
- http://m.3g.oexnr.cn/nnews/75296.htm
- http://m.3g.oexnr.cn/nnews/1700699.htm
- http://m.3g.oexnr.cn/nnews/5600.htm
- http://m.3g.oexnr.cn/nnews/2216.htm
- http://m.3g.oexnr.cn/nnews/8868487.htm
- http://m.3g.oexnr.cn/nnews/6024.htm
- http://m.3g.oexnr.cn/nnews/404548.htm
- http://m.3g.oexnr.cn/nnews/7841601.htm
- http://m.3g.oexnr.cn/nnews/46737.htm
- http://m.3g.oexnr.cn/nnews/70964.htm
- http://m.3g.oexnr.cn/nnews/1153.htm
- http://m.3g.oexnr.cn/nnews/583963.htm
- http://m.3g.oexnr.cn/nnews/77474.htm
- http://m.3g.oexnr.cn/nnews/2304094.htm
- http://m.3g.oexnr.cn/nnews/7438.htm
- http://m.3g.oexnr.cn/nnews/94131.htm
- http://m.3g.oexnr.cn/nnews/7780.htm
- http://m.3g.oexnr.cn/nnews/45250.htm
- http://m.3g.oexnr.cn/nnews/604725.htm
- http://m.3g.oexnr.cn/nnews/355641.htm
- http://m.3g.oexnr.cn/nnews/9261.htm
- http://m.3g.oexnr.cn/nnews/1157746.htm
- http://m.3g.oexnr.cn/nnews/2318.htm
- http://m.3g.oexnr.cn/nnews/8211334.htm
- http://m.3g.oexnr.cn/nnews/070802.htm
- http://m.3g.oexnr.cn/nnews/0230.htm
- http://m.3g.oexnr.cn/nnews/93941.htm
- http://m.3g.oexnr.cn/nnews/1358.htm
- http://m.3g.oexnr.cn/nnews/6832.htm
- http://m.3g.oexnr.cn/nnews/655102.htm
- http://m.3g.oexnr.cn/nnews/45770.htm
- http://m.3g.oexnr.cn/nnews/4980707.htm
- http://m.3g.oexnr.cn/nnews/833201.htm
- http://m.3g.oexnr.cn/nnews/099650.htm
- http://m.3g.oexnr.cn/nnews/7476924.htm
- http://m.3g.oexnr.cn/nnews/0398656.htm
- http://m.3g.oexnr.cn/nnews/97122.htm
- http://m.3g.oexnr.cn/nnews/6884530.htm
- http://m.3g.oexnr.cn/nnews/3045251.htm
- http://m.3g.oexnr.cn/nnews/28854.htm
- http://m.3g.oexnr.cn/nnews/5461708.htm
- http://m.3g.oexnr.cn/nnews/3936391.htm
- http://m.3g.oexnr.cn/nnews/7569399.htm
- http://m.3g.oexnr.cn/nnews/16944.htm
- http://m.3g.oexnr.cn/nnews/96068.htm
- http://m.3g.oexnr.cn/nnews/97383.htm
- http://m.3g.oexnr.cn/nnews/11813.htm
- http://m.3g.oexnr.cn/nnews/987516.htm
- http://m.3g.oexnr.cn/nnews/0961894.htm
- http://m.3g.oexnr.cn/nnews/8197100.htm
- http://m.3g.oexnr.cn/nnews/58353.htm
- http://m.3g.oexnr.cn/nnews/766450.htm
- http://m.3g.oexnr.cn/nnews/5404.htm
- http://m.3g.oexnr.cn/nnews/6507.htm
- http://m.3g.oexnr.cn/nnews/783353.htm
- http://m.3g.oexnr.cn/nnews/801569.htm
- http://m.3g.oexnr.cn/nnews/57167.htm
- http://m.3g.oexnr.cn/nnews/3216595.htm
- http://m.3g.oexnr.cn/nnews/2627.htm
- http://m.3g.oexnr.cn/nnews/589564.htm
- http://m.3g.oexnr.cn/nnews/4554341.htm
- http://m.3g.oexnr.cn/nnews/5427.htm
- http://m.3g.oexnr.cn/nnews/83917.htm
- http://m.3g.oexnr.cn/nnews/8921.htm
- http://m.3g.oexnr.cn/nnews/26045.htm
- http://m.3g.oexnr.cn/nnews/8466905.htm
- http://m.3g.oexnr.cn/nnews/039781.htm
- http://m.3g.oexnr.cn/nnews/997330.htm
- http://m.3g.oexnr.cn/nnews/9744.htm
- http://m.3g.oexnr.cn/nnews/227274.htm
- http://m.3g.oexnr.cn/nnews/68982.htm
- http://m.3g.oexnr.cn/nnews/099265.htm
- http://m.3g.oexnr.cn/nnews/54936.htm
- http://m.3g.oexnr.cn/nnews/289033.htm
- http://m.3g.oexnr.cn/nnews/2135.htm
- http://m.3g.oexnr.cn/nnews/841071.htm
- http://m.3g.oexnr.cn/nnews/48027.htm
- http://m.3g.oexnr.cn/nnews/20942.htm
- http://m.3g.oexnr.cn/nnews/871595.htm
- http://m.3g.oexnr.cn/nnews/771913.htm
- http://m.3g.oexnr.cn/nnews/256372.htm
- http://m.3g.oexnr.cn/nnews/390572.htm
- http://m.3g.oexnr.cn/nnews/8202579.htm
- http://m.3g.oexnr.cn/nnews/2565.htm
- http://m.3g.oexnr.cn/nnews/26203.htm
- http://m.3g.oexnr.cn/nnews/3910.htm
- http://m.3g.oexnr.cn/nnews/2104238.htm
- http://m.3g.oexnr.cn/nnews/67452.htm
- http://m.3g.oexnr.cn/nnews/65429.htm
- http://m.3g.oexnr.cn/nnews/83943.htm
- http://m.3g.oexnr.cn/nnews/7595.htm
- http://m.3g.oexnr.cn/nnews/9123.htm
- http://m.3g.oexnr.cn/nnews/6410121.htm
- http://m.3g.oexnr.cn/nnews/2745122.htm
- http://m.3g.oexnr.cn/nnews/5459.htm
- http://m.3g.oexnr.cn/nnews/8295.htm
- http://m.3g.oexnr.cn/nnews/9606007.htm
- http://m.3g.oexnr.cn/nnews/0004.htm
- http://m.3g.oexnr.cn/nnews/186071.htm
- http://m.3g.oexnr.cn/nnews/4162178.htm
- http://m.3g.oexnr.cn/nnews/12837.htm
- http://m.3g.oexnr.cn/nnews/5636054.htm
- http://m.3g.oexnr.cn/nnews/781581.htm
- http://m.3g.oexnr.cn/nnews/8525.htm
- http://m.3g.oexnr.cn/nnews/9525731.htm

## 项目结构

```
newslink-harvest/
├── manage.py                 # 项目管理入口，用于启动服务与执行命令行操作
├── requirements.txt          # 声明所有 Python 依赖及其版本约束
├── config/                   # 全局配置模块
│   ├── settings.py           # Django 基础配置，包含数据库、中间件、时区等
│   ├── celery.py             # Celery 应用定义，用于配置异步任务队列
│   └── urls.py               # 根路由映射，挂载 admin 与 api 子路由
├── apps/                     # 所有功能模块按应用拆分存放
│   ├── core/                 # 核心数据模型与基础管理器
│   │   ├── models.py         # 定义 Link, Tag, CheckRecord 等数据库模型
│   │   ├── managers.py       # 自定义查询集，封装常用过滤与统计方法
│   │   └── validators.py     # URL 格式校验、域名黑名单等校验逻辑
│   ├── importer/             # 链接导入模块，支持多种数据源
│   │   ├── parsers.py        # CSV、JSON、纯文本列表解析器实现
│   │   └── tasks.py          # 导入任务的异步执行入口
│   ├── checker/              # 链接健康检查模块
│   │   ├── client.py         # 封装 requests 会话，配置超时与重试策略
│   │   ├── scheduler.py      # 定义定时任务调度规则（每日凌晨与每周全量）
│   │   └── signals.py        # 检查完成后触发状态变更信号
│   ├── metadata/             # 元数据提取模块
│   │   ├── extractors.py     # 基于 beautifulsoup 的标题、时间、摘要提取器
│   │   └── processors.py     # 提取结果的后处理，如日期标准化与文本清洗
│   ├── api/                  # RESTful API 模块
│   │   ├── views.py          # 基于 Django REST Framework 的视图集
│   │   ├── serializers.py    # 模型序列化器，控制输入输出字段
│   │   └── routers.py        # 自动注册 ViewSet 路由
│   └── dashboard/            # 管理看板模块
│       ├── views.py          # 仪表盘统计视图，返回聚合指标数据
│       └── templates/        # 管理界面 HTML 模板文件
├── tests/                    # 单元测试与集成测试目录
│   ├── test_models.py        # 数据模型层测试用例
│   ├── test_checker.py       # 可用性检测逻辑测试，含 mock 外部请求
│   └── test_api.py           # API 端点响应与权限测试
├── scripts/                  # 运维与辅助脚本
│   ├── export_links.py       # 按条件导出链接数据的命令行工具
│   └── import_batch.py       # 批量导入指定路径文件的命令行工具
└── docs/                     # 文档源文件，使用 Markdown 编写
    ├── quickstart.md
    ├── usage.md
    ├── api.md
    └── architecture.md
```

## 贡献指南

1. 在 GitHub 上 fork 本项目至个人账户，随后 clone 到本地开发环境。建议在 dev 分支上进行所有改动，避免直接操作 main 分支。

2. 创建新的功能分支或修复分支，命名遵循 `feature/功能简述` 或 `fix/问题简述` 的格式。确保所有代码变更均附带对应的单元测试，测试覆盖率达到百分之八十以上。

3. 运行完整的测试套件 `python manage.py test` 确保本地所有测试通过，同时使用 `flake8` 和 `black` 进行代码风格检查与自动格式化，保持与项目现有风格一致。

4. 提交 pull request 至 main 分支，在 PR 描述中清晰说明改动目的、影响范围以及是否包含数据库迁移文件。项目维护者将在两个工作日内进行 Review。

5. 若涉及新增依赖或修改配置变量，请在 PR 中同步更新 `requirements.txt` 与 `config/settings.py` 的注释说明，并在文档目录下补充相应的配置示例。

## 常见问题

**Q：导入包含上千条链接的文件时，页面响应很慢甚至超时，应如何解决？**

A：系统默认将超过 100 条记录的导入任务自动转由后台异步队列执行，前端立即返回任务 ID 并提示“导入中”。您可在管理看板的“任务中心”查看进度。若仍需同步导入，请在 `config/settings.py` 中将 `IMPORTER_SYNC_THRESHOLD` 调大，但不建议超过 500 条，以免阻塞请求线程。

**Q：定时健康检查是否会频繁请求外部站点，导致我的 IP 被目标网站封禁？**

A：检查模块默认启用礼貌爬取策略，包括设置 `requests.Session` 的 `headers` 模拟主流浏览器、请求间隔随机延迟（2 至 5 秒）以及单次超时限制（10 秒）。同时支持在 `config/settings.py` 中配置 `CHECKER_WHITELIST_DOMAINS` 与 `CHECKER_BLACKLIST_DOMAINS`，可针对特定站点单独调整检查频率或完全跳过检查。

**Q：元数据提取对于不同新闻网站的兼容性如何，能否保证百分百准确？**

A：元数据提取器内置了针对常见 CMS 系统（如 WordPress、Drupal、自定义门户）的通用规则，优先从 `<article>` 标签、`og:title` 属性、`meta[name="pubdate"]` 等常见位置抽取信息。对于结构特殊的页面，提取器会降级返回整页标题与首段文本，并标记 `extraction_confidence` 字段为低置信度。您可通过 API 手动修正单条记录的元数据，或提交自定义提取规则 PR 以增强对特定站点的支持。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
