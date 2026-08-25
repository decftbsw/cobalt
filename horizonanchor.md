# WebLink Navigator

WebLink Navigator 是一个面向技术调研、内容聚合与知识管理场景的轻量级外链资源汇总平台。该项目定位于帮助开发者、技术写作者、数据分析师以及信息运营人员，将散落在各个垂直资讯站点的深层页面进行统一收录、分类索引和快速检索。WebLink Navigator 本身不生产内容，而是通过结构化的资源清单与元数据描述，构建一个可复用、可扩展的外部信息资产目录，解决从“发现有用链接”到“长期跟进链接内容”之间的效率断层问题。

项目采用纯静态前端结合后端元数据索引服务的设计，所有外链资源按批次入库，每批次最多容纳 300 个独立链接。当前版本为第 209/300 批资源整合。WebLink Navigator 提供资源列表导出、链接状态巡检、访问热度标记以及自定义标签分组等辅助功能，适合作为个人或团队内部的知识底座，也可用于构建公开的技术导航站或行业资讯看板。

## 功能概览

**资源批次化管理**：每批资源独立存储，支持批次编号、导入时间、来源描述等元信息记录，便于回溯与维护。

**多维度列表展示**：资源以扁平列表呈现，同时支持按域名、文件类型、路径层级等维度自动归类，降低大量链接的认知负荷。

**快速关键字筛选**：基于标题和 URL 片段的客户端模糊匹配，无需后端即可在已有资源集合中进行初步定位。

**访问状态监测**：定期对已收录链接发起 HEAD 请求，标记可访问性状态（有效、失效、重定向），并记录最近检查时间。

**自定义标签系统**：用户可为每个资源添加多个文本标签，例如“待读”、“深度技术”、“月度报告”，实现个性化分类。

**导入导出兼容**：支持以 JSON 和 CSV 格式导入外部链接清单，也可将当前批次资源导出为标准数据交换格式。

**访问热度排序**：根据手动标记的点击次数或外部引用频次，对资源进行热度排序，辅助识别高价值内容。

**轻量化部署**：无需数据库，所有数据以文件形式存储，适合在低资源环境下运行，包括个人开发机、NAS 设备或静态托管服务。

## 应用场景

技术团队内部知识库维护：团队可将日常调研中发现的优质技术博客、官方文档、API 参考链接统一收录到 WebLink Navigator 中，按项目或技术栈打标，新成员入职时可直接浏览已沉淀的资源清单，快速了解团队关注的技术领域。

技术写作者与自媒体运营：内容创作者在准备技术选题时，需要大量引用外部资料作为论据或参考来源。WebLink Navigator 帮助作者集中管理所有备选引用链接，并随时导出为规范的参考文献列表，减少手动整理和格式调整的时间。

数据分析与行业监测：分析师可将特定行业报告、数据发布页面、竞品动态公告等链接批量入库，配合访问状态监测功能，定期检查链接是否失效或内容是否更新，确保数据来源的持续可用性。

个人学习路径管理：自学者在跟踪多门在线课程或技术教程时，可将课程主页、作业说明、延伸阅读材料等链接统一存放，利用标签区分“进行中”、“已完成”、“待拓展”等状态，形成清晰的学习进度看板。

开源项目外部依赖索引：开源项目维护者可将上游依赖的文档、镜像源地址、社区讨论帖等外部资源集中记录，帮助贡献者快速定位相关上下文，减少因信息分散导致的沟通成本。

## 快速开始

以下步骤帮助您在本地环境中快速启动 WebLink Navigator 服务。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目根目录
cd weblink-navigator

# 安装项目依赖（基于 Node.js 环境）
npm install

