# WebLink Navigator

WebLink Navigator 是一个面向技术文档聚合与外部资源导航的开源工具集，专为需要批量管理、分类展示和快速检索大量外链资源的开发团队与内容创作者设计。该项目以静态站点生成器为核心，将结构化的链接数据转换为可浏览、可搜索、可定制的导航页面，适用于技术博客、项目文档站、知识库以及个人书签管理场景。

项目定位为轻量级的外链治理中间件，不依赖数据库，不涉及后端服务，所有数据以 Markdown 和 YAML 格式存储，通过构建流程产出纯静态 HTML。目标用户包括开源维护者、技术写作者、社区运营人员以及需要维护大量外部引用资源的研发团队。WebLink Navigator 解决了外链分散、格式不统一、检索困难、失效链接难以追踪等实际问题，提供一套从数据录入到页面渲染的完整工作流。

## 功能概览

**批量链接导入与校验** 支持从 CSV、JSON 和 YAML 文件批量导入链接数据，自动校验 URL 格式合法性，检测重复条目并生成导入报告。

**多维度分类与标签系统** 每条链接可归属多个分类并附加任意数量的标签，支持层级分类结构，便于构建精细化的导航体系。

**全文检索与过滤** 内置基于 Lunr.js 的离线全文检索引擎，支持按标题、描述、标签、分类进行组合过滤，检索结果实时高亮显示。

**自定义元数据扩展** 每条链接可附加自定义元数据字段，如作者、发布日期、所属批次、重要性评分等，满足不同场景下的个性化展示需求。

**链接状态监测** 集成链接可用性检查功能，可配置定时任务对已收录链接进行 HTTP 状态码探测，标记失效链接并生成告警通知。

**主题与布局切换** 提供多套响应式界面主题，支持列表视图与卡片视图切换，用户可根据偏好调整页面布局和配色方案。

**数据导出与备份** 支持将全部链接数据导出为 JSON、CSV 或 SQLite 格式，便于迁移、备份或与其他系统集成。

## 应用场景

技术文档站点的外链统一管理。技术博客或开源项目文档中通常包含大量外部参考链接，分散在不同章节中难以维护。使用 WebLink Navigator 可集中管理这些链接，通过分类和标签让读者快速定位相关资源，同时利用状态监测功能及时发现失效引用。

团队知识库的资源聚合。研发团队内部的知识库常常需要汇集各类技术规范、设计文档、工具官网、学习资料等外部资源。WebLink Navigator 可作为知识库的补充模块，提供独立的导航页面，让团队成员高效获取所需信息。

社区资源导航站的快速构建。开源社区或技术社群运营者需要定期发布资源汇总贴或导航站点。WebLink Navigator 的批量导入和静态生成能力使得从原始数据到上线页面可以在数分钟内完成，支持按月或按批次更新内容。

个人书签与阅读列表的管理。开发者个人积累的大量技术书签、论文链接、教程地址等可通过 WebLink Navigator 进行结构化整理，配合全文检索功能实现比浏览器原生书签更高效的检索体验。

## 快速开始

