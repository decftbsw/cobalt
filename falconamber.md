# WebLink Navigator

WebLink Navigator 是一个面向技术研究者和信息分析人员的高密度外链聚合与导航系统。该项目定位于对分散在互联网各处的深层页面进行结构化收集、分类存储与快速检索，帮助用户从海量零散 URL 中提炼出可复用、可追溯的信息资产。不同于传统的书签管理工具或简单的收藏夹同步方案，WebLink Navigator 将每条外链视为独立的数据条目，支持批量导入、自动去重、标签标注和全文本搜索，适用于需要长期跟踪特定领域信息源、构建个人或团队知识索引的场景。

目标用户包括渗透测试工程师、威胁情报分析师、数字取证专家、新闻聚合平台运营者以及需要从公开网络信息中提取关键线索的研究人员。系统不对 URL 可访问性做主动探测，仅提供本地化的存储、组织和检索能力，用户可自行结合第三方可用性监测服务进行链路健康检查。

## 功能概览

**批量外链导入与解析**：支持从纯文本、CSV 及结构化日志中批量提取 URL，自动识别路径层级与文件扩展名，并生成内部唯一标识符。

**分层标签管理体系**：允许用户为每条链接分配多级标签，支持标签继承、合并与批量替换，便于按主题、来源、时间或可信度维度组织资源。

**全文检索与高级过滤**：基于倒排索引实现毫秒级关键词匹配，支持按域名、路径前缀、文件类型、导入时间范围等条件组合过滤。

**重复链接检测与合并**：对完全相同或仅查询参数差异的 URL 进行自动聚类，提示用户合并重复条目，减少冗余存储。

**导入批次追踪**：记录每批次导入的来源、时间戳与条目数量，支持按批次回滚或导出，便于审计与溯源。

**数据导出与共享**：支持将选中的链接列表导出为纯文本、JSON 或 CSV 格式，方便迁移至其他分析工具或与协作者共享。

## 应用场景

**威胁情报线索归档**：安全研究人员在浏览各类安全公告、博客和漏洞数据库时，可将涉及 IOC 或 POC 的页面链接批量导入系统，按攻击组织、漏洞编号或时间线打标，形成可回溯的情报库。

**新闻事件溯源分析**：媒体监测人员在追踪突发新闻时，可将来自不同信源的报道链接集中存储，通过标签区分信源类型和报道角度，后续通过全文检索快速定位特定事件的相关报道。

**技术文档参考库构建**：开发者在阅读大量技术博客、API 文档和开源项目手册时，可将有价值的参考链接按技术栈、框架版本或问题领域分类保存，作为团队知识沉淀的基础数据层。

**合规审计链路备查**：法务或合规人员在对第三方内容进行引用时，可将引用链接统一入库，生成带时间戳的引用清单，便于后续接受审计或复核时快速调取原始出处。

## 快速开始

以下命令演示如何从 GitHub 克隆项目仓库、安装依赖并启动本地服务。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

启动后，访问本地 8000 端口即可进入 Web 管理界面。首次启动将自动创建 SQLite 数据库文件，如需使用 PostgreSQL 或 MySQL，请修改 settings.py 中的数据库配置。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 - 3.11 | 核心运行环境，3.12 及以上版本暂未经过充分测试 |
| Django | 4.2.x | Web 框架，用于提供管理界面和 REST API |
| SQLite | 3.35+ | 默认数据库，支持 WAL 模式以提升并发读取性能 |
| Whoosh | 2.7.4 | 全文检索引擎，用于实现标题和备注字段的快速搜索 |
| requests | 2.31.0 | 仅在导入时用于可选的头信息探测，非核心必需 |
| tqdm | 4.66.0 | 命令行导入时提供进度条显示，提升交互体验 |

