# NewsAggregatorX

NewsAggregatorX 是一个面向移动端的高性能新闻外链聚合与导航系统，专注于从特定数据源（oexnr.cn）批量采集、归档和展示新闻条目。该项目定位为技术资源型外链汇总站，服务于需要快速查阅和分类管理大量新闻链接的开发者、数据分析师及内容运营人员。通过结构化的目录树、自动化的链接巡检和静态站点生成机制，NewsAggregatorX 将原始散乱的 .htm 外链转化为可检索、可分类、可追踪的知识库。

本项目基于 Node.js 和 TypeScript 构建，核心功能包括外链抓取、元数据提取、去重校验、Markdown 文档生成和静态站点部署。项目本身不存储任何新闻内容，仅提供链接导航与分类索引，完全遵守 robots.txt 协议，适合用于个人学习、内部知识管理或开源情报（OSINT）场景下的外链梳理。

## 功能概览

**批量外链导入** 支持从文本文件、CSV 或 JSON 数据源批量导入 URL，自动解析文件名中的数字 ID 作为唯一索引。

**智能元数据提取** 对每个 .htm 链接尝试发起 HEAD 请求获取 Content-Type 和 Last-Modified 头，并依据文件名前缀生成分类标签（如 nnews 映射为 "国内快讯"）。

**分类索引生成** 根据 URL 路径中的目录层级（如 /nnews/）自动建立分类目录，并在 README 中生成分类统计表。

**链接可达性巡检** 内置定时任务或手动触发模式，对全部外链进行 HTTP 状态码检查，标记失效链接并生成巡检报告。

**静态站点编译** 将外链列表、分类索引、巡检报告编译为纯静态 HTML 页面，适配移动端浏览，无 JavaScript 依赖。

**Markdown 文档流输出** 所有聚合结果最终输出为结构化的 Markdown 文件，便于版本管理、全文检索和二次加工。

**标签与全文检索** 为每条链接生成基于文件名数字 ID 和路径关键词的标签体系，支持简单的 grep 检索。

**增量更新机制** 支持通过比对 Last-Modified 时间或 ETag 实现增量拉取，避免全量重复处理。

## 应用场景

**个人知识库外链归档** 研究人员或开发者可将 NewsAggregatorX 作为每日外链收集工具，将来自特定源头的散乱链接整理为带时间戳的分类文档，便于后续引用和回溯。

**数据源健康度监控** 运维人员可利用链接巡检功能，定期扫描大量外链的有效性，及时发现源站 404 或 500 错误，辅助判断数据源可用性。

**静态资讯导航站构建** 内容运营人员可基于 NewsAggregatorX 生成的静态页面，快速搭建一个轻量级、按分类索引的新闻外链导航站，部署到 CDN 或对象存储上供团队内部使用。

**开源情报（OSINT）预处理** 安全分析人员可借助该工具对特定域名下的公开 .htm 文件进行批量采集和元数据归档，为后续的情报分析提供结构化输入数据。

## 快速开始

以下步骤帮助您在本地环境快速启动 NewsAggregatorX 实例。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/news-aggregator-x.git
cd news-aggregator-x

# 安装项目依赖（使用 npm）
npm install

# 执行外链导入与聚合编译（默认读取 ./data/links.txt）
npm run build

