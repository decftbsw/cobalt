# WebLink Navigator

WebLink Navigator 是一个面向技术研究者与内容聚合场景的轻量级外链导航与资源归档系统。该项目定位于帮助个人开发者、技术团队与内容运营者快速构建结构化的外链资源库，对分散在各类新闻页面、技术博客、文档站点中的高价值链接进行统一采集、分类存储与版本追踪。项目本身不依赖复杂的前端框架，以静态资源管理与元数据索引为核心，适用于需要长期维护外部链接清单的中小型项目。

目标用户包括技术文档维护者、开源社区运营人员、数据采集工程师以及需要定期整理浏览器书签的高级用户。WebLink Navigator 提供基于目录结构的资源组织方式，支持按批次、来源、关键词对链接进行粗粒度分类，并能够生成可读性良好的 Markdown 索引页，便于直接集成到现有文档站点或静态博客中。

## 功能概览

**批次化链接管理**：支持将大量原始 URL 按批次导入系统，每一批次可独立命名、备注与归档，方便后续按时间或主题检索。

**自动去重与校验**：在录入链接时自动检测重复条目，并基于 HTTP 状态码或域名可用性进行基础的健康检查，标记失效链接。

**目录树索引生成**：根据用户配置的分类规则，自动生成层级清晰的目录树结构，并将链接分配至对应子目录，输出可视化树形索引。

**Markdown 原生输出**：所有资源列表与索引页均以标准 Markdown 格式输出，无需额外解析器即可在 GitHub、GitLab 或本地编辑器中直接预览。

**原始数据保留模式**：系统严格保留用户提供的 URL 原始格式，包括协议类型（http/https）、三级域名（www 或裸域）以及路径大小写，确保链接跳转的准确性与合规性。

**资源状态追踪**：每条链接可附加状态标签，如有效、待审、失效、更新中，便于团队协作时明确处理进度。

**轻量级配置驱动**：所有分类规则、输出路径与命名规范均通过单一配置文件管理，无需修改核心代码即可适配不同项目需求。

## 应用场景

技术博客外链整理：技术博主在撰写聚合类文章时，需要整理数十个参考链接。WebLink Navigator 可将这些链接按主题（如前端框架、后端语言、DevOps 工具）分类，并生成可直接插入博客的 Markdown 列表，节省手动排版时间。

开源项目文档资源站：开源项目维护者需要在 README 或 Wiki 中维护外部依赖、工具链、学习资料等链接集合。使用本系统可按批次管理这些链接，并在每次发版前统一检查链接有效性，避免文档中出现死链。

数据采集任务中的 URL 归档：数据采集工程师在爬取任务中会产生大量原始 URL 清单，这些链接需要被归档并附带采集时间、采集状态等元数据。WebLink Navigator 可作为轻量级归档工具，将原始链接与处理结果关联存储。

团队知识库外链治理：企业内部知识库常包含大量指向外部文档、技术标准的链接。运营人员可定期将新增链接导入系统，按部门或项目分配至不同目录，并生成索引页供全员查阅。

个人书签库迁移与去重：浏览器书签积累过多后难以维护。用户可导出书签 HTML 文件，提取其中的 URL 后导入本系统，利用自动去重与分类功能重建整洁的链接收藏体系。

## 快速开始

以下命令演示如何从 GitHub 克隆项目、安装依赖并启动本地服务。

```bash
# 克隆仓库到本地
git clone https://github.com/weblink-navigator/weblink-navigator.git

# 进入项目目录
cd weblink-navigator

# 安装 Python 依赖（推荐使用虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 执行链接导入示例（将原始 URL 列表导入至 data/raw/ 目录）
python scripts/import_links.py --source lists/batch_259.txt --batch 259

# 生成索引页与目录树
python scripts/generate_index.py --batch 259 --output docs/index.md

# 启动内置预览服务器（可选）
python -m http.server 8000 -d docs
```

