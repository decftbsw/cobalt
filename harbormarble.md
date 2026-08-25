# WebLink Navigator

WebLink Navigator 是一个面向技术研究人员、信息分析人员和内容聚合者的高性能外链资源导航与归档系统。该项目旨在解决分散于各类技术博客、新闻站点和文档平台中的高质量外链难以统一管理和快速检索的问题。通过将大量分散的 URL 资源进行集中化索引和分类存储，WebLink Navigator 为用户提供了一个稳定、可扩展、可自托管的资源链接枢纽。

本项目定位于中大规模外链数据的结构化存储与展示，尤其适用于需要定期采集、整理和分享技术资讯、行业动态或学术参考链接的个人或团队。WebLink Navigator 不生产内容，而是通过高效的组织方式帮助用户建立自身的知识外脑。

## 功能概览

**结构化资源索引**：将所有收录的 URL 按照自定义分类和标签体系进行组织，支持多维度筛选与排序。

**自动化链接健康检查**：内置链接可用性检测模块，定期扫描资源列表中的每一个 URL，标记失效或重定向链接，并生成报告。

**全文元数据提取**：对每个收录的 URL 自动抓取页面标题、描述、关键词和发布时间，形成丰富的资源卡片。

**快速检索与过滤**：提供基于标题、域名、分类和日期范围的全文检索功能，支持正则表达式和模糊匹配模式。

**批量导入与导出**：支持通过 CSV、JSON 和纯文本列表格式批量导入 URL 资源，同时支持将整个索引导出为静态 HTML 或 Markdown 文档。

**响应式资源展示面板**：提供面向桌面和移动设备的自适应界面，以列表、网格和时间线三种视图展示资源。

**用户自定义标签体系**：允许用户为每个资源添加自定义标签，并基于标签创建动态聚合视图，实现个性化分类。

**定期备份与版本记录**：自动对资源索引库进行增量备份，并记录每次更新的变更日志，支持回溯至任意历史版本。

## 应用场景

**技术团队内部知识库构建**：技术团队可以将日常阅读的技术博客、官方文档、API 参考和问题讨论贴统一收录至 WebLink Navigator，形成团队共享的技术参考资源池，新成员入职时可快速浏览团队积累的优质外链。

**行业资讯每日汇总**：内容运营人员或行业分析师可以使用 WebLink Navigator 收集当日发布的行业新闻、分析报告和官方公告，通过标签和日期筛选快速生成每日简报，提高信息整合效率。

**开源项目文档外链管理**：开源项目维护者可以将项目依赖的第三方库文档、社区讨论帖、扩展阅读材料和版本发布说明集中存放于 WebLink Navigator，避免在项目 README 中堆砌过长外链，同时便于版本迭代时更新链接。

**学术研究文献参考归档**：研究人员在查阅论文、预印本、技术白皮书和实验数据页面时，可通过 WebLink Navigator 统一记录参考链接，并添加研究主题标签，为后续撰写文献综述或实验报告提供快捷引用来源。

**个人博客友情链接与资源推荐**：独立博客作者可以利用 WebLink Navigator 管理博客侧边栏或友情页面中推荐的站点和文章链接，定期检查链接可用性，确保对外推荐的资源长期有效。

## 快速开始

以下命令演示了如何在本地环境中克隆代码仓库、安装项目依赖并启动开发服务。

```bash
# 克隆代码仓库至本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 安装后端与前端依赖（使用 npm，适用于 Node.js 18+ 环境）
npm install

# 初始化 SQLite 数据库结构并导入示例资源
npm run init-db

# 启动开发服务器（默认监听 3000 端口）
npm run dev
```