# 启动本地预览服务（默认端口 3000）
npm run serve
```

执行 `npm run build` 后，项目会读取 `./data/links.txt` 中的 URL 列表（每行一个），生成分类索引、巡检报告，并将最终文档输出至 `./dist` 目录。您可以通过 `npm run serve` 启动一个简单的 HTTP 服务器预览生成的静态站点。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | >= 18.0.0 | 运行时环境，要求支持原生 fetch API 和 ES Module |
| npm | >= 8.0.0 | 包管理工具，用于安装项目依赖 |
| TypeScript | >= 4.9.0 | 开发依赖，项目源码使用 TypeScript 编写 |
| Jest | >= 29.0.0 | 可选依赖，用于运行单元测试套件 |
| http-server | >= 14.0.0 | 可选依赖，用于本地预览静态站点 |
| rimraf | >= 5.0.0 | 构建辅助工具，用于清理输出目录 |
| cross-env | >= 7.0.0 | 跨平台环境变量设置工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | ./docs/user-guide.md | 如何配置数据源、如何运行增量更新、如何自定义分类规则 |
| 开发者指南 | ./docs/developer-guide.md | 项目架构设计、核心模块说明、如何扩展新的数据源适配器 |
| API 参考 | ./docs/api-reference.md | 各模块函数签名、参数说明、异常处理规范 |
| 部署指南 | ./docs/deployment-guide.md | 如何部署到 Vercel、Netlify 或自建 Nginx 服务器 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/844413.htm
- http://m.3g.oexnr.cn/nnews/6700992.htm
- http://m.3g.oexnr.cn/nnews/429922.htm
- http://m.3g.oexnr.cn/nnews/3956247.htm
- http://m.3g.oexnr.cn/nnews/978099.htm
- http://m.3g.oexnr.cn/nnews/0024.htm
- http://m.3g.oexnr.cn/nnews/54932.htm
- http://m.3g.oexnr.cn/nnews/107837.htm
- http://m.3g.oexnr.cn/nnews/1779.htm
- http://m.3g.oexnr.cn/nnews/12830.htm
- http://m.3g.oexnr.cn/nnews/0356231.htm
- http://m.3g.oexnr.cn/nnews/2854.htm
- http://m.3g.oexnr.cn/nnews/158806.htm
- http://m.3g.oexnr.cn/nnews/456559.htm
- http://m.3g.oexnr.cn/nnews/270910.htm
- http://m.3g.oexnr.cn/nnews/539317.htm
- http://m.3g.oexnr.cn/nnews/0950.htm
- http://m.3g.oexnr.cn/nnews/2067.htm
- http://m.3g.oexnr.cn/nnews/437292.htm
- http://m.3g.oexnr.cn/nnews/5438.htm
- http://m.3g.oexnr.cn/nnews/7626.htm
- http://m.3g.oexnr.cn/nnews/22627.htm
- http://m.3g.oexnr.cn/nnews/240620.htm
- http://m.3g.oexnr.cn/nnews/59523.htm
- http://m.3g.oexnr.cn/nnews/77991.htm
- http://m.3g.oexnr.cn/nnews/4664.htm
- http://m.3g.oexnr.cn/nnews/5578631.htm
- http://m.3g.oexnr.cn/nnews/384872.htm
- http://m.3g.oexnr.cn/nnews/9545524.htm
- http://m.3g.oexnr.cn/nnews/26326.htm
- http://m.3g.oexnr.cn/nnews/9347410.htm
- http://m.3g.oexnr.cn/nnews/566451.htm
- http://m.3g.oexnr.cn/nnews/5693319.htm
- http://m.3g.oexnr.cn/nnews/5419.htm
- http://m.3g.oexnr.cn/nnews/8643663.htm
- http://m.3g.oexnr.cn/nnews/02886.htm
- http://m.3g.oexnr.cn/nnews/518563.htm
- http://m.3g.oexnr.cn/nnews/9276537.htm
- http://m.3g.oexnr.cn/nnews/33385.htm
- http://m.3g.oexnr.cn/nnews/5149.htm
- http://m.3g.oexnr.cn/nnews/2853.htm
- http://m.3g.oexnr.cn/nnews/3929324.htm
- http://m.3g.oexnr.cn/nnews/361172.htm
- http://m.3g.oexnr.cn/nnews/44120.htm
- http://m.3g.oexnr.cn/nnews/22936.htm
- http://m.3g.oexnr.cn/nnews/548683.htm
- http://m.3g.oexnr.cn/nnews/59354.htm
- http://m.3g.oexnr.cn/nnews/6204562.htm
- http://m.3g.oexnr.cn/nnews/81427.htm
- http://m.3g.oexnr.cn/nnews/49375.htm
- http://m.3g.oexnr.cn/nnews/0105675.htm
- http://m.3g.oexnr.cn/nnews/97455.htm
- http://m.3g.oexnr.cn/nnews/983828.htm
- http://m.3g.oexnr.cn/nnews/58380.htm
- http://m.3g.oexnr.cn/nnews/163765.htm
- http://m.3g.oexnr.cn/nnews/4526863.htm
- http://m.3g.oexnr.cn/nnews/30198.htm
- http://m.3g.oexnr.cn/nnews/2740.htm
- http://m.3g.oexnr.cn/nnews/7885.htm
- http://m.3g.oexnr.cn/nnews/0910.htm
- http://m.3g.oexnr.cn/nnews/237399.htm
- http://m.3g.oexnr.cn/nnews/98098.htm
- http://m.3g.oexnr.cn/nnews/8362891.htm
- http://m.3g.oexnr.cn/nnews/128585.htm
- http://m.3g.oexnr.cn/nnews/6328562.htm
- http://m.3g.oexnr.cn/nnews/98277.htm
- http://m.3g.oexnr.cn/nnews/9030.htm
- http://m.3g.oexnr.cn/nnews/32541.htm
- http://m.3g.oexnr.cn/nnews/853487.htm
- http://m.3g.oexnr.cn/nnews/357871.htm
- http://m.3g.oexnr.cn/nnews/9117605.htm
- http://m.3g.oexnr.cn/nnews/93868.htm
- http://m.3g.oexnr.cn/nnews/031294.htm
- http://m.3g.oexnr.cn/nnews/49602.htm
- http://m.3g.oexnr.cn/nnews/342632.htm
- http://m.3g.oexnr.cn/nnews/2545.htm
- http://m.3g.oexnr.cn/nnews/180782.htm
- http://m.3g.oexnr.cn/nnews/512859.htm
- http://m.3g.oexnr.cn/nnews/0020.htm
- http://m.3g.oexnr.cn/nnews/1964.htm
- http://m.3g.oexnr.cn/nnews/3592.htm
- http://m.3g.oexnr.cn/nnews/79010.htm
- http://m.3g.oexnr.cn/nnews/34865.htm
- http://m.3g.oexnr.cn/nnews/3522.htm
- http://m.3g.oexnr.cn/nnews/32205.htm
- http://m.3g.oexnr.cn/nnews/007276.htm
- http://m.3g.oexnr.cn/nnews/27589.htm
- http://m.3g.oexnr.cn/nnews/105811.htm
- http://m.3g.oexnr.cn/nnews/263676.htm
- http://m.3g.oexnr.cn/nnews/4279237.htm
- http://m.3g.oexnr.cn/nnews/59420.htm
- http://m.3g.oexnr.cn/nnews/74858.htm
- http://m.3g.oexnr.cn/nnews/647914.htm
- http://m.3g.oexnr.cn/nnews/8381723.htm
- http://m.3g.oexnr.cn/nnews/65882.htm
- http://m.3g.oexnr.cn/nnews/0482919.htm
- http://m.3g.oexnr.cn/nnews/1191.htm
- http://m.3g.oexnr.cn/nnews/98040.htm
- http://m.3g.oexnr.cn/nnews/57165.htm
- http://m.3g.oexnr.cn/nnews/8977.htm
- http://m.3g.oexnr.cn/nnews/9069.htm
- http://m.3g.oexnr.cn/nnews/3296.htm
- http://m.3g.oexnr.cn/nnews/1549699.htm
- http://m.3g.oexnr.cn/nnews/47184.htm
- http://m.3g.oexnr.cn/nnews/623199.htm
- http://m.3g.oexnr.cn/nnews/7074734.htm
- http://m.3g.oexnr.cn/nnews/723303.htm
- http://m.3g.oexnr.cn/nnews/146154.htm
- http://m.3g.oexnr.cn/nnews/183924.htm
- http://m.3g.oexnr.cn/nnews/2981820.htm
- http://m.3g.oexnr.cn/nnews/2655.htm
- http://m.3g.oexnr.cn/nnews/677715.htm
- http://m.3g.oexnr.cn/nnews/195057.htm
- http://m.3g.oexnr.cn/nnews/1324569.htm
- http://m.3g.oexnr.cn/nnews/539230.htm
- http://m.3g.oexnr.cn/nnews/9873.htm
- http://m.3g.oexnr.cn/nnews/7423.htm
- http://m.3g.oexnr.cn/nnews/34423.htm
- http://m.3g.oexnr.cn/nnews/6381167.htm
- http://m.3g.oexnr.cn/nnews/6424.htm
- http://m.3g.oexnr.cn/nnews/00941.htm
- http://m.3g.oexnr.cn/nnews/01035.htm
- http://m.3g.oexnr.cn/nnews/93782.htm
- http://m.3g.oexnr.cn/nnews/6082.htm
- http://m.3g.oexnr.cn/nnews/9101.htm
- http://m.3g.oexnr.cn/nnews/598967.htm
- http://m.3g.oexnr.cn/nnews/18900.htm
- http://m.3g.oexnr.cn/nnews/003664.htm
- http://m.3g.oexnr.cn/nnews/2710237.htm
- http://m.3g.oexnr.cn/nnews/614434.htm
- http://m.3g.oexnr.cn/nnews/47944.htm
- http://m.3g.oexnr.cn/nnews/3133.htm
- http://m.3g.oexnr.cn/nnews/203268.htm
- http://m.3g.oexnr.cn/nnews/8950.htm
- http://m.3g.oexnr.cn/nnews/2429643.htm
- http://m.3g.oexnr.cn/nnews/1805449.htm
- http://m.3g.oexnr.cn/nnews/2131.htm
- http://m.3g.oexnr.cn/nnews/6722560.htm
- http://m.3g.oexnr.cn/nnews/6662.htm
- http://m.3g.oexnr.cn/nnews/2107354.htm
- http://m.3g.oexnr.cn/nnews/17407.htm
- http://m.3g.oexnr.cn/nnews/86227.htm
- http://m.3g.oexnr.cn/nnews/9247.htm
- http://m.3g.oexnr.cn/nnews/85688.htm
- http://m.3g.oexnr.cn/nnews/581266.htm
- http://m.3g.oexnr.cn/nnews/37898.htm
- http://m.3g.oexnr.cn/nnews/502525.htm
- http://m.3g.oexnr.cn/nnews/0141.htm
- http://m.3g.oexnr.cn/nnews/2220.htm
- http://m.3g.oexnr.cn/nnews/5279057.htm
- http://m.3g.oexnr.cn/nnews/072688.htm
- http://m.3g.oexnr.cn/nnews/48344.htm
- http://m.3g.oexnr.cn/nnews/193908.htm
- http://m.3g.oexnr.cn/nnews/7178661.htm
- http://m.3g.oexnr.cn/nnews/746167.htm
- http://m.3g.oexnr.cn/nnews/42435.htm
- http://m.3g.oexnr.cn/nnews/75505.htm
- http://m.3g.oexnr.cn/nnews/600999.htm
- http://m.3g.oexnr.cn/nnews/7009.htm
- http://m.3g.oexnr.cn/nnews/133464.htm
- http://m.3g.oexnr.cn/nnews/9452501.htm
- http://m.3g.oexnr.cn/nnews/1422.htm
- http://m.3g.oexnr.cn/nnews/9655.htm
- http://m.3g.oexnr.cn/nnews/765765.htm
- http://m.3g.oexnr.cn/nnews/546867.htm
- http://m.3g.oexnr.cn/nnews/02772.htm
- http://m.3g.oexnr.cn/nnews/61694.htm
- http://m.3g.oexnr.cn/nnews/2189.htm
- http://m.3g.oexnr.cn/nnews/2112847.htm
- http://m.3g.oexnr.cn/nnews/38636.htm
- http://m.3g.oexnr.cn/nnews/32371.htm
- http://m.3g.oexnr.cn/nnews/794719.htm
- http://m.3g.oexnr.cn/nnews/14638.htm
- http://m.3g.oexnr.cn/nnews/411998.htm
- http://m.3g.oexnr.cn/nnews/66921.htm
- http://m.3g.oexnr.cn/nnews/297367.htm
- http://m.3g.oexnr.cn/nnews/8065062.htm
- http://m.3g.oexnr.cn/nnews/2585632.htm
- http://m.3g.oexnr.cn/nnews/6985055.htm
- http://m.3g.oexnr.cn/nnews/2017210.htm
- http://m.3g.oexnr.cn/nnews/8572331.htm
- http://m.3g.oexnr.cn/nnews/0727.htm
- http://m.3g.oexnr.cn/nnews/3885620.htm
- http://m.3g.oexnr.cn/nnews/4659249.htm
- http://m.3g.oexnr.cn/nnews/94814.htm
- http://m.3g.oexnr.cn/nnews/281362.htm
- http://m.3g.oexnr.cn/nnews/1083974.htm
- http://m.3g.oexnr.cn/nnews/300804.htm
- http://m.3g.oexnr.cn/nnews/5700778.htm
- http://m.3g.oexnr.cn/nnews/5168205.htm
- http://m.3g.oexnr.cn/nnews/107171.htm
- http://m.3g.oexnr.cn/nnews/80923.htm
- http://m.3g.oexnr.cn/nnews/3870.htm
- http://m.3g.oexnr.cn/nnews/8599796.htm
- http://m.3g.oexnr.cn/nnews/0225471.htm
- http://m.3g.oexnr.cn/nnews/5934.htm
- http://m.3g.oexnr.cn/nnews/2011.htm
- http://m.3g.oexnr.cn/nnews/5902.htm
- http://m.3g.oexnr.cn/nnews/2081786.htm
- http://m.3g.oexnr.cn/nnews/8773.htm
- http://m.3g.oexnr.cn/nnews/5906.htm
- http://m.3g.oexnr.cn/nnews/1539.htm
- http://m.3g.oexnr.cn/nnews/053491.htm
- http://m.3g.oexnr.cn/nnews/186484.htm
- http://m.3g.oexnr.cn/nnews/583145.htm
- http://m.3g.oexnr.cn/nnews/0143926.htm
- http://m.3g.oexnr.cn/nnews/69760.htm
- http://m.3g.oexnr.cn/nnews/75723.htm
- http://m.3g.oexnr.cn/nnews/63462.htm
- http://m.3g.oexnr.cn/nnews/2153838.htm
- http://m.3g.oexnr.cn/nnews/907328.htm
- http://m.3g.oexnr.cn/nnews/59044.htm
- http://m.3g.oexnr.cn/nnews/2907.htm
- http://m.3g.oexnr.cn/nnews/550405.htm
- http://m.3g.oexnr.cn/nnews/60197.htm
- http://m.3g.oexnr.cn/nnews/155696.htm
- http://m.3g.oexnr.cn/nnews/8754331.htm
- http://m.3g.oexnr.cn/nnews/7237.htm
- http://m.3g.oexnr.cn/nnews/980423.htm
- http://m.3g.oexnr.cn/nnews/2966.htm
- http://m.3g.oexnr.cn/nnews/1145179.htm
- http://m.3g.oexnr.cn/nnews/456302.htm
- http://m.3g.oexnr.cn/nnews/01835.htm
- http://m.3g.oexnr.cn/nnews/93766.htm
- http://m.3g.oexnr.cn/nnews/1005.htm
- http://m.3g.oexnr.cn/nnews/3894.htm
- http://m.3g.oexnr.cn/nnews/299967.htm
- http://m.3g.oexnr.cn/nnews/5196991.htm
- http://m.3g.oexnr.cn/nnews/054409.htm
- http://m.3g.oexnr.cn/nnews/6123.htm
- http://m.3g.oexnr.cn/nnews/2836.htm
- http://m.3g.oexnr.cn/nnews/892455.htm
- http://m.3g.oexnr.cn/nnews/66490.htm
- http://m.3g.oexnr.cn/nnews/4188954.htm
- http://m.3g.oexnr.cn/nnews/3652144.htm
- http://m.3g.oexnr.cn/nnews/432526.htm
- http://m.3g.oexnr.cn/nnews/489859.htm
- http://m.3g.oexnr.cn/nnews/0150.htm
- http://m.3g.oexnr.cn/nnews/069969.htm
- http://m.3g.oexnr.cn/nnews/4163.htm
- http://m.3g.oexnr.cn/nnews/8297165.htm
- http://m.3g.oexnr.cn/nnews/612805.htm
- http://m.3g.oexnr.cn/nnews/4002654.htm
- http://m.3g.oexnr.cn/nnews/845118.htm
- http://m.3g.oexnr.cn/nnews/989467.htm
- http://m.3g.oexnr.cn/nnews/1670808.htm
- http://m.3g.oexnr.cn/nnews/5651.htm
- http://m.3g.oexnr.cn/nnews/84063.htm
- http://m.3g.oexnr.cn/nnews/78557.htm
- http://m.3g.oexnr.cn/nnews/806866.htm
- http://m.3g.oexnr.cn/nnews/90437.htm
- http://m.3g.oexnr.cn/nnews/9874.htm
- http://m.3g.oexnr.cn/nnews/42865.htm
- http://m.3g.oexnr.cn/nnews/6979412.htm
- http://m.3g.oexnr.cn/nnews/429435.htm
- http://m.3g.oexnr.cn/nnews/14921.htm
- http://m.3g.oexnr.cn/nnews/5208786.htm
- http://m.3g.oexnr.cn/nnews/5928557.htm
- http://m.3g.oexnr.cn/nnews/19956.htm
- http://m.3g.oexnr.cn/nnews/46403.htm
- http://m.3g.oexnr.cn/nnews/15062.htm
- http://m.3g.oexnr.cn/nnews/51347.htm
- http://m.3g.oexnr.cn/nnews/3736166.htm
- http://m.3g.oexnr.cn/nnews/712427.htm
- http://m.3g.oexnr.cn/nnews/6379.htm
- http://m.3g.oexnr.cn/nnews/502598.htm
- http://m.3g.oexnr.cn/nnews/313497.htm
- http://m.3g.oexnr.cn/nnews/42670.htm
- http://m.3g.oexnr.cn/nnews/785624.htm
- http://m.3g.oexnr.cn/nnews/65758.htm
- http://m.3g.oexnr.cn/nnews/54510.htm
- http://m.3g.oexnr.cn/nnews/2195.htm
- http://m.3g.oexnr.cn/nnews/409719.htm
- http://m.3g.oexnr.cn/nnews/3841543.htm
- http://m.3g.oexnr.cn/nnews/616913.htm
- http://m.3g.oexnr.cn/nnews/2224622.htm
- http://m.3g.oexnr.cn/nnews/4981366.htm
- http://m.3g.oexnr.cn/nnews/7496.htm
- http://m.3g.oexnr.cn/nnews/3288.htm
- http://m.3g.oexnr.cn/nnews/53965.htm
- http://m.3g.oexnr.cn/nnews/9081533.htm
- http://m.3g.oexnr.cn/nnews/9563169.htm
- http://m.3g.oexnr.cn/nnews/3533111.htm
- http://m.3g.oexnr.cn/nnews/2785542.htm
- http://m.3g.oexnr.cn/nnews/96069.htm
- http://m.3g.oexnr.cn/nnews/9861044.htm
- http://m.3g.oexnr.cn/nnews/56164.htm
- http://m.3g.oexnr.cn/nnews/6100.htm
- http://m.3g.oexnr.cn/nnews/7475408.htm
- http://m.3g.oexnr.cn/nnews/7591763.htm
- http://m.3g.oexnr.cn/nnews/945625.htm
- http://m.3g.oexnr.cn/nnews/9456289.htm
- http://m.3g.oexnr.cn/nnews/72728.htm
- http://m.3g.oexnr.cn/nnews/95100.htm
- http://m.3g.oexnr.cn/nnews/759932.htm
- http://m.3g.oexnr.cn/nnews/07471.htm
- http://m.3g.oexnr.cn/nnews/1085418.htm
- http://m.3g.oexnr.cn/nnews/7218.htm
- http://m.3g.oexnr.cn/nnews/9242.htm
- http://m.3g.oexnr.cn/nnews/6093.htm

## 项目结构

```
news-aggregator-x/
├── src/                                # 核心源码目录
│   ├── core/                           # 核心处理模块
│   │   ├── fetcher.ts                  # 外链抓取器，负责发起 HTTP 请求
│   │   ├── parser.ts                   # URL 解析器，提取文件名与分类标识
│   │   └── indexer.ts                  # 索引生成器，构建分类映射表
│   ├── cli/                            # 命令行工具入口
│   │   ├── build.ts                    # build 命令实现
│   │   └── serve.ts                    # serve 命令实现
│   ├── generators/                     # 文档生成器
│   │   ├── markdown.ts                 # Markdown 文档流输出
│   │   └── html.ts                     # 静态 HTML 页面编译
│   ├── utils/                          # 通用工具函数
│   │   ├── http.ts                     # HTTP 辅助函数（超时、重试）
│   │   ├── file.ts                     # 文件读写工具
│   │   └── logger.ts                   # 日志记录器
│   └── types/                          # TypeScript 类型定义
│       └── index.ts                    # 全局类型声明
├── data/                               # 数据目录
│   └── links.txt                       # 默认外链数据源（每行一个 URL）
├── docs/                               # 项目文档
│   ├── user-guide.md                   # 用户手册
│   ├── developer-guide.md              # 开发者指南
│   ├── api-reference.md                # API 参考
│   └── deployment-guide.md             # 部署指南
├── dist/                               # 构建输出目录（自动生成）
│   ├── index.html                      # 生成的导航首页
│   ├── categories/                     # 分类索引页面
│   └── reports/                        # 巡检报告
├── tests/                              # 单元测试
│   ├── fetcher.test.ts                 # 抓取器测试
│   └── parser.test.ts                  # 解析器测试
├── .github/                            # GitHub 工作流配置
│   └── workflows/                      # CI/CD 流水线
│       └── ci.yml                      # 持续集成配置
├── package.json                        # 项目配置文件
├── tsconfig.json                       # TypeScript 编译配置
├── .gitignore                          # Git 忽略文件
└── README.md                           # 项目说明文档
```

## 贡献指南

我们欢迎并感谢任何形式的贡献。请遵循以下步骤参与项目开发。

首先，在 GitHub 上 Fork 本仓库，并将您的 Fork 克隆到本地。然后，创建一个新的功能分支，分支名称应清晰反映您要解决的问题或添加的功能，例如 `fix-link-parser` 或 `add-json-exporter`。

其次，在开发前请确保已安装所有依赖，并运行 `npm run test` 确认现有测试全部通过。对于新增功能，请同步编写对应的单元测试用例，测试覆盖率不低于 80%。

第三，完成代码修改后，请运行 `npm run lint` 和 `npm run format` 对代码进行风格检查和格式化。本项目使用 ESLint 和 Prettier 统一代码风格。

第四，提交代码时请遵循 Conventional Commits 规范，提交信息格式为 `<type>(<scope>): <subject>`，例如 `feat(core): add retry mechanism for fetcher`。

最后，向本仓库的 `main` 分支提交 Pull Request，并在 PR 描述中详细说明变更内容、测试结果和影响范围。项目维护者会在 48 小时内进行 Code Review。

## 常见问题

**Q: 项目是否会对目标网站造成过大请求压力？**

A: 不会。NewsAggregatorX 默认采用串行请求模式，并且每次请求之间强制间隔 500 毫秒。您可以在 `src/core/fetcher.ts` 中调整 `REQUEST_INTERVAL` 常量来控制请求频率。此外，项目严格遵守 `robots.txt` 协议，仅对允许的路径发起请求。

**Q: 如何处理外链中的相对路径或非法 URL 格式？**

A: 项目内置了 URL 标准化函数（位于 `src/utils/url.ts`），会自动对输入的 URL 进行协议补全、路径解析和编码处理。对于无法解析的非法 URL，系统会将其记录到 `./dist/reports/error.log` 中，并跳过该条目继续处理后续链接，不影响整体流程。

**Q: 是否支持 Windows 操作系统？**

A: 支持。NewsAggregatorX 使用 Node.js 跨平台 API，所有文件路径操作均通过 `path` 模块处理，命令行脚本通过 `cross-env` 兼容 Windows 和 Unix 环境。但建议在 Windows 上使用 PowerShell 或 WSL2 终端以获得最佳体验。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
