# JNews Link Aggregator

JNews Link Aggregator 是一个面向技术内容聚合与新闻线索管理的开源外链汇总系统，专为需要批量处理、分类整理和快速检索分散式新闻资源的技术团队与内容运营者设计。项目定位为轻量级新闻外链中台，不依赖复杂的前端框架，通过结构化数据管理和静态资源映射，帮助用户从混乱的 URL 列表中提取有价值的信息线索。

该项目诞生于第 136/300 批资源整理计划，目前已经完成对 300 个新闻来源链接的规范化收录与分类标注。JNews Link Aggregator 不提供爬虫或自动化采集功能，而是作为人工整理与机器可读索引之间的桥梁，为后续的数据分析、舆情监控或历史归档提供干净的数据入口。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入新闻链接，自动去重并校验协议格式。

**分类标签系统** 每个链接可绑定多个自定义标签，支持按来源域名、内容主题、收录批次或时间范围进行多维度筛选。

**元数据提取辅助** 提供 URL 解析工具，自动提取域名、路径层级、文件扩展名和查询参数，辅助用户快速识别链接结构特征。

**状态跟踪管理** 为每个链接标记已读、待处理、归档或失效状态，支持手动更新和批量状态变更。

**检索与过滤引擎** 基于关键字、域名、状态和标签组合的布尔查询，毫秒级返回匹配结果，支持结果导出为 JSON 或 Markdown 表格。

**收录批次记录** 内置批次管理模块，当前批次为第 136/300 批，支持批次备注、收录时间戳和进度追踪。

**数据导出接口** 提供 RESTful 风格的查询接口，可输出完整链接列表、分类统计或特定标签下的资源快照。

## 应用场景

**技术团队内部新闻源整理** 开发或运维团队可将分散在多个渠道的公告、更新日志或安全通告链接统一收录，形成内部可共享的知识索引，避免信息孤岛。

**内容运营人员选题挖掘** 运营人员通过标签和关键字检索，快速定位特定领域的历史新闻链接，分析报道趋势或寻找素材来源，提升选题效率。

**历史数据归档与审计** 对于需要长期保存新闻链接记录的项目，JNews Link Aggregator 提供批次管理和状态追踪，便于回溯特定时间段的收录情况或审计链接可用性。

**个人研究者的资源管理** 独立研究者可利用该工具整理文献、新闻报道或事件时间线，通过分类和检索功能快速构建个人研究数据库。

## 快速开始

以下步骤指导您在本地环境快速启动 JNews Link Aggregator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/jnews-link-aggregator.git

# 进入项目目录
cd jnews-link-aggregator

# 安装依赖（基于 Python 3.10+ 与 pip）
pip install -r requirements.txt

# 初始化本地数据库（SQLite）
python scripts/init_db.py

