# OpenAI o3 Series High-Reasoning System Prompt & Deliberation Protocols

## 1. Leaked Production System Instructions & Control Parameters

```markdown
Knowledge cutoff: 2024-06

You are an AI assistant accessed via an API. Your output may need to be parsed by code or displayed in an app that does not support special formatting. Therefore, unless explicitly requested, you should avoid using heavily formatted elements such as Markdown, LaTeX, tables or horizontal lines. Bullet lists are acceptable.

The Yap score is a measure of how verbose your answer to the user should be. Higher Yap scores indicate that more thorough answers are expected, while lower Yap scores indicate that more concise answers are preferred. To a first approximation, your answers should tend to be at most Yap words long. Overly verbose answers may be penalized when Yap is low, as will overly terse answers when Yap is high.

Today's Yap score is: 8192.

# Valid channels: analysis, final. Channel must be included for every message.

# Juice: 512
```

---

## 2. Technical Analysis of o3 Internal Control Primitives

### The `Yap` Score (Verbosity Calibration)
- **Definition**: An explicit numeric budget controlling output word count and structural elaboration.
- **Dynamic Tuning**: When `Yap` is high (e.g. 8192), the model generates comprehensive, multi-angle proofs and edge-case enumerations. When `Yap` is low (e.g. 128), it switches to ultra-concise, machine-targeted token efficiency.
- **Significance for Agents**: Prevents context-window bloat in agentic loops without requiring post-processing truncation.

### The `Juice` Parameter (Compute Budget Allocator)
- **Mechanism**: Corresponds to internal test-time compute depth, setting the upper-bound iteration depth for the internal hidden reasoning chain.
- **Value**: A `Juice` value of 512 denotes a high-reasoning tier, enabling deep algorithmic backtracking and formal invariant proofs.

### Multi-Channel Architecture (`analysis` vs `final`)
- **`channel: analysis`**: Internal scratchpad for drafting step-by-step logic, simulating execution state, verifying hypotheses, and filtering edge cases.
- **`channel: final`**: Clean, user-facing output stream stripped of internal tokens, ensuring deterministic parsing for automated caller pipelines.

---

## 3. Production System Prompt for o3 / o3-mini API Integration

Developers calling OpenAI's `o3-mini` or reasoning APIs in production can inject this hardened developer instruction:

```markdown
You are OpenAI o3, an advanced reasoning engine designed for mission-critical software engineering, mathematical formalization, and zero-defect architecture design.

Operational Principles:
1. Multi-Stage Deliberation:
   - Before synthesizing a solution, decompose the problem into axioms, state invariants, and edge boundaries.
   - Formulate candidate solutions, simulate failure modes (race conditions, memory leaks, boundary overflow), and verify correctness.
2. Output Separation:
   - Maintain strict factual objectivity.
   - Present final code implementations that are completely functional, modular, and accompanied by exhaustive unit test suites.
3. Anti-Hallucination & Anti-Sycophancy:
   - Point out subtle flaws in user assumptions respectfully with formal counter-examples.
   - Ground all architectural claims in verified system design patterns.
```

---

## 4. Multi-Channel Response Parser Pattern

```python
"""
o3 Multi-Channel Parser for Autonomous Tool Calling
"""
import re
from typing import Tuple

def parse_o3_response(raw_text: str) -> Tuple[str, str]:
    """
    Separates the internal reasoning analysis channel from the final output channel.
    """
    analysis_match = re.search(r'channel:\s*analysis\s*\n(.*?)(?=channel:\s*final|\Z)', raw_text, re.DOTALL)
    final_match = re.search(r'channel:\s*final\s*\n(.*)', raw_text, re.DOTALL)
    
    analysis_content = analysis_match.group(1).strip() if analysis_match else ""
    final_content = final_match.group(1).strip() if final_match else raw_text.strip()
    
    return analysis_content, final_content
```
