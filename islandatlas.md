# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端资讯聚合与内容导航的开源工具集，专注于对来自 jnews 源的结构化新闻链接进行批量采集、分类存储、元数据提取与快速检索。项目定位于内容运营团队、个人开发者与学术研究机构，帮助用户在碎片化资讯中建立有序的本地知识索引。

本项目提供从原始 URL 列表导入、自动去重、字段解析到静态站点生成的全链路能力，不依赖第三方云服务，可完全在本地或内网环境中运行。当前批次涵盖 300 个 jnews 链接资源，作为项目默认内置数据源示例，用户亦可替换为自己的链接集合。

## 功能概览

**批量链接导入**：支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别协议与域名格式。

**元数据自动提取**：对每条链接尝试获取标题、内容摘要、发布时间与内容类型，提取结果以结构化 JSON 存储。

**去重与冲突检测**：基于 URL 完整路径与资源指纹双重校验，避免重复入库，并提供手动合并策略。

**分类标签管理**：支持自定义标签体系，可对链接进行多级分类，内置默认分类模板包括科技、财经、健康、教育、社会等。

**全文检索接口**：基于 SQLite FTS5 提供轻量级全文搜索，支持标题、摘要与自定义备注字段的联合查询。

**静态站点导出**：将链接索引导出为静态 HTML 页面，适配移动端阅读布局，便于部署到任意 Web 服务器或 CDN。

**增量更新机制**：支持定期扫描新增链接，仅处理增量数据，适用于持续监控的资讯流场景。

## 应用场景

内容运营团队的内部分享库：团队成员可将分散的 jnews 链接统一提交到聚合器，系统自动提取摘要并生成周报，减少重复劳动。

个人开发者的信息聚合实验：开发者可基于本项目搭建个人资讯仪表盘，将不同栏目的 jnews 链接按主题分流，配合定时任务实现每日推送。

学术研究的数据采集前置：研究人员可使用本项目对 jnews 链接进行初步清洗与分类，为后续自然语言处理或舆情分析提供干净的输入数据。

企业内网的知识归档系统：企业可将外部资讯链接与内部文档链接混合管理，通过统一的检索入口快速定位相关信息，降低信息孤岛。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化数据库并导入内置 300 条链接
python manage.py initdb
python manage.py import --source data/links.txt

