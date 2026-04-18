# Academic Mentor Skill Repo

中文 | [English](./README_EN.md)

一个面向学术场景的 `academic-mentor` skill 仓库。它不是通用陪聊人格，而是一个严格的博士导师型判断 skill，用来处理研究方向筛选、开题把关、论文逻辑审查、答辩准备和阶段性研究决策。

## 仓库目标

这个仓库解决三件事：

1. 把 `academic-mentor` 封装成可直接安装、可直接推送 GitHub 的独立 skill 仓库
2. 把导师人格从“模仿名人说话”收束到“基于公开来源提炼研究判断规则”
3. 将其升级为“统一导师表层 + 三导师内部协同 + 反馈调权学习”的导师系统

## 仓库内容

- 可安装 skill：
  - `skills/academic-mentor/`
- 仓库级方法文档：
  - `docs/skill-review-and-architecture.md`
  - `docs/source-distillation-and-testing.md`
  - `docs/persona-interaction-and-switching.md`
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
```

如果你使用的是其他 agent 框架，只要它支持技能目录加载，也可以直接指向 `skills/academic-mentor/`。

## 仓库结构

```text
academic-mentor-skill-repo/
├── README.md
├── README_EN.md
├── .gitignore
├── docs/
│   ├── skill-review-and-architecture.md
│   ├── source-distillation-and-testing.md
│   └── persona-interaction-and-switching.md
├── examples/
│   └── mode-switch-prompts.md
├── tests/
│   └── academic-persona-eval.md
└── skills/
    └── academic-mentor/
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
            ├── phd-scenario-optimization.md
            ├── student-feedback-learning.md
            ├── shared-memory-schema.md
            └── shared-memory-operations.md
```

当前 research 证据层还包含视频蒸馏资料：

- `references/research/video-source-map.md`
- `references/research/fei-fei-li-video-card.md`
- `references/research/kaiming-he-video-card.md`
- `references/research/li-mu-video-card.md`

## 推送到 GitHub

当前仓库已经本地初始化并提交。后续只需要添加 remote 并 push：

```bash
git remote add origin <your-repo-url>
git push -u origin main
```

## 当前建议

如果下一步继续增强这个仓库，优先级建议是：

1. 继续按论文、项目页、公开视频、访谈扩充三位导师源包
2. 优先验证“统一导师表层 + 三导师协同 + 反馈调权”是否稳定成立
3. 用仓库内测试集检查多导师差异性和综合输出质量
4. 再考虑是否把 `academic-research-copilot` 作为兄弟 skill 一起封装
