# NNews External Resource Aggregator

NNews External Resource Aggregator 是一个面向技术信息检索与新闻聚合场景的开源外链汇总工具。该项目定位于对分散在互联网各处的非结构化新闻页面、公告页面与技术文档入口进行集中化收录与分类管理，帮助开发者、技术研究人员与信息分析人员快速定位特定编号下的原始信息源。

该项目不提供内容抓取与存储功能，不涉及数据库持久化，仅以轻量级目录结构对原始 URL 进行组织与标注。目标用户包括需要批量管理外链资源的运维工程师、需要构建自定义新闻聚合流的自动化脚本开发者，以及需要对外链可用性进行定期巡检的质量保障人员。通过本项目的目录规范与命名约定，用户能够将大量散落的 URL 转化为可维护、可版本控制、可协作的文本资产。

## 功能概览

**基于编号的条目索引** 每个外部资源以数字编号作为唯一标识，与原始 URL 中的文件名前缀保持一一对应关系，便于快速检索与引用。

**分类目录分层存储** 按照资源主题、来源域名或日期区间对 URL 进行逻辑分组，支持用户根据自身业务需求调整目录结构而不影响核心引用链。

**纯文本清单导出** 所有收录的 URL 以纯文本列表形式集中管理，无需依赖数据库或第三方服务即可完成批量导出与导入操作。

**URL 可用性检查脚本** 项目附带的简易 Shell 脚本支持对清单中的每个 URL 执行 HTTP 状态码检查，并生成可用性报告。

**外链变更追踪** 通过 Git 版本控制对 URL 列表的增删改操作进行记录，每次变更均可追溯至具体提交信息与变更原因。

**Markdown 文档自动生成** 基于预定义模板自动生成格式统一的资源导航文档，减少手动编写文档的重复劳动。

**多终端访问适配** 资源列表中的 URL 本身已针对移动端访问进行优化，项目本身不额外增加访问门槛，保持原始链接的访问特性。

## 应用场景

**技术新闻日常监控** 技术团队可利用本项目的分类目录，将每日需要关注的技术公告、安全更新与版本发布链接集中存放，并通过定时脚本对链接有效性进行每日校验，及时发现失效来源。

**开源项目外部依赖溯源** 当开源项目中引用了第三方文档或公告页面时，可将这些外部链接统一收录至本项目的资源清单中，便于后续审计外部依赖的变更情况或迁移影响范围。

**信息聚合流构建** 数据分析师或爬虫开发者可将本项目的 URL 列表作为爬虫种子队列的输入源，通过解析编号规则实现批量请求的自动化调度，避免手动收集种子链接的重复工作。

**离线文档资源整理** 对于需要将大量在线文档归档至内部知识库的团队，可利用本项目的目录结构先行整理 URL 清单，再配合离线下载工具完成批量归档，整个过程保持清单与归档文件的对应关系。

## 快速开始

以下步骤演示如何克隆本仓库、安装基础依赖并运行可用性检查脚本。

```bash
git clone https://github.com/example/nnews-aggregator.git
cd nnews-aggregator

# 安装依赖（仅需 curl 与 grep，多数系统预装）
sudo apt-get update && sudo apt-get install -y curl grep coreutils

# 运行可用性检查脚本（示例脚本，检查资源列表前 10 条）
./scripts/check_urls.sh resources/urls.txt 10
```

