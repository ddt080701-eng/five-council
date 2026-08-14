# Five Council — 五维审查官

一个纯 prompt 驱动的 AI 防讨好审查系统。让 LLM 在单次对话中模拟 5 个独立顾问角色 + 1 位主席，对你的观点、方案、选题、决策或商业想法进行多维度审查。

## 为什么需要这个

LLM 天生倾向于讨好用户——RLHF 训练让它们默认顺从、附和、不挑战。当你问"这个想法怎么样"时，大多数 AI 会说"这个想法很好，不过可以优化……"。

Five Council 强制 AI 站到你的对立面：

- 不先夸再批
- 不空泛批评
- 不和稀泥
- 不编造证据
- 不讨好式结尾

## 五个顾问

| 顾问 | 角色 | 做什么 |
|------|------|--------|
| 反驳者 | The Challenger | 用失败案例和数据挑毛病 |
| 本质追问者 | The Essence Questioner | 连追 3 层"凭什么"，挖未验证假设 |
| 机会发现者 | The Opportunity Finder | 找你漏掉的 C、D、E 方向 |
| 外行人 | The Outsider | 用大白话问最基本的问题 |
| 无情执行者 | The Ruthless Executor | 只关心今天下午能干什么 |

## 执行流程

```
用户提出想法
    ↓
第一阶段：5 个顾问独立发言（互不通气）
    ↓
第二阶段：交叉审查（互相反驳/补充/指出盲区）
    ↓
第三阶段：主席综合结论（明确判断 + 风险 + 证据 + 行动 + 置信度）
```

## 安装

### Claude Code / Codex / 通用 Agent

```bash
# 克隆到 skills 目录
git clone https://github.com/ddt080701/five-council.git ~/.codex/skills/five-council
```

### TraeWork

将 `SKILL.md` 放入项目的 `.trae/skills/five-council/` 目录。

### Claude Code

将 `SKILL.md` 放入 `~/.claude/skills/five-council/` 目录。

## 使用

安装后，对 AI 说以下任意一种即可触发：

```
/five-council
帮我审查一下这个想法
这个方案怎么样
帮我看看这个决策
五顾问
```

然后描述你的想法、方案或决策即可。

## 示例

```
用户：帮我审查一下"做AI宠物短片"这个想法

[AI 自动生成 5 个顾问的独立审查 → 交叉审查 → 主席综合结论]
```

## 与 llm-council 的区别

| | [llm-council](https://github.com/karpathy/llm-council) (Karpathy) | five-council (本项目) |
|---|---|---|
| 需要 API | 是（OpenRouter） | 不需要 |
| 模型多样性 | 真实多模型（GPT/Gemini/Claude/Grok） | 同一模型模拟 5 角色 |
| 成本 | 每次审查消耗多模型 API 调用 | 零成本 |
| 配置 | 需安装 FastAPI + React + API key | 零配置，即装即用 |
| 角色 | 匿名评审 + Chairman 排名 | 5 个有明确分工的顾问 + 主席 |

**代价**：缺少真正的模型多样性（5 个顾问本质上是同一个模型）
**优势**：零成本、零配置、即时可用、角色可定制

## 自定义

修改 `SKILL.md` 中的顾问角色定义即可。你可以：

- 替换顾问角色（比如把"外行人"换成"法务专家"）
- 增减顾问数量
- 调整执行流程
- 修改触发条件

## 设计理念

基于一个简单观察：**一个人提出想法时，最需要的不是认同，而是反对。** 但人天生倾向寻求认同，AI 天生倾向给予认同。Five Council 用结构化流程强制 AI 站到对立面，用 5 种不同的反对方式帮你看到盲区。

## License

MIT
