# Oexnr News Resource Aggregator

Oexnr News Resource Aggregator 是一个面向移动端新闻资讯采集、归档与结构化检索的开源工具链项目。该项目定位于为新闻研究人员、内容聚合平台运营者以及舆情分析系统提供标准化的新闻页面元数据抽取与持久化存储方案。通过处理来自 oexnr.cn 域名下特定路径的新闻内容批次，本项目实现了从非结构化 HTML 页面到可查询、可分析的结构化数据集的转换流程。

本项目不提供面向最终读者的新闻浏览界面，而是作为数据管道中的中间层组件，专注于解决大规模新闻链接的批量抓取、去重、字段解析与版本管理问题。目标用户包括开源社区的数据工程师、学术机构的社会科学研究者以及需要构建私有新闻语料库的开发者。

## 功能概览

批量链接预取与存活检测 对输入的新闻链接列表进行并发 HEAD 请求，快速过滤无效或重定向的 URL，减少后续抓取开销。

结构化元数据抽取 从每篇新闻页面中提取标题、发布时间、正文摘要、来源作者及分类标签，支持自定义 XPath 或 CSS 选择器映射规则。

增量去重与版本追踪 基于 URL 指纹与内容哈希双重校验机制，识别已处理的新闻条目，避免重复入库，并记录每次抓取的状态码与响应时间。

多格式数据导出 支持将解析结果输出为 JSON Lines、CSV 或 Parquet 格式，便于接入数据分析工作流或数据湖存储。

可配置的重试与降级策略 针对网络波动或服务端限流，提供指数退避重试、代理轮换与超时熔断机制，保障长时间运行任务的稳定性。

任务断点续传 抓取进度定期持久化至本地 SQLite 数据库，中断后可从上次完成的链接处恢复，适用于大规模批处理场景。

容器化部署支持 提供 Dockerfile 与 docker-compose 编排示例，可快速在 Kubernetes 或单机环境中部署调度器与工作节点。

## 应用场景

舆情监测系统的数据采集层 舆情分析团队需要持续监控特定媒体来源的新闻动态。本项目可作为采集适配器，定期拉取 oexnr.cn 的新闻批次，将解析后的结构化数据推送至 Kafka 或 Elasticsearch，供下游 sentiment analysis 模块消费。

学术研究中的新闻语料构建 社会科学研究者需构建特定时间段内的新闻数据集用于内容分析或主题建模。利用本项目的批量处理能力，可快速将数百篇新闻页面转换为纯文本语料，并附带时间戳与分类信息，满足研究数据集的规范化要求。

个人或团队的知识归档工具 内容创作者或自媒体运营者希望备份自己关注来源的新闻文章，以便离线阅读或长期引用。本项目提供轻量级的本地运行模式，通过简单的命令行参数即可将指定批次的新闻保存为 Markdown 或 PDF 快照，并生成索引文件。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，需提前安装 Git 与 Python 3.9 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/oexnr-aggregator.git
cd oexnr-aggregator

# 创建并激活 Python 虚拟环境
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate

# 安装核心依赖
pip install -r requirements.txt

