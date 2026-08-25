# JNews Archive Gateway

JNews Archive Gateway 是一个面向移动端新闻资源聚合与历史存档检索的开源网关项目。该项目旨在为研究人员、数据分析师以及内容聚合服务提供商提供统一、可编程的新闻条目访问接口，通过对分散的历史新闻页面进行结构化索引与元数据提取，降低新闻数据的获取与维护成本。项目定位于技术资源中转层与轻量级新闻外链汇总站，不直接存储新闻正文，而是提供高效的链接路由、状态监控与访问日志分析能力。

## 功能概览

批量链接健康检查：支持对大量新闻外链进行自动化的 HTTP 状态码检测与响应时间监控，快速识别失效或重定向资源。

结构化元数据提取：从目标新闻页面中自动提取发布时间、正文长度、关键标题与图片数量等核心元数据，并输出为 JSON 格式。

移动端自适应路由：针对移动设备 User-Agent 进行智能路由适配，确保通过网关访问的新闻链接在手机端获得最佳阅读体验。

链接有效性周期报告：按照每日、每周维度生成链接有效性统计报告，包含存活率、平均响应时间与异常链接列表。

简易全文检索接口：基于提取的元数据与标题关键词，提供轻量级全文检索能力，支持模糊匹配与时间范围过滤。

访问频次控制与防滥用策略：内置基于 IP 与 API Key 的访问频次限制，支持自定义阈值，防止网关资源被恶意抓取。

## 应用场景

历史新闻数据批量整理与归档迁移：内容迁移工程师在将旧版新闻系统切换至新平台时，可通过本网关批量验证存量外链的有效性，并自动生成链接状态清单，辅助决策是否保留或替换特定来源。

移动端新闻聚合应用原型开发：移动应用开发者在构建新闻聚合类 Demo 时，可使用本网关提供的统一路由与元数据接口，快速完成内容展示层的联调，无需逐一处理各个新闻源站的复杂页面结构。

学术研究中的新闻传播路径追踪：新闻传播学研究者可利用本网关的访问日志与链接跳转记录，分析特定新闻话题在移动端的传播路径与热度变化趋势，为内容传播模型提供数据支撑。

运维监控体系的新闻源可用性探测：网站运维团队可将本网关集成至现有监控系统（如 Prometheus 或 Zabbix），定期对新闻源链接进行探测，当大面积链接异常时触发告警，及时通知内容运营人员。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目仓库、安装依赖并启动开发服务器。请确保您的开发环境已安装 Node.js 18.x 或更高版本。

```bash
git clone https://github.com/your-org/jnews-archive-gateway.git
cd jnews-archive-gateway
npm install
npm run dev
```

