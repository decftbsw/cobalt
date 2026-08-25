# WebIndex Pro

WebIndex Pro 是一个面向技术研究者和信息分析人员的结构化外链资源聚合系统。该项目通过对分散于互联网各处的新闻资讯、技术博客及行业动态链接进行统一采集、分类与索引，构建可快速检索与追溯的外链资源库。项目定位于轻量级信息中台，适用于需要定期追踪特定域名下内容更新、进行批量链接归档或搭建自定义资讯聚合页面的场景。

## 功能概览

- 批量链接采集：支持对指定域名下多组数字ID路径的资源进行并发拉取，自动解析HTML元数据与正文摘要。
- 结构化存储：将每条链接的标题、发布时间、来源域名及内容哈希以JSONL格式落盘，便于后续导入数据库或数据分析流水线。
- 去重与状态检测：内置基于内容指纹的URL去重机制，并支持对已收录链接进行HTTP状态码巡检，标注失效或重定向资源。
- 正则路径过滤：允许用户通过正则表达式筛选特定模式（如 `/nnews/` 前缀加数字ID）的链接，精准控制采集范围。
- 索引快照导出：支持将当前索引库导出为静态HTML目录页或Markdown表格，方便内部分享与离线查阅。
- 增量更新模式：支持基于上次采集时间戳的增量抓取，避免重复处理历史链接，降低源站请求压力。
- 标签分类系统：允许用户为每个链接手动或自动打标（如“技术前沿”、“行业政策”、“数据报告”），实现主题维度聚合。

## 应用场景

- 技术情报每日汇总：研究人员可配置定时任务，每日清晨自动拉取指定资讯站点下的最新文章链接，生成当日情报简报。
- 竞品动态追踪：产品分析团队将竞品官方新闻发布页的链接模式纳入监控，当出现新的数字ID路径时自动触发告警通知。
- 历史资料归档整理：内容运营人员将分散在多个年份、多批次导出列表中的链接统一导入本系统，形成可检索的企业知识库外链索引。

## 快速开始

以下指令适用于 Linux / macOS 系统，需预先安装 Git 与 Python 3.9 及以上版本。

```bash
git clone https://github.com/webindex-pro/webindex-core.git
cd webindex-core
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
python cli.py collect --domain m.blog.ghtkgg.cn --path-pattern "/nnews/*" --output ./data/index.jsonl
```

