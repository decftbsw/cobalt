# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研与信息聚合场景的轻量级导航聚合系统，定位于帮助开发者、运维人员与技术研究者快速检索、分类管理与批量访问分散在互联网各处的技术博文、新闻动态与参考资料。该项目不依赖复杂后端架构，以静态资源聚合与前端检索为核心，适用于搭建个人或团队内部的技术外链收藏与分享平台。

WebIndex 以资源链接的标准化入库、标签化组织和全文检索为主要工作流，内置简易爬虫框架与数据清洗管道，支持将原始 URL 批量导入并自动抽取标题、摘要及发布时间。项目采用模块化设计，核心解析引擎与展示层解耦，便于二次开发或集成至现有知识管理体系。目标用户包括需要维护技术周报的社区运营者、从事竞品分析的研发效能团队以及希望系统化管理学习资料的个人开发者。

## 功能概览

批量链接导入与去重校验 支持从文本文件或标准输入流批量载入 URL 列表，自动识别重复条目并生成导入报告。

智能元数据抽取 对每条链接发起轻量级 HEAD 与 GET 请求，解析 HTML 标题、 meta 描述及正文首段，形成结构化索引条目。

多维度标签分类 允许用户为每条记录附加自定义标签，支持层级标签体系与批量标签操作，便于按主题、来源或优先级归组。

全文检索与过滤 基于倒排索引实现标题与摘要的快速检索，同时支持按标签、域名、导入时间区间进行组合过滤。

响应式链接展示面板 以列表、卡片与表格三种视图呈现索引结果，每条记录包含标题、摘要、来源域名、标签集合及最后校验状态。

定时健康检查 后台任务周期性地对已收录链接发起可用性探测，标记失效链接并生成告警通知，保证资源列表的鲜活度。

数据导入导出 支持 JSON、CSV 与 Markdown 三种格式的完整数据导出，便于迁移至其他系统或生成静态站点页面。

访问统计与点击追踪 记录每条链接的点击次数与最后访问时间，提供简单的热度排序功能，辅助用户识别高频参考资源。

## 应用场景

技术团队内部知识库构建 研发团队可将日常遇到的调试记录、架构方案文档与官方公告通过 WebIndex 统一入库，按项目或技术栈打标，替代浏览器收藏夹的碎片化管理。新成员入职时可通过标签筛选快速了解团队常用的技术参考源。

开源项目文档聚合 开源社区维护者可使用 WebIndex 收集与项目相关的周边生态链接，如插件列表、案例演示、性能测试报告等，并以卡片面板形式展示在项目官网的生态页面中，降低用户寻找扩展资源的门槛。

技术周报与月刊素材管理 内容编辑人员可将候选文章链接批量导入，利用元数据抽取功能自动生成摘要，再通过标签筛选与全文检索快速组稿，大幅减少人工整理时间。定时健康检查可提前发现已失效的参考链接，避免对外发布死链。

个人学习路径规划 学习者可按技术领域（如容器编排、性能调优、安全审计）创建分类标签，将散落的教程、视频与实战项目链接集中存储，并通过点击统计识别高频回看内容，动态调整学习重点。

## 快速开始

以下指令适用于 Linux / macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆代码仓库
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装依赖（使用 pip 与虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化数据库并启动开发服务
python manage.py migrate
python manage.py runserver 0.0.0.0:8000
```

访问 http://127.0.0.1:8000 即可进入索引面板，首次启动时系统会自动创建示例分类与演示数据。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 - 3.11 | 核心运行环境，低于 3.8 将无法解析类型注解 |
| Django | 3.2 LTS | Web 框架，用于提供管理界面与 API 端点 |
| SQLite | 3.28+ | 默认内置数据库，生产环境可切换至 PostgreSQL 12+ |
| requests | 2.28+ | 用于发起 HTTP 请求，获取页面元数据 |
| lxml | 4.9+ | HTML 解析引擎，提供高性能的 DOM 遍历与 XPath 支持 |
| redis | 6.2+ | 可选组件，用于缓存元数据抽取结果以提升批量处理速度 |
| Node.js | 16+ | 仅前端构建时需要，用于编译静态资源与样式文件 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何进行批量导入、标签管理、视图切换与数据导出 |
| 开发指南 | /docs/developer/ | 如何扩展解析器、自定义标签规则及替换前端模板引擎 |
| API 参考 | /docs/api/ | RESTful 接口的请求参数与返回结构说明，支持第三方集成 |
| 运维手册 | /docs/ops/ | 生产环境部署配置、健康检查参数调优与数据备份策略 |

## 资源列表

- http://m.blog.oexnr.cn/snews/16307.htm
- http://m.blog.oexnr.cn/snews/92408.htm
- http://m.blog.oexnr.cn/snews/29631.htm
- http://m.blog.oexnr.cn/snews/68117.htm
- http://m.blog.oexnr.cn/snews/6984.htm
- http://m.blog.oexnr.cn/snews/616672.htm
- http://m.blog.oexnr.cn/snews/46382.htm
- http://m.blog.oexnr.cn/snews/9003955.htm
- http://m.blog.oexnr.cn/snews/82976.htm
- http://m.blog.oexnr.cn/snews/18266.htm
- http://m.blog.oexnr.cn/snews/6599.htm
- http://m.blog.oexnr.cn/snews/3464387.htm
- http://m.blog.oexnr.cn/snews/04999.htm
- http://m.blog.oexnr.cn/snews/94608.htm
- http://m.blog.oexnr.cn/snews/82003.htm
- http://m.blog.oexnr.cn/snews/4591617.htm
- http://m.blog.oexnr.cn/snews/34320.htm
- http://m.blog.oexnr.cn/snews/513020.htm
- http://m.blog.oexnr.cn/snews/03548.htm
- http://m.blog.oexnr.cn/snews/9009930.htm
- http://m.blog.oexnr.cn/snews/72903.htm
- http://m.blog.oexnr.cn/snews/1180.htm
- http://m.blog.oexnr.cn/snews/3749569.htm
- http://m.blog.oexnr.cn/snews/3845.htm
- http://m.blog.oexnr.cn/snews/029921.htm
- http://m.blog.oexnr.cn/snews/19548.htm
- http://m.blog.oexnr.cn/snews/2172.htm
- http://m.blog.oexnr.cn/snews/233927.htm
- http://m.blog.oexnr.cn/snews/688859.htm
- http://m.blog.oexnr.cn/snews/12507.htm
- http://m.blog.oexnr.cn/snews/701762.htm
- http://m.blog.oexnr.cn/snews/903790.htm
- http://m.blog.oexnr.cn/snews/5220.htm
- http://m.blog.oexnr.cn/snews/384148.htm
- http://m.blog.oexnr.cn/snews/7380.htm
- http://m.blog.oexnr.cn/snews/3534897.htm
- http://m.blog.oexnr.cn/snews/2062.htm
- http://m.blog.oexnr.cn/snews/8920.htm
- http://m.blog.oexnr.cn/snews/04289.htm
- http://m.blog.oexnr.cn/snews/4385642.htm
- http://m.blog.oexnr.cn/snews/93754.htm
- http://m.blog.oexnr.cn/snews/0589679.htm
- http://m.blog.oexnr.cn/snews/5020288.htm
- http://m.blog.oexnr.cn/snews/55088.htm
- http://m.blog.oexnr.cn/snews/1140043.htm
- http://m.blog.oexnr.cn/snews/563879.htm
- http://m.blog.oexnr.cn/snews/55353.htm
- http://m.blog.oexnr.cn/snews/828210.htm
- http://m.blog.oexnr.cn/snews/88508.htm
- http://m.blog.oexnr.cn/snews/9749.htm
- http://m.blog.oexnr.cn/snews/406523.htm
- http://m.blog.oexnr.cn/snews/81815.htm
- http://m.blog.oexnr.cn/snews/0768.htm
- http://m.blog.oexnr.cn/snews/2191289.htm
- http://m.blog.oexnr.cn/snews/6307.htm
- http://m.blog.oexnr.cn/snews/2675050.htm
- http://m.blog.oexnr.cn/snews/371341.htm
- http://m.blog.oexnr.cn/snews/7553.htm
- http://m.blog.oexnr.cn/snews/1113.htm
- http://m.blog.oexnr.cn/snews/30531.htm
- http://m.blog.oexnr.cn/snews/24235.htm
- http://m.blog.oexnr.cn/snews/6297.htm
- http://m.blog.oexnr.cn/snews/886152.htm
- http://m.blog.oexnr.cn/snews/44177.htm
- http://m.blog.oexnr.cn/snews/3302.htm
- http://m.blog.oexnr.cn/snews/5525.htm
- http://m.blog.oexnr.cn/snews/82674.htm
- http://m.blog.oexnr.cn/snews/973349.htm
- http://m.blog.oexnr.cn/snews/2139.htm
- http://m.blog.oexnr.cn/snews/9150.htm
- http://m.blog.oexnr.cn/snews/00206.htm
- http://m.blog.oexnr.cn/snews/1277.htm
- http://m.blog.oexnr.cn/snews/49338.htm
- http://m.blog.oexnr.cn/snews/934812.htm
- http://m.blog.oexnr.cn/snews/9810.htm
- http://m.blog.oexnr.cn/snews/07724.htm
- http://m.blog.oexnr.cn/snews/752363.htm
- http://m.blog.oexnr.cn/snews/75393.htm
- http://m.blog.oexnr.cn/snews/6004.htm
- http://m.blog.oexnr.cn/snews/87636.htm
- http://m.blog.oexnr.cn/snews/7042492.htm
- http://m.blog.oexnr.cn/snews/1610.htm
- http://m.blog.oexnr.cn/snews/89396.htm
- http://m.blog.oexnr.cn/snews/4803.htm
- http://m.blog.oexnr.cn/snews/9054390.htm
- http://m.blog.oexnr.cn/snews/4654449.htm
- http://m.blog.oexnr.cn/snews/3189.htm
- http://m.blog.oexnr.cn/snews/3421.htm
- http://m.blog.oexnr.cn/snews/7678003.htm
- http://m.blog.oexnr.cn/snews/8490842.htm
- http://m.blog.oexnr.cn/snews/12314.htm
- http://m.blog.oexnr.cn/snews/2737912.htm
- http://m.blog.oexnr.cn/snews/22874.htm
- http://m.blog.oexnr.cn/snews/10685.htm
- http://m.blog.oexnr.cn/snews/4471.htm
- http://m.blog.oexnr.cn/snews/81607.htm
- http://m.blog.oexnr.cn/snews/6173.htm
- http://m.blog.oexnr.cn/snews/191011.htm
- http://m.blog.oexnr.cn/snews/694853.htm
- http://m.blog.oexnr.cn/snews/77475.htm
- http://m.blog.oexnr.cn/snews/3711.htm
- http://m.blog.oexnr.cn/snews/33034.htm
- http://m.blog.oexnr.cn/snews/0786.htm
- http://m.blog.oexnr.cn/snews/74463.htm
- http://m.blog.oexnr.cn/snews/0518153.htm
- http://m.blog.oexnr.cn/snews/2621.htm
- http://m.blog.oexnr.cn/snews/186858.htm
- http://m.blog.oexnr.cn/snews/9297.htm
- http://m.blog.oexnr.cn/snews/1305415.htm
- http://m.blog.oexnr.cn/snews/2925.htm
- http://m.blog.oexnr.cn/snews/314947.htm
- http://m.blog.oexnr.cn/snews/8021.htm
- http://m.blog.oexnr.cn/snews/7668039.htm
- http://m.blog.oexnr.cn/snews/35717.htm
- http://m.blog.oexnr.cn/snews/651516.htm
- http://m.blog.oexnr.cn/snews/5634366.htm
- http://m.blog.oexnr.cn/snews/57808.htm
- http://m.blog.oexnr.cn/snews/4869566.htm
- http://m.blog.oexnr.cn/snews/277037.htm
- http://m.blog.oexnr.cn/snews/72840.htm
- http://m.blog.oexnr.cn/snews/5249.htm
- http://m.blog.oexnr.cn/snews/9647787.htm
- http://m.blog.oexnr.cn/snews/4770809.htm
- http://m.blog.oexnr.cn/snews/9585.htm
- http://m.blog.oexnr.cn/snews/469714.htm
- http://m.blog.oexnr.cn/snews/6285.htm
- http://m.blog.oexnr.cn/snews/2499.htm
- http://m.blog.oexnr.cn/snews/1133.htm
- http://m.blog.oexnr.cn/snews/0013.htm
- http://m.blog.oexnr.cn/snews/0002.htm
- http://m.blog.oexnr.cn/snews/8055610.htm
- http://m.blog.oexnr.cn/snews/35747.htm
- http://m.blog.oexnr.cn/snews/324491.htm
- http://m.blog.oexnr.cn/snews/6798.htm
- http://m.blog.oexnr.cn/snews/0836408.htm
- http://m.blog.oexnr.cn/snews/3012.htm
- http://m.blog.oexnr.cn/snews/047843.htm
- http://m.blog.oexnr.cn/snews/735022.htm
- http://m.blog.oexnr.cn/snews/0569034.htm
- http://m.blog.oexnr.cn/snews/603747.htm
- http://m.blog.oexnr.cn/snews/48745.htm
- http://m.blog.oexnr.cn/snews/4272.htm
- http://m.blog.oexnr.cn/snews/40058.htm
- http://m.blog.oexnr.cn/snews/21419.htm
- http://m.blog.oexnr.cn/snews/3859.htm
- http://m.blog.oexnr.cn/snews/4699.htm
- http://m.blog.oexnr.cn/snews/03507.htm
- http://m.blog.oexnr.cn/snews/5833127.htm
- http://m.blog.oexnr.cn/snews/6304745.htm
- http://m.blog.oexnr.cn/snews/344624.htm
- http://m.blog.oexnr.cn/snews/038999.htm
- http://m.blog.oexnr.cn/snews/85374.htm
- http://m.blog.oexnr.cn/snews/51724.htm
- http://m.blog.oexnr.cn/snews/513047.htm
- http://m.blog.oexnr.cn/snews/70543.htm
- http://m.blog.oexnr.cn/snews/6789102.htm
- http://m.blog.oexnr.cn/snews/6313.htm
- http://m.blog.oexnr.cn/snews/987026.htm
- http://m.blog.oexnr.cn/snews/13139.htm
- http://m.blog.oexnr.cn/snews/0349.htm
- http://m.blog.oexnr.cn/snews/7811.htm
- http://m.blog.oexnr.cn/snews/044835.htm
- http://m.blog.oexnr.cn/snews/266442.htm
- http://m.blog.oexnr.cn/snews/056115.htm
- http://m.blog.oexnr.cn/snews/749391.htm
- http://m.blog.oexnr.cn/snews/0914618.htm
- http://m.blog.oexnr.cn/snews/673946.htm
- http://m.blog.oexnr.cn/snews/46741.htm
- http://m.blog.oexnr.cn/snews/26454.htm
- http://m.blog.oexnr.cn/snews/4484041.htm
- http://m.blog.oexnr.cn/snews/3032059.htm
- http://m.blog.oexnr.cn/snews/1506348.htm
- http://m.blog.oexnr.cn/snews/018535.htm
- http://m.blog.oexnr.cn/snews/82016.htm
- http://m.blog.oexnr.cn/snews/8015602.htm
- http://m.blog.oexnr.cn/snews/19896.htm
- http://m.blog.oexnr.cn/snews/552647.htm
- http://m.blog.oexnr.cn/snews/71592.htm
- http://m.blog.oexnr.cn/snews/5684148.htm
- http://m.blog.oexnr.cn/snews/48718.htm
- http://m.blog.oexnr.cn/snews/314713.htm
- http://m.blog.oexnr.cn/snews/53180.htm
- http://m.blog.oexnr.cn/snews/7242972.htm
- http://m.blog.oexnr.cn/snews/00956.htm
- http://m.blog.oexnr.cn/snews/75916.htm
- http://m.blog.oexnr.cn/snews/2084980.htm
- http://m.blog.oexnr.cn/snews/002251.htm
- http://m.blog.oexnr.cn/snews/6494102.htm
- http://m.blog.oexnr.cn/snews/5037.htm
- http://m.blog.oexnr.cn/snews/620643.htm
- http://m.blog.oexnr.cn/snews/5049363.htm
- http://m.blog.oexnr.cn/snews/2559832.htm
- http://m.blog.oexnr.cn/snews/02145.htm
- http://m.blog.oexnr.cn/snews/7195934.htm
- http://m.blog.oexnr.cn/snews/049242.htm
- http://m.blog.oexnr.cn/snews/34183.htm
- http://m.blog.oexnr.cn/snews/4316870.htm
- http://m.blog.oexnr.cn/snews/368808.htm
- http://m.blog.oexnr.cn/snews/9301260.htm
- http://m.blog.oexnr.cn/snews/3385.htm
- http://m.blog.oexnr.cn/snews/41210.htm
- http://m.blog.oexnr.cn/snews/150569.htm
- http://m.blog.oexnr.cn/snews/2461.htm
- http://m.blog.oexnr.cn/snews/26973.htm
- http://m.blog.oexnr.cn/snews/3166.htm
- http://m.blog.oexnr.cn/snews/0887.htm
- http://m.blog.oexnr.cn/snews/87964.htm
- http://m.blog.oexnr.cn/snews/6675.htm
- http://m.blog.oexnr.cn/snews/8056.htm
- http://m.blog.oexnr.cn/snews/51412.htm
- http://m.blog.oexnr.cn/snews/328588.htm
- http://m.blog.oexnr.cn/snews/4067.htm
- http://m.blog.oexnr.cn/snews/3536025.htm
- http://m.blog.oexnr.cn/snews/279027.htm
- http://m.blog.oexnr.cn/snews/05207.htm
- http://m.blog.oexnr.cn/snews/1847.htm
- http://m.blog.oexnr.cn/snews/188339.htm
- http://m.blog.oexnr.cn/snews/8832.htm
- http://m.blog.oexnr.cn/snews/638151.htm
- http://m.blog.oexnr.cn/snews/6254344.htm
- http://m.blog.oexnr.cn/snews/870946.htm
- http://m.blog.oexnr.cn/snews/6584.htm
- http://m.blog.oexnr.cn/snews/03444.htm
- http://m.blog.oexnr.cn/snews/23002.htm
- http://m.blog.oexnr.cn/snews/7334.htm
- http://m.blog.oexnr.cn/snews/3371979.htm
- http://m.blog.oexnr.cn/snews/237459.htm
- http://m.blog.oexnr.cn/snews/0882617.htm
- http://m.blog.oexnr.cn/snews/7156208.htm
- http://m.blog.oexnr.cn/snews/60742.htm
- http://m.blog.oexnr.cn/snews/19206.htm
- http://m.blog.oexnr.cn/snews/5916147.htm
- http://m.blog.oexnr.cn/snews/41649.htm
- http://m.blog.oexnr.cn/snews/8171433.htm
- http://m.blog.oexnr.cn/snews/02309.htm
- http://m.blog.oexnr.cn/snews/22869.htm
- http://m.blog.oexnr.cn/snews/0981.htm
- http://m.blog.oexnr.cn/snews/8079564.htm
- http://m.blog.oexnr.cn/snews/776875.htm
- http://m.blog.oexnr.cn/snews/55969.htm
- http://m.blog.oexnr.cn/snews/1581558.htm
- http://m.blog.oexnr.cn/snews/9070.htm
- http://m.blog.oexnr.cn/snews/3768.htm
- http://m.blog.oexnr.cn/snews/0973.htm
- http://m.blog.oexnr.cn/snews/8683.htm
- http://m.blog.oexnr.cn/snews/7897940.htm
- http://m.blog.oexnr.cn/snews/431741.htm
- http://m.blog.oexnr.cn/snews/8673106.htm
- http://m.blog.oexnr.cn/snews/792611.htm
- http://m.blog.oexnr.cn/snews/9189.htm
- http://m.blog.oexnr.cn/snews/4926.htm
- http://m.blog.oexnr.cn/snews/64636.htm
- http://m.blog.oexnr.cn/snews/72973.htm
- http://m.blog.oexnr.cn/snews/694269.htm
- http://m.blog.oexnr.cn/snews/2871.htm
- http://m.blog.oexnr.cn/snews/4996509.htm
- http://m.blog.oexnr.cn/snews/26855.htm
- http://m.blog.oexnr.cn/snews/23243.htm
- http://m.blog.oexnr.cn/snews/265030.htm
- http://m.blog.oexnr.cn/snews/51626.htm
- http://m.blog.oexnr.cn/snews/4627073.htm
- http://m.blog.oexnr.cn/snews/5043730.htm
- http://m.blog.oexnr.cn/snews/551727.htm
- http://m.blog.oexnr.cn/snews/731747.htm
- http://m.blog.oexnr.cn/snews/000408.htm
- http://m.blog.oexnr.cn/snews/436906.htm
- http://m.blog.oexnr.cn/snews/6127017.htm
- http://m.blog.oexnr.cn/snews/074872.htm
- http://m.blog.oexnr.cn/snews/621082.htm
- http://m.blog.oexnr.cn/snews/2298.htm
- http://m.blog.oexnr.cn/snews/3061.htm
- http://m.blog.oexnr.cn/snews/89402.htm
- http://m.blog.oexnr.cn/snews/12911.htm
- http://m.blog.oexnr.cn/snews/3594382.htm
- http://m.blog.oexnr.cn/snews/1316199.htm
- http://m.blog.oexnr.cn/snews/03312.htm
- http://m.blog.oexnr.cn/snews/54712.htm
- http://m.blog.oexnr.cn/snews/1550.htm
- http://m.blog.oexnr.cn/snews/1447442.htm
- http://m.blog.oexnr.cn/snews/35679.htm
- http://m.blog.oexnr.cn/snews/4483.htm
- http://m.blog.oexnr.cn/snews/201337.htm
- http://m.blog.oexnr.cn/snews/48520.htm
- http://m.blog.oexnr.cn/snews/2740794.htm
- http://m.blog.oexnr.cn/snews/685916.htm
- http://m.blog.oexnr.cn/snews/8278.htm
- http://m.blog.oexnr.cn/snews/75956.htm
- http://m.blog.oexnr.cn/snews/0088360.htm
- http://m.blog.oexnr.cn/snews/0653.htm
- http://m.blog.oexnr.cn/snews/422377.htm
- http://m.blog.oexnr.cn/snews/3874081.htm
- http://m.blog.oexnr.cn/snews/21217.htm
- http://m.blog.oexnr.cn/snews/2467.htm
- http://m.blog.oexnr.cn/snews/238067.htm
- http://m.blog.oexnr.cn/snews/0048.htm
- http://m.blog.oexnr.cn/snews/891612.htm
- http://m.blog.oexnr.cn/snews/6440.htm
- http://m.blog.oexnr.cn/snews/484292.htm
- http://m.blog.oexnr.cn/snews/1888.htm
- http://m.blog.oexnr.cn/snews/330607.htm

## 项目结构

```
webindex/
├── bin/                                 # 命令行入口与辅助脚本
│   ├── manage.py                        # Django 管理命令封装
│   └── crawler_cli.py                   # 独立爬虫调度脚本，支持增量更新
├── core/                                # 核心数据层与业务逻辑
│   ├── indexer/                         # 索引构建模块
│   │   ├── parser.py                    # 元数据抽取器，封装 lxml 与 requests
│   │   ├── dedup.py                     # 基于 URL 指纹与标题相似度的去重算法
│   │   └── pipeline.py                  # 入库管道，协调抽取与持久化
│   ├── models/                          # 数据模型定义
│   │   ├── link.py                      # 链接实体，含 URL、标题、摘要、状态码
│   │   ├── tag.py                       # 标签实体，支持树形结构
│   │   └── audit.py                     # 健康检查记录，包含检查时间与响应码
│   └── search/                          # 检索与过滤引擎
│       ├── inverted.py                  # 倒排索引构建与查询
│       └── filter.py                    # 标签与时间范围组合过滤器
├── web/                                 # 展示层与用户交互
│   ├── views/                           # 基于类的视图集
│   │   ├── list.py                      # 列表与卡片视图，支持分页
│   │   ├── detail.py                    # 单条链接详情页
│   │   └── dashboard.py                 # 统计概览面板
│   ├── templates/                       # Jinja2 模板文件
│   │   ├── base.html                    # 基模板，含导航与全局样式
│   │   ├── link_list.html               # 列表视图模板
│   │   └── card_grid.html               # 卡片视图模板
│   └── static/                          # 编译后的 CSS 与 JavaScript
│       ├── css/                         # 基于 Tailwind 的自定义样式
│       └── js/                          # 前端交互逻辑，含搜索与标签过滤
├── conf/                                # 配置与环境变量
│   ├── settings.py                      # Django 主配置，含数据库、缓存与中间件
│   ├── celery.py                        # 周期性任务配置，含健康检查调度
│   └── logging.yaml                     # 日志分级与轮转策略
├── tests/                               # 单元测试与集成测试
│   ├── unit/                            # 针对解析器、去重器与过滤器的单测
│   └── integration/                     # 端到端导入与检索流程测试
├── docs/                                # 文档源文件，基于 Sphinx 构建
├── scripts/                             # 运维辅助脚本
│   ├── backup_db.sh                     # 数据库定时备份脚本
│   └── import_batch.sh                  # 批量导入外部链接列表的 Shell 封装
├── requirements.txt                     # Python 生产依赖锁定
├── requirements-dev.txt                 # 开发与测试额外依赖
└── README.md                            # 本文件
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账户，并克隆到本地开发环境。建议在 dev 分支上进行所有修改，避免直接操作 main 分支。

