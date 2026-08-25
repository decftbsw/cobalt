# NewsLink Aggregator

NewsLink Aggregator 是一个面向内容聚合与新闻外链管理的开源工具集，专门用于批量采集、归档和展示来自移动端新闻源的结构化数据。项目定位为技术资源型外链汇总平台，主要服务于需要从分散的移动新闻页面中提取元信息、构建索引库或进行舆情监控的开发团队、数据研究人员以及内容运营人员。

项目核心解决大规模新闻外链手工整理效率低下、链接失效难以追踪、元数据缺失导致检索困难等问题。通过提供标准化的采集脚本、元数据解析模板和静态索引生成器，使用者可以快速将原始新闻链接转化为可检索、可归档、可导出为多种格式的结构化数据集。项目本身不依赖重型框架，以轻量级脚本和配置文件驱动，适合集成到现有的数据流水线或定时任务系统中。

## 功能概览

批量链接采集 支持从本地文件或远程列表中批量读取新闻 URL，自动去重并进行状态码检测，过滤不可达链接。

元数据解析引擎 内置针对移动端新闻页面的通用解析规则，可提取标题、发布时间、正文摘要、来源域名等关键字段，支持自定义 XPath 或正则表达式扩展。

静态索引生成 根据解析结果自动生成按日期、域名或自定义标签分组的静态 HTML 索引页面，便于内部查阅或轻量级发布。

链接生命周期追踪 记录每次采集的时间戳、响应状态和内容哈希值，支持检测链接内容更新或页面下架情况，输出变动报告。

多格式数据导出 采集结果支持输出为 CSV、JSON Lines 和 SQLite 数据库文件，方便下游系统导入或进行二次分析。

定时任务集成 提供无依赖的调度脚本，可通过 cron 或系统计划任务定时执行采集流程，实现增量更新。

配置热加载 采集规则和解析模板采用 YAML 配置文件，修改后无需重启服务即可生效，降低维护成本。

## 应用场景

舆情监控与热点追踪 运营人员可以定期将目标新闻源链接导入系统，系统自动检测页面内容变更并生成摘要报告，帮助团队快速掌握话题动态，减少人工重复访问。

历史数据归档与检索 研究机构或档案馆可将大量历史新闻链接通过本工具进行结构化归档，生成可按时间、来源检索的本地数据库，避免原始页面失效后信息丢失。

内容聚合站数据源管理 小型内容聚合站点可使用本项目作为后端数据采集模块，定时拉取指定的新闻列表，生成统一格式的 JSON 数据供前端展示，降低直接调用第三方 API 的成本。

链接健康度巡检 运维团队可将本工具集成到监控体系中，定期检测重要外链集合的可访问性，自动输出失效链接清单，便于及时修复或替换。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/your-org/news-aggregator.git
cd news-aggregator

# 安装依赖（Python 3.8+ 环境）
pip install -r requirements.txt

# 准备链接列表文件 urls.txt，每行一个 URL
# 然后执行采集脚本
python collector.py --input urls.txt --output data/result.json

# 生成静态索引页
python generator.py --source data/result.json --target docs/index.html

