# JNews Resource Aggregator

JNews Resource Aggregator 是一个面向移动端新闻资讯整合的开源外链管理平台，专注于对分散式新闻源链接进行系统化收集、分类存储与快速检索。该项目主要服务于内容运营人员、个人站长以及新闻聚合类应用开发者，帮助其从零散的手动维护模式切换至结构化、可扩展的自动化资源管理流程。

项目本身不存储任何新闻正文或多媒体文件，仅维护指向原始新闻页面的标准超链接。通过将第 161/300 批共计 300 个新闻外链纳入统一索引体系，该平台提供基础的去重校验、时效性标记以及分类标签附着能力，使得大量历史新闻链接可以被高效组织与回溯。对于需要长期跟踪特定新闻源动态或构建轻量级新闻存档系统的团队，本项目提供了一套开箱即用的外链管理参考实现。

## 功能概览

批量外链导入：支持通过命令行脚本或 Web 表单将大量新闻 URL 一次性写入索引库，自动完成协议头校验与重复条目过滤。

时效性自动标记：依据链接采集时间戳与当前系统时间差，为每条外链自动附加"最新"、"普通"、"归档"三级时效标签，便于后续筛选与清理。

分类标签系统：允许用户为每条新闻链接定义多个自定义标签，例如"科技"、"财经"、"社会"等，实现跨维度的资源分组管理。

快速全文检索：基于内置的倒排索引机制，支持对新闻链接的标题、来源域名以及描述字段进行毫秒级关键词匹配查询。

资源访问状态监控：定期对索引库中的外链执行可用性探测，自动标记无法访问或响应超时的链接，并提供可视化状态仪表盘。

数据导入导出：支持将全部或筛选后的链接列表导出为标准 CSV 与 JSON 格式，也支持从外部 CSV 文件批量追加新链接至索引库。

访问统计与热度排序：记录每条外链在平台内的点击次数与最近访问时间，支持按热度或时间降序排列输出结果。

## 应用场景

个人站长构建垂直领域新闻导航站：运营者可将本项目作为后台数据管理核心，定期导入特定领域（如数码评测或汽车资讯）的新闻链接，通过分类标签系统生成不同主题的导航页面，为站点访客提供集中的外链跳转入口。

内容运营团队进行竞品动态跟踪：市场或运营人员可将竞品相关的新闻报道链接统一录入平台，利用时效性标签快速定位最新发布的内容，减少在多个新闻站点间反复切换搜索的时间成本。

新闻聚合类应用的后端开发测试：开发者在构建自有新闻聚合应用原型时，可使用本项目提供的标准化外链数据集作为模拟数据源，测试应用的数据抓取、解析与展示流程是否正常运作。

历史新闻归档与回顾系统搭建：对于需要长期保存特定事件或主题新闻报道记录的机构，本项目可作为基础索引框架，将分散的历史链接条目化，配合访问状态监控功能及时发现失效链接并采取补救措施。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目仓库、安装必要依赖并启动本地开发服务器。请确保在执行前已满足安装要求章节列出的所有依赖。

```bash
git clone https://github.com/your-org/jnews-resource-aggregator.git
cd jnews-resource-aggregator
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py load_initial_data
python manage.py runserver
```

若使用 Docker 部署，可以执行以下简化流程：

```bash
docker-compose up -d
docker-compose exec app python manage.py load_initial_data
```

