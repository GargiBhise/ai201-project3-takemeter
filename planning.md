# Milestone 1: Community and Label Taxonomy

## Chosen Community

I will study English-language football discussion on **r/soccer**. The community contains active discussion about matches, players, managers, tactics, statistics, transfers, and football history.

My dataset will use public comments from several thread types, including post-match discussions, player and manager quotes, statistics posts, historical posts, and tactical discussions. I chose this community because Seattle is a host city for the 2026 FIFA World Cup, making football discussion timely and personally relevant.

---

## Label Taxonomy

Each comment will receive exactly one of the following labels:

* `analysis`
* `hot_take`
* `reaction`
* `observation`

The label will be based on the comment's primary purpose.

---

## 1. Analysis

### Definition

A comment that makes a structured football argument supported by specific evidence, such as statistics, tactical reasoning, concrete examples, or historical comparisons.

### Clear Example 1

> Among 76 players at this World Cup who have attempted 100 or more passes, he has the fewest inaccurate passes, with only three, showing how reliable he has been in possession.

This is `analysis` because it uses a specific and verifiable statistic to support an evaluation of the player's passing.

### Clear Example 2

> When he plays as a six, he focuses on retaining possession and passing into space so another midfielder can progress the ball.

This is `analysis` because it explains the player's tactical role and how his passing contributes to the team's progression.

### Uncertain Example

> He scored more than anyone else during his first six months at Real Madrid. The pressure did not seem to affect him.

This could be `analysis` because it uses historical context, or `observation` because it mainly reports what happened.

### Decision

I will label it `analysis` only when the historical comparison is used to support a clear conclusion or explanation. If the comment simply reports the comparison without developing an argument, I will label it `observation`.

---

## 2. Hot Take

### Definition

A bold, confident football opinion stated without meaningful supporting evidence. The comment asserts a conclusion rather than arguing for it.

### Clear Example 1

> If Celje played against Frankfurt, they could keep up.

This is a `hot_take` because it makes a confident comparison without supporting evidence or reasoning.

### Clear Example 2

> The stars are not going to determine this World Cup.

This is a `hot_take` because it makes a strong prediction without explaining why.

### Uncertain Example

> De Jong is one of the most misunderstood midfielders because people only look at goals and assists.

This could be `hot_take` because it is a broad, confident claim, or `analysis` because it offers an explanation.

### Decision

I will label it `hot_take` unless the comment provides specific examples, statistics, tactical mechanisms, or a meaningful comparison that supports the conclusion. A vague explanation will not be enough to count as analysis.

---

## 3. Reaction

### Definition

An immediate emotional or humorous response to a specific football event or statement. The comment mainly expresses a feeling rather than making an argument.

### Clear Example 1

> My word, we are awful. I genuinely find us painful to watch.

This is a `reaction` because it expresses frustration about a team's performance without supporting analysis.

### Clear Example 2

> I'm still annoyed that we did not get to see Brazil play Argentina in the 2022 semifinal.

This is a `reaction` because it expresses disappointment about a specific tournament outcome.

### Uncertain Example

> Easy to make fun of him because of his mistakes, but he is about the same age as Lamine. Pretty impressive.

This could be `reaction` because it expresses admiration, or `observation` because it includes a factual age comparison.

### Decision

I will label it `observation` when the factual comparison is the main point. I will use `reaction` when the comment's main purpose is expressing admiration, frustration, surprise, humor, or another emotion.

---

## 4. Observation

### Definition

A neutral or lightly evaluative comment that reports a fact, identifies a visible pattern, or makes a straightforward comparison without explaining why it happened.

### Clear Example 1

> Sweden's matches alone have produced ten goals already.

This is an `observation` because it reports a factual pattern without explanation or emotional language.

### Clear Example 2

> He is one of the youngest regular starting center-backs at the tournament.

This is an `observation` because it makes a factual comparison without explaining its cause or significance.

### Uncertain Example

> He is a starter for Barcelona and Spain and sometimes makes mistakes because of the way Barcelona plays.

This could be `observation` because it states facts about the player, or `analysis` because it links his mistakes to the team's style.

### Decision

I will label it `analysis` when the cause-and-effect explanation is meaningful and developed. I will label it `observation` when the comment mainly lists facts or makes a basic comparison.

---

## Mutual-Exclusivity Rules

Each included comment will receive one label based on its primary communicative purpose.

I will use the following order:

1. If the comment explains **why or how** something happened using specific evidence or reasoning, label it `analysis`.
2. If it makes a strong opinion or prediction without meaningful support, label it `hot_take`.
3. If its main purpose is emotional expression, humor, celebration, surprise, frustration, or disappointment, label it `reaction`.
4. If it neutrally reports a fact, pattern, event, or comparison without explanation, label it `observation`.

Bot messages, moderator notices, deleted comments, duplicate comments, spam, and replies that cannot be understood without missing context will be excluded rather than forced into a label.

---

## Hardest Edge Cases

The hardest boundary will be between `analysis` and `hot_take`.

For example:

> De Jong is one of the most misunderstood midfielders because people only look at goals and assists.

The comment contains both a bold judgment and a possible explanation. However, the explanation is broad and unsupported.

### Decision Rule

A comment will be labeled `analysis` only when it provides specific evidence, concrete examples, statistics, tactical reasoning, historical comparison, or a meaningful cause-and-effect explanation that genuinely supports its conclusion.

A confident claim followed by a vague, speculative, decorative, or weak explanation will remain a `hot_take`.

---

A second difficult boundary is between `analysis` and `observation`.

A comment that only states what happened or identifies a pattern will be labeled `observation`. A comment that explains why it happened, how it works, or what effect it creates will be labeled `analysis`.

---

A third boundary is between `reaction` and `hot_take`. Both can be unsupported opinions.

For example:

> We were utter pish tonight. Steve Clarke had no idea what he was doing.

The first sentence is a `reaction` triggered by a specific match. The second is a `hot_take` — a general judgment about the manager that extends beyond the immediate moment.

### Decision Rule

A comment will be labeled `reaction` when it is triggered by a **specific event** and expresses a feeling in the moment. It will be labeled `hot_take` when it makes a **general claim** about football, a player, or a manager that could apply beyond the immediate moment. When a comment contains both, the label will reflect its primary purpose. If neither purpose clearly dominates and the comment cannot be assigned without forcing it, it will be excluded from the dataset.

---

## Brief Project Description

I will study English-language football discussion on **r/soccer**, using public comments from post-match threads, player and manager quotes, statistics posts, and tactical discussions. I will classify comments as `analysis`, `hot_take`, `reaction`, or `observation` based on whether they provide structured reasoning, make unsupported claims, express immediate emotion, or describe facts and patterns. These distinctions matter because r/soccer contains a wide range of discourse quality, and the labels help separate evidence-based football discussion from speculation, emotional responses, and neutral reporting.