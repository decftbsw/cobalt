# JNews Aggregator

JNews Aggregator 是一个面向中文互联网资讯聚合与导航的开源工具，专注于从指定的新闻源服务器（jnews）批量获取、整理和展示结构化新闻条目。该项目主要服务于需要快速浏览大量新闻标题、按分类筛选资讯内容、以及对外链资源进行集中管理的个人站长、内容运营人员和信息分析爱好者。通过提供统一的访问入口和标准化的数据输出格式，JNews Aggregator 降低了从分散URL中提取新闻信息的操作成本，并支持将外部链接整合为可检索、可分类的内部知识库。

## 功能概览

**批量URL导入解析**：支持从文本文件或标准输入流中批量导入新闻URL，自动识别URL中的数字ID与分类路径，并提取元数据。

**新闻列表分页展示**：将导入的新闻条目生成分页列表，每页显示固定数量的条目，支持上一页、下一页及跳转功能。

**关键词快速检索**：基于标题或正文摘要进行关键词匹配检索，返回相关性排序后的结果集。

**分类标签自动生成**：根据URL路径中的/jnews/前缀和后缀的数字规律，自动为每条新闻打上分类标签，便于后续筛选。

**外部资源外链管理**：将用户提供的所有新闻URL作为外链资源统一存储、去重和验证，并提供健康检查接口。

**数据导出为结构化格式**：支持将新闻列表导出为JSON、CSV或Markdown表格格式，方便二次处理或存档。

**自定义黑名单过滤**：支持配置域名或关键词黑名单，在导入阶段自动过滤不符合规则的URL条目。

## 应用场景

个人站长构建每日新闻简报：个人站长可以每日将采集到的新闻URL列表导入JNews Aggregator，系统自动生成带时间戳的新闻简报页面，直接部署为网站的子栏目，减少手动编辑工作量。

内容运营团队内部资讯共享：内容运营团队成员分别从不同渠道收集新闻URL，统一录入JNews Aggregator后，系统生成共享的新闻看板，支持按标签分类浏览，提升团队信息同步效率。

信息分析项目的数据源管理：在进行舆情分析或趋势研究时，研究人员可将大量新闻URL作为数据源导入系统，利用导出功能将结构化数据对接至数据分析流水线，实现自动化处理。

教育机构的信息检索教学案例：在信息检索或网络爬虫课程中，教师可使用JNews Aggregator作为示例项目，演示URL解析、数据清洗和列表渲染等基础技术概念，帮助学生理解实际工程实现。

个人知识库的外链备份中心：个人用户可将日常阅读的新闻链接统一收纳至JNews Aggregator，配合分类标签功能构建个人外链知识库，避免链接丢失或遗忘。

## 快速开始

```bash
# 克隆代码仓库
git clone https://github.com/your-org/jnews-aggregator.git

# 进入项目根目录
cd jnews-aggregator

# 安装项目依赖（使用 pip 安装 Python 依赖）
pip install -r requirements.txt

# 启动开发服务器（默认监听 127.0.0.1:5000）
python app.py

# 或者使用 Gunicorn 启动生产环境服务
gunicorn -w 4 -b 0.0.0.0:8080 app:app
```

## 安装要求