服务启动后，访问 http://127.0.0.1:8000 即可进入管理界面。首次登录需使用初始化时生成的管理员凭证，具体请查看控制台输出或 .env 文件中的默认账户配置。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 或更高版本 | 核心运行环境，用于启动后端服务与执行管理命令 |
| PostgreSQL | 13 或更高版本 | 生产环境推荐的主数据库，用于存储外链索引与元数据 |
| Redis | 6 或更高版本 | 用于缓存高频查询结果与存储临时会话数据 |
| Node.js | 16 或更高版本 | 仅在前端静态资源构建时使用，运行时可免安装 |
| pip | 22 或更高版本 | Python 包依赖管理工具，用于安装 requirements.txt 中的库 |
| Docker | 20.10 或更高版本 | 可选依赖，用于容器化部署与开发环境隔离 |
| git | 2.25 或更高版本 | 用于克隆仓库及版本控制操作 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速搭建开发环境？首次启动需要执行哪些初始化操作？ |
| 数据管理 | docs/data-management.md | 如何批量导入外链？如何定义分类标签？数据导出格式有哪些选项？ |
| 运维手册 | docs/operations.md | 如何进行生产环境部署？外链状态监控的频率与告警阈值如何配置？ |
| API 参考 | docs/api-reference.md | 平台提供了哪些 RESTful API 端点？请求与响应的数据结构是什么？ |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/7779994.htm
- http://m.wap.ghtkgg.cn/jnews/452188.htm
- http://m.wap.ghtkgg.cn/jnews/1878.htm
- http://m.wap.ghtkgg.cn/jnews/8993.htm
- http://m.wap.ghtkgg.cn/jnews/77434.htm
- http://m.wap.ghtkgg.cn/jnews/3546247.htm
- http://m.wap.ghtkgg.cn/jnews/49685.htm
- http://m.wap.ghtkgg.cn/jnews/058855.htm
- http://m.wap.ghtkgg.cn/jnews/11922.htm
- http://m.wap.ghtkgg.cn/jnews/65030.htm
- http://m.wap.ghtkgg.cn/jnews/55648.htm
- http://m.wap.ghtkgg.cn/jnews/47975.htm
- http://m.wap.ghtkgg.cn/jnews/570468.htm
- http://m.wap.ghtkgg.cn/jnews/8997700.htm
- http://m.wap.ghtkgg.cn/jnews/476783.htm
- http://m.wap.ghtkgg.cn/jnews/43633.htm
- http://m.wap.ghtkgg.cn/jnews/114428.htm
- http://m.wap.ghtkgg.cn/jnews/28715.htm
- http://m.wap.ghtkgg.cn/jnews/55733.htm
- http://m.wap.ghtkgg.cn/jnews/04614.htm
- http://m.wap.ghtkgg.cn/jnews/2713.htm
- http://m.wap.ghtkgg.cn/jnews/5861213.htm
- http://m.wap.ghtkgg.cn/jnews/072327.htm
- http://m.wap.ghtkgg.cn/jnews/4267.htm
- http://m.wap.ghtkgg.cn/jnews/97248.htm
- http://m.wap.ghtkgg.cn/jnews/59503.htm
- http://m.wap.ghtkgg.cn/jnews/06374.htm
- http://m.wap.ghtkgg.cn/jnews/8955.htm
- http://m.wap.ghtkgg.cn/jnews/37851.htm
- http://m.wap.ghtkgg.cn/jnews/09981.htm
- http://m.wap.ghtkgg.cn/jnews/95753.htm
- http://m.wap.ghtkgg.cn/jnews/14724.htm
- http://m.wap.ghtkgg.cn/jnews/53851.htm
- http://m.wap.ghtkgg.cn/jnews/74485.htm
- http://m.wap.ghtkgg.cn/jnews/9753834.htm
- http://m.wap.ghtkgg.cn/jnews/8537332.htm
- http://m.wap.ghtkgg.cn/jnews/372613.htm
- http://m.wap.ghtkgg.cn/jnews/925393.htm
- http://m.wap.ghtkgg.cn/jnews/214569.htm
- http://m.wap.ghtkgg.cn/jnews/051307.htm
- http://m.wap.ghtkgg.cn/jnews/95104.htm
- http://m.wap.ghtkgg.cn/jnews/9309.htm
- http://m.wap.ghtkgg.cn/jnews/41633.htm
- http://m.wap.ghtkgg.cn/jnews/13904.htm
- http://m.wap.ghtkgg.cn/jnews/669779.htm
- http://m.wap.ghtkgg.cn/jnews/641574.htm
- http://m.wap.ghtkgg.cn/jnews/9988.htm
- http://m.wap.ghtkgg.cn/jnews/246204.htm
- http://m.wap.ghtkgg.cn/jnews/1159501.htm
- http://m.wap.ghtkgg.cn/jnews/9659.htm
- http://m.wap.ghtkgg.cn/jnews/600067.htm
- http://m.wap.ghtkgg.cn/jnews/6480132.htm
- http://m.wap.ghtkgg.cn/jnews/9704.htm
- http://m.wap.ghtkgg.cn/jnews/0703.htm
- http://m.wap.ghtkgg.cn/jnews/1360.htm
- http://m.wap.ghtkgg.cn/jnews/65843.htm
- http://m.wap.ghtkgg.cn/jnews/511858.htm
- http://m.wap.ghtkgg.cn/jnews/1437.htm
- http://m.wap.ghtkgg.cn/jnews/47356.htm
- http://m.wap.ghtkgg.cn/jnews/033690.htm
- http://m.wap.ghtkgg.cn/jnews/34077.htm
- http://m.wap.ghtkgg.cn/jnews/67161.htm
- http://m.wap.ghtkgg.cn/jnews/8253.htm
- http://m.wap.ghtkgg.cn/jnews/3947640.htm
- http://m.wap.ghtkgg.cn/jnews/9140871.htm
- http://m.wap.ghtkgg.cn/jnews/00300.htm
- http://m.wap.ghtkgg.cn/jnews/1012.htm
- http://m.wap.ghtkgg.cn/jnews/2933.htm
- http://m.wap.ghtkgg.cn/jnews/34100.htm
- http://m.wap.ghtkgg.cn/jnews/92522.htm
- http://m.wap.ghtkgg.cn/jnews/4702646.htm
- http://m.wap.ghtkgg.cn/jnews/7269.htm
- http://m.wap.ghtkgg.cn/jnews/3638.htm
- http://m.wap.ghtkgg.cn/jnews/1706.htm
- http://m.wap.ghtkgg.cn/jnews/671914.htm
- http://m.wap.ghtkgg.cn/jnews/2672.htm
- http://m.wap.ghtkgg.cn/jnews/1911.htm
- http://m.wap.ghtkgg.cn/jnews/68175.htm
- http://m.wap.ghtkgg.cn/jnews/30159.htm
- http://m.wap.ghtkgg.cn/jnews/875369.htm
- http://m.wap.ghtkgg.cn/jnews/38274.htm
- http://m.wap.ghtkgg.cn/jnews/5989653.htm
- http://m.wap.ghtkgg.cn/jnews/3955721.htm
- http://m.wap.ghtkgg.cn/jnews/323427.htm
- http://m.wap.ghtkgg.cn/jnews/489874.htm
- http://m.wap.ghtkgg.cn/jnews/3379.htm
- http://m.wap.ghtkgg.cn/jnews/2941.htm
- http://m.wap.ghtkgg.cn/jnews/4819181.htm
- http://m.wap.ghtkgg.cn/jnews/9581.htm
- http://m.wap.ghtkgg.cn/jnews/162826.htm
- http://m.wap.ghtkgg.cn/jnews/3170.htm
- http://m.wap.ghtkgg.cn/jnews/3506.htm
- http://m.wap.ghtkgg.cn/jnews/7576.htm
- http://m.wap.ghtkgg.cn/jnews/6596.htm
- http://m.wap.ghtkgg.cn/jnews/00305.htm
- http://m.wap.ghtkgg.cn/jnews/31870.htm
- http://m.wap.ghtkgg.cn/jnews/484905.htm
- http://m.wap.ghtkgg.cn/jnews/83760.htm
- http://m.wap.ghtkgg.cn/jnews/42023.htm
- http://m.wap.ghtkgg.cn/jnews/958978.htm
- http://m.wap.ghtkgg.cn/jnews/2324623.htm
- http://m.wap.ghtkgg.cn/jnews/37002.htm
- http://m.wap.ghtkgg.cn/jnews/21251.htm
- http://m.wap.ghtkgg.cn/jnews/68349.htm
- http://m.wap.ghtkgg.cn/jnews/48465.htm
- http://m.wap.ghtkgg.cn/jnews/5767649.htm
- http://m.wap.ghtkgg.cn/jnews/515550.htm
- http://m.wap.ghtkgg.cn/jnews/409063.htm
- http://m.wap.ghtkgg.cn/jnews/140912.htm
- http://m.wap.ghtkgg.cn/jnews/6295.htm
- http://m.wap.ghtkgg.cn/jnews/601762.htm
- http://m.wap.ghtkgg.cn/jnews/706013.htm
- http://m.wap.ghtkgg.cn/jnews/08507.htm
- http://m.wap.ghtkgg.cn/jnews/9623852.htm
- http://m.wap.ghtkgg.cn/jnews/1728454.htm
- http://m.wap.ghtkgg.cn/jnews/7473786.htm
- http://m.wap.ghtkgg.cn/jnews/6981.htm
- http://m.wap.ghtkgg.cn/jnews/13461.htm
- http://m.wap.ghtkgg.cn/jnews/95084.htm
- http://m.wap.ghtkgg.cn/jnews/7267967.htm
- http://m.wap.ghtkgg.cn/jnews/9103060.htm
- http://m.wap.ghtkgg.cn/jnews/0272603.htm
- http://m.wap.ghtkgg.cn/jnews/36844.htm
- http://m.wap.ghtkgg.cn/jnews/3726.htm
- http://m.wap.ghtkgg.cn/jnews/465177.htm
- http://m.wap.ghtkgg.cn/jnews/77734.htm
- http://m.wap.ghtkgg.cn/jnews/0153.htm
- http://m.wap.ghtkgg.cn/jnews/1729363.htm
- http://m.wap.ghtkgg.cn/jnews/39615.htm
- http://m.wap.ghtkgg.cn/jnews/648419.htm
- http://m.wap.ghtkgg.cn/jnews/251387.htm
- http://m.wap.ghtkgg.cn/jnews/144448.htm
- http://m.wap.ghtkgg.cn/jnews/9609556.htm
- http://m.wap.ghtkgg.cn/jnews/698556.htm
- http://m.wap.ghtkgg.cn/jnews/3231.htm
- http://m.wap.ghtkgg.cn/jnews/5017516.htm
- http://m.wap.ghtkgg.cn/jnews/753450.htm
- http://m.wap.ghtkgg.cn/jnews/8493.htm
- http://m.wap.ghtkgg.cn/jnews/72833.htm
- http://m.wap.ghtkgg.cn/jnews/221130.htm
- http://m.wap.ghtkgg.cn/jnews/26070.htm
- http://m.wap.ghtkgg.cn/jnews/4776.htm
- http://m.wap.ghtkgg.cn/jnews/8316.htm
- http://m.wap.ghtkgg.cn/jnews/219534.htm
- http://m.wap.ghtkgg.cn/jnews/6951125.htm
- http://m.wap.ghtkgg.cn/jnews/3565194.htm
- http://m.wap.ghtkgg.cn/jnews/3745741.htm
- http://m.wap.ghtkgg.cn/jnews/07403.htm
- http://m.wap.ghtkgg.cn/jnews/27622.htm
- http://m.wap.ghtkgg.cn/jnews/44831.htm
- http://m.wap.ghtkgg.cn/jnews/35730.htm
- http://m.wap.ghtkgg.cn/jnews/6547639.htm
- http://m.wap.ghtkgg.cn/jnews/73768.htm
- http://m.wap.ghtkgg.cn/jnews/0080546.htm
- http://m.wap.ghtkgg.cn/jnews/86381.htm
- http://m.wap.ghtkgg.cn/jnews/90659.htm
- http://m.wap.ghtkgg.cn/jnews/8514176.htm
- http://m.wap.ghtkgg.cn/jnews/0775555.htm
- http://m.wap.ghtkgg.cn/jnews/8453.htm
- http://m.wap.ghtkgg.cn/jnews/0560439.htm
- http://m.wap.ghtkgg.cn/jnews/999629.htm
- http://m.wap.ghtkgg.cn/jnews/728436.htm
- http://m.wap.ghtkgg.cn/jnews/5091.htm
- http://m.wap.ghtkgg.cn/jnews/49398.htm
- http://m.wap.ghtkgg.cn/jnews/94095.htm
- http://m.wap.ghtkgg.cn/jnews/3712926.htm
- http://m.wap.ghtkgg.cn/jnews/155916.htm
- http://m.wap.ghtkgg.cn/jnews/2502.htm
- http://m.wap.ghtkgg.cn/jnews/309767.htm
- http://m.wap.ghtkgg.cn/jnews/6763928.htm
- http://m.wap.ghtkgg.cn/jnews/7420.htm
- http://m.wap.ghtkgg.cn/jnews/7837.htm
- http://m.wap.ghtkgg.cn/jnews/50649.htm
- http://m.wap.ghtkgg.cn/jnews/3364.htm
- http://m.wap.ghtkgg.cn/jnews/54357.htm
- http://m.wap.ghtkgg.cn/jnews/2624.htm
- http://m.wap.ghtkgg.cn/jnews/358312.htm
- http://m.wap.ghtkgg.cn/jnews/891862.htm
- http://m.wap.ghtkgg.cn/jnews/411298.htm
- http://m.wap.ghtkgg.cn/jnews/1946987.htm
- http://m.wap.ghtkgg.cn/jnews/1706589.htm
- http://m.wap.ghtkgg.cn/jnews/27463.htm
- http://m.wap.ghtkgg.cn/jnews/98012.htm
- http://m.wap.ghtkgg.cn/jnews/7396.htm
- http://m.wap.ghtkgg.cn/jnews/00485.htm
- http://m.wap.ghtkgg.cn/jnews/6072271.htm
- http://m.wap.ghtkgg.cn/jnews/3128965.htm
- http://m.wap.ghtkgg.cn/jnews/3574922.htm
- http://m.wap.ghtkgg.cn/jnews/4207084.htm
- http://m.wap.ghtkgg.cn/jnews/3948.htm
- http://m.wap.ghtkgg.cn/jnews/693351.htm
- http://m.wap.ghtkgg.cn/jnews/4664157.htm
- http://m.wap.ghtkgg.cn/jnews/0426.htm
- http://m.wap.ghtkgg.cn/jnews/5603.htm
- http://m.wap.ghtkgg.cn/jnews/966153.htm
- http://m.wap.ghtkgg.cn/jnews/41971.htm
- http://m.wap.ghtkgg.cn/jnews/5263422.htm
- http://m.wap.ghtkgg.cn/jnews/88050.htm
- http://m.wap.ghtkgg.cn/jnews/771174.htm
- http://m.wap.ghtkgg.cn/jnews/0089900.htm
- http://m.wap.ghtkgg.cn/jnews/359420.htm
- http://m.wap.ghtkgg.cn/jnews/6534502.htm
- http://m.wap.ghtkgg.cn/jnews/96949.htm
- http://m.wap.ghtkgg.cn/jnews/3024837.htm
- http://m.wap.ghtkgg.cn/jnews/8627238.htm
- http://m.wap.ghtkgg.cn/jnews/072886.htm
- http://m.wap.ghtkgg.cn/jnews/6357.htm
- http://m.wap.ghtkgg.cn/jnews/1843441.htm
- http://m.wap.ghtkgg.cn/jnews/05278.htm
- http://m.wap.ghtkgg.cn/jnews/9955.htm
- http://m.wap.ghtkgg.cn/jnews/054421.htm
- http://m.wap.ghtkgg.cn/jnews/4858309.htm
- http://m.wap.ghtkgg.cn/jnews/874533.htm
- http://m.wap.ghtkgg.cn/jnews/4494562.htm
- http://m.wap.ghtkgg.cn/jnews/750598.htm
- http://m.wap.ghtkgg.cn/jnews/70902.htm
- http://m.wap.ghtkgg.cn/jnews/8122.htm
- http://m.wap.ghtkgg.cn/jnews/6913483.htm
- http://m.wap.ghtkgg.cn/jnews/9588902.htm
- http://m.wap.ghtkgg.cn/jnews/2611.htm
- http://m.wap.ghtkgg.cn/jnews/12864.htm
- http://m.wap.ghtkgg.cn/jnews/911925.htm
- http://m.wap.ghtkgg.cn/jnews/9508.htm
- http://m.wap.ghtkgg.cn/jnews/96154.htm
- http://m.wap.ghtkgg.cn/jnews/109602.htm
- http://m.wap.ghtkgg.cn/jnews/22699.htm
- http://m.wap.ghtkgg.cn/jnews/5069.htm
- http://m.wap.ghtkgg.cn/jnews/120986.htm
- http://m.wap.ghtkgg.cn/jnews/60627.htm
- http://m.wap.ghtkgg.cn/jnews/50611.htm
- http://m.wap.ghtkgg.cn/jnews/8792.htm
- http://m.wap.ghtkgg.cn/jnews/57350.htm
- http://m.wap.ghtkgg.cn/jnews/2264.htm
- http://m.wap.ghtkgg.cn/jnews/8051.htm
- http://m.wap.ghtkgg.cn/jnews/3506881.htm
- http://m.wap.ghtkgg.cn/jnews/518134.htm
- http://m.wap.ghtkgg.cn/jnews/5165221.htm
- http://m.wap.ghtkgg.cn/jnews/13939.htm
- http://m.wap.ghtkgg.cn/jnews/957350.htm
- http://m.wap.ghtkgg.cn/jnews/386353.htm
- http://m.wap.ghtkgg.cn/jnews/06502.htm
- http://m.wap.ghtkgg.cn/jnews/1078769.htm
- http://m.wap.ghtkgg.cn/jnews/6479.htm
- http://m.wap.ghtkgg.cn/jnews/070389.htm
- http://m.wap.ghtkgg.cn/jnews/0794.htm
- http://m.wap.ghtkgg.cn/jnews/366526.htm
- http://m.wap.ghtkgg.cn/jnews/05411.htm
- http://m.wap.ghtkgg.cn/jnews/1015.htm
- http://m.wap.ghtkgg.cn/jnews/96775.htm
- http://m.wap.ghtkgg.cn/jnews/04138.htm
- http://m.wap.ghtkgg.cn/jnews/0857271.htm
- http://m.wap.ghtkgg.cn/jnews/5350781.htm
- http://m.wap.ghtkgg.cn/jnews/213171.htm
- http://m.wap.ghtkgg.cn/jnews/4981.htm
- http://m.wap.ghtkgg.cn/jnews/16072.htm
- http://m.wap.ghtkgg.cn/jnews/52569.htm
- http://m.wap.ghtkgg.cn/jnews/5099.htm
- http://m.wap.ghtkgg.cn/jnews/0898961.htm
- http://m.wap.ghtkgg.cn/jnews/50668.htm
- http://m.wap.ghtkgg.cn/jnews/3337710.htm
- http://m.wap.ghtkgg.cn/jnews/44645.htm
- http://m.wap.ghtkgg.cn/jnews/7393152.htm
- http://m.wap.ghtkgg.cn/jnews/27708.htm
- http://m.wap.ghtkgg.cn/jnews/57869.htm
- http://m.wap.ghtkgg.cn/jnews/8086.htm
- http://m.wap.ghtkgg.cn/jnews/7952178.htm
- http://m.wap.ghtkgg.cn/jnews/77235.htm
- http://m.wap.ghtkgg.cn/jnews/024779.htm
- http://m.wap.ghtkgg.cn/jnews/9101.htm
- http://m.wap.ghtkgg.cn/jnews/466507.htm
- http://m.wap.ghtkgg.cn/jnews/5688155.htm
- http://m.wap.ghtkgg.cn/jnews/232086.htm
- http://m.wap.ghtkgg.cn/jnews/6672266.htm
- http://m.wap.ghtkgg.cn/jnews/748109.htm
- http://m.wap.ghtkgg.cn/jnews/24547.htm
- http://m.wap.ghtkgg.cn/jnews/2550631.htm
- http://m.wap.ghtkgg.cn/jnews/9342107.htm
- http://m.wap.ghtkgg.cn/jnews/654025.htm
- http://m.wap.ghtkgg.cn/jnews/987982.htm
- http://m.wap.ghtkgg.cn/jnews/91272.htm
- http://m.wap.ghtkgg.cn/jnews/6156151.htm
- http://m.wap.ghtkgg.cn/jnews/7978987.htm
- http://m.wap.ghtkgg.cn/jnews/2499529.htm
- http://m.wap.ghtkgg.cn/jnews/5483571.htm
- http://m.wap.ghtkgg.cn/jnews/5737.htm
- http://m.wap.ghtkgg.cn/jnews/90676.htm
- http://m.wap.ghtkgg.cn/jnews/6449416.htm
- http://m.wap.ghtkgg.cn/jnews/9630.htm
- http://m.wap.ghtkgg.cn/jnews/4769092.htm
- http://m.wap.ghtkgg.cn/jnews/20162.htm
- http://m.wap.ghtkgg.cn/jnews/582239.htm
- http://m.wap.ghtkgg.cn/jnews/2366294.htm
- http://m.wap.ghtkgg.cn/jnews/63741.htm
- http://m.wap.ghtkgg.cn/jnews/5983.htm
- http://m.wap.ghtkgg.cn/jnews/8101990.htm
- http://m.wap.ghtkgg.cn/jnews/6156962.htm
- http://m.wap.ghtkgg.cn/jnews/7703042.htm
- http://m.wap.ghtkgg.cn/jnews/952933.htm
- http://m.wap.ghtkgg.cn/jnews/1773958.htm
- http://m.wap.ghtkgg.cn/jnews/945694.htm

