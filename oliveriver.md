# NewsIndexer

NewsIndexer 是一个面向技术资讯聚合与历史新闻存档检索的开源外链归集系统。项目定位于为开发者、数据分析师、内容研究人员提供一套结构化的新闻链接管理方案，能够将散落在各类渠道中的新闻页面 URL 按照统一格式进行归集、编号、分类与快速访问。NewsIndexer 不生产新闻内容，也不做全文抓取与存储，而是以轻量级索引方式维护一批高质量新闻外链，帮助用户避免链接遗失、检索困难、来源不可考等问题。项目适用于个人知识库搭建、团队共享新闻池、舆情素材收集、以及历史事件时间线整理等场景。

## 功能概览

批量链接导入：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入新闻外链，自动解析 URL 结构并提取编号信息。

索引编号生成：为每条导入的链接自动分配唯一索引编号，编号规则支持自定义前缀与日期时间戳组合，便于后续检索与引用。

分类标签管理：允许用户为每条链接添加多个分类标签，标签支持层级结构，可按照主题、来源、地域、重要性等维度进行组织。

检索与过滤：提供基于关键词、编号范围、标签组合、导入时间等多条件联合检索能力，支持正则表达式匹配与模糊搜索。

导出与分享：支持将选中的链接列表导出为 Markdown 表格、JSON、CSV 等格式，方便嵌入报告、文档或用于数据交换。

访问状态检测：内置链接可达性检测模块，可定期检查已收录链接的 HTTP 状态码，标记失效或重定向链接，辅助维护索引质量。

批处理操作：支持对选中链接进行批量标签添加、批量删除、批量编号重排等操作，提高大规模链接管理效率。

## 应用场景

技术团队内部知识库建设：技术团队在日常开发中会积累大量参考文档、博客教程、官方公告等外链。NewsIndexer 可以帮助团队将分散在邮件、聊天记录、浏览器书签中的链接统一归集到同一个索引库中，并按照技术栈、项目名称、重要程度等维度进行分类，方便新成员快速了解项目历史背景与技术选型依据。

舆情监控与素材收集：内容运营人员或市场分析师需要持续跟踪特定行业或事件的相关报道。NewsIndexer 可以批量导入每日发现的新闻链接，通过标签体系标注事件类型、涉及主体、情感倾向等属性，后续可通过检索快速调取某一时间段内的全部相关链接，形成舆情分析报告的基础素材列表。

历史新闻存档与时间线整理：研究人员在梳理某一历史事件的发展脉络时，需要整理大量的新闻报道链接。NewsIndexer 的编号系统与导入时间戳可以天然形成时间序列，配合标签与关键词检索，能够帮助研究者快速定位特定时间节点的事件报道，构建事件时间线索引。

个人阅读列表与书签管理替代：个人用户可以使用 NewsIndexer 替代传统的浏览器书签管理，通过导入每日阅读的新闻链接并添加个人备注与标签，形成带有语义信息的阅读历史库，便于后续回顾与引用。

## 快速开始

以下命令演示了如何从 GitHub 克隆 NewsIndexer 仓库、安装依赖并启动本地服务。

