# NewsLink Indexer

NewsLink Indexer 是一个面向移动端新闻资源聚合与结构化索引的开源工具集，专为需要从碎片化、半结构化新闻页面中提取元数据、建立检索关系与内容监控的技术团队设计。项目定位为轻量级新闻外链中间层，不提供爬虫框架，而是聚焦于 URL 规范化管理、链接有效性校验、来源分类与批量导入导出能力，适用于内容聚合站、舆情监控系统、新闻存档项目与研究机构的数据预处理环节。

项目当前维护第 114/300 批次资源，共计 300 个新闻链接条目，均来自 ghtkgg.cn 域下的移动端新闻发布路径。NewsLink Indexer 不存储新闻正文，仅作为链接清单的版本化管理工具，帮助开发者快速构建新闻源白名单、去重与分发流程。

## 功能概览

**链接批量校验** 支持对批次内全部 URL 进行 GET 头请求或状态码检测，输出可达性报告，标记 4xx、5xx 及超时记录。

**来源域名归一化** 自动提取 URL 中的主域名与路径层级，生成域名频次统计与顶级目录分布图，用于识别主要新闻源。

**批次版本管理** 以 300 条为单位组织链接批次，支持批次间差异对比，输出新增、删除与变更清单，便于增量更新。

**元数据模板注入** 允许用户为每条链接附加自定义标签、分类、抓取优先级与过期时间，生成 CSV/JSON 格式的增强索引。

**结构化导出** 内置 Markdown 表格、JSON 数组、纯文本列表三种导出格式，可直接嵌入文档或供给下游数据处理管道。

**去重指纹计算** 基于 URL 路径末尾数字序列与查询参数生成简化指纹，在批次内及跨批次间快速定位重复条目。

## 应用场景

舆情监控系统数据接入 运维团队可将本项目的链接清单作为监控系统的输入源，定时拉取列表并交由下游爬虫按优先级抓取，避免人工维护 URL 集合的繁琐工作。

新闻存档项目初始建库 数字存档工作者使用本项目的导出功能，将 300 条新闻链接转换为结构化 CSV，再结合自定义元数据字段完成分类与时间戳标记，快速建立原始数据索引表。

学术研究样本采集 社会科学或计算传播学研究人员利用本项目的校验与去重能力，快速清理冗余链接，获得较为干净的新闻 URL 样本集，用于后续内容分析与趋势研究。

内容聚合站白名单管理 小型内容聚合站点管理员将本批次链接作为内容来源白名单，通过项目的差异对比功能跟踪每日新增链接，保持聚合内容的新鲜度。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/your-org/newslink-indexer.git

# 进入项目目录
cd newslink-indexer

# 安装依赖（使用 pip 安装 Python 依赖）
pip install -r requirements.txt

# 运行批次导入与校验
python indexer.py --batch 114 --import-file links_batch_114.txt --validate

# 生成增强索引（CSV 格式）
python indexer.py --batch 114 --export csv --output batch_114_enhanced.csv

