# WebIndex Core

WebIndex Core 是一个面向技术调研与信息聚合场景的轻量级外链资源索引工具。该项目定位于帮助开发者、技术研究员与内容运营人员快速构建可维护的 URL 资源清单，并提供结构化的文档导航与依赖管理能力。它不依赖复杂的数据库或前端框架，核心设计目标是以最简化的工程结构管理大批量外部链接，同时保证资源列表的可追溯性与可导出性。

该项目适用于需要定期整理、分类和共享外部技术文章、官方文档、社区讨论或数据源链接的团队或个人。WebIndex Core 不对链接内容做爬取或解析，仅提供本地化的索引管理、版本跟踪与快速启动环境，从而避免因外部资源变动导致的信息丢失问题。通过固定的目录结构和约定式配置，用户可以在一小时内完成从克隆到自定义资源库的完整部署。

---

## 功能概览

**零依赖索引引擎** 核心脚本仅依赖 Python 标准库与系统原生工具，无需额外安装第三方包即可完成资源列表的解析、校验与导出。

**批量 URL 导入与去重** 支持从纯文本文件、Markdown 表格或 CSV 中批量导入 URL，自动识别重复条目并生成去重报告。

**分层文档导航** 内置四级文档目录体系，支持按技术领域、资源类型、优先级与归档状态对链接进行多维分类。

**快照版本标记** 每次运行自动生成时间戳快照文件，记录当前资源列表的完整状态，便于回溯历史变更。

**格式规范检查** 提供独立的链接格式检查器，可检测 URL 是否包含非法字符、缺失协议头或存在大小写不一致问题。

**一键导出多种格式** 支持将索引结果导出为纯文本列表、JSON 结构体或 HTML 目录页，满足不同发布平台的需求。

**环境自检与修复** 启动时自动检测依赖项版本与文件权限，对缺失或损坏的目录结构执行自动修复。

---

## 应用场景

**技术文档归档** 技术团队在编写项目文档时，通常需要引用大量外部规范、教程或 API 参考。WebIndex Core 可以将这些分散的链接统一收录至项目仓库，避免因个人书签丢失导致引用失效。

**开源项目外链管理** 开源项目维护者需要在 README 或官网中展示生态相关资源。使用本工具可以结构化地管理这些外链，并在每次发布前自动校验每个链接的可达性（需配合健康检查脚本）。

**数据源登记与共享** 数据分析团队在开展研究时，往往需要从多个公开数据门户获取资源。WebIndex Core 提供的数据源登记表功能允许团队成员共同维护一份可追溯的数据源清单，并记录每个资源的最后访问时间。

**技术培训课程资料包** 技术培训讲师可以将课程涉及的所有阅读材料、在线工具与视频地址汇总为一份索引文件，学员通过克隆仓库即可获得完整的参考资料列表，无需逐个手动搜索。

**个人知识库外链备份** 个人知识管理爱好者可以将浏览器收藏夹导出为文本，再通过本工具的导入功能整理为分类索引，配合 Git 实现跨设备同步与版本控制。

---

## 快速开始

以下命令演示了从克隆仓库到启动索引服务的完整流程。所有操作均可在 Unix-like 系统及 Windows WSL 环境中直接执行。

```bash
git clone https://github.com/webindex/core.git webindex-core
cd webindex-core
cp config/example.env .env
./scripts/init.sh
python3 -m webindex.cli --scan ./data/raw_links.txt --output ./data/index.json
```

执行完毕后，索引结果将写入 `data/index.json` 文件，同时控制台会输出资源总数、有效链接数与分类统计摘要。

