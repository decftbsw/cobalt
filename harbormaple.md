# Oexnr Resource Index

Oexnr Resource Index 是一个面向技术内容聚合与外部链接导航的开源项目。该项目定位为高密度信息索引层，用于对分散于多个子域名或内容路径下的文章、公告与新闻条目进行统一化整理与结构化呈现。项目本身不存储原始内容，而是以外部链接为数据主体，通过标准化的分类与编号机制，提供快速检索与批量访问能力。

目标用户包括技术调研人员、内容运营者、信息归档工程师以及需要定期查阅大量外链资源的开发人员。Oexnr Resource Index 解决的核心问题是：当大量有价值的外部内容散落在同一域名的不同路径下时，如何通过一个轻量级索引项目实现高效管理与引用。

## 功能概览

- **统一资源索引**：将所有外部链接以唯一编号方式纳入索引体系，支持快速按 ID 查找对应资源。
- **分类标签支持**：每个资源条目可关联多个分类标签，方便按主题或类型筛选。
- **元数据提取占位**：项目结构预留元数据字段，便于后续扩展标题、发布时间、摘要等信息。
- **批量导入与更新**：支持通过脚本批量导入新链接，自动去重并生成编号。
- **静态站点生成适配**：项目输出为纯 Markdown 与结构化数据，可配合 Hugo、VuePress 等工具生成静态导航站点。
- **链接状态检查**：内置链接可达性检测脚本，可定期检查资源是否可访问。
- **访问统计记录**：通过外部分析工具或自建日志模块，记录资源被引用的频次。
- **多级目录组织**：按年份、主题或来源层级对链接进行归类，避免单一大列表造成的检索困难。

## 应用场景

- **技术团队内部知识归档**：团队可将日常阅读的优质技术文章、官方公告通过本索引项目集中管理，避免链接散落在聊天记录或邮件中。
- **开源项目外部依赖引用清单**：当开源项目需要引用大量外部参考资料或数据源时，可使用本索引统一声明依赖资源的来源地址。
- **内容聚合站点后端数据源**：内容聚合类网站可使用本索引作为原始链接池，定时抓取并展示最新条目摘要。
- **运营活动素材管理**：运营人员可将多批次活动相关的新闻稿、宣传页面链接归入不同目录，便于复盘与交接。
- **个人书签系统替代方案**：开发者可用该索引替代浏览器书签，配合 Git 进行版本控制，实现跨设备同步。

## 快速开始

以下指令演示如何从仓库克隆项目、安装基础依赖并启动本地预览服务。

```bash
git clone https://github.com/your-org/oexnr-resource-index.git
cd oexnr-resource-index
npm install
npm run build
```

执行完成后，项目将在 `dist` 目录下生成静态索引页面，可使用任意 HTTP 服务器进行本地预览，例如：

```bash
npx serve dist
```

## 安装要求

| 依赖 | 必需 | 说明 |
|------|------|------|
| Node.js 18.x 或更高 | 是 | 用于运行构建脚本与依赖管理 |
| npm 9.x 或更高 | 是 | 用于安装项目依赖包 |
| Git 2.30 或更高 | 是 | 用于克隆仓库及版本控制操作 |
| 现代浏览器（Chrome/Firefox/Edge） | 否 | 仅用于预览生成的静态页面 |
| Python 3.9 或更高 | 否 | 若使用链接状态检查脚本（可选） |
| 磁盘空间 ≥ 50 MB | 是 | 存储项目文件及构建产物 |
| 网络连接 | 是 | 用于访问索引中的外部链接 |
| 操作系统：Linux/macOS/Windows | 否 | 项目跨平台，无特定系统要求 |
| Make 或同类构建工具 | 否 | 若使用 Makefile 进行任务自动化 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ | 如何添加资源、如何分类、如何生成索引页面 |
| 开发者指南 | docs/developer-guide/ | 如何扩展脚本、如何修改构建流程、如何提交补丁 |
| 运维参考 | docs/operations/ | 如何部署静态站点、如何配置自动检查、如何处理失效链接 |
| 设计说明 | docs/design/ | 索引编号规则、元数据格式、目录结构的设计考量 |
| 更新日志 | CHANGELOG.md | 每个版本新增了哪些功能、修复了哪些缺陷 |

## 资源列表

