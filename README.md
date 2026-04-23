# Gmail Draft Automation — README

## Overview
This project automates Gmail draft creation for a business mailbox using an AI agent. It reads your historical emails to learn your business knowledge and writing style, then drafts replies to new unread threads for human review.

## Files
| File | Purpose |
|------|---------|
| `INIT.MD` | One-time bootstrap spec — generates the two knowledge files (COMPANY_BUSINESS_KNOWLEDGE.MD, EMAIL_REPLY_STYLE_GUIDE.MD) |
| `COMPANY_BUSINESS_KNOWLEDGE.MD` | Auto-generated business facts (pricing, scope, FAQs, etc.) |
| `EMAIL_REPLY_STYLE_GUIDE.MD` | Auto-generated writing style rules (tone, structure, sign-offs) |
| `GMAIL_DRAFT_AUTOMATION_PROMPT.MD` | Automation task prompt — used for every normal run |

## How It Works

### Step 1 — Initialize (run once)
Use the following prompt with your agent:
```
Follow instructions in INIT.MD
```
The agent will scan your Gmail history, extract durable business knowledge and writing patterns, and generate `COMPANY_BUSINESS_KNOWLEDGE.MD` and `EMAIL_REPLY_STYLE_GUIDE.MD`. Do not repeat this step unless you want to re-bootstrap.

### Step 2 — Automation Task (daily)
Copy and paste the full contents of `GMAIL_DRAFT_AUTOMATION_PROMPT.MD` as the prompt to your agent. It will:
1. Read the two knowledge files
2. Find all unread threads from the past 7 days
3. Skip noise, closed threads, and threads where you replied last
4. Create one draft per qualifying thread — ready for your manual review and send

**The agent never sends email. All drafts require human approval.**

---

# Gmail 草稿自动化 — README

## 项目简介
本项目使用 AI agent 为业务邮箱自动生成 Gmail 草稿。它通过读取历史邮件学习你的业务知识与写作风格，然后为新的未读会话起草回复，供人工审阅后发送。

## 文件说明
| 文件 | 用途 |
|------|------|
| `INIT.MD` | 一次性 bootstrap 规范 — 用于生成两份知识文件 (COMPANY_BUSINESS_KNOWLEDGE.MD, EMAIL_REPLY_STYLE_GUIDE.MD) |
| `COMPANY_BUSINESS_KNOWLEDGE.MD` | 自动生成的业务知识（定价、范围、FAQ 等）|
| `EMAIL_REPLY_STYLE_GUIDE.MD` | 自动生成的写作风格规则（语气、结构、落款等）|
| `GMAIL_DRAFT_AUTOMATION_PROMPT.MD` | 自动化任务 prompt — 每次日常运行时使用 |

## 运行方式

### 第一步 — 初始化（仅执行一次）
使用以下 prompt 与 agent 对话：
```
Follow instructions in INIT.MD
```
Agent 会扫描你的 Gmail 历史记录，提取持久的业务知识与写作模式，并生成 `COMPANY_BUSINESS_KNOWLEDGE.MD` 与 `EMAIL_REPLY_STYLE_GUIDE.MD`。初始化完成后，不要再重复此步骤，除非需要重新 bootstrap。

### 第二步 — 自动化任务（每日执行）
将 `GMAIL_DRAFT_AUTOMATION_PROMPT.MD` 的完整内容复制并粘贴，作为 prompt 提交给你的 agent。它将：
1. 读取两份知识文件
2. 找出过去 7 天内所有未读会话
3. 跳过噪音邮件、已结束的会话，以及最后一封由你回复的会话
4. 为每一条符合条件的会话创建一份草稿 — 供你手动审阅后发送

**Agent 不会发送任何邮件。所有草稿均需人工确认。**