---

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心解释器，用于运行 CLI 与辅助脚本 |
| Git | 2.25 及以上 | 用于克隆仓库及后续版本管理 |
| Bash | 4.0 及以上 | 用于执行初始化脚本与环境检测 |
| GNU Coreutils | 8.30 及以上 | 提供 `sort`、`uniq`、`wc` 等基础文本处理命令 |
| curl | 7.68 及以上 | 可选组件，用于执行链接健康检查（默认关闭） |
| make | 3.81 及以上 | 用于运行预定义的构建任务（如导出 HTML） |
| grep | 3.4 及以上 | 用于日志过滤与格式校验的正则匹配 |
| sed | 4.7 及以上 | 用于文本替换与变量插值 |
| awk | 5.0.1 及以上 | 用于统计报表生成 |
| findutils | 4.7.0 及以上 | 用于递归查找索引文件 |

---

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何安装、配置并运行第一次索引扫描 |
| 格式规范 | docs/format-spec.md | URL 列表文件的编写格式、注释语法与字段定义 |
| 高级配置 | docs/advanced-config.md | 如何自定义分类规则、快照频率与导出模板 |
| 故障排除 | docs/troubleshooting.md | 常见错误码解释、日志分析方法与恢复步骤 |
| 贡献手册 | docs/contributing.md | 代码风格、提交规范与测试要求 |
| 版本日志 | CHANGELOG.md | 每个版本的更新摘要、破坏性变更与废弃功能 |

