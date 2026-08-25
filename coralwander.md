# WebLink Corpus Manager

WebLink Corpus Manager 是一个面向技术文档检索、外链监控与内容聚合场景的轻量级链接资源管理工具。该项目定位于技术团队、内容运营者与独立研究员，用于对大规模分散式 URL 资源进行结构化整理、元数据标注与状态巡检。项目不依赖复杂前端框架，以纯静态资源索引与可扩展的元数据描述文件为核心，适用于内网部署或 CI/CD 流水线中的链接资产托管。

项目目标用户包括：需要定期批量验证外链有效性的运维人员、构建垂直领域知识图谱的研究者、以及需要将分散链接统一归档为可查询数据集的内容中台团队。通过对 URL 资源的目录化梳理与状态追踪，项目帮助用户降低链接失效风险，提升资源复用效率。

## 功能概览

**批量链接导入** 支持从纯文本文件、CSV 或标准输入流中批量解析 URL，自动去重并生成初始索引记录。

**元数据自动补全** 根据 URL 路径模式与域名特征，自动提取资源类型、来源站点与预估发布时间区间。

**状态轮询与健康检查** 内置 HTTP 状态码探测与响应时间记录，支持对全部资源进行周期性的可达性验证。

**标签体系与分类检索** 允许用户为每条链接添加自定义标签（如 "official-doc"、"blog-post"、"api-ref"），并基于标签进行快速过滤。

**索引导出与集成支持** 支持将整理后的链接数据导出为 JSON、YAML 或 Markdown 表格格式，便于接入下游文档生成或监控告警系统。

**增量更新机制** 通过记录上次拉取或检查的时间戳，仅对新增或变更的资源条目执行全量处理，降低重复计算开销。

## 应用场景

**技术文档站点的外链资产托管** 技术团队可将项目 README、官网文档或博客文章中引用的所有外部链接统一托管至 WebLink Corpus Manager，通过定期健康检查提前发现死链或重定向异常，避免用户访问到失效引用。

**垂直领域知识库的构建与维护** 研究人员在收集某一技术领域（如云原生、数据库内核、前端框架）的优质文章与官方资料时，可利用该项目对数百个分散链接进行分类标注与版本记录，形成可检索、可追溯的个人知识索引。

**内容聚合平台的资源预处理** 内容中台在接入第三方 RSS 或 API 数据前，可借助该工具对原始 URL 列表进行合法性过滤、来源归类与风险标注，确保下游分发环节仅包含已验证的高质量链接。

**CI/CD 流程中的链接审计** 在自动化构建流水线中集成 WebLink Corpus Manager 作为检查步骤，对每次代码变更引入的新增外链执行合规性与可达性扫描，将问题反馈提前至开发阶段。

## 快速开始

以下指令演示如何获取项目源码、安装依赖并启动本地索引服务。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-corpus/weblink-corpus-manager.git

# 进入项目目录
cd weblink-corpus-manager

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化本地索引数据库（SQLite）
python scripts/init_db.py --db-path ./data/corpus.db

# 从示例文件导入首批链接
python scripts/import_links.py --input ./samples/seed_urls.txt --db ./data/corpus.db

# 启动健康检查轮询（单次运行）
python scripts/check_status.py --db ./data/corpus.db --timeout 5 --concurrency 10

# 运行本地 Web 仪表板（开发模式）
python app.py --host 127.0.0.1 --port 8080
```

完成上述步骤后，可通过浏览器访问 `http://127.0.0.1:8080` 查看当前资源列表与状态概览。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.11 以获得更好性能 |
| SQLite | 3.35 及以上 | 内置索引存储引擎，支持 JSON 扩展函数 |
| aiohttp | 3.9.0 及以上 | 异步 HTTP 客户端，用于并发健康检查 |
| click | 8.1.0 及以上 | 命令行交互框架，提供子命令解析能力 |
| pyyaml | 6.0 及以上 | 用于 YAML 格式的元数据配置文件读写 |
| pytest | 7.4.0 及以上 | 单元测试与集成测试框架（仅开发环境需要） |
| black | 23.0.0 及以上 | 代码格式化工具（仅开发环境需要） |
| 操作系统 | Linux / macOS / Windows WSL2 | 生产环境推荐 Debian 11 或 Ubuntu 22.04 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | docs/getting-started.md | 如何快速部署并导入第一批链接？如何理解核心数据模型？ |
| 操作手册 | docs/operation.md | 如何执行批量状态检查？如何自定义标签体系？如何导出索引快照？ |
| 配置参考 | docs/configuration.md | 环境变量、配置文件与命令行参数的具体含义及默认值说明 |
| 开发指南 | docs/development.md | 如何扩展新的元数据提取器？如何编写自定义状态校验规则？ |

