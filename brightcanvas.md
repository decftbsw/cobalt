# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研、信息聚合与批量外链管理的静态导航站点生成框架。项目定位于为开发者、技术写作者、信息整理从业者提供一套结构清晰、可扩展性强的 URL 索引管理方案，能够将大批量异构链接以目录树与标签系统进行归类和展示。目标用户包括开源文档维护者、技术社区运营人员、以及需要定期梳理大量参考链接的研究人员。项目核心解决的是海量外链缺乏元数据管理、展示层级混乱、以及无法快速定位有效资源的问题，通过约定式目录结构与自动化索引生成，将原始 URL 列表转化为可浏览、可检索、可维护的静态站点。

## 功能概览

批量链接导入与自动清洗 系统提供基于文本列表的批量导入接口，自动识别并清洗 URL 中的冗余参数，保留原始路径与查询字符串，确保链接完整可用。

多层级目录索引生成 根据 URL 来源域名与路径结构，自动构建二级与三级目录树，将同源或同主题链接聚合在同一视图下，便于批量浏览。

静态站点渲染引擎 内置基于 Markdown 模板的渲染管线，将目录树与链接列表输出为 HTML 静态页面，无需后端服务即可部署至任何 Web 服务器。

标签系统与全文检索 支持对每条链接附加自定义标签，并提供基于标题与 URL 片段的轻量级全文检索功能，提升大型资源库的查找效率。

链接可用性定时检测 集成定时任务模块，周期性对已收录链接进行 HTTP 状态码检测，标记失效链接并生成报告，辅助维护者清理或更新资源。

导入导出兼容多种格式 除纯文本列表外，支持 CSV 与 JSON 格式的链接数据导入导出，便于与其他数据管理工具或脚本进行交互。

访问统计与热度排序 记录每个链接的点击次数，提供按访问热度排序的视图，帮助识别高价值资源与冷门内容。

## 应用场景

技术文档团队维护外部参考链接库 技术文档撰写过程中需要引用大量外部规范、标准与博文。WebIndex 允许团队将分散的参考链接统一录入，自动生成带分类导航的参考页面，嵌入文档站点或 Wiki 中，方便读者查阅原始出处。

开源项目 README 资源汇总页管理 开源项目通常需要维护社区资源列表、插件索引或相关项目导航。WebIndex 可将大批量链接转化为结构化的资源导航页，替代冗长的无序列表，提升 README 或项目官网的信息密度与可读性。

个人知识库外链归档与回溯 研究员或博客作者在浏览过程中积累大量待读或待引用链接。通过 WebIndex 的批量导入与标签功能，可以快速建立个人外链档案馆，并按主题或时间维度进行检索与回溯，避免链接丢失或遗忘。

社区活动或课程资料汇总 技术社区或培训机构在举办线上活动或开设课程时，需要向参与者提供大量参考材料链接。WebIndex 可快速生成活动专属导航页，支持按日程或模块分类，参与者无需在聊天记录中翻找链接。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex-core.git

# 进入项目目录
cd webindex-core

# 安装依赖（基于 Node.js 22 LTS）
npm install

# 将原始 URL 列表放入 data/raw_links.txt，每行一个 URL
# 然后执行构建命令
npm run build

