# Oexnr News Resource Aggregator

Oexnr News Resource Aggregator 是一个面向移动端新闻资讯聚合与分发场景的开源外链管理工具。该项目定位于为内容运营团队、个人站长以及新闻聚合类应用开发者提供一套标准化的新闻条目采集、归档与展示方案。通过结构化的链接管理机制，项目能够高效处理大规模新闻资源条目，支持按批次、按分类对海量外链进行整理与呈现，适用于需要定期更新大量新闻索引的技术场景。

本项目不对新闻内容本身进行存储或修改，仅作为新闻资源链接的索引层与展示层。项目核心受众包括从事内容聚合的技术人员、需要快速构建新闻列表的轻量级站点运营者，以及希望将外部新闻源整合进自身技术栈的开发者。

## 功能概览

**批次化资源管理**：项目内建批次管理能力，当前为第 65/300 批次，支持将大量外链按批次导入、分类与展示，便于运营人员追踪资源入库进度与状态。

**移动端适配链接索引**：针对移动端新闻阅读场景设计链接索引结构，所有资源条目均以移动端 URL 格式存储，确保在手机端访问时获得良好的页面适配效果。

**自动化目录树生成**：项目启动后自动根据资源条目生成 ASCII 目录树，以可视化方式呈现新闻资源在项目中的存储路径与分类层级，方便开发者快速定位。

**结构化元数据提取**：每条新闻链接均支持附加元数据字段，包括入库时间、批次编号、资源类型标识等，为后续的数据分析与检索提供结构化基础。

**命令行快速操作**：提供完整的命令行工具集，支持资源列表的导入、导出、查重与校验，满足自动化运维与持续集成场景下的操作需求。

**低依赖轻量部署**：项目核心逻辑仅依赖标准 Python 环境与基础文件读写库，无需额外数据库或中间件即可完成新闻资源列表的生成与展示。

**可扩展模板系统**：支持自定义展示模板，开发者可根据业务需求调整新闻列表的渲染样式与输出格式，适配不同的前端框架或静态站点生成器。

## 应用场景

移动新闻聚合站点的链接索引维护。运营人员需要每日更新数百条新闻外链，本项目提供批量化导入与展示能力，将原始链接列表转化为结构清晰、可在线访问的新闻目录，显著降低人工整理与发布的时间成本。

个人技术博客的新闻推荐模块。开发者可在个人站点中集成本项目生成的新闻列表，作为站内资讯推荐或友情链接板块的数据源，提升博客内容维度的丰富性。

新闻资源采集系统的数据预览层。数据采集团队在后台完成新闻 URL 抓取后，可通过本项目快速生成可供外部访问的资源索引页面，便于内部审核与外部合作方查阅。

轻量级静态站点的内容填充方案。对于使用静态站点生成器构建的网站，本项目可作为内容插件使用，将新闻链接列表以结构化方式嵌入站点页面，无需依赖动态后端服务。

## 快速开始

