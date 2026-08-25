# NewsLink Catalog

NewsLink Catalog 是一个面向技术信息聚合与外部资源导航的开源工具，定位于帮助开发者、技术研究员及内容运营人员高效收集、分类、检索和展示来自各类来源的新闻条目与动态链接。该项目不依赖复杂后端，采用静态站点生成逻辑与轻量级前端交互，可用于构建小规模技术新闻聚合站、内部知识库的外链索引系统或特定领域事件追踪面板。

目标用户包括个人站长、开源社区文档维护者、技术资讯编辑以及需要快速搭建外链汇总层的开发团队。NewsLink Catalog 处理的核心问题在于：大量零散外部链接难以结构化管理和快速呈现，而现有通用书签工具或笔记系统缺乏针对链接集合的分类导航、状态标记和批量导入导出能力。本项目通过对链接条目进行规范化处理、按元数据分组、生成可筛选视图，为用户提供一套可直接运行、易于扩展的链接目录生成方案。

## 功能概览

**链接条目结构化解析** 自动提取 URL 中的路径与参数特征，归类至预设新闻分类标签，支持手动覆盖分类。

**批量导入与去重校验** 支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动检测重复条目并生成报告。

**分类导航与多维度筛选** 按来源域名、发布时间段、内容类型（如公告、技术文档、事件记录）三层筛选，生成动态导航菜单。

**静态页面渲染引擎** 基于模板系统生成可供浏览器直接访问的 HTML 目录页，支持响应式布局与暗色模式。

**链接存活状态检测** 提供可选的周期性 HEAD 请求检测，标记失效链接并输出异常日志，便于定期清理。

**元数据扩展字段** 每条链接可附加备注标签、重要等级、归档日期和自定义键值对，满足个性化管理需求。

**导出与嵌入支持** 将目录导出为 JSON、Markdown 表格或 HTML 片段，便于嵌入现有文档平台或博客侧栏。

## 应用场景

技术团队内部周报汇总 每周团队会产出多篇外部参考链接（技术提案、故障复盘、行业动态），使用 NewsLink Catalog 可将这些链接按周次和主题归类，生成可公开或内部共享的周报导航页，减少在聊天记录中翻找链接的时间。

开源项目外部依赖追踪 开源项目维护者需要关注上游依赖的发布公告、安全更新及兼容性说明。通过定期导入相关项目发布页链接，利用分类标签和存活检测功能，可快速识别变更并更新项目文档中的依赖表。

技术活动与会议信息归档 参与或组织线下技术 meetup 时，会积累大量报名页、议程链接、讲稿资源地址。使用本工具按活动日期和议题分类，生成带时间线的链接目录，方便参与者和后续组织者查阅历史资料。

个人技术阅读清单管理 开发者日常阅读技术博客、论文预印本、在线教程时，可将值得回看的链接录入系统，按领域（前端、后端、ML、运维等）标记，并定期导出为个人知识库的引用索引。

## 快速开始

以下命令演示从仓库克隆、安装依赖到启动开发服务的完整流程。

```bash
git clone https://github.com/your-org/newslink-catalog.git
cd newslink-catalog
npm install
npm run build
npm start
```

