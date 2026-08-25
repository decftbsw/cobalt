# NewsAggregator MCP Server

NewsAggregator MCP Server 是一个基于 Model Context Protocol 协议构建的新闻资讯聚合与分发系统，专为 AI 助手和开发工具链设计。该项目将 m.3g.oexnr.cn 站点下的批量新闻资源封装为标准化的 MCP 工具接口，使 AI 应用能够以结构化方式检索、筛选和获取新闻内容。

目标用户包括 AI 应用开发者、新闻聚合平台运维人员、RAG 系统构建者以及需要将实时新闻数据集成到自动化工作流中的技术团队。通过 MCP 协议标准，本项目解决了传统新闻爬虫与 AI 系统之间接口不统一、数据格式杂乱、缺乏语义化检索能力等问题，为智能新闻消费场景提供基础设施。

## 功能概览

**新闻资源索引** 对 m.3g.oexnr.cn 域名下三百余条新闻链接建立本地索引缓存，支持按 ID 和发布时间快速定位。

**MCP 工具接口** 将每条新闻暴露为 MCP 工具（Tool），AI 客户端可通过标准化调用获取新闻标题、正文摘要和原始链接。

**批量检索能力** 支持按批次（Batch）拉取新闻列表，第 32/300 批次资源已完整收录，可通过工具参数指定批次范围。

**内容过滤与排序** 提供基于关键词、发布时间、新闻 ID 的过滤与排序功能，支持升序/降序输出。

**结构化响应** 所有返回数据遵循 JSON Schema 规范，包含元数据字段（source、timestamp、batch_id）便于下游系统处理。

**缓存更新机制** 内置 TTL 缓存策略，资源列表可定期刷新，避免重复请求源站。

**可观测性支持** 集成结构化日志（structured logging）与调用追踪（trace），便于调试和性能监控。

**扩展接口预留** 预留了自定义解析器（Parser）和过滤器（Filter）的注册点，用户可接入其他新闻源。

## 应用场景

**AI 新闻简报生成** 开发者可将本 MCP Server 集成到 LLM 应用中，每日定时拉取最新新闻资源，由 AI 自动生成摘要简报并推送至钉钉、飞书或邮件。

**RAG 知识库构建** 新闻内容作为外部知识源，通过 MCP 工具检索后注入 RAG 流水线，为垂直领域问答系统提供时效性上下文。

**舆情监控系统** 运维团队设置关键词过滤规则，对特定主题新闻进行实时追踪，结合告警阈值实现舆情风险预警。

**开发测试数据填充** 在集成测试或演示环境中，使用本项目的新闻列表作为模拟数据源，替代真实外部 API 调用，降低测试成本和网络依赖。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/your-org/newsaggregator-mcp.git
cd newsaggregator-mcp

# 安装依赖（使用 Poetry）
poetry install

# 或使用 pip
pip install -r requirements.txt

