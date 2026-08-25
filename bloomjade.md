# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端新闻资讯聚合的开源项目，旨在为开发者、内容聚合平台以及个人研究者提供一套标准化的新闻外链采集与整理工具。该项目定位于批量处理来自单一信源的新闻条目链接，通过结构化输出和分类管理，帮助用户快速构建新闻数据集或内容索引。

本项目适用于需要从特定新闻源定期抓取、归档和分发新闻链接的场景，尤其适合移动端新闻聚合类应用的开发者或内容运营人员使用。JNews Link Aggregator 提供了一套完整的链接收录与分类方案，支持将散乱的新闻条目 URL 按照日期、主题或热度进行归纳整理，极大提升信息检索效率。

## 功能概览

**批量链接导入** 支持一次性导入数百条新闻 URL，自动去重并校验链接可用性。

**结构化分类存储** 根据 URL 路径中的数字 ID 或日期信息，自动将链接划分至不同新闻专题或时间分区。

**移动端适配输出** 生成的链接列表专为移动端浏览优化，支持响应式布局和触控操作。

**元数据自动提取** 从 URL 中解析新闻发布时间、文章编号等关键信息，生成结构化元数据表。

**自定义标签系统** 允许用户为每条新闻链接添加自定义标签，便于后续按主题检索。

**导出格式多样化** 支持将收录的新闻链接导出为 JSON、CSV 或纯文本格式，方便二次开发。

**定时同步机制** 内置定时任务模块，可定期检查源站更新，自动抓取新增新闻链接。

**访问统计与监控** 提供链接访问次数统计和失效链接检测，帮助维护链接库的健康度。

## 应用场景

新闻聚合类 App 的后台数据采集模块开发。开发者可以使用 JNews Link Aggregator 快速搭建新闻链接抓取与存储的原型系统，通过批量导入功能将目标信源的全部历史新闻链接纳入本地索引，再结合自定义标签系统进行分类，最终为前端展示提供结构化数据接口。

舆情监控与热点分析项目的前期数据准备。研究人员或数据分析师可以利用本项目的链接分类和元数据提取功能，将大量新闻 URL 转化为可分析的数据集，例如按日期统计新闻发布频率、按主题标签聚类热点事件等。

个人知识库与阅读清单管理。内容爱好者可以借助 JNews Link Aggregator 保存来自特定新闻站点的感兴趣文章链接，通过标签系统和分类存储建立个人化的新闻阅读索引，避免链接散落在浏览器收藏夹中难以检索。

自动化新闻简报生成工具的基础组件。运营人员可以将本项目集成到自动化工作流中，定时抓取最新新闻链接，配合外部内容提取 API 生成每日新闻简报，实现从链接采集到内容呈现的完整链路。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/your-org/jnews-link-aggregator.git

# 进入项目目录
cd jnews-link-aggregator

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 初始化数据库
python scripts/init_db.py

# 运行链接导入示例（导入当前批次的所有链接）
python scripts/import_links.py --batch 143 --input links_143.txt

