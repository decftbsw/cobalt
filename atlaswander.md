# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研与信息聚合场景的轻量级外链导航系统，定位于为开发者、数据分析师与技术研究人员提供结构化的外部信息入口索引。该系统不对页面内容进行二次加工或存储，仅通过人工筛选与分类整理，将分散在互联网各处的技术文档、行业报告、案例分析与工具资源以目录树形式统一呈现，帮助用户快速定位高价值信息源，减少无效检索时间。

本项目适用于需要定期追踪特定领域动态、维护个人知识库或搭建团队信息看板的场景。WebIndex 不依赖外部数据库，所有索引数据以纯文本格式存储于仓库中，支持版本控制与协作编辑，便于用户按自身需求定制分类逻辑与展示层级。

## 功能概览

- **多级目录索引**：支持无限层级的分类目录结构，用户可根据主题、行业、日期或任意自定义维度组织链接资源。

- **原始链接直出**：所有外链以原始 URL 形式完整保留，不经过任何中间页跳转或参数追加，确保访问路径的透明性与可追溯性。

- **批量导入与校验**：提供批量添加链接的接口与格式校验工具，支持对 URL 协议头、域名格式、路径合法性进行自动化检查。

- **分类视图切换**：内置按时间排序、按热度排序与按字母排序三种视图模式，满足不同场景下的查阅习惯。

- **全文检索过滤**：基于目录名称与链接描述字段的轻量级关键词检索，支持模糊匹配与精确匹配两种模式。

- **状态标记系统**：可对每条链接添加"待阅""已读""重点关注""失效"等自定义状态标签，辅助个人阅读进度管理。

- **导出与分享**：支持将当前目录树或筛选结果导出为 Markdown 列表、JSON 结构化数据或纯文本清单，便于嵌入其他文档或分享给协作者。

- **变更历史追踪**：配合 Git 版本管理，每次增删改操作均保留提交记录，支持回溯任意历史版本。

## 应用场景

- **技术团队知识库建设**：研发团队可使用 WebIndex 整理内部常用的 API 文档地址、组件库主页、运维监控面板链接与故障排查手册，替代浏览器书签的分散管理方式，实现团队共享与同步更新。

- **行业信息周报素材采集**：市场分析师或产品经理可建立按赛道分类的竞品动态目录，每周批量打开索引链接进行信息扫描，结合状态标记系统快速产出周报素材。

- **开源项目依赖导航**：开源维护者可在项目仓库中嵌入 WebIndex 生成的依赖资源清单，明确列出上游项目主页、协议文本、社区论坛与构建状态看板，降低新贡献者的上手门槛。

- **学术文献检索辅助**：研究人员可按研究方向建立预印本服务器、数据集发布页、工具包文档与实验室主页的索引目录，配合全文检索功能快速定位特定主题的历史资料。

- **个人阅读清单管理**：个人用户可将待读的技术博客、教程系列与视频课程统一收录，通过状态标记追踪学习进度，避免信息淹没在社交媒体的时间线中。

## 快速开始

以下命令适用于 Linux 与 macOS 环境，Windows 用户可使用 WSL 或 Git Bash 执行。

```bash
# 克隆仓库到本地
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装依赖（基于 Node.js 环境，版本要求见安装要求章节）
npm install

# 启动本地开发服务器，默认监听端口 3000
npm run serve
```