## 项目结构

```
jnews-resource-aggregator/
├── manage.py                      # Django 项目管理入口，用于启动服务与执行命令
├── requirements.txt               # Python 后端依赖清单，包含 Django 及数据库驱动
├── docker-compose.yml             # 容器编排配置，定义 Web 服务、PostgreSQL 与 Redis 服务
├── .env.example                   # 环境变量模板，包含数据库连接与密钥配置示例
├── src/                           # 核心源代码目录
│   ├── settings/                  # 多环境配置子目录
│   │   ├── base.py                # 通用配置，适用于所有运行环境
│   │   ├── development.py         # 开发环境专用配置，开启调试与本地数据库
│   │   └── production.py          # 生产环境配置，关闭调试并启用缓存与日志轮转
│   ├── apps/                      # 功能模块集合
│   │   ├── links/                 # 外链管理核心模块，定义数据模型与导入导出逻辑
│   │   ├── tags/                  # 标签系统模块，实现分类标签的增删改查与关联
│   │   ├── monitoring/            # 访问状态监控模块，执行定时探测与结果记录
│   │   └── statistics/            # 访问统计模块，记录点击次数并计算热度排序
│   ├── templates/                 # 后端渲染的 HTML 模板文件，包含管理后台页面
│   ├── static/                    # 静态资源文件，包含 CSS 样式表与 JavaScript 脚本
│   └── utils/                     # 通用工具函数库，包含 URL 校验、时间处理与数据转换
├── tests/                         # 单元测试与集成测试脚本，覆盖数据模型与 API 端点
├── scripts/                       # 运维与辅助脚本，包含批量导入与数据迁移工具
└── docs/                          # 项目文档源文件，包含入门指南、API 参考与运维手册
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账号，然后克隆该复刻版本至本地开发环境。建议在新建的功能分支上开展工作，分支命名采用 feature/ 或 fix/ 前缀加简要描述。

2. 确保本地开发环境已完全按照安装要求章节配置，运行完整测试套件确认无既有功能损坏。若新增功能或修复缺陷，请同步编写或更新对应的单元测试用例，保证测试覆盖率不低于现有水平。

3. 提交代码前执行代码风格检查工具（如 flake8 与 black），确保代码风格与项目现有风格保持一致。提交信息需遵循约定式提交规范，使用 feat:、fix:、docs:、chore: 等类型前缀。

4. 发起 Pull Request 至主仓库的 develop 分支，在请求描述中清晰说明本次变更的目的、影响范围以及测试情况。项目维护者将在 3 个工作日内进行审查并提出修改意见。

5. 若涉及文档更新，请同步修改 docs 目录下的对应文件，并确保文档中的示例代码与实际功能一致。新增功能需在文档导航表中增加对应条目。

## 常见问题

Q: 导入包含大量 URL 的 CSV 文件时，页面长时间无响应或超时，应如何处理？

A: 对于超过 500 条记录的导入操作，建议使用命令行导入工具而非 Web 表单。具体命令为 python manage.py import_links --file /path/to/file.csv，该命令会绕过 HTTP 请求超时限制并在后台完成处理。同时可以调整 CSV 文件的分批大小参数 batch_size，默认每批提交 100 条至数据库，可根据服务器性能适当调小该值。

Q: 外链状态监控显示大量链接为不可访问，但手动在浏览器中打开这些链接是正常的，原因是什么？

A: 监控模块默认使用 requests 库的默认超时设置（3 秒）且不携带浏览器 User-Agent 头。部分新闻站点会对非浏览器请求进行拦截或响应较慢。建议在 .env 文件中调整 MONITOR_TIMEOUT 环境变量至 10 秒，并设置 MONITOR_USER_AGENT 为常见移动端浏览器标识。若问题依旧，可在监控配置中关闭 SSL 证书验证选项。

Q: 生产环境部署后，后台管理界面加载缓慢，查询操作耗时严重，如何优化？

A: 首先确认 Redis 缓存服务已正确启用并在 settings/production.py 中配置了 CACHES 选项。对于频繁执行的列表查询，建议在数据模型上添加数据库索引，尤其是针对 created_at 和 last_accessed 字段。若数据量超过 5 万条，可考虑启用分页功能，每页默认显示 50 条记录。此外，定时清理三个月前的归档级链接也可有效减小主表体积。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
