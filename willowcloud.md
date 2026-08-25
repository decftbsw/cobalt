# WebLink Navigator

WebLink Navigator 是一个面向技术研究者、信息分析人员和内容聚合者的轻量级外链资源汇总与导航系统。该项目定位于对海量分散的 URL 进行结构化收录、分类标注与状态监控，帮助用户从繁杂的链接集合中快速定位有价值的信息入口。本系统不提供爬虫或数据采集功能，专注于链接的整理、展示与基础可用性检测，适用于个人知识库构建、团队共享书签库以及公开的信息导航站点建设。

## 功能概览

**多源链接统一收录** 支持将来自不同域名、不同路径结构的 URL 集中存储于单一数据源中，并通过唯一标识进行管理。

**自动协议识别与补全提示** 系统在录入链接时自动检测协议头（http / https）缺失情况，并给出标准化建议，但不强制修改用户原始输入。

**链接状态周期性检测** 内置轻量级巡检模块，可配置定时任务对已收录链接进行 HTTP 状态码检查，标记异常链接。

**分类标签与全文检索** 每条链接可关联多个自定义标签，支持基于标题、描述、标签及 URL 自身的全文模糊搜索。

**导入导出兼容多种格式** 支持 JSON、CSV 及 Markdown 列表格式的链接批量导入与导出，便于与其他工具链集成。

**访问统计与热度排序** 记录每个链接的点击次数与最近访问时间，支持按热度、收录时间或字母序排列展示。

**响应式管理面板** 提供适配桌面与移动设备的 Web 管理界面，无需额外客户端即可完成链接增删改查操作。

## 应用场景

**技术文档与教程聚合** 开发团队可将分散在各大技术博客、官方文档、社区讨论中的教程链接统一收录，按技术栈分类，新成员入职时可快速获取学习路径。

**行业资讯监控清单** 研究人员将每日浏览的行业分析报告、政策文件、市场数据源链接集中管理，配合状态检测功能及时发现失效来源，保证信息链的完整性。

**开源项目依赖参考库** 开源维护者记录项目所依赖的第三方库主页、镜像源、备用下载地址，当主站不可用时快速切换至备用链接。

**个人知识体系外脑** 知识工作者将阅读过程中积累的参考文章、工具页面、在线计算器等零散链接结构化存储，避免浏览器书签的混乱与丢失。

**活动与会议资料归档** 技术会议组织者将演讲幻灯片、视频回放、相关论文的链接按议程顺序整理，会后统一发布给参会者，便于资料追溯。

## 快速开始

以下步骤指导您在本地环境中完成 WebLink Navigator 的部署与初始运行。

```bash
# 克隆代码仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装项目依赖（使用 pip 与虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 初始化数据库表结构
python manage.py migrate

# 导入示例链接数据（可选）
python manage.py loaddata sample_links.json

# 启动开发服务器
python manage.py runserver 0.0.0.0:8000
```

服务启动后，访问 http://127.0.0.1:8000 进入管理界面。默认管理员账户为 admin / admin123，首次登录后请立即修改密码。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|----------|----------|------|
| Python | 3.9 - 3.11 | 核心运行时环境，低于 3.9 版本不兼容异步检测模块 |
| Django | 4.2.x | Web 框架及 ORM 层，用于管理界面与数据模型 |
| SQLite | 3.35+ | 默认嵌入式数据库，生产环境可切换至 PostgreSQL 14+ |
| requests | 2.31.0 | 用于链接状态检测的 HTTP 客户端库 |
| python-dotenv | 1.0.0 | 环境变量配置加载工具，管理敏感参数 |
| uWSGI | 2.0.22 | 生产环境部署所需的应用网关服务器（可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user/quick-start.md | 如何添加第一条链接、如何分类、如何搜索已有资源 |
| 运维指南 | /docs/ops/deployment.md | 如何将系统部署至生产服务器、配置 HTTPS 与反向代理 |
| 开发者文档 | /docs/dev/api-design.md | 链接数据模型字段定义、RESTful API 端点说明与示例 |
| 故障排查 | /docs/troubleshooting/common-issues.md | 检测任务超时、数据库锁冲突、内存占用过高等问题处理 |

## 资源列表

