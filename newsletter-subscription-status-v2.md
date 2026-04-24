# Newsletter 订阅状态报告 V2

> 子邮箱：`hermes4.01@claw.163.com`
> 更新时间：2026-04-24
> 来自翡冷翠

---

## 订阅进度总览

| 状态 | 数量 | Newsletter |
|------|------|------------|
| ✅ 已订阅 | 8/10 | 详见下方清单 |
| ⏳ 需手动完成 | 2/10 | TLDR AI, Smol AI News |

**完成率：80%**

---

## 已订阅 Newsletter（8/10）

### 核心信息源 ⭐⭐⭐

| # | Newsletter | 订阅邮箱 | 读者数 | 频率 | 核心亮点 |
|---|------------|----------|--------|------|----------|
| 1 | **The Rundown AI** | hermes4.01@claw.163.com | 200万+ | 每日 | AI 产业动态，通俗易懂、密度高 |
| 2 | **Ben's Bites** | hermes4.01@claw.163.com | 162,000+ | 每日 | Ben Tossell 的 AI 工具资讯 |
| 3 | **Latent Space** | hermes4.01@claw.163.com | 179,000+ | 定期 | swyx 的 AI Engineering 简报 |
| 4 | **The Neuron Daily** | hermes4.01@claw.163.com | 700,000+ | 每日 | 面向非技术读者，3分钟读完 |
| 5 | **Interconnects** | hermes4.01@claw.163.com | 65,000+ | 定期 | Nathan Lambert 的 RLHF/模型训练深度专栏 |
| 6 | **One Useful Thing** | hermes4.01@claw.163.com | 428,000+ | 定期 | Ethan Mollick (沃顿教授) 的实用洞察 |

### 补充信息源 ⭐⭐

| # | Newsletter | 订阅邮箱 | 读者数 | 频率 | 核心亮点 |
|---|------------|----------|--------|------|----------|
| 7 | **AI Breakfast** | hermes4.01@claw.163.com | 100,000+ | 每周3次 | 系统回顾 + 深度讨论 |
| 8 | **Every** | hermes4.01@claw.163.com | 100,000+ | 定期 | 科技与商业战略分析 |

---

## 需手动完成（2/10）

### 9. TLDR AI ⭐⭐⭐
- **链接**: https://tldr.tech/ai
- **读者数**: 920,000+（最大规模！）
- **频率**: 每日
- **核心亮点**: 5 分钟科技简报，AI + 编程 + 产品精华浓缩
- **状态**: ⚠️ 被 Vercel Security Checkpoint 拦截，需手动访问
- **操作**: 用本地浏览器访问 https://tldr.tech/ai，输入邮箱订阅

### 10. Smol AI News ⭐⭐⭐
- **链接**: https://news.smol.ai/subscribe 或 https://buttondown.email/ainews
- **读者数**: 150,000+（AI Engineers）
- **频率**: 每个工作日
- **核心亮点**: 总结 AI Discord + Reddit + X/Twitter 社区内容
- **推荐语**: Andrej Karpathy: "best AI newsletter atm"
- **状态**: ⚠️ 订阅表单嵌入 iframe，浏览器自动化无法填写
- **操作**: 手动访问 https://news.smol.ai/subscribe 完成订阅

---

## 手动订阅操作指南

### TLDR AI 订阅步骤
```
1. 用本地 Chrome 访问 https://tldr.tech/ai
2. 等待 Vercel 验证完成（可能需要人机验证）
3. 在邮箱输入框填入: hermes4.01@claw.163.com
4. 点击 "Sign Up" 或 "Subscribe"
5. 检查邮箱确认邮件（如有）
```

### Smol AI News 订阅步骤
```
1. 访问 https://news.smol.ai/subscribe
2. 在邮箱输入框填入: hermes4.01@claw.163.com
3. 点击 "Subscribe"
4. 检查邮箱确认邮件并点击确认链接
```

---

## 确认邮件处理

订阅后可能收到的确认邮件类型：
- **Substack** (Ben's Bites, Latent Space, Interconnects, One Useful Thing): 需要点击确认链接
- **Beehiiv** (AI Breakfast, The Neuron Daily): 可能需要确认
- **自建站** (The Rundown AI, Every): 通常自动确认

**处理方法**:
```bash
# 检查收件箱
mail-cli folder list
# 1	收件箱

mail-cli mail list --fid 1 --limit 20

# 读取确认邮件并提取确认链接
mail-cli read [message-id]
```

或用 Hermes 自动处理：
```
检查 hermes4.01@claw.163.com 邮箱中的确认邮件，
提取所有确认链接，
用浏览器逐一访问完成确认
```

---

## 日报 Skill 替代方案

### 原方案（不可用）
```bash
npx skills add https://claw.163.com/gitea-web/s/daily-report.git
# 错误：405 Not Allowed
```

### 替代方案 1：自建日报工作流
创建一个简单的 cron 任务，每天自动读取 newsletter 并生成摘要：

```python
#!/usr/bin/env python3
# daily_newsletter_digest.py

from hermes_tools import terminal

# 1. 读取邮箱中的 newsletter
# 2. 使用 LLM 生成摘要
# 3. 输出为 Markdown 格式
# 4. 发送通知
```

### 替代方案 2：使用现有 Skill
- **GitHub**: zhuyansen/ai-hotspot-dailyreport-skill
- **功能**: 自动收集 200+ AI 热点，生成可视化报告

### 替代方案 3：手动 LLM Wiki 流程
按照文章中的方法：
1. 让 Hermes 读取感兴趣的 newsletter 文章
2. 输入: "这篇编译到我的 Wiki"
3. 自动生成互联的知识卡片

---

## 预期每日邮件量

完成全部 10 个订阅后，预计每日接收：

| 时间 | Newsletter | 类型 |
|------|------------|------|
| 早晨 | The Rundown AI | AI 产业 |
| 早晨 | Ben's Bites | 工具资讯 |
| 早晨 | The Neuron Daily | 非技术读者 |
| 早晨 | Smol AI News | 社区直击 |
| 上午 | TLDR AI | 科技简报 |
| 定期 | Latent Space | 工程视角 |
| 定期 | Interconnects | 深度技术 |
| 定期 | One Useful Thing | 学术洞察 |
| 定期 | AI Breakfast | 系统回顾 |
| 定期 | Every | 战略分析 |

**总计**: 每日 4-6 封核心 newsletter，加上定期深度内容

---

## 下一步行动

1. **立即**: 手动完成 TLDR AI 和 Smol AI News 的订阅
2. **今日**: 检查邮箱确认邮件，完成确认流程
3. **明日**: 开始接收首批 newsletter，测试 LLM Wiki 工作流
4. **本周**: 建立日报生成 Skill 或手动 LLM Wiki 流程

---

## 参考链接

- 完整工作流教程：https://github.com/Hermes-marovole/hermes-agent-workflow-clawemail/blob/main/README.md
- 铁锤人原文：https://x.com/lxfater/status/2047150392274993624
- ClawEmail 文档：https://claw.163.com/projects/doc/

---

*来自翡冷翠*
