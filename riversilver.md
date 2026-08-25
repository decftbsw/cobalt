# WebLink Navigator

WebLink Navigator 是一个面向技术调研人员、内容聚合者与运维工程师的轻量级外链资源导航与快照归档工具。该项目不依赖复杂前端框架，以静态站点生成器为核心，将分散于各处的新闻、公告、技术文档链接进行结构化整理，并提供本地检索与标签过滤能力。

项目定位为“技术外链的元数据登记表”，解决以下问题：技术团队在调研过程中积累的大量散乱 URL 难以追溯、链接失效后无法找回原始内容、不同成员之间共享链接缺乏统一格式。WebLink Navigator 通过生成一份可离线访问的 Markdown 索引页面，配合简单的 Python 脚本实现链接可用性检测和元信息提取，帮助团队在 30 秒内完成一批链接的登记与分类。

## 功能概览

- **批量链接导入** 支持从纯文本文件、CSV 或直接粘贴的 URL 列表中批量导入链接，自动去重并识别域名归属。

- **元信息自动补全** 对每个 URL 发起轻量级 HEAD 请求，获取响应状态码、内容类型、最后修改时间，并尝试从 HTML Title 中提取页面标题。

- **状态监控看板** 生成一个状态总览表格，用颜色标记链接的可用性（绿色正常、黄色重定向、红色失效），便于定期巡检。

- **标签与分类系统** 允许用户为每条链接添加自定义标签（如“新闻”“文档”“API 参考”），并支持按标签筛选和统计。

- **快照存储机制** 对于标记为“重要”的链接，自动保存页面的 Markdown 化正文快照至本地仓库，防止原文删除后信息丢失。

- **静态站点导出** 一键生成完整的静态 HTML 站点，包含索引页、分类页和标签云，可直接部署到 Nginx 或 GitHub Pages 供团队内部访问。

- **定时任务集成** 提供 crontab 兼容的调度脚本，支持每日凌晨自动检测所有链接的有效性，并生成变更报告。

## 应用场景

1. 技术调研阶段的外链整理：工程师在阅读技术博客或论文时，将引用到的所有外部链接统一录入系统，并标注重要程度，后续撰写调研报告时可直接引用索引编号。

2. 运维知识库的补充材料：运维团队将常用监控面板、日志查询入口、内部 Wiki 链接集中托管，配合快照功能避免内部文档迁移后入口丢失。

3. 内容聚合站点预处理：内容编辑人员将每日从 RSS 或邮件订阅中获取的新闻链接批量导入，项目自动抓取标题和摘要，辅助人工筛选后发布到正式站点。

4. 合规审计的链接留底：法务或合规部门将需要定期复查的外部政策链接导入系统，每次运行时对比快照差异，及时发现页面变动。

## 快速开始

```bash
# 克隆仓库
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator

# 安装依赖（推荐使用 Python 3.9+ 虚拟环境）
python -m venv venv
source venv/bin/activate  # Windows 下使用 venv\Scripts\activate
pip install -r requirements.txt

# 运行导入与生成流程（以本批次资源为例）
python weblink.py --input ./batch_236.txt --output ./docs/index.md --check
```

其中 `batch_236.txt` 文件内容即为资源列表中的全部 URL，每行一个。执行完成后，`./docs/index.md` 将生成包含所有链接的导航页，`--check` 参数会同时执行一次可用性探测。

## 安装要求

