# WebIndex 批次聚合导航

WebIndex 是一个面向技术信息检索与批量外链管理的开源导航聚合工具，专为需要定期整理、归档、查阅大量技术文章、新闻动态或博客更新的研发团队、技术运营人员及个人知识管理者设计。该项目不对内容做二次加工，仅提供结构化的索引视图与本地检索能力，帮助用户在数百乃至数千条分散链接中快速定位目标信息。

项目定位于“轻量级外链知识库的构建基础设施”，本身不依赖外部数据库或云服务，所有资源清单以纯文本形式维护，支持静态站点生成、命令行快速查询以及简单的元信息标记扩展。当前批次为第 175/300 批，共计收录 300 个来自固定源站的信息条目。

## 功能概览

批量外链导入与结构化存储 支持以纯文本或 Markdown 列表形式导入大量 URL，自动解析编号与扩展名，按批次分目录存放，保留原始域名与路径信息。

本地全文与正则检索 提供基于 ripgrep 或 grep 的轻量级检索脚本，可根据关键词、文件名模式或 URL 中的数字特征快速筛选目标链接。

元信息标注扩展 允许用户为每条链接添加自定义标签（如 `#backend`、`#tutorial`、`#release`）、阅读状态或优先级标记，标注信息保存在同目录的 `.meta` 文件中。

静态导航站点生成 内置一个简单的 Pandoc 或 Python 脚本，可将当前批次的资源列表渲染为带索引和分类的静态 HTML 页面，适合部署到内部服务器或 GitHub Pages。

批次管理与差异对比 支持按批次号（如 175/300）组织资源，提供脚本计算两个批次之间的新增、删除与重复链接，方便增量更新。

数据导出与订阅 支持将选中的链接列表导出为 JSON、CSV 或 OPML 格式，便于迁移至 RSS 阅读器、书签系统或其他知识管理工具。

零外部依赖运行 核心功能仅依赖标准 Unix 工具（bash、grep、sed、awk）或 Python 标准库，无需安装额外包即可在 Linux/macOS/WSL 环境下直接使用。

## 应用场景

技术团队内部周报汇总 团队技术负责人每周收集组员提交的参考链接（如性能分析报告、架构设计讨论、安全公告），通过 WebIndex 统一编号归档，并在周报中引用批次号，便于回溯讨论上下文。

个人技术阅读工作流 个人开发者每日浏览技术博客、Hacker News、GitHub Trending 后，将值得保存的链接批量粘贴到 WebIndex 的资源列表中，利用检索功能快速回顾上周阅读过的某篇关于并发模型的文章。

文档站外链治理 开源项目文档维护者使用 WebIndex 管理文档中引用的所有外部链接，定期运行差异对比脚本检查失效链接或来源变更，保持文档外部引用质量。

离线知识库镜像准备 在无网络或弱网络环境中工作的研发人员，将 WebIndex 中的链接列表配合 wget 镜像脚本，批量拉取指定 URL 的内容保存为本地离线文档集合。

## 快速开始

以下命令演示如何克隆项目、安装基础脚本并运行第一个批次索引。

```bash
git clone https://github.com/your-org/webindex.git
cd webindex
cp scripts/webindex.sh /usr/local/bin/webindex  # 或直接在当前目录使用 ./scripts/webindex.sh
webindex init --batch 175
webindex add --batch 175 --urls resources/batch_175.txt
webindex list --batch 175 --count
```

