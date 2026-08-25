# WebLink Harvest 聚合导航系统

WebLink Harvest 是一个面向技术研究者、信息分析人员和内容聚合者的高密度外链资源管理与导航系统。本项目定位于对分散在多个内容源、多种格式下的外部链接进行统一采集、结构化存储、分类索引与快速检索，帮助用户在海量碎片化信息中建立有序的访问入口。系统以轻量化架构为核心，支持静态部署与动态更新两种模式，适用于个人知识库构建、团队协作资源共享以及自动化信息采集链路中的链接中转环节。

本项目并非简单的书签管理工具，而是专注于处理大量不定长、非标准格式、来源复杂的 URL 集合。系统内置了链接去重、来源追溯、有效性预检和访问统计等数据治理功能，能够显著降低人工整理海量外链时的维护成本。项目默认以批次（Batch）为组织单元，每个批次可承载数百至数千条链接，并提供基于标签、域名、时间维度的多级筛选视图。

第 59/300 批资源已作为默认数据源预置在系统中。

## 功能概览

批量链接导入：支持通过文本文件、JSON 数组或直接粘贴原始 URL 列表的方式批量导入链接数据，系统自动解析并校验 URL 格式。

智能去重与合并：基于 URL 标准化算法对导入的链接进行去重处理，对同源不同参数的变体链接执行合并与规范重写。

域名聚合统计：自动提取链接中的顶级域名与二级域名，生成域名访问热力图，快速识别高频资源站点。

自定义标签分类：允许用户为每条链接添加多个自定义标签，支持标签层级嵌套与跨标签快速筛选。

链接可用性检测：内置异步 HTTP 探针，可配置定时任务对已收录链接进行可用性检查，标记失效链接并记录响应状态码。

多维度检索查询：支持按域名、标签、导入批次、关键字全文检索以及正则表达式匹配等多种查询方式。

数据导入导出：提供 JSON、CSV、Markdown 表格三种导出格式，支持与其他知识管理工具（如 Obsidian、Notion）进行数据交换。

## 应用场景

技术文档归档与查阅：开发者在日常阅读技术博客、开源项目文档或 API 参考时，可将分散在数十个标签页中的链接统一收录至 WebLink Harvest，并按技术栈（如 React、Rust、Kubernetes）打标签分类。后续需要查阅特定主题时，可通过标签筛选快速定位历史阅读过的优质文档。

信息采集管道中转：数据采集工程师在构建分布式爬虫系统时，可使用本系统作为 URL 暂存池。各采集节点将提取到的原始链接推入系统，经过去重和域名白名单过滤后再分发给下游解析模块，有效避免重复抓取和域名污染。

团队知识共享库：产品、运营与技术团队可将各自积累的外部参考链接汇总至同一系统中，通过批次编号（如第 59/300 批）进行版本管理。新成员入职时可直接按批次浏览历史积累的资源，快速了解业务相关的信息生态。

安全分析溯源：安全研究人员在分析钓鱼网站、恶意域名或 C2 服务器时，需要大量记录可疑 URL。本系统的批量导入和域名聚合统计功能可辅助研究人员快速归类同一域名下的不同路径，理清攻击基础设施的分布规律。

个人阅读队列管理：日常通过 RSS、社交媒体或邮件简报获取大量待读文章链接的用户，可将链接暂存至系统，利用可用性检测功能预先过滤已失效的链接，再集中安排阅读时间，提升信息消费效率。

## 快速开始

以下命令将项目克隆至本地、安装依赖并启动开发服务器。

```bash
git clone https://github.com/weblink-harvest/weblink-harvest.git
cd weblink-harvest
npm install
npm run dev
```

生产环境构建与启动：

```bash
npm run build
npm run start
```

Docker 部署方式：