# 启动本地预览（可选）
python -m http.server --directory docs 8000
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于页面抓取 |
| beautifulsoup4 | 4.12.0 及以上 | HTML 解析库，用于内容提取 |
| lxml | 4.9.0 及以上 | 高性能 XML/HTML 解析器，beautifulsoup4 的推荐后端 |
| pyyaml | 6.0 及以上 | YAML 配置文件解析 |
| sqlite3 | 系统自带 | Python 标准库，用于本地数据库导出 |
| tqdm | 4.65.0 及以上 | 进度条显示，可选但推荐 |
| 网络连接 | 稳定 | 访问目标新闻站点所需 |
| 磁盘空间 | 至少 500MB | 用于存储采集数据、索引文件和日志 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速跑通完整采集流程，生成第一份报告 |
| 配置手册 | docs/configuration.md | 所有 YAML 配置项的详细说明，包括解析规则、输出格式和调度参数 |
| 开发指南 | docs/development.md | 如何扩展自定义解析器、增加新的输出格式或集成外部存储 |
| 运维参考 | docs/operations.md | 生产环境部署建议、性能调优参数、常见错误排查方法 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/835075.htm
- http://m.blog.ghtkgg.cn/nnews/2460998.htm
- http://m.blog.ghtkgg.cn/nnews/9640.htm
- http://m.blog.ghtkgg.cn/nnews/6354683.htm
- http://m.blog.ghtkgg.cn/nnews/930878.htm
- http://m.blog.ghtkgg.cn/nnews/9966.htm
- http://m.blog.ghtkgg.cn/nnews/2776.htm
- http://m.blog.ghtkgg.cn/nnews/839134.htm
- http://m.blog.ghtkgg.cn/nnews/790135.htm
- http://m.blog.ghtkgg.cn/nnews/4780.htm
- http://m.blog.ghtkgg.cn/nnews/1287157.htm
- http://m.blog.ghtkgg.cn/nnews/435797.htm
- http://m.blog.ghtkgg.cn/nnews/659527.htm
- http://m.blog.ghtkgg.cn/nnews/5969.htm
- http://m.blog.ghtkgg.cn/nnews/026889.htm
- http://m.blog.ghtkgg.cn/nnews/9163.htm
- http://m.blog.ghtkgg.cn/nnews/2277535.htm
- http://m.blog.ghtkgg.cn/nnews/75790.htm
- http://m.blog.ghtkgg.cn/nnews/7250883.htm
- http://m.blog.ghtkgg.cn/nnews/00726.htm
- http://m.blog.ghtkgg.cn/nnews/3636.htm
- http://m.blog.ghtkgg.cn/nnews/305358.htm
- http://m.blog.ghtkgg.cn/nnews/5638785.htm
- http://m.blog.ghtkgg.cn/nnews/321590.htm
- http://m.blog.ghtkgg.cn/nnews/5187352.htm
- http://m.blog.ghtkgg.cn/nnews/58130.htm
- http://m.blog.ghtkgg.cn/nnews/24978.htm
- http://m.blog.ghtkgg.cn/nnews/4101622.htm
- http://m.blog.ghtkgg.cn/nnews/93409.htm
- http://m.blog.ghtkgg.cn/nnews/6134485.htm
- http://m.blog.ghtkgg.cn/nnews/40007.htm
- http://m.blog.ghtkgg.cn/nnews/5018.htm
- http://m.blog.ghtkgg.cn/nnews/677233.htm
- http://m.blog.ghtkgg.cn/nnews/96853.htm
- http://m.blog.ghtkgg.cn/nnews/6362.htm
- http://m.blog.ghtkgg.cn/nnews/570198.htm
- http://m.blog.ghtkgg.cn/nnews/0797519.htm
- http://m.blog.ghtkgg.cn/nnews/4867.htm
- http://m.blog.ghtkgg.cn/nnews/1644465.htm
- http://m.blog.ghtkgg.cn/nnews/2383457.htm
- http://m.blog.ghtkgg.cn/nnews/771990.htm
- http://m.blog.ghtkgg.cn/nnews/326502.htm
- http://m.blog.ghtkgg.cn/nnews/7293.htm
- http://m.blog.ghtkgg.cn/nnews/83349.htm
- http://m.blog.ghtkgg.cn/nnews/4744954.htm
- http://m.blog.ghtkgg.cn/nnews/803603.htm
- http://m.blog.ghtkgg.cn/nnews/964300.htm
- http://m.blog.ghtkgg.cn/nnews/1068053.htm
- http://m.blog.ghtkgg.cn/nnews/03545.htm
- http://m.blog.ghtkgg.cn/nnews/303737.htm
- http://m.blog.ghtkgg.cn/nnews/0777.htm
- http://m.blog.ghtkgg.cn/nnews/671580.htm
- http://m.blog.ghtkgg.cn/nnews/168590.htm
- http://m.blog.ghtkgg.cn/nnews/4995700.htm
- http://m.blog.ghtkgg.cn/nnews/5347071.htm
- http://m.blog.ghtkgg.cn/nnews/5505.htm
- http://m.blog.ghtkgg.cn/nnews/888545.htm
- http://m.blog.ghtkgg.cn/nnews/90783.htm
- http://m.blog.ghtkgg.cn/nnews/442425.htm
- http://m.blog.ghtkgg.cn/nnews/3843215.htm
- http://m.blog.ghtkgg.cn/nnews/662052.htm
- http://m.blog.ghtkgg.cn/nnews/2618.htm
- http://m.blog.ghtkgg.cn/nnews/2190628.htm
- http://m.blog.ghtkgg.cn/nnews/28261.htm
- http://m.blog.ghtkgg.cn/nnews/42241.htm
- http://m.blog.ghtkgg.cn/nnews/96570.htm
- http://m.blog.ghtkgg.cn/nnews/1773.htm
- http://m.blog.ghtkgg.cn/nnews/23540.htm
- http://m.blog.ghtkgg.cn/nnews/7721700.htm
- http://m.blog.ghtkgg.cn/nnews/299002.htm
- http://m.blog.ghtkgg.cn/nnews/1087.htm
- http://m.blog.ghtkgg.cn/nnews/10598.htm
- http://m.blog.ghtkgg.cn/nnews/72390.htm
- http://m.blog.ghtkgg.cn/nnews/6357822.htm
- http://m.blog.ghtkgg.cn/nnews/718362.htm
- http://m.blog.ghtkgg.cn/nnews/329451.htm
- http://m.blog.ghtkgg.cn/nnews/2205871.htm
- http://m.blog.ghtkgg.cn/nnews/649345.htm
- http://m.blog.ghtkgg.cn/nnews/929578.htm
- http://m.blog.ghtkgg.cn/nnews/856724.htm
- http://m.blog.ghtkgg.cn/nnews/7823376.htm
- http://m.blog.ghtkgg.cn/nnews/407421.htm
- http://m.blog.ghtkgg.cn/nnews/927990.htm
- http://m.blog.ghtkgg.cn/nnews/001065.htm
- http://m.blog.ghtkgg.cn/nnews/51805.htm
- http://m.blog.ghtkgg.cn/nnews/970960.htm
- http://m.blog.ghtkgg.cn/nnews/7875465.htm
- http://m.blog.ghtkgg.cn/nnews/5587904.htm
- http://m.blog.ghtkgg.cn/nnews/40649.htm
- http://m.blog.ghtkgg.cn/nnews/8735216.htm
- http://m.blog.ghtkgg.cn/nnews/6153.htm
- http://m.blog.ghtkgg.cn/nnews/8286628.htm
- http://m.blog.ghtkgg.cn/nnews/1850.htm
- http://m.blog.ghtkgg.cn/nnews/627827.htm
- http://m.blog.ghtkgg.cn/nnews/649854.htm
- http://m.blog.ghtkgg.cn/nnews/60005.htm
- http://m.blog.ghtkgg.cn/nnews/6156021.htm
- http://m.blog.ghtkgg.cn/nnews/304189.htm
- http://m.blog.ghtkgg.cn/nnews/3040.htm
- http://m.blog.ghtkgg.cn/nnews/099048.htm
- http://m.blog.ghtkgg.cn/nnews/6405236.htm
- http://m.blog.ghtkgg.cn/nnews/41942.htm
- http://m.blog.ghtkgg.cn/nnews/6545043.htm
- http://m.blog.ghtkgg.cn/nnews/83829.htm
- http://m.blog.ghtkgg.cn/nnews/4882305.htm
- http://m.blog.ghtkgg.cn/nnews/6156.htm
- http://m.blog.ghtkgg.cn/nnews/0308.htm
- http://m.blog.ghtkgg.cn/nnews/653686.htm
- http://m.blog.ghtkgg.cn/nnews/5096.htm
- http://m.blog.ghtkgg.cn/nnews/6733155.htm
- http://m.blog.ghtkgg.cn/nnews/5763.htm
- http://m.blog.ghtkgg.cn/nnews/24915.htm
- http://m.blog.ghtkgg.cn/nnews/727067.htm
- http://m.blog.ghtkgg.cn/nnews/0778.htm
- http://m.blog.ghtkgg.cn/nnews/50291.htm
- http://m.blog.ghtkgg.cn/nnews/2186050.htm
- http://m.blog.ghtkgg.cn/nnews/67965.htm
- http://m.blog.ghtkgg.cn/nnews/6996861.htm
- http://m.blog.ghtkgg.cn/nnews/4954477.htm
- http://m.blog.ghtkgg.cn/nnews/4228.htm
- http://m.blog.ghtkgg.cn/nnews/3990.htm
- http://m.blog.ghtkgg.cn/nnews/357553.htm
- http://m.blog.ghtkgg.cn/nnews/51965.htm
- http://m.blog.ghtkgg.cn/nnews/5057.htm
- http://m.blog.ghtkgg.cn/nnews/8298297.htm
- http://m.blog.ghtkgg.cn/nnews/49166.htm
- http://m.blog.ghtkgg.cn/nnews/4185.htm
- http://m.blog.ghtkgg.cn/nnews/811268.htm
- http://m.blog.ghtkgg.cn/nnews/49274.htm
- http://m.blog.ghtkgg.cn/nnews/4045907.htm
- http://m.blog.ghtkgg.cn/nnews/9929760.htm
- http://m.blog.ghtkgg.cn/nnews/4286438.htm
- http://m.blog.ghtkgg.cn/nnews/5725.htm
- http://m.blog.ghtkgg.cn/nnews/619961.htm
- http://m.blog.ghtkgg.cn/nnews/92553.htm
- http://m.blog.ghtkgg.cn/nnews/831252.htm
- http://m.blog.ghtkgg.cn/nnews/5644198.htm
- http://m.blog.ghtkgg.cn/nnews/5093.htm
- http://m.blog.ghtkgg.cn/nnews/6346.htm
- http://m.blog.ghtkgg.cn/nnews/4023.htm
- http://m.blog.ghtkgg.cn/nnews/89558.htm
- http://m.blog.ghtkgg.cn/nnews/7322457.htm
- http://m.blog.ghtkgg.cn/nnews/6812448.htm
- http://m.blog.ghtkgg.cn/nnews/86448.htm
- http://m.blog.ghtkgg.cn/nnews/3610.htm
- http://m.blog.ghtkgg.cn/nnews/149205.htm
- http://m.blog.ghtkgg.cn/nnews/2331.htm
- http://m.blog.ghtkgg.cn/nnews/0716039.htm
- http://m.blog.ghtkgg.cn/nnews/051269.htm
- http://m.blog.ghtkgg.cn/nnews/35082.htm
- http://m.blog.ghtkgg.cn/nnews/9564662.htm
- http://m.blog.ghtkgg.cn/nnews/46257.htm
- http://m.blog.ghtkgg.cn/nnews/2516.htm
- http://m.blog.ghtkgg.cn/nnews/587124.htm
- http://m.blog.ghtkgg.cn/nnews/578014.htm
- http://m.blog.ghtkgg.cn/nnews/86117.htm
- http://m.blog.ghtkgg.cn/nnews/4061.htm
- http://m.blog.ghtkgg.cn/nnews/5014.htm
- http://m.blog.ghtkgg.cn/nnews/5285148.htm
- http://m.blog.ghtkgg.cn/nnews/36108.htm
- http://m.blog.ghtkgg.cn/nnews/91852.htm
- http://m.blog.ghtkgg.cn/nnews/878897.htm
- http://m.blog.ghtkgg.cn/nnews/3331002.htm
- http://m.blog.ghtkgg.cn/nnews/3562953.htm
- http://m.blog.ghtkgg.cn/nnews/4557789.htm
- http://m.blog.ghtkgg.cn/nnews/2692.htm
- http://m.blog.ghtkgg.cn/nnews/9673.htm
- http://m.blog.ghtkgg.cn/nnews/315186.htm
- http://m.blog.ghtkgg.cn/nnews/3334.htm
- http://m.blog.ghtkgg.cn/nnews/44951.htm
- http://m.blog.ghtkgg.cn/nnews/3941.htm
- http://m.blog.ghtkgg.cn/nnews/041781.htm
- http://m.blog.ghtkgg.cn/nnews/82653.htm
- http://m.blog.ghtkgg.cn/nnews/0239341.htm
- http://m.blog.ghtkgg.cn/nnews/0578.htm
- http://m.blog.ghtkgg.cn/nnews/325770.htm
- http://m.blog.ghtkgg.cn/nnews/662232.htm
- http://m.blog.ghtkgg.cn/nnews/4781.htm
- http://m.blog.ghtkgg.cn/nnews/8387616.htm
- http://m.blog.ghtkgg.cn/nnews/2298194.htm
- http://m.blog.ghtkgg.cn/nnews/5829064.htm
- http://m.blog.ghtkgg.cn/nnews/1114.htm
- http://m.blog.ghtkgg.cn/nnews/8152917.htm
- http://m.blog.ghtkgg.cn/nnews/444413.htm
- http://m.blog.ghtkgg.cn/nnews/135111.htm
- http://m.blog.ghtkgg.cn/nnews/053161.htm
- http://m.blog.ghtkgg.cn/nnews/155998.htm
- http://m.blog.ghtkgg.cn/nnews/443540.htm
- http://m.blog.ghtkgg.cn/nnews/3792120.htm
- http://m.blog.ghtkgg.cn/nnews/763816.htm
- http://m.blog.ghtkgg.cn/nnews/559864.htm
- http://m.blog.ghtkgg.cn/nnews/2241900.htm
- http://m.blog.ghtkgg.cn/nnews/8587.htm
- http://m.blog.ghtkgg.cn/nnews/298678.htm
- http://m.blog.ghtkgg.cn/nnews/9415.htm
- http://m.blog.ghtkgg.cn/nnews/95989.htm
- http://m.blog.ghtkgg.cn/nnews/636620.htm
- http://m.blog.ghtkgg.cn/nnews/9656.htm
- http://m.blog.ghtkgg.cn/nnews/2925.htm
- http://m.blog.ghtkgg.cn/nnews/18484.htm
- http://m.blog.ghtkgg.cn/nnews/761688.htm
- http://m.blog.ghtkgg.cn/nnews/2891562.htm
- http://m.blog.ghtkgg.cn/nnews/8459179.htm
- http://m.blog.ghtkgg.cn/nnews/50912.htm
- http://m.blog.ghtkgg.cn/nnews/8878983.htm
- http://m.blog.ghtkgg.cn/nnews/9726.htm
- http://m.blog.ghtkgg.cn/nnews/37316.htm
- http://m.blog.ghtkgg.cn/nnews/08907.htm
- http://m.blog.ghtkgg.cn/nnews/477126.htm
- http://m.blog.ghtkgg.cn/nnews/5603306.htm
- http://m.blog.ghtkgg.cn/nnews/58487.htm
- http://m.blog.ghtkgg.cn/nnews/9153561.htm
- http://m.blog.ghtkgg.cn/nnews/844439.htm
- http://m.blog.ghtkgg.cn/nnews/841884.htm
- http://m.blog.ghtkgg.cn/nnews/79399.htm
- http://m.blog.ghtkgg.cn/nnews/3298.htm
- http://m.blog.ghtkgg.cn/nnews/621507.htm
- http://m.blog.ghtkgg.cn/nnews/118770.htm
- http://m.blog.ghtkgg.cn/nnews/85880.htm
- http://m.blog.ghtkgg.cn/nnews/0417.htm
- http://m.blog.ghtkgg.cn/nnews/045558.htm
- http://m.blog.ghtkgg.cn/nnews/9642.htm
- http://m.blog.ghtkgg.cn/nnews/80379.htm
- http://m.blog.ghtkgg.cn/nnews/86387.htm
- http://m.blog.ghtkgg.cn/nnews/1878232.htm
- http://m.blog.ghtkgg.cn/nnews/144370.htm
- http://m.blog.ghtkgg.cn/nnews/4236803.htm
- http://m.blog.ghtkgg.cn/nnews/28809.htm
- http://m.blog.ghtkgg.cn/nnews/265669.htm
- http://m.blog.ghtkgg.cn/nnews/8698610.htm
- http://m.blog.ghtkgg.cn/nnews/7471085.htm
- http://m.blog.ghtkgg.cn/nnews/1898577.htm
- http://m.blog.ghtkgg.cn/nnews/168268.htm
- http://m.blog.ghtkgg.cn/nnews/1231.htm
- http://m.blog.ghtkgg.cn/nnews/1431.htm
- http://m.blog.ghtkgg.cn/nnews/8812.htm
- http://m.blog.ghtkgg.cn/nnews/7538.htm
- http://m.blog.ghtkgg.cn/nnews/41338.htm
- http://m.blog.ghtkgg.cn/nnews/165332.htm
- http://m.blog.ghtkgg.cn/nnews/94516.htm
- http://m.blog.ghtkgg.cn/nnews/148938.htm
- http://m.blog.ghtkgg.cn/nnews/794749.htm
- http://m.blog.ghtkgg.cn/nnews/1096.htm
- http://m.blog.ghtkgg.cn/nnews/142717.htm
- http://m.blog.ghtkgg.cn/nnews/95872.htm
- http://m.blog.ghtkgg.cn/nnews/620897.htm
- http://m.blog.ghtkgg.cn/nnews/86877.htm
- http://m.blog.ghtkgg.cn/nnews/6505.htm
- http://m.blog.ghtkgg.cn/nnews/2601718.htm
- http://m.blog.ghtkgg.cn/nnews/136838.htm
- http://m.blog.ghtkgg.cn/nnews/02901.htm
- http://m.blog.ghtkgg.cn/nnews/078675.htm
- http://m.blog.ghtkgg.cn/nnews/4473.htm
- http://m.blog.ghtkgg.cn/nnews/3921134.htm
- http://m.blog.ghtkgg.cn/nnews/03186.htm
- http://m.blog.ghtkgg.cn/nnews/0223197.htm
- http://m.blog.ghtkgg.cn/nnews/423142.htm
- http://m.blog.ghtkgg.cn/nnews/0537523.htm
- http://m.blog.ghtkgg.cn/nnews/2541.htm
- http://m.blog.ghtkgg.cn/nnews/6059462.htm
- http://m.blog.ghtkgg.cn/nnews/03521.htm
- http://m.blog.ghtkgg.cn/nnews/9499801.htm
- http://m.blog.ghtkgg.cn/nnews/912332.htm
- http://m.blog.ghtkgg.cn/nnews/7749075.htm
- http://m.blog.ghtkgg.cn/nnews/903835.htm
- http://m.blog.ghtkgg.cn/nnews/6405475.htm
- http://m.blog.ghtkgg.cn/nnews/715996.htm
- http://m.blog.ghtkgg.cn/nnews/9836244.htm
- http://m.blog.ghtkgg.cn/nnews/968719.htm
- http://m.blog.ghtkgg.cn/nnews/394497.htm
- http://m.blog.ghtkgg.cn/nnews/83274.htm
- http://m.blog.ghtkgg.cn/nnews/7326.htm
- http://m.blog.ghtkgg.cn/nnews/74852.htm
- http://m.blog.ghtkgg.cn/nnews/9098.htm
- http://m.blog.ghtkgg.cn/nnews/27551.htm
- http://m.blog.ghtkgg.cn/nnews/0515679.htm
- http://m.blog.ghtkgg.cn/nnews/7403.htm
- http://m.blog.ghtkgg.cn/nnews/417438.htm
- http://m.blog.ghtkgg.cn/nnews/0950367.htm
- http://m.blog.ghtkgg.cn/nnews/83203.htm
- http://m.blog.ghtkgg.cn/nnews/62115.htm
- http://m.blog.ghtkgg.cn/nnews/69206.htm
- http://m.blog.ghtkgg.cn/nnews/19888.htm
- http://m.blog.ghtkgg.cn/nnews/3982448.htm
- http://m.blog.ghtkgg.cn/nnews/87946.htm
- http://m.blog.ghtkgg.cn/nnews/3314.htm
- http://m.blog.ghtkgg.cn/nnews/1660471.htm
- http://m.blog.ghtkgg.cn/nnews/8557573.htm
- http://m.blog.ghtkgg.cn/nnews/0976102.htm
- http://m.blog.ghtkgg.cn/nnews/518324.htm
- http://m.blog.ghtkgg.cn/nnews/5945.htm
- http://m.blog.ghtkgg.cn/nnews/375265.htm
- http://m.blog.ghtkgg.cn/nnews/1743252.htm
- http://m.blog.ghtkgg.cn/nnews/4024711.htm
- http://m.blog.ghtkgg.cn/nnews/70162.htm
- http://m.blog.ghtkgg.cn/nnews/46018.htm
- http://m.blog.ghtkgg.cn/nnews/268456.htm
- http://m.blog.ghtkgg.cn/nnews/4271083.htm
- http://m.blog.ghtkgg.cn/nnews/4863003.htm
- http://m.blog.ghtkgg.cn/nnews/5299.htm

