# NewsLink Aggregator

NewsLink Aggregator 是一个面向技术资讯聚合与轻量级新闻订阅的开源外链管理工具，定位于帮助开发者、内容创作者及小型团队从分散的信息源中高效收集、分类和展示外部新闻链接。该项目通过结构化的 URL 编排机制与自动化的元数据提取流程，将原始新闻链接转化为可检索、可标记、可分享的标准化条目，降低人工整理成本，提升信息流转效率。

本项目适用于需要定期跟进特定领域动态的技术社区运营者、个人博客作者以及企业内部知识库维护人员。NewsLink Aggregator 不提供新闻内容本身，而是构建一个可靠的外链引用层，确保每条原始链接都被准确记录、可追溯且可导出为多种数据格式，从而与现有工作流无缝集成。

## 功能概览

**批量链接导入** 支持从文本文件、CSV 或直接粘贴的 URL 列表中批量导入新闻链接，自动识别协议头与域名格式，去除重复条目并生成导入日志。

**自动元数据补全** 对每条导入的链接发起异步 HEAD 请求与页面标题提取，填充发布时间、来源站点、内容摘要等基础字段，减少手动输入负担。

**标签与分类体系** 提供多级标签系统，允许用户为每条链接附加自定义标签（如 "AI"、"前端"、"安全"），并支持按标签组合筛选与批量编辑。

**链接状态监控** 定时检测已收录链接的可访问性，标记失效链接（404、超时、DNS 解析失败），并生成健康度报告，便于及时清理或更新。

**全文检索与过滤** 基于标题、标签、来源域名和导入时间构建倒排索引，支持复杂查询表达式（如 tag:AI AND source:example.com），快速定位目标链接。

**数据导出与订阅** 支持将筛选结果导出为 JSON、CSV 或 OPML 格式，并可生成静态 HTML 页面用于内部订阅或嵌入其他系统。

## 应用场景

**技术社区每日资讯汇总** 社区运营人员每天从多个技术博客、论坛和官方公告页面收集数十条更新链接，使用 NewsLink Aggregator 批量导入后，通过标签区分 "前端"、"后端"、"运维" 等方向，再定期导出为社区周报的参考素材，减少人工复制粘贴的重复劳动。

**个人知识库外链管理** 独立研究者或博客作者在阅读过程中积累大量待读或已读的外部文章，利用本工具记录每条链接的原始来源，并标记阅读状态与笔记标签，后续可通过检索快速找回某条特定主题下的参考资料，避免浏览器书签无序膨胀。

**企业内部合规新闻追踪** 企业内部法务或公关团队需持续监控特定行业关键词相关的新闻报道，可将收集到的链接统一录入 NewsLink Aggregator，利用链接状态监控功能自动检查页面是否仍可访问，确保存档链接的有效性，满足内部审计对引用来源可追溯的要求。

**开源项目文档引用维护** 开源项目的文档维护者需在 README、教程或设计文档中引用大量外部资源链接，通过本工具管理这些引用 URL，定期批量检测失效链接并生成替换建议，避免文档中出现死链影响用户体验。

## 快速开始

以下步骤指导您在本地环境中快速启动 NewsLink Aggregator 服务。

```bash
# 克隆代码仓库
git clone https://github.com/your-org/newslink-aggregator.git
cd newslink-aggregator

# 安装依赖（使用 Python 虚拟环境）
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 初始化数据库并运行服务
python manage.py migrate
python manage.py runserver --host=0.0.0.0 --port=8080
```