- http://m.blog.oexnr.cn/snews/392179.htm
- http://m.blog.oexnr.cn/snews/1966.htm
- http://m.blog.oexnr.cn/snews/17547.htm
- http://m.blog.oexnr.cn/snews/940839.htm
- http://m.blog.oexnr.cn/snews/2430.htm
- http://m.blog.oexnr.cn/snews/3212706.htm
- http://m.blog.oexnr.cn/snews/5860729.htm
- http://m.blog.oexnr.cn/snews/845925.htm
- http://m.blog.oexnr.cn/snews/338441.htm
- http://m.blog.oexnr.cn/snews/73795.htm
- http://m.blog.oexnr.cn/snews/4747340.htm
- http://m.blog.oexnr.cn/snews/0113472.htm
- http://m.blog.oexnr.cn/snews/7392.htm
- http://m.blog.oexnr.cn/snews/4010324.htm
- http://m.blog.oexnr.cn/snews/75308.htm
- http://m.blog.oexnr.cn/snews/0234.htm
- http://m.blog.oexnr.cn/snews/6571468.htm
- http://m.blog.oexnr.cn/snews/9595535.htm
- http://m.blog.oexnr.cn/snews/5943.htm
- http://m.blog.oexnr.cn/snews/28076.htm
- http://m.blog.oexnr.cn/snews/55595.htm
- http://m.blog.oexnr.cn/snews/011577.htm
- http://m.blog.oexnr.cn/snews/58640.htm
- http://m.blog.oexnr.cn/snews/549233.htm
- http://m.blog.oexnr.cn/snews/82519.htm
- http://m.blog.oexnr.cn/snews/8822.htm
- http://m.blog.oexnr.cn/snews/1309.htm
- http://m.blog.oexnr.cn/snews/4850764.htm
- http://m.blog.oexnr.cn/snews/4877402.htm
- http://m.blog.oexnr.cn/snews/0792195.htm
- http://m.blog.oexnr.cn/snews/4738.htm
- http://m.blog.oexnr.cn/snews/969543.htm
- http://m.blog.oexnr.cn/snews/5083078.htm
- http://m.blog.oexnr.cn/snews/169880.htm
- http://m.blog.oexnr.cn/snews/4958006.htm
- http://m.blog.oexnr.cn/snews/3978313.htm
- http://m.blog.oexnr.cn/snews/76720.htm
- http://m.blog.oexnr.cn/snews/938519.htm
- http://m.blog.oexnr.cn/snews/423222.htm
- http://m.blog.oexnr.cn/snews/13717.htm
- http://m.blog.oexnr.cn/snews/6757.htm
- http://m.blog.oexnr.cn/snews/3338166.htm
- http://m.blog.oexnr.cn/snews/54887.htm
- http://m.blog.oexnr.cn/snews/10415.htm
- http://m.blog.oexnr.cn/snews/255957.htm
- http://m.blog.oexnr.cn/snews/291384.htm
- http://m.blog.oexnr.cn/snews/53158.htm
- http://m.blog.oexnr.cn/snews/6670.htm
- http://m.blog.oexnr.cn/snews/2413.htm
- http://m.blog.oexnr.cn/snews/6996320.htm
- http://m.blog.oexnr.cn/snews/014724.htm
- http://m.blog.oexnr.cn/snews/0183.htm
- http://m.blog.oexnr.cn/snews/9215.htm
- http://m.blog.oexnr.cn/snews/5235985.htm
- http://m.blog.oexnr.cn/snews/5870865.htm
- http://m.blog.oexnr.cn/snews/522107.htm
- http://m.blog.oexnr.cn/snews/15306.htm
- http://m.blog.oexnr.cn/snews/8631.htm
- http://m.blog.oexnr.cn/snews/418574.htm
- http://m.blog.oexnr.cn/snews/3712007.htm
- http://m.blog.oexnr.cn/snews/9936.htm
- http://m.blog.oexnr.cn/snews/6818577.htm
- http://m.blog.oexnr.cn/snews/8496708.htm
- http://m.blog.oexnr.cn/snews/892722.htm
- http://m.blog.oexnr.cn/snews/6989512.htm
- http://m.blog.oexnr.cn/snews/92389.htm
- http://m.blog.oexnr.cn/snews/41398.htm
- http://m.blog.oexnr.cn/snews/56385.htm
- http://m.blog.oexnr.cn/snews/0791.htm
- http://m.blog.oexnr.cn/snews/5007684.htm
- http://m.blog.oexnr.cn/snews/9932.htm
- http://m.blog.oexnr.cn/snews/0676.htm
- http://m.blog.oexnr.cn/snews/1819.htm
- http://m.blog.oexnr.cn/snews/4460435.htm
- http://m.blog.oexnr.cn/snews/3280.htm
- http://m.blog.oexnr.cn/snews/1029.htm
- http://m.blog.oexnr.cn/snews/62115.htm
- http://m.blog.oexnr.cn/snews/942355.htm
- http://m.blog.oexnr.cn/snews/257322.htm
- http://m.blog.oexnr.cn/snews/455277.htm
- http://m.blog.oexnr.cn/snews/284724.htm
- http://m.blog.oexnr.cn/snews/802095.htm
- http://m.blog.oexnr.cn/snews/807080.htm
- http://m.blog.oexnr.cn/snews/3001.htm
- http://m.blog.oexnr.cn/snews/089381.htm
- http://m.blog.oexnr.cn/snews/12074.htm
- http://m.blog.oexnr.cn/snews/341884.htm
- http://m.blog.oexnr.cn/snews/620340.htm
- http://m.blog.oexnr.cn/snews/7711.htm
- http://m.blog.oexnr.cn/snews/48466.htm
- http://m.blog.oexnr.cn/snews/081683.htm
- http://m.blog.oexnr.cn/snews/384515.htm
- http://m.blog.oexnr.cn/snews/8714384.htm
- http://m.blog.oexnr.cn/snews/85883.htm
- http://m.blog.oexnr.cn/snews/37349.htm
- http://m.blog.oexnr.cn/snews/0399028.htm
- http://m.blog.oexnr.cn/snews/82253.htm
- http://m.blog.oexnr.cn/snews/989589.htm
- http://m.blog.oexnr.cn/snews/72654.htm
- http://m.blog.oexnr.cn/snews/4005352.htm
- http://m.blog.oexnr.cn/snews/76220.htm
- http://m.blog.oexnr.cn/snews/7262518.htm
- http://m.blog.oexnr.cn/snews/750311.htm
- http://m.blog.oexnr.cn/snews/5720.htm
- http://m.blog.oexnr.cn/snews/5219178.htm
- http://m.blog.oexnr.cn/snews/8342.htm
- http://m.blog.oexnr.cn/snews/7814.htm
- http://m.blog.oexnr.cn/snews/509037.htm
- http://m.blog.oexnr.cn/snews/406588.htm
- http://m.blog.oexnr.cn/snews/7298.htm
- http://m.blog.oexnr.cn/snews/45057.htm
- http://m.blog.oexnr.cn/snews/91879.htm
- http://m.blog.oexnr.cn/snews/8010498.htm
- http://m.blog.oexnr.cn/snews/42826.htm
- http://m.blog.oexnr.cn/snews/5276898.htm
- http://m.blog.oexnr.cn/snews/388778.htm
- http://m.blog.oexnr.cn/snews/3820.htm
- http://m.blog.oexnr.cn/snews/02614.htm
- http://m.blog.oexnr.cn/snews/9023175.htm
- http://m.blog.oexnr.cn/snews/509180.htm
- http://m.blog.oexnr.cn/snews/30601.htm
- http://m.blog.oexnr.cn/snews/2328.htm
- http://m.blog.oexnr.cn/snews/2801281.htm
- http://m.blog.oexnr.cn/snews/4164643.htm
- http://m.blog.oexnr.cn/snews/442308.htm
- http://m.blog.oexnr.cn/snews/693165.htm
- http://m.blog.oexnr.cn/snews/4067668.htm
- http://m.blog.oexnr.cn/snews/6759.htm
- http://m.blog.oexnr.cn/snews/8863556.htm
- http://m.blog.oexnr.cn/snews/0458533.htm
- http://m.blog.oexnr.cn/snews/770119.htm
- http://m.blog.oexnr.cn/snews/55117.htm
- http://m.blog.oexnr.cn/snews/75932.htm
- http://m.blog.oexnr.cn/snews/2571568.htm
- http://m.blog.oexnr.cn/snews/2039.htm
- http://m.blog.oexnr.cn/snews/49099.htm
- http://m.blog.oexnr.cn/snews/7882.htm
- http://m.blog.oexnr.cn/snews/8640580.htm
- http://m.blog.oexnr.cn/snews/6973.htm
- http://m.blog.oexnr.cn/snews/49683.htm
- http://m.blog.oexnr.cn/snews/0809358.htm
- http://m.blog.oexnr.cn/snews/300924.htm
- http://m.blog.oexnr.cn/snews/538755.htm
- http://m.blog.oexnr.cn/snews/857646.htm
- http://m.blog.oexnr.cn/snews/58483.htm
- http://m.blog.oexnr.cn/snews/425849.htm
- http://m.blog.oexnr.cn/snews/804242.htm
- http://m.blog.oexnr.cn/snews/9692.htm
- http://m.blog.oexnr.cn/snews/65729.htm
- http://m.blog.oexnr.cn/snews/66545.htm
- http://m.blog.oexnr.cn/snews/9613.htm
- http://m.blog.oexnr.cn/snews/1248932.htm
- http://m.blog.oexnr.cn/snews/0592.htm
- http://m.blog.oexnr.cn/snews/9379990.htm
- http://m.blog.oexnr.cn/snews/801005.htm
- http://m.blog.oexnr.cn/snews/6221.htm
- http://m.blog.oexnr.cn/snews/21327.htm
- http://m.blog.oexnr.cn/snews/9631492.htm
- http://m.blog.oexnr.cn/snews/27555.htm
- http://m.blog.oexnr.cn/snews/8041.htm
- http://m.blog.oexnr.cn/snews/2684321.htm
- http://m.blog.oexnr.cn/snews/1924.htm
- http://m.blog.oexnr.cn/snews/5730.htm
- http://m.blog.oexnr.cn/snews/0258972.htm
- http://m.blog.oexnr.cn/snews/04064.htm
- http://m.blog.oexnr.cn/snews/458017.htm
- http://m.blog.oexnr.cn/snews/5900.htm
- http://m.blog.oexnr.cn/snews/104005.htm
- http://m.blog.oexnr.cn/snews/057036.htm
- http://m.blog.oexnr.cn/snews/03639.htm
- http://m.blog.oexnr.cn/snews/25656.htm
- http://m.blog.oexnr.cn/snews/3469951.htm
- http://m.blog.oexnr.cn/snews/3846168.htm
- http://m.blog.oexnr.cn/snews/1266138.htm
- http://m.blog.oexnr.cn/snews/673203.htm
- http://m.blog.oexnr.cn/snews/8461.htm
- http://m.blog.oexnr.cn/snews/0292399.htm
- http://m.blog.oexnr.cn/snews/66084.htm
- http://m.blog.oexnr.cn/snews/37614.htm
- http://m.blog.oexnr.cn/snews/8859438.htm
- http://m.blog.oexnr.cn/snews/17081.htm
- http://m.blog.oexnr.cn/snews/65588.htm
- http://m.blog.oexnr.cn/snews/3146913.htm
- http://m.blog.oexnr.cn/snews/8788744.htm
- http://m.blog.oexnr.cn/snews/2784.htm
- http://m.blog.oexnr.cn/snews/5829500.htm
- http://m.blog.oexnr.cn/snews/38164.htm
- http://m.blog.oexnr.cn/snews/17945.htm
- http://m.blog.oexnr.cn/snews/304071.htm
- http://m.blog.oexnr.cn/snews/301251.htm
- http://m.blog.oexnr.cn/snews/85212.htm
- http://m.blog.oexnr.cn/snews/17347.htm
- http://m.blog.oexnr.cn/snews/17037.htm
- http://m.blog.oexnr.cn/snews/70834.htm
- http://m.blog.oexnr.cn/snews/1667.htm
- http://m.blog.oexnr.cn/snews/771601.htm
- http://m.blog.oexnr.cn/snews/4391.htm
- http://m.blog.oexnr.cn/snews/256062.htm
- http://m.blog.oexnr.cn/snews/65452.htm
- http://m.blog.oexnr.cn/snews/4072.htm
- http://m.blog.oexnr.cn/snews/9426598.htm
- http://m.blog.oexnr.cn/snews/27613.htm
- http://m.blog.oexnr.cn/snews/50209.htm
- http://m.blog.oexnr.cn/snews/59211.htm
- http://m.blog.oexnr.cn/snews/281321.htm
- http://m.blog.oexnr.cn/snews/8210.htm
- http://m.blog.oexnr.cn/snews/2844933.htm
- http://m.blog.oexnr.cn/snews/542877.htm
- http://m.blog.oexnr.cn/snews/4727760.htm
- http://m.blog.oexnr.cn/snews/22283.htm
- http://m.blog.oexnr.cn/snews/48325.htm
- http://m.blog.oexnr.cn/snews/4163.htm
- http://m.blog.oexnr.cn/snews/57467.htm
- http://m.blog.oexnr.cn/snews/9511.htm
- http://m.blog.oexnr.cn/snews/378269.htm
- http://m.blog.oexnr.cn/snews/3765.htm
- http://m.blog.oexnr.cn/snews/4420762.htm
- http://m.blog.oexnr.cn/snews/0196078.htm
- http://m.blog.oexnr.cn/snews/7700064.htm
- http://m.blog.oexnr.cn/snews/9766741.htm
- http://m.blog.oexnr.cn/snews/339895.htm
- http://m.blog.oexnr.cn/snews/85477.htm
- http://m.blog.oexnr.cn/snews/7940001.htm
- http://m.blog.oexnr.cn/snews/762172.htm
- http://m.blog.oexnr.cn/snews/496813.htm
- http://m.blog.oexnr.cn/snews/684939.htm
- http://m.blog.oexnr.cn/snews/737090.htm
- http://m.blog.oexnr.cn/snews/66603.htm
- http://m.blog.oexnr.cn/snews/617108.htm
- http://m.blog.oexnr.cn/snews/330040.htm
- http://m.blog.oexnr.cn/snews/170077.htm
- http://m.blog.oexnr.cn/snews/0370.htm
- http://m.blog.oexnr.cn/snews/4658.htm
- http://m.blog.oexnr.cn/snews/4109148.htm
- http://m.blog.oexnr.cn/snews/958375.htm
- http://m.blog.oexnr.cn/snews/5387.htm
- http://m.blog.oexnr.cn/snews/313382.htm
- http://m.blog.oexnr.cn/snews/8459115.htm
- http://m.blog.oexnr.cn/snews/65498.htm
- http://m.blog.oexnr.cn/snews/875588.htm
- http://m.blog.oexnr.cn/snews/5879492.htm
- http://m.blog.oexnr.cn/snews/8615544.htm
- http://m.blog.oexnr.cn/snews/46847.htm
- http://m.blog.oexnr.cn/snews/23137.htm
- http://m.blog.oexnr.cn/snews/492714.htm
- http://m.blog.oexnr.cn/snews/9564616.htm
- http://m.blog.oexnr.cn/snews/520310.htm
- http://m.blog.oexnr.cn/snews/14000.htm
- http://m.blog.oexnr.cn/snews/067001.htm
- http://m.blog.oexnr.cn/snews/02890.htm
- http://m.blog.oexnr.cn/snews/47515.htm
- http://m.blog.oexnr.cn/snews/4225.htm
- http://m.blog.oexnr.cn/snews/565891.htm
- http://m.blog.oexnr.cn/snews/499111.htm
- http://m.blog.oexnr.cn/snews/191789.htm
- http://m.blog.oexnr.cn/snews/890664.htm
- http://m.blog.oexnr.cn/snews/086947.htm
- http://m.blog.oexnr.cn/snews/8157291.htm
- http://m.blog.oexnr.cn/snews/116171.htm
- http://m.blog.oexnr.cn/snews/475303.htm
- http://m.blog.oexnr.cn/snews/027035.htm
- http://m.blog.oexnr.cn/snews/563476.htm
- http://m.blog.oexnr.cn/snews/8132051.htm
- http://m.blog.oexnr.cn/snews/47984.htm
- http://m.blog.oexnr.cn/snews/866789.htm
- http://m.blog.oexnr.cn/snews/83985.htm
- http://m.blog.oexnr.cn/snews/0548874.htm
- http://m.blog.oexnr.cn/snews/60488.htm
- http://m.blog.oexnr.cn/snews/884803.htm
- http://m.blog.oexnr.cn/snews/15016.htm
- http://m.blog.oexnr.cn/snews/1976005.htm
- http://m.blog.oexnr.cn/snews/45379.htm
- http://m.blog.oexnr.cn/snews/6664.htm
- http://m.blog.oexnr.cn/snews/01699.htm
- http://m.blog.oexnr.cn/snews/6279.htm
- http://m.blog.oexnr.cn/snews/6247971.htm
- http://m.blog.oexnr.cn/snews/0465735.htm
- http://m.blog.oexnr.cn/snews/3508.htm
- http://m.blog.oexnr.cn/snews/102196.htm
- http://m.blog.oexnr.cn/snews/131253.htm
- http://m.blog.oexnr.cn/snews/3824051.htm
- http://m.blog.oexnr.cn/snews/985573.htm
- http://m.blog.oexnr.cn/snews/8336143.htm
- http://m.blog.oexnr.cn/snews/4839.htm
- http://m.blog.oexnr.cn/snews/9835501.htm
- http://m.blog.oexnr.cn/snews/03775.htm
- http://m.blog.oexnr.cn/snews/2883.htm
- http://m.blog.oexnr.cn/snews/7551668.htm
- http://m.blog.oexnr.cn/snews/10524.htm
- http://m.blog.oexnr.cn/snews/768559.htm
- http://m.blog.oexnr.cn/snews/180870.htm
- http://m.blog.oexnr.cn/snews/4523.htm
- http://m.blog.oexnr.cn/snews/377369.htm
- http://m.blog.oexnr.cn/snews/959358.htm
- http://m.blog.oexnr.cn/snews/774086.htm
- http://m.blog.oexnr.cn/snews/9522708.htm
- http://m.blog.oexnr.cn/snews/9436.htm
- http://m.blog.oexnr.cn/snews/107492.htm
- http://m.blog.oexnr.cn/snews/8883666.htm
- http://m.blog.oexnr.cn/snews/6901.htm