## 项目结构

```
news-aggregator/
├── collector.py                # 主采集脚本，接收输入文件或参数，执行批量抓取
├── generator.py                # 静态索引生成器，将采集结果渲染为 HTML 页面
├── config/
│   ├── default.yaml            # 默认全局配置，包含请求头、超时、重试策略
│   ├── parser_rules.yaml       # 针对不同站点的解析规则模板（XPath/CSS选择器）
│   └── schedule.yaml           # 定时任务配置文件（用于集成 cron 或系统调度器）
├── core/
│   ├── fetcher.py              # HTTP 请求封装，处理重试、代理、SSL 验证
│   ├── parser.py               # 通用解析引擎，调用 BeautifulSoup 提取元数据
│   ├── deduper.py              # 基于 URL 哈希和内容哈希的去重模块
│   └── exporter.py             # 多格式导出器，支持 JSON/CSV/SQLite
├── utils/
│   ├── logger.py               # 日志模块，支持分级输出和文件轮转
│   ├── validator.py            # URL 格式校验和域名白名单过滤
│   └── time_utils.py           # 时间解析辅助函数，处理多种日期格式
├── tests/
│   ├── test_fetcher.py         # fetcher 模块单元测试
│   ├── test_parser.py          # parser 模块单元测试，包含模拟 HTML 样例
│   └── fixtures/               # 测试用静态 HTML 样本文件
├── data/                       # 默认数据存储目录（可配置），存放采集结果和日志
│   ├── raw/                    # 原始采集 JSON 文件按日期归档
│   ├── exported/               # 导出的 CSV/JSONL/SQLite 文件
│   └── cache/                  # 请求缓存，避免重复抓取
├── docs/                       # 文档目录，包含详细使用手册和 API 说明
│   ├── quickstart.md           # 快速入门
│   ├── configuration.md        # 配置项详解
│   ├── development.md          # 二次开发指南
│   └── operations.md           # 运维部署说明
├── scripts/
│   ├── cron_entry.sh           # cron 调度入口脚本，设置环境变量并调用 collector
│   └── migrate_db.py           # 数据库结构升级脚本
├── requirements.txt            # Python 依赖清单（带版本锁定）
├── setup.py                    # 项目安装脚本，支持 pip install -e .
├── LICENSE                     # MIT 许可证文件
└── README.md                   # 项目主文档（本文件）
```

