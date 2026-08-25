# LinkStack 技术资源导航

LinkStack 是一个面向开发者、技术研究人员与运维工程师的轻量级技术资源外链汇总平台。该项目旨在解决技术文档分散、优质教程难以检索、社区讨论缺乏统一入口等问题，通过结构化组织外部 URL，帮助技术团队快速定位所需信息。LinkStack 适用于搭建内部技术知识库的补充索引、开源项目文档的外部引用清单，或作为个人技术收藏夹的公共展示层。

## 功能概览

- **批量外链导入与去重**：支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动检测并移除重复条目，保留原始来源标记。

- **多级分类与标签系统**：每个外链可归属一个主分类并附加多个标签，分类支持无限层级嵌套，便于按技术领域、语言、项目阶段等维度组织资源。

- **全文检索与过滤**：基于标题、描述、标签、来源域名进行关键词检索，支持按分类、添加时间、访问频次等条件过滤排序。

- **链接可用性健康检查**：后台定时任务对已收录链接发起 HEAD 请求，检测 HTTP 状态码，标记失效或重定向链接，支持导出异常报告。

- **访问统计与热度排行**：记录每个外链的点击次数与最后访问时间，自动生成近 7 日、30 日热门资源排行榜，辅助团队发现高频使用内容。

- **Markdown 备注与版本记录**：每个链接可附加 Markdown 格式的备注说明，记录使用心得、注意事项或补充上下文；修改历史自动保存，支持回滚。

- **RESTful API 与数据导出**：提供只读 API 接口，支持按分类或标签获取链接列表，数据可导出为 JSON、CSV 或 OPML 格式，便于迁移或集成到其他系统。

## 应用场景

- **团队技术文档库的外部引用管理**：开发团队在维护内部 Wiki 或 Confluence 时，可将 LinkStack 作为外部参考资料的统一来源，避免在文档中散落大量裸 URL，方便统一更新失效链接。

- **开源项目 README 的资源索引页**：开源项目维护者可以使用 LinkStack 整理社区贡献的教程、视频、插件列表，然后在项目 README 中仅放置 LinkStack 的入口地址，降低 README 篇幅并提升可维护性。

- **技术培训课程的课前阅读清单**：培训机构或企业内训讲师可预先将相关文章、官方文档、视频地址录入 LinkStack 并按课程章节分类，学员通过统一入口按序学习，减少搜索时间。

- **个人技术收藏夹的团队共享**：资深工程师可将个人积累的技术书签导入 LinkStack，添加详细备注后分享给团队成员，帮助新人快速了解推荐资源的使用场景和优先级。

- **运维监控的知识库辅助**：运维团队可将常见故障处理手册、监控面板地址、日志查询工具等外链集中管理，在故障应急时快速获取所需工具入口，减少在收藏夹或聊天记录中翻找的时间。

## 快速开始

以下步骤适用于 Linux / macOS / Windows WSL 环境，项目基于 Python 3.10 开发，使用 Flask 作为 Web 框架，SQLite 作为默认数据库。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/linkstack.git
cd linkstack

# 创建 Python 虚拟环境并激活
python3 -m venv venv
source venv/bin/activate      # Linux/macOS
# venv\Scripts\activate       # Windows

# 安装项目依赖
pip install -r requirements.txt

# 初始化数据库表结构并加载默认分类
python manage.py init-db