# 使用示例数据运行抓取任务（output 目录将生成结果文件）
python run_pipeline.py --input sample_links.json --output ./output --format jsonl
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 ~ 3.11 | 核心运行环境，低于 3.9 不支持类型注解新特性 |
| requests | 2.28.0+ | HTTP 会话管理与连接池复用 |
| lxml | 4.9.0+ | HTML 解析与 XPath 评估，性能优于 BeautifulSoup |
| sqlite3 | 3.35.0+ | 内置持久化队列与断点记录存储 |
| pytest | 7.0.0+ | 单元测试与集成测试框架（开发依赖） |
| docker | 20.10.0+ | 容器镜像构建与运行时（可选，用于生产部署） |
| redis | 6.2.0+ | 分布式任务锁与状态缓存（可选，用于多节点部署） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user_guide.md | 如何配置抓取参数、选择输出格式、调整并发数 |
| 开发指南 | /docs/development.md | 如何扩展新的解析器、添加自定义字段映射、编写单元测试 |
| API 参考 | /docs/api_reference.md | 各模块的类与方法签名、参数说明、异常类型 |
| 部署运维 | /docs/deployment.md | 如何配置 Docker 环境、设置定时任务、监控任务状态 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/1204.htm
- http://m.wap.oexnr.cn/jnews/8717068.htm
- http://m.wap.oexnr.cn/jnews/1626.htm
- http://m.wap.oexnr.cn/jnews/27508.htm
- http://m.wap.oexnr.cn/jnews/3139025.htm
- http://m.wap.oexnr.cn/jnews/826532.htm
- http://m.wap.oexnr.cn/jnews/00982.htm
- http://m.wap.oexnr.cn/jnews/5438.htm
- http://m.wap.oexnr.cn/jnews/5928909.htm
- http://m.wap.oexnr.cn/jnews/642173.htm
- http://m.wap.oexnr.cn/jnews/43900.htm
- http://m.wap.oexnr.cn/jnews/62982.htm
- http://m.wap.oexnr.cn/jnews/4353.htm
- http://m.wap.oexnr.cn/jnews/000166.htm
- http://m.wap.oexnr.cn/jnews/3270153.htm
- http://m.wap.oexnr.cn/jnews/76840.htm
- http://m.wap.oexnr.cn/jnews/251263.htm
- http://m.wap.oexnr.cn/jnews/00018.htm
- http://m.wap.oexnr.cn/jnews/84298.htm
- http://m.wap.oexnr.cn/jnews/35106.htm
- http://m.wap.oexnr.cn/jnews/5380.htm
- http://m.wap.oexnr.cn/jnews/3135200.htm
- http://m.wap.oexnr.cn/jnews/00105.htm
- http://m.wap.oexnr.cn/jnews/4932.htm
- http://m.wap.oexnr.cn/jnews/73483.htm
- http://m.wap.oexnr.cn/jnews/430862.htm
- http://m.wap.oexnr.cn/jnews/032935.htm
- http://m.wap.oexnr.cn/jnews/419467.htm
- http://m.wap.oexnr.cn/jnews/9004618.htm
- http://m.wap.oexnr.cn/jnews/976338.htm
- http://m.wap.oexnr.cn/jnews/535933.htm
- http://m.wap.oexnr.cn/jnews/603436.htm
- http://m.wap.oexnr.cn/jnews/0980091.htm
- http://m.wap.oexnr.cn/jnews/4781741.htm
- http://m.wap.oexnr.cn/jnews/278226.htm
- http://m.wap.oexnr.cn/jnews/0182331.htm
- http://m.wap.oexnr.cn/jnews/251343.htm
- http://m.wap.oexnr.cn/jnews/5191.htm
- http://m.wap.oexnr.cn/jnews/345637.htm
- http://m.wap.oexnr.cn/jnews/5638434.htm
- http://m.wap.oexnr.cn/jnews/431012.htm
- http://m.wap.oexnr.cn/jnews/9702188.htm
- http://m.wap.oexnr.cn/jnews/278576.htm
- http://m.wap.oexnr.cn/jnews/40157.htm
- http://m.wap.oexnr.cn/jnews/47439.htm
- http://m.wap.oexnr.cn/jnews/04586.htm
- http://m.wap.oexnr.cn/jnews/70167.htm
- http://m.wap.oexnr.cn/jnews/3461.htm
- http://m.wap.oexnr.cn/jnews/205851.htm
- http://m.wap.oexnr.cn/jnews/0317.htm
- http://m.wap.oexnr.cn/jnews/9831509.htm
- http://m.wap.oexnr.cn/jnews/19164.htm
- http://m.wap.oexnr.cn/jnews/0831.htm
- http://m.wap.oexnr.cn/jnews/5848228.htm
- http://m.wap.oexnr.cn/jnews/23464.htm
- http://m.wap.oexnr.cn/jnews/327225.htm
- http://m.wap.oexnr.cn/jnews/83542.htm
- http://m.wap.oexnr.cn/jnews/615192.htm
- http://m.wap.oexnr.cn/jnews/29806.htm
- http://m.wap.oexnr.cn/jnews/27140.htm
- http://m.wap.oexnr.cn/jnews/9890423.htm
- http://m.wap.oexnr.cn/jnews/30637.htm
- http://m.wap.oexnr.cn/jnews/5299060.htm
- http://m.wap.oexnr.cn/jnews/237713.htm
- http://m.wap.oexnr.cn/jnews/116397.htm
- http://m.wap.oexnr.cn/jnews/07570.htm
- http://m.wap.oexnr.cn/jnews/9037.htm
- http://m.wap.oexnr.cn/jnews/8951.htm
- http://m.wap.oexnr.cn/jnews/4084.htm
- http://m.wap.oexnr.cn/jnews/2217.htm
- http://m.wap.oexnr.cn/jnews/3522.htm
- http://m.wap.oexnr.cn/jnews/12105.htm
- http://m.wap.oexnr.cn/jnews/8933949.htm
- http://m.wap.oexnr.cn/jnews/9808047.htm
- http://m.wap.oexnr.cn/jnews/4766347.htm
- http://m.wap.oexnr.cn/jnews/5783.htm
- http://m.wap.oexnr.cn/jnews/69495.htm
- http://m.wap.oexnr.cn/jnews/295956.htm
- http://m.wap.oexnr.cn/jnews/3417.htm
- http://m.wap.oexnr.cn/jnews/1101.htm
- http://m.wap.oexnr.cn/jnews/619392.htm
- http://m.wap.oexnr.cn/jnews/90859.htm
- http://m.wap.oexnr.cn/jnews/893993.htm
- http://m.wap.oexnr.cn/jnews/7006.htm
- http://m.wap.oexnr.cn/jnews/29482.htm
- http://m.wap.oexnr.cn/jnews/720190.htm
- http://m.wap.oexnr.cn/jnews/568868.htm
- http://m.wap.oexnr.cn/jnews/3192727.htm
- http://m.wap.oexnr.cn/jnews/04903.htm
- http://m.wap.oexnr.cn/jnews/26079.htm
- http://m.wap.oexnr.cn/jnews/6690.htm
- http://m.wap.oexnr.cn/jnews/284602.htm
- http://m.wap.oexnr.cn/jnews/1456.htm
- http://m.wap.oexnr.cn/jnews/50698.htm
- http://m.wap.oexnr.cn/jnews/5609062.htm
- http://m.wap.oexnr.cn/jnews/07720.htm
- http://m.wap.oexnr.cn/jnews/7422.htm
- http://m.wap.oexnr.cn/jnews/6204.htm
- http://m.wap.oexnr.cn/jnews/28844.htm
- http://m.wap.oexnr.cn/jnews/744481.htm
- http://m.wap.oexnr.cn/jnews/28790.htm
- http://m.wap.oexnr.cn/jnews/2759.htm
- http://m.wap.oexnr.cn/jnews/6701240.htm
- http://m.wap.oexnr.cn/jnews/581824.htm
- http://m.wap.oexnr.cn/jnews/3478.htm
- http://m.wap.oexnr.cn/jnews/5782303.htm
- http://m.wap.oexnr.cn/jnews/409967.htm
- http://m.wap.oexnr.cn/jnews/5802.htm
- http://m.wap.oexnr.cn/jnews/2071559.htm
- http://m.wap.oexnr.cn/jnews/6738.htm
- http://m.wap.oexnr.cn/jnews/9386.htm
- http://m.wap.oexnr.cn/jnews/96905.htm
- http://m.wap.oexnr.cn/jnews/876205.htm
- http://m.wap.oexnr.cn/jnews/90661.htm
- http://m.wap.oexnr.cn/jnews/5821.htm
- http://m.wap.oexnr.cn/jnews/2317488.htm
- http://m.wap.oexnr.cn/jnews/18427.htm
- http://m.wap.oexnr.cn/jnews/563851.htm
- http://m.wap.oexnr.cn/jnews/662296.htm
- http://m.wap.oexnr.cn/jnews/3443.htm
- http://m.wap.oexnr.cn/jnews/93755.htm
- http://m.wap.oexnr.cn/jnews/929261.htm
- http://m.wap.oexnr.cn/jnews/7189113.htm
- http://m.wap.oexnr.cn/jnews/093124.htm
- http://m.wap.oexnr.cn/jnews/1379.htm
- http://m.wap.oexnr.cn/jnews/302807.htm
- http://m.wap.oexnr.cn/jnews/4758.htm
- http://m.wap.oexnr.cn/jnews/9333453.htm
- http://m.wap.oexnr.cn/jnews/5361.htm
- http://m.wap.oexnr.cn/jnews/1346697.htm
- http://m.wap.oexnr.cn/jnews/5925884.htm
- http://m.wap.oexnr.cn/jnews/306265.htm
- http://m.wap.oexnr.cn/jnews/6399537.htm
- http://m.wap.oexnr.cn/jnews/5567393.htm
- http://m.wap.oexnr.cn/jnews/8848.htm
- http://m.wap.oexnr.cn/jnews/197765.htm
- http://m.wap.oexnr.cn/jnews/2579996.htm
- http://m.wap.oexnr.cn/jnews/0083.htm
- http://m.wap.oexnr.cn/jnews/3580.htm
- http://m.wap.oexnr.cn/jnews/45979.htm
- http://m.wap.oexnr.cn/jnews/69748.htm
- http://m.wap.oexnr.cn/jnews/5169888.htm
- http://m.wap.oexnr.cn/jnews/29458.htm
- http://m.wap.oexnr.cn/jnews/469665.htm
- http://m.wap.oexnr.cn/jnews/023457.htm
- http://m.wap.oexnr.cn/jnews/609721.htm
- http://m.wap.oexnr.cn/jnews/9124.htm
- http://m.wap.oexnr.cn/jnews/2562873.htm
- http://m.wap.oexnr.cn/jnews/564855.htm
- http://m.wap.oexnr.cn/jnews/8900.htm
- http://m.wap.oexnr.cn/jnews/0163952.htm
- http://m.wap.oexnr.cn/jnews/241022.htm
- http://m.wap.oexnr.cn/jnews/00157.htm
- http://m.wap.oexnr.cn/jnews/7451.htm
- http://m.wap.oexnr.cn/jnews/47053.htm
- http://m.wap.oexnr.cn/jnews/90624.htm
- http://m.wap.oexnr.cn/jnews/018878.htm
- http://m.wap.oexnr.cn/jnews/0392653.htm
- http://m.wap.oexnr.cn/jnews/015976.htm
- http://m.wap.oexnr.cn/jnews/0303304.htm
- http://m.wap.oexnr.cn/jnews/7306651.htm
- http://m.wap.oexnr.cn/jnews/4661493.htm
- http://m.wap.oexnr.cn/jnews/1227927.htm
- http://m.wap.oexnr.cn/jnews/3221851.htm
- http://m.wap.oexnr.cn/jnews/685685.htm
- http://m.wap.oexnr.cn/jnews/939485.htm
- http://m.wap.oexnr.cn/jnews/876954.htm
- http://m.wap.oexnr.cn/jnews/9057.htm
- http://m.wap.oexnr.cn/jnews/953386.htm
- http://m.wap.oexnr.cn/jnews/0061381.htm
- http://m.wap.oexnr.cn/jnews/5409393.htm
- http://m.wap.oexnr.cn/jnews/90030.htm
- http://m.wap.oexnr.cn/jnews/7750631.htm
- http://m.wap.oexnr.cn/jnews/3069164.htm
- http://m.wap.oexnr.cn/jnews/039840.htm
- http://m.wap.oexnr.cn/jnews/64038.htm
- http://m.wap.oexnr.cn/jnews/0932.htm
- http://m.wap.oexnr.cn/jnews/6455.htm
- http://m.wap.oexnr.cn/jnews/67134.htm
- http://m.wap.oexnr.cn/jnews/4920508.htm
- http://m.wap.oexnr.cn/jnews/2499191.htm
- http://m.wap.oexnr.cn/jnews/648740.htm
- http://m.wap.oexnr.cn/jnews/054277.htm
- http://m.wap.oexnr.cn/jnews/880951.htm
- http://m.wap.oexnr.cn/jnews/64875.htm
- http://m.wap.oexnr.cn/jnews/209075.htm
- http://m.wap.oexnr.cn/jnews/347765.htm
- http://m.wap.oexnr.cn/jnews/860042.htm
- http://m.wap.oexnr.cn/jnews/734078.htm
- http://m.wap.oexnr.cn/jnews/3220917.htm
- http://m.wap.oexnr.cn/jnews/34202.htm
- http://m.wap.oexnr.cn/jnews/60785.htm
- http://m.wap.oexnr.cn/jnews/261344.htm
- http://m.wap.oexnr.cn/jnews/631572.htm
- http://m.wap.oexnr.cn/jnews/29188.htm
- http://m.wap.oexnr.cn/jnews/75878.htm
- http://m.wap.oexnr.cn/jnews/1816480.htm
- http://m.wap.oexnr.cn/jnews/6442294.htm
- http://m.wap.oexnr.cn/jnews/270717.htm
- http://m.wap.oexnr.cn/jnews/89964.htm
- http://m.wap.oexnr.cn/jnews/61419.htm
- http://m.wap.oexnr.cn/jnews/9580569.htm
- http://m.wap.oexnr.cn/jnews/261730.htm
- http://m.wap.oexnr.cn/jnews/8594579.htm
- http://m.wap.oexnr.cn/jnews/358491.htm
- http://m.wap.oexnr.cn/jnews/0028.htm
- http://m.wap.oexnr.cn/jnews/511479.htm
- http://m.wap.oexnr.cn/jnews/8049447.htm
- http://m.wap.oexnr.cn/jnews/533978.htm
- http://m.wap.oexnr.cn/jnews/195204.htm
- http://m.wap.oexnr.cn/jnews/7823.htm
- http://m.wap.oexnr.cn/jnews/3798166.htm
- http://m.wap.oexnr.cn/jnews/97126.htm
- http://m.wap.oexnr.cn/jnews/110431.htm
- http://m.wap.oexnr.cn/jnews/855085.htm
- http://m.wap.oexnr.cn/jnews/22457.htm
- http://m.wap.oexnr.cn/jnews/1670.htm
- http://m.wap.oexnr.cn/jnews/240459.htm
- http://m.wap.oexnr.cn/jnews/16133.htm
- http://m.wap.oexnr.cn/jnews/203521.htm
- http://m.wap.oexnr.cn/jnews/7726.htm
- http://m.wap.oexnr.cn/jnews/09200.htm
- http://m.wap.oexnr.cn/jnews/62194.htm
- http://m.wap.oexnr.cn/jnews/253001.htm
- http://m.wap.oexnr.cn/jnews/036088.htm
- http://m.wap.oexnr.cn/jnews/2766998.htm
- http://m.wap.oexnr.cn/jnews/9029.htm
- http://m.wap.oexnr.cn/jnews/0330.htm
- http://m.wap.oexnr.cn/jnews/50035.htm
- http://m.wap.oexnr.cn/jnews/33708.htm
- http://m.wap.oexnr.cn/jnews/7069029.htm
- http://m.wap.oexnr.cn/jnews/6331000.htm
- http://m.wap.oexnr.cn/jnews/9220.htm
- http://m.wap.oexnr.cn/jnews/29731.htm
- http://m.wap.oexnr.cn/jnews/8709.htm
- http://m.wap.oexnr.cn/jnews/96199.htm
- http://m.wap.oexnr.cn/jnews/339878.htm
- http://m.wap.oexnr.cn/jnews/4936.htm
- http://m.wap.oexnr.cn/jnews/1757534.htm
- http://m.wap.oexnr.cn/jnews/9298.htm
- http://m.wap.oexnr.cn/jnews/7416.htm
- http://m.wap.oexnr.cn/jnews/795231.htm
- http://m.wap.oexnr.cn/jnews/0021407.htm
- http://m.wap.oexnr.cn/jnews/9346164.htm
- http://m.wap.oexnr.cn/jnews/9110.htm
- http://m.wap.oexnr.cn/jnews/181105.htm
- http://m.wap.oexnr.cn/jnews/7996.htm
- http://m.wap.oexnr.cn/jnews/8847770.htm
- http://m.wap.oexnr.cn/jnews/7344.htm
- http://m.wap.oexnr.cn/jnews/7956785.htm
- http://m.wap.oexnr.cn/jnews/9261.htm
- http://m.wap.oexnr.cn/jnews/3934576.htm
- http://m.wap.oexnr.cn/jnews/60885.htm
- http://m.wap.oexnr.cn/jnews/33770.htm
- http://m.wap.oexnr.cn/jnews/42545.htm
- http://m.wap.oexnr.cn/jnews/4487.htm
- http://m.wap.oexnr.cn/jnews/3325.htm
- http://m.wap.oexnr.cn/jnews/84459.htm
- http://m.wap.oexnr.cn/jnews/80728.htm
- http://m.wap.oexnr.cn/jnews/330849.htm
- http://m.wap.oexnr.cn/jnews/6920.htm
- http://m.wap.oexnr.cn/jnews/6199.htm
- http://m.wap.oexnr.cn/jnews/5860016.htm
- http://m.wap.oexnr.cn/jnews/1670207.htm
- http://m.wap.oexnr.cn/jnews/0679.htm
- http://m.wap.oexnr.cn/jnews/336482.htm
- http://m.wap.oexnr.cn/jnews/814009.htm
- http://m.wap.oexnr.cn/jnews/2388.htm
- http://m.wap.oexnr.cn/jnews/234898.htm
- http://m.wap.oexnr.cn/jnews/76137.htm
- http://m.wap.oexnr.cn/jnews/0381121.htm
- http://m.wap.oexnr.cn/jnews/22899.htm
- http://m.wap.oexnr.cn/jnews/3308090.htm
- http://m.wap.oexnr.cn/jnews/9110612.htm
- http://m.wap.oexnr.cn/jnews/41682.htm
- http://m.wap.oexnr.cn/jnews/4242.htm
- http://m.wap.oexnr.cn/jnews/9588875.htm
- http://m.wap.oexnr.cn/jnews/1266732.htm
- http://m.wap.oexnr.cn/jnews/8917386.htm
- http://m.wap.oexnr.cn/jnews/2765.htm
- http://m.wap.oexnr.cn/jnews/88898.htm
- http://m.wap.oexnr.cn/jnews/8846.htm
- http://m.wap.oexnr.cn/jnews/28487.htm
- http://m.wap.oexnr.cn/jnews/8270716.htm
- http://m.wap.oexnr.cn/jnews/6818238.htm
- http://m.wap.oexnr.cn/jnews/02164.htm
- http://m.wap.oexnr.cn/jnews/879191.htm
- http://m.wap.oexnr.cn/jnews/574445.htm
- http://m.wap.oexnr.cn/jnews/61571.htm
- http://m.wap.oexnr.cn/jnews/570810.htm
- http://m.wap.oexnr.cn/jnews/3023811.htm
- http://m.wap.oexnr.cn/jnews/74294.htm
- http://m.wap.oexnr.cn/jnews/8075.htm
- http://m.wap.oexnr.cn/jnews/1188.htm
- http://m.wap.oexnr.cn/jnews/981928.htm
- http://m.wap.oexnr.cn/jnews/219995.htm
- http://m.wap.oexnr.cn/jnews/3090919.htm
- http://m.wap.oexnr.cn/jnews/005153.htm
- http://m.wap.oexnr.cn/jnews/2170.htm
- http://m.wap.oexnr.cn/jnews/41662.htm