| 依赖项 | 必需版本 | 说明 |
|--------|----------|------|
| Python | 3.8 或更高 | 核心运行环境，用于执行应用逻辑和依赖管理 |
| Flask | 2.2.0 或更高 | Web 框架，提供路由、请求处理和模板渲染能力 |
| requests | 2.28.0 或更高 | 用于发起对外部新闻URL的HTTP请求，验证链接可用性 |
| beautifulsoup4 | 4.11.0 或更高 | 解析新闻页面HTML内容，提取标题和正文摘要 |
| lxml | 4.9.0 或更高 | 作为BeautifulSoup的解析器后端，提供高性能XML/HTML解析 |
| markdown | 3.4.0 或更高 | 将Markdown格式的新闻正文渲染为HTML，用于展示 |
| pytest | 7.2.0 或更高 | 单元测试框架，用于运行项目测试套件（开发依赖） |
| flake8 | 6.0.0 或更高 | 代码风格检查工具，用于保持代码规范（开发依赖） |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | /docs/user-guide.md | 如何导入新闻URL、如何浏览列表、如何进行检索和导出数据 |
| 部署指南 | /docs/deployment.md | 如何在生产环境部署JNews Aggregator，包括Nginx反向代理和Systemd服务配置 |
| API参考 | /docs/api-reference.md | 项目提供了哪些RESTful API接口，请求参数和响应格式分别是什么 |
| 开发指南 | /docs/development.md | 如何扩展新的解析器、如何修改分类逻辑、如何提交代码贡献 |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/1999525.htm
- http://m.wap.ghtkgg.cn/jnews/6461.htm
- http://m.wap.ghtkgg.cn/jnews/3321.htm
- http://m.wap.ghtkgg.cn/jnews/4928.htm
- http://m.wap.ghtkgg.cn/jnews/9723819.htm
- http://m.wap.ghtkgg.cn/jnews/77236.htm
- http://m.wap.ghtkgg.cn/jnews/230492.htm
- http://m.wap.ghtkgg.cn/jnews/55884.htm
- http://m.wap.ghtkgg.cn/jnews/884513.htm
- http://m.wap.ghtkgg.cn/jnews/215517.htm
- http://m.wap.ghtkgg.cn/jnews/27902.htm
- http://m.wap.ghtkgg.cn/jnews/2521.htm
- http://m.wap.ghtkgg.cn/jnews/0707554.htm
- http://m.wap.ghtkgg.cn/jnews/054111.htm
- http://m.wap.ghtkgg.cn/jnews/8069.htm
- http://m.wap.ghtkgg.cn/jnews/302544.htm
- http://m.wap.ghtkgg.cn/jnews/1816180.htm
- http://m.wap.ghtkgg.cn/jnews/552124.htm
- http://m.wap.ghtkgg.cn/jnews/64846.htm
- http://m.wap.ghtkgg.cn/jnews/23966.htm
- http://m.wap.ghtkgg.cn/jnews/747239.htm
- http://m.wap.ghtkgg.cn/jnews/1370124.htm
- http://m.wap.ghtkgg.cn/jnews/174135.htm
- http://m.wap.ghtkgg.cn/jnews/796549.htm
- http://m.wap.ghtkgg.cn/jnews/32478.htm
- http://m.wap.ghtkgg.cn/jnews/27550.htm
- http://m.wap.ghtkgg.cn/jnews/8530846.htm
- http://m.wap.ghtkgg.cn/jnews/5979977.htm
- http://m.wap.ghtkgg.cn/jnews/190906.htm
- http://m.wap.ghtkgg.cn/jnews/86543.htm
- http://m.wap.ghtkgg.cn/jnews/127821.htm
- http://m.wap.ghtkgg.cn/jnews/9617957.htm
- http://m.wap.ghtkgg.cn/jnews/9484.htm
- http://m.wap.ghtkgg.cn/jnews/7730607.htm
- http://m.wap.ghtkgg.cn/jnews/1309.htm
- http://m.wap.ghtkgg.cn/jnews/22343.htm
- http://m.wap.ghtkgg.cn/jnews/647619.htm
- http://m.wap.ghtkgg.cn/jnews/8075.htm
- http://m.wap.ghtkgg.cn/jnews/94685.htm
- http://m.wap.ghtkgg.cn/jnews/2062.htm
- http://m.wap.ghtkgg.cn/jnews/282436.htm
- http://m.wap.ghtkgg.cn/jnews/031992.htm
- http://m.wap.ghtkgg.cn/jnews/703381.htm
- http://m.wap.ghtkgg.cn/jnews/316163.htm
- http://m.wap.ghtkgg.cn/jnews/5770041.htm
- http://m.wap.ghtkgg.cn/jnews/63311.htm
- http://m.wap.ghtkgg.cn/jnews/759218.htm
- http://m.wap.ghtkgg.cn/jnews/07193.htm
- http://m.wap.ghtkgg.cn/jnews/632954.htm
- http://m.wap.ghtkgg.cn/jnews/348302.htm
- http://m.wap.ghtkgg.cn/jnews/3404918.htm
- http://m.wap.ghtkgg.cn/jnews/6946584.htm
- http://m.wap.ghtkgg.cn/jnews/7508.htm
- http://m.wap.ghtkgg.cn/jnews/806818.htm
- http://m.wap.ghtkgg.cn/jnews/974574.htm
- http://m.wap.ghtkgg.cn/jnews/0052790.htm
- http://m.wap.ghtkgg.cn/jnews/060467.htm
- http://m.wap.ghtkgg.cn/jnews/2826076.htm
- http://m.wap.ghtkgg.cn/jnews/5234.htm
- http://m.wap.ghtkgg.cn/jnews/12743.htm
- http://m.wap.ghtkgg.cn/jnews/32258.htm
- http://m.wap.ghtkgg.cn/jnews/66974.htm
- http://m.wap.ghtkgg.cn/jnews/02547.htm
- http://m.wap.ghtkgg.cn/jnews/98502.htm
- http://m.wap.ghtkgg.cn/jnews/2670.htm
- http://m.wap.ghtkgg.cn/jnews/95853.htm
- http://m.wap.ghtkgg.cn/jnews/8726.htm
- http://m.wap.ghtkgg.cn/jnews/757958.htm
- http://m.wap.ghtkgg.cn/jnews/3722.htm
- http://m.wap.ghtkgg.cn/jnews/0327790.htm
- http://m.wap.ghtkgg.cn/jnews/708980.htm
- http://m.wap.ghtkgg.cn/jnews/601177.htm
- http://m.wap.ghtkgg.cn/jnews/1355.htm
- http://m.wap.ghtkgg.cn/jnews/9999.htm
- http://m.wap.ghtkgg.cn/jnews/4980566.htm
- http://m.wap.ghtkgg.cn/jnews/69019.htm
- http://m.wap.ghtkgg.cn/jnews/2561.htm
- http://m.wap.ghtkgg.cn/jnews/70088.htm
- http://m.wap.ghtkgg.cn/jnews/4325910.htm
- http://m.wap.ghtkgg.cn/jnews/3025.htm
- http://m.wap.ghtkgg.cn/jnews/528294.htm
- http://m.wap.ghtkgg.cn/jnews/355638.htm
- http://m.wap.ghtkgg.cn/jnews/55771.htm
- http://m.wap.ghtkgg.cn/jnews/34024.htm
- http://m.wap.ghtkgg.cn/jnews/53574.htm
- http://m.wap.ghtkgg.cn/jnews/13125.htm
- http://m.wap.ghtkgg.cn/jnews/35169.htm
- http://m.wap.ghtkgg.cn/jnews/41900.htm
- http://m.wap.ghtkgg.cn/jnews/7192.htm
- http://m.wap.ghtkgg.cn/jnews/6351060.htm
- http://m.wap.ghtkgg.cn/jnews/3120.htm
- http://m.wap.ghtkgg.cn/jnews/050331.htm
- http://m.wap.ghtkgg.cn/jnews/0745713.htm
- http://m.wap.ghtkgg.cn/jnews/53756.htm
- http://m.wap.ghtkgg.cn/jnews/6921145.htm
- http://m.wap.ghtkgg.cn/jnews/1205880.htm
- http://m.wap.ghtkgg.cn/jnews/336018.htm
- http://m.wap.ghtkgg.cn/jnews/1187.htm
- http://m.wap.ghtkgg.cn/jnews/975184.htm
- http://m.wap.ghtkgg.cn/jnews/94984.htm
- http://m.wap.ghtkgg.cn/jnews/781300.htm
- http://m.wap.ghtkgg.cn/jnews/27010.htm
- http://m.wap.ghtkgg.cn/jnews/63190.htm
- http://m.wap.ghtkgg.cn/jnews/23551.htm
- http://m.wap.ghtkgg.cn/jnews/833694.htm
- http://m.wap.ghtkgg.cn/jnews/9693.htm
- http://m.wap.ghtkgg.cn/jnews/58152.htm
- http://m.wap.ghtkgg.cn/jnews/2733224.htm
- http://m.wap.ghtkgg.cn/jnews/7550.htm
- http://m.wap.ghtkgg.cn/jnews/436218.htm
- http://m.wap.ghtkgg.cn/jnews/3395.htm
- http://m.wap.ghtkgg.cn/jnews/337038.htm
- http://m.wap.ghtkgg.cn/jnews/305502.htm
- http://m.wap.ghtkgg.cn/jnews/5116390.htm
- http://m.wap.ghtkgg.cn/jnews/735407.htm
- http://m.wap.ghtkgg.cn/jnews/260096.htm
- http://m.wap.ghtkgg.cn/jnews/3206301.htm
- http://m.wap.ghtkgg.cn/jnews/777835.htm
- http://m.wap.ghtkgg.cn/jnews/2054825.htm
- http://m.wap.ghtkgg.cn/jnews/7073.htm
- http://m.wap.ghtkgg.cn/jnews/8586569.htm
- http://m.wap.ghtkgg.cn/jnews/0323.htm
- http://m.wap.ghtkgg.cn/jnews/84113.htm
- http://m.wap.ghtkgg.cn/jnews/23529.htm
- http://m.wap.ghtkgg.cn/jnews/1970104.htm
- http://m.wap.ghtkgg.cn/jnews/3595525.htm
- http://m.wap.ghtkgg.cn/jnews/8580835.htm
- http://m.wap.ghtkgg.cn/jnews/1259774.htm
- http://m.wap.ghtkgg.cn/jnews/817522.htm
- http://m.wap.ghtkgg.cn/jnews/3405241.htm
- http://m.wap.ghtkgg.cn/jnews/8081157.htm
- http://m.wap.ghtkgg.cn/jnews/44284.htm
- http://m.wap.ghtkgg.cn/jnews/3314.htm
- http://m.wap.ghtkgg.cn/jnews/483546.htm
- http://m.wap.ghtkgg.cn/jnews/9109579.htm
- http://m.wap.ghtkgg.cn/jnews/53713.htm
- http://m.wap.ghtkgg.cn/jnews/5496.htm
- http://m.wap.ghtkgg.cn/jnews/13656.htm
- http://m.wap.ghtkgg.cn/jnews/1760281.htm
- http://m.wap.ghtkgg.cn/jnews/5271.htm
- http://m.wap.ghtkgg.cn/jnews/0475.htm
- http://m.wap.ghtkgg.cn/jnews/786750.htm
- http://m.wap.ghtkgg.cn/jnews/8536.htm
- http://m.wap.ghtkgg.cn/jnews/80193.htm
- http://m.wap.ghtkgg.cn/jnews/7731286.htm
- http://m.wap.ghtkgg.cn/jnews/6486317.htm
- http://m.wap.ghtkgg.cn/jnews/28418.htm
- http://m.wap.ghtkgg.cn/jnews/819567.htm
- http://m.wap.ghtkgg.cn/jnews/71198.htm
- http://m.wap.ghtkgg.cn/jnews/82998.htm
- http://m.wap.ghtkgg.cn/jnews/2094.htm
- http://m.wap.ghtkgg.cn/jnews/565944.htm
- http://m.wap.ghtkgg.cn/jnews/9819.htm
- http://m.wap.ghtkgg.cn/jnews/8146404.htm
- http://m.wap.ghtkgg.cn/jnews/7301327.htm
- http://m.wap.ghtkgg.cn/jnews/974480.htm
- http://m.wap.ghtkgg.cn/jnews/50117.htm
- http://m.wap.ghtkgg.cn/jnews/3178452.htm
- http://m.wap.ghtkgg.cn/jnews/5930.htm
- http://m.wap.ghtkgg.cn/jnews/8205381.htm
- http://m.wap.ghtkgg.cn/jnews/0771.htm
- http://m.wap.ghtkgg.cn/jnews/2718.htm
- http://m.wap.ghtkgg.cn/jnews/44834.htm
- http://m.wap.ghtkgg.cn/jnews/06021.htm
- http://m.wap.ghtkgg.cn/jnews/8577.htm
- http://m.wap.ghtkgg.cn/jnews/6204.htm
- http://m.wap.ghtkgg.cn/jnews/7869569.htm
- http://m.wap.ghtkgg.cn/jnews/7046301.htm
- http://m.wap.ghtkgg.cn/jnews/2633046.htm
- http://m.wap.ghtkgg.cn/jnews/1221187.htm
- http://m.wap.ghtkgg.cn/jnews/7734087.htm
- http://m.wap.ghtkgg.cn/jnews/4254.htm
- http://m.wap.ghtkgg.cn/jnews/72255.htm
- http://m.wap.ghtkgg.cn/jnews/2267761.htm
- http://m.wap.ghtkgg.cn/jnews/4550.htm
- http://m.wap.ghtkgg.cn/jnews/2960538.htm
- http://m.wap.ghtkgg.cn/jnews/922842.htm
- http://m.wap.ghtkgg.cn/jnews/1843064.htm
- http://m.wap.ghtkgg.cn/jnews/6279.htm
- http://m.wap.ghtkgg.cn/jnews/59446.htm
- http://m.wap.ghtkgg.cn/jnews/5757.htm
- http://m.wap.ghtkgg.cn/jnews/491719.htm
- http://m.wap.ghtkgg.cn/jnews/42106.htm
- http://m.wap.ghtkgg.cn/jnews/4547311.htm
- http://m.wap.ghtkgg.cn/jnews/0678.htm
- http://m.wap.ghtkgg.cn/jnews/73436.htm
- http://m.wap.ghtkgg.cn/jnews/1340450.htm
- http://m.wap.ghtkgg.cn/jnews/627523.htm
- http://m.wap.ghtkgg.cn/jnews/544093.htm
- http://m.wap.ghtkgg.cn/jnews/563263.htm
- http://m.wap.ghtkgg.cn/jnews/4001.htm
- http://m.wap.ghtkgg.cn/jnews/6831370.htm
- http://m.wap.ghtkgg.cn/jnews/59155.htm
- http://m.wap.ghtkgg.cn/jnews/33262.htm
- http://m.wap.ghtkgg.cn/jnews/469317.htm
- http://m.wap.ghtkgg.cn/jnews/3792975.htm
- http://m.wap.ghtkgg.cn/jnews/77207.htm
- http://m.wap.ghtkgg.cn/jnews/6195.htm
- http://m.wap.ghtkgg.cn/jnews/1132326.htm
- http://m.wap.ghtkgg.cn/jnews/6793.htm
- http://m.wap.ghtkgg.cn/jnews/8428.htm
- http://m.wap.ghtkgg.cn/jnews/1908223.htm
- http://m.wap.ghtkgg.cn/jnews/1158.htm
- http://m.wap.ghtkgg.cn/jnews/92478.htm
- http://m.wap.ghtkgg.cn/jnews/4487943.htm
- http://m.wap.ghtkgg.cn/jnews/5720.htm
- http://m.wap.ghtkgg.cn/jnews/6703.htm
- http://m.wap.ghtkgg.cn/jnews/51953.htm
- http://m.wap.ghtkgg.cn/jnews/2813236.htm
- http://m.wap.ghtkgg.cn/jnews/605348.htm
- http://m.wap.ghtkgg.cn/jnews/487068.htm
- http://m.wap.ghtkgg.cn/jnews/1416.htm
- http://m.wap.ghtkgg.cn/jnews/04006.htm
- http://m.wap.ghtkgg.cn/jnews/048557.htm
- http://m.wap.ghtkgg.cn/jnews/110709.htm
- http://m.wap.ghtkgg.cn/jnews/789438.htm
- http://m.wap.ghtkgg.cn/jnews/525563.htm
- http://m.wap.ghtkgg.cn/jnews/4556.htm
- http://m.wap.ghtkgg.cn/jnews/6389.htm
- http://m.wap.ghtkgg.cn/jnews/8602.htm
- http://m.wap.ghtkgg.cn/jnews/49954.htm
- http://m.wap.ghtkgg.cn/jnews/183254.htm
- http://m.wap.ghtkgg.cn/jnews/9459838.htm
- http://m.wap.ghtkgg.cn/jnews/004229.htm
- http://m.wap.ghtkgg.cn/jnews/1406.htm
- http://m.wap.ghtkgg.cn/jnews/5354526.htm
- http://m.wap.ghtkgg.cn/jnews/896106.htm
- http://m.wap.ghtkgg.cn/jnews/6849140.htm
- http://m.wap.ghtkgg.cn/jnews/9336.htm
- http://m.wap.ghtkgg.cn/jnews/2248.htm
- http://m.wap.ghtkgg.cn/jnews/635753.htm
- http://m.wap.ghtkgg.cn/jnews/8986.htm
- http://m.wap.ghtkgg.cn/jnews/24394.htm
- http://m.wap.ghtkgg.cn/jnews/860257.htm
- http://m.wap.ghtkgg.cn/jnews/0292833.htm
- http://m.wap.ghtkgg.cn/jnews/625885.htm
- http://m.wap.ghtkgg.cn/jnews/20583.htm
- http://m.wap.ghtkgg.cn/jnews/86096.htm
- http://m.wap.ghtkgg.cn/jnews/4068446.htm
- http://m.wap.ghtkgg.cn/jnews/35851.htm
- http://m.wap.ghtkgg.cn/jnews/28839.htm
- http://m.wap.ghtkgg.cn/jnews/3618.htm
- http://m.wap.ghtkgg.cn/jnews/4236375.htm
- http://m.wap.ghtkgg.cn/jnews/0078.htm
- http://m.wap.ghtkgg.cn/jnews/9128152.htm
- http://m.wap.ghtkgg.cn/jnews/016611.htm
- http://m.wap.ghtkgg.cn/jnews/8319.htm
- http://m.wap.ghtkgg.cn/jnews/2083481.htm
- http://m.wap.ghtkgg.cn/jnews/78335.htm
- http://m.wap.ghtkgg.cn/jnews/215165.htm
- http://m.wap.ghtkgg.cn/jnews/70660.htm
- http://m.wap.ghtkgg.cn/jnews/68694.htm
- http://m.wap.ghtkgg.cn/jnews/6387363.htm
- http://m.wap.ghtkgg.cn/jnews/9158863.htm
- http://m.wap.ghtkgg.cn/jnews/29898.htm
- http://m.wap.ghtkgg.cn/jnews/13567.htm
- http://m.wap.ghtkgg.cn/jnews/76112.htm
- http://m.wap.ghtkgg.cn/jnews/3236602.htm
- http://m.wap.ghtkgg.cn/jnews/7637.htm
- http://m.wap.ghtkgg.cn/jnews/12597.htm
- http://m.wap.ghtkgg.cn/jnews/2757.htm
- http://m.wap.ghtkgg.cn/jnews/7530549.htm
- http://m.wap.ghtkgg.cn/jnews/15865.htm
- http://m.wap.ghtkgg.cn/jnews/0931790.htm
- http://m.wap.ghtkgg.cn/jnews/507268.htm
- http://m.wap.ghtkgg.cn/jnews/2483571.htm
- http://m.wap.ghtkgg.cn/jnews/77278.htm
- http://m.wap.ghtkgg.cn/jnews/872571.htm
- http://m.wap.ghtkgg.cn/jnews/88146.htm
- http://m.wap.ghtkgg.cn/jnews/1272024.htm
- http://m.wap.ghtkgg.cn/jnews/361423.htm
- http://m.wap.ghtkgg.cn/jnews/68103.htm
- http://m.wap.ghtkgg.cn/jnews/4210701.htm
- http://m.wap.ghtkgg.cn/jnews/4052347.htm
- http://m.wap.ghtkgg.cn/jnews/1655.htm
- http://m.wap.ghtkgg.cn/jnews/2595.htm
- http://m.wap.ghtkgg.cn/jnews/3746064.htm
- http://m.wap.ghtkgg.cn/jnews/3701.htm
- http://m.wap.ghtkgg.cn/jnews/09508.htm
- http://m.wap.ghtkgg.cn/jnews/225766.htm
- http://m.wap.ghtkgg.cn/jnews/70155.htm
- http://m.wap.ghtkgg.cn/jnews/5388011.htm
- http://m.wap.ghtkgg.cn/jnews/8516184.htm
- http://m.wap.ghtkgg.cn/jnews/752775.htm
- http://m.wap.ghtkgg.cn/jnews/70186.htm
- http://m.wap.ghtkgg.cn/jnews/770105.htm
- http://m.wap.ghtkgg.cn/jnews/30952.htm
- http://m.wap.ghtkgg.cn/jnews/7379.htm
- http://m.wap.ghtkgg.cn/jnews/503694.htm
- http://m.wap.ghtkgg.cn/jnews/6382.htm
- http://m.wap.ghtkgg.cn/jnews/7133.htm
- http://m.wap.ghtkgg.cn/jnews/506059.htm
- http://m.wap.ghtkgg.cn/jnews/5723.htm
- http://m.wap.ghtkgg.cn/jnews/7371014.htm
- http://m.wap.ghtkgg.cn/jnews/47016.htm
- http://m.wap.ghtkgg.cn/jnews/79559.htm
- http://m.wap.ghtkgg.cn/jnews/69530.htm
- http://m.wap.ghtkgg.cn/jnews/670466.htm
- http://m.wap.ghtkgg.cn/jnews/4709653.htm
- http://m.wap.ghtkgg.cn/jnews/28615.htm

