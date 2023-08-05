# Usability Evaluation

## User-Task Analysis
- generate list of detailed task descriptions, sequences, realtionships, user work information flow
- start with protopying (ie.: with another person and on paper)

### Evaluation Approaches
|                       | Phases and Strategies        | Methods               |
| --------------------- | ---------------------------- | --------------------- |
| Before Development    | Expert Reviews               | Cognitive Walkthrough |
|                       | User Surveys                 | Heuristic Evaluation  |
| → What is needed?     |                              |                       |
|                       |                              |                       |
| During Development    | Usability Testing            | Formative Evaluation  |
|                       | User Surveys                 | Questionnaires        |
|                       |                              | Interviews and Demos  |
| → How is it working?  |                              |                       |
|                       |                              |                       |
| After Development     | Acceptance Test              | Questionnaires        |
|                       | Evaluation during active Use | Interviews and Demos  |
|                       | User Surveys                 |                       |
| → General Acceptance? |                              |                       |


#### NASA-TLX (Task Load Index)
- subjective workload assessment tool
- mental / cognitive / physical load of achieving task with your system
- score based on weighted average of demands, performance and frustration

#### SUS (System Usability Scale)
Subjective determination of usability:
1. Effectiveness (users can achieve their goals)
2. Efficiency (little effort is required for this achievement)
3. Satisfaction (experience was satisfactory)

#### Evaluation Metrics
1. System Perfomance Metrics (FPS, Network Delay, Latency, Distortion → In System)
2. Task Performance Metrics (Accuracy, Time to achieve tasks, Speed of learning → in System/Interview)
3. User Preference Metrics (Perceived eas of use, ease of learning, satisfaction → In Interview)

## Usability Testing
- Usability is the measure of quality of the user experience
- Usefullness is the measure of perceived "practicality" or potential of an application

→ Test different Alternatives in Test Groups for comparison

## Statistical Tools and Analysis

### How to show data is different
0. Null-Hypothesis $H_0$ → there is only one distribution and ours is not any different ($H_1 = H_0$)
1. Prove $H_1$ by showing that it is unlikely that they are the same

Example: Proof that a new interaction technique is faster
 0. Gather statistical Data on previous interaction technique $T_0$
 1. Gather statistical Data on new technique $T_1$
 2. Comparing the Data Sets suggests $T_1$ is faster 
 3. Proof by showing that it is more likely for $T_1 \neq T_0$ then $T_1 = T_0$ to be true

#### $\alpha$ and p -value
- $\alpha$-Value: picked manually → probability of having a false-positive rejection of $H_0$
- p-Value: calculate → probability that your results are significant under $H_0$ 
- if $p>\alpha$ reject $H_0$ 

#### Type I and Type II Errors
- Type I ($\alpha \ Error$): false-positive → results show true but it actually is false
- Type II ($\beta \ Error$): false-negative → results show false but it is actually true