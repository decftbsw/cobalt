# NewsLink Aggregator - 轻量级新闻外链资源聚合系统

NewsLink Aggregator 是一个面向内容创作者、舆情分析人员与信息研究者的标准化新闻外链资源聚合与导航工具。该项目不对新闻内容进行二次编辑或转载，而是提供结构化的外部链接索引服务，帮助用户快速定位来自 m.3g.ghtkgg.cn 域名下的历史新闻页面，适用于批量信息检索、存档分析以及定向内容追踪场景。

项目定位为纯静态资源导航层，不依赖数据库，不采集落地页正文，仅维护 URL 映射关系与基础元信息标注。目标用户包括需要长期跟踪特定信源发布规律的研究人员、构建自定义新闻聚合流的产品开发者，以及希望对指定域名下历史稿件进行系统性梳理的档案管理者。

## 功能概览

**批量链接导入与去重**：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别并移除重复条目，保留原始路径参数。

**多维度标签分类**：允许用户为每条外链添加自定义标签（如“科技”、“社会”、“公告”），并支持按标签快速过滤，便于构建个性化阅读队列。

**状态监控与可用性检测**：内置轻量级 HTTP 头检测模块，可定时验证链接是否返回 200 状态码，标记失效链接并生成可用性报告。

**全文检索与模糊匹配**：基于链接路径中的数字 ID 和文件名片段，提供前缀匹配、后缀匹配与数字范围检索功能，支持按 ID 段批量筛选。

**黑白名单过滤规则**：支持通过正则表达式配置过滤规则，自动屏蔽包含特定关键词或 ID 模式的链接，辅助内容安全管理。

**导出与集成接口**：提供 JSON、CSV、纯文本列表三种导出格式，并开放 RESTful 风格的查询 API，方便嵌入其他数据分析流水线。

**暗色主题与自适应布局**：前端界面同时支持亮色与暗色主题，在移动端与桌面端均保持良好可读性，降低长时间浏览的视觉疲劳。

## 应用场景

舆情监测机构批量采集历史数据前的链接预处理：在启动大规模爬虫任务之前，使用 NewsLink Aggregator 清洗和验证目标 URL 列表，剔除重复项与已失效链接，提高采集任务的成功率与资源利用率。

内容策展人构建主题新闻合辑：编辑人员可根据特定事件或时间范围，从海量外链中筛选相关条目，添加备注后导出为结构化清单，用于内部简报或公开资源推荐。

开发人员测试 URL 解析与规范化逻辑：本项目提供的纯 URL 操作接口可作为单元测试的样本来源，帮助验证各类协议处理、路径拼接与查询参数保留的正确性。

学术研究中的信源可追溯性记录：研究人员在引用网络信息时，可利用本项目的归档列表功能记录访问时间、状态码与链接快照，增强引用证据链的完整性和透明度。

个人用户日常信息消费的去重过滤：普通用户可将频繁访问的新闻链接导入系统，利用标签与过滤规则屏蔽不感兴趣的主题，仅保留高优先级内容进行集中阅读。

## 快速开始

以下指令适用于 Linux / macOS / Windows WSL 环境。项目基于 Node.js 开发，需提前安装 Node.js 16.x 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/newslink-aggregator.git

# 进入项目目录
cd newslink-aggregator

# 安装依赖包
npm install