# 启动本地预览服务
python app.py --port 8080
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10 及以上 | 核心运行环境，用于执行脚本和启动服务 |
| SQLite | 3.35 及以上 | 默认内嵌数据库，存储链接元数据和分类信息 |
| requests | 2.28.0 及以上 | HTTP 请求库，用于链接可用性校验 |
| pandas | 1.5.0 及以上 | 数据分析和导出功能依赖 |
| beautifulsoup4 | 4.11.0 及以上 | HTML 解析库，用于元数据提取 |
| flask | 2.2.0 及以上 | Web 预览服务依赖（可选，用于可视化界面） |
| croniter | 1.3.0 及以上 | 定时任务调度依赖 |
| pytest | 7.2.0 及以上 | 单元测试框架（仅开发环境需要） |
| black | 22.10.0 及以上 | 代码格式化工具（仅开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|----------|
| 用户指南 | docs/user_guide.md | 如何安装、配置和运行本项目，如何导入链接和导出数据 |
| 开发者文档 | docs/developer_guide.md | 项目架构设计、模块划分、如何扩展新功能或集成到其他系统 |
| API 参考 | docs/api_reference.md | 各核心函数和类的详细说明、参数定义、返回值格式 |
| 常见问题 | docs/faq.md | 部署过程中可能遇到的错误码解释、性能调优建议和故障排除 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/40858.htm
- http://m.wap.ghtkgg.cn/jnews/086329.htm
- http://m.wap.ghtkgg.cn/jnews/8220.htm
- http://m.wap.ghtkgg.cn/jnews/5758307.htm
- http://m.wap.ghtkgg.cn/jnews/44996.htm
- http://m.wap.ghtkgg.cn/jnews/6077755.htm
- http://m.wap.ghtkgg.cn/jnews/1603.htm
- http://m.wap.ghtkgg.cn/jnews/103591.htm
- http://m.wap.ghtkgg.cn/jnews/27900.htm
- http://m.wap.ghtkgg.cn/jnews/3503796.htm
- http://m.wap.ghtkgg.cn/jnews/9096.htm
- http://m.wap.ghtkgg.cn/jnews/781233.htm
- http://m.wap.ghtkgg.cn/jnews/760718.htm
- http://m.wap.ghtkgg.cn/jnews/8540.htm
- http://m.wap.ghtkgg.cn/jnews/6780607.htm
- http://m.wap.ghtkgg.cn/jnews/32821.htm
- http://m.wap.ghtkgg.cn/jnews/566564.htm
- http://m.wap.ghtkgg.cn/jnews/8173013.htm
- http://m.wap.ghtkgg.cn/jnews/8247.htm
- http://m.wap.ghtkgg.cn/jnews/0590.htm
- http://m.wap.ghtkgg.cn/jnews/0586.htm
- http://m.wap.ghtkgg.cn/jnews/7761.htm
- http://m.wap.ghtkgg.cn/jnews/1337311.htm
- http://m.wap.ghtkgg.cn/jnews/13696.htm
- http://m.wap.ghtkgg.cn/jnews/094832.htm
- http://m.wap.ghtkgg.cn/jnews/33934.htm
- http://m.wap.ghtkgg.cn/jnews/0854227.htm
- http://m.wap.ghtkgg.cn/jnews/39785.htm
- http://m.wap.ghtkgg.cn/jnews/7439.htm
- http://m.wap.ghtkgg.cn/jnews/987075.htm
- http://m.wap.ghtkgg.cn/jnews/50062.htm
- http://m.wap.ghtkgg.cn/jnews/204887.htm
- http://m.wap.ghtkgg.cn/jnews/57200.htm
- http://m.wap.ghtkgg.cn/jnews/8303475.htm
- http://m.wap.ghtkgg.cn/jnews/322377.htm
- http://m.wap.ghtkgg.cn/jnews/5533.htm
- http://m.wap.ghtkgg.cn/jnews/1684724.htm
- http://m.wap.ghtkgg.cn/jnews/230770.htm
- http://m.wap.ghtkgg.cn/jnews/96926.htm
- http://m.wap.ghtkgg.cn/jnews/89776.htm
- http://m.wap.ghtkgg.cn/jnews/18581.htm
- http://m.wap.ghtkgg.cn/jnews/8674494.htm
- http://m.wap.ghtkgg.cn/jnews/6208196.htm
- http://m.wap.ghtkgg.cn/jnews/6616437.htm
- http://m.wap.ghtkgg.cn/jnews/1988050.htm
- http://m.wap.ghtkgg.cn/jnews/29617.htm
- http://m.wap.ghtkgg.cn/jnews/4714533.htm
- http://m.wap.ghtkgg.cn/jnews/1556.htm
- http://m.wap.ghtkgg.cn/jnews/77106.htm
- http://m.wap.ghtkgg.cn/jnews/592710.htm
- http://m.wap.ghtkgg.cn/jnews/4487.htm
- http://m.wap.ghtkgg.cn/jnews/857241.htm
- http://m.wap.ghtkgg.cn/jnews/79362.htm
- http://m.wap.ghtkgg.cn/jnews/6060.htm
- http://m.wap.ghtkgg.cn/jnews/986881.htm
- http://m.wap.ghtkgg.cn/jnews/169167.htm
- http://m.wap.ghtkgg.cn/jnews/5444696.htm
- http://m.wap.ghtkgg.cn/jnews/6216919.htm
- http://m.wap.ghtkgg.cn/jnews/9817466.htm
- http://m.wap.ghtkgg.cn/jnews/2149465.htm
- http://m.wap.ghtkgg.cn/jnews/4093184.htm
- http://m.wap.ghtkgg.cn/jnews/6465991.htm
- http://m.wap.ghtkgg.cn/jnews/62841.htm
- http://m.wap.ghtkgg.cn/jnews/555004.htm
- http://m.wap.ghtkgg.cn/jnews/99676.htm
- http://m.wap.ghtkgg.cn/jnews/830661.htm
- http://m.wap.ghtkgg.cn/jnews/1320.htm
- http://m.wap.ghtkgg.cn/jnews/98570.htm
- http://m.wap.ghtkgg.cn/jnews/6939.htm
- http://m.wap.ghtkgg.cn/jnews/8293231.htm
- http://m.wap.ghtkgg.cn/jnews/339563.htm
- http://m.wap.ghtkgg.cn/jnews/757428.htm
- http://m.wap.ghtkgg.cn/jnews/50136.htm
- http://m.wap.ghtkgg.cn/jnews/8384.htm
- http://m.wap.ghtkgg.cn/jnews/587560.htm
- http://m.wap.ghtkgg.cn/jnews/967882.htm
- http://m.wap.ghtkgg.cn/jnews/77833.htm
- http://m.wap.ghtkgg.cn/jnews/74337.htm
- http://m.wap.ghtkgg.cn/jnews/4949629.htm
- http://m.wap.ghtkgg.cn/jnews/2633436.htm
- http://m.wap.ghtkgg.cn/jnews/638307.htm
- http://m.wap.ghtkgg.cn/jnews/512098.htm
- http://m.wap.ghtkgg.cn/jnews/44492.htm
- http://m.wap.ghtkgg.cn/jnews/59491.htm
- http://m.wap.ghtkgg.cn/jnews/200043.htm
- http://m.wap.ghtkgg.cn/jnews/465019.htm
- http://m.wap.ghtkgg.cn/jnews/7349.htm
- http://m.wap.ghtkgg.cn/jnews/6728.htm
- http://m.wap.ghtkgg.cn/jnews/456298.htm
- http://m.wap.ghtkgg.cn/jnews/0980630.htm
- http://m.wap.ghtkgg.cn/jnews/877859.htm
- http://m.wap.ghtkgg.cn/jnews/72313.htm
- http://m.wap.ghtkgg.cn/jnews/8950284.htm
- http://m.wap.ghtkgg.cn/jnews/5703777.htm
- http://m.wap.ghtkgg.cn/jnews/1220156.htm
- http://m.wap.ghtkgg.cn/jnews/691150.htm
- http://m.wap.ghtkgg.cn/jnews/0032675.htm
- http://m.wap.ghtkgg.cn/jnews/6297394.htm
- http://m.wap.ghtkgg.cn/jnews/77515.htm
- http://m.wap.ghtkgg.cn/jnews/86614.htm
- http://m.wap.ghtkgg.cn/jnews/2536.htm
- http://m.wap.ghtkgg.cn/jnews/773998.htm
- http://m.wap.ghtkgg.cn/jnews/21939.htm
- http://m.wap.ghtkgg.cn/jnews/4584.htm
- http://m.wap.ghtkgg.cn/jnews/1455.htm
- http://m.wap.ghtkgg.cn/jnews/38291.htm
- http://m.wap.ghtkgg.cn/jnews/7436.htm
- http://m.wap.ghtkgg.cn/jnews/70514.htm
- http://m.wap.ghtkgg.cn/jnews/329721.htm
- http://m.wap.ghtkgg.cn/jnews/9170.htm
- http://m.wap.ghtkgg.cn/jnews/007679.htm
- http://m.wap.ghtkgg.cn/jnews/836527.htm
- http://m.wap.ghtkgg.cn/jnews/45505.htm
- http://m.wap.ghtkgg.cn/jnews/06597.htm
- http://m.wap.ghtkgg.cn/jnews/1679736.htm
- http://m.wap.ghtkgg.cn/jnews/53674.htm
- http://m.wap.ghtkgg.cn/jnews/3165.htm
- http://m.wap.ghtkgg.cn/jnews/201974.htm
- http://m.wap.ghtkgg.cn/jnews/00112.htm
- http://m.wap.ghtkgg.cn/jnews/5199.htm
- http://m.wap.ghtkgg.cn/jnews/3282.htm
- http://m.wap.ghtkgg.cn/jnews/4539271.htm
- http://m.wap.ghtkgg.cn/jnews/887081.htm
- http://m.wap.ghtkgg.cn/jnews/0958.htm
- http://m.wap.ghtkgg.cn/jnews/255595.htm
- http://m.wap.ghtkgg.cn/jnews/35140.htm
- http://m.wap.ghtkgg.cn/jnews/501139.htm
- http://m.wap.ghtkgg.cn/jnews/246567.htm
- http://m.wap.ghtkgg.cn/jnews/4322.htm
- http://m.wap.ghtkgg.cn/jnews/9218.htm
- http://m.wap.ghtkgg.cn/jnews/0777.htm
- http://m.wap.ghtkgg.cn/jnews/8636411.htm
- http://m.wap.ghtkgg.cn/jnews/62959.htm
- http://m.wap.ghtkgg.cn/jnews/0723736.htm
- http://m.wap.ghtkgg.cn/jnews/192438.htm
- http://m.wap.ghtkgg.cn/jnews/8084.htm
- http://m.wap.ghtkgg.cn/jnews/968220.htm
- http://m.wap.ghtkgg.cn/jnews/1605281.htm
- http://m.wap.ghtkgg.cn/jnews/8189.htm
- http://m.wap.ghtkgg.cn/jnews/33199.htm
- http://m.wap.ghtkgg.cn/jnews/067017.htm
- http://m.wap.ghtkgg.cn/jnews/6287931.htm
- http://m.wap.ghtkgg.cn/jnews/02781.htm
- http://m.wap.ghtkgg.cn/jnews/467291.htm
- http://m.wap.ghtkgg.cn/jnews/19153.htm
- http://m.wap.ghtkgg.cn/jnews/6723171.htm
- http://m.wap.ghtkgg.cn/jnews/4254391.htm
- http://m.wap.ghtkgg.cn/jnews/607192.htm
- http://m.wap.ghtkgg.cn/jnews/94454.htm
- http://m.wap.ghtkgg.cn/jnews/484195.htm
- http://m.wap.ghtkgg.cn/jnews/933595.htm
- http://m.wap.ghtkgg.cn/jnews/3426451.htm
- http://m.wap.ghtkgg.cn/jnews/49605.htm
- http://m.wap.ghtkgg.cn/jnews/1281995.htm
- http://m.wap.ghtkgg.cn/jnews/57947.htm
- http://m.wap.ghtkgg.cn/jnews/5979.htm
- http://m.wap.ghtkgg.cn/jnews/14945.htm
- http://m.wap.ghtkgg.cn/jnews/73249.htm
- http://m.wap.ghtkgg.cn/jnews/88222.htm
- http://m.wap.ghtkgg.cn/jnews/49093.htm
- http://m.wap.ghtkgg.cn/jnews/3156.htm
- http://m.wap.ghtkgg.cn/jnews/9530803.htm
- http://m.wap.ghtkgg.cn/jnews/5498206.htm
- http://m.wap.ghtkgg.cn/jnews/9485.htm
- http://m.wap.ghtkgg.cn/jnews/4664431.htm
- http://m.wap.ghtkgg.cn/jnews/1314741.htm
- http://m.wap.ghtkgg.cn/jnews/276096.htm
- http://m.wap.ghtkgg.cn/jnews/4242758.htm
- http://m.wap.ghtkgg.cn/jnews/0637.htm
- http://m.wap.ghtkgg.cn/jnews/377324.htm
- http://m.wap.ghtkgg.cn/jnews/564868.htm
- http://m.wap.ghtkgg.cn/jnews/87130.htm
- http://m.wap.ghtkgg.cn/jnews/970743.htm
- http://m.wap.ghtkgg.cn/jnews/7174289.htm
- http://m.wap.ghtkgg.cn/jnews/54059.htm
- http://m.wap.ghtkgg.cn/jnews/6430487.htm
- http://m.wap.ghtkgg.cn/jnews/2127.htm
- http://m.wap.ghtkgg.cn/jnews/4971451.htm
- http://m.wap.ghtkgg.cn/jnews/1914363.htm
- http://m.wap.ghtkgg.cn/jnews/6517189.htm
- http://m.wap.ghtkgg.cn/jnews/334658.htm
- http://m.wap.ghtkgg.cn/jnews/66737.htm
- http://m.wap.ghtkgg.cn/jnews/10317.htm
- http://m.wap.ghtkgg.cn/jnews/5733151.htm
- http://m.wap.ghtkgg.cn/jnews/3795439.htm
- http://m.wap.ghtkgg.cn/jnews/789053.htm
- http://m.wap.ghtkgg.cn/jnews/512806.htm
- http://m.wap.ghtkgg.cn/jnews/5284.htm
- http://m.wap.ghtkgg.cn/jnews/741197.htm
- http://m.wap.ghtkgg.cn/jnews/91740.htm
- http://m.wap.ghtkgg.cn/jnews/55679.htm
- http://m.wap.ghtkgg.cn/jnews/2049680.htm
- http://m.wap.ghtkgg.cn/jnews/0632.htm
- http://m.wap.ghtkgg.cn/jnews/07063.htm
- http://m.wap.ghtkgg.cn/jnews/1394.htm
- http://m.wap.ghtkgg.cn/jnews/2005.htm
- http://m.wap.ghtkgg.cn/jnews/997934.htm
- http://m.wap.ghtkgg.cn/jnews/20920.htm
- http://m.wap.ghtkgg.cn/jnews/4312982.htm
- http://m.wap.ghtkgg.cn/jnews/4979.htm
- http://m.wap.ghtkgg.cn/jnews/29115.htm
- http://m.wap.ghtkgg.cn/jnews/454377.htm
- http://m.wap.ghtkgg.cn/jnews/5878.htm
- http://m.wap.ghtkgg.cn/jnews/991299.htm
- http://m.wap.ghtkgg.cn/jnews/172254.htm
- http://m.wap.ghtkgg.cn/jnews/5705.htm
- http://m.wap.ghtkgg.cn/jnews/2371.htm
- http://m.wap.ghtkgg.cn/jnews/53452.htm
- http://m.wap.ghtkgg.cn/jnews/621335.htm
- http://m.wap.ghtkgg.cn/jnews/0237.htm
- http://m.wap.ghtkgg.cn/jnews/6963.htm
- http://m.wap.ghtkgg.cn/jnews/408054.htm
- http://m.wap.ghtkgg.cn/jnews/6583264.htm
- http://m.wap.ghtkgg.cn/jnews/5511.htm
- http://m.wap.ghtkgg.cn/jnews/36840.htm
- http://m.wap.ghtkgg.cn/jnews/9709.htm
- http://m.wap.ghtkgg.cn/jnews/8079.htm
- http://m.wap.ghtkgg.cn/jnews/7069.htm
- http://m.wap.ghtkgg.cn/jnews/8080.htm
- http://m.wap.ghtkgg.cn/jnews/87228.htm
- http://m.wap.ghtkgg.cn/jnews/4184024.htm
- http://m.wap.ghtkgg.cn/jnews/93109.htm
- http://m.wap.ghtkgg.cn/jnews/79370.htm
- http://m.wap.ghtkgg.cn/jnews/131270.htm
- http://m.wap.ghtkgg.cn/jnews/1578249.htm
- http://m.wap.ghtkgg.cn/jnews/913078.htm
- http://m.wap.ghtkgg.cn/jnews/163580.htm
- http://m.wap.ghtkgg.cn/jnews/1165.htm
- http://m.wap.ghtkgg.cn/jnews/972769.htm
- http://m.wap.ghtkgg.cn/jnews/7429433.htm
- http://m.wap.ghtkgg.cn/jnews/55649.htm
- http://m.wap.ghtkgg.cn/jnews/628127.htm
- http://m.wap.ghtkgg.cn/jnews/4944.htm
- http://m.wap.ghtkgg.cn/jnews/5585.htm
- http://m.wap.ghtkgg.cn/jnews/8116.htm
- http://m.wap.ghtkgg.cn/jnews/7370.htm
- http://m.wap.ghtkgg.cn/jnews/5932293.htm
- http://m.wap.ghtkgg.cn/jnews/510550.htm
- http://m.wap.ghtkgg.cn/jnews/44191.htm
- http://m.wap.ghtkgg.cn/jnews/5969.htm
- http://m.wap.ghtkgg.cn/jnews/2332.htm
- http://m.wap.ghtkgg.cn/jnews/6940.htm
- http://m.wap.ghtkgg.cn/jnews/8563051.htm
- http://m.wap.ghtkgg.cn/jnews/6244603.htm
- http://m.wap.ghtkgg.cn/jnews/33971.htm
- http://m.wap.ghtkgg.cn/jnews/233315.htm
- http://m.wap.ghtkgg.cn/jnews/600294.htm
- http://m.wap.ghtkgg.cn/jnews/6099271.htm
- http://m.wap.ghtkgg.cn/jnews/3519467.htm
- http://m.wap.ghtkgg.cn/jnews/742875.htm
- http://m.wap.ghtkgg.cn/jnews/5820917.htm
- http://m.wap.ghtkgg.cn/jnews/61160.htm
- http://m.wap.ghtkgg.cn/jnews/8390.htm
- http://m.wap.ghtkgg.cn/jnews/73583.htm
- http://m.wap.ghtkgg.cn/jnews/0311.htm
- http://m.wap.ghtkgg.cn/jnews/2823.htm
- http://m.wap.ghtkgg.cn/jnews/187729.htm
- http://m.wap.ghtkgg.cn/jnews/844950.htm
- http://m.wap.ghtkgg.cn/jnews/7028984.htm
- http://m.wap.ghtkgg.cn/jnews/8281.htm
- http://m.wap.ghtkgg.cn/jnews/1465572.htm
- http://m.wap.ghtkgg.cn/jnews/2729.htm
- http://m.wap.ghtkgg.cn/jnews/702802.htm
- http://m.wap.ghtkgg.cn/jnews/5958.htm
- http://m.wap.ghtkgg.cn/jnews/3196.htm
- http://m.wap.ghtkgg.cn/jnews/01895.htm
- http://m.wap.ghtkgg.cn/jnews/7150936.htm
- http://m.wap.ghtkgg.cn/jnews/3369.htm
- http://m.wap.ghtkgg.cn/jnews/3495706.htm
- http://m.wap.ghtkgg.cn/jnews/5186680.htm
- http://m.wap.ghtkgg.cn/jnews/5189467.htm
- http://m.wap.ghtkgg.cn/jnews/5488717.htm
- http://m.wap.ghtkgg.cn/jnews/62184.htm
- http://m.wap.ghtkgg.cn/jnews/519657.htm
- http://m.wap.ghtkgg.cn/jnews/0575089.htm
- http://m.wap.ghtkgg.cn/jnews/532491.htm
- http://m.wap.ghtkgg.cn/jnews/07831.htm
- http://m.wap.ghtkgg.cn/jnews/9894.htm
- http://m.wap.ghtkgg.cn/jnews/7050921.htm
- http://m.wap.ghtkgg.cn/jnews/9615.htm
- http://m.wap.ghtkgg.cn/jnews/2439.htm
- http://m.wap.ghtkgg.cn/jnews/05045.htm
- http://m.wap.ghtkgg.cn/jnews/669237.htm
- http://m.wap.ghtkgg.cn/jnews/425756.htm
- http://m.wap.ghtkgg.cn/jnews/5849390.htm
- http://m.wap.ghtkgg.cn/jnews/05508.htm
- http://m.wap.ghtkgg.cn/jnews/19136.htm
- http://m.wap.ghtkgg.cn/jnews/39795.htm
- http://m.wap.ghtkgg.cn/jnews/602270.htm
- http://m.wap.ghtkgg.cn/jnews/305112.htm
- http://m.wap.ghtkgg.cn/jnews/9979.htm
- http://m.wap.ghtkgg.cn/jnews/054454.htm
- http://m.wap.ghtkgg.cn/jnews/915191.htm
- http://m.wap.ghtkgg.cn/jnews/5094.htm
- http://m.wap.ghtkgg.cn/jnews/98813.htm
- http://m.wap.ghtkgg.cn/jnews/6714015.htm
- http://m.wap.ghtkgg.cn/jnews/87024.htm
- http://m.wap.ghtkgg.cn/jnews/45645.htm
- http://m.wap.ghtkgg.cn/jnews/69018.htm
- http://m.wap.ghtkgg.cn/jnews/9190.htm