## 资源列表

- http://m.blog.oexnr.cn/snews/34154.htm
- http://m.blog.oexnr.cn/snews/4878368.htm
- http://m.blog.oexnr.cn/snews/9141890.htm
- http://m.blog.oexnr.cn/snews/7896349.htm
- http://m.blog.oexnr.cn/snews/731046.htm
- http://m.blog.oexnr.cn/snews/0057063.htm
- http://m.blog.oexnr.cn/snews/7218.htm
- http://m.blog.oexnr.cn/snews/9441081.htm
- http://m.blog.oexnr.cn/snews/130166.htm
- http://m.blog.oexnr.cn/snews/831865.htm
- http://m.blog.oexnr.cn/snews/209217.htm
- http://m.blog.oexnr.cn/snews/1979.htm
- http://m.blog.oexnr.cn/snews/1810080.htm
- http://m.blog.oexnr.cn/snews/132672.htm
- http://m.blog.oexnr.cn/snews/48834.htm
- http://m.blog.oexnr.cn/snews/09325.htm
- http://m.blog.oexnr.cn/snews/424344.htm
- http://m.blog.oexnr.cn/snews/01074.htm
- http://m.blog.oexnr.cn/snews/1441143.htm
- http://m.blog.oexnr.cn/snews/9519.htm
- http://m.blog.oexnr.cn/snews/8353.htm
- http://m.blog.oexnr.cn/snews/2928.htm
- http://m.blog.oexnr.cn/snews/3219.htm
- http://m.blog.oexnr.cn/snews/584611.htm
- http://m.blog.oexnr.cn/snews/64924.htm
- http://m.blog.oexnr.cn/snews/1455.htm
- http://m.blog.oexnr.cn/snews/7107701.htm
- http://m.blog.oexnr.cn/snews/25242.htm
- http://m.blog.oexnr.cn/snews/606039.htm
- http://m.blog.oexnr.cn/snews/38682.htm
- http://m.blog.oexnr.cn/snews/7832.htm
- http://m.blog.oexnr.cn/snews/3241543.htm
- http://m.blog.oexnr.cn/snews/4551797.htm
- http://m.blog.oexnr.cn/snews/7236.htm
- http://m.blog.oexnr.cn/snews/9169.htm
- http://m.blog.oexnr.cn/snews/78574.htm
- http://m.blog.oexnr.cn/snews/0373412.htm
- http://m.blog.oexnr.cn/snews/9134575.htm
- http://m.blog.oexnr.cn/snews/4666513.htm
- http://m.blog.oexnr.cn/snews/9982.htm
- http://m.blog.oexnr.cn/snews/67684.htm
- http://m.blog.oexnr.cn/snews/313998.htm
- http://m.blog.oexnr.cn/snews/409801.htm
- http://m.blog.oexnr.cn/snews/9051744.htm
- http://m.blog.oexnr.cn/snews/5116843.htm
- http://m.blog.oexnr.cn/snews/3998.htm
- http://m.blog.oexnr.cn/snews/559218.htm
- http://m.blog.oexnr.cn/snews/6609957.htm
- http://m.blog.oexnr.cn/snews/85296.htm
- http://m.blog.oexnr.cn/snews/0283555.htm
- http://m.blog.oexnr.cn/snews/427770.htm
- http://m.blog.oexnr.cn/snews/06830.htm
- http://m.blog.oexnr.cn/snews/427968.htm
- http://m.blog.oexnr.cn/snews/814647.htm
- http://m.blog.oexnr.cn/snews/5424321.htm
- http://m.blog.oexnr.cn/snews/8555.htm
- http://m.blog.oexnr.cn/snews/1123681.htm
- http://m.blog.oexnr.cn/snews/258187.htm
- http://m.blog.oexnr.cn/snews/44458.htm
- http://m.blog.oexnr.cn/snews/350551.htm
- http://m.blog.oexnr.cn/snews/430624.htm
- http://m.blog.oexnr.cn/snews/1713.htm
- http://m.blog.oexnr.cn/snews/5854804.htm
- http://m.blog.oexnr.cn/snews/715140.htm
- http://m.blog.oexnr.cn/snews/6365030.htm
- http://m.blog.oexnr.cn/snews/95616.htm
- http://m.blog.oexnr.cn/snews/15406.htm
- http://m.blog.oexnr.cn/snews/360963.htm
- http://m.blog.oexnr.cn/snews/50196.htm
- http://m.blog.oexnr.cn/snews/2520.htm
- http://m.blog.oexnr.cn/snews/6240.htm
- http://m.blog.oexnr.cn/snews/4706.htm
- http://m.blog.oexnr.cn/snews/4604.htm
- http://m.blog.oexnr.cn/snews/791478.htm
- http://m.blog.oexnr.cn/snews/1718.htm
- http://m.blog.oexnr.cn/snews/2254.htm
- http://m.blog.oexnr.cn/snews/4458.htm
- http://m.blog.oexnr.cn/snews/0784125.htm
- http://m.blog.oexnr.cn/snews/40371.htm
- http://m.blog.oexnr.cn/snews/136717.htm
- http://m.blog.oexnr.cn/snews/220499.htm
- http://m.blog.oexnr.cn/snews/3724.htm
- http://m.blog.oexnr.cn/snews/89176.htm
- http://m.blog.oexnr.cn/snews/8225435.htm
- http://m.blog.oexnr.cn/snews/6839.htm
- http://m.blog.oexnr.cn/snews/364311.htm
- http://m.blog.oexnr.cn/snews/1460.htm
- http://m.blog.oexnr.cn/snews/0015.htm
- http://m.blog.oexnr.cn/snews/239241.htm
- http://m.blog.oexnr.cn/snews/5224.htm
- http://m.blog.oexnr.cn/snews/6201.htm
- http://m.blog.oexnr.cn/snews/388586.htm
- http://m.blog.oexnr.cn/snews/394910.htm
- http://m.blog.oexnr.cn/snews/603623.htm
- http://m.blog.oexnr.cn/snews/186186.htm
- http://m.blog.oexnr.cn/snews/760724.htm
- http://m.blog.oexnr.cn/snews/2325283.htm
- http://m.blog.oexnr.cn/snews/29153.htm
- http://m.blog.oexnr.cn/snews/37860.htm
- http://m.blog.oexnr.cn/snews/77474.htm
- http://m.blog.oexnr.cn/snews/0239104.htm
- http://m.blog.oexnr.cn/snews/2265865.htm
- http://m.blog.oexnr.cn/snews/929482.htm
- http://m.blog.oexnr.cn/snews/0977.htm
- http://m.blog.oexnr.cn/snews/57928.htm
- http://m.blog.oexnr.cn/snews/1995434.htm
- http://m.blog.oexnr.cn/snews/926140.htm
- http://m.blog.oexnr.cn/snews/413629.htm
- http://m.blog.oexnr.cn/snews/72455.htm
- http://m.blog.oexnr.cn/snews/9301352.htm
- http://m.blog.oexnr.cn/snews/5202774.htm
- http://m.blog.oexnr.cn/snews/3134107.htm
- http://m.blog.oexnr.cn/snews/99060.htm
- http://m.blog.oexnr.cn/snews/1050691.htm
- http://m.blog.oexnr.cn/snews/754036.htm
- http://m.blog.oexnr.cn/snews/8816310.htm
- http://m.blog.oexnr.cn/snews/9774354.htm
- http://m.blog.oexnr.cn/snews/786498.htm
- http://m.blog.oexnr.cn/snews/2245.htm
- http://m.blog.oexnr.cn/snews/4159496.htm
- http://m.blog.oexnr.cn/snews/6653659.htm
- http://m.blog.oexnr.cn/snews/419500.htm
- http://m.blog.oexnr.cn/snews/9257.htm
- http://m.blog.oexnr.cn/snews/58954.htm
- http://m.blog.oexnr.cn/snews/1036995.htm
- http://m.blog.oexnr.cn/snews/5504030.htm
- http://m.blog.oexnr.cn/snews/2896806.htm
- http://m.blog.oexnr.cn/snews/8876.htm
- http://m.blog.oexnr.cn/snews/0216.htm
- http://m.blog.oexnr.cn/snews/8821284.htm
- http://m.blog.oexnr.cn/snews/39066.htm
- http://m.blog.oexnr.cn/snews/8433.htm
- http://m.blog.oexnr.cn/snews/2084138.htm
- http://m.blog.oexnr.cn/snews/0018.htm
- http://m.blog.oexnr.cn/snews/685733.htm
- http://m.blog.oexnr.cn/snews/420612.htm
- http://m.blog.oexnr.cn/snews/4185947.htm
- http://m.blog.oexnr.cn/snews/836584.htm
- http://m.blog.oexnr.cn/snews/978576.htm
- http://m.blog.oexnr.cn/snews/5879.htm
- http://m.blog.oexnr.cn/snews/5236096.htm
- http://m.blog.oexnr.cn/snews/3328810.htm
- http://m.blog.oexnr.cn/snews/732108.htm
- http://m.blog.oexnr.cn/snews/742149.htm
- http://m.blog.oexnr.cn/snews/19132.htm
- http://m.blog.oexnr.cn/snews/309450.htm
- http://m.blog.oexnr.cn/snews/173999.htm
- http://m.blog.oexnr.cn/snews/0767.htm
- http://m.blog.oexnr.cn/snews/8686361.htm
- http://m.blog.oexnr.cn/snews/20873.htm
- http://m.blog.oexnr.cn/snews/072256.htm
- http://m.blog.oexnr.cn/snews/398968.htm
- http://m.blog.oexnr.cn/snews/1638.htm
- http://m.blog.oexnr.cn/snews/6801.htm
- http://m.blog.oexnr.cn/snews/9047842.htm
- http://m.blog.oexnr.cn/snews/0706885.htm
- http://m.blog.oexnr.cn/snews/95854.htm
- http://m.blog.oexnr.cn/snews/4980.htm
- http://m.blog.oexnr.cn/snews/535900.htm
- http://m.blog.oexnr.cn/snews/7433587.htm
- http://m.blog.oexnr.cn/snews/73835.htm
- http://m.blog.oexnr.cn/snews/84725.htm
- http://m.blog.oexnr.cn/snews/803934.htm
- http://m.blog.oexnr.cn/snews/811852.htm
- http://m.blog.oexnr.cn/snews/0707484.htm
- http://m.blog.oexnr.cn/snews/6282.htm
- http://m.blog.oexnr.cn/snews/1678.htm
- http://m.blog.oexnr.cn/snews/4754606.htm
- http://m.blog.oexnr.cn/snews/289217.htm
- http://m.blog.oexnr.cn/snews/301781.htm
- http://m.blog.oexnr.cn/snews/94560.htm
- http://m.blog.oexnr.cn/snews/47179.htm
- http://m.blog.oexnr.cn/snews/8599390.htm
- http://m.blog.oexnr.cn/snews/504993.htm
- http://m.blog.oexnr.cn/snews/5479778.htm
- http://m.blog.oexnr.cn/snews/109673.htm
- http://m.blog.oexnr.cn/snews/54643.htm
- http://m.blog.oexnr.cn/snews/243094.htm
- http://m.blog.oexnr.cn/snews/6245041.htm
- http://m.blog.oexnr.cn/snews/5574.htm
- http://m.blog.oexnr.cn/snews/20370.htm
- http://m.blog.oexnr.cn/snews/5132710.htm
- http://m.blog.oexnr.cn/snews/55276.htm
- http://m.blog.oexnr.cn/snews/074517.htm
- http://m.blog.oexnr.cn/snews/5512088.htm
- http://m.blog.oexnr.cn/snews/9393773.htm
- http://m.blog.oexnr.cn/snews/99572.htm
- http://m.blog.oexnr.cn/snews/15470.htm
- http://m.blog.oexnr.cn/snews/2106.htm
- http://m.blog.oexnr.cn/snews/74269.htm
- http://m.blog.oexnr.cn/snews/90044.htm
- http://m.blog.oexnr.cn/snews/2505.htm
- http://m.blog.oexnr.cn/snews/3526113.htm
- http://m.blog.oexnr.cn/snews/98342.htm
- http://m.blog.oexnr.cn/snews/28885.htm
- http://m.blog.oexnr.cn/snews/9809.htm
- http://m.blog.oexnr.cn/snews/652327.htm
- http://m.blog.oexnr.cn/snews/6486710.htm
- http://m.blog.oexnr.cn/snews/9735726.htm
- http://m.blog.oexnr.cn/snews/1414808.htm
- http://m.blog.oexnr.cn/snews/6978240.htm
- http://m.blog.oexnr.cn/snews/5983724.htm
- http://m.blog.oexnr.cn/snews/0681.htm
- http://m.blog.oexnr.cn/snews/9966.htm
- http://m.blog.oexnr.cn/snews/150016.htm
- http://m.blog.oexnr.cn/snews/1383.htm
- http://m.blog.oexnr.cn/snews/3753098.htm
- http://m.blog.oexnr.cn/snews/1859420.htm
- http://m.blog.oexnr.cn/snews/57905.htm
- http://m.blog.oexnr.cn/snews/0112.htm
- http://m.blog.oexnr.cn/snews/2544895.htm
- http://m.blog.oexnr.cn/snews/9946.htm
- http://m.blog.oexnr.cn/snews/5471674.htm
- http://m.blog.oexnr.cn/snews/7317312.htm
- http://m.blog.oexnr.cn/snews/81978.htm
- http://m.blog.oexnr.cn/snews/9715.htm
- http://m.blog.oexnr.cn/snews/9360610.htm
- http://m.blog.oexnr.cn/snews/6212061.htm
- http://m.blog.oexnr.cn/snews/6447.htm
- http://m.blog.oexnr.cn/snews/2648.htm
- http://m.blog.oexnr.cn/snews/95959.htm
- http://m.blog.oexnr.cn/snews/57926.htm
- http://m.blog.oexnr.cn/snews/1768.htm
- http://m.blog.oexnr.cn/snews/46398.htm
- http://m.blog.oexnr.cn/snews/949643.htm
- http://m.blog.oexnr.cn/snews/3836.htm
- http://m.blog.oexnr.cn/snews/136261.htm
- http://m.blog.oexnr.cn/snews/1537711.htm
- http://m.blog.oexnr.cn/snews/73053.htm
- http://m.blog.oexnr.cn/snews/0779960.htm
- http://m.blog.oexnr.cn/snews/8207775.htm
- http://m.blog.oexnr.cn/snews/724642.htm
- http://m.blog.oexnr.cn/snews/4320910.htm
- http://m.blog.oexnr.cn/snews/0127.htm
- http://m.blog.oexnr.cn/snews/6607.htm
- http://m.blog.oexnr.cn/snews/418394.htm
- http://m.blog.oexnr.cn/snews/2353363.htm
- http://m.blog.oexnr.cn/snews/7420126.htm
- http://m.blog.oexnr.cn/snews/9683697.htm
- http://m.blog.oexnr.cn/snews/346420.htm
- http://m.blog.oexnr.cn/snews/841437.htm
- http://m.blog.oexnr.cn/snews/14159.htm
- http://m.blog.oexnr.cn/snews/1593.htm
- http://m.blog.oexnr.cn/snews/27820.htm
- http://m.blog.oexnr.cn/snews/9445.htm
- http://m.blog.oexnr.cn/snews/17025.htm
- http://m.blog.oexnr.cn/snews/1388144.htm
- http://m.blog.oexnr.cn/snews/46991.htm
- http://m.blog.oexnr.cn/snews/162653.htm
- http://m.blog.oexnr.cn/snews/540444.htm
- http://m.blog.oexnr.cn/snews/519578.htm
- http://m.blog.oexnr.cn/snews/31631.htm
- http://m.blog.oexnr.cn/snews/6168.htm
- http://m.blog.oexnr.cn/snews/23098.htm
- http://m.blog.oexnr.cn/snews/03016.htm
- http://m.blog.oexnr.cn/snews/0930163.htm
- http://m.blog.oexnr.cn/snews/28194.htm
- http://m.blog.oexnr.cn/snews/7496176.htm
- http://m.blog.oexnr.cn/snews/18021.htm
- http://m.blog.oexnr.cn/snews/6525.htm
- http://m.blog.oexnr.cn/snews/79849.htm
- http://m.blog.oexnr.cn/snews/9783226.htm
- http://m.blog.oexnr.cn/snews/191912.htm
- http://m.blog.oexnr.cn/snews/91493.htm
- http://m.blog.oexnr.cn/snews/4926095.htm
- http://m.blog.oexnr.cn/snews/7844611.htm
- http://m.blog.oexnr.cn/snews/5216.htm
- http://m.blog.oexnr.cn/snews/9466913.htm
- http://m.blog.oexnr.cn/snews/899270.htm
- http://m.blog.oexnr.cn/snews/5210278.htm
- http://m.blog.oexnr.cn/snews/2849.htm
- http://m.blog.oexnr.cn/snews/6079629.htm
- http://m.blog.oexnr.cn/snews/0284.htm
- http://m.blog.oexnr.cn/snews/022561.htm
- http://m.blog.oexnr.cn/snews/20573.htm
- http://m.blog.oexnr.cn/snews/80899.htm
- http://m.blog.oexnr.cn/snews/3273.htm
- http://m.blog.oexnr.cn/snews/7135.htm
- http://m.blog.oexnr.cn/snews/4774.htm
- http://m.blog.oexnr.cn/snews/49109.htm
- http://m.blog.oexnr.cn/snews/7589.htm
- http://m.blog.oexnr.cn/snews/699565.htm
- http://m.blog.oexnr.cn/snews/296789.htm
- http://m.blog.oexnr.cn/snews/140740.htm
- http://m.blog.oexnr.cn/snews/769903.htm
- http://m.blog.oexnr.cn/snews/0473.htm
- http://m.blog.oexnr.cn/snews/407088.htm
- http://m.blog.oexnr.cn/snews/877518.htm
- http://m.blog.oexnr.cn/snews/99963.htm
- http://m.blog.oexnr.cn/snews/5510626.htm
- http://m.blog.oexnr.cn/snews/21275.htm
- http://m.blog.oexnr.cn/snews/36859.htm
- http://m.blog.oexnr.cn/snews/15294.htm
- http://m.blog.oexnr.cn/snews/797720.htm
- http://m.blog.oexnr.cn/snews/2363470.htm
- http://m.blog.oexnr.cn/snews/6193.htm
- http://m.blog.oexnr.cn/snews/2066041.htm
- http://m.blog.oexnr.cn/snews/551682.htm
- http://m.blog.oexnr.cn/snews/3714.htm
- http://m.blog.oexnr.cn/snews/762092.htm

