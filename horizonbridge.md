# WebLink Navigator

WebLink Navigator 是一个面向技术研究、信息聚合与内容追溯的轻量级外链资源导航系统。该项目定位于帮助开发者、数据分析师、内容研究员及运维人员高效管理和访问分散于互联网各处的结构化新闻与资讯链接。系统以静态资源索引为核心，提供统一的条目化访问入口，支持快速检索、批量导入、状态监控与元数据标注，适用于需要长期维护大量外链来源的场景。

WebLink Navigator 不依赖动态数据库，所有链接资源以纯文本与结构化目录方式组织，兼容主流静态站点生成工具与CI/CD工作流。项目默认集成第163/300批次共计300条新闻类URL，覆盖多主题、多时间点的信息节点，可作为外链仓库的种子数据直接使用。

## 功能概览

统一条目管理 提供一致的条目标识与访问路径，每条资源独立编号并归档至对应批次目录，支持按批次、按时间、按来源域名进行归类与筛选。

静态索引生成 内置索引生成器，可根据原始URL列表自动生成HTML目录页与JSON结构映射，便于部署为静态站点或接入搜索服务。

批量导入与去重 支持从纯文本、CSV或JSON格式批量导入URL列表，自动进行基于域名与路径的重复检测，避免冗余条目占用存储与检索资源。

元数据扩展字段 每条链接支持可选的标题、摘要、标签、抓取时间、状态码与备注字段，用户可通过附属配置文件补充元数据，提升检索与筛选精度。

健康状态检查 集成轻量级HTTP状态检测模块，可定时或按需发起HEAD请求，标记失效链接并生成异常报告，辅助维护链接可用性。

标签分类与过滤 允许为每条资源添加一个或多个分类标签（如technology、finance、health、policy），并基于标签进行快速过滤与聚合统计。

导出与分享 支持将选定批次或全部链接导出为Markdown列表、JSON数组或纯文本格式，便于嵌入其他文档系统或与协作者分享。

访问统计记录 可选启用本地访问日志，记录每条链接的查询次数与最后访问时间，帮助识别高频资源与冷门数据。

## 应用场景

技术文档外链仓库 技术团队在撰写文档、博客或API说明时，可将所有引用的外部参考资料统一纳入WebLink Navigator进行管理。每个链接对应一个独立条目，支持添加备注说明引用原因与上下文，避免文档中散落大量裸URL导致维护困难。

数据分析素材索引 数据分析师在采集网络新闻、报告或公开数据源时，可使用本系统对原始链接进行编号与分类。配合标签功能，可快速筛选特定领域（如宏观经济、行业动态）的素材集合，为后续分析提供可追溯的数据来源清单。

运维监控告警关联 运维人员可将监控系统产生的告警文档、故障排查指南或外部知识库链接录入WebLink Navigator，并利用健康检查模块定期验证外部文档的可用性。当某条链接失效时，系统可输出异常报告，提示运维团队更新或替换引用。

内容聚合与定期回顾 内容编辑或信息研究员可按批次导入每日采集的新闻链接，利用元数据字段记录摘要与关键词。每周或每月生成特定标签的链接列表，用于内部简报、行业动态周报或竞品信息追踪。

## 快速开始

