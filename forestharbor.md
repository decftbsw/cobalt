# WebIndex 聚合导航系统

WebIndex 是一个面向技术调研与信息聚合场景的轻量级外链资源导航系统。本项目定位于为开发者、技术决策者与信息分析人员提供结构化的外部新闻与资讯入口索引，通过固定格式的链接聚合机制降低信息分散带来的检索成本。本系统不存储任何原始内容，仅作为 URL 索引层存在，适用于个人知识库辅助、团队技术雷达构建以及自动化信息采集管道的前置环节。

WebIndex 的核心设计理念包含三点：URL 原样留存、分类索引透明、采集路径可审计。系统不对任何外部资源进行内容改写或摘要生成，所有链接均以原始形态呈现，确保信息溯源路径的完整性与可验证性。

## 功能概览

**裸链接原样收录** 所有外部 URL 均以用户提交时的原始格式直接存入索引库，不进行协议补全、域名规范化或路径重写，确保每一条链接的完整性可被第三方审计工具验证。

**多层级索引组织** 支持按资源批次、来源域名、文件类型等多维度建立索引视图，便于在大规模链接集合中快速定位特定范围的目标资源。

**快速部署与零配置启动** 项目采用静态文件生成方案，克隆后即可通过本地 HTTP 服务或直接挂载至对象存储托管平台运行，无需数据库或后端运行时环境。

**可扩展的链接清单管理** 所有资源列表以 Markdown 表格与列表形式维护，支持通过 Pull Request 批量增删条目，适配持续集成工作流中的自动化更新需求。

**HTML 元数据提取支持** 提供可选的辅助脚本，对已收录链接进行标题、描述与关键词的批量拉取，生成侧栏索引文件以提升本地浏览体验。

**访问日志与失效检测接口** 内置轻量级链接状态检查工具，可定期输出 HTTP 状态码报表，辅助维护者识别失效或重定向的资源条目。

**离线浏览友好** 所有索引页面与资源清单均为静态生成，支持完全离线打开，适用于内网环境或移动存储设备中的文档查阅场景。

## 应用场景

技术团队内部知识库构建
技术团队在日常研发过程中需要频繁查阅外部资讯、公告与技术博客。WebIndex 可作为知识库的导航入口层，将分散的外部链接按批次导入并附加内部备注，团队成员通过访问本地部署的索引页面即可获取经过筛选的参考资源列表，减少重复搜索时间。

自动化信息采集管道的前置配置
在构建定向爬虫或 RSS 聚合服务时，通常需要维护一份种子 URL 清单。WebIndex 的链接清单文件可直接作为采集管道的输入源，运维人员通过版本控制系统管理 URL 的增删改，配合 CI/CD 实现种子列表的变更自动同步至采集节点。

技术调研与竞品动态跟踪
产品经理与技术调研人员可定期将关注的外部新闻链接导入 WebIndex，按时间批次归档。系统提供的批次编号与原始链接输出能力，使得调研报告中的引用来源可被清晰追溯，满足合规审计对于信息来源记录的要求。

个人开发者阅读清单管理
个人开发者可使用 WebIndex 维护自己的技术阅读列表，将日常浏览过程中发现的感兴趣文章统一归档。静态页面的本地打开方式适合在碎片化时间中快速翻阅，无需依赖第三方网络收藏夹服务。

## 快速开始

以下指令适用于 Linux 与 macOS 环境，Windows 用户可使用 Git Bash 或 WSL 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webindex/webindex.git
cd webindex

# 安装依赖工具（基于 Node.js，用于本地预览与链接检查）
npm install -g markdown-index-cli@1.2.0
npm install

