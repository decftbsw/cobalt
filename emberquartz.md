# WebIndex Central

WebIndex Central 是一个面向技术调研、内容聚合与自动化外链管理的开源导航系统。该项目定位于帮助开发者、技术内容运营者以及数据调研团队，将分散在移动端新闻门户中的高质量信息条目进行统一索引、分类标注与状态监控。项目本身不生产内容，而是提供一套轻量级、可扩展的索引框架，用于管理指向第三方新闻详情的稳定链接集合，解决人工收藏易丢失、分类混乱、无法批量检测链接可用性等痛点。通过结构化的资源列表与模块化的项目组织，用户可以快速搭建属于自己的外链监控台，并集成到日常的数据采集或内容推荐流程中。

## 功能概览

**批量链接导入与标准化存储** 系统支持通过文本文件或标准输入流批量导入 URL 列表，自动识别协议头并生成规范化存储记录，所有链接均保留原始格式，不做自动跳转或协议改写。

**资源状态定期可访问性检测** 集成基于 HTTP 状态码的链接存活检测模块，可定时对索引库中的每条记录发起请求，标记异常链接并生成报表，便于运维人员及时清理或更新失效资源。

**分类标签与多维度检索** 允许用户为每条链接添加自定义标签（如行业、日期、来源模块），并基于标签组合进行快速过滤检索，提升大规模链接库下的查找效率。

**数据导出与外部系统对接** 提供 JSON、CSV 及纯文本格式的导出接口，支持将索引数据通过 API 方式推送至第三方数据分析平台或内容管理系统，方便二次开发与集成。

**轻量级 Web 管理界面** 内置基于 Python Flask 或 Node.js Express 的可选可视化面板，展示链接总数、今日新增、异常率等关键指标，并支持基础的增删改查操作，降低非技术用户的运维门槛。

**增量更新与去重机制** 在导入新资源时自动执行基于 URL 完整字符串的去重逻辑，避免同一链接被重复收录，同时支持增量追加模式，不影响已有条目状态。

**操作日志与变更追溯** 记录每一次链接的新增、删除、状态修改行为及操作时间戳，便于多人协作环境下追溯变更历史，满足审计合规需求。

## 应用场景

企业内部技术调研团队的知识库构建。调研人员日常会从多个移动新闻源收集与竞品动态、行业政策相关的参考文章链接。使用 WebIndex Central 可以快速将这些零散的链接归入统一索引，按日期和专题分类，每周自动生成链接可用性报告，减少人工检查时间。

开源社区文档与资源导航站点的后台管理。社区维护者需要为项目文档页或 Wiki 页面整理外部参考链接，但手动维护 Markdown 列表容易出错且无法监控死链。通过本项目的 API 接口，社区可以将链接管理逻辑与文档生成流水线结合，实现链接状态的半自动化维护。

数据采集管道中的种子链接暂存与调度。在分布式爬虫系统中，种子 URL 需要经过去重、过滤和状态验证后才能分发至下游采集节点。WebIndex Central 可作为轻量级种子暂存池，提供标准化的增删查接口，并与调度器联动，确保分发链路的稳定性。

## 快速开始

以下步骤适用于 Linux 及 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库到本地
git clone https://github.com/your-org/webindex-central.git
cd webindex-central

# 安装 Python 3.9+ 环境依赖（使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地 SQLite 数据库并创建默认表结构
python scripts/init_db.py

