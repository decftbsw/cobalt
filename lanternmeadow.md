# WebResource Aggregation Gateway

WebResource Aggregation Gateway 是一个面向技术研究者和信息分析人员的结构化外链资源归集与导航系统。项目定位于对分散在互联网各处的深层页面链接进行统一抓取、分类存储和状态监控，解决个人书签管理混乱、链接失效不可知、资源间缺乏关联关系等实际问题。目标用户包括开源社区维护者、技术调研工程师、学术文献检索人员以及任何需要系统化管理大量外链的个体工作者。

本项目不提供内容聚合或全文转载，仅作为 URL 元数据的收录、校验和导航层。通过标准化的资源清单格式、自动化的可用性探测脚本以及轻量级的静态页面生成工具，用户可快速部署属于自己的外链看板，并集成至现有知识管理流程。

## 功能概览

批量链接导入与自动规范化清洗：支持从纯文本、CSV 或简易表格中批量导入 URL，自动去除首尾空白、检测协议缺失并补充默认 HTTP 方案，同时识别重复条目并生成去重报告。

链接可达性与状态码实时探测：内置异步 HTTP 客户端，可对资源列表中的每一个 URL 执行周期性 HEAD 及 GET 请求，记录响应状态码、响应时间、重定向链及最终落地地址。

元数据智能提取与摘要生成：对可访问的 HTML 页面自动抽取标题、meta 描述、正文前 200 字符纯文本以及主要内容类型，形成资源概览卡片。

自定义标签与多级分类体系：允许用户为每个链接附加一个或多个自定义标签，并基于标签组合构建动态筛选视图，支持无限层级的目录分类映射。

资源变更追踪与历史快照对比：每次探测运行结果均存入时序数据库，支持查看单个 URL 的历史状态变化曲线，并可对比任意两次全量扫描的差异项。

静态站点生成与一键导出：根据当前资源库和标签结构，输出完整的静态 HTML 导航站，包含索引页、分类页、标签云和最近失效提醒，可直接托管至任意 Web 服务器。

RESTful API 与命令行双交互模式：提供完整的 HTTP API 用于第三方系统集成，同时保留 CLI 工具满足脚本化批量操作需求，适配自动化流水线场景。

## 应用场景

技术文档维护者利用本系统聚合项目文档中引用的所有外部参考链接，每周自动运行可用性检查，及时定位失效引用并通知相关维护人进行替换或移除。

学术研究人员在文献调研阶段将预印本仓库、数据开放平台、机构知识库等数百个候选链接导入系统，通过标签标记主题领域和重要程度，快速生成文献地图和访问热度排行。

运维工程师将系统部署在内网环境，监控企业外部依赖的 API 文档站、SDK 下载源、镜像仓库地址等关键资源的在线状态，当探测到连续失败时触发告警机器人。

内容运营团队将待审核的合作方官网、稿件来源链接统一收录至系统，利用元数据提取功能自动生成资源简介，减少人工整理时间，同时通过变更追踪关注对方站点改版动态。

个人知识管理爱好者将浏览器书签导出文件直接导入系统，获得比原生书签管理更强大的检索、过滤和状态感知能力，逐步构建长期可维护的外脑式资源网络。

## 快速开始

以下指令适用于 Linux 及 macOS 环境，Windows 用户建议通过 WSL2 或 Git Bash 执行。

```bash
# 克隆项目仓库至本地
git clone https://github.com/webresource-aggregation/gateway.git
cd gateway

# 安装 Python 依赖（推荐使用虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install --upgrade pip
pip install -r requirements.txt

# 执行初始数据迁移并创建管理员账户
python manage.py migrate
python manage.py createsuperuser

# 以开发模式启动服务
python manage.py runserver 0.0.0.0:8000
```