生产环境建议额外部署 Redis 作为缓存后端，并配置 Nginx 或 Apache 作为反向代理。内存需求随导入条目数量线性增长，每 10 万条 URL 约占用 200MB 内存用于索引缓存。

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | /docs/quickstart.md | 如何快速安装并导入第一批链接，以及首次使用时的推荐工作流 |
| 操作手册 | /docs/user-guide.md | 每个功能页面的具体操作步骤，包括导入、打标、搜索和导出 |
| 管理指南 | /docs/admin-guide.md | 数据库迁移、备份恢复、性能调优和日常运维注意事项 |
| API 参考 | /docs/api-reference.md | 所有 RESTful 接口的请求参数、响应格式和错误码说明 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/5712187.htm
- http://m.3g.bwbkj.cn/jnews/0734.htm
- http://m.3g.bwbkj.cn/jnews/912701.htm
- http://m.3g.bwbkj.cn/jnews/4144.htm
- http://m.3g.bwbkj.cn/jnews/19152.htm
- http://m.3g.bwbkj.cn/jnews/262124.htm
- http://m.3g.bwbkj.cn/jnews/33812.htm
- http://m.3g.bwbkj.cn/jnews/8589639.htm
- http://m.3g.bwbkj.cn/jnews/4720.htm
- http://m.3g.bwbkj.cn/jnews/0840525.htm
- http://m.3g.bwbkj.cn/jnews/018340.htm
- http://m.3g.bwbkj.cn/jnews/826172.htm
- http://m.3g.bwbkj.cn/jnews/23070.htm
- http://m.3g.bwbkj.cn/jnews/311644.htm
- http://m.3g.bwbkj.cn/jnews/33456.htm
- http://m.3g.bwbkj.cn/jnews/9003762.htm
- http://m.3g.bwbkj.cn/jnews/40796.htm
- http://m.3g.bwbkj.cn/jnews/356339.htm
- http://m.3g.bwbkj.cn/jnews/129736.htm
- http://m.3g.bwbkj.cn/jnews/1906316.htm
- http://m.3g.bwbkj.cn/jnews/5628.htm
- http://m.3g.bwbkj.cn/jnews/211049.htm
- http://m.3g.bwbkj.cn/jnews/7254968.htm
- http://m.3g.bwbkj.cn/jnews/424900.htm
- http://m.3g.bwbkj.cn/jnews/3951648.htm
- http://m.3g.bwbkj.cn/jnews/30054.htm
- http://m.3g.bwbkj.cn/jnews/565343.htm
- http://m.3g.bwbkj.cn/jnews/6369.htm
- http://m.3g.bwbkj.cn/jnews/0173581.htm
- http://m.3g.bwbkj.cn/jnews/93088.htm
- http://m.3g.bwbkj.cn/jnews/0551.htm
- http://m.3g.bwbkj.cn/jnews/2059.htm
- http://m.3g.bwbkj.cn/jnews/24331.htm
- http://m.3g.bwbkj.cn/jnews/176056.htm
- http://m.3g.bwbkj.cn/jnews/68355.htm
- http://m.3g.bwbkj.cn/jnews/88584.htm
- http://m.3g.bwbkj.cn/jnews/77099.htm
- http://m.3g.bwbkj.cn/jnews/9718804.htm
- http://m.3g.bwbkj.cn/jnews/6914942.htm
- http://m.3g.bwbkj.cn/jnews/4850962.htm
- http://m.3g.bwbkj.cn/jnews/4336.htm
- http://m.3g.bwbkj.cn/jnews/0079348.htm
- http://m.3g.bwbkj.cn/jnews/2111563.htm
- http://m.3g.bwbkj.cn/jnews/0949.htm
- http://m.3g.bwbkj.cn/jnews/877229.htm
- http://m.3g.bwbkj.cn/jnews/8605657.htm
- http://m.3g.bwbkj.cn/jnews/33460.htm
- http://m.3g.bwbkj.cn/jnews/942870.htm
- http://m.3g.bwbkj.cn/jnews/828274.htm
- http://m.3g.bwbkj.cn/jnews/14996.htm
- http://m.3g.bwbkj.cn/jnews/38789.htm
- http://m.3g.bwbkj.cn/jnews/246792.htm
- http://m.3g.bwbkj.cn/jnews/611200.htm
- http://m.3g.bwbkj.cn/jnews/2876397.htm
- http://m.3g.bwbkj.cn/jnews/932563.htm
- http://m.3g.bwbkj.cn/jnews/0230973.htm
- http://m.3g.bwbkj.cn/jnews/1226.htm
- http://m.3g.bwbkj.cn/jnews/28712.htm
- http://m.3g.bwbkj.cn/jnews/13631.htm
- http://m.3g.bwbkj.cn/jnews/8127481.htm
- http://m.3g.bwbkj.cn/jnews/26874.htm
- http://m.3g.bwbkj.cn/jnews/1017.htm
- http://m.3g.bwbkj.cn/jnews/33817.htm
- http://m.3g.bwbkj.cn/jnews/2068945.htm
- http://m.3g.bwbkj.cn/jnews/64958.htm
- http://m.3g.bwbkj.cn/jnews/646076.htm
- http://m.3g.bwbkj.cn/jnews/9132.htm
- http://m.3g.bwbkj.cn/jnews/294835.htm
- http://m.3g.bwbkj.cn/jnews/1202068.htm
- http://m.3g.bwbkj.cn/jnews/4291.htm
- http://m.3g.bwbkj.cn/jnews/8258653.htm
- http://m.3g.bwbkj.cn/jnews/4523.htm
- http://m.3g.bwbkj.cn/jnews/8087.htm
- http://m.3g.bwbkj.cn/jnews/30714.htm
- http://m.3g.bwbkj.cn/jnews/0687.htm
- http://m.3g.bwbkj.cn/jnews/394605.htm
- http://m.3g.bwbkj.cn/jnews/7476.htm
- http://m.3g.bwbkj.cn/jnews/7800.htm
- http://m.3g.bwbkj.cn/jnews/548940.htm
- http://m.3g.bwbkj.cn/jnews/3601.htm
- http://m.3g.bwbkj.cn/jnews/49825.htm
- http://m.3g.bwbkj.cn/jnews/8302.htm
- http://m.3g.bwbkj.cn/jnews/93605.htm
- http://m.3g.bwbkj.cn/jnews/126543.htm
- http://m.3g.bwbkj.cn/jnews/6067.htm
- http://m.3g.bwbkj.cn/jnews/51824.htm
- http://m.3g.bwbkj.cn/jnews/80057.htm
- http://m.3g.bwbkj.cn/jnews/60444.htm
- http://m.3g.bwbkj.cn/jnews/004084.htm
- http://m.3g.bwbkj.cn/jnews/69019.htm
- http://m.3g.bwbkj.cn/jnews/127198.htm
- http://m.3g.bwbkj.cn/jnews/41432.htm
- http://m.3g.bwbkj.cn/jnews/6631426.htm
- http://m.3g.bwbkj.cn/jnews/4751560.htm
- http://m.3g.bwbkj.cn/jnews/7467244.htm
- http://m.3g.bwbkj.cn/jnews/28260.htm
- http://m.3g.bwbkj.cn/jnews/9563.htm
- http://m.3g.bwbkj.cn/jnews/8085.htm
- http://m.3g.bwbkj.cn/jnews/6241983.htm
- http://m.3g.bwbkj.cn/jnews/0009.htm
- http://m.3g.bwbkj.cn/jnews/2596.htm
- http://m.3g.bwbkj.cn/jnews/79594.htm
- http://m.3g.bwbkj.cn/jnews/8324.htm
- http://m.3g.bwbkj.cn/jnews/0118841.htm
- http://m.3g.bwbkj.cn/jnews/903403.htm
- http://m.3g.bwbkj.cn/jnews/65186.htm
- http://m.3g.bwbkj.cn/jnews/9191943.htm
- http://m.3g.bwbkj.cn/jnews/120279.htm
- http://m.3g.bwbkj.cn/jnews/806245.htm
- http://m.3g.bwbkj.cn/jnews/595441.htm
- http://m.3g.bwbkj.cn/jnews/22152.htm
- http://m.3g.bwbkj.cn/jnews/14574.htm
- http://m.3g.bwbkj.cn/jnews/5191063.htm
- http://m.3g.bwbkj.cn/jnews/6635042.htm
- http://m.3g.bwbkj.cn/jnews/808300.htm
- http://m.3g.bwbkj.cn/jnews/16359.htm
- http://m.3g.bwbkj.cn/jnews/35727.htm
- http://m.3g.bwbkj.cn/jnews/884749.htm
- http://m.3g.bwbkj.cn/jnews/11147.htm
- http://m.3g.bwbkj.cn/jnews/9569.htm
- http://m.3g.bwbkj.cn/jnews/38920.htm
- http://m.3g.bwbkj.cn/jnews/121525.htm
- http://m.3g.bwbkj.cn/jnews/2299.htm
- http://m.3g.bwbkj.cn/jnews/3809262.htm
- http://m.3g.bwbkj.cn/jnews/87298.htm
- http://m.3g.bwbkj.cn/jnews/186095.htm
- http://m.3g.bwbkj.cn/jnews/489960.htm
- http://m.3g.bwbkj.cn/jnews/993298.htm
- http://m.3g.bwbkj.cn/jnews/55414.htm
- http://m.3g.bwbkj.cn/jnews/66441.htm
- http://m.3g.bwbkj.cn/jnews/3779124.htm
- http://m.3g.bwbkj.cn/jnews/7595.htm
- http://m.3g.bwbkj.cn/jnews/0779.htm
- http://m.3g.bwbkj.cn/jnews/435232.htm
- http://m.3g.bwbkj.cn/jnews/4324439.htm
- http://m.3g.bwbkj.cn/jnews/821470.htm
- http://m.3g.bwbkj.cn/jnews/4793071.htm
- http://m.3g.bwbkj.cn/jnews/9803576.htm
- http://m.3g.bwbkj.cn/jnews/29663.htm
- http://m.3g.bwbkj.cn/jnews/3174200.htm
- http://m.3g.bwbkj.cn/jnews/032439.htm
- http://m.3g.bwbkj.cn/jnews/0987.htm
- http://m.3g.bwbkj.cn/jnews/605786.htm
- http://m.3g.bwbkj.cn/jnews/9879.htm
- http://m.3g.bwbkj.cn/jnews/3325539.htm
- http://m.3g.bwbkj.cn/jnews/8740.htm
- http://m.3g.bwbkj.cn/jnews/05941.htm
- http://m.3g.bwbkj.cn/jnews/765910.htm
- http://m.3g.bwbkj.cn/jnews/87862.htm
- http://m.3g.bwbkj.cn/jnews/0694.htm
- http://m.3g.bwbkj.cn/jnews/6089.htm
- http://m.3g.bwbkj.cn/jnews/188139.htm
- http://m.3g.bwbkj.cn/jnews/809254.htm
- http://m.3g.bwbkj.cn/jnews/50997.htm
- http://m.3g.bwbkj.cn/jnews/7165.htm
- http://m.3g.bwbkj.cn/jnews/991870.htm
- http://m.3g.bwbkj.cn/jnews/60790.htm
- http://m.3g.bwbkj.cn/jnews/2935101.htm
- http://m.3g.bwbkj.cn/jnews/80915.htm
- http://m.3g.bwbkj.cn/jnews/416955.htm
- http://m.3g.bwbkj.cn/jnews/91175.htm
- http://m.3g.bwbkj.cn/jnews/3156.htm
- http://m.3g.bwbkj.cn/jnews/2359.htm
- http://m.3g.bwbkj.cn/jnews/4460748.htm
- http://m.3g.bwbkj.cn/jnews/7591129.htm
- http://m.3g.bwbkj.cn/jnews/45037.htm
- http://m.3g.bwbkj.cn/jnews/1432.htm
- http://m.3g.bwbkj.cn/jnews/938750.htm
- http://m.3g.bwbkj.cn/jnews/87509.htm
- http://m.3g.bwbkj.cn/jnews/8902474.htm
- http://m.3g.bwbkj.cn/jnews/40298.htm
- http://m.3g.bwbkj.cn/jnews/8950.htm
- http://m.3g.bwbkj.cn/jnews/3433687.htm
- http://m.3g.bwbkj.cn/jnews/88918.htm
- http://m.3g.bwbkj.cn/jnews/219788.htm
- http://m.3g.bwbkj.cn/jnews/4636605.htm
- http://m.3g.bwbkj.cn/jnews/70134.htm
- http://m.3g.bwbkj.cn/jnews/977791.htm
- http://m.3g.bwbkj.cn/jnews/002842.htm
- http://m.3g.bwbkj.cn/jnews/308844.htm
- http://m.3g.bwbkj.cn/jnews/7614461.htm
- http://m.3g.bwbkj.cn/jnews/1043383.htm
- http://m.3g.bwbkj.cn/jnews/53960.htm
- http://m.3g.bwbkj.cn/jnews/8433499.htm
- http://m.3g.bwbkj.cn/jnews/8625.htm
- http://m.3g.bwbkj.cn/jnews/625240.htm
- http://m.3g.bwbkj.cn/jnews/939184.htm
- http://m.3g.bwbkj.cn/jnews/35434.htm
- http://m.3g.bwbkj.cn/jnews/954334.htm
- http://m.3g.bwbkj.cn/jnews/44712.htm
- http://m.3g.bwbkj.cn/jnews/736252.htm
- http://m.3g.bwbkj.cn/jnews/48028.htm
- http://m.3g.bwbkj.cn/jnews/704004.htm
- http://m.3g.bwbkj.cn/jnews/3683.htm
- http://m.3g.bwbkj.cn/jnews/4962238.htm
- http://m.3g.bwbkj.cn/jnews/7887469.htm
- http://m.3g.bwbkj.cn/jnews/10295.htm
- http://m.3g.bwbkj.cn/jnews/0777.htm
- http://m.3g.bwbkj.cn/jnews/5440960.htm
- http://m.3g.bwbkj.cn/jnews/08801.htm
- http://m.3g.bwbkj.cn/jnews/50475.htm
- http://m.3g.bwbkj.cn/jnews/376056.htm
- http://m.3g.bwbkj.cn/jnews/53831.htm
- http://m.3g.bwbkj.cn/jnews/021437.htm
- http://m.3g.bwbkj.cn/jnews/57397.htm
- http://m.3g.bwbkj.cn/jnews/5534.htm
- http://m.3g.bwbkj.cn/jnews/931842.htm
- http://m.3g.bwbkj.cn/jnews/6731476.htm
- http://m.3g.bwbkj.cn/jnews/9241.htm
- http://m.3g.bwbkj.cn/jnews/06801.htm
- http://m.3g.bwbkj.cn/jnews/0124467.htm
- http://m.3g.bwbkj.cn/jnews/5311.htm
- http://m.3g.bwbkj.cn/jnews/01161.htm
- http://m.3g.bwbkj.cn/jnews/7171312.htm
- http://m.3g.bwbkj.cn/jnews/194964.htm
- http://m.3g.bwbkj.cn/jnews/866260.htm
- http://m.3g.bwbkj.cn/jnews/09445.htm
- http://m.3g.bwbkj.cn/jnews/2253.htm
- http://m.3g.bwbkj.cn/jnews/7166.htm
- http://m.3g.bwbkj.cn/jnews/61742.htm
- http://m.3g.bwbkj.cn/jnews/763499.htm
- http://m.3g.bwbkj.cn/jnews/83470.htm
- http://m.3g.bwbkj.cn/jnews/8914614.htm
- http://m.3g.bwbkj.cn/jnews/3672.htm
- http://m.3g.bwbkj.cn/jnews/08468.htm
- http://m.3g.bwbkj.cn/jnews/5863.htm
- http://m.3g.bwbkj.cn/jnews/7365699.htm
- http://m.3g.bwbkj.cn/jnews/5113.htm
- http://m.3g.bwbkj.cn/jnews/0670618.htm
- http://m.3g.bwbkj.cn/jnews/516084.htm
- http://m.3g.bwbkj.cn/jnews/5627072.htm
- http://m.3g.bwbkj.cn/jnews/9495.htm
- http://m.3g.bwbkj.cn/jnews/5807308.htm
- http://m.3g.bwbkj.cn/jnews/8995.htm
- http://m.3g.bwbkj.cn/jnews/731175.htm
- http://m.3g.bwbkj.cn/jnews/36698.htm
- http://m.3g.bwbkj.cn/jnews/71134.htm
- http://m.3g.bwbkj.cn/jnews/43432.htm
- http://m.3g.bwbkj.cn/jnews/834686.htm
- http://m.3g.bwbkj.cn/jnews/7718.htm
- http://m.3g.bwbkj.cn/jnews/0770574.htm
- http://m.3g.bwbkj.cn/jnews/9240474.htm
- http://m.3g.bwbkj.cn/jnews/3666897.htm
- http://m.3g.bwbkj.cn/jnews/5146591.htm
- http://m.3g.bwbkj.cn/jnews/9198038.htm
- http://m.3g.bwbkj.cn/jnews/56815.htm
- http://m.3g.bwbkj.cn/jnews/37673.htm
- http://m.3g.bwbkj.cn/jnews/275256.htm
- http://m.3g.bwbkj.cn/jnews/986335.htm
- http://m.3g.bwbkj.cn/jnews/6561788.htm
- http://m.3g.bwbkj.cn/jnews/6694.htm
- http://m.3g.bwbkj.cn/jnews/8599.htm
- http://m.3g.bwbkj.cn/jnews/804652.htm
- http://m.3g.bwbkj.cn/jnews/3374.htm
- http://m.3g.bwbkj.cn/jnews/7931.htm
- http://m.3g.bwbkj.cn/jnews/1996.htm
- http://m.3g.bwbkj.cn/jnews/6506.htm
- http://m.3g.bwbkj.cn/jnews/05337.htm
- http://m.3g.bwbkj.cn/jnews/2510974.htm
- http://m.3g.bwbkj.cn/jnews/71483.htm
- http://m.3g.bwbkj.cn/jnews/64543.htm
- http://m.3g.bwbkj.cn/jnews/709695.htm
- http://m.3g.bwbkj.cn/jnews/0939479.htm
- http://m.3g.bwbkj.cn/jnews/4327.htm
- http://m.3g.bwbkj.cn/jnews/3987302.htm
- http://m.3g.bwbkj.cn/jnews/7449.htm
- http://m.3g.bwbkj.cn/jnews/486359.htm
- http://m.3g.bwbkj.cn/jnews/2669634.htm
- http://m.3g.bwbkj.cn/jnews/175977.htm
- http://m.3g.bwbkj.cn/jnews/42770.htm
- http://m.3g.bwbkj.cn/jnews/1530374.htm
- http://m.3g.bwbkj.cn/jnews/00555.htm
- http://m.3g.bwbkj.cn/jnews/9008457.htm
- http://m.3g.bwbkj.cn/jnews/3223.htm
- http://m.3g.bwbkj.cn/jnews/665164.htm
- http://m.3g.bwbkj.cn/jnews/61264.htm
- http://m.3g.bwbkj.cn/jnews/04895.htm
- http://m.3g.bwbkj.cn/jnews/4540.htm
- http://m.3g.bwbkj.cn/jnews/8232426.htm
- http://m.3g.bwbkj.cn/jnews/36016.htm
- http://m.3g.bwbkj.cn/jnews/12815.htm
- http://m.3g.bwbkj.cn/jnews/847373.htm
- http://m.3g.bwbkj.cn/jnews/094626.htm
- http://m.3g.bwbkj.cn/jnews/875389.htm
- http://m.3g.bwbkj.cn/jnews/78857.htm
- http://m.3g.bwbkj.cn/jnews/26684.htm
- http://m.3g.bwbkj.cn/jnews/991139.htm
- http://m.3g.bwbkj.cn/jnews/0709348.htm
- http://m.3g.bwbkj.cn/jnews/7825563.htm
- http://m.3g.bwbkj.cn/jnews/5841.htm
- http://m.3g.bwbkj.cn/jnews/5507515.htm
- http://m.3g.bwbkj.cn/jnews/323633.htm
- http://m.3g.bwbkj.cn/jnews/1505.htm
- http://m.3g.bwbkj.cn/jnews/694612.htm
- http://m.3g.bwbkj.cn/jnews/59621.htm
- http://m.3g.bwbkj.cn/jnews/97047.htm
- http://m.3g.bwbkj.cn/jnews/0718.htm
- http://m.3g.bwbkj.cn/jnews/740952.htm
- http://m.3g.bwbkj.cn/jnews/427826.htm
- http://m.3g.bwbkj.cn/jnews/405167.htm