启动成功后，在浏览器中访问 http://localhost:3000 即可查看资源面板。如需构建生产环境静态文件，请执行 `npm run build`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.0.0 或更高 | 项目运行时环境，用于执行 JavaScript 代码与包管理 |
| npm | 9.0.0 或更高 | Node.js 包管理器，用于安装项目依赖 |
| SQLite3 | 3.31.0 或更高 | 嵌入式关系型数据库，用于存储资源索引和元数据 |
| Git | 2.25.0 或更高 | 版本控制工具，用于克隆仓库和管理代码更新 |
| 操作系统 | Linux (Ubuntu 20.04+) / macOS 11+ / Windows 10+ | 支持主流操作系统，生产环境推荐 Linux |
| 内存 | 最低 512 MB，推荐 1 GB 以上 | 用于运行数据库服务和 Web 服务进程 |
| 磁盘空间 | 最低 200 MB | 用于存储代码、数据库文件和备份数据（随资源数量增长） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何添加资源、创建标签、检索链接、导出数据及配置个人偏好 |
| 开发者指南 | /docs/developer-guide/ | 如何二次开发、扩展数据模型、增加新适配器及参与核心代码贡献 |
| 部署运维手册 | /docs/deployment/ | 如何在生产环境部署（Nginx 反向代理、PM2 管理、数据库迁移、备份策略） |
| API 参考文档 | /docs/api-reference/ | 后端 RESTful API 的端点列表、请求参数、响应格式及鉴权方式 |
| 变更日志 | /CHANGELOG.md | 每个版本的更新内容、修复的缺陷、已知问题及升级注意事项 |

## 资源列表