若使用 Yarn 作为包管理器，可将 `npm install` 替换为 `yarn install`，`npm run dev` 替换为 `yarn dev`。启动成功后，访问 `http://localhost:3000` 即可查看网关状态面板。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 项目运行时基础环境，推荐使用 LTS 版本以确保稳定性 |
| npm | 9.x 或以上 | Node.js 默认包管理器，用于安装项目依赖 |
| SQLite3 | 3.40.x 或以上 | 嵌入式数据库，用于存储链接元数据与访问日志，无需额外安装服务端 |
| PM2 | 5.x 或以上 | 生产环境进程守护工具，用于保持网关服务持续运行 |
| Git | 2.30.x 或以上 | 版本控制工具，用于克隆仓库与管理代码更新 |
| curl | 7.68.x 或以上 | 用于本地调试与健康检查脚本的 HTTP 请求工具 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quick-start.md | 如何最快部署网关服务并进行首次链接检查？ |
| API 参考 | docs/api-reference.md | 网关对外提供了哪些 RESTful 端点？每个端点的请求参数与返回结构是什么？ |
| 配置说明 | docs/configuration.md | 如何修改链接检查的超时时间、并发数以及报告生成周期？ |
| 部署运维 | docs/deployment.md | 在生产环境中如何使用 PM2 或 Docker 部署网关？如何查看日志与监控性能？ |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/988638.htm
- http://m.3g.bwbkj.cn/jnews/42068.htm
- http://m.3g.bwbkj.cn/jnews/071827.htm
- http://m.3g.bwbkj.cn/jnews/692398.htm
- http://m.3g.bwbkj.cn/jnews/0005.htm
- http://m.3g.bwbkj.cn/jnews/67709.htm
- http://m.3g.bwbkj.cn/jnews/00788.htm
- http://m.3g.bwbkj.cn/jnews/4979.htm
- http://m.3g.bwbkj.cn/jnews/909584.htm
- http://m.3g.bwbkj.cn/jnews/2442.htm
- http://m.3g.bwbkj.cn/jnews/96488.htm
- http://m.3g.bwbkj.cn/jnews/500028.htm
- http://m.3g.bwbkj.cn/jnews/3889564.htm
- http://m.3g.bwbkj.cn/jnews/01013.htm
- http://m.3g.bwbkj.cn/jnews/0063486.htm
- http://m.3g.bwbkj.cn/jnews/80773.htm
- http://m.3g.bwbkj.cn/jnews/05235.htm
- http://m.3g.bwbkj.cn/jnews/74171.htm
- http://m.3g.bwbkj.cn/jnews/3296.htm
- http://m.3g.bwbkj.cn/jnews/5849.htm
- http://m.3g.bwbkj.cn/jnews/76976.htm
- http://m.3g.bwbkj.cn/jnews/561356.htm
- http://m.3g.bwbkj.cn/jnews/78860.htm
- http://m.3g.bwbkj.cn/jnews/492247.htm
- http://m.3g.bwbkj.cn/jnews/7438875.htm
- http://m.3g.bwbkj.cn/jnews/08141.htm
- http://m.3g.bwbkj.cn/jnews/0216.htm
- http://m.3g.bwbkj.cn/jnews/8115.htm
- http://m.3g.bwbkj.cn/jnews/19938.htm
- http://m.3g.bwbkj.cn/jnews/745555.htm
- http://m.3g.bwbkj.cn/jnews/3430.htm
- http://m.3g.bwbkj.cn/jnews/27096.htm
- http://m.3g.bwbkj.cn/jnews/59893.htm
- http://m.3g.bwbkj.cn/jnews/19852.htm
- http://m.3g.bwbkj.cn/jnews/559129.htm
- http://m.3g.bwbkj.cn/jnews/4716.htm
- http://m.3g.bwbkj.cn/jnews/6298754.htm
- http://m.3g.bwbkj.cn/jnews/9038.htm
- http://m.3g.bwbkj.cn/jnews/43831.htm
- http://m.3g.bwbkj.cn/jnews/876430.htm
- http://m.3g.bwbkj.cn/jnews/8682.htm
- http://m.3g.bwbkj.cn/jnews/1566301.htm
- http://m.3g.bwbkj.cn/jnews/25074.htm
- http://m.3g.bwbkj.cn/jnews/4328163.htm
- http://m.3g.bwbkj.cn/jnews/6331.htm
- http://m.3g.bwbkj.cn/jnews/1498528.htm
- http://m.3g.bwbkj.cn/jnews/24581.htm
- http://m.3g.bwbkj.cn/jnews/7277504.htm
- http://m.3g.bwbkj.cn/jnews/4623506.htm
- http://m.3g.bwbkj.cn/jnews/2770968.htm
- http://m.3g.bwbkj.cn/jnews/1643838.htm
- http://m.3g.bwbkj.cn/jnews/37590.htm
- http://m.3g.bwbkj.cn/jnews/6760.htm
- http://m.3g.bwbkj.cn/jnews/2618197.htm
- http://m.3g.bwbkj.cn/jnews/12580.htm
- http://m.3g.bwbkj.cn/jnews/849602.htm
- http://m.3g.bwbkj.cn/jnews/1193.htm
- http://m.3g.bwbkj.cn/jnews/580542.htm
- http://m.3g.bwbkj.cn/jnews/2471563.htm
- http://m.3g.bwbkj.cn/jnews/407443.htm
- http://m.3g.bwbkj.cn/jnews/3809371.htm
- http://m.3g.bwbkj.cn/jnews/755750.htm
- http://m.3g.bwbkj.cn/jnews/7228129.htm
- http://m.3g.bwbkj.cn/jnews/72597.htm
- http://m.3g.bwbkj.cn/jnews/3194950.htm
- http://m.3g.bwbkj.cn/jnews/476828.htm
- http://m.3g.bwbkj.cn/jnews/5376.htm
- http://m.3g.bwbkj.cn/jnews/7053417.htm
- http://m.3g.bwbkj.cn/jnews/1333778.htm
- http://m.3g.bwbkj.cn/jnews/6833.htm
- http://m.3g.bwbkj.cn/jnews/6707678.htm
- http://m.3g.bwbkj.cn/jnews/54529.htm
- http://m.3g.bwbkj.cn/jnews/66897.htm
- http://m.3g.bwbkj.cn/jnews/478097.htm
- http://m.3g.bwbkj.cn/jnews/661975.htm
- http://m.3g.bwbkj.cn/jnews/6963.htm
- http://m.3g.bwbkj.cn/jnews/00222.htm
- http://m.3g.bwbkj.cn/jnews/40347.htm
- http://m.3g.bwbkj.cn/jnews/2362.htm
- http://m.3g.bwbkj.cn/jnews/777482.htm
- http://m.3g.bwbkj.cn/jnews/88922.htm
- http://m.3g.bwbkj.cn/jnews/0369.htm
- http://m.3g.bwbkj.cn/jnews/8540837.htm
- http://m.3g.bwbkj.cn/jnews/4142.htm
- http://m.3g.bwbkj.cn/jnews/9978.htm
- http://m.3g.bwbkj.cn/jnews/0228092.htm
- http://m.3g.bwbkj.cn/jnews/9616701.htm
- http://m.3g.bwbkj.cn/jnews/1548205.htm
- http://m.3g.bwbkj.cn/jnews/1817336.htm
- http://m.3g.bwbkj.cn/jnews/9271.htm
- http://m.3g.bwbkj.cn/jnews/98783.htm
- http://m.3g.bwbkj.cn/jnews/47406.htm
- http://m.3g.bwbkj.cn/jnews/1872069.htm
- http://m.3g.bwbkj.cn/jnews/81374.htm
- http://m.3g.bwbkj.cn/jnews/4905201.htm
- http://m.3g.bwbkj.cn/jnews/28460.htm
- http://m.3g.bwbkj.cn/jnews/1026997.htm
- http://m.3g.bwbkj.cn/jnews/56575.htm
- http://m.3g.bwbkj.cn/jnews/9731.htm
- http://m.3g.bwbkj.cn/jnews/0054484.htm
- http://m.3g.bwbkj.cn/jnews/9999.htm
- http://m.3g.bwbkj.cn/jnews/745458.htm
- http://m.3g.bwbkj.cn/jnews/91225.htm
- http://m.3g.bwbkj.cn/jnews/15018.htm
- http://m.3g.bwbkj.cn/jnews/53201.htm
- http://m.3g.bwbkj.cn/jnews/08174.htm
- http://m.3g.bwbkj.cn/jnews/18950.htm
- http://m.3g.bwbkj.cn/jnews/6157321.htm
- http://m.3g.bwbkj.cn/jnews/97822.htm
- http://m.3g.bwbkj.cn/jnews/0418.htm
- http://m.3g.bwbkj.cn/jnews/472822.htm
- http://m.3g.bwbkj.cn/jnews/6425877.htm
- http://m.3g.bwbkj.cn/jnews/7276714.htm
- http://m.3g.bwbkj.cn/jnews/8695.htm
- http://m.3g.bwbkj.cn/jnews/44156.htm
- http://m.3g.bwbkj.cn/jnews/8111458.htm
- http://m.3g.bwbkj.cn/jnews/9822.htm
- http://m.3g.bwbkj.cn/jnews/3754022.htm
- http://m.3g.bwbkj.cn/jnews/7212.htm
- http://m.3g.bwbkj.cn/jnews/605557.htm
- http://m.3g.bwbkj.cn/jnews/2107337.htm
- http://m.3g.bwbkj.cn/jnews/6764.htm
- http://m.3g.bwbkj.cn/jnews/300325.htm
- http://m.3g.bwbkj.cn/jnews/87666.htm
- http://m.3g.bwbkj.cn/jnews/9220.htm
- http://m.3g.bwbkj.cn/jnews/3807.htm
- http://m.3g.bwbkj.cn/jnews/8351895.htm
- http://m.3g.bwbkj.cn/jnews/92893.htm
- http://m.3g.bwbkj.cn/jnews/42050.htm
- http://m.3g.bwbkj.cn/jnews/4190212.htm
- http://m.3g.bwbkj.cn/jnews/158527.htm
- http://m.3g.bwbkj.cn/jnews/6021.htm
- http://m.3g.bwbkj.cn/jnews/6810060.htm
- http://m.3g.bwbkj.cn/jnews/7776956.htm
- http://m.3g.bwbkj.cn/jnews/573931.htm
- http://m.3g.bwbkj.cn/jnews/984567.htm
- http://m.3g.bwbkj.cn/jnews/1427.htm
- http://m.3g.bwbkj.cn/jnews/1922.htm
- http://m.3g.bwbkj.cn/jnews/6589.htm
- http://m.3g.bwbkj.cn/jnews/1130.htm
- http://m.3g.bwbkj.cn/jnews/1485445.htm
- http://m.3g.bwbkj.cn/jnews/5748678.htm
- http://m.3g.bwbkj.cn/jnews/3288.htm
- http://m.3g.bwbkj.cn/jnews/6191968.htm
- http://m.3g.bwbkj.cn/jnews/768814.htm
- http://m.3g.bwbkj.cn/jnews/780481.htm
- http://m.3g.bwbkj.cn/jnews/79935.htm
- http://m.3g.bwbkj.cn/jnews/7998942.htm
- http://m.3g.bwbkj.cn/jnews/89945.htm
- http://m.3g.bwbkj.cn/jnews/5136.htm
- http://m.3g.bwbkj.cn/jnews/2324084.htm
- http://m.3g.bwbkj.cn/jnews/487628.htm
- http://m.3g.bwbkj.cn/jnews/828000.htm
- http://m.3g.bwbkj.cn/jnews/03962.htm
- http://m.3g.bwbkj.cn/jnews/4441853.htm
- http://m.3g.bwbkj.cn/jnews/625806.htm
- http://m.3g.bwbkj.cn/jnews/9141.htm
- http://m.3g.bwbkj.cn/jnews/2206005.htm
- http://m.3g.bwbkj.cn/jnews/4663962.htm
- http://m.3g.bwbkj.cn/jnews/69181.htm
- http://m.3g.bwbkj.cn/jnews/57602.htm
- http://m.3g.bwbkj.cn/jnews/348136.htm
- http://m.3g.bwbkj.cn/jnews/8762.htm
- http://m.3g.bwbkj.cn/jnews/15986.htm
- http://m.3g.bwbkj.cn/jnews/681011.htm
- http://m.3g.bwbkj.cn/jnews/028448.htm
- http://m.3g.bwbkj.cn/jnews/1152880.htm
- http://m.3g.bwbkj.cn/jnews/537399.htm
- http://m.3g.bwbkj.cn/jnews/4164.htm
- http://m.3g.bwbkj.cn/jnews/664671.htm
- http://m.3g.bwbkj.cn/jnews/8550.htm
- http://m.3g.bwbkj.cn/jnews/2005.htm
- http://m.3g.bwbkj.cn/jnews/3511674.htm
- http://m.3g.bwbkj.cn/jnews/6933826.htm
- http://m.3g.bwbkj.cn/jnews/7284.htm
- http://m.3g.bwbkj.cn/jnews/5792.htm
- http://m.3g.bwbkj.cn/jnews/2131.htm
- http://m.3g.bwbkj.cn/jnews/9619835.htm
- http://m.3g.bwbkj.cn/jnews/049453.htm
- http://m.3g.bwbkj.cn/jnews/04924.htm
- http://m.3g.bwbkj.cn/jnews/0596.htm
- http://m.3g.bwbkj.cn/jnews/8278.htm
- http://m.3g.bwbkj.cn/jnews/7580360.htm
- http://m.3g.bwbkj.cn/jnews/3088029.htm
- http://m.3g.bwbkj.cn/jnews/7884908.htm
- http://m.3g.bwbkj.cn/jnews/7982887.htm
- http://m.3g.bwbkj.cn/jnews/1379228.htm
- http://m.3g.bwbkj.cn/jnews/25687.htm
- http://m.3g.bwbkj.cn/jnews/889632.htm
- http://m.3g.bwbkj.cn/jnews/847269.htm
- http://m.3g.bwbkj.cn/jnews/50929.htm
- http://m.3g.bwbkj.cn/jnews/4255193.htm
- http://m.3g.bwbkj.cn/jnews/3888.htm
- http://m.3g.bwbkj.cn/jnews/3844.htm
- http://m.3g.bwbkj.cn/jnews/1830.htm
- http://m.3g.bwbkj.cn/jnews/6515.htm
- http://m.3g.bwbkj.cn/jnews/7787651.htm
- http://m.3g.bwbkj.cn/jnews/92727.htm
- http://m.3g.bwbkj.cn/jnews/403077.htm
- http://m.3g.bwbkj.cn/jnews/980592.htm
- http://m.3g.bwbkj.cn/jnews/0700.htm
- http://m.3g.bwbkj.cn/jnews/8034845.htm
- http://m.3g.bwbkj.cn/jnews/115245.htm
- http://m.3g.bwbkj.cn/jnews/088833.htm
- http://m.3g.bwbkj.cn/jnews/511134.htm
- http://m.3g.bwbkj.cn/jnews/789755.htm
- http://m.3g.bwbkj.cn/jnews/8079.htm
- http://m.3g.bwbkj.cn/jnews/1451.htm
- http://m.3g.bwbkj.cn/jnews/816445.htm
- http://m.3g.bwbkj.cn/jnews/97059.htm
- http://m.3g.bwbkj.cn/jnews/678915.htm
- http://m.3g.bwbkj.cn/jnews/6677944.htm
- http://m.3g.bwbkj.cn/jnews/0667.htm
- http://m.3g.bwbkj.cn/jnews/59834.htm
- http://m.3g.bwbkj.cn/jnews/27410.htm
- http://m.3g.bwbkj.cn/jnews/2106939.htm
- http://m.3g.bwbkj.cn/jnews/088212.htm
- http://m.3g.bwbkj.cn/jnews/4781.htm
- http://m.3g.bwbkj.cn/jnews/4802.htm
- http://m.3g.bwbkj.cn/jnews/080647.htm
- http://m.3g.bwbkj.cn/jnews/35848.htm
- http://m.3g.bwbkj.cn/jnews/9372.htm
- http://m.3g.bwbkj.cn/jnews/5789003.htm
- http://m.3g.bwbkj.cn/jnews/2916198.htm
- http://m.3g.bwbkj.cn/jnews/77151.htm
- http://m.3g.bwbkj.cn/jnews/2003.htm
- http://m.3g.bwbkj.cn/jnews/566578.htm
- http://m.3g.bwbkj.cn/jnews/051869.htm
- http://m.3g.bwbkj.cn/jnews/008140.htm
- http://m.3g.bwbkj.cn/jnews/4126.htm
- http://m.3g.bwbkj.cn/jnews/477042.htm
- http://m.3g.bwbkj.cn/jnews/0972637.htm
- http://m.3g.bwbkj.cn/jnews/0115.htm
- http://m.3g.bwbkj.cn/jnews/166872.htm
- http://m.3g.bwbkj.cn/jnews/099232.htm
- http://m.3g.bwbkj.cn/jnews/979109.htm
- http://m.3g.bwbkj.cn/jnews/79766.htm
- http://m.3g.bwbkj.cn/jnews/91633.htm
- http://m.3g.bwbkj.cn/jnews/114664.htm
- http://m.3g.bwbkj.cn/jnews/26966.htm
- http://m.3g.bwbkj.cn/jnews/47779.htm
- http://m.3g.bwbkj.cn/jnews/44733.htm
- http://m.3g.bwbkj.cn/jnews/5584.htm
- http://m.3g.bwbkj.cn/jnews/19858.htm
- http://m.3g.bwbkj.cn/jnews/3313.htm
- http://m.3g.bwbkj.cn/jnews/3826644.htm
- http://m.3g.bwbkj.cn/jnews/929060.htm
- http://m.3g.bwbkj.cn/jnews/01394.htm
- http://m.3g.bwbkj.cn/jnews/49423.htm
- http://m.3g.bwbkj.cn/jnews/90195.htm
- http://m.3g.bwbkj.cn/jnews/4490.htm
- http://m.3g.bwbkj.cn/jnews/651548.htm
- http://m.3g.bwbkj.cn/jnews/0166.htm
- http://m.3g.bwbkj.cn/jnews/0717978.htm
- http://m.3g.bwbkj.cn/jnews/0106.htm
- http://m.3g.bwbkj.cn/jnews/9334.htm
- http://m.3g.bwbkj.cn/jnews/653050.htm
- http://m.3g.bwbkj.cn/jnews/2424356.htm
- http://m.3g.bwbkj.cn/jnews/32486.htm
- http://m.3g.bwbkj.cn/jnews/1893.htm
- http://m.3g.bwbkj.cn/jnews/93664.htm
- http://m.3g.bwbkj.cn/jnews/205239.htm
- http://m.3g.bwbkj.cn/jnews/2031.htm
- http://m.3g.bwbkj.cn/jnews/9440254.htm
- http://m.3g.bwbkj.cn/jnews/1675813.htm
- http://m.3g.bwbkj.cn/jnews/727429.htm
- http://m.3g.bwbkj.cn/jnews/5407.htm
- http://m.3g.bwbkj.cn/jnews/1861984.htm
- http://m.3g.bwbkj.cn/jnews/6466384.htm
- http://m.3g.bwbkj.cn/jnews/3695364.htm
- http://m.3g.bwbkj.cn/jnews/940137.htm
- http://m.3g.bwbkj.cn/jnews/2348195.htm
- http://m.3g.bwbkj.cn/jnews/176590.htm
- http://m.3g.bwbkj.cn/jnews/89707.htm
- http://m.3g.bwbkj.cn/jnews/21139.htm
- http://m.3g.bwbkj.cn/jnews/304146.htm
- http://m.3g.bwbkj.cn/jnews/701282.htm
- http://m.3g.bwbkj.cn/jnews/8036980.htm
- http://m.3g.bwbkj.cn/jnews/2063433.htm
- http://m.3g.bwbkj.cn/jnews/571601.htm
- http://m.3g.bwbkj.cn/jnews/755838.htm
- http://m.3g.bwbkj.cn/jnews/5846567.htm
- http://m.3g.bwbkj.cn/jnews/6619.htm
- http://m.3g.bwbkj.cn/jnews/4177.htm
- http://m.3g.bwbkj.cn/jnews/7892191.htm
- http://m.3g.bwbkj.cn/jnews/766961.htm
- http://m.3g.bwbkj.cn/jnews/421387.htm
- http://m.3g.bwbkj.cn/jnews/0582776.htm
- http://m.3g.bwbkj.cn/jnews/1045.htm
- http://m.3g.bwbkj.cn/jnews/9164827.htm
- http://m.3g.bwbkj.cn/jnews/2341339.htm
- http://m.3g.bwbkj.cn/jnews/2902904.htm
- http://m.3g.bwbkj.cn/jnews/0073521.htm
- http://m.3g.bwbkj.cn/jnews/4217.htm
- http://m.3g.bwbkj.cn/jnews/9494576.htm
- http://m.3g.bwbkj.cn/jnews/1668118.htm
- http://m.3g.bwbkj.cn/jnews/2803020.htm
- http://m.3g.bwbkj.cn/jnews/8528.htm
- http://m.3g.bwbkj.cn/jnews/875385.htm
- http://m.3g.bwbkj.cn/jnews/594812.htm

