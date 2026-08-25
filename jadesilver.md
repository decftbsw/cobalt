# WebLink Navigator

WebLink Navigator 是一个轻量级的技术资源与外链导航系统，专为需要批量管理、分类展示和快速检索大量外部链接的开发者与内容运营团队设计。该项目将分散的 URL 资源结构化，提供统一的访问入口与状态监控能力，适用于个人书签管理、团队知识库外链整合、以及内容型网站的引用资源托管等场景。

本项目定位于技术资源汇聚站，不生产内容，只做链接的可靠载体。通过约定式目录结构与自动化校验脚本，确保每一条外链的可访问性与分类合理性。项目内置链接状态检查、访问计数统计、分类标签过滤等基础功能，并支持通过 JSON 配置文件批量导入或更新链接数据，满足 300 条及以上规模的外链管理需求。

## 功能概览

**批量链接导入** 支持通过 JSON 或 CSV 格式批量导入 URL 列表，自动解析域名与路径参数，生成内部唯一标识符。

**链接状态监控** 定时发起 HTTP HEAD 请求检测链接可用性，标记失效链接并生成报告，支持自定义超时时间与重试策略。

**分类标签体系** 每条链接可关联多个自定义标签，支持按标签组合筛选与聚合统计，便于构建专题导航页。

**访问计数追踪** 记录每次点击事件，统计链接的点击频次与最近访问时间，辅助判断内容热度。

**响应式导航页** 内置移动端优先的卡片布局模板，支持暗色主题切换，适配移动端与桌面端浏览。

**API 查询接口** 提供 RESTful API 供外部系统调用，支持按 ID、标签、域名前缀等条件检索链接数据。

**链接去重校验** 导入时自动检测重复 URL，基于域名与路径的归一化比对，避免冗余存储。

**数据导出备份** 支持将全量链接数据导出为 JSON 或 Markdown 格式，便于迁移或离线归档。

## 应用场景

个人技术博客的外链资源管理。博主在撰写技术文章时需引用大量外部文档、工具站或代码仓库地址，使用 WebLink Navigator 可统一管理这些引用链接，并在文章底部自动生成标准化引用列表，同时监控链接有效性，避免文章中的外链失效。

团队内部知识库的外部参考整合。技术团队在维护项目文档或设计规范时，常常需要引用官方 SDK 文档、第三方服务条款或行业标准链接。通过本项目可建立一个团队共享的外链池，所有成员均可查询、添加或标注链接，减少重复查找时间。

内容聚合站点的链接分类导航。运营一个技术资讯或资源推荐类网站时，需定期整理推荐的外部资源。WebLink Navigator 的分类标签体系可帮助编辑按主题、难度或适用人群组织链接，快速生成专题页面，提升用户浏览体验。

开源项目的依赖文档索引。开源项目通常依赖多个外部库或服务，其文档分散在不同站点。本项目可为开源项目维护一份结构化的外链索引，包含各依赖项的官方文档、社区论坛、问题追踪地址等，方便贡献者与用户快速定位。

## 快速开始

以下命令演示如何在本地环境中克隆代码、安装依赖并启动开发服务器。

```bash
git clone https://github.com/weblink-navigator/weblink-navigator.git
cd weblink-navigator
npm install
npm run dev
```

执行完成后，访问控制台输出的本地地址（默认为 http://localhost:3000）即可进入导航管理界面。生产环境部署请参考 `docs/deployment.md` 文档。

## 安装要求

| 依赖组件 | 必需版本 | 说明 |
|---|---|---|
| Node.js | >= 18.0.0 | 运行时环境，需支持 ES2020 特性 |
| npm | >= 9.0.0 | 包管理工具，用于安装项目依赖 |
| SQLite3 | 系统自带或通过 npm 安装 | 轻量级数据库，用于存储链接元数据与统计信息 |
| Git | >= 2.25.0 | 版本控制工具，用于克隆仓库与提交贡献 |
| 现代浏览器 | Chrome 90+ / Firefox 88+ / Edge 90+ | 管理界面运行环境，需支持 Web Components |
| 网络环境 | 可访问公网 | 用于链接状态检测时发起外网请求 |