访问 http://localhost:8000 进入系统首页，使用创建的管理员账户登录后台开始导入链接资源。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 - 3.11 | 核心运行环境，3.12 暂未完成兼容性测试 |
| PostgreSQL | 13.0 及以上 | 主数据库，用于存储链接元数据、探测记录及标签体系 |
| Redis | 6.0 及以上 | 缓存层与任务队列 Broker，支持异步探测任务分发 |
| Node.js | 16.0 及以上 | 仅用于前端静态资源构建，运行时非必需 |
| Nginx | 1.18 及以上 | 生产环境推荐反向代理，用于静态文件服务和负载均衡 |
| systemd | 245 及以上 | Linux 发行版服务管理，用于守护进程和开机自启 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quick-start.md | 如何快速导入第一批链接、如何进行首次探测、如何查看结果面板 |
| 用户手册 | /docs/user/tagging-guide.md | 标签体系的设计原则、批量打标签的方法、动态视图的构建技巧 |
| 运维指南 | /docs/ops/deployment-prod.md | 生产环境容器化部署步骤、环境变量配置清单、日志收集策略 |
| 运维指南 | /docs/ops/monitoring-alert.md | 探测任务的调度参数调优、失效告警规则配置、钉钉/飞书机器人集成示例 |
| 开发者文档 | /docs/dev/api-reference.md | 全部 RESTful 接口的请求响应格式、鉴权方式、分页规范及错误码定义 |
| 开发者文档 | /docs/dev/contributing.md | 代码风格检查工具配置、单元测试编写规范、Pull Request 提交流程 |

## 资源列表