完成上述步骤后，打开浏览器访问 `http://localhost:8000` 即可查看生成的索引页面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，用于执行导入、校验与生成脚本 |
| pip | 20.0 及以上 | Python 包管理工具，用于安装第三方依赖库 |
| requests | 2.25.0 及以上 | 用于发送 HTTP 请求，执行链接健康检查与状态探测 |
| PyYAML | 5.4.0 及以上 | 解析项目配置文件 config.yaml，管理分类与输出规则 |
| markdown | 3.3.0 及以上 | 将生成的索引数据渲染为标准 Markdown 格式字符串 |
| Git | 2.25.0 及以上 | 用于克隆仓库、版本管理与贡献代码提交 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide/installation.md | 如何在不同操作系统上安装与配置 WebLink Navigator |
| 用户手册 | docs/user-guide/batch-import.md | 如何导入新批次链接，支持哪些输入格式与参数选项 |
| 开发者指南 | docs/developer-guide/architecture.md | 项目的模块划分、数据流方向与扩展点设计 |
| 开发者指南 | docs/developer-guide/api-reference.md | 核心脚本的函数签名、参数说明与返回数据结构 |
| 运维参考 | docs/ops/health-check.md | 如何配置定时任务自动检查链接状态并生成报告 |
| 运维参考 | docs/ops/output-customization.md | 如何修改索引页模板、目录树样式与分类标签规则 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/82048.htm
- http://m.wap.bwbkj.cn/snews/82504.htm
- http://m.wap.bwbkj.cn/snews/603246.htm
- http://m.wap.bwbkj.cn/snews/9256744.htm
- http://m.wap.bwbkj.cn/snews/0891949.htm
- http://m.wap.bwbkj.cn/snews/9769.htm
- http://m.wap.bwbkj.cn/snews/8699.htm
- http://m.wap.bwbkj.cn/snews/288966.htm
- http://m.wap.bwbkj.cn/snews/89647.htm
- http://m.wap.bwbkj.cn/snews/87989.htm
- http://m.wap.bwbkj.cn/snews/089064.htm
- http://m.wap.bwbkj.cn/snews/80777.htm
- http://m.wap.bwbkj.cn/snews/462155.htm
- http://m.wap.bwbkj.cn/snews/7533.htm
- http://m.wap.bwbkj.cn/snews/596510.htm
- http://m.wap.bwbkj.cn/snews/97961.htm
- http://m.wap.bwbkj.cn/snews/562219.htm
- http://m.wap.bwbkj.cn/snews/6235985.htm
- http://m.wap.bwbkj.cn/snews/0138155.htm
- http://m.wap.bwbkj.cn/snews/84043.htm
- http://m.wap.bwbkj.cn/snews/889672.htm
- http://m.wap.bwbkj.cn/snews/8638112.htm
- http://m.wap.bwbkj.cn/snews/16913.htm
- http://m.wap.bwbkj.cn/snews/43991.htm
- http://m.wap.bwbkj.cn/snews/161163.htm
- http://m.wap.bwbkj.cn/snews/95790.htm
- http://m.wap.bwbkj.cn/snews/12983.htm
- http://m.wap.bwbkj.cn/snews/055471.htm
- http://m.wap.bwbkj.cn/snews/18206.htm
- http://m.wap.bwbkj.cn/snews/84810.htm
- http://m.wap.bwbkj.cn/snews/207058.htm
- http://m.wap.bwbkj.cn/snews/2924.htm
- http://m.wap.bwbkj.cn/snews/910625.htm
- http://m.wap.bwbkj.cn/snews/8205555.htm
- http://m.wap.bwbkj.cn/snews/187247.htm
- http://m.wap.bwbkj.cn/snews/287498.htm
- http://m.wap.bwbkj.cn/snews/6181075.htm
- http://m.wap.bwbkj.cn/snews/06845.htm
- http://m.wap.bwbkj.cn/snews/62405.htm
- http://m.wap.bwbkj.cn/snews/7956.htm
- http://m.wap.bwbkj.cn/snews/45898.htm
- http://m.wap.bwbkj.cn/snews/718699.htm
- http://m.wap.bwbkj.cn/snews/730516.htm
- http://m.wap.bwbkj.cn/snews/05903.htm
- http://m.wap.bwbkj.cn/snews/7052984.htm
- http://m.wap.bwbkj.cn/snews/9843593.htm
- http://m.wap.bwbkj.cn/snews/7885394.htm
- http://m.wap.bwbkj.cn/snews/5332.htm
- http://m.wap.bwbkj.cn/snews/460042.htm
- http://m.wap.bwbkj.cn/snews/58699.htm
- http://m.wap.bwbkj.cn/snews/384971.htm
- http://m.wap.bwbkj.cn/snews/374199.htm
- http://m.wap.bwbkj.cn/snews/924161.htm
- http://m.wap.bwbkj.cn/snews/2620387.htm
- http://m.wap.bwbkj.cn/snews/25391.htm
- http://m.wap.bwbkj.cn/snews/8843.htm
- http://m.wap.bwbkj.cn/snews/00849.htm
- http://m.wap.bwbkj.cn/snews/7612.htm
- http://m.wap.bwbkj.cn/snews/8237111.htm
- http://m.wap.bwbkj.cn/snews/7108996.htm
- http://m.wap.bwbkj.cn/snews/53593.htm
- http://m.wap.bwbkj.cn/snews/7699.htm
- http://m.wap.bwbkj.cn/snews/5968.htm
- http://m.wap.bwbkj.cn/snews/9532.htm
- http://m.wap.bwbkj.cn/snews/1230.htm
- http://m.wap.bwbkj.cn/snews/6246.htm
- http://m.wap.bwbkj.cn/snews/6100.htm
- http://m.wap.bwbkj.cn/snews/8243.htm
- http://m.wap.bwbkj.cn/snews/208169.htm
- http://m.wap.bwbkj.cn/snews/3295850.htm
- http://m.wap.bwbkj.cn/snews/014432.htm
- http://m.wap.bwbkj.cn/snews/6394272.htm
- http://m.wap.bwbkj.cn/snews/51952.htm
- http://m.wap.bwbkj.cn/snews/378815.htm
- http://m.wap.bwbkj.cn/snews/0485463.htm
- http://m.wap.bwbkj.cn/snews/2683403.htm
- http://m.wap.bwbkj.cn/snews/0838.htm
- http://m.wap.bwbkj.cn/snews/76878.htm
- http://m.wap.bwbkj.cn/snews/1928835.htm
- http://m.wap.bwbkj.cn/snews/444813.htm
- http://m.wap.bwbkj.cn/snews/3148804.htm
- http://m.wap.bwbkj.cn/snews/241185.htm
- http://m.wap.bwbkj.cn/snews/255617.htm
- http://m.wap.bwbkj.cn/snews/54508.htm
- http://m.wap.bwbkj.cn/snews/38830.htm
- http://m.wap.bwbkj.cn/snews/4873711.htm
- http://m.wap.bwbkj.cn/snews/1230585.htm
- http://m.wap.bwbkj.cn/snews/205614.htm
- http://m.wap.bwbkj.cn/snews/3983721.htm
- http://m.wap.bwbkj.cn/snews/5788593.htm
- http://m.wap.bwbkj.cn/snews/1085978.htm
- http://m.wap.bwbkj.cn/snews/4576.htm
- http://m.wap.bwbkj.cn/snews/038728.htm
- http://m.wap.bwbkj.cn/snews/557790.htm
- http://m.wap.bwbkj.cn/snews/5235131.htm
- http://m.wap.bwbkj.cn/snews/570437.htm
- http://m.wap.bwbkj.cn/snews/614719.htm
- http://m.wap.bwbkj.cn/snews/879442.htm
- http://m.wap.bwbkj.cn/snews/1276145.htm
- http://m.wap.bwbkj.cn/snews/149334.htm
- http://m.wap.bwbkj.cn/snews/265148.htm
- http://m.wap.bwbkj.cn/snews/658629.htm
- http://m.wap.bwbkj.cn/snews/3754244.htm
- http://m.wap.bwbkj.cn/snews/21797.htm
- http://m.wap.bwbkj.cn/snews/6293.htm
- http://m.wap.bwbkj.cn/snews/3873907.htm
- http://m.wap.bwbkj.cn/snews/48099.htm
- http://m.wap.bwbkj.cn/snews/917048.htm
- http://m.wap.bwbkj.cn/snews/4381850.htm
- http://m.wap.bwbkj.cn/snews/21671.htm
- http://m.wap.bwbkj.cn/snews/086136.htm
- http://m.wap.bwbkj.cn/snews/9611057.htm
- http://m.wap.bwbkj.cn/snews/96612.htm
- http://m.wap.bwbkj.cn/snews/8831.htm
- http://m.wap.bwbkj.cn/snews/419388.htm
- http://m.wap.bwbkj.cn/snews/0476330.htm
- http://m.wap.bwbkj.cn/snews/3179160.htm
- http://m.wap.bwbkj.cn/snews/55693.htm
- http://m.wap.bwbkj.cn/snews/798215.htm
- http://m.wap.bwbkj.cn/snews/18003.htm
- http://m.wap.bwbkj.cn/snews/5985.htm
- http://m.wap.bwbkj.cn/snews/0474.htm
- http://m.wap.bwbkj.cn/snews/1342.htm
- http://m.wap.bwbkj.cn/snews/9070.htm
- http://m.wap.bwbkj.cn/snews/5479591.htm
- http://m.wap.bwbkj.cn/snews/6863065.htm
- http://m.wap.bwbkj.cn/snews/0202.htm
- http://m.wap.bwbkj.cn/snews/4480814.htm
- http://m.wap.bwbkj.cn/snews/3969888.htm
- http://m.wap.bwbkj.cn/snews/4879785.htm
- http://m.wap.bwbkj.cn/snews/019983.htm
- http://m.wap.bwbkj.cn/snews/62314.htm
- http://m.wap.bwbkj.cn/snews/836902.htm
- http://m.wap.bwbkj.cn/snews/4969856.htm
- http://m.wap.bwbkj.cn/snews/3108766.htm
- http://m.wap.bwbkj.cn/snews/629515.htm
- http://m.wap.bwbkj.cn/snews/2489000.htm
- http://m.wap.bwbkj.cn/snews/137621.htm
- http://m.wap.bwbkj.cn/snews/5737471.htm
- http://m.wap.bwbkj.cn/snews/75909.htm
- http://m.wap.bwbkj.cn/snews/1434541.htm
- http://m.wap.bwbkj.cn/snews/3609.htm
- http://m.wap.bwbkj.cn/snews/924394.htm
- http://m.wap.bwbkj.cn/snews/95640.htm
- http://m.wap.bwbkj.cn/snews/451033.htm
- http://m.wap.bwbkj.cn/snews/6961825.htm
- http://m.wap.bwbkj.cn/snews/2212.htm
- http://m.wap.bwbkj.cn/snews/8093622.htm
- http://m.wap.bwbkj.cn/snews/1893411.htm
- http://m.wap.bwbkj.cn/snews/926671.htm
- http://m.wap.bwbkj.cn/snews/58454.htm
- http://m.wap.bwbkj.cn/snews/0891.htm
- http://m.wap.bwbkj.cn/snews/032365.htm
- http://m.wap.bwbkj.cn/snews/905231.htm
- http://m.wap.bwbkj.cn/snews/4543105.htm
- http://m.wap.bwbkj.cn/snews/76815.htm
- http://m.wap.bwbkj.cn/snews/25016.htm
- http://m.wap.bwbkj.cn/snews/3075.htm
- http://m.wap.bwbkj.cn/snews/70827.htm
- http://m.wap.bwbkj.cn/snews/843100.htm
- http://m.wap.bwbkj.cn/snews/97726.htm
- http://m.wap.bwbkj.cn/snews/41827.htm
- http://m.wap.bwbkj.cn/snews/537681.htm
- http://m.wap.bwbkj.cn/snews/28776.htm
- http://m.wap.bwbkj.cn/snews/0663.htm
- http://m.wap.bwbkj.cn/snews/4218.htm
- http://m.wap.bwbkj.cn/snews/7787.htm
- http://m.wap.bwbkj.cn/snews/078641.htm
- http://m.wap.bwbkj.cn/snews/258059.htm
- http://m.wap.bwbkj.cn/snews/8620.htm
- http://m.wap.bwbkj.cn/snews/3853079.htm
- http://m.wap.bwbkj.cn/snews/72669.htm
- http://m.wap.bwbkj.cn/snews/5274225.htm
- http://m.wap.bwbkj.cn/snews/224172.htm
- http://m.wap.bwbkj.cn/snews/2173980.htm
- http://m.wap.bwbkj.cn/snews/87384.htm
- http://m.wap.bwbkj.cn/snews/3342.htm
- http://m.wap.bwbkj.cn/snews/598904.htm
- http://m.wap.bwbkj.cn/snews/618144.htm
- http://m.wap.bwbkj.cn/snews/000162.htm
- http://m.wap.bwbkj.cn/snews/0991.htm
- http://m.wap.bwbkj.cn/snews/97502.htm
- http://m.wap.bwbkj.cn/snews/867696.htm
- http://m.wap.bwbkj.cn/snews/125827.htm
- http://m.wap.bwbkj.cn/snews/9948.htm
- http://m.wap.bwbkj.cn/snews/4660143.htm
- http://m.wap.bwbkj.cn/snews/166765.htm
- http://m.wap.bwbkj.cn/snews/333780.htm
- http://m.wap.bwbkj.cn/snews/4908.htm
- http://m.wap.bwbkj.cn/snews/77368.htm
- http://m.wap.bwbkj.cn/snews/01764.htm
- http://m.wap.bwbkj.cn/snews/8115.htm
- http://m.wap.bwbkj.cn/snews/0055.htm
- http://m.wap.bwbkj.cn/snews/048193.htm
- http://m.wap.bwbkj.cn/snews/48440.htm
- http://m.wap.bwbkj.cn/snews/04380.htm
- http://m.wap.bwbkj.cn/snews/26360.htm
- http://m.wap.bwbkj.cn/snews/413320.htm
- http://m.wap.bwbkj.cn/snews/886721.htm
- http://m.wap.bwbkj.cn/snews/4112430.htm
- http://m.wap.bwbkj.cn/snews/79471.htm
- http://m.wap.bwbkj.cn/snews/288692.htm
- http://m.wap.bwbkj.cn/snews/10691.htm
- http://m.wap.bwbkj.cn/snews/3049.htm
- http://m.wap.bwbkj.cn/snews/9727091.htm
- http://m.wap.bwbkj.cn/snews/6546330.htm
- http://m.wap.bwbkj.cn/snews/738874.htm
- http://m.wap.bwbkj.cn/snews/4109506.htm
- http://m.wap.bwbkj.cn/snews/9416.htm
- http://m.wap.bwbkj.cn/snews/171400.htm
- http://m.wap.bwbkj.cn/snews/3876.htm
- http://m.wap.bwbkj.cn/snews/7274602.htm
- http://m.wap.bwbkj.cn/snews/72485.htm
- http://m.wap.bwbkj.cn/snews/187178.htm
- http://m.wap.bwbkj.cn/snews/2104.htm
- http://m.wap.bwbkj.cn/snews/9842909.htm
- http://m.wap.bwbkj.cn/snews/32708.htm
- http://m.wap.bwbkj.cn/snews/81930.htm
- http://m.wap.bwbkj.cn/snews/034054.htm
- http://m.wap.bwbkj.cn/snews/9931276.htm
- http://m.wap.bwbkj.cn/snews/02433.htm
- http://m.wap.bwbkj.cn/snews/6518.htm
- http://m.wap.bwbkj.cn/snews/5111.htm
- http://m.wap.bwbkj.cn/snews/501184.htm
- http://m.wap.bwbkj.cn/snews/9585.htm
- http://m.wap.bwbkj.cn/snews/6327925.htm
- http://m.wap.bwbkj.cn/snews/6479564.htm
- http://m.wap.bwbkj.cn/snews/5772564.htm
- http://m.wap.bwbkj.cn/snews/545672.htm
- http://m.wap.bwbkj.cn/snews/59812.htm
- http://m.wap.bwbkj.cn/snews/53518.htm
- http://m.wap.bwbkj.cn/snews/3094729.htm
- http://m.wap.bwbkj.cn/snews/9946517.htm
- http://m.wap.bwbkj.cn/snews/82490.htm
- http://m.wap.bwbkj.cn/snews/59272.htm
- http://m.wap.bwbkj.cn/snews/52824.htm
- http://m.wap.bwbkj.cn/snews/1099139.htm
- http://m.wap.bwbkj.cn/snews/0290208.htm
- http://m.wap.bwbkj.cn/snews/649843.htm
- http://m.wap.bwbkj.cn/snews/3604761.htm
- http://m.wap.bwbkj.cn/snews/25974.htm
- http://m.wap.bwbkj.cn/snews/829124.htm
- http://m.wap.bwbkj.cn/snews/53316.htm
- http://m.wap.bwbkj.cn/snews/67710.htm
- http://m.wap.bwbkj.cn/snews/1570172.htm
- http://m.wap.bwbkj.cn/snews/4527076.htm
- http://m.wap.bwbkj.cn/snews/28113.htm
- http://m.wap.bwbkj.cn/snews/3518.htm
- http://m.wap.bwbkj.cn/snews/8462.htm
- http://m.wap.bwbkj.cn/snews/99800.htm
- http://m.wap.bwbkj.cn/snews/3840229.htm
- http://m.wap.bwbkj.cn/snews/219468.htm
- http://m.wap.bwbkj.cn/snews/811073.htm
- http://m.wap.bwbkj.cn/snews/5689855.htm
- http://m.wap.bwbkj.cn/snews/052317.htm
- http://m.wap.bwbkj.cn/snews/9570222.htm
- http://m.wap.bwbkj.cn/snews/4101.htm
- http://m.wap.bwbkj.cn/snews/282720.htm
- http://m.wap.bwbkj.cn/snews/63213.htm
- http://m.wap.bwbkj.cn/snews/59693.htm
- http://m.wap.bwbkj.cn/snews/321298.htm
- http://m.wap.bwbkj.cn/snews/71601.htm
- http://m.wap.bwbkj.cn/snews/0751.htm
- http://m.wap.bwbkj.cn/snews/375249.htm
- http://m.wap.bwbkj.cn/snews/9679494.htm
- http://m.wap.bwbkj.cn/snews/81234.htm
- http://m.wap.bwbkj.cn/snews/46044.htm
- http://m.wap.bwbkj.cn/snews/3785908.htm
- http://m.wap.bwbkj.cn/snews/66613.htm
- http://m.wap.bwbkj.cn/snews/897300.htm
- http://m.wap.bwbkj.cn/snews/5732.htm
- http://m.wap.bwbkj.cn/snews/2757.htm
- http://m.wap.bwbkj.cn/snews/4256.htm
- http://m.wap.bwbkj.cn/snews/565839.htm
- http://m.wap.bwbkj.cn/snews/2920112.htm
- http://m.wap.bwbkj.cn/snews/8163.htm
- http://m.wap.bwbkj.cn/snews/4801.htm
- http://m.wap.bwbkj.cn/snews/318067.htm
- http://m.wap.bwbkj.cn/snews/80592.htm
- http://m.wap.bwbkj.cn/snews/0166.htm
- http://m.wap.bwbkj.cn/snews/9235.htm
- http://m.wap.bwbkj.cn/snews/3939207.htm
- http://m.wap.bwbkj.cn/snews/1890.htm
- http://m.wap.bwbkj.cn/snews/2007.htm
- http://m.wap.bwbkj.cn/snews/8939.htm
- http://m.wap.bwbkj.cn/snews/9007957.htm
- http://m.wap.bwbkj.cn/snews/3626.htm
- http://m.wap.bwbkj.cn/snews/999131.htm
- http://m.wap.bwbkj.cn/snews/8906350.htm
- http://m.wap.bwbkj.cn/snews/8177.htm
- http://m.wap.bwbkj.cn/snews/3205874.htm
- http://m.wap.bwbkj.cn/snews/659557.htm
- http://m.wap.bwbkj.cn/snews/2828.htm
- http://m.wap.bwbkj.cn/snews/36312.htm
- http://m.wap.bwbkj.cn/snews/7329.htm
- http://m.wap.bwbkj.cn/snews/516211.htm
- http://m.wap.bwbkj.cn/snews/412517.htm
- http://m.wap.bwbkj.cn/snews/955080.htm
- http://m.wap.bwbkj.cn/snews/9530.htm
- http://m.wap.bwbkj.cn/snews/630960.htm

