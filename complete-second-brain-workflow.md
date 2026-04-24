# 完整第二大脑工作流：Hermes Agent + ClawEmail + Obsidian + Claude Code

> 整合铁锤人 Newsletter 工作流 + 花叔橙皮书 Obsidian 方法论
> 从零搭建 AI 驱动的个人知识管理系统
> 来自翡冷翠

---

## 工作流架构图

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                        AI Newsletter 信息输入层                              │
├─────────────────────────────────────────────────────────────────────────────┤
│  The Rundown AI → Ben's Bites → Latent Space → The Neuron Daily             │
│  Interconnects → One Useful Thing → AI Breakfast → Every                   │
└────────────────────┬────────────────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                     ClawEmail 子邮箱 (hermes4.01@claw.163.com)              │
│                         ↓ 自动接收 & 筛选                                   │
└────────────────────┬────────────────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                      Hermes Agent 处理层                                      │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐                      │
│  │ 日报生成     │  │ 深度文章筛选 │  │ LLM Wiki编译 │                      │
│  │ (Daily Skill)│  │ (人工+AI)    │  │ (核心)       │                      │
│  └──────────────┘  └──────────────┘  └──────────────┘                      │
└────────────────────┬────────────────────────────────────────────────────────┘
                     │
                     ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│                    Obsidian + Claude Code 知识库层                            │
│                                                                              │
│   Vault 结构:                                                                 │
│   ├── CLAUDE.md          (AI 导航中枢)                                       │
│   ├── index.md           (知识库入口)                                        │
│   ├── 01-Inbox/          (待处理输入)                                        │
│   ├── 02-Processing/     (处理中)                                              │
│   ├── 03-Knowledge/      (已整理知识)  ← LLM Wiki 核心                       │
│   │   ├── Concepts/      (概念卡片)                                          │
│   │   ├── Entities/      (实体/人物)                                         │
│   │   ├── Claims/        (主张/论点)                                         │
│   │   └── OpenQuestions/ (开放问题)                                          │
│   ├── 04-Projects/       (项目应用)                                          │
│   └── 05-Outputs/        (输出成品)                                           │
│                                                                              │
└─────────────────────────────────────────────────────────────────────────────┘
```

---

## 第一部分：信息输入层（Newsletter 订阅）

### 已配置的 8 个顶级 AI Newsletter

| # | Newsletter | 读者数 | 频率 | 核心内容 | 状态 |
|---|------------|--------|------|----------|------|
| 1 | The Rundown AI | 200万+ | 每日 | AI 产业动态 | ✅ 已订阅 |
| 2 | Ben's Bites | 162,000+ | 每日 | AI 工具资讯 | ✅ 已订阅 |
| 3 | Latent Space | 179,000+ | 定期 | AI Engineering | ✅ 已订阅 |
| 4 | The Neuron Daily | 700,000+ | 每日 | 非技术读者 | ✅ 已订阅 |
| 5 | Interconnects | 65,000+ | 定期 | RLHF/模型训练 | ✅ 已订阅 |
| 6 | One Useful Thing | 428,000+ | 定期 | 学术+工作洞察 | ✅ 已订阅 |
| 7 | AI Breakfast | 100,000+ | 每周3次 | 系统回顾 | ✅ 已订阅 |
| 8 | Every | 100,000+ | 定期 | 战略分析 | ✅ 已订阅 |

### 待手动完成（2个）

| # | Newsletter | 读者数 | 核心内容 | 操作 |
|---|------------|--------|----------|------|
| 9 | TLDR AI | 920,000+ | 5分钟科技简报 | 访问 https://tldr.tech/ai 手动订阅 |
| 10 | Smol AI News | 150,000+ | 社区直击 | 访问 https://news.smol.ai/subscribe 手动订阅 |

---

## 第二部分：ClawEmail 邮箱配置

### 已配置的邮箱

```bash
# 主邮箱
hermes4@claw.163.com (default)

