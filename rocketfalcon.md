# WebIndex 聚合导航系统

WebIndex 是一个面向技术研究者与信息分析人员的轻量级外链聚合与新闻索引系统。该项目不提供内容存储，不进行数据清洗，仅作为 URL 索引层，用于对分散在移动端新闻门户中的特定条目进行统一收录、分类标注与可追溯管理。目标用户包括信息采集工程师、舆情监控平台运维人员、搜索引擎优化顾问以及学术研究机构的数据标注团队。

WebIndex 解决了以下核心问题：大量有价值的新闻条目与信息页面分散在移动端域名下，缺乏统一的入口索引；人工记录容易丢失来源且无法批量追踪；传统爬虫体系对零散 URL 的管理成本过高。本项目以极简的静态索引结构，提供一套可维护、可扩展、可版本控制的外链登记方案，使得用户能够快速定位到具体新闻编号，并依据编号规则进行二次数据整理与归档。

## 功能概览

**基于编号的精准索引** 每个收录的 URL 均包含独立的数字编号，系统按照编号段进行逻辑分组，方便用户通过编号快速筛选目标条目。

**移动端页面适配标记** 所有链接均来自移动端域名 m.wap.oexnr.cn，系统自动识别并标记其移动端特性，便于用户在不同设备环境下进行访问测试。

**可扩展的目录结构** 项目采用分类子目录组织方式，支持按照新闻类型、发布时间、重要性等级进行多维度归类，无需修改核心代码即可扩展新类别。

**轻量级纯静态部署** 无需数据库支持，无需后端服务，所有索引数据以 Markdown 和 JSON 格式存储，可直接托管于任何静态文件服务器或代码托管平台。

**版本化变更追踪** 基于 Git 进行每次收录操作的变更记录，每次新增或删除 URL 均形成可追溯的提交历史，便于团队协作与审计。

**批量导入与校验工具** 提供命令行脚本，支持从 CSV 或纯文本列表中批量导入 URL，并自动校验链接可访问性及格式合法性。

**标签化分类体系** 支持对每条链接添加多个文本标签，标签体系完全由用户自定义，满足不同项目的分类需求。

**快速检索与过滤** 内置简单的 grep 与 awk 查询脚本，能够在秒级完成对数百条 URL 的编号匹配与域名筛选操作。

## 应用场景

**移动端新闻监控与采集** 数据分析团队可使用本索引作为基础数据源，每日定时拉取最新收录的新闻编号，并结合第三方采集工具对目标页面进行内容抓取与情感分析。通过统一的索引层，团队能够避免重复记录和遗漏。

**历史报道追溯与归档** 研究人员在回顾特定事件或趋势时，可通过本索引快速定位到过往收录的报道编号，结合项目结构中的分类目录，按主题或时间段进行批量回溯，极大提升文献调研效率。

**链接可用性定期巡检** 运维人员可利用项目提供的校验工具，对所有索引链接进行周期性连通性测试，及时发现失效链接并进行标记或移除，保证索引库的健康度。

**第三方系统数据对接** 开发人员可通过本项目提供的 JSON 导出接口，将全部索引数据导入到自有 CMS 系统、舆情大屏或数据分析平台中，作为外部数据源的基础层。

## 快速开始