---

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/8027.htm
- http://m.blog.ghtkgg.cn/nnews/5078079.htm
- http://m.blog.ghtkgg.cn/nnews/8326950.htm
- http://m.blog.ghtkgg.cn/nnews/864821.htm
- http://m.blog.ghtkgg.cn/nnews/86914.htm
- http://m.blog.ghtkgg.cn/nnews/5601.htm
- http://m.blog.ghtkgg.cn/nnews/61240.htm
- http://m.blog.ghtkgg.cn/nnews/49503.htm
- http://m.blog.ghtkgg.cn/nnews/8555.htm
- http://m.blog.ghtkgg.cn/nnews/55471.htm
- http://m.blog.ghtkgg.cn/nnews/53047.htm
- http://m.blog.ghtkgg.cn/nnews/652679.htm
- http://m.blog.ghtkgg.cn/nnews/1923860.htm
- http://m.blog.ghtkgg.cn/nnews/0354.htm
- http://m.blog.ghtkgg.cn/nnews/230568.htm
- http://m.blog.ghtkgg.cn/nnews/16177.htm
- http://m.blog.ghtkgg.cn/nnews/633925.htm
- http://m.blog.ghtkgg.cn/nnews/328369.htm
- http://m.blog.ghtkgg.cn/nnews/51140.htm
- http://m.blog.ghtkgg.cn/nnews/584059.htm
- http://m.blog.ghtkgg.cn/nnews/0203.htm
- http://m.blog.ghtkgg.cn/nnews/903973.htm
- http://m.blog.ghtkgg.cn/nnews/88203.htm
- http://m.blog.ghtkgg.cn/nnews/64553.htm
- http://m.blog.ghtkgg.cn/nnews/8363909.htm
- http://m.blog.ghtkgg.cn/nnews/7683.htm
- http://m.blog.ghtkgg.cn/nnews/62016.htm
- http://m.blog.ghtkgg.cn/nnews/2661.htm
- http://m.blog.ghtkgg.cn/nnews/1480.htm
- http://m.blog.ghtkgg.cn/nnews/05308.htm
- http://m.blog.ghtkgg.cn/nnews/2761.htm
- http://m.blog.ghtkgg.cn/nnews/117580.htm
- http://m.blog.ghtkgg.cn/nnews/063420.htm
- http://m.blog.ghtkgg.cn/nnews/86640.htm
- http://m.blog.ghtkgg.cn/nnews/314635.htm
- http://m.blog.ghtkgg.cn/nnews/961609.htm
- http://m.blog.ghtkgg.cn/nnews/5265872.htm
- http://m.blog.ghtkgg.cn/nnews/5472.htm
- http://m.blog.ghtkgg.cn/nnews/811829.htm
- http://m.blog.ghtkgg.cn/nnews/9160793.htm
- http://m.blog.ghtkgg.cn/nnews/07698.htm
- http://m.blog.ghtkgg.cn/nnews/0510.htm
- http://m.blog.ghtkgg.cn/nnews/450249.htm
- http://m.blog.ghtkgg.cn/nnews/7828995.htm
- http://m.blog.ghtkgg.cn/nnews/8641153.htm
- http://m.blog.ghtkgg.cn/nnews/010904.htm
- http://m.blog.ghtkgg.cn/nnews/210493.htm
- http://m.blog.ghtkgg.cn/nnews/502295.htm
- http://m.blog.ghtkgg.cn/nnews/0769612.htm
- http://m.blog.ghtkgg.cn/nnews/9537.htm
- http://m.blog.ghtkgg.cn/nnews/543956.htm
- http://m.blog.ghtkgg.cn/nnews/383051.htm
- http://m.blog.ghtkgg.cn/nnews/37675.htm
- http://m.blog.ghtkgg.cn/nnews/830049.htm
- http://m.blog.ghtkgg.cn/nnews/231262.htm
- http://m.blog.ghtkgg.cn/nnews/5224705.htm
- http://m.blog.ghtkgg.cn/nnews/4435.htm
- http://m.blog.ghtkgg.cn/nnews/6290179.htm
- http://m.blog.ghtkgg.cn/nnews/12745.htm
- http://m.blog.ghtkgg.cn/nnews/2232648.htm
- http://m.blog.ghtkgg.cn/nnews/373354.htm
- http://m.blog.ghtkgg.cn/nnews/17734.htm
- http://m.blog.ghtkgg.cn/nnews/069973.htm
- http://m.blog.ghtkgg.cn/nnews/545286.htm
- http://m.blog.ghtkgg.cn/nnews/319774.htm
- http://m.blog.ghtkgg.cn/nnews/1947816.htm
- http://m.blog.ghtkgg.cn/nnews/5310640.htm
- http://m.blog.ghtkgg.cn/nnews/26037.htm
- http://m.blog.ghtkgg.cn/nnews/0563061.htm
- http://m.blog.ghtkgg.cn/nnews/5311000.htm
- http://m.blog.ghtkgg.cn/nnews/636522.htm
- http://m.blog.ghtkgg.cn/nnews/0121.htm
- http://m.blog.ghtkgg.cn/nnews/90026.htm
- http://m.blog.ghtkgg.cn/nnews/66856.htm
- http://m.blog.ghtkgg.cn/nnews/6470939.htm
- http://m.blog.ghtkgg.cn/nnews/435134.htm
- http://m.blog.ghtkgg.cn/nnews/56888.htm
- http://m.blog.ghtkgg.cn/nnews/2097.htm
- http://m.blog.ghtkgg.cn/nnews/417320.htm
- http://m.blog.ghtkgg.cn/nnews/0751.htm
- http://m.blog.ghtkgg.cn/nnews/03263.htm
- http://m.blog.ghtkgg.cn/nnews/1599.htm
- http://m.blog.ghtkgg.cn/nnews/40953.htm
- http://m.blog.ghtkgg.cn/nnews/71189.htm
- http://m.blog.ghtkgg.cn/nnews/5071.htm
- http://m.blog.ghtkgg.cn/nnews/61749.htm
- http://m.blog.ghtkgg.cn/nnews/169463.htm
- http://m.blog.ghtkgg.cn/nnews/918682.htm
- http://m.blog.ghtkgg.cn/nnews/3689.htm
- http://m.blog.ghtkgg.cn/nnews/939999.htm
- http://m.blog.ghtkgg.cn/nnews/4958192.htm
- http://m.blog.ghtkgg.cn/nnews/020673.htm
- http://m.blog.ghtkgg.cn/nnews/0567197.htm
- http://m.blog.ghtkgg.cn/nnews/2345576.htm
- http://m.blog.ghtkgg.cn/nnews/2724113.htm
- http://m.blog.ghtkgg.cn/nnews/0378890.htm
- http://m.blog.ghtkgg.cn/nnews/1358.htm
- http://m.blog.ghtkgg.cn/nnews/9347.htm
- http://m.blog.ghtkgg.cn/nnews/4646790.htm
- http://m.blog.ghtkgg.cn/nnews/5641800.htm
- http://m.blog.ghtkgg.cn/nnews/937911.htm
- http://m.blog.ghtkgg.cn/nnews/15206.htm
- http://m.blog.ghtkgg.cn/nnews/9949858.htm
- http://m.blog.ghtkgg.cn/nnews/384865.htm
- http://m.blog.ghtkgg.cn/nnews/7080.htm
- http://m.blog.ghtkgg.cn/nnews/6013.htm
- http://m.blog.ghtkgg.cn/nnews/8781780.htm
- http://m.blog.ghtkgg.cn/nnews/687066.htm
- http://m.blog.ghtkgg.cn/nnews/9450.htm
- http://m.blog.ghtkgg.cn/nnews/52214.htm
- http://m.blog.ghtkgg.cn/nnews/8007.htm
- http://m.blog.ghtkgg.cn/nnews/80251.htm
- http://m.blog.ghtkgg.cn/nnews/26660.htm
- http://m.blog.ghtkgg.cn/nnews/5669.htm
- http://m.blog.ghtkgg.cn/nnews/8494734.htm
- http://m.blog.ghtkgg.cn/nnews/1030632.htm
- http://m.blog.ghtkgg.cn/nnews/5251990.htm
- http://m.blog.ghtkgg.cn/nnews/3511648.htm
- http://m.blog.ghtkgg.cn/nnews/5136770.htm
- http://m.blog.ghtkgg.cn/nnews/3421.htm
- http://m.blog.ghtkgg.cn/nnews/1253099.htm
- http://m.blog.ghtkgg.cn/nnews/0532.htm
- http://m.blog.ghtkgg.cn/nnews/930220.htm
- http://m.blog.ghtkgg.cn/nnews/98034.htm
- http://m.blog.ghtkgg.cn/nnews/8921742.htm
- http://m.blog.ghtkgg.cn/nnews/5714.htm
- http://m.blog.ghtkgg.cn/nnews/5996735.htm
- http://m.blog.ghtkgg.cn/nnews/8712.htm
- http://m.blog.ghtkgg.cn/nnews/1398956.htm
- http://m.blog.ghtkgg.cn/nnews/1641.htm
- http://m.blog.ghtkgg.cn/nnews/1587266.htm
- http://m.blog.ghtkgg.cn/nnews/0987904.htm
- http://m.blog.ghtkgg.cn/nnews/4887.htm
- http://m.blog.ghtkgg.cn/nnews/14669.htm
- http://m.blog.ghtkgg.cn/nnews/530994.htm
- http://m.blog.ghtkgg.cn/nnews/64745.htm
- http://m.blog.ghtkgg.cn/nnews/73988.htm
- http://m.blog.ghtkgg.cn/nnews/5729422.htm
- http://m.blog.ghtkgg.cn/nnews/75811.htm
- http://m.blog.ghtkgg.cn/nnews/54537.htm
- http://m.blog.ghtkgg.cn/nnews/3101.htm
- http://m.blog.ghtkgg.cn/nnews/5587.htm
- http://m.blog.ghtkgg.cn/nnews/26167.htm
- http://m.blog.ghtkgg.cn/nnews/6586583.htm
- http://m.blog.ghtkgg.cn/nnews/693446.htm
- http://m.blog.ghtkgg.cn/nnews/2370.htm
- http://m.blog.ghtkgg.cn/nnews/1589.htm
- http://m.blog.ghtkgg.cn/nnews/333104.htm
- http://m.blog.ghtkgg.cn/nnews/27092.htm
- http://m.blog.ghtkgg.cn/nnews/0925.htm
- http://m.blog.ghtkgg.cn/nnews/264684.htm
- http://m.blog.ghtkgg.cn/nnews/43767.htm
- http://m.blog.ghtkgg.cn/nnews/15507.htm
- http://m.blog.ghtkgg.cn/nnews/535444.htm
- http://m.blog.ghtkgg.cn/nnews/278872.htm
- http://m.blog.ghtkgg.cn/nnews/3429.htm
- http://m.blog.ghtkgg.cn/nnews/12713.htm
- http://m.blog.ghtkgg.cn/nnews/4506395.htm
- http://m.blog.ghtkgg.cn/nnews/228027.htm
- http://m.blog.ghtkgg.cn/nnews/5029066.htm
- http://m.blog.ghtkgg.cn/nnews/79968.htm
- http://m.blog.ghtkgg.cn/nnews/56860.htm
- http://m.blog.ghtkgg.cn/nnews/67165.htm
- http://m.blog.ghtkgg.cn/nnews/149750.htm
- http://m.blog.ghtkgg.cn/nnews/47266.htm
- http://m.blog.ghtkgg.cn/nnews/527884.htm
- http://m.blog.ghtkgg.cn/nnews/69675.htm
- http://m.blog.ghtkgg.cn/nnews/420728.htm
- http://m.blog.ghtkgg.cn/nnews/0897.htm
- http://m.blog.ghtkgg.cn/nnews/051909.htm
- http://m.blog.ghtkgg.cn/nnews/1344476.htm
- http://m.blog.ghtkgg.cn/nnews/18505.htm
- http://m.blog.ghtkgg.cn/nnews/27407.htm
- http://m.blog.ghtkgg.cn/nnews/44090.htm
- http://m.blog.ghtkgg.cn/nnews/41208.htm
- http://m.blog.ghtkgg.cn/nnews/87962.htm
- http://m.blog.ghtkgg.cn/nnews/4833.htm
- http://m.blog.ghtkgg.cn/nnews/873786.htm
- http://m.blog.ghtkgg.cn/nnews/9878287.htm
- http://m.blog.ghtkgg.cn/nnews/108249.htm
- http://m.blog.ghtkgg.cn/nnews/20842.htm
- http://m.blog.ghtkgg.cn/nnews/7179979.htm
- http://m.blog.ghtkgg.cn/nnews/1717238.htm
- http://m.blog.ghtkgg.cn/nnews/2211279.htm
- http://m.blog.ghtkgg.cn/nnews/43963.htm
- http://m.blog.ghtkgg.cn/nnews/15467.htm
- http://m.blog.ghtkgg.cn/nnews/20202.htm
- http://m.blog.ghtkgg.cn/nnews/905845.htm
- http://m.blog.ghtkgg.cn/nnews/2429.htm
- http://m.blog.ghtkgg.cn/nnews/7253232.htm
- http://m.blog.ghtkgg.cn/nnews/82494.htm
- http://m.blog.ghtkgg.cn/nnews/996433.htm
- http://m.blog.ghtkgg.cn/nnews/2407.htm
- http://m.blog.ghtkgg.cn/nnews/664191.htm
- http://m.blog.ghtkgg.cn/nnews/5312.htm
- http://m.blog.ghtkgg.cn/nnews/96580.htm
- http://m.blog.ghtkgg.cn/nnews/6046157.htm
- http://m.blog.ghtkgg.cn/nnews/37340.htm
- http://m.blog.ghtkgg.cn/nnews/4492.htm
- http://m.blog.ghtkgg.cn/nnews/8852.htm
- http://m.blog.ghtkgg.cn/nnews/9532.htm
- http://m.blog.ghtkgg.cn/nnews/6690257.htm
- http://m.blog.ghtkgg.cn/nnews/24576.htm
- http://m.blog.ghtkgg.cn/nnews/98401.htm
- http://m.blog.ghtkgg.cn/nnews/4873.htm
- http://m.blog.ghtkgg.cn/nnews/894488.htm
- http://m.blog.ghtkgg.cn/nnews/25480.htm
- http://m.blog.ghtkgg.cn/nnews/6443346.htm
- http://m.blog.ghtkgg.cn/nnews/18267.htm
- http://m.blog.ghtkgg.cn/nnews/30916.htm
- http://m.blog.ghtkgg.cn/nnews/279556.htm
- http://m.blog.ghtkgg.cn/nnews/033497.htm
- http://m.blog.ghtkgg.cn/nnews/7713931.htm
- http://m.blog.ghtkgg.cn/nnews/44087.htm
- http://m.blog.ghtkgg.cn/nnews/81866.htm
- http://m.blog.ghtkgg.cn/nnews/9374261.htm
- http://m.blog.ghtkgg.cn/nnews/23129.htm
- http://m.blog.ghtkgg.cn/nnews/0404288.htm
- http://m.blog.ghtkgg.cn/nnews/3693.htm
- http://m.blog.ghtkgg.cn/nnews/1900230.htm
- http://m.blog.ghtkgg.cn/nnews/4582809.htm
- http://m.blog.ghtkgg.cn/nnews/8122.htm
- http://m.blog.ghtkgg.cn/nnews/04751.htm
- http://m.blog.ghtkgg.cn/nnews/7054191.htm
- http://m.blog.ghtkgg.cn/nnews/3460953.htm
- http://m.blog.ghtkgg.cn/nnews/4591602.htm
- http://m.blog.ghtkgg.cn/nnews/9054.htm
- http://m.blog.ghtkgg.cn/nnews/0322986.htm
- http://m.blog.ghtkgg.cn/nnews/64970.htm
- http://m.blog.ghtkgg.cn/nnews/31287.htm
- http://m.blog.ghtkgg.cn/nnews/3934.htm
- http://m.blog.ghtkgg.cn/nnews/1642619.htm
- http://m.blog.ghtkgg.cn/nnews/1588.htm
- http://m.blog.ghtkgg.cn/nnews/734759.htm
- http://m.blog.ghtkgg.cn/nnews/9884366.htm
- http://m.blog.ghtkgg.cn/nnews/63412.htm
- http://m.blog.ghtkgg.cn/nnews/3841395.htm
- http://m.blog.ghtkgg.cn/nnews/2861.htm
- http://m.blog.ghtkgg.cn/nnews/4503.htm
- http://m.blog.ghtkgg.cn/nnews/8983295.htm
- http://m.blog.ghtkgg.cn/nnews/1446.htm
- http://m.blog.ghtkgg.cn/nnews/60204.htm
- http://m.blog.ghtkgg.cn/nnews/138398.htm
- http://m.blog.ghtkgg.cn/nnews/8648.htm
- http://m.blog.ghtkgg.cn/nnews/2863491.htm
- http://m.blog.ghtkgg.cn/nnews/0319.htm
- http://m.blog.ghtkgg.cn/nnews/7518.htm
- http://m.blog.ghtkgg.cn/nnews/793445.htm
- http://m.blog.ghtkgg.cn/nnews/0839905.htm
- http://m.blog.ghtkgg.cn/nnews/6398800.htm
- http://m.blog.ghtkgg.cn/nnews/6495446.htm
- http://m.blog.ghtkgg.cn/nnews/9671.htm
- http://m.blog.ghtkgg.cn/nnews/2355045.htm
- http://m.blog.ghtkgg.cn/nnews/823697.htm
- http://m.blog.ghtkgg.cn/nnews/26151.htm
- http://m.blog.ghtkgg.cn/nnews/5456.htm
- http://m.blog.ghtkgg.cn/nnews/8828170.htm
- http://m.blog.ghtkgg.cn/nnews/1336571.htm
- http://m.blog.ghtkgg.cn/nnews/63929.htm
- http://m.blog.ghtkgg.cn/nnews/2677.htm
- http://m.blog.ghtkgg.cn/nnews/74946.htm
- http://m.blog.ghtkgg.cn/nnews/0306.htm
- http://m.blog.ghtkgg.cn/nnews/9621504.htm
- http://m.blog.ghtkgg.cn/nnews/814955.htm
- http://m.blog.ghtkgg.cn/nnews/3655.htm
- http://m.blog.ghtkgg.cn/nnews/2918.htm
- http://m.blog.ghtkgg.cn/nnews/356696.htm
- http://m.blog.ghtkgg.cn/nnews/6482986.htm
- http://m.blog.ghtkgg.cn/nnews/1551533.htm
- http://m.blog.ghtkgg.cn/nnews/8511.htm
- http://m.blog.ghtkgg.cn/nnews/6731126.htm
- http://m.blog.ghtkgg.cn/nnews/9461.htm
- http://m.blog.ghtkgg.cn/nnews/9373565.htm
- http://m.blog.ghtkgg.cn/nnews/91497.htm
- http://m.blog.ghtkgg.cn/nnews/41167.htm
- http://m.blog.ghtkgg.cn/nnews/221673.htm
- http://m.blog.ghtkgg.cn/nnews/122420.htm
- http://m.blog.ghtkgg.cn/nnews/5415.htm
- http://m.blog.ghtkgg.cn/nnews/1967.htm
- http://m.blog.ghtkgg.cn/nnews/2828262.htm
- http://m.blog.ghtkgg.cn/nnews/266263.htm
- http://m.blog.ghtkgg.cn/nnews/82390.htm
- http://m.blog.ghtkgg.cn/nnews/5244.htm
- http://m.blog.ghtkgg.cn/nnews/1455.htm
- http://m.blog.ghtkgg.cn/nnews/2199.htm
- http://m.blog.ghtkgg.cn/nnews/952513.htm
- http://m.blog.ghtkgg.cn/nnews/4096.htm
- http://m.blog.ghtkgg.cn/nnews/46859.htm
- http://m.blog.ghtkgg.cn/nnews/5414415.htm
- http://m.blog.ghtkgg.cn/nnews/2464562.htm
- http://m.blog.ghtkgg.cn/nnews/470978.htm
- http://m.blog.ghtkgg.cn/nnews/379938.htm
- http://m.blog.ghtkgg.cn/nnews/107756.htm
- http://m.blog.ghtkgg.cn/nnews/80730.htm
- http://m.blog.ghtkgg.cn/nnews/350395.htm
- http://m.blog.ghtkgg.cn/nnews/7233.htm
- http://m.blog.ghtkgg.cn/nnews/367506.htm
- http://m.blog.ghtkgg.cn/nnews/889799.htm
- http://m.blog.ghtkgg.cn/nnews/48682.htm
- http://m.blog.ghtkgg.cn/nnews/896917.htm