## 项目结构

```
weblink-navigator/
├── config.yaml                     # 主配置文件，定义分类规则、输出路径与批次参数
├── requirements.txt                # Python 依赖清单，包含 requests、PyYAML、markdown 等
├── scripts/                        # 核心脚本目录
│   ├── import_links.py             # 链接导入脚本，支持 txt/csv 格式，执行去重与校验
│   ├── generate_index.py           # 索引生成脚本，输出 Markdown 索引页与目录树
│   ├── health_check.py             # 链接健康检查脚本，并发探测 HTTP 状态码
│   └── utils/                      # 脚本工具模块
│       ├── validator.py            # URL 格式验证与协议规范化工具函数
│       └── file_handler.py         # 文件读写与目录创建辅助函数
├── data/                           # 数据存储目录
│   ├── raw/                        # 原始导入数据，按批次保存为 .txt 或 .csv
│   ├── parsed/                     # 解析后的结构化链接数据，附带分类标签
│   └── cache/                      # 健康检查结果缓存，减少重复网络请求
├── docs/                           # 生成文档输出目录
│   ├── index.md                    # 主索引页，包含所有批次链接的汇总列表
│   └── batches/                    # 按批次划分的独立索引页面
│       └── batch_259.md            # 第 259 批次详细页面
├── tests/                          # 单元测试与集成测试目录
│   ├── test_validator.py           # URL 验证模块的测试用例
│   └── test_import.py              # 导入流程的端到端测试
└── .gitignore                      # Git 忽略规则，排除缓存与临时文件
```