## 项目结构

```
oexnr-aggregator/
├── run_pipeline.py                # 主入口脚本，解析命令行参数并调度执行
├── requirements.txt               # Python 依赖列表（含版本锁定）
├── Dockerfile                     # 多阶段构建镜像定义（基于 python:3.11-slim）
├── docker-compose.yml             # 本地开发环境编排（含 redis 与 sqlite 卷）
├── .github/
│   └── workflows/
│       └── ci.yml                 # GitHub Actions 持续集成流程（测试 + 代码风格）
├── src/                           # 核心源码包
│   ├── __init__.py
│   ├── fetcher/                   # 网络请求与重试逻辑模块
│   │   ├── client.py              # 封装 requests.Session，支持代理与超时
│   │   └── middleware.py          # 重试装饰器与熔断器实现
│   ├── parser/                    # 页面解析与字段映射模块
│   │   ├── extractor.py           # 基于 lxml 的 XPath 抽取引擎
│   │   └── schema.py              # 定义新闻实体的 Pydantic 模型
│   ├── storage/                   # 持久化与去重模块
│   │   ├── queue.py               # SQLite 任务队列管理
│   │   └── writer.py              # 输出 JSONL / CSV / Parquet 的写入器
│   ├── scheduler/                 # 调度与并发控制模块
│   │   ├── pool.py                # 多线程工作池与异步事件循环
│   │   └── checkpoint.py          # 进度快照与断点恢复逻辑
│   └── utils/                     # 通用工具函数
│       ├── logging.py             # 结构化日志配置（JSON 格式）
│       └── hash.py                # 内容指纹计算（SHA-256 与 Bloom Filter）
├── tests/                         # 单元测试与集成测试目录
│   ├── test_fetcher.py            # 模拟 HTTP 响应的客户端测试
│   ├── test_parser.py             # 使用 sample_html 的解析正确性测试
│   └── fixtures/                  # 测试用的静态 HTML 样本
│       └── sample_news.html
├── config/                        # 配置文件目录
│   ├── default.yaml               # 默认抓取参数（并发数、重试次数、超时）
│   └── production.yaml            # 生产环境覆盖配置（调高并发、启用代理）
├── docs/                          # 完整文档源文件
│   ├── user_guide.md
│   ├── development.md
│   ├── api_reference.md
│   └── deployment.md
└── output/                        # 默认输出目录（gitignore 忽略，运行时生成）
    └── .gitkeep
```