# 启动开发服务器，默认监听端口 3000
npm run dev
```

执行完毕后，在浏览器中访问 `http://localhost:3000` 即可进入资源管理界面。首次启动时系统会自动生成示例批次数据用于体验。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 运行时基础环境，用于执行后端服务和构建脚本 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| 现代浏览器 | Chrome 110+ / Firefox 110+ / Edge 110+ | 前端界面运行环境，需要支持 ES2022 语法 |
| 磁盘空间 | 至少 500 MB | 用于存储资源索引文件和日志数据 |
| 操作系统 | Linux / macOS / Windows (WSL2 推荐) | 跨平台支持，生产环境建议使用 Linux 发行版 |
| 网络连接 | 出站 HTTP/HTTPS 访问 | 用于链接状态监测和资源内容抓取（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user-guide.md | 如何添加资源、打标签、导出列表、查看访问状态 |
| 管理员指南 | /docs/admin-guide.md | 如何创建新批次、配置监测频率、备份数据文件 |
| 开发贡献 | /docs/contributing.md | 如何提交代码、新增功能模块、编写单元测试 |
| API 参考 | /docs/api-reference.md | 后端接口定义、请求参数、返回数据结构说明 |
| 部署运维 | /docs/deployment.md | 生产环境部署选项（Nginx 反向代理、Docker 容器化） |
| 常见问题 | /docs/faq.md | 涵盖安装报错、链接监测失败、数据迁移等典型问题 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/4907.htm
- http://m.3g.bwbkj.cn/jnews/366519.htm
- http://m.3g.bwbkj.cn/jnews/566177.htm
- http://m.3g.bwbkj.cn/jnews/5772925.htm
- http://m.3g.bwbkj.cn/jnews/19448.htm
- http://m.3g.bwbkj.cn/jnews/1433.htm
- http://m.3g.bwbkj.cn/jnews/129498.htm
- http://m.3g.bwbkj.cn/jnews/681118.htm
- http://m.3g.bwbkj.cn/jnews/478834.htm
- http://m.3g.bwbkj.cn/jnews/544543.htm
- http://m.3g.bwbkj.cn/jnews/3798514.htm
- http://m.3g.bwbkj.cn/jnews/12107.htm
- http://m.3g.bwbkj.cn/jnews/6325083.htm
- http://m.3g.bwbkj.cn/jnews/4370813.htm
- http://m.3g.bwbkj.cn/jnews/9928456.htm
- http://m.3g.bwbkj.cn/jnews/745392.htm
- http://m.3g.bwbkj.cn/jnews/6527333.htm
- http://m.3g.bwbkj.cn/jnews/331152.htm
- http://m.3g.bwbkj.cn/jnews/8596.htm
- http://m.3g.bwbkj.cn/jnews/66552.htm
- http://m.3g.bwbkj.cn/jnews/8349.htm
- http://m.3g.bwbkj.cn/jnews/5624994.htm
- http://m.3g.bwbkj.cn/jnews/7652637.htm
- http://m.3g.bwbkj.cn/jnews/080687.htm
- http://m.3g.bwbkj.cn/jnews/373680.htm
- http://m.3g.bwbkj.cn/jnews/11964.htm
- http://m.3g.bwbkj.cn/jnews/2229878.htm
- http://m.3g.bwbkj.cn/jnews/04046.htm
- http://m.3g.bwbkj.cn/jnews/56262.htm
- http://m.3g.bwbkj.cn/jnews/07526.htm
- http://m.3g.bwbkj.cn/jnews/7311.htm
- http://m.3g.bwbkj.cn/jnews/2125302.htm
- http://m.3g.bwbkj.cn/jnews/6127857.htm
- http://m.3g.bwbkj.cn/jnews/7893.htm
- http://m.3g.bwbkj.cn/jnews/5997.htm
- http://m.3g.bwbkj.cn/jnews/657039.htm
- http://m.3g.bwbkj.cn/jnews/2725.htm
- http://m.3g.bwbkj.cn/jnews/472893.htm
- http://m.3g.bwbkj.cn/jnews/9085.htm
- http://m.3g.bwbkj.cn/jnews/7901952.htm
- http://m.3g.bwbkj.cn/jnews/743459.htm
- http://m.3g.bwbkj.cn/jnews/9640283.htm
- http://m.3g.bwbkj.cn/jnews/7100848.htm
- http://m.3g.bwbkj.cn/jnews/69779.htm
- http://m.3g.bwbkj.cn/jnews/087120.htm
- http://m.3g.bwbkj.cn/jnews/401484.htm
- http://m.3g.bwbkj.cn/jnews/0992602.htm
- http://m.3g.bwbkj.cn/jnews/60499.htm
- http://m.3g.bwbkj.cn/jnews/681106.htm
- http://m.3g.bwbkj.cn/jnews/23668.htm
- http://m.3g.bwbkj.cn/jnews/77239.htm
- http://m.3g.bwbkj.cn/jnews/7572195.htm
- http://m.3g.bwbkj.cn/jnews/3794574.htm
- http://m.3g.bwbkj.cn/jnews/1704879.htm
- http://m.3g.bwbkj.cn/jnews/475355.htm
- http://m.3g.bwbkj.cn/jnews/905242.htm
- http://m.3g.bwbkj.cn/jnews/4148601.htm
- http://m.3g.bwbkj.cn/jnews/6272930.htm
- http://m.3g.bwbkj.cn/jnews/5075135.htm
- http://m.3g.bwbkj.cn/jnews/78710.htm
- http://m.3g.bwbkj.cn/jnews/0233.htm
- http://m.3g.bwbkj.cn/jnews/51836.htm
- http://m.3g.bwbkj.cn/jnews/69231.htm
- http://m.3g.bwbkj.cn/jnews/1695.htm
- http://m.3g.bwbkj.cn/jnews/683476.htm
- http://m.3g.bwbkj.cn/jnews/31781.htm
- http://m.3g.bwbkj.cn/jnews/6235857.htm
- http://m.3g.bwbkj.cn/jnews/34577.htm
- http://m.3g.bwbkj.cn/jnews/31637.htm
- http://m.3g.bwbkj.cn/jnews/0508210.htm
- http://m.3g.bwbkj.cn/jnews/35861.htm
- http://m.3g.bwbkj.cn/jnews/0395264.htm
- http://m.3g.bwbkj.cn/jnews/1795.htm
- http://m.3g.bwbkj.cn/jnews/5027876.htm
- http://m.3g.bwbkj.cn/jnews/8565.htm
- http://m.3g.bwbkj.cn/jnews/2703.htm
- http://m.3g.bwbkj.cn/jnews/8370.htm
- http://m.3g.bwbkj.cn/jnews/4181888.htm
- http://m.3g.bwbkj.cn/jnews/98426.htm
- http://m.3g.bwbkj.cn/jnews/8882089.htm
- http://m.3g.bwbkj.cn/jnews/5987.htm
- http://m.3g.bwbkj.cn/jnews/1283583.htm
- http://m.3g.bwbkj.cn/jnews/83247.htm
- http://m.3g.bwbkj.cn/jnews/2637630.htm
- http://m.3g.bwbkj.cn/jnews/823023.htm
- http://m.3g.bwbkj.cn/jnews/858167.htm
- http://m.3g.bwbkj.cn/jnews/6100884.htm
- http://m.3g.bwbkj.cn/jnews/2387525.htm
- http://m.3g.bwbkj.cn/jnews/5747.htm
- http://m.3g.bwbkj.cn/jnews/6893.htm
- http://m.3g.bwbkj.cn/jnews/9848.htm
- http://m.3g.bwbkj.cn/jnews/88846.htm
- http://m.3g.bwbkj.cn/jnews/26950.htm
- http://m.3g.bwbkj.cn/jnews/715891.htm
- http://m.3g.bwbkj.cn/jnews/73852.htm
- http://m.3g.bwbkj.cn/jnews/9351.htm
- http://m.3g.bwbkj.cn/jnews/5899662.htm
- http://m.3g.bwbkj.cn/jnews/6058709.htm
- http://m.3g.bwbkj.cn/jnews/16785.htm
- http://m.3g.bwbkj.cn/jnews/96199.htm
- http://m.3g.bwbkj.cn/jnews/9036674.htm
- http://m.3g.bwbkj.cn/jnews/610897.htm
- http://m.3g.bwbkj.cn/jnews/97060.htm
- http://m.3g.bwbkj.cn/jnews/30930.htm
- http://m.3g.bwbkj.cn/jnews/54912.htm
- http://m.3g.bwbkj.cn/jnews/0315432.htm
- http://m.3g.bwbkj.cn/jnews/8932.htm
- http://m.3g.bwbkj.cn/jnews/2566046.htm
- http://m.3g.bwbkj.cn/jnews/8029.htm
- http://m.3g.bwbkj.cn/jnews/6212250.htm
- http://m.3g.bwbkj.cn/jnews/8364.htm
- http://m.3g.bwbkj.cn/jnews/041733.htm
- http://m.3g.bwbkj.cn/jnews/322175.htm
- http://m.3g.bwbkj.cn/jnews/4255.htm
- http://m.3g.bwbkj.cn/jnews/92139.htm
- http://m.3g.bwbkj.cn/jnews/9662336.htm
- http://m.3g.bwbkj.cn/jnews/118958.htm
- http://m.3g.bwbkj.cn/jnews/7338.htm
- http://m.3g.bwbkj.cn/jnews/20772.htm
- http://m.3g.bwbkj.cn/jnews/626174.htm
- http://m.3g.bwbkj.cn/jnews/19714.htm
- http://m.3g.bwbkj.cn/jnews/66337.htm
- http://m.3g.bwbkj.cn/jnews/228891.htm
- http://m.3g.bwbkj.cn/jnews/30002.htm
- http://m.3g.bwbkj.cn/jnews/316850.htm
- http://m.3g.bwbkj.cn/jnews/207384.htm
- http://m.3g.bwbkj.cn/jnews/1804352.htm
- http://m.3g.bwbkj.cn/jnews/45935.htm
- http://m.3g.bwbkj.cn/jnews/4500.htm
- http://m.3g.bwbkj.cn/jnews/278376.htm
- http://m.3g.bwbkj.cn/jnews/3185.htm
- http://m.3g.bwbkj.cn/jnews/499602.htm
- http://m.3g.bwbkj.cn/jnews/0543993.htm
- http://m.3g.bwbkj.cn/jnews/73459.htm
- http://m.3g.bwbkj.cn/jnews/83527.htm
- http://m.3g.bwbkj.cn/jnews/58624.htm
- http://m.3g.bwbkj.cn/jnews/6772.htm
- http://m.3g.bwbkj.cn/jnews/4807104.htm
- http://m.3g.bwbkj.cn/jnews/87520.htm
- http://m.3g.bwbkj.cn/jnews/1997794.htm
- http://m.3g.bwbkj.cn/jnews/5347487.htm
- http://m.3g.bwbkj.cn/jnews/13685.htm
- http://m.3g.bwbkj.cn/jnews/1842680.htm
- http://m.3g.bwbkj.cn/jnews/8951.htm
- http://m.3g.bwbkj.cn/jnews/6852.htm
- http://m.3g.bwbkj.cn/jnews/503463.htm
- http://m.3g.bwbkj.cn/jnews/5395.htm
- http://m.3g.bwbkj.cn/jnews/28425.htm
- http://m.3g.bwbkj.cn/jnews/9918671.htm
- http://m.3g.bwbkj.cn/jnews/0156.htm
- http://m.3g.bwbkj.cn/jnews/95515.htm
- http://m.3g.bwbkj.cn/jnews/1876712.htm
- http://m.3g.bwbkj.cn/jnews/84319.htm
- http://m.3g.bwbkj.cn/jnews/7166707.htm
- http://m.3g.bwbkj.cn/jnews/4533.htm
- http://m.3g.bwbkj.cn/jnews/9781726.htm
- http://m.3g.bwbkj.cn/jnews/13129.htm
- http://m.3g.bwbkj.cn/jnews/4127130.htm
- http://m.3g.bwbkj.cn/jnews/7305.htm
- http://m.3g.bwbkj.cn/jnews/8267912.htm
- http://m.3g.bwbkj.cn/jnews/6354046.htm
- http://m.3g.bwbkj.cn/jnews/1407305.htm
- http://m.3g.bwbkj.cn/jnews/9357.htm
- http://m.3g.bwbkj.cn/jnews/523155.htm
- http://m.3g.bwbkj.cn/jnews/2170.htm
- http://m.3g.bwbkj.cn/jnews/7246.htm
- http://m.3g.bwbkj.cn/jnews/79603.htm
- http://m.3g.bwbkj.cn/jnews/1378.htm
- http://m.3g.bwbkj.cn/jnews/0997.htm
- http://m.3g.bwbkj.cn/jnews/7345.htm
- http://m.3g.bwbkj.cn/jnews/73143.htm
- http://m.3g.bwbkj.cn/jnews/521092.htm
- http://m.3g.bwbkj.cn/jnews/534366.htm
- http://m.3g.bwbkj.cn/jnews/8346.htm
- http://m.3g.bwbkj.cn/jnews/402543.htm
- http://m.3g.bwbkj.cn/jnews/80016.htm
- http://m.3g.bwbkj.cn/jnews/5855.htm
- http://m.3g.bwbkj.cn/jnews/4604077.htm
- http://m.3g.bwbkj.cn/jnews/0407.htm
- http://m.3g.bwbkj.cn/jnews/9933944.htm
- http://m.3g.bwbkj.cn/jnews/7261.htm
- http://m.3g.bwbkj.cn/jnews/18141.htm
- http://m.3g.bwbkj.cn/jnews/4779.htm
- http://m.3g.bwbkj.cn/jnews/211833.htm
- http://m.3g.bwbkj.cn/jnews/4165.htm
- http://m.3g.bwbkj.cn/jnews/58058.htm
- http://m.3g.bwbkj.cn/jnews/31906.htm
- http://m.3g.bwbkj.cn/jnews/197115.htm
- http://m.3g.bwbkj.cn/jnews/5715380.htm
- http://m.3g.bwbkj.cn/jnews/36143.htm
- http://m.3g.bwbkj.cn/jnews/1691.htm
- http://m.3g.bwbkj.cn/jnews/984228.htm
- http://m.3g.bwbkj.cn/jnews/5016614.htm
- http://m.3g.bwbkj.cn/jnews/42660.htm
- http://m.3g.bwbkj.cn/jnews/8164.htm
- http://m.3g.bwbkj.cn/jnews/1193044.htm
- http://m.3g.bwbkj.cn/jnews/77987.htm
- http://m.3g.bwbkj.cn/jnews/4110.htm
- http://m.3g.bwbkj.cn/jnews/7353.htm
- http://m.3g.bwbkj.cn/jnews/079948.htm
- http://m.3g.bwbkj.cn/jnews/2203.htm
- http://m.3g.bwbkj.cn/jnews/893065.htm
- http://m.3g.bwbkj.cn/jnews/03330.htm
- http://m.3g.bwbkj.cn/jnews/9639746.htm
- http://m.3g.bwbkj.cn/jnews/8154640.htm
- http://m.3g.bwbkj.cn/jnews/5813.htm
- http://m.3g.bwbkj.cn/jnews/32344.htm
- http://m.3g.bwbkj.cn/jnews/40825.htm
- http://m.3g.bwbkj.cn/jnews/271060.htm
- http://m.3g.bwbkj.cn/jnews/216976.htm
- http://m.3g.bwbkj.cn/jnews/1926182.htm
- http://m.3g.bwbkj.cn/jnews/40623.htm
- http://m.3g.bwbkj.cn/jnews/1614771.htm
- http://m.3g.bwbkj.cn/jnews/5798001.htm
- http://m.3g.bwbkj.cn/jnews/4701.htm
- http://m.3g.bwbkj.cn/jnews/0940.htm
- http://m.3g.bwbkj.cn/jnews/1396.htm
- http://m.3g.bwbkj.cn/jnews/787475.htm
- http://m.3g.bwbkj.cn/jnews/80156.htm
- http://m.3g.bwbkj.cn/jnews/8466829.htm
- http://m.3g.bwbkj.cn/jnews/641258.htm
- http://m.3g.bwbkj.cn/jnews/2461.htm
- http://m.3g.bwbkj.cn/jnews/2100904.htm
- http://m.3g.bwbkj.cn/jnews/740792.htm
- http://m.3g.bwbkj.cn/jnews/6608.htm
- http://m.3g.bwbkj.cn/jnews/919714.htm
- http://m.3g.bwbkj.cn/jnews/312091.htm
- http://m.3g.bwbkj.cn/jnews/34665.htm
- http://m.3g.bwbkj.cn/jnews/626448.htm
- http://m.3g.bwbkj.cn/jnews/3349914.htm
- http://m.3g.bwbkj.cn/jnews/462014.htm
- http://m.3g.bwbkj.cn/jnews/6481722.htm
- http://m.3g.bwbkj.cn/jnews/02136.htm
- http://m.3g.bwbkj.cn/jnews/40100.htm
- http://m.3g.bwbkj.cn/jnews/1696566.htm
- http://m.3g.bwbkj.cn/jnews/6580.htm
- http://m.3g.bwbkj.cn/jnews/8406462.htm
- http://m.3g.bwbkj.cn/jnews/73230.htm
- http://m.3g.bwbkj.cn/jnews/639196.htm
- http://m.3g.bwbkj.cn/jnews/9991944.htm
- http://m.3g.bwbkj.cn/jnews/283625.htm
- http://m.3g.bwbkj.cn/jnews/470868.htm
- http://m.3g.bwbkj.cn/jnews/8319513.htm
- http://m.3g.bwbkj.cn/jnews/358643.htm
- http://m.3g.bwbkj.cn/jnews/500085.htm
- http://m.3g.bwbkj.cn/jnews/8198.htm
- http://m.3g.bwbkj.cn/jnews/369567.htm
- http://m.3g.bwbkj.cn/jnews/18529.htm
- http://m.3g.bwbkj.cn/jnews/7611.htm
- http://m.3g.bwbkj.cn/jnews/581550.htm
- http://m.3g.bwbkj.cn/jnews/47643.htm
- http://m.3g.bwbkj.cn/jnews/046393.htm
- http://m.3g.bwbkj.cn/jnews/02161.htm
- http://m.3g.bwbkj.cn/jnews/56449.htm
- http://m.3g.bwbkj.cn/jnews/1675735.htm
- http://m.3g.bwbkj.cn/jnews/0127.htm
- http://m.3g.bwbkj.cn/jnews/6261.htm
- http://m.3g.bwbkj.cn/jnews/6114563.htm
- http://m.3g.bwbkj.cn/jnews/45743.htm
- http://m.3g.bwbkj.cn/jnews/33715.htm
- http://m.3g.bwbkj.cn/jnews/6807.htm
- http://m.3g.bwbkj.cn/jnews/797495.htm
- http://m.3g.bwbkj.cn/jnews/9828612.htm
- http://m.3g.bwbkj.cn/jnews/4055709.htm
- http://m.3g.bwbkj.cn/jnews/4831113.htm
- http://m.3g.bwbkj.cn/jnews/26228.htm
- http://m.3g.bwbkj.cn/jnews/8554.htm
- http://m.3g.bwbkj.cn/jnews/0925.htm
- http://m.3g.bwbkj.cn/jnews/964833.htm
- http://m.3g.bwbkj.cn/jnews/0962.htm
- http://m.3g.bwbkj.cn/jnews/7461.htm
- http://m.3g.bwbkj.cn/jnews/1720.htm
- http://m.3g.bwbkj.cn/jnews/433128.htm
- http://m.3g.bwbkj.cn/jnews/437681.htm
- http://m.3g.bwbkj.cn/jnews/1337740.htm
- http://m.3g.bwbkj.cn/jnews/7164722.htm
- http://m.3g.bwbkj.cn/jnews/12651.htm
- http://m.3g.bwbkj.cn/jnews/44287.htm
- http://m.3g.bwbkj.cn/jnews/95705.htm
- http://m.3g.bwbkj.cn/jnews/7839175.htm
- http://m.3g.bwbkj.cn/jnews/45407.htm
- http://m.3g.bwbkj.cn/jnews/32353.htm
- http://m.3g.bwbkj.cn/jnews/60709.htm
- http://m.3g.bwbkj.cn/jnews/7916.htm
- http://m.3g.bwbkj.cn/jnews/0281341.htm
- http://m.3g.bwbkj.cn/jnews/905109.htm
- http://m.3g.bwbkj.cn/jnews/1654.htm
- http://m.3g.bwbkj.cn/jnews/9353298.htm
- http://m.3g.bwbkj.cn/jnews/291150.htm
- http://m.3g.bwbkj.cn/jnews/3916.htm
- http://m.3g.bwbkj.cn/jnews/1568.htm
- http://m.3g.bwbkj.cn/jnews/169256.htm
- http://m.3g.bwbkj.cn/jnews/823415.htm
- http://m.3g.bwbkj.cn/jnews/59485.htm
- http://m.3g.bwbkj.cn/jnews/50129.htm
- http://m.3g.bwbkj.cn/jnews/6577291.htm
- http://m.3g.bwbkj.cn/jnews/8535900.htm
- http://m.3g.bwbkj.cn/jnews/495215.htm
- http://m.3g.bwbkj.cn/jnews/74826.htm
- http://m.3g.bwbkj.cn/jnews/47481.htm

