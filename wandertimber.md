# WebLink Navigator

WebLink Navigator 是一个面向技术研究与信息聚合场景的轻量级外链资源导航系统。该项目定位于帮助开发者、技术作者、信息整理人员快速收录、分类、检索和展示大量外部链接资源，特别适用于构建内部知识库、技术周报素材库、垂直领域外链集合等用途。本系统不提供内容抓取或存储服务，仅作为 URL 的索引、标签化与展示层，所有原始资源均以原始链接形式对外呈现。

项目当前处于第 252/300 批次资源收录阶段，已累计处理超过 250 批次的链接数据，具备稳定的批量导入、去重校验、分类标记和只读展示能力。目标用户包括开源社区文档维护者、技术自媒体运营者、企业内部知识管理团队以及需要频繁处理外链列表的研发人员。

## 功能概览

**批量链接导入** 支持通过文本文件、CSV 或直接粘贴方式一次性导入数百条 URL，系统自动完成格式清洗与重复项检测。

**原始链接透传展示** 所有收录的 URL 均以用户提交时的原始格式直接展示，不添加任何协议补全、域名规范化或跳转封装，确保链接可追溯性。

**分类标签系统** 允许为每条链接分配一个或多个主题标签，支持按标签筛选和聚合展示，便于构建专题资源页。

**只读访问模式** 面向公开访问的场景设计，默认所有链接为只读展示，不提供写入或修改接口，保证数据稳定性。

**搜索与过滤** 提供基于 URL 关键词、标签、收录批次号的快速检索能力，支持精确匹配和模糊查询。

**批次管理** 每一批导入的链接以批次号（如 252/300）为单位进行组织，支持按批次查看全部资源列表。

**响应式展示层** 前端展示层适配桌面与移动设备，所有链接以纯文本列表形式输出，不依赖 JavaScript 框架，兼容主流浏览器。

## 应用场景

**技术周报素材整理** 技术编辑在撰写每周资讯汇总时，需要收集大量外部参考链接。WebLink Navigator 可作为一个中间缓存层，将分散在浏览器书签、即时通讯记录、邮件中的链接统一导入并按主题分类，周报撰写时直接按标签导出列表。

**开源项目外部引用管理** 开源项目文档中常需要引用第三方资源、参考实现或相关标准。维护者可使用本系统集中管理这些外链，确保文档中的引用链接有据可查，并便于定期检查链接有效性。

**企业内部知识库外链聚合** 企业技术团队在构建内部 Wiki 或知识库时，往往需要引用大量外部技术文章、工具站点和 API 文档。WebLink Navigator 可作为知识库的一个外链前置层，统一收纳所有外部资源，内部文档仅需引用本系统中的链接 ID。

**个人书签系统增强** 个人开发者可将本系统作为书签管理工具的补充，利用批次和标签能力对收藏的链接进行结构性整理，取代传统的浏览器无层级书签。

## 快速开始

以下步骤帮助您在本地环境快速启动 WebLink Navigator 实例。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装依赖（基于 Node.js 18+ 与 npm）
npm install

