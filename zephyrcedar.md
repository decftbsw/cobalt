# JNews Link Aggregator

JNews Link Aggregator 是一个专注于移动端新闻资讯链接的整理与分发平台，旨在为内容创作者、信息研究员以及普通读者提供结构化的新闻资源访问入口。本项目不对新闻内容本身进行编辑或改写，而是通过人工筛选与分类索引，将散落于移动新闻站点的优质报道以链接目录的形式呈现，帮助用户快速定位特定主题或时间段的新闻原始稿件。

本项目定位于技术资源与外链汇总工具，目标用户包括需要批量获取新闻素材的运营人员、进行舆情分析的数据从业者，以及希望从单一入口追踪多个新闻事件的普通读者。项目本身不存储任何新闻正文，仅维护链接索引关系，符合开源项目的轻量化与透明化原则。

## 功能概览

**新闻链接分类索引**：按照新闻主题、发布时间、来源频道等维度对入库链接进行标签化分类，支持多级筛选。

**链接有效性巡检**：内置链接存活检测模块，可定期检查已收录链接的响应状态码，标记失效链接并生成报告。

**批量导入与导出**：支持通过 CSV 或 JSON 格式批量导入新闻链接，同时可将索引结果导出为结构化数据文件。

**移动端优先的阅读视图**：针对移动设备屏幕尺寸优化链接展示布局，提供沉浸式阅读体验，减少翻页操作。

**全文元数据提取**：对每个入库链接自动提取页面标题、发布时间、正文摘要等元信息，用于快速预览。

**自定义标签与备注**：用户可为每个链接添加自定义标签和备注信息，便于个人化整理与后续检索。

**链接去重与合并**：自动检测重复提交的链接，合并相同 URL 的元数据记录，保持索引库整洁。

## 应用场景

内容运营人员每日需要从移动新闻站点收集特定行业或竞品的报道素材。本项目提供批量链接导入与分类功能，运营人员可将分散的链接集中管理，通过标签快速筛选出相关稿件，提升素材整理效率。

舆情分析师在进行事件追踪时，需要按时间线梳理不同媒体对同一事件的报道。本项目支持按发布时间排序和标签筛选，分析师可快速构建事件报道的时间轴，对比不同信源的观点差异。

普通读者希望在一个页面内浏览多个新闻来源的最新动态，而不必逐个访问站点。本项目将多个新闻链接聚合于统一目录下，读者打开项目页面即可获取最新链接列表，点击直达原始新闻页面。

开发者需要测试移动端网页解析脚本或链接抓取工具时，本项目可提供大量真实移动端 URL 作为测试样本。项目内置的链接存活检测模块也可作为参考实现，供开发者学习链接状态监测的逻辑。

## 快速开始

以下命令可帮助您在本地环境中快速部署并运行 JNews Link Aggregator 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/jnews-aggregator/jnews-link-aggregator.git

# 进入项目根目录
cd jnews-link-aggregator

# 安装项目依赖（使用 npm）
npm install