启动成功后，在浏览器中访问 `http://localhost:3000` 即可查看索引主页。首次启动将自动生成示例目录结构与演示数据，用户可直接在 `./data` 目录下编辑 Markdown 或 JSON 文件以修改索引内容。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 18.x 或 20.x LTS | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 9.x 或 10.x | 包管理器，随 Node.js 一并安装 |
| Git | 2.30 及以上 | 版本控制工具，用于克隆仓库与提交变更 |
| 操作系统 | Linux / macOS / Windows（WSL2） | 开发环境建议使用 Unix-like 系统，生产部署需额外配置反向代理 |
| 磁盘空间 | 200 MB 以上 | 不含索引内容本身，实际占用取决于链接数量与描述文本长度 |
| 内存 | 512 MB 以上 | 开发服务器运行时内存占用，生产构建时建议 1 GB 以上 |
| 浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 前端界面运行环境，需支持 ES2020 语法 |
| 网络 | 外网访问能力 | 用于打开索引中的外部链接，本地运行无需外网 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门 | `docs/quick-start.md` | 如何安装、配置首次运行环境与生成初始索引结构？ |
| 使用 | `docs/user-guide.md` | 如何添加新链接、编辑分类、切换视图与使用状态标记？ |
| 开发 | `docs/developer-guide.md` | 如何参与二次开发、自定义前端主题或扩展后端解析器？ |
| 运维 | `docs/operations.md` | 如何部署到生产环境、配置 HTTPS 反向代理与自动化备份索引数据？ |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/94060.htm
- http://m.wap.ghtkgg.cn/jnews/4479501.htm
- http://m.wap.ghtkgg.cn/jnews/7138.htm
- http://m.wap.ghtkgg.cn/jnews/2760006.htm
- http://m.wap.ghtkgg.cn/jnews/6196.htm
- http://m.wap.ghtkgg.cn/jnews/125691.htm
- http://m.wap.ghtkgg.cn/jnews/1166947.htm
- http://m.wap.ghtkgg.cn/jnews/0985.htm
- http://m.wap.ghtkgg.cn/jnews/4697586.htm
- http://m.wap.ghtkgg.cn/jnews/888554.htm
- http://m.wap.ghtkgg.cn/jnews/5147700.htm
- http://m.wap.ghtkgg.cn/jnews/60706.htm
- http://m.wap.ghtkgg.cn/jnews/1521972.htm
- http://m.wap.ghtkgg.cn/jnews/32429.htm
- http://m.wap.ghtkgg.cn/jnews/3247635.htm
- http://m.wap.ghtkgg.cn/jnews/7467517.htm
- http://m.wap.ghtkgg.cn/jnews/5623467.htm
- http://m.wap.ghtkgg.cn/jnews/7042034.htm
- http://m.wap.ghtkgg.cn/jnews/20525.htm
- http://m.wap.ghtkgg.cn/jnews/127522.htm
- http://m.wap.ghtkgg.cn/jnews/4250.htm
- http://m.wap.ghtkgg.cn/jnews/9347305.htm
- http://m.wap.ghtkgg.cn/jnews/358397.htm
- http://m.wap.ghtkgg.cn/jnews/0539.htm
- http://m.wap.ghtkgg.cn/jnews/5544118.htm
- http://m.wap.ghtkgg.cn/jnews/9273.htm
- http://m.wap.ghtkgg.cn/jnews/22889.htm
- http://m.wap.ghtkgg.cn/jnews/65766.htm
- http://m.wap.ghtkgg.cn/jnews/49889.htm
- http://m.wap.ghtkgg.cn/jnews/8747285.htm
- http://m.wap.ghtkgg.cn/jnews/09369.htm
- http://m.wap.ghtkgg.cn/jnews/600357.htm
- http://m.wap.ghtkgg.cn/jnews/619728.htm
- http://m.wap.ghtkgg.cn/jnews/575854.htm
- http://m.wap.ghtkgg.cn/jnews/91097.htm
- http://m.wap.ghtkgg.cn/jnews/1821355.htm
- http://m.wap.ghtkgg.cn/jnews/8413.htm
- http://m.wap.ghtkgg.cn/jnews/3004994.htm
- http://m.wap.ghtkgg.cn/jnews/397868.htm
- http://m.wap.ghtkgg.cn/jnews/6456180.htm
- http://m.wap.ghtkgg.cn/jnews/05660.htm
- http://m.wap.ghtkgg.cn/jnews/1646.htm
- http://m.wap.ghtkgg.cn/jnews/04045.htm
- http://m.wap.ghtkgg.cn/jnews/98583.htm
- http://m.wap.ghtkgg.cn/jnews/611956.htm
- http://m.wap.ghtkgg.cn/jnews/107347.htm
- http://m.wap.ghtkgg.cn/jnews/05826.htm
- http://m.wap.ghtkgg.cn/jnews/051575.htm
- http://m.wap.ghtkgg.cn/jnews/966832.htm
- http://m.wap.ghtkgg.cn/jnews/8470479.htm
- http://m.wap.ghtkgg.cn/jnews/63340.htm
- http://m.wap.ghtkgg.cn/jnews/8683.htm
- http://m.wap.ghtkgg.cn/jnews/8710154.htm
- http://m.wap.ghtkgg.cn/jnews/90625.htm
- http://m.wap.ghtkgg.cn/jnews/7468409.htm
- http://m.wap.ghtkgg.cn/jnews/9719.htm
- http://m.wap.ghtkgg.cn/jnews/012069.htm
- http://m.wap.ghtkgg.cn/jnews/2635542.htm
- http://m.wap.ghtkgg.cn/jnews/777067.htm
- http://m.wap.ghtkgg.cn/jnews/18835.htm
- http://m.wap.ghtkgg.cn/jnews/27206.htm
- http://m.wap.ghtkgg.cn/jnews/31119.htm
- http://m.wap.ghtkgg.cn/jnews/3729813.htm
- http://m.wap.ghtkgg.cn/jnews/313411.htm
- http://m.wap.ghtkgg.cn/jnews/05542.htm
- http://m.wap.ghtkgg.cn/jnews/5062.htm
- http://m.wap.ghtkgg.cn/jnews/9200213.htm
- http://m.wap.ghtkgg.cn/jnews/014416.htm
- http://m.wap.ghtkgg.cn/jnews/77891.htm
- http://m.wap.ghtkgg.cn/jnews/412096.htm
- http://m.wap.ghtkgg.cn/jnews/44500.htm
- http://m.wap.ghtkgg.cn/jnews/1839784.htm
- http://m.wap.ghtkgg.cn/jnews/61588.htm
- http://m.wap.ghtkgg.cn/jnews/6866852.htm
- http://m.wap.ghtkgg.cn/jnews/774746.htm
- http://m.wap.ghtkgg.cn/jnews/9861779.htm
- http://m.wap.ghtkgg.cn/jnews/89454.htm
- http://m.wap.ghtkgg.cn/jnews/49300.htm
- http://m.wap.ghtkgg.cn/jnews/95632.htm
- http://m.wap.ghtkgg.cn/jnews/4375.htm
- http://m.wap.ghtkgg.cn/jnews/4617818.htm
- http://m.wap.ghtkgg.cn/jnews/1338389.htm
- http://m.wap.ghtkgg.cn/jnews/056547.htm
- http://m.wap.ghtkgg.cn/jnews/1821995.htm
- http://m.wap.ghtkgg.cn/jnews/594895.htm
- http://m.wap.ghtkgg.cn/jnews/89038.htm
- http://m.wap.ghtkgg.cn/jnews/5611014.htm
- http://m.wap.ghtkgg.cn/jnews/1862.htm
- http://m.wap.ghtkgg.cn/jnews/06490.htm
- http://m.wap.ghtkgg.cn/jnews/103488.htm
- http://m.wap.ghtkgg.cn/jnews/0594062.htm
- http://m.wap.ghtkgg.cn/jnews/06610.htm
- http://m.wap.ghtkgg.cn/jnews/47685.htm
- http://m.wap.ghtkgg.cn/jnews/049131.htm
- http://m.wap.ghtkgg.cn/jnews/98222.htm
- http://m.wap.ghtkgg.cn/jnews/882965.htm
- http://m.wap.ghtkgg.cn/jnews/0456739.htm
- http://m.wap.ghtkgg.cn/jnews/69146.htm
- http://m.wap.ghtkgg.cn/jnews/9030.htm
- http://m.wap.ghtkgg.cn/jnews/5018.htm
- http://m.wap.ghtkgg.cn/jnews/27792.htm
- http://m.wap.ghtkgg.cn/jnews/1914.htm
- http://m.wap.ghtkgg.cn/jnews/0219.htm
- http://m.wap.ghtkgg.cn/jnews/214053.htm
- http://m.wap.ghtkgg.cn/jnews/4547.htm
- http://m.wap.ghtkgg.cn/jnews/85519.htm
- http://m.wap.ghtkgg.cn/jnews/4456994.htm
- http://m.wap.ghtkgg.cn/jnews/428966.htm
- http://m.wap.ghtkgg.cn/jnews/5468290.htm
- http://m.wap.ghtkgg.cn/jnews/74351.htm
- http://m.wap.ghtkgg.cn/jnews/5306882.htm
- http://m.wap.ghtkgg.cn/jnews/846860.htm
- http://m.wap.ghtkgg.cn/jnews/47317.htm
- http://m.wap.ghtkgg.cn/jnews/91370.htm
- http://m.wap.ghtkgg.cn/jnews/955731.htm
- http://m.wap.ghtkgg.cn/jnews/921605.htm
- http://m.wap.ghtkgg.cn/jnews/3973477.htm
- http://m.wap.ghtkgg.cn/jnews/5310.htm
- http://m.wap.ghtkgg.cn/jnews/8192262.htm
- http://m.wap.ghtkgg.cn/jnews/732561.htm
- http://m.wap.ghtkgg.cn/jnews/94006.htm
- http://m.wap.ghtkgg.cn/jnews/0807029.htm
- http://m.wap.ghtkgg.cn/jnews/906965.htm
- http://m.wap.ghtkgg.cn/jnews/6761632.htm
- http://m.wap.ghtkgg.cn/jnews/390585.htm
- http://m.wap.ghtkgg.cn/jnews/18588.htm
- http://m.wap.ghtkgg.cn/jnews/281615.htm
- http://m.wap.ghtkgg.cn/jnews/1896.htm
- http://m.wap.ghtkgg.cn/jnews/37027.htm
- http://m.wap.ghtkgg.cn/jnews/3529699.htm
- http://m.wap.ghtkgg.cn/jnews/1576.htm
- http://m.wap.ghtkgg.cn/jnews/916817.htm
- http://m.wap.ghtkgg.cn/jnews/16985.htm
- http://m.wap.ghtkgg.cn/jnews/4480319.htm
- http://m.wap.ghtkgg.cn/jnews/1608025.htm
- http://m.wap.ghtkgg.cn/jnews/1063662.htm
- http://m.wap.ghtkgg.cn/jnews/023024.htm
- http://m.wap.ghtkgg.cn/jnews/7656.htm
- http://m.wap.ghtkgg.cn/jnews/3244.htm
- http://m.wap.ghtkgg.cn/jnews/2181206.htm
- http://m.wap.ghtkgg.cn/jnews/03801.htm
- http://m.wap.ghtkgg.cn/jnews/14941.htm
- http://m.wap.ghtkgg.cn/jnews/08217.htm
- http://m.wap.ghtkgg.cn/jnews/5825.htm
- http://m.wap.ghtkgg.cn/jnews/0699069.htm
- http://m.wap.ghtkgg.cn/jnews/2161298.htm
- http://m.wap.ghtkgg.cn/jnews/790540.htm
- http://m.wap.ghtkgg.cn/jnews/59800.htm
- http://m.wap.ghtkgg.cn/jnews/5399782.htm
- http://m.wap.ghtkgg.cn/jnews/108302.htm
- http://m.wap.ghtkgg.cn/jnews/0820870.htm
- http://m.wap.ghtkgg.cn/jnews/7628673.htm
- http://m.wap.ghtkgg.cn/jnews/235873.htm
- http://m.wap.ghtkgg.cn/jnews/533928.htm
- http://m.wap.ghtkgg.cn/jnews/929670.htm
- http://m.wap.ghtkgg.cn/jnews/7785299.htm
- http://m.wap.ghtkgg.cn/jnews/68119.htm
- http://m.wap.ghtkgg.cn/jnews/859679.htm
- http://m.wap.ghtkgg.cn/jnews/02659.htm
- http://m.wap.ghtkgg.cn/jnews/541092.htm
- http://m.wap.ghtkgg.cn/jnews/0646829.htm
- http://m.wap.ghtkgg.cn/jnews/239076.htm
- http://m.wap.ghtkgg.cn/jnews/17414.htm
- http://m.wap.ghtkgg.cn/jnews/5938.htm
- http://m.wap.ghtkgg.cn/jnews/066298.htm
- http://m.wap.ghtkgg.cn/jnews/9061.htm
- http://m.wap.ghtkgg.cn/jnews/62988.htm
- http://m.wap.ghtkgg.cn/jnews/1326568.htm
- http://m.wap.ghtkgg.cn/jnews/421857.htm
- http://m.wap.ghtkgg.cn/jnews/695564.htm
- http://m.wap.ghtkgg.cn/jnews/36154.htm
- http://m.wap.ghtkgg.cn/jnews/601602.htm
- http://m.wap.ghtkgg.cn/jnews/13475.htm
- http://m.wap.ghtkgg.cn/jnews/5991197.htm
- http://m.wap.ghtkgg.cn/jnews/6967.htm
- http://m.wap.ghtkgg.cn/jnews/71016.htm
- http://m.wap.ghtkgg.cn/jnews/8269.htm
- http://m.wap.ghtkgg.cn/jnews/7227.htm
- http://m.wap.ghtkgg.cn/jnews/180789.htm
- http://m.wap.ghtkgg.cn/jnews/62760.htm
- http://m.wap.ghtkgg.cn/jnews/740189.htm
- http://m.wap.ghtkgg.cn/jnews/64101.htm
- http://m.wap.ghtkgg.cn/jnews/7801544.htm
- http://m.wap.ghtkgg.cn/jnews/263987.htm
- http://m.wap.ghtkgg.cn/jnews/0841395.htm
- http://m.wap.ghtkgg.cn/jnews/972520.htm
- http://m.wap.ghtkgg.cn/jnews/4303270.htm
- http://m.wap.ghtkgg.cn/jnews/5457.htm
- http://m.wap.ghtkgg.cn/jnews/084428.htm
- http://m.wap.ghtkgg.cn/jnews/4574106.htm
- http://m.wap.ghtkgg.cn/jnews/1720.htm
- http://m.wap.ghtkgg.cn/jnews/39536.htm
- http://m.wap.ghtkgg.cn/jnews/9465010.htm
- http://m.wap.ghtkgg.cn/jnews/2751.htm
- http://m.wap.ghtkgg.cn/jnews/1689.htm
- http://m.wap.ghtkgg.cn/jnews/8908491.htm
- http://m.wap.ghtkgg.cn/jnews/0410466.htm
- http://m.wap.ghtkgg.cn/jnews/488954.htm
- http://m.wap.ghtkgg.cn/jnews/486552.htm
- http://m.wap.ghtkgg.cn/jnews/1630686.htm
- http://m.wap.ghtkgg.cn/jnews/0351765.htm
- http://m.wap.ghtkgg.cn/jnews/6798040.htm
- http://m.wap.ghtkgg.cn/jnews/361949.htm
- http://m.wap.ghtkgg.cn/jnews/05779.htm
- http://m.wap.ghtkgg.cn/jnews/4306.htm
- http://m.wap.ghtkgg.cn/jnews/0207091.htm
- http://m.wap.ghtkgg.cn/jnews/7842.htm
- http://m.wap.ghtkgg.cn/jnews/830837.htm
- http://m.wap.ghtkgg.cn/jnews/14603.htm
- http://m.wap.ghtkgg.cn/jnews/5643.htm
- http://m.wap.ghtkgg.cn/jnews/2169176.htm
- http://m.wap.ghtkgg.cn/jnews/75109.htm
- http://m.wap.ghtkgg.cn/jnews/98037.htm
- http://m.wap.ghtkgg.cn/jnews/0137.htm
- http://m.wap.ghtkgg.cn/jnews/388896.htm
- http://m.wap.ghtkgg.cn/jnews/557902.htm
- http://m.wap.ghtkgg.cn/jnews/3478.htm
- http://m.wap.ghtkgg.cn/jnews/7523910.htm
- http://m.wap.ghtkgg.cn/jnews/5192.htm
- http://m.wap.ghtkgg.cn/jnews/86581.htm
- http://m.wap.ghtkgg.cn/jnews/5470.htm
- http://m.wap.ghtkgg.cn/jnews/593940.htm
- http://m.wap.ghtkgg.cn/jnews/9673.htm
- http://m.wap.ghtkgg.cn/jnews/8327930.htm
- http://m.wap.ghtkgg.cn/jnews/5763.htm
- http://m.wap.ghtkgg.cn/jnews/39294.htm
- http://m.wap.ghtkgg.cn/jnews/1723186.htm
- http://m.wap.ghtkgg.cn/jnews/4893.htm
- http://m.wap.ghtkgg.cn/jnews/641778.htm
- http://m.wap.ghtkgg.cn/jnews/490708.htm
- http://m.wap.ghtkgg.cn/jnews/1909.htm
- http://m.wap.ghtkgg.cn/jnews/43051.htm
- http://m.wap.ghtkgg.cn/jnews/0612.htm
- http://m.wap.ghtkgg.cn/jnews/01839.htm
- http://m.wap.ghtkgg.cn/jnews/8938.htm
- http://m.wap.ghtkgg.cn/jnews/1811374.htm
- http://m.wap.ghtkgg.cn/jnews/3524.htm
- http://m.wap.ghtkgg.cn/jnews/6420.htm
- http://m.wap.ghtkgg.cn/jnews/3154.htm
- http://m.wap.ghtkgg.cn/jnews/45981.htm
- http://m.wap.ghtkgg.cn/jnews/63946.htm
- http://m.wap.ghtkgg.cn/jnews/13796.htm
- http://m.wap.ghtkgg.cn/jnews/398280.htm
- http://m.wap.ghtkgg.cn/jnews/26514.htm
- http://m.wap.ghtkgg.cn/jnews/435200.htm
- http://m.wap.ghtkgg.cn/jnews/75374.htm
- http://m.wap.ghtkgg.cn/jnews/27597.htm
- http://m.wap.ghtkgg.cn/jnews/805777.htm
- http://m.wap.ghtkgg.cn/jnews/0022268.htm
- http://m.wap.ghtkgg.cn/jnews/8643482.htm
- http://m.wap.ghtkgg.cn/jnews/9931196.htm
- http://m.wap.ghtkgg.cn/jnews/80916.htm
- http://m.wap.ghtkgg.cn/jnews/93901.htm
- http://m.wap.ghtkgg.cn/jnews/378803.htm
- http://m.wap.ghtkgg.cn/jnews/76032.htm
- http://m.wap.ghtkgg.cn/jnews/804123.htm
- http://m.wap.ghtkgg.cn/jnews/6272578.htm
- http://m.wap.ghtkgg.cn/jnews/54113.htm
- http://m.wap.ghtkgg.cn/jnews/16526.htm
- http://m.wap.ghtkgg.cn/jnews/3063.htm
- http://m.wap.ghtkgg.cn/jnews/324123.htm
- http://m.wap.ghtkgg.cn/jnews/369128.htm
- http://m.wap.ghtkgg.cn/jnews/98289.htm
- http://m.wap.ghtkgg.cn/jnews/8128585.htm
- http://m.wap.ghtkgg.cn/jnews/93236.htm
- http://m.wap.ghtkgg.cn/jnews/41530.htm
- http://m.wap.ghtkgg.cn/jnews/5143.htm
- http://m.wap.ghtkgg.cn/jnews/2549671.htm
- http://m.wap.ghtkgg.cn/jnews/6231050.htm
- http://m.wap.ghtkgg.cn/jnews/757019.htm
- http://m.wap.ghtkgg.cn/jnews/969919.htm
- http://m.wap.ghtkgg.cn/jnews/24764.htm
- http://m.wap.ghtkgg.cn/jnews/814763.htm
- http://m.wap.ghtkgg.cn/jnews/1566.htm
- http://m.wap.ghtkgg.cn/jnews/2348.htm
- http://m.wap.ghtkgg.cn/jnews/818299.htm
- http://m.wap.ghtkgg.cn/jnews/050551.htm
- http://m.wap.ghtkgg.cn/jnews/196887.htm
- http://m.wap.ghtkgg.cn/jnews/0867.htm
- http://m.wap.ghtkgg.cn/jnews/741845.htm
- http://m.wap.ghtkgg.cn/jnews/54181.htm
- http://m.wap.ghtkgg.cn/jnews/42276.htm
- http://m.wap.ghtkgg.cn/jnews/23614.htm
- http://m.wap.ghtkgg.cn/jnews/7316090.htm
- http://m.wap.ghtkgg.cn/jnews/51981.htm
- http://m.wap.ghtkgg.cn/jnews/5595568.htm
- http://m.wap.ghtkgg.cn/jnews/26856.htm
- http://m.wap.ghtkgg.cn/jnews/1937464.htm
- http://m.wap.ghtkgg.cn/jnews/15585.htm
- http://m.wap.ghtkgg.cn/jnews/007577.htm
- http://m.wap.ghtkgg.cn/jnews/7736.htm
- http://m.wap.ghtkgg.cn/jnews/106207.htm
- http://m.wap.ghtkgg.cn/jnews/82441.htm
- http://m.wap.ghtkgg.cn/jnews/03120.htm
- http://m.wap.ghtkgg.cn/jnews/66689.htm
- http://m.wap.ghtkgg.cn/jnews/5992545.htm
- http://m.wap.ghtkgg.cn/jnews/20704.htm
- http://m.wap.ghtkgg.cn/jnews/954740.htm
- http://m.wap.ghtkgg.cn/jnews/3715812.htm
- http://m.wap.ghtkgg.cn/jnews/6079228.htm

