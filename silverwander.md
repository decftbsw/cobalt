# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端新闻资讯聚合的技术资源索引项目，专注于对 ghtkgg.cn 域名下 jnews 路径中的大量新闻条目进行集中化整理与分类管理。本项目定位为新闻外链导航工具，主要服务于需要批量查阅、归档或分析移动端新闻内容的技术人员、内容运营人员以及数据采集开发者，帮助其从海量条目中快速定位目标资源，减少人工检索成本。

项目以纯静态 Markdown 文档形式对外提供资源列表，不依赖数据库或后端服务，所有链接均保持原始 URL 结构，确保访问路径的完整性与可追溯性。通过固定批次归档方式，本项目收录第 164/300 批资源链接，共计 300 个新闻条目 URL，所有链接均源自 m.wap.ghtkgg.cn 移动站点下的 jnews 目录。

## 功能概览

**批量链接归档**：提供固定的 300 条新闻链接结构化列表，支持按批次查阅全部资源。

**原始 URL 保留**：所有链接均以原始字符串形式呈现，不添加协议补全、不修改域名、不转换为超链接语法，确保数据可被直接复制使用。

**移动端适配来源**：所有资源均来自 m.wap.ghtkgg.cn 子域名，符合移动端新闻页面的访问规范。

**ASCII 目录树展示**：项目结构以树形图呈现，附带注释说明各目录与文件的职责。

**多维度文档导航**：通过表格形式划分不同层面的文档指引，帮助用户按需定位信息。

**快速部署脚本**：提供 bash 命令集实现项目克隆、依赖安装与服务启动的一体化操作。

**系统依赖清单**：以表格形式明确列出所有必需的系统组件与运行环境要求。

**贡献流程规范**：定义清晰的 PR 提交、分支管理与问题反馈流程。

## 应用场景

**新闻数据采集任务的前置准备**：数据采集工程师在编写爬虫脚本前，可通过本项目的资源列表快速获取目标 URL 集合，用于配置起始种子链接或验证站点结构。例如，采集任务需要覆盖 jnews 目录下的多个数字 ID 段时，可直接从列表中提取 ID 范围。

**内容运营人员的批量转存操作**：运营人员需要将某一批次的新闻链接存入内部内容管理系统或分享至协作平台时，可复制列表中的 URL 进行批量导入，无需逐条从移动端页面手动复制。

**网站迁移与链接有效性检查**：在进行站点迁移或域名更换时，技术运维可利用本项目的完整 URL 列表进行批量访问测试，检查哪些链接仍可正常响应，哪些已返回 404 或重定向状态码，从而辅助迁移决策。

**学术研究中的新闻样本抽样**：社会科学或传播学研究者需要抽取移动端新闻样本进行内容分析时，可将本批次链接作为抽样框架，从中随机选取若干条目进行编码与分析。

## 快速开始

以下命令序列用于完成项目克隆、依赖安装和本地预览服务启动：

```bash
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator
npm install -g markdown-server
md-server --port 8080 --dir ./docs
```

若使用 Python 生态，可替换为：

```bash
pip install mkdocs
mkdocs build
mkdocs serve --dev-addr=127.0.0.1:8000
```

