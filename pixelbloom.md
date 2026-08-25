# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研、信息聚合与快速知识检索的轻量级网络资源索引系统。该项目定位于将分散在多个数据源中的结构化与非结构化信息进行统一收集、分类存储与可追溯管理，主要服务于需要高频查阅外部参考资料、技术文档或案例库的开发人员、研究员与技术写作人员。WebIndex 本身不生产内容，而是通过高度规范化的链接采集与元数据标注机制，为用户提供稳定、可审计、可扩展的外部资源挂载能力。

与传统的书签管理工具或简单链接收集器不同，WebIndex 在底层设计上强调数据来源的可追溯性、批次管理的清晰性以及资源快照的持久化记录。该项目采用纯静态资源索引模型，支持本地快速部署，亦可通过简单的 HTTP 服务器对外发布，适用于个人知识库构建、团队技术周报素材库、以及项目文档中的引用来源管理。当前版本为第 77 批次资源整合发布，共纳入 300 个独立资源链接，全部经由基础可用性校验与分类标记处理。

## 功能概览

**批次化资源导入** 支持按批次组织外部链接，每一批次独立记录导入时间、资源总数与校验状态，便于后续增量更新与差异比对。

**原始链接强制保真** 系统对用户输入的每一个 URL 执行严格的原文保留策略，不自动补全协议头，不修改域名大小写，不添加尾部斜杠，确保引用路径与用户原始意图完全一致。

**多维度资源筛选** 提供基于资源类型、来源域名、导入批次与关键字组合的过滤查询能力，帮助用户在数百乃至数千条链接中快速定位目标条目。

**元数据扩展标注** 每条资源支持附加标题摘要、分类标签、重要程度评分与备注字段，弥补纯链接列表在语义信息上的不足。

**目录树结构可视化** 项目内部按功能模块划分清晰的目录层次，所有资源文件、配置模板与工具脚本均以标准化命名规范存放，降低新用户的上手成本。

**快速启动与零配置运行** 项目不依赖外部数据库或运行时容器，克隆后即可通过本地静态服务器启动，适合在内网或离线环境中使用。

**状态监控与链接有效性提示** 内置基础的健康检查脚本，可对资源列表中的域名可达性进行抽样检测，并以标记形式提醒用户关注潜在失效链接。

**导出与集成友好** 资源列表支持以纯文本、JSON 和 CSV 三种格式导出，便于导入其他数据处理流水线或文档生成工具。

## 应用场景

技术文档撰写与参考文献管理
技术博客、白皮书或项目文档中需要引用大量外部资料时，WebIndex 可充当统一的引用来源登记系统。用户将待引用的链接统一录入平台，在写作过程中通过资源编号或标签快速检索，最终在文末生成标准化的引用列表，避免链接丢失或格式不一致的问题。

团队知识库资源沉淀
研发团队内部常积累大量零散的技术文章链接、视频教程地址或开源工具主页。通过 WebIndex 的批次导入功能，团队可按周或按版本汇总这些资源，并附加评论与使用心得，形成可共享、可传承的团队知识索引。

竞品分析与市场调研素材整理
产品经理或市场分析师在调研过程中收集的行业报告、竞品动态与用户案例，可通过 WebIndex 统一归档。每个资源条目支持标注重要程度与所属分析维度，便于后续生成调研报告时快速调取证据材料。

个人学习路径规划与进度追踪
学习者可以将在线课程、编程练习平台、官方文档等学习资源集中录入 WebIndex，并为每条资源设置学习状态与优先级。系统提供的标签过滤功能可帮助学习者按技术领域或学习阶段快速切换视图，实现学习任务的有序管理。

离线环境下的资源导航页
在内部网络或封闭开发环境中，WebIndex 可作为一个轻量级门户首页，集中展示团队常用的内部系统地址、代码仓库入口与运维监控面板链接。由于项目无需联网即可运行，非常适合部署于跳板机或内部文档服务器上。

## 快速开始

以下操作步骤指导用户在本地环境完成 WebIndex 的克隆、安装与运行。所有命令均基于 Linux/macOS 或 Windows WSL 环境，若使用 Windows 原生 PowerShell，请将 `./scripts` 路径替换为 `scripts\`。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装基础依赖（若使用 Python 环境）
pip install -r requirements.txt

# 执行资源索引构建脚本
./scripts/build_index.sh

# 启动本地静态服务（默认监听 8000 端口）
python -m http.server 8000
```