# 查看批次统计摘要
python indexer.py --batch 114 --stats
```

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.8 及以上 | 核心运行时环境，用于执行索引器脚本及依赖库调用 |
| requests | 2.28.0 及以上 | 发送 HTTP 请求进行链接可达性校验与状态码检测 |
| pandas | 1.5.0 及以上 | 用于链接数据的表格化处理、统计分析及 CSV 导出 |
| tqdm | 4.64.0 及以上 | 提供批次处理时的进度条显示，便于监控长时间校验任务 |
| PyYAML | 6.0 及以上 | 解析配置文件中的批次元数据与自定义标签映射规则 |
| openpyxl | 3.0.0 及以上 | 可选依赖，用于导出 Excel 格式的增强索引表格 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user_guide.md | 如何导入新批次、执行校验、导出不同格式以及自定义元数据字段 |
| 批次规范 | docs/batch_spec.md | 批次文件的结构要求、命名规则、字段定义与版本递增策略 |
| API 参考 | docs/api_reference.md | Indexer 核心类的方法签名、参数说明、返回值与异常类型 |
| 运维指南 | docs/ops_guide.md | 部署到服务器的环境配置、定时任务设置、日志轮转与性能调优建议 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/02425.htm
- http://m.3g.ghtkgg.cn/nnews/0264098.htm
- http://m.3g.ghtkgg.cn/nnews/086913.htm
- http://m.3g.ghtkgg.cn/nnews/8857.htm
- http://m.3g.ghtkgg.cn/nnews/2517.htm
- http://m.3g.ghtkgg.cn/nnews/266123.htm
- http://m.3g.ghtkgg.cn/nnews/54852.htm
- http://m.3g.ghtkgg.cn/nnews/4124238.htm
- http://m.3g.ghtkgg.cn/nnews/67128.htm
- http://m.3g.ghtkgg.cn/nnews/4593.htm
- http://m.3g.ghtkgg.cn/nnews/1261.htm
- http://m.3g.ghtkgg.cn/nnews/65157.htm
- http://m.3g.ghtkgg.cn/nnews/117925.htm
- http://m.3g.ghtkgg.cn/nnews/0917144.htm
- http://m.3g.ghtkgg.cn/nnews/857490.htm
- http://m.3g.ghtkgg.cn/nnews/4243048.htm
- http://m.3g.ghtkgg.cn/nnews/2697.htm
- http://m.3g.ghtkgg.cn/nnews/6673639.htm
- http://m.3g.ghtkgg.cn/nnews/9528.htm
- http://m.3g.ghtkgg.cn/nnews/894866.htm
- http://m.3g.ghtkgg.cn/nnews/3457377.htm
- http://m.3g.ghtkgg.cn/nnews/9870.htm
- http://m.3g.ghtkgg.cn/nnews/970777.htm
- http://m.3g.ghtkgg.cn/nnews/673556.htm
- http://m.3g.ghtkgg.cn/nnews/9468219.htm
- http://m.3g.ghtkgg.cn/nnews/2123.htm
- http://m.3g.ghtkgg.cn/nnews/4142.htm
- http://m.3g.ghtkgg.cn/nnews/055522.htm
- http://m.3g.ghtkgg.cn/nnews/7742946.htm
- http://m.3g.ghtkgg.cn/nnews/423372.htm
- http://m.3g.ghtkgg.cn/nnews/8242.htm
- http://m.3g.ghtkgg.cn/nnews/902425.htm
- http://m.3g.ghtkgg.cn/nnews/22747.htm
- http://m.3g.ghtkgg.cn/nnews/24816.htm
- http://m.3g.ghtkgg.cn/nnews/062942.htm
- http://m.3g.ghtkgg.cn/nnews/772305.htm
- http://m.3g.ghtkgg.cn/nnews/433001.htm
- http://m.3g.ghtkgg.cn/nnews/4642.htm
- http://m.3g.ghtkgg.cn/nnews/8583186.htm
- http://m.3g.ghtkgg.cn/nnews/22214.htm
- http://m.3g.ghtkgg.cn/nnews/3527778.htm
- http://m.3g.ghtkgg.cn/nnews/89838.htm
- http://m.3g.ghtkgg.cn/nnews/01181.htm
- http://m.3g.ghtkgg.cn/nnews/2359422.htm
- http://m.3g.ghtkgg.cn/nnews/156993.htm
- http://m.3g.ghtkgg.cn/nnews/6676589.htm
- http://m.3g.ghtkgg.cn/nnews/33030.htm
- http://m.3g.ghtkgg.cn/nnews/81787.htm
- http://m.3g.ghtkgg.cn/nnews/1971.htm
- http://m.3g.ghtkgg.cn/nnews/5577.htm
- http://m.3g.ghtkgg.cn/nnews/62265.htm
- http://m.3g.ghtkgg.cn/nnews/2259.htm
- http://m.3g.ghtkgg.cn/nnews/5840803.htm
- http://m.3g.ghtkgg.cn/nnews/33823.htm
- http://m.3g.ghtkgg.cn/nnews/3358932.htm
- http://m.3g.ghtkgg.cn/nnews/923208.htm
- http://m.3g.ghtkgg.cn/nnews/59794.htm
- http://m.3g.ghtkgg.cn/nnews/73187.htm
- http://m.3g.ghtkgg.cn/nnews/989885.htm
- http://m.3g.ghtkgg.cn/nnews/565867.htm
- http://m.3g.ghtkgg.cn/nnews/966083.htm
- http://m.3g.ghtkgg.cn/nnews/318533.htm
- http://m.3g.ghtkgg.cn/nnews/8984.htm
- http://m.3g.ghtkgg.cn/nnews/954152.htm
- http://m.3g.ghtkgg.cn/nnews/6361587.htm
- http://m.3g.ghtkgg.cn/nnews/7689.htm
- http://m.3g.ghtkgg.cn/nnews/537356.htm
- http://m.3g.ghtkgg.cn/nnews/2477850.htm
- http://m.3g.ghtkgg.cn/nnews/2066.htm
- http://m.3g.ghtkgg.cn/nnews/2244.htm
- http://m.3g.ghtkgg.cn/nnews/50879.htm
- http://m.3g.ghtkgg.cn/nnews/6787.htm
- http://m.3g.ghtkgg.cn/nnews/3542.htm
- http://m.3g.ghtkgg.cn/nnews/9872.htm
- http://m.3g.ghtkgg.cn/nnews/57703.htm
- http://m.3g.ghtkgg.cn/nnews/070686.htm
- http://m.3g.ghtkgg.cn/nnews/2562.htm
- http://m.3g.ghtkgg.cn/nnews/273793.htm
- http://m.3g.ghtkgg.cn/nnews/58064.htm
- http://m.3g.ghtkgg.cn/nnews/7682769.htm
- http://m.3g.ghtkgg.cn/nnews/1836.htm
- http://m.3g.ghtkgg.cn/nnews/76277.htm
- http://m.3g.ghtkgg.cn/nnews/821294.htm
- http://m.3g.ghtkgg.cn/nnews/758005.htm
- http://m.3g.ghtkgg.cn/nnews/3062.htm
- http://m.3g.ghtkgg.cn/nnews/1342.htm
- http://m.3g.ghtkgg.cn/nnews/709798.htm
- http://m.3g.ghtkgg.cn/nnews/005492.htm
- http://m.3g.ghtkgg.cn/nnews/7709981.htm
- http://m.3g.ghtkgg.cn/nnews/8390.htm
- http://m.3g.ghtkgg.cn/nnews/577406.htm
- http://m.3g.ghtkgg.cn/nnews/3111.htm
- http://m.3g.ghtkgg.cn/nnews/4648368.htm
- http://m.3g.ghtkgg.cn/nnews/2254.htm
- http://m.3g.ghtkgg.cn/nnews/035115.htm
- http://m.3g.ghtkgg.cn/nnews/07075.htm
- http://m.3g.ghtkgg.cn/nnews/5084721.htm
- http://m.3g.ghtkgg.cn/nnews/4912.htm
- http://m.3g.ghtkgg.cn/nnews/3822.htm
- http://m.3g.ghtkgg.cn/nnews/1163831.htm
- http://m.3g.ghtkgg.cn/nnews/529928.htm
- http://m.3g.ghtkgg.cn/nnews/0563.htm
- http://m.3g.ghtkgg.cn/nnews/68344.htm
- http://m.3g.ghtkgg.cn/nnews/3956.htm
- http://m.3g.ghtkgg.cn/nnews/482713.htm
- http://m.3g.ghtkgg.cn/nnews/07004.htm
- http://m.3g.ghtkgg.cn/nnews/0287731.htm
- http://m.3g.ghtkgg.cn/nnews/43826.htm
- http://m.3g.ghtkgg.cn/nnews/3167.htm
- http://m.3g.ghtkgg.cn/nnews/2417173.htm
- http://m.3g.ghtkgg.cn/nnews/74882.htm
- http://m.3g.ghtkgg.cn/nnews/983869.htm
- http://m.3g.ghtkgg.cn/nnews/2375.htm
- http://m.3g.ghtkgg.cn/nnews/4942068.htm
- http://m.3g.ghtkgg.cn/nnews/7227.htm
- http://m.3g.ghtkgg.cn/nnews/7316950.htm
- http://m.3g.ghtkgg.cn/nnews/025937.htm
- http://m.3g.ghtkgg.cn/nnews/0020196.htm
- http://m.3g.ghtkgg.cn/nnews/87539.htm
- http://m.3g.ghtkgg.cn/nnews/799843.htm
- http://m.3g.ghtkgg.cn/nnews/8019805.htm
- http://m.3g.ghtkgg.cn/nnews/2005030.htm
- http://m.3g.ghtkgg.cn/nnews/60453.htm
- http://m.3g.ghtkgg.cn/nnews/4121.htm
- http://m.3g.ghtkgg.cn/nnews/255177.htm
- http://m.3g.ghtkgg.cn/nnews/73284.htm
- http://m.3g.ghtkgg.cn/nnews/938218.htm
- http://m.3g.ghtkgg.cn/nnews/0556398.htm
- http://m.3g.ghtkgg.cn/nnews/4809964.htm
- http://m.3g.ghtkgg.cn/nnews/22589.htm
- http://m.3g.ghtkgg.cn/nnews/1409974.htm
- http://m.3g.ghtkgg.cn/nnews/34703.htm
- http://m.3g.ghtkgg.cn/nnews/4974978.htm
- http://m.3g.ghtkgg.cn/nnews/2723.htm
- http://m.3g.ghtkgg.cn/nnews/1160.htm
- http://m.3g.ghtkgg.cn/nnews/1944484.htm
- http://m.3g.ghtkgg.cn/nnews/4044825.htm
- http://m.3g.ghtkgg.cn/nnews/7722100.htm
- http://m.3g.ghtkgg.cn/nnews/9729.htm
- http://m.3g.ghtkgg.cn/nnews/4229703.htm
- http://m.3g.ghtkgg.cn/nnews/57611.htm
- http://m.3g.ghtkgg.cn/nnews/4209.htm
- http://m.3g.ghtkgg.cn/nnews/9974865.htm
- http://m.3g.ghtkgg.cn/nnews/84118.htm
- http://m.3g.ghtkgg.cn/nnews/2855.htm
- http://m.3g.ghtkgg.cn/nnews/5346584.htm
- http://m.3g.ghtkgg.cn/nnews/919120.htm
- http://m.3g.ghtkgg.cn/nnews/3424932.htm
- http://m.3g.ghtkgg.cn/nnews/8352.htm
- http://m.3g.ghtkgg.cn/nnews/281785.htm
- http://m.3g.ghtkgg.cn/nnews/600111.htm
- http://m.3g.ghtkgg.cn/nnews/306003.htm
- http://m.3g.ghtkgg.cn/nnews/4709.htm
- http://m.3g.ghtkgg.cn/nnews/3890.htm
- http://m.3g.ghtkgg.cn/nnews/7621.htm
- http://m.3g.ghtkgg.cn/nnews/3246.htm
- http://m.3g.ghtkgg.cn/nnews/5739.htm
- http://m.3g.ghtkgg.cn/nnews/8278.htm
- http://m.3g.ghtkgg.cn/nnews/88550.htm
- http://m.3g.ghtkgg.cn/nnews/355763.htm
- http://m.3g.ghtkgg.cn/nnews/5237428.htm
- http://m.3g.ghtkgg.cn/nnews/926617.htm
- http://m.3g.ghtkgg.cn/nnews/2524.htm
- http://m.3g.ghtkgg.cn/nnews/2021.htm
- http://m.3g.ghtkgg.cn/nnews/8521967.htm
- http://m.3g.ghtkgg.cn/nnews/4946918.htm
- http://m.3g.ghtkgg.cn/nnews/764983.htm
- http://m.3g.ghtkgg.cn/nnews/5837.htm
- http://m.3g.ghtkgg.cn/nnews/6411.htm
- http://m.3g.ghtkgg.cn/nnews/046894.htm
- http://m.3g.ghtkgg.cn/nnews/41785.htm
- http://m.3g.ghtkgg.cn/nnews/77752.htm
- http://m.3g.ghtkgg.cn/nnews/2111.htm
- http://m.3g.ghtkgg.cn/nnews/12782.htm
- http://m.3g.ghtkgg.cn/nnews/530086.htm
- http://m.3g.ghtkgg.cn/nnews/37995.htm
- http://m.3g.ghtkgg.cn/nnews/8990.htm
- http://m.3g.ghtkgg.cn/nnews/670143.htm
- http://m.3g.ghtkgg.cn/nnews/10952.htm
- http://m.3g.ghtkgg.cn/nnews/525547.htm
- http://m.3g.ghtkgg.cn/nnews/00491.htm
- http://m.3g.ghtkgg.cn/nnews/876072.htm
- http://m.3g.ghtkgg.cn/nnews/7527467.htm
- http://m.3g.ghtkgg.cn/nnews/275751.htm
- http://m.3g.ghtkgg.cn/nnews/215571.htm
- http://m.3g.ghtkgg.cn/nnews/8012256.htm
- http://m.3g.ghtkgg.cn/nnews/75793.htm
- http://m.3g.ghtkgg.cn/nnews/486430.htm
- http://m.3g.ghtkgg.cn/nnews/1606887.htm
- http://m.3g.ghtkgg.cn/nnews/794368.htm
- http://m.3g.ghtkgg.cn/nnews/96487.htm
- http://m.3g.ghtkgg.cn/nnews/757926.htm
- http://m.3g.ghtkgg.cn/nnews/493438.htm
- http://m.3g.ghtkgg.cn/nnews/06529.htm
- http://m.3g.ghtkgg.cn/nnews/22241.htm
- http://m.3g.ghtkgg.cn/nnews/7254.htm
- http://m.3g.ghtkgg.cn/nnews/9883445.htm
- http://m.3g.ghtkgg.cn/nnews/154377.htm
- http://m.3g.ghtkgg.cn/nnews/2064.htm
- http://m.3g.ghtkgg.cn/nnews/0593297.htm
- http://m.3g.ghtkgg.cn/nnews/14146.htm
- http://m.3g.ghtkgg.cn/nnews/5095175.htm
- http://m.3g.ghtkgg.cn/nnews/01741.htm
- http://m.3g.ghtkgg.cn/nnews/0345988.htm
- http://m.3g.ghtkgg.cn/nnews/948020.htm
- http://m.3g.ghtkgg.cn/nnews/0719788.htm
- http://m.3g.ghtkgg.cn/nnews/49986.htm
- http://m.3g.ghtkgg.cn/nnews/22011.htm
- http://m.3g.ghtkgg.cn/nnews/3927.htm
- http://m.3g.ghtkgg.cn/nnews/30530.htm
- http://m.3g.ghtkgg.cn/nnews/9146.htm
- http://m.3g.ghtkgg.cn/nnews/0028665.htm
- http://m.3g.ghtkgg.cn/nnews/4121124.htm
- http://m.3g.ghtkgg.cn/nnews/602159.htm
- http://m.3g.ghtkgg.cn/nnews/291451.htm
- http://m.3g.ghtkgg.cn/nnews/4540.htm
- http://m.3g.ghtkgg.cn/nnews/063999.htm
- http://m.3g.ghtkgg.cn/nnews/62151.htm
- http://m.3g.ghtkgg.cn/nnews/22069.htm
- http://m.3g.ghtkgg.cn/nnews/8347367.htm
- http://m.3g.ghtkgg.cn/nnews/1456.htm
- http://m.3g.ghtkgg.cn/nnews/1007.htm
- http://m.3g.ghtkgg.cn/nnews/4177685.htm
- http://m.3g.ghtkgg.cn/nnews/009657.htm
- http://m.3g.ghtkgg.cn/nnews/736506.htm
- http://m.3g.ghtkgg.cn/nnews/2984415.htm
- http://m.3g.ghtkgg.cn/nnews/2809186.htm
- http://m.3g.ghtkgg.cn/nnews/697156.htm
- http://m.3g.ghtkgg.cn/nnews/5893.htm
- http://m.3g.ghtkgg.cn/nnews/4463991.htm
- http://m.3g.ghtkgg.cn/nnews/8160.htm
- http://m.3g.ghtkgg.cn/nnews/08691.htm
- http://m.3g.ghtkgg.cn/nnews/0902.htm
- http://m.3g.ghtkgg.cn/nnews/75432.htm
- http://m.3g.ghtkgg.cn/nnews/352574.htm
- http://m.3g.ghtkgg.cn/nnews/25887.htm
- http://m.3g.ghtkgg.cn/nnews/27212.htm
- http://m.3g.ghtkgg.cn/nnews/0083.htm
- http://m.3g.ghtkgg.cn/nnews/0846996.htm
- http://m.3g.ghtkgg.cn/nnews/2842935.htm
- http://m.3g.ghtkgg.cn/nnews/0873.htm
- http://m.3g.ghtkgg.cn/nnews/4048.htm
- http://m.3g.ghtkgg.cn/nnews/76034.htm
- http://m.3g.ghtkgg.cn/nnews/23856.htm
- http://m.3g.ghtkgg.cn/nnews/0462.htm
- http://m.3g.ghtkgg.cn/nnews/0091.htm
- http://m.3g.ghtkgg.cn/nnews/72051.htm
- http://m.3g.ghtkgg.cn/nnews/7845081.htm
- http://m.3g.ghtkgg.cn/nnews/85790.htm
- http://m.3g.ghtkgg.cn/nnews/09754.htm
- http://m.3g.ghtkgg.cn/nnews/126920.htm
- http://m.3g.ghtkgg.cn/nnews/5103437.htm
- http://m.3g.ghtkgg.cn/nnews/1868018.htm
- http://m.3g.ghtkgg.cn/nnews/57265.htm
- http://m.3g.ghtkgg.cn/nnews/17220.htm
- http://m.3g.ghtkgg.cn/nnews/082891.htm
- http://m.3g.ghtkgg.cn/nnews/5700814.htm
- http://m.3g.ghtkgg.cn/nnews/2941.htm
- http://m.3g.ghtkgg.cn/nnews/254803.htm
- http://m.3g.ghtkgg.cn/nnews/6831479.htm
- http://m.3g.ghtkgg.cn/nnews/05032.htm
- http://m.3g.ghtkgg.cn/nnews/5060.htm
- http://m.3g.ghtkgg.cn/nnews/0481923.htm
- http://m.3g.ghtkgg.cn/nnews/8218.htm
- http://m.3g.ghtkgg.cn/nnews/13813.htm
- http://m.3g.ghtkgg.cn/nnews/27117.htm
- http://m.3g.ghtkgg.cn/nnews/156279.htm
- http://m.3g.ghtkgg.cn/nnews/99012.htm
- http://m.3g.ghtkgg.cn/nnews/5311207.htm
- http://m.3g.ghtkgg.cn/nnews/3891798.htm
- http://m.3g.ghtkgg.cn/nnews/4855.htm
- http://m.3g.ghtkgg.cn/nnews/6739000.htm
- http://m.3g.ghtkgg.cn/nnews/6884.htm
- http://m.3g.ghtkgg.cn/nnews/102668.htm
- http://m.3g.ghtkgg.cn/nnews/643302.htm
- http://m.3g.ghtkgg.cn/nnews/86186.htm
- http://m.3g.ghtkgg.cn/nnews/5839.htm
- http://m.3g.ghtkgg.cn/nnews/905209.htm
- http://m.3g.ghtkgg.cn/nnews/70915.htm
- http://m.3g.ghtkgg.cn/nnews/46271.htm
- http://m.3g.ghtkgg.cn/nnews/6154.htm
- http://m.3g.ghtkgg.cn/nnews/4607468.htm
- http://m.3g.ghtkgg.cn/nnews/5997.htm
- http://m.3g.ghtkgg.cn/nnews/7927.htm
- http://m.3g.ghtkgg.cn/nnews/1033.htm
- http://m.3g.ghtkgg.cn/nnews/83586.htm
- http://m.3g.ghtkgg.cn/nnews/731827.htm
- http://m.3g.ghtkgg.cn/nnews/1500153.htm
- http://m.3g.ghtkgg.cn/nnews/3294.htm
- http://m.3g.ghtkgg.cn/nnews/1709.htm
- http://m.3g.ghtkgg.cn/nnews/29323.htm
- http://m.3g.ghtkgg.cn/nnews/562986.htm
- http://m.3g.ghtkgg.cn/nnews/4234145.htm
- http://m.3g.ghtkgg.cn/nnews/23143.htm
- http://m.3g.ghtkgg.cn/nnews/29805.htm
- http://m.3g.ghtkgg.cn/nnews/2575.htm
- http://m.3g.ghtkgg.cn/nnews/398969.htm
- http://m.3g.ghtkgg.cn/nnews/4665425.htm
- http://m.3g.ghtkgg.cn/nnews/74575.htm
- http://m.3g.ghtkgg.cn/nnews/1280408.htm

## 项目结构

```
newslink-indexer/
├── indexer.py                 # 主入口脚本，解析命令行参数并调度各模块
├── config.yaml                # 全局配置文件，定义请求超时、重试策略与导出格式偏好
├── requirements.txt           # Python 依赖清单，锁定各库版本号
├── batch/                     # 批次数据目录，存放原始链接文件与导入记录
│   ├── 114/                   # 第 114 批次子目录，包含原始列表及校验结果
│   │   ├── raw_links.txt      # 原始 300 条链接纯文本文件
│   │   ├── validated.json     # 校验结果，含状态码与响应时间
│   │   └── metadata.yaml      # 批次元数据，如导入时间、条目数、来源备注
│   └── archive/               # 历史批次存档，按编号组织
├── core/                      # 核心逻辑模块
│   ├── validator.py           # 链接校验器，并发执行 HEAD 请求，返回状态报告
│   ├── deduper.py             # 去重指纹计算与重复条目定位
│   ├── exporter.py            # 导出驱动，支持 csv、json、md 三种格式
│   └── fingerprint.py         # 指纹生成算法，基于路径尾部数字与参数排序
├── docs/                      # 文档目录，存放用户手册与 API 参考
│   ├── user_guide.md          # 详细使用说明，含命令示例与配置解读
│   ├── batch_spec.md          # 批次文件格式规范与字段定义
│   ├── api_reference.md       # 核心类与方法 API 文档
│   └── ops_guide.md           # 部署与运维相关说明
├── tests/                     # 单元测试与集成测试用例
│   ├── test_validator.py      # 校验器模块测试，覆盖超时与错误处理
│   ├── test_deduper.py        # 去重算法测试，验证指纹碰撞检测
│   └── fixtures/              # 测试用的固定数据样本
└── output/                    # 导出文件默认存放位置，按时间戳命名子目录
    └── 2026-08-25_114.csv     # 示例导出文件，含增强元数据字段