## 项目结构

```
webindex/
├── data/                           # 索引数据存储目录
│   ├── categories/                 # 分类定义文件，每个 .json 对应一级分类
│   │   ├── technology.json         # 技术类目索引定义
│   │   ├── industry.json           # 行业报告类目定义
│   │   └── tools.json              # 工具资源类目定义
│   ├── entries/                    # 链接条目存储，按分类分目录存放
│   │   ├── tech/                   # 技术类链接条目
│   │   │   ├── frontend.md         # 前端相关链接清单
│   │   │   └── backend.md          # 后端相关链接清单
│   │   └── research/               # 研究类链接条目
│   │       └── papers.md           # 论文预印本链接清单
│   └── tags.json                   # 全局标签定义与颜色映射
├── src/                            # 源代码目录
│   ├── core/                       # 核心解析与索引引擎
│   │   ├── parser.js               # Markdown / JSON 解析器
│   │   ├── validator.js            # URL 格式校验模块
│   │   └── indexer.js              # 索引构建与缓存生成
│   ├── server/                     # HTTP 服务层
│   │   ├── app.js                  # Express 应用入口
│   │   └── routes/                 # 路由定义
│   │       ├── api.js              # RESTful API 路由
│   │       └── view.js             # 页面渲染路由
│   ├── client/                     # 前端界面源码
│   │   ├── components/             # Vue / React 组件（视具体实现）
│   │   │   ├── DirectoryTree.vue   # 目录树组件
│   │   │   └── LinkList.vue        # 链接列表组件
│   │   ├── assets/                 # 静态资源
│   │   │   ├── styles/             # CSS / SCSS 样式文件
│   │   │   └── scripts/            # 前端 JavaScript 工具函数
│   │   └── index.html              # 单页应用入口模板
│   └── lib/                        # 通用工具库
│       ├── logger.js               # 日志记录模块
│       └── config.js               # 配置加载与合并
├── tests/                          # 单元测试与集成测试
│   ├── unit/                       # 单元测试用例
│   └── integration/                # 端到端测试脚本
├── docs/                           # 项目文档
│   ├── quick-start.md              # 快速入门指南
│   ├── user-guide.md               # 用户操作手册
│   ├── developer-guide.md          # 开发者文档
│   └── operations.md               # 运维部署手册
├── scripts/                        # 辅助运维脚本
│   ├── import.js                   # 批量导入工具
│   └── export.js                   # 数据导出工具
├── .gitignore                      # Git 忽略文件配置
├── package.json                    # Node.js 项目清单
├── package-lock.json               # 依赖锁定文件
├── README.md                       # 项目说明文档（本文件）
└── LICENSE                         # MIT 许可协议文本
```

