# JNews Link Aggregator

JNews Link Aggregator 是一个专注于聚合、整理和检索移动端新闻资讯链接的开源工具集。该项目面向数据采集工程师、新闻聚合平台运营者以及学术研究者，提供了一套标准化的外链采集与元数据提取方案，用于从指定的移动新闻站点批量获取文章 URL 并进行结构化存储。

项目核心定位在于解决移动端新闻链接分散、格式不统一、采集效率低下等问题，通过轻量级的爬虫调度与链接质量校验机制，帮助用户快速构建专属的新闻链接仓库。当前版本已针对 ghtkgg.cn 移动站点的新闻路径规则完成适配，支持批量链接的可用性检查与基础信息抽取。

## 功能概览

批量链接导入与解析：支持从文本文件或标准输入流中批量导入 URL 列表，自动识别符合 /jnews/ 路径模式的链接并进行分类存储。

链接状态健康检查：对每条链接执行 HTTP 头部请求与响应状态码校验，自动标记超时、重定向及失效链接，并生成健康报告。

元数据智能提取：从目标页面中自动抽取标题、发布时间、正文摘要与来源字段，支持自定义提取规则与 XPath 配置。

链接去重与规范化：基于 URL 路径末尾的数字 ID 进行去重，剔除重复条目并保留最新版本，同时对 URL 进行协议与大小写归一化处理。

定时采集任务调度：内置轻量级任务调度器，支持按小时、每日或每周自动执行采集流水线，并将结果输出至指定目录。

数据导出与格式转换：支持将采集结果导出为 CSV、JSON 或 Markdown 表格格式，便于下游系统对接或人工审阅。

增量更新与日志追踪：记录每次采集任务的执行时间、成功数量与失败详情，支持增量追加写入，避免全量覆盖历史数据。

## 应用场景

新闻聚合平台的内容入库：运营人员可通过本工具定时拉取指定新闻源的最新文章链接，经过去重与状态校验后自动写入平台数据库，替代人工复制粘贴的低效流程。

学术研究的数据采集：社会科学或传播学研究者可使用本工具批量获取特定时间段内的新闻链接列表，结合元数据提取功能快速构建研究所需的语料索引。

SEO 与外链监测：SEO 优化师可通过链接健康检查功能定期扫描已发布外链的存活状态，及时发现并处理失效链接，维护网站的外部链接质量。

个人知识库的新闻订阅：技术爱好者可将本工具与个人笔记系统结合，每日自动抓取感兴趣的新闻链接并生成汇总报告，实现轻量级的个性化新闻简报。

## 快速开始

以下步骤将指导您在本地环境快速部署并运行 JNews Link Aggregator。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/jnews-link-aggregator.git

# 进入项目根目录
cd jnews-link-aggregator

# 安装项目依赖（使用 pip 和虚拟环境）
python3 -m venv venv
source venv/bin/activate  # Windows 系统请使用 venv\Scripts\activate
pip install -r requirements.txt

# 准备链接列表文件 links.txt，每行一个 URL
# 然后执行采集任务
python run_aggregator.py --input links.txt --output output/report.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 或更高 | 核心运行环境，推荐使用 3.9+ 以获得最佳性能 |
| requests | 2.28.0+ | 发送 HTTP 请求与处理响应，用于链接状态检查与页面抓取 |
| beautifulsoup4 | 4.11.0+ | 解析 HTML 文档并提取元数据，支持 lxml 与 html.parser 双引擎 |
| lxml | 4.9.0+ | 高性能 XML/HTML 解析器，beautifulsoup4 的推荐后端 |
| schedule | 1.2.0+ | 轻量级任务调度库，支持分钟级与小时级定时配置 |
| pandas | 1.5.0+ | 数据框操作与导出 CSV/JSON 格式，可选依赖但建议安装 |
| urllib3 | 1.26.0+ | 底层连接池与重试机制，requests 的依赖项 |
| certifi | 2022.12.0+ | SSL 证书验证包，确保 HTTPS 连接安全 |
| chardet | 5.0.0+ | 自动检测页面字符编码，避免中文乱码问题 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何安装、配置和运行第一次采集任务？ |
| 配置手册 | docs/configuration.md | 如何调整请求头、超时时间、重试策略和调度规则？ |
| 开发指南 | docs/development.md | 如何扩展自定义提取器、添加新数据源或修改采集流水线？ |
| API 参考 | docs/api-reference.md | 各模块的类与方法签名、参数说明与返回值类型是什么？ |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/7035.htm
- http://m.wap.ghtkgg.cn/jnews/966159.htm
- http://m.wap.ghtkgg.cn/jnews/8990071.htm
- http://m.wap.ghtkgg.cn/jnews/7884668.htm
- http://m.wap.ghtkgg.cn/jnews/9623.htm
- http://m.wap.ghtkgg.cn/jnews/024995.htm
- http://m.wap.ghtkgg.cn/jnews/7748777.htm
- http://m.wap.ghtkgg.cn/jnews/7524.htm
- http://m.wap.ghtkgg.cn/jnews/0220.htm
- http://m.wap.ghtkgg.cn/jnews/3741384.htm
- http://m.wap.ghtkgg.cn/jnews/9330682.htm
- http://m.wap.ghtkgg.cn/jnews/978574.htm
- http://m.wap.ghtkgg.cn/jnews/37339.htm
- http://m.wap.ghtkgg.cn/jnews/990045.htm
- http://m.wap.ghtkgg.cn/jnews/00024.htm
- http://m.wap.ghtkgg.cn/jnews/0597576.htm
- http://m.wap.ghtkgg.cn/jnews/7987697.htm
- http://m.wap.ghtkgg.cn/jnews/589152.htm
- http://m.wap.ghtkgg.cn/jnews/53235.htm
- http://m.wap.ghtkgg.cn/jnews/2454674.htm
- http://m.wap.ghtkgg.cn/jnews/933104.htm
- http://m.wap.ghtkgg.cn/jnews/27536.htm
- http://m.wap.ghtkgg.cn/jnews/82359.htm
- http://m.wap.ghtkgg.cn/jnews/40726.htm
- http://m.wap.ghtkgg.cn/jnews/92581.htm
- http://m.wap.ghtkgg.cn/jnews/066821.htm
- http://m.wap.ghtkgg.cn/jnews/67128.htm
- http://m.wap.ghtkgg.cn/jnews/0115564.htm
- http://m.wap.ghtkgg.cn/jnews/0988048.htm
- http://m.wap.ghtkgg.cn/jnews/9822532.htm
- http://m.wap.ghtkgg.cn/jnews/4429160.htm
- http://m.wap.ghtkgg.cn/jnews/073616.htm
- http://m.wap.ghtkgg.cn/jnews/4378252.htm
- http://m.wap.ghtkgg.cn/jnews/6503396.htm
- http://m.wap.ghtkgg.cn/jnews/05532.htm
- http://m.wap.ghtkgg.cn/jnews/5158.htm
- http://m.wap.ghtkgg.cn/jnews/5589.htm
- http://m.wap.ghtkgg.cn/jnews/1089466.htm
- http://m.wap.ghtkgg.cn/jnews/146461.htm
- http://m.wap.ghtkgg.cn/jnews/0098951.htm
- http://m.wap.ghtkgg.cn/jnews/5115.htm
- http://m.wap.ghtkgg.cn/jnews/956825.htm
- http://m.wap.ghtkgg.cn/jnews/751355.htm
- http://m.wap.ghtkgg.cn/jnews/9285.htm
- http://m.wap.ghtkgg.cn/jnews/0588427.htm
- http://m.wap.ghtkgg.cn/jnews/25952.htm
- http://m.wap.ghtkgg.cn/jnews/57520.htm
- http://m.wap.ghtkgg.cn/jnews/6381.htm
- http://m.wap.ghtkgg.cn/jnews/3923675.htm
- http://m.wap.ghtkgg.cn/jnews/2008503.htm
- http://m.wap.ghtkgg.cn/jnews/8511.htm
- http://m.wap.ghtkgg.cn/jnews/932346.htm
- http://m.wap.ghtkgg.cn/jnews/9269952.htm
- http://m.wap.ghtkgg.cn/jnews/083491.htm
- http://m.wap.ghtkgg.cn/jnews/939087.htm
- http://m.wap.ghtkgg.cn/jnews/2698359.htm
- http://m.wap.ghtkgg.cn/jnews/76183.htm
- http://m.wap.ghtkgg.cn/jnews/3377.htm
- http://m.wap.ghtkgg.cn/jnews/0245.htm
- http://m.wap.ghtkgg.cn/jnews/562893.htm
- http://m.wap.ghtkgg.cn/jnews/47424.htm
- http://m.wap.ghtkgg.cn/jnews/8357001.htm
- http://m.wap.ghtkgg.cn/jnews/8806.htm
- http://m.wap.ghtkgg.cn/jnews/8245.htm
- http://m.wap.ghtkgg.cn/jnews/595279.htm
- http://m.wap.ghtkgg.cn/jnews/73226.htm
- http://m.wap.ghtkgg.cn/jnews/70822.htm
- http://m.wap.ghtkgg.cn/jnews/6290.htm
- http://m.wap.ghtkgg.cn/jnews/888194.htm
- http://m.wap.ghtkgg.cn/jnews/496199.htm
- http://m.wap.ghtkgg.cn/jnews/4356237.htm
- http://m.wap.ghtkgg.cn/jnews/6488.htm
- http://m.wap.ghtkgg.cn/jnews/3069087.htm
- http://m.wap.ghtkgg.cn/jnews/64558.htm
- http://m.wap.ghtkgg.cn/jnews/0239007.htm
- http://m.wap.ghtkgg.cn/jnews/931906.htm
- http://m.wap.ghtkgg.cn/jnews/0516045.htm
- http://m.wap.ghtkgg.cn/jnews/6604730.htm
- http://m.wap.ghtkgg.cn/jnews/1283.htm
- http://m.wap.ghtkgg.cn/jnews/0972619.htm
- http://m.wap.ghtkgg.cn/jnews/85035.htm
- http://m.wap.ghtkgg.cn/jnews/6203.htm
- http://m.wap.ghtkgg.cn/jnews/5289.htm
- http://m.wap.ghtkgg.cn/jnews/1172800.htm
- http://m.wap.ghtkgg.cn/jnews/8608.htm
- http://m.wap.ghtkgg.cn/jnews/786609.htm
- http://m.wap.ghtkgg.cn/jnews/4689.htm
- http://m.wap.ghtkgg.cn/jnews/2431685.htm
- http://m.wap.ghtkgg.cn/jnews/026688.htm
- http://m.wap.ghtkgg.cn/jnews/773565.htm
- http://m.wap.ghtkgg.cn/jnews/624543.htm
- http://m.wap.ghtkgg.cn/jnews/495365.htm
- http://m.wap.ghtkgg.cn/jnews/6228970.htm
- http://m.wap.ghtkgg.cn/jnews/497554.htm
- http://m.wap.ghtkgg.cn/jnews/97476.htm
- http://m.wap.ghtkgg.cn/jnews/96619.htm
- http://m.wap.ghtkgg.cn/jnews/460374.htm
- http://m.wap.ghtkgg.cn/jnews/1910.htm
- http://m.wap.ghtkgg.cn/jnews/0317.htm
- http://m.wap.ghtkgg.cn/jnews/8013.htm
- http://m.wap.ghtkgg.cn/jnews/6620.htm
- http://m.wap.ghtkgg.cn/jnews/0135.htm
- http://m.wap.ghtkgg.cn/jnews/9763.htm
- http://m.wap.ghtkgg.cn/jnews/4850.htm
- http://m.wap.ghtkgg.cn/jnews/3620687.htm
- http://m.wap.ghtkgg.cn/jnews/972976.htm
- http://m.wap.ghtkgg.cn/jnews/225009.htm
- http://m.wap.ghtkgg.cn/jnews/8664.htm
- http://m.wap.ghtkgg.cn/jnews/6479868.htm
- http://m.wap.ghtkgg.cn/jnews/37591.htm
- http://m.wap.ghtkgg.cn/jnews/362650.htm
- http://m.wap.ghtkgg.cn/jnews/1691302.htm
- http://m.wap.ghtkgg.cn/jnews/383002.htm
- http://m.wap.ghtkgg.cn/jnews/544447.htm
- http://m.wap.ghtkgg.cn/jnews/0505813.htm
- http://m.wap.ghtkgg.cn/jnews/854938.htm
- http://m.wap.ghtkgg.cn/jnews/24514.htm
- http://m.wap.ghtkgg.cn/jnews/997309.htm
- http://m.wap.ghtkgg.cn/jnews/183205.htm
- http://m.wap.ghtkgg.cn/jnews/95121.htm
- http://m.wap.ghtkgg.cn/jnews/9735605.htm
- http://m.wap.ghtkgg.cn/jnews/1994652.htm
- http://m.wap.ghtkgg.cn/jnews/138629.htm
- http://m.wap.ghtkgg.cn/jnews/01869.htm
- http://m.wap.ghtkgg.cn/jnews/4449.htm
- http://m.wap.ghtkgg.cn/jnews/9327.htm
- http://m.wap.ghtkgg.cn/jnews/013574.htm
- http://m.wap.ghtkgg.cn/jnews/7927.htm
- http://m.wap.ghtkgg.cn/jnews/465775.htm
- http://m.wap.ghtkgg.cn/jnews/674624.htm
- http://m.wap.ghtkgg.cn/jnews/6790113.htm
- http://m.wap.ghtkgg.cn/jnews/201365.htm
- http://m.wap.ghtkgg.cn/jnews/431955.htm
- http://m.wap.ghtkgg.cn/jnews/015486.htm
- http://m.wap.ghtkgg.cn/jnews/61217.htm
- http://m.wap.ghtkgg.cn/jnews/21679.htm
- http://m.wap.ghtkgg.cn/jnews/8224.htm
- http://m.wap.ghtkgg.cn/jnews/4121940.htm
- http://m.wap.ghtkgg.cn/jnews/31929.htm
- http://m.wap.ghtkgg.cn/jnews/7502405.htm
- http://m.wap.ghtkgg.cn/jnews/53831.htm
- http://m.wap.ghtkgg.cn/jnews/1784046.htm
- http://m.wap.ghtkgg.cn/jnews/813209.htm
- http://m.wap.ghtkgg.cn/jnews/79889.htm
- http://m.wap.ghtkgg.cn/jnews/694120.htm
- http://m.wap.ghtkgg.cn/jnews/26976.htm
- http://m.wap.ghtkgg.cn/jnews/57007.htm
- http://m.wap.ghtkgg.cn/jnews/233843.htm
- http://m.wap.ghtkgg.cn/jnews/169869.htm
- http://m.wap.ghtkgg.cn/jnews/2727.htm
- http://m.wap.ghtkgg.cn/jnews/195575.htm
- http://m.wap.ghtkgg.cn/jnews/399259.htm
- http://m.wap.ghtkgg.cn/jnews/79596.htm
- http://m.wap.ghtkgg.cn/jnews/89344.htm
- http://m.wap.ghtkgg.cn/jnews/481791.htm
- http://m.wap.ghtkgg.cn/jnews/9312151.htm
- http://m.wap.ghtkgg.cn/jnews/2496.htm
- http://m.wap.ghtkgg.cn/jnews/834917.htm
- http://m.wap.ghtkgg.cn/jnews/41264.htm
- http://m.wap.ghtkgg.cn/jnews/975499.htm
- http://m.wap.ghtkgg.cn/jnews/824910.htm
- http://m.wap.ghtkgg.cn/jnews/3592603.htm
- http://m.wap.ghtkgg.cn/jnews/4097.htm
- http://m.wap.ghtkgg.cn/jnews/8958688.htm
- http://m.wap.ghtkgg.cn/jnews/14507.htm
- http://m.wap.ghtkgg.cn/jnews/122268.htm
- http://m.wap.ghtkgg.cn/jnews/5589612.htm
- http://m.wap.ghtkgg.cn/jnews/4930615.htm
- http://m.wap.ghtkgg.cn/jnews/402410.htm
- http://m.wap.ghtkgg.cn/jnews/931662.htm
- http://m.wap.ghtkgg.cn/jnews/6159.htm
- http://m.wap.ghtkgg.cn/jnews/8890.htm
- http://m.wap.ghtkgg.cn/jnews/22625.htm
- http://m.wap.ghtkgg.cn/jnews/96216.htm
- http://m.wap.ghtkgg.cn/jnews/4796202.htm
- http://m.wap.ghtkgg.cn/jnews/577806.htm
- http://m.wap.ghtkgg.cn/jnews/8289.htm
- http://m.wap.ghtkgg.cn/jnews/62508.htm
- http://m.wap.ghtkgg.cn/jnews/5267.htm
- http://m.wap.ghtkgg.cn/jnews/571297.htm
- http://m.wap.ghtkgg.cn/jnews/6271566.htm
- http://m.wap.ghtkgg.cn/jnews/2480.htm
- http://m.wap.ghtkgg.cn/jnews/182048.htm
- http://m.wap.ghtkgg.cn/jnews/7258.htm
- http://m.wap.ghtkgg.cn/jnews/3452672.htm
- http://m.wap.ghtkgg.cn/jnews/150958.htm
- http://m.wap.ghtkgg.cn/jnews/04677.htm
- http://m.wap.ghtkgg.cn/jnews/2076.htm
- http://m.wap.ghtkgg.cn/jnews/81963.htm
- http://m.wap.ghtkgg.cn/jnews/8778980.htm
- http://m.wap.ghtkgg.cn/jnews/8149526.htm
- http://m.wap.ghtkgg.cn/jnews/41355.htm
- http://m.wap.ghtkgg.cn/jnews/122167.htm
- http://m.wap.ghtkgg.cn/jnews/66508.htm
- http://m.wap.ghtkgg.cn/jnews/578054.htm
- http://m.wap.ghtkgg.cn/jnews/08032.htm
- http://m.wap.ghtkgg.cn/jnews/16597.htm
- http://m.wap.ghtkgg.cn/jnews/3102.htm
- http://m.wap.ghtkgg.cn/jnews/3142.htm
- http://m.wap.ghtkgg.cn/jnews/5651069.htm
- http://m.wap.ghtkgg.cn/jnews/8673.htm
- http://m.wap.ghtkgg.cn/jnews/572993.htm
- http://m.wap.ghtkgg.cn/jnews/988122.htm
- http://m.wap.ghtkgg.cn/jnews/9279527.htm
- http://m.wap.ghtkgg.cn/jnews/4312417.htm
- http://m.wap.ghtkgg.cn/jnews/0924954.htm
- http://m.wap.ghtkgg.cn/jnews/56416.htm
- http://m.wap.ghtkgg.cn/jnews/4939.htm
- http://m.wap.ghtkgg.cn/jnews/373424.htm
- http://m.wap.ghtkgg.cn/jnews/14501.htm
- http://m.wap.ghtkgg.cn/jnews/1640.htm
- http://m.wap.ghtkgg.cn/jnews/8980.htm
- http://m.wap.ghtkgg.cn/jnews/72577.htm
- http://m.wap.ghtkgg.cn/jnews/6360345.htm
- http://m.wap.ghtkgg.cn/jnews/4741245.htm
- http://m.wap.ghtkgg.cn/jnews/18207.htm
- http://m.wap.ghtkgg.cn/jnews/127491.htm
- http://m.wap.ghtkgg.cn/jnews/79216.htm
- http://m.wap.ghtkgg.cn/jnews/6420006.htm
- http://m.wap.ghtkgg.cn/jnews/0114.htm
- http://m.wap.ghtkgg.cn/jnews/381983.htm
- http://m.wap.ghtkgg.cn/jnews/587819.htm
- http://m.wap.ghtkgg.cn/jnews/901339.htm
- http://m.wap.ghtkgg.cn/jnews/2212005.htm
- http://m.wap.ghtkgg.cn/jnews/724523.htm
- http://m.wap.ghtkgg.cn/jnews/74234.htm
- http://m.wap.ghtkgg.cn/jnews/551391.htm
- http://m.wap.ghtkgg.cn/jnews/42168.htm
- http://m.wap.ghtkgg.cn/jnews/5986.htm
- http://m.wap.ghtkgg.cn/jnews/707828.htm
- http://m.wap.ghtkgg.cn/jnews/23566.htm
- http://m.wap.ghtkgg.cn/jnews/6717.htm
- http://m.wap.ghtkgg.cn/jnews/82969.htm
- http://m.wap.ghtkgg.cn/jnews/284682.htm
- http://m.wap.ghtkgg.cn/jnews/4676.htm
- http://m.wap.ghtkgg.cn/jnews/0880434.htm
- http://m.wap.ghtkgg.cn/jnews/794381.htm
- http://m.wap.ghtkgg.cn/jnews/9328496.htm
- http://m.wap.ghtkgg.cn/jnews/8077478.htm
- http://m.wap.ghtkgg.cn/jnews/1145.htm
- http://m.wap.ghtkgg.cn/jnews/835906.htm
- http://m.wap.ghtkgg.cn/jnews/4344419.htm
- http://m.wap.ghtkgg.cn/jnews/3279.htm
- http://m.wap.ghtkgg.cn/jnews/3161884.htm
- http://m.wap.ghtkgg.cn/jnews/1688.htm
- http://m.wap.ghtkgg.cn/jnews/7765874.htm
- http://m.wap.ghtkgg.cn/jnews/8793697.htm
- http://m.wap.ghtkgg.cn/jnews/83977.htm
- http://m.wap.ghtkgg.cn/jnews/187242.htm
- http://m.wap.ghtkgg.cn/jnews/24480.htm
- http://m.wap.ghtkgg.cn/jnews/417309.htm
- http://m.wap.ghtkgg.cn/jnews/6225804.htm
- http://m.wap.ghtkgg.cn/jnews/4592381.htm
- http://m.wap.ghtkgg.cn/jnews/9451.htm
- http://m.wap.ghtkgg.cn/jnews/59458.htm
- http://m.wap.ghtkgg.cn/jnews/4918.htm
- http://m.wap.ghtkgg.cn/jnews/74641.htm
- http://m.wap.ghtkgg.cn/jnews/37683.htm
- http://m.wap.ghtkgg.cn/jnews/9399.htm
- http://m.wap.ghtkgg.cn/jnews/0064372.htm
- http://m.wap.ghtkgg.cn/jnews/6966759.htm
- http://m.wap.ghtkgg.cn/jnews/3776145.htm
- http://m.wap.ghtkgg.cn/jnews/7553944.htm
- http://m.wap.ghtkgg.cn/jnews/13159.htm
- http://m.wap.ghtkgg.cn/jnews/63814.htm
- http://m.wap.ghtkgg.cn/jnews/8120436.htm
- http://m.wap.ghtkgg.cn/jnews/3134661.htm
- http://m.wap.ghtkgg.cn/jnews/490279.htm
- http://m.wap.ghtkgg.cn/jnews/4570.htm
- http://m.wap.ghtkgg.cn/jnews/3560.htm
- http://m.wap.ghtkgg.cn/jnews/932472.htm
- http://m.wap.ghtkgg.cn/jnews/71514.htm
- http://m.wap.ghtkgg.cn/jnews/6165.htm
- http://m.wap.ghtkgg.cn/jnews/806577.htm
- http://m.wap.ghtkgg.cn/jnews/17000.htm
- http://m.wap.ghtkgg.cn/jnews/866961.htm
- http://m.wap.ghtkgg.cn/jnews/966798.htm
- http://m.wap.ghtkgg.cn/jnews/5552.htm
- http://m.wap.ghtkgg.cn/jnews/0659.htm
- http://m.wap.ghtkgg.cn/jnews/807829.htm
- http://m.wap.ghtkgg.cn/jnews/9663703.htm
- http://m.wap.ghtkgg.cn/jnews/8249900.htm
- http://m.wap.ghtkgg.cn/jnews/4106298.htm
- http://m.wap.ghtkgg.cn/jnews/7791512.htm
- http://m.wap.ghtkgg.cn/jnews/09371.htm
- http://m.wap.ghtkgg.cn/jnews/5617.htm
- http://m.wap.ghtkgg.cn/jnews/0796689.htm
- http://m.wap.ghtkgg.cn/jnews/97207.htm
- http://m.wap.ghtkgg.cn/jnews/08183.htm
- http://m.wap.ghtkgg.cn/jnews/139007.htm
- http://m.wap.ghtkgg.cn/jnews/9722.htm
- http://m.wap.ghtkgg.cn/jnews/81470.htm
- http://m.wap.ghtkgg.cn/jnews/8032364.htm
- http://m.wap.ghtkgg.cn/jnews/266092.htm
- http://m.wap.ghtkgg.cn/jnews/6755573.htm
- http://m.wap.ghtkgg.cn/jnews/9800862.htm
- http://m.wap.ghtkgg.cn/jnews/4844670.htm
- http://m.wap.ghtkgg.cn/jnews/07929.htm
- http://m.wap.ghtkgg.cn/jnews/785260.htm
- http://m.wap.ghtkgg.cn/jnews/09775.htm

