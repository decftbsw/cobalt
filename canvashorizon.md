# WebArchive Navigator

WebArchive Navigator 是一个面向技术研究、历史内容回溯与互联网资源存档验证的轻量级外链导航与元数据检索工具。该项目定位于帮助开发者、数据研究员、内容审核人员以及历史信息分析者，快速定位并访问散布于互联网各处的历史存档页面、新闻稿件与技术博文。通过统一的索引机制与原始外链聚合，本项目将零散的、存在失效风险的历史 URL 组织为可复用的资源清单，并提供基础的本机运行环境，以便用户在内网或本地工作站中搭建专属的历史链接门户。目标用户包括数字档案管理员、SEO 技术分析师、内容迁移工程师以及需要批量处理历史 URL 状态的自动化运维团队。

## 功能概览

批量外链导入与规范化存储 支持一次性导入大量历史 URL 记录，自动完成去重、协议校验与基础格式清洗，并按照批次编号（当前为第 286/300 批）进行标签化管理。

原始链接直出模式 所有收录的 URL 在输出与展示环节均保持用户提交时的原始字符串形态，不进行协议补全、大小写转换、末尾斜杠增删或域名规范化重写，确保与上游数据源完全一致。

轻量级本地检索服务 内置基于内存索引的简易关键词匹配功能，可根据 URL 路径中的数字 ID、文件名称或域名特征进行快速筛选，无需外部数据库即可运行。

资源批次状态追踪 为每一批次（共计 300 个资源链接）生成独立的导入时间戳、链接总数、有效可访问性预检状态（基于 HTTP HEAD 请求的离线模拟）以及异常记录列表，便于用户掌握整体数据质量。

导出与报告生成 支持将当前索引的全部原始 URL 以纯文本列表、Markdown 无序列表或 JSON 数组格式导出，方便集成到上游数据处理管道或文档系统中。

安全访问控制开关 提供可配置的本地绑定地址与端口参数，允许用户将服务限制在环回接口或指定内网网段，防止未授权的外部访问。

健康检查与存活探测 集成基于超时控制的异步 HTTP 探测功能，可批量检查每个 URL 的响应状态码（200/404/30x），并将结果汇总为结构化日志输出。

零外部依赖的静态文件服务 项目内置一个微型 HTTP 文件服务器，用于托管示例页面与资源列表，仅依赖 Python 标准库或 Node.js 内置模块，无需安装额外第三方包。

## 应用场景

数字档案室批量链接整理 档案管理人员在接收一批历史新闻页面链接（如来自旧版内容管理系统的导出文件）后，可使用 WebArchive Navigator 将这些链接统一导入并生成索引页面，方便后续按批次进行可用性审计。例如，将本批次 300 条来自 blog.bwbkj.cn 的历史文章链接集中展示，并快速筛选出响应异常的条目。

历史内容迁移前的快照比对 在将旧站点内容迁移至新域名或新架构之前，技术团队可使用本项目挂载原始 URL 清单，通过内置探测功能逐一验证源站是否仍可访问，从而决定哪些内容需要优先抓取或手动迁移，避免迁移过程中丢失仍在线的重要资料。

SEO 外链历史状态复盘 SEO 分析师在审查网站外链建设历史时，经常需要回顾多年前发布在第三方博客平台上的引用链接。通过将分散的存档 URL 导入 WebArchive Navigator，分析师可以按批次、按来源域名进行批量状态检查，快速定位已失效的链接并生成替换建议报告。

离线文档站点的导航页生成 对于需要在内网环境（如研发中心内部网络）部署离线文档中心的团队，本项目可作为导航层，将一系列无法直接通过公网访问的内部历史文章链接或归档页面整理为统一的入口页面，并利用本地服务进行展示。

自动化监控脚本的数据源 运维人员可将本项目导出的 JSON 格式链接列表作为上游数据源，输入到自定义的健康监控脚本中，定期对这批历史 URL 进行定时探测，并将异常结果推送至企业微信或邮件告警系统。

## 快速开始

以下步骤适用于 Linux / macOS / Windows（WSL 或 Git Bash）环境，需提前安装 Git 与 Python 3.8 及以上版本。

