# WebLink Nexus 聚合检索系统

WebLink Nexus 是一个面向技术文档检索与新闻资讯聚合的开源外链索引平台，专为需要批量追踪分散信息源、建立自定义知识库的开发者与研究人员设计。项目通过对结构化 URL 资源进行规范化采集、分类标注与全文检索，解决信息碎片化场景下的数据溯源与内容定位问题。当前批次涵盖第 129/300 批共计 300 个新闻资讯类外链资源，所有条目均经过格式校验与元数据抽取，可直接用于自动化采集管道或人工查阅索引。

## 功能概览

批量外链导入与格式标准化 支持任意数量 URL 的批量录入，自动识别协议头、域名与路径层级，剔除重复条目并生成统一资源清单。

多维度元数据抽取 从 URL 路径中解析发布时间、内容编号、分类后缀等字段，构建可排序、可过滤的元数据索引表。

全文检索与正则匹配 内置基于词频的轻量检索引擎，支持对 URL 标题、路径关键词及自定义标签进行布尔查询与正则表达式过滤。

资源状态健康检查 周期性对已收录 URL 发起 HEAD 请求，检测响应状态码与重定向链，标记失效或迁移链接。

分类标签与注解系统 允许用户为每条资源附加自定义分类标签与备注说明，支持标签聚合统计与分组导出。

数据导入导出接口 提供 JSON、CSV、Markdown 三种格式的完整数据导出功能，便于对接外部数据分析工具或静态站点生成器。

访问统计与热度排序 记录每条外链的查询次数与最后访问时间，支持按热度、更新时间或添加时间排序输出。

## 应用场景

技术文档归档与检索 开发团队可将分散在多个新闻站点、技术博客的参考文档链接统一收录至 WebLink Nexus，通过标签分类和全文检索快速定位特定技术主题的历史文章。

舆情监控与资讯追踪 媒体研究人员或市场分析人员可利用本系统定期导入行业新闻 URL 列表，借助状态检查功能监控文章是否仍可访问，并通过热度排序识别近期高频查阅的内容。

自动化数据采集管道前置 数据工程师可将 WebLink Nexus 作为采集任务的数据源管理组件，批量导出 URL 列表供爬虫调度器使用，同时利用元数据字段控制采集优先级与频率。

个人知识库外链索引 知识管理爱好者可将日常阅读积累的零散外链集中存储，通过注解系统记录阅读笔记，构建可长期维护的个人外链知识图谱。

## 快速开始

以下命令演示如何在本地环境中完成 WebLink Nexus 的克隆、依赖安装与服务启动。

```bash
# 克隆项目仓库至本地
git clone https://github.com/weblink-nexus/weblink-nexus.git

# 进入项目根目录
cd weblink-nexus

# 安装 Python 依赖包（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 请使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化 SQLite 数据库表结构
python scripts/init_db.py

# 启动开发服务器（默认监听 127.0.0.1:5000）
python app.py
```