## 项目结构

```
jnews-link-aggregator/
├── run_aggregator.py          # 项目入口脚本，解析命令行参数并启动采集流程
├── requirements.txt           # Python 依赖声明文件，锁定所有第三方库版本
├── config/
│   ├── settings.yaml          # 主配置文件，包含请求头、超时、重试与调度参数
│   └── extractors.yaml        # 元数据提取规则配置，定义 CSS 选择器与 XPath 映射
├── core/
│   ├── __init__.py
│   ├── fetcher.py             # 页面抓取模块，负责发送请求与获取响应内容
│   ├── parser.py              # HTML 解析模块，调用 beautifulsoup4 提取结构化数据
│   ├── checker.py             # 链接状态检查模块，执行 HEAD 请求并记录状态码
│   └── deduplicator.py        # 去重模块，基于 URL 数字 ID 实现内存与文件双重去重
├── scheduler/
│   ├── __init__.py
│   ├── task_manager.py        # 任务管理器，注册定时任务并维护执行队列
│   └── job_factory.py         # 作业工厂类，生成不同采集策略的作业实例
├── exporters/
│   ├── __init__.py
│   ├── json_exporter.py       # JSON 格式导出器，支持缩进与流式写入
│   ├── csv_exporter.py        # CSV 格式导出器，兼容 Excel 与数据库导入
│   └── markdown_exporter.py   # Markdown 表格导出器，用于生成可读性报告
├── utils/
│   ├── __init__.py
│   ├── logger.py              # 日志工具，按日期轮转并支持多级别输出
│   ├── url_normalizer.py      # URL 规范化工具，处理协议缺失、大小写与尾部斜杠
│   └── file_rotator.py        # 文件轮转工具，自动归档旧数据并保留最近 N 个版本
├── tests/
│   ├── __init__.py
│   ├── test_fetcher.py        # 抓取模块的单元测试，包含 mock 与 fixtures
│   └── test_deduplicator.py   # 去重模块的单元测试，覆盖边界条件与并发场景
├── docs/
│   ├── getting-started.md     # 入门指南，涵盖安装、配置与首次运行
│   ├── configuration.md       # 配置手册，详细解释所有可调参数
│   ├── development.md         # 开发指南，说明扩展点与提交规范
│   └── api-reference.md       # API 文档，自动生成的核心类与方法说明
└── output/                    # 默认输出目录，存放采集结果与日志文件（自动创建）
```

## 贡献指南

1. 阅读项目文档与代码风格规范：在提交代码之前，请仔细阅读 docs/development.md 中的编码约定与 Git 提交信息格式要求，确保新增代码与现有架构保持一致。

2. 选择或创建 Issue 并分配给自己：前往 GitHub Issues 页面查看待办任务，选择尚未被认领的问题或提出新的改进建议，并在评论区中表明您将负责该任务的开发。

3. 创建功能分支并实现变更：从 main 分支拉取最新的开发基准，新建以 feature/ 或 fix/ 为前缀的分支，在本地完成代码编写与单元测试，确保所有原有测试用例均通过。

4. 运行完整测试套件并自检：在提交 Pull Request 之前，执行 pytest tests/ 命令运行全部测试，同时使用 flake8 和 mypy 进行静态类型检查，修复所有警告与错误。

5. 提交 Pull Request 并等待评审：将分支推送至远程仓库后，创建 Pull Request 并填写变更摘要，关联相关的 Issue 编号。项目维护者会在三个工作日内给出评审意见。

## 常见问题

问：采集过程中遇到 HTTP 403 禁止访问错误，应如何解决？

答：该错误通常表明目标站点启用了反爬虫策略。请检查 config/settings.yaml 中的 User-Agent 配置，将其替换为最新的移动端浏览器 UA 字符串。同时，可适当增加请求间隔时间（建议设置为 3 至 5 秒）并启用随机延迟功能，以降低被识别为自动化工具的风险。如果问题持续存在，可尝试通过配置代理服务器列表实现 IP 轮转。

问：链接状态检查显示大量超时，但浏览器中可以正常访问，原因是什么？

答：超时问题多由网络环境或请求参数不当引起。请确认系统防火墙或代理设置未屏蔽目标域名，并检查 config/settings.yaml 中的连接超时与读取超时参数，建议将超时阈值从默认的 10 秒调整为 30 秒。此外，部分移动站点对 HTTP/1.1 的 Keep-Alive 支持不完善，可尝试在请求头中显式设置 Connection: close 以强制每次独立建立连接。

问：如何将采集结果增量更新到已有的数据文件中，避免重复写入？

答：您可以使用 --mode append 参数启动采集器，该模式会先读取目标输出文件中的已有链接 ID 集合，在采集过程中自动过滤掉已存在的条目，仅将新增链接追加至文件末尾。同时，去重模块会基于内存缓存进行二次校验，确保即使在并发写入场景下也不会产生重复数据。如需完全覆盖旧数据，请使用 --mode overwrite 参数。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
