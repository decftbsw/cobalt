# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端新闻资讯聚合的开源外链管理工具，专为内容编辑、资讯站运维人员和数据采集工程师设计，用于对来自 m.3g.bwbkj.cn 等移动新闻源的大量文章链接进行批量收集、结构化存储、去重校验和元数据提取。该项目不提供新闻内容本身，而是作为技术基础设施，帮助用户高效管理分散在多个批次中的数千条新闻外链，降低人工整理成本，提升数据流转的可追溯性。

本工具定位为轻量级、可扩展的链接处理管道，支持从原始链接列表中自动解析文章ID、来源域名、发布时间模式，并生成标准化的输出格式供下游系统使用。项目内置针对第 204/300 批次共 300 个资源链接的索引模板，方便快速导入和分类。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动识别 HTTP/HTTPS 协议格式。

**智能去重校验** 基于链接完整路径和文章ID的哈希值进行去重，避免同一篇文章被多次录入，并提供重复报告。

**元数据解析提取** 从每个 URL 中解析出文章数字ID、扩展名类型以及可能的分类路径，生成结构化字段。

**移动端来源标记** 识别并保留 m.3g.bwbkj.cn 等移动子域名来源标记，便于后续按来源域名过滤和分析。

**批次管理支持** 内置批次编号字段（如 204/300），支持多批次链接的分组存储和切换查询。

**导出格式灵活** 支持导出为 JSON、Markdown 列表、纯文本和 SQL INSERT 语句，适配不同后端数据库需求。

**链接状态检测** 提供可选的在线状态检查功能，通过 HTTP HEAD 请求验证链接是否可访问，并记录状态码。

## 应用场景

**资讯站每日链接整理** 内容编辑每天需要从移动新闻源收集上百条文章链接，手动复制粘贴容易出错。本工具提供脚本化导入和校验流程，编辑只需将原始链接列表保存为 .txt 文件，运行一条命令即可完成清洗和分类，输出带时间戳的归档表。

**数据采集管道前置处理** 在数据采集系统中，原始爬虫输出的链接列表往往包含重复项和无效协议。本工具作为前置过滤节点，在进入深度采集之前对链接进行去重和格式化校验，确保采集队列只包含有效且唯一的 URL，减少无效请求对采集目标站点的压力。

**历史链接归档与检索** 对于运营超过一年的内容项目，历史新闻链接散落在多个文档和邮件中。本工具提供统一的导入接口，将不同批次的链接合并到同一个 SQLite 数据库中，并支持按批次编号（如 204/300）检索，方便查找某一批次的全部外链。

**迁移与备份校验** 当站点迁移或更换域名时，需要批量替换或验证原有外链的可用性。本工具支持链接前缀替换规则和批量状态检测，可快速生成迁移前后的对照表，帮助运维人员确认迁移完整性。

## 快速开始

