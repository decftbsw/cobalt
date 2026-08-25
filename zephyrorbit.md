# NewsLink 聚合导航系统

NewsLink 聚合导航系统是一个面向技术资讯聚合与外部资源结构化管理的开源导航工具，定位于为开发者、技术研究人员以及信息聚合爱好者提供统一的新闻链接采集、分类、存储与检索能力。该项目通过解析特定来源的新闻页面标识符，将大量散落的动态资讯地址转化为可索引、可分类、可回溯的导航资源池，适用于需要定期跟踪大量主题新闻、公告或事件通知的场景。

本项目内置了第 11/300 批次共计三百个新闻链接资源，配合目录解析脚本与分类过滤工具，可以快速构建从采集到展示的完整导航工作流。目标用户包括需要运维公告聚合看板的系统管理员、需要跟踪行业动态的技术决策者以及希望批量管理信息入口的内容整理人员。

## 功能概览

**动态链接识别与解析**：针对批量生成的数字型页面标识符进行自动识别与规则匹配，提取有效访问路径。

**多级目录自动归类**：依据链接中的目录层级与文件命名规则，将资源自动划分到预设分类树中，支持自定义分类映射。

**批次化资源管理**：以三百条链接为一个标准批次进行组织，支持多批次并行导入、增量更新与版本记录。

**去重与有效性校验**：内置链接去重算法，可检测重复条目并标记失效或重定向的地址，减少无效导航条目。

**全文检索与标签筛选**：基于链接元数据（标题、分类、批次号、录入时间）提供关键字检索和多维标签组合筛选。

**导航站静态生成**：支持将整理后的链接集合导出为静态导航页面（HTML 格式），可直接部署到任意 Web 服务器或 CDN。

**扩展导入导出接口**：支持 JSON、CSV、Markdown 列表三种格式的批量导入导出，便于与其他系统或人工编辑流程对接。

## 应用场景

**技术团队内部资讯看板**：开发团队可以利用 NewsLink 系统将每日关注的行业新闻、安全公告、版本发布链接集中管理，生成团队共享的资讯导航页，减少重复搜索时间。

**个人知识库外链整理**：研究人员或技术博主可将长期积累的参考链接按主题批次导入系统，通过标签和分类快速定位历史资料，避免收藏夹无序膨胀。

**活动或会议通知聚合**：组织者可将多场线上技术会议、开源社区活动通知链接归入同一批次，生成时间线导航页面，方便参会者一站式访问。

**自动化采集流水线终点**：结合爬虫或 RSS 订阅工具，将抓取到的新闻地址自动存入 NewsLink 的导入目录，由系统完成去重和分类，形成持续更新的导航资源库。

## 快速开始

以下步骤帮助您在本地快速启动 NewsLink 聚合导航系统。

```bash
# 克隆项目仓库到本地
git clone https://github.com/example/newslink-navigator.git

# 进入项目根目录
cd newslink-navigator

# 安装 Python 依赖（需要 Python 3.8+）
pip install -r requirements.txt

# 执行批次导入脚本，载入第 11 批资源（示例）
python scripts/batch_import.py --batch 11 --source data/batch_11_raw.txt

# 启动本地预览服务
python app.py --port 8080
```