启动后，访问 http://localhost:8080 即可进入 Web 管理界面，使用默认管理员账号 admin / admin123 登录，或通过 `python manage.py create_user` 创建新用户。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Python | 3.9 及以上 | 核心运行环境，建议使用 3.11 LTS 版本 |
| SQLite | 3.35 及以上 | 默认嵌入式数据库，用于元数据存储与索引 |
| Redis | 6.2 及以上 | 可选，用于链接状态监控的异步任务队列与缓存 |
| Node.js | 18.x LTS | 仅用于前端静态资源构建，生产环境可单独部署预构建包 |
| Nginx | 1.22 及以上 | 生产环境推荐反向代理，处理静态文件与负载均衡 |
| 系统内存 | 最低 512 MB | 建议 1 GB 以上以保证链接检测并发任务的稳定执行 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | /docs/user-guide/ | 如何导入链接、编辑标签、使用检索语法及导出数据 |
| 管理员手册 | /docs/admin/ | 如何配置定时任务、调整链接检测间隔、管理用户权限 |
| 开发者文档 | /docs/developer/ | API 接口规范、数据库表结构、自定义标签插件开发流程 |
| 部署运维 | /docs/deployment/ | 使用 Docker Compose 一键部署、环境变量配置、日志收集与备份策略 |

## 资源列表

