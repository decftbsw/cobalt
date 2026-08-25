# LinkVault

LinkVault 是一个面向技术内容聚合与长效外链管理的高性能资源导航系统。项目定位于为开发者、技术博主、开源社区运营者以及企业内部文档维护团队提供一套标准化的外链归集与分发工具。LinkVault 通过结构化的 URL 采集、分类标记、可用性检测与访问统计，解决技术资源链接散落、失效不可知、引用不可追溯等长期痛点。

LinkVault 并非传统的静态书签管理器，而是一个具备后台任务调度、HTTP 状态监控、标签体系与简易 API 输出的轻量级服务。项目采用模块化设计，核心数据存储基于 SQLite，支持单机部署与小型团队共享使用，适用于个人知识库、项目文档站、技术周报编辑后台等场景。

## 功能概览

**批量链接导入**：支持从纯文本列表、CSV 或简易 JSON 格式批量导入 URL，自动解析协议与路径结构。

**递归资源采集**：针对指定域名或路径前缀，支持设定深度的页面链接抓取，便于将分散的文章与文档入口统一收录。

**可用性健康检查**：内置基于 HTTP 状态码与响应时间的探测任务，支持定时轮询并标记失效或重定向链接。

**标签分类体系**：允许为每条记录附加多级标签，支持按标签组合筛选与导出，便于构建专题资源集合。

**访问热度统计**：记录每个链接的点击次数与最后访问时间，提供简单的热度排序与趋势视图。

**开放 JSON API**：提供只读查询接口与写入接口，方便与其他内部系统或自动化脚本集成。

**数据导入导出**：支持将资源列表导出为 Markdown 表格、JSON 数组或纯文本 URL 清单，满足文档生成与备份需求。

**日志审计追踪**：记录所有链接的增删改操作与探测历史，便于追溯数据变更来源。

## 应用场景

技术博客文章引用维护：技术作者可在发布文章后，将文中所有外部引用链接统一录入 LinkVault，系统定期检查链接有效性，一旦发现失效链接即生成报告，便于及时更新或替换引用源。

开源项目 README 资源汇总：开源项目维护者可将项目依赖的文档站、示例代码仓库、社区论坛等链接通过 LinkVault 统一管理，并定时导出为 Markdown 格式的资源列表直接嵌入项目文档。

团队内部知识库导航构建：企业技术团队可利用 LinkVault 汇聚内部 Wiki、API 文档、设计稿原型、CI/CD 流水线控制台等常用入口，通过标签区分不同产品线或开发阶段，形成统一的团队导航页。

技术资讯周报素材整理：技术社区编辑或运营人员可将一周内收集到的技术动态、新工具发布、优质教程等链接先行录入 LinkVault，利用标签标记分类与优先级，再批量导出为周报内容素材。

个人学习路线资源归档：开发者可将学习过程中遇到的重要参考文档、视频课程页面、开源项目仓库等链接长期归档，配合访问统计功能回顾高频查阅的资源。

## 快速开始

以下命令演示了从克隆代码到启动服务的完整流程，默认使用开发环境配置。

```bash
git clone https://github.com/linkvault/linkvault.git
cd linkvault
pip install -r requirements.txt
cp .env.example .env
python manage.py migrate
python manage.py runserver --host 0.0.0.0 --port 8080
```

完成上述步骤后，访问 http://localhost:8080 即可进入系统首页。首次启动将自动创建管理员账户，登录信息将在终端输出中显示。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 至 3.12 | 核心运行环境，3.13 暂未完全适配 |
| SQLite | 3.35 或更高 | 内置数据库，支持 WAL 模式与 JSON 扩展 |
| pip | 22.0 或更高 | Python 包管理工具，用于安装依赖项 |
| virtualenv | 20.0 或更高 | 推荐使用虚拟环境隔离项目依赖 |
| git | 2.30 或更高 | 用于克隆代码仓库与版本管理 |
| 操作系统 | Linux / macOS / Windows WSL2 | 生产环境建议使用 Linux 内核 5.0 以上 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user/quickstart.md | 如何快速导入第一批链接并执行健康检查 |
| 用户指南 | /docs/user/tagging.md | 标签体系的设计逻辑与批量打标方法 |
| 运维手册 | /docs/ops/deployment.md | 使用 systemd 或 Docker 进行生产环境部署 |
| 运维手册 | /docs/ops/scheduler.md | 后台探测任务的调度配置与调优参数 |
| 开发文档 | /docs/dev/api.md | JSON API 各端点的请求与响应格式说明 |
| 开发文档 | /docs/dev/contributing.md | 代码风格、测试流程与提交规范 |