以下命令序列指导您在本地环境完成项目的克隆、依赖安装与服务启动。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run build
npm start
```

执行完成后，访问控制台输出的本地地址（默认为 http://localhost:3000）即可进入管理界面。首次启动会自动生成示例数据，您可以通过管理面板的导入功能将自定义链接数据添加至系统。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 9.x 或更高 | 包管理器，随 Node.js 一同安装 |
| Git | 2.30 或更高 | 用于克隆仓库及版本控制 |
| Python | 3.9 或更高（可选） | 仅在启用链接状态监测的异步 HTTP 探测功能时需要 |
| SQLite | 3.35 或更高（可选） | 若选择 SQLite 作为数据持久化后端则需要 |
| Nginx 或 Apache | 任意现代版本（生产部署） | 用于托管构建产出的静态文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/getting-started.md | 如何安装、配置和首次运行项目；管理界面各功能模块的使用方法 |
| 开发者文档 | /docs/developer/architecture.md | 项目的整体架构设计、核心模块职责、数据流转路径及扩展点说明 |
| 数据规范 | /docs/schema/link-specification.md | 链接数据结构的完整字段定义、合法取值约束、自定义元数据的扩展规则 |
| 运维手册 | /docs/operations/deployment.md | 生产环境部署方案、性能调优参数、日志管理与监控告警配置 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/2596.htm
- http://m.wap.ghtkgg.cn/jnews/635167.htm
- http://m.wap.ghtkgg.cn/jnews/92133.htm
- http://m.wap.ghtkgg.cn/jnews/0436546.htm
- http://m.wap.ghtkgg.cn/jnews/60566.htm
- http://m.wap.ghtkgg.cn/jnews/875814.htm
- http://m.wap.ghtkgg.cn/jnews/91699.htm
- http://m.wap.ghtkgg.cn/jnews/652508.htm
- http://m.wap.ghtkgg.cn/jnews/326480.htm
- http://m.wap.ghtkgg.cn/jnews/434260.htm
- http://m.wap.ghtkgg.cn/jnews/5391.htm
- http://m.wap.ghtkgg.cn/jnews/0346928.htm
- http://m.wap.ghtkgg.cn/jnews/9004380.htm
- http://m.wap.ghtkgg.cn/jnews/7514217.htm
- http://m.wap.ghtkgg.cn/jnews/34183.htm
- http://m.wap.ghtkgg.cn/jnews/0355839.htm
- http://m.wap.ghtkgg.cn/jnews/484616.htm
- http://m.wap.ghtkgg.cn/jnews/77887.htm
- http://m.wap.ghtkgg.cn/jnews/1169428.htm
- http://m.wap.ghtkgg.cn/jnews/4290585.htm
- http://m.wap.ghtkgg.cn/jnews/6254.htm
- http://m.wap.ghtkgg.cn/jnews/0576637.htm
- http://m.wap.ghtkgg.cn/jnews/5696.htm
- http://m.wap.ghtkgg.cn/jnews/55466.htm
- http://m.wap.ghtkgg.cn/jnews/0346.htm
- http://m.wap.ghtkgg.cn/jnews/6286529.htm
- http://m.wap.ghtkgg.cn/jnews/3939762.htm
- http://m.wap.ghtkgg.cn/jnews/41492.htm
- http://m.wap.ghtkgg.cn/jnews/71804.htm
- http://m.wap.ghtkgg.cn/jnews/792164.htm
- http://m.wap.ghtkgg.cn/jnews/0620075.htm
- http://m.wap.ghtkgg.cn/jnews/8896.htm
- http://m.wap.ghtkgg.cn/jnews/471267.htm
- http://m.wap.ghtkgg.cn/jnews/554174.htm
- http://m.wap.ghtkgg.cn/jnews/1362554.htm
- http://m.wap.ghtkgg.cn/jnews/36971.htm
- http://m.wap.ghtkgg.cn/jnews/821214.htm
- http://m.wap.ghtkgg.cn/jnews/038308.htm
- http://m.wap.ghtkgg.cn/jnews/8561.htm
- http://m.wap.ghtkgg.cn/jnews/377733.htm
- http://m.wap.ghtkgg.cn/jnews/1867.htm
- http://m.wap.ghtkgg.cn/jnews/490845.htm
- http://m.wap.ghtkgg.cn/jnews/248856.htm
- http://m.wap.ghtkgg.cn/jnews/60339.htm
- http://m.wap.ghtkgg.cn/jnews/10513.htm
- http://m.wap.ghtkgg.cn/jnews/669795.htm
- http://m.wap.ghtkgg.cn/jnews/1729.htm
- http://m.wap.ghtkgg.cn/jnews/17801.htm
- http://m.wap.ghtkgg.cn/jnews/312266.htm
- http://m.wap.ghtkgg.cn/jnews/28987.htm
- http://m.wap.ghtkgg.cn/jnews/2981.htm
- http://m.wap.ghtkgg.cn/jnews/33708.htm
- http://m.wap.ghtkgg.cn/jnews/55239.htm
- http://m.wap.ghtkgg.cn/jnews/4390.htm
- http://m.wap.ghtkgg.cn/jnews/5110223.htm
- http://m.wap.ghtkgg.cn/jnews/17201.htm
- http://m.wap.ghtkgg.cn/jnews/8676053.htm
- http://m.wap.ghtkgg.cn/jnews/4579.htm
- http://m.wap.ghtkgg.cn/jnews/417861.htm
- http://m.wap.ghtkgg.cn/jnews/9097.htm
- http://m.wap.ghtkgg.cn/jnews/97974.htm
- http://m.wap.ghtkgg.cn/jnews/82080.htm
- http://m.wap.ghtkgg.cn/jnews/3607.htm
- http://m.wap.ghtkgg.cn/jnews/4538812.htm
- http://m.wap.ghtkgg.cn/jnews/6327.htm
- http://m.wap.ghtkgg.cn/jnews/23974.htm
- http://m.wap.ghtkgg.cn/jnews/053545.htm
- http://m.wap.ghtkgg.cn/jnews/1810.htm
- http://m.wap.ghtkgg.cn/jnews/598189.htm
- http://m.wap.ghtkgg.cn/jnews/3070494.htm
- http://m.wap.ghtkgg.cn/jnews/2969232.htm
- http://m.wap.ghtkgg.cn/jnews/8684839.htm
- http://m.wap.ghtkgg.cn/jnews/9107.htm
- http://m.wap.ghtkgg.cn/jnews/1868090.htm
- http://m.wap.ghtkgg.cn/jnews/1549362.htm
- http://m.wap.ghtkgg.cn/jnews/27590.htm
- http://m.wap.ghtkgg.cn/jnews/8066501.htm
- http://m.wap.ghtkgg.cn/jnews/762449.htm
- http://m.wap.ghtkgg.cn/jnews/0882931.htm
- http://m.wap.ghtkgg.cn/jnews/739792.htm
- http://m.wap.ghtkgg.cn/jnews/78245.htm
- http://m.wap.ghtkgg.cn/jnews/100477.htm
- http://m.wap.ghtkgg.cn/jnews/79187.htm
- http://m.wap.ghtkgg.cn/jnews/9391350.htm
- http://m.wap.ghtkgg.cn/jnews/182572.htm
- http://m.wap.ghtkgg.cn/jnews/27523.htm
- http://m.wap.ghtkgg.cn/jnews/1718.htm
- http://m.wap.ghtkgg.cn/jnews/1902239.htm
- http://m.wap.ghtkgg.cn/jnews/9604920.htm
- http://m.wap.ghtkgg.cn/jnews/401499.htm
- http://m.wap.ghtkgg.cn/jnews/8769236.htm
- http://m.wap.ghtkgg.cn/jnews/895257.htm
- http://m.wap.ghtkgg.cn/jnews/0931263.htm
- http://m.wap.ghtkgg.cn/jnews/5258955.htm
- http://m.wap.ghtkgg.cn/jnews/367650.htm
- http://m.wap.ghtkgg.cn/jnews/274447.htm
- http://m.wap.ghtkgg.cn/jnews/0113353.htm
- http://m.wap.ghtkgg.cn/jnews/0137539.htm
- http://m.wap.ghtkgg.cn/jnews/243698.htm
- http://m.wap.ghtkgg.cn/jnews/7945854.htm
- http://m.wap.ghtkgg.cn/jnews/507088.htm
- http://m.wap.ghtkgg.cn/jnews/55589.htm
- http://m.wap.ghtkgg.cn/jnews/4068.htm
- http://m.wap.ghtkgg.cn/jnews/88954.htm
- http://m.wap.ghtkgg.cn/jnews/726774.htm
- http://m.wap.ghtkgg.cn/jnews/845228.htm
- http://m.wap.ghtkgg.cn/jnews/1007.htm
- http://m.wap.ghtkgg.cn/jnews/7002919.htm
- http://m.wap.ghtkgg.cn/jnews/98732.htm
- http://m.wap.ghtkgg.cn/jnews/99165.htm
- http://m.wap.ghtkgg.cn/jnews/743095.htm
- http://m.wap.ghtkgg.cn/jnews/19714.htm
- http://m.wap.ghtkgg.cn/jnews/422036.htm
- http://m.wap.ghtkgg.cn/jnews/6467.htm
- http://m.wap.ghtkgg.cn/jnews/463608.htm
- http://m.wap.ghtkgg.cn/jnews/397883.htm
- http://m.wap.ghtkgg.cn/jnews/0306834.htm
- http://m.wap.ghtkgg.cn/jnews/6262164.htm
- http://m.wap.ghtkgg.cn/jnews/25651.htm
- http://m.wap.ghtkgg.cn/jnews/6311.htm
- http://m.wap.ghtkgg.cn/jnews/7943666.htm
- http://m.wap.ghtkgg.cn/jnews/034564.htm
- http://m.wap.ghtkgg.cn/jnews/0222.htm
- http://m.wap.ghtkgg.cn/jnews/486312.htm
- http://m.wap.ghtkgg.cn/jnews/6918.htm
- http://m.wap.ghtkgg.cn/jnews/309538.htm
- http://m.wap.ghtkgg.cn/jnews/6999360.htm
- http://m.wap.ghtkgg.cn/jnews/6002450.htm
- http://m.wap.ghtkgg.cn/jnews/4685254.htm
- http://m.wap.ghtkgg.cn/jnews/3484994.htm
- http://m.wap.ghtkgg.cn/jnews/7144481.htm
- http://m.wap.ghtkgg.cn/jnews/1930006.htm
- http://m.wap.ghtkgg.cn/jnews/6605732.htm
- http://m.wap.ghtkgg.cn/jnews/14039.htm
- http://m.wap.ghtkgg.cn/jnews/70845.htm
- http://m.wap.ghtkgg.cn/jnews/9913728.htm
- http://m.wap.ghtkgg.cn/jnews/26597.htm
- http://m.wap.ghtkgg.cn/jnews/014986.htm
- http://m.wap.ghtkgg.cn/jnews/117865.htm
- http://m.wap.ghtkgg.cn/jnews/4466023.htm
- http://m.wap.ghtkgg.cn/jnews/1095098.htm
- http://m.wap.ghtkgg.cn/jnews/5296250.htm
- http://m.wap.ghtkgg.cn/jnews/909183.htm
- http://m.wap.ghtkgg.cn/jnews/61855.htm
- http://m.wap.ghtkgg.cn/jnews/571803.htm
- http://m.wap.ghtkgg.cn/jnews/870977.htm
- http://m.wap.ghtkgg.cn/jnews/783064.htm
- http://m.wap.ghtkgg.cn/jnews/33666.htm
- http://m.wap.ghtkgg.cn/jnews/5941.htm
- http://m.wap.ghtkgg.cn/jnews/736259.htm
- http://m.wap.ghtkgg.cn/jnews/7264281.htm
- http://m.wap.ghtkgg.cn/jnews/25663.htm
- http://m.wap.ghtkgg.cn/jnews/50911.htm
- http://m.wap.ghtkgg.cn/jnews/1422139.htm
- http://m.wap.ghtkgg.cn/jnews/134184.htm
- http://m.wap.ghtkgg.cn/jnews/12498.htm
- http://m.wap.ghtkgg.cn/jnews/159332.htm
- http://m.wap.ghtkgg.cn/jnews/9362420.htm
- http://m.wap.ghtkgg.cn/jnews/5083198.htm
- http://m.wap.ghtkgg.cn/jnews/858045.htm
- http://m.wap.ghtkgg.cn/jnews/7147.htm
- http://m.wap.ghtkgg.cn/jnews/5279237.htm
- http://m.wap.ghtkgg.cn/jnews/838249.htm
- http://m.wap.ghtkgg.cn/jnews/76267.htm
- http://m.wap.ghtkgg.cn/jnews/6590519.htm
- http://m.wap.ghtkgg.cn/jnews/8991674.htm
- http://m.wap.ghtkgg.cn/jnews/3581402.htm
- http://m.wap.ghtkgg.cn/jnews/66182.htm
- http://m.wap.ghtkgg.cn/jnews/9455.htm
- http://m.wap.ghtkgg.cn/jnews/9425251.htm
- http://m.wap.ghtkgg.cn/jnews/13470.htm
- http://m.wap.ghtkgg.cn/jnews/075844.htm
- http://m.wap.ghtkgg.cn/jnews/0393199.htm
- http://m.wap.ghtkgg.cn/jnews/8105506.htm
- http://m.wap.ghtkgg.cn/jnews/559666.htm
- http://m.wap.ghtkgg.cn/jnews/320155.htm
- http://m.wap.ghtkgg.cn/jnews/5656776.htm
- http://m.wap.ghtkgg.cn/jnews/74815.htm
- http://m.wap.ghtkgg.cn/jnews/1071.htm
- http://m.wap.ghtkgg.cn/jnews/63449.htm
- http://m.wap.ghtkgg.cn/jnews/0535053.htm
- http://m.wap.ghtkgg.cn/jnews/4388056.htm
- http://m.wap.ghtkgg.cn/jnews/7398.htm
- http://m.wap.ghtkgg.cn/jnews/0040.htm
- http://m.wap.ghtkgg.cn/jnews/4728468.htm
- http://m.wap.ghtkgg.cn/jnews/48208.htm
- http://m.wap.ghtkgg.cn/jnews/236315.htm
- http://m.wap.ghtkgg.cn/jnews/6712.htm
- http://m.wap.ghtkgg.cn/jnews/7371522.htm
- http://m.wap.ghtkgg.cn/jnews/6564.htm
- http://m.wap.ghtkgg.cn/jnews/42715.htm
- http://m.wap.ghtkgg.cn/jnews/760118.htm
- http://m.wap.ghtkgg.cn/jnews/3032.htm
- http://m.wap.ghtkgg.cn/jnews/369818.htm
- http://m.wap.ghtkgg.cn/jnews/17644.htm
- http://m.wap.ghtkgg.cn/jnews/011595.htm
- http://m.wap.ghtkgg.cn/jnews/23146.htm
- http://m.wap.ghtkgg.cn/jnews/62084.htm
- http://m.wap.ghtkgg.cn/jnews/18069.htm
- http://m.wap.ghtkgg.cn/jnews/5421.htm
- http://m.wap.ghtkgg.cn/jnews/511465.htm
- http://m.wap.ghtkgg.cn/jnews/80034.htm
- http://m.wap.ghtkgg.cn/jnews/1515.htm
- http://m.wap.ghtkgg.cn/jnews/9546893.htm
- http://m.wap.ghtkgg.cn/jnews/69147.htm
- http://m.wap.ghtkgg.cn/jnews/7965139.htm
- http://m.wap.ghtkgg.cn/jnews/71518.htm
- http://m.wap.ghtkgg.cn/jnews/76751.htm
- http://m.wap.ghtkgg.cn/jnews/7967326.htm
- http://m.wap.ghtkgg.cn/jnews/49833.htm
- http://m.wap.ghtkgg.cn/jnews/2487894.htm
- http://m.wap.ghtkgg.cn/jnews/75363.htm
- http://m.wap.ghtkgg.cn/jnews/1391.htm
- http://m.wap.ghtkgg.cn/jnews/8418822.htm
- http://m.wap.ghtkgg.cn/jnews/6401484.htm
- http://m.wap.ghtkgg.cn/jnews/2118418.htm
- http://m.wap.ghtkgg.cn/jnews/831657.htm
- http://m.wap.ghtkgg.cn/jnews/871671.htm
- http://m.wap.ghtkgg.cn/jnews/9525604.htm
- http://m.wap.ghtkgg.cn/jnews/1727.htm
- http://m.wap.ghtkgg.cn/jnews/4801537.htm
- http://m.wap.ghtkgg.cn/jnews/4192.htm
- http://m.wap.ghtkgg.cn/jnews/2905171.htm
- http://m.wap.ghtkgg.cn/jnews/0291.htm
- http://m.wap.ghtkgg.cn/jnews/11487.htm
- http://m.wap.ghtkgg.cn/jnews/79246.htm
- http://m.wap.ghtkgg.cn/jnews/305743.htm
- http://m.wap.ghtkgg.cn/jnews/010325.htm
- http://m.wap.ghtkgg.cn/jnews/03053.htm
- http://m.wap.ghtkgg.cn/jnews/05767.htm
- http://m.wap.ghtkgg.cn/jnews/9004041.htm
- http://m.wap.ghtkgg.cn/jnews/8928519.htm
- http://m.wap.ghtkgg.cn/jnews/4396637.htm
- http://m.wap.ghtkgg.cn/jnews/5962651.htm
- http://m.wap.ghtkgg.cn/jnews/87844.htm
- http://m.wap.ghtkgg.cn/jnews/1474248.htm
- http://m.wap.ghtkgg.cn/jnews/0901.htm
- http://m.wap.ghtkgg.cn/jnews/687737.htm
- http://m.wap.ghtkgg.cn/jnews/340595.htm
- http://m.wap.ghtkgg.cn/jnews/9925.htm
- http://m.wap.ghtkgg.cn/jnews/0292.htm
- http://m.wap.ghtkgg.cn/jnews/1787889.htm
- http://m.wap.ghtkgg.cn/jnews/9897.htm
- http://m.wap.ghtkgg.cn/jnews/62229.htm
- http://m.wap.ghtkgg.cn/jnews/7782.htm
- http://m.wap.ghtkgg.cn/jnews/7537312.htm
- http://m.wap.ghtkgg.cn/jnews/11764.htm
- http://m.wap.ghtkgg.cn/jnews/05674.htm
- http://m.wap.ghtkgg.cn/jnews/75254.htm
- http://m.wap.ghtkgg.cn/jnews/66845.htm
- http://m.wap.ghtkgg.cn/jnews/4425.htm
- http://m.wap.ghtkgg.cn/jnews/18658.htm
- http://m.wap.ghtkgg.cn/jnews/5033.htm
- http://m.wap.ghtkgg.cn/jnews/326559.htm
- http://m.wap.ghtkgg.cn/jnews/45549.htm
- http://m.wap.ghtkgg.cn/jnews/92558.htm
- http://m.wap.ghtkgg.cn/jnews/542129.htm
- http://m.wap.ghtkgg.cn/jnews/13041.htm
- http://m.wap.ghtkgg.cn/jnews/47165.htm
- http://m.wap.ghtkgg.cn/jnews/051214.htm
- http://m.wap.ghtkgg.cn/jnews/3739.htm
- http://m.wap.ghtkgg.cn/jnews/095806.htm
- http://m.wap.ghtkgg.cn/jnews/91174.htm
- http://m.wap.ghtkgg.cn/jnews/8558.htm
- http://m.wap.ghtkgg.cn/jnews/8853569.htm
- http://m.wap.ghtkgg.cn/jnews/486082.htm
- http://m.wap.ghtkgg.cn/jnews/076933.htm
- http://m.wap.ghtkgg.cn/jnews/7000699.htm
- http://m.wap.ghtkgg.cn/jnews/9646266.htm
- http://m.wap.ghtkgg.cn/jnews/0644.htm
- http://m.wap.ghtkgg.cn/jnews/60581.htm
- http://m.wap.ghtkgg.cn/jnews/713564.htm
- http://m.wap.ghtkgg.cn/jnews/8198.htm
- http://m.wap.ghtkgg.cn/jnews/5433260.htm
- http://m.wap.ghtkgg.cn/jnews/619714.htm
- http://m.wap.ghtkgg.cn/jnews/41641.htm
- http://m.wap.ghtkgg.cn/jnews/141239.htm
- http://m.wap.ghtkgg.cn/jnews/1543.htm
- http://m.wap.ghtkgg.cn/jnews/4023844.htm
- http://m.wap.ghtkgg.cn/jnews/6643623.htm
- http://m.wap.ghtkgg.cn/jnews/002120.htm
- http://m.wap.ghtkgg.cn/jnews/1805.htm
- http://m.wap.ghtkgg.cn/jnews/55541.htm
- http://m.wap.ghtkgg.cn/jnews/9488.htm
- http://m.wap.ghtkgg.cn/jnews/5112.htm
- http://m.wap.ghtkgg.cn/jnews/6426.htm
- http://m.wap.ghtkgg.cn/jnews/0305.htm
- http://m.wap.ghtkgg.cn/jnews/9108765.htm
- http://m.wap.ghtkgg.cn/jnews/665681.htm
- http://m.wap.ghtkgg.cn/jnews/53647.htm
- http://m.wap.ghtkgg.cn/jnews/931990.htm
- http://m.wap.ghtkgg.cn/jnews/2564109.htm
- http://m.wap.ghtkgg.cn/jnews/29952.htm
- http://m.wap.ghtkgg.cn/jnews/5294005.htm
- http://m.wap.ghtkgg.cn/jnews/49837.htm
- http://m.wap.ghtkgg.cn/jnews/38430.htm
- http://m.wap.ghtkgg.cn/jnews/3124.htm
- http://m.wap.ghtkgg.cn/jnews/424224.htm
- http://m.wap.ghtkgg.cn/jnews/579341.htm
- http://m.wap.ghtkgg.cn/jnews/69000.htm

## 项目结构

```
weblink-navigator/
├── src/                                 # 核心源代码目录
│   ├── core/                            # 数据核心处理模块
│   │   ├── importer.js                  # 批量导入引擎，支持多种格式解析
│   │   ├── validator.js                 # URL 校验与去重逻辑
│   │   └── linker.js                    # 链接状态监测与更新调度
│   ├── server/                          # 本地开发服务器与 API 路由
│   │   ├── index.js                     # 服务入口，配置中间件与路由挂载
│   │   └── routes/                      # RESTful 接口定义
│   ├── generator/                       # 静态站点生成器
│   │   ├── page-builder.js              # 页面模板渲染与 HTML 产出
│   │   ├── indexer.js                   # 全文检索索引构建
│   │   └── asset-pipeline.js            # CSS 与 JavaScript 资源打包
│   ├── cli/                             # 命令行工具入口
│   │   ├── commands/                    # 子命令实现：init, build, serve, check
│   │   └── runner.js                    # 命令解析与执行调度
│   └── shared/                          # 跨模块共享工具函数与常量
│       ├── constants.js                 # 配置常量与默认参数
│       └── utils.js                     # 通用辅助函数
├── config/                              # 配置文件目录
│   ├── default.yaml                     # 默认配置项，包含端口、数据目录、主题等
│   └── schema.json                      # 配置文件的 JSON Schema 校验定义
├── data/                                # 用户数据存储目录（运行时生成）
│   ├── links/                           # 链接条目按分类存放为 YAML 文件
│   ├── tags/                            # 标签索引与关联关系
│   └── meta/                            # 导入历史、监测日志等元数据
├── themes/                              # 主题模板目录
│   ├── default/                         # 默认主题模板文件
│   │   ├── layouts/                     # 页面布局模板
│   │   └── assets/                      # 主题专属静态资源
│   └── compact/                         # 紧凑型主题备选方案
├── docs/                                # 项目文档源文件
│   ├── user-guide/                      # 用户指南文档
│   ├── developer/                       # 开发者文档
│   └── schema/                          # 数据规范定义
├── test/                                # 单元测试与集成测试用例
│   ├── unit/                            # 各模块单元测试
│   └── fixtures/                        # 测试用固定数据集
├── scripts/                             # 辅助脚本（lint、format、pre-commit 钩子）
├── package.json                         # npm 包声明与依赖清单
├── README.md                            # 项目说明文档（本文件）
└── LICENSE                              # MIT 许可证文本
```

## 贡献指南

首先，在 GitHub 仓库的 Issues 页面查找现有议题或新建一个议题，描述您希望解决的问题或提议的新功能，等待核心维护者的反馈与确认。

其次，从仓库的 main 分支创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 的格式，确保分支基于最新的上游代码。

第三，在本地完成代码编写后，运行测试套件确保所有现有测试通过，并为新增功能或修复编写对应的单元测试与集成测试用例，保证测试覆盖率不低于现有水平。

第四，提交代码时遵循 Conventional Commits 规范编写提交信息，格式为 `<类型>: <简短描述>`，类型包括 feat、fix、docs、style、refactor、test、chore 等。

最后，向 main 分支发起 Pull Request，在 PR 描述中清晰说明变更内容、测试结果以及相关的 Issue 编号，等待代码审查与合并。

## 常见问题

问：导入大量链接时出现内存占用过高或超时的情况应如何处理？

答：当单次导入链接数量超过 5000 条时，建议将数据分批导入，每批不超过 2000 条。您可以使用 `--batch` 参数指定批次大小，或通过管理界面的分页导入功能分批上传。若数据量极大（超过 20000 条），建议直接操作数据目录下的 YAML 文件，通过文件系统批量复制或脚本生成，然后执行 `npm run rebuild` 重建索引。

问：链接状态监测功能是否会频繁触发目标服务器的访问限制？

答：系统默认采用指数退避策略进行请求调度，并发请求数默认限制为 5，且每个目标域名在 60 秒内最多被探测 3 次。您可以在配置文件中调整 `checker.concurrency` 和 `checker.rateLimit` 参数来控制探测频率。对于大型站点，建议将监测任务安排在非高峰时段执行。

问：如何迁移已有的书签或收藏夹数据到 WebLink Navigator？

答：项目内置了针对主流浏览器书签导出格式（HTML 书签文件）的转换脚本，您可以从浏览器导出书签为 HTML 文件，然后通过管理界面的「导入」-「浏览器书签」功能上传。对于 Chrome 和 Firefox，导出格式可直接兼容。若使用其他工具，建议先将数据整理为 CSV 格式（列标题为 title、url、description、tags），再使用通用 CSV 导入功能。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
