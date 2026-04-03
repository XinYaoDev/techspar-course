# Module 4: 简历面试状态机 — LangGraph 如何推进面试

## Teaching Arc
- **Metaphor:** 剧本杀主持人——手里有个流程单，引导你走过：开场 → 自我介绍 → 技术题 → 项目深挖 → 反问。
- **Opening hook:** AI 面试官怎么知道什么时候该切换问题类型？它不是"随机问"，而是按流程推进——每个阶段有固定的名字和转换规则。
- **Key insight:** LangGraph 是一个"状态机框架"：状态（State）记录面试进度，节点（Node）执行具体任务，边（Edge）决定下一步去哪里。
- **"Why should I care?":** 知道"状态机"这个概念，能让你指挥 AI"在这个阶段多加几道题"，而不是说"随便问问"。

## Code Snippets (pre-extracted)

File: backend/graphs/resume_interview.py (阶段顺序)
```python
PHASE_ORDER = [
    InterviewPhase.GREETING.value,        # 开场寒暄
    InterviewPhase.SELF_INTRO.value,       # 自我介绍
    InterviewPhase.TECHNICAL.value,       # 技术问题
    InterviewPhase.PROJECT_DEEP_DIVE.value,  # 项目深挖
    InterviewPhase.REVERSE_QA.value,     # 反问环节
]
HARD_MAX_PER_PHASE = 10  # 每阶段最多10题，防止无限循环
```

File: backend/graphs/resume_interview.py (状态定义)
```python
class ResumeInterviewState(TypedDict):
    messages: list[BaseMessage]       # 对话历史
    resume_context: str               # 简历上下文
    phase: str                        # 当前阶段
    questions_asked: list[str]       # 已问问题
    phase_question_count: int         # 当前阶段已问题数
    is_finished: bool                # 是否结束
    eval_history: list[dict]          # 每题评估历史
```

File: backend/models.py (阶段枚举)
```python
class InterviewPhase(str, Enum):
    GREETING = "greeting"
    SELF_INTRO = "self_introduction"
    TECHNICAL = "technical"
    PROJECT_DEEP_DIVE = "project_deep_dive"
    REVERSE_QA = "reverse_qa"
```

## Interactive Elements

- **Code↔English translation** — PHASE_ORDER 列表 + ResumeInterviewState 定义
- **Quiz** — 3题：哪个阶段负责什么？如果 AI 在 TECHNICAL 阶段一直问项目问题，哪里出错了？
- **Group chat animation** — 5个阶段角色：Greeting问"为什么紧张"，Technical说"我来接手"，Project说"该我了"...
- **Data flow animation** — 用户回答 → LLM判断是否切换阶段 → 阶段切换 → 新阶段提问
- **其他** — 流程图：GREETING → SELF_INTRO → TECHNICAL → PROJECT_DEEP_DIVE → REVERSE_QA

## Reference Files to Read
- `references/content-philosophy.md` → 全文
- `references/gotchas.md` → 全文
- `references/interactive-elements.md` → Group Chat Animation, Data Flow Animation, Multiple-Choice Quizzes

## Connections
- **Previous module:** SM-2 算法 — 面试前有调度，面试中有流程
- **Next module:** 实时 Copilot — 有流程框架之后，实时辅助是怎么工作的
- **Tone/style notes:** accent=vermillion，语言=简体中文

---

## Module 4 Screen Plan

### Screen 4-1: AI 面试官不是随机问问题
**Hero visual:** 流程图——5个阶段顺序推进

### Screen 4-2: 5个阶段分别做什么
**Visual:** 阶段卡片，每个阶段一句话说明

### Screen 4-3: Code ↔ English — PHASE_ORDER + State
**Content:** 阶段列表和状态定义

### Screen 4-4: Group Chat Animation
**Content:** 5个阶段角色对话，演示交接过程

### Screen 4-5: 测验
**Quiz:** 3题