若使用 Yarn 作为包管理器，可将 `npm install` 替换为 `yarn install`，`npm start` 替换为 `yarn start`。构建产物默认输出至 `dist/` 目录，可将其部署至任意静态托管服务。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 16.20.0 或更高 | 运行时与包管理基础环境，推荐使用 LTS 版本 |
| npm | 8.0.0 或更高 | 随 Node.js 一同安装，用于依赖安装与脚本执行 |
| Git | 2.25.0 或更高 | 用于克隆仓库及版本控制操作 |
| 操作系统 | Linux/macOS/Windows (WSL2 推荐) | 跨平台支持，Windows 下建议使用 PowerShell 7+ |
| 浏览器 | 基于 Chromium 或 Firefox 的现代版本 | 仅开发预览时需使用，生产环境无浏览器要求 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速配置第一个链接目录并生成预览页面 |
| 配置参考 | docs/configuration.md | 所有可用的配置文件字段、默认值及自定义模板选项 |
| 导入与导出 | docs/import-export.md | 支持哪些导入格式、导出模板如何编写、批量操作注意事项 |
| 部署指南 | docs/deployment.md | 如何将生成的静态站点部署至 Vercel、Netlify 或自建 Nginx 服务器 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/3508038.htm
- http://m.3g.ghtkgg.cn/nnews/5064.htm
- http://m.3g.ghtkgg.cn/nnews/2566106.htm
- http://m.3g.ghtkgg.cn/nnews/11706.htm
- http://m.3g.ghtkgg.cn/nnews/0418.htm
- http://m.3g.ghtkgg.cn/nnews/1386.htm
- http://m.3g.ghtkgg.cn/nnews/6616.htm
- http://m.3g.ghtkgg.cn/nnews/975337.htm
- http://m.3g.ghtkgg.cn/nnews/3556242.htm
- http://m.3g.ghtkgg.cn/nnews/07544.htm
- http://m.3g.ghtkgg.cn/nnews/49876.htm
- http://m.3g.ghtkgg.cn/nnews/266391.htm
- http://m.3g.ghtkgg.cn/nnews/824631.htm
- http://m.3g.ghtkgg.cn/nnews/042422.htm
- http://m.3g.ghtkgg.cn/nnews/6386949.htm
- http://m.3g.ghtkgg.cn/nnews/4526339.htm
- http://m.3g.ghtkgg.cn/nnews/8624999.htm
- http://m.3g.ghtkgg.cn/nnews/3226259.htm
- http://m.3g.ghtkgg.cn/nnews/869622.htm
- http://m.3g.ghtkgg.cn/nnews/8344.htm
- http://m.3g.ghtkgg.cn/nnews/652825.htm
- http://m.3g.ghtkgg.cn/nnews/5451508.htm
- http://m.3g.ghtkgg.cn/nnews/4225.htm
- http://m.3g.ghtkgg.cn/nnews/72191.htm
- http://m.3g.ghtkgg.cn/nnews/3393.htm
- http://m.3g.ghtkgg.cn/nnews/219426.htm
- http://m.3g.ghtkgg.cn/nnews/8747.htm
- http://m.3g.ghtkgg.cn/nnews/07461.htm
- http://m.3g.ghtkgg.cn/nnews/0139.htm
- http://m.3g.ghtkgg.cn/nnews/3103101.htm
- http://m.3g.ghtkgg.cn/nnews/6318717.htm
- http://m.3g.ghtkgg.cn/nnews/6101406.htm
- http://m.3g.ghtkgg.cn/nnews/9435990.htm
- http://m.3g.ghtkgg.cn/nnews/3497.htm
- http://m.3g.ghtkgg.cn/nnews/5216696.htm
- http://m.3g.ghtkgg.cn/nnews/2637988.htm
- http://m.3g.ghtkgg.cn/nnews/086626.htm
- http://m.3g.ghtkgg.cn/nnews/9941837.htm
- http://m.3g.ghtkgg.cn/nnews/0307500.htm
- http://m.3g.ghtkgg.cn/nnews/9032.htm
- http://m.3g.ghtkgg.cn/nnews/5980.htm
- http://m.3g.ghtkgg.cn/nnews/9396.htm
- http://m.3g.ghtkgg.cn/nnews/9327807.htm
- http://m.3g.ghtkgg.cn/nnews/5648131.htm
- http://m.3g.ghtkgg.cn/nnews/84946.htm
- http://m.3g.ghtkgg.cn/nnews/884434.htm
- http://m.3g.ghtkgg.cn/nnews/6544.htm
- http://m.3g.ghtkgg.cn/nnews/4398.htm
- http://m.3g.ghtkgg.cn/nnews/176828.htm
- http://m.3g.ghtkgg.cn/nnews/2368.htm
- http://m.3g.ghtkgg.cn/nnews/068201.htm
- http://m.3g.ghtkgg.cn/nnews/7849409.htm
- http://m.3g.ghtkgg.cn/nnews/14464.htm
- http://m.3g.ghtkgg.cn/nnews/4498205.htm
- http://m.3g.ghtkgg.cn/nnews/953301.htm
- http://m.3g.ghtkgg.cn/nnews/8283724.htm
- http://m.3g.ghtkgg.cn/nnews/68186.htm
- http://m.3g.ghtkgg.cn/nnews/401785.htm
- http://m.3g.ghtkgg.cn/nnews/8640517.htm
- http://m.3g.ghtkgg.cn/nnews/26983.htm
- http://m.3g.ghtkgg.cn/nnews/91596.htm
- http://m.3g.ghtkgg.cn/nnews/9098.htm
- http://m.3g.ghtkgg.cn/nnews/2684.htm
- http://m.3g.ghtkgg.cn/nnews/8308.htm
- http://m.3g.ghtkgg.cn/nnews/269541.htm
- http://m.3g.ghtkgg.cn/nnews/782201.htm
- http://m.3g.ghtkgg.cn/nnews/6320.htm
- http://m.3g.ghtkgg.cn/nnews/8674.htm
- http://m.3g.ghtkgg.cn/nnews/277982.htm
- http://m.3g.ghtkgg.cn/nnews/633559.htm
- http://m.3g.ghtkgg.cn/nnews/82022.htm
- http://m.3g.ghtkgg.cn/nnews/468578.htm
- http://m.3g.ghtkgg.cn/nnews/84057.htm
- http://m.3g.ghtkgg.cn/nnews/480488.htm
- http://m.3g.ghtkgg.cn/nnews/5589654.htm
- http://m.3g.ghtkgg.cn/nnews/1694161.htm
- http://m.3g.ghtkgg.cn/nnews/5003.htm
- http://m.3g.ghtkgg.cn/nnews/17535.htm
- http://m.3g.ghtkgg.cn/nnews/1352.htm
- http://m.3g.ghtkgg.cn/nnews/448600.htm
- http://m.3g.ghtkgg.cn/nnews/8623319.htm
- http://m.3g.ghtkgg.cn/nnews/361717.htm
- http://m.3g.ghtkgg.cn/nnews/82684.htm
- http://m.3g.ghtkgg.cn/nnews/6297.htm
- http://m.3g.ghtkgg.cn/nnews/5196.htm
- http://m.3g.ghtkgg.cn/nnews/94204.htm
- http://m.3g.ghtkgg.cn/nnews/21018.htm
- http://m.3g.ghtkgg.cn/nnews/87170.htm
- http://m.3g.ghtkgg.cn/nnews/35699.htm
- http://m.3g.ghtkgg.cn/nnews/2318.htm
- http://m.3g.ghtkgg.cn/nnews/57158.htm
- http://m.3g.ghtkgg.cn/nnews/0790.htm
- http://m.3g.ghtkgg.cn/nnews/672996.htm
- http://m.3g.ghtkgg.cn/nnews/380882.htm
- http://m.3g.ghtkgg.cn/nnews/6979.htm
- http://m.3g.ghtkgg.cn/nnews/8542.htm
- http://m.3g.ghtkgg.cn/nnews/85848.htm
- http://m.3g.ghtkgg.cn/nnews/013921.htm
- http://m.3g.ghtkgg.cn/nnews/037003.htm
- http://m.3g.ghtkgg.cn/nnews/9782338.htm
- http://m.3g.ghtkgg.cn/nnews/5299.htm
- http://m.3g.ghtkgg.cn/nnews/84862.htm
- http://m.3g.ghtkgg.cn/nnews/503245.htm
- http://m.3g.ghtkgg.cn/nnews/85506.htm
- http://m.3g.ghtkgg.cn/nnews/4861464.htm
- http://m.3g.ghtkgg.cn/nnews/694108.htm
- http://m.3g.ghtkgg.cn/nnews/7318.htm
- http://m.3g.ghtkgg.cn/nnews/0986.htm
- http://m.3g.ghtkgg.cn/nnews/3741677.htm
- http://m.3g.ghtkgg.cn/nnews/1031000.htm
- http://m.3g.ghtkgg.cn/nnews/9346.htm
- http://m.3g.ghtkgg.cn/nnews/363857.htm
- http://m.3g.ghtkgg.cn/nnews/6801872.htm
- http://m.3g.ghtkgg.cn/nnews/385674.htm
- http://m.3g.ghtkgg.cn/nnews/75636.htm
- http://m.3g.ghtkgg.cn/nnews/8047626.htm
- http://m.3g.ghtkgg.cn/nnews/24112.htm
- http://m.3g.ghtkgg.cn/nnews/37573.htm
- http://m.3g.ghtkgg.cn/nnews/0024.htm
- http://m.3g.ghtkgg.cn/nnews/09232.htm
- http://m.3g.ghtkgg.cn/nnews/7041678.htm
- http://m.3g.ghtkgg.cn/nnews/9578843.htm
- http://m.3g.ghtkgg.cn/nnews/870390.htm
- http://m.3g.ghtkgg.cn/nnews/64349.htm
- http://m.3g.ghtkgg.cn/nnews/2361.htm
- http://m.3g.ghtkgg.cn/nnews/761722.htm
- http://m.3g.ghtkgg.cn/nnews/8334.htm
- http://m.3g.ghtkgg.cn/nnews/8367.htm
- http://m.3g.ghtkgg.cn/nnews/3266571.htm
- http://m.3g.ghtkgg.cn/nnews/255907.htm
- http://m.3g.ghtkgg.cn/nnews/86356.htm
- http://m.3g.ghtkgg.cn/nnews/3994160.htm
- http://m.3g.ghtkgg.cn/nnews/5472616.htm
- http://m.3g.ghtkgg.cn/nnews/3121220.htm
- http://m.3g.ghtkgg.cn/nnews/31398.htm
- http://m.3g.ghtkgg.cn/nnews/314294.htm
- http://m.3g.ghtkgg.cn/nnews/724333.htm
- http://m.3g.ghtkgg.cn/nnews/89415.htm
- http://m.3g.ghtkgg.cn/nnews/635285.htm
- http://m.3g.ghtkgg.cn/nnews/410858.htm
- http://m.3g.ghtkgg.cn/nnews/3607.htm
- http://m.3g.ghtkgg.cn/nnews/336935.htm
- http://m.3g.ghtkgg.cn/nnews/911021.htm
- http://m.3g.ghtkgg.cn/nnews/415513.htm
- http://m.3g.ghtkgg.cn/nnews/4405965.htm
- http://m.3g.ghtkgg.cn/nnews/9850611.htm
- http://m.3g.ghtkgg.cn/nnews/210808.htm
- http://m.3g.ghtkgg.cn/nnews/064433.htm
- http://m.3g.ghtkgg.cn/nnews/0144.htm
- http://m.3g.ghtkgg.cn/nnews/55540.htm
- http://m.3g.ghtkgg.cn/nnews/0600985.htm
- http://m.3g.ghtkgg.cn/nnews/702896.htm
- http://m.3g.ghtkgg.cn/nnews/433962.htm
- http://m.3g.ghtkgg.cn/nnews/9964138.htm
- http://m.3g.ghtkgg.cn/nnews/1890540.htm
- http://m.3g.ghtkgg.cn/nnews/80032.htm
- http://m.3g.ghtkgg.cn/nnews/3901.htm
- http://m.3g.ghtkgg.cn/nnews/69663.htm
- http://m.3g.ghtkgg.cn/nnews/6758951.htm
- http://m.3g.ghtkgg.cn/nnews/4163816.htm
- http://m.3g.ghtkgg.cn/nnews/79215.htm
- http://m.3g.ghtkgg.cn/nnews/16002.htm
- http://m.3g.ghtkgg.cn/nnews/305622.htm
- http://m.3g.ghtkgg.cn/nnews/6868.htm
- http://m.3g.ghtkgg.cn/nnews/995526.htm
- http://m.3g.ghtkgg.cn/nnews/9668959.htm
- http://m.3g.ghtkgg.cn/nnews/900522.htm
- http://m.3g.ghtkgg.cn/nnews/4162.htm
- http://m.3g.ghtkgg.cn/nnews/568776.htm
- http://m.3g.ghtkgg.cn/nnews/461090.htm
- http://m.3g.ghtkgg.cn/nnews/032014.htm
- http://m.3g.ghtkgg.cn/nnews/87950.htm
- http://m.3g.ghtkgg.cn/nnews/8821.htm
- http://m.3g.ghtkgg.cn/nnews/9964266.htm
- http://m.3g.ghtkgg.cn/nnews/63560.htm
- http://m.3g.ghtkgg.cn/nnews/9146641.htm
- http://m.3g.ghtkgg.cn/nnews/3177813.htm
- http://m.3g.ghtkgg.cn/nnews/10883.htm
- http://m.3g.ghtkgg.cn/nnews/509009.htm
- http://m.3g.ghtkgg.cn/nnews/491129.htm
- http://m.3g.ghtkgg.cn/nnews/0615.htm
- http://m.3g.ghtkgg.cn/nnews/858571.htm
- http://m.3g.ghtkgg.cn/nnews/713331.htm
- http://m.3g.ghtkgg.cn/nnews/648460.htm
- http://m.3g.ghtkgg.cn/nnews/47236.htm
- http://m.3g.ghtkgg.cn/nnews/13573.htm
- http://m.3g.ghtkgg.cn/nnews/5735818.htm
- http://m.3g.ghtkgg.cn/nnews/18809.htm
- http://m.3g.ghtkgg.cn/nnews/8937.htm
- http://m.3g.ghtkgg.cn/nnews/436044.htm
- http://m.3g.ghtkgg.cn/nnews/8990007.htm
- http://m.3g.ghtkgg.cn/nnews/9844531.htm
- http://m.3g.ghtkgg.cn/nnews/66904.htm
- http://m.3g.ghtkgg.cn/nnews/8110958.htm
- http://m.3g.ghtkgg.cn/nnews/385432.htm
- http://m.3g.ghtkgg.cn/nnews/984792.htm
- http://m.3g.ghtkgg.cn/nnews/80111.htm
- http://m.3g.ghtkgg.cn/nnews/2116530.htm
- http://m.3g.ghtkgg.cn/nnews/00233.htm
- http://m.3g.ghtkgg.cn/nnews/3706.htm
- http://m.3g.ghtkgg.cn/nnews/1299.htm
- http://m.3g.ghtkgg.cn/nnews/807810.htm
- http://m.3g.ghtkgg.cn/nnews/4199394.htm
- http://m.3g.ghtkgg.cn/nnews/374221.htm
- http://m.3g.ghtkgg.cn/nnews/184347.htm
- http://m.3g.ghtkgg.cn/nnews/17492.htm
- http://m.3g.ghtkgg.cn/nnews/2655206.htm
- http://m.3g.ghtkgg.cn/nnews/99242.htm
- http://m.3g.ghtkgg.cn/nnews/3571996.htm
- http://m.3g.ghtkgg.cn/nnews/01557.htm
- http://m.3g.ghtkgg.cn/nnews/2041798.htm
- http://m.3g.ghtkgg.cn/nnews/419764.htm
- http://m.3g.ghtkgg.cn/nnews/7446.htm
- http://m.3g.ghtkgg.cn/nnews/55021.htm
- http://m.3g.ghtkgg.cn/nnews/288758.htm
- http://m.3g.ghtkgg.cn/nnews/51811.htm
- http://m.3g.ghtkgg.cn/nnews/18461.htm
- http://m.3g.ghtkgg.cn/nnews/5864.htm
- http://m.3g.ghtkgg.cn/nnews/2794.htm
- http://m.3g.ghtkgg.cn/nnews/55617.htm
- http://m.3g.ghtkgg.cn/nnews/38887.htm
- http://m.3g.ghtkgg.cn/nnews/8316.htm
- http://m.3g.ghtkgg.cn/nnews/2957794.htm
- http://m.3g.ghtkgg.cn/nnews/7881.htm
- http://m.3g.ghtkgg.cn/nnews/25928.htm
- http://m.3g.ghtkgg.cn/nnews/9057856.htm
- http://m.3g.ghtkgg.cn/nnews/5176949.htm
- http://m.3g.ghtkgg.cn/nnews/62922.htm
- http://m.3g.ghtkgg.cn/nnews/6694773.htm
- http://m.3g.ghtkgg.cn/nnews/7075781.htm
- http://m.3g.ghtkgg.cn/nnews/0084042.htm
- http://m.3g.ghtkgg.cn/nnews/10781.htm
- http://m.3g.ghtkgg.cn/nnews/4371.htm
- http://m.3g.ghtkgg.cn/nnews/04863.htm
- http://m.3g.ghtkgg.cn/nnews/30789.htm
- http://m.3g.ghtkgg.cn/nnews/22946.htm
- http://m.3g.ghtkgg.cn/nnews/572575.htm
- http://m.3g.ghtkgg.cn/nnews/1509.htm
- http://m.3g.ghtkgg.cn/nnews/143476.htm
- http://m.3g.ghtkgg.cn/nnews/92025.htm
- http://m.3g.ghtkgg.cn/nnews/9135347.htm
- http://m.3g.ghtkgg.cn/nnews/4200211.htm
- http://m.3g.ghtkgg.cn/nnews/56804.htm
- http://m.3g.ghtkgg.cn/nnews/324143.htm
- http://m.3g.ghtkgg.cn/nnews/94523.htm
- http://m.3g.ghtkgg.cn/nnews/08315.htm
- http://m.3g.ghtkgg.cn/nnews/9884.htm
- http://m.3g.ghtkgg.cn/nnews/85691.htm
- http://m.3g.ghtkgg.cn/nnews/659357.htm
- http://m.3g.ghtkgg.cn/nnews/80052.htm
- http://m.3g.ghtkgg.cn/nnews/0785.htm
- http://m.3g.ghtkgg.cn/nnews/142150.htm
- http://m.3g.ghtkgg.cn/nnews/77740.htm
- http://m.3g.ghtkgg.cn/nnews/315699.htm
- http://m.3g.ghtkgg.cn/nnews/4067148.htm
- http://m.3g.ghtkgg.cn/nnews/897897.htm
- http://m.3g.ghtkgg.cn/nnews/5657562.htm
- http://m.3g.ghtkgg.cn/nnews/9711.htm
- http://m.3g.ghtkgg.cn/nnews/9272.htm
- http://m.3g.ghtkgg.cn/nnews/6130660.htm
- http://m.3g.ghtkgg.cn/nnews/6541186.htm
- http://m.3g.ghtkgg.cn/nnews/2707439.htm
- http://m.3g.ghtkgg.cn/nnews/810986.htm
- http://m.3g.ghtkgg.cn/nnews/33395.htm
- http://m.3g.ghtkgg.cn/nnews/315945.htm
- http://m.3g.ghtkgg.cn/nnews/57861.htm
- http://m.3g.ghtkgg.cn/nnews/812649.htm
- http://m.3g.ghtkgg.cn/nnews/3368.htm
- http://m.3g.ghtkgg.cn/nnews/57477.htm
- http://m.3g.ghtkgg.cn/nnews/02255.htm
- http://m.3g.ghtkgg.cn/nnews/301978.htm
- http://m.3g.ghtkgg.cn/nnews/306160.htm
- http://m.3g.ghtkgg.cn/nnews/357505.htm
- http://m.3g.ghtkgg.cn/nnews/1072.htm
- http://m.3g.ghtkgg.cn/nnews/76244.htm
- http://m.3g.ghtkgg.cn/nnews/71623.htm
- http://m.3g.ghtkgg.cn/nnews/95728.htm
- http://m.3g.ghtkgg.cn/nnews/91199.htm
- http://m.3g.ghtkgg.cn/nnews/83777.htm
- http://m.3g.ghtkgg.cn/nnews/321936.htm
- http://m.3g.ghtkgg.cn/nnews/36591.htm
- http://m.3g.ghtkgg.cn/nnews/79958.htm
- http://m.3g.ghtkgg.cn/nnews/57440.htm
- http://m.3g.ghtkgg.cn/nnews/1934.htm
- http://m.3g.ghtkgg.cn/nnews/2302.htm
- http://m.3g.ghtkgg.cn/nnews/9131691.htm
- http://m.3g.ghtkgg.cn/nnews/051257.htm
- http://m.3g.ghtkgg.cn/nnews/89311.htm
- http://m.3g.ghtkgg.cn/nnews/26758.htm
- http://m.3g.ghtkgg.cn/nnews/918372.htm
- http://m.3g.ghtkgg.cn/nnews/281839.htm
- http://m.3g.ghtkgg.cn/nnews/317149.htm
- http://m.3g.ghtkgg.cn/nnews/8769.htm
- http://m.3g.ghtkgg.cn/nnews/0861.htm
- http://m.3g.ghtkgg.cn/nnews/21369.htm
- http://m.3g.ghtkgg.cn/nnews/429092.htm
- http://m.3g.ghtkgg.cn/nnews/4167.htm
- http://m.3g.ghtkgg.cn/nnews/466007.htm
- http://m.3g.ghtkgg.cn/nnews/06051.htm
- http://m.3g.ghtkgg.cn/nnews/30542.htm

