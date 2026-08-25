# WebLink Navigator

WebLink Navigator 是一个面向技术研究人员、信息聚合开发者与内容分析团队的高性能外链资源导航系统。该项目定位于对大规模分散式网络资源进行结构化整理、状态监控与快速检索，提供从原始链接收集到健康度检测、分类标注、导出集成的完整工具链。主要解决用户在管理数百乃至数千个外部链接时面临的分类混乱、失效不可知、检索低效以及缺乏自动化监控手段等核心问题。

## 功能概览

**批量链接导入与解析**：支持从纯文本、CSV 及 JSON 格式批量导入 URL 列表，自动识别协议头与域名结构，并对异常格式进行容错处理。

**链接健康度定时检测**：内置异步 HTTP 请求引擎，可配置定时任务（每分钟至每周）对全部或指定分组链接进行可达性检测，返回状态码、响应时间与内容摘要。

**多维度标签分类体系**：允许用户创建无限层级的标签树，为每个链接分配一个或多个标签，支持基于标签的快速筛选与统计分析。

**全文检索与高级过滤**：基于 URL、页面标题、自定义备注及标签组合进行全文检索，支持正则表达式与模糊匹配模式。

**资源变更历史记录**：对链接的每一次新增、删除、标签修改与状态变更均记录审计日志，支持按时间轴回溯操作记录。

**监控告警通知**：当链接状态从可用变为不可用，或响应时间超过预设阈值时，通过 Webhook 或邮件发送告警通知。

**开放 API 与数据导出**：提供 RESTful API 接口，支持 JSON、XML 与 Markdown 格式的数据全量导出，便于集成到其他文档或监控系统。

## 应用场景

技术博客与文档站点的外链管理：技术作者在撰写文章或维护项目文档时，经常需要引用大量外部参考资料。WebLink Navigator 可以帮助作者集中管理这些引用链接，定期检测其有效性，避免文档中出现死链，提升文档质量与读者体验。

信息聚合平台的数据源监控：运营信息聚合类网站或每日简报服务的团队，需要从数十个固定新闻源或技术站点抓取内容。使用 WebLink Navigator 可统一管理这些数据源 URL，监控其可用性与响应性能，在源站出现异常时及时切换或告警。

企业内外部资源导航门户建设：企业内部通常存在多个常用系统入口、知识库地址与工具平台。该工具可作为后端链接库，为内部导航页提供数据支撑，保证入口地址的准确性与变更同步。

学术研究中的参考文献管理：科研人员在整理文献综述或技术调研时，需要追踪大量在线论文、项目仓库与技术讨论帖。WebLink Navigator 提供的标签分类与变更记录功能有助于按研究主题组织链接，并追溯链接状态变化。

## 快速开始

以下步骤指导您在本地环境中快速启动 WebLink Navigator 服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装依赖（使用 pip 与虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化数据库与配置文件
cp .env.example .env
python scripts/init_db.py

