# Newsletter 订阅状态报告

> 子邮箱：`hermes4.01@claw.163.com`
> 时间：2026-04-24
> 来自翡冷翠

---

## 订阅进度总览

| 状态 | 数量 | Newsletter |
|------|------|------------|
| ✅ 已订阅 | 7 | The Rundown AI, Ben's Bites, Latent Space, AI Breakfast, Interconnects, Every, One Useful Thing |
| ⏳ 待确认 | 3 | TLDR AI, The Neuron, Smol AI News |

---

## 已订阅 Newsletter（7/10）

### 1. The Rundown AI ⭐
- **链接**: https://www.therundown.ai/
- **类型**: 每日 AI 产业动态
- **订阅邮箱**: hermes4.01@claw.163.com
- **特点**: 通俗易懂、密度高，已有 200万+ 读者

### 2. Ben's Bites ⭐
- **链接**: https://www.bensbites.com/
- **类型**: AI 工具资讯日报
- **订阅邮箱**: hermes4.01@claw.163.com
- **作者**: Ben Tossell
- **特点**: 工具圈消息源，已有 162,000+ 订阅者

### 3. Latent Space ⭐
- **链接**: https://www.latent.space/
- **类型**: AI Engineering 播客 + 简报
- **订阅邮箱**: hermes4.01@claw.163.com
- **作者**: swyx 和 Alessio
- **特点**: 未公开项目 + 工程视角，已有 179,000+ 订阅者

### 4. AI Breakfast
- **链接**: https://aibreakfast.beehiiv.com/
- **类型**: 每周 AI 新闻早餐
- **订阅邮箱**: hermes4.01@claw.163.com
- **特点**: 系统回顾 + 深度讨论，已有 100,000+ 订阅者

### 5. Interconnects ⭐
- **链接**: https://www.interconnects.ai/
- **类型**: RLHF、模型训练深度专栏
- **订阅邮箱**: hermes4.01@claw.163.com
- **作者**: Nathan Lambert
- **特点**: 前沿 AI 实验室内部视角，已有 65,000+ 订阅者

### 6. Every
- **链接**: https://every.to/
- **类型**: 科技与商业战略分析
- **订阅邮箱**: hermes4.01@claw.163.com
- **特点**: 资深专家战略分析，已有 100,000+ 订阅者

### 7. One Useful Thing ⭐
- **链接**: https://www.oneusefulthing.org/
- **类型**: AI 实用洞察
- **订阅邮箱**: hermes4.01@claw.163.com
- **作者**: Ethan Mollick（宾夕法尼亚大学沃顿商学院教授）
- **特点**: 学术 + 工作场景，已有 428,000+ 订阅者

---

## 待确认 Newsletter（3/10）

### 8. TLDR AI
- **链接**: https://tldr.tech/ai
- **类型**: 5 分钟科技简报
- **状态**: ⚠️ 被 Vercel Security Checkpoint 拦截
- **解决方案**: 需要手动访问并输入邮箱

### 9. The Neuron
- **链接**: https://www.theneuron.ai/
- **类型**: 面向非技术读者的 AI 日报
- **状态**: ⚠️ 被 Cloudflare 安全验证拦截
- **解决方案**: 需要手动访问并输入邮箱

### 10. Smol AI News ⭐
- **链接**: https://buttondown.email/ainews 或 https://news.smol.ai/
- **类型**: Discord、Reddit 等 AI 社区圈内直击
- **状态**: ⚠️ 订阅表单嵌入 iframe，浏览器操作超时
- **解决方案**: 需手动访问 https://news.smol.ai/subscribe/ 完成订阅
- **推荐语**: Andrej Karpathy 称这是 "best AI newsletter atm"

---

## 下一步操作

### 1. 确认邮件处理
多数 newsletter 会发送确认邮件到 `hermes4.01@claw.163.com`。需要：
- 检查邮箱中的确认邮件
- 点击确认链接或回复确认邮件
- 可使用 Hermes 自动提取确认链接并完成确认

### 2. 日报 Skill 安装
```bash
# 日报 Skill 当前安装失败（返回 405），可能原因：
# - URL 需要认证
# - 仓库权限问题
# - 需要更新安装方式

# 替代方案：等待官方更新 Skill 安装方式
```

### 3. 手动订阅剩余 Newsletter
对于被拦截的 3 个 newsletter，建议：
- 使用本地浏览器手动访问订阅页面
- 输入邮箱 `hermes4.01@claw.163.com`
- 完成人机验证（如有）

---

## 邮箱配置状态

```bash
# 邮箱列表
$ mail-cli clawemail list

EMAIL                           TYPE    STATUS  DISPLAY NAME
hermes4@claw.163.com            primary active  hermes4
hermes4.01@claw.163.com         sub     active  01
```

**子邮箱通讯规则**: 需要手动在 Dashboard 设置为「开放外部通信」+「所有人」

---

## 预期效果

完成全部订阅后，`hermes4.01@claw.163.com` 将每天收到：
- The Rundown AI - 每日 AI 产业动态
- Ben's Bites - AI 工具资讯
- Latent Space - AI Engineering 简报
- AI Breakfast - 每周系统回顾
- Interconnects - 深度技术专栏
- Every - 战略分析
- One Useful Thing - 实用洞察

预计每天接收 3-7 封 newsletter，可通过 Hermes Agent 自动筛选、摘要、编译到 LLM Wiki。

---

## 参考文档

完整工作流教程：https://github.com/Hermes-marovole/hermes-agent-workflow-clawemail/blob/main/README.md

---

*来自翡冷翠*