```bash
# 克隆项目仓库
git clone https://github.com/oexnr/news-resource-aggregator.git

# 进入项目目录
cd news-resource-aggregator

# 安装基础依赖（仅需 Python 标准库）
pip install -r requirements.txt

# 运行资源列表生成脚本
python build.py --batch 65 --input resources.txt --output dist/index.html
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行构建脚本与模板渲染 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| Git | 2.25 及以上 | 版本控制工具，用于克隆仓库与版本管理 |
| 文件系统读写权限 | 必需 | 项目需要读取资源列表文件并写入生成结果 |
| 网络连接 | 可选 | 仅在需要在线验证链接可达性时需要 |
| 终端环境 | 必需 | 用于执行命令行操作与查看输出日志 |
| 文本编辑器 | 可选 | 用于编辑配置文件或自定义模板内容 |
| 静态 HTTP 服务器 | 可选 | 用于本地预览生成的 HTML 页面 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速搭建项目环境并生成第一批新闻资源列表 |
| 批次管理 | docs/batch-management.md | 如何管理不同批次的资源条目，包括导入、删除与版本回溯 |
| 模板定制 | docs/template-customization.md | 如何修改展示模板以适配不同的前端样式与布局需求 |
| 命令行参考 | docs/cli-reference.md | 所有可用命令的完整参数说明与使用示例 |
| 常见问题 | docs/faq.md | 部署与使用过程中常见问题的解决方案 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/5577087.htm
- http://m.wap.oexnr.cn/jnews/7027725.htm
- http://m.wap.oexnr.cn/jnews/08687.htm
- http://m.wap.oexnr.cn/jnews/08128.htm
- http://m.wap.oexnr.cn/jnews/65871.htm
- http://m.wap.oexnr.cn/jnews/73445.htm
- http://m.wap.oexnr.cn/jnews/34446.htm
- http://m.wap.oexnr.cn/jnews/8242537.htm
- http://m.wap.oexnr.cn/jnews/258238.htm
- http://m.wap.oexnr.cn/jnews/7973.htm
- http://m.wap.oexnr.cn/jnews/672490.htm
- http://m.wap.oexnr.cn/jnews/2601013.htm
- http://m.wap.oexnr.cn/jnews/536524.htm
- http://m.wap.oexnr.cn/jnews/4071.htm
- http://m.wap.oexnr.cn/jnews/3808335.htm
- http://m.wap.oexnr.cn/jnews/9132025.htm
- http://m.wap.oexnr.cn/jnews/7115.htm
- http://m.wap.oexnr.cn/jnews/752124.htm
- http://m.wap.oexnr.cn/jnews/8557.htm
- http://m.wap.oexnr.cn/jnews/5473.htm
- http://m.wap.oexnr.cn/jnews/450427.htm
- http://m.wap.oexnr.cn/jnews/3003854.htm
- http://m.wap.oexnr.cn/jnews/3820.htm
- http://m.wap.oexnr.cn/jnews/98473.htm
- http://m.wap.oexnr.cn/jnews/45192.htm
- http://m.wap.oexnr.cn/jnews/283950.htm
- http://m.wap.oexnr.cn/jnews/6697.htm
- http://m.wap.oexnr.cn/jnews/8090.htm
- http://m.wap.oexnr.cn/jnews/4734818.htm
- http://m.wap.oexnr.cn/jnews/2885981.htm
- http://m.wap.oexnr.cn/jnews/292253.htm
- http://m.wap.oexnr.cn/jnews/2263437.htm
- http://m.wap.oexnr.cn/jnews/1074889.htm
- http://m.wap.oexnr.cn/jnews/41846.htm
- http://m.wap.oexnr.cn/jnews/2705226.htm
- http://m.wap.oexnr.cn/jnews/79774.htm
- http://m.wap.oexnr.cn/jnews/47524.htm
- http://m.wap.oexnr.cn/jnews/39947.htm
- http://m.wap.oexnr.cn/jnews/49451.htm
- http://m.wap.oexnr.cn/jnews/4919800.htm
- http://m.wap.oexnr.cn/jnews/3604.htm
- http://m.wap.oexnr.cn/jnews/22987.htm
- http://m.wap.oexnr.cn/jnews/5067.htm
- http://m.wap.oexnr.cn/jnews/19063.htm
- http://m.wap.oexnr.cn/jnews/36235.htm
- http://m.wap.oexnr.cn/jnews/287577.htm
- http://m.wap.oexnr.cn/jnews/8979.htm
- http://m.wap.oexnr.cn/jnews/6140.htm
- http://m.wap.oexnr.cn/jnews/3057.htm
- http://m.wap.oexnr.cn/jnews/1556971.htm
- http://m.wap.oexnr.cn/jnews/7697.htm
- http://m.wap.oexnr.cn/jnews/62298.htm
- http://m.wap.oexnr.cn/jnews/41081.htm
- http://m.wap.oexnr.cn/jnews/9215557.htm
- http://m.wap.oexnr.cn/jnews/698167.htm
- http://m.wap.oexnr.cn/jnews/96841.htm
- http://m.wap.oexnr.cn/jnews/0041700.htm
- http://m.wap.oexnr.cn/jnews/701291.htm
- http://m.wap.oexnr.cn/jnews/4890438.htm
- http://m.wap.oexnr.cn/jnews/9633924.htm
- http://m.wap.oexnr.cn/jnews/442967.htm
- http://m.wap.oexnr.cn/jnews/0041.htm
- http://m.wap.oexnr.cn/jnews/3765.htm
- http://m.wap.oexnr.cn/jnews/14036.htm
- http://m.wap.oexnr.cn/jnews/87491.htm
- http://m.wap.oexnr.cn/jnews/365441.htm
- http://m.wap.oexnr.cn/jnews/393442.htm
- http://m.wap.oexnr.cn/jnews/97385.htm
- http://m.wap.oexnr.cn/jnews/742084.htm
- http://m.wap.oexnr.cn/jnews/679883.htm
- http://m.wap.oexnr.cn/jnews/1374393.htm
- http://m.wap.oexnr.cn/jnews/3351376.htm
- http://m.wap.oexnr.cn/jnews/98500.htm
- http://m.wap.oexnr.cn/jnews/6631840.htm
- http://m.wap.oexnr.cn/jnews/90271.htm
- http://m.wap.oexnr.cn/jnews/8995.htm
- http://m.wap.oexnr.cn/jnews/300652.htm
- http://m.wap.oexnr.cn/jnews/56011.htm
- http://m.wap.oexnr.cn/jnews/8231.htm
- http://m.wap.oexnr.cn/jnews/5947326.htm
- http://m.wap.oexnr.cn/jnews/64200.htm
- http://m.wap.oexnr.cn/jnews/24890.htm
- http://m.wap.oexnr.cn/jnews/32494.htm
- http://m.wap.oexnr.cn/jnews/1550843.htm
- http://m.wap.oexnr.cn/jnews/9182.htm
- http://m.wap.oexnr.cn/jnews/3079.htm
- http://m.wap.oexnr.cn/jnews/462940.htm
- http://m.wap.oexnr.cn/jnews/2168.htm
- http://m.wap.oexnr.cn/jnews/60163.htm
- http://m.wap.oexnr.cn/jnews/42810.htm
- http://m.wap.oexnr.cn/jnews/2872.htm
- http://m.wap.oexnr.cn/jnews/938121.htm
- http://m.wap.oexnr.cn/jnews/8408.htm
- http://m.wap.oexnr.cn/jnews/7355953.htm
- http://m.wap.oexnr.cn/jnews/1732.htm
- http://m.wap.oexnr.cn/jnews/5727.htm
- http://m.wap.oexnr.cn/jnews/6380858.htm
- http://m.wap.oexnr.cn/jnews/7103.htm
- http://m.wap.oexnr.cn/jnews/4913117.htm
- http://m.wap.oexnr.cn/jnews/685132.htm
- http://m.wap.oexnr.cn/jnews/94889.htm
- http://m.wap.oexnr.cn/jnews/85214.htm
- http://m.wap.oexnr.cn/jnews/0875.htm
- http://m.wap.oexnr.cn/jnews/0340096.htm
- http://m.wap.oexnr.cn/jnews/887581.htm
- http://m.wap.oexnr.cn/jnews/93495.htm
- http://m.wap.oexnr.cn/jnews/6636652.htm
- http://m.wap.oexnr.cn/jnews/05630.htm
- http://m.wap.oexnr.cn/jnews/3140949.htm
- http://m.wap.oexnr.cn/jnews/73214.htm
- http://m.wap.oexnr.cn/jnews/53989.htm
- http://m.wap.oexnr.cn/jnews/3981.htm
- http://m.wap.oexnr.cn/jnews/7870.htm
- http://m.wap.oexnr.cn/jnews/4328.htm
- http://m.wap.oexnr.cn/jnews/6779.htm
- http://m.wap.oexnr.cn/jnews/50268.htm
- http://m.wap.oexnr.cn/jnews/7318346.htm
- http://m.wap.oexnr.cn/jnews/418825.htm
- http://m.wap.oexnr.cn/jnews/3117763.htm
- http://m.wap.oexnr.cn/jnews/3414.htm
- http://m.wap.oexnr.cn/jnews/532711.htm
- http://m.wap.oexnr.cn/jnews/56177.htm
- http://m.wap.oexnr.cn/jnews/0278204.htm
- http://m.wap.oexnr.cn/jnews/67379.htm
- http://m.wap.oexnr.cn/jnews/8219.htm
- http://m.wap.oexnr.cn/jnews/961210.htm
- http://m.wap.oexnr.cn/jnews/9922292.htm
- http://m.wap.oexnr.cn/jnews/2121569.htm
- http://m.wap.oexnr.cn/jnews/56996.htm
- http://m.wap.oexnr.cn/jnews/04431.htm
- http://m.wap.oexnr.cn/jnews/87705.htm
- http://m.wap.oexnr.cn/jnews/66609.htm
- http://m.wap.oexnr.cn/jnews/1824.htm
- http://m.wap.oexnr.cn/jnews/77711.htm
- http://m.wap.oexnr.cn/jnews/09786.htm
- http://m.wap.oexnr.cn/jnews/653088.htm
- http://m.wap.oexnr.cn/jnews/986605.htm
- http://m.wap.oexnr.cn/jnews/51870.htm
- http://m.wap.oexnr.cn/jnews/7165.htm
- http://m.wap.oexnr.cn/jnews/71654.htm
- http://m.wap.oexnr.cn/jnews/85229.htm
- http://m.wap.oexnr.cn/jnews/125530.htm
- http://m.wap.oexnr.cn/jnews/269687.htm
- http://m.wap.oexnr.cn/jnews/6144.htm
- http://m.wap.oexnr.cn/jnews/610848.htm
- http://m.wap.oexnr.cn/jnews/9445.htm
- http://m.wap.oexnr.cn/jnews/11151.htm
- http://m.wap.oexnr.cn/jnews/71859.htm
- http://m.wap.oexnr.cn/jnews/997248.htm
- http://m.wap.oexnr.cn/jnews/4352078.htm
- http://m.wap.oexnr.cn/jnews/6250.htm
- http://m.wap.oexnr.cn/jnews/692127.htm
- http://m.wap.oexnr.cn/jnews/227883.htm
- http://m.wap.oexnr.cn/jnews/59194.htm
- http://m.wap.oexnr.cn/jnews/6461158.htm
- http://m.wap.oexnr.cn/jnews/69275.htm
- http://m.wap.oexnr.cn/jnews/7766.htm
- http://m.wap.oexnr.cn/jnews/8492600.htm
- http://m.wap.oexnr.cn/jnews/4303096.htm
- http://m.wap.oexnr.cn/jnews/1778.htm
- http://m.wap.oexnr.cn/jnews/30996.htm
- http://m.wap.oexnr.cn/jnews/7994.htm
- http://m.wap.oexnr.cn/jnews/978023.htm
- http://m.wap.oexnr.cn/jnews/752551.htm
- http://m.wap.oexnr.cn/jnews/150312.htm
- http://m.wap.oexnr.cn/jnews/509654.htm
- http://m.wap.oexnr.cn/jnews/2752649.htm
- http://m.wap.oexnr.cn/jnews/16485.htm
- http://m.wap.oexnr.cn/jnews/782940.htm
- http://m.wap.oexnr.cn/jnews/943650.htm
- http://m.wap.oexnr.cn/jnews/6469.htm
- http://m.wap.oexnr.cn/jnews/12203.htm
- http://m.wap.oexnr.cn/jnews/7858630.htm
- http://m.wap.oexnr.cn/jnews/2108159.htm
- http://m.wap.oexnr.cn/jnews/6201.htm
- http://m.wap.oexnr.cn/jnews/777451.htm
- http://m.wap.oexnr.cn/jnews/8616.htm
- http://m.wap.oexnr.cn/jnews/12418.htm
- http://m.wap.oexnr.cn/jnews/8124.htm
- http://m.wap.oexnr.cn/jnews/1747571.htm
- http://m.wap.oexnr.cn/jnews/5098314.htm
- http://m.wap.oexnr.cn/jnews/3918.htm
- http://m.wap.oexnr.cn/jnews/89061.htm
- http://m.wap.oexnr.cn/jnews/4992.htm
- http://m.wap.oexnr.cn/jnews/21406.htm
- http://m.wap.oexnr.cn/jnews/3634.htm
- http://m.wap.oexnr.cn/jnews/2501319.htm
- http://m.wap.oexnr.cn/jnews/5203214.htm
- http://m.wap.oexnr.cn/jnews/473811.htm
- http://m.wap.oexnr.cn/jnews/8970.htm
- http://m.wap.oexnr.cn/jnews/476914.htm
- http://m.wap.oexnr.cn/jnews/1594.htm
- http://m.wap.oexnr.cn/jnews/1427534.htm
- http://m.wap.oexnr.cn/jnews/1776.htm
- http://m.wap.oexnr.cn/jnews/7972.htm
- http://m.wap.oexnr.cn/jnews/676316.htm
- http://m.wap.oexnr.cn/jnews/001769.htm
- http://m.wap.oexnr.cn/jnews/410541.htm
- http://m.wap.oexnr.cn/jnews/9188594.htm
- http://m.wap.oexnr.cn/jnews/2567527.htm
- http://m.wap.oexnr.cn/jnews/570723.htm
- http://m.wap.oexnr.cn/jnews/4633.htm
- http://m.wap.oexnr.cn/jnews/5922.htm
- http://m.wap.oexnr.cn/jnews/4722.htm
- http://m.wap.oexnr.cn/jnews/9334877.htm
- http://m.wap.oexnr.cn/jnews/1304.htm
- http://m.wap.oexnr.cn/jnews/135052.htm
- http://m.wap.oexnr.cn/jnews/08957.htm
- http://m.wap.oexnr.cn/jnews/0880125.htm
- http://m.wap.oexnr.cn/jnews/321271.htm
- http://m.wap.oexnr.cn/jnews/7521165.htm
- http://m.wap.oexnr.cn/jnews/470146.htm
- http://m.wap.oexnr.cn/jnews/28740.htm
- http://m.wap.oexnr.cn/jnews/4091.htm
- http://m.wap.oexnr.cn/jnews/348617.htm
- http://m.wap.oexnr.cn/jnews/561395.htm
- http://m.wap.oexnr.cn/jnews/1231474.htm
- http://m.wap.oexnr.cn/jnews/22282.htm
- http://m.wap.oexnr.cn/jnews/1705.htm
- http://m.wap.oexnr.cn/jnews/6172793.htm
- http://m.wap.oexnr.cn/jnews/1336.htm
- http://m.wap.oexnr.cn/jnews/82543.htm
- http://m.wap.oexnr.cn/jnews/975642.htm
- http://m.wap.oexnr.cn/jnews/7982744.htm
- http://m.wap.oexnr.cn/jnews/174997.htm
- http://m.wap.oexnr.cn/jnews/6851912.htm
- http://m.wap.oexnr.cn/jnews/16169.htm
- http://m.wap.oexnr.cn/jnews/8642079.htm
- http://m.wap.oexnr.cn/jnews/4979.htm
- http://m.wap.oexnr.cn/jnews/4180.htm
- http://m.wap.oexnr.cn/jnews/25876.htm
- http://m.wap.oexnr.cn/jnews/8058.htm
- http://m.wap.oexnr.cn/jnews/9791.htm
- http://m.wap.oexnr.cn/jnews/8097866.htm
- http://m.wap.oexnr.cn/jnews/49296.htm
- http://m.wap.oexnr.cn/jnews/72427.htm
- http://m.wap.oexnr.cn/jnews/820434.htm
- http://m.wap.oexnr.cn/jnews/5841398.htm
- http://m.wap.oexnr.cn/jnews/2972558.htm
- http://m.wap.oexnr.cn/jnews/3534302.htm
- http://m.wap.oexnr.cn/jnews/4369530.htm
- http://m.wap.oexnr.cn/jnews/81173.htm
- http://m.wap.oexnr.cn/jnews/5740.htm
- http://m.wap.oexnr.cn/jnews/849167.htm
- http://m.wap.oexnr.cn/jnews/393710.htm
- http://m.wap.oexnr.cn/jnews/4425.htm
- http://m.wap.oexnr.cn/jnews/7031526.htm
- http://m.wap.oexnr.cn/jnews/0829182.htm
- http://m.wap.oexnr.cn/jnews/4678527.htm
- http://m.wap.oexnr.cn/jnews/3698.htm
- http://m.wap.oexnr.cn/jnews/5173982.htm
- http://m.wap.oexnr.cn/jnews/6640.htm
- http://m.wap.oexnr.cn/jnews/038740.htm
- http://m.wap.oexnr.cn/jnews/1397.htm
- http://m.wap.oexnr.cn/jnews/7371.htm
- http://m.wap.oexnr.cn/jnews/651985.htm
- http://m.wap.oexnr.cn/jnews/772791.htm
- http://m.wap.oexnr.cn/jnews/6442632.htm
- http://m.wap.oexnr.cn/jnews/587838.htm
- http://m.wap.oexnr.cn/jnews/4700554.htm
- http://m.wap.oexnr.cn/jnews/5308.htm
- http://m.wap.oexnr.cn/jnews/2390766.htm
- http://m.wap.oexnr.cn/jnews/1571.htm
- http://m.wap.oexnr.cn/jnews/3771838.htm
- http://m.wap.oexnr.cn/jnews/5462158.htm
- http://m.wap.oexnr.cn/jnews/67733.htm
- http://m.wap.oexnr.cn/jnews/5125481.htm
- http://m.wap.oexnr.cn/jnews/04610.htm
- http://m.wap.oexnr.cn/jnews/9535.htm
- http://m.wap.oexnr.cn/jnews/8444.htm
- http://m.wap.oexnr.cn/jnews/126939.htm
- http://m.wap.oexnr.cn/jnews/21942.htm
- http://m.wap.oexnr.cn/jnews/1937269.htm
- http://m.wap.oexnr.cn/jnews/7194591.htm
- http://m.wap.oexnr.cn/jnews/005667.htm
- http://m.wap.oexnr.cn/jnews/7280616.htm
- http://m.wap.oexnr.cn/jnews/3638087.htm
- http://m.wap.oexnr.cn/jnews/7099103.htm
- http://m.wap.oexnr.cn/jnews/236212.htm
- http://m.wap.oexnr.cn/jnews/201572.htm
- http://m.wap.oexnr.cn/jnews/3926.htm
- http://m.wap.oexnr.cn/jnews/4526933.htm
- http://m.wap.oexnr.cn/jnews/998486.htm
- http://m.wap.oexnr.cn/jnews/1998.htm
- http://m.wap.oexnr.cn/jnews/538403.htm
- http://m.wap.oexnr.cn/jnews/594744.htm
- http://m.wap.oexnr.cn/jnews/23761.htm
- http://m.wap.oexnr.cn/jnews/85195.htm
- http://m.wap.oexnr.cn/jnews/4309965.htm
- http://m.wap.oexnr.cn/jnews/429790.htm
- http://m.wap.oexnr.cn/jnews/6887216.htm
- http://m.wap.oexnr.cn/jnews/5748140.htm
- http://m.wap.oexnr.cn/jnews/47265.htm
- http://m.wap.oexnr.cn/jnews/075851.htm
- http://m.wap.oexnr.cn/jnews/31414.htm
- http://m.wap.oexnr.cn/jnews/348022.htm
- http://m.wap.oexnr.cn/jnews/5379246.htm
- http://m.wap.oexnr.cn/jnews/93794.htm
- http://m.wap.oexnr.cn/jnews/2542151.htm
- http://m.wap.oexnr.cn/jnews/668460.htm

## 项目结构

```
news-resource-aggregator/
├── build.py                 # 主构建脚本，负责读取资源列表并生成展示页面
├── config.yaml              # 项目配置文件，包含批次编号、输出路径等参数
├── requirements.txt         # Python 依赖声明文件
├── README.md                # 项目说明文档
├── LICENSE                  # MIT 许可证文件
├── src/                     # 核心源代码目录
│   ├── parser.py            # URL 解析与校验模块
│   ├── generator.py         # HTML 页面生成器
│   ├── validator.py         # 链接可达性与格式验证
│   └── utils.py             # 通用工具函数集合
├── templates/               # 展示模板目录
│   ├── default.html         # 默认新闻列表渲染模板
│   ├── compact.html         # 紧凑型列表模板
│   └── custom/              # 用户自定义模板存放目录
├── data/                    # 数据存储目录
│   ├── batches/             # 按批次存储的资源文件
│   │   └── batch_65.txt     # 第 65 批次资源列表
│   └── metadata.json        # 资源元数据索引文件
├── dist/                    # 构建输出目录
│   └── index.html           # 最终生成的新闻索引页面
├── docs/                    # 文档目录
│   ├── getting-started.md   # 入门指南
│   ├── batch-management.md  # 批次管理文档
│   ├── template-customization.md # 模板定制文档
│   └── cli-reference.md     # 命令行参考文档
├── tests/                   # 单元测试目录
│   ├── test_parser.py       # 解析模块测试
│   ├── test_validator.py    # 验证模块测试
│   └── test_generator.py    # 生成模块测试
└── scripts/                 # 辅助脚本目录
    ├── import.sh            # 批量导入辅助脚本
    └── validate.sh          # 链接校验辅助脚本