启动后访问本地服务地址即可查阅完整资源列表与文档内容。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Node.js | 14.x 及以上 | 用于运行 Markdown 预览服务或相关构建工具 |
| npm | 6.x 及以上 | Node.js 包管理器，用于安装文档服务依赖 |
| Git | 2.x 及以上 | 用于克隆项目仓库和版本控制操作 |
| Python | 3.8 及以上（可选） | 若使用 mkdocs 作为文档引擎则需要 |
| mkdocs | 1.3.x 及以上（可选） | Python 静态站点生成器，用于本地预览 |
| markdown-server | 1.0.x 及以上（可选） | Node.js 环境下的 Markdown 渲染服务 |
| 现代浏览器 | 最新两个版本 | 用于查看渲染后的文档页面 |
| 网络连接 | 稳定 | 访问原始 URL 资源时需连接互联网 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门 | README.md | 项目是什么、如何快速开始使用、基本功能有哪些 |
| 资源 | 资源列表章节 | 当前批次包含哪些具体 URL、如何批量获取链接 |
| 结构 | 项目结构章节 | 仓库目录组织方式、各文件与文件夹的职责划分 |
| 贡献 | 贡献指南章节 | 如何提交改进、报告问题、参与项目协作 |
| 环境 | 安装要求章节 | 运行本项目需要哪些软件依赖与版本约束 |
| 场景 | 应用场景章节 | 本项目在哪些实际工作流程中能够发挥作用 |
| 规则 | 常见问题章节 | 用户高频疑问的集中解答 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/9339683.htm
- http://m.wap.ghtkgg.cn/jnews/0519.htm
- http://m.wap.ghtkgg.cn/jnews/17161.htm
- http://m.wap.ghtkgg.cn/jnews/2267.htm
- http://m.wap.ghtkgg.cn/jnews/0760.htm
- http://m.wap.ghtkgg.cn/jnews/4407267.htm
- http://m.wap.ghtkgg.cn/jnews/4782367.htm
- http://m.wap.ghtkgg.cn/jnews/7276648.htm
- http://m.wap.ghtkgg.cn/jnews/9663025.htm
- http://m.wap.ghtkgg.cn/jnews/2578.htm
- http://m.wap.ghtkgg.cn/jnews/70971.htm
- http://m.wap.ghtkgg.cn/jnews/0948102.htm
- http://m.wap.ghtkgg.cn/jnews/06868.htm
- http://m.wap.ghtkgg.cn/jnews/59030.htm
- http://m.wap.ghtkgg.cn/jnews/9554098.htm
- http://m.wap.ghtkgg.cn/jnews/7698019.htm
- http://m.wap.ghtkgg.cn/jnews/6189170.htm
- http://m.wap.ghtkgg.cn/jnews/0893.htm
- http://m.wap.ghtkgg.cn/jnews/72853.htm
- http://m.wap.ghtkgg.cn/jnews/17733.htm
- http://m.wap.ghtkgg.cn/jnews/215971.htm
- http://m.wap.ghtkgg.cn/jnews/6325984.htm
- http://m.wap.ghtkgg.cn/jnews/4142.htm
- http://m.wap.ghtkgg.cn/jnews/0751.htm
- http://m.wap.ghtkgg.cn/jnews/280781.htm
- http://m.wap.ghtkgg.cn/jnews/650048.htm
- http://m.wap.ghtkgg.cn/jnews/2065092.htm
- http://m.wap.ghtkgg.cn/jnews/446317.htm
- http://m.wap.ghtkgg.cn/jnews/3098196.htm
- http://m.wap.ghtkgg.cn/jnews/6066452.htm
- http://m.wap.ghtkgg.cn/jnews/89002.htm
- http://m.wap.ghtkgg.cn/jnews/7551.htm
- http://m.wap.ghtkgg.cn/jnews/7884.htm
- http://m.wap.ghtkgg.cn/jnews/22804.htm
- http://m.wap.ghtkgg.cn/jnews/7456714.htm
- http://m.wap.ghtkgg.cn/jnews/7811932.htm
- http://m.wap.ghtkgg.cn/jnews/657623.htm
- http://m.wap.ghtkgg.cn/jnews/848085.htm
- http://m.wap.ghtkgg.cn/jnews/70398.htm
- http://m.wap.ghtkgg.cn/jnews/8867974.htm
- http://m.wap.ghtkgg.cn/jnews/2527081.htm
- http://m.wap.ghtkgg.cn/jnews/1535408.htm
- http://m.wap.ghtkgg.cn/jnews/265840.htm
- http://m.wap.ghtkgg.cn/jnews/3825.htm
- http://m.wap.ghtkgg.cn/jnews/757541.htm
- http://m.wap.ghtkgg.cn/jnews/7591226.htm
- http://m.wap.ghtkgg.cn/jnews/4569499.htm
- http://m.wap.ghtkgg.cn/jnews/680811.htm
- http://m.wap.ghtkgg.cn/jnews/594997.htm
- http://m.wap.ghtkgg.cn/jnews/0764.htm
- http://m.wap.ghtkgg.cn/jnews/06520.htm
- http://m.wap.ghtkgg.cn/jnews/38004.htm
- http://m.wap.ghtkgg.cn/jnews/124300.htm
- http://m.wap.ghtkgg.cn/jnews/6318.htm
- http://m.wap.ghtkgg.cn/jnews/1210.htm
- http://m.wap.ghtkgg.cn/jnews/3961.htm
- http://m.wap.ghtkgg.cn/jnews/2086556.htm
- http://m.wap.ghtkgg.cn/jnews/7720.htm
- http://m.wap.ghtkgg.cn/jnews/8950165.htm
- http://m.wap.ghtkgg.cn/jnews/13222.htm
- http://m.wap.ghtkgg.cn/jnews/7510.htm
- http://m.wap.ghtkgg.cn/jnews/7498.htm
- http://m.wap.ghtkgg.cn/jnews/3501.htm
- http://m.wap.ghtkgg.cn/jnews/336286.htm
- http://m.wap.ghtkgg.cn/jnews/1215913.htm
- http://m.wap.ghtkgg.cn/jnews/94573.htm
- http://m.wap.ghtkgg.cn/jnews/9490.htm
- http://m.wap.ghtkgg.cn/jnews/25945.htm
- http://m.wap.ghtkgg.cn/jnews/34172.htm
- http://m.wap.ghtkgg.cn/jnews/238465.htm
- http://m.wap.ghtkgg.cn/jnews/18675.htm
- http://m.wap.ghtkgg.cn/jnews/125877.htm
- http://m.wap.ghtkgg.cn/jnews/8008.htm
- http://m.wap.ghtkgg.cn/jnews/691109.htm
- http://m.wap.ghtkgg.cn/jnews/55859.htm
- http://m.wap.ghtkgg.cn/jnews/218033.htm
- http://m.wap.ghtkgg.cn/jnews/2534743.htm
- http://m.wap.ghtkgg.cn/jnews/348560.htm
- http://m.wap.ghtkgg.cn/jnews/4855653.htm
- http://m.wap.ghtkgg.cn/jnews/9406.htm
- http://m.wap.ghtkgg.cn/jnews/2869943.htm
- http://m.wap.ghtkgg.cn/jnews/1709136.htm
- http://m.wap.ghtkgg.cn/jnews/7260.htm
- http://m.wap.ghtkgg.cn/jnews/01937.htm
- http://m.wap.ghtkgg.cn/jnews/2421.htm
- http://m.wap.ghtkgg.cn/jnews/540476.htm
- http://m.wap.ghtkgg.cn/jnews/58203.htm
- http://m.wap.ghtkgg.cn/jnews/9721676.htm
- http://m.wap.ghtkgg.cn/jnews/039975.htm
- http://m.wap.ghtkgg.cn/jnews/317197.htm
- http://m.wap.ghtkgg.cn/jnews/8359.htm
- http://m.wap.ghtkgg.cn/jnews/459184.htm
- http://m.wap.ghtkgg.cn/jnews/99178.htm
- http://m.wap.ghtkgg.cn/jnews/0439.htm
- http://m.wap.ghtkgg.cn/jnews/989664.htm
- http://m.wap.ghtkgg.cn/jnews/0257611.htm
- http://m.wap.ghtkgg.cn/jnews/6814271.htm
- http://m.wap.ghtkgg.cn/jnews/1819.htm
- http://m.wap.ghtkgg.cn/jnews/0955373.htm
- http://m.wap.ghtkgg.cn/jnews/688556.htm
- http://m.wap.ghtkgg.cn/jnews/0337.htm
- http://m.wap.ghtkgg.cn/jnews/0131.htm
- http://m.wap.ghtkgg.cn/jnews/787327.htm
- http://m.wap.ghtkgg.cn/jnews/911004.htm
- http://m.wap.ghtkgg.cn/jnews/143964.htm
- http://m.wap.ghtkgg.cn/jnews/9466.htm
- http://m.wap.ghtkgg.cn/jnews/1123526.htm
- http://m.wap.ghtkgg.cn/jnews/76048.htm
- http://m.wap.ghtkgg.cn/jnews/3611.htm
- http://m.wap.ghtkgg.cn/jnews/33810.htm
- http://m.wap.ghtkgg.cn/jnews/482082.htm
- http://m.wap.ghtkgg.cn/jnews/9216.htm
- http://m.wap.ghtkgg.cn/jnews/649558.htm
- http://m.wap.ghtkgg.cn/jnews/4098661.htm
- http://m.wap.ghtkgg.cn/jnews/6473140.htm
- http://m.wap.ghtkgg.cn/jnews/403348.htm
- http://m.wap.ghtkgg.cn/jnews/62850.htm
- http://m.wap.ghtkgg.cn/jnews/28507.htm
- http://m.wap.ghtkgg.cn/jnews/978261.htm
- http://m.wap.ghtkgg.cn/jnews/58073.htm
- http://m.wap.ghtkgg.cn/jnews/6714041.htm
- http://m.wap.ghtkgg.cn/jnews/1848.htm
- http://m.wap.ghtkgg.cn/jnews/8049.htm
- http://m.wap.ghtkgg.cn/jnews/5484.htm
- http://m.wap.ghtkgg.cn/jnews/0613218.htm
- http://m.wap.ghtkgg.cn/jnews/565859.htm
- http://m.wap.ghtkgg.cn/jnews/292830.htm
- http://m.wap.ghtkgg.cn/jnews/95156.htm
- http://m.wap.ghtkgg.cn/jnews/8570950.htm
- http://m.wap.ghtkgg.cn/jnews/1408207.htm
- http://m.wap.ghtkgg.cn/jnews/06025.htm
- http://m.wap.ghtkgg.cn/jnews/20273.htm
- http://m.wap.ghtkgg.cn/jnews/2477.htm
- http://m.wap.ghtkgg.cn/jnews/0811.htm
- http://m.wap.ghtkgg.cn/jnews/12788.htm
- http://m.wap.ghtkgg.cn/jnews/558495.htm
- http://m.wap.ghtkgg.cn/jnews/1608597.htm
- http://m.wap.ghtkgg.cn/jnews/94437.htm
- http://m.wap.ghtkgg.cn/jnews/50835.htm
- http://m.wap.ghtkgg.cn/jnews/4030.htm
- http://m.wap.ghtkgg.cn/jnews/6831.htm
- http://m.wap.ghtkgg.cn/jnews/29622.htm
- http://m.wap.ghtkgg.cn/jnews/994704.htm
- http://m.wap.ghtkgg.cn/jnews/0169148.htm
- http://m.wap.ghtkgg.cn/jnews/66850.htm
- http://m.wap.ghtkgg.cn/jnews/6782.htm
- http://m.wap.ghtkgg.cn/jnews/000718.htm
- http://m.wap.ghtkgg.cn/jnews/68572.htm
- http://m.wap.ghtkgg.cn/jnews/15099.htm
- http://m.wap.ghtkgg.cn/jnews/74088.htm
- http://m.wap.ghtkgg.cn/jnews/369843.htm
- http://m.wap.ghtkgg.cn/jnews/10424.htm
- http://m.wap.ghtkgg.cn/jnews/1023.htm
- http://m.wap.ghtkgg.cn/jnews/23632.htm
- http://m.wap.ghtkgg.cn/jnews/00336.htm
- http://m.wap.ghtkgg.cn/jnews/52271.htm
- http://m.wap.ghtkgg.cn/jnews/3106777.htm
- http://m.wap.ghtkgg.cn/jnews/5624174.htm
- http://m.wap.ghtkgg.cn/jnews/325793.htm
- http://m.wap.ghtkgg.cn/jnews/462162.htm
- http://m.wap.ghtkgg.cn/jnews/5200.htm
- http://m.wap.ghtkgg.cn/jnews/2675.htm
- http://m.wap.ghtkgg.cn/jnews/4003.htm
- http://m.wap.ghtkgg.cn/jnews/4460.htm
- http://m.wap.ghtkgg.cn/jnews/5205.htm
- http://m.wap.ghtkgg.cn/jnews/814359.htm
- http://m.wap.ghtkgg.cn/jnews/5664.htm
- http://m.wap.ghtkgg.cn/jnews/17390.htm
- http://m.wap.ghtkgg.cn/jnews/5606.htm
- http://m.wap.ghtkgg.cn/jnews/0203149.htm
- http://m.wap.ghtkgg.cn/jnews/237896.htm
- http://m.wap.ghtkgg.cn/jnews/308612.htm
- http://m.wap.ghtkgg.cn/jnews/434867.htm
- http://m.wap.ghtkgg.cn/jnews/2610.htm
- http://m.wap.ghtkgg.cn/jnews/7461.htm
- http://m.wap.ghtkgg.cn/jnews/2779.htm
- http://m.wap.ghtkgg.cn/jnews/9293.htm
- http://m.wap.ghtkgg.cn/jnews/0861.htm
- http://m.wap.ghtkgg.cn/jnews/4569.htm
- http://m.wap.ghtkgg.cn/jnews/7444454.htm
- http://m.wap.ghtkgg.cn/jnews/0373382.htm
- http://m.wap.ghtkgg.cn/jnews/965652.htm
- http://m.wap.ghtkgg.cn/jnews/645938.htm
- http://m.wap.ghtkgg.cn/jnews/63638.htm
- http://m.wap.ghtkgg.cn/jnews/1621386.htm
- http://m.wap.ghtkgg.cn/jnews/5243598.htm
- http://m.wap.ghtkgg.cn/jnews/0496831.htm
- http://m.wap.ghtkgg.cn/jnews/4254535.htm
- http://m.wap.ghtkgg.cn/jnews/2351905.htm
- http://m.wap.ghtkgg.cn/jnews/118806.htm
- http://m.wap.ghtkgg.cn/jnews/524041.htm
- http://m.wap.ghtkgg.cn/jnews/961596.htm
- http://m.wap.ghtkgg.cn/jnews/7631.htm
- http://m.wap.ghtkgg.cn/jnews/2035.htm
- http://m.wap.ghtkgg.cn/jnews/7954458.htm
- http://m.wap.ghtkgg.cn/jnews/0061.htm
- http://m.wap.ghtkgg.cn/jnews/1111803.htm
- http://m.wap.ghtkgg.cn/jnews/3969.htm
- http://m.wap.ghtkgg.cn/jnews/304503.htm
- http://m.wap.ghtkgg.cn/jnews/678348.htm
- http://m.wap.ghtkgg.cn/jnews/7415.htm
- http://m.wap.ghtkgg.cn/jnews/04987.htm
- http://m.wap.ghtkgg.cn/jnews/245462.htm
- http://m.wap.ghtkgg.cn/jnews/7483.htm
- http://m.wap.ghtkgg.cn/jnews/3617.htm
- http://m.wap.ghtkgg.cn/jnews/5178.htm
- http://m.wap.ghtkgg.cn/jnews/315399.htm
- http://m.wap.ghtkgg.cn/jnews/2389906.htm
- http://m.wap.ghtkgg.cn/jnews/9404.htm
- http://m.wap.ghtkgg.cn/jnews/9306415.htm
- http://m.wap.ghtkgg.cn/jnews/58047.htm
- http://m.wap.ghtkgg.cn/jnews/620204.htm
- http://m.wap.ghtkgg.cn/jnews/8412.htm
- http://m.wap.ghtkgg.cn/jnews/17464.htm
- http://m.wap.ghtkgg.cn/jnews/252489.htm
- http://m.wap.ghtkgg.cn/jnews/1690.htm
- http://m.wap.ghtkgg.cn/jnews/48728.htm
- http://m.wap.ghtkgg.cn/jnews/3195689.htm
- http://m.wap.ghtkgg.cn/jnews/4469.htm
- http://m.wap.ghtkgg.cn/jnews/0608863.htm
- http://m.wap.ghtkgg.cn/jnews/0077.htm
- http://m.wap.ghtkgg.cn/jnews/27621.htm
- http://m.wap.ghtkgg.cn/jnews/830339.htm
- http://m.wap.ghtkgg.cn/jnews/5271004.htm
- http://m.wap.ghtkgg.cn/jnews/08361.htm
- http://m.wap.ghtkgg.cn/jnews/54634.htm
- http://m.wap.ghtkgg.cn/jnews/272266.htm
- http://m.wap.ghtkgg.cn/jnews/146110.htm
- http://m.wap.ghtkgg.cn/jnews/0974939.htm
- http://m.wap.ghtkgg.cn/jnews/0475532.htm
- http://m.wap.ghtkgg.cn/jnews/363325.htm
- http://m.wap.ghtkgg.cn/jnews/3095574.htm
- http://m.wap.ghtkgg.cn/jnews/288127.htm
- http://m.wap.ghtkgg.cn/jnews/27631.htm
- http://m.wap.ghtkgg.cn/jnews/8849716.htm
- http://m.wap.ghtkgg.cn/jnews/4359.htm
- http://m.wap.ghtkgg.cn/jnews/14375.htm
- http://m.wap.ghtkgg.cn/jnews/953941.htm
- http://m.wap.ghtkgg.cn/jnews/514193.htm
- http://m.wap.ghtkgg.cn/jnews/8007.htm
- http://m.wap.ghtkgg.cn/jnews/3971628.htm
- http://m.wap.ghtkgg.cn/jnews/551316.htm
- http://m.wap.ghtkgg.cn/jnews/53587.htm
- http://m.wap.ghtkgg.cn/jnews/6017.htm
- http://m.wap.ghtkgg.cn/jnews/09319.htm
- http://m.wap.ghtkgg.cn/jnews/37432.htm
- http://m.wap.ghtkgg.cn/jnews/8713.htm
- http://m.wap.ghtkgg.cn/jnews/492175.htm
- http://m.wap.ghtkgg.cn/jnews/8411010.htm
- http://m.wap.ghtkgg.cn/jnews/060313.htm
- http://m.wap.ghtkgg.cn/jnews/70205.htm
- http://m.wap.ghtkgg.cn/jnews/45162.htm
- http://m.wap.ghtkgg.cn/jnews/496943.htm
- http://m.wap.ghtkgg.cn/jnews/701626.htm
- http://m.wap.ghtkgg.cn/jnews/9356681.htm
- http://m.wap.ghtkgg.cn/jnews/315973.htm
- http://m.wap.ghtkgg.cn/jnews/0349.htm
- http://m.wap.ghtkgg.cn/jnews/694616.htm
- http://m.wap.ghtkgg.cn/jnews/25395.htm
- http://m.wap.ghtkgg.cn/jnews/647102.htm
- http://m.wap.ghtkgg.cn/jnews/413047.htm
- http://m.wap.ghtkgg.cn/jnews/2518.htm
- http://m.wap.ghtkgg.cn/jnews/8407694.htm
- http://m.wap.ghtkgg.cn/jnews/9415807.htm
- http://m.wap.ghtkgg.cn/jnews/160000.htm
- http://m.wap.ghtkgg.cn/jnews/571641.htm
- http://m.wap.ghtkgg.cn/jnews/3038.htm
- http://m.wap.ghtkgg.cn/jnews/6161260.htm
- http://m.wap.ghtkgg.cn/jnews/6140267.htm
- http://m.wap.ghtkgg.cn/jnews/71122.htm
- http://m.wap.ghtkgg.cn/jnews/5117668.htm
- http://m.wap.ghtkgg.cn/jnews/5760108.htm
- http://m.wap.ghtkgg.cn/jnews/974053.htm
- http://m.wap.ghtkgg.cn/jnews/53550.htm
- http://m.wap.ghtkgg.cn/jnews/39762.htm
- http://m.wap.ghtkgg.cn/jnews/17232.htm
- http://m.wap.ghtkgg.cn/jnews/56784.htm
- http://m.wap.ghtkgg.cn/jnews/68212.htm
- http://m.wap.ghtkgg.cn/jnews/516287.htm
- http://m.wap.ghtkgg.cn/jnews/9827.htm
- http://m.wap.ghtkgg.cn/jnews/309699.htm
- http://m.wap.ghtkgg.cn/jnews/47951.htm
- http://m.wap.ghtkgg.cn/jnews/020967.htm
- http://m.wap.ghtkgg.cn/jnews/5065416.htm
- http://m.wap.ghtkgg.cn/jnews/480729.htm
- http://m.wap.ghtkgg.cn/jnews/664126.htm
- http://m.wap.ghtkgg.cn/jnews/620323.htm
- http://m.wap.ghtkgg.cn/jnews/1059512.htm
- http://m.wap.ghtkgg.cn/jnews/6986.htm
- http://m.wap.ghtkgg.cn/jnews/644443.htm
- http://m.wap.ghtkgg.cn/jnews/2866.htm
- http://m.wap.ghtkgg.cn/jnews/3964.htm
- http://m.wap.ghtkgg.cn/jnews/8031.htm
- http://m.wap.ghtkgg.cn/jnews/620381.htm
- http://m.wap.ghtkgg.cn/jnews/3792.htm
- http://m.wap.ghtkgg.cn/jnews/889481.htm
- http://m.wap.ghtkgg.cn/jnews/5767333.htm
- http://m.wap.ghtkgg.cn/jnews/2186.htm
- http://m.wap.ghtkgg.cn/jnews/15423.htm
- http://m.wap.ghtkgg.cn/jnews/5577.htm

