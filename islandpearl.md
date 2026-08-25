# LinkVault 结构化资源聚合平台

LinkVault 是一个面向技术团队、内容策展人与研究者的高密度外链资源归集与导航系统。项目定位为“技术信息基础设施的辅助层”，专注于解决分散在各类技术博客、新闻通告、变更日志与社区讨论中的高价值链接的采集、分类、持久化与可检索问题。目标用户包括技术文档工程师、开发者关系维护人员、安全研究员以及需要长期跟踪特定域名或内容类型变化的自动化脚本使用者。LinkVault 不提供爬虫或采集功能，但为手动或半自动化的链接整理工作提供标准化的元数据描述框架、存储结构、去重索引与静态站点生成支持，帮助用户将数百甚至上千条原始 URL 转化为结构清晰、可维护、可分享的本地知识库。

## 功能概览

**链接条目规范化入库** 对用户输入的任意 URL 进行协议保留、大小写保持、路径完整性校验，并自动补充缺失的尾部斜杠检测标记，确保入库链接与原始来源完全一致。

**多级标签与分类引擎** 支持为每条链接自定义主分类、子分类以及最多五个自由标签，并基于域名、路径模式或内容特征提供批量标签预测建议。

**状态监控与可用性追踪** 定时检测已入库链接的 HTTP 状态码、响应时间与内容哈希变化，标记失效链接、重定向链接以及内容发生重大变更的链接，并生成变更报告。

**全文检索与高级过滤** 基于 SQLite FTS5 或 Elasticsearch 可选后端，支持对链接标题、描述、标签、来源域名及注释内容进行全文检索，并支持按状态、分类、标签组合过滤。

**静态站点生成与分享** 提供内置模板引擎，可将当前链接库一键导出为纯静态 HTML 网站，包含索引页、分类页、标签云与 sitemap，适用于团队内部文档站或公开资源导航页。

**数据导入导出兼容性** 支持 CSV、JSON、Markdown 列表、书签 HTML 等多种格式的批量导入与导出，方便与其他工具链集成。

**变更审计日志** 记录每次链接新增、编辑、删除、状态变更的操作人、时间与变更前后内容，满足团队协作与合规追溯需求。

## 应用场景

技术文档团队维护外部参考资料库 文档撰写过程中引用的技术博客、规范文档、官方 SDK 发布说明等外部链接数量庞大且容易失效。LinkVault 允许团队集中管理这些链接，定期检查可用性，并在文档发布前自动生成链接健康度报告，避免文档中出现死链。

安全研究人员的威胁情报链接归集 安全研究员每日收集大量关于漏洞公告、POC 发布、厂商安全响应中心的链接。LinkVault 的标签系统与状态监控可帮助研究员按 CVE 编号、影响产品、威胁等级等维度快速检索，并及时发现原有链接的内容更新。

开源项目外部依赖与参考材料索引 开源项目 README 或文档中常引用大量外部资源。LinkVault 可作为项目仓库的子模块，存储所有外部参考链接的元数据，并在 CI 流程中检查链接有效性，确保项目文档中的资源始终可访问。

技术策展人的主题资源周刊制作 技术策展人或社区运营者需要定期整理某一技术领域的优质文章、工具、视频等资源并发布周刊或月刊。LinkVault 的静态站点生成功能可快速将链接集合渲染为可直接发布的 HTML 页面，减少手动排版工作。

## 快速开始

以下命令演示如何获取 LinkVault 源码、安装依赖并启动本地开发服务。

```bash
git clone https://github.com/linkvault/linkvault-core.git
cd linkvault-core
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py load_sample_data
python manage.py runserver
```

