# WebLink Harvest 索引网关

WebLink Harvest 是一个面向技术调研、内容聚合与知识工程场景的轻量级外链索引网关。该项目定位于对分散在各类信息源中的原始链接进行统一采集、结构化登记与状态监控，帮助研究人员、运维工程师与内容策展人建立可维护的链接资产清单。项目本身不提供内容缓存或代理转发，仅对链接元数据与可达性进行周期性记录，适用于内部知识库前置处理、舆情素材暂存与第三方内容平台入口整理等场景。

## 功能概览

**批量链接导入** 支持以纯文本、CSV 或 JSON 格式一次性导入大量原始 URL，自动解析并提取域名、路径、查询参数等结构信息。

**元数据增强** 对每条链接自动补充协议类型、状态码预期、内容类型推断与最后访问时间戳，生成可用于过滤与排序的维度字段。

**可达性探活** 内置轻量级 HTTP 健康检查模块，支持配置超时与重试策略，定期对收录链接进行连通性测试并记录响应码与耗时。

**分类标签管理** 提供灵活的自定义标签体系，允许用户对链接按主题、来源、优先级或业务归属进行多维度标记与筛选。

**检索与过滤** 支持基于域名、路径关键字、标签组合、状态码与时间范围的联合查询，结果可导出为结构化表格或迁移脚本。

**导入导出适配** 输出格式兼容常见数据管道工具，支持 JSON Lines、Markdown 列表与纯文本地址簿三种导出形式，便于集成到下游系统。

## 应用场景

**技术博客与文档聚合** 团队内部可将分散在多个个人博客、官方文档与论坛中的参考链接统一收录，通过标签区分语言、框架与版本，方便新成员快速查阅相关上下文。

**舆情素材暂存管理** 内容运营人员对来自不同渠道的新闻页面与讨论帖进行链接登记，配合可达性监控及时发现失效来源，避免调研报告中出现大量死链。

**依赖项来源追溯** 在开源组件审计过程中，将项目依赖的各类仓库、镜像站与补丁公告链接集中记录，形成可核查的供应链信息台账，降低追踪成本。

**数据管道前置清洗** 数据工程师在采集流程前使用本系统对候选 URL 列表进行格式校验与去重，过滤明显无效或重复的条目，提升后续抓取任务的执行效率。

## 快速开始

以下命令演示了从克隆仓库到启动本地服务的完整流程。

```bash
git clone https://github.com/weblink-harvest/weblink-harvest.git
cd weblink-harvest
pip install -r requirements.txt
python scripts/init_db.py
python app.py --port 8080
```

