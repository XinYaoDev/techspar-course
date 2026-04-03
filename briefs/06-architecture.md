# Module 6: 架构全景 — 所有组件如何协同

## Teaching Arc
- **Metaphor:** 管弦乐团——每个人只演奏自己的乐器，但指挥让所有人合成一首曲子。TechSpar 也是：前端、后端、LangGraph、Profile、SM-2 各司其职，FastAPI 指挥协调。
- **Opening hook:** 让我们把 TechSpar 拆开看：从你点"开始训练"到收到"薄弱点分析报告"，这中间经过了哪些组件？
- **Key insight:** TechSpar 是一个典型的"前端轻、后端重"架构——React 负责交互，FastAPI 负责大脑，LangGraph 负责流程编排，Profile.json 负责记忆。
- **"Why should I care?":** 知道架构，能让你判断"这个功能应该加在前端还是后端"，以及"这个问题该问谁"。

## Code Snippets (pre-extracted)

File: docker-compose.yml (架构概览)
```
Frontend: React 19 + Vite + Tailwind CSS → :5173
Backend: FastAPI + LangChain + LangGraph  → :8000
SQLite: 本地持久化
JWT: 认证
```

File: backend/main.py (API 入口)
```python
@router.post("/interview/resume")
async def resume_interview(user_id: str, ...):
    # 1. 读取 profile + 历史
    # 2. 启动 LangGraph 状态机
    # 3. 流式返回 AI 回复
    # 4. 更新 profile + SM2 调度
```

## Interactive Elements

- **Code↔English translation** — docker-compose 和 API 入口
- **Quiz** — 3题：综合应用——给一个新产品需求，问加在哪里，为什么
- **Group chat animation** — 组件总动员：Frontend / FastAPI / LangGraph / Profile / SM-2 各自发言
- **Data flow animation** — 完整端到端流程图：用户点击"简历面试" → FastAPI → LangGraph → LLM → Profile 更新 → SM-2 调度
- **其他** — 架构总图（前端 / 后端 / 存储层）

## Reference Files to Read
- `references/content-philosophy.md` → 全文
- `references/gotchas.md` → 全文
- `references/interactive-elements.md` → Group Chat Animation, Data Flow Animation, Multiple-Choice Quizzes

## Connections
- **Previous module:** 实时 Copilot — 单个功能讲完，现在看整体
- **Next module:** 无（总结模块）
- **Tone/style notes:** accent=vermillion，语言=简体中文

---

## Module 6 Screen Plan

### Screen 6-1: TechSpar 的三层架构
**Hero visual:** 三层图——前端交互层 / 后端大脑层 / 数据持久层

### Screen 6-2: 组件总动员
**Visual:** Group Chat Animation — 5个组件角色各自介绍职责

### Screen 6-3: 端到端数据流
**Visual:** Data Flow Animation — 完整流程：点击"开始" → 收到"薄弱点报告"

### Screen 6-4: Code ↔ English
**Content:** API 入口注释

### Screen 6-5: TechSpar vs 传统面试工具
**Visual:** 对比表

### Screen 6-6: 测验
**Quiz:** 3题综合应用
