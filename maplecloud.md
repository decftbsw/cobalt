# WebLink Harvest

WebLink Harvest 是一个面向技术调研、内容聚合与批量外链分析的开源辅助工具集。该项目定位于帮助开发者、技术写作者、SEO 分析师以及信息检索研究人员，系统化地收集、整理、验证和导出大规模外链资源。WebLink Harvest 不提供具体的业务数据，而是提供一套标准化的外链处理流水线，支持从原始 URL 列表出发，完成去重、可用性检查、分类标记、元信息补充等操作，最终生成结构化的资源清单，便于下游系统使用。

WebLink Harvest 的核心设计理念是“原始链接可追溯，处理过程可复现”。所有输入输出均采用纯文本或结构化数据格式，支持脚本级调用和批处理任务集成。项目本身不依赖任何外部商业 API，完全基于开源生态组件构建，适合部署在个人工作站、CI 环境或轻量级云服务器中。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入待处理链接，自动识别常见协议格式。

**自动去重与归一化** 基于 URL 标准化规则，对输入的链接进行去重处理，移除冗余参数片段，保留原始地址的可追溯映射关系。

**存活状态探测** 通过可配置的超时与重试策略，对每条链接发起 HEAD 或 GET 请求，记录状态码、响应时间和内容类型，标记不可用资源。

**元信息提取** 对可访问的链接，自动提取页面标题、摘要描述、关键词等基础元数据，供后续分类和索引使用。

**规则化分类标签** 支持用户自定义正则表达式或关键词规则，根据 URL 特征或页面内容为链接打上分类标签，便于按主题组织资源。

**多格式导出** 支持将处理完毕的链接列表导出为 JSON、CSV 或纯文本格式，适配不同下游工具的使用习惯。

**处理日志与审计** 完整记录每一次处理任务的开始时间、结束时间、处理条目数、失败条目数以及错误详情，确保操作可审计。

**增量更新支持** 支持基于已有结果文件进行增量追加或刷新，避免重复处理未变更的链接，提升大规模任务效率。

## 应用场景

技术文档外链整理：技术作者在编写文档或博客时，常常需要引用大量外部参考资料。WebLink Harvest 可帮助快速导入原始链接池，自动检查每篇参考文章的可用性，并提取标题和摘要，便于在文档末尾生成规范的参考链接列表。

历史资源库迁移验证：当组织需要将旧版网站或知识库中的外部链接迁移到新平台时，可使用 WebLink Harvest 对全部外链进行批量可达性检测，标记出已失效或变更的链接，为迁移决策提供数据依据。

SEO 外链质量初筛：SEO 分析师在获取一批潜在外链资源后，可使用 WebLink Harvest 快速检测目标域名是否可访问、响应速度是否正常、是否存在重定向链，从而初步筛选出质量较高的候选外链，减少人工逐一验证的时间成本。

学术文献补充材料整理：研究人员在整理论文或报告中的网络资源引用时，可使用 WebLink Harvest 对引用 URL 进行统一格式整理和存活状态记录，生成可供审阅人核验的资源附录。

## 快速开始

以下步骤演示如何从代码仓库获取 WebLink Harvest 并在本地环境完成初次运行。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-harvest/weblink-harvest.git

# 进入项目目录
cd weblink-harvest