启动成功后，在浏览器中访问 `http://localhost:8000` 即可查看 WebIndex 的主界面。资源列表默认以批次倒序排列，最新导入的第 77 批次资源会显示在列表最上方。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 或更高 | 用于运行索引构建工具与本地服务器 |
| Git | 2.25 或更高 | 用于克隆仓库与版本管理 |
| pip | 20.0 或更高 | Python 包管理工具，用于安装依赖库 |
| 操作系统 | Linux / macOS / Windows WSL | 项目脚本基于 POSIX 兼容环境开发 |
| 硬盘空间 | 最低 50 MB | 主要用于存储资源列表元数据与静态页面模板 |
| 内存 | 最低 256 MB | 运行时内存占用极低，无需额外配置 |
| 网络访问 | 可选 | 仅在首次克隆或更新外部资源索引时需要 |
| 浏览器 | 任意主流浏览器 | 用于查看生成的索引页面 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何录入新资源、如何管理标签、如何导出过滤后的列表 |
| 管理员指南 | docs/admin-guide.md | 如何创建新批次、如何执行批量校验、如何处理失效链接 |
| 开发者文档 | docs/developer-guide.md | 项目目录结构说明、脚本接口定义、自定义渲染模板的方法 |
| 资源格式规范 | docs/schema.md | 资源列表 JSON Schema 定义、必填字段与可选字段的说明 |
| 常见操作示例 | docs/examples.md | 通过命令行进行批量导入、按域名过滤、生成统计报表的实例 |
| 版本发布记录 | docs/releases.md | 每个批次资源整合的更新日志与注意事项 |
| 贡献者指引 | CONTRIBUTING.md | 外部贡献者提交资源建议或改进代码的流程与规范 |

## 资源列表