服务启动后，可通过 HTTP 接口或命令行工具导入链接列表。默认使用 SQLite 作为后端存储，数据文件位于 `data/weblink.db`。首次运行时会自动创建所需表结构与索引。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 至 3.11 | 核心运行时环境，低于 3.9 将无法解析类型注解 |
| SQLite | 3.31 及以上 | 内嵌数据库引擎，用于存储链接元数据与标签关系 |
| requests | 2.28.0 及以上 | 执行 HTTP 探活请求，处理重定向与超时 |
| pydantic | 1.10.0 及以上 | 数据校验与配置管理，用于接口参数与模型定义 |
| click | 8.1.0 及以上 | 命令行交互框架，提供子命令与参数解析 |
| pytest | 7.2.0 及以上 | 单元测试与集成测试执行器，仅在开发环境中需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何导入链接、添加标签、执行健康检查与导出结果 |
| 接口参考 | docs/api-reference.md | HTTP 端点定义、请求参数格式、响应结构及错误码说明 |
| 运维指南 | docs/operations.md | 数据库迁移、日志配置、性能调优与定期清理策略 |
| 设计说明 | docs/design.md | 整体架构、模块划分、数据模型与扩展点设计思路 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/5084.htm
- http://m.3g.bwbkj.cn/jnews/9937102.htm
- http://m.3g.bwbkj.cn/jnews/9168.htm
- http://m.3g.bwbkj.cn/jnews/25259.htm
- http://m.3g.bwbkj.cn/jnews/905732.htm
- http://m.3g.bwbkj.cn/jnews/409991.htm
- http://m.3g.bwbkj.cn/jnews/4133086.htm
- http://m.3g.bwbkj.cn/jnews/6400167.htm
- http://m.3g.bwbkj.cn/jnews/04657.htm
- http://m.3g.bwbkj.cn/jnews/40763.htm
- http://m.3g.bwbkj.cn/jnews/14568.htm
- http://m.3g.bwbkj.cn/jnews/1030678.htm
- http://m.3g.bwbkj.cn/jnews/21029.htm
- http://m.3g.bwbkj.cn/jnews/302033.htm
- http://m.3g.bwbkj.cn/jnews/2183341.htm
- http://m.3g.bwbkj.cn/jnews/281643.htm
- http://m.3g.bwbkj.cn/jnews/76092.htm
- http://m.3g.bwbkj.cn/jnews/624085.htm
- http://m.3g.bwbkj.cn/jnews/340199.htm
- http://m.3g.bwbkj.cn/jnews/839528.htm
- http://m.3g.bwbkj.cn/jnews/0670867.htm
- http://m.3g.bwbkj.cn/jnews/1590498.htm
- http://m.3g.bwbkj.cn/jnews/6277.htm
- http://m.3g.bwbkj.cn/jnews/7712751.htm
- http://m.3g.bwbkj.cn/jnews/97337.htm
- http://m.3g.bwbkj.cn/jnews/9518322.htm
- http://m.3g.bwbkj.cn/jnews/180778.htm
- http://m.3g.bwbkj.cn/jnews/978615.htm
- http://m.3g.bwbkj.cn/jnews/6577700.htm
- http://m.3g.bwbkj.cn/jnews/11782.htm
- http://m.3g.bwbkj.cn/jnews/2731467.htm
- http://m.3g.bwbkj.cn/jnews/002235.htm
- http://m.3g.bwbkj.cn/jnews/5962674.htm
- http://m.3g.bwbkj.cn/jnews/914562.htm
- http://m.3g.bwbkj.cn/jnews/2647811.htm
- http://m.3g.bwbkj.cn/jnews/21043.htm
- http://m.3g.bwbkj.cn/jnews/1666.htm
- http://m.3g.bwbkj.cn/jnews/322698.htm
- http://m.3g.bwbkj.cn/jnews/05261.htm
- http://m.3g.bwbkj.cn/jnews/8954389.htm
- http://m.3g.bwbkj.cn/jnews/2585.htm
- http://m.3g.bwbkj.cn/jnews/51977.htm
- http://m.3g.bwbkj.cn/jnews/647242.htm
- http://m.3g.bwbkj.cn/jnews/6349962.htm
- http://m.3g.bwbkj.cn/jnews/322721.htm
- http://m.3g.bwbkj.cn/jnews/2336.htm
- http://m.3g.bwbkj.cn/jnews/730049.htm
- http://m.3g.bwbkj.cn/jnews/540796.htm
- http://m.3g.bwbkj.cn/jnews/795918.htm
- http://m.3g.bwbkj.cn/jnews/557739.htm
- http://m.3g.bwbkj.cn/jnews/453346.htm
- http://m.3g.bwbkj.cn/jnews/762524.htm
- http://m.3g.bwbkj.cn/jnews/7999843.htm
- http://m.3g.bwbkj.cn/jnews/06213.htm
- http://m.3g.bwbkj.cn/jnews/8517501.htm
- http://m.3g.bwbkj.cn/jnews/201452.htm
- http://m.3g.bwbkj.cn/jnews/73462.htm
- http://m.3g.bwbkj.cn/jnews/206290.htm
- http://m.3g.bwbkj.cn/jnews/45312.htm
- http://m.3g.bwbkj.cn/jnews/171598.htm
- http://m.3g.bwbkj.cn/jnews/6729020.htm
- http://m.3g.bwbkj.cn/jnews/5504.htm
- http://m.3g.bwbkj.cn/jnews/0313.htm
- http://m.3g.bwbkj.cn/jnews/3879921.htm
- http://m.3g.bwbkj.cn/jnews/742592.htm
- http://m.3g.bwbkj.cn/jnews/87738.htm
- http://m.3g.bwbkj.cn/jnews/254878.htm
- http://m.3g.bwbkj.cn/jnews/8868684.htm
- http://m.3g.bwbkj.cn/jnews/925630.htm
- http://m.3g.bwbkj.cn/jnews/0268354.htm
- http://m.3g.bwbkj.cn/jnews/1881.htm
- http://m.3g.bwbkj.cn/jnews/2833688.htm
- http://m.3g.bwbkj.cn/jnews/752757.htm
- http://m.3g.bwbkj.cn/jnews/84804.htm
- http://m.3g.bwbkj.cn/jnews/3069058.htm
- http://m.3g.bwbkj.cn/jnews/327554.htm
- http://m.3g.bwbkj.cn/jnews/9385.htm
- http://m.3g.bwbkj.cn/jnews/208514.htm
- http://m.3g.bwbkj.cn/jnews/78380.htm
- http://m.3g.bwbkj.cn/jnews/4545.htm
- http://m.3g.bwbkj.cn/jnews/22661.htm
- http://m.3g.bwbkj.cn/jnews/680648.htm
- http://m.3g.bwbkj.cn/jnews/26224.htm
- http://m.3g.bwbkj.cn/jnews/16464.htm
- http://m.3g.bwbkj.cn/jnews/98881.htm
- http://m.3g.bwbkj.cn/jnews/9630.htm
- http://m.3g.bwbkj.cn/jnews/218520.htm
- http://m.3g.bwbkj.cn/jnews/472083.htm
- http://m.3g.bwbkj.cn/jnews/71191.htm
- http://m.3g.bwbkj.cn/jnews/113320.htm
- http://m.3g.bwbkj.cn/jnews/522443.htm
- http://m.3g.bwbkj.cn/jnews/3621855.htm
- http://m.3g.bwbkj.cn/jnews/55846.htm
- http://m.3g.bwbkj.cn/jnews/257994.htm
- http://m.3g.bwbkj.cn/jnews/2182.htm
- http://m.3g.bwbkj.cn/jnews/8971.htm
- http://m.3g.bwbkj.cn/jnews/7896.htm
- http://m.3g.bwbkj.cn/jnews/271353.htm
- http://m.3g.bwbkj.cn/jnews/611337.htm
- http://m.3g.bwbkj.cn/jnews/3989.htm
- http://m.3g.bwbkj.cn/jnews/21347.htm
- http://m.3g.bwbkj.cn/jnews/1674.htm
- http://m.3g.bwbkj.cn/jnews/8064782.htm
- http://m.3g.bwbkj.cn/jnews/3036.htm
- http://m.3g.bwbkj.cn/jnews/86628.htm
- http://m.3g.bwbkj.cn/jnews/9944943.htm
- http://m.3g.bwbkj.cn/jnews/207515.htm
- http://m.3g.bwbkj.cn/jnews/023174.htm
- http://m.3g.bwbkj.cn/jnews/6112642.htm
- http://m.3g.bwbkj.cn/jnews/8886749.htm
- http://m.3g.bwbkj.cn/jnews/45500.htm
- http://m.3g.bwbkj.cn/jnews/0732.htm
- http://m.3g.bwbkj.cn/jnews/4046490.htm
- http://m.3g.bwbkj.cn/jnews/3930.htm
- http://m.3g.bwbkj.cn/jnews/9968.htm
- http://m.3g.bwbkj.cn/jnews/82605.htm
- http://m.3g.bwbkj.cn/jnews/17598.htm
- http://m.3g.bwbkj.cn/jnews/7423.htm
- http://m.3g.bwbkj.cn/jnews/2642.htm
- http://m.3g.bwbkj.cn/jnews/8461.htm
- http://m.3g.bwbkj.cn/jnews/0153452.htm
- http://m.3g.bwbkj.cn/jnews/3806.htm
- http://m.3g.bwbkj.cn/jnews/15040.htm
- http://m.3g.bwbkj.cn/jnews/12901.htm
- http://m.3g.bwbkj.cn/jnews/5225261.htm
- http://m.3g.bwbkj.cn/jnews/164874.htm
- http://m.3g.bwbkj.cn/jnews/5381.htm
- http://m.3g.bwbkj.cn/jnews/21305.htm
- http://m.3g.bwbkj.cn/jnews/84916.htm
- http://m.3g.bwbkj.cn/jnews/0983.htm
- http://m.3g.bwbkj.cn/jnews/0606.htm
- http://m.3g.bwbkj.cn/jnews/002649.htm
- http://m.3g.bwbkj.cn/jnews/1871054.htm
- http://m.3g.bwbkj.cn/jnews/2766844.htm
- http://m.3g.bwbkj.cn/jnews/9877876.htm
- http://m.3g.bwbkj.cn/jnews/5444.htm
- http://m.3g.bwbkj.cn/jnews/066744.htm
- http://m.3g.bwbkj.cn/jnews/58373.htm
- http://m.3g.bwbkj.cn/jnews/1421209.htm
- http://m.3g.bwbkj.cn/jnews/3056901.htm
- http://m.3g.bwbkj.cn/jnews/7537825.htm
- http://m.3g.bwbkj.cn/jnews/507801.htm
- http://m.3g.bwbkj.cn/jnews/71612.htm
- http://m.3g.bwbkj.cn/jnews/725010.htm
- http://m.3g.bwbkj.cn/jnews/74278.htm
- http://m.3g.bwbkj.cn/jnews/371115.htm
- http://m.3g.bwbkj.cn/jnews/1249.htm
- http://m.3g.bwbkj.cn/jnews/0323677.htm
- http://m.3g.bwbkj.cn/jnews/920715.htm
- http://m.3g.bwbkj.cn/jnews/28914.htm
- http://m.3g.bwbkj.cn/jnews/7602.htm
- http://m.3g.bwbkj.cn/jnews/74954.htm
- http://m.3g.bwbkj.cn/jnews/3712471.htm
- http://m.3g.bwbkj.cn/jnews/5204447.htm
- http://m.3g.bwbkj.cn/jnews/46453.htm
- http://m.3g.bwbkj.cn/jnews/1278944.htm
- http://m.3g.bwbkj.cn/jnews/1734682.htm
- http://m.3g.bwbkj.cn/jnews/0714814.htm
- http://m.3g.bwbkj.cn/jnews/0793.htm
- http://m.3g.bwbkj.cn/jnews/230551.htm
- http://m.3g.bwbkj.cn/jnews/9164991.htm
- http://m.3g.bwbkj.cn/jnews/1390777.htm
- http://m.3g.bwbkj.cn/jnews/206666.htm
- http://m.3g.bwbkj.cn/jnews/5052.htm
- http://m.3g.bwbkj.cn/jnews/9236.htm
- http://m.3g.bwbkj.cn/jnews/947481.htm
- http://m.3g.bwbkj.cn/jnews/613327.htm
- http://m.3g.bwbkj.cn/jnews/96798.htm
- http://m.3g.bwbkj.cn/jnews/3734332.htm
- http://m.3g.bwbkj.cn/jnews/745706.htm
- http://m.3g.bwbkj.cn/jnews/1213214.htm
- http://m.3g.bwbkj.cn/jnews/42988.htm
- http://m.3g.bwbkj.cn/jnews/925695.htm
- http://m.3g.bwbkj.cn/jnews/261159.htm
- http://m.3g.bwbkj.cn/jnews/849496.htm
- http://m.3g.bwbkj.cn/jnews/75706.htm
- http://m.3g.bwbkj.cn/jnews/4774.htm
- http://m.3g.bwbkj.cn/jnews/39687.htm
- http://m.3g.bwbkj.cn/jnews/161726.htm
- http://m.3g.bwbkj.cn/jnews/612655.htm
- http://m.3g.bwbkj.cn/jnews/3764.htm
- http://m.3g.bwbkj.cn/jnews/8845704.htm
- http://m.3g.bwbkj.cn/jnews/4489.htm
- http://m.3g.bwbkj.cn/jnews/6908536.htm
- http://m.3g.bwbkj.cn/jnews/64181.htm
- http://m.3g.bwbkj.cn/jnews/2906.htm
- http://m.3g.bwbkj.cn/jnews/8612.htm
- http://m.3g.bwbkj.cn/jnews/457524.htm
- http://m.3g.bwbkj.cn/jnews/3698745.htm
- http://m.3g.bwbkj.cn/jnews/2389.htm
- http://m.3g.bwbkj.cn/jnews/846443.htm
- http://m.3g.bwbkj.cn/jnews/9731158.htm
- http://m.3g.bwbkj.cn/jnews/4567.htm
- http://m.3g.bwbkj.cn/jnews/258347.htm
- http://m.3g.bwbkj.cn/jnews/52424.htm
- http://m.3g.bwbkj.cn/jnews/125337.htm
- http://m.3g.bwbkj.cn/jnews/2540286.htm
- http://m.3g.bwbkj.cn/jnews/9106407.htm
- http://m.3g.bwbkj.cn/jnews/79220.htm
- http://m.3g.bwbkj.cn/jnews/210194.htm
- http://m.3g.bwbkj.cn/jnews/1578.htm
- http://m.3g.bwbkj.cn/jnews/933707.htm
- http://m.3g.bwbkj.cn/jnews/182510.htm
- http://m.3g.bwbkj.cn/jnews/0811136.htm
- http://m.3g.bwbkj.cn/jnews/6462495.htm
- http://m.3g.bwbkj.cn/jnews/443526.htm
- http://m.3g.bwbkj.cn/jnews/366005.htm
- http://m.3g.bwbkj.cn/jnews/4608381.htm
- http://m.3g.bwbkj.cn/jnews/075497.htm
- http://m.3g.bwbkj.cn/jnews/0877.htm
- http://m.3g.bwbkj.cn/jnews/96048.htm
- http://m.3g.bwbkj.cn/jnews/6525.htm
- http://m.3g.bwbkj.cn/jnews/8517553.htm
- http://m.3g.bwbkj.cn/jnews/3347085.htm
- http://m.3g.bwbkj.cn/jnews/849452.htm
- http://m.3g.bwbkj.cn/jnews/1982883.htm
- http://m.3g.bwbkj.cn/jnews/1701.htm
- http://m.3g.bwbkj.cn/jnews/772503.htm
- http://m.3g.bwbkj.cn/jnews/4755.htm
- http://m.3g.bwbkj.cn/jnews/516080.htm
- http://m.3g.bwbkj.cn/jnews/691351.htm
- http://m.3g.bwbkj.cn/jnews/1201159.htm
- http://m.3g.bwbkj.cn/jnews/8400.htm
- http://m.3g.bwbkj.cn/jnews/87964.htm
- http://m.3g.bwbkj.cn/jnews/3255340.htm
- http://m.3g.bwbkj.cn/jnews/9837.htm
- http://m.3g.bwbkj.cn/jnews/696576.htm
- http://m.3g.bwbkj.cn/jnews/84001.htm
- http://m.3g.bwbkj.cn/jnews/24406.htm
- http://m.3g.bwbkj.cn/jnews/9511.htm
- http://m.3g.bwbkj.cn/jnews/1116137.htm
- http://m.3g.bwbkj.cn/jnews/73299.htm
- http://m.3g.bwbkj.cn/jnews/116949.htm
- http://m.3g.bwbkj.cn/jnews/55244.htm
- http://m.3g.bwbkj.cn/jnews/551541.htm
- http://m.3g.bwbkj.cn/jnews/8057.htm
- http://m.3g.bwbkj.cn/jnews/8310341.htm
- http://m.3g.bwbkj.cn/jnews/8072093.htm
- http://m.3g.bwbkj.cn/jnews/412014.htm
- http://m.3g.bwbkj.cn/jnews/6310492.htm
- http://m.3g.bwbkj.cn/jnews/3225521.htm
- http://m.3g.bwbkj.cn/jnews/7125590.htm
- http://m.3g.bwbkj.cn/jnews/86172.htm
- http://m.3g.bwbkj.cn/jnews/1481715.htm
- http://m.3g.bwbkj.cn/jnews/2634707.htm
- http://m.3g.bwbkj.cn/jnews/58092.htm
- http://m.3g.bwbkj.cn/jnews/9335750.htm
- http://m.3g.bwbkj.cn/jnews/2648.htm
- http://m.3g.bwbkj.cn/jnews/8380.htm
- http://m.3g.bwbkj.cn/jnews/36292.htm
- http://m.3g.bwbkj.cn/jnews/679959.htm
- http://m.3g.bwbkj.cn/jnews/6859.htm
- http://m.3g.bwbkj.cn/jnews/7590.htm
- http://m.3g.bwbkj.cn/jnews/04567.htm
- http://m.3g.bwbkj.cn/jnews/1821069.htm
- http://m.3g.bwbkj.cn/jnews/85714.htm
- http://m.3g.bwbkj.cn/jnews/7434901.htm
- http://m.3g.bwbkj.cn/jnews/06405.htm
- http://m.3g.bwbkj.cn/jnews/779070.htm
- http://m.3g.bwbkj.cn/jnews/1295.htm
- http://m.3g.bwbkj.cn/jnews/722254.htm
- http://m.3g.bwbkj.cn/jnews/350265.htm
- http://m.3g.bwbkj.cn/jnews/6471741.htm
- http://m.3g.bwbkj.cn/jnews/87126.htm
- http://m.3g.bwbkj.cn/jnews/1419.htm
- http://m.3g.bwbkj.cn/jnews/46633.htm
- http://m.3g.bwbkj.cn/jnews/2597.htm
- http://m.3g.bwbkj.cn/jnews/01809.htm
- http://m.3g.bwbkj.cn/jnews/4607.htm
- http://m.3g.bwbkj.cn/jnews/26870.htm
- http://m.3g.bwbkj.cn/jnews/910395.htm
- http://m.3g.bwbkj.cn/jnews/359224.htm
- http://m.3g.bwbkj.cn/jnews/68627.htm
- http://m.3g.bwbkj.cn/jnews/9628438.htm
- http://m.3g.bwbkj.cn/jnews/130716.htm
- http://m.3g.bwbkj.cn/jnews/3167824.htm
- http://m.3g.bwbkj.cn/jnews/655708.htm
- http://m.3g.bwbkj.cn/jnews/4448354.htm
- http://m.3g.bwbkj.cn/jnews/33827.htm
- http://m.3g.bwbkj.cn/jnews/9604.htm
- http://m.3g.bwbkj.cn/jnews/1021.htm
- http://m.3g.bwbkj.cn/jnews/5767.htm
- http://m.3g.bwbkj.cn/jnews/10019.htm
- http://m.3g.bwbkj.cn/jnews/2157.htm
- http://m.3g.bwbkj.cn/jnews/0510.htm
- http://m.3g.bwbkj.cn/jnews/15806.htm
- http://m.3g.bwbkj.cn/jnews/2813759.htm
- http://m.3g.bwbkj.cn/jnews/074169.htm
- http://m.3g.bwbkj.cn/jnews/43770.htm
- http://m.3g.bwbkj.cn/jnews/6215693.htm
- http://m.3g.bwbkj.cn/jnews/06517.htm
- http://m.3g.bwbkj.cn/jnews/021764.htm
- http://m.3g.bwbkj.cn/jnews/621277.htm
- http://m.3g.bwbkj.cn/jnews/2628680.htm
- http://m.3g.bwbkj.cn/jnews/14459.htm
- http://m.3g.bwbkj.cn/jnews/73548.htm
- http://m.3g.bwbkj.cn/jnews/2703928.htm
- http://m.3g.bwbkj.cn/jnews/76612.htm
- http://m.3g.bwbkj.cn/jnews/41215.htm
- http://m.3g.bwbkj.cn/jnews/35617.htm