```

## 贡献指南

提交问题报告 在 GitHub Issues 中描述您遇到的问题，附上批次编号、操作步骤、预期结果与实际输出日志。若涉及链接校验失败，请提供失败链接的完整 URL 列表。

改进校验策略 如果您发现现有校验模块对某些状态码处理不当，或希望增加对重定向、SSL 证书错误的更细粒度控制，请 Fork 仓库后在 validator.py 中实现改进并提交 Pull Request。

完善导出格式 若需新增导出格式如 XML、Parquet 或 SQLite，请在 exporter.py 中扩展导出函数，并在 tests 目录下补充对应的格式测试用例。提交前请确保通过全部现有测试。

补充文档示例 若使用过程中发现文档缺少命令组合示例或配置项解释不够清晰，欢迎在 docs 目录下更新相应文件。对于批次规范文档，鼓励附上真实的批次文件片段作为参考。

本地测试流程 提交代码前，请运行 pytest tests/ 确保所有测试通过，并在 Python 3.8 与 Python 3.11 两个环境中验证兼容性。若新增依赖，请同步更新 requirements.txt。

## 常见问题

问：校验过程中出现大量超时链接，如何处理？

答：超时通常由目标服务器响应缓慢或网络环境不稳定引起。建议在 config.yaml 中调整 timeout 参数，默认值为 10 秒，可酌情增至 20 或 30 秒。同时，indexer.py 支持 --retry 参数，可设置重试次数。若超时链接占比超过 30%，建议检查网络代理设置或切换至网络更稳定的执行环境。

问：导出的 CSV 文件中，元数据字段为空如何填充？

答：CSV 导出会保留每条链接的自定义标签、分类与优先级字段。若导入时未提供这些信息，对应字段将保持空值。用户可在导出前通过 indexer.py 的 --annotate 参数指定一个额外的键值对文件，为特定链接或全部链接批量注入元数据。文件格式为 JSON，键为链接完整 URL，值为元数据对象。

问：如何跨批次进行去重比较？

答：使用 indexer.py 的 --compare 参数，后跟两个批次编号，例如 --compare 113 114。系统将分别计算两个批次的指纹集合，输出交集（重复）、仅存在于前者与仅存在于后者的链接清单。该操作不修改原始批次文件，结果以 Markdown 表格形式输出至终端或指定文件。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:37:55