- http://m.3g.ghtkgg.cn/nnews/40892.htm
- http://m.3g.ghtkgg.cn/nnews/179424.htm
- http://m.3g.ghtkgg.cn/nnews/675994.htm
- http://m.3g.ghtkgg.cn/nnews/84103.htm
- http://m.3g.ghtkgg.cn/nnews/8048089.htm
- http://m.3g.ghtkgg.cn/nnews/05559.htm
- http://m.3g.ghtkgg.cn/nnews/2706.htm
- http://m.3g.ghtkgg.cn/nnews/3679890.htm
- http://m.3g.ghtkgg.cn/nnews/3308344.htm
- http://m.3g.ghtkgg.cn/nnews/745598.htm
- http://m.3g.ghtkgg.cn/nnews/2401275.htm
- http://m.3g.ghtkgg.cn/nnews/17598.htm
- http://m.3g.ghtkgg.cn/nnews/49991.htm
- http://m.3g.ghtkgg.cn/nnews/53090.htm
- http://m.3g.ghtkgg.cn/nnews/2160.htm
- http://m.3g.ghtkgg.cn/nnews/58126.htm
- http://m.3g.ghtkgg.cn/nnews/8842701.htm
- http://m.3g.ghtkgg.cn/nnews/0194.htm
- http://m.3g.ghtkgg.cn/nnews/604540.htm
- http://m.3g.ghtkgg.cn/nnews/9105791.htm
- http://m.3g.ghtkgg.cn/nnews/793956.htm
- http://m.3g.ghtkgg.cn/nnews/6997.htm
- http://m.3g.ghtkgg.cn/nnews/341160.htm
- http://m.3g.ghtkgg.cn/nnews/3161896.htm
- http://m.3g.ghtkgg.cn/nnews/277692.htm
- http://m.3g.ghtkgg.cn/nnews/90820.htm
- http://m.3g.ghtkgg.cn/nnews/393065.htm
- http://m.3g.ghtkgg.cn/nnews/523780.htm
- http://m.3g.ghtkgg.cn/nnews/11818.htm
- http://m.3g.ghtkgg.cn/nnews/3413132.htm
- http://m.3g.ghtkgg.cn/nnews/72035.htm
- http://m.3g.ghtkgg.cn/nnews/457559.htm
- http://m.3g.ghtkgg.cn/nnews/2445628.htm
- http://m.3g.ghtkgg.cn/nnews/29416.htm
- http://m.3g.ghtkgg.cn/nnews/389832.htm
- http://m.3g.ghtkgg.cn/nnews/219306.htm
- http://m.3g.ghtkgg.cn/nnews/07376.htm
- http://m.3g.ghtkgg.cn/nnews/2207.htm
- http://m.3g.ghtkgg.cn/nnews/5168.htm
- http://m.3g.ghtkgg.cn/nnews/43283.htm
- http://m.3g.ghtkgg.cn/nnews/6484.htm
- http://m.3g.ghtkgg.cn/nnews/60948.htm
- http://m.3g.ghtkgg.cn/nnews/1320.htm
- http://m.3g.ghtkgg.cn/nnews/901493.htm
- http://m.3g.ghtkgg.cn/nnews/3551412.htm
- http://m.3g.ghtkgg.cn/nnews/5939.htm
- http://m.3g.ghtkgg.cn/nnews/229084.htm
- http://m.3g.ghtkgg.cn/nnews/1149.htm
- http://m.3g.ghtkgg.cn/nnews/33283.htm
- http://m.3g.ghtkgg.cn/nnews/2020.htm
- http://m.3g.ghtkgg.cn/nnews/203166.htm
- http://m.3g.ghtkgg.cn/nnews/59386.htm
- http://m.3g.ghtkgg.cn/nnews/96985.htm
- http://m.3g.ghtkgg.cn/nnews/39715.htm
- http://m.3g.ghtkgg.cn/nnews/4127893.htm
- http://m.3g.ghtkgg.cn/nnews/6213926.htm
- http://m.3g.ghtkgg.cn/nnews/36798.htm
- http://m.3g.ghtkgg.cn/nnews/9465858.htm
- http://m.3g.ghtkgg.cn/nnews/797225.htm
- http://m.3g.ghtkgg.cn/nnews/1813703.htm
- http://m.3g.ghtkgg.cn/nnews/8995492.htm
- http://m.3g.ghtkgg.cn/nnews/43450.htm
- http://m.3g.ghtkgg.cn/nnews/7619091.htm
- http://m.3g.ghtkgg.cn/nnews/57447.htm
- http://m.3g.ghtkgg.cn/nnews/6428178.htm
- http://m.3g.ghtkgg.cn/nnews/2431.htm
- http://m.3g.ghtkgg.cn/nnews/5685.htm
- http://m.3g.ghtkgg.cn/nnews/789121.htm
- http://m.3g.ghtkgg.cn/nnews/68046.htm
- http://m.3g.ghtkgg.cn/nnews/814381.htm
- http://m.3g.ghtkgg.cn/nnews/6107.htm
- http://m.3g.ghtkgg.cn/nnews/54211.htm
- http://m.3g.ghtkgg.cn/nnews/5084.htm
- http://m.3g.ghtkgg.cn/nnews/3051.htm
- http://m.3g.ghtkgg.cn/nnews/06841.htm
- http://m.3g.ghtkgg.cn/nnews/10140.htm
- http://m.3g.ghtkgg.cn/nnews/3211548.htm
- http://m.3g.ghtkgg.cn/nnews/926252.htm
- http://m.3g.ghtkgg.cn/nnews/4731689.htm
- http://m.3g.ghtkgg.cn/nnews/0043.htm
- http://m.3g.ghtkgg.cn/nnews/3019.htm
- http://m.3g.ghtkgg.cn/nnews/9250.htm
- http://m.3g.ghtkgg.cn/nnews/6626384.htm
- http://m.3g.ghtkgg.cn/nnews/85536.htm
- http://m.3g.ghtkgg.cn/nnews/463317.htm
- http://m.3g.ghtkgg.cn/nnews/68216.htm
- http://m.3g.ghtkgg.cn/nnews/31324.htm
- http://m.3g.ghtkgg.cn/nnews/355020.htm
- http://m.3g.ghtkgg.cn/nnews/9512.htm
- http://m.3g.ghtkgg.cn/nnews/5258.htm
- http://m.3g.ghtkgg.cn/nnews/0658155.htm
- http://m.3g.ghtkgg.cn/nnews/9106933.htm
- http://m.3g.ghtkgg.cn/nnews/9256.htm
- http://m.3g.ghtkgg.cn/nnews/97465.htm
- http://m.3g.ghtkgg.cn/nnews/3795.htm
- http://m.3g.ghtkgg.cn/nnews/8924.htm
- http://m.3g.ghtkgg.cn/nnews/4869.htm
- http://m.3g.ghtkgg.cn/nnews/91380.htm
- http://m.3g.ghtkgg.cn/nnews/2654781.htm
- http://m.3g.ghtkgg.cn/nnews/9231521.htm
- http://m.3g.ghtkgg.cn/nnews/043143.htm
- http://m.3g.ghtkgg.cn/nnews/940291.htm
- http://m.3g.ghtkgg.cn/nnews/916874.htm
- http://m.3g.ghtkgg.cn/nnews/3266.htm
- http://m.3g.ghtkgg.cn/nnews/102144.htm
- http://m.3g.ghtkgg.cn/nnews/7751.htm
- http://m.3g.ghtkgg.cn/nnews/2641454.htm
- http://m.3g.ghtkgg.cn/nnews/3783.htm
- http://m.3g.ghtkgg.cn/nnews/75045.htm
- http://m.3g.ghtkgg.cn/nnews/5284.htm
- http://m.3g.ghtkgg.cn/nnews/75679.htm
- http://m.3g.ghtkgg.cn/nnews/4480.htm
- http://m.3g.ghtkgg.cn/nnews/6102.htm
- http://m.3g.ghtkgg.cn/nnews/6322.htm
- http://m.3g.ghtkgg.cn/nnews/3066.htm
- http://m.3g.ghtkgg.cn/nnews/981419.htm
- http://m.3g.ghtkgg.cn/nnews/7612.htm
- http://m.3g.ghtkgg.cn/nnews/10898.htm
- http://m.3g.ghtkgg.cn/nnews/6268885.htm
- http://m.3g.ghtkgg.cn/nnews/16331.htm
- http://m.3g.ghtkgg.cn/nnews/63366.htm
- http://m.3g.ghtkgg.cn/nnews/26449.htm
- http://m.3g.ghtkgg.cn/nnews/1100327.htm
- http://m.3g.ghtkgg.cn/nnews/9462962.htm
- http://m.3g.ghtkgg.cn/nnews/241326.htm
- http://m.3g.ghtkgg.cn/nnews/2280331.htm
- http://m.3g.ghtkgg.cn/nnews/2602132.htm
- http://m.3g.ghtkgg.cn/nnews/8939818.htm
- http://m.3g.ghtkgg.cn/nnews/573924.htm
- http://m.3g.ghtkgg.cn/nnews/7226.htm
- http://m.3g.ghtkgg.cn/nnews/5554.htm
- http://m.3g.ghtkgg.cn/nnews/8227170.htm
- http://m.3g.ghtkgg.cn/nnews/29288.htm
- http://m.3g.ghtkgg.cn/nnews/855606.htm
- http://m.3g.ghtkgg.cn/nnews/72722.htm
- http://m.3g.ghtkgg.cn/nnews/1856670.htm
- http://m.3g.ghtkgg.cn/nnews/33834.htm
- http://m.3g.ghtkgg.cn/nnews/8756939.htm
- http://m.3g.ghtkgg.cn/nnews/91472.htm
- http://m.3g.ghtkgg.cn/nnews/9020271.htm
- http://m.3g.ghtkgg.cn/nnews/8638530.htm
- http://m.3g.ghtkgg.cn/nnews/0977724.htm
- http://m.3g.ghtkgg.cn/nnews/37778.htm
- http://m.3g.ghtkgg.cn/nnews/3275.htm
- http://m.3g.ghtkgg.cn/nnews/50652.htm
- http://m.3g.ghtkgg.cn/nnews/7963.htm
- http://m.3g.ghtkgg.cn/nnews/3690.htm
- http://m.3g.ghtkgg.cn/nnews/5254.htm
- http://m.3g.ghtkgg.cn/nnews/5481.htm
- http://m.3g.ghtkgg.cn/nnews/97430.htm
- http://m.3g.ghtkgg.cn/nnews/3316.htm
- http://m.3g.ghtkgg.cn/nnews/73829.htm
- http://m.3g.ghtkgg.cn/nnews/3806.htm
- http://m.3g.ghtkgg.cn/nnews/15087.htm
- http://m.3g.ghtkgg.cn/nnews/1181.htm
- http://m.3g.ghtkgg.cn/nnews/629672.htm
- http://m.3g.ghtkgg.cn/nnews/4472909.htm
- http://m.3g.ghtkgg.cn/nnews/39148.htm
- http://m.3g.ghtkgg.cn/nnews/4666185.htm
- http://m.3g.ghtkgg.cn/nnews/98576.htm
- http://m.3g.ghtkgg.cn/nnews/3530447.htm
- http://m.3g.ghtkgg.cn/nnews/1569505.htm
- http://m.3g.ghtkgg.cn/nnews/2488.htm
- http://m.3g.ghtkgg.cn/nnews/835277.htm
- http://m.3g.ghtkgg.cn/nnews/1909.htm
- http://m.3g.ghtkgg.cn/nnews/3764.htm
- http://m.3g.ghtkgg.cn/nnews/103626.htm
- http://m.3g.ghtkgg.cn/nnews/6184355.htm
- http://m.3g.ghtkgg.cn/nnews/14428.htm
- http://m.3g.ghtkgg.cn/nnews/2240081.htm
- http://m.3g.ghtkgg.cn/nnews/4601.htm
- http://m.3g.ghtkgg.cn/nnews/0257.htm
- http://m.3g.ghtkgg.cn/nnews/8229806.htm
- http://m.3g.ghtkgg.cn/nnews/05941.htm
- http://m.3g.ghtkgg.cn/nnews/476684.htm
- http://m.3g.ghtkgg.cn/nnews/2723731.htm
- http://m.3g.ghtkgg.cn/nnews/404157.htm
- http://m.3g.ghtkgg.cn/nnews/269282.htm
- http://m.3g.ghtkgg.cn/nnews/95050.htm
- http://m.3g.ghtkgg.cn/nnews/4914.htm
- http://m.3g.ghtkgg.cn/nnews/6281481.htm
- http://m.3g.ghtkgg.cn/nnews/597691.htm
- http://m.3g.ghtkgg.cn/nnews/078467.htm
- http://m.3g.ghtkgg.cn/nnews/97695.htm
- http://m.3g.ghtkgg.cn/nnews/7827302.htm
- http://m.3g.ghtkgg.cn/nnews/5205.htm
- http://m.3g.ghtkgg.cn/nnews/578344.htm
- http://m.3g.ghtkgg.cn/nnews/7195204.htm
- http://m.3g.ghtkgg.cn/nnews/70167.htm
- http://m.3g.ghtkgg.cn/nnews/854192.htm
- http://m.3g.ghtkgg.cn/nnews/292000.htm
- http://m.3g.ghtkgg.cn/nnews/2249.htm
- http://m.3g.ghtkgg.cn/nnews/0405146.htm
- http://m.3g.ghtkgg.cn/nnews/5215.htm
- http://m.3g.ghtkgg.cn/nnews/6523927.htm
- http://m.3g.ghtkgg.cn/nnews/9778.htm
- http://m.3g.ghtkgg.cn/nnews/7639854.htm
- http://m.3g.ghtkgg.cn/nnews/0696.htm
- http://m.3g.ghtkgg.cn/nnews/49218.htm
- http://m.3g.ghtkgg.cn/nnews/79582.htm
- http://m.3g.ghtkgg.cn/nnews/56404.htm
- http://m.3g.ghtkgg.cn/nnews/4812039.htm
- http://m.3g.ghtkgg.cn/nnews/1689350.htm
- http://m.3g.ghtkgg.cn/nnews/11215.htm
- http://m.3g.ghtkgg.cn/nnews/57422.htm
- http://m.3g.ghtkgg.cn/nnews/989424.htm
- http://m.3g.ghtkgg.cn/nnews/6935413.htm
- http://m.3g.ghtkgg.cn/nnews/67241.htm
- http://m.3g.ghtkgg.cn/nnews/569177.htm
- http://m.3g.ghtkgg.cn/nnews/1553826.htm
- http://m.3g.ghtkgg.cn/nnews/595056.htm
- http://m.3g.ghtkgg.cn/nnews/0683.htm
- http://m.3g.ghtkgg.cn/nnews/1991524.htm
- http://m.3g.ghtkgg.cn/nnews/29156.htm
- http://m.3g.ghtkgg.cn/nnews/491975.htm
- http://m.3g.ghtkgg.cn/nnews/3772.htm
- http://m.3g.ghtkgg.cn/nnews/1594496.htm
- http://m.3g.ghtkgg.cn/nnews/30843.htm
- http://m.3g.ghtkgg.cn/nnews/054620.htm
- http://m.3g.ghtkgg.cn/nnews/348290.htm
- http://m.3g.ghtkgg.cn/nnews/855444.htm
- http://m.3g.ghtkgg.cn/nnews/1814809.htm
- http://m.3g.ghtkgg.cn/nnews/7846320.htm
- http://m.3g.ghtkgg.cn/nnews/9622.htm
- http://m.3g.ghtkgg.cn/nnews/284434.htm
- http://m.3g.ghtkgg.cn/nnews/4250651.htm
- http://m.3g.ghtkgg.cn/nnews/64344.htm
- http://m.3g.ghtkgg.cn/nnews/2218427.htm
- http://m.3g.ghtkgg.cn/nnews/55470.htm
- http://m.3g.ghtkgg.cn/nnews/0931991.htm
- http://m.3g.ghtkgg.cn/nnews/7321238.htm
- http://m.3g.ghtkgg.cn/nnews/1321.htm
- http://m.3g.ghtkgg.cn/nnews/662620.htm
- http://m.3g.ghtkgg.cn/nnews/506958.htm
- http://m.3g.ghtkgg.cn/nnews/2973000.htm
- http://m.3g.ghtkgg.cn/nnews/197795.htm
- http://m.3g.ghtkgg.cn/nnews/538414.htm
- http://m.3g.ghtkgg.cn/nnews/3587.htm
- http://m.3g.ghtkgg.cn/nnews/81832.htm
- http://m.3g.ghtkgg.cn/nnews/516240.htm
- http://m.3g.ghtkgg.cn/nnews/85295.htm
- http://m.3g.ghtkgg.cn/nnews/3389187.htm
- http://m.3g.ghtkgg.cn/nnews/145717.htm
- http://m.3g.ghtkgg.cn/nnews/697990.htm
- http://m.3g.ghtkgg.cn/nnews/2524240.htm
- http://m.3g.ghtkgg.cn/nnews/444230.htm
- http://m.3g.ghtkgg.cn/nnews/7836499.htm
- http://m.3g.ghtkgg.cn/nnews/3350851.htm
- http://m.3g.ghtkgg.cn/nnews/501273.htm
- http://m.3g.ghtkgg.cn/nnews/3424999.htm
- http://m.3g.ghtkgg.cn/nnews/241506.htm
- http://m.3g.ghtkgg.cn/nnews/4852.htm
- http://m.3g.ghtkgg.cn/nnews/2821.htm
- http://m.3g.ghtkgg.cn/nnews/75747.htm
- http://m.3g.ghtkgg.cn/nnews/64742.htm
- http://m.3g.ghtkgg.cn/nnews/3393816.htm
- http://m.3g.ghtkgg.cn/nnews/50382.htm
- http://m.3g.ghtkgg.cn/nnews/1693.htm
- http://m.3g.ghtkgg.cn/nnews/20958.htm
- http://m.3g.ghtkgg.cn/nnews/28795.htm
- http://m.3g.ghtkgg.cn/nnews/00931.htm
- http://m.3g.ghtkgg.cn/nnews/3426767.htm
- http://m.3g.ghtkgg.cn/nnews/53630.htm
- http://m.3g.ghtkgg.cn/nnews/048465.htm
- http://m.3g.ghtkgg.cn/nnews/7647399.htm
- http://m.3g.ghtkgg.cn/nnews/69570.htm
- http://m.3g.ghtkgg.cn/nnews/66392.htm
- http://m.3g.ghtkgg.cn/nnews/504238.htm
- http://m.3g.ghtkgg.cn/nnews/5185727.htm
- http://m.3g.ghtkgg.cn/nnews/366077.htm
- http://m.3g.ghtkgg.cn/nnews/678538.htm
- http://m.3g.ghtkgg.cn/nnews/6893.htm
- http://m.3g.ghtkgg.cn/nnews/3291074.htm
- http://m.3g.ghtkgg.cn/nnews/16705.htm
- http://m.3g.ghtkgg.cn/nnews/299072.htm
- http://m.3g.ghtkgg.cn/nnews/1133430.htm
- http://m.3g.ghtkgg.cn/nnews/2611044.htm
- http://m.3g.ghtkgg.cn/nnews/415424.htm
- http://m.3g.ghtkgg.cn/nnews/449664.htm
- http://m.3g.ghtkgg.cn/nnews/055981.htm
- http://m.3g.ghtkgg.cn/nnews/7695698.htm
- http://m.3g.ghtkgg.cn/nnews/6116162.htm
- http://m.3g.ghtkgg.cn/nnews/3626.htm
- http://m.3g.ghtkgg.cn/nnews/294341.htm
- http://m.3g.ghtkgg.cn/nnews/427704.htm
- http://m.3g.ghtkgg.cn/nnews/9973695.htm
- http://m.3g.ghtkgg.cn/nnews/15131.htm
- http://m.3g.ghtkgg.cn/nnews/3631.htm
- http://m.3g.ghtkgg.cn/nnews/4073.htm
- http://m.3g.ghtkgg.cn/nnews/1145395.htm
- http://m.3g.ghtkgg.cn/nnews/7009.htm
- http://m.3g.ghtkgg.cn/nnews/02844.htm
- http://m.3g.ghtkgg.cn/nnews/31213.htm
- http://m.3g.ghtkgg.cn/nnews/1413547.htm
- http://m.3g.ghtkgg.cn/nnews/5303515.htm
- http://m.3g.ghtkgg.cn/nnews/882171.htm
- http://m.3g.ghtkgg.cn/nnews/27660.htm
- http://m.3g.ghtkgg.cn/nnews/933383.htm
- http://m.3g.ghtkgg.cn/nnews/1255139.htm
- http://m.3g.ghtkgg.cn/nnews/292267.htm