## 项目结构

```
newslink-catalog/
├── bin/                             # 可执行入口与命令行工具
│   └── cli.js                       # 主命令行入口，接收导入、构建、检测等子命令
├── src/                             # 核心源代码目录
│   ├── core/                        # 核心逻辑模块
│   │   ├── parser.js                # URL 解析与特征提取
│   │   ├── dedupe.js                # 去重与合并算法
│   │   └── validator.js             # 链接格式与存活校验
│   ├── render/                      # 渲染引擎
│   │   ├── template-engine.js       # 模板编译与变量替换
│   │   ├── markdown-generator.js    # Markdown 表格与列表输出
│   │   └── html-theme.js            # 默认 HTML 主题样式与布局
│   ├── io/                          # 输入输出处理
│   │   ├── importer.js              # 多种格式导入（txt/csv/json）
│   │   ├── exporter.js              # 导出至 JSON/Markdown/HTML
│   │   └── file-watcher.js          # 开发模式下的文件变更监听
│   └── utils/                       # 通用工具函数
│       ├── logger.js                # 分级日志输出（info/warn/error）
│       ├── config-loader.js         # 读取与合并用户配置文件
│       └── network.js               # HTTP 请求封装，用于存活检测
├── templates/                       # 用户可覆盖的模板文件
│   ├── default.html                 # 默认页面骨架
│   ├── item-partial.html            # 单条链接渲染片段
│   └── nav-partial.html             # 分类导航渲染片段
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 针对核心函数的单元测试
│   └── fixtures/                    # 测试用的静态数据样本
├── config/                          # 配置示例与默认配置
│   ├── default.yaml                 # 默认配置项（分类规则、检测间隔）
│   └── schema.json                  # 配置文件 JSON Schema 校验
├── docs/                            # 完整文档（除 README 外的补充文档）
│   ├── getting-started.md
│   ├── configuration.md
│   ├── import-export.md
│   └── deployment.md
├── dist/                            # 构建输出目录（默认忽略，不纳入版本库）
├── .gitignore
├── package.json                     # npm 依赖与脚本声明
├── README.md                        # 本文件
└── LICENSE                          # MIT 许可证文本
```