## 项目结构

项目采用模块化分层设计，所有核心脚本集中于 `webindex` 包内，配置与数据文件存放于 `data` 和 `config` 目录。顶层目录同时包含文档、测试与构建相关文件。

```
webindex-core/
├── webindex/                        # 核心 Python 包
│   ├── __init__.py                  # 包版本与导出符号控制
│   ├── cli.py                       # 命令行入口，解析参数并调度子命令
│   ├── scanner.py                   # 链接扫描器，负责读取、解析与去重
│   ├── validator.py                 # URL 格式校验器，含协议头与字符集检查
│   ├── exporter.py                  # 多格式导出器，支持 json / txt / html
│   └── snapshot.py                  # 快照管理器，生成与恢复时间戳版本
├── scripts/                         # 可执行辅助脚本
│   ├── init.sh                      # 环境初始化，创建目录与默认配置
│   ├── health_check.sh              # 可选健康检查，使用 curl 探测链接状态
│   └── export_all.sh                # 批量导出所有格式
├── config/                          # 配置目录
│   ├── example.env                  # 环境变量示例，包含扫描深度与输出路径
│   └── categories.toml              # 分类映射表，定义技术领域与关键词的对应关系
├── data/                            # 数据目录
│   ├── raw_links.txt                # 用户输入的原始链接列表（纯文本）
│   ├── index.json                   # 当前索引主文件
│   └── snapshots/                   # 快照存储目录，按时间戳命名
│       └── 2026-08-25-14-30.json    # 示例快照文件
├── docs/                            # 文档目录
│   ├── getting-started.md           # 入门指南
│   ├── format-spec.md               # 格式规范
│   ├── advanced-config.md           # 高级配置
│   └── troubleshooting.md           # 故障排除
├── tests/                           # 单元测试
│   ├── test_scanner.py              # 扫描器测试用例
│   ├── test_validator.py            # 校验器测试用例
│   └── fixtures/                    # 测试数据固定装置
│       └── sample_links.txt         # 用于测试的样例链接列表
├── Makefile                         # 构建任务定义（导出、测试、清理）
├── CHANGELOG.md                     # 版本变更日志
└── README.md                        # 项目说明文档（本文件）
```