## 项目结构

```
jnews-aggregator/
├── app.py                      # 应用入口文件，初始化Flask实例并注册路由
├── requirements.txt            # 生产环境依赖列表，固定版本号
├── dev-requirements.txt        # 开发环境额外依赖，包含测试和代码检查工具
├── .flake8                     # flake8代码风格检查配置文件
├── .gitignore                  # Git版本控制忽略文件规则
├── README.md                   # 项目说明文档，即当前文件
├── LICENSE                     # MIT许可证文件
│
├── jnews/                      # 核心业务逻辑包
│   ├── __init__.py             # 包初始化，导出主要接口类
│   ├── parser.py               # URL解析器，提取新闻ID、分类和基础元数据
│   ├── fetcher.py              # 内容抓取器，使用requests发起HTTP请求获取HTML
│   ├── cleaner.py              # 数据清洗器，去除HTML标签、过滤无效字符
│   ├── indexer.py              # 索引构建器，为新闻条目生成倒排索引用于检索
│   └── exporter.py             # 数据导出器，支持JSON、CSV和Markdown格式输出
│
├── web/                        # Web展示层模块
│   ├── __init__.py             # 蓝图初始化
│   ├── routes.py               # 路由定义：首页、列表页、详情页、检索页
│   ├── filters.py              # 自定义Jinja2模板过滤器
│   └── static/                 # 静态资源目录
│       ├── css/                # 样式表文件（基于Bootstrap定制）
│       ├── js/                 # 前端交互脚本（分页、检索、筛选）
│       └── images/             # 图片资源（Logo、图标等）
│
├── templates/                  # Jinja2 HTML模板目录
│   ├── base.html               # 基础模板，定义页面骨架和导航栏
│   ├── index.html              # 首页模板，显示新闻列表和检索框
│   ├── detail.html             # 详情页模板，展示单条新闻完整内容
│   └── about.html              # 关于页面，展示项目信息和版本历史
│
├── tests/                      # 单元测试目录
│   ├── test_parser.py          # 解析器单元测试
│   ├── test_fetcher.py         # 抓取器单元测试
│   ├── test_cleaner.py         # 清洗器单元测试
│   └── test_routes.py          # Web路由功能测试
│
├── scripts/                    # 运维和辅助脚本
│   ├── import_urls.py          # 从文本文件批量导入URL的命令行工具
│   ├── check_links.py          # 检查所有外链可用性的健康检查脚本
│   └── generate_sitemap.py     # 生成站点地图XML文件
│
└── docs/                       # 项目文档目录
    ├── user-guide.md           # 用户使用手册
    ├── deployment.md           # 生产部署指南
    ├── api-reference.md        # RESTful API接口文档
    └── development.md          # 开发者贡献指南
```

