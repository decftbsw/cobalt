# WebLink Navigator

WebLink Navigator 是一个面向技术信息检索与外部资源聚合的开源导航工具，旨在解决开发者在日常工作中面对海量散落技术文档、新闻资讯与参考链接时难以高效归类、检索与共享的问题。项目定位于个人开发者、技术团队及小型技术社区，提供轻量级、可自部署的链接管理方案，帮助用户将零散的 URL 资源转化为结构化、可检索、可分享的知识网络。

项目核心围绕“链接即数据”的理念设计，不依赖外部数据库，所有资源索引基于静态文件与约定式目录结构生成，支持快速启动与低维护成本运行。WebLink Navigator 适用于需要长期积累技术阅读材料、维护团队知识库、构建个人阅读列表或运营主题化内容聚合站点的场景。当前版本为第 245/300 批资源整合迭代，已累计处理超过两千条外部链接，持续优化链接有效性校验与分类标注逻辑。

## 功能概览

**静态站点生成**：基于配置文件与目录扫描自动生成链接导航页面，无需动态后端服务，输出纯静态 HTML，可直接托管于任何 Web 服务器或对象存储。

**多维度分类与标签**：支持为每条链接标记一级分类、二级标签及优先级，提供按分类筛选、按标签聚合的浏览视图，便于快速定位特定主题资源。

**链接状态监控**：内置定时校验任务，对已收录链接进行可达性检查，标记失效链接并生成报告，帮助维护资源列表的健康度。

**全文检索支持**：集成轻量级前端索引，支持按标题、摘要、分类、标签关键词进行实时搜索，搜索结果按相关度排序。

**导入与导出接口**：支持 CSV 与 JSON 格式的批量导入导出，便于与其他工具（如书签管理器、笔记软件）进行数据迁移或同步。

**自定义主题与布局**：提供多套配色方案与布局模板，用户可通过修改配置文件切换显示风格，适配个人或团队品牌需求。

**访问统计分析**：基于页面内链点击日志，生成简单的访问热度统计，展示热门链接与高频分类，辅助资源优化决策。

**协作评论标记**：为每条链接提供轻量级注释字段，支持团队成员对链接添加备注、评分或阅读状态标记，便于协作审阅。

## 应用场景

**个人技术阅读清单管理**：开发者可将日常浏览到的技术博客、官方文档、GitHub 仓库、视频教程等链接统一收录，按学习主题分类，并定期回顾。配合状态监控功能，可及时发现已失效的参考链接，避免因资源迁移导致的信息断层。

**团队知识库外链聚合**：技术团队可将项目依赖的第三方库文档、内部设计提案链接、运维手册、线上监控面板地址等集中维护在 WebLink Navigator 中，作为团队入口页。新成员入职时，通过导航页即可快速了解项目所涉及的全部外部资源，降低信息交接成本。

**技术社区内容推荐系统**：中小型技术社区或兴趣小组可使用该项目搭建每日或每周优质内容推荐页，将精选文章、工具、播客等以卡片形式呈现。配合分类与标签功能，可针对不同用户群体（如前端、后端、运维）提供定制化视图。

**主题化学习路径构建**：教育机构或技术培训组织可围绕特定技术主题（如深度学习、云原生、区块链）整理完整学习路径，将每个阶段所需的阅读材料、实验环境链接、项目代码仓库等按顺序组织为导航结构，辅助系统性教学。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/weblink-navigator.git
cd weblink-navigator

# 安装依赖（项目基于 Node.js 开发，需要 Node.js 16.x 或更高版本）
npm install

# 构建静态站点（默认读取 ./data/links.json 与 ./config/site.yml）
npm run build