启动后，在浏览器中访问 http://localhost:8080 即可查看导航首页。默认使用内置的轻量级 SQLite 数据库，无需额外配置。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行导入脚本与 Web 服务 |
| SQLite | 3.28 及以上 | 默认嵌入式数据库，用于存储链接元数据与分类树 |
| pip | 21.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| Flask | 2.2.3 及以上 | Web 界面框架，提供导航页预览与管理后台 |
| beautifulsoup4 | 4.11.0 及以上 | 用于解析导入的 HTML 摘要信息（可选，增强模式需要） |
| requests | 2.28.0 及以上 | 用于远程链接可用性校验（可选，建议安装） |
| markdown | 3.4.0 及以上 | 用于将 Markdown 资源列表转换为内部数据结构 |
| git | 2.25 及以上 | 用于克隆仓库和版本管理（开发环境需要） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|-----|------|-----------|
| 用户手册 | docs/user_guide.md | 如何导入链接批次、如何创建分类、如何生成导航页面 |
| 管理员指南 | docs/admin_guide.md | 如何配置自动去重规则、如何调整校验策略、如何备份数据库 |
| 开发者文档 | docs/developer_api.md | 如何扩展导入格式、如何自定义分类器、如何集成外部存储 |
| 批次规范 | docs/batch_spec.md | 批次文件的格式要求、编号规则、字段定义及示例 |
| 部署指南 | docs/deployment.md | 如何将系统部署到生产服务器、如何使用 Docker 运行 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/3771.htm
- http://m.3g.oexnr.cn/nnews/238938.htm
- http://m.3g.oexnr.cn/nnews/49116.htm
- http://m.3g.oexnr.cn/nnews/75703.htm
- http://m.3g.oexnr.cn/nnews/6372.htm
- http://m.3g.oexnr.cn/nnews/386537.htm
- http://m.3g.oexnr.cn/nnews/015361.htm
- http://m.3g.oexnr.cn/nnews/0278053.htm
- http://m.3g.oexnr.cn/nnews/20545.htm
- http://m.3g.oexnr.cn/nnews/101092.htm
- http://m.3g.oexnr.cn/nnews/1177.htm
- http://m.3g.oexnr.cn/nnews/6695.htm
- http://m.3g.oexnr.cn/nnews/703996.htm
- http://m.3g.oexnr.cn/nnews/174659.htm
- http://m.3g.oexnr.cn/nnews/5854.htm
- http://m.3g.oexnr.cn/nnews/03443.htm
- http://m.3g.oexnr.cn/nnews/5370574.htm
- http://m.3g.oexnr.cn/nnews/8399419.htm
- http://m.3g.oexnr.cn/nnews/2743.htm
- http://m.3g.oexnr.cn/nnews/387261.htm
- http://m.3g.oexnr.cn/nnews/88283.htm
- http://m.3g.oexnr.cn/nnews/840683.htm
- http://m.3g.oexnr.cn/nnews/17403.htm
- http://m.3g.oexnr.cn/nnews/9965.htm
- http://m.3g.oexnr.cn/nnews/2224.htm
- http://m.3g.oexnr.cn/nnews/44834.htm
- http://m.3g.oexnr.cn/nnews/738225.htm
- http://m.3g.oexnr.cn/nnews/3235.htm
- http://m.3g.oexnr.cn/nnews/470604.htm
- http://m.3g.oexnr.cn/nnews/3904.htm
- http://m.3g.oexnr.cn/nnews/750582.htm
- http://m.3g.oexnr.cn/nnews/5490245.htm
- http://m.3g.oexnr.cn/nnews/0960708.htm
- http://m.3g.oexnr.cn/nnews/078565.htm
- http://m.3g.oexnr.cn/nnews/962286.htm
- http://m.3g.oexnr.cn/nnews/75437.htm
- http://m.3g.oexnr.cn/nnews/54114.htm
- http://m.3g.oexnr.cn/nnews/369763.htm
- http://m.3g.oexnr.cn/nnews/446534.htm
- http://m.3g.oexnr.cn/nnews/832846.htm
- http://m.3g.oexnr.cn/nnews/24926.htm
- http://m.3g.oexnr.cn/nnews/806548.htm
- http://m.3g.oexnr.cn/nnews/5028.htm
- http://m.3g.oexnr.cn/nnews/45218.htm
- http://m.3g.oexnr.cn/nnews/1433.htm
- http://m.3g.oexnr.cn/nnews/0765.htm
- http://m.3g.oexnr.cn/nnews/020369.htm
- http://m.3g.oexnr.cn/nnews/5068220.htm
- http://m.3g.oexnr.cn/nnews/3911652.htm
- http://m.3g.oexnr.cn/nnews/947424.htm
- http://m.3g.oexnr.cn/nnews/7855.htm
- http://m.3g.oexnr.cn/nnews/36078.htm
- http://m.3g.oexnr.cn/nnews/1821.htm
- http://m.3g.oexnr.cn/nnews/036788.htm
- http://m.3g.oexnr.cn/nnews/804399.htm
- http://m.3g.oexnr.cn/nnews/28138.htm
- http://m.3g.oexnr.cn/nnews/387363.htm
- http://m.3g.oexnr.cn/nnews/5407.htm
- http://m.3g.oexnr.cn/nnews/55244.htm
- http://m.3g.oexnr.cn/nnews/339181.htm
- http://m.3g.oexnr.cn/nnews/11642.htm
- http://m.3g.oexnr.cn/nnews/4622.htm
- http://m.3g.oexnr.cn/nnews/1552.htm
- http://m.3g.oexnr.cn/nnews/7939386.htm
- http://m.3g.oexnr.cn/nnews/0546.htm
- http://m.3g.oexnr.cn/nnews/855534.htm
- http://m.3g.oexnr.cn/nnews/119518.htm
- http://m.3g.oexnr.cn/nnews/298001.htm
- http://m.3g.oexnr.cn/nnews/0466216.htm
- http://m.3g.oexnr.cn/nnews/7498.htm
- http://m.3g.oexnr.cn/nnews/05837.htm
- http://m.3g.oexnr.cn/nnews/4273721.htm
- http://m.3g.oexnr.cn/nnews/996074.htm
- http://m.3g.oexnr.cn/nnews/6909.htm
- http://m.3g.oexnr.cn/nnews/8226972.htm
- http://m.3g.oexnr.cn/nnews/3477.htm
- http://m.3g.oexnr.cn/nnews/41512.htm
- http://m.3g.oexnr.cn/nnews/574476.htm
- http://m.3g.oexnr.cn/nnews/289592.htm
- http://m.3g.oexnr.cn/nnews/39147.htm
- http://m.3g.oexnr.cn/nnews/08618.htm
- http://m.3g.oexnr.cn/nnews/2764.htm
- http://m.3g.oexnr.cn/nnews/7228382.htm
- http://m.3g.oexnr.cn/nnews/7089368.htm
- http://m.3g.oexnr.cn/nnews/2736354.htm
- http://m.3g.oexnr.cn/nnews/83055.htm
- http://m.3g.oexnr.cn/nnews/32482.htm
- http://m.3g.oexnr.cn/nnews/9502504.htm
- http://m.3g.oexnr.cn/nnews/8431.htm
- http://m.3g.oexnr.cn/nnews/0596391.htm
- http://m.3g.oexnr.cn/nnews/2724.htm
- http://m.3g.oexnr.cn/nnews/73848.htm
- http://m.3g.oexnr.cn/nnews/5547248.htm
- http://m.3g.oexnr.cn/nnews/16940.htm
- http://m.3g.oexnr.cn/nnews/62224.htm
- http://m.3g.oexnr.cn/nnews/4591326.htm
- http://m.3g.oexnr.cn/nnews/36762.htm
- http://m.3g.oexnr.cn/nnews/763002.htm
- http://m.3g.oexnr.cn/nnews/37816.htm
- http://m.3g.oexnr.cn/nnews/8209.htm
- http://m.3g.oexnr.cn/nnews/6857119.htm
- http://m.3g.oexnr.cn/nnews/56493.htm
- http://m.3g.oexnr.cn/nnews/5034652.htm
- http://m.3g.oexnr.cn/nnews/1932.htm
- http://m.3g.oexnr.cn/nnews/45637.htm
- http://m.3g.oexnr.cn/nnews/62678.htm
- http://m.3g.oexnr.cn/nnews/4061254.htm
- http://m.3g.oexnr.cn/nnews/292734.htm
- http://m.3g.oexnr.cn/nnews/0441813.htm
- http://m.3g.oexnr.cn/nnews/3881.htm
- http://m.3g.oexnr.cn/nnews/305369.htm
- http://m.3g.oexnr.cn/nnews/2265514.htm
- http://m.3g.oexnr.cn/nnews/3105371.htm
- http://m.3g.oexnr.cn/nnews/29595.htm
- http://m.3g.oexnr.cn/nnews/8877.htm
- http://m.3g.oexnr.cn/nnews/7961792.htm
- http://m.3g.oexnr.cn/nnews/17186.htm
- http://m.3g.oexnr.cn/nnews/808022.htm
- http://m.3g.oexnr.cn/nnews/36223.htm
- http://m.3g.oexnr.cn/nnews/978642.htm
- http://m.3g.oexnr.cn/nnews/575100.htm
- http://m.3g.oexnr.cn/nnews/252908.htm
- http://m.3g.oexnr.cn/nnews/8314.htm
- http://m.3g.oexnr.cn/nnews/629668.htm
- http://m.3g.oexnr.cn/nnews/194429.htm
- http://m.3g.oexnr.cn/nnews/0733702.htm
- http://m.3g.oexnr.cn/nnews/7395150.htm
- http://m.3g.oexnr.cn/nnews/94338.htm
- http://m.3g.oexnr.cn/nnews/663991.htm
- http://m.3g.oexnr.cn/nnews/139824.htm
- http://m.3g.oexnr.cn/nnews/17153.htm
- http://m.3g.oexnr.cn/nnews/8453.htm
- http://m.3g.oexnr.cn/nnews/27245.htm
- http://m.3g.oexnr.cn/nnews/586943.htm
- http://m.3g.oexnr.cn/nnews/8366636.htm
- http://m.3g.oexnr.cn/nnews/76516.htm
- http://m.3g.oexnr.cn/nnews/258097.htm
- http://m.3g.oexnr.cn/nnews/6695721.htm
- http://m.3g.oexnr.cn/nnews/016049.htm
- http://m.3g.oexnr.cn/nnews/19255.htm
- http://m.3g.oexnr.cn/nnews/9658650.htm
- http://m.3g.oexnr.cn/nnews/8984720.htm
- http://m.3g.oexnr.cn/nnews/9268743.htm
- http://m.3g.oexnr.cn/nnews/0928071.htm
- http://m.3g.oexnr.cn/nnews/21548.htm
- http://m.3g.oexnr.cn/nnews/80597.htm
- http://m.3g.oexnr.cn/nnews/2508200.htm
- http://m.3g.oexnr.cn/nnews/551925.htm
- http://m.3g.oexnr.cn/nnews/9081353.htm
- http://m.3g.oexnr.cn/nnews/3827.htm
- http://m.3g.oexnr.cn/nnews/7921467.htm
- http://m.3g.oexnr.cn/nnews/3141.htm
- http://m.3g.oexnr.cn/nnews/7372.htm
- http://m.3g.oexnr.cn/nnews/54908.htm
- http://m.3g.oexnr.cn/nnews/4993594.htm
- http://m.3g.oexnr.cn/nnews/4270.htm
- http://m.3g.oexnr.cn/nnews/253547.htm
- http://m.3g.oexnr.cn/nnews/5322.htm
- http://m.3g.oexnr.cn/nnews/18301.htm
- http://m.3g.oexnr.cn/nnews/2342755.htm
- http://m.3g.oexnr.cn/nnews/18733.htm
- http://m.3g.oexnr.cn/nnews/337585.htm
- http://m.3g.oexnr.cn/nnews/16427.htm
- http://m.3g.oexnr.cn/nnews/32912.htm
- http://m.3g.oexnr.cn/nnews/2239.htm
- http://m.3g.oexnr.cn/nnews/063893.htm
- http://m.3g.oexnr.cn/nnews/126563.htm
- http://m.3g.oexnr.cn/nnews/8142.htm
- http://m.3g.oexnr.cn/nnews/3821504.htm
- http://m.3g.oexnr.cn/nnews/9724.htm
- http://m.3g.oexnr.cn/nnews/2231.htm
- http://m.3g.oexnr.cn/nnews/04644.htm
- http://m.3g.oexnr.cn/nnews/359927.htm
- http://m.3g.oexnr.cn/nnews/52290.htm
- http://m.3g.oexnr.cn/nnews/4633.htm
- http://m.3g.oexnr.cn/nnews/1366024.htm
- http://m.3g.oexnr.cn/nnews/5960566.htm
- http://m.3g.oexnr.cn/nnews/9774127.htm
- http://m.3g.oexnr.cn/nnews/66987.htm
- http://m.3g.oexnr.cn/nnews/296299.htm
- http://m.3g.oexnr.cn/nnews/845869.htm
- http://m.3g.oexnr.cn/nnews/82130.htm
- http://m.3g.oexnr.cn/nnews/7193.htm
- http://m.3g.oexnr.cn/nnews/661865.htm
- http://m.3g.oexnr.cn/nnews/542788.htm
- http://m.3g.oexnr.cn/nnews/8081.htm
- http://m.3g.oexnr.cn/nnews/791186.htm
- http://m.3g.oexnr.cn/nnews/5724.htm
- http://m.3g.oexnr.cn/nnews/31539.htm
- http://m.3g.oexnr.cn/nnews/0603.htm
- http://m.3g.oexnr.cn/nnews/7616370.htm
- http://m.3g.oexnr.cn/nnews/57542.htm
- http://m.3g.oexnr.cn/nnews/85293.htm
- http://m.3g.oexnr.cn/nnews/2116191.htm
- http://m.3g.oexnr.cn/nnews/921372.htm
- http://m.3g.oexnr.cn/nnews/36107.htm
- http://m.3g.oexnr.cn/nnews/678902.htm
- http://m.3g.oexnr.cn/nnews/95398.htm
- http://m.3g.oexnr.cn/nnews/062676.htm
- http://m.3g.oexnr.cn/nnews/591961.htm
- http://m.3g.oexnr.cn/nnews/09937.htm
- http://m.3g.oexnr.cn/nnews/9145.htm
- http://m.3g.oexnr.cn/nnews/808256.htm
- http://m.3g.oexnr.cn/nnews/087312.htm
- http://m.3g.oexnr.cn/nnews/665642.htm
- http://m.3g.oexnr.cn/nnews/3313254.htm
- http://m.3g.oexnr.cn/nnews/6204.htm
- http://m.3g.oexnr.cn/nnews/5228764.htm
- http://m.3g.oexnr.cn/nnews/236657.htm
- http://m.3g.oexnr.cn/nnews/6158.htm
- http://m.3g.oexnr.cn/nnews/5039.htm
- http://m.3g.oexnr.cn/nnews/894046.htm
- http://m.3g.oexnr.cn/nnews/85900.htm
- http://m.3g.oexnr.cn/nnews/54746.htm
- http://m.3g.oexnr.cn/nnews/7016743.htm
- http://m.3g.oexnr.cn/nnews/516578.htm
- http://m.3g.oexnr.cn/nnews/0083767.htm
- http://m.3g.oexnr.cn/nnews/438429.htm
- http://m.3g.oexnr.cn/nnews/124204.htm
- http://m.3g.oexnr.cn/nnews/5690238.htm
- http://m.3g.oexnr.cn/nnews/15398.htm
- http://m.3g.oexnr.cn/nnews/21522.htm
- http://m.3g.oexnr.cn/nnews/4417.htm
- http://m.3g.oexnr.cn/nnews/40006.htm
- http://m.3g.oexnr.cn/nnews/372112.htm
- http://m.3g.oexnr.cn/nnews/8168035.htm
- http://m.3g.oexnr.cn/nnews/177221.htm
- http://m.3g.oexnr.cn/nnews/1895790.htm
- http://m.3g.oexnr.cn/nnews/90091.htm
- http://m.3g.oexnr.cn/nnews/4540162.htm
- http://m.3g.oexnr.cn/nnews/3443.htm
- http://m.3g.oexnr.cn/nnews/151077.htm
- http://m.3g.oexnr.cn/nnews/446758.htm
- http://m.3g.oexnr.cn/nnews/05564.htm
- http://m.3g.oexnr.cn/nnews/6327003.htm
- http://m.3g.oexnr.cn/nnews/949809.htm
- http://m.3g.oexnr.cn/nnews/695609.htm
- http://m.3g.oexnr.cn/nnews/969511.htm
- http://m.3g.oexnr.cn/nnews/7739072.htm
- http://m.3g.oexnr.cn/nnews/802723.htm
- http://m.3g.oexnr.cn/nnews/2095.htm
- http://m.3g.oexnr.cn/nnews/03188.htm
- http://m.3g.oexnr.cn/nnews/285889.htm
- http://m.3g.oexnr.cn/nnews/0129987.htm
- http://m.3g.oexnr.cn/nnews/77196.htm
- http://m.3g.oexnr.cn/nnews/7956.htm
- http://m.3g.oexnr.cn/nnews/660405.htm
- http://m.3g.oexnr.cn/nnews/7563065.htm
- http://m.3g.oexnr.cn/nnews/59591.htm
- http://m.3g.oexnr.cn/nnews/4832.htm
- http://m.3g.oexnr.cn/nnews/0120.htm
- http://m.3g.oexnr.cn/nnews/139750.htm
- http://m.3g.oexnr.cn/nnews/52224.htm
- http://m.3g.oexnr.cn/nnews/663885.htm
- http://m.3g.oexnr.cn/nnews/6662070.htm
- http://m.3g.oexnr.cn/nnews/180558.htm
- http://m.3g.oexnr.cn/nnews/5982797.htm
- http://m.3g.oexnr.cn/nnews/504709.htm
- http://m.3g.oexnr.cn/nnews/7035.htm
- http://m.3g.oexnr.cn/nnews/8881088.htm
- http://m.3g.oexnr.cn/nnews/781839.htm
- http://m.3g.oexnr.cn/nnews/5523.htm
- http://m.3g.oexnr.cn/nnews/02723.htm
- http://m.3g.oexnr.cn/nnews/922385.htm
- http://m.3g.oexnr.cn/nnews/7188000.htm
- http://m.3g.oexnr.cn/nnews/98956.htm
- http://m.3g.oexnr.cn/nnews/73406.htm
- http://m.3g.oexnr.cn/nnews/6412727.htm
- http://m.3g.oexnr.cn/nnews/530782.htm
- http://m.3g.oexnr.cn/nnews/7624.htm
- http://m.3g.oexnr.cn/nnews/0714.htm
- http://m.3g.oexnr.cn/nnews/73862.htm
- http://m.3g.oexnr.cn/nnews/652219.htm
- http://m.3g.oexnr.cn/nnews/77663.htm
- http://m.3g.oexnr.cn/nnews/0815397.htm
- http://m.3g.oexnr.cn/nnews/7054.htm
- http://m.3g.oexnr.cn/nnews/40992.htm
- http://m.3g.oexnr.cn/nnews/693416.htm
- http://m.3g.oexnr.cn/nnews/065562.htm
- http://m.3g.oexnr.cn/nnews/795584.htm
- http://m.3g.oexnr.cn/nnews/3031446.htm
- http://m.3g.oexnr.cn/nnews/72514.htm
- http://m.3g.oexnr.cn/nnews/1488.htm
- http://m.3g.oexnr.cn/nnews/1890.htm
- http://m.3g.oexnr.cn/nnews/7888646.htm
- http://m.3g.oexnr.cn/nnews/88277.htm
- http://m.3g.oexnr.cn/nnews/684868.htm
- http://m.3g.oexnr.cn/nnews/31663.htm
- http://m.3g.oexnr.cn/nnews/5990354.htm
- http://m.3g.oexnr.cn/nnews/95616.htm
- http://m.3g.oexnr.cn/nnews/8165714.htm
- http://m.3g.oexnr.cn/nnews/47143.htm
- http://m.3g.oexnr.cn/nnews/1732891.htm
- http://m.3g.oexnr.cn/nnews/522980.htm
- http://m.3g.oexnr.cn/nnews/0518.htm
- http://m.3g.oexnr.cn/nnews/8513.htm
- http://m.3g.oexnr.cn/nnews/1774.htm
- http://m.3g.oexnr.cn/nnews/55189.htm
- http://m.3g.oexnr.cn/nnews/0758.htm
- http://m.3g.oexnr.cn/nnews/9997.htm

