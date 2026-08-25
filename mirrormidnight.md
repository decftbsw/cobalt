# WebLink Navigator

WebLink Navigator 是一个面向开发者和技术研究人员的结构化外链资源聚合平台，专注于对分散在互联网各处的技术文档、开源项目页面、社区讨论与知识库文章进行系统化归集与索引。该项目不生产原始内容，而是通过人工筛选与自动化校验相结合的方式，将高质量外部链接按照主题域、内容类型和更新频率进行分层组织，最终以清晰目录树和标签体系呈现给用户。项目目标用户包括需要快速查阅特定技术栈官方资料的一线研发人员、从事技术选型调研的架构师，以及希望系统化跟踪某领域动态的研究者。WebLink Navigator 通过解决外链散落、失效频繁、回溯困难这三个核心痛点，帮助用户将碎片化信息浏览转化为可复用的知识检索行为。

## 功能概览

- **多级分类目录体系**：按编程语言、框架生态、基础设施、云服务、学术论文等顶层分类，每级目录下再按细分主题拆分，确保每个链接都有明确的归属路径。

- **链接活性健康检查**：每日定时对收录的全部外链发起 HEAD 请求，检测 HTTP 状态码变化，自动标记 4xx/5xx 异常链接，并在管理后台生成失效报告。

- **全文元数据提取**：对每个外链页面抓取标题、描述、作者、发布时间、正文关键词，并存入结构化字段，支持后续高级筛选与聚合统计。

- **标签与多维度筛选**：支持为单个链接打上多个自定义标签（如 "官方文档" "最佳实践" "性能调优" "安全加固"），允许用户按标签组合快速定位资源。

- **变更历史追溯**：记录每个外链的添加时间、最后校验时间、状态变更日志，支持按时间线回看某链接的可用性变化，便于排查外部资源下架或迁移情况。

- **开放数据导出接口**：提供 RESTful API 和 CSV 批量导出能力，允许用户将链接列表及其元数据导入到个人知识管理工具、监控系统或自定义分析脚本中。

- **用户收藏与备注**：注册用户可对任意链接添加私人备注和收藏标记，收藏夹支持自定义分组，满足个人化知识整理需求。

## 应用场景

- **技术选型调研**：团队在评估消息队列中间件时，可通过 WebLink Navigator 快速筛选出 "消息队列" 分类下所有标记为 "官方文档" 和 "性能对比" 的链接，一键打开 RabbitMQ、Kafka、Pulsar 的官方手册与第三方 benchmark 报告，大幅减少搜索引擎重复检索时间。

- **日常开发查阅**：前端开发者在处理浏览器兼容性问题时，可直接进入 "Web API" 目录，找到 MDN、Can I Use、W3C 规范等常驻链接，配合标签过滤 "事件模型" "DOM 操作" 等细项，迅速定位到准确说明页，避免在历史记录中反复翻找。

- **离线知识库构建**：运维人员可定期通过 API 导出 "Linux 内核调优" 和 "Kubernetes 故障排查" 两个分类下的全部链接列表，结合 wget 镜像工具制作内部离线文档站点，供无外网权限的生产环境服务器维护时参考。

- **开源项目 README 外链维护**：开源项目维护者可将 WebLink Navigator 作为项目文档中 "相关资源" 章节的后台数据源，通过嵌入动态标签过滤链接，确保 README 中的外部引用地址始终经过活性检测，避免用户点击到已失效的旧链接。

## 快速开始

以下命令演示如何在本地环境中克隆项目仓库、安装依赖并启动开发服务。

```bash
# 克隆仓库到本地
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装后端依赖 (Python)
pip install -r requirements.txt

# 安装前端依赖 (Node.js)
cd frontend
npm install
cd ..

# 初始化本地配置文件
cp .env.example .env
# 编辑 .env 文件，填写数据库连接等必要变量

# 执行数据库迁移
python manage.py migrate

# 导入示例链接数据
python manage.py loaddata sample_links.json

# 启动开发服务器 (后端)
python manage.py runserver 0.0.0.0:8000

# 启动前端开发服务 (另开终端)
cd frontend
npm run dev
```

