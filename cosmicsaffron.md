# WebIndex 移动端资讯聚合网关

WebIndex 是一个面向移动端资讯聚合场景的轻量级网关与资源导航系统，定位于为开发者、数据采集工程师、内容运营人员提供结构化的外链资源池与快速访问入口。项目本身不存储任何原始内容，而是作为索引层，将分散的移动端新闻、公告、行业动态等 URL 资源按批次归档，并提供标准化的访问接口、健康检查与过期链接检测能力。目标用户包括爬虫开发者、舆情监控系统集成方、内部知识库维护团队以及需要对大量外链进行统一管理的技术运维人员。通过本系统，用户可以快速获取第 61/300 批次共计 300 个资讯类 URL，并利用配套的 CLI 工具进行批量可用性验证、元信息提取与访问日志记录。

## 功能概览

批量资源导入与持久化 支持通过 CSV、JSON Lines 或纯文本列表批量导入 URL，自动解析并存入 SQLite 本地缓存，同时生成唯一批次标识。

健康检查与死链检测 内置异步 HTTP 客户端，支持并发请求，可配置超时与重试策略，自动标记返回状态码非 2xx/3xx 的链接，并生成死链报告。

访问代理与重写规则 提供可选的透明代理模式，允许对目标 URL 附加自定义查询参数（如来源标记、时间戳），便于链路追踪。

元信息提取 对每个 URL 执行轻量级页面标题、描述、关键词抓取，并存储至本地索引库，支持后续全文检索。

批次管理与版本追踪 每个资源批次拥有独立版本号、导入时间、链接总数与有效数统计，支持按批次回滚或导出。

RESTful 查询接口 提供 `/api/batch/{id}/urls`、`/api/url/{hash}/status` 等标准 JSON 接口，便于第三方系统集成。

CLI 运维工具 提供 `webindex check`、`webindex export`、`webindex stats` 等子命令，无需启动 Web 服务即可完成日常巡检与数据导出。

## 应用场景

舆情监控系统的外链数据源初始化 舆情分析团队在搭建新话题监测任务时，可将本批次 URL 作为初始种子链接，通过系统导出的链接列表快速配置爬虫抓取队列，省去人工收集与去重步骤。

内部知识库的参考文献归档 企业技术文档团队在整理行业资讯周报时，可利用本系统的批次导出功能，将 300 条链接一键生成为 Markdown 引用列表，并自动检测失效链接，保障归档质量。

移动端内容聚合平台的测试数据集 移动应用开发者在测试内容展示模块的加载性能与异常处理逻辑时，可使用本系统提供的代理端点模拟大量外链请求，验证图片懒加载、超时降级等策略。

自动化运维巡检的链接存活监控 运维团队可编写定时任务调用 `webindex check` 命令，每日扫描本批次链接的可用性，并将异常结果推送至企业微信或钉钉机器人，实现被动监控。

数据中台的外链资源标准化接入 数据中台团队需要将不同来源的 URL 统一成标准格式并记录元数据，本系统可作为适配层，对原始链接进行规范化存储与基础信息补充，降低下游 ETL 复杂度。

## 快速开始

以下命令演示了从克隆仓库到运行基础健康检查的完整流程。请确保系统已安装 Git 与 Python 3.9 及以上版本。