# 启动本地开发服务器
npm run dev
```

## 安装要求

本项目基于 Node.js 运行时构建，推荐使用 LTS 版本以确保兼容性。前端界面采用 Vue 3 框架，后端服务使用 Express 实现。数据库依赖 SQLite 进行本地数据持久化，无需额外安装数据库服务。测试框架选用 Jest，代码规范遵循 ESLint 配置。具体依赖清单如下：

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 项目运行时环境，建议使用 LTS 版本 |
| npm | 9.x 或更高 | 包管理工具，用于安装项目依赖 |
| Vue 3 | 3.3.x | 前端渐进式框架，用于构建用户界面 |
| Express | 4.18.x | 后端 Web 服务框架，提供 API 接口 |
| SQLite3 | 5.1.x | 嵌入式数据库，用于链接元数据存储 |
| Jest | 29.x | 单元测试框架，用于执行功能测试用例 |

## 文档导航

本项目文档分为使用指南、开发参考、运维手册和 API 参考四个层面，分别面向普通用户、开发者、运维人员和接口调用者。各层面文档所回答的核心问题如下表所示：

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 使用指南 | /docs/user-guide/ | 如何导入链接、如何分类筛选、如何导出数据、如何查看链接状态 |
| 开发参考 | /docs/developer-guide/ | 项目目录结构如何组织、核心模块如何扩展、如何提交代码变更 |
| 运维手册 | /docs/operations/ | 如何部署生产环境、如何配置日志轮转、如何执行数据备份 |
| API 参考 | /docs/api-reference/ | 有哪些可用接口、请求参数如何构造、响应数据结构是怎样的 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/7933938.htm
- http://m.wap.ghtkgg.cn/jnews/9983393.htm
- http://m.wap.ghtkgg.cn/jnews/719440.htm
- http://m.wap.ghtkgg.cn/jnews/0495852.htm
- http://m.wap.ghtkgg.cn/jnews/0193686.htm
- http://m.wap.ghtkgg.cn/jnews/096887.htm
- http://m.wap.ghtkgg.cn/jnews/28604.htm
- http://m.wap.ghtkgg.cn/jnews/5310729.htm
- http://m.wap.ghtkgg.cn/jnews/6633162.htm
- http://m.wap.ghtkgg.cn/jnews/676832.htm
- http://m.wap.ghtkgg.cn/jnews/545709.htm
- http://m.wap.ghtkgg.cn/jnews/1642664.htm
- http://m.wap.ghtkgg.cn/jnews/5187623.htm
- http://m.wap.ghtkgg.cn/jnews/3783654.htm
- http://m.wap.ghtkgg.cn/jnews/6477939.htm
- http://m.wap.ghtkgg.cn/jnews/5990.htm
- http://m.wap.ghtkgg.cn/jnews/0963385.htm
- http://m.wap.ghtkgg.cn/jnews/4972.htm
- http://m.wap.ghtkgg.cn/jnews/566192.htm
- http://m.wap.ghtkgg.cn/jnews/08956.htm
- http://m.wap.ghtkgg.cn/jnews/0553.htm
- http://m.wap.ghtkgg.cn/jnews/2566059.htm
- http://m.wap.ghtkgg.cn/jnews/2447066.htm
- http://m.wap.ghtkgg.cn/jnews/726887.htm
- http://m.wap.ghtkgg.cn/jnews/7018.htm
- http://m.wap.ghtkgg.cn/jnews/65735.htm
- http://m.wap.ghtkgg.cn/jnews/9125755.htm
- http://m.wap.ghtkgg.cn/jnews/749254.htm
- http://m.wap.ghtkgg.cn/jnews/0502.htm
- http://m.wap.ghtkgg.cn/jnews/10504.htm
- http://m.wap.ghtkgg.cn/jnews/0554.htm
- http://m.wap.ghtkgg.cn/jnews/196799.htm
- http://m.wap.ghtkgg.cn/jnews/9822.htm
- http://m.wap.ghtkgg.cn/jnews/5794493.htm
- http://m.wap.ghtkgg.cn/jnews/7875076.htm
- http://m.wap.ghtkgg.cn/jnews/2927397.htm
- http://m.wap.ghtkgg.cn/jnews/568963.htm
- http://m.wap.ghtkgg.cn/jnews/4290.htm
- http://m.wap.ghtkgg.cn/jnews/149310.htm
- http://m.wap.ghtkgg.cn/jnews/93682.htm
- http://m.wap.ghtkgg.cn/jnews/19653.htm
- http://m.wap.ghtkgg.cn/jnews/23567.htm
- http://m.wap.ghtkgg.cn/jnews/99222.htm
- http://m.wap.ghtkgg.cn/jnews/964213.htm
- http://m.wap.ghtkgg.cn/jnews/6047.htm
- http://m.wap.ghtkgg.cn/jnews/180836.htm
- http://m.wap.ghtkgg.cn/jnews/68315.htm
- http://m.wap.ghtkgg.cn/jnews/4505.htm
- http://m.wap.ghtkgg.cn/jnews/12827.htm
- http://m.wap.ghtkgg.cn/jnews/46916.htm
- http://m.wap.ghtkgg.cn/jnews/788468.htm
- http://m.wap.ghtkgg.cn/jnews/36409.htm
- http://m.wap.ghtkgg.cn/jnews/2432802.htm
- http://m.wap.ghtkgg.cn/jnews/3776.htm
- http://m.wap.ghtkgg.cn/jnews/7282461.htm
- http://m.wap.ghtkgg.cn/jnews/99006.htm
- http://m.wap.ghtkgg.cn/jnews/821545.htm
- http://m.wap.ghtkgg.cn/jnews/1282.htm
- http://m.wap.ghtkgg.cn/jnews/124658.htm
- http://m.wap.ghtkgg.cn/jnews/4510.htm
- http://m.wap.ghtkgg.cn/jnews/4453339.htm
- http://m.wap.ghtkgg.cn/jnews/3978.htm
- http://m.wap.ghtkgg.cn/jnews/1516543.htm
- http://m.wap.ghtkgg.cn/jnews/40044.htm
- http://m.wap.ghtkgg.cn/jnews/90339.htm
- http://m.wap.ghtkgg.cn/jnews/5988041.htm
- http://m.wap.ghtkgg.cn/jnews/07450.htm
- http://m.wap.ghtkgg.cn/jnews/3970192.htm
- http://m.wap.ghtkgg.cn/jnews/622231.htm
- http://m.wap.ghtkgg.cn/jnews/5823098.htm
- http://m.wap.ghtkgg.cn/jnews/001431.htm
- http://m.wap.ghtkgg.cn/jnews/998242.htm
- http://m.wap.ghtkgg.cn/jnews/40386.htm
- http://m.wap.ghtkgg.cn/jnews/2828.htm
- http://m.wap.ghtkgg.cn/jnews/2763.htm
- http://m.wap.ghtkgg.cn/jnews/2056091.htm
- http://m.wap.ghtkgg.cn/jnews/8405723.htm
- http://m.wap.ghtkgg.cn/jnews/7328521.htm
- http://m.wap.ghtkgg.cn/jnews/5727091.htm
- http://m.wap.ghtkgg.cn/jnews/39631.htm
- http://m.wap.ghtkgg.cn/jnews/674898.htm
- http://m.wap.ghtkgg.cn/jnews/62609.htm
- http://m.wap.ghtkgg.cn/jnews/455309.htm
- http://m.wap.ghtkgg.cn/jnews/0381.htm
- http://m.wap.ghtkgg.cn/jnews/36025.htm
- http://m.wap.ghtkgg.cn/jnews/04969.htm
- http://m.wap.ghtkgg.cn/jnews/77273.htm
- http://m.wap.ghtkgg.cn/jnews/69476.htm
- http://m.wap.ghtkgg.cn/jnews/4385840.htm
- http://m.wap.ghtkgg.cn/jnews/04939.htm
- http://m.wap.ghtkgg.cn/jnews/759911.htm
- http://m.wap.ghtkgg.cn/jnews/696883.htm
- http://m.wap.ghtkgg.cn/jnews/85819.htm
- http://m.wap.ghtkgg.cn/jnews/22010.htm
- http://m.wap.ghtkgg.cn/jnews/5096642.htm
- http://m.wap.ghtkgg.cn/jnews/41231.htm
- http://m.wap.ghtkgg.cn/jnews/1104.htm
- http://m.wap.ghtkgg.cn/jnews/713132.htm
- http://m.wap.ghtkgg.cn/jnews/9887.htm
- http://m.wap.ghtkgg.cn/jnews/734042.htm
- http://m.wap.ghtkgg.cn/jnews/0644074.htm
- http://m.wap.ghtkgg.cn/jnews/149951.htm
- http://m.wap.ghtkgg.cn/jnews/2044.htm
- http://m.wap.ghtkgg.cn/jnews/97424.htm
- http://m.wap.ghtkgg.cn/jnews/41678.htm
- http://m.wap.ghtkgg.cn/jnews/45432.htm
- http://m.wap.ghtkgg.cn/jnews/9812256.htm
- http://m.wap.ghtkgg.cn/jnews/3544.htm
- http://m.wap.ghtkgg.cn/jnews/0950742.htm
- http://m.wap.ghtkgg.cn/jnews/06008.htm
- http://m.wap.ghtkgg.cn/jnews/8481.htm
- http://m.wap.ghtkgg.cn/jnews/49798.htm
- http://m.wap.ghtkgg.cn/jnews/7010.htm
- http://m.wap.ghtkgg.cn/jnews/7304.htm
- http://m.wap.ghtkgg.cn/jnews/1079.htm
- http://m.wap.ghtkgg.cn/jnews/504055.htm
- http://m.wap.ghtkgg.cn/jnews/518993.htm
- http://m.wap.ghtkgg.cn/jnews/33356.htm
- http://m.wap.ghtkgg.cn/jnews/22678.htm
- http://m.wap.ghtkgg.cn/jnews/073614.htm
- http://m.wap.ghtkgg.cn/jnews/200953.htm
- http://m.wap.ghtkgg.cn/jnews/741110.htm
- http://m.wap.ghtkgg.cn/jnews/917312.htm
- http://m.wap.ghtkgg.cn/jnews/4564089.htm
- http://m.wap.ghtkgg.cn/jnews/9852.htm
- http://m.wap.ghtkgg.cn/jnews/1015558.htm
- http://m.wap.ghtkgg.cn/jnews/8865224.htm
- http://m.wap.ghtkgg.cn/jnews/118360.htm
- http://m.wap.ghtkgg.cn/jnews/83334.htm
- http://m.wap.ghtkgg.cn/jnews/15559.htm
- http://m.wap.ghtkgg.cn/jnews/03557.htm
- http://m.wap.ghtkgg.cn/jnews/623729.htm
- http://m.wap.ghtkgg.cn/jnews/77214.htm
- http://m.wap.ghtkgg.cn/jnews/649905.htm
- http://m.wap.ghtkgg.cn/jnews/4070463.htm
- http://m.wap.ghtkgg.cn/jnews/7657625.htm
- http://m.wap.ghtkgg.cn/jnews/04244.htm
- http://m.wap.ghtkgg.cn/jnews/6602580.htm
- http://m.wap.ghtkgg.cn/jnews/3793.htm
- http://m.wap.ghtkgg.cn/jnews/32387.htm
- http://m.wap.ghtkgg.cn/jnews/3199111.htm
- http://m.wap.ghtkgg.cn/jnews/58351.htm
- http://m.wap.ghtkgg.cn/jnews/4992036.htm
- http://m.wap.ghtkgg.cn/jnews/243854.htm
- http://m.wap.ghtkgg.cn/jnews/5804.htm
- http://m.wap.ghtkgg.cn/jnews/814296.htm
- http://m.wap.ghtkgg.cn/jnews/55415.htm
- http://m.wap.ghtkgg.cn/jnews/97052.htm
- http://m.wap.ghtkgg.cn/jnews/993736.htm
- http://m.wap.ghtkgg.cn/jnews/3688833.htm
- http://m.wap.ghtkgg.cn/jnews/29156.htm
- http://m.wap.ghtkgg.cn/jnews/8534142.htm
- http://m.wap.ghtkgg.cn/jnews/4343.htm
- http://m.wap.ghtkgg.cn/jnews/607879.htm
- http://m.wap.ghtkgg.cn/jnews/273399.htm
- http://m.wap.ghtkgg.cn/jnews/4424083.htm
- http://m.wap.ghtkgg.cn/jnews/1734054.htm
- http://m.wap.ghtkgg.cn/jnews/570831.htm
- http://m.wap.ghtkgg.cn/jnews/092886.htm
- http://m.wap.ghtkgg.cn/jnews/602507.htm
- http://m.wap.ghtkgg.cn/jnews/2541.htm
- http://m.wap.ghtkgg.cn/jnews/7814.htm
- http://m.wap.ghtkgg.cn/jnews/9721830.htm
- http://m.wap.ghtkgg.cn/jnews/021858.htm
- http://m.wap.ghtkgg.cn/jnews/8572955.htm
- http://m.wap.ghtkgg.cn/jnews/0473.htm
- http://m.wap.ghtkgg.cn/jnews/28169.htm
- http://m.wap.ghtkgg.cn/jnews/585088.htm
- http://m.wap.ghtkgg.cn/jnews/575888.htm
- http://m.wap.ghtkgg.cn/jnews/516899.htm
- http://m.wap.ghtkgg.cn/jnews/716692.htm
- http://m.wap.ghtkgg.cn/jnews/28401.htm
- http://m.wap.ghtkgg.cn/jnews/139870.htm
- http://m.wap.ghtkgg.cn/jnews/89185.htm
- http://m.wap.ghtkgg.cn/jnews/3941.htm
- http://m.wap.ghtkgg.cn/jnews/334981.htm
- http://m.wap.ghtkgg.cn/jnews/65747.htm
- http://m.wap.ghtkgg.cn/jnews/2507831.htm
- http://m.wap.ghtkgg.cn/jnews/9194833.htm
- http://m.wap.ghtkgg.cn/jnews/90707.htm
- http://m.wap.ghtkgg.cn/jnews/4421610.htm
- http://m.wap.ghtkgg.cn/jnews/059992.htm
- http://m.wap.ghtkgg.cn/jnews/4259284.htm
- http://m.wap.ghtkgg.cn/jnews/176487.htm
- http://m.wap.ghtkgg.cn/jnews/690440.htm
- http://m.wap.ghtkgg.cn/jnews/10992.htm
- http://m.wap.ghtkgg.cn/jnews/711669.htm
- http://m.wap.ghtkgg.cn/jnews/449314.htm
- http://m.wap.ghtkgg.cn/jnews/5948681.htm
- http://m.wap.ghtkgg.cn/jnews/083129.htm
- http://m.wap.ghtkgg.cn/jnews/4277.htm
- http://m.wap.ghtkgg.cn/jnews/205097.htm
- http://m.wap.ghtkgg.cn/jnews/9162617.htm
- http://m.wap.ghtkgg.cn/jnews/181711.htm
- http://m.wap.ghtkgg.cn/jnews/68683.htm
- http://m.wap.ghtkgg.cn/jnews/2902941.htm
- http://m.wap.ghtkgg.cn/jnews/2318630.htm
- http://m.wap.ghtkgg.cn/jnews/57993.htm
- http://m.wap.ghtkgg.cn/jnews/6567.htm
- http://m.wap.ghtkgg.cn/jnews/5564309.htm
- http://m.wap.ghtkgg.cn/jnews/807125.htm
- http://m.wap.ghtkgg.cn/jnews/7991.htm
- http://m.wap.ghtkgg.cn/jnews/6370296.htm
- http://m.wap.ghtkgg.cn/jnews/756623.htm
- http://m.wap.ghtkgg.cn/jnews/47303.htm
- http://m.wap.ghtkgg.cn/jnews/93782.htm
- http://m.wap.ghtkgg.cn/jnews/5256.htm
- http://m.wap.ghtkgg.cn/jnews/67729.htm
- http://m.wap.ghtkgg.cn/jnews/4394482.htm
- http://m.wap.ghtkgg.cn/jnews/37262.htm
- http://m.wap.ghtkgg.cn/jnews/82313.htm
- http://m.wap.ghtkgg.cn/jnews/465839.htm
- http://m.wap.ghtkgg.cn/jnews/478216.htm
- http://m.wap.ghtkgg.cn/jnews/9918786.htm
- http://m.wap.ghtkgg.cn/jnews/277840.htm
- http://m.wap.ghtkgg.cn/jnews/98772.htm
- http://m.wap.ghtkgg.cn/jnews/301538.htm
- http://m.wap.ghtkgg.cn/jnews/6067.htm
- http://m.wap.ghtkgg.cn/jnews/7895069.htm
- http://m.wap.ghtkgg.cn/jnews/56039.htm
- http://m.wap.ghtkgg.cn/jnews/5411.htm
- http://m.wap.ghtkgg.cn/jnews/806616.htm
- http://m.wap.ghtkgg.cn/jnews/75266.htm
- http://m.wap.ghtkgg.cn/jnews/41111.htm
- http://m.wap.ghtkgg.cn/jnews/7575.htm
- http://m.wap.ghtkgg.cn/jnews/6532.htm
- http://m.wap.ghtkgg.cn/jnews/26027.htm
- http://m.wap.ghtkgg.cn/jnews/16505.htm
- http://m.wap.ghtkgg.cn/jnews/465381.htm
- http://m.wap.ghtkgg.cn/jnews/61305.htm
- http://m.wap.ghtkgg.cn/jnews/5188986.htm
- http://m.wap.ghtkgg.cn/jnews/17594.htm
- http://m.wap.ghtkgg.cn/jnews/93578.htm
- http://m.wap.ghtkgg.cn/jnews/2001004.htm
- http://m.wap.ghtkgg.cn/jnews/369242.htm
- http://m.wap.ghtkgg.cn/jnews/2733767.htm
- http://m.wap.ghtkgg.cn/jnews/937722.htm
- http://m.wap.ghtkgg.cn/jnews/4927900.htm
- http://m.wap.ghtkgg.cn/jnews/13084.htm
- http://m.wap.ghtkgg.cn/jnews/720302.htm
- http://m.wap.ghtkgg.cn/jnews/5019.htm
- http://m.wap.ghtkgg.cn/jnews/9357472.htm
- http://m.wap.ghtkgg.cn/jnews/1730.htm
- http://m.wap.ghtkgg.cn/jnews/592742.htm
- http://m.wap.ghtkgg.cn/jnews/175971.htm
- http://m.wap.ghtkgg.cn/jnews/5862016.htm
- http://m.wap.ghtkgg.cn/jnews/8217054.htm
- http://m.wap.ghtkgg.cn/jnews/5776359.htm
- http://m.wap.ghtkgg.cn/jnews/0509732.htm
- http://m.wap.ghtkgg.cn/jnews/433495.htm
- http://m.wap.ghtkgg.cn/jnews/7897.htm
- http://m.wap.ghtkgg.cn/jnews/601126.htm
- http://m.wap.ghtkgg.cn/jnews/48452.htm
- http://m.wap.ghtkgg.cn/jnews/48827.htm
- http://m.wap.ghtkgg.cn/jnews/0515234.htm
- http://m.wap.ghtkgg.cn/jnews/9357.htm
- http://m.wap.ghtkgg.cn/jnews/4422.htm
- http://m.wap.ghtkgg.cn/jnews/222793.htm
- http://m.wap.ghtkgg.cn/jnews/50190.htm
- http://m.wap.ghtkgg.cn/jnews/3463584.htm
- http://m.wap.ghtkgg.cn/jnews/0015.htm
- http://m.wap.ghtkgg.cn/jnews/63013.htm
- http://m.wap.ghtkgg.cn/jnews/55571.htm
- http://m.wap.ghtkgg.cn/jnews/2964.htm
- http://m.wap.ghtkgg.cn/jnews/078217.htm
- http://m.wap.ghtkgg.cn/jnews/91214.htm
- http://m.wap.ghtkgg.cn/jnews/80459.htm
- http://m.wap.ghtkgg.cn/jnews/1487.htm
- http://m.wap.ghtkgg.cn/jnews/3241.htm
- http://m.wap.ghtkgg.cn/jnews/8435.htm
- http://m.wap.ghtkgg.cn/jnews/3194412.htm
- http://m.wap.ghtkgg.cn/jnews/665457.htm
- http://m.wap.ghtkgg.cn/jnews/9230458.htm
- http://m.wap.ghtkgg.cn/jnews/23788.htm
- http://m.wap.ghtkgg.cn/jnews/6515461.htm
- http://m.wap.ghtkgg.cn/jnews/0061006.htm
- http://m.wap.ghtkgg.cn/jnews/3812844.htm
- http://m.wap.ghtkgg.cn/jnews/83408.htm
- http://m.wap.ghtkgg.cn/jnews/778488.htm
- http://m.wap.ghtkgg.cn/jnews/8787.htm
- http://m.wap.ghtkgg.cn/jnews/4435.htm
- http://m.wap.ghtkgg.cn/jnews/63127.htm
- http://m.wap.ghtkgg.cn/jnews/7623375.htm
- http://m.wap.ghtkgg.cn/jnews/289575.htm
- http://m.wap.ghtkgg.cn/jnews/5820.htm
- http://m.wap.ghtkgg.cn/jnews/0575213.htm
- http://m.wap.ghtkgg.cn/jnews/2301199.htm
- http://m.wap.ghtkgg.cn/jnews/14962.htm
- http://m.wap.ghtkgg.cn/jnews/836409.htm
- http://m.wap.ghtkgg.cn/jnews/00385.htm
- http://m.wap.ghtkgg.cn/jnews/36758.htm
- http://m.wap.ghtkgg.cn/jnews/4310.htm
- http://m.wap.ghtkgg.cn/jnews/854167.htm
- http://m.wap.ghtkgg.cn/jnews/349378.htm
- http://m.wap.ghtkgg.cn/jnews/5963.htm
- http://m.wap.ghtkgg.cn/jnews/22574.htm
- http://m.wap.ghtkgg.cn/jnews/8005.htm
- http://m.wap.ghtkgg.cn/jnews/03485.htm
- http://m.wap.ghtkgg.cn/jnews/7076638.htm
- http://m.wap.ghtkgg.cn/jnews/83870.htm

## 项目结构

项目采用模块化分层架构，前端界面与后端服务分离，数据存储层独立。核心代码位于 src 目录下，测试用例与配置文件分别存放于各自目录。

```
jnews-link-aggregator/
├── src/                                # 项目核心源代码目录
│   ├── backend/                        # 后端服务模块（Express 应用）
│   │   ├── controllers/                # 控制器层，处理 HTTP 请求与响应
│   │   ├── models/                     # 数据模型层，定义链接、标签等实体
│   │   ├── routes/                     # 路由定义层，映射 URL 路径到控制器
│   │   └── services/                   # 业务逻辑层，实现链接管理核心功能
│   ├── frontend/                       # 前端界面模块（Vue 3 应用）
│   │   ├── components/                 # Vue 单文件组件，可复用 UI 部件
│   │   ├── views/                      # 页面级视图组件，对应独立路由
│   │   ├── stores/                     # Pinia 状态管理，维护全局数据
│   │   └── utils/                      # 前端工具函数，包含请求封装等
│   └── shared/                         # 前后端共享代码（类型定义与常量）
│       ├── types/                      # TypeScript 类型声明文件
│       └── constants/                  # 项目常量配置（状态码、标签规则）
├── tests/                              # 测试用例目录
│   ├── unit/                           # 单元测试（Jest）
│   └── integration/                    # 集成测试（API 接口测试）
├── docs/                               # 项目文档目录
│   ├── user-guide/                     # 用户使用指南
│   ├── developer-guide/                # 开发者贡献指南
│   ├── operations/                     # 运维部署手册
│   └── api-reference/                  # API 接口参考文档
├── scripts/                            # 运维脚本与自动化工具
│   ├── backup.sh                       # 数据备份脚本
│   └── health-check.js                 # 链接存活状态巡检脚本
├── config/                             # 环境配置文件
│   ├── default.json                    # 默认配置
│   ├── development.json                # 开发环境覆盖配置
│   └── production.json                 # 生产环境覆盖配置
├── package.json                        # npm 包管理配置文件
├── tsconfig.json                       # TypeScript 编译配置
├── .eslintrc.js                        # ESLint 代码规范配置
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