服务启动后，访问 http://127.0.0.1:5000 即可进入 Web 管理界面，通过「批量导入」功能粘贴 URL 列表开始使用。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，类型注解依赖 3.9+ 语法 |
| SQLite | 3.35 及以上 | 内置数据库，支持 JSON 字段存储元数据 |
| Flask | 2.2.x | Web 框架，用于提供管理界面与 REST API |
| requests | 2.28.x | 发送 HTTP 请求，用于健康检查与状态探测 |
| pytest | 7.2.x | 单元测试框架，仅开发环境需要 |
| gunicorn | 20.1.x | 生产环境 WSGI 服务器，Linux 部署推荐 |
| python-dotenv | 1.0.x | 环境变量加载，用于配置敏感参数 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user_guide.md | 如何使用批量导入、标签管理、检索查询等核心功能 |
| 开发者指南 | docs/developer_guide.md | 如何扩展元数据解析器、自定义分类规则与插件开发 |
| API 参考 | docs/api_reference.md | REST 接口的请求格式、响应结构及鉴权方式 |
| 部署运维 | docs/deployment.md | 生产环境下的进程管理、日志配置与性能调优参数 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/2568831.htm
- http://m.3g.ghtkgg.cn/nnews/3413530.htm
- http://m.3g.ghtkgg.cn/nnews/670149.htm
- http://m.3g.ghtkgg.cn/nnews/14615.htm
- http://m.3g.ghtkgg.cn/nnews/3338.htm
- http://m.3g.ghtkgg.cn/nnews/5697080.htm
- http://m.3g.ghtkgg.cn/nnews/04174.htm
- http://m.3g.ghtkgg.cn/nnews/9834561.htm
- http://m.3g.ghtkgg.cn/nnews/18484.htm
- http://m.3g.ghtkgg.cn/nnews/520991.htm
- http://m.3g.ghtkgg.cn/nnews/5844.htm
- http://m.3g.ghtkgg.cn/nnews/7063212.htm
- http://m.3g.ghtkgg.cn/nnews/66621.htm
- http://m.3g.ghtkgg.cn/nnews/4495891.htm
- http://m.3g.ghtkgg.cn/nnews/9208.htm
- http://m.3g.ghtkgg.cn/nnews/7143494.htm
- http://m.3g.ghtkgg.cn/nnews/749908.htm
- http://m.3g.ghtkgg.cn/nnews/968841.htm
- http://m.3g.ghtkgg.cn/nnews/39527.htm
- http://m.3g.ghtkgg.cn/nnews/726870.htm
- http://m.3g.ghtkgg.cn/nnews/09339.htm
- http://m.3g.ghtkgg.cn/nnews/177015.htm
- http://m.3g.ghtkgg.cn/nnews/164128.htm
- http://m.3g.ghtkgg.cn/nnews/8320687.htm
- http://m.3g.ghtkgg.cn/nnews/6108.htm
- http://m.3g.ghtkgg.cn/nnews/5830968.htm
- http://m.3g.ghtkgg.cn/nnews/3339.htm
- http://m.3g.ghtkgg.cn/nnews/880798.htm
- http://m.3g.ghtkgg.cn/nnews/41471.htm
- http://m.3g.ghtkgg.cn/nnews/532136.htm
- http://m.3g.ghtkgg.cn/nnews/002585.htm
- http://m.3g.ghtkgg.cn/nnews/70478.htm
- http://m.3g.ghtkgg.cn/nnews/9461958.htm
- http://m.3g.ghtkgg.cn/nnews/759172.htm
- http://m.3g.ghtkgg.cn/nnews/502744.htm
- http://m.3g.ghtkgg.cn/nnews/1276130.htm
- http://m.3g.ghtkgg.cn/nnews/702898.htm
- http://m.3g.ghtkgg.cn/nnews/014963.htm
- http://m.3g.ghtkgg.cn/nnews/1466.htm
- http://m.3g.ghtkgg.cn/nnews/3129569.htm
- http://m.3g.ghtkgg.cn/nnews/5992604.htm
- http://m.3g.ghtkgg.cn/nnews/0261178.htm
- http://m.3g.ghtkgg.cn/nnews/786679.htm
- http://m.3g.ghtkgg.cn/nnews/668995.htm
- http://m.3g.ghtkgg.cn/nnews/0583.htm
- http://m.3g.ghtkgg.cn/nnews/081244.htm
- http://m.3g.ghtkgg.cn/nnews/45774.htm
- http://m.3g.ghtkgg.cn/nnews/7901916.htm
- http://m.3g.ghtkgg.cn/nnews/395118.htm
- http://m.3g.ghtkgg.cn/nnews/955122.htm
- http://m.3g.ghtkgg.cn/nnews/49242.htm
- http://m.3g.ghtkgg.cn/nnews/45463.htm
- http://m.3g.ghtkgg.cn/nnews/2184345.htm
- http://m.3g.ghtkgg.cn/nnews/754127.htm
- http://m.3g.ghtkgg.cn/nnews/8281.htm
- http://m.3g.ghtkgg.cn/nnews/714045.htm
- http://m.3g.ghtkgg.cn/nnews/46197.htm
- http://m.3g.ghtkgg.cn/nnews/42391.htm
- http://m.3g.ghtkgg.cn/nnews/75345.htm
- http://m.3g.ghtkgg.cn/nnews/218727.htm
- http://m.3g.ghtkgg.cn/nnews/6704.htm
- http://m.3g.ghtkgg.cn/nnews/6729994.htm
- http://m.3g.ghtkgg.cn/nnews/9202003.htm
- http://m.3g.ghtkgg.cn/nnews/45447.htm
- http://m.3g.ghtkgg.cn/nnews/9005.htm
- http://m.3g.ghtkgg.cn/nnews/565750.htm
- http://m.3g.ghtkgg.cn/nnews/97063.htm
- http://m.3g.ghtkgg.cn/nnews/1278.htm
- http://m.3g.ghtkgg.cn/nnews/834795.htm
- http://m.3g.ghtkgg.cn/nnews/520313.htm
- http://m.3g.ghtkgg.cn/nnews/391818.htm
- http://m.3g.ghtkgg.cn/nnews/1132.htm
- http://m.3g.ghtkgg.cn/nnews/26003.htm
- http://m.3g.ghtkgg.cn/nnews/040774.htm
- http://m.3g.ghtkgg.cn/nnews/1183687.htm
- http://m.3g.ghtkgg.cn/nnews/64531.htm
- http://m.3g.ghtkgg.cn/nnews/0790975.htm
- http://m.3g.ghtkgg.cn/nnews/862605.htm
- http://m.3g.ghtkgg.cn/nnews/6299.htm
- http://m.3g.ghtkgg.cn/nnews/972523.htm
- http://m.3g.ghtkgg.cn/nnews/8452.htm
- http://m.3g.ghtkgg.cn/nnews/207820.htm
- http://m.3g.ghtkgg.cn/nnews/2586375.htm
- http://m.3g.ghtkgg.cn/nnews/2705.htm
- http://m.3g.ghtkgg.cn/nnews/9403407.htm
- http://m.3g.ghtkgg.cn/nnews/9567.htm
- http://m.3g.ghtkgg.cn/nnews/29262.htm
- http://m.3g.ghtkgg.cn/nnews/844538.htm
- http://m.3g.ghtkgg.cn/nnews/4741.htm
- http://m.3g.ghtkgg.cn/nnews/7839.htm
- http://m.3g.ghtkgg.cn/nnews/1351214.htm
- http://m.3g.ghtkgg.cn/nnews/7510224.htm
- http://m.3g.ghtkgg.cn/nnews/9232454.htm
- http://m.3g.ghtkgg.cn/nnews/4444.htm
- http://m.3g.ghtkgg.cn/nnews/243140.htm
- http://m.3g.ghtkgg.cn/nnews/2237067.htm
- http://m.3g.ghtkgg.cn/nnews/13774.htm
- http://m.3g.ghtkgg.cn/nnews/371944.htm
- http://m.3g.ghtkgg.cn/nnews/290478.htm
- http://m.3g.ghtkgg.cn/nnews/22890.htm
- http://m.3g.ghtkgg.cn/nnews/8722.htm
- http://m.3g.ghtkgg.cn/nnews/53142.htm
- http://m.3g.ghtkgg.cn/nnews/2594.htm
- http://m.3g.ghtkgg.cn/nnews/812097.htm
- http://m.3g.ghtkgg.cn/nnews/2443.htm
- http://m.3g.ghtkgg.cn/nnews/76789.htm
- http://m.3g.ghtkgg.cn/nnews/124396.htm
- http://m.3g.ghtkgg.cn/nnews/71966.htm
- http://m.3g.ghtkgg.cn/nnews/5776.htm
- http://m.3g.ghtkgg.cn/nnews/20481.htm
- http://m.3g.ghtkgg.cn/nnews/617767.htm
- http://m.3g.ghtkgg.cn/nnews/8197433.htm
- http://m.3g.ghtkgg.cn/nnews/791233.htm
- http://m.3g.ghtkgg.cn/nnews/886707.htm
- http://m.3g.ghtkgg.cn/nnews/2688.htm
- http://m.3g.ghtkgg.cn/nnews/7052.htm
- http://m.3g.ghtkgg.cn/nnews/3002928.htm
- http://m.3g.ghtkgg.cn/nnews/8905.htm
- http://m.3g.ghtkgg.cn/nnews/614858.htm
- http://m.3g.ghtkgg.cn/nnews/0449.htm
- http://m.3g.ghtkgg.cn/nnews/052443.htm
- http://m.3g.ghtkgg.cn/nnews/812243.htm
- http://m.3g.ghtkgg.cn/nnews/4053273.htm
- http://m.3g.ghtkgg.cn/nnews/1548.htm
- http://m.3g.ghtkgg.cn/nnews/1500.htm
- http://m.3g.ghtkgg.cn/nnews/66445.htm
- http://m.3g.ghtkgg.cn/nnews/63850.htm
- http://m.3g.ghtkgg.cn/nnews/6737.htm
- http://m.3g.ghtkgg.cn/nnews/960595.htm
- http://m.3g.ghtkgg.cn/nnews/835015.htm
- http://m.3g.ghtkgg.cn/nnews/6901.htm
- http://m.3g.ghtkgg.cn/nnews/17204.htm
- http://m.3g.ghtkgg.cn/nnews/74446.htm
- http://m.3g.ghtkgg.cn/nnews/15575.htm
- http://m.3g.ghtkgg.cn/nnews/4150.htm
- http://m.3g.ghtkgg.cn/nnews/043104.htm
- http://m.3g.ghtkgg.cn/nnews/3570.htm
- http://m.3g.ghtkgg.cn/nnews/7303442.htm
- http://m.3g.ghtkgg.cn/nnews/733561.htm
- http://m.3g.ghtkgg.cn/nnews/625320.htm
- http://m.3g.ghtkgg.cn/nnews/478298.htm
- http://m.3g.ghtkgg.cn/nnews/775283.htm
- http://m.3g.ghtkgg.cn/nnews/182713.htm
- http://m.3g.ghtkgg.cn/nnews/23020.htm
- http://m.3g.ghtkgg.cn/nnews/6534.htm
- http://m.3g.ghtkgg.cn/nnews/35218.htm
- http://m.3g.ghtkgg.cn/nnews/889430.htm
- http://m.3g.ghtkgg.cn/nnews/1707516.htm
- http://m.3g.ghtkgg.cn/nnews/342615.htm
- http://m.3g.ghtkgg.cn/nnews/433360.htm
- http://m.3g.ghtkgg.cn/nnews/2995.htm
- http://m.3g.ghtkgg.cn/nnews/91452.htm
- http://m.3g.ghtkgg.cn/nnews/24871.htm
- http://m.3g.ghtkgg.cn/nnews/164245.htm
- http://m.3g.ghtkgg.cn/nnews/406948.htm
- http://m.3g.ghtkgg.cn/nnews/4289.htm
- http://m.3g.ghtkgg.cn/nnews/1410.htm
- http://m.3g.ghtkgg.cn/nnews/2501247.htm
- http://m.3g.ghtkgg.cn/nnews/408220.htm
- http://m.3g.ghtkgg.cn/nnews/1610.htm
- http://m.3g.ghtkgg.cn/nnews/0255647.htm
- http://m.3g.ghtkgg.cn/nnews/4586.htm
- http://m.3g.ghtkgg.cn/nnews/0595559.htm
- http://m.3g.ghtkgg.cn/nnews/974974.htm
- http://m.3g.ghtkgg.cn/nnews/261897.htm
- http://m.3g.ghtkgg.cn/nnews/036481.htm
- http://m.3g.ghtkgg.cn/nnews/46804.htm
- http://m.3g.ghtkgg.cn/nnews/946743.htm
- http://m.3g.ghtkgg.cn/nnews/703519.htm
- http://m.3g.ghtkgg.cn/nnews/6153.htm
- http://m.3g.ghtkgg.cn/nnews/9631650.htm
- http://m.3g.ghtkgg.cn/nnews/0349695.htm
- http://m.3g.ghtkgg.cn/nnews/3120601.htm
- http://m.3g.ghtkgg.cn/nnews/47216.htm
- http://m.3g.ghtkgg.cn/nnews/0081.htm
- http://m.3g.ghtkgg.cn/nnews/78117.htm
- http://m.3g.ghtkgg.cn/nnews/048774.htm
- http://m.3g.ghtkgg.cn/nnews/0955323.htm
- http://m.3g.ghtkgg.cn/nnews/04392.htm
- http://m.3g.ghtkgg.cn/nnews/485908.htm
- http://m.3g.ghtkgg.cn/nnews/0302707.htm
- http://m.3g.ghtkgg.cn/nnews/39030.htm
- http://m.3g.ghtkgg.cn/nnews/5866539.htm
- http://m.3g.ghtkgg.cn/nnews/592323.htm
- http://m.3g.ghtkgg.cn/nnews/028436.htm
- http://m.3g.ghtkgg.cn/nnews/118591.htm
- http://m.3g.ghtkgg.cn/nnews/0596.htm
- http://m.3g.ghtkgg.cn/nnews/7907.htm
- http://m.3g.ghtkgg.cn/nnews/617967.htm
- http://m.3g.ghtkgg.cn/nnews/7819.htm
- http://m.3g.ghtkgg.cn/nnews/727057.htm
- http://m.3g.ghtkgg.cn/nnews/8427.htm
- http://m.3g.ghtkgg.cn/nnews/494298.htm
- http://m.3g.ghtkgg.cn/nnews/7002905.htm
- http://m.3g.ghtkgg.cn/nnews/3753.htm
- http://m.3g.ghtkgg.cn/nnews/301683.htm
- http://m.3g.ghtkgg.cn/nnews/36912.htm
- http://m.3g.ghtkgg.cn/nnews/8415.htm
- http://m.3g.ghtkgg.cn/nnews/09022.htm
- http://m.3g.ghtkgg.cn/nnews/8643.htm
- http://m.3g.ghtkgg.cn/nnews/450556.htm
- http://m.3g.ghtkgg.cn/nnews/3996.htm
- http://m.3g.ghtkgg.cn/nnews/155537.htm
- http://m.3g.ghtkgg.cn/nnews/3270.htm
- http://m.3g.ghtkgg.cn/nnews/165068.htm
- http://m.3g.ghtkgg.cn/nnews/0676211.htm
- http://m.3g.ghtkgg.cn/nnews/89241.htm
- http://m.3g.ghtkgg.cn/nnews/8391.htm
- http://m.3g.ghtkgg.cn/nnews/4309934.htm
- http://m.3g.ghtkgg.cn/nnews/11869.htm
- http://m.3g.ghtkgg.cn/nnews/0857.htm
- http://m.3g.ghtkgg.cn/nnews/54019.htm
- http://m.3g.ghtkgg.cn/nnews/3413556.htm
- http://m.3g.ghtkgg.cn/nnews/4484783.htm
- http://m.3g.ghtkgg.cn/nnews/365192.htm
- http://m.3g.ghtkgg.cn/nnews/179566.htm
- http://m.3g.ghtkgg.cn/nnews/7947835.htm
- http://m.3g.ghtkgg.cn/nnews/9018608.htm
- http://m.3g.ghtkgg.cn/nnews/5721650.htm
- http://m.3g.ghtkgg.cn/nnews/5050.htm
- http://m.3g.ghtkgg.cn/nnews/673555.htm
- http://m.3g.ghtkgg.cn/nnews/79879.htm
- http://m.3g.ghtkgg.cn/nnews/6486264.htm
- http://m.3g.ghtkgg.cn/nnews/2663.htm
- http://m.3g.ghtkgg.cn/nnews/1535659.htm
- http://m.3g.ghtkgg.cn/nnews/014709.htm
- http://m.3g.ghtkgg.cn/nnews/1514440.htm
- http://m.3g.ghtkgg.cn/nnews/41419.htm
- http://m.3g.ghtkgg.cn/nnews/27359.htm
- http://m.3g.ghtkgg.cn/nnews/33738.htm
- http://m.3g.ghtkgg.cn/nnews/85142.htm
- http://m.3g.ghtkgg.cn/nnews/1952.htm
- http://m.3g.ghtkgg.cn/nnews/62991.htm
- http://m.3g.ghtkgg.cn/nnews/762017.htm
- http://m.3g.ghtkgg.cn/nnews/9470611.htm
- http://m.3g.ghtkgg.cn/nnews/8503200.htm
- http://m.3g.ghtkgg.cn/nnews/2073.htm
- http://m.3g.ghtkgg.cn/nnews/9122.htm
- http://m.3g.ghtkgg.cn/nnews/422538.htm
- http://m.3g.ghtkgg.cn/nnews/0078.htm
- http://m.3g.ghtkgg.cn/nnews/90793.htm
- http://m.3g.ghtkgg.cn/nnews/46723.htm
- http://m.3g.ghtkgg.cn/nnews/0234.htm
- http://m.3g.ghtkgg.cn/nnews/2174.htm
- http://m.3g.ghtkgg.cn/nnews/405371.htm
- http://m.3g.ghtkgg.cn/nnews/230488.htm
- http://m.3g.ghtkgg.cn/nnews/93985.htm
- http://m.3g.ghtkgg.cn/nnews/97799.htm
- http://m.3g.ghtkgg.cn/nnews/9175285.htm
- http://m.3g.ghtkgg.cn/nnews/194295.htm
- http://m.3g.ghtkgg.cn/nnews/7222720.htm
- http://m.3g.ghtkgg.cn/nnews/071953.htm
- http://m.3g.ghtkgg.cn/nnews/4875.htm
- http://m.3g.ghtkgg.cn/nnews/0704.htm
- http://m.3g.ghtkgg.cn/nnews/3041611.htm
- http://m.3g.ghtkgg.cn/nnews/4196466.htm
- http://m.3g.ghtkgg.cn/nnews/109757.htm
- http://m.3g.ghtkgg.cn/nnews/8163891.htm
- http://m.3g.ghtkgg.cn/nnews/3444782.htm
- http://m.3g.ghtkgg.cn/nnews/10969.htm
- http://m.3g.ghtkgg.cn/nnews/6555.htm
- http://m.3g.ghtkgg.cn/nnews/5247.htm
- http://m.3g.ghtkgg.cn/nnews/673195.htm
- http://m.3g.ghtkgg.cn/nnews/9603422.htm
- http://m.3g.ghtkgg.cn/nnews/46966.htm
- http://m.3g.ghtkgg.cn/nnews/8463118.htm
- http://m.3g.ghtkgg.cn/nnews/0875.htm
- http://m.3g.ghtkgg.cn/nnews/9114952.htm
- http://m.3g.ghtkgg.cn/nnews/885251.htm
- http://m.3g.ghtkgg.cn/nnews/0374.htm
- http://m.3g.ghtkgg.cn/nnews/48612.htm
- http://m.3g.ghtkgg.cn/nnews/864028.htm
- http://m.3g.ghtkgg.cn/nnews/9573277.htm
- http://m.3g.ghtkgg.cn/nnews/887567.htm
- http://m.3g.ghtkgg.cn/nnews/241182.htm
- http://m.3g.ghtkgg.cn/nnews/4886.htm
- http://m.3g.ghtkgg.cn/nnews/363034.htm
- http://m.3g.ghtkgg.cn/nnews/7323558.htm
- http://m.3g.ghtkgg.cn/nnews/08404.htm
- http://m.3g.ghtkgg.cn/nnews/75103.htm
- http://m.3g.ghtkgg.cn/nnews/459864.htm
- http://m.3g.ghtkgg.cn/nnews/432435.htm
- http://m.3g.ghtkgg.cn/nnews/804229.htm
- http://m.3g.ghtkgg.cn/nnews/800681.htm
- http://m.3g.ghtkgg.cn/nnews/059931.htm
- http://m.3g.ghtkgg.cn/nnews/897374.htm
- http://m.3g.ghtkgg.cn/nnews/5000.htm
- http://m.3g.ghtkgg.cn/nnews/5433972.htm
- http://m.3g.ghtkgg.cn/nnews/0138194.htm
- http://m.3g.ghtkgg.cn/nnews/152431.htm
- http://m.3g.ghtkgg.cn/nnews/24392.htm
- http://m.3g.ghtkgg.cn/nnews/075388.htm
- http://m.3g.ghtkgg.cn/nnews/514241.htm
- http://m.3g.ghtkgg.cn/nnews/93685.htm
- http://m.3g.ghtkgg.cn/nnews/25126.htm
- http://m.3g.ghtkgg.cn/nnews/9171955.htm
- http://m.3g.ghtkgg.cn/nnews/70734.htm
- http://m.3g.ghtkgg.cn/nnews/734301.htm
- http://m.3g.ghtkgg.cn/nnews/95523.htm
- http://m.3g.ghtkgg.cn/nnews/500583.htm