执行上述步骤后，开发服务器将运行在本地 8000 端口。访问 http://127.0.0.1:8000 可查看示例链接列表。如需导入用户提供的原始链接数据，可将链接列表保存为 links.txt 后执行 `python manage.py import --file links.txt`。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 或更高 | 核心运行环境，推荐使用 3.11+ 以获得性能优化 |
| SQLite | 3.35 或更高 | 内置数据库引擎，支持 JSON 函数与 FTS5 全文搜索 |
| pip | 21.0 或更高 | Python 包管理器，用于安装项目依赖 |
| Git | 2.25 或更高 | 版本控制工具，用于克隆仓库与管理配置变更 |
| Node.js | 16.0 或更高 | 仅当启用前端构建功能时需要，用于编译静态资源 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | /docs/user-guide/ | 如何添加链接、编辑元数据、使用搜索与过滤、生成静态站点 |
| 管理员指南 | /docs/admin-guide/ | 如何配置监控周期、管理用户权限、调整导入导出编码与格式 |
| 开发者文档 | /docs/developer-guide/ | 如何扩展标签预测器、增加新的导入导出格式、自定义状态检查策略 |
| API 参考 | /docs/api-reference/ | RESTful API 的端点列表、请求参数、响应格式与鉴权方式 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/8513.htm
- http://m.3g.ghtkgg.cn/nnews/367426.htm
- http://m.3g.ghtkgg.cn/nnews/46414.htm
- http://m.3g.ghtkgg.cn/nnews/52772.htm
- http://m.3g.ghtkgg.cn/nnews/1554080.htm
- http://m.3g.ghtkgg.cn/nnews/872601.htm
- http://m.3g.ghtkgg.cn/nnews/7884.htm
- http://m.3g.ghtkgg.cn/nnews/071804.htm
- http://m.3g.ghtkgg.cn/nnews/565020.htm
- http://m.3g.ghtkgg.cn/nnews/313134.htm
- http://m.3g.ghtkgg.cn/nnews/55813.htm
- http://m.3g.ghtkgg.cn/nnews/536790.htm
- http://m.3g.ghtkgg.cn/nnews/5313.htm
- http://m.3g.ghtkgg.cn/nnews/1695853.htm
- http://m.3g.ghtkgg.cn/nnews/336506.htm
- http://m.3g.ghtkgg.cn/nnews/21046.htm
- http://m.3g.ghtkgg.cn/nnews/52960.htm
- http://m.3g.ghtkgg.cn/nnews/2672.htm
- http://m.3g.ghtkgg.cn/nnews/388276.htm
- http://m.3g.ghtkgg.cn/nnews/8796.htm
- http://m.3g.ghtkgg.cn/nnews/217109.htm
- http://m.3g.ghtkgg.cn/nnews/380923.htm
- http://m.3g.ghtkgg.cn/nnews/4429.htm
- http://m.3g.ghtkgg.cn/nnews/11519.htm
- http://m.3g.ghtkgg.cn/nnews/14945.htm
- http://m.3g.ghtkgg.cn/nnews/9905.htm
- http://m.3g.ghtkgg.cn/nnews/12449.htm
- http://m.3g.ghtkgg.cn/nnews/2709.htm
- http://m.3g.ghtkgg.cn/nnews/10313.htm
- http://m.3g.ghtkgg.cn/nnews/5774.htm
- http://m.3g.ghtkgg.cn/nnews/1513169.htm
- http://m.3g.ghtkgg.cn/nnews/0263971.htm
- http://m.3g.ghtkgg.cn/nnews/30089.htm
- http://m.3g.ghtkgg.cn/nnews/383404.htm
- http://m.3g.ghtkgg.cn/nnews/806669.htm
- http://m.3g.ghtkgg.cn/nnews/748135.htm
- http://m.3g.ghtkgg.cn/nnews/2487569.htm
- http://m.3g.ghtkgg.cn/nnews/82358.htm
- http://m.3g.ghtkgg.cn/nnews/1033335.htm
- http://m.3g.ghtkgg.cn/nnews/1304300.htm
- http://m.3g.ghtkgg.cn/nnews/876186.htm
- http://m.3g.ghtkgg.cn/nnews/3189065.htm
- http://m.3g.ghtkgg.cn/nnews/2337846.htm
- http://m.3g.ghtkgg.cn/nnews/1396.htm
- http://m.3g.ghtkgg.cn/nnews/60609.htm
- http://m.3g.ghtkgg.cn/nnews/2480176.htm
- http://m.3g.ghtkgg.cn/nnews/62702.htm
- http://m.3g.ghtkgg.cn/nnews/7794.htm
- http://m.3g.ghtkgg.cn/nnews/22845.htm
- http://m.3g.ghtkgg.cn/nnews/009861.htm
- http://m.3g.ghtkgg.cn/nnews/1906.htm
- http://m.3g.ghtkgg.cn/nnews/9672.htm
- http://m.3g.ghtkgg.cn/nnews/5358.htm
- http://m.3g.ghtkgg.cn/nnews/02222.htm
- http://m.3g.ghtkgg.cn/nnews/3049.htm
- http://m.3g.ghtkgg.cn/nnews/562882.htm
- http://m.3g.ghtkgg.cn/nnews/671358.htm
- http://m.3g.ghtkgg.cn/nnews/375901.htm
- http://m.3g.ghtkgg.cn/nnews/939518.htm
- http://m.3g.ghtkgg.cn/nnews/118336.htm
- http://m.3g.ghtkgg.cn/nnews/4820.htm
- http://m.3g.ghtkgg.cn/nnews/2563120.htm
- http://m.3g.ghtkgg.cn/nnews/1682554.htm
- http://m.3g.ghtkgg.cn/nnews/0936.htm
- http://m.3g.ghtkgg.cn/nnews/5717.htm
- http://m.3g.ghtkgg.cn/nnews/91302.htm
- http://m.3g.ghtkgg.cn/nnews/8420097.htm
- http://m.3g.ghtkgg.cn/nnews/016369.htm
- http://m.3g.ghtkgg.cn/nnews/0362411.htm
- http://m.3g.ghtkgg.cn/nnews/0224.htm
- http://m.3g.ghtkgg.cn/nnews/6801817.htm
- http://m.3g.ghtkgg.cn/nnews/06328.htm
- http://m.3g.ghtkgg.cn/nnews/750196.htm
- http://m.3g.ghtkgg.cn/nnews/045278.htm
- http://m.3g.ghtkgg.cn/nnews/3581.htm
- http://m.3g.ghtkgg.cn/nnews/06184.htm
- http://m.3g.ghtkgg.cn/nnews/3307.htm
- http://m.3g.ghtkgg.cn/nnews/3344.htm
- http://m.3g.ghtkgg.cn/nnews/47421.htm
- http://m.3g.ghtkgg.cn/nnews/406170.htm
- http://m.3g.ghtkgg.cn/nnews/0711.htm
- http://m.3g.ghtkgg.cn/nnews/8712266.htm
- http://m.3g.ghtkgg.cn/nnews/3747997.htm
- http://m.3g.ghtkgg.cn/nnews/370224.htm
- http://m.3g.ghtkgg.cn/nnews/572549.htm
- http://m.3g.ghtkgg.cn/nnews/05038.htm
- http://m.3g.ghtkgg.cn/nnews/1215200.htm
- http://m.3g.ghtkgg.cn/nnews/87397.htm
- http://m.3g.ghtkgg.cn/nnews/9030901.htm
- http://m.3g.ghtkgg.cn/nnews/7180808.htm
- http://m.3g.ghtkgg.cn/nnews/49143.htm
- http://m.3g.ghtkgg.cn/nnews/202680.htm
- http://m.3g.ghtkgg.cn/nnews/86006.htm
- http://m.3g.ghtkgg.cn/nnews/435774.htm
- http://m.3g.ghtkgg.cn/nnews/4342.htm
- http://m.3g.ghtkgg.cn/nnews/0372.htm
- http://m.3g.ghtkgg.cn/nnews/69053.htm
- http://m.3g.ghtkgg.cn/nnews/690790.htm
- http://m.3g.ghtkgg.cn/nnews/3526053.htm
- http://m.3g.ghtkgg.cn/nnews/0391.htm
- http://m.3g.ghtkgg.cn/nnews/6318344.htm
- http://m.3g.ghtkgg.cn/nnews/30609.htm
- http://m.3g.ghtkgg.cn/nnews/4272002.htm
- http://m.3g.ghtkgg.cn/nnews/5190.htm
- http://m.3g.ghtkgg.cn/nnews/71737.htm
- http://m.3g.ghtkgg.cn/nnews/906802.htm
- http://m.3g.ghtkgg.cn/nnews/886920.htm
- http://m.3g.ghtkgg.cn/nnews/2447.htm
- http://m.3g.ghtkgg.cn/nnews/66744.htm
- http://m.3g.ghtkgg.cn/nnews/9003.htm
- http://m.3g.ghtkgg.cn/nnews/067521.htm
- http://m.3g.ghtkgg.cn/nnews/890307.htm
- http://m.3g.ghtkgg.cn/nnews/72389.htm
- http://m.3g.ghtkgg.cn/nnews/682637.htm
- http://m.3g.ghtkgg.cn/nnews/6472319.htm
- http://m.3g.ghtkgg.cn/nnews/858463.htm
- http://m.3g.ghtkgg.cn/nnews/402984.htm
- http://m.3g.ghtkgg.cn/nnews/5793933.htm
- http://m.3g.ghtkgg.cn/nnews/14354.htm
- http://m.3g.ghtkgg.cn/nnews/803291.htm
- http://m.3g.ghtkgg.cn/nnews/2419.htm
- http://m.3g.ghtkgg.cn/nnews/7473273.htm
- http://m.3g.ghtkgg.cn/nnews/1743.htm
- http://m.3g.ghtkgg.cn/nnews/3022.htm
- http://m.3g.ghtkgg.cn/nnews/880506.htm
- http://m.3g.ghtkgg.cn/nnews/1200.htm
- http://m.3g.ghtkgg.cn/nnews/13348.htm
- http://m.3g.ghtkgg.cn/nnews/419060.htm
- http://m.3g.ghtkgg.cn/nnews/76165.htm
- http://m.3g.ghtkgg.cn/nnews/4540227.htm
- http://m.3g.ghtkgg.cn/nnews/09922.htm
- http://m.3g.ghtkgg.cn/nnews/46338.htm
- http://m.3g.ghtkgg.cn/nnews/6001.htm
- http://m.3g.ghtkgg.cn/nnews/577984.htm
- http://m.3g.ghtkgg.cn/nnews/53228.htm
- http://m.3g.ghtkgg.cn/nnews/423611.htm
- http://m.3g.ghtkgg.cn/nnews/848648.htm
- http://m.3g.ghtkgg.cn/nnews/34122.htm
- http://m.3g.ghtkgg.cn/nnews/440392.htm
- http://m.3g.ghtkgg.cn/nnews/315404.htm
- http://m.3g.ghtkgg.cn/nnews/47673.htm
- http://m.3g.ghtkgg.cn/nnews/4183.htm
- http://m.3g.ghtkgg.cn/nnews/3054457.htm
- http://m.3g.ghtkgg.cn/nnews/58322.htm
- http://m.3g.ghtkgg.cn/nnews/9305869.htm
- http://m.3g.ghtkgg.cn/nnews/54529.htm
- http://m.3g.ghtkgg.cn/nnews/780829.htm
- http://m.3g.ghtkgg.cn/nnews/813677.htm
- http://m.3g.ghtkgg.cn/nnews/4416571.htm
- http://m.3g.ghtkgg.cn/nnews/36651.htm
- http://m.3g.ghtkgg.cn/nnews/1833115.htm
- http://m.3g.ghtkgg.cn/nnews/669664.htm
- http://m.3g.ghtkgg.cn/nnews/726823.htm
- http://m.3g.ghtkgg.cn/nnews/961809.htm
- http://m.3g.ghtkgg.cn/nnews/641669.htm
- http://m.3g.ghtkgg.cn/nnews/9310144.htm
- http://m.3g.ghtkgg.cn/nnews/6332.htm
- http://m.3g.ghtkgg.cn/nnews/8715653.htm
- http://m.3g.ghtkgg.cn/nnews/14589.htm
- http://m.3g.ghtkgg.cn/nnews/3471478.htm
- http://m.3g.ghtkgg.cn/nnews/1379702.htm
- http://m.3g.ghtkgg.cn/nnews/553977.htm
- http://m.3g.ghtkgg.cn/nnews/12142.htm
- http://m.3g.ghtkgg.cn/nnews/93105.htm
- http://m.3g.ghtkgg.cn/nnews/935946.htm
- http://m.3g.ghtkgg.cn/nnews/3281289.htm
- http://m.3g.ghtkgg.cn/nnews/211254.htm
- http://m.3g.ghtkgg.cn/nnews/394311.htm
- http://m.3g.ghtkgg.cn/nnews/679371.htm
- http://m.3g.ghtkgg.cn/nnews/55982.htm
- http://m.3g.ghtkgg.cn/nnews/8795214.htm
- http://m.3g.ghtkgg.cn/nnews/83425.htm
- http://m.3g.ghtkgg.cn/nnews/6738.htm
- http://m.3g.ghtkgg.cn/nnews/46136.htm
- http://m.3g.ghtkgg.cn/nnews/7871.htm
- http://m.3g.ghtkgg.cn/nnews/524695.htm
- http://m.3g.ghtkgg.cn/nnews/661456.htm
- http://m.3g.ghtkgg.cn/nnews/90992.htm
- http://m.3g.ghtkgg.cn/nnews/1445.htm
- http://m.3g.ghtkgg.cn/nnews/4624.htm
- http://m.3g.ghtkgg.cn/nnews/271298.htm
- http://m.3g.ghtkgg.cn/nnews/809763.htm
- http://m.3g.ghtkgg.cn/nnews/05730.htm
- http://m.3g.ghtkgg.cn/nnews/9727.htm
- http://m.3g.ghtkgg.cn/nnews/7977423.htm
- http://m.3g.ghtkgg.cn/nnews/419432.htm
- http://m.3g.ghtkgg.cn/nnews/97062.htm
- http://m.3g.ghtkgg.cn/nnews/9834.htm
- http://m.3g.ghtkgg.cn/nnews/4880014.htm
- http://m.3g.ghtkgg.cn/nnews/110870.htm
- http://m.3g.ghtkgg.cn/nnews/5772314.htm
- http://m.3g.ghtkgg.cn/nnews/91966.htm
- http://m.3g.ghtkgg.cn/nnews/2057.htm
- http://m.3g.ghtkgg.cn/nnews/647208.htm
- http://m.3g.ghtkgg.cn/nnews/0148.htm
- http://m.3g.ghtkgg.cn/nnews/69398.htm
- http://m.3g.ghtkgg.cn/nnews/7523490.htm
- http://m.3g.ghtkgg.cn/nnews/12796.htm
- http://m.3g.ghtkgg.cn/nnews/580234.htm
- http://m.3g.ghtkgg.cn/nnews/5929.htm
- http://m.3g.ghtkgg.cn/nnews/2906.htm
- http://m.3g.ghtkgg.cn/nnews/0710631.htm
- http://m.3g.ghtkgg.cn/nnews/2143.htm
- http://m.3g.ghtkgg.cn/nnews/834789.htm
- http://m.3g.ghtkgg.cn/nnews/5500.htm
- http://m.3g.ghtkgg.cn/nnews/3718.htm
- http://m.3g.ghtkgg.cn/nnews/59425.htm
- http://m.3g.ghtkgg.cn/nnews/24507.htm
- http://m.3g.ghtkgg.cn/nnews/55376.htm
- http://m.3g.ghtkgg.cn/nnews/3059.htm
- http://m.3g.ghtkgg.cn/nnews/960491.htm
- http://m.3g.ghtkgg.cn/nnews/3221649.htm
- http://m.3g.ghtkgg.cn/nnews/47713.htm
- http://m.3g.ghtkgg.cn/nnews/55506.htm
- http://m.3g.ghtkgg.cn/nnews/136701.htm
- http://m.3g.ghtkgg.cn/nnews/764365.htm
- http://m.3g.ghtkgg.cn/nnews/4499.htm
- http://m.3g.ghtkgg.cn/nnews/0341.htm
- http://m.3g.ghtkgg.cn/nnews/68760.htm
- http://m.3g.ghtkgg.cn/nnews/1749766.htm
- http://m.3g.ghtkgg.cn/nnews/7443874.htm
- http://m.3g.ghtkgg.cn/nnews/61106.htm
- http://m.3g.ghtkgg.cn/nnews/57601.htm
- http://m.3g.ghtkgg.cn/nnews/4217.htm
- http://m.3g.ghtkgg.cn/nnews/03141.htm
- http://m.3g.ghtkgg.cn/nnews/60053.htm
- http://m.3g.ghtkgg.cn/nnews/944237.htm
- http://m.3g.ghtkgg.cn/nnews/8036988.htm
- http://m.3g.ghtkgg.cn/nnews/0987352.htm
- http://m.3g.ghtkgg.cn/nnews/0720.htm
- http://m.3g.ghtkgg.cn/nnews/252449.htm
- http://m.3g.ghtkgg.cn/nnews/8039239.htm
- http://m.3g.ghtkgg.cn/nnews/1821125.htm
- http://m.3g.ghtkgg.cn/nnews/86296.htm
- http://m.3g.ghtkgg.cn/nnews/4014.htm
- http://m.3g.ghtkgg.cn/nnews/042915.htm
- http://m.3g.ghtkgg.cn/nnews/813668.htm
- http://m.3g.ghtkgg.cn/nnews/1828.htm
- http://m.3g.ghtkgg.cn/nnews/91972.htm
- http://m.3g.ghtkgg.cn/nnews/2655915.htm
- http://m.3g.ghtkgg.cn/nnews/6771.htm
- http://m.3g.ghtkgg.cn/nnews/0016.htm
- http://m.3g.ghtkgg.cn/nnews/8783673.htm
- http://m.3g.ghtkgg.cn/nnews/499569.htm
- http://m.3g.ghtkgg.cn/nnews/3530.htm
- http://m.3g.ghtkgg.cn/nnews/816901.htm
- http://m.3g.ghtkgg.cn/nnews/4282.htm
- http://m.3g.ghtkgg.cn/nnews/173932.htm
- http://m.3g.ghtkgg.cn/nnews/0632.htm
- http://m.3g.ghtkgg.cn/nnews/8329384.htm
- http://m.3g.ghtkgg.cn/nnews/84941.htm
- http://m.3g.ghtkgg.cn/nnews/01020.htm
- http://m.3g.ghtkgg.cn/nnews/72219.htm
- http://m.3g.ghtkgg.cn/nnews/0926915.htm
- http://m.3g.ghtkgg.cn/nnews/6444.htm
- http://m.3g.ghtkgg.cn/nnews/395860.htm
- http://m.3g.ghtkgg.cn/nnews/93438.htm
- http://m.3g.ghtkgg.cn/nnews/4161.htm
- http://m.3g.ghtkgg.cn/nnews/4250835.htm
- http://m.3g.ghtkgg.cn/nnews/993034.htm
- http://m.3g.ghtkgg.cn/nnews/2131362.htm
- http://m.3g.ghtkgg.cn/nnews/832380.htm
- http://m.3g.ghtkgg.cn/nnews/371469.htm
- http://m.3g.ghtkgg.cn/nnews/70353.htm
- http://m.3g.ghtkgg.cn/nnews/69632.htm
- http://m.3g.ghtkgg.cn/nnews/668810.htm
- http://m.3g.ghtkgg.cn/nnews/849979.htm
- http://m.3g.ghtkgg.cn/nnews/71472.htm
- http://m.3g.ghtkgg.cn/nnews/9584718.htm
- http://m.3g.ghtkgg.cn/nnews/1806.htm
- http://m.3g.ghtkgg.cn/nnews/917830.htm
- http://m.3g.ghtkgg.cn/nnews/963190.htm
- http://m.3g.ghtkgg.cn/nnews/052429.htm
- http://m.3g.ghtkgg.cn/nnews/51236.htm
- http://m.3g.ghtkgg.cn/nnews/3596.htm
- http://m.3g.ghtkgg.cn/nnews/28353.htm
- http://m.3g.ghtkgg.cn/nnews/67901.htm
- http://m.3g.ghtkgg.cn/nnews/320292.htm
- http://m.3g.ghtkgg.cn/nnews/1741.htm
- http://m.3g.ghtkgg.cn/nnews/29692.htm
- http://m.3g.ghtkgg.cn/nnews/450275.htm
- http://m.3g.ghtkgg.cn/nnews/3082389.htm
- http://m.3g.ghtkgg.cn/nnews/268303.htm
- http://m.3g.ghtkgg.cn/nnews/603942.htm
- http://m.3g.ghtkgg.cn/nnews/7599000.htm
- http://m.3g.ghtkgg.cn/nnews/145457.htm
- http://m.3g.ghtkgg.cn/nnews/02040.htm
- http://m.3g.ghtkgg.cn/nnews/2404574.htm
- http://m.3g.ghtkgg.cn/nnews/413850.htm
- http://m.3g.ghtkgg.cn/nnews/912317.htm
- http://m.3g.ghtkgg.cn/nnews/13885.htm
- http://m.3g.ghtkgg.cn/nnews/6316.htm
- http://m.3g.ghtkgg.cn/nnews/33824.htm
- http://m.3g.ghtkgg.cn/nnews/889251.htm
- http://m.3g.ghtkgg.cn/nnews/1336362.htm
- http://m.3g.ghtkgg.cn/nnews/7003275.htm
- http://m.3g.ghtkgg.cn/nnews/7437703.htm
- http://m.3g.ghtkgg.cn/nnews/4972.htm
- http://m.3g.ghtkgg.cn/nnews/7806736.htm
- http://m.3g.ghtkgg.cn/nnews/251631.htm