## 项目结构

```
weblink-navigator/
├── manage.py                  # Django 项目管理入口
├── requirements.txt           # Python 依赖清单
├── .env.example               # 环境变量配置模板
├── src/                       # 源代码主目录
│   ├── core/                  # 核心配置模块
│   │   ├── settings.py        # 项目配置（数据库、中间件、静态文件）
│   │   ├── urls.py            # 根路由映射
│   │   └── wsgi.py            # 生产环境 WSGI 入口
│   ├── links/                 # 链接管理应用
│   │   ├── models.py          # Link, Tag, Category 数据模型
│   │   ├── views.py           # 列表、详情、搜索、导入导出视图
│   │   ├── serializer.py      # DRF 序列化器（API 输出）
│   │   └── tasks.py           # 链接状态检测异步任务
│   ├── checks/                # 健康检查与巡检模块
│   │   ├── http_client.py     # 自定义 HTTP 请求封装（超时、重试）
│   │   └── scheduler.py       # 定时任务配置（每 6 小时巡检一次）
│   ├── utils/                 # 通用工具函数
│   │   ├── url_parser.py      # URL 拆解、协议补全提示
│   │   └── export_import.py   # JSON / CSV / Markdown 转换器
│   ├── static/                # 静态资源（CSS, JavaScript, 图标）
│   │   ├── css/               # 响应式管理面板样式
│   │   └── js/                # 前端交互脚本（搜索、排序、分页）
│   └── templates/             # Django 模板文件
│       ├── base.html          # 基础布局模板
│       ├── link_list.html     # 链接列表页
│       └── link_detail.html   # 链接详情页
├── tests/                     # 单元测试与集成测试
│   ├── test_models.py         # 数据模型测试
│   ├── test_api.py            # API 端点测试
│   └── test_checks.py         # 健康检测逻辑测试
├── docs/                      # 文档目录
│   ├── user/                  # 用户手册
│   ├── ops/                   # 运维部署文档
│   └── dev/                   # 开发者文档
├── scripts/                   # 辅助运维脚本
│   ├── init_db.py             # 初始化数据库与超级用户
│   └── backup_links.py        # 链接数据备份脚本
└── logs/                      # 应用日志存储目录
    ├── access.log             # 访问日志
    └── error.log              # 错误日志
```