## 项目结构

项目采用分层目录结构，将索引数据、构建逻辑、文档与输出产物分离。以下为项目核心目录树示意。

```
oexnr-resource-index/
├── data/                           # 原始索引数据目录
│   ├── raw/                        # 原始链接列表，按批次存放
│   │   ├── batch_70.csv            # 第70批次资源（对应本项目）
│   │   └── batch_71.csv            # 后续批次占位
│   ├── parsed/                     # 解析后的结构化数据（JSON）
│   │   ├── index.json              # 全量索引
│   │   └── tags.json               # 标签聚合
│   └── schema/                     # 数据格式定义
│       └── resource.schema.json    # JSON Schema 校验规则
├── scripts/                        # 工具脚本
│   ├── import.js                   # 从 CSV 导入链接
│   ├── validate.js                 # 校验链接格式与可达性
│   ├── build.js                    # 生成静态索引页面
│   └── check-links.py              # Python 编写的链接状态检查
├── docs/                           # 项目文档
│   ├── user-guide/                 # 用户手册
│   ├── developer-guide/            # 开发者指南
│   ├── operations/                 # 运维参考
│   └── design/                     # 设计说明
├── templates/                      # 页面模板（针对静态生成）
│   ├── index.template.html         # 首页模板
│   └── detail.template.html        # 详情页模板
├── dist/                           # 构建输出目录（生成后出现）
├── tests/                          # 单元测试与集成测试
│   ├── unit/                       # 单元测试用例
│   └── fixtures/                   # 测试用固定数据
├── .github/                        # GitHub 配置
│   └── workflows/                  # CI/CD 流水线
│       └── ci.yml                  # 持续集成配置
├── package.json                    # npm 依赖声明
├── package-lock.json               # 依赖锁定文件
├── README.md                       # 项目说明（本文件）
├── CHANGELOG.md                    # 版本更新日志
├── CONTRIBUTING.md                 # 贡献指南详情
└── LICENSE                         # MIT 许可证
```