## 资源列表

- http://m.blog.oexnr.cn/snews/678666.htm
- http://m.blog.oexnr.cn/snews/14540.htm
- http://m.blog.oexnr.cn/snews/8258189.htm
- http://m.blog.oexnr.cn/snews/5300400.htm
- http://m.blog.oexnr.cn/snews/0487.htm
- http://m.blog.oexnr.cn/snews/9760.htm
- http://m.blog.oexnr.cn/snews/0742.htm
- http://m.blog.oexnr.cn/snews/9801868.htm
- http://m.blog.oexnr.cn/snews/790867.htm
- http://m.blog.oexnr.cn/snews/6767469.htm
- http://m.blog.oexnr.cn/snews/7954.htm
- http://m.blog.oexnr.cn/snews/7119822.htm
- http://m.blog.oexnr.cn/snews/4666636.htm
- http://m.blog.oexnr.cn/snews/15152.htm
- http://m.blog.oexnr.cn/snews/50285.htm
- http://m.blog.oexnr.cn/snews/7478953.htm
- http://m.blog.oexnr.cn/snews/821161.htm
- http://m.blog.oexnr.cn/snews/725917.htm
- http://m.blog.oexnr.cn/snews/7111268.htm
- http://m.blog.oexnr.cn/snews/867487.htm
- http://m.blog.oexnr.cn/snews/4339389.htm
- http://m.blog.oexnr.cn/snews/0439.htm
- http://m.blog.oexnr.cn/snews/6314.htm
- http://m.blog.oexnr.cn/snews/4312086.htm
- http://m.blog.oexnr.cn/snews/65596.htm
- http://m.blog.oexnr.cn/snews/65888.htm
- http://m.blog.oexnr.cn/snews/88549.htm
- http://m.blog.oexnr.cn/snews/3116.htm
- http://m.blog.oexnr.cn/snews/5688467.htm
- http://m.blog.oexnr.cn/snews/99528.htm
- http://m.blog.oexnr.cn/snews/5158.htm
- http://m.blog.oexnr.cn/snews/3051.htm
- http://m.blog.oexnr.cn/snews/888943.htm
- http://m.blog.oexnr.cn/snews/252082.htm
- http://m.blog.oexnr.cn/snews/8574.htm
- http://m.blog.oexnr.cn/snews/7390.htm
- http://m.blog.oexnr.cn/snews/0537533.htm
- http://m.blog.oexnr.cn/snews/41840.htm
- http://m.blog.oexnr.cn/snews/976373.htm
- http://m.blog.oexnr.cn/snews/3845372.htm
- http://m.blog.oexnr.cn/snews/5986955.htm
- http://m.blog.oexnr.cn/snews/4461.htm
- http://m.blog.oexnr.cn/snews/23618.htm
- http://m.blog.oexnr.cn/snews/5305547.htm
- http://m.blog.oexnr.cn/snews/07091.htm
- http://m.blog.oexnr.cn/snews/46603.htm
- http://m.blog.oexnr.cn/snews/329815.htm
- http://m.blog.oexnr.cn/snews/3751.htm
- http://m.blog.oexnr.cn/snews/6710570.htm
- http://m.blog.oexnr.cn/snews/11143.htm
- http://m.blog.oexnr.cn/snews/71753.htm
- http://m.blog.oexnr.cn/snews/4812.htm
- http://m.blog.oexnr.cn/snews/030447.htm
- http://m.blog.oexnr.cn/snews/6215057.htm
- http://m.blog.oexnr.cn/snews/169663.htm
- http://m.blog.oexnr.cn/snews/366427.htm
- http://m.blog.oexnr.cn/snews/1181.htm
- http://m.blog.oexnr.cn/snews/653680.htm
- http://m.blog.oexnr.cn/snews/96579.htm
- http://m.blog.oexnr.cn/snews/65723.htm
- http://m.blog.oexnr.cn/snews/973198.htm
- http://m.blog.oexnr.cn/snews/4750.htm
- http://m.blog.oexnr.cn/snews/7848266.htm
- http://m.blog.oexnr.cn/snews/4782531.htm
- http://m.blog.oexnr.cn/snews/21097.htm
- http://m.blog.oexnr.cn/snews/7112.htm
- http://m.blog.oexnr.cn/snews/095759.htm
- http://m.blog.oexnr.cn/snews/025878.htm
- http://m.blog.oexnr.cn/snews/117405.htm
- http://m.blog.oexnr.cn/snews/47739.htm
- http://m.blog.oexnr.cn/snews/96176.htm
- http://m.blog.oexnr.cn/snews/653324.htm
- http://m.blog.oexnr.cn/snews/9303.htm
- http://m.blog.oexnr.cn/snews/04357.htm
- http://m.blog.oexnr.cn/snews/6604998.htm
- http://m.blog.oexnr.cn/snews/2060.htm
- http://m.blog.oexnr.cn/snews/505049.htm
- http://m.blog.oexnr.cn/snews/5894368.htm
- http://m.blog.oexnr.cn/snews/0275.htm
- http://m.blog.oexnr.cn/snews/36812.htm
- http://m.blog.oexnr.cn/snews/337875.htm
- http://m.blog.oexnr.cn/snews/6720380.htm
- http://m.blog.oexnr.cn/snews/33128.htm
- http://m.blog.oexnr.cn/snews/3775.htm
- http://m.blog.oexnr.cn/snews/764995.htm
- http://m.blog.oexnr.cn/snews/1666652.htm
- http://m.blog.oexnr.cn/snews/2395.htm
- http://m.blog.oexnr.cn/snews/96387.htm
- http://m.blog.oexnr.cn/snews/4445.htm
- http://m.blog.oexnr.cn/snews/4598145.htm
- http://m.blog.oexnr.cn/snews/27619.htm
- http://m.blog.oexnr.cn/snews/6391325.htm
- http://m.blog.oexnr.cn/snews/928066.htm
- http://m.blog.oexnr.cn/snews/11652.htm
- http://m.blog.oexnr.cn/snews/922422.htm
- http://m.blog.oexnr.cn/snews/7995873.htm
- http://m.blog.oexnr.cn/snews/634046.htm
- http://m.blog.oexnr.cn/snews/66786.htm
- http://m.blog.oexnr.cn/snews/1883.htm
- http://m.blog.oexnr.cn/snews/919807.htm
- http://m.blog.oexnr.cn/snews/8571.htm
- http://m.blog.oexnr.cn/snews/96052.htm
- http://m.blog.oexnr.cn/snews/74868.htm
- http://m.blog.oexnr.cn/snews/516306.htm
- http://m.blog.oexnr.cn/snews/4294.htm
- http://m.blog.oexnr.cn/snews/54677.htm
- http://m.blog.oexnr.cn/snews/478570.htm
- http://m.blog.oexnr.cn/snews/0126970.htm
- http://m.blog.oexnr.cn/snews/3537986.htm
- http://m.blog.oexnr.cn/snews/90285.htm
- http://m.blog.oexnr.cn/snews/35879.htm
- http://m.blog.oexnr.cn/snews/1375.htm
- http://m.blog.oexnr.cn/snews/9449.htm
- http://m.blog.oexnr.cn/snews/324150.htm
- http://m.blog.oexnr.cn/snews/5154328.htm
- http://m.blog.oexnr.cn/snews/73660.htm
- http://m.blog.oexnr.cn/snews/75649.htm
- http://m.blog.oexnr.cn/snews/0171086.htm
- http://m.blog.oexnr.cn/snews/455800.htm
- http://m.blog.oexnr.cn/snews/607936.htm
- http://m.blog.oexnr.cn/snews/0584.htm
- http://m.blog.oexnr.cn/snews/8191.htm
- http://m.blog.oexnr.cn/snews/3255.htm
- http://m.blog.oexnr.cn/snews/0163933.htm
- http://m.blog.oexnr.cn/snews/98141.htm
- http://m.blog.oexnr.cn/snews/6341971.htm
- http://m.blog.oexnr.cn/snews/7502060.htm
- http://m.blog.oexnr.cn/snews/6748.htm
- http://m.blog.oexnr.cn/snews/86427.htm
- http://m.blog.oexnr.cn/snews/1080.htm
- http://m.blog.oexnr.cn/snews/580116.htm
- http://m.blog.oexnr.cn/snews/023825.htm
- http://m.blog.oexnr.cn/snews/9147.htm
- http://m.blog.oexnr.cn/snews/28167.htm
- http://m.blog.oexnr.cn/snews/8644.htm
- http://m.blog.oexnr.cn/snews/379074.htm
- http://m.blog.oexnr.cn/snews/216188.htm
- http://m.blog.oexnr.cn/snews/701982.htm
- http://m.blog.oexnr.cn/snews/4186081.htm
- http://m.blog.oexnr.cn/snews/7739.htm
- http://m.blog.oexnr.cn/snews/51501.htm
- http://m.blog.oexnr.cn/snews/87631.htm
- http://m.blog.oexnr.cn/snews/8137.htm
- http://m.blog.oexnr.cn/snews/79842.htm
- http://m.blog.oexnr.cn/snews/687941.htm
- http://m.blog.oexnr.cn/snews/35023.htm
- http://m.blog.oexnr.cn/snews/894112.htm
- http://m.blog.oexnr.cn/snews/0188.htm
- http://m.blog.oexnr.cn/snews/26112.htm
- http://m.blog.oexnr.cn/snews/5521623.htm
- http://m.blog.oexnr.cn/snews/4595740.htm
- http://m.blog.oexnr.cn/snews/612241.htm
- http://m.blog.oexnr.cn/snews/8917.htm
- http://m.blog.oexnr.cn/snews/517340.htm
- http://m.blog.oexnr.cn/snews/02873.htm
- http://m.blog.oexnr.cn/snews/1746.htm
- http://m.blog.oexnr.cn/snews/512154.htm
- http://m.blog.oexnr.cn/snews/3089880.htm
- http://m.blog.oexnr.cn/snews/165536.htm
- http://m.blog.oexnr.cn/snews/9428021.htm
- http://m.blog.oexnr.cn/snews/9090.htm
- http://m.blog.oexnr.cn/snews/220205.htm
- http://m.blog.oexnr.cn/snews/6041.htm
- http://m.blog.oexnr.cn/snews/441400.htm
- http://m.blog.oexnr.cn/snews/4789.htm
- http://m.blog.oexnr.cn/snews/984245.htm
- http://m.blog.oexnr.cn/snews/893096.htm
- http://m.blog.oexnr.cn/snews/9080185.htm
- http://m.blog.oexnr.cn/snews/2409.htm
- http://m.blog.oexnr.cn/snews/1641971.htm
- http://m.blog.oexnr.cn/snews/158703.htm
- http://m.blog.oexnr.cn/snews/4239.htm
- http://m.blog.oexnr.cn/snews/7528272.htm
- http://m.blog.oexnr.cn/snews/02259.htm
- http://m.blog.oexnr.cn/snews/1226.htm
- http://m.blog.oexnr.cn/snews/8059.htm
- http://m.blog.oexnr.cn/snews/8611.htm
- http://m.blog.oexnr.cn/snews/7445929.htm
- http://m.blog.oexnr.cn/snews/2940.htm
- http://m.blog.oexnr.cn/snews/30389.htm
- http://m.blog.oexnr.cn/snews/149832.htm
- http://m.blog.oexnr.cn/snews/52195.htm
- http://m.blog.oexnr.cn/snews/93970.htm
- http://m.blog.oexnr.cn/snews/400949.htm
- http://m.blog.oexnr.cn/snews/161857.htm
- http://m.blog.oexnr.cn/snews/9601.htm
- http://m.blog.oexnr.cn/snews/2057268.htm
- http://m.blog.oexnr.cn/snews/1188429.htm
- http://m.blog.oexnr.cn/snews/6421687.htm
- http://m.blog.oexnr.cn/snews/452030.htm
- http://m.blog.oexnr.cn/snews/065432.htm
- http://m.blog.oexnr.cn/snews/16058.htm
- http://m.blog.oexnr.cn/snews/656046.htm
- http://m.blog.oexnr.cn/snews/1912.htm
- http://m.blog.oexnr.cn/snews/6769193.htm
- http://m.blog.oexnr.cn/snews/6835302.htm
- http://m.blog.oexnr.cn/snews/980914.htm
- http://m.blog.oexnr.cn/snews/532075.htm
- http://m.blog.oexnr.cn/snews/13931.htm
- http://m.blog.oexnr.cn/snews/27639.htm
- http://m.blog.oexnr.cn/snews/65642.htm
- http://m.blog.oexnr.cn/snews/636484.htm
- http://m.blog.oexnr.cn/snews/0327039.htm
- http://m.blog.oexnr.cn/snews/737159.htm
- http://m.blog.oexnr.cn/snews/4334538.htm
- http://m.blog.oexnr.cn/snews/458164.htm
- http://m.blog.oexnr.cn/snews/134958.htm
- http://m.blog.oexnr.cn/snews/665268.htm
- http://m.blog.oexnr.cn/snews/0354.htm
- http://m.blog.oexnr.cn/snews/582605.htm
- http://m.blog.oexnr.cn/snews/0641.htm
- http://m.blog.oexnr.cn/snews/476605.htm
- http://m.blog.oexnr.cn/snews/090406.htm
- http://m.blog.oexnr.cn/snews/511764.htm
- http://m.blog.oexnr.cn/snews/1787.htm
- http://m.blog.oexnr.cn/snews/836154.htm
- http://m.blog.oexnr.cn/snews/8097131.htm
- http://m.blog.oexnr.cn/snews/003132.htm
- http://m.blog.oexnr.cn/snews/6918.htm
- http://m.blog.oexnr.cn/snews/54804.htm
- http://m.blog.oexnr.cn/snews/8103.htm
- http://m.blog.oexnr.cn/snews/5027954.htm
- http://m.blog.oexnr.cn/snews/611576.htm
- http://m.blog.oexnr.cn/snews/01195.htm
- http://m.blog.oexnr.cn/snews/66176.htm
- http://m.blog.oexnr.cn/snews/274238.htm
- http://m.blog.oexnr.cn/snews/113910.htm
- http://m.blog.oexnr.cn/snews/4435785.htm
- http://m.blog.oexnr.cn/snews/1526092.htm
- http://m.blog.oexnr.cn/snews/2230.htm
- http://m.blog.oexnr.cn/snews/3464483.htm
- http://m.blog.oexnr.cn/snews/50215.htm
- http://m.blog.oexnr.cn/snews/534584.htm
- http://m.blog.oexnr.cn/snews/2257.htm
- http://m.blog.oexnr.cn/snews/71495.htm
- http://m.blog.oexnr.cn/snews/108066.htm
- http://m.blog.oexnr.cn/snews/9144280.htm
- http://m.blog.oexnr.cn/snews/1192043.htm
- http://m.blog.oexnr.cn/snews/99477.htm
- http://m.blog.oexnr.cn/snews/162773.htm
- http://m.blog.oexnr.cn/snews/0075559.htm
- http://m.blog.oexnr.cn/snews/91945.htm
- http://m.blog.oexnr.cn/snews/9460.htm
- http://m.blog.oexnr.cn/snews/16380.htm
- http://m.blog.oexnr.cn/snews/9366827.htm
- http://m.blog.oexnr.cn/snews/706469.htm
- http://m.blog.oexnr.cn/snews/40014.htm
- http://m.blog.oexnr.cn/snews/45365.htm
- http://m.blog.oexnr.cn/snews/05484.htm
- http://m.blog.oexnr.cn/snews/755456.htm
- http://m.blog.oexnr.cn/snews/72210.htm
- http://m.blog.oexnr.cn/snews/42306.htm
- http://m.blog.oexnr.cn/snews/3118.htm
- http://m.blog.oexnr.cn/snews/6879.htm
- http://m.blog.oexnr.cn/snews/43944.htm
- http://m.blog.oexnr.cn/snews/1119.htm
- http://m.blog.oexnr.cn/snews/13466.htm
- http://m.blog.oexnr.cn/snews/9952024.htm
- http://m.blog.oexnr.cn/snews/2764.htm
- http://m.blog.oexnr.cn/snews/0225.htm
- http://m.blog.oexnr.cn/snews/0287745.htm
- http://m.blog.oexnr.cn/snews/5259.htm
- http://m.blog.oexnr.cn/snews/3831117.htm
- http://m.blog.oexnr.cn/snews/84447.htm
- http://m.blog.oexnr.cn/snews/7391051.htm
- http://m.blog.oexnr.cn/snews/305700.htm
- http://m.blog.oexnr.cn/snews/71986.htm
- http://m.blog.oexnr.cn/snews/1382318.htm
- http://m.blog.oexnr.cn/snews/6961.htm
- http://m.blog.oexnr.cn/snews/996856.htm
- http://m.blog.oexnr.cn/snews/305741.htm
- http://m.blog.oexnr.cn/snews/03282.htm
- http://m.blog.oexnr.cn/snews/5287929.htm
- http://m.blog.oexnr.cn/snews/3109.htm
- http://m.blog.oexnr.cn/snews/350494.htm
- http://m.blog.oexnr.cn/snews/1117379.htm
- http://m.blog.oexnr.cn/snews/31790.htm
- http://m.blog.oexnr.cn/snews/7999.htm
- http://m.blog.oexnr.cn/snews/03586.htm
- http://m.blog.oexnr.cn/snews/314403.htm
- http://m.blog.oexnr.cn/snews/85138.htm
- http://m.blog.oexnr.cn/snews/7031.htm
- http://m.blog.oexnr.cn/snews/7757735.htm
- http://m.blog.oexnr.cn/snews/865862.htm
- http://m.blog.oexnr.cn/snews/749951.htm
- http://m.blog.oexnr.cn/snews/84078.htm
- http://m.blog.oexnr.cn/snews/587708.htm
- http://m.blog.oexnr.cn/snews/9764511.htm
- http://m.blog.oexnr.cn/snews/3890267.htm
- http://m.blog.oexnr.cn/snews/1904006.htm
- http://m.blog.oexnr.cn/snews/7654745.htm
- http://m.blog.oexnr.cn/snews/271153.htm
- http://m.blog.oexnr.cn/snews/201635.htm
- http://m.blog.oexnr.cn/snews/8073779.htm
- http://m.blog.oexnr.cn/snews/88614.htm
- http://m.blog.oexnr.cn/snews/4163969.htm
- http://m.blog.oexnr.cn/snews/273072.htm
- http://m.blog.oexnr.cn/snews/3740249.htm
- http://m.blog.oexnr.cn/snews/46074.htm
- http://m.blog.oexnr.cn/snews/8585436.htm