## 贡献指南

1. 复刻仓库并创建功能分支：从主仓库复刻代码至个人账户，再基于 `main` 分支新建 `feature/your-feature-name` 格式的分支，避免直接向主分支提交。

2. 安装开发依赖与配置环境：执行 `npm install` 安装所有依赖，复制 `.env.example` 为 `.env` 并根据本地路径修改 `DATA_ROOT` 与 `PORT` 变量。

3. 编写或修改索引数据文件：在 `data/entries/` 对应分类目录下编辑 Markdown 文件，每行一个链接并附简短描述，遵守 `[描述文字](URL)` 格式或项目约定的纯文本格式。

4. 运行测试与格式校验：执行 `npm run test` 运行单元测试，确保所有既有用例通过；执行 `npm run lint` 检查代码风格一致性，修复所有警告与错误。

5. 提交变更并发起合并请求：提交信息请遵循 `type(scope): subject` 格式，例如 `feat(parser): add support for numbered list`。推送分支后在 GitHub 上发起 Pull Request，等待维护者审阅。

## 常见问题

**Q: 项目是否会对收录的外部链接进行内容缓存或代理转发？**

A: 不会。WebIndex 仅存储链接地址与描述文本，不下载、不缓存、不代理任何外部页面内容。用户点击链接后直接访问原始站点，所有流量与数据交互发生在用户浏览器与目标服务器之间，项目方不介入传输过程。

**Q: 如何批量更新索引中的链接状态，例如一次性标记大量已失效链接？**

A: 建议结合外部链接检查工具（如 `linkchecker` 或 `wget --spider`）生成失效列表，然后使用项目提供的 `scripts/import.js` 工具配合 `--mark-invalid` 参数批量更新状态标签。具体用法请参考 `docs/operations.md` 中的"链接健康检查"章节。

**Q: 能否将 WebIndex 部署到静态托管服务，如 GitHub Pages 或 Vercel？**

A: 可以。项目支持构建为完全静态站点，执行 `npm run build` 后生成 `dist` 目录，将其内容部署至任意静态托管服务即可。但需注意静态模式下无法使用实时编辑、状态标记写入等动态功能，仅适合作为只读导航页展示。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