开源项目的持续发展离不开社区贡献者的支持。欢迎提交代码、文档或问题反馈，共同完善 JNews Link Aggregator。请遵循以下步骤参与贡献。

第一步，在 GitHub 上 Fork 本项目仓库至个人账号，然后克隆 Fork 后的仓库到本地开发环境，并配置上游远程仓库以同步主分支更新。

第二步，创建新的功能分支或修复分支，分支命名应遵循 feat/xxx 或 fix/xxx 格式，确保分支用途清晰可辨。

第三步，在本地完成代码开发或文档编写后，运行测试套件确保所有现有用例通过，并为新增功能补充对应的单元测试或集成测试。

第四步，提交代码变更时使用约定式提交规范（Conventional Commits），提交信息应包含类型、范围和简短描述，便于自动生成变更日志。

第五步，推送分支至个人远程仓库，然后向主仓库的 develop 分支发起 Pull Request，并在 PR 描述中详细说明变更内容、测试覆盖情况及相关 Issue 编号。

## 常见问题

问：项目启动后无法获取新闻链接内容，页面显示为空列表，该如何处理？

答：请确认 config/development.json 中的数据库连接配置是否正确，尤其是数据库文件路径是否具有读写权限。若使用 SQLite 默认配置，可尝试删除 data 目录下的数据库文件后重新启动服务，系统将自动重建空数据库。同时检查网络环境是否能够正常访问外网，因为部分链接元数据提取依赖外部页面抓取。

问：导入大量链接时页面响应缓慢或超时，有何优化建议？

答：批量导入接口默认单次最大处理 100 条记录，若链接总数超过此限制，建议将导入文件拆分为多个批次分次提交。您也可以在 config/default.json 中调整 batchSize 参数的值，但请注意增大批处理量会占用更多内存资源，建议根据服务器实际配置合理设置。此外，导入时关闭前端实时预览功能可显著提升后端处理速度。

问：如何更新已收录链接的元数据，例如重新抓取页面标题或摘要？

答：您可以通过调用 API 接口 /api/links/refresh 并传入需要更新的链接 ID 数组来触发重新抓取。系统将异步执行抓取任务，并在完成后更新数据库记录。若需要批量刷新全部链接，可使用命令行脚本 npm run refresh:metadata，该脚本会遍历所有链接并重新提取元信息，执行时间取决于链接总数和网络状况。

## 许可证

MIT License

Copyright (c) 2026 JNews Link Aggregator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