- http://m.blog.ghtkgg.cn/nnews/48527.htm
- http://m.blog.ghtkgg.cn/nnews/155442.htm
- http://m.blog.ghtkgg.cn/nnews/351427.htm
- http://m.blog.ghtkgg.cn/nnews/83477.htm
- http://m.blog.ghtkgg.cn/nnews/9009730.htm
- http://m.blog.ghtkgg.cn/nnews/063452.htm
- http://m.blog.ghtkgg.cn/nnews/9592.htm
- http://m.blog.ghtkgg.cn/nnews/3872.htm
- http://m.blog.ghtkgg.cn/nnews/6396786.htm
- http://m.blog.ghtkgg.cn/nnews/511485.htm
- http://m.blog.ghtkgg.cn/nnews/9518983.htm
- http://m.blog.ghtkgg.cn/nnews/077707.htm
- http://m.blog.ghtkgg.cn/nnews/1415.htm
- http://m.blog.ghtkgg.cn/nnews/2334183.htm
- http://m.blog.ghtkgg.cn/nnews/88251.htm
- http://m.blog.ghtkgg.cn/nnews/84659.htm
- http://m.blog.ghtkgg.cn/nnews/9877.htm
- http://m.blog.ghtkgg.cn/nnews/957942.htm
- http://m.blog.ghtkgg.cn/nnews/393509.htm
- http://m.blog.ghtkgg.cn/nnews/194471.htm
- http://m.blog.ghtkgg.cn/nnews/392611.htm
- http://m.blog.ghtkgg.cn/nnews/55820.htm
- http://m.blog.ghtkgg.cn/nnews/9964.htm
- http://m.blog.ghtkgg.cn/nnews/12050.htm
- http://m.blog.ghtkgg.cn/nnews/43635.htm
- http://m.blog.ghtkgg.cn/nnews/782537.htm
- http://m.blog.ghtkgg.cn/nnews/64590.htm
- http://m.blog.ghtkgg.cn/nnews/316138.htm
- http://m.blog.ghtkgg.cn/nnews/971468.htm
- http://m.blog.ghtkgg.cn/nnews/6657087.htm
- http://m.blog.ghtkgg.cn/nnews/6173.htm
- http://m.blog.ghtkgg.cn/nnews/6054138.htm
- http://m.blog.ghtkgg.cn/nnews/499360.htm
- http://m.blog.ghtkgg.cn/nnews/16527.htm
- http://m.blog.ghtkgg.cn/nnews/73145.htm
- http://m.blog.ghtkgg.cn/nnews/9097078.htm
- http://m.blog.ghtkgg.cn/nnews/843132.htm
- http://m.blog.ghtkgg.cn/nnews/070712.htm
- http://m.blog.ghtkgg.cn/nnews/8202.htm
- http://m.blog.ghtkgg.cn/nnews/7122784.htm
- http://m.blog.ghtkgg.cn/nnews/9191137.htm
- http://m.blog.ghtkgg.cn/nnews/5555129.htm
- http://m.blog.ghtkgg.cn/nnews/322126.htm
- http://m.blog.ghtkgg.cn/nnews/8043571.htm
- http://m.blog.ghtkgg.cn/nnews/9584.htm
- http://m.blog.ghtkgg.cn/nnews/8345267.htm
- http://m.blog.ghtkgg.cn/nnews/3733052.htm
- http://m.blog.ghtkgg.cn/nnews/2273463.htm
- http://m.blog.ghtkgg.cn/nnews/4924.htm
- http://m.blog.ghtkgg.cn/nnews/82887.htm
- http://m.blog.ghtkgg.cn/nnews/8794436.htm
- http://m.blog.ghtkgg.cn/nnews/72141.htm
- http://m.blog.ghtkgg.cn/nnews/8406.htm
- http://m.blog.ghtkgg.cn/nnews/99520.htm
- http://m.blog.ghtkgg.cn/nnews/14254.htm
- http://m.blog.ghtkgg.cn/nnews/007898.htm
- http://m.blog.ghtkgg.cn/nnews/2219.htm
- http://m.blog.ghtkgg.cn/nnews/7035684.htm
- http://m.blog.ghtkgg.cn/nnews/737835.htm
- http://m.blog.ghtkgg.cn/nnews/8578.htm
- http://m.blog.ghtkgg.cn/nnews/8360060.htm
- http://m.blog.ghtkgg.cn/nnews/2462840.htm
- http://m.blog.ghtkgg.cn/nnews/6630726.htm
- http://m.blog.ghtkgg.cn/nnews/03770.htm
- http://m.blog.ghtkgg.cn/nnews/0294.htm
- http://m.blog.ghtkgg.cn/nnews/701092.htm
- http://m.blog.ghtkgg.cn/nnews/830374.htm
- http://m.blog.ghtkgg.cn/nnews/9471.htm
- http://m.blog.ghtkgg.cn/nnews/578528.htm
- http://m.blog.ghtkgg.cn/nnews/2514215.htm
- http://m.blog.ghtkgg.cn/nnews/2952119.htm
- http://m.blog.ghtkgg.cn/nnews/015590.htm
- http://m.blog.ghtkgg.cn/nnews/6729031.htm
- http://m.blog.ghtkgg.cn/nnews/474437.htm
- http://m.blog.ghtkgg.cn/nnews/928990.htm
- http://m.blog.ghtkgg.cn/nnews/158958.htm
- http://m.blog.ghtkgg.cn/nnews/21363.htm
- http://m.blog.ghtkgg.cn/nnews/47060.htm
- http://m.blog.ghtkgg.cn/nnews/36208.htm
- http://m.blog.ghtkgg.cn/nnews/4225.htm
- http://m.blog.ghtkgg.cn/nnews/18757.htm
- http://m.blog.ghtkgg.cn/nnews/009385.htm
- http://m.blog.ghtkgg.cn/nnews/6147704.htm
- http://m.blog.ghtkgg.cn/nnews/10707.htm
- http://m.blog.ghtkgg.cn/nnews/9576498.htm
- http://m.blog.ghtkgg.cn/nnews/7331.htm
- http://m.blog.ghtkgg.cn/nnews/1575.htm
- http://m.blog.ghtkgg.cn/nnews/7948.htm
- http://m.blog.ghtkgg.cn/nnews/529624.htm
- http://m.blog.ghtkgg.cn/nnews/737830.htm
- http://m.blog.ghtkgg.cn/nnews/3875.htm
- http://m.blog.ghtkgg.cn/nnews/0437196.htm
- http://m.blog.ghtkgg.cn/nnews/49749.htm
- http://m.blog.ghtkgg.cn/nnews/2124.htm
- http://m.blog.ghtkgg.cn/nnews/1978957.htm
- http://m.blog.ghtkgg.cn/nnews/45022.htm
- http://m.blog.ghtkgg.cn/nnews/7777.htm
- http://m.blog.ghtkgg.cn/nnews/81141.htm
- http://m.blog.ghtkgg.cn/nnews/18598.htm
- http://m.blog.ghtkgg.cn/nnews/462661.htm
- http://m.blog.ghtkgg.cn/nnews/1923.htm
- http://m.blog.ghtkgg.cn/nnews/32475.htm
- http://m.blog.ghtkgg.cn/nnews/1713.htm
- http://m.blog.ghtkgg.cn/nnews/6592.htm
- http://m.blog.ghtkgg.cn/nnews/0009.htm
- http://m.blog.ghtkgg.cn/nnews/9768804.htm
- http://m.blog.ghtkgg.cn/nnews/910232.htm
- http://m.blog.ghtkgg.cn/nnews/6144729.htm
- http://m.blog.ghtkgg.cn/nnews/2618863.htm
- http://m.blog.ghtkgg.cn/nnews/391377.htm
- http://m.blog.ghtkgg.cn/nnews/8974.htm
- http://m.blog.ghtkgg.cn/nnews/067266.htm
- http://m.blog.ghtkgg.cn/nnews/2063526.htm
- http://m.blog.ghtkgg.cn/nnews/8739.htm
- http://m.blog.ghtkgg.cn/nnews/9764.htm
- http://m.blog.ghtkgg.cn/nnews/22859.htm
- http://m.blog.ghtkgg.cn/nnews/353375.htm
- http://m.blog.ghtkgg.cn/nnews/565303.htm
- http://m.blog.ghtkgg.cn/nnews/120567.htm
- http://m.blog.ghtkgg.cn/nnews/1459899.htm
- http://m.blog.ghtkgg.cn/nnews/49487.htm
- http://m.blog.ghtkgg.cn/nnews/9300.htm
- http://m.blog.ghtkgg.cn/nnews/6508.htm
- http://m.blog.ghtkgg.cn/nnews/1578.htm
- http://m.blog.ghtkgg.cn/nnews/312111.htm
- http://m.blog.ghtkgg.cn/nnews/0355457.htm
- http://m.blog.ghtkgg.cn/nnews/5003541.htm
- http://m.blog.ghtkgg.cn/nnews/09080.htm
- http://m.blog.ghtkgg.cn/nnews/737527.htm
- http://m.blog.ghtkgg.cn/nnews/6649.htm
- http://m.blog.ghtkgg.cn/nnews/253106.htm
- http://m.blog.ghtkgg.cn/nnews/776601.htm
- http://m.blog.ghtkgg.cn/nnews/13007.htm
- http://m.blog.ghtkgg.cn/nnews/25423.htm
- http://m.blog.ghtkgg.cn/nnews/9828616.htm
- http://m.blog.ghtkgg.cn/nnews/90674.htm
- http://m.blog.ghtkgg.cn/nnews/73746.htm
- http://m.blog.ghtkgg.cn/nnews/1481427.htm
- http://m.blog.ghtkgg.cn/nnews/4222.htm
- http://m.blog.ghtkgg.cn/nnews/3684.htm
- http://m.blog.ghtkgg.cn/nnews/6743.htm
- http://m.blog.ghtkgg.cn/nnews/36665.htm
- http://m.blog.ghtkgg.cn/nnews/3886061.htm
- http://m.blog.ghtkgg.cn/nnews/2556.htm
- http://m.blog.ghtkgg.cn/nnews/5645260.htm
- http://m.blog.ghtkgg.cn/nnews/8442.htm
- http://m.blog.ghtkgg.cn/nnews/4975493.htm
- http://m.blog.ghtkgg.cn/nnews/2286.htm
- http://m.blog.ghtkgg.cn/nnews/2034.htm
- http://m.blog.ghtkgg.cn/nnews/102160.htm
- http://m.blog.ghtkgg.cn/nnews/78407.htm
- http://m.blog.ghtkgg.cn/nnews/8746636.htm
- http://m.blog.ghtkgg.cn/nnews/10280.htm
- http://m.blog.ghtkgg.cn/nnews/4667493.htm
- http://m.blog.ghtkgg.cn/nnews/4423.htm
- http://m.blog.ghtkgg.cn/nnews/56022.htm
- http://m.blog.ghtkgg.cn/nnews/4414.htm
- http://m.blog.ghtkgg.cn/nnews/4644454.htm
- http://m.blog.ghtkgg.cn/nnews/3553.htm
- http://m.blog.ghtkgg.cn/nnews/6558315.htm
- http://m.blog.ghtkgg.cn/nnews/2789.htm
- http://m.blog.ghtkgg.cn/nnews/45122.htm
- http://m.blog.ghtkgg.cn/nnews/7737629.htm
- http://m.blog.ghtkgg.cn/nnews/75655.htm
- http://m.blog.ghtkgg.cn/nnews/7139206.htm
- http://m.blog.ghtkgg.cn/nnews/91118.htm
- http://m.blog.ghtkgg.cn/nnews/015908.htm
- http://m.blog.ghtkgg.cn/nnews/79067.htm
- http://m.blog.ghtkgg.cn/nnews/168503.htm
- http://m.blog.ghtkgg.cn/nnews/62435.htm
- http://m.blog.ghtkgg.cn/nnews/077791.htm
- http://m.blog.ghtkgg.cn/nnews/00610.htm
- http://m.blog.ghtkgg.cn/nnews/929048.htm
- http://m.blog.ghtkgg.cn/nnews/7733802.htm
- http://m.blog.ghtkgg.cn/nnews/7777664.htm
- http://m.blog.ghtkgg.cn/nnews/8109536.htm
- http://m.blog.ghtkgg.cn/nnews/04641.htm
- http://m.blog.ghtkgg.cn/nnews/88091.htm
- http://m.blog.ghtkgg.cn/nnews/480338.htm
- http://m.blog.ghtkgg.cn/nnews/4864.htm
- http://m.blog.ghtkgg.cn/nnews/3605057.htm
- http://m.blog.ghtkgg.cn/nnews/87029.htm
- http://m.blog.ghtkgg.cn/nnews/9352135.htm
- http://m.blog.ghtkgg.cn/nnews/127298.htm
- http://m.blog.ghtkgg.cn/nnews/010610.htm
- http://m.blog.ghtkgg.cn/nnews/1487.htm
- http://m.blog.ghtkgg.cn/nnews/633655.htm
- http://m.blog.ghtkgg.cn/nnews/5150.htm
- http://m.blog.ghtkgg.cn/nnews/91023.htm
- http://m.blog.ghtkgg.cn/nnews/2359053.htm
- http://m.blog.ghtkgg.cn/nnews/3010865.htm
- http://m.blog.ghtkgg.cn/nnews/81313.htm
- http://m.blog.ghtkgg.cn/nnews/832047.htm
- http://m.blog.ghtkgg.cn/nnews/0529533.htm
- http://m.blog.ghtkgg.cn/nnews/314156.htm
- http://m.blog.ghtkgg.cn/nnews/14009.htm
- http://m.blog.ghtkgg.cn/nnews/159587.htm
- http://m.blog.ghtkgg.cn/nnews/4881.htm
- http://m.blog.ghtkgg.cn/nnews/22321.htm
- http://m.blog.ghtkgg.cn/nnews/703513.htm
- http://m.blog.ghtkgg.cn/nnews/150197.htm
- http://m.blog.ghtkgg.cn/nnews/9333656.htm
- http://m.blog.ghtkgg.cn/nnews/607534.htm
- http://m.blog.ghtkgg.cn/nnews/8492900.htm
- http://m.blog.ghtkgg.cn/nnews/89353.htm
- http://m.blog.ghtkgg.cn/nnews/6690954.htm
- http://m.blog.ghtkgg.cn/nnews/8502075.htm
- http://m.blog.ghtkgg.cn/nnews/04134.htm
- http://m.blog.ghtkgg.cn/nnews/32285.htm
- http://m.blog.ghtkgg.cn/nnews/04408.htm
- http://m.blog.ghtkgg.cn/nnews/4817149.htm
- http://m.blog.ghtkgg.cn/nnews/515394.htm
- http://m.blog.ghtkgg.cn/nnews/6838356.htm
- http://m.blog.ghtkgg.cn/nnews/99372.htm
- http://m.blog.ghtkgg.cn/nnews/5247950.htm
- http://m.blog.ghtkgg.cn/nnews/928206.htm
- http://m.blog.ghtkgg.cn/nnews/373698.htm
- http://m.blog.ghtkgg.cn/nnews/81406.htm
- http://m.blog.ghtkgg.cn/nnews/4231647.htm
- http://m.blog.ghtkgg.cn/nnews/614844.htm
- http://m.blog.ghtkgg.cn/nnews/4978426.htm
- http://m.blog.ghtkgg.cn/nnews/120596.htm
- http://m.blog.ghtkgg.cn/nnews/2147871.htm
- http://m.blog.ghtkgg.cn/nnews/294853.htm
- http://m.blog.ghtkgg.cn/nnews/3138.htm
- http://m.blog.ghtkgg.cn/nnews/40187.htm
- http://m.blog.ghtkgg.cn/nnews/4743476.htm
- http://m.blog.ghtkgg.cn/nnews/9566.htm
- http://m.blog.ghtkgg.cn/nnews/43148.htm
- http://m.blog.ghtkgg.cn/nnews/926265.htm
- http://m.blog.ghtkgg.cn/nnews/1225477.htm
- http://m.blog.ghtkgg.cn/nnews/791538.htm
- http://m.blog.ghtkgg.cn/nnews/3717.htm
- http://m.blog.ghtkgg.cn/nnews/6229492.htm
- http://m.blog.ghtkgg.cn/nnews/600082.htm
- http://m.blog.ghtkgg.cn/nnews/17472.htm
- http://m.blog.ghtkgg.cn/nnews/244125.htm
- http://m.blog.ghtkgg.cn/nnews/99554.htm
- http://m.blog.ghtkgg.cn/nnews/22486.htm
- http://m.blog.ghtkgg.cn/nnews/336189.htm
- http://m.blog.ghtkgg.cn/nnews/4217.htm
- http://m.blog.ghtkgg.cn/nnews/5599006.htm
- http://m.blog.ghtkgg.cn/nnews/4806.htm
- http://m.blog.ghtkgg.cn/nnews/46626.htm
- http://m.blog.ghtkgg.cn/nnews/59586.htm
- http://m.blog.ghtkgg.cn/nnews/6638150.htm
- http://m.blog.ghtkgg.cn/nnews/3670182.htm
- http://m.blog.ghtkgg.cn/nnews/6164.htm
- http://m.blog.ghtkgg.cn/nnews/6945907.htm
- http://m.blog.ghtkgg.cn/nnews/9247988.htm
- http://m.blog.ghtkgg.cn/nnews/9003809.htm
- http://m.blog.ghtkgg.cn/nnews/74746.htm
- http://m.blog.ghtkgg.cn/nnews/25501.htm
- http://m.blog.ghtkgg.cn/nnews/9910326.htm
- http://m.blog.ghtkgg.cn/nnews/2471.htm
- http://m.blog.ghtkgg.cn/nnews/691007.htm
- http://m.blog.ghtkgg.cn/nnews/54591.htm
- http://m.blog.ghtkgg.cn/nnews/4198125.htm
- http://m.blog.ghtkgg.cn/nnews/781022.htm
- http://m.blog.ghtkgg.cn/nnews/5713008.htm
- http://m.blog.ghtkgg.cn/nnews/9341475.htm
- http://m.blog.ghtkgg.cn/nnews/935494.htm
- http://m.blog.ghtkgg.cn/nnews/37852.htm
- http://m.blog.ghtkgg.cn/nnews/8295.htm
- http://m.blog.ghtkgg.cn/nnews/0628.htm
- http://m.blog.ghtkgg.cn/nnews/1251106.htm
- http://m.blog.ghtkgg.cn/nnews/3763693.htm
- http://m.blog.ghtkgg.cn/nnews/1417357.htm
- http://m.blog.ghtkgg.cn/nnews/3946490.htm
- http://m.blog.ghtkgg.cn/nnews/617620.htm
- http://m.blog.ghtkgg.cn/nnews/18221.htm
- http://m.blog.ghtkgg.cn/nnews/0484375.htm
- http://m.blog.ghtkgg.cn/nnews/715174.htm
- http://m.blog.ghtkgg.cn/nnews/862698.htm
- http://m.blog.ghtkgg.cn/nnews/1886537.htm
- http://m.blog.ghtkgg.cn/nnews/91170.htm
- http://m.blog.ghtkgg.cn/nnews/994320.htm
- http://m.blog.ghtkgg.cn/nnews/2033.htm
- http://m.blog.ghtkgg.cn/nnews/7842.htm
- http://m.blog.ghtkgg.cn/nnews/7877969.htm
- http://m.blog.ghtkgg.cn/nnews/904115.htm
- http://m.blog.ghtkgg.cn/nnews/5889421.htm
- http://m.blog.ghtkgg.cn/nnews/017230.htm
- http://m.blog.ghtkgg.cn/nnews/8136916.htm
- http://m.blog.ghtkgg.cn/nnews/3106714.htm
- http://m.blog.ghtkgg.cn/nnews/5449344.htm
- http://m.blog.ghtkgg.cn/nnews/0102224.htm
- http://m.blog.ghtkgg.cn/nnews/2327.htm
- http://m.blog.ghtkgg.cn/nnews/0419197.htm
- http://m.blog.ghtkgg.cn/nnews/43253.htm
- http://m.blog.ghtkgg.cn/nnews/2088.htm
- http://m.blog.ghtkgg.cn/nnews/9433583.htm
- http://m.blog.ghtkgg.cn/nnews/77210.htm
- http://m.blog.ghtkgg.cn/nnews/7871.htm
- http://m.blog.ghtkgg.cn/nnews/5851.htm
- http://m.blog.ghtkgg.cn/nnews/69961.htm
- http://m.blog.ghtkgg.cn/nnews/60985.htm
- http://m.blog.ghtkgg.cn/nnews/19803.htm
- http://m.blog.ghtkgg.cn/nnews/050793.htm
- http://m.blog.ghtkgg.cn/nnews/7905394.htm