```bash
docker build -t weblink-harvest:latest .
docker run -p 3000:3000 -d weblink-harvest:latest
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时环境，推荐使用 LTS 版本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.39 或更高 | 默认嵌入式数据库，用于链接元数据存储 |
| Redis | 7.0 或更高 | 可选组件，启用缓存与任务队列时需安装 |
| PM2 | 5.x 或更高 | 可选组件，用于生产环境进程守护 |
| Nginx | 1.24 或更高 | 可选组件，用于反向代理与静态资源加速 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/getting-started.md | 如何快速部署并导入第一批链接数据？系统初始配置有哪些必填项？ |
| 数据管理 | /docs/data-management.md | 如何批量导入、导出和清理链接数据？去重规则是如何设计的？ |
| API 参考 | /docs/api-reference.md | 系统提供了哪些 RESTful API 接口？如何通过 API 实现自动化链接推送？ |
| 运维手册 | /docs/operations.md | 如何配置定时可用性检测？如何备份和恢复数据库？日志系统如何对接？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/07361.htm
- http://m.wap.oexnr.cn/jnews/8598.htm
- http://m.wap.oexnr.cn/jnews/2430596.htm
- http://m.wap.oexnr.cn/jnews/523641.htm
- http://m.wap.oexnr.cn/jnews/73221.htm
- http://m.wap.oexnr.cn/jnews/1724.htm
- http://m.wap.oexnr.cn/jnews/408308.htm
- http://m.wap.oexnr.cn/jnews/505004.htm
- http://m.wap.oexnr.cn/jnews/87850.htm
- http://m.wap.oexnr.cn/jnews/8024284.htm
- http://m.wap.oexnr.cn/jnews/255428.htm
- http://m.wap.oexnr.cn/jnews/098783.htm
- http://m.wap.oexnr.cn/jnews/9325.htm
- http://m.wap.oexnr.cn/jnews/86299.htm
- http://m.wap.oexnr.cn/jnews/9041.htm
- http://m.wap.oexnr.cn/jnews/4002.htm
- http://m.wap.oexnr.cn/jnews/38182.htm
- http://m.wap.oexnr.cn/jnews/076351.htm
- http://m.wap.oexnr.cn/jnews/319476.htm
- http://m.wap.oexnr.cn/jnews/5878.htm
- http://m.wap.oexnr.cn/jnews/0743234.htm
- http://m.wap.oexnr.cn/jnews/1746710.htm
- http://m.wap.oexnr.cn/jnews/3463472.htm
- http://m.wap.oexnr.cn/jnews/75675.htm
- http://m.wap.oexnr.cn/jnews/60164.htm
- http://m.wap.oexnr.cn/jnews/9731.htm
- http://m.wap.oexnr.cn/jnews/7164474.htm
- http://m.wap.oexnr.cn/jnews/35023.htm
- http://m.wap.oexnr.cn/jnews/92959.htm
- http://m.wap.oexnr.cn/jnews/88806.htm
- http://m.wap.oexnr.cn/jnews/258722.htm
- http://m.wap.oexnr.cn/jnews/7285.htm
- http://m.wap.oexnr.cn/jnews/7498645.htm
- http://m.wap.oexnr.cn/jnews/05190.htm
- http://m.wap.oexnr.cn/jnews/27602.htm
- http://m.wap.oexnr.cn/jnews/782910.htm
- http://m.wap.oexnr.cn/jnews/3784880.htm
- http://m.wap.oexnr.cn/jnews/987066.htm
- http://m.wap.oexnr.cn/jnews/6108571.htm
- http://m.wap.oexnr.cn/jnews/3133325.htm
- http://m.wap.oexnr.cn/jnews/53661.htm
- http://m.wap.oexnr.cn/jnews/471279.htm
- http://m.wap.oexnr.cn/jnews/9571.htm
- http://m.wap.oexnr.cn/jnews/62813.htm
- http://m.wap.oexnr.cn/jnews/70121.htm
- http://m.wap.oexnr.cn/jnews/9155423.htm
- http://m.wap.oexnr.cn/jnews/06471.htm
- http://m.wap.oexnr.cn/jnews/122939.htm
- http://m.wap.oexnr.cn/jnews/29877.htm
- http://m.wap.oexnr.cn/jnews/9054.htm
- http://m.wap.oexnr.cn/jnews/70922.htm
- http://m.wap.oexnr.cn/jnews/268405.htm
- http://m.wap.oexnr.cn/jnews/3464.htm
- http://m.wap.oexnr.cn/jnews/83415.htm
- http://m.wap.oexnr.cn/jnews/9679.htm
- http://m.wap.oexnr.cn/jnews/4284316.htm
- http://m.wap.oexnr.cn/jnews/0273942.htm
- http://m.wap.oexnr.cn/jnews/3624.htm
- http://m.wap.oexnr.cn/jnews/2809977.htm
- http://m.wap.oexnr.cn/jnews/7881249.htm
- http://m.wap.oexnr.cn/jnews/3796011.htm
- http://m.wap.oexnr.cn/jnews/9391.htm
- http://m.wap.oexnr.cn/jnews/5134.htm
- http://m.wap.oexnr.cn/jnews/835040.htm
- http://m.wap.oexnr.cn/jnews/7440147.htm
- http://m.wap.oexnr.cn/jnews/93791.htm
- http://m.wap.oexnr.cn/jnews/360403.htm
- http://m.wap.oexnr.cn/jnews/820379.htm
- http://m.wap.oexnr.cn/jnews/9086272.htm
- http://m.wap.oexnr.cn/jnews/523329.htm
- http://m.wap.oexnr.cn/jnews/908257.htm
- http://m.wap.oexnr.cn/jnews/8448.htm
- http://m.wap.oexnr.cn/jnews/9381.htm
- http://m.wap.oexnr.cn/jnews/02050.htm
- http://m.wap.oexnr.cn/jnews/969148.htm
- http://m.wap.oexnr.cn/jnews/8142994.htm
- http://m.wap.oexnr.cn/jnews/0618.htm
- http://m.wap.oexnr.cn/jnews/978272.htm
- http://m.wap.oexnr.cn/jnews/2635.htm
- http://m.wap.oexnr.cn/jnews/5019.htm
- http://m.wap.oexnr.cn/jnews/9450.htm
- http://m.wap.oexnr.cn/jnews/834085.htm
- http://m.wap.oexnr.cn/jnews/9931.htm
- http://m.wap.oexnr.cn/jnews/874079.htm
- http://m.wap.oexnr.cn/jnews/89444.htm
- http://m.wap.oexnr.cn/jnews/8763425.htm
- http://m.wap.oexnr.cn/jnews/39283.htm
- http://m.wap.oexnr.cn/jnews/18541.htm
- http://m.wap.oexnr.cn/jnews/3361.htm
- http://m.wap.oexnr.cn/jnews/018248.htm
- http://m.wap.oexnr.cn/jnews/780207.htm
- http://m.wap.oexnr.cn/jnews/376497.htm
- http://m.wap.oexnr.cn/jnews/44526.htm
- http://m.wap.oexnr.cn/jnews/9356.htm
- http://m.wap.oexnr.cn/jnews/999639.htm
- http://m.wap.oexnr.cn/jnews/510198.htm
- http://m.wap.oexnr.cn/jnews/9772251.htm
- http://m.wap.oexnr.cn/jnews/313528.htm
- http://m.wap.oexnr.cn/jnews/3435.htm
- http://m.wap.oexnr.cn/jnews/939825.htm
- http://m.wap.oexnr.cn/jnews/850985.htm
- http://m.wap.oexnr.cn/jnews/11368.htm
- http://m.wap.oexnr.cn/jnews/926588.htm
- http://m.wap.oexnr.cn/jnews/8930292.htm
- http://m.wap.oexnr.cn/jnews/9566.htm
- http://m.wap.oexnr.cn/jnews/297247.htm
- http://m.wap.oexnr.cn/jnews/33413.htm
- http://m.wap.oexnr.cn/jnews/57836.htm
- http://m.wap.oexnr.cn/jnews/43853.htm
- http://m.wap.oexnr.cn/jnews/7522.htm
- http://m.wap.oexnr.cn/jnews/5591.htm
- http://m.wap.oexnr.cn/jnews/70609.htm
- http://m.wap.oexnr.cn/jnews/8413936.htm
- http://m.wap.oexnr.cn/jnews/5251378.htm
- http://m.wap.oexnr.cn/jnews/5770407.htm
- http://m.wap.oexnr.cn/jnews/078014.htm
- http://m.wap.oexnr.cn/jnews/2644404.htm
- http://m.wap.oexnr.cn/jnews/25590.htm
- http://m.wap.oexnr.cn/jnews/2400.htm
- http://m.wap.oexnr.cn/jnews/20986.htm
- http://m.wap.oexnr.cn/jnews/5759696.htm
- http://m.wap.oexnr.cn/jnews/867267.htm
- http://m.wap.oexnr.cn/jnews/96568.htm
- http://m.wap.oexnr.cn/jnews/8771461.htm
- http://m.wap.oexnr.cn/jnews/18856.htm
- http://m.wap.oexnr.cn/jnews/4918958.htm
- http://m.wap.oexnr.cn/jnews/19854.htm
- http://m.wap.oexnr.cn/jnews/2202.htm
- http://m.wap.oexnr.cn/jnews/5941.htm
- http://m.wap.oexnr.cn/jnews/7469.htm
- http://m.wap.oexnr.cn/jnews/7914358.htm
- http://m.wap.oexnr.cn/jnews/95879.htm
- http://m.wap.oexnr.cn/jnews/1885.htm
- http://m.wap.oexnr.cn/jnews/1404133.htm
- http://m.wap.oexnr.cn/jnews/858595.htm
- http://m.wap.oexnr.cn/jnews/102069.htm
- http://m.wap.oexnr.cn/jnews/598981.htm
- http://m.wap.oexnr.cn/jnews/0277.htm
- http://m.wap.oexnr.cn/jnews/2653766.htm
- http://m.wap.oexnr.cn/jnews/16178.htm
- http://m.wap.oexnr.cn/jnews/293587.htm
- http://m.wap.oexnr.cn/jnews/60777.htm
- http://m.wap.oexnr.cn/jnews/9836.htm
- http://m.wap.oexnr.cn/jnews/50471.htm
- http://m.wap.oexnr.cn/jnews/3914.htm
- http://m.wap.oexnr.cn/jnews/9350828.htm
- http://m.wap.oexnr.cn/jnews/066843.htm
- http://m.wap.oexnr.cn/jnews/656380.htm
- http://m.wap.oexnr.cn/jnews/4364172.htm
- http://m.wap.oexnr.cn/jnews/18548.htm
- http://m.wap.oexnr.cn/jnews/209519.htm
- http://m.wap.oexnr.cn/jnews/2287214.htm
- http://m.wap.oexnr.cn/jnews/56428.htm
- http://m.wap.oexnr.cn/jnews/36732.htm
- http://m.wap.oexnr.cn/jnews/079857.htm
- http://m.wap.oexnr.cn/jnews/7989085.htm
- http://m.wap.oexnr.cn/jnews/452160.htm
- http://m.wap.oexnr.cn/jnews/88077.htm
- http://m.wap.oexnr.cn/jnews/1421351.htm
- http://m.wap.oexnr.cn/jnews/551049.htm
- http://m.wap.oexnr.cn/jnews/868482.htm
- http://m.wap.oexnr.cn/jnews/2901328.htm
- http://m.wap.oexnr.cn/jnews/6233.htm
- http://m.wap.oexnr.cn/jnews/136016.htm
- http://m.wap.oexnr.cn/jnews/0897135.htm
- http://m.wap.oexnr.cn/jnews/186663.htm
- http://m.wap.oexnr.cn/jnews/0904900.htm
- http://m.wap.oexnr.cn/jnews/4102.htm
- http://m.wap.oexnr.cn/jnews/050662.htm
- http://m.wap.oexnr.cn/jnews/689509.htm
- http://m.wap.oexnr.cn/jnews/1751525.htm
- http://m.wap.oexnr.cn/jnews/1981588.htm
- http://m.wap.oexnr.cn/jnews/9455.htm
- http://m.wap.oexnr.cn/jnews/9701311.htm
- http://m.wap.oexnr.cn/jnews/49242.htm
- http://m.wap.oexnr.cn/jnews/7037801.htm
- http://m.wap.oexnr.cn/jnews/583923.htm
- http://m.wap.oexnr.cn/jnews/879977.htm
- http://m.wap.oexnr.cn/jnews/3320.htm
- http://m.wap.oexnr.cn/jnews/04406.htm
- http://m.wap.oexnr.cn/jnews/24692.htm
- http://m.wap.oexnr.cn/jnews/878107.htm
- http://m.wap.oexnr.cn/jnews/9974.htm
- http://m.wap.oexnr.cn/jnews/8960.htm
- http://m.wap.oexnr.cn/jnews/6151.htm
- http://m.wap.oexnr.cn/jnews/60534.htm
- http://m.wap.oexnr.cn/jnews/4856141.htm
- http://m.wap.oexnr.cn/jnews/46543.htm
- http://m.wap.oexnr.cn/jnews/7320.htm
- http://m.wap.oexnr.cn/jnews/3560053.htm
- http://m.wap.oexnr.cn/jnews/607321.htm
- http://m.wap.oexnr.cn/jnews/6775400.htm
- http://m.wap.oexnr.cn/jnews/94685.htm
- http://m.wap.oexnr.cn/jnews/231106.htm
- http://m.wap.oexnr.cn/jnews/33808.htm
- http://m.wap.oexnr.cn/jnews/796575.htm
- http://m.wap.oexnr.cn/jnews/983561.htm
- http://m.wap.oexnr.cn/jnews/638357.htm
- http://m.wap.oexnr.cn/jnews/1549.htm
- http://m.wap.oexnr.cn/jnews/9398073.htm
- http://m.wap.oexnr.cn/jnews/528319.htm
- http://m.wap.oexnr.cn/jnews/53107.htm
- http://m.wap.oexnr.cn/jnews/0327220.htm
- http://m.wap.oexnr.cn/jnews/08754.htm
- http://m.wap.oexnr.cn/jnews/632969.htm
- http://m.wap.oexnr.cn/jnews/1265425.htm
- http://m.wap.oexnr.cn/jnews/669899.htm
- http://m.wap.oexnr.cn/jnews/3956.htm
- http://m.wap.oexnr.cn/jnews/9256597.htm
- http://m.wap.oexnr.cn/jnews/05921.htm
- http://m.wap.oexnr.cn/jnews/58479.htm
- http://m.wap.oexnr.cn/jnews/8363357.htm
- http://m.wap.oexnr.cn/jnews/8978152.htm
- http://m.wap.oexnr.cn/jnews/66594.htm
- http://m.wap.oexnr.cn/jnews/6359.htm
- http://m.wap.oexnr.cn/jnews/1616.htm
- http://m.wap.oexnr.cn/jnews/6125615.htm
- http://m.wap.oexnr.cn/jnews/530777.htm
- http://m.wap.oexnr.cn/jnews/448838.htm
- http://m.wap.oexnr.cn/jnews/403797.htm
- http://m.wap.oexnr.cn/jnews/87425.htm
- http://m.wap.oexnr.cn/jnews/2944.htm
- http://m.wap.oexnr.cn/jnews/723957.htm
- http://m.wap.oexnr.cn/jnews/933300.htm
- http://m.wap.oexnr.cn/jnews/1177352.htm
- http://m.wap.oexnr.cn/jnews/1429758.htm
- http://m.wap.oexnr.cn/jnews/9469941.htm
- http://m.wap.oexnr.cn/jnews/2612727.htm
- http://m.wap.oexnr.cn/jnews/01867.htm
- http://m.wap.oexnr.cn/jnews/14023.htm
- http://m.wap.oexnr.cn/jnews/3329991.htm
- http://m.wap.oexnr.cn/jnews/1561934.htm
- http://m.wap.oexnr.cn/jnews/28334.htm
- http://m.wap.oexnr.cn/jnews/29557.htm
- http://m.wap.oexnr.cn/jnews/18236.htm
- http://m.wap.oexnr.cn/jnews/3347.htm
- http://m.wap.oexnr.cn/jnews/94634.htm
- http://m.wap.oexnr.cn/jnews/70676.htm
- http://m.wap.oexnr.cn/jnews/78801.htm
- http://m.wap.oexnr.cn/jnews/74688.htm
- http://m.wap.oexnr.cn/jnews/36000.htm
- http://m.wap.oexnr.cn/jnews/146812.htm
- http://m.wap.oexnr.cn/jnews/11322.htm
- http://m.wap.oexnr.cn/jnews/9590.htm
- http://m.wap.oexnr.cn/jnews/374460.htm
- http://m.wap.oexnr.cn/jnews/2491.htm
- http://m.wap.oexnr.cn/jnews/2611485.htm
- http://m.wap.oexnr.cn/jnews/85957.htm
- http://m.wap.oexnr.cn/jnews/223565.htm
- http://m.wap.oexnr.cn/jnews/0367782.htm
- http://m.wap.oexnr.cn/jnews/67678.htm
- http://m.wap.oexnr.cn/jnews/3271195.htm
- http://m.wap.oexnr.cn/jnews/0449.htm
- http://m.wap.oexnr.cn/jnews/1789855.htm
- http://m.wap.oexnr.cn/jnews/3686683.htm
- http://m.wap.oexnr.cn/jnews/6109479.htm
- http://m.wap.oexnr.cn/jnews/1116.htm
- http://m.wap.oexnr.cn/jnews/021531.htm
- http://m.wap.oexnr.cn/jnews/5457199.htm
- http://m.wap.oexnr.cn/jnews/127503.htm
- http://m.wap.oexnr.cn/jnews/39377.htm
- http://m.wap.oexnr.cn/jnews/7145.htm
- http://m.wap.oexnr.cn/jnews/421840.htm
- http://m.wap.oexnr.cn/jnews/499765.htm
- http://m.wap.oexnr.cn/jnews/650014.htm
- http://m.wap.oexnr.cn/jnews/1208145.htm
- http://m.wap.oexnr.cn/jnews/5706431.htm
- http://m.wap.oexnr.cn/jnews/5801.htm
- http://m.wap.oexnr.cn/jnews/1040.htm
- http://m.wap.oexnr.cn/jnews/91387.htm
- http://m.wap.oexnr.cn/jnews/927638.htm
- http://m.wap.oexnr.cn/jnews/38361.htm
- http://m.wap.oexnr.cn/jnews/03628.htm
- http://m.wap.oexnr.cn/jnews/0398238.htm
- http://m.wap.oexnr.cn/jnews/84512.htm
- http://m.wap.oexnr.cn/jnews/6569562.htm
- http://m.wap.oexnr.cn/jnews/2965631.htm
- http://m.wap.oexnr.cn/jnews/9696.htm
- http://m.wap.oexnr.cn/jnews/6594.htm
- http://m.wap.oexnr.cn/jnews/1976.htm
- http://m.wap.oexnr.cn/jnews/493569.htm
- http://m.wap.oexnr.cn/jnews/75069.htm
- http://m.wap.oexnr.cn/jnews/47047.htm
- http://m.wap.oexnr.cn/jnews/11127.htm
- http://m.wap.oexnr.cn/jnews/23034.htm
- http://m.wap.oexnr.cn/jnews/349346.htm
- http://m.wap.oexnr.cn/jnews/542096.htm
- http://m.wap.oexnr.cn/jnews/149155.htm
- http://m.wap.oexnr.cn/jnews/9782240.htm
- http://m.wap.oexnr.cn/jnews/34335.htm
- http://m.wap.oexnr.cn/jnews/410803.htm
- http://m.wap.oexnr.cn/jnews/8517685.htm
- http://m.wap.oexnr.cn/jnews/28062.htm
- http://m.wap.oexnr.cn/jnews/75728.htm
- http://m.wap.oexnr.cn/jnews/932178.htm
- http://m.wap.oexnr.cn/jnews/4100.htm
- http://m.wap.oexnr.cn/jnews/3112.htm
- http://m.wap.oexnr.cn/jnews/4961841.htm
- http://m.wap.oexnr.cn/jnews/3835.htm
- http://m.wap.oexnr.cn/jnews/0150673.htm

## 项目结构

```
weblink-harvest/
├── src/
│   ├── core/                           # 核心业务逻辑模块
│   │   ├── linkProcessor.js            # 链接解析、标准化与去重引擎
│   │   ├── tagManager.js               # 标签树管理与层级维护
│   │   └── batchController.js          # 批次导入、导出与状态控制
│   ├── api/                            # RESTful API 路由层
│   │   ├── v1/
│   │   │   ├── links.js                # 链接增删改查接口
│   │   │   ├── batches.js              # 批次管理接口
│   │   │   └── stats.js                # 聚合统计接口
│   ├── db/                             # 数据库适配层
│   │   ├── sqliteAdapter.js            # SQLite3 连接池与查询构造器
│   │   ├── redisClient.js              # Redis 缓存与队列客户端
│   │   └── migrations/                 # 数据库版本迁移脚本
│   ├── scheduler/                      # 定时任务调度模块
│   │   ├── healthCheck.js              # 链接可用性定时检测任务
│   │   └── reportGenerator.js          # 每日/每周统计报告生成
│   ├── frontend/                       # Web 管理界面静态资源
│   │   ├── pages/                      # 页面组件（导入、检索、统计）
│   │   ├── components/                 # 可复用 UI 组件（表格、筛选器）
│   │   └── assets/                     # CSS 样式与前端静态资源
│   └── utils/                          # 通用工具函数
│       ├── urlNormalizer.js            # URL 标准化与格式校验
│       ├── logger.js                   # 日志记录与分级输出
│       └── configLoader.js             # 环境配置加载与验证
├── tests/                              # 单元测试与集成测试用例
│   ├── unit/                           # 核心模块单元测试
│   └── integration/                    # API 与数据库集成测试
├── docs/                               # 项目文档（入门指南、API 参考等）
├── scripts/                            # 运维辅助脚本（数据迁移、备份）
├── docker-compose.yml                  # Docker Compose 编排文件
├── Dockerfile                          # 容器构建定义
├── package.json                        # npm 依赖清单与脚本命令
├── .env.example                        # 环境变量配置模板
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻项目仓库至个人账户，在本地创建功能分支（如 feature/batch-import-optimization），所有开发工作在该分支上进行。