# 启动开发服务器
python manage.py serve --port 8080
```

访问 http://127.0.0.1:8080 即可查看链接列表与搜索界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9+ | 核心运行环境，建议使用 3.11 长期支持版本 |
| SQLite | 3.35+ | 内置数据库，需启用 FTS5 扩展支持全文搜索 |
| requests | 2.28+ | 用于获取链接元数据时的 HTTP 请求发送 |
| beautifulsoup4 | 4.11+ | 解析 HTML 内容以提取标题与摘要信息 |
| lxml | 4.9+ | 作为 beautifulsoup4 的解析器后端，性能优于 html.parser |
| markdown | 3.4+ | 将链接备注渲染为 Markdown 格式，用于导出静态页面 |
| pytest | 7.0+ | 开发测试依赖，运行单元测试套件时使用 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user/quickstart.md | 如何安装、配置与运行聚合器核心功能 |
| 用户手册 | docs/user/import-guide.md | 如何批量导入链接、处理冲突与更新元数据 |
| 开发者指南 | docs/dev/api-reference.md | 核心模块的接口定义、参数说明与回调钩子 |
| 开发者指南 | docs/dev/contributing.md | 代码风格规范、提交信息格式与 PR 流程 |
| 运维参考 | docs/ops/deployment.md | 生产环境部署方案、性能调优与备份策略 |
| 运维参考 | docs/ops/troubleshooting.md | 常见启动错误、数据库锁问题与网络超时处理 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/418774.htm
- http://m.3g.bwbkj.cn/jnews/6498926.htm
- http://m.3g.bwbkj.cn/jnews/6464324.htm
- http://m.3g.bwbkj.cn/jnews/7525026.htm
- http://m.3g.bwbkj.cn/jnews/842228.htm
- http://m.3g.bwbkj.cn/jnews/9816543.htm
- http://m.3g.bwbkj.cn/jnews/0972293.htm
- http://m.3g.bwbkj.cn/jnews/97958.htm
- http://m.3g.bwbkj.cn/jnews/7535099.htm
- http://m.3g.bwbkj.cn/jnews/3857.htm
- http://m.3g.bwbkj.cn/jnews/230481.htm
- http://m.3g.bwbkj.cn/jnews/4138.htm
- http://m.3g.bwbkj.cn/jnews/861825.htm
- http://m.3g.bwbkj.cn/jnews/2735.htm
- http://m.3g.bwbkj.cn/jnews/56174.htm
- http://m.3g.bwbkj.cn/jnews/7981949.htm
- http://m.3g.bwbkj.cn/jnews/226798.htm
- http://m.3g.bwbkj.cn/jnews/52652.htm
- http://m.3g.bwbkj.cn/jnews/0765.htm
- http://m.3g.bwbkj.cn/jnews/8360.htm
- http://m.3g.bwbkj.cn/jnews/13462.htm
- http://m.3g.bwbkj.cn/jnews/3039.htm
- http://m.3g.bwbkj.cn/jnews/853236.htm
- http://m.3g.bwbkj.cn/jnews/18975.htm
- http://m.3g.bwbkj.cn/jnews/9881004.htm
- http://m.3g.bwbkj.cn/jnews/01025.htm
- http://m.3g.bwbkj.cn/jnews/245144.htm
- http://m.3g.bwbkj.cn/jnews/2251.htm
- http://m.3g.bwbkj.cn/jnews/5281027.htm
- http://m.3g.bwbkj.cn/jnews/3342.htm
- http://m.3g.bwbkj.cn/jnews/0620.htm
- http://m.3g.bwbkj.cn/jnews/65468.htm
- http://m.3g.bwbkj.cn/jnews/15143.htm
- http://m.3g.bwbkj.cn/jnews/2012938.htm
- http://m.3g.bwbkj.cn/jnews/539183.htm
- http://m.3g.bwbkj.cn/jnews/5650088.htm
- http://m.3g.bwbkj.cn/jnews/8409812.htm
- http://m.3g.bwbkj.cn/jnews/963440.htm
- http://m.3g.bwbkj.cn/jnews/833563.htm
- http://m.3g.bwbkj.cn/jnews/3937695.htm
- http://m.3g.bwbkj.cn/jnews/326558.htm
- http://m.3g.bwbkj.cn/jnews/050770.htm
- http://m.3g.bwbkj.cn/jnews/41733.htm
- http://m.3g.bwbkj.cn/jnews/69343.htm
- http://m.3g.bwbkj.cn/jnews/3247496.htm
- http://m.3g.bwbkj.cn/jnews/0814.htm
- http://m.3g.bwbkj.cn/jnews/73782.htm
- http://m.3g.bwbkj.cn/jnews/9165003.htm
- http://m.3g.bwbkj.cn/jnews/94897.htm
- http://m.3g.bwbkj.cn/jnews/0371332.htm
- http://m.3g.bwbkj.cn/jnews/7834548.htm
- http://m.3g.bwbkj.cn/jnews/988649.htm
- http://m.3g.bwbkj.cn/jnews/4639.htm
- http://m.3g.bwbkj.cn/jnews/4099150.htm
- http://m.3g.bwbkj.cn/jnews/2489245.htm
- http://m.3g.bwbkj.cn/jnews/7988979.htm
- http://m.3g.bwbkj.cn/jnews/66882.htm
- http://m.3g.bwbkj.cn/jnews/153663.htm
- http://m.3g.bwbkj.cn/jnews/94997.htm
- http://m.3g.bwbkj.cn/jnews/2989.htm
- http://m.3g.bwbkj.cn/jnews/64750.htm
- http://m.3g.bwbkj.cn/jnews/0055.htm
- http://m.3g.bwbkj.cn/jnews/600743.htm
- http://m.3g.bwbkj.cn/jnews/2208.htm
- http://m.3g.bwbkj.cn/jnews/7444.htm
- http://m.3g.bwbkj.cn/jnews/5365095.htm
- http://m.3g.bwbkj.cn/jnews/6241.htm
- http://m.3g.bwbkj.cn/jnews/77769.htm
- http://m.3g.bwbkj.cn/jnews/02350.htm
- http://m.3g.bwbkj.cn/jnews/2999.htm
- http://m.3g.bwbkj.cn/jnews/7702.htm
- http://m.3g.bwbkj.cn/jnews/866313.htm
- http://m.3g.bwbkj.cn/jnews/104653.htm
- http://m.3g.bwbkj.cn/jnews/25284.htm
- http://m.3g.bwbkj.cn/jnews/3155.htm
- http://m.3g.bwbkj.cn/jnews/80582.htm
- http://m.3g.bwbkj.cn/jnews/23508.htm
- http://m.3g.bwbkj.cn/jnews/38834.htm
- http://m.3g.bwbkj.cn/jnews/0553848.htm
- http://m.3g.bwbkj.cn/jnews/98113.htm
- http://m.3g.bwbkj.cn/jnews/4395.htm
- http://m.3g.bwbkj.cn/jnews/90039.htm
- http://m.3g.bwbkj.cn/jnews/2598797.htm
- http://m.3g.bwbkj.cn/jnews/1494.htm
- http://m.3g.bwbkj.cn/jnews/400525.htm
- http://m.3g.bwbkj.cn/jnews/276134.htm
- http://m.3g.bwbkj.cn/jnews/1165.htm
- http://m.3g.bwbkj.cn/jnews/5775518.htm
- http://m.3g.bwbkj.cn/jnews/5559221.htm
- http://m.3g.bwbkj.cn/jnews/895753.htm
- http://m.3g.bwbkj.cn/jnews/3319.htm
- http://m.3g.bwbkj.cn/jnews/8491.htm
- http://m.3g.bwbkj.cn/jnews/2610874.htm
- http://m.3g.bwbkj.cn/jnews/49300.htm
- http://m.3g.bwbkj.cn/jnews/7763290.htm
- http://m.3g.bwbkj.cn/jnews/48770.htm
- http://m.3g.bwbkj.cn/jnews/10738.htm
- http://m.3g.bwbkj.cn/jnews/0042.htm
- http://m.3g.bwbkj.cn/jnews/0622.htm
- http://m.3g.bwbkj.cn/jnews/90286.htm
- http://m.3g.bwbkj.cn/jnews/3403.htm
- http://m.3g.bwbkj.cn/jnews/29060.htm
- http://m.3g.bwbkj.cn/jnews/2798821.htm
- http://m.3g.bwbkj.cn/jnews/5102.htm
- http://m.3g.bwbkj.cn/jnews/2831899.htm
- http://m.3g.bwbkj.cn/jnews/565563.htm
- http://m.3g.bwbkj.cn/jnews/97604.htm
- http://m.3g.bwbkj.cn/jnews/5243634.htm
- http://m.3g.bwbkj.cn/jnews/5405.htm
- http://m.3g.bwbkj.cn/jnews/121512.htm
- http://m.3g.bwbkj.cn/jnews/7811.htm
- http://m.3g.bwbkj.cn/jnews/7700.htm
- http://m.3g.bwbkj.cn/jnews/6876.htm
- http://m.3g.bwbkj.cn/jnews/71796.htm
- http://m.3g.bwbkj.cn/jnews/99364.htm
- http://m.3g.bwbkj.cn/jnews/11381.htm
- http://m.3g.bwbkj.cn/jnews/5579160.htm
- http://m.3g.bwbkj.cn/jnews/18131.htm
- http://m.3g.bwbkj.cn/jnews/52961.htm
- http://m.3g.bwbkj.cn/jnews/7428.htm
- http://m.3g.bwbkj.cn/jnews/6375626.htm
- http://m.3g.bwbkj.cn/jnews/39549.htm
- http://m.3g.bwbkj.cn/jnews/1647.htm
- http://m.3g.bwbkj.cn/jnews/4953.htm
- http://m.3g.bwbkj.cn/jnews/83423.htm
- http://m.3g.bwbkj.cn/jnews/636812.htm
- http://m.3g.bwbkj.cn/jnews/3075831.htm
- http://m.3g.bwbkj.cn/jnews/03251.htm
- http://m.3g.bwbkj.cn/jnews/1278.htm
- http://m.3g.bwbkj.cn/jnews/8224642.htm
- http://m.3g.bwbkj.cn/jnews/02854.htm
- http://m.3g.bwbkj.cn/jnews/3731.htm
- http://m.3g.bwbkj.cn/jnews/9046678.htm
- http://m.3g.bwbkj.cn/jnews/065698.htm
- http://m.3g.bwbkj.cn/jnews/55588.htm
- http://m.3g.bwbkj.cn/jnews/3459325.htm
- http://m.3g.bwbkj.cn/jnews/5256128.htm
- http://m.3g.bwbkj.cn/jnews/5168412.htm
- http://m.3g.bwbkj.cn/jnews/1866.htm
- http://m.3g.bwbkj.cn/jnews/5606.htm
- http://m.3g.bwbkj.cn/jnews/820780.htm
- http://m.3g.bwbkj.cn/jnews/5428.htm
- http://m.3g.bwbkj.cn/jnews/207856.htm
- http://m.3g.bwbkj.cn/jnews/7136471.htm
- http://m.3g.bwbkj.cn/jnews/6005.htm
- http://m.3g.bwbkj.cn/jnews/1188.htm
- http://m.3g.bwbkj.cn/jnews/0512750.htm
- http://m.3g.bwbkj.cn/jnews/865863.htm
- http://m.3g.bwbkj.cn/jnews/5799.htm
- http://m.3g.bwbkj.cn/jnews/9095481.htm
- http://m.3g.bwbkj.cn/jnews/7763657.htm
- http://m.3g.bwbkj.cn/jnews/0716.htm
- http://m.3g.bwbkj.cn/jnews/7365.htm
- http://m.3g.bwbkj.cn/jnews/79380.htm
- http://m.3g.bwbkj.cn/jnews/8000518.htm
- http://m.3g.bwbkj.cn/jnews/10634.htm
- http://m.3g.bwbkj.cn/jnews/79102.htm
- http://m.3g.bwbkj.cn/jnews/1140.htm
- http://m.3g.bwbkj.cn/jnews/898165.htm
- http://m.3g.bwbkj.cn/jnews/1279634.htm
- http://m.3g.bwbkj.cn/jnews/0771848.htm
- http://m.3g.bwbkj.cn/jnews/1828.htm
- http://m.3g.bwbkj.cn/jnews/9691.htm
- http://m.3g.bwbkj.cn/jnews/247156.htm
- http://m.3g.bwbkj.cn/jnews/468204.htm
- http://m.3g.bwbkj.cn/jnews/25690.htm
- http://m.3g.bwbkj.cn/jnews/5399.htm
- http://m.3g.bwbkj.cn/jnews/2363702.htm
- http://m.3g.bwbkj.cn/jnews/470894.htm
- http://m.3g.bwbkj.cn/jnews/6428.htm
- http://m.3g.bwbkj.cn/jnews/815246.htm
- http://m.3g.bwbkj.cn/jnews/1123.htm
- http://m.3g.bwbkj.cn/jnews/27324.htm
- http://m.3g.bwbkj.cn/jnews/093374.htm
- http://m.3g.bwbkj.cn/jnews/279495.htm
- http://m.3g.bwbkj.cn/jnews/5785994.htm
- http://m.3g.bwbkj.cn/jnews/50624.htm
- http://m.3g.bwbkj.cn/jnews/64693.htm
- http://m.3g.bwbkj.cn/jnews/536589.htm
- http://m.3g.bwbkj.cn/jnews/6646235.htm
- http://m.3g.bwbkj.cn/jnews/75540.htm
- http://m.3g.bwbkj.cn/jnews/93358.htm
- http://m.3g.bwbkj.cn/jnews/58243.htm
- http://m.3g.bwbkj.cn/jnews/1022.htm
- http://m.3g.bwbkj.cn/jnews/5115606.htm
- http://m.3g.bwbkj.cn/jnews/3519414.htm
- http://m.3g.bwbkj.cn/jnews/825058.htm
- http://m.3g.bwbkj.cn/jnews/40314.htm
- http://m.3g.bwbkj.cn/jnews/7127801.htm
- http://m.3g.bwbkj.cn/jnews/5882468.htm
- http://m.3g.bwbkj.cn/jnews/06601.htm
- http://m.3g.bwbkj.cn/jnews/925254.htm
- http://m.3g.bwbkj.cn/jnews/69302.htm
- http://m.3g.bwbkj.cn/jnews/89574.htm
- http://m.3g.bwbkj.cn/jnews/27150.htm
- http://m.3g.bwbkj.cn/jnews/52281.htm
- http://m.3g.bwbkj.cn/jnews/9977.htm
- http://m.3g.bwbkj.cn/jnews/717649.htm
- http://m.3g.bwbkj.cn/jnews/3660.htm
- http://m.3g.bwbkj.cn/jnews/8276.htm
- http://m.3g.bwbkj.cn/jnews/71289.htm
- http://m.3g.bwbkj.cn/jnews/42510.htm
- http://m.3g.bwbkj.cn/jnews/92356.htm
- http://m.3g.bwbkj.cn/jnews/9297004.htm
- http://m.3g.bwbkj.cn/jnews/5336960.htm
- http://m.3g.bwbkj.cn/jnews/4628.htm
- http://m.3g.bwbkj.cn/jnews/2080998.htm
- http://m.3g.bwbkj.cn/jnews/707819.htm
- http://m.3g.bwbkj.cn/jnews/3221.htm
- http://m.3g.bwbkj.cn/jnews/35245.htm
- http://m.3g.bwbkj.cn/jnews/72647.htm
- http://m.3g.bwbkj.cn/jnews/32601.htm
- http://m.3g.bwbkj.cn/jnews/3547.htm
- http://m.3g.bwbkj.cn/jnews/19945.htm
- http://m.3g.bwbkj.cn/jnews/039595.htm
- http://m.3g.bwbkj.cn/jnews/7901691.htm
- http://m.3g.bwbkj.cn/jnews/28775.htm
- http://m.3g.bwbkj.cn/jnews/1007356.htm
- http://m.3g.bwbkj.cn/jnews/87023.htm
- http://m.3g.bwbkj.cn/jnews/61474.htm
- http://m.3g.bwbkj.cn/jnews/0003851.htm
- http://m.3g.bwbkj.cn/jnews/0566111.htm
- http://m.3g.bwbkj.cn/jnews/90851.htm
- http://m.3g.bwbkj.cn/jnews/9205707.htm
- http://m.3g.bwbkj.cn/jnews/257339.htm
- http://m.3g.bwbkj.cn/jnews/6894.htm
- http://m.3g.bwbkj.cn/jnews/153975.htm
- http://m.3g.bwbkj.cn/jnews/5830738.htm
- http://m.3g.bwbkj.cn/jnews/6418.htm
- http://m.3g.bwbkj.cn/jnews/7529.htm
- http://m.3g.bwbkj.cn/jnews/19223.htm
- http://m.3g.bwbkj.cn/jnews/0458316.htm
- http://m.3g.bwbkj.cn/jnews/0564511.htm
- http://m.3g.bwbkj.cn/jnews/7998603.htm
- http://m.3g.bwbkj.cn/jnews/64628.htm
- http://m.3g.bwbkj.cn/jnews/527262.htm
- http://m.3g.bwbkj.cn/jnews/9028171.htm
- http://m.3g.bwbkj.cn/jnews/5618395.htm
- http://m.3g.bwbkj.cn/jnews/5685409.htm
- http://m.3g.bwbkj.cn/jnews/3400.htm
- http://m.3g.bwbkj.cn/jnews/0343953.htm
- http://m.3g.bwbkj.cn/jnews/2033286.htm
- http://m.3g.bwbkj.cn/jnews/3546607.htm
- http://m.3g.bwbkj.cn/jnews/7836666.htm
- http://m.3g.bwbkj.cn/jnews/64608.htm
- http://m.3g.bwbkj.cn/jnews/8731.htm
- http://m.3g.bwbkj.cn/jnews/6028.htm
- http://m.3g.bwbkj.cn/jnews/2491435.htm
- http://m.3g.bwbkj.cn/jnews/4210421.htm
- http://m.3g.bwbkj.cn/jnews/5754.htm
- http://m.3g.bwbkj.cn/jnews/3194.htm
- http://m.3g.bwbkj.cn/jnews/9622829.htm
- http://m.3g.bwbkj.cn/jnews/94227.htm
- http://m.3g.bwbkj.cn/jnews/6508354.htm
- http://m.3g.bwbkj.cn/jnews/118883.htm
- http://m.3g.bwbkj.cn/jnews/0072.htm
- http://m.3g.bwbkj.cn/jnews/93129.htm
- http://m.3g.bwbkj.cn/jnews/8338035.htm
- http://m.3g.bwbkj.cn/jnews/85263.htm
- http://m.3g.bwbkj.cn/jnews/2847.htm
- http://m.3g.bwbkj.cn/jnews/825759.htm
- http://m.3g.bwbkj.cn/jnews/32674.htm
- http://m.3g.bwbkj.cn/jnews/9392.htm
- http://m.3g.bwbkj.cn/jnews/6823.htm
- http://m.3g.bwbkj.cn/jnews/8428531.htm
- http://m.3g.bwbkj.cn/jnews/705698.htm
- http://m.3g.bwbkj.cn/jnews/9190.htm
- http://m.3g.bwbkj.cn/jnews/9161.htm
- http://m.3g.bwbkj.cn/jnews/635667.htm
- http://m.3g.bwbkj.cn/jnews/3366091.htm
- http://m.3g.bwbkj.cn/jnews/8415557.htm
- http://m.3g.bwbkj.cn/jnews/57745.htm
- http://m.3g.bwbkj.cn/jnews/1093064.htm
- http://m.3g.bwbkj.cn/jnews/54076.htm
- http://m.3g.bwbkj.cn/jnews/3018200.htm
- http://m.3g.bwbkj.cn/jnews/1961.htm
- http://m.3g.bwbkj.cn/jnews/00601.htm
- http://m.3g.bwbkj.cn/jnews/2558.htm
- http://m.3g.bwbkj.cn/jnews/561082.htm
- http://m.3g.bwbkj.cn/jnews/153750.htm
- http://m.3g.bwbkj.cn/jnews/2810057.htm
- http://m.3g.bwbkj.cn/jnews/472653.htm
- http://m.3g.bwbkj.cn/jnews/255364.htm
- http://m.3g.bwbkj.cn/jnews/64728.htm
- http://m.3g.bwbkj.cn/jnews/45093.htm
- http://m.3g.bwbkj.cn/jnews/2817.htm
- http://m.3g.bwbkj.cn/jnews/55396.htm
- http://m.3g.bwbkj.cn/jnews/4846.htm
- http://m.3g.bwbkj.cn/jnews/799206.htm
- http://m.3g.bwbkj.cn/jnews/8731715.htm
- http://m.3g.bwbkj.cn/jnews/55978.htm
- http://m.3g.bwbkj.cn/jnews/6513.htm
- http://m.3g.bwbkj.cn/jnews/52576.htm
- http://m.3g.bwbkj.cn/jnews/88123.htm
- http://m.3g.bwbkj.cn/jnews/338100.htm
- http://m.3g.bwbkj.cn/jnews/163729.htm
- http://m.3g.bwbkj.cn/jnews/1356697.htm
- http://m.3g.bwbkj.cn/jnews/633967.htm
- http://m.3g.bwbkj.cn/jnews/9831903.htm
- http://m.3g.bwbkj.cn/jnews/9418940.htm

## 项目结构

```
jnews-link-aggregator/
├── src/                                  # 核心源码目录
│   ├── core/                             # 核心业务逻辑模块
│   │   ├── importer.py                   # 链接导入与去重引擎
│   │   ├── metadata.py                   # 元数据提取与缓存策略
│   │   └── classifier.py                 # 基于规则的分类器实现
│   ├── storage/                          # 数据持久化层
│   │   ├── database.py                   # SQLite 连接池与表结构管理
│   │   ├── repository.py                 # 链接增删改查的仓库接口
│   │   └── migrations/                   # 数据库迁移脚本目录
│   │       └── 001_initial_schema.sql    # 初始表结构定义
│   ├── web/                              # Web 服务与静态导出
│   │   ├── app.py                        # Flask 应用主入口
│   │   ├── templates/                    # Jinja2 模板目录
│   │   │   ├── index.html                # 链接列表主页
│   │   │   └── search.html               # 搜索结果页面
│   │   └── static/                       # 编译后的 CSS/JS 资源
│   │       └── style.css                 # 移动端自适应样式表
│   └── utils/                            # 通用工具函数集
│       ├── http_client.py                # 带重试与超时控制的 HTTP 客户端
│       └── text_parser.py                # 摘要截断、标签清洗与日期解析
├── tests/                                # 单元测试与集成测试
│   ├── test_importer.py                  # 导入流程的测试用例
│   ├── test_metadata.py                  # 元数据提取的模拟响应测试
│   └── fixtures/                         # 测试用的固定数据样例
│       └── sample_links.txt              # 10 条示例链接供测试使用
├── data/                                 # 用户数据与内置资源
│   ├── links.txt                         # 默认导入的 300 条链接源文件
│   └── tags.json                         # 预设分类标签与关键词映射
├── docs/                                 # 完整文档目录（参见文档导航）
│   ├── user/                             # 用户手册
│   ├── dev/                              # 开发者指南
│   └── ops/                              # 运维参考
├── scripts/                              # 辅助运维脚本
│   ├── backup.sh                         # 数据库备份脚本
│   └── weekly_import.sh                  # 每周增量导入的定时任务模板
├── requirements.txt                      # Python 生产依赖列表
├── requirements-dev.txt                  # 开发环境额外依赖（pytest、black 等）
├── manage.py                             # 统一命令行入口（initdb/import/serve）
└── README.md                             # 本文件
```

## 贡献指南

首先在 GitHub 上 fork 本仓库，并将 fork 后的仓库克隆到本地开发环境中。建议在 dev 分支上进行所有修改，保持 master 分支与上游同步。

运行测试套件确保现有功能未被破坏，使用 `pytest tests/` 执行全部用例。新增功能必须附带对应的测试用例，覆盖核心逻辑分支。

提交代码前使用 `black` 与 `isort` 进行自动格式化，保证代码风格一致。提交信息遵循常规提交格式，即 `type(scope): subject` 的形式，例如 `feat(importer): add retry mechanism for failed requests`。

发起 Pull Request 时请填写提供的模板，清晰描述改动内容、影响范围以及是否包含破坏性变更。PR 需要至少一位维护者审阅通过后方可合并。

## 常见问题

**导入链接时出现 SSL 证书验证失败，如何处理？**

部分 jnews 源站可能使用自签名证书或过期证书。默认配置下，系统会跳过证书验证以保障内网环境可用性。如需强制验证，可将配置文件中的 `VERIFY_SSL` 参数设为 `true`。若仍报错，请检查系统时间是否准确，或手动将证书添加到信任链。

**全文搜索对中文支持不完善，能否改进？**

项目默认使用 SQLite FTS5 的 tokenizer，对中文分词效果有限。建议在导入阶段为每条记录生成拼音或拆分字词作为辅助索引字段。后续版本计划集成 jieba 分词作为可选的预处理步骤，届时可通过配置切换。

**静态导出页面包含链接失效，如何标记并清理？**

导出过程会自动检测链接的 HTTP 状态码，将返回 4xx 或 5xx 的链接标记为“需复核”，并在页面上以不同颜色显示。用户可在管理后台手动确认后删除或更新这些链接。定期运行 `python manage.py validate --timeout 5` 可刷新所有链接的存活状态。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:00