以下步骤演示如何克隆项目、安装依赖并运行一次完整的链接导入流程。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行链接导入命令，指定批次编号和输入文件
python link_aggregator.py import --batch 204 --input ./samples/links_204.txt --output ./output/batch_204.json
```

若需要直接测试示例数据，项目根目录下的 `samples/links_204.txt` 已包含本批次的部分示例链接，运行上述命令即可生成 JSON 报告。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐 3.10 稳定版 |
| requests | 2.28.0 及以上 | 用于链接状态检测和 HTTP 请求 |
| click | 8.1.0 及以上 | 命令行交互框架，用于解析子命令参数 |
| sqlite3 | 内置模块 | 用于本地链接数据持久化存储 |
| pytest | 7.0.0 及以上 | 单元测试框架，仅开发环境需要 |
| black | 22.0.0 及以上 | 代码格式化工具，仅开发环境需要 |
| mypy | 0.990 及以上 | 类型检查工具，仅开发环境需要 |
| pre-commit | 2.20.0 及以上 | Git 提交钩子管理，仅贡献者需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/usage.md | 如何导入链接、去重配置、导出格式选择以及状态检测参数说明 |
| 开发指南 | docs/development.md | 项目代码结构、新增解析器的方法、单元测试编写规范 |
| 批次管理 | docs/batch_management.md | 批次编号规则、多批次数据合并策略、历史批次迁移步骤 |
| API 参考 | docs/api_reference.md | 核心模块 Link 类和 LinkAggregator 类的所有公开方法签名与返回值说明 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/68247.htm
- http://m.3g.bwbkj.cn/jnews/030898.htm
- http://m.3g.bwbkj.cn/jnews/71222.htm
- http://m.3g.bwbkj.cn/jnews/6493335.htm
- http://m.3g.bwbkj.cn/jnews/53391.htm
- http://m.3g.bwbkj.cn/jnews/20259.htm
- http://m.3g.bwbkj.cn/jnews/89335.htm
- http://m.3g.bwbkj.cn/jnews/39416.htm
- http://m.3g.bwbkj.cn/jnews/0908105.htm
- http://m.3g.bwbkj.cn/jnews/868656.htm
- http://m.3g.bwbkj.cn/jnews/75066.htm
- http://m.3g.bwbkj.cn/jnews/9687.htm
- http://m.3g.bwbkj.cn/jnews/770137.htm
- http://m.3g.bwbkj.cn/jnews/4915645.htm
- http://m.3g.bwbkj.cn/jnews/1144.htm
- http://m.3g.bwbkj.cn/jnews/6889049.htm
- http://m.3g.bwbkj.cn/jnews/31052.htm
- http://m.3g.bwbkj.cn/jnews/366837.htm
- http://m.3g.bwbkj.cn/jnews/6694266.htm
- http://m.3g.bwbkj.cn/jnews/7474.htm
- http://m.3g.bwbkj.cn/jnews/525955.htm
- http://m.3g.bwbkj.cn/jnews/9564.htm
- http://m.3g.bwbkj.cn/jnews/9829948.htm
- http://m.3g.bwbkj.cn/jnews/185919.htm
- http://m.3g.bwbkj.cn/jnews/796976.htm
- http://m.3g.bwbkj.cn/jnews/2067.htm
- http://m.3g.bwbkj.cn/jnews/6172.htm
- http://m.3g.bwbkj.cn/jnews/8790.htm
- http://m.3g.bwbkj.cn/jnews/3814764.htm
- http://m.3g.bwbkj.cn/jnews/61587.htm
- http://m.3g.bwbkj.cn/jnews/29680.htm
- http://m.3g.bwbkj.cn/jnews/2152.htm
- http://m.3g.bwbkj.cn/jnews/05393.htm
- http://m.3g.bwbkj.cn/jnews/05859.htm
- http://m.3g.bwbkj.cn/jnews/6222.htm
- http://m.3g.bwbkj.cn/jnews/2962604.htm
- http://m.3g.bwbkj.cn/jnews/7690750.htm
- http://m.3g.bwbkj.cn/jnews/08331.htm
- http://m.3g.bwbkj.cn/jnews/5284320.htm
- http://m.3g.bwbkj.cn/jnews/7961549.htm
- http://m.3g.bwbkj.cn/jnews/398081.htm
- http://m.3g.bwbkj.cn/jnews/6811491.htm
- http://m.3g.bwbkj.cn/jnews/6758.htm
- http://m.3g.bwbkj.cn/jnews/6390.htm
- http://m.3g.bwbkj.cn/jnews/8894500.htm
- http://m.3g.bwbkj.cn/jnews/4338530.htm
- http://m.3g.bwbkj.cn/jnews/025361.htm
- http://m.3g.bwbkj.cn/jnews/2940.htm
- http://m.3g.bwbkj.cn/jnews/8279.htm
- http://m.3g.bwbkj.cn/jnews/0364704.htm
- http://m.3g.bwbkj.cn/jnews/32284.htm
- http://m.3g.bwbkj.cn/jnews/711602.htm
- http://m.3g.bwbkj.cn/jnews/33166.htm
- http://m.3g.bwbkj.cn/jnews/40644.htm
- http://m.3g.bwbkj.cn/jnews/70839.htm
- http://m.3g.bwbkj.cn/jnews/7276107.htm
- http://m.3g.bwbkj.cn/jnews/1927821.htm
- http://m.3g.bwbkj.cn/jnews/9231.htm
- http://m.3g.bwbkj.cn/jnews/81865.htm
- http://m.3g.bwbkj.cn/jnews/702425.htm
- http://m.3g.bwbkj.cn/jnews/42310.htm
- http://m.3g.bwbkj.cn/jnews/9972585.htm
- http://m.3g.bwbkj.cn/jnews/6287.htm
- http://m.3g.bwbkj.cn/jnews/17729.htm
- http://m.3g.bwbkj.cn/jnews/978152.htm
- http://m.3g.bwbkj.cn/jnews/22320.htm
- http://m.3g.bwbkj.cn/jnews/9043593.htm
- http://m.3g.bwbkj.cn/jnews/091609.htm
- http://m.3g.bwbkj.cn/jnews/4597.htm
- http://m.3g.bwbkj.cn/jnews/3906604.htm
- http://m.3g.bwbkj.cn/jnews/44085.htm
- http://m.3g.bwbkj.cn/jnews/3297.htm
- http://m.3g.bwbkj.cn/jnews/3406956.htm
- http://m.3g.bwbkj.cn/jnews/87843.htm
- http://m.3g.bwbkj.cn/jnews/6724.htm
- http://m.3g.bwbkj.cn/jnews/810524.htm
- http://m.3g.bwbkj.cn/jnews/22564.htm
- http://m.3g.bwbkj.cn/jnews/8142575.htm
- http://m.3g.bwbkj.cn/jnews/7936170.htm
- http://m.3g.bwbkj.cn/jnews/7990.htm
- http://m.3g.bwbkj.cn/jnews/79366.htm
- http://m.3g.bwbkj.cn/jnews/7255.htm
- http://m.3g.bwbkj.cn/jnews/9317029.htm
- http://m.3g.bwbkj.cn/jnews/3007604.htm
- http://m.3g.bwbkj.cn/jnews/29058.htm
- http://m.3g.bwbkj.cn/jnews/604277.htm
- http://m.3g.bwbkj.cn/jnews/42799.htm
- http://m.3g.bwbkj.cn/jnews/667566.htm
- http://m.3g.bwbkj.cn/jnews/3214738.htm
- http://m.3g.bwbkj.cn/jnews/55843.htm
- http://m.3g.bwbkj.cn/jnews/40204.htm
- http://m.3g.bwbkj.cn/jnews/9537.htm
- http://m.3g.bwbkj.cn/jnews/1853.htm
- http://m.3g.bwbkj.cn/jnews/918152.htm
- http://m.3g.bwbkj.cn/jnews/5890.htm
- http://m.3g.bwbkj.cn/jnews/4180.htm
- http://m.3g.bwbkj.cn/jnews/77120.htm
- http://m.3g.bwbkj.cn/jnews/127304.htm
- http://m.3g.bwbkj.cn/jnews/8776.htm
- http://m.3g.bwbkj.cn/jnews/1625941.htm
- http://m.3g.bwbkj.cn/jnews/8279055.htm
- http://m.3g.bwbkj.cn/jnews/9004.htm
- http://m.3g.bwbkj.cn/jnews/398636.htm
- http://m.3g.bwbkj.cn/jnews/3548.htm
- http://m.3g.bwbkj.cn/jnews/3725242.htm
- http://m.3g.bwbkj.cn/jnews/37268.htm
- http://m.3g.bwbkj.cn/jnews/9728.htm
- http://m.3g.bwbkj.cn/jnews/80292.htm
- http://m.3g.bwbkj.cn/jnews/30012.htm
- http://m.3g.bwbkj.cn/jnews/14498.htm
- http://m.3g.bwbkj.cn/jnews/2572755.htm
- http://m.3g.bwbkj.cn/jnews/282705.htm
- http://m.3g.bwbkj.cn/jnews/3941551.htm
- http://m.3g.bwbkj.cn/jnews/4997857.htm
- http://m.3g.bwbkj.cn/jnews/9590.htm
- http://m.3g.bwbkj.cn/jnews/924299.htm
- http://m.3g.bwbkj.cn/jnews/2380.htm
- http://m.3g.bwbkj.cn/jnews/935533.htm
- http://m.3g.bwbkj.cn/jnews/5011.htm
- http://m.3g.bwbkj.cn/jnews/01241.htm
- http://m.3g.bwbkj.cn/jnews/9398.htm
- http://m.3g.bwbkj.cn/jnews/25645.htm
- http://m.3g.bwbkj.cn/jnews/61739.htm
- http://m.3g.bwbkj.cn/jnews/2137.htm
- http://m.3g.bwbkj.cn/jnews/970020.htm
- http://m.3g.bwbkj.cn/jnews/949086.htm
- http://m.3g.bwbkj.cn/jnews/1984.htm
- http://m.3g.bwbkj.cn/jnews/5914247.htm
- http://m.3g.bwbkj.cn/jnews/9169573.htm
- http://m.3g.bwbkj.cn/jnews/13637.htm
- http://m.3g.bwbkj.cn/jnews/5851842.htm
- http://m.3g.bwbkj.cn/jnews/287968.htm
- http://m.3g.bwbkj.cn/jnews/03340.htm
- http://m.3g.bwbkj.cn/jnews/062511.htm
- http://m.3g.bwbkj.cn/jnews/25577.htm
- http://m.3g.bwbkj.cn/jnews/5006.htm
- http://m.3g.bwbkj.cn/jnews/9857403.htm
- http://m.3g.bwbkj.cn/jnews/1927618.htm
- http://m.3g.bwbkj.cn/jnews/59706.htm
- http://m.3g.bwbkj.cn/jnews/36825.htm
- http://m.3g.bwbkj.cn/jnews/58362.htm
- http://m.3g.bwbkj.cn/jnews/30806.htm
- http://m.3g.bwbkj.cn/jnews/5530254.htm
- http://m.3g.bwbkj.cn/jnews/9755.htm
- http://m.3g.bwbkj.cn/jnews/59515.htm
- http://m.3g.bwbkj.cn/jnews/009575.htm
- http://m.3g.bwbkj.cn/jnews/029781.htm
- http://m.3g.bwbkj.cn/jnews/54824.htm
- http://m.3g.bwbkj.cn/jnews/2658.htm
- http://m.3g.bwbkj.cn/jnews/665238.htm
- http://m.3g.bwbkj.cn/jnews/2056497.htm
- http://m.3g.bwbkj.cn/jnews/73108.htm
- http://m.3g.bwbkj.cn/jnews/4728839.htm
- http://m.3g.bwbkj.cn/jnews/6184.htm
- http://m.3g.bwbkj.cn/jnews/275678.htm
- http://m.3g.bwbkj.cn/jnews/191275.htm
- http://m.3g.bwbkj.cn/jnews/855916.htm
- http://m.3g.bwbkj.cn/jnews/65434.htm
- http://m.3g.bwbkj.cn/jnews/3109605.htm
- http://m.3g.bwbkj.cn/jnews/7494.htm
- http://m.3g.bwbkj.cn/jnews/6529451.htm
- http://m.3g.bwbkj.cn/jnews/831919.htm
- http://m.3g.bwbkj.cn/jnews/02629.htm
- http://m.3g.bwbkj.cn/jnews/49283.htm
- http://m.3g.bwbkj.cn/jnews/6728299.htm
- http://m.3g.bwbkj.cn/jnews/317831.htm
- http://m.3g.bwbkj.cn/jnews/3402.htm
- http://m.3g.bwbkj.cn/jnews/8857.htm
- http://m.3g.bwbkj.cn/jnews/364637.htm
- http://m.3g.bwbkj.cn/jnews/34392.htm
- http://m.3g.bwbkj.cn/jnews/1250.htm
- http://m.3g.bwbkj.cn/jnews/7903.htm
- http://m.3g.bwbkj.cn/jnews/20871.htm
- http://m.3g.bwbkj.cn/jnews/362065.htm
- http://m.3g.bwbkj.cn/jnews/7460493.htm
- http://m.3g.bwbkj.cn/jnews/88589.htm
- http://m.3g.bwbkj.cn/jnews/358142.htm
- http://m.3g.bwbkj.cn/jnews/2301717.htm
- http://m.3g.bwbkj.cn/jnews/78799.htm
- http://m.3g.bwbkj.cn/jnews/722284.htm
- http://m.3g.bwbkj.cn/jnews/68644.htm
- http://m.3g.bwbkj.cn/jnews/7481018.htm
- http://m.3g.bwbkj.cn/jnews/42950.htm
- http://m.3g.bwbkj.cn/jnews/5186.htm
- http://m.3g.bwbkj.cn/jnews/300624.htm
- http://m.3g.bwbkj.cn/jnews/5157183.htm
- http://m.3g.bwbkj.cn/jnews/402123.htm
- http://m.3g.bwbkj.cn/jnews/2734453.htm
- http://m.3g.bwbkj.cn/jnews/79044.htm
- http://m.3g.bwbkj.cn/jnews/270477.htm
- http://m.3g.bwbkj.cn/jnews/899150.htm
- http://m.3g.bwbkj.cn/jnews/9030.htm
- http://m.3g.bwbkj.cn/jnews/793527.htm
- http://m.3g.bwbkj.cn/jnews/2724.htm
- http://m.3g.bwbkj.cn/jnews/42092.htm
- http://m.3g.bwbkj.cn/jnews/0701.htm
- http://m.3g.bwbkj.cn/jnews/97045.htm
- http://m.3g.bwbkj.cn/jnews/6911.htm
- http://m.3g.bwbkj.cn/jnews/374246.htm
- http://m.3g.bwbkj.cn/jnews/5633.htm
- http://m.3g.bwbkj.cn/jnews/9428.htm
- http://m.3g.bwbkj.cn/jnews/3538957.htm
- http://m.3g.bwbkj.cn/jnews/7955.htm
- http://m.3g.bwbkj.cn/jnews/0528.htm
- http://m.3g.bwbkj.cn/jnews/7114.htm
- http://m.3g.bwbkj.cn/jnews/54427.htm
- http://m.3g.bwbkj.cn/jnews/0725914.htm
- http://m.3g.bwbkj.cn/jnews/4632007.htm
- http://m.3g.bwbkj.cn/jnews/8708.htm
- http://m.3g.bwbkj.cn/jnews/6534.htm
- http://m.3g.bwbkj.cn/jnews/1681.htm
- http://m.3g.bwbkj.cn/jnews/5437557.htm
- http://m.3g.bwbkj.cn/jnews/7909983.htm
- http://m.3g.bwbkj.cn/jnews/33176.htm
- http://m.3g.bwbkj.cn/jnews/63289.htm
- http://m.3g.bwbkj.cn/jnews/8248206.htm
- http://m.3g.bwbkj.cn/jnews/12421.htm
- http://m.3g.bwbkj.cn/jnews/0513.htm
- http://m.3g.bwbkj.cn/jnews/5552.htm
- http://m.3g.bwbkj.cn/jnews/12220.htm
- http://m.3g.bwbkj.cn/jnews/587532.htm
- http://m.3g.bwbkj.cn/jnews/823302.htm
- http://m.3g.bwbkj.cn/jnews/37790.htm
- http://m.3g.bwbkj.cn/jnews/976950.htm
- http://m.3g.bwbkj.cn/jnews/41646.htm
- http://m.3g.bwbkj.cn/jnews/77911.htm
- http://m.3g.bwbkj.cn/jnews/571804.htm
- http://m.3g.bwbkj.cn/jnews/375338.htm
- http://m.3g.bwbkj.cn/jnews/36337.htm
- http://m.3g.bwbkj.cn/jnews/34706.htm
- http://m.3g.bwbkj.cn/jnews/293918.htm
- http://m.3g.bwbkj.cn/jnews/565278.htm
- http://m.3g.bwbkj.cn/jnews/5119.htm
- http://m.3g.bwbkj.cn/jnews/6300.htm
- http://m.3g.bwbkj.cn/jnews/8285569.htm
- http://m.3g.bwbkj.cn/jnews/87047.htm
- http://m.3g.bwbkj.cn/jnews/891434.htm
- http://m.3g.bwbkj.cn/jnews/721172.htm
- http://m.3g.bwbkj.cn/jnews/51311.htm
- http://m.3g.bwbkj.cn/jnews/462549.htm
- http://m.3g.bwbkj.cn/jnews/553137.htm
- http://m.3g.bwbkj.cn/jnews/0012282.htm
- http://m.3g.bwbkj.cn/jnews/3189.htm
- http://m.3g.bwbkj.cn/jnews/7133743.htm
- http://m.3g.bwbkj.cn/jnews/686818.htm
- http://m.3g.bwbkj.cn/jnews/76540.htm
- http://m.3g.bwbkj.cn/jnews/499648.htm
- http://m.3g.bwbkj.cn/jnews/648049.htm
- http://m.3g.bwbkj.cn/jnews/5978566.htm
- http://m.3g.bwbkj.cn/jnews/85614.htm
- http://m.3g.bwbkj.cn/jnews/6670179.htm
- http://m.3g.bwbkj.cn/jnews/2436865.htm
- http://m.3g.bwbkj.cn/jnews/28601.htm
- http://m.3g.bwbkj.cn/jnews/368125.htm
- http://m.3g.bwbkj.cn/jnews/8272526.htm
- http://m.3g.bwbkj.cn/jnews/8219968.htm
- http://m.3g.bwbkj.cn/jnews/517874.htm
- http://m.3g.bwbkj.cn/jnews/209697.htm
- http://m.3g.bwbkj.cn/jnews/729069.htm
- http://m.3g.bwbkj.cn/jnews/7229461.htm
- http://m.3g.bwbkj.cn/jnews/73544.htm
- http://m.3g.bwbkj.cn/jnews/9967.htm
- http://m.3g.bwbkj.cn/jnews/017175.htm
- http://m.3g.bwbkj.cn/jnews/726385.htm
- http://m.3g.bwbkj.cn/jnews/25981.htm
- http://m.3g.bwbkj.cn/jnews/547454.htm
- http://m.3g.bwbkj.cn/jnews/116675.htm
- http://m.3g.bwbkj.cn/jnews/5959.htm
- http://m.3g.bwbkj.cn/jnews/37707.htm
- http://m.3g.bwbkj.cn/jnews/16314.htm
- http://m.3g.bwbkj.cn/jnews/31369.htm
- http://m.3g.bwbkj.cn/jnews/6664749.htm
- http://m.3g.bwbkj.cn/jnews/94513.htm
- http://m.3g.bwbkj.cn/jnews/933181.htm
- http://m.3g.bwbkj.cn/jnews/32663.htm
- http://m.3g.bwbkj.cn/jnews/0732930.htm
- http://m.3g.bwbkj.cn/jnews/1103.htm
- http://m.3g.bwbkj.cn/jnews/53041.htm
- http://m.3g.bwbkj.cn/jnews/9011086.htm
- http://m.3g.bwbkj.cn/jnews/865898.htm
- http://m.3g.bwbkj.cn/jnews/61223.htm
- http://m.3g.bwbkj.cn/jnews/2855.htm
- http://m.3g.bwbkj.cn/jnews/128983.htm
- http://m.3g.bwbkj.cn/jnews/509457.htm
- http://m.3g.bwbkj.cn/jnews/163908.htm
- http://m.3g.bwbkj.cn/jnews/3424.htm
- http://m.3g.bwbkj.cn/jnews/52929.htm
- http://m.3g.bwbkj.cn/jnews/057134.htm
- http://m.3g.bwbkj.cn/jnews/5352365.htm
- http://m.3g.bwbkj.cn/jnews/32778.htm
- http://m.3g.bwbkj.cn/jnews/6824016.htm
- http://m.3g.bwbkj.cn/jnews/1821.htm
- http://m.3g.bwbkj.cn/jnews/043225.htm
- http://m.3g.bwbkj.cn/jnews/0974406.htm
- http://m.3g.bwbkj.cn/jnews/5743507.htm
- http://m.3g.bwbkj.cn/jnews/131619.htm
- http://m.3g.bwbkj.cn/jnews/903638.htm
- http://m.3g.bwbkj.cn/jnews/8678598.htm
- http://m.3g.bwbkj.cn/jnews/027949.htm
- http://m.3g.bwbkj.cn/jnews/19133.htm

## 项目结构

```
jnews-link-aggregator/
├── link_aggregator.py          # 主入口命令行工具，注册 import、export、check 子命令
├── requirements.txt            # 生产环境依赖列表，包含 requests 和 click
├── setup.py                    # 包安装配置，定义项目元数据和 entry_points
├── pyproject.toml              # 格式化与类型检查工具配置（black、mypy）
├── .pre-commit-config.yaml     # Git 提交前钩子配置，自动运行格式检查
├── src/                        # 核心源码目录
│   ├── __init__.py
│   ├── parser.py               # URL 解析模块，提取域名、文章ID和扩展名
│   ├── aggregator.py           # 链接聚合器核心类，管理批次和去重逻辑
│   ├── storage.py              # SQLite 存储层，提供增删改查接口
│   ├── checker.py              # 链接状态检测模块，并发 HEAD 请求
│   └── exporter.py             # 导出模块，支持 JSON、Markdown、SQL 格式
├── tests/                      # 单元测试目录
│   ├── test_parser.py          # 测试 URL 解析边界情况，包含异常输入
│   ├── test_aggregator.py      # 测试去重和批次合并逻辑
│   └── test_checker.py         # 测试状态检测的超时和重试机制
├── docs/                       # 用户文档和开发文档
│   ├── usage.md                # 详细使用教程，附带示例截图说明
│   ├── development.md          # 开发环境搭建和 PR 提交规范
│   ├── batch_management.md     # 批次编号规则和数据迁移步骤
│   └── api_reference.md        # 从 docstring 生成的核心 API 参考
├── samples/                    # 示例数据文件
│   ├── links_204.txt           # 第 204 批次示例链接列表
│   └── output_sample.json      # 导入后生成的示例输出报告
└── scripts/                    # 辅助运维脚本
    ├── init_db.py              # 初始化 SQLite 数据库表结构
    └── migrate_batch.py        # 跨批次数据迁移和校验工具
