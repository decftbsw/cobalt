# NewsLink Aggregator

NewsLink Aggregator 是一个面向移动端资讯聚合场景的轻量级新闻外链管理工具，专为内容运营团队、个人站长以及资讯类小程序开发者设计。该项目通过结构化的外链收录机制，帮助用户快速归类、检索和展示来自不同来源的新闻条目，降低人工维护成本，提升内容分发效率。

本项目的核心定位不是重复造轮子式的爬虫框架，而是一个聚焦于外链元数据组织与呈现的中间层服务。它接收结构化的新闻链接列表，提供分类筛选、时间排序、关键词检索以及对外输出接口，适用于日均处理数百条级资讯链接的中小型业务场景。

## 功能概览

**批量链接导入** 支持通过文本文件、JSON 或直接粘贴方式批量导入新闻 URL，自动解析链接中的资源标识符。

**智能元数据提取** 从链接中自动提取发布时间、分类线索和资源编号，为后续检索与排序提供基础字段。

**分类标签管理** 允许用户为每条链接自定义标签，支持多级分类体系，便于按专题或栏目聚合内容。

**时效性排序引擎** 基于链接中的时间戳字段进行降序排列，确保最新资讯优先展示，支持手动置顶。

**全文检索接口** 提供对链接标题、来源域名、标签及描述信息的模糊搜索能力，返回匹配结果集。

**外链健康检测** 定期对已收录链接进行可访问性探测，标记失效或响应超时的条目，辅助运维清理。

**数据导入导出** 支持将当前链接库导出为 CSV、JSON 或 RSS 格式，便于迁移至其他系统或生成 Feed 流。

**访问统计看板** 记录每条外链的被点击次数与最近访问时间，为内容热度分析提供数据支撑。

## 应用场景

内容运营团队每日收集来自多个信源的新闻链接，需要统一去重、打标并发布至小程序前端。NewsLink Aggregator 可作为内部管理后台，运营人员批量粘贴链接后，系统自动完成格式清洗与排序，生成可直接对外的数据接口。

个人技术博主维护“每日资讯”栏目时，可通过本项目快速建立链接台账，避免手动编写 HTML 列表的重复劳动。系统生成的 RSS 输出可直接挂载至博客侧栏。

资讯类小程序开发者需要为客户端提供稳定的新闻源接口。使用本项目部署后端服务后，开发者只需按约定格式提交链接列表，前端即可通过 RESTful API 获取已分类、已排序的新闻数据，无需关心底层存储逻辑。

小型编辑部使用共享表格维护新闻选题库时，链接格式混乱且难以检索。迁移至本系统后，所有链接按统一规范存储，编辑可按日期、标签或关键词快速回溯历史稿件来源。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整流程。

```bash
git clone https://github.com/your-org/newslink-aggregator.git
cd newslink-aggregator
npm install
cp .env.example .env
# 编辑 .env 文件配置数据库连接与端口
npm run build
npm start
```

若使用 Docker 部署，可执行以下命令：