## 项目结构

```
newslink-aggregator/
├── app/                             # 主应用模块
│   ├── api/                         # RESTful API 路由与视图
│   │   ├── v1/                      # API 版本 v1 端点
│   │   │   ├── endpoints/           # 按资源划分的端点模块（links, tags, health）
│   │   │   └── schemas/             # Pydantic 模型，用于请求与响应校验
│   │   └── middleware/              # 认证、日志、跨域中间件
│   ├── core/                        # 核心业务逻辑层
│   │   ├── importer/                # 批量导入引擎，支持 CSV/TXT 解析
│   │   ├── metadata/                # 元数据提取器（标题、时间、来源解析）
│   │   ├── monitor/                 # 链接状态检测调度器与结果缓存
│   │   └── search/                  # 倒排索引构建与查询解析器
│   ├── models/                      # SQLAlchemy ORM 实体定义
│   │   ├── link.py                  # 链接条目模型（URL、标题、状态、时间戳）
│   │   ├── tag.py                   # 标签模型与多对多关联表
│   │   └── user.py                  # 用户认证与偏好设置
│   ├── services/                    # 外部服务集成（Redis 队列、邮件通知）
│   └── templates/                   # 管理后台 Jinja2 模板文件
├── frontend/                        # 独立前端项目（Vue 3 + Vite）
│   ├── src/                         # 组件、视图、状态管理（Pinia）
│   └── dist/                        # 生产构建输出目录（由部署流程生成）
├── scripts/                         # 运维与开发辅助脚本
│   ├── backup_db.py                 # 数据库备份脚本
│   └── seed_dev_data.py             # 开发环境数据填充
├── tests/                           # 单元测试与集成测试
│   ├── unit/                        # 针对 core 层的隔离测试
│   └── integration/                 # API 与数据库交互测试
├── docker/                          # Docker 构建上下文
│   ├── Dockerfile.app               # 应用容器镜像定义
│   └── docker-compose.yml           # 本地开发与生产部署编排文件
├── docs/                            # 完整文档源文件（Markdown + MkDocs 配置）
├── config/                          # 环境配置文件（development, production）
├── logs/                            # 运行日志存储目录（由应用自动创建）
├── requirements.txt                 # Python 依赖列表（生产环境）
├── requirements-dev.txt             # 开发与测试额外依赖
├── pyproject.toml                   # 项目元数据与构建系统配置
├── manage.py                        # CLI 管理入口（迁移、创建用户、启动服务）
└── README.md                        # 本文件
```