| 依赖 | 必需版本 | 说明 |
|------|----------|------|
| Python | 3.9 或更高 | 核心运行环境，3.8 及以下版本不支持 `http.client` 的部分新特性 |
| requests | 2.28.0+ | 用于发送 HTTP 请求获取状态码与响应头，替代标准库 `urllib` |
| beautifulsoup4 | 4.11.0+ | 解析 HTML 页面标题和正文，为快照功能提供支持 |
| markdown | 3.4.0+ | 将生成的 Markdown 索引转换为静态 HTML 页面 |
| pyyaml | 6.0+ | 读取用户配置文件 `config.yaml`，支持自定义标签和忽略列表 |
| click | 8.1.0+ | 命令行参数解析，提供 `--input`、`--output`、`--check` 等子命令 |
| tqdm | 4.64.0+ | 批量链接处理时显示进度条，提升交互体验 |
| html5lib | 1.1+ | beautifulsoup4 的备选解析器，处理不规范的 HTML 页面 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|------|------|------------|
| 用户手册 | `docs/user_guide.md` | 如何安装、配置、运行批量导入任务，以及如何解读状态报告 |
| 开发指南 | `docs/dev_guide.md` | 项目模块划分、自定义插件接口说明、单元测试运行方法 |
| 配置参考 | `docs/config_reference.md` | `config.yaml` 中所有字段的详细说明，包括代理设置、超时阈值、标签别名 |
| 部署说明 | `docs/deployment.md` | 如何将生成的静态站点部署到 Nginx、Apache 或 S3 存储桶 |
| 故障排查 | `docs/troubleshooting.md` | 常见运行错误（如 SSL 证书问题、内存不足、编码异常）的解决方案 |

## 资源列表

