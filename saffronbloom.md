# WebLink Compass

WebLink Compass 是一个面向技术研究者和信息分析人员的轻量级外链资源聚合与导航系统。该项目旨在解决海量分散链接难以有效组织、检索和共享的问题，通过结构化的资源收录机制，将散落于各类技术博客、新闻资讯与文档站点中的高价值外链进行统一归集与分类管理。目标用户包括技术调研工程师、开源社区维护者、网络安全分析师以及需要定期追踪特定领域信息动态的研发人员。本项目不提供爬虫或自动化采集功能，而是作为人工精选资源的索引层，通过清晰的目录树与元数据标注，帮助用户快速定位所需信息源，降低信息过载带来的认知负担。

## 功能概览

- **资源条目标准化收录** 支持对任意 HTTP/HTTPS 外链进行标题、来源站点、摘要描述与收录时间的结构化录入，所有条目存储于本地 JSON 数据文件中，便于版本控制与批量导入导出。

- **多维度分类标签系统** 每条资源可关联一个或多个自定义标签（如 security、frontend、devops、ai），系统提供标签云统计与按标签筛选的视图功能，支持标签合并与重命名操作。

- **全文检索与快速过滤** 基于标题和摘要字段的模糊匹配检索，支持按收录日期范围、来源域名后缀、标签组合等条件进行复合过滤，检索结果按相关度或时间排序。

- **资源状态监控与有效性检查** 定期对已收录的链接进行 HEAD 请求检测，标记失效链接（4xx/5xx 状态码）并生成过期报告，辅助维护者清理或更新资源。

- **外部数据导入与导出** 支持 CSV 与 Markdown 列表格式的资源批量导入，导出功能涵盖 JSON、Markdown 表格及纯 URL 列表三种格式，方便与其他工具链集成。

- **静态站点生成模式** 内置模板引擎可将资源数据渲染为静态 HTML 页面，输出完整的导航站点文件，适合部署到 Nginx 或 GitHub Pages 等静态托管环境。

- **访问热度统计** 记录每条资源的点击次数与最近访问时间，自动生成周榜与月榜，帮助识别高频使用的核心资源。

## 应用场景

- **技术团队内部知识库外链管理** 研发团队可将日常遇到的优质技术文章、官方文档、工具仓库链接统一收录至 WebLink Compass，通过标签区分前端、后端、运维等方向，新成员入职时可快速浏览团队积累的外部参考资料。

- **安全情报信息聚合** 安全研究人员可将不同渠道的漏洞公告、补丁发布、威胁分析报告等链接集中管理，利用日期范围过滤功能快速回溯特定时间窗口内的情报来源，提升应急响应效率。

- **开源项目依赖资源索引** 开源项目维护者可将项目依赖的第三方库文档、社区论坛、示例代码仓库等外链整理为配套资源导航，随项目仓库一同分发，降低用户查找辅助资料的难度。

- **技术资讯周报素材库** 技术编辑或社区运营人员可预先将一周内值得关注的博文、发布公告、视频教程等链接录入系统，利用导出功能生成 Markdown 格式的周报草稿，减少重复手工整理工作。

## 快速开始

以下步骤适用于 Linux/macOS 及 Windows WSL 环境，确保系统已安装 Git 与 Node.js（版本 16.x 及以上）。

```bash
# 克隆项目仓库
git clone https://github.com/weblink-compass/weblink-compass.git
cd weblink-compass

# 安装项目依赖
npm install

# 初始化本地资源数据库（生成默认配置与示例数据）
npm run init

# 启动开发服务器，默认监听 3000 端口
npm run dev
```