访问 http://localhost:8000 查看后端 API 文档，访问 http://localhost:3000 进入前端界面。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.10 或更高 | 后端运行环境，核心业务逻辑及链接检测服务依赖 |
| Node.js | 18.x 或 20.x LTS | 前端构建与开发服务运行时，使用 Vite 作为构建工具 |
| PostgreSQL | 14.x 或更高 | 主数据库，存储链接元数据、标签、用户信息及变更日志 |
| Redis | 6.2 或更高 | 缓存与消息队列，用于链接健康检查任务的异步调度和结果暂存 |
| Nginx | 1.20 或更高 | 生产环境反向代理，用于静态资源托管和 API 负载均衡（开发环境可选） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户手册 | /docs/user/quick-start.md | 如何注册账号、添加第一个外链、使用标签筛选和收藏功能 |
| 用户手册 | /docs/user/link-check.md | 链接健康检查的触发方式、结果解读以及异常告警配置方法 |
| 管理员指南 | /docs/admin/deployment.md | 生产环境部署流程，包括 Nginx 配置、SSL 证书安装、系统服务注册 |
| 管理员指南 | /docs/admin/data-maintenance.md | 如何批量导入/导出链接数据、清理失效记录、重建索引 |
| 开发者文档 | /docs/dev/api-reference.md | RESTful API 的端点列表、请求/响应格式、鉴权方式与速率限制说明 |
| 开发者文档 | /docs/dev/contribution-guide.md | 插件化扩展机制、自定义健康检查策略的实现步骤与测试规范 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/405805.htm
- http://m.wap.bwbkj.cn/snews/200967.htm
- http://m.wap.bwbkj.cn/snews/08461.htm
- http://m.wap.bwbkj.cn/snews/7162.htm
- http://m.wap.bwbkj.cn/snews/40776.htm
- http://m.wap.bwbkj.cn/snews/633805.htm
- http://m.wap.bwbkj.cn/snews/5019.htm
- http://m.wap.bwbkj.cn/snews/0683.htm
- http://m.wap.bwbkj.cn/snews/899093.htm
- http://m.wap.bwbkj.cn/snews/69525.htm
- http://m.wap.bwbkj.cn/snews/8044.htm
- http://m.wap.bwbkj.cn/snews/9102861.htm
- http://m.wap.bwbkj.cn/snews/50935.htm
- http://m.wap.bwbkj.cn/snews/66772.htm
- http://m.wap.bwbkj.cn/snews/0494936.htm
- http://m.wap.bwbkj.cn/snews/9705243.htm
- http://m.wap.bwbkj.cn/snews/95705.htm
- http://m.wap.bwbkj.cn/snews/8585.htm
- http://m.wap.bwbkj.cn/snews/5729987.htm
- http://m.wap.bwbkj.cn/snews/34135.htm
- http://m.wap.bwbkj.cn/snews/5732145.htm
- http://m.wap.bwbkj.cn/snews/93765.htm
- http://m.wap.bwbkj.cn/snews/1257.htm
- http://m.wap.bwbkj.cn/snews/28951.htm
- http://m.wap.bwbkj.cn/snews/5740.htm
- http://m.wap.bwbkj.cn/snews/16488.htm
- http://m.wap.bwbkj.cn/snews/642970.htm
- http://m.wap.bwbkj.cn/snews/25799.htm
- http://m.wap.bwbkj.cn/snews/129887.htm
- http://m.wap.bwbkj.cn/snews/5755.htm
- http://m.wap.bwbkj.cn/snews/402949.htm
- http://m.wap.bwbkj.cn/snews/04737.htm
- http://m.wap.bwbkj.cn/snews/526242.htm
- http://m.wap.bwbkj.cn/snews/46874.htm
- http://m.wap.bwbkj.cn/snews/9800334.htm
- http://m.wap.bwbkj.cn/snews/1066436.htm
- http://m.wap.bwbkj.cn/snews/78287.htm
- http://m.wap.bwbkj.cn/snews/4847297.htm
- http://m.wap.bwbkj.cn/snews/1524.htm
- http://m.wap.bwbkj.cn/snews/9625.htm
- http://m.wap.bwbkj.cn/snews/3644.htm
- http://m.wap.bwbkj.cn/snews/4739577.htm
- http://m.wap.bwbkj.cn/snews/8436443.htm
- http://m.wap.bwbkj.cn/snews/313036.htm
- http://m.wap.bwbkj.cn/snews/6439.htm
- http://m.wap.bwbkj.cn/snews/36195.htm
- http://m.wap.bwbkj.cn/snews/96701.htm
- http://m.wap.bwbkj.cn/snews/30587.htm
- http://m.wap.bwbkj.cn/snews/118152.htm
- http://m.wap.bwbkj.cn/snews/141755.htm
- http://m.wap.bwbkj.cn/snews/6912308.htm
- http://m.wap.bwbkj.cn/snews/14805.htm
- http://m.wap.bwbkj.cn/snews/25434.htm
- http://m.wap.bwbkj.cn/snews/2300294.htm
- http://m.wap.bwbkj.cn/snews/49602.htm
- http://m.wap.bwbkj.cn/snews/18709.htm
- http://m.wap.bwbkj.cn/snews/2279279.htm
- http://m.wap.bwbkj.cn/snews/9696490.htm
- http://m.wap.bwbkj.cn/snews/2006.htm
- http://m.wap.bwbkj.cn/snews/277954.htm
- http://m.wap.bwbkj.cn/snews/8322222.htm
- http://m.wap.bwbkj.cn/snews/923961.htm
- http://m.wap.bwbkj.cn/snews/2714229.htm
- http://m.wap.bwbkj.cn/snews/1628.htm
- http://m.wap.bwbkj.cn/snews/6110.htm
- http://m.wap.bwbkj.cn/snews/156003.htm
- http://m.wap.bwbkj.cn/snews/6526970.htm
- http://m.wap.bwbkj.cn/snews/8515093.htm
- http://m.wap.bwbkj.cn/snews/3026.htm
- http://m.wap.bwbkj.cn/snews/19963.htm
- http://m.wap.bwbkj.cn/snews/2159.htm
- http://m.wap.bwbkj.cn/snews/58016.htm
- http://m.wap.bwbkj.cn/snews/800118.htm
- http://m.wap.bwbkj.cn/snews/2666.htm
- http://m.wap.bwbkj.cn/snews/44777.htm
- http://m.wap.bwbkj.cn/snews/57409.htm
- http://m.wap.bwbkj.cn/snews/13297.htm
- http://m.wap.bwbkj.cn/snews/847643.htm
- http://m.wap.bwbkj.cn/snews/6321019.htm
- http://m.wap.bwbkj.cn/snews/6463665.htm
- http://m.wap.bwbkj.cn/snews/8677.htm
- http://m.wap.bwbkj.cn/snews/915653.htm
- http://m.wap.bwbkj.cn/snews/73835.htm
- http://m.wap.bwbkj.cn/snews/74927.htm
- http://m.wap.bwbkj.cn/snews/283904.htm
- http://m.wap.bwbkj.cn/snews/8791.htm
- http://m.wap.bwbkj.cn/snews/841820.htm
- http://m.wap.bwbkj.cn/snews/6180.htm
- http://m.wap.bwbkj.cn/snews/6665.htm
- http://m.wap.bwbkj.cn/snews/9508.htm
- http://m.wap.bwbkj.cn/snews/11230.htm
- http://m.wap.bwbkj.cn/snews/6686.htm
- http://m.wap.bwbkj.cn/snews/9773.htm
- http://m.wap.bwbkj.cn/snews/3229.htm
- http://m.wap.bwbkj.cn/snews/76359.htm
- http://m.wap.bwbkj.cn/snews/24580.htm
- http://m.wap.bwbkj.cn/snews/5843280.htm
- http://m.wap.bwbkj.cn/snews/3189115.htm
- http://m.wap.bwbkj.cn/snews/74542.htm
- http://m.wap.bwbkj.cn/snews/8522854.htm
- http://m.wap.bwbkj.cn/snews/0618065.htm
- http://m.wap.bwbkj.cn/snews/21347.htm
- http://m.wap.bwbkj.cn/snews/0471.htm
- http://m.wap.bwbkj.cn/snews/42367.htm
- http://m.wap.bwbkj.cn/snews/0801023.htm
- http://m.wap.bwbkj.cn/snews/6838.htm
- http://m.wap.bwbkj.cn/snews/70347.htm
- http://m.wap.bwbkj.cn/snews/46064.htm
- http://m.wap.bwbkj.cn/snews/62396.htm
- http://m.wap.bwbkj.cn/snews/6633050.htm
- http://m.wap.bwbkj.cn/snews/0760214.htm
- http://m.wap.bwbkj.cn/snews/6549808.htm
- http://m.wap.bwbkj.cn/snews/549299.htm
- http://m.wap.bwbkj.cn/snews/18853.htm
- http://m.wap.bwbkj.cn/snews/145087.htm
- http://m.wap.bwbkj.cn/snews/0251.htm
- http://m.wap.bwbkj.cn/snews/35500.htm
- http://m.wap.bwbkj.cn/snews/95707.htm
- http://m.wap.bwbkj.cn/snews/3198676.htm
- http://m.wap.bwbkj.cn/snews/7148.htm
- http://m.wap.bwbkj.cn/snews/0107198.htm
- http://m.wap.bwbkj.cn/snews/8405.htm
- http://m.wap.bwbkj.cn/snews/89822.htm
- http://m.wap.bwbkj.cn/snews/11216.htm
- http://m.wap.bwbkj.cn/snews/434957.htm
- http://m.wap.bwbkj.cn/snews/3183.htm
- http://m.wap.bwbkj.cn/snews/654785.htm
- http://m.wap.bwbkj.cn/snews/91081.htm
- http://m.wap.bwbkj.cn/snews/629212.htm
- http://m.wap.bwbkj.cn/snews/3566731.htm
- http://m.wap.bwbkj.cn/snews/44012.htm
- http://m.wap.bwbkj.cn/snews/4495.htm
- http://m.wap.bwbkj.cn/snews/8654131.htm
- http://m.wap.bwbkj.cn/snews/39580.htm
- http://m.wap.bwbkj.cn/snews/7757269.htm
- http://m.wap.bwbkj.cn/snews/2961.htm
- http://m.wap.bwbkj.cn/snews/784317.htm
- http://m.wap.bwbkj.cn/snews/738777.htm
- http://m.wap.bwbkj.cn/snews/9586.htm
- http://m.wap.bwbkj.cn/snews/8506071.htm
- http://m.wap.bwbkj.cn/snews/9417835.htm
- http://m.wap.bwbkj.cn/snews/9500009.htm
- http://m.wap.bwbkj.cn/snews/1136516.htm
- http://m.wap.bwbkj.cn/snews/22036.htm
- http://m.wap.bwbkj.cn/snews/204116.htm
- http://m.wap.bwbkj.cn/snews/9979886.htm
- http://m.wap.bwbkj.cn/snews/61109.htm
- http://m.wap.bwbkj.cn/snews/7087038.htm
- http://m.wap.bwbkj.cn/snews/6330.htm
- http://m.wap.bwbkj.cn/snews/6924634.htm
- http://m.wap.bwbkj.cn/snews/06726.htm
- http://m.wap.bwbkj.cn/snews/21108.htm
- http://m.wap.bwbkj.cn/snews/641427.htm
- http://m.wap.bwbkj.cn/snews/948370.htm
- http://m.wap.bwbkj.cn/snews/0947.htm
- http://m.wap.bwbkj.cn/snews/37317.htm
- http://m.wap.bwbkj.cn/snews/01328.htm
- http://m.wap.bwbkj.cn/snews/0567.htm
- http://m.wap.bwbkj.cn/snews/6588.htm
- http://m.wap.bwbkj.cn/snews/7960770.htm
- http://m.wap.bwbkj.cn/snews/5728.htm
- http://m.wap.bwbkj.cn/snews/5431.htm
- http://m.wap.bwbkj.cn/snews/6641739.htm
- http://m.wap.bwbkj.cn/snews/9255.htm
- http://m.wap.bwbkj.cn/snews/6105.htm
- http://m.wap.bwbkj.cn/snews/3435512.htm
- http://m.wap.bwbkj.cn/snews/5088908.htm
- http://m.wap.bwbkj.cn/snews/4398405.htm
- http://m.wap.bwbkj.cn/snews/221727.htm
- http://m.wap.bwbkj.cn/snews/8746.htm
- http://m.wap.bwbkj.cn/snews/996213.htm
- http://m.wap.bwbkj.cn/snews/930685.htm
- http://m.wap.bwbkj.cn/snews/6288.htm
- http://m.wap.bwbkj.cn/snews/3776642.htm
- http://m.wap.bwbkj.cn/snews/07483.htm
- http://m.wap.bwbkj.cn/snews/8997642.htm
- http://m.wap.bwbkj.cn/snews/2500567.htm
- http://m.wap.bwbkj.cn/snews/2459.htm
- http://m.wap.bwbkj.cn/snews/5294.htm
- http://m.wap.bwbkj.cn/snews/1174253.htm
- http://m.wap.bwbkj.cn/snews/1650399.htm
- http://m.wap.bwbkj.cn/snews/7675.htm
- http://m.wap.bwbkj.cn/snews/95423.htm
- http://m.wap.bwbkj.cn/snews/8487855.htm
- http://m.wap.bwbkj.cn/snews/2769780.htm
- http://m.wap.bwbkj.cn/snews/4510.htm
- http://m.wap.bwbkj.cn/snews/0579770.htm
- http://m.wap.bwbkj.cn/snews/124366.htm
- http://m.wap.bwbkj.cn/snews/23776.htm
- http://m.wap.bwbkj.cn/snews/505043.htm
- http://m.wap.bwbkj.cn/snews/60865.htm
- http://m.wap.bwbkj.cn/snews/4266443.htm
- http://m.wap.bwbkj.cn/snews/767744.htm
- http://m.wap.bwbkj.cn/snews/63678.htm
- http://m.wap.bwbkj.cn/snews/9627237.htm
- http://m.wap.bwbkj.cn/snews/6952.htm
- http://m.wap.bwbkj.cn/snews/07043.htm
- http://m.wap.bwbkj.cn/snews/3979059.htm
- http://m.wap.bwbkj.cn/snews/8265387.htm
- http://m.wap.bwbkj.cn/snews/7932772.htm
- http://m.wap.bwbkj.cn/snews/242277.htm
- http://m.wap.bwbkj.cn/snews/7108.htm
- http://m.wap.bwbkj.cn/snews/032390.htm
- http://m.wap.bwbkj.cn/snews/450440.htm
- http://m.wap.bwbkj.cn/snews/21161.htm
- http://m.wap.bwbkj.cn/snews/3812890.htm
- http://m.wap.bwbkj.cn/snews/535592.htm
- http://m.wap.bwbkj.cn/snews/1253438.htm
- http://m.wap.bwbkj.cn/snews/4041.htm
- http://m.wap.bwbkj.cn/snews/1476917.htm
- http://m.wap.bwbkj.cn/snews/387745.htm
- http://m.wap.bwbkj.cn/snews/4752.htm
- http://m.wap.bwbkj.cn/snews/3232.htm
- http://m.wap.bwbkj.cn/snews/2713.htm
- http://m.wap.bwbkj.cn/snews/12055.htm
- http://m.wap.bwbkj.cn/snews/5530.htm
- http://m.wap.bwbkj.cn/snews/042590.htm
- http://m.wap.bwbkj.cn/snews/0559662.htm
- http://m.wap.bwbkj.cn/snews/16348.htm
- http://m.wap.bwbkj.cn/snews/450877.htm
- http://m.wap.bwbkj.cn/snews/10221.htm
- http://m.wap.bwbkj.cn/snews/8751691.htm
- http://m.wap.bwbkj.cn/snews/9972.htm
- http://m.wap.bwbkj.cn/snews/66685.htm
- http://m.wap.bwbkj.cn/snews/5325.htm
- http://m.wap.bwbkj.cn/snews/924858.htm
- http://m.wap.bwbkj.cn/snews/2350.htm
- http://m.wap.bwbkj.cn/snews/3540.htm
- http://m.wap.bwbkj.cn/snews/35801.htm
- http://m.wap.bwbkj.cn/snews/4547.htm
- http://m.wap.bwbkj.cn/snews/06075.htm
- http://m.wap.bwbkj.cn/snews/3857.htm
- http://m.wap.bwbkj.cn/snews/94369.htm
- http://m.wap.bwbkj.cn/snews/9478.htm
- http://m.wap.bwbkj.cn/snews/745343.htm
- http://m.wap.bwbkj.cn/snews/9417.htm
- http://m.wap.bwbkj.cn/snews/707581.htm
- http://m.wap.bwbkj.cn/snews/3012762.htm
- http://m.wap.bwbkj.cn/snews/9318733.htm
- http://m.wap.bwbkj.cn/snews/84657.htm
- http://m.wap.bwbkj.cn/snews/2517.htm
- http://m.wap.bwbkj.cn/snews/6673.htm
- http://m.wap.bwbkj.cn/snews/0546.htm
- http://m.wap.bwbkj.cn/snews/246932.htm
- http://m.wap.bwbkj.cn/snews/584341.htm
- http://m.wap.bwbkj.cn/snews/29738.htm
- http://m.wap.bwbkj.cn/snews/24652.htm
- http://m.wap.bwbkj.cn/snews/772082.htm
- http://m.wap.bwbkj.cn/snews/1691433.htm
- http://m.wap.bwbkj.cn/snews/8614.htm
- http://m.wap.bwbkj.cn/snews/1564.htm
- http://m.wap.bwbkj.cn/snews/47068.htm
- http://m.wap.bwbkj.cn/snews/0384356.htm
- http://m.wap.bwbkj.cn/snews/647744.htm
- http://m.wap.bwbkj.cn/snews/8723351.htm
- http://m.wap.bwbkj.cn/snews/204359.htm
- http://m.wap.bwbkj.cn/snews/0680.htm
- http://m.wap.bwbkj.cn/snews/126904.htm
- http://m.wap.bwbkj.cn/snews/695405.htm
- http://m.wap.bwbkj.cn/snews/292151.htm
- http://m.wap.bwbkj.cn/snews/45271.htm
- http://m.wap.bwbkj.cn/snews/2808229.htm
- http://m.wap.bwbkj.cn/snews/27206.htm
- http://m.wap.bwbkj.cn/snews/6482.htm
- http://m.wap.bwbkj.cn/snews/0310798.htm
- http://m.wap.bwbkj.cn/snews/9466.htm
- http://m.wap.bwbkj.cn/snews/2359.htm
- http://m.wap.bwbkj.cn/snews/1892433.htm
- http://m.wap.bwbkj.cn/snews/6675890.htm
- http://m.wap.bwbkj.cn/snews/64603.htm
- http://m.wap.bwbkj.cn/snews/523895.htm
- http://m.wap.bwbkj.cn/snews/82022.htm
- http://m.wap.bwbkj.cn/snews/6012.htm
- http://m.wap.bwbkj.cn/snews/7432733.htm
- http://m.wap.bwbkj.cn/snews/68560.htm
- http://m.wap.bwbkj.cn/snews/46500.htm
- http://m.wap.bwbkj.cn/snews/0757715.htm
- http://m.wap.bwbkj.cn/snews/0300.htm
- http://m.wap.bwbkj.cn/snews/0327.htm
- http://m.wap.bwbkj.cn/snews/701790.htm
- http://m.wap.bwbkj.cn/snews/5183.htm
- http://m.wap.bwbkj.cn/snews/612068.htm
- http://m.wap.bwbkj.cn/snews/25032.htm
- http://m.wap.bwbkj.cn/snews/7328337.htm
- http://m.wap.bwbkj.cn/snews/79610.htm
- http://m.wap.bwbkj.cn/snews/80253.htm
- http://m.wap.bwbkj.cn/snews/5189.htm
- http://m.wap.bwbkj.cn/snews/6079503.htm
- http://m.wap.bwbkj.cn/snews/6734923.htm
- http://m.wap.bwbkj.cn/snews/6656222.htm
- http://m.wap.bwbkj.cn/snews/13785.htm
- http://m.wap.bwbkj.cn/snews/87387.htm
- http://m.wap.bwbkj.cn/snews/32050.htm
- http://m.wap.bwbkj.cn/snews/3940146.htm
- http://m.wap.bwbkj.cn/snews/633823.htm
- http://m.wap.bwbkj.cn/snews/326995.htm
- http://m.wap.bwbkj.cn/snews/364841.htm
- http://m.wap.bwbkj.cn/snews/4708.htm
- http://m.wap.bwbkj.cn/snews/70493.htm
- http://m.wap.bwbkj.cn/snews/339645.htm