## 项目结构

```
weblink-nexus/
├── app/                                # 主应用包
│   ├── __init__.py                     # 工厂函数，创建 Flask 实例并注册蓝图
│   ├── models.py                       # SQLAlchemy 数据模型：Resource, Tag, AccessLog
│   ├── routes/                         # 路由蓝图模块
│   │   ├── __init__.py                 # 统一导出所有蓝图
│   │   ├── import_routes.py            # 批量导入、去重校验接口
│   │   ├── search_routes.py            # 全文检索、正则过滤接口
│   │   ├── health_routes.py            # 状态检查、重定向追踪接口
│   │   └── export_routes.py            # JSON/CSV/Markdown 导出接口
│   ├── services/                       # 业务逻辑层
│   │   ├── parser.py                   # URL 路径解析器，抽取编号与时间戳
│   │   ├── checker.py                  # 并发 HTTP 健康检查器
│   │   ├── indexer.py                  # 倒排索引构建与查询器
│   │   └── exporter.py                 # 多格式数据导出器
│   ├── templates/                      # Jinja2 模板
│   │   ├── base.html                   # 基础布局模板
│   │   ├── dashboard.html              # 资源总览与统计看板
│   │   └── import_batch.html           # 批量粘贴导入页面
│   └── static/                         # 静态资源
│       ├── css/                        # Bootstrap 定制样式表
│       └── js/                         # 前端交互脚本（批量粘贴、实时校验）
├── scripts/                            # 运维与工具脚本
│   ├── init_db.py                      # 初始化 SQLite 数据库表结构
│   ├── seed_test_data.py               # 生成测试用模拟数据
│   └── batch_import_from_file.py       # 从文本文件批量导入 URL 的命令行工具
├── tests/                              # 单元测试与集成测试
│   ├── test_parser.py                  # 解析器边界用例测试
│   ├── test_checker.py                 # 健康检查超时与重试逻辑测试
│   └── test_routes.py                  # 路由接口的端到端测试
├── config/                             # 配置文件目录
│   ├── development.py                  # 开发环境配置（开启调试、SQLite 路径）
│   ├── production.py                   # 生产环境配置（关闭调试、日志级别）
│   └── testing.py                      # 测试环境配置（内存数据库）
├── docs/                               # 完整项目文档
│   ├── user_guide.md                   # 用户操作手册
│   ├── developer_guide.md              # 开发者扩展指南
│   ├── api_reference.md                # REST API 详细参考
│   └── deployment.md                   # 生产部署与运维手册
├── requirements.txt                    # 生产环境依赖列表
├── requirements-dev.txt                # 开发环境额外依赖（pytest, flake8, black）
├── .env.example                        # 环境变量配置示例
├── .gitignore                          # Git 忽略文件列表
├── Dockerfile                          # 容器化构建文件
├── docker-compose.yml                  # 本地开发容器编排
└── README.md                           # 项目主说明文档
```