启动成功后，访问控制台输出的本地地址（通常为 http://localhost:3000）即可进入 Web 管理界面。首次运行将自动创建 data/ 目录，其中 resources.json 为资源主存储文件，config.yaml 为系统配置文件。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Node.js | 16.14.0 或更高 | 运行时环境，推荐使用 LTS 版本 |
| npm | 8.0.0 或更高 | 包管理器，用于安装项目依赖 |
| Git | 2.25.0 或更高 | 版本控制工具，用于克隆仓库 |
| 磁盘空间 | 至少 200 MB | 存储资源数据库与静态生成文件 |
| 内存 | 至少 512 MB | 开发模式运行所需最低内存 |
| 网络 | 外网访问能力 | 用于首次启动时下载依赖包及后续链接状态检查 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user-guide.md | 如何添加资源、编辑标签、使用检索与过滤功能 |
| 管理员指南 | docs/admin-guide.md | 如何配置状态检查频率、导入导出数据、管理用户权限 |
| 部署文档 | docs/deployment.md | 如何构建静态站点、配置 Nginx 反向代理、使用 Docker 容器化运行 |
| 开发指南 | docs/development.md | 如何扩展标签解析器、自定义前端主题、贡献代码与提交规范 |
| API 参考 | docs/api-reference.md | 后端 RESTful API 的端点列表、请求参数与响应格式说明 |

## 资源列表