- http://m.blog.oexnr.cn/snews/61700.htm
- http://m.blog.oexnr.cn/snews/26139.htm
- http://m.blog.oexnr.cn/snews/7820.htm
- http://m.blog.oexnr.cn/snews/2997.htm
- http://m.blog.oexnr.cn/snews/4162.htm
- http://m.blog.oexnr.cn/snews/742286.htm
- http://m.blog.oexnr.cn/snews/5999681.htm
- http://m.blog.oexnr.cn/snews/38318.htm
- http://m.blog.oexnr.cn/snews/89192.htm
- http://m.blog.oexnr.cn/snews/05692.htm
- http://m.blog.oexnr.cn/snews/7766.htm
- http://m.blog.oexnr.cn/snews/278724.htm
- http://m.blog.oexnr.cn/snews/6717627.htm
- http://m.blog.oexnr.cn/snews/6250677.htm
- http://m.blog.oexnr.cn/snews/2862506.htm
- http://m.blog.oexnr.cn/snews/6405.htm
- http://m.blog.oexnr.cn/snews/486890.htm
- http://m.blog.oexnr.cn/snews/85988.htm
- http://m.blog.oexnr.cn/snews/5200086.htm
- http://m.blog.oexnr.cn/snews/8151.htm
- http://m.blog.oexnr.cn/snews/8192.htm
- http://m.blog.oexnr.cn/snews/4160608.htm
- http://m.blog.oexnr.cn/snews/9891.htm
- http://m.blog.oexnr.cn/snews/08564.htm
- http://m.blog.oexnr.cn/snews/4578.htm
- http://m.blog.oexnr.cn/snews/894328.htm
- http://m.blog.oexnr.cn/snews/22660.htm
- http://m.blog.oexnr.cn/snews/4271774.htm
- http://m.blog.oexnr.cn/snews/87336.htm
- http://m.blog.oexnr.cn/snews/9531.htm
- http://m.blog.oexnr.cn/snews/8551866.htm
- http://m.blog.oexnr.cn/snews/96963.htm
- http://m.blog.oexnr.cn/snews/38340.htm
- http://m.blog.oexnr.cn/snews/7927680.htm
- http://m.blog.oexnr.cn/snews/227236.htm
- http://m.blog.oexnr.cn/snews/95230.htm
- http://m.blog.oexnr.cn/snews/00871.htm
- http://m.blog.oexnr.cn/snews/72626.htm
- http://m.blog.oexnr.cn/snews/344903.htm
- http://m.blog.oexnr.cn/snews/923969.htm
- http://m.blog.oexnr.cn/snews/4171230.htm
- http://m.blog.oexnr.cn/snews/3876.htm
- http://m.blog.oexnr.cn/snews/28564.htm
- http://m.blog.oexnr.cn/snews/56602.htm
- http://m.blog.oexnr.cn/snews/0159027.htm
- http://m.blog.oexnr.cn/snews/1784295.htm
- http://m.blog.oexnr.cn/snews/98468.htm
- http://m.blog.oexnr.cn/snews/940267.htm
- http://m.blog.oexnr.cn/snews/830831.htm
- http://m.blog.oexnr.cn/snews/3667008.htm
- http://m.blog.oexnr.cn/snews/03592.htm
- http://m.blog.oexnr.cn/snews/3845015.htm
- http://m.blog.oexnr.cn/snews/1986.htm
- http://m.blog.oexnr.cn/snews/771193.htm
- http://m.blog.oexnr.cn/snews/54181.htm
- http://m.blog.oexnr.cn/snews/5256146.htm
- http://m.blog.oexnr.cn/snews/873979.htm
- http://m.blog.oexnr.cn/snews/6134.htm
- http://m.blog.oexnr.cn/snews/0387327.htm
- http://m.blog.oexnr.cn/snews/401459.htm
- http://m.blog.oexnr.cn/snews/6756464.htm
- http://m.blog.oexnr.cn/snews/3297.htm
- http://m.blog.oexnr.cn/snews/6631.htm
- http://m.blog.oexnr.cn/snews/4546649.htm
- http://m.blog.oexnr.cn/snews/3282.htm
- http://m.blog.oexnr.cn/snews/007112.htm
- http://m.blog.oexnr.cn/snews/88655.htm
- http://m.blog.oexnr.cn/snews/638917.htm
- http://m.blog.oexnr.cn/snews/964798.htm
- http://m.blog.oexnr.cn/snews/1068.htm
- http://m.blog.oexnr.cn/snews/513210.htm
- http://m.blog.oexnr.cn/snews/7137833.htm
- http://m.blog.oexnr.cn/snews/2381569.htm
- http://m.blog.oexnr.cn/snews/0447899.htm
- http://m.blog.oexnr.cn/snews/7238292.htm
- http://m.blog.oexnr.cn/snews/6752.htm
- http://m.blog.oexnr.cn/snews/7420014.htm
- http://m.blog.oexnr.cn/snews/118683.htm
- http://m.blog.oexnr.cn/snews/03929.htm
- http://m.blog.oexnr.cn/snews/048273.htm
- http://m.blog.oexnr.cn/snews/122717.htm
- http://m.blog.oexnr.cn/snews/06751.htm
- http://m.blog.oexnr.cn/snews/8473.htm
- http://m.blog.oexnr.cn/snews/1231183.htm
- http://m.blog.oexnr.cn/snews/1856191.htm
- http://m.blog.oexnr.cn/snews/0337.htm
- http://m.blog.oexnr.cn/snews/905762.htm
- http://m.blog.oexnr.cn/snews/011124.htm
- http://m.blog.oexnr.cn/snews/0129671.htm
- http://m.blog.oexnr.cn/snews/9854.htm
- http://m.blog.oexnr.cn/snews/1001178.htm
- http://m.blog.oexnr.cn/snews/9341.htm
- http://m.blog.oexnr.cn/snews/9667.htm
- http://m.blog.oexnr.cn/snews/0848933.htm
- http://m.blog.oexnr.cn/snews/32210.htm
- http://m.blog.oexnr.cn/snews/7773837.htm
- http://m.blog.oexnr.cn/snews/830834.htm
- http://m.blog.oexnr.cn/snews/7179.htm
- http://m.blog.oexnr.cn/snews/287474.htm
- http://m.blog.oexnr.cn/snews/41946.htm
- http://m.blog.oexnr.cn/snews/7122.htm
- http://m.blog.oexnr.cn/snews/0663.htm
- http://m.blog.oexnr.cn/snews/571254.htm
- http://m.blog.oexnr.cn/snews/208097.htm
- http://m.blog.oexnr.cn/snews/47001.htm
- http://m.blog.oexnr.cn/snews/62556.htm
- http://m.blog.oexnr.cn/snews/964642.htm
- http://m.blog.oexnr.cn/snews/3401.htm
- http://m.blog.oexnr.cn/snews/51552.htm
- http://m.blog.oexnr.cn/snews/25511.htm
- http://m.blog.oexnr.cn/snews/3026284.htm
- http://m.blog.oexnr.cn/snews/5067.htm
- http://m.blog.oexnr.cn/snews/4332.htm
- http://m.blog.oexnr.cn/snews/72259.htm
- http://m.blog.oexnr.cn/snews/74172.htm
- http://m.blog.oexnr.cn/snews/2113.htm
- http://m.blog.oexnr.cn/snews/15210.htm
- http://m.blog.oexnr.cn/snews/288552.htm
- http://m.blog.oexnr.cn/snews/1049357.htm
- http://m.blog.oexnr.cn/snews/300221.htm
- http://m.blog.oexnr.cn/snews/46432.htm
- http://m.blog.oexnr.cn/snews/648487.htm
- http://m.blog.oexnr.cn/snews/7880.htm
- http://m.blog.oexnr.cn/snews/4409683.htm
- http://m.blog.oexnr.cn/snews/9726.htm
- http://m.blog.oexnr.cn/snews/59963.htm
- http://m.blog.oexnr.cn/snews/4816622.htm
- http://m.blog.oexnr.cn/snews/4934078.htm
- http://m.blog.oexnr.cn/snews/43038.htm
- http://m.blog.oexnr.cn/snews/48214.htm
- http://m.blog.oexnr.cn/snews/7973693.htm
- http://m.blog.oexnr.cn/snews/4718.htm
- http://m.blog.oexnr.cn/snews/2072.htm
- http://m.blog.oexnr.cn/snews/0607.htm
- http://m.blog.oexnr.cn/snews/4492939.htm
- http://m.blog.oexnr.cn/snews/146358.htm
- http://m.blog.oexnr.cn/snews/71220.htm
- http://m.blog.oexnr.cn/snews/03749.htm
- http://m.blog.oexnr.cn/snews/89342.htm
- http://m.blog.oexnr.cn/snews/90623.htm
- http://m.blog.oexnr.cn/snews/355727.htm
- http://m.blog.oexnr.cn/snews/34618.htm
- http://m.blog.oexnr.cn/snews/8734986.htm
- http://m.blog.oexnr.cn/snews/46493.htm
- http://m.blog.oexnr.cn/snews/304633.htm
- http://m.blog.oexnr.cn/snews/008706.htm
- http://m.blog.oexnr.cn/snews/42290.htm
- http://m.blog.oexnr.cn/snews/5673169.htm
- http://m.blog.oexnr.cn/snews/8898.htm
- http://m.blog.oexnr.cn/snews/82946.htm
- http://m.blog.oexnr.cn/snews/4652.htm
- http://m.blog.oexnr.cn/snews/51807.htm
- http://m.blog.oexnr.cn/snews/396860.htm
- http://m.blog.oexnr.cn/snews/7155.htm
- http://m.blog.oexnr.cn/snews/30979.htm
- http://m.blog.oexnr.cn/snews/96790.htm
- http://m.blog.oexnr.cn/snews/7249.htm
- http://m.blog.oexnr.cn/snews/06306.htm
- http://m.blog.oexnr.cn/snews/2326133.htm
- http://m.blog.oexnr.cn/snews/890767.htm
- http://m.blog.oexnr.cn/snews/9155924.htm
- http://m.blog.oexnr.cn/snews/3180379.htm
- http://m.blog.oexnr.cn/snews/2973684.htm
- http://m.blog.oexnr.cn/snews/415264.htm
- http://m.blog.oexnr.cn/snews/792831.htm
- http://m.blog.oexnr.cn/snews/948598.htm
- http://m.blog.oexnr.cn/snews/9119.htm
- http://m.blog.oexnr.cn/snews/0508.htm
- http://m.blog.oexnr.cn/snews/93480.htm
- http://m.blog.oexnr.cn/snews/6029.htm
- http://m.blog.oexnr.cn/snews/0453294.htm
- http://m.blog.oexnr.cn/snews/6123.htm
- http://m.blog.oexnr.cn/snews/0210.htm
- http://m.blog.oexnr.cn/snews/76449.htm
- http://m.blog.oexnr.cn/snews/2973.htm
- http://m.blog.oexnr.cn/snews/85865.htm
- http://m.blog.oexnr.cn/snews/9690883.htm
- http://m.blog.oexnr.cn/snews/104197.htm
- http://m.blog.oexnr.cn/snews/0933783.htm
- http://m.blog.oexnr.cn/snews/8054164.htm
- http://m.blog.oexnr.cn/snews/3672274.htm
- http://m.blog.oexnr.cn/snews/6614059.htm
- http://m.blog.oexnr.cn/snews/5068.htm
- http://m.blog.oexnr.cn/snews/8186.htm
- http://m.blog.oexnr.cn/snews/90493.htm
- http://m.blog.oexnr.cn/snews/819629.htm
- http://m.blog.oexnr.cn/snews/2340.htm
- http://m.blog.oexnr.cn/snews/9211.htm
- http://m.blog.oexnr.cn/snews/84468.htm
- http://m.blog.oexnr.cn/snews/5507812.htm
- http://m.blog.oexnr.cn/snews/902165.htm
- http://m.blog.oexnr.cn/snews/274599.htm
- http://m.blog.oexnr.cn/snews/29887.htm
- http://m.blog.oexnr.cn/snews/6623.htm
- http://m.blog.oexnr.cn/snews/08611.htm
- http://m.blog.oexnr.cn/snews/4223801.htm
- http://m.blog.oexnr.cn/snews/32198.htm
- http://m.blog.oexnr.cn/snews/2909.htm
- http://m.blog.oexnr.cn/snews/16747.htm
- http://m.blog.oexnr.cn/snews/809864.htm
- http://m.blog.oexnr.cn/snews/82106.htm
- http://m.blog.oexnr.cn/snews/56081.htm
- http://m.blog.oexnr.cn/snews/9153597.htm
- http://m.blog.oexnr.cn/snews/3895700.htm
- http://m.blog.oexnr.cn/snews/2149.htm
- http://m.blog.oexnr.cn/snews/12832.htm
- http://m.blog.oexnr.cn/snews/73411.htm
- http://m.blog.oexnr.cn/snews/0688221.htm
- http://m.blog.oexnr.cn/snews/1996.htm
- http://m.blog.oexnr.cn/snews/47536.htm
- http://m.blog.oexnr.cn/snews/3050310.htm
- http://m.blog.oexnr.cn/snews/9274608.htm
- http://m.blog.oexnr.cn/snews/980851.htm
- http://m.blog.oexnr.cn/snews/62140.htm
- http://m.blog.oexnr.cn/snews/55995.htm
- http://m.blog.oexnr.cn/snews/7387705.htm
- http://m.blog.oexnr.cn/snews/33211.htm
- http://m.blog.oexnr.cn/snews/5247533.htm
- http://m.blog.oexnr.cn/snews/08465.htm
- http://m.blog.oexnr.cn/snews/85860.htm
- http://m.blog.oexnr.cn/snews/9242982.htm
- http://m.blog.oexnr.cn/snews/698019.htm
- http://m.blog.oexnr.cn/snews/8934.htm
- http://m.blog.oexnr.cn/snews/2990364.htm
- http://m.blog.oexnr.cn/snews/3514495.htm
- http://m.blog.oexnr.cn/snews/81329.htm
- http://m.blog.oexnr.cn/snews/1279.htm
- http://m.blog.oexnr.cn/snews/253852.htm
- http://m.blog.oexnr.cn/snews/1286.htm
- http://m.blog.oexnr.cn/snews/0185139.htm
- http://m.blog.oexnr.cn/snews/6611.htm
- http://m.blog.oexnr.cn/snews/765080.htm
- http://m.blog.oexnr.cn/snews/605986.htm
- http://m.blog.oexnr.cn/snews/6759896.htm
- http://m.blog.oexnr.cn/snews/3040.htm
- http://m.blog.oexnr.cn/snews/24004.htm
- http://m.blog.oexnr.cn/snews/7801.htm
- http://m.blog.oexnr.cn/snews/188344.htm
- http://m.blog.oexnr.cn/snews/3967340.htm
- http://m.blog.oexnr.cn/snews/2408.htm
- http://m.blog.oexnr.cn/snews/15237.htm
- http://m.blog.oexnr.cn/snews/563991.htm
- http://m.blog.oexnr.cn/snews/67716.htm
- http://m.blog.oexnr.cn/snews/781147.htm
- http://m.blog.oexnr.cn/snews/9424.htm
- http://m.blog.oexnr.cn/snews/75404.htm
- http://m.blog.oexnr.cn/snews/505909.htm
- http://m.blog.oexnr.cn/snews/3394526.htm
- http://m.blog.oexnr.cn/snews/49238.htm
- http://m.blog.oexnr.cn/snews/7951867.htm
- http://m.blog.oexnr.cn/snews/729857.htm
- http://m.blog.oexnr.cn/snews/6741204.htm
- http://m.blog.oexnr.cn/snews/0919.htm
- http://m.blog.oexnr.cn/snews/781895.htm
- http://m.blog.oexnr.cn/snews/8341621.htm
- http://m.blog.oexnr.cn/snews/5260549.htm
- http://m.blog.oexnr.cn/snews/798765.htm
- http://m.blog.oexnr.cn/snews/7768868.htm
- http://m.blog.oexnr.cn/snews/471158.htm
- http://m.blog.oexnr.cn/snews/15202.htm
- http://m.blog.oexnr.cn/snews/467886.htm
- http://m.blog.oexnr.cn/snews/34247.htm
- http://m.blog.oexnr.cn/snews/545628.htm
- http://m.blog.oexnr.cn/snews/2239782.htm
- http://m.blog.oexnr.cn/snews/7837.htm
- http://m.blog.oexnr.cn/snews/14043.htm
- http://m.blog.oexnr.cn/snews/98245.htm
- http://m.blog.oexnr.cn/snews/3033543.htm
- http://m.blog.oexnr.cn/snews/063615.htm
- http://m.blog.oexnr.cn/snews/90662.htm
- http://m.blog.oexnr.cn/snews/352424.htm
- http://m.blog.oexnr.cn/snews/0206.htm
- http://m.blog.oexnr.cn/snews/6590.htm
- http://m.blog.oexnr.cn/snews/292368.htm
- http://m.blog.oexnr.cn/snews/715174.htm
- http://m.blog.oexnr.cn/snews/7783.htm
- http://m.blog.oexnr.cn/snews/98292.htm
- http://m.blog.oexnr.cn/snews/2807720.htm
- http://m.blog.oexnr.cn/snews/440654.htm
- http://m.blog.oexnr.cn/snews/9652238.htm
- http://m.blog.oexnr.cn/snews/746475.htm
- http://m.blog.oexnr.cn/snews/8398.htm
- http://m.blog.oexnr.cn/snews/741693.htm
- http://m.blog.oexnr.cn/snews/6284473.htm
- http://m.blog.oexnr.cn/snews/0573.htm
- http://m.blog.oexnr.cn/snews/004328.htm
- http://m.blog.oexnr.cn/snews/38533.htm
- http://m.blog.oexnr.cn/snews/5655.htm
- http://m.blog.oexnr.cn/snews/3318.htm
- http://m.blog.oexnr.cn/snews/98736.htm
- http://m.blog.oexnr.cn/snews/96910.htm
- http://m.blog.oexnr.cn/snews/92884.htm
- http://m.blog.oexnr.cn/snews/8782084.htm
- http://m.blog.oexnr.cn/snews/4681.htm
- http://m.blog.oexnr.cn/snews/19629.htm
- http://m.blog.oexnr.cn/snews/676148.htm
- http://m.blog.oexnr.cn/snews/29370.htm
- http://m.blog.oexnr.cn/snews/837869.htm
- http://m.blog.oexnr.cn/snews/9362924.htm
- http://m.blog.oexnr.cn/snews/669509.htm