# 启动开发服务器，预览生成的站点
npm run serve
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 22.x LTS 或更高 | 运行时环境与包管理基础 |
| npm | 10.x 或更高 | 依赖安装与脚本执行 |
| SQLite3 | 3.40.0 或更高 | 本地元数据存储与检索索引 |
| Python | 3.10 或更高（可选） | 仅用于链接可用性检测脚本的扩展支持 |
| Git | 2.30 或更高 | 版本控制与克隆操作 |
| 磁盘空间 | 至少 200 MB | 用于存储源码、数据库与生成的静态文件 |
| 内存 | 建议 512 MB 以上 | 构建大型索引（超过 5000 条链接）时的性能保障 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速安装、配置第一条数据源并生成首个站点 |
| 数据格式规范 | docs/data-format.md | 原始链接列表的格式要求、字段含义与示例说明 |
| 目录树配置 | docs/directory-config.md | 如何自定义分类规则、路径映射与排序策略 |
| 部署与运维 | docs/deployment.md | 静态站点构建后的部署方式、环境变量与性能调优 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/27491.htm
- http://m.blog.ghtkgg.cn/nnews/8637.htm
- http://m.blog.ghtkgg.cn/nnews/35420.htm
- http://m.blog.ghtkgg.cn/nnews/0829680.htm
- http://m.blog.ghtkgg.cn/nnews/5514.htm
- http://m.blog.ghtkgg.cn/nnews/6336837.htm
- http://m.blog.ghtkgg.cn/nnews/273568.htm
- http://m.blog.ghtkgg.cn/nnews/7836.htm
- http://m.blog.ghtkgg.cn/nnews/7637014.htm
- http://m.blog.ghtkgg.cn/nnews/7964.htm
- http://m.blog.ghtkgg.cn/nnews/8721.htm
- http://m.blog.ghtkgg.cn/nnews/328400.htm
- http://m.blog.ghtkgg.cn/nnews/1864575.htm
- http://m.blog.ghtkgg.cn/nnews/83826.htm
- http://m.blog.ghtkgg.cn/nnews/49527.htm
- http://m.blog.ghtkgg.cn/nnews/8639245.htm
- http://m.blog.ghtkgg.cn/nnews/346832.htm
- http://m.blog.ghtkgg.cn/nnews/42486.htm
- http://m.blog.ghtkgg.cn/nnews/8066307.htm
- http://m.blog.ghtkgg.cn/nnews/2558781.htm
- http://m.blog.ghtkgg.cn/nnews/82961.htm
- http://m.blog.ghtkgg.cn/nnews/46240.htm
- http://m.blog.ghtkgg.cn/nnews/579318.htm
- http://m.blog.ghtkgg.cn/nnews/471514.htm
- http://m.blog.ghtkgg.cn/nnews/8353.htm
- http://m.blog.ghtkgg.cn/nnews/739764.htm
- http://m.blog.ghtkgg.cn/nnews/0267.htm
- http://m.blog.ghtkgg.cn/nnews/184660.htm
- http://m.blog.ghtkgg.cn/nnews/419198.htm
- http://m.blog.ghtkgg.cn/nnews/8358061.htm
- http://m.blog.ghtkgg.cn/nnews/81124.htm
- http://m.blog.ghtkgg.cn/nnews/1292608.htm
- http://m.blog.ghtkgg.cn/nnews/822738.htm
- http://m.blog.ghtkgg.cn/nnews/6345.htm
- http://m.blog.ghtkgg.cn/nnews/2855333.htm
- http://m.blog.ghtkgg.cn/nnews/7367975.htm
- http://m.blog.ghtkgg.cn/nnews/47536.htm
- http://m.blog.ghtkgg.cn/nnews/8165654.htm
- http://m.blog.ghtkgg.cn/nnews/68076.htm
- http://m.blog.ghtkgg.cn/nnews/8765413.htm
- http://m.blog.ghtkgg.cn/nnews/545940.htm
- http://m.blog.ghtkgg.cn/nnews/595819.htm
- http://m.blog.ghtkgg.cn/nnews/147202.htm
- http://m.blog.ghtkgg.cn/nnews/7838803.htm
- http://m.blog.ghtkgg.cn/nnews/0697319.htm
- http://m.blog.ghtkgg.cn/nnews/731993.htm
- http://m.blog.ghtkgg.cn/nnews/1399.htm
- http://m.blog.ghtkgg.cn/nnews/229815.htm
- http://m.blog.ghtkgg.cn/nnews/39493.htm
- http://m.blog.ghtkgg.cn/nnews/0054.htm
- http://m.blog.ghtkgg.cn/nnews/9723217.htm
- http://m.blog.ghtkgg.cn/nnews/4540128.htm
- http://m.blog.ghtkgg.cn/nnews/9538243.htm
- http://m.blog.ghtkgg.cn/nnews/1963983.htm
- http://m.blog.ghtkgg.cn/nnews/45911.htm
- http://m.blog.ghtkgg.cn/nnews/4405.htm
- http://m.blog.ghtkgg.cn/nnews/485255.htm
- http://m.blog.ghtkgg.cn/nnews/5066730.htm
- http://m.blog.ghtkgg.cn/nnews/96572.htm
- http://m.blog.ghtkgg.cn/nnews/9693.htm
- http://m.blog.ghtkgg.cn/nnews/671748.htm
- http://m.blog.ghtkgg.cn/nnews/293374.htm
- http://m.blog.ghtkgg.cn/nnews/4676929.htm
- http://m.blog.ghtkgg.cn/nnews/3476.htm
- http://m.blog.ghtkgg.cn/nnews/7015544.htm
- http://m.blog.ghtkgg.cn/nnews/731537.htm
- http://m.blog.ghtkgg.cn/nnews/07829.htm
- http://m.blog.ghtkgg.cn/nnews/5902.htm
- http://m.blog.ghtkgg.cn/nnews/0528054.htm
- http://m.blog.ghtkgg.cn/nnews/987194.htm
- http://m.blog.ghtkgg.cn/nnews/6893.htm
- http://m.blog.ghtkgg.cn/nnews/9905343.htm
- http://m.blog.ghtkgg.cn/nnews/2479749.htm
- http://m.blog.ghtkgg.cn/nnews/3982028.htm
- http://m.blog.ghtkgg.cn/nnews/5263827.htm
- http://m.blog.ghtkgg.cn/nnews/013735.htm
- http://m.blog.ghtkgg.cn/nnews/97821.htm
- http://m.blog.ghtkgg.cn/nnews/3148538.htm
- http://m.blog.ghtkgg.cn/nnews/73544.htm
- http://m.blog.ghtkgg.cn/nnews/159247.htm
- http://m.blog.ghtkgg.cn/nnews/12054.htm
- http://m.blog.ghtkgg.cn/nnews/78539.htm
- http://m.blog.ghtkgg.cn/nnews/98775.htm
- http://m.blog.ghtkgg.cn/nnews/2169.htm
- http://m.blog.ghtkgg.cn/nnews/610219.htm
- http://m.blog.ghtkgg.cn/nnews/497052.htm
- http://m.blog.ghtkgg.cn/nnews/22265.htm
- http://m.blog.ghtkgg.cn/nnews/51978.htm
- http://m.blog.ghtkgg.cn/nnews/146450.htm
- http://m.blog.ghtkgg.cn/nnews/850664.htm
- http://m.blog.ghtkgg.cn/nnews/5796543.htm
- http://m.blog.ghtkgg.cn/nnews/5986881.htm
- http://m.blog.ghtkgg.cn/nnews/6683.htm
- http://m.blog.ghtkgg.cn/nnews/854489.htm
- http://m.blog.ghtkgg.cn/nnews/14445.htm
- http://m.blog.ghtkgg.cn/nnews/072500.htm
- http://m.blog.ghtkgg.cn/nnews/990245.htm
- http://m.blog.ghtkgg.cn/nnews/391027.htm
- http://m.blog.ghtkgg.cn/nnews/3543.htm
- http://m.blog.ghtkgg.cn/nnews/3357329.htm
- http://m.blog.ghtkgg.cn/nnews/3047629.htm
- http://m.blog.ghtkgg.cn/nnews/468915.htm
- http://m.blog.ghtkgg.cn/nnews/3815832.htm
- http://m.blog.ghtkgg.cn/nnews/463415.htm
- http://m.blog.ghtkgg.cn/nnews/76119.htm
- http://m.blog.ghtkgg.cn/nnews/016551.htm
- http://m.blog.ghtkgg.cn/nnews/826633.htm
- http://m.blog.ghtkgg.cn/nnews/122680.htm
- http://m.blog.ghtkgg.cn/nnews/740627.htm
- http://m.blog.ghtkgg.cn/nnews/991247.htm
- http://m.blog.ghtkgg.cn/nnews/2869530.htm
- http://m.blog.ghtkgg.cn/nnews/4249.htm
- http://m.blog.ghtkgg.cn/nnews/405994.htm
- http://m.blog.ghtkgg.cn/nnews/783236.htm
- http://m.blog.ghtkgg.cn/nnews/713467.htm
- http://m.blog.ghtkgg.cn/nnews/961862.htm
- http://m.blog.ghtkgg.cn/nnews/2543949.htm
- http://m.blog.ghtkgg.cn/nnews/213755.htm
- http://m.blog.ghtkgg.cn/nnews/52498.htm
- http://m.blog.ghtkgg.cn/nnews/2717.htm
- http://m.blog.ghtkgg.cn/nnews/7136455.htm
- http://m.blog.ghtkgg.cn/nnews/2411233.htm
- http://m.blog.ghtkgg.cn/nnews/47184.htm
- http://m.blog.ghtkgg.cn/nnews/56782.htm
- http://m.blog.ghtkgg.cn/nnews/17256.htm
- http://m.blog.ghtkgg.cn/nnews/537133.htm
- http://m.blog.ghtkgg.cn/nnews/5581332.htm
- http://m.blog.ghtkgg.cn/nnews/0921141.htm
- http://m.blog.ghtkgg.cn/nnews/0769722.htm
- http://m.blog.ghtkgg.cn/nnews/47883.htm
- http://m.blog.ghtkgg.cn/nnews/019623.htm
- http://m.blog.ghtkgg.cn/nnews/2081273.htm
- http://m.blog.ghtkgg.cn/nnews/951899.htm
- http://m.blog.ghtkgg.cn/nnews/8222862.htm
- http://m.blog.ghtkgg.cn/nnews/6728.htm
- http://m.blog.ghtkgg.cn/nnews/10735.htm
- http://m.blog.ghtkgg.cn/nnews/00928.htm
- http://m.blog.ghtkgg.cn/nnews/85233.htm
- http://m.blog.ghtkgg.cn/nnews/50034.htm
- http://m.blog.ghtkgg.cn/nnews/2405890.htm
- http://m.blog.ghtkgg.cn/nnews/09246.htm
- http://m.blog.ghtkgg.cn/nnews/7512630.htm
- http://m.blog.ghtkgg.cn/nnews/81291.htm
- http://m.blog.ghtkgg.cn/nnews/993134.htm
- http://m.blog.ghtkgg.cn/nnews/9482178.htm
- http://m.blog.ghtkgg.cn/nnews/84256.htm
- http://m.blog.ghtkgg.cn/nnews/4477571.htm
- http://m.blog.ghtkgg.cn/nnews/245459.htm
- http://m.blog.ghtkgg.cn/nnews/9840.htm
- http://m.blog.ghtkgg.cn/nnews/6611991.htm
- http://m.blog.ghtkgg.cn/nnews/2837.htm
- http://m.blog.ghtkgg.cn/nnews/8392808.htm
- http://m.blog.ghtkgg.cn/nnews/421041.htm
- http://m.blog.ghtkgg.cn/nnews/2065715.htm
- http://m.blog.ghtkgg.cn/nnews/34283.htm
- http://m.blog.ghtkgg.cn/nnews/7344238.htm
- http://m.blog.ghtkgg.cn/nnews/1314.htm
- http://m.blog.ghtkgg.cn/nnews/58520.htm
- http://m.blog.ghtkgg.cn/nnews/33033.htm
- http://m.blog.ghtkgg.cn/nnews/98499.htm
- http://m.blog.ghtkgg.cn/nnews/373298.htm
- http://m.blog.ghtkgg.cn/nnews/0830.htm
- http://m.blog.ghtkgg.cn/nnews/3292.htm
- http://m.blog.ghtkgg.cn/nnews/06320.htm
- http://m.blog.ghtkgg.cn/nnews/2114729.htm
- http://m.blog.ghtkgg.cn/nnews/77313.htm
- http://m.blog.ghtkgg.cn/nnews/9641.htm
- http://m.blog.ghtkgg.cn/nnews/75967.htm
- http://m.blog.ghtkgg.cn/nnews/88383.htm
- http://m.blog.ghtkgg.cn/nnews/623172.htm
- http://m.blog.ghtkgg.cn/nnews/6418490.htm
- http://m.blog.ghtkgg.cn/nnews/624169.htm
- http://m.blog.ghtkgg.cn/nnews/980941.htm
- http://m.blog.ghtkgg.cn/nnews/26182.htm
- http://m.blog.ghtkgg.cn/nnews/43085.htm
- http://m.blog.ghtkgg.cn/nnews/3801.htm
- http://m.blog.ghtkgg.cn/nnews/4829.htm
- http://m.blog.ghtkgg.cn/nnews/648397.htm
- http://m.blog.ghtkgg.cn/nnews/791484.htm
- http://m.blog.ghtkgg.cn/nnews/110644.htm
- http://m.blog.ghtkgg.cn/nnews/194063.htm
- http://m.blog.ghtkgg.cn/nnews/9472.htm
- http://m.blog.ghtkgg.cn/nnews/758083.htm
- http://m.blog.ghtkgg.cn/nnews/364932.htm
- http://m.blog.ghtkgg.cn/nnews/8161.htm
- http://m.blog.ghtkgg.cn/nnews/253664.htm
- http://m.blog.ghtkgg.cn/nnews/6687.htm
- http://m.blog.ghtkgg.cn/nnews/500582.htm
- http://m.blog.ghtkgg.cn/nnews/35568.htm
- http://m.blog.ghtkgg.cn/nnews/33646.htm
- http://m.blog.ghtkgg.cn/nnews/2761733.htm
- http://m.blog.ghtkgg.cn/nnews/751223.htm
- http://m.blog.ghtkgg.cn/nnews/3298090.htm
- http://m.blog.ghtkgg.cn/nnews/9545.htm
- http://m.blog.ghtkgg.cn/nnews/142436.htm
- http://m.blog.ghtkgg.cn/nnews/515260.htm
- http://m.blog.ghtkgg.cn/nnews/333208.htm
- http://m.blog.ghtkgg.cn/nnews/3888.htm
- http://m.blog.ghtkgg.cn/nnews/7839761.htm
- http://m.blog.ghtkgg.cn/nnews/4416.htm
- http://m.blog.ghtkgg.cn/nnews/7671645.htm
- http://m.blog.ghtkgg.cn/nnews/406807.htm
- http://m.blog.ghtkgg.cn/nnews/5553.htm
- http://m.blog.ghtkgg.cn/nnews/116434.htm
- http://m.blog.ghtkgg.cn/nnews/494689.htm
- http://m.blog.ghtkgg.cn/nnews/8027543.htm
- http://m.blog.ghtkgg.cn/nnews/513902.htm
- http://m.blog.ghtkgg.cn/nnews/189398.htm
- http://m.blog.ghtkgg.cn/nnews/9773983.htm
- http://m.blog.ghtkgg.cn/nnews/2471716.htm
- http://m.blog.ghtkgg.cn/nnews/0236305.htm
- http://m.blog.ghtkgg.cn/nnews/2955.htm
- http://m.blog.ghtkgg.cn/nnews/36373.htm
- http://m.blog.ghtkgg.cn/nnews/178906.htm
- http://m.blog.ghtkgg.cn/nnews/0147.htm
- http://m.blog.ghtkgg.cn/nnews/4071325.htm
- http://m.blog.ghtkgg.cn/nnews/4107.htm
- http://m.blog.ghtkgg.cn/nnews/6934.htm
- http://m.blog.ghtkgg.cn/nnews/042505.htm
- http://m.blog.ghtkgg.cn/nnews/1196796.htm
- http://m.blog.ghtkgg.cn/nnews/3109.htm
- http://m.blog.ghtkgg.cn/nnews/225611.htm
- http://m.blog.ghtkgg.cn/nnews/901697.htm
- http://m.blog.ghtkgg.cn/nnews/80865.htm
- http://m.blog.ghtkgg.cn/nnews/061750.htm
- http://m.blog.ghtkgg.cn/nnews/657613.htm
- http://m.blog.ghtkgg.cn/nnews/240196.htm
- http://m.blog.ghtkgg.cn/nnews/3280694.htm
- http://m.blog.ghtkgg.cn/nnews/905067.htm
- http://m.blog.ghtkgg.cn/nnews/568996.htm
- http://m.blog.ghtkgg.cn/nnews/47894.htm
- http://m.blog.ghtkgg.cn/nnews/5283430.htm
- http://m.blog.ghtkgg.cn/nnews/44606.htm
- http://m.blog.ghtkgg.cn/nnews/581390.htm
- http://m.blog.ghtkgg.cn/nnews/9603157.htm
- http://m.blog.ghtkgg.cn/nnews/92737.htm
- http://m.blog.ghtkgg.cn/nnews/955575.htm
- http://m.blog.ghtkgg.cn/nnews/924460.htm
- http://m.blog.ghtkgg.cn/nnews/7919.htm
- http://m.blog.ghtkgg.cn/nnews/2797588.htm
- http://m.blog.ghtkgg.cn/nnews/224738.htm
- http://m.blog.ghtkgg.cn/nnews/654058.htm
- http://m.blog.ghtkgg.cn/nnews/53816.htm
- http://m.blog.ghtkgg.cn/nnews/6798.htm
- http://m.blog.ghtkgg.cn/nnews/9569474.htm
- http://m.blog.ghtkgg.cn/nnews/279969.htm
- http://m.blog.ghtkgg.cn/nnews/689402.htm
- http://m.blog.ghtkgg.cn/nnews/5917062.htm
- http://m.blog.ghtkgg.cn/nnews/6371.htm
- http://m.blog.ghtkgg.cn/nnews/70582.htm
- http://m.blog.ghtkgg.cn/nnews/223620.htm
- http://m.blog.ghtkgg.cn/nnews/849332.htm
- http://m.blog.ghtkgg.cn/nnews/566187.htm
- http://m.blog.ghtkgg.cn/nnews/0365.htm
- http://m.blog.ghtkgg.cn/nnews/0913.htm
- http://m.blog.ghtkgg.cn/nnews/165792.htm
- http://m.blog.ghtkgg.cn/nnews/875141.htm
- http://m.blog.ghtkgg.cn/nnews/781013.htm
- http://m.blog.ghtkgg.cn/nnews/3165.htm
- http://m.blog.ghtkgg.cn/nnews/421083.htm
- http://m.blog.ghtkgg.cn/nnews/3399858.htm
- http://m.blog.ghtkgg.cn/nnews/982984.htm
- http://m.blog.ghtkgg.cn/nnews/7895.htm
- http://m.blog.ghtkgg.cn/nnews/410386.htm
- http://m.blog.ghtkgg.cn/nnews/619982.htm
- http://m.blog.ghtkgg.cn/nnews/52525.htm
- http://m.blog.ghtkgg.cn/nnews/87824.htm
- http://m.blog.ghtkgg.cn/nnews/46729.htm
- http://m.blog.ghtkgg.cn/nnews/852242.htm
- http://m.blog.ghtkgg.cn/nnews/6338756.htm
- http://m.blog.ghtkgg.cn/nnews/6654673.htm
- http://m.blog.ghtkgg.cn/nnews/99263.htm
- http://m.blog.ghtkgg.cn/nnews/774660.htm
- http://m.blog.ghtkgg.cn/nnews/6840428.htm
- http://m.blog.ghtkgg.cn/nnews/9906.htm
- http://m.blog.ghtkgg.cn/nnews/5396139.htm
- http://m.blog.ghtkgg.cn/nnews/9088689.htm
- http://m.blog.ghtkgg.cn/nnews/4176705.htm
- http://m.blog.ghtkgg.cn/nnews/699699.htm
- http://m.blog.ghtkgg.cn/nnews/4939920.htm
- http://m.blog.ghtkgg.cn/nnews/069604.htm
- http://m.blog.ghtkgg.cn/nnews/5602.htm
- http://m.blog.ghtkgg.cn/nnews/3106033.htm
- http://m.blog.ghtkgg.cn/nnews/320926.htm
- http://m.blog.ghtkgg.cn/nnews/02524.htm
- http://m.blog.ghtkgg.cn/nnews/8784130.htm
- http://m.blog.ghtkgg.cn/nnews/6102239.htm
- http://m.blog.ghtkgg.cn/nnews/3963.htm
- http://m.blog.ghtkgg.cn/nnews/8548626.htm
- http://m.blog.ghtkgg.cn/nnews/815082.htm
- http://m.blog.ghtkgg.cn/nnews/69246.htm
- http://m.blog.ghtkgg.cn/nnews/75011.htm
- http://m.blog.ghtkgg.cn/nnews/623861.htm
- http://m.blog.ghtkgg.cn/nnews/19168.htm
- http://m.blog.ghtkgg.cn/nnews/34615.htm
- http://m.blog.ghtkgg.cn/nnews/097510.htm
- http://m.blog.ghtkgg.cn/nnews/9199.htm
- http://m.blog.ghtkgg.cn/nnews/115477.htm
- http://m.blog.ghtkgg.cn/nnews/58653.htm
- http://m.blog.ghtkgg.cn/nnews/514780.htm