# 启动开发服务器，默认监听 127.0.0.1:5000
python manage.py runserver
```

访问 http://127.0.0.1:5000 即可进入 LinkStack 首页。生产环境部署请参考 `docs/deployment.md` 使用 Gunicorn + Nginx。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.10.x 或 3.11.x | 核心运行环境，低于 3.10 不兼容 f-string 调试语法 |
| pip | 22.0+ | 包管理工具，用于安装 requirements 中的依赖 |
| SQLite | 3.35+ | 默认数据库，支持 JSON 字段存储标签和扩展属性 |
| Redis | 6.0+ | 可选，用于缓存热门链接和会话存储，生产环境推荐 |
| Node.js | 16.x+ | 仅用于前端资源构建（Tailwind CSS 编译），非运行时必需 |
| Nginx | 1.20+ | 生产环境反向代理，处理静态资源缓存和负载均衡 |
| systemd | 245+ | Linux 系统服务管理，用于后台健康检查定时任务 |
| git | 2.25+ | 版本控制，用于克隆仓库和后续更新合并 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 入门指南 | `docs/quick-start.md` | 如何在一小时内完成首次部署并添加第一批链接？ |
| 配置参考 | `docs/configuration.md` | 环境变量有哪些？如何修改分类默认图标和页面标题？ |
| API 文档 | `docs/api.md` | 如何通过接口读取链接列表？认证方式是什么？ |
| 运维手册 | `docs/operations.md` | 如何备份数据库？健康检查失败如何告警？如何升级版本？ |
| 前端自定义 | `docs/frontend-theming.md` | 如何修改页面布局、替换 Logo 或调整配色方案？ |
| 数据迁移 | `docs/migration.md` | 从书签 HTML、CSV 或 JSON 导入数据的详细映射规则 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/6521838.htm
- http://m.blog.ghtkgg.cn/nnews/7701789.htm
- http://m.blog.ghtkgg.cn/nnews/8869663.htm
- http://m.blog.ghtkgg.cn/nnews/4596.htm
- http://m.blog.ghtkgg.cn/nnews/33093.htm
- http://m.blog.ghtkgg.cn/nnews/8501.htm
- http://m.blog.ghtkgg.cn/nnews/81284.htm
- http://m.blog.ghtkgg.cn/nnews/4310775.htm
- http://m.blog.ghtkgg.cn/nnews/3668.htm
- http://m.blog.ghtkgg.cn/nnews/334162.htm
- http://m.blog.ghtkgg.cn/nnews/9833344.htm
- http://m.blog.ghtkgg.cn/nnews/5653.htm
- http://m.blog.ghtkgg.cn/nnews/114128.htm
- http://m.blog.ghtkgg.cn/nnews/96026.htm
- http://m.blog.ghtkgg.cn/nnews/18228.htm
- http://m.blog.ghtkgg.cn/nnews/5509835.htm
- http://m.blog.ghtkgg.cn/nnews/3921153.htm
- http://m.blog.ghtkgg.cn/nnews/89413.htm
- http://m.blog.ghtkgg.cn/nnews/994472.htm
- http://m.blog.ghtkgg.cn/nnews/7539514.htm
- http://m.blog.ghtkgg.cn/nnews/81512.htm
- http://m.blog.ghtkgg.cn/nnews/87971.htm
- http://m.blog.ghtkgg.cn/nnews/8844753.htm
- http://m.blog.ghtkgg.cn/nnews/65604.htm
- http://m.blog.ghtkgg.cn/nnews/2217631.htm
- http://m.blog.ghtkgg.cn/nnews/16992.htm
- http://m.blog.ghtkgg.cn/nnews/4379.htm
- http://m.blog.ghtkgg.cn/nnews/7367.htm
- http://m.blog.ghtkgg.cn/nnews/432995.htm
- http://m.blog.ghtkgg.cn/nnews/54961.htm
- http://m.blog.ghtkgg.cn/nnews/6830493.htm
- http://m.blog.ghtkgg.cn/nnews/12655.htm
- http://m.blog.ghtkgg.cn/nnews/3102.htm
- http://m.blog.ghtkgg.cn/nnews/39466.htm
- http://m.blog.ghtkgg.cn/nnews/72456.htm
- http://m.blog.ghtkgg.cn/nnews/8608776.htm
- http://m.blog.ghtkgg.cn/nnews/8935.htm
- http://m.blog.ghtkgg.cn/nnews/6344059.htm
- http://m.blog.ghtkgg.cn/nnews/9243607.htm
- http://m.blog.ghtkgg.cn/nnews/468383.htm
- http://m.blog.ghtkgg.cn/nnews/91043.htm
- http://m.blog.ghtkgg.cn/nnews/23733.htm
- http://m.blog.ghtkgg.cn/nnews/6829.htm
- http://m.blog.ghtkgg.cn/nnews/3001.htm
- http://m.blog.ghtkgg.cn/nnews/08270.htm
- http://m.blog.ghtkgg.cn/nnews/9607.htm
- http://m.blog.ghtkgg.cn/nnews/4679792.htm
- http://m.blog.ghtkgg.cn/nnews/8789402.htm
- http://m.blog.ghtkgg.cn/nnews/68798.htm
- http://m.blog.ghtkgg.cn/nnews/9048429.htm
- http://m.blog.ghtkgg.cn/nnews/8582.htm
- http://m.blog.ghtkgg.cn/nnews/6178808.htm
- http://m.blog.ghtkgg.cn/nnews/22277.htm
- http://m.blog.ghtkgg.cn/nnews/47494.htm
- http://m.blog.ghtkgg.cn/nnews/55252.htm
- http://m.blog.ghtkgg.cn/nnews/48660.htm
- http://m.blog.ghtkgg.cn/nnews/135193.htm
- http://m.blog.ghtkgg.cn/nnews/793670.htm
- http://m.blog.ghtkgg.cn/nnews/5984.htm
- http://m.blog.ghtkgg.cn/nnews/6772700.htm
- http://m.blog.ghtkgg.cn/nnews/4231589.htm
- http://m.blog.ghtkgg.cn/nnews/3392.htm
- http://m.blog.ghtkgg.cn/nnews/84076.htm
- http://m.blog.ghtkgg.cn/nnews/6029040.htm
- http://m.blog.ghtkgg.cn/nnews/58248.htm
- http://m.blog.ghtkgg.cn/nnews/4530.htm
- http://m.blog.ghtkgg.cn/nnews/405916.htm
- http://m.blog.ghtkgg.cn/nnews/77967.htm
- http://m.blog.ghtkgg.cn/nnews/2567180.htm
- http://m.blog.ghtkgg.cn/nnews/3265.htm
- http://m.blog.ghtkgg.cn/nnews/061121.htm
- http://m.blog.ghtkgg.cn/nnews/4011901.htm
- http://m.blog.ghtkgg.cn/nnews/48731.htm
- http://m.blog.ghtkgg.cn/nnews/55575.htm
- http://m.blog.ghtkgg.cn/nnews/60831.htm
- http://m.blog.ghtkgg.cn/nnews/06722.htm
- http://m.blog.ghtkgg.cn/nnews/368423.htm
- http://m.blog.ghtkgg.cn/nnews/3782035.htm
- http://m.blog.ghtkgg.cn/nnews/7432.htm
- http://m.blog.ghtkgg.cn/nnews/4834669.htm
- http://m.blog.ghtkgg.cn/nnews/684660.htm
- http://m.blog.ghtkgg.cn/nnews/0587.htm
- http://m.blog.ghtkgg.cn/nnews/3767071.htm
- http://m.blog.ghtkgg.cn/nnews/224732.htm
- http://m.blog.ghtkgg.cn/nnews/6323491.htm
- http://m.blog.ghtkgg.cn/nnews/1409862.htm
- http://m.blog.ghtkgg.cn/nnews/3651801.htm
- http://m.blog.ghtkgg.cn/nnews/1021.htm
- http://m.blog.ghtkgg.cn/nnews/01131.htm
- http://m.blog.ghtkgg.cn/nnews/1288.htm
- http://m.blog.ghtkgg.cn/nnews/67342.htm
- http://m.blog.ghtkgg.cn/nnews/780707.htm
- http://m.blog.ghtkgg.cn/nnews/732276.htm
- http://m.blog.ghtkgg.cn/nnews/283123.htm
- http://m.blog.ghtkgg.cn/nnews/53887.htm
- http://m.blog.ghtkgg.cn/nnews/613225.htm
- http://m.blog.ghtkgg.cn/nnews/817392.htm
- http://m.blog.ghtkgg.cn/nnews/3854769.htm
- http://m.blog.ghtkgg.cn/nnews/4204.htm
- http://m.blog.ghtkgg.cn/nnews/6099752.htm
- http://m.blog.ghtkgg.cn/nnews/1416.htm
- http://m.blog.ghtkgg.cn/nnews/27979.htm
- http://m.blog.ghtkgg.cn/nnews/933470.htm
- http://m.blog.ghtkgg.cn/nnews/4362.htm
- http://m.blog.ghtkgg.cn/nnews/888896.htm
- http://m.blog.ghtkgg.cn/nnews/3634413.htm
- http://m.blog.ghtkgg.cn/nnews/7823.htm
- http://m.blog.ghtkgg.cn/nnews/465519.htm
- http://m.blog.ghtkgg.cn/nnews/747332.htm
- http://m.blog.ghtkgg.cn/nnews/572457.htm
- http://m.blog.ghtkgg.cn/nnews/2289.htm
- http://m.blog.ghtkgg.cn/nnews/16816.htm
- http://m.blog.ghtkgg.cn/nnews/6287322.htm
- http://m.blog.ghtkgg.cn/nnews/465894.htm
- http://m.blog.ghtkgg.cn/nnews/47247.htm
- http://m.blog.ghtkgg.cn/nnews/1543.htm
- http://m.blog.ghtkgg.cn/nnews/1007.htm
- http://m.blog.ghtkgg.cn/nnews/550966.htm
- http://m.blog.ghtkgg.cn/nnews/7075536.htm
- http://m.blog.ghtkgg.cn/nnews/1519.htm
- http://m.blog.ghtkgg.cn/nnews/866019.htm
- http://m.blog.ghtkgg.cn/nnews/694567.htm
- http://m.blog.ghtkgg.cn/nnews/2950.htm
- http://m.blog.ghtkgg.cn/nnews/79512.htm
- http://m.blog.ghtkgg.cn/nnews/2693.htm
- http://m.blog.ghtkgg.cn/nnews/0047997.htm
- http://m.blog.ghtkgg.cn/nnews/60798.htm
- http://m.blog.ghtkgg.cn/nnews/67484.htm
- http://m.blog.ghtkgg.cn/nnews/2305228.htm
- http://m.blog.ghtkgg.cn/nnews/6964138.htm
- http://m.blog.ghtkgg.cn/nnews/0854.htm
- http://m.blog.ghtkgg.cn/nnews/59210.htm
- http://m.blog.ghtkgg.cn/nnews/652696.htm
- http://m.blog.ghtkgg.cn/nnews/9220.htm
- http://m.blog.ghtkgg.cn/nnews/04212.htm
- http://m.blog.ghtkgg.cn/nnews/69881.htm
- http://m.blog.ghtkgg.cn/nnews/159605.htm
- http://m.blog.ghtkgg.cn/nnews/6740.htm
- http://m.blog.ghtkgg.cn/nnews/801333.htm
- http://m.blog.ghtkgg.cn/nnews/3701.htm
- http://m.blog.ghtkgg.cn/nnews/2215.htm
- http://m.blog.ghtkgg.cn/nnews/4089081.htm
- http://m.blog.ghtkgg.cn/nnews/1997476.htm
- http://m.blog.ghtkgg.cn/nnews/7122.htm
- http://m.blog.ghtkgg.cn/nnews/75239.htm
- http://m.blog.ghtkgg.cn/nnews/889788.htm
- http://m.blog.ghtkgg.cn/nnews/85932.htm
- http://m.blog.ghtkgg.cn/nnews/7666.htm
- http://m.blog.ghtkgg.cn/nnews/430788.htm
- http://m.blog.ghtkgg.cn/nnews/89180.htm
- http://m.blog.ghtkgg.cn/nnews/35575.htm
- http://m.blog.ghtkgg.cn/nnews/4935643.htm
- http://m.blog.ghtkgg.cn/nnews/833094.htm
- http://m.blog.ghtkgg.cn/nnews/460548.htm
- http://m.blog.ghtkgg.cn/nnews/972617.htm
- http://m.blog.ghtkgg.cn/nnews/7903.htm
- http://m.blog.ghtkgg.cn/nnews/1196.htm
- http://m.blog.ghtkgg.cn/nnews/17109.htm
- http://m.blog.ghtkgg.cn/nnews/0819477.htm
- http://m.blog.ghtkgg.cn/nnews/1515.htm
- http://m.blog.ghtkgg.cn/nnews/804621.htm
- http://m.blog.ghtkgg.cn/nnews/521987.htm
- http://m.blog.ghtkgg.cn/nnews/2044.htm
- http://m.blog.ghtkgg.cn/nnews/6559437.htm
- http://m.blog.ghtkgg.cn/nnews/0316883.htm
- http://m.blog.ghtkgg.cn/nnews/95696.htm
- http://m.blog.ghtkgg.cn/nnews/758744.htm
- http://m.blog.ghtkgg.cn/nnews/42733.htm
- http://m.blog.ghtkgg.cn/nnews/309894.htm
- http://m.blog.ghtkgg.cn/nnews/13026.htm
- http://m.blog.ghtkgg.cn/nnews/14537.htm
- http://m.blog.ghtkgg.cn/nnews/4237658.htm
- http://m.blog.ghtkgg.cn/nnews/4441311.htm
- http://m.blog.ghtkgg.cn/nnews/3053.htm
- http://m.blog.ghtkgg.cn/nnews/868822.htm
- http://m.blog.ghtkgg.cn/nnews/6004615.htm
- http://m.blog.ghtkgg.cn/nnews/5306.htm
- http://m.blog.ghtkgg.cn/nnews/6326.htm
- http://m.blog.ghtkgg.cn/nnews/1636447.htm
- http://m.blog.ghtkgg.cn/nnews/3287752.htm
- http://m.blog.ghtkgg.cn/nnews/30100.htm
- http://m.blog.ghtkgg.cn/nnews/2531.htm
- http://m.blog.ghtkgg.cn/nnews/7047384.htm
- http://m.blog.ghtkgg.cn/nnews/5744.htm
- http://m.blog.ghtkgg.cn/nnews/141089.htm
- http://m.blog.ghtkgg.cn/nnews/33168.htm
- http://m.blog.ghtkgg.cn/nnews/022794.htm
- http://m.blog.ghtkgg.cn/nnews/924088.htm
- http://m.blog.ghtkgg.cn/nnews/4699.htm
- http://m.blog.ghtkgg.cn/nnews/3137.htm
- http://m.blog.ghtkgg.cn/nnews/071627.htm
- http://m.blog.ghtkgg.cn/nnews/9915.htm
- http://m.blog.ghtkgg.cn/nnews/663162.htm
- http://m.blog.ghtkgg.cn/nnews/7062949.htm
- http://m.blog.ghtkgg.cn/nnews/4857.htm
- http://m.blog.ghtkgg.cn/nnews/35299.htm
- http://m.blog.ghtkgg.cn/nnews/1433397.htm
- http://m.blog.ghtkgg.cn/nnews/3152.htm
- http://m.blog.ghtkgg.cn/nnews/3998.htm
- http://m.blog.ghtkgg.cn/nnews/831263.htm
- http://m.blog.ghtkgg.cn/nnews/845735.htm
- http://m.blog.ghtkgg.cn/nnews/91473.htm
- http://m.blog.ghtkgg.cn/nnews/84559.htm
- http://m.blog.ghtkgg.cn/nnews/0988.htm
- http://m.blog.ghtkgg.cn/nnews/2045.htm
- http://m.blog.ghtkgg.cn/nnews/4606250.htm
- http://m.blog.ghtkgg.cn/nnews/452616.htm
- http://m.blog.ghtkgg.cn/nnews/6121364.htm
- http://m.blog.ghtkgg.cn/nnews/0029195.htm
- http://m.blog.ghtkgg.cn/nnews/9012032.htm
- http://m.blog.ghtkgg.cn/nnews/1006760.htm
- http://m.blog.ghtkgg.cn/nnews/64597.htm
- http://m.blog.ghtkgg.cn/nnews/133830.htm
- http://m.blog.ghtkgg.cn/nnews/9295613.htm
- http://m.blog.ghtkgg.cn/nnews/389003.htm
- http://m.blog.ghtkgg.cn/nnews/4816.htm
- http://m.blog.ghtkgg.cn/nnews/1061.htm
- http://m.blog.ghtkgg.cn/nnews/8666264.htm
- http://m.blog.ghtkgg.cn/nnews/85078.htm
- http://m.blog.ghtkgg.cn/nnews/5598626.htm
- http://m.blog.ghtkgg.cn/nnews/1389.htm
- http://m.blog.ghtkgg.cn/nnews/05727.htm
- http://m.blog.ghtkgg.cn/nnews/149367.htm
- http://m.blog.ghtkgg.cn/nnews/1540237.htm
- http://m.blog.ghtkgg.cn/nnews/4457.htm
- http://m.blog.ghtkgg.cn/nnews/49995.htm
- http://m.blog.ghtkgg.cn/nnews/26177.htm
- http://m.blog.ghtkgg.cn/nnews/9225.htm
- http://m.blog.ghtkgg.cn/nnews/6306.htm
- http://m.blog.ghtkgg.cn/nnews/617879.htm
- http://m.blog.ghtkgg.cn/nnews/23099.htm
- http://m.blog.ghtkgg.cn/nnews/0290.htm
- http://m.blog.ghtkgg.cn/nnews/2433082.htm
- http://m.blog.ghtkgg.cn/nnews/9980528.htm
- http://m.blog.ghtkgg.cn/nnews/7038.htm
- http://m.blog.ghtkgg.cn/nnews/52664.htm
- http://m.blog.ghtkgg.cn/nnews/285744.htm
- http://m.blog.ghtkgg.cn/nnews/0055633.htm
- http://m.blog.ghtkgg.cn/nnews/4254763.htm
- http://m.blog.ghtkgg.cn/nnews/34050.htm
- http://m.blog.ghtkgg.cn/nnews/697788.htm
- http://m.blog.ghtkgg.cn/nnews/0919.htm
- http://m.blog.ghtkgg.cn/nnews/239427.htm
- http://m.blog.ghtkgg.cn/nnews/044702.htm
- http://m.blog.ghtkgg.cn/nnews/783729.htm
- http://m.blog.ghtkgg.cn/nnews/88998.htm
- http://m.blog.ghtkgg.cn/nnews/781260.htm
- http://m.blog.ghtkgg.cn/nnews/2778699.htm
- http://m.blog.ghtkgg.cn/nnews/0273312.htm
- http://m.blog.ghtkgg.cn/nnews/7924.htm
- http://m.blog.ghtkgg.cn/nnews/176003.htm
- http://m.blog.ghtkgg.cn/nnews/6715.htm
- http://m.blog.ghtkgg.cn/nnews/438986.htm
- http://m.blog.ghtkgg.cn/nnews/195026.htm
- http://m.blog.ghtkgg.cn/nnews/58699.htm
- http://m.blog.ghtkgg.cn/nnews/0601554.htm
- http://m.blog.ghtkgg.cn/nnews/7612.htm
- http://m.blog.ghtkgg.cn/nnews/4105446.htm
- http://m.blog.ghtkgg.cn/nnews/920890.htm
- http://m.blog.ghtkgg.cn/nnews/7449.htm
- http://m.blog.ghtkgg.cn/nnews/817827.htm
- http://m.blog.ghtkgg.cn/nnews/65023.htm
- http://m.blog.ghtkgg.cn/nnews/181945.htm
- http://m.blog.ghtkgg.cn/nnews/78451.htm
- http://m.blog.ghtkgg.cn/nnews/2187645.htm
- http://m.blog.ghtkgg.cn/nnews/670729.htm
- http://m.blog.ghtkgg.cn/nnews/09323.htm
- http://m.blog.ghtkgg.cn/nnews/4764.htm
- http://m.blog.ghtkgg.cn/nnews/8567.htm
- http://m.blog.ghtkgg.cn/nnews/8106.htm
- http://m.blog.ghtkgg.cn/nnews/0767252.htm
- http://m.blog.ghtkgg.cn/nnews/363602.htm
- http://m.blog.ghtkgg.cn/nnews/555598.htm
- http://m.blog.ghtkgg.cn/nnews/569586.htm
- http://m.blog.ghtkgg.cn/nnews/55946.htm
- http://m.blog.ghtkgg.cn/nnews/1175.htm
- http://m.blog.ghtkgg.cn/nnews/5729326.htm
- http://m.blog.ghtkgg.cn/nnews/3199618.htm
- http://m.blog.ghtkgg.cn/nnews/93168.htm
- http://m.blog.ghtkgg.cn/nnews/851560.htm
- http://m.blog.ghtkgg.cn/nnews/92604.htm
- http://m.blog.ghtkgg.cn/nnews/206051.htm
- http://m.blog.ghtkgg.cn/nnews/139843.htm
- http://m.blog.ghtkgg.cn/nnews/58480.htm
- http://m.blog.ghtkgg.cn/nnews/402625.htm
- http://m.blog.ghtkgg.cn/nnews/3830019.htm
- http://m.blog.ghtkgg.cn/nnews/7439.htm
- http://m.blog.ghtkgg.cn/nnews/739024.htm
- http://m.blog.ghtkgg.cn/nnews/157932.htm
- http://m.blog.ghtkgg.cn/nnews/55728.htm
- http://m.blog.ghtkgg.cn/nnews/8088.htm
- http://m.blog.ghtkgg.cn/nnews/929266.htm
- http://m.blog.ghtkgg.cn/nnews/2122573.htm
- http://m.blog.ghtkgg.cn/nnews/979606.htm
- http://m.blog.ghtkgg.cn/nnews/038318.htm
- http://m.blog.ghtkgg.cn/nnews/3173.htm
- http://m.blog.ghtkgg.cn/nnews/681141.htm
- http://m.blog.ghtkgg.cn/nnews/28457.htm
- http://m.blog.ghtkgg.cn/nnews/6727928.htm
- http://m.blog.ghtkgg.cn/nnews/81752.htm

## 项目结构

```
linkstack/
├── app/
│   ├── api/                      # RESTful API 路由与序列化
│   │   ├── routes.py             # 链接列表、分类、标签的 API 端点
│   │   └── schemas.py            # Pydantic / Marshmallow 校验模型
│   ├── models/
│   │   ├── link.py               # Link 表：标题、URL、状态码、点击量
│   │   ├── category.py           # Category 表：层级分类与排序权重
│   │   ├── tag.py                # Tag 表与 Link-Tag 多对多关联
│   │   └── health_check.py       # 健康检查记录表：检查时间、响应码、耗时
│   ├── services/
│   │   ├── importer.py           # 批量导入服务：支持 JSON / CSV / 纯文本
│   │   ├── health.py             # 后台健康检查调度器（基于 APScheduler）
│   │   └── stats.py              # 访问统计与排行计算
│   ├── templates/                # Jinja2 前端模板
│   │   ├── base.html             # 基础布局，含导航栏与页脚
│   │   ├── index.html            # 首页：分类导航 + 热门链接
│   │   └── detail.html           # 链接详情页：备注 + 访问跳转
│   └── static/                   # 编译后的 CSS / JS / 图片资源
│       ├── css/
│       ├── js/
│       └── images/
├── config/
│   ├── development.py            # 开发环境配置：SQLite + 调试模式
│   ├── production.py             # 生产环境配置：PostgreSQL / MySQL + Redis
│   └── testing.py                # 单元测试配置：内存数据库 + 禁用调度器
├── scripts/
│   ├── init_db.py                # 数据库初始化与基础分类种子数据
│   ├── import_batch.py           # 命令行批量导入工具（支持第 198/300 批次格式）
│   └── export_opml.py            # 导出为 OPML 格式，供 RSS 阅读器使用
├── tests/
│   ├── test_models.py            # 模型层单元测试
│   ├── test_api.py               # API 端点测试（pytest + 测试客户端）
│   └── test_health.py            # 健康检查服务模拟测试
├── docs/                         # 详细文档（见文档导航表格）
├── requirements.txt              # Python 依赖列表（Flask, SQLAlchemy, APScheduler）
├── manage.py                     # 统一管理入口（runserver, init-db, health-check）
├── .env.example                  # 环境变量模板（数据库连接串、SECRET_KEY）
├── .gitignore
└── README.md                     # 本文件
```

## 贡献指南

1. 在 GitHub 仓库页面点击 Fork 按钮，将项目复制到个人账号下，然后克隆到本地进行开发。建议在 dev 分支上切出特性分支，命名格式为 `feature/功能简述` 或 `fix/问题编号`。

2. 编写或修改代码时，请保持 PEP 8 编码规范，并确保新增功能包含对应的单元测试（位于 `tests/` 目录）。对于前端模板的变更，需确保在无 JavaScript 环境下页面仍可完整访问。

3. 提交前运行 `python manage.py test` 确保所有测试用例通过，同时使用 `flake8` 和 `black` 进行代码风格检查与自动格式化。提交信息请采用 `类型: 简短描述` 的格式，例如 `feat: 增加按域名过滤链接的 API 参数`。

4. 推送到个人远程仓库后，通过 GitHub 界面发起 Pull Request 到主仓库的 `main` 分支。PR 描述中请说明变更动机、影响范围以及是否涉及数据库迁移。核心维护者会在 3 个工作日内进行 Review。

5. 若发现资源列表中的失效链接或希望推荐新的技术资源，请直接在 `data/links_198.csv` 文件中按格式追加，并通过 PR 提交。项目维护者会定期合并社区提交的外链更新。

## 常见问题

**问：健康检查标记失效链接后，系统会自动删除它们吗？**

答：不会。健康检查仅将链接状态标记为 `unreachable` 并记录最后一次异常响应码，链接本身不会被自动删除。管理员可以在后台管理界面查看异常列表，手动决定保留、更新 URL 或移除。这样设计是为了避免误判（例如临时维护、网络抖动）导致的数据丢失。

**问：能否将 LinkStack 部署在无外网访问的内网环境？**

答：可以。LinkStack 本身不强制要求外网访问，所有外链资源仅供展示和跳转。但健康检查功能在内网环境中可能无法探测到公网地址的响应，建议在内网部署时禁用健康检查调度器，或仅对内部域名开启检查。另外，初始化时使用 `--offline` 参数可跳过 CDN 前端库的下载，改用本地静态文件。

**问：如何从旧版 SQLite 迁移到生产环境的 PostgreSQL？**

答：项目提供了 `scripts/migrate_db.py` 脚本，支持从 SQLite 导出完整数据（包含分类、标签、链接和访问日志）并生成 PostgreSQL 兼容的 SQL 转储文件。操作步骤为：先在目标 PostgreSQL 中创建空库，然后运行 `python scripts/migrate_db.py --source sqlite:///data.db --target postgresql://user:pass@host/db`，脚本会自动处理主键序列和 JSON 字段的转换。建议在迁移前使用 `--dry-run` 选项进行预检查。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:08
