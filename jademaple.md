# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与外链管理场景的开源工具集，定位于对海量外部新闻链接进行批量采集、结构化存储与快速检索。项目目标用户包括技术内容运营者、舆情监控工程师、个人站长以及需要定期处理大量外链资源的开发者。通过统一的链接处理流水线，解决分散来源新闻链接难以规整、去重、分类与持久化的问题。

## 功能概览

批量链接导入：支持从纯文本、CSV 及 JSON 格式批量导入原始 URL 列表，自动识别协议头与域名结构。

链接状态检测：对每条外链执行 HTTP 状态码检查，标记失效、重定向或可访问状态，支持超时与重试策略配置。

元信息提取：从目标页面自动抽取标题、发布时间、正文摘要与关键词，生成结构化元数据用于后续筛选。

规则化标签系统：基于域名、路径模式与内容特征，为用户提供可定制的自动打标规则引擎，便于分类管理。

去重与历史比对：维护本地链接库，对新导入链接进行 MD5 或完整 URL 去重，避免重复处理相同资源。

检索与过滤：提供按状态、标签、时间范围和来源域名的组合过滤查询，支持正则表达式匹配路径或查询参数。

导出集成：支持将筛选后的链接集导出为 Markdown 列表、JSON 数组或纯文本清单，便于嵌入文档或下游系统。

监控与日志：记录每次批量操作的执行时间、成功数与失败数，提供详细错误日志用于问题回溯。

## 应用场景

技术内容聚合站点维护：运营人员每日收集数十条技术新闻链接，使用 NewsLink Aggregator 批量导入并进行状态检测，自动剔除已失效链接，再将有效链接按来源域名分组，生成每日更新列表。

舆情监控数据预处理：舆情分析团队从多个监控源获取大量新闻 URL，通过元信息提取模块快速获取每条链接的标题与发布时间，过滤出指定时间窗口内的链接，供后续情感分析模型使用。

个人知识库外链管理：个人笔记或博客作者维护外部参考资料链接库，利用去重与标签系统按主题分类，定期运行状态检测以清理死链，保持知识库的可用性。

批量链接迁移与清洗：在站点改版或域名更换场景下，将旧站所有外链导入工具，通过规则化标签系统识别需要保留或替换的链接集合，导出清洗后的链接清单用于新站部署。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆项目仓库
git clone https://github.com/example/newslink-aggregator.git
cd newslink-aggregator

# 安装依赖（使用 pip 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 运行初始导入示例（将 urls.txt 替换为实际链接文件）
python main.py import --input urls.txt --output data/imported.json
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行环境，推荐 3.10 长期支持版 |
| pip | 20.0 及以上 | 包管理工具，用于安装第三方库 |
| requests | 2.25.0 及以上 | HTTP 请求库，用于链接状态检测与页面抓取 |
| beautifulsoup4 | 4.9.0 及以上 | HTML 解析库，用于元信息提取 |
| lxml | 4.6.0 及以上 | 高性能 XML/HTML 解析器，作为 beautifulsoup4 后端 |
| jsonschema | 3.2.0 及以上 | JSON 结构校验，用于导入数据格式验证 |
| pytest | 6.0.0 及以上 | 单元测试框架，仅开发环境必需 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何导入链接、配置标签规则、执行状态检测与导出结果 |
| 配置参考 | docs/config-reference.md | 所有命令行参数与配置文件字段的详细说明及默认值 |
| 开发指南 | docs/developer-guide.md | 项目模块划分、扩展自定义提取器的方法与调试技巧 |
| 常见流程 | docs/workflows.md | 每日批量处理、定时监控清理、数据迁移等典型操作步骤 |

## 资源列表

