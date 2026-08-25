# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与新闻外链管理的轻量级开源工具，定位于为开发者、内容创作者及小型媒体团队提供统一的新闻链接收集、分类与分发能力。该工具通过解析标准化的新闻索引页面，将散落在各个源站的新闻条目转化为可检索、可导出的结构化数据集，从而解决资讯采编过程中多源数据整合效率低、外链管理混乱以及人工录入错误率高的痛点。

本项目不依赖重型框架，核心逻辑采用 Python 实现，支持命令行交互与定时任务调度，能够在低资源环境下稳定运行。NewsLink Aggregator 适用于需要定期从特定新闻门户抓取更新列表、进行链接有效性检测以及生成日报摘要的自动化场景。

## 功能概览

批量链接抽取 从指定新闻索引页面中自动识别并提取符合规则的外链列表，支持分页与增量更新。

链接状态检测 对抽取得到的每个链接进行 HTTP 状态码校验，自动标记死链、重定向及异常响应。

内容摘要生成 对目标新闻页面进行标题与正文首段的智能提取，生成可用于日报的短摘要信息。

分类标签管理 基于 URL 路径模式或关键词规则，为每条外链自动打上分类标签，便于后续检索。

数据导出格式支持 支持将处理后的链接数据导出为 CSV、JSON 以及 Markdown 表格三种常用格式。

定时任务集成 内置 cron 表达式解析器，可配置定时抓取与检测任务，适用于自动化运维场景。

增量去重机制 基于链接 URL 与标题哈希的复合去重策略，避免重复收录相同新闻条目。

日志审计 提供分级日志记录系统，支持输出处理流水线中每个环节的详细执行记录。

## 应用场景

自媒体内容采编 内容创作者在每日早报撰写过程中，可利用 NewsLink Aggregator 快速采集多个新闻源的最新链接，并自动生成包含标题和摘要的素材列表，显著减少手动复制粘贴的时间。

新闻聚合站运营 小型新闻聚合站点管理员可通过定时任务，每半小时拉取一次目标新闻页面的外链更新，结合去重机制后将新增链接推送至前端数据库，实现近乎实时的内容同步。

链接有效性监控 运维人员可使用该工具对历史新闻外链进行周期性巡检，获取死链报告，并及时通知内容编辑修正或移除失效链接，提升站点用户体验。

数据归档与迁移 在进行网站改版或数据迁移时，利用 NewsLink Aggregator 批量导出原始新闻链接及其元数据，生成标准化的 CSV 对照表，便于在新系统中批量导入。

## 快速开始

以下命令序列演示了从代码仓库克隆、安装依赖到首次运行抓取任务的全过程。

```bash
git clone https://github.com/tech-archive/news-aggregator.git
cd news-aggregator
pip install -r requirements.txt
python main.py --source http://m.3g.oexnr.cn/nnews/1247.htm --output result.json
```

如需执行批量链接检测，可使用以下命令：

```bash
python checker.py --input urls.txt --timeout 5 --retry 2
```

若配置定时任务，可参考以下 crontab 示例（每天凌晨 2 点执行全量更新）：

