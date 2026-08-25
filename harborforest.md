# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研、信息聚合与快速内容检索的轻量级网页资源索引系统。本系统定位于个人开发者、技术研究团队与内容运营人员，用于将分散的网页链接进行结构化存储、分类标注与快速访问，解决信息碎片化导致的知识回溯困难与资源复用率低下的问题。项目本身不依赖数据库，采用纯文本索引与静态页面生成策略，兼顾部署简便性与检索效率。

## 功能概览

- 链接结构化索引：支持对任意网页链接进行标题、摘要、关键词与分类标签的批量录入与自动索引生成。
- 多维度筛选与排序：可按收录时间、访问热度、分类目录或自定义标签对资源列表进行动态筛选与排序。
- 全文检索支持：基于倒排索引实现针对标题与摘要字段的快速关键词检索，响应时间控制在毫秒级。
- 静态页面导出：内置模板引擎可将索引数据渲染为纯静态 HTML 页面，便于托管至任何 Web 服务器或 CDN。
- 数据导入与导出：支持 CSV 与 JSON 格式的资源数据批量导入与导出，方便与其他系统进行数据交换。
- 资源状态监控：周期性检查已收录链接的可访问性，对失效链接进行标记并生成巡检报告。
- 访问统计与热点分析：记录资源被点击次数，自动生成热门资源排行榜与分类热度分布图表。

## 应用场景

技术文档与 API 参考资料整理：研发团队在日常开发中会积累大量外部技术文档、API 手册与博客教程链接，WebIndex 可为这些资源建立统一入口，避免重复查找与记忆负担。

行业资讯与竞品动态追踪：市场分析与产品调研人员需要持续关注行业新闻与竞品动态，通过 WebIndex 对资讯类链接进行打标与分类，可快速回溯特定时间段或特定主题的相关报道。

开源项目与工具链导航：开源社区维护者或企业内部技术委员会可利用 WebIndex 构建精选工具链导航页，为团队成员或社区用户提供经过筛选与评价的高质量工具清单。

学术文献与研究报告归档：科研人员与高校师生在文献调研过程中积累的大量论文链接、预印本与技术报告，可通过 WebIndex 按研究方向、发表年份或期刊会议进行组织，提升文献回顾效率。

## 快速开始

以下命令可在 Linux 与 macOS 环境下完成 WebIndex 的下载、依赖安装与服务启动。

```bash
# 克隆代码仓库
git clone https://github.com/webindex/webindex-core.git
cd webindex-core

# 安装 Python 依赖（建议使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化示例数据并启动开发服务器
python manage.py initdb --sample-data
python manage.py runserver --host 0.0.0.0 --port 8080
```

启动成功后，访问 http://localhost:8080 即可进入 WebIndex 索引管理界面。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.9 及以上 | 核心运行时环境，用于执行索引生成与 Web 服务 |
| pip | 22.0 及以上 | Python 包管理工具，用于安装项目依赖 |
| Git | 2.25 及以上 | 用于克隆代码仓库及版本管理 |
| 磁盘空间 | 500 MB 及以上 | 用于存放索引数据、日志及静态导出文件 |
| 内存 | 512 MB 及以上 | 开发环境最低内存要求，生产环境建议 2 GB 以上 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide/ | 如何录入链接、分类管理、检索与导出静态页面 |
| 部署指南 | /docs/deployment/ | 如何将 WebIndex 部署至生产服务器或容器环境 |
| API 参考 | /docs/api-reference/ | 索引数据的导入导出接口及第三方集成方法 |
| 运维手册 | /docs/operations/ | 链接状态监控配置、日志分析与性能调优策略 |

## 资源列表

