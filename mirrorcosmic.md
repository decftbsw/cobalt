# NewsLink Archive

NewsLink Archive 是一个面向技术内容聚合与长期外链管理的开源新闻链接归档系统。该项目定位为技术团队、内容运营者与数据研究者的轻量化外链资源池，用于对大量散落的 `.htm` 新闻链接进行结构化存储、分类索引与快速检索。NewsLink Archive 不提供爬虫与采集功能，而是专注于已获取链接的元数据增强、标签化组织与多维度筛选，解决信息过载时代下外链资源“存得下、找得到、可复用”的核心痛点。

## 功能概览

**批量链接导入与去重校验**：支持通过文本文件或标准输入流一次性导入大量 `.htm` 格式链接，系统自动校验 URL 协议合规性、域名合法性并剔除重复条目。

**智能元数据提取与补全**：基于链接路径中的数字ID自动生成时间戳索引，并允许用户通过自定义规则批量补充来源、分类与优先级标签。

**多级标签分类体系**：内置灵活的分类树结构，用户可创建、编辑、删除分类节点，并为每个链接分配一个或多个分类标签，实现精细化资源管理。

**全文检索与高级筛选**：提供基于链接ID、文件名关键词、导入批次、时间范围的组合查询接口，支持正则表达式匹配与模糊搜索。

**批次管理视图**：针对第 12/300 批等批量导入场景提供独立的批次概览面板，展示批次内链接总数、已标记数量、分类分布统计等核心指标。

**数据导出与快照备份**：支持将当前归档数据导出为 JSON、CSV 或纯文本链接清单格式，便于与其他数据处理工具集成，同时提供定时快照备份机制。

**RESTful API 接口**：提供标准 HTTP API 用于第三方系统集成，支持链接查询、分类更新、批量删除等操作，返回格式为 JSON。

## 应用场景

内容运营团队定期归档合作媒体发布的新闻链接，通过 NewsLink Archive 按主题分类并添加内部备注，方便后续编辑稿件时快速引用相关来源。

技术研究人员收集特定行业的外部新闻链接用于趋势分析，利用批次管理功能按采集时间分组，并结合高级筛选接口提取特定ID范围的链接进行统计建模。

开源项目文档站点需要维护一份“相关资源”外部链接清单，维护者使用本系统管理这些链接的生命周期，定期检查链接有效性并更新分类标签，保证对外文档的准确性与时效性。

个人开发者整理日常阅读的新闻简报链接，利用标签体系区分“技术前沿”、“行业动态”、“开源社区”等维度，构建个人知识检索库，避免链接散落在浏览器书签中无法有效复用。

## 快速开始

以下指令演示如何克隆项目仓库、安装依赖并启动开发服务。