```bash
# 克隆项目仓库至本地
git clone https://github.com/example/webarchive-navigator.git
cd webarchive-navigator

# 安装依赖（项目本身无外部依赖，但若需要使用增强探测功能，可安装可选模块）
# 对于 Python 环境，建议创建虚拟环境
python3 -m venv venv
source venv/bin/activate     # Linux/macOS
# venv\Scripts\activate      # Windows

# 安装可选依赖（用于并发探测与日志格式化）
pip install aiohttp rich

# 导入本批次 URL 数据（将用户提供的原始链接列表保存为 data/batch_286.txt）
# 项目内置脚本支持从文本文件批量导入
python scripts/import_batch.py --file data/batch_286.txt --batch 286

# 启动本地导航服务（默认监听 127.0.0.1:8080）
python server.py --host 127.0.0.1 --port 8080
```

启动后，在浏览器中访问 `http://127.0.0.1:8080` 即可查看当前批次的资源索引页面，所有原始链接将按原样陈列于列表之中。

## 安装要求

| 依赖项 | 必需性 | 说明 |
|--------|--------|------|
| Python 3.8 或更高版本 | 必需 | 项目核心运行环境，用于执行服务端脚本与导入工具 |
| Git 2.20 或更高版本 | 必需 | 用于克隆仓库及版本管理，若通过压缩包安装则可选 |
| 网络连接（用于初始克隆） | 必需 | 仅首次下载仓库时需要，后续运行可完全离线 |
| aiohttp 库 | 可选 | 用于支持高并发的异步 HTTP 存活探测，若未安装则回退至同步请求 |
| rich 库 | 可选 | 提供终端美化输出与进度条显示，若不安装则使用标准 print 输出 |
| 磁盘可用空间 > 20 MB | 必需 | 用于存储索引文件、日志及静态资源，实际占用取决于导入链接数量 |
| 操作系统兼容层 | 必需 | 支持 POSIX 信号量或 Windows 事件机制，用于进程管理 |
| 浏览器（最新版 Chrome/Firefox/Edge） | 推荐 | 用于查看生成的导航页面，若仅使用 API 模式则无需浏览器 |
| 内存 > 128 MB | 必需 | 内存中索引 10000 条记录约占用 50 MB，本批次 300 条远低于此阈值 |
| 日志目录写入权限 | 必需 | 程序运行时会向 logs/ 目录写入访问日志与错误日志 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | docs/user_guide.md | 如何导入批次、启动服务、查看资源列表以及导出结果 |
| 运维指南 | docs/ops_manual.md | 如何配置绑定地址、修改端口、设置日志轮转及健康检查参数 |
| 数据格式规范 | docs/data_spec.md | 批次文件的输入格式要求（TXT / CSV / JSON）、URL 清洗规则及元数据字段定义 |
| 开发者设计文档 | docs/design.md | 项目整体架构、内存索引结构、探测并发模型及扩展接口说明 |
| API 参考 | docs/api_reference.md | 提供 JSON API 的端点列表（/list、/probe、/export），请求与响应示例 |
| 故障排除 | docs/troubleshooting.md | 常见启动失败、端口占用、探测超时及字符编码问题的解决方案 |
| 贡献者须知 | CONTRIBUTING.md | 代码风格约定、测试用例编写要求及 Pull Request 提交流程 |

## 资源列表

