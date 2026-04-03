# Module 1: TechSpar 是什么

## Teaching Arc
- **Metaphor:** A personal trainer who watches you gym over weeks — not a one-time class.
- **Opening hook:** 你用过其他 AI 面试工具吗？每次进去都像第一次用它，毫无记忆。TechSpar 不一样——它记得你上次哪里答得差。
- **Key insight:** TechSpar 不是一个"生成更多题"的工具，它是一个**持续进化的面试训练闭环**：练 → 反馈 → 记忆 → 下一次更精准。
- **"Why should I care?":** 知道什么是"闭环"，才能判断一个 AI 工具是真的智能还是在装智能。

## Code Snippets (pre-extracted)

File: README.md (产品定位)
```
TechSpar 的核心不是某一个单独功能页面。
它的核心是同一套长期记忆、画像更新和下一轮训练调度机制。
专项训练、简历面试、JD 备面、实时 Copilot 与录音复盘，
不是彼此孤立的五个页面，而是围绕同一套长期记忆、掌握度和画像系统协同工作的同一个闭环。
```

File: backend/main.py (FastAPI 入口)
```python
from backend.graphs.resume_interview import create_resume_interview_graph
from backend.graphs.topic_training import create_topic_training_graph
from backend.memory import get_profile_summary, update_profile
from backend.spaced_repetition import get_due_reviews, sm2_update
```

## Interactive Elements

- **Code↔English translation** — README 文字：说明什么叫"闭环"
- **Quiz** — 3题，场景题：你发现工具每次都像重置新人，哪里出了问题？哪个组件需要修复？
- **Group chat animation** — 五个训练模式对话：专项训练、简历面试、JD备面、Copilot、录音复盘"认出了同一个人"
- **Data flow animation** — 用户做第一次训练 → 系统写回 Profile → 第二次训练读取 Profile（闭环流动）
- **其他** — 5个功能卡片，每个带图标和一句话说明

## Reference Files to Read
- `references/content-philosophy.md` → 全文
- `references/gotchas.md` → 全文
- `references/interactive-elements.md` → Group Chat Animation, Data Flow Animation, Multiple-Choice Quizzes
- `references/design-system.md` → 颜色/字体 token

## Connections
- **Previous module:** 无（intro 模块）
- **Next module:** 长期记忆系统 — 讲 Profile 和 Topic Mastery 怎么存储
- **Tone/style notes:** accent=vermillion，语言=简体中文

---

## Module 1 Screen Plan

### Screen 1-1: 你每次进去它都像第一次认识你
**Hero visual:** 并排对比图——左边：传统工具每次重置；右边：TechSpar 记住你

### Screen 1-2: TechSpar 的 5 种训练模式
**Visual:** 5个功能卡片，图标+一句话
- 专项强化训练：围绕薄弱点集中进攻
- 简历模拟面试：AI 读简历后开始问
- JD 定向备面：输入岗位描述，系统生成针对性问题
- 实时 Copilot：面试中实时辅助
- 录音复盘：上传录音，AI 分析哪里答得差

### Screen 1-3: 闭环是如何运转的
**Visual:** 循环图（训练 → 评估 → 画像更新 → 下轮训练更精准 → 训练）

### Screen 1-4: Code ↔ English
**Content:** backend/main.py 导入语句，逐行英文翻译

### Screen 1-5: 测验
**Quiz:** 3题场景判断