# 运行本地预览服务，默认监听端口 8080
npm run serve
```

执行完毕后，在浏览器中访问 http://localhost:8080 即可查看索引首页。所有资源列表位于 /resources 目录下，按批次编号组织。

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|---|---|---|
| Node.js | 18.x 或更高 | 用于运行本地预览服务与链接检查脚本，LTS 版本优先推荐 |
| npm | 8.x 或更高 | 包管理工具，用于安装项目依赖的命令行工具 |
| Git | 2.25 或更高 | 用于克隆仓库以及参与贡献时的版本控制操作 |
| markdown-index-cli | 1.2.0 | 本地索引生成工具，用于将 Markdown 列表渲染为可浏览的 HTML 页面 |
| http-server | 14.0.0 | 可选依赖，用于替代内置预览服务，提供更灵活的静态托管配置 |
| curl | 7.68 或更高 | 用于运行链接状态检查脚本，非强制但推荐安装 |
| grep | 3.4 或更高 | 配合检查脚本进行日志过滤，Linux 与 macOS 默认已预装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户入门 | /docs/quick-start.md | 如何在一分钟内完成部署并看到索引页面；如何添加第一批外部链接 |
| 维护指南 | /docs/maintenance.md | 如何批量更新资源列表；如何运行链接失效检测；如何清理重复条目 |
| 设计说明 | /docs/architecture.md | 索引系统的目录结构设计依据；静态生成方案的选型理由；扩展性考量 |
| 贡献规范 | /docs/contributing.md | 提交链接清单的格式要求；Pull Request 的标题与描述规范；审核流程说明 |

## 资源列表

- http://m.wap.oexnr.cn/jnews/4050476.htm
- http://m.wap.oexnr.cn/jnews/8151457.htm
- http://m.wap.oexnr.cn/jnews/198644.htm
- http://m.wap.oexnr.cn/jnews/0561.htm
- http://m.wap.oexnr.cn/jnews/95054.htm
- http://m.wap.oexnr.cn/jnews/4288.htm
- http://m.wap.oexnr.cn/jnews/4969.htm
- http://m.wap.oexnr.cn/jnews/7980643.htm
- http://m.wap.oexnr.cn/jnews/6031.htm
- http://m.wap.oexnr.cn/jnews/0497845.htm
- http://m.wap.oexnr.cn/jnews/3650.htm
- http://m.wap.oexnr.cn/jnews/1681.htm
- http://m.wap.oexnr.cn/jnews/5046.htm
- http://m.wap.oexnr.cn/jnews/6826872.htm
- http://m.wap.oexnr.cn/jnews/5122.htm
- http://m.wap.oexnr.cn/jnews/69834.htm
- http://m.wap.oexnr.cn/jnews/11902.htm
- http://m.wap.oexnr.cn/jnews/953668.htm
- http://m.wap.oexnr.cn/jnews/940484.htm
- http://m.wap.oexnr.cn/jnews/6342.htm
- http://m.wap.oexnr.cn/jnews/38017.htm
- http://m.wap.oexnr.cn/jnews/27630.htm
- http://m.wap.oexnr.cn/jnews/17869.htm
- http://m.wap.oexnr.cn/jnews/28075.htm
- http://m.wap.oexnr.cn/jnews/859637.htm
- http://m.wap.oexnr.cn/jnews/310517.htm
- http://m.wap.oexnr.cn/jnews/60456.htm
- http://m.wap.oexnr.cn/jnews/4165107.htm
- http://m.wap.oexnr.cn/jnews/2032138.htm
- http://m.wap.oexnr.cn/jnews/1457245.htm
- http://m.wap.oexnr.cn/jnews/71388.htm
- http://m.wap.oexnr.cn/jnews/833447.htm
- http://m.wap.oexnr.cn/jnews/226655.htm
- http://m.wap.oexnr.cn/jnews/03875.htm
- http://m.wap.oexnr.cn/jnews/8006427.htm
- http://m.wap.oexnr.cn/jnews/292280.htm
- http://m.wap.oexnr.cn/jnews/231431.htm
- http://m.wap.oexnr.cn/jnews/6822868.htm
- http://m.wap.oexnr.cn/jnews/272258.htm
- http://m.wap.oexnr.cn/jnews/8192.htm
- http://m.wap.oexnr.cn/jnews/711052.htm
- http://m.wap.oexnr.cn/jnews/562241.htm
- http://m.wap.oexnr.cn/jnews/8041020.htm
- http://m.wap.oexnr.cn/jnews/02434.htm
- http://m.wap.oexnr.cn/jnews/6511.htm
- http://m.wap.oexnr.cn/jnews/1062.htm
- http://m.wap.oexnr.cn/jnews/7441.htm
- http://m.wap.oexnr.cn/jnews/1258.htm
- http://m.wap.oexnr.cn/jnews/251517.htm
- http://m.wap.oexnr.cn/jnews/272304.htm
- http://m.wap.oexnr.cn/jnews/137739.htm
- http://m.wap.oexnr.cn/jnews/22413.htm
- http://m.wap.oexnr.cn/jnews/4744.htm
- http://m.wap.oexnr.cn/jnews/7674565.htm
- http://m.wap.oexnr.cn/jnews/84387.htm
- http://m.wap.oexnr.cn/jnews/849136.htm
- http://m.wap.oexnr.cn/jnews/14660.htm
- http://m.wap.oexnr.cn/jnews/9767.htm
- http://m.wap.oexnr.cn/jnews/0038478.htm
- http://m.wap.oexnr.cn/jnews/932070.htm
- http://m.wap.oexnr.cn/jnews/101931.htm
- http://m.wap.oexnr.cn/jnews/17790.htm
- http://m.wap.oexnr.cn/jnews/52341.htm
- http://m.wap.oexnr.cn/jnews/37632.htm
- http://m.wap.oexnr.cn/jnews/390201.htm
- http://m.wap.oexnr.cn/jnews/7116210.htm
- http://m.wap.oexnr.cn/jnews/980014.htm
- http://m.wap.oexnr.cn/jnews/815939.htm
- http://m.wap.oexnr.cn/jnews/339312.htm
- http://m.wap.oexnr.cn/jnews/28840.htm
- http://m.wap.oexnr.cn/jnews/9151.htm
- http://m.wap.oexnr.cn/jnews/382336.htm
- http://m.wap.oexnr.cn/jnews/781121.htm
- http://m.wap.oexnr.cn/jnews/400123.htm
- http://m.wap.oexnr.cn/jnews/465952.htm
- http://m.wap.oexnr.cn/jnews/12867.htm
- http://m.wap.oexnr.cn/jnews/6121.htm
- http://m.wap.oexnr.cn/jnews/3298.htm
- http://m.wap.oexnr.cn/jnews/408831.htm
- http://m.wap.oexnr.cn/jnews/5634928.htm
- http://m.wap.oexnr.cn/jnews/9397.htm
- http://m.wap.oexnr.cn/jnews/06406.htm
- http://m.wap.oexnr.cn/jnews/269658.htm
- http://m.wap.oexnr.cn/jnews/6264.htm
- http://m.wap.oexnr.cn/jnews/760136.htm
- http://m.wap.oexnr.cn/jnews/17652.htm
- http://m.wap.oexnr.cn/jnews/0359.htm
- http://m.wap.oexnr.cn/jnews/3352322.htm
- http://m.wap.oexnr.cn/jnews/84440.htm
- http://m.wap.oexnr.cn/jnews/77249.htm
- http://m.wap.oexnr.cn/jnews/6707222.htm
- http://m.wap.oexnr.cn/jnews/09123.htm
- http://m.wap.oexnr.cn/jnews/9379.htm
- http://m.wap.oexnr.cn/jnews/425793.htm
- http://m.wap.oexnr.cn/jnews/1600.htm
- http://m.wap.oexnr.cn/jnews/36122.htm
- http://m.wap.oexnr.cn/jnews/3502.htm
- http://m.wap.oexnr.cn/jnews/22898.htm
- http://m.wap.oexnr.cn/jnews/9849.htm
- http://m.wap.oexnr.cn/jnews/2150705.htm
- http://m.wap.oexnr.cn/jnews/1043000.htm
- http://m.wap.oexnr.cn/jnews/11282.htm
- http://m.wap.oexnr.cn/jnews/767556.htm
- http://m.wap.oexnr.cn/jnews/011369.htm
- http://m.wap.oexnr.cn/jnews/03823.htm
- http://m.wap.oexnr.cn/jnews/8927.htm
- http://m.wap.oexnr.cn/jnews/69542.htm
- http://m.wap.oexnr.cn/jnews/26247.htm
- http://m.wap.oexnr.cn/jnews/2447.htm
- http://m.wap.oexnr.cn/jnews/8729.htm
- http://m.wap.oexnr.cn/jnews/22333.htm
- http://m.wap.oexnr.cn/jnews/73792.htm
- http://m.wap.oexnr.cn/jnews/4384412.htm
- http://m.wap.oexnr.cn/jnews/5511.htm
- http://m.wap.oexnr.cn/jnews/5237381.htm
- http://m.wap.oexnr.cn/jnews/70956.htm
- http://m.wap.oexnr.cn/jnews/648425.htm
- http://m.wap.oexnr.cn/jnews/1100767.htm
- http://m.wap.oexnr.cn/jnews/1729328.htm
- http://m.wap.oexnr.cn/jnews/5086301.htm
- http://m.wap.oexnr.cn/jnews/650040.htm
- http://m.wap.oexnr.cn/jnews/5406692.htm
- http://m.wap.oexnr.cn/jnews/474196.htm
- http://m.wap.oexnr.cn/jnews/21096.htm
- http://m.wap.oexnr.cn/jnews/461755.htm
- http://m.wap.oexnr.cn/jnews/56301.htm
- http://m.wap.oexnr.cn/jnews/77785.htm
- http://m.wap.oexnr.cn/jnews/1280.htm
- http://m.wap.oexnr.cn/jnews/8237618.htm
- http://m.wap.oexnr.cn/jnews/499262.htm
- http://m.wap.oexnr.cn/jnews/4180489.htm
- http://m.wap.oexnr.cn/jnews/017364.htm
- http://m.wap.oexnr.cn/jnews/98058.htm
- http://m.wap.oexnr.cn/jnews/95941.htm
- http://m.wap.oexnr.cn/jnews/942314.htm
- http://m.wap.oexnr.cn/jnews/226698.htm
- http://m.wap.oexnr.cn/jnews/6410216.htm
- http://m.wap.oexnr.cn/jnews/854980.htm
- http://m.wap.oexnr.cn/jnews/42170.htm
- http://m.wap.oexnr.cn/jnews/243192.htm
- http://m.wap.oexnr.cn/jnews/5282.htm
- http://m.wap.oexnr.cn/jnews/337684.htm
- http://m.wap.oexnr.cn/jnews/1942.htm
- http://m.wap.oexnr.cn/jnews/3687075.htm
- http://m.wap.oexnr.cn/jnews/5680.htm
- http://m.wap.oexnr.cn/jnews/4591.htm
- http://m.wap.oexnr.cn/jnews/3142255.htm
- http://m.wap.oexnr.cn/jnews/90944.htm
- http://m.wap.oexnr.cn/jnews/91968.htm
- http://m.wap.oexnr.cn/jnews/0885.htm
- http://m.wap.oexnr.cn/jnews/2700867.htm
- http://m.wap.oexnr.cn/jnews/37699.htm
- http://m.wap.oexnr.cn/jnews/72023.htm
- http://m.wap.oexnr.cn/jnews/460860.htm
- http://m.wap.oexnr.cn/jnews/76505.htm
- http://m.wap.oexnr.cn/jnews/211258.htm
- http://m.wap.oexnr.cn/jnews/58193.htm
- http://m.wap.oexnr.cn/jnews/7348751.htm
- http://m.wap.oexnr.cn/jnews/5090.htm
- http://m.wap.oexnr.cn/jnews/9150.htm
- http://m.wap.oexnr.cn/jnews/2171519.htm
- http://m.wap.oexnr.cn/jnews/93147.htm
- http://m.wap.oexnr.cn/jnews/6343865.htm
- http://m.wap.oexnr.cn/jnews/1207215.htm
- http://m.wap.oexnr.cn/jnews/8117415.htm
- http://m.wap.oexnr.cn/jnews/2943277.htm
- http://m.wap.oexnr.cn/jnews/1130.htm
- http://m.wap.oexnr.cn/jnews/462178.htm
- http://m.wap.oexnr.cn/jnews/77845.htm
- http://m.wap.oexnr.cn/jnews/18255.htm
- http://m.wap.oexnr.cn/jnews/2162749.htm
- http://m.wap.oexnr.cn/jnews/403994.htm
- http://m.wap.oexnr.cn/jnews/476891.htm
- http://m.wap.oexnr.cn/jnews/0889.htm
- http://m.wap.oexnr.cn/jnews/0731781.htm
- http://m.wap.oexnr.cn/jnews/751856.htm
- http://m.wap.oexnr.cn/jnews/8013.htm
- http://m.wap.oexnr.cn/jnews/25075.htm
- http://m.wap.oexnr.cn/jnews/899472.htm
- http://m.wap.oexnr.cn/jnews/3243238.htm
- http://m.wap.oexnr.cn/jnews/7239174.htm
- http://m.wap.oexnr.cn/jnews/2632832.htm
- http://m.wap.oexnr.cn/jnews/7426.htm
- http://m.wap.oexnr.cn/jnews/38087.htm
- http://m.wap.oexnr.cn/jnews/6636837.htm
- http://m.wap.oexnr.cn/jnews/66831.htm
- http://m.wap.oexnr.cn/jnews/2183965.htm
- http://m.wap.oexnr.cn/jnews/6761322.htm
- http://m.wap.oexnr.cn/jnews/0015.htm
- http://m.wap.oexnr.cn/jnews/8033.htm
- http://m.wap.oexnr.cn/jnews/1707939.htm
- http://m.wap.oexnr.cn/jnews/42969.htm
- http://m.wap.oexnr.cn/jnews/8829.htm
- http://m.wap.oexnr.cn/jnews/2263237.htm
- http://m.wap.oexnr.cn/jnews/3003.htm
- http://m.wap.oexnr.cn/jnews/910772.htm
- http://m.wap.oexnr.cn/jnews/9607152.htm
- http://m.wap.oexnr.cn/jnews/40214.htm
- http://m.wap.oexnr.cn/jnews/5391.htm
- http://m.wap.oexnr.cn/jnews/871564.htm
- http://m.wap.oexnr.cn/jnews/2204931.htm
- http://m.wap.oexnr.cn/jnews/8529847.htm
- http://m.wap.oexnr.cn/jnews/32781.htm
- http://m.wap.oexnr.cn/jnews/0841255.htm
- http://m.wap.oexnr.cn/jnews/36668.htm
- http://m.wap.oexnr.cn/jnews/6326869.htm
- http://m.wap.oexnr.cn/jnews/2007928.htm
- http://m.wap.oexnr.cn/jnews/78151.htm
- http://m.wap.oexnr.cn/jnews/9308.htm
- http://m.wap.oexnr.cn/jnews/1900608.htm
- http://m.wap.oexnr.cn/jnews/639917.htm
- http://m.wap.oexnr.cn/jnews/2512081.htm
- http://m.wap.oexnr.cn/jnews/50044.htm
- http://m.wap.oexnr.cn/jnews/1870.htm
- http://m.wap.oexnr.cn/jnews/282921.htm
- http://m.wap.oexnr.cn/jnews/30061.htm
- http://m.wap.oexnr.cn/jnews/9267.htm
- http://m.wap.oexnr.cn/jnews/7558695.htm
- http://m.wap.oexnr.cn/jnews/62611.htm
- http://m.wap.oexnr.cn/jnews/06084.htm
- http://m.wap.oexnr.cn/jnews/1116827.htm
- http://m.wap.oexnr.cn/jnews/8396.htm
- http://m.wap.oexnr.cn/jnews/60759.htm
- http://m.wap.oexnr.cn/jnews/701813.htm
- http://m.wap.oexnr.cn/jnews/51308.htm
- http://m.wap.oexnr.cn/jnews/920142.htm
- http://m.wap.oexnr.cn/jnews/48342.htm
- http://m.wap.oexnr.cn/jnews/931418.htm
- http://m.wap.oexnr.cn/jnews/427298.htm
- http://m.wap.oexnr.cn/jnews/5608992.htm
- http://m.wap.oexnr.cn/jnews/71416.htm
- http://m.wap.oexnr.cn/jnews/04522.htm
- http://m.wap.oexnr.cn/jnews/22216.htm
- http://m.wap.oexnr.cn/jnews/3586314.htm
- http://m.wap.oexnr.cn/jnews/2839.htm
- http://m.wap.oexnr.cn/jnews/573362.htm
- http://m.wap.oexnr.cn/jnews/2882219.htm
- http://m.wap.oexnr.cn/jnews/44232.htm
- http://m.wap.oexnr.cn/jnews/065768.htm
- http://m.wap.oexnr.cn/jnews/535046.htm
- http://m.wap.oexnr.cn/jnews/7023.htm
- http://m.wap.oexnr.cn/jnews/3635.htm
- http://m.wap.oexnr.cn/jnews/6540.htm
- http://m.wap.oexnr.cn/jnews/7384.htm
- http://m.wap.oexnr.cn/jnews/58214.htm
- http://m.wap.oexnr.cn/jnews/5276.htm
- http://m.wap.oexnr.cn/jnews/7630.htm
- http://m.wap.oexnr.cn/jnews/85131.htm
- http://m.wap.oexnr.cn/jnews/9406.htm
- http://m.wap.oexnr.cn/jnews/69259.htm
- http://m.wap.oexnr.cn/jnews/1092060.htm
- http://m.wap.oexnr.cn/jnews/0273.htm
- http://m.wap.oexnr.cn/jnews/5645127.htm
- http://m.wap.oexnr.cn/jnews/329344.htm
- http://m.wap.oexnr.cn/jnews/4980804.htm
- http://m.wap.oexnr.cn/jnews/859177.htm
- http://m.wap.oexnr.cn/jnews/6329689.htm
- http://m.wap.oexnr.cn/jnews/1927014.htm
- http://m.wap.oexnr.cn/jnews/7841.htm
- http://m.wap.oexnr.cn/jnews/8232424.htm
- http://m.wap.oexnr.cn/jnews/84623.htm
- http://m.wap.oexnr.cn/jnews/2733.htm
- http://m.wap.oexnr.cn/jnews/0861.htm
- http://m.wap.oexnr.cn/jnews/59362.htm
- http://m.wap.oexnr.cn/jnews/7969.htm
- http://m.wap.oexnr.cn/jnews/15137.htm
- http://m.wap.oexnr.cn/jnews/5380858.htm
- http://m.wap.oexnr.cn/jnews/94024.htm
- http://m.wap.oexnr.cn/jnews/9650843.htm
- http://m.wap.oexnr.cn/jnews/73852.htm
- http://m.wap.oexnr.cn/jnews/6730.htm
- http://m.wap.oexnr.cn/jnews/0090.htm
- http://m.wap.oexnr.cn/jnews/5847.htm
- http://m.wap.oexnr.cn/jnews/589502.htm
- http://m.wap.oexnr.cn/jnews/3151491.htm
- http://m.wap.oexnr.cn/jnews/5858933.htm
- http://m.wap.oexnr.cn/jnews/619499.htm
- http://m.wap.oexnr.cn/jnews/591998.htm
- http://m.wap.oexnr.cn/jnews/50660.htm
- http://m.wap.oexnr.cn/jnews/646751.htm
- http://m.wap.oexnr.cn/jnews/19832.htm
- http://m.wap.oexnr.cn/jnews/997571.htm
- http://m.wap.oexnr.cn/jnews/4945.htm
- http://m.wap.oexnr.cn/jnews/97801.htm
- http://m.wap.oexnr.cn/jnews/276837.htm
- http://m.wap.oexnr.cn/jnews/124253.htm
- http://m.wap.oexnr.cn/jnews/3167.htm
- http://m.wap.oexnr.cn/jnews/4807.htm
- http://m.wap.oexnr.cn/jnews/8909.htm
- http://m.wap.oexnr.cn/jnews/2005.htm
- http://m.wap.oexnr.cn/jnews/169863.htm
- http://m.wap.oexnr.cn/jnews/2457408.htm
- http://m.wap.oexnr.cn/jnews/623002.htm
- http://m.wap.oexnr.cn/jnews/1439503.htm
- http://m.wap.oexnr.cn/jnews/5424.htm
- http://m.wap.oexnr.cn/jnews/4237848.htm
- http://m.wap.oexnr.cn/jnews/2559132.htm
- http://m.wap.oexnr.cn/jnews/9367129.htm
- http://m.wap.oexnr.cn/jnews/15449.htm
- http://m.wap.oexnr.cn/jnews/15809.htm

## 项目结构

```
webindex/
├── index.md                     # 项目首页与总览，包含批次索引入口
├── README.md                    # 本文件，项目说明与使用指南
├── LICENSE                      # MIT 许可证文件
├── .gitignore                   # Git 忽略规则，排除临时文件与本地配置
│
├── resources/                   # 资源清单目录，按批次组织
│   ├── batch_001/               # 第 1 批次资源，含 metadata.json 与 links.md
│   ├── batch_002/               # 第 2 批次资源，格式同上
│   └── batch_062/               # 第 62 批次资源，当前活跃批次
│       ├── links.md             # 本批次的完整链接列表（Markdown 无序列表）
│       └── metadata.json        # 批次元信息：导入日期、条目数、来源说明
│
├── scripts/                     # 辅助工具脚本目录
│   ├── check-links.sh           # 链接状态检查脚本，基于 curl 批量探测 HTTP 状态码
│   ├── generate-index.js        # 根据 resources 目录生成总索引页面的 Node 脚本
│   └── extract-titles.py        # 可选 Python 脚本，批量拉取页面标题与描述
│
├── docs/                        # 详细文档目录
│   ├── quick-start.md           # 快速上手教程，含详细截图与常见问题排查
│   ├── maintenance.md           # 维护指南，含链接去重、失效处理与批次管理
│   ├── architecture.md          # 架构设计说明，含静态生成方案与扩展接口设计
│   └── contributing.md          # 贡献者指南，含 Commit 消息规范与 PR 流程
│
├── output/                      # 静态站点生成输出目录（默认不纳入版本控制）
│   ├── index.html               # 由 generate-index.js 生成的入口页面
│   └── resources/               # 资源页面的 HTML 渲染版本
│
└── tests/                       # 单元测试与集成测试目录
    ├── link-format.test.js      # 测试链接格式是否符合原始保留规则
    └── batch-metadata.test.js   # 校验批次元数据文件的完整性与字段类型