2. 安装开发依赖（pip install -r requirements-dev.txt），并运行预提交钩子（pre-commit install）以自动执行代码风格检查与单元测试。所有新增功能必须附带对应的单元测试，测试覆盖率不得低于 85%。

3. 若扩展解析器（例如新增对 PDF 或 JSON 格式的支持），请遵循 core/indexer/parser.py 中的抽象基类规范，并在 tests/unit/test_parser.py 中补充对应格式的测试用例。

4. 提交代码时请使用规范的 commit 信息格式：`<type>(<scope>): <subject>`，其中 type 可选 feat/fix/docs/style/refactor/test/chore，scope 标注影响的模块名称（如 parser/models/search）。

5. 发起 Pull Request 前请确保本地所有测试通过（pytest tests/），并同步更新 docs/ 下相关文档。PR 描述中需明确指出解决的问题或新增的功能，并附上必要的截图或 API 调用示例。

## 常见问题

问：导入大量链接时出现超时或连接中断，应如何处理？

答：系统默认将单次批量导入的上限设为 500 条，若超过该数量建议使用 scripts/import_batch.sh 脚本进行分片导入。同时可调整 conf/settings.py 中的 REQUESTS_TIMEOUT 与 BATCH_SIZE 参数，以适应网络环境较慢的场景。若中断发生在元数据抽取阶段，可通过 core/indexer/pipeline.py 中的断点续传机制恢复进度，系统会记录已成功抽取的记录 ID，再次运行时会自动跳过。

问：健康检查任务如何自定义频率与超时阈值？

答：健康检查由 Celery 周期性任务驱动，在 conf/celery.py 中通过 beat_schedule 配置项定义执行间隔，默认为每 24 小时执行一次。超时阈值可在 conf/settings.py 的 HEALTH_CHECK_TIMEOUT 变量中调整，单位为秒。若需对特定域名单独配置检查策略，可在 core/models/link.py 中扩展 domain_policy 字段，实现基于域名的差异化超时与重试次数。

问：能否将检索结果导出为外部系统可读的格式？

答：可以。系统内置了三种导出格式：JSON（完整结构化数据）、CSV（仅含标题、URL、标签、最后检查时间）以及 Markdown（生成适合嵌入文档的链接列表）。导出入口位于 web/views/list.py 中的 export_view，支持通过查询参数过滤后再导出。若需对接特定第三方系统（如 Notion 或 Confluence），可参考 docs/developer/export_extension.md 中的扩展指南，通过注册自定义渲染器实现。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