- http://m.3g.oexnr.cn/nnews/145624.htm
- http://m.3g.oexnr.cn/nnews/8977871.htm
- http://m.3g.oexnr.cn/nnews/15397.htm
- http://m.3g.oexnr.cn/nnews/545434.htm
- http://m.3g.oexnr.cn/nnews/56158.htm
- http://m.3g.oexnr.cn/nnews/3551815.htm
- http://m.3g.oexnr.cn/nnews/40078.htm
- http://m.3g.oexnr.cn/nnews/24886.htm
- http://m.3g.oexnr.cn/nnews/6450235.htm
- http://m.3g.oexnr.cn/nnews/4012.htm
- http://m.3g.oexnr.cn/nnews/26861.htm
- http://m.3g.oexnr.cn/nnews/05761.htm
- http://m.3g.oexnr.cn/nnews/196002.htm
- http://m.3g.oexnr.cn/nnews/996769.htm
- http://m.3g.oexnr.cn/nnews/88446.htm
- http://m.3g.oexnr.cn/nnews/965070.htm
- http://m.3g.oexnr.cn/nnews/047165.htm
- http://m.3g.oexnr.cn/nnews/97036.htm
- http://m.3g.oexnr.cn/nnews/98422.htm
- http://m.3g.oexnr.cn/nnews/9720096.htm
- http://m.3g.oexnr.cn/nnews/7432349.htm
- http://m.3g.oexnr.cn/nnews/7610170.htm
- http://m.3g.oexnr.cn/nnews/39189.htm
- http://m.3g.oexnr.cn/nnews/3805.htm
- http://m.3g.oexnr.cn/nnews/2402.htm
- http://m.3g.oexnr.cn/nnews/33633.htm
- http://m.3g.oexnr.cn/nnews/059680.htm
- http://m.3g.oexnr.cn/nnews/14740.htm
- http://m.3g.oexnr.cn/nnews/552737.htm
- http://m.3g.oexnr.cn/nnews/56552.htm
- http://m.3g.oexnr.cn/nnews/3409.htm
- http://m.3g.oexnr.cn/nnews/176135.htm
- http://m.3g.oexnr.cn/nnews/9437970.htm
- http://m.3g.oexnr.cn/nnews/23608.htm
- http://m.3g.oexnr.cn/nnews/510126.htm
- http://m.3g.oexnr.cn/nnews/4754.htm
- http://m.3g.oexnr.cn/nnews/685200.htm
- http://m.3g.oexnr.cn/nnews/1944.htm
- http://m.3g.oexnr.cn/nnews/494088.htm
- http://m.3g.oexnr.cn/nnews/24737.htm
- http://m.3g.oexnr.cn/nnews/118273.htm
- http://m.3g.oexnr.cn/nnews/3705924.htm
- http://m.3g.oexnr.cn/nnews/2842276.htm
- http://m.3g.oexnr.cn/nnews/93275.htm
- http://m.3g.oexnr.cn/nnews/48561.htm
- http://m.3g.oexnr.cn/nnews/031604.htm
- http://m.3g.oexnr.cn/nnews/6639.htm
- http://m.3g.oexnr.cn/nnews/2048.htm
- http://m.3g.oexnr.cn/nnews/0526026.htm
- http://m.3g.oexnr.cn/nnews/1749447.htm
- http://m.3g.oexnr.cn/nnews/6032.htm
- http://m.3g.oexnr.cn/nnews/2682715.htm
- http://m.3g.oexnr.cn/nnews/6015.htm
- http://m.3g.oexnr.cn/nnews/27619.htm
- http://m.3g.oexnr.cn/nnews/00859.htm
- http://m.3g.oexnr.cn/nnews/093071.htm
- http://m.3g.oexnr.cn/nnews/2263.htm
- http://m.3g.oexnr.cn/nnews/808537.htm
- http://m.3g.oexnr.cn/nnews/1834.htm
- http://m.3g.oexnr.cn/nnews/44803.htm
- http://m.3g.oexnr.cn/nnews/220280.htm
- http://m.3g.oexnr.cn/nnews/8551.htm
- http://m.3g.oexnr.cn/nnews/7478.htm
- http://m.3g.oexnr.cn/nnews/9760.htm
- http://m.3g.oexnr.cn/nnews/833758.htm
- http://m.3g.oexnr.cn/nnews/681039.htm
- http://m.3g.oexnr.cn/nnews/108545.htm
- http://m.3g.oexnr.cn/nnews/37277.htm
- http://m.3g.oexnr.cn/nnews/284494.htm
- http://m.3g.oexnr.cn/nnews/491103.htm
- http://m.3g.oexnr.cn/nnews/3196.htm
- http://m.3g.oexnr.cn/nnews/16039.htm
- http://m.3g.oexnr.cn/nnews/89077.htm
- http://m.3g.oexnr.cn/nnews/0816152.htm
- http://m.3g.oexnr.cn/nnews/434268.htm
- http://m.3g.oexnr.cn/nnews/11725.htm
- http://m.3g.oexnr.cn/nnews/248731.htm
- http://m.3g.oexnr.cn/nnews/76108.htm
- http://m.3g.oexnr.cn/nnews/80058.htm
- http://m.3g.oexnr.cn/nnews/798598.htm
- http://m.3g.oexnr.cn/nnews/6394165.htm
- http://m.3g.oexnr.cn/nnews/9370484.htm
- http://m.3g.oexnr.cn/nnews/5606799.htm
- http://m.3g.oexnr.cn/nnews/487713.htm
- http://m.3g.oexnr.cn/nnews/2725.htm
- http://m.3g.oexnr.cn/nnews/8444131.htm
- http://m.3g.oexnr.cn/nnews/708662.htm
- http://m.3g.oexnr.cn/nnews/5596.htm
- http://m.3g.oexnr.cn/nnews/161225.htm
- http://m.3g.oexnr.cn/nnews/00560.htm
- http://m.3g.oexnr.cn/nnews/366508.htm
- http://m.3g.oexnr.cn/nnews/02621.htm
- http://m.3g.oexnr.cn/nnews/26490.htm
- http://m.3g.oexnr.cn/nnews/6682.htm
- http://m.3g.oexnr.cn/nnews/07246.htm
- http://m.3g.oexnr.cn/nnews/2945606.htm
- http://m.3g.oexnr.cn/nnews/177158.htm
- http://m.3g.oexnr.cn/nnews/749977.htm
- http://m.3g.oexnr.cn/nnews/3169.htm
- http://m.3g.oexnr.cn/nnews/69921.htm
- http://m.3g.oexnr.cn/nnews/772572.htm
- http://m.3g.oexnr.cn/nnews/3502551.htm
- http://m.3g.oexnr.cn/nnews/863239.htm
- http://m.3g.oexnr.cn/nnews/0928011.htm
- http://m.3g.oexnr.cn/nnews/9372.htm
- http://m.3g.oexnr.cn/nnews/02643.htm
- http://m.3g.oexnr.cn/nnews/478365.htm
- http://m.3g.oexnr.cn/nnews/816880.htm
- http://m.3g.oexnr.cn/nnews/3672505.htm
- http://m.3g.oexnr.cn/nnews/0584452.htm
- http://m.3g.oexnr.cn/nnews/8318963.htm
- http://m.3g.oexnr.cn/nnews/071569.htm
- http://m.3g.oexnr.cn/nnews/3778030.htm
- http://m.3g.oexnr.cn/nnews/864125.htm
- http://m.3g.oexnr.cn/nnews/27018.htm
- http://m.3g.oexnr.cn/nnews/784205.htm
- http://m.3g.oexnr.cn/nnews/4215.htm
- http://m.3g.oexnr.cn/nnews/81095.htm
- http://m.3g.oexnr.cn/nnews/3612.htm
- http://m.3g.oexnr.cn/nnews/6866538.htm
- http://m.3g.oexnr.cn/nnews/2300.htm
- http://m.3g.oexnr.cn/nnews/49274.htm
- http://m.3g.oexnr.cn/nnews/91802.htm
- http://m.3g.oexnr.cn/nnews/5581016.htm
- http://m.3g.oexnr.cn/nnews/68215.htm
- http://m.3g.oexnr.cn/nnews/0892101.htm
- http://m.3g.oexnr.cn/nnews/0063.htm
- http://m.3g.oexnr.cn/nnews/3509.htm
- http://m.3g.oexnr.cn/nnews/66395.htm
- http://m.3g.oexnr.cn/nnews/726110.htm
- http://m.3g.oexnr.cn/nnews/4484661.htm
- http://m.3g.oexnr.cn/nnews/0837.htm
- http://m.3g.oexnr.cn/nnews/93569.htm
- http://m.3g.oexnr.cn/nnews/8915.htm
- http://m.3g.oexnr.cn/nnews/0316743.htm
- http://m.3g.oexnr.cn/nnews/921001.htm
- http://m.3g.oexnr.cn/nnews/08456.htm
- http://m.3g.oexnr.cn/nnews/42817.htm
- http://m.3g.oexnr.cn/nnews/7156.htm
- http://m.3g.oexnr.cn/nnews/1650.htm
- http://m.3g.oexnr.cn/nnews/3756851.htm
- http://m.3g.oexnr.cn/nnews/8055536.htm
- http://m.3g.oexnr.cn/nnews/0735.htm
- http://m.3g.oexnr.cn/nnews/6933753.htm
- http://m.3g.oexnr.cn/nnews/848348.htm
- http://m.3g.oexnr.cn/nnews/97233.htm
- http://m.3g.oexnr.cn/nnews/06605.htm
- http://m.3g.oexnr.cn/nnews/90823.htm
- http://m.3g.oexnr.cn/nnews/0834.htm
- http://m.3g.oexnr.cn/nnews/700489.htm
- http://m.3g.oexnr.cn/nnews/46318.htm
- http://m.3g.oexnr.cn/nnews/19381.htm
- http://m.3g.oexnr.cn/nnews/064249.htm
- http://m.3g.oexnr.cn/nnews/35210.htm
- http://m.3g.oexnr.cn/nnews/9250.htm
- http://m.3g.oexnr.cn/nnews/7577858.htm
- http://m.3g.oexnr.cn/nnews/059601.htm
- http://m.3g.oexnr.cn/nnews/4774.htm
- http://m.3g.oexnr.cn/nnews/61961.htm
- http://m.3g.oexnr.cn/nnews/14275.htm
- http://m.3g.oexnr.cn/nnews/10425.htm
- http://m.3g.oexnr.cn/nnews/136253.htm
- http://m.3g.oexnr.cn/nnews/96635.htm
- http://m.3g.oexnr.cn/nnews/14862.htm
- http://m.3g.oexnr.cn/nnews/95921.htm
- http://m.3g.oexnr.cn/nnews/24743.htm
- http://m.3g.oexnr.cn/nnews/592930.htm
- http://m.3g.oexnr.cn/nnews/790210.htm
- http://m.3g.oexnr.cn/nnews/248471.htm
- http://m.3g.oexnr.cn/nnews/50151.htm
- http://m.3g.oexnr.cn/nnews/2257355.htm
- http://m.3g.oexnr.cn/nnews/69962.htm
- http://m.3g.oexnr.cn/nnews/74367.htm
- http://m.3g.oexnr.cn/nnews/859031.htm
- http://m.3g.oexnr.cn/nnews/8495.htm
- http://m.3g.oexnr.cn/nnews/874074.htm
- http://m.3g.oexnr.cn/nnews/4729352.htm
- http://m.3g.oexnr.cn/nnews/8324.htm
- http://m.3g.oexnr.cn/nnews/3192.htm
- http://m.3g.oexnr.cn/nnews/37091.htm
- http://m.3g.oexnr.cn/nnews/5226377.htm
- http://m.3g.oexnr.cn/nnews/4130913.htm
- http://m.3g.oexnr.cn/nnews/41574.htm
- http://m.3g.oexnr.cn/nnews/44819.htm
- http://m.3g.oexnr.cn/nnews/33026.htm
- http://m.3g.oexnr.cn/nnews/126776.htm
- http://m.3g.oexnr.cn/nnews/1696443.htm
- http://m.3g.oexnr.cn/nnews/57562.htm
- http://m.3g.oexnr.cn/nnews/25115.htm
- http://m.3g.oexnr.cn/nnews/5517.htm
- http://m.3g.oexnr.cn/nnews/916638.htm
- http://m.3g.oexnr.cn/nnews/2169413.htm
- http://m.3g.oexnr.cn/nnews/6249.htm
- http://m.3g.oexnr.cn/nnews/2852783.htm
- http://m.3g.oexnr.cn/nnews/488711.htm
- http://m.3g.oexnr.cn/nnews/1927467.htm
- http://m.3g.oexnr.cn/nnews/2291.htm
- http://m.3g.oexnr.cn/nnews/48044.htm
- http://m.3g.oexnr.cn/nnews/3043442.htm
- http://m.3g.oexnr.cn/nnews/1982.htm
- http://m.3g.oexnr.cn/nnews/90930.htm
- http://m.3g.oexnr.cn/nnews/2074.htm
- http://m.3g.oexnr.cn/nnews/85324.htm
- http://m.3g.oexnr.cn/nnews/05375.htm
- http://m.3g.oexnr.cn/nnews/32696.htm
- http://m.3g.oexnr.cn/nnews/1802.htm
- http://m.3g.oexnr.cn/nnews/018396.htm
- http://m.3g.oexnr.cn/nnews/86239.htm
- http://m.3g.oexnr.cn/nnews/716037.htm
- http://m.3g.oexnr.cn/nnews/1557.htm
- http://m.3g.oexnr.cn/nnews/2175.htm
- http://m.3g.oexnr.cn/nnews/306766.htm
- http://m.3g.oexnr.cn/nnews/17842.htm
- http://m.3g.oexnr.cn/nnews/8498.htm
- http://m.3g.oexnr.cn/nnews/74309.htm
- http://m.3g.oexnr.cn/nnews/5136220.htm
- http://m.3g.oexnr.cn/nnews/8131.htm
- http://m.3g.oexnr.cn/nnews/084426.htm
- http://m.3g.oexnr.cn/nnews/277905.htm
- http://m.3g.oexnr.cn/nnews/8358159.htm
- http://m.3g.oexnr.cn/nnews/91570.htm
- http://m.3g.oexnr.cn/nnews/34338.htm
- http://m.3g.oexnr.cn/nnews/778311.htm
- http://m.3g.oexnr.cn/nnews/7263977.htm
- http://m.3g.oexnr.cn/nnews/88427.htm
- http://m.3g.oexnr.cn/nnews/747298.htm
- http://m.3g.oexnr.cn/nnews/966369.htm
- http://m.3g.oexnr.cn/nnews/111476.htm
- http://m.3g.oexnr.cn/nnews/5958952.htm
- http://m.3g.oexnr.cn/nnews/9517569.htm
- http://m.3g.oexnr.cn/nnews/696534.htm
- http://m.3g.oexnr.cn/nnews/5091.htm
- http://m.3g.oexnr.cn/nnews/70046.htm
- http://m.3g.oexnr.cn/nnews/91625.htm
- http://m.3g.oexnr.cn/nnews/557666.htm
- http://m.3g.oexnr.cn/nnews/909303.htm
- http://m.3g.oexnr.cn/nnews/38560.htm
- http://m.3g.oexnr.cn/nnews/3705.htm
- http://m.3g.oexnr.cn/nnews/0386.htm
- http://m.3g.oexnr.cn/nnews/247825.htm
- http://m.3g.oexnr.cn/nnews/9901.htm
- http://m.3g.oexnr.cn/nnews/72209.htm
- http://m.3g.oexnr.cn/nnews/139306.htm
- http://m.3g.oexnr.cn/nnews/6975.htm
- http://m.3g.oexnr.cn/nnews/3357886.htm
- http://m.3g.oexnr.cn/nnews/7171.htm
- http://m.3g.oexnr.cn/nnews/8530095.htm
- http://m.3g.oexnr.cn/nnews/828555.htm
- http://m.3g.oexnr.cn/nnews/085037.htm
- http://m.3g.oexnr.cn/nnews/9511.htm
- http://m.3g.oexnr.cn/nnews/9616.htm
- http://m.3g.oexnr.cn/nnews/89287.htm
- http://m.3g.oexnr.cn/nnews/63695.htm
- http://m.3g.oexnr.cn/nnews/0941.htm
- http://m.3g.oexnr.cn/nnews/5660317.htm
- http://m.3g.oexnr.cn/nnews/141020.htm
- http://m.3g.oexnr.cn/nnews/446765.htm
- http://m.3g.oexnr.cn/nnews/1448.htm
- http://m.3g.oexnr.cn/nnews/64586.htm
- http://m.3g.oexnr.cn/nnews/6080.htm
- http://m.3g.oexnr.cn/nnews/237977.htm
- http://m.3g.oexnr.cn/nnews/579158.htm
- http://m.3g.oexnr.cn/nnews/00888.htm
- http://m.3g.oexnr.cn/nnews/998460.htm
- http://m.3g.oexnr.cn/nnews/87698.htm
- http://m.3g.oexnr.cn/nnews/363529.htm
- http://m.3g.oexnr.cn/nnews/7090.htm
- http://m.3g.oexnr.cn/nnews/8321894.htm
- http://m.3g.oexnr.cn/nnews/7738.htm
- http://m.3g.oexnr.cn/nnews/5513.htm
- http://m.3g.oexnr.cn/nnews/676221.htm
- http://m.3g.oexnr.cn/nnews/93770.htm
- http://m.3g.oexnr.cn/nnews/2550.htm
- http://m.3g.oexnr.cn/nnews/4954.htm
- http://m.3g.oexnr.cn/nnews/935837.htm
- http://m.3g.oexnr.cn/nnews/9140183.htm
- http://m.3g.oexnr.cn/nnews/56612.htm
- http://m.3g.oexnr.cn/nnews/3081907.htm
- http://m.3g.oexnr.cn/nnews/7162620.htm
- http://m.3g.oexnr.cn/nnews/836215.htm
- http://m.3g.oexnr.cn/nnews/5294031.htm
- http://m.3g.oexnr.cn/nnews/390314.htm
- http://m.3g.oexnr.cn/nnews/18983.htm
- http://m.3g.oexnr.cn/nnews/4024585.htm
- http://m.3g.oexnr.cn/nnews/55252.htm
- http://m.3g.oexnr.cn/nnews/35163.htm
- http://m.3g.oexnr.cn/nnews/33364.htm
- http://m.3g.oexnr.cn/nnews/928742.htm
- http://m.3g.oexnr.cn/nnews/2869.htm
- http://m.3g.oexnr.cn/nnews/31149.htm
- http://m.3g.oexnr.cn/nnews/60541.htm
- http://m.3g.oexnr.cn/nnews/96434.htm
- http://m.3g.oexnr.cn/nnews/61029.htm
- http://m.3g.oexnr.cn/nnews/777170.htm
- http://m.3g.oexnr.cn/nnews/36431.htm
- http://m.3g.oexnr.cn/nnews/289403.htm
- http://m.3g.oexnr.cn/nnews/307975.htm
- http://m.3g.oexnr.cn/nnews/44722.htm
- http://m.3g.oexnr.cn/nnews/075107.htm
- http://m.3g.oexnr.cn/nnews/037119.htm

