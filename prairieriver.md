# WebIndex 聚合导航系统

WebIndex 是一个面向技术文档、开源资源与信息聚合的静态导航站点框架，专为需要高效管理和展示大量外链资源的开发者、技术博主及内容运营团队设计。系统以纯静态 HTML 为基础，结合轻量级脚本实现分类检索、标签过滤与访问统计，适用于日均 PV 十万级的中小型资源站部署场景。

项目本身不提供数据库或后端服务，所有资源数据以 JSON 配置文件驱动，构建时通过 Node.js 脚本生成完整站点页面，输出内容可直接托管至任意静态 Web 服务器、CDN 或对象存储服务。WebIndex 定位为开源技术生态中的“外链资源目录引擎”，帮助用户从无序的链接集合中快速定位高价值信息。

## 功能概览

**多级分类索引**：支持三级分类体系，每个资源条目可归属多个标签，分类结构通过配置文件灵活调整，无需修改模板代码。

**全文检索与即时过滤**：基于 Lunr.js 实现客户端全文搜索，输入关键词即可匹配标题、摘要、标签及来源域名，搜索结果实时高亮显示。

**访问热度统计**：集成轻量级点击计数模块，记录每个外链资源的访问次数，支持按热度排序展示热门资源榜单。

**响应式网格布局**：页面采用 CSS Grid 与 Flexbox 混合布局，在桌面、平板与移动设备上均保持良好的浏览体验，资源卡片自适应排列。

**批量导入与校验**：提供命令行工具支持从 CSV 或纯文本 URL 列表批量导入资源，自动去重并校验 URL 可访问性，生成结构化数据文件。

**自定义主题系统**：内置三套配色方案（浅色、深色、高对比度），用户可通过修改 CSS 变量快速定制品牌色调，满足不同站点的视觉需求。

**RSS 订阅源生成**：每次构建自动生成资源更新 RSS 2.0 订阅文件，支持外部阅读器订阅最新添加的外链资源。

**SEO 元数据注入**：为每个资源详情页自动生成 Open Graph 标签与结构化 JSON-LD 数据，便于搜索引擎收录与社交媒体分享预览。

## 应用场景

技术博客的外链资源库：技术博主可使用 WebIndex 整理个人博客中引用的所有外部参考链接、工具文档和开源项目地址，形成可检索、可分类的独立资源页面，替代传统的“友情链接”杂乱列表。

开源社区的知识导航站：开源项目社区可部署 WebIndex 作为社区文档门户的补充，集中收录项目相关的教程视频、插件生态、第三方工具及论坛讨论帖，降低新贡献者的信息查找门槛。

企业内部技术文档聚合：企业研发团队可将 WebIndex 部署在内网服务器，聚合各部门的技术规范、API 文档、运维手册和培训视频链接，实现内部知识资产的统一导航与检索。

在线教育课程资源目录：教育机构或独立讲师可使用 WebIndex 整理课程涉及的延伸阅读材料、代码仓库示例、在线练习平台和参考文献，按课程章节或难度等级分类，方便学员按需查阅。

个人书签管理系统的前端展示层：个人开发者可将浏览器书签导出为 CSV 文件，通过 WebIndex 的导入工具生成美观的在线书签墙，并配合全文搜索快速访问常用工具站点。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装项目依赖
npm install

# 准备资源数据文件，将用户提供的 URL 列表保存至 ./data/raw_urls.txt
# 每行一个 URL，系统将自动进行去重与校验

# 执行构建命令，生成静态站点至 ./dist 目录
npm run build

# 启动本地开发服务器，预览生成的站点
npm run serve

