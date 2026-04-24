# Hermes Agent + ClawEmail 工作流：用顶级 AI Newsletter 构建第二大脑

> 来源：https://x.com/lxfater/status/2047150392274993624
> 整理时间：2026-04-24
> 来自翡冷翠

---

## 简介

这是一套完整的 AI 信息处理工作流，通过 **Hermes Agent** + **ClawEmail** 邮箱服务，将分散的 AI Newsletter 信息源整合为个人知识库，实现从信息输入到知识输出的完整闭环。

文章作者铁锤人（@lxfater）使用这套方法后，文章输出质量显著提升，连续产出 18w、17w、86w 浏览量的文章。

---

## 内容清单总览

| 章节 | 主题 | 核心内容 |
|------|------|----------|
| 1 | 信息源筛选 | 10 个顶级 AI Newsletter 推荐 |
| 2 | 邮箱配置 | ClawEmail 注册与 mail-cli 安装 |
| 3 | 子邮箱管理 | 创建隔离的 Newsletter 专用邮箱 |
| 4 | 日报生成 | 自动摘要与推荐 |
| 5 | LLM Wiki | 知识编译与第二大脑构建 |
| 6 | 输出实操 | 从 Wiki 到 X 文章/信息图 |

---

## 详细内容

### 第一章：换掉信息源 — 顶级 AI Newsletter 清单

作者从 50+ 个信息源中筛选出的 10 个高质量 AI Newsletter：

| Newsletter | 类型 | 核心亮点 |
|------------|------|----------|
| **The Rundown AI** | 产业动态 | 每日 AI 产业动态，通俗易懂、密度高 |
| **TLDR AI** | 科技简报 | 5 分钟科技简报，AI + 编程 + 产品精华浓缩 |
| **The Neuron** | 非技术日报 | 面向非技术读者的 AI 日报，3 分钟读完 |
| **Ben's Bites** | 工具资讯 | Ben Tossell 的 AI 日报，工具圈消息源 |
| **Latent Space** | 开发者简报 | swyx 开发者简报，未公开项目 + 工程视角 |
| **Smol AI News** | 社区直击 | Discord、Reddit 等 AI 社区圈内直击 |
| **Interconnects** | 深度专栏 | Nathan Lambert 的 RLHF、模型训练深度专栏 |
| **One Useful Thing** | 实用洞察 | Ethan Mollick 的 AI 实用洞察（学术 + 工作场景） |
| **AI Breakfast** | 系统回顾 | 每周一份 AI 新闻早餐，系统回顾 + 深度讨论 |
| **Every** | 战略分析 | 科技与商业的下一步，资深专家战略分析 |

**关键洞察**：AI 变化快的赛道，真正有信号的源头在海外 newsletter。公众号经过多层洗稿过滤，看到时已是二手信息。

---

### 第二章：构建 Newsletter 到 Agent 的管道

#### 2.1 注册 ClawEmail 邮箱

ClawEmail 是网易推出的 **Agent 专属邮箱产品**。

**注册步骤**：
1. 访问 https://claw.163.com 报名内测
2. 使用邀请码（可选）：`CLAW3C02D3891B6C`（上限 200 次）
3. 创建主邮箱，如 `yourname@claw.163.com`

#### 2.2 安装 mail-cli 工具

```bash
# 1. 全局安装 mail-cli
npm install -g @clawemail/mail-cli

# 2. 设置 API Key（从 Dashboard 获取）
mail-cli auth apikey set ck_live_xxxxxxxxxxxxxxxx

# 3. 登录主邮箱
mail-cli auth login --user yourname@claw.163.com

# 4. 测试连接
mail-cli auth test
```

#### 2.3 让 Hermes 学会使用 mail-cli

在 Hermes 中输入提示词：

```
阅读 https://claw.163.com/projects/doc/ 这个 CLI 文档，然后制作一个 Skill 来专门操纵这 CLI。
```

利用 Hermes 自学习能力，Agent 很快就能掌握 mail-cli 的使用。

---

### 第三章：创建 Newsletter 专用子邮箱

为了隔离不同类型的邮件（newsletter vs 客服邮件），建议创建专用子邮箱。

#### 3.1 创建子邮箱

```bash
mail-cli clawemail create \
  --prefix newsletter \
  --type sub \
  --display-name "Newsletter Bot"
```

#### 3.2 配置通讯规则

1. Dashboard → Agent 邮箱管理 → 选中子邮箱 → 通讯规则
2. 选择 **开放外部通信**
3. 收信范围选 **所有人**（newsletter 发件域太杂，白名单维护成本高）

---

### 第四章：用 Agent 订阅 Newsletter

订阅流程简化：

1. 在 newsletter 订阅框填入 `newsletter@yourname.claw.163.com`
2. 确认邮件到达后，让 Hermes 提取确认地址
3. 将地址输入浏览器完成确认
4. 如需回复邮件进行人机检查，让 Hermes 帮忙回复

完成这步后，newsletter 将进入 Agent 专属邮箱，Agent 随时能读取。

---