## 项目结构

```
webindex-core/
├── manage.py                 # 项目统一管理入口，集成开发服务器、数据库初始化与静态导出命令
├── requirements.txt          # Python 依赖清单，包含 Flask、Whoosh、Requests 等核心库
├── config/
│   ├── settings.py           # 主配置文件，包含服务端口、索引路径、缓存策略等参数
│   └── logging.conf          # 日志格式与输出级别配置
├── app/
│   ├── __init__.py           # Flask 应用工厂函数，完成蓝图注册与扩展初始化
│   ├── indexer/              # 索引核心模块，负责链接的增删改查与倒排索引维护
│   │   ├── schema.py         # 索引字段定义，包含标题、摘要、链接、分类与时间戳
│   │   └── writer.py         # 索引写入与合并逻辑，支持批量提交与事务回滚
│   ├── crawler/              # 链接状态巡检模块，周期性检测资源可访问性
│   │   ├── checker.py        # 基于 Requests 的 HTTP 状态码检测与超时处理
│   │   └── reporter.py       # 生成巡检报告，标记失效链接与响应时间异常
│   ├── web/                  # Web 界面模块，提供检索、筛选与数据管理页面
│   │   ├── routes.py         # 路由定义，包含主页、检索页、详情页与管理后台
│   │   └── forms.py          # 表单验证类，用于链接录入与编辑操作
│   ├── static/               # 静态资源文件，包含 CSS 样式与前端 JavaScript 脚本
│   └── templates/            # Jinja2 模板文件，用于渲染各类页面视图
├── data/
│   ├── index/                # Whoosh 倒排索引存储目录，包含段文件与元数据
│   ├── snapshots/            # 索引数据快照目录，用于版本回滚与备份恢复
│   └── exports/              # 静态页面导出目录，可完整托管至 Web 服务器
├── tests/                    # 单元测试与集成测试目录，覆盖索引操作与 API 接口
│   ├── test_indexer.py       # 索引增删改查功能的测试用例
│   └── test_crawler.py       # 链接状态检测功能的测试用例
└── docs/                     # 项目文档源码，采用 Markdown 格式编写
    ├── user-guide.md         # 用户手册，涵盖日常操作流程与界面说明
    ├── deployment.md         # 部署指南，包含 Nginx 配置、Systemd 服务与容器化方案
    └── api-reference.md      # API 参考文档，描述导入导出接口与数据格式规范
```

## 贡献指南

1. 在 GitHub 上 Fork 本仓库至个人账户，并在本地克隆 Fork 后的副本，建议使用 `--recurse-submodules` 选项确保子模块同步拉取。

2. 创建新的功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式，避免在主干分支直接进行修改。

3. 完成代码或文档变更后，请确保通过项目内全部单元测试，并在 `tests/` 目录下补充与变更内容相关的测试用例，保持测试覆盖率不低于 85%。

4. 提交变更时使用语义化提交信息格式，例如 `feat: 增加按分类筛选接口` 或 `docs: 更新部署指南中的环境变量说明`，便于自动生成变更日志。

5. 发起 Pull Request 至本仓库的 `main` 分支，并在 PR 描述中清晰说明变更目的、影响范围与测试验证情况，项目维护者将在 3 个工作日内完成审阅。

## 常见问题

问：索引数据是否支持迁移至其他服务器？

答：支持。项目的数据目录 `data/index/` 包含完整的倒排索引文件，将该目录整体拷贝至目标服务器的相同相对路径下，并确保配置文件中的索引路径指向正确位置即可。建议在迁移前使用 `python manage.py snapshot create` 创建数据快照，迁移后使用 `python manage.py snapshot restore` 进行恢复验证。

问：如何处理失效链接的批量清理？

答：系统内置的链接状态巡检模块会每日自动检测资源可访问性，并将失效链接标记为 `unreachable` 状态。管理员可通过管理后台的「失效链接」视图进行批量删除或重新验证操作。若需手动触发检测，可执行 `python manage.py check-links --timeout 5 --retry 2` 命令，其中 `--timeout` 参数设置单次请求超时秒数，`--retry` 参数设置失败重试次数。

问：静态页面导出是否支持自定义模板样式？

答：支持。项目使用 Jinja2 模板引擎，所有导出模板位于 `app/templates/export/` 目录下。用户可修改 `base.html` 定义全局布局，或调整 `list.html` 与 `detail.html` 控制列表页与详情页的呈现结构。修改后需运行 `python manage.py export --rebuild` 重新生成全部静态页面，增量更新可使用 `python manage.py export --incremental` 仅导出新增或变更的资源。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