# 访问 http://localhost:3000 查看站点效果
```

构建完成后，将 `./dist` 目录下的所有文件上传至您的 Web 服务器根目录即可完成部署。如需增量更新资源，只需修改 `./data/resources.json` 文件后重新执行 `npm run build`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.0.0 及以上 | 构建脚本与命令行工具运行环境，推荐使用 LTS 版本 |
| npm | 8.0.0 及以上 | 包管理器，用于安装项目依赖及执行构建命令 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端页面运行环境，需支持 ES6 模块与 CSS Grid |
| 静态 Web 服务器 | Nginx 1.18+ / Apache 2.4+ / Caddy 2 | 生产环境部署所需，支持静态文件服务与 Gzip 压缩 |
| 磁盘空间 | 50 MB 以上 | 存放源码、构建产物及资源数据文件，实际占用视资源数量而定 |
| 内存 | 512 MB 以上 | 构建时 Node.js 进程内存需求，大型资源集（超 1 万条）建议提升至 1 GB |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/getting-started.md | 如何快速部署 WebIndex、首次构建需要哪些准备、如何添加第一批资源 |
| 配置手册 | /docs/configuration.md | 站点标题、分类体系、主题颜色、分页大小等所有配置项的含义与修改方法 |
| 数据规范 | /docs/data-format.md | 资源 JSON 数据结构定义、字段说明、标签命名规范及校验规则 |
| CLI 工具 | /docs/cli-commands.md | 构建、导入、校验、清理等所有命令行工具的使用示例与参数解释 |
| API 参考 | /docs/api-reference.md | 前端 JavaScript 模块接口、事件钩子及扩展开发所需的核心类说明 |
| 部署指南 | /docs/deployment.md | 如何部署到 Nginx、Apache、Cloudflare Pages、Netlify 等不同平台 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/0677.htm
- http://m.blog.ghtkgg.cn/nnews/816890.htm
- http://m.blog.ghtkgg.cn/nnews/297639.htm
- http://m.blog.ghtkgg.cn/nnews/8330089.htm
- http://m.blog.ghtkgg.cn/nnews/6011504.htm
- http://m.blog.ghtkgg.cn/nnews/713541.htm
- http://m.blog.ghtkgg.cn/nnews/2642935.htm
- http://m.blog.ghtkgg.cn/nnews/5868.htm
- http://m.blog.ghtkgg.cn/nnews/7029.htm
- http://m.blog.ghtkgg.cn/nnews/1547730.htm
- http://m.blog.ghtkgg.cn/nnews/5003183.htm
- http://m.blog.ghtkgg.cn/nnews/256385.htm
- http://m.blog.ghtkgg.cn/nnews/5845.htm
- http://m.blog.ghtkgg.cn/nnews/4301435.htm
- http://m.blog.ghtkgg.cn/nnews/645800.htm
- http://m.blog.ghtkgg.cn/nnews/639565.htm
- http://m.blog.ghtkgg.cn/nnews/0771716.htm
- http://m.blog.ghtkgg.cn/nnews/9449.htm
- http://m.blog.ghtkgg.cn/nnews/2272.htm
- http://m.blog.ghtkgg.cn/nnews/908981.htm
- http://m.blog.ghtkgg.cn/nnews/0389.htm
- http://m.blog.ghtkgg.cn/nnews/0716778.htm
- http://m.blog.ghtkgg.cn/nnews/219477.htm
- http://m.blog.ghtkgg.cn/nnews/176498.htm
- http://m.blog.ghtkgg.cn/nnews/9363.htm
- http://m.blog.ghtkgg.cn/nnews/4988.htm
- http://m.blog.ghtkgg.cn/nnews/4691547.htm
- http://m.blog.ghtkgg.cn/nnews/085722.htm
- http://m.blog.ghtkgg.cn/nnews/9091288.htm
- http://m.blog.ghtkgg.cn/nnews/34790.htm
- http://m.blog.ghtkgg.cn/nnews/0756.htm
- http://m.blog.ghtkgg.cn/nnews/152763.htm
- http://m.blog.ghtkgg.cn/nnews/1833518.htm
- http://m.blog.ghtkgg.cn/nnews/550950.htm
- http://m.blog.ghtkgg.cn/nnews/8343.htm
- http://m.blog.ghtkgg.cn/nnews/463377.htm
- http://m.blog.ghtkgg.cn/nnews/012850.htm
- http://m.blog.ghtkgg.cn/nnews/36631.htm
- http://m.blog.ghtkgg.cn/nnews/70065.htm
- http://m.blog.ghtkgg.cn/nnews/3138413.htm
- http://m.blog.ghtkgg.cn/nnews/9705737.htm
- http://m.blog.ghtkgg.cn/nnews/23483.htm
- http://m.blog.ghtkgg.cn/nnews/78517.htm
- http://m.blog.ghtkgg.cn/nnews/4471.htm
- http://m.blog.ghtkgg.cn/nnews/1690.htm
- http://m.blog.ghtkgg.cn/nnews/5342216.htm
- http://m.blog.ghtkgg.cn/nnews/080335.htm
- http://m.blog.ghtkgg.cn/nnews/514020.htm
- http://m.blog.ghtkgg.cn/nnews/76993.htm
- http://m.blog.ghtkgg.cn/nnews/2595292.htm
- http://m.blog.ghtkgg.cn/nnews/417081.htm
- http://m.blog.ghtkgg.cn/nnews/56830.htm
- http://m.blog.ghtkgg.cn/nnews/04736.htm
- http://m.blog.ghtkgg.cn/nnews/23589.htm
- http://m.blog.ghtkgg.cn/nnews/614532.htm
- http://m.blog.ghtkgg.cn/nnews/3678121.htm
- http://m.blog.ghtkgg.cn/nnews/2271.htm
- http://m.blog.ghtkgg.cn/nnews/156357.htm
- http://m.blog.ghtkgg.cn/nnews/118213.htm
- http://m.blog.ghtkgg.cn/nnews/39201.htm
- http://m.blog.ghtkgg.cn/nnews/274159.htm
- http://m.blog.ghtkgg.cn/nnews/21058.htm
- http://m.blog.ghtkgg.cn/nnews/1412.htm
- http://m.blog.ghtkgg.cn/nnews/4191176.htm
- http://m.blog.ghtkgg.cn/nnews/9754321.htm
- http://m.blog.ghtkgg.cn/nnews/6634687.htm
- http://m.blog.ghtkgg.cn/nnews/408183.htm
- http://m.blog.ghtkgg.cn/nnews/4089590.htm
- http://m.blog.ghtkgg.cn/nnews/6036910.htm
- http://m.blog.ghtkgg.cn/nnews/2624036.htm
- http://m.blog.ghtkgg.cn/nnews/9096126.htm
- http://m.blog.ghtkgg.cn/nnews/014797.htm
- http://m.blog.ghtkgg.cn/nnews/3101397.htm
- http://m.blog.ghtkgg.cn/nnews/8056951.htm
- http://m.blog.ghtkgg.cn/nnews/635739.htm
- http://m.blog.ghtkgg.cn/nnews/533380.htm
- http://m.blog.ghtkgg.cn/nnews/598721.htm
- http://m.blog.ghtkgg.cn/nnews/159697.htm
- http://m.blog.ghtkgg.cn/nnews/146635.htm
- http://m.blog.ghtkgg.cn/nnews/4194748.htm
- http://m.blog.ghtkgg.cn/nnews/0976041.htm
- http://m.blog.ghtkgg.cn/nnews/164900.htm
- http://m.blog.ghtkgg.cn/nnews/73768.htm
- http://m.blog.ghtkgg.cn/nnews/9412.htm
- http://m.blog.ghtkgg.cn/nnews/4692774.htm
- http://m.blog.ghtkgg.cn/nnews/485024.htm
- http://m.blog.ghtkgg.cn/nnews/8338474.htm
- http://m.blog.ghtkgg.cn/nnews/0422.htm
- http://m.blog.ghtkgg.cn/nnews/0394685.htm
- http://m.blog.ghtkgg.cn/nnews/5690220.htm
- http://m.blog.ghtkgg.cn/nnews/4570.htm
- http://m.blog.ghtkgg.cn/nnews/219286.htm
- http://m.blog.ghtkgg.cn/nnews/8223928.htm
- http://m.blog.ghtkgg.cn/nnews/7132064.htm
- http://m.blog.ghtkgg.cn/nnews/4994.htm
- http://m.blog.ghtkgg.cn/nnews/8286.htm
- http://m.blog.ghtkgg.cn/nnews/331748.htm
- http://m.blog.ghtkgg.cn/nnews/7746.htm
- http://m.blog.ghtkgg.cn/nnews/149220.htm
- http://m.blog.ghtkgg.cn/nnews/22598.htm
- http://m.blog.ghtkgg.cn/nnews/1506.htm
- http://m.blog.ghtkgg.cn/nnews/9392.htm
- http://m.blog.ghtkgg.cn/nnews/4991784.htm
- http://m.blog.ghtkgg.cn/nnews/8695841.htm
- http://m.blog.ghtkgg.cn/nnews/0776084.htm
- http://m.blog.ghtkgg.cn/nnews/0053776.htm
- http://m.blog.ghtkgg.cn/nnews/3631.htm
- http://m.blog.ghtkgg.cn/nnews/7165.htm
- http://m.blog.ghtkgg.cn/nnews/136054.htm
- http://m.blog.ghtkgg.cn/nnews/0340.htm
- http://m.blog.ghtkgg.cn/nnews/1919.htm
- http://m.blog.ghtkgg.cn/nnews/935064.htm
- http://m.blog.ghtkgg.cn/nnews/129864.htm
- http://m.blog.ghtkgg.cn/nnews/5058.htm
- http://m.blog.ghtkgg.cn/nnews/503009.htm
- http://m.blog.ghtkgg.cn/nnews/080660.htm
- http://m.blog.ghtkgg.cn/nnews/227069.htm
- http://m.blog.ghtkgg.cn/nnews/0314733.htm
- http://m.blog.ghtkgg.cn/nnews/341169.htm
- http://m.blog.ghtkgg.cn/nnews/31862.htm
- http://m.blog.ghtkgg.cn/nnews/770726.htm
- http://m.blog.ghtkgg.cn/nnews/5552812.htm
- http://m.blog.ghtkgg.cn/nnews/058868.htm
- http://m.blog.ghtkgg.cn/nnews/97681.htm
- http://m.blog.ghtkgg.cn/nnews/73131.htm
- http://m.blog.ghtkgg.cn/nnews/411384.htm
- http://m.blog.ghtkgg.cn/nnews/6401363.htm
- http://m.blog.ghtkgg.cn/nnews/5495.htm
- http://m.blog.ghtkgg.cn/nnews/05199.htm
- http://m.blog.ghtkgg.cn/nnews/1670.htm
- http://m.blog.ghtkgg.cn/nnews/62035.htm
- http://m.blog.ghtkgg.cn/nnews/90106.htm
- http://m.blog.ghtkgg.cn/nnews/549193.htm
- http://m.blog.ghtkgg.cn/nnews/551039.htm
- http://m.blog.ghtkgg.cn/nnews/54994.htm
- http://m.blog.ghtkgg.cn/nnews/3734944.htm
- http://m.blog.ghtkgg.cn/nnews/1001273.htm
- http://m.blog.ghtkgg.cn/nnews/128690.htm
- http://m.blog.ghtkgg.cn/nnews/80997.htm
- http://m.blog.ghtkgg.cn/nnews/55327.htm
- http://m.blog.ghtkgg.cn/nnews/89688.htm
- http://m.blog.ghtkgg.cn/nnews/3323.htm
- http://m.blog.ghtkgg.cn/nnews/55968.htm
- http://m.blog.ghtkgg.cn/nnews/64439.htm
- http://m.blog.ghtkgg.cn/nnews/364028.htm
- http://m.blog.ghtkgg.cn/nnews/73803.htm
- http://m.blog.ghtkgg.cn/nnews/0443.htm
- http://m.blog.ghtkgg.cn/nnews/9313.htm
- http://m.blog.ghtkgg.cn/nnews/80323.htm
- http://m.blog.ghtkgg.cn/nnews/408981.htm
- http://m.blog.ghtkgg.cn/nnews/857493.htm
- http://m.blog.ghtkgg.cn/nnews/5739220.htm
- http://m.blog.ghtkgg.cn/nnews/4514932.htm
- http://m.blog.ghtkgg.cn/nnews/30283.htm
- http://m.blog.ghtkgg.cn/nnews/4885202.htm
- http://m.blog.ghtkgg.cn/nnews/9185964.htm
- http://m.blog.ghtkgg.cn/nnews/65088.htm
- http://m.blog.ghtkgg.cn/nnews/3209464.htm
- http://m.blog.ghtkgg.cn/nnews/4103127.htm
- http://m.blog.ghtkgg.cn/nnews/6294428.htm
- http://m.blog.ghtkgg.cn/nnews/9942.htm
- http://m.blog.ghtkgg.cn/nnews/070842.htm
- http://m.blog.ghtkgg.cn/nnews/751885.htm
- http://m.blog.ghtkgg.cn/nnews/1008.htm
- http://m.blog.ghtkgg.cn/nnews/799821.htm
- http://m.blog.ghtkgg.cn/nnews/291517.htm
- http://m.blog.ghtkgg.cn/nnews/8749.htm
- http://m.blog.ghtkgg.cn/nnews/187833.htm
- http://m.blog.ghtkgg.cn/nnews/4461.htm
- http://m.blog.ghtkgg.cn/nnews/3180238.htm
- http://m.blog.ghtkgg.cn/nnews/905624.htm
- http://m.blog.ghtkgg.cn/nnews/59636.htm
- http://m.blog.ghtkgg.cn/nnews/06521.htm
- http://m.blog.ghtkgg.cn/nnews/83386.htm
- http://m.blog.ghtkgg.cn/nnews/99517.htm
- http://m.blog.ghtkgg.cn/nnews/6539.htm
- http://m.blog.ghtkgg.cn/nnews/23899.htm
- http://m.blog.ghtkgg.cn/nnews/3110.htm
- http://m.blog.ghtkgg.cn/nnews/5496617.htm
- http://m.blog.ghtkgg.cn/nnews/4411868.htm
- http://m.blog.ghtkgg.cn/nnews/8047.htm
- http://m.blog.ghtkgg.cn/nnews/323709.htm
- http://m.blog.ghtkgg.cn/nnews/00197.htm
- http://m.blog.ghtkgg.cn/nnews/5122.htm
- http://m.blog.ghtkgg.cn/nnews/10872.htm
- http://m.blog.ghtkgg.cn/nnews/2874344.htm
- http://m.blog.ghtkgg.cn/nnews/9334.htm
- http://m.blog.ghtkgg.cn/nnews/131863.htm
- http://m.blog.ghtkgg.cn/nnews/5100362.htm
- http://m.blog.ghtkgg.cn/nnews/526765.htm
- http://m.blog.ghtkgg.cn/nnews/634444.htm
- http://m.blog.ghtkgg.cn/nnews/3143.htm
- http://m.blog.ghtkgg.cn/nnews/951265.htm
- http://m.blog.ghtkgg.cn/nnews/960177.htm
- http://m.blog.ghtkgg.cn/nnews/59035.htm
- http://m.blog.ghtkgg.cn/nnews/1292.htm
- http://m.blog.ghtkgg.cn/nnews/0583.htm
- http://m.blog.ghtkgg.cn/nnews/4869.htm
- http://m.blog.ghtkgg.cn/nnews/3468440.htm
- http://m.blog.ghtkgg.cn/nnews/45246.htm
- http://m.blog.ghtkgg.cn/nnews/0622646.htm
- http://m.blog.ghtkgg.cn/nnews/338639.htm
- http://m.blog.ghtkgg.cn/nnews/418414.htm
- http://m.blog.ghtkgg.cn/nnews/609472.htm
- http://m.blog.ghtkgg.cn/nnews/205340.htm
- http://m.blog.ghtkgg.cn/nnews/50405.htm
- http://m.blog.ghtkgg.cn/nnews/29546.htm
- http://m.blog.ghtkgg.cn/nnews/766079.htm
- http://m.blog.ghtkgg.cn/nnews/71425.htm
- http://m.blog.ghtkgg.cn/nnews/9960.htm
- http://m.blog.ghtkgg.cn/nnews/589182.htm
- http://m.blog.ghtkgg.cn/nnews/93376.htm
- http://m.blog.ghtkgg.cn/nnews/47064.htm
- http://m.blog.ghtkgg.cn/nnews/045875.htm
- http://m.blog.ghtkgg.cn/nnews/5165671.htm
- http://m.blog.ghtkgg.cn/nnews/4466968.htm
- http://m.blog.ghtkgg.cn/nnews/182261.htm
- http://m.blog.ghtkgg.cn/nnews/6450205.htm
- http://m.blog.ghtkgg.cn/nnews/100968.htm
- http://m.blog.ghtkgg.cn/nnews/15003.htm
- http://m.blog.ghtkgg.cn/nnews/3249492.htm
- http://m.blog.ghtkgg.cn/nnews/66645.htm
- http://m.blog.ghtkgg.cn/nnews/884805.htm
- http://m.blog.ghtkgg.cn/nnews/8512.htm
- http://m.blog.ghtkgg.cn/nnews/5592440.htm
- http://m.blog.ghtkgg.cn/nnews/3587.htm
- http://m.blog.ghtkgg.cn/nnews/03412.htm
- http://m.blog.ghtkgg.cn/nnews/494309.htm
- http://m.blog.ghtkgg.cn/nnews/7724.htm
- http://m.blog.ghtkgg.cn/nnews/9585.htm
- http://m.blog.ghtkgg.cn/nnews/8650925.htm
- http://m.blog.ghtkgg.cn/nnews/1736.htm
- http://m.blog.ghtkgg.cn/nnews/354185.htm
- http://m.blog.ghtkgg.cn/nnews/6002.htm
- http://m.blog.ghtkgg.cn/nnews/7548546.htm
- http://m.blog.ghtkgg.cn/nnews/24445.htm
- http://m.blog.ghtkgg.cn/nnews/32483.htm
- http://m.blog.ghtkgg.cn/nnews/86418.htm
- http://m.blog.ghtkgg.cn/nnews/1580390.htm
- http://m.blog.ghtkgg.cn/nnews/349964.htm
- http://m.blog.ghtkgg.cn/nnews/9574102.htm
- http://m.blog.ghtkgg.cn/nnews/60485.htm
- http://m.blog.ghtkgg.cn/nnews/25879.htm
- http://m.blog.ghtkgg.cn/nnews/9164950.htm
- http://m.blog.ghtkgg.cn/nnews/8897.htm
- http://m.blog.ghtkgg.cn/nnews/9895.htm
- http://m.blog.ghtkgg.cn/nnews/7745384.htm
- http://m.blog.ghtkgg.cn/nnews/369977.htm
- http://m.blog.ghtkgg.cn/nnews/527486.htm
- http://m.blog.ghtkgg.cn/nnews/3387396.htm
- http://m.blog.ghtkgg.cn/nnews/6868056.htm
- http://m.blog.ghtkgg.cn/nnews/9360954.htm
- http://m.blog.ghtkgg.cn/nnews/3047.htm
- http://m.blog.ghtkgg.cn/nnews/0498777.htm
- http://m.blog.ghtkgg.cn/nnews/4514.htm
- http://m.blog.ghtkgg.cn/nnews/21076.htm
- http://m.blog.ghtkgg.cn/nnews/8881390.htm
- http://m.blog.ghtkgg.cn/nnews/4475.htm
- http://m.blog.ghtkgg.cn/nnews/3177430.htm
- http://m.blog.ghtkgg.cn/nnews/023626.htm
- http://m.blog.ghtkgg.cn/nnews/378341.htm
- http://m.blog.ghtkgg.cn/nnews/4690732.htm
- http://m.blog.ghtkgg.cn/nnews/8218.htm
- http://m.blog.ghtkgg.cn/nnews/24143.htm
- http://m.blog.ghtkgg.cn/nnews/9252436.htm
- http://m.blog.ghtkgg.cn/nnews/8173.htm
- http://m.blog.ghtkgg.cn/nnews/9490443.htm
- http://m.blog.ghtkgg.cn/nnews/9650.htm
- http://m.blog.ghtkgg.cn/nnews/2902.htm
- http://m.blog.ghtkgg.cn/nnews/024519.htm
- http://m.blog.ghtkgg.cn/nnews/587069.htm
- http://m.blog.ghtkgg.cn/nnews/486785.htm
- http://m.blog.ghtkgg.cn/nnews/30419.htm
- http://m.blog.ghtkgg.cn/nnews/23412.htm
- http://m.blog.ghtkgg.cn/nnews/7577585.htm
- http://m.blog.ghtkgg.cn/nnews/8562593.htm
- http://m.blog.ghtkgg.cn/nnews/567049.htm
- http://m.blog.ghtkgg.cn/nnews/6218463.htm
- http://m.blog.ghtkgg.cn/nnews/3496291.htm
- http://m.blog.ghtkgg.cn/nnews/3009390.htm
- http://m.blog.ghtkgg.cn/nnews/3120504.htm
- http://m.blog.ghtkgg.cn/nnews/4564.htm
- http://m.blog.ghtkgg.cn/nnews/0429580.htm
- http://m.blog.ghtkgg.cn/nnews/967781.htm
- http://m.blog.ghtkgg.cn/nnews/2336.htm
- http://m.blog.ghtkgg.cn/nnews/96518.htm
- http://m.blog.ghtkgg.cn/nnews/5133573.htm
- http://m.blog.ghtkgg.cn/nnews/852691.htm
- http://m.blog.ghtkgg.cn/nnews/2677019.htm
- http://m.blog.ghtkgg.cn/nnews/9743.htm
- http://m.blog.ghtkgg.cn/nnews/9832192.htm
- http://m.blog.ghtkgg.cn/nnews/4735.htm
- http://m.blog.ghtkgg.cn/nnews/455490.htm
- http://m.blog.ghtkgg.cn/nnews/404738.htm
- http://m.blog.ghtkgg.cn/nnews/4744.htm
- http://m.blog.ghtkgg.cn/nnews/21300.htm
- http://m.blog.ghtkgg.cn/nnews/1265142.htm
- http://m.blog.ghtkgg.cn/nnews/54430.htm
- http://m.blog.ghtkgg.cn/nnews/146085.htm
- http://m.blog.ghtkgg.cn/nnews/2103.htm

## 项目结构

```
webindex/
├── build/                           # 构建脚本目录
│   ├── builder.js                   # 主构建流程控制，读取配置与数据，生成 HTML 页面
│   ├── rss-generator.js             # RSS 订阅文件生成模块，按时间排序输出最新资源
│   ├── validator.js                 # URL 校验与资源数据格式验证工具
│   └── importer.js                  # CSV / 纯文本批量导入处理器，支持去重与增量更新
├── src/                             # 前端源代码目录
│   ├── assets/                      # 静态资源文件
│   │   ├── css/                     # 样式表文件
│   │   │   ├── base.css             # 全局基础样式，包含 CSS 变量定义与重置样式
│   │   │   ├── layout.css           # 页面布局样式，网格系统与响应式断点
│   │   │   └── themes/              # 主题风格子目录，存放各配色方案的覆盖样式
│   │   └── images/                  # 图片资源，含默认图标与占位图
│   ├── scripts/                     # 前端 JavaScript 模块
│   │   ├── search.js                # 基于 Lunr.js 的全文检索实现，包含索引构建与查询解析
│   │   ├── counter.js               # 访问计数模块，通过 Beacon API 发送点击统计
│   │   ├── render.js                # 资源卡片渲染引擎，支持分类切换与分页加载
│   │   └── utils.js                 # 通用工具函数库，包含 URL 处理、日期格式化等
│   └── templates/                   # HTML 模板文件
│       ├── index.html               # 首页模板，展示分类导航与热门资源
│       ├── category.html            # 分类详情页模板，按标签筛选资源列表
│       └── detail.html              # 资源详情页模板，展示完整摘要与访问入口
├── data/                            # 数据配置目录
│   ├── resources.json               # 核心资源数据文件，包含所有外链条目及元信息
│   ├── categories.json              # 分类体系定义，配置分类名称、层级与显示顺序
│   ├── site.config.json             # 站点全局配置，包含标题、描述、主题等参数
│   └── raw_urls.txt                 # 原始 URL 列表输入文件，由用户维护，构建时自动导入
├── dist/                            # 构建输出目录（生成产物，不纳入版本控制）
│   ├── index.html                   # 生成的首页文件
│   ├── category/                    # 分类页面子目录
│   ├── detail/                      # 资源详情页面子目录
│   ├── feed.xml                     # RSS 订阅源文件
│   └── assets/                      # 编译后的静态资源文件
├── tests/                           # 单元测试与集成测试目录
│   ├── validator.test.js            # 数据校验模块的单元测试用例
│   └── builder.test.js              # 构建流程的集成测试用例
├── docs/                            # 项目文档目录
│   ├── getting-started.md           # 入门指南
│   ├── configuration.md             # 配置手册
│   ├── data-format.md               # 数据规范
│   ├── cli-commands.md              # CLI 工具命令参考
│   ├── api-reference.md             # API 参考文档
│   └── deployment.md                # 部署指南
├── .eslintrc.js                     # ESLint 代码检查配置文件
├── .gitignore                       # Git 版本忽略规则配置
├── package.json                     # npm 包管理配置，定义依赖与脚本命令
├── package-lock.json                # npm 依赖版本锁定文件
└── README.md                        # 项目自述文件（本文件）
```

## 贡献指南

1. 复刻项目仓库至个人账户，在本地克隆复刻后的代码库，建议使用 `--depth=1` 进行浅克隆以减少下载时间。创建新的功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。

2. 安装项目开发依赖，执行 `npm install` 安装所有必要的构建工具与测试框架。运行 `npm run test` 确保现有测试用例全部通过，以验证本地环境配置正确。

3. 提交代码前运行 `npm run lint` 进行代码风格检查，确保 JavaScript 与 CSS 代码符合项目 ESLint 与 Stylelint 规则。新增功能需补充对应的单元测试用例，测试覆盖率不应低于现有水平。

4. 编写清晰的提交信息，遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`chore:` 等前缀。提交前执行 `npm run build` 验证构建流程可完整执行且输出产物无异常。

5. 向主仓库发起 Pull Request，描述中需说明变更目的、实现方案及影响范围。项目维护者将在三个工作日内进行 Code Review，通过后合并至主干分支。

## 常见问题

问：资源数量很大时，构建速度变慢甚至内存溢出，如何优化？

答：当资源条目超过 5000 条时，建议使用 `npm run build -- --chunk-size=500` 参数启用分块构建模式，该模式将资源分批处理，每批 500 条，可显著降低内存峰值消耗。同时建议在 `package.json` 中为构建脚本增加 `NODE_OPTIONS="--max-old-space-size=1024"` 环境变量以增加 Node.js 内存上限。若仍遇性能瓶颈，可将资源数据按年份或分类拆分为多个 JSON 文件，使用多页面模式分别构建。

问：部署后点击资源链接跳转时提示“危险网站”或被浏览器拦截，如何处理？

答：WebIndex 本身仅提供外链导航功能，不控制第三方站点的安全状态。出现拦截提示通常是因为目标站点被浏览器安全策略标记为低信誉域名。建议在站点页脚添加免责声明，明确说明本导航站仅做信息汇总，不对外链内容负责。同时可在 `site.config.json` 中启用“外链跳转中间页”功能，即点击资源后先进入一个带有安全提示的过渡页面，用户确认后再跳转至目标 URL，该机制可降低浏览器的直接拦截概率。若确认某目标站点安全但被误报，可引导用户手动添加信任或使用企业级浏览器的策略例外。

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