# 启动本地预览服务（默认监听端口 8080）
npm run serve
```

执行完毕后，访问 http://localhost:8080 即可查看生成的导航页面。如需自定义数据目录或修改构建参数，请参考 `docs/configuration.md` 中的高级配置说明。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.x 或更高 | 核心运行时，用于执行构建脚本与本地服务 |
| npm | 7.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.25 或更高 | 版本控制工具，用于克隆仓库及管理源码 |
| 操作系统 | Linux / macOS / Windows (WSL) | 推荐 Linux 或 macOS 以获得最佳性能 |
| 磁盘空间 | 至少 200 MB | 包含源码、依赖及构建产物 |
| 网络访问 | 需访问公共 npm 仓库 | 用于安装依赖包，首次构建需联网 |
| 浏览器 | 支持 ES6 的现代浏览器 | 用于预览生成的静态页面，如 Chrome、Firefox、Edge |
| 可选 - 定时校验 | cron / systemd timer | 如需启用链接状态自动监控，需配置计划任务 |
| 可选 - 日志存储 | 可写目录权限 | 用于存储校验报告与访问日志 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门 | docs/quick-start.md | 如何在 5 分钟内完成首次部署？如何修改站点标题与 Logo？ |
| 配置 | docs/configuration.md | 站点配置文件各字段含义是什么？如何自定义分类与标签体系？ |
| 数据管理 | docs/data-format.md | 链接数据文件采用什么格式？必填字段与扩展字段有哪些？ |
| 部署 | docs/deployment.md | 如何将构建产物部署到 Nginx、Caddy 或云存储服务？ |
| 运维 | docs/maintenance.md | 如何手动触发链接校验？如何查看失效链接报告？ |
| 扩展 | docs/custom-theme.md | 如何开发自定义主题模板？如何覆盖默认样式？ |
| API | docs/import-export.md | 导入导出接口的 JSON 结构是什么？如何与其他工具集成？ |
| 常见问题 | docs/faq.md | 构建失败如何排查？搜索功能不生效怎么办？ |

## 资源列表

- http://m.wap.bwbkj.cn/snews/6293617.htm
- http://m.wap.bwbkj.cn/snews/05990.htm
- http://m.wap.bwbkj.cn/snews/4595215.htm
- http://m.wap.bwbkj.cn/snews/594655.htm
- http://m.wap.bwbkj.cn/snews/80432.htm
- http://m.wap.bwbkj.cn/snews/04027.htm
- http://m.wap.bwbkj.cn/snews/68969.htm
- http://m.wap.bwbkj.cn/snews/6639426.htm
- http://m.wap.bwbkj.cn/snews/94729.htm
- http://m.wap.bwbkj.cn/snews/5671.htm
- http://m.wap.bwbkj.cn/snews/076441.htm
- http://m.wap.bwbkj.cn/snews/454429.htm
- http://m.wap.bwbkj.cn/snews/292598.htm
- http://m.wap.bwbkj.cn/snews/9785113.htm
- http://m.wap.bwbkj.cn/snews/7722422.htm
- http://m.wap.bwbkj.cn/snews/6650466.htm
- http://m.wap.bwbkj.cn/snews/2895.htm
- http://m.wap.bwbkj.cn/snews/0817682.htm
- http://m.wap.bwbkj.cn/snews/84173.htm
- http://m.wap.bwbkj.cn/snews/32154.htm
- http://m.wap.bwbkj.cn/snews/7883.htm
- http://m.wap.bwbkj.cn/snews/42930.htm
- http://m.wap.bwbkj.cn/snews/1468.htm
- http://m.wap.bwbkj.cn/snews/119295.htm
- http://m.wap.bwbkj.cn/snews/41853.htm
- http://m.wap.bwbkj.cn/snews/118836.htm
- http://m.wap.bwbkj.cn/snews/61083.htm
- http://m.wap.bwbkj.cn/snews/14727.htm
- http://m.wap.bwbkj.cn/snews/821574.htm
- http://m.wap.bwbkj.cn/snews/32215.htm
- http://m.wap.bwbkj.cn/snews/3038877.htm
- http://m.wap.bwbkj.cn/snews/3010596.htm
- http://m.wap.bwbkj.cn/snews/101810.htm
- http://m.wap.bwbkj.cn/snews/08900.htm
- http://m.wap.bwbkj.cn/snews/134070.htm
- http://m.wap.bwbkj.cn/snews/2278.htm
- http://m.wap.bwbkj.cn/snews/71281.htm
- http://m.wap.bwbkj.cn/snews/902162.htm
- http://m.wap.bwbkj.cn/snews/869473.htm
- http://m.wap.bwbkj.cn/snews/6473.htm
- http://m.wap.bwbkj.cn/snews/57470.htm
- http://m.wap.bwbkj.cn/snews/295369.htm
- http://m.wap.bwbkj.cn/snews/4263845.htm
- http://m.wap.bwbkj.cn/snews/6592602.htm
- http://m.wap.bwbkj.cn/snews/1167.htm
- http://m.wap.bwbkj.cn/snews/9247.htm
- http://m.wap.bwbkj.cn/snews/3425.htm
- http://m.wap.bwbkj.cn/snews/5257107.htm
- http://m.wap.bwbkj.cn/snews/552109.htm
- http://m.wap.bwbkj.cn/snews/1421.htm
- http://m.wap.bwbkj.cn/snews/0120.htm
- http://m.wap.bwbkj.cn/snews/2791642.htm
- http://m.wap.bwbkj.cn/snews/0252.htm
- http://m.wap.bwbkj.cn/snews/0242.htm
- http://m.wap.bwbkj.cn/snews/7002037.htm
- http://m.wap.bwbkj.cn/snews/1887.htm
- http://m.wap.bwbkj.cn/snews/5603.htm
- http://m.wap.bwbkj.cn/snews/64615.htm
- http://m.wap.bwbkj.cn/snews/309610.htm
- http://m.wap.bwbkj.cn/snews/6221.htm
- http://m.wap.bwbkj.cn/snews/49798.htm
- http://m.wap.bwbkj.cn/snews/83368.htm
- http://m.wap.bwbkj.cn/snews/20645.htm
- http://m.wap.bwbkj.cn/snews/242171.htm
- http://m.wap.bwbkj.cn/snews/2289793.htm
- http://m.wap.bwbkj.cn/snews/1805098.htm
- http://m.wap.bwbkj.cn/snews/57083.htm
- http://m.wap.bwbkj.cn/snews/767000.htm
- http://m.wap.bwbkj.cn/snews/9466417.htm
- http://m.wap.bwbkj.cn/snews/1771.htm
- http://m.wap.bwbkj.cn/snews/339294.htm
- http://m.wap.bwbkj.cn/snews/62616.htm
- http://m.wap.bwbkj.cn/snews/818721.htm
- http://m.wap.bwbkj.cn/snews/6875827.htm
- http://m.wap.bwbkj.cn/snews/24906.htm
- http://m.wap.bwbkj.cn/snews/049679.htm
- http://m.wap.bwbkj.cn/snews/2678.htm
- http://m.wap.bwbkj.cn/snews/90411.htm
- http://m.wap.bwbkj.cn/snews/82964.htm
- http://m.wap.bwbkj.cn/snews/3254.htm
- http://m.wap.bwbkj.cn/snews/83619.htm
- http://m.wap.bwbkj.cn/snews/26714.htm
- http://m.wap.bwbkj.cn/snews/7895.htm
- http://m.wap.bwbkj.cn/snews/6351.htm
- http://m.wap.bwbkj.cn/snews/40449.htm
- http://m.wap.bwbkj.cn/snews/4115.htm
- http://m.wap.bwbkj.cn/snews/990811.htm
- http://m.wap.bwbkj.cn/snews/6714.htm
- http://m.wap.bwbkj.cn/snews/3828.htm
- http://m.wap.bwbkj.cn/snews/5534737.htm
- http://m.wap.bwbkj.cn/snews/6245639.htm
- http://m.wap.bwbkj.cn/snews/9155041.htm
- http://m.wap.bwbkj.cn/snews/500868.htm
- http://m.wap.bwbkj.cn/snews/03940.htm
- http://m.wap.bwbkj.cn/snews/5409.htm
- http://m.wap.bwbkj.cn/snews/15372.htm
- http://m.wap.bwbkj.cn/snews/57525.htm
- http://m.wap.bwbkj.cn/snews/4785.htm
- http://m.wap.bwbkj.cn/snews/47930.htm
- http://m.wap.bwbkj.cn/snews/5875.htm
- http://m.wap.bwbkj.cn/snews/1236839.htm
- http://m.wap.bwbkj.cn/snews/82009.htm
- http://m.wap.bwbkj.cn/snews/43079.htm
- http://m.wap.bwbkj.cn/snews/1592424.htm
- http://m.wap.bwbkj.cn/snews/8192.htm
- http://m.wap.bwbkj.cn/snews/8717.htm
- http://m.wap.bwbkj.cn/snews/2541.htm
- http://m.wap.bwbkj.cn/snews/633453.htm
- http://m.wap.bwbkj.cn/snews/19710.htm
- http://m.wap.bwbkj.cn/snews/8605713.htm
- http://m.wap.bwbkj.cn/snews/373468.htm
- http://m.wap.bwbkj.cn/snews/3618048.htm
- http://m.wap.bwbkj.cn/snews/9355874.htm
- http://m.wap.bwbkj.cn/snews/8137.htm
- http://m.wap.bwbkj.cn/snews/665450.htm
- http://m.wap.bwbkj.cn/snews/5958.htm
- http://m.wap.bwbkj.cn/snews/16436.htm
- http://m.wap.bwbkj.cn/snews/882387.htm
- http://m.wap.bwbkj.cn/snews/8464.htm
- http://m.wap.bwbkj.cn/snews/36515.htm
- http://m.wap.bwbkj.cn/snews/191101.htm
- http://m.wap.bwbkj.cn/snews/8994537.htm
- http://m.wap.bwbkj.cn/snews/1354148.htm
- http://m.wap.bwbkj.cn/snews/041119.htm
- http://m.wap.bwbkj.cn/snews/7806.htm
- http://m.wap.bwbkj.cn/snews/1965.htm
- http://m.wap.bwbkj.cn/snews/518203.htm
- http://m.wap.bwbkj.cn/snews/8132.htm
- http://m.wap.bwbkj.cn/snews/1463.htm
- http://m.wap.bwbkj.cn/snews/1200.htm
- http://m.wap.bwbkj.cn/snews/914986.htm
- http://m.wap.bwbkj.cn/snews/7689.htm
- http://m.wap.bwbkj.cn/snews/3053195.htm
- http://m.wap.bwbkj.cn/snews/058017.htm
- http://m.wap.bwbkj.cn/snews/59300.htm
- http://m.wap.bwbkj.cn/snews/4751663.htm
- http://m.wap.bwbkj.cn/snews/033449.htm
- http://m.wap.bwbkj.cn/snews/2953111.htm
- http://m.wap.bwbkj.cn/snews/29931.htm
- http://m.wap.bwbkj.cn/snews/2045.htm
- http://m.wap.bwbkj.cn/snews/3063948.htm
- http://m.wap.bwbkj.cn/snews/9871026.htm
- http://m.wap.bwbkj.cn/snews/0862.htm
- http://m.wap.bwbkj.cn/snews/778756.htm
- http://m.wap.bwbkj.cn/snews/96630.htm
- http://m.wap.bwbkj.cn/snews/1899.htm
- http://m.wap.bwbkj.cn/snews/663783.htm
- http://m.wap.bwbkj.cn/snews/973797.htm
- http://m.wap.bwbkj.cn/snews/550697.htm
- http://m.wap.bwbkj.cn/snews/685178.htm
- http://m.wap.bwbkj.cn/snews/84010.htm
- http://m.wap.bwbkj.cn/snews/697458.htm
- http://m.wap.bwbkj.cn/snews/2758940.htm
- http://m.wap.bwbkj.cn/snews/64080.htm
- http://m.wap.bwbkj.cn/snews/44703.htm
- http://m.wap.bwbkj.cn/snews/518216.htm
- http://m.wap.bwbkj.cn/snews/10977.htm
- http://m.wap.bwbkj.cn/snews/69611.htm
- http://m.wap.bwbkj.cn/snews/5818.htm
- http://m.wap.bwbkj.cn/snews/9614.htm
- http://m.wap.bwbkj.cn/snews/5558.htm
- http://m.wap.bwbkj.cn/snews/4970.htm
- http://m.wap.bwbkj.cn/snews/37831.htm
- http://m.wap.bwbkj.cn/snews/27984.htm
- http://m.wap.bwbkj.cn/snews/821371.htm
- http://m.wap.bwbkj.cn/snews/477263.htm
- http://m.wap.bwbkj.cn/snews/4154069.htm
- http://m.wap.bwbkj.cn/snews/474828.htm
- http://m.wap.bwbkj.cn/snews/5066.htm
- http://m.wap.bwbkj.cn/snews/497302.htm
- http://m.wap.bwbkj.cn/snews/2728.htm
- http://m.wap.bwbkj.cn/snews/41151.htm
- http://m.wap.bwbkj.cn/snews/0141.htm
- http://m.wap.bwbkj.cn/snews/5106974.htm
- http://m.wap.bwbkj.cn/snews/477097.htm
- http://m.wap.bwbkj.cn/snews/6796927.htm
- http://m.wap.bwbkj.cn/snews/5874402.htm
- http://m.wap.bwbkj.cn/snews/77257.htm
- http://m.wap.bwbkj.cn/snews/93352.htm
- http://m.wap.bwbkj.cn/snews/7505.htm
- http://m.wap.bwbkj.cn/snews/6879738.htm
- http://m.wap.bwbkj.cn/snews/555833.htm
- http://m.wap.bwbkj.cn/snews/2852415.htm
- http://m.wap.bwbkj.cn/snews/7263.htm
- http://m.wap.bwbkj.cn/snews/382689.htm
- http://m.wap.bwbkj.cn/snews/4578616.htm
- http://m.wap.bwbkj.cn/snews/292229.htm
- http://m.wap.bwbkj.cn/snews/6760.htm
- http://m.wap.bwbkj.cn/snews/37169.htm
- http://m.wap.bwbkj.cn/snews/899805.htm
- http://m.wap.bwbkj.cn/snews/3762.htm
- http://m.wap.bwbkj.cn/snews/49074.htm
- http://m.wap.bwbkj.cn/snews/8804048.htm
- http://m.wap.bwbkj.cn/snews/89906.htm
- http://m.wap.bwbkj.cn/snews/3476944.htm
- http://m.wap.bwbkj.cn/snews/135957.htm
- http://m.wap.bwbkj.cn/snews/15199.htm
- http://m.wap.bwbkj.cn/snews/8425436.htm
- http://m.wap.bwbkj.cn/snews/12250.htm
- http://m.wap.bwbkj.cn/snews/825861.htm
- http://m.wap.bwbkj.cn/snews/6738.htm
- http://m.wap.bwbkj.cn/snews/127025.htm
- http://m.wap.bwbkj.cn/snews/535307.htm
- http://m.wap.bwbkj.cn/snews/6966390.htm
- http://m.wap.bwbkj.cn/snews/6344262.htm
- http://m.wap.bwbkj.cn/snews/986777.htm
- http://m.wap.bwbkj.cn/snews/9622646.htm
- http://m.wap.bwbkj.cn/snews/4335893.htm
- http://m.wap.bwbkj.cn/snews/9622.htm
- http://m.wap.bwbkj.cn/snews/2543260.htm
- http://m.wap.bwbkj.cn/snews/4416223.htm
- http://m.wap.bwbkj.cn/snews/0097218.htm
- http://m.wap.bwbkj.cn/snews/15472.htm
- http://m.wap.bwbkj.cn/snews/268000.htm
- http://m.wap.bwbkj.cn/snews/1745436.htm
- http://m.wap.bwbkj.cn/snews/581544.htm
- http://m.wap.bwbkj.cn/snews/037529.htm
- http://m.wap.bwbkj.cn/snews/306374.htm
- http://m.wap.bwbkj.cn/snews/1070591.htm
- http://m.wap.bwbkj.cn/snews/691091.htm
- http://m.wap.bwbkj.cn/snews/19576.htm
- http://m.wap.bwbkj.cn/snews/9730.htm
- http://m.wap.bwbkj.cn/snews/499665.htm
- http://m.wap.bwbkj.cn/snews/5588701.htm
- http://m.wap.bwbkj.cn/snews/43564.htm
- http://m.wap.bwbkj.cn/snews/56038.htm
- http://m.wap.bwbkj.cn/snews/0855065.htm
- http://m.wap.bwbkj.cn/snews/8599713.htm
- http://m.wap.bwbkj.cn/snews/8419.htm
- http://m.wap.bwbkj.cn/snews/91970.htm
- http://m.wap.bwbkj.cn/snews/6492.htm
- http://m.wap.bwbkj.cn/snews/4833173.htm
- http://m.wap.bwbkj.cn/snews/5855679.htm
- http://m.wap.bwbkj.cn/snews/4956.htm
- http://m.wap.bwbkj.cn/snews/7268.htm
- http://m.wap.bwbkj.cn/snews/039286.htm
- http://m.wap.bwbkj.cn/snews/1040.htm
- http://m.wap.bwbkj.cn/snews/01297.htm
- http://m.wap.bwbkj.cn/snews/58023.htm
- http://m.wap.bwbkj.cn/snews/7570268.htm
- http://m.wap.bwbkj.cn/snews/41628.htm
- http://m.wap.bwbkj.cn/snews/3896.htm
- http://m.wap.bwbkj.cn/snews/29699.htm
- http://m.wap.bwbkj.cn/snews/9077376.htm
- http://m.wap.bwbkj.cn/snews/145214.htm
- http://m.wap.bwbkj.cn/snews/05942.htm
- http://m.wap.bwbkj.cn/snews/49770.htm
- http://m.wap.bwbkj.cn/snews/1387.htm
- http://m.wap.bwbkj.cn/snews/9866223.htm
- http://m.wap.bwbkj.cn/snews/282508.htm
- http://m.wap.bwbkj.cn/snews/9018.htm
- http://m.wap.bwbkj.cn/snews/8435.htm
- http://m.wap.bwbkj.cn/snews/8162.htm
- http://m.wap.bwbkj.cn/snews/66594.htm
- http://m.wap.bwbkj.cn/snews/0196.htm
- http://m.wap.bwbkj.cn/snews/83060.htm
- http://m.wap.bwbkj.cn/snews/4998180.htm
- http://m.wap.bwbkj.cn/snews/3501.htm
- http://m.wap.bwbkj.cn/snews/7888.htm
- http://m.wap.bwbkj.cn/snews/7544.htm
- http://m.wap.bwbkj.cn/snews/3354274.htm
- http://m.wap.bwbkj.cn/snews/9083400.htm
- http://m.wap.bwbkj.cn/snews/4185444.htm
- http://m.wap.bwbkj.cn/snews/23516.htm
- http://m.wap.bwbkj.cn/snews/3996767.htm
- http://m.wap.bwbkj.cn/snews/9294.htm
- http://m.wap.bwbkj.cn/snews/5044.htm
- http://m.wap.bwbkj.cn/snews/845876.htm
- http://m.wap.bwbkj.cn/snews/1321296.htm
- http://m.wap.bwbkj.cn/snews/621795.htm
- http://m.wap.bwbkj.cn/snews/9759.htm
- http://m.wap.bwbkj.cn/snews/14480.htm
- http://m.wap.bwbkj.cn/snews/553118.htm
- http://m.wap.bwbkj.cn/snews/330423.htm
- http://m.wap.bwbkj.cn/snews/20335.htm
- http://m.wap.bwbkj.cn/snews/5976331.htm
- http://m.wap.bwbkj.cn/snews/44794.htm
- http://m.wap.bwbkj.cn/snews/08723.htm
- http://m.wap.bwbkj.cn/snews/7440.htm
- http://m.wap.bwbkj.cn/snews/72020.htm
- http://m.wap.bwbkj.cn/snews/959753.htm
- http://m.wap.bwbkj.cn/snews/64410.htm
- http://m.wap.bwbkj.cn/snews/615060.htm
- http://m.wap.bwbkj.cn/snews/885484.htm
- http://m.wap.bwbkj.cn/snews/06227.htm
- http://m.wap.bwbkj.cn/snews/673453.htm
- http://m.wap.bwbkj.cn/snews/972842.htm
- http://m.wap.bwbkj.cn/snews/156989.htm
- http://m.wap.bwbkj.cn/snews/7657939.htm
- http://m.wap.bwbkj.cn/snews/6458720.htm
- http://m.wap.bwbkj.cn/snews/0156234.htm
- http://m.wap.bwbkj.cn/snews/9550.htm
- http://m.wap.bwbkj.cn/snews/0707874.htm
- http://m.wap.bwbkj.cn/snews/71840.htm
- http://m.wap.bwbkj.cn/snews/2393525.htm
- http://m.wap.bwbkj.cn/snews/91329.htm
- http://m.wap.bwbkj.cn/snews/4850.htm
- http://m.wap.bwbkj.cn/snews/161226.htm
- http://m.wap.bwbkj.cn/snews/247141.htm
- http://m.wap.bwbkj.cn/snews/0536.htm

## 项目结构

```
weblink-navigator/
├── bin/                                 # 可执行脚本与命令行工具
│   ├── build.js                         # 构建主程序，读取数据并生成静态页面
│   ├── serve.js                         # 本地预览服务启动脚本
│   └── validate.js                      # 链接有效性校验独立脚本
├── config/                              # 配置文件目录
│   ├── site.yml                         # 站点全局配置（标题、描述、主题、分页等）
│   ├── categories.yml                   # 分类与标签的映射定义
│   └── validator.yml                    # 链接校验参数（超时、重试次数、并发数）
├── data/                                # 用户数据目录（核心内容）
│   ├── links.json                       # 主链接数据文件，包含所有收录链接的元信息
│   ├── import/                          # 导入文件存放目录，支持 CSV/JSON 批量导入
│   └── export/                          # 导出文件输出目录
├── src/                                 # 源码目录
│   ├── core/                            # 核心逻辑模块
│   │   ├── indexer.js                   # 链接索引生成器，负责构建搜索数据结构
│   │   ├── parser.js                    # 数据解析器，校验并转换原始数据格式
│   │   └── renderer.js                  # 页面渲染引擎，基于模板生成 HTML
│   ├── themes/                          # 主题模板目录
│   │   ├── default/                     # 默认主题（卡片式布局，浅色/深色自适应）
│   │   └── compact/                     # 紧凑主题（列表式布局，适合信息密集展示）
│   ├── assets/                          # 静态资源（CSS、JavaScript、字体、图标）
│   │   ├── css/                         # 样式文件（基于 CSS 变量，支持主题切换）
│   │   ├── js/                          # 前端交互脚本（搜索、过滤、点击统计）
│   │   └── images/                      # 默认图标与占位图
│   └── utils/                           # 工具函数库
│       ├── fetch.js                     # HTTP 请求封装，用于链接校验
│       ├── logger.js                    # 日志记录器，输出构建与校验日志
│       └── file.js                      # 文件读写工具，处理 JSON/CSV 操作
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 单元测试用例（基于 Jest）
│   └── fixtures/                        # 测试用数据样本
├── docs/                                # 文档目录（详见文档导航章节）
├── logs/                                # 运行时日志与校验报告输出目录
│   ├── build.log                        # 构建过程日志
│   └── validation-report.json           # 最新链接校验报告
├── dist/                                # 构建输出目录（生成的静态站点）
│   ├── index.html                       # 导航首页
│   ├── search.html                      # 搜索结果页
│   └── assets/                          # 构建后复用的静态资源副本
├── .env.example                         # 环境变量示例文件（配置校验密钥、代理等）
├── package.json                         # npm 依赖与脚本声明
├── package-lock.json                    # 依赖锁定文件
├── .gitignore                           # Git 版本控制忽略规则
└── README.md                            # 项目说明文档（当前文件）
```

## 贡献指南

**提交问题报告**：在 GitHub Issues 中提交 Bug 报告或功能请求时，请使用提供的模板，明确描述复现步骤、预期行为与实际行为，并附上运行环境信息（Node.js 版本、操作系统、构建日志片段）。对于链接校验相关的问题，请附带校验报告中的错误摘要。

**代码贡献流程**：Fork 本仓库至个人账号，在本地创建功能分支（命名格式为 `feature/简要描述` 或 `fix/问题编号`）。开发完成后，请确保新增代码通过所有现有单元测试，并为新增功能补充对应的测试用例。提交前运行 `npm run lint` 检查代码风格，确保与项目 ESLint 配置一致。最后发起 Pull Request 至主仓库的 `main` 分支，并在描述中关联相关 Issue 编号。

**数据贡献与审核**：若希望推荐优质技术链接加入默认资源列表，请按照 `data/links.json` 的格式提交包含标题、URL、分类、标签及简要摘要的条目。提交前请确认链接内容与项目定位（技术信息、开发工具、学术资源）相符，且链接状态可正常访问。项目维护者将在两周内完成审核与合并。

**文档完善与翻译**：欢迎对项目文档进行补充、修正或翻译。文档源文件位于 `docs/` 目录，采用 Markdown 格式。翻译时请保持术语一致性，并确保技术命令与代码示例的准确性。新增文档需在 `README.md` 的文档导航表格中同步更新条目。

**主题与模板扩展**：开发者可贡献新的主题模板。主题需放置在 `src/themes/` 下，遵循现有模板引擎的变量约定，并提供预览截图。提交新主题时，请同步更新 `config/site.yml` 中的主题列表说明，确保用户可通过配置切换。

## 常见问题

**构建过程报错“Cannot find module 'xxx'”如何解决？**

该错误通常表示项目依赖未完整安装，或 Node.js 版本与某些原生模块不兼容。首先确认 Node.js 版本满足 16.x 及以上要求，然后执行 `rm -rf node_modules package-lock.json` 清理旧依赖，再重新运行 `npm install`。若问题依旧，请检查网络环境是否能够正常访问 npm 公共仓库，或尝试切换为淘宝镜像源。

**搜索功能无法返回任何结果，即使输入明显存在的关键词？**

搜索功能依赖构建时生成的索引文件 `search-index.json`。请确认该文件在 `dist/` 目录下存在且大小不为 0。若文件缺失，可能是构建过程中数据解析失败导致的。检查 `data/links.json` 格式是否合法（使用 JSON 校验工具），确保所有条目均包含 `title` 字段且非空。重新运行 `npm run build` 并观察控制台是否有解析警告信息。

**如何更新已收录链接的标签或分类，而不丢失已有注释数据？**

本项目推荐所有元数据维护在 `data/links.json` 单一文件中。修改时建议使用支持 JSON Schema 的编辑器（如 VSCode 配合 YAML 插件）以避免格式错误。若需要批量修改，可利用 `data/import/` 目录下的 CSV 导入功能，覆盖现有数据前请备份原文件。对于注释等扩展字段，可通过 `extra` 对象存储，修改时注意合并而非覆盖。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:09
