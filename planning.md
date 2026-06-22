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





# Milestone 2: Project Specification

## Community Fit

I chose r/soccer, an active English-language football community where users discuss matches, players, managers, tactics, statistics, transfers, and football history. It is a good fit for a classification task because the comments vary significantly in purpose and depth: some provide detailed tactical reasoning, some make unsupported predictions, some express immediate emotion, and others simply report facts or patterns.

The subreddit is highly active and contains many public, text-based discussions, making it practical to collect more than 200 comments from varied thread types without relying on private or restricted content. These differences are meaningful within the community because users regularly distinguish between informed football analysis, exaggerated claims, match-day reactions, and neutral observations.

## Labels

The project will use four labels:

* `analysis`: A structured football argument supported by specific evidence, tactical reasoning, concrete examples, statistics, or historical comparisons.
* `hot_take`: A bold and confident football opinion stated without meaningful supporting evidence.
* `reaction`: An immediate emotional or humorous response to a specific football event or statement.
* `observation`: A neutral or lightly evaluative comment that reports a fact, pattern, event, or comparison without explaining why it happened.

The full definitions, two examples per label, and uncertain examples are documented in the Milestone 1 section above.

## Hard Edge Cases

The most difficult distinction will be between `analysis` and `hot_take`. Some comments include a strong opinion followed by a brief explanation, but the explanation may be vague, speculative, or unsupported.

For example:

> De Jong is one of the most misunderstood midfielders because people only look at goals and assists.

This comment gives a possible reason, but it does not include specific evidence or developed reasoning.

### Difficult Annotation Decisions

**Case 1 — `analysis` vs `hot_take`**

> De Jong actually plays a lot of progressive passes though. If someone actually thinks he's not a good player, you should probably disregard their footballing input.

This could be `hot_take` because the conclusion is dismissive and unsupported, or `analysis` because progressive passing is cited as specific evidence. I labeled it `analysis` because the passing claim is a concrete, verifiable football observation that genuinely supports the conclusion.

**Case 2 — `observation` vs `reaction`**

> What's his passing like now? From my memory he was always pretty good at finding the right person but I haven't watched him in years. I have hope Mainoo would develop that side of his game a bit more.

This could be `reaction` because it expresses personal hope, or observation because it mainly describes a remembered passing trait and compares it with another player's development. I labeled it `observation` because the descriptive comparison is the main purpose, while the emotional element is secondary.

**Case 3 — `observation` vs `reaction`**

> Easy to make fun of because of his mistakes but he's about the same age as Lamine. Pretty impressive.

This could be `reaction` because it expresses admiration, or `observation` because the age comparison is the main point. I labeled it `observation` because the factual age comparison is what drives the comment, with admiration as a secondary response to that fact.

### Decision rule

A comment will be labeled `analysis` only when it includes specific statistics, tactical mechanisms, concrete examples, historical comparisons, or a meaningful cause-and-effect explanation that genuinely supports its conclusion. A confident claim followed only by a vague or decorative explanation will be labeled `hot_take`.

Another difficult distinction will be between `analysis` and `observation`. A comment that states what happened or identifies a pattern will be labeled `observation`. A comment that explains why it happened, how it works, or what effect it creates will be labeled `analysis`.

A third difficult distinction will be between `reaction` and `hot_take`. A comment will be labeled `reaction` when its main purpose is expressing emotion about a specific event. It will be labeled `hot_take` when it makes a broader unsupported judgment about a player, manager, team, or football issue.

## Data Collection Plan

I will collect public comments primarily from **r/soccer**. I will use several thread types so the dataset does not overrepresent one kind of football discussion:

* post-match threads;
* player and manager quote threads;
* tactical discussions;
* statistics posts;
* historical football discussions;
* a limited number of goal or highlight threads.

I will exclude bot messages, moderator notices, deleted or removed comments, duplicate comments, spam, comments containing only links, and replies that cannot be understood without missing context.

The final dataset will contain at least **200 labeled comments**. I will initially aim for approximately **50–60 examples per label**, producing a dataset of around **220–240 usable comments**.

My target distribution is:

| Label         | Target number |
| ------------- | ------------: |
| `analysis`    |         50–60 |
| `hot_take`    |         50–60 |
| `reaction`    |         50–60 |
| `observation` |         50–60 |

The dataset does not need to be perfectly balanced, but I will aim for each label to represent at least 20% of the final examples when possible. No label should account for more than 70% of the dataset.

