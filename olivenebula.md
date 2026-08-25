# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与外部资源索引的开源工具，专为需要批量管理、分类展示和快速检索分散式新闻链接的开发者与内容运营团队设计。该项目不依赖任何商业 API，完全基于静态链接的元数据提取与本地索引构建，能够将大量无序的 URL 转化为可查询、可分类、可版本控制的结构化知识库。

本项目的目标用户包括技术博客作者、开源社区维护者、数据调研人员以及任何需要长期跟踪大量信息源但不愿被封闭平台绑定的个体。通过 NewsLink Aggregator，用户可以在本地环境中对海量外部链接进行抓取、标注、标签化存储和全文检索，从而摆脱对第三方书签服务或云笔记的依赖。

## 功能概览

链接元数据提取：自动从目标 URL 的 HTML 页面中提取标题、meta 描述、关键词、发布时间和正文前 200 字符，无需人工录入。

批量导入与去重：支持从纯文本列表、CSV 文件或 OPML 订阅源批量导入链接，内置基于 URL 结构和内容哈希的双重去重机制。

标签与分类管理：允许用户为每条链接添加自定义标签（如“AI”、“后端”、“运维”），并支持按标签组合进行快速筛选。

全文检索与高亮：基于 SQLite FTS5 扩展提供中文分词与全文搜索能力，搜索结果中自动高亮匹配关键词。

本地 Web 仪表盘：提供一个轻量级 Flask Web 界面，用于浏览、搜索、编辑和删除已收录的链接，支持响应式布局。

定时更新检测：对已收录的链接可配置每日或每周的更新检查任务，若目标页面发生变化则自动标记并推送通知（支持邮件和 Webhook）。

数据导出与迁移：支持将全部链接数据导出为 JSON、CSV 或 Markdown 表格格式，便于备份或迁移至其他系统。

## 应用场景

技术团队内部知识库构建：技术团队可以使用本工具将日常阅读的行业新闻、技术博客、故障报告等外部链接统一归档，并添加内部评级和备注，逐步形成团队共享的知识资产。

开源项目文档外链管理：开源项目的维护者可以在项目仓库的 docs 目录下维护一个 links.md 文件，通过本工具生成结构化的外链列表，并自动检查链接有效性，避免文档中出现死链。

个人信息流离线聚合：个人开发者可以定期从 Feedly、Twitter 或邮件订阅中提取感兴趣的文章链接，导入本工具后通过本地搜索功能快速回溯历史内容，无需反复访问原始站点。

运营活动素材整理：内容运营人员可以针对不同主题（如产品发布、技术大会、节日营销）建立独立的链接集合，利用标签和备注功能记录素材来源、使用状态和版权信息。

数据调研与竞品监测：市场分析人员可以批量导入竞品官方公告、媒体报道和用户反馈链接，通过定时更新检测功能关注动态变化，辅助决策分析。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整过程。请确保系统已安装 Python 3.9 及以上版本和 Git。

```bash
git clone https://github.com/your-org/newslink-aggregator.git
cd newslink-aggregator
python -m venv venv
source venv/bin/activate  # Windows 系统请使用 venv\Scripts\activate
pip install -r requirements.txt
flask db upgrade
flask run --host=0.0.0.0 --port=5000
```

