# WebFront Archive Project

WebFront Archive Project 是一个面向技术研究与历史资料存档的轻量级新闻外链聚合系统。该项目定位于对特定信源（m.3g.oexnr.cn）下的新闻条目进行结构化收集、索引与展示，为研究人员、历史数据爱好者以及内容分析人员提供稳定、可追溯的原始链接访问入口。

本项目不提供内容解析、全文代理或数据清洗服务，仅作为外链引用管理与导航系统运行。目标用户包括开源情报分析人员、新闻聚合站开发者、历史数据归档工程师以及需要批量引用特定信源链接的内容创作者。通过本项目，用户能够快速获取指定批次下的全部原始链接，并基于链接命名规则进行二次处理或自动化采集。

项目采用纯静态 Markdown 文档作为索引载体，所有链接保持原始信源格式，未经任何重定向、短链转换或参数追加，确保每一条引用均可直接回溯至源站。

## 功能概览

批量外链收录 支持单次收录不少于 300 条原始新闻链接，并提供批次编号管理，便于后续增量更新与版本追踪。

原始格式保留 所有链接严格以源站原始 URL 形式存储，不添加协议前缀、不省略路径参数、不进行大小写转换，确保引用链路的可复现性。

结构化工单索引 每个链接条目配合项目内唯一编号与批次标识，支持按批次、按序号、按域名进行快速检索与筛选。

纯静态文档交付 项目以 Markdown 作为唯一交付格式，无需数据库、无需后端服务、无需额外运行时环境，开箱即用。

多维度文档导航 提供按功能层面、按文档目录、按常见问题三个维度的交叉导航表格，帮助不同角色的使用者快速定位所需信息。

项目结构可视化 提供完整的 ASCII 目录树，标注每个目录与文件的职责边界，降低新贡献者的上手成本。

贡献流程标准化 通过分支管理、PR 流程、代码审查与批次校验四步流程，保证每批新增链接的准确性与完整性。

跨平台兼容性 依赖仅包括标准 POSIX 工具集与 Git，可在 Linux、macOS、Windows WSL 环境中无缝运行。

## 应用场景

历史新闻批次归档 研究人员需要对特定信源在特定时间段内的新闻条目进行批量收集时，可使用本项目作为链接索引底座。每批 300 条链接按编号顺序排列，便于与外部时间戳或爬虫日志进行交叉比对。

第三方爬虫入口管理 爬虫开发者可将本项目作为种子 URL 源，通过读取项目根目录下的资源列表，批量构造采集任务。由于所有链接均保持原始格式，爬虫无需额外编写 URL 规范化逻辑。

信源可用性监控 运维人员可基于本项目提供的链接列表，定期发起 HTTP 探活检测，统计源站响应率、状态码分布与 DNS 解析耗时，从而评估信源的稳定性与可用性。

开源文档示范项目 本项目可作为开源社区中「如何规范管理大量外链」的参考实现，展示从链接收集、文档撰写、目录组织到贡献流程的完整实践。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户请使用 WSL 或 Git Bash。

