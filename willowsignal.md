# WebIndexer

WebIndexer 是一个面向技术研究者与内容聚合者的轻量级外链资源归集与导航系统。该项目定位于将分散在各类信息源中的结构化或半结构化数据条目，以统一的条目模型进行标准化收录、索引与展示，适用于小规模知识库构建、垂直领域资源导航以及个人书签系统的原型验证场景。WebIndexer 并不提供自动爬取或智能摘要能力，而是强调人工精选条目的有序化管理与快速检索，目标用户包括技术文档撰写者、开源社区维护者以及需要长期维护外链清单的运营人员。

WebIndexer 以静态站点生成的方式运作，用户通过编辑结构化数据文件即可完成资源条目的增删改，构建过程不依赖外部数据库，所有索引文件在构建时生成，便于部署到任何静态托管服务。项目提供按分类、标签、发布日期和来源域名进行多维度筛选的能力，同时支持简单的关键词搜索，确保在数百至数千条资源规模下仍保持流畅的浏览体验。

## 功能概览

条目元数据管理 支持为每个资源条目记录标题、原始 URL、来源域名、收录时间、分类标签和备注说明，所有字段以 Markdown 或 YAML 前置数据形式存储。

多维度筛选视图 提供按分类目录、标签云、来源域名分组和收录时间范围进行资源筛选的导航面板，帮助用户快速定位特定主题或来源的内容。

静态全文搜索 构建时生成倒排索引，支持对条目标题、备注和分类标签进行关键词匹配检索，搜索结果按相关性排序。

自定义分类体系 用户可根据实际需要自由定义一级分类与二级子分类，分类定义独立于条目数据，便于统一调整结构。

批量导入与导出 支持从 CSV 文件批量导入资源条目，并提供将现有条目库导出为 JSON 或 CSV 格式的功能，方便与其他工具进行数据交换。

资源状态标记 每条资源可标记为有效、失效或待审核三种状态，失效链接可在视图中统一过滤或高亮显示，便于定期清理维护。

响应式浏览界面 基于 CSS 弹性布局实现桌面端与移动端自适应展示，确保在不同屏幕尺寸下均可正常使用筛选、搜索与列表浏览功能。

## 应用场景

技术文档外部参考管理 技术写作团队在编写文档时需要引用大量外部资料，使用 WebIndexer 可以集中管理所有引用链接，并为每一条记录添加分类标签（如性能测试、API 设计规范、安全指南等），方便后期校对与更新。当外部资料地址变更时，团队可在统一界面中快速查找并修正。

开源项目相关资源导航 开源项目维护者可将社区中与本项目相关的教程文章、视频讲解、衍生工具和插件列表通过 WebIndexer 组织为外链导航页面，放置于项目文档或 GitHub Pages 中，为社区贡献者提供清晰的资源索引，减少重复提问。

个人知识库外链归档 长期进行技术学习的个人开发者可使用 WebIndexer 搭建自己的书签归档系统，将阅读过的技术博客、在线工具和学术论文按主题分类保存，并通过备注字段记录阅读心得或关键要点，构建个人化的知识外链网络。

垂直领域资源聚合站 运营者可以针对特定技术领域（如云原生、前端框架、数据库运维）收集相关优质资源，通过 WebIndexer 生成分类清晰的资源导航站，为同领域从业者提供便捷的查阅入口，同时通过定期导出数据备份保证资源清单的可迁移性。

## 快速开始

以下步骤适用于 macOS 及 Linux 环境，Windows 用户建议使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/example/webindexer.git
cd webindexer

# 安装依赖（项目基于 Node.js 构建）
npm install

# 复制示例数据文件
cp config/example.data.yml data/entries.yml

# 执行构建，生成静态站点
npm run build