```

## 贡献指南

欢迎提交问题报告、功能建议和代码贡献。请遵循以下流程以确保贡献被顺利审核和合并。

第一，在 GitHub Issues 中搜索是否存在相似或相关的问题，避免重复提交。若未找到，请新建 Issue 并选择对应的模板（Bug 报告或功能请求），清晰描述当前行为和期望行为，附上可重现的最小示例或日志片段。

第二，Fork 本仓库到个人账户，在本地创建新的功能分支，分支命名遵循 `feature/简述` 或 `fix/简述` 格式，例如 `feature/add-csv-export`。请确保分支基于最新的 main 分支创建。

第三，提交代码前运行 `pre-commit run --all-files` 确保代码格式符合 black 和 mypy 检查，并补充相应的单元测试覆盖新增或修改的代码路径。测试用例需放置在 tests/ 目录下对应的文件中，确保 `pytest` 全部通过。

第四，提交 Pull Request 时，在描述中关联对应的 Issue 编号，列出本 PR 所做的具体变更、测试结果以及是否影响现有 API 兼容性。等待至少一位维护者审核，根据反馈进行修改直至合并。

## 常见问题

**导入链接时程序报错 "Invalid URL format" 如何处理？**

该错误通常因为输入文件中包含空行、空格或非 HTTP/HTTPS 协议的文本。请检查输入文件每一行是否均为完整的 URL 字符串，且不包含多余的前后空白字符。本工具要求每行一个 URL，不支持逗号分隔或表格形式。若确认格式无误仍报错，可尝试使用 `--strict false` 参数跳过非标准行的校验，程序会记录跳过行数并在日志中输出警告。

**如何查看某一批次已导入的全部链接列表？**

使用 `list` 子命令并按批次编号过滤。例如 `python link_aggregator.py list --batch 204` 会输出该批次所有链接的文章ID和导入时间戳。若需要导出为文件，可结合 `export` 命令，如 `python link_aggregator.py export --batch 204 --format markdown --output batch_204.md`，生成的 Markdown 列表可直接用于文档或报告。

**状态检测很慢，能否调整超时或并发数？**

可以。状态检测模块默认超时时间为 5 秒，并发数为 10 个线程。若网络环境较差或链接数量极大，可通过配置文件 `config.yaml` 中的 `checker.timeout` 和 `checker.max_workers` 字段调整。也支持命令行覆盖：`python link_aggregator.py check --timeout 3 --workers 5`。建议根据目标站点的响应速度合理设置，避免被目标服务器误判为攻击行为。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:59