执行完成后，采集结果将写入 `./data/index.jsonl`，每行为一个JSON对象，包含 `url`、`fetched_at`、`status` 等字段。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，3.12 及以上暂未完全兼容 |
| Git | 2.25 以上 | 用于克隆仓库及版本管理 |
| pip | 21.0 以上 | Python 包依赖管理工具 |
| virtualenv | 可选 | 推荐使用 venv 模块创建隔离环境 |
| curl | 7.68 以上 | 部分底层健康检查脚本依赖 curl 执行轻量探测 |
| SQLite | 3.31 以上 | 用于本地索引缓存与去重存储（无需额外安装） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/quickstart.md | 如何快速完成首次采集并生成索引报告 |
| 配置参考 | docs/configuration.md | 采集并发数、超时时间、重试策略等参数详解 |
| API 接口 | docs/api.md | 如何通过 HTTP API 对外提供查询与统计服务 |
| 运维手册 | docs/operations.md | 日志轮转、数据备份及异常恢复流程 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/237785.htm
- http://m.blog.ghtkgg.cn/nnews/510469.htm
- http://m.blog.ghtkgg.cn/nnews/064378.htm
- http://m.blog.ghtkgg.cn/nnews/62946.htm
- http://m.blog.ghtkgg.cn/nnews/4016483.htm
- http://m.blog.ghtkgg.cn/nnews/88525.htm
- http://m.blog.ghtkgg.cn/nnews/1513.htm
- http://m.blog.ghtkgg.cn/nnews/0551096.htm
- http://m.blog.ghtkgg.cn/nnews/1848.htm
- http://m.blog.ghtkgg.cn/nnews/10943.htm
- http://m.blog.ghtkgg.cn/nnews/2781.htm
- http://m.blog.ghtkgg.cn/nnews/338784.htm
- http://m.blog.ghtkgg.cn/nnews/2491.htm
- http://m.blog.ghtkgg.cn/nnews/14192.htm
- http://m.blog.ghtkgg.cn/nnews/4853.htm
- http://m.blog.ghtkgg.cn/nnews/4542022.htm
- http://m.blog.ghtkgg.cn/nnews/4226818.htm
- http://m.blog.ghtkgg.cn/nnews/833249.htm
- http://m.blog.ghtkgg.cn/nnews/981656.htm
- http://m.blog.ghtkgg.cn/nnews/7569.htm
- http://m.blog.ghtkgg.cn/nnews/0756784.htm
- http://m.blog.ghtkgg.cn/nnews/05742.htm
- http://m.blog.ghtkgg.cn/nnews/4803.htm
- http://m.blog.ghtkgg.cn/nnews/7464307.htm
- http://m.blog.ghtkgg.cn/nnews/638497.htm
- http://m.blog.ghtkgg.cn/nnews/6194584.htm
- http://m.blog.ghtkgg.cn/nnews/8733210.htm
- http://m.blog.ghtkgg.cn/nnews/984292.htm
- http://m.blog.ghtkgg.cn/nnews/04322.htm
- http://m.blog.ghtkgg.cn/nnews/723854.htm
- http://m.blog.ghtkgg.cn/nnews/10968.htm
- http://m.blog.ghtkgg.cn/nnews/524889.htm
- http://m.blog.ghtkgg.cn/nnews/08443.htm
- http://m.blog.ghtkgg.cn/nnews/70153.htm
- http://m.blog.ghtkgg.cn/nnews/42030.htm
- http://m.blog.ghtkgg.cn/nnews/008111.htm
- http://m.blog.ghtkgg.cn/nnews/545576.htm
- http://m.blog.ghtkgg.cn/nnews/0665.htm
- http://m.blog.ghtkgg.cn/nnews/32311.htm
- http://m.blog.ghtkgg.cn/nnews/67465.htm
- http://m.blog.ghtkgg.cn/nnews/8146202.htm
- http://m.blog.ghtkgg.cn/nnews/72526.htm
- http://m.blog.ghtkgg.cn/nnews/4511.htm
- http://m.blog.ghtkgg.cn/nnews/5938.htm
- http://m.blog.ghtkgg.cn/nnews/9655.htm
- http://m.blog.ghtkgg.cn/nnews/837780.htm
- http://m.blog.ghtkgg.cn/nnews/6814407.htm
- http://m.blog.ghtkgg.cn/nnews/995903.htm
- http://m.blog.ghtkgg.cn/nnews/6286.htm
- http://m.blog.ghtkgg.cn/nnews/27060.htm
- http://m.blog.ghtkgg.cn/nnews/884637.htm
- http://m.blog.ghtkgg.cn/nnews/4813603.htm
- http://m.blog.ghtkgg.cn/nnews/8513.htm
- http://m.blog.ghtkgg.cn/nnews/241882.htm
- http://m.blog.ghtkgg.cn/nnews/11059.htm
- http://m.blog.ghtkgg.cn/nnews/499705.htm
- http://m.blog.ghtkgg.cn/nnews/3160.htm
- http://m.blog.ghtkgg.cn/nnews/1089731.htm
- http://m.blog.ghtkgg.cn/nnews/04041.htm
- http://m.blog.ghtkgg.cn/nnews/2689389.htm
- http://m.blog.ghtkgg.cn/nnews/355519.htm
- http://m.blog.ghtkgg.cn/nnews/12540.htm
- http://m.blog.ghtkgg.cn/nnews/280127.htm
- http://m.blog.ghtkgg.cn/nnews/72440.htm
- http://m.blog.ghtkgg.cn/nnews/7886413.htm
- http://m.blog.ghtkgg.cn/nnews/22036.htm
- http://m.blog.ghtkgg.cn/nnews/3932.htm
- http://m.blog.ghtkgg.cn/nnews/1304731.htm
- http://m.blog.ghtkgg.cn/nnews/4328.htm
- http://m.blog.ghtkgg.cn/nnews/0949403.htm
- http://m.blog.ghtkgg.cn/nnews/023543.htm
- http://m.blog.ghtkgg.cn/nnews/86618.htm
- http://m.blog.ghtkgg.cn/nnews/1324247.htm
- http://m.blog.ghtkgg.cn/nnews/38885.htm
- http://m.blog.ghtkgg.cn/nnews/475001.htm
- http://m.blog.ghtkgg.cn/nnews/7431.htm
- http://m.blog.ghtkgg.cn/nnews/54784.htm
- http://m.blog.ghtkgg.cn/nnews/2646.htm
- http://m.blog.ghtkgg.cn/nnews/0881183.htm
- http://m.blog.ghtkgg.cn/nnews/7791.htm
- http://m.blog.ghtkgg.cn/nnews/42220.htm
- http://m.blog.ghtkgg.cn/nnews/7258127.htm
- http://m.blog.ghtkgg.cn/nnews/21894.htm
- http://m.blog.ghtkgg.cn/nnews/197019.htm
- http://m.blog.ghtkgg.cn/nnews/69075.htm
- http://m.blog.ghtkgg.cn/nnews/5760050.htm
- http://m.blog.ghtkgg.cn/nnews/5645.htm
- http://m.blog.ghtkgg.cn/nnews/4049708.htm
- http://m.blog.ghtkgg.cn/nnews/31397.htm
- http://m.blog.ghtkgg.cn/nnews/8674519.htm
- http://m.blog.ghtkgg.cn/nnews/28469.htm
- http://m.blog.ghtkgg.cn/nnews/38087.htm
- http://m.blog.ghtkgg.cn/nnews/7048.htm
- http://m.blog.ghtkgg.cn/nnews/7945.htm
- http://m.blog.ghtkgg.cn/nnews/1045.htm
- http://m.blog.ghtkgg.cn/nnews/503049.htm
- http://m.blog.ghtkgg.cn/nnews/0138604.htm
- http://m.blog.ghtkgg.cn/nnews/7358910.htm
- http://m.blog.ghtkgg.cn/nnews/3124847.htm
- http://m.blog.ghtkgg.cn/nnews/93671.htm
- http://m.blog.ghtkgg.cn/nnews/2586834.htm
- http://m.blog.ghtkgg.cn/nnews/7564387.htm
- http://m.blog.ghtkgg.cn/nnews/43830.htm
- http://m.blog.ghtkgg.cn/nnews/4809111.htm
- http://m.blog.ghtkgg.cn/nnews/3915267.htm
- http://m.blog.ghtkgg.cn/nnews/14943.htm
- http://m.blog.ghtkgg.cn/nnews/72546.htm
- http://m.blog.ghtkgg.cn/nnews/400251.htm
- http://m.blog.ghtkgg.cn/nnews/41653.htm
- http://m.blog.ghtkgg.cn/nnews/584806.htm
- http://m.blog.ghtkgg.cn/nnews/0643640.htm
- http://m.blog.ghtkgg.cn/nnews/37149.htm
- http://m.blog.ghtkgg.cn/nnews/5449.htm
- http://m.blog.ghtkgg.cn/nnews/2543.htm
- http://m.blog.ghtkgg.cn/nnews/76063.htm
- http://m.blog.ghtkgg.cn/nnews/9826489.htm
- http://m.blog.ghtkgg.cn/nnews/8488491.htm
- http://m.blog.ghtkgg.cn/nnews/6454131.htm
- http://m.blog.ghtkgg.cn/nnews/6979459.htm
- http://m.blog.ghtkgg.cn/nnews/65217.htm
- http://m.blog.ghtkgg.cn/nnews/498911.htm
- http://m.blog.ghtkgg.cn/nnews/6455.htm
- http://m.blog.ghtkgg.cn/nnews/398257.htm
- http://m.blog.ghtkgg.cn/nnews/66021.htm
- http://m.blog.ghtkgg.cn/nnews/70650.htm
- http://m.blog.ghtkgg.cn/nnews/7157.htm
- http://m.blog.ghtkgg.cn/nnews/61555.htm
- http://m.blog.ghtkgg.cn/nnews/0702949.htm
- http://m.blog.ghtkgg.cn/nnews/054450.htm
- http://m.blog.ghtkgg.cn/nnews/48509.htm
- http://m.blog.ghtkgg.cn/nnews/63354.htm
- http://m.blog.ghtkgg.cn/nnews/7765786.htm
- http://m.blog.ghtkgg.cn/nnews/4405956.htm
- http://m.blog.ghtkgg.cn/nnews/1985.htm
- http://m.blog.ghtkgg.cn/nnews/91798.htm
- http://m.blog.ghtkgg.cn/nnews/0593607.htm
- http://m.blog.ghtkgg.cn/nnews/5993.htm
- http://m.blog.ghtkgg.cn/nnews/7235492.htm
- http://m.blog.ghtkgg.cn/nnews/89678.htm
- http://m.blog.ghtkgg.cn/nnews/4711.htm
- http://m.blog.ghtkgg.cn/nnews/8119246.htm
- http://m.blog.ghtkgg.cn/nnews/976896.htm
- http://m.blog.ghtkgg.cn/nnews/59416.htm
- http://m.blog.ghtkgg.cn/nnews/5063639.htm
- http://m.blog.ghtkgg.cn/nnews/532364.htm
- http://m.blog.ghtkgg.cn/nnews/055919.htm
- http://m.blog.ghtkgg.cn/nnews/89967.htm
- http://m.blog.ghtkgg.cn/nnews/96378.htm
- http://m.blog.ghtkgg.cn/nnews/31179.htm
- http://m.blog.ghtkgg.cn/nnews/45451.htm
- http://m.blog.ghtkgg.cn/nnews/731889.htm
- http://m.blog.ghtkgg.cn/nnews/1193.htm
- http://m.blog.ghtkgg.cn/nnews/727888.htm
- http://m.blog.ghtkgg.cn/nnews/85066.htm
- http://m.blog.ghtkgg.cn/nnews/36821.htm
- http://m.blog.ghtkgg.cn/nnews/4891.htm
- http://m.blog.ghtkgg.cn/nnews/706653.htm
- http://m.blog.ghtkgg.cn/nnews/7018886.htm
- http://m.blog.ghtkgg.cn/nnews/8643633.htm
- http://m.blog.ghtkgg.cn/nnews/2553.htm
- http://m.blog.ghtkgg.cn/nnews/9957.htm
- http://m.blog.ghtkgg.cn/nnews/57535.htm
- http://m.blog.ghtkgg.cn/nnews/25970.htm
- http://m.blog.ghtkgg.cn/nnews/625301.htm
- http://m.blog.ghtkgg.cn/nnews/06835.htm
- http://m.blog.ghtkgg.cn/nnews/9239299.htm
- http://m.blog.ghtkgg.cn/nnews/61497.htm
- http://m.blog.ghtkgg.cn/nnews/900531.htm
- http://m.blog.ghtkgg.cn/nnews/804574.htm
- http://m.blog.ghtkgg.cn/nnews/3745441.htm
- http://m.blog.ghtkgg.cn/nnews/73407.htm
- http://m.blog.ghtkgg.cn/nnews/24650.htm
- http://m.blog.ghtkgg.cn/nnews/0085931.htm
- http://m.blog.ghtkgg.cn/nnews/3481.htm
- http://m.blog.ghtkgg.cn/nnews/36289.htm
- http://m.blog.ghtkgg.cn/nnews/8444.htm
- http://m.blog.ghtkgg.cn/nnews/83985.htm
- http://m.blog.ghtkgg.cn/nnews/2523975.htm
- http://m.blog.ghtkgg.cn/nnews/54435.htm
- http://m.blog.ghtkgg.cn/nnews/23006.htm
- http://m.blog.ghtkgg.cn/nnews/7649.htm
- http://m.blog.ghtkgg.cn/nnews/576425.htm
- http://m.blog.ghtkgg.cn/nnews/40528.htm
- http://m.blog.ghtkgg.cn/nnews/1594804.htm
- http://m.blog.ghtkgg.cn/nnews/9002.htm
- http://m.blog.ghtkgg.cn/nnews/0155400.htm
- http://m.blog.ghtkgg.cn/nnews/1048.htm
- http://m.blog.ghtkgg.cn/nnews/0509185.htm
- http://m.blog.ghtkgg.cn/nnews/3793.htm
- http://m.blog.ghtkgg.cn/nnews/994075.htm
- http://m.blog.ghtkgg.cn/nnews/4400.htm
- http://m.blog.ghtkgg.cn/nnews/6997908.htm
- http://m.blog.ghtkgg.cn/nnews/4532199.htm
- http://m.blog.ghtkgg.cn/nnews/829154.htm
- http://m.blog.ghtkgg.cn/nnews/7617.htm
- http://m.blog.ghtkgg.cn/nnews/575234.htm
- http://m.blog.ghtkgg.cn/nnews/395134.htm
- http://m.blog.ghtkgg.cn/nnews/744181.htm
- http://m.blog.ghtkgg.cn/nnews/97188.htm
- http://m.blog.ghtkgg.cn/nnews/8072.htm
- http://m.blog.ghtkgg.cn/nnews/2024.htm
- http://m.blog.ghtkgg.cn/nnews/5707404.htm
- http://m.blog.ghtkgg.cn/nnews/8236.htm
- http://m.blog.ghtkgg.cn/nnews/1049750.htm
- http://m.blog.ghtkgg.cn/nnews/2167669.htm
- http://m.blog.ghtkgg.cn/nnews/4789.htm
- http://m.blog.ghtkgg.cn/nnews/94030.htm
- http://m.blog.ghtkgg.cn/nnews/1900730.htm
- http://m.blog.ghtkgg.cn/nnews/4805.htm
- http://m.blog.ghtkgg.cn/nnews/8192.htm
- http://m.blog.ghtkgg.cn/nnews/115441.htm
- http://m.blog.ghtkgg.cn/nnews/4134.htm
- http://m.blog.ghtkgg.cn/nnews/30423.htm
- http://m.blog.ghtkgg.cn/nnews/0661.htm
- http://m.blog.ghtkgg.cn/nnews/5420.htm
- http://m.blog.ghtkgg.cn/nnews/219392.htm
- http://m.blog.ghtkgg.cn/nnews/2467.htm
- http://m.blog.ghtkgg.cn/nnews/4057.htm
- http://m.blog.ghtkgg.cn/nnews/5648448.htm
- http://m.blog.ghtkgg.cn/nnews/185020.htm
- http://m.blog.ghtkgg.cn/nnews/337427.htm
- http://m.blog.ghtkgg.cn/nnews/51089.htm
- http://m.blog.ghtkgg.cn/nnews/6050.htm
- http://m.blog.ghtkgg.cn/nnews/874004.htm
- http://m.blog.ghtkgg.cn/nnews/7550.htm
- http://m.blog.ghtkgg.cn/nnews/24367.htm
- http://m.blog.ghtkgg.cn/nnews/481090.htm
- http://m.blog.ghtkgg.cn/nnews/3456.htm
- http://m.blog.ghtkgg.cn/nnews/8064.htm
- http://m.blog.ghtkgg.cn/nnews/42233.htm
- http://m.blog.ghtkgg.cn/nnews/65134.htm
- http://m.blog.ghtkgg.cn/nnews/7673559.htm
- http://m.blog.ghtkgg.cn/nnews/9180.htm
- http://m.blog.ghtkgg.cn/nnews/9062024.htm
- http://m.blog.ghtkgg.cn/nnews/519339.htm
- http://m.blog.ghtkgg.cn/nnews/0343.htm
- http://m.blog.ghtkgg.cn/nnews/8041.htm
- http://m.blog.ghtkgg.cn/nnews/991832.htm
- http://m.blog.ghtkgg.cn/nnews/296222.htm
- http://m.blog.ghtkgg.cn/nnews/60449.htm
- http://m.blog.ghtkgg.cn/nnews/328606.htm
- http://m.blog.ghtkgg.cn/nnews/0355077.htm
- http://m.blog.ghtkgg.cn/nnews/3940.htm
- http://m.blog.ghtkgg.cn/nnews/9154.htm
- http://m.blog.ghtkgg.cn/nnews/6600.htm
- http://m.blog.ghtkgg.cn/nnews/506779.htm
- http://m.blog.ghtkgg.cn/nnews/5454997.htm
- http://m.blog.ghtkgg.cn/nnews/257453.htm
- http://m.blog.ghtkgg.cn/nnews/7220232.htm
- http://m.blog.ghtkgg.cn/nnews/86403.htm
- http://m.blog.ghtkgg.cn/nnews/509172.htm
- http://m.blog.ghtkgg.cn/nnews/97500.htm
- http://m.blog.ghtkgg.cn/nnews/3195.htm
- http://m.blog.ghtkgg.cn/nnews/386767.htm
- http://m.blog.ghtkgg.cn/nnews/325500.htm
- http://m.blog.ghtkgg.cn/nnews/896466.htm
- http://m.blog.ghtkgg.cn/nnews/6290.htm
- http://m.blog.ghtkgg.cn/nnews/5328761.htm
- http://m.blog.ghtkgg.cn/nnews/16879.htm
- http://m.blog.ghtkgg.cn/nnews/8609.htm
- http://m.blog.ghtkgg.cn/nnews/34207.htm
- http://m.blog.ghtkgg.cn/nnews/21905.htm
- http://m.blog.ghtkgg.cn/nnews/63407.htm
- http://m.blog.ghtkgg.cn/nnews/3618.htm
- http://m.blog.ghtkgg.cn/nnews/0784618.htm
- http://m.blog.ghtkgg.cn/nnews/1360.htm
- http://m.blog.ghtkgg.cn/nnews/6179134.htm
- http://m.blog.ghtkgg.cn/nnews/1225408.htm
- http://m.blog.ghtkgg.cn/nnews/501046.htm
- http://m.blog.ghtkgg.cn/nnews/632833.htm
- http://m.blog.ghtkgg.cn/nnews/556460.htm
- http://m.blog.ghtkgg.cn/nnews/3905.htm
- http://m.blog.ghtkgg.cn/nnews/6889580.htm
- http://m.blog.ghtkgg.cn/nnews/2852.htm
- http://m.blog.ghtkgg.cn/nnews/490925.htm
- http://m.blog.ghtkgg.cn/nnews/28241.htm
- http://m.blog.ghtkgg.cn/nnews/794049.htm
- http://m.blog.ghtkgg.cn/nnews/4604.htm
- http://m.blog.ghtkgg.cn/nnews/1421547.htm
- http://m.blog.ghtkgg.cn/nnews/2188.htm
- http://m.blog.ghtkgg.cn/nnews/879519.htm
- http://m.blog.ghtkgg.cn/nnews/12780.htm
- http://m.blog.ghtkgg.cn/nnews/7937.htm
- http://m.blog.ghtkgg.cn/nnews/22403.htm
- http://m.blog.ghtkgg.cn/nnews/5870913.htm
- http://m.blog.ghtkgg.cn/nnews/336216.htm
- http://m.blog.ghtkgg.cn/nnews/716273.htm
- http://m.blog.ghtkgg.cn/nnews/07534.htm
- http://m.blog.ghtkgg.cn/nnews/38424.htm
- http://m.blog.ghtkgg.cn/nnews/58898.htm
- http://m.blog.ghtkgg.cn/nnews/083433.htm
- http://m.blog.ghtkgg.cn/nnews/9525360.htm
- http://m.blog.ghtkgg.cn/nnews/2497646.htm
- http://m.blog.ghtkgg.cn/nnews/52181.htm
- http://m.blog.ghtkgg.cn/nnews/9064.htm
- http://m.blog.ghtkgg.cn/nnews/72492.htm
- http://m.blog.ghtkgg.cn/nnews/069375.htm
- http://m.blog.ghtkgg.cn/nnews/256229.htm
- http://m.blog.ghtkgg.cn/nnews/90471.htm
- http://m.blog.ghtkgg.cn/nnews/862589.htm

