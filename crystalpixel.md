# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与历史新闻存档检索的轻量级链接管理工具。项目定位于为开发者、数据分析师与内容研究员提供结构化的外部新闻链接收录与快速查阅能力，通过统一的链接索引机制将分散的新闻条目组织为可检索、可归档的资源库。本项目的核心目标用户包括需要批量管理新闻外链的运维人员、进行舆情历史回溯的研究者以及构建自定义新闻聚合流的自动化脚本开发者。项目本身不存储新闻正文，仅维护链接元数据与分类标签，通过外部链接跳转实现内容访问，解决了多源新闻链接分散、难以统一管理和快速定位的问题。

## 功能概览

链接批量导入与解析 支持通过文本文件或标准输入批量导入新闻链接，自动解析 URL 中的域名、路径与参数结构，提取内容标识符。

元数据自动提取 对每条链接自动生成收录时间戳、来源域名分类以及基于路径模式的类型标签，减少人工整理成本。

多维度检索过滤 提供按时间范围、来源域名、关键词模糊匹配等筛选方式，快速定位特定批次或主题的新闻链接。

外部链接健康检查 周期性对已收录链接发起 HEAD 请求，检测资源可达性，标记失效链接并生成报告。

数据导出与同步 支持将链接列表导出为 CSV、JSON 或纯文本格式，便于与其他数据处理流水线或可视化工具对接。

访问频次统计 记录每条链接的查询与跳转次数，生成热点链接排行，辅助识别高价值新闻来源。

标签体系与分类管理 允许用户自定义标签，为链接附加主题分类（如科技、财经、政策），支持标签组合检索。

## 应用场景

历史新闻归档与回溯 内容研究员可批量导入特定时间段的外部新闻链接，通过时间筛选快速回顾某一事件周期内的报道来源分布，用于舆情分析或事件脉络梳理。

技术文档外链管理 技术博客或开源项目文档维护者可使用本项目整理引用链接，定期检查外链可用性，避免文档中出现死链，提升文档质量。

自动化新闻聚合流构建 开发者可结合定时任务脚本，每日将新采集的新闻链接输入本项目，利用导出功能生成动态链接列表，供 RSS 生成器或静态站点生成器消费。

数据清洗与去重预处理 数据分析师在抓取新闻数据后，可利用本项目的链接解析与去重功能，清洗出规范化的 URL 列表，作为后续自然语言处理或分类模型的输入。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/news-link/news-aggregator.git

# 进入项目目录
cd news-aggregator

# 安装依赖（使用 pip 安装 Python 依赖）
pip install -r requirements.txt

# 运行初始化配置，生成默认配置文件 config.yaml
python bin/init_config.py

