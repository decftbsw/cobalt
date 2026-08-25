# NewsLink 聚合服务

NewsLink 是一个面向移动端新闻资讯聚合的开源中间件项目，旨在为开发者、内容聚合平台及个人站长提供结构化的新闻外链管理与分发能力。该项目定位于技术资源汇总层，不对原始内容做改写或二次编辑，仅提供高效、可扩展的链接索引与元数据提取框架。目标用户包括独立开发者、内容推荐系统维护者、舆情监控工具开发者以及需要批量管理外部新闻链接的运维人员。NewsLink 通过统一的数据接入规范，解决分散新闻源难以维护、链接失效不可追踪、多批次数据导入缺乏标准流程等实际问题，帮助用户在数分钟内完成千级外链的批量入库与健康度检查。

## 功能概览

批量链接导入 支持平面文件、JSON 及 CSV 格式的批量链接提交，自动过滤重复条目并生成入库时间戳。

健康度巡检 每日定时对已收录链接进行 HTTP 状态码检测，标记异常链接并输出可视化报表。

元数据抽取 从目标页面自动提取标题、发布时间、正文摘要及关键词，支持自定义 XPath 选择器。

分类标签管理 允许用户为每条链接附加多级分类标签，支持标签合并、拆分及权重排序。

检索与过滤 提供基于日期、状态码、域名及自定义标签的多条件组合检索，响应时间低于 200 毫秒。

导出管道 支持将链接列表及元数据导出为 JSON、RSS 及 Markdown 表格格式，便于嵌入第三方系统。

访问统计 记录每条链接的调用次数、最后访问时间及来源 IP 地域分布，辅助内容热度分析。

## 应用场景

舆情监控系统数据接入 舆情分析团队可使用 NewsLink 将每日采集到的数千条新闻外链统一入库，再通过健康度巡检自动剔除失效链接，确保下游分析模型输入数据的完整性和时效性。

个人技术博客外链推荐 技术博主可在文章末尾通过 NewsLink 的检索接口动态拉取与当前主题相关的历史新闻链接，实现站内内容的自动关联推荐，提升读者停留时长。

企业内部资讯周报生成 企业市场部门可将每周关注的行业动态链接批量导入 NewsLink，利用分类标签管理功能按“竞品动向”“政策法规”“技术突破”等维度分组，最终通过导出管道生成结构化的周报 Markdown 文件。

批量链接迁移与备份 当站长更换域名或迁移内容管理系统时，NewsLink 支持将旧站所有外链一次性导出为标准格式，再导入新系统，避免手动复制粘贴导致的遗漏和格式错乱。

学术研究数据采集辅助 社会科学研究人员在收集网络新闻样本时，可将候选链接先行导入 NewsLink 进行元数据抽取，获得结构化的标题-时间-摘要数据集，大幅降低手工整理成本。

## 快速开始

以下命令演示了如何在 Linux 或 macOS 环境下从源码部署 NewsLink 实例。

