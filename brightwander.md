# JNews Link Aggregator

JNews Link Aggregator 是一个面向技术信息采编、新闻聚合与内容分析场景的轻量级外链资源汇总工具。该项目定位于为开发者、内容运营人员与数据分析师提供结构化的新闻条目入口，通过集中管理大量动态新闻链接，降低手工收集与维护成本，提升信息检索与跟踪效率。项目本身不存储新闻正文，仅维护链接元数据与基础分类标签，可作为上层爬虫系统、舆情监控平台或日报自动生成系统的数据源头。

本项目适用于需要快速建立新闻链接池的中小型团队，以及希望在本地环境自建新闻源索引的技术人员。通过标准化的链接清单输出与简单的部署流程，用户可在数分钟内完成环境搭建并开始使用。

## 功能概览

- 批量链接导入与去重：支持从文本文件、CSV 或 JSON 格式批量导入新闻链接，自动识别重复条目并生成去重报告。
- 链接状态健康检查：定时对已收录链接发送 HEAD 请求，检测响应状态码，标记失效或重定向链接。
- 分类标签管理：允许用户为每条链接添加自定义标签，支持按标签过滤与统计，便于分主题整理。
- 全文元数据提取：调用外部解析服务，从目标页面提取标题、发布时间、正文摘要等关键字段，生成结构化记录。
- 导出为多种格式：支持将链接及元数据导出为 Markdown 表格、CSV、JSON 或 RSS 订阅源格式。
- 定时任务调度：内置 cron 风格调度器，可配置每日、每小时或每周自动执行健康检查与元数据刷新。
- 简易 Web 管理界面：提供基于 Flask 的轻量仪表板，用于查看链接状态、执行手动检查与导出数据。
- API 接口开放：提供 RESTful API，支持第三方系统远程调用，获取链接列表、状态信息或触发任务。

## 应用场景

- 日常新闻源监控：运营人员可将本项目作为新闻入口的统一管理后台，每日定时检查链接可访问性，及时发现失效源，保证下游推送服务的数据质量。
- 技术文章日报生成：开发者可结合元数据提取功能，定期抓取指定标签下的最新技术博文链接，自动生成日报 Markdown 文件并提交至团队知识库。
- 舆情分析数据准备：数据分析师可将本项目的导出接口与数据处理流水线对接，批量获取新闻链接列表后，利用外部 NLP 服务进行情感分析与热点词提取。
- 个人阅读清单整理：技术爱好者可使用分类标签功能，按编程语言、框架、行业动态等维度归档感兴趣的文章链接，并通过 Web 界面统一浏览。

## 快速开始

以下命令适用于 Linux / macOS / Windows WSL 环境，假设已安装 Git 与 Python 3.9 或更高版本。

```bash
# 克隆项目仓库
git clone https://github.com/your-org/jnews-link-aggregator.git
cd jnews-link-aggregator

# 创建并激活 Python 虚拟环境
python3 -m venv venv
source venv/bin/activate      # Linux / macOS
# venv\Scripts\activate       # Windows

# 安装项目依赖
pip install --upgrade pip
pip install -r requirements.txt

# 复制示例配置文件并修改数据库连接等参数
cp .env.example .env

# 初始化 SQLite 数据库表结构
python manage.py init-db

# 导入示例链接数据（包含本批次 300 条新闻链接）
python manage.py import-links --file data/sample_links.json

# 启动 Web 管理界面（默认监听 127.0.0.1:5000）
python manage.py runserver
```