## 项目结构

```
weblink-harvest/
├── app.py                         # 主入口，启动 HTTP 服务与调度探活任务
├── config/
│   ├── settings.py                # 环境变量解析、默认超时与重试参数
│   └── logging.yaml               # 日志级别与输出格式配置
├── core/
│   ├── models.py                  # Link 与 Tag 数据模型定义，包含 Pydantic 校验
│   ├── parser.py                  # URL 解析与规范化工具，处理编码与片段剥离
│   └── probe.py                   # 异步 HTTP 探活器，支持并发与熔断
├── storage/
│   ├── db.py                      # SQLite 连接池与原始 SQL 操作封装
│   ├── migrations/                # 版本化 schema 变更脚本
│   │   ├── 001_initial.sql
│   │   └── 002_add_indexes.sql
│   └── repository.py              # 链接与标签的 CRUD 聚合方法
├── api/
│   ├── routes.py                  # Flask 路由注册，定义 /import、/search、/health 等端点
│   └── schemas.py                 # 请求与响应 JSON 结构声明
├── cli/
│   ├── main.py                    # Click 命令组入口，支持 import、check、export 子命令
│   └── formatters.py              # 控制台表格输出与颜色高亮辅助
├── scripts/
│   ├── init_db.py                 # 首次运行创建表结构与默认标签
│   └── sample_import.json         # 用于快速测试的示例链接数据集
├── tests/
│   ├── unit/                      # 单测覆盖解析、探活与存储层
│   └── integration/               # 端到端测试依赖临时数据库与模拟网络
├── docs/                          # 文档目录，含用户手册与运维指南
├── requirements.txt               # 生产环境依赖列表
├── requirements-dev.txt           # 开发测试额外依赖
└── README.md                      # 项目概述与快速指引
```

