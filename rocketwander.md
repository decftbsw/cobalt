# NewsIndex Aggregate

NewsIndex Aggregate 是一个面向新闻资讯聚合、外链资源整理与内容导航的开源工具集。该项目定位于为个人开发者、内容运营团队以及学术研究机构提供一套结构化的新闻外链管理方案，用于批量处理、分类存储和快速检索来自特定信源的历史新闻页面。

本项目不提供新闻抓取与爬虫功能，而是专注于对已有的新闻外链进行规范化整理、元数据标注与索引构建。通过标准化的目录结构与配置文件，用户可以将大量散乱的新闻 URL 转化为可维护、可扩展的资源清单，适用于内容归档、舆情分析语料构建以及历史新闻回溯等场景。

## 功能概览

**批量外链导入** 支持从文本文件或标准输入中批量读取新闻 URL，自动解析 URL 结构并进行格式校验。

**动态索引生成** 根据新闻 ID 与发布时间等元数据，自动生成多级索引目录，支持按日期、按类别、按关键词进行归类。

**元数据提取与标注** 从 URL 路径中提取新闻编号、发布时间等隐含信息，并支持用户自定义标签与备注字段。

**查重与冲突检测** 自动识别重复导入的 URL，提供冲突处理策略，避免资源重复收录。

**多格式导出支持** 支持将整理后的资源列表导出为 JSON、CSV 以及纯文本格式，便于下游工具链使用。

**配置化运行模式** 通过 YAML 配置文件定义资源整理规则，包括分类映射、命名规范和输出目录结构。

**增量更新机制** 支持基于已有索引的增量导入模式，仅处理新增或变更的 URL，提升大规模资源整理效率。

## 应用场景

个人博客或小型内容站点的外链归档。内容创作者可以将日常收集的新闻链接通过本项目进行统一管理，生成可供站内引用的资源目录，避免外链散落与遗忘。

学术研究中的新闻语料构建。社会科学或计算语言学研究者可将特定时间段内的新闻页面链接整理为结构化数据集，配合后续的文本下载与内容分析流程。

历史新闻回溯与事件追踪。运营人员可通过本项目维护历史新闻链接库，按时间轴或事件主题进行标注，方便后续快速检索与复盘。

团队内部知识库的新闻资源整合。团队可将来自同一信源的不同新闻页面整合为统一的资源索引，减少重复劳动，提升信息共享效率。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/example/newsindex-aggregate.git

# 进入项目目录
cd newsindex-aggregate

# 安装依赖（基于 Python 3.10+）
pip install -r requirements.txt