- http://m.wap.bwbkj.cn/snews/2126.htm
- http://m.wap.bwbkj.cn/snews/2659604.htm
- http://m.wap.bwbkj.cn/snews/8581177.htm
- http://m.wap.bwbkj.cn/snews/2669.htm
- http://m.wap.bwbkj.cn/snews/7603373.htm
- http://m.wap.bwbkj.cn/snews/6444.htm
- http://m.wap.bwbkj.cn/snews/94081.htm
- http://m.wap.bwbkj.cn/snews/7063899.htm
- http://m.wap.bwbkj.cn/snews/632375.htm
- http://m.wap.bwbkj.cn/snews/05400.htm
- http://m.wap.bwbkj.cn/snews/79213.htm
- http://m.wap.bwbkj.cn/snews/78836.htm
- http://m.wap.bwbkj.cn/snews/8170.htm
- http://m.wap.bwbkj.cn/snews/4385231.htm
- http://m.wap.bwbkj.cn/snews/2238662.htm
- http://m.wap.bwbkj.cn/snews/30520.htm
- http://m.wap.bwbkj.cn/snews/8113.htm
- http://m.wap.bwbkj.cn/snews/50372.htm
- http://m.wap.bwbkj.cn/snews/5218.htm
- http://m.wap.bwbkj.cn/snews/422905.htm
- http://m.wap.bwbkj.cn/snews/8899.htm
- http://m.wap.bwbkj.cn/snews/56877.htm
- http://m.wap.bwbkj.cn/snews/59589.htm
- http://m.wap.bwbkj.cn/snews/2221.htm
- http://m.wap.bwbkj.cn/snews/5028121.htm
- http://m.wap.bwbkj.cn/snews/0175.htm
- http://m.wap.bwbkj.cn/snews/9503547.htm
- http://m.wap.bwbkj.cn/snews/00665.htm
- http://m.wap.bwbkj.cn/snews/44979.htm
- http://m.wap.bwbkj.cn/snews/5925.htm
- http://m.wap.bwbkj.cn/snews/92210.htm
- http://m.wap.bwbkj.cn/snews/6341861.htm
- http://m.wap.bwbkj.cn/snews/469931.htm
- http://m.wap.bwbkj.cn/snews/745296.htm
- http://m.wap.bwbkj.cn/snews/10239.htm
- http://m.wap.bwbkj.cn/snews/2731923.htm
- http://m.wap.bwbkj.cn/snews/96469.htm
- http://m.wap.bwbkj.cn/snews/2542328.htm
- http://m.wap.bwbkj.cn/snews/119718.htm
- http://m.wap.bwbkj.cn/snews/376141.htm
- http://m.wap.bwbkj.cn/snews/90276.htm
- http://m.wap.bwbkj.cn/snews/13101.htm
- http://m.wap.bwbkj.cn/snews/735616.htm
- http://m.wap.bwbkj.cn/snews/500687.htm
- http://m.wap.bwbkj.cn/snews/121960.htm
- http://m.wap.bwbkj.cn/snews/115524.htm
- http://m.wap.bwbkj.cn/snews/5038778.htm
- http://m.wap.bwbkj.cn/snews/559845.htm
- http://m.wap.bwbkj.cn/snews/3431.htm
- http://m.wap.bwbkj.cn/snews/0369113.htm
- http://m.wap.bwbkj.cn/snews/75426.htm
- http://m.wap.bwbkj.cn/snews/3852277.htm
- http://m.wap.bwbkj.cn/snews/92624.htm
- http://m.wap.bwbkj.cn/snews/34482.htm
- http://m.wap.bwbkj.cn/snews/998470.htm
- http://m.wap.bwbkj.cn/snews/2810.htm
- http://m.wap.bwbkj.cn/snews/10951.htm
- http://m.wap.bwbkj.cn/snews/8936217.htm
- http://m.wap.bwbkj.cn/snews/52834.htm
- http://m.wap.bwbkj.cn/snews/2530587.htm
- http://m.wap.bwbkj.cn/snews/7042.htm
- http://m.wap.bwbkj.cn/snews/5999.htm
- http://m.wap.bwbkj.cn/snews/5288734.htm
- http://m.wap.bwbkj.cn/snews/6809.htm
- http://m.wap.bwbkj.cn/snews/8449395.htm
- http://m.wap.bwbkj.cn/snews/61722.htm
- http://m.wap.bwbkj.cn/snews/532930.htm
- http://m.wap.bwbkj.cn/snews/2609624.htm
- http://m.wap.bwbkj.cn/snews/4357512.htm
- http://m.wap.bwbkj.cn/snews/6028594.htm
- http://m.wap.bwbkj.cn/snews/5822236.htm
- http://m.wap.bwbkj.cn/snews/0692145.htm
- http://m.wap.bwbkj.cn/snews/4085.htm
- http://m.wap.bwbkj.cn/snews/23897.htm
- http://m.wap.bwbkj.cn/snews/080351.htm
- http://m.wap.bwbkj.cn/snews/125835.htm
- http://m.wap.bwbkj.cn/snews/0835.htm
- http://m.wap.bwbkj.cn/snews/87508.htm
- http://m.wap.bwbkj.cn/snews/3536.htm
- http://m.wap.bwbkj.cn/snews/3854617.htm
- http://m.wap.bwbkj.cn/snews/8208.htm
- http://m.wap.bwbkj.cn/snews/961883.htm
- http://m.wap.bwbkj.cn/snews/95824.htm
- http://m.wap.bwbkj.cn/snews/0129.htm
- http://m.wap.bwbkj.cn/snews/263912.htm
- http://m.wap.bwbkj.cn/snews/6330284.htm
- http://m.wap.bwbkj.cn/snews/2190.htm
- http://m.wap.bwbkj.cn/snews/3320347.htm
- http://m.wap.bwbkj.cn/snews/4319800.htm
- http://m.wap.bwbkj.cn/snews/06921.htm
- http://m.wap.bwbkj.cn/snews/2099.htm
- http://m.wap.bwbkj.cn/snews/4833661.htm
- http://m.wap.bwbkj.cn/snews/73085.htm
- http://m.wap.bwbkj.cn/snews/0344937.htm
- http://m.wap.bwbkj.cn/snews/15786.htm
- http://m.wap.bwbkj.cn/snews/4460153.htm
- http://m.wap.bwbkj.cn/snews/6575200.htm
- http://m.wap.bwbkj.cn/snews/0827193.htm
- http://m.wap.bwbkj.cn/snews/6299778.htm
- http://m.wap.bwbkj.cn/snews/233469.htm
- http://m.wap.bwbkj.cn/snews/473660.htm
- http://m.wap.bwbkj.cn/snews/004326.htm
- http://m.wap.bwbkj.cn/snews/26415.htm
- http://m.wap.bwbkj.cn/snews/21236.htm
- http://m.wap.bwbkj.cn/snews/0251157.htm
- http://m.wap.bwbkj.cn/snews/7627225.htm
- http://m.wap.bwbkj.cn/snews/357187.htm
- http://m.wap.bwbkj.cn/snews/65791.htm
- http://m.wap.bwbkj.cn/snews/47136.htm
- http://m.wap.bwbkj.cn/snews/8805.htm
- http://m.wap.bwbkj.cn/snews/507417.htm
- http://m.wap.bwbkj.cn/snews/93714.htm
- http://m.wap.bwbkj.cn/snews/0243.htm
- http://m.wap.bwbkj.cn/snews/15862.htm
- http://m.wap.bwbkj.cn/snews/41232.htm
- http://m.wap.bwbkj.cn/snews/7150279.htm
- http://m.wap.bwbkj.cn/snews/1436.htm
- http://m.wap.bwbkj.cn/snews/287986.htm
- http://m.wap.bwbkj.cn/snews/28531.htm
- http://m.wap.bwbkj.cn/snews/9543.htm
- http://m.wap.bwbkj.cn/snews/899071.htm
- http://m.wap.bwbkj.cn/snews/4759.htm
- http://m.wap.bwbkj.cn/snews/764595.htm
- http://m.wap.bwbkj.cn/snews/37461.htm
- http://m.wap.bwbkj.cn/snews/0877.htm
- http://m.wap.bwbkj.cn/snews/0315.htm
- http://m.wap.bwbkj.cn/snews/213510.htm
- http://m.wap.bwbkj.cn/snews/1823553.htm
- http://m.wap.bwbkj.cn/snews/650663.htm
- http://m.wap.bwbkj.cn/snews/83601.htm
- http://m.wap.bwbkj.cn/snews/7178926.htm
- http://m.wap.bwbkj.cn/snews/7095.htm
- http://m.wap.bwbkj.cn/snews/7163.htm
- http://m.wap.bwbkj.cn/snews/4178.htm
- http://m.wap.bwbkj.cn/snews/08316.htm
- http://m.wap.bwbkj.cn/snews/080118.htm
- http://m.wap.bwbkj.cn/snews/36666.htm
- http://m.wap.bwbkj.cn/snews/8401646.htm
- http://m.wap.bwbkj.cn/snews/429838.htm
- http://m.wap.bwbkj.cn/snews/4932535.htm
- http://m.wap.bwbkj.cn/snews/261998.htm
- http://m.wap.bwbkj.cn/snews/7927122.htm
- http://m.wap.bwbkj.cn/snews/621216.htm
- http://m.wap.bwbkj.cn/snews/585549.htm
- http://m.wap.bwbkj.cn/snews/08202.htm
- http://m.wap.bwbkj.cn/snews/773024.htm
- http://m.wap.bwbkj.cn/snews/4995.htm
- http://m.wap.bwbkj.cn/snews/5209891.htm
- http://m.wap.bwbkj.cn/snews/0247.htm
- http://m.wap.bwbkj.cn/snews/226850.htm
- http://m.wap.bwbkj.cn/snews/091266.htm
- http://m.wap.bwbkj.cn/snews/277395.htm
- http://m.wap.bwbkj.cn/snews/61088.htm
- http://m.wap.bwbkj.cn/snews/060381.htm
- http://m.wap.bwbkj.cn/snews/32065.htm
- http://m.wap.bwbkj.cn/snews/4644.htm
- http://m.wap.bwbkj.cn/snews/10257.htm
- http://m.wap.bwbkj.cn/snews/2574518.htm
- http://m.wap.bwbkj.cn/snews/9224785.htm
- http://m.wap.bwbkj.cn/snews/69334.htm
- http://m.wap.bwbkj.cn/snews/2590.htm
- http://m.wap.bwbkj.cn/snews/32740.htm
- http://m.wap.bwbkj.cn/snews/22890.htm
- http://m.wap.bwbkj.cn/snews/4283545.htm
- http://m.wap.bwbkj.cn/snews/26027.htm
- http://m.wap.bwbkj.cn/snews/7372617.htm
- http://m.wap.bwbkj.cn/snews/6251.htm
- http://m.wap.bwbkj.cn/snews/6072.htm
- http://m.wap.bwbkj.cn/snews/6584936.htm
- http://m.wap.bwbkj.cn/snews/0000.htm
- http://m.wap.bwbkj.cn/snews/8410.htm
- http://m.wap.bwbkj.cn/snews/1089.htm
- http://m.wap.bwbkj.cn/snews/290285.htm
- http://m.wap.bwbkj.cn/snews/1369670.htm
- http://m.wap.bwbkj.cn/snews/046231.htm
- http://m.wap.bwbkj.cn/snews/95202.htm
- http://m.wap.bwbkj.cn/snews/576765.htm
- http://m.wap.bwbkj.cn/snews/2407458.htm
- http://m.wap.bwbkj.cn/snews/140470.htm
- http://m.wap.bwbkj.cn/snews/065143.htm
- http://m.wap.bwbkj.cn/snews/7338.htm
- http://m.wap.bwbkj.cn/snews/35815.htm
- http://m.wap.bwbkj.cn/snews/26364.htm
- http://m.wap.bwbkj.cn/snews/1546.htm
- http://m.wap.bwbkj.cn/snews/2855417.htm
- http://m.wap.bwbkj.cn/snews/592061.htm
- http://m.wap.bwbkj.cn/snews/2938.htm
- http://m.wap.bwbkj.cn/snews/38982.htm
- http://m.wap.bwbkj.cn/snews/9532605.htm
- http://m.wap.bwbkj.cn/snews/9099.htm
- http://m.wap.bwbkj.cn/snews/1330376.htm
- http://m.wap.bwbkj.cn/snews/35067.htm
- http://m.wap.bwbkj.cn/snews/615946.htm
- http://m.wap.bwbkj.cn/snews/8633219.htm
- http://m.wap.bwbkj.cn/snews/8671.htm
- http://m.wap.bwbkj.cn/snews/6367.htm
- http://m.wap.bwbkj.cn/snews/357547.htm
- http://m.wap.bwbkj.cn/snews/0322063.htm
- http://m.wap.bwbkj.cn/snews/25882.htm
- http://m.wap.bwbkj.cn/snews/95028.htm
- http://m.wap.bwbkj.cn/snews/0826283.htm
- http://m.wap.bwbkj.cn/snews/4871352.htm
- http://m.wap.bwbkj.cn/snews/1949.htm
- http://m.wap.bwbkj.cn/snews/5024474.htm
- http://m.wap.bwbkj.cn/snews/81901.htm
- http://m.wap.bwbkj.cn/snews/4603366.htm
- http://m.wap.bwbkj.cn/snews/7381615.htm
- http://m.wap.bwbkj.cn/snews/9392.htm
- http://m.wap.bwbkj.cn/snews/816930.htm
- http://m.wap.bwbkj.cn/snews/672186.htm
- http://m.wap.bwbkj.cn/snews/3304768.htm
- http://m.wap.bwbkj.cn/snews/0791719.htm
- http://m.wap.bwbkj.cn/snews/630740.htm
- http://m.wap.bwbkj.cn/snews/200667.htm
- http://m.wap.bwbkj.cn/snews/8581410.htm
- http://m.wap.bwbkj.cn/snews/6614.htm
- http://m.wap.bwbkj.cn/snews/204804.htm
- http://m.wap.bwbkj.cn/snews/95495.htm
- http://m.wap.bwbkj.cn/snews/165763.htm
- http://m.wap.bwbkj.cn/snews/2070953.htm
- http://m.wap.bwbkj.cn/snews/0337.htm
- http://m.wap.bwbkj.cn/snews/901613.htm
- http://m.wap.bwbkj.cn/snews/5225590.htm
- http://m.wap.bwbkj.cn/snews/23384.htm
- http://m.wap.bwbkj.cn/snews/95967.htm
- http://m.wap.bwbkj.cn/snews/8550454.htm
- http://m.wap.bwbkj.cn/snews/5549.htm
- http://m.wap.bwbkj.cn/snews/961537.htm
- http://m.wap.bwbkj.cn/snews/23198.htm
- http://m.wap.bwbkj.cn/snews/76158.htm
- http://m.wap.bwbkj.cn/snews/5420415.htm
- http://m.wap.bwbkj.cn/snews/1538.htm
- http://m.wap.bwbkj.cn/snews/9067056.htm
- http://m.wap.bwbkj.cn/snews/20415.htm
- http://m.wap.bwbkj.cn/snews/27454.htm
- http://m.wap.bwbkj.cn/snews/36336.htm
- http://m.wap.bwbkj.cn/snews/534184.htm
- http://m.wap.bwbkj.cn/snews/852005.htm
- http://m.wap.bwbkj.cn/snews/1954.htm
- http://m.wap.bwbkj.cn/snews/5595.htm
- http://m.wap.bwbkj.cn/snews/574852.htm
- http://m.wap.bwbkj.cn/snews/757239.htm
- http://m.wap.bwbkj.cn/snews/4088715.htm
- http://m.wap.bwbkj.cn/snews/8258227.htm
- http://m.wap.bwbkj.cn/snews/98547.htm
- http://m.wap.bwbkj.cn/snews/23871.htm
- http://m.wap.bwbkj.cn/snews/2712405.htm
- http://m.wap.bwbkj.cn/snews/615301.htm
- http://m.wap.bwbkj.cn/snews/9342150.htm
- http://m.wap.bwbkj.cn/snews/0088223.htm
- http://m.wap.bwbkj.cn/snews/77545.htm
- http://m.wap.bwbkj.cn/snews/9135.htm
- http://m.wap.bwbkj.cn/snews/76863.htm
- http://m.wap.bwbkj.cn/snews/968785.htm
- http://m.wap.bwbkj.cn/snews/2603.htm
- http://m.wap.bwbkj.cn/snews/49526.htm
- http://m.wap.bwbkj.cn/snews/7834729.htm
- http://m.wap.bwbkj.cn/snews/98455.htm
- http://m.wap.bwbkj.cn/snews/188850.htm
- http://m.wap.bwbkj.cn/snews/49836.htm
- http://m.wap.bwbkj.cn/snews/48785.htm
- http://m.wap.bwbkj.cn/snews/7018302.htm
- http://m.wap.bwbkj.cn/snews/34445.htm
- http://m.wap.bwbkj.cn/snews/28331.htm
- http://m.wap.bwbkj.cn/snews/105927.htm
- http://m.wap.bwbkj.cn/snews/856147.htm
- http://m.wap.bwbkj.cn/snews/6625.htm
- http://m.wap.bwbkj.cn/snews/22927.htm
- http://m.wap.bwbkj.cn/snews/51491.htm
- http://m.wap.bwbkj.cn/snews/629531.htm
- http://m.wap.bwbkj.cn/snews/5404.htm
- http://m.wap.bwbkj.cn/snews/99041.htm
- http://m.wap.bwbkj.cn/snews/890994.htm
- http://m.wap.bwbkj.cn/snews/26088.htm
- http://m.wap.bwbkj.cn/snews/0555753.htm
- http://m.wap.bwbkj.cn/snews/823989.htm
- http://m.wap.bwbkj.cn/snews/4297.htm
- http://m.wap.bwbkj.cn/snews/67249.htm
- http://m.wap.bwbkj.cn/snews/0229627.htm
- http://m.wap.bwbkj.cn/snews/53260.htm
- http://m.wap.bwbkj.cn/snews/02090.htm
- http://m.wap.bwbkj.cn/snews/6349863.htm
- http://m.wap.bwbkj.cn/snews/81992.htm
- http://m.wap.bwbkj.cn/snews/788372.htm
- http://m.wap.bwbkj.cn/snews/15576.htm
- http://m.wap.bwbkj.cn/snews/5138.htm
- http://m.wap.bwbkj.cn/snews/6664573.htm
- http://m.wap.bwbkj.cn/snews/498644.htm
- http://m.wap.bwbkj.cn/snews/808004.htm
- http://m.wap.bwbkj.cn/snews/1342935.htm
- http://m.wap.bwbkj.cn/snews/5673035.htm
- http://m.wap.bwbkj.cn/snews/2703.htm
- http://m.wap.bwbkj.cn/snews/307672.htm
- http://m.wap.bwbkj.cn/snews/9805.htm
- http://m.wap.bwbkj.cn/snews/4988.htm
- http://m.wap.bwbkj.cn/snews/6188114.htm
- http://m.wap.bwbkj.cn/snews/0843872.htm
- http://m.wap.bwbkj.cn/snews/3761.htm
- http://m.wap.bwbkj.cn/snews/15023.htm
- http://m.wap.bwbkj.cn/snews/4055.htm