## 项目结构

```
jnews-link-aggregator/
├── docs/                                 # 文档根目录，存放所有 Markdown 文档
│   ├── index.md                          # 项目主页，即 README 的内容副本
│   ├── resources/                        # 资源子目录，按批次存放 URL 列表
│   │   ├── batch-164.md                  # 第 164 批链接明细，即当前资源列表
│   │   └── batch-index.md                # 批次索引，记录各批次范围与状态
│   ├── guides/                           # 使用指南目录
│   │   ├── quick-start.md                # 快速上手教程，扩展快速开始章节
│   │   └── advanced-usage.md             # 高级用法，包含批量导出与检查脚本
│   └── assets/                           # 静态资源目录
│       └── stylesheets/                  # 自定义样式文件
│           └── extra.css                 # 覆盖 MkDocs 默认样式的补充规则
├── scripts/                              # 辅助脚本目录
│   ├── validate-urls.py                  # 验证链接可访问性的 Python 脚本
│   ├── batch-extract.sh                  # 从 Markdown 中提取所有 URL 的 Shell 脚本
│   └── generate-toc.py                   # 自动生成目录树的辅助工具
├── tests/                                # 测试目录
│   ├── test_urls.py                      # 单元测试：检查 URL 格式合法性
│   └── test_structure.py                 # 单元测试：验证目录结构完整性
├── mkdocs.yml                            # MkDocs 站点配置文件，定义导航与主题
├── requirements.txt                      # Python 依赖清单，用于 mkdocs 环境
├── package.json                          # Node.js 依赖清单（如使用 markdown-server）
├── .gitignore                            # Git 忽略规则，排除临时文件与缓存
└── LICENSE                               # MIT 许可证文件
```