# 启动开发服务器，默认监听端口 3000
npm run dev
```

启动成功后，访问 `http://localhost:3000` 即可看到资源列表首页。若需导入新的链接批次，可通过管理后台的导入功能提交文本文件，或直接调用 `POST /api/batches` 接口。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 18.x 或更高 | 运行时环境，用于执行服务端代码与构建工具 |
| npm | 8.x 或更高 | 包管理器，用于安装项目所有依赖库 |
| SQLite | 3.x（内置） | 轻量级嵌入式数据库，用于存储链接与批次数据，无需额外安装 |
| 内存 | 512 MB 及以上 | 运行服务的最小内存建议，生产环境建议 1 GB 以上 |
| 磁盘空间 | 100 MB 及以上 | 用于存放数据库文件与日志，链接数量增加时按需扩展 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | /docs/quick-start.md | 如何快速运行项目、导入第一批链接、访问前端页面 |
| API 参考 | /docs/api-reference.md | 所有 RESTful 接口的定义、请求参数、响应格式与状态码 |
| 数据格式 | /docs/data-format.md | 导入文件的格式要求、字段说明、批次与链接的数据结构 |
| 部署手册 | /docs/deployment.md | 如何将系统部署到生产环境，包括反向代理、持久化存储和性能调优 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/116808.htm
- http://m.wap.bwbkj.cn/snews/372690.htm
- http://m.wap.bwbkj.cn/snews/3671136.htm
- http://m.wap.bwbkj.cn/snews/5780867.htm
- http://m.wap.bwbkj.cn/snews/5903703.htm
- http://m.wap.bwbkj.cn/snews/8587.htm
- http://m.wap.bwbkj.cn/snews/9903848.htm
- http://m.wap.bwbkj.cn/snews/6640.htm
- http://m.wap.bwbkj.cn/snews/9244.htm
- http://m.wap.bwbkj.cn/snews/5645.htm
- http://m.wap.bwbkj.cn/snews/18867.htm
- http://m.wap.bwbkj.cn/snews/8249639.htm
- http://m.wap.bwbkj.cn/snews/01577.htm
- http://m.wap.bwbkj.cn/snews/767406.htm
- http://m.wap.bwbkj.cn/snews/5997.htm
- http://m.wap.bwbkj.cn/snews/7754.htm
- http://m.wap.bwbkj.cn/snews/6429383.htm
- http://m.wap.bwbkj.cn/snews/6311.htm
- http://m.wap.bwbkj.cn/snews/13279.htm
- http://m.wap.bwbkj.cn/snews/542346.htm
- http://m.wap.bwbkj.cn/snews/8495.htm
- http://m.wap.bwbkj.cn/snews/1299687.htm
- http://m.wap.bwbkj.cn/snews/62736.htm
- http://m.wap.bwbkj.cn/snews/3150200.htm
- http://m.wap.bwbkj.cn/snews/6536599.htm
- http://m.wap.bwbkj.cn/snews/2553447.htm
- http://m.wap.bwbkj.cn/snews/9066232.htm
- http://m.wap.bwbkj.cn/snews/5492744.htm
- http://m.wap.bwbkj.cn/snews/5458.htm
- http://m.wap.bwbkj.cn/snews/354775.htm
- http://m.wap.bwbkj.cn/snews/884829.htm
- http://m.wap.bwbkj.cn/snews/742465.htm
- http://m.wap.bwbkj.cn/snews/827896.htm
- http://m.wap.bwbkj.cn/snews/27374.htm
- http://m.wap.bwbkj.cn/snews/200685.htm
- http://m.wap.bwbkj.cn/snews/1039411.htm
- http://m.wap.bwbkj.cn/snews/290947.htm
- http://m.wap.bwbkj.cn/snews/92680.htm
- http://m.wap.bwbkj.cn/snews/223053.htm
- http://m.wap.bwbkj.cn/snews/3925.htm
- http://m.wap.bwbkj.cn/snews/8894068.htm
- http://m.wap.bwbkj.cn/snews/24595.htm
- http://m.wap.bwbkj.cn/snews/3727.htm
- http://m.wap.bwbkj.cn/snews/64106.htm
- http://m.wap.bwbkj.cn/snews/9896562.htm
- http://m.wap.bwbkj.cn/snews/50366.htm
- http://m.wap.bwbkj.cn/snews/9847.htm
- http://m.wap.bwbkj.cn/snews/4282828.htm
- http://m.wap.bwbkj.cn/snews/1915817.htm
- http://m.wap.bwbkj.cn/snews/8155.htm
- http://m.wap.bwbkj.cn/snews/9301167.htm
- http://m.wap.bwbkj.cn/snews/3809129.htm
- http://m.wap.bwbkj.cn/snews/261255.htm
- http://m.wap.bwbkj.cn/snews/23042.htm
- http://m.wap.bwbkj.cn/snews/1440186.htm
- http://m.wap.bwbkj.cn/snews/77481.htm
- http://m.wap.bwbkj.cn/snews/414672.htm
- http://m.wap.bwbkj.cn/snews/2189908.htm
- http://m.wap.bwbkj.cn/snews/270426.htm
- http://m.wap.bwbkj.cn/snews/45529.htm
- http://m.wap.bwbkj.cn/snews/0371939.htm
- http://m.wap.bwbkj.cn/snews/6390490.htm
- http://m.wap.bwbkj.cn/snews/0930.htm
- http://m.wap.bwbkj.cn/snews/684878.htm
- http://m.wap.bwbkj.cn/snews/155205.htm
- http://m.wap.bwbkj.cn/snews/3057375.htm
- http://m.wap.bwbkj.cn/snews/2269153.htm
- http://m.wap.bwbkj.cn/snews/4542915.htm
- http://m.wap.bwbkj.cn/snews/203063.htm
- http://m.wap.bwbkj.cn/snews/0512439.htm
- http://m.wap.bwbkj.cn/snews/117906.htm
- http://m.wap.bwbkj.cn/snews/8701.htm
- http://m.wap.bwbkj.cn/snews/674019.htm
- http://m.wap.bwbkj.cn/snews/147579.htm
- http://m.wap.bwbkj.cn/snews/4797961.htm
- http://m.wap.bwbkj.cn/snews/555661.htm
- http://m.wap.bwbkj.cn/snews/996006.htm
- http://m.wap.bwbkj.cn/snews/4756577.htm
- http://m.wap.bwbkj.cn/snews/60787.htm
- http://m.wap.bwbkj.cn/snews/6263.htm
- http://m.wap.bwbkj.cn/snews/857367.htm
- http://m.wap.bwbkj.cn/snews/6577964.htm
- http://m.wap.bwbkj.cn/snews/29659.htm
- http://m.wap.bwbkj.cn/snews/56782.htm
- http://m.wap.bwbkj.cn/snews/6816.htm
- http://m.wap.bwbkj.cn/snews/850062.htm
- http://m.wap.bwbkj.cn/snews/451823.htm
- http://m.wap.bwbkj.cn/snews/576746.htm
- http://m.wap.bwbkj.cn/snews/4191914.htm
- http://m.wap.bwbkj.cn/snews/2602339.htm
- http://m.wap.bwbkj.cn/snews/87113.htm
- http://m.wap.bwbkj.cn/snews/1932.htm
- http://m.wap.bwbkj.cn/snews/1113.htm
- http://m.wap.bwbkj.cn/snews/7596703.htm
- http://m.wap.bwbkj.cn/snews/5059.htm
- http://m.wap.bwbkj.cn/snews/8487999.htm
- http://m.wap.bwbkj.cn/snews/99070.htm
- http://m.wap.bwbkj.cn/snews/6018340.htm
- http://m.wap.bwbkj.cn/snews/2246141.htm
- http://m.wap.bwbkj.cn/snews/4426659.htm
- http://m.wap.bwbkj.cn/snews/9433922.htm
- http://m.wap.bwbkj.cn/snews/7851.htm
- http://m.wap.bwbkj.cn/snews/1052500.htm
- http://m.wap.bwbkj.cn/snews/2233.htm
- http://m.wap.bwbkj.cn/snews/6369434.htm
- http://m.wap.bwbkj.cn/snews/45086.htm
- http://m.wap.bwbkj.cn/snews/938544.htm
- http://m.wap.bwbkj.cn/snews/6494.htm
- http://m.wap.bwbkj.cn/snews/9665.htm
- http://m.wap.bwbkj.cn/snews/821312.htm
- http://m.wap.bwbkj.cn/snews/959370.htm
- http://m.wap.bwbkj.cn/snews/0978.htm
- http://m.wap.bwbkj.cn/snews/923282.htm
- http://m.wap.bwbkj.cn/snews/3310.htm
- http://m.wap.bwbkj.cn/snews/0769.htm
- http://m.wap.bwbkj.cn/snews/13217.htm
- http://m.wap.bwbkj.cn/snews/6360.htm
- http://m.wap.bwbkj.cn/snews/348607.htm
- http://m.wap.bwbkj.cn/snews/9225.htm
- http://m.wap.bwbkj.cn/snews/17499.htm
- http://m.wap.bwbkj.cn/snews/702823.htm
- http://m.wap.bwbkj.cn/snews/731409.htm
- http://m.wap.bwbkj.cn/snews/5133436.htm
- http://m.wap.bwbkj.cn/snews/68417.htm
- http://m.wap.bwbkj.cn/snews/369295.htm
- http://m.wap.bwbkj.cn/snews/57701.htm
- http://m.wap.bwbkj.cn/snews/690076.htm
- http://m.wap.bwbkj.cn/snews/49273.htm
- http://m.wap.bwbkj.cn/snews/01967.htm
- http://m.wap.bwbkj.cn/snews/12024.htm
- http://m.wap.bwbkj.cn/snews/67428.htm
- http://m.wap.bwbkj.cn/snews/2018.htm
- http://m.wap.bwbkj.cn/snews/7844.htm
- http://m.wap.bwbkj.cn/snews/2578.htm
- http://m.wap.bwbkj.cn/snews/1051483.htm
- http://m.wap.bwbkj.cn/snews/01989.htm
- http://m.wap.bwbkj.cn/snews/143300.htm
- http://m.wap.bwbkj.cn/snews/9649.htm
- http://m.wap.bwbkj.cn/snews/663188.htm
- http://m.wap.bwbkj.cn/snews/4407106.htm
- http://m.wap.bwbkj.cn/snews/46768.htm
- http://m.wap.bwbkj.cn/snews/4860.htm
- http://m.wap.bwbkj.cn/snews/760696.htm
- http://m.wap.bwbkj.cn/snews/368623.htm
- http://m.wap.bwbkj.cn/snews/0275.htm
- http://m.wap.bwbkj.cn/snews/914507.htm
- http://m.wap.bwbkj.cn/snews/1761.htm
- http://m.wap.bwbkj.cn/snews/10357.htm
- http://m.wap.bwbkj.cn/snews/9727.htm
- http://m.wap.bwbkj.cn/snews/2638.htm
- http://m.wap.bwbkj.cn/snews/37228.htm
- http://m.wap.bwbkj.cn/snews/08510.htm
- http://m.wap.bwbkj.cn/snews/2571808.htm
- http://m.wap.bwbkj.cn/snews/8048083.htm
- http://m.wap.bwbkj.cn/snews/3430375.htm
- http://m.wap.bwbkj.cn/snews/63102.htm
- http://m.wap.bwbkj.cn/snews/280729.htm
- http://m.wap.bwbkj.cn/snews/78143.htm
- http://m.wap.bwbkj.cn/snews/5816306.htm
- http://m.wap.bwbkj.cn/snews/4831240.htm
- http://m.wap.bwbkj.cn/snews/94969.htm
- http://m.wap.bwbkj.cn/snews/8716956.htm
- http://m.wap.bwbkj.cn/snews/6595.htm
- http://m.wap.bwbkj.cn/snews/8801867.htm
- http://m.wap.bwbkj.cn/snews/69566.htm
- http://m.wap.bwbkj.cn/snews/7106.htm
- http://m.wap.bwbkj.cn/snews/20586.htm
- http://m.wap.bwbkj.cn/snews/9882759.htm
- http://m.wap.bwbkj.cn/snews/1396510.htm
- http://m.wap.bwbkj.cn/snews/5484948.htm
- http://m.wap.bwbkj.cn/snews/79531.htm
- http://m.wap.bwbkj.cn/snews/85569.htm
- http://m.wap.bwbkj.cn/snews/9035.htm
- http://m.wap.bwbkj.cn/snews/239355.htm
- http://m.wap.bwbkj.cn/snews/2891124.htm
- http://m.wap.bwbkj.cn/snews/508972.htm
- http://m.wap.bwbkj.cn/snews/2381.htm
- http://m.wap.bwbkj.cn/snews/50346.htm
- http://m.wap.bwbkj.cn/snews/409274.htm
- http://m.wap.bwbkj.cn/snews/9139891.htm
- http://m.wap.bwbkj.cn/snews/16155.htm
- http://m.wap.bwbkj.cn/snews/239686.htm
- http://m.wap.bwbkj.cn/snews/16901.htm
- http://m.wap.bwbkj.cn/snews/6808.htm
- http://m.wap.bwbkj.cn/snews/39672.htm
- http://m.wap.bwbkj.cn/snews/4225273.htm
- http://m.wap.bwbkj.cn/snews/05838.htm
- http://m.wap.bwbkj.cn/snews/007454.htm
- http://m.wap.bwbkj.cn/snews/1114.htm
- http://m.wap.bwbkj.cn/snews/76174.htm
- http://m.wap.bwbkj.cn/snews/425502.htm
- http://m.wap.bwbkj.cn/snews/41315.htm
- http://m.wap.bwbkj.cn/snews/288132.htm
- http://m.wap.bwbkj.cn/snews/3428595.htm
- http://m.wap.bwbkj.cn/snews/9743.htm
- http://m.wap.bwbkj.cn/snews/1909.htm
- http://m.wap.bwbkj.cn/snews/9367159.htm
- http://m.wap.bwbkj.cn/snews/17657.htm
- http://m.wap.bwbkj.cn/snews/6285329.htm
- http://m.wap.bwbkj.cn/snews/7274837.htm
- http://m.wap.bwbkj.cn/snews/192131.htm
- http://m.wap.bwbkj.cn/snews/03766.htm
- http://m.wap.bwbkj.cn/snews/9385835.htm
- http://m.wap.bwbkj.cn/snews/1578.htm
- http://m.wap.bwbkj.cn/snews/4517647.htm
- http://m.wap.bwbkj.cn/snews/5154709.htm
- http://m.wap.bwbkj.cn/snews/2395072.htm
- http://m.wap.bwbkj.cn/snews/11735.htm
- http://m.wap.bwbkj.cn/snews/26648.htm
- http://m.wap.bwbkj.cn/snews/20188.htm
- http://m.wap.bwbkj.cn/snews/7873.htm
- http://m.wap.bwbkj.cn/snews/0239369.htm
- http://m.wap.bwbkj.cn/snews/528496.htm
- http://m.wap.bwbkj.cn/snews/060349.htm
- http://m.wap.bwbkj.cn/snews/73633.htm
- http://m.wap.bwbkj.cn/snews/5365.htm
- http://m.wap.bwbkj.cn/snews/0960273.htm
- http://m.wap.bwbkj.cn/snews/635318.htm
- http://m.wap.bwbkj.cn/snews/5980479.htm
- http://m.wap.bwbkj.cn/snews/2034811.htm
- http://m.wap.bwbkj.cn/snews/7086.htm
- http://m.wap.bwbkj.cn/snews/8940897.htm
- http://m.wap.bwbkj.cn/snews/2337315.htm
- http://m.wap.bwbkj.cn/snews/378916.htm
- http://m.wap.bwbkj.cn/snews/9572046.htm
- http://m.wap.bwbkj.cn/snews/0733.htm
- http://m.wap.bwbkj.cn/snews/0744128.htm
- http://m.wap.bwbkj.cn/snews/7258.htm
- http://m.wap.bwbkj.cn/snews/69681.htm
- http://m.wap.bwbkj.cn/snews/5659.htm
- http://m.wap.bwbkj.cn/snews/45790.htm
- http://m.wap.bwbkj.cn/snews/00695.htm
- http://m.wap.bwbkj.cn/snews/8198.htm
- http://m.wap.bwbkj.cn/snews/2680.htm
- http://m.wap.bwbkj.cn/snews/3099873.htm
- http://m.wap.bwbkj.cn/snews/6807659.htm
- http://m.wap.bwbkj.cn/snews/9055.htm
- http://m.wap.bwbkj.cn/snews/4659.htm
- http://m.wap.bwbkj.cn/snews/80696.htm
- http://m.wap.bwbkj.cn/snews/4113.htm
- http://m.wap.bwbkj.cn/snews/34254.htm
- http://m.wap.bwbkj.cn/snews/8209822.htm
- http://m.wap.bwbkj.cn/snews/726613.htm
- http://m.wap.bwbkj.cn/snews/7538.htm
- http://m.wap.bwbkj.cn/snews/2553962.htm
- http://m.wap.bwbkj.cn/snews/4833.htm
- http://m.wap.bwbkj.cn/snews/1194.htm
- http://m.wap.bwbkj.cn/snews/207042.htm
- http://m.wap.bwbkj.cn/snews/404213.htm
- http://m.wap.bwbkj.cn/snews/953019.htm
- http://m.wap.bwbkj.cn/snews/446766.htm
- http://m.wap.bwbkj.cn/snews/58746.htm
- http://m.wap.bwbkj.cn/snews/761539.htm
- http://m.wap.bwbkj.cn/snews/08737.htm
- http://m.wap.bwbkj.cn/snews/093631.htm
- http://m.wap.bwbkj.cn/snews/3234149.htm
- http://m.wap.bwbkj.cn/snews/26186.htm
- http://m.wap.bwbkj.cn/snews/6245355.htm
- http://m.wap.bwbkj.cn/snews/7789410.htm
- http://m.wap.bwbkj.cn/snews/22266.htm
- http://m.wap.bwbkj.cn/snews/112382.htm
- http://m.wap.bwbkj.cn/snews/7530.htm
- http://m.wap.bwbkj.cn/snews/7053.htm
- http://m.wap.bwbkj.cn/snews/73469.htm
- http://m.wap.bwbkj.cn/snews/16704.htm
- http://m.wap.bwbkj.cn/snews/4526.htm
- http://m.wap.bwbkj.cn/snews/82907.htm
- http://m.wap.bwbkj.cn/snews/5103.htm
- http://m.wap.bwbkj.cn/snews/851883.htm
- http://m.wap.bwbkj.cn/snews/5020.htm
- http://m.wap.bwbkj.cn/snews/0702672.htm
- http://m.wap.bwbkj.cn/snews/7134.htm
- http://m.wap.bwbkj.cn/snews/0210.htm
- http://m.wap.bwbkj.cn/snews/21962.htm
- http://m.wap.bwbkj.cn/snews/18390.htm
- http://m.wap.bwbkj.cn/snews/109123.htm
- http://m.wap.bwbkj.cn/snews/1415.htm
- http://m.wap.bwbkj.cn/snews/9493223.htm
- http://m.wap.bwbkj.cn/snews/57490.htm
- http://m.wap.bwbkj.cn/snews/4422.htm
- http://m.wap.bwbkj.cn/snews/226630.htm
- http://m.wap.bwbkj.cn/snews/1775.htm
- http://m.wap.bwbkj.cn/snews/44097.htm
- http://m.wap.bwbkj.cn/snews/2909237.htm
- http://m.wap.bwbkj.cn/snews/059750.htm
- http://m.wap.bwbkj.cn/snews/4142867.htm
- http://m.wap.bwbkj.cn/snews/78390.htm
- http://m.wap.bwbkj.cn/snews/58485.htm
- http://m.wap.bwbkj.cn/snews/4530.htm
- http://m.wap.bwbkj.cn/snews/0399.htm
- http://m.wap.bwbkj.cn/snews/4352.htm
- http://m.wap.bwbkj.cn/snews/033740.htm
- http://m.wap.bwbkj.cn/snews/66365.htm
- http://m.wap.bwbkj.cn/snews/704984.htm
- http://m.wap.bwbkj.cn/snews/845991.htm
- http://m.wap.bwbkj.cn/snews/4779.htm
- http://m.wap.bwbkj.cn/snews/826432.htm
- http://m.wap.bwbkj.cn/snews/6490189.htm
- http://m.wap.bwbkj.cn/snews/45958.htm
- http://m.wap.bwbkj.cn/snews/3971924.htm