## 项目结构

```
weblink-navigator/
├── weblink.py               # 主入口脚本，整合导入、检测、生成全流程
├── config.yaml              # 用户配置文件，定义超时、标签别名、忽略域名列表
├── requirements.txt         # Python 依赖清单，固定版本号以保证可复现性
├── batch_236.txt            # 本批次原始链接输入文件（每行一个 URL）
├── core/                    # 核心逻辑模块
│   ├── loader.py            # 从文件或标准输入读取 URL 列表，去重并校验格式
│   ├── checker.py           # 并发执行 HTTP 探测，返回状态码、耗时、标题
│   └── snapshot.py          # 使用 requests + BeautifulSoup 提取正文并存储为 .md
├── output/                  # 生成结果输出目录
│   ├── index.md             # 主索引文件，按域名分组排列所有链接及状态
│   ├── index.html           # 由 index.md 转换而来的静态 HTML 页面
│   ├── snapshots/           # 快照存储子目录，以 URL 的 hash 值命名 .md 文件
│   └── reports/             # 每日检测报告存档，按日期命名如 2026-08-25.json
├── templates/               # 用于自定义 HTML 输出的 Jinja2 模板
│   ├── base.html            # 基础布局模板
│   └── report.html          # 状态报告专用模板
├── scripts/                 # 辅助运维脚本
│   ├── daily_check.sh       # 供 crontab 调用的每日检测包装脚本
│   └── export_static.sh     # 调用 markdown 库批量转换所有 .md 为 .html
├── tests/                   # 单元测试目录，覆盖 loader、checker、snapshot 核心函数
│   ├── test_loader.py
│   ├── test_checker.py
│   └── test_snapshot.py
└── docs/                    # 用户文档目录（详见文档导航章节）
    ├── user_guide.md
    ├── dev_guide.md
    ├── config_reference.md
    ├── deployment.md
    └── troubleshooting.md
```

