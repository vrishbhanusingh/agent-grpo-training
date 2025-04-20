# STARLING: Self-supervised Training of Text-based Reinforcement Learning Agent with Large Language Models (arXiv 2024)

## Paper Link
https://arxiv.org/abs/2406.00000

## Problem Statement
STARLING tackles the challenge of training LLM-based agents for text-based RL tasks without requiring large amounts of human-annotated data. The goal is to leverage self-supervised learning and LLMs' language understanding to enable agents to learn effective policies in interactive, text-based environments.

## Methodology
- **Self-Supervised RL:** The agent learns from its own interactions with the environment, using intrinsic objectives and self-generated feedback.
- **LLM Policy:** The agent's policy is parameterized by a large language model, which generates actions based on the current state and history.
- **Trajectory Optimization:** The agent refines its policy by optimizing over trajectories (sequences of actions and observations), using self-consistency and reward signals.
- **Iterative Improvement:** The agent iteratively improves its policy through repeated environment interaction and self-supervised updates.

## Architecture Visualization
```mermaid
flowchart TD
    subgraph STARLING_Agent_Workflow
        direction TB
        State[Current State]
        LLMPolicy[LLM Policy Generates Action]
        EnvStep[Environment Step]
        Reward[Self/Env Reward]
        Update[Policy Update (Self-Supervised)]
        Loop[Iterate]
        Output[Learned Policy]
    end
    State --> LLMPolicy --> EnvStep --> Reward --> Update --> Loop
    Loop -->|Continue| State
    Loop -->|Converged| Output
```

## Technical Details
- **Agent:** LLM (e.g., GPT-3/4) as the policy network for RL.
- **Self-Supervision:** Uses objectives like self-consistency, imitation of successful trajectories, and intrinsic motivation.
- **Benchmarks:** Evaluated on text-based games and interactive fiction environments.
- **Performance:** Achieves strong results without human-labeled data, outperforming some supervised and RL baselines.

## Strengths
- Reduces reliance on expensive human annotation.
- Leverages LLMs' language understanding for efficient policy learning.
- Demonstrates strong performance in text-based RL tasks.

## Weaknesses / Limitations
- May require significant compute for large-scale self-supervised training.
- Effectiveness depends on the quality of intrinsic objectives and environment diversity.

## Relevance to Agentic Workflow Project
- Self-supervised RL can be used to bootstrap agent policies before introducing human or automated feedback.
- The iterative, trajectory-based optimization aligns with your GRPO and reward-driven training design.
- LLM-based policy networks are directly relevant to your agent architecture.

## References
- STARLING: Self-supervised Training of Text-based Reinforcement Learning Agent with Large Language Models. arXiv 2024. https://arxiv.org/abs/2406.00000
