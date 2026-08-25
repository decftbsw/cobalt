# WebIndex Resource Aggregator

WebIndex Resource Aggregator 是一个轻量级的技术信息导航与外部资源链接汇总工具，专为开发者、技术研究员及信息分析人员设计，用于系统化收集、分类展示和快速检索来自特定数据源的海量条目型链接。该项目不依赖复杂的前端框架，以纯静态文档为核心，提供高可读性的资源索引视图，适用于个人知识库构建、数据源归档或自动化信息采集管道的前端展示层。

项目定位于解决以下问题：当用户需要处理来自同一域名下大量结构相似的内容页面（如编号型新闻、公告或技术笔记）时，缺乏一个统一的本地索引入口来管理这些分散的 URL。WebIndex 通过提供标准化的文档模板、自动化构建脚本和清晰的项目导航，帮助用户将原始链接列表转化为可维护、可扩展的技术资源站。

## 功能概览

**批量链接导入与规范化**：支持从纯文本、CSV 或 JSON 格式的源文件中批量读取 URL，自动去重并按照域名与路径结构进行初步分类，生成统一的资源清单。

**多维度标签筛选系统**：每条资源可关联多个自定义标签（如协议类型、内容主题、数据批次），内置标签云模块允许用户按标签快速过滤目标链接。

**响应式静态页面生成**：基于模板引擎将资源数据渲染为适配桌面与移动终端的 HTML 页面，无需数据库支持，所有页面可部署于任意 HTTP 服务器或 CDN。

**链接状态健康检查**：集成可选的定时任务模块，对已收录 URL 发送 HEAD 请求，检测响应状态码并标记失效或重定向链接，辅助维护资源有效性。

**全文模糊搜索**：针对 URL 中的文件名、数字编号及路径关键词提供简单的客户端搜索功能，支持大小写不敏感的模糊匹配，便于在海量链接中定位特定条目。

**项目元数据管理**：自动生成包含资源总数、最后更新时间、批次编号（当前为第 104/300 批）的统计看板，方便用户掌握整体数据规模。

**导出与备份机制**：支持将当前索引数据导出为 Markdown 表格、JSON 或 YAML 格式，便于版本控制或迁移至其他数据分析工具。

**插件化钩子系统**：允许高级用户通过编写 Python 脚本在链接导入或页面渲染前后执行自定义逻辑，如字段转换、外部 API 调用或本地文件预处理。

## 应用场景

**技术文档归档与检索**：开发团队可将项目用于整理内部技术分享的会议纪要链接、代码审查记录或故障排查日志，通过统一的索引页面快速回溯历史内容。每日新增的链接按批次编号自动归入对应目录，降低人工整理成本。

**数据源监控与变化追踪**：数据分析师可定期将特定来源的编号型资源链接导入本系统，配合健康检查功能监控目标页面是否可访问，并结合导出功能生成可用性报告。当链接状态发生变化时，系统输出差异日志辅助分析。

**知识库外链管理中心**：个人知识管理爱好者可使用 WebIndex 作为外部参考链接的中央注册表，为每个收录 URL 标注主题领域、收录理由和阅读优先级，构建个人化的学习资源导航站。所有数据以纯文本形式存储，兼容 Obsidian、Notion 等主流笔记工具。

**自动化采集管道前端展示**：在爬虫或数据采集流程中，WebIndex 可作为最终输出环节的展示层，将采集到的原始链接列表渲染为人类可读的 HTML 索引，替代直接暴露 JSON 或日志文件的方式，提升交付物的专业性。

## 快速开始

以下命令演示了从 GitHub 克隆项目、安装依赖并启动开发服务器的完整流程。

```bash
git clone https://github.com/webindex/webindex-agg.git
cd webindex-agg
pip install -r requirements.txt
python build.py --input ./data/raw_links.txt --output ./dist --batch 104
python server.py --port 8080
```