## 项目结构

```
weblink-navigator/
├── backend/                          # 后端服务根目录
│   ├── api/                          # RESTful API 路由与视图
│   │   ├── v1/                       # API v1 版本端点
│   │   │   ├── links.py              # 链接增删改查及校验接口
│   │   │   ├── tags.py               # 标签管理接口
│   │   │   └── health.py             # 健康检查状态查询接口
│   │   └── middleware/               # 认证与速率限制中间件
│   ├── core/                         # 核心业务逻辑层
│   │   ├── checker/                  # 链接活性检测引擎
│   │   │   ├── http_client.py        # 异步 HTTP 请求封装
│   │   │   └── scheduler.py          # 定时任务调度器 (基于 APScheduler)
│   │   ├── parser/                   # 元数据提取器
│   │   │   ├── html_parser.py        # HTML 标题/描述解析
│   │   │   └── keyword_extract.py    # 关键词自动提取
│   │   └── exporter/                 # 数据导出模块 (CSV / JSON / API)
│   ├── models/                       # 数据库模型 (SQLAlchemy ORM)
│   │   ├── link.py                   # 链接实体及状态字段
│   │   ├── tag.py                    # 标签实体与多对多关联
│   │   └── user.py                   # 用户、收藏夹与备注
│   ├── migrations/                   # Alembic 数据库迁移脚本
│   ├── tests/                        # 单元测试与集成测试
│   │   ├── test_checker.py           # 健康检查功能测试
│   │   └── test_api.py               # API 端点测试
│   ├── requirements.txt              # Python 依赖列表
│   └── config.py                     # 全局配置 (环境变量映射)
├── frontend/                         # 前端单页应用根目录
│   ├── src/                          # 源代码目录
│   │   ├── pages/                    # 页面组件 (Dashboard / LinkList / Detail)
│   │   ├── components/               # 可复用 UI 组件 (筛选栏 / 标签云 / 状态徽标)
│   │   ├── stores/                   # Pinia 状态管理 (用户偏好 / 筛选条件)
│   │   ├── api/                      # 与后端 API 交互的客户端封装
│   │   └── assets/                   # 静态资源 (CSS 变量 / 图标)
│   ├── index.html                    # 入口 HTML
│   ├── package.json                  # Node.js 依赖及脚本
│   └── vite.config.js                # Vite 构建配置
├── docker/                           # 容器化部署配置
│   ├── Dockerfile.backend            # 后端镜像构建文件
│   ├── Dockerfile.frontend           # 前端镜像构建文件
│   └── docker-compose.yml            # 多容器编排 (PostgreSQL / Redis / Nginx)
├── docs/                             # 项目文档目录
│   ├── user/                         # 用户手册
│   ├── admin/                        # 管理员部署与维护指南
│   └── dev/                          # 开发者贡献文档
├── scripts/                          # 辅助运维脚本
│   ├── init_db.py                    # 初始化数据库表及默认标签
│   └── import_legacy.py              # 从旧格式 CSV 导入链接数据
├── .env.example                      # 环境变量模板文件
├── .gitignore                        # Git 忽略规则
└── README.md                         # 本文件
```

