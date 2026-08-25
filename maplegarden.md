# WebFront Resource Aggregator

WebFront Resource Aggregator 是一个面向前端开发者和技术内容消费者的轻量级外链资源汇总工具。该项目旨在将分散在互联网各处的技术新闻、开发教程、框架更新公告和工程实践案例集中管理，通过结构化的数据索引和分类机制，帮助开发者快速定位高价值技术内容。项目本身不存储任何文章内容，仅提供元数据索引和跳转能力，适用于个人开发者作为技术阅读入口，也适用于技术团队内部作为知识分享的中转站。

## 功能概览

**多源内容聚合**：系统支持从多个技术资讯源自动拉取文章元数据，包括标题、发布时间、摘要和原始链接，统一存入本地索引库。

**分类标签体系**：每一篇收录的资源均可被打上框架、工具、性能优化、安全、工程化等分类标签，便于后续按主题筛选。

**全文检索支持**：基于标题和摘要构建倒排索引，支持布尔查询和短语匹配，帮助用户在数百条链接中快速定位相关内容。

**定期同步机制**：内置定时任务，可每天自动检查源站更新，新增资源自动入库并标记未读状态。

**访问统计看板**：记录每条外链的点击次数和最后访问时间，提供热门内容排行榜，辅助用户判断内容价值。

**导出与分享**：支持将筛选后的资源列表导出为 JSON 或 Markdown 格式，方便团队文档沉淀或博客引用。

**命令行交互界面**：提供 CLI 工具，用户可通过终端执行查询、导入、统计等操作，无需图形界面即可完成日常使用。

**RESTful API 接口**：对外提供标准 HTTP API，允许第三方工具集成资源查询和导入功能，便于构建自动化工作流。

## 应用场景

个人技术阅读聚合：开发者每日早晨通过命令行执行一次同步命令，拉取最新的技术文章列表，按标签筛选自己关注的框架动态，在一个工具内完成所有技术资讯的浏览，避免频繁切换浏览器标签页。

团队内部知识中转：技术团队在项目迭代过程中，成员将各自发现的有价值外链通过 API 提交到聚合器，系统自动归类并生成周报摘要，团队周会时直接查看本周热门资源排行，快速同步行业动态。

自动化内容采集流水线：运维人员配置定时任务，将聚合器与公司内部 Wiki 或钉钉机器人联动，每当检测到指定关键词的新资源时，自动推送通知到团队群组，实现内容从发现到分发的全自动流程。

技术博客素材管理：技术博主使用本工具的导出功能，将一段时间内收集的参考资料按分类导出为 Markdown 表格，直接作为博文的参考文献附录，节省手动整理引用链接的时间。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webfront-resource/aggregator.git

# 进入项目目录
cd aggregator

# 安装依赖（使用 npm）
npm install

# 复制配置文件模板并修改
cp .env.example .env

# 初始化本地索引数据库
npm run init-db

# 启动定时同步任务（后台运行）
npm run sync

