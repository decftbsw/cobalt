# OEXNR News Index Gateway

OEXNR News Index Gateway 是一个面向移动端资讯聚合与新闻导航的开源工具，专注于对 oexnr.cn 域名下海量新闻条目进行结构化索引、分类检索与快速预览。项目定位为技术型新闻外链汇总与导航系统，主要服务于需要批量访问、筛选和归档特定编号新闻内容的研究人员、数据分析师以及资讯运营人员。

该项目不提供新闻内容存储或改写服务，而是基于原始新闻链接构建轻量级索引层，通过本地化的元数据缓存与标签体系，帮助用户在大量新闻条目中实现精准定位与高效浏览。项目设计上强调对移动端页面（m.wap 子域）的兼容性，并内置链接可用性检测、访问时效标注与批量导出功能，适用于新闻监控、舆情跟踪与内容归档等专业场景。

## 功能概览

**批量链接导入与解析** 支持一次性导入大量 oexnr.cn 新闻链接，自动提取新闻编号与发布时间特征，建立本地索引数据库。

**分类标签与全文检索** 基于新闻编号规则与路径结构，提供多维度标签生成机制，支持关键词模糊匹配与编号范围筛选。

**移动端页面适配预览** 针对 m.wap 移动端子域名优化预览视图，在桌面端和移动设备上均可获得一致的阅读体验。

**链接健康度监控** 定时检测已收录新闻链接的可访问状态，自动标记失效链接并生成可用性报表。

**索引数据导出与同步** 支持将索引结果导出为 CSV、JSON 及 HTML 摘要格式，便于下游系统集成或离线分析。

**自定义分类规则引擎** 允许用户根据新闻编号前缀或数字区间自定义分类映射，实现个性化新闻分组与优先级排序。

**轻量级本地缓存机制** 采用 SQLite 作为本地存储后端，缓存新闻标题、摘要与访问时间戳，减少重复网络请求开销。

## 应用场景

**新闻舆情监控与分析** 数据分析师可使用本系统导入特定编号区间的新闻链接，结合自定义分类规则快速筛选出与特定话题相关的条目，生成舆情简报。

**移动端新闻归档与备份** 内容运营人员可利用链接健康度监控功能定期检查已归档新闻的可访问状态，及时发现失效链接并启动补充备份流程。

**技术研究数据采集** 研究人员可基于索引导出功能将新闻链接列表与编号元数据输出为结构化数据文件，用于后续的时间序列分析或内容趋势研究。

**资讯导航门户构建** 开发者可基于本项目的索引层与预览能力，快速搭建面向特定领域新闻的垂直导航站点，为终端用户提供清晰的浏览入口。

## 快速开始

以下命令演示了如何从 GitHub 克隆项目、安装依赖并启动本地索引服务。

```bash
# 克隆项目仓库
git clone https://github.com/oexnr/news-index-gateway.git

# 进入项目目录
cd news-index-gateway

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化本地数据库并导入示例链接
python scripts/init_db.py
python scripts/import_links.py --input samples/links.txt

# 启动本地 Web 预览服务
python app.py --host 127.0.0.1 --port 8080
```