以下命令演示了从克隆仓库到启动本地预览服务的完整流程。请确保系统已安装Git与Node.js（或任意静态服务器工具）。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run build
npm run serve
```

执行完成后，访问 http://localhost:8080 即可查看索引页面。若需仅生成静态文件而不启动服务，可执行 `npm run build`，输出目录为 `dist/`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | >= 16.0.0 | 运行时环境，用于执行索引生成与构建脚本 |
| npm | >= 8.0.0 | 包管理器，用于安装项目依赖 |
| Git | >= 2.30.0 | 版本控制工具，用于克隆仓库与提交变更 |
| curl | >= 7.68.0 | 可选组件，用于健康检查模块的HTTP请求 |
| bash | >= 4.0 | 用于运行辅助脚本与快捷命令 |
| 磁盘空间 | >= 50 MB | 用于存放源码、索引文件与日志 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何导入链接、添加标签、导出列表、配置检查任务 |
| 管理员指南 | docs/admin-guide.md | 如何自定义索引模板、调整批次结构、部署静态站点 |
| 开发者文档 | docs/developer-guide.md | 如何扩展元数据字段、编写自定义过滤器、集成外部API |
| 故障排查 | docs/troubleshooting.md | 健康检查失败如何诊断、索引生成报错如何解决、日志位置与解读 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/1972.htm
- http://m.wap.ghtkgg.cn/jnews/4721.htm
- http://m.wap.ghtkgg.cn/jnews/093896.htm
- http://m.wap.ghtkgg.cn/jnews/679389.htm
- http://m.wap.ghtkgg.cn/jnews/653966.htm
- http://m.wap.ghtkgg.cn/jnews/946727.htm
- http://m.wap.ghtkgg.cn/jnews/9496288.htm
- http://m.wap.ghtkgg.cn/jnews/252061.htm
- http://m.wap.ghtkgg.cn/jnews/5128.htm
- http://m.wap.ghtkgg.cn/jnews/442143.htm
- http://m.wap.ghtkgg.cn/jnews/7031389.htm
- http://m.wap.ghtkgg.cn/jnews/7153852.htm
- http://m.wap.ghtkgg.cn/jnews/1466714.htm
- http://m.wap.ghtkgg.cn/jnews/566065.htm
- http://m.wap.ghtkgg.cn/jnews/7939.htm
- http://m.wap.ghtkgg.cn/jnews/8541.htm
- http://m.wap.ghtkgg.cn/jnews/34625.htm
- http://m.wap.ghtkgg.cn/jnews/35542.htm
- http://m.wap.ghtkgg.cn/jnews/797076.htm
- http://m.wap.ghtkgg.cn/jnews/381018.htm
- http://m.wap.ghtkgg.cn/jnews/1311848.htm
- http://m.wap.ghtkgg.cn/jnews/8521639.htm
- http://m.wap.ghtkgg.cn/jnews/16044.htm
- http://m.wap.ghtkgg.cn/jnews/3132.htm
- http://m.wap.ghtkgg.cn/jnews/4723.htm
- http://m.wap.ghtkgg.cn/jnews/921112.htm
- http://m.wap.ghtkgg.cn/jnews/2851.htm
- http://m.wap.ghtkgg.cn/jnews/3091.htm
- http://m.wap.ghtkgg.cn/jnews/6727.htm
- http://m.wap.ghtkgg.cn/jnews/990184.htm
- http://m.wap.ghtkgg.cn/jnews/05571.htm
- http://m.wap.ghtkgg.cn/jnews/19315.htm
- http://m.wap.ghtkgg.cn/jnews/4254423.htm
- http://m.wap.ghtkgg.cn/jnews/08825.htm
- http://m.wap.ghtkgg.cn/jnews/2646322.htm
- http://m.wap.ghtkgg.cn/jnews/2688587.htm
- http://m.wap.ghtkgg.cn/jnews/6470.htm
- http://m.wap.ghtkgg.cn/jnews/9266369.htm
- http://m.wap.ghtkgg.cn/jnews/3564294.htm
- http://m.wap.ghtkgg.cn/jnews/2809733.htm
- http://m.wap.ghtkgg.cn/jnews/67734.htm
- http://m.wap.ghtkgg.cn/jnews/6450.htm
- http://m.wap.ghtkgg.cn/jnews/088573.htm
- http://m.wap.ghtkgg.cn/jnews/5801724.htm
- http://m.wap.ghtkgg.cn/jnews/8925431.htm
- http://m.wap.ghtkgg.cn/jnews/60058.htm
- http://m.wap.ghtkgg.cn/jnews/59316.htm
- http://m.wap.ghtkgg.cn/jnews/978133.htm
- http://m.wap.ghtkgg.cn/jnews/15311.htm
- http://m.wap.ghtkgg.cn/jnews/8613.htm
- http://m.wap.ghtkgg.cn/jnews/97260.htm
- http://m.wap.ghtkgg.cn/jnews/966055.htm
- http://m.wap.ghtkgg.cn/jnews/4942.htm
- http://m.wap.ghtkgg.cn/jnews/856606.htm
- http://m.wap.ghtkgg.cn/jnews/647503.htm
- http://m.wap.ghtkgg.cn/jnews/03248.htm
- http://m.wap.ghtkgg.cn/jnews/281465.htm
- http://m.wap.ghtkgg.cn/jnews/284973.htm
- http://m.wap.ghtkgg.cn/jnews/6315537.htm
- http://m.wap.ghtkgg.cn/jnews/88129.htm
- http://m.wap.ghtkgg.cn/jnews/97630.htm
- http://m.wap.ghtkgg.cn/jnews/3295.htm
- http://m.wap.ghtkgg.cn/jnews/0286000.htm
- http://m.wap.ghtkgg.cn/jnews/554649.htm
- http://m.wap.ghtkgg.cn/jnews/101604.htm
- http://m.wap.ghtkgg.cn/jnews/56922.htm
- http://m.wap.ghtkgg.cn/jnews/170231.htm
- http://m.wap.ghtkgg.cn/jnews/2600008.htm
- http://m.wap.ghtkgg.cn/jnews/291524.htm
- http://m.wap.ghtkgg.cn/jnews/0573.htm
- http://m.wap.ghtkgg.cn/jnews/8113957.htm
- http://m.wap.ghtkgg.cn/jnews/0408.htm
- http://m.wap.ghtkgg.cn/jnews/1785021.htm
- http://m.wap.ghtkgg.cn/jnews/2039897.htm
- http://m.wap.ghtkgg.cn/jnews/6683.htm
- http://m.wap.ghtkgg.cn/jnews/93015.htm
- http://m.wap.ghtkgg.cn/jnews/41795.htm
- http://m.wap.ghtkgg.cn/jnews/847084.htm
- http://m.wap.ghtkgg.cn/jnews/311703.htm
- http://m.wap.ghtkgg.cn/jnews/6291.htm
- http://m.wap.ghtkgg.cn/jnews/2692349.htm
- http://m.wap.ghtkgg.cn/jnews/18759.htm
- http://m.wap.ghtkgg.cn/jnews/505146.htm
- http://m.wap.ghtkgg.cn/jnews/7532586.htm
- http://m.wap.ghtkgg.cn/jnews/12844.htm
- http://m.wap.ghtkgg.cn/jnews/7515456.htm
- http://m.wap.ghtkgg.cn/jnews/10939.htm
- http://m.wap.ghtkgg.cn/jnews/1713500.htm
- http://m.wap.ghtkgg.cn/jnews/0582.htm
- http://m.wap.ghtkgg.cn/jnews/391342.htm
- http://m.wap.ghtkgg.cn/jnews/265334.htm
- http://m.wap.ghtkgg.cn/jnews/4286.htm
- http://m.wap.ghtkgg.cn/jnews/0740848.htm
- http://m.wap.ghtkgg.cn/jnews/3824433.htm
- http://m.wap.ghtkgg.cn/jnews/4927.htm
- http://m.wap.ghtkgg.cn/jnews/8555593.htm
- http://m.wap.ghtkgg.cn/jnews/6201481.htm
- http://m.wap.ghtkgg.cn/jnews/9778.htm
- http://m.wap.ghtkgg.cn/jnews/056610.htm
- http://m.wap.ghtkgg.cn/jnews/0780.htm
- http://m.wap.ghtkgg.cn/jnews/9205144.htm
- http://m.wap.ghtkgg.cn/jnews/9871.htm
- http://m.wap.ghtkgg.cn/jnews/2698976.htm
- http://m.wap.ghtkgg.cn/jnews/2443.htm
- http://m.wap.ghtkgg.cn/jnews/9068156.htm
- http://m.wap.ghtkgg.cn/jnews/638488.htm
- http://m.wap.ghtkgg.cn/jnews/893238.htm
- http://m.wap.ghtkgg.cn/jnews/52837.htm
- http://m.wap.ghtkgg.cn/jnews/4180.htm
- http://m.wap.ghtkgg.cn/jnews/7003.htm
- http://m.wap.ghtkgg.cn/jnews/27697.htm
- http://m.wap.ghtkgg.cn/jnews/9932767.htm
- http://m.wap.ghtkgg.cn/jnews/88464.htm
- http://m.wap.ghtkgg.cn/jnews/213166.htm
- http://m.wap.ghtkgg.cn/jnews/5685.htm
- http://m.wap.ghtkgg.cn/jnews/518128.htm
- http://m.wap.ghtkgg.cn/jnews/64811.htm
- http://m.wap.ghtkgg.cn/jnews/95659.htm
- http://m.wap.ghtkgg.cn/jnews/55309.htm
- http://m.wap.ghtkgg.cn/jnews/858247.htm
- http://m.wap.ghtkgg.cn/jnews/67904.htm
- http://m.wap.ghtkgg.cn/jnews/48200.htm
- http://m.wap.ghtkgg.cn/jnews/76740.htm
- http://m.wap.ghtkgg.cn/jnews/551637.htm
- http://m.wap.ghtkgg.cn/jnews/720722.htm
- http://m.wap.ghtkgg.cn/jnews/26746.htm
- http://m.wap.ghtkgg.cn/jnews/391373.htm
- http://m.wap.ghtkgg.cn/jnews/27374.htm
- http://m.wap.ghtkgg.cn/jnews/986493.htm
- http://m.wap.ghtkgg.cn/jnews/133029.htm
- http://m.wap.ghtkgg.cn/jnews/419875.htm
- http://m.wap.ghtkgg.cn/jnews/91559.htm
- http://m.wap.ghtkgg.cn/jnews/0548.htm
- http://m.wap.ghtkgg.cn/jnews/6575.htm
- http://m.wap.ghtkgg.cn/jnews/931624.htm
- http://m.wap.ghtkgg.cn/jnews/210374.htm
- http://m.wap.ghtkgg.cn/jnews/458561.htm
- http://m.wap.ghtkgg.cn/jnews/7832.htm
- http://m.wap.ghtkgg.cn/jnews/153286.htm
- http://m.wap.ghtkgg.cn/jnews/76710.htm
- http://m.wap.ghtkgg.cn/jnews/2357219.htm
- http://m.wap.ghtkgg.cn/jnews/338403.htm
- http://m.wap.ghtkgg.cn/jnews/4199.htm
- http://m.wap.ghtkgg.cn/jnews/96659.htm
- http://m.wap.ghtkgg.cn/jnews/88855.htm
- http://m.wap.ghtkgg.cn/jnews/52997.htm
- http://m.wap.ghtkgg.cn/jnews/303281.htm
- http://m.wap.ghtkgg.cn/jnews/402290.htm
- http://m.wap.ghtkgg.cn/jnews/1311.htm
- http://m.wap.ghtkgg.cn/jnews/56177.htm
- http://m.wap.ghtkgg.cn/jnews/8353.htm
- http://m.wap.ghtkgg.cn/jnews/25000.htm
- http://m.wap.ghtkgg.cn/jnews/9790426.htm
- http://m.wap.ghtkgg.cn/jnews/63246.htm
- http://m.wap.ghtkgg.cn/jnews/757407.htm
- http://m.wap.ghtkgg.cn/jnews/3657454.htm
- http://m.wap.ghtkgg.cn/jnews/7899.htm
- http://m.wap.ghtkgg.cn/jnews/644568.htm
- http://m.wap.ghtkgg.cn/jnews/982346.htm
- http://m.wap.ghtkgg.cn/jnews/9311.htm
- http://m.wap.ghtkgg.cn/jnews/2029.htm
- http://m.wap.ghtkgg.cn/jnews/8924.htm
- http://m.wap.ghtkgg.cn/jnews/26811.htm
- http://m.wap.ghtkgg.cn/jnews/471337.htm
- http://m.wap.ghtkgg.cn/jnews/37537.htm
- http://m.wap.ghtkgg.cn/jnews/96604.htm
- http://m.wap.ghtkgg.cn/jnews/58425.htm
- http://m.wap.ghtkgg.cn/jnews/8167.htm
- http://m.wap.ghtkgg.cn/jnews/212585.htm
- http://m.wap.ghtkgg.cn/jnews/170455.htm
- http://m.wap.ghtkgg.cn/jnews/2325.htm
- http://m.wap.ghtkgg.cn/jnews/1137716.htm
- http://m.wap.ghtkgg.cn/jnews/282897.htm
- http://m.wap.ghtkgg.cn/jnews/6989756.htm
- http://m.wap.ghtkgg.cn/jnews/09607.htm
- http://m.wap.ghtkgg.cn/jnews/97000.htm
- http://m.wap.ghtkgg.cn/jnews/81904.htm
- http://m.wap.ghtkgg.cn/jnews/9391477.htm
- http://m.wap.ghtkgg.cn/jnews/34489.htm
- http://m.wap.ghtkgg.cn/jnews/723072.htm
- http://m.wap.ghtkgg.cn/jnews/132803.htm
- http://m.wap.ghtkgg.cn/jnews/33573.htm
- http://m.wap.ghtkgg.cn/jnews/876320.htm
- http://m.wap.ghtkgg.cn/jnews/708242.htm
- http://m.wap.ghtkgg.cn/jnews/0963211.htm
- http://m.wap.ghtkgg.cn/jnews/67649.htm
- http://m.wap.ghtkgg.cn/jnews/92001.htm
- http://m.wap.ghtkgg.cn/jnews/05568.htm
- http://m.wap.ghtkgg.cn/jnews/53193.htm
- http://m.wap.ghtkgg.cn/jnews/0260813.htm
- http://m.wap.ghtkgg.cn/jnews/3721626.htm
- http://m.wap.ghtkgg.cn/jnews/3419.htm
- http://m.wap.ghtkgg.cn/jnews/97463.htm
- http://m.wap.ghtkgg.cn/jnews/5620.htm
- http://m.wap.ghtkgg.cn/jnews/7876263.htm
- http://m.wap.ghtkgg.cn/jnews/20905.htm
- http://m.wap.ghtkgg.cn/jnews/363393.htm
- http://m.wap.ghtkgg.cn/jnews/1431978.htm
- http://m.wap.ghtkgg.cn/jnews/1690537.htm
- http://m.wap.ghtkgg.cn/jnews/09190.htm
- http://m.wap.ghtkgg.cn/jnews/879058.htm
- http://m.wap.ghtkgg.cn/jnews/44318.htm
- http://m.wap.ghtkgg.cn/jnews/1970.htm
- http://m.wap.ghtkgg.cn/jnews/79770.htm
- http://m.wap.ghtkgg.cn/jnews/756066.htm
- http://m.wap.ghtkgg.cn/jnews/537847.htm
- http://m.wap.ghtkgg.cn/jnews/63131.htm
- http://m.wap.ghtkgg.cn/jnews/8371649.htm
- http://m.wap.ghtkgg.cn/jnews/797014.htm
- http://m.wap.ghtkgg.cn/jnews/3961679.htm
- http://m.wap.ghtkgg.cn/jnews/786679.htm
- http://m.wap.ghtkgg.cn/jnews/7342290.htm
- http://m.wap.ghtkgg.cn/jnews/1268.htm
- http://m.wap.ghtkgg.cn/jnews/6154166.htm
- http://m.wap.ghtkgg.cn/jnews/0256.htm
- http://m.wap.ghtkgg.cn/jnews/69253.htm
- http://m.wap.ghtkgg.cn/jnews/2849.htm
- http://m.wap.ghtkgg.cn/jnews/2515.htm
- http://m.wap.ghtkgg.cn/jnews/14053.htm
- http://m.wap.ghtkgg.cn/jnews/287244.htm
- http://m.wap.ghtkgg.cn/jnews/590095.htm
- http://m.wap.ghtkgg.cn/jnews/177055.htm
- http://m.wap.ghtkgg.cn/jnews/36580.htm
- http://m.wap.ghtkgg.cn/jnews/985239.htm
- http://m.wap.ghtkgg.cn/jnews/95153.htm
- http://m.wap.ghtkgg.cn/jnews/8045.htm
- http://m.wap.ghtkgg.cn/jnews/765340.htm
- http://m.wap.ghtkgg.cn/jnews/98355.htm
- http://m.wap.ghtkgg.cn/jnews/671203.htm
- http://m.wap.ghtkgg.cn/jnews/556593.htm
- http://m.wap.ghtkgg.cn/jnews/7341.htm
- http://m.wap.ghtkgg.cn/jnews/08049.htm
- http://m.wap.ghtkgg.cn/jnews/02400.htm
- http://m.wap.ghtkgg.cn/jnews/55862.htm
- http://m.wap.ghtkgg.cn/jnews/4303.htm
- http://m.wap.ghtkgg.cn/jnews/27681.htm
- http://m.wap.ghtkgg.cn/jnews/370729.htm
- http://m.wap.ghtkgg.cn/jnews/85423.htm
- http://m.wap.ghtkgg.cn/jnews/7015550.htm
- http://m.wap.ghtkgg.cn/jnews/9913.htm
- http://m.wap.ghtkgg.cn/jnews/209683.htm
- http://m.wap.ghtkgg.cn/jnews/0749597.htm
- http://m.wap.ghtkgg.cn/jnews/13486.htm
- http://m.wap.ghtkgg.cn/jnews/579187.htm
- http://m.wap.ghtkgg.cn/jnews/10967.htm
- http://m.wap.ghtkgg.cn/jnews/9081.htm
- http://m.wap.ghtkgg.cn/jnews/7161.htm
- http://m.wap.ghtkgg.cn/jnews/28518.htm
- http://m.wap.ghtkgg.cn/jnews/60887.htm
- http://m.wap.ghtkgg.cn/jnews/6599546.htm
- http://m.wap.ghtkgg.cn/jnews/0868.htm
- http://m.wap.ghtkgg.cn/jnews/77879.htm
- http://m.wap.ghtkgg.cn/jnews/557401.htm
- http://m.wap.ghtkgg.cn/jnews/546412.htm
- http://m.wap.ghtkgg.cn/jnews/9684406.htm
- http://m.wap.ghtkgg.cn/jnews/36495.htm
- http://m.wap.ghtkgg.cn/jnews/046725.htm
- http://m.wap.ghtkgg.cn/jnews/7917199.htm
- http://m.wap.ghtkgg.cn/jnews/68785.htm
- http://m.wap.ghtkgg.cn/jnews/7712.htm
- http://m.wap.ghtkgg.cn/jnews/945315.htm
- http://m.wap.ghtkgg.cn/jnews/86113.htm
- http://m.wap.ghtkgg.cn/jnews/2072360.htm
- http://m.wap.ghtkgg.cn/jnews/5936815.htm
- http://m.wap.ghtkgg.cn/jnews/9969.htm
- http://m.wap.ghtkgg.cn/jnews/97927.htm
- http://m.wap.ghtkgg.cn/jnews/82579.htm
- http://m.wap.ghtkgg.cn/jnews/9765.htm
- http://m.wap.ghtkgg.cn/jnews/0255952.htm
- http://m.wap.ghtkgg.cn/jnews/483214.htm
- http://m.wap.ghtkgg.cn/jnews/00505.htm
- http://m.wap.ghtkgg.cn/jnews/510199.htm
- http://m.wap.ghtkgg.cn/jnews/3802592.htm
- http://m.wap.ghtkgg.cn/jnews/031698.htm
- http://m.wap.ghtkgg.cn/jnews/3481483.htm
- http://m.wap.ghtkgg.cn/jnews/09594.htm
- http://m.wap.ghtkgg.cn/jnews/870751.htm
- http://m.wap.ghtkgg.cn/jnews/1993459.htm
- http://m.wap.ghtkgg.cn/jnews/48471.htm
- http://m.wap.ghtkgg.cn/jnews/13012.htm
- http://m.wap.ghtkgg.cn/jnews/40438.htm
- http://m.wap.ghtkgg.cn/jnews/1015963.htm
- http://m.wap.ghtkgg.cn/jnews/4925371.htm
- http://m.wap.ghtkgg.cn/jnews/2535868.htm
- http://m.wap.ghtkgg.cn/jnews/945812.htm
- http://m.wap.ghtkgg.cn/jnews/4616290.htm
- http://m.wap.ghtkgg.cn/jnews/3737.htm
- http://m.wap.ghtkgg.cn/jnews/60783.htm
- http://m.wap.ghtkgg.cn/jnews/11304.htm
- http://m.wap.ghtkgg.cn/jnews/945148.htm
- http://m.wap.ghtkgg.cn/jnews/26623.htm
- http://m.wap.ghtkgg.cn/jnews/17288.htm
- http://m.wap.ghtkgg.cn/jnews/6812115.htm
- http://m.wap.ghtkgg.cn/jnews/86346.htm
- http://m.wap.ghtkgg.cn/jnews/87986.htm
- http://m.wap.ghtkgg.cn/jnews/872855.htm
- http://m.wap.ghtkgg.cn/jnews/3538463.htm
- http://m.wap.ghtkgg.cn/jnews/5792.htm
- http://m.wap.ghtkgg.cn/jnews/2565795.htm
- http://m.wap.ghtkgg.cn/jnews/0808726.htm

## 项目结构

```
weblink-navigator/
├── src/                           # 源代码主目录
│   ├── core/                      # 核心逻辑模块
│   │   ├── indexer.js             # 索引生成器，负责解析列表并构建HTML/JSON
│   │   ├── importer.js            # 批量导入与格式转换（CSV/JSON/TXT）
│   │   ├── dedupe.js              # 基于路径与域名的去重引擎
│   │   └── validator.js           # URL格式校验与规范化工具
│   ├── health/                    # 健康检查模块
│   │   ├── checker.js             # HTTP状态检测主逻辑（支持HEAD/GET）
│   │   ├── reporter.js            # 异常报告生成器（输出JSON/CSV）
│   │   └── scheduler.js           # 定时任务调度器（基于cron表达式）
│   ├── metadata/                  # 元数据处理
│   │   ├── fields.js              # 扩展字段定义（标签/摘要/状态码等）
│   │   ├── parser.js              # 从附属配置文件中读取元数据
│   │   └── aggregator.js          # 按标签、批次、状态聚合统计
│   ├── export/                    # 导出模块
│   │   ├── markdown.js            # 导出为Markdown列表格式
│   │   ├── json.js                # 导出为结构化JSON数组
│   │   └── plain.js               # 导出为纯文本每行一个URL
│   └── cli/                       # 命令行入口
│       ├── commands.js            # 注册所有CLI子命令（build/import/check/export）
│       └── runner.js              # 命令路由与参数解析
├── data/                          # 数据存储目录
│   ├── batches/                   # 按批次存放原始列表
│   │   └── 163/                   # 第163批次（当前默认种子数据）
│   │       └── links.txt          # 纯文本URL列表，每行一条
│   ├── metadata/                  # 元数据附加文件（YAML/JSON）
│   │   └── 163.yaml               # 对应批次的标签、摘要、备注
│   ├── indices/                   # 生成的索引文件
│   │   ├── index.html             # 静态站点入口页面
│   │   └── index.json             # 结构化数据映射
│   └── logs/                      # 运行日志与健康检查报告
│       ├── access.log             # 访问记录（可选）
│       └── health-report.json     # 最新健康检查结果
├── docs/                          # 文档目录（用户手册、管理员指南、开发者文档）
│   ├── user-guide.md
│   ├── admin-guide.md
│   ├── developer-guide.md
│   └── troubleshooting.md
├── scripts/                       # 辅助运维脚本
│   ├── setup.sh                   # 环境初始化脚本（检查依赖、创建目录）
│   ├── daily-check.sh             # 每日健康检查cron任务
│   └── archive.sh                 # 批次归档与清理脚本
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 单元测试（核心模块覆盖率 > 80%）
│   └── integration/               # 集成测试（端到端构建与导入）
├── package.json                   # npm项目配置（依赖、脚本、版本）
├── .gitignore                     # Git忽略规则（node_modules、logs、dist）
└── README.md                      # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻仓库并创建功能分支。从主分支的latest标签切出新分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。提交前请确保本地通过全部单元测试与集成测试。