## 项目结构

```
webindex-core/
├── cli.py                      # 命令行入口，封装采集、查询、导出子命令
├── config/
│   ├── settings.yaml           # 全局配置（并发数、超时、重试、日志级别）
│   └── sources.json            # 预置采集源模板（可扩展）
├── core/
│   ├── collector/
│   │   ├── fetcher.py          # 基于 aiohttp 的异步抓取器，支持自定义请求头
│   │   ├── parser.py           # HTML 元数据解析（title， meta， 时间提取）
│   │   └── dedup.py            # 布隆过滤器 + SQLite 双重去重实现
│   ├── indexer/
│   │   ├── store.py            # JSONL 读写与索引检索接口
│   │   └── tags.py             # 标签关联与分类统计模块
│   └── monitor/
│       ├── checker.py          # 批量 HTTP 状态检查（HEAD 请求）
│       └── reporter.py         # 生成健康报告与失效列表
├── data/
│   ├── index.jsonl             # 主索引数据（每行一个 JSON）
│   ├── cache.db                # SQLite 缓存（去重与时间戳记录）
│   └── snapshots/              # 导出的 HTML / Markdown 快照目录
├── tests/
│   ├── test_fetcher.py
│   ├── test_parser.py
│   └── test_dedup.py
├── docs/
│   ├── quickstart.md
│   ├── configuration.md
│   ├── api.md
│   └── operations.md
├── requirements.txt            # 依赖列表（aiohttp， lxml， click， jinja2 等）
├── setup.py                    # 打包与安装脚本
└── README.md                   # 本文档
```