上述命令执行后，会在 `data/batches/175/` 目录下生成 `index.md` 和 `urls.txt` 两个文件，其中 `urls.txt` 包含本批次所有原始链接。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Bash | 4.0 或更高 | 所有核心控制脚本均使用 Bash 编写，需支持关联数组。 |
| GNU Coreutils | 8.0 或更高 | 提供 `cat`、`sort`、`uniq`、`wc` 等基础命令。 |
| GNU Grep | 3.0 或更高 | 用于正则检索，建议支持 `-P`（Perl 正则）以提升匹配精度。 |
| Sed | 4.0 或更高 | 用于流式编辑 URL 列表和元数据文件。 |
| Python | 3.6 或更高 | 可选，用于静态站点生成和 JSON/OPML 导出模块。 |
| Git | 2.20 或更高 | 用于克隆仓库和版本管理，非运行时强制依赖。 |
| Ripgrep (rg) | 12.0 或更高 | 推荐安装，大幅提升全文检索速度，尤其适用于千条以上数据。 |
| Pandoc | 2.0 或更高 | 可选，用于将 Markdown 索引转换为 HTML 静态页面。 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user-guide.md | 如何安装、初始化批次、添加链接、执行检索以及生成静态站点。 |
| 管理员指南 | docs/admin-guide.md | 如何管理多批次数据、执行批次差异对比、自定义元信息模板。 |
| 脚本参考 | docs/script-reference.md | 每个核心脚本（init/add/list/diff/export）的参数、环境变量与退出码说明。 |
| 扩展开发 | docs/development.md | 如何编写自定义过滤器、添加新的导出格式、修改静态站点主题。 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/4996742.htm
- http://m.blog.ghtkgg.cn/nnews/2352.htm
- http://m.blog.ghtkgg.cn/nnews/567228.htm
- http://m.blog.ghtkgg.cn/nnews/1677.htm
- http://m.blog.ghtkgg.cn/nnews/9466644.htm
- http://m.blog.ghtkgg.cn/nnews/53482.htm
- http://m.blog.ghtkgg.cn/nnews/25402.htm
- http://m.blog.ghtkgg.cn/nnews/4468425.htm
- http://m.blog.ghtkgg.cn/nnews/4974999.htm
- http://m.blog.ghtkgg.cn/nnews/190355.htm
- http://m.blog.ghtkgg.cn/nnews/69917.htm
- http://m.blog.ghtkgg.cn/nnews/89412.htm
- http://m.blog.ghtkgg.cn/nnews/798927.htm
- http://m.blog.ghtkgg.cn/nnews/3192469.htm
- http://m.blog.ghtkgg.cn/nnews/09980.htm
- http://m.blog.ghtkgg.cn/nnews/7249546.htm
- http://m.blog.ghtkgg.cn/nnews/08129.htm
- http://m.blog.ghtkgg.cn/nnews/5442168.htm
- http://m.blog.ghtkgg.cn/nnews/1938894.htm
- http://m.blog.ghtkgg.cn/nnews/1150.htm
- http://m.blog.ghtkgg.cn/nnews/054208.htm
- http://m.blog.ghtkgg.cn/nnews/16402.htm
- http://m.blog.ghtkgg.cn/nnews/23151.htm
- http://m.blog.ghtkgg.cn/nnews/77190.htm
- http://m.blog.ghtkgg.cn/nnews/8969.htm
- http://m.blog.ghtkgg.cn/nnews/92132.htm
- http://m.blog.ghtkgg.cn/nnews/2272817.htm
- http://m.blog.ghtkgg.cn/nnews/3314729.htm
- http://m.blog.ghtkgg.cn/nnews/71349.htm
- http://m.blog.ghtkgg.cn/nnews/7765.htm
- http://m.blog.ghtkgg.cn/nnews/940418.htm
- http://m.blog.ghtkgg.cn/nnews/1249581.htm
- http://m.blog.ghtkgg.cn/nnews/3845438.htm
- http://m.blog.ghtkgg.cn/nnews/561951.htm
- http://m.blog.ghtkgg.cn/nnews/1494.htm
- http://m.blog.ghtkgg.cn/nnews/386731.htm
- http://m.blog.ghtkgg.cn/nnews/0143.htm
- http://m.blog.ghtkgg.cn/nnews/9326.htm
- http://m.blog.ghtkgg.cn/nnews/2337.htm
- http://m.blog.ghtkgg.cn/nnews/0977.htm
- http://m.blog.ghtkgg.cn/nnews/2654288.htm
- http://m.blog.ghtkgg.cn/nnews/8847035.htm
- http://m.blog.ghtkgg.cn/nnews/684236.htm
- http://m.blog.ghtkgg.cn/nnews/94901.htm
- http://m.blog.ghtkgg.cn/nnews/95961.htm
- http://m.blog.ghtkgg.cn/nnews/8403.htm
- http://m.blog.ghtkgg.cn/nnews/8392.htm
- http://m.blog.ghtkgg.cn/nnews/2112477.htm
- http://m.blog.ghtkgg.cn/nnews/79484.htm
- http://m.blog.ghtkgg.cn/nnews/207321.htm
- http://m.blog.ghtkgg.cn/nnews/6603.htm
- http://m.blog.ghtkgg.cn/nnews/554712.htm
- http://m.blog.ghtkgg.cn/nnews/32270.htm
- http://m.blog.ghtkgg.cn/nnews/41210.htm
- http://m.blog.ghtkgg.cn/nnews/418420.htm
- http://m.blog.ghtkgg.cn/nnews/8631955.htm
- http://m.blog.ghtkgg.cn/nnews/56977.htm
- http://m.blog.ghtkgg.cn/nnews/6671325.htm
- http://m.blog.ghtkgg.cn/nnews/3773266.htm
- http://m.blog.ghtkgg.cn/nnews/108226.htm
- http://m.blog.ghtkgg.cn/nnews/202439.htm
- http://m.blog.ghtkgg.cn/nnews/419046.htm
- http://m.blog.ghtkgg.cn/nnews/7200020.htm
- http://m.blog.ghtkgg.cn/nnews/38300.htm
- http://m.blog.ghtkgg.cn/nnews/3182510.htm
- http://m.blog.ghtkgg.cn/nnews/180098.htm
- http://m.blog.ghtkgg.cn/nnews/24983.htm
- http://m.blog.ghtkgg.cn/nnews/16896.htm
- http://m.blog.ghtkgg.cn/nnews/0987554.htm
- http://m.blog.ghtkgg.cn/nnews/4172.htm
- http://m.blog.ghtkgg.cn/nnews/92374.htm
- http://m.blog.ghtkgg.cn/nnews/7388110.htm
- http://m.blog.ghtkgg.cn/nnews/3491887.htm
- http://m.blog.ghtkgg.cn/nnews/740453.htm
- http://m.blog.ghtkgg.cn/nnews/070883.htm
- http://m.blog.ghtkgg.cn/nnews/6128.htm
- http://m.blog.ghtkgg.cn/nnews/89532.htm
- http://m.blog.ghtkgg.cn/nnews/2263651.htm
- http://m.blog.ghtkgg.cn/nnews/596961.htm
- http://m.blog.ghtkgg.cn/nnews/3229125.htm
- http://m.blog.ghtkgg.cn/nnews/9513.htm
- http://m.blog.ghtkgg.cn/nnews/5716087.htm
- http://m.blog.ghtkgg.cn/nnews/91854.htm
- http://m.blog.ghtkgg.cn/nnews/3476862.htm
- http://m.blog.ghtkgg.cn/nnews/070813.htm
- http://m.blog.ghtkgg.cn/nnews/6559.htm
- http://m.blog.ghtkgg.cn/nnews/6401.htm
- http://m.blog.ghtkgg.cn/nnews/343277.htm
- http://m.blog.ghtkgg.cn/nnews/25142.htm
- http://m.blog.ghtkgg.cn/nnews/8497.htm
- http://m.blog.ghtkgg.cn/nnews/16993.htm
- http://m.blog.ghtkgg.cn/nnews/7611.htm
- http://m.blog.ghtkgg.cn/nnews/001806.htm
- http://m.blog.ghtkgg.cn/nnews/533101.htm
- http://m.blog.ghtkgg.cn/nnews/055263.htm
- http://m.blog.ghtkgg.cn/nnews/89806.htm
- http://m.blog.ghtkgg.cn/nnews/418114.htm
- http://m.blog.ghtkgg.cn/nnews/2729491.htm
- http://m.blog.ghtkgg.cn/nnews/0528.htm
- http://m.blog.ghtkgg.cn/nnews/87538.htm
- http://m.blog.ghtkgg.cn/nnews/459152.htm
- http://m.blog.ghtkgg.cn/nnews/9834.htm
- http://m.blog.ghtkgg.cn/nnews/3864721.htm
- http://m.blog.ghtkgg.cn/nnews/803964.htm
- http://m.blog.ghtkgg.cn/nnews/8054.htm
- http://m.blog.ghtkgg.cn/nnews/65988.htm
- http://m.blog.ghtkgg.cn/nnews/1780.htm
- http://m.blog.ghtkgg.cn/nnews/7819507.htm
- http://m.blog.ghtkgg.cn/nnews/3911.htm
- http://m.blog.ghtkgg.cn/nnews/0863949.htm
- http://m.blog.ghtkgg.cn/nnews/2976495.htm
- http://m.blog.ghtkgg.cn/nnews/783970.htm
- http://m.blog.ghtkgg.cn/nnews/78724.htm
- http://m.blog.ghtkgg.cn/nnews/6648.htm
- http://m.blog.ghtkgg.cn/nnews/5531472.htm
- http://m.blog.ghtkgg.cn/nnews/2358.htm
- http://m.blog.ghtkgg.cn/nnews/38125.htm
- http://m.blog.ghtkgg.cn/nnews/976352.htm
- http://m.blog.ghtkgg.cn/nnews/9227783.htm
- http://m.blog.ghtkgg.cn/nnews/713058.htm
- http://m.blog.ghtkgg.cn/nnews/58465.htm
- http://m.blog.ghtkgg.cn/nnews/2414237.htm
- http://m.blog.ghtkgg.cn/nnews/0892.htm
- http://m.blog.ghtkgg.cn/nnews/93625.htm
- http://m.blog.ghtkgg.cn/nnews/507824.htm
- http://m.blog.ghtkgg.cn/nnews/07187.htm
- http://m.blog.ghtkgg.cn/nnews/21403.htm
- http://m.blog.ghtkgg.cn/nnews/468322.htm
- http://m.blog.ghtkgg.cn/nnews/55862.htm
- http://m.blog.ghtkgg.cn/nnews/9960089.htm
- http://m.blog.ghtkgg.cn/nnews/3226693.htm
- http://m.blog.ghtkgg.cn/nnews/6557713.htm
- http://m.blog.ghtkgg.cn/nnews/4612.htm
- http://m.blog.ghtkgg.cn/nnews/619482.htm
- http://m.blog.ghtkgg.cn/nnews/440188.htm
- http://m.blog.ghtkgg.cn/nnews/3789.htm
- http://m.blog.ghtkgg.cn/nnews/457510.htm
- http://m.blog.ghtkgg.cn/nnews/9927889.htm
- http://m.blog.ghtkgg.cn/nnews/47154.htm
- http://m.blog.ghtkgg.cn/nnews/2983.htm
- http://m.blog.ghtkgg.cn/nnews/6734598.htm
- http://m.blog.ghtkgg.cn/nnews/289559.htm
- http://m.blog.ghtkgg.cn/nnews/00736.htm
- http://m.blog.ghtkgg.cn/nnews/63002.htm
- http://m.blog.ghtkgg.cn/nnews/38890.htm
- http://m.blog.ghtkgg.cn/nnews/209135.htm
- http://m.blog.ghtkgg.cn/nnews/630340.htm
- http://m.blog.ghtkgg.cn/nnews/00359.htm
- http://m.blog.ghtkgg.cn/nnews/9125045.htm
- http://m.blog.ghtkgg.cn/nnews/2239.htm
- http://m.blog.ghtkgg.cn/nnews/18870.htm
- http://m.blog.ghtkgg.cn/nnews/164378.htm
- http://m.blog.ghtkgg.cn/nnews/0124057.htm
- http://m.blog.ghtkgg.cn/nnews/2979.htm
- http://m.blog.ghtkgg.cn/nnews/0219563.htm
- http://m.blog.ghtkgg.cn/nnews/89957.htm
- http://m.blog.ghtkgg.cn/nnews/6006878.htm
- http://m.blog.ghtkgg.cn/nnews/23498.htm
- http://m.blog.ghtkgg.cn/nnews/5813.htm
- http://m.blog.ghtkgg.cn/nnews/1096547.htm
- http://m.blog.ghtkgg.cn/nnews/240955.htm
- http://m.blog.ghtkgg.cn/nnews/8521150.htm
- http://m.blog.ghtkgg.cn/nnews/73897.htm
- http://m.blog.ghtkgg.cn/nnews/522115.htm
- http://m.blog.ghtkgg.cn/nnews/87485.htm
- http://m.blog.ghtkgg.cn/nnews/0355.htm
- http://m.blog.ghtkgg.cn/nnews/8049.htm
- http://m.blog.ghtkgg.cn/nnews/99509.htm
- http://m.blog.ghtkgg.cn/nnews/9650400.htm
- http://m.blog.ghtkgg.cn/nnews/372371.htm
- http://m.blog.ghtkgg.cn/nnews/20132.htm
- http://m.blog.ghtkgg.cn/nnews/419231.htm
- http://m.blog.ghtkgg.cn/nnews/9452.htm
- http://m.blog.ghtkgg.cn/nnews/970478.htm
- http://m.blog.ghtkgg.cn/nnews/0395383.htm
- http://m.blog.ghtkgg.cn/nnews/37844.htm
- http://m.blog.ghtkgg.cn/nnews/4843110.htm
- http://m.blog.ghtkgg.cn/nnews/260031.htm
- http://m.blog.ghtkgg.cn/nnews/9240.htm
- http://m.blog.ghtkgg.cn/nnews/7903105.htm
- http://m.blog.ghtkgg.cn/nnews/8806387.htm
- http://m.blog.ghtkgg.cn/nnews/14741.htm
- http://m.blog.ghtkgg.cn/nnews/5117336.htm
- http://m.blog.ghtkgg.cn/nnews/7800.htm
- http://m.blog.ghtkgg.cn/nnews/1611.htm
- http://m.blog.ghtkgg.cn/nnews/2179816.htm
- http://m.blog.ghtkgg.cn/nnews/6123.htm
- http://m.blog.ghtkgg.cn/nnews/641873.htm
- http://m.blog.ghtkgg.cn/nnews/24503.htm
- http://m.blog.ghtkgg.cn/nnews/8562481.htm
- http://m.blog.ghtkgg.cn/nnews/878997.htm
- http://m.blog.ghtkgg.cn/nnews/137497.htm
- http://m.blog.ghtkgg.cn/nnews/299012.htm
- http://m.blog.ghtkgg.cn/nnews/312555.htm
- http://m.blog.ghtkgg.cn/nnews/81622.htm
- http://m.blog.ghtkgg.cn/nnews/77226.htm
- http://m.blog.ghtkgg.cn/nnews/94712.htm
- http://m.blog.ghtkgg.cn/nnews/934218.htm
- http://m.blog.ghtkgg.cn/nnews/8004731.htm
- http://m.blog.ghtkgg.cn/nnews/6584033.htm
- http://m.blog.ghtkgg.cn/nnews/68791.htm
- http://m.blog.ghtkgg.cn/nnews/13283.htm
- http://m.blog.ghtkgg.cn/nnews/338341.htm
- http://m.blog.ghtkgg.cn/nnews/0855365.htm
- http://m.blog.ghtkgg.cn/nnews/3992580.htm
- http://m.blog.ghtkgg.cn/nnews/3671.htm
- http://m.blog.ghtkgg.cn/nnews/48088.htm
- http://m.blog.ghtkgg.cn/nnews/3113412.htm
- http://m.blog.ghtkgg.cn/nnews/179770.htm
- http://m.blog.ghtkgg.cn/nnews/45346.htm
- http://m.blog.ghtkgg.cn/nnews/3451783.htm
- http://m.blog.ghtkgg.cn/nnews/0455494.htm
- http://m.blog.ghtkgg.cn/nnews/36834.htm
- http://m.blog.ghtkgg.cn/nnews/6640.htm
- http://m.blog.ghtkgg.cn/nnews/6274812.htm
- http://m.blog.ghtkgg.cn/nnews/3480129.htm
- http://m.blog.ghtkgg.cn/nnews/89596.htm
- http://m.blog.ghtkgg.cn/nnews/55020.htm
- http://m.blog.ghtkgg.cn/nnews/7153.htm
- http://m.blog.ghtkgg.cn/nnews/8583.htm
- http://m.blog.ghtkgg.cn/nnews/3485.htm
- http://m.blog.ghtkgg.cn/nnews/567690.htm
- http://m.blog.ghtkgg.cn/nnews/1395.htm
- http://m.blog.ghtkgg.cn/nnews/2372.htm
- http://m.blog.ghtkgg.cn/nnews/7258.htm
- http://m.blog.ghtkgg.cn/nnews/14331.htm
- http://m.blog.ghtkgg.cn/nnews/0520.htm
- http://m.blog.ghtkgg.cn/nnews/699293.htm
- http://m.blog.ghtkgg.cn/nnews/773945.htm
- http://m.blog.ghtkgg.cn/nnews/25042.htm
- http://m.blog.ghtkgg.cn/nnews/6487876.htm
- http://m.blog.ghtkgg.cn/nnews/789060.htm
- http://m.blog.ghtkgg.cn/nnews/07866.htm
- http://m.blog.ghtkgg.cn/nnews/6829045.htm
- http://m.blog.ghtkgg.cn/nnews/8604.htm
- http://m.blog.ghtkgg.cn/nnews/96552.htm
- http://m.blog.ghtkgg.cn/nnews/52786.htm
- http://m.blog.ghtkgg.cn/nnews/632096.htm
- http://m.blog.ghtkgg.cn/nnews/4533.htm
- http://m.blog.ghtkgg.cn/nnews/1727.htm
- http://m.blog.ghtkgg.cn/nnews/48105.htm
- http://m.blog.ghtkgg.cn/nnews/428216.htm
- http://m.blog.ghtkgg.cn/nnews/01322.htm
- http://m.blog.ghtkgg.cn/nnews/4504.htm
- http://m.blog.ghtkgg.cn/nnews/60096.htm
- http://m.blog.ghtkgg.cn/nnews/0012.htm
- http://m.blog.ghtkgg.cn/nnews/87772.htm
- http://m.blog.ghtkgg.cn/nnews/1006.htm
- http://m.blog.ghtkgg.cn/nnews/641039.htm
- http://m.blog.ghtkgg.cn/nnews/7535022.htm
- http://m.blog.ghtkgg.cn/nnews/5859058.htm
- http://m.blog.ghtkgg.cn/nnews/0134610.htm
- http://m.blog.ghtkgg.cn/nnews/8760.htm
- http://m.blog.ghtkgg.cn/nnews/47554.htm
- http://m.blog.ghtkgg.cn/nnews/5131695.htm
- http://m.blog.ghtkgg.cn/nnews/3430390.htm
- http://m.blog.ghtkgg.cn/nnews/58111.htm
- http://m.blog.ghtkgg.cn/nnews/1678714.htm
- http://m.blog.ghtkgg.cn/nnews/9817.htm
- http://m.blog.ghtkgg.cn/nnews/3288244.htm
- http://m.blog.ghtkgg.cn/nnews/959493.htm
- http://m.blog.ghtkgg.cn/nnews/834021.htm
- http://m.blog.ghtkgg.cn/nnews/6871.htm
- http://m.blog.ghtkgg.cn/nnews/432863.htm
- http://m.blog.ghtkgg.cn/nnews/3602995.htm
- http://m.blog.ghtkgg.cn/nnews/99858.htm
- http://m.blog.ghtkgg.cn/nnews/6162.htm
- http://m.blog.ghtkgg.cn/nnews/7612619.htm
- http://m.blog.ghtkgg.cn/nnews/50086.htm
- http://m.blog.ghtkgg.cn/nnews/1558976.htm
- http://m.blog.ghtkgg.cn/nnews/580026.htm
- http://m.blog.ghtkgg.cn/nnews/5081656.htm
- http://m.blog.ghtkgg.cn/nnews/65404.htm
- http://m.blog.ghtkgg.cn/nnews/440485.htm
- http://m.blog.ghtkgg.cn/nnews/2694637.htm
- http://m.blog.ghtkgg.cn/nnews/31386.htm
- http://m.blog.ghtkgg.cn/nnews/68678.htm
- http://m.blog.ghtkgg.cn/nnews/3359.htm
- http://m.blog.ghtkgg.cn/nnews/8318539.htm
- http://m.blog.ghtkgg.cn/nnews/7517.htm
- http://m.blog.ghtkgg.cn/nnews/10719.htm
- http://m.blog.ghtkgg.cn/nnews/3591417.htm
- http://m.blog.ghtkgg.cn/nnews/638885.htm
- http://m.blog.ghtkgg.cn/nnews/49256.htm
- http://m.blog.ghtkgg.cn/nnews/2564505.htm
- http://m.blog.ghtkgg.cn/nnews/3335342.htm
- http://m.blog.ghtkgg.cn/nnews/01873.htm
- http://m.blog.ghtkgg.cn/nnews/5182408.htm
- http://m.blog.ghtkgg.cn/nnews/07132.htm
- http://m.blog.ghtkgg.cn/nnews/32843.htm
- http://m.blog.ghtkgg.cn/nnews/591837.htm
- http://m.blog.ghtkgg.cn/nnews/6081213.htm
- http://m.blog.ghtkgg.cn/nnews/9368.htm
- http://m.blog.ghtkgg.cn/nnews/7930514.htm
- http://m.blog.ghtkgg.cn/nnews/525405.htm
- http://m.blog.ghtkgg.cn/nnews/051431.htm
- http://m.blog.ghtkgg.cn/nnews/01858.htm
- http://m.blog.ghtkgg.cn/nnews/0085610.htm
- http://m.blog.ghtkgg.cn/nnews/7524031.htm
- http://m.blog.ghtkgg.cn/nnews/11425.htm