```bash
git clone https://github.com/your-organization/newslink-archive.git
cd newslink-archive
npm install
npm run dev
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或 20.x LTS | 运行时环境，建议使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，用于安装项目依赖 |
| SQLite3 | 3.40 以上 | 嵌入式数据库，用于存储链接元数据与分类关系 |
| TypeScript | 5.0 以上 | 开发时依赖，用于类型检查与编译 |
| Git | 2.30 以上 | 版本控制工具，用于克隆与提交变更 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 入门指南 | docs/getting-started.md | 如何快速部署开发环境并导入第一批链接？ |
| 操作手册 | docs/user-guide.md | 链接导入、分类管理、检索导出等日常操作如何执行？ |
| API 参考 | docs/api-reference.md | RESTful API 的端点列表、请求参数与响应格式是什么？ |
| 批次管理 | docs/batch-management.md | 如何创建新批次、查看批次状态并进行批次内数据分析？ |

## 资源列表

- http://m.3g.oexnr.cn/nnews/3633359.htm
- http://m.3g.oexnr.cn/nnews/4053.htm
- http://m.3g.oexnr.cn/nnews/5126.htm
- http://m.3g.oexnr.cn/nnews/78268.htm
- http://m.3g.oexnr.cn/nnews/451294.htm
- http://m.3g.oexnr.cn/nnews/474934.htm
- http://m.3g.oexnr.cn/nnews/706598.htm
- http://m.3g.oexnr.cn/nnews/7874.htm
- http://m.3g.oexnr.cn/nnews/5544.htm
- http://m.3g.oexnr.cn/nnews/4980.htm
- http://m.3g.oexnr.cn/nnews/637079.htm
- http://m.3g.oexnr.cn/nnews/541397.htm
- http://m.3g.oexnr.cn/nnews/55787.htm
- http://m.3g.oexnr.cn/nnews/000582.htm
- http://m.3g.oexnr.cn/nnews/7165176.htm
- http://m.3g.oexnr.cn/nnews/460834.htm
- http://m.3g.oexnr.cn/nnews/584987.htm
- http://m.3g.oexnr.cn/nnews/30537.htm
- http://m.3g.oexnr.cn/nnews/8845.htm
- http://m.3g.oexnr.cn/nnews/1809966.htm
- http://m.3g.oexnr.cn/nnews/2806661.htm
- http://m.3g.oexnr.cn/nnews/55821.htm
- http://m.3g.oexnr.cn/nnews/343074.htm
- http://m.3g.oexnr.cn/nnews/3686.htm
- http://m.3g.oexnr.cn/nnews/5347777.htm
- http://m.3g.oexnr.cn/nnews/8874559.htm
- http://m.3g.oexnr.cn/nnews/99034.htm
- http://m.3g.oexnr.cn/nnews/18399.htm
- http://m.3g.oexnr.cn/nnews/566313.htm
- http://m.3g.oexnr.cn/nnews/891982.htm
- http://m.3g.oexnr.cn/nnews/4286.htm
- http://m.3g.oexnr.cn/nnews/5251585.htm
- http://m.3g.oexnr.cn/nnews/85163.htm
- http://m.3g.oexnr.cn/nnews/0437396.htm
- http://m.3g.oexnr.cn/nnews/05410.htm
- http://m.3g.oexnr.cn/nnews/963462.htm
- http://m.3g.oexnr.cn/nnews/039203.htm
- http://m.3g.oexnr.cn/nnews/81460.htm
- http://m.3g.oexnr.cn/nnews/6758.htm
- http://m.3g.oexnr.cn/nnews/4439628.htm
- http://m.3g.oexnr.cn/nnews/05354.htm
- http://m.3g.oexnr.cn/nnews/28183.htm
- http://m.3g.oexnr.cn/nnews/404796.htm
- http://m.3g.oexnr.cn/nnews/29688.htm
- http://m.3g.oexnr.cn/nnews/814084.htm
- http://m.3g.oexnr.cn/nnews/1871772.htm
- http://m.3g.oexnr.cn/nnews/2527866.htm
- http://m.3g.oexnr.cn/nnews/2614.htm
- http://m.3g.oexnr.cn/nnews/2528158.htm
- http://m.3g.oexnr.cn/nnews/168549.htm
- http://m.3g.oexnr.cn/nnews/3545.htm
- http://m.3g.oexnr.cn/nnews/7440649.htm
- http://m.3g.oexnr.cn/nnews/34361.htm
- http://m.3g.oexnr.cn/nnews/8702112.htm
- http://m.3g.oexnr.cn/nnews/3700.htm
- http://m.3g.oexnr.cn/nnews/490873.htm
- http://m.3g.oexnr.cn/nnews/3272318.htm
- http://m.3g.oexnr.cn/nnews/9939864.htm
- http://m.3g.oexnr.cn/nnews/5578722.htm
- http://m.3g.oexnr.cn/nnews/317963.htm
- http://m.3g.oexnr.cn/nnews/6866822.htm
- http://m.3g.oexnr.cn/nnews/832212.htm
- http://m.3g.oexnr.cn/nnews/63421.htm
- http://m.3g.oexnr.cn/nnews/140962.htm
- http://m.3g.oexnr.cn/nnews/464915.htm
- http://m.3g.oexnr.cn/nnews/0392176.htm
- http://m.3g.oexnr.cn/nnews/6623.htm
- http://m.3g.oexnr.cn/nnews/39497.htm
- http://m.3g.oexnr.cn/nnews/27652.htm
- http://m.3g.oexnr.cn/nnews/7507.htm
- http://m.3g.oexnr.cn/nnews/59387.htm
- http://m.3g.oexnr.cn/nnews/357219.htm
- http://m.3g.oexnr.cn/nnews/7452068.htm
- http://m.3g.oexnr.cn/nnews/5048.htm
- http://m.3g.oexnr.cn/nnews/959578.htm
- http://m.3g.oexnr.cn/nnews/35793.htm
- http://m.3g.oexnr.cn/nnews/5508.htm
- http://m.3g.oexnr.cn/nnews/01009.htm
- http://m.3g.oexnr.cn/nnews/91828.htm
- http://m.3g.oexnr.cn/nnews/0009.htm
- http://m.3g.oexnr.cn/nnews/2882.htm
- http://m.3g.oexnr.cn/nnews/7582361.htm
- http://m.3g.oexnr.cn/nnews/576815.htm
- http://m.3g.oexnr.cn/nnews/8548999.htm
- http://m.3g.oexnr.cn/nnews/448692.htm
- http://m.3g.oexnr.cn/nnews/804188.htm
- http://m.3g.oexnr.cn/nnews/453038.htm
- http://m.3g.oexnr.cn/nnews/0859.htm
- http://m.3g.oexnr.cn/nnews/308158.htm
- http://m.3g.oexnr.cn/nnews/650012.htm
- http://m.3g.oexnr.cn/nnews/2736.htm
- http://m.3g.oexnr.cn/nnews/6149987.htm
- http://m.3g.oexnr.cn/nnews/6871.htm
- http://m.3g.oexnr.cn/nnews/18905.htm
- http://m.3g.oexnr.cn/nnews/5081788.htm
- http://m.3g.oexnr.cn/nnews/187912.htm
- http://m.3g.oexnr.cn/nnews/0923.htm
- http://m.3g.oexnr.cn/nnews/5159.htm
- http://m.3g.oexnr.cn/nnews/90587.htm
- http://m.3g.oexnr.cn/nnews/41778.htm
- http://m.3g.oexnr.cn/nnews/8684.htm
- http://m.3g.oexnr.cn/nnews/0613.htm
- http://m.3g.oexnr.cn/nnews/79703.htm
- http://m.3g.oexnr.cn/nnews/154770.htm
- http://m.3g.oexnr.cn/nnews/1005676.htm
- http://m.3g.oexnr.cn/nnews/2806604.htm
- http://m.3g.oexnr.cn/nnews/5145416.htm
- http://m.3g.oexnr.cn/nnews/554947.htm
- http://m.3g.oexnr.cn/nnews/21103.htm
- http://m.3g.oexnr.cn/nnews/0070627.htm
- http://m.3g.oexnr.cn/nnews/4494.htm
- http://m.3g.oexnr.cn/nnews/9442349.htm
- http://m.3g.oexnr.cn/nnews/4924.htm
- http://m.3g.oexnr.cn/nnews/62025.htm
- http://m.3g.oexnr.cn/nnews/7312430.htm
- http://m.3g.oexnr.cn/nnews/06745.htm
- http://m.3g.oexnr.cn/nnews/3254441.htm
- http://m.3g.oexnr.cn/nnews/0415.htm
- http://m.3g.oexnr.cn/nnews/6980446.htm
- http://m.3g.oexnr.cn/nnews/1321.htm
- http://m.3g.oexnr.cn/nnews/6635974.htm
- http://m.3g.oexnr.cn/nnews/23958.htm
- http://m.3g.oexnr.cn/nnews/1530.htm
- http://m.3g.oexnr.cn/nnews/98144.htm
- http://m.3g.oexnr.cn/nnews/547045.htm
- http://m.3g.oexnr.cn/nnews/7670.htm
- http://m.3g.oexnr.cn/nnews/5058705.htm
- http://m.3g.oexnr.cn/nnews/13476.htm
- http://m.3g.oexnr.cn/nnews/68682.htm
- http://m.3g.oexnr.cn/nnews/72532.htm
- http://m.3g.oexnr.cn/nnews/221857.htm
- http://m.3g.oexnr.cn/nnews/8083.htm
- http://m.3g.oexnr.cn/nnews/843979.htm
- http://m.3g.oexnr.cn/nnews/40593.htm
- http://m.3g.oexnr.cn/nnews/61248.htm
- http://m.3g.oexnr.cn/nnews/31454.htm
- http://m.3g.oexnr.cn/nnews/89707.htm
- http://m.3g.oexnr.cn/nnews/8769657.htm
- http://m.3g.oexnr.cn/nnews/9024069.htm
- http://m.3g.oexnr.cn/nnews/03847.htm
- http://m.3g.oexnr.cn/nnews/7078259.htm
- http://m.3g.oexnr.cn/nnews/0893.htm
- http://m.3g.oexnr.cn/nnews/0090735.htm
- http://m.3g.oexnr.cn/nnews/066398.htm
- http://m.3g.oexnr.cn/nnews/8004.htm
- http://m.3g.oexnr.cn/nnews/62643.htm
- http://m.3g.oexnr.cn/nnews/8393492.htm
- http://m.3g.oexnr.cn/nnews/528775.htm
- http://m.3g.oexnr.cn/nnews/9563293.htm
- http://m.3g.oexnr.cn/nnews/8082201.htm
- http://m.3g.oexnr.cn/nnews/3312769.htm
- http://m.3g.oexnr.cn/nnews/7552907.htm
- http://m.3g.oexnr.cn/nnews/582042.htm
- http://m.3g.oexnr.cn/nnews/4748209.htm
- http://m.3g.oexnr.cn/nnews/230931.htm
- http://m.3g.oexnr.cn/nnews/13359.htm
- http://m.3g.oexnr.cn/nnews/7597723.htm
- http://m.3g.oexnr.cn/nnews/21934.htm
- http://m.3g.oexnr.cn/nnews/2358807.htm
- http://m.3g.oexnr.cn/nnews/221005.htm
- http://m.3g.oexnr.cn/nnews/116571.htm
- http://m.3g.oexnr.cn/nnews/133377.htm
- http://m.3g.oexnr.cn/nnews/251812.htm
- http://m.3g.oexnr.cn/nnews/2983.htm
- http://m.3g.oexnr.cn/nnews/1863.htm
- http://m.3g.oexnr.cn/nnews/817466.htm
- http://m.3g.oexnr.cn/nnews/338082.htm
- http://m.3g.oexnr.cn/nnews/6625888.htm
- http://m.3g.oexnr.cn/nnews/8055.htm
- http://m.3g.oexnr.cn/nnews/717018.htm
- http://m.3g.oexnr.cn/nnews/3381.htm
- http://m.3g.oexnr.cn/nnews/3673.htm
- http://m.3g.oexnr.cn/nnews/1623147.htm
- http://m.3g.oexnr.cn/nnews/7762.htm
- http://m.3g.oexnr.cn/nnews/3921643.htm
- http://m.3g.oexnr.cn/nnews/6571828.htm
- http://m.3g.oexnr.cn/nnews/35802.htm
- http://m.3g.oexnr.cn/nnews/8947352.htm
- http://m.3g.oexnr.cn/nnews/5660136.htm
- http://m.3g.oexnr.cn/nnews/322743.htm
- http://m.3g.oexnr.cn/nnews/1692319.htm
- http://m.3g.oexnr.cn/nnews/223217.htm
- http://m.3g.oexnr.cn/nnews/9302226.htm
- http://m.3g.oexnr.cn/nnews/2442.htm
- http://m.3g.oexnr.cn/nnews/80314.htm
- http://m.3g.oexnr.cn/nnews/7927.htm
- http://m.3g.oexnr.cn/nnews/7992.htm
- http://m.3g.oexnr.cn/nnews/0465472.htm
- http://m.3g.oexnr.cn/nnews/4525323.htm
- http://m.3g.oexnr.cn/nnews/5920.htm
- http://m.3g.oexnr.cn/nnews/2860483.htm
- http://m.3g.oexnr.cn/nnews/328021.htm
- http://m.3g.oexnr.cn/nnews/0806023.htm
- http://m.3g.oexnr.cn/nnews/4263114.htm
- http://m.3g.oexnr.cn/nnews/5202.htm
- http://m.3g.oexnr.cn/nnews/2648.htm
- http://m.3g.oexnr.cn/nnews/631236.htm
- http://m.3g.oexnr.cn/nnews/52541.htm
- http://m.3g.oexnr.cn/nnews/4780802.htm
- http://m.3g.oexnr.cn/nnews/0245788.htm
- http://m.3g.oexnr.cn/nnews/6782.htm
- http://m.3g.oexnr.cn/nnews/87905.htm
- http://m.3g.oexnr.cn/nnews/3937171.htm
- http://m.3g.oexnr.cn/nnews/22653.htm
- http://m.3g.oexnr.cn/nnews/7704841.htm
- http://m.3g.oexnr.cn/nnews/251967.htm
- http://m.3g.oexnr.cn/nnews/0348498.htm
- http://m.3g.oexnr.cn/nnews/28911.htm
- http://m.3g.oexnr.cn/nnews/41039.htm
- http://m.3g.oexnr.cn/nnews/8982.htm
- http://m.3g.oexnr.cn/nnews/8846279.htm
- http://m.3g.oexnr.cn/nnews/616212.htm
- http://m.3g.oexnr.cn/nnews/2425958.htm
- http://m.3g.oexnr.cn/nnews/5590.htm
- http://m.3g.oexnr.cn/nnews/24172.htm
- http://m.3g.oexnr.cn/nnews/908086.htm
- http://m.3g.oexnr.cn/nnews/0554.htm
- http://m.3g.oexnr.cn/nnews/7205.htm
- http://m.3g.oexnr.cn/nnews/3520133.htm
- http://m.3g.oexnr.cn/nnews/9015422.htm
- http://m.3g.oexnr.cn/nnews/4609523.htm
- http://m.3g.oexnr.cn/nnews/57670.htm
- http://m.3g.oexnr.cn/nnews/803340.htm
- http://m.3g.oexnr.cn/nnews/4520.htm
- http://m.3g.oexnr.cn/nnews/0961.htm
- http://m.3g.oexnr.cn/nnews/98028.htm
- http://m.3g.oexnr.cn/nnews/784223.htm
- http://m.3g.oexnr.cn/nnews/93291.htm
- http://m.3g.oexnr.cn/nnews/7345.htm
- http://m.3g.oexnr.cn/nnews/5383940.htm
- http://m.3g.oexnr.cn/nnews/75178.htm
- http://m.3g.oexnr.cn/nnews/3953746.htm
- http://m.3g.oexnr.cn/nnews/5424007.htm
- http://m.3g.oexnr.cn/nnews/697077.htm
- http://m.3g.oexnr.cn/nnews/83705.htm
- http://m.3g.oexnr.cn/nnews/652564.htm
- http://m.3g.oexnr.cn/nnews/786455.htm
- http://m.3g.oexnr.cn/nnews/539394.htm
- http://m.3g.oexnr.cn/nnews/9485.htm
- http://m.3g.oexnr.cn/nnews/87322.htm
- http://m.3g.oexnr.cn/nnews/488678.htm
- http://m.3g.oexnr.cn/nnews/456598.htm
- http://m.3g.oexnr.cn/nnews/4863283.htm
- http://m.3g.oexnr.cn/nnews/2745488.htm
- http://m.3g.oexnr.cn/nnews/243324.htm
- http://m.3g.oexnr.cn/nnews/5512439.htm
- http://m.3g.oexnr.cn/nnews/6648194.htm
- http://m.3g.oexnr.cn/nnews/14541.htm
- http://m.3g.oexnr.cn/nnews/50818.htm
- http://m.3g.oexnr.cn/nnews/9433.htm
- http://m.3g.oexnr.cn/nnews/96337.htm
- http://m.3g.oexnr.cn/nnews/7464458.htm
- http://m.3g.oexnr.cn/nnews/4482.htm
- http://m.3g.oexnr.cn/nnews/3027.htm
- http://m.3g.oexnr.cn/nnews/8200.htm
- http://m.3g.oexnr.cn/nnews/8083057.htm
- http://m.3g.oexnr.cn/nnews/3571.htm
- http://m.3g.oexnr.cn/nnews/4908853.htm
- http://m.3g.oexnr.cn/nnews/6155952.htm
- http://m.3g.oexnr.cn/nnews/0041846.htm
- http://m.3g.oexnr.cn/nnews/0829109.htm
- http://m.3g.oexnr.cn/nnews/8400584.htm
- http://m.3g.oexnr.cn/nnews/602233.htm
- http://m.3g.oexnr.cn/nnews/5145.htm
- http://m.3g.oexnr.cn/nnews/548596.htm
- http://m.3g.oexnr.cn/nnews/814758.htm
- http://m.3g.oexnr.cn/nnews/6673.htm
- http://m.3g.oexnr.cn/nnews/352780.htm
- http://m.3g.oexnr.cn/nnews/3695931.htm
- http://m.3g.oexnr.cn/nnews/9364402.htm
- http://m.3g.oexnr.cn/nnews/134990.htm
- http://m.3g.oexnr.cn/nnews/763344.htm
- http://m.3g.oexnr.cn/nnews/4547214.htm
- http://m.3g.oexnr.cn/nnews/62150.htm
- http://m.3g.oexnr.cn/nnews/0580.htm
- http://m.3g.oexnr.cn/nnews/2749834.htm
- http://m.3g.oexnr.cn/nnews/7208276.htm
- http://m.3g.oexnr.cn/nnews/51434.htm
- http://m.3g.oexnr.cn/nnews/5778491.htm
- http://m.3g.oexnr.cn/nnews/5673179.htm
- http://m.3g.oexnr.cn/nnews/42363.htm
- http://m.3g.oexnr.cn/nnews/3982.htm
- http://m.3g.oexnr.cn/nnews/6200580.htm
- http://m.3g.oexnr.cn/nnews/94626.htm
- http://m.3g.oexnr.cn/nnews/8934.htm
- http://m.3g.oexnr.cn/nnews/1775380.htm
- http://m.3g.oexnr.cn/nnews/1920.htm
- http://m.3g.oexnr.cn/nnews/4110.htm
- http://m.3g.oexnr.cn/nnews/4906.htm
- http://m.3g.oexnr.cn/nnews/9079.htm
- http://m.3g.oexnr.cn/nnews/25075.htm
- http://m.3g.oexnr.cn/nnews/288260.htm
- http://m.3g.oexnr.cn/nnews/66439.htm
- http://m.3g.oexnr.cn/nnews/2511547.htm
- http://m.3g.oexnr.cn/nnews/4826697.htm
- http://m.3g.oexnr.cn/nnews/32823.htm
- http://m.3g.oexnr.cn/nnews/5396630.htm
- http://m.3g.oexnr.cn/nnews/1175.htm
- http://m.3g.oexnr.cn/nnews/7634933.htm
- http://m.3g.oexnr.cn/nnews/83352.htm

## 项目结构

```
newslink-archive/
├── src/
│   ├── core/                     # 核心业务逻辑模块
│   │   ├── importer.ts           # 链接批量导入与去重校验实现
│   │   ├── metadata.ts           # 元数据提取与补全处理器
│   │   └── batch-manager.ts      # 批次创建、状态管理与统计
│   ├── api/                      # RESTful API 路由与控制器
│   │   ├── routes.ts             # 路由注册与中间件配置
│   │   └── handlers/             # 各端点请求处理函数
│   ├── models/                   # 数据模型定义（SQLite 表结构映射）
│   │   ├── link.ts               # 链接实体模型
│   │   ├── category.ts           # 分类标签模型
│   │   └── batch.ts              # 批次实体模型
│   ├── services/                 # 外部服务集成与工具层
│   │   ├── search-engine.ts      # 全文检索索引构建与查询
│   │   └── export-service.ts     # 数据导出与快照生成
│   ├── utils/                    # 通用辅助函数
│   │   ├── validator.ts          # URL 协议与格式校验
│   │   └── logger.ts             # 日志记录与分级输出
│   └── app.ts                    # 应用入口与依赖注入容器
├── tests/                        # 单元测试与集成测试套件
│   ├── unit/                     # 各模块单元测试用例
│   └── integration/              # API 与数据库集成测试
├── docs/                         # 完整文档目录
│   ├── getting-started.md        # 快速入门指南
│   ├── user-guide.md             # 用户操作手册
│   ├── api-reference.md          # API 详细参考文档
│   └── batch-management.md       # 批次管理专项文档
├── config/                       # 环境配置与默认参数
│   ├── default.json              # 默认配置项
│   └── production.json           # 生产环境覆盖配置
├── scripts/                      # 运维与辅助脚本
│   ├── init-db.sh                # 初始化数据库表结构
│   └── backup.sh                 # 定时快照备份脚本
├── .gitignore
├── package.json
├── tsconfig.json
└── README.md
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 描述你希望修复的问题或新增的功能，等待维护者确认需求范围，避免无效劳动。