# Newsletter 专用子邮箱  
hermes4.01@claw.163.com (01)
```

### 子邮箱通讯规则设置

需要登录 ClawEmail Dashboard 完成：
1. Dashboard → Agent 邮箱管理 → 选择 hermes4.01
2. 通讯规则 → 开放外部通信
3. 收信范围 → 所有人（newsletter 发件域太杂）

---

## 第三部分：LLM Wiki 知识编译（核心方法论）

### 核心洞察（来自橙皮书 + Karpathy）

**洞察1：Markdown 是 AI Agent 的原生接口**
- Manus（Meta 20亿美元收购）、OpenClaw（35.5万+ stars）、Claude Code 都选择 Markdown 存储 AI 记忆
- 不是向量数据库，而是纯文本 Markdown 文件
- Obsidian vault 就是一堆 Markdown 文件，天生适配

**洞察2：LLM 应该是「编译器」而非「检索器」**
- Karpathy 核心论点：与其建 RAG 让 LLM 检索笔记，不如让 LLM 直接维护知识库
- RAG 检索太窄，LLM 应该做知识编译器
- 在 40 万字规模下验证有效

**洞察3：CLAUDE.md + index.md 做了 80% 的工作**
- 不需要复杂的 MCP 设置
- 一个 CLAUDE.md（AI 导航中枢）+ 每个文件夹一个 index.md
- 足以让 Claude Code 高效导航整个知识库

### Vault 架构设计

```
~/My-Second-Brain/
├── CLAUDE.md              # AI 导航中枢文件
├── index.md               # 知识库入口索引
├── 01-Inbox/              # 收件箱（原始输入）
│   └── [日期]-newsletter-summary.md
├── 02-Processing/         # 处理中
│   └── [文章标题]-raw.md
├── 03-Knowledge/          # 已整理知识（LLM Wiki 核心）
│   ├── Concepts/          # 概念卡片
│   │   ├── llm-wiki.md
│   │   ├── rag-vs-compile.md
│   │   └── [概念名称].md
│   ├── Entities/          # 实体/人物
│   │   ├── karpathy-andrej.md
│   │   ├── altman-sam.md
│   │   └── [人物/公司].md
│   ├── Claims/            # 主张/论点
│   │   └── [主张摘要].md
│   └── OpenQuestions/     # 开放问题
│       └── [问题].md
├── 04-Projects/           # 项目应用
│   └── [项目名称]/
└── 05-Outputs/            # 输出成品
    ├── x-posts/
    ├── articles/
    └── reports/
```

### CLAUDE.md 模板

```markdown
# CLAUDE.md - 第二大脑导航中枢

## Vault 结构
- `01-Inbox/` - 原始输入（newsletter、文章、笔记）
- `02-Processing/` - 处理中内容
- `03-Knowledge/` - 已整理知识库（核心）
  - `Concepts/` - 概念卡片
  - `Entities/` - 实体/人物卡片
  - `Claims/` - 主张/论点卡片
  - `OpenQuestions/` - 开放问题
- `04-Projects/` - 项目应用
- `05-Outputs/` - 输出成品

## 工作流指令

### /compile 命令
当用户说"编译到 Wiki"时：
1. 读取指定文章/内容
2. 提取关键概念、实体、主张、开放问题
3. 在 03-Knowledge/ 创建或更新对应卡片
4. 建立双向链接（[[概念名]]）
5. 更新相关 index.md

### /daily 命令
生成每日知识摘要：
1. 读取 01-Inbox/ 当天内容
2. 筛选高价值信息
3. 推荐今日深读文章
4. 输出摘要到日报文件

## 命名规范
- 概念卡片: `概念名称.md`
- 实体卡片: `姓氏-名字.md` 或 `公司名.md`
- 主张卡片: `主张前5个词...md`
- 日期格式: `YYYY-MM-DD`