2. 遵循项目代码风格规范，JavaScript 文件使用 ESLint 配置（基于 Airbnb 风格指南），提交前执行 npm run lint 确保无风格错误。

3. 编写新功能或修复缺陷时，需同步补充对应的单元测试用例，保证测试覆盖率不低于 80%。测试文件存放于 tests/ 目录下，命名规则为 模块名.test.js。

4. 提交 Pull Request 前，请确保所有现有测试用例通过（npm run test），并更新 docs/ 目录下相关文档以反映代码变更。PR 描述中需明确说明变更目的、影响范围及测试验证情况。

5. 项目维护者将在收到 PR 后的 5 个工作日内进行 Code Review，可能会要求补充测试或调整实现方案。合并后您的贡献将被列入贡献者名单。

## 常见问题

问：导入大量链接时系统响应变慢，如何优化？

答：当单批次导入链接数量超过 5000 条时，建议启用批量写入模式。在 .env 文件中设置 BATCH_WRITE_SIZE=1000 和 USE_TRANSACTION=true，系统将使用事务包裹批量插入操作，显著降低磁盘 I/O 次数。同时可开启 Redis 缓存（需安装 Redis 并配置 REDIS_URL）以分担数据库查询压力。

问：系统检测到部分链接显示为失效，但手动访问浏览器可以打开，是什么原因？

答：可用性检测模块默认使用 HEAD 请求方法并设置 5 秒超时，某些服务器可能不支持 HEAD 方法或响应较慢。您可在配置文件中将检测方法改为 GET，并适当调整超时阈值。此外，部分站点可能对非浏览器 User-Agent 进行拦截，请将检测请求的 User-Agent 更新为常见浏览器标识。

问：如何将本系统与其他笔记软件（如 Obsidian）进行数据同步？

答：系统支持 CSV 和 Markdown 列表两种导出格式。在 Obsidian 中，您可以使用 Templater 插件读取导出的 CSV 文件并生成带有链接的笔记页面。对于 Markdown 列表格式，可直接将导出的内容复制到 Obsidian 笔记中，系统导出的每条链接均包含标签信息和导入时间，便于在 Obsidian 中通过 Dataview 插件进行二次筛选和统计。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