```bash
docker build -t newslink-aggregator .
docker run -p 3000:3000 -v ./data:/app/data newslink-aggregator
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.20.0 或更高 | 运行时环境，建议使用 LTS 版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装项目依赖 |
| SQLite | 3.32.0 或更高 | 默认嵌入式数据库，无需额外安装 |
| Redis | 6.2.0 或更高 | 缓存与会话存储，可选但推荐 |
| Nginx | 1.20.0 或更高 | 生产环境反向代理，可选 |
| PM2 | 5.0.0 或更高 | 进程守护工具，生产环境推荐 |
| Git | 2.25.0 或更高 | 代码克隆与版本管理 |
| curl | 7.68.0 或更高 | 健康检测模块依赖的命令行工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quick-start.md | 如何快速运行项目并进行首次链接导入 |
| 配置手册 | /docs/configuration.md | 环境变量、数据库连接、缓存策略如何配置 |
| API 参考 | /docs/api-reference.md | 提供哪些 RESTful 接口，请求与响应格式是什么 |
| 运维指南 | /docs/operations.md | 如何备份数据、迁移数据库、处理失效链接 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/3514891.htm
- http://m.3g.oexnr.cn/nnews/993523.htm
- http://m.3g.oexnr.cn/nnews/510226.htm
- http://m.3g.oexnr.cn/nnews/106991.htm
- http://m.3g.oexnr.cn/nnews/2551132.htm
- http://m.3g.oexnr.cn/nnews/0757.htm
- http://m.3g.oexnr.cn/nnews/2320822.htm
- http://m.3g.oexnr.cn/nnews/746534.htm
- http://m.3g.oexnr.cn/nnews/44433.htm
- http://m.3g.oexnr.cn/nnews/896640.htm
- http://m.3g.oexnr.cn/nnews/311523.htm
- http://m.3g.oexnr.cn/nnews/053677.htm
- http://m.3g.oexnr.cn/nnews/59091.htm
- http://m.3g.oexnr.cn/nnews/3194046.htm
- http://m.3g.oexnr.cn/nnews/392029.htm
- http://m.3g.oexnr.cn/nnews/945532.htm
- http://m.3g.oexnr.cn/nnews/5066.htm
- http://m.3g.oexnr.cn/nnews/2043652.htm
- http://m.3g.oexnr.cn/nnews/4064880.htm
- http://m.3g.oexnr.cn/nnews/1702770.htm
- http://m.3g.oexnr.cn/nnews/95177.htm
- http://m.3g.oexnr.cn/nnews/37837.htm
- http://m.3g.oexnr.cn/nnews/9504606.htm
- http://m.3g.oexnr.cn/nnews/91033.htm
- http://m.3g.oexnr.cn/nnews/8455788.htm
- http://m.3g.oexnr.cn/nnews/006653.htm
- http://m.3g.oexnr.cn/nnews/3990645.htm
- http://m.3g.oexnr.cn/nnews/11035.htm
- http://m.3g.oexnr.cn/nnews/01993.htm
- http://m.3g.oexnr.cn/nnews/2420.htm
- http://m.3g.oexnr.cn/nnews/0385.htm
- http://m.3g.oexnr.cn/nnews/2849.htm
- http://m.3g.oexnr.cn/nnews/3685229.htm
- http://m.3g.oexnr.cn/nnews/4357.htm
- http://m.3g.oexnr.cn/nnews/49900.htm
- http://m.3g.oexnr.cn/nnews/183568.htm
- http://m.3g.oexnr.cn/nnews/6467231.htm
- http://m.3g.oexnr.cn/nnews/68562.htm
- http://m.3g.oexnr.cn/nnews/237965.htm
- http://m.3g.oexnr.cn/nnews/152766.htm
- http://m.3g.oexnr.cn/nnews/0807.htm
- http://m.3g.oexnr.cn/nnews/92876.htm
- http://m.3g.oexnr.cn/nnews/74514.htm
- http://m.3g.oexnr.cn/nnews/074954.htm
- http://m.3g.oexnr.cn/nnews/7426.htm
- http://m.3g.oexnr.cn/nnews/9129.htm
- http://m.3g.oexnr.cn/nnews/71302.htm
- http://m.3g.oexnr.cn/nnews/4552768.htm
- http://m.3g.oexnr.cn/nnews/4629.htm
- http://m.3g.oexnr.cn/nnews/0409952.htm
- http://m.3g.oexnr.cn/nnews/43773.htm
- http://m.3g.oexnr.cn/nnews/1643349.htm
- http://m.3g.oexnr.cn/nnews/316933.htm
- http://m.3g.oexnr.cn/nnews/8900355.htm
- http://m.3g.oexnr.cn/nnews/3885085.htm
- http://m.3g.oexnr.cn/nnews/6033243.htm
- http://m.3g.oexnr.cn/nnews/6868305.htm
- http://m.3g.oexnr.cn/nnews/30816.htm
- http://m.3g.oexnr.cn/nnews/4219594.htm
- http://m.3g.oexnr.cn/nnews/7653440.htm
- http://m.3g.oexnr.cn/nnews/4784793.htm
- http://m.3g.oexnr.cn/nnews/6893742.htm
- http://m.3g.oexnr.cn/nnews/9991.htm
- http://m.3g.oexnr.cn/nnews/45631.htm
- http://m.3g.oexnr.cn/nnews/7198.htm
- http://m.3g.oexnr.cn/nnews/64784.htm
- http://m.3g.oexnr.cn/nnews/2646778.htm
- http://m.3g.oexnr.cn/nnews/1936097.htm
- http://m.3g.oexnr.cn/nnews/717717.htm
- http://m.3g.oexnr.cn/nnews/4931.htm
- http://m.3g.oexnr.cn/nnews/646261.htm
- http://m.3g.oexnr.cn/nnews/59347.htm
- http://m.3g.oexnr.cn/nnews/2699.htm
- http://m.3g.oexnr.cn/nnews/54240.htm
- http://m.3g.oexnr.cn/nnews/512533.htm
- http://m.3g.oexnr.cn/nnews/43245.htm
- http://m.3g.oexnr.cn/nnews/59434.htm
- http://m.3g.oexnr.cn/nnews/0391973.htm
- http://m.3g.oexnr.cn/nnews/290534.htm
- http://m.3g.oexnr.cn/nnews/324370.htm
- http://m.3g.oexnr.cn/nnews/663646.htm
- http://m.3g.oexnr.cn/nnews/8850170.htm
- http://m.3g.oexnr.cn/nnews/4344111.htm
- http://m.3g.oexnr.cn/nnews/292522.htm
- http://m.3g.oexnr.cn/nnews/176922.htm
- http://m.3g.oexnr.cn/nnews/84992.htm
- http://m.3g.oexnr.cn/nnews/925493.htm
- http://m.3g.oexnr.cn/nnews/7212.htm
- http://m.3g.oexnr.cn/nnews/1594.htm
- http://m.3g.oexnr.cn/nnews/0331040.htm
- http://m.3g.oexnr.cn/nnews/713357.htm
- http://m.3g.oexnr.cn/nnews/085867.htm
- http://m.3g.oexnr.cn/nnews/23578.htm
- http://m.3g.oexnr.cn/nnews/97941.htm
- http://m.3g.oexnr.cn/nnews/5023726.htm
- http://m.3g.oexnr.cn/nnews/0116.htm
- http://m.3g.oexnr.cn/nnews/55480.htm
- http://m.3g.oexnr.cn/nnews/8181074.htm
- http://m.3g.oexnr.cn/nnews/8639372.htm
- http://m.3g.oexnr.cn/nnews/5729841.htm
- http://m.3g.oexnr.cn/nnews/1379344.htm
- http://m.3g.oexnr.cn/nnews/8530.htm
- http://m.3g.oexnr.cn/nnews/444222.htm
- http://m.3g.oexnr.cn/nnews/564010.htm
- http://m.3g.oexnr.cn/nnews/1600303.htm
- http://m.3g.oexnr.cn/nnews/8307.htm
- http://m.3g.oexnr.cn/nnews/95714.htm
- http://m.3g.oexnr.cn/nnews/276664.htm
- http://m.3g.oexnr.cn/nnews/4270695.htm
- http://m.3g.oexnr.cn/nnews/5913799.htm
- http://m.3g.oexnr.cn/nnews/239004.htm
- http://m.3g.oexnr.cn/nnews/7865531.htm
- http://m.3g.oexnr.cn/nnews/8806.htm
- http://m.3g.oexnr.cn/nnews/362970.htm
- http://m.3g.oexnr.cn/nnews/0973.htm
- http://m.3g.oexnr.cn/nnews/908464.htm
- http://m.3g.oexnr.cn/nnews/120532.htm
- http://m.3g.oexnr.cn/nnews/6858.htm
- http://m.3g.oexnr.cn/nnews/2231288.htm
- http://m.3g.oexnr.cn/nnews/3811.htm
- http://m.3g.oexnr.cn/nnews/438925.htm
- http://m.3g.oexnr.cn/nnews/8274393.htm
- http://m.3g.oexnr.cn/nnews/9258348.htm
- http://m.3g.oexnr.cn/nnews/8120913.htm
- http://m.3g.oexnr.cn/nnews/9763.htm
- http://m.3g.oexnr.cn/nnews/18311.htm
- http://m.3g.oexnr.cn/nnews/06119.htm
- http://m.3g.oexnr.cn/nnews/6415762.htm
- http://m.3g.oexnr.cn/nnews/3486085.htm
- http://m.3g.oexnr.cn/nnews/939553.htm
- http://m.3g.oexnr.cn/nnews/89824.htm
- http://m.3g.oexnr.cn/nnews/8957929.htm
- http://m.3g.oexnr.cn/nnews/4192681.htm
- http://m.3g.oexnr.cn/nnews/184382.htm
- http://m.3g.oexnr.cn/nnews/26209.htm
- http://m.3g.oexnr.cn/nnews/65317.htm
- http://m.3g.oexnr.cn/nnews/077493.htm
- http://m.3g.oexnr.cn/nnews/211966.htm
- http://m.3g.oexnr.cn/nnews/2313661.htm
- http://m.3g.oexnr.cn/nnews/86338.htm
- http://m.3g.oexnr.cn/nnews/7549216.htm
- http://m.3g.oexnr.cn/nnews/909429.htm
- http://m.3g.oexnr.cn/nnews/1770879.htm
- http://m.3g.oexnr.cn/nnews/57063.htm
- http://m.3g.oexnr.cn/nnews/72253.htm
- http://m.3g.oexnr.cn/nnews/1339649.htm
- http://m.3g.oexnr.cn/nnews/6551008.htm
- http://m.3g.oexnr.cn/nnews/6037.htm
- http://m.3g.oexnr.cn/nnews/0836430.htm
- http://m.3g.oexnr.cn/nnews/804744.htm
- http://m.3g.oexnr.cn/nnews/247216.htm
- http://m.3g.oexnr.cn/nnews/196105.htm
- http://m.3g.oexnr.cn/nnews/84415.htm
- http://m.3g.oexnr.cn/nnews/86358.htm
- http://m.3g.oexnr.cn/nnews/6591712.htm
- http://m.3g.oexnr.cn/nnews/4605028.htm
- http://m.3g.oexnr.cn/nnews/34883.htm
- http://m.3g.oexnr.cn/nnews/0782.htm
- http://m.3g.oexnr.cn/nnews/5340660.htm
- http://m.3g.oexnr.cn/nnews/7693055.htm
- http://m.3g.oexnr.cn/nnews/6044807.htm
- http://m.3g.oexnr.cn/nnews/721483.htm
- http://m.3g.oexnr.cn/nnews/627387.htm
- http://m.3g.oexnr.cn/nnews/7867.htm
- http://m.3g.oexnr.cn/nnews/3933.htm
- http://m.3g.oexnr.cn/nnews/40499.htm
- http://m.3g.oexnr.cn/nnews/5132.htm
- http://m.3g.oexnr.cn/nnews/4645.htm
- http://m.3g.oexnr.cn/nnews/45219.htm
- http://m.3g.oexnr.cn/nnews/35211.htm
- http://m.3g.oexnr.cn/nnews/4785.htm
- http://m.3g.oexnr.cn/nnews/565703.htm
- http://m.3g.oexnr.cn/nnews/8048.htm
- http://m.3g.oexnr.cn/nnews/962421.htm
- http://m.3g.oexnr.cn/nnews/9448459.htm
- http://m.3g.oexnr.cn/nnews/71390.htm
- http://m.3g.oexnr.cn/nnews/6245922.htm
- http://m.3g.oexnr.cn/nnews/5199817.htm
- http://m.3g.oexnr.cn/nnews/997145.htm
- http://m.3g.oexnr.cn/nnews/79763.htm
- http://m.3g.oexnr.cn/nnews/986369.htm
- http://m.3g.oexnr.cn/nnews/9907835.htm
- http://m.3g.oexnr.cn/nnews/9998.htm
- http://m.3g.oexnr.cn/nnews/99731.htm
- http://m.3g.oexnr.cn/nnews/85657.htm
- http://m.3g.oexnr.cn/nnews/258339.htm
- http://m.3g.oexnr.cn/nnews/7456.htm
- http://m.3g.oexnr.cn/nnews/736101.htm
- http://m.3g.oexnr.cn/nnews/1493.htm
- http://m.3g.oexnr.cn/nnews/05632.htm
- http://m.3g.oexnr.cn/nnews/055521.htm
- http://m.3g.oexnr.cn/nnews/8843726.htm
- http://m.3g.oexnr.cn/nnews/36419.htm
- http://m.3g.oexnr.cn/nnews/0092.htm
- http://m.3g.oexnr.cn/nnews/9857.htm
- http://m.3g.oexnr.cn/nnews/5206905.htm
- http://m.3g.oexnr.cn/nnews/0659542.htm
- http://m.3g.oexnr.cn/nnews/9456048.htm
- http://m.3g.oexnr.cn/nnews/451277.htm
- http://m.3g.oexnr.cn/nnews/99564.htm
- http://m.3g.oexnr.cn/nnews/519249.htm
- http://m.3g.oexnr.cn/nnews/38011.htm
- http://m.3g.oexnr.cn/nnews/045570.htm
- http://m.3g.oexnr.cn/nnews/91468.htm
- http://m.3g.oexnr.cn/nnews/327531.htm
- http://m.3g.oexnr.cn/nnews/6551665.htm
- http://m.3g.oexnr.cn/nnews/690340.htm
- http://m.3g.oexnr.cn/nnews/43186.htm
- http://m.3g.oexnr.cn/nnews/1888251.htm
- http://m.3g.oexnr.cn/nnews/159344.htm
- http://m.3g.oexnr.cn/nnews/9031726.htm
- http://m.3g.oexnr.cn/nnews/5216.htm
- http://m.3g.oexnr.cn/nnews/7873.htm
- http://m.3g.oexnr.cn/nnews/3003.htm
- http://m.3g.oexnr.cn/nnews/73210.htm
- http://m.3g.oexnr.cn/nnews/2693986.htm
- http://m.3g.oexnr.cn/nnews/798521.htm
- http://m.3g.oexnr.cn/nnews/033178.htm
- http://m.3g.oexnr.cn/nnews/4301.htm
- http://m.3g.oexnr.cn/nnews/2443860.htm
- http://m.3g.oexnr.cn/nnews/951836.htm
- http://m.3g.oexnr.cn/nnews/026949.htm
- http://m.3g.oexnr.cn/nnews/3182540.htm
- http://m.3g.oexnr.cn/nnews/2809.htm
- http://m.3g.oexnr.cn/nnews/8186827.htm
- http://m.3g.oexnr.cn/nnews/14936.htm
- http://m.3g.oexnr.cn/nnews/28712.htm
- http://m.3g.oexnr.cn/nnews/6134023.htm
- http://m.3g.oexnr.cn/nnews/2204936.htm
- http://m.3g.oexnr.cn/nnews/8848918.htm
- http://m.3g.oexnr.cn/nnews/3013.htm
- http://m.3g.oexnr.cn/nnews/2753.htm
- http://m.3g.oexnr.cn/nnews/9865.htm
- http://m.3g.oexnr.cn/nnews/70874.htm
- http://m.3g.oexnr.cn/nnews/022937.htm
- http://m.3g.oexnr.cn/nnews/3133278.htm
- http://m.3g.oexnr.cn/nnews/2902.htm
- http://m.3g.oexnr.cn/nnews/826886.htm
- http://m.3g.oexnr.cn/nnews/449325.htm
- http://m.3g.oexnr.cn/nnews/755983.htm
- http://m.3g.oexnr.cn/nnews/553552.htm
- http://m.3g.oexnr.cn/nnews/9432321.htm
- http://m.3g.oexnr.cn/nnews/601996.htm
- http://m.3g.oexnr.cn/nnews/278372.htm
- http://m.3g.oexnr.cn/nnews/0690461.htm
- http://m.3g.oexnr.cn/nnews/0164.htm
- http://m.3g.oexnr.cn/nnews/32158.htm
- http://m.3g.oexnr.cn/nnews/420424.htm
- http://m.3g.oexnr.cn/nnews/9107585.htm
- http://m.3g.oexnr.cn/nnews/78263.htm
- http://m.3g.oexnr.cn/nnews/2536.htm
- http://m.3g.oexnr.cn/nnews/7574.htm
- http://m.3g.oexnr.cn/nnews/4576016.htm
- http://m.3g.oexnr.cn/nnews/66661.htm
- http://m.3g.oexnr.cn/nnews/211445.htm
- http://m.3g.oexnr.cn/nnews/5363945.htm
- http://m.3g.oexnr.cn/nnews/7378.htm
- http://m.3g.oexnr.cn/nnews/09737.htm
- http://m.3g.oexnr.cn/nnews/991886.htm
- http://m.3g.oexnr.cn/nnews/4589292.htm
- http://m.3g.oexnr.cn/nnews/97609.htm
- http://m.3g.oexnr.cn/nnews/92015.htm
- http://m.3g.oexnr.cn/nnews/73374.htm
- http://m.3g.oexnr.cn/nnews/86458.htm
- http://m.3g.oexnr.cn/nnews/84406.htm
- http://m.3g.oexnr.cn/nnews/26623.htm
- http://m.3g.oexnr.cn/nnews/923389.htm
- http://m.3g.oexnr.cn/nnews/5274.htm
- http://m.3g.oexnr.cn/nnews/3141188.htm
- http://m.3g.oexnr.cn/nnews/55172.htm
- http://m.3g.oexnr.cn/nnews/5124250.htm
- http://m.3g.oexnr.cn/nnews/86966.htm
- http://m.3g.oexnr.cn/nnews/5507967.htm
- http://m.3g.oexnr.cn/nnews/474229.htm
- http://m.3g.oexnr.cn/nnews/3524897.htm
- http://m.3g.oexnr.cn/nnews/7876.htm
- http://m.3g.oexnr.cn/nnews/4790128.htm
- http://m.3g.oexnr.cn/nnews/4670.htm
- http://m.3g.oexnr.cn/nnews/7614.htm
- http://m.3g.oexnr.cn/nnews/053328.htm
- http://m.3g.oexnr.cn/nnews/0183738.htm
- http://m.3g.oexnr.cn/nnews/677861.htm
- http://m.3g.oexnr.cn/nnews/897244.htm
- http://m.3g.oexnr.cn/nnews/2201.htm
- http://m.3g.oexnr.cn/nnews/9133.htm
- http://m.3g.oexnr.cn/nnews/79024.htm
- http://m.3g.oexnr.cn/nnews/5490656.htm
- http://m.3g.oexnr.cn/nnews/7349.htm
- http://m.3g.oexnr.cn/nnews/2828184.htm
- http://m.3g.oexnr.cn/nnews/5239771.htm
- http://m.3g.oexnr.cn/nnews/3873173.htm
- http://m.3g.oexnr.cn/nnews/4229.htm
- http://m.3g.oexnr.cn/nnews/3431730.htm
- http://m.3g.oexnr.cn/nnews/1335.htm
- http://m.3g.oexnr.cn/nnews/019742.htm
- http://m.3g.oexnr.cn/nnews/5045254.htm
- http://m.3g.oexnr.cn/nnews/3102547.htm
- http://m.3g.oexnr.cn/nnews/662190.htm
- http://m.3g.oexnr.cn/nnews/91558.htm
- http://m.3g.oexnr.cn/nnews/95074.htm

## 项目结构

```
newslink-aggregator/
├── src/
│   ├── core/
│   │   ├── link-parser.js      # 链接解析器，提取资源编号与时间戳
│   │   ├── health-checker.js   # 外链健康检测轮询任务
│   │   └── metadata-extractor.js # 元数据补充与清洗
│   ├── api/
│   │   ├── routes/
│   │   │   ├── links.js        # 链接增删改查路由
│   │   │   ├── tags.js         # 标签管理路由
│   │   │   └── stats.js        # 访问统计路由
│   │   └── middleware/
│   │       ├── auth.js         # 简单令牌认证中间件
│   │       └── validator.js    # 请求参数校验
│   ├── storage/
│   │   ├── sqlite-store.js     # SQLite 数据访问层
│   │   ├── redis-cache.js      # Redis 缓存操作封装
│   │   └── migrations/         # 数据库版本迁移脚本
│   ├── services/
│   │   ├── import-service.js   # 批量导入与格式适配
│   │   ├── export-service.js   # RSS/CSV/JSON 导出
│   │   └── search-service.js   # 全文检索实现
│   └── app.js                  # 应用入口与中间件组装
├── tests/
│   ├── unit/                   # 单元测试用例
│   └── integration/            # 接口集成测试
├── docs/
│   ├── quick-start.md          # 快速入门指南
│   ├── configuration.md        # 配置参数详解
│   ├── api-reference.md        # API 文档
│   └── operations.md           # 运维与故障排查
├── scripts/
│   ├── seed-db.js              # 初始化测试数据
│   └── backup.js               # 数据备份脚本
├── .env.example                # 环境变量模板
├── docker-compose.yml          # 容器编排配置
├── Dockerfile                  # 生产环境镜像构建
├── package.json                # 项目依赖与脚本
├── README.md                   # 本文件
└── LICENSE                     # MIT 许可证
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账户，然后克隆到本地开发环境。请确保使用 main 分支作为基准，创建新的功能分支进行开发。