- http://m.blog.oexnr.cn/snews/3986.htm
- http://m.blog.oexnr.cn/snews/3838268.htm
- http://m.blog.oexnr.cn/snews/1392.htm
- http://m.blog.oexnr.cn/snews/8132.htm
- http://m.blog.oexnr.cn/snews/707364.htm
- http://m.blog.oexnr.cn/snews/06073.htm
- http://m.blog.oexnr.cn/snews/681550.htm
- http://m.blog.oexnr.cn/snews/2332216.htm
- http://m.blog.oexnr.cn/snews/5839282.htm
- http://m.blog.oexnr.cn/snews/3682910.htm
- http://m.blog.oexnr.cn/snews/90702.htm
- http://m.blog.oexnr.cn/snews/5015.htm
- http://m.blog.oexnr.cn/snews/5382.htm
- http://m.blog.oexnr.cn/snews/84386.htm
- http://m.blog.oexnr.cn/snews/62800.htm
- http://m.blog.oexnr.cn/snews/3597.htm
- http://m.blog.oexnr.cn/snews/4064460.htm
- http://m.blog.oexnr.cn/snews/207342.htm
- http://m.blog.oexnr.cn/snews/94068.htm
- http://m.blog.oexnr.cn/snews/936351.htm
- http://m.blog.oexnr.cn/snews/9691.htm
- http://m.blog.oexnr.cn/snews/0618279.htm
- http://m.blog.oexnr.cn/snews/9485.htm
- http://m.blog.oexnr.cn/snews/1458478.htm
- http://m.blog.oexnr.cn/snews/3086.htm
- http://m.blog.oexnr.cn/snews/76306.htm
- http://m.blog.oexnr.cn/snews/847366.htm
- http://m.blog.oexnr.cn/snews/628258.htm
- http://m.blog.oexnr.cn/snews/32554.htm
- http://m.blog.oexnr.cn/snews/7542598.htm
- http://m.blog.oexnr.cn/snews/12986.htm
- http://m.blog.oexnr.cn/snews/67552.htm
- http://m.blog.oexnr.cn/snews/19469.htm
- http://m.blog.oexnr.cn/snews/718323.htm
- http://m.blog.oexnr.cn/snews/716025.htm
- http://m.blog.oexnr.cn/snews/2461866.htm
- http://m.blog.oexnr.cn/snews/3933.htm
- http://m.blog.oexnr.cn/snews/1356.htm
- http://m.blog.oexnr.cn/snews/11177.htm
- http://m.blog.oexnr.cn/snews/8597.htm
- http://m.blog.oexnr.cn/snews/9101.htm
- http://m.blog.oexnr.cn/snews/04198.htm
- http://m.blog.oexnr.cn/snews/52904.htm
- http://m.blog.oexnr.cn/snews/417213.htm
- http://m.blog.oexnr.cn/snews/0176288.htm
- http://m.blog.oexnr.cn/snews/404051.htm
- http://m.blog.oexnr.cn/snews/0258129.htm
- http://m.blog.oexnr.cn/snews/39809.htm
- http://m.blog.oexnr.cn/snews/8005296.htm
- http://m.blog.oexnr.cn/snews/518208.htm
- http://m.blog.oexnr.cn/snews/95137.htm
- http://m.blog.oexnr.cn/snews/90284.htm
- http://m.blog.oexnr.cn/snews/4385.htm
- http://m.blog.oexnr.cn/snews/963621.htm
- http://m.blog.oexnr.cn/snews/5914745.htm
- http://m.blog.oexnr.cn/snews/20541.htm
- http://m.blog.oexnr.cn/snews/646914.htm
- http://m.blog.oexnr.cn/snews/1766272.htm
- http://m.blog.oexnr.cn/snews/14986.htm
- http://m.blog.oexnr.cn/snews/8767946.htm
- http://m.blog.oexnr.cn/snews/543886.htm
- http://m.blog.oexnr.cn/snews/9697718.htm
- http://m.blog.oexnr.cn/snews/8073734.htm
- http://m.blog.oexnr.cn/snews/1943768.htm
- http://m.blog.oexnr.cn/snews/6767214.htm
- http://m.blog.oexnr.cn/snews/8814265.htm
- http://m.blog.oexnr.cn/snews/3007717.htm
- http://m.blog.oexnr.cn/snews/60990.htm
- http://m.blog.oexnr.cn/snews/391412.htm
- http://m.blog.oexnr.cn/snews/561112.htm
- http://m.blog.oexnr.cn/snews/0837.htm
- http://m.blog.oexnr.cn/snews/62785.htm
- http://m.blog.oexnr.cn/snews/380015.htm
- http://m.blog.oexnr.cn/snews/6709.htm
- http://m.blog.oexnr.cn/snews/24801.htm
- http://m.blog.oexnr.cn/snews/1463.htm
- http://m.blog.oexnr.cn/snews/4836729.htm
- http://m.blog.oexnr.cn/snews/851164.htm
- http://m.blog.oexnr.cn/snews/374564.htm
- http://m.blog.oexnr.cn/snews/9741692.htm
- http://m.blog.oexnr.cn/snews/7275.htm
- http://m.blog.oexnr.cn/snews/19838.htm
- http://m.blog.oexnr.cn/snews/0869718.htm
- http://m.blog.oexnr.cn/snews/87129.htm
- http://m.blog.oexnr.cn/snews/95231.htm
- http://m.blog.oexnr.cn/snews/982570.htm
- http://m.blog.oexnr.cn/snews/221445.htm
- http://m.blog.oexnr.cn/snews/02887.htm
- http://m.blog.oexnr.cn/snews/4539363.htm
- http://m.blog.oexnr.cn/snews/01982.htm
- http://m.blog.oexnr.cn/snews/9539713.htm
- http://m.blog.oexnr.cn/snews/05072.htm
- http://m.blog.oexnr.cn/snews/888297.htm
- http://m.blog.oexnr.cn/snews/83981.htm
- http://m.blog.oexnr.cn/snews/1009265.htm
- http://m.blog.oexnr.cn/snews/637752.htm
- http://m.blog.oexnr.cn/snews/7450.htm
- http://m.blog.oexnr.cn/snews/9666.htm
- http://m.blog.oexnr.cn/snews/8104.htm
- http://m.blog.oexnr.cn/snews/633596.htm
- http://m.blog.oexnr.cn/snews/0077985.htm
- http://m.blog.oexnr.cn/snews/120799.htm
- http://m.blog.oexnr.cn/snews/610344.htm
- http://m.blog.oexnr.cn/snews/96200.htm
- http://m.blog.oexnr.cn/snews/13935.htm
- http://m.blog.oexnr.cn/snews/43221.htm
- http://m.blog.oexnr.cn/snews/302129.htm
- http://m.blog.oexnr.cn/snews/056972.htm
- http://m.blog.oexnr.cn/snews/56276.htm
- http://m.blog.oexnr.cn/snews/2997290.htm
- http://m.blog.oexnr.cn/snews/969668.htm
- http://m.blog.oexnr.cn/snews/2112330.htm
- http://m.blog.oexnr.cn/snews/790374.htm
- http://m.blog.oexnr.cn/snews/3594.htm
- http://m.blog.oexnr.cn/snews/202001.htm
- http://m.blog.oexnr.cn/snews/2859053.htm
- http://m.blog.oexnr.cn/snews/1351338.htm
- http://m.blog.oexnr.cn/snews/09615.htm
- http://m.blog.oexnr.cn/snews/489629.htm
- http://m.blog.oexnr.cn/snews/50417.htm
- http://m.blog.oexnr.cn/snews/662319.htm
- http://m.blog.oexnr.cn/snews/667712.htm
- http://m.blog.oexnr.cn/snews/258053.htm
- http://m.blog.oexnr.cn/snews/893940.htm
- http://m.blog.oexnr.cn/snews/240368.htm
- http://m.blog.oexnr.cn/snews/0478287.htm
- http://m.blog.oexnr.cn/snews/10112.htm
- http://m.blog.oexnr.cn/snews/2017.htm
- http://m.blog.oexnr.cn/snews/03151.htm
- http://m.blog.oexnr.cn/snews/6206.htm
- http://m.blog.oexnr.cn/snews/594118.htm
- http://m.blog.oexnr.cn/snews/04547.htm
- http://m.blog.oexnr.cn/snews/709127.htm
- http://m.blog.oexnr.cn/snews/9339214.htm
- http://m.blog.oexnr.cn/snews/32120.htm
- http://m.blog.oexnr.cn/snews/23119.htm
- http://m.blog.oexnr.cn/snews/1615.htm
- http://m.blog.oexnr.cn/snews/2026335.htm
- http://m.blog.oexnr.cn/snews/170229.htm
- http://m.blog.oexnr.cn/snews/41405.htm
- http://m.blog.oexnr.cn/snews/5508666.htm
- http://m.blog.oexnr.cn/snews/6213.htm
- http://m.blog.oexnr.cn/snews/13181.htm
- http://m.blog.oexnr.cn/snews/0120890.htm
- http://m.blog.oexnr.cn/snews/091802.htm
- http://m.blog.oexnr.cn/snews/761131.htm
- http://m.blog.oexnr.cn/snews/74237.htm
- http://m.blog.oexnr.cn/snews/88122.htm
- http://m.blog.oexnr.cn/snews/729263.htm
- http://m.blog.oexnr.cn/snews/36605.htm
- http://m.blog.oexnr.cn/snews/1831.htm
- http://m.blog.oexnr.cn/snews/516427.htm
- http://m.blog.oexnr.cn/snews/6137479.htm
- http://m.blog.oexnr.cn/snews/023224.htm
- http://m.blog.oexnr.cn/snews/9841204.htm
- http://m.blog.oexnr.cn/snews/998991.htm
- http://m.blog.oexnr.cn/snews/369173.htm
- http://m.blog.oexnr.cn/snews/5911.htm
- http://m.blog.oexnr.cn/snews/0537501.htm
- http://m.blog.oexnr.cn/snews/562550.htm
- http://m.blog.oexnr.cn/snews/8358392.htm
- http://m.blog.oexnr.cn/snews/828983.htm
- http://m.blog.oexnr.cn/snews/8804.htm
- http://m.blog.oexnr.cn/snews/5580897.htm
- http://m.blog.oexnr.cn/snews/8077.htm
- http://m.blog.oexnr.cn/snews/940283.htm
- http://m.blog.oexnr.cn/snews/0015602.htm
- http://m.blog.oexnr.cn/snews/1932.htm
- http://m.blog.oexnr.cn/snews/59531.htm
- http://m.blog.oexnr.cn/snews/4607353.htm
- http://m.blog.oexnr.cn/snews/40752.htm
- http://m.blog.oexnr.cn/snews/6596974.htm
- http://m.blog.oexnr.cn/snews/9676.htm
- http://m.blog.oexnr.cn/snews/7321634.htm
- http://m.blog.oexnr.cn/snews/38241.htm
- http://m.blog.oexnr.cn/snews/54432.htm
- http://m.blog.oexnr.cn/snews/29562.htm
- http://m.blog.oexnr.cn/snews/2990986.htm
- http://m.blog.oexnr.cn/snews/43273.htm
- http://m.blog.oexnr.cn/snews/9528.htm
- http://m.blog.oexnr.cn/snews/4119712.htm
- http://m.blog.oexnr.cn/snews/6542994.htm
- http://m.blog.oexnr.cn/snews/033901.htm
- http://m.blog.oexnr.cn/snews/164345.htm
- http://m.blog.oexnr.cn/snews/7253.htm
- http://m.blog.oexnr.cn/snews/35577.htm
- http://m.blog.oexnr.cn/snews/14161.htm
- http://m.blog.oexnr.cn/snews/4290.htm
- http://m.blog.oexnr.cn/snews/7923187.htm
- http://m.blog.oexnr.cn/snews/0596.htm
- http://m.blog.oexnr.cn/snews/8128.htm
- http://m.blog.oexnr.cn/snews/27327.htm
- http://m.blog.oexnr.cn/snews/602649.htm
- http://m.blog.oexnr.cn/snews/403788.htm
- http://m.blog.oexnr.cn/snews/898662.htm
- http://m.blog.oexnr.cn/snews/97148.htm
- http://m.blog.oexnr.cn/snews/617120.htm
- http://m.blog.oexnr.cn/snews/02601.htm
- http://m.blog.oexnr.cn/snews/165780.htm
- http://m.blog.oexnr.cn/snews/1745589.htm
- http://m.blog.oexnr.cn/snews/257611.htm
- http://m.blog.oexnr.cn/snews/9920510.htm
- http://m.blog.oexnr.cn/snews/90256.htm
- http://m.blog.oexnr.cn/snews/966044.htm
- http://m.blog.oexnr.cn/snews/2599194.htm
- http://m.blog.oexnr.cn/snews/19807.htm
- http://m.blog.oexnr.cn/snews/48148.htm
- http://m.blog.oexnr.cn/snews/81707.htm
- http://m.blog.oexnr.cn/snews/7757944.htm
- http://m.blog.oexnr.cn/snews/8040566.htm
- http://m.blog.oexnr.cn/snews/87604.htm
- http://m.blog.oexnr.cn/snews/816943.htm
- http://m.blog.oexnr.cn/snews/37275.htm
- http://m.blog.oexnr.cn/snews/77867.htm
- http://m.blog.oexnr.cn/snews/25676.htm
- http://m.blog.oexnr.cn/snews/797130.htm
- http://m.blog.oexnr.cn/snews/5621353.htm
- http://m.blog.oexnr.cn/snews/932742.htm
- http://m.blog.oexnr.cn/snews/491269.htm
- http://m.blog.oexnr.cn/snews/023762.htm
- http://m.blog.oexnr.cn/snews/6054162.htm
- http://m.blog.oexnr.cn/snews/8687004.htm
- http://m.blog.oexnr.cn/snews/320431.htm
- http://m.blog.oexnr.cn/snews/9125.htm
- http://m.blog.oexnr.cn/snews/615884.htm
- http://m.blog.oexnr.cn/snews/950380.htm
- http://m.blog.oexnr.cn/snews/56217.htm
- http://m.blog.oexnr.cn/snews/3125.htm
- http://m.blog.oexnr.cn/snews/4623486.htm
- http://m.blog.oexnr.cn/snews/29563.htm
- http://m.blog.oexnr.cn/snews/9729630.htm
- http://m.blog.oexnr.cn/snews/269310.htm
- http://m.blog.oexnr.cn/snews/3850.htm
- http://m.blog.oexnr.cn/snews/2136.htm
- http://m.blog.oexnr.cn/snews/0151.htm
- http://m.blog.oexnr.cn/snews/4181.htm
- http://m.blog.oexnr.cn/snews/1805.htm
- http://m.blog.oexnr.cn/snews/5675.htm
- http://m.blog.oexnr.cn/snews/6588.htm
- http://m.blog.oexnr.cn/snews/69325.htm
- http://m.blog.oexnr.cn/snews/922842.htm
- http://m.blog.oexnr.cn/snews/8197.htm
- http://m.blog.oexnr.cn/snews/74046.htm
- http://m.blog.oexnr.cn/snews/217822.htm
- http://m.blog.oexnr.cn/snews/05995.htm
- http://m.blog.oexnr.cn/snews/42595.htm
- http://m.blog.oexnr.cn/snews/3959.htm
- http://m.blog.oexnr.cn/snews/3121752.htm
- http://m.blog.oexnr.cn/snews/9087.htm
- http://m.blog.oexnr.cn/snews/55856.htm
- http://m.blog.oexnr.cn/snews/9837.htm
- http://m.blog.oexnr.cn/snews/1114627.htm
- http://m.blog.oexnr.cn/snews/1361735.htm
- http://m.blog.oexnr.cn/snews/901551.htm
- http://m.blog.oexnr.cn/snews/51538.htm
- http://m.blog.oexnr.cn/snews/26376.htm
- http://m.blog.oexnr.cn/snews/4877.htm
- http://m.blog.oexnr.cn/snews/982810.htm
- http://m.blog.oexnr.cn/snews/126462.htm
- http://m.blog.oexnr.cn/snews/60616.htm
- http://m.blog.oexnr.cn/snews/5653.htm
- http://m.blog.oexnr.cn/snews/48968.htm
- http://m.blog.oexnr.cn/snews/4732.htm
- http://m.blog.oexnr.cn/snews/7668272.htm
- http://m.blog.oexnr.cn/snews/56413.htm
- http://m.blog.oexnr.cn/snews/2563302.htm
- http://m.blog.oexnr.cn/snews/87193.htm
- http://m.blog.oexnr.cn/snews/0504475.htm
- http://m.blog.oexnr.cn/snews/430771.htm
- http://m.blog.oexnr.cn/snews/1366102.htm
- http://m.blog.oexnr.cn/snews/7276.htm
- http://m.blog.oexnr.cn/snews/7373189.htm
- http://m.blog.oexnr.cn/snews/7666824.htm
- http://m.blog.oexnr.cn/snews/0288.htm
- http://m.blog.oexnr.cn/snews/6556290.htm
- http://m.blog.oexnr.cn/snews/7634.htm
- http://m.blog.oexnr.cn/snews/98291.htm
- http://m.blog.oexnr.cn/snews/44130.htm
- http://m.blog.oexnr.cn/snews/3347602.htm
- http://m.blog.oexnr.cn/snews/0023472.htm
- http://m.blog.oexnr.cn/snews/30749.htm
- http://m.blog.oexnr.cn/snews/7185702.htm
- http://m.blog.oexnr.cn/snews/77155.htm
- http://m.blog.oexnr.cn/snews/2992.htm
- http://m.blog.oexnr.cn/snews/2164305.htm
- http://m.blog.oexnr.cn/snews/1523.htm
- http://m.blog.oexnr.cn/snews/5864.htm
- http://m.blog.oexnr.cn/snews/8903.htm
- http://m.blog.oexnr.cn/snews/712932.htm
- http://m.blog.oexnr.cn/snews/490451.htm
- http://m.blog.oexnr.cn/snews/0673614.htm
- http://m.blog.oexnr.cn/snews/135457.htm
- http://m.blog.oexnr.cn/snews/73073.htm
- http://m.blog.oexnr.cn/snews/5534.htm
- http://m.blog.oexnr.cn/snews/4259845.htm
- http://m.blog.oexnr.cn/snews/5779378.htm
- http://m.blog.oexnr.cn/snews/4121876.htm
- http://m.blog.oexnr.cn/snews/2044.htm
- http://m.blog.oexnr.cn/snews/5120137.htm
- http://m.blog.oexnr.cn/snews/8339.htm