## 贡献指南

1. 在 GitHub 上 fork 本仓库至个人账号，并 clone 到本地开发环境。
2. 创建以 `feature/` 或 `fix/` 为前缀的分支，例如 `feature/add-rss-output`，并在该分支上进行开发。
3. 编写或修改代码后，请在 `tests/` 目录下补充对应的单元测试用例，确保所有测试通过。
4. 提交前执行 `make lint` 和 `make test`（若项目已配置 Makefile），或手动运行 `pytest` 与 `flake8` 检查代码风格。
5. 发起 Pull Request 到主仓库的 `main` 分支，并在 PR 描述中清晰说明改动内容、关联 issue 及测试覆盖情况。

## 常见问题

**Q：采集过程中出现大量超时或连接错误怎么办？**

A：建议调整 `config/settings.yaml` 中的 `timeout` 参数（默认 10 秒）和 `retry` 次数（默认 3 次）。同时可降低 `concurrency` 并发数（默认 20），以减轻目标服务器压力。若目标域名存在反爬策略，可尝试在 `sources.json` 中配置自定义 `User-Agent` 请求头。

**Q：如何只采集指定日期范围内的链接？**

A：当前版本暂未内置时间范围过滤器，但可利用外部工具对导出的 `index.jsonl` 进行后处理。例如使用 `jq` 命令按 `fetched_at` 字段筛选：`jq 'select(.fetched_at >= "2026-01-01")' data/index.jsonl`。后续版本将增加 `--since` 与 `--until` 命令行参数。

**Q：导入之前批次采集的 JSONL 文件时，如何避免重复？**

A：系统在 `core/indexer/store.py` 中提供了 `merge` 方法，可基于 URL 与内容指纹进行合并。执行 `python cli.py merge --input /path/to/old.jsonl --output data/index.jsonl` 即可自动去重并保留最新记录。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
