# Module 5: 实时 Copilot — 面试现场的 AI 辅助

## Teaching Arc
- **Metaphor:** 导航仪——你开车，导航仪在旁边实时提示：前方急转弯（追问方向），建议加速（深挖技术细节），前方测速（小心陷阱题）。
- **Opening hook:** 你正在真实面试，HR 抛出一个问题——Copilot 同时在转写、预测追问方向、给你回答建议。这些工作同时发生，你感觉不到延迟。
- **Key insight:** Copilot 不是等 HR 说完再处理，而是实时流式处理——每句话都在被分析，每个回答建议都在更新。
- **"Why should I care?":** 知道实时流式处理，能帮你理解为什么 AI 辅助工具会有延迟，以及"异步处理"和"实时处理"的区别。

## Code Snippets (pre-extracted)

File: backend/copilot/strategy.py (概念)
```
# Copilot 的核心输入：
# 1. JD（岗位描述）
# 2. 简历
# 3. 历史画像（薄弱点/强项）
# → 生成：提问策略树 + 高危路径（容易被追问的地方）
```

File: backend/transcribe.py (录音转写)
```python
# 录音复盘流程：
# 1. 上传录音 → 2. 自动转写 → 3. 结构化Q&A → 4. 逐题分析 → 5. 薄弱点提取
```

## Interactive Elements

- **Code↔English translation** — Copilot 预处理流程
- **Quiz** — 3题：场景判断——Copilot 报错或给出错误建议时，哪里出了问题？
- **Group chat animation** — Copilot vs HR vs 用户 三方实时对话
- **Data flow animation** — HR说话 → 流式转写 → LLM分析 → 回答建议浮现

## Reference Files to Read
- `references/content-philosophy.md` → 全文
- `references/gotchas.md` → 全文
- `references/interactive-elements.md` → Group Chat Animation, Data Flow Animation, Multiple-Choice Quizzes

## Connections
- **Previous module:** 简历面试状态机 — 静态流程；Copilot 是动态实时版
- **Next module:** 架构全景 — 把所有组件拼在一起看全貌
- **Tone/style notes:** accent=vermillion，语言=简体中文

---

## Module 5 Screen Plan

### Screen 5-1: 面试现场的 AI 副驾驶
**Hero visual:** 三列图：HR说话 / Copilot实时分析 / 用户看到建议

### Screen 5-2: Copilot 预处理 — 上场前的准备
**Visual:** 流程：JD + 简历 + 历史画像 → 提问策略树 + 高危路径

### Screen 5-3: 实时辅助的三件事
**Visual:** 三卡片——转写 / 方向预测 / 回答建议

### Screen 5-4: Group Chat Animation
**Content:** HR / Copilot / 用户 三方对话

### Screen 5-5: 测验
**Quiz:** 3题