2. 从主分支派生代码仓库到个人账户，在本地新建功能分支，分支命名遵循 `feature/描述` 或 `fix/描述` 格式。

3. 编写代码时遵循项目已配置的 ESLint 与 Prettier 规则，确保所有新增或修改的代码通过现有单元测试，并为新增功能补充对应的测试用例。

4. 提交变更时使用语义化提交信息格式，例如 `feat: 增加按批次筛选链接的API接口` 或 `fix: 修复导入时重复ID未正确去重的问题`。

5. 向主分支发起合并请求，在请求描述中清晰说明变更内容、测试覆盖情况以及相关 issue 编号，等待至少一名维护者审核通过后合并。

## 常见问题

**导入链接时提示“协议不受支持”或“域名不在白名单中”，如何处理？**

系统默认仅允许 http 与 https 协议，且会对域名进行格式校验。如果遇到此错误，请检查链接是否以 `http://` 或 `https://` 开头，并确保域名部分不包含非法字符。若确需添加新的可信域名，可在 `config/default.json` 中的 `allowedDomains` 数组中追加。

**如何迁移现有 SQLite 数据库文件到另一台服务器？**

直接复制项目根目录下的 `data.sqlite` 文件到新服务器对应路径即可。建议在迁移前使用内置的 `scripts/backup.sh` 脚本生成快照备份，迁移完成后运行 `npm run migrate` 确保数据库表结构与当前版本一致。

**API 接口返回的数据格式是什么？是否支持跨域请求？**

所有 API 响应均采用标准 JSON 格式，包含 `code`、`message` 和 `data` 三个顶级字段。系统默认启用 CORS 中间件，允许来自任意来源的跨域请求，可通过配置项 `cors.allowOrigin` 进行更精细的控制。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