# 启动 CLI 交互界面
npm run cli
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 项目运行时环境，推荐使用 LTS 版本 |
| npm | >= 9.0.0 | 包管理器，用于安装项目依赖 |
| SQLite3 | >= 3.40.0 | 嵌入式数据库，存储资源索引和元数据 |
| cURL | >= 7.68.0 | 用于外部资源抓取时的 HTTP 请求（备选 fetch） |
| cron | >= 1.5.2（Linux） / Windows 任务计划程序 | 定时同步任务的系统级调度器 |
| git | >= 2.30.0 | 版本控制工具，用于克隆仓库和拉取更新 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何安装、配置和首次运行项目；环境变量各字段含义 |
| API 参考 | docs/api-reference.md | RESTful API 各端点的请求格式、返回字段和错误码 |
| 同步机制 | docs/sync-mechanism.md | 定时任务的调度策略、去重逻辑和失败重试机制 |
| 贡献规范 | docs/contributing.md | 提交代码的流程、代码风格检查和测试用例编写要求 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/8161852.htm
- http://m.wap.oexnr.cn/jnews/2394.htm
- http://m.wap.oexnr.cn/jnews/81663.htm
- http://m.wap.oexnr.cn/jnews/8739627.htm
- http://m.wap.oexnr.cn/jnews/6083.htm
- http://m.wap.oexnr.cn/jnews/6270573.htm
- http://m.wap.oexnr.cn/jnews/878017.htm
- http://m.wap.oexnr.cn/jnews/78444.htm
- http://m.wap.oexnr.cn/jnews/53537.htm
- http://m.wap.oexnr.cn/jnews/062820.htm
- http://m.wap.oexnr.cn/jnews/229163.htm
- http://m.wap.oexnr.cn/jnews/3421507.htm
- http://m.wap.oexnr.cn/jnews/0071941.htm
- http://m.wap.oexnr.cn/jnews/525048.htm
- http://m.wap.oexnr.cn/jnews/852571.htm
- http://m.wap.oexnr.cn/jnews/214878.htm
- http://m.wap.oexnr.cn/jnews/1364.htm
- http://m.wap.oexnr.cn/jnews/20930.htm
- http://m.wap.oexnr.cn/jnews/9078639.htm
- http://m.wap.oexnr.cn/jnews/163585.htm
- http://m.wap.oexnr.cn/jnews/8959.htm
- http://m.wap.oexnr.cn/jnews/51668.htm
- http://m.wap.oexnr.cn/jnews/9928.htm
- http://m.wap.oexnr.cn/jnews/2416702.htm
- http://m.wap.oexnr.cn/jnews/4211248.htm
- http://m.wap.oexnr.cn/jnews/97242.htm
- http://m.wap.oexnr.cn/jnews/8875.htm
- http://m.wap.oexnr.cn/jnews/3422.htm
- http://m.wap.oexnr.cn/jnews/479446.htm
- http://m.wap.oexnr.cn/jnews/86396.htm
- http://m.wap.oexnr.cn/jnews/3800716.htm
- http://m.wap.oexnr.cn/jnews/666149.htm
- http://m.wap.oexnr.cn/jnews/0309821.htm
- http://m.wap.oexnr.cn/jnews/3732.htm
- http://m.wap.oexnr.cn/jnews/596595.htm
- http://m.wap.oexnr.cn/jnews/10152.htm
- http://m.wap.oexnr.cn/jnews/5222261.htm
- http://m.wap.oexnr.cn/jnews/00207.htm
- http://m.wap.oexnr.cn/jnews/831380.htm
- http://m.wap.oexnr.cn/jnews/45157.htm
- http://m.wap.oexnr.cn/jnews/88025.htm
- http://m.wap.oexnr.cn/jnews/10510.htm
- http://m.wap.oexnr.cn/jnews/7318.htm
- http://m.wap.oexnr.cn/jnews/0698.htm
- http://m.wap.oexnr.cn/jnews/2951472.htm
- http://m.wap.oexnr.cn/jnews/521649.htm
- http://m.wap.oexnr.cn/jnews/4146.htm
- http://m.wap.oexnr.cn/jnews/8874453.htm
- http://m.wap.oexnr.cn/jnews/9184080.htm
- http://m.wap.oexnr.cn/jnews/46422.htm
- http://m.wap.oexnr.cn/jnews/0963.htm
- http://m.wap.oexnr.cn/jnews/1948.htm
- http://m.wap.oexnr.cn/jnews/659524.htm
- http://m.wap.oexnr.cn/jnews/9864.htm
- http://m.wap.oexnr.cn/jnews/5489790.htm
- http://m.wap.oexnr.cn/jnews/2815028.htm
- http://m.wap.oexnr.cn/jnews/03500.htm
- http://m.wap.oexnr.cn/jnews/660489.htm
- http://m.wap.oexnr.cn/jnews/7509.htm
- http://m.wap.oexnr.cn/jnews/253966.htm
- http://m.wap.oexnr.cn/jnews/8997394.htm
- http://m.wap.oexnr.cn/jnews/61518.htm
- http://m.wap.oexnr.cn/jnews/799995.htm
- http://m.wap.oexnr.cn/jnews/0432348.htm
- http://m.wap.oexnr.cn/jnews/8841326.htm
- http://m.wap.oexnr.cn/jnews/755471.htm
- http://m.wap.oexnr.cn/jnews/36656.htm
- http://m.wap.oexnr.cn/jnews/762230.htm
- http://m.wap.oexnr.cn/jnews/6068195.htm
- http://m.wap.oexnr.cn/jnews/74644.htm
- http://m.wap.oexnr.cn/jnews/1913.htm
- http://m.wap.oexnr.cn/jnews/2151.htm
- http://m.wap.oexnr.cn/jnews/324984.htm
- http://m.wap.oexnr.cn/jnews/24286.htm
- http://m.wap.oexnr.cn/jnews/943604.htm
- http://m.wap.oexnr.cn/jnews/4944327.htm
- http://m.wap.oexnr.cn/jnews/516732.htm
- http://m.wap.oexnr.cn/jnews/1540.htm
- http://m.wap.oexnr.cn/jnews/4218026.htm
- http://m.wap.oexnr.cn/jnews/6564.htm
- http://m.wap.oexnr.cn/jnews/5196674.htm
- http://m.wap.oexnr.cn/jnews/019726.htm
- http://m.wap.oexnr.cn/jnews/3130392.htm
- http://m.wap.oexnr.cn/jnews/0364820.htm
- http://m.wap.oexnr.cn/jnews/6918707.htm
- http://m.wap.oexnr.cn/jnews/4094.htm
- http://m.wap.oexnr.cn/jnews/3847.htm
- http://m.wap.oexnr.cn/jnews/675117.htm
- http://m.wap.oexnr.cn/jnews/004961.htm
- http://m.wap.oexnr.cn/jnews/969222.htm
- http://m.wap.oexnr.cn/jnews/2729984.htm
- http://m.wap.oexnr.cn/jnews/2189352.htm
- http://m.wap.oexnr.cn/jnews/8493695.htm
- http://m.wap.oexnr.cn/jnews/31105.htm
- http://m.wap.oexnr.cn/jnews/5181.htm
- http://m.wap.oexnr.cn/jnews/3017716.htm
- http://m.wap.oexnr.cn/jnews/2265722.htm
- http://m.wap.oexnr.cn/jnews/574259.htm
- http://m.wap.oexnr.cn/jnews/3278.htm
- http://m.wap.oexnr.cn/jnews/31800.htm
- http://m.wap.oexnr.cn/jnews/89527.htm
- http://m.wap.oexnr.cn/jnews/8774037.htm
- http://m.wap.oexnr.cn/jnews/0724.htm
- http://m.wap.oexnr.cn/jnews/9941.htm
- http://m.wap.oexnr.cn/jnews/598262.htm
- http://m.wap.oexnr.cn/jnews/4489405.htm
- http://m.wap.oexnr.cn/jnews/4753608.htm
- http://m.wap.oexnr.cn/jnews/6993.htm
- http://m.wap.oexnr.cn/jnews/2769355.htm
- http://m.wap.oexnr.cn/jnews/3162.htm
- http://m.wap.oexnr.cn/jnews/05530.htm
- http://m.wap.oexnr.cn/jnews/7040.htm
- http://m.wap.oexnr.cn/jnews/5722061.htm
- http://m.wap.oexnr.cn/jnews/011768.htm
- http://m.wap.oexnr.cn/jnews/4774.htm
- http://m.wap.oexnr.cn/jnews/8768494.htm
- http://m.wap.oexnr.cn/jnews/567533.htm
- http://m.wap.oexnr.cn/jnews/6182624.htm
- http://m.wap.oexnr.cn/jnews/4362.htm
- http://m.wap.oexnr.cn/jnews/24258.htm
- http://m.wap.oexnr.cn/jnews/65494.htm
- http://m.wap.oexnr.cn/jnews/7010573.htm
- http://m.wap.oexnr.cn/jnews/7450.htm
- http://m.wap.oexnr.cn/jnews/252531.htm
- http://m.wap.oexnr.cn/jnews/3240183.htm
- http://m.wap.oexnr.cn/jnews/8529.htm
- http://m.wap.oexnr.cn/jnews/7526.htm
- http://m.wap.oexnr.cn/jnews/432746.htm
- http://m.wap.oexnr.cn/jnews/9471233.htm
- http://m.wap.oexnr.cn/jnews/9197417.htm
- http://m.wap.oexnr.cn/jnews/848537.htm
- http://m.wap.oexnr.cn/jnews/061898.htm
- http://m.wap.oexnr.cn/jnews/4940.htm
- http://m.wap.oexnr.cn/jnews/35632.htm
- http://m.wap.oexnr.cn/jnews/747165.htm
- http://m.wap.oexnr.cn/jnews/3598.htm
- http://m.wap.oexnr.cn/jnews/48438.htm
- http://m.wap.oexnr.cn/jnews/17611.htm
- http://m.wap.oexnr.cn/jnews/17829.htm
- http://m.wap.oexnr.cn/jnews/8166139.htm
- http://m.wap.oexnr.cn/jnews/0903876.htm
- http://m.wap.oexnr.cn/jnews/10464.htm
- http://m.wap.oexnr.cn/jnews/841262.htm
- http://m.wap.oexnr.cn/jnews/7707.htm
- http://m.wap.oexnr.cn/jnews/06287.htm
- http://m.wap.oexnr.cn/jnews/06977.htm
- http://m.wap.oexnr.cn/jnews/0638395.htm
- http://m.wap.oexnr.cn/jnews/3424475.htm
- http://m.wap.oexnr.cn/jnews/78667.htm
- http://m.wap.oexnr.cn/jnews/1585.htm
- http://m.wap.oexnr.cn/jnews/08927.htm
- http://m.wap.oexnr.cn/jnews/49828.htm
- http://m.wap.oexnr.cn/jnews/7175560.htm
- http://m.wap.oexnr.cn/jnews/3398919.htm
- http://m.wap.oexnr.cn/jnews/018988.htm
- http://m.wap.oexnr.cn/jnews/0055736.htm
- http://m.wap.oexnr.cn/jnews/8276964.htm
- http://m.wap.oexnr.cn/jnews/421212.htm
- http://m.wap.oexnr.cn/jnews/0462.htm
- http://m.wap.oexnr.cn/jnews/7821028.htm
- http://m.wap.oexnr.cn/jnews/1409.htm
- http://m.wap.oexnr.cn/jnews/3883355.htm
- http://m.wap.oexnr.cn/jnews/09935.htm
- http://m.wap.oexnr.cn/jnews/63676.htm
- http://m.wap.oexnr.cn/jnews/10128.htm
- http://m.wap.oexnr.cn/jnews/4213.htm
- http://m.wap.oexnr.cn/jnews/987233.htm
- http://m.wap.oexnr.cn/jnews/665196.htm
- http://m.wap.oexnr.cn/jnews/779211.htm
- http://m.wap.oexnr.cn/jnews/1167.htm
- http://m.wap.oexnr.cn/jnews/4645766.htm
- http://m.wap.oexnr.cn/jnews/506066.htm
- http://m.wap.oexnr.cn/jnews/042289.htm
- http://m.wap.oexnr.cn/jnews/50214.htm
- http://m.wap.oexnr.cn/jnews/568254.htm
- http://m.wap.oexnr.cn/jnews/855312.htm
- http://m.wap.oexnr.cn/jnews/8621065.htm
- http://m.wap.oexnr.cn/jnews/629636.htm
- http://m.wap.oexnr.cn/jnews/9325607.htm
- http://m.wap.oexnr.cn/jnews/50098.htm
- http://m.wap.oexnr.cn/jnews/107181.htm
- http://m.wap.oexnr.cn/jnews/0022.htm
- http://m.wap.oexnr.cn/jnews/67030.htm
- http://m.wap.oexnr.cn/jnews/8034479.htm
- http://m.wap.oexnr.cn/jnews/3479429.htm
- http://m.wap.oexnr.cn/jnews/1368174.htm
- http://m.wap.oexnr.cn/jnews/6111.htm
- http://m.wap.oexnr.cn/jnews/77666.htm
- http://m.wap.oexnr.cn/jnews/53071.htm
- http://m.wap.oexnr.cn/jnews/6853317.htm
- http://m.wap.oexnr.cn/jnews/76879.htm
- http://m.wap.oexnr.cn/jnews/1487.htm
- http://m.wap.oexnr.cn/jnews/00005.htm
- http://m.wap.oexnr.cn/jnews/8208814.htm
- http://m.wap.oexnr.cn/jnews/7402664.htm
- http://m.wap.oexnr.cn/jnews/74592.htm
- http://m.wap.oexnr.cn/jnews/0703.htm
- http://m.wap.oexnr.cn/jnews/966448.htm
- http://m.wap.oexnr.cn/jnews/873584.htm
- http://m.wap.oexnr.cn/jnews/96385.htm
- http://m.wap.oexnr.cn/jnews/8717713.htm
- http://m.wap.oexnr.cn/jnews/38090.htm
- http://m.wap.oexnr.cn/jnews/73684.htm
- http://m.wap.oexnr.cn/jnews/9072694.htm
- http://m.wap.oexnr.cn/jnews/60892.htm
- http://m.wap.oexnr.cn/jnews/28948.htm
- http://m.wap.oexnr.cn/jnews/9619.htm
- http://m.wap.oexnr.cn/jnews/8024922.htm
- http://m.wap.oexnr.cn/jnews/605031.htm
- http://m.wap.oexnr.cn/jnews/01146.htm
- http://m.wap.oexnr.cn/jnews/76528.htm
- http://m.wap.oexnr.cn/jnews/801648.htm
- http://m.wap.oexnr.cn/jnews/2711.htm
- http://m.wap.oexnr.cn/jnews/42570.htm
- http://m.wap.oexnr.cn/jnews/15824.htm
- http://m.wap.oexnr.cn/jnews/95024.htm
- http://m.wap.oexnr.cn/jnews/928844.htm
- http://m.wap.oexnr.cn/jnews/4333.htm
- http://m.wap.oexnr.cn/jnews/2851443.htm
- http://m.wap.oexnr.cn/jnews/51435.htm
- http://m.wap.oexnr.cn/jnews/87049.htm
- http://m.wap.oexnr.cn/jnews/3692.htm
- http://m.wap.oexnr.cn/jnews/63069.htm
- http://m.wap.oexnr.cn/jnews/054816.htm
- http://m.wap.oexnr.cn/jnews/942438.htm
- http://m.wap.oexnr.cn/jnews/713245.htm
- http://m.wap.oexnr.cn/jnews/73807.htm
- http://m.wap.oexnr.cn/jnews/5030.htm
- http://m.wap.oexnr.cn/jnews/1511086.htm
- http://m.wap.oexnr.cn/jnews/9963.htm
- http://m.wap.oexnr.cn/jnews/967833.htm
- http://m.wap.oexnr.cn/jnews/09482.htm
- http://m.wap.oexnr.cn/jnews/856879.htm
- http://m.wap.oexnr.cn/jnews/1481855.htm
- http://m.wap.oexnr.cn/jnews/56608.htm
- http://m.wap.oexnr.cn/jnews/2755467.htm
- http://m.wap.oexnr.cn/jnews/7163.htm
- http://m.wap.oexnr.cn/jnews/2266157.htm
- http://m.wap.oexnr.cn/jnews/024340.htm
- http://m.wap.oexnr.cn/jnews/1463.htm
- http://m.wap.oexnr.cn/jnews/84927.htm
- http://m.wap.oexnr.cn/jnews/293336.htm
- http://m.wap.oexnr.cn/jnews/5738.htm
- http://m.wap.oexnr.cn/jnews/9318308.htm
- http://m.wap.oexnr.cn/jnews/2443687.htm
- http://m.wap.oexnr.cn/jnews/7390.htm
- http://m.wap.oexnr.cn/jnews/5519.htm
- http://m.wap.oexnr.cn/jnews/64558.htm
- http://m.wap.oexnr.cn/jnews/06904.htm
- http://m.wap.oexnr.cn/jnews/2448.htm
- http://m.wap.oexnr.cn/jnews/456862.htm
- http://m.wap.oexnr.cn/jnews/181273.htm
- http://m.wap.oexnr.cn/jnews/4947162.htm
- http://m.wap.oexnr.cn/jnews/12824.htm
- http://m.wap.oexnr.cn/jnews/74718.htm
- http://m.wap.oexnr.cn/jnews/94507.htm
- http://m.wap.oexnr.cn/jnews/5765.htm
- http://m.wap.oexnr.cn/jnews/53189.htm
- http://m.wap.oexnr.cn/jnews/6790363.htm
- http://m.wap.oexnr.cn/jnews/2537205.htm
- http://m.wap.oexnr.cn/jnews/832768.htm
- http://m.wap.oexnr.cn/jnews/8191592.htm
- http://m.wap.oexnr.cn/jnews/600126.htm
- http://m.wap.oexnr.cn/jnews/4399270.htm
- http://m.wap.oexnr.cn/jnews/28719.htm
- http://m.wap.oexnr.cn/jnews/87962.htm
- http://m.wap.oexnr.cn/jnews/7185019.htm
- http://m.wap.oexnr.cn/jnews/671302.htm
- http://m.wap.oexnr.cn/jnews/4272964.htm
- http://m.wap.oexnr.cn/jnews/96891.htm
- http://m.wap.oexnr.cn/jnews/5290.htm
- http://m.wap.oexnr.cn/jnews/942414.htm
- http://m.wap.oexnr.cn/jnews/2926.htm
- http://m.wap.oexnr.cn/jnews/762726.htm
- http://m.wap.oexnr.cn/jnews/5349803.htm
- http://m.wap.oexnr.cn/jnews/15074.htm
- http://m.wap.oexnr.cn/jnews/3942.htm
- http://m.wap.oexnr.cn/jnews/4645750.htm
- http://m.wap.oexnr.cn/jnews/84159.htm
- http://m.wap.oexnr.cn/jnews/4598.htm
- http://m.wap.oexnr.cn/jnews/881471.htm
- http://m.wap.oexnr.cn/jnews/59108.htm
- http://m.wap.oexnr.cn/jnews/0405452.htm
- http://m.wap.oexnr.cn/jnews/6747799.htm
- http://m.wap.oexnr.cn/jnews/1970.htm
- http://m.wap.oexnr.cn/jnews/874088.htm
- http://m.wap.oexnr.cn/jnews/8187185.htm
- http://m.wap.oexnr.cn/jnews/9104512.htm
- http://m.wap.oexnr.cn/jnews/6643.htm
- http://m.wap.oexnr.cn/jnews/27816.htm
- http://m.wap.oexnr.cn/jnews/5244.htm
- http://m.wap.oexnr.cn/jnews/52358.htm
- http://m.wap.oexnr.cn/jnews/8223176.htm
- http://m.wap.oexnr.cn/jnews/715075.htm
- http://m.wap.oexnr.cn/jnews/7289039.htm
- http://m.wap.oexnr.cn/jnews/55333.htm
- http://m.wap.oexnr.cn/jnews/33965.htm
- http://m.wap.oexnr.cn/jnews/601305.htm
- http://m.wap.oexnr.cn/jnews/563184.htm
- http://m.wap.oexnr.cn/jnews/675774.htm