# 运行开发服务器
python app.py --port 8080
```

启动后，访问 `http://localhost:8080` 即可进入链接管理界面。默认管理员账户为 `admin`，密码在首次启动时由初始化脚本生成并输出至控制台。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 或更高 | 核心运行环境，低于此版本将导致类型注解解析失败 |
| SQLite | 3.35 或更高 | 默认内嵌数据库，用于存储链接元数据和标签关系 |
| Flask | 2.3.x | Web 服务框架，提供路由和请求处理能力 |
| Jinja2 | 3.1.x | 模板引擎，用于渲染管理界面 |
| Werkzeug | 2.3.x | WSGI 工具集，用于调试和请求上下文管理 |
| markdown | 3.5.x | 用于将链接备注中的 Markdown 内容渲染为 HTML |
| pytest | 7.4.x | 可选依赖，仅在运行测试套件时需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | `/docs/user-guide.md` | 如何批量导入链接、如何创建标签、如何检索和导出数据 |
| 管理员指南 | `/docs/admin-guide.md` | 如何初始化数据库、管理用户权限、执行数据备份与恢复 |
| 开发者文档 | `/docs/developer-guide.md` | 如何扩展数据模型、自定义导出格式、贡献代码或插件 |
| API 参考 | `/docs/api-reference.md` | RESTful 接口的端点定义、请求参数、返回格式与状态码说明 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/54973.htm
- http://m.wap.ghtkgg.cn/jnews/1987.htm
- http://m.wap.ghtkgg.cn/jnews/7634156.htm
- http://m.wap.ghtkgg.cn/jnews/7714964.htm
- http://m.wap.ghtkgg.cn/jnews/985975.htm
- http://m.wap.ghtkgg.cn/jnews/6368.htm
- http://m.wap.ghtkgg.cn/jnews/5363.htm
- http://m.wap.ghtkgg.cn/jnews/41449.htm
- http://m.wap.ghtkgg.cn/jnews/384804.htm
- http://m.wap.ghtkgg.cn/jnews/49146.htm
- http://m.wap.ghtkgg.cn/jnews/90049.htm
- http://m.wap.ghtkgg.cn/jnews/90916.htm
- http://m.wap.ghtkgg.cn/jnews/58815.htm
- http://m.wap.ghtkgg.cn/jnews/2266765.htm
- http://m.wap.ghtkgg.cn/jnews/5237832.htm
- http://m.wap.ghtkgg.cn/jnews/97711.htm
- http://m.wap.ghtkgg.cn/jnews/0814433.htm
- http://m.wap.ghtkgg.cn/jnews/55397.htm
- http://m.wap.ghtkgg.cn/jnews/14711.htm
- http://m.wap.ghtkgg.cn/jnews/88204.htm
- http://m.wap.ghtkgg.cn/jnews/7346.htm
- http://m.wap.ghtkgg.cn/jnews/9816791.htm
- http://m.wap.ghtkgg.cn/jnews/3569637.htm
- http://m.wap.ghtkgg.cn/jnews/2525.htm
- http://m.wap.ghtkgg.cn/jnews/5474088.htm
- http://m.wap.ghtkgg.cn/jnews/9806.htm
- http://m.wap.ghtkgg.cn/jnews/6056.htm
- http://m.wap.ghtkgg.cn/jnews/9316.htm
- http://m.wap.ghtkgg.cn/jnews/2895907.htm
- http://m.wap.ghtkgg.cn/jnews/729864.htm
- http://m.wap.ghtkgg.cn/jnews/7554569.htm
- http://m.wap.ghtkgg.cn/jnews/052988.htm
- http://m.wap.ghtkgg.cn/jnews/6744.htm
- http://m.wap.ghtkgg.cn/jnews/4675.htm
- http://m.wap.ghtkgg.cn/jnews/803646.htm
- http://m.wap.ghtkgg.cn/jnews/48306.htm
- http://m.wap.ghtkgg.cn/jnews/99699.htm
- http://m.wap.ghtkgg.cn/jnews/144891.htm
- http://m.wap.ghtkgg.cn/jnews/9984292.htm
- http://m.wap.ghtkgg.cn/jnews/0929.htm
- http://m.wap.ghtkgg.cn/jnews/1817971.htm
- http://m.wap.ghtkgg.cn/jnews/839188.htm
- http://m.wap.ghtkgg.cn/jnews/7550119.htm
- http://m.wap.ghtkgg.cn/jnews/289387.htm
- http://m.wap.ghtkgg.cn/jnews/8981.htm
- http://m.wap.ghtkgg.cn/jnews/42199.htm
- http://m.wap.ghtkgg.cn/jnews/0700.htm
- http://m.wap.ghtkgg.cn/jnews/71532.htm
- http://m.wap.ghtkgg.cn/jnews/774711.htm
- http://m.wap.ghtkgg.cn/jnews/27775.htm
- http://m.wap.ghtkgg.cn/jnews/678009.htm
- http://m.wap.ghtkgg.cn/jnews/54660.htm
- http://m.wap.ghtkgg.cn/jnews/46764.htm
- http://m.wap.ghtkgg.cn/jnews/399566.htm
- http://m.wap.ghtkgg.cn/jnews/035293.htm
- http://m.wap.ghtkgg.cn/jnews/443470.htm
- http://m.wap.ghtkgg.cn/jnews/8274.htm
- http://m.wap.ghtkgg.cn/jnews/020153.htm
- http://m.wap.ghtkgg.cn/jnews/17808.htm
- http://m.wap.ghtkgg.cn/jnews/5448310.htm
- http://m.wap.ghtkgg.cn/jnews/1386.htm
- http://m.wap.ghtkgg.cn/jnews/80414.htm
- http://m.wap.ghtkgg.cn/jnews/71717.htm
- http://m.wap.ghtkgg.cn/jnews/5070.htm
- http://m.wap.ghtkgg.cn/jnews/3613.htm
- http://m.wap.ghtkgg.cn/jnews/4230.htm
- http://m.wap.ghtkgg.cn/jnews/1050659.htm
- http://m.wap.ghtkgg.cn/jnews/8620.htm
- http://m.wap.ghtkgg.cn/jnews/013544.htm
- http://m.wap.ghtkgg.cn/jnews/78265.htm
- http://m.wap.ghtkgg.cn/jnews/359802.htm
- http://m.wap.ghtkgg.cn/jnews/44013.htm
- http://m.wap.ghtkgg.cn/jnews/46943.htm
- http://m.wap.ghtkgg.cn/jnews/2874.htm
- http://m.wap.ghtkgg.cn/jnews/7401169.htm
- http://m.wap.ghtkgg.cn/jnews/8741.htm
- http://m.wap.ghtkgg.cn/jnews/1992.htm
- http://m.wap.ghtkgg.cn/jnews/526730.htm
- http://m.wap.ghtkgg.cn/jnews/393798.htm
- http://m.wap.ghtkgg.cn/jnews/5032335.htm
- http://m.wap.ghtkgg.cn/jnews/1286432.htm
- http://m.wap.ghtkgg.cn/jnews/46953.htm
- http://m.wap.ghtkgg.cn/jnews/35031.htm
- http://m.wap.ghtkgg.cn/jnews/2656657.htm
- http://m.wap.ghtkgg.cn/jnews/9818861.htm
- http://m.wap.ghtkgg.cn/jnews/5671947.htm
- http://m.wap.ghtkgg.cn/jnews/0399955.htm
- http://m.wap.ghtkgg.cn/jnews/2508095.htm
- http://m.wap.ghtkgg.cn/jnews/4471.htm
- http://m.wap.ghtkgg.cn/jnews/42992.htm
- http://m.wap.ghtkgg.cn/jnews/780507.htm
- http://m.wap.ghtkgg.cn/jnews/8506307.htm
- http://m.wap.ghtkgg.cn/jnews/3208.htm
- http://m.wap.ghtkgg.cn/jnews/994050.htm
- http://m.wap.ghtkgg.cn/jnews/9730.htm
- http://m.wap.ghtkgg.cn/jnews/7346041.htm
- http://m.wap.ghtkgg.cn/jnews/23412.htm
- http://m.wap.ghtkgg.cn/jnews/6175.htm
- http://m.wap.ghtkgg.cn/jnews/08360.htm
- http://m.wap.ghtkgg.cn/jnews/210561.htm
- http://m.wap.ghtkgg.cn/jnews/1883010.htm
- http://m.wap.ghtkgg.cn/jnews/8044.htm
- http://m.wap.ghtkgg.cn/jnews/0239.htm
- http://m.wap.ghtkgg.cn/jnews/4948.htm
- http://m.wap.ghtkgg.cn/jnews/5711523.htm
- http://m.wap.ghtkgg.cn/jnews/3586.htm
- http://m.wap.ghtkgg.cn/jnews/469818.htm
- http://m.wap.ghtkgg.cn/jnews/63422.htm
- http://m.wap.ghtkgg.cn/jnews/157170.htm
- http://m.wap.ghtkgg.cn/jnews/415714.htm
- http://m.wap.ghtkgg.cn/jnews/506002.htm
- http://m.wap.ghtkgg.cn/jnews/9413.htm
- http://m.wap.ghtkgg.cn/jnews/931951.htm
- http://m.wap.ghtkgg.cn/jnews/697391.htm
- http://m.wap.ghtkgg.cn/jnews/1225478.htm
- http://m.wap.ghtkgg.cn/jnews/1066.htm
- http://m.wap.ghtkgg.cn/jnews/390345.htm
- http://m.wap.ghtkgg.cn/jnews/3746567.htm
- http://m.wap.ghtkgg.cn/jnews/408031.htm
- http://m.wap.ghtkgg.cn/jnews/522943.htm
- http://m.wap.ghtkgg.cn/jnews/23318.htm
- http://m.wap.ghtkgg.cn/jnews/3270257.htm
- http://m.wap.ghtkgg.cn/jnews/064891.htm
- http://m.wap.ghtkgg.cn/jnews/008083.htm
- http://m.wap.ghtkgg.cn/jnews/508759.htm
- http://m.wap.ghtkgg.cn/jnews/1295.htm
- http://m.wap.ghtkgg.cn/jnews/272633.htm
- http://m.wap.ghtkgg.cn/jnews/39136.htm
- http://m.wap.ghtkgg.cn/jnews/2592.htm
- http://m.wap.ghtkgg.cn/jnews/0214573.htm
- http://m.wap.ghtkgg.cn/jnews/8209.htm
- http://m.wap.ghtkgg.cn/jnews/37115.htm
- http://m.wap.ghtkgg.cn/jnews/4097601.htm
- http://m.wap.ghtkgg.cn/jnews/631208.htm
- http://m.wap.ghtkgg.cn/jnews/2831.htm
- http://m.wap.ghtkgg.cn/jnews/2888600.htm
- http://m.wap.ghtkgg.cn/jnews/7424470.htm
- http://m.wap.ghtkgg.cn/jnews/9020821.htm
- http://m.wap.ghtkgg.cn/jnews/448215.htm
- http://m.wap.ghtkgg.cn/jnews/8341.htm
- http://m.wap.ghtkgg.cn/jnews/98280.htm
- http://m.wap.ghtkgg.cn/jnews/228738.htm
- http://m.wap.ghtkgg.cn/jnews/63716.htm
- http://m.wap.ghtkgg.cn/jnews/888931.htm
- http://m.wap.ghtkgg.cn/jnews/4423700.htm
- http://m.wap.ghtkgg.cn/jnews/9161.htm
- http://m.wap.ghtkgg.cn/jnews/71225.htm
- http://m.wap.ghtkgg.cn/jnews/54975.htm
- http://m.wap.ghtkgg.cn/jnews/8426010.htm
- http://m.wap.ghtkgg.cn/jnews/31390.htm
- http://m.wap.ghtkgg.cn/jnews/80941.htm
- http://m.wap.ghtkgg.cn/jnews/719583.htm
- http://m.wap.ghtkgg.cn/jnews/6952270.htm
- http://m.wap.ghtkgg.cn/jnews/2722.htm
- http://m.wap.ghtkgg.cn/jnews/302344.htm
- http://m.wap.ghtkgg.cn/jnews/044221.htm
- http://m.wap.ghtkgg.cn/jnews/7709.htm
- http://m.wap.ghtkgg.cn/jnews/989716.htm
- http://m.wap.ghtkgg.cn/jnews/4498.htm
- http://m.wap.ghtkgg.cn/jnews/6015.htm
- http://m.wap.ghtkgg.cn/jnews/1731.htm
- http://m.wap.ghtkgg.cn/jnews/9105964.htm
- http://m.wap.ghtkgg.cn/jnews/80395.htm
- http://m.wap.ghtkgg.cn/jnews/5980.htm
- http://m.wap.ghtkgg.cn/jnews/2145.htm
- http://m.wap.ghtkgg.cn/jnews/64505.htm
- http://m.wap.ghtkgg.cn/jnews/654758.htm
- http://m.wap.ghtkgg.cn/jnews/672345.htm
- http://m.wap.ghtkgg.cn/jnews/9968.htm
- http://m.wap.ghtkgg.cn/jnews/81827.htm
- http://m.wap.ghtkgg.cn/jnews/48002.htm
- http://m.wap.ghtkgg.cn/jnews/640721.htm
- http://m.wap.ghtkgg.cn/jnews/37058.htm
- http://m.wap.ghtkgg.cn/jnews/844547.htm
- http://m.wap.ghtkgg.cn/jnews/900263.htm
- http://m.wap.ghtkgg.cn/jnews/053705.htm
- http://m.wap.ghtkgg.cn/jnews/054358.htm
- http://m.wap.ghtkgg.cn/jnews/3502.htm
- http://m.wap.ghtkgg.cn/jnews/88847.htm
- http://m.wap.ghtkgg.cn/jnews/08853.htm
- http://m.wap.ghtkgg.cn/jnews/8093069.htm
- http://m.wap.ghtkgg.cn/jnews/2918.htm
- http://m.wap.ghtkgg.cn/jnews/419305.htm
- http://m.wap.ghtkgg.cn/jnews/7749.htm
- http://m.wap.ghtkgg.cn/jnews/4848147.htm
- http://m.wap.ghtkgg.cn/jnews/3608.htm
- http://m.wap.ghtkgg.cn/jnews/4442484.htm
- http://m.wap.ghtkgg.cn/jnews/849933.htm
- http://m.wap.ghtkgg.cn/jnews/107900.htm
- http://m.wap.ghtkgg.cn/jnews/68735.htm
- http://m.wap.ghtkgg.cn/jnews/7458037.htm
- http://m.wap.ghtkgg.cn/jnews/306137.htm
- http://m.wap.ghtkgg.cn/jnews/69950.htm
- http://m.wap.ghtkgg.cn/jnews/4194852.htm
- http://m.wap.ghtkgg.cn/jnews/5258.htm
- http://m.wap.ghtkgg.cn/jnews/9870573.htm
- http://m.wap.ghtkgg.cn/jnews/311811.htm
- http://m.wap.ghtkgg.cn/jnews/8805466.htm
- http://m.wap.ghtkgg.cn/jnews/0560426.htm
- http://m.wap.ghtkgg.cn/jnews/5384781.htm
- http://m.wap.ghtkgg.cn/jnews/7472645.htm
- http://m.wap.ghtkgg.cn/jnews/7714425.htm
- http://m.wap.ghtkgg.cn/jnews/5614.htm
- http://m.wap.ghtkgg.cn/jnews/4987998.htm
- http://m.wap.ghtkgg.cn/jnews/331416.htm
- http://m.wap.ghtkgg.cn/jnews/9240504.htm
- http://m.wap.ghtkgg.cn/jnews/1899289.htm
- http://m.wap.ghtkgg.cn/jnews/28554.htm
- http://m.wap.ghtkgg.cn/jnews/41032.htm
- http://m.wap.ghtkgg.cn/jnews/4947.htm
- http://m.wap.ghtkgg.cn/jnews/192989.htm
- http://m.wap.ghtkgg.cn/jnews/31677.htm
- http://m.wap.ghtkgg.cn/jnews/6942.htm
- http://m.wap.ghtkgg.cn/jnews/7568361.htm
- http://m.wap.ghtkgg.cn/jnews/872860.htm
- http://m.wap.ghtkgg.cn/jnews/6352.htm
- http://m.wap.ghtkgg.cn/jnews/2033795.htm
- http://m.wap.ghtkgg.cn/jnews/9586.htm
- http://m.wap.ghtkgg.cn/jnews/6292.htm
- http://m.wap.ghtkgg.cn/jnews/40377.htm
- http://m.wap.ghtkgg.cn/jnews/10556.htm
- http://m.wap.ghtkgg.cn/jnews/59396.htm
- http://m.wap.ghtkgg.cn/jnews/467398.htm
- http://m.wap.ghtkgg.cn/jnews/111038.htm
- http://m.wap.ghtkgg.cn/jnews/4067.htm
- http://m.wap.ghtkgg.cn/jnews/0968.htm
- http://m.wap.ghtkgg.cn/jnews/69369.htm
- http://m.wap.ghtkgg.cn/jnews/883902.htm
- http://m.wap.ghtkgg.cn/jnews/6675.htm
- http://m.wap.ghtkgg.cn/jnews/3298541.htm
- http://m.wap.ghtkgg.cn/jnews/98189.htm
- http://m.wap.ghtkgg.cn/jnews/898105.htm
- http://m.wap.ghtkgg.cn/jnews/42738.htm
- http://m.wap.ghtkgg.cn/jnews/3085754.htm
- http://m.wap.ghtkgg.cn/jnews/610995.htm
- http://m.wap.ghtkgg.cn/jnews/717884.htm
- http://m.wap.ghtkgg.cn/jnews/481944.htm
- http://m.wap.ghtkgg.cn/jnews/0101125.htm
- http://m.wap.ghtkgg.cn/jnews/735700.htm
- http://m.wap.ghtkgg.cn/jnews/45800.htm
- http://m.wap.ghtkgg.cn/jnews/342994.htm
- http://m.wap.ghtkgg.cn/jnews/65207.htm
- http://m.wap.ghtkgg.cn/jnews/288041.htm
- http://m.wap.ghtkgg.cn/jnews/629979.htm
- http://m.wap.ghtkgg.cn/jnews/89893.htm
- http://m.wap.ghtkgg.cn/jnews/892773.htm
- http://m.wap.ghtkgg.cn/jnews/709190.htm
- http://m.wap.ghtkgg.cn/jnews/4802.htm
- http://m.wap.ghtkgg.cn/jnews/839854.htm
- http://m.wap.ghtkgg.cn/jnews/869969.htm
- http://m.wap.ghtkgg.cn/jnews/5888.htm
- http://m.wap.ghtkgg.cn/jnews/3826.htm
- http://m.wap.ghtkgg.cn/jnews/74787.htm
- http://m.wap.ghtkgg.cn/jnews/0300589.htm
- http://m.wap.ghtkgg.cn/jnews/24809.htm
- http://m.wap.ghtkgg.cn/jnews/925679.htm
- http://m.wap.ghtkgg.cn/jnews/50156.htm
- http://m.wap.ghtkgg.cn/jnews/9232.htm
- http://m.wap.ghtkgg.cn/jnews/5074.htm
- http://m.wap.ghtkgg.cn/jnews/50021.htm
- http://m.wap.ghtkgg.cn/jnews/466748.htm
- http://m.wap.ghtkgg.cn/jnews/447556.htm
- http://m.wap.ghtkgg.cn/jnews/989941.htm
- http://m.wap.ghtkgg.cn/jnews/563946.htm
- http://m.wap.ghtkgg.cn/jnews/6511095.htm
- http://m.wap.ghtkgg.cn/jnews/4407.htm
- http://m.wap.ghtkgg.cn/jnews/0031633.htm
- http://m.wap.ghtkgg.cn/jnews/610481.htm
- http://m.wap.ghtkgg.cn/jnews/0617262.htm
- http://m.wap.ghtkgg.cn/jnews/875060.htm
- http://m.wap.ghtkgg.cn/jnews/222172.htm
- http://m.wap.ghtkgg.cn/jnews/8777.htm
- http://m.wap.ghtkgg.cn/jnews/447551.htm
- http://m.wap.ghtkgg.cn/jnews/5740.htm
- http://m.wap.ghtkgg.cn/jnews/747673.htm
- http://m.wap.ghtkgg.cn/jnews/1289.htm
- http://m.wap.ghtkgg.cn/jnews/01630.htm
- http://m.wap.ghtkgg.cn/jnews/3496.htm
- http://m.wap.ghtkgg.cn/jnews/548682.htm
- http://m.wap.ghtkgg.cn/jnews/26122.htm
- http://m.wap.ghtkgg.cn/jnews/07140.htm
- http://m.wap.ghtkgg.cn/jnews/3959.htm
- http://m.wap.ghtkgg.cn/jnews/36307.htm
- http://m.wap.ghtkgg.cn/jnews/4355.htm
- http://m.wap.ghtkgg.cn/jnews/29467.htm
- http://m.wap.ghtkgg.cn/jnews/5569950.htm
- http://m.wap.ghtkgg.cn/jnews/3709399.htm
- http://m.wap.ghtkgg.cn/jnews/42829.htm
- http://m.wap.ghtkgg.cn/jnews/456136.htm
- http://m.wap.ghtkgg.cn/jnews/58443.htm
- http://m.wap.ghtkgg.cn/jnews/221791.htm
- http://m.wap.ghtkgg.cn/jnews/01200.htm
- http://m.wap.ghtkgg.cn/jnews/303647.htm
- http://m.wap.ghtkgg.cn/jnews/1083.htm
- http://m.wap.ghtkgg.cn/jnews/48413.htm
- http://m.wap.ghtkgg.cn/jnews/3253.htm
- http://m.wap.ghtkgg.cn/jnews/119051.htm
- http://m.wap.ghtkgg.cn/jnews/4682527.htm
- http://m.wap.ghtkgg.cn/jnews/9569538.htm
- http://m.wap.ghtkgg.cn/jnews/2386149.htm