```bash
# 克隆项目仓库
git clone https://github.com/webindex/webindex-gateway.git
cd webindex-gateway

# 创建并激活虚拟环境（推荐）
python3 -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate

# 安装核心依赖与 CLI 工具
pip install -e .

# 导入本批次 URL 列表（假设已保存为 batch_61.txt，每行一个 URL）
webindex import --batch 61 --source batch_61.txt

# 执行链接健康检查，并发数 50，超时 5 秒
webindex check --batch 61 --concurrency 50 --timeout 5

# 查看批次统计摘要
webindex stats --batch 61

# 导出有效链接列表（状态码 200）
webindex export --batch 61 --status 200 --output valid_urls.txt
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 – 3.11 | 核心运行时，3.12 暂未全面测试 |
| aiohttp | >= 3.8.0 | 异步 HTTP 客户端，用于并发健康检查 |
| sqlite3 | 内置模块 | 本地元数据存储，无需额外安装 |
| click | >= 8.0.0 | CLI 命令行交互框架 |
| pytest | >= 7.0.0 | 仅开发测试环境需要 |
| black | >= 22.0.0 | 仅代码格式化时使用，非运行时依赖 |
| uvicorn | >= 0.17.0 | 若启动 Web API 服务则需要 |
| fastapi | >= 0.85.0 | 若启动 Web API 服务则需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | `docs/getting-started.md` | 如何在一分钟内完成安装并导入第一个批次？ |
| 命令行参考 | `docs/cli-reference.md` | 每个子命令的完整参数列表与使用示例是什么？ |
| API 规范 | `docs/api-specification.yaml` | RESTful 接口的请求/响应结构、状态码定义如何？ |
| 运维手册 | `docs/operations-guide.md` | 如何配置日志轮转、监控指标与故障恢复流程？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/313199.htm
- http://m.wap.oexnr.cn/jnews/8085.htm
- http://m.wap.oexnr.cn/jnews/6873085.htm
- http://m.wap.oexnr.cn/jnews/4855.htm
- http://m.wap.oexnr.cn/jnews/637463.htm
- http://m.wap.oexnr.cn/jnews/51020.htm
- http://m.wap.oexnr.cn/jnews/3357.htm
- http://m.wap.oexnr.cn/jnews/182814.htm
- http://m.wap.oexnr.cn/jnews/0006738.htm
- http://m.wap.oexnr.cn/jnews/4777.htm
- http://m.wap.oexnr.cn/jnews/6328310.htm
- http://m.wap.oexnr.cn/jnews/6277.htm
- http://m.wap.oexnr.cn/jnews/40670.htm
- http://m.wap.oexnr.cn/jnews/6018397.htm
- http://m.wap.oexnr.cn/jnews/1000.htm
- http://m.wap.oexnr.cn/jnews/2856686.htm
- http://m.wap.oexnr.cn/jnews/255358.htm
- http://m.wap.oexnr.cn/jnews/74697.htm
- http://m.wap.oexnr.cn/jnews/435959.htm
- http://m.wap.oexnr.cn/jnews/5172493.htm
- http://m.wap.oexnr.cn/jnews/0005.htm
- http://m.wap.oexnr.cn/jnews/4277348.htm
- http://m.wap.oexnr.cn/jnews/11316.htm
- http://m.wap.oexnr.cn/jnews/9443631.htm
- http://m.wap.oexnr.cn/jnews/5685.htm
- http://m.wap.oexnr.cn/jnews/15101.htm
- http://m.wap.oexnr.cn/jnews/228218.htm
- http://m.wap.oexnr.cn/jnews/1992.htm
- http://m.wap.oexnr.cn/jnews/6763.htm
- http://m.wap.oexnr.cn/jnews/1788.htm
- http://m.wap.oexnr.cn/jnews/385461.htm
- http://m.wap.oexnr.cn/jnews/4346011.htm
- http://m.wap.oexnr.cn/jnews/92221.htm
- http://m.wap.oexnr.cn/jnews/0342350.htm
- http://m.wap.oexnr.cn/jnews/784768.htm
- http://m.wap.oexnr.cn/jnews/089120.htm
- http://m.wap.oexnr.cn/jnews/9527.htm
- http://m.wap.oexnr.cn/jnews/0838.htm
- http://m.wap.oexnr.cn/jnews/63980.htm
- http://m.wap.oexnr.cn/jnews/88445.htm
- http://m.wap.oexnr.cn/jnews/83279.htm
- http://m.wap.oexnr.cn/jnews/89962.htm
- http://m.wap.oexnr.cn/jnews/87884.htm
- http://m.wap.oexnr.cn/jnews/68742.htm
- http://m.wap.oexnr.cn/jnews/209745.htm
- http://m.wap.oexnr.cn/jnews/104574.htm
- http://m.wap.oexnr.cn/jnews/2641.htm
- http://m.wap.oexnr.cn/jnews/95985.htm
- http://m.wap.oexnr.cn/jnews/0003149.htm
- http://m.wap.oexnr.cn/jnews/700917.htm
- http://m.wap.oexnr.cn/jnews/805347.htm
- http://m.wap.oexnr.cn/jnews/041675.htm
- http://m.wap.oexnr.cn/jnews/62781.htm
- http://m.wap.oexnr.cn/jnews/618589.htm
- http://m.wap.oexnr.cn/jnews/8707944.htm
- http://m.wap.oexnr.cn/jnews/6164531.htm
- http://m.wap.oexnr.cn/jnews/89914.htm
- http://m.wap.oexnr.cn/jnews/89021.htm
- http://m.wap.oexnr.cn/jnews/264713.htm
- http://m.wap.oexnr.cn/jnews/565928.htm
- http://m.wap.oexnr.cn/jnews/6411667.htm
- http://m.wap.oexnr.cn/jnews/03308.htm
- http://m.wap.oexnr.cn/jnews/37851.htm
- http://m.wap.oexnr.cn/jnews/61531.htm
- http://m.wap.oexnr.cn/jnews/908112.htm
- http://m.wap.oexnr.cn/jnews/605113.htm
- http://m.wap.oexnr.cn/jnews/8777864.htm
- http://m.wap.oexnr.cn/jnews/6870518.htm
- http://m.wap.oexnr.cn/jnews/97366.htm
- http://m.wap.oexnr.cn/jnews/92746.htm
- http://m.wap.oexnr.cn/jnews/5652569.htm
- http://m.wap.oexnr.cn/jnews/35295.htm
- http://m.wap.oexnr.cn/jnews/62333.htm
- http://m.wap.oexnr.cn/jnews/3060.htm
- http://m.wap.oexnr.cn/jnews/83021.htm
- http://m.wap.oexnr.cn/jnews/5286263.htm
- http://m.wap.oexnr.cn/jnews/3547.htm
- http://m.wap.oexnr.cn/jnews/0893924.htm
- http://m.wap.oexnr.cn/jnews/41852.htm
- http://m.wap.oexnr.cn/jnews/3159943.htm
- http://m.wap.oexnr.cn/jnews/0841993.htm
- http://m.wap.oexnr.cn/jnews/63878.htm
- http://m.wap.oexnr.cn/jnews/52486.htm
- http://m.wap.oexnr.cn/jnews/4667671.htm
- http://m.wap.oexnr.cn/jnews/8010.htm
- http://m.wap.oexnr.cn/jnews/116260.htm
- http://m.wap.oexnr.cn/jnews/83206.htm
- http://m.wap.oexnr.cn/jnews/0077878.htm
- http://m.wap.oexnr.cn/jnews/7260.htm
- http://m.wap.oexnr.cn/jnews/521003.htm
- http://m.wap.oexnr.cn/jnews/5251.htm
- http://m.wap.oexnr.cn/jnews/21592.htm
- http://m.wap.oexnr.cn/jnews/8729346.htm
- http://m.wap.oexnr.cn/jnews/1399609.htm
- http://m.wap.oexnr.cn/jnews/2755.htm
- http://m.wap.oexnr.cn/jnews/9139171.htm
- http://m.wap.oexnr.cn/jnews/191846.htm
- http://m.wap.oexnr.cn/jnews/01441.htm
- http://m.wap.oexnr.cn/jnews/87120.htm
- http://m.wap.oexnr.cn/jnews/96214.htm
- http://m.wap.oexnr.cn/jnews/445243.htm
- http://m.wap.oexnr.cn/jnews/831193.htm
- http://m.wap.oexnr.cn/jnews/61887.htm
- http://m.wap.oexnr.cn/jnews/04160.htm
- http://m.wap.oexnr.cn/jnews/3913050.htm
- http://m.wap.oexnr.cn/jnews/6864410.htm
- http://m.wap.oexnr.cn/jnews/121600.htm
- http://m.wap.oexnr.cn/jnews/8068.htm
- http://m.wap.oexnr.cn/jnews/2809315.htm
- http://m.wap.oexnr.cn/jnews/1813447.htm
- http://m.wap.oexnr.cn/jnews/35555.htm
- http://m.wap.oexnr.cn/jnews/00493.htm
- http://m.wap.oexnr.cn/jnews/39410.htm
- http://m.wap.oexnr.cn/jnews/3244454.htm
- http://m.wap.oexnr.cn/jnews/4352.htm
- http://m.wap.oexnr.cn/jnews/5910.htm
- http://m.wap.oexnr.cn/jnews/6707439.htm
- http://m.wap.oexnr.cn/jnews/2025620.htm
- http://m.wap.oexnr.cn/jnews/64927.htm
- http://m.wap.oexnr.cn/jnews/1532012.htm
- http://m.wap.oexnr.cn/jnews/657283.htm
- http://m.wap.oexnr.cn/jnews/2042.htm
- http://m.wap.oexnr.cn/jnews/6768415.htm
- http://m.wap.oexnr.cn/jnews/278038.htm
- http://m.wap.oexnr.cn/jnews/6388775.htm
- http://m.wap.oexnr.cn/jnews/1739.htm
- http://m.wap.oexnr.cn/jnews/1460.htm
- http://m.wap.oexnr.cn/jnews/868876.htm
- http://m.wap.oexnr.cn/jnews/18402.htm
- http://m.wap.oexnr.cn/jnews/31167.htm
- http://m.wap.oexnr.cn/jnews/3015685.htm
- http://m.wap.oexnr.cn/jnews/7828.htm
- http://m.wap.oexnr.cn/jnews/570664.htm
- http://m.wap.oexnr.cn/jnews/628823.htm
- http://m.wap.oexnr.cn/jnews/6006.htm
- http://m.wap.oexnr.cn/jnews/4700.htm
- http://m.wap.oexnr.cn/jnews/385856.htm
- http://m.wap.oexnr.cn/jnews/6008824.htm
- http://m.wap.oexnr.cn/jnews/9421.htm
- http://m.wap.oexnr.cn/jnews/9435459.htm
- http://m.wap.oexnr.cn/jnews/23707.htm
- http://m.wap.oexnr.cn/jnews/10713.htm
- http://m.wap.oexnr.cn/jnews/4909.htm
- http://m.wap.oexnr.cn/jnews/383349.htm
- http://m.wap.oexnr.cn/jnews/0093.htm
- http://m.wap.oexnr.cn/jnews/4267.htm
- http://m.wap.oexnr.cn/jnews/6872.htm
- http://m.wap.oexnr.cn/jnews/22716.htm
- http://m.wap.oexnr.cn/jnews/5797781.htm
- http://m.wap.oexnr.cn/jnews/15566.htm
- http://m.wap.oexnr.cn/jnews/0735.htm
- http://m.wap.oexnr.cn/jnews/882156.htm
- http://m.wap.oexnr.cn/jnews/3564080.htm
- http://m.wap.oexnr.cn/jnews/5434324.htm
- http://m.wap.oexnr.cn/jnews/5299173.htm
- http://m.wap.oexnr.cn/jnews/4675.htm
- http://m.wap.oexnr.cn/jnews/5991.htm
- http://m.wap.oexnr.cn/jnews/8389361.htm
- http://m.wap.oexnr.cn/jnews/972662.htm
- http://m.wap.oexnr.cn/jnews/28998.htm
- http://m.wap.oexnr.cn/jnews/405242.htm
- http://m.wap.oexnr.cn/jnews/41225.htm
- http://m.wap.oexnr.cn/jnews/6332.htm
- http://m.wap.oexnr.cn/jnews/3330.htm
- http://m.wap.oexnr.cn/jnews/5896523.htm
- http://m.wap.oexnr.cn/jnews/1287318.htm
- http://m.wap.oexnr.cn/jnews/1241260.htm
- http://m.wap.oexnr.cn/jnews/13219.htm
- http://m.wap.oexnr.cn/jnews/3348047.htm
- http://m.wap.oexnr.cn/jnews/450777.htm
- http://m.wap.oexnr.cn/jnews/2374761.htm
- http://m.wap.oexnr.cn/jnews/000607.htm
- http://m.wap.oexnr.cn/jnews/0129.htm
- http://m.wap.oexnr.cn/jnews/2374086.htm
- http://m.wap.oexnr.cn/jnews/934643.htm
- http://m.wap.oexnr.cn/jnews/6283.htm
- http://m.wap.oexnr.cn/jnews/69123.htm
- http://m.wap.oexnr.cn/jnews/508490.htm
- http://m.wap.oexnr.cn/jnews/13677.htm
- http://m.wap.oexnr.cn/jnews/469190.htm
- http://m.wap.oexnr.cn/jnews/8689.htm
- http://m.wap.oexnr.cn/jnews/6023046.htm
- http://m.wap.oexnr.cn/jnews/111431.htm
- http://m.wap.oexnr.cn/jnews/2058073.htm
- http://m.wap.oexnr.cn/jnews/8283.htm
- http://m.wap.oexnr.cn/jnews/4807818.htm
- http://m.wap.oexnr.cn/jnews/7592.htm
- http://m.wap.oexnr.cn/jnews/4870847.htm
- http://m.wap.oexnr.cn/jnews/944890.htm
- http://m.wap.oexnr.cn/jnews/1114.htm
- http://m.wap.oexnr.cn/jnews/9105082.htm
- http://m.wap.oexnr.cn/jnews/530985.htm
- http://m.wap.oexnr.cn/jnews/61555.htm
- http://m.wap.oexnr.cn/jnews/0852.htm
- http://m.wap.oexnr.cn/jnews/22742.htm
- http://m.wap.oexnr.cn/jnews/7583556.htm
- http://m.wap.oexnr.cn/jnews/5218411.htm
- http://m.wap.oexnr.cn/jnews/963931.htm
- http://m.wap.oexnr.cn/jnews/0514.htm
- http://m.wap.oexnr.cn/jnews/6913.htm
- http://m.wap.oexnr.cn/jnews/9560731.htm
- http://m.wap.oexnr.cn/jnews/7743235.htm
- http://m.wap.oexnr.cn/jnews/557868.htm
- http://m.wap.oexnr.cn/jnews/5345105.htm
- http://m.wap.oexnr.cn/jnews/7724295.htm
- http://m.wap.oexnr.cn/jnews/5944984.htm
- http://m.wap.oexnr.cn/jnews/8480369.htm
- http://m.wap.oexnr.cn/jnews/7650.htm
- http://m.wap.oexnr.cn/jnews/0262.htm
- http://m.wap.oexnr.cn/jnews/148842.htm
- http://m.wap.oexnr.cn/jnews/87288.htm
- http://m.wap.oexnr.cn/jnews/528729.htm
- http://m.wap.oexnr.cn/jnews/400743.htm
- http://m.wap.oexnr.cn/jnews/5805794.htm
- http://m.wap.oexnr.cn/jnews/6705.htm
- http://m.wap.oexnr.cn/jnews/1470061.htm
- http://m.wap.oexnr.cn/jnews/61762.htm
- http://m.wap.oexnr.cn/jnews/3903888.htm
- http://m.wap.oexnr.cn/jnews/1164.htm
- http://m.wap.oexnr.cn/jnews/6057814.htm
- http://m.wap.oexnr.cn/jnews/1372162.htm
- http://m.wap.oexnr.cn/jnews/11740.htm
- http://m.wap.oexnr.cn/jnews/959870.htm
- http://m.wap.oexnr.cn/jnews/0283520.htm
- http://m.wap.oexnr.cn/jnews/4386683.htm
- http://m.wap.oexnr.cn/jnews/85427.htm
- http://m.wap.oexnr.cn/jnews/5571538.htm
- http://m.wap.oexnr.cn/jnews/5092.htm
- http://m.wap.oexnr.cn/jnews/29804.htm
- http://m.wap.oexnr.cn/jnews/2191548.htm
- http://m.wap.oexnr.cn/jnews/6997099.htm
- http://m.wap.oexnr.cn/jnews/175475.htm
- http://m.wap.oexnr.cn/jnews/1922287.htm
- http://m.wap.oexnr.cn/jnews/0434255.htm
- http://m.wap.oexnr.cn/jnews/0357010.htm
- http://m.wap.oexnr.cn/jnews/7526057.htm
- http://m.wap.oexnr.cn/jnews/1341387.htm
- http://m.wap.oexnr.cn/jnews/6559.htm
- http://m.wap.oexnr.cn/jnews/019754.htm
- http://m.wap.oexnr.cn/jnews/79311.htm
- http://m.wap.oexnr.cn/jnews/0703990.htm
- http://m.wap.oexnr.cn/jnews/7126838.htm
- http://m.wap.oexnr.cn/jnews/8987519.htm
- http://m.wap.oexnr.cn/jnews/09472.htm
- http://m.wap.oexnr.cn/jnews/6695153.htm
- http://m.wap.oexnr.cn/jnews/096544.htm
- http://m.wap.oexnr.cn/jnews/14389.htm
- http://m.wap.oexnr.cn/jnews/805234.htm
- http://m.wap.oexnr.cn/jnews/906667.htm
- http://m.wap.oexnr.cn/jnews/87226.htm
- http://m.wap.oexnr.cn/jnews/9981584.htm
- http://m.wap.oexnr.cn/jnews/6235071.htm
- http://m.wap.oexnr.cn/jnews/8300604.htm
- http://m.wap.oexnr.cn/jnews/0099951.htm
- http://m.wap.oexnr.cn/jnews/49712.htm
- http://m.wap.oexnr.cn/jnews/627333.htm
- http://m.wap.oexnr.cn/jnews/765105.htm
- http://m.wap.oexnr.cn/jnews/672416.htm
- http://m.wap.oexnr.cn/jnews/758999.htm
- http://m.wap.oexnr.cn/jnews/343416.htm
- http://m.wap.oexnr.cn/jnews/59776.htm
- http://m.wap.oexnr.cn/jnews/55282.htm
- http://m.wap.oexnr.cn/jnews/512048.htm
- http://m.wap.oexnr.cn/jnews/64879.htm
- http://m.wap.oexnr.cn/jnews/7608585.htm
- http://m.wap.oexnr.cn/jnews/4643.htm
- http://m.wap.oexnr.cn/jnews/08566.htm
- http://m.wap.oexnr.cn/jnews/8704347.htm
- http://m.wap.oexnr.cn/jnews/43398.htm
- http://m.wap.oexnr.cn/jnews/9374.htm
- http://m.wap.oexnr.cn/jnews/5755745.htm
- http://m.wap.oexnr.cn/jnews/5703.htm
- http://m.wap.oexnr.cn/jnews/4400194.htm
- http://m.wap.oexnr.cn/jnews/9391054.htm
- http://m.wap.oexnr.cn/jnews/192697.htm
- http://m.wap.oexnr.cn/jnews/362903.htm
- http://m.wap.oexnr.cn/jnews/68436.htm
- http://m.wap.oexnr.cn/jnews/5537.htm
- http://m.wap.oexnr.cn/jnews/27903.htm
- http://m.wap.oexnr.cn/jnews/60843.htm
- http://m.wap.oexnr.cn/jnews/63854.htm
- http://m.wap.oexnr.cn/jnews/10065.htm
- http://m.wap.oexnr.cn/jnews/75750.htm
- http://m.wap.oexnr.cn/jnews/93959.htm
- http://m.wap.oexnr.cn/jnews/061796.htm
- http://m.wap.oexnr.cn/jnews/5484.htm
- http://m.wap.oexnr.cn/jnews/274673.htm
- http://m.wap.oexnr.cn/jnews/493618.htm
- http://m.wap.oexnr.cn/jnews/5860.htm
- http://m.wap.oexnr.cn/jnews/0210336.htm
- http://m.wap.oexnr.cn/jnews/40637.htm
- http://m.wap.oexnr.cn/jnews/918685.htm
- http://m.wap.oexnr.cn/jnews/35932.htm
- http://m.wap.oexnr.cn/jnews/79430.htm
- http://m.wap.oexnr.cn/jnews/973428.htm
- http://m.wap.oexnr.cn/jnews/1413362.htm
- http://m.wap.oexnr.cn/jnews/0061637.htm
- http://m.wap.oexnr.cn/jnews/1192413.htm
- http://m.wap.oexnr.cn/jnews/5199551.htm
- http://m.wap.oexnr.cn/jnews/9663.htm

## 项目结构

项目采用模块化分层设计，核心逻辑与 CLI、Web 层解耦，便于二次开发与单元测试。

```
webindex-gateway/
├── src/                                  # 核心源代码目录
│   ├── webindex/                         # 主包
│   │   ├── __init__.py                   # 版本号与导出符号定义
│   │   ├── importer/                     # 导入模块：支持多种格式解析
│   │   │   ├── __init__.py
│   │   │   ├── csv_loader.py             # CSV 格式解析器
│   │   │   └── lines_loader.py           # 纯文本行格式解析器
│   │   ├── checker/                      # 健康检查模块
│   │   │   ├── __init__.py
│   │   │   ├── client.py                 # 异步 HTTP 客户端封装
│   │   │   └── reporter.py               # 报告生成器（JSON/CSV/Markdown）
│   │   ├── storage/                      # 存储层
│   │   │   ├── __init__.py
│   │   │   ├── database.py               # SQLite 连接与表结构管理
│   │   │   └── repository.py             # CRUD 操作封装
│   │   ├── api/                          # RESTful API 端点
│   │   │   ├── __init__.py
│   │   │   ├── routes.py                 # FastAPI 路由注册
│   │   │   └── schemas.py                # Pydantic 请求/响应模型
│   │   └── cli/                          # 命令行子命令
│   │       ├── __init__.py
│   │       ├── main.py                   # click 入口与全局选项
│   │       ├── import_cmd.py             # webindex import 实现
│   │       ├── check_cmd.py              # webindex check 实现
│   │       ├── export_cmd.py             # webindex export 实现
│   │       └── stats_cmd.py              # webindex stats 实现
├── tests/                                # 单元测试与集成测试
│   ├── conftest.py                       # pytest 共享 fixture
│   ├── test_importer.py
│   ├── test_checker.py
│   └── test_storage.py
├── docs/                                 # 文档源文件
│   ├── getting-started.md
│   ├── cli-reference.md
│   ├── api-specification.yaml
│   └── operations-guide.md
├── scripts/                              # 运维辅助脚本
│   ├── init_db.sql                       # 手动建表 DDL
│   └── daily_check_cron.sh               # 每日巡检定时任务示例
├── pyproject.toml                        # 项目元数据与构建配置
├── README.md                             # 本文件
└── LICENSE                               # MIT 许可证文本
```

## 贡献指南

我们欢迎并鼓励社区提交各类改进，包括但不限于新增解析器、优化检查并发模型、完善文档与增加测试用例。请遵循以下流程：

1. 在 GitHub 上 fork 本仓库，并克隆至本地开发环境。确保基于 `main` 分支创建新的功能分支，分支命名建议采用 `feat/` 或 `fix/` 前缀，例如 `feat/add-jsonlines-importer`。

2. 编写代码时请遵循 PEP 8 风格，并使用 `black` 与 `isort` 进行自动格式化。所有新增功能必须包含对应的单元测试，测试覆盖率不低于 80%。本地运行 `pytest tests/` 确保全部通过。

3. 提交前请更新相关文档，包括但不限于 `docs/` 目录下的使用说明与 `README.md` 中的功能列表。若涉及 CLI 变更，需同步更新 `cli-reference.md` 中的示例。

4. 发起 Pull Request 至 `main` 分支，并在描述中清晰说明改动目的、实现方案与测试结果。PR 标题请遵循 Conventional Commits 规范，如 `feat(importer): support JSON Lines format`。

5. 核心维护者将在 3 个工作日内进行 Code Review，可能会要求补充测试或调整实现细节。合并后，您的贡献将出现在下一版本的发布说明中。

## 常见问题

Q: 导入 URL 时提示 "invalid scheme"，但我的链接确实是 http 开头，为什么？

A: 系统默认仅允许 http 与 https 协议，但会校验 URL 格式是否严格符合 RFC 3986。若您使用纯文本行导入，请确保每行没有首尾空白字符，且不包含 HTML 标签或额外描述文字。您可以使用 `webindex import --strip` 参数自动清理每行的空白与不可见字符。

Q: 健康检查并发数设置为多少比较合适？

A: 推荐值取决于您的网络环境与目标服务器的承受能力。对于移动端资讯类站点，建议并发数控制在 30 至 50 之间，超时设为 5 秒。若检查过程中出现大量超时或连接错误，可适当降低并发并增加超时时间。您也可以使用 `--retry 2` 参数开启自动重试，提升有效成功率。

Q: 如何将本系统部署为长期运行的 Web 服务？

A: 项目内置了 FastAPI 服务，您可以使用 `uvicorn webindex.api:app --host 0.0.0.0 --port 8000` 启动。生产环境建议配合 systemd 或 supervisor 进行进程管理，并使用 nginx 作为反向代理以处理静态资源与 TLS 终结。详细配置步骤请参考 `docs/operations-guide.md` 中的部署章节。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
