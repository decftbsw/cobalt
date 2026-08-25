# WebLink Navigator

WebLink Navigator 是一个面向技术信息检索与外部资源聚合的轻量级导航工具，专为需要高频访问分散式技术内容（包括博客、新闻、技术文档与行业动态）的开发者、研究人员与技术决策者设计。该项目不提供内容托管或数据存储，而是作为结构化链接网关，将松散分布的优质信息源整合为可版本化、可批处理、可协作维护的链接集合。WebLink Navigator 通过标准化的链接清单与元数据描述，帮助团队或个人建立属于自己的外部知识索引，降低信息遗失与重复查找的成本，同时保持对外部源站的直接引用透明性。项目自身不依赖数据库或后端服务，所有链接记录以静态清单形式存在，兼容主流静态站点生成工具与持续集成流水线，适合作为技术团队内部文档体系的外部补充模块。

## 功能概览

- 批量链接清单导入与去重检测：支持从纯文本、CSV 或结构化 Markdown 列表批量导入外部 URL，自动执行格式规整与重复项识别，输出标准化条目。

- 元数据标签与分类标记：每条链接可附加自定义标签（如 "backend"、"security"、"release-note"）和分类标记，便于按主题或项目阶段进行筛选。

- 链接可用性状态标记：提供手动或半自动化的状态标注机制，用于记录链接是否有效、是否需要代理访问、是否属于存档页面。

- 静态导航页面生成模板：内置简约的 HTML 与 Markdown 混合模板，可将链接清单渲染为可浏览的导航页，支持按标签或按日期排序。

- 变更历史与注释记录：支持为每个链接条目添加变更注释（变更原因、推荐人、检查日期），便于多人协作维护时追溯责任与信息源演变。

- 外部链接关系图导出：可生成简单的依赖关系描述文件（DOT 格式），描述链接之间的引用或逻辑关联，用于可视化分析信息流向。

- 健康检查报告输出：提供脚本工具，定期对清单中的链接发起 HEAD 请求，生成可达性与响应时间报告，标记异常条目。

## 应用场景

技术团队内部文档体系外部链接管理：开发团队在维护项目文档时，需要引用大量外部规范、参考实现或社区讨论链接。WebLink Navigator 可作为子模块嵌入 docs 目录，集中管理这些外部引用，避免链接散落在各个 Markdown 文件中导致维护困难。

技术调研阶段信息源聚合：在进行竞品分析或新技术选型时，研究人员需要收集数十至上百个相关文章、官方公告和性能测试报告。使用 WebLink Navigator 可快速构建调研期链接池，并在调研结束后通过标签筛选保留高价值条目。

个人技术博客的"已阅链接"归档：技术博主或资讯编辑在阅读大量每日资讯后，可将有价值但暂未形成完整文章的材料存入链接清单，并标注阅读状态和初步观点，作为后续写作的素材池。

离线环境下的链接缓存索引：部分内部网络环境无法直接访问外网，但允许通过代理或定时同步更新链接清单。WebLink Navigator 可在此类环境中充当"链接索引说明"，清晰列出所有外部资源地址及其用途描述，供运维人员按需同步。

## 快速开始

