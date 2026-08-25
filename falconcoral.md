# NewsIndex 聚合导航系统

NewsIndex 是一个面向信息聚合与快速检索的开源新闻外链汇总平台。该项目旨在为开发者、数据挖掘爱好者以及内容聚合服务提供方提供一套标准化的新闻链接采集、归类与展示方案。系统以高可用性和可扩展性为核心，支持对海量外链资源进行结构化整理，并内置了轻量级全文检索与分类过滤功能。NewsIndex 适用于需要快速搭建垂直领域新闻聚合站或个人信息看板的场景，帮助用户在信息过载时代高效定位高价值内容。

## 功能概览

- **多源外链统一接入**：支持批量导入任意数量的新闻外链，自动识别链接结构并提取元数据。
- **智能分类与标签系统**：基于规则引擎对链接进行自动归类，支持自定义分类标签。
- **全文检索与高级过滤**：内置倒排索引，支持标题、来源、时间等多维度检索与过滤。
- **链接健康度监控**：定时检测外链可达性，自动标记失效链接并生成报告。
- **响应式数据面板**：提供简洁的数据统计仪表盘，实时展示链接总数、分类占比及更新趋势。
- **开放 API 接口**：提供 RESTful API 供第三方系统调用，支持数据导出与二次开发。
- **可配置爬取策略**：支持自定义抓取频率、超时时间及 User-Agent，适应不同网站访问策略。

## 应用场景

**个人新闻聚合看板**：开发者或研究人员可通过 NewsIndex 快速搭建个人新闻聚合页面，将分散在多个站点的高频阅读源集中管理，每日定时更新，节省手动查阅时间。

**垂直领域信息监控**：面向金融、科技或医疗等垂直行业，用户可将相关领域的外链导入系统，利用分类标签与检索功能实时追踪行业动态，为决策提供数据支撑。

**内容平台数据预处理**：内容聚合平台或推荐系统团队可将 NewsIndex 作为上游数据预处理模块，对原始外链进行清洗、去重和归类，降低下游系统的数据处理复杂度。

**学术研究与数据分析**：高校或研究机构可利用 NewsIndex 收集特定时间段内的新闻链接，结合外部分析工具进行舆情分析、热点检测或传播路径研究。

## 快速开始

以下步骤指导你在本地环境中快速启动 NewsIndex 服务。

```bash
# 克隆项目仓库
git clone https://github.com/newsindex/newsindex.git

# 进入项目目录
cd newsindex

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库
python manage.py initdb

# 启动开发服务器
python manage.py runserver --host 0.0.0.0 --port 8080
```