## 项目结构

```
webindex/
├── bin/                              # 可执行脚本入口
│   ├── webindex                      # 主控制脚本，解析子命令并路由
│   ├── wi-init                       # 初始化批次目录与模板
│   ├── wi-add                        # 从文件或标准输入添加链接
│   ├── wi-list                       # 列表展示与计数
│   ├── wi-search                     # 基于 ripgrep 的全文检索封装
│   └── wi-export                     # 导出为 JSON / CSV / OPML
├── lib/                              # 公共函数库与核心逻辑
│   ├── core.sh                       # 路径解析、批次校验、错误处理
│   ├── io.sh                         # 读写 URL 列表与元数据文件
│   ├── filter.sh                     # 去重、正则过滤、黑白名单
│   └── render.sh                     # 将索引渲染为 Markdown/HTML
├── data/                             # 数据目录（按批次隔离）
│   └── batches/
│       ├── 175/                      # 当前批次（第 175/300 批）
│       │   ├── index.md              # 主索引文档，含元信息头部
│       │   ├── urls.txt              # 纯文本 URL 列表，每行一条
│       │   ├── .meta                 # 可选元信息标注（标签/状态）
│       │   └── .checksum             # 文件校验和，用于变更检测
│       └── 176/                      # 下一批次模板（预创建）
├── docs/                             # 用户与开发者文档
│   ├── user-guide.md                 # 安装、初始化、日常操作
│   ├── admin-guide.md                # 多批次管理、差异对比
│   ├── script-reference.md           # 各子命令参数与环境变量
│   └── development.md                # 扩展开发与主题定制
├── templates/                        # 静态站点生成模板
│   ├── default.css                   # 基础样式表
│   ├── page.tmpl                     # HTML 页面骨架
│   └── index.tmpl                    # 批次索引页布局
├── tests/                            # 单元测试与集成测试
│   ├── test_core.sh                  # 核心函数测试
│   ├── test_filter.sh                # 过滤与去重逻辑测试
│   └── fixtures/                     # 测试用固定数据集
├── Makefile                          # 构建与安装入口（make install）
└── README.md                         # 本文档
```