- http://m.blog.oexnr.cn/snews/94434.htm
- http://m.blog.oexnr.cn/snews/8862.htm
- http://m.blog.oexnr.cn/snews/7117323.htm
- http://m.blog.oexnr.cn/snews/10574.htm
- http://m.blog.oexnr.cn/snews/38737.htm
- http://m.blog.oexnr.cn/snews/427934.htm
- http://m.blog.oexnr.cn/snews/5723.htm
- http://m.blog.oexnr.cn/snews/77089.htm
- http://m.blog.oexnr.cn/snews/78472.htm
- http://m.blog.oexnr.cn/snews/30780.htm
- http://m.blog.oexnr.cn/snews/870566.htm
- http://m.blog.oexnr.cn/snews/3875.htm
- http://m.blog.oexnr.cn/snews/3347.htm
- http://m.blog.oexnr.cn/snews/183297.htm
- http://m.blog.oexnr.cn/snews/1661543.htm
- http://m.blog.oexnr.cn/snews/8412365.htm
- http://m.blog.oexnr.cn/snews/0231.htm
- http://m.blog.oexnr.cn/snews/81199.htm
- http://m.blog.oexnr.cn/snews/3345.htm
- http://m.blog.oexnr.cn/snews/609330.htm
- http://m.blog.oexnr.cn/snews/3793012.htm
- http://m.blog.oexnr.cn/snews/619380.htm
- http://m.blog.oexnr.cn/snews/334418.htm
- http://m.blog.oexnr.cn/snews/059455.htm
- http://m.blog.oexnr.cn/snews/61343.htm
- http://m.blog.oexnr.cn/snews/7629479.htm
- http://m.blog.oexnr.cn/snews/041044.htm
- http://m.blog.oexnr.cn/snews/15420.htm
- http://m.blog.oexnr.cn/snews/8211424.htm
- http://m.blog.oexnr.cn/snews/747956.htm
- http://m.blog.oexnr.cn/snews/3608.htm
- http://m.blog.oexnr.cn/snews/327439.htm
- http://m.blog.oexnr.cn/snews/39572.htm
- http://m.blog.oexnr.cn/snews/5267839.htm
- http://m.blog.oexnr.cn/snews/270817.htm
- http://m.blog.oexnr.cn/snews/05213.htm
- http://m.blog.oexnr.cn/snews/1564403.htm
- http://m.blog.oexnr.cn/snews/4258938.htm
- http://m.blog.oexnr.cn/snews/4828533.htm
- http://m.blog.oexnr.cn/snews/216335.htm
- http://m.blog.oexnr.cn/snews/554359.htm
- http://m.blog.oexnr.cn/snews/6567195.htm
- http://m.blog.oexnr.cn/snews/625859.htm
- http://m.blog.oexnr.cn/snews/9926.htm
- http://m.blog.oexnr.cn/snews/3761937.htm
- http://m.blog.oexnr.cn/snews/759208.htm
- http://m.blog.oexnr.cn/snews/977973.htm
- http://m.blog.oexnr.cn/snews/492065.htm
- http://m.blog.oexnr.cn/snews/9908710.htm
- http://m.blog.oexnr.cn/snews/155564.htm
- http://m.blog.oexnr.cn/snews/758151.htm
- http://m.blog.oexnr.cn/snews/2697.htm
- http://m.blog.oexnr.cn/snews/73638.htm
- http://m.blog.oexnr.cn/snews/55523.htm
- http://m.blog.oexnr.cn/snews/6156.htm
- http://m.blog.oexnr.cn/snews/137257.htm
- http://m.blog.oexnr.cn/snews/331815.htm
- http://m.blog.oexnr.cn/snews/1324546.htm
- http://m.blog.oexnr.cn/snews/15802.htm
- http://m.blog.oexnr.cn/snews/3471.htm
- http://m.blog.oexnr.cn/snews/274375.htm
- http://m.blog.oexnr.cn/snews/2675552.htm
- http://m.blog.oexnr.cn/snews/0935813.htm
- http://m.blog.oexnr.cn/snews/7280610.htm
- http://m.blog.oexnr.cn/snews/7873.htm
- http://m.blog.oexnr.cn/snews/9580.htm
- http://m.blog.oexnr.cn/snews/43817.htm
- http://m.blog.oexnr.cn/snews/0072.htm
- http://m.blog.oexnr.cn/snews/440944.htm
- http://m.blog.oexnr.cn/snews/75398.htm
- http://m.blog.oexnr.cn/snews/5403052.htm
- http://m.blog.oexnr.cn/snews/66582.htm
- http://m.blog.oexnr.cn/snews/2957681.htm
- http://m.blog.oexnr.cn/snews/2315092.htm
- http://m.blog.oexnr.cn/snews/8810575.htm
- http://m.blog.oexnr.cn/snews/1158733.htm
- http://m.blog.oexnr.cn/snews/7732.htm
- http://m.blog.oexnr.cn/snews/16193.htm
- http://m.blog.oexnr.cn/snews/26542.htm
- http://m.blog.oexnr.cn/snews/38448.htm
- http://m.blog.oexnr.cn/snews/2341054.htm
- http://m.blog.oexnr.cn/snews/584548.htm
- http://m.blog.oexnr.cn/snews/8138.htm
- http://m.blog.oexnr.cn/snews/1162.htm
- http://m.blog.oexnr.cn/snews/331885.htm
- http://m.blog.oexnr.cn/snews/29920.htm
- http://m.blog.oexnr.cn/snews/0702096.htm
- http://m.blog.oexnr.cn/snews/65210.htm
- http://m.blog.oexnr.cn/snews/84334.htm
- http://m.blog.oexnr.cn/snews/993092.htm
- http://m.blog.oexnr.cn/snews/956233.htm
- http://m.blog.oexnr.cn/snews/607445.htm
- http://m.blog.oexnr.cn/snews/348005.htm
- http://m.blog.oexnr.cn/snews/00097.htm
- http://m.blog.oexnr.cn/snews/636193.htm
- http://m.blog.oexnr.cn/snews/85030.htm
- http://m.blog.oexnr.cn/snews/47302.htm
- http://m.blog.oexnr.cn/snews/5097.htm
- http://m.blog.oexnr.cn/snews/791432.htm
- http://m.blog.oexnr.cn/snews/63187.htm
- http://m.blog.oexnr.cn/snews/9319.htm
- http://m.blog.oexnr.cn/snews/648169.htm
- http://m.blog.oexnr.cn/snews/4783120.htm
- http://m.blog.oexnr.cn/snews/2778294.htm
- http://m.blog.oexnr.cn/snews/61645.htm
- http://m.blog.oexnr.cn/snews/77253.htm
- http://m.blog.oexnr.cn/snews/560009.htm
- http://m.blog.oexnr.cn/snews/66373.htm
- http://m.blog.oexnr.cn/snews/1297.htm
- http://m.blog.oexnr.cn/snews/24560.htm
- http://m.blog.oexnr.cn/snews/328935.htm
- http://m.blog.oexnr.cn/snews/7201.htm
- http://m.blog.oexnr.cn/snews/40873.htm
- http://m.blog.oexnr.cn/snews/9213.htm
- http://m.blog.oexnr.cn/snews/295027.htm
- http://m.blog.oexnr.cn/snews/1592.htm
- http://m.blog.oexnr.cn/snews/2944.htm
- http://m.blog.oexnr.cn/snews/11152.htm
- http://m.blog.oexnr.cn/snews/948366.htm
- http://m.blog.oexnr.cn/snews/189290.htm
- http://m.blog.oexnr.cn/snews/15361.htm
- http://m.blog.oexnr.cn/snews/732885.htm
- http://m.blog.oexnr.cn/snews/93514.htm
- http://m.blog.oexnr.cn/snews/7701.htm
- http://m.blog.oexnr.cn/snews/282067.htm
- http://m.blog.oexnr.cn/snews/810237.htm
- http://m.blog.oexnr.cn/snews/2606.htm
- http://m.blog.oexnr.cn/snews/37293.htm
- http://m.blog.oexnr.cn/snews/6051408.htm
- http://m.blog.oexnr.cn/snews/0251152.htm
- http://m.blog.oexnr.cn/snews/124199.htm
- http://m.blog.oexnr.cn/snews/4271770.htm
- http://m.blog.oexnr.cn/snews/30682.htm
- http://m.blog.oexnr.cn/snews/03816.htm
- http://m.blog.oexnr.cn/snews/935707.htm
- http://m.blog.oexnr.cn/snews/047097.htm
- http://m.blog.oexnr.cn/snews/920230.htm
- http://m.blog.oexnr.cn/snews/801473.htm
- http://m.blog.oexnr.cn/snews/6634199.htm
- http://m.blog.oexnr.cn/snews/2635.htm
- http://m.blog.oexnr.cn/snews/42244.htm
- http://m.blog.oexnr.cn/snews/0967.htm
- http://m.blog.oexnr.cn/snews/8020449.htm
- http://m.blog.oexnr.cn/snews/6825670.htm
- http://m.blog.oexnr.cn/snews/6949345.htm
- http://m.blog.oexnr.cn/snews/003974.htm
- http://m.blog.oexnr.cn/snews/593911.htm
- http://m.blog.oexnr.cn/snews/372059.htm
- http://m.blog.oexnr.cn/snews/55511.htm
- http://m.blog.oexnr.cn/snews/8648.htm
- http://m.blog.oexnr.cn/snews/06557.htm
- http://m.blog.oexnr.cn/snews/54334.htm
- http://m.blog.oexnr.cn/snews/9229637.htm
- http://m.blog.oexnr.cn/snews/3071.htm
- http://m.blog.oexnr.cn/snews/235295.htm
- http://m.blog.oexnr.cn/snews/0485866.htm
- http://m.blog.oexnr.cn/snews/3754797.htm
- http://m.blog.oexnr.cn/snews/4226.htm
- http://m.blog.oexnr.cn/snews/6981.htm
- http://m.blog.oexnr.cn/snews/5363568.htm
- http://m.blog.oexnr.cn/snews/4144.htm
- http://m.blog.oexnr.cn/snews/2244879.htm
- http://m.blog.oexnr.cn/snews/42344.htm
- http://m.blog.oexnr.cn/snews/3196359.htm
- http://m.blog.oexnr.cn/snews/73715.htm
- http://m.blog.oexnr.cn/snews/683063.htm
- http://m.blog.oexnr.cn/snews/668271.htm
- http://m.blog.oexnr.cn/snews/88693.htm
- http://m.blog.oexnr.cn/snews/04468.htm
- http://m.blog.oexnr.cn/snews/25838.htm
- http://m.blog.oexnr.cn/snews/40824.htm
- http://m.blog.oexnr.cn/snews/1828.htm
- http://m.blog.oexnr.cn/snews/9770626.htm
- http://m.blog.oexnr.cn/snews/8304.htm
- http://m.blog.oexnr.cn/snews/3076108.htm
- http://m.blog.oexnr.cn/snews/62510.htm
- http://m.blog.oexnr.cn/snews/8960.htm
- http://m.blog.oexnr.cn/snews/993568.htm
- http://m.blog.oexnr.cn/snews/0611.htm
- http://m.blog.oexnr.cn/snews/570338.htm
- http://m.blog.oexnr.cn/snews/1939498.htm
- http://m.blog.oexnr.cn/snews/66492.htm
- http://m.blog.oexnr.cn/snews/7166530.htm
- http://m.blog.oexnr.cn/snews/4565660.htm
- http://m.blog.oexnr.cn/snews/7780.htm
- http://m.blog.oexnr.cn/snews/68264.htm
- http://m.blog.oexnr.cn/snews/212743.htm
- http://m.blog.oexnr.cn/snews/32663.htm
- http://m.blog.oexnr.cn/snews/71072.htm
- http://m.blog.oexnr.cn/snews/6155873.htm
- http://m.blog.oexnr.cn/snews/084042.htm
- http://m.blog.oexnr.cn/snews/98907.htm
- http://m.blog.oexnr.cn/snews/184048.htm
- http://m.blog.oexnr.cn/snews/9839370.htm
- http://m.blog.oexnr.cn/snews/50519.htm
- http://m.blog.oexnr.cn/snews/4191805.htm
- http://m.blog.oexnr.cn/snews/17045.htm
- http://m.blog.oexnr.cn/snews/93486.htm
- http://m.blog.oexnr.cn/snews/58447.htm
- http://m.blog.oexnr.cn/snews/11884.htm
- http://m.blog.oexnr.cn/snews/13030.htm
- http://m.blog.oexnr.cn/snews/76191.htm
- http://m.blog.oexnr.cn/snews/7600.htm
- http://m.blog.oexnr.cn/snews/6017.htm
- http://m.blog.oexnr.cn/snews/4353785.htm
- http://m.blog.oexnr.cn/snews/80401.htm
- http://m.blog.oexnr.cn/snews/500440.htm
- http://m.blog.oexnr.cn/snews/0267.htm
- http://m.blog.oexnr.cn/snews/61015.htm
- http://m.blog.oexnr.cn/snews/5235.htm
- http://m.blog.oexnr.cn/snews/53221.htm
- http://m.blog.oexnr.cn/snews/064651.htm
- http://m.blog.oexnr.cn/snews/517245.htm
- http://m.blog.oexnr.cn/snews/26596.htm
- http://m.blog.oexnr.cn/snews/15485.htm
- http://m.blog.oexnr.cn/snews/2161906.htm
- http://m.blog.oexnr.cn/snews/191084.htm
- http://m.blog.oexnr.cn/snews/0118.htm
- http://m.blog.oexnr.cn/snews/587223.htm
- http://m.blog.oexnr.cn/snews/5885849.htm
- http://m.blog.oexnr.cn/snews/1423.htm
- http://m.blog.oexnr.cn/snews/2418577.htm
- http://m.blog.oexnr.cn/snews/095971.htm
- http://m.blog.oexnr.cn/snews/9674.htm
- http://m.blog.oexnr.cn/snews/5256036.htm
- http://m.blog.oexnr.cn/snews/99033.htm
- http://m.blog.oexnr.cn/snews/65820.htm
- http://m.blog.oexnr.cn/snews/0971617.htm
- http://m.blog.oexnr.cn/snews/8215.htm
- http://m.blog.oexnr.cn/snews/3094773.htm
- http://m.blog.oexnr.cn/snews/4270960.htm
- http://m.blog.oexnr.cn/snews/047584.htm
- http://m.blog.oexnr.cn/snews/91891.htm
- http://m.blog.oexnr.cn/snews/2917153.htm
- http://m.blog.oexnr.cn/snews/2236426.htm
- http://m.blog.oexnr.cn/snews/5489367.htm
- http://m.blog.oexnr.cn/snews/9237.htm
- http://m.blog.oexnr.cn/snews/3142.htm
- http://m.blog.oexnr.cn/snews/4262.htm
- http://m.blog.oexnr.cn/snews/52841.htm
- http://m.blog.oexnr.cn/snews/138920.htm
- http://m.blog.oexnr.cn/snews/12459.htm
- http://m.blog.oexnr.cn/snews/2997116.htm
- http://m.blog.oexnr.cn/snews/8002.htm
- http://m.blog.oexnr.cn/snews/4314617.htm
- http://m.blog.oexnr.cn/snews/6217826.htm
- http://m.blog.oexnr.cn/snews/0861.htm
- http://m.blog.oexnr.cn/snews/9367.htm
- http://m.blog.oexnr.cn/snews/368124.htm
- http://m.blog.oexnr.cn/snews/5736.htm
- http://m.blog.oexnr.cn/snews/1230596.htm
- http://m.blog.oexnr.cn/snews/8407.htm
- http://m.blog.oexnr.cn/snews/406891.htm
- http://m.blog.oexnr.cn/snews/6926056.htm
- http://m.blog.oexnr.cn/snews/8101563.htm
- http://m.blog.oexnr.cn/snews/0760.htm
- http://m.blog.oexnr.cn/snews/7012981.htm
- http://m.blog.oexnr.cn/snews/8906.htm
- http://m.blog.oexnr.cn/snews/0457726.htm
- http://m.blog.oexnr.cn/snews/56286.htm
- http://m.blog.oexnr.cn/snews/3183.htm
- http://m.blog.oexnr.cn/snews/8393926.htm
- http://m.blog.oexnr.cn/snews/7397987.htm
- http://m.blog.oexnr.cn/snews/87659.htm
- http://m.blog.oexnr.cn/snews/80706.htm
- http://m.blog.oexnr.cn/snews/65725.htm
- http://m.blog.oexnr.cn/snews/3128.htm
- http://m.blog.oexnr.cn/snews/60017.htm
- http://m.blog.oexnr.cn/snews/405795.htm
- http://m.blog.oexnr.cn/snews/4742.htm
- http://m.blog.oexnr.cn/snews/548714.htm
- http://m.blog.oexnr.cn/snews/3146.htm
- http://m.blog.oexnr.cn/snews/07596.htm
- http://m.blog.oexnr.cn/snews/447881.htm
- http://m.blog.oexnr.cn/snews/0885398.htm
- http://m.blog.oexnr.cn/snews/21756.htm
- http://m.blog.oexnr.cn/snews/4039.htm
- http://m.blog.oexnr.cn/snews/7886255.htm
- http://m.blog.oexnr.cn/snews/619241.htm
- http://m.blog.oexnr.cn/snews/200001.htm
- http://m.blog.oexnr.cn/snews/7975343.htm
- http://m.blog.oexnr.cn/snews/200179.htm
- http://m.blog.oexnr.cn/snews/7565.htm
- http://m.blog.oexnr.cn/snews/2819794.htm
- http://m.blog.oexnr.cn/snews/01509.htm
- http://m.blog.oexnr.cn/snews/628224.htm
- http://m.blog.oexnr.cn/snews/7876991.htm
- http://m.blog.oexnr.cn/snews/9412090.htm
- http://m.blog.oexnr.cn/snews/543245.htm
- http://m.blog.oexnr.cn/snews/03857.htm
- http://m.blog.oexnr.cn/snews/33496.htm
- http://m.blog.oexnr.cn/snews/2886159.htm
- http://m.blog.oexnr.cn/snews/19593.htm
- http://m.blog.oexnr.cn/snews/3147421.htm
- http://m.blog.oexnr.cn/snews/84830.htm
- http://m.blog.oexnr.cn/snews/7012678.htm
- http://m.blog.oexnr.cn/snews/7767.htm
- http://m.blog.oexnr.cn/snews/0673314.htm
- http://m.blog.oexnr.cn/snews/4360367.htm
- http://m.blog.oexnr.cn/snews/3178170.htm