访问 http://127.0.0.1:5000 即可进入仪表板。首次运行将自动执行一次全量链接健康检查，结果记录于数据库。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---------|---------|------|
| Python | 3.9 或更高 | 核心运行环境，推荐使用 3.11 以上以获得性能提升 |
| SQLite | 3.28 或更高 | 内置数据库，用于存储链接元数据与任务日志，无需额外安装 |
| requests | 2.28.0 或更高 | 用于发送 HTTP 请求，执行链接状态检查与元数据抓取 |
| flask | 2.2.0 或更高 | 提供 Web 管理界面的后端框架 |
| flask-cors | 3.0.10 或更高 | 处理 API 跨域请求，便于前端或第三方调用 |
| python-dotenv | 0.21.0 或更高 | 加载 .env 环境变量配置文件 |
| apscheduler | 3.10.0 或更高 | 管理定时任务调度，支持 cron 表达式配置 |
| lxml | 4.9.0 或更高 | 用于解析 HTML 页面，提取元数据中的标题与正文摘要 |
| pytest | 7.0.0 或更高 | 仅开发测试需要，生产环境可不安装 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|-----------|
| 用户手册 | docs/user_guide.md | 如何配置定时任务、如何管理标签、如何导出不同格式的数据、Web 界面各模块的操作说明 |
| 开发者指南 | docs/developer_guide.md | 如何扩展自定义解析器、如何新增 API 端点、如何修改数据库 Schema、如何运行单元测试 |
| 部署参考 | docs/deployment.md | 如何将项目部署至生产环境（Nginx + Gunicorn）、如何使用 PostgreSQL 替代 SQLite、如何配置 HTTPS |
| 常见任务 | docs/recipes.md | 如何一键检查所有链接状态、如何清空失效链接、如何生成每周报告、如何与 Slack 或钉钉机器人集成 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/354477.htm
- http://m.wap.ghtkgg.cn/jnews/9397.htm
- http://m.wap.ghtkgg.cn/jnews/02567.htm
- http://m.wap.ghtkgg.cn/jnews/5645.htm
- http://m.wap.ghtkgg.cn/jnews/0401365.htm
- http://m.wap.ghtkgg.cn/jnews/539635.htm
- http://m.wap.ghtkgg.cn/jnews/386697.htm
- http://m.wap.ghtkgg.cn/jnews/8671.htm
- http://m.wap.ghtkgg.cn/jnews/880755.htm
- http://m.wap.ghtkgg.cn/jnews/114263.htm
- http://m.wap.ghtkgg.cn/jnews/1353224.htm
- http://m.wap.ghtkgg.cn/jnews/5714870.htm
- http://m.wap.ghtkgg.cn/jnews/957175.htm
- http://m.wap.ghtkgg.cn/jnews/0995344.htm
- http://m.wap.ghtkgg.cn/jnews/23228.htm
- http://m.wap.ghtkgg.cn/jnews/0754.htm
- http://m.wap.ghtkgg.cn/jnews/9582349.htm
- http://m.wap.ghtkgg.cn/jnews/68743.htm
- http://m.wap.ghtkgg.cn/jnews/68204.htm
- http://m.wap.ghtkgg.cn/jnews/4686.htm
- http://m.wap.ghtkgg.cn/jnews/949057.htm
- http://m.wap.ghtkgg.cn/jnews/2126906.htm
- http://m.wap.ghtkgg.cn/jnews/9427364.htm
- http://m.wap.ghtkgg.cn/jnews/3307.htm
- http://m.wap.ghtkgg.cn/jnews/3818953.htm
- http://m.wap.ghtkgg.cn/jnews/563378.htm
- http://m.wap.ghtkgg.cn/jnews/0115589.htm
- http://m.wap.ghtkgg.cn/jnews/918107.htm
- http://m.wap.ghtkgg.cn/jnews/343367.htm
- http://m.wap.ghtkgg.cn/jnews/21171.htm
- http://m.wap.ghtkgg.cn/jnews/7217133.htm
- http://m.wap.ghtkgg.cn/jnews/8841.htm
- http://m.wap.ghtkgg.cn/jnews/82884.htm
- http://m.wap.ghtkgg.cn/jnews/3608548.htm
- http://m.wap.ghtkgg.cn/jnews/421507.htm
- http://m.wap.ghtkgg.cn/jnews/6307.htm
- http://m.wap.ghtkgg.cn/jnews/9746.htm
- http://m.wap.ghtkgg.cn/jnews/9611.htm
- http://m.wap.ghtkgg.cn/jnews/4770776.htm
- http://m.wap.ghtkgg.cn/jnews/4196156.htm
- http://m.wap.ghtkgg.cn/jnews/0343.htm
- http://m.wap.ghtkgg.cn/jnews/75839.htm
- http://m.wap.ghtkgg.cn/jnews/2429.htm
- http://m.wap.ghtkgg.cn/jnews/577672.htm
- http://m.wap.ghtkgg.cn/jnews/3293257.htm
- http://m.wap.ghtkgg.cn/jnews/06833.htm
- http://m.wap.ghtkgg.cn/jnews/9378370.htm
- http://m.wap.ghtkgg.cn/jnews/3546123.htm
- http://m.wap.ghtkgg.cn/jnews/0651.htm
- http://m.wap.ghtkgg.cn/jnews/0467.htm
- http://m.wap.ghtkgg.cn/jnews/81309.htm
- http://m.wap.ghtkgg.cn/jnews/702031.htm
- http://m.wap.ghtkgg.cn/jnews/851287.htm
- http://m.wap.ghtkgg.cn/jnews/533879.htm
- http://m.wap.ghtkgg.cn/jnews/795786.htm
- http://m.wap.ghtkgg.cn/jnews/2263051.htm
- http://m.wap.ghtkgg.cn/jnews/921692.htm
- http://m.wap.ghtkgg.cn/jnews/673952.htm
- http://m.wap.ghtkgg.cn/jnews/103232.htm
- http://m.wap.ghtkgg.cn/jnews/246501.htm
- http://m.wap.ghtkgg.cn/jnews/2612.htm
- http://m.wap.ghtkgg.cn/jnews/8961146.htm
- http://m.wap.ghtkgg.cn/jnews/5394.htm
- http://m.wap.ghtkgg.cn/jnews/4662.htm
- http://m.wap.ghtkgg.cn/jnews/46933.htm
- http://m.wap.ghtkgg.cn/jnews/955543.htm
- http://m.wap.ghtkgg.cn/jnews/98721.htm
- http://m.wap.ghtkgg.cn/jnews/701213.htm
- http://m.wap.ghtkgg.cn/jnews/37938.htm
- http://m.wap.ghtkgg.cn/jnews/87733.htm
- http://m.wap.ghtkgg.cn/jnews/7646245.htm
- http://m.wap.ghtkgg.cn/jnews/81643.htm
- http://m.wap.ghtkgg.cn/jnews/89977.htm
- http://m.wap.ghtkgg.cn/jnews/80800.htm
- http://m.wap.ghtkgg.cn/jnews/41571.htm
- http://m.wap.ghtkgg.cn/jnews/8029852.htm
- http://m.wap.ghtkgg.cn/jnews/29552.htm
- http://m.wap.ghtkgg.cn/jnews/316489.htm
- http://m.wap.ghtkgg.cn/jnews/3119.htm
- http://m.wap.ghtkgg.cn/jnews/42840.htm
- http://m.wap.ghtkgg.cn/jnews/94351.htm
- http://m.wap.ghtkgg.cn/jnews/3852533.htm
- http://m.wap.ghtkgg.cn/jnews/89172.htm
- http://m.wap.ghtkgg.cn/jnews/0689.htm
- http://m.wap.ghtkgg.cn/jnews/763210.htm
- http://m.wap.ghtkgg.cn/jnews/57878.htm
- http://m.wap.ghtkgg.cn/jnews/47368.htm
- http://m.wap.ghtkgg.cn/jnews/99504.htm
- http://m.wap.ghtkgg.cn/jnews/948716.htm
- http://m.wap.ghtkgg.cn/jnews/81658.htm
- http://m.wap.ghtkgg.cn/jnews/2399.htm
- http://m.wap.ghtkgg.cn/jnews/033691.htm
- http://m.wap.ghtkgg.cn/jnews/782128.htm
- http://m.wap.ghtkgg.cn/jnews/09063.htm
- http://m.wap.ghtkgg.cn/jnews/5508799.htm
- http://m.wap.ghtkgg.cn/jnews/29476.htm
- http://m.wap.ghtkgg.cn/jnews/3031.htm
- http://m.wap.ghtkgg.cn/jnews/9870060.htm
- http://m.wap.ghtkgg.cn/jnews/7553532.htm
- http://m.wap.ghtkgg.cn/jnews/3861772.htm
- http://m.wap.ghtkgg.cn/jnews/38166.htm
- http://m.wap.ghtkgg.cn/jnews/8545673.htm
- http://m.wap.ghtkgg.cn/jnews/5149.htm
- http://m.wap.ghtkgg.cn/jnews/7829.htm
- http://m.wap.ghtkgg.cn/jnews/71710.htm
- http://m.wap.ghtkgg.cn/jnews/94999.htm
- http://m.wap.ghtkgg.cn/jnews/121768.htm
- http://m.wap.ghtkgg.cn/jnews/6519724.htm
- http://m.wap.ghtkgg.cn/jnews/68176.htm
- http://m.wap.ghtkgg.cn/jnews/9485123.htm
- http://m.wap.ghtkgg.cn/jnews/4952846.htm
- http://m.wap.ghtkgg.cn/jnews/4279182.htm
- http://m.wap.ghtkgg.cn/jnews/60699.htm
- http://m.wap.ghtkgg.cn/jnews/7782076.htm
- http://m.wap.ghtkgg.cn/jnews/3233.htm
- http://m.wap.ghtkgg.cn/jnews/9360.htm
- http://m.wap.ghtkgg.cn/jnews/4545.htm
- http://m.wap.ghtkgg.cn/jnews/1844.htm
- http://m.wap.ghtkgg.cn/jnews/15540.htm
- http://m.wap.ghtkgg.cn/jnews/681434.htm
- http://m.wap.ghtkgg.cn/jnews/1694759.htm
- http://m.wap.ghtkgg.cn/jnews/928630.htm
- http://m.wap.ghtkgg.cn/jnews/29314.htm
- http://m.wap.ghtkgg.cn/jnews/23735.htm
- http://m.wap.ghtkgg.cn/jnews/61683.htm
- http://m.wap.ghtkgg.cn/jnews/6778532.htm
- http://m.wap.ghtkgg.cn/jnews/705083.htm
- http://m.wap.ghtkgg.cn/jnews/7674.htm
- http://m.wap.ghtkgg.cn/jnews/7219677.htm
- http://m.wap.ghtkgg.cn/jnews/7134.htm
- http://m.wap.ghtkgg.cn/jnews/500355.htm
- http://m.wap.ghtkgg.cn/jnews/6821.htm
- http://m.wap.ghtkgg.cn/jnews/2722079.htm
- http://m.wap.ghtkgg.cn/jnews/91912.htm
- http://m.wap.ghtkgg.cn/jnews/803268.htm
- http://m.wap.ghtkgg.cn/jnews/502914.htm
- http://m.wap.ghtkgg.cn/jnews/4513509.htm
- http://m.wap.ghtkgg.cn/jnews/7449.htm
- http://m.wap.ghtkgg.cn/jnews/796081.htm
- http://m.wap.ghtkgg.cn/jnews/6959.htm
- http://m.wap.ghtkgg.cn/jnews/12427.htm
- http://m.wap.ghtkgg.cn/jnews/113970.htm
- http://m.wap.ghtkgg.cn/jnews/1717075.htm
- http://m.wap.ghtkgg.cn/jnews/61838.htm
- http://m.wap.ghtkgg.cn/jnews/1760.htm
- http://m.wap.ghtkgg.cn/jnews/378233.htm
- http://m.wap.ghtkgg.cn/jnews/1929801.htm
- http://m.wap.ghtkgg.cn/jnews/7039674.htm
- http://m.wap.ghtkgg.cn/jnews/42499.htm
- http://m.wap.ghtkgg.cn/jnews/3265.htm
- http://m.wap.ghtkgg.cn/jnews/4779.htm
- http://m.wap.ghtkgg.cn/jnews/2204.htm
- http://m.wap.ghtkgg.cn/jnews/1427.htm
- http://m.wap.ghtkgg.cn/jnews/9515.htm
- http://m.wap.ghtkgg.cn/jnews/072756.htm
- http://m.wap.ghtkgg.cn/jnews/1197744.htm
- http://m.wap.ghtkgg.cn/jnews/081328.htm
- http://m.wap.ghtkgg.cn/jnews/9183652.htm
- http://m.wap.ghtkgg.cn/jnews/83902.htm
- http://m.wap.ghtkgg.cn/jnews/5885004.htm
- http://m.wap.ghtkgg.cn/jnews/77257.htm
- http://m.wap.ghtkgg.cn/jnews/68768.htm
- http://m.wap.ghtkgg.cn/jnews/19720.htm
- http://m.wap.ghtkgg.cn/jnews/0244.htm
- http://m.wap.ghtkgg.cn/jnews/8619767.htm
- http://m.wap.ghtkgg.cn/jnews/95146.htm
- http://m.wap.ghtkgg.cn/jnews/9618227.htm
- http://m.wap.ghtkgg.cn/jnews/52197.htm
- http://m.wap.ghtkgg.cn/jnews/57840.htm
- http://m.wap.ghtkgg.cn/jnews/552645.htm
- http://m.wap.ghtkgg.cn/jnews/866353.htm
- http://m.wap.ghtkgg.cn/jnews/40721.htm
- http://m.wap.ghtkgg.cn/jnews/435296.htm
- http://m.wap.ghtkgg.cn/jnews/399736.htm
- http://m.wap.ghtkgg.cn/jnews/2943.htm
- http://m.wap.ghtkgg.cn/jnews/63669.htm
- http://m.wap.ghtkgg.cn/jnews/459379.htm
- http://m.wap.ghtkgg.cn/jnews/1797770.htm
- http://m.wap.ghtkgg.cn/jnews/1535.htm
- http://m.wap.ghtkgg.cn/jnews/1723.htm
- http://m.wap.ghtkgg.cn/jnews/5422.htm
- http://m.wap.ghtkgg.cn/jnews/66251.htm
- http://m.wap.ghtkgg.cn/jnews/0681.htm
- http://m.wap.ghtkgg.cn/jnews/389655.htm
- http://m.wap.ghtkgg.cn/jnews/7876729.htm
- http://m.wap.ghtkgg.cn/jnews/16162.htm
- http://m.wap.ghtkgg.cn/jnews/9550.htm
- http://m.wap.ghtkgg.cn/jnews/3205217.htm
- http://m.wap.ghtkgg.cn/jnews/62150.htm
- http://m.wap.ghtkgg.cn/jnews/0606.htm
- http://m.wap.ghtkgg.cn/jnews/84349.htm
- http://m.wap.ghtkgg.cn/jnews/74023.htm
- http://m.wap.ghtkgg.cn/jnews/637991.htm
- http://m.wap.ghtkgg.cn/jnews/975285.htm
- http://m.wap.ghtkgg.cn/jnews/45491.htm
- http://m.wap.ghtkgg.cn/jnews/57798.htm
- http://m.wap.ghtkgg.cn/jnews/5487.htm
- http://m.wap.ghtkgg.cn/jnews/7080.htm
- http://m.wap.ghtkgg.cn/jnews/837125.htm
- http://m.wap.ghtkgg.cn/jnews/63872.htm
- http://m.wap.ghtkgg.cn/jnews/60295.htm
- http://m.wap.ghtkgg.cn/jnews/76910.htm
- http://m.wap.ghtkgg.cn/jnews/79314.htm
- http://m.wap.ghtkgg.cn/jnews/74952.htm
- http://m.wap.ghtkgg.cn/jnews/760202.htm
- http://m.wap.ghtkgg.cn/jnews/434826.htm
- http://m.wap.ghtkgg.cn/jnews/9523792.htm
- http://m.wap.ghtkgg.cn/jnews/650409.htm
- http://m.wap.ghtkgg.cn/jnews/37149.htm
- http://m.wap.ghtkgg.cn/jnews/1515433.htm
- http://m.wap.ghtkgg.cn/jnews/5226550.htm
- http://m.wap.ghtkgg.cn/jnews/918362.htm
- http://m.wap.ghtkgg.cn/jnews/769467.htm
- http://m.wap.ghtkgg.cn/jnews/54287.htm
- http://m.wap.ghtkgg.cn/jnews/4637.htm
- http://m.wap.ghtkgg.cn/jnews/9647821.htm
- http://m.wap.ghtkgg.cn/jnews/73530.htm
- http://m.wap.ghtkgg.cn/jnews/993595.htm
- http://m.wap.ghtkgg.cn/jnews/9082.htm
- http://m.wap.ghtkgg.cn/jnews/350716.htm
- http://m.wap.ghtkgg.cn/jnews/912693.htm
- http://m.wap.ghtkgg.cn/jnews/0220347.htm
- http://m.wap.ghtkgg.cn/jnews/62913.htm
- http://m.wap.ghtkgg.cn/jnews/6933728.htm
- http://m.wap.ghtkgg.cn/jnews/73270.htm
- http://m.wap.ghtkgg.cn/jnews/7804277.htm
- http://m.wap.ghtkgg.cn/jnews/3058939.htm
- http://m.wap.ghtkgg.cn/jnews/567692.htm
- http://m.wap.ghtkgg.cn/jnews/3925.htm
- http://m.wap.ghtkgg.cn/jnews/5539.htm
- http://m.wap.ghtkgg.cn/jnews/2201518.htm
- http://m.wap.ghtkgg.cn/jnews/2886.htm
- http://m.wap.ghtkgg.cn/jnews/9890851.htm
- http://m.wap.ghtkgg.cn/jnews/557569.htm
- http://m.wap.ghtkgg.cn/jnews/547815.htm
- http://m.wap.ghtkgg.cn/jnews/051560.htm
- http://m.wap.ghtkgg.cn/jnews/946623.htm
- http://m.wap.ghtkgg.cn/jnews/3039753.htm
- http://m.wap.ghtkgg.cn/jnews/8276404.htm
- http://m.wap.ghtkgg.cn/jnews/9473.htm
- http://m.wap.ghtkgg.cn/jnews/20941.htm
- http://m.wap.ghtkgg.cn/jnews/10086.htm
- http://m.wap.ghtkgg.cn/jnews/41512.htm
- http://m.wap.ghtkgg.cn/jnews/94933.htm
- http://m.wap.ghtkgg.cn/jnews/939415.htm
- http://m.wap.ghtkgg.cn/jnews/01193.htm
- http://m.wap.ghtkgg.cn/jnews/4044.htm
- http://m.wap.ghtkgg.cn/jnews/47969.htm
- http://m.wap.ghtkgg.cn/jnews/5843344.htm
- http://m.wap.ghtkgg.cn/jnews/3695907.htm
- http://m.wap.ghtkgg.cn/jnews/1423.htm
- http://m.wap.ghtkgg.cn/jnews/32177.htm
- http://m.wap.ghtkgg.cn/jnews/30392.htm
- http://m.wap.ghtkgg.cn/jnews/9306.htm
- http://m.wap.ghtkgg.cn/jnews/728313.htm
- http://m.wap.ghtkgg.cn/jnews/242108.htm
- http://m.wap.ghtkgg.cn/jnews/865619.htm
- http://m.wap.ghtkgg.cn/jnews/576746.htm
- http://m.wap.ghtkgg.cn/jnews/9645.htm
- http://m.wap.ghtkgg.cn/jnews/8358.htm
- http://m.wap.ghtkgg.cn/jnews/543596.htm
- http://m.wap.ghtkgg.cn/jnews/97306.htm
- http://m.wap.ghtkgg.cn/jnews/66873.htm
- http://m.wap.ghtkgg.cn/jnews/2466335.htm
- http://m.wap.ghtkgg.cn/jnews/0417.htm
- http://m.wap.ghtkgg.cn/jnews/2837330.htm
- http://m.wap.ghtkgg.cn/jnews/993850.htm
- http://m.wap.ghtkgg.cn/jnews/3060622.htm
- http://m.wap.ghtkgg.cn/jnews/35924.htm
- http://m.wap.ghtkgg.cn/jnews/47329.htm
- http://m.wap.ghtkgg.cn/jnews/9405.htm
- http://m.wap.ghtkgg.cn/jnews/42895.htm
- http://m.wap.ghtkgg.cn/jnews/49564.htm
- http://m.wap.ghtkgg.cn/jnews/5199525.htm
- http://m.wap.ghtkgg.cn/jnews/9913131.htm
- http://m.wap.ghtkgg.cn/jnews/046217.htm
- http://m.wap.ghtkgg.cn/jnews/5291288.htm
- http://m.wap.ghtkgg.cn/jnews/0314365.htm
- http://m.wap.ghtkgg.cn/jnews/5626687.htm
- http://m.wap.ghtkgg.cn/jnews/9579.htm
- http://m.wap.ghtkgg.cn/jnews/8432.htm
- http://m.wap.ghtkgg.cn/jnews/5546.htm
- http://m.wap.ghtkgg.cn/jnews/5130.htm
- http://m.wap.ghtkgg.cn/jnews/82066.htm
- http://m.wap.ghtkgg.cn/jnews/054034.htm
- http://m.wap.ghtkgg.cn/jnews/347971.htm
- http://m.wap.ghtkgg.cn/jnews/158031.htm
- http://m.wap.ghtkgg.cn/jnews/598004.htm
- http://m.wap.ghtkgg.cn/jnews/0534649.htm
- http://m.wap.ghtkgg.cn/jnews/43787.htm
- http://m.wap.ghtkgg.cn/jnews/2161.htm
- http://m.wap.ghtkgg.cn/jnews/85989.htm
- http://m.wap.ghtkgg.cn/jnews/3031683.htm
- http://m.wap.ghtkgg.cn/jnews/8900656.htm
- http://m.wap.ghtkgg.cn/jnews/6411.htm
- http://m.wap.ghtkgg.cn/jnews/883974.htm
- http://m.wap.ghtkgg.cn/jnews/42765.htm
- http://m.wap.ghtkgg.cn/jnews/334090.htm
- http://m.wap.ghtkgg.cn/jnews/6495448.htm
- http://m.wap.ghtkgg.cn/jnews/753381.htm

