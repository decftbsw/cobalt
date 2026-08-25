# NewsLink Hub

NewsLink Hub 是一个面向技术资讯聚合与轻量级新闻分发场景的开源外链资源管理站。项目定位于为中小型内容站点、个人博客、RSS 聚合工具以及自动化舆情分析系统提供结构化的新闻入口链接池，解决分散来源、人工采集效率低、链接管理混乱等问题。本项目不生产内容，仅作为高质量外链的索引层与导航层，通过规范化 URL 编排与分类标记，帮助用户快速定位目标信息源。

本项目适用于需要批量管理外部新闻链接、构建自定义新闻门户、或进行链接热度与有效性巡检的开发者与运维人员。项目本身不依赖数据库，所有资源以静态清单形式维护，便于版本控制、批量导入与自动化流水线集成。

## 功能概览

批量链接导入与去重 支持从 CSV、JSON 及纯文本列表批量导入 URL，自动识别重复条目并生成去重报告。

分类标签系统 允许用户为每条链接打上多个自定义标签（如 科技、财经、军事、体育），并支持按标签过滤与检索。

链接可用性巡检 内置 HTTP 状态码检查模块，可定时探测链接存活状态，输出失效链接报表。

全文元数据提取 自动抓取目标页面的标题、摘要与发布时间，生成结构化索引卡片。

多级目录树视图 按来源域名、日期区间或自定义分组将链接组织为树状目录，便于人工审阅。

外部资源导出 支持将选中的链接列表导出为 Markdown 表格、JSON API 格式或纯文本清单。

静态化生成模式 提供构建命令，可将当前链接池渲染为纯静态 HTML 门户，无需后端服务即可部署。

访问统计与点击追踪 可选接入轻量级计数接口，统计各链接的点击频次与来源 Referer。

## 应用场景

技术博客的每周资讯汇总 个人博主或小型编辑团队可使用本项目整理一周内值得关注的行业新闻链接，自动生成带摘要的「一周速览」页面，减少手动排版工作。

企业内部舆情监控数据源管理 企业公关或市场部门可将本项目作为舆情系统前置组件，维护一批重点媒体与论坛的监控入口，每日巡检链接有效性，确保采集管道稳定。

自动化 RSS 增强中间层 开发者可将本项目输出的结构化 JSON 作为 RSS 生成器的输入，为不具备 RSS 输出的传统新闻站点制作自定义 Feed。

学术研究中的媒体内容采样 社会科学研究者可借助本项目的标签过滤与导出功能，快速构建特定主题（如 人工智能 或 气候变化）的新闻样本库，用于内容分析。

个人导航站自建方案 普通用户可通过静态化生成模式，将本项目快速变身为个人风格的信息导航首页，替代浏览器书签的杂乱管理。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/newslink-hub/newslink-hub.git
cd newslink-hub

# 安装依赖（基于 Node.js 20+）
npm install

# 复制示例配置文件
cp .env.example .env

# 执行初始化构建，生成静态资源
npm run build