## 项目结构

```
jnews-link-aggregator/
├── app.py                           # Flask 应用入口，提供 Web 预览界面和 API 服务
├── requirements.txt                 # Python 依赖声明文件
├── config/
│   ├── settings.py                  # 全局配置项（端口、数据库路径、日志级别等）
│   └── batch_143.yaml               # 第 143 批链接的元数据配置（批次说明、分类规则）
├── core/
│   ├── __init__.py
│   ├── importer.py                  # 链接批量导入核心模块，包含去重和校验逻辑
│   ├── classifier.py                # 基于 URL 模式和标签系统的自动分类模块
│   ├── metadata_extractor.py        # 从 URL 和内容中提取元数据（日期、编号等）
│   └── exporter.py                  # 支持 JSON / CSV / TXT 格式的数据导出模块
├── scripts/
│   ├── init_db.py                   # 初始化 SQLite 数据库表结构的脚本
│   ├── import_links.py              # 命令行导入工具，支持指定批次和输入文件
│   └── schedule_fetcher.py          # 定时任务守护脚本，周期性检查源站更新
├── data/
│   ├── raw_links/                   # 原始链接文本文件存储目录
│   │   └── links_143.txt            # 第 143 批原始链接清单
│   ├── parsed/                      # 解析后的结构化数据缓存目录
│   │   └── batch_143.parquet        # 第 143 批处理后的列式存储数据
│   └── database/
│       └── jnews.db                 # SQLite 主数据库文件
├── tests/
│   ├── test_importer.py             # 导入模块的单元测试
│   ├── test_classifier.py           # 分类模块的单元测试
│   └── test_metadata.py             # 元数据提取模块的单元测试
├── docs/
│   ├── user_guide.md                # 用户指南文档
│   ├── developer_guide.md           # 开发者文档
│   ├── api_reference.md             # API 参考文档
│   └── faq.md                       # 常见问题文档
└── LICENSE                          # MIT 许可证文件
```