## 贡献指南

1. 阅读设计说明文档 docs/design.md 与接口参考 docs/api-reference.md，了解整体架构与模块边界，避免重复实现或破坏既有约定。

2. 在 GitHub 仓库中提交 Issue 说明拟解决的问题或新增功能，等待维护者确认需求范围后再开始编码，以减少无效 PR。

3. 编写代码时遵循项目既定的命名规范与类型注解风格，新增或修改功能须同步更新对应的单元测试与集成测试用例。

4. 提交 Pull Request 前确保所有测试通过，并在 PR 描述中引用相关 Issue 编号，同时说明改动点与可能影响面。

5. 文档类改动（包括 README、用户手册与 API 示例）应与代码改动同等对待，保持中英文术语一致，避免过时信息。

## 常见问题

**Q：探活检查会对目标服务器造成压力吗？**

默认配置下，探活模块使用 5 秒超时与 2 次重试，并发数限制为 10 个连接。单次全量扫描间隔为 24 小时，且仅发送 HEAD 请求（若服务器支持），不会拉取完整响应体。对于敏感或高负载来源，可通过配置跳过探活或调整并发与间隔参数。

**Q：如何迁移已有链接数据到新版本？**

项目在 storage/migrations 目录下提供版本化增量脚本。升级前请备份 data/weblink.db 文件，然后执行 python scripts/migrate.py --target latest。迁移过程会自动应用未执行的变更，不会删除现有字段或表。如需回滚，可使用 --rollback 参数指定目标版本号。

**Q：能否与外部监控系统集成？**

可以。探活结果会写入本地数据库，同时支持通过 Webhook 配置将状态变更实时推送到第三方系统。详细配置方式参见 docs/operations.md 中的报警与集成章节，支持自定义回调 URL 与请求模板。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:02