## 项目结构

```
webindex/
├── index.html                         # 项目入口页面，展示资源列表与搜索栏
├── config/
│   ├── settings.yaml                  # 全局配置文件，包含站点名称、每页显示条数等
│   └── batch_77.yaml                  # 第 77 批次的元数据配置，记录导入时间与校验状态
├── data/
│   ├── raw/                           # 原始资源数据存放目录
│   │   └── batch_77_raw.json          # 第 77 批次未经处理的原始链接列表
│   ├── processed/                     # 经过清洗与标注处理后的数据
│   │   └── batch_77_enriched.json     # 附加了分类标签与备注的增强数据
│   └── cache/                         # 缓存目录，存放临时生成的渲染结果
│       └── index_cache.html           # 主页静态缓存文件
├── scripts/
│   ├── build_index.sh                 # 主构建脚本，调用 Python 模块生成静态页面
│   ├── validate_urls.py               # URL 格式校验与域名可达性检查脚本
│   ├── export_csv.py                  # 将资源列表导出为 CSV 格式的工具
│   └── watch_changes.sh               # 开发模式下监听文件变更并自动重新构建
├── templates/
│   ├── base.html                      # 基础 HTML 模板，包含通用头部与底部
│   ├── list_view.html                 # 资源列表渲染模板
│   └── detail_view.html               # 单条资源详情展示模板
├── static/
│   ├── css/
│   │   └── style.css                  # 全局样式表，基于 Flexbox 实现响应式布局
│   ├── js/
│   │   ├── filter.js                  # 前端过滤与搜索逻辑
│   │   └── pagination.js              # 分页控制脚本
│   └── assets/
│       └── logo.svg                   # 项目标识图形文件
├── docs/                              # 完整文档目录，内容与文档导航章节一一对应
│   ├── user-guide.md
│   ├── admin-guide.md
│   ├── developer-guide.md
│   ├── schema.md
│   ├── examples.md
│   └── releases.md
├── tests/                             # 单元测试与集成测试目录
│   ├── test_validator.py              # 测试 URL 校验函数的正确性
│   └── test_exporter.py               # 测试导出功能的数据完整性
├── requirements.txt                   # Python 依赖清单，包含 PyYAML、requests 等库
├── LICENSE                            # MIT 许可证全文
└── CONTRIBUTING.md                    # 贡献者行为准则与提交规范
```