## 项目结构

```
newslink-navigator/
├── app.py                         # Web 服务主入口，启动导航站和管理后台
├── requirements.txt               # Python 依赖清单
├── config/
│   ├── default.yaml               # 默认配置（端口、数据库路径、校验开关）
│   └── batch_11_mapping.yaml      # 第 11 批次的分类映射规则
├── data/
│   ├── batch_11_raw.txt           # 第 11 批次原始链接列表
│   ├── batch_11_parsed.json       # 解析后的结构化元数据
│   └── newslink.db                # SQLite 数据库文件（运行时生成）
├── scripts/
│   ├── batch_import.py            # 批次导入脚本，支持去重与校验
│   ├── dedup.py                   # 独立去重工具
│   └── export_html.py             # 导出静态导航页面的脚本
├── src/
│   ├── parser.py                  # 链接解析器，提取目录与文件名信息
│   ├── classifier.py              # 自动分类器，基于关键字与批次映射
│   ├── validator.py               # 链接可用性校验模块
│   └── storage.py                 # 数据库读写接口封装
├── templates/
│   ├── index.html                 # 导航首页模板
│   ├── category.html              # 分类浏览页模板
│   └── admin.html                 # 管理后台模板
├── static/
│   ├── css/                       # 样式文件目录
│   ├── js/                        # 前端交互脚本
│   └── assets/                    # 图标与静态资源
├── docs/                          # 完整文档目录（见文档导航章节）
└── tests/                         # 单元测试与集成测试用例
```