# 安装依赖（使用 Python 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 执行示例任务：处理 resources/example_links.txt 中的链接列表
python run_harvest.py --input resources/example_links.txt --output results/output.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 或更高版本以获得更好的性能 |
| requests | 2.25.0 及以上 | 用于发送 HTTP 请求，检测链接可用性及获取响应元数据 |
| beautifulsoup4 | 4.9.0 及以上 | 用于解析 HTML 页面内容，提取标题和描述等元信息 |
| lxml | 4.6.0 及以上 | 作为 beautifulsoup4 的解析后端，提供更快的 HTML 解析速度 |
| pandas | 1.2.0 及以上 | 用于处理 CSV 和 Excel 格式的输入输出，仅在需要表格导出功能时强制要求 |
| pytest | 6.0.0 及以上 | 仅开发测试时使用，生产环境可不安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting_started.md | 如何安装、配置并运行第一个处理任务；输入文件格式要求是什么 |
| 配置参考 | docs/configuration.md | 支持哪些配置项；如何调整超时时间、重试次数、并发数等参数 |
| 数据格式规范 | docs/data_formats.md | 输入输出文件的具体字段定义；JSON 和 CSV 的结构示例 |
| 高级用法 | docs/advanced_usage.md | 如何使用自定义分类规则；如何实现增量更新；如何扩展元信息提取器 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/038093.htm
- http://m.wap.bwbkj.cn/snews/6355.htm
- http://m.wap.bwbkj.cn/snews/06660.htm
- http://m.wap.bwbkj.cn/snews/65712.htm
- http://m.wap.bwbkj.cn/snews/734822.htm
- http://m.wap.bwbkj.cn/snews/9063.htm
- http://m.wap.bwbkj.cn/snews/8471248.htm
- http://m.wap.bwbkj.cn/snews/69966.htm
- http://m.wap.bwbkj.cn/snews/893941.htm
- http://m.wap.bwbkj.cn/snews/9961.htm
- http://m.wap.bwbkj.cn/snews/4707.htm
- http://m.wap.bwbkj.cn/snews/1272113.htm
- http://m.wap.bwbkj.cn/snews/2741360.htm
- http://m.wap.bwbkj.cn/snews/6918.htm
- http://m.wap.bwbkj.cn/snews/09134.htm
- http://m.wap.bwbkj.cn/snews/8232.htm
- http://m.wap.bwbkj.cn/snews/5417842.htm
- http://m.wap.bwbkj.cn/snews/91885.htm
- http://m.wap.bwbkj.cn/snews/82658.htm
- http://m.wap.bwbkj.cn/snews/1235.htm
- http://m.wap.bwbkj.cn/snews/2794897.htm
- http://m.wap.bwbkj.cn/snews/3611.htm
- http://m.wap.bwbkj.cn/snews/828863.htm
- http://m.wap.bwbkj.cn/snews/1400.htm
- http://m.wap.bwbkj.cn/snews/4124161.htm
- http://m.wap.bwbkj.cn/snews/26438.htm
- http://m.wap.bwbkj.cn/snews/5233.htm
- http://m.wap.bwbkj.cn/snews/950742.htm
- http://m.wap.bwbkj.cn/snews/7565750.htm
- http://m.wap.bwbkj.cn/snews/3393.htm
- http://m.wap.bwbkj.cn/snews/4011939.htm
- http://m.wap.bwbkj.cn/snews/441335.htm
- http://m.wap.bwbkj.cn/snews/4502791.htm
- http://m.wap.bwbkj.cn/snews/499407.htm
- http://m.wap.bwbkj.cn/snews/9226341.htm
- http://m.wap.bwbkj.cn/snews/9112.htm
- http://m.wap.bwbkj.cn/snews/75483.htm
- http://m.wap.bwbkj.cn/snews/346391.htm
- http://m.wap.bwbkj.cn/snews/060623.htm
- http://m.wap.bwbkj.cn/snews/4158972.htm
- http://m.wap.bwbkj.cn/snews/5335739.htm
- http://m.wap.bwbkj.cn/snews/6935928.htm
- http://m.wap.bwbkj.cn/snews/2384.htm
- http://m.wap.bwbkj.cn/snews/9858907.htm
- http://m.wap.bwbkj.cn/snews/8397134.htm
- http://m.wap.bwbkj.cn/snews/8776123.htm
- http://m.wap.bwbkj.cn/snews/2239.htm
- http://m.wap.bwbkj.cn/snews/328823.htm
- http://m.wap.bwbkj.cn/snews/3123.htm
- http://m.wap.bwbkj.cn/snews/2591552.htm
- http://m.wap.bwbkj.cn/snews/9594348.htm
- http://m.wap.bwbkj.cn/snews/05487.htm
- http://m.wap.bwbkj.cn/snews/8357.htm
- http://m.wap.bwbkj.cn/snews/3354.htm
- http://m.wap.bwbkj.cn/snews/0057.htm
- http://m.wap.bwbkj.cn/snews/17289.htm
- http://m.wap.bwbkj.cn/snews/9320.htm
- http://m.wap.bwbkj.cn/snews/4727.htm
- http://m.wap.bwbkj.cn/snews/7400951.htm
- http://m.wap.bwbkj.cn/snews/526050.htm
- http://m.wap.bwbkj.cn/snews/4461584.htm
- http://m.wap.bwbkj.cn/snews/42860.htm
- http://m.wap.bwbkj.cn/snews/4725033.htm
- http://m.wap.bwbkj.cn/snews/4037.htm
- http://m.wap.bwbkj.cn/snews/761087.htm
- http://m.wap.bwbkj.cn/snews/76396.htm
- http://m.wap.bwbkj.cn/snews/21627.htm
- http://m.wap.bwbkj.cn/snews/28233.htm
- http://m.wap.bwbkj.cn/snews/16933.htm
- http://m.wap.bwbkj.cn/snews/0967733.htm
- http://m.wap.bwbkj.cn/snews/5376937.htm
- http://m.wap.bwbkj.cn/snews/61400.htm
- http://m.wap.bwbkj.cn/snews/5517.htm
- http://m.wap.bwbkj.cn/snews/3802909.htm
- http://m.wap.bwbkj.cn/snews/98877.htm
- http://m.wap.bwbkj.cn/snews/4999.htm
- http://m.wap.bwbkj.cn/snews/90567.htm
- http://m.wap.bwbkj.cn/snews/15775.htm
- http://m.wap.bwbkj.cn/snews/22592.htm
- http://m.wap.bwbkj.cn/snews/21114.htm
- http://m.wap.bwbkj.cn/snews/596052.htm
- http://m.wap.bwbkj.cn/snews/337588.htm
- http://m.wap.bwbkj.cn/snews/928472.htm
- http://m.wap.bwbkj.cn/snews/0905092.htm
- http://m.wap.bwbkj.cn/snews/3600395.htm
- http://m.wap.bwbkj.cn/snews/1051712.htm
- http://m.wap.bwbkj.cn/snews/9223314.htm
- http://m.wap.bwbkj.cn/snews/339747.htm
- http://m.wap.bwbkj.cn/snews/0036351.htm
- http://m.wap.bwbkj.cn/snews/65812.htm
- http://m.wap.bwbkj.cn/snews/70548.htm
- http://m.wap.bwbkj.cn/snews/828987.htm
- http://m.wap.bwbkj.cn/snews/053708.htm
- http://m.wap.bwbkj.cn/snews/37977.htm
- http://m.wap.bwbkj.cn/snews/872178.htm
- http://m.wap.bwbkj.cn/snews/7174851.htm
- http://m.wap.bwbkj.cn/snews/0947129.htm
- http://m.wap.bwbkj.cn/snews/63691.htm
- http://m.wap.bwbkj.cn/snews/31670.htm
- http://m.wap.bwbkj.cn/snews/6647887.htm
- http://m.wap.bwbkj.cn/snews/2574507.htm
- http://m.wap.bwbkj.cn/snews/6727909.htm
- http://m.wap.bwbkj.cn/snews/695783.htm
- http://m.wap.bwbkj.cn/snews/5395.htm
- http://m.wap.bwbkj.cn/snews/82917.htm
- http://m.wap.bwbkj.cn/snews/2714.htm
- http://m.wap.bwbkj.cn/snews/7057.htm
- http://m.wap.bwbkj.cn/snews/5294279.htm
- http://m.wap.bwbkj.cn/snews/729331.htm
- http://m.wap.bwbkj.cn/snews/96809.htm
- http://m.wap.bwbkj.cn/snews/6351524.htm
- http://m.wap.bwbkj.cn/snews/9387976.htm
- http://m.wap.bwbkj.cn/snews/0853001.htm
- http://m.wap.bwbkj.cn/snews/6247380.htm
- http://m.wap.bwbkj.cn/snews/71955.htm
- http://m.wap.bwbkj.cn/snews/22386.htm
- http://m.wap.bwbkj.cn/snews/7367010.htm
- http://m.wap.bwbkj.cn/snews/87834.htm
- http://m.wap.bwbkj.cn/snews/3941.htm
- http://m.wap.bwbkj.cn/snews/88658.htm
- http://m.wap.bwbkj.cn/snews/88063.htm
- http://m.wap.bwbkj.cn/snews/7541.htm
- http://m.wap.bwbkj.cn/snews/7671.htm
- http://m.wap.bwbkj.cn/snews/5653.htm
- http://m.wap.bwbkj.cn/snews/051764.htm
- http://m.wap.bwbkj.cn/snews/8947626.htm
- http://m.wap.bwbkj.cn/snews/15729.htm
- http://m.wap.bwbkj.cn/snews/4381352.htm
- http://m.wap.bwbkj.cn/snews/2780.htm
- http://m.wap.bwbkj.cn/snews/9787384.htm
- http://m.wap.bwbkj.cn/snews/89266.htm
- http://m.wap.bwbkj.cn/snews/7506801.htm
- http://m.wap.bwbkj.cn/snews/2217.htm
- http://m.wap.bwbkj.cn/snews/656492.htm
- http://m.wap.bwbkj.cn/snews/6368.htm
- http://m.wap.bwbkj.cn/snews/243983.htm
- http://m.wap.bwbkj.cn/snews/789763.htm
- http://m.wap.bwbkj.cn/snews/40980.htm
- http://m.wap.bwbkj.cn/snews/20014.htm
- http://m.wap.bwbkj.cn/snews/5992363.htm
- http://m.wap.bwbkj.cn/snews/0551.htm
- http://m.wap.bwbkj.cn/snews/52931.htm
- http://m.wap.bwbkj.cn/snews/2584.htm
- http://m.wap.bwbkj.cn/snews/817272.htm
- http://m.wap.bwbkj.cn/snews/94501.htm
- http://m.wap.bwbkj.cn/snews/263592.htm
- http://m.wap.bwbkj.cn/snews/106423.htm
- http://m.wap.bwbkj.cn/snews/40311.htm
- http://m.wap.bwbkj.cn/snews/26709.htm
- http://m.wap.bwbkj.cn/snews/5248260.htm
- http://m.wap.bwbkj.cn/snews/8202597.htm
- http://m.wap.bwbkj.cn/snews/8296902.htm
- http://m.wap.bwbkj.cn/snews/18339.htm
- http://m.wap.bwbkj.cn/snews/104025.htm
- http://m.wap.bwbkj.cn/snews/9645194.htm
- http://m.wap.bwbkj.cn/snews/88355.htm
- http://m.wap.bwbkj.cn/snews/29777.htm
- http://m.wap.bwbkj.cn/snews/0943.htm
- http://m.wap.bwbkj.cn/snews/2650499.htm
- http://m.wap.bwbkj.cn/snews/3168196.htm
- http://m.wap.bwbkj.cn/snews/08228.htm
- http://m.wap.bwbkj.cn/snews/216419.htm
- http://m.wap.bwbkj.cn/snews/1696735.htm
- http://m.wap.bwbkj.cn/snews/00782.htm
- http://m.wap.bwbkj.cn/snews/8520386.htm
- http://m.wap.bwbkj.cn/snews/16016.htm
- http://m.wap.bwbkj.cn/snews/72825.htm
- http://m.wap.bwbkj.cn/snews/1006.htm
- http://m.wap.bwbkj.cn/snews/6524.htm
- http://m.wap.bwbkj.cn/snews/94285.htm
- http://m.wap.bwbkj.cn/snews/36776.htm
- http://m.wap.bwbkj.cn/snews/1165.htm
- http://m.wap.bwbkj.cn/snews/9101.htm
- http://m.wap.bwbkj.cn/snews/1517801.htm
- http://m.wap.bwbkj.cn/snews/1001844.htm
- http://m.wap.bwbkj.cn/snews/43364.htm
- http://m.wap.bwbkj.cn/snews/7986284.htm
- http://m.wap.bwbkj.cn/snews/3678216.htm
- http://m.wap.bwbkj.cn/snews/3758.htm
- http://m.wap.bwbkj.cn/snews/86090.htm
- http://m.wap.bwbkj.cn/snews/773131.htm
- http://m.wap.bwbkj.cn/snews/1078974.htm
- http://m.wap.bwbkj.cn/snews/2876346.htm
- http://m.wap.bwbkj.cn/snews/28167.htm
- http://m.wap.bwbkj.cn/snews/8925467.htm
- http://m.wap.bwbkj.cn/snews/699076.htm
- http://m.wap.bwbkj.cn/snews/775456.htm
- http://m.wap.bwbkj.cn/snews/7550136.htm
- http://m.wap.bwbkj.cn/snews/8158475.htm
- http://m.wap.bwbkj.cn/snews/66060.htm
- http://m.wap.bwbkj.cn/snews/0794494.htm
- http://m.wap.bwbkj.cn/snews/0049303.htm
- http://m.wap.bwbkj.cn/snews/5805736.htm
- http://m.wap.bwbkj.cn/snews/4585932.htm
- http://m.wap.bwbkj.cn/snews/03008.htm
- http://m.wap.bwbkj.cn/snews/9616.htm
- http://m.wap.bwbkj.cn/snews/61836.htm
- http://m.wap.bwbkj.cn/snews/4160.htm
- http://m.wap.bwbkj.cn/snews/40600.htm
- http://m.wap.bwbkj.cn/snews/079563.htm
- http://m.wap.bwbkj.cn/snews/901765.htm
- http://m.wap.bwbkj.cn/snews/904316.htm
- http://m.wap.bwbkj.cn/snews/84205.htm
- http://m.wap.bwbkj.cn/snews/704090.htm
- http://m.wap.bwbkj.cn/snews/324523.htm
- http://m.wap.bwbkj.cn/snews/3146881.htm
- http://m.wap.bwbkj.cn/snews/216379.htm
- http://m.wap.bwbkj.cn/snews/474856.htm
- http://m.wap.bwbkj.cn/snews/3080.htm
- http://m.wap.bwbkj.cn/snews/6912.htm
- http://m.wap.bwbkj.cn/snews/4869.htm
- http://m.wap.bwbkj.cn/snews/231917.htm
- http://m.wap.bwbkj.cn/snews/1935585.htm
- http://m.wap.bwbkj.cn/snews/4444.htm
- http://m.wap.bwbkj.cn/snews/61224.htm
- http://m.wap.bwbkj.cn/snews/6765443.htm
- http://m.wap.bwbkj.cn/snews/82550.htm
- http://m.wap.bwbkj.cn/snews/668961.htm
- http://m.wap.bwbkj.cn/snews/9070502.htm
- http://m.wap.bwbkj.cn/snews/33540.htm
- http://m.wap.bwbkj.cn/snews/6728627.htm
- http://m.wap.bwbkj.cn/snews/208844.htm
- http://m.wap.bwbkj.cn/snews/7364.htm
- http://m.wap.bwbkj.cn/snews/84403.htm
- http://m.wap.bwbkj.cn/snews/040132.htm
- http://m.wap.bwbkj.cn/snews/108563.htm
- http://m.wap.bwbkj.cn/snews/0875452.htm
- http://m.wap.bwbkj.cn/snews/6232255.htm
- http://m.wap.bwbkj.cn/snews/9745.htm
- http://m.wap.bwbkj.cn/snews/4473768.htm
- http://m.wap.bwbkj.cn/snews/963372.htm
- http://m.wap.bwbkj.cn/snews/748127.htm
- http://m.wap.bwbkj.cn/snews/894209.htm
- http://m.wap.bwbkj.cn/snews/5602163.htm
- http://m.wap.bwbkj.cn/snews/6911.htm
- http://m.wap.bwbkj.cn/snews/113955.htm
- http://m.wap.bwbkj.cn/snews/0849037.htm
- http://m.wap.bwbkj.cn/snews/386890.htm
- http://m.wap.bwbkj.cn/snews/0539.htm
- http://m.wap.bwbkj.cn/snews/45760.htm
- http://m.wap.bwbkj.cn/snews/36841.htm
- http://m.wap.bwbkj.cn/snews/154785.htm
- http://m.wap.bwbkj.cn/snews/6662.htm
- http://m.wap.bwbkj.cn/snews/17368.htm
- http://m.wap.bwbkj.cn/snews/24116.htm
- http://m.wap.bwbkj.cn/snews/6608.htm
- http://m.wap.bwbkj.cn/snews/8666.htm
- http://m.wap.bwbkj.cn/snews/63676.htm
- http://m.wap.bwbkj.cn/snews/1065295.htm
- http://m.wap.bwbkj.cn/snews/604105.htm
- http://m.wap.bwbkj.cn/snews/2392.htm
- http://m.wap.bwbkj.cn/snews/50208.htm
- http://m.wap.bwbkj.cn/snews/1109607.htm
- http://m.wap.bwbkj.cn/snews/1396.htm
- http://m.wap.bwbkj.cn/snews/7533468.htm
- http://m.wap.bwbkj.cn/snews/14682.htm
- http://m.wap.bwbkj.cn/snews/46466.htm
- http://m.wap.bwbkj.cn/snews/9252.htm
- http://m.wap.bwbkj.cn/snews/0644.htm
- http://m.wap.bwbkj.cn/snews/392434.htm
- http://m.wap.bwbkj.cn/snews/90800.htm
- http://m.wap.bwbkj.cn/snews/1114080.htm
- http://m.wap.bwbkj.cn/snews/12570.htm
- http://m.wap.bwbkj.cn/snews/65217.htm
- http://m.wap.bwbkj.cn/snews/44257.htm
- http://m.wap.bwbkj.cn/snews/907939.htm
- http://m.wap.bwbkj.cn/snews/59001.htm
- http://m.wap.bwbkj.cn/snews/1912.htm
- http://m.wap.bwbkj.cn/snews/5951.htm
- http://m.wap.bwbkj.cn/snews/39235.htm
- http://m.wap.bwbkj.cn/snews/2054.htm
- http://m.wap.bwbkj.cn/snews/2405.htm
- http://m.wap.bwbkj.cn/snews/386684.htm
- http://m.wap.bwbkj.cn/snews/92184.htm
- http://m.wap.bwbkj.cn/snews/923115.htm
- http://m.wap.bwbkj.cn/snews/380271.htm
- http://m.wap.bwbkj.cn/snews/5666926.htm
- http://m.wap.bwbkj.cn/snews/3339891.htm
- http://m.wap.bwbkj.cn/snews/086653.htm
- http://m.wap.bwbkj.cn/snews/73649.htm
- http://m.wap.bwbkj.cn/snews/9702174.htm
- http://m.wap.bwbkj.cn/snews/394736.htm
- http://m.wap.bwbkj.cn/snews/548674.htm
- http://m.wap.bwbkj.cn/snews/9744.htm
- http://m.wap.bwbkj.cn/snews/8483522.htm
- http://m.wap.bwbkj.cn/snews/627264.htm
- http://m.wap.bwbkj.cn/snews/8619.htm
- http://m.wap.bwbkj.cn/snews/0797262.htm
- http://m.wap.bwbkj.cn/snews/486867.htm
- http://m.wap.bwbkj.cn/snews/249992.htm
- http://m.wap.bwbkj.cn/snews/2906115.htm
- http://m.wap.bwbkj.cn/snews/561727.htm
- http://m.wap.bwbkj.cn/snews/207681.htm
- http://m.wap.bwbkj.cn/snews/624202.htm
- http://m.wap.bwbkj.cn/snews/117884.htm
- http://m.wap.bwbkj.cn/snews/3124.htm
- http://m.wap.bwbkj.cn/snews/766426.htm
- http://m.wap.bwbkj.cn/snews/8659.htm
- http://m.wap.bwbkj.cn/snews/921221.htm
- http://m.wap.bwbkj.cn/snews/822336.htm