## 项目结构

```
jnews-archive-gateway/
├── src/
│   ├── core/                           # 核心业务逻辑模块
│   │   ├── linkChecker.js              # 批量链接健康检查引擎，支持并发与超时控制
│   │   ├── metaExtractor.js            # 元数据提取器，解析新闻页面的标题、时间与正文特征
│   │   └── reportGenerator.js          # 周期报告生成器，输出 JSON 与 CSV 格式报告
│   ├── routes/                         # RESTful 路由定义
│   │   ├── api/v1/                     # 主要 API 版本
│   │   │   ├── health.js               # 网关健康状态与版本信息接口
│   │   │   ├── links.js                # 链接管理接口（增删改查与批量检查）
│   │   │   └── stats.js                # 统计数据接口（存活率、响应时间分布）
│   │   └── web/                        # 管理后台页面路由
│   │       └── dashboard.js            # 状态面板与可视化图表路由
│   ├── middleware/                     # 请求中间件
│   │   ├── auth.js                     # API Key 认证与权限校验
│   │   ├── rateLimiter.js              # 基于 IP 与 API Key 的频次限制中间件
│   │   └── logger.js                   # 访问日志记录与结构化日志输出
│   ├── models/                         # 数据模型与数据库操作层
│   │   ├── LinkModel.js                # 链接元数据模型（状态、标题、提取时间）
│   │   └── LogModel.js                 # 访问日志模型（IP、时间戳、响应状态）
│   ├── utils/                          # 通用工具函数
│   │   ├── httpClient.js               # 封装的 HTTP 请求客户端，支持重试与超时
│   │   ├── userAgent.js                # 移动端与桌面端 User-Agent 轮换池
│   │   └── dateHelper.js               # 时间格式化与时区转换工具
│   └── app.js                          # Express 应用入口，注册中间件与路由
├── config/
│   ├── default.yaml                    # 默认配置文件（端口、超时时间、检查并发数）
│   └── production.yaml                 # 生产环境覆盖配置（日志级别、缓存策略）
├── scripts/
│   ├── initDb.js                       # SQLite 数据库初始化脚本，创建表结构与索引
│   └── seedLinks.js                    # 从 CSV 或 JSON 文件批量导入初始链接列表
├── docs/                               # 项目文档目录（详见文档导航章节）
├── test/                               # 单元测试与集成测试
│   ├── unit/                           # 单元测试用例
│   └── integration/                    # 接口集成测试
├── .env.example                        # 环境变量示例文件（API Key、数据库路径）
├── .gitignore                          # Git 忽略文件配置
├── package.json                        # npm 依赖清单与脚本定义
└── README.md                           # 项目总览与快速入门文档
```