以下命令演示如何获取项目代码、安装基础依赖并启动本地预览服务。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
pip install -r requirements.txt
python scripts/build_index.py --input ./links/master_list.txt --output ./dist/index.html
python -m http.server 8080 --directory ./dist
```

执行完毕后，访问 http://localhost:8080 即可查看当前链接清单生成的静态导航页面。如需更新清单内容，直接编辑 links/master_list.txt 文件后重新运行 build_index.py 脚本。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心脚本运行环境，用于链接处理与页面生成 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装依赖库 |
| requests | 2.25.0 及以上 | 用于链接健康检查中的 HTTP 请求发送 |
| markdown | 3.3.0 及以上 | 用于将 Markdown 格式的链接注释渲染为 HTML 描述 |
| PyYAML | 5.4.0 及以上 | 用于解析可选的 YAML 格式元数据配置文件 |
| Git | 2.20.0 及以上 | 用于克隆仓库和版本管理（非运行强制依赖） |
| 操作系统 | Linux / macOS / Windows (WSL推荐) | 跨平台支持，但路径处理在 Windows 原生环境下需注意反斜杠转义 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何首次配置链接清单、如何运行生成脚本、如何查看生成的导航页 |
| 链接清单规范 | docs/link-specification.md | 链接条目的字段定义（URL、标题、标签、状态、注释）、分隔符约定、特殊字符转义规则 |
| 运维与健康检查 | docs/health-check.md | 如何配置定时检查任务、如何解读健康报告、如何处理失效链接 |
| 自定义主题与布局 | docs/custom-theme.md | 如何修改导航页的 CSS 样式、如何调整排序逻辑、如何添加自定义页脚信息 |
| 贡献与协作流程 | docs/contributing.md | 外部贡献者如何提交链接增删改建议、内部审核流程、版本发布节奏 |

## 资源列表

- http://m.blog.oexnr.cn/snews/70183.htm
- http://m.blog.oexnr.cn/snews/3867330.htm
- http://m.blog.oexnr.cn/snews/00559.htm
- http://m.blog.oexnr.cn/snews/128905.htm
- http://m.blog.oexnr.cn/snews/3935294.htm
- http://m.blog.oexnr.cn/snews/6319534.htm
- http://m.blog.oexnr.cn/snews/9551086.htm
- http://m.blog.oexnr.cn/snews/535674.htm
- http://m.blog.oexnr.cn/snews/8491306.htm
- http://m.blog.oexnr.cn/snews/9566.htm
- http://m.blog.oexnr.cn/snews/7759917.htm
- http://m.blog.oexnr.cn/snews/2975.htm
- http://m.blog.oexnr.cn/snews/75945.htm
- http://m.blog.oexnr.cn/snews/19792.htm
- http://m.blog.oexnr.cn/snews/5211321.htm
- http://m.blog.oexnr.cn/snews/0208.htm
- http://m.blog.oexnr.cn/snews/21425.htm
- http://m.blog.oexnr.cn/snews/886040.htm
- http://m.blog.oexnr.cn/snews/9174292.htm
- http://m.blog.oexnr.cn/snews/137259.htm
- http://m.blog.oexnr.cn/snews/9517823.htm
- http://m.blog.oexnr.cn/snews/5147.htm
- http://m.blog.oexnr.cn/snews/02759.htm
- http://m.blog.oexnr.cn/snews/178503.htm
- http://m.blog.oexnr.cn/snews/0562.htm
- http://m.blog.oexnr.cn/snews/836669.htm
- http://m.blog.oexnr.cn/snews/6533.htm
- http://m.blog.oexnr.cn/snews/711126.htm
- http://m.blog.oexnr.cn/snews/75565.htm
- http://m.blog.oexnr.cn/snews/689911.htm
- http://m.blog.oexnr.cn/snews/58778.htm
- http://m.blog.oexnr.cn/snews/1929.htm
- http://m.blog.oexnr.cn/snews/7421311.htm
- http://m.blog.oexnr.cn/snews/951143.htm
- http://m.blog.oexnr.cn/snews/136420.htm
- http://m.blog.oexnr.cn/snews/0703276.htm
- http://m.blog.oexnr.cn/snews/04787.htm
- http://m.blog.oexnr.cn/snews/5486634.htm
- http://m.blog.oexnr.cn/snews/297044.htm
- http://m.blog.oexnr.cn/snews/033273.htm
- http://m.blog.oexnr.cn/snews/8697489.htm
- http://m.blog.oexnr.cn/snews/722689.htm
- http://m.blog.oexnr.cn/snews/18596.htm
- http://m.blog.oexnr.cn/snews/820998.htm
- http://m.blog.oexnr.cn/snews/000022.htm
- http://m.blog.oexnr.cn/snews/70141.htm
- http://m.blog.oexnr.cn/snews/9432.htm
- http://m.blog.oexnr.cn/snews/61636.htm
- http://m.blog.oexnr.cn/snews/12476.htm
- http://m.blog.oexnr.cn/snews/6780.htm
- http://m.blog.oexnr.cn/snews/01656.htm
- http://m.blog.oexnr.cn/snews/2714090.htm
- http://m.blog.oexnr.cn/snews/515981.htm
- http://m.blog.oexnr.cn/snews/0149518.htm
- http://m.blog.oexnr.cn/snews/5409.htm
- http://m.blog.oexnr.cn/snews/14593.htm
- http://m.blog.oexnr.cn/snews/2720725.htm
- http://m.blog.oexnr.cn/snews/5246.htm
- http://m.blog.oexnr.cn/snews/2822161.htm
- http://m.blog.oexnr.cn/snews/7746220.htm
- http://m.blog.oexnr.cn/snews/6354.htm
- http://m.blog.oexnr.cn/snews/310880.htm
- http://m.blog.oexnr.cn/snews/385808.htm
- http://m.blog.oexnr.cn/snews/7567561.htm
- http://m.blog.oexnr.cn/snews/959860.htm
- http://m.blog.oexnr.cn/snews/83309.htm
- http://m.blog.oexnr.cn/snews/955964.htm
- http://m.blog.oexnr.cn/snews/17969.htm
- http://m.blog.oexnr.cn/snews/4610.htm
- http://m.blog.oexnr.cn/snews/625380.htm
- http://m.blog.oexnr.cn/snews/6598021.htm
- http://m.blog.oexnr.cn/snews/579736.htm
- http://m.blog.oexnr.cn/snews/3533.htm
- http://m.blog.oexnr.cn/snews/92357.htm
- http://m.blog.oexnr.cn/snews/7438.htm
- http://m.blog.oexnr.cn/snews/37629.htm
- http://m.blog.oexnr.cn/snews/8079714.htm
- http://m.blog.oexnr.cn/snews/7169.htm
- http://m.blog.oexnr.cn/snews/7499227.htm
- http://m.blog.oexnr.cn/snews/80975.htm
- http://m.blog.oexnr.cn/snews/220114.htm
- http://m.blog.oexnr.cn/snews/611167.htm
- http://m.blog.oexnr.cn/snews/17839.htm
- http://m.blog.oexnr.cn/snews/85129.htm
- http://m.blog.oexnr.cn/snews/11007.htm
- http://m.blog.oexnr.cn/snews/987912.htm
- http://m.blog.oexnr.cn/snews/4054056.htm
- http://m.blog.oexnr.cn/snews/172205.htm
- http://m.blog.oexnr.cn/snews/91376.htm
- http://m.blog.oexnr.cn/snews/378600.htm
- http://m.blog.oexnr.cn/snews/592013.htm
- http://m.blog.oexnr.cn/snews/7611503.htm
- http://m.blog.oexnr.cn/snews/57217.htm
- http://m.blog.oexnr.cn/snews/7210802.htm
- http://m.blog.oexnr.cn/snews/4964.htm
- http://m.blog.oexnr.cn/snews/3246.htm
- http://m.blog.oexnr.cn/snews/99793.htm
- http://m.blog.oexnr.cn/snews/20218.htm
- http://m.blog.oexnr.cn/snews/0598.htm
- http://m.blog.oexnr.cn/snews/9261781.htm
- http://m.blog.oexnr.cn/snews/37598.htm
- http://m.blog.oexnr.cn/snews/96300.htm
- http://m.blog.oexnr.cn/snews/75156.htm
- http://m.blog.oexnr.cn/snews/806454.htm
- http://m.blog.oexnr.cn/snews/567857.htm
- http://m.blog.oexnr.cn/snews/9475991.htm
- http://m.blog.oexnr.cn/snews/6362532.htm
- http://m.blog.oexnr.cn/snews/3549182.htm
- http://m.blog.oexnr.cn/snews/0991.htm
- http://m.blog.oexnr.cn/snews/74150.htm
- http://m.blog.oexnr.cn/snews/7966904.htm
- http://m.blog.oexnr.cn/snews/0909.htm
- http://m.blog.oexnr.cn/snews/469936.htm
- http://m.blog.oexnr.cn/snews/410615.htm
- http://m.blog.oexnr.cn/snews/5344.htm
- http://m.blog.oexnr.cn/snews/01376.htm
- http://m.blog.oexnr.cn/snews/6833661.htm
- http://m.blog.oexnr.cn/snews/64230.htm
- http://m.blog.oexnr.cn/snews/4530745.htm
- http://m.blog.oexnr.cn/snews/470741.htm
- http://m.blog.oexnr.cn/snews/269193.htm
- http://m.blog.oexnr.cn/snews/057620.htm
- http://m.blog.oexnr.cn/snews/07914.htm
- http://m.blog.oexnr.cn/snews/253623.htm
- http://m.blog.oexnr.cn/snews/924507.htm
- http://m.blog.oexnr.cn/snews/3915.htm
- http://m.blog.oexnr.cn/snews/1161415.htm
- http://m.blog.oexnr.cn/snews/6207028.htm
- http://m.blog.oexnr.cn/snews/62459.htm
- http://m.blog.oexnr.cn/snews/797752.htm
- http://m.blog.oexnr.cn/snews/4480.htm
- http://m.blog.oexnr.cn/snews/70993.htm
- http://m.blog.oexnr.cn/snews/6475297.htm
- http://m.blog.oexnr.cn/snews/66860.htm
- http://m.blog.oexnr.cn/snews/8602508.htm
- http://m.blog.oexnr.cn/snews/0670731.htm
- http://m.blog.oexnr.cn/snews/66310.htm
- http://m.blog.oexnr.cn/snews/85611.htm
- http://m.blog.oexnr.cn/snews/1092904.htm
- http://m.blog.oexnr.cn/snews/5270545.htm
- http://m.blog.oexnr.cn/snews/077787.htm
- http://m.blog.oexnr.cn/snews/919034.htm
- http://m.blog.oexnr.cn/snews/83994.htm
- http://m.blog.oexnr.cn/snews/68615.htm
- http://m.blog.oexnr.cn/snews/501868.htm
- http://m.blog.oexnr.cn/snews/53066.htm
- http://m.blog.oexnr.cn/snews/2392.htm
- http://m.blog.oexnr.cn/snews/6753941.htm
- http://m.blog.oexnr.cn/snews/1579.htm
- http://m.blog.oexnr.cn/snews/886292.htm
- http://m.blog.oexnr.cn/snews/2281.htm
- http://m.blog.oexnr.cn/snews/0996.htm
- http://m.blog.oexnr.cn/snews/65472.htm
- http://m.blog.oexnr.cn/snews/4811.htm
- http://m.blog.oexnr.cn/snews/360496.htm
- http://m.blog.oexnr.cn/snews/601436.htm
- http://m.blog.oexnr.cn/snews/7572722.htm
- http://m.blog.oexnr.cn/snews/5768205.htm
- http://m.blog.oexnr.cn/snews/61944.htm
- http://m.blog.oexnr.cn/snews/978389.htm
- http://m.blog.oexnr.cn/snews/3381.htm
- http://m.blog.oexnr.cn/snews/0988.htm
- http://m.blog.oexnr.cn/snews/5088973.htm
- http://m.blog.oexnr.cn/snews/143006.htm
- http://m.blog.oexnr.cn/snews/934056.htm
- http://m.blog.oexnr.cn/snews/4587.htm
- http://m.blog.oexnr.cn/snews/68075.htm
- http://m.blog.oexnr.cn/snews/5582682.htm
- http://m.blog.oexnr.cn/snews/10756.htm
- http://m.blog.oexnr.cn/snews/4553.htm
- http://m.blog.oexnr.cn/snews/1786.htm
- http://m.blog.oexnr.cn/snews/218107.htm
- http://m.blog.oexnr.cn/snews/756026.htm
- http://m.blog.oexnr.cn/snews/3720.htm
- http://m.blog.oexnr.cn/snews/9316.htm
- http://m.blog.oexnr.cn/snews/15135.htm
- http://m.blog.oexnr.cn/snews/8817.htm
- http://m.blog.oexnr.cn/snews/059728.htm
- http://m.blog.oexnr.cn/snews/6084186.htm
- http://m.blog.oexnr.cn/snews/691499.htm
- http://m.blog.oexnr.cn/snews/11782.htm
- http://m.blog.oexnr.cn/snews/375101.htm
- http://m.blog.oexnr.cn/snews/39266.htm
- http://m.blog.oexnr.cn/snews/61433.htm
- http://m.blog.oexnr.cn/snews/5671.htm
- http://m.blog.oexnr.cn/snews/5576.htm
- http://m.blog.oexnr.cn/snews/435905.htm
- http://m.blog.oexnr.cn/snews/570422.htm
- http://m.blog.oexnr.cn/snews/2453044.htm
- http://m.blog.oexnr.cn/snews/0743673.htm
- http://m.blog.oexnr.cn/snews/23978.htm
- http://m.blog.oexnr.cn/snews/05925.htm
- http://m.blog.oexnr.cn/snews/4306062.htm
- http://m.blog.oexnr.cn/snews/8571919.htm
- http://m.blog.oexnr.cn/snews/1342683.htm
- http://m.blog.oexnr.cn/snews/203033.htm
- http://m.blog.oexnr.cn/snews/86374.htm
- http://m.blog.oexnr.cn/snews/1400.htm
- http://m.blog.oexnr.cn/snews/0483.htm
- http://m.blog.oexnr.cn/snews/1786204.htm
- http://m.blog.oexnr.cn/snews/1864.htm
- http://m.blog.oexnr.cn/snews/37616.htm
- http://m.blog.oexnr.cn/snews/68168.htm
- http://m.blog.oexnr.cn/snews/7221119.htm
- http://m.blog.oexnr.cn/snews/65936.htm
- http://m.blog.oexnr.cn/snews/473929.htm
- http://m.blog.oexnr.cn/snews/5628377.htm
- http://m.blog.oexnr.cn/snews/4387.htm
- http://m.blog.oexnr.cn/snews/38760.htm
- http://m.blog.oexnr.cn/snews/845407.htm
- http://m.blog.oexnr.cn/snews/696619.htm
- http://m.blog.oexnr.cn/snews/36172.htm
- http://m.blog.oexnr.cn/snews/804455.htm
- http://m.blog.oexnr.cn/snews/9927.htm
- http://m.blog.oexnr.cn/snews/19749.htm
- http://m.blog.oexnr.cn/snews/0252.htm
- http://m.blog.oexnr.cn/snews/1728826.htm
- http://m.blog.oexnr.cn/snews/078810.htm
- http://m.blog.oexnr.cn/snews/6749124.htm
- http://m.blog.oexnr.cn/snews/9778.htm
- http://m.blog.oexnr.cn/snews/728836.htm
- http://m.blog.oexnr.cn/snews/17482.htm
- http://m.blog.oexnr.cn/snews/3796.htm
- http://m.blog.oexnr.cn/snews/31722.htm
- http://m.blog.oexnr.cn/snews/6783.htm
- http://m.blog.oexnr.cn/snews/415966.htm
- http://m.blog.oexnr.cn/snews/86705.htm
- http://m.blog.oexnr.cn/snews/8281425.htm
- http://m.blog.oexnr.cn/snews/7855669.htm
- http://m.blog.oexnr.cn/snews/634476.htm
- http://m.blog.oexnr.cn/snews/08079.htm
- http://m.blog.oexnr.cn/snews/044372.htm
- http://m.blog.oexnr.cn/snews/2906.htm
- http://m.blog.oexnr.cn/snews/274237.htm
- http://m.blog.oexnr.cn/snews/2473.htm
- http://m.blog.oexnr.cn/snews/0544633.htm
- http://m.blog.oexnr.cn/snews/0080571.htm
- http://m.blog.oexnr.cn/snews/0411.htm
- http://m.blog.oexnr.cn/snews/0588.htm
- http://m.blog.oexnr.cn/snews/135589.htm
- http://m.blog.oexnr.cn/snews/026886.htm
- http://m.blog.oexnr.cn/snews/13497.htm
- http://m.blog.oexnr.cn/snews/0923960.htm
- http://m.blog.oexnr.cn/snews/700167.htm
- http://m.blog.oexnr.cn/snews/938923.htm
- http://m.blog.oexnr.cn/snews/6286960.htm
- http://m.blog.oexnr.cn/snews/5120079.htm
- http://m.blog.oexnr.cn/snews/2329.htm
- http://m.blog.oexnr.cn/snews/7528551.htm
- http://m.blog.oexnr.cn/snews/77712.htm
- http://m.blog.oexnr.cn/snews/9296980.htm
- http://m.blog.oexnr.cn/snews/50641.htm
- http://m.blog.oexnr.cn/snews/011177.htm
- http://m.blog.oexnr.cn/snews/2272.htm
- http://m.blog.oexnr.cn/snews/4317.htm
- http://m.blog.oexnr.cn/snews/0041645.htm
- http://m.blog.oexnr.cn/snews/109863.htm
- http://m.blog.oexnr.cn/snews/30850.htm
- http://m.blog.oexnr.cn/snews/6979841.htm
- http://m.blog.oexnr.cn/snews/79868.htm
- http://m.blog.oexnr.cn/snews/714555.htm
- http://m.blog.oexnr.cn/snews/582119.htm
- http://m.blog.oexnr.cn/snews/2889029.htm
- http://m.blog.oexnr.cn/snews/5907.htm
- http://m.blog.oexnr.cn/snews/9414.htm
- http://m.blog.oexnr.cn/snews/3028.htm
- http://m.blog.oexnr.cn/snews/53814.htm
- http://m.blog.oexnr.cn/snews/88188.htm
- http://m.blog.oexnr.cn/snews/728804.htm
- http://m.blog.oexnr.cn/snews/8529.htm
- http://m.blog.oexnr.cn/snews/1146424.htm
- http://m.blog.oexnr.cn/snews/4093.htm
- http://m.blog.oexnr.cn/snews/150688.htm
- http://m.blog.oexnr.cn/snews/201521.htm
- http://m.blog.oexnr.cn/snews/440125.htm
- http://m.blog.oexnr.cn/snews/55401.htm
- http://m.blog.oexnr.cn/snews/530315.htm
- http://m.blog.oexnr.cn/snews/52224.htm
- http://m.blog.oexnr.cn/snews/55765.htm
- http://m.blog.oexnr.cn/snews/49418.htm
- http://m.blog.oexnr.cn/snews/72095.htm
- http://m.blog.oexnr.cn/snews/6668.htm
- http://m.blog.oexnr.cn/snews/14336.htm
- http://m.blog.oexnr.cn/snews/0503214.htm
- http://m.blog.oexnr.cn/snews/2247.htm
- http://m.blog.oexnr.cn/snews/8017.htm
- http://m.blog.oexnr.cn/snews/68542.htm
- http://m.blog.oexnr.cn/snews/3687.htm
- http://m.blog.oexnr.cn/snews/43504.htm
- http://m.blog.oexnr.cn/snews/4128.htm
- http://m.blog.oexnr.cn/snews/612115.htm
- http://m.blog.oexnr.cn/snews/9181.htm
- http://m.blog.oexnr.cn/snews/899576.htm
- http://m.blog.oexnr.cn/snews/3251.htm
- http://m.blog.oexnr.cn/snews/7447.htm
- http://m.blog.oexnr.cn/snews/392585.htm
- http://m.blog.oexnr.cn/snews/0758.htm
- http://m.blog.oexnr.cn/snews/18018.htm
- http://m.blog.oexnr.cn/snews/3586950.htm
- http://m.blog.oexnr.cn/snews/775218.htm

## 项目结构

```
weblink-navigator/
├── links/                                  # 核心链接清单存储目录
│   ├── master_list.txt                     # 主清单文件，每行一个 URL，支持 # 注释
│   ├── tags.yaml                           # 标签定义与颜色映射配置
│   └── archive/                            # 历史版本归档，按日期存放旧清单快照
│       └── 2026-08-01_master_list.txt
├── scripts/                                # 可执行脚本集合
│   ├── build_index.py                      # 主构建脚本，读取清单并生成导航页
│   ├── health_check.py                     # 链接可用性检查脚本，输出 CSV 报告
│   ├── import_csv.py                       # 从外部 CSV 导入链接并合并至主清单
│   └── dedup.py                            # 去重工具，扫描清单并标记重复条目
├── templates/                              # 页面生成模板
│   ├── base.html                           # HTML 基础骨架
│   ├── index_template.html                 # 导航首页模板，包含标签筛选区
│   └── detail_template.html                # 单个链接详情页模板（可选）
├── static/                                 # 静态资源文件
│   ├── css/
│   │   └── style.css                       # 响应式布局样式，适配桌面与移动端
│   ├── js/
│   │   └── filter.js                       # 前端标签筛选与搜索逻辑
│   └── assets/
│       └── logo.svg                        # 项目标识，无额外依赖
├── docs/                                   # 项目文档，与文档导航章节对应
│   ├── getting-started.md
│   ├── link-specification.md
│   ├── health-check.md
│   ├── custom-theme.md
│   └── contributing.md
├── tests/                                  # 单元测试与集成测试脚本
│   ├── test_parser.py                      # 测试链接解析与格式校验
│   ├── test_dedup.py
│   └── test_health.py
├── requirements.txt                        # Python 依赖清单
├── setup.py                                # 可选安装脚本，用于将脚本注册为命令行工具
└── README.md                               # 当前文件
```

## 贡献指南

提交链接增删改建议时，请先通过 issue 系统说明变更理由（如链接失效、新增高价值来源、分类错误），并附上至少一条验证依据（如文章标题或简要内容描述）。审核通过后，由维护者或贡献者本人提交拉取请求。

拉取请求应遵循单一职责原则：单个 PR 仅处理一类变更（新增、删除、修改），且修改范围不超过 20 条链接，以便于逐条审查。PR 描述中需明确列出受影响的链接条目及其变更前后的状态。

所有新增链接须通过基本的可用性检查，即目标页面应返回 HTTP 状态码 200 或 301/302 且最终可访问。如果链接需要特定 User-Agent 或 Cookie 才能访问，请在注释中注明访问条件。

文档与注释更新需与链接变更同步进行。如果新增链接涉及新的技术主题或分类，应同步更新 tags.yaml 文件中的标签定义，并在 docs/link-specification.md 中补充相关说明。

代码贡献（脚本优化、模板改进）需附带对应的单元测试，确保在 Python 3.8 至 3.11 环境下测试通过。测试覆盖率不低于 80%，且不引入新的外部依赖（除非经过讨论并获得批准）。

## 常见问题

问：健康检查脚本报告大量链接超时，但浏览器可以正常访问，是什么原因？

答：部分源站会拒绝来自非浏览器 User-Agent 的请求，或对频繁的 HEAD 请求实施限流。建议在 health_check.py 中调整请求头（如将 User-Agent 修改为常见浏览器标识），并适当增加请求间隔（默认 1 秒，可调整至 2-3 秒）。如果目标站点位于特定网络区域，可能需要配置代理参数。

问：如何将现有的浏览器书签批量导入链接清单？

答：大多数浏览器支持将书签导出为 HTML 或 CSV 格式。你可以先导出书签文件，然后使用 scripts/import_csv.py 脚本（需先将书签文件转换为 CSV 格式，包含 URL 和标题列）进行导入。导入后，手动补充标签和分类字段即可。项目暂不直接支持 Netscape 书签格式，但可通过第三方工具转换。

问：生成的导航页面在本地打开时样式正常，但部署到内网服务器后 CSS 加载失败，如何解决？

答：请检查 build_index.py 中的静态资源引用路径设置。默认使用相对路径，如果部署在子目录下，需在配置文件中设置 base_url 前缀。推荐做法是将 static 目录与 index.html 放置于同一输出根目录下，并保持相对路径引用。如果使用 nginx 或 Apache，请确保静态资源目录的访问权限已开放。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