- http://m.blog.bwbkj.cn/snews/8176235.htm
- http://m.blog.bwbkj.cn/snews/16043.htm
- http://m.blog.bwbkj.cn/snews/902394.htm
- http://m.blog.bwbkj.cn/snews/0945.htm
- http://m.blog.bwbkj.cn/snews/100181.htm
- http://m.blog.bwbkj.cn/snews/2498086.htm
- http://m.blog.bwbkj.cn/snews/35134.htm
- http://m.blog.bwbkj.cn/snews/3042404.htm
- http://m.blog.bwbkj.cn/snews/4445462.htm
- http://m.blog.bwbkj.cn/snews/1931773.htm
- http://m.blog.bwbkj.cn/snews/7234368.htm
- http://m.blog.bwbkj.cn/snews/197410.htm
- http://m.blog.bwbkj.cn/snews/73340.htm
- http://m.blog.bwbkj.cn/snews/3923302.htm
- http://m.blog.bwbkj.cn/snews/38739.htm
- http://m.blog.bwbkj.cn/snews/8560593.htm
- http://m.blog.bwbkj.cn/snews/1534530.htm
- http://m.blog.bwbkj.cn/snews/862757.htm
- http://m.blog.bwbkj.cn/snews/5743.htm
- http://m.blog.bwbkj.cn/snews/7099.htm
- http://m.blog.bwbkj.cn/snews/17519.htm
- http://m.blog.bwbkj.cn/snews/3238.htm
- http://m.blog.bwbkj.cn/snews/7502.htm
- http://m.blog.bwbkj.cn/snews/80981.htm
- http://m.blog.bwbkj.cn/snews/337880.htm
- http://m.blog.bwbkj.cn/snews/9748.htm
- http://m.blog.bwbkj.cn/snews/6823.htm
- http://m.blog.bwbkj.cn/snews/2976050.htm
- http://m.blog.bwbkj.cn/snews/9924.htm
- http://m.blog.bwbkj.cn/snews/47816.htm
- http://m.blog.bwbkj.cn/snews/9507776.htm
- http://m.blog.bwbkj.cn/snews/569403.htm
- http://m.blog.bwbkj.cn/snews/8783985.htm
- http://m.blog.bwbkj.cn/snews/24461.htm
- http://m.blog.bwbkj.cn/snews/497841.htm
- http://m.blog.bwbkj.cn/snews/4093661.htm
- http://m.blog.bwbkj.cn/snews/3614380.htm
- http://m.blog.bwbkj.cn/snews/25698.htm
- http://m.blog.bwbkj.cn/snews/9289271.htm
- http://m.blog.bwbkj.cn/snews/3604.htm
- http://m.blog.bwbkj.cn/snews/0328.htm
- http://m.blog.bwbkj.cn/snews/79312.htm
- http://m.blog.bwbkj.cn/snews/8227940.htm
- http://m.blog.bwbkj.cn/snews/13567.htm
- http://m.blog.bwbkj.cn/snews/995306.htm
- http://m.blog.bwbkj.cn/snews/0652057.htm
- http://m.blog.bwbkj.cn/snews/2960.htm
- http://m.blog.bwbkj.cn/snews/177351.htm
- http://m.blog.bwbkj.cn/snews/832225.htm
- http://m.blog.bwbkj.cn/snews/9200304.htm
- http://m.blog.bwbkj.cn/snews/195653.htm
- http://m.blog.bwbkj.cn/snews/900995.htm
- http://m.blog.bwbkj.cn/snews/8676832.htm
- http://m.blog.bwbkj.cn/snews/77783.htm
- http://m.blog.bwbkj.cn/snews/76100.htm
- http://m.blog.bwbkj.cn/snews/2177.htm
- http://m.blog.bwbkj.cn/snews/7874679.htm
- http://m.blog.bwbkj.cn/snews/176502.htm
- http://m.blog.bwbkj.cn/snews/5413455.htm
- http://m.blog.bwbkj.cn/snews/54305.htm
- http://m.blog.bwbkj.cn/snews/6613.htm
- http://m.blog.bwbkj.cn/snews/6092984.htm
- http://m.blog.bwbkj.cn/snews/932810.htm
- http://m.blog.bwbkj.cn/snews/78414.htm
- http://m.blog.bwbkj.cn/snews/48572.htm
- http://m.blog.bwbkj.cn/snews/30250.htm
- http://m.blog.bwbkj.cn/snews/2493.htm
- http://m.blog.bwbkj.cn/snews/52952.htm
- http://m.blog.bwbkj.cn/snews/31070.htm
- http://m.blog.bwbkj.cn/snews/0655481.htm
- http://m.blog.bwbkj.cn/snews/3481803.htm
- http://m.blog.bwbkj.cn/snews/94992.htm
- http://m.blog.bwbkj.cn/snews/550948.htm
- http://m.blog.bwbkj.cn/snews/10435.htm
- http://m.blog.bwbkj.cn/snews/2845.htm
- http://m.blog.bwbkj.cn/snews/95031.htm
- http://m.blog.bwbkj.cn/snews/1391090.htm
- http://m.blog.bwbkj.cn/snews/594685.htm
- http://m.blog.bwbkj.cn/snews/66620.htm
- http://m.blog.bwbkj.cn/snews/76889.htm
- http://m.blog.bwbkj.cn/snews/4950.htm
- http://m.blog.bwbkj.cn/snews/0623.htm
- http://m.blog.bwbkj.cn/snews/57075.htm
- http://m.blog.bwbkj.cn/snews/411056.htm
- http://m.blog.bwbkj.cn/snews/17830.htm
- http://m.blog.bwbkj.cn/snews/895717.htm
- http://m.blog.bwbkj.cn/snews/184110.htm
- http://m.blog.bwbkj.cn/snews/2745942.htm
- http://m.blog.bwbkj.cn/snews/6669853.htm
- http://m.blog.bwbkj.cn/snews/73947.htm
- http://m.blog.bwbkj.cn/snews/06198.htm
- http://m.blog.bwbkj.cn/snews/1985.htm
- http://m.blog.bwbkj.cn/snews/1795962.htm
- http://m.blog.bwbkj.cn/snews/2622908.htm
- http://m.blog.bwbkj.cn/snews/020636.htm
- http://m.blog.bwbkj.cn/snews/99101.htm
- http://m.blog.bwbkj.cn/snews/9607042.htm
- http://m.blog.bwbkj.cn/snews/4098093.htm
- http://m.blog.bwbkj.cn/snews/0565778.htm
- http://m.blog.bwbkj.cn/snews/620022.htm
- http://m.blog.bwbkj.cn/snews/8422133.htm
- http://m.blog.bwbkj.cn/snews/4255.htm
- http://m.blog.bwbkj.cn/snews/65456.htm
- http://m.blog.bwbkj.cn/snews/12158.htm
- http://m.blog.bwbkj.cn/snews/389957.htm
- http://m.blog.bwbkj.cn/snews/460015.htm
- http://m.blog.bwbkj.cn/snews/16649.htm
- http://m.blog.bwbkj.cn/snews/4855040.htm
- http://m.blog.bwbkj.cn/snews/17022.htm
- http://m.blog.bwbkj.cn/snews/8514986.htm
- http://m.blog.bwbkj.cn/snews/64299.htm
- http://m.blog.bwbkj.cn/snews/80885.htm
- http://m.blog.bwbkj.cn/snews/532932.htm
- http://m.blog.bwbkj.cn/snews/3767555.htm
- http://m.blog.bwbkj.cn/snews/32952.htm
- http://m.blog.bwbkj.cn/snews/95639.htm
- http://m.blog.bwbkj.cn/snews/008559.htm
- http://m.blog.bwbkj.cn/snews/005780.htm
- http://m.blog.bwbkj.cn/snews/9117958.htm
- http://m.blog.bwbkj.cn/snews/2471855.htm
- http://m.blog.bwbkj.cn/snews/15247.htm
- http://m.blog.bwbkj.cn/snews/452675.htm
- http://m.blog.bwbkj.cn/snews/7204.htm
- http://m.blog.bwbkj.cn/snews/6338378.htm
- http://m.blog.bwbkj.cn/snews/6172.htm
- http://m.blog.bwbkj.cn/snews/5190940.htm
- http://m.blog.bwbkj.cn/snews/5902.htm
- http://m.blog.bwbkj.cn/snews/7885.htm
- http://m.blog.bwbkj.cn/snews/28652.htm
- http://m.blog.bwbkj.cn/snews/516512.htm
- http://m.blog.bwbkj.cn/snews/964666.htm
- http://m.blog.bwbkj.cn/snews/7587.htm
- http://m.blog.bwbkj.cn/snews/67725.htm
- http://m.blog.bwbkj.cn/snews/45488.htm
- http://m.blog.bwbkj.cn/snews/70406.htm
- http://m.blog.bwbkj.cn/snews/3332.htm
- http://m.blog.bwbkj.cn/snews/4963.htm
- http://m.blog.bwbkj.cn/snews/388430.htm
- http://m.blog.bwbkj.cn/snews/3329.htm
- http://m.blog.bwbkj.cn/snews/2402321.htm
- http://m.blog.bwbkj.cn/snews/3691.htm
- http://m.blog.bwbkj.cn/snews/422771.htm
- http://m.blog.bwbkj.cn/snews/52652.htm
- http://m.blog.bwbkj.cn/snews/240423.htm
- http://m.blog.bwbkj.cn/snews/796629.htm
- http://m.blog.bwbkj.cn/snews/712560.htm
- http://m.blog.bwbkj.cn/snews/2200.htm
- http://m.blog.bwbkj.cn/snews/2637835.htm
- http://m.blog.bwbkj.cn/snews/866043.htm
- http://m.blog.bwbkj.cn/snews/00344.htm
- http://m.blog.bwbkj.cn/snews/228656.htm
- http://m.blog.bwbkj.cn/snews/85400.htm
- http://m.blog.bwbkj.cn/snews/3947.htm
- http://m.blog.bwbkj.cn/snews/2040.htm
- http://m.blog.bwbkj.cn/snews/119014.htm
- http://m.blog.bwbkj.cn/snews/7748.htm
- http://m.blog.bwbkj.cn/snews/13584.htm
- http://m.blog.bwbkj.cn/snews/10254.htm
- http://m.blog.bwbkj.cn/snews/59335.htm
- http://m.blog.bwbkj.cn/snews/802131.htm
- http://m.blog.bwbkj.cn/snews/209955.htm
- http://m.blog.bwbkj.cn/snews/1268.htm
- http://m.blog.bwbkj.cn/snews/192767.htm
- http://m.blog.bwbkj.cn/snews/3177.htm
- http://m.blog.bwbkj.cn/snews/1587.htm
- http://m.blog.bwbkj.cn/snews/5867501.htm
- http://m.blog.bwbkj.cn/snews/33632.htm
- http://m.blog.bwbkj.cn/snews/47702.htm
- http://m.blog.bwbkj.cn/snews/976257.htm
- http://m.blog.bwbkj.cn/snews/391931.htm
- http://m.blog.bwbkj.cn/snews/606388.htm
- http://m.blog.bwbkj.cn/snews/85441.htm
- http://m.blog.bwbkj.cn/snews/7189.htm
- http://m.blog.bwbkj.cn/snews/362174.htm
- http://m.blog.bwbkj.cn/snews/7649.htm
- http://m.blog.bwbkj.cn/snews/8242.htm
- http://m.blog.bwbkj.cn/snews/01644.htm
- http://m.blog.bwbkj.cn/snews/6093.htm
- http://m.blog.bwbkj.cn/snews/0454888.htm
- http://m.blog.bwbkj.cn/snews/9357484.htm
- http://m.blog.bwbkj.cn/snews/86234.htm
- http://m.blog.bwbkj.cn/snews/0854252.htm
- http://m.blog.bwbkj.cn/snews/9513013.htm
- http://m.blog.bwbkj.cn/snews/4901.htm
- http://m.blog.bwbkj.cn/snews/9378498.htm
- http://m.blog.bwbkj.cn/snews/3900.htm
- http://m.blog.bwbkj.cn/snews/1519900.htm
- http://m.blog.bwbkj.cn/snews/94803.htm
- http://m.blog.bwbkj.cn/snews/8318.htm
- http://m.blog.bwbkj.cn/snews/6278680.htm
- http://m.blog.bwbkj.cn/snews/4597.htm
- http://m.blog.bwbkj.cn/snews/1556086.htm
- http://m.blog.bwbkj.cn/snews/0182.htm
- http://m.blog.bwbkj.cn/snews/4556062.htm
- http://m.blog.bwbkj.cn/snews/5611.htm
- http://m.blog.bwbkj.cn/snews/1997.htm
- http://m.blog.bwbkj.cn/snews/4275007.htm
- http://m.blog.bwbkj.cn/snews/6360251.htm
- http://m.blog.bwbkj.cn/snews/79627.htm
- http://m.blog.bwbkj.cn/snews/7149.htm
- http://m.blog.bwbkj.cn/snews/4573790.htm
- http://m.blog.bwbkj.cn/snews/469558.htm
- http://m.blog.bwbkj.cn/snews/9459194.htm
- http://m.blog.bwbkj.cn/snews/1550.htm
- http://m.blog.bwbkj.cn/snews/5268.htm
- http://m.blog.bwbkj.cn/snews/55237.htm
- http://m.blog.bwbkj.cn/snews/64322.htm
- http://m.blog.bwbkj.cn/snews/518869.htm
- http://m.blog.bwbkj.cn/snews/3885909.htm
- http://m.blog.bwbkj.cn/snews/4468.htm
- http://m.blog.bwbkj.cn/snews/6711350.htm
- http://m.blog.bwbkj.cn/snews/06175.htm
- http://m.blog.bwbkj.cn/snews/361486.htm
- http://m.blog.bwbkj.cn/snews/179755.htm
- http://m.blog.bwbkj.cn/snews/77180.htm
- http://m.blog.bwbkj.cn/snews/016678.htm
- http://m.blog.bwbkj.cn/snews/607674.htm
- http://m.blog.bwbkj.cn/snews/04927.htm
- http://m.blog.bwbkj.cn/snews/9329492.htm
- http://m.blog.bwbkj.cn/snews/668182.htm
- http://m.blog.bwbkj.cn/snews/4724.htm
- http://m.blog.bwbkj.cn/snews/8101024.htm
- http://m.blog.bwbkj.cn/snews/3370619.htm
- http://m.blog.bwbkj.cn/snews/1090.htm
- http://m.blog.bwbkj.cn/snews/824627.htm
- http://m.blog.bwbkj.cn/snews/748852.htm
- http://m.blog.bwbkj.cn/snews/54692.htm
- http://m.blog.bwbkj.cn/snews/0735.htm
- http://m.blog.bwbkj.cn/snews/02403.htm
- http://m.blog.bwbkj.cn/snews/10422.htm
- http://m.blog.bwbkj.cn/snews/3826710.htm
- http://m.blog.bwbkj.cn/snews/721921.htm
- http://m.blog.bwbkj.cn/snews/4959078.htm
- http://m.blog.bwbkj.cn/snews/18382.htm
- http://m.blog.bwbkj.cn/snews/928128.htm
- http://m.blog.bwbkj.cn/snews/0632.htm
- http://m.blog.bwbkj.cn/snews/078633.htm
- http://m.blog.bwbkj.cn/snews/678434.htm
- http://m.blog.bwbkj.cn/snews/65965.htm
- http://m.blog.bwbkj.cn/snews/261634.htm
- http://m.blog.bwbkj.cn/snews/382602.htm
- http://m.blog.bwbkj.cn/snews/2047.htm
- http://m.blog.bwbkj.cn/snews/8771212.htm
- http://m.blog.bwbkj.cn/snews/8149919.htm
- http://m.blog.bwbkj.cn/snews/996920.htm
- http://m.blog.bwbkj.cn/snews/35117.htm
- http://m.blog.bwbkj.cn/snews/291587.htm
- http://m.blog.bwbkj.cn/snews/646017.htm
- http://m.blog.bwbkj.cn/snews/6642.htm
- http://m.blog.bwbkj.cn/snews/3105.htm
- http://m.blog.bwbkj.cn/snews/10351.htm
- http://m.blog.bwbkj.cn/snews/06689.htm
- http://m.blog.bwbkj.cn/snews/8592507.htm
- http://m.blog.bwbkj.cn/snews/2981890.htm
- http://m.blog.bwbkj.cn/snews/3557532.htm
- http://m.blog.bwbkj.cn/snews/4747.htm
- http://m.blog.bwbkj.cn/snews/021008.htm
- http://m.blog.bwbkj.cn/snews/88015.htm
- http://m.blog.bwbkj.cn/snews/324367.htm
- http://m.blog.bwbkj.cn/snews/4124.htm
- http://m.blog.bwbkj.cn/snews/7253836.htm
- http://m.blog.bwbkj.cn/snews/4746124.htm
- http://m.blog.bwbkj.cn/snews/7999494.htm
- http://m.blog.bwbkj.cn/snews/97986.htm
- http://m.blog.bwbkj.cn/snews/0884.htm
- http://m.blog.bwbkj.cn/snews/9848414.htm
- http://m.blog.bwbkj.cn/snews/199249.htm
- http://m.blog.bwbkj.cn/snews/4842015.htm
- http://m.blog.bwbkj.cn/snews/87542.htm
- http://m.blog.bwbkj.cn/snews/1650228.htm
- http://m.blog.bwbkj.cn/snews/874561.htm
- http://m.blog.bwbkj.cn/snews/8718.htm
- http://m.blog.bwbkj.cn/snews/998880.htm
- http://m.blog.bwbkj.cn/snews/58632.htm
- http://m.blog.bwbkj.cn/snews/98446.htm
- http://m.blog.bwbkj.cn/snews/30829.htm
- http://m.blog.bwbkj.cn/snews/269530.htm
- http://m.blog.bwbkj.cn/snews/02850.htm
- http://m.blog.bwbkj.cn/snews/153053.htm
- http://m.blog.bwbkj.cn/snews/3443.htm
- http://m.blog.bwbkj.cn/snews/399272.htm
- http://m.blog.bwbkj.cn/snews/1099.htm
- http://m.blog.bwbkj.cn/snews/78328.htm
- http://m.blog.bwbkj.cn/snews/958654.htm
- http://m.blog.bwbkj.cn/snews/631895.htm
- http://m.blog.bwbkj.cn/snews/2258.htm
- http://m.blog.bwbkj.cn/snews/8207.htm
- http://m.blog.bwbkj.cn/snews/050783.htm
- http://m.blog.bwbkj.cn/snews/56086.htm
- http://m.blog.bwbkj.cn/snews/3123.htm
- http://m.blog.bwbkj.cn/snews/495583.htm
- http://m.blog.bwbkj.cn/snews/6879.htm
- http://m.blog.bwbkj.cn/snews/4955.htm
- http://m.blog.bwbkj.cn/snews/365694.htm
- http://m.blog.bwbkj.cn/snews/1114.htm
- http://m.blog.bwbkj.cn/snews/1697617.htm
- http://m.blog.bwbkj.cn/snews/81814.htm
- http://m.blog.bwbkj.cn/snews/65933.htm
- http://m.blog.bwbkj.cn/snews/5947020.htm
- http://m.blog.bwbkj.cn/snews/90114.htm