## 项目结构

```
aggregator/
├── src/
│   ├── core/                     # 核心逻辑模块
│   │   ├── indexer.js            # 资源索引构建与更新
│   │   ├── fetcher.js            # HTTP 抓取与超时重试控制
│   │   └── parser.js             # HTML 元数据提取与清洗
│   ├── cli/                      # 命令行交互实现
│   │   ├── commands/             # 各子命令（sync, search, stats）
│   │   └── repl.js               # 交互式 REPL 环境
│   ├── api/                      # RESTful API 服务
│   │   ├── routes/               # 路由定义（资源查询、导入、统计）
│   │   └── middleware/           # 日志、限流、错误处理中间件
│   ├── db/                       # 数据库层
│   │   ├── schema.sql            # SQLite 表结构定义
│   │   └── repository.js         # CRUD 操作封装
│   └── scheduler/                # 定时任务调度
│       ├── cron.js               # cron 表达式解析与任务注册
│       └── worker.js             # 后台工作线程执行体
├── config/                       # 配置文件目录
│   ├── default.json              # 默认配置（抓取间隔、超时时间）
│   └── custom.json               # 用户自定义覆盖配置
├── docs/                         # 文档目录
│   ├── getting-started.md        # 快速入门指南
│   ├── api-reference.md          # API 接口详细文档
│   └── contributing.md           # 贡献者指南
├── tests/                        # 单元测试与集成测试
│   ├── unit/                     # 各模块单元测试
│   └── integration/              # API 与数据库集成测试
├── scripts/                      # 运维辅助脚本
│   ├── backup-db.sh              # 数据库备份脚本
│   └── migrate.sh                # 数据库迁移工具
├── .env.example                  # 环境变量模板
├── package.json                  # npm 项目配置与依赖声明
├── README.md                     # 项目说明文档（本文件）
└── LICENSE                       # MIT 许可证文本
```