- http://m.3g.bwbkj.cn/jnews/719753.htm
- http://m.3g.bwbkj.cn/jnews/2569001.htm
- http://m.3g.bwbkj.cn/jnews/222319.htm
- http://m.3g.bwbkj.cn/jnews/6044.htm
- http://m.3g.bwbkj.cn/jnews/6245.htm
- http://m.3g.bwbkj.cn/jnews/443239.htm
- http://m.3g.bwbkj.cn/jnews/7386445.htm
- http://m.3g.bwbkj.cn/jnews/8330856.htm
- http://m.3g.bwbkj.cn/jnews/1291.htm
- http://m.3g.bwbkj.cn/jnews/469485.htm
- http://m.3g.bwbkj.cn/jnews/4841393.htm
- http://m.3g.bwbkj.cn/jnews/397092.htm
- http://m.3g.bwbkj.cn/jnews/85708.htm
- http://m.3g.bwbkj.cn/jnews/4828066.htm
- http://m.3g.bwbkj.cn/jnews/5876971.htm
- http://m.3g.bwbkj.cn/jnews/1751.htm
- http://m.3g.bwbkj.cn/jnews/81198.htm
- http://m.3g.bwbkj.cn/jnews/9036834.htm
- http://m.3g.bwbkj.cn/jnews/4028.htm
- http://m.3g.bwbkj.cn/jnews/1992379.htm
- http://m.3g.bwbkj.cn/jnews/1343714.htm
- http://m.3g.bwbkj.cn/jnews/6889659.htm
- http://m.3g.bwbkj.cn/jnews/25112.htm
- http://m.3g.bwbkj.cn/jnews/8276450.htm
- http://m.3g.bwbkj.cn/jnews/9655.htm
- http://m.3g.bwbkj.cn/jnews/03252.htm
- http://m.3g.bwbkj.cn/jnews/65973.htm
- http://m.3g.bwbkj.cn/jnews/735183.htm
- http://m.3g.bwbkj.cn/jnews/224261.htm
- http://m.3g.bwbkj.cn/jnews/0858.htm
- http://m.3g.bwbkj.cn/jnews/937713.htm
- http://m.3g.bwbkj.cn/jnews/4773.htm
- http://m.3g.bwbkj.cn/jnews/3098968.htm
- http://m.3g.bwbkj.cn/jnews/1289267.htm
- http://m.3g.bwbkj.cn/jnews/251412.htm
- http://m.3g.bwbkj.cn/jnews/8503.htm
- http://m.3g.bwbkj.cn/jnews/18375.htm
- http://m.3g.bwbkj.cn/jnews/231169.htm
- http://m.3g.bwbkj.cn/jnews/7734646.htm
- http://m.3g.bwbkj.cn/jnews/550552.htm
- http://m.3g.bwbkj.cn/jnews/0486.htm
- http://m.3g.bwbkj.cn/jnews/0958818.htm
- http://m.3g.bwbkj.cn/jnews/9896.htm
- http://m.3g.bwbkj.cn/jnews/6613.htm
- http://m.3g.bwbkj.cn/jnews/7766086.htm
- http://m.3g.bwbkj.cn/jnews/89969.htm
- http://m.3g.bwbkj.cn/jnews/8602582.htm
- http://m.3g.bwbkj.cn/jnews/212954.htm
- http://m.3g.bwbkj.cn/jnews/2052291.htm
- http://m.3g.bwbkj.cn/jnews/57852.htm
- http://m.3g.bwbkj.cn/jnews/65393.htm
- http://m.3g.bwbkj.cn/jnews/96397.htm
- http://m.3g.bwbkj.cn/jnews/5787855.htm
- http://m.3g.bwbkj.cn/jnews/41791.htm
- http://m.3g.bwbkj.cn/jnews/01881.htm
- http://m.3g.bwbkj.cn/jnews/7908576.htm
- http://m.3g.bwbkj.cn/jnews/1636157.htm
- http://m.3g.bwbkj.cn/jnews/7064.htm
- http://m.3g.bwbkj.cn/jnews/55016.htm
- http://m.3g.bwbkj.cn/jnews/7174.htm
- http://m.3g.bwbkj.cn/jnews/6129705.htm
- http://m.3g.bwbkj.cn/jnews/93500.htm
- http://m.3g.bwbkj.cn/jnews/01805.htm
- http://m.3g.bwbkj.cn/jnews/8121529.htm
- http://m.3g.bwbkj.cn/jnews/8100.htm
- http://m.3g.bwbkj.cn/jnews/3982.htm
- http://m.3g.bwbkj.cn/jnews/5613.htm
- http://m.3g.bwbkj.cn/jnews/9391.htm
- http://m.3g.bwbkj.cn/jnews/85611.htm
- http://m.3g.bwbkj.cn/jnews/54553.htm
- http://m.3g.bwbkj.cn/jnews/56466.htm
- http://m.3g.bwbkj.cn/jnews/288824.htm
- http://m.3g.bwbkj.cn/jnews/968043.htm
- http://m.3g.bwbkj.cn/jnews/102268.htm
- http://m.3g.bwbkj.cn/jnews/247818.htm
- http://m.3g.bwbkj.cn/jnews/648539.htm
- http://m.3g.bwbkj.cn/jnews/9501700.htm
- http://m.3g.bwbkj.cn/jnews/74976.htm
- http://m.3g.bwbkj.cn/jnews/975516.htm
- http://m.3g.bwbkj.cn/jnews/420784.htm
- http://m.3g.bwbkj.cn/jnews/658527.htm
- http://m.3g.bwbkj.cn/jnews/6190.htm
- http://m.3g.bwbkj.cn/jnews/9462.htm
- http://m.3g.bwbkj.cn/jnews/62382.htm
- http://m.3g.bwbkj.cn/jnews/88624.htm
- http://m.3g.bwbkj.cn/jnews/83757.htm
- http://m.3g.bwbkj.cn/jnews/61318.htm
- http://m.3g.bwbkj.cn/jnews/4286.htm
- http://m.3g.bwbkj.cn/jnews/6737538.htm
- http://m.3g.bwbkj.cn/jnews/3962.htm
- http://m.3g.bwbkj.cn/jnews/938230.htm
- http://m.3g.bwbkj.cn/jnews/2097.htm
- http://m.3g.bwbkj.cn/jnews/64077.htm
- http://m.3g.bwbkj.cn/jnews/0185.htm
- http://m.3g.bwbkj.cn/jnews/567435.htm
- http://m.3g.bwbkj.cn/jnews/44391.htm
- http://m.3g.bwbkj.cn/jnews/748594.htm
- http://m.3g.bwbkj.cn/jnews/5924.htm
- http://m.3g.bwbkj.cn/jnews/47607.htm
- http://m.3g.bwbkj.cn/jnews/847285.htm
- http://m.3g.bwbkj.cn/jnews/30014.htm
- http://m.3g.bwbkj.cn/jnews/563265.htm
- http://m.3g.bwbkj.cn/jnews/4758901.htm
- http://m.3g.bwbkj.cn/jnews/3736758.htm
- http://m.3g.bwbkj.cn/jnews/0154994.htm
- http://m.3g.bwbkj.cn/jnews/7230.htm
- http://m.3g.bwbkj.cn/jnews/3310895.htm
- http://m.3g.bwbkj.cn/jnews/98612.htm
- http://m.3g.bwbkj.cn/jnews/6848127.htm
- http://m.3g.bwbkj.cn/jnews/8263395.htm
- http://m.3g.bwbkj.cn/jnews/199378.htm
- http://m.3g.bwbkj.cn/jnews/7289.htm
- http://m.3g.bwbkj.cn/jnews/57402.htm
- http://m.3g.bwbkj.cn/jnews/707474.htm
- http://m.3g.bwbkj.cn/jnews/5174.htm
- http://m.3g.bwbkj.cn/jnews/7960594.htm
- http://m.3g.bwbkj.cn/jnews/589118.htm
- http://m.3g.bwbkj.cn/jnews/1981.htm
- http://m.3g.bwbkj.cn/jnews/81003.htm
- http://m.3g.bwbkj.cn/jnews/8327102.htm
- http://m.3g.bwbkj.cn/jnews/07075.htm
- http://m.3g.bwbkj.cn/jnews/2651101.htm
- http://m.3g.bwbkj.cn/jnews/2258.htm
- http://m.3g.bwbkj.cn/jnews/096360.htm
- http://m.3g.bwbkj.cn/jnews/327565.htm
- http://m.3g.bwbkj.cn/jnews/7402017.htm
- http://m.3g.bwbkj.cn/jnews/9006169.htm
- http://m.3g.bwbkj.cn/jnews/0504.htm
- http://m.3g.bwbkj.cn/jnews/516677.htm
- http://m.3g.bwbkj.cn/jnews/6825891.htm
- http://m.3g.bwbkj.cn/jnews/905876.htm
- http://m.3g.bwbkj.cn/jnews/40399.htm
- http://m.3g.bwbkj.cn/jnews/06190.htm
- http://m.3g.bwbkj.cn/jnews/3533.htm
- http://m.3g.bwbkj.cn/jnews/58969.htm
- http://m.3g.bwbkj.cn/jnews/99539.htm
- http://m.3g.bwbkj.cn/jnews/05907.htm
- http://m.3g.bwbkj.cn/jnews/2742.htm
- http://m.3g.bwbkj.cn/jnews/99856.htm
- http://m.3g.bwbkj.cn/jnews/42114.htm
- http://m.3g.bwbkj.cn/jnews/348937.htm
- http://m.3g.bwbkj.cn/jnews/20649.htm
- http://m.3g.bwbkj.cn/jnews/5252.htm
- http://m.3g.bwbkj.cn/jnews/7726429.htm
- http://m.3g.bwbkj.cn/jnews/8654645.htm
- http://m.3g.bwbkj.cn/jnews/4694564.htm
- http://m.3g.bwbkj.cn/jnews/7677168.htm
- http://m.3g.bwbkj.cn/jnews/4859.htm
- http://m.3g.bwbkj.cn/jnews/136695.htm
- http://m.3g.bwbkj.cn/jnews/61534.htm
- http://m.3g.bwbkj.cn/jnews/91882.htm
- http://m.3g.bwbkj.cn/jnews/193576.htm
- http://m.3g.bwbkj.cn/jnews/1849301.htm
- http://m.3g.bwbkj.cn/jnews/0893.htm
- http://m.3g.bwbkj.cn/jnews/2340.htm
- http://m.3g.bwbkj.cn/jnews/153746.htm
- http://m.3g.bwbkj.cn/jnews/21762.htm
- http://m.3g.bwbkj.cn/jnews/364872.htm
- http://m.3g.bwbkj.cn/jnews/7152.htm
- http://m.3g.bwbkj.cn/jnews/231737.htm
- http://m.3g.bwbkj.cn/jnews/966796.htm
- http://m.3g.bwbkj.cn/jnews/33200.htm
- http://m.3g.bwbkj.cn/jnews/1027646.htm
- http://m.3g.bwbkj.cn/jnews/269217.htm
- http://m.3g.bwbkj.cn/jnews/1354177.htm
- http://m.3g.bwbkj.cn/jnews/2548082.htm
- http://m.3g.bwbkj.cn/jnews/592264.htm
- http://m.3g.bwbkj.cn/jnews/09672.htm
- http://m.3g.bwbkj.cn/jnews/662226.htm
- http://m.3g.bwbkj.cn/jnews/93258.htm
- http://m.3g.bwbkj.cn/jnews/1118543.htm
- http://m.3g.bwbkj.cn/jnews/1608577.htm
- http://m.3g.bwbkj.cn/jnews/15417.htm
- http://m.3g.bwbkj.cn/jnews/67067.htm
- http://m.3g.bwbkj.cn/jnews/78026.htm
- http://m.3g.bwbkj.cn/jnews/417912.htm
- http://m.3g.bwbkj.cn/jnews/789743.htm
- http://m.3g.bwbkj.cn/jnews/4556.htm
- http://m.3g.bwbkj.cn/jnews/045323.htm
- http://m.3g.bwbkj.cn/jnews/8207.htm
- http://m.3g.bwbkj.cn/jnews/232314.htm
- http://m.3g.bwbkj.cn/jnews/47711.htm
- http://m.3g.bwbkj.cn/jnews/863688.htm
- http://m.3g.bwbkj.cn/jnews/3360658.htm
- http://m.3g.bwbkj.cn/jnews/5770.htm
- http://m.3g.bwbkj.cn/jnews/0414627.htm
- http://m.3g.bwbkj.cn/jnews/91707.htm
- http://m.3g.bwbkj.cn/jnews/90796.htm
- http://m.3g.bwbkj.cn/jnews/7296.htm
- http://m.3g.bwbkj.cn/jnews/5895061.htm
- http://m.3g.bwbkj.cn/jnews/170534.htm
- http://m.3g.bwbkj.cn/jnews/2556136.htm
- http://m.3g.bwbkj.cn/jnews/820569.htm
- http://m.3g.bwbkj.cn/jnews/8746195.htm
- http://m.3g.bwbkj.cn/jnews/3091859.htm
- http://m.3g.bwbkj.cn/jnews/6674.htm
- http://m.3g.bwbkj.cn/jnews/373837.htm
- http://m.3g.bwbkj.cn/jnews/57078.htm
- http://m.3g.bwbkj.cn/jnews/0863.htm
- http://m.3g.bwbkj.cn/jnews/98785.htm
- http://m.3g.bwbkj.cn/jnews/2399.htm
- http://m.3g.bwbkj.cn/jnews/2954353.htm
- http://m.3g.bwbkj.cn/jnews/5664493.htm
- http://m.3g.bwbkj.cn/jnews/58881.htm
- http://m.3g.bwbkj.cn/jnews/875355.htm
- http://m.3g.bwbkj.cn/jnews/59798.htm
- http://m.3g.bwbkj.cn/jnews/6305.htm
- http://m.3g.bwbkj.cn/jnews/1299863.htm
- http://m.3g.bwbkj.cn/jnews/28109.htm
- http://m.3g.bwbkj.cn/jnews/5143.htm
- http://m.3g.bwbkj.cn/jnews/63292.htm
- http://m.3g.bwbkj.cn/jnews/769716.htm
- http://m.3g.bwbkj.cn/jnews/3134.htm
- http://m.3g.bwbkj.cn/jnews/2769277.htm
- http://m.3g.bwbkj.cn/jnews/4097.htm
- http://m.3g.bwbkj.cn/jnews/38797.htm
- http://m.3g.bwbkj.cn/jnews/641373.htm
- http://m.3g.bwbkj.cn/jnews/263252.htm
- http://m.3g.bwbkj.cn/jnews/9343.htm
- http://m.3g.bwbkj.cn/jnews/8704.htm
- http://m.3g.bwbkj.cn/jnews/937987.htm
- http://m.3g.bwbkj.cn/jnews/0548.htm
- http://m.3g.bwbkj.cn/jnews/5404.htm
- http://m.3g.bwbkj.cn/jnews/9101593.htm
- http://m.3g.bwbkj.cn/jnews/17586.htm
- http://m.3g.bwbkj.cn/jnews/9321740.htm
- http://m.3g.bwbkj.cn/jnews/1750124.htm
- http://m.3g.bwbkj.cn/jnews/6861943.htm
- http://m.3g.bwbkj.cn/jnews/986996.htm
- http://m.3g.bwbkj.cn/jnews/2446272.htm
- http://m.3g.bwbkj.cn/jnews/34076.htm
- http://m.3g.bwbkj.cn/jnews/301254.htm
- http://m.3g.bwbkj.cn/jnews/7999.htm
- http://m.3g.bwbkj.cn/jnews/40320.htm
- http://m.3g.bwbkj.cn/jnews/019389.htm
- http://m.3g.bwbkj.cn/jnews/620679.htm
- http://m.3g.bwbkj.cn/jnews/60551.htm
- http://m.3g.bwbkj.cn/jnews/4949159.htm
- http://m.3g.bwbkj.cn/jnews/47620.htm
- http://m.3g.bwbkj.cn/jnews/9072.htm
- http://m.3g.bwbkj.cn/jnews/43808.htm
- http://m.3g.bwbkj.cn/jnews/614884.htm
- http://m.3g.bwbkj.cn/jnews/2492.htm
- http://m.3g.bwbkj.cn/jnews/24580.htm
- http://m.3g.bwbkj.cn/jnews/8153643.htm
- http://m.3g.bwbkj.cn/jnews/12336.htm
- http://m.3g.bwbkj.cn/jnews/081197.htm
- http://m.3g.bwbkj.cn/jnews/0844142.htm
- http://m.3g.bwbkj.cn/jnews/30594.htm
- http://m.3g.bwbkj.cn/jnews/9210649.htm
- http://m.3g.bwbkj.cn/jnews/81715.htm
- http://m.3g.bwbkj.cn/jnews/8726.htm
- http://m.3g.bwbkj.cn/jnews/841117.htm
- http://m.3g.bwbkj.cn/jnews/86349.htm
- http://m.3g.bwbkj.cn/jnews/983886.htm
- http://m.3g.bwbkj.cn/jnews/28275.htm
- http://m.3g.bwbkj.cn/jnews/2643.htm
- http://m.3g.bwbkj.cn/jnews/8018545.htm
- http://m.3g.bwbkj.cn/jnews/6074464.htm
- http://m.3g.bwbkj.cn/jnews/504336.htm
- http://m.3g.bwbkj.cn/jnews/24758.htm
- http://m.3g.bwbkj.cn/jnews/199896.htm
- http://m.3g.bwbkj.cn/jnews/5761.htm
- http://m.3g.bwbkj.cn/jnews/865544.htm
- http://m.3g.bwbkj.cn/jnews/557800.htm
- http://m.3g.bwbkj.cn/jnews/949618.htm
- http://m.3g.bwbkj.cn/jnews/923652.htm
- http://m.3g.bwbkj.cn/jnews/1491344.htm
- http://m.3g.bwbkj.cn/jnews/6148578.htm
- http://m.3g.bwbkj.cn/jnews/42027.htm
- http://m.3g.bwbkj.cn/jnews/390097.htm
- http://m.3g.bwbkj.cn/jnews/54228.htm
- http://m.3g.bwbkj.cn/jnews/8719.htm
- http://m.3g.bwbkj.cn/jnews/7836.htm
- http://m.3g.bwbkj.cn/jnews/921500.htm
- http://m.3g.bwbkj.cn/jnews/192998.htm
- http://m.3g.bwbkj.cn/jnews/2687193.htm
- http://m.3g.bwbkj.cn/jnews/3455.htm
- http://m.3g.bwbkj.cn/jnews/8274.htm
- http://m.3g.bwbkj.cn/jnews/706156.htm
- http://m.3g.bwbkj.cn/jnews/010952.htm
- http://m.3g.bwbkj.cn/jnews/8449960.htm
- http://m.3g.bwbkj.cn/jnews/1031198.htm
- http://m.3g.bwbkj.cn/jnews/35319.htm
- http://m.3g.bwbkj.cn/jnews/51402.htm
- http://m.3g.bwbkj.cn/jnews/9239201.htm
- http://m.3g.bwbkj.cn/jnews/2036677.htm
- http://m.3g.bwbkj.cn/jnews/8304329.htm
- http://m.3g.bwbkj.cn/jnews/328599.htm
- http://m.3g.bwbkj.cn/jnews/3314228.htm
- http://m.3g.bwbkj.cn/jnews/7073.htm
- http://m.3g.bwbkj.cn/jnews/8756.htm
- http://m.3g.bwbkj.cn/jnews/385137.htm
- http://m.3g.bwbkj.cn/jnews/56337.htm
- http://m.3g.bwbkj.cn/jnews/3290074.htm
- http://m.3g.bwbkj.cn/jnews/2198729.htm
- http://m.3g.bwbkj.cn/jnews/5004.htm
- http://m.3g.bwbkj.cn/jnews/0661.htm
- http://m.3g.bwbkj.cn/jnews/9444.htm
- http://m.3g.bwbkj.cn/jnews/8003.htm