## 贡献指南

1. 从 GitHub Issues 中选择未被指派的 feature 或 bug 类问题，在问题评论区声明认领，等待维护者确认以避免重复工作。对于较大规模的功能改动，建议先创建讨论议题并附上设计草图。

2. 派生代码仓库至个人账户，基于 develop 分支创建功能分支，分支命名遵循 `feature/功能简述` 或 `fix/问题编号` 格式。本地开发时需确保通过全部现有单元测试，并为新增代码补充对应测试用例。

3. 提交代码时遵循 Conventional Commits 规范（如 `feat: 添加标签批量编辑接口`），提交信息应清晰描述变更内容与影响范围。提交前自动执行 pre-commit 钩子进行代码格式检查与静态分析。

4. 发起 Pull Request 至 develop 分支，填写 PR 模板中的检查清单，包括测试覆盖说明、文档更新情况以及是否破坏兼容性。至少需要一名项目维护者进行 Code Review 并通过所有 CI 流水线检查后方可合并。

5. 文档类贡献（包括修正拼写错误、补充 API 示例、完善部署说明）可以直接提交至 docs 目录，无需关联 Issue，但同样需要遵循 PR 流程以确保文档与代码保持同步。

## 常见问题

**问：导入的链接数量很大时，元数据提取会阻塞界面操作吗？**