## 贡献指南

提交 Issue 报告缺陷或功能请求：在 GitHub Issues 页面新建 Issue，请使用提供的模板详细描述问题现象、复现步骤、环境信息以及期望行为。缺陷报告需附上相关日志片段。

Fork 仓库并创建功能分支：将本仓库 Fork 至个人账户，然后基于 main 分支创建以 feature/ 或 fix/ 为前缀的新分支，例如 feature/add-batch-export。禁止直接在 main 分支上修改。

编写代码并确保测试通过：在本地执行 `npm run test` 运行全部单元测试与集成测试，确保新增代码的测试覆盖率达到 80% 以上。同时使用 `npm run lint` 检查代码风格是否符合 ESLint 配置。

提交 Pull Request 并关联 Issue：推送分支至远程仓库后，向本仓库的 main 分支发起 Pull Request。PR 描述中需使用 `Closes #ISSUE_NUMBER` 关联相关 Issue，并简要说明改动内容与测试结果。

遵循提交信息规范：提交信息请使用 Conventional Commits 格式，即 `type(scope): subject`，其中 type 包括 feat、fix、docs、style、refactor、test 等。例如 `fix(linkChecker): 修复超时后未释放并发槽位的缺陷`。

## 常见问题

问：网关检查链接时出现大量超时，应如何调整配置？