若系统中未预装 curl 或 grep，请参考安装要求章节的依赖表格进行补充安装。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| curl | 7.68.0 及以上 | 用于执行 HTTP 请求，检查 URL 可用性状态 |
| grep | 3.4 及以上 | 用于解析脚本输出结果与状态码过滤 |
| bash | 5.0 及以上 | 运行项目附带的所有 Shell 脚本 |
| git | 2.25.0 及以上 | 克隆仓库以及进行版本变更追踪 |
| coreutils | 8.30 及以上 | 提供 sort、uniq、wc 等基础命令行工具 |
| sed | 4.7 及以上 | 用于文本替换与格式清洗操作 |
| awk | 5.0.0 及以上 | 用于对检查结果进行统计汇总 |
| wc | 8.30 及以上 | 用于计数与行数统计 |
| cat | 8.30 及以上 | 用于文件内容查看与合并 |
| echo | 内置 | 用于脚本输出信息提示 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/usage.md | 如何新增 URL、如何更新分类、如何运行检查脚本 |
| 维护指南 | docs/maintenance.md | 如何处理失效链接、如何提交变更、如何与上游同步 |
| 结构说明 | docs/structure.md | 目录树各部分的含义、编号规则的详细解释 |
| 常见工作流 | docs/workflows.md | 批量导入、批量导出、批量替换域名的具体操作步骤 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/88476.htm
- http://m.3g.ghtkgg.cn/nnews/98163.htm
- http://m.3g.ghtkgg.cn/nnews/5218041.htm
- http://m.3g.ghtkgg.cn/nnews/8617.htm
- http://m.3g.ghtkgg.cn/nnews/384949.htm
- http://m.3g.ghtkgg.cn/nnews/2184.htm
- http://m.3g.ghtkgg.cn/nnews/22317.htm
- http://m.3g.ghtkgg.cn/nnews/50311.htm
- http://m.3g.ghtkgg.cn/nnews/8442.htm
- http://m.3g.ghtkgg.cn/nnews/97330.htm
- http://m.3g.ghtkgg.cn/nnews/9078.htm
- http://m.3g.ghtkgg.cn/nnews/642979.htm
- http://m.3g.ghtkgg.cn/nnews/8059.htm
- http://m.3g.ghtkgg.cn/nnews/336496.htm
- http://m.3g.ghtkgg.cn/nnews/068250.htm
- http://m.3g.ghtkgg.cn/nnews/808986.htm
- http://m.3g.ghtkgg.cn/nnews/49564.htm
- http://m.3g.ghtkgg.cn/nnews/4623301.htm
- http://m.3g.ghtkgg.cn/nnews/3174.htm
- http://m.3g.ghtkgg.cn/nnews/2930432.htm
- http://m.3g.ghtkgg.cn/nnews/58904.htm
- http://m.3g.ghtkgg.cn/nnews/302004.htm
- http://m.3g.ghtkgg.cn/nnews/674165.htm
- http://m.3g.ghtkgg.cn/nnews/7591.htm
- http://m.3g.ghtkgg.cn/nnews/4179.htm
- http://m.3g.ghtkgg.cn/nnews/83690.htm
- http://m.3g.ghtkgg.cn/nnews/2585.htm
- http://m.3g.ghtkgg.cn/nnews/7457153.htm
- http://m.3g.ghtkgg.cn/nnews/3361.htm
- http://m.3g.ghtkgg.cn/nnews/0218612.htm
- http://m.3g.ghtkgg.cn/nnews/0408355.htm
- http://m.3g.ghtkgg.cn/nnews/115714.htm
- http://m.3g.ghtkgg.cn/nnews/253423.htm
- http://m.3g.ghtkgg.cn/nnews/6748.htm
- http://m.3g.ghtkgg.cn/nnews/906058.htm
- http://m.3g.ghtkgg.cn/nnews/1758.htm
- http://m.3g.ghtkgg.cn/nnews/1303.htm
- http://m.3g.ghtkgg.cn/nnews/6724.htm
- http://m.3g.ghtkgg.cn/nnews/2678.htm
- http://m.3g.ghtkgg.cn/nnews/2501959.htm
- http://m.3g.ghtkgg.cn/nnews/167404.htm
- http://m.3g.ghtkgg.cn/nnews/93614.htm
- http://m.3g.ghtkgg.cn/nnews/6041770.htm
- http://m.3g.ghtkgg.cn/nnews/160601.htm
- http://m.3g.ghtkgg.cn/nnews/72154.htm
- http://m.3g.ghtkgg.cn/nnews/770172.htm
- http://m.3g.ghtkgg.cn/nnews/765195.htm
- http://m.3g.ghtkgg.cn/nnews/01686.htm
- http://m.3g.ghtkgg.cn/nnews/3885133.htm
- http://m.3g.ghtkgg.cn/nnews/79893.htm
- http://m.3g.ghtkgg.cn/nnews/7041411.htm
- http://m.3g.ghtkgg.cn/nnews/5940113.htm
- http://m.3g.ghtkgg.cn/nnews/0525136.htm
- http://m.3g.ghtkgg.cn/nnews/392383.htm
- http://m.3g.ghtkgg.cn/nnews/4616194.htm
- http://m.3g.ghtkgg.cn/nnews/9376.htm
- http://m.3g.ghtkgg.cn/nnews/30006.htm
- http://m.3g.ghtkgg.cn/nnews/8107.htm
- http://m.3g.ghtkgg.cn/nnews/839439.htm
- http://m.3g.ghtkgg.cn/nnews/853626.htm
- http://m.3g.ghtkgg.cn/nnews/096939.htm
- http://m.3g.ghtkgg.cn/nnews/945011.htm
- http://m.3g.ghtkgg.cn/nnews/37216.htm
- http://m.3g.ghtkgg.cn/nnews/54498.htm
- http://m.3g.ghtkgg.cn/nnews/91390.htm
- http://m.3g.ghtkgg.cn/nnews/3391.htm
- http://m.3g.ghtkgg.cn/nnews/8053.htm
- http://m.3g.ghtkgg.cn/nnews/668254.htm
- http://m.3g.ghtkgg.cn/nnews/30038.htm
- http://m.3g.ghtkgg.cn/nnews/09883.htm
- http://m.3g.ghtkgg.cn/nnews/62235.htm
- http://m.3g.ghtkgg.cn/nnews/413823.htm
- http://m.3g.ghtkgg.cn/nnews/5718.htm
- http://m.3g.ghtkgg.cn/nnews/56208.htm
- http://m.3g.ghtkgg.cn/nnews/6630.htm
- http://m.3g.ghtkgg.cn/nnews/260873.htm
- http://m.3g.ghtkgg.cn/nnews/5580794.htm
- http://m.3g.ghtkgg.cn/nnews/6982.htm
- http://m.3g.ghtkgg.cn/nnews/6817.htm
- http://m.3g.ghtkgg.cn/nnews/1671.htm
- http://m.3g.ghtkgg.cn/nnews/959349.htm
- http://m.3g.ghtkgg.cn/nnews/051387.htm
- http://m.3g.ghtkgg.cn/nnews/840130.htm
- http://m.3g.ghtkgg.cn/nnews/15851.htm
- http://m.3g.ghtkgg.cn/nnews/640748.htm
- http://m.3g.ghtkgg.cn/nnews/17864.htm
- http://m.3g.ghtkgg.cn/nnews/44346.htm
- http://m.3g.ghtkgg.cn/nnews/6814.htm
- http://m.3g.ghtkgg.cn/nnews/3988922.htm
- http://m.3g.ghtkgg.cn/nnews/0466.htm
- http://m.3g.ghtkgg.cn/nnews/2839.htm
- http://m.3g.ghtkgg.cn/nnews/106048.htm
- http://m.3g.ghtkgg.cn/nnews/12961.htm
- http://m.3g.ghtkgg.cn/nnews/5527.htm
- http://m.3g.ghtkgg.cn/nnews/1658045.htm
- http://m.3g.ghtkgg.cn/nnews/3761.htm
- http://m.3g.ghtkgg.cn/nnews/0412052.htm
- http://m.3g.ghtkgg.cn/nnews/7660726.htm
- http://m.3g.ghtkgg.cn/nnews/6143798.htm
- http://m.3g.ghtkgg.cn/nnews/9937684.htm
- http://m.3g.ghtkgg.cn/nnews/2989.htm
- http://m.3g.ghtkgg.cn/nnews/729847.htm
- http://m.3g.ghtkgg.cn/nnews/2748.htm
- http://m.3g.ghtkgg.cn/nnews/3954.htm
- http://m.3g.ghtkgg.cn/nnews/1883700.htm
- http://m.3g.ghtkgg.cn/nnews/8105701.htm
- http://m.3g.ghtkgg.cn/nnews/9966.htm
- http://m.3g.ghtkgg.cn/nnews/236338.htm
- http://m.3g.ghtkgg.cn/nnews/851609.htm
- http://m.3g.ghtkgg.cn/nnews/2345067.htm
- http://m.3g.ghtkgg.cn/nnews/0091515.htm
- http://m.3g.ghtkgg.cn/nnews/9044591.htm
- http://m.3g.ghtkgg.cn/nnews/86441.htm
- http://m.3g.ghtkgg.cn/nnews/85986.htm
- http://m.3g.ghtkgg.cn/nnews/604702.htm
- http://m.3g.ghtkgg.cn/nnews/85182.htm
- http://m.3g.ghtkgg.cn/nnews/546440.htm
- http://m.3g.ghtkgg.cn/nnews/6274373.htm
- http://m.3g.ghtkgg.cn/nnews/0963.htm
- http://m.3g.ghtkgg.cn/nnews/3118666.htm
- http://m.3g.ghtkgg.cn/nnews/91151.htm
- http://m.3g.ghtkgg.cn/nnews/772539.htm
- http://m.3g.ghtkgg.cn/nnews/90043.htm
- http://m.3g.ghtkgg.cn/nnews/62027.htm
- http://m.3g.ghtkgg.cn/nnews/0386427.htm
- http://m.3g.ghtkgg.cn/nnews/840650.htm
- http://m.3g.ghtkgg.cn/nnews/625017.htm
- http://m.3g.ghtkgg.cn/nnews/5625167.htm
- http://m.3g.ghtkgg.cn/nnews/2075.htm
- http://m.3g.ghtkgg.cn/nnews/22532.htm
- http://m.3g.ghtkgg.cn/nnews/8472.htm
- http://m.3g.ghtkgg.cn/nnews/2563755.htm
- http://m.3g.ghtkgg.cn/nnews/0205.htm
- http://m.3g.ghtkgg.cn/nnews/9442635.htm
- http://m.3g.ghtkgg.cn/nnews/8630933.htm
- http://m.3g.ghtkgg.cn/nnews/405477.htm
- http://m.3g.ghtkgg.cn/nnews/075548.htm
- http://m.3g.ghtkgg.cn/nnews/3484.htm
- http://m.3g.ghtkgg.cn/nnews/430578.htm
- http://m.3g.ghtkgg.cn/nnews/73809.htm
- http://m.3g.ghtkgg.cn/nnews/1587872.htm
- http://m.3g.ghtkgg.cn/nnews/9347234.htm
- http://m.3g.ghtkgg.cn/nnews/5765477.htm
- http://m.3g.ghtkgg.cn/nnews/7437093.htm
- http://m.3g.ghtkgg.cn/nnews/7269564.htm
- http://m.3g.ghtkgg.cn/nnews/290220.htm
- http://m.3g.ghtkgg.cn/nnews/2772.htm
- http://m.3g.ghtkgg.cn/nnews/558430.htm
- http://m.3g.ghtkgg.cn/nnews/073353.htm
- http://m.3g.ghtkgg.cn/nnews/5311996.htm
- http://m.3g.ghtkgg.cn/nnews/5033416.htm
- http://m.3g.ghtkgg.cn/nnews/193474.htm
- http://m.3g.ghtkgg.cn/nnews/0310437.htm
- http://m.3g.ghtkgg.cn/nnews/71540.htm
- http://m.3g.ghtkgg.cn/nnews/6509773.htm
- http://m.3g.ghtkgg.cn/nnews/29358.htm
- http://m.3g.ghtkgg.cn/nnews/33851.htm
- http://m.3g.ghtkgg.cn/nnews/676228.htm
- http://m.3g.ghtkgg.cn/nnews/237270.htm
- http://m.3g.ghtkgg.cn/nnews/8277980.htm
- http://m.3g.ghtkgg.cn/nnews/10900.htm
- http://m.3g.ghtkgg.cn/nnews/6269070.htm
- http://m.3g.ghtkgg.cn/nnews/01800.htm
- http://m.3g.ghtkgg.cn/nnews/20745.htm
- http://m.3g.ghtkgg.cn/nnews/6858201.htm
- http://m.3g.ghtkgg.cn/nnews/82512.htm
- http://m.3g.ghtkgg.cn/nnews/41748.htm
- http://m.3g.ghtkgg.cn/nnews/2142465.htm
- http://m.3g.ghtkgg.cn/nnews/6764.htm
- http://m.3g.ghtkgg.cn/nnews/642212.htm
- http://m.3g.ghtkgg.cn/nnews/1309470.htm
- http://m.3g.ghtkgg.cn/nnews/652482.htm
- http://m.3g.ghtkgg.cn/nnews/1279948.htm
- http://m.3g.ghtkgg.cn/nnews/55720.htm
- http://m.3g.ghtkgg.cn/nnews/9181.htm
- http://m.3g.ghtkgg.cn/nnews/260825.htm
- http://m.3g.ghtkgg.cn/nnews/950519.htm
- http://m.3g.ghtkgg.cn/nnews/618676.htm
- http://m.3g.ghtkgg.cn/nnews/07329.htm
- http://m.3g.ghtkgg.cn/nnews/809738.htm
- http://m.3g.ghtkgg.cn/nnews/837245.htm
- http://m.3g.ghtkgg.cn/nnews/5781.htm
- http://m.3g.ghtkgg.cn/nnews/0792081.htm
- http://m.3g.ghtkgg.cn/nnews/06565.htm
- http://m.3g.ghtkgg.cn/nnews/40227.htm
- http://m.3g.ghtkgg.cn/nnews/6701.htm
- http://m.3g.ghtkgg.cn/nnews/832930.htm
- http://m.3g.ghtkgg.cn/nnews/0040556.htm
- http://m.3g.ghtkgg.cn/nnews/9517.htm
- http://m.3g.ghtkgg.cn/nnews/9233.htm
- http://m.3g.ghtkgg.cn/nnews/4535798.htm
- http://m.3g.ghtkgg.cn/nnews/251341.htm
- http://m.3g.ghtkgg.cn/nnews/69834.htm
- http://m.3g.ghtkgg.cn/nnews/63123.htm
- http://m.3g.ghtkgg.cn/nnews/596198.htm
- http://m.3g.ghtkgg.cn/nnews/4681468.htm
- http://m.3g.ghtkgg.cn/nnews/479112.htm
- http://m.3g.ghtkgg.cn/nnews/3535.htm
- http://m.3g.ghtkgg.cn/nnews/460936.htm
- http://m.3g.ghtkgg.cn/nnews/8707396.htm
- http://m.3g.ghtkgg.cn/nnews/3312944.htm
- http://m.3g.ghtkgg.cn/nnews/1103816.htm
- http://m.3g.ghtkgg.cn/nnews/198246.htm
- http://m.3g.ghtkgg.cn/nnews/233627.htm
- http://m.3g.ghtkgg.cn/nnews/5174778.htm
- http://m.3g.ghtkgg.cn/nnews/27509.htm
- http://m.3g.ghtkgg.cn/nnews/2916.htm
- http://m.3g.ghtkgg.cn/nnews/39116.htm
- http://m.3g.ghtkgg.cn/nnews/298168.htm
- http://m.3g.ghtkgg.cn/nnews/2170083.htm
- http://m.3g.ghtkgg.cn/nnews/92613.htm
- http://m.3g.ghtkgg.cn/nnews/99624.htm
- http://m.3g.ghtkgg.cn/nnews/1335042.htm
- http://m.3g.ghtkgg.cn/nnews/0454268.htm
- http://m.3g.ghtkgg.cn/nnews/2708931.htm
- http://m.3g.ghtkgg.cn/nnews/3282342.htm
- http://m.3g.ghtkgg.cn/nnews/913483.htm
- http://m.3g.ghtkgg.cn/nnews/2470510.htm
- http://m.3g.ghtkgg.cn/nnews/574293.htm
- http://m.3g.ghtkgg.cn/nnews/067159.htm
- http://m.3g.ghtkgg.cn/nnews/8380.htm
- http://m.3g.ghtkgg.cn/nnews/8266.htm
- http://m.3g.ghtkgg.cn/nnews/04086.htm
- http://m.3g.ghtkgg.cn/nnews/0115668.htm
- http://m.3g.ghtkgg.cn/nnews/4364.htm
- http://m.3g.ghtkgg.cn/nnews/3841.htm
- http://m.3g.ghtkgg.cn/nnews/165168.htm
- http://m.3g.ghtkgg.cn/nnews/1605676.htm
- http://m.3g.ghtkgg.cn/nnews/02724.htm
- http://m.3g.ghtkgg.cn/nnews/45730.htm
- http://m.3g.ghtkgg.cn/nnews/7723182.htm
- http://m.3g.ghtkgg.cn/nnews/2696226.htm
- http://m.3g.ghtkgg.cn/nnews/13964.htm
- http://m.3g.ghtkgg.cn/nnews/279486.htm
- http://m.3g.ghtkgg.cn/nnews/34984.htm
- http://m.3g.ghtkgg.cn/nnews/6019.htm
- http://m.3g.ghtkgg.cn/nnews/0125.htm
- http://m.3g.ghtkgg.cn/nnews/791562.htm
- http://m.3g.ghtkgg.cn/nnews/0107.htm
- http://m.3g.ghtkgg.cn/nnews/67351.htm
- http://m.3g.ghtkgg.cn/nnews/307821.htm
- http://m.3g.ghtkgg.cn/nnews/02679.htm
- http://m.3g.ghtkgg.cn/nnews/6499313.htm
- http://m.3g.ghtkgg.cn/nnews/9148.htm
- http://m.3g.ghtkgg.cn/nnews/7164.htm
- http://m.3g.ghtkgg.cn/nnews/8985460.htm
- http://m.3g.ghtkgg.cn/nnews/9987.htm
- http://m.3g.ghtkgg.cn/nnews/4513.htm
- http://m.3g.ghtkgg.cn/nnews/2528378.htm
- http://m.3g.ghtkgg.cn/nnews/688003.htm
- http://m.3g.ghtkgg.cn/nnews/886652.htm
- http://m.3g.ghtkgg.cn/nnews/5619.htm
- http://m.3g.ghtkgg.cn/nnews/1457651.htm
- http://m.3g.ghtkgg.cn/nnews/067180.htm
- http://m.3g.ghtkgg.cn/nnews/3838164.htm
- http://m.3g.ghtkgg.cn/nnews/22965.htm
- http://m.3g.ghtkgg.cn/nnews/8409.htm
- http://m.3g.ghtkgg.cn/nnews/47910.htm
- http://m.3g.ghtkgg.cn/nnews/0129.htm
- http://m.3g.ghtkgg.cn/nnews/7304.htm
- http://m.3g.ghtkgg.cn/nnews/1413.htm
- http://m.3g.ghtkgg.cn/nnews/447266.htm
- http://m.3g.ghtkgg.cn/nnews/3537522.htm
- http://m.3g.ghtkgg.cn/nnews/6059580.htm
- http://m.3g.ghtkgg.cn/nnews/5909568.htm
- http://m.3g.ghtkgg.cn/nnews/1874.htm
- http://m.3g.ghtkgg.cn/nnews/7029.htm
- http://m.3g.ghtkgg.cn/nnews/630542.htm
- http://m.3g.ghtkgg.cn/nnews/775279.htm
- http://m.3g.ghtkgg.cn/nnews/4047914.htm
- http://m.3g.ghtkgg.cn/nnews/984768.htm
- http://m.3g.ghtkgg.cn/nnews/1470538.htm
- http://m.3g.ghtkgg.cn/nnews/1973.htm
- http://m.3g.ghtkgg.cn/nnews/614448.htm
- http://m.3g.ghtkgg.cn/nnews/686265.htm
- http://m.3g.ghtkgg.cn/nnews/5622.htm
- http://m.3g.ghtkgg.cn/nnews/2780.htm
- http://m.3g.ghtkgg.cn/nnews/4233349.htm
- http://m.3g.ghtkgg.cn/nnews/010124.htm
- http://m.3g.ghtkgg.cn/nnews/36304.htm
- http://m.3g.ghtkgg.cn/nnews/620772.htm
- http://m.3g.ghtkgg.cn/nnews/2739386.htm
- http://m.3g.ghtkgg.cn/nnews/2363.htm
- http://m.3g.ghtkgg.cn/nnews/81065.htm
- http://m.3g.ghtkgg.cn/nnews/936303.htm
- http://m.3g.ghtkgg.cn/nnews/6281.htm
- http://m.3g.ghtkgg.cn/nnews/9276.htm
- http://m.3g.ghtkgg.cn/nnews/1428.htm
- http://m.3g.ghtkgg.cn/nnews/0852415.htm
- http://m.3g.ghtkgg.cn/nnews/9225151.htm
- http://m.3g.ghtkgg.cn/nnews/85239.htm
- http://m.3g.ghtkgg.cn/nnews/6173.htm
- http://m.3g.ghtkgg.cn/nnews/67875.htm
- http://m.3g.ghtkgg.cn/nnews/6985.htm
- http://m.3g.ghtkgg.cn/nnews/9163913.htm
- http://m.3g.ghtkgg.cn/nnews/4947.htm
- http://m.3g.ghtkgg.cn/nnews/6706892.htm
- http://m.3g.ghtkgg.cn/nnews/9992.htm
- http://m.3g.ghtkgg.cn/nnews/74487.htm
- http://m.3g.ghtkgg.cn/nnews/9882.htm