执行上述命令后，访问 http://localhost:8080 即可查看生成的资源索引页面。如需自定义模板或修改分类规则，请参考 `docs/customization.md` 中的详细说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心构建脚本与服务器运行环境 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装依赖库 |
| Jinja2 | 3.0.x | 模板渲染引擎，负责生成 HTML 页面 |
| requests | 2.28.x | 用于链接状态健康检查的 HTTP 客户端 |
| pytest | 7.0.x | 单元测试框架（仅开发环境必需） |
| markdown | 3.4.x | 将 Markdown 格式的文档说明转换为 HTML |
| pyyaml | 6.0.x | 解析 YAML 格式的配置文件与元数据 |
| watchdog | 2.3.x | 文件系统监控，用于开发模式下的自动重建（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | `docs/quickstart.md` | 如何最快运行项目并生成第一批索引页面？ |
| 配置手册 | `docs/configuration.md` | 如何修改分类规则、自定义标签和页面标题？ |
| 模板开发 | `docs/templating.md` | 如何编写或修改 Jinja2 模板以改变页面布局？ |
| 插件编写 | `docs/plugins.md` | 如何通过钩子系统扩展导入、渲染或导出流程？ |
| API 参考 | `docs/api_reference.md` | 各核心模块的函数签名、参数说明与返回值定义 |
| 故障排除 | `docs/troubleshooting.md` | 遇到构建失败、链接检查超时等问题时的解决方案 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/09381.htm
- http://m.3g.ghtkgg.cn/nnews/29368.htm
- http://m.3g.ghtkgg.cn/nnews/7015464.htm
- http://m.3g.ghtkgg.cn/nnews/94970.htm
- http://m.3g.ghtkgg.cn/nnews/98612.htm
- http://m.3g.ghtkgg.cn/nnews/052845.htm
- http://m.3g.ghtkgg.cn/nnews/7531312.htm
- http://m.3g.ghtkgg.cn/nnews/32302.htm
- http://m.3g.ghtkgg.cn/nnews/582343.htm
- http://m.3g.ghtkgg.cn/nnews/5414309.htm
- http://m.3g.ghtkgg.cn/nnews/487857.htm
- http://m.3g.ghtkgg.cn/nnews/69665.htm
- http://m.3g.ghtkgg.cn/nnews/07293.htm
- http://m.3g.ghtkgg.cn/nnews/525395.htm
- http://m.3g.ghtkgg.cn/nnews/947746.htm
- http://m.3g.ghtkgg.cn/nnews/879532.htm
- http://m.3g.ghtkgg.cn/nnews/1875.htm
- http://m.3g.ghtkgg.cn/nnews/13891.htm
- http://m.3g.ghtkgg.cn/nnews/061900.htm
- http://m.3g.ghtkgg.cn/nnews/7986027.htm
- http://m.3g.ghtkgg.cn/nnews/2370364.htm
- http://m.3g.ghtkgg.cn/nnews/9778028.htm
- http://m.3g.ghtkgg.cn/nnews/4628.htm
- http://m.3g.ghtkgg.cn/nnews/6015956.htm
- http://m.3g.ghtkgg.cn/nnews/419515.htm
- http://m.3g.ghtkgg.cn/nnews/25926.htm
- http://m.3g.ghtkgg.cn/nnews/3072015.htm
- http://m.3g.ghtkgg.cn/nnews/856975.htm
- http://m.3g.ghtkgg.cn/nnews/58597.htm
- http://m.3g.ghtkgg.cn/nnews/7688011.htm
- http://m.3g.ghtkgg.cn/nnews/87908.htm
- http://m.3g.ghtkgg.cn/nnews/969371.htm
- http://m.3g.ghtkgg.cn/nnews/2870977.htm
- http://m.3g.ghtkgg.cn/nnews/1682.htm
- http://m.3g.ghtkgg.cn/nnews/13311.htm
- http://m.3g.ghtkgg.cn/nnews/752893.htm
- http://m.3g.ghtkgg.cn/nnews/7031.htm
- http://m.3g.ghtkgg.cn/nnews/828860.htm
- http://m.3g.ghtkgg.cn/nnews/2040.htm
- http://m.3g.ghtkgg.cn/nnews/0479.htm
- http://m.3g.ghtkgg.cn/nnews/8246651.htm
- http://m.3g.ghtkgg.cn/nnews/8808.htm
- http://m.3g.ghtkgg.cn/nnews/0296107.htm
- http://m.3g.ghtkgg.cn/nnews/97537.htm
- http://m.3g.ghtkgg.cn/nnews/477211.htm
- http://m.3g.ghtkgg.cn/nnews/3470986.htm
- http://m.3g.ghtkgg.cn/nnews/354459.htm
- http://m.3g.ghtkgg.cn/nnews/9582.htm
- http://m.3g.ghtkgg.cn/nnews/4998299.htm
- http://m.3g.ghtkgg.cn/nnews/4361.htm
- http://m.3g.ghtkgg.cn/nnews/63851.htm
- http://m.3g.ghtkgg.cn/nnews/15951.htm
- http://m.3g.ghtkgg.cn/nnews/4716.htm
- http://m.3g.ghtkgg.cn/nnews/141545.htm
- http://m.3g.ghtkgg.cn/nnews/830084.htm
- http://m.3g.ghtkgg.cn/nnews/9200145.htm
- http://m.3g.ghtkgg.cn/nnews/4017.htm
- http://m.3g.ghtkgg.cn/nnews/940254.htm
- http://m.3g.ghtkgg.cn/nnews/47522.htm
- http://m.3g.ghtkgg.cn/nnews/0307108.htm
- http://m.3g.ghtkgg.cn/nnews/519928.htm
- http://m.3g.ghtkgg.cn/nnews/83035.htm
- http://m.3g.ghtkgg.cn/nnews/899614.htm
- http://m.3g.ghtkgg.cn/nnews/4554304.htm
- http://m.3g.ghtkgg.cn/nnews/185769.htm
- http://m.3g.ghtkgg.cn/nnews/100961.htm
- http://m.3g.ghtkgg.cn/nnews/3488.htm
- http://m.3g.ghtkgg.cn/nnews/8180.htm
- http://m.3g.ghtkgg.cn/nnews/6751.htm
- http://m.3g.ghtkgg.cn/nnews/213765.htm
- http://m.3g.ghtkgg.cn/nnews/02913.htm
- http://m.3g.ghtkgg.cn/nnews/381428.htm
- http://m.3g.ghtkgg.cn/nnews/1562966.htm
- http://m.3g.ghtkgg.cn/nnews/9837433.htm
- http://m.3g.ghtkgg.cn/nnews/68689.htm
- http://m.3g.ghtkgg.cn/nnews/525118.htm
- http://m.3g.ghtkgg.cn/nnews/7444248.htm
- http://m.3g.ghtkgg.cn/nnews/986958.htm
- http://m.3g.ghtkgg.cn/nnews/3414861.htm
- http://m.3g.ghtkgg.cn/nnews/016538.htm
- http://m.3g.ghtkgg.cn/nnews/3452.htm
- http://m.3g.ghtkgg.cn/nnews/50551.htm
- http://m.3g.ghtkgg.cn/nnews/5218043.htm
- http://m.3g.ghtkgg.cn/nnews/11988.htm
- http://m.3g.ghtkgg.cn/nnews/0707.htm
- http://m.3g.ghtkgg.cn/nnews/242100.htm
- http://m.3g.ghtkgg.cn/nnews/3672.htm
- http://m.3g.ghtkgg.cn/nnews/3189442.htm
- http://m.3g.ghtkgg.cn/nnews/851053.htm
- http://m.3g.ghtkgg.cn/nnews/58193.htm
- http://m.3g.ghtkgg.cn/nnews/2239421.htm
- http://m.3g.ghtkgg.cn/nnews/657746.htm
- http://m.3g.ghtkgg.cn/nnews/71928.htm
- http://m.3g.ghtkgg.cn/nnews/2244247.htm
- http://m.3g.ghtkgg.cn/nnews/767616.htm
- http://m.3g.ghtkgg.cn/nnews/2778122.htm
- http://m.3g.ghtkgg.cn/nnews/7570.htm
- http://m.3g.ghtkgg.cn/nnews/06319.htm
- http://m.3g.ghtkgg.cn/nnews/960080.htm
- http://m.3g.ghtkgg.cn/nnews/7438164.htm
- http://m.3g.ghtkgg.cn/nnews/32917.htm
- http://m.3g.ghtkgg.cn/nnews/8799874.htm
- http://m.3g.ghtkgg.cn/nnews/3065.htm
- http://m.3g.ghtkgg.cn/nnews/2484074.htm
- http://m.3g.ghtkgg.cn/nnews/085693.htm
- http://m.3g.ghtkgg.cn/nnews/3061.htm
- http://m.3g.ghtkgg.cn/nnews/481301.htm
- http://m.3g.ghtkgg.cn/nnews/24333.htm
- http://m.3g.ghtkgg.cn/nnews/0929.htm
- http://m.3g.ghtkgg.cn/nnews/347644.htm
- http://m.3g.ghtkgg.cn/nnews/691973.htm
- http://m.3g.ghtkgg.cn/nnews/73410.htm
- http://m.3g.ghtkgg.cn/nnews/6833546.htm
- http://m.3g.ghtkgg.cn/nnews/940058.htm
- http://m.3g.ghtkgg.cn/nnews/98582.htm
- http://m.3g.ghtkgg.cn/nnews/6311.htm
- http://m.3g.ghtkgg.cn/nnews/87517.htm
- http://m.3g.ghtkgg.cn/nnews/2797.htm
- http://m.3g.ghtkgg.cn/nnews/706025.htm
- http://m.3g.ghtkgg.cn/nnews/50430.htm
- http://m.3g.ghtkgg.cn/nnews/742165.htm
- http://m.3g.ghtkgg.cn/nnews/8894201.htm
- http://m.3g.ghtkgg.cn/nnews/4862.htm
- http://m.3g.ghtkgg.cn/nnews/70640.htm
- http://m.3g.ghtkgg.cn/nnews/4335.htm
- http://m.3g.ghtkgg.cn/nnews/4573565.htm
- http://m.3g.ghtkgg.cn/nnews/04408.htm
- http://m.3g.ghtkgg.cn/nnews/3552.htm
- http://m.3g.ghtkgg.cn/nnews/6344.htm
- http://m.3g.ghtkgg.cn/nnews/4770240.htm
- http://m.3g.ghtkgg.cn/nnews/718835.htm
- http://m.3g.ghtkgg.cn/nnews/943547.htm
- http://m.3g.ghtkgg.cn/nnews/6999826.htm
- http://m.3g.ghtkgg.cn/nnews/1999.htm
- http://m.3g.ghtkgg.cn/nnews/9082.htm
- http://m.3g.ghtkgg.cn/nnews/16989.htm
- http://m.3g.ghtkgg.cn/nnews/380549.htm
- http://m.3g.ghtkgg.cn/nnews/23380.htm
- http://m.3g.ghtkgg.cn/nnews/52056.htm
- http://m.3g.ghtkgg.cn/nnews/7749.htm
- http://m.3g.ghtkgg.cn/nnews/0738072.htm
- http://m.3g.ghtkgg.cn/nnews/345552.htm
- http://m.3g.ghtkgg.cn/nnews/64387.htm
- http://m.3g.ghtkgg.cn/nnews/1835.htm
- http://m.3g.ghtkgg.cn/nnews/0067.htm
- http://m.3g.ghtkgg.cn/nnews/032319.htm
- http://m.3g.ghtkgg.cn/nnews/0807.htm
- http://m.3g.ghtkgg.cn/nnews/34356.htm
- http://m.3g.ghtkgg.cn/nnews/5475278.htm
- http://m.3g.ghtkgg.cn/nnews/464090.htm
- http://m.3g.ghtkgg.cn/nnews/70338.htm
- http://m.3g.ghtkgg.cn/nnews/173215.htm
- http://m.3g.ghtkgg.cn/nnews/5354951.htm
- http://m.3g.ghtkgg.cn/nnews/1306626.htm
- http://m.3g.ghtkgg.cn/nnews/85387.htm
- http://m.3g.ghtkgg.cn/nnews/9365.htm
- http://m.3g.ghtkgg.cn/nnews/29755.htm
- http://m.3g.ghtkgg.cn/nnews/1191.htm
- http://m.3g.ghtkgg.cn/nnews/4763.htm
- http://m.3g.ghtkgg.cn/nnews/7085920.htm
- http://m.3g.ghtkgg.cn/nnews/20962.htm
- http://m.3g.ghtkgg.cn/nnews/622144.htm
- http://m.3g.ghtkgg.cn/nnews/2447383.htm
- http://m.3g.ghtkgg.cn/nnews/156908.htm
- http://m.3g.ghtkgg.cn/nnews/770054.htm
- http://m.3g.ghtkgg.cn/nnews/6815477.htm
- http://m.3g.ghtkgg.cn/nnews/5076951.htm
- http://m.3g.ghtkgg.cn/nnews/0081319.htm
- http://m.3g.ghtkgg.cn/nnews/3851984.htm
- http://m.3g.ghtkgg.cn/nnews/800706.htm
- http://m.3g.ghtkgg.cn/nnews/57200.htm
- http://m.3g.ghtkgg.cn/nnews/920399.htm
- http://m.3g.ghtkgg.cn/nnews/943223.htm
- http://m.3g.ghtkgg.cn/nnews/108071.htm
- http://m.3g.ghtkgg.cn/nnews/2708.htm
- http://m.3g.ghtkgg.cn/nnews/87450.htm
- http://m.3g.ghtkgg.cn/nnews/2670.htm
- http://m.3g.ghtkgg.cn/nnews/628012.htm
- http://m.3g.ghtkgg.cn/nnews/5578610.htm
- http://m.3g.ghtkgg.cn/nnews/29340.htm
- http://m.3g.ghtkgg.cn/nnews/2532.htm
- http://m.3g.ghtkgg.cn/nnews/093823.htm
- http://m.3g.ghtkgg.cn/nnews/560134.htm
- http://m.3g.ghtkgg.cn/nnews/2832269.htm
- http://m.3g.ghtkgg.cn/nnews/203564.htm
- http://m.3g.ghtkgg.cn/nnews/27677.htm
- http://m.3g.ghtkgg.cn/nnews/729349.htm
- http://m.3g.ghtkgg.cn/nnews/1805747.htm
- http://m.3g.ghtkgg.cn/nnews/56336.htm
- http://m.3g.ghtkgg.cn/nnews/70405.htm
- http://m.3g.ghtkgg.cn/nnews/967420.htm
- http://m.3g.ghtkgg.cn/nnews/8805.htm
- http://m.3g.ghtkgg.cn/nnews/48423.htm
- http://m.3g.ghtkgg.cn/nnews/0485679.htm
- http://m.3g.ghtkgg.cn/nnews/47328.htm
- http://m.3g.ghtkgg.cn/nnews/3591872.htm
- http://m.3g.ghtkgg.cn/nnews/0573.htm
- http://m.3g.ghtkgg.cn/nnews/78606.htm
- http://m.3g.ghtkgg.cn/nnews/112106.htm
- http://m.3g.ghtkgg.cn/nnews/681830.htm
- http://m.3g.ghtkgg.cn/nnews/2043.htm
- http://m.3g.ghtkgg.cn/nnews/2819.htm
- http://m.3g.ghtkgg.cn/nnews/8860039.htm
- http://m.3g.ghtkgg.cn/nnews/712365.htm
- http://m.3g.ghtkgg.cn/nnews/0058654.htm
- http://m.3g.ghtkgg.cn/nnews/894543.htm
- http://m.3g.ghtkgg.cn/nnews/92256.htm
- http://m.3g.ghtkgg.cn/nnews/130373.htm
- http://m.3g.ghtkgg.cn/nnews/4391.htm
- http://m.3g.ghtkgg.cn/nnews/276439.htm
- http://m.3g.ghtkgg.cn/nnews/6208.htm
- http://m.3g.ghtkgg.cn/nnews/381358.htm
- http://m.3g.ghtkgg.cn/nnews/5613814.htm
- http://m.3g.ghtkgg.cn/nnews/703884.htm
- http://m.3g.ghtkgg.cn/nnews/401522.htm
- http://m.3g.ghtkgg.cn/nnews/70823.htm
- http://m.3g.ghtkgg.cn/nnews/474248.htm
- http://m.3g.ghtkgg.cn/nnews/7544.htm
- http://m.3g.ghtkgg.cn/nnews/6346.htm
- http://m.3g.ghtkgg.cn/nnews/8082749.htm
- http://m.3g.ghtkgg.cn/nnews/40958.htm
- http://m.3g.ghtkgg.cn/nnews/0835598.htm
- http://m.3g.ghtkgg.cn/nnews/419830.htm
- http://m.3g.ghtkgg.cn/nnews/6045.htm
- http://m.3g.ghtkgg.cn/nnews/6724472.htm
- http://m.3g.ghtkgg.cn/nnews/20780.htm
- http://m.3g.ghtkgg.cn/nnews/2083.htm
- http://m.3g.ghtkgg.cn/nnews/051473.htm
- http://m.3g.ghtkgg.cn/nnews/518230.htm
- http://m.3g.ghtkgg.cn/nnews/85552.htm
- http://m.3g.ghtkgg.cn/nnews/900138.htm
- http://m.3g.ghtkgg.cn/nnews/8735376.htm
- http://m.3g.ghtkgg.cn/nnews/4842683.htm
- http://m.3g.ghtkgg.cn/nnews/2140949.htm
- http://m.3g.ghtkgg.cn/nnews/84660.htm
- http://m.3g.ghtkgg.cn/nnews/8692.htm
- http://m.3g.ghtkgg.cn/nnews/3870747.htm
- http://m.3g.ghtkgg.cn/nnews/1829.htm
- http://m.3g.ghtkgg.cn/nnews/487207.htm
- http://m.3g.ghtkgg.cn/nnews/0019515.htm
- http://m.3g.ghtkgg.cn/nnews/9156.htm
- http://m.3g.ghtkgg.cn/nnews/488679.htm
- http://m.3g.ghtkgg.cn/nnews/37688.htm
- http://m.3g.ghtkgg.cn/nnews/7022735.htm
- http://m.3g.ghtkgg.cn/nnews/473018.htm
- http://m.3g.ghtkgg.cn/nnews/4827769.htm
- http://m.3g.ghtkgg.cn/nnews/6445076.htm
- http://m.3g.ghtkgg.cn/nnews/509399.htm
- http://m.3g.ghtkgg.cn/nnews/4184.htm
- http://m.3g.ghtkgg.cn/nnews/3770.htm
- http://m.3g.ghtkgg.cn/nnews/62350.htm
- http://m.3g.ghtkgg.cn/nnews/0953.htm
- http://m.3g.ghtkgg.cn/nnews/9402767.htm
- http://m.3g.ghtkgg.cn/nnews/6957226.htm
- http://m.3g.ghtkgg.cn/nnews/1099.htm
- http://m.3g.ghtkgg.cn/nnews/187711.htm
- http://m.3g.ghtkgg.cn/nnews/0627.htm
- http://m.3g.ghtkgg.cn/nnews/5480.htm
- http://m.3g.ghtkgg.cn/nnews/9894608.htm
- http://m.3g.ghtkgg.cn/nnews/64553.htm
- http://m.3g.ghtkgg.cn/nnews/22588.htm
- http://m.3g.ghtkgg.cn/nnews/7079895.htm
- http://m.3g.ghtkgg.cn/nnews/1304386.htm
- http://m.3g.ghtkgg.cn/nnews/52856.htm
- http://m.3g.ghtkgg.cn/nnews/703871.htm
- http://m.3g.ghtkgg.cn/nnews/34404.htm
- http://m.3g.ghtkgg.cn/nnews/8561.htm
- http://m.3g.ghtkgg.cn/nnews/0823240.htm
- http://m.3g.ghtkgg.cn/nnews/6349893.htm
- http://m.3g.ghtkgg.cn/nnews/5028.htm
- http://m.3g.ghtkgg.cn/nnews/2308909.htm
- http://m.3g.ghtkgg.cn/nnews/1510421.htm
- http://m.3g.ghtkgg.cn/nnews/5394.htm
- http://m.3g.ghtkgg.cn/nnews/4571867.htm
- http://m.3g.ghtkgg.cn/nnews/7395.htm
- http://m.3g.ghtkgg.cn/nnews/471392.htm
- http://m.3g.ghtkgg.cn/nnews/95828.htm
- http://m.3g.ghtkgg.cn/nnews/8417.htm
- http://m.3g.ghtkgg.cn/nnews/1844.htm
- http://m.3g.ghtkgg.cn/nnews/94893.htm
- http://m.3g.ghtkgg.cn/nnews/1221236.htm
- http://m.3g.ghtkgg.cn/nnews/4207.htm
- http://m.3g.ghtkgg.cn/nnews/426712.htm
- http://m.3g.ghtkgg.cn/nnews/7019.htm
- http://m.3g.ghtkgg.cn/nnews/8716820.htm
- http://m.3g.ghtkgg.cn/nnews/076910.htm
- http://m.3g.ghtkgg.cn/nnews/2097.htm
- http://m.3g.ghtkgg.cn/nnews/700326.htm
- http://m.3g.ghtkgg.cn/nnews/4581.htm
- http://m.3g.ghtkgg.cn/nnews/76061.htm
- http://m.3g.ghtkgg.cn/nnews/528810.htm
- http://m.3g.ghtkgg.cn/nnews/6924782.htm
- http://m.3g.ghtkgg.cn/nnews/06606.htm
- http://m.3g.ghtkgg.cn/nnews/718831.htm
- http://m.3g.ghtkgg.cn/nnews/3346.htm
- http://m.3g.ghtkgg.cn/nnews/468263.htm
- http://m.3g.ghtkgg.cn/nnews/063682.htm
- http://m.3g.ghtkgg.cn/nnews/4287.htm
- http://m.3g.ghtkgg.cn/nnews/93746.htm
- http://m.3g.ghtkgg.cn/nnews/62313.htm