# 启动本地服务（默认监听 8080 端口）
python bin/server.py --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐使用 3.10 稳定版 |
| Flask | 2.2.x 及以上 | Web 服务框架，用于提供 RESTful API 与管理界面 |
| requests | 2.28.x 及以上 | 发送 HTTP 请求，用于链接健康检查与元数据获取 |
| PyYAML | 6.0.x 及以上 | 解析与生成配置文件，管理用户自定义参数 |
| SQLite | 3.35 及以上 | 内嵌数据库，存储链接元数据与标签信息，无需额外安装 |
| gunicorn | 20.1.x 及以上 | 生产环境 WSGI 服务器，仅在部署时使用 |
| pytest | 7.2.x 及以上 | 单元测试框架，仅在开发与测试环境中安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user_guide.md | 如何导入链接、如何进行检索筛选、如何导出数据、如何自定义标签 |
| 部署指南 | docs/deployment.md | 如何将服务部署到生产环境、如何配置反向代理、如何启用 HTTPS |
| API 参考 | docs/api_reference.md | 所有 RESTful 端点说明、请求参数格式、返回数据结构与状态码含义 |
| 开发指引 | docs/development.md | 项目代码结构、二次开发规范、如何新增解析器插件、如何提交代码 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/1179.htm
- http://m.3g.ghtkgg.cn/nnews/61102.htm
- http://m.3g.ghtkgg.cn/nnews/6128798.htm
- http://m.3g.ghtkgg.cn/nnews/1764086.htm
- http://m.3g.ghtkgg.cn/nnews/4531.htm
- http://m.3g.ghtkgg.cn/nnews/3349005.htm
- http://m.3g.ghtkgg.cn/nnews/48323.htm
- http://m.3g.ghtkgg.cn/nnews/6098069.htm
- http://m.3g.ghtkgg.cn/nnews/129164.htm
- http://m.3g.ghtkgg.cn/nnews/1197512.htm
- http://m.3g.ghtkgg.cn/nnews/5446.htm
- http://m.3g.ghtkgg.cn/nnews/0797682.htm
- http://m.3g.ghtkgg.cn/nnews/8848.htm
- http://m.3g.ghtkgg.cn/nnews/34127.htm
- http://m.3g.ghtkgg.cn/nnews/6460046.htm
- http://m.3g.ghtkgg.cn/nnews/3050846.htm
- http://m.3g.ghtkgg.cn/nnews/7097321.htm
- http://m.3g.ghtkgg.cn/nnews/7848.htm
- http://m.3g.ghtkgg.cn/nnews/1778535.htm
- http://m.3g.ghtkgg.cn/nnews/1557.htm
- http://m.3g.ghtkgg.cn/nnews/736590.htm
- http://m.3g.ghtkgg.cn/nnews/8708170.htm
- http://m.3g.ghtkgg.cn/nnews/6098683.htm
- http://m.3g.ghtkgg.cn/nnews/5275893.htm
- http://m.3g.ghtkgg.cn/nnews/8523702.htm
- http://m.3g.ghtkgg.cn/nnews/1489620.htm
- http://m.3g.ghtkgg.cn/nnews/52259.htm
- http://m.3g.ghtkgg.cn/nnews/2735564.htm
- http://m.3g.ghtkgg.cn/nnews/351837.htm
- http://m.3g.ghtkgg.cn/nnews/82835.htm
- http://m.3g.ghtkgg.cn/nnews/5958.htm
- http://m.3g.ghtkgg.cn/nnews/49338.htm
- http://m.3g.ghtkgg.cn/nnews/976429.htm
- http://m.3g.ghtkgg.cn/nnews/27754.htm
- http://m.3g.ghtkgg.cn/nnews/183556.htm
- http://m.3g.ghtkgg.cn/nnews/275720.htm
- http://m.3g.ghtkgg.cn/nnews/44837.htm
- http://m.3g.ghtkgg.cn/nnews/1768473.htm
- http://m.3g.ghtkgg.cn/nnews/260340.htm
- http://m.3g.ghtkgg.cn/nnews/34389.htm
- http://m.3g.ghtkgg.cn/nnews/17525.htm
- http://m.3g.ghtkgg.cn/nnews/8715446.htm
- http://m.3g.ghtkgg.cn/nnews/78021.htm
- http://m.3g.ghtkgg.cn/nnews/7361.htm
- http://m.3g.ghtkgg.cn/nnews/492485.htm
- http://m.3g.ghtkgg.cn/nnews/5650825.htm
- http://m.3g.ghtkgg.cn/nnews/1159.htm
- http://m.3g.ghtkgg.cn/nnews/9730922.htm
- http://m.3g.ghtkgg.cn/nnews/63648.htm
- http://m.3g.ghtkgg.cn/nnews/466486.htm
- http://m.3g.ghtkgg.cn/nnews/015475.htm
- http://m.3g.ghtkgg.cn/nnews/514003.htm
- http://m.3g.ghtkgg.cn/nnews/644256.htm
- http://m.3g.ghtkgg.cn/nnews/634363.htm
- http://m.3g.ghtkgg.cn/nnews/89970.htm
- http://m.3g.ghtkgg.cn/nnews/47001.htm
- http://m.3g.ghtkgg.cn/nnews/4336905.htm
- http://m.3g.ghtkgg.cn/nnews/9259.htm
- http://m.3g.ghtkgg.cn/nnews/2033686.htm
- http://m.3g.ghtkgg.cn/nnews/72795.htm
- http://m.3g.ghtkgg.cn/nnews/7127.htm
- http://m.3g.ghtkgg.cn/nnews/821302.htm
- http://m.3g.ghtkgg.cn/nnews/195911.htm
- http://m.3g.ghtkgg.cn/nnews/706673.htm
- http://m.3g.ghtkgg.cn/nnews/46659.htm
- http://m.3g.ghtkgg.cn/nnews/5797518.htm
- http://m.3g.ghtkgg.cn/nnews/7979755.htm
- http://m.3g.ghtkgg.cn/nnews/03297.htm
- http://m.3g.ghtkgg.cn/nnews/44584.htm
- http://m.3g.ghtkgg.cn/nnews/163992.htm
- http://m.3g.ghtkgg.cn/nnews/1285866.htm
- http://m.3g.ghtkgg.cn/nnews/2101.htm
- http://m.3g.ghtkgg.cn/nnews/9179610.htm
- http://m.3g.ghtkgg.cn/nnews/3651176.htm
- http://m.3g.ghtkgg.cn/nnews/22140.htm
- http://m.3g.ghtkgg.cn/nnews/009690.htm
- http://m.3g.ghtkgg.cn/nnews/378261.htm
- http://m.3g.ghtkgg.cn/nnews/04382.htm
- http://m.3g.ghtkgg.cn/nnews/1966.htm
- http://m.3g.ghtkgg.cn/nnews/21592.htm
- http://m.3g.ghtkgg.cn/nnews/3030990.htm
- http://m.3g.ghtkgg.cn/nnews/3077.htm
- http://m.3g.ghtkgg.cn/nnews/837914.htm
- http://m.3g.ghtkgg.cn/nnews/50467.htm
- http://m.3g.ghtkgg.cn/nnews/81123.htm
- http://m.3g.ghtkgg.cn/nnews/63145.htm
- http://m.3g.ghtkgg.cn/nnews/22717.htm
- http://m.3g.ghtkgg.cn/nnews/78449.htm
- http://m.3g.ghtkgg.cn/nnews/30712.htm
- http://m.3g.ghtkgg.cn/nnews/37304.htm
- http://m.3g.ghtkgg.cn/nnews/649725.htm
- http://m.3g.ghtkgg.cn/nnews/780867.htm
- http://m.3g.ghtkgg.cn/nnews/356463.htm
- http://m.3g.ghtkgg.cn/nnews/8303168.htm
- http://m.3g.ghtkgg.cn/nnews/0659.htm
- http://m.3g.ghtkgg.cn/nnews/7495553.htm
- http://m.3g.ghtkgg.cn/nnews/91071.htm
- http://m.3g.ghtkgg.cn/nnews/2056289.htm
- http://m.3g.ghtkgg.cn/nnews/96777.htm
- http://m.3g.ghtkgg.cn/nnews/72888.htm
- http://m.3g.ghtkgg.cn/nnews/93296.htm
- http://m.3g.ghtkgg.cn/nnews/77270.htm
- http://m.3g.ghtkgg.cn/nnews/9849.htm
- http://m.3g.ghtkgg.cn/nnews/32869.htm
- http://m.3g.ghtkgg.cn/nnews/216063.htm
- http://m.3g.ghtkgg.cn/nnews/09035.htm
- http://m.3g.ghtkgg.cn/nnews/5902.htm
- http://m.3g.ghtkgg.cn/nnews/0368.htm
- http://m.3g.ghtkgg.cn/nnews/2586.htm
- http://m.3g.ghtkgg.cn/nnews/8934495.htm
- http://m.3g.ghtkgg.cn/nnews/2460227.htm
- http://m.3g.ghtkgg.cn/nnews/464767.htm
- http://m.3g.ghtkgg.cn/nnews/699126.htm
- http://m.3g.ghtkgg.cn/nnews/9956.htm
- http://m.3g.ghtkgg.cn/nnews/4810.htm
- http://m.3g.ghtkgg.cn/nnews/0165.htm
- http://m.3g.ghtkgg.cn/nnews/105213.htm
- http://m.3g.ghtkgg.cn/nnews/64457.htm
- http://m.3g.ghtkgg.cn/nnews/197231.htm
- http://m.3g.ghtkgg.cn/nnews/4529.htm
- http://m.3g.ghtkgg.cn/nnews/558138.htm
- http://m.3g.ghtkgg.cn/nnews/44680.htm
- http://m.3g.ghtkgg.cn/nnews/472710.htm
- http://m.3g.ghtkgg.cn/nnews/29917.htm
- http://m.3g.ghtkgg.cn/nnews/89519.htm
- http://m.3g.ghtkgg.cn/nnews/49783.htm
- http://m.3g.ghtkgg.cn/nnews/2335.htm
- http://m.3g.ghtkgg.cn/nnews/0089.htm
- http://m.3g.ghtkgg.cn/nnews/9004.htm
- http://m.3g.ghtkgg.cn/nnews/7997.htm
- http://m.3g.ghtkgg.cn/nnews/80174.htm
- http://m.3g.ghtkgg.cn/nnews/7043785.htm
- http://m.3g.ghtkgg.cn/nnews/4488628.htm
- http://m.3g.ghtkgg.cn/nnews/0386818.htm
- http://m.3g.ghtkgg.cn/nnews/77168.htm
- http://m.3g.ghtkgg.cn/nnews/97521.htm
- http://m.3g.ghtkgg.cn/nnews/897543.htm
- http://m.3g.ghtkgg.cn/nnews/0500529.htm
- http://m.3g.ghtkgg.cn/nnews/3324220.htm
- http://m.3g.ghtkgg.cn/nnews/8527673.htm
- http://m.3g.ghtkgg.cn/nnews/281868.htm
- http://m.3g.ghtkgg.cn/nnews/471387.htm
- http://m.3g.ghtkgg.cn/nnews/644409.htm
- http://m.3g.ghtkgg.cn/nnews/74319.htm
- http://m.3g.ghtkgg.cn/nnews/5601055.htm
- http://m.3g.ghtkgg.cn/nnews/7179195.htm
- http://m.3g.ghtkgg.cn/nnews/6374.htm
- http://m.3g.ghtkgg.cn/nnews/4070.htm
- http://m.3g.ghtkgg.cn/nnews/12903.htm
- http://m.3g.ghtkgg.cn/nnews/3337595.htm
- http://m.3g.ghtkgg.cn/nnews/4407.htm
- http://m.3g.ghtkgg.cn/nnews/67544.htm
- http://m.3g.ghtkgg.cn/nnews/7632.htm
- http://m.3g.ghtkgg.cn/nnews/2823242.htm
- http://m.3g.ghtkgg.cn/nnews/373670.htm
- http://m.3g.ghtkgg.cn/nnews/6963.htm
- http://m.3g.ghtkgg.cn/nnews/3402830.htm
- http://m.3g.ghtkgg.cn/nnews/096032.htm
- http://m.3g.ghtkgg.cn/nnews/6336388.htm
- http://m.3g.ghtkgg.cn/nnews/4783.htm
- http://m.3g.ghtkgg.cn/nnews/57901.htm
- http://m.3g.ghtkgg.cn/nnews/86825.htm
- http://m.3g.ghtkgg.cn/nnews/20352.htm
- http://m.3g.ghtkgg.cn/nnews/055846.htm
- http://m.3g.ghtkgg.cn/nnews/6539.htm
- http://m.3g.ghtkgg.cn/nnews/33188.htm
- http://m.3g.ghtkgg.cn/nnews/4317373.htm
- http://m.3g.ghtkgg.cn/nnews/03075.htm
- http://m.3g.ghtkgg.cn/nnews/1744992.htm
- http://m.3g.ghtkgg.cn/nnews/5865.htm
- http://m.3g.ghtkgg.cn/nnews/9504257.htm
- http://m.3g.ghtkgg.cn/nnews/2178210.htm
- http://m.3g.ghtkgg.cn/nnews/0320.htm
- http://m.3g.ghtkgg.cn/nnews/89483.htm
- http://m.3g.ghtkgg.cn/nnews/47084.htm
- http://m.3g.ghtkgg.cn/nnews/7623848.htm
- http://m.3g.ghtkgg.cn/nnews/318104.htm
- http://m.3g.ghtkgg.cn/nnews/215229.htm
- http://m.3g.ghtkgg.cn/nnews/9720.htm
- http://m.3g.ghtkgg.cn/nnews/918767.htm
- http://m.3g.ghtkgg.cn/nnews/667473.htm
- http://m.3g.ghtkgg.cn/nnews/8428698.htm
- http://m.3g.ghtkgg.cn/nnews/5017.htm
- http://m.3g.ghtkgg.cn/nnews/65744.htm
- http://m.3g.ghtkgg.cn/nnews/959099.htm
- http://m.3g.ghtkgg.cn/nnews/76118.htm
- http://m.3g.ghtkgg.cn/nnews/0491.htm
- http://m.3g.ghtkgg.cn/nnews/522917.htm
- http://m.3g.ghtkgg.cn/nnews/026447.htm
- http://m.3g.ghtkgg.cn/nnews/605514.htm
- http://m.3g.ghtkgg.cn/nnews/867959.htm
- http://m.3g.ghtkgg.cn/nnews/21133.htm
- http://m.3g.ghtkgg.cn/nnews/81316.htm
- http://m.3g.ghtkgg.cn/nnews/2312672.htm
- http://m.3g.ghtkgg.cn/nnews/514847.htm
- http://m.3g.ghtkgg.cn/nnews/8013.htm
- http://m.3g.ghtkgg.cn/nnews/5280.htm
- http://m.3g.ghtkgg.cn/nnews/5466422.htm
- http://m.3g.ghtkgg.cn/nnews/1423.htm
- http://m.3g.ghtkgg.cn/nnews/76764.htm
- http://m.3g.ghtkgg.cn/nnews/439643.htm
- http://m.3g.ghtkgg.cn/nnews/352179.htm
- http://m.3g.ghtkgg.cn/nnews/9273182.htm
- http://m.3g.ghtkgg.cn/nnews/143640.htm
- http://m.3g.ghtkgg.cn/nnews/499415.htm
- http://m.3g.ghtkgg.cn/nnews/4985704.htm
- http://m.3g.ghtkgg.cn/nnews/25794.htm
- http://m.3g.ghtkgg.cn/nnews/997690.htm
- http://m.3g.ghtkgg.cn/nnews/5887.htm
- http://m.3g.ghtkgg.cn/nnews/4649064.htm
- http://m.3g.ghtkgg.cn/nnews/35633.htm
- http://m.3g.ghtkgg.cn/nnews/512671.htm
- http://m.3g.ghtkgg.cn/nnews/9818883.htm
- http://m.3g.ghtkgg.cn/nnews/63720.htm
- http://m.3g.ghtkgg.cn/nnews/4131549.htm
- http://m.3g.ghtkgg.cn/nnews/05143.htm
- http://m.3g.ghtkgg.cn/nnews/0309.htm
- http://m.3g.ghtkgg.cn/nnews/5455.htm
- http://m.3g.ghtkgg.cn/nnews/58676.htm
- http://m.3g.ghtkgg.cn/nnews/77859.htm
- http://m.3g.ghtkgg.cn/nnews/047912.htm
- http://m.3g.ghtkgg.cn/nnews/60490.htm
- http://m.3g.ghtkgg.cn/nnews/5223791.htm
- http://m.3g.ghtkgg.cn/nnews/558463.htm
- http://m.3g.ghtkgg.cn/nnews/1726044.htm
- http://m.3g.ghtkgg.cn/nnews/05747.htm
- http://m.3g.ghtkgg.cn/nnews/55422.htm
- http://m.3g.ghtkgg.cn/nnews/7119.htm
- http://m.3g.ghtkgg.cn/nnews/7846.htm
- http://m.3g.ghtkgg.cn/nnews/44879.htm
- http://m.3g.ghtkgg.cn/nnews/2309582.htm
- http://m.3g.ghtkgg.cn/nnews/129220.htm
- http://m.3g.ghtkgg.cn/nnews/4037008.htm
- http://m.3g.ghtkgg.cn/nnews/615534.htm
- http://m.3g.ghtkgg.cn/nnews/09932.htm
- http://m.3g.ghtkgg.cn/nnews/5929693.htm
- http://m.3g.ghtkgg.cn/nnews/098246.htm
- http://m.3g.ghtkgg.cn/nnews/64804.htm
- http://m.3g.ghtkgg.cn/nnews/021205.htm
- http://m.3g.ghtkgg.cn/nnews/9334602.htm
- http://m.3g.ghtkgg.cn/nnews/828171.htm
- http://m.3g.ghtkgg.cn/nnews/6747.htm
- http://m.3g.ghtkgg.cn/nnews/5972.htm
- http://m.3g.ghtkgg.cn/nnews/24357.htm
- http://m.3g.ghtkgg.cn/nnews/2600338.htm
- http://m.3g.ghtkgg.cn/nnews/88244.htm
- http://m.3g.ghtkgg.cn/nnews/321699.htm
- http://m.3g.ghtkgg.cn/nnews/7289060.htm
- http://m.3g.ghtkgg.cn/nnews/040870.htm
- http://m.3g.ghtkgg.cn/nnews/68519.htm
- http://m.3g.ghtkgg.cn/nnews/245974.htm
- http://m.3g.ghtkgg.cn/nnews/7873.htm
- http://m.3g.ghtkgg.cn/nnews/7064.htm
- http://m.3g.ghtkgg.cn/nnews/5727.htm
- http://m.3g.ghtkgg.cn/nnews/6605.htm
- http://m.3g.ghtkgg.cn/nnews/7183417.htm
- http://m.3g.ghtkgg.cn/nnews/5962405.htm
- http://m.3g.ghtkgg.cn/nnews/6336.htm
- http://m.3g.ghtkgg.cn/nnews/7002148.htm
- http://m.3g.ghtkgg.cn/nnews/274137.htm
- http://m.3g.ghtkgg.cn/nnews/6619738.htm
- http://m.3g.ghtkgg.cn/nnews/615718.htm
- http://m.3g.ghtkgg.cn/nnews/3043886.htm
- http://m.3g.ghtkgg.cn/nnews/4758.htm
- http://m.3g.ghtkgg.cn/nnews/3470.htm
- http://m.3g.ghtkgg.cn/nnews/94935.htm
- http://m.3g.ghtkgg.cn/nnews/91753.htm
- http://m.3g.ghtkgg.cn/nnews/87271.htm
- http://m.3g.ghtkgg.cn/nnews/2693448.htm
- http://m.3g.ghtkgg.cn/nnews/3774.htm
- http://m.3g.ghtkgg.cn/nnews/208443.htm
- http://m.3g.ghtkgg.cn/nnews/65826.htm
- http://m.3g.ghtkgg.cn/nnews/712115.htm
- http://m.3g.ghtkgg.cn/nnews/67867.htm
- http://m.3g.ghtkgg.cn/nnews/1551674.htm
- http://m.3g.ghtkgg.cn/nnews/72970.htm
- http://m.3g.ghtkgg.cn/nnews/2550.htm
- http://m.3g.ghtkgg.cn/nnews/7894.htm
- http://m.3g.ghtkgg.cn/nnews/740504.htm
- http://m.3g.ghtkgg.cn/nnews/44585.htm
- http://m.3g.ghtkgg.cn/nnews/2471546.htm
- http://m.3g.ghtkgg.cn/nnews/361775.htm
- http://m.3g.ghtkgg.cn/nnews/9799.htm
- http://m.3g.ghtkgg.cn/nnews/3256.htm
- http://m.3g.ghtkgg.cn/nnews/938917.htm
- http://m.3g.ghtkgg.cn/nnews/0734252.htm
- http://m.3g.ghtkgg.cn/nnews/13273.htm
- http://m.3g.ghtkgg.cn/nnews/61731.htm
- http://m.3g.ghtkgg.cn/nnews/71260.htm
- http://m.3g.ghtkgg.cn/nnews/787908.htm
- http://m.3g.ghtkgg.cn/nnews/5646306.htm
- http://m.3g.ghtkgg.cn/nnews/0500932.htm
- http://m.3g.ghtkgg.cn/nnews/068191.htm
- http://m.3g.ghtkgg.cn/nnews/6687.htm
- http://m.3g.ghtkgg.cn/nnews/432568.htm
- http://m.3g.ghtkgg.cn/nnews/21314.htm
- http://m.3g.ghtkgg.cn/nnews/482727.htm
- http://m.3g.ghtkgg.cn/nnews/7171.htm
- http://m.3g.ghtkgg.cn/nnews/9584610.htm
- http://m.3g.ghtkgg.cn/nnews/4791.htm