## 项目结构

```
newslink-aggregator/
├── main.py                      # 命令行入口，解析参数并调度各模块
├── config.yaml                  # 全局配置文件，含超时、重试、日志级别等
├── requirements.txt             # 生产环境依赖列表
├── requirements-dev.txt         # 开发与测试环境额外依赖
├── src/                         # 核心源码目录
│   ├── importer/                # 导入模块：支持多种格式解析
│   │   ├── __init__.py
│   │   ├── base.py              # 导入器抽象基类
│   │   ├── csv_importer.py      # CSV 格式解析
│   │   └── json_importer.py     # JSON 格式解析
│   ├── checker/                 # 状态检测模块
│   │   ├── __init__.py
│   │   ├── http_checker.py      # HTTP 请求与状态判断
│   │   └── retry_policy.py      # 重试与超时策略配置
│   ├── extractor/               # 元信息提取模块
│   │   ├── __init__.py
│   │   ├── html_parser.py       # BeautifulSoup 封装
│   │   └── metadata.py          # 标题、时间、关键词提取逻辑
│   ├── storage/                 # 存储模块
│   │   ├── __init__.py
│   │   ├── local_cache.py       # 本地 JSON 文件读写
│   │   └── deduplicator.py      # URL 去重与历史比对
│   ├── filter/                  # 检索与过滤模块
│   │   ├── __init__.py
│   │   ├── query_parser.py      # 组合查询条件解析
│   │   └── rule_engine.py       # 标签规则引擎
│   └── exporter/                # 导出模块
│       ├── __init__.py
│       ├── markdown.py          # 导出为 Markdown 列表
│       └── json_exporter.py     # 导出为 JSON 数组
├── tests/                       # 单元测试目录
│   ├── test_importer.py
│   ├── test_checker.py
│   └── test_extractor.py
├── docs/                        # 文档目录
│   ├── user-guide.md
│   ├── config-reference.md
│   ├── developer-guide.md
│   └── workflows.md
├── data/                        # 运行时数据目录
│   ├── imported.json            # 导入后的结构化链接库
│   └── logs/                    # 操作日志存储
│       └── operations.log
└── scripts/                     # 辅助脚本
    ├── batch_import.sh          # 批量导入 Shell 封装
    └── clean_old_records.py     # 定期清理过期历史记录
```