# 启动本地开发服务器，默认端口 3000
npm start
```

访问 http://localhost:3000 即可查看默认的链接看板。如需导入用户提供的原始链接列表，请将 URL 逐行放入 `data/raw_links.txt` 文件，然后执行 `npm run import` 命令。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Node.js | 20.x 或更高 | 运行时环境，用于执行构建脚本与开发服务器 |
| npm | 9.x 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.30 或更高 | 版本控制工具，用于克隆仓库与提交变更 |
| curl | 7.68 或更高 | 用于链接可用性巡检模块的 HTTP 探测 |
| sqlite3 | 3.31 或更高 | 可选依赖，用于启用持久化存储与历史记录 |
| Python | 3.9 或更高 | 仅用于运行附带的元数据提取辅助脚本 |
| cron | 系统自带 | 用于定时任务调度（可选，仅在启用自动巡检时需要） |
| nginx | 1.18 或更高 | 生产环境静态部署推荐（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide/ | 如何导入链接、打标签、生成静态门户与导出数据 |
| 运维指南 | docs/ops-guide/ | 如何配置巡检频率、调整缓存策略、备份链接池 |
| 开发者文档 | docs/dev-guide/ | 插件扩展机制、API 接口规范、自定义渲染模板 |
| 设计说明 | docs/design/ | 数据模型、目录结构设计、静态化生成原理 |
| 变更日志 | CHANGELOG.md | 每个版本的更新内容、破坏性变更与迁移步骤 |
| 常见工作流 | docs/workflows/ | 针对内容编辑、运维、开发三种角色的典型操作路径 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/716569.htm
- http://m.3g.ghtkgg.cn/nnews/6286861.htm
- http://m.3g.ghtkgg.cn/nnews/4436603.htm
- http://m.3g.ghtkgg.cn/nnews/66449.htm
- http://m.3g.ghtkgg.cn/nnews/8375473.htm
- http://m.3g.ghtkgg.cn/nnews/0881036.htm
- http://m.3g.ghtkgg.cn/nnews/2301.htm
- http://m.3g.ghtkgg.cn/nnews/98711.htm
- http://m.3g.ghtkgg.cn/nnews/132534.htm
- http://m.3g.ghtkgg.cn/nnews/2511504.htm
- http://m.3g.ghtkgg.cn/nnews/51793.htm
- http://m.3g.ghtkgg.cn/nnews/441323.htm
- http://m.3g.ghtkgg.cn/nnews/33719.htm
- http://m.3g.ghtkgg.cn/nnews/7111.htm
- http://m.3g.ghtkgg.cn/nnews/8336.htm
- http://m.3g.ghtkgg.cn/nnews/9289.htm
- http://m.3g.ghtkgg.cn/nnews/2832.htm
- http://m.3g.ghtkgg.cn/nnews/6013535.htm
- http://m.3g.ghtkgg.cn/nnews/571905.htm
- http://m.3g.ghtkgg.cn/nnews/490097.htm
- http://m.3g.ghtkgg.cn/nnews/6007192.htm
- http://m.3g.ghtkgg.cn/nnews/1643.htm
- http://m.3g.ghtkgg.cn/nnews/3930427.htm
- http://m.3g.ghtkgg.cn/nnews/61627.htm
- http://m.3g.ghtkgg.cn/nnews/272737.htm
- http://m.3g.ghtkgg.cn/nnews/368124.htm
- http://m.3g.ghtkgg.cn/nnews/098294.htm
- http://m.3g.ghtkgg.cn/nnews/1364786.htm
- http://m.3g.ghtkgg.cn/nnews/82988.htm
- http://m.3g.ghtkgg.cn/nnews/944098.htm
- http://m.3g.ghtkgg.cn/nnews/0461.htm
- http://m.3g.ghtkgg.cn/nnews/4633.htm
- http://m.3g.ghtkgg.cn/nnews/3495365.htm
- http://m.3g.ghtkgg.cn/nnews/4368385.htm
- http://m.3g.ghtkgg.cn/nnews/8803519.htm
- http://m.3g.ghtkgg.cn/nnews/2420299.htm
- http://m.3g.ghtkgg.cn/nnews/7933400.htm
- http://m.3g.ghtkgg.cn/nnews/1672121.htm
- http://m.3g.ghtkgg.cn/nnews/340535.htm
- http://m.3g.ghtkgg.cn/nnews/9069005.htm
- http://m.3g.ghtkgg.cn/nnews/26846.htm
- http://m.3g.ghtkgg.cn/nnews/29377.htm
- http://m.3g.ghtkgg.cn/nnews/89385.htm
- http://m.3g.ghtkgg.cn/nnews/775258.htm
- http://m.3g.ghtkgg.cn/nnews/8716.htm
- http://m.3g.ghtkgg.cn/nnews/17705.htm
- http://m.3g.ghtkgg.cn/nnews/844670.htm
- http://m.3g.ghtkgg.cn/nnews/4145383.htm
- http://m.3g.ghtkgg.cn/nnews/2525324.htm
- http://m.3g.ghtkgg.cn/nnews/59321.htm
- http://m.3g.ghtkgg.cn/nnews/8149.htm
- http://m.3g.ghtkgg.cn/nnews/215627.htm
- http://m.3g.ghtkgg.cn/nnews/7259.htm
- http://m.3g.ghtkgg.cn/nnews/7555.htm
- http://m.3g.ghtkgg.cn/nnews/26502.htm
- http://m.3g.ghtkgg.cn/nnews/25531.htm
- http://m.3g.ghtkgg.cn/nnews/45365.htm
- http://m.3g.ghtkgg.cn/nnews/7748.htm
- http://m.3g.ghtkgg.cn/nnews/05151.htm
- http://m.3g.ghtkgg.cn/nnews/3927575.htm
- http://m.3g.ghtkgg.cn/nnews/530016.htm
- http://m.3g.ghtkgg.cn/nnews/21307.htm
- http://m.3g.ghtkgg.cn/nnews/407314.htm
- http://m.3g.ghtkgg.cn/nnews/6147098.htm
- http://m.3g.ghtkgg.cn/nnews/648739.htm
- http://m.3g.ghtkgg.cn/nnews/893862.htm
- http://m.3g.ghtkgg.cn/nnews/33724.htm
- http://m.3g.ghtkgg.cn/nnews/65854.htm
- http://m.3g.ghtkgg.cn/nnews/7356.htm
- http://m.3g.ghtkgg.cn/nnews/461503.htm
- http://m.3g.ghtkgg.cn/nnews/4389982.htm
- http://m.3g.ghtkgg.cn/nnews/480224.htm
- http://m.3g.ghtkgg.cn/nnews/087948.htm
- http://m.3g.ghtkgg.cn/nnews/9682993.htm
- http://m.3g.ghtkgg.cn/nnews/50522.htm
- http://m.3g.ghtkgg.cn/nnews/357327.htm
- http://m.3g.ghtkgg.cn/nnews/560415.htm
- http://m.3g.ghtkgg.cn/nnews/3843776.htm
- http://m.3g.ghtkgg.cn/nnews/4390.htm
- http://m.3g.ghtkgg.cn/nnews/047808.htm
- http://m.3g.ghtkgg.cn/nnews/58165.htm
- http://m.3g.ghtkgg.cn/nnews/9833.htm
- http://m.3g.ghtkgg.cn/nnews/23476.htm
- http://m.3g.ghtkgg.cn/nnews/8472637.htm
- http://m.3g.ghtkgg.cn/nnews/7723295.htm
- http://m.3g.ghtkgg.cn/nnews/60562.htm
- http://m.3g.ghtkgg.cn/nnews/5168526.htm
- http://m.3g.ghtkgg.cn/nnews/5092637.htm
- http://m.3g.ghtkgg.cn/nnews/41262.htm
- http://m.3g.ghtkgg.cn/nnews/076410.htm
- http://m.3g.ghtkgg.cn/nnews/4565.htm
- http://m.3g.ghtkgg.cn/nnews/79129.htm
- http://m.3g.ghtkgg.cn/nnews/7900902.htm
- http://m.3g.ghtkgg.cn/nnews/3831090.htm
- http://m.3g.ghtkgg.cn/nnews/0686444.htm
- http://m.3g.ghtkgg.cn/nnews/7275850.htm
- http://m.3g.ghtkgg.cn/nnews/8423076.htm
- http://m.3g.ghtkgg.cn/nnews/321803.htm
- http://m.3g.ghtkgg.cn/nnews/5919.htm
- http://m.3g.ghtkgg.cn/nnews/9228.htm
- http://m.3g.ghtkgg.cn/nnews/841405.htm
- http://m.3g.ghtkgg.cn/nnews/7663.htm
- http://m.3g.ghtkgg.cn/nnews/55035.htm
- http://m.3g.ghtkgg.cn/nnews/361459.htm
- http://m.3g.ghtkgg.cn/nnews/1468266.htm
- http://m.3g.ghtkgg.cn/nnews/0178388.htm
- http://m.3g.ghtkgg.cn/nnews/7961723.htm
- http://m.3g.ghtkgg.cn/nnews/1302393.htm
- http://m.3g.ghtkgg.cn/nnews/5930076.htm
- http://m.3g.ghtkgg.cn/nnews/58388.htm
- http://m.3g.ghtkgg.cn/nnews/3453.htm
- http://m.3g.ghtkgg.cn/nnews/7850444.htm
- http://m.3g.ghtkgg.cn/nnews/6506.htm
- http://m.3g.ghtkgg.cn/nnews/171446.htm
- http://m.3g.ghtkgg.cn/nnews/5210605.htm
- http://m.3g.ghtkgg.cn/nnews/4984779.htm
- http://m.3g.ghtkgg.cn/nnews/890789.htm
- http://m.3g.ghtkgg.cn/nnews/1074278.htm
- http://m.3g.ghtkgg.cn/nnews/4355134.htm
- http://m.3g.ghtkgg.cn/nnews/977998.htm
- http://m.3g.ghtkgg.cn/nnews/240300.htm
- http://m.3g.ghtkgg.cn/nnews/8488.htm
- http://m.3g.ghtkgg.cn/nnews/22476.htm
- http://m.3g.ghtkgg.cn/nnews/3780.htm
- http://m.3g.ghtkgg.cn/nnews/535958.htm
- http://m.3g.ghtkgg.cn/nnews/9787617.htm
- http://m.3g.ghtkgg.cn/nnews/9709019.htm
- http://m.3g.ghtkgg.cn/nnews/0580.htm
- http://m.3g.ghtkgg.cn/nnews/7634.htm
- http://m.3g.ghtkgg.cn/nnews/9235.htm
- http://m.3g.ghtkgg.cn/nnews/130166.htm
- http://m.3g.ghtkgg.cn/nnews/3643.htm
- http://m.3g.ghtkgg.cn/nnews/8467.htm
- http://m.3g.ghtkgg.cn/nnews/93673.htm
- http://m.3g.ghtkgg.cn/nnews/0601.htm
- http://m.3g.ghtkgg.cn/nnews/04705.htm
- http://m.3g.ghtkgg.cn/nnews/0794.htm
- http://m.3g.ghtkgg.cn/nnews/8730.htm
- http://m.3g.ghtkgg.cn/nnews/2715687.htm
- http://m.3g.ghtkgg.cn/nnews/3044.htm
- http://m.3g.ghtkgg.cn/nnews/7883192.htm
- http://m.3g.ghtkgg.cn/nnews/3033.htm
- http://m.3g.ghtkgg.cn/nnews/44447.htm
- http://m.3g.ghtkgg.cn/nnews/459761.htm
- http://m.3g.ghtkgg.cn/nnews/16735.htm
- http://m.3g.ghtkgg.cn/nnews/5350.htm
- http://m.3g.ghtkgg.cn/nnews/2175849.htm
- http://m.3g.ghtkgg.cn/nnews/305521.htm
- http://m.3g.ghtkgg.cn/nnews/5038828.htm
- http://m.3g.ghtkgg.cn/nnews/26726.htm
- http://m.3g.ghtkgg.cn/nnews/929048.htm
- http://m.3g.ghtkgg.cn/nnews/663225.htm
- http://m.3g.ghtkgg.cn/nnews/1127.htm
- http://m.3g.ghtkgg.cn/nnews/7768947.htm
- http://m.3g.ghtkgg.cn/nnews/606736.htm
- http://m.3g.ghtkgg.cn/nnews/53959.htm
- http://m.3g.ghtkgg.cn/nnews/313438.htm
- http://m.3g.ghtkgg.cn/nnews/0919.htm
- http://m.3g.ghtkgg.cn/nnews/0352937.htm
- http://m.3g.ghtkgg.cn/nnews/10365.htm
- http://m.3g.ghtkgg.cn/nnews/467725.htm
- http://m.3g.ghtkgg.cn/nnews/3070.htm
- http://m.3g.ghtkgg.cn/nnews/5810.htm
- http://m.3g.ghtkgg.cn/nnews/2651.htm
- http://m.3g.ghtkgg.cn/nnews/37672.htm
- http://m.3g.ghtkgg.cn/nnews/186615.htm
- http://m.3g.ghtkgg.cn/nnews/6959.htm
- http://m.3g.ghtkgg.cn/nnews/2671.htm
- http://m.3g.ghtkgg.cn/nnews/8548.htm
- http://m.3g.ghtkgg.cn/nnews/88348.htm
- http://m.3g.ghtkgg.cn/nnews/59255.htm
- http://m.3g.ghtkgg.cn/nnews/6856.htm
- http://m.3g.ghtkgg.cn/nnews/91468.htm
- http://m.3g.ghtkgg.cn/nnews/11784.htm
- http://m.3g.ghtkgg.cn/nnews/8925.htm
- http://m.3g.ghtkgg.cn/nnews/938175.htm
- http://m.3g.ghtkgg.cn/nnews/5175.htm
- http://m.3g.ghtkgg.cn/nnews/769247.htm
- http://m.3g.ghtkgg.cn/nnews/38976.htm
- http://m.3g.ghtkgg.cn/nnews/987762.htm
- http://m.3g.ghtkgg.cn/nnews/1260780.htm
- http://m.3g.ghtkgg.cn/nnews/0365037.htm
- http://m.3g.ghtkgg.cn/nnews/28158.htm
- http://m.3g.ghtkgg.cn/nnews/80212.htm
- http://m.3g.ghtkgg.cn/nnews/1545527.htm
- http://m.3g.ghtkgg.cn/nnews/9302.htm
- http://m.3g.ghtkgg.cn/nnews/4124.htm
- http://m.3g.ghtkgg.cn/nnews/595014.htm
- http://m.3g.ghtkgg.cn/nnews/82620.htm
- http://m.3g.ghtkgg.cn/nnews/7942501.htm
- http://m.3g.ghtkgg.cn/nnews/403522.htm
- http://m.3g.ghtkgg.cn/nnews/12214.htm
- http://m.3g.ghtkgg.cn/nnews/9878422.htm
- http://m.3g.ghtkgg.cn/nnews/9910172.htm
- http://m.3g.ghtkgg.cn/nnews/6302.htm
- http://m.3g.ghtkgg.cn/nnews/477891.htm
- http://m.3g.ghtkgg.cn/nnews/1152.htm
- http://m.3g.ghtkgg.cn/nnews/3236.htm
- http://m.3g.ghtkgg.cn/nnews/464533.htm
- http://m.3g.ghtkgg.cn/nnews/3533.htm
- http://m.3g.ghtkgg.cn/nnews/599663.htm
- http://m.3g.ghtkgg.cn/nnews/15405.htm
- http://m.3g.ghtkgg.cn/nnews/3506.htm
- http://m.3g.ghtkgg.cn/nnews/1645.htm
- http://m.3g.ghtkgg.cn/nnews/7729.htm
- http://m.3g.ghtkgg.cn/nnews/57667.htm
- http://m.3g.ghtkgg.cn/nnews/5302.htm
- http://m.3g.ghtkgg.cn/nnews/139789.htm
- http://m.3g.ghtkgg.cn/nnews/76590.htm
- http://m.3g.ghtkgg.cn/nnews/855967.htm
- http://m.3g.ghtkgg.cn/nnews/93417.htm
- http://m.3g.ghtkgg.cn/nnews/0746054.htm
- http://m.3g.ghtkgg.cn/nnews/1552673.htm
- http://m.3g.ghtkgg.cn/nnews/2856461.htm
- http://m.3g.ghtkgg.cn/nnews/1888039.htm
- http://m.3g.ghtkgg.cn/nnews/3856.htm
- http://m.3g.ghtkgg.cn/nnews/3298.htm
- http://m.3g.ghtkgg.cn/nnews/1566.htm
- http://m.3g.ghtkgg.cn/nnews/1360.htm
- http://m.3g.ghtkgg.cn/nnews/203709.htm
- http://m.3g.ghtkgg.cn/nnews/0451.htm
- http://m.3g.ghtkgg.cn/nnews/5579.htm
- http://m.3g.ghtkgg.cn/nnews/8750.htm
- http://m.3g.ghtkgg.cn/nnews/5061121.htm
- http://m.3g.ghtkgg.cn/nnews/9482796.htm
- http://m.3g.ghtkgg.cn/nnews/5004.htm
- http://m.3g.ghtkgg.cn/nnews/11736.htm
- http://m.3g.ghtkgg.cn/nnews/51429.htm
- http://m.3g.ghtkgg.cn/nnews/1383649.htm
- http://m.3g.ghtkgg.cn/nnews/841782.htm
- http://m.3g.ghtkgg.cn/nnews/630335.htm
- http://m.3g.ghtkgg.cn/nnews/9694658.htm
- http://m.3g.ghtkgg.cn/nnews/5311503.htm
- http://m.3g.ghtkgg.cn/nnews/683602.htm
- http://m.3g.ghtkgg.cn/nnews/171464.htm
- http://m.3g.ghtkgg.cn/nnews/5581789.htm
- http://m.3g.ghtkgg.cn/nnews/6216.htm
- http://m.3g.ghtkgg.cn/nnews/47964.htm
- http://m.3g.ghtkgg.cn/nnews/3652.htm
- http://m.3g.ghtkgg.cn/nnews/3926670.htm
- http://m.3g.ghtkgg.cn/nnews/1346601.htm
- http://m.3g.ghtkgg.cn/nnews/3511983.htm
- http://m.3g.ghtkgg.cn/nnews/503638.htm
- http://m.3g.ghtkgg.cn/nnews/0383.htm
- http://m.3g.ghtkgg.cn/nnews/6881133.htm
- http://m.3g.ghtkgg.cn/nnews/59162.htm
- http://m.3g.ghtkgg.cn/nnews/50720.htm
- http://m.3g.ghtkgg.cn/nnews/8575.htm
- http://m.3g.ghtkgg.cn/nnews/73688.htm
- http://m.3g.ghtkgg.cn/nnews/3941368.htm
- http://m.3g.ghtkgg.cn/nnews/931950.htm
- http://m.3g.ghtkgg.cn/nnews/4215996.htm
- http://m.3g.ghtkgg.cn/nnews/556196.htm
- http://m.3g.ghtkgg.cn/nnews/0988.htm
- http://m.3g.ghtkgg.cn/nnews/66180.htm
- http://m.3g.ghtkgg.cn/nnews/8693.htm
- http://m.3g.ghtkgg.cn/nnews/450448.htm
- http://m.3g.ghtkgg.cn/nnews/80303.htm
- http://m.3g.ghtkgg.cn/nnews/6459356.htm
- http://m.3g.ghtkgg.cn/nnews/91774.htm
- http://m.3g.ghtkgg.cn/nnews/3894.htm
- http://m.3g.ghtkgg.cn/nnews/833506.htm
- http://m.3g.ghtkgg.cn/nnews/5912020.htm
- http://m.3g.ghtkgg.cn/nnews/910203.htm
- http://m.3g.ghtkgg.cn/nnews/1431167.htm
- http://m.3g.ghtkgg.cn/nnews/9162.htm
- http://m.3g.ghtkgg.cn/nnews/6848600.htm
- http://m.3g.ghtkgg.cn/nnews/2333.htm
- http://m.3g.ghtkgg.cn/nnews/1703.htm
- http://m.3g.ghtkgg.cn/nnews/38881.htm
- http://m.3g.ghtkgg.cn/nnews/1986.htm
- http://m.3g.ghtkgg.cn/nnews/0930.htm
- http://m.3g.ghtkgg.cn/nnews/972159.htm
- http://m.3g.ghtkgg.cn/nnews/7911.htm
- http://m.3g.ghtkgg.cn/nnews/7161150.htm
- http://m.3g.ghtkgg.cn/nnews/481713.htm
- http://m.3g.ghtkgg.cn/nnews/127977.htm
- http://m.3g.ghtkgg.cn/nnews/643612.htm
- http://m.3g.ghtkgg.cn/nnews/85126.htm
- http://m.3g.ghtkgg.cn/nnews/53428.htm
- http://m.3g.ghtkgg.cn/nnews/59814.htm
- http://m.3g.ghtkgg.cn/nnews/1975.htm
- http://m.3g.ghtkgg.cn/nnews/50196.htm
- http://m.3g.ghtkgg.cn/nnews/5276.htm
- http://m.3g.ghtkgg.cn/nnews/29160.htm
- http://m.3g.ghtkgg.cn/nnews/4081573.htm
- http://m.3g.ghtkgg.cn/nnews/645722.htm
- http://m.3g.ghtkgg.cn/nnews/1343.htm
- http://m.3g.ghtkgg.cn/nnews/153470.htm
- http://m.3g.ghtkgg.cn/nnews/5496190.htm
- http://m.3g.ghtkgg.cn/nnews/409442.htm
- http://m.3g.ghtkgg.cn/nnews/2294.htm
- http://m.3g.ghtkgg.cn/nnews/7589.htm
- http://m.3g.ghtkgg.cn/nnews/9629.htm
- http://m.3g.ghtkgg.cn/nnews/2100.htm
- http://m.3g.ghtkgg.cn/nnews/40582.htm
- http://m.3g.ghtkgg.cn/nnews/24766.htm
- http://m.3g.ghtkgg.cn/nnews/0969.htm
- http://m.3g.ghtkgg.cn/nnews/820036.htm
- http://m.3g.ghtkgg.cn/nnews/541772.htm

## 项目结构

```
newslink-hub/
├── bin/                                可执行脚本目录
│   ├── import.js                       # 批量导入命令行入口
│   ├── check-links.js                  # 链接巡检命令行工具
│   └── generate-static.js              # 静态化生成构建脚本
├── config/                             配置文件目录
│   ├── default.json                    # 默认配置（端口、缓存、超时等）
│   ├── tags.json                       # 预设分类标签定义
│   └── schedule.yaml                   # 定时巡检任务配置（cron 表达式）
├── data/                               数据存储目录
│   ├── raw_links.txt                   # 原始链接池文本文件
│   ├── indexed.db                      # sqlite3 索引数据库文件
│   └── history/                        # 历史巡检记录归档
│       └── 2026-08-25.json
├── docs/                               文档目录
│   ├── user-guide/                     # 用户手册
│   ├── ops-guide/                      # 运维指南
│   ├── dev-guide/                      # 开发者文档
│   └── design/                         # 设计说明
├── src/                                源代码目录
│   ├── core/                           # 核心逻辑模块
│   │   ├── linker.js                   # 链接管理类（增删改查）
│   │   ├── checker.js                  # 可用性检测引擎
│   │   ├── parser.js                   # 元数据提取解析器
│   │   └── exporter.js                 # 导出格式转换器
│   ├── web/                            # Web 服务层
│   │   ├── app.js                      # Express 应用主入口
│   │   ├── routes/                     # 路由定义
│   │   └── views/                      # 模板视图（EJS）
│   ├── static/                         # 静态资源（CSS、JS、图片）
│   └── utils/                          # 通用工具函数
│       ├── logger.js                   # 日志封装
│       └── validator.js                # URL 校验与归一化
├── test/                               单元测试与集成测试目录
│   ├── unit/                           # 单元测试用例
│   └── fixtures/                       # 测试数据样本
├── .env.example                        环境变量模板文件
├── .gitignore                          Git 忽略规则
├── package.json                        npm 包声明文件
├── package-lock.json                   npm 依赖锁定文件
├── README.md                           项目说明文档（本文件）
├── CHANGELOG.md                        版本变更日志
├── LICENSE                             MIT 许可证文件
└── docker-compose.yml                  可选 Docker 编排文件（用于生产部署）
```

## 贡献指南

我们欢迎各类形式的贡献，包括但不限于新增链接源、改进巡检逻辑、优化文档与翻译。请遵循以下步骤提交变更：

1. 查阅 issue 列表与 project 看板，确认当前开发优先级与尚未被认领的任务。若为新增功能或较大改动，请先新建 issue 与维护者讨论方案可行性。

2. Fork 本仓库并创建本地功能分支，分支命名建议采用 `feature/功能简述` 或 `fix/问题简述` 格式。确保分支基于最新的 main 分支。

3. 编写或修改代码后，请运行完整的测试套件 `npm test`，并确保所有测试用例通过。若新增功能未覆盖测试，请补充相应的单元测试。

4. 更新文档目录下对应的手册文件，特别是当变更涉及配置项、命令行参数或 API 接口时，需同步修改 `docs/` 中的相关章节。

5. 提交 Pull Request 至 main 分支，PR 描述中请清晰说明变更目的、实现方式以及是否包含破坏性变更。维护者将在三个工作日内进行 Review。

## 常见问题

问：导入大量链接时出现内存占用过高或超时怎么办？

答：建议将原始链接文件拆分为每份不超过 5000 行的多个小文件，分批执行导入命令。也可通过 `--batch-size` 参数控制单次事务提交的记录数，默认值为 1000。若仍然遇到问题，可将 Node.js 内存上限调整为 4GB：`NODE_OPTIONS="--max-old-space-size=4096" npm run import`。

问：如何自定义链接的元数据提取规则？

答：元数据提取器位于 `src/core/parser.js`，默认使用正则表达式匹配标题与摘要。若目标站点结构特殊，可在 `config/default.json` 中的 `parser.rules` 字段增加自定义选择器（支持 CSS 选择器与 XPath）。修改后需重启服务生效。

问：静态生成的 HTML 门户如何部署到生产环境？

答：执行 `npm run build:static` 后，所有静态文件会输出到 `dist/` 目录。将该目录内容复制到任意 HTTP 服务器（如 Nginx、Apache、Caddy）的根目录即可。若需部署到对象存储（如 AWS S3、阿里云 OSS），可使用 `--output` 参数指定输出路径，然后同步至云端。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:53