- http://m.blog.bwbkj.cn/snews/9589.htm
- http://m.blog.bwbkj.cn/snews/6581242.htm
- http://m.blog.bwbkj.cn/snews/0384857.htm
- http://m.blog.bwbkj.cn/snews/379158.htm
- http://m.blog.bwbkj.cn/snews/0441.htm
- http://m.blog.bwbkj.cn/snews/6998935.htm
- http://m.blog.bwbkj.cn/snews/155216.htm
- http://m.blog.bwbkj.cn/snews/024716.htm
- http://m.blog.bwbkj.cn/snews/756280.htm
- http://m.blog.bwbkj.cn/snews/7039.htm
- http://m.blog.bwbkj.cn/snews/51869.htm
- http://m.blog.bwbkj.cn/snews/69660.htm
- http://m.blog.bwbkj.cn/snews/0551.htm
- http://m.blog.bwbkj.cn/snews/112473.htm
- http://m.blog.bwbkj.cn/snews/30981.htm
- http://m.blog.bwbkj.cn/snews/38345.htm
- http://m.blog.bwbkj.cn/snews/48237.htm
- http://m.blog.bwbkj.cn/snews/9135860.htm
- http://m.blog.bwbkj.cn/snews/9176254.htm
- http://m.blog.bwbkj.cn/snews/78118.htm
- http://m.blog.bwbkj.cn/snews/78384.htm
- http://m.blog.bwbkj.cn/snews/847959.htm
- http://m.blog.bwbkj.cn/snews/1569.htm
- http://m.blog.bwbkj.cn/snews/677127.htm
- http://m.blog.bwbkj.cn/snews/89822.htm
- http://m.blog.bwbkj.cn/snews/7346.htm
- http://m.blog.bwbkj.cn/snews/6968.htm
- http://m.blog.bwbkj.cn/snews/136209.htm
- http://m.blog.bwbkj.cn/snews/4278.htm
- http://m.blog.bwbkj.cn/snews/11274.htm
- http://m.blog.bwbkj.cn/snews/464256.htm
- http://m.blog.bwbkj.cn/snews/800993.htm
- http://m.blog.bwbkj.cn/snews/2876815.htm
- http://m.blog.bwbkj.cn/snews/15273.htm
- http://m.blog.bwbkj.cn/snews/5502506.htm
- http://m.blog.bwbkj.cn/snews/337309.htm
- http://m.blog.bwbkj.cn/snews/78489.htm
- http://m.blog.bwbkj.cn/snews/352188.htm
- http://m.blog.bwbkj.cn/snews/3349605.htm
- http://m.blog.bwbkj.cn/snews/29295.htm
- http://m.blog.bwbkj.cn/snews/0428158.htm
- http://m.blog.bwbkj.cn/snews/65862.htm
- http://m.blog.bwbkj.cn/snews/8059.htm
- http://m.blog.bwbkj.cn/snews/72147.htm
- http://m.blog.bwbkj.cn/snews/475952.htm
- http://m.blog.bwbkj.cn/snews/30826.htm
- http://m.blog.bwbkj.cn/snews/66088.htm
- http://m.blog.bwbkj.cn/snews/940675.htm
- http://m.blog.bwbkj.cn/snews/1137.htm
- http://m.blog.bwbkj.cn/snews/9320756.htm
- http://m.blog.bwbkj.cn/snews/5997836.htm
- http://m.blog.bwbkj.cn/snews/54730.htm
- http://m.blog.bwbkj.cn/snews/41837.htm
- http://m.blog.bwbkj.cn/snews/51526.htm
- http://m.blog.bwbkj.cn/snews/3686.htm
- http://m.blog.bwbkj.cn/snews/508955.htm
- http://m.blog.bwbkj.cn/snews/0477.htm
- http://m.blog.bwbkj.cn/snews/1724130.htm
- http://m.blog.bwbkj.cn/snews/8556061.htm
- http://m.blog.bwbkj.cn/snews/1322988.htm
- http://m.blog.bwbkj.cn/snews/388249.htm
- http://m.blog.bwbkj.cn/snews/94839.htm
- http://m.blog.bwbkj.cn/snews/699051.htm
- http://m.blog.bwbkj.cn/snews/0840.htm
- http://m.blog.bwbkj.cn/snews/762517.htm
- http://m.blog.bwbkj.cn/snews/78513.htm
- http://m.blog.bwbkj.cn/snews/1972201.htm
- http://m.blog.bwbkj.cn/snews/5906.htm
- http://m.blog.bwbkj.cn/snews/38658.htm
- http://m.blog.bwbkj.cn/snews/1045747.htm
- http://m.blog.bwbkj.cn/snews/2517430.htm
- http://m.blog.bwbkj.cn/snews/4755.htm
- http://m.blog.bwbkj.cn/snews/9992935.htm
- http://m.blog.bwbkj.cn/snews/43451.htm
- http://m.blog.bwbkj.cn/snews/99535.htm
- http://m.blog.bwbkj.cn/snews/35158.htm
- http://m.blog.bwbkj.cn/snews/4262.htm
- http://m.blog.bwbkj.cn/snews/9579.htm
- http://m.blog.bwbkj.cn/snews/5433162.htm
- http://m.blog.bwbkj.cn/snews/623613.htm
- http://m.blog.bwbkj.cn/snews/98407.htm
- http://m.blog.bwbkj.cn/snews/490915.htm
- http://m.blog.bwbkj.cn/snews/8944.htm
- http://m.blog.bwbkj.cn/snews/93901.htm
- http://m.blog.bwbkj.cn/snews/52754.htm
- http://m.blog.bwbkj.cn/snews/3031.htm
- http://m.blog.bwbkj.cn/snews/217972.htm
- http://m.blog.bwbkj.cn/snews/086400.htm
- http://m.blog.bwbkj.cn/snews/8298.htm
- http://m.blog.bwbkj.cn/snews/9869.htm
- http://m.blog.bwbkj.cn/snews/5610.htm
- http://m.blog.bwbkj.cn/snews/60268.htm
- http://m.blog.bwbkj.cn/snews/2078.htm
- http://m.blog.bwbkj.cn/snews/1694765.htm
- http://m.blog.bwbkj.cn/snews/78764.htm
- http://m.blog.bwbkj.cn/snews/6927425.htm
- http://m.blog.bwbkj.cn/snews/971819.htm
- http://m.blog.bwbkj.cn/snews/825552.htm
- http://m.blog.bwbkj.cn/snews/355033.htm
- http://m.blog.bwbkj.cn/snews/4340769.htm
- http://m.blog.bwbkj.cn/snews/0498.htm
- http://m.blog.bwbkj.cn/snews/384045.htm
- http://m.blog.bwbkj.cn/snews/2991442.htm
- http://m.blog.bwbkj.cn/snews/31742.htm
- http://m.blog.bwbkj.cn/snews/908060.htm
- http://m.blog.bwbkj.cn/snews/79605.htm
- http://m.blog.bwbkj.cn/snews/41836.htm
- http://m.blog.bwbkj.cn/snews/1173.htm
- http://m.blog.bwbkj.cn/snews/8416652.htm
- http://m.blog.bwbkj.cn/snews/2963371.htm
- http://m.blog.bwbkj.cn/snews/254432.htm
- http://m.blog.bwbkj.cn/snews/05279.htm
- http://m.blog.bwbkj.cn/snews/8574.htm
- http://m.blog.bwbkj.cn/snews/182654.htm
- http://m.blog.bwbkj.cn/snews/9713.htm
- http://m.blog.bwbkj.cn/snews/8507.htm
- http://m.blog.bwbkj.cn/snews/57862.htm
- http://m.blog.bwbkj.cn/snews/3834.htm
- http://m.blog.bwbkj.cn/snews/828593.htm
- http://m.blog.bwbkj.cn/snews/0616.htm
- http://m.blog.bwbkj.cn/snews/263810.htm
- http://m.blog.bwbkj.cn/snews/441018.htm
- http://m.blog.bwbkj.cn/snews/99230.htm
- http://m.blog.bwbkj.cn/snews/7965571.htm
- http://m.blog.bwbkj.cn/snews/0647.htm
- http://m.blog.bwbkj.cn/snews/6732726.htm
- http://m.blog.bwbkj.cn/snews/624957.htm
- http://m.blog.bwbkj.cn/snews/0595.htm
- http://m.blog.bwbkj.cn/snews/9958674.htm
- http://m.blog.bwbkj.cn/snews/6148.htm
- http://m.blog.bwbkj.cn/snews/35088.htm
- http://m.blog.bwbkj.cn/snews/425969.htm
- http://m.blog.bwbkj.cn/snews/91262.htm
- http://m.blog.bwbkj.cn/snews/9540.htm
- http://m.blog.bwbkj.cn/snews/22893.htm
- http://m.blog.bwbkj.cn/snews/1766864.htm
- http://m.blog.bwbkj.cn/snews/49757.htm
- http://m.blog.bwbkj.cn/snews/1372554.htm
- http://m.blog.bwbkj.cn/snews/484632.htm
- http://m.blog.bwbkj.cn/snews/8393453.htm
- http://m.blog.bwbkj.cn/snews/9821.htm
- http://m.blog.bwbkj.cn/snews/206857.htm
- http://m.blog.bwbkj.cn/snews/56036.htm
- http://m.blog.bwbkj.cn/snews/87482.htm
- http://m.blog.bwbkj.cn/snews/67672.htm
- http://m.blog.bwbkj.cn/snews/3857861.htm
- http://m.blog.bwbkj.cn/snews/9401468.htm
- http://m.blog.bwbkj.cn/snews/2520.htm
- http://m.blog.bwbkj.cn/snews/8654.htm
- http://m.blog.bwbkj.cn/snews/1670230.htm
- http://m.blog.bwbkj.cn/snews/1718367.htm
- http://m.blog.bwbkj.cn/snews/2802.htm
- http://m.blog.bwbkj.cn/snews/108804.htm
- http://m.blog.bwbkj.cn/snews/3212.htm
- http://m.blog.bwbkj.cn/snews/79712.htm
- http://m.blog.bwbkj.cn/snews/10888.htm
- http://m.blog.bwbkj.cn/snews/6815903.htm
- http://m.blog.bwbkj.cn/snews/06321.htm
- http://m.blog.bwbkj.cn/snews/18314.htm
- http://m.blog.bwbkj.cn/snews/4445783.htm
- http://m.blog.bwbkj.cn/snews/9069.htm
- http://m.blog.bwbkj.cn/snews/2494250.htm
- http://m.blog.bwbkj.cn/snews/408051.htm
- http://m.blog.bwbkj.cn/snews/4619377.htm
- http://m.blog.bwbkj.cn/snews/9957271.htm
- http://m.blog.bwbkj.cn/snews/56982.htm
- http://m.blog.bwbkj.cn/snews/05303.htm
- http://m.blog.bwbkj.cn/snews/91959.htm
- http://m.blog.bwbkj.cn/snews/63148.htm
- http://m.blog.bwbkj.cn/snews/0356427.htm
- http://m.blog.bwbkj.cn/snews/9011398.htm
- http://m.blog.bwbkj.cn/snews/37381.htm
- http://m.blog.bwbkj.cn/snews/9639728.htm
- http://m.blog.bwbkj.cn/snews/44341.htm
- http://m.blog.bwbkj.cn/snews/9832602.htm
- http://m.blog.bwbkj.cn/snews/859897.htm
- http://m.blog.bwbkj.cn/snews/15647.htm
- http://m.blog.bwbkj.cn/snews/005643.htm
- http://m.blog.bwbkj.cn/snews/545750.htm
- http://m.blog.bwbkj.cn/snews/28086.htm
- http://m.blog.bwbkj.cn/snews/6701276.htm
- http://m.blog.bwbkj.cn/snews/2630.htm
- http://m.blog.bwbkj.cn/snews/9815.htm
- http://m.blog.bwbkj.cn/snews/2577.htm
- http://m.blog.bwbkj.cn/snews/28836.htm
- http://m.blog.bwbkj.cn/snews/5349.htm
- http://m.blog.bwbkj.cn/snews/8206345.htm
- http://m.blog.bwbkj.cn/snews/499995.htm
- http://m.blog.bwbkj.cn/snews/0382.htm
- http://m.blog.bwbkj.cn/snews/453627.htm
- http://m.blog.bwbkj.cn/snews/355427.htm
- http://m.blog.bwbkj.cn/snews/1742831.htm
- http://m.blog.bwbkj.cn/snews/10257.htm
- http://m.blog.bwbkj.cn/snews/89580.htm
- http://m.blog.bwbkj.cn/snews/0994.htm
- http://m.blog.bwbkj.cn/snews/2064509.htm
- http://m.blog.bwbkj.cn/snews/600881.htm
- http://m.blog.bwbkj.cn/snews/79824.htm
- http://m.blog.bwbkj.cn/snews/1697485.htm
- http://m.blog.bwbkj.cn/snews/58259.htm
- http://m.blog.bwbkj.cn/snews/0731.htm
- http://m.blog.bwbkj.cn/snews/5157147.htm
- http://m.blog.bwbkj.cn/snews/708163.htm
- http://m.blog.bwbkj.cn/snews/170008.htm
- http://m.blog.bwbkj.cn/snews/4781134.htm
- http://m.blog.bwbkj.cn/snews/9766.htm
- http://m.blog.bwbkj.cn/snews/95126.htm
- http://m.blog.bwbkj.cn/snews/3527.htm
- http://m.blog.bwbkj.cn/snews/24648.htm
- http://m.blog.bwbkj.cn/snews/86858.htm
- http://m.blog.bwbkj.cn/snews/241050.htm
- http://m.blog.bwbkj.cn/snews/30830.htm
- http://m.blog.bwbkj.cn/snews/7703269.htm
- http://m.blog.bwbkj.cn/snews/4491974.htm
- http://m.blog.bwbkj.cn/snews/2533.htm
- http://m.blog.bwbkj.cn/snews/41466.htm
- http://m.blog.bwbkj.cn/snews/519670.htm
- http://m.blog.bwbkj.cn/snews/90343.htm
- http://m.blog.bwbkj.cn/snews/8291.htm
- http://m.blog.bwbkj.cn/snews/7299228.htm
- http://m.blog.bwbkj.cn/snews/56552.htm
- http://m.blog.bwbkj.cn/snews/750091.htm
- http://m.blog.bwbkj.cn/snews/3672.htm
- http://m.blog.bwbkj.cn/snews/37145.htm
- http://m.blog.bwbkj.cn/snews/4783.htm
- http://m.blog.bwbkj.cn/snews/57662.htm
- http://m.blog.bwbkj.cn/snews/432097.htm
- http://m.blog.bwbkj.cn/snews/596731.htm
- http://m.blog.bwbkj.cn/snews/4342.htm
- http://m.blog.bwbkj.cn/snews/5026.htm
- http://m.blog.bwbkj.cn/snews/94281.htm
- http://m.blog.bwbkj.cn/snews/0197.htm
- http://m.blog.bwbkj.cn/snews/9980.htm
- http://m.blog.bwbkj.cn/snews/5213.htm
- http://m.blog.bwbkj.cn/snews/81597.htm
- http://m.blog.bwbkj.cn/snews/641557.htm
- http://m.blog.bwbkj.cn/snews/783423.htm
- http://m.blog.bwbkj.cn/snews/912999.htm
- http://m.blog.bwbkj.cn/snews/14220.htm
- http://m.blog.bwbkj.cn/snews/497203.htm
- http://m.blog.bwbkj.cn/snews/5200198.htm
- http://m.blog.bwbkj.cn/snews/5584545.htm
- http://m.blog.bwbkj.cn/snews/490673.htm
- http://m.blog.bwbkj.cn/snews/755269.htm
- http://m.blog.bwbkj.cn/snews/5788097.htm
- http://m.blog.bwbkj.cn/snews/4581.htm
- http://m.blog.bwbkj.cn/snews/6911851.htm
- http://m.blog.bwbkj.cn/snews/361141.htm
- http://m.blog.bwbkj.cn/snews/8140279.htm
- http://m.blog.bwbkj.cn/snews/484564.htm
- http://m.blog.bwbkj.cn/snews/8550719.htm
- http://m.blog.bwbkj.cn/snews/16155.htm
- http://m.blog.bwbkj.cn/snews/9167054.htm
- http://m.blog.bwbkj.cn/snews/5762487.htm
- http://m.blog.bwbkj.cn/snews/144898.htm
- http://m.blog.bwbkj.cn/snews/0794629.htm
- http://m.blog.bwbkj.cn/snews/46619.htm
- http://m.blog.bwbkj.cn/snews/10453.htm
- http://m.blog.bwbkj.cn/snews/838265.htm
- http://m.blog.bwbkj.cn/snews/9512.htm
- http://m.blog.bwbkj.cn/snews/1151970.htm
- http://m.blog.bwbkj.cn/snews/0879802.htm
- http://m.blog.bwbkj.cn/snews/48708.htm
- http://m.blog.bwbkj.cn/snews/37731.htm
- http://m.blog.bwbkj.cn/snews/9187309.htm
- http://m.blog.bwbkj.cn/snews/389983.htm
- http://m.blog.bwbkj.cn/snews/45532.htm
- http://m.blog.bwbkj.cn/snews/4608440.htm
- http://m.blog.bwbkj.cn/snews/5592.htm
- http://m.blog.bwbkj.cn/snews/458616.htm
- http://m.blog.bwbkj.cn/snews/981016.htm
- http://m.blog.bwbkj.cn/snews/3734667.htm
- http://m.blog.bwbkj.cn/snews/1998.htm
- http://m.blog.bwbkj.cn/snews/233088.htm
- http://m.blog.bwbkj.cn/snews/9344.htm
- http://m.blog.bwbkj.cn/snews/2144.htm
- http://m.blog.bwbkj.cn/snews/3468.htm
- http://m.blog.bwbkj.cn/snews/0221.htm
- http://m.blog.bwbkj.cn/snews/4207.htm
- http://m.blog.bwbkj.cn/snews/223233.htm
- http://m.blog.bwbkj.cn/snews/0984.htm
- http://m.blog.bwbkj.cn/snews/9884.htm
- http://m.blog.bwbkj.cn/snews/14465.htm
- http://m.blog.bwbkj.cn/snews/8681100.htm
- http://m.blog.bwbkj.cn/snews/35821.htm
- http://m.blog.bwbkj.cn/snews/082583.htm
- http://m.blog.bwbkj.cn/snews/7023.htm
- http://m.blog.bwbkj.cn/snews/042345.htm
- http://m.blog.bwbkj.cn/snews/51772.htm
- http://m.blog.bwbkj.cn/snews/185038.htm
- http://m.blog.bwbkj.cn/snews/5321.htm
- http://m.blog.bwbkj.cn/snews/53137.htm
- http://m.blog.bwbkj.cn/snews/1977416.htm
- http://m.blog.bwbkj.cn/snews/0261550.htm
- http://m.blog.bwbkj.cn/snews/9781272.htm
- http://m.blog.bwbkj.cn/snews/2566.htm
- http://m.blog.bwbkj.cn/snews/731912.htm
- http://m.blog.bwbkj.cn/snews/5328481.htm
- http://m.blog.bwbkj.cn/snews/790030.htm
- http://m.blog.bwbkj.cn/snews/09693.htm