启动后，在浏览器中访问 `http://127.0.0.1:8080` 即可进入索引导航界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，用于索引引擎与 Web 服务 |
| SQLite | 3.35 及以上 | 本地索引数据库与缓存存储 |
| Flask | 2.2.x | Web 预览界面与 API 服务框架 |
| requests | 2.28.x | 新闻链接可用性检测与页面抓取 |
| beautifulsoup4 | 4.11.x | 移动端页面标题与摘要解析 |
| lxml | 4.9.x | HTML 解析加速依赖，提升页面解析性能 |
| pytest | 7.2.x | 单元测试与集成测试框架（开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 入门指南 | docs/quickstart.md | 如何快速安装并运行索引服务？如何导入第一批新闻链接？ |
| 配置说明 | docs/configuration.md | 如何自定义分类规则？如何调整缓存策略与检测频率？ |
| API 参考 | docs/api_reference.md | 索引引擎提供了哪些编程接口？如何通过 API 批量查询链接状态？ |
| 运维手册 | docs/operations.md | 如何备份索引数据库？如何迁移索引数据到新环境？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/303393.htm
- http://m.wap.oexnr.cn/jnews/25178.htm
- http://m.wap.oexnr.cn/jnews/3980147.htm
- http://m.wap.oexnr.cn/jnews/769162.htm
- http://m.wap.oexnr.cn/jnews/807549.htm
- http://m.wap.oexnr.cn/jnews/92062.htm
- http://m.wap.oexnr.cn/jnews/1165182.htm
- http://m.wap.oexnr.cn/jnews/54096.htm
- http://m.wap.oexnr.cn/jnews/30854.htm
- http://m.wap.oexnr.cn/jnews/05005.htm
- http://m.wap.oexnr.cn/jnews/39383.htm
- http://m.wap.oexnr.cn/jnews/311059.htm
- http://m.wap.oexnr.cn/jnews/1944198.htm
- http://m.wap.oexnr.cn/jnews/4029.htm
- http://m.wap.oexnr.cn/jnews/7483.htm
- http://m.wap.oexnr.cn/jnews/49176.htm
- http://m.wap.oexnr.cn/jnews/030718.htm
- http://m.wap.oexnr.cn/jnews/04859.htm
- http://m.wap.oexnr.cn/jnews/00871.htm
- http://m.wap.oexnr.cn/jnews/3172851.htm
- http://m.wap.oexnr.cn/jnews/9546220.htm
- http://m.wap.oexnr.cn/jnews/7274.htm
- http://m.wap.oexnr.cn/jnews/9622.htm
- http://m.wap.oexnr.cn/jnews/22690.htm
- http://m.wap.oexnr.cn/jnews/16801.htm
- http://m.wap.oexnr.cn/jnews/7737737.htm
- http://m.wap.oexnr.cn/jnews/3265933.htm
- http://m.wap.oexnr.cn/jnews/680623.htm
- http://m.wap.oexnr.cn/jnews/28891.htm
- http://m.wap.oexnr.cn/jnews/93252.htm
- http://m.wap.oexnr.cn/jnews/2143591.htm
- http://m.wap.oexnr.cn/jnews/8776078.htm
- http://m.wap.oexnr.cn/jnews/18913.htm
- http://m.wap.oexnr.cn/jnews/2625112.htm
- http://m.wap.oexnr.cn/jnews/5103.htm
- http://m.wap.oexnr.cn/jnews/7785481.htm
- http://m.wap.oexnr.cn/jnews/9136.htm
- http://m.wap.oexnr.cn/jnews/341636.htm
- http://m.wap.oexnr.cn/jnews/19638.htm
- http://m.wap.oexnr.cn/jnews/5280.htm
- http://m.wap.oexnr.cn/jnews/54119.htm
- http://m.wap.oexnr.cn/jnews/9403.htm
- http://m.wap.oexnr.cn/jnews/3475203.htm
- http://m.wap.oexnr.cn/jnews/6733.htm
- http://m.wap.oexnr.cn/jnews/7078.htm
- http://m.wap.oexnr.cn/jnews/6537.htm
- http://m.wap.oexnr.cn/jnews/5110.htm
- http://m.wap.oexnr.cn/jnews/10711.htm
- http://m.wap.oexnr.cn/jnews/82776.htm
- http://m.wap.oexnr.cn/jnews/3007.htm
- http://m.wap.oexnr.cn/jnews/4872.htm
- http://m.wap.oexnr.cn/jnews/9945003.htm
- http://m.wap.oexnr.cn/jnews/2388507.htm
- http://m.wap.oexnr.cn/jnews/4120825.htm
- http://m.wap.oexnr.cn/jnews/8152.htm
- http://m.wap.oexnr.cn/jnews/9412814.htm
- http://m.wap.oexnr.cn/jnews/364125.htm
- http://m.wap.oexnr.cn/jnews/007707.htm
- http://m.wap.oexnr.cn/jnews/307242.htm
- http://m.wap.oexnr.cn/jnews/3624346.htm
- http://m.wap.oexnr.cn/jnews/8815.htm
- http://m.wap.oexnr.cn/jnews/135369.htm
- http://m.wap.oexnr.cn/jnews/650170.htm
- http://m.wap.oexnr.cn/jnews/1423.htm
- http://m.wap.oexnr.cn/jnews/0617003.htm
- http://m.wap.oexnr.cn/jnews/3065.htm
- http://m.wap.oexnr.cn/jnews/665836.htm
- http://m.wap.oexnr.cn/jnews/13792.htm
- http://m.wap.oexnr.cn/jnews/302740.htm
- http://m.wap.oexnr.cn/jnews/088825.htm
- http://m.wap.oexnr.cn/jnews/2953.htm
- http://m.wap.oexnr.cn/jnews/753228.htm
- http://m.wap.oexnr.cn/jnews/7508584.htm
- http://m.wap.oexnr.cn/jnews/890974.htm
- http://m.wap.oexnr.cn/jnews/0163.htm
- http://m.wap.oexnr.cn/jnews/5797565.htm
- http://m.wap.oexnr.cn/jnews/2908483.htm
- http://m.wap.oexnr.cn/jnews/8007185.htm
- http://m.wap.oexnr.cn/jnews/2454966.htm
- http://m.wap.oexnr.cn/jnews/4295900.htm
- http://m.wap.oexnr.cn/jnews/8549245.htm
- http://m.wap.oexnr.cn/jnews/8837.htm
- http://m.wap.oexnr.cn/jnews/81702.htm
- http://m.wap.oexnr.cn/jnews/300302.htm
- http://m.wap.oexnr.cn/jnews/32787.htm
- http://m.wap.oexnr.cn/jnews/5982507.htm
- http://m.wap.oexnr.cn/jnews/089781.htm
- http://m.wap.oexnr.cn/jnews/6476.htm
- http://m.wap.oexnr.cn/jnews/6137896.htm
- http://m.wap.oexnr.cn/jnews/030688.htm
- http://m.wap.oexnr.cn/jnews/3721643.htm
- http://m.wap.oexnr.cn/jnews/49134.htm
- http://m.wap.oexnr.cn/jnews/5861621.htm
- http://m.wap.oexnr.cn/jnews/910001.htm
- http://m.wap.oexnr.cn/jnews/52336.htm
- http://m.wap.oexnr.cn/jnews/5966.htm
- http://m.wap.oexnr.cn/jnews/5387.htm
- http://m.wap.oexnr.cn/jnews/1916.htm
- http://m.wap.oexnr.cn/jnews/3270.htm
- http://m.wap.oexnr.cn/jnews/45433.htm
- http://m.wap.oexnr.cn/jnews/3934.htm
- http://m.wap.oexnr.cn/jnews/7417.htm
- http://m.wap.oexnr.cn/jnews/9907.htm
- http://m.wap.oexnr.cn/jnews/0824.htm
- http://m.wap.oexnr.cn/jnews/35242.htm
- http://m.wap.oexnr.cn/jnews/50192.htm
- http://m.wap.oexnr.cn/jnews/0815244.htm
- http://m.wap.oexnr.cn/jnews/1066038.htm
- http://m.wap.oexnr.cn/jnews/8050.htm
- http://m.wap.oexnr.cn/jnews/436137.htm
- http://m.wap.oexnr.cn/jnews/7990837.htm
- http://m.wap.oexnr.cn/jnews/6213.htm
- http://m.wap.oexnr.cn/jnews/74007.htm
- http://m.wap.oexnr.cn/jnews/0029111.htm
- http://m.wap.oexnr.cn/jnews/1865838.htm
- http://m.wap.oexnr.cn/jnews/7328.htm
- http://m.wap.oexnr.cn/jnews/7259681.htm
- http://m.wap.oexnr.cn/jnews/4959114.htm
- http://m.wap.oexnr.cn/jnews/5228839.htm
- http://m.wap.oexnr.cn/jnews/7811.htm
- http://m.wap.oexnr.cn/jnews/026606.htm
- http://m.wap.oexnr.cn/jnews/8419931.htm
- http://m.wap.oexnr.cn/jnews/04700.htm
- http://m.wap.oexnr.cn/jnews/4856.htm
- http://m.wap.oexnr.cn/jnews/2471.htm
- http://m.wap.oexnr.cn/jnews/1593546.htm
- http://m.wap.oexnr.cn/jnews/2688.htm
- http://m.wap.oexnr.cn/jnews/2036.htm
- http://m.wap.oexnr.cn/jnews/74200.htm
- http://m.wap.oexnr.cn/jnews/84255.htm
- http://m.wap.oexnr.cn/jnews/71946.htm
- http://m.wap.oexnr.cn/jnews/03384.htm
- http://m.wap.oexnr.cn/jnews/974125.htm
- http://m.wap.oexnr.cn/jnews/711844.htm
- http://m.wap.oexnr.cn/jnews/95801.htm
- http://m.wap.oexnr.cn/jnews/6572651.htm
- http://m.wap.oexnr.cn/jnews/520393.htm
- http://m.wap.oexnr.cn/jnews/20087.htm
- http://m.wap.oexnr.cn/jnews/84612.htm
- http://m.wap.oexnr.cn/jnews/72528.htm
- http://m.wap.oexnr.cn/jnews/9249071.htm
- http://m.wap.oexnr.cn/jnews/2079.htm
- http://m.wap.oexnr.cn/jnews/69513.htm
- http://m.wap.oexnr.cn/jnews/4642531.htm
- http://m.wap.oexnr.cn/jnews/1821.htm
- http://m.wap.oexnr.cn/jnews/6880.htm
- http://m.wap.oexnr.cn/jnews/82071.htm
- http://m.wap.oexnr.cn/jnews/7074550.htm
- http://m.wap.oexnr.cn/jnews/70644.htm
- http://m.wap.oexnr.cn/jnews/9444.htm
- http://m.wap.oexnr.cn/jnews/8383806.htm
- http://m.wap.oexnr.cn/jnews/0564.htm
- http://m.wap.oexnr.cn/jnews/094638.htm
- http://m.wap.oexnr.cn/jnews/5918.htm
- http://m.wap.oexnr.cn/jnews/970560.htm
- http://m.wap.oexnr.cn/jnews/3009990.htm
- http://m.wap.oexnr.cn/jnews/442920.htm
- http://m.wap.oexnr.cn/jnews/3473833.htm
- http://m.wap.oexnr.cn/jnews/28434.htm
- http://m.wap.oexnr.cn/jnews/021532.htm
- http://m.wap.oexnr.cn/jnews/15320.htm
- http://m.wap.oexnr.cn/jnews/10266.htm
- http://m.wap.oexnr.cn/jnews/382778.htm
- http://m.wap.oexnr.cn/jnews/7050811.htm
- http://m.wap.oexnr.cn/jnews/5158729.htm
- http://m.wap.oexnr.cn/jnews/353873.htm
- http://m.wap.oexnr.cn/jnews/095161.htm
- http://m.wap.oexnr.cn/jnews/892800.htm
- http://m.wap.oexnr.cn/jnews/9224.htm
- http://m.wap.oexnr.cn/jnews/78889.htm
- http://m.wap.oexnr.cn/jnews/10395.htm
- http://m.wap.oexnr.cn/jnews/09607.htm
- http://m.wap.oexnr.cn/jnews/4883593.htm
- http://m.wap.oexnr.cn/jnews/8869026.htm
- http://m.wap.oexnr.cn/jnews/04136.htm
- http://m.wap.oexnr.cn/jnews/42753.htm
- http://m.wap.oexnr.cn/jnews/15344.htm
- http://m.wap.oexnr.cn/jnews/9723.htm
- http://m.wap.oexnr.cn/jnews/547089.htm
- http://m.wap.oexnr.cn/jnews/43498.htm
- http://m.wap.oexnr.cn/jnews/443311.htm
- http://m.wap.oexnr.cn/jnews/221547.htm
- http://m.wap.oexnr.cn/jnews/0521925.htm
- http://m.wap.oexnr.cn/jnews/9659988.htm
- http://m.wap.oexnr.cn/jnews/603512.htm
- http://m.wap.oexnr.cn/jnews/048334.htm
- http://m.wap.oexnr.cn/jnews/6943.htm
- http://m.wap.oexnr.cn/jnews/95214.htm
- http://m.wap.oexnr.cn/jnews/3746.htm
- http://m.wap.oexnr.cn/jnews/546904.htm
- http://m.wap.oexnr.cn/jnews/312828.htm
- http://m.wap.oexnr.cn/jnews/71281.htm
- http://m.wap.oexnr.cn/jnews/9573.htm
- http://m.wap.oexnr.cn/jnews/9937.htm
- http://m.wap.oexnr.cn/jnews/373787.htm
- http://m.wap.oexnr.cn/jnews/9402082.htm
- http://m.wap.oexnr.cn/jnews/4759220.htm
- http://m.wap.oexnr.cn/jnews/4554304.htm
- http://m.wap.oexnr.cn/jnews/8313.htm
- http://m.wap.oexnr.cn/jnews/1365.htm
- http://m.wap.oexnr.cn/jnews/0190116.htm
- http://m.wap.oexnr.cn/jnews/5831.htm
- http://m.wap.oexnr.cn/jnews/376621.htm
- http://m.wap.oexnr.cn/jnews/8293062.htm
- http://m.wap.oexnr.cn/jnews/9071263.htm
- http://m.wap.oexnr.cn/jnews/334376.htm
- http://m.wap.oexnr.cn/jnews/6642.htm
- http://m.wap.oexnr.cn/jnews/84453.htm
- http://m.wap.oexnr.cn/jnews/56107.htm
- http://m.wap.oexnr.cn/jnews/914272.htm
- http://m.wap.oexnr.cn/jnews/41168.htm
- http://m.wap.oexnr.cn/jnews/052637.htm
- http://m.wap.oexnr.cn/jnews/6174123.htm
- http://m.wap.oexnr.cn/jnews/4077.htm
- http://m.wap.oexnr.cn/jnews/344512.htm
- http://m.wap.oexnr.cn/jnews/35620.htm
- http://m.wap.oexnr.cn/jnews/36566.htm
- http://m.wap.oexnr.cn/jnews/8685.htm
- http://m.wap.oexnr.cn/jnews/5224.htm
- http://m.wap.oexnr.cn/jnews/51491.htm
- http://m.wap.oexnr.cn/jnews/005124.htm
- http://m.wap.oexnr.cn/jnews/202770.htm
- http://m.wap.oexnr.cn/jnews/9850.htm
- http://m.wap.oexnr.cn/jnews/251619.htm
- http://m.wap.oexnr.cn/jnews/29106.htm
- http://m.wap.oexnr.cn/jnews/61211.htm
- http://m.wap.oexnr.cn/jnews/48862.htm
- http://m.wap.oexnr.cn/jnews/59522.htm
- http://m.wap.oexnr.cn/jnews/6962315.htm
- http://m.wap.oexnr.cn/jnews/524827.htm
- http://m.wap.oexnr.cn/jnews/564004.htm
- http://m.wap.oexnr.cn/jnews/1138686.htm
- http://m.wap.oexnr.cn/jnews/3251472.htm
- http://m.wap.oexnr.cn/jnews/651741.htm
- http://m.wap.oexnr.cn/jnews/2224.htm
- http://m.wap.oexnr.cn/jnews/03502.htm
- http://m.wap.oexnr.cn/jnews/659335.htm
- http://m.wap.oexnr.cn/jnews/4830.htm
- http://m.wap.oexnr.cn/jnews/0774705.htm
- http://m.wap.oexnr.cn/jnews/1286.htm
- http://m.wap.oexnr.cn/jnews/0642.htm
- http://m.wap.oexnr.cn/jnews/227127.htm
- http://m.wap.oexnr.cn/jnews/3419.htm
- http://m.wap.oexnr.cn/jnews/561112.htm
- http://m.wap.oexnr.cn/jnews/8674.htm
- http://m.wap.oexnr.cn/jnews/021146.htm
- http://m.wap.oexnr.cn/jnews/8305372.htm
- http://m.wap.oexnr.cn/jnews/552861.htm
- http://m.wap.oexnr.cn/jnews/4299.htm
- http://m.wap.oexnr.cn/jnews/2490.htm
- http://m.wap.oexnr.cn/jnews/03590.htm
- http://m.wap.oexnr.cn/jnews/894871.htm
- http://m.wap.oexnr.cn/jnews/3000.htm
- http://m.wap.oexnr.cn/jnews/360561.htm
- http://m.wap.oexnr.cn/jnews/150757.htm
- http://m.wap.oexnr.cn/jnews/2263178.htm
- http://m.wap.oexnr.cn/jnews/5577.htm
- http://m.wap.oexnr.cn/jnews/2622583.htm
- http://m.wap.oexnr.cn/jnews/6056830.htm
- http://m.wap.oexnr.cn/jnews/013144.htm
- http://m.wap.oexnr.cn/jnews/02624.htm
- http://m.wap.oexnr.cn/jnews/009903.htm
- http://m.wap.oexnr.cn/jnews/51055.htm
- http://m.wap.oexnr.cn/jnews/3427229.htm
- http://m.wap.oexnr.cn/jnews/339607.htm
- http://m.wap.oexnr.cn/jnews/3430.htm
- http://m.wap.oexnr.cn/jnews/7332003.htm
- http://m.wap.oexnr.cn/jnews/3974.htm
- http://m.wap.oexnr.cn/jnews/4017532.htm
- http://m.wap.oexnr.cn/jnews/4249.htm
- http://m.wap.oexnr.cn/jnews/16647.htm
- http://m.wap.oexnr.cn/jnews/48435.htm
- http://m.wap.oexnr.cn/jnews/0485383.htm
- http://m.wap.oexnr.cn/jnews/84638.htm
- http://m.wap.oexnr.cn/jnews/0101943.htm
- http://m.wap.oexnr.cn/jnews/7381598.htm
- http://m.wap.oexnr.cn/jnews/10997.htm
- http://m.wap.oexnr.cn/jnews/99052.htm
- http://m.wap.oexnr.cn/jnews/8042436.htm
- http://m.wap.oexnr.cn/jnews/866290.htm
- http://m.wap.oexnr.cn/jnews/01296.htm
- http://m.wap.oexnr.cn/jnews/76807.htm
- http://m.wap.oexnr.cn/jnews/893668.htm
- http://m.wap.oexnr.cn/jnews/2888438.htm
- http://m.wap.oexnr.cn/jnews/4750.htm
- http://m.wap.oexnr.cn/jnews/1218.htm
- http://m.wap.oexnr.cn/jnews/94296.htm
- http://m.wap.oexnr.cn/jnews/262281.htm
- http://m.wap.oexnr.cn/jnews/5774108.htm
- http://m.wap.oexnr.cn/jnews/1046.htm
- http://m.wap.oexnr.cn/jnews/8953874.htm
- http://m.wap.oexnr.cn/jnews/3440317.htm
- http://m.wap.oexnr.cn/jnews/0625.htm
- http://m.wap.oexnr.cn/jnews/67429.htm
- http://m.wap.oexnr.cn/jnews/0249309.htm
- http://m.wap.oexnr.cn/jnews/587744.htm
- http://m.wap.oexnr.cn/jnews/32495.htm
- http://m.wap.oexnr.cn/jnews/9853906.htm
- http://m.wap.oexnr.cn/jnews/844773.htm
- http://m.wap.oexnr.cn/jnews/963988.htm