## 项目结构

```
news-aggregator/
├── bin/                                 # 可执行脚本与启动入口
│   ├── server.py                        # Web 服务主启动脚本，含参数解析与端口绑定
│   ├── init_config.py                   # 初始化配置文件，生成默认 config.yaml
│   └── health_check.py                  # 独立运行的链接健康检查定时任务脚本
├── config/                              # 配置文件目录
│   ├── config.yaml                      # 主配置文件，包含数据库路径、服务端口、检查周期等
│   └── logging.conf                     # 日志格式与输出级别配置
├── core/                                # 核心业务逻辑模块
│   ├── import_engine.py                 # 链接导入引擎，支持文件读取与标准输入解析
│   ├── metadata_extractor.py            # 元数据提取器，解析域名、路径、时间与类型标签
│   ├── filter_engine.py                 # 多维过滤引擎，实现时间、域名、关键词组合检索
│   └── health_checker.py                # 健康检查核心逻辑，管理 HEAD 请求与状态记录
├── web/                                 # Web 层模块
│   ├── app.py                           # Flask 应用工厂，注册路由与蓝图
│   ├── routes/                          # 路由蓝图目录
│   │   ├── index.py                     # 主页与管理面板路由
│   │   ├── api.py                       # RESTful API 端点实现
│   │   └── export.py                    # 数据导出接口（CSV、JSON、TXT）
│   └── templates/                       # Jinja2 模板文件
│       ├── index.html                   # 链接列表展示页
│       ├── detail.html                  # 单条链接详情与统计信息
│       └── admin.html                   # 标签管理与系统配置界面
├── data/                                # 数据存储目录
│   ├── newslinks.db                     # SQLite 主数据库文件（自动创建）
│   └── imports/                         # 导入历史记录存档目录
├── tests/                               # 单元测试与集成测试
│   ├── test_import.py                   # 导入引擎功能测试
│   ├── test_filter.py                   # 过滤引擎查询测试
│   └── test_health.py                   # 健康检查逻辑测试
├── docs/                                # 项目文档
│   ├── user_guide.md                    # 用户手册
│   ├── deployment.md                    # 部署指南
│   ├── api_reference.md                 # API 参考文档
│   └── development.md                   # 开发指引
├── requirements.txt                     # Python 依赖列表
├── setup.py                             # 项目打包与安装脚本
└── README.md                            # 项目说明文档（本文件）
```

