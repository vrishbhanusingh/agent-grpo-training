# Reflexion: Language Agents with Verbal Reinforcement Learning (NeurIPS 2023)

## Paper Link
https://arxiv.org/abs/2303.11366

## Problem Statement
Reflexion addresses the challenge of enabling LLM-based agents to learn from their own mistakes and successes in a manner similar to human self-improvement. The goal is to move beyond static prompting or simple RL fine-tuning, allowing agents to iteratively improve through self-reflection and natural language feedback.

## Methodology
- **Verbal Reinforcement Learning:** Agents receive feedback in natural language (not just scalar rewards), which they use to update their reasoning and future actions.
- **Reflection Mechanism:** After each attempt at a task, the agent generates a reflection (in natural language) about what went wrong or right, and how to improve.
- **Iterative Improvement:** The agent can retry tasks, using its own reflections to guide subsequent attempts, leading to improved task performance over time.
- **Feedback Loop:** The agent's process is: (1) attempt task, (2) receive feedback, (3) reflect, (4) retry with improved strategy.

## Architecture Visualization
```mermaid
flowchart TD
    subgraph Reflexion_Agent_Workflow
        direction TB
        Input[Task/Input]
        Attempt[Agent Generates Solution]
        Feedback[Receive Feedback (Verbal/Scalar)]
        Reflection[Agent Reflects on Attempt]
        Retry[Agent Retries Task]
        Output[Final Output]
    end
    Input --> Attempt --> Feedback --> Reflection --> Retry
    Retry -->|If not solved| Attempt
    Retry -->|If solved| Output
```

## Technical Details
- **Agent:** LLM (e.g., GPT-3) with the ability to generate both solutions and self-reflections.
- **Feedback:** Can be provided by humans, automated critics, or the environment (in natural language).
- **Reflection Prompting:** The agent is prompted to analyze its own output and propose improvements.
- **Benchmarks:** Evaluated on text-based games (e.g., ALFWorld) and code generation tasks (e.g., HumanEval).
- **Performance:** Reflexion outperforms standard prompting and some RL fine-tuning baselines, especially in tasks requiring reasoning and iterative improvement.

## Strengths
- Mimics human-like learning via self-reflection and feedback.
- Flexible: can use both scalar and natural language feedback.
- Demonstrates strong improvements in complex, multi-step tasks.

## Weaknesses / Limitations
- Requires high-quality feedback (human or advanced automated critics).
- Computationally intensive due to multiple iterations per task.
- Reflection quality depends on the LLM's ability to self-critique.

## Relevance to Agentic Workflow Project
- The reflection and feedback loop aligns with your GRPO training and reward-based improvement for LLM agents.
- The use of natural language feedback could be integrated into your scoring agent, allowing richer reward signals than scalar scores.
- Iterative, self-improving agents fit well with your decoupled trainer and adapter management design.

## References
- Reflexion: Language Agents with Verbal Reinforcement Learning. NeurIPS 2023. https://arxiv.org/abs/2303.11366