## 贡献指南

提交资源建议或改进代码前，请先阅读项目行为准则并签署贡献者许可协议。所有贡献均需通过 GitHub Pull Request 流程提交，并在提交信息中明确标注关联的批次编号。

具体贡献步骤如下：

1.  Fork 本仓库至个人账户，并在本地克隆 fork 后的版本。创建新分支时请使用 `feature/` 或 `fix/` 前缀，例如 `feature/batch-78-resources`。

2.  若新增资源链接，请将原始 URL 以纯文本形式追加至 `data/raw/` 目录下对应批次的 JSON 文件中，并确保每条链接独占一行，不附加任何额外格式。若为代码改进，请确保代码风格符合 PEP 8 规范，并为新增功能编写对应的单元测试。

3.  提交前执行本地验证流程：运行 `./scripts/build_index.sh` 确保构建成功，执行 `pytest tests/` 确认所有测试用例通过，并检查文档中涉及的部分是否与变更保持同步。

4.  向主仓库的 `develop` 分支发起 Pull Request，在描述中清晰说明本次变更的目的、涉及的文件范围以及测试结果摘要。若贡献涉及资源批次更新，请注明新旧资源数量对比。

5.  等待项目维护者进行代码审查。审查通过后，维护者会将变更合并至主分支，并更新 `docs/releases.md` 中的发布记录。若审查未通过，请根据反馈意见修改后重新提交。