服务启动后，访问 `http://localhost:8080` 即可进入管理面板。默认管理员账户为 `admin`，初始密码在首次启动时由控制台输出，请及时修改。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐 3.10 长期支持版 |
| SQLite | 3.28 及以上 | 默认轻量级数据库，用于存储链接元数据 |
| Redis | 6.0 及以上 | 可选依赖，用于提升缓存与爬取队列性能 |
| requests | 2.25.1 及以上 | HTTP 请求库，用于外链健康检测与内容抓取 |
| beautifulsoup4 | 4.9.3 及以上 | HTML 解析库，用于提取链接标题与摘要 |
| flask | 2.0.1 及以上 | Web 框架，提供管理界面与 RESTful API |
| flask-cors | 3.0.10 及以上 | 跨域资源共享支持，便于前后端分离部署 |
| gunicorn | 20.1.0 及以上 | 生产环境 WSGI 服务器（Linux 下推荐） |
| pytest | 7.0.0 及以上 | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何快速部署 NewsIndex？首次启动需要哪些步骤？ |
| 配置手册 | docs/configuration.md | 如何修改数据库连接、爬取频率或 API 认证方式？ |
| API 参考 | docs/api_reference.md | 提供了哪些 RESTful 端点？如何获取链接列表或添加新链接？ |
| 运维指南 | docs/operations.md | 如何监控系统状态？备份与恢复数据的最佳实践是什么？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/227841.htm
- http://m.wap.oexnr.cn/jnews/12682.htm
- http://m.wap.oexnr.cn/jnews/2871.htm
- http://m.wap.oexnr.cn/jnews/963870.htm
- http://m.wap.oexnr.cn/jnews/471327.htm
- http://m.wap.oexnr.cn/jnews/997773.htm
- http://m.wap.oexnr.cn/jnews/2713218.htm
- http://m.wap.oexnr.cn/jnews/691014.htm
- http://m.wap.oexnr.cn/jnews/8708772.htm
- http://m.wap.oexnr.cn/jnews/3071085.htm
- http://m.wap.oexnr.cn/jnews/6909.htm
- http://m.wap.oexnr.cn/jnews/3093.htm
- http://m.wap.oexnr.cn/jnews/2221.htm
- http://m.wap.oexnr.cn/jnews/16272.htm
- http://m.wap.oexnr.cn/jnews/2719.htm
- http://m.wap.oexnr.cn/jnews/2546208.htm
- http://m.wap.oexnr.cn/jnews/219126.htm
- http://m.wap.oexnr.cn/jnews/799166.htm
- http://m.wap.oexnr.cn/jnews/15779.htm
- http://m.wap.oexnr.cn/jnews/122992.htm
- http://m.wap.oexnr.cn/jnews/28762.htm
- http://m.wap.oexnr.cn/jnews/59286.htm
- http://m.wap.oexnr.cn/jnews/9465765.htm
- http://m.wap.oexnr.cn/jnews/0684.htm
- http://m.wap.oexnr.cn/jnews/569516.htm
- http://m.wap.oexnr.cn/jnews/92805.htm
- http://m.wap.oexnr.cn/jnews/11235.htm
- http://m.wap.oexnr.cn/jnews/01815.htm
- http://m.wap.oexnr.cn/jnews/218969.htm
- http://m.wap.oexnr.cn/jnews/4873.htm
- http://m.wap.oexnr.cn/jnews/9333195.htm
- http://m.wap.oexnr.cn/jnews/874617.htm
- http://m.wap.oexnr.cn/jnews/1636.htm
- http://m.wap.oexnr.cn/jnews/222437.htm
- http://m.wap.oexnr.cn/jnews/4137527.htm
- http://m.wap.oexnr.cn/jnews/516392.htm
- http://m.wap.oexnr.cn/jnews/75943.htm
- http://m.wap.oexnr.cn/jnews/951606.htm
- http://m.wap.oexnr.cn/jnews/4616.htm
- http://m.wap.oexnr.cn/jnews/591762.htm
- http://m.wap.oexnr.cn/jnews/023540.htm
- http://m.wap.oexnr.cn/jnews/61399.htm
- http://m.wap.oexnr.cn/jnews/3621.htm
- http://m.wap.oexnr.cn/jnews/932400.htm
- http://m.wap.oexnr.cn/jnews/1442456.htm
- http://m.wap.oexnr.cn/jnews/27331.htm
- http://m.wap.oexnr.cn/jnews/88672.htm
- http://m.wap.oexnr.cn/jnews/1249819.htm
- http://m.wap.oexnr.cn/jnews/49229.htm
- http://m.wap.oexnr.cn/jnews/31065.htm
- http://m.wap.oexnr.cn/jnews/741224.htm
- http://m.wap.oexnr.cn/jnews/87716.htm
- http://m.wap.oexnr.cn/jnews/499318.htm
- http://m.wap.oexnr.cn/jnews/47234.htm
- http://m.wap.oexnr.cn/jnews/4200.htm
- http://m.wap.oexnr.cn/jnews/711480.htm
- http://m.wap.oexnr.cn/jnews/445620.htm
- http://m.wap.oexnr.cn/jnews/165404.htm
- http://m.wap.oexnr.cn/jnews/70741.htm
- http://m.wap.oexnr.cn/jnews/5768.htm
- http://m.wap.oexnr.cn/jnews/7943.htm
- http://m.wap.oexnr.cn/jnews/7427375.htm
- http://m.wap.oexnr.cn/jnews/5775.htm
- http://m.wap.oexnr.cn/jnews/275123.htm
- http://m.wap.oexnr.cn/jnews/0672.htm
- http://m.wap.oexnr.cn/jnews/04821.htm
- http://m.wap.oexnr.cn/jnews/55959.htm
- http://m.wap.oexnr.cn/jnews/159954.htm
- http://m.wap.oexnr.cn/jnews/2737.htm
- http://m.wap.oexnr.cn/jnews/53902.htm
- http://m.wap.oexnr.cn/jnews/852450.htm
- http://m.wap.oexnr.cn/jnews/1944947.htm
- http://m.wap.oexnr.cn/jnews/64835.htm
- http://m.wap.oexnr.cn/jnews/236869.htm
- http://m.wap.oexnr.cn/jnews/3727109.htm
- http://m.wap.oexnr.cn/jnews/9548.htm
- http://m.wap.oexnr.cn/jnews/7242370.htm
- http://m.wap.oexnr.cn/jnews/6306968.htm
- http://m.wap.oexnr.cn/jnews/41628.htm
- http://m.wap.oexnr.cn/jnews/9008.htm
- http://m.wap.oexnr.cn/jnews/9132.htm
- http://m.wap.oexnr.cn/jnews/8846688.htm
- http://m.wap.oexnr.cn/jnews/0783.htm
- http://m.wap.oexnr.cn/jnews/1750441.htm
- http://m.wap.oexnr.cn/jnews/6356.htm
- http://m.wap.oexnr.cn/jnews/8077342.htm
- http://m.wap.oexnr.cn/jnews/2663.htm
- http://m.wap.oexnr.cn/jnews/924583.htm
- http://m.wap.oexnr.cn/jnews/870990.htm
- http://m.wap.oexnr.cn/jnews/239298.htm
- http://m.wap.oexnr.cn/jnews/377573.htm
- http://m.wap.oexnr.cn/jnews/8381.htm
- http://m.wap.oexnr.cn/jnews/1251.htm
- http://m.wap.oexnr.cn/jnews/84659.htm
- http://m.wap.oexnr.cn/jnews/8135662.htm
- http://m.wap.oexnr.cn/jnews/2922008.htm
- http://m.wap.oexnr.cn/jnews/405027.htm
- http://m.wap.oexnr.cn/jnews/99795.htm
- http://m.wap.oexnr.cn/jnews/263500.htm
- http://m.wap.oexnr.cn/jnews/4452.htm
- http://m.wap.oexnr.cn/jnews/8839.htm
- http://m.wap.oexnr.cn/jnews/4566.htm
- http://m.wap.oexnr.cn/jnews/5105369.htm
- http://m.wap.oexnr.cn/jnews/79510.htm
- http://m.wap.oexnr.cn/jnews/45334.htm
- http://m.wap.oexnr.cn/jnews/2842592.htm
- http://m.wap.oexnr.cn/jnews/696183.htm
- http://m.wap.oexnr.cn/jnews/824984.htm
- http://m.wap.oexnr.cn/jnews/48535.htm
- http://m.wap.oexnr.cn/jnews/14457.htm
- http://m.wap.oexnr.cn/jnews/61049.htm
- http://m.wap.oexnr.cn/jnews/7058008.htm
- http://m.wap.oexnr.cn/jnews/27967.htm
- http://m.wap.oexnr.cn/jnews/2738.htm
- http://m.wap.oexnr.cn/jnews/0963626.htm
- http://m.wap.oexnr.cn/jnews/294169.htm
- http://m.wap.oexnr.cn/jnews/1424247.htm
- http://m.wap.oexnr.cn/jnews/85188.htm
- http://m.wap.oexnr.cn/jnews/8081.htm
- http://m.wap.oexnr.cn/jnews/6344.htm
- http://m.wap.oexnr.cn/jnews/17080.htm
- http://m.wap.oexnr.cn/jnews/59298.htm
- http://m.wap.oexnr.cn/jnews/2639.htm
- http://m.wap.oexnr.cn/jnews/26038.htm
- http://m.wap.oexnr.cn/jnews/9522.htm
- http://m.wap.oexnr.cn/jnews/2373.htm
- http://m.wap.oexnr.cn/jnews/165615.htm
- http://m.wap.oexnr.cn/jnews/18602.htm
- http://m.wap.oexnr.cn/jnews/04257.htm
- http://m.wap.oexnr.cn/jnews/6152.htm
- http://m.wap.oexnr.cn/jnews/457026.htm
- http://m.wap.oexnr.cn/jnews/489841.htm
- http://m.wap.oexnr.cn/jnews/96801.htm
- http://m.wap.oexnr.cn/jnews/0752817.htm
- http://m.wap.oexnr.cn/jnews/69455.htm
- http://m.wap.oexnr.cn/jnews/45924.htm
- http://m.wap.oexnr.cn/jnews/01292.htm
- http://m.wap.oexnr.cn/jnews/831162.htm
- http://m.wap.oexnr.cn/jnews/8080813.htm
- http://m.wap.oexnr.cn/jnews/7403458.htm
- http://m.wap.oexnr.cn/jnews/69515.htm
- http://m.wap.oexnr.cn/jnews/8681.htm
- http://m.wap.oexnr.cn/jnews/7648223.htm
- http://m.wap.oexnr.cn/jnews/7276579.htm
- http://m.wap.oexnr.cn/jnews/03589.htm
- http://m.wap.oexnr.cn/jnews/7116.htm
- http://m.wap.oexnr.cn/jnews/772769.htm
- http://m.wap.oexnr.cn/jnews/99851.htm
- http://m.wap.oexnr.cn/jnews/8085236.htm
- http://m.wap.oexnr.cn/jnews/0841.htm
- http://m.wap.oexnr.cn/jnews/973249.htm
- http://m.wap.oexnr.cn/jnews/6265.htm
- http://m.wap.oexnr.cn/jnews/83767.htm
- http://m.wap.oexnr.cn/jnews/950869.htm
- http://m.wap.oexnr.cn/jnews/11430.htm
- http://m.wap.oexnr.cn/jnews/21974.htm
- http://m.wap.oexnr.cn/jnews/50042.htm
- http://m.wap.oexnr.cn/jnews/071895.htm
- http://m.wap.oexnr.cn/jnews/7468167.htm
- http://m.wap.oexnr.cn/jnews/89443.htm
- http://m.wap.oexnr.cn/jnews/12269.htm
- http://m.wap.oexnr.cn/jnews/328816.htm
- http://m.wap.oexnr.cn/jnews/4101274.htm
- http://m.wap.oexnr.cn/jnews/2081.htm
- http://m.wap.oexnr.cn/jnews/77735.htm
- http://m.wap.oexnr.cn/jnews/8334636.htm
- http://m.wap.oexnr.cn/jnews/02820.htm
- http://m.wap.oexnr.cn/jnews/192621.htm
- http://m.wap.oexnr.cn/jnews/092299.htm
- http://m.wap.oexnr.cn/jnews/1853419.htm
- http://m.wap.oexnr.cn/jnews/807954.htm
- http://m.wap.oexnr.cn/jnews/927246.htm
- http://m.wap.oexnr.cn/jnews/61368.htm
- http://m.wap.oexnr.cn/jnews/1163674.htm
- http://m.wap.oexnr.cn/jnews/38262.htm
- http://m.wap.oexnr.cn/jnews/45265.htm
- http://m.wap.oexnr.cn/jnews/422265.htm
- http://m.wap.oexnr.cn/jnews/88221.htm
- http://m.wap.oexnr.cn/jnews/5736.htm
- http://m.wap.oexnr.cn/jnews/358538.htm
- http://m.wap.oexnr.cn/jnews/5542779.htm
- http://m.wap.oexnr.cn/jnews/4461945.htm
- http://m.wap.oexnr.cn/jnews/210076.htm
- http://m.wap.oexnr.cn/jnews/0127.htm
- http://m.wap.oexnr.cn/jnews/1584314.htm
- http://m.wap.oexnr.cn/jnews/3274390.htm
- http://m.wap.oexnr.cn/jnews/54382.htm
- http://m.wap.oexnr.cn/jnews/2603814.htm
- http://m.wap.oexnr.cn/jnews/1101887.htm
- http://m.wap.oexnr.cn/jnews/0182.htm
- http://m.wap.oexnr.cn/jnews/2207814.htm
- http://m.wap.oexnr.cn/jnews/1005161.htm
- http://m.wap.oexnr.cn/jnews/808646.htm
- http://m.wap.oexnr.cn/jnews/21701.htm
- http://m.wap.oexnr.cn/jnews/7042.htm
- http://m.wap.oexnr.cn/jnews/6089.htm
- http://m.wap.oexnr.cn/jnews/67909.htm
- http://m.wap.oexnr.cn/jnews/4463.htm
- http://m.wap.oexnr.cn/jnews/1639.htm
- http://m.wap.oexnr.cn/jnews/7349.htm
- http://m.wap.oexnr.cn/jnews/2610.htm
- http://m.wap.oexnr.cn/jnews/055856.htm
- http://m.wap.oexnr.cn/jnews/58253.htm
- http://m.wap.oexnr.cn/jnews/4105967.htm
- http://m.wap.oexnr.cn/jnews/4334730.htm
- http://m.wap.oexnr.cn/jnews/8787177.htm
- http://m.wap.oexnr.cn/jnews/564455.htm
- http://m.wap.oexnr.cn/jnews/25632.htm
- http://m.wap.oexnr.cn/jnews/409203.htm
- http://m.wap.oexnr.cn/jnews/30167.htm
- http://m.wap.oexnr.cn/jnews/15777.htm
- http://m.wap.oexnr.cn/jnews/302475.htm
- http://m.wap.oexnr.cn/jnews/808629.htm
- http://m.wap.oexnr.cn/jnews/0170.htm
- http://m.wap.oexnr.cn/jnews/0580000.htm
- http://m.wap.oexnr.cn/jnews/409226.htm
- http://m.wap.oexnr.cn/jnews/255519.htm
- http://m.wap.oexnr.cn/jnews/3532.htm
- http://m.wap.oexnr.cn/jnews/606020.htm
- http://m.wap.oexnr.cn/jnews/5782.htm
- http://m.wap.oexnr.cn/jnews/151189.htm
- http://m.wap.oexnr.cn/jnews/788010.htm
- http://m.wap.oexnr.cn/jnews/7067070.htm
- http://m.wap.oexnr.cn/jnews/898639.htm
- http://m.wap.oexnr.cn/jnews/078534.htm
- http://m.wap.oexnr.cn/jnews/4888.htm
- http://m.wap.oexnr.cn/jnews/682286.htm
- http://m.wap.oexnr.cn/jnews/420359.htm
- http://m.wap.oexnr.cn/jnews/146452.htm
- http://m.wap.oexnr.cn/jnews/22695.htm
- http://m.wap.oexnr.cn/jnews/85301.htm
- http://m.wap.oexnr.cn/jnews/8029.htm
- http://m.wap.oexnr.cn/jnews/831599.htm
- http://m.wap.oexnr.cn/jnews/2507843.htm
- http://m.wap.oexnr.cn/jnews/83786.htm
- http://m.wap.oexnr.cn/jnews/897743.htm
- http://m.wap.oexnr.cn/jnews/9310.htm
- http://m.wap.oexnr.cn/jnews/080816.htm
- http://m.wap.oexnr.cn/jnews/786356.htm
- http://m.wap.oexnr.cn/jnews/283142.htm
- http://m.wap.oexnr.cn/jnews/00610.htm
- http://m.wap.oexnr.cn/jnews/1441245.htm
- http://m.wap.oexnr.cn/jnews/950461.htm
- http://m.wap.oexnr.cn/jnews/434758.htm
- http://m.wap.oexnr.cn/jnews/7933.htm
- http://m.wap.oexnr.cn/jnews/3174.htm
- http://m.wap.oexnr.cn/jnews/4326.htm
- http://m.wap.oexnr.cn/jnews/621238.htm
- http://m.wap.oexnr.cn/jnews/6587.htm
- http://m.wap.oexnr.cn/jnews/070786.htm
- http://m.wap.oexnr.cn/jnews/8868227.htm
- http://m.wap.oexnr.cn/jnews/2775965.htm
- http://m.wap.oexnr.cn/jnews/999018.htm
- http://m.wap.oexnr.cn/jnews/502540.htm
- http://m.wap.oexnr.cn/jnews/0080057.htm
- http://m.wap.oexnr.cn/jnews/47049.htm
- http://m.wap.oexnr.cn/jnews/0278.htm
- http://m.wap.oexnr.cn/jnews/480781.htm
- http://m.wap.oexnr.cn/jnews/146209.htm
- http://m.wap.oexnr.cn/jnews/004061.htm
- http://m.wap.oexnr.cn/jnews/08791.htm
- http://m.wap.oexnr.cn/jnews/732378.htm
- http://m.wap.oexnr.cn/jnews/3342541.htm
- http://m.wap.oexnr.cn/jnews/5762.htm
- http://m.wap.oexnr.cn/jnews/48442.htm
- http://m.wap.oexnr.cn/jnews/455457.htm
- http://m.wap.oexnr.cn/jnews/9786.htm
- http://m.wap.oexnr.cn/jnews/06971.htm
- http://m.wap.oexnr.cn/jnews/41399.htm
- http://m.wap.oexnr.cn/jnews/3673.htm
- http://m.wap.oexnr.cn/jnews/269212.htm
- http://m.wap.oexnr.cn/jnews/7645.htm
- http://m.wap.oexnr.cn/jnews/646944.htm
- http://m.wap.oexnr.cn/jnews/663355.htm
- http://m.wap.oexnr.cn/jnews/08742.htm
- http://m.wap.oexnr.cn/jnews/503525.htm
- http://m.wap.oexnr.cn/jnews/1239.htm
- http://m.wap.oexnr.cn/jnews/7507781.htm
- http://m.wap.oexnr.cn/jnews/1813.htm
- http://m.wap.oexnr.cn/jnews/547234.htm
- http://m.wap.oexnr.cn/jnews/44083.htm
- http://m.wap.oexnr.cn/jnews/2479.htm
- http://m.wap.oexnr.cn/jnews/2182777.htm
- http://m.wap.oexnr.cn/jnews/38913.htm
- http://m.wap.oexnr.cn/jnews/859678.htm
- http://m.wap.oexnr.cn/jnews/734412.htm
- http://m.wap.oexnr.cn/jnews/48731.htm
- http://m.wap.oexnr.cn/jnews/8514.htm
- http://m.wap.oexnr.cn/jnews/4553.htm
- http://m.wap.oexnr.cn/jnews/7669.htm
- http://m.wap.oexnr.cn/jnews/2119.htm
- http://m.wap.oexnr.cn/jnews/007557.htm
- http://m.wap.oexnr.cn/jnews/7435888.htm
- http://m.wap.oexnr.cn/jnews/5539.htm
- http://m.wap.oexnr.cn/jnews/5636.htm
- http://m.wap.oexnr.cn/jnews/1683635.htm
- http://m.wap.oexnr.cn/jnews/4853.htm
- http://m.wap.oexnr.cn/jnews/05043.htm
- http://m.wap.oexnr.cn/jnews/3547488.htm
- http://m.wap.oexnr.cn/jnews/96177.htm