## 贡献指南

1. 复刻仓库并创建功能分支 在 GitHub 页面点击 Fork 按钮将项目复制到个人账户，随后使用 git checkout -b feature/your-feature-name 创建分支进行开发。

2. 编写或更新单元测试 所有新增功能或缺陷修复均需在 tests/ 目录下编写对应的测试用例，确保测试覆盖率达到 80% 以上。运行 pytest tests/ 验证本地全部测试通过。

3. 遵循代码风格规范 代码格式使用 Black 进行统一格式化，导入语句排序使用 isort，提交前执行 black . && isort . 保证风格一致。

4. 提交变更并签署开发者原创声明 提交信息采用 Conventional Commits 格式（如 feat: 新增分类标签批量编辑接口），并在 Pull Request 描述中确认代码为原创且未侵犯第三方权益。

5. 发起 Pull Request 等待审核 推送分支至个人远程仓库后，在原始仓库发起 Pull Request，项目维护者将在 3 个工作日内进行代码审查并反馈修改意见。

## 常见问题

Q: 系统能同时处理多少条 URL 的导入请求？是否有数量限制？

A: WebLink Nexus 单次导入请求的默认上限为 10000 条 URL，超过此数量建议使用 scripts/batch_import_from_file.py 命令行工具分批导入。导入过程中采用流式处理与批量提交策略，1000 条 URL 的解析与入库操作通常在 2 秒内完成，具体耗时受网络健康检查并发数影响。

Q: 健康检查功能会频繁请求外部站点，是否会导致我的 IP 被限制？

A: 健康检查模块默认采用 5 个并发线程、超时时间 10 秒、重试 1 次的保守策略，且每次检查之间随机延迟 0.5 至 2 秒，以模拟真实用户访问行为。对于同一站点的检查频率可通过配置 CHECK_INTERVAL_HOURS 参数调整为每 24 小时仅检查一次，有效降低对外部站点的请求压力。

Q: 系统支持自定义元数据字段吗？比如我想为每条记录添加「来源部门」或「重要程度」属性？

A: 当前版本提供可扩展的标签系统（Tag），用户可通过创建不同的标签来实现分类维度的自定义。如需添加结构化字段，可以继承 models.py 中的 Resource 模型，在子类中定义额外列，或使用 metadata 字段存储 JSON 格式的扩展属性。完整的自定义字段指南请参考 docs/developer_guide.md 中的数据模型扩展章节。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:01