2. 新增资源批次时遵循数据格式规范。在 `data/batches/` 下按批次号创建目录，放入 `links.txt` 文件，每行一条URL。如需附加元数据，在 `data/metadata/` 下创建同名YAML文件，包含标签、摘要、备注等字段。

3. 提交代码前运行完整构建流程。执行 `npm run build` 确保索引生成无报错，执行 `npm run test` 验证所有测试用例通过。提交信息采用约定式提交格式（feat/fix/docs/style/refactor/test/chore）。

4. 提交Pull Request时附带详细说明。描述本次变更的目的、影响范围、测试覆盖情况，并关联相关Issue编号。PR目标分支为 `main`，合并前需要至少一位维护者审阅批准。

5. 文档更新随代码同步。任何新增功能或修改行为必须在 `docs/` 对应手册中补充说明，确保用户手册、管理员指南与开发者文档始终保持与当前主分支代码一致。

## 常见问题

问：导入的URL列表中有重复条目，系统如何处理？
系统在导入过程中会自动执行基于域名与路径的去重检测。当检测到重复时，默认保留第一条出现记录，后续重复条目将被标记为"已跳过"并记录在导入日志中。用户可通过修改配置将去重策略切换为"覆盖"或"保留最新"。

问：健康检查模块如何配置超时与重试？
健康检查模块的配置文件位于 `src/health/config.js`，用户可修改 `TIMEOUT_MS`（默认3000毫秒）和 `RETRY_COUNT`（默认2次）参数。若需调整检查频率，可编辑 `scheduler.js` 中的cron表达式，默认每日凌晨2:00执行全量检查。

问：静态索引页面能否部署到CDN或对象存储？
可以。执行 `npm run build` 后生成的 `dist/` 目录完全由静态文件组成（HTML、JSON、CSS、JavaScript），可直接上传至任何支持静态托管的对象存储服务（如AWS S3、阿里云OSS、腾讯云COS）或CDN。所有链接资源均以相对路径引用，无需额外配置服务端环境。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