## 项目结构

```
linkvault-core/
├── manage.py                 # 项目入口命令行工具，集成迁移、导入、检查、运行服务等子命令
├── requirements.txt          # Python 依赖清单，包含 Django、requests、sqlite-utils 等核心库
├── .env.example              # 环境变量模板，配置数据库路径、监控间隔、日志级别等参数
├── src/
│   ├── core/                 # 核心配置与应用启动模块
│   │   ├── settings.py       # Django 项目配置，包含数据库、中间件、模板与静态文件路径
│   │   ├── urls.py           # 根路由配置，映射 API 与视图端点
│   │   └── wsgi.py           # 生产环境 WSGI 入口
│   ├── links/                # 链接管理主应用
│   │   ├── models.py         # Link、Tag、StatusHistory、AuditLog 等数据模型定义
│   │   ├── admin.py          # 后台管理界面定制，支持批量标签编辑与状态筛选
│   │   ├── views/            # API 视图与网页视图函数集合
│   │   ├── services/         # 业务逻辑层，包含链接检查器、导入导出器、静态生成器
│   │   └── migrations/       # 数据库迁移脚本，按版本管理表结构变更
│   ├── common/               # 通用工具与辅助函数
│   │   ├── validators.py     # URL 规范化、协议保留、路径清洗等校验函数
│   │   ├── parsers.py        # 多种格式解析器，支持 CSV、JSON、HTML 书签等
│   │   └── logger.py         # 日志配置与审计日志写入接口
│   └── static/               # 静态资源目录
│       ├── css/              # 基础样式与响应式布局文件
│       └── js/               # 前端交互脚本，包含搜索自动补全与状态图表
├── tests/                    # 单元测试与集成测试用例
│   ├── test_models.py        # 数据模型层测试
│   ├── test_services.py      # 业务服务层测试，覆盖检查器与导入导出逻辑
│   └── test_validators.py    # URL 校验与规范化函数测试
├── docs/                     # 完整文档源文件
│   ├── user-guide/           # 用户手册分章节 Markdown
│   ├── admin-guide/          # 管理员指南
│   └── api-reference/        # API 接口文档，含请求与响应示例
└── scripts/                  # 运维与辅助脚本
    ├── backup_db.sh          # 数据库定时备份脚本
    ├── import_batch.sh       # 批量导入命令行封装
    └── check_all_links.py    # 手动触发全量链接状态检查脚本
```