## 项目结构

```
webarchive-navigator/
├── server.py                 # 主服务入口，基于标准库构建HTTP服务器
├── config.yaml               # 全局配置文件，包含绑定地址、端口、超时阈值等
├── requirements.txt          # 可选依赖清单，供pip安装使用
├── README.md                 # 项目说明文档（即当前文件）
├── LICENSE                   # MIT许可证文本
│
├── data/                     # 数据存储目录
│   ├── batches/              # 按批次号存放导入的原始链接文件
│   │   └── batch_286.txt     # 本批次原始URL列表（用户原始数据）
│   ├── index.db              # 内存索引持久化镜像（JSON格式）
│   └── manifest.json         # 批次元数据记录（导入时间、条数、状态）
│
├── scripts/                  # 辅助工具脚本目录
│   ├── import_batch.py       # 批量导入脚本，支持TXT/CSV格式
│   ├── export_formats.py     # 导出为纯文本/JSON/Markdown列表
│   ├── probe_batch.py        # 存活探测脚本，生成状态报告
│   └── health_check.py       # 周期性健康检查调度器
│
├── src/                      # 核心源码目录
│   ├── indexer.py            # 内存索引构建与查询模块
│   ├── loader.py             # 文件加载与解析器
│   ├── probe.py              # 异步HTTP探测实现
│   ├── logger.py             # 日志格式化与轮转模块
│   └── validator.py          # URL格式校验与清洗工具
│
├── templates/                # 静态HTML模板目录
│   ├── index.html            # 默认导航首页模板
│   ├── list.html             # 资源列表渲染模板
│   └── error.html            # 错误提示页面
│
├── logs/                     # 运行日志存储目录（自动创建）
│   ├── access.log            # HTTP访问日志
│   ├── error.log             # 错误与异常日志
│   └── probe_report.log      # 探测任务输出日志
│
└── tests/                    # 单元测试与集成测试目录
    ├── test_indexer.py       # 索引模块测试用例
    ├── test_probe.py         # 探测模块测试用例
    └── test_loader.py        # 加载器测试用例
```