答：超时问题通常由目标服务器响应慢或网络抖动引起。您可以修改 config/default.yaml 文件中的 `checker.timeout` 参数，默认值为 5000 毫秒（5 秒），可酌情增加至 10000 或 15000 毫秒。同时，调整 `checker.concurrency` 参数降低并发数（例如从 10 降至 5），以避免被目标服务器限流。调整后需重启服务生效。

问：如何查看网关的访问日志与链接检查历史记录？

答：访问日志存储在 SQLite 数据库的 `logs` 表中，您可以通过 SQL 查询语句直接分析，例如 `SELECT * FROM logs WHERE timestamp > datetime('now', '-1 day')`。此外，您可以通过 API 端点 `GET /api/v1/stats/daily` 获取前一日链接检查的汇总统计，包括总检查数、存活数与平均响应时间。若需导出完整历史，可使用 `scripts/exportLogs.js` 脚本将数据导出为 CSV 格式。

问：部署到生产环境后，如何确保网关服务在崩溃后自动重启？

答：推荐使用 PM2 进行进程守护。首先全局安装 PM2：`npm install -g pm2`。然后在项目根目录执行 `pm2 start src/app.js --name jnews-gateway`。执行 `pm2 save` 保存当前进程列表，最后执行 `pm2 startup` 生成开机自启脚本。您还可以使用 `pm2 monit` 实时监控 CPU 与内存占用情况。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:07