## 项目结构

```
linkvault/
├── cmd/                            # 命令行入口与子命令实现
│   ├── server/                     # HTTP 服务启动命令 (main.go)
│   ├── migrate/                    # 数据库迁移与初始化命令
│   └── probe/                      # 手动触发健康检查的命令行工具
├── internal/                       # 内部私有包，不对外暴露
│   ├── config/                     # 环境变量解析与配置结构体定义
│   ├── db/                         # SQLite 连接池与基础 CRUD 操作
│   │   ├── migrations/             # 版本化的 DDL 变更文件 (按时间戳命名)
│   │   └── queries/                # 预编译的 SQL 查询模板
│   ├── model/                      # 数据实体定义 (Link, Tag, ProbeLog, AccessLog)
│   ├── scheduler/                  # 基于 cron 表达式的任务调度器
│   ├── probe/                      # HTTP 探测引擎 (含重定向跟踪与超时控制)
│   ├── api/                        # JSON API 路由处理器与中间件
│   └── exporter/                   # 数据导出器 (Markdown, JSON, PlainText)
├── pkg/                            # 可被外部项目引用的公共库
│   ├── httpclient/                 # 带熔断与重试机制的 HTTP 客户端封装
│   ├── validator/                  # URL 格式校验与域名黑名单检查
│   └── logger/                     # 结构化日志 (基于 slog 的封装)
├── web/                            # Web 静态资源与模板文件
│   ├── static/                     # CSS, JavaScript 与图标文件
│   └── templates/                  # 服务端渲染的 HTML 模板 (列表页、详情页)
├── scripts/                        # 开发与运维辅助脚本
│   ├── seed.sh                     # 生成测试数据
│   └── backup.sh                   # 数据库备份脚本 (配合 cron)
├── configs/                        # 样例配置文件与应用默认值
│   ├── app.yaml.example            # 完整配置项示例
│   └── scheduler.yaml.example      # 探测任务预设示例
├── tests/                          # 单元测试与集成测试
│   ├── unit/                       # 各模块单元测试 (按包划分)
│   └── integration/                # API 端到端测试与数据库回放测试
├── docs/                           # 完整文档源文件 (参考文档导航章节)
├── go.mod                          # Go 模块依赖管理
├── go.sum                          # 依赖校验和
├── Makefile                        # 常用构建命令封装 (build, test, run)
├── Dockerfile                      # 基于 Alpine 的生产级容器构建文件
├── docker-compose.yml              # 本地开发环境容器编排 (含 Redis 缓存)
└── README.md                       # 项目入口文档 (即本文档)
```