## 项目结构

```
jnews-link-aggregator/
├── app/
│   ├── __init__.py               # Flask 应用工厂，注册蓝图与扩展
│   ├── config.py                 # 配置类定义，支持开发、测试、生产三环境
│   ├── models.py                 # SQLAlchemy 模型：Link, Tag, TaskLog
│   ├── schemas.py                # Pydantic / Marshmallow 序列化模式
│   ├── api/                      # RESTful API 蓝图
│   │   ├── __init__.py
│   │   ├── links.py              # 链接 CRUD 与状态查询端点
│   │   └── tasks.py              # 任务触发与日志查询端点
│   ├── web/                      # Web 管理界面蓝图
│   │   ├── __init__.py
│   │   ├── routes.py             # 仪表板、列表、导出页面路由
│   │   └── templates/            # Jinja2 模板文件
│   │       ├── base.html
│   │       ├── index.html
│   │       └── detail.html
│   ├── core/                     # 核心业务逻辑层
│   │   ├── __init__.py
│   │   ├── checker.py            # 链接健康检查器，支持并发 HEAD 请求
│   │   ├── extractor.py          # 元数据提取器，基于 lxml 与可配置选择器
│   │   ├── importer.py           # 批量导入处理器，支持 JSON / CSV / 纯文本
│   │   └── exporter.py           # 导出器，生成 Markdown / CSV / JSON / RSS
│   └── scheduler/                # 定时任务模块
│       ├── __init__.py
│       └── jobs.py               # APScheduler 任务定义：每日检查、每周报告等
├── data/
│   ├── sample_links.json         # 本批次 300 条新闻链接示例数据
│   └── tags.yaml                 # 预置标签分类映射表
├── tests/
│   ├── __init__.py
│   ├── test_checker.py           # 健康检查器单元测试
│   ├── test_extractor.py         # 元数据提取器测试（含 mock 响应）
│   └── test_api.py               # API 端点集成测试
├── scripts/
│   ├── init_db.py                # 数据库初始化脚本
│   └── cron_wrapper.sh           # 外部 cron 调用包装脚本
├── docs/                         # 完整文档目录，含用户手册与开发者指南
├── .env.example                  # 环境变量配置模板
├── requirements.txt              # 生产依赖列表
├── requirements-dev.txt          # 开发与测试额外依赖
├── manage.py                     # 统一 CLI 入口，集成 flask 命令与自定义扩展
└── README.md                     # 项目主说明文档
```

