# Academic Mentor Skill Repo

中文 | [English](./README_EN.md)

你是否想过：如果世界上顶级的科学家能够成为你的长期导师，会怎样指导你的毕业论文、研究方向和科研训练？

不是简单回答问题，也不是把知识点堆给你；而是在你选题发散时帮你收束，在你方法堆叠时指出真正的问题，在你写开题和论文时追问证据是否站得住，在你准备答辩时提前暴露最危险的漏洞。

这个仓库试图把这种“引路人”做成可运行的 skill 系统：一个助手负责和你一起读论文、整理知识、推进写作和实验；一个导师负责从更高标准审查研究方向、问题定义、证据链和完成质量。两者不是互相附和，而是在“助手执行 + 导师审查 + 未完成则继续”的对抗式闭环中，帮助你把科研任务真正做到可交付。

它不是通用陪聊人格，而是一个面向学术场景的导师-助手协作仓库。`academic-research-copilot` 负责执行，`academic-mentor` 负责审查，覆盖研究方向筛选、开题把关、论文逻辑审查、答辩准备、阶段性研究决策，以及“目标未完成则有界续跑”的学术任务闭环。

## 为什么需要它

大多数 AI 学术助手的问题不是知识不够，而是缺少导师式判断：

- 它会帮你润色一句话，却不一定指出这句话背后的 claim 根本站不住。
- 它会给你列出很多方法，却不一定判断这些方法是否服务于一个干净的问题。
- 它会鼓励你继续探索，却不一定告诉你这个方向应该收缩、补证据，甚至及时放弃。
- 它会生成一份看起来完整的开题报告，却不一定检查题目、科学问题、研究路线和实验闭环是否一致。

本仓库的核心目标是把“知识型助手”升级成“科研训练系统”：助手陪你做，导师逼你想清楚；助手推进交付，导师判断是否真的完成。

## 仓库目标

这个仓库解决四件事：

1. 把 `academic-mentor` 和 `academic-research-copilot` 封装成可直接安装、可直接推送 GitHub 的双 skill 仓库
2. 把导师人格从“模仿名人说话”收束到“基于公开来源提炼研究判断规则”
3. 将李飞飞、何凯明、李沐三类导师特质转化为可审查、可测试、可切换权重的内部判断机制
4. 将其升级为“助手执行 + 导师审查 + 有界续跑 + 反馈调权学习”的学术协作系统

## 仓库内容

- 可安装 skill：
  - `skills/academic-mentor/`
  - `skills/academic-research-copilot/`
- 仓库级方法文档：
  - `docs/skill-review-and-architecture.md`
  - `docs/source-distillation-and-testing.md`
  - `docs/persona-interaction-and-switching.md`
  - `docs/adversarial-completion-loop.md`
- 示例与测试设计：
  - `examples/mode-switch-prompts.md`
  - `tests/academic-persona-eval.md`

## 当前 skill 的核心逻辑

`academic-mentor` 的判断顺序固定为：

1. 先判断问题是否成立
2. 再判断方法是否服务于问题
3. 再判断证据是否支撑主张
4. 最后才看措辞和包装

它的默认产品形态现在是一个“统一导师系统”：

- 用户看到的是一个连续稳定的统一导师
- 内部由三位导师协同分析
- 学生反馈用于调节三位导师权重，而不是改写底层事实

内部三位导师分别负责：

- `Fei-Fei advisor`
  - 大图景、研究意义、叙事闭环
- `Kaiming advisor`
  - 问题是否干净、方法是否本质、复杂度是否值得
- `Li-Mu advisor`
  - 如何拆解、如何验证、如何把问题压到可执行步骤

这些导师不是角色扮演，而是内部判断分析器。

## 来源蒸馏方式

当前仓库已经包含三份人物源包：

- `fei-fei-li-source-pack.md`
- `kaiming-he-source-pack.md`
- `li-mu-source-pack.md`

但如果要进一步提升质量，蒸馏材料还应继续扩展到：

- 代表论文和项目页
- 官方主页和机构资料
- 高信号公开课程、talk、lecture 和 video
- 能反映稳定研究观的访谈

其中最重要的一层不是“语气模仿”，而是“论文表达蒸馏”：

- 论文如何定义问题
- 论文如何控制贡献边界
- 论文如何组织证据与实验
- 论文如何处理局限、风险与不过度宣称

这一层现在已经被显式写入 skill 结构，见：

- `references/paper-first-distillation.md`
- `references/research/fei-fei-li-paper-dna.md`
- `references/research/kaiming-he-paper-dna.md`
- `references/research/li-mu-paper-dna.md`

并进一步细化为三张“代表论文写作剖面卡”：

- `references/research/fei-fei-li-paper-profile-card.md`
- `references/research/kaiming-he-paper-profile-card.md`
- `references/research/li-mu-paper-profile-card.md`

以及三份“代表论文锚点”：

- `references/research/fei-fei-li-representative-paper-anchors.md`
- `references/research/kaiming-he-representative-paper-anchors.md`
- `references/research/li-mu-representative-paper-anchors.md`

具体方法与建议见：

- [docs/source-distillation-and-testing.md](./docs/source-distillation-and-testing.md)
- [examples/mode-switch-prompts.md](./examples/mode-switch-prompts.md)
- [tests/academic-persona-eval.md](./tests/academic-persona-eval.md)