2. 安装依赖后运行 npm run test 确认现有测试用例全部通过。新增功能或修复缺陷时，请同步编写对应的单元测试或集成测试，测试覆盖率不得低于原有水平。

3. 提交代码前执行 npm run lint 和 npm run format 统一代码风格。提交信息请遵循 Conventional Commits 规范，使用 feat、fix、docs、chore 等类型前缀。

4. 完成本地验证后推送至个人 fork 仓库，然后通过 GitHub 界面发起 Pull Request 至主仓库的 main 分支。PR 描述中应清晰说明变更目的、影响范围以及测试情况。

5. 项目维护者会在 48 小时内审阅 PR，可能提出修改意见。请及时响应审阅反馈，直至 PR 被合并或关闭。

## 常见问题

**问：导入大量链接时页面出现超时或卡顿，应该如何处理？**

答：单次导入建议不超过 500 条链接。若需批量导入更大规模数据，请使用 scripts/seed-db.js 脚本通过命令行执行，该脚本会分批提交并输出进度日志，避免 HTTP 请求超时。同时可调整环境变量中的 BATCH_SIZE 参数控制每批处理数量。

**问：健康检测模块误报大量链接为失效，如何调整灵敏度？**

答：健康检测默认超时时间为 5 秒，重试次数为 2 次。部分新闻站点响应较慢可能被误判。可在 .env 文件中设置 CHECK_TIMEOUT=10000 增加超时阈值，或设置 CHECK_RETRIES=3 提高重试次数。同时可将特定域名加入白名单跳过检测。

**问：如何将系统数据从 SQLite 迁移至 MySQL 或 PostgreSQL？**

答：项目使用 Knex.js 作为查询构建器，支持多种数据库。迁移步骤为：在 .env 中修改 DB_CLIENT 为 mysql2 或 pg，配置对应的 DB_HOST、DB_PORT、DB_USER 等参数，然后运行 npm run migrate:latest 执行建表语句。数据迁移可使用 scripts/backup.js 导出 SQLite 数据为 JSON，再通过导入接口写入新库。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