## 项目结构

```
weblink-navigator/
├── src/
│   ├── server/                 # 服务端核心代码
│   │   ├── index.js            # 入口文件，初始化 Express 应用与数据库连接
│   │   ├── routes/             # 路由层，定义所有 API 端点
│   │   │   ├── batches.js      # 批次管理路由（创建、查询、列表）
│   │   │   └── links.js        # 链接查询路由（列表、搜索、按批次过滤）
│   │   ├── controllers/        # 控制器层，处理请求参数与响应格式
│   │   │   ├── batchController.js
│   │   │   └── linkController.js
│   │   ├── models/             # 数据模型层，封装 SQLite 表操作
│   │   │   ├── BatchModel.js   # 批次表的增删改查方法
│   │   │   └── LinkModel.js    # 链接表的批量插入与查询方法
│   │   └── utils/              # 工具函数集合
│   │       ├── validator.js    # URL 格式校验与去重逻辑
│   │       └── importer.js     # 批量导入解析器（支持纯文本与 CSV）
│   ├── client/                 # 前端静态资源
│   │   ├── index.html          # 首页 HTML 模板，展示所有链接列表
│   │   ├── styles/             # CSS 样式文件
│   │   │   └── main.css        # 响应式布局与基础样式定义
│   │   └── scripts/            # 前端交互脚本（仅用于搜索过滤，无框架依赖）
│   │       └── filter.js
│   └── config/                 # 配置文件目录
│       ├── database.js         # 数据库初始化与连接配置
│       └── settings.js         # 服务端口、日志级别等运行参数
├── data/                       # 数据持久化目录（SQLite 数据库文件存放处）
│   └── weblink.db              # 主数据库文件（首次启动时自动生成）
├── tests/                      # 单元测试与集成测试脚本
│   ├── unit/                   # 模型层与工具函数单元测试
│   └── integration/            # API 接口端到端测试
├── docs/                       # 完整文档，详见文档导航章节
│   ├── quick-start.md
│   ├── api-reference.md
│   ├── data-format.md
│   └── deployment.md
├── .gitignore                  # Git 忽略规则，排除 node_modules 与 data/*.db
├── package.json                # npm 依赖清单与脚本定义
├── README.md                   # 本文件
└── LICENSE                     # MIT 许可证文本
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境中进行修改。建议先阅读 `docs/` 目录下的设计文档，了解整体架构后再着手代码改动。

2. 创建新的功能分支，分支命名规则为 `feature/简要描述` 或 `fix/问题编号`。所有代码修改需确保通过现有单元测试，并为新增功能补充对应的测试用例。

3. 提交代码前运行 `npm run lint` 检查代码风格，并执行 `npm test` 确认所有测试通过。提交信息请使用简洁明确的英文描述，格式为 `<类型>: <简短说明>`，例如 `feat: add batch export API`。

4. 向主仓库发起 Pull Request，描述中需说明改动目的、实现方式以及是否涉及数据库迁移或配置变更。PR 需要至少一名维护者审核通过后方可合并。

5. 若发现链接失效、分类错误或希望新增功能，请先在 Issues 中创建工单进行讨论，避免直接提交未经确认的大规模改动。

## 常见问题

**Q: 系统是否会主动访问或验证这些外部链接的有效性？**

A: 不会。WebLink Navigator 仅作为 URL 的索引与展示层，不发起任何对外部资源的 HTTP 请求，也不验证链接是否可访问。所有链接以用户提交时的原始状态保存和显示，使用者应自行确认链接的有效性。

**Q: 如何批量导入下一批链接？导入文件有什么格式要求？**

A: 可通过管理后台的导入界面上传文本文件，或使用 `POST /api/batches` 接口提交 JSON 格式数据。文本文件要求每行一个 URL，空行自动忽略。JSON 格式要求包含 `batchName` 和 `links` 数组字段。具体格式示例请参考 `docs/data-format.md` 文档。

**Q: 数据库文件会随着链接数量增加而变得过大吗？如何优化？**

A: SQLite 对百万级记录的表有良好支持。本系统每条链接仅存储 URL 字符串、标签和批次号三个主要字段，单条记录体积很小。若链接数量超过 10 万条，建议定期执行 `VACUUM` 命令回收数据库空间，并考虑对 `url` 字段建立索引以加速搜索。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:10