## 常见问题

问题：资源列表中包含大量链接，如何快速判断哪些链接已经失效？

回答：项目提供了 `scripts/validate_urls.py` 脚本，该脚本会并发发送 HEAD 请求检测每个域名的基础可达性。执行 `python scripts/validate_urls.py --batch 77` 即可对第 77 批次进行抽样检测（默认抽样比例 20%）。脚本会生成一份 `validation_report.json` 报告，列出响应时间异常或返回非 2xx/3xx 状态码的链接。需要注意的是，部分网站可能屏蔽 HEAD 请求或存在反爬机制，因此该检测结果仅作为参考，不能完全代表链接内容的实际可用性。

问题：我可以在 WebIndex 中录入非 HTTP/HTTPS 协议的链接吗，例如 mailto 或 ftp？

回答：WebIndex 的 URL 校验模块默认只接受 HTTP 和 HTTPS 协议，这是为了保证链接在浏览器中可被正常打开。对于 mailto、ftp、telnet 等其他协议，系统会发出警告但不会强制拦截，用户可以手动确认后继续录入。不过这些非网页协议的链接在导出和展示时不会附带额外的可点击标识，仅作为纯文本参考信息。

问题：项目每次启动时都会重新构建所有批次的索引页面，批次数过多时构建速度变慢，有何优化建议？

回答：从第 50 批次开始，项目引入了增量构建模式。用户可以在 `config/settings.yaml` 中将 `build_mode` 设置为 `incremental`，此时构建脚本只会处理最近新增或修改过的批次数据，不会重新扫描全部历史批次。同时建议定期归档早期批次数据至 `data/archive/` 目录，并在主配置文件中排除归档目录的扫描路径，以进一步缩短构建时间。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