## 贡献指南

提交代码或文档更新前，请确保遵循以下流程，以保证项目的一致性与可维护性。

首先，在 GitHub 上 fork 本仓库至个人账户，并将 fork 后的仓库克隆到本地开发环境中。建议在新建的功能分支上开展工作，分支命名遵循 `feature/描述` 或 `fix/描述` 的格式，例如 `feature/add-json-export`。

其次，完成代码修改后，请确保所有现有单元测试能够通过，并为新增功能或修复的缺陷补充对应的测试用例。测试文件需放置在 `tests/` 目录下，命名与对应模块保持一致。执行测试可使用 `python -m unittest discover tests` 命令。

第三，提交代码前，请运行代码风格检查工具（如 `flake8` 或 `pylint`），确保代码符合 PEP 8 规范。同时，更新 `docs/` 目录下受影响的文档，并在 `CHANGELOG.md` 中记录本次变更的类型（新增、修复、废弃）及简要描述。

第四，发起 Pull Request 至主仓库的 `main` 分支。PR 描述中应清晰说明改动目的、实现方式以及测试覆盖情况。项目维护者将在 48 小时内进行评审，若需要进一步修改，会通过评论方式反馈。

最后，对于非代码类的贡献（如文档改进、翻译、示例补充），可直接在 `docs/` 目录下编辑并提交 PR，无需强制关联测试用例。但需确保文档格式采用 Markdown 标准语法，且无拼写错误。

