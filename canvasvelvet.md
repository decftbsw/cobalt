# Oexnr JNews Link Aggregator

Oexnr JNews Link Aggregator 是一个面向移动端新闻资讯聚合的开源外链管理工具，专为内容聚合站点、个人资讯博主以及小型新闻编辑部设计，用于统一收集、分类和展示来自 Oexnr 新闻频道的海量外部文章链接。该项目定位为轻量级链接中台，不对新闻内容做二次编辑，仅提供高效的链接抓取、状态监控和访问重定向能力，帮助运营方快速构建基于 URL 目录结构的新闻导航页。

目标用户包括使用移动端 WAP 门户的内容管理者、需要批量导入外部新闻链接的爬虫开发者，以及希望将 Oexnr 新闻资源整合进自有系统的技术团队。项目以高可读性的 URL 列表为核心资产，通过自动化脚本检测链接可访问性，支持按新闻编号、发布时间和分类标签进行检索，有效解决手动维护数百条外链时容易出现的链接失效、分类混乱和更新延迟问题。

## 功能概览

**批量链接导入** 支持从 CSV 或纯文本列表批量导入 Oexnr 新闻 URL，自动解析文章编号和来源域名，减少人工录入错误。

**链接可用性监控** 定时对全部外链发起 HEAD 请求，检测 HTTP 状态码，标记无法访问的链接并生成异常报告。

**分类标签管理** 允许为每条链接添加多个自定义标签（如国内、国际、科技、财经），支持按标签快速筛选新闻列表。

**移动端自适应展示** 前端模板针对手机 WAP 浏览器优化，列表视图采用卡片式布局，链接点击区域适配触屏操作。

**搜索与过滤** 提供基于文章编号、关键词和日期范围的搜索接口，支持对超过 200 条链接进行实时模糊匹配。

**访问统计看板** 记录每条链接的点击次数、最后访问时间和来源 Referer，以柱状图展示热门新闻排行。

**导入导出工具** 支持将当前链接列表导出为 JSON 或 CSV 格式，方便迁移至其他新闻聚合平台或备份存档。

**配置化重定向规则** 允许管理员配置基于文章编号前缀的重定向目标地址，实现旧链接到新地址的无缝跳转。

## 应用场景

移动新闻门户的每日外链更新：内容编辑每日从 Oexnr 新闻频道获取最新文章编号，通过本项目提供的导入接口批量添加至链接列表，前端页面自动刷新展示新条目，无需手动编写 HTML 列表。

历史新闻资源的归档整理：运营人员将积累的数百条历史新闻 URL 导入系统，利用分类标签按年份和主题分组，构建可供读者回溯的新闻档案库，提升网站内容深度。

第三方资讯平台的数据桥接：开发团队将本项目的链接导出接口集成至自有 CMS 系统，定时拉取 Oexnr 新闻链接并写入本地数据库，作为外部内容源的数据补充通道。

链接健康度巡检：站点管理员设置每日凌晨的定时任务，对全部链接执行可用性检测，自动将失效链接移至待处理区，保障前端展示的链接均为有效资源。

## 快速开始

以下步骤适用于 Linux 与 macOS 环境，Windows 用户建议使用 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/your-org/oexnr-link-aggregator.git

# 进入项目根目录
cd oexnr-link-aggregator

# 安装依赖（基于 Node.js 22 LTS）
npm install

# 复制环境变量模板并填写配置
cp .env.example .env

# 初始化 SQLite 数据库表结构
npm run migrate

# 导入示例链接数据（包含本批次部分 URL）
npm run seed