## 项目结构

```
webindex-core/
├── src/                           # 核心源代码目录
│   ├── core/                      # 索引引擎与数据清洗模块
│   │   ├── importer.js            # 批量链接导入与清洗逻辑
│   │   └── indexer.js             # 目录树构建与索引生成
│   ├── render/                    # 静态渲染引擎
│   │   ├── html-render.js         # Markdown 转 HTML 模板渲染
│   │   └── asset-pipeline.js      # CSS / JS 资源打包与指纹化
│   ├── server/                    # 开发服务器与热重载
│   │   ├── dev-server.js          # 基于 Express 的本地预览服务
│   │   └── watcher.js             # 文件变更监听与增量构建
│   ├── scheduler/                 # 定时任务与后台检测
│   │   ├── link-checker.js        # 链接可用性 HTTP 状态检测
│   │   └── reporter.js            # 失效链接报告生成
│   └── utils/                     # 通用工具函数库
│       ├── url-helper.js          # URL 解析、规范化与比较
│       └── logger.js              # 多级别日志输出
├── templates/                     # 页面模板与主题样式
│   ├── layouts/                   # 基础布局模板（EJS）
│   │   ├── default.ejs            # 默认页面骨架
│   │   └── navigation.ejs         # 导航栏与侧边栏组件
│   └── static/                    # 静态资源源文件
│       ├── css/                   # 基础样式与响应式设计
│       └── js/                    # 检索交互与统计脚本
├── data/                          # 数据存储目录
│   ├── raw_links.txt              # 用户原始链接列表（输入）
│   ├── metadata.db                # SQLite 索引数据库
│   └── tags.json                  # 用户自定义标签映射
├── docs/                          # 完整文档
│   ├── getting-started.md         # 入门指南
│   ├── data-format.md             # 数据格式规范
│   ├── directory-config.md        # 目录树配置说明
│   └── deployment.md              # 部署与运维手册
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 核心模块单元测试
│   └── fixtures/                  # 测试用固定数据集
├── dist/                          # 构建输出目录（生成的静态站点）
│   ├── index.html                 # 站点首页
│   └── assets/                    # 打包后的 CSS/JS 资源
├── config/                        # 配置文件目录
│   ├── site.config.js             # 站点名称、描述与主题配置
│   └── scheduler.config.js        # 定时检测间隔与通知策略
├── scripts/                       # 辅助脚本
│   ├── build.sh                   # 生产环境构建脚本
│   └── clean.sh                   # 清理缓存与构建产物
├── package.json                   # npm 依赖与脚本定义
├── README.md                      # 项目说明文档（本文件）
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

首先，请阅读项目行为准则并在提交前运行完整的测试套件。所有新功能与修复需附带对应的单元测试用例。

提交合并请求前，请确保代码通过 ESLint 规则检查，并且提交信息遵循 Conventional Commits 格式，以便自动生成变更日志。

若需新增解析器或渲染扩展，请在 src/core 下创建独立模块，并在 index.js 中注册。同时更新 docs 目录下的对应文档，说明新模块的配置方式。

对于链接检测模块的改进，请提供测试用的示例 URL 列表与预期状态码，验证检测准确率不低于 99%。

## 常见问题

问：导入的 URL 列表包含大量重复项，系统如何处理？

答：系统在导入阶段会自动对 URL 进行规范化处理（去除尾部斜杠、统一协议小写等），然后基于规范化后的字符串进行去重。重复项会被记录在导入日志中，但仅保留首次出现的条目。如需强制覆盖，可在配置文件中设置 dedupe: false。

问：生成的静态站点能否部署到 GitHub Pages 或 Nginx？

答：可以。dist 目录输出的全部为纯静态文件，无需任何后端服务。将 dist 内容推送到 GitHub Pages 分支，或直接复制到 Nginx 的 root 目录下即可正常访问。站点内部所有链接均为相对路径，支持部署在子目录下。

问：如何自定义分类目录的排序规则，而非按字母顺序？

答：在 config/site.config.js 中，可以配置 sortOrder 字段，支持按创建时间、点击热度或手动指定优先级的权重数组进行排序。若需要完全自定义顺序，可以在 data/tags.json 中为每个分类指定 order 数值，构建时优先读取该数值。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