### 第五章：日报生成 — 自动筛选与消化

#### 5.1 安装日报 Skill

ClawEmail 官方提供自动日报功能，每天早上一封摘要邮件。

```bash
npx skills add https://claw.163.com/gitea-web/s/daily-report.git
```

**关键用法**：Digest 不只是为了省时间，更重要的是**挑出今天最值得深读的那一篇文章**。

---

### 第六章：核心 — LLM Wiki 知识编译

#### 6.1 什么是 LLM Wiki？

这是 Karpathy 2026 年提出的概念。他说 RAG 检索太窄，LLM 真正该干的是**知识编译器**。

**运作原理**：
- 每天扔一篇文章给 Agent
- Agent 把概念、实体、主张、开放问题拆出来
- 每个知识点做成索引卡片
- 用链接把新卡片与已有卡片连接起来
- 久之形成一张活的知识图

#### 6.2 具体操作

在 Hermes 中：

```
给出邮箱里面你感兴趣的文章，告诉它：这篇编译到我的 Wiki
```

跑完后会获得一个互相链接的 Markdown 文件，构成知识网络。

#### 6.3 可视化知识图谱

用 Obsidian 打开知识图谱功能，可以看到概念间的链接关系：

- 找到不懂的概念，不断问 Hermes 拆解
- 知识图上形成互相勾连的概念
- 旧概念因为新文章又加了新论据
- 新旧概念第一次被连到一起

**效果**：读 1 篇等于刷新了 10 篇！知识图一天厚一点，学进去就不易遗忘。

---

### 第七章：输出实操 — 从 Wiki 到文章

#### 7.1 信息图生成

Hermes Agent 内置信息图命令行（基于宝玉的信息图 prompt）。

操作方式：
- 把 Wiki index 地址给 AI
- 问一个概念：如 "Verification Loop 是什么？"
- AI 扫描相关知识，直接生成信息图

#### 7.2 文章撰写辅助

大多数人以为 AI 写文章就是 AI 帮你写，但真正让你写出好文章的是**你自己把事情想明白**。AI 只做脑爆，提高多做多可能性。

写的时候对着 Hermes 问：
1. 这个概念我上周读过哪几篇支持？
2. 那个观点我怎么反驳？
3. 还有哪些角度我没考虑到？

让 Hermes 利用 LLM Wiki 功能给你灵感和解决盲点。

#### 7.3 自动排版与发布

参考 Skill：**自动排版并发送到公众号草稿**（开源 Skill）

相关文章：https://x.com/lxfater/status/2047038752204521659

---

## 资源汇总

### 相关链接

| 名称 | 链接 | 说明 |
|------|------|------|
| ClawEmail 官网 | https://claw.163.com | Agent 专属邮箱服务 |
| 原文 X 文章 | https://x.com/lxfater/status/2047150392274993624 | 铁锤人的完整教程 |
| 相关教程 | https://x.com/lxfater/status/2047038752204521659 | 自动排版与发布教程 |

### 命令速查表

```bash
# 安装 mail-cli
npm install -g @clawemail/mail-cli

# 设置 API Key
mail-cli auth apikey set ck_live_xxxxx

# 登录
mail-cli auth login --user yourname@claw.163.com

# 测试连接
mail-cli auth test

# 创建子邮箱
mail-cli clawemail create \
  --prefix newsletter \
  --type sub \
  --display-name "Newsletter Bot"

# 安装日报 Skill
npx skills add https://claw.163.com/gitea-web/s/daily-report.git
```

### 10 个 AI Newsletter 订阅地址

- The Rundown AI: https://www.therundown.ai/
- TLDR AI: https://tldr.tech/ai
- The Neuron: https://www.theneuron.ai/
- Ben's Bites: https://www.bensbites.co/
- Latent Space: https://www.latent.space/
- Smol AI News: https://smol.ai/news
- Interconnects: https://www.interconnects.ai/
- One Useful Thing: https://www.oneusefulthing.org/
- AI Breakfast: https://aibreakfast.beehiiv.com/
- Every: https://every.to/

---

## 建议学习/使用路径

1. **第一周**：注册 ClawEmail，配置 mail-cli，订阅 3-5 个 newsletter
2. **第二周**：创建子邮箱，安装日报 Skill，让 Agent 开始筛选文章
3. **第三周**：开始构建 LLM Wiki，每天编译 1 篇深读文章
4. **第四周**：利用 Wiki 进行输出，尝试生成信息图或撰写 X 文章

---

## 附录：关键概念解释

| 概念 | 解释 |
|------|------|
| **ClawEmail** | 网易推出的 Agent 专用邮箱服务，支持 API 操作 |
| **mail-cli** | ClawEmail 的命令行工具，让 Agent 能读/写邮件 |
| **LLM Wiki** | Karpathy 提出的知识编译方法，将文章拆解为互联的知识卡片 |
| **第二大脑** | 个人知识管理系统，通过链接将知识点形成网络 |
| **Newsletter** | 定期发送的电子邮件简报，通常聚焦特定主题 |

---

*来自翡冷翠*