## 项目结构

```
nnews-aggregator/
├── resources/                         # 资源清单主目录
│   ├── urls.txt                       # 完整 URL 列表，每行一条
│   ├── categories/                    # 分类子目录，按主题拆分
│   │   ├── tech_news.txt              # 技术新闻类链接
│   │   ├── announcements.txt          # 公告类链接
│   │   └── general.txt                # 通用类链接
│   └── meta/                          # 元信息目录
│       ├── changelog.md               # 链接变更记录
│       └── last_checked.txt           # 最近一次可用性检查时间
├── scripts/                           # 工具脚本目录
│   ├── check_urls.sh                  # 批量检查 URL 可用性
│   ├── sort_urls.sh                   # 按编号或域名排序
│   ├── dedup_urls.sh                  # 去重脚本
│   └── export_markdown.py             # 从 urls.txt 生成 Markdown 表格
├── docs/                              # 文档目录
│   ├── usage.md                       # 用户使用手册
│   ├── maintenance.md                 # 维护指南
│   ├── structure.md                   # 结构说明
│   └── workflows.md                   # 常见工作流
├── tests/                             # 测试目录
│   ├── test_check.sh                  # 测试检查脚本功能
│   └── fixtures/                      # 测试固定数据
│       └── sample_urls.txt            # 样例链接用于测试
├── .gitignore                         # Git 忽略规则
├── LICENSE                            # MIT 许可证文件
└── README.md                          # 项目入口文档（本文件）
```

