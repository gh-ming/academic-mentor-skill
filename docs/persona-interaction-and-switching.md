# Persona Interaction and Switching

This document focuses on what matters most for this repository next: multi-persona interaction and switching for academic use.

The current skill is good at integrated judgment. It is weaker at explicit mode control.

## 1. Recommended Persona Modes

### Mode A: `integrated` (default)

Use one unified mentor voice.

Best for:

- everyday academic advising
- proposal review
- paper logic critique
- defense preparation

Strength:

- stable and easy to use

Risk:

- the internal lens balance is hidden, so the user cannot explicitly ask for one dominant viewpoint

### Mode B: `lens-switch`

Let the user explicitly emphasize one lens:

- `vision`
- `problem`
- `execution`

Interpretation:

- `vision` ≈ Fei-Fei-weighted
- `problem` ≈ Kaiming-weighted
- `execution` ≈ Li Mu-weighted

Best for:

- "Just tell me if this problem is clean"
- "Focus on whether the story is thesis-worthy"
- "Break this into executable milestones"

Strength:

- gives the user finer academic control without turning the skill into role-play theater

### Mode C: `panel`

Multiple personas review the same problem, then synthesize a final answer.

Best for:

- very high-stakes proposal decisions
- pre-defense attack simulation
- paper strategy disagreements

Suggested structure:

1. `vision` opinion
2. `problem` opinion
3. `execution` opinion
4. final integrated judgment

Strength:

- exposes tradeoffs
- useful when the user wants to see disagreement instead of only the merged answer

Risk:

- more verbose
- easier to drift into performance instead of judgment

## 2. Academic-Scene Recommendations

### Proposal

Recommended default:

- `integrated`

Optional escalation:

- switch to `panel` when the user is unsure whether the proposed three-part structure really holds together

### Direction Choice

Recommended default:

- `problem`

Reason:

- direction decisions usually fail because the problem is weak or the scope is wrong, not because the writing is poor

### Paper Strategy

Recommended default:

- `integrated`

Optional escalation:

- `vision` when the story is the main issue
- `problem` when method-problem mismatch is the main issue

### Defense Preparation

Recommended default:

- `panel`

Reason:

- defense preparation benefits from explicit multi-angle pressure

### Milestone Review

Recommended default:

- `execution`

Reason:

- milestone reviews need clear next actions and realistic scope compression

## 3. How To Implement Without Ruining the Skill

Do not:

- turn each persona into theatrical dialogue
- overfit to named individuals
- make switching depend on mimicry

Do:

- map switching to academic judgment emphasis
- keep one shared style discipline
- preserve one final integrated conclusion even in `panel` mode

## 4. Recommended Next-Step Changes

If this repo continues evolving, the best next changes are:

1. add an explicit `mode` section to `SKILL.md`
2. define the three switchable lenses as supported interaction patterns
3. add 1-2 examples for each mode
4. add tests checking that the same prompt yields different emphases under different modes without losing academic rigor

## 5. My Recommendation

For an academic mentor skill, the best product balance is:

- keep `integrated` as default
- support `lens-switch` for controllable emphasis
- support `panel` only for high-stakes scenarios

This is a better fit for academic use than copying `nuwa-skill`'s personality-distillation pattern too literally, because your goal is not personality entertainment. Your goal is decision quality under different academic pressures.