## 贡献指南

1. 复刻项目仓库至个人账户，并克隆到本地开发环境。在提交任何更改前，请确保本地已通过全部现有测试用例。

2. 新建功能分支或修复分支，命名格式建议为 `feature/简短描述` 或 `fix/问题编号`。分支应基于最新的 main 分支创建。

3. 在 `scripts/utils/` 或 `tests/` 目录下添加或修改对应代码。所有新增功能必须附带单元测试，测试覆盖率不得低于原有水平。

4. 提交代码前执行代码格式化工具（如 black 或 ruff），并确保所有 linter 警告已被处理。提交信息应遵循约定式提交规范，首行简明概括变更内容。

5. 发起合并请求至主仓库的 main 分支，并在请求描述中详细说明本次变更的目的、实现方式与影响范围。项目维护者将在 3 个工作日内进行审查。

## 常见问题

问：导入链接时提示“URL 格式不合法”，但链接在浏览器中可以正常打开。

答：系统内置的验证器会检查 URL 是否包含协议头（http:// 或 https://）。如果原始数据缺少协议头，请在导入前使用 `--fix-protocol` 参数尝试自动补全。若链接包含特殊字符或中文路径，请确认文件编码为 UTF-8 后再行导入。

问：生成索引页后，部分链接显示为“待审”状态，如何批量更新为“有效”？

答：待审状态通常表示该链接尚未经过健康检查。您可手动执行 `python scripts/health_check.py --batch 259 --workers 10` 进行并发探测，系统将根据 HTTP 响应自动更新状态标签。若需强制标记，可在配置文件中修改 `default_status` 选项。

问：如何将现有浏览器书签导出为系统支持的输入格式？

答：主流浏览器支持将书签导出为 HTML 文件。您可使用项目提供的 `scripts/convert_bookmarks.py` 辅助脚本（位于 `scripts/contrib/` 目录）将 HTML 书签转换为纯 URL 列表，再通过 `import_links.py` 导入。转换时请注意选择正确的书签导出编码。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:10
