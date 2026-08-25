# LinkCatalog Core

LinkCatalog Core 是一个面向技术文档维护者、知识库管理员和开源项目贡献者的外链资源归集与结构化呈现工具。该项目并非简单的网址导航，而是围绕批量原始链接进行元数据提取、分类标注、有效性校验与多格式导出的自动化流水线。其核心定位是解决技术写作与项目文档中大量零散引用链接难以维护、难以追溯变更、难以批量检查可用性的问题。目标用户包括技术文档工程师、开源项目维护者、技术社区运营人员以及需要长期管理大量外链引用的研究人员。LinkCatalog Core 不依赖特定云服务，可完全本地化运行，输出标准 Markdown 与 JSON 格式数据，便于集成到静态站点生成器或 CI/CD 文档发布流程中。

## 功能概览

**批量链接导入解析**：支持从纯文本列表、CSV 以及 Markdown 表格中批量导入原始 URL，自动识别协议类型与域名结构，并对异常格式进行初步清洗与标准化提示。

**元数据自动提取**：对每个导入的链接尝试发起轻量级 HEAD 请求，获取响应状态码、内容类型、最后修改时间等基础元数据，为后续有效性判断提供依据。

**自定义标签分类**：允许用户为每个链接分配多个层级标签（如 source/official/archive/reference），并支持基于标签组合的快速筛选与统计。

**状态监控与变更报告**：定期或按需对已收录链接进行可用性重检，生成状态变更报告，标记响应超时、状态码异常、内容类型变动等情形，输出差异对比数据。

**多格式文档生成**：将链接数据按照可配置模板渲染为 Markdown 列表、JSON 数组或 HTML 表格，其中 Markdown 输出严格遵循原始 URL 原样呈现规则，不添加任何额外修饰。

**全文检索与过滤**：内置简单的关键词检索接口，支持按域名、状态码、标签组合、最后检查时间等维度进行复合过滤，便于快速定位特定资源。

**数据导入导出兼容性**：支持将链接数据导出为 CSV 格式，便于在电子表格软件中进一步处理；同时支持从 JSON 备份文件完整恢复目录状态。

## 应用场景

技术文档外链审计与清理：技术文档中往往包含大量外部引用链接，这些链接随时间推移可能失效或被重定向。文档维护者可使用 LinkCatalog Core 定期扫描整个文档目录中提取出的链接列表，快速获得失效链接清单，并有针对性地进行更新或替换，避免发布后出现死链影响阅读体验。

开源项目 README 资源汇总管理：开源项目维护者需要在 README 中列出相关工具、文档、社区论坛等外部资源。随着项目发展，这些资源列表会不断增删调整。LinkCatalog Core 可以帮助维护者统一管理这些链接的原始记录，并在生成最终 README 时确保所有 URL 原样输出，符合各类开源社区对引用格式的严格要求。

技术资料归档与镜像站点同步：在进行技术资料离线归档或搭建内部镜像站点时，需要准确记录原始资源的网络位置。LinkCatalog Core 可作为外部链接索引工具，协助归档人员生成完整的引用清单，并在镜像部署后批量验证各资源在内外网环境下的可达性差异。

技术社区内容聚合与推荐：技术社区运营人员可以定期从社区讨论、博客文章、项目仓库中收集优质外部链接，通过 LinkCatalog Core 进行统一编号与分类，再以标准化格式输出到社区周报、资源推荐页面或知识库中，提升内容聚合效率。

## 快速开始

以下指令演示如何在 Linux 或 macOS 环境下从源码启动 LinkCatalog Core 服务，并执行一次示例链接导入与状态检查。