启动成功后，打开浏览器访问 http://localhost:5000 即可进入仪表盘。首次启动会自动创建 SQLite 数据库文件 instance/links.db 并生成默认管理员账户（用户名 admin，密码 changeme，请在首次登录后修改）。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 - 3.12 | 核心运行环境，低于 3.9 版本将无法使用类型注解和 f-string 特性 |
| SQLite | 3.35.0 以上 | 数据库引擎，需支持 FTS5 扩展以提供中文全文检索功能 |
| Flask | 2.3.x | Web 框架，用于提供仪表盘界面和 REST API 接口 |
| requests | 2.31.x | HTTP 客户端，负责发送链接抓取请求，支持重试和超时控制 |
| beautifulsoup4 | 4.12.x | HTML 解析库，用于提取页面标题、描述和正文内容 |
| lxml | 4.9.x | 作为 beautifulsoup4 的解析后端，提供更高效的 HTML 和 XML 解析能力 |
| pytest | 7.4.x | 单元测试框架（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/quickstart.md | 如何从零开始安装、配置并首次运行本项目？如何导入第一批链接？ |
| 核心配置 | docs/configuration.md | 环境变量有哪些？如何修改定时更新频率、邮件通知参数和 Webhook 地址？ |
| 命令行工具 | docs/cli.md | 如何在不启动 Web 服务的情况下执行批量导入、导出、去重和更新检测？ |
| API 参考 | docs/api.md | 如何通过 REST API 进行第三方集成？请求格式、返回字段和状态码分别是什么？ |
| 部署手册 | docs/deployment.md | 如何将其部署到生产环境（Nginx + Gunicorn / Docker）？如何处理高并发请求？ |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/8570.htm
- http://m.3g.ghtkgg.cn/nnews/848979.htm
- http://m.3g.ghtkgg.cn/nnews/1199.htm
- http://m.3g.ghtkgg.cn/nnews/8293.htm
- http://m.3g.ghtkgg.cn/nnews/20853.htm
- http://m.3g.ghtkgg.cn/nnews/6621343.htm
- http://m.3g.ghtkgg.cn/nnews/6853559.htm
- http://m.3g.ghtkgg.cn/nnews/1154.htm
- http://m.3g.ghtkgg.cn/nnews/9053659.htm
- http://m.3g.ghtkgg.cn/nnews/8486009.htm
- http://m.3g.ghtkgg.cn/nnews/685706.htm
- http://m.3g.ghtkgg.cn/nnews/9223.htm
- http://m.3g.ghtkgg.cn/nnews/2614171.htm
- http://m.3g.ghtkgg.cn/nnews/8137743.htm
- http://m.3g.ghtkgg.cn/nnews/843575.htm
- http://m.3g.ghtkgg.cn/nnews/232957.htm
- http://m.3g.ghtkgg.cn/nnews/4994201.htm
- http://m.3g.ghtkgg.cn/nnews/518535.htm
- http://m.3g.ghtkgg.cn/nnews/7951994.htm
- http://m.3g.ghtkgg.cn/nnews/27037.htm
- http://m.3g.ghtkgg.cn/nnews/8323313.htm
- http://m.3g.ghtkgg.cn/nnews/917669.htm
- http://m.3g.ghtkgg.cn/nnews/903118.htm
- http://m.3g.ghtkgg.cn/nnews/9483280.htm
- http://m.3g.ghtkgg.cn/nnews/920556.htm
- http://m.3g.ghtkgg.cn/nnews/5646.htm
- http://m.3g.ghtkgg.cn/nnews/44307.htm
- http://m.3g.ghtkgg.cn/nnews/19460.htm
- http://m.3g.ghtkgg.cn/nnews/17146.htm
- http://m.3g.ghtkgg.cn/nnews/8929.htm
- http://m.3g.ghtkgg.cn/nnews/6194865.htm
- http://m.3g.ghtkgg.cn/nnews/8292.htm
- http://m.3g.ghtkgg.cn/nnews/42148.htm
- http://m.3g.ghtkgg.cn/nnews/8339.htm
- http://m.3g.ghtkgg.cn/nnews/592009.htm
- http://m.3g.ghtkgg.cn/nnews/94941.htm
- http://m.3g.ghtkgg.cn/nnews/7686.htm
- http://m.3g.ghtkgg.cn/nnews/8763.htm
- http://m.3g.ghtkgg.cn/nnews/13439.htm
- http://m.3g.ghtkgg.cn/nnews/2803.htm
- http://m.3g.ghtkgg.cn/nnews/652175.htm
- http://m.3g.ghtkgg.cn/nnews/2451821.htm
- http://m.3g.ghtkgg.cn/nnews/632435.htm
- http://m.3g.ghtkgg.cn/nnews/6101827.htm
- http://m.3g.ghtkgg.cn/nnews/1700.htm
- http://m.3g.ghtkgg.cn/nnews/5022588.htm
- http://m.3g.ghtkgg.cn/nnews/9838.htm
- http://m.3g.ghtkgg.cn/nnews/494255.htm
- http://m.3g.ghtkgg.cn/nnews/57196.htm
- http://m.3g.ghtkgg.cn/nnews/9418811.htm
- http://m.3g.ghtkgg.cn/nnews/3721670.htm
- http://m.3g.ghtkgg.cn/nnews/205960.htm
- http://m.3g.ghtkgg.cn/nnews/445381.htm
- http://m.3g.ghtkgg.cn/nnews/3980550.htm
- http://m.3g.ghtkgg.cn/nnews/1570.htm
- http://m.3g.ghtkgg.cn/nnews/26533.htm
- http://m.3g.ghtkgg.cn/nnews/48044.htm
- http://m.3g.ghtkgg.cn/nnews/3465523.htm
- http://m.3g.ghtkgg.cn/nnews/38716.htm
- http://m.3g.ghtkgg.cn/nnews/9894.htm
- http://m.3g.ghtkgg.cn/nnews/7461.htm
- http://m.3g.ghtkgg.cn/nnews/69361.htm
- http://m.3g.ghtkgg.cn/nnews/9704.htm
- http://m.3g.ghtkgg.cn/nnews/12505.htm
- http://m.3g.ghtkgg.cn/nnews/597941.htm
- http://m.3g.ghtkgg.cn/nnews/6237276.htm
- http://m.3g.ghtkgg.cn/nnews/75895.htm
- http://m.3g.ghtkgg.cn/nnews/4072.htm
- http://m.3g.ghtkgg.cn/nnews/7999171.htm
- http://m.3g.ghtkgg.cn/nnews/880440.htm
- http://m.3g.ghtkgg.cn/nnews/9284.htm
- http://m.3g.ghtkgg.cn/nnews/61605.htm
- http://m.3g.ghtkgg.cn/nnews/0052.htm
- http://m.3g.ghtkgg.cn/nnews/284104.htm
- http://m.3g.ghtkgg.cn/nnews/319812.htm
- http://m.3g.ghtkgg.cn/nnews/488880.htm
- http://m.3g.ghtkgg.cn/nnews/589674.htm
- http://m.3g.ghtkgg.cn/nnews/52413.htm
- http://m.3g.ghtkgg.cn/nnews/7844431.htm
- http://m.3g.ghtkgg.cn/nnews/103042.htm
- http://m.3g.ghtkgg.cn/nnews/9473780.htm
- http://m.3g.ghtkgg.cn/nnews/5802253.htm
- http://m.3g.ghtkgg.cn/nnews/1460983.htm
- http://m.3g.ghtkgg.cn/nnews/3769087.htm
- http://m.3g.ghtkgg.cn/nnews/6110291.htm
- http://m.3g.ghtkgg.cn/nnews/5112.htm
- http://m.3g.ghtkgg.cn/nnews/3302022.htm
- http://m.3g.ghtkgg.cn/nnews/503113.htm
- http://m.3g.ghtkgg.cn/nnews/909972.htm
- http://m.3g.ghtkgg.cn/nnews/416197.htm
- http://m.3g.ghtkgg.cn/nnews/364666.htm
- http://m.3g.ghtkgg.cn/nnews/6689434.htm
- http://m.3g.ghtkgg.cn/nnews/5227573.htm
- http://m.3g.ghtkgg.cn/nnews/5782361.htm
- http://m.3g.ghtkgg.cn/nnews/546535.htm
- http://m.3g.ghtkgg.cn/nnews/3936.htm
- http://m.3g.ghtkgg.cn/nnews/582309.htm
- http://m.3g.ghtkgg.cn/nnews/3739.htm
- http://m.3g.ghtkgg.cn/nnews/75122.htm
- http://m.3g.ghtkgg.cn/nnews/4928221.htm
- http://m.3g.ghtkgg.cn/nnews/597155.htm
- http://m.3g.ghtkgg.cn/nnews/988707.htm
- http://m.3g.ghtkgg.cn/nnews/4022068.htm
- http://m.3g.ghtkgg.cn/nnews/813080.htm
- http://m.3g.ghtkgg.cn/nnews/566399.htm
- http://m.3g.ghtkgg.cn/nnews/1446987.htm
- http://m.3g.ghtkgg.cn/nnews/8983.htm
- http://m.3g.ghtkgg.cn/nnews/6358960.htm
- http://m.3g.ghtkgg.cn/nnews/9057.htm
- http://m.3g.ghtkgg.cn/nnews/8213616.htm
- http://m.3g.ghtkgg.cn/nnews/8882509.htm
- http://m.3g.ghtkgg.cn/nnews/7508.htm
- http://m.3g.ghtkgg.cn/nnews/46400.htm
- http://m.3g.ghtkgg.cn/nnews/3088814.htm
- http://m.3g.ghtkgg.cn/nnews/1530.htm
- http://m.3g.ghtkgg.cn/nnews/297409.htm
- http://m.3g.ghtkgg.cn/nnews/1335899.htm
- http://m.3g.ghtkgg.cn/nnews/18723.htm
- http://m.3g.ghtkgg.cn/nnews/4533.htm
- http://m.3g.ghtkgg.cn/nnews/67175.htm
- http://m.3g.ghtkgg.cn/nnews/287812.htm
- http://m.3g.ghtkgg.cn/nnews/54906.htm
- http://m.3g.ghtkgg.cn/nnews/74748.htm
- http://m.3g.ghtkgg.cn/nnews/5162788.htm
- http://m.3g.ghtkgg.cn/nnews/22106.htm
- http://m.3g.ghtkgg.cn/nnews/1597.htm
- http://m.3g.ghtkgg.cn/nnews/9186.htm
- http://m.3g.ghtkgg.cn/nnews/7302081.htm
- http://m.3g.ghtkgg.cn/nnews/8076.htm
- http://m.3g.ghtkgg.cn/nnews/31809.htm
- http://m.3g.ghtkgg.cn/nnews/179808.htm
- http://m.3g.ghtkgg.cn/nnews/9897806.htm
- http://m.3g.ghtkgg.cn/nnews/92295.htm
- http://m.3g.ghtkgg.cn/nnews/3715.htm
- http://m.3g.ghtkgg.cn/nnews/2513329.htm
- http://m.3g.ghtkgg.cn/nnews/604773.htm
- http://m.3g.ghtkgg.cn/nnews/7008489.htm
- http://m.3g.ghtkgg.cn/nnews/28165.htm
- http://m.3g.ghtkgg.cn/nnews/0460.htm
- http://m.3g.ghtkgg.cn/nnews/749230.htm
- http://m.3g.ghtkgg.cn/nnews/537417.htm
- http://m.3g.ghtkgg.cn/nnews/14075.htm
- http://m.3g.ghtkgg.cn/nnews/408442.htm
- http://m.3g.ghtkgg.cn/nnews/488821.htm
- http://m.3g.ghtkgg.cn/nnews/6575842.htm
- http://m.3g.ghtkgg.cn/nnews/267770.htm
- http://m.3g.ghtkgg.cn/nnews/7283.htm
- http://m.3g.ghtkgg.cn/nnews/58510.htm
- http://m.3g.ghtkgg.cn/nnews/386094.htm
- http://m.3g.ghtkgg.cn/nnews/5802204.htm
- http://m.3g.ghtkgg.cn/nnews/420549.htm
- http://m.3g.ghtkgg.cn/nnews/2506.htm
- http://m.3g.ghtkgg.cn/nnews/3799.htm
- http://m.3g.ghtkgg.cn/nnews/60039.htm
- http://m.3g.ghtkgg.cn/nnews/44918.htm
- http://m.3g.ghtkgg.cn/nnews/6994682.htm
- http://m.3g.ghtkgg.cn/nnews/906192.htm
- http://m.3g.ghtkgg.cn/nnews/8038354.htm
- http://m.3g.ghtkgg.cn/nnews/6821.htm
- http://m.3g.ghtkgg.cn/nnews/259741.htm
- http://m.3g.ghtkgg.cn/nnews/2015.htm
- http://m.3g.ghtkgg.cn/nnews/8516967.htm
- http://m.3g.ghtkgg.cn/nnews/17528.htm
- http://m.3g.ghtkgg.cn/nnews/8573.htm
- http://m.3g.ghtkgg.cn/nnews/5521189.htm
- http://m.3g.ghtkgg.cn/nnews/9902525.htm
- http://m.3g.ghtkgg.cn/nnews/1624.htm
- http://m.3g.ghtkgg.cn/nnews/5962.htm
- http://m.3g.ghtkgg.cn/nnews/3845.htm
- http://m.3g.ghtkgg.cn/nnews/6680496.htm
- http://m.3g.ghtkgg.cn/nnews/590532.htm
- http://m.3g.ghtkgg.cn/nnews/6864.htm
- http://m.3g.ghtkgg.cn/nnews/8310851.htm
- http://m.3g.ghtkgg.cn/nnews/8716099.htm
- http://m.3g.ghtkgg.cn/nnews/7681.htm
- http://m.3g.ghtkgg.cn/nnews/89601.htm
- http://m.3g.ghtkgg.cn/nnews/8154973.htm
- http://m.3g.ghtkgg.cn/nnews/444121.htm
- http://m.3g.ghtkgg.cn/nnews/40208.htm
- http://m.3g.ghtkgg.cn/nnews/0783.htm
- http://m.3g.ghtkgg.cn/nnews/65938.htm
- http://m.3g.ghtkgg.cn/nnews/4469203.htm
- http://m.3g.ghtkgg.cn/nnews/20972.htm
- http://m.3g.ghtkgg.cn/nnews/64854.htm
- http://m.3g.ghtkgg.cn/nnews/230521.htm
- http://m.3g.ghtkgg.cn/nnews/441948.htm
- http://m.3g.ghtkgg.cn/nnews/3016112.htm
- http://m.3g.ghtkgg.cn/nnews/5051874.htm
- http://m.3g.ghtkgg.cn/nnews/856752.htm
- http://m.3g.ghtkgg.cn/nnews/39022.htm
- http://m.3g.ghtkgg.cn/nnews/26151.htm
- http://m.3g.ghtkgg.cn/nnews/92405.htm
- http://m.3g.ghtkgg.cn/nnews/5936.htm
- http://m.3g.ghtkgg.cn/nnews/56827.htm
- http://m.3g.ghtkgg.cn/nnews/9601.htm
- http://m.3g.ghtkgg.cn/nnews/4441.htm
- http://m.3g.ghtkgg.cn/nnews/4241730.htm
- http://m.3g.ghtkgg.cn/nnews/6042987.htm
- http://m.3g.ghtkgg.cn/nnews/18078.htm
- http://m.3g.ghtkgg.cn/nnews/3449.htm
- http://m.3g.ghtkgg.cn/nnews/6600.htm
- http://m.3g.ghtkgg.cn/nnews/3709.htm
- http://m.3g.ghtkgg.cn/nnews/7165378.htm
- http://m.3g.ghtkgg.cn/nnews/9895.htm
- http://m.3g.ghtkgg.cn/nnews/68906.htm
- http://m.3g.ghtkgg.cn/nnews/322344.htm
- http://m.3g.ghtkgg.cn/nnews/6035287.htm
- http://m.3g.ghtkgg.cn/nnews/531629.htm
- http://m.3g.ghtkgg.cn/nnews/73854.htm
- http://m.3g.ghtkgg.cn/nnews/502486.htm
- http://m.3g.ghtkgg.cn/nnews/8984253.htm
- http://m.3g.ghtkgg.cn/nnews/0609282.htm
- http://m.3g.ghtkgg.cn/nnews/6019298.htm
- http://m.3g.ghtkgg.cn/nnews/9378378.htm
- http://m.3g.ghtkgg.cn/nnews/488165.htm
- http://m.3g.ghtkgg.cn/nnews/2507172.htm
- http://m.3g.ghtkgg.cn/nnews/082262.htm
- http://m.3g.ghtkgg.cn/nnews/250733.htm
- http://m.3g.ghtkgg.cn/nnews/90741.htm
- http://m.3g.ghtkgg.cn/nnews/937460.htm
- http://m.3g.ghtkgg.cn/nnews/920527.htm
- http://m.3g.ghtkgg.cn/nnews/1521185.htm
- http://m.3g.ghtkgg.cn/nnews/9565.htm
- http://m.3g.ghtkgg.cn/nnews/548771.htm
- http://m.3g.ghtkgg.cn/nnews/48248.htm
- http://m.3g.ghtkgg.cn/nnews/5677.htm
- http://m.3g.ghtkgg.cn/nnews/77895.htm
- http://m.3g.ghtkgg.cn/nnews/0784.htm
- http://m.3g.ghtkgg.cn/nnews/613506.htm
- http://m.3g.ghtkgg.cn/nnews/3268135.htm
- http://m.3g.ghtkgg.cn/nnews/395916.htm
- http://m.3g.ghtkgg.cn/nnews/9066.htm
- http://m.3g.ghtkgg.cn/nnews/5668093.htm
- http://m.3g.ghtkgg.cn/nnews/054765.htm
- http://m.3g.ghtkgg.cn/nnews/0191.htm
- http://m.3g.ghtkgg.cn/nnews/102078.htm
- http://m.3g.ghtkgg.cn/nnews/29991.htm
- http://m.3g.ghtkgg.cn/nnews/687106.htm
- http://m.3g.ghtkgg.cn/nnews/0367.htm
- http://m.3g.ghtkgg.cn/nnews/37160.htm
- http://m.3g.ghtkgg.cn/nnews/040950.htm
- http://m.3g.ghtkgg.cn/nnews/8483.htm
- http://m.3g.ghtkgg.cn/nnews/994999.htm
- http://m.3g.ghtkgg.cn/nnews/9379.htm
- http://m.3g.ghtkgg.cn/nnews/737277.htm
- http://m.3g.ghtkgg.cn/nnews/1882.htm
- http://m.3g.ghtkgg.cn/nnews/5654144.htm
- http://m.3g.ghtkgg.cn/nnews/589898.htm
- http://m.3g.ghtkgg.cn/nnews/6049.htm
- http://m.3g.ghtkgg.cn/nnews/8750796.htm
- http://m.3g.ghtkgg.cn/nnews/502395.htm
- http://m.3g.ghtkgg.cn/nnews/15151.htm
- http://m.3g.ghtkgg.cn/nnews/314178.htm
- http://m.3g.ghtkgg.cn/nnews/4864.htm
- http://m.3g.ghtkgg.cn/nnews/87909.htm
- http://m.3g.ghtkgg.cn/nnews/8388.htm
- http://m.3g.ghtkgg.cn/nnews/1160461.htm
- http://m.3g.ghtkgg.cn/nnews/8168.htm
- http://m.3g.ghtkgg.cn/nnews/841123.htm
- http://m.3g.ghtkgg.cn/nnews/1549876.htm
- http://m.3g.ghtkgg.cn/nnews/240490.htm
- http://m.3g.ghtkgg.cn/nnews/9127.htm
- http://m.3g.ghtkgg.cn/nnews/6212244.htm
- http://m.3g.ghtkgg.cn/nnews/9205.htm
- http://m.3g.ghtkgg.cn/nnews/57239.htm
- http://m.3g.ghtkgg.cn/nnews/0733570.htm
- http://m.3g.ghtkgg.cn/nnews/4523.htm
- http://m.3g.ghtkgg.cn/nnews/59993.htm
- http://m.3g.ghtkgg.cn/nnews/5019.htm
- http://m.3g.ghtkgg.cn/nnews/2135821.htm
- http://m.3g.ghtkgg.cn/nnews/77936.htm
- http://m.3g.ghtkgg.cn/nnews/1688.htm
- http://m.3g.ghtkgg.cn/nnews/8698986.htm
- http://m.3g.ghtkgg.cn/nnews/294864.htm
- http://m.3g.ghtkgg.cn/nnews/8724.htm
- http://m.3g.ghtkgg.cn/nnews/4082.htm
- http://m.3g.ghtkgg.cn/nnews/5092672.htm
- http://m.3g.ghtkgg.cn/nnews/2167790.htm
- http://m.3g.ghtkgg.cn/nnews/72206.htm
- http://m.3g.ghtkgg.cn/nnews/267172.htm
- http://m.3g.ghtkgg.cn/nnews/905645.htm
- http://m.3g.ghtkgg.cn/nnews/1016260.htm
- http://m.3g.ghtkgg.cn/nnews/9227.htm
- http://m.3g.ghtkgg.cn/nnews/4890599.htm
- http://m.3g.ghtkgg.cn/nnews/09998.htm
- http://m.3g.ghtkgg.cn/nnews/9280.htm
- http://m.3g.ghtkgg.cn/nnews/8951212.htm
- http://m.3g.ghtkgg.cn/nnews/4714.htm
- http://m.3g.ghtkgg.cn/nnews/956996.htm
- http://m.3g.ghtkgg.cn/nnews/3920.htm
- http://m.3g.ghtkgg.cn/nnews/87872.htm
- http://m.3g.ghtkgg.cn/nnews/572847.htm
- http://m.3g.ghtkgg.cn/nnews/9604.htm
- http://m.3g.ghtkgg.cn/nnews/999108.htm
- http://m.3g.ghtkgg.cn/nnews/12418.htm
- http://m.3g.ghtkgg.cn/nnews/0176143.htm
- http://m.3g.ghtkgg.cn/nnews/5389278.htm
- http://m.3g.ghtkgg.cn/nnews/36265.htm
- http://m.3g.ghtkgg.cn/nnews/464150.htm
- http://m.3g.ghtkgg.cn/nnews/03061.htm

