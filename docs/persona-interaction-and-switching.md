# Persona Interaction and Switching

This document focuses on what matters most for this repository next: multi-advisor interaction and switching for academic use.

The current direction should be understood as one unified mentor with an internal advisor council, not a surface-level multi-character system.

That said, "unified mentor" should not mean "flattened voice." A good academic mentor still needs recognizable communication style, question rhythm, and human conversational continuity.

## 1. Recommended Persona Modes

### Mode A: `integrated` (default)

Use one unified mentor voice.

This does not mean every answer should share the same visible format. `Integrated` means one continuous mentor identity, while sentence rhythm, opening shape, and criticism style may still move toward the dominant advisor.

Best for:

- everyday academic advising
- proposal review
- paper logic critique
- defense preparation

Strength:

- stable and easy to use
- preserves the feeling of one long-term mentor relationship
- allows the mentor to feel like one real person rather than a rotating prompt template

Risk:

- the internal lens balance is hidden, so the user cannot explicitly ask for one dominant viewpoint

### Mode B: `lens-switch`

Let the user explicitly emphasize one advisor:

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

The three advisors review the same problem, then synthesize a final answer.

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

## 1.5. Feedback-Based Reweighting

Across all three modes, student feedback should primarily adjust internal advisor weighting rather than the visible persona.

This means:

- the mentor can become more aligned over time
- the visible product still feels like one mentor
- repeated evidence can change emphasis without rewriting core standards

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
- keep one shared style discipline while preserving advisor-specific expression DNA
- preserve one final integrated conclusion even in `panel` mode
- keep feedback-learning in the weighting layer, not the theatrical layer

## 4. Recommended Next-Step Changes

If this repo continues evolving, the best next changes are:

1. keep `integrated / lens-switch / panel` explicit in `SKILL.md`
2. define advisor-specific signals and one synthesis layer
3. add examples for each mode
4. add tests checking that the same prompt yields different emphases under different modes without losing academic rigor
5. add feedback-learning checks to confirm that repeated student responses only change weighting gradually

## 5. My Recommendation

For an academic mentor skill, the best product balance is:

- keep `integrated` as default
- support `lens-switch` for controllable emphasis
- support `panel` only for high-stakes scenarios
- keep feedback-learning behind the scenes so the mentor feels more personal without turning into a performance system

This is a better fit for academic use than copying `nuwa-skill` too literally as a role-play engine. But the repo should still learn from `nuwa-skill` that language style matters. The target is not entertainment. The target is a mentor who feels human, recognizable, and academically useful at the same time.