## 项目结构

```
weblink-navigator/
├── manage.py                      # Django 项目管理入口，用于执行迁移、运行服务等操作
├── requirements.txt               # Python 依赖清单，包含 Django、Whoosh 等核心库
├── config/                        # 项目全局配置目录
│   ├── settings.py                # 主配置文件，包含数据库、中间件、静态文件等设置
│   ├── urls.py                    # 根路由映射，将 API 和管理界面请求分发至对应应用
│   └── wsgi.py                    # WSGI 网关配置，用于生产环境部署
├── apps/                          # 所有功能模块存放目录
│   ├── core/                      # 核心数据模型与通用工具函数
│   │   ├── models.py              # Link、Tag、Batch 等主要数据表定义
│   │   ├── utils.py               # URL 解析、去重算法、日期格式化等辅助函数
│   │   └── validators.py          # 自定义字段校验器，如 URL 格式与长度验证
│   ├── importer/                  # 批量导入模块，支持多种输入格式
│   │   ├── parsers.py             # TXT、CSV、JSON 格式解析器实现
│   │   ├── handlers.py            # 解析后数据入库的处理逻辑与事务管理
│   │   └── tasks.py               # 后台异步导入任务定义（Celery 可选）
│   ├── search/                    # 全文检索模块，基于 Whoosh 实现
│   │   ├── indexer.py             # 索引创建、更新与删除操作
│   │   ├── queries.py             # 查询构建器，支持分词、模糊匹配与过滤
│   │   └── schema.py              # 索引字段定义，包括标题、备注、域名等
│   ├── api/                       # RESTful API 接口层，供前端或外部调用
│   │   ├── views.py               # 所有 API 视图函数，处理请求与响应序列化
│   │   ├── serializers.py         # 模型序列化器，定义输出字段与校验规则
│   │   └── routers.py             # 自动路由注册，生成标准 DRF 路由表
│   └── web/                       # Web 管理界面，提供可视化操作面板
│       ├── views.py               # 页面渲染视图，返回 HTML 模板
│       ├── templates/             # Django 模板文件目录
│       │   ├── base.html          # 基础布局模板，包含导航栏和全局样式
│       │   ├── index.html         # 首页仪表板，显示统计概览与最近导入
│       │   └── detail.html        # 单条链接详情页，展示完整元数据
│       └── static/                # 静态资源文件（CSS、JavaScript、图片）
├── data/                          # 数据存储目录（默认 SQLite 数据库和 Whoosh 索引）
│   ├── db.sqlite3                 # 默认 SQLite 数据库文件，包含所有表结构及记录
│   └── whoosh_index/              # Whoosh 全文索引文件目录，用于快速文本检索
├── tests/                         # 单元测试与集成测试用例目录
│   ├── test_models.py             # 数据模型层测试，验证 CRUD 操作与约束条件
│   ├── test_import.py             # 导入功能测试，覆盖正常与异常输入场景
│   └── test_search.py             # 检索功能测试，验证分词准确性与查询性能
└── docs/                          # 项目文档源文件，采用 Markdown 格式编写
    ├── quickstart.md              # 快速入门指南，帮助新用户在 5 分钟内完成部署
    ├── user-guide.md              # 完整用户手册，逐项说明所有界面操作
    ├── admin-guide.md             # 系统管理员手册，涵盖备份、迁移和监控
    └── api-reference.md           # API 接口完整参考文档，含示例请求与响应
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库，并克隆到本地开发环境。建议在 dev 分支上创建新的功能分支，命名格式为 feature/功能简述 或 fix/问题描述。

2. 按照项目根目录下的 development.md 文件配置本地开发环境，确保所有依赖安装完整，并运行预置的测试套件确认基础环境无异常。

3. 进行代码修改或新增功能时，请遵循 PEP 8 编码规范，并为新增的类、函数和方法添加完整的 docstring 注释。涉及数据模型变更时，需要同时编写对应的迁移脚本。

4. 提交前执行 ruff 或 flake8 进行静态检查，并补充相应的单元测试用例，确保测试覆盖率达到 90% 以上。提交信息请采用常规提交格式，即 type(scope): subject 的形式。

5. 发起 Pull Request 至主仓库的 main 分支，并在描述中清晰说明修改目的、涉及的问题编号以及测试验证情况。项目维护者将在 7 个工作日内进行审查。

## 常见问题

**Q：导入超过 1 万条 URL 时页面响应变慢，应如何优化？**

A：当条目数量较大时，建议使用命令行导入工具而非 Web 界面上传，命令行模式会绕过界面渲染开销并启用批量提交。同时可以在 settings.py 中启用数据库连接池，并将 Whoosh 索引的 commit 间隔从默认的 10 条调整为 500 条。若仍无法满足需求，可考虑迁移至 PostgreSQL 并配置合适的 work_mem 参数。

**Q：系统是否支持自动检测外链是否可访问或内容是否变更？**

A：当前版本不包含主动探测功能，因为频繁对外发起 HTTP 请求可能违反目标站点的使用策略，且对大量链接进行实时检测会显著增加服务器负载。建议用户定期手动抽查，或结合外部监控服务（如 uptimerobot 或自定义脚本）实现链路健康检查，然后将结果作为标签或备注手动录入系统。

**Q：如何在不同设备之间同步数据？**

A：WebLink Navigator 采用单机架构，数据文件默认存储于本地磁盘。若需跨设备同步，可将 data/ 目录和 whoosh_index/ 目录置于云存储同步文件夹（如 Dropbox、Nextcloud）中，或使用 Git LFS 进行版本管理。团队协作场景建议将数据库迁移至共享网络存储或云数据库服务，并配置 Django 的跨域设置以允许多实例访问。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:05