## 贡献指南

1. 从 GitHub 仓库 Fork 本项目到个人账号，然后克隆到本地开发环境。建议在开发前阅读 docs/developer_guide.md 了解项目架构和代码规范。

2. 创建新的功能分支进行开发，分支命名建议遵循 feature/功能描述 或 fix/问题描述 的格式。确保所有新增代码均包含对应的单元测试，且测试覆盖率达到 80% 以上。

3. 提交代码前运行 black 和 pytest 进行格式检查和测试验证，确保代码风格统一且所有测试用例通过。提交信息请使用清晰的英文描述，说明本次变更的目的和影响范围。

4. 向主仓库的 develop 分支发起 Pull Request，并在 PR 描述中详细说明功能实现方案、测试结果以及可能的兼容性影响。项目维护者会在 3 个工作日内进行 Code Review。

5. 如需新增新闻源支持或扩展元数据字段，请在 core/ 目录下对应的模块中添加适配器，并更新 docs/api_reference.md 中的相关接口说明。

## 常见问题

问：导入链接时提示部分链接校验失败，如何定位具体问题？

答：校验失败通常由网络超时或目标服务器拒绝连接引起。请检查 logs/importer.log 日志文件，其中会记录每个失败链接的 HTTP 状态码和错误详情。您也可以调整 config/settings.py 中的 REQUEST_TIMEOUT 和 RETRY_COUNT 参数，增加超时时间和重试次数。对于持续失败的链接，可能是源站已删除该新闻条目，建议手动确认后从导入列表中移除。

问：如何扩展定时抓取功能以支持多个新闻源？

答：您可以在 config/settings.py 中配置 SOURCES 列表，每个源包含名称、基础 URL 和链接匹配规则。然后在 core/fetcher.py 中实现针对不同源的解析适配器。本项目目前已支持基于正则表达式的 URL 模式匹配，您只需在配置文件中添加新的匹配规则和对应的元数据映射即可。具体实现细节可参考 docs/developer_guide.md 中的扩展开发章节。

问：导出的 JSON 数据中 link_status 字段包含 error 值，应如何处理？

答：link_status 字段值为 error 表示该链接在导入时或定期检查中无法访问。建议定期运行 scripts/check_links.py 脚本更新所有链接的状态。如果大量链接出现 error 状态，请检查您的网络环境是否能够正常访问 m.wap.ghtkgg.cn 域名，或者该新闻源是否已停止服务。对于长期不可用的链接，可通过管理命令将其标记为 archived 状态并从活跃列表中排除。

## 许可证

MIT License

Copyright (c) 2026 JNews Link Aggregator Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