## 项目结构

```
weblink-navigator/
├── src/                           # 源代码主目录
│   ├── server/                    # 后端服务代码
│   │   ├── app.js                 # Express 应用主入口，配置中间件与路由
│   │   ├── routes/                # RESTful API 路由定义（resources, tags, health）
│   │   ├── controllers/           # 请求处理控制器，执行业务逻辑
│   │   ├── models/                # 数据库模型定义（Resource, Tag, Backup）
│   │   └── workers/               # 后台任务进程（链接健康检查、元数据抓取）
│   ├── client/                    # 前端用户界面代码
│   │   ├── pages/                 # 页面级组件（Dashboard, ResourceList, Settings）
│   │   ├── components/            # 可复用 UI 组件（ResourceCard, TagFilter, SearchBar）
│   │   ├── hooks/                 # React 自定义钩子（useResources, useTags）
│   │   └── styles/                # 全局样式与主题变量（CSS Modules）
│   └── shared/                    # 前后端共享代码
│       ├── types/                 # TypeScript 类型定义（Resource, Tag, ApiResponse）
│       └── utils/                 # 通用工具函数（日期格式化、URL 验证）
├── data/                          # 数据存储目录
│   ├── database.sqlite            # SQLite 主数据库文件
│   ├── backups/                   # 数据库自动备份存放目录
│   └── logs/                      # 应用运行日志（访问日志、错误日志）
├── docs/                          # 项目文档（用户手册、开发者指南、API 文档）
├── scripts/                       # 运维与初始化脚本（init-db.js, backup.js, migrate.js）
├── tests/                         # 单元测试与集成测试（Mocha + Chai）
├── .env.example                   # 环境变量配置模板
├── package.json                   # npm 项目清单与依赖声明
├── README.md                      # 项目概览文档（即本文档）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

欢迎各类形式的贡献，包括但不限于代码提交、文档改进、问题反馈和新功能建议。请遵循以下流程：

1. 在 GitHub 仓库中 Fork 本项目至个人账户，并将 Fork 后的仓库克隆到本地开发环境。确保本地 Node.js 和 SQLite 版本满足安装要求。

2. 创建新的功能分支，分支名称应简明描述所解决的问题或新增的功能，例如 `fix-link-checker-timeout` 或 `add-export-json-format`。请勿在主分支直接开发。

3. 编写代码或文档时，请严格遵守项目代码风格（使用 ESLint 和 Prettier 配置），并为新增功能编写对应的单元测试用例。所有测试用例须通过 `npm test` 命令验证。

4. 提交代码时，请使用语义化提交信息格式，例如 `feat: 添加按域名筛选资源的功能` 或 `fix: 修复元数据抓取时特殊字符编码错误`。提交前需确保无 ESLint 警告。

5. 向主仓库发起 Pull Request，并在描述中详细说明变更内容、影响范围以及测试覆盖情况。PR 将被至少一位项目维护者审查，审查通过后合并至主分支。

## 常见问题

**问：导入大量 URL 后页面加载变慢，如何优化？**

答：当资源数量超过 5000 条时，建议启用分页和虚拟滚动功能。前端已内置懒加载机制，但你可以通过修改 `src/client/pages/ResourceList.jsx` 中的 `PAGE_SIZE` 常量（默认 50）来调整每页显示条数。此外，定期执行 `npm run cleanup-logs` 清理历史日志也有助于减轻磁盘 I/O 压力。如果数据量超过 2 万条，推荐将数据库迁移至 PostgreSQL 以获得更好的查询性能。

**问：链接健康检查任务频繁导致服务器负载过高，如何调整？**

答：健康检查任务默认每 24 小时执行一次，并发请求数为 10。你可以通过修改 `.env` 文件中的 `HEALTH_CHECK_INTERVAL`（单位小时）和 `HEALTH_CHECK_CONCURRENCY` 变量来调整频率和并发数。建议在业务低峰期（如凌晨 2 点至 5 点）执行全量检查，并通过 `src/server/workers/healthCheck.js` 中的白名单机制排除内部网络地址。

**问：如何将现有的书签 HTML 文件或浏览器收藏夹导入系统？**

答：WebLink Navigator 支持通过 `npm run import:bookmarks -- --file=bookmarks.html` 命令导入 Netscape 格式的书签文件。该命令会解析 HTML 中的 `<A>` 标签，提取 href、title 和 add_date 属性，并自动存入数据库。对于其他格式（如 Chrome JSON 导出），请先使用第三方工具转换为 Netscape 格式，或通过 `npm run import:csv -- --file=links.csv` 导入 CSV 文件，CSV 需包含 `url,title,tags` 三列。

## 许可证

MIT License

Copyright (c) 2026 WebLink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