## 贡献指南

1. 查阅 issue 列表或新建 issue 描述您希望修复的问题或新增的功能，等待维护者确认需求范围。对于较大的改动，建议先通过 issue 讨论设计思路。

2. 从主分支 fork 项目到个人账户，并创建功能分支（命名格式为 feature/功能简述 或 fix/问题编号），确保分支基于最新的 main 分支。

3. 编写代码并补充对应的单元测试，测试覆盖率不应低于 80%。同时更新 docs 目录下受影响的文档章节，确保文档与代码行为一致。

4. 提交代码前运行本地测试套件（pytest tests/）和代码风格检查（flake8 或 ruff），保证所有测试通过且无 lint 警告。提交信息遵循 Conventional Commits 规范。

## 常见问题

Q: 运行过程中出现 SSL 证书验证错误，如何解决？

A: 该问题通常由目标站点使用自签名证书或过期的 TLS 配置引起。您可以在配置文件 config/default.yaml 中将 fetcher.verify_ssl 设置为 false 以跳过证书验证。请注意，这降低了通信安全性，仅建议在隔离网络环境中使用。若需保持验证，请将目标站点的根证书添加至系统信任库。

Q: 如何处理目标页面返回的动态内容（例如由 JavaScript 渲染的正文）？

A: 本项目默认使用 lxml 解析静态 HTML，不执行 JavaScript。若目标页面依赖客户端渲染，建议使用 Playwright 或 Selenium 作为替代方案。您可继承 src/parser/extractor.py 中的 BaseExtractor 类，重写 fetch 方法以调用 Playwright 的异步 API，并在配置中切换解析器实现。

Q: 断点续传功能是否支持分布式多机部署？

A: 本地 SQLite 队列仅支持单机持久化。如需在多节点间共享进度状态，请将 storage.queue 配置项切换为 redis 后端，本项目提供了 RedisQueue 的参考实现（位于 src/storage/redis_queue.py）。您需要自行部署 Redis 服务并配置连接字符串。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
