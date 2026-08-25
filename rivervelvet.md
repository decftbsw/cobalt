# WebLink Catalog System

WebLink Catalog System 是一个面向技术内容聚合与导航的开源外链管理框架，专为需要批量维护、分类展示和快速检索外部资讯链接的运维人员、内容编辑与开发者设计。该系统的核心定位并非简单书签管理，而是围绕海量异构 URL 构建可持久化的元数据索引，支持标签过滤、状态监控与访问热度统计，从而将零散的浏览记录转化为结构化的信息资源池。

本项目面向两类目标用户：其一为需要每日处理大量行业新闻、政策公告或技术文档的资讯聚合团队，其二为希望自建轻量级导航站但不愿依赖第三方数据库的独立开发者。WebLink Catalog System 本身不提供爬虫或自动化采集能力，而是提供一套标准化的数据录入与呈现契约，让用户能够以纯文本方式维护链接库，并通过内置的静态生成器输出响应式导航页面。系统默认采用文件即数据库的设计哲学，所有链接信息存储于单一数据文件中，无需配置外部数据库即可启动，极大降低了部署与迁移成本。

## 功能概览

- **批量链接录入与校验**：系统提供结构化数据模板，支持一次性导入数百条外链，并在录入阶段自动检测 URL 格式合法性、去重校验以及协议一致性检查，避免无效或重复条目污染资源库。

- **多维度标签分类体系**：每条链接可附加多个自定义标签，例如“行业动态”“政策解读”“技术文档”“视频教程”等，系统根据标签自动生成分类视图，用户可按标签组合快速筛选目标内容。

- **访问状态周期性探测**：内置轻量级 HTTP 探测器，支持配置定时任务对已收录链接进行可达性检查，返回状态码与响应时间，并将异常链接标记为“待复核”状态，便于运维人员及时清理失效资源。

- **访问热度与点击统计**：基于访问日志记录每个链接的点击次数与最近访问时间，系统自动计算热度指数并生成热门链接排行榜，辅助内容运营者识别高价值资源。

- **响应式导航页面静态生成**：用户执行构建命令后，系统根据数据文件自动生成完整的 HTML 导航站，包含分类目录、搜索框与标签云，所有页面均为静态文件，可直接部署至任意 HTTP 服务器或对象存储服务。

- **数据导入导出兼容性**：支持 JSON、YAML 与 CSV 三种数据格式的导入导出，方便用户在不同工具间迁移数据，亦可与电子表格软件协同编辑链接清单。

- **命令行交互式管理工具**：提供交互式 CLI 工具，用户可通过终端命令完成链接增删改查、标签重命名、批量导出等常规运维操作，无需手动编辑数据文件。

## 应用场景

- **行业资讯每日汇总**：内容编辑每日从多个来源收集行业新闻、政策文件与技术博客，利用 WebLink Catalog System 统一录入并为每条链接标注来源领域与紧急程度，生成内部共享的资讯导航页，供团队成员快速浏览当日要闻。

- **技术文档知识库构建**：开发团队在项目迭代过程中积累大量外部参考文档、API 手册与故障排查案例，通过本系统分类存储并定期检测链接有效性，确保知识库中的参考资料始终可访问，减少因链接失效导致的信息中断。

- **个人书签管理与迁移**：独立开发者或研究员将浏览器分散收藏的数百个书签导出为 CSV 文件后批量导入系统，利用标签分类替代浏览器自带的文件夹分层结构，并借助静态生成功能生成个人起始页，实现跨设备、跨浏览器的书签统一访问入口。

- **运营活动资源看板**：市场运营人员在筹备线上活动时，需要整理合作方介绍、案例展示、媒体报导等外部链接，通过系统建立专属活动资源看板，设置临时标签并生成限时公开的导航页面，活动结束后一键归档。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户建议通过 Git Bash 或 WSL 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-catalog/weblink-catalog-system.git

# 进入项目根目录
cd weblink-catalog-system

# 安装依赖（项目基于 Python 3.10 开发，使用 pip 管理依赖）
pip install -r requirements.txt

# 运行内置数据样例，生成静态导航页面
python cli.py build --input data/sample.json --output dist/