## 贡献指南

1. 阅读项目文档中的贡献规范（docs/contributing.md），了解代码风格、提交信息格式和测试覆盖率要求。所有提交必须通过 ESLint 检查，且单元测试覆盖率不低于 80%。

2. 在 GitHub 仓库中提交 Issue 描述你发现的问题或希望新增的功能，等待维护者确认后再开始编码。对于重大功能变更，建议先通过 Issue 进行设计讨论，避免 PR 被拒绝。

3. Fork 项目仓库，在本地新建一个功能分支（feature/xxx 或 fix/xxx），在该分支上进行开发和测试。确保所有现有测试用例通过，并为新增代码编写对应的测试用例。

4. 提交 Pull Request 时，在描述中清晰说明改动内容、测试结果和影响范围。PR 需要至少一位维护者 Approve 后方可合并。合并后分支将被自动删除。

## 常见问题

问：同步任务执行时出现超时错误，如何解决？

答：超时通常由目标源站响应缓慢或网络不稳定引起。请检查 config/default.json 中的 fetch.timeout 字段，默认值为 30000 毫秒。你可以适当增大该值，例如设为 60000。同时，检查系统是否配置了 HTTP 代理，若存在代理，请在 .env 文件中设置 HTTP_PROXY 和 HTTPS_PROXY 环境变量。

问：数据库索引文件过大，如何清理历史数据？

答：SQLite 数据库在长期使用后可能积累大量已删除记录。你可以运行 npm run vacuum 命令执行数据库压缩。若需按时间清理旧数据，可使用 scripts/cleanup.js 脚本，指定保留天数参数，例如 node scripts/cleanup.js --days 90 将删除 90 天前标记为已读的资源记录。

问：CLI 界面无法正常启动，提示 "command not found"？

答：请确保在项目根目录下执行命令，并且 npm install 已成功完成。若使用全局安装模式，请检查 package.json 中的 bin 字段是否正确指向 src/cli/index.js。你也可以尝试使用 node src/cli/index.js 直接启动。如果问题仍然存在，请删除 node_modules 目录并重新执行 npm install。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
