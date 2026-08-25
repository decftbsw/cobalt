# NewsLink Aggregator

NewsLink Aggregator 是一个面向移动端新闻资讯的轻量级外链聚合与导航系统。项目定位于为开发者和资讯运营人员提供一套标准化的新闻外链采集、分类与分发框架，能够将零散的 .htm 新闻链接转化为可维护、可扩展的链接资源池。目标用户包括个人站长、新闻聚合应用开发者、数据爬虫工程师以及内容运营团队。项目核心解决以下问题：新闻外链散落于不同路径导致管理混乱、链接失效无法及时检测、采集规则难以复用、以及缺乏统一的链接展示与跳转中间层。通过本项目的约定式目录结构和自动化校验脚本，用户可以快速构建一个稳定、可监控的新闻链接导航站。

## 功能概览

自动化链接采集 提供基于正则表达式与 XPath 的混合采集模板，支持从目标页面批量提取新闻链接并规范化输出。

链接健康度巡检 内置定时任务与报告生成器，可对已收录的 .htm 链接进行状态码检测，自动标记 404、500 及重定向链接。

多级分类标签 支持为每条链接附加主题分类、来源站点、发布时间等元数据标签，便于后续按维度筛选与排序。

移动端自适应渲染 提供响应式列表视图与卡片视图，针对手机屏幕优化排版，确保在 320px 至 768px 宽度下均有良好可读性。

外链跳转中间页 在用户点击新闻链接时先经过本地跳转页，记录点击日志并携带来源 referrer，同时规避部分平台的外链屏蔽策略。

数据导入导出 支持 JSON、CSV、Markdown 表格三种格式的链接批量导入与导出，方便与其他系统（如 CMS、爬虫管理平台）对接。

链接去重与合并 基于 URL 路径中的数字 ID 进行去重，并支持手动合并重复链接的点击统计与标签信息。

## 应用场景

个人新闻导航站搭建 个人开发者可使用本项目快速生成一个每日更新的新闻外链导航页面，将分散在多个站点中的行业动态链接集中展示，方便日常查阅。

爬虫数据持久化存储 数据采集工程师可将爬取到的新闻 .htm 链接直接导入 NewsLink Aggregator，借助内置的分类与健康巡检功能，持续监控采集源的有效性。

企业内部资讯看板 企业运营团队可在内网部署本系统，将各部门关注的行业资讯、竞品动态、政策公告等链接统一收录，并生成每周链接报告供管理层审阅。

开源文档资源聚合 技术社区维护者可使用本项目整理与项目相关的教程、公告、版本发布等外部链接，作为文档站点的补充资源模块，降低文档维护成本。

## 快速开始

以下命令演示了从 GitHub 克隆项目、安装依赖并启动开发服务的完整流程。

```bash
git clone https://github.com/yourorg/newslink-aggregator.git
cd newslink-aggregator
npm install
cp .env.example .env
npm run dev
```

执行完毕后，访问 http://localhost:3000 即可查看链接聚合首页。如需构建生产环境静态文件，请执行 `npm run build`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.20.0 或更高 | 运行时环境，推荐使用 LTS 版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装依赖与执行脚本 |
| SQLite3 | 系统级依赖 | 内置数据库引擎，用于存储链接元数据与状态 |
| 操作系统 | Linux / macOS / Windows | 跨平台支持，生产环境推荐 Linux |
| 网络环境 | 可访问公网 | 用于链接健康巡检及采集任务 |
| 浏览器 | 现代浏览器（Chrome 90+ / Firefox 88+） | 用于前台渲染与调试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | /docs/quick-start.md | 如何用 10 分钟完成项目部署并看到第一条链接？ |
| 采集配置 | /docs/collection.md | 如何编写采集规则以适配不同的新闻源站点？ |
| 运维手册 | /docs/operations.md | 如何配置定时巡检、处理链接失效告警？ |
| 二次开发 | /docs/development.md | 如何扩展自定义分类器或增加新的导入导出格式？ |

## 资源列表