## 项目结构

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── core/                           # 核心功能模块
│   │   ├── indexer.js                  # 资源索引构建与更新逻辑
│   │   ├── validator.js                # 链接格式校验与规范化处理
│   │   └── monitor.js                  # 链接访问状态监测调度器
│   ├── server/                         # HTTP 服务端实现
│   │   ├── app.js                      # Express 应用入口与中间件配置
│   │   ├── routes/                     # 路由定义目录
│   │   │   ├── api.js                  # RESTful API 路由集合
│   │   │   └── web.js                  # 前端页面路由
│   │   └── services/                   # 业务逻辑服务层
│   │       ├── batchService.js         # 批次数据读写操作
│   │       └── tagService.js           # 标签增删改查服务
│   ├── ui/                             # 前端用户界面源码
│   │   ├── components/                 # Vue.js 组件目录
│   │   │   ├── ResourceList.vue        # 资源列表主表格组件
│   │   │   ├── FilterPanel.vue         # 关键字与标签筛选面板
│   │   │   └── StatusBadge.vue         # 访问状态指示器组件
│   │   ├── layouts/                    # 页面布局模板
│   │   │   └── DefaultLayout.vue       # 默认导航与内容区布局
│   │   └── store/                      # Pinia 状态管理
│   │       └── resourceStore.js        # 资源数据与筛选状态存储
│   └── utils/                          # 通用工具函数库
│       ├── logger.js                   # 日志输出封装（基于 winston）
│       └── fetcher.js                  # HTTP 请求封装（基于 axios）
├── data/                               # 数据存储目录（自动生成）
│   ├── batches/                        # 批次数据文件，按编号存储
│   │   └── 209.json                    # 当前第 209 批资源数据
│   └── cache/                          # 链接监测缓存
│       └── status_cache.db             # SQLite 轻量缓存数据库
├── config/                             # 配置文件目录
│   ├── default.yaml                    # 默认环境配置
│   └── production.yaml                 # 生产环境覆盖配置
├── docs/                               # 完整文档目录
│   ├── user-guide.md                   # 用户操作手册
│   ├── admin-guide.md                  # 管理员维护指南
│   ├── contributing.md                 # 贡献者指引
│   ├── api-reference.md                # API 详细参考文档
│   ├── deployment.md                   # 部署与运维说明
│   └── faq.md                          # 常见问题汇总
├── scripts/                            # 辅助运维脚本
│   ├── import-csv.js                   # CSV 格式批量导入脚本
│   └── export-json.js                  # JSON 格式批量导出脚本
├── tests/                              # 单元与集成测试目录
│   ├── unit/                           # 单元测试用例
│   │   └── validator.test.js           # 链接校验模块测试
│   └── integration/                    # 集成测试用例
│       └── api.test.js                 # API 接口集成测试
├── .env.example                        # 环境变量模板文件
├── package.json                        # npm 依赖与脚本定义
├── README.md                           # 项目介绍文档（本文件）
└── LICENSE                             # MIT 许可证文件
```

## 贡献指南

首先在 GitHub 上 Fork 本仓库至个人账号，然后克隆到本地开发环境。建议在 dev 分支上进行所有修改，避免直接操作 main 分支。

安装依赖并启动开发服务器后，针对新增功能或缺陷修复编写对应的单元测试用例，确保测试覆盖率达到现有水平。所有测试用例需通过 `npm test` 命令验证。

提交代码前运行 `npm run lint` 检查代码风格是否符合项目 ESLint 配置，并执行 `npm run format` 自动格式化源文件。提交信息请遵循 Conventional Commits 规范，使用 `feat:`、`fix:`、`docs:`、`refactor:` 等前缀。

对于新增功能或 API 变更，必须同步更新对应的文档文件，包括用户手册、API 参考或管理员指南。文档变更应与代码变更在同一 Pull Request 中提交。

提交 Pull Request 时请在描述中清晰说明变更目的、影响范围以及测试验证情况，至少需要一名项目维护者审核通过后方可合并。

## 常见问题

**Q：启动服务时提示端口 3000 已被占用，如何解决？**

A：可以通过修改配置文件 `config/default.yaml` 中的 `server.port` 字段，或设置环境变量 `PORT=3001` 来指定其他可用端口。修改后重启服务即可生效。

**Q：导入的资源链接数量超过单批上限怎么办？**

A：当前每批资源固定为 300 条，这是为了保持索引性能和批次管理的清晰性。如果链接总数超过 300，系统会自动提示创建新的批次。您可以通过管理界面手动新建批次，或使用脚本 `scripts/import-csv.js` 配合 `--batch` 参数指定目标批次编号。

**Q：链接访问状态监测显示失效，但实际在浏览器中可访问，是什么原因？**

A：监测模块默认使用 HEAD 请求检测链接可访问性，部分站点可能屏蔽 HEAD 请求或返回 405 状态码。此时监测结果可能为假阴性。您可以在配置文件中将监测方法改为 GET，或调整 `monitor.timeout` 参数增加超时时间。建议对少量误报链接手动更新状态。

**Q：如何将当前批次数据迁移到另一台服务器？**

A：直接复制 `data/batches/` 目录下的 JSON 文件到新服务器的对应路径即可。如果使用了状态缓存数据库 `data/cache/status_cache.db`，也可一并迁移，避免重新监测所有链接。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:02
