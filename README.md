# futurelab
<div align="center">

<img src="docs/banner.svg" alt="追番计划" width="100%"/>

**纯信息型动画数据库与追番管理网站** · 界面形态受 [bgm.tv](https://bgm.tv) 启发，独立实现

[![Next.js](https://img.shields.io/badge/Next.js-16-000000?logo=nextdotjs)](https://nextjs.org)
[![TypeScript](https://img.shields.io/badge/TypeScript-5-3178C6?logo=typescript&logoColor=white)](https://www.typescriptlang.org)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind-v4-06B6D4?logo=tailwindcss&logoColor=white)](https://tailwindcss.com)
[![SQLite · node:sqlite](https://img.shields.io/badge/SQLite-node%3Asqlite-003B57?logo=sqlite&logoColor=white)](https://nodejs.org)
[![Node](https://img.shields.io/badge/Node-%E2%89%A522.5-339933?logo=nodedotjs&logoColor=white)](https://nodejs.org)
[![License: MIT](https://img.shields.io/badge/License-MIT-e46a76)](LICENSE)

**运行时零第三方依赖 · 无任何影视资源 · 深色模式 · 移动端适配**

</div>

---

## 📸 预览

| 首页（浅色 · 真实海报） | 条目页（浅色） |
| :---: | :---: |
| ![首页](docs/screenshots/home-light.png) | ![条目页](docs/screenshots/subject-light.png) |
| **公告弹窗（深色）** | **个人设置（浅色）** |
| ![公告弹窗](docs/screenshots/modal-dark.png) | ![个人设置](docs/screenshots/settings-light.png) |

## ✨ 功能

<details open>
<summary><b>📖 条目与浏览</b></summary>

- 40+ 部动画完整资料：信息栏 / 标签 / 简介 / **角色声优 / 制作人员**（可点击进入人物介绍页）/ 集数列表 / 关联条目
- 加权评分 + 全站 Rank + 星级分布图 + 站内评分
- **季度番剧**：一月 / 四月 / 七月 / 十月新番 tab，跟随真实日历轮换，待播番「未放送」徽章与下季预告
- **每周放送日历**：周一至周日分组，今日脉冲高亮
- 条目索引：关键词搜索（中日文/别名）× 类型 / 状态 / 年份 / 标签筛选 × 多维排序 × 分页
- 条目页「猜你喜欢」：按标签重合度智能推荐

</details>

<details open>
<summary><b>🔖 追番管理</b></summary>

- 五状态收藏（想看 / 在看 / 看过 / 搁置 / 抛弃）+ 1-10 评分
- 封面「⋯」快捷收藏菜单，不进条目页直接改状态
- 单集勾选 + 「看到第 N 集」批量标记；看完自动转「看过」
- **观看时间**自动记录（开始于 / 最近观看 / 看完于）
- **每集备注**与**收藏私密备注**（仅自己可见）

</details>

<details open>
<summary><b>💬 社区</b></summary>

- 吐槽箱：短评 + 评分快照，**敏感词过滤**（命中即拦，提示命中词）
- 评论 👍👎 点赞点踩（可取消/切换）
- 举报分类菜单（垃圾广告 / 人身攻击 / 剧透 / …）→ 管理员处理
- 个人主页：五状态收藏 + 观看时间 + **动态流（可设私密）**

</details>

<details open>
<summary><b>🛠 管理后台（`/admin`，仅管理员）</b></summary>

- 数据概览统计卡
- 条目管理：搜索 / 分页 / **新增 / 编辑 / 删除**，集数增删改，自动重算 Rank
- 公告管理：发布 / 编辑 / 置顶 / 删除 → **访客首次访问自动弹窗**
- 评论管理与举报处理 / 用户管理（授权管理员、删除用户）

</details>

## 🚀 快速开始

> 要求 Node.js ≥ 22.5（内置 `node:sqlite`，**运行时零第三方依赖**）

```bash
npm install
npm run seed      # 建库 + 40 部动画种子数据 + 生成 SVG 封面
npm run dev       # http://localhost:3000
```

可选增强（需可达对应站点）：

```bash
npm run covers        # 从 AniList 下载 39 张真实海报
npm run enrich-people # 抓取声优/制作人员真实照片与简介
npm run fetch:bgm     # 从 Bangumi API 拉取条目数据（需可达 bgm.tv）
```

## 🔑 测试账号

| 用户名 | 密码 | 说明 |
| --- | --- | --- |
| **demo** | `demo123` | 管理员 · 已有收藏/评分/进度/备注/吐槽 |
| akira / moe_moe / nightowl | `demo123` | 演示用户 |

## 🗂 项目结构

```
prisma/seed.ts           # 建库 DDL + 种子数据 + SVG 封面生成
prisma/seed-data.ts      # 离线动画数据集
scripts/                 # AniList 海报/人物/Bangumi 数据抓取脚本
src/lib/                 # node:sqlite 数据层 / 会话 / 验证码 / 敏感词
src/actions/             # Server Actions（认证/收藏/进度/评论/公告/管理）
src/app/                 # 首页 / browse / subject / user / rank
                         # person / company / settings / admin / about / privacy
src/components/          # UI 组件（弹窗/菜单/表单/卡片…）
```

## 📄 相关页面

[关于本站](/about) · [隐私政策](/privacy)（密码 scrypt 加盐哈希、备注私密、无第三方追踪） · 联系方式：contact@zhuifan.example

## 📃 License

[MIT](LICENSE) © 2026 Logiczk-cn

---

<div align="center">
<sub>海报与人物照片版权归原出品方所有 · 本站不提供任何在线播放或下载资源</sub>
</div>