## 贡献指南

1. 查阅 issues 列表，选择未被认领的待办事项或提出新的改进建议。建议优先处理与批次导入性能优化、分类规则扩展相关的议题。

2. 克隆项目到本地并创建独立的功能分支，分支命名格式为 `feature/功能简述` 或 `fix/问题简述`，避免在主分支直接提交。

3. 编写或修改代码后，请确保在 `tests/` 目录下补充对应的单元测试用例，并运行 `pytest` 确认所有测试通过，同时保持代码风格符合 PEP8 规范。

4. 提交 commit 时使用清晰、规范的提交信息，格式为 `<类型>: <简短描述>`，例如 `feat: add support for custom tag filtering` 或 `docs: update batch_spec with new fields`。

5. 发起 Pull Request 至主仓库的 `develop` 分支，在 PR 描述中说明变更内容、测试覆盖情况以及是否影响现有批次数据兼容性。PR 需要至少一位项目维护者审核通过后方可合并。

## 常见问题

**问：导入批次时提示链接格式校验失败，如何解决？**

答：请检查原始列表是否包含非标准字符或空行。本项目严格接受每行一个 URL 的格式，且 URL 中不得包含空格或未转义的符号。若文件编码不是 UTF-8，也可能导致解析异常，建议使用 `iconv` 或文本编辑器将文件转换为 UTF-8 编码后再导入。如果问题持续，可使用 `scripts/dedup.py` 先清洗文件。

**问：如何自定义分类映射，使特定目录前缀的链接归入指定类别？**

答：您可以在 `config/batch_XX_mapping.yaml` 中编辑 `category_rules` 字段，规则采用正则表达式匹配目录路径。例如，若希望将所有 `/nnews/` 路径下的链接归入 "行业动态" 类别，可添加规则 `- pattern: '/nnews/.*' category: 'industry_news'`。修改后重新运行导入脚本即可。

**问：系统是否支持增量更新，即只添加新链接而不覆盖已有数据？**

答：支持。导入时使用 `--update-only` 参数，系统会比较当前批次与数据库中的现有记录，仅插入不存在的链接，并更新已有链接的访问时间戳。已删除的链接不会被自动移除，需手动使用 `--cleanup` 参数配合失效检测执行清理。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