```

## 贡献指南

本项目的核心资产为外部链接的索引清单，所有贡献均需遵循以下流程以确保索引的一致性与可审计性。

第一，Fork 本仓库至个人账号，并在本地克隆 Fork 后的副本。所有修改应在独立的功能分支上进行，分支命名格式建议为 `batch-update/描述` 或 `fix/描述`。

第二，在 `resources/batch_062/links.md` 文件中按现有格式追加或删除 URL 条目。新增条目需确保为原始未改写形式，删除条目需在提交信息中注明移除原因。

第三，运行链接格式校验脚本 `npm run validate` 以确认所有 URL 均未发生协议补全或域名改写。若校验失败，需根据输出提示修正后重新提交。

第四，提交变更时使用语义化的 Commit 信息，格式为 `type(scope): subject`。例如 `feat(resources): add 50 new links to batch_062` 或 `fix(links): remove duplicate entry for batch_061`。

第五，向主仓库发起 Pull Request，并在描述中明确说明本次变更的条目数量、操作类型（新增/删除/修改）以及是否有特殊处理事项。审核通过后由维护者合并。

## 常见问题

问：为什么所有外部链接都必须以原始格式保存，不能补全协议或域名？

答：本项目定位为纯索引层，不承担内容改写或重定向服务的职能。保留原始格式可以确保第三方审计工具、爬虫程序以及人工审核人员能够准确还原用户提交时的完整路径，避免因规范化引入的隐含信息丢失或误判。同时，原始格式保留也符合数据溯源的基本原则，便于在链接失效时快速定位问题环节。

问：如何批量检查资源列表中是否存在失效链接？

答：项目提供了 `scripts/check-links.sh` 脚本，该脚本基于 curl 并发探测每个 URL 的 HTTP 响应状态码。执行 `bash scripts/check-links.sh resources/batch_062/links.md` 即可输出状态报表，包含 2xx 成功、3xx 重定向、4xx 客户端错误以及 5xx 服务端错误的分类统计。建议每周运行一次并将结果提交至批次元数据中作为健康度记录。

问：我能否在本地修改已经收录的链接格式，例如将 http 改为 https？

答：不可以。根据本项目的核心规则，所有链接必须以用户提交时的原始形态永久留存。任何对协议、域名、端口、路径或查询参数的修改均视为破坏索引完整性的行为，此类 Pull Request 将被直接拒绝。若源站已支持 HTTPS，用户应在其提交的原始链接中自行体现，维护者不做主动升级。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