# 启动开发服务器
npm run dev
```

执行完成后，访问终端输出的本地地址（默认为 http://localhost:5173）即可使用界面。生产环境构建请执行 `npm run build`，构建产物位于 `dist` 目录。

## 安装要求

| 依赖 | 必需 | 说明 |
|------|------|------|
| Node.js | 是 | 版本 16.x 至 20.x，用于运行构建工具与本地开发服务器 |
| npm | 是 | 随 Node.js 一起安装，用于管理项目依赖包 |
| Git | 是 | 用于克隆仓库及版本控制，推荐 2.25 以上版本 |
| 现代浏览器 | 否 | 仅开发调试需要，生产环境为静态文件，无浏览器兼容性强制要求 |
| 磁盘空间 | 是 | 至少 50 MB 空闲空间用于存放源码、依赖及构建产物 |
| 网络连接 | 否 | 首次安装依赖时需要网络，后续运行无需联网（链接检测功能除外） |
| 操作系统 | 否 | 无特定限制，Windows / Linux / macOS 均可运行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何导入链接、添加标签、执行批量验证以及导出结果数据 |
| 开发者指南 | /docs/developer-guide.md | 项目目录结构说明、核心模块职责、如何扩展新的过滤器或导出格式 |
| API 参考 | /docs/api-reference.md | 查询接口的请求参数格式、返回字段含义、状态码与错误处理规范 |
| 部署说明 | /docs/deployment.md | 如何将构建产物部署到 Nginx、Apache 或静态托管服务（如 Netlify、Vercel） |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/258534.htm
- http://m.3g.ghtkgg.cn/nnews/56261.htm
- http://m.3g.ghtkgg.cn/nnews/27002.htm
- http://m.3g.ghtkgg.cn/nnews/184029.htm
- http://m.3g.ghtkgg.cn/nnews/824732.htm
- http://m.3g.ghtkgg.cn/nnews/2396.htm
- http://m.3g.ghtkgg.cn/nnews/8562.htm
- http://m.3g.ghtkgg.cn/nnews/19803.htm
- http://m.3g.ghtkgg.cn/nnews/3132810.htm
- http://m.3g.ghtkgg.cn/nnews/5536200.htm
- http://m.3g.ghtkgg.cn/nnews/199005.htm
- http://m.3g.ghtkgg.cn/nnews/7701700.htm
- http://m.3g.ghtkgg.cn/nnews/3243558.htm
- http://m.3g.ghtkgg.cn/nnews/7476.htm
- http://m.3g.ghtkgg.cn/nnews/2994600.htm
- http://m.3g.ghtkgg.cn/nnews/552698.htm
- http://m.3g.ghtkgg.cn/nnews/1926676.htm
- http://m.3g.ghtkgg.cn/nnews/83833.htm
- http://m.3g.ghtkgg.cn/nnews/6886.htm
- http://m.3g.ghtkgg.cn/nnews/776602.htm
- http://m.3g.ghtkgg.cn/nnews/15635.htm
- http://m.3g.ghtkgg.cn/nnews/405209.htm
- http://m.3g.ghtkgg.cn/nnews/05401.htm
- http://m.3g.ghtkgg.cn/nnews/1435049.htm
- http://m.3g.ghtkgg.cn/nnews/9425635.htm
- http://m.3g.ghtkgg.cn/nnews/9124409.htm
- http://m.3g.ghtkgg.cn/nnews/8084948.htm
- http://m.3g.ghtkgg.cn/nnews/9581.htm
- http://m.3g.ghtkgg.cn/nnews/071996.htm
- http://m.3g.ghtkgg.cn/nnews/370086.htm
- http://m.3g.ghtkgg.cn/nnews/8122345.htm
- http://m.3g.ghtkgg.cn/nnews/5409283.htm
- http://m.3g.ghtkgg.cn/nnews/515430.htm
- http://m.3g.ghtkgg.cn/nnews/6299287.htm
- http://m.3g.ghtkgg.cn/nnews/1518.htm
- http://m.3g.ghtkgg.cn/nnews/789954.htm
- http://m.3g.ghtkgg.cn/nnews/597216.htm
- http://m.3g.ghtkgg.cn/nnews/80447.htm
- http://m.3g.ghtkgg.cn/nnews/474360.htm
- http://m.3g.ghtkgg.cn/nnews/5549481.htm
- http://m.3g.ghtkgg.cn/nnews/6083.htm
- http://m.3g.ghtkgg.cn/nnews/5363.htm
- http://m.3g.ghtkgg.cn/nnews/65959.htm
- http://m.3g.ghtkgg.cn/nnews/3738666.htm
- http://m.3g.ghtkgg.cn/nnews/189272.htm
- http://m.3g.ghtkgg.cn/nnews/00947.htm
- http://m.3g.ghtkgg.cn/nnews/7141550.htm
- http://m.3g.ghtkgg.cn/nnews/6613.htm
- http://m.3g.ghtkgg.cn/nnews/55998.htm
- http://m.3g.ghtkgg.cn/nnews/218969.htm
- http://m.3g.ghtkgg.cn/nnews/9843.htm
- http://m.3g.ghtkgg.cn/nnews/8418.htm
- http://m.3g.ghtkgg.cn/nnews/79458.htm
- http://m.3g.ghtkgg.cn/nnews/320463.htm
- http://m.3g.ghtkgg.cn/nnews/5021.htm
- http://m.3g.ghtkgg.cn/nnews/698605.htm
- http://m.3g.ghtkgg.cn/nnews/2002.htm
- http://m.3g.ghtkgg.cn/nnews/47546.htm
- http://m.3g.ghtkgg.cn/nnews/73727.htm
- http://m.3g.ghtkgg.cn/nnews/0260.htm
- http://m.3g.ghtkgg.cn/nnews/94219.htm
- http://m.3g.ghtkgg.cn/nnews/2720.htm
- http://m.3g.ghtkgg.cn/nnews/77048.htm
- http://m.3g.ghtkgg.cn/nnews/97329.htm
- http://m.3g.ghtkgg.cn/nnews/7867.htm
- http://m.3g.ghtkgg.cn/nnews/582707.htm
- http://m.3g.ghtkgg.cn/nnews/518227.htm
- http://m.3g.ghtkgg.cn/nnews/879280.htm
- http://m.3g.ghtkgg.cn/nnews/63144.htm
- http://m.3g.ghtkgg.cn/nnews/142347.htm
- http://m.3g.ghtkgg.cn/nnews/69450.htm
- http://m.3g.ghtkgg.cn/nnews/3308013.htm
- http://m.3g.ghtkgg.cn/nnews/12574.htm
- http://m.3g.ghtkgg.cn/nnews/78986.htm
- http://m.3g.ghtkgg.cn/nnews/77277.htm
- http://m.3g.ghtkgg.cn/nnews/93878.htm
- http://m.3g.ghtkgg.cn/nnews/3345558.htm
- http://m.3g.ghtkgg.cn/nnews/8383796.htm
- http://m.3g.ghtkgg.cn/nnews/681135.htm
- http://m.3g.ghtkgg.cn/nnews/2211033.htm
- http://m.3g.ghtkgg.cn/nnews/900680.htm
- http://m.3g.ghtkgg.cn/nnews/15741.htm
- http://m.3g.ghtkgg.cn/nnews/125740.htm
- http://m.3g.ghtkgg.cn/nnews/71983.htm
- http://m.3g.ghtkgg.cn/nnews/7368124.htm
- http://m.3g.ghtkgg.cn/nnews/5090.htm
- http://m.3g.ghtkgg.cn/nnews/5332.htm
- http://m.3g.ghtkgg.cn/nnews/944737.htm
- http://m.3g.ghtkgg.cn/nnews/1140609.htm
- http://m.3g.ghtkgg.cn/nnews/308147.htm
- http://m.3g.ghtkgg.cn/nnews/9325781.htm
- http://m.3g.ghtkgg.cn/nnews/0820.htm
- http://m.3g.ghtkgg.cn/nnews/477270.htm
- http://m.3g.ghtkgg.cn/nnews/7732882.htm
- http://m.3g.ghtkgg.cn/nnews/752049.htm
- http://m.3g.ghtkgg.cn/nnews/0116863.htm
- http://m.3g.ghtkgg.cn/nnews/79105.htm
- http://m.3g.ghtkgg.cn/nnews/1441581.htm
- http://m.3g.ghtkgg.cn/nnews/3394.htm
- http://m.3g.ghtkgg.cn/nnews/617102.htm
- http://m.3g.ghtkgg.cn/nnews/9579795.htm
- http://m.3g.ghtkgg.cn/nnews/7349.htm
- http://m.3g.ghtkgg.cn/nnews/6224602.htm
- http://m.3g.ghtkgg.cn/nnews/8610592.htm
- http://m.3g.ghtkgg.cn/nnews/5862876.htm
- http://m.3g.ghtkgg.cn/nnews/1134166.htm
- http://m.3g.ghtkgg.cn/nnews/5992246.htm
- http://m.3g.ghtkgg.cn/nnews/0189.htm
- http://m.3g.ghtkgg.cn/nnews/59107.htm
- http://m.3g.ghtkgg.cn/nnews/613718.htm
- http://m.3g.ghtkgg.cn/nnews/7353.htm
- http://m.3g.ghtkgg.cn/nnews/1246.htm
- http://m.3g.ghtkgg.cn/nnews/27582.htm
- http://m.3g.ghtkgg.cn/nnews/11361.htm
- http://m.3g.ghtkgg.cn/nnews/22797.htm
- http://m.3g.ghtkgg.cn/nnews/0833.htm
- http://m.3g.ghtkgg.cn/nnews/98677.htm
- http://m.3g.ghtkgg.cn/nnews/1585239.htm
- http://m.3g.ghtkgg.cn/nnews/4110622.htm
- http://m.3g.ghtkgg.cn/nnews/009101.htm
- http://m.3g.ghtkgg.cn/nnews/9805893.htm
- http://m.3g.ghtkgg.cn/nnews/538546.htm
- http://m.3g.ghtkgg.cn/nnews/4290160.htm
- http://m.3g.ghtkgg.cn/nnews/15126.htm
- http://m.3g.ghtkgg.cn/nnews/480896.htm
- http://m.3g.ghtkgg.cn/nnews/0703.htm
- http://m.3g.ghtkgg.cn/nnews/5307.htm
- http://m.3g.ghtkgg.cn/nnews/3331216.htm
- http://m.3g.ghtkgg.cn/nnews/137753.htm
- http://m.3g.ghtkgg.cn/nnews/58481.htm
- http://m.3g.ghtkgg.cn/nnews/1450762.htm
- http://m.3g.ghtkgg.cn/nnews/0022.htm
- http://m.3g.ghtkgg.cn/nnews/91459.htm
- http://m.3g.ghtkgg.cn/nnews/8802637.htm
- http://m.3g.ghtkgg.cn/nnews/91686.htm
- http://m.3g.ghtkgg.cn/nnews/9560685.htm
- http://m.3g.ghtkgg.cn/nnews/59102.htm
- http://m.3g.ghtkgg.cn/nnews/83607.htm
- http://m.3g.ghtkgg.cn/nnews/9053.htm
- http://m.3g.ghtkgg.cn/nnews/77221.htm
- http://m.3g.ghtkgg.cn/nnews/527741.htm
- http://m.3g.ghtkgg.cn/nnews/94271.htm
- http://m.3g.ghtkgg.cn/nnews/0910.htm
- http://m.3g.ghtkgg.cn/nnews/0372400.htm
- http://m.3g.ghtkgg.cn/nnews/8773.htm
- http://m.3g.ghtkgg.cn/nnews/007396.htm
- http://m.3g.ghtkgg.cn/nnews/222961.htm
- http://m.3g.ghtkgg.cn/nnews/5515106.htm
- http://m.3g.ghtkgg.cn/nnews/752985.htm
- http://m.3g.ghtkgg.cn/nnews/16910.htm
- http://m.3g.ghtkgg.cn/nnews/1550987.htm
- http://m.3g.ghtkgg.cn/nnews/5421570.htm
- http://m.3g.ghtkgg.cn/nnews/8549.htm
- http://m.3g.ghtkgg.cn/nnews/9793593.htm
- http://m.3g.ghtkgg.cn/nnews/0270587.htm
- http://m.3g.ghtkgg.cn/nnews/5247274.htm
- http://m.3g.ghtkgg.cn/nnews/0468.htm
- http://m.3g.ghtkgg.cn/nnews/057687.htm
- http://m.3g.ghtkgg.cn/nnews/6999.htm
- http://m.3g.ghtkgg.cn/nnews/5448.htm
- http://m.3g.ghtkgg.cn/nnews/82328.htm
- http://m.3g.ghtkgg.cn/nnews/40783.htm
- http://m.3g.ghtkgg.cn/nnews/45906.htm
- http://m.3g.ghtkgg.cn/nnews/31083.htm
- http://m.3g.ghtkgg.cn/nnews/9544.htm
- http://m.3g.ghtkgg.cn/nnews/718514.htm
- http://m.3g.ghtkgg.cn/nnews/1024084.htm
- http://m.3g.ghtkgg.cn/nnews/2095.htm
- http://m.3g.ghtkgg.cn/nnews/9688.htm
- http://m.3g.ghtkgg.cn/nnews/42031.htm
- http://m.3g.ghtkgg.cn/nnews/1632081.htm
- http://m.3g.ghtkgg.cn/nnews/4516739.htm
- http://m.3g.ghtkgg.cn/nnews/8029.htm
- http://m.3g.ghtkgg.cn/nnews/01920.htm
- http://m.3g.ghtkgg.cn/nnews/3745711.htm
- http://m.3g.ghtkgg.cn/nnews/12328.htm
- http://m.3g.ghtkgg.cn/nnews/16499.htm
- http://m.3g.ghtkgg.cn/nnews/56236.htm
- http://m.3g.ghtkgg.cn/nnews/2862.htm
- http://m.3g.ghtkgg.cn/nnews/66821.htm
- http://m.3g.ghtkgg.cn/nnews/318923.htm
- http://m.3g.ghtkgg.cn/nnews/51507.htm
- http://m.3g.ghtkgg.cn/nnews/403098.htm
- http://m.3g.ghtkgg.cn/nnews/88344.htm
- http://m.3g.ghtkgg.cn/nnews/74745.htm
- http://m.3g.ghtkgg.cn/nnews/2366894.htm
- http://m.3g.ghtkgg.cn/nnews/198950.htm
- http://m.3g.ghtkgg.cn/nnews/575772.htm
- http://m.3g.ghtkgg.cn/nnews/881138.htm
- http://m.3g.ghtkgg.cn/nnews/2917.htm
- http://m.3g.ghtkgg.cn/nnews/97150.htm
- http://m.3g.ghtkgg.cn/nnews/1647.htm
- http://m.3g.ghtkgg.cn/nnews/9316184.htm
- http://m.3g.ghtkgg.cn/nnews/1902717.htm
- http://m.3g.ghtkgg.cn/nnews/023639.htm
- http://m.3g.ghtkgg.cn/nnews/9988.htm
- http://m.3g.ghtkgg.cn/nnews/069305.htm
- http://m.3g.ghtkgg.cn/nnews/03164.htm
- http://m.3g.ghtkgg.cn/nnews/93345.htm
- http://m.3g.ghtkgg.cn/nnews/27136.htm
- http://m.3g.ghtkgg.cn/nnews/3718527.htm
- http://m.3g.ghtkgg.cn/nnews/9661989.htm
- http://m.3g.ghtkgg.cn/nnews/43375.htm
- http://m.3g.ghtkgg.cn/nnews/8270.htm
- http://m.3g.ghtkgg.cn/nnews/90198.htm
- http://m.3g.ghtkgg.cn/nnews/6801806.htm
- http://m.3g.ghtkgg.cn/nnews/45679.htm
- http://m.3g.ghtkgg.cn/nnews/213335.htm
- http://m.3g.ghtkgg.cn/nnews/1846390.htm
- http://m.3g.ghtkgg.cn/nnews/782492.htm
- http://m.3g.ghtkgg.cn/nnews/27214.htm
- http://m.3g.ghtkgg.cn/nnews/442065.htm
- http://m.3g.ghtkgg.cn/nnews/3595.htm
- http://m.3g.ghtkgg.cn/nnews/95666.htm
- http://m.3g.ghtkgg.cn/nnews/00199.htm
- http://m.3g.ghtkgg.cn/nnews/427585.htm
- http://m.3g.ghtkgg.cn/nnews/2469066.htm
- http://m.3g.ghtkgg.cn/nnews/55091.htm
- http://m.3g.ghtkgg.cn/nnews/5314591.htm
- http://m.3g.ghtkgg.cn/nnews/3891872.htm
- http://m.3g.ghtkgg.cn/nnews/9361025.htm
- http://m.3g.ghtkgg.cn/nnews/313829.htm
- http://m.3g.ghtkgg.cn/nnews/05611.htm
- http://m.3g.ghtkgg.cn/nnews/9877.htm
- http://m.3g.ghtkgg.cn/nnews/12146.htm
- http://m.3g.ghtkgg.cn/nnews/506587.htm
- http://m.3g.ghtkgg.cn/nnews/4307038.htm
- http://m.3g.ghtkgg.cn/nnews/2989736.htm
- http://m.3g.ghtkgg.cn/nnews/952115.htm
- http://m.3g.ghtkgg.cn/nnews/675066.htm
- http://m.3g.ghtkgg.cn/nnews/36355.htm
- http://m.3g.ghtkgg.cn/nnews/9640.htm
- http://m.3g.ghtkgg.cn/nnews/0124330.htm
- http://m.3g.ghtkgg.cn/nnews/8896.htm
- http://m.3g.ghtkgg.cn/nnews/981480.htm
- http://m.3g.ghtkgg.cn/nnews/32781.htm
- http://m.3g.ghtkgg.cn/nnews/8591693.htm
- http://m.3g.ghtkgg.cn/nnews/5273716.htm
- http://m.3g.ghtkgg.cn/nnews/60575.htm
- http://m.3g.ghtkgg.cn/nnews/617600.htm
- http://m.3g.ghtkgg.cn/nnews/1250.htm
- http://m.3g.ghtkgg.cn/nnews/9062070.htm
- http://m.3g.ghtkgg.cn/nnews/3864.htm
- http://m.3g.ghtkgg.cn/nnews/905037.htm
- http://m.3g.ghtkgg.cn/nnews/9858.htm
- http://m.3g.ghtkgg.cn/nnews/0789450.htm
- http://m.3g.ghtkgg.cn/nnews/149979.htm
- http://m.3g.ghtkgg.cn/nnews/056584.htm
- http://m.3g.ghtkgg.cn/nnews/4788441.htm
- http://m.3g.ghtkgg.cn/nnews/445951.htm
- http://m.3g.ghtkgg.cn/nnews/789725.htm
- http://m.3g.ghtkgg.cn/nnews/3421222.htm
- http://m.3g.ghtkgg.cn/nnews/38548.htm
- http://m.3g.ghtkgg.cn/nnews/071672.htm
- http://m.3g.ghtkgg.cn/nnews/288010.htm
- http://m.3g.ghtkgg.cn/nnews/157872.htm
- http://m.3g.ghtkgg.cn/nnews/91015.htm
- http://m.3g.ghtkgg.cn/nnews/42130.htm
- http://m.3g.ghtkgg.cn/nnews/975112.htm
- http://m.3g.ghtkgg.cn/nnews/5721.htm
- http://m.3g.ghtkgg.cn/nnews/991610.htm
- http://m.3g.ghtkgg.cn/nnews/55204.htm
- http://m.3g.ghtkgg.cn/nnews/4786.htm
- http://m.3g.ghtkgg.cn/nnews/161538.htm
- http://m.3g.ghtkgg.cn/nnews/0053160.htm
- http://m.3g.ghtkgg.cn/nnews/9477495.htm
- http://m.3g.ghtkgg.cn/nnews/185118.htm
- http://m.3g.ghtkgg.cn/nnews/1807.htm
- http://m.3g.ghtkgg.cn/nnews/9536.htm
- http://m.3g.ghtkgg.cn/nnews/0010.htm
- http://m.3g.ghtkgg.cn/nnews/91540.htm
- http://m.3g.ghtkgg.cn/nnews/038720.htm
- http://m.3g.ghtkgg.cn/nnews/2783570.htm
- http://m.3g.ghtkgg.cn/nnews/09987.htm
- http://m.3g.ghtkgg.cn/nnews/0233.htm
- http://m.3g.ghtkgg.cn/nnews/706129.htm
- http://m.3g.ghtkgg.cn/nnews/18689.htm
- http://m.3g.ghtkgg.cn/nnews/67432.htm
- http://m.3g.ghtkgg.cn/nnews/3860303.htm
- http://m.3g.ghtkgg.cn/nnews/42059.htm
- http://m.3g.ghtkgg.cn/nnews/705910.htm
- http://m.3g.ghtkgg.cn/nnews/1543586.htm
- http://m.3g.ghtkgg.cn/nnews/44543.htm
- http://m.3g.ghtkgg.cn/nnews/5333.htm
- http://m.3g.ghtkgg.cn/nnews/814403.htm
- http://m.3g.ghtkgg.cn/nnews/423470.htm
- http://m.3g.ghtkgg.cn/nnews/5184061.htm
- http://m.3g.ghtkgg.cn/nnews/1424.htm
- http://m.3g.ghtkgg.cn/nnews/706206.htm
- http://m.3g.ghtkgg.cn/nnews/515408.htm
- http://m.3g.ghtkgg.cn/nnews/661392.htm
- http://m.3g.ghtkgg.cn/nnews/8896752.htm
- http://m.3g.ghtkgg.cn/nnews/54157.htm
- http://m.3g.ghtkgg.cn/nnews/5638780.htm
- http://m.3g.ghtkgg.cn/nnews/7328251.htm
- http://m.3g.ghtkgg.cn/nnews/7070.htm
- http://m.3g.ghtkgg.cn/nnews/99822.htm
- http://m.3g.ghtkgg.cn/nnews/0196.htm
- http://m.3g.ghtkgg.cn/nnews/29219.htm
- http://m.3g.ghtkgg.cn/nnews/4553.htm

## 项目结构

```
newslink-aggregator/
├── public/                         # 静态资源目录，不经过构建工具处理
│   └── favicon.ico                 # 站点图标
├── src/                            # 核心源代码目录
│   ├── core/                       # 核心业务逻辑模块
│   │   ├── linkParser.js           # URL 解析与规范化，处理路径提取与参数保留
│   │   ├── deduplicator.js         # 基于 Set 和哈希的去重引擎，支持内存与持久化两种模式
│   │   └── validator.js            # HTTP 状态检测与超时重试，支持并发控制
│   ├── filters/                    # 过滤规则实现
│   │   ├── blacklist.js            # 正则黑名单匹配，支持从外部文件加载规则集
│   │   └── whitelist.js            # 白名单优先模式，用于严格场景
│   ├── ui/                         # 前端界面组件
│   │   ├── components/             # Vue/React 组件（根据构建配置切换）
│   │   │   ├── LinkTable.vue       # 链接列表主表格，支持排序与分页
│   │   │   ├── TagManager.vue      # 标签增删改界面
│   │   │   └── StatusBadge.vue     # 可用性状态徽标渲染
│   │   └── styles/                 # 全局样式与主题变量
│   │       ├── light.css           # 亮色主题变量定义
│   │       └── dark.css            # 暗色主题变量定义
│   ├── api/                        # 轻量级 API 路由
│   │   ├── query.js                # 接受 tag / idRange / keyword 参数，返回过滤后的列表
│   │   └── export.js               # 提供 JSON / CSV / TXT 三种导出端点
│   └── main.js                     # 应用入口，负责挂载路由与初始化全局状态
├── tests/                          # 单元测试与集成测试
│   ├── parser.test.js              # 链接解析函数的边界条件测试
│   ├── validator.test.js           # 模拟 HTTP 响应的可用性检测测试
│   └── fixtures/                   # 测试用的固定数据样本
├── docs/                           # 详细文档（见文档导航章节）
├── scripts/                        # 辅助脚本（批量导入、数据迁移等）
├── package.json                    # npm 依赖清单与脚本定义
└── README.md                       # 本文档
```

## 贡献指南

我们欢迎并感谢任何形式的贡献，包括但不限于提交问题报告、改进文档、新增功能或修复缺陷。请遵循以下步骤以确保协作顺畅。

第一步：查阅现有 Issues 与 Pull Requests。在开始工作之前，请浏览 GitHub Issues 列表，确认您要解决的问题或希望添加的功能尚未被其他人认领或实现。如无相关记录，请新建一个 Issue 简要描述您的意图。

第二步：派生项目并创建功能分支。将本项目派生至您的个人账户，然后在本地仓库中基于 main 分支创建一个新的分支，分支命名建议采用 `feature/简短描述` 或 `fix/问题编号` 的格式。

第三步：编写或修改代码并添加测试。所有新增功能必须包含相应的单元测试，所有修复必须附带回归测试。请确保现有测试套件全部通过，且代码风格符合项目配置的 ESLint 规则。

第四步：提交变更并推送至远程分支。提交信息请采用约定式提交格式，例如 `feat: 添加按日期范围过滤链接的功能` 或 `fix: 修正长 URL 在表格中换行错位的问题`。提交前请运行 `npm run lint` 与 `npm run test` 进行自检。

第五步：发起 Pull Request 并等待审阅。从您的功能分支向本项目的 main 分支提交 Pull Request，在描述中关联对应的 Issue 编号，并简要说明您的实现思路与测试覆盖情况。维护者将在 3 个工作日内给予反馈。

## 常见问题

问：项目是否存储或缓存新闻页面的完整正文内容？

答：不存储。本项目仅维护 URL 字符串及其附属的标签、状态与时间戳等元数据，不抓取、不缓存、不转发任何新闻页面的 HTML 或文本内容。所有链接的访问均需要用户自行通过网络请求进行，本项目不充当内容代理或镜像源。

问：如何导入大量历史链接？是否有数量上限？

答：您可以通过 `scripts/batch-import.js` 脚本读取纯文本或 CSV 文件进行批量导入。单次导入数量无硬性上限，但建议每批不超过 5000 条以避免浏览器内存占用过高。对于超过 10000 条的列表，推荐使用 Node.js 命令行模式而非浏览器界面执行导入。

问：链接可用性检测是否会影响目标服务器的正常访问？

答：检测模块默认使用 HEAD 请求，仅获取响应头信息而不下载响应体，单次检测的超时设置为 5 秒，且并发请求数限制为 10 个。该策略旨在最小化对目标服务器的压力，但仍建议用户在非高峰时段执行大规模验证任务，并遵守目标网站 robots.txt 中的爬取规范。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:53
