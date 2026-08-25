# WebLink Navigator

WebLink Navigator 是一个面向技术调研、内容聚合与信息归档场景的轻量级外链资源汇总平台。该项目专为开发者、技术研究员、内容编辑以及运维人员设计，用于系统化地收集、分类、展示和检索来自互联网的离散型信息页面。其核心定位并非搜索引擎，而是一个结构化的外部链接索引系统，帮助用户从海量散乱 URL 中建立可维护的知识导航体系。

该项目通过静态页面生成技术，将大量原始 URL 转化为具有分类标签、时间戳标注和状态监控的可视化目录。用户可以通过该项目快速定位特定来源的资讯，避免重复劳动，同时降低人工维护书签或文档链接的心智负担。WebLink Navigator 适用于需要长期跟踪特定域名下内容更新的工作流，例如行业新闻监控、漏洞公告追踪或版本发布记录归档。

## 功能概览

**批量链接导入与解析**：支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动解析域名、路径参数和文件扩展名，提取核心标识符用于索引。

**智能分类与标签生成**：基于 URL 路径模式、查询参数或域名特征，自动为每条外链分配分类标签，并支持用户自定义标签体系，便于按主题或来源分组浏览。

**实时可用性检测**：内置异步 HTTP 检测模块，定期对已收录的 URL 执行 HEAD 请求，标记异常链接（如 404、超时或重定向），并在界面中高亮显示状态变更。

**多维度检索与筛选**：提供基于关键词、域名、状态码、收录时间范围等多条件组合筛选功能，支持正则表达式高级搜索，满足技术调研中的精确匹配需求。

**数据导出与快照归档**：允许将当前链接列表导出为 JSON、CSV 或 Markdown 表格格式，支持生成带时间戳的归档快照，便于版本对比和离线备份。

**访问统计与热度排序**：记录每条外链的被访问次数（需配合后端或前端埋点），按点击频率、添加时间或字母序进行动态排序，辅助用户识别高价值资源。

**响应式管理面板**：提供移动端适配的 Web 管理界面，支持在手机或平板上完成链接增删改查操作，适合运维人员在非桌面环境下快速处理异常链接。

## 应用场景

**技术文档维护团队**：当技术文档中包含大量外部参考链接时，使用 WebLink Navigator 统一管理这些引用，定期检查链接有效性，避免文档中出现失效链接影响用户体验。团队可以每周运行一次可用性检测，自动生成失效链接报告。

**行业资讯聚合站点运营者**：运营者需要从特定新闻源持续采集文章链接，但不想搭建完整的爬虫系统。通过本项目的批量导入和分类功能，手动或半自动地将新发现的 URL 录入系统，并利用标签功能区分“行业动态”、“政策法规”、“技术前沿”等类别，快速生成每日资讯汇总页面。

**安全研究员漏洞情报跟踪**：安全研究员需要跟踪多个漏洞披露平台（如 CVE、CNVD 以及各类安全博客）的新增条目。将相关 URL 模板或具体链接纳入 WebLink Navigator 后，利用其状态检测功能自动监控页面是否存在（即漏洞详情是否已公开），从而第一时间获取情报。

**开源项目外部依赖记录**：开源项目维护者可以使用本工具记录项目所依赖的第三方库文档地址、镜像源地址、以及相关工具链的官方网站，形成一份结构化的外部资源清单，在项目迁移或镜像源变更时快速批量替换。

## 快速开始

以下步骤帮助您在本地环境中快速启动 WebLink Navigator 实例。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装项目依赖（使用 npm）
npm install

# 配置环境变量（复制示例配置文件）
cp .env.example .env

# 初始化数据库并导入示例链接数据
npm run init-db
npm run import-sample