## 贡献指南

1. 在 GitHub Issues 中查找标记为 `help wanted` 或 `good first issue` 的任务，或提交新的 Bug 报告与功能建议，描述清晰重现步骤或使用场景。

2. Fork 本仓库并创建本地分支，分支命名规范为 `feature/功能简述` 或 `fix/问题简述`，确保代码风格与现有模块保持一致（使用 PEP8 规范，单行不超过 120 字符）。

3. 为新增或修改的功能编写对应的单元测试，测试用例放置于 `tests/` 目录下，命名格式为 `test_模块名.py`，保证 `pytest` 执行全部用例无报错。

4. 提交 Pull Request 时，请参照 `docs/dev_guide.md` 中的提交说明模板，列出变更点、影响范围以及手动测试结果（包括运行 `--check` 检测本批次至少 20 条链接的截图）。

5. 项目维护者会在 3 个工作日内进行 Code Review，如果涉及新增依赖或修改配置结构，请提前在 Issue 中讨论，避免合并冲突。

## 常见问题

**Q: 为什么某些链接始终显示为“失效”，但浏览器可以正常打开？**

A: 这可能是因为目标站点启用了反爬机制（如 Cloudflare 的 5 秒盾）或对 `User-Agent` 做了严格校验。我们默认使用 `Mozilla/5.0 (compatible; WeblinkNavigator/1.0)` 头，若仍被拦截，请检查目标站点是否要求特定的 Referer 或 Cookie。建议在 `config.yaml` 中为该域名单独配置 `headers` 字段，或将该域名加入 `ignore_domains` 列表以免误报。

**Q: 快照保存的 Markdown 文件内容杂乱，无法阅读怎么办？**

A: 快照功能主要面向“内容留底”而非“精美排版”。我们默认提取 `body` 内的可见文本，并移除 `<script>`、`<style>` 和注释。若目标页面严重依赖 JavaScript 渲染（如 SPA 应用），建议改用 Puppeteer 或 Playwright 等无头浏览器方案，本项目提供了 `snapshot_engine: "playwright"` 的实验性配置项（需自行安装 playwright）。

**Q: 如何迁移已有的链接数据到新版本？**

A: 项目使用 `output/index.md` 作为主数据源，其格式为标准的 Markdown 列表。您可以直接复制旧版本的 `index.md` 中的链接部分，粘贴到新版本的输入文件（如 `batch_236.txt`）中，然后重新运行导入流程。注意关闭 `--check` 参数以跳过实时检测，仅做元信息重新提取。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:39:08
