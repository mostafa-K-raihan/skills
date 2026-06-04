# Chinese Technical Prose

Use this reference when writing, rewriting, or reviewing Chinese technical prose. Focus only on three things:

- evidence-first claims
- removing narrator-style filler
- replacing buzzwords and empty evaluations with concrete information

Do not use this reference to impose a special long-form internal-document structure. Keep the document shape chosen in `SKILL.md`.

## Evidence-First Claims

Prefer this order:

```text
observation / code / issue / trace / metric / example -> pattern -> conclusion -> action
```

Before a strong claim, ask:

- What was observed?
- Where is the evidence?
- Which module, command, trace, metric, issue, user behavior, or example supports it?
- Is the statement a conclusion, an assumption, or a decision?

Rewrite unsupported conclusions into evidence-backed statements.

Weak:

```text
这条链路已经很清楚。
```

Stronger:

```text
从现有调用看，A 先写入 task state，B 再从同一个状态入口读取结果。这个顺序说明当前风险主要集中在状态写入和读取之间的一致性。
```

Weak:

```text
这个方案很适合后续扩展。
```

Stronger:

```text
这个方案把解析逻辑放在 adapter 边界内，新增 source 时只需要补一个 adapter，不需要改调度层。
```

Use softer wording when evidence is incomplete:

- `当前证据更支持...`
- `从这几处调用看...`
- `这里先按假设处理...`
- `还需要用...验证`

## Remove Narrator-Style Filler

Delete sentences that only manage the article's flow and do not add facts, constraints, or reasoning.

Common filler patterns:

- `聊到这里...`
- `接下来我们来看...`
- `这一节真正想说明的是...`
- `这张图想表达的很简单...`
- `最后用一句话收住...`
- `先把这个问题单独拿出来说...`
- `继续往下看...`

Default action:

1. Delete the sentence.
2. Let the next factual sentence become the opening.
3. If the transition contains real information, rewrite it as a condition, object, relationship, or result.

Weak:

```text
接下来我们来看 Agent Runtime 这一层。
```

Stronger:

```text
Agent Runtime 是请求进入执行阶段后的第一个稳定边界。
```

Weak:

```text
这张图想说明的事情很简单。
```

Stronger:

```text
图里的关键关系是：adapter 只负责输入归一化，policy 才决定是否触发后续动作。
```

## Buzzword And Empty-Word Audit

Do not mechanically replace a word with another word. First decide whether the sentence contains real information. If it does not, delete it. If it does, rewrite around concrete actors, actions, constraints, data, or effects.

### Abstract buzzwords

| Avoid | Replace with |
| --- | --- |
| `生态` | concrete dependencies, users, integrations, or ownership |
| `赋能` | `让 X 能 Y` |
| `闭环` | the concrete path from A to B and back to A |
| `抓手` | the variable or mechanism the team can change |
| `打通链路` | which producer can now call/read/write which consumer |
| `沉淀` | where the knowledge, rule, or artifact is recorded |
| `落地` | the module, workflow, or scenario where it is implemented |
| `底座` | the infrastructure, prerequisite, or shared module |
| `一站式` | which tasks can be completed in the same entry point |
| `深度集成` | exact integration points and data/control flow |

### Empty evaluations

| Avoid | Ask instead |
| --- | --- |
| `很清楚` | clear from which code path, metric, or example? |
| `很顺` | lower cost, fewer steps, cleaner boundary, or less latency? |
| `很现实` | which constraint appears after which condition? |
| `显然` | what evidence makes it obvious? |
| `真正` | what contrast is being proven? |
| `极致` | which measurable target improves? |
| `值得` | valuable on which dimension and for whom? |

## Rewrite Pattern

Use this pattern when a Chinese sentence feels inflated:

1. Identify the claim.
2. Identify the actor and object.
3. Add the supporting evidence or condition.
4. Name the concrete effect.
5. Delete any sentence left over that only comments on the writing flow.

Example:

Weak:

```text
这个能力会形成一个比较完整的闭环，也能沉淀更多经验。
```

Stronger:

```text
完成 action 后，系统会把结果写回 task history。后续调试可以直接从同一条 task history 里看到输入、决策和执行结果。
```

Example:

Weak:

```text
这个入口会赋能更多场景。
```

Stronger:

```text
这个入口暴露后，CLI 和后台任务可以复用同一套解析逻辑，不需要各自维护参数转换代码。
```

## Review Checklist

- Does each strong claim have evidence, a condition, or a clear assumption marker?
- Are module names, metrics, traces, issues, commands, or examples used where they would clarify the claim?
- Did you delete narrator-style transition sentences rather than polishing them?
- Did buzzwords become concrete actors, actions, constraints, data, or effects?
- Did empty evaluations become measurable or observable statements?
- Did the final prose still preserve the user's intended meaning?