```bash
git clone https://github.com/linkcatalog/core.git
cd linkcatalog-core
pip install -r requirements.txt
cp config.example.yml config.yml
python main.py --import samples/links.txt --check --output report.md
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，类型提示与异步特性依赖 |
| pip | 21.0 及以上 | 包管理工具，用于安装依赖库 |
| aiohttp | 3.8.0 及以上 | 异步 HTTP 客户端，用于批量链接状态检查 |
| pyyaml | 6.0 及以上 | 配置文件解析，支持 YAML 格式的配置项 |
| markdown | 3.4.0 及以上 | Markdown 格式输出渲染，用于生成文档 |
| pytest | 7.0.0 及以上 | 单元测试框架，仅在开发环境中需要 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | docs/user-guide.md | 如何安装、配置、执行基本导入与导出操作 |
| 配置参考 | docs/config-reference.md | 配置文件每一项参数的含义与可选值 |
| 开发指南 | docs/development.md | 项目代码结构、编码规范与本地调试方法 |
| API 接口 | docs/api/http-endpoints.md | 如果启用 Web 模式，各端点的请求与响应格式 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/9445908.htm
- http://m.wap.ghtkgg.cn/jnews/7114.htm
- http://m.wap.ghtkgg.cn/jnews/6023477.htm
- http://m.wap.ghtkgg.cn/jnews/8853257.htm
- http://m.wap.ghtkgg.cn/jnews/94722.htm
- http://m.wap.ghtkgg.cn/jnews/2885.htm
- http://m.wap.ghtkgg.cn/jnews/552666.htm
- http://m.wap.ghtkgg.cn/jnews/5838.htm
- http://m.wap.ghtkgg.cn/jnews/64738.htm
- http://m.wap.ghtkgg.cn/jnews/0224.htm
- http://m.wap.ghtkgg.cn/jnews/761620.htm
- http://m.wap.ghtkgg.cn/jnews/7789197.htm
- http://m.wap.ghtkgg.cn/jnews/88280.htm
- http://m.wap.ghtkgg.cn/jnews/894496.htm
- http://m.wap.ghtkgg.cn/jnews/3894.htm
- http://m.wap.ghtkgg.cn/jnews/75888.htm
- http://m.wap.ghtkgg.cn/jnews/6799.htm
- http://m.wap.ghtkgg.cn/jnews/900689.htm
- http://m.wap.ghtkgg.cn/jnews/6328224.htm
- http://m.wap.ghtkgg.cn/jnews/8342.htm
- http://m.wap.ghtkgg.cn/jnews/684916.htm
- http://m.wap.ghtkgg.cn/jnews/0024.htm
- http://m.wap.ghtkgg.cn/jnews/7145.htm
- http://m.wap.ghtkgg.cn/jnews/2471957.htm
- http://m.wap.ghtkgg.cn/jnews/24371.htm
- http://m.wap.ghtkgg.cn/jnews/27580.htm
- http://m.wap.ghtkgg.cn/jnews/2705187.htm
- http://m.wap.ghtkgg.cn/jnews/95440.htm
- http://m.wap.ghtkgg.cn/jnews/09886.htm
- http://m.wap.ghtkgg.cn/jnews/727172.htm
- http://m.wap.ghtkgg.cn/jnews/2527362.htm
- http://m.wap.ghtkgg.cn/jnews/1555569.htm
- http://m.wap.ghtkgg.cn/jnews/8301768.htm
- http://m.wap.ghtkgg.cn/jnews/0743.htm
- http://m.wap.ghtkgg.cn/jnews/43884.htm
- http://m.wap.ghtkgg.cn/jnews/29567.htm
- http://m.wap.ghtkgg.cn/jnews/457563.htm
- http://m.wap.ghtkgg.cn/jnews/9492181.htm
- http://m.wap.ghtkgg.cn/jnews/56628.htm
- http://m.wap.ghtkgg.cn/jnews/53485.htm
- http://m.wap.ghtkgg.cn/jnews/654040.htm
- http://m.wap.ghtkgg.cn/jnews/168906.htm
- http://m.wap.ghtkgg.cn/jnews/9514.htm
- http://m.wap.ghtkgg.cn/jnews/217261.htm
- http://m.wap.ghtkgg.cn/jnews/842588.htm
- http://m.wap.ghtkgg.cn/jnews/2450773.htm
- http://m.wap.ghtkgg.cn/jnews/2612236.htm
- http://m.wap.ghtkgg.cn/jnews/44734.htm
- http://m.wap.ghtkgg.cn/jnews/4110.htm
- http://m.wap.ghtkgg.cn/jnews/24790.htm
- http://m.wap.ghtkgg.cn/jnews/879547.htm
- http://m.wap.ghtkgg.cn/jnews/8132.htm
- http://m.wap.ghtkgg.cn/jnews/955324.htm
- http://m.wap.ghtkgg.cn/jnews/051652.htm
- http://m.wap.ghtkgg.cn/jnews/42684.htm
- http://m.wap.ghtkgg.cn/jnews/9705.htm
- http://m.wap.ghtkgg.cn/jnews/0551443.htm
- http://m.wap.ghtkgg.cn/jnews/8427940.htm
- http://m.wap.ghtkgg.cn/jnews/3037844.htm
- http://m.wap.ghtkgg.cn/jnews/8026.htm
- http://m.wap.ghtkgg.cn/jnews/7122.htm
- http://m.wap.ghtkgg.cn/jnews/4902925.htm
- http://m.wap.ghtkgg.cn/jnews/2904.htm
- http://m.wap.ghtkgg.cn/jnews/4258596.htm
- http://m.wap.ghtkgg.cn/jnews/5349.htm
- http://m.wap.ghtkgg.cn/jnews/2619077.htm
- http://m.wap.ghtkgg.cn/jnews/13328.htm
- http://m.wap.ghtkgg.cn/jnews/28642.htm
- http://m.wap.ghtkgg.cn/jnews/3121966.htm
- http://m.wap.ghtkgg.cn/jnews/4668659.htm
- http://m.wap.ghtkgg.cn/jnews/617941.htm
- http://m.wap.ghtkgg.cn/jnews/7535737.htm
- http://m.wap.ghtkgg.cn/jnews/29085.htm
- http://m.wap.ghtkgg.cn/jnews/745726.htm
- http://m.wap.ghtkgg.cn/jnews/145933.htm
- http://m.wap.ghtkgg.cn/jnews/529333.htm
- http://m.wap.ghtkgg.cn/jnews/459936.htm
- http://m.wap.ghtkgg.cn/jnews/693428.htm
- http://m.wap.ghtkgg.cn/jnews/381623.htm
- http://m.wap.ghtkgg.cn/jnews/09565.htm
- http://m.wap.ghtkgg.cn/jnews/66077.htm
- http://m.wap.ghtkgg.cn/jnews/721409.htm
- http://m.wap.ghtkgg.cn/jnews/995038.htm
- http://m.wap.ghtkgg.cn/jnews/486788.htm
- http://m.wap.ghtkgg.cn/jnews/211683.htm
- http://m.wap.ghtkgg.cn/jnews/975531.htm
- http://m.wap.ghtkgg.cn/jnews/8988330.htm
- http://m.wap.ghtkgg.cn/jnews/878287.htm
- http://m.wap.ghtkgg.cn/jnews/6286378.htm
- http://m.wap.ghtkgg.cn/jnews/78473.htm
- http://m.wap.ghtkgg.cn/jnews/957799.htm
- http://m.wap.ghtkgg.cn/jnews/39348.htm
- http://m.wap.ghtkgg.cn/jnews/6876.htm
- http://m.wap.ghtkgg.cn/jnews/6202983.htm
- http://m.wap.ghtkgg.cn/jnews/1884.htm
- http://m.wap.ghtkgg.cn/jnews/0360.htm
- http://m.wap.ghtkgg.cn/jnews/484824.htm
- http://m.wap.ghtkgg.cn/jnews/9453579.htm
- http://m.wap.ghtkgg.cn/jnews/12022.htm
- http://m.wap.ghtkgg.cn/jnews/92048.htm
- http://m.wap.ghtkgg.cn/jnews/146301.htm
- http://m.wap.ghtkgg.cn/jnews/6790438.htm
- http://m.wap.ghtkgg.cn/jnews/2989704.htm
- http://m.wap.ghtkgg.cn/jnews/593945.htm
- http://m.wap.ghtkgg.cn/jnews/14011.htm
- http://m.wap.ghtkgg.cn/jnews/26913.htm
- http://m.wap.ghtkgg.cn/jnews/517772.htm
- http://m.wap.ghtkgg.cn/jnews/24273.htm
- http://m.wap.ghtkgg.cn/jnews/13866.htm
- http://m.wap.ghtkgg.cn/jnews/4858336.htm
- http://m.wap.ghtkgg.cn/jnews/0351.htm
- http://m.wap.ghtkgg.cn/jnews/8336.htm
- http://m.wap.ghtkgg.cn/jnews/4587.htm
- http://m.wap.ghtkgg.cn/jnews/500613.htm
- http://m.wap.ghtkgg.cn/jnews/4880.htm
- http://m.wap.ghtkgg.cn/jnews/3874.htm
- http://m.wap.ghtkgg.cn/jnews/1033.htm
- http://m.wap.ghtkgg.cn/jnews/87699.htm
- http://m.wap.ghtkgg.cn/jnews/52508.htm
- http://m.wap.ghtkgg.cn/jnews/5884041.htm
- http://m.wap.ghtkgg.cn/jnews/78499.htm
- http://m.wap.ghtkgg.cn/jnews/730294.htm
- http://m.wap.ghtkgg.cn/jnews/2318.htm
- http://m.wap.ghtkgg.cn/jnews/85383.htm
- http://m.wap.ghtkgg.cn/jnews/4910156.htm
- http://m.wap.ghtkgg.cn/jnews/78189.htm
- http://m.wap.ghtkgg.cn/jnews/2712.htm
- http://m.wap.ghtkgg.cn/jnews/30472.htm
- http://m.wap.ghtkgg.cn/jnews/70652.htm
- http://m.wap.ghtkgg.cn/jnews/297937.htm
- http://m.wap.ghtkgg.cn/jnews/258056.htm
- http://m.wap.ghtkgg.cn/jnews/12588.htm
- http://m.wap.ghtkgg.cn/jnews/3704245.htm
- http://m.wap.ghtkgg.cn/jnews/013456.htm
- http://m.wap.ghtkgg.cn/jnews/779467.htm
- http://m.wap.ghtkgg.cn/jnews/200397.htm
- http://m.wap.ghtkgg.cn/jnews/3015252.htm
- http://m.wap.ghtkgg.cn/jnews/26801.htm
- http://m.wap.ghtkgg.cn/jnews/8972225.htm
- http://m.wap.ghtkgg.cn/jnews/3252549.htm
- http://m.wap.ghtkgg.cn/jnews/26653.htm
- http://m.wap.ghtkgg.cn/jnews/832940.htm
- http://m.wap.ghtkgg.cn/jnews/297471.htm
- http://m.wap.ghtkgg.cn/jnews/64602.htm
- http://m.wap.ghtkgg.cn/jnews/2999350.htm
- http://m.wap.ghtkgg.cn/jnews/5977925.htm
- http://m.wap.ghtkgg.cn/jnews/31146.htm
- http://m.wap.ghtkgg.cn/jnews/21912.htm
- http://m.wap.ghtkgg.cn/jnews/76143.htm
- http://m.wap.ghtkgg.cn/jnews/8993703.htm
- http://m.wap.ghtkgg.cn/jnews/999843.htm
- http://m.wap.ghtkgg.cn/jnews/321731.htm
- http://m.wap.ghtkgg.cn/jnews/29586.htm
- http://m.wap.ghtkgg.cn/jnews/16765.htm
- http://m.wap.ghtkgg.cn/jnews/35309.htm
- http://m.wap.ghtkgg.cn/jnews/0784.htm
- http://m.wap.ghtkgg.cn/jnews/7548931.htm
- http://m.wap.ghtkgg.cn/jnews/87262.htm
- http://m.wap.ghtkgg.cn/jnews/675315.htm
- http://m.wap.ghtkgg.cn/jnews/799223.htm
- http://m.wap.ghtkgg.cn/jnews/4318082.htm
- http://m.wap.ghtkgg.cn/jnews/69016.htm
- http://m.wap.ghtkgg.cn/jnews/4067325.htm
- http://m.wap.ghtkgg.cn/jnews/7327.htm
- http://m.wap.ghtkgg.cn/jnews/5573.htm
- http://m.wap.ghtkgg.cn/jnews/9677270.htm
- http://m.wap.ghtkgg.cn/jnews/3987.htm
- http://m.wap.ghtkgg.cn/jnews/3084903.htm
- http://m.wap.ghtkgg.cn/jnews/9560.htm
- http://m.wap.ghtkgg.cn/jnews/5156.htm
- http://m.wap.ghtkgg.cn/jnews/64593.htm
- http://m.wap.ghtkgg.cn/jnews/0829.htm
- http://m.wap.ghtkgg.cn/jnews/2583.htm
- http://m.wap.ghtkgg.cn/jnews/7045.htm
- http://m.wap.ghtkgg.cn/jnews/814463.htm
- http://m.wap.ghtkgg.cn/jnews/6413866.htm
- http://m.wap.ghtkgg.cn/jnews/43041.htm
- http://m.wap.ghtkgg.cn/jnews/2572.htm
- http://m.wap.ghtkgg.cn/jnews/2442.htm
- http://m.wap.ghtkgg.cn/jnews/7082.htm
- http://m.wap.ghtkgg.cn/jnews/9052.htm
- http://m.wap.ghtkgg.cn/jnews/89922.htm
- http://m.wap.ghtkgg.cn/jnews/479142.htm
- http://m.wap.ghtkgg.cn/jnews/3133054.htm
- http://m.wap.ghtkgg.cn/jnews/5250.htm
- http://m.wap.ghtkgg.cn/jnews/607320.htm
- http://m.wap.ghtkgg.cn/jnews/7754346.htm
- http://m.wap.ghtkgg.cn/jnews/95727.htm
- http://m.wap.ghtkgg.cn/jnews/3180142.htm
- http://m.wap.ghtkgg.cn/jnews/98363.htm
- http://m.wap.ghtkgg.cn/jnews/91209.htm
- http://m.wap.ghtkgg.cn/jnews/312138.htm
- http://m.wap.ghtkgg.cn/jnews/90889.htm
- http://m.wap.ghtkgg.cn/jnews/7047.htm
- http://m.wap.ghtkgg.cn/jnews/4502550.htm
- http://m.wap.ghtkgg.cn/jnews/9164325.htm
- http://m.wap.ghtkgg.cn/jnews/9149.htm
- http://m.wap.ghtkgg.cn/jnews/07404.htm
- http://m.wap.ghtkgg.cn/jnews/22997.htm
- http://m.wap.ghtkgg.cn/jnews/5537347.htm
- http://m.wap.ghtkgg.cn/jnews/627685.htm
- http://m.wap.ghtkgg.cn/jnews/4271021.htm
- http://m.wap.ghtkgg.cn/jnews/86128.htm
- http://m.wap.ghtkgg.cn/jnews/0835.htm
- http://m.wap.ghtkgg.cn/jnews/4767.htm
- http://m.wap.ghtkgg.cn/jnews/331781.htm
- http://m.wap.ghtkgg.cn/jnews/3854515.htm
- http://m.wap.ghtkgg.cn/jnews/169356.htm
- http://m.wap.ghtkgg.cn/jnews/8647.htm
- http://m.wap.ghtkgg.cn/jnews/28199.htm
- http://m.wap.ghtkgg.cn/jnews/62676.htm
- http://m.wap.ghtkgg.cn/jnews/97071.htm
- http://m.wap.ghtkgg.cn/jnews/3210420.htm
- http://m.wap.ghtkgg.cn/jnews/69540.htm
- http://m.wap.ghtkgg.cn/jnews/8621880.htm
- http://m.wap.ghtkgg.cn/jnews/5528696.htm
- http://m.wap.ghtkgg.cn/jnews/749567.htm
- http://m.wap.ghtkgg.cn/jnews/593403.htm
- http://m.wap.ghtkgg.cn/jnews/2624510.htm
- http://m.wap.ghtkgg.cn/jnews/650804.htm
- http://m.wap.ghtkgg.cn/jnews/91871.htm
- http://m.wap.ghtkgg.cn/jnews/2179648.htm
- http://m.wap.ghtkgg.cn/jnews/593590.htm
- http://m.wap.ghtkgg.cn/jnews/9186549.htm
- http://m.wap.ghtkgg.cn/jnews/365482.htm
- http://m.wap.ghtkgg.cn/jnews/557966.htm
- http://m.wap.ghtkgg.cn/jnews/78910.htm
- http://m.wap.ghtkgg.cn/jnews/2579557.htm
- http://m.wap.ghtkgg.cn/jnews/86858.htm
- http://m.wap.ghtkgg.cn/jnews/947132.htm
- http://m.wap.ghtkgg.cn/jnews/6241.htm
- http://m.wap.ghtkgg.cn/jnews/1688293.htm
- http://m.wap.ghtkgg.cn/jnews/8079100.htm
- http://m.wap.ghtkgg.cn/jnews/05050.htm
- http://m.wap.ghtkgg.cn/jnews/013259.htm
- http://m.wap.ghtkgg.cn/jnews/4056230.htm
- http://m.wap.ghtkgg.cn/jnews/6481.htm
- http://m.wap.ghtkgg.cn/jnews/803298.htm
- http://m.wap.ghtkgg.cn/jnews/5131.htm
- http://m.wap.ghtkgg.cn/jnews/645149.htm
- http://m.wap.ghtkgg.cn/jnews/22918.htm
- http://m.wap.ghtkgg.cn/jnews/4398.htm
- http://m.wap.ghtkgg.cn/jnews/52274.htm
- http://m.wap.ghtkgg.cn/jnews/0273554.htm
- http://m.wap.ghtkgg.cn/jnews/464518.htm
- http://m.wap.ghtkgg.cn/jnews/803710.htm
- http://m.wap.ghtkgg.cn/jnews/932747.htm
- http://m.wap.ghtkgg.cn/jnews/9300470.htm
- http://m.wap.ghtkgg.cn/jnews/34857.htm
- http://m.wap.ghtkgg.cn/jnews/607252.htm
- http://m.wap.ghtkgg.cn/jnews/2151.htm
- http://m.wap.ghtkgg.cn/jnews/411545.htm
- http://m.wap.ghtkgg.cn/jnews/4481.htm
- http://m.wap.ghtkgg.cn/jnews/2810042.htm
- http://m.wap.ghtkgg.cn/jnews/254265.htm
- http://m.wap.ghtkgg.cn/jnews/9765745.htm
- http://m.wap.ghtkgg.cn/jnews/47407.htm
- http://m.wap.ghtkgg.cn/jnews/8177759.htm
- http://m.wap.ghtkgg.cn/jnews/67251.htm
- http://m.wap.ghtkgg.cn/jnews/903308.htm
- http://m.wap.ghtkgg.cn/jnews/3509458.htm
- http://m.wap.ghtkgg.cn/jnews/32297.htm
- http://m.wap.ghtkgg.cn/jnews/34179.htm
- http://m.wap.ghtkgg.cn/jnews/7681.htm
- http://m.wap.ghtkgg.cn/jnews/575718.htm
- http://m.wap.ghtkgg.cn/jnews/2355598.htm
- http://m.wap.ghtkgg.cn/jnews/5921.htm
- http://m.wap.ghtkgg.cn/jnews/78778.htm
- http://m.wap.ghtkgg.cn/jnews/2625.htm
- http://m.wap.ghtkgg.cn/jnews/13884.htm
- http://m.wap.ghtkgg.cn/jnews/4924.htm
- http://m.wap.ghtkgg.cn/jnews/86896.htm
- http://m.wap.ghtkgg.cn/jnews/293719.htm
- http://m.wap.ghtkgg.cn/jnews/61879.htm
- http://m.wap.ghtkgg.cn/jnews/2795516.htm
- http://m.wap.ghtkgg.cn/jnews/064258.htm
- http://m.wap.ghtkgg.cn/jnews/3911835.htm
- http://m.wap.ghtkgg.cn/jnews/1334846.htm
- http://m.wap.ghtkgg.cn/jnews/904761.htm
- http://m.wap.ghtkgg.cn/jnews/1836995.htm
- http://m.wap.ghtkgg.cn/jnews/2666.htm
- http://m.wap.ghtkgg.cn/jnews/4676436.htm
- http://m.wap.ghtkgg.cn/jnews/9603406.htm
- http://m.wap.ghtkgg.cn/jnews/7730693.htm
- http://m.wap.ghtkgg.cn/jnews/8170.htm
- http://m.wap.ghtkgg.cn/jnews/61167.htm
- http://m.wap.ghtkgg.cn/jnews/3117.htm
- http://m.wap.ghtkgg.cn/jnews/5775.htm
- http://m.wap.ghtkgg.cn/jnews/5639055.htm
- http://m.wap.ghtkgg.cn/jnews/527734.htm
- http://m.wap.ghtkgg.cn/jnews/800407.htm
- http://m.wap.ghtkgg.cn/jnews/4889533.htm
- http://m.wap.ghtkgg.cn/jnews/350743.htm
- http://m.wap.ghtkgg.cn/jnews/67644.htm
- http://m.wap.ghtkgg.cn/jnews/8871170.htm
- http://m.wap.ghtkgg.cn/jnews/9842041.htm
- http://m.wap.ghtkgg.cn/jnews/74352.htm
- http://m.wap.ghtkgg.cn/jnews/5646.htm
- http://m.wap.ghtkgg.cn/jnews/4599184.htm
- http://m.wap.ghtkgg.cn/jnews/45395.htm

## 项目结构

```
linkcatalog-core/
├── main.py                      # 命令行入口，解析参数并调度核心流程
├── config.yml                   # 主配置文件，包含检查间隔、输出模板路径等
├── requirements.txt             # Python 依赖列表
├── src/                         # 核心源码目录
│   ├── importer/                # 导入模块，负责解析不同格式的输入文件
│   │   ├── parser.py            # 纯文本、CSV、Markdown 表格解析器
│   │   └── validator.py         # URL 格式校验与规范化处理
│   ├── checker/                 # 链接状态检查模块
│   │   ├── http_client.py       # 基于 aiohttp 的异步请求封装
│   │   ├── status.py            # 状态码与内容类型判读逻辑
│   │   └── reporter.py          # 生成状态变更报告
│   ├── catalog/                 # 目录数据管理模块
│   │   ├── record.py            # 单条链接记录的数据类定义
│   │   ├── store.py             # 内存与文件存储操作（JSON 序列化）
│   │   └── filter.py            # 标签、状态、关键词复合过滤器
│   ├── renderer/                # 多格式输出渲染模块
│   │   ├── markdown.py          # Markdown 列表生成器，严格按原样输出 URL
│   │   ├── json_exporter.py     # JSON 格式导出
│   │   └── csv_exporter.py      # CSV 表格导出
│   └── utils/                   # 通用工具函数
│       ├── logger.py            # 日志配置与输出
│       └── time_utils.py        # 时间戳格式化与比较辅助
├── tests/                       # 单元测试目录
│   ├── test_parser.py
│   ├── test_checker.py
│   └── test_renderer.py
├── samples/                     # 示例数据目录
│   ├── links.txt                # 纯文本链接示例
│   └── sample_report.md         # 生成的报告样例
└── docs/                        # 文档目录
    ├── user-guide.md
    ├── config-reference.md
    ├── development.md
    └── api/
        └── http-endpoints.md
```

## 贡献指南

1. 阅读开发指南文档 docs/development.md，了解项目代码风格要求，包括 Python 类型注解、异步函数编写规范以及 pytest 测试用例的命名约定。

2. 在 GitHub 仓库中创建一个新的 issue 描述你希望修复的问题或新增的功能，等待维护者确认需求范围，避免重复工作或不必要的代码变动。

3. 从 main 分支派生一个新的功能分支，分支命名格式为 feature/简短描述 或 fix/问题编号，在该分支上进行代码修改和本地测试。

4. 提交代码前运行完整的测试套件，确保所有已有测试用例通过，并为新增功能或修复编写对应的测试用例，保证测试覆盖率不低于原有水平。

5. 提交 Pull Request 到主仓库，在 PR 描述中关联对应的 issue 编号，并简要说明改动内容与测试结果，等待代码审查与合并。

## 常见问题

问题：导入大量链接时，程序是否会因为网络请求过慢而阻塞？

回答：LinkCatalog Core 默认使用异步 HTTP 客户端 aiohttp，并支持配置并发请求数量上限。在导入阶段如果仅执行解析而不执行检查，则不会有任何网络请求，速度极快。若在导入时同时启用 --check 参数，系统会以配置的并发度（默认为 50）分批发起 HEAD 请求，避免同时打开过多连接导致本地端口耗尽或目标服务器限流。

问题：生成的 Markdown 报告中，URL 是否会被自动转换为超链接格式？

回答：不会。LinkCatalog Core 的 Markdown 渲染器对 URL 字段做纯文本输出，不添加任何方括号或圆括号结构，也不添加 HTML 标签。这确保了在任何 Markdown 解析器下，URL 均以原始字符串形式呈现，满足需要原样展示链接地址的场景，例如在纯文本环境或需要人工逐条核对链接的审查流程中。

问题：如何定期自动检查所有链接的有效性并生成更新报告？

回答：项目提供了一个独立的调度脚本 scheduler.py，可通过系统 cron 或 systemd timer 定期触发。用户需在 config.yml 中配置检查间隔（单位小时）和报告输出路径，调度脚本会自动加载完整目录数据，执行全量检查，并将状态变更部分追加写入按日期命名的报告文件中，同时保留历史检查记录用于对比分析。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:05