## 学术场景重点

本仓库的目标不是“让名人替你说话”，而是让导师 skill 在学术场景里更有判断力。重点适用场景：

- 开题题目和研究内容是否成立
- 研究方向是否值得继续
- 论文是否在讲真问题
- 方法是否大于问题
- 答辩时哪里最容易被打穿

当前 `paper` 能力已进一步拆分为两类：

- `paper-logic`
  - 先判断论文到底有没有在讲真问题、论证是否站得住
- `paper-strategy`
  - 在方向基本成立的前提下，判断下一步最该怎么改、怎么补实验、怎么收贡献

## 对抗式完成检查 Hook

仓库现在加入了 skill 协议层的完成检查机制：

- `academic-research-copilot` 负责执行任务
- `academic-mentor` 负责判断目标是否完成
- 若导师返回 `continue`，助手只执行导师给出的下一轮任务
- 默认最多 3 轮，避免无限运行

核心对象：

- `Goal Contract`
- `Completion Check`
- `Loop Trace`

这是一套客户端无关协议。后续可以映射到 Claude Code Stop hook 或独立 harness，但第一版不绑定具体客户端。

## 人格交互与切换

这是当前最值得继续强化的方向之一。

建议把导师交互分成三层：

- `integrated`
  - 默认模式，一个统一导师声音，内部运行三导师协同
- `lens-switch`
  - 显式更偏某位导师，例如更强调问题洁净度或执行路径
- `panel/debate`
  - 三位导师并行短评，再输出综合判断

具体建议见：

- [docs/persona-interaction-and-switching.md](./docs/persona-interaction-and-switching.md)

## 安装

将 skill 目录复制到你的本地 skills 路径：

```bash
cp -R skills/academic-mentor ~/.codex/skills/
cp -R skills/academic-research-copilot ~/.codex/skills/
```

如果你使用的是其他 agent 框架，只要它支持技能目录加载，也可以直接指向 `skills/academic-mentor/` 和 `skills/academic-research-copilot/`。

## 仓库结构

```text
academic-mentor-skill-repo/
├── README.md
├── README_EN.md
├── .gitignore
├── docs/
│   ├── skill-review-and-architecture.md
│   ├── source-distillation-and-testing.md
│   ├── persona-interaction-and-switching.md
│   └── adversarial-completion-loop.md
├── examples/
│   └── mode-switch-prompts.md
├── tests/
│   └── academic-persona-eval.md
└── skills/
    ├── academic-mentor/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── advisor-persona.md
            ├── advisor-expression-rules.md
            ├── mentor-council.md
            ├── source-grounding.md
            ├── fei-fei-li-source-pack.md
            ├── kaiming-he-source-pack.md
            ├── li-mu-source-pack.md
            ├── proposal-review-rubric.md
            ├── research-direction-triage.md
            ├── paper-guidance-rubric.md
            ├── defense-prep-rubric.md
            ├── milestone-review-rubric.md
            ├── adversarial-completion-loop.md
            ├── goal-contract-schema.md
            ├── completion-gate-rubric.md
            ├── loop-trace-schema.md
            ├── phd-scenario-optimization.md
            ├── student-feedback-learning.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
    └── academic-research-copilot/
        ├── SKILL.md
        ├── agents/
        │   └── openai.yaml
        └── references/
            ├── copilot-orchestration.md
            ├── adversarial-completion-loop.md
            ├── goal-contract-schema.md
            ├── completion-gate-rubric.md
            ├── loop-trace-schema.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

当前 research 证据层还包含视频蒸馏资料：

- `references/research/video-source-map.md`
- `references/research/fei-fei-li-video-card.md`
- `references/research/kaiming-he-video-card.md`
- `references/research/li-mu-video-card.md`

并新增论文表达蒸馏资料：

- `references/paper-first-distillation.md`
- `references/research/fei-fei-li-paper-dna.md`
- `references/research/kaiming-he-paper-dna.md`
- `references/research/li-mu-paper-dna.md`
- `references/research/fei-fei-li-paper-profile-card.md`
- `references/research/kaiming-he-paper-profile-card.md`
- `references/research/li-mu-paper-profile-card.md`
- `references/research/fei-fei-li-representative-paper-anchors.md`
- `references/research/kaiming-he-representative-paper-anchors.md`
- `references/research/li-mu-representative-paper-anchors.md`

## 推送到 GitHub

当前仓库已经本地初始化。检查并提交当前改动后，添加 remote 并 push：

```bash
git status
git add README.md README_EN.md docs examples tests skills
git commit -m "Add adversarial academic mentor-copilot skills"
git remote add origin <your-repo-url>
git push -u origin main
```

## 当前建议

如果下一步继续增强这个仓库，优先级建议是：

1. 继续按论文、项目页、公开视频、访谈扩充三位导师源包
2. 优先用论文表达而不是访谈口吻来强化三位导师的判断规则
3. 验证“统一导师表层 + 三导师协同 + 反馈调权”是否稳定成立
4. 用仓库内测试集检查多导师差异性和综合输出质量
5. 在协议稳定后，再增加客户端级 Stop hook adapter 或独立 loop harness
