# Module 2: 长期记忆系统 — 你的 AI 画像

## Teaching Arc
- **Metaphor:** 学校里老师手里的学生档案——不是记一次成绩，而是记录习惯、弱点、进步曲线。
- **Opening hook:** 你的简历面试表现被存进了一个 JSON 文件——里面记录了你的技术掌握度、表达习惯、答题模式。你知道里面写了什么吗？
- **Key insight:** TechSpar 用文件存储"你是谁"，而不是存在数据库黑箱里——这意味着你可以打开文件直接看到、修改你的画像。
- **"Why should I care?":** 知道数据存在哪里，就能判断这个工具是"真个性化"还是"假装记得你"。

## Code Snippets (pre-extracted)

File: backend/memory.py (Profile Schema 定义)
```python
DEFAULT_PROFILE = {
    "name": "",
    "target_role": "AI 应用开发实习生",
    # 技术掌握度 (topic → {level: 1-5, notes: str})
    "topic_mastery": {},
    # 薄弱点 (list of {point, topic, first_seen, last_seen, times_seen, improved})
    "weak_points": [],
    # 强项 (list of {point, topic, first_seen})
    "strong_points": [],
    # 表达与沟通特征
    "communication": {
        "style": "",        # e.g. "回答偏短，缺少具体例子"
        "habits": [],       # e.g. ["紧张时语速加快", "喜欢用类比解释"]
        "suggestions": [],  # e.g. ["多用 STAR 法描述项目"]
    },
    # 答题思维模式
    "thinking_patterns": {
        "strengths": [],    # e.g. ["能用类比解释抽象概念"]
        "gaps": [],         # e.g. ["对比类问题缺乏结构"]
    },
    # 面试统计
    "stats": {
        "total_sessions": 0,
        "avg_score": 0,
        "score_history": [],
    },
}
```

File: data/users/{user_id}/profile.json (实际文件路径)
```
data/users/{user_id}/profile.json
```

## Interactive Elements

- **Code↔English translation** — DEFAULT_PROFILE JSON，字段逐行翻译
- **Quiz** — 3题：场景判断（给一个新场景，问系统会如何读写 Profile）
- **Group chat animation** — 简历面试结束后，Profile 和 Topic Mastery 两个"角色"对话更新记录
- **Data flow animation** — 面试结束 → 评估 → 写入 profile.json → 下次训练读取

## Reference Files to Read
- `references/content-philosophy.md` → 全文
- `references/gotchas.md` → 全文
- `references/interactive-elements.md` → Group Chat Animation, Data Flow Animation, Multiple-Choice Quizzes

## Connections
- **Previous module:** TechSpar 是什么 — 知道了"有闭环"，现在知道"闭环是怎么记住你的"
- **Next module:** SM-2 算法 — 知道了"记忆什么"，现在知道"记忆如何调度"
- **Tone/style notes:** accent=vermillion，语言=简体中文

---

## Module 2 Screen Plan

### Screen 2-1: 你的画像存在哪里？
**Hero visual:** 文件夹截图：data/users/xxx/profile.json

### Screen 2-2: Profile 里都记了什么？
**Visual:** 分区图——Topic Mastery / Weak Points / Strong Points / Communication / Stats

### Screen 2-3: Code ↔ English — Profile Schema
**Content:** DEFAULT_PROFILE 字典，逐行英文翻译

### Screen 2-4: Group Chat Animation
**Content:** Profile 更新场景——评估模块说"用户对比类问题总答不好"，Profile 说"收到，记录为 gap"

### Screen 2-5: 测验
**Quiz:** 3题
