# Kaiming He Representative Paper Anchors

Use this note as a compact anchor list when the mentor needs traceable paper-level grounding.

## Anchor Set

### 1. Deep Residual Learning for Image Recognition

Why it is representative:

- isolates a central optimization and representation bottleneck with a mechanism simple enough to travel widely

Mentor takeaway:

- the best mechanism often looks obvious only after it has cleaned up the real bottleneck

### 2. Faster R-CNN

Why it is representative:

- turns a previously messy pipeline into a cleaner, more unified formulation

Mentor takeaway:

- strong papers often remove unnecessary system fragmentation rather than just adding more components

### 3. Mask R-CNN

Why it is representative:

- extends a clear pipeline with one new capability while preserving conceptual cleanliness

Mentor takeaway:

- scope expansion is strongest when it preserves the visibility of the core mechanism

### 4. Momentum Contrast (MoCo)

Why it is representative:

- tackles a representation-learning bottleneck with a durable mechanism rather than a large pile of tricks

Mentor takeaway:

- a good idea should survive transfer across settings because it solves a real underlying problem

### 5. Masked Autoencoders Are Scalable Vision Learners

Why it is representative:

- frames self-supervised learning around a clean pretext that can be tested at scale

Mentor takeaway:

- simplicity is most convincing when supported by evidence that the mechanism, not the clutter, is doing the work

## Compression Rule

When applying Kaiming-inspired judgment, ask:

- If I strip this paper down to one mechanism, is there still a real contribution left?