If a label is underrepresented after the first 200 examples, I will collect additional comments from thread types likely to contain that label:

* For more `analysis`, I will use tactical, statistical, and detailed post-match discussions.
* For more `hot_take`, I will use prediction, player-rating, and manager-discussion threads.
* For more `reaction`, I will use post-match, goal, and major-event threads.
* For more `observation`, I will use statistics, historical, and match-summary discussions.

The final CSV will contain at least these columns:

* `text`
* `label`
* `notes`

The `notes` column will record difficult or borderline annotation decisions. The Colab notebook will divide the complete CSV into training, validation, and test sets using a 70% / 15% / 15% split.

## Evaluation Metrics

I will evaluate both the fine-tuned DistilBERT model and the zero-shot Groq baseline on the same test set.

### Overall accuracy

Accuracy will measure the percentage of test comments assigned the correct label. It provides a simple summary of overall model performance, but it is not sufficient by itself because a model could achieve reasonable accuracy by favoring common labels.

### Per-class precision

Precision will measure how often a predicted label is correct. This is important because the model may overuse labels such as `reaction` or `hot_take` for short or emotional comments.

For example, low precision for `analysis` would mean that many comments predicted as analysis do not actually contain sufficient reasoning or evidence.

### Per-class recall

Recall will measure how many true examples of each label the model successfully identifies. This will show whether the model systematically misses a class.

For example, low recall for `observation` may indicate that the model incorrectly treats neutral factual statements as analysis.

### Per-class F1 score

F1 combines precision and recall. It will be the most useful metric for comparing performance across the four labels because it penalizes both missed examples and excessive incorrect predictions.

I will also report **macro-average F1**, which gives equal importance to all four labels even if their counts are slightly different.

### Confusion matrix

A confusion matrix will show which label pairs the model confuses. This is especially important because I expect the most difficult boundaries to be:

* `analysis` versus `hot_take`;
* `analysis` versus `observation`;
* `reaction` versus `hot_take`.

The confusion matrix will help determine whether the model learned the intended discourse distinctions or relied on simpler signals such as comment length, emotional words, or the presence of numbers.

## Definition of Success

For this four-class task, random guessing would produce approximately 25% accuracy. A classifier would not be useful merely because it performs better than random.

I will consider the fine-tuned model **successful enough for this project** if it achieves:

* at least **70% overall test accuracy**;
* at least **0.65 macro F1**;
* an F1 score of at least **0.55 for every individual label**;
* better overall accuracy or macro F1 than the zero-shot Groq baseline.

I will consider the model **strong enough for limited real-world experimentation** if it achieves:

* at least **75% overall accuracy**;
* at least **0.70 macro F1**;
* no individual class with an F1 score below **0.60**.

These thresholds acknowledge that the task is subjective and that the dataset is relatively small. Even if the overall target is reached, I would not recommend fully automatic moderation or ranking without human review. A realistic community tool should present the predicted label and confidence as decision support rather than treating the model's output as an unquestionable judgment.

## AI Tool Plan

### Label stress-testing

I will give an AI tool my four label definitions and decision rules and ask it to generate 5–10 football comments that sit near difficult boundaries, especially:

* `analysis` versus `hot_take`;
* `analysis` versus `observation`;
* `reaction` versus `hot_take`.

I will classify each generated example myself. If several examples cannot be assigned consistently, I will revise the definitions or add a more precise decision rule before completing annotation.

### Annotation assistance

I may use an AI tool to pre-label some collected comments. Any AI-generated label will be treated only as a suggestion. I will personally read and approve or correct every example before including it in the final dataset.

I will use the `notes` column to identify examples that were difficult, corrected after AI pre-labeling, or required a special decision rule. I will disclose the use of AI-assisted pre-labeling in the README.

### Failure analysis

After evaluating the fine-tuned model, I will provide an AI tool with the misclassified examples, their correct labels, and the model's predictions. I will ask it to identify possible patterns such as:

* short comments being overclassified as reactions;
* numbers causing observations to be predicted as analysis;
* sarcasm being interpreted literally;
* unsupported opinions with explanations being confused with analysis;
* specific label pairs being confused repeatedly.

I will verify every suggested pattern by reviewing the actual examples and confusion matrix. I will only report patterns that are supported by multiple errors rather than accepting the AI tool's conclusions automatically.