## 项目结构

```
newsindex/
├── manage.py                 # 项目入口脚本，集成命令行管理工具
├── requirements.txt          # Python 依赖清单，锁定核心库版本
├── config/
│   ├── default.py            # 默认配置项（数据库、爬取参数、日志级别）
│   ├── development.py        # 开发环境配置，启用调试与热重载
│   └── production.py         # 生产环境配置，关闭调试，使用外部 Redis
├── app/
│   ├── __init__.py           # Flask 应用工厂，初始化扩展与蓝图
│   ├── models/
│   │   ├── link.py           # 链接数据模型，定义表结构与验证逻辑
│   │   └── category.py       # 分类数据模型，支持层级标签
│   ├── services/
│   │   ├── fetcher.py        # 外链抓取服务，处理 HTTP 请求与超时重试
│   │   ├── parser.py         # HTML 解析服务，提取标题、摘要与发布时间
│   │   └── health.py         # 链接健康度检测服务，记录响应码与响应时间
│   ├── routes/
│   │   ├── api.py            # RESTful API 路由，提供增删改查接口
│   │   └── dashboard.py      # 管理面板路由，渲染统计视图与表单
│   ├── templates/            # Jinja2 模板文件，用于服务端渲染
│   │   ├── base.html
│   │   ├── index.html
│   │   └── detail.html
│   └── static/               # 静态资源（CSS、JavaScript、图标）
│       ├── css/
│       └── js/
├── tests/                    # 单元测试与集成测试用例
│   ├── test_models.py
│   ├── test_services.py
│   └── test_routes.py
├── scripts/
│   ├── import_links.py       # 批量导入外链的脚本，支持 CSV 格式
│   └── export_stats.py       # 导出统计报告为 JSON 或 CSV
├── logs/                     # 应用日志目录，按日期滚动存储
│   └── app.log
└── data/
    └── newsindex.db          # SQLite 数据库文件（生产环境可迁移至 PostgreSQL）
```