# 启动 MCP Server（stdio 模式）
python -m newsaggregator.server
```

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | >= 3.10 | 核心运行环境，需要支持 async/await 语法 |
| mcp | >= 0.1.0 | Model Context Protocol Python SDK，提供协议基础框架 |
| httpx | >= 0.27.0 | 异步 HTTP 客户端，用于获取原始新闻页面内容 |
| pydantic | >= 2.0.0 | 数据验证与序列化，用于工具输入输出 Schema 定义 |
| structlog | >= 24.0.0 | 结构化日志库，提供 JSON 格式日志输出 |
| cachetools | >= 5.3.0 | 内存缓存库，用于 TTL 缓存管理 |
| pytest | >= 8.0.0 | 测试框架（开发依赖） |
| black | >= 24.0.0 | 代码格式化工具（开发依赖） |
| mypy | >= 1.8.0 | 静态类型检查（开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速部署并测试第一个新闻检索请求？ |
| 工具接口 | docs/tools-reference.md | MCP 工具列表、参数定义、返回结构详解 |
| 配置说明 | docs/configuration.md | 环境变量、缓存策略、日志级别等配置项 |
| 架构设计 | docs/architecture.md | 系统模块划分、数据流、扩展点设计原理 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/2018554.htm
- http://m.3g.oexnr.cn/nnews/413999.htm
- http://m.3g.oexnr.cn/nnews/4620.htm
- http://m.3g.oexnr.cn/nnews/2455.htm
- http://m.3g.oexnr.cn/nnews/506355.htm
- http://m.3g.oexnr.cn/nnews/7338758.htm
- http://m.3g.oexnr.cn/nnews/709313.htm
- http://m.3g.oexnr.cn/nnews/74387.htm
- http://m.3g.oexnr.cn/nnews/118459.htm
- http://m.3g.oexnr.cn/nnews/30475.htm
- http://m.3g.oexnr.cn/nnews/3826.htm
- http://m.3g.oexnr.cn/nnews/4796272.htm
- http://m.3g.oexnr.cn/nnews/2150303.htm
- http://m.3g.oexnr.cn/nnews/2185.htm
- http://m.3g.oexnr.cn/nnews/6417.htm
- http://m.3g.oexnr.cn/nnews/2781.htm
- http://m.3g.oexnr.cn/nnews/758389.htm
- http://m.3g.oexnr.cn/nnews/1419134.htm
- http://m.3g.oexnr.cn/nnews/8652530.htm
- http://m.3g.oexnr.cn/nnews/3307.htm
- http://m.3g.oexnr.cn/nnews/0611516.htm
- http://m.3g.oexnr.cn/nnews/169459.htm
- http://m.3g.oexnr.cn/nnews/9595424.htm
- http://m.3g.oexnr.cn/nnews/469661.htm
- http://m.3g.oexnr.cn/nnews/3852.htm
- http://m.3g.oexnr.cn/nnews/5393500.htm
- http://m.3g.oexnr.cn/nnews/26821.htm
- http://m.3g.oexnr.cn/nnews/6443441.htm
- http://m.3g.oexnr.cn/nnews/070704.htm
- http://m.3g.oexnr.cn/nnews/1806728.htm
- http://m.3g.oexnr.cn/nnews/8687195.htm
- http://m.3g.oexnr.cn/nnews/13570.htm
- http://m.3g.oexnr.cn/nnews/3636.htm
- http://m.3g.oexnr.cn/nnews/10661.htm
- http://m.3g.oexnr.cn/nnews/80142.htm
- http://m.3g.oexnr.cn/nnews/56719.htm
- http://m.3g.oexnr.cn/nnews/9092239.htm
- http://m.3g.oexnr.cn/nnews/3951.htm
- http://m.3g.oexnr.cn/nnews/812424.htm
- http://m.3g.oexnr.cn/nnews/6160.htm
- http://m.3g.oexnr.cn/nnews/5064.htm
- http://m.3g.oexnr.cn/nnews/0659208.htm
- http://m.3g.oexnr.cn/nnews/45026.htm
- http://m.3g.oexnr.cn/nnews/13268.htm
- http://m.3g.oexnr.cn/nnews/0651588.htm
- http://m.3g.oexnr.cn/nnews/571011.htm
- http://m.3g.oexnr.cn/nnews/136081.htm
- http://m.3g.oexnr.cn/nnews/8954432.htm
- http://m.3g.oexnr.cn/nnews/27101.htm
- http://m.3g.oexnr.cn/nnews/06131.htm
- http://m.3g.oexnr.cn/nnews/7688.htm
- http://m.3g.oexnr.cn/nnews/3461620.htm
- http://m.3g.oexnr.cn/nnews/8609.htm
- http://m.3g.oexnr.cn/nnews/23056.htm
- http://m.3g.oexnr.cn/nnews/5165949.htm
- http://m.3g.oexnr.cn/nnews/700849.htm
- http://m.3g.oexnr.cn/nnews/694309.htm
- http://m.3g.oexnr.cn/nnews/5473864.htm
- http://m.3g.oexnr.cn/nnews/19244.htm
- http://m.3g.oexnr.cn/nnews/502985.htm
- http://m.3g.oexnr.cn/nnews/7081.htm
- http://m.3g.oexnr.cn/nnews/12936.htm
- http://m.3g.oexnr.cn/nnews/4293.htm
- http://m.3g.oexnr.cn/nnews/25811.htm
- http://m.3g.oexnr.cn/nnews/2394176.htm
- http://m.3g.oexnr.cn/nnews/07449.htm
- http://m.3g.oexnr.cn/nnews/0393259.htm
- http://m.3g.oexnr.cn/nnews/0373.htm
- http://m.3g.oexnr.cn/nnews/4212.htm
- http://m.3g.oexnr.cn/nnews/52145.htm
- http://m.3g.oexnr.cn/nnews/8976444.htm
- http://m.3g.oexnr.cn/nnews/9813718.htm
- http://m.3g.oexnr.cn/nnews/6722141.htm
- http://m.3g.oexnr.cn/nnews/1134305.htm
- http://m.3g.oexnr.cn/nnews/4208.htm
- http://m.3g.oexnr.cn/nnews/7695971.htm
- http://m.3g.oexnr.cn/nnews/759489.htm
- http://m.3g.oexnr.cn/nnews/58305.htm
- http://m.3g.oexnr.cn/nnews/7866578.htm
- http://m.3g.oexnr.cn/nnews/320826.htm
- http://m.3g.oexnr.cn/nnews/5329.htm
- http://m.3g.oexnr.cn/nnews/28931.htm
- http://m.3g.oexnr.cn/nnews/0977613.htm
- http://m.3g.oexnr.cn/nnews/9928.htm
- http://m.3g.oexnr.cn/nnews/780554.htm
- http://m.3g.oexnr.cn/nnews/68754.htm
- http://m.3g.oexnr.cn/nnews/04045.htm
- http://m.3g.oexnr.cn/nnews/8398.htm
- http://m.3g.oexnr.cn/nnews/81077.htm
- http://m.3g.oexnr.cn/nnews/24137.htm
- http://m.3g.oexnr.cn/nnews/77349.htm
- http://m.3g.oexnr.cn/nnews/0420407.htm
- http://m.3g.oexnr.cn/nnews/6299341.htm
- http://m.3g.oexnr.cn/nnews/3281516.htm
- http://m.3g.oexnr.cn/nnews/1035228.htm
- http://m.3g.oexnr.cn/nnews/070787.htm
- http://m.3g.oexnr.cn/nnews/5893.htm
- http://m.3g.oexnr.cn/nnews/9164186.htm
- http://m.3g.oexnr.cn/nnews/08613.htm
- http://m.3g.oexnr.cn/nnews/8799.htm
- http://m.3g.oexnr.cn/nnews/66458.htm
- http://m.3g.oexnr.cn/nnews/15910.htm
- http://m.3g.oexnr.cn/nnews/1397569.htm
- http://m.3g.oexnr.cn/nnews/1535264.htm
- http://m.3g.oexnr.cn/nnews/8279.htm
- http://m.3g.oexnr.cn/nnews/589811.htm
- http://m.3g.oexnr.cn/nnews/0960450.htm
- http://m.3g.oexnr.cn/nnews/75397.htm
- http://m.3g.oexnr.cn/nnews/18606.htm
- http://m.3g.oexnr.cn/nnews/3361280.htm
- http://m.3g.oexnr.cn/nnews/82798.htm
- http://m.3g.oexnr.cn/nnews/3390232.htm
- http://m.3g.oexnr.cn/nnews/1885.htm
- http://m.3g.oexnr.cn/nnews/0773248.htm
- http://m.3g.oexnr.cn/nnews/8026.htm
- http://m.3g.oexnr.cn/nnews/374532.htm
- http://m.3g.oexnr.cn/nnews/08641.htm
- http://m.3g.oexnr.cn/nnews/3817.htm
- http://m.3g.oexnr.cn/nnews/59243.htm
- http://m.3g.oexnr.cn/nnews/092021.htm
- http://m.3g.oexnr.cn/nnews/3466.htm
- http://m.3g.oexnr.cn/nnews/416458.htm
- http://m.3g.oexnr.cn/nnews/3306521.htm
- http://m.3g.oexnr.cn/nnews/924134.htm
- http://m.3g.oexnr.cn/nnews/4875.htm
- http://m.3g.oexnr.cn/nnews/0974.htm
- http://m.3g.oexnr.cn/nnews/048031.htm
- http://m.3g.oexnr.cn/nnews/7069.htm
- http://m.3g.oexnr.cn/nnews/6255.htm
- http://m.3g.oexnr.cn/nnews/7355.htm
- http://m.3g.oexnr.cn/nnews/23468.htm
- http://m.3g.oexnr.cn/nnews/9453037.htm
- http://m.3g.oexnr.cn/nnews/30291.htm
- http://m.3g.oexnr.cn/nnews/4843313.htm
- http://m.3g.oexnr.cn/nnews/0657834.htm
- http://m.3g.oexnr.cn/nnews/415362.htm
- http://m.3g.oexnr.cn/nnews/1109019.htm
- http://m.3g.oexnr.cn/nnews/63323.htm
- http://m.3g.oexnr.cn/nnews/577017.htm
- http://m.3g.oexnr.cn/nnews/4058.htm
- http://m.3g.oexnr.cn/nnews/7857.htm
- http://m.3g.oexnr.cn/nnews/665384.htm
- http://m.3g.oexnr.cn/nnews/3504.htm
- http://m.3g.oexnr.cn/nnews/6285814.htm
- http://m.3g.oexnr.cn/nnews/7256855.htm
- http://m.3g.oexnr.cn/nnews/4187683.htm
- http://m.3g.oexnr.cn/nnews/36824.htm
- http://m.3g.oexnr.cn/nnews/0133.htm
- http://m.3g.oexnr.cn/nnews/676073.htm
- http://m.3g.oexnr.cn/nnews/6820.htm
- http://m.3g.oexnr.cn/nnews/93157.htm
- http://m.3g.oexnr.cn/nnews/9531576.htm
- http://m.3g.oexnr.cn/nnews/3847439.htm
- http://m.3g.oexnr.cn/nnews/5643.htm
- http://m.3g.oexnr.cn/nnews/6236.htm
- http://m.3g.oexnr.cn/nnews/8988.htm
- http://m.3g.oexnr.cn/nnews/503200.htm
- http://m.3g.oexnr.cn/nnews/4569928.htm
- http://m.3g.oexnr.cn/nnews/616580.htm
- http://m.3g.oexnr.cn/nnews/81019.htm
- http://m.3g.oexnr.cn/nnews/1058421.htm
- http://m.3g.oexnr.cn/nnews/7925458.htm
- http://m.3g.oexnr.cn/nnews/3178141.htm
- http://m.3g.oexnr.cn/nnews/90549.htm
- http://m.3g.oexnr.cn/nnews/068221.htm
- http://m.3g.oexnr.cn/nnews/963421.htm
- http://m.3g.oexnr.cn/nnews/4627127.htm
- http://m.3g.oexnr.cn/nnews/9607.htm
- http://m.3g.oexnr.cn/nnews/6381595.htm
- http://m.3g.oexnr.cn/nnews/3886.htm
- http://m.3g.oexnr.cn/nnews/45094.htm
- http://m.3g.oexnr.cn/nnews/194432.htm
- http://m.3g.oexnr.cn/nnews/17722.htm
- http://m.3g.oexnr.cn/nnews/918538.htm
- http://m.3g.oexnr.cn/nnews/3564.htm
- http://m.3g.oexnr.cn/nnews/4121790.htm
- http://m.3g.oexnr.cn/nnews/2276.htm
- http://m.3g.oexnr.cn/nnews/27121.htm
- http://m.3g.oexnr.cn/nnews/8247.htm
- http://m.3g.oexnr.cn/nnews/2926.htm
- http://m.3g.oexnr.cn/nnews/34703.htm
- http://m.3g.oexnr.cn/nnews/81596.htm
- http://m.3g.oexnr.cn/nnews/23902.htm
- http://m.3g.oexnr.cn/nnews/762216.htm
- http://m.3g.oexnr.cn/nnews/8540947.htm
- http://m.3g.oexnr.cn/nnews/94050.htm
- http://m.3g.oexnr.cn/nnews/04105.htm
- http://m.3g.oexnr.cn/nnews/6190261.htm
- http://m.3g.oexnr.cn/nnews/83156.htm
- http://m.3g.oexnr.cn/nnews/15642.htm
- http://m.3g.oexnr.cn/nnews/0149740.htm
- http://m.3g.oexnr.cn/nnews/741584.htm
- http://m.3g.oexnr.cn/nnews/58208.htm
- http://m.3g.oexnr.cn/nnews/0825026.htm
- http://m.3g.oexnr.cn/nnews/36039.htm
- http://m.3g.oexnr.cn/nnews/35709.htm
- http://m.3g.oexnr.cn/nnews/9773454.htm
- http://m.3g.oexnr.cn/nnews/2757.htm
- http://m.3g.oexnr.cn/nnews/0695964.htm
- http://m.3g.oexnr.cn/nnews/59051.htm
- http://m.3g.oexnr.cn/nnews/690560.htm
- http://m.3g.oexnr.cn/nnews/9343.htm
- http://m.3g.oexnr.cn/nnews/1909008.htm
- http://m.3g.oexnr.cn/nnews/9296.htm
- http://m.3g.oexnr.cn/nnews/4498.htm
- http://m.3g.oexnr.cn/nnews/593002.htm
- http://m.3g.oexnr.cn/nnews/1477.htm
- http://m.3g.oexnr.cn/nnews/03313.htm
- http://m.3g.oexnr.cn/nnews/98842.htm
- http://m.3g.oexnr.cn/nnews/77576.htm
- http://m.3g.oexnr.cn/nnews/96452.htm
- http://m.3g.oexnr.cn/nnews/86756.htm
- http://m.3g.oexnr.cn/nnews/4222.htm
- http://m.3g.oexnr.cn/nnews/7934867.htm
- http://m.3g.oexnr.cn/nnews/4358.htm
- http://m.3g.oexnr.cn/nnews/34065.htm
- http://m.3g.oexnr.cn/nnews/8069228.htm
- http://m.3g.oexnr.cn/nnews/38758.htm
- http://m.3g.oexnr.cn/nnews/1986085.htm
- http://m.3g.oexnr.cn/nnews/995750.htm
- http://m.3g.oexnr.cn/nnews/57205.htm
- http://m.3g.oexnr.cn/nnews/6339290.htm
- http://m.3g.oexnr.cn/nnews/02101.htm
- http://m.3g.oexnr.cn/nnews/0536967.htm
- http://m.3g.oexnr.cn/nnews/7407472.htm
- http://m.3g.oexnr.cn/nnews/899992.htm
- http://m.3g.oexnr.cn/nnews/2435.htm
- http://m.3g.oexnr.cn/nnews/07626.htm
- http://m.3g.oexnr.cn/nnews/0478898.htm
- http://m.3g.oexnr.cn/nnews/1595.htm
- http://m.3g.oexnr.cn/nnews/5056879.htm
- http://m.3g.oexnr.cn/nnews/8779.htm
- http://m.3g.oexnr.cn/nnews/841353.htm
- http://m.3g.oexnr.cn/nnews/616327.htm
- http://m.3g.oexnr.cn/nnews/68420.htm
- http://m.3g.oexnr.cn/nnews/504650.htm
- http://m.3g.oexnr.cn/nnews/772827.htm
- http://m.3g.oexnr.cn/nnews/404449.htm
- http://m.3g.oexnr.cn/nnews/9749.htm
- http://m.3g.oexnr.cn/nnews/774613.htm
- http://m.3g.oexnr.cn/nnews/673625.htm
- http://m.3g.oexnr.cn/nnews/485094.htm
- http://m.3g.oexnr.cn/nnews/0153452.htm
- http://m.3g.oexnr.cn/nnews/16635.htm
- http://m.3g.oexnr.cn/nnews/63394.htm
- http://m.3g.oexnr.cn/nnews/845577.htm
- http://m.3g.oexnr.cn/nnews/1062443.htm
- http://m.3g.oexnr.cn/nnews/3686840.htm
- http://m.3g.oexnr.cn/nnews/8496895.htm
- http://m.3g.oexnr.cn/nnews/129870.htm
- http://m.3g.oexnr.cn/nnews/5587.htm
- http://m.3g.oexnr.cn/nnews/3665185.htm
- http://m.3g.oexnr.cn/nnews/3417.htm
- http://m.3g.oexnr.cn/nnews/247153.htm
- http://m.3g.oexnr.cn/nnews/640751.htm
- http://m.3g.oexnr.cn/nnews/95529.htm
- http://m.3g.oexnr.cn/nnews/71870.htm
- http://m.3g.oexnr.cn/nnews/728882.htm
- http://m.3g.oexnr.cn/nnews/878707.htm
- http://m.3g.oexnr.cn/nnews/8500.htm
- http://m.3g.oexnr.cn/nnews/6486059.htm
- http://m.3g.oexnr.cn/nnews/4843.htm
- http://m.3g.oexnr.cn/nnews/229135.htm
- http://m.3g.oexnr.cn/nnews/7240645.htm
- http://m.3g.oexnr.cn/nnews/37289.htm
- http://m.3g.oexnr.cn/nnews/6182727.htm
- http://m.3g.oexnr.cn/nnews/3175.htm
- http://m.3g.oexnr.cn/nnews/4777.htm
- http://m.3g.oexnr.cn/nnews/53236.htm
- http://m.3g.oexnr.cn/nnews/7616.htm
- http://m.3g.oexnr.cn/nnews/061538.htm
- http://m.3g.oexnr.cn/nnews/82293.htm
- http://m.3g.oexnr.cn/nnews/1653.htm
- http://m.3g.oexnr.cn/nnews/63279.htm
- http://m.3g.oexnr.cn/nnews/5828.htm
- http://m.3g.oexnr.cn/nnews/9852489.htm
- http://m.3g.oexnr.cn/nnews/264740.htm
- http://m.3g.oexnr.cn/nnews/9106041.htm
- http://m.3g.oexnr.cn/nnews/3652.htm
- http://m.3g.oexnr.cn/nnews/266233.htm
- http://m.3g.oexnr.cn/nnews/1846363.htm
- http://m.3g.oexnr.cn/nnews/67882.htm
- http://m.3g.oexnr.cn/nnews/54826.htm
- http://m.3g.oexnr.cn/nnews/8909827.htm
- http://m.3g.oexnr.cn/nnews/8452484.htm
- http://m.3g.oexnr.cn/nnews/3598.htm
- http://m.3g.oexnr.cn/nnews/0444.htm
- http://m.3g.oexnr.cn/nnews/32980.htm
- http://m.3g.oexnr.cn/nnews/348269.htm
- http://m.3g.oexnr.cn/nnews/10012.htm
- http://m.3g.oexnr.cn/nnews/75936.htm
- http://m.3g.oexnr.cn/nnews/452598.htm
- http://m.3g.oexnr.cn/nnews/578316.htm
- http://m.3g.oexnr.cn/nnews/2296364.htm
- http://m.3g.oexnr.cn/nnews/0850.htm
- http://m.3g.oexnr.cn/nnews/11351.htm
- http://m.3g.oexnr.cn/nnews/530710.htm
- http://m.3g.oexnr.cn/nnews/1334874.htm
- http://m.3g.oexnr.cn/nnews/2303539.htm
- http://m.3g.oexnr.cn/nnews/1866.htm

## 项目结构

```
newsaggregator-mcp/
├── src/                                # 源代码主目录
│   └── newsaggregator/                 # 包根目录
│       ├── __init__.py                 # 包初始化，导出核心接口
│       ├── server.py                   # MCP Server 主入口，初始化工具注册
│       ├── resources/                  # 资源管理模块
│       │   ├── __init__.py
│       │   ├── index.py                # 新闻索引构建与查询逻辑
│       │   └── fetcher.py              # 异步 HTTP 获取与页面解析
│       ├── tools/                      # MCP 工具实现
│       │   ├── __init__.py
│       │   ├── list_news.py            # 列表工具：返回批次资源列表
│       │   ├── get_news.py             # 详情工具：返回单条新闻内容
│       │   └── filter_news.py          # 过滤工具：关键词/日期过滤
│       ├── schemas/                    # Pydantic 数据模型
│       │   ├── __init__.py
│       │   ├── news.py                 # NewsItem, BatchMetadata 定义
│       │   └── request.py              # 工具请求参数 Schema
│       └── utils/                      # 通用工具函数
│           ├── __init__.py
│           ├── cache.py                # TTL 缓存装饰器与缓存管理器
│           └── logger.py               # structlog 配置与上下文绑定
├── tests/                              # 单元测试与集成测试
│   ├── __init__.py
│   ├── test_index.py                   # 索引模块测试
│   ├── test_tools.py                   # 工具接口测试（使用 pytest-asyncio）
│   └── fixtures/                       # 测试固定数据
│       └── sample_news.json            # 模拟新闻响应数据
├── docs/                               # 文档目录
│   ├── getting-started.md
│   ├── tools-reference.md
│   ├── configuration.md
│   └── architecture.md
├── scripts/                            # 运维与开发脚本
│   ├── update_cache.py                 # 手动触发缓存更新
│   └── validate_urls.py                # 校验资源列表 URL 可用性
├── pyproject.toml                      # Poetry 项目配置与依赖声明
├── requirements.txt                    # pip 兼容依赖锁定文件
├── .env.example                        # 环境变量配置模板
├── .gitignore                          # Git 忽略规则
└── README.md                           # 项目说明文档（本文件）
```

## 贡献指南

**提交 Issue 与需求反馈** 在 GitHub Issues 中描述使用中遇到的问题或期望新增的功能，请附上复现步骤、日志片段和运行环境信息。

**本地开发环境搭建** Fork 本仓库后，使用 Poetry 创建虚拟环境并安装所有开发依赖，运行 pre-commit 钩子确保代码格式符合 black 和 mypy 规范。

**编写与测试工具接口** 新增 MCP 工具时，需在 src/newsaggregator/tools/ 下创建模块，实现 async 调用函数，并在 server.py 中完成注册。所有工具必须附带 pytest 单元测试，覆盖率不低于 80%。

**更新资源列表** 若需要同步最新新闻链接，修改资源列表后运行 scripts/validate_urls.py 校验所有 URL 可访问性，确认无误后提交 Pull Request。

**文档同步更新** 任何代码变更必须同步更新 README 或 docs/ 下对应文档，确保文档中示例、参数说明与实际代码保持一致。

## 常见问题

**Q: 为什么启动后没有任何新闻数据？**  
A: 首次启动需要初始化索引缓存。请检查网络连接是否能够访问 m.3g.oexnr.cn 域名。若网络正常，可尝试执行 scripts/update_cache.py 手动拉取数据并构建缓存。缓存文件默认存储在项目根目录下的 .cache/ 文件夹中。

**Q: 如何修改缓存刷新间隔？**  
A: 在 .env 文件中设置 CACHE_TTL_SECONDS 环境变量，单位秒。默认值为 3600（一小时）。修改后重启 MCP Server 生效。

**Q: 是否支持 HTTPS 访问源站？**  
A: 目前源站 m.3g.oexnr.cn 仅提供 HTTP 服务，本项目严格遵循原始 URL 协议，不进行协议升级。若源站未来支持 HTTPS，将发布兼容更新。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