## 贡献指南

提交议题与功能请求：请在 GitHub Issues 中选择对应的模板，清晰描述复现步骤、预期行为与实际表现。功能请求需明确使用场景与预期收益。

代码提交规范：所有 Pull Request 需基于 dev 分支创建，提交信息遵循 Conventional Commits 格式 (feat/fix/docs/chore)。每个 PR 应关联至少一个 Issue 编号。

测试覆盖要求：新增功能或修复缺陷时，需补充对应的单元测试或集成测试。测试覆盖率不得低于 80%。运行 make test 可执行全部测试用例。

文档同步更新：涉及 API 变更、配置项新增或行为调整时，必须同步更新 docs 目录下的对应文档以及 README 中的相关章节。

本地开发环境准备：克隆仓库后执行 make setup 自动安装 pre-commit 钩子与依赖工具。开发过程中请确保 golangci-lint 检查通过。

## 常见问题

系统启动后无法访问后台管理界面如何解决

请检查 .env 文件中 ADMIN_EMAIL 与 ADMIN_PASSWORD_HASH 是否正确配置。若使用默认 SQLite 数据库，确认 data/ 目录具有写入权限。首次启动时系统会在终端输出临时生成的初始密码，请注意保留该输出。

健康检查任务一直显示超时如何处理

超时通常由目标服务器网络延迟或防火墙策略导致。可在配置文件中调整 probe_timeout 参数，默认值为 5 秒，建议逐步增加至 15 秒。同时检查 probe_parallelism 参数，过高的并发可能导致本地网络连接耗尽。

导入大量链接时页面响应缓慢是什么原因

系统默认使用 SQLite 数据库，批量写入操作在高并发下会产生锁竞争。建议通过 API 接口分批导入，每批不超过 500 条记录，并设置 batch_commit_interval 参数控制提交间隔。对于超过万条级别的导入，可临时启用 WAL 模式并关闭同步锁。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:36:48