## 项目结构

```
weblink-compass/
├── src/                                # 核心源代码目录
│   ├── server/                         # 后端服务层 (Express.js)
│   │   ├── index.js                    # 服务入口，初始化路由与中间件
│   │   ├── routes/                     # RESTful API 路由定义 (resources, tags, stats)
│   │   └── middleware/                 # 请求日志、CORS、错误处理中间件
│   ├── core/                           # 业务逻辑层
│   │   ├── resource-manager.js         # 资源增删改查、标签管理核心逻辑
│   │   ├── link-validator.js           # 链接有效性异步检查与状态更新
│   │   └── stats-collector.js          # 点击统计与热度排行计算
│   ├── frontend/                       # 前端静态资源 (原生 JavaScript + CSS)
│   │   ├── index.html                  # 管理界面主页面
│   │   ├── app.js                      # 前端交互逻辑 (列表渲染、表单提交、筛选)
│   │   └── style.css                   # 响应式布局与暗色主题样式
│   └── generators/                     # 静态站点生成器
│       ├── html-renderer.js            # 基于 EJS 模板渲染 HTML 页面
│       └── markdown-exporter.js        # 资源列表导出为 Markdown 格式
├── data/                               # 数据存储目录 (默认 Git 忽略)
│   ├── resources.json                  # 资源主数据库 (JSON 数组)
│   ├── tags.json                       # 标签列表与使用频次统计
│   └── config.yaml                     # 系统配置文件 (检查间隔、端口、导出选项)
├── docs/                               # 项目文档 (用户手册、部署指南、API 参考)
│   ├── user-guide.md
│   ├── admin-guide.md
│   ├── deployment.md
│   ├── development.md
│   └── api-reference.md
├── tests/                              # 单元测试与集成测试 (Jest)
│   ├── unit/                           # 核心模块单元测试
│   └── integration/                    # API 端点与数据库读写集成测试
├── scripts/                            # 辅助运维脚本
│   ├── init-db.js                      # 初始化数据库与示例数据
│   ├── validate-links.js               # 手动触发链接检查
│   └── export-static.js                # 命令行静态站点生成
├── .github/                            # GitHub 社区配置文件
│   ├── ISSUE_TEMPLATE/                 # 问题报告与功能请求模板
│   └── workflows/                      # CI 流水线 (测试、构建、部署)
├── package.json                        # npm 依赖清单与脚本定义
├── .eslintrc.js                        # ESLint 代码规范配置
├── .gitignore                          # Git 版本控制忽略规则
└── README.md                           # 项目说明文档 (本文件)
```