## 项目结构

```
newslink-aggregator/
├── app/
│   ├── __init__.py                # Flask 应用工厂，注册蓝图和扩展
│   ├── models.py                  # SQLAlchemy 数据模型（Link, Tag, CheckTask）
│   ├── schemas.py                 # Pydantic / Marshmallow 序列化模式
│   ├── routes/
│   │   ├── api.py                 # REST API 端点：增删改查、标签管理、导入导出
│   │   └── web.py                 # 仪表盘页面路由：主页、搜索页、详情页
│   ├── services/
│   │   ├── fetcher.py             # 链接抓取服务：requests + 重试 + 超时控制
│   │   ├── parser.py              # HTML 解析器：基于 beautifulsoup4 提取元数据
│   │   ├── indexer.py             # FTS5 索引构建与全文搜索服务
│   │   └── notifier.py            # 更新通知服务：邮件和 Webhook 推送
│   ├── cli/
│   │   ├── import_cmd.py          # 批量导入命令：支持 txt / csv / opml
│   │   ├── export_cmd.py          # 导出命令：支持 json / csv / markdown
│   │   └── check_cmd.py           # 手动触发更新检测的命令
│   └── templates/
│       ├── base.html              # 基础模板，包含导航栏和页脚
│       ├── index.html             # 仪表盘首页，显示统计卡片和最近链接
│       ├── search.html            # 搜索结果页，含高亮片段
│       └── detail.html            # 单条链接详情页，展示完整元数据和编辑表单
├── migrations/                    # Alembic 数据库迁移脚本
├── tests/
│   ├── unit/                      # 单元测试：模型、服务、解析器
│   └── integration/               # 集成测试：API 端点、CLI 命令
├── scripts/
│   ├── init_db.py                 # 初始化数据库并创建管理员账户
│   └── sample_data.py             # 生成示例数据用于测试和演示
├── requirements.txt               # 生产环境依赖列表
├── requirements-dev.txt           # 开发环境额外依赖（pytest, black, flake8）
├── Dockerfile                     # 多阶段构建镜像文件
├── docker-compose.yml             # 本地开发容器编排（含 SQLite 持久化卷）
├── .env.example                   # 环境变量模板（配置 SECRET_KEY, MAIL_SERVER 等）
├── config.py                      # 应用配置类（Development, Production, Testing）
├── wsgi.py                        # Gunicorn 入口文件
└── README.md                      # 本文件
```