```

## 贡献指南

提交 Issue 报告问题或提出功能建议。在提交 Issue 前，请先查阅已有 Issue 列表及文档 FAQ 章节，确认该问题未被重复报告。Issue 描述需包含操作系统版本、Python 版本、完整错误日志及复现步骤。

Fork 本仓库并创建特性分支进行开发。分支命名规范为 `feature/功能简述` 或 `fix/问题简述`。开发过程中请遵循 PEP 8 代码风格规范，并为新增功能编写对应的单元测试用例。

提交 Pull Request 前确保所有单元测试通过。在本地执行 `python -m pytest tests/` 验证测试覆盖率不低于 80%。PR 描述需清晰说明改动目的、实现方案及测试结果，并关联相关的 Issue 编号。

更新文档以反映代码变更。若改动涉及用户可见的功能变化或配置项调整，需同步更新 README.md 及对应的 docs 目录下的文档文件。文档变更需与代码变更在同一 PR 中提交。

## 常见问题

问：项目启动后生成的页面中新闻链接无法正常访问，应如何排查？

答：首先确认生成页面中的 URL 格式是否与原始资源列表一致，项目不对 URL 做任何改写。其次检查目标新闻站点是否对特定 User-Agent 或来源域名做了访问限制。可在配置文件中启用链接预校验功能，项目会在构建过程中对每个链接发送 HEAD 请求以验证可达性，超时时间默认为 3 秒。

问：如何导入新批次的新闻资源并替换当前展示内容？

答：将新批次的 URL 列表按行存入 `data/batches/` 目录下的新文件中，文件命名建议包含批次编号如 `batch_66.txt`。然后修改 `config.yaml` 中的 `batch` 字段为对应编号，重新执行 `python build.py` 即可完成切换。项目保留历史批次数据，如需回溯可再次修改配置文件并重新构建。

问：项目是否支持将新闻列表输出为 JSON 或 RSS 格式以供其他系统调用？

答：支持。项目内置了输出格式扩展机制，在 `config.yaml` 中设置 `output.format` 字段为 `json` 或 `rss` 即可切换输出格式。JSON 格式输出包含每条新闻的 URL、入库时间戳及批次编号等完整元数据。RSS 格式输出遵循 RSS 2.0 规范，可被主流阅读器订阅。自定义输出格式可通过扩展 `src/generator.py` 中的渲染器类实现。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