## 项目结构

```
webindex-agg/
├── build.py                 # 主构建脚本，负责读取数据、渲染模板并输出静态页面
├── server.py                # 开发阶段使用的轻量级 HTTP 服务器，支持热加载
├── requirements.txt         # Python 依赖清单，包含 Jinja2、requests 等核心库
├── config.yaml              # 全局配置文件，定义站点标题、分类映射、标签别名等
├── data/                    # 数据存储目录，存放原始链接列表与处理后的索引文件
│   ├── raw/                 # 原始输入目录，可放置 .txt、.csv 或 .json 格式的链接源文件
│   ├── parsed/              # 解析后的标准化数据，按批次编号（如 batch_104.json）组织
│   └── cache/               # 链接状态检查的缓存文件，避免重复请求相同 URL
├── src/                     # 核心源代码目录
│   ├── loader.py            # 链接加载器，支持多种输入格式解析与字段映射
│   ├── parser.py            # URL 解析器，提取域名、路径、文件名及数字编号
│   ├── checker.py           # 健康检查模块，并发发送 HEAD 请求并记录状态码
│   ├── indexer.py           # 索引构建器，生成倒排标签映射与搜索数据结构
│   └── exporter.py          # 导出模块，支持 Markdown、JSON、YAML 等格式输出
├── templates/               # Jinja2 HTML 模板目录
│   ├── base.html            # 基础布局模板，定义全局导航与页脚
│   ├── index.html           # 资源列表首页模板，展示所有链接及标签云
│   ├── detail.html          # 单条资源详情页模板（预留，当前未启用）
│   └── stats.html           # 统计看板模板，显示资源总数、批次信息等
├── static/                  # 静态资源目录，包含 CSS 样式与 JavaScript 脚本
│   ├── style.css            # 响应式布局样式，适配桌面与移动端
│   └── search.js            # 客户端全文搜索脚本，实现模糊匹配与结果高亮
├── tests/                   # 单元测试目录，使用 pytest 框架
│   ├── test_loader.py       # 测试数据加载器的各类输入格式解析
│   ├── test_parser.py       # 测试 URL 解析逻辑的准确性与边界情况
│   └── test_checker.py      # 测试健康检查模块的并发控制与超时处理
├── docs/                    # 项目文档目录，包含入门指南、配置手册等
│   ├── quickstart.md
│   ├── configuration.md
│   ├── templating.md
│   ├── plugins.md
│   ├── api_reference.md
│   └── troubleshooting.md
├── scripts/                 # 辅助脚本目录
│   ├── import_from_csv.py   # 从外部 CSV 文件导入链接的独立脚本
│   └── batch_rename.py      # 批量重命名或更新链接编号的辅助工具
└── .gitignore               # Git 忽略文件配置，排除缓存、临时文件与敏感配置
```