## 项目结构

```
news-index-gateway/
├── app.py                         # Web 服务主入口，启动 Flask 应用与路由注册
├── requirements.txt               # Python 依赖声明文件，包含 Flask、requests 等核心库
├── config/
│   ├── default.yaml               # 默认配置参数，包含缓存路径、检测间隔与端口设置
│   └── custom.yaml.example        # 用户自定义配置模板，用于覆盖分类规则与日志级别
├── core/
│   ├── indexer.py                 # 新闻链接索引引擎，负责解析编号、生成标签与写入数据库
│   ├── crawler.py                 # 页面抓取模块，封装 requests 与 BeautifulSoup 获取移动端页面信息
│   ├── checker.py                 # 链接健康度检测器，支持异步并发与超时重试机制
│   └── exporter.py                # 数据导出模块，支持 CSV、JSON 与 HTML 摘要格式输出
├── storage/
│   ├── database.py                # SQLite 数据库连接与 ORM 映射，管理索引表与缓存表
│   ├── migrations/                # 数据库版本迁移脚本，使用 Alembic 进行增量变更管理
│   └── cache/                     # 本地缓存文件目录，存储临时页面快照与解析结果
├── web/
│   ├── templates/                 # Jinja2 模板目录，包含首页、列表页与详情页视图
│   ├── static/                    # 静态资源目录，包含 CSS 样式、JavaScript 脚本与图标文件
│   └── routes.py                  # 路由处理器，定义 URL 映射与请求响应逻辑
├── scripts/
│   ├── init_db.py                 # 初始化数据库脚本，创建表结构与基础索引
│   ├── import_links.py            # 批量导入链接脚本，支持从文本文件读取 URL 列表
│   └── scheduled_check.py         # 定时检测脚本，可配置 cron 任务定期刷新链接状态
├── tests/
│   ├── unit/                      # 单元测试目录，覆盖索引器、检查器与导出器核心逻辑
│   ├── integration/               # 集成测试目录，验证数据库操作与 Web 接口联动正确性
│   └── fixtures/                  # 测试数据固件，包含示例链接与模拟页面响应体
├── docs/                          # 文档目录，包含快速入门、配置说明与 API 参考手册
└── LICENSE                        # MIT 许可证文件
```