# 运行快速导入示例（使用项目内置的示例 URL 列表）
python run.py --input samples/urls.txt --output data/index.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 及以上 | 核心运行环境，需支持类型注解与 dataclass |
| PyYAML | 6.0 及以上 | 用于解析项目配置文件 |
| click | 8.1 及以上 | 命令行界面交互框架 |
| pytest | 7.0 及以上 | 单元测试与集成测试（仅开发依赖） |
| black | 22.0 及以上 | 代码格式化工具（仅开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何安装、配置、运行以及常见操作流程 |
| 配置参考 | docs/config-reference.md | 所有配置字段的含义、默认值与示例 |
| 开发者指南 | docs/developer-guide.md | 项目架构、模块划分与二次开发说明 |
| API 文档 | docs/api.md | 核心模块与函数的接口定义及调用示例 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/2174.htm
- http://m.wap.oexnr.cn/jnews/9039.htm
- http://m.wap.oexnr.cn/jnews/100066.htm
- http://m.wap.oexnr.cn/jnews/334846.htm
- http://m.wap.oexnr.cn/jnews/5069.htm
- http://m.wap.oexnr.cn/jnews/744015.htm
- http://m.wap.oexnr.cn/jnews/74133.htm
- http://m.wap.oexnr.cn/jnews/18384.htm
- http://m.wap.oexnr.cn/jnews/3558192.htm
- http://m.wap.oexnr.cn/jnews/6581921.htm
- http://m.wap.oexnr.cn/jnews/70968.htm
- http://m.wap.oexnr.cn/jnews/269165.htm
- http://m.wap.oexnr.cn/jnews/0024.htm
- http://m.wap.oexnr.cn/jnews/6683969.htm
- http://m.wap.oexnr.cn/jnews/4098.htm
- http://m.wap.oexnr.cn/jnews/2793.htm
- http://m.wap.oexnr.cn/jnews/74970.htm
- http://m.wap.oexnr.cn/jnews/2306.htm
- http://m.wap.oexnr.cn/jnews/6244201.htm
- http://m.wap.oexnr.cn/jnews/4135270.htm
- http://m.wap.oexnr.cn/jnews/5418.htm
- http://m.wap.oexnr.cn/jnews/297426.htm
- http://m.wap.oexnr.cn/jnews/033535.htm
- http://m.wap.oexnr.cn/jnews/3502420.htm
- http://m.wap.oexnr.cn/jnews/59793.htm
- http://m.wap.oexnr.cn/jnews/634192.htm
- http://m.wap.oexnr.cn/jnews/202750.htm
- http://m.wap.oexnr.cn/jnews/602595.htm
- http://m.wap.oexnr.cn/jnews/2905.htm
- http://m.wap.oexnr.cn/jnews/011490.htm
- http://m.wap.oexnr.cn/jnews/71568.htm
- http://m.wap.oexnr.cn/jnews/2628.htm
- http://m.wap.oexnr.cn/jnews/1323.htm
- http://m.wap.oexnr.cn/jnews/9706.htm
- http://m.wap.oexnr.cn/jnews/8631.htm
- http://m.wap.oexnr.cn/jnews/6990923.htm
- http://m.wap.oexnr.cn/jnews/2651652.htm
- http://m.wap.oexnr.cn/jnews/657641.htm
- http://m.wap.oexnr.cn/jnews/9257753.htm
- http://m.wap.oexnr.cn/jnews/4922.htm
- http://m.wap.oexnr.cn/jnews/6485135.htm
- http://m.wap.oexnr.cn/jnews/2505295.htm
- http://m.wap.oexnr.cn/jnews/42983.htm
- http://m.wap.oexnr.cn/jnews/2752429.htm
- http://m.wap.oexnr.cn/jnews/6565.htm
- http://m.wap.oexnr.cn/jnews/205140.htm
- http://m.wap.oexnr.cn/jnews/7337.htm
- http://m.wap.oexnr.cn/jnews/0011.htm
- http://m.wap.oexnr.cn/jnews/011419.htm
- http://m.wap.oexnr.cn/jnews/4112.htm
- http://m.wap.oexnr.cn/jnews/4051.htm
- http://m.wap.oexnr.cn/jnews/821925.htm
- http://m.wap.oexnr.cn/jnews/7521.htm
- http://m.wap.oexnr.cn/jnews/457677.htm
- http://m.wap.oexnr.cn/jnews/747137.htm
- http://m.wap.oexnr.cn/jnews/61806.htm
- http://m.wap.oexnr.cn/jnews/397008.htm
- http://m.wap.oexnr.cn/jnews/15750.htm
- http://m.wap.oexnr.cn/jnews/23625.htm
- http://m.wap.oexnr.cn/jnews/94236.htm
- http://m.wap.oexnr.cn/jnews/4096317.htm
- http://m.wap.oexnr.cn/jnews/3763430.htm
- http://m.wap.oexnr.cn/jnews/8788138.htm
- http://m.wap.oexnr.cn/jnews/80792.htm
- http://m.wap.oexnr.cn/jnews/7074.htm
- http://m.wap.oexnr.cn/jnews/1170123.htm
- http://m.wap.oexnr.cn/jnews/48651.htm
- http://m.wap.oexnr.cn/jnews/738300.htm
- http://m.wap.oexnr.cn/jnews/5507.htm
- http://m.wap.oexnr.cn/jnews/8650302.htm
- http://m.wap.oexnr.cn/jnews/945742.htm
- http://m.wap.oexnr.cn/jnews/50721.htm
- http://m.wap.oexnr.cn/jnews/493722.htm
- http://m.wap.oexnr.cn/jnews/65626.htm
- http://m.wap.oexnr.cn/jnews/8633.htm
- http://m.wap.oexnr.cn/jnews/0148341.htm
- http://m.wap.oexnr.cn/jnews/7606.htm
- http://m.wap.oexnr.cn/jnews/9459217.htm
- http://m.wap.oexnr.cn/jnews/5912.htm
- http://m.wap.oexnr.cn/jnews/1779277.htm
- http://m.wap.oexnr.cn/jnews/9545515.htm
- http://m.wap.oexnr.cn/jnews/2153.htm
- http://m.wap.oexnr.cn/jnews/3964.htm
- http://m.wap.oexnr.cn/jnews/85986.htm
- http://m.wap.oexnr.cn/jnews/044515.htm
- http://m.wap.oexnr.cn/jnews/01856.htm
- http://m.wap.oexnr.cn/jnews/5584.htm
- http://m.wap.oexnr.cn/jnews/8872.htm
- http://m.wap.oexnr.cn/jnews/4508550.htm
- http://m.wap.oexnr.cn/jnews/29590.htm
- http://m.wap.oexnr.cn/jnews/9964563.htm
- http://m.wap.oexnr.cn/jnews/8088.htm
- http://m.wap.oexnr.cn/jnews/246680.htm
- http://m.wap.oexnr.cn/jnews/0542481.htm
- http://m.wap.oexnr.cn/jnews/68166.htm
- http://m.wap.oexnr.cn/jnews/8078.htm
- http://m.wap.oexnr.cn/jnews/59008.htm
- http://m.wap.oexnr.cn/jnews/66282.htm
- http://m.wap.oexnr.cn/jnews/2392611.htm
- http://m.wap.oexnr.cn/jnews/7628494.htm
- http://m.wap.oexnr.cn/jnews/605527.htm
- http://m.wap.oexnr.cn/jnews/7898524.htm
- http://m.wap.oexnr.cn/jnews/5248067.htm
- http://m.wap.oexnr.cn/jnews/6219992.htm
- http://m.wap.oexnr.cn/jnews/196918.htm
- http://m.wap.oexnr.cn/jnews/4387.htm
- http://m.wap.oexnr.cn/jnews/389977.htm
- http://m.wap.oexnr.cn/jnews/14140.htm
- http://m.wap.oexnr.cn/jnews/939098.htm
- http://m.wap.oexnr.cn/jnews/6194.htm
- http://m.wap.oexnr.cn/jnews/6524412.htm
- http://m.wap.oexnr.cn/jnews/46913.htm
- http://m.wap.oexnr.cn/jnews/1418.htm
- http://m.wap.oexnr.cn/jnews/4448.htm
- http://m.wap.oexnr.cn/jnews/998246.htm
- http://m.wap.oexnr.cn/jnews/0057126.htm
- http://m.wap.oexnr.cn/jnews/30148.htm
- http://m.wap.oexnr.cn/jnews/6695149.htm
- http://m.wap.oexnr.cn/jnews/8547.htm
- http://m.wap.oexnr.cn/jnews/3817614.htm
- http://m.wap.oexnr.cn/jnews/898077.htm
- http://m.wap.oexnr.cn/jnews/774351.htm
- http://m.wap.oexnr.cn/jnews/7862.htm
- http://m.wap.oexnr.cn/jnews/811025.htm
- http://m.wap.oexnr.cn/jnews/0058784.htm
- http://m.wap.oexnr.cn/jnews/29718.htm
- http://m.wap.oexnr.cn/jnews/1355958.htm
- http://m.wap.oexnr.cn/jnews/518466.htm
- http://m.wap.oexnr.cn/jnews/68517.htm
- http://m.wap.oexnr.cn/jnews/8961.htm
- http://m.wap.oexnr.cn/jnews/6081.htm
- http://m.wap.oexnr.cn/jnews/511867.htm
- http://m.wap.oexnr.cn/jnews/9290246.htm
- http://m.wap.oexnr.cn/jnews/74120.htm
- http://m.wap.oexnr.cn/jnews/736020.htm
- http://m.wap.oexnr.cn/jnews/4104.htm
- http://m.wap.oexnr.cn/jnews/7741780.htm
- http://m.wap.oexnr.cn/jnews/2261.htm
- http://m.wap.oexnr.cn/jnews/3150857.htm
- http://m.wap.oexnr.cn/jnews/1247840.htm
- http://m.wap.oexnr.cn/jnews/627311.htm
- http://m.wap.oexnr.cn/jnews/1510.htm
- http://m.wap.oexnr.cn/jnews/2819408.htm
- http://m.wap.oexnr.cn/jnews/2735354.htm
- http://m.wap.oexnr.cn/jnews/4228.htm
- http://m.wap.oexnr.cn/jnews/712786.htm
- http://m.wap.oexnr.cn/jnews/53301.htm
- http://m.wap.oexnr.cn/jnews/75697.htm
- http://m.wap.oexnr.cn/jnews/08846.htm
- http://m.wap.oexnr.cn/jnews/9342627.htm
- http://m.wap.oexnr.cn/jnews/528248.htm
- http://m.wap.oexnr.cn/jnews/20599.htm
- http://m.wap.oexnr.cn/jnews/1606.htm
- http://m.wap.oexnr.cn/jnews/4974.htm
- http://m.wap.oexnr.cn/jnews/655788.htm
- http://m.wap.oexnr.cn/jnews/3411632.htm
- http://m.wap.oexnr.cn/jnews/585961.htm
- http://m.wap.oexnr.cn/jnews/4941.htm
- http://m.wap.oexnr.cn/jnews/1822420.htm
- http://m.wap.oexnr.cn/jnews/319783.htm
- http://m.wap.oexnr.cn/jnews/5766.htm
- http://m.wap.oexnr.cn/jnews/02103.htm
- http://m.wap.oexnr.cn/jnews/3354.htm
- http://m.wap.oexnr.cn/jnews/61746.htm
- http://m.wap.oexnr.cn/jnews/995272.htm
- http://m.wap.oexnr.cn/jnews/6808.htm
- http://m.wap.oexnr.cn/jnews/46324.htm
- http://m.wap.oexnr.cn/jnews/915044.htm
- http://m.wap.oexnr.cn/jnews/9886509.htm
- http://m.wap.oexnr.cn/jnews/8803.htm
- http://m.wap.oexnr.cn/jnews/930331.htm
- http://m.wap.oexnr.cn/jnews/345817.htm
- http://m.wap.oexnr.cn/jnews/848617.htm
- http://m.wap.oexnr.cn/jnews/43967.htm
- http://m.wap.oexnr.cn/jnews/8561.htm
- http://m.wap.oexnr.cn/jnews/0562012.htm
- http://m.wap.oexnr.cn/jnews/703099.htm
- http://m.wap.oexnr.cn/jnews/052097.htm
- http://m.wap.oexnr.cn/jnews/3002.htm
- http://m.wap.oexnr.cn/jnews/836046.htm
- http://m.wap.oexnr.cn/jnews/8684.htm
- http://m.wap.oexnr.cn/jnews/7856805.htm
- http://m.wap.oexnr.cn/jnews/7517625.htm
- http://m.wap.oexnr.cn/jnews/76939.htm
- http://m.wap.oexnr.cn/jnews/830951.htm
- http://m.wap.oexnr.cn/jnews/4938.htm
- http://m.wap.oexnr.cn/jnews/2709.htm
- http://m.wap.oexnr.cn/jnews/947816.htm
- http://m.wap.oexnr.cn/jnews/973969.htm
- http://m.wap.oexnr.cn/jnews/75918.htm
- http://m.wap.oexnr.cn/jnews/6854.htm
- http://m.wap.oexnr.cn/jnews/9789.htm
- http://m.wap.oexnr.cn/jnews/333915.htm
- http://m.wap.oexnr.cn/jnews/34797.htm
- http://m.wap.oexnr.cn/jnews/5836.htm
- http://m.wap.oexnr.cn/jnews/9508891.htm
- http://m.wap.oexnr.cn/jnews/0886.htm
- http://m.wap.oexnr.cn/jnews/1499.htm
- http://m.wap.oexnr.cn/jnews/7163696.htm
- http://m.wap.oexnr.cn/jnews/33122.htm
- http://m.wap.oexnr.cn/jnews/48644.htm
- http://m.wap.oexnr.cn/jnews/197584.htm
- http://m.wap.oexnr.cn/jnews/3550801.htm
- http://m.wap.oexnr.cn/jnews/2029741.htm
- http://m.wap.oexnr.cn/jnews/041999.htm
- http://m.wap.oexnr.cn/jnews/80418.htm
- http://m.wap.oexnr.cn/jnews/715844.htm
- http://m.wap.oexnr.cn/jnews/66802.htm
- http://m.wap.oexnr.cn/jnews/9228.htm
- http://m.wap.oexnr.cn/jnews/50677.htm
- http://m.wap.oexnr.cn/jnews/8455.htm
- http://m.wap.oexnr.cn/jnews/38683.htm
- http://m.wap.oexnr.cn/jnews/8314808.htm
- http://m.wap.oexnr.cn/jnews/2733980.htm
- http://m.wap.oexnr.cn/jnews/1401054.htm
- http://m.wap.oexnr.cn/jnews/35466.htm
- http://m.wap.oexnr.cn/jnews/1877.htm
- http://m.wap.oexnr.cn/jnews/23312.htm
- http://m.wap.oexnr.cn/jnews/5911.htm
- http://m.wap.oexnr.cn/jnews/778688.htm
- http://m.wap.oexnr.cn/jnews/3202.htm
- http://m.wap.oexnr.cn/jnews/728262.htm
- http://m.wap.oexnr.cn/jnews/421842.htm
- http://m.wap.oexnr.cn/jnews/3874404.htm
- http://m.wap.oexnr.cn/jnews/4196.htm
- http://m.wap.oexnr.cn/jnews/4219.htm
- http://m.wap.oexnr.cn/jnews/9641937.htm
- http://m.wap.oexnr.cn/jnews/9545171.htm
- http://m.wap.oexnr.cn/jnews/69944.htm
- http://m.wap.oexnr.cn/jnews/8165373.htm
- http://m.wap.oexnr.cn/jnews/6911291.htm
- http://m.wap.oexnr.cn/jnews/961021.htm
- http://m.wap.oexnr.cn/jnews/17712.htm
- http://m.wap.oexnr.cn/jnews/32482.htm
- http://m.wap.oexnr.cn/jnews/27096.htm
- http://m.wap.oexnr.cn/jnews/3762078.htm
- http://m.wap.oexnr.cn/jnews/86372.htm
- http://m.wap.oexnr.cn/jnews/556887.htm
- http://m.wap.oexnr.cn/jnews/931553.htm
- http://m.wap.oexnr.cn/jnews/9591210.htm
- http://m.wap.oexnr.cn/jnews/5861.htm
- http://m.wap.oexnr.cn/jnews/3876086.htm
- http://m.wap.oexnr.cn/jnews/03800.htm
- http://m.wap.oexnr.cn/jnews/8799199.htm
- http://m.wap.oexnr.cn/jnews/118414.htm
- http://m.wap.oexnr.cn/jnews/8164947.htm
- http://m.wap.oexnr.cn/jnews/6661.htm
- http://m.wap.oexnr.cn/jnews/7618.htm
- http://m.wap.oexnr.cn/jnews/15849.htm
- http://m.wap.oexnr.cn/jnews/450147.htm
- http://m.wap.oexnr.cn/jnews/15719.htm
- http://m.wap.oexnr.cn/jnews/31010.htm
- http://m.wap.oexnr.cn/jnews/5439216.htm
- http://m.wap.oexnr.cn/jnews/159424.htm
- http://m.wap.oexnr.cn/jnews/84840.htm
- http://m.wap.oexnr.cn/jnews/3247797.htm
- http://m.wap.oexnr.cn/jnews/4443561.htm
- http://m.wap.oexnr.cn/jnews/2852.htm
- http://m.wap.oexnr.cn/jnews/34718.htm
- http://m.wap.oexnr.cn/jnews/049887.htm
- http://m.wap.oexnr.cn/jnews/8358.htm
- http://m.wap.oexnr.cn/jnews/424397.htm
- http://m.wap.oexnr.cn/jnews/08502.htm
- http://m.wap.oexnr.cn/jnews/3139032.htm
- http://m.wap.oexnr.cn/jnews/7049211.htm
- http://m.wap.oexnr.cn/jnews/8670.htm
- http://m.wap.oexnr.cn/jnews/0673.htm
- http://m.wap.oexnr.cn/jnews/3588.htm
- http://m.wap.oexnr.cn/jnews/8303.htm
- http://m.wap.oexnr.cn/jnews/1243166.htm
- http://m.wap.oexnr.cn/jnews/5788172.htm
- http://m.wap.oexnr.cn/jnews/2315.htm
- http://m.wap.oexnr.cn/jnews/027448.htm
- http://m.wap.oexnr.cn/jnews/14774.htm
- http://m.wap.oexnr.cn/jnews/1243779.htm
- http://m.wap.oexnr.cn/jnews/6326439.htm
- http://m.wap.oexnr.cn/jnews/1174232.htm
- http://m.wap.oexnr.cn/jnews/0656928.htm
- http://m.wap.oexnr.cn/jnews/3291.htm
- http://m.wap.oexnr.cn/jnews/5326906.htm
- http://m.wap.oexnr.cn/jnews/824957.htm
- http://m.wap.oexnr.cn/jnews/312625.htm
- http://m.wap.oexnr.cn/jnews/8355043.htm
- http://m.wap.oexnr.cn/jnews/4007.htm
- http://m.wap.oexnr.cn/jnews/68895.htm
- http://m.wap.oexnr.cn/jnews/1261.htm
- http://m.wap.oexnr.cn/jnews/45139.htm
- http://m.wap.oexnr.cn/jnews/1333658.htm
- http://m.wap.oexnr.cn/jnews/6119.htm
- http://m.wap.oexnr.cn/jnews/349016.htm
- http://m.wap.oexnr.cn/jnews/1560.htm
- http://m.wap.oexnr.cn/jnews/04158.htm
- http://m.wap.oexnr.cn/jnews/34440.htm
- http://m.wap.oexnr.cn/jnews/0818.htm
- http://m.wap.oexnr.cn/jnews/1233571.htm
- http://m.wap.oexnr.cn/jnews/962569.htm
- http://m.wap.oexnr.cn/jnews/3902.htm
- http://m.wap.oexnr.cn/jnews/2292514.htm
- http://m.wap.oexnr.cn/jnews/281979.htm
- http://m.wap.oexnr.cn/jnews/6781.htm