- http://m.3g.oexnr.cn/nnews/3659649.htm
- http://m.3g.oexnr.cn/nnews/8288.htm
- http://m.3g.oexnr.cn/nnews/99129.htm
- http://m.3g.oexnr.cn/nnews/0513095.htm
- http://m.3g.oexnr.cn/nnews/2110.htm
- http://m.3g.oexnr.cn/nnews/4227.htm
- http://m.3g.oexnr.cn/nnews/9658.htm
- http://m.3g.oexnr.cn/nnews/41385.htm
- http://m.3g.oexnr.cn/nnews/4468891.htm
- http://m.3g.oexnr.cn/nnews/10309.htm
- http://m.3g.oexnr.cn/nnews/42421.htm
- http://m.3g.oexnr.cn/nnews/632492.htm
- http://m.3g.oexnr.cn/nnews/75237.htm
- http://m.3g.oexnr.cn/nnews/1195089.htm
- http://m.3g.oexnr.cn/nnews/787304.htm
- http://m.3g.oexnr.cn/nnews/4192821.htm
- http://m.3g.oexnr.cn/nnews/86692.htm
- http://m.3g.oexnr.cn/nnews/294661.htm
- http://m.3g.oexnr.cn/nnews/6051746.htm
- http://m.3g.oexnr.cn/nnews/5741224.htm
- http://m.3g.oexnr.cn/nnews/186077.htm
- http://m.3g.oexnr.cn/nnews/12780.htm
- http://m.3g.oexnr.cn/nnews/967730.htm
- http://m.3g.oexnr.cn/nnews/0064.htm
- http://m.3g.oexnr.cn/nnews/17439.htm
- http://m.3g.oexnr.cn/nnews/7471721.htm
- http://m.3g.oexnr.cn/nnews/6970.htm
- http://m.3g.oexnr.cn/nnews/1542176.htm
- http://m.3g.oexnr.cn/nnews/9767.htm
- http://m.3g.oexnr.cn/nnews/2543.htm
- http://m.3g.oexnr.cn/nnews/416406.htm
- http://m.3g.oexnr.cn/nnews/4391.htm
- http://m.3g.oexnr.cn/nnews/6666541.htm
- http://m.3g.oexnr.cn/nnews/9120883.htm
- http://m.3g.oexnr.cn/nnews/26147.htm
- http://m.3g.oexnr.cn/nnews/40580.htm
- http://m.3g.oexnr.cn/nnews/344513.htm
- http://m.3g.oexnr.cn/nnews/824385.htm
- http://m.3g.oexnr.cn/nnews/681448.htm
- http://m.3g.oexnr.cn/nnews/4913766.htm
- http://m.3g.oexnr.cn/nnews/496543.htm
- http://m.3g.oexnr.cn/nnews/6223380.htm
- http://m.3g.oexnr.cn/nnews/6520.htm
- http://m.3g.oexnr.cn/nnews/5917534.htm
- http://m.3g.oexnr.cn/nnews/7275425.htm
- http://m.3g.oexnr.cn/nnews/0051.htm
- http://m.3g.oexnr.cn/nnews/7924.htm
- http://m.3g.oexnr.cn/nnews/284787.htm
- http://m.3g.oexnr.cn/nnews/419610.htm
- http://m.3g.oexnr.cn/nnews/1023.htm
- http://m.3g.oexnr.cn/nnews/3277680.htm
- http://m.3g.oexnr.cn/nnews/9414932.htm
- http://m.3g.oexnr.cn/nnews/67813.htm
- http://m.3g.oexnr.cn/nnews/809754.htm
- http://m.3g.oexnr.cn/nnews/4166625.htm
- http://m.3g.oexnr.cn/nnews/524549.htm
- http://m.3g.oexnr.cn/nnews/454739.htm
- http://m.3g.oexnr.cn/nnews/5786738.htm
- http://m.3g.oexnr.cn/nnews/3503.htm
- http://m.3g.oexnr.cn/nnews/40421.htm
- http://m.3g.oexnr.cn/nnews/46598.htm
- http://m.3g.oexnr.cn/nnews/14728.htm
- http://m.3g.oexnr.cn/nnews/6822.htm
- http://m.3g.oexnr.cn/nnews/0917.htm
- http://m.3g.oexnr.cn/nnews/6421.htm
- http://m.3g.oexnr.cn/nnews/853740.htm
- http://m.3g.oexnr.cn/nnews/953224.htm
- http://m.3g.oexnr.cn/nnews/9736.htm
- http://m.3g.oexnr.cn/nnews/859288.htm
- http://m.3g.oexnr.cn/nnews/1276.htm
- http://m.3g.oexnr.cn/nnews/4774037.htm
- http://m.3g.oexnr.cn/nnews/5338.htm
- http://m.3g.oexnr.cn/nnews/2214317.htm
- http://m.3g.oexnr.cn/nnews/761241.htm
- http://m.3g.oexnr.cn/nnews/3574.htm
- http://m.3g.oexnr.cn/nnews/1140537.htm
- http://m.3g.oexnr.cn/nnews/57293.htm
- http://m.3g.oexnr.cn/nnews/9382.htm
- http://m.3g.oexnr.cn/nnews/4228067.htm
- http://m.3g.oexnr.cn/nnews/8702166.htm
- http://m.3g.oexnr.cn/nnews/74343.htm
- http://m.3g.oexnr.cn/nnews/617999.htm
- http://m.3g.oexnr.cn/nnews/87410.htm
- http://m.3g.oexnr.cn/nnews/92793.htm
- http://m.3g.oexnr.cn/nnews/2972179.htm
- http://m.3g.oexnr.cn/nnews/2166.htm
- http://m.3g.oexnr.cn/nnews/68521.htm
- http://m.3g.oexnr.cn/nnews/9611.htm
- http://m.3g.oexnr.cn/nnews/007452.htm
- http://m.3g.oexnr.cn/nnews/5860.htm
- http://m.3g.oexnr.cn/nnews/84610.htm
- http://m.3g.oexnr.cn/nnews/0530337.htm
- http://m.3g.oexnr.cn/nnews/5728835.htm
- http://m.3g.oexnr.cn/nnews/6365.htm
- http://m.3g.oexnr.cn/nnews/26787.htm
- http://m.3g.oexnr.cn/nnews/2148.htm
- http://m.3g.oexnr.cn/nnews/375837.htm
- http://m.3g.oexnr.cn/nnews/72230.htm
- http://m.3g.oexnr.cn/nnews/547911.htm
- http://m.3g.oexnr.cn/nnews/002343.htm
- http://m.3g.oexnr.cn/nnews/0149.htm
- http://m.3g.oexnr.cn/nnews/13175.htm
- http://m.3g.oexnr.cn/nnews/9291166.htm
- http://m.3g.oexnr.cn/nnews/068305.htm
- http://m.3g.oexnr.cn/nnews/35160.htm
- http://m.3g.oexnr.cn/nnews/476492.htm
- http://m.3g.oexnr.cn/nnews/030474.htm
- http://m.3g.oexnr.cn/nnews/4534.htm
- http://m.3g.oexnr.cn/nnews/3485074.htm
- http://m.3g.oexnr.cn/nnews/0023.htm
- http://m.3g.oexnr.cn/nnews/66455.htm
- http://m.3g.oexnr.cn/nnews/6381787.htm
- http://m.3g.oexnr.cn/nnews/29832.htm
- http://m.3g.oexnr.cn/nnews/711400.htm
- http://m.3g.oexnr.cn/nnews/831477.htm
- http://m.3g.oexnr.cn/nnews/6803.htm
- http://m.3g.oexnr.cn/nnews/9041334.htm
- http://m.3g.oexnr.cn/nnews/31069.htm
- http://m.3g.oexnr.cn/nnews/5357.htm
- http://m.3g.oexnr.cn/nnews/4891888.htm
- http://m.3g.oexnr.cn/nnews/2062.htm
- http://m.3g.oexnr.cn/nnews/245750.htm
- http://m.3g.oexnr.cn/nnews/139435.htm
- http://m.3g.oexnr.cn/nnews/230311.htm
- http://m.3g.oexnr.cn/nnews/27177.htm
- http://m.3g.oexnr.cn/nnews/779305.htm
- http://m.3g.oexnr.cn/nnews/587569.htm
- http://m.3g.oexnr.cn/nnews/03848.htm
- http://m.3g.oexnr.cn/nnews/5489928.htm
- http://m.3g.oexnr.cn/nnews/08362.htm
- http://m.3g.oexnr.cn/nnews/0980.htm
- http://m.3g.oexnr.cn/nnews/28726.htm
- http://m.3g.oexnr.cn/nnews/2267867.htm
- http://m.3g.oexnr.cn/nnews/8871.htm
- http://m.3g.oexnr.cn/nnews/260215.htm
- http://m.3g.oexnr.cn/nnews/57830.htm
- http://m.3g.oexnr.cn/nnews/03087.htm
- http://m.3g.oexnr.cn/nnews/0594836.htm
- http://m.3g.oexnr.cn/nnews/377827.htm
- http://m.3g.oexnr.cn/nnews/8668.htm
- http://m.3g.oexnr.cn/nnews/665687.htm
- http://m.3g.oexnr.cn/nnews/9343874.htm
- http://m.3g.oexnr.cn/nnews/0412.htm
- http://m.3g.oexnr.cn/nnews/5524508.htm
- http://m.3g.oexnr.cn/nnews/02049.htm
- http://m.3g.oexnr.cn/nnews/840641.htm
- http://m.3g.oexnr.cn/nnews/536378.htm
- http://m.3g.oexnr.cn/nnews/1447.htm
- http://m.3g.oexnr.cn/nnews/4095.htm
- http://m.3g.oexnr.cn/nnews/0505828.htm
- http://m.3g.oexnr.cn/nnews/586594.htm
- http://m.3g.oexnr.cn/nnews/9743.htm
- http://m.3g.oexnr.cn/nnews/51266.htm
- http://m.3g.oexnr.cn/nnews/1729.htm
- http://m.3g.oexnr.cn/nnews/835289.htm
- http://m.3g.oexnr.cn/nnews/336944.htm
- http://m.3g.oexnr.cn/nnews/31585.htm
- http://m.3g.oexnr.cn/nnews/7302852.htm
- http://m.3g.oexnr.cn/nnews/6194385.htm
- http://m.3g.oexnr.cn/nnews/82017.htm
- http://m.3g.oexnr.cn/nnews/861400.htm
- http://m.3g.oexnr.cn/nnews/2361.htm
- http://m.3g.oexnr.cn/nnews/1401991.htm
- http://m.3g.oexnr.cn/nnews/60530.htm
- http://m.3g.oexnr.cn/nnews/950020.htm
- http://m.3g.oexnr.cn/nnews/7226935.htm
- http://m.3g.oexnr.cn/nnews/4282.htm
- http://m.3g.oexnr.cn/nnews/3721246.htm
- http://m.3g.oexnr.cn/nnews/50747.htm
- http://m.3g.oexnr.cn/nnews/88900.htm
- http://m.3g.oexnr.cn/nnews/440852.htm
- http://m.3g.oexnr.cn/nnews/29478.htm
- http://m.3g.oexnr.cn/nnews/45788.htm
- http://m.3g.oexnr.cn/nnews/027640.htm
- http://m.3g.oexnr.cn/nnews/476963.htm
- http://m.3g.oexnr.cn/nnews/2026.htm
- http://m.3g.oexnr.cn/nnews/6195.htm
- http://m.3g.oexnr.cn/nnews/01962.htm
- http://m.3g.oexnr.cn/nnews/28509.htm
- http://m.3g.oexnr.cn/nnews/2701680.htm
- http://m.3g.oexnr.cn/nnews/4509.htm
- http://m.3g.oexnr.cn/nnews/216704.htm
- http://m.3g.oexnr.cn/nnews/99370.htm
- http://m.3g.oexnr.cn/nnews/57754.htm
- http://m.3g.oexnr.cn/nnews/8076.htm
- http://m.3g.oexnr.cn/nnews/8599017.htm
- http://m.3g.oexnr.cn/nnews/9654004.htm
- http://m.3g.oexnr.cn/nnews/67333.htm
- http://m.3g.oexnr.cn/nnews/87857.htm
- http://m.3g.oexnr.cn/nnews/6697800.htm
- http://m.3g.oexnr.cn/nnews/0799390.htm
- http://m.3g.oexnr.cn/nnews/0087.htm
- http://m.3g.oexnr.cn/nnews/507211.htm
- http://m.3g.oexnr.cn/nnews/590863.htm
- http://m.3g.oexnr.cn/nnews/2240.htm
- http://m.3g.oexnr.cn/nnews/7887115.htm
- http://m.3g.oexnr.cn/nnews/584684.htm
- http://m.3g.oexnr.cn/nnews/876198.htm
- http://m.3g.oexnr.cn/nnews/04237.htm
- http://m.3g.oexnr.cn/nnews/0403267.htm
- http://m.3g.oexnr.cn/nnews/3337.htm
- http://m.3g.oexnr.cn/nnews/966884.htm
- http://m.3g.oexnr.cn/nnews/8028101.htm
- http://m.3g.oexnr.cn/nnews/2812745.htm
- http://m.3g.oexnr.cn/nnews/8558.htm
- http://m.3g.oexnr.cn/nnews/6516783.htm
- http://m.3g.oexnr.cn/nnews/2775.htm
- http://m.3g.oexnr.cn/nnews/3658277.htm
- http://m.3g.oexnr.cn/nnews/7945.htm
- http://m.3g.oexnr.cn/nnews/309103.htm
- http://m.3g.oexnr.cn/nnews/3437758.htm
- http://m.3g.oexnr.cn/nnews/355237.htm
- http://m.3g.oexnr.cn/nnews/883625.htm
- http://m.3g.oexnr.cn/nnews/48564.htm
- http://m.3g.oexnr.cn/nnews/8755328.htm
- http://m.3g.oexnr.cn/nnews/40310.htm
- http://m.3g.oexnr.cn/nnews/615481.htm
- http://m.3g.oexnr.cn/nnews/3970415.htm
- http://m.3g.oexnr.cn/nnews/8551168.htm
- http://m.3g.oexnr.cn/nnews/1538517.htm
- http://m.3g.oexnr.cn/nnews/209253.htm
- http://m.3g.oexnr.cn/nnews/9230.htm
- http://m.3g.oexnr.cn/nnews/3850.htm
- http://m.3g.oexnr.cn/nnews/347186.htm
- http://m.3g.oexnr.cn/nnews/3279812.htm
- http://m.3g.oexnr.cn/nnews/95163.htm
- http://m.3g.oexnr.cn/nnews/6381.htm
- http://m.3g.oexnr.cn/nnews/5500.htm
- http://m.3g.oexnr.cn/nnews/85565.htm
- http://m.3g.oexnr.cn/nnews/0257451.htm
- http://m.3g.oexnr.cn/nnews/0680.htm
- http://m.3g.oexnr.cn/nnews/07971.htm
- http://m.3g.oexnr.cn/nnews/775665.htm
- http://m.3g.oexnr.cn/nnews/5364.htm
- http://m.3g.oexnr.cn/nnews/8379233.htm
- http://m.3g.oexnr.cn/nnews/2984.htm
- http://m.3g.oexnr.cn/nnews/24166.htm
- http://m.3g.oexnr.cn/nnews/772820.htm
- http://m.3g.oexnr.cn/nnews/2119.htm
- http://m.3g.oexnr.cn/nnews/0577.htm
- http://m.3g.oexnr.cn/nnews/5982.htm
- http://m.3g.oexnr.cn/nnews/5698048.htm
- http://m.3g.oexnr.cn/nnews/3615.htm
- http://m.3g.oexnr.cn/nnews/9321965.htm
- http://m.3g.oexnr.cn/nnews/2960.htm
- http://m.3g.oexnr.cn/nnews/9075237.htm
- http://m.3g.oexnr.cn/nnews/4712516.htm
- http://m.3g.oexnr.cn/nnews/8693384.htm
- http://m.3g.oexnr.cn/nnews/0252.htm
- http://m.3g.oexnr.cn/nnews/26596.htm
- http://m.3g.oexnr.cn/nnews/003800.htm
- http://m.3g.oexnr.cn/nnews/2548630.htm
- http://m.3g.oexnr.cn/nnews/1876061.htm
- http://m.3g.oexnr.cn/nnews/5726423.htm
- http://m.3g.oexnr.cn/nnews/53136.htm
- http://m.3g.oexnr.cn/nnews/74649.htm
- http://m.3g.oexnr.cn/nnews/5866946.htm
- http://m.3g.oexnr.cn/nnews/62410.htm
- http://m.3g.oexnr.cn/nnews/3360045.htm
- http://m.3g.oexnr.cn/nnews/02314.htm
- http://m.3g.oexnr.cn/nnews/6255820.htm
- http://m.3g.oexnr.cn/nnews/8777.htm
- http://m.3g.oexnr.cn/nnews/5402124.htm
- http://m.3g.oexnr.cn/nnews/582519.htm
- http://m.3g.oexnr.cn/nnews/25365.htm
- http://m.3g.oexnr.cn/nnews/90878.htm
- http://m.3g.oexnr.cn/nnews/6242.htm
- http://m.3g.oexnr.cn/nnews/56062.htm
- http://m.3g.oexnr.cn/nnews/8579.htm
- http://m.3g.oexnr.cn/nnews/8160357.htm
- http://m.3g.oexnr.cn/nnews/8217892.htm
- http://m.3g.oexnr.cn/nnews/0116408.htm
- http://m.3g.oexnr.cn/nnews/3507893.htm
- http://m.3g.oexnr.cn/nnews/814712.htm
- http://m.3g.oexnr.cn/nnews/781247.htm
- http://m.3g.oexnr.cn/nnews/567318.htm
- http://m.3g.oexnr.cn/nnews/0891.htm
- http://m.3g.oexnr.cn/nnews/9965019.htm
- http://m.3g.oexnr.cn/nnews/26739.htm
- http://m.3g.oexnr.cn/nnews/3747140.htm
- http://m.3g.oexnr.cn/nnews/8168.htm
- http://m.3g.oexnr.cn/nnews/682166.htm
- http://m.3g.oexnr.cn/nnews/400740.htm
- http://m.3g.oexnr.cn/nnews/7305755.htm
- http://m.3g.oexnr.cn/nnews/22888.htm
- http://m.3g.oexnr.cn/nnews/0536.htm
- http://m.3g.oexnr.cn/nnews/3135945.htm
- http://m.3g.oexnr.cn/nnews/465379.htm
- http://m.3g.oexnr.cn/nnews/0702.htm
- http://m.3g.oexnr.cn/nnews/9690.htm
- http://m.3g.oexnr.cn/nnews/7143326.htm
- http://m.3g.oexnr.cn/nnews/646969.htm
- http://m.3g.oexnr.cn/nnews/353585.htm
- http://m.3g.oexnr.cn/nnews/2127.htm
- http://m.3g.oexnr.cn/nnews/9571.htm
- http://m.3g.oexnr.cn/nnews/0754.htm
- http://m.3g.oexnr.cn/nnews/92157.htm
- http://m.3g.oexnr.cn/nnews/8410740.htm
- http://m.3g.oexnr.cn/nnews/624330.htm
- http://m.3g.oexnr.cn/nnews/2886.htm

