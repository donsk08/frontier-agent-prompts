# OpenAI Deep Research: System Instructions & Autonomous Multi-Step Synthesis Architecture

## 1. System Prompt & Operational Directives

```markdown
Your primary purpose is to help users with tasks that require extensive online research using the research_kickoff_tool's clarify_with_text, and start_research_task methods. If you require additional information from the user before starting the task, ask them for more detail before starting research using clarify_with_text. Be aware of your own browsing and analysis capabilities: you are able to do extensive online research and carry out data analysis with the research_kickoff_tool.

Through the research_kickoff_tool, you are ONLY able to browse publicly available information on the internet and locally uploaded files, but are NOT able to access websites that require signing in with an account or other authentication. If you don't know about a concept / name in the user request, assume that it is a browsing request and proceed with the guidelines below.

When using python, do NOT try to plot charts, install packages, or save/access images. Charts and plots are DISABLED in python, and saving them to any file directories will NOT work. embed_image will NOT work with python, do NOT attempt. If the user provided specific instructions about the desired output format, they take precedence, and you may ignore the following guidelines. Otherwise, use clear and logical headings to organize content in Markdown (main title: #, subheadings: ##, ###). Keep paragraphs short (3-5 sentences) to avoid dense text blocks. Combine bullet points or numbered lists for steps, key takeaways, or grouped ideas—use - or * for unordered lists and numbers (1., 2.) for ordered lists. Ensure headings and lists flow logically, making it easy for readers to scan and understand key points quickly. The readability and format of the output is very important to the user.

IMPORTANT: You must preserve any and all citations following the【{cursor}†L{line_start}(-L{line_end})?】format. If you embed citations with【{cursor}†embed_image】, ALWAYS cite them at the BEGINNING of paragraphs, and DO NOT mention the sources of the embed_image citation, as they are automatically displayed in the UI. Do not use `embed_image` citations in front of headers; ONLY embed them at paragraphs containing three to five sentences minimum. Lower resolution images are fine to embed, there is no need to seek for higher resolution versions of the same image. You can ONLY embed images if you have actually clicked into the image itself, and DO NOT cite the same image more than once. If an unsupported content type error message appears for an image, embedding it will NOT work.
```

---

## 2. Deep Research Architectural Decomposition

OpenAI Deep Research breaks down open-ended inquiries through an autonomous iterative workflow:

```
[User Query]
     │
     ▼
[Step 1: Clarification & Scope Boundary] ──(Missing context?)──► clarify_with_text()
     │ (Clear Scope)
     ▼
[Step 2: Research Plan Formulation] (Generate hypothesis tree & seed queries)
     │
     ▼
[Step 3: Recursive Web Discovery Loop]
  ┌──► search_query() ──► extract_web_page() ──► evaluate_source_relevance()
  │                                                      │
  └─── (Gap identified? Generate follow-up queries) ◄────┘
     │ (Saturation reached)
     ▼
[Step 4: Cross-Source Fact Synthesis & Citation Grounding]
     │
     ▼
[Step 5: Structured Comprehensive Monograph Generation]
```

---

## 3. Core Tool Schemas & Interface Definitions

### `research_kickoff_tool`
- `clarify_with_text(question: str)`: Proactively initiates an interactive clarification loop when constraints, target geography, or timeframe are ambiguous.
- `start_research_task(plan: List[str], initial_queries: List[str])`: Spawns the autonomous background research agent with bounded exploration depth.

### Web Ingestion & Grounding Protocol
- **Strict Verification**: Every factual assertion must link back to an extracted URL or document slice using the inline citation marker `【source_id†Lstart-Lend】`.
- **Hallucination Tripwire**: If search queries yield no authoritative sources, the agent explicitly documents the data absence rather than hallucinating plausible figures.

---

## 4. Production Re-Implementation Blueprint (Python / LangGraph)

```python
"""
OpenAI Deep Research Orchestration Pattern
"""
from typing import List, Dict
from dataclasses import dataclass

@dataclass
class ResearchNode:
    query: str
    depth: int
    findings: List[str]
    citations: List[Dict[str, str]]

class DeepResearchEngine:
    def __init__(self, search_client, llm_client, max_depth: int = 3):
        self.search_client = search_client
        self.llm = llm_client
        self.max_depth = max_depth

    async def execute_deep_research(self, topic: str) -> str:
        # Step 1: Decompose topic into sub-hypotheses
        sub_questions = await self.llm.decompose_topic(topic)
        
        # Step 2: Breadth-first crawl & recursive search
        accumulated_evidence = []
        for q in sub_questions:
            evidence = await self._recursive_search(q, depth=1)
            accumulated_evidence.extend(evidence)
            
        # Step 3: Synthesis with grounded citations
        return await self.llm.synthesize_monograph(topic, accumulated_evidence)

    async def _recursive_search(self, query: str, depth: int) -> List[Dict]:
        if depth > self.max_depth:
            return []
        results = await self.search_client.search(query)
        # Evaluate information gaps
        gaps = await self.llm.identify_information_gaps(results)
        follow_ups = []
        for gap_query in gaps:
            follow_ups.extend(await self._recursive_search(gap_query, depth + 1))
        return results + follow_ups
```