---

## 贡献指南

本项目的贡献流程遵循标准的 GitHub Pull Request 工作流。所有新增功能或修复必须通过完整的测试套件，并保持文档同步更新。

1. 从 `main` 分支创建新的功能分支，分支命名格式为 `feature/简要描述` 或 `fix/问题编号`。确保分支名称清晰反映变更内容。

2. 在 `webindex/` 目录下修改或新增 Python 模块，遵循 PEP 8 代码风格，并在 `tests/` 目录下补充相应的单元测试用例。测试覆盖率不得低于 85%。

3. 更新 `docs/` 下相关文档，若变更影响用户可见行为（如命令行参数、配置项或输出格式），必须同步更新 `getting-started.md` 或 `advanced-config.md` 中的对应章节。

4. 提交前运行 `make test` 确保所有测试通过，并执行 `make lint` 进行静态代码检查。提交信息采用约定式提交格式（`feat:`、`fix:`、`docs:`、`chore:` 等）。

5. 发起 Pull Request 至 `main` 分支，在 PR 描述中列出变更动机、实现方式以及影响范围。至少需要一位项目维护者审核通过后方可合并。

---

## 常见问题

**问：扫描器是否支持对 URL 进行递归解析或重定向跟踪？**

答：当前版本不执行递归解析或重定向跟踪。扫描器仅做格式检查与去重处理，不发起实际 HTTP 请求。如需验证链接可达性，可单独运行 `health_check.sh` 脚本，该脚本会使用 curl 探测每个链接的状态码并生成报告。请注意，健康检查会增加运行时间，建议仅在网络环境稳定时执行。

**问：如何处理资源列表中包含非标准协议的 URL（如 ftp、mailto 或相对路径）？**

答：默认格式校验器仅接受 `http://` 和 `https://` 协议的链接，其他协议会被标记为警告并跳过索引。如果确实需要收录非 HTTP 协议的链接，可以在 `config/categories.toml` 中将 `strict_protocol` 设为 `false`，此时校验器只检查 URL 是否包含合法字符，不再强制协议头。但请注意，导出为 HTML 目录页时，非 HTTP 链接可能无法在浏览器中正常打开。

**问：快照功能是否会占用大量磁盘空间？**

答：快照仅存储链接列表的元数据（URL、分类标签、添加时间），而非链接指向的实际内容。每个快照文件大小通常不超过 500 KB。系统默认保留最近 30 天的快照，超过期限的旧快照会在每次扫描时自动清理。若需调整保留策略，可在 `config/example.env` 中设置 `SNAPSHOT_RETENTION_DAYS` 参数。

---

## 许可证

MIT License

Copyright (c) 2026 WebIndex Core Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:49