```bash
# 克隆项目仓库
git clone https://github.com/webfront-archive/webfront-archive.git
cd webfront-archive

# 安装依赖（仅需标准工具）
# 本项目依赖 git、curl、grep、awk，通常系统已预装
# 如需校验链接可访问性，可安装 curl
sudo apt-get install curl  # Debian/Ubuntu
sudo yum install curl      # RHEL/CentOS

# 运行本地索引生成脚本（可选）
# 该脚本会扫描 /resources 目录下的所有批次文件，生成 SUMMARY.md
./scripts/generate-index.sh

# 启动本地预览服务（使用 Python 内置 HTTP 服务器）
python3 -m http.server 8000
# 访问 http://localhost:8000 查看项目文档
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Git | 2.20.0 或更高 | 用于克隆仓库、分支管理、提交历史追溯 |
| Bash | 4.0 或更高 | 运行项目内所有 Shell 脚本，包括索引生成与格式校验 |
| curl | 7.68.0 或更高 | 可选依赖，用于链接可用性检测脚本 |
| grep | 3.4 或更高 | 用于文本过滤与 URL 格式校验 |
| awk | 5.0.0 或更高 | 用于批量处理资源列表的编号生成与统计 |
| Python | 3.6 或更高 | 仅用于本地预览服务器，非运行时必需 |
| markdownlint-cli | 0.31.0 或更高 | 可选，用于 Markdown 文档风格检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 项目概述 | README.md | 项目是什么、谁该使用、如何开始 |
| 批次索引 | resources/README.md | 当前已收录多少批次、每批的链接数量与编号范围 |
| 第 17 批原始数据 | resources/batch_017.md | 本批 300 条链接的完整列表及其原始格式 |
| 贡献流程 | CONTRIBUTING.md | 如何新增批次、如何提交 PR、如何通过 CI 校验 |
| 脚本工具 | scripts/ | 有哪些自动化工具、各自的功能与用法 |
| 常见问题 | FAQ.md | 链接失效怎么办、如何请求新增信源、如何报告错误 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/109812.htm
- http://m.3g.oexnr.cn/nnews/070968.htm
- http://m.3g.oexnr.cn/nnews/316905.htm
- http://m.3g.oexnr.cn/nnews/0503.htm
- http://m.3g.oexnr.cn/nnews/9057893.htm
- http://m.3g.oexnr.cn/nnews/20466.htm
- http://m.3g.oexnr.cn/nnews/999482.htm
- http://m.3g.oexnr.cn/nnews/34810.htm
- http://m.3g.oexnr.cn/nnews/7264.htm
- http://m.3g.oexnr.cn/nnews/6945.htm
- http://m.3g.oexnr.cn/nnews/634971.htm
- http://m.3g.oexnr.cn/nnews/04162.htm
- http://m.3g.oexnr.cn/nnews/7746555.htm
- http://m.3g.oexnr.cn/nnews/419657.htm
- http://m.3g.oexnr.cn/nnews/0673270.htm
- http://m.3g.oexnr.cn/nnews/0290.htm
- http://m.3g.oexnr.cn/nnews/71473.htm
- http://m.3g.oexnr.cn/nnews/2790342.htm
- http://m.3g.oexnr.cn/nnews/99832.htm
- http://m.3g.oexnr.cn/nnews/2021410.htm
- http://m.3g.oexnr.cn/nnews/5529.htm
- http://m.3g.oexnr.cn/nnews/958959.htm
- http://m.3g.oexnr.cn/nnews/2435035.htm
- http://m.3g.oexnr.cn/nnews/669080.htm
- http://m.3g.oexnr.cn/nnews/578666.htm
- http://m.3g.oexnr.cn/nnews/11592.htm
- http://m.3g.oexnr.cn/nnews/4054994.htm
- http://m.3g.oexnr.cn/nnews/586328.htm
- http://m.3g.oexnr.cn/nnews/4216.htm
- http://m.3g.oexnr.cn/nnews/6724.htm
- http://m.3g.oexnr.cn/nnews/4166084.htm
- http://m.3g.oexnr.cn/nnews/9296229.htm
- http://m.3g.oexnr.cn/nnews/324969.htm
- http://m.3g.oexnr.cn/nnews/574549.htm
- http://m.3g.oexnr.cn/nnews/0869271.htm
- http://m.3g.oexnr.cn/nnews/0623194.htm
- http://m.3g.oexnr.cn/nnews/1681720.htm
- http://m.3g.oexnr.cn/nnews/4923255.htm
- http://m.3g.oexnr.cn/nnews/025612.htm
- http://m.3g.oexnr.cn/nnews/3369.htm
- http://m.3g.oexnr.cn/nnews/259279.htm
- http://m.3g.oexnr.cn/nnews/8480.htm
- http://m.3g.oexnr.cn/nnews/8881.htm
- http://m.3g.oexnr.cn/nnews/67537.htm
- http://m.3g.oexnr.cn/nnews/59360.htm
- http://m.3g.oexnr.cn/nnews/034432.htm
- http://m.3g.oexnr.cn/nnews/7709.htm
- http://m.3g.oexnr.cn/nnews/252699.htm
- http://m.3g.oexnr.cn/nnews/501628.htm
- http://m.3g.oexnr.cn/nnews/6133186.htm
- http://m.3g.oexnr.cn/nnews/21239.htm
- http://m.3g.oexnr.cn/nnews/6908229.htm
- http://m.3g.oexnr.cn/nnews/78409.htm
- http://m.3g.oexnr.cn/nnews/9779129.htm
- http://m.3g.oexnr.cn/nnews/8226379.htm
- http://m.3g.oexnr.cn/nnews/440161.htm
- http://m.3g.oexnr.cn/nnews/64253.htm
- http://m.3g.oexnr.cn/nnews/372052.htm
- http://m.3g.oexnr.cn/nnews/8712321.htm
- http://m.3g.oexnr.cn/nnews/1310272.htm
- http://m.3g.oexnr.cn/nnews/5168502.htm
- http://m.3g.oexnr.cn/nnews/08492.htm
- http://m.3g.oexnr.cn/nnews/8407683.htm
- http://m.3g.oexnr.cn/nnews/0840945.htm
- http://m.3g.oexnr.cn/nnews/146234.htm
- http://m.3g.oexnr.cn/nnews/304225.htm
- http://m.3g.oexnr.cn/nnews/574577.htm
- http://m.3g.oexnr.cn/nnews/4421180.htm
- http://m.3g.oexnr.cn/nnews/7133696.htm
- http://m.3g.oexnr.cn/nnews/11411.htm
- http://m.3g.oexnr.cn/nnews/01104.htm
- http://m.3g.oexnr.cn/nnews/9321397.htm
- http://m.3g.oexnr.cn/nnews/683960.htm
- http://m.3g.oexnr.cn/nnews/5403619.htm
- http://m.3g.oexnr.cn/nnews/84790.htm
- http://m.3g.oexnr.cn/nnews/22100.htm
- http://m.3g.oexnr.cn/nnews/0650.htm
- http://m.3g.oexnr.cn/nnews/51489.htm
- http://m.3g.oexnr.cn/nnews/204986.htm
- http://m.3g.oexnr.cn/nnews/1342.htm
- http://m.3g.oexnr.cn/nnews/5322650.htm
- http://m.3g.oexnr.cn/nnews/4259736.htm
- http://m.3g.oexnr.cn/nnews/888851.htm
- http://m.3g.oexnr.cn/nnews/168089.htm
- http://m.3g.oexnr.cn/nnews/6565572.htm
- http://m.3g.oexnr.cn/nnews/568753.htm
- http://m.3g.oexnr.cn/nnews/764384.htm
- http://m.3g.oexnr.cn/nnews/16043.htm
- http://m.3g.oexnr.cn/nnews/76066.htm
- http://m.3g.oexnr.cn/nnews/97538.htm
- http://m.3g.oexnr.cn/nnews/8204.htm
- http://m.3g.oexnr.cn/nnews/7586.htm
- http://m.3g.oexnr.cn/nnews/226025.htm
- http://m.3g.oexnr.cn/nnews/515906.htm
- http://m.3g.oexnr.cn/nnews/9492.htm
- http://m.3g.oexnr.cn/nnews/299170.htm
- http://m.3g.oexnr.cn/nnews/45671.htm
- http://m.3g.oexnr.cn/nnews/652526.htm
- http://m.3g.oexnr.cn/nnews/923086.htm
- http://m.3g.oexnr.cn/nnews/08168.htm
- http://m.3g.oexnr.cn/nnews/57634.htm
- http://m.3g.oexnr.cn/nnews/6951189.htm
- http://m.3g.oexnr.cn/nnews/2524.htm
- http://m.3g.oexnr.cn/nnews/8023.htm
- http://m.3g.oexnr.cn/nnews/3175845.htm
- http://m.3g.oexnr.cn/nnews/33811.htm
- http://m.3g.oexnr.cn/nnews/3268.htm
- http://m.3g.oexnr.cn/nnews/723413.htm
- http://m.3g.oexnr.cn/nnews/392042.htm
- http://m.3g.oexnr.cn/nnews/45063.htm
- http://m.3g.oexnr.cn/nnews/8530409.htm
- http://m.3g.oexnr.cn/nnews/250502.htm
- http://m.3g.oexnr.cn/nnews/2821709.htm
- http://m.3g.oexnr.cn/nnews/65772.htm
- http://m.3g.oexnr.cn/nnews/1015.htm
- http://m.3g.oexnr.cn/nnews/44995.htm
- http://m.3g.oexnr.cn/nnews/45698.htm
- http://m.3g.oexnr.cn/nnews/3851517.htm
- http://m.3g.oexnr.cn/nnews/1426228.htm
- http://m.3g.oexnr.cn/nnews/18133.htm
- http://m.3g.oexnr.cn/nnews/711133.htm
- http://m.3g.oexnr.cn/nnews/09912.htm
- http://m.3g.oexnr.cn/nnews/354999.htm
- http://m.3g.oexnr.cn/nnews/9941.htm
- http://m.3g.oexnr.cn/nnews/50712.htm
- http://m.3g.oexnr.cn/nnews/492586.htm
- http://m.3g.oexnr.cn/nnews/729996.htm
- http://m.3g.oexnr.cn/nnews/405333.htm
- http://m.3g.oexnr.cn/nnews/7398.htm
- http://m.3g.oexnr.cn/nnews/4264.htm
- http://m.3g.oexnr.cn/nnews/95498.htm
- http://m.3g.oexnr.cn/nnews/0756659.htm
- http://m.3g.oexnr.cn/nnews/2281.htm
- http://m.3g.oexnr.cn/nnews/583618.htm
- http://m.3g.oexnr.cn/nnews/61758.htm
- http://m.3g.oexnr.cn/nnews/9876.htm
- http://m.3g.oexnr.cn/nnews/18793.htm
- http://m.3g.oexnr.cn/nnews/1642547.htm
- http://m.3g.oexnr.cn/nnews/69469.htm
- http://m.3g.oexnr.cn/nnews/43299.htm
- http://m.3g.oexnr.cn/nnews/98376.htm
- http://m.3g.oexnr.cn/nnews/169780.htm
- http://m.3g.oexnr.cn/nnews/2115059.htm
- http://m.3g.oexnr.cn/nnews/73367.htm
- http://m.3g.oexnr.cn/nnews/32309.htm
- http://m.3g.oexnr.cn/nnews/20590.htm
- http://m.3g.oexnr.cn/nnews/92261.htm
- http://m.3g.oexnr.cn/nnews/65275.htm
- http://m.3g.oexnr.cn/nnews/3374743.htm
- http://m.3g.oexnr.cn/nnews/75557.htm
- http://m.3g.oexnr.cn/nnews/84286.htm
- http://m.3g.oexnr.cn/nnews/180646.htm
- http://m.3g.oexnr.cn/nnews/98976.htm
- http://m.3g.oexnr.cn/nnews/8539.htm
- http://m.3g.oexnr.cn/nnews/7044.htm
- http://m.3g.oexnr.cn/nnews/50166.htm
- http://m.3g.oexnr.cn/nnews/0551806.htm
- http://m.3g.oexnr.cn/nnews/5100.htm
- http://m.3g.oexnr.cn/nnews/8161703.htm
- http://m.3g.oexnr.cn/nnews/4763.htm
- http://m.3g.oexnr.cn/nnews/32471.htm
- http://m.3g.oexnr.cn/nnews/49724.htm
- http://m.3g.oexnr.cn/nnews/9677.htm
- http://m.3g.oexnr.cn/nnews/313525.htm
- http://m.3g.oexnr.cn/nnews/689687.htm
- http://m.3g.oexnr.cn/nnews/81375.htm
- http://m.3g.oexnr.cn/nnews/203652.htm
- http://m.3g.oexnr.cn/nnews/11518.htm
- http://m.3g.oexnr.cn/nnews/03820.htm
- http://m.3g.oexnr.cn/nnews/26248.htm
- http://m.3g.oexnr.cn/nnews/6081637.htm
- http://m.3g.oexnr.cn/nnews/6946.htm
- http://m.3g.oexnr.cn/nnews/1753593.htm
- http://m.3g.oexnr.cn/nnews/841570.htm
- http://m.3g.oexnr.cn/nnews/6888.htm
- http://m.3g.oexnr.cn/nnews/551625.htm
- http://m.3g.oexnr.cn/nnews/2754.htm
- http://m.3g.oexnr.cn/nnews/02903.htm
- http://m.3g.oexnr.cn/nnews/525406.htm
- http://m.3g.oexnr.cn/nnews/3308.htm
- http://m.3g.oexnr.cn/nnews/224765.htm
- http://m.3g.oexnr.cn/nnews/658444.htm
- http://m.3g.oexnr.cn/nnews/4258287.htm
- http://m.3g.oexnr.cn/nnews/32550.htm
- http://m.3g.oexnr.cn/nnews/18604.htm
- http://m.3g.oexnr.cn/nnews/27736.htm
- http://m.3g.oexnr.cn/nnews/1832827.htm
- http://m.3g.oexnr.cn/nnews/944490.htm
- http://m.3g.oexnr.cn/nnews/55273.htm
- http://m.3g.oexnr.cn/nnews/102465.htm
- http://m.3g.oexnr.cn/nnews/77095.htm
- http://m.3g.oexnr.cn/nnews/52295.htm
- http://m.3g.oexnr.cn/nnews/46104.htm
- http://m.3g.oexnr.cn/nnews/412278.htm
- http://m.3g.oexnr.cn/nnews/102480.htm
- http://m.3g.oexnr.cn/nnews/336520.htm
- http://m.3g.oexnr.cn/nnews/4976.htm
- http://m.3g.oexnr.cn/nnews/038965.htm
- http://m.3g.oexnr.cn/nnews/25185.htm
- http://m.3g.oexnr.cn/nnews/3422002.htm
- http://m.3g.oexnr.cn/nnews/018165.htm
- http://m.3g.oexnr.cn/nnews/2132644.htm
- http://m.3g.oexnr.cn/nnews/63589.htm
- http://m.3g.oexnr.cn/nnews/1278.htm
- http://m.3g.oexnr.cn/nnews/8479606.htm
- http://m.3g.oexnr.cn/nnews/1095.htm
- http://m.3g.oexnr.cn/nnews/60930.htm
- http://m.3g.oexnr.cn/nnews/10837.htm
- http://m.3g.oexnr.cn/nnews/53896.htm
- http://m.3g.oexnr.cn/nnews/0958863.htm
- http://m.3g.oexnr.cn/nnews/65187.htm
- http://m.3g.oexnr.cn/nnews/0728563.htm
- http://m.3g.oexnr.cn/nnews/3275.htm
- http://m.3g.oexnr.cn/nnews/9136.htm
- http://m.3g.oexnr.cn/nnews/6797.htm
- http://m.3g.oexnr.cn/nnews/8537.htm
- http://m.3g.oexnr.cn/nnews/3076.htm
- http://m.3g.oexnr.cn/nnews/603636.htm
- http://m.3g.oexnr.cn/nnews/8378.htm
- http://m.3g.oexnr.cn/nnews/514359.htm
- http://m.3g.oexnr.cn/nnews/1957.htm
- http://m.3g.oexnr.cn/nnews/9934819.htm
- http://m.3g.oexnr.cn/nnews/6572808.htm
- http://m.3g.oexnr.cn/nnews/000084.htm
- http://m.3g.oexnr.cn/nnews/8387.htm
- http://m.3g.oexnr.cn/nnews/7884.htm
- http://m.3g.oexnr.cn/nnews/72752.htm
- http://m.3g.oexnr.cn/nnews/241847.htm
- http://m.3g.oexnr.cn/nnews/2480889.htm
- http://m.3g.oexnr.cn/nnews/0167.htm
- http://m.3g.oexnr.cn/nnews/9242390.htm
- http://m.3g.oexnr.cn/nnews/0972093.htm
- http://m.3g.oexnr.cn/nnews/54572.htm
- http://m.3g.oexnr.cn/nnews/51652.htm
- http://m.3g.oexnr.cn/nnews/196265.htm
- http://m.3g.oexnr.cn/nnews/597137.htm
- http://m.3g.oexnr.cn/nnews/86648.htm
- http://m.3g.oexnr.cn/nnews/4757.htm
- http://m.3g.oexnr.cn/nnews/11632.htm
- http://m.3g.oexnr.cn/nnews/63881.htm
- http://m.3g.oexnr.cn/nnews/888532.htm
- http://m.3g.oexnr.cn/nnews/4975.htm
- http://m.3g.oexnr.cn/nnews/296780.htm
- http://m.3g.oexnr.cn/nnews/486505.htm
- http://m.3g.oexnr.cn/nnews/3218976.htm
- http://m.3g.oexnr.cn/nnews/241060.htm
- http://m.3g.oexnr.cn/nnews/88679.htm
- http://m.3g.oexnr.cn/nnews/8973739.htm
- http://m.3g.oexnr.cn/nnews/6666938.htm
- http://m.3g.oexnr.cn/nnews/9573761.htm
- http://m.3g.oexnr.cn/nnews/4209.htm
- http://m.3g.oexnr.cn/nnews/6386.htm
- http://m.3g.oexnr.cn/nnews/41772.htm
- http://m.3g.oexnr.cn/nnews/470757.htm
- http://m.3g.oexnr.cn/nnews/0080342.htm
- http://m.3g.oexnr.cn/nnews/97063.htm
- http://m.3g.oexnr.cn/nnews/570718.htm
- http://m.3g.oexnr.cn/nnews/1634257.htm
- http://m.3g.oexnr.cn/nnews/5715.htm
- http://m.3g.oexnr.cn/nnews/35857.htm
- http://m.3g.oexnr.cn/nnews/6031.htm
- http://m.3g.oexnr.cn/nnews/132464.htm
- http://m.3g.oexnr.cn/nnews/5574749.htm
- http://m.3g.oexnr.cn/nnews/2657.htm
- http://m.3g.oexnr.cn/nnews/0871477.htm
- http://m.3g.oexnr.cn/nnews/532824.htm
- http://m.3g.oexnr.cn/nnews/1993517.htm
- http://m.3g.oexnr.cn/nnews/6701868.htm
- http://m.3g.oexnr.cn/nnews/577805.htm
- http://m.3g.oexnr.cn/nnews/919751.htm
- http://m.3g.oexnr.cn/nnews/0205536.htm
- http://m.3g.oexnr.cn/nnews/30709.htm
- http://m.3g.oexnr.cn/nnews/371169.htm
- http://m.3g.oexnr.cn/nnews/3402.htm
- http://m.3g.oexnr.cn/nnews/3548233.htm
- http://m.3g.oexnr.cn/nnews/42492.htm
- http://m.3g.oexnr.cn/nnews/5205.htm
- http://m.3g.oexnr.cn/nnews/4456346.htm
- http://m.3g.oexnr.cn/nnews/8058814.htm
- http://m.3g.oexnr.cn/nnews/6149593.htm
- http://m.3g.oexnr.cn/nnews/0557498.htm
- http://m.3g.oexnr.cn/nnews/05634.htm
- http://m.3g.oexnr.cn/nnews/6752.htm
- http://m.3g.oexnr.cn/nnews/5942625.htm
- http://m.3g.oexnr.cn/nnews/64991.htm
- http://m.3g.oexnr.cn/nnews/05462.htm
- http://m.3g.oexnr.cn/nnews/75079.htm
- http://m.3g.oexnr.cn/nnews/02039.htm
- http://m.3g.oexnr.cn/nnews/49838.htm
- http://m.3g.oexnr.cn/nnews/34951.htm
- http://m.3g.oexnr.cn/nnews/28654.htm
- http://m.3g.oexnr.cn/nnews/35368.htm
- http://m.3g.oexnr.cn/nnews/066987.htm
- http://m.3g.oexnr.cn/nnews/308498.htm
- http://m.3g.oexnr.cn/nnews/5491568.htm
- http://m.3g.oexnr.cn/nnews/2489.htm
- http://m.3g.oexnr.cn/nnews/00339.htm
- http://m.3g.oexnr.cn/nnews/9982.htm
- http://m.3g.oexnr.cn/nnews/74075.htm
- http://m.3g.oexnr.cn/nnews/3565529.htm

## 项目结构

```
webfront-archive/
├── README.md                         # 项目总览、快速开始与核心概念
├── CONTRIBUTING.md                   # 贡献者指南，包含分支策略与 PR 流程
├── LICENSE                           # MIT 许可证全文
├── .gitignore                        # 忽略编译产物、临时文件与 IDE 配置
├── .markdownlint.yml                 # Markdown 风格检查规则配置
├── resources/                        # 所有批次资源文件存放目录
│   ├── README.md                     # 批次索引说明，包含批次编号规则与总数统计
│   ├── batch_001.md                  # 第 1 批资源列表（示范批次）
│   ├── batch_002.md                  # 第 2 批资源列表（示范批次）
│   └── batch_017.md                  # 第 17 批资源列表（当前批次，含 300 条链接）
├── scripts/                          # 自动化脚本工具集
│   ├── generate-index.sh             # 扫描 resources/ 生成 SUMMARY 索引
│   ├── validate-urls.sh              # 校验所有 URL 格式是否符合规范
│   ├── check-duplicates.sh           # 检测跨批次重复链接
│   └── count-links.sh                # 统计每批次链接数量并输出报表
├── docs/                             # 扩展文档与设计决策记录
│   ├── architecture.md               # 项目架构设计文档
│   ├── url-format-spec.md            # URL 格式规范与处理原则
│   └── batch-workflow.md             # 批次新增与发布工作流说明
├── tests/                            # 测试脚本与测试数据
│   ├── test-validate.sh              # 单元测试：URL 校验函数
│   └── fixtures/                     # 测试用固定数据
│       └── sample-urls.txt           # 模拟链接列表用于测试
└── .github/                          # GitHub 相关配置
    └── workflows/
        └── ci.yml                    # CI 流水线：每次 PR 自动执行校验脚本