```bash
git clone https://github.com/newsindexer/newsindexer.git
cd newsindexer
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 长期支持版本 |
| Django | 4.2 LTS | Web 框架，用于提供管理界面与 API 服务 |
| SQLite | 3.35 及以上 | 默认数据库，用于存储链接索引与标签数据 |
| requests | 2.31.0 及以上 | 用于发送 HTTP 请求检测链接可达性 |
| pytest | 7.4.0 及以上 | 单元测试框架，仅开发环境需要 |
| nodejs | 18.x 及以上 | 前端静态资源构建工具依赖，仅开发环境需要 |
| npm | 9.x 及以上 | 前端包管理器，仅开发环境需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速安装并运行 NewsIndexer，完成第一个链接的导入与检索 |
| 功能手册 | docs/user-manual.md | 所有功能的详细操作说明，包括导入、标签、检索、导出、状态检测等 |
| API 参考 | docs/api-reference.md | RESTful API 端点列表、请求参数与响应格式说明，用于二次开发与集成 |
| 运维指南 | docs/operations.md | 生产环境部署建议、性能调优参数、数据库备份与恢复策略 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/2754.htm
- http://m.3g.ghtkgg.cn/nnews/1047087.htm
- http://m.3g.ghtkgg.cn/nnews/0635.htm
- http://m.3g.ghtkgg.cn/nnews/000866.htm
- http://m.3g.ghtkgg.cn/nnews/36935.htm
- http://m.3g.ghtkgg.cn/nnews/61498.htm
- http://m.3g.ghtkgg.cn/nnews/0378.htm
- http://m.3g.ghtkgg.cn/nnews/3114388.htm
- http://m.3g.ghtkgg.cn/nnews/9175.htm
- http://m.3g.ghtkgg.cn/nnews/8343371.htm
- http://m.3g.ghtkgg.cn/nnews/2063.htm
- http://m.3g.ghtkgg.cn/nnews/872775.htm
- http://m.3g.ghtkgg.cn/nnews/755987.htm
- http://m.3g.ghtkgg.cn/nnews/1031886.htm
- http://m.3g.ghtkgg.cn/nnews/55373.htm
- http://m.3g.ghtkgg.cn/nnews/4477316.htm
- http://m.3g.ghtkgg.cn/nnews/49576.htm
- http://m.3g.ghtkgg.cn/nnews/7309.htm
- http://m.3g.ghtkgg.cn/nnews/6460609.htm
- http://m.3g.ghtkgg.cn/nnews/591299.htm
- http://m.3g.ghtkgg.cn/nnews/4218027.htm
- http://m.3g.ghtkgg.cn/nnews/26953.htm
- http://m.3g.ghtkgg.cn/nnews/3996230.htm
- http://m.3g.ghtkgg.cn/nnews/4499623.htm
- http://m.3g.ghtkgg.cn/nnews/6580.htm
- http://m.3g.ghtkgg.cn/nnews/0122.htm
- http://m.3g.ghtkgg.cn/nnews/328019.htm
- http://m.3g.ghtkgg.cn/nnews/17019.htm
- http://m.3g.ghtkgg.cn/nnews/07370.htm
- http://m.3g.ghtkgg.cn/nnews/3870.htm
- http://m.3g.ghtkgg.cn/nnews/9179.htm
- http://m.3g.ghtkgg.cn/nnews/4098239.htm
- http://m.3g.ghtkgg.cn/nnews/1912.htm
- http://m.3g.ghtkgg.cn/nnews/26364.htm
- http://m.3g.ghtkgg.cn/nnews/1969.htm
- http://m.3g.ghtkgg.cn/nnews/4176567.htm
- http://m.3g.ghtkgg.cn/nnews/7623288.htm
- http://m.3g.ghtkgg.cn/nnews/846198.htm
- http://m.3g.ghtkgg.cn/nnews/457083.htm
- http://m.3g.ghtkgg.cn/nnews/166337.htm
- http://m.3g.ghtkgg.cn/nnews/01697.htm
- http://m.3g.ghtkgg.cn/nnews/6580910.htm
- http://m.3g.ghtkgg.cn/nnews/5487860.htm
- http://m.3g.ghtkgg.cn/nnews/1562.htm
- http://m.3g.ghtkgg.cn/nnews/4177962.htm
- http://m.3g.ghtkgg.cn/nnews/833467.htm
- http://m.3g.ghtkgg.cn/nnews/76874.htm
- http://m.3g.ghtkgg.cn/nnews/993251.htm
- http://m.3g.ghtkgg.cn/nnews/329186.htm
- http://m.3g.ghtkgg.cn/nnews/3244948.htm
- http://m.3g.ghtkgg.cn/nnews/3128.htm
- http://m.3g.ghtkgg.cn/nnews/33921.htm
- http://m.3g.ghtkgg.cn/nnews/6993522.htm
- http://m.3g.ghtkgg.cn/nnews/843141.htm
- http://m.3g.ghtkgg.cn/nnews/665812.htm
- http://m.3g.ghtkgg.cn/nnews/270719.htm
- http://m.3g.ghtkgg.cn/nnews/300400.htm
- http://m.3g.ghtkgg.cn/nnews/9211.htm
- http://m.3g.ghtkgg.cn/nnews/71728.htm
- http://m.3g.ghtkgg.cn/nnews/7921191.htm
- http://m.3g.ghtkgg.cn/nnews/43068.htm
- http://m.3g.ghtkgg.cn/nnews/741799.htm
- http://m.3g.ghtkgg.cn/nnews/8359.htm
- http://m.3g.ghtkgg.cn/nnews/1188570.htm
- http://m.3g.ghtkgg.cn/nnews/7821489.htm
- http://m.3g.ghtkgg.cn/nnews/73466.htm
- http://m.3g.ghtkgg.cn/nnews/8500467.htm
- http://m.3g.ghtkgg.cn/nnews/925232.htm
- http://m.3g.ghtkgg.cn/nnews/95809.htm
- http://m.3g.ghtkgg.cn/nnews/254952.htm
- http://m.3g.ghtkgg.cn/nnews/92615.htm
- http://m.3g.ghtkgg.cn/nnews/4042.htm
- http://m.3g.ghtkgg.cn/nnews/2443782.htm
- http://m.3g.ghtkgg.cn/nnews/17216.htm
- http://m.3g.ghtkgg.cn/nnews/665116.htm
- http://m.3g.ghtkgg.cn/nnews/6127882.htm
- http://m.3g.ghtkgg.cn/nnews/514640.htm
- http://m.3g.ghtkgg.cn/nnews/37260.htm
- http://m.3g.ghtkgg.cn/nnews/9391657.htm
- http://m.3g.ghtkgg.cn/nnews/2447842.htm
- http://m.3g.ghtkgg.cn/nnews/5062050.htm
- http://m.3g.ghtkgg.cn/nnews/6751045.htm
- http://m.3g.ghtkgg.cn/nnews/62762.htm
- http://m.3g.ghtkgg.cn/nnews/6010.htm
- http://m.3g.ghtkgg.cn/nnews/5189.htm
- http://m.3g.ghtkgg.cn/nnews/4624177.htm
- http://m.3g.ghtkgg.cn/nnews/59071.htm
- http://m.3g.ghtkgg.cn/nnews/353195.htm
- http://m.3g.ghtkgg.cn/nnews/2358402.htm
- http://m.3g.ghtkgg.cn/nnews/851372.htm
- http://m.3g.ghtkgg.cn/nnews/6740813.htm
- http://m.3g.ghtkgg.cn/nnews/0167389.htm
- http://m.3g.ghtkgg.cn/nnews/56274.htm
- http://m.3g.ghtkgg.cn/nnews/944816.htm
- http://m.3g.ghtkgg.cn/nnews/46187.htm
- http://m.3g.ghtkgg.cn/nnews/900695.htm
- http://m.3g.ghtkgg.cn/nnews/96617.htm
- http://m.3g.ghtkgg.cn/nnews/282518.htm
- http://m.3g.ghtkgg.cn/nnews/168164.htm
- http://m.3g.ghtkgg.cn/nnews/7044.htm
- http://m.3g.ghtkgg.cn/nnews/65339.htm
- http://m.3g.ghtkgg.cn/nnews/1938.htm
- http://m.3g.ghtkgg.cn/nnews/5854802.htm
- http://m.3g.ghtkgg.cn/nnews/96343.htm
- http://m.3g.ghtkgg.cn/nnews/1503.htm
- http://m.3g.ghtkgg.cn/nnews/482068.htm
- http://m.3g.ghtkgg.cn/nnews/1631253.htm
- http://m.3g.ghtkgg.cn/nnews/4145.htm
- http://m.3g.ghtkgg.cn/nnews/9722.htm
- http://m.3g.ghtkgg.cn/nnews/594042.htm
- http://m.3g.ghtkgg.cn/nnews/8335681.htm
- http://m.3g.ghtkgg.cn/nnews/801335.htm
- http://m.3g.ghtkgg.cn/nnews/25851.htm
- http://m.3g.ghtkgg.cn/nnews/1811198.htm
- http://m.3g.ghtkgg.cn/nnews/843823.htm
- http://m.3g.ghtkgg.cn/nnews/2653.htm
- http://m.3g.ghtkgg.cn/nnews/9451.htm
- http://m.3g.ghtkgg.cn/nnews/415304.htm
- http://m.3g.ghtkgg.cn/nnews/37298.htm
- http://m.3g.ghtkgg.cn/nnews/85523.htm
- http://m.3g.ghtkgg.cn/nnews/987913.htm
- http://m.3g.ghtkgg.cn/nnews/0852.htm
- http://m.3g.ghtkgg.cn/nnews/926530.htm
- http://m.3g.ghtkgg.cn/nnews/44614.htm
- http://m.3g.ghtkgg.cn/nnews/6516.htm
- http://m.3g.ghtkgg.cn/nnews/377852.htm
- http://m.3g.ghtkgg.cn/nnews/7845237.htm
- http://m.3g.ghtkgg.cn/nnews/49142.htm
- http://m.3g.ghtkgg.cn/nnews/621656.htm
- http://m.3g.ghtkgg.cn/nnews/181418.htm
- http://m.3g.ghtkgg.cn/nnews/17827.htm
- http://m.3g.ghtkgg.cn/nnews/5166531.htm
- http://m.3g.ghtkgg.cn/nnews/1006.htm
- http://m.3g.ghtkgg.cn/nnews/326600.htm
- http://m.3g.ghtkgg.cn/nnews/8255.htm
- http://m.3g.ghtkgg.cn/nnews/126668.htm
- http://m.3g.ghtkgg.cn/nnews/5158.htm
- http://m.3g.ghtkgg.cn/nnews/615236.htm
- http://m.3g.ghtkgg.cn/nnews/9472399.htm
- http://m.3g.ghtkgg.cn/nnews/3518050.htm
- http://m.3g.ghtkgg.cn/nnews/56052.htm
- http://m.3g.ghtkgg.cn/nnews/7064666.htm
- http://m.3g.ghtkgg.cn/nnews/068174.htm
- http://m.3g.ghtkgg.cn/nnews/52314.htm
- http://m.3g.ghtkgg.cn/nnews/7658091.htm
- http://m.3g.ghtkgg.cn/nnews/5649.htm
- http://m.3g.ghtkgg.cn/nnews/96848.htm
- http://m.3g.ghtkgg.cn/nnews/9055601.htm
- http://m.3g.ghtkgg.cn/nnews/3430327.htm
- http://m.3g.ghtkgg.cn/nnews/2196.htm
- http://m.3g.ghtkgg.cn/nnews/36117.htm
- http://m.3g.ghtkgg.cn/nnews/979755.htm
- http://m.3g.ghtkgg.cn/nnews/2995496.htm
- http://m.3g.ghtkgg.cn/nnews/0284389.htm
- http://m.3g.ghtkgg.cn/nnews/03401.htm
- http://m.3g.ghtkgg.cn/nnews/06267.htm
- http://m.3g.ghtkgg.cn/nnews/12210.htm
- http://m.3g.ghtkgg.cn/nnews/8200.htm
- http://m.3g.ghtkgg.cn/nnews/3961.htm
- http://m.3g.ghtkgg.cn/nnews/9733328.htm
- http://m.3g.ghtkgg.cn/nnews/58855.htm
- http://m.3g.ghtkgg.cn/nnews/089603.htm
- http://m.3g.ghtkgg.cn/nnews/03125.htm
- http://m.3g.ghtkgg.cn/nnews/1645894.htm
- http://m.3g.ghtkgg.cn/nnews/264484.htm
- http://m.3g.ghtkgg.cn/nnews/482820.htm
- http://m.3g.ghtkgg.cn/nnews/8590110.htm
- http://m.3g.ghtkgg.cn/nnews/1456556.htm
- http://m.3g.ghtkgg.cn/nnews/26392.htm
- http://m.3g.ghtkgg.cn/nnews/3613.htm
- http://m.3g.ghtkgg.cn/nnews/8530677.htm
- http://m.3g.ghtkgg.cn/nnews/6718993.htm
- http://m.3g.ghtkgg.cn/nnews/8598802.htm
- http://m.3g.ghtkgg.cn/nnews/09599.htm
- http://m.3g.ghtkgg.cn/nnews/0348.htm
- http://m.3g.ghtkgg.cn/nnews/7696.htm
- http://m.3g.ghtkgg.cn/nnews/8470436.htm
- http://m.3g.ghtkgg.cn/nnews/303085.htm
- http://m.3g.ghtkgg.cn/nnews/43933.htm
- http://m.3g.ghtkgg.cn/nnews/07932.htm
- http://m.3g.ghtkgg.cn/nnews/36740.htm
- http://m.3g.ghtkgg.cn/nnews/0676660.htm
- http://m.3g.ghtkgg.cn/nnews/232006.htm
- http://m.3g.ghtkgg.cn/nnews/84554.htm
- http://m.3g.ghtkgg.cn/nnews/6618.htm
- http://m.3g.ghtkgg.cn/nnews/03351.htm
- http://m.3g.ghtkgg.cn/nnews/1078.htm
- http://m.3g.ghtkgg.cn/nnews/21123.htm
- http://m.3g.ghtkgg.cn/nnews/8944.htm
- http://m.3g.ghtkgg.cn/nnews/4771769.htm
- http://m.3g.ghtkgg.cn/nnews/7348.htm
- http://m.3g.ghtkgg.cn/nnews/692429.htm
- http://m.3g.ghtkgg.cn/nnews/337941.htm
- http://m.3g.ghtkgg.cn/nnews/031253.htm
- http://m.3g.ghtkgg.cn/nnews/5255914.htm
- http://m.3g.ghtkgg.cn/nnews/70688.htm
- http://m.3g.ghtkgg.cn/nnews/03543.htm
- http://m.3g.ghtkgg.cn/nnews/097114.htm
- http://m.3g.ghtkgg.cn/nnews/237531.htm
- http://m.3g.ghtkgg.cn/nnews/023108.htm
- http://m.3g.ghtkgg.cn/nnews/176755.htm
- http://m.3g.ghtkgg.cn/nnews/52254.htm
- http://m.3g.ghtkgg.cn/nnews/1604074.htm
- http://m.3g.ghtkgg.cn/nnews/9296331.htm
- http://m.3g.ghtkgg.cn/nnews/913167.htm
- http://m.3g.ghtkgg.cn/nnews/82037.htm
- http://m.3g.ghtkgg.cn/nnews/61884.htm
- http://m.3g.ghtkgg.cn/nnews/280903.htm
- http://m.3g.ghtkgg.cn/nnews/41403.htm
- http://m.3g.ghtkgg.cn/nnews/056389.htm
- http://m.3g.ghtkgg.cn/nnews/4555.htm
- http://m.3g.ghtkgg.cn/nnews/9664.htm
- http://m.3g.ghtkgg.cn/nnews/45838.htm
- http://m.3g.ghtkgg.cn/nnews/97037.htm
- http://m.3g.ghtkgg.cn/nnews/2524100.htm
- http://m.3g.ghtkgg.cn/nnews/9230.htm
- http://m.3g.ghtkgg.cn/nnews/99583.htm
- http://m.3g.ghtkgg.cn/nnews/75429.htm
- http://m.3g.ghtkgg.cn/nnews/607091.htm
- http://m.3g.ghtkgg.cn/nnews/08930.htm
- http://m.3g.ghtkgg.cn/nnews/02274.htm
- http://m.3g.ghtkgg.cn/nnews/6506568.htm
- http://m.3g.ghtkgg.cn/nnews/79799.htm
- http://m.3g.ghtkgg.cn/nnews/350032.htm
- http://m.3g.ghtkgg.cn/nnews/4129982.htm
- http://m.3g.ghtkgg.cn/nnews/21257.htm
- http://m.3g.ghtkgg.cn/nnews/86123.htm
- http://m.3g.ghtkgg.cn/nnews/70715.htm
- http://m.3g.ghtkgg.cn/nnews/9526224.htm
- http://m.3g.ghtkgg.cn/nnews/30166.htm
- http://m.3g.ghtkgg.cn/nnews/496503.htm
- http://m.3g.ghtkgg.cn/nnews/837350.htm
- http://m.3g.ghtkgg.cn/nnews/85684.htm
- http://m.3g.ghtkgg.cn/nnews/5230488.htm
- http://m.3g.ghtkgg.cn/nnews/83441.htm
- http://m.3g.ghtkgg.cn/nnews/4624327.htm
- http://m.3g.ghtkgg.cn/nnews/521724.htm
- http://m.3g.ghtkgg.cn/nnews/6159.htm
- http://m.3g.ghtkgg.cn/nnews/5913.htm
- http://m.3g.ghtkgg.cn/nnews/5531544.htm
- http://m.3g.ghtkgg.cn/nnews/6736164.htm
- http://m.3g.ghtkgg.cn/nnews/191365.htm
- http://m.3g.ghtkgg.cn/nnews/6659.htm
- http://m.3g.ghtkgg.cn/nnews/7205757.htm
- http://m.3g.ghtkgg.cn/nnews/00030.htm
- http://m.3g.ghtkgg.cn/nnews/510447.htm
- http://m.3g.ghtkgg.cn/nnews/068797.htm
- http://m.3g.ghtkgg.cn/nnews/3409497.htm
- http://m.3g.ghtkgg.cn/nnews/5422.htm
- http://m.3g.ghtkgg.cn/nnews/3103793.htm
- http://m.3g.ghtkgg.cn/nnews/1994.htm
- http://m.3g.ghtkgg.cn/nnews/27925.htm
- http://m.3g.ghtkgg.cn/nnews/024182.htm
- http://m.3g.ghtkgg.cn/nnews/535077.htm
- http://m.3g.ghtkgg.cn/nnews/405534.htm
- http://m.3g.ghtkgg.cn/nnews/722514.htm
- http://m.3g.ghtkgg.cn/nnews/825414.htm
- http://m.3g.ghtkgg.cn/nnews/4836773.htm
- http://m.3g.ghtkgg.cn/nnews/4528.htm
- http://m.3g.ghtkgg.cn/nnews/037398.htm
- http://m.3g.ghtkgg.cn/nnews/883420.htm
- http://m.3g.ghtkgg.cn/nnews/1302497.htm
- http://m.3g.ghtkgg.cn/nnews/8986.htm
- http://m.3g.ghtkgg.cn/nnews/66430.htm
- http://m.3g.ghtkgg.cn/nnews/20913.htm
- http://m.3g.ghtkgg.cn/nnews/6660472.htm
- http://m.3g.ghtkgg.cn/nnews/35636.htm
- http://m.3g.ghtkgg.cn/nnews/861092.htm
- http://m.3g.ghtkgg.cn/nnews/0550.htm
- http://m.3g.ghtkgg.cn/nnews/13899.htm
- http://m.3g.ghtkgg.cn/nnews/208232.htm
- http://m.3g.ghtkgg.cn/nnews/38587.htm
- http://m.3g.ghtkgg.cn/nnews/0460073.htm
- http://m.3g.ghtkgg.cn/nnews/9467822.htm
- http://m.3g.ghtkgg.cn/nnews/872055.htm
- http://m.3g.ghtkgg.cn/nnews/67831.htm
- http://m.3g.ghtkgg.cn/nnews/039287.htm
- http://m.3g.ghtkgg.cn/nnews/354058.htm
- http://m.3g.ghtkgg.cn/nnews/9081561.htm
- http://m.3g.ghtkgg.cn/nnews/9951.htm
- http://m.3g.ghtkgg.cn/nnews/0529253.htm
- http://m.3g.ghtkgg.cn/nnews/0124110.htm
- http://m.3g.ghtkgg.cn/nnews/0054.htm
- http://m.3g.ghtkgg.cn/nnews/007177.htm
- http://m.3g.ghtkgg.cn/nnews/524156.htm
- http://m.3g.ghtkgg.cn/nnews/3347.htm
- http://m.3g.ghtkgg.cn/nnews/0778.htm
- http://m.3g.ghtkgg.cn/nnews/3695853.htm
- http://m.3g.ghtkgg.cn/nnews/9710.htm
- http://m.3g.ghtkgg.cn/nnews/2133223.htm
- http://m.3g.ghtkgg.cn/nnews/3807414.htm
- http://m.3g.ghtkgg.cn/nnews/8686460.htm
- http://m.3g.ghtkgg.cn/nnews/5124758.htm
- http://m.3g.ghtkgg.cn/nnews/27939.htm
- http://m.3g.ghtkgg.cn/nnews/785130.htm
- http://m.3g.ghtkgg.cn/nnews/150759.htm
- http://m.3g.ghtkgg.cn/nnews/76976.htm
- http://m.3g.ghtkgg.cn/nnews/416440.htm
- http://m.3g.ghtkgg.cn/nnews/1702223.htm
- http://m.3g.ghtkgg.cn/nnews/7868147.htm

## 项目结构

```
newsindexer/
├── manage.py                      # Django 项目管理入口脚本
├── requirements.txt               # Python 后端依赖清单
├── package.json                   # Node.js 前端构建依赖清单
├── newsindexer/                   # 项目主配置目录
│   ├── settings.py                # 全局配置（数据库、中间件、静态资源等）
│   ├── urls.py                    # 根路由配置，映射 API 与页面路由
│   ├── wsgi.py                    # 生产环境 WSGI 入口
│   └── asgi.py                    # 异步 ASGI 入口，用于 WebSocket 支持
├── apps/                          # 所有自定义 Django 应用存放目录
│   ├── core/                      # 核心功能应用：链接索引、编号生成、标签管理
│   │   ├── models.py              # Link, Tag, LinkTag 数据模型定义
│   │   ├── services.py            # 链接导入、编号生成、状态检测等业务逻辑
│   │   └── admin.py               # Django 管理后台定制配置
│   ├── api/                       # RESTful API 应用：对外提供接口服务
│   │   ├── views.py               # API 视图集，处理检索、导入、导出等请求
│   │   ├── serializers.py         # 数据序列化器，定义 API 输入输出格式
│   │   └── routers.py             # 路由注册，自动生成 API 端点
│   └── dashboard/                 # 管理仪表盘应用：基于 Django 模板的前端界面
│       ├── views.py               # 页面视图，渲染链接列表、检索表单等
│       ├── templates/             # HTML 模板文件目录
│       └── static/                # CSS、JavaScript、图片等静态资源
├── tests/                         # 单元测试与集成测试用例目录
│   ├── test_models.py             # 数据模型单元测试
│   ├── test_services.py           # 业务逻辑单元测试
│   └── test_api.py                # API 端点集成测试
├── scripts/                       # 运维与辅助脚本目录
│   ├── import_batch.py            # 批量导入脚本，支持从 CSV 或文本文件读取链接
│   ├── check_links.py             # 链接可达性批量检测脚本，输出检测报告
│   └── export_json.py             # 导出为 JSON 格式的数据迁移脚本
├── docs/                          # 项目文档目录，包含 Markdown 格式的各类文档
│   ├── getting-started.md         # 入门指南
│   ├── user-manual.md             # 用户手册
│   ├── api-reference.md           # API 参考文档
│   └── operations.md              # 生产环境运维指南
├── logs/                          # 日志文件存储目录，按日期滚动切割
├── data/                          # 数据存储目录，包含 SQLite 数据库文件与导入缓存
└── .env.example                   # 环境变量配置模板，包含数据库连接串与密钥占位
```

## 贡献指南

提交 Issue 报告缺陷或功能请求：请在 GitHub Issues 页面新建 Issue，使用提供的模板填写复现步骤、运行环境、预期行为与实际行为，缺陷报告需附带最小可复现示例或相关日志片段。

Fork 仓库并创建功能分支：从主仓库 Fork 到个人账户后，基于 main 分支创建以 feature/ 或 fix/ 为前缀的功能分支，分支命名需简要描述变更内容，例如 feature/add-batch-export-json。

编写代码并遵循项目编码规范：Python 代码需符合 PEP 8 规范，使用 Black 格式化工具保持风格一致，所有新增函数与类需编写 docstring，核心逻辑需附带单元测试用例，测试覆盖率不低于百分之八十。

提交 Pull Request 并进行代码审查：推送分支到个人 Fork 仓库后，向主仓库的 main 分支发起 Pull Request，PR 描述需清晰说明变更目的、实现方案与测试结果，至少需要一位项目维护者审核通过后方可合并。

更新文档与变更日志：涉及用户可见的功能变更或配置调整时，需同步更新 docs/ 目录下对应的文档文件，并在 CHANGELOG.md 中记录变更条目，条目格式需遵循 Keep a Changelog 规范。

## 常见问题

Q: 导入大量链接时页面出现超时或卡顿，应该如何优化？

A: 链接导入操作建议使用命令行脚本 scripts/import_batch.py 进行，该脚本会分批处理链接并输出进度日志，避免 Web 请求超时限制。如果链接数量超过一万条，可以调整脚本中的 BATCH_SIZE 参数降低单次数据库写入压力，同时建议将 SQLite 数据库切换为 PostgreSQL 以获得更好的并发写入性能。

Q: 链接状态检测显示大量链接为失效状态，但手动访问浏览器中可正常打开，是什么原因？

A: 链接状态检测模块默认使用 requests 库发送 HEAD 请求并设置超时时间为 5 秒。部分新闻网站可能对 HEAD 请求返回 405 或 403 状态码，但实际 GET 请求可正常访问。可以在检测配置中将请求方法改为 GET 并禁用重定向跟随，同时检查检测时是否配置了正确的 User-Agent 头。若网站有反爬机制，建议调整检测间隔时间并配置代理池。

Q: 检索结果中能否同时展示链接的标题或摘要内容？

A: NewsIndexer 默认只存储 URL 与用户自定义标签，不主动抓取页面标题或摘要。如需在检索结果中展示标题信息，可以通过二次开发在导入流程中调用第三方元数据提取服务，将提取到的标题存入扩展字段中。项目提供的 API 接口支持扩展字段的读写，具体实现可参考 docs/api-reference.md 中的自定义字段章节。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:51