## 贡献指南

1. 查阅 issue 列表，选择未被认领且与自身技能匹配的任务，或提交新的功能建议与缺陷报告，描述清楚问题现象、复现步骤及预期行为。

2. 派生项目仓库至个人账户，基于主分支的 develop 分支创建功能分支，分支命名遵循 feat/功能简述 或 fix/问题简述 格式，确保代码风格符合 .eslintrc.js 中定义的规则。

3. 开发完成后，补充或更新对应的单元测试用例，确保所有测试通过（npm test），并更新 docs/ 目录下受影响的文档，尤其是 API 变更或配置项新增的情况。

4. 提交代码时编写清晰的 commit message，遵循 Conventional Commits 规范（类型包括 feat、fix、docs、style、refactor、test、chore），描述变更原因与影响范围。

5. 向主仓库发起 Pull Request，目标分支为 develop，在 PR 描述中关联相关 issue 编号，等待维护者审核反馈；审核通过后由维护者合并至主分支。

## 常见问题

**Q: 资源链接状态检查显示大量超时或失败，如何调整检查参数？**

A: 可在 data/config.yaml 文件中修改 validator 配置节，调整 timeout（单位毫秒）、retryCount 与 concurrency 参数。默认超时 5000ms，重试 2 次，并发 10 个请求。若目标站点网络响应较慢，可适当增加超时与重试次数，但请注意过高的并发可能被目标站点限流。

**Q: 静态站点生成后，页面中的资源链接点击无法统计，如何解决？**

A: 静态模式下的点击统计依赖前端 JavaScript 发送信标请求。请确认生成的 HTML 页面中包含 stats-collector.js 脚本，且 config.yaml 中 frontend.statsEndpoint 配置指向正确的后端 API 地址。若部署为纯静态站点无后端支持，可改用 localStorage 本地缓存统计并在导出时汇总，相关配置项见部署文档。

**Q: 导入大量资源时页面响应变慢，有什么优化建议？**

A: 单次导入建议不超过 500 条记录，超过此数量可使用批量导入接口（POST /api/resources/batch），该接口采用流式处理避免阻塞事件循环。同时建议将 resources.json 文件大小控制在 10 MB 以内，若资源数量超过 10000 条，考虑使用 SQLite 版本分支（项目提供 sqlite 实验分支）。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:12
