# Oexnr News Resource Aggregator

Oexnr News Resource Aggregator 是一个面向移动端新闻资讯聚合的开源项目，专注于从 oexnr.cn 域名体系下采集、整理和索引 jnews 路径中的热点报道与深度内容。项目定位为技术研究者和新闻数据分析人员提供结构化的新闻资源索引库，通过标准化的 URL 采集流程和元数据提取方案，将散落的新闻页面转化为可批量处理的数据资产。

本项目并非一个完整的新闻门户或内容管理系统，而是一套轻量级的资源导航与采集框架，适用于需要定期抓取特定域名下新闻列表、分析报道趋势或构建自定义新闻订阅管道的开发场景。项目提供明确的 URL 清单、采集脚本示例和目录组织规范，帮助用户快速理解 oexnr.cn 移动站点的资源分布规律，并基于此扩展自身的数据采集应用。

## 功能概览

**批量 URL 索引管理** 提供超过 300 条 jnews 路径的完整 URL 清单，所有链接按原始格式收录，支持一键导出用于采集任务配置。

**移动端新闻资源分类** 依据 URL 路径中的数字 ID 规律，对新闻资源进行初步的时间段和主题分类，便于用户按需筛选。

**轻量级采集脚手架** 内置 Python 和 Shell 两种采集脚本模板，用户可基于模板快速定制自己的新闻抓取逻辑。

**数据去重与校验机制** 提供 URL 格式校验和重复条目过滤功能，确保索引库的整洁性和可用性。

**多格式输出支持** 支持将资源列表导出为纯文本、JSON 或 CSV 格式，满足不同数据处理工具的使用习惯。

**文档化目录结构** 项目文件和目录均附带注释说明，降低新用户的认知负担，提升二次开发效率。

## 应用场景

**新闻趋势分析与统计** 研究人员可通过遍历 URL 清单，采集对应页面的发布时间、标题和正文内容，进而分析 oexnr.cn 平台在不同时间段的报道热点和发文频率。

**自定义新闻订阅源构建** 开发者可将本项目提供的 URL 清单作为种子列表，结合 RSS 生成工具或 Webhook 服务，构建私人的移动端新闻订阅推送系统。

**数据采集教学与实验** 本项目可作为爬虫教学中的目标站点案例，学员通过处理真实的 URL 结构和页面响应，练习请求发送、内容解析和数据持久化等基础技能。

**站点可用性监控** 运维人员可定期对清单中的 URL 进行连通性检测，监控 oexnr.cn 移动端服务的稳定性和响应速度，及时发现异常状态。

## 快速开始