## 贡献指南

贡献者请遵循以下流程以确保代码质量和项目一致性。所有贡献均需遵守贡献者行为准则。

提交 Issue 描述需求或缺陷：在 GitHub Issues 页面新建议题，使用提供的模板清晰描述问题、复现步骤、预期结果和实际结果。功能请求需说明使用场景和收益。

Fork 仓库并创建功能分支：从主分支 latest 切出新的分支，分支命名遵循 feature/功能名称 或 fix/问题简述。禁止直接在主分支上修改。

编写代码并添加单元测试：所有新增功能或修复必须附带对应的单元测试，覆盖率不得低于 85%。代码风格遵循 PEP 8，提交前使用 black 和 flake8 进行格式化与检查。

发起 Pull Request 并关联 Issue：PR 标题应简明扼要，正文中描述修改内容、测试结果和破坏性变更。必须关联至少一个 Issue 编号。PR 需要至少一位维护者审核通过后方可合并。

更新文档和示例：若修改涉及用户可见的功能或配置，需同步更新 README.md 或 docs 目录下的对应文档。新增命令行参数需在 cli.md 中补充说明。

## 常见问题

Q：导入大量链接时出现超时或内存不足，如何解决？

A：对于超过 1000 条链接的批量导入，建议使用命令行工具并添加 --batch-size 参数控制每批次处理的数量，默认值为 200。同时可降低 fetcher 服务中的并发数（通过环境变量 MAX_WORKERS 调整）。若内存持续告警，考虑使用 SQLite 的 WAL 模式并定期执行 VACUUM 命令。

Q：全文搜索对中文支持不完善，某些关键词搜不到预期结果？

A：本项目使用 SQLite FTS5 的默认分词器，对中文分词效果有限。建议在配置文件中启用 jieba 分词扩展（需安装 jieba 库），并在创建 FTS 虚拟表时指定 tokenize=jieba。若已存在数据，需重建 FTS 表并重新索引所有链接。

Q：如何更换数据库后端，例如从 SQLite 迁移到 PostgreSQL？

A：SQLAlchemy 支持多数据库后端。修改 config.py 中的 SQLALCHEMY_DATABASE_URI 为 PostgreSQL 连接字符串（格式 postgresql://user:pass@host/dbname），然后执行 flask db upgrade 迁移表结构。注意 PostgreSQL 的全文检索语法与 SQLite 不同，需要调整 services/indexer.py 中的查询构造逻辑。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:56
