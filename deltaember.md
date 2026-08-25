# JNews Link Aggregator

JNews Link Aggregator 是一个面向移动端资讯聚合的技术资源导航项目，专注于采集、整理和索引来自 m.wap.ghtkgg.cn 域名下的深度新闻报道与专题文章。该项目为内容研究者、舆情分析人员以及移动端资讯开发者提供结构化的外链数据池，支持批量链接的版本追踪、有效性检测与分类归档。

本项目定位为技术化的外链资源汇总站，不包含爬虫实现、不存储页面内容，仅提供链接的整理规范与索引框架。目标用户包括新闻聚合应用开发者、市场情报分析师以及需要批量处理移动端新闻链接的数据工程团队。通过本项目提供的链接数据集，用户可以快速获得一批带有固定域名模式与编号规律的新闻入口，便于后续进行内容抓取、NLP 处理或趋势分析。

## 功能概览

批量链接索引管理：提供超过两百条移动端新闻链接的集中式列表，每条链接均保留原始协议与路径结构，确保可直接访问。

域名级资源过滤：所有链接均归属于同一根域名 m.wap.ghtkgg.cn，便于进行域名白名单配置或反爬策略调整。

路径编号可追溯：每个链接的 jnews 路径后跟随唯一数字编号，支持按 ID 范围进行批次筛选与去重比对。

纯静态文档输出：项目以 Markdown 形式发布，无需数据库或后端服务即可查看完整资源列表。

链接状态占位体系：预留链接有效性检查字段，用户可自行扩展为周期性健康检查工具的基础数据源。

跨平台访问兼容：所有链接采用 http 协议与移动端子域，适配手机浏览器与桌面端代理环境。

批次版本标注：明确标注当前为第 137/300 批次，方便多批次数据合并时进行版本对齐与增量更新。

## 应用场景

移动端新闻聚合测试：开发者在构建新闻聚合应用时，可将本列表作为测试数据源，验证解析器对不同编号格式的兼容性，以及页面在 WebView 中的渲染表现。

舆情分析样本采集：市场分析团队可使用这批链接作为起始种子，批量获取特定时间段或主题下的移动端报道内容，用于情感分析或热点词频统计。

链接稳定性监测：运维人员可定期对比本列表与线上实际可访问状态，快速定位失效链接或重定向异常，评估源站的服务可用性。

数据工程教学案例：在数据工程或 Python 爬虫课程中，本列表可作为练习素材，供学生练习请求发送、HTML 解析、数据去重与结果导出等操作。

## 快速开始

以下命令帮助您在本地环境中快速初始化项目目录并准备数据文件。