# 启动开发调试服务（默认监听 5000 端口）
python app.py runserver
```

访问 http://127.0.0.1:5000 即可进入管理面板首页。如需通过命令行导入初始资源列表，可使用 `cli/import.py` 工具并传入文本文件路径。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.11 | 核心运行环境，推荐使用 3.10 长期支持版 |
| SQLite | 3.28.0 及以上 | 内嵌数据库引擎，用于存储链接元数据与状态标记 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装依赖库 |
| Flask | 2.2.5 或 2.3.x 系列 | Web 管理面板与 API 服务的基础框架（可选，但建议安装） |
| requests | 2.28.0 及以上 | 用于执行链接存活检测的 HTTP 客户端库 |
| pytest | 7.2.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何在一台新机器上完成从克隆到首次启动的全过程？ |
| 运维手册 | docs/operations.md | 如何配置定期检测任务、如何导出异常链接列表、如何备份数据库？ |
| API 参考 | docs/api_reference.md | 外部系统如何通过 REST 接口新增、查询或删除索引条目？ |
| 数据模型 | docs/data_model.md | 链接记录包含哪些字段、状态枚举值的含义以及数据库表关联关系是什么？ |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/7423.htm
- http://m.wap.ghtkgg.cn/jnews/914883.htm
- http://m.wap.ghtkgg.cn/jnews/484693.htm
- http://m.wap.ghtkgg.cn/jnews/65663.htm
- http://m.wap.ghtkgg.cn/jnews/03629.htm
- http://m.wap.ghtkgg.cn/jnews/89568.htm
- http://m.wap.ghtkgg.cn/jnews/0603.htm
- http://m.wap.ghtkgg.cn/jnews/319233.htm
- http://m.wap.ghtkgg.cn/jnews/0541767.htm
- http://m.wap.ghtkgg.cn/jnews/60558.htm
- http://m.wap.ghtkgg.cn/jnews/9171.htm
- http://m.wap.ghtkgg.cn/jnews/6609.htm
- http://m.wap.ghtkgg.cn/jnews/3415216.htm
- http://m.wap.ghtkgg.cn/jnews/40950.htm
- http://m.wap.ghtkgg.cn/jnews/033043.htm
- http://m.wap.ghtkgg.cn/jnews/70288.htm
- http://m.wap.ghtkgg.cn/jnews/7580.htm
- http://m.wap.ghtkgg.cn/jnews/718186.htm
- http://m.wap.ghtkgg.cn/jnews/744281.htm
- http://m.wap.ghtkgg.cn/jnews/847885.htm
- http://m.wap.ghtkgg.cn/jnews/10787.htm
- http://m.wap.ghtkgg.cn/jnews/0196353.htm
- http://m.wap.ghtkgg.cn/jnews/97177.htm
- http://m.wap.ghtkgg.cn/jnews/956573.htm
- http://m.wap.ghtkgg.cn/jnews/968661.htm
- http://m.wap.ghtkgg.cn/jnews/4669.htm
- http://m.wap.ghtkgg.cn/jnews/197011.htm
- http://m.wap.ghtkgg.cn/jnews/31999.htm
- http://m.wap.ghtkgg.cn/jnews/0978965.htm
- http://m.wap.ghtkgg.cn/jnews/141421.htm
- http://m.wap.ghtkgg.cn/jnews/5648.htm
- http://m.wap.ghtkgg.cn/jnews/16205.htm
- http://m.wap.ghtkgg.cn/jnews/9528694.htm
- http://m.wap.ghtkgg.cn/jnews/599742.htm
- http://m.wap.ghtkgg.cn/jnews/7448254.htm
- http://m.wap.ghtkgg.cn/jnews/5549.htm
- http://m.wap.ghtkgg.cn/jnews/3295707.htm
- http://m.wap.ghtkgg.cn/jnews/535398.htm
- http://m.wap.ghtkgg.cn/jnews/26763.htm
- http://m.wap.ghtkgg.cn/jnews/7148.htm
- http://m.wap.ghtkgg.cn/jnews/29835.htm
- http://m.wap.ghtkgg.cn/jnews/97746.htm
- http://m.wap.ghtkgg.cn/jnews/87991.htm
- http://m.wap.ghtkgg.cn/jnews/8793.htm
- http://m.wap.ghtkgg.cn/jnews/59663.htm
- http://m.wap.ghtkgg.cn/jnews/7416.htm
- http://m.wap.ghtkgg.cn/jnews/39078.htm
- http://m.wap.ghtkgg.cn/jnews/6884.htm
- http://m.wap.ghtkgg.cn/jnews/930976.htm
- http://m.wap.ghtkgg.cn/jnews/786813.htm
- http://m.wap.ghtkgg.cn/jnews/21797.htm
- http://m.wap.ghtkgg.cn/jnews/32265.htm
- http://m.wap.ghtkgg.cn/jnews/7649.htm
- http://m.wap.ghtkgg.cn/jnews/8749690.htm
- http://m.wap.ghtkgg.cn/jnews/656067.htm
- http://m.wap.ghtkgg.cn/jnews/9104.htm
- http://m.wap.ghtkgg.cn/jnews/8961.htm
- http://m.wap.ghtkgg.cn/jnews/081642.htm
- http://m.wap.ghtkgg.cn/jnews/10183.htm
- http://m.wap.ghtkgg.cn/jnews/97093.htm
- http://m.wap.ghtkgg.cn/jnews/27508.htm
- http://m.wap.ghtkgg.cn/jnews/24812.htm
- http://m.wap.ghtkgg.cn/jnews/91835.htm
- http://m.wap.ghtkgg.cn/jnews/74947.htm
- http://m.wap.ghtkgg.cn/jnews/81050.htm
- http://m.wap.ghtkgg.cn/jnews/349241.htm
- http://m.wap.ghtkgg.cn/jnews/67690.htm
- http://m.wap.ghtkgg.cn/jnews/6044.htm
- http://m.wap.ghtkgg.cn/jnews/82847.htm
- http://m.wap.ghtkgg.cn/jnews/7062.htm
- http://m.wap.ghtkgg.cn/jnews/368810.htm
- http://m.wap.ghtkgg.cn/jnews/2683756.htm
- http://m.wap.ghtkgg.cn/jnews/3813438.htm
- http://m.wap.ghtkgg.cn/jnews/39500.htm
- http://m.wap.ghtkgg.cn/jnews/2810785.htm
- http://m.wap.ghtkgg.cn/jnews/150218.htm
- http://m.wap.ghtkgg.cn/jnews/99069.htm
- http://m.wap.ghtkgg.cn/jnews/863512.htm
- http://m.wap.ghtkgg.cn/jnews/2513.htm
- http://m.wap.ghtkgg.cn/jnews/591618.htm
- http://m.wap.ghtkgg.cn/jnews/3756.htm
- http://m.wap.ghtkgg.cn/jnews/1378.htm
- http://m.wap.ghtkgg.cn/jnews/2410.htm
- http://m.wap.ghtkgg.cn/jnews/858863.htm
- http://m.wap.ghtkgg.cn/jnews/98704.htm
- http://m.wap.ghtkgg.cn/jnews/7819981.htm
- http://m.wap.ghtkgg.cn/jnews/9732.htm
- http://m.wap.ghtkgg.cn/jnews/60438.htm
- http://m.wap.ghtkgg.cn/jnews/04180.htm
- http://m.wap.ghtkgg.cn/jnews/0635.htm
- http://m.wap.ghtkgg.cn/jnews/813806.htm
- http://m.wap.ghtkgg.cn/jnews/317780.htm
- http://m.wap.ghtkgg.cn/jnews/6360837.htm
- http://m.wap.ghtkgg.cn/jnews/874033.htm
- http://m.wap.ghtkgg.cn/jnews/8426.htm
- http://m.wap.ghtkgg.cn/jnews/65667.htm
- http://m.wap.ghtkgg.cn/jnews/9147.htm
- http://m.wap.ghtkgg.cn/jnews/9672.htm
- http://m.wap.ghtkgg.cn/jnews/85781.htm
- http://m.wap.ghtkgg.cn/jnews/0946511.htm
- http://m.wap.ghtkgg.cn/jnews/4299.htm
- http://m.wap.ghtkgg.cn/jnews/0357077.htm
- http://m.wap.ghtkgg.cn/jnews/68804.htm
- http://m.wap.ghtkgg.cn/jnews/680673.htm
- http://m.wap.ghtkgg.cn/jnews/080795.htm
- http://m.wap.ghtkgg.cn/jnews/057977.htm
- http://m.wap.ghtkgg.cn/jnews/85478.htm
- http://m.wap.ghtkgg.cn/jnews/2121.htm
- http://m.wap.ghtkgg.cn/jnews/754588.htm
- http://m.wap.ghtkgg.cn/jnews/925804.htm
- http://m.wap.ghtkgg.cn/jnews/1344308.htm
- http://m.wap.ghtkgg.cn/jnews/375093.htm
- http://m.wap.ghtkgg.cn/jnews/304876.htm
- http://m.wap.ghtkgg.cn/jnews/98402.htm
- http://m.wap.ghtkgg.cn/jnews/3915.htm
- http://m.wap.ghtkgg.cn/jnews/525359.htm
- http://m.wap.ghtkgg.cn/jnews/0533065.htm
- http://m.wap.ghtkgg.cn/jnews/79603.htm
- http://m.wap.ghtkgg.cn/jnews/4457876.htm
- http://m.wap.ghtkgg.cn/jnews/10321.htm
- http://m.wap.ghtkgg.cn/jnews/6123.htm
- http://m.wap.ghtkgg.cn/jnews/747498.htm
- http://m.wap.ghtkgg.cn/jnews/05873.htm
- http://m.wap.ghtkgg.cn/jnews/462017.htm
- http://m.wap.ghtkgg.cn/jnews/6686299.htm
- http://m.wap.ghtkgg.cn/jnews/7495.htm
- http://m.wap.ghtkgg.cn/jnews/47737.htm
- http://m.wap.ghtkgg.cn/jnews/69326.htm
- http://m.wap.ghtkgg.cn/jnews/6929.htm
- http://m.wap.ghtkgg.cn/jnews/59268.htm
- http://m.wap.ghtkgg.cn/jnews/115281.htm
- http://m.wap.ghtkgg.cn/jnews/3321972.htm
- http://m.wap.ghtkgg.cn/jnews/502099.htm
- http://m.wap.ghtkgg.cn/jnews/3458.htm
- http://m.wap.ghtkgg.cn/jnews/74145.htm
- http://m.wap.ghtkgg.cn/jnews/5078.htm
- http://m.wap.ghtkgg.cn/jnews/369492.htm
- http://m.wap.ghtkgg.cn/jnews/1393.htm
- http://m.wap.ghtkgg.cn/jnews/09051.htm
- http://m.wap.ghtkgg.cn/jnews/729415.htm
- http://m.wap.ghtkgg.cn/jnews/992715.htm
- http://m.wap.ghtkgg.cn/jnews/2263888.htm
- http://m.wap.ghtkgg.cn/jnews/637410.htm
- http://m.wap.ghtkgg.cn/jnews/89268.htm
- http://m.wap.ghtkgg.cn/jnews/6780653.htm
- http://m.wap.ghtkgg.cn/jnews/5065458.htm
- http://m.wap.ghtkgg.cn/jnews/1270.htm
- http://m.wap.ghtkgg.cn/jnews/180714.htm
- http://m.wap.ghtkgg.cn/jnews/9345.htm
- http://m.wap.ghtkgg.cn/jnews/2166015.htm
- http://m.wap.ghtkgg.cn/jnews/552281.htm
- http://m.wap.ghtkgg.cn/jnews/687079.htm
- http://m.wap.ghtkgg.cn/jnews/7095.htm
- http://m.wap.ghtkgg.cn/jnews/1199.htm
- http://m.wap.ghtkgg.cn/jnews/4906.htm
- http://m.wap.ghtkgg.cn/jnews/40487.htm
- http://m.wap.ghtkgg.cn/jnews/96757.htm
- http://m.wap.ghtkgg.cn/jnews/5173.htm
- http://m.wap.ghtkgg.cn/jnews/1972128.htm
- http://m.wap.ghtkgg.cn/jnews/4218.htm
- http://m.wap.ghtkgg.cn/jnews/44874.htm
- http://m.wap.ghtkgg.cn/jnews/494397.htm
- http://m.wap.ghtkgg.cn/jnews/107099.htm
- http://m.wap.ghtkgg.cn/jnews/0909.htm
- http://m.wap.ghtkgg.cn/jnews/84322.htm
- http://m.wap.ghtkgg.cn/jnews/33468.htm
- http://m.wap.ghtkgg.cn/jnews/4712585.htm
- http://m.wap.ghtkgg.cn/jnews/1143256.htm
- http://m.wap.ghtkgg.cn/jnews/1028317.htm
- http://m.wap.ghtkgg.cn/jnews/843245.htm
- http://m.wap.ghtkgg.cn/jnews/45293.htm
- http://m.wap.ghtkgg.cn/jnews/01084.htm
- http://m.wap.ghtkgg.cn/jnews/8869362.htm
- http://m.wap.ghtkgg.cn/jnews/1153127.htm
- http://m.wap.ghtkgg.cn/jnews/93748.htm
- http://m.wap.ghtkgg.cn/jnews/6041176.htm
- http://m.wap.ghtkgg.cn/jnews/619852.htm
- http://m.wap.ghtkgg.cn/jnews/17248.htm
- http://m.wap.ghtkgg.cn/jnews/73025.htm
- http://m.wap.ghtkgg.cn/jnews/092602.htm
- http://m.wap.ghtkgg.cn/jnews/0969.htm
- http://m.wap.ghtkgg.cn/jnews/5119.htm
- http://m.wap.ghtkgg.cn/jnews/309047.htm
- http://m.wap.ghtkgg.cn/jnews/92900.htm
- http://m.wap.ghtkgg.cn/jnews/07177.htm
- http://m.wap.ghtkgg.cn/jnews/328673.htm
- http://m.wap.ghtkgg.cn/jnews/6739473.htm
- http://m.wap.ghtkgg.cn/jnews/62505.htm
- http://m.wap.ghtkgg.cn/jnews/7370466.htm
- http://m.wap.ghtkgg.cn/jnews/7977.htm
- http://m.wap.ghtkgg.cn/jnews/3137.htm
- http://m.wap.ghtkgg.cn/jnews/5611567.htm
- http://m.wap.ghtkgg.cn/jnews/842594.htm
- http://m.wap.ghtkgg.cn/jnews/845247.htm
- http://m.wap.ghtkgg.cn/jnews/70623.htm
- http://m.wap.ghtkgg.cn/jnews/51705.htm
- http://m.wap.ghtkgg.cn/jnews/650063.htm
- http://m.wap.ghtkgg.cn/jnews/406997.htm
- http://m.wap.ghtkgg.cn/jnews/75125.htm
- http://m.wap.ghtkgg.cn/jnews/2115834.htm
- http://m.wap.ghtkgg.cn/jnews/7840122.htm
- http://m.wap.ghtkgg.cn/jnews/8052180.htm
- http://m.wap.ghtkgg.cn/jnews/650102.htm
- http://m.wap.ghtkgg.cn/jnews/82807.htm
- http://m.wap.ghtkgg.cn/jnews/276713.htm
- http://m.wap.ghtkgg.cn/jnews/2485619.htm
- http://m.wap.ghtkgg.cn/jnews/5662129.htm
- http://m.wap.ghtkgg.cn/jnews/4672671.htm
- http://m.wap.ghtkgg.cn/jnews/0892.htm
- http://m.wap.ghtkgg.cn/jnews/711085.htm
- http://m.wap.ghtkgg.cn/jnews/649499.htm
- http://m.wap.ghtkgg.cn/jnews/13288.htm
- http://m.wap.ghtkgg.cn/jnews/24777.htm
- http://m.wap.ghtkgg.cn/jnews/3075.htm
- http://m.wap.ghtkgg.cn/jnews/39731.htm
- http://m.wap.ghtkgg.cn/jnews/2455.htm
- http://m.wap.ghtkgg.cn/jnews/580040.htm
- http://m.wap.ghtkgg.cn/jnews/8580219.htm
- http://m.wap.ghtkgg.cn/jnews/805586.htm
- http://m.wap.ghtkgg.cn/jnews/17328.htm
- http://m.wap.ghtkgg.cn/jnews/15906.htm
- http://m.wap.ghtkgg.cn/jnews/5938722.htm
- http://m.wap.ghtkgg.cn/jnews/910601.htm
- http://m.wap.ghtkgg.cn/jnews/3275.htm
- http://m.wap.ghtkgg.cn/jnews/7706.htm
- http://m.wap.ghtkgg.cn/jnews/40009.htm
- http://m.wap.ghtkgg.cn/jnews/567121.htm
- http://m.wap.ghtkgg.cn/jnews/4160.htm
- http://m.wap.ghtkgg.cn/jnews/4750.htm
- http://m.wap.ghtkgg.cn/jnews/341138.htm
- http://m.wap.ghtkgg.cn/jnews/67117.htm
- http://m.wap.ghtkgg.cn/jnews/227972.htm
- http://m.wap.ghtkgg.cn/jnews/8864283.htm
- http://m.wap.ghtkgg.cn/jnews/11174.htm
- http://m.wap.ghtkgg.cn/jnews/61755.htm
- http://m.wap.ghtkgg.cn/jnews/60633.htm
- http://m.wap.ghtkgg.cn/jnews/2838377.htm
- http://m.wap.ghtkgg.cn/jnews/4888.htm
- http://m.wap.ghtkgg.cn/jnews/8379.htm
- http://m.wap.ghtkgg.cn/jnews/5384522.htm
- http://m.wap.ghtkgg.cn/jnews/0050412.htm
- http://m.wap.ghtkgg.cn/jnews/959074.htm
- http://m.wap.ghtkgg.cn/jnews/1459.htm
- http://m.wap.ghtkgg.cn/jnews/4305.htm
- http://m.wap.ghtkgg.cn/jnews/09958.htm
- http://m.wap.ghtkgg.cn/jnews/7419.htm
- http://m.wap.ghtkgg.cn/jnews/0215.htm
- http://m.wap.ghtkgg.cn/jnews/5323548.htm
- http://m.wap.ghtkgg.cn/jnews/429798.htm
- http://m.wap.ghtkgg.cn/jnews/272745.htm
- http://m.wap.ghtkgg.cn/jnews/52053.htm
- http://m.wap.ghtkgg.cn/jnews/9629.htm
- http://m.wap.ghtkgg.cn/jnews/5368.htm
- http://m.wap.ghtkgg.cn/jnews/473862.htm
- http://m.wap.ghtkgg.cn/jnews/76519.htm
- http://m.wap.ghtkgg.cn/jnews/8255742.htm
- http://m.wap.ghtkgg.cn/jnews/887586.htm
- http://m.wap.ghtkgg.cn/jnews/6437.htm
- http://m.wap.ghtkgg.cn/jnews/0772.htm
- http://m.wap.ghtkgg.cn/jnews/3212739.htm
- http://m.wap.ghtkgg.cn/jnews/866873.htm
- http://m.wap.ghtkgg.cn/jnews/3310177.htm
- http://m.wap.ghtkgg.cn/jnews/5530.htm
- http://m.wap.ghtkgg.cn/jnews/217264.htm
- http://m.wap.ghtkgg.cn/jnews/23241.htm
- http://m.wap.ghtkgg.cn/jnews/9743.htm
- http://m.wap.ghtkgg.cn/jnews/0768427.htm
- http://m.wap.ghtkgg.cn/jnews/1680.htm
- http://m.wap.ghtkgg.cn/jnews/7295609.htm
- http://m.wap.ghtkgg.cn/jnews/678693.htm
- http://m.wap.ghtkgg.cn/jnews/2279991.htm
- http://m.wap.ghtkgg.cn/jnews/1395.htm
- http://m.wap.ghtkgg.cn/jnews/8734.htm
- http://m.wap.ghtkgg.cn/jnews/891827.htm
- http://m.wap.ghtkgg.cn/jnews/564507.htm
- http://m.wap.ghtkgg.cn/jnews/139758.htm
- http://m.wap.ghtkgg.cn/jnews/225287.htm
- http://m.wap.ghtkgg.cn/jnews/2239974.htm
- http://m.wap.ghtkgg.cn/jnews/9527212.htm
- http://m.wap.ghtkgg.cn/jnews/3709780.htm
- http://m.wap.ghtkgg.cn/jnews/30907.htm
- http://m.wap.ghtkgg.cn/jnews/454857.htm
- http://m.wap.ghtkgg.cn/jnews/013569.htm
- http://m.wap.ghtkgg.cn/jnews/3823.htm
- http://m.wap.ghtkgg.cn/jnews/5422357.htm
- http://m.wap.ghtkgg.cn/jnews/32751.htm
- http://m.wap.ghtkgg.cn/jnews/4485.htm
- http://m.wap.ghtkgg.cn/jnews/82417.htm
- http://m.wap.ghtkgg.cn/jnews/3507058.htm
- http://m.wap.ghtkgg.cn/jnews/4529.htm
- http://m.wap.ghtkgg.cn/jnews/7259409.htm
- http://m.wap.ghtkgg.cn/jnews/43112.htm
- http://m.wap.ghtkgg.cn/jnews/7553.htm
- http://m.wap.ghtkgg.cn/jnews/1414.htm
- http://m.wap.ghtkgg.cn/jnews/9158.htm
- http://m.wap.ghtkgg.cn/jnews/573033.htm
- http://m.wap.ghtkgg.cn/jnews/91709.htm
- http://m.wap.ghtkgg.cn/jnews/439526.htm
- http://m.wap.ghtkgg.cn/jnews/9467.htm
- http://m.wap.ghtkgg.cn/jnews/0147140.htm

## 项目结构

```
webindex-central/
├── app/                                # 核心应用包
│   ├── __init__.py                     # 应用工厂与配置加载入口
│   ├── models.py                       # SQLAlchemy ORM 数据模型（Link, Tag, AuditLog）
│   ├── routes/                         # 蓝图路由模块
│   │   ├── api_v1.py                   # RESTful API 端点（增删改查 + 状态检测）
│   │   └── dashboard.py                # Web 管理面板页面路由
│   ├── services/                       # 业务逻辑层
│   │   ├── link_importer.py            # 批量导入与去重处理
│   │   ├── health_checker.py           # 基于 requests 的并发存活检测
│   │   └── exporter.py                 # JSON / CSV 导出生成器
│   └── templates/                      # Jinja2 前端模板
│       ├── base.html                   # 基础布局骨架
│       └── index.html                  # 仪表板主页
├── cli/                                # 命令行工具集
│   ├── import.py                       # 从文件或 stdin 导入链接列表
│   └── check.py                        # 手动触发全量链接状态检测
├── scripts/                            # 运维与初始化脚本
│   ├── init_db.py                      # 创建 SQLite 数据库及表结构
│   └── migrate_v1_to_v2.py             # 版本迁移脚本（保留历史数据）
├── tests/                              # 单元测试与集成测试套件
│   ├── test_models.py                  # 数据模型层测试
│   └── test_api.py                     # API 端点响应与状态码测试
├── docs/                               # 完整文档存放目录
│   ├── getting_started.md              # 快速入门与环境配置详解
│   ├── operations.md                   # 日常运维与监控指南
│   ├── api_reference.md                # 接口参数与返回示例
│   └── data_model.md                   # 字段定义与 ER 关系图描述
├── requirements.txt                    # 生产环境 Python 依赖锁定
├── requirements-dev.txt                # 开发环境额外依赖（pytest, flake8）
├── Dockerfile                          # 基于 Alpine Linux 的容器镜像构建文件
├── docker-compose.yml                  # 本地开发容器编排（含 Redis 缓存可选）
└── README.md                           # 项目总览与入口文档（本文件）
```

## 贡献指南

1. 在 GitHub 仓库的 Issues 区域查找标记为 `help-wanted` 或 `good-first-issue` 的任务，或根据自身需求创建新的 Issue 描述待解决的问题，等待维护者确认需求合理性。

2. 从仓库主分支 `main` 切出新的功能分支，命名规范为 `feature/功能简述` 或 `fix/问题简述`，并在本地环境完成代码编写与自测，确保不影响现有核心功能。

3. 运行完整的测试套件（`pytest tests/`）以保证所有用例通过，同时使用 `flake8` 或 `black` 对修改的 Python 文件进行代码风格检查，维持与项目现有风格一致。

4. 提交 Pull Request 至 `main` 分支，在 PR 描述中清晰列出变更内容、涉及模块以及测试覆盖情况，并关联相关的 Issue 编号，等待至少一位维护者进行 Code Review。

5. 根据 Review 意见进行修改并补充必要的文档注释，在变更涉及 API 或数据模型时同步更新 `docs/` 目录下的对应文档，最终由维护者合并。

## 常见问题

**问：导入链接时提示去重命中，但我想强制重新导入并刷新状态，应该如何处理？**

答：默认情况下系统会基于 URL 完整字符串进行去重。若需要强制覆盖，可以在导入命令中添加 `--force` 参数（如 `python cli/import.py --force links.txt`），该操作会将匹配到的已存在记录更新为最新导入时间，并重置其状态检测标记为待检测。

**问：检测模块返回大量超时或连接错误，是否会影响正常链接的检测效率？**

答：健康检查器默认采用并发请求模式，单次超时时间设置为 5 秒，并发数上限为 20。若目标站点响应较慢，可通过修改 `app/services/health_checker.py` 中的 `TIMEOUT` 和 `MAX_WORKERS` 变量调整策略。建议在低峰时段运行全量检测，或利用 `--only-failed` 参数仅重试异常链接。

**问：项目是否支持 PostgreSQL 替代 SQLite 作为生产数据库？**

答：支持。项目使用 SQLAlchemy ORM，只需在实例配置中将 `SQLALCHEMY_DATABASE_URI` 修改为 PostgreSQL 连接串（如 `postgresql://user:pass@localhost/dbname`），并安装 `psycopg2` 驱动即可。但需注意 PostgreSQL 下的字符串比较行为与 SQLite 存在细微差异，建议迁移后对去重逻辑进行回归测试。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