## 贡献指南

1. 阅读 CONTRIBUTING.md 文件了解完整的贡献流程与行为准则。
2. 在 Issue 列表中认领未分配的任务，或提交新 Issue 描述建议变更。
3. 从 main 分支创建新的功能分支，命名格式为 feature/描述 或 fix/描述。
4. 完成代码或文档修改后，确保所有测试通过，并更新 CHANGELOG.md 中对应条目。
5. 发起 Pull Request，并至少邀请一位维护者进行代码审查。审查通过后由维护者合并。

## 常见问题

**问：索引中的链接如果失效了怎么办？**

项目提供了链接检查脚本 scripts/check-links.py，可定期运行以检测所有外链的 HTTP 状态。发现失效链接后，请在 data/raw 对应批次文件中标注失效状态，或提交 Issue 通知维护者处理。对于持续失效的链接，将视情况在下一次批次更新中移出索引。

**问：如何提交新的链接批次？**

使用 scripts/import.js 工具，传入 CSV 或纯文本列表文件即可导入。导入后系统会自动去重并分配编号。新批次会合并到全量索引中，并重新生成 dist 目录下的静态页面。

**问：项目是否支持非 HTTP 协议的资源？**

当前版本仅支持 HTTP/HTTPS 协议链接。对于 FTP、mailto 或 magnet 等协议暂不纳入索引范围。如需支持其他协议，可在 schema/resource.schema.json 中扩展 protocol 枚举值并提交功能请求。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