## 项目结构

```
newslink-aggregator/
├── src/
│   ├── collectors/               # 采集器模块，定义各新闻源的抓取规则
│   │   ├── base.js               # 采集基类，封装请求与重试逻辑
│   │   ├── oexnr.js              # oexnr 源专用解析器
│   │   └── registry.js           # 采集器注册中心
│   ├── models/                   # 数据模型层
│   │   ├── link.js               # 链接实体模型（含状态、标签、时间戳）
│   │   ├── check.js              # 健康检查记录模型
│   │   └── category.js           # 分类标签模型
│   ├── services/                 # 业务服务层
│   │   ├── health-check.js       # 链接状态巡检服务
│   │   ├── dedupe.js             # 去重与合并服务
│   │   └── export.js             # 数据导出服务（JSON/CSV/Markdown）
│   ├── routes/                   # API 路由层
│   │   ├── api.js                # RESTful API 聚合
│   │   └── web.js                # 前台页面路由
│   ├── views/                    # 前台渲染模板
│   │   ├── list.ejs              # 链接列表页模板
│   │   ├── detail.ejs            # 链接详情与跳转页
│   │   └── report.ejs            # 健康报告页
│   └── utils/                    # 通用工具函数
│       ├── fetcher.js            # HTTP 请求封装
│       ├── logger.js             # 日志工具（按天滚动）
│       └── validator.js          # URL 校验与规范化
├── config/                       # 配置文件目录
│   ├── default.json              # 默认配置（端口、超时、分页大小）
│   ├── production.json           # 生产环境覆盖配置
│   └── sources.json              # 新闻源采集规则配置
├── data/                         # 本地数据存储目录（SQLite 数据库文件存放于此）
│   └── newslink.db               # 主数据库文件（自动生成）
├── docs/                         # 项目文档
│   ├── quick-start.md
│   ├── collection.md
│   ├── operations.md
│   └── development.md
├── scripts/                      # 运维与辅助脚本
│   ├── init-db.js                # 数据库初始化脚本
│   ├── seed.js                   # 种子数据填充脚本
│   └── health-report.js          # 手动触发生成健康报告
├── tests/                        # 单元测试与集成测试
│   ├── collectors.test.js
│   ├── models.test.js
│   └── services.test.js
├── .env.example                  # 环境变量模板
├── .gitignore
├── package.json
├── README.md
└── LICENSE
```