```bash
# 克隆项目仓库到本地
git clone https://github.com/your-org/oexnr-news-aggregator.git

# 进入项目根目录
cd oexnr-news-aggregator

# 安装依赖（Python 环境）
pip install -r requirements.txt

# 运行采集示例脚本，检查 URL 可达性
python scripts/check_urls.py --input data/urls.txt --output reports/status.json

# 执行完整资源索引构建
make build-index
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 核心采集脚本和工具链的运行环境 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装第三方库 |
| requests | 2.25.0 及以上 | 发送 HTTP 请求，获取新闻页面内容 |
| lxml | 4.6.0 及以上 | 解析 HTML 文档，提取页面元数据 |
| pandas | 1.2.0 及以上 | 用于数据清洗和表格化输出（可选） |
| Git | 2.20.0 及以上 | 克隆仓库和管理版本更新 |
| Make | 3.8 及以上 | 执行自动化构建任务（可选） |
| curl | 7.68.0 及以上 | 用于 Shell 脚本中的快速请求测试 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何使用项目提供的 URL 清单和采集脚本？如何配置采集参数？ |
| 开发者指南 | docs/developer-guide.md | 如何扩展新的采集模块？URL 索引更新的流程是什么？ |
| 数据结构 | docs/data-schema.md | 采集到的新闻数据以什么格式存储？各个字段的含义是什么？ |
| 部署运维 | docs/deployment.md | 如何将采集任务部署到服务器？定时任务如何配置？ |
| 常见问题 | docs/faq.md | 遇到请求失败、编码问题或数据缺失时如何处理？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/4837.htm
- http://m.wap.oexnr.cn/jnews/3740776.htm
- http://m.wap.oexnr.cn/jnews/5911097.htm
- http://m.wap.oexnr.cn/jnews/2911392.htm
- http://m.wap.oexnr.cn/jnews/919713.htm
- http://m.wap.oexnr.cn/jnews/74611.htm
- http://m.wap.oexnr.cn/jnews/20487.htm
- http://m.wap.oexnr.cn/jnews/70461.htm
- http://m.wap.oexnr.cn/jnews/5474674.htm
- http://m.wap.oexnr.cn/jnews/6986326.htm
- http://m.wap.oexnr.cn/jnews/8242295.htm
- http://m.wap.oexnr.cn/jnews/068737.htm
- http://m.wap.oexnr.cn/jnews/332210.htm
- http://m.wap.oexnr.cn/jnews/8711.htm
- http://m.wap.oexnr.cn/jnews/12894.htm
- http://m.wap.oexnr.cn/jnews/4835.htm
- http://m.wap.oexnr.cn/jnews/7419.htm
- http://m.wap.oexnr.cn/jnews/2870.htm
- http://m.wap.oexnr.cn/jnews/15979.htm
- http://m.wap.oexnr.cn/jnews/2841224.htm
- http://m.wap.oexnr.cn/jnews/9669.htm
- http://m.wap.oexnr.cn/jnews/60659.htm
- http://m.wap.oexnr.cn/jnews/3085427.htm
- http://m.wap.oexnr.cn/jnews/206946.htm
- http://m.wap.oexnr.cn/jnews/25912.htm
- http://m.wap.oexnr.cn/jnews/8901627.htm
- http://m.wap.oexnr.cn/jnews/69098.htm
- http://m.wap.oexnr.cn/jnews/439652.htm
- http://m.wap.oexnr.cn/jnews/49387.htm
- http://m.wap.oexnr.cn/jnews/098396.htm
- http://m.wap.oexnr.cn/jnews/9967907.htm
- http://m.wap.oexnr.cn/jnews/6364.htm
- http://m.wap.oexnr.cn/jnews/60185.htm
- http://m.wap.oexnr.cn/jnews/881126.htm
- http://m.wap.oexnr.cn/jnews/10033.htm
- http://m.wap.oexnr.cn/jnews/5949.htm
- http://m.wap.oexnr.cn/jnews/80466.htm
- http://m.wap.oexnr.cn/jnews/249380.htm
- http://m.wap.oexnr.cn/jnews/3894887.htm
- http://m.wap.oexnr.cn/jnews/365215.htm
- http://m.wap.oexnr.cn/jnews/56394.htm
- http://m.wap.oexnr.cn/jnews/6604.htm
- http://m.wap.oexnr.cn/jnews/74021.htm
- http://m.wap.oexnr.cn/jnews/4300658.htm
- http://m.wap.oexnr.cn/jnews/305962.htm
- http://m.wap.oexnr.cn/jnews/7945971.htm
- http://m.wap.oexnr.cn/jnews/1835.htm
- http://m.wap.oexnr.cn/jnews/7868026.htm
- http://m.wap.oexnr.cn/jnews/783077.htm
- http://m.wap.oexnr.cn/jnews/5398517.htm
- http://m.wap.oexnr.cn/jnews/029849.htm
- http://m.wap.oexnr.cn/jnews/617458.htm
- http://m.wap.oexnr.cn/jnews/21891.htm
- http://m.wap.oexnr.cn/jnews/3089.htm
- http://m.wap.oexnr.cn/jnews/89584.htm
- http://m.wap.oexnr.cn/jnews/4405755.htm
- http://m.wap.oexnr.cn/jnews/8182757.htm
- http://m.wap.oexnr.cn/jnews/755510.htm
- http://m.wap.oexnr.cn/jnews/55034.htm
- http://m.wap.oexnr.cn/jnews/233829.htm
- http://m.wap.oexnr.cn/jnews/3990343.htm
- http://m.wap.oexnr.cn/jnews/1015.htm
- http://m.wap.oexnr.cn/jnews/5578.htm
- http://m.wap.oexnr.cn/jnews/833329.htm
- http://m.wap.oexnr.cn/jnews/4477609.htm
- http://m.wap.oexnr.cn/jnews/798951.htm
- http://m.wap.oexnr.cn/jnews/75256.htm
- http://m.wap.oexnr.cn/jnews/313300.htm
- http://m.wap.oexnr.cn/jnews/099248.htm
- http://m.wap.oexnr.cn/jnews/2505.htm
- http://m.wap.oexnr.cn/jnews/5780521.htm
- http://m.wap.oexnr.cn/jnews/7320257.htm
- http://m.wap.oexnr.cn/jnews/1554.htm
- http://m.wap.oexnr.cn/jnews/446581.htm
- http://m.wap.oexnr.cn/jnews/3884.htm
- http://m.wap.oexnr.cn/jnews/66185.htm
- http://m.wap.oexnr.cn/jnews/1750244.htm
- http://m.wap.oexnr.cn/jnews/5961.htm
- http://m.wap.oexnr.cn/jnews/72035.htm
- http://m.wap.oexnr.cn/jnews/10003.htm
- http://m.wap.oexnr.cn/jnews/491378.htm
- http://m.wap.oexnr.cn/jnews/6118038.htm
- http://m.wap.oexnr.cn/jnews/15416.htm
- http://m.wap.oexnr.cn/jnews/30135.htm
- http://m.wap.oexnr.cn/jnews/47594.htm
- http://m.wap.oexnr.cn/jnews/0231904.htm
- http://m.wap.oexnr.cn/jnews/283444.htm
- http://m.wap.oexnr.cn/jnews/2699.htm
- http://m.wap.oexnr.cn/jnews/643668.htm
- http://m.wap.oexnr.cn/jnews/722845.htm
- http://m.wap.oexnr.cn/jnews/915935.htm
- http://m.wap.oexnr.cn/jnews/337892.htm
- http://m.wap.oexnr.cn/jnews/2434052.htm
- http://m.wap.oexnr.cn/jnews/98311.htm
- http://m.wap.oexnr.cn/jnews/346973.htm
- http://m.wap.oexnr.cn/jnews/675452.htm
- http://m.wap.oexnr.cn/jnews/2789.htm
- http://m.wap.oexnr.cn/jnews/8668.htm
- http://m.wap.oexnr.cn/jnews/643534.htm
- http://m.wap.oexnr.cn/jnews/51831.htm
- http://m.wap.oexnr.cn/jnews/922362.htm
- http://m.wap.oexnr.cn/jnews/367012.htm
- http://m.wap.oexnr.cn/jnews/65505.htm
- http://m.wap.oexnr.cn/jnews/9134091.htm
- http://m.wap.oexnr.cn/jnews/113012.htm
- http://m.wap.oexnr.cn/jnews/436593.htm
- http://m.wap.oexnr.cn/jnews/05105.htm
- http://m.wap.oexnr.cn/jnews/13942.htm
- http://m.wap.oexnr.cn/jnews/82912.htm
- http://m.wap.oexnr.cn/jnews/5001648.htm
- http://m.wap.oexnr.cn/jnews/1133.htm
- http://m.wap.oexnr.cn/jnews/98095.htm
- http://m.wap.oexnr.cn/jnews/86759.htm
- http://m.wap.oexnr.cn/jnews/7858.htm
- http://m.wap.oexnr.cn/jnews/608247.htm
- http://m.wap.oexnr.cn/jnews/2996.htm
- http://m.wap.oexnr.cn/jnews/3485.htm
- http://m.wap.oexnr.cn/jnews/9412797.htm
- http://m.wap.oexnr.cn/jnews/8904854.htm
- http://m.wap.oexnr.cn/jnews/42237.htm
- http://m.wap.oexnr.cn/jnews/049504.htm
- http://m.wap.oexnr.cn/jnews/777749.htm
- http://m.wap.oexnr.cn/jnews/7491795.htm
- http://m.wap.oexnr.cn/jnews/3860190.htm
- http://m.wap.oexnr.cn/jnews/381884.htm
- http://m.wap.oexnr.cn/jnews/2116882.htm
- http://m.wap.oexnr.cn/jnews/9123.htm
- http://m.wap.oexnr.cn/jnews/20073.htm
- http://m.wap.oexnr.cn/jnews/6889.htm
- http://m.wap.oexnr.cn/jnews/9038.htm
- http://m.wap.oexnr.cn/jnews/6035.htm
- http://m.wap.oexnr.cn/jnews/945583.htm
- http://m.wap.oexnr.cn/jnews/891729.htm
- http://m.wap.oexnr.cn/jnews/518121.htm
- http://m.wap.oexnr.cn/jnews/255652.htm
- http://m.wap.oexnr.cn/jnews/8891172.htm
- http://m.wap.oexnr.cn/jnews/7386087.htm
- http://m.wap.oexnr.cn/jnews/9207.htm
- http://m.wap.oexnr.cn/jnews/3801598.htm
- http://m.wap.oexnr.cn/jnews/461024.htm
- http://m.wap.oexnr.cn/jnews/57478.htm
- http://m.wap.oexnr.cn/jnews/4977.htm
- http://m.wap.oexnr.cn/jnews/31494.htm
- http://m.wap.oexnr.cn/jnews/797578.htm
- http://m.wap.oexnr.cn/jnews/7784.htm
- http://m.wap.oexnr.cn/jnews/61470.htm
- http://m.wap.oexnr.cn/jnews/68609.htm
- http://m.wap.oexnr.cn/jnews/09961.htm
- http://m.wap.oexnr.cn/jnews/33129.htm
- http://m.wap.oexnr.cn/jnews/53007.htm
- http://m.wap.oexnr.cn/jnews/972657.htm
- http://m.wap.oexnr.cn/jnews/152317.htm
- http://m.wap.oexnr.cn/jnews/01605.htm
- http://m.wap.oexnr.cn/jnews/3034.htm
- http://m.wap.oexnr.cn/jnews/6124.htm
- http://m.wap.oexnr.cn/jnews/243944.htm
- http://m.wap.oexnr.cn/jnews/4342.htm
- http://m.wap.oexnr.cn/jnews/4773.htm
- http://m.wap.oexnr.cn/jnews/74870.htm
- http://m.wap.oexnr.cn/jnews/3032.htm
- http://m.wap.oexnr.cn/jnews/81226.htm
- http://m.wap.oexnr.cn/jnews/3377.htm
- http://m.wap.oexnr.cn/jnews/790000.htm
- http://m.wap.oexnr.cn/jnews/83787.htm
- http://m.wap.oexnr.cn/jnews/1005.htm
- http://m.wap.oexnr.cn/jnews/8074.htm
- http://m.wap.oexnr.cn/jnews/26299.htm
- http://m.wap.oexnr.cn/jnews/2494.htm
- http://m.wap.oexnr.cn/jnews/3998.htm
- http://m.wap.oexnr.cn/jnews/028605.htm
- http://m.wap.oexnr.cn/jnews/3999250.htm
- http://m.wap.oexnr.cn/jnews/149554.htm
- http://m.wap.oexnr.cn/jnews/15347.htm
- http://m.wap.oexnr.cn/jnews/6859.htm
- http://m.wap.oexnr.cn/jnews/573482.htm
- http://m.wap.oexnr.cn/jnews/9863881.htm
- http://m.wap.oexnr.cn/jnews/7087.htm
- http://m.wap.oexnr.cn/jnews/46852.htm
- http://m.wap.oexnr.cn/jnews/4400444.htm
- http://m.wap.oexnr.cn/jnews/77883.htm
- http://m.wap.oexnr.cn/jnews/69108.htm
- http://m.wap.oexnr.cn/jnews/8954635.htm
- http://m.wap.oexnr.cn/jnews/783454.htm
- http://m.wap.oexnr.cn/jnews/87300.htm
- http://m.wap.oexnr.cn/jnews/771543.htm
- http://m.wap.oexnr.cn/jnews/2333.htm
- http://m.wap.oexnr.cn/jnews/031130.htm
- http://m.wap.oexnr.cn/jnews/1910.htm
- http://m.wap.oexnr.cn/jnews/066188.htm
- http://m.wap.oexnr.cn/jnews/1227171.htm
- http://m.wap.oexnr.cn/jnews/24484.htm
- http://m.wap.oexnr.cn/jnews/258321.htm
- http://m.wap.oexnr.cn/jnews/157094.htm
- http://m.wap.oexnr.cn/jnews/13591.htm
- http://m.wap.oexnr.cn/jnews/4569.htm
- http://m.wap.oexnr.cn/jnews/4394113.htm
- http://m.wap.oexnr.cn/jnews/58121.htm
- http://m.wap.oexnr.cn/jnews/9449215.htm
- http://m.wap.oexnr.cn/jnews/315769.htm
- http://m.wap.oexnr.cn/jnews/67575.htm
- http://m.wap.oexnr.cn/jnews/7357.htm
- http://m.wap.oexnr.cn/jnews/636808.htm
- http://m.wap.oexnr.cn/jnews/125148.htm
- http://m.wap.oexnr.cn/jnews/19702.htm
- http://m.wap.oexnr.cn/jnews/87485.htm
- http://m.wap.oexnr.cn/jnews/7754.htm
- http://m.wap.oexnr.cn/jnews/6261715.htm
- http://m.wap.oexnr.cn/jnews/351407.htm
- http://m.wap.oexnr.cn/jnews/5773.htm
- http://m.wap.oexnr.cn/jnews/8280.htm
- http://m.wap.oexnr.cn/jnews/0783332.htm
- http://m.wap.oexnr.cn/jnews/619299.htm
- http://m.wap.oexnr.cn/jnews/9590004.htm
- http://m.wap.oexnr.cn/jnews/45396.htm
- http://m.wap.oexnr.cn/jnews/37683.htm
- http://m.wap.oexnr.cn/jnews/73578.htm
- http://m.wap.oexnr.cn/jnews/9970.htm
- http://m.wap.oexnr.cn/jnews/5462.htm
- http://m.wap.oexnr.cn/jnews/095926.htm
- http://m.wap.oexnr.cn/jnews/1672.htm
- http://m.wap.oexnr.cn/jnews/4599985.htm
- http://m.wap.oexnr.cn/jnews/4974525.htm
- http://m.wap.oexnr.cn/jnews/5409.htm
- http://m.wap.oexnr.cn/jnews/50172.htm
- http://m.wap.oexnr.cn/jnews/79479.htm
- http://m.wap.oexnr.cn/jnews/993869.htm
- http://m.wap.oexnr.cn/jnews/1516354.htm
- http://m.wap.oexnr.cn/jnews/286739.htm
- http://m.wap.oexnr.cn/jnews/06166.htm
- http://m.wap.oexnr.cn/jnews/29890.htm
- http://m.wap.oexnr.cn/jnews/0039.htm
- http://m.wap.oexnr.cn/jnews/938243.htm
- http://m.wap.oexnr.cn/jnews/153219.htm
- http://m.wap.oexnr.cn/jnews/1727.htm
- http://m.wap.oexnr.cn/jnews/33030.htm
- http://m.wap.oexnr.cn/jnews/70639.htm
- http://m.wap.oexnr.cn/jnews/5369614.htm
- http://m.wap.oexnr.cn/jnews/21243.htm
- http://m.wap.oexnr.cn/jnews/19506.htm
- http://m.wap.oexnr.cn/jnews/6599752.htm
- http://m.wap.oexnr.cn/jnews/657668.htm
- http://m.wap.oexnr.cn/jnews/017354.htm
- http://m.wap.oexnr.cn/jnews/470603.htm
- http://m.wap.oexnr.cn/jnews/7562.htm
- http://m.wap.oexnr.cn/jnews/56101.htm
- http://m.wap.oexnr.cn/jnews/7878013.htm
- http://m.wap.oexnr.cn/jnews/1586.htm
- http://m.wap.oexnr.cn/jnews/7086770.htm
- http://m.wap.oexnr.cn/jnews/625681.htm
- http://m.wap.oexnr.cn/jnews/4450463.htm
- http://m.wap.oexnr.cn/jnews/6160.htm
- http://m.wap.oexnr.cn/jnews/075741.htm
- http://m.wap.oexnr.cn/jnews/85037.htm
- http://m.wap.oexnr.cn/jnews/698308.htm
- http://m.wap.oexnr.cn/jnews/930516.htm
- http://m.wap.oexnr.cn/jnews/3639.htm
- http://m.wap.oexnr.cn/jnews/818872.htm
- http://m.wap.oexnr.cn/jnews/05407.htm
- http://m.wap.oexnr.cn/jnews/2906.htm
- http://m.wap.oexnr.cn/jnews/68497.htm
- http://m.wap.oexnr.cn/jnews/1582969.htm
- http://m.wap.oexnr.cn/jnews/4874.htm
- http://m.wap.oexnr.cn/jnews/327922.htm
- http://m.wap.oexnr.cn/jnews/28813.htm
- http://m.wap.oexnr.cn/jnews/8825333.htm
- http://m.wap.oexnr.cn/jnews/165950.htm
- http://m.wap.oexnr.cn/jnews/81608.htm
- http://m.wap.oexnr.cn/jnews/982213.htm
- http://m.wap.oexnr.cn/jnews/533485.htm
- http://m.wap.oexnr.cn/jnews/368379.htm
- http://m.wap.oexnr.cn/jnews/5938.htm
- http://m.wap.oexnr.cn/jnews/5469096.htm
- http://m.wap.oexnr.cn/jnews/8750627.htm
- http://m.wap.oexnr.cn/jnews/65666.htm
- http://m.wap.oexnr.cn/jnews/9648966.htm
- http://m.wap.oexnr.cn/jnews/8170360.htm
- http://m.wap.oexnr.cn/jnews/0283.htm
- http://m.wap.oexnr.cn/jnews/32907.htm
- http://m.wap.oexnr.cn/jnews/58227.htm
- http://m.wap.oexnr.cn/jnews/975800.htm
- http://m.wap.oexnr.cn/jnews/496581.htm
- http://m.wap.oexnr.cn/jnews/2942473.htm
- http://m.wap.oexnr.cn/jnews/8215706.htm
- http://m.wap.oexnr.cn/jnews/27764.htm
- http://m.wap.oexnr.cn/jnews/883091.htm
- http://m.wap.oexnr.cn/jnews/945080.htm
- http://m.wap.oexnr.cn/jnews/9957646.htm
- http://m.wap.oexnr.cn/jnews/4713895.htm
- http://m.wap.oexnr.cn/jnews/3796074.htm
- http://m.wap.oexnr.cn/jnews/8653470.htm
- http://m.wap.oexnr.cn/jnews/6769340.htm
- http://m.wap.oexnr.cn/jnews/63184.htm
- http://m.wap.oexnr.cn/jnews/13707.htm
- http://m.wap.oexnr.cn/jnews/3819432.htm
- http://m.wap.oexnr.cn/jnews/971474.htm
- http://m.wap.oexnr.cn/jnews/4873480.htm
- http://m.wap.oexnr.cn/jnews/69864.htm
- http://m.wap.oexnr.cn/jnews/5387594.htm
- http://m.wap.oexnr.cn/jnews/9586.htm
- http://m.wap.oexnr.cn/jnews/37716.htm

## 项目结构

```
oexnr-news-aggregator/
├── data/                                 # 数据存储目录，存放原始 URL 清单和处理后的数据文件
│   ├── urls.txt                          # 核心 URL 索引文件，每行一个链接
│   ├── urls.json                         # JSON 格式的 URL 列表，便于程序读取
│   └── archive/                          # 历史版本归档，保留每次更新的 URL 快照
│       └── 2026-08-25-urls.txt           # 按日期命名的历史清单备份
├── scripts/                              # 可执行脚本目录
│   ├── check_urls.py                     # URL 连通性检测脚本，输出状态报告
│   ├── fetch_metadata.py                 # 批量抓取页面标题和摘要信息
│   ├── export_csv.py                     # 将 URL 列表导出为 CSV 表格
│   └── utils/                            # 通用工具函数模块
│       ├── validators.py                 # URL 格式校验和去重函数
│       └── request_handlers.py           # 统一的 HTTP 请求封装和重试逻辑
├── config/                               # 配置文件目录
│   ├── settings.yaml                     # 全局配置项，包括超时、重试次数、输出路径
│   └── logging.conf                      # 日志输出格式和级别配置
├── docs/                                 # 项目文档
│   ├── user-guide.md                     # 用户使用手册
│   ├── developer-guide.md                # 开发者扩展指南
│   ├── data-schema.md                    # 数据结构和字段说明
│   └── faq.md                            # 常见问题解答
├── reports/                              # 运行报告输出目录
│   ├── status.json                       # 最新一次 URL 状态检测结果
│   └── logs/                             # 脚本执行日志
│       └── app.log
├── tests/                                # 单元测试目录
│   ├── test_validators.py                # 校验函数的测试用例
│   └── test_handlers.py                  # 请求处理函数的测试用例
├── Makefile                              # 构建自动化任务定义
├── requirements.txt                      # Python 依赖声明
├── LICENSE                               # MIT 许可证文本
└── README.md                             # 项目根目录说明文档
```

## 贡献指南

1. 复刻项目仓库到个人账户，在本地创建功能分支进行开发。分支命名建议采用 feature/功能名称 或 fix/问题描述 的格式，便于维护者识别变更意图。

2. 在 data/urls.txt 中新增或更新 URL 条目时，必须保证每行一个链接，并移除重复项。新增的 URL 需通过 scripts/check_urls.py 脚本检测，确保返回状态码为 200 方可提交。

3. 提交代码前运行完整的测试套件，确保未破坏现有功能。若新增采集逻辑或数据处理函数，需同步编写对应的单元测试，覆盖正常输入和边界情况。

4. 发起 Pull Request 时详细描述变更内容，包括新增 URL 的来源说明、脚本功能调整的原因以及测试结果摘要。核心模块的变更需至少一名维护者审阅通过后方可合并。

5. 文档类贡献同样欢迎，包括纠正拼写错误、补充使用示例或翻译非中文章节。文档修改可直接在主分支提交，但涉及安装步骤和配置项说明的变更需经过验证。

## 常见问题

**问：部分 URL 无法访问或返回 404 状态码，是否应该从清单中移除？**

答：不建议立即移除。移动端新闻页面的临时下线或路径调整较为常见，建议使用 check_urls.py 脚本持续监测一段时间（如 7 天），若持续无法访问再考虑归档至 archive 目录。项目维护者会定期清理长期失效的链接，但不会在未经通知的情况下删除用户提交的 URL。

**问：采集脚本运行时遇到编码错误或乱码，如何解决？**

答：oexnr.cn 移动端页面多数采用 UTF-8 编码，但部分历史页面可能使用 GBK 或 GB2312。在 fetch_metadata.py 中已内置编码自动检测逻辑，若仍出现乱码，可尝试在请求头中指定 Accept-Encoding 和 CharSet，或手动在配置文件中设置 fallback_encoding 参数为 gbk。

**问：项目是否提供定时自动更新 URL 清单的功能？**

答：项目本身不内置定时任务调度器，但提供了完整的命令行接口和 Makefile 任务。用户可通过系统自带的 cron（Linux/macOS）或计划任务（Windows）定期执行 make update-index 命令，结合自己的需求设置更新频率。具体配置方法参见 docs/deployment.md 中的部署示例。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