## 贡献指南

**报告问题或建议新功能**：请使用 GitHub Issues 提交详细的错误描述或功能请求。包含复现步骤、预期行为与实际行为的对比，以及相关日志或截图。对于功能请求，请清晰说明使用场景和预期收益。

**提交代码变更**：Fork 本仓库并创建新的特性分支（如 `feature/add-json-export`）。遵循 PEP 8 编码规范，确保所有新增代码包含对应的单元测试，且现有测试套件全部通过。提交前运行 `pytest tests/` 进行完整回归测试。

**完善文档或修复拼写错误**：直接编辑 `docs/` 目录下的 Markdown 文件并提交 Pull Request。对于涉及配置或 API 的修改，请同步更新 `config.yaml` 或 `api_reference.md` 中的相关描述。

**增加新的链接源适配器**：在 `src/loader.py` 中注册新的格式解析类（如 XML 或 Excel），并在 `tests/test_loader.py` 中添加对应的测试用例。提交前请确保新适配器已通过所有单元测试，并在 `docs/configuration.md` 中补充配置示例。

**参与讨论与社区支持**：在 GitHub Discussions 中回答其他用户的问题，分享使用经验或提出改进建议。对于重大变更或架构调整，建议先发起 Discussion 或 Issue 进行讨论，再投入开发工作。

## 常见问题

**问：构建脚本报错 `ModuleNotFoundError: No module named 'jinja2'`，如何解决？**

答：该错误表明 Python 环境中未安装所需的依赖包。请确认已执行 `pip install -r requirements.txt`。若使用虚拟环境，请确保虚拟环境已激活。如果仍存在问题，检查 pip 版本是否过旧（`pip install --upgrade pip`），或尝试使用 `pip install --user` 进行用户级安装。

**问：如何更新已收录链接的状态信息？**

答：链接健康检查结果默认存储在 `data/cache/

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:51