# 启动开发服务器，默认监听 3000 端口
npm run dev
```

访问 http://localhost:3000 即可查看链接列表页面。生产环境部署请使用 `npm run build` 构建静态资源，并通过 `pm2 start ecosystem.config.js` 启动守护进程。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Node.js | 22.x LTS 或更高 | 运行时环境，推荐使用 nvm 管理版本 |
| npm | 10.x 或更高 | 包管理器，随 Node.js 一同安装 |
| SQLite3 | 3.40.0 或更高 | 嵌入式数据库，用于存储链接元数据和访问日志 |
| PM2 | 5.3.0 或更高 | 生产环境进程守护工具（仅部署时需要） |
| Nginx | 1.24.0 或更高 | 反向代理服务器，用于承载静态资源和负载均衡（可选） |
| Git | 2.30.0 或更高 | 版本控制工具，用于克隆仓库和拉取更新 |
| curl | 7.68.0 或更高 | 用于链接可用性检测的底层 HTTP 客户端 |
| jq | 1.6 或更高 | 命令行 JSON 处理器，用于脚本输出格式化（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 入门指南 | docs/getting-started.md | 如何快速启动项目并加载第一批新闻链接？初始配置需要注意哪些参数？ |
| 链接管理 | docs/link-management.md | 如何批量导入 URL、编辑标签和删除失效链接？支持哪些导入格式？ |
| API 参考 | docs/api-reference.md | 后端提供了哪些 RESTful 接口？请求参数和响应结构是怎样的？ |
| 部署运维 | docs/deployment.md | 如何将项目部署到生产服务器？如何配置 Nginx 反向代理和 SSL 证书？ |
| 监控告警 | docs/monitoring.md | 如何配置链接健康度检查的阈值和告警通知？日志文件存放在哪里？ |
| 数据迁移 | docs/migration.md | 如何将现有链接数据从其他系统迁移至本项目？导出备份的步骤是什么？ |

## 资源列表

- http://m.wap.oexnr.cn/jnews/0208547.htm
- http://m.wap.oexnr.cn/jnews/89374.htm
- http://m.wap.oexnr.cn/jnews/29115.htm
- http://m.wap.oexnr.cn/jnews/9403831.htm
- http://m.wap.oexnr.cn/jnews/72874.htm
- http://m.wap.oexnr.cn/jnews/140774.htm
- http://m.wap.oexnr.cn/jnews/1571029.htm
- http://m.wap.oexnr.cn/jnews/53566.htm
- http://m.wap.oexnr.cn/jnews/129930.htm
- http://m.wap.oexnr.cn/jnews/0086.htm
- http://m.wap.oexnr.cn/jnews/004973.htm
- http://m.wap.oexnr.cn/jnews/01257.htm
- http://m.wap.oexnr.cn/jnews/4167435.htm
- http://m.wap.oexnr.cn/jnews/3238.htm
- http://m.wap.oexnr.cn/jnews/918847.htm
- http://m.wap.oexnr.cn/jnews/90312.htm
- http://m.wap.oexnr.cn/jnews/0373399.htm
- http://m.wap.oexnr.cn/jnews/362820.htm
- http://m.wap.oexnr.cn/jnews/410671.htm
- http://m.wap.oexnr.cn/jnews/591732.htm
- http://m.wap.oexnr.cn/jnews/64708.htm
- http://m.wap.oexnr.cn/jnews/8686866.htm
- http://m.wap.oexnr.cn/jnews/2176296.htm
- http://m.wap.oexnr.cn/jnews/3356.htm
- http://m.wap.oexnr.cn/jnews/22514.htm
- http://m.wap.oexnr.cn/jnews/36244.htm
- http://m.wap.oexnr.cn/jnews/138894.htm
- http://m.wap.oexnr.cn/jnews/601967.htm
- http://m.wap.oexnr.cn/jnews/1553.htm
- http://m.wap.oexnr.cn/jnews/7501.htm
- http://m.wap.oexnr.cn/jnews/7972925.htm
- http://m.wap.oexnr.cn/jnews/3000930.htm
- http://m.wap.oexnr.cn/jnews/3708942.htm
- http://m.wap.oexnr.cn/jnews/579215.htm
- http://m.wap.oexnr.cn/jnews/4753.htm
- http://m.wap.oexnr.cn/jnews/1570.htm
- http://m.wap.oexnr.cn/jnews/969822.htm
- http://m.wap.oexnr.cn/jnews/071449.htm
- http://m.wap.oexnr.cn/jnews/0665.htm
- http://m.wap.oexnr.cn/jnews/519911.htm
- http://m.wap.oexnr.cn/jnews/76721.htm
- http://m.wap.oexnr.cn/jnews/3711.htm
- http://m.wap.oexnr.cn/jnews/8844887.htm
- http://m.wap.oexnr.cn/jnews/1202.htm
- http://m.wap.oexnr.cn/jnews/6035314.htm
- http://m.wap.oexnr.cn/jnews/5241.htm
- http://m.wap.oexnr.cn/jnews/43521.htm
- http://m.wap.oexnr.cn/jnews/49944.htm
- http://m.wap.oexnr.cn/jnews/17970.htm
- http://m.wap.oexnr.cn/jnews/6868.htm
- http://m.wap.oexnr.cn/jnews/479031.htm
- http://m.wap.oexnr.cn/jnews/740540.htm
- http://m.wap.oexnr.cn/jnews/674345.htm
- http://m.wap.oexnr.cn/jnews/0084.htm
- http://m.wap.oexnr.cn/jnews/1823.htm
- http://m.wap.oexnr.cn/jnews/8841.htm
- http://m.wap.oexnr.cn/jnews/1833364.htm
- http://m.wap.oexnr.cn/jnews/641390.htm
- http://m.wap.oexnr.cn/jnews/018677.htm
- http://m.wap.oexnr.cn/jnews/76465.htm
- http://m.wap.oexnr.cn/jnews/64940.htm
- http://m.wap.oexnr.cn/jnews/751915.htm
- http://m.wap.oexnr.cn/jnews/5550101.htm
- http://m.wap.oexnr.cn/jnews/5022335.htm
- http://m.wap.oexnr.cn/jnews/0402.htm
- http://m.wap.oexnr.cn/jnews/98443.htm
- http://m.wap.oexnr.cn/jnews/86538.htm
- http://m.wap.oexnr.cn/jnews/708268.htm
- http://m.wap.oexnr.cn/jnews/53093.htm
- http://m.wap.oexnr.cn/jnews/2718.htm
- http://m.wap.oexnr.cn/jnews/73511.htm
- http://m.wap.oexnr.cn/jnews/2602.htm
- http://m.wap.oexnr.cn/jnews/9528.htm
- http://m.wap.oexnr.cn/jnews/926815.htm
- http://m.wap.oexnr.cn/jnews/587654.htm
- http://m.wap.oexnr.cn/jnews/4134.htm
- http://m.wap.oexnr.cn/jnews/10519.htm
- http://m.wap.oexnr.cn/jnews/7678.htm
- http://m.wap.oexnr.cn/jnews/3244.htm
- http://m.wap.oexnr.cn/jnews/60964.htm
- http://m.wap.oexnr.cn/jnews/955879.htm
- http://m.wap.oexnr.cn/jnews/45964.htm
- http://m.wap.oexnr.cn/jnews/95309.htm
- http://m.wap.oexnr.cn/jnews/608182.htm
- http://m.wap.oexnr.cn/jnews/839616.htm
- http://m.wap.oexnr.cn/jnews/7470551.htm
- http://m.wap.oexnr.cn/jnews/1253.htm
- http://m.wap.oexnr.cn/jnews/9956191.htm
- http://m.wap.oexnr.cn/jnews/2055.htm
- http://m.wap.oexnr.cn/jnews/48894.htm
- http://m.wap.oexnr.cn/jnews/833980.htm
- http://m.wap.oexnr.cn/jnews/547260.htm
- http://m.wap.oexnr.cn/jnews/5939183.htm
- http://m.wap.oexnr.cn/jnews/7487.htm
- http://m.wap.oexnr.cn/jnews/69872.htm
- http://m.wap.oexnr.cn/jnews/48465.htm
- http://m.wap.oexnr.cn/jnews/0031.htm
- http://m.wap.oexnr.cn/jnews/4890965.htm
- http://m.wap.oexnr.cn/jnews/056544.htm
- http://m.wap.oexnr.cn/jnews/0206.htm
- http://m.wap.oexnr.cn/jnews/5366.htm
- http://m.wap.oexnr.cn/jnews/8994144.htm
- http://m.wap.oexnr.cn/jnews/4471710.htm
- http://m.wap.oexnr.cn/jnews/72644.htm
- http://m.wap.oexnr.cn/jnews/697013.htm
- http://m.wap.oexnr.cn/jnews/35381.htm
- http://m.wap.oexnr.cn/jnews/86425.htm
- http://m.wap.oexnr.cn/jnews/3982566.htm
- http://m.wap.oexnr.cn/jnews/2576958.htm
- http://m.wap.oexnr.cn/jnews/2026.htm
- http://m.wap.oexnr.cn/jnews/77204.htm
- http://m.wap.oexnr.cn/jnews/7251.htm
- http://m.wap.oexnr.cn/jnews/2846273.htm
- http://m.wap.oexnr.cn/jnews/70522.htm
- http://m.wap.oexnr.cn/jnews/409941.htm
- http://m.wap.oexnr.cn/jnews/371245.htm
- http://m.wap.oexnr.cn/jnews/7500959.htm
- http://m.wap.oexnr.cn/jnews/1192252.htm
- http://m.wap.oexnr.cn/jnews/458073.htm
- http://m.wap.oexnr.cn/jnews/0290.htm
- http://m.wap.oexnr.cn/jnews/300676.htm
- http://m.wap.oexnr.cn/jnews/1202935.htm
- http://m.wap.oexnr.cn/jnews/39399.htm
- http://m.wap.oexnr.cn/jnews/6953.htm
- http://m.wap.oexnr.cn/jnews/9913022.htm
- http://m.wap.oexnr.cn/jnews/77770.htm
- http://m.wap.oexnr.cn/jnews/03833.htm
- http://m.wap.oexnr.cn/jnews/9877.htm
- http://m.wap.oexnr.cn/jnews/7848.htm
- http://m.wap.oexnr.cn/jnews/3638645.htm
- http://m.wap.oexnr.cn/jnews/2623.htm
- http://m.wap.oexnr.cn/jnews/92247.htm
- http://m.wap.oexnr.cn/jnews/5865.htm
- http://m.wap.oexnr.cn/jnews/0353148.htm
- http://m.wap.oexnr.cn/jnews/2998.htm
- http://m.wap.oexnr.cn/jnews/76892.htm
- http://m.wap.oexnr.cn/jnews/1073228.htm
- http://m.wap.oexnr.cn/jnews/728066.htm
- http://m.wap.oexnr.cn/jnews/212559.htm
- http://m.wap.oexnr.cn/jnews/4663.htm
- http://m.wap.oexnr.cn/jnews/881644.htm
- http://m.wap.oexnr.cn/jnews/866671.htm
- http://m.wap.oexnr.cn/jnews/4868573.htm
- http://m.wap.oexnr.cn/jnews/1226843.htm
- http://m.wap.oexnr.cn/jnews/8720.htm
- http://m.wap.oexnr.cn/jnews/6793.htm
- http://m.wap.oexnr.cn/jnews/7164.htm
- http://m.wap.oexnr.cn/jnews/2890.htm
- http://m.wap.oexnr.cn/jnews/279709.htm
- http://m.wap.oexnr.cn/jnews/9717.htm
- http://m.wap.oexnr.cn/jnews/5242.htm
- http://m.wap.oexnr.cn/jnews/669040.htm
- http://m.wap.oexnr.cn/jnews/9365450.htm
- http://m.wap.oexnr.cn/jnews/97874.htm
- http://m.wap.oexnr.cn/jnews/736508.htm
- http://m.wap.oexnr.cn/jnews/49058.htm
- http://m.wap.oexnr.cn/jnews/506547.htm
- http://m.wap.oexnr.cn/jnews/21485.htm
- http://m.wap.oexnr.cn/jnews/388699.htm
- http://m.wap.oexnr.cn/jnews/16906.htm
- http://m.wap.oexnr.cn/jnews/4105435.htm
- http://m.wap.oexnr.cn/jnews/0869350.htm
- http://m.wap.oexnr.cn/jnews/006344.htm
- http://m.wap.oexnr.cn/jnews/34688.htm
- http://m.wap.oexnr.cn/jnews/420354.htm
- http://m.wap.oexnr.cn/jnews/041690.htm
- http://m.wap.oexnr.cn/jnews/6863130.htm
- http://m.wap.oexnr.cn/jnews/0259765.htm
- http://m.wap.oexnr.cn/jnews/8554581.htm
- http://m.wap.oexnr.cn/jnews/7984169.htm
- http://m.wap.oexnr.cn/jnews/3630.htm
- http://m.wap.oexnr.cn/jnews/10554.htm
- http://m.wap.oexnr.cn/jnews/61120.htm
- http://m.wap.oexnr.cn/jnews/6395313.htm
- http://m.wap.oexnr.cn/jnews/5248.htm
- http://m.wap.oexnr.cn/jnews/6012.htm
- http://m.wap.oexnr.cn/jnews/3937396.htm
- http://m.wap.oexnr.cn/jnews/1937335.htm
- http://m.wap.oexnr.cn/jnews/8029251.htm
- http://m.wap.oexnr.cn/jnews/236841.htm
- http://m.wap.oexnr.cn/jnews/502775.htm
- http://m.wap.oexnr.cn/jnews/5512.htm
- http://m.wap.oexnr.cn/jnews/5553540.htm
- http://m.wap.oexnr.cn/jnews/3457.htm
- http://m.wap.oexnr.cn/jnews/7494.htm
- http://m.wap.oexnr.cn/jnews/20491.htm
- http://m.wap.oexnr.cn/jnews/0306.htm
- http://m.wap.oexnr.cn/jnews/61093.htm
- http://m.wap.oexnr.cn/jnews/920331.htm
- http://m.wap.oexnr.cn/jnews/8001.htm
- http://m.wap.oexnr.cn/jnews/1875.htm
- http://m.wap.oexnr.cn/jnews/93208.htm
- http://m.wap.oexnr.cn/jnews/0935.htm
- http://m.wap.oexnr.cn/jnews/474890.htm
- http://m.wap.oexnr.cn/jnews/7704097.htm
- http://m.wap.oexnr.cn/jnews/060472.htm
- http://m.wap.oexnr.cn/jnews/601505.htm
- http://m.wap.oexnr.cn/jnews/3560858.htm
- http://m.wap.oexnr.cn/jnews/2904.htm
- http://m.wap.oexnr.cn/jnews/509114.htm
- http://m.wap.oexnr.cn/jnews/7651882.htm
- http://m.wap.oexnr.cn/jnews/4099.htm
- http://m.wap.oexnr.cn/jnews/477373.htm
- http://m.wap.oexnr.cn/jnews/184553.htm
- http://m.wap.oexnr.cn/jnews/93799.htm
- http://m.wap.oexnr.cn/jnews/9933233.htm
- http://m.wap.oexnr.cn/jnews/4515.htm
- http://m.wap.oexnr.cn/jnews/5747.htm
- http://m.wap.oexnr.cn/jnews/5449422.htm
- http://m.wap.oexnr.cn/jnews/76104.htm
- http://m.wap.oexnr.cn/jnews/7209.htm
- http://m.wap.oexnr.cn/jnews/288720.htm
- http://m.wap.oexnr.cn/jnews/175466.htm
- http://m.wap.oexnr.cn/jnews/281626.htm
- http://m.wap.oexnr.cn/jnews/68045.htm
- http://m.wap.oexnr.cn/jnews/141700.htm
- http://m.wap.oexnr.cn/jnews/0344129.htm
- http://m.wap.oexnr.cn/jnews/867716.htm
- http://m.wap.oexnr.cn/jnews/29593.htm
- http://m.wap.oexnr.cn/jnews/0626208.htm
- http://m.wap.oexnr.cn/jnews/4129.htm
- http://m.wap.oexnr.cn/jnews/840098.htm
- http://m.wap.oexnr.cn/jnews/0626134.htm
- http://m.wap.oexnr.cn/jnews/82499.htm
- http://m.wap.oexnr.cn/jnews/142868.htm
- http://m.wap.oexnr.cn/jnews/025774.htm
- http://m.wap.oexnr.cn/jnews/126716.htm
- http://m.wap.oexnr.cn/jnews/0548122.htm
- http://m.wap.oexnr.cn/jnews/07301.htm
- http://m.wap.oexnr.cn/jnews/8580.htm
- http://m.wap.oexnr.cn/jnews/61971.htm
- http://m.wap.oexnr.cn/jnews/2437564.htm
- http://m.wap.oexnr.cn/jnews/119483.htm
- http://m.wap.oexnr.cn/jnews/91304.htm
- http://m.wap.oexnr.cn/jnews/1674.htm
- http://m.wap.oexnr.cn/jnews/72559.htm
- http://m.wap.oexnr.cn/jnews/6688.htm
- http://m.wap.oexnr.cn/jnews/37933.htm
- http://m.wap.oexnr.cn/jnews/0904457.htm
- http://m.wap.oexnr.cn/jnews/72483.htm
- http://m.wap.oexnr.cn/jnews/569807.htm
- http://m.wap.oexnr.cn/jnews/574359.htm
- http://m.wap.oexnr.cn/jnews/1731.htm
- http://m.wap.oexnr.cn/jnews/8865341.htm
- http://m.wap.oexnr.cn/jnews/95951.htm
- http://m.wap.oexnr.cn/jnews/170763.htm
- http://m.wap.oexnr.cn/jnews/102407.htm
- http://m.wap.oexnr.cn/jnews/56261.htm
- http://m.wap.oexnr.cn/jnews/6566.htm
- http://m.wap.oexnr.cn/jnews/8843.htm
- http://m.wap.oexnr.cn/jnews/1562.htm
- http://m.wap.oexnr.cn/jnews/3454797.htm
- http://m.wap.oexnr.cn/jnews/90150.htm
- http://m.wap.oexnr.cn/jnews/5473376.htm
- http://m.wap.oexnr.cn/jnews/6874411.htm
- http://m.wap.oexnr.cn/jnews/1332.htm
- http://m.wap.oexnr.cn/jnews/61288.htm
- http://m.wap.oexnr.cn/jnews/1781.htm
- http://m.wap.oexnr.cn/jnews/2004.htm
- http://m.wap.oexnr.cn/jnews/6700908.htm
- http://m.wap.oexnr.cn/jnews/22481.htm
- http://m.wap.oexnr.cn/jnews/07042.htm
- http://m.wap.oexnr.cn/jnews/6590.htm
- http://m.wap.oexnr.cn/jnews/15803.htm
- http://m.wap.oexnr.cn/jnews/6724341.htm
- http://m.wap.oexnr.cn/jnews/96361.htm
- http://m.wap.oexnr.cn/jnews/4227.htm
- http://m.wap.oexnr.cn/jnews/6911.htm
- http://m.wap.oexnr.cn/jnews/27219.htm
- http://m.wap.oexnr.cn/jnews/660224.htm
- http://m.wap.oexnr.cn/jnews/443570.htm
- http://m.wap.oexnr.cn/jnews/1904.htm
- http://m.wap.oexnr.cn/jnews/48995.htm
- http://m.wap.oexnr.cn/jnews/8330127.htm
- http://m.wap.oexnr.cn/jnews/985586.htm
- http://m.wap.oexnr.cn/jnews/7555160.htm
- http://m.wap.oexnr.cn/jnews/25502.htm
- http://m.wap.oexnr.cn/jnews/7847.htm
- http://m.wap.oexnr.cn/jnews/98263.htm
- http://m.wap.oexnr.cn/jnews/7927.htm
- http://m.wap.oexnr.cn/jnews/471756.htm
- http://m.wap.oexnr.cn/jnews/7481.htm
- http://m.wap.oexnr.cn/jnews/652133.htm
- http://m.wap.oexnr.cn/jnews/16044.htm
- http://m.wap.oexnr.cn/jnews/1458445.htm
- http://m.wap.oexnr.cn/jnews/786331.htm
- http://m.wap.oexnr.cn/jnews/1390147.htm
- http://m.wap.oexnr.cn/jnews/3294.htm
- http://m.wap.oexnr.cn/jnews/5550392.htm
- http://m.wap.oexnr.cn/jnews/3897633.htm
- http://m.wap.oexnr.cn/jnews/54332.htm
- http://m.wap.oexnr.cn/jnews/0120368.htm
- http://m.wap.oexnr.cn/jnews/116811.htm
- http://m.wap.oexnr.cn/jnews/0063276.htm
- http://m.wap.oexnr.cn/jnews/302701.htm
- http://m.wap.oexnr.cn/jnews/9912780.htm
- http://m.wap.oexnr.cn/jnews/883836.htm
- http://m.wap.oexnr.cn/jnews/261768.htm
- http://m.wap.oexnr.cn/jnews/4470.htm
- http://m.wap.oexnr.cn/jnews/2485163.htm

## 项目结构

```
oexnr-link-aggregator/
├── src/
│   ├── core/
│   │   ├── linkManager.js          # 链接增删改查核心逻辑，封装所有数据库操作
│   │   ├── healthChecker.js        # 定时任务调度器，并发控制与超时重试机制
│   │   └── tagEngine.js            # 标签解析与匹配引擎，支持正则表达式规则
│   ├── routes/
│   │   ├── api.js                  # RESTful API 路由定义，包含分页与过滤参数
│   │   └── web.js                  # 服务端渲染页面路由，适配移动端模板
│   ├── models/
│   │   ├── linkModel.js            # Sequelize 链接数据模型定义
│   │   └── clickLogModel.js        # 点击日志模型，用于统计排行
│   ├── services/
│   │   ├── crawlerService.js       # 基于 puppeteer 的链接元数据抓取服务
│   │   └── exportService.js        # JSON/CSV 导出格式化与流式输出
│   └── utils/
│       ├── logger.js               # winston 日志封装，支持按日期轮转
│       └── validator.js            # URL 格式校验与文章编号提取工具
├── frontend/
│   ├── views/
│   │   ├── list.ejs                # 链接列表主页面，含分页和搜索栏
│   │   ├── detail.ejs              # 单条链接详情与访问统计展示
│   │   └── admin.ejs               # 后台管理界面，批量操作入口
│   ├── static/
│   │   ├── css/
│   │   │   └── mobile.css          # 移动优先的响应式样式表
│   │   └── js/
│   │       └── filter.js           # 前端筛选与排序交互逻辑
│   └── components/
│       ├── card.ejs                # 新闻卡片子组件，复用至多个模板
│       └── pagination.ejs          # 分页组件，支持跳转至指定页码
├── config/
│   ├── database.js                 # 数据库连接配置（SQLite 文件路径）
│   ├── schedule.js                 # 定时任务 cron 表达式与并发数配置
│   └── whitelist.js                # 允许导入的域名白名单配置
├── migrations/
│   ├── 001_init.sql                # 初始数据库表结构迁移脚本
│   └── 002_add_index.sql           # 增加文章编号和创建时间复合索引
├── scripts/
│   ├── seed.js                     # 初始化种子数据，导入本批次 URL 列表
│   ├── healthCheck.js              # 独立运行的链接健康度检测脚本
│   └── export.js                   # 命令行导出工具，支持按标签过滤
├── tests/
│   ├── unit/
│   │   └── linkManager.test.js     # 核心模块单元测试（Jest）
│   └── integration/
│       └── api.test.js             # API 接口集成测试
├── logs/                           # 运行时日志存储目录（gitignore）
├── data/                           # SQLite 数据库文件存放目录
├── .env.example                    # 环境变量配置模板
├── ecosystem.config.js             # PM2 进程管理配置文件
├── package.json                    # npm 依赖清单与脚本定义
├── Dockerfile                      # 容器化构建文件，基于 Alpine Linux
└── README.md                       # 项目说明文档（本文件）
```

## 贡献指南

1. 复刻项目仓库至个人账号，并克隆至本地开发环境。确保本地 Node.js 版本与安装要求一致，执行 `npm install` 安装全部依赖。

2. 新建功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题简述` 格式。所有代码提交需附带清晰的 commit message，说明改动原因和影响范围。