## 文档导航

| 层面 | 目录 | 回答的问题 |
|---|---|---|
| 用户指南 | `docs/user-guide/` | 如何添加链接、创建分类、查看统计报表以及个性化配置？ |
| 开发指南 | `docs/developer-guide/` | 项目整体架构如何分层？如何新增数据源适配器或扩展 API 接口？ |
| 部署手册 | `docs/deployment/` | 如何将系统部署到生产服务器？支持哪些部署方式（Docker、PM2、系统服务）？ |
| 设计说明 | `docs/design/` | 数据库表结构设计依据是什么？链接去重与状态检测的算法逻辑是怎样的？ |

## 资源列表

- http://m.wap.ghtkgg.cn/jnews/97037.htm
- http://m.wap.ghtkgg.cn/jnews/6702.htm
- http://m.wap.ghtkgg.cn/jnews/7468.htm
- http://m.wap.ghtkgg.cn/jnews/754667.htm
- http://m.wap.ghtkgg.cn/jnews/1501610.htm
- http://m.wap.ghtkgg.cn/jnews/808946.htm
- http://m.wap.ghtkgg.cn/jnews/3080960.htm
- http://m.wap.ghtkgg.cn/jnews/796574.htm
- http://m.wap.ghtkgg.cn/jnews/3703088.htm
- http://m.wap.ghtkgg.cn/jnews/28936.htm
- http://m.wap.ghtkgg.cn/jnews/862513.htm
- http://m.wap.ghtkgg.cn/jnews/6591437.htm
- http://m.wap.ghtkgg.cn/jnews/3776912.htm
- http://m.wap.ghtkgg.cn/jnews/3800444.htm
- http://m.wap.ghtkgg.cn/jnews/299029.htm
- http://m.wap.ghtkgg.cn/jnews/02630.htm
- http://m.wap.ghtkgg.cn/jnews/16953.htm
- http://m.wap.ghtkgg.cn/jnews/6177935.htm
- http://m.wap.ghtkgg.cn/jnews/0806.htm
- http://m.wap.ghtkgg.cn/jnews/469781.htm
- http://m.wap.ghtkgg.cn/jnews/2166.htm
- http://m.wap.ghtkgg.cn/jnews/7227865.htm
- http://m.wap.ghtkgg.cn/jnews/7954564.htm
- http://m.wap.ghtkgg.cn/jnews/53071.htm
- http://m.wap.ghtkgg.cn/jnews/039951.htm
- http://m.wap.ghtkgg.cn/jnews/711582.htm
- http://m.wap.ghtkgg.cn/jnews/15091.htm
- http://m.wap.ghtkgg.cn/jnews/10003.htm
- http://m.wap.ghtkgg.cn/jnews/3543760.htm
- http://m.wap.ghtkgg.cn/jnews/404519.htm
- http://m.wap.ghtkgg.cn/jnews/0202.htm
- http://m.wap.ghtkgg.cn/jnews/1533.htm
- http://m.wap.ghtkgg.cn/jnews/253370.htm
- http://m.wap.ghtkgg.cn/jnews/9982.htm
- http://m.wap.ghtkgg.cn/jnews/4643293.htm
- http://m.wap.ghtkgg.cn/jnews/5478.htm
- http://m.wap.ghtkgg.cn/jnews/69808.htm
- http://m.wap.ghtkgg.cn/jnews/9974.htm
- http://m.wap.ghtkgg.cn/jnews/400010.htm
- http://m.wap.ghtkgg.cn/jnews/3892421.htm
- http://m.wap.ghtkgg.cn/jnews/72605.htm
- http://m.wap.ghtkgg.cn/jnews/021667.htm
- http://m.wap.ghtkgg.cn/jnews/110256.htm
- http://m.wap.ghtkgg.cn/jnews/053343.htm
- http://m.wap.ghtkgg.cn/jnews/1387.htm
- http://m.wap.ghtkgg.cn/jnews/1782.htm
- http://m.wap.ghtkgg.cn/jnews/387448.htm
- http://m.wap.ghtkgg.cn/jnews/8076661.htm
- http://m.wap.ghtkgg.cn/jnews/98801.htm
- http://m.wap.ghtkgg.cn/jnews/932285.htm
- http://m.wap.ghtkgg.cn/jnews/63683.htm
- http://m.wap.ghtkgg.cn/jnews/23689.htm
- http://m.wap.ghtkgg.cn/jnews/404342.htm
- http://m.wap.ghtkgg.cn/jnews/61640.htm
- http://m.wap.ghtkgg.cn/jnews/8394.htm
- http://m.wap.ghtkgg.cn/jnews/19927.htm
- http://m.wap.ghtkgg.cn/jnews/210522.htm
- http://m.wap.ghtkgg.cn/jnews/842684.htm
- http://m.wap.ghtkgg.cn/jnews/169143.htm
- http://m.wap.ghtkgg.cn/jnews/922808.htm
- http://m.wap.ghtkgg.cn/jnews/707720.htm
- http://m.wap.ghtkgg.cn/jnews/2786516.htm
- http://m.wap.ghtkgg.cn/jnews/75804.htm
- http://m.wap.ghtkgg.cn/jnews/02523.htm
- http://m.wap.ghtkgg.cn/jnews/499546.htm
- http://m.wap.ghtkgg.cn/jnews/3372.htm
- http://m.wap.ghtkgg.cn/jnews/369241.htm
- http://m.wap.ghtkgg.cn/jnews/51699.htm
- http://m.wap.ghtkgg.cn/jnews/950792.htm
- http://m.wap.ghtkgg.cn/jnews/1897.htm
- http://m.wap.ghtkgg.cn/jnews/0368.htm
- http://m.wap.ghtkgg.cn/jnews/141664.htm
- http://m.wap.ghtkgg.cn/jnews/4984145.htm
- http://m.wap.ghtkgg.cn/jnews/4204.htm
- http://m.wap.ghtkgg.cn/jnews/736381.htm
- http://m.wap.ghtkgg.cn/jnews/1923090.htm
- http://m.wap.ghtkgg.cn/jnews/5600209.htm
- http://m.wap.ghtkgg.cn/jnews/113635.htm
- http://m.wap.ghtkgg.cn/jnews/3873710.htm
- http://m.wap.ghtkgg.cn/jnews/3586897.htm
- http://m.wap.ghtkgg.cn/jnews/16474.htm
- http://m.wap.ghtkgg.cn/jnews/1785.htm
- http://m.wap.ghtkgg.cn/jnews/615630.htm
- http://m.wap.ghtkgg.cn/jnews/0922358.htm
- http://m.wap.ghtkgg.cn/jnews/495085.htm
- http://m.wap.ghtkgg.cn/jnews/3508.htm
- http://m.wap.ghtkgg.cn/jnews/0065019.htm
- http://m.wap.ghtkgg.cn/jnews/78555.htm
- http://m.wap.ghtkgg.cn/jnews/31010.htm
- http://m.wap.ghtkgg.cn/jnews/016066.htm
- http://m.wap.ghtkgg.cn/jnews/49193.htm
- http://m.wap.ghtkgg.cn/jnews/8615.htm
- http://m.wap.ghtkgg.cn/jnews/01715.htm
- http://m.wap.ghtkgg.cn/jnews/88405.htm
- http://m.wap.ghtkgg.cn/jnews/1622.htm
- http://m.wap.ghtkgg.cn/jnews/7881027.htm
- http://m.wap.ghtkgg.cn/jnews/742031.htm
- http://m.wap.ghtkgg.cn/jnews/3429193.htm
- http://m.wap.ghtkgg.cn/jnews/52778.htm
- http://m.wap.ghtkgg.cn/jnews/4811683.htm
- http://m.wap.ghtkgg.cn/jnews/79912.htm
- http://m.wap.ghtkgg.cn/jnews/5122145.htm
- http://m.wap.ghtkgg.cn/jnews/719971.htm
- http://m.wap.ghtkgg.cn/jnews/630285.htm
- http://m.wap.ghtkgg.cn/jnews/215104.htm
- http://m.wap.ghtkgg.cn/jnews/4445.htm
- http://m.wap.ghtkgg.cn/jnews/27147.htm
- http://m.wap.ghtkgg.cn/jnews/84405.htm
- http://m.wap.ghtkgg.cn/jnews/4467391.htm
- http://m.wap.ghtkgg.cn/jnews/4064.htm
- http://m.wap.ghtkgg.cn/jnews/6342822.htm
- http://m.wap.ghtkgg.cn/jnews/282652.htm
- http://m.wap.ghtkgg.cn/jnews/24949.htm
- http://m.wap.ghtkgg.cn/jnews/1661100.htm
- http://m.wap.ghtkgg.cn/jnews/5916.htm
- http://m.wap.ghtkgg.cn/jnews/67671.htm
- http://m.wap.ghtkgg.cn/jnews/75324.htm
- http://m.wap.ghtkgg.cn/jnews/67600.htm
- http://m.wap.ghtkgg.cn/jnews/0707.htm
- http://m.wap.ghtkgg.cn/jnews/373273.htm
- http://m.wap.ghtkgg.cn/jnews/701629.htm
- http://m.wap.ghtkgg.cn/jnews/67868.htm
- http://m.wap.ghtkgg.cn/jnews/0041.htm
- http://m.wap.ghtkgg.cn/jnews/0267.htm
- http://m.wap.ghtkgg.cn/jnews/4520.htm
- http://m.wap.ghtkgg.cn/jnews/257112.htm
- http://m.wap.ghtkgg.cn/jnews/3436.htm
- http://m.wap.ghtkgg.cn/jnews/2572237.htm
- http://m.wap.ghtkgg.cn/jnews/64204.htm
- http://m.wap.ghtkgg.cn/jnews/24121.htm
- http://m.wap.ghtkgg.cn/jnews/3815132.htm
- http://m.wap.ghtkgg.cn/jnews/4049.htm
- http://m.wap.ghtkgg.cn/jnews/4420.htm
- http://m.wap.ghtkgg.cn/jnews/47104.htm
- http://m.wap.ghtkgg.cn/jnews/9129.htm
- http://m.wap.ghtkgg.cn/jnews/6805.htm
- http://m.wap.ghtkgg.cn/jnews/827913.htm
- http://m.wap.ghtkgg.cn/jnews/9187.htm
- http://m.wap.ghtkgg.cn/jnews/332685.htm
- http://m.wap.ghtkgg.cn/jnews/181205.htm
- http://m.wap.ghtkgg.cn/jnews/3118260.htm
- http://m.wap.ghtkgg.cn/jnews/6826586.htm
- http://m.wap.ghtkgg.cn/jnews/601345.htm
- http://m.wap.ghtkgg.cn/jnews/5013089.htm
- http://m.wap.ghtkgg.cn/jnews/904342.htm
- http://m.wap.ghtkgg.cn/jnews/21001.htm
- http://m.wap.ghtkgg.cn/jnews/271903.htm
- http://m.wap.ghtkgg.cn/jnews/48476.htm
- http://m.wap.ghtkgg.cn/jnews/22852.htm
- http://m.wap.ghtkgg.cn/jnews/44344.htm
- http://m.wap.ghtkgg.cn/jnews/177556.htm
- http://m.wap.ghtkgg.cn/jnews/19094.htm
- http://m.wap.ghtkgg.cn/jnews/332294.htm
- http://m.wap.ghtkgg.cn/jnews/133480.htm
- http://m.wap.ghtkgg.cn/jnews/077908.htm
- http://m.wap.ghtkgg.cn/jnews/5948730.htm
- http://m.wap.ghtkgg.cn/jnews/4165877.htm
- http://m.wap.ghtkgg.cn/jnews/00442.htm
- http://m.wap.ghtkgg.cn/jnews/1419.htm
- http://m.wap.ghtkgg.cn/jnews/616954.htm
- http://m.wap.ghtkgg.cn/jnews/71910.htm
- http://m.wap.ghtkgg.cn/jnews/97311.htm
- http://m.wap.ghtkgg.cn/jnews/887258.htm
- http://m.wap.ghtkgg.cn/jnews/4174.htm
- http://m.wap.ghtkgg.cn/jnews/271592.htm
- http://m.wap.ghtkgg.cn/jnews/43698.htm
- http://m.wap.ghtkgg.cn/jnews/368329.htm
- http://m.wap.ghtkgg.cn/jnews/347151.htm
- http://m.wap.ghtkgg.cn/jnews/7283.htm
- http://m.wap.ghtkgg.cn/jnews/4656.htm
- http://m.wap.ghtkgg.cn/jnews/32281.htm
- http://m.wap.ghtkgg.cn/jnews/0823065.htm
- http://m.wap.ghtkgg.cn/jnews/8380.htm
- http://m.wap.ghtkgg.cn/jnews/7990112.htm
- http://m.wap.ghtkgg.cn/jnews/511959.htm
- http://m.wap.ghtkgg.cn/jnews/6022416.htm
- http://m.wap.ghtkgg.cn/jnews/1709352.htm
- http://m.wap.ghtkgg.cn/jnews/447326.htm
- http://m.wap.ghtkgg.cn/jnews/11987.htm
- http://m.wap.ghtkgg.cn/jnews/4144002.htm
- http://m.wap.ghtkgg.cn/jnews/35207.htm
- http://m.wap.ghtkgg.cn/jnews/132153.htm
- http://m.wap.ghtkgg.cn/jnews/09566.htm
- http://m.wap.ghtkgg.cn/jnews/619043.htm
- http://m.wap.ghtkgg.cn/jnews/93142.htm
- http://m.wap.ghtkgg.cn/jnews/2860051.htm
- http://m.wap.ghtkgg.cn/jnews/72268.htm
- http://m.wap.ghtkgg.cn/jnews/89686.htm
- http://m.wap.ghtkgg.cn/jnews/5618.htm
- http://m.wap.ghtkgg.cn/jnews/86397.htm
- http://m.wap.ghtkgg.cn/jnews/00768.htm
- http://m.wap.ghtkgg.cn/jnews/04155.htm
- http://m.wap.ghtkgg.cn/jnews/13463.htm
- http://m.wap.ghtkgg.cn/jnews/28553.htm
- http://m.wap.ghtkgg.cn/jnews/5235.htm
- http://m.wap.ghtkgg.cn/jnews/3428818.htm
- http://m.wap.ghtkgg.cn/jnews/81821.htm
- http://m.wap.ghtkgg.cn/jnews/45579.htm
- http://m.wap.ghtkgg.cn/jnews/10366.htm
- http://m.wap.ghtkgg.cn/jnews/76839.htm
- http://m.wap.ghtkgg.cn/jnews/2801172.htm
- http://m.wap.ghtkgg.cn/jnews/5047.htm
- http://m.wap.ghtkgg.cn/jnews/515499.htm
- http://m.wap.ghtkgg.cn/jnews/47233.htm
- http://m.wap.ghtkgg.cn/jnews/7864.htm
- http://m.wap.ghtkgg.cn/jnews/4878528.htm
- http://m.wap.ghtkgg.cn/jnews/8502689.htm
- http://m.wap.ghtkgg.cn/jnews/007223.htm
- http://m.wap.ghtkgg.cn/jnews/198631.htm
- http://m.wap.ghtkgg.cn/jnews/259383.htm
- http://m.wap.ghtkgg.cn/jnews/73023.htm
- http://m.wap.ghtkgg.cn/jnews/6729302.htm
- http://m.wap.ghtkgg.cn/jnews/0404224.htm
- http://m.wap.ghtkgg.cn/jnews/88455.htm
- http://m.wap.ghtkgg.cn/jnews/9164.htm
- http://m.wap.ghtkgg.cn/jnews/593630.htm
- http://m.wap.ghtkgg.cn/jnews/169907.htm
- http://m.wap.ghtkgg.cn/jnews/86787.htm
- http://m.wap.ghtkgg.cn/jnews/989875.htm
- http://m.wap.ghtkgg.cn/jnews/2051.htm
- http://m.wap.ghtkgg.cn/jnews/6257.htm
- http://m.wap.ghtkgg.cn/jnews/2759.htm
- http://m.wap.ghtkgg.cn/jnews/997849.htm
- http://m.wap.ghtkgg.cn/jnews/42137.htm
- http://m.wap.ghtkgg.cn/jnews/8434.htm
- http://m.wap.ghtkgg.cn/jnews/097319.htm
- http://m.wap.ghtkgg.cn/jnews/77629.htm
- http://m.wap.ghtkgg.cn/jnews/58650.htm
- http://m.wap.ghtkgg.cn/jnews/3432.htm
- http://m.wap.ghtkgg.cn/jnews/3488034.htm
- http://m.wap.ghtkgg.cn/jnews/4460837.htm
- http://m.wap.ghtkgg.cn/jnews/6214.htm
- http://m.wap.ghtkgg.cn/jnews/593562.htm
- http://m.wap.ghtkgg.cn/jnews/3129.htm
- http://m.wap.ghtkgg.cn/jnews/7229.htm
- http://m.wap.ghtkgg.cn/jnews/5101.htm
- http://m.wap.ghtkgg.cn/jnews/860338.htm
- http://m.wap.ghtkgg.cn/jnews/732826.htm
- http://m.wap.ghtkgg.cn/jnews/685804.htm
- http://m.wap.ghtkgg.cn/jnews/67098.htm
- http://m.wap.ghtkgg.cn/jnews/2565107.htm
- http://m.wap.ghtkgg.cn/jnews/199498.htm
- http://m.wap.ghtkgg.cn/jnews/8348.htm
- http://m.wap.ghtkgg.cn/jnews/4269547.htm
- http://m.wap.ghtkgg.cn/jnews/7111545.htm
- http://m.wap.ghtkgg.cn/jnews/8343.htm
- http://m.wap.ghtkgg.cn/jnews/0304.htm
- http://m.wap.ghtkgg.cn/jnews/5844979.htm
- http://m.wap.ghtkgg.cn/jnews/398413.htm
- http://m.wap.ghtkgg.cn/jnews/1717858.htm
- http://m.wap.ghtkgg.cn/jnews/75743.htm
- http://m.wap.ghtkgg.cn/jnews/431962.htm
- http://m.wap.ghtkgg.cn/jnews/7125627.htm
- http://m.wap.ghtkgg.cn/jnews/0578.htm
- http://m.wap.ghtkgg.cn/jnews/822475.htm
- http://m.wap.ghtkgg.cn/jnews/1210710.htm
- http://m.wap.ghtkgg.cn/jnews/18212.htm
- http://m.wap.ghtkgg.cn/jnews/45703.htm
- http://m.wap.ghtkgg.cn/jnews/5360.htm
- http://m.wap.ghtkgg.cn/jnews/210064.htm
- http://m.wap.ghtkgg.cn/jnews/857512.htm
- http://m.wap.ghtkgg.cn/jnews/3367592.htm
- http://m.wap.ghtkgg.cn/jnews/366752.htm
- http://m.wap.ghtkgg.cn/jnews/3783484.htm
- http://m.wap.ghtkgg.cn/jnews/331694.htm
- http://m.wap.ghtkgg.cn/jnews/9207761.htm
- http://m.wap.ghtkgg.cn/jnews/5461936.htm
- http://m.wap.ghtkgg.cn/jnews/21520.htm
- http://m.wap.ghtkgg.cn/jnews/38289.htm
- http://m.wap.ghtkgg.cn/jnews/414591.htm
- http://m.wap.ghtkgg.cn/jnews/94842.htm
- http://m.wap.ghtkgg.cn/jnews/1642657.htm
- http://m.wap.ghtkgg.cn/jnews/65450.htm
- http://m.wap.ghtkgg.cn/jnews/680211.htm
- http://m.wap.ghtkgg.cn/jnews/71568.htm
- http://m.wap.ghtkgg.cn/jnews/67814.htm
- http://m.wap.ghtkgg.cn/jnews/6216.htm
- http://m.wap.ghtkgg.cn/jnews/6443885.htm
- http://m.wap.ghtkgg.cn/jnews/72243.htm
- http://m.wap.ghtkgg.cn/jnews/020507.htm
- http://m.wap.ghtkgg.cn/jnews/7641370.htm
- http://m.wap.ghtkgg.cn/jnews/1616926.htm
- http://m.wap.ghtkgg.cn/jnews/2677293.htm
- http://m.wap.ghtkgg.cn/jnews/2884.htm
- http://m.wap.ghtkgg.cn/jnews/367155.htm
- http://m.wap.ghtkgg.cn/jnews/19898.htm
- http://m.wap.ghtkgg.cn/jnews/5117507.htm
- http://m.wap.ghtkgg.cn/jnews/85294.htm
- http://m.wap.ghtkgg.cn/jnews/2010.htm
- http://m.wap.ghtkgg.cn/jnews/5195.htm
- http://m.wap.ghtkgg.cn/jnews/70773.htm
- http://m.wap.ghtkgg.cn/jnews/8470326.htm
- http://m.wap.ghtkgg.cn/jnews/4559327.htm
- http://m.wap.ghtkgg.cn/jnews/1790.htm
- http://m.wap.ghtkgg.cn/jnews/2926653.htm
- http://m.wap.ghtkgg.cn/jnews/8122498.htm
- http://m.wap.ghtkgg.cn/jnews/54941.htm
- http://m.wap.ghtkgg.cn/jnews/81599.htm
- http://m.wap.ghtkgg.cn/jnews/3966.htm
- http://m.wap.ghtkgg.cn/jnews/570113.htm