## 贡献指南

1. 阅读项目文档中的开发指引（/docs/development.md）了解代码规范与架构设计，然后从 GitHub 复刻项目仓库到个人账号下，并克隆到本地开发环境。

2. 创建一个新的功能分支，分支命名遵循 feat/功能描述 或 fix/问题描述 的格式，例如 feat/add-weibo-collector，在该分支上进行代码修改。

3. 针对新增功能或修复编写对应的单元测试用例，确保测试覆盖率达到 80% 以上，并执行 npm run test 验证所有现有测试均通过。

4. 提交代码前执行 npm run lint 进行代码风格检查，并按照约定式提交规范（Conventional Commits）编写提交信息，例如 feat(collector): add new source parser for oexnr。

5. 将分支推送至复刻仓库，然后向主仓库的 develop 分支发起合并请求（Pull Request），在请求描述中清楚说明改动内容、测试结果以及相关的 Issue 编号。

## 常见问题

问：启动项目后页面显示「无链接数据」，如何导入初始链接？
答：项目默认不包含预置数据。您可以通过以下方式导入链接：1）使用采集器运行 npm run collect 从配置的新闻源抓取；2）通过后台管理界面手动添加单条链接；3）使用导入命令 npm run import -- --file=links.json 批量导入 JSON 或 CSV 格式的数据文件。示例数据文件可在 /docs/examples 目录下找到。

问：链接健康巡检显示大量超时或 404，如何调整检测策略？
答：健康巡检的并发数、超时阈值和重试次数可在 config/default.json 中的 healthCheck 字段进行调整。对于特定域名，您可以在 sources.json 中为该域名配置独立的超时参数。此外，巡检任务支持白名单与黑名单过滤，可通过环境变量 HEALTH_FILTER_DOMAINS 指定仅检测特定来源的链接。

问：如何在生产环境中部署本项目并保证稳定性？
答：生产环境建议使用 PM2 或 systemd 管理进程，并配合 Nginx 反向代理处理静态资源与负载均衡。数据库方面，SQLite 适用于中小规模数据（链接数低于 10 万条），数据量更大时建议切换至 PostgreSQL（需修改 models 中的数据库适配层）。项目提供了 docker-compose.prod.yml 示例文件，可通过 docker compose -f docker-compose.prod.yml up -d 一键启动生产容器。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