## 贡献指南

1. 提交链接更新或错误修正时，请先在 Issues 中创建对应议题，说明修改原因与影响范围，等待维护者确认后再发起 Pull Request。

2. 所有 Pull Request 必须基于 develop 分支创建，提交前请运行本地验证脚本确保链接格式未被破坏，并更新相关文档中的批次说明。

3. 若发现资源列表中存在失效链接，请在 Issue 中提供具体 URL 以及返回的 HTTP 状态码，便于维护者核实与标记。

4. 对于新增功能或脚本改进，请补充对应的单元测试用例，确保测试覆盖率达到 80% 以上。

5. 文档类修改（如错别字修正、排版优化）可直接提交 Pull Request 至 main 分支，无需预先创建 Issue，但需在 PR 描述中注明修改类型为文档。

## 常见问题

**问：资源列表中的 URL 无法直接点击访问，如何处理？**

答：本项目有意将所有 URL 保留为纯文本字符串，不添加 markdown 超链接语法，以确保原始数据不被篡改。用户如需访问，可直接复制链接至浏览器地址栏，或使用脚本批量提取后通过 curl、wget 等工具进行请求。

**问：某个链接返回 404 或无法打开，项目会对其进行更新吗？**

答：本项目仅提供链接归档与索引功能，并不维护原始新闻内容的可用性。若发现大量链接失效，可在 Issues 中反馈，维护者会根据反馈情况在后续批次中标注失效链接或调整收录策略。

**问：为什么所有链接都来自同一个域名下的 jnews 路径？**

答：本项目专注于特定来源的结构化链接整理，旨在为固定数据源的批量处理提供便利。不同批次均来自同一站点的 jnews 目录，以保证数据格式的一致性和采集规则的稳定性。

## 许可证

MIT License

Copyright (c) 2026 JNews Link Aggregator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