## 贡献指南

**提交问题报告** 在 GitHub Issues 中提交详细的 bug 描述，包含运行环境、Python 版本、错误日志及可复现的输入链接列表。建议使用项目提供的 issue 模板。

**实现新功能或修复补丁** Fork 项目仓库，在 dev 分支基础上创建功能分支，遵循 PEP 8 编码规范，并为新增代码编写单元测试。确保所有现有测试通过后提交 Pull Request。

**完善文档与示例** 改进 README、配置说明或 API 文档中的表述不清之处，补充典型使用场景的代码示例。文档贡献者需确保中英文术语统一，技术描述准确无歧义。

**参与社区讨论与评审** 积极参与 Pull Request 的代码评审，对他人提交的变更提供建设性反馈。在 Discussions 版块分享使用经验、分类规则配置技巧或性能优化建议。

## 常见问题

**导入大量链接时出现超时或连接重置错误如何解决？**

这通常是因为目标新闻服务器对频繁请求做出了限流响应。建议在 import_links.py 中使用 --delay 参数设置请求间隔（单位毫秒），默认值为 500 毫秒。对于超过 1000 条链接的批量导入，推荐将 --batch-size 设为 50 并使用 --retry 参数启用失败重试机制。若仍存在大量超时，可考虑在配置文件中调整 user-agent 与请求头模拟移动端浏览器行为。

**索引数据库能否迁移至 PostgreSQL 或 MySQL 等生产级数据库？**

当前版本原生支持 SQLite，但 storage/database.py 中使用了 SQLAlchemy ORM，理论上可切换至其他关系型数据库。如需迁移至 PostgreSQL，请修改 config/default.yaml 中的 database_url 连接字符串，并在 requirements.txt 中添加 psycopg2-binary 依赖。需注意不同数据库对全文检索语法的差异，迁移后可能需要调整查询构造逻辑。

**如何定期自动检测已收录链接的可用性？**

项目提供了 scripts/scheduled_check.py 脚本，支持命令行参数配置检测并发数与超时阈值。推荐在 Linux 服务器上通过 crontab 设置定时任务，例如每日凌晨 2:00 执行全量检测。检测结果会写入数据库的 link_status 表，可通过 Web 界面的 /status 端点查看汇总报表。对于频繁失效的域名，可在配置中设置黑名单自动过滤。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