## 项目结构

```
gateway/
├── cmd/                                # 命令行入口与脚本工具
│   ├── server/                         # 主服务启动入口
│   │   └── main.go                     # 加载配置、初始化路由、启动 HTTP 服务
│   ├── crawler/                        # 独立探测任务调度器
│   │   └── main.go                     # 周期性拉取待测链接并执行状态检查
│   └── exporter/                       # 静态站点生成工具
│       └── main.go                     # 读取数据库输出完整 HTML 文件至指定目录
├── internal/                           # 内部核心业务逻辑，不对外暴露
│   ├── api/                            # RESTful API 处理器
│   │   ├── v1/                         # API 版本 v1 路由及控制器
│   │   │   ├── link.go                 # 链接增删改查及批量导入接口
│   │   │   ├── probe.go                # 探测结果查询与重跑触发接口
│   │   │   └── tag.go                  # 标签管理及关联关系操作接口
│   │   └── middleware/                 # 认证、限流、日志等中间件
│   ├── model/                          # 数据模型定义与 ORM 映射
│   │   ├── link.go                     # Link 结构体，包含 URL、标题、摘要、添加时间
│   │   ├── probe_record.go             # 探测记录，含状态码、响应时间、重定向链
│   │   └── tag.go                      # 标签与 Link-Tag 多对多关联表
│   ├── service/                        # 业务服务层，封装核心操作
│   │   ├── link_service.go             # 链接去重、规范化、元数据提取逻辑
│   │   ├── probe_service.go            # 并发探测调度、超时控制、结果持久化
│   │   └── export_service.go           # 模板渲染、静态资源聚合、站点地图生成
│   └── pkg/                            # 内部通用工具库
│       ├── httpclient/                 # 自定义 HTTP 客户端，含重试和代理支持
│       ├── validator/                  # URL 格式校验与协议补全工具函数
│       └── scheduler/                  # 基于 cron 表达式的任务调度封装
├── pkg/                                # 可被外部项目引用的公共库
│   ├── storage/                        # 数据库连接池与迁移管理
│   │   ├── postgres.go                 # PostgreSQL 驱动初始化及连接健康检查
│   │   └── redis.go                    # Redis 客户端初始化和缓存操作接口
│   └── logger/                         # 结构化日志组件，支持 JSON 和文本格式输出
├── web/                                # 前端静态资源及模板
│   ├── templates/                      # Go template 页面模板
│   │   ├── index.html                  # 资源总览首页，展示统计卡片和最近失效
│   │   ├── list.html                   # 链接列表页，支持筛选和排序
│   │   └── detail.html                 # 单个链接详情，含历史探测趋势图占位
│   ├── static/                         # 原始静态资源（CSS、JavaScript、图片）
│   │   ├── css/                        # 基于 Tailwind 构建的响应式样式
│   │   └── js/                         # 前端交互逻辑，包括实时搜索和图表绘制
│   └── build/                          # 前端构建产物（经 webpack 打包后的文件）
├── configs/                            # 配置文件目录
│   ├── config.yaml                     # 主配置文件，含数据库连接、探测间隔、日志级别
│   └── config.example.yaml             # 配置示例，供新用户参考
├── scripts/                            # 辅助运维与开发脚本
│   ├── init_db.sql                     # 数据库初始化 DDL 语句
│   ├── seed_test_data.py               # 生成测试数据用于开发环境调试
│   └── health_check.sh                 # 服务存活检查脚本，用于监控系统集成
├── docs/                               # 完整项目文档
│   ├── user/                           # 用户手册
│   ├── ops/                            # 运维部署文档
│   └── dev/                            # 开发者指南与 API 参考
├── test/                               # 单元测试与集成测试
│   ├── unit/                           # 各模块单元测试，覆盖 service 及 pkg
│   └── integration/                    # 端到端测试，需依赖真实数据库环境
├── go.mod                              # Go 模块依赖管理文件
├── go.sum                              # 依赖校验和文件
├── Makefile                            # 常用命令封装（编译、测试、运行、打包）
├── Dockerfile                          # 生产环境镜像构建定义
├── docker-compose.yml                  # 本地开发环境一键启动（PostgreSQL + Redis + 应用）
└── README.md                           # 项目入口文档
```