## 项目结构

```
newsindex-aggregate/
├── run.py                           # 项目主入口，处理命令行参数与流程调度
├── config.yaml                      # 全局配置文件，定义分类规则与输出路径
├── requirements.txt                 # Python 依赖声明
├── README.md                        # 项目说明文档
├── LICENSE                          # MIT 许可证文件
├── src/                             # 核心源代码目录
│   ├── __init__.py                  # 包初始化
│   ├── cli.py                       # 命令行接口实现
│   ├── parser.py                    # URL 解析与校验模块
│   ├── indexer.py                   # 索引构建与更新核心逻辑
│   ├── exporter.py                  # 多格式导出模块
│   └── utils.py                     # 通用工具函数集合
├── tests/                           # 单元测试与集成测试目录
│   ├── test_parser.py               # 解析模块测试用例
│   ├── test_indexer.py              # 索引模块测试用例
│   └── test_exporter.py             # 导出模块测试用例
├── docs/                            # 文档目录
│   ├── user-guide.md                # 用户使用手册
│   ├── config-reference.md          # 配置参考文档
│   ├── developer-guide.md           # 开发者指南
│   └── api.md                       # API 接口文档
├── samples/                         # 示例文件目录
│   ├── urls.txt                     # 示例 URL 列表
│   └── output.json                  # 示例输出文件
└── data/                            # 运行时数据存储目录（自动创建）
    ├── index.json                   # 主索引文件
    └── archive/                     # 历史归档目录
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库，并将 fork 后的仓库克隆到本地开发环境。
2. 创建新的功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 的格式。
3. 提交代码前运行测试套件确保所有现有功能正常，新增功能需补充对应的单元测试。
4. 提交 pull request 到主仓库的 main 分支，并在描述中清晰说明改动目的与影响范围。
5. 代码审查通过后由项目维护者合并，合并后贡献者将列入项目贡献者列表。

## 常见问题

Q: 本项目是否包含新闻内容的抓取与存储功能？

A: 不包含。本项目仅处理新闻页面的 URL 链接本身，不涉及任何网页内容抓取、存储或展示功能。用户需自行负责内容获取的合规性。

Q: 如何导入自定义的 URL 列表？

A: 在项目根目录下创建一个纯文本文件，每行写入一个 URL，然后使用 `--input` 参数指定该文件路径运行 `run.py` 即可。项目会自动进行格式校验与索引构建。

Q: 索引文件支持增量更新吗？

A: 支持。在配置文件中开启增量模式后，再次导入时会自动比对现有索引，仅添加新 URL 并记录变更时间，不会覆盖已有的元数据标注。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