# 启动本地预览服务器，访问 http://localhost:8080 查看生成的导航站
python cli.py serve --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或更高 | 核心运行环境，低于 3.10 版本将导致类型注解解析异常 |
| pip | 22.0 或更高 | Python 包管理工具，用于安装项目依赖库 |
| Git | 2.30 或更高 | 用于克隆仓库及版本管理，非运行时必需但建议安装 |
| 网络连接 | 任意 | 仅访问状态探测功能需要出站 HTTP 权限，静态生成与本地管理无需网络 |
| 磁盘空间 | 50 MB 以上 | 项目本体与生成产物占用空间，具体取决于链接数量与生成页面规模 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，Windows 下需确保文件路径长度不超过 260 字符 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置数据文件路径并生成第一个导航页面 |
| 数据格式规范 | docs/data-format.md | 链接数据文件采用何种 JSON 结构，必填字段与可选字段分别有哪些 |
| CLI 命令参考 | docs/cli-commands.md | build、serve、check、export 等命令的完整参数说明与使用示例 |
| 高级配置 | docs/advanced-config.md | 自定义页面模板、调整探测超时时间、配置多语言标签等进阶操作 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/69630.htm
- http://m.wap.bwbkj.cn/snews/0453342.htm
- http://m.wap.bwbkj.cn/snews/71698.htm
- http://m.wap.bwbkj.cn/snews/78312.htm
- http://m.wap.bwbkj.cn/snews/707095.htm
- http://m.wap.bwbkj.cn/snews/51783.htm
- http://m.wap.bwbkj.cn/snews/29385.htm
- http://m.wap.bwbkj.cn/snews/59744.htm
- http://m.wap.bwbkj.cn/snews/17247.htm
- http://m.wap.bwbkj.cn/snews/431714.htm
- http://m.wap.bwbkj.cn/snews/841347.htm
- http://m.wap.bwbkj.cn/snews/90866.htm
- http://m.wap.bwbkj.cn/snews/67196.htm
- http://m.wap.bwbkj.cn/snews/1625.htm
- http://m.wap.bwbkj.cn/snews/8333868.htm
- http://m.wap.bwbkj.cn/snews/47777.htm
- http://m.wap.bwbkj.cn/snews/8181513.htm
- http://m.wap.bwbkj.cn/snews/6008130.htm
- http://m.wap.bwbkj.cn/snews/283377.htm
- http://m.wap.bwbkj.cn/snews/110344.htm
- http://m.wap.bwbkj.cn/snews/906823.htm
- http://m.wap.bwbkj.cn/snews/3976.htm
- http://m.wap.bwbkj.cn/snews/6440166.htm
- http://m.wap.bwbkj.cn/snews/87684.htm
- http://m.wap.bwbkj.cn/snews/185199.htm
- http://m.wap.bwbkj.cn/snews/3106.htm
- http://m.wap.bwbkj.cn/snews/3412.htm
- http://m.wap.bwbkj.cn/snews/8509.htm
- http://m.wap.bwbkj.cn/snews/316958.htm
- http://m.wap.bwbkj.cn/snews/3129.htm
- http://m.wap.bwbkj.cn/snews/7874.htm
- http://m.wap.bwbkj.cn/snews/8337.htm
- http://m.wap.bwbkj.cn/snews/1222682.htm
- http://m.wap.bwbkj.cn/snews/6787946.htm
- http://m.wap.bwbkj.cn/snews/8960106.htm
- http://m.wap.bwbkj.cn/snews/61639.htm
- http://m.wap.bwbkj.cn/snews/6526759.htm
- http://m.wap.bwbkj.cn/snews/4279.htm
- http://m.wap.bwbkj.cn/snews/6130.htm
- http://m.wap.bwbkj.cn/snews/367407.htm
- http://m.wap.bwbkj.cn/snews/8868600.htm
- http://m.wap.bwbkj.cn/snews/72091.htm
- http://m.wap.bwbkj.cn/snews/1125588.htm
- http://m.wap.bwbkj.cn/snews/5679.htm
- http://m.wap.bwbkj.cn/snews/2017165.htm
- http://m.wap.bwbkj.cn/snews/8135695.htm
- http://m.wap.bwbkj.cn/snews/3949.htm
- http://m.wap.bwbkj.cn/snews/4914207.htm
- http://m.wap.bwbkj.cn/snews/3328.htm
- http://m.wap.bwbkj.cn/snews/437468.htm
- http://m.wap.bwbkj.cn/snews/0047567.htm
- http://m.wap.bwbkj.cn/snews/8619810.htm
- http://m.wap.bwbkj.cn/snews/61099.htm
- http://m.wap.bwbkj.cn/snews/254505.htm
- http://m.wap.bwbkj.cn/snews/62507.htm
- http://m.wap.bwbkj.cn/snews/565928.htm
- http://m.wap.bwbkj.cn/snews/2250.htm
- http://m.wap.bwbkj.cn/snews/9749977.htm
- http://m.wap.bwbkj.cn/snews/5748.htm
- http://m.wap.bwbkj.cn/snews/29950.htm
- http://m.wap.bwbkj.cn/snews/2473.htm
- http://m.wap.bwbkj.cn/snews/507085.htm
- http://m.wap.bwbkj.cn/snews/3552.htm
- http://m.wap.bwbkj.cn/snews/8490.htm
- http://m.wap.bwbkj.cn/snews/061038.htm
- http://m.wap.bwbkj.cn/snews/1186821.htm
- http://m.wap.bwbkj.cn/snews/530798.htm
- http://m.wap.bwbkj.cn/snews/9147618.htm
- http://m.wap.bwbkj.cn/snews/244951.htm
- http://m.wap.bwbkj.cn/snews/31229.htm
- http://m.wap.bwbkj.cn/snews/51364.htm
- http://m.wap.bwbkj.cn/snews/122141.htm
- http://m.wap.bwbkj.cn/snews/549067.htm
- http://m.wap.bwbkj.cn/snews/0050128.htm
- http://m.wap.bwbkj.cn/snews/2952.htm
- http://m.wap.bwbkj.cn/snews/345791.htm
- http://m.wap.bwbkj.cn/snews/5717782.htm
- http://m.wap.bwbkj.cn/snews/86383.htm
- http://m.wap.bwbkj.cn/snews/50237.htm
- http://m.wap.bwbkj.cn/snews/0202229.htm
- http://m.wap.bwbkj.cn/snews/4637.htm
- http://m.wap.bwbkj.cn/snews/34625.htm
- http://m.wap.bwbkj.cn/snews/195231.htm
- http://m.wap.bwbkj.cn/snews/8596.htm
- http://m.wap.bwbkj.cn/snews/3543.htm
- http://m.wap.bwbkj.cn/snews/38989.htm
- http://m.wap.bwbkj.cn/snews/7882319.htm
- http://m.wap.bwbkj.cn/snews/412236.htm
- http://m.wap.bwbkj.cn/snews/20467.htm
- http://m.wap.bwbkj.cn/snews/9165.htm
- http://m.wap.bwbkj.cn/snews/17553.htm
- http://m.wap.bwbkj.cn/snews/720660.htm
- http://m.wap.bwbkj.cn/snews/5277.htm
- http://m.wap.bwbkj.cn/snews/78928.htm
- http://m.wap.bwbkj.cn/snews/77451.htm
- http://m.wap.bwbkj.cn/snews/021839.htm
- http://m.wap.bwbkj.cn/snews/14312.htm
- http://m.wap.bwbkj.cn/snews/25384.htm
- http://m.wap.bwbkj.cn/snews/90733.htm
- http://m.wap.bwbkj.cn/snews/7527075.htm
- http://m.wap.bwbkj.cn/snews/72567.htm
- http://m.wap.bwbkj.cn/snews/967934.htm
- http://m.wap.bwbkj.cn/snews/5308.htm
- http://m.wap.bwbkj.cn/snews/437137.htm
- http://m.wap.bwbkj.cn/snews/4497.htm
- http://m.wap.bwbkj.cn/snews/8060.htm
- http://m.wap.bwbkj.cn/snews/8567.htm
- http://m.wap.bwbkj.cn/snews/8609127.htm
- http://m.wap.bwbkj.cn/snews/1512742.htm
- http://m.wap.bwbkj.cn/snews/713433.htm
- http://m.wap.bwbkj.cn/snews/9579.htm
- http://m.wap.bwbkj.cn/snews/61439.htm
- http://m.wap.bwbkj.cn/snews/306035.htm
- http://m.wap.bwbkj.cn/snews/038076.htm
- http://m.wap.bwbkj.cn/snews/6050603.htm
- http://m.wap.bwbkj.cn/snews/55511.htm
- http://m.wap.bwbkj.cn/snews/8096.htm
- http://m.wap.bwbkj.cn/snews/6248.htm
- http://m.wap.bwbkj.cn/snews/04460.htm
- http://m.wap.bwbkj.cn/snews/5886798.htm
- http://m.wap.bwbkj.cn/snews/7848.htm
- http://m.wap.bwbkj.cn/snews/55653.htm
- http://m.wap.bwbkj.cn/snews/3368.htm
- http://m.wap.bwbkj.cn/snews/4252121.htm
- http://m.wap.bwbkj.cn/snews/2615951.htm
- http://m.wap.bwbkj.cn/snews/1803288.htm
- http://m.wap.bwbkj.cn/snews/2894.htm
- http://m.wap.bwbkj.cn/snews/658456.htm
- http://m.wap.bwbkj.cn/snews/205221.htm
- http://m.wap.bwbkj.cn/snews/241367.htm
- http://m.wap.bwbkj.cn/snews/2513222.htm
- http://m.wap.bwbkj.cn/snews/918673.htm
- http://m.wap.bwbkj.cn/snews/7127.htm
- http://m.wap.bwbkj.cn/snews/9924.htm
- http://m.wap.bwbkj.cn/snews/6652.htm
- http://m.wap.bwbkj.cn/snews/62535.htm
- http://m.wap.bwbkj.cn/snews/8422892.htm
- http://m.wap.bwbkj.cn/snews/5467.htm
- http://m.wap.bwbkj.cn/snews/6385636.htm
- http://m.wap.bwbkj.cn/snews/7413868.htm
- http://m.wap.bwbkj.cn/snews/9706.htm
- http://m.wap.bwbkj.cn/snews/529585.htm
- http://m.wap.bwbkj.cn/snews/9988660.htm
- http://m.wap.bwbkj.cn/snews/144284.htm
- http://m.wap.bwbkj.cn/snews/99444.htm
- http://m.wap.bwbkj.cn/snews/06018.htm
- http://m.wap.bwbkj.cn/snews/559628.htm
- http://m.wap.bwbkj.cn/snews/2074.htm
- http://m.wap.bwbkj.cn/snews/0782718.htm
- http://m.wap.bwbkj.cn/snews/66518.htm
- http://m.wap.bwbkj.cn/snews/229567.htm
- http://m.wap.bwbkj.cn/snews/737344.htm
- http://m.wap.bwbkj.cn/snews/6609.htm
- http://m.wap.bwbkj.cn/snews/0020909.htm
- http://m.wap.bwbkj.cn/snews/61588.htm
- http://m.wap.bwbkj.cn/snews/770695.htm
- http://m.wap.bwbkj.cn/snews/638464.htm
- http://m.wap.bwbkj.cn/snews/9540675.htm
- http://m.wap.bwbkj.cn/snews/10043.htm
- http://m.wap.bwbkj.cn/snews/373736.htm
- http://m.wap.bwbkj.cn/snews/2116.htm
- http://m.wap.bwbkj.cn/snews/0208.htm
- http://m.wap.bwbkj.cn/snews/0416056.htm
- http://m.wap.bwbkj.cn/snews/695685.htm
- http://m.wap.bwbkj.cn/snews/73213.htm
- http://m.wap.bwbkj.cn/snews/7601.htm
- http://m.wap.bwbkj.cn/snews/73767.htm
- http://m.wap.bwbkj.cn/snews/32594.htm
- http://m.wap.bwbkj.cn/snews/5560090.htm
- http://m.wap.bwbkj.cn/snews/0446702.htm
- http://m.wap.bwbkj.cn/snews/4003757.htm
- http://m.wap.bwbkj.cn/snews/995296.htm
- http://m.wap.bwbkj.cn/snews/7295897.htm
- http://m.wap.bwbkj.cn/snews/64066.htm
- http://m.wap.bwbkj.cn/snews/12976.htm
- http://m.wap.bwbkj.cn/snews/719811.htm
- http://m.wap.bwbkj.cn/snews/110377.htm
- http://m.wap.bwbkj.cn/snews/245014.htm
- http://m.wap.bwbkj.cn/snews/6422359.htm
- http://m.wap.bwbkj.cn/snews/943784.htm
- http://m.wap.bwbkj.cn/snews/852857.htm
- http://m.wap.bwbkj.cn/snews/2635963.htm
- http://m.wap.bwbkj.cn/snews/189001.htm
- http://m.wap.bwbkj.cn/snews/583469.htm
- http://m.wap.bwbkj.cn/snews/36447.htm
- http://m.wap.bwbkj.cn/snews/04506.htm
- http://m.wap.bwbkj.cn/snews/17672.htm
- http://m.wap.bwbkj.cn/snews/4261371.htm
- http://m.wap.bwbkj.cn/snews/2363.htm
- http://m.wap.bwbkj.cn/snews/1010.htm
- http://m.wap.bwbkj.cn/snews/0149.htm
- http://m.wap.bwbkj.cn/snews/1243.htm
- http://m.wap.bwbkj.cn/snews/9251.htm
- http://m.wap.bwbkj.cn/snews/08109.htm
- http://m.wap.bwbkj.cn/snews/48881.htm
- http://m.wap.bwbkj.cn/snews/2712674.htm
- http://m.wap.bwbkj.cn/snews/2519543.htm
- http://m.wap.bwbkj.cn/snews/7577.htm
- http://m.wap.bwbkj.cn/snews/1570.htm
- http://m.wap.bwbkj.cn/snews/1305.htm
- http://m.wap.bwbkj.cn/snews/50063.htm
- http://m.wap.bwbkj.cn/snews/5329.htm
- http://m.wap.bwbkj.cn/snews/25822.htm
- http://m.wap.bwbkj.cn/snews/01068.htm
- http://m.wap.bwbkj.cn/snews/11383.htm
- http://m.wap.bwbkj.cn/snews/0828731.htm
- http://m.wap.bwbkj.cn/snews/1799.htm
- http://m.wap.bwbkj.cn/snews/74680.htm
- http://m.wap.bwbkj.cn/snews/3701218.htm
- http://m.wap.bwbkj.cn/snews/2309432.htm
- http://m.wap.bwbkj.cn/snews/9828.htm
- http://m.wap.bwbkj.cn/snews/1441.htm
- http://m.wap.bwbkj.cn/snews/495967.htm
- http://m.wap.bwbkj.cn/snews/7417162.htm
- http://m.wap.bwbkj.cn/snews/58257.htm
- http://m.wap.bwbkj.cn/snews/9195837.htm
- http://m.wap.bwbkj.cn/snews/510236.htm
- http://m.wap.bwbkj.cn/snews/3680423.htm
- http://m.wap.bwbkj.cn/snews/7007517.htm
- http://m.wap.bwbkj.cn/snews/448427.htm
- http://m.wap.bwbkj.cn/snews/7347385.htm
- http://m.wap.bwbkj.cn/snews/55153.htm
- http://m.wap.bwbkj.cn/snews/7356386.htm
- http://m.wap.bwbkj.cn/snews/282866.htm
- http://m.wap.bwbkj.cn/snews/2074022.htm
- http://m.wap.bwbkj.cn/snews/11956.htm
- http://m.wap.bwbkj.cn/snews/295663.htm
- http://m.wap.bwbkj.cn/snews/30600.htm
- http://m.wap.bwbkj.cn/snews/8774983.htm
- http://m.wap.bwbkj.cn/snews/147760.htm
- http://m.wap.bwbkj.cn/snews/17015.htm
- http://m.wap.bwbkj.cn/snews/1724937.htm
- http://m.wap.bwbkj.cn/snews/8341.htm
- http://m.wap.bwbkj.cn/snews/8242.htm
- http://m.wap.bwbkj.cn/snews/27490.htm
- http://m.wap.bwbkj.cn/snews/8174459.htm
- http://m.wap.bwbkj.cn/snews/966838.htm
- http://m.wap.bwbkj.cn/snews/21511.htm
- http://m.wap.bwbkj.cn/snews/44659.htm
- http://m.wap.bwbkj.cn/snews/31884.htm
- http://m.wap.bwbkj.cn/snews/6208299.htm
- http://m.wap.bwbkj.cn/snews/8165558.htm
- http://m.wap.bwbkj.cn/snews/9826.htm
- http://m.wap.bwbkj.cn/snews/5697422.htm
- http://m.wap.bwbkj.cn/snews/2018656.htm
- http://m.wap.bwbkj.cn/snews/2380146.htm
- http://m.wap.bwbkj.cn/snews/451440.htm
- http://m.wap.bwbkj.cn/snews/44274.htm
- http://m.wap.bwbkj.cn/snews/9995746.htm
- http://m.wap.bwbkj.cn/snews/577290.htm
- http://m.wap.bwbkj.cn/snews/504841.htm
- http://m.wap.bwbkj.cn/snews/8094.htm
- http://m.wap.bwbkj.cn/snews/2279651.htm
- http://m.wap.bwbkj.cn/snews/32573.htm
- http://m.wap.bwbkj.cn/snews/70441.htm
- http://m.wap.bwbkj.cn/snews/2711.htm
- http://m.wap.bwbkj.cn/snews/72154.htm
- http://m.wap.bwbkj.cn/snews/56177.htm
- http://m.wap.bwbkj.cn/snews/8436147.htm
- http://m.wap.bwbkj.cn/snews/910296.htm
- http://m.wap.bwbkj.cn/snews/3178.htm
- http://m.wap.bwbkj.cn/snews/0403.htm
- http://m.wap.bwbkj.cn/snews/6512373.htm
- http://m.wap.bwbkj.cn/snews/53046.htm
- http://m.wap.bwbkj.cn/snews/342031.htm
- http://m.wap.bwbkj.cn/snews/9655.htm
- http://m.wap.bwbkj.cn/snews/3401738.htm
- http://m.wap.bwbkj.cn/snews/851799.htm
- http://m.wap.bwbkj.cn/snews/5181844.htm
- http://m.wap.bwbkj.cn/snews/81724.htm
- http://m.wap.bwbkj.cn/snews/0128740.htm
- http://m.wap.bwbkj.cn/snews/29988.htm
- http://m.wap.bwbkj.cn/snews/61397.htm
- http://m.wap.bwbkj.cn/snews/24186.htm
- http://m.wap.bwbkj.cn/snews/7932.htm
- http://m.wap.bwbkj.cn/snews/32682.htm
- http://m.wap.bwbkj.cn/snews/64951.htm
- http://m.wap.bwbkj.cn/snews/96645.htm
- http://m.wap.bwbkj.cn/snews/04703.htm
- http://m.wap.bwbkj.cn/snews/34137.htm
- http://m.wap.bwbkj.cn/snews/56039.htm
- http://m.wap.bwbkj.cn/snews/902539.htm
- http://m.wap.bwbkj.cn/snews/623174.htm
- http://m.wap.bwbkj.cn/snews/3739575.htm
- http://m.wap.bwbkj.cn/snews/9685073.htm
- http://m.wap.bwbkj.cn/snews/158422.htm
- http://m.wap.bwbkj.cn/snews/7415.htm
- http://m.wap.bwbkj.cn/snews/47182.htm
- http://m.wap.bwbkj.cn/snews/87641.htm
- http://m.wap.bwbkj.cn/snews/897406.htm
- http://m.wap.bwbkj.cn/snews/61622.htm
- http://m.wap.bwbkj.cn/snews/05334.htm
- http://m.wap.bwbkj.cn/snews/0976379.htm
- http://m.wap.bwbkj.cn/snews/4187063.htm
- http://m.wap.bwbkj.cn/snews/9564250.htm
- http://m.wap.bwbkj.cn/snews/98052.htm
- http://m.wap.bwbkj.cn/snews/7430207.htm
- http://m.wap.bwbkj.cn/snews/61016.htm
- http://m.wap.bwbkj.cn/snews/06216.htm
- http://m.wap.bwbkj.cn/snews/1301432.htm