## 项目结构

```
jnews-link-aggregator/
├── app.py                         # 主入口文件，初始化 Flask 应用并注册路由
├── requirements.txt               # Python 依赖列表，锁定所有第三方库版本
├── config/
│   ├── default.py                 # 默认配置项（端口、数据库路径、日志级别）
│   └── production.py              # 生产环境覆盖配置（禁用调试、使用外部数据库）
├── models/
│   ├── __init__.py                # 模型包初始化，导出核心 ORM 类
│   ├── link.py                    # Link 数据模型定义（URL、状态、标签、批次）
│   ├── tag.py                     # Tag 数据模型定义（名称、颜色、创建时间）
│   └── batch.py                   # Batch 数据模型定义（批次号、收录数量、备注）
├── services/
│   ├── importer.py                # 批量链接导入服务（支持 txt/csv/纯文本）
│   ├── exporter.py                # 数据导出服务（JSON / Markdown / CSV）
│   └── validator.py               # URL 格式校验与去重服务
├── routes/
│   ├── api.py                     # RESTful API 路由（查询、导入、导出、状态更新）
│   └── web.py                     # 管理界面路由（仪表盘、列表页、详情页）
├── static/                        # 前端静态资源（CSS、JavaScript、图标）
│   ├── css/
│   │   └── style.css              # 管理界面样式表
│   └── js/
│       └── dashboard.js           # 前端交互逻辑（筛选、批量操作、实时搜索）
├── templates/
│   ├── base.html                  # 基础模板，包含导航栏和页脚
│   ├── index.html                 # 链接列表主页，包含筛选表单和表格
│   └── detail.html                # 单条链接详情页，展示元数据和操作按钮
├── scripts/
│   ├── init_db.py                 # 初始化 SQLite 数据库表结构和默认数据
│   └── seed_sample.py             # 填充示例链接和标签，用于测试和演示
├── tests/
│   ├── test_models.py             # 数据模型单元测试
│   ├── test_services.py           # 导入和导出服务单元测试
│   └── test_routes.py             # API 路由集成测试
└── docs/
    ├── user-guide.md              # 用户手册（导入、检索、导出操作说明）
    ├── admin-guide.md             # 管理员指南（部署、备份、权限配置）
    ├── developer-guide.md         # 开发者文档（扩展模型、自定义导出、插件开发）
    └── api-reference.md           # 完整 API 参考文档（端点、参数、示例）
```