## 项目结构

```
weblink-corpus-manager/
├── app.py                         # Web 仪表板入口，基于 aiohttp 提供轻量级 UI 与 API
├── requirements.txt               # 生产环境依赖清单，锁定主要库版本
├── README.md                      # 项目概览与快速入门说明
├── config/
│   ├── default.yaml               # 默认配置项：轮询间隔、超时阈值、并发数
│   └── schema.json                # 元数据描述文件的 JSON Schema 校验定义
├── data/
│   ├── corpus.db                  # SQLite 索引数据库文件（首次初始化后生成）
│   └── seed_urls.txt              # 示例种子链接文件，用于导入测试
├── docs/
│   ├── getting-started.md         # 安装部署与首次使用详解
│   ├── operation.md               # 日常巡检、标签管理与导出操作指南
│   ├── configuration.md           # 所有可调参数及其影响说明
│   └── development.md             # 二次开发与插件编写指引
├── scripts/
│   ├── init_db.py                 # 初始化数据库表结构与索引
│   ├── import_links.py            # 从文本或 CSV 导入链接列表
│   ├── check_status.py            # 执行异步 HTTP 健康检查并更新状态
│   ├── export_index.py            # 导出索引为 JSON / YAML / Markdown
│   └── cleanup_duplicates.py      # 检测并合并重复条目
├── src/
│   ├── __init__.py
│   ├── corpus/
│   │   ├── __init__.py
│   │   ├── models.py              # 链接条目、标签、检查记录的数据类定义
│   │   ├── repository.py          # 数据库 CRUD 操作封装
│   │   └── indexer.py             # 链接解析、规范化与元数据提取核心逻辑
│   ├── checker/
│   │   ├── __init__.py
│   │   ├── http_client.py         # 异步 HTTP 会话与重试策略
│   │   ├── probe.py               # 单条链接状态探测与响应解析
│   │   └── scheduler.py           # 批量轮询任务调度与结果持久化
│   ├── exporter/
│   │   ├── __init__.py
│   │   ├── json_exporter.py       # JSON 格式导出器
│   │   ├── yaml_exporter.py       # YAML 格式导出器
│   │   └── markdown_exporter.py   # Markdown 表格导出器
│   └── web/
│       ├── __init__.py
│       ├── routes.py              # 仪表板路由定义
│       ├── templates/             # Jinja2 模板目录
│       └── static/                # CSS 与 JavaScript 静态资源
├── tests/
│   ├── unit/                      # 单元测试：模型、解析器、导出器
│   └── integration/               # 集成测试：数据库、HTTP 探测、端到端流程
└── .github/
    └── workflows/
        └── ci.yml                 # GitHub Actions 持续集成流水线配置
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账号，并克隆到本地开发环境。确保本地 Python 版本符合要求，且已安装所有开发依赖（见 requirements-dev.txt）。

2. 新建以 `feature/` 或 `fix/` 为前缀的特性分支，例如 `feature/add-csv-export`。所有开发工作在该分支上进行，避免直接修改 main 分支。

3. 代码变更需遵循项目既有的代码风格（由 black 与 flake8 约束），并补充相应的单元测试与集成测试。测试覆盖率不得低于 85%。

4. 提交前运行完整测试套件：`pytest tests/`，确保全部用例通过且无回归问题。同时运行 `python scripts/check_status.py --db ./data/corpus.db --dry-run` 验证核心检查流程未受影响。

5. 发起 Pull Request 到主仓库的 main 分支，并在描述中清晰说明变更动机、影响范围以及测试结果摘要。PR 将由项目维护者进行 Code Review，通过后合并。

## 常见问题

**Q：健康检查对目标服务器会造成压力吗？如何控制检查频率？**

A：项目默认采用并发数 10、超时 5 秒的配置，并通过指数退避重试策略降低重复请求。用户可通过 `config/default.yaml` 中的 `checker.concurrency` 和 `checker.interval_seconds` 字段调整并发度与最小检查间隔。对于生产环境，建议将轮询频率设置为每日一次，并避开业务高峰时段。

**Q：导入链接时，是否支持自动识别重复条目？**

A：支持。导入模块会基于 URL 的标准化形式（去除尾部斜杠、统一协议为小写、解码百分号编码）计算哈希值，并与现有索引进行对比。若发现重复，则默认跳过并记录警告日志，用户也可通过 `--update-existing` 参数强制覆盖已有条目的元数据。

**Q：索引数据库能否迁移至 PostgreSQL 或 MySQL？**

A：项目原生使用 SQLite 以降低部署门槛，但 repository 层已抽象出统一的 DAO 接口。若需迁移至其他关系型数据库，用户可参考 `src/corpus/repository.py` 中的 SQL 方言适配示例，自行实现对应数据库的连接池与 SQL 生成逻辑。社区版暂不提供官方迁移工具。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