## 贡献指南

1. 查阅开发者文档中 "插件化扩展机制" 一节，了解自定义健康检查策略的抽象基类与注册方式，然后在 backend/core/checker/ 目录下新建策略文件，继承 BaseChecker 并实现 check() 方法。

2. 运行后端测试套件确保新增策略不破坏现有功能：在 backend/ 目录下执行 pytest tests/，所有测试用例应保持通过状态，若涉及外部网络请求需使用 mock 对象隔离。

3. 提交代码前执行代码风格检查，后端使用 flake8 和 black，前端使用 eslint 和 prettier，确保与项目现有风格一致。提交信息遵循 Conventional Commits 规范，类型包括 feat / fix / docs / refactor / test。

4. 在 GitHub 仓库中创建 Pull Request，描述中需注明变更动机、实现方案以及手动测试步骤。若变更涉及 API 接口，需同步更新 /docs/dev/api-reference.md 中的对应示例。

5. 等待至少一位项目维护者进行 Code Review，根据反馈修改直至获得批准。合并后，CI 流水线将自动构建镜像并部署到 staging 环境进行冒烟测试。

## 常见问题

**Q: 链接健康检查会访问原始服务器，是否会对目标站点造成压力？**

A: 系统对每个链接的检查频率为每 24 小时一次，且所有请求均附带标准的 User-Agent 头，明确标识为 WebLink Navigator 的活性探测。同一目标域名的多个链接会被分散在时间窗口内随机执行，避免集中突发请求。若目标站点有 robots.txt 明确禁止爬取，系统将自动跳过该域名的检查并记录警告日志。

**Q: 用户能否导入自己维护的外链集合？**

A: 可以。平台提供批量导入功能，支持 CSV 和 JSON 两种格式。导入模板需包含 url、title、category 和 tags 四个必要字段。导入过程中系统会自动去重（基于 url 的标准化形式），并触发一次即时健康检查以填充初始状态。导入记录可在用户中心的 "导入历史" 中查看，包含成功数量、跳过数量及错误明细。

**Q: 如果某个外链永久失效，系统如何通知维护者？**

A: 当链接连续三次检查均返回 4xx 或 5xx 状态码时，系统会将其标记为 "确认失效" 状态，并通过管理后台的 "待处理告警" 面板集中展示。同时，配置了邮件通知的管理员会收到每日汇总报告，包含新增失效链接的列表及最后有效响应时间。失效链接不会被自动删除，而是保留以供追溯，但会在前端界面默认隐藏，仅管理员可见。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:10