## 链接规范
- 使用 Wikilink: `[[概念名]]`
- 别名链接: `[[概念名|显示文字]]`
- 块引用: `[[概念名#标题]]`
```

### LLM Wiki 编译流程

**步骤1：文章进入 Inbox**
```
Hermes: 读取今天的 newsletter，保存到 01-Inbox/2026-04-24-newsletter.md
```

**步骤2：执行 /compile 命令**
```
用户: 这篇文章编译到我的 Wiki
Hermes: 
  1. 读取文章内容
  2. 提取关键概念（如 "Claude Design"、"LLM Wiki"）
  3. 提取实体（如 "Anthropic"、"Karpathy"）
  4. 提取主张（如 "AI 应该做编译器而非检索器"）
  5. 在 03-Knowledge/ 创建/更新卡片
  6. 建立链接：[[Claude Design]]、[[Karpathy]]、[[LLM Wiki]]
  7. 更新 index.md
```

**步骤3：知识图谱可视化**
- 在 Obsidian 中打开 Graph View
- 查看概念间的链接关系
- 发现新的知识连接

---

## 第四部分：实战工作流（7个可直接复制）

### 工作流1：Newsletter 自动筛选

**触发**: 每天早晨
**动作**:
1. Hermes 读取 hermes4.01@claw.163.com 新邮件
2. 按优先级排序（The Rundown AI > TLDR AI > ...）
3. 生成摘要，保存到 01-Inbox/YYYY-MM-DD-newsletter-summary.md
4. 推荐今日深读文章（1篇）

**Prompt**:
```
读取 hermes4.01@claw.163.com 今天的 newsletter 邮件。
对每篇文章：
- 提取标题、核心观点、关键链接
- 评估重要性（1-5分）
- 判断是否值得深度阅读

输出格式：
## 今日 Newsletter 摘要 (YYYY-MM-DD)

### 🔥 推荐深读
1. [文章标题] - [来源] - 重要性: 5/5
   核心观点: [一句话总结]
   链接: [URL]

### 📋 其他简报
2. [文章标题] - [来源] - 重要性: X/5
   ...

保存到 01-Inbox/2026-04-24-newsletter-summary.md
```

### 工作流2：文章编译到 Wiki

**触发**: 发现高价值文章
**动作**: 执行 /compile 命令

**Prompt**:
```
读取文件 01-Inbox/[文章].md，执行 LLM Wiki 编译：

1. 提取关键概念（3-5个），在 03-Knowledge/Concepts/ 创建/更新卡片
2. 提取实体/人物（2-3个），在 03-Knowledge/Entities/ 创建/更新卡片
3. 提取核心主张（2-3个），在 03-Knowledge/Claims/ 创建/更新卡片
4. 提取开放问题（如有），在 03-Knowledge/OpenQuestions/ 创建卡片
5. 在每个卡片中建立双向链接 [[相关概念]]
6. 更新 03-Knowledge/index.md