## 贡献指南

提交 Issue 描述问题或新功能请求 在 GitHub Issue 页面提交详细的问题描述，包含复现步骤、运行环境版本以及相关日志输出。新功能请求需说明使用场景与预期行为。

Fork 仓库并创建特性分支 将主仓库 Fork 至个人账户，基于 main 分支创建新的特性分支，分支命名格式为 feature/功能简述或 fix/问题简述。

编写代码并添加单元测试 所有新增功能或修复必须包含对应的单元测试，测试用例放置在 tests/ 目录下，确保测试覆盖率达到 90% 以上。代码风格遵循 PEP 8 规范。

提交 Pull Request 并描述变更 推送分支后向主仓库提交 Pull Request，在描述中关联对应的 Issue 编号，列出主要变更点、测试结果以及是否影响现有 API 兼容性。

代码审查与合并 项目维护者将进行代码审查，提出修改意见。通过审查后由维护者合并至 main 分支，并自动触发持续集成流水线进行构建与发布。

## 常见问题

Q: 导入链接时支持哪些文件格式？

A: 当前版本支持纯文本文件（每行一条 URL）、CSV 格式（需包含 url 列）以及 JSON 数组格式（[{"url": "..."}]）。更多格式支持计划在后续版本中添加。导入时可通过 --format 参数手动指定格式，未指定时将根据文件扩展名自动识别。

Q: 链接健康检查的频率和超时时间如何配置？

A: 健康检查的周期和超时时间均在 config/config.yaml 文件中配置。check_interval 参数控制检查周期，默认值为 86400 秒（24 小时）。timeout 参数控制单次请求超时时间，默认值为 10 秒。修改配置后需要重启服务或重新运行健康检查脚本使配置生效。

Q: 如何迁移数据库到其他服务器？

A: 本项目使用 SQLite 作为内嵌数据库，迁移时只需将 data/newslinks.db 文件复制到目标服务器的相同相对路径下，并确保目标服务器安装有相同或更高版本的 SQLite 即可。若需迁移至其他数据库系统（如 PostgreSQL），需自行编写数据迁移脚本，项目本身不提供跨数据库迁移工具。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:01