答：元数据提取任务默认放入 Redis 队列中由后台工作进程异步执行，Web 界面在导入后立即返回链接列表，提取状态会逐步更新。您可以在管理后台的 "任务中心" 查看提取进度，或调整 `config/development.py` 中的 `ASYNC_BATCH_SIZE` 参数控制并发提取数量以平衡性能。

**问：链接状态监控是否会频繁请求目标网站，导致我的 IP 被封禁？**

答：监控模块内置了随机延迟间隔（默认 1-3 秒）和 User-Agent 轮换策略，每个目标链接在 24 小时内最多检测一次。您可以在配置文件中调整 `MONITOR_INTERVAL_HOURS` 和 `MONITOR_TIMEOUT` 参数，也可以将特定域名加入 `MONITOR_WHITELIST` 以提高检测频率，或加入 `MONITOR_BLACKLIST` 完全跳过检测。

**问：如何从旧版 SQLite 迁移到 PostgreSQL 用于生产环境？**

答：项目提供了迁移脚本 `scripts/migrate_sqlite_to_pg.py`，执行时需先配置目标 PostgreSQL 数据库连接字符串。该脚本会自动迁移所有表结构、索引和数据，并校验迁移前后记录数一致性。建议在迁移前备份 SQLite 文件，并在低峰时段执行。迁移完成后，请更新 `config/production.py` 中的 `SQLALCHEMY_DATABASE_URI` 指向新的 PostgreSQL 实例。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