3. 在 `docs/` 目录下补充或更新相关文档，确保新功能的使用方法在文档导航中有对应条目。若新增 API 接口，需同步更新 `docs/api-reference.md`。

4. 编写单元测试覆盖新增或修改的核心逻辑，运行 `npm test` 确保全部测试用例通过。集成测试需在本地启动服务后执行。

5. 提交 Pull Request 至主仓库的 develop 分支，PR 描述中需注明关联的 Issue 编号和改动摘要。代码合并前将由项目维护者进行 Code Review。

## 常见问题

**问：导入超过 200 条链接时页面加载缓慢，如何优化列表渲染性能？**

答：前端默认采用服务端分页，每页仅加载 20 条记录。如仍感觉卡顿，可在 `config/schedule.js` 中调整 `PAGE_SIZE` 参数为 10 或 15。对于大量链接的批量操作，建议使用管理后台的异步任务队列，避免阻塞主线程。同时可启用 Nginx 的 gzip 压缩减少传输体积。

**问：链接健康度检测出现大量超时或连接拒绝，如何排查？**

答：首先检查服务器网络环境是否能够正常访问外网，部分机房可能限制出站 HTTP 请求。其次，在 `config/schedule.js` 中增加 `TIMEOUT` 配置值（单位毫秒）并调低 `CONCURRENCY` 并发数。若目标站点存在反爬机制，可在 `src/services/crawlerService.js` 中配置 User-Agent 轮换池。检测日志存放于 `logs/health-check.log`，可定位具体失败原因。

**问：如何将本项目的链接数据迁移至其他数据库如 MySQL 或 PostgreSQL？**

答：项目默认使用 SQLite 便于小型部署，但 Sequelize ORM 支持多数据库方言。修改 `config/database.js` 中的 `dialect` 参数为 `mysql` 或 `postgres`，并填写对应的连接凭证。运行 `npm run migrate` 时会根据新配置自动生成适配的建表语句。已有数据可通过 `npm run export` 导出为 JSON 文件，再通过自定义脚本导入新库。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