```bash
# 克隆项目仓库
git clone https://github.com/news-link/core.git newslink
cd newslink

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化 SQLite 数据库及默认配置
python manage.py initdb
python manage.py migrate

# 启动开发服务器（默认监听 127.0.0.1:8080）
python manage.py runserver
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 - 3.12 | 核心运行环境，低于 3.9 不支持类型提示新语法 |
| SQLite | 3.35.0 及以上 | 默认元数据库引擎，支持 JSON 字段存储扩展属性 |
| Redis | 6.2 及以上 | 用于缓存健康度检测结果及访问计数（可选，默认使用内存缓存） |
| BeautifulSoup4 | 4.12.0 及以上 | 用于 HTML 解析及元数据抽取，依赖 lxml 或 html5lib 解析器 |
| requests | 2.31.0 及以上 | HTTP 客户端库，用于链接健康度检测及页面抓取 |
| pytest | 8.0.0 及以上 | 仅在开发环境运行单元测试时使用，生产环境可不安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何在 5 分钟内完成首次链接导入与健康检查 |
| 配置参考 | docs/configuration.md | 各环境变量、配置文件参数的含义及默认值 |
| API 手册 | docs/api_reference.md | 所有 RESTful 接口的请求/响应格式、错误码说明 |
| 部署指南 | docs/deployment.md | 使用 Docker Compose 或 uWSGI 生产级部署方案 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/7069546.htm
- http://m.wap.oexnr.cn/jnews/65084.htm
- http://m.wap.oexnr.cn/jnews/493817.htm
- http://m.wap.oexnr.cn/jnews/83821.htm
- http://m.wap.oexnr.cn/jnews/63536.htm
- http://m.wap.oexnr.cn/jnews/8736566.htm
- http://m.wap.oexnr.cn/jnews/71481.htm
- http://m.wap.oexnr.cn/jnews/581946.htm
- http://m.wap.oexnr.cn/jnews/91267.htm
- http://m.wap.oexnr.cn/jnews/39550.htm
- http://m.wap.oexnr.cn/jnews/228885.htm
- http://m.wap.oexnr.cn/jnews/1251740.htm
- http://m.wap.oexnr.cn/jnews/33302.htm
- http://m.wap.oexnr.cn/jnews/039157.htm
- http://m.wap.oexnr.cn/jnews/8475328.htm
- http://m.wap.oexnr.cn/jnews/1360120.htm
- http://m.wap.oexnr.cn/jnews/91800.htm
- http://m.wap.oexnr.cn/jnews/82465.htm
- http://m.wap.oexnr.cn/jnews/610342.htm
- http://m.wap.oexnr.cn/jnews/9945.htm
- http://m.wap.oexnr.cn/jnews/035888.htm
- http://m.wap.oexnr.cn/jnews/4573.htm
- http://m.wap.oexnr.cn/jnews/105926.htm
- http://m.wap.oexnr.cn/jnews/964309.htm
- http://m.wap.oexnr.cn/jnews/6212938.htm
- http://m.wap.oexnr.cn/jnews/632289.htm
- http://m.wap.oexnr.cn/jnews/0807525.htm
- http://m.wap.oexnr.cn/jnews/2175956.htm
- http://m.wap.oexnr.cn/jnews/8588178.htm
- http://m.wap.oexnr.cn/jnews/4862800.htm
- http://m.wap.oexnr.cn/jnews/106242.htm
- http://m.wap.oexnr.cn/jnews/5676686.htm
- http://m.wap.oexnr.cn/jnews/37298.htm
- http://m.wap.oexnr.cn/jnews/412432.htm
- http://m.wap.oexnr.cn/jnews/043737.htm
- http://m.wap.oexnr.cn/jnews/3235.htm
- http://m.wap.oexnr.cn/jnews/010898.htm
- http://m.wap.oexnr.cn/jnews/1697.htm
- http://m.wap.oexnr.cn/jnews/5277.htm
- http://m.wap.oexnr.cn/jnews/84533.htm
- http://m.wap.oexnr.cn/jnews/4416.htm
- http://m.wap.oexnr.cn/jnews/4725.htm
- http://m.wap.oexnr.cn/jnews/147111.htm
- http://m.wap.oexnr.cn/jnews/8601598.htm
- http://m.wap.oexnr.cn/jnews/0076549.htm
- http://m.wap.oexnr.cn/jnews/9331.htm
- http://m.wap.oexnr.cn/jnews/16927.htm
- http://m.wap.oexnr.cn/jnews/450633.htm
- http://m.wap.oexnr.cn/jnews/408565.htm
- http://m.wap.oexnr.cn/jnews/7741.htm
- http://m.wap.oexnr.cn/jnews/08236.htm
- http://m.wap.oexnr.cn/jnews/709727.htm
- http://m.wap.oexnr.cn/jnews/3289.htm
- http://m.wap.oexnr.cn/jnews/6055.htm
- http://m.wap.oexnr.cn/jnews/1431332.htm
- http://m.wap.oexnr.cn/jnews/4436456.htm
- http://m.wap.oexnr.cn/jnews/9693388.htm
- http://m.wap.oexnr.cn/jnews/60226.htm
- http://m.wap.oexnr.cn/jnews/33629.htm
- http://m.wap.oexnr.cn/jnews/3954069.htm
- http://m.wap.oexnr.cn/jnews/469778.htm
- http://m.wap.oexnr.cn/jnews/140706.htm
- http://m.wap.oexnr.cn/jnews/5653.htm
- http://m.wap.oexnr.cn/jnews/000104.htm
- http://m.wap.oexnr.cn/jnews/8735.htm
- http://m.wap.oexnr.cn/jnews/34395.htm
- http://m.wap.oexnr.cn/jnews/1671.htm
- http://m.wap.oexnr.cn/jnews/81022.htm
- http://m.wap.oexnr.cn/jnews/61836.htm
- http://m.wap.oexnr.cn/jnews/2427629.htm
- http://m.wap.oexnr.cn/jnews/636476.htm
- http://m.wap.oexnr.cn/jnews/686139.htm
- http://m.wap.oexnr.cn/jnews/3971319.htm
- http://m.wap.oexnr.cn/jnews/69473.htm
- http://m.wap.oexnr.cn/jnews/6534466.htm
- http://m.wap.oexnr.cn/jnews/682726.htm
- http://m.wap.oexnr.cn/jnews/8819513.htm
- http://m.wap.oexnr.cn/jnews/286054.htm
- http://m.wap.oexnr.cn/jnews/6181.htm
- http://m.wap.oexnr.cn/jnews/5147.htm
- http://m.wap.oexnr.cn/jnews/3166623.htm
- http://m.wap.oexnr.cn/jnews/6376563.htm
- http://m.wap.oexnr.cn/jnews/64758.htm
- http://m.wap.oexnr.cn/jnews/822273.htm
- http://m.wap.oexnr.cn/jnews/1817174.htm
- http://m.wap.oexnr.cn/jnews/517763.htm
- http://m.wap.oexnr.cn/jnews/21398.htm
- http://m.wap.oexnr.cn/jnews/72101.htm
- http://m.wap.oexnr.cn/jnews/7897118.htm
- http://m.wap.oexnr.cn/jnews/8706500.htm
- http://m.wap.oexnr.cn/jnews/4110480.htm
- http://m.wap.oexnr.cn/jnews/37554.htm
- http://m.wap.oexnr.cn/jnews/94945.htm
- http://m.wap.oexnr.cn/jnews/42768.htm
- http://m.wap.oexnr.cn/jnews/917291.htm
- http://m.wap.oexnr.cn/jnews/815629.htm
- http://m.wap.oexnr.cn/jnews/7577381.htm
- http://m.wap.oexnr.cn/jnews/49876.htm
- http://m.wap.oexnr.cn/jnews/668087.htm
- http://m.wap.oexnr.cn/jnews/180313.htm
- http://m.wap.oexnr.cn/jnews/3184.htm
- http://m.wap.oexnr.cn/jnews/9202458.htm
- http://m.wap.oexnr.cn/jnews/830071.htm
- http://m.wap.oexnr.cn/jnews/0404288.htm
- http://m.wap.oexnr.cn/jnews/7772062.htm
- http://m.wap.oexnr.cn/jnews/2534074.htm
- http://m.wap.oexnr.cn/jnews/2281.htm
- http://m.wap.oexnr.cn/jnews/1544.htm
- http://m.wap.oexnr.cn/jnews/6359630.htm
- http://m.wap.oexnr.cn/jnews/67941.htm
- http://m.wap.oexnr.cn/jnews/287586.htm
- http://m.wap.oexnr.cn/jnews/2685.htm
- http://m.wap.oexnr.cn/jnews/2616.htm
- http://m.wap.oexnr.cn/jnews/489438.htm
- http://m.wap.oexnr.cn/jnews/83073.htm
- http://m.wap.oexnr.cn/jnews/3797.htm
- http://m.wap.oexnr.cn/jnews/24627.htm
- http://m.wap.oexnr.cn/jnews/953333.htm
- http://m.wap.oexnr.cn/jnews/1579.htm
- http://m.wap.oexnr.cn/jnews/4865819.htm
- http://m.wap.oexnr.cn/jnews/25906.htm
- http://m.wap.oexnr.cn/jnews/97844.htm
- http://m.wap.oexnr.cn/jnews/9461151.htm
- http://m.wap.oexnr.cn/jnews/0338374.htm
- http://m.wap.oexnr.cn/jnews/9058096.htm
- http://m.wap.oexnr.cn/jnews/3225703.htm
- http://m.wap.oexnr.cn/jnews/9156.htm
- http://m.wap.oexnr.cn/jnews/8466603.htm
- http://m.wap.oexnr.cn/jnews/294021.htm
- http://m.wap.oexnr.cn/jnews/7945166.htm
- http://m.wap.oexnr.cn/jnews/5347606.htm
- http://m.wap.oexnr.cn/jnews/99846.htm
- http://m.wap.oexnr.cn/jnews/850287.htm
- http://m.wap.oexnr.cn/jnews/9715.htm
- http://m.wap.oexnr.cn/jnews/76002.htm
- http://m.wap.oexnr.cn/jnews/6717098.htm
- http://m.wap.oexnr.cn/jnews/2655018.htm
- http://m.wap.oexnr.cn/jnews/3655929.htm
- http://m.wap.oexnr.cn/jnews/335745.htm
- http://m.wap.oexnr.cn/jnews/524733.htm
- http://m.wap.oexnr.cn/jnews/2693.htm
- http://m.wap.oexnr.cn/jnews/2880.htm
- http://m.wap.oexnr.cn/jnews/6624027.htm
- http://m.wap.oexnr.cn/jnews/81066.htm
- http://m.wap.oexnr.cn/jnews/9034869.htm
- http://m.wap.oexnr.cn/jnews/220340.htm
- http://m.wap.oexnr.cn/jnews/0551.htm
- http://m.wap.oexnr.cn/jnews/5635128.htm
- http://m.wap.oexnr.cn/jnews/1654399.htm
- http://m.wap.oexnr.cn/jnews/8017670.htm
- http://m.wap.oexnr.cn/jnews/1878.htm
- http://m.wap.oexnr.cn/jnews/454904.htm
- http://m.wap.oexnr.cn/jnews/38890.htm
- http://m.wap.oexnr.cn/jnews/1638729.htm
- http://m.wap.oexnr.cn/jnews/9667.htm
- http://m.wap.oexnr.cn/jnews/0559.htm
- http://m.wap.oexnr.cn/jnews/13287.htm
- http://m.wap.oexnr.cn/jnews/40507.htm
- http://m.wap.oexnr.cn/jnews/5053.htm
- http://m.wap.oexnr.cn/jnews/2498.htm
- http://m.wap.oexnr.cn/jnews/93419.htm
- http://m.wap.oexnr.cn/jnews/0712569.htm
- http://m.wap.oexnr.cn/jnews/0856.htm
- http://m.wap.oexnr.cn/jnews/31973.htm
- http://m.wap.oexnr.cn/jnews/7395501.htm
- http://m.wap.oexnr.cn/jnews/9618.htm
- http://m.wap.oexnr.cn/jnews/53919.htm
- http://m.wap.oexnr.cn/jnews/6608472.htm
- http://m.wap.oexnr.cn/jnews/20470.htm
- http://m.wap.oexnr.cn/jnews/358293.htm
- http://m.wap.oexnr.cn/jnews/89062.htm
- http://m.wap.oexnr.cn/jnews/99489.htm
- http://m.wap.oexnr.cn/jnews/7948479.htm
- http://m.wap.oexnr.cn/jnews/8966.htm
- http://m.wap.oexnr.cn/jnews/9632084.htm
- http://m.wap.oexnr.cn/jnews/65398.htm
- http://m.wap.oexnr.cn/jnews/1520082.htm
- http://m.wap.oexnr.cn/jnews/48504.htm
- http://m.wap.oexnr.cn/jnews/6651.htm
- http://m.wap.oexnr.cn/jnews/1604336.htm
- http://m.wap.oexnr.cn/jnews/7141739.htm
- http://m.wap.oexnr.cn/jnews/838277.htm
- http://m.wap.oexnr.cn/jnews/8101062.htm
- http://m.wap.oexnr.cn/jnews/5132434.htm
- http://m.wap.oexnr.cn/jnews/0580.htm
- http://m.wap.oexnr.cn/jnews/98340.htm
- http://m.wap.oexnr.cn/jnews/9368135.htm
- http://m.wap.oexnr.cn/jnews/3887.htm
- http://m.wap.oexnr.cn/jnews/8923.htm
- http://m.wap.oexnr.cn/jnews/446135.htm
- http://m.wap.oexnr.cn/jnews/497412.htm
- http://m.wap.oexnr.cn/jnews/2772470.htm
- http://m.wap.oexnr.cn/jnews/0888887.htm
- http://m.wap.oexnr.cn/jnews/2196490.htm
- http://m.wap.oexnr.cn/jnews/754042.htm
- http://m.wap.oexnr.cn/jnews/0161023.htm
- http://m.wap.oexnr.cn/jnews/348678.htm
- http://m.wap.oexnr.cn/jnews/7582.htm
- http://m.wap.oexnr.cn/jnews/797207.htm
- http://m.wap.oexnr.cn/jnews/9635.htm
- http://m.wap.oexnr.cn/jnews/3440.htm
- http://m.wap.oexnr.cn/jnews/3285.htm
- http://m.wap.oexnr.cn/jnews/2262994.htm
- http://m.wap.oexnr.cn/jnews/081606.htm
- http://m.wap.oexnr.cn/jnews/1383.htm
- http://m.wap.oexnr.cn/jnews/10010.htm
- http://m.wap.oexnr.cn/jnews/1514025.htm
- http://m.wap.oexnr.cn/jnews/6258363.htm
- http://m.wap.oexnr.cn/jnews/7008.htm
- http://m.wap.oexnr.cn/jnews/54374.htm
- http://m.wap.oexnr.cn/jnews/78029.htm
- http://m.wap.oexnr.cn/jnews/9736294.htm
- http://m.wap.oexnr.cn/jnews/18959.htm
- http://m.wap.oexnr.cn/jnews/5212.htm
- http://m.wap.oexnr.cn/jnews/045327.htm
- http://m.wap.oexnr.cn/jnews/35323.htm
- http://m.wap.oexnr.cn/jnews/093605.htm
- http://m.wap.oexnr.cn/jnews/729388.htm
- http://m.wap.oexnr.cn/jnews/408652.htm
- http://m.wap.oexnr.cn/jnews/4908112.htm
- http://m.wap.oexnr.cn/jnews/01748.htm
- http://m.wap.oexnr.cn/jnews/9333.htm
- http://m.wap.oexnr.cn/jnews/2949790.htm
- http://m.wap.oexnr.cn/jnews/0618886.htm
- http://m.wap.oexnr.cn/jnews/038728.htm
- http://m.wap.oexnr.cn/jnews/383609.htm
- http://m.wap.oexnr.cn/jnews/3282364.htm
- http://m.wap.oexnr.cn/jnews/2277002.htm
- http://m.wap.oexnr.cn/jnews/68936.htm
- http://m.wap.oexnr.cn/jnews/7074668.htm
- http://m.wap.oexnr.cn/jnews/029697.htm
- http://m.wap.oexnr.cn/jnews/9104540.htm
- http://m.wap.oexnr.cn/jnews/0131.htm
- http://m.wap.oexnr.cn/jnews/3139017.htm
- http://m.wap.oexnr.cn/jnews/1442696.htm
- http://m.wap.oexnr.cn/jnews/98935.htm
- http://m.wap.oexnr.cn/jnews/57166.htm
- http://m.wap.oexnr.cn/jnews/011392.htm
- http://m.wap.oexnr.cn/jnews/8829453.htm
- http://m.wap.oexnr.cn/jnews/0075500.htm
- http://m.wap.oexnr.cn/jnews/41216.htm
- http://m.wap.oexnr.cn/jnews/969497.htm
- http://m.wap.oexnr.cn/jnews/74789.htm
- http://m.wap.oexnr.cn/jnews/5058.htm
- http://m.wap.oexnr.cn/jnews/283715.htm
- http://m.wap.oexnr.cn/jnews/80742.htm
- http://m.wap.oexnr.cn/jnews/7996094.htm
- http://m.wap.oexnr.cn/jnews/39916.htm
- http://m.wap.oexnr.cn/jnews/01848.htm
- http://m.wap.oexnr.cn/jnews/63896.htm
- http://m.wap.oexnr.cn/jnews/437008.htm
- http://m.wap.oexnr.cn/jnews/2739.htm
- http://m.wap.oexnr.cn/jnews/9319637.htm
- http://m.wap.oexnr.cn/jnews/6198614.htm
- http://m.wap.oexnr.cn/jnews/7861.htm
- http://m.wap.oexnr.cn/jnews/766564.htm
- http://m.wap.oexnr.cn/jnews/0730556.htm
- http://m.wap.oexnr.cn/jnews/8733.htm
- http://m.wap.oexnr.cn/jnews/267296.htm
- http://m.wap.oexnr.cn/jnews/452975.htm
- http://m.wap.oexnr.cn/jnews/1155657.htm
- http://m.wap.oexnr.cn/jnews/491069.htm
- http://m.wap.oexnr.cn/jnews/6751.htm
- http://m.wap.oexnr.cn/jnews/428890.htm
- http://m.wap.oexnr.cn/jnews/5466670.htm
- http://m.wap.oexnr.cn/jnews/9582.htm
- http://m.wap.oexnr.cn/jnews/816879.htm
- http://m.wap.oexnr.cn/jnews/6384.htm
- http://m.wap.oexnr.cn/jnews/46822.htm
- http://m.wap.oexnr.cn/jnews/3585.htm
- http://m.wap.oexnr.cn/jnews/893204.htm
- http://m.wap.oexnr.cn/jnews/8580247.htm
- http://m.wap.oexnr.cn/jnews/071075.htm
- http://m.wap.oexnr.cn/jnews/9876.htm
- http://m.wap.oexnr.cn/jnews/791854.htm
- http://m.wap.oexnr.cn/jnews/422058.htm
- http://m.wap.oexnr.cn/jnews/91133.htm
- http://m.wap.oexnr.cn/jnews/66115.htm
- http://m.wap.oexnr.cn/jnews/7318521.htm
- http://m.wap.oexnr.cn/jnews/3298786.htm
- http://m.wap.oexnr.cn/jnews/1628.htm
- http://m.wap.oexnr.cn/jnews/50883.htm
- http://m.wap.oexnr.cn/jnews/723969.htm
- http://m.wap.oexnr.cn/jnews/8575964.htm
- http://m.wap.oexnr.cn/jnews/3440917.htm
- http://m.wap.oexnr.cn/jnews/96522.htm
- http://m.wap.oexnr.cn/jnews/6308424.htm
- http://m.wap.oexnr.cn/jnews/9340.htm
- http://m.wap.oexnr.cn/jnews/1696220.htm
- http://m.wap.oexnr.cn/jnews/1753.htm
- http://m.wap.oexnr.cn/jnews/8485868.htm
- http://m.wap.oexnr.cn/jnews/436199.htm
- http://m.wap.oexnr.cn/jnews/36314.htm
- http://m.wap.oexnr.cn/jnews/128022.htm
- http://m.wap.oexnr.cn/jnews/77870.htm
- http://m.wap.oexnr.cn/jnews/7612.htm
- http://m.wap.oexnr.cn/jnews/020111.htm
- http://m.wap.oexnr.cn/jnews/484655.htm
- http://m.wap.oexnr.cn/jnews/7978.htm
- http://m.wap.oexnr.cn/jnews/4464236.htm

## 项目结构

```
newsLink/
├── core/                           # 核心业务逻辑模块
│   ├── __init__.py                 # 模块初始化与版本声明
│   ├── collector.py                # 批量链接导入与去重引擎
│   ├── checker.py                  # HTTP 健康度巡检调度器
│   ├── parser.py                   # 基于 BeautifulSoup 的元数据抽取器
│   └── exporter.py                 # 多格式导出管道（JSON/RSS/Markdown）
├── api/                            # RESTful 接口层
│   ├── routes/                     # 路由分组目录
│   │   ├── links.py                # 链接增删改查端点
│   │   ├── tags.py                 # 分类标签管理端点
│   │   └── stats.py                # 访问统计与报表端点
│   └── middleware/                 # 请求拦截与日志中间件
│       ├── auth.py                 # API Key 鉴权逻辑
│       └── ratelimit.py            # 基于 Redis 的流量限制器
├── models/                         # 数据模型与 ORM 映射
│   ├── link.py                     # 链接条目模型（含状态、时间戳）
│   ├── tag.py                      # 标签模型及多对多关联表
│   └── visit.py                    # 访问日志模型
├── tests/                          # 单元测试与集成测试目录
│   ├── test_collector.py           # 导入引擎测试用例
│   ├── test_checker.py             # 健康度检测模拟测试
│   └── fixtures/                   # 测试用静态数据（JSON/CSV 样本）
├── scripts/                        # 运维与辅助脚本
│   ├── initdb.py                   # 数据库初始化及种子数据填充
│   ├── migrate.py                  # 表结构迁移工具
│   └── daily_check.py              # 定时巡检任务入口（cron 调用）
├── config/                         # 配置管理
│   ├── settings.py                 # 基础配置类（环境变量读取）
│   ├── development.py              # 开发环境特定配置
│   └── production.py               # 生产环境配置（覆盖基础项）
├── docs/                           # 完整文档源码（Markdown）
│   ├── quickstart.md               # 快速入门指南
│   ├── configuration.md            # 配置参数详细说明
│   ├── api_reference.md            # API 接口完整手册
│   └── deployment.md               # 生产环境部署步骤
├── logs/                           # 运行时日志存储目录（自动创建）
├── requirements.txt                # Python 依赖清单（固定版本）
├── Dockerfile                      # 基于 Python 3.11-slim 的镜像构建文件
├── docker-compose.yml              # 含 Redis 与 SQLite 扩展的编排配置
└── README.md                       # 本文档
```

## 贡献指南

提交 Issue 与功能请求 访问 GitHub Issues 页面，使用提供的模板描述缺陷或新功能建议，需附带最小复现步骤或预期行为说明。

代码风格与测试 所有提交的 Python 代码必须通过 flake8 和 black 格式检查，并为新增功能编写对应的 pytest 单元测试，覆盖率不低于 85%。

分支管理策略 主分支为 main，开发分支为 dev。所有特性开发应基于 dev 创建 feature/xxx 分支，完成后通过 Pull Request 合并，且需至少一名维护者审核。

文档更新要求 任何涉及接口变更、配置项新增或部署步骤调整的提交，必须同步更新 docs 目录下对应的 Markdown 文档，并确保示例代码可执行。

本地验证流程 提交前需在本地执行 python manage.py test 确保全部用例通过，并运行 python manage.py runserver 进行手动冒烟测试，验证核心流程无回归缺陷。

## 常见问题

Q: 导入大量链接时出现超时或内存不足如何处理？
A: 导入引擎默认每批次处理 1000 条，可通过环境变量 BATCH_SIZE 调整该值。若内存占用过高，建议降低并发线程数（通过 MAX_WORKERS 设置，默认 4）。对于超过 10 万条的数据集，推荐使用 --stream 参数启用流式读取模式，避免一次性加载全部内容到内存。

Q: 健康度检测的 HTTP 超时时间是多少，能否自定义？
A: 默认连接超时为 5 秒，读取超时为 10 秒。您可以在 config/production.py 中覆盖 CHECKER_TIMEOUT 元组（如 (3.0, 8.0)），或在环境变量中设置 CHECKER_CONNECT_TIMEOUT 和 CHECKER_READ_TIMEOUT 分别指定。对于移动端页面较多的站点，建议适当延长读取超时至 15 秒以上。

Q: 如何迁移现有数据到生产环境的 PostgreSQL？
A: NewsLink 底层使用 SQLAlchemy ORM，支持 PostgreSQL、MySQL 等多种数据库。迁移步骤为：1) 在 config/production.py 中修改 SQLALCHEMY_DATABASE_URI 为 postgresql://user:pass@host/dbname；2) 运行 python manage.py migrate 自动生成表结构；3) 使用 python manage.py dumpdata 导出 SQLite 数据为 JSON，再使用 python manage.py loaddata 导入到新库。注意外键约束顺序，建议先导入标签表再导入链接表。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