输出：显示创建/更新的所有卡片列表
```

### 工作流3：概念深度研究

**触发**: 遇到不懂的概念
**动作**: 在 Wiki 中追问

**Prompt**:
```
在 Obsidian Wiki 中搜索概念 [[Claude Design]]，然后：
1. 列出所有引用该概念的卡片
2. 总结该概念的多个维度定义
3. 找出相关但尚未链接的概念
4. 建议下一步阅读
```

### 工作流4：信息图生成

**触发**: 需要可视化输出
**动作**: 基于 Wiki 内容生成信息图

**Hermes Agent 内置命令**:
```
使用信息图命令行，基于 03-Knowledge/Concepts/llm-wiki.md 生成信息图
主题: "LLM Wiki vs RAG 的区别"
```

### 工作流5：X 文章撰写辅助

**触发**: 撰写 X 文章时
**动作**: 查询 Wiki 获取支持

**Prompt**:
```
我正在写一篇关于 [主题] 的 X 文章。
请查询我的 Wiki：
1. 找出上周读过支持这个观点的文章
2. 找出可以反驳这个观点的视角
3. 建议我没有考虑到的角度
4. 从 Wiki 中提取关键引用
```

### 工作流6：周报生成

**触发**: 每周日晚
**动作**: 汇总本周知识输入

**Prompt**:
```
汇总本周 01-Inbox/ 和 03-Knowledge/ 的更新：
1. 统计本周新增概念、实体、主张数量
2. 列出本周最重要的 3 个新洞察
3. 生成知识图谱变化摘要
4. 输出周报到 05-Outputs/weekly/YYYY-MM-DD-weekly-report.md
```

### 工作流7：项目知识库建立

**触发**: 启动新项目
**动作**: 创建项目专用知识库

**Prompt**:
```
创建新项目 "[项目名称]" 的知识库：
1. 在 04-Projects/[项目名称]/ 创建项目目录
2. 创建 project-index.md（项目目标、关键问题、相关概念）
3. 从 03-Knowledge/ 链接相关概念到项目
4. 设置项目跟踪模板
```

---

## 第五部分：推荐插件生态（1000+ 中选 4 个）

### 必备插件

| 插件名 | 功能 | 用途 |
|--------|------|------|
| **Claudian** | Claude Code 图形化界面 | 在 Obsidian 中直接与 AI 对话 |
| **Dataview** | 动态查询 | 生成自动化知识统计、仪表盘 |
| **Graph Analysis** | 图谱分析 | 发现知识间的隐藏连接 |
| **Obsidian Web Clipper** | 一键剪藏 | 快速保存网页到 Inbox |

---

## 第六部分：部署清单

### 已完成 ✅

- [x] 配置 ClawEmail 主邮箱 (hermes4@claw.163.com)
- [x] 配置 ClawEmail 子邮箱 (hermes4.01@claw.163.com)
- [x] 订阅 8 个核心 AI Newsletter
- [x] 整理 Newsletter 工作流文档
- [x] 研究 Obsidian + Claude Code 橙皮书完整教程

### 待完成 ⏳

**立即（今日）**:
- [ ] 手动订阅 TLDR AI (https://tldr.tech/ai)
- [ ] 手动订阅 Smol AI News (https://news.smol.ai/subscribe)
- [ ] 设置子邮箱通讯规则（开放外部通信）
- [ ] 检查确认邮件并完成确认

**本周内**:
- [ ] 安装 Obsidian
- [ ] 安装 Claude Code (`npm install -g @anthropic-ai/claude-code`)
- [ ] 创建 Vault 目录结构
- [ ] 编写 CLAUDE.md 导航文件
- [ ] 安装 Claudian 插件
- [ ] 测试第一个 /compile 命令

**持续进行**:
- [ ] 每日执行 Newsletter 筛选工作流
- [ ] 每周执行 LLM Wiki 编译（至少 3 篇文章）
- [ ] 每周生成周报
- [ ] 每月回顾知识图谱演变

---

## 参考资源

### 核心教程
- **铁锤人原文**: https://x.com/lxfater/status/2047150392274993624
- **橙皮书 GitHub**: https://github.com/alchaincyf/obsidian-ai-orange-book (717⭐)
- **橙皮书 PDF**: [Obsidian-AI-v1.0.0.pdf](https://github.com/alchaincyf/obsidian-ai-orange-book/blob/master/Obsidian-AI-v1.0.0.pdf)

### 工具文档
- **ClawEmail 文档**: https://claw.163.com/projects/doc/
- **Claude Code 文档**: https://docs.anthropic.com/en/docs/agents/claude-code
- **Obsidian 官网**: https://obsidian.md/

### Newsletter 源
| Newsletter | 链接 |
|------------|------|
| The Rundown AI | https://www.therundown.ai/ |
| TLDR AI | https://tldr.tech/ai |
| The Neuron | https://www.theneurondaily.com/ |
| Ben's Bites | https://www.bensbites.com/ |
| Latent Space | https://www.latent.space/ |
| Smol AI News | https://news.smol.ai/ |
| Interconnects | https://www.interconnects.ai/ |
| One Useful Thing | https://www.oneusefulthing.org/ |
| AI Breakfast | https://aibreakfast.beehiiv.com/ |
| Every | https://every.to/ |

---

*来自翡冷翠*