```bash
# 克隆项目仓库到本地
git clone https://github.com/your-org/webindex.git

# 进入项目根目录
cd webindex

# 安装基础依赖（仅需 Python 3.8+ 与 coreutils）
pip install -r requirements.txt

# 运行索引校验脚本，检查所有 URL 格式是否正确
./scripts/validate_index.sh

# 启动本地静态预览服务（默认端口 8080）
python -m http.server 8080
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 或更高 | 用于运行校验脚本与导出工具 |
| Git | 2.25 或更高 | 用于版本控制与克隆仓库 |
| Bash | 4.0 或更高 | 用于执行 shell 脚本工具链 |
| curl | 7.68 或更高 | 用于链接可用性测试工具 |
| grep | 3.4 或更高 | 用于文本检索与编号过滤 |
| awk | 5.0 或更高 | 用于结构化数据解析 |
| sed | 4.7 或更高 | 用于批量文本替换操作 |
| coreutils | 8.30 或更高 | 提供基础文件操作命令 |
| jq | 1.6 或更高 | 用于 JSON 数据的生成与解析 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 索引层 | /index/ | 包含所有 URL 的主索引文件，按编号范围分段存储，用户可快速定位到目标编号所在的文件位置。 |
| 分类层 | /categories/ | 按照预定义分类（技术、财经、社会、国际、体育等）对链接进行二次映射，解答特定主题下有哪些收录条目的问题。 |
| 工具层 | /scripts/ | 提供导入、校验、导出、统计等命令行工具，解答如何批量操作索引数据以及如何自动化日常维护的问题。 |
| 数据层 | /data/raw/ 与 /data/parsed/ | 存储原始导入文件与解析后的结构化数据，解答数据来源如何追溯以及解析格式如何定义的问题。 |
| 配置层 | /config/ | 存放分类映射规则、标签词典与校验白名单，解答如何自定义项目行为以适应不同使用环境的问题。 |
| 输出层 | /output/ | 存放生成的静态页面与 JSON 导出文件，解答如何将索引数据发布为可视化页面或 API 接口的问题。 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/3376.htm
- http://m.wap.oexnr.cn/jnews/3343.htm
- http://m.wap.oexnr.cn/jnews/5058679.htm
- http://m.wap.oexnr.cn/jnews/8861.htm
- http://m.wap.oexnr.cn/jnews/456382.htm
- http://m.wap.oexnr.cn/jnews/892713.htm
- http://m.wap.oexnr.cn/jnews/25321.htm
- http://m.wap.oexnr.cn/jnews/2383.htm
- http://m.wap.oexnr.cn/jnews/4764554.htm
- http://m.wap.oexnr.cn/jnews/0246.htm
- http://m.wap.oexnr.cn/jnews/95369.htm
- http://m.wap.oexnr.cn/jnews/7387.htm
- http://m.wap.oexnr.cn/jnews/883668.htm
- http://m.wap.oexnr.cn/jnews/1269657.htm
- http://m.wap.oexnr.cn/jnews/335145.htm
- http://m.wap.oexnr.cn/jnews/138411.htm
- http://m.wap.oexnr.cn/jnews/01401.htm
- http://m.wap.oexnr.cn/jnews/1528053.htm
- http://m.wap.oexnr.cn/jnews/2335819.htm
- http://m.wap.oexnr.cn/jnews/29232.htm
- http://m.wap.oexnr.cn/jnews/0154.htm
- http://m.wap.oexnr.cn/jnews/417733.htm
- http://m.wap.oexnr.cn/jnews/0749684.htm
- http://m.wap.oexnr.cn/jnews/6047395.htm
- http://m.wap.oexnr.cn/jnews/5719.htm
- http://m.wap.oexnr.cn/jnews/5890.htm
- http://m.wap.oexnr.cn/jnews/21090.htm
- http://m.wap.oexnr.cn/jnews/33126.htm
- http://m.wap.oexnr.cn/jnews/7247.htm
- http://m.wap.oexnr.cn/jnews/8625946.htm
- http://m.wap.oexnr.cn/jnews/295387.htm
- http://m.wap.oexnr.cn/jnews/5938796.htm
- http://m.wap.oexnr.cn/jnews/6935661.htm
- http://m.wap.oexnr.cn/jnews/5186.htm
- http://m.wap.oexnr.cn/jnews/6016666.htm
- http://m.wap.oexnr.cn/jnews/9823.htm
- http://m.wap.oexnr.cn/jnews/8237.htm
- http://m.wap.oexnr.cn/jnews/1404419.htm
- http://m.wap.oexnr.cn/jnews/2607.htm
- http://m.wap.oexnr.cn/jnews/1360284.htm
- http://m.wap.oexnr.cn/jnews/3476171.htm
- http://m.wap.oexnr.cn/jnews/1595.htm
- http://m.wap.oexnr.cn/jnews/4271138.htm
- http://m.wap.oexnr.cn/jnews/666440.htm
- http://m.wap.oexnr.cn/jnews/8991.htm
- http://m.wap.oexnr.cn/jnews/9335.htm
- http://m.wap.oexnr.cn/jnews/3292.htm
- http://m.wap.oexnr.cn/jnews/76431.htm
- http://m.wap.oexnr.cn/jnews/4122.htm
- http://m.wap.oexnr.cn/jnews/86078.htm
- http://m.wap.oexnr.cn/jnews/29848.htm
- http://m.wap.oexnr.cn/jnews/2847.htm
- http://m.wap.oexnr.cn/jnews/1920035.htm
- http://m.wap.oexnr.cn/jnews/1031.htm
- http://m.wap.oexnr.cn/jnews/3119.htm
- http://m.wap.oexnr.cn/jnews/2497.htm
- http://m.wap.oexnr.cn/jnews/1657.htm
- http://m.wap.oexnr.cn/jnews/2328157.htm
- http://m.wap.oexnr.cn/jnews/9650.htm
- http://m.wap.oexnr.cn/jnews/8363.htm
- http://m.wap.oexnr.cn/jnews/4748.htm
- http://m.wap.oexnr.cn/jnews/89371.htm
- http://m.wap.oexnr.cn/jnews/7419195.htm
- http://m.wap.oexnr.cn/jnews/7170.htm
- http://m.wap.oexnr.cn/jnews/39497.htm
- http://m.wap.oexnr.cn/jnews/0058973.htm
- http://m.wap.oexnr.cn/jnews/5296.htm
- http://m.wap.oexnr.cn/jnews/75414.htm
- http://m.wap.oexnr.cn/jnews/4466118.htm
- http://m.wap.oexnr.cn/jnews/7126245.htm
- http://m.wap.oexnr.cn/jnews/822933.htm
- http://m.wap.oexnr.cn/jnews/4505934.htm
- http://m.wap.oexnr.cn/jnews/306145.htm
- http://m.wap.oexnr.cn/jnews/7044334.htm
- http://m.wap.oexnr.cn/jnews/752731.htm
- http://m.wap.oexnr.cn/jnews/999476.htm
- http://m.wap.oexnr.cn/jnews/6346.htm
- http://m.wap.oexnr.cn/jnews/21861.htm
- http://m.wap.oexnr.cn/jnews/51961.htm
- http://m.wap.oexnr.cn/jnews/8939.htm
- http://m.wap.oexnr.cn/jnews/370868.htm
- http://m.wap.oexnr.cn/jnews/9581.htm
- http://m.wap.oexnr.cn/jnews/3697.htm
- http://m.wap.oexnr.cn/jnews/4444.htm
- http://m.wap.oexnr.cn/jnews/9771331.htm
- http://m.wap.oexnr.cn/jnews/7872.htm
- http://m.wap.oexnr.cn/jnews/86911.htm
- http://m.wap.oexnr.cn/jnews/4592.htm
- http://m.wap.oexnr.cn/jnews/1244704.htm
- http://m.wap.oexnr.cn/jnews/19073.htm
- http://m.wap.oexnr.cn/jnews/6622387.htm
- http://m.wap.oexnr.cn/jnews/2923.htm
- http://m.wap.oexnr.cn/jnews/030848.htm
- http://m.wap.oexnr.cn/jnews/1143.htm
- http://m.wap.oexnr.cn/jnews/941950.htm
- http://m.wap.oexnr.cn/jnews/5676572.htm
- http://m.wap.oexnr.cn/jnews/957893.htm
- http://m.wap.oexnr.cn/jnews/1256.htm
- http://m.wap.oexnr.cn/jnews/4180268.htm
- http://m.wap.oexnr.cn/jnews/0970.htm
- http://m.wap.oexnr.cn/jnews/58473.htm
- http://m.wap.oexnr.cn/jnews/647334.htm
- http://m.wap.oexnr.cn/jnews/08233.htm
- http://m.wap.oexnr.cn/jnews/8261415.htm
- http://m.wap.oexnr.cn/jnews/7677602.htm
- http://m.wap.oexnr.cn/jnews/04300.htm
- http://m.wap.oexnr.cn/jnews/1039.htm
- http://m.wap.oexnr.cn/jnews/60835.htm
- http://m.wap.oexnr.cn/jnews/522877.htm
- http://m.wap.oexnr.cn/jnews/837312.htm
- http://m.wap.oexnr.cn/jnews/2621335.htm
- http://m.wap.oexnr.cn/jnews/33203.htm
- http://m.wap.oexnr.cn/jnews/2384439.htm
- http://m.wap.oexnr.cn/jnews/829318.htm
- http://m.wap.oexnr.cn/jnews/528838.htm
- http://m.wap.oexnr.cn/jnews/2179.htm
- http://m.wap.oexnr.cn/jnews/321930.htm
- http://m.wap.oexnr.cn/jnews/54883.htm
- http://m.wap.oexnr.cn/jnews/4561.htm
- http://m.wap.oexnr.cn/jnews/67095.htm
- http://m.wap.oexnr.cn/jnews/64145.htm
- http://m.wap.oexnr.cn/jnews/05517.htm
- http://m.wap.oexnr.cn/jnews/74504.htm
- http://m.wap.oexnr.cn/jnews/4070.htm
- http://m.wap.oexnr.cn/jnews/5189617.htm
- http://m.wap.oexnr.cn/jnews/31801.htm
- http://m.wap.oexnr.cn/jnews/8077177.htm
- http://m.wap.oexnr.cn/jnews/634631.htm
- http://m.wap.oexnr.cn/jnews/379112.htm
- http://m.wap.oexnr.cn/jnews/7238291.htm
- http://m.wap.oexnr.cn/jnews/7251108.htm
- http://m.wap.oexnr.cn/jnews/9766.htm
- http://m.wap.oexnr.cn/jnews/0597.htm
- http://m.wap.oexnr.cn/jnews/940029.htm
- http://m.wap.oexnr.cn/jnews/238865.htm
- http://m.wap.oexnr.cn/jnews/2210.htm
- http://m.wap.oexnr.cn/jnews/9428.htm
- http://m.wap.oexnr.cn/jnews/6294.htm
- http://m.wap.oexnr.cn/jnews/867903.htm
- http://m.wap.oexnr.cn/jnews/6917229.htm
- http://m.wap.oexnr.cn/jnews/334583.htm
- http://m.wap.oexnr.cn/jnews/1155079.htm
- http://m.wap.oexnr.cn/jnews/153627.htm
- http://m.wap.oexnr.cn/jnews/39628.htm
- http://m.wap.oexnr.cn/jnews/18383.htm
- http://m.wap.oexnr.cn/jnews/6040.htm
- http://m.wap.oexnr.cn/jnews/08536.htm
- http://m.wap.oexnr.cn/jnews/119364.htm
- http://m.wap.oexnr.cn/jnews/3083644.htm
- http://m.wap.oexnr.cn/jnews/98040.htm
- http://m.wap.oexnr.cn/jnews/945655.htm
- http://m.wap.oexnr.cn/jnews/33351.htm
- http://m.wap.oexnr.cn/jnews/6756857.htm
- http://m.wap.oexnr.cn/jnews/1482.htm
- http://m.wap.oexnr.cn/jnews/289874.htm
- http://m.wap.oexnr.cn/jnews/91171.htm
- http://m.wap.oexnr.cn/jnews/8656745.htm
- http://m.wap.oexnr.cn/jnews/5353.htm
- http://m.wap.oexnr.cn/jnews/3489.htm
- http://m.wap.oexnr.cn/jnews/6462448.htm
- http://m.wap.oexnr.cn/jnews/42375.htm
- http://m.wap.oexnr.cn/jnews/12430.htm
- http://m.wap.oexnr.cn/jnews/022566.htm
- http://m.wap.oexnr.cn/jnews/9305.htm
- http://m.wap.oexnr.cn/jnews/2800.htm
- http://m.wap.oexnr.cn/jnews/99578.htm
- http://m.wap.oexnr.cn/jnews/44312.htm
- http://m.wap.oexnr.cn/jnews/5218120.htm
- http://m.wap.oexnr.cn/jnews/6855.htm
- http://m.wap.oexnr.cn/jnews/9637.htm
- http://m.wap.oexnr.cn/jnews/5088.htm
- http://m.wap.oexnr.cn/jnews/595957.htm
- http://m.wap.oexnr.cn/jnews/793370.htm
- http://m.wap.oexnr.cn/jnews/377446.htm
- http://m.wap.oexnr.cn/jnews/3664906.htm
- http://m.wap.oexnr.cn/jnews/8680594.htm
- http://m.wap.oexnr.cn/jnews/5016.htm
- http://m.wap.oexnr.cn/jnews/9028425.htm
- http://m.wap.oexnr.cn/jnews/2268865.htm
- http://m.wap.oexnr.cn/jnews/0797.htm
- http://m.wap.oexnr.cn/jnews/845461.htm
- http://m.wap.oexnr.cn/jnews/207938.htm
- http://m.wap.oexnr.cn/jnews/04822.htm
- http://m.wap.oexnr.cn/jnews/6049899.htm
- http://m.wap.oexnr.cn/jnews/2909841.htm
- http://m.wap.oexnr.cn/jnews/0745.htm
- http://m.wap.oexnr.cn/jnews/932887.htm
- http://m.wap.oexnr.cn/jnews/54949.htm
- http://m.wap.oexnr.cn/jnews/58478.htm
- http://m.wap.oexnr.cn/jnews/94715.htm
- http://m.wap.oexnr.cn/jnews/5994.htm
- http://m.wap.oexnr.cn/jnews/6638.htm
- http://m.wap.oexnr.cn/jnews/6683662.htm
- http://m.wap.oexnr.cn/jnews/425822.htm
- http://m.wap.oexnr.cn/jnews/6950510.htm
- http://m.wap.oexnr.cn/jnews/2903145.htm
- http://m.wap.oexnr.cn/jnews/134862.htm
- http://m.wap.oexnr.cn/jnews/0229.htm
- http://m.wap.oexnr.cn/jnews/9482758.htm
- http://m.wap.oexnr.cn/jnews/504805.htm
- http://m.wap.oexnr.cn/jnews/2454.htm
- http://m.wap.oexnr.cn/jnews/1300802.htm
- http://m.wap.oexnr.cn/jnews/18937.htm
- http://m.wap.oexnr.cn/jnews/9347062.htm
- http://m.wap.oexnr.cn/jnews/236874.htm
- http://m.wap.oexnr.cn/jnews/0472.htm
- http://m.wap.oexnr.cn/jnews/1950.htm
- http://m.wap.oexnr.cn/jnews/512573.htm
- http://m.wap.oexnr.cn/jnews/1017.htm
- http://m.wap.oexnr.cn/jnews/24546.htm
- http://m.wap.oexnr.cn/jnews/33795.htm
- http://m.wap.oexnr.cn/jnews/592963.htm
- http://m.wap.oexnr.cn/jnews/9539999.htm
- http://m.wap.oexnr.cn/jnews/83406.htm
- http://m.wap.oexnr.cn/jnews/3231.htm
- http://m.wap.oexnr.cn/jnews/590761.htm
- http://m.wap.oexnr.cn/jnews/8670873.htm
- http://m.wap.oexnr.cn/jnews/6954.htm
- http://m.wap.oexnr.cn/jnews/097501.htm
- http://m.wap.oexnr.cn/jnews/9163502.htm
- http://m.wap.oexnr.cn/jnews/999721.htm
- http://m.wap.oexnr.cn/jnews/925341.htm
- http://m.wap.oexnr.cn/jnews/7543759.htm
- http://m.wap.oexnr.cn/jnews/0719.htm
- http://m.wap.oexnr.cn/jnews/974560.htm
- http://m.wap.oexnr.cn/jnews/3117349.htm
- http://m.wap.oexnr.cn/jnews/957510.htm
- http://m.wap.oexnr.cn/jnews/78039.htm
- http://m.wap.oexnr.cn/jnews/9172982.htm
- http://m.wap.oexnr.cn/jnews/092433.htm
- http://m.wap.oexnr.cn/jnews/05951.htm
- http://m.wap.oexnr.cn/jnews/7991158.htm
- http://m.wap.oexnr.cn/jnews/7883852.htm
- http://m.wap.oexnr.cn/jnews/4017913.htm
- http://m.wap.oexnr.cn/jnews/820790.htm
- http://m.wap.oexnr.cn/jnews/1913351.htm
- http://m.wap.oexnr.cn/jnews/6917987.htm
- http://m.wap.oexnr.cn/jnews/140408.htm
- http://m.wap.oexnr.cn/jnews/0593.htm
- http://m.wap.oexnr.cn/jnews/55896.htm
- http://m.wap.oexnr.cn/jnews/42216.htm
- http://m.wap.oexnr.cn/jnews/7705378.htm
- http://m.wap.oexnr.cn/jnews/1103061.htm
- http://m.wap.oexnr.cn/jnews/5910953.htm
- http://m.wap.oexnr.cn/jnews/2922512.htm
- http://m.wap.oexnr.cn/jnews/5898.htm
- http://m.wap.oexnr.cn/jnews/1683326.htm
- http://m.wap.oexnr.cn/jnews/7808656.htm
- http://m.wap.oexnr.cn/jnews/91408.htm
- http://m.wap.oexnr.cn/jnews/248931.htm
- http://m.wap.oexnr.cn/jnews/184203.htm
- http://m.wap.oexnr.cn/jnews/8949.htm
- http://m.wap.oexnr.cn/jnews/405376.htm
- http://m.wap.oexnr.cn/jnews/2990.htm
- http://m.wap.oexnr.cn/jnews/57473.htm
- http://m.wap.oexnr.cn/jnews/5466.htm
- http://m.wap.oexnr.cn/jnews/9589986.htm
- http://m.wap.oexnr.cn/jnews/65661.htm
- http://m.wap.oexnr.cn/jnews/72568.htm
- http://m.wap.oexnr.cn/jnews/606736.htm
- http://m.wap.oexnr.cn/jnews/47617.htm
- http://m.wap.oexnr.cn/jnews/809475.htm
- http://m.wap.oexnr.cn/jnews/7407725.htm
- http://m.wap.oexnr.cn/jnews/318990.htm
- http://m.wap.oexnr.cn/jnews/2982762.htm
- http://m.wap.oexnr.cn/jnews/007130.htm
- http://m.wap.oexnr.cn/jnews/116761.htm
- http://m.wap.oexnr.cn/jnews/873927.htm
- http://m.wap.oexnr.cn/jnews/34528.htm
- http://m.wap.oexnr.cn/jnews/350286.htm
- http://m.wap.oexnr.cn/jnews/456018.htm
- http://m.wap.oexnr.cn/jnews/8230664.htm
- http://m.wap.oexnr.cn/jnews/632507.htm
- http://m.wap.oexnr.cn/jnews/6352366.htm
- http://m.wap.oexnr.cn/jnews/67368.htm
- http://m.wap.oexnr.cn/jnews/4730438.htm
- http://m.wap.oexnr.cn/jnews/243732.htm
- http://m.wap.oexnr.cn/jnews/6009.htm
- http://m.wap.oexnr.cn/jnews/3459.htm
- http://m.wap.oexnr.cn/jnews/5300.htm
- http://m.wap.oexnr.cn/jnews/86258.htm
- http://m.wap.oexnr.cn/jnews/731875.htm
- http://m.wap.oexnr.cn/jnews/38387.htm
- http://m.wap.oexnr.cn/jnews/9530508.htm
- http://m.wap.oexnr.cn/jnews/29997.htm
- http://m.wap.oexnr.cn/jnews/084273.htm
- http://m.wap.oexnr.cn/jnews/02380.htm
- http://m.wap.oexnr.cn/jnews/6929865.htm
- http://m.wap.oexnr.cn/jnews/8437.htm
- http://m.wap.oexnr.cn/jnews/7086.htm
- http://m.wap.oexnr.cn/jnews/2469710.htm
- http://m.wap.oexnr.cn/jnews/190161.htm
- http://m.wap.oexnr.cn/jnews/7692736.htm
- http://m.wap.oexnr.cn/jnews/1688346.htm
- http://m.wap.oexnr.cn/jnews/6485843.htm
- http://m.wap.oexnr.cn/jnews/6029.htm
- http://m.wap.oexnr.cn/jnews/930810.htm
- http://m.wap.oexnr.cn/jnews/42089.htm
- http://m.wap.oexnr.cn/jnews/6292.htm
- http://m.wap.oexnr.cn/jnews/790690.htm

## 项目结构

```
webindex/
├── index/                          # 主索引目录，按编号范围分段
│   ├── 0_999.md                    # 编号 0-999 的链接列表
│   ├── 1000_9999.md                # 编号 1000-9999 的链接列表
│   ├── 10000_99999.md              # 编号 10000-99999 的链接列表
│   ├── 100000_999999.md            # 编号 100000-999999 的链接列表
│   └── 1000000_9999999.md          # 编号 1000000-9999999 的链接列表
│
├── categories/                     # 分类映射目录
│   ├── technology.md               # 技术类链接的二次索引
│   ├── finance.md                  # 财经类链接的二次索引
│   ├── society.md                  # 社会类链接的二次索引
│   ├── international.md            # 国际类链接的二次索引
│   └── sports.md                   # 体育类链接的二次索引
│
├── scripts/                        # 工具脚本目录
│   ├── validate_index.sh           # 校验所有 URL 格式与可访问性
│   ├── import_csv.py               # 从 CSV 文件批量导入链接
│   ├── export_json.py              # 导出全部索引为 JSON 格式
│   ├── stats.sh                    # 统计各类别链接数量
│   └── dedup.sh                    # 检测并移除重复收录的 URL
│
├── data/                           # 数据存储目录
│   ├── raw/                        # 原始导入文件备份
│   │   ├── batch_20260801.csv
│   │   └── batch_20260825.txt
│   └── parsed/                     # 解析后的结构化数据
│       └── index_normalized.json
│
├── config/                         # 配置文件目录
│   ├── categories.conf             # 分类与标签映射规则
│   ├── whitelist.conf              # 域名白名单校验规则
│   └── schema.json                 # JSON 导出格式定义
│
├── output/                         # 输出产物目录
│   ├── static/                     # 生成的静态 HTML 页面
│   └── api/                        # 导出的 JSON API 数据
│
├── docs/                           # 项目文档
│   ├── api_reference.md            # 导出接口参数说明
│   ├── contribution_guide.md       # 详细贡献流程
│   └── changelog.md                # 版本更新历史
│
├── tests/                          # 单元测试与集成测试
│   ├── test_validator.py
│   └── test_importer.py
│
├── README.md                       # 项目介绍与快速入门
├── LICENSE                         # MIT 许可证文件
├── requirements.txt                # Python 依赖清单
└── .gitignore                      # Git 忽略文件配置
```

## 贡献指南

**提交新链接** 在 index 目录下找到对应编号范围的 Markdown 文件，按照已有格式追加新的链接条目，并确保编号不重复。提交前运行 validate_index.sh 进行格式校验。

**创建新的分类映射** 在 categories 目录中新建或编辑对应的分类文件，将已有链接通过编号引用方式添加到分类下。分类文件格式为每行一个编号，后跟可选的备注说明。

**完善工具脚本** 如果发现校验工具或导入脚本存在缺陷，请先编写对应的单元测试，然后提交修复代码。所有脚本需保持与 POSIX 标准的兼容性，避免使用 GNU 扩展特性。

**更新项目文档** 当新增功能或修改配置结构时，需同步更新 README 以及 docs 目录下的相关文档。文档变更应与代码变更位于同一提交中，保持一致性。

**报告问题与建议** 通过项目 Issue 追踪系统提交问题报告，需附带完整的环境信息、复现步骤和期望行为。功能建议应明确说明使用场景和预期收益。

## 常见问题

**问：链接编号的生成规则是什么？为什么编号不是连续的？**

答：编号直接取自源新闻系统自身的发布编号，本项目不对编号进行重新编排或补全。编号不连续是因为源系统本身的编号体系存在跳号，这是正常现象，不影响索引功能。用户可以通过编号大致判断条目的相对顺序。

**问：如何批量验证所有链接是否仍然有效？**

答：项目提供了 scripts/validate_index.sh 脚本，该脚本会遍历所有索引文件中的 URL，使用 curl 发起 HEAD 请求检测响应状态。检测结果会输出到控制台并同时写入 logs/validation_report.log 文件，便于后续分析和清理失效链接。

**问：是否支持自动抓取链接对应的页面标题和摘要信息？**

答：当前版本的设计定位为轻量级索引层，不包含内容抓取功能，以避免法律风险和版权问题。用户可以通过二次开发集成第三方抓取服务，或手动在分类文件中为链接添加备注说明。后续版本会考虑提供可选的元数据扩展字段。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