## 项目结构

```
weblink-navigator/
├── src/                           # 核心源代码目录
│   ├── api/                       # RESTful API 路由与控制器
│   │   ├── v1/                    # API 版本 1 的实现
│   │   │   ├── links.js           # 链接资源的 CRUD 操作
│   │   │   └── tags.js            # 标签资源的查询与管理
│   │   └── middleware/            # 请求中间件（鉴权、日志、限流）
│   ├── core/                      # 核心业务逻辑层
│   │   ├── link-manager.js        # 链接增删改查、去重与状态更新
│   │   ├── health-checker.js      # 链接可用性检测与超时重试策略
│   │   └── stats-collector.js     # 点击统计与访问趋势聚合
│   ├── db/                        # 数据持久化层
│   │   ├── migrations/            # 数据库迁移脚本（SQLite 表结构变更）
│   │   ├── models/                # 数据模型定义（Link, Tag, ClickLog）
│   │   └── client.js              # 数据库连接池与查询构建器
│   ├── ui/                        # 前端界面资源
│   │   ├── pages/                 # 导航页、管理仪表盘、分类浏览页
│   │   ├── components/            # 可复用 UI 组件（卡片、筛选栏、图表）
│   │   └── static/                # CSS 样式、JavaScript 脚本与图片资源
│   └── utils/                     # 通用工具函数
│       ├── validator.js           # URL 格式校验与归一化
│       ├── parser.js              # 导入文件解析（JSON/CSV）
│       └── logger.js              # 日志记录器（支持文件与控制台输出）
├── tests/                         # 单元测试与集成测试
│   ├── unit/                      # 各模块的单元测试用例
│   └── integration/               # API 接口与数据库交互测试
├── docs/                          # 项目文档（用户指南、开发文档、部署说明）
├── scripts/                       # 运维与辅助脚本
│   ├── import-links.js            # 批量导入链接数据脚本
│   ├── export-links.js            # 导出链接数据脚本
│   └── health-scan.js             # 手动触发全量链接状态扫描
├── config/                        # 配置文件目录
│   ├── default.json               # 默认配置（端口、超时、分页大小）
│   └── production.json            # 生产环境覆盖配置
├── .env.example                   # 环境变量模板（数据库路径、密钥等）
├── package.json                   # npm 项目清单与依赖声明
├── package-lock.json              # 依赖锁定文件
├── README.md                      # 项目说明文档（本文件）
└── LICENSE                        # MIT 许可证文本
```

