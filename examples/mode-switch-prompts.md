# Mode Switch Prompts

This file gives reusable prompts for testing persona interaction in academic scenarios.

## 1. Integrated

Use when you want one unified strict mentor answer.

Example prompt:

> 从导师视角整体判断这个开题是否成立。不要润色，先判断问题、方法和证据链是否站得住。

Expected behavior:

- one unified mentor voice
- problem-first judgment
- compact next action

## 2. Lens Switch: Vision

Use when the main question is thesis-worthiness, significance, or story coherence.

Example prompt:

> 切换到 vision lens，判断这个研究题目是否真的有博士论文级别的意义，以及整体叙事是否成立。

Expected behavior:

- stronger emphasis on significance and narrative closure
- still avoids hype
- does not skip problem validity

## 3. Lens Switch: Problem

Use when the main question is whether the problem is clean and worth attacking.

Example prompt:

> 切换到 problem lens，只判断这个方向的问题定义是否干净，是否抓住真正困难，不要先讨论写法。

Expected behavior:

- stronger emphasis on problem cleanliness
- identifies method-over-problem risk early
- likely to recommend narrowing

## 4. Lens Switch: Execution

Use when the main question is how to make the work executable.

Example prompt:

> 切换到 execution lens，把这个研究计划压缩成可以在三个月内验证的最小闭环。

Expected behavior:

- stronger emphasis on experiment chain and milestone planning
- concrete pass conditions
- reduced abstraction

## 5. Panel

Use when you want explicit multi-angle academic pressure.

Example prompt:

> 用 panel 模式审查这个博士开题：先给 vision、problem、execution 三个角度的短判断，再给最终综合结论。

Expected behavior:

- short multi-angle review
- clear disagreement when it matters
- final integrated decision

## 6. Defense

Use panel mode for high-stakes defense simulation.

Example prompt:

> 用 panel 模式模拟答辩委员会，重点检查题目意义、技术本质和实验可信度，然后给我最危险的问题。

Expected behavior:

- not theatrical role-play
- reveals the most dangerous attack surface
- ends with a response strategy