## 贡献指南

贡献者需先查阅项目行为准则与开发者证书。所有贡献均通过 GitHub Pull Request 流程提交，并需确保代码通过现有测试套件且新增功能附带相应测试用例。

具体步骤包括：Fork 本仓库至个人账户，克隆 Fork 后的仓库到本地，并添加 upstream 指向原仓库。创建新的功能分支，分支名称应反映修改内容，例如 feature/add-csv-export-encoding 或 fix/import-path-normalization。在本地完成代码编写与测试后，提交变更并推送到个人 Fork 仓库。随后在原仓库中发起 Pull Request，并在描述中明确说明修改目的、影响范围以及是否涉及数据库迁移或配置变更。项目维护者将在三个工作日内进行代码审查，提出修改意见或合并请求。对于非代码类贡献，如文档改进、示例数据补充或翻译，可直接在 Issue 中描述变更内容，由维护者评估后合并。

## 常见问题

问：导入链接时提示“URL 格式不合法”，但我确认链接可以正常访问。

答：LinkVault 的 URL 校验器默认禁止非标准的协议（如 ftp、file）以及包含未编码空格或中文逗号的链接。请检查链接是否包含特殊字符，如有需要可启用宽松模式（在 .env 中设置 LINK_VALIDATION_STRICT=false）。此外，校验器会保留原始 URL 的大小写和协议，不会自动补全缺失的协议头，请确保每条链接以 http:// 或 https:// 开头。

问：静态站点生成后，部分链接在页面中显示为纯文本而非可点击的超链接。

答：这是 LinkVault 的设计选择，生成静态页面时默认将外部链接渲染为纯文本，以避免自动添加的链接误导读者或引入追踪参数。如需生成可点击链接，可在导出配置中设置 EXPORT_LINK_RENDER_MODE=anchor，但请注意这可能会改变原始链接的呈现方式。推荐做法是在页面顶部或底部统一声明所有链接为外部资源，不保证其长期可用性。

问：如何迁移 LinkVault 数据到另一台服务器？

答：迁移需要同时转移 SQLite 数据库文件（默认为 data/linkvault.db）以及 media 目录下存储的附件或缓存文件。在新服务器上安装相同版本的 LinkVault 后，停止服务，将数据库文件和 media 目录覆盖到对应位置，然后执行 python manage.py migrate --run-syncdb 以确保数据库表结构与当前版本一致，但不会清空已有数据。最后执行 python manage.py check_links --rebuild-index 重建全文搜索索引。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:55