## 常见问题

**问：导入 URL 时提示“格式校验失败”，但我的链接明明是合法的 HTTP 地址，怎么办？**

答：本项目的校验器默认启用了严格的路径规则检查。若原始链接包含非常规字符（如中文未编码部分、多余空格或控制字符），校验器会拒绝导入。解决方法是：首先检查原始文本是否为纯 ASCII 编码，若包含非 ASCII 字符，请先进行 URL 编码（Percent-encoding）。此外，校验器要求路径部分不得为空，且必须包含至少一个斜杠。对于 `http://m.blog.bwbkj.cn/snews/8176235.htm` 这类格式，校验器能够正常识别。若仍无法通过，可在 `config.yaml` 中将 `strict_validation` 设置为 `false` 以绕过校验，但需自行承担无效链接导入后的风险。

**问：启动服务后，浏览器无法访问 `127.0.0.1:8080`，显示“连接被拒绝”，如何排查？**

答：该问题通常由端口占用或绑定地址限制引起。首先检查终端输出是否显示 `Address already in use` 错误，若是，请更换端口号（如 `--port 8081`）或终止占用进程。其次，确认启动命令中 `--host` 参数是否为 `127.0.0.1`，如果设置为 `0.0.0.0`，则需使用本机实际 IP 访问。此外，检查操作系统防火墙是否阻止了该端口的入站连接（特别是 Windows 系统），可尝试临时关闭防火墙或添加允许规则。最后，确认 Python 版本为 3.8 及以上，低版本可能不支持某些标准库 API。

**问：探测功能显示大量链接超时，但我在浏览器中手动访问这些链接是正常的，为什么？**

答：本项目的探测模块默认超时时间为 3 秒，且使用异步并发请求，若目标服务器对批量请求有频率限制或较慢的响应时间，可能导致超时。建议通过 `config.yaml` 中的 `probe_timeout` 参数调整超时阈值（例如设为 10 秒），并减少并发数（`max_concurrent` 参数）。另外，某些服务器会针对非浏览器 User-Agent 返回 403 或 429 状态码，此时可在配置中修改 `user_agent` 字段为常见的浏览器标识。如果探测结果仍不理想，可考虑使用脚本的 `--retry` 选项启用重试机制。

## 许可证

本项目采用 MIT 许可证。有关详细信息，请参阅项目根目录下的 LICENSE 文件。

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:13