```bash
# 克隆项目仓库到本地
git clone https://github.com/your-org/jnews-link-aggregator.git

# 进入项目根目录
cd jnews-link-aggregator

# 创建数据目录并生成链接列表文件
mkdir -p data
cat > data/links.txt << 'EOF'
http://m.wap.ghtkgg.cn/jnews/940267.htm
http://m.wap.ghtkgg.cn/jnews/941364.htm
... (此处按实际列表补全)
EOF

# 运行基础校验脚本（需 Python 3.8+）
python scripts/check_links.py --input data/links.txt --output reports/status.json
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 及以上 | 用于运行链接校验与格式化工具脚本 |
| Git | 2.25 及以上 | 用于克隆仓库和管理版本历史 |
| curl | 7.68 及以上 | 可选，用于手动发送 HTTP 请求测试链接 |
| jq | 1.6 及以上 | 可选，用于在命令行解析 JSON 格式的校验报告 |
| make | 3.81 及以上 | 可选，用于执行自动化任务如批量导出和格式检查 |
| markdownlint-cli | 0.31 及以上 | 可选，用于检查 README 及文档的 Markdown 语法规范性 |
| shellcheck | 0.7.0 及以上 | 可选，用于校验脚本中的 Shell 代码片段 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 项目总览 | README.md | 项目定位是什么、包含哪些资源、如何快速上手 |
| 链接清单 | data/links.txt | 完整的 URL 列表以纯文本形式存放，便于程序读取 |
| 校验报告 | reports/status.json | 哪些链接可正常访问、哪些返回错误码及响应时间 |
| 变更日志 | CHANGELOG.md | 每批次新增、删除或修正了哪些链接，版本演进历史 |
| 贡献指引 | CONTRIBUTING.md | 外部开发者如何提交新链接、更新描述或修复错误 |
| 许可证信息 | LICENSE | 项目的使用、分发与修改的法律许可条款 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/940267.htm
- http://m.wap.ghtkgg.cn/jnews/941364.htm
- http://m.wap.ghtkgg.cn/jnews/80203.htm
- http://m.wap.ghtkgg.cn/jnews/07735.htm
- http://m.wap.ghtkgg.cn/jnews/6977.htm
- http://m.wap.ghtkgg.cn/jnews/32613.htm
- http://m.wap.ghtkgg.cn/jnews/446015.htm
- http://m.wap.ghtkgg.cn/jnews/0787.htm
- http://m.wap.ghtkgg.cn/jnews/0026666.htm
- http://m.wap.ghtkgg.cn/jnews/2242.htm
- http://m.wap.ghtkgg.cn/jnews/5488.htm
- http://m.wap.ghtkgg.cn/jnews/1613.htm
- http://m.wap.ghtkgg.cn/jnews/17926.htm
- http://m.wap.ghtkgg.cn/jnews/3965061.htm
- http://m.wap.ghtkgg.cn/jnews/1597651.htm
- http://m.wap.ghtkgg.cn/jnews/7496903.htm
- http://m.wap.ghtkgg.cn/jnews/093723.htm
- http://m.wap.ghtkgg.cn/jnews/0051386.htm
- http://m.wap.ghtkgg.cn/jnews/79874.htm
- http://m.wap.ghtkgg.cn/jnews/665807.htm
- http://m.wap.ghtkgg.cn/jnews/40402.htm
- http://m.wap.ghtkgg.cn/jnews/9520.htm
- http://m.wap.ghtkgg.cn/jnews/18403.htm
- http://m.wap.ghtkgg.cn/jnews/2908.htm
- http://m.wap.ghtkgg.cn/jnews/07030.htm
- http://m.wap.ghtkgg.cn/jnews/80353.htm
- http://m.wap.ghtkgg.cn/jnews/270466.htm
- http://m.wap.ghtkgg.cn/jnews/6918187.htm
- http://m.wap.ghtkgg.cn/jnews/88786.htm
- http://m.wap.ghtkgg.cn/jnews/6459090.htm
- http://m.wap.ghtkgg.cn/jnews/8836.htm
- http://m.wap.ghtkgg.cn/jnews/2236.htm
- http://m.wap.ghtkgg.cn/jnews/415405.htm
- http://m.wap.ghtkgg.cn/jnews/29348.htm
- http://m.wap.ghtkgg.cn/jnews/430899.htm
- http://m.wap.ghtkgg.cn/jnews/47501.htm
- http://m.wap.ghtkgg.cn/jnews/51601.htm
- http://m.wap.ghtkgg.cn/jnews/2171.htm
- http://m.wap.ghtkgg.cn/jnews/9192.htm
- http://m.wap.ghtkgg.cn/jnews/5153.htm
- http://m.wap.ghtkgg.cn/jnews/8437930.htm
- http://m.wap.ghtkgg.cn/jnews/768409.htm
- http://m.wap.ghtkgg.cn/jnews/685991.htm
- http://m.wap.ghtkgg.cn/jnews/8271430.htm
- http://m.wap.ghtkgg.cn/jnews/0688846.htm
- http://m.wap.ghtkgg.cn/jnews/22182.htm
- http://m.wap.ghtkgg.cn/jnews/6079.htm
- http://m.wap.ghtkgg.cn/jnews/9626.htm
- http://m.wap.ghtkgg.cn/jnews/41110.htm
- http://m.wap.ghtkgg.cn/jnews/087059.htm
- http://m.wap.ghtkgg.cn/jnews/3046927.htm
- http://m.wap.ghtkgg.cn/jnews/47164.htm
- http://m.wap.ghtkgg.cn/jnews/6811.htm
- http://m.wap.ghtkgg.cn/jnews/9449138.htm
- http://m.wap.ghtkgg.cn/jnews/3842.htm
- http://m.wap.ghtkgg.cn/jnews/76455.htm
- http://m.wap.ghtkgg.cn/jnews/692235.htm
- http://m.wap.ghtkgg.cn/jnews/9946.htm
- http://m.wap.ghtkgg.cn/jnews/056107.htm
- http://m.wap.ghtkgg.cn/jnews/621045.htm
- http://m.wap.ghtkgg.cn/jnews/948346.htm
- http://m.wap.ghtkgg.cn/jnews/63362.htm
- http://m.wap.ghtkgg.cn/jnews/83414.htm
- http://m.wap.ghtkgg.cn/jnews/35981.htm
- http://m.wap.ghtkgg.cn/jnews/57048.htm
- http://m.wap.ghtkgg.cn/jnews/3162928.htm
- http://m.wap.ghtkgg.cn/jnews/93074.htm
- http://m.wap.ghtkgg.cn/jnews/67762.htm
- http://m.wap.ghtkgg.cn/jnews/285739.htm
- http://m.wap.ghtkgg.cn/jnews/28468.htm
- http://m.wap.ghtkgg.cn/jnews/8141.htm
- http://m.wap.ghtkgg.cn/jnews/8860418.htm
- http://m.wap.ghtkgg.cn/jnews/7786516.htm
- http://m.wap.ghtkgg.cn/jnews/1347.htm
- http://m.wap.ghtkgg.cn/jnews/2506.htm
- http://m.wap.ghtkgg.cn/jnews/732733.htm
- http://m.wap.ghtkgg.cn/jnews/9403972.htm
- http://m.wap.ghtkgg.cn/jnews/081806.htm
- http://m.wap.ghtkgg.cn/jnews/4648.htm
- http://m.wap.ghtkgg.cn/jnews/93218.htm
- http://m.wap.ghtkgg.cn/jnews/6878310.htm
- http://m.wap.ghtkgg.cn/jnews/03971.htm
- http://m.wap.ghtkgg.cn/jnews/983659.htm
- http://m.wap.ghtkgg.cn/jnews/2992.htm
- http://m.wap.ghtkgg.cn/jnews/24545.htm
- http://m.wap.ghtkgg.cn/jnews/9781.htm
- http://m.wap.ghtkgg.cn/jnews/0948.htm
- http://m.wap.ghtkgg.cn/jnews/5100420.htm
- http://m.wap.ghtkgg.cn/jnews/9884177.htm
- http://m.wap.ghtkgg.cn/jnews/7521150.htm
- http://m.wap.ghtkgg.cn/jnews/73618.htm
- http://m.wap.ghtkgg.cn/jnews/2969038.htm
- http://m.wap.ghtkgg.cn/jnews/10361.htm
- http://m.wap.ghtkgg.cn/jnews/6722597.htm
- http://m.wap.ghtkgg.cn/jnews/236239.htm
- http://m.wap.ghtkgg.cn/jnews/123095.htm
- http://m.wap.ghtkgg.cn/jnews/8397.htm
- http://m.wap.ghtkgg.cn/jnews/0875.htm
- http://m.wap.ghtkgg.cn/jnews/2943165.htm
- http://m.wap.ghtkgg.cn/jnews/410231.htm
- http://m.wap.ghtkgg.cn/jnews/749621.htm
- http://m.wap.ghtkgg.cn/jnews/4352450.htm
- http://m.wap.ghtkgg.cn/jnews/0933.htm
- http://m.wap.ghtkgg.cn/jnews/7778610.htm
- http://m.wap.ghtkgg.cn/jnews/8783387.htm
- http://m.wap.ghtkgg.cn/jnews/16888.htm
- http://m.wap.ghtkgg.cn/jnews/6108947.htm
- http://m.wap.ghtkgg.cn/jnews/0572.htm
- http://m.wap.ghtkgg.cn/jnews/40411.htm
- http://m.wap.ghtkgg.cn/jnews/8977.htm
- http://m.wap.ghtkgg.cn/jnews/5566.htm
- http://m.wap.ghtkgg.cn/jnews/1763478.htm
- http://m.wap.ghtkgg.cn/jnews/6643.htm
- http://m.wap.ghtkgg.cn/jnews/456783.htm
- http://m.wap.ghtkgg.cn/jnews/2240.htm
- http://m.wap.ghtkgg.cn/jnews/6057.htm
- http://m.wap.ghtkgg.cn/jnews/202309.htm
- http://m.wap.ghtkgg.cn/jnews/89069.htm
- http://m.wap.ghtkgg.cn/jnews/7639769.htm
- http://m.wap.ghtkgg.cn/jnews/9899756.htm
- http://m.wap.ghtkgg.cn/jnews/067653.htm
- http://m.wap.ghtkgg.cn/jnews/723383.htm
- http://m.wap.ghtkgg.cn/jnews/10430.htm
- http://m.wap.ghtkgg.cn/jnews/46135.htm
- http://m.wap.ghtkgg.cn/jnews/69126.htm
- http://m.wap.ghtkgg.cn/jnews/17796.htm
- http://m.wap.ghtkgg.cn/jnews/99617.htm
- http://m.wap.ghtkgg.cn/jnews/435415.htm
- http://m.wap.ghtkgg.cn/jnews/90246.htm
- http://m.wap.ghtkgg.cn/jnews/4619257.htm
- http://m.wap.ghtkgg.cn/jnews/25842.htm
- http://m.wap.ghtkgg.cn/jnews/994107.htm
- http://m.wap.ghtkgg.cn/jnews/5965.htm
- http://m.wap.ghtkgg.cn/jnews/264173.htm
- http://m.wap.ghtkgg.cn/jnews/04749.htm
- http://m.wap.ghtkgg.cn/jnews/1450897.htm
- http://m.wap.ghtkgg.cn/jnews/07376.htm
- http://m.wap.ghtkgg.cn/jnews/34387.htm
- http://m.wap.ghtkgg.cn/jnews/3953642.htm
- http://m.wap.ghtkgg.cn/jnews/826906.htm
- http://m.wap.ghtkgg.cn/jnews/79135.htm
- http://m.wap.ghtkgg.cn/jnews/5781670.htm
- http://m.wap.ghtkgg.cn/jnews/660542.htm
- http://m.wap.ghtkgg.cn/jnews/921453.htm
- http://m.wap.ghtkgg.cn/jnews/70846.htm
- http://m.wap.ghtkgg.cn/jnews/6167620.htm
- http://m.wap.ghtkgg.cn/jnews/11943.htm
- http://m.wap.ghtkgg.cn/jnews/4600164.htm
- http://m.wap.ghtkgg.cn/jnews/0592394.htm
- http://m.wap.ghtkgg.cn/jnews/352689.htm
- http://m.wap.ghtkgg.cn/jnews/17407.htm
- http://m.wap.ghtkgg.cn/jnews/9957595.htm
- http://m.wap.ghtkgg.cn/jnews/150633.htm
- http://m.wap.ghtkgg.cn/jnews/211530.htm
- http://m.wap.ghtkgg.cn/jnews/901199.htm
- http://m.wap.ghtkgg.cn/jnews/3554153.htm
- http://m.wap.ghtkgg.cn/jnews/2380845.htm
- http://m.wap.ghtkgg.cn/jnews/8859420.htm
- http://m.wap.ghtkgg.cn/jnews/300119.htm
- http://m.wap.ghtkgg.cn/jnews/75030.htm
- http://m.wap.ghtkgg.cn/jnews/7625683.htm
- http://m.wap.ghtkgg.cn/jnews/57583.htm
- http://m.wap.ghtkgg.cn/jnews/6890281.htm
- http://m.wap.ghtkgg.cn/jnews/148994.htm
- http://m.wap.ghtkgg.cn/jnews/43095.htm
- http://m.wap.ghtkgg.cn/jnews/71653.htm
- http://m.wap.ghtkgg.cn/jnews/628269.htm
- http://m.wap.ghtkgg.cn/jnews/9461.htm
- http://m.wap.ghtkgg.cn/jnews/3879210.htm
- http://m.wap.ghtkgg.cn/jnews/5848.htm
- http://m.wap.ghtkgg.cn/jnews/5396998.htm
- http://m.wap.ghtkgg.cn/jnews/18328.htm
- http://m.wap.ghtkgg.cn/jnews/9937094.htm
- http://m.wap.ghtkgg.cn/jnews/9209.htm
- http://m.wap.ghtkgg.cn/jnews/7838.htm
- http://m.wap.ghtkgg.cn/jnews/05285.htm
- http://m.wap.ghtkgg.cn/jnews/809428.htm
- http://m.wap.ghtkgg.cn/jnews/41233.htm
- http://m.wap.ghtkgg.cn/jnews/239460.htm
- http://m.wap.ghtkgg.cn/jnews/4112.htm
- http://m.wap.ghtkgg.cn/jnews/7950912.htm
- http://m.wap.ghtkgg.cn/jnews/81066.htm
- http://m.wap.ghtkgg.cn/jnews/3357433.htm
- http://m.wap.ghtkgg.cn/jnews/5569.htm
- http://m.wap.ghtkgg.cn/jnews/8855.htm
- http://m.wap.ghtkgg.cn/jnews/28495.htm
- http://m.wap.ghtkgg.cn/jnews/4755.htm
- http://m.wap.ghtkgg.cn/jnews/39968.htm
- http://m.wap.ghtkgg.cn/jnews/1548.htm
- http://m.wap.ghtkgg.cn/jnews/353293.htm
- http://m.wap.ghtkgg.cn/jnews/13961.htm
- http://m.wap.ghtkgg.cn/jnews/0660.htm
- http://m.wap.ghtkgg.cn/jnews/7187008.htm
- http://m.wap.ghtkgg.cn/jnews/139823.htm
- http://m.wap.ghtkgg.cn/jnews/06998.htm
- http://m.wap.ghtkgg.cn/jnews/35258.htm
- http://m.wap.ghtkgg.cn/jnews/19270.htm
- http://m.wap.ghtkgg.cn/jnews/67985.htm
- http://m.wap.ghtkgg.cn/jnews/931916.htm
- http://m.wap.ghtkgg.cn/jnews/0293916.htm
- http://m.wap.ghtkgg.cn/jnews/8218727.htm
- http://m.wap.ghtkgg.cn/jnews/3202795.htm
- http://m.wap.ghtkgg.cn/jnews/4973261.htm
- http://m.wap.ghtkgg.cn/jnews/023828.htm
- http://m.wap.ghtkgg.cn/jnews/60216.htm
- http://m.wap.ghtkgg.cn/jnews/7754.htm
- http://m.wap.ghtkgg.cn/jnews/845378.htm
- http://m.wap.ghtkgg.cn/jnews/043222.htm
- http://m.wap.ghtkgg.cn/jnews/4953.htm
- http://m.wap.ghtkgg.cn/jnews/8098.htm
- http://m.wap.ghtkgg.cn/jnews/3025142.htm
- http://m.wap.ghtkgg.cn/jnews/69408.htm
- http://m.wap.ghtkgg.cn/jnews/9469.htm
- http://m.wap.ghtkgg.cn/jnews/6349510.htm
- http://m.wap.ghtkgg.cn/jnews/3950534.htm
- http://m.wap.ghtkgg.cn/jnews/7817.htm
- http://m.wap.ghtkgg.cn/jnews/04738.htm
- http://m.wap.ghtkgg.cn/jnews/619241.htm
- http://m.wap.ghtkgg.cn/jnews/2409169.htm
- http://m.wap.ghtkgg.cn/jnews/2203186.htm
- http://m.wap.ghtkgg.cn/jnews/8610219.htm
- http://m.wap.ghtkgg.cn/jnews/2283242.htm
- http://m.wap.ghtkgg.cn/jnews/7142997.htm
- http://m.wap.ghtkgg.cn/jnews/20072.htm
- http://m.wap.ghtkgg.cn/jnews/24172.htm
- http://m.wap.ghtkgg.cn/jnews/39292.htm
- http://m.wap.ghtkgg.cn/jnews/853795.htm
- http://m.wap.ghtkgg.cn/jnews/9747301.htm
- http://m.wap.ghtkgg.cn/jnews/15241.htm
- http://m.wap.ghtkgg.cn/jnews/5315.htm
- http://m.wap.ghtkgg.cn/jnews/2902760.htm
- http://m.wap.ghtkgg.cn/jnews/8700388.htm
- http://m.wap.ghtkgg.cn/jnews/3350046.htm
- http://m.wap.ghtkgg.cn/jnews/1675770.htm
- http://m.wap.ghtkgg.cn/jnews/0423497.htm
- http://m.wap.ghtkgg.cn/jnews/9648776.htm
- http://m.wap.ghtkgg.cn/jnews/3756538.htm
- http://m.wap.ghtkgg.cn/jnews/90846.htm
- http://m.wap.ghtkgg.cn/jnews/916311.htm
- http://m.wap.ghtkgg.cn/jnews/2207.htm
- http://m.wap.ghtkgg.cn/jnews/2404.htm
- http://m.wap.ghtkgg.cn/jnews/58432.htm
- http://m.wap.ghtkgg.cn/jnews/4066.htm
- http://m.wap.ghtkgg.cn/jnews/066335.htm
- http://m.wap.ghtkgg.cn/jnews/7127844.htm
- http://m.wap.ghtkgg.cn/jnews/4267998.htm
- http://m.wap.ghtkgg.cn/jnews/41076.htm
- http://m.wap.ghtkgg.cn/jnews/36363.htm
- http://m.wap.ghtkgg.cn/jnews/5725071.htm
- http://m.wap.ghtkgg.cn/jnews/1298.htm
- http://m.wap.ghtkgg.cn/jnews/8490863.htm
- http://m.wap.ghtkgg.cn/jnews/424434.htm
- http://m.wap.ghtkgg.cn/jnews/13516.htm
- http://m.wap.ghtkgg.cn/jnews/08274.htm
- http://m.wap.ghtkgg.cn/jnews/6997187.htm
- http://m.wap.ghtkgg.cn/jnews/1335428.htm
- http://m.wap.ghtkgg.cn/jnews/55765.htm
- http://m.wap.ghtkgg.cn/jnews/4216438.htm
- http://m.wap.ghtkgg.cn/jnews/6955.htm
- http://m.wap.ghtkgg.cn/jnews/2762.htm
- http://m.wap.ghtkgg.cn/jnews/2979061.htm
- http://m.wap.ghtkgg.cn/jnews/322436.htm
- http://m.wap.ghtkgg.cn/jnews/9045696.htm
- http://m.wap.ghtkgg.cn/jnews/42628.htm
- http://m.wap.ghtkgg.cn/jnews/35162.htm
- http://m.wap.ghtkgg.cn/jnews/5360826.htm
- http://m.wap.ghtkgg.cn/jnews/0350.htm
- http://m.wap.ghtkgg.cn/jnews/7869.htm
- http://m.wap.ghtkgg.cn/jnews/3715.htm
- http://m.wap.ghtkgg.cn/jnews/7563.htm
- http://m.wap.ghtkgg.cn/jnews/8826681.htm
- http://m.wap.ghtkgg.cn/jnews/269245.htm
- http://m.wap.ghtkgg.cn/jnews/069096.htm
- http://m.wap.ghtkgg.cn/jnews/168232.htm
- http://m.wap.ghtkgg.cn/jnews/1522633.htm
- http://m.wap.ghtkgg.cn/jnews/6605064.htm
- http://m.wap.ghtkgg.cn/jnews/99303.htm
- http://m.wap.ghtkgg.cn/jnews/6848395.htm
- http://m.wap.ghtkgg.cn/jnews/9116.htm
- http://m.wap.ghtkgg.cn/jnews/7964.htm
- http://m.wap.ghtkgg.cn/jnews/09141.htm
- http://m.wap.ghtkgg.cn/jnews/172530.htm
- http://m.wap.ghtkgg.cn/jnews/8468537.htm
- http://m.wap.ghtkgg.cn/jnews/0094.htm
- http://m.wap.ghtkgg.cn/jnews/706989.htm
- http://m.wap.ghtkgg.cn/jnews/0606226.htm
- http://m.wap.ghtkgg.cn/jnews/0847331.htm
- http://m.wap.ghtkgg.cn/jnews/1662.htm
- http://m.wap.ghtkgg.cn/jnews/369652.htm
- http://m.wap.ghtkgg.cn/jnews/6962.htm
- http://m.wap.ghtkgg.cn/jnews/3337.htm
- http://m.wap.ghtkgg.cn/jnews/74035.htm
- http://m.wap.ghtkgg.cn/jnews/3547.htm
- http://m.wap.ghtkgg.cn/jnews/4055964.htm
- http://m.wap.ghtkgg.cn/jnews/4177.htm
- http://m.wap.ghtkgg.cn/jnews/182450.htm
- http://m.wap.ghtkgg.cn/jnews/680017.htm
- http://m.wap.ghtkgg.cn/jnews/399072.htm
- http://m.wap.ghtkgg.cn/jnews/6998752.htm
- http://m.wap.ghtkgg.cn/jnews/77285.htm

## 项目结构

```
jnews-link-aggregator/
├── data/                           # 存放原始链接数据文件
│   ├── links.txt                   # 完整的链接列表，每行一条URL
│   └── metadata.json               # 批次信息、采集时间与条目统计
├── scripts/                        # 可执行的辅助脚本目录
│   ├── check_links.py              # 批量发送HEAD请求检测链接可达性
│   ├── format_export.py            # 将links.txt转换为多种格式（CSV/JSON）
│   └── deduplicate.sh              # Shell脚本，基于awk去除重复编号条目
├── reports/                        # 生成的报告输出目录
│   ├── status.json                 # 链接健康检查结果，含状态码与响应时长
│   └── summary.md                  # 可读性较高的批次摘要报告
├── docs/                           # 扩展文档存放位置
│   ├── api_notes.md                # 关于链接结构设计与扩展字段的说明
│   └── troubleshooting.md          # 常见访问异常及网络环境配置建议
├── tests/                          # 简单单元测试或样例请求脚本
│   └── test_sample.py              # 使用pytest验证链接格式合法性
├── .gitignore                      # 忽略临时文件、缓存与本地配置文件
├── Makefile                        # 封装常用任务：check, export, clean
├── CHANGELOG.md                    # 记录每个批次的变更明细
├── CONTRIBUTING.md                 # 面向外部贡献者的操作规范
├── LICENSE                         # MIT许可证全文
└── README.md                       # 本文件，项目入口文档
```

## 贡献指南

提交新的链接批次或优化现有数据时，请遵循以下标准化流程，以确保项目的长期可维护性与数据一致性。

首先，在 GitHub 上 fork 本仓库到您的个人账号下，并克隆到本地开发环境中。创建新的分支，分支命名建议采用 `batch-{编号}` 或 `fix-{简述}` 的格式，例如 `batch-138` 或 `fix-duplicate-ids`。

其次，修改 data/links.txt 文件时，请确保每行仅包含一个完整的 URL，且不改变已有的协议头与路径格式。新增链接必须来源于 m.wap.ghtkgg.cn 域名，并验证其实际可访问性。若需删除或替换现有链接，请在 commit 信息中注明原因。

然后，运行本地的校验脚本以验证链接格式与基本网络状态。执行 `make check` 或直接运行 `python scripts/check_links.py --input data/links.txt`，确保没有输出致命错误或严重警告。如果校验失败，请修正后再提交。

之后，更新 CHANGELOG.md 文件，在顶部 "Unreleased" 或新版本标题下，使用列表形式记录本次变更的摘要，例如 "添加第138批次共计50条链接" 或 "移除编号重复的条目 12345"。

最后，向主仓库发起 Pull Request，并在描述中清晰说明本次修改的范围、测试结果以及是否影响现有功能。等待项目维护者审核，若有反馈请及时响应。合并后，您的贡献将出现在下一个正式版本中。

## 常见问题

问：为什么所有链接都使用 http 协议而不是 https？

答：原始数据源 m.wap.ghtkgg.cn 在收集期间仅支持 http 协议访问，且部分移动端网络环境对 https 支持不完善。为保持与源站的一致性，项目保留原始协议头。若您需要强制升级为 https，可使用 sed 或 awk 在本地进行批量替换，但本仓库不保证替换后的可访问性。

问：如何判断某个链接是否仍然有效？

答：项目提供了 scripts/check_links.py 脚本，该脚本使用 Python 的 requests 库发送 HEAD 请求，并记录返回的 HTTP 状态码。有效链接通常返回 200 或 301/302 重定向。您可以通过定期运行该脚本并对比 reports/status.json 的历史记录来监测链接的生命周期变化。

问：链接列表中存在重复编号怎么办？

答：本批次中每个编号均为唯一值。如果发现重复，请先确认是否由手动编辑导致。您可以使用 scripts/deduplicate.sh 脚本基于路径末尾的数字 ID 进行去重，该脚本会保留首次出现的条目并删除后续重复项。去重后请重新运行校验流程以确保数据完整性。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:05
