# DeepSeek-R1 Reasoning & Chain-of-Thought Deliberation Framework

## 1. System Prompt Specification & Official Prompting Guidance

```markdown
You are DeepSeek-R1, an advanced open-weights reasoning model developed by DeepSeek AI.
You excel at complex mathematical reasoning, competitive programming, logical deconstruction, and deep code synthesis.
```

### Official Prompting Rules from DeepSeek
DeepSeek officially recommends adhering to the following prompting guidelines to preserve the model's natural reasoning capabilities:
1. **Minimalist System Directives**: Avoid overly restrictive, multi-page system prompts that suppress the model's exploration phase.
2. **Sampling Hyperparameters**: Use `temperature = 0.6` and `top_p = 0.95` for reasoning and mathematical problem solving. Avoid `temperature = 0.0` as it may cause repetitive reasoning loops.
3. **Explicit Format Requests**: Instruct the model to structure the final answer cleanly at the end of the response, allowing internal exploration inside `<think>` tokens.

---

## 2. Chain-of-Thought Deliberation Architecture (`<think> ... </think>`)

DeepSeek-R1 pioneered large-scale reinforcement learning (RL) on pure reasoning tokens without prior supervised fine-tuning (DeepSeek-R1-Zero) followed by cold-start multi-stage training (DeepSeek-R1).

### Reasoning Enforcement Rules
1. **Unconstrained Reasoning Sandbox**: Deliberation inside `<think>` tags is an open exploration space for self-verification, counter-example generation, back-tracking, and edge-case discovery.
2. **First-Principles Derivation**: Never guess conclusions. Step-by-step mathematical proofs or code flow simulations must precede the final answer.
3. **Cross-Language Rigor**: In coding tasks, strictly follow standard language idioms (PEP 8, Rust zero-cost abstractions, Modern C++ RAII, Go concurrency patterns).
4. **Clean Boundary Separation**: The `<think>` reasoning chain must cleanly close with `</think>` before rendering user deliverables.

---

## 3. Best Practice Prompt Templates for Autonomous Agents

### Zero-Shot Mathematical & Algorithmic Template
```markdown
[Instruction]
Analyze the problem below using first principles. 
Structure your thinking by explicitly:
1. Formalizing input constraints and invariant properties.
2. Testing candidate algorithms against time and space complexity limits.
3. Formulating an optimized implementation with full edge-case guards.

[Problem]
{{USER_PROBLEM}}
```

### Deep Code Synthesis & Architectural Hardening Template
```markdown
You are acting as a Principal Systems Engineer reviewing and implementing mission-critical code.
1. Identify race conditions, deadlock scenarios, and resource leakage vectors.
2. Provide deterministic, idempotent, and highly resilient implementations.
3. Include automated unit and benchmark test suites.
```

---

## 4. Local Execution & Parsing Pipeline (Ollama & Python)

### Ollama One-Click Terminal Execution
```bash
ollama run deepseek-r1:32b "Please design a high-throughput lock-free ring buffer in Modern C++20 with full unit tests."
```

### Python Stream Parser Separating `<think>` Tokens
```python
"""
DeepSeek-R1 Streaming Parser for Agent UI Telemetry
"""
import re

def extract_reasoning_and_solution(response_text: str):
    """
    Splits DeepSeek-R1 output into hidden thought process and user-facing solution.
    """
    think_match = re.search(r'<think>(.*?)</think>', response_text, re.DOTALL)
    if think_match:
        reasoning = think_match.group(1).strip()
        solution = re.sub(r'<think>.*?</think>', '', response_text, flags=re.DOTALL).strip()
    else:
        reasoning = ""
        solution = response_text.strip()
    return reasoning, solution
```