## 项目结构

```
weblink-harvest/
├── run_harvest.py                # 命令行入口，解析参数并调度主流程
├── requirements.txt              # Python 依赖清单，包含核心库与可选库
├── config/                       # 配置目录
│   ├── default.yaml              # 默认配置，含超时、重试、并发等参数
│   └── custom_rules.yaml         # 用户自定义分类规则模板
├── core/                         # 核心处理模块
│   ├── loader.py                 # 链接加载器，支持文件与直接输入
│   ├── deduper.py                # 去重与归一化处理
│   ├── checker.py                # 存活状态探测，含 HTTP 请求逻辑
│   └── extractor.py              # 元信息提取，依赖 beautifulsoup4
├── export/                       # 导出模块
│   ├── json_exporter.py          # JSON 格式导出
│   ├── csv_exporter.py           # CSV 格式导出，依赖 pandas
│   └── text_exporter.py          # 纯文本格式导出
├── utils/                        # 工具函数集合
│   ├── logger.py                 # 日志记录与审计文件生成
│   ├── url_parser.py             # URL 解析与标准化辅助函数
│   └── retry.py                  # 重试策略与退避算法实现
├── tests/                        # 单元测试目录
│   ├── test_loader.py            # 链接加载器测试用例
│   ├── test_deduper.py           # 去重逻辑测试用例
│   └── test_checker.py           # 存活检查测试用例
├── resources/                    # 示例资源目录
│   ├── example_links.txt         # 示例输入链接列表
│   └── sample_output.json        # 示例输出结果文件
└── docs/                         # 完整文档目录
    ├── getting_started.md        # 入门指南
    ├── configuration.md          # 配置说明
    ├── data_formats.md           # 数据格式规范
    └── advanced_usage.md         # 高级用法说明
```