## 贡献指南

提交 Issue 或功能请求 访问 GitHub Issues 页面，使用提供的模板描述问题或建议。对于缺陷报告，请附带完整的错误日志、复现步骤和运行环境信息。

遵循代码风格规范 项目使用 PEP 8 作为 Python 代码风格基准，并配置了 flake8 和 black 进行自动检查。提交前请运行 `black .` 和 `flake8 .` 确保格式符合要求。

编写单元测试 所有新增功能或修复补丁都应包含对应的单元测试用例，测试文件放置在 tests/ 目录下，并确保现有测试套件全部通过（`pytest tests/`）。

更新文档 对于影响配置、命令行参数或输出格式的变更，请同步更新 docs/ 目录下的对应文档，并在 README 中补充必要的示例说明。

提交 Pull Request 从主仓库 fork 后创建功能分支，提交前请确保 commit 信息清晰（使用常规提交格式），PR 描述中需说明变更动机、实现方式和测试覆盖情况。

## 常见问题

采集过程中出现大量超时或连接错误如何处理

首先检查网络环境是否可正常访问目标站点，并确认站点是否对自动化请求有反制措施。项目配置中提供了 `max_retries`、`timeout` 和 `proxy` 参数，可适当调整。同时建议启用 `cache` 功能避免重复请求同一 URL。若特定站点持续失败，可将其加入 `skip_domains` 列表或编写自定义解析器绕过限制。

如何自定义解析规则以适应不同新闻页面的结构

编辑 config/parser_rules.yaml 文件，按照现有模板添加新的域名匹配规则。每个规则需指定 `title_selector`、`time_selector` 和 `summary_selector`，支持 CSS 选择器和 XPath 两种表达式。项目在启动时会自动加载该配置，无需重启服务。如果页面内容为动态加载，则需要结合 Selenium 或 Playwright 进行改造，官方文档 development.md 中提供了扩展指引。

采集结果中的时间字段解析失败或格式不统一如何解决

项目内置了常见中文日期格式的解析器，但部分站点可能使用自定义格式。此时可在 parser_rules.yaml 中为对应域名指定 `time_format` 参数，使用 Python strptime 指令集描述格式。若格式高度不规则，可编写自定义时间处理函数，并在 `core/parser.py` 中注册。另外，所有解析失败的时间字段会回退为页面抓取时间，并在日志中输出警告信息。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