## 贡献指南

**提交 Issue 报告缺陷或提议功能** 在 GitHub Issues 页面选择对应模板，详细描述问题现象、复现步骤或功能需求，并附上相关日志或截图。

**Fork 仓库并创建功能分支** 将主仓库 Fork 至个人账户，基于 `main` 分支创建新的功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。

**编写或更新测试用例** 确保新增代码或修复包含对应的单元测试或集成测试，运行 `pytest tests/` 验证所有测试通过且覆盖率不低于 80%。

**提交 Pull Request 并关联 Issue** 提交 PR 前请同步上游仓库的最新代码，解决冲突后填写 PR 模板中的检查清单，并在描述中关联相关的 Issue 编号。

**代码风格与文档规范** Python 代码遵循 PEP 8 规范，使用 Black 格式化，文档字符串采用 Google 风格；用户文档需在 `docs/` 目录下同步更新。

## 常见问题

**问：导入包含大量链接的文件时，页面响应超时怎么办？**

答：单次导入建议不超过 500 条链接。若需导入大规模数据，推荐使用命令行脚本 `scripts/bulk_import.py`，该脚本支持分批次提交和进度显示，避免 Web 请求超时。同时可调整 `config/default.py` 中的 `IMPORT_CHUNK_SIZE` 参数控制每批次大小。

**问：如何迁移数据库到生产环境的 PostgreSQL？**

答：项目默认使用 SQLite，但支持 PostgreSQL 作为生产数据库。需在 `config/production.py` 中配置 `SQLALCHEMY_DATABASE_URI` 为 PostgreSQL 连接串，然后运行 `flask db upgrade` 迁移现有表结构。注意 SQLite 与 PostgreSQL 在数据类型上有细微差异，建议先在测试环境验证。

**问：链接状态更新后，前端页面没有立即刷新显示？**

答：前端页面默认启用缓存以提升性能。若需强制刷新，可在浏览器中使用 Ctrl+F5 清除缓存。若问题持续，请检查浏览器控制台是否有 JavaScript 错误，或确认后端 API 返回的状态码是否为 200。对于批量更新，建议使用 `/api/links/batch` 接口并设置 `async=false` 参数同步等待完成。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:04