## 贡献指南

1. 复刻主仓库至个人账户下，并在本地克隆复刻版本，同时将原仓库设置为上游远程分支以保持同步更新。

2. 在 issue 列表中查找标记为 "help wanted" 或 "good first issue" 的任务，或在讨论区提出新的功能构想，等待核心维护者确认方案可行性。

3. 基于最新 main 分支创建以功能名称命名的特性分支，如 feat/add-batch-import，在该分支上完成代码编写、单元测试和本地自验证，确保所有已有测试用例均通过。

4. 提交代码时遵循约定的提交信息格式，类型包括 feat、fix、docs、refactor、perf、test、chore，正文描述修改动机、实现方式及影响范围。

5. 向主仓库的 main 分支发起 Pull Request，填写标准 PR 模板中的检查清单，包括测试覆盖说明、文档更新情况以及是否向后兼容，等待至少一位维护者进行 Code Review。

## 常见问题

Q: 系统能够处理的最大链接数量是多少？导入数千个链接时性能如何？

A: 系统设计上未对链接总数设硬上限，实际承载能力取决于部署环境的内存和数据库配置。单次批量导入支持万级记录，采用分批次提交和异步索引更新策略，避免事务阻塞。对于十万级以上的超大规模场景，建议启用 Redis 队列将导入任务异步化，并适当调整 PostgreSQL 的 work_mem 参数以优化排序和去重操作。

Q: 探测任务是否会触发目标网站的访问频率限制或导致 IP 被封？

A: 探测模块内置可配置的请求间隔控制，默认每个目标域名在 60 秒窗口内最多发送 3 次 HEAD 请求，同时支持设置全局 QPS 上限。此外，用户可在配置文件中指定代理池列表，系统自动轮换出口 IP 以降低单一来源的请求密度。对于 robots.txt 明确禁止爬取的路径，系统会尊重协议并跳过探测。

Q: 静态站点生成后，链接状态数据如何保持最新？

A: 静态站点是某一时刻的快照，不包含动态交互能力。用户可通过设置 cron 任务定期运行 exporter 命令（例如每小时执行一次），并将生成的 HTML 文件自动同步到 Web 服务器目录。若需要实时状态展示，建议直接使用系统提供的 Web 界面或通过 REST API 获取实时探测结果，而非依赖静态导出。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