## 贡献指南

**克隆仓库并创建特性分支** 从主分支签出新的特性分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式，避免直接在主分支上操作。

**新增或修改 URL 条目** 在 resources/urls.txt 中追加新链接或修改已有链接，同时更新 resources/meta/changelog.md 记录本次变更的原因与日期，保持变更历史清晰可查。

**运行本地检查脚本** 在提交前执行 scripts/check_urls.sh 对新增或修改的链接进行可用性验证，确保至少 90% 以上的链接返回 2xx 或 3xx 状态码，避免引入大量失效链接。

**提交 Pull Request 并描述变更** 推送分支至远程仓库后，创建 Pull Request 并在描述中注明本次变更涉及的具体编号范围、变更类型（新增/删除/修改）以及是否影响现有分类结构。

**等待代码审查与合并** 项目维护者将在 3 个工作日内进行审查，必要时会要求补充说明或调整链接格式，通过后即合并至主分支并自动更新文档。

## 常见问题

**Q：资源列表中的 URL 如果失效了怎么办？**

项目本身不保证外部链接的永久有效性。建议用户定期运行 scripts/check_urls.sh 脚本获取可用性报告，对于返回 4xx 或 5xx 状态的链接，可在资源清单中标注为失效并记录发现时间，或提交 Pull Request 从列表中移除该条目并在 changelog 中说明。

**Q：能否一次性导入大量自定义 URL？**

可以。用户可直接编辑 resources/urls.txt 文件，按每行一个 URL 的格式追加内容。追加后建议运行 scripts/dedup_urls.sh 进行去重，并运行 scripts/sort_urls.sh 按字母顺序或编号顺序重排，以保持清单整洁。

**Q：本项目是否提供对 URL 内容的全文检索功能？**

不提供。本项目的定位为外链汇总与可用性管理，不涉及内容抓取、全文索引或关键词搜索。如需对链接指向的页面内容进行检索，建议配合外部搜索引擎或专用爬虫工具使用。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:03