# 启动开发服务器
python app.py
```

服务启动后，访问 http://localhost:5000 即可进入 Web 管理界面。默认管理员账号为 admin，密码在首次启动时打印在控制台日志中。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，推荐使用 3.11 或 3.12 |
| SQLite | 3.35 及以上 | 默认内置数据库，用于存储链接信息与审计日志 |
| Redis | 6.0 及以上 | 可选，用于任务队列缓存与分布式锁，生产环境建议配置 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发链接健康检测 |
| APScheduler | 3.10.0 及以上 | 定时任务调度引擎，驱动周期性检测任务 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 基础入门 | /docs/quick-start.md | 如何快速安装并运行第一个链接扫描任务 |
| 功能手册 | /docs/user-guide/link-management.md | 如何批量导入、编辑、分类和删除链接资源 |
| 运维指南 | /docs/operations/monitoring-config.md | 如何配置检测频率、告警规则与日志轮转 |
| 开发参考 | /docs/developer/api-endpoints.md | 如何使用 REST API 进行二次开发与数据集成 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/154741.htm
- http://m.wap.ghtkgg.cn/jnews/4706.htm
- http://m.wap.ghtkgg.cn/jnews/533462.htm
- http://m.wap.ghtkgg.cn/jnews/72573.htm
- http://m.wap.ghtkgg.cn/jnews/5886683.htm
- http://m.wap.ghtkgg.cn/jnews/1995.htm
- http://m.wap.ghtkgg.cn/jnews/23191.htm
- http://m.wap.ghtkgg.cn/jnews/7240935.htm
- http://m.wap.ghtkgg.cn/jnews/4279.htm
- http://m.wap.ghtkgg.cn/jnews/4042175.htm
- http://m.wap.ghtkgg.cn/jnews/7055550.htm
- http://m.wap.ghtkgg.cn/jnews/49252.htm
- http://m.wap.ghtkgg.cn/jnews/193386.htm
- http://m.wap.ghtkgg.cn/jnews/299472.htm
- http://m.wap.ghtkgg.cn/jnews/810420.htm
- http://m.wap.ghtkgg.cn/jnews/290206.htm
- http://m.wap.ghtkgg.cn/jnews/1241704.htm
- http://m.wap.ghtkgg.cn/jnews/80699.htm
- http://m.wap.ghtkgg.cn/jnews/142883.htm
- http://m.wap.ghtkgg.cn/jnews/600673.htm
- http://m.wap.ghtkgg.cn/jnews/50756.htm
- http://m.wap.ghtkgg.cn/jnews/1361.htm
- http://m.wap.ghtkgg.cn/jnews/599982.htm
- http://m.wap.ghtkgg.cn/jnews/3973.htm
- http://m.wap.ghtkgg.cn/jnews/034618.htm
- http://m.wap.ghtkgg.cn/jnews/2786.htm
- http://m.wap.ghtkgg.cn/jnews/9438.htm
- http://m.wap.ghtkgg.cn/jnews/60617.htm
- http://m.wap.ghtkgg.cn/jnews/693165.htm
- http://m.wap.ghtkgg.cn/jnews/8051937.htm
- http://m.wap.ghtkgg.cn/jnews/72260.htm
- http://m.wap.ghtkgg.cn/jnews/6632.htm
- http://m.wap.ghtkgg.cn/jnews/5293541.htm
- http://m.wap.ghtkgg.cn/jnews/84098.htm
- http://m.wap.ghtkgg.cn/jnews/6205581.htm
- http://m.wap.ghtkgg.cn/jnews/24968.htm
- http://m.wap.ghtkgg.cn/jnews/492420.htm
- http://m.wap.ghtkgg.cn/jnews/414457.htm
- http://m.wap.ghtkgg.cn/jnews/78864.htm
- http://m.wap.ghtkgg.cn/jnews/573918.htm
- http://m.wap.ghtkgg.cn/jnews/8995.htm
- http://m.wap.ghtkgg.cn/jnews/8436143.htm
- http://m.wap.ghtkgg.cn/jnews/444612.htm
- http://m.wap.ghtkgg.cn/jnews/7326759.htm
- http://m.wap.ghtkgg.cn/jnews/9580.htm
- http://m.wap.ghtkgg.cn/jnews/2452.htm
- http://m.wap.ghtkgg.cn/jnews/5482.htm
- http://m.wap.ghtkgg.cn/jnews/8391.htm
- http://m.wap.ghtkgg.cn/jnews/2232110.htm
- http://m.wap.ghtkgg.cn/jnews/07258.htm
- http://m.wap.ghtkgg.cn/jnews/580641.htm
- http://m.wap.ghtkgg.cn/jnews/9985472.htm
- http://m.wap.ghtkgg.cn/jnews/5781.htm
- http://m.wap.ghtkgg.cn/jnews/040308.htm
- http://m.wap.ghtkgg.cn/jnews/287930.htm
- http://m.wap.ghtkgg.cn/jnews/0086.htm
- http://m.wap.ghtkgg.cn/jnews/666775.htm
- http://m.wap.ghtkgg.cn/jnews/2038.htm
- http://m.wap.ghtkgg.cn/jnews/9174387.htm
- http://m.wap.ghtkgg.cn/jnews/3366619.htm
- http://m.wap.ghtkgg.cn/jnews/9826381.htm
- http://m.wap.ghtkgg.cn/jnews/0208.htm
- http://m.wap.ghtkgg.cn/jnews/35513.htm
- http://m.wap.ghtkgg.cn/jnews/0316785.htm
- http://m.wap.ghtkgg.cn/jnews/89151.htm
- http://m.wap.ghtkgg.cn/jnews/500939.htm
- http://m.wap.ghtkgg.cn/jnews/8932642.htm
- http://m.wap.ghtkgg.cn/jnews/278584.htm
- http://m.wap.ghtkgg.cn/jnews/768664.htm
- http://m.wap.ghtkgg.cn/jnews/290895.htm
- http://m.wap.ghtkgg.cn/jnews/5461841.htm
- http://m.wap.ghtkgg.cn/jnews/9924456.htm
- http://m.wap.ghtkgg.cn/jnews/21424.htm
- http://m.wap.ghtkgg.cn/jnews/0116.htm
- http://m.wap.ghtkgg.cn/jnews/04068.htm
- http://m.wap.ghtkgg.cn/jnews/11851.htm
- http://m.wap.ghtkgg.cn/jnews/9117.htm
- http://m.wap.ghtkgg.cn/jnews/6919055.htm
- http://m.wap.ghtkgg.cn/jnews/758872.htm
- http://m.wap.ghtkgg.cn/jnews/264755.htm
- http://m.wap.ghtkgg.cn/jnews/9204830.htm
- http://m.wap.ghtkgg.cn/jnews/4068956.htm
- http://m.wap.ghtkgg.cn/jnews/388366.htm
- http://m.wap.ghtkgg.cn/jnews/2089.htm
- http://m.wap.ghtkgg.cn/jnews/299485.htm
- http://m.wap.ghtkgg.cn/jnews/4442825.htm
- http://m.wap.ghtkgg.cn/jnews/525818.htm
- http://m.wap.ghtkgg.cn/jnews/8725.htm
- http://m.wap.ghtkgg.cn/jnews/2939.htm
- http://m.wap.ghtkgg.cn/jnews/60027.htm
- http://m.wap.ghtkgg.cn/jnews/347229.htm
- http://m.wap.ghtkgg.cn/jnews/7073586.htm
- http://m.wap.ghtkgg.cn/jnews/1162.htm
- http://m.wap.ghtkgg.cn/jnews/03178.htm
- http://m.wap.ghtkgg.cn/jnews/4889.htm
- http://m.wap.ghtkgg.cn/jnews/38055.htm
- http://m.wap.ghtkgg.cn/jnews/3295383.htm
- http://m.wap.ghtkgg.cn/jnews/2392191.htm
- http://m.wap.ghtkgg.cn/jnews/942945.htm
- http://m.wap.ghtkgg.cn/jnews/6851.htm
- http://m.wap.ghtkgg.cn/jnews/3133.htm
- http://m.wap.ghtkgg.cn/jnews/7404769.htm
- http://m.wap.ghtkgg.cn/jnews/252167.htm
- http://m.wap.ghtkgg.cn/jnews/8924143.htm
- http://m.wap.ghtkgg.cn/jnews/703786.htm
- http://m.wap.ghtkgg.cn/jnews/8006206.htm
- http://m.wap.ghtkgg.cn/jnews/5952434.htm
- http://m.wap.ghtkgg.cn/jnews/5879394.htm
- http://m.wap.ghtkgg.cn/jnews/78635.htm
- http://m.wap.ghtkgg.cn/jnews/1128.htm
- http://m.wap.ghtkgg.cn/jnews/8617.htm
- http://m.wap.ghtkgg.cn/jnews/64651.htm
- http://m.wap.ghtkgg.cn/jnews/83425.htm
- http://m.wap.ghtkgg.cn/jnews/9193590.htm
- http://m.wap.ghtkgg.cn/jnews/215126.htm
- http://m.wap.ghtkgg.cn/jnews/122370.htm
- http://m.wap.ghtkgg.cn/jnews/844020.htm
- http://m.wap.ghtkgg.cn/jnews/7062584.htm
- http://m.wap.ghtkgg.cn/jnews/8525.htm
- http://m.wap.ghtkgg.cn/jnews/43631.htm
- http://m.wap.ghtkgg.cn/jnews/2557862.htm
- http://m.wap.ghtkgg.cn/jnews/789077.htm
- http://m.wap.ghtkgg.cn/jnews/9463720.htm
- http://m.wap.ghtkgg.cn/jnews/9712201.htm
- http://m.wap.ghtkgg.cn/jnews/6524724.htm
- http://m.wap.ghtkgg.cn/jnews/64940.htm
- http://m.wap.ghtkgg.cn/jnews/940953.htm
- http://m.wap.ghtkgg.cn/jnews/64921.htm
- http://m.wap.ghtkgg.cn/jnews/5901.htm
- http://m.wap.ghtkgg.cn/jnews/276163.htm
- http://m.wap.ghtkgg.cn/jnews/605437.htm
- http://m.wap.ghtkgg.cn/jnews/5501.htm
- http://m.wap.ghtkgg.cn/jnews/31415.htm
- http://m.wap.ghtkgg.cn/jnews/3866175.htm
- http://m.wap.ghtkgg.cn/jnews/5647391.htm
- http://m.wap.ghtkgg.cn/jnews/0166181.htm
- http://m.wap.ghtkgg.cn/jnews/9665239.htm
- http://m.wap.ghtkgg.cn/jnews/9853163.htm
- http://m.wap.ghtkgg.cn/jnews/52270.htm
- http://m.wap.ghtkgg.cn/jnews/77161.htm
- http://m.wap.ghtkgg.cn/jnews/7973.htm
- http://m.wap.ghtkgg.cn/jnews/937095.htm
- http://m.wap.ghtkgg.cn/jnews/747828.htm
- http://m.wap.ghtkgg.cn/jnews/3481514.htm
- http://m.wap.ghtkgg.cn/jnews/67416.htm
- http://m.wap.ghtkgg.cn/jnews/154911.htm
- http://m.wap.ghtkgg.cn/jnews/23020.htm
- http://m.wap.ghtkgg.cn/jnews/7663963.htm
- http://m.wap.ghtkgg.cn/jnews/364364.htm
- http://m.wap.ghtkgg.cn/jnews/637848.htm
- http://m.wap.ghtkgg.cn/jnews/4786652.htm
- http://m.wap.ghtkgg.cn/jnews/145679.htm
- http://m.wap.ghtkgg.cn/jnews/494492.htm
- http://m.wap.ghtkgg.cn/jnews/91963.htm
- http://m.wap.ghtkgg.cn/jnews/5490.htm
- http://m.wap.ghtkgg.cn/jnews/1823537.htm
- http://m.wap.ghtkgg.cn/jnews/430929.htm
- http://m.wap.ghtkgg.cn/jnews/60611.htm
- http://m.wap.ghtkgg.cn/jnews/6836991.htm
- http://m.wap.ghtkgg.cn/jnews/4481987.htm
- http://m.wap.ghtkgg.cn/jnews/16961.htm
- http://m.wap.ghtkgg.cn/jnews/9794.htm
- http://m.wap.ghtkgg.cn/jnews/0325.htm
- http://m.wap.ghtkgg.cn/jnews/1783.htm
- http://m.wap.ghtkgg.cn/jnews/193549.htm
- http://m.wap.ghtkgg.cn/jnews/8920057.htm
- http://m.wap.ghtkgg.cn/jnews/6587371.htm
- http://m.wap.ghtkgg.cn/jnews/3152.htm
- http://m.wap.ghtkgg.cn/jnews/75292.htm
- http://m.wap.ghtkgg.cn/jnews/80765.htm
- http://m.wap.ghtkgg.cn/jnews/8533783.htm
- http://m.wap.ghtkgg.cn/jnews/17428.htm
- http://m.wap.ghtkgg.cn/jnews/0555970.htm
- http://m.wap.ghtkgg.cn/jnews/7525.htm
- http://m.wap.ghtkgg.cn/jnews/3507864.htm
- http://m.wap.ghtkgg.cn/jnews/449590.htm
- http://m.wap.ghtkgg.cn/jnews/7376.htm
- http://m.wap.ghtkgg.cn/jnews/91515.htm
- http://m.wap.ghtkgg.cn/jnews/8151964.htm
- http://m.wap.ghtkgg.cn/jnews/767943.htm
- http://m.wap.ghtkgg.cn/jnews/82001.htm
- http://m.wap.ghtkgg.cn/jnews/236905.htm
- http://m.wap.ghtkgg.cn/jnews/32517.htm
- http://m.wap.ghtkgg.cn/jnews/39941.htm
- http://m.wap.ghtkgg.cn/jnews/8647661.htm
- http://m.wap.ghtkgg.cn/jnews/32161.htm
- http://m.wap.ghtkgg.cn/jnews/39780.htm
- http://m.wap.ghtkgg.cn/jnews/50775.htm
- http://m.wap.ghtkgg.cn/jnews/12832.htm
- http://m.wap.ghtkgg.cn/jnews/029037.htm
- http://m.wap.ghtkgg.cn/jnews/211423.htm
- http://m.wap.ghtkgg.cn/jnews/045945.htm
- http://m.wap.ghtkgg.cn/jnews/792594.htm
- http://m.wap.ghtkgg.cn/jnews/0127.htm
- http://m.wap.ghtkgg.cn/jnews/0544436.htm
- http://m.wap.ghtkgg.cn/jnews/0332758.htm
- http://m.wap.ghtkgg.cn/jnews/6844346.htm
- http://m.wap.ghtkgg.cn/jnews/8001.htm
- http://m.wap.ghtkgg.cn/jnews/2574.htm
- http://m.wap.ghtkgg.cn/jnews/9108.htm
- http://m.wap.ghtkgg.cn/jnews/4741.htm
- http://m.wap.ghtkgg.cn/jnews/57311.htm
- http://m.wap.ghtkgg.cn/jnews/877841.htm
- http://m.wap.ghtkgg.cn/jnews/24683.htm
- http://m.wap.ghtkgg.cn/jnews/5254.htm
- http://m.wap.ghtkgg.cn/jnews/28247.htm
- http://m.wap.ghtkgg.cn/jnews/2318960.htm
- http://m.wap.ghtkgg.cn/jnews/6713.htm
- http://m.wap.ghtkgg.cn/jnews/971153.htm
- http://m.wap.ghtkgg.cn/jnews/85672.htm
- http://m.wap.ghtkgg.cn/jnews/733332.htm
- http://m.wap.ghtkgg.cn/jnews/02936.htm
- http://m.wap.ghtkgg.cn/jnews/90511.htm
- http://m.wap.ghtkgg.cn/jnews/61899.htm
- http://m.wap.ghtkgg.cn/jnews/2321.htm
- http://m.wap.ghtkgg.cn/jnews/285617.htm
- http://m.wap.ghtkgg.cn/jnews/4712.htm
- http://m.wap.ghtkgg.cn/jnews/9950.htm
- http://m.wap.ghtkgg.cn/jnews/0955.htm
- http://m.wap.ghtkgg.cn/jnews/352019.htm
- http://m.wap.ghtkgg.cn/jnews/37543.htm
- http://m.wap.ghtkgg.cn/jnews/950468.htm
- http://m.wap.ghtkgg.cn/jnews/6386.htm
- http://m.wap.ghtkgg.cn/jnews/38118.htm
- http://m.wap.ghtkgg.cn/jnews/163074.htm
- http://m.wap.ghtkgg.cn/jnews/7347.htm
- http://m.wap.ghtkgg.cn/jnews/8816168.htm
- http://m.wap.ghtkgg.cn/jnews/96615.htm
- http://m.wap.ghtkgg.cn/jnews/0567.htm
- http://m.wap.ghtkgg.cn/jnews/12962.htm
- http://m.wap.ghtkgg.cn/jnews/9547.htm
- http://m.wap.ghtkgg.cn/jnews/096998.htm
- http://m.wap.ghtkgg.cn/jnews/053475.htm
- http://m.wap.ghtkgg.cn/jnews/59791.htm
- http://m.wap.ghtkgg.cn/jnews/5419.htm
- http://m.wap.ghtkgg.cn/jnews/6004.htm
- http://m.wap.ghtkgg.cn/jnews/7110505.htm
- http://m.wap.ghtkgg.cn/jnews/800951.htm
- http://m.wap.ghtkgg.cn/jnews/26729.htm
- http://m.wap.ghtkgg.cn/jnews/6675793.htm
- http://m.wap.ghtkgg.cn/jnews/5277.htm
- http://m.wap.ghtkgg.cn/jnews/9922.htm
- http://m.wap.ghtkgg.cn/jnews/7935662.htm
- http://m.wap.ghtkgg.cn/jnews/3248.htm
- http://m.wap.ghtkgg.cn/jnews/95473.htm
- http://m.wap.ghtkgg.cn/jnews/7979.htm
- http://m.wap.ghtkgg.cn/jnews/0168894.htm
- http://m.wap.ghtkgg.cn/jnews/28385.htm
- http://m.wap.ghtkgg.cn/jnews/469110.htm
- http://m.wap.ghtkgg.cn/jnews/77927.htm
- http://m.wap.ghtkgg.cn/jnews/20477.htm
- http://m.wap.ghtkgg.cn/jnews/648412.htm
- http://m.wap.ghtkgg.cn/jnews/4879750.htm
- http://m.wap.ghtkgg.cn/jnews/45715.htm
- http://m.wap.ghtkgg.cn/jnews/665650.htm
- http://m.wap.ghtkgg.cn/jnews/7162.htm
- http://m.wap.ghtkgg.cn/jnews/794809.htm
- http://m.wap.ghtkgg.cn/jnews/129090.htm
- http://m.wap.ghtkgg.cn/jnews/57142.htm
- http://m.wap.ghtkgg.cn/jnews/9987762.htm
- http://m.wap.ghtkgg.cn/jnews/71908.htm
- http://m.wap.ghtkgg.cn/jnews/8205.htm
- http://m.wap.ghtkgg.cn/jnews/263392.htm
- http://m.wap.ghtkgg.cn/jnews/795038.htm
- http://m.wap.ghtkgg.cn/jnews/0050452.htm
- http://m.wap.ghtkgg.cn/jnews/8294.htm
- http://m.wap.ghtkgg.cn/jnews/1374126.htm
- http://m.wap.ghtkgg.cn/jnews/71545.htm
- http://m.wap.ghtkgg.cn/jnews/9558.htm
- http://m.wap.ghtkgg.cn/jnews/1343.htm
- http://m.wap.ghtkgg.cn/jnews/73544.htm
- http://m.wap.ghtkgg.cn/jnews/9319.htm
- http://m.wap.ghtkgg.cn/jnews/95282.htm
- http://m.wap.ghtkgg.cn/jnews/95811.htm
- http://m.wap.ghtkgg.cn/jnews/2103917.htm
- http://m.wap.ghtkgg.cn/jnews/40193.htm
- http://m.wap.ghtkgg.cn/jnews/44489.htm
- http://m.wap.ghtkgg.cn/jnews/93603.htm
- http://m.wap.ghtkgg.cn/jnews/9757.htm
- http://m.wap.ghtkgg.cn/jnews/53958.htm
- http://m.wap.ghtkgg.cn/jnews/7543.htm
- http://m.wap.ghtkgg.cn/jnews/1911427.htm
- http://m.wap.ghtkgg.cn/jnews/265699.htm
- http://m.wap.ghtkgg.cn/jnews/2716018.htm
- http://m.wap.ghtkgg.cn/jnews/50871.htm
- http://m.wap.ghtkgg.cn/jnews/22463.htm
- http://m.wap.ghtkgg.cn/jnews/729204.htm
- http://m.wap.ghtkgg.cn/jnews/29213.htm
- http://m.wap.ghtkgg.cn/jnews/05704.htm
- http://m.wap.ghtkgg.cn/jnews/901189.htm
- http://m.wap.ghtkgg.cn/jnews/7307.htm
- http://m.wap.ghtkgg.cn/jnews/9753083.htm
- http://m.wap.ghtkgg.cn/jnews/65290.htm
- http://m.wap.ghtkgg.cn/jnews/355862.htm
- http://m.wap.ghtkgg.cn/jnews/86354.htm
- http://m.wap.ghtkgg.cn/jnews/1057834.htm
- http://m.wap.ghtkgg.cn/jnews/32039.htm
- http://m.wap.ghtkgg.cn/jnews/10758.htm
- http://m.wap.ghtkgg.cn/jnews/6070.htm
- http://m.wap.ghtkgg.cn/jnews/9749908.htm

## 项目结构

项目采用分层架构设计，核心模块划分为数据访问层、业务逻辑层与表示层，同时包含独立的工具脚本与配置目录。

```
weblink-navigator/
├── app/                            # 主应用包
│   ├── __init__.py                 # 应用工厂函数与配置加载
│   ├── models/                     # 数据模型与 ORM 定义
│   │   ├── link.py                 # Link 实体模型，包含 URL、状态、标签关系等字段
│   │   ├── tag.py                  # 标签模型，支持层级父子结构
│   │   └── audit_log.py            # 审计日志模型，记录所有操作变更
│   ├── services/                   # 核心业务服务层
│   │   ├── checker.py              # 链接健康检测异步服务，包含并发请求与超时重试逻辑
│   │   ├── scheduler.py            # 定时任务调度服务，封装 APScheduler 配置与任务注册
│   │   └── exporter.py             # 数据导出服务，支持 JSON / XML / Markdown 格式生成
│   ├── routes/                     # Web 路由与 API 端点
│   │   ├── web.py                  # 管理界面路由，渲染模板与表单处理
│   │   └── api.py                  # RESTful API 端点，供外部系统调用
│   └── utils/                      # 通用工具函数
│       ├── http_client.py          # 异步 HTTP 客户端封装，含连接池与 SSL 配置
│       └── validators.py           # URL 格式校验与规范化工具
├── scripts/                        # 运维与开发辅助脚本
│   ├── init_db.py                  # 初始化 SQLite 数据库表结构与默认数据
│   └── import_links.py             # 批量导入链接的命令行脚本，支持 CSV / JSON
├── tests/                          # 单元测试与集成测试
│   ├── test_checker.py             # 健康检测服务测试用例
│   └── test_api.py                 # API 端点功能测试
├── docs/                           # 项目文档源文件
├── requirements.txt                # Python 依赖清单
├── .env.example                    # 环境变量配置模板
└── README.md                       # 项目说明文档
```

## 贡献指南

我们欢迎各类贡献，包括但不限于功能建议、缺陷报告、文档改进与代码提交。请遵循以下步骤参与项目。

提交 Issue 描述需求或缺陷：在 GitHub Issues 页面新建议题，使用提供的模板详细填写问题复现步骤、预期行为与实际行为，并标注相应的标签（bug / enhancement / question）。

Fork 仓库并创建特性分支：将主仓库 Fork 至个人账户，克隆本地后创建新的分支，分支命名规范为 feature/简述功能 或 fix/简述修复。

编写代码与对应单元测试：在实现新功能或修复缺陷时，请在 tests 目录下补充或更新相应的测试用例，确保测试覆盖率达到 80% 以上。

提交 Pull Request 并关联 Issue：推送分支至远程仓库后，在 GitHub 上创建 Pull Request，描述变更内容、测试结果以及关联的 Issue 编号。PR 至少需要一位维护者审核通过方可合并。

遵守代码风格与提交规范：Python 代码遵循 PEP 8 规范，提交信息采用约定式提交格式（type(scope): subject），类型包括 feat、fix、docs、style、refactor、test、chore。

## 常见问题

Q: 健康检测任务执行时出现大量超时或连接错误，应如何调整？

A: 此情况通常源于目标服务器响应缓慢或网络环境限制。可通过以下方式优化：在 .env 文件中调整 CHECKER_TIMEOUT 参数（默认 10 秒）增加超时阈值；降低 CHECKER_CONCURRENCY 参数（默认 50）减少并发请求数量，避免被目标服务器限流；若为生产环境，建议配置 Redis 作为任务队列后端，利用分布式调度分散检测压力。

Q: 如何将现有的链接列表从其他工具迁移至 WebLink Navigator？

A: 本项目提供了通用的导入接口。首先将原数据整理为 CSV 格式，其中必须包含 url 列，可选包含 title、tags（以分号分隔的标签字符串）与 note 列。然后使用 scripts/import_links.py 脚本执行导入，具体命令为 python scripts/import_links.py --file ./data.csv --format csv。对于 JSON 格式，可将格式参数改为 json 并确保键名与字段对应。

Q: 数据库从 SQLite 迁移到 PostgreSQL 需要额外进行哪些配置？

A: 项目使用 SQLAlchemy ORM，切换数据库仅需修改 .env 文件中的 DATABASE_URL 变量，将其从 sqlite:///weblink.db 改为 postgresql://user:password@host/dbname。同时需在 requirements.txt 中添加 psycopg2 或 asyncpg 驱动依赖，并执行 scripts/init_db.py 重新初始化表结构。注意原有 SQLite 数据需使用 pgloader 等工具进行迁移。

## 许可证

MIT License

Copyright (c) 2026 WebLink Navigator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:05