# 启动本地预览服务器
npm run serve
```

执行完成后，访问终端输出的本地地址（默认 http://localhost:8080 ）即可查看生成的资源索引页面。如需自定义条目数据，请编辑 data/entries.yml 文件后重新运行构建命令。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，用于执行构建脚本与开发服务器 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库与管理变更 |
| YAML 解析器 | 项目内置依赖 | 用于解析条目数据文件，无需单独安装 |
| 静态 Web 服务器 | 任意（开发时使用内置 serve） | 生产环境可选用 Nginx、Apache 或 Caddy 等 |
| 磁盘空间 | 至少 50 MB | 用于存放源码、依赖和构建产物 |
| 内存 | 建议 512 MB 以上 | 构建过程中索引生成需要一定内存 |
| 操作系统 | Linux / macOS / Windows（WSL） | 跨平台支持，Windows 原生环境需使用 PowerShell |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速搭建实例、添加第一条资源、生成站点并预览效果 |
| 数据格式规范 | docs/data-format.md | 条目数据文件的结构定义、字段类型、必填项与可选项说明 |
| 分类配置说明 | docs/category-config.md | 如何自定义分类体系、配置分类图标与层级关系 |
| 部署指南 | docs/deployment.md | 如何将生成的静态站点部署到 GitHub Pages、Netlify 或自有服务器 |

## 资源列表

- http://m.blog.bwbkj.cn/snews/866223.htm
- http://m.blog.bwbkj.cn/snews/968135.htm
- http://m.blog.bwbkj.cn/snews/080254.htm
- http://m.blog.bwbkj.cn/snews/958805.htm
- http://m.blog.bwbkj.cn/snews/884587.htm
- http://m.blog.bwbkj.cn/snews/47645.htm
- http://m.blog.bwbkj.cn/snews/0452051.htm
- http://m.blog.bwbkj.cn/snews/264100.htm
- http://m.blog.bwbkj.cn/snews/0669225.htm
- http://m.blog.bwbkj.cn/snews/59407.htm
- http://m.blog.bwbkj.cn/snews/39105.htm
- http://m.blog.bwbkj.cn/snews/806825.htm
- http://m.blog.bwbkj.cn/snews/7677232.htm
- http://m.blog.bwbkj.cn/snews/534260.htm
- http://m.blog.bwbkj.cn/snews/8459.htm
- http://m.blog.bwbkj.cn/snews/8220619.htm
- http://m.blog.bwbkj.cn/snews/377495.htm
- http://m.blog.bwbkj.cn/snews/386492.htm
- http://m.blog.bwbkj.cn/snews/1971.htm
- http://m.blog.bwbkj.cn/snews/4086.htm
- http://m.blog.bwbkj.cn/snews/9494964.htm
- http://m.blog.bwbkj.cn/snews/5846.htm
- http://m.blog.bwbkj.cn/snews/6624546.htm
- http://m.blog.bwbkj.cn/snews/90665.htm
- http://m.blog.bwbkj.cn/snews/515362.htm
- http://m.blog.bwbkj.cn/snews/746077.htm
- http://m.blog.bwbkj.cn/snews/614975.htm
- http://m.blog.bwbkj.cn/snews/2717551.htm
- http://m.blog.bwbkj.cn/snews/471888.htm
- http://m.blog.bwbkj.cn/snews/7005.htm
- http://m.blog.bwbkj.cn/snews/78295.htm
- http://m.blog.bwbkj.cn/snews/19025.htm
- http://m.blog.bwbkj.cn/snews/45998.htm
- http://m.blog.bwbkj.cn/snews/357034.htm
- http://m.blog.bwbkj.cn/snews/5888.htm
- http://m.blog.bwbkj.cn/snews/6610.htm
- http://m.blog.bwbkj.cn/snews/7682.htm
- http://m.blog.bwbkj.cn/snews/8580.htm
- http://m.blog.bwbkj.cn/snews/77847.htm
- http://m.blog.bwbkj.cn/snews/0570420.htm
- http://m.blog.bwbkj.cn/snews/4730474.htm
- http://m.blog.bwbkj.cn/snews/5012.htm
- http://m.blog.bwbkj.cn/snews/70320.htm
- http://m.blog.bwbkj.cn/snews/308657.htm
- http://m.blog.bwbkj.cn/snews/5667.htm
- http://m.blog.bwbkj.cn/snews/0160.htm
- http://m.blog.bwbkj.cn/snews/2201.htm
- http://m.blog.bwbkj.cn/snews/3829807.htm
- http://m.blog.bwbkj.cn/snews/327178.htm
- http://m.blog.bwbkj.cn/snews/242537.htm
- http://m.blog.bwbkj.cn/snews/6391.htm
- http://m.blog.bwbkj.cn/snews/0524436.htm
- http://m.blog.bwbkj.cn/snews/5739785.htm
- http://m.blog.bwbkj.cn/snews/3930.htm
- http://m.blog.bwbkj.cn/snews/8914120.htm
- http://m.blog.bwbkj.cn/snews/4527.htm
- http://m.blog.bwbkj.cn/snews/871191.htm
- http://m.blog.bwbkj.cn/snews/34390.htm
- http://m.blog.bwbkj.cn/snews/3575.htm
- http://m.blog.bwbkj.cn/snews/6038806.htm
- http://m.blog.bwbkj.cn/snews/8783527.htm
- http://m.blog.bwbkj.cn/snews/8472.htm
- http://m.blog.bwbkj.cn/snews/2198051.htm
- http://m.blog.bwbkj.cn/snews/1855169.htm
- http://m.blog.bwbkj.cn/snews/81781.htm
- http://m.blog.bwbkj.cn/snews/9487.htm
- http://m.blog.bwbkj.cn/snews/549899.htm
- http://m.blog.bwbkj.cn/snews/8861.htm
- http://m.blog.bwbkj.cn/snews/856601.htm
- http://m.blog.bwbkj.cn/snews/30453.htm
- http://m.blog.bwbkj.cn/snews/1291145.htm
- http://m.blog.bwbkj.cn/snews/6625.htm
- http://m.blog.bwbkj.cn/snews/6311.htm
- http://m.blog.bwbkj.cn/snews/43605.htm
- http://m.blog.bwbkj.cn/snews/29133.htm
- http://m.blog.bwbkj.cn/snews/69554.htm
- http://m.blog.bwbkj.cn/snews/41565.htm
- http://m.blog.bwbkj.cn/snews/128572.htm
- http://m.blog.bwbkj.cn/snews/9712508.htm
- http://m.blog.bwbkj.cn/snews/9873459.htm
- http://m.blog.bwbkj.cn/snews/2294.htm
- http://m.blog.bwbkj.cn/snews/7787.htm
- http://m.blog.bwbkj.cn/snews/4991060.htm
- http://m.blog.bwbkj.cn/snews/9226166.htm
- http://m.blog.bwbkj.cn/snews/5747.htm
- http://m.blog.bwbkj.cn/snews/0248.htm
- http://m.blog.bwbkj.cn/snews/6174.htm
- http://m.blog.bwbkj.cn/snews/3139.htm
- http://m.blog.bwbkj.cn/snews/57422.htm
- http://m.blog.bwbkj.cn/snews/3588652.htm
- http://m.blog.bwbkj.cn/snews/927953.htm
- http://m.blog.bwbkj.cn/snews/942838.htm
- http://m.blog.bwbkj.cn/snews/138137.htm
- http://m.blog.bwbkj.cn/snews/1558.htm
- http://m.blog.bwbkj.cn/snews/845687.htm
- http://m.blog.bwbkj.cn/snews/9993747.htm
- http://m.blog.bwbkj.cn/snews/850683.htm
- http://m.blog.bwbkj.cn/snews/82908.htm
- http://m.blog.bwbkj.cn/snews/8373342.htm
- http://m.blog.bwbkj.cn/snews/33295.htm
- http://m.blog.bwbkj.cn/snews/20494.htm
- http://m.blog.bwbkj.cn/snews/244993.htm
- http://m.blog.bwbkj.cn/snews/806847.htm
- http://m.blog.bwbkj.cn/snews/4690.htm
- http://m.blog.bwbkj.cn/snews/62282.htm
- http://m.blog.bwbkj.cn/snews/4505666.htm
- http://m.blog.bwbkj.cn/snews/359661.htm
- http://m.blog.bwbkj.cn/snews/105491.htm
- http://m.blog.bwbkj.cn/snews/62913.htm
- http://m.blog.bwbkj.cn/snews/036791.htm
- http://m.blog.bwbkj.cn/snews/03568.htm
- http://m.blog.bwbkj.cn/snews/256674.htm
- http://m.blog.bwbkj.cn/snews/8656242.htm
- http://m.blog.bwbkj.cn/snews/56271.htm
- http://m.blog.bwbkj.cn/snews/59346.htm
- http://m.blog.bwbkj.cn/snews/923379.htm
- http://m.blog.bwbkj.cn/snews/5712.htm
- http://m.blog.bwbkj.cn/snews/389215.htm
- http://m.blog.bwbkj.cn/snews/960173.htm
- http://m.blog.bwbkj.cn/snews/1837.htm
- http://m.blog.bwbkj.cn/snews/085909.htm
- http://m.blog.bwbkj.cn/snews/39765.htm
- http://m.blog.bwbkj.cn/snews/1593013.htm
- http://m.blog.bwbkj.cn/snews/658859.htm
- http://m.blog.bwbkj.cn/snews/7286317.htm
- http://m.blog.bwbkj.cn/snews/2353826.htm
- http://m.blog.bwbkj.cn/snews/35835.htm
- http://m.blog.bwbkj.cn/snews/2280.htm
- http://m.blog.bwbkj.cn/snews/1231289.htm
- http://m.blog.bwbkj.cn/snews/2130.htm
- http://m.blog.bwbkj.cn/snews/015261.htm
- http://m.blog.bwbkj.cn/snews/3986.htm
- http://m.blog.bwbkj.cn/snews/4072801.htm
- http://m.blog.bwbkj.cn/snews/341190.htm
- http://m.blog.bwbkj.cn/snews/719594.htm
- http://m.blog.bwbkj.cn/snews/153876.htm
- http://m.blog.bwbkj.cn/snews/274255.htm
- http://m.blog.bwbkj.cn/snews/700856.htm
- http://m.blog.bwbkj.cn/snews/7375198.htm
- http://m.blog.bwbkj.cn/snews/8820.htm
- http://m.blog.bwbkj.cn/snews/1490.htm
- http://m.blog.bwbkj.cn/snews/909596.htm
- http://m.blog.bwbkj.cn/snews/875583.htm
- http://m.blog.bwbkj.cn/snews/76137.htm
- http://m.blog.bwbkj.cn/snews/053446.htm
- http://m.blog.bwbkj.cn/snews/9682.htm
- http://m.blog.bwbkj.cn/snews/02342.htm
- http://m.blog.bwbkj.cn/snews/7816.htm
- http://m.blog.bwbkj.cn/snews/83779.htm
- http://m.blog.bwbkj.cn/snews/328189.htm
- http://m.blog.bwbkj.cn/snews/297106.htm
- http://m.blog.bwbkj.cn/snews/9624.htm
- http://m.blog.bwbkj.cn/snews/6117767.htm
- http://m.blog.bwbkj.cn/snews/0216.htm
- http://m.blog.bwbkj.cn/snews/13844.htm
- http://m.blog.bwbkj.cn/snews/6420.htm
- http://m.blog.bwbkj.cn/snews/7514197.htm
- http://m.blog.bwbkj.cn/snews/9213721.htm
- http://m.blog.bwbkj.cn/snews/9183.htm
- http://m.blog.bwbkj.cn/snews/2549342.htm
- http://m.blog.bwbkj.cn/snews/306058.htm
- http://m.blog.bwbkj.cn/snews/8676.htm
- http://m.blog.bwbkj.cn/snews/4682.htm
- http://m.blog.bwbkj.cn/snews/21999.htm
- http://m.blog.bwbkj.cn/snews/2996711.htm
- http://m.blog.bwbkj.cn/snews/8891877.htm
- http://m.blog.bwbkj.cn/snews/6569761.htm
- http://m.blog.bwbkj.cn/snews/93531.htm
- http://m.blog.bwbkj.cn/snews/3407.htm
- http://m.blog.bwbkj.cn/snews/490984.htm
- http://m.blog.bwbkj.cn/snews/1241871.htm
- http://m.blog.bwbkj.cn/snews/9603.htm
- http://m.blog.bwbkj.cn/snews/7104541.htm
- http://m.blog.bwbkj.cn/snews/80747.htm
- http://m.blog.bwbkj.cn/snews/3986297.htm
- http://m.blog.bwbkj.cn/snews/2753.htm
- http://m.blog.bwbkj.cn/snews/3622796.htm
- http://m.blog.bwbkj.cn/snews/60622.htm
- http://m.blog.bwbkj.cn/snews/91524.htm
- http://m.blog.bwbkj.cn/snews/8263836.htm
- http://m.blog.bwbkj.cn/snews/511126.htm
- http://m.blog.bwbkj.cn/snews/41527.htm
- http://m.blog.bwbkj.cn/snews/933384.htm
- http://m.blog.bwbkj.cn/snews/3597686.htm
- http://m.blog.bwbkj.cn/snews/605346.htm
- http://m.blog.bwbkj.cn/snews/0639.htm
- http://m.blog.bwbkj.cn/snews/2051945.htm
- http://m.blog.bwbkj.cn/snews/48305.htm
- http://m.blog.bwbkj.cn/snews/0454.htm
- http://m.blog.bwbkj.cn/snews/3544949.htm
- http://m.blog.bwbkj.cn/snews/41844.htm
- http://m.blog.bwbkj.cn/snews/25135.htm
- http://m.blog.bwbkj.cn/snews/63315.htm
- http://m.blog.bwbkj.cn/snews/1672.htm
- http://m.blog.bwbkj.cn/snews/283191.htm
- http://m.blog.bwbkj.cn/snews/678558.htm
- http://m.blog.bwbkj.cn/snews/424037.htm
- http://m.blog.bwbkj.cn/snews/287002.htm
- http://m.blog.bwbkj.cn/snews/972622.htm
- http://m.blog.bwbkj.cn/snews/2039.htm
- http://m.blog.bwbkj.cn/snews/32239.htm
- http://m.blog.bwbkj.cn/snews/011669.htm
- http://m.blog.bwbkj.cn/snews/08295.htm
- http://m.blog.bwbkj.cn/snews/2528550.htm
- http://m.blog.bwbkj.cn/snews/857566.htm
- http://m.blog.bwbkj.cn/snews/58895.htm
- http://m.blog.bwbkj.cn/snews/230274.htm
- http://m.blog.bwbkj.cn/snews/0557270.htm
- http://m.blog.bwbkj.cn/snews/9393338.htm
- http://m.blog.bwbkj.cn/snews/2538125.htm
- http://m.blog.bwbkj.cn/snews/916161.htm
- http://m.blog.bwbkj.cn/snews/2529045.htm
- http://m.blog.bwbkj.cn/snews/73899.htm
- http://m.blog.bwbkj.cn/snews/21098.htm
- http://m.blog.bwbkj.cn/snews/071984.htm
- http://m.blog.bwbkj.cn/snews/57027.htm
- http://m.blog.bwbkj.cn/snews/40063.htm
- http://m.blog.bwbkj.cn/snews/5477201.htm
- http://m.blog.bwbkj.cn/snews/6168491.htm
- http://m.blog.bwbkj.cn/snews/58374.htm
- http://m.blog.bwbkj.cn/snews/50020.htm
- http://m.blog.bwbkj.cn/snews/8924099.htm
- http://m.blog.bwbkj.cn/snews/2041.htm
- http://m.blog.bwbkj.cn/snews/7615.htm
- http://m.blog.bwbkj.cn/snews/01310.htm
- http://m.blog.bwbkj.cn/snews/4756.htm
- http://m.blog.bwbkj.cn/snews/243649.htm
- http://m.blog.bwbkj.cn/snews/08456.htm
- http://m.blog.bwbkj.cn/snews/404120.htm
- http://m.blog.bwbkj.cn/snews/431675.htm
- http://m.blog.bwbkj.cn/snews/87966.htm
- http://m.blog.bwbkj.cn/snews/98781.htm
- http://m.blog.bwbkj.cn/snews/007325.htm
- http://m.blog.bwbkj.cn/snews/07653.htm
- http://m.blog.bwbkj.cn/snews/2299.htm
- http://m.blog.bwbkj.cn/snews/5060646.htm
- http://m.blog.bwbkj.cn/snews/0166.htm
- http://m.blog.bwbkj.cn/snews/0579190.htm
- http://m.blog.bwbkj.cn/snews/755360.htm
- http://m.blog.bwbkj.cn/snews/7107000.htm
- http://m.blog.bwbkj.cn/snews/1259.htm
- http://m.blog.bwbkj.cn/snews/361114.htm
- http://m.blog.bwbkj.cn/snews/6239000.htm
- http://m.blog.bwbkj.cn/snews/4997.htm
- http://m.blog.bwbkj.cn/snews/6806914.htm
- http://m.blog.bwbkj.cn/snews/35842.htm
- http://m.blog.bwbkj.cn/snews/13338.htm
- http://m.blog.bwbkj.cn/snews/2020826.htm
- http://m.blog.bwbkj.cn/snews/439640.htm
- http://m.blog.bwbkj.cn/snews/3938437.htm
- http://m.blog.bwbkj.cn/snews/8822111.htm
- http://m.blog.bwbkj.cn/snews/1249.htm
- http://m.blog.bwbkj.cn/snews/64668.htm
- http://m.blog.bwbkj.cn/snews/790322.htm
- http://m.blog.bwbkj.cn/snews/83596.htm
- http://m.blog.bwbkj.cn/snews/5670.htm
- http://m.blog.bwbkj.cn/snews/4743509.htm
- http://m.blog.bwbkj.cn/snews/8514625.htm
- http://m.blog.bwbkj.cn/snews/26005.htm
- http://m.blog.bwbkj.cn/snews/5685247.htm
- http://m.blog.bwbkj.cn/snews/66699.htm
- http://m.blog.bwbkj.cn/snews/7820.htm
- http://m.blog.bwbkj.cn/snews/8016.htm
- http://m.blog.bwbkj.cn/snews/3918262.htm
- http://m.blog.bwbkj.cn/snews/2934156.htm
- http://m.blog.bwbkj.cn/snews/1787572.htm
- http://m.blog.bwbkj.cn/snews/2171043.htm
- http://m.blog.bwbkj.cn/snews/597697.htm
- http://m.blog.bwbkj.cn/snews/536512.htm
- http://m.blog.bwbkj.cn/snews/030641.htm
- http://m.blog.bwbkj.cn/snews/0841666.htm
- http://m.blog.bwbkj.cn/snews/286911.htm
- http://m.blog.bwbkj.cn/snews/1960.htm
- http://m.blog.bwbkj.cn/snews/8686690.htm
- http://m.blog.bwbkj.cn/snews/146913.htm
- http://m.blog.bwbkj.cn/snews/5167.htm
- http://m.blog.bwbkj.cn/snews/070795.htm
- http://m.blog.bwbkj.cn/snews/321453.htm
- http://m.blog.bwbkj.cn/snews/427677.htm
- http://m.blog.bwbkj.cn/snews/81701.htm
- http://m.blog.bwbkj.cn/snews/4851093.htm
- http://m.blog.bwbkj.cn/snews/00469.htm
- http://m.blog.bwbkj.cn/snews/9486.htm
- http://m.blog.bwbkj.cn/snews/34376.htm
- http://m.blog.bwbkj.cn/snews/49854.htm
- http://m.blog.bwbkj.cn/snews/8280.htm
- http://m.blog.bwbkj.cn/snews/78227.htm
- http://m.blog.bwbkj.cn/snews/7633388.htm
- http://m.blog.bwbkj.cn/snews/245898.htm
- http://m.blog.bwbkj.cn/snews/323125.htm
- http://m.blog.bwbkj.cn/snews/796055.htm
- http://m.blog.bwbkj.cn/snews/3456.htm
- http://m.blog.bwbkj.cn/snews/2106529.htm
- http://m.blog.bwbkj.cn/snews/286087.htm
- http://m.blog.bwbkj.cn/snews/9827555.htm
- http://m.blog.bwbkj.cn/snews/583262.htm
- http://m.blog.bwbkj.cn/snews/0015992.htm
- http://m.blog.bwbkj.cn/snews/8734965.htm
- http://m.blog.bwbkj.cn/snews/82157.htm
- http://m.blog.bwbkj.cn/snews/3150.htm

## 项目结构

```
webindexer/
├── src/                             # 源代码主目录
│   ├── core/                        # 核心处理模块
│   │   ├── parser.js                # 解析条目数据文件（YAML/CSV）
│   │   ├── indexer.js               # 构建倒排索引与分类聚合
│   │   └── validator.js             # 校验条目字段完整性与 URL 格式
│   ├── generators/                  # 静态文件生成器
│   │   ├── html.js                  # 生成 HTML 页面（列表、详情、搜索）
│   │   ├── json.js                  # 生成 JSON 数据接口供前端调用
│   │   └── sitemap.js               # 生成站点地图与 RSS 订阅文件
│   ├── templates/                   # 页面模板与样式
│   │   ├── layout.ejs               # 主布局模板
│   │   ├── components/              # 可复用 UI 组件（筛选栏、分页）
│   │   └── assets/                  # 静态资源（CSS、JavaScript 脚本）
│   └── cli/                         # 命令行入口
│       ├── build.js                 # 构建命令实现
│       └── serve.js                 # 本地预览服务器实现
├── config/                          # 配置文件目录
│   ├── categories.yml               # 分类体系定义
│   └── example.data.yml             # 示例条目数据文件
├── data/                            # 用户数据存放目录（需自行创建）
│   └── entries.yml                  # 主条目数据文件
├── dist/                            # 构建输出目录（自动生成）
│   ├── index.html                   # 首页
│   ├── search.html                  # 搜索结果页
│   └── categories/                  # 分类筛选页面
├── docs/                            # 项目文档
│   ├── getting-started.md
│   ├── data-format.md
│   ├── category-config.md
│   └── deployment.md
├── tests/                           # 单元测试与集成测试
│   ├── parser.test.js
│   ├── indexer.test.js
│   └── fixtures/                    # 测试用数据样本
├── package.json                     # npm 项目配置与依赖声明
├── package-lock.json                # 依赖版本锁定文件
├── .gitignore                       # Git 忽略文件列表
├── LICENSE                          # MIT 许可证文本
└── README.md                        # 项目说明文档
```

## 贡献指南

1. 阅读项目文档中的 docs/data-format.md 与 docs/category-config.md，了解条目数据结构和分类配置方式，确保新增内容符合规范。对于现有功能改进或 Bug 修复，建议先在 issues 列表中搜索是否已有相关讨论。

2. 从 GitHub 仓库 Fork 项目到个人账户，克隆本地后创建新的功能分支。分支命名建议采用 feature/功能简述 或 fix/问题简述 的格式，便于维护者识别变更目的。

3. 在本地环境中执行 npm install 安装依赖，并通过 npm run test 运行现有测试套件，确保当前环境通过全部测试。新增功能或修复缺陷时，应在 tests/ 目录下补充对应的单元测试用例。

4. 完成代码变更后，执行 npm run build 验证构建流程无报错，并手动启动预览服务器检查生成的静态页面展示效果。确认无误后提交变更，提交信息应遵循 Conventional Commits 规范，使用 feat:、fix:、docs: 等前缀。

5. 向主仓库发起 Pull Request，在描述中清晰说明变更内容、关联的 Issue 编号以及测试覆盖情况。维护者将在 3 个工作日内进行 review，并根据反馈进行必要的修改调整。

## 常见问题

问：添加大量条目后，构建速度明显变慢，如何优化？

答：当条目数量超过 2000 条时，建议将 data/entries.yml 按年份或分类拆分为多个 YAML 文件，并在 config/categories.yml 中通过 include 指令合并加载。同时可关闭搜索索引中的备注字段全文索引，仅保留标题和标签，以减小索引体积。若仍无法满足性能要求，可考虑将构建流程迁移至 CI 环境定时执行，而非本地每次修改后实时构建。

问：如何批量更新已有条目的分类标签？

答：项目提供了辅助脚本 npm run migrate -- --from=旧分类 --to=新分类，可一键将所有条目的指定分类替换为新分类。如需更复杂的批量编辑，建议将 data/entries.yml 导出为 CSV 格式，使用电子表格软件批量编辑后再导入回 YAML 格式。注意导入时需保持字段名与原有结构一致，避免解析错误。

问：部署到生产环境后，搜索功能无法返回任何结果，可能是什么原因？

答：最常见的原因是构建时未正确生成搜索索引文件。请检查构建日志中是否包含 "index written" 字样，并确认 dist/ 目录下存在 search-index.json 文件。如果文件存在但前端仍无法检索，请打开浏览器开发者工具查看网络请求，确认该 JSON 文件的加载路径是否正确。部分托管平台对 .json 文件的 MIME 类型有特殊要求，需在服务器配置中添加 application/json 支持。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:12