## 贡献指南

欢迎提交问题和改进建议。在提交拉取请求之前，请确保遵循以下流程：

首先，在 GitHub 仓库的 Issue 区域中查找是否已有类似议题。若无，请新建一个议题详细描述你发现的问题或希望新增的功能，并等待维护者的反馈。

其次，从仓库派生一份代码到你的个人账户下，并在本地创建一个新的功能分支。分支命名建议采用 `feature/描述` 或 `fix/描述` 的格式，以便于识别。

完成代码修改后，请确保所有现有单元测试能够通过，并为新增的逻辑补充对应的测试用例。测试覆盖率不应低于现有水平。

提交拉取请求时，请在描述中清晰引用相关的议题编号，并简要说明修改内容、测试结果以及是否影响现有接口兼容性。

最后，拉取请求需要至少一位项目维护者进行代码审查。审查通过后，将由维护者合并至主分支并同步更新文档。

## 常见问题

问题：程序在执行链接检查时出现大量超时错误，如何处理？

回答：超时通常由网络环境不稳定或目标服务器响应缓慢引起。建议首先检查本机网络连接状况。若网络正常，可在配置文件中调整 `request_timeout` 参数，适当增加超时阈值。同时，可通过 `max_retries` 参数控制重试次数，以及 `retry_backoff` 参数设置退避间隔。对于大规模任务，建议降低并发数 `concurrency_limit` 以避免被目标服务器限流。

问题：处理结果中部分链接显示状态码为 403 或 429，是否意味着链接无效？

回答：状态码 403 表示服务器拒绝访问，可能由防盗链机制或 IP 限制导致。状态码 429 表示请求过于频繁，触发速率限制。这两种情况均不代表链接永久失效。建议对 403 链接尝试更换 User-Agent 或 Referer 头信息后重新检测。对于 429 链接，应适当延长请求间隔或降低并发数。WebLink Harvest 的配置文件中提供了自定义请求头字段，可供用户按需修改。

问题：如何批量更新已有结果文件中的链接状态，而不重新处理所有条目？

回答：WebLink Harvest 支持增量更新模式。在命令行中使用 `--update` 参数，并指定已有的结果 JSON 文件路径，程序将仅对结果文件中标记为未处理或处理失败的链接重新发起检测请求，对已成功的链接保持原状态不变。此模式可显著减少重复请求次数，适合定期刷新资源列表的场景。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:09