## 贡献指南

我们欢迎并鼓励社区开发者以多种方式参与 WebLink Navigator 项目的改进。请遵循以下步骤提交您的贡献。

首先，在 GitHub 上 fork 本仓库至您的个人账号，并将 fork 后的仓库克隆至本地开发环境。然后，创建以功能或修复命名的特性分支，例如 `feature/add-batch-tag-editor` 或 `fix/url-parse-issue-123`。在分支上进行开发时，请确保代码风格符合 PEP 8 规范，并为新增功能或修复编写对应的单元测试用例，测试覆盖率不低于 85%。完成开发后，使用 `git push` 将分支推送至您的远程 fork 仓库，随后通过 GitHub 界面发起 Pull Request 至本仓库的 main 分支。PR 描述中应清晰说明改动目的、实现方式以及相关 issue 编号（如有）。项目维护者将在三个工作日内进行 Code Review，并可能提出修改意见，请保持关注并积极回应。所有 PR 必须通过持续集成流程（包括单元测试与静态代码检查）后方可合并。

## 常见问题

**问：系统收录的链接数量达到多少时会影响性能？**

答：在默认 SQLite 配置下，单表记录数超过 5 万条时，未加索引的检索操作可能出现明显延迟。建议在生产环境中切换至 PostgreSQL，并为 url 字段和 created_at 字段建立联合索引。实测 PostgreSQL 环境下，百万级链接的检索响应时间可维持在 200 毫秒以内。若链接数量持续增长，可考虑按月分表或接入 Elasticsearch 作为搜索后端。

**问：链接状态检测任务是否会频繁触发目标服务器的反爬机制？**

答：系统默认的检测间隔为每 6 小时一次，且每个链接在单次巡检中仅发起一次 HEAD 请求（若 HEAD 不支持则降级为 GET 但仅读取头部）。并发请求数通过 semaphore 限制为 10 个，避免对同一目标域名造成瞬时压力。对于明确声明了 robots.txt 且禁止自动检测的站点，用户可在管理后台将该链接标记为“跳过检测”以规避风险。

**问：如何将现有的浏览器书签或 Pocket 收藏批量导入系统？**

答：系统管理界面内置了“导入”功能，支持 Netscape Bookmark HTML 格式（所有主流浏览器均可导出）、Pocket 的 CSV 导出格式以及通用 JSON 格式。导入时用户可选择是否自动提取关键词作为标签，以及是否跳过重复 URL。对于结构不规范的原始数据，建议先使用脚本清洗后再通过 JSON 格式导入。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:00