# 启动开发服务器
npm run dev
```

访问控制台输出中显示的本地地址（默认 http://localhost:3000）即可开始使用。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.x 或更高（LTS 版本推荐） | 项目运行时环境，提供 JavaScript 执行引擎与 npm 包管理器 |
| npm 或 yarn | npm 8.x / yarn 1.22.x | 用于安装项目依赖包，锁定具体版本以确保兼容性 |
| SQLite3 | 3.35 或更高（嵌入式） | 项目默认使用 SQLite 作为数据存储引擎，无需额外安装数据库服务 |
| Git | 2.25 或更高 | 用于克隆仓库以及后续拉取更新，要求支持浅克隆 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 用于访问管理面板，需支持 ES2020 语法与 CSS Grid 布局 |
| 网络环境 | 可访问公网（用于检测外链状态） | 可用性检测功能需要能够向目标 URL 发起 HTTP 请求，内网环境需自行配置代理或 DNS |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何从零开始部署 WebLink Navigator，包括首次启动、管理员账号创建和基础配置 |
| 链接管理 | docs/link-management.md | 如何批量添加链接、编辑元数据、删除冗余条目以及导入导出数据 |
| 检测与监控 | docs/health-check.md | 状态检测的工作原理、检测频率设置、异常通知配置以及日志解读 |
| API 参考 | docs/api-reference.md | 后端提供的 RESTful API 端点说明，包括请求参数、响应格式和鉴权方式 |
| 部署运维 | docs/deployment.md | 生产环境下的部署方案（Nginx 反向代理、PM2 进程守护、Docker 镜像构建） |
| 自定义开发 | docs/customization.md | 如何修改前端主题、添加自定义分类策略以及扩展检测器插件 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/17637.htm
- http://m.wap.bwbkj.cn/snews/6656.htm
- http://m.wap.bwbkj.cn/snews/22644.htm
- http://m.wap.bwbkj.cn/snews/649710.htm
- http://m.wap.bwbkj.cn/snews/770304.htm
- http://m.wap.bwbkj.cn/snews/1967.htm
- http://m.wap.bwbkj.cn/snews/407930.htm
- http://m.wap.bwbkj.cn/snews/588272.htm
- http://m.wap.bwbkj.cn/snews/1202.htm
- http://m.wap.bwbkj.cn/snews/6732146.htm
- http://m.wap.bwbkj.cn/snews/853091.htm
- http://m.wap.bwbkj.cn/snews/662288.htm
- http://m.wap.bwbkj.cn/snews/151893.htm
- http://m.wap.bwbkj.cn/snews/4451673.htm
- http://m.wap.bwbkj.cn/snews/6803.htm
- http://m.wap.bwbkj.cn/snews/4640909.htm
- http://m.wap.bwbkj.cn/snews/8221.htm
- http://m.wap.bwbkj.cn/snews/8539.htm
- http://m.wap.bwbkj.cn/snews/51070.htm
- http://m.wap.bwbkj.cn/snews/4746.htm
- http://m.wap.bwbkj.cn/snews/5889569.htm
- http://m.wap.bwbkj.cn/snews/4681181.htm
- http://m.wap.bwbkj.cn/snews/57457.htm
- http://m.wap.bwbkj.cn/snews/41287.htm
- http://m.wap.bwbkj.cn/snews/690783.htm
- http://m.wap.bwbkj.cn/snews/83524.htm
- http://m.wap.bwbkj.cn/snews/52213.htm
- http://m.wap.bwbkj.cn/snews/521092.htm
- http://m.wap.bwbkj.cn/snews/7208.htm
- http://m.wap.bwbkj.cn/snews/5506.htm
- http://m.wap.bwbkj.cn/snews/408591.htm
- http://m.wap.bwbkj.cn/snews/876998.htm
- http://m.wap.bwbkj.cn/snews/5238040.htm
- http://m.wap.bwbkj.cn/snews/1045.htm
- http://m.wap.bwbkj.cn/snews/104931.htm
- http://m.wap.bwbkj.cn/snews/124176.htm
- http://m.wap.bwbkj.cn/snews/42241.htm
- http://m.wap.bwbkj.cn/snews/2404574.htm
- http://m.wap.bwbkj.cn/snews/43838.htm
- http://m.wap.bwbkj.cn/snews/2066264.htm
- http://m.wap.bwbkj.cn/snews/088500.htm
- http://m.wap.bwbkj.cn/snews/2462143.htm
- http://m.wap.bwbkj.cn/snews/62017.htm
- http://m.wap.bwbkj.cn/snews/0040730.htm
- http://m.wap.bwbkj.cn/snews/101815.htm
- http://m.wap.bwbkj.cn/snews/0565100.htm
- http://m.wap.bwbkj.cn/snews/10044.htm
- http://m.wap.bwbkj.cn/snews/8454.htm
- http://m.wap.bwbkj.cn/snews/7594797.htm
- http://m.wap.bwbkj.cn/snews/24663.htm
- http://m.wap.bwbkj.cn/snews/2497.htm
- http://m.wap.bwbkj.cn/snews/90559.htm
- http://m.wap.bwbkj.cn/snews/9220.htm
- http://m.wap.bwbkj.cn/snews/3851.htm
- http://m.wap.bwbkj.cn/snews/1278309.htm
- http://m.wap.bwbkj.cn/snews/23502.htm
- http://m.wap.bwbkj.cn/snews/49915.htm
- http://m.wap.bwbkj.cn/snews/76781.htm
- http://m.wap.bwbkj.cn/snews/260362.htm
- http://m.wap.bwbkj.cn/snews/65339.htm
- http://m.wap.bwbkj.cn/snews/59286.htm
- http://m.wap.bwbkj.cn/snews/1125860.htm
- http://m.wap.bwbkj.cn/snews/7799.htm
- http://m.wap.bwbkj.cn/snews/826600.htm
- http://m.wap.bwbkj.cn/snews/909522.htm
- http://m.wap.bwbkj.cn/snews/06424.htm
- http://m.wap.bwbkj.cn/snews/17823.htm
- http://m.wap.bwbkj.cn/snews/897502.htm
- http://m.wap.bwbkj.cn/snews/6237632.htm
- http://m.wap.bwbkj.cn/snews/322238.htm
- http://m.wap.bwbkj.cn/snews/03909.htm
- http://m.wap.bwbkj.cn/snews/8875.htm
- http://m.wap.bwbkj.cn/snews/53498.htm
- http://m.wap.bwbkj.cn/snews/259878.htm
- http://m.wap.bwbkj.cn/snews/1868.htm
- http://m.wap.bwbkj.cn/snews/5887.htm
- http://m.wap.bwbkj.cn/snews/27153.htm
- http://m.wap.bwbkj.cn/snews/149713.htm
- http://m.wap.bwbkj.cn/snews/017256.htm
- http://m.wap.bwbkj.cn/snews/81340.htm
- http://m.wap.bwbkj.cn/snews/1685998.htm
- http://m.wap.bwbkj.cn/snews/3776.htm
- http://m.wap.bwbkj.cn/snews/485769.htm
- http://m.wap.bwbkj.cn/snews/21210.htm
- http://m.wap.bwbkj.cn/snews/2711912.htm
- http://m.wap.bwbkj.cn/snews/0314.htm
- http://m.wap.bwbkj.cn/snews/2124.htm
- http://m.wap.bwbkj.cn/snews/751103.htm
- http://m.wap.bwbkj.cn/snews/99560.htm
- http://m.wap.bwbkj.cn/snews/67216.htm
- http://m.wap.bwbkj.cn/snews/541786.htm
- http://m.wap.bwbkj.cn/snews/3693.htm
- http://m.wap.bwbkj.cn/snews/39673.htm
- http://m.wap.bwbkj.cn/snews/531733.htm
- http://m.wap.bwbkj.cn/snews/8870452.htm
- http://m.wap.bwbkj.cn/snews/5753.htm
- http://m.wap.bwbkj.cn/snews/72536.htm
- http://m.wap.bwbkj.cn/snews/96053.htm
- http://m.wap.bwbkj.cn/snews/577701.htm
- http://m.wap.bwbkj.cn/snews/26616.htm
- http://m.wap.bwbkj.cn/snews/3153929.htm
- http://m.wap.bwbkj.cn/snews/26639.htm
- http://m.wap.bwbkj.cn/snews/31315.htm
- http://m.wap.bwbkj.cn/snews/2579606.htm
- http://m.wap.bwbkj.cn/snews/84059.htm
- http://m.wap.bwbkj.cn/snews/9311.htm
- http://m.wap.bwbkj.cn/snews/860138.htm
- http://m.wap.bwbkj.cn/snews/693965.htm
- http://m.wap.bwbkj.cn/snews/035730.htm
- http://m.wap.bwbkj.cn/snews/21619.htm
- http://m.wap.bwbkj.cn/snews/0601305.htm
- http://m.wap.bwbkj.cn/snews/3903932.htm
- http://m.wap.bwbkj.cn/snews/2226229.htm
- http://m.wap.bwbkj.cn/snews/102845.htm
- http://m.wap.bwbkj.cn/snews/7641.htm
- http://m.wap.bwbkj.cn/snews/616353.htm
- http://m.wap.bwbkj.cn/snews/60686.htm
- http://m.wap.bwbkj.cn/snews/126344.htm
- http://m.wap.bwbkj.cn/snews/078887.htm
- http://m.wap.bwbkj.cn/snews/97343.htm
- http://m.wap.bwbkj.cn/snews/00867.htm
- http://m.wap.bwbkj.cn/snews/4106543.htm
- http://m.wap.bwbkj.cn/snews/800567.htm
- http://m.wap.bwbkj.cn/snews/42133.htm
- http://m.wap.bwbkj.cn/snews/718204.htm
- http://m.wap.bwbkj.cn/snews/145780.htm
- http://m.wap.bwbkj.cn/snews/2225.htm
- http://m.wap.bwbkj.cn/snews/88860.htm
- http://m.wap.bwbkj.cn/snews/39598.htm
- http://m.wap.bwbkj.cn/snews/9432.htm
- http://m.wap.bwbkj.cn/snews/267096.htm
- http://m.wap.bwbkj.cn/snews/6834777.htm
- http://m.wap.bwbkj.cn/snews/129078.htm
- http://m.wap.bwbkj.cn/snews/5706.htm
- http://m.wap.bwbkj.cn/snews/51685.htm
- http://m.wap.bwbkj.cn/snews/349943.htm
- http://m.wap.bwbkj.cn/snews/2832447.htm
- http://m.wap.bwbkj.cn/snews/18421.htm
- http://m.wap.bwbkj.cn/snews/9931406.htm
- http://m.wap.bwbkj.cn/snews/78536.htm
- http://m.wap.bwbkj.cn/snews/991308.htm
- http://m.wap.bwbkj.cn/snews/990988.htm
- http://m.wap.bwbkj.cn/snews/5139920.htm
- http://m.wap.bwbkj.cn/snews/1754288.htm
- http://m.wap.bwbkj.cn/snews/54351.htm
- http://m.wap.bwbkj.cn/snews/1323.htm
- http://m.wap.bwbkj.cn/snews/203555.htm
- http://m.wap.bwbkj.cn/snews/6745.htm
- http://m.wap.bwbkj.cn/snews/4702.htm
- http://m.wap.bwbkj.cn/snews/18134.htm
- http://m.wap.bwbkj.cn/snews/43707.htm
- http://m.wap.bwbkj.cn/snews/18558.htm
- http://m.wap.bwbkj.cn/snews/1585258.htm
- http://m.wap.bwbkj.cn/snews/35354.htm
- http://m.wap.bwbkj.cn/snews/238015.htm
- http://m.wap.bwbkj.cn/snews/77825.htm
- http://m.wap.bwbkj.cn/snews/2207911.htm
- http://m.wap.bwbkj.cn/snews/680145.htm
- http://m.wap.bwbkj.cn/snews/4407.htm
- http://m.wap.bwbkj.cn/snews/12992.htm
- http://m.wap.bwbkj.cn/snews/87924.htm
- http://m.wap.bwbkj.cn/snews/5981.htm
- http://m.wap.bwbkj.cn/snews/339140.htm
- http://m.wap.bwbkj.cn/snews/95185.htm
- http://m.wap.bwbkj.cn/snews/7678799.htm
- http://m.wap.bwbkj.cn/snews/9701.htm
- http://m.wap.bwbkj.cn/snews/956408.htm
- http://m.wap.bwbkj.cn/snews/10596.htm
- http://m.wap.bwbkj.cn/snews/411091.htm
- http://m.wap.bwbkj.cn/snews/0459485.htm
- http://m.wap.bwbkj.cn/snews/859189.htm
- http://m.wap.bwbkj.cn/snews/37805.htm
- http://m.wap.bwbkj.cn/snews/6963944.htm
- http://m.wap.bwbkj.cn/snews/7890.htm
- http://m.wap.bwbkj.cn/snews/954718.htm
- http://m.wap.bwbkj.cn/snews/62224.htm
- http://m.wap.bwbkj.cn/snews/34496.htm
- http://m.wap.bwbkj.cn/snews/58837.htm
- http://m.wap.bwbkj.cn/snews/46831.htm
- http://m.wap.bwbkj.cn/snews/44095.htm
- http://m.wap.bwbkj.cn/snews/0977.htm
- http://m.wap.bwbkj.cn/snews/094628.htm
- http://m.wap.bwbkj.cn/snews/1291170.htm
- http://m.wap.bwbkj.cn/snews/065989.htm
- http://m.wap.bwbkj.cn/snews/7362.htm
- http://m.wap.bwbkj.cn/snews/0740.htm
- http://m.wap.bwbkj.cn/snews/73346.htm
- http://m.wap.bwbkj.cn/snews/714779.htm
- http://m.wap.bwbkj.cn/snews/90311.htm
- http://m.wap.bwbkj.cn/snews/62391.htm
- http://m.wap.bwbkj.cn/snews/10269.htm
- http://m.wap.bwbkj.cn/snews/0024.htm
- http://m.wap.bwbkj.cn/snews/0967.htm
- http://m.wap.bwbkj.cn/snews/4754995.htm
- http://m.wap.bwbkj.cn/snews/8733.htm
- http://m.wap.bwbkj.cn/snews/8393.htm
- http://m.wap.bwbkj.cn/snews/2283919.htm
- http://m.wap.bwbkj.cn/snews/55665.htm
- http://m.wap.bwbkj.cn/snews/5604.htm
- http://m.wap.bwbkj.cn/snews/0250.htm
- http://m.wap.bwbkj.cn/snews/8850898.htm
- http://m.wap.bwbkj.cn/snews/625432.htm
- http://m.wap.bwbkj.cn/snews/0086.htm
- http://m.wap.bwbkj.cn/snews/38075.htm
- http://m.wap.bwbkj.cn/snews/8034.htm
- http://m.wap.bwbkj.cn/snews/63027.htm
- http://m.wap.bwbkj.cn/snews/26457.htm
- http://m.wap.bwbkj.cn/snews/945065.htm
- http://m.wap.bwbkj.cn/snews/5313686.htm
- http://m.wap.bwbkj.cn/snews/8566950.htm
- http://m.wap.bwbkj.cn/snews/4415.htm
- http://m.wap.bwbkj.cn/snews/706394.htm
- http://m.wap.bwbkj.cn/snews/2280329.htm
- http://m.wap.bwbkj.cn/snews/2746.htm
- http://m.wap.bwbkj.cn/snews/53711.htm
- http://m.wap.bwbkj.cn/snews/7129.htm
- http://m.wap.bwbkj.cn/snews/81444.htm
- http://m.wap.bwbkj.cn/snews/62658.htm
- http://m.wap.bwbkj.cn/snews/0323364.htm
- http://m.wap.bwbkj.cn/snews/94257.htm
- http://m.wap.bwbkj.cn/snews/26097.htm
- http://m.wap.bwbkj.cn/snews/8998.htm
- http://m.wap.bwbkj.cn/snews/349611.htm
- http://m.wap.bwbkj.cn/snews/1548.htm
- http://m.wap.bwbkj.cn/snews/2118.htm
- http://m.wap.bwbkj.cn/snews/3285.htm
- http://m.wap.bwbkj.cn/snews/72328.htm
- http://m.wap.bwbkj.cn/snews/9175645.htm
- http://m.wap.bwbkj.cn/snews/98473.htm
- http://m.wap.bwbkj.cn/snews/8951961.htm
- http://m.wap.bwbkj.cn/snews/3925758.htm
- http://m.wap.bwbkj.cn/snews/472986.htm
- http://m.wap.bwbkj.cn/snews/5063.htm
- http://m.wap.bwbkj.cn/snews/7310.htm
- http://m.wap.bwbkj.cn/snews/5610740.htm
- http://m.wap.bwbkj.cn/snews/6937210.htm
- http://m.wap.bwbkj.cn/snews/8492206.htm
- http://m.wap.bwbkj.cn/snews/11426.htm
- http://m.wap.bwbkj.cn/snews/1504953.htm
- http://m.wap.bwbkj.cn/snews/4218213.htm
- http://m.wap.bwbkj.cn/snews/4927.htm
- http://m.wap.bwbkj.cn/snews/2920485.htm
- http://m.wap.bwbkj.cn/snews/54258.htm
- http://m.wap.bwbkj.cn/snews/0220459.htm
- http://m.wap.bwbkj.cn/snews/712507.htm
- http://m.wap.bwbkj.cn/snews/946220.htm
- http://m.wap.bwbkj.cn/snews/078214.htm
- http://m.wap.bwbkj.cn/snews/4750358.htm
- http://m.wap.bwbkj.cn/snews/948784.htm
- http://m.wap.bwbkj.cn/snews/7272672.htm
- http://m.wap.bwbkj.cn/snews/8246.htm
- http://m.wap.bwbkj.cn/snews/8664.htm
- http://m.wap.bwbkj.cn/snews/9123940.htm
- http://m.wap.bwbkj.cn/snews/46615.htm
- http://m.wap.bwbkj.cn/snews/2352.htm
- http://m.wap.bwbkj.cn/snews/40465.htm
- http://m.wap.bwbkj.cn/snews/9180152.htm
- http://m.wap.bwbkj.cn/snews/382587.htm
- http://m.wap.bwbkj.cn/snews/362202.htm
- http://m.wap.bwbkj.cn/snews/75666.htm
- http://m.wap.bwbkj.cn/snews/802051.htm
- http://m.wap.bwbkj.cn/snews/8272828.htm
- http://m.wap.bwbkj.cn/snews/2648.htm
- http://m.wap.bwbkj.cn/snews/9238845.htm
- http://m.wap.bwbkj.cn/snews/6966.htm
- http://m.wap.bwbkj.cn/snews/9733805.htm
- http://m.wap.bwbkj.cn/snews/394061.htm
- http://m.wap.bwbkj.cn/snews/73853.htm
- http://m.wap.bwbkj.cn/snews/35655.htm
- http://m.wap.bwbkj.cn/snews/5170495.htm
- http://m.wap.bwbkj.cn/snews/0407.htm
- http://m.wap.bwbkj.cn/snews/900295.htm
- http://m.wap.bwbkj.cn/snews/66769.htm
- http://m.wap.bwbkj.cn/snews/15855.htm
- http://m.wap.bwbkj.cn/snews/1175.htm
- http://m.wap.bwbkj.cn/snews/662776.htm
- http://m.wap.bwbkj.cn/snews/90372.htm
- http://m.wap.bwbkj.cn/snews/9562.htm
- http://m.wap.bwbkj.cn/snews/8023.htm
- http://m.wap.bwbkj.cn/snews/6585.htm
- http://m.wap.bwbkj.cn/snews/02814.htm
- http://m.wap.bwbkj.cn/snews/70416.htm
- http://m.wap.bwbkj.cn/snews/55369.htm
- http://m.wap.bwbkj.cn/snews/0748.htm
- http://m.wap.bwbkj.cn/snews/49141.htm
- http://m.wap.bwbkj.cn/snews/6061.htm
- http://m.wap.bwbkj.cn/snews/82228.htm
- http://m.wap.bwbkj.cn/snews/0411264.htm
- http://m.wap.bwbkj.cn/snews/09210.htm
- http://m.wap.bwbkj.cn/snews/6059412.htm
- http://m.wap.bwbkj.cn/snews/99889.htm
- http://m.wap.bwbkj.cn/snews/5718.htm
- http://m.wap.bwbkj.cn/snews/5810.htm
- http://m.wap.bwbkj.cn/snews/6285.htm
- http://m.wap.bwbkj.cn/snews/677610.htm
- http://m.wap.bwbkj.cn/snews/59153.htm
- http://m.wap.bwbkj.cn/snews/0344.htm
- http://m.wap.bwbkj.cn/snews/993924.htm
- http://m.wap.bwbkj.cn/snews/95894.htm
- http://m.wap.bwbkj.cn/snews/0013234.htm

## 项目结构

```
weblink-navigator/
├── src/                                # 源代码主目录
│   ├── server/                         # 后端服务模块（Node.js + Express）
│   │   ├── app.js                      # Express 应用入口，注册中间件与路由
│   │   ├── routes/                     # REST API 路由定义（links, tags, health）
│   │   ├── controllers/                # 控制器层，处理请求参数与响应格式
│   │   ├── services/                   # 业务逻辑层，包含链接解析、检测调度等核心服务
│   │   └── models/                     # 数据模型层（使用 Sequelize 或 Knex 操作 SQLite）
│   ├── client/                         # 前端静态资源（React / Vue 单页应用）
│   │   ├── pages/                      # 路由页面组件（仪表板、链接列表、详情页）
│   │   ├── components/                 # 通用 UI 组件（表格、筛选器、状态徽标）
│   │   ├── hooks/                      # 自定义 React Hooks（数据请求、表单验证）
│   │   └── styles/                     # 全局样式表与主题变量（CSS Modules）
│   ├── workers/                        # 后台任务进程（独立于主线程运行）
│   │   ├── health-check.js             # 定时执行链接可用性检测的 Worker
│   │   └── report-generator.js         # 定期生成链接状态报告并写入日志
│   └── shared/                         # 前后端共享代码（常量定义、工具函数、类型声明）
│       ├── constants.js                # 状态码枚举、分类标签白名单、默认配置
│       └── validators.js               # URL 校验、参数格式清洗等通用函数
├── data/                               # 数据存储目录（默认 SQLite 文件存放位置）
│   └── weblink.db                      # SQLite 数据库文件（首次启动时自动生成）
├── logs/                               # 应用运行日志（访问日志、错误日志、检测报告）
│   ├── access.log                      # HTTP 请求访问日志（按天轮转）
│   └── health.log                      # 链接健康检测的详细输出与异常栈
├── config/                             # 配置文件目录（支持多环境）
│   ├── default.json                    # 默认配置项（端口、检测间隔、分页大小）
│   ├── production.json                 # 生产环境覆盖配置（关闭调试、启用缓存）
│   └── development.json                # 开发环境覆盖配置（开启热加载、详细日志）
├── scripts/                            # 辅助脚本与工具集
│   ├── import-csv.js                   # 从 CSV 文件批量导入链接的命令行工具
│   ├── export-json.js                  # 将当前链接数据导出为 JSON 格式
│   └── init-db.js                      # 初始化数据库表结构和默认标签
├── tests/                              # 单元测试与集成测试
│   ├── unit/                           # 针对服务层与工具函数的隔离测试
│   ├── integration/                    # API 端点端到端测试（使用 Supertest）
│   └── fixtures/                       # 测试用模拟数据（样本链接列表）
├── docs/                               # 完整项目文档（除 README 外的详细手册）
├── .env.example                        # 环境变量模板（JWT 密钥、代理地址等）
├── .gitignore                          # Git 忽略规则（node_modules, logs, data）
├── package.json                        # npm 项目清单（依赖列表与脚本命令）
├── package-lock.json                   # 依赖版本锁定文件
└── README.md                           # 项目说明文档（即本文件）
```

## 贡献指南

我们欢迎社区贡献者参与 WebLink Navigator 的改进与完善。请遵循以下流程提交您的贡献。

**提交 issue 讨论**：在开始任何代码或文档修改之前，请先在 GitHub Issues 中搜索是否存在相关讨论。若无，则新建一个 issue，清晰描述您发现的问题、建议的新功能或希望改进的文档章节，并等待维护者反馈。

**Fork 仓库并创建功能分支**：将主仓库 Fork 至您的个人账户，然后克隆到本地。基于主分支（main）创建一个新的功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 的格式，例如 `feature/add-export-csv`。

**编写或修改代码，并补充测试**：确保您的更改包含必要的单元测试或集成测试，且所有现有测试均能通过。代码风格需遵循项目配置的 ESLint 和 Prettier 规则。对于新增功能，请同步更新对应的 API 文档或使用说明。

**提交 Pull Request**：将您的功能分支推送至个人仓库，然后向主仓库的 main 分支发起 Pull Request。PR 标题应简明扼要，内容中需关联对应的 Issue 编号，并逐条列出您的改动点、测试结果以及可能影响现有功能的兼容性说明。PR 通过 CI 检查后，将由项目维护者进行 Code Review。

## 常见问题

**问：WebLink Navigator 能否同时管理超过 10000 条外链？性能表现如何？**

答：项目核心数据存储基于 SQLite，在合理索引设计下，支持万级链接的增删改查操作。对于可用性检测功能，系统采用异步并发请求控制（默认并发数为 50），检测 10000 条链接的完整周期约为 5-8 分钟（取决于网络状况）。若链接数量极大（如 10 万级以上），建议配合 Redis 缓存和消息队列改造部署架构，或使用 PostgreSQL 作为生产数据库。

**问：如何更新已导入链接的元数据（如分类标签或备注）？**

答：您可以通过 Web 管理面板的编辑功能逐条修改，也可以使用批量更新接口（API 端点 `/api/links/batch-update`）按 ID 列表统一修改标签或备注字段。此外，项目提供了 CSV 重新导入并覆盖的功能，您可以在导出当前数据后修改 CSV 文件，再通过 `scripts/import-csv.js` 脚本执行覆盖式导入。

**问：部署到生产环境时，如何确保外链检测功能不会对目标服务器造成压力？**

答：系统默认的检测请求间隔为 60 秒，且单次检测仅发送 HEAD 请求，不下载响应体，以最小化网络开销。您可以在配置文件中调整 `healthCheck.concurrency`（并发数）和 `healthCheck.interval`（执行间隔）。对于高价值或敏感目标，建议在环境变量中配置 `HEALTH_CHECK_WHITELIST` 和 `HEALTH_CHECK_BLACKLIST`，仅对特定域名执行检测。

## 许可证

MIT License。允许免费使用、修改、分发，仅需保留原始版权声明。详见项目根目录下的 LICENSE 文件。

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:10