## 项目结构

```
weblink-catalog-system/
├── cli.py                     # 命令行入口，注册所有子命令（build/serve/check/export）
├── requirements.txt           # Python 依赖清单（requests, pyyaml, markdown, click, jinja2）
├── data/                      # 数据存储目录
│   ├── sample.json            # 样例链接数据文件（含 20 条演示记录）
│   ├── schema/                # JSON Schema 校验定义目录
│   │   └── link_schema.json   # 链接对象字段类型与约束定义
│   └── migrations/            # 数据格式升级脚本目录
│       └── v1_to_v2.py        # 从旧版单标签升级至多标签体系的迁移脚本
├── src/                       # 核心源码目录
│   ├── core/                  # 核心业务逻辑模块
│   │   ├── loader.py          # 数据文件加载与解析（支持 JSON/YAML/CSV）
│   │   ├── validator.py       # URL 格式校验、去重与协议检查
│   │   ├── probe.py           # HTTP 状态探测与超时控制
│   │   └── stats.py           # 点击统计与热度计算
│   ├── generators/            # 静态页面生成器模块
│   │   ├── html_renderer.py   # 基于 Jinja2 模板的 HTML 渲染引擎
│   │   ├── rss_feeder.py      # RSS 订阅源生成器，输出 feed.xml
│   │   └── assets/            # 静态资源目录（CSS/JS/字体）
│   │       ├── style.css      # 导航页默认样式表
│   │       └── search.js      # 前端搜索与标签过滤脚本
│   └── utils/                 # 通用工具函数
│       ├── logger.py          # 日志配置与控制台输出格式化
│       └── file_utils.py      # 文件读写、路径规范化与目录创建
├── tests/                     # 单元测试与集成测试目录
│   ├── test_loader.py         # 数据加载模块测试用例
│   ├── test_probe.py          # 状态探测模块模拟测试
│   └── fixtures/              # 测试用固定数据文件
│       └── mock_data.json     # 模拟数据用于 CI 自动化测试
├── docs/                      # 完整文档目录
│   ├── getting-started.md     # 入门指南
│   ├── data-format.md         # 数据格式规范
│   ├── cli-commands.md        # CLI 命令完整参考
│   └── advanced-config.md     # 高级配置与模板定制
├── dist/                      # 静态生成输出目录（默认，可配置）
│   ├── index.html             # 生成的导航首页
│   ├── categories/            # 分类子页面目录
│   └── feed.xml               # 自动生成的 RSS 订阅文件
├── .gitignore                 # Git 忽略规则（排除 dist/ 与 __pycache__）
└── LICENSE                    # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制至个人账号下，随后克隆该复刻版本至本地开发环境，并添加 upstream 远程仓库以同步主分支更新。

2. 创建新的功能分支，分支名称需简明描述改动目标，例如 `feat/add-csv-export` 或 `fix/probe-timeout`，避免在主干分支直接修改。

3. 编写或修改代码后，请确保在 `tests/` 目录下补充对应的单元测试用例，并执行 `pytest` 验证全部测试通过，同时确保新增代码符合 PEP 8 编码规范。

4. 提交变更时使用语义化提交信息格式，即 `<type>: <subject>`，其中 type 可选 feat、fix、docs、style、refactor、test、chore，subject 为简短描述，不超过 72 字符。

5. 推送分支至个人复刻仓库后，通过 GitHub 界面发起 Pull Request 至主仓库的 main 分支，在 PR 描述中说明改动内容、测试结果以及是否涉及破坏性变更，等待项目维护者审核。

## 常见问题

**问：系统能否处理超过一万条链接的数据文件？**

答：可以。WebLink Catalog System 采用流式加载策略，对于 JSON 与 CSV 格式的大文件，内存占用仅与当前处理的批次大小相关，而非全量加载。但生成静态页面时，单次构建产生的 HTML 文件数量与链接总数成正比，建议根据服务器文件系统性能适当控制单次构建规模，或通过配置分页参数生成多级索引页面。

**问：访问状态探测功能是否会影响链接来源站的正常访问？**

答：系统默认探测间隔为 24 小时一次，且单次探测仅发送标准 HEAD 请求，不下载响应体，对目标服务器造成的负载可忽略不计。用户可在配置文件中调整探测超时时间与重试次数，对于频繁被探测的站点，建议通过 `exclude_domains` 配置项排除特定域名。

**问：如何将现有浏览器书签导入系统？**

答：主流浏览器均支持将书签导出为 HTML 文件，系统未直接提供 HTML 解析器，但用户可使用浏览器自带的导出功能生成 CSV 或使用第三方工具将 HTML 书签转换为 JSON 格式，然后按照 `docs/data-format.md` 中描述的字段结构调整键名，最后通过 `cli.py import` 命令完成导入。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:10