## 贡献指南

我们欢迎社区贡献者参与 NewsIndex 的改进。请遵循以下流程提交变更。

1. 阅读项目行为准则，确保所有交互尊重且专业。在提交 Issue 或 Pull Request 前，请先在 Issues 列表中检索是否有类似问题或需求，避免重复劳动。

2. 从 `main` 分支派生个人分支，命名遵循 `feature/描述` 或 `fix/描述` 格式。所有代码变更须包含对应的单元测试，且测试覆盖率不得低于现有基线。

3. 提交代码前运行完整测试套件，确保本地无失败用例。使用 `pytest tests/` 执行全部测试，并检查日志中是否存在新增警告或错误。

4. 更新文档以反映代码变更，包括但不限于 README、配置示例和 API 参考。若新增配置项，须在 `config/default.py` 中添加注释说明。

5. 发起 Pull Request 至 `main` 分支，并在描述中关联相关 Issue 编号。项目维护者将在 7 个工作日内进行审查，必要时会要求补充修改。

## 常见问题

**问：NewsIndex 是否支持 HTTPS 访问？**

答：是的。NewsIndex 本身不强制要求 HTTPS，但建议在生产环境中使用反向代理（如 Nginx 或 Apache）终止 TLS，并将请求转发至本地 HTTP 服务。配置文件中的 `PREFERRED_URL_SCHEME` 项可设为 `https` 以生成正确的外部链接。

**问：导入大量外链时系统性能如何？**

答：单机环境下，NewsIndex 可稳定处理 10 万条链接记录。导入操作建议通过 `scripts/import_links.py` 异步执行，避免阻塞 Web 请求。若链接数量超过 50 万条，推荐使用 PostgreSQL 替代 SQLite 以获得更优的查询性能，同时开启 Redis 缓存减少重复查询。

**问：如何定期自动更新外链内容？**

答：你可以使用系统自带的定时任务模块，在配置中启用 `SCHEDULED_FETCH_ENABLED` 并设置 `FETCH_INTERVAL_HOURS`。该功能依赖 APScheduler 库，默认每天凌晨 2 点执行全量更新。若需更高频次更新，建议结合外部 Cron 作业调用 `manage.py fetch` 命令实现自定义调度。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