## 贡献指南

提交问题报告与功能请求。访问 GitHub Issues 页面，使用提供的模板描述您遇到的问题或期望的新特性。请附上复现步骤、系统环境信息以及相关的日志片段，以便维护人员快速定位。

创建分支并进行本地开发。从 main 分支签出新的 feature 或 fix 分支，遵循命名规范如 `feature/批量导入优化` 或 `fix/链接检测超时`。提交代码时请编写清晰的提交信息，遵守 Conventional Commits 规范。

编写或更新测试用例。所有新增功能或缺陷修复均需包含对应的单元测试或集成测试，确保测试覆盖率达到 80% 以上。运行 `npm test` 验证所有测试通过后方可提交。

提交 Pull Request 并参与评审。将分支推送到远程仓库后，创建 Pull Request 至 main 分支，详细描述变更内容、测试结果以及可能的影响范围。至少需要一位项目维护者批准后方可合并。

完善文档与示例。若变更涉及用户可见的功能或配置项，请同步更新 `docs/` 目录下的对应文档，并在必要处补充代码示例或配置片段。

## 常见问题

**问：链接状态检测出现大量超时或失败，应如何调整？**

答：链接检测依赖公网网络环境，部分站点可能屏蔽 HEAD 请求或响应较慢。您可以在 `config/default.json` 中调整 `healthCheck.timeout` 参数（单位毫秒）增加超时阈值，同时通过 `healthCheck.retries` 设置重试次数。对于频繁超时的域名，可将其加入 `healthCheck.ignoreDomains` 列表跳过检测。

**问：导入大量链接时页面卡顿或内存占用过高，如何优化？**

答：批量导入操作建议使用命令行脚本 `scripts/import-links.js` 而非通过管理界面上传。该脚本采用流式读取与批量写入，可处理数千条链接而不会耗尽内存。同时，请确保 SQLite 数据库已启用 WAL 模式以提升并发写入性能。

**问：如何将现有书签或收藏夹数据迁移到 WebLink Navigator？**

答：主流浏览器支持将书签导出为 HTML 文件。您可以使用项目提供的转换工具 `scripts/convert-bookmarks.js` 将 HTML 书签文件转换为项目可识别的 JSON 格式，然后通过导入接口或脚本批量写入数据库。具体步骤请参考 `docs/user-guide/migration.md`。

## 许可证

MIT

> 外链数量: 300 | 生成时间: 2026-08-25 19:38:06