## 贡献指南

提交 Issue 报告缺陷或功能请求 在 GitHub Issues 页面新建 Issue，使用提供的模板填写复现步骤、预期行为与实际行为，或详细描述期望增加的功能及使用场景。

派生仓库并创建功能分支 将项目派生至个人账号下，基于 main 分支新建以 feature/ 或 fix/ 为前缀的分支，例如 feature/support-csv-export。

编写或更新测试用例 针对新增代码或修复的缺陷，在 tests/ 对应目录下补充单元测试或集成测试，确保测试覆盖率达到现有水平以上。

提交 Pull Request 并关联 Issue 在 PR 描述中明确关联相关 Issue 编号，列出变更摘要、测试结果以及是否包含破坏性变更。PR 需通过所有 CI 检查项后方可合并。

更新文档与示例 若变更涉及配置项、命令行参数或导出格式，须同步更新 docs/ 下对应文档以及 README 中的相关章节，保证文档与实现保持一致。

## 常见问题

如何批量导入已有书签文件中的链接
本工具内置的导入器支持 CSV 和纯文本格式。若书签文件为 HTML 格式（如浏览器导出的 bookmarks.html），建议先使用在线工具或脚本提取其中的 URL 列表，保存为每行一个 URL 的纯文本文件，然后通过 `newslink-catalog import --from text --input bookmarks.txt` 命令导入。未来版本将考虑直接解析 HTML 书签文件。

存活检测是否会对外部站点造成压力
存活检测使用 HEAD 请求且默认超时为 5 秒，并发数限制为 10 个连接，间隔为 2 秒。该设计旨在避免对目标服务器造成异常流量。对于大型目录，建议在非高峰时段运行检测，或通过配置 `--concurrency 3` 进一步降低并发。

生成的静态页面能否部署到 GitLab Pages 或 Cloudflare Pages
可以。`dist/` 目录包含完整的静态资源，无需后端服务。将构建产物推送到 GitLab Pages 的 `public/` 目录或 Cloudflare Pages 关联的仓库即可自动部署。需确保项目配置文件中的 `baseUrl` 字段与部署域名一致，以保证导航链接正确。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:58