## 贡献指南

提交问题报告：在 GitHub Issues 中使用提供的模板描述问题，附上复现步骤、输入数据样本与预期输出，以及运行环境信息（Python 版本、操作系统）。

代码贡献流程：Fork 项目仓库，创建功能分支，编写代码并添加对应的单元测试，确保所有现有测试通过后提交 Pull Request，并关联相关 Issue 编号。

文档改进：对用户手册、配置参考或开发指南的修正或增补，可直接修改 docs 目录下的 Markdown 文件，提交 Pull Request 时注明文档变更范围。

新增提取器或规则：如需支持自定义元信息字段或标签规则，请参考 developer-guide.md 中关于插件接口的说明，提供示例配置与测试数据。

本地测试要求：所有提交前需在 Python 3.8 与 3.10 环境下分别运行 pytest，确保无回归错误，并更新 requirements-dev.txt 中可能新增的依赖。

## 常见问题

导入大量链接时进程卡住如何解决

检查 config.yaml 中的并发请求数与超时设置，调低并发数并适当延长超时时间。对于数千条以上的链接，建议使用 --batch-size 参数分批处理，每批 100 条并间隔 2 秒，避免目标服务器限流或本地资源耗尽。

元信息提取不准确或缺失怎么办

部分新闻页面使用动态 JavaScript 渲染内容，当前提取器仅处理静态 HTML。若目标站点依赖前端渲染，可考虑结合 Selenium 或 Playwright 扩展提取器。同时可在配置中关闭元信息提取，仅保留状态检测功能以提高稳定性。

如何升级到新版本而不丢失已导入数据

data/ 目录下的 imported.json 文件采用版本化格式，升级前备份该文件。新版本通常提供迁移脚本，位于 scripts/migrate.py，运行后可将旧格式数据转换为新结构。具体迁移步骤请查阅对应版本的 Release Notes。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:01