```bash
0 2 * * * cd /opt/news-aggregator && python main.py --source http://m.3g.oexnr.cn/nnews/1247.htm --output /data/daily.json --cron
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.8 及以上 | 核心运行环境，建议使用 3.10 长期支持版本 |
| requests | 2.28.0 及以上 | 处理 HTTP 请求与响应，支持重定向与超时控制 |
| beautifulsoup4 | 4.11.0 及以上 | 用于解析 HTML 文档结构，提取链接与文本内容 |
| lxml | 4.9.0 及以上 | 作为 beautifulsoup4 的解析器后端，提供高性能 XML/HTML 解析能力 |
| python-crontab | 2.6.0 及以上 | 提供定时任务配置与写入系统 crontab 的接口 |
| pytest | 7.2.0 及以上 | 单元测试框架，仅在开发环境中使用 |
| black | 22.3.0 及以上 | 代码格式化工具，仅在开发环境中使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速安装并完成第一次抓取任务；如何理解项目的主配置文件结构 |
| 配置参考 | docs/configuration.md | 所有可用的命令行参数及其对应配置文件字段的含义与默认值 |
| API 文档 | docs/api.md | 各核心模块（抓取器、检测器、摘要生成器）的类与方法详细说明 |
| 运维手册 | docs/operations.md | 如何部署定时任务、如何查看日志、如何进行数据备份与恢复 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/1247.htm
- http://m.3g.oexnr.cn/nnews/661523.htm
- http://m.3g.oexnr.cn/nnews/3769.htm
- http://m.3g.oexnr.cn/nnews/9077.htm
- http://m.3g.oexnr.cn/nnews/8693686.htm
- http://m.3g.oexnr.cn/nnews/7805.htm
- http://m.3g.oexnr.cn/nnews/982194.htm
- http://m.3g.oexnr.cn/nnews/4429841.htm
- http://m.3g.oexnr.cn/nnews/124591.htm
- http://m.3g.oexnr.cn/nnews/94506.htm
- http://m.3g.oexnr.cn/nnews/951178.htm
- http://m.3g.oexnr.cn/nnews/2018980.htm
- http://m.3g.oexnr.cn/nnews/3336833.htm
- http://m.3g.oexnr.cn/nnews/6497.htm
- http://m.3g.oexnr.cn/nnews/1654.htm
- http://m.3g.oexnr.cn/nnews/9303342.htm
- http://m.3g.oexnr.cn/nnews/381820.htm
- http://m.3g.oexnr.cn/nnews/4963383.htm
- http://m.3g.oexnr.cn/nnews/448179.htm
- http://m.3g.oexnr.cn/nnews/8798565.htm
- http://m.3g.oexnr.cn/nnews/195750.htm
- http://m.3g.oexnr.cn/nnews/9397754.htm
- http://m.3g.oexnr.cn/nnews/7851.htm
- http://m.3g.oexnr.cn/nnews/2438.htm
- http://m.3g.oexnr.cn/nnews/74117.htm
- http://m.3g.oexnr.cn/nnews/9030832.htm
- http://m.3g.oexnr.cn/nnews/544845.htm
- http://m.3g.oexnr.cn/nnews/772707.htm
- http://m.3g.oexnr.cn/nnews/967323.htm
- http://m.3g.oexnr.cn/nnews/5535825.htm
- http://m.3g.oexnr.cn/nnews/31394.htm
- http://m.3g.oexnr.cn/nnews/5962845.htm
- http://m.3g.oexnr.cn/nnews/283814.htm
- http://m.3g.oexnr.cn/nnews/8672.htm
- http://m.3g.oexnr.cn/nnews/5159924.htm
- http://m.3g.oexnr.cn/nnews/848475.htm
- http://m.3g.oexnr.cn/nnews/7974.htm
- http://m.3g.oexnr.cn/nnews/6025675.htm
- http://m.3g.oexnr.cn/nnews/996899.htm
- http://m.3g.oexnr.cn/nnews/1664048.htm
- http://m.3g.oexnr.cn/nnews/3126741.htm
- http://m.3g.oexnr.cn/nnews/33846.htm
- http://m.3g.oexnr.cn/nnews/04894.htm
- http://m.3g.oexnr.cn/nnews/9403039.htm
- http://m.3g.oexnr.cn/nnews/293984.htm
- http://m.3g.oexnr.cn/nnews/3282219.htm
- http://m.3g.oexnr.cn/nnews/9396622.htm
- http://m.3g.oexnr.cn/nnews/2371.htm
- http://m.3g.oexnr.cn/nnews/3503063.htm
- http://m.3g.oexnr.cn/nnews/641324.htm
- http://m.3g.oexnr.cn/nnews/8623005.htm
- http://m.3g.oexnr.cn/nnews/433275.htm
- http://m.3g.oexnr.cn/nnews/28895.htm
- http://m.3g.oexnr.cn/nnews/1316408.htm
- http://m.3g.oexnr.cn/nnews/839303.htm
- http://m.3g.oexnr.cn/nnews/8140.htm
- http://m.3g.oexnr.cn/nnews/423363.htm
- http://m.3g.oexnr.cn/nnews/6420456.htm
- http://m.3g.oexnr.cn/nnews/50427.htm
- http://m.3g.oexnr.cn/nnews/1138.htm
- http://m.3g.oexnr.cn/nnews/60645.htm
- http://m.3g.oexnr.cn/nnews/298845.htm
- http://m.3g.oexnr.cn/nnews/0285439.htm
- http://m.3g.oexnr.cn/nnews/0043.htm
- http://m.3g.oexnr.cn/nnews/65983.htm
- http://m.3g.oexnr.cn/nnews/6706.htm
- http://m.3g.oexnr.cn/nnews/9531.htm
- http://m.3g.oexnr.cn/nnews/75851.htm
- http://m.3g.oexnr.cn/nnews/914969.htm
- http://m.3g.oexnr.cn/nnews/155875.htm
- http://m.3g.oexnr.cn/nnews/7720265.htm
- http://m.3g.oexnr.cn/nnews/45841.htm
- http://m.3g.oexnr.cn/nnews/537419.htm
- http://m.3g.oexnr.cn/nnews/97371.htm
- http://m.3g.oexnr.cn/nnews/503465.htm
- http://m.3g.oexnr.cn/nnews/165860.htm
- http://m.3g.oexnr.cn/nnews/3043.htm
- http://m.3g.oexnr.cn/nnews/4399.htm
- http://m.3g.oexnr.cn/nnews/50074.htm
- http://m.3g.oexnr.cn/nnews/6191.htm
- http://m.3g.oexnr.cn/nnews/7095768.htm
- http://m.3g.oexnr.cn/nnews/537671.htm
- http://m.3g.oexnr.cn/nnews/11310.htm
- http://m.3g.oexnr.cn/nnews/8652597.htm
- http://m.3g.oexnr.cn/nnews/2019.htm
- http://m.3g.oexnr.cn/nnews/735870.htm
- http://m.3g.oexnr.cn/nnews/799446.htm
- http://m.3g.oexnr.cn/nnews/4241.htm
- http://m.3g.oexnr.cn/nnews/8890427.htm
- http://m.3g.oexnr.cn/nnews/05955.htm
- http://m.3g.oexnr.cn/nnews/401511.htm
- http://m.3g.oexnr.cn/nnews/071097.htm
- http://m.3g.oexnr.cn/nnews/9700292.htm
- http://m.3g.oexnr.cn/nnews/9195943.htm
- http://m.3g.oexnr.cn/nnews/026948.htm
- http://m.3g.oexnr.cn/nnews/7410446.htm
- http://m.3g.oexnr.cn/nnews/29398.htm
- http://m.3g.oexnr.cn/nnews/6068.htm
- http://m.3g.oexnr.cn/nnews/123603.htm
- http://m.3g.oexnr.cn/nnews/592979.htm
- http://m.3g.oexnr.cn/nnews/97965.htm
- http://m.3g.oexnr.cn/nnews/84567.htm
- http://m.3g.oexnr.cn/nnews/6957.htm
- http://m.3g.oexnr.cn/nnews/918552.htm
- http://m.3g.oexnr.cn/nnews/9472.htm
- http://m.3g.oexnr.cn/nnews/9766315.htm
- http://m.3g.oexnr.cn/nnews/6229.htm
- http://m.3g.oexnr.cn/nnews/1034620.htm
- http://m.3g.oexnr.cn/nnews/3520887.htm
- http://m.3g.oexnr.cn/nnews/9654439.htm
- http://m.3g.oexnr.cn/nnews/8922013.htm
- http://m.3g.oexnr.cn/nnews/8010031.htm
- http://m.3g.oexnr.cn/nnews/8571.htm
- http://m.3g.oexnr.cn/nnews/8651096.htm
- http://m.3g.oexnr.cn/nnews/4213615.htm
- http://m.3g.oexnr.cn/nnews/93520.htm
- http://m.3g.oexnr.cn/nnews/55446.htm
- http://m.3g.oexnr.cn/nnews/12719.htm
- http://m.3g.oexnr.cn/nnews/7516049.htm
- http://m.3g.oexnr.cn/nnews/324809.htm
- http://m.3g.oexnr.cn/nnews/1904280.htm
- http://m.3g.oexnr.cn/nnews/71524.htm
- http://m.3g.oexnr.cn/nnews/8563.htm
- http://m.3g.oexnr.cn/nnews/20605.htm
- http://m.3g.oexnr.cn/nnews/3151062.htm
- http://m.3g.oexnr.cn/nnews/856174.htm
- http://m.3g.oexnr.cn/nnews/8705.htm
- http://m.3g.oexnr.cn/nnews/69505.htm
- http://m.3g.oexnr.cn/nnews/367914.htm
- http://m.3g.oexnr.cn/nnews/19400.htm
- http://m.3g.oexnr.cn/nnews/4873.htm
- http://m.3g.oexnr.cn/nnews/05539.htm
- http://m.3g.oexnr.cn/nnews/6598.htm
- http://m.3g.oexnr.cn/nnews/46060.htm
- http://m.3g.oexnr.cn/nnews/91122.htm
- http://m.3g.oexnr.cn/nnews/4840.htm
- http://m.3g.oexnr.cn/nnews/8566.htm
- http://m.3g.oexnr.cn/nnews/75751.htm
- http://m.3g.oexnr.cn/nnews/202978.htm
- http://m.3g.oexnr.cn/nnews/622664.htm
- http://m.3g.oexnr.cn/nnews/74829.htm
- http://m.3g.oexnr.cn/nnews/629360.htm
- http://m.3g.oexnr.cn/nnews/7868616.htm
- http://m.3g.oexnr.cn/nnews/6860.htm
- http://m.3g.oexnr.cn/nnews/8114.htm
- http://m.3g.oexnr.cn/nnews/778062.htm
- http://m.3g.oexnr.cn/nnews/07670.htm
- http://m.3g.oexnr.cn/nnews/8281.htm
- http://m.3g.oexnr.cn/nnews/779280.htm
- http://m.3g.oexnr.cn/nnews/8621735.htm
- http://m.3g.oexnr.cn/nnews/4694.htm
- http://m.3g.oexnr.cn/nnews/88833.htm
- http://m.3g.oexnr.cn/nnews/4831.htm
- http://m.3g.oexnr.cn/nnews/78778.htm
- http://m.3g.oexnr.cn/nnews/7332841.htm
- http://m.3g.oexnr.cn/nnews/2059933.htm
- http://m.3g.oexnr.cn/nnews/139872.htm
- http://m.3g.oexnr.cn/nnews/5389071.htm
- http://m.3g.oexnr.cn/nnews/8171437.htm
- http://m.3g.oexnr.cn/nnews/3527050.htm
- http://m.3g.oexnr.cn/nnews/5867547.htm
- http://m.3g.oexnr.cn/nnews/337339.htm
- http://m.3g.oexnr.cn/nnews/068209.htm
- http://m.3g.oexnr.cn/nnews/5187.htm
- http://m.3g.oexnr.cn/nnews/67941.htm
- http://m.3g.oexnr.cn/nnews/9103.htm
- http://m.3g.oexnr.cn/nnews/7104.htm
- http://m.3g.oexnr.cn/nnews/6513.htm
- http://m.3g.oexnr.cn/nnews/24451.htm
- http://m.3g.oexnr.cn/nnews/475253.htm
- http://m.3g.oexnr.cn/nnews/651901.htm
- http://m.3g.oexnr.cn/nnews/4125949.htm
- http://m.3g.oexnr.cn/nnews/183043.htm
- http://m.3g.oexnr.cn/nnews/59226.htm
- http://m.3g.oexnr.cn/nnews/6579.htm
- http://m.3g.oexnr.cn/nnews/411635.htm
- http://m.3g.oexnr.cn/nnews/136397.htm
- http://m.3g.oexnr.cn/nnews/423524.htm
- http://m.3g.oexnr.cn/nnews/706721.htm
- http://m.3g.oexnr.cn/nnews/394215.htm
- http://m.3g.oexnr.cn/nnews/523749.htm
- http://m.3g.oexnr.cn/nnews/3745139.htm
- http://m.3g.oexnr.cn/nnews/6545591.htm
- http://m.3g.oexnr.cn/nnews/4927.htm
- http://m.3g.oexnr.cn/nnews/020258.htm
- http://m.3g.oexnr.cn/nnews/6073510.htm
- http://m.3g.oexnr.cn/nnews/7251.htm
- http://m.3g.oexnr.cn/nnews/3348.htm
- http://m.3g.oexnr.cn/nnews/3528.htm
- http://m.3g.oexnr.cn/nnews/37892.htm
- http://m.3g.oexnr.cn/nnews/230744.htm
- http://m.3g.oexnr.cn/nnews/78054.htm
- http://m.3g.oexnr.cn/nnews/05450.htm
- http://m.3g.oexnr.cn/nnews/5902168.htm
- http://m.3g.oexnr.cn/nnews/2647594.htm
- http://m.3g.oexnr.cn/nnews/5950136.htm
- http://m.3g.oexnr.cn/nnews/133007.htm
- http://m.3g.oexnr.cn/nnews/36346.htm
- http://m.3g.oexnr.cn/nnews/32648.htm
- http://m.3g.oexnr.cn/nnews/379660.htm
- http://m.3g.oexnr.cn/nnews/0878960.htm
- http://m.3g.oexnr.cn/nnews/7503.htm
- http://m.3g.oexnr.cn/nnews/2900.htm
- http://m.3g.oexnr.cn/nnews/731867.htm
- http://m.3g.oexnr.cn/nnews/4271.htm
- http://m.3g.oexnr.cn/nnews/787559.htm
- http://m.3g.oexnr.cn/nnews/7694.htm
- http://m.3g.oexnr.cn/nnews/1479660.htm
- http://m.3g.oexnr.cn/nnews/8691.htm
- http://m.3g.oexnr.cn/nnews/17233.htm
- http://m.3g.oexnr.cn/nnews/4517.htm
- http://m.3g.oexnr.cn/nnews/6336.htm
- http://m.3g.oexnr.cn/nnews/698375.htm
- http://m.3g.oexnr.cn/nnews/870465.htm
- http://m.3g.oexnr.cn/nnews/04614.htm
- http://m.3g.oexnr.cn/nnews/7135119.htm
- http://m.3g.oexnr.cn/nnews/419550.htm
- http://m.3g.oexnr.cn/nnews/7619033.htm
- http://m.3g.oexnr.cn/nnews/3080324.htm
- http://m.3g.oexnr.cn/nnews/96540.htm
- http://m.3g.oexnr.cn/nnews/972813.htm
- http://m.3g.oexnr.cn/nnews/43293.htm
- http://m.3g.oexnr.cn/nnews/57322.htm
- http://m.3g.oexnr.cn/nnews/7320.htm
- http://m.3g.oexnr.cn/nnews/4059.htm
- http://m.3g.oexnr.cn/nnews/0977937.htm
- http://m.3g.oexnr.cn/nnews/5182453.htm
- http://m.3g.oexnr.cn/nnews/43259.htm
- http://m.3g.oexnr.cn/nnews/8002736.htm
- http://m.3g.oexnr.cn/nnews/254997.htm
- http://m.3g.oexnr.cn/nnews/577038.htm
- http://m.3g.oexnr.cn/nnews/245196.htm
- http://m.3g.oexnr.cn/nnews/288568.htm
- http://m.3g.oexnr.cn/nnews/84760.htm
- http://m.3g.oexnr.cn/nnews/4052660.htm
- http://m.3g.oexnr.cn/nnews/32666.htm
- http://m.3g.oexnr.cn/nnews/4971.htm
- http://m.3g.oexnr.cn/nnews/09005.htm
- http://m.3g.oexnr.cn/nnews/10893.htm
- http://m.3g.oexnr.cn/nnews/6003.htm
- http://m.3g.oexnr.cn/nnews/69387.htm
- http://m.3g.oexnr.cn/nnews/2333.htm
- http://m.3g.oexnr.cn/nnews/88288.htm
- http://m.3g.oexnr.cn/nnews/486057.htm
- http://m.3g.oexnr.cn/nnews/1958.htm
- http://m.3g.oexnr.cn/nnews/37491.htm
- http://m.3g.oexnr.cn/nnews/8831984.htm
- http://m.3g.oexnr.cn/nnews/0027612.htm
- http://m.3g.oexnr.cn/nnews/654420.htm
- http://m.3g.oexnr.cn/nnews/89258.htm
- http://m.3g.oexnr.cn/nnews/70429.htm
- http://m.3g.oexnr.cn/nnews/2505.htm
- http://m.3g.oexnr.cn/nnews/3605578.htm
- http://m.3g.oexnr.cn/nnews/4176.htm
- http://m.3g.oexnr.cn/nnews/7758818.htm
- http://m.3g.oexnr.cn/nnews/304779.htm
- http://m.3g.oexnr.cn/nnews/2445998.htm
- http://m.3g.oexnr.cn/nnews/9368251.htm
- http://m.3g.oexnr.cn/nnews/0663.htm
- http://m.3g.oexnr.cn/nnews/3393754.htm
- http://m.3g.oexnr.cn/nnews/611948.htm
- http://m.3g.oexnr.cn/nnews/10008.htm
- http://m.3g.oexnr.cn/nnews/1047.htm
- http://m.3g.oexnr.cn/nnews/526088.htm
- http://m.3g.oexnr.cn/nnews/368129.htm
- http://m.3g.oexnr.cn/nnews/8387510.htm
- http://m.3g.oexnr.cn/nnews/0025509.htm
- http://m.3g.oexnr.cn/nnews/23077.htm
- http://m.3g.oexnr.cn/nnews/75860.htm
- http://m.3g.oexnr.cn/nnews/0945.htm
- http://m.3g.oexnr.cn/nnews/670965.htm
- http://m.3g.oexnr.cn/nnews/2467.htm
- http://m.3g.oexnr.cn/nnews/7493.htm
- http://m.3g.oexnr.cn/nnews/5471093.htm
- http://m.3g.oexnr.cn/nnews/1455.htm
- http://m.3g.oexnr.cn/nnews/3456.htm
- http://m.3g.oexnr.cn/nnews/282039.htm
- http://m.3g.oexnr.cn/nnews/502880.htm
- http://m.3g.oexnr.cn/nnews/9356.htm
- http://m.3g.oexnr.cn/nnews/1732.htm
- http://m.3g.oexnr.cn/nnews/652409.htm
- http://m.3g.oexnr.cn/nnews/28409.htm
- http://m.3g.oexnr.cn/nnews/6042144.htm
- http://m.3g.oexnr.cn/nnews/076186.htm
- http://m.3g.oexnr.cn/nnews/7605.htm
- http://m.3g.oexnr.cn/nnews/307496.htm
- http://m.3g.oexnr.cn/nnews/623949.htm
- http://m.3g.oexnr.cn/nnews/45558.htm
- http://m.3g.oexnr.cn/nnews/919395.htm
- http://m.3g.oexnr.cn/nnews/2004.htm
- http://m.3g.oexnr.cn/nnews/0434864.htm
- http://m.3g.oexnr.cn/nnews/4782764.htm
- http://m.3g.oexnr.cn/nnews/688274.htm
- http://m.3g.oexnr.cn/nnews/1573.htm
- http://m.3g.oexnr.cn/nnews/44900.htm
- http://m.3g.oexnr.cn/nnews/6023.htm
- http://m.3g.oexnr.cn/nnews/5372.htm
- http://m.3g.oexnr.cn/nnews/67457.htm
- http://m.3g.oexnr.cn/nnews/392239.htm
- http://m.3g.oexnr.cn/nnews/0789355.htm

## 项目结构

```
news-aggregator/
├── main.py                     # 程序入口，解析命令行参数并调度核心流程
├── checker.py                  # 链接状态检测模块，独立运行或由主流程调用
├── requirements.txt            # 生产环境依赖列表，固定所有第三方库版本
├── config/
│   ├── settings.yaml           # 主配置文件，包含抓取间隔、超时、重试策略等
│   └── sources.list            # 新闻源索引文件，每行一个基础 URL
├── core/
│   ├── fetcher.py              # 页面抓取器，封装 requests 与重试逻辑
│   ├── parser.py               # HTML 解析器，基于 beautifulsoup4 实现链接与文本提取
│   ├── deduper.py              # 增量去重器，维护已处理链接的哈希集合
│   └── exporter.py             # 数据导出器，支持 CSV / JSON / Markdown 格式
├── utils/
│   ├── logger.py               # 日志工具，支持文件轮转与分级输出
│   ├── cron_helper.py          # 定时任务辅助函数，用于写入和删除 crontab 条目
│   └── validators.py           # URL 合法性校验与规范化工具函数
├── tests/
│   ├── test_fetcher.py         # 抓取器单元测试，包含 mock 响应
│   ├── test_parser.py          # 解析器单元测试，覆盖各类 HTML 结构
│   └── test_deduper.py         # 去重器单元测试，验证哈希碰撞处理
├── docs/
│   ├── getting-started.md      # 入门指南，含安装与首次运行示例
│   ├── configuration.md        # 完整配置项说明与参数调优建议
│   ├── api.md                  # 模块 API 参考文档，由 Sphinx 自动生成
│   └── operations.md           # 运维手册，包含日志分析、性能监控与故障排查
└── LICENSE                     # MIT 许可证文件
```

## 贡献指南

1. 阅读项目文档与代码风格规范。在提交代码前，请仔细阅读 docs/ 目录下的入门指南与 API 文档，并确保代码符合 PEP 8 风格规范。使用 black 工具进行自动格式化，行宽限制为 88 字符。

2. 提交 Issue 讨论新功能或缺陷修复。对于较大规模的特性开发，建议先在 GitHub Issues 中创建讨论帖，说明设计思路与实现方案，获得核心维护者反馈后再进行编码，避免无效工作。

3. 创建特性分支并编写单元测试。请基于最新的 main 分支创建以 feature/ 或 fix/ 为前缀的分支名称。所有新增功能或缺陷修复必须包含对应的单元测试用例，且测试覆盖率不得低于 85%。

4. 发起 Pull Request 并等待代码审查。PR 标题应简明扼要概括变更内容，描述中需关联对应的 Issue 编号。至少需要一名项目维护者批准后方可合并，CI 流水线中的所有检查（包括测试、格式化、静态分析）必须全部通过。

5. 更新文档与示例配置。当变更涉及配置项、命令行参数或公共 API 时，必须同步更新 docs/ 目录下的相关文档以及 config/settings.yaml 中的示例配置，确保文档与代码保持一致。

## 常见问题

Q: 抓取过程中出现 HTTP 429 或 503 状态码应如何处理？
A: 此类状态码通常表示目标服务器限流或临时过载。本项目内置了指数退避重试策略，默认重试 3 次，间隔分别为 2 秒、4 秒、8 秒。若持续失败，建议调整 config/settings.yaml 中的 retry_times 与 backoff_factor 参数，或增加 time.sleep 间隔。同时可开启 checker.py 中的 --slow 模式，将请求间隔延长至 5 秒以上。

Q: 如何将每日抓取结果自动发送至电子邮件或即时通讯工具？
A: 项目本身不内置消息推送模块，但支持通过 --output 参数导出 JSON 文件。用户可以自行编写外部脚本（例如使用 sendmail 或 curl 调用 Webhook 接口）读取导出的 JSON 文件，并将其内容格式化后发送。建议将外部脚本与 main.py 一同写入 crontab 定时任务中，实现完整的自动化通知链路。

Q: 增量去重机制是否支持跨多个新闻源的去重？
A: 支持。去重器基于 URL 绝对路径与标题文本的 SHA-256 哈希组合进行判定。当配置文件中 dedup_scope 字段设置为 global 时，所有来源的链接将共享同一个哈希集合，从而实现跨源去重。若设置为 source，则每个新闻源单独维护去重集合，适用于同一链接在不同源中表示不同内容的特殊场景。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