## 贡献指南

1. 在GitHub仓库中提交Issue说明您要修复的问题或新增的功能，等待维护者确认后再开始编码，避免重复劳动或方向偏差。

2. Fork本仓库到您的个人账户，将代码克隆到本地环境，并按照开发指南配置开发环境，确保所有测试用例能够通过。

3. 在本地创建新的功能分支，遵循项目的代码风格规范（使用flake8检查），编写包含完整文档字符串和单元测试的代码。

4. 提交代码前运行全部测试套件确保无回归问题，并更新相应的文档文件（如用户手册或API参考），反映您的变更内容。

5. 向主仓库的main分支发起Pull Request，在PR描述中清晰说明变更目的、实现方式和测试覆盖情况，等待代码审查和合并。

## 常见问题

**Q: 导入大量URL后页面加载变慢，如何优化列表渲染速度？**

A: 建议启用Flask的缓存扩展（如flask-caching）缓存分页结果，并配置每页显示数量为20条以下。同时可以在生产环境中部署Redis作为缓存后端，减少数据库查询或列表重新生成的频率。此外，可将外链健康检查设置为异步任务，避免阻塞主请求响应。

**Q: 部分新闻URL返回404或超时，系统如何处理？**

A: 在导入阶段，fetcher模块会尝试对每个URL发起HEAD请求验证可用性，超时时间默认为5秒。对于不可用的链接，系统会记录日志并标记状态为失效，但在列表中仍然保留条目以便用户查看。您可以通过配置CHECK_ACTIVE环境变量为false来跳过验证，仅保留URL的元数据信息。

**Q: 如何自定义分类标签的生成规则？**

A: 在jnews/parser.py中修改_extract_category方法，该方法目前基于URL中的数字ID长度和特定前缀模式生成标签。您可以重写此方法，改为从新闻页面HTML的meta标签或DOM结构中提取真实分类，并在config.py中配置自定义的映射字典。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