## 贡献指南

1. 提交问题报告或功能请求时，请使用 GitHub Issues 模板，明确标注批次号、操作步骤、预期结果与实际行为，并附上相关的 `urls.txt` 片段或错误日志。

2. 代码贡献请基于 `develop` 分支创建功能分支，命名格式为 `feature/{功能名}` 或 `fix/{问题编号}`，确保所有新脚本通过 `tests/` 下的单元测试后再提交 Pull Request。

3. 文档类贡献（包括修正错别字、补充示例、翻译）可直接修改 `docs/` 目录下的对应 Markdown 文件，并在提交信息中注明 `[docs]` 前缀。

4. 新增导出格式或静态站点主题时，请同时在 `docs/development.md` 中补充对应的扩展接口说明与配置示例，保持文档与代码同步更新。

5. 提交前请运行 `make lint` 检查脚本语法，运行 `make test` 执行完整测试套件，确保不引入回归缺陷。

## 常见问题

Q: 如何快速从 300 条链接中找出所有包含数字 `2026` 的条目？

A: 使用内置检索命令：`webindex search --batch 175 --pattern "2026"`。该命令默认对 `urls.txt` 和 `.meta` 文件执行大小写不敏感匹配，并输出匹配行的行号和原始内容。若需正则表达式匹配，可追加 `--regex` 选项。

Q: 不同批次之间的链接可能存在大量重复，如何清理？

A: 使用差异对比功能：`webindex diff --left 174 --right 175`。该命令输出三部分：仅存在于左批次的链接、仅存在于右批次的链接、以及共同链接。结合 `--dedup` 选项可自动生成去重后的合并列表，供人工审核后写入新批次。

Q: 静态站点生成后，页面中的链接排序与原始顺序不一致，如何保持原始顺序？

A: 生成脚本默认按字母序排序以便于查找。如需保持原始顺序，请在运行 `webindex render --batch 175 --html` 时添加 `--preserve-order` 参数，此时生成的 HTML 列表将严格遵循 `urls.txt` 中的行序。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