```

## 贡献指南

1.  Fork 本仓库至个人账户，并在本地克隆 Fork 后的副本。所有修改应在独立功能分支上进行，分支命名遵循 `feat/batch-xxx` 或 `fix/description` 格式。

2.  在 `resources/` 目录下新增批次文件，文件命名必须为 `batch_xxx.md`，其中 xxx 为三位数字编号（如 `batch_018.md`）。文件内每行一条 URL，严格保持原始格式，不得添加额外描述或编号前缀。

3.  提交前需在本地运行 `./scripts/validate-urls.sh` 与 `./scripts/check-duplicates.sh`，确保所有新增链接格式正确且不与历史批次重复。若校验失败，需修正后方可提交。

4.  发起 Pull Request 至主仓库的 `main` 分支，PR 标题需包含批次编号与链接数量，例如 `[batch-018] add 300 links for batch 18`。PR 描述中需附上本地校验脚本的完整输出日志。

5.  等待维护者进行代码审查与 CI 检查。CI 流水线会自动执行格式校验、重复检测与 Markdown 语法检查。审查通过后由维护者合并，合并后该批次即纳入正式索引。

## 常见问题

问：资源列表中的部分链接返回 HTTP 404 或连接超时，是否影响项目本身？

答：本项目仅作为外链索引系统，不代理、不缓存、不验证目标资源的实时可用性。链接的访问状态由源站决定，项目本身不因目标链接失效而视为缺陷。使用者可通过外部监控工具自行检测链接健康度，如需标记失效链接，可提交 Issue 说明具体 URL 与状态码，维护者将在下一批次中备注。

问：如何申请新增其他信源域名，而不仅限于 m.3g.oexnr.cn？

答：本项目当前定位于单信源深度索引，暂不支持多信源混合收录。如确有其他信源需求，请 Fork 本项目并自行修改资源目录结构。主仓库目前仅接受 m.3g.oexnr.cn 域名下的链接提交，其他域名链接将被 PR 校验脚本直接拒绝。

问：如果发现某条链接的 URL 书写有误（例如数字缺失或扩展名错误），应当如何处理？

答：请发起 Issue 详细描述错误位置与正确值，或直接提交 PR 修正对应批次文件。修正 PR 需在标题中注明 `[hotfix]`，并在描述中附上原值与修正后的对比。维护者会优先审查修复类 PR。

## 许可证

MIT License

Copyright (c) 2026 WebFront Archive Project Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