## 贡献指南

1. 查阅 issue 列表，寻找标记为 "help wanted" 或 "good first issue" 的任务，或提交新的 bug 报告与功能建议。提交前请确认问题未被重复报告。

2. 克隆项目并创建个人功能分支，分支命名遵循 feat/功能简述 或 fix/问题简述 格式。本地开发时请使用 requirements-dev.txt 安装测试与代码检查工具。

3. 编写或修改代码后，运行 pytest 确保所有测试用例通过，新增功能需附带对应单元测试。使用 flake8 与 black 进行代码风格检查与格式化。

4. 更新 docs/ 下相关文档，若修改了 API 行为或配置项，请在对应的用户手册或开发者指南中同步变更说明。

5. 发起 Pull Request 到 main 分支，PR 描述中请清晰说明改动目的、实现方式与测试覆盖情况。至少一名项目维护者审核通过后合入。

## 常见问题

Q: 导入大量链接时出现内存占用过高或导入超时怎么办？
A: 建议将大文件拆分为多个小于 5MB 的小批次导入。项目提供的 import-links 命令支持 --chunk-size 参数，可控制每次批量插入的记录数，默认 500 条。若仍遇超时，可调整 .env 中的 DATABASE_POOL_TIMEOUT 与 WEB_CONCURRENCY 参数。

Q: 元数据提取器无法正确获取部分页面的标题或发布时间，如何自定义解析规则？
A: 项目允许用户通过 data/tags.yaml 文件为特定域名或 URL 前缀配置自定义 CSS 选择器或 XPath 表达式。具体配置格式参考 docs/recipes.md 中的 "自定义解析器" 章节。若普遍性问题，欢迎提交 issue 或 PR 贡献通用规则。

Q: 生产环境下如何将 SQLite 替换为 PostgreSQL？
A: 修改 .env 中的 DATABASE_URL 为 postgresql://user:pass@host/dbname 格式，并确保已安装 psycopg2-binary 依赖。项目模型使用 SQLAlchemy ORM，无需改动代码即可切换。首次启动时 manage.py init-db 会自动创建对应表结构。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
