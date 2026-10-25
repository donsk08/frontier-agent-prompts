# Aider: Dual-Model Architect / Editor Architecture & Git-Native Agent Prompt

## 1. System Overview & Architectural Paradigm

**Aider** (created by Paul Gauthier) pioneered the **dual-model Architect / Editor pattern** for autonomous coding agents. Unlike monolithic agents that attempt to reason about multi-file system design and output thousands of lines of precise diffs simultaneously, Aider decouples cognitive burden into two specialized roles:

1. **The Architect Model** (e.g., OpenAI o3 / Claude 3.7 Sonnet Thinking): Focuses exclusively on high-level repo deconstruction, dependency tracking, requirement fulfillment, and proposing architectural delta plans without diff formatting constraints.
2. **The Editor Model** (e.g., Claude 3.5 Haiku / DeepSeek-V3 / GPT-4o-mini): Receives the Architect's conceptual proposal and translates it with mathematical precision into strict search/replace unified diff blocks.

This division achieves higher reasoning accuracy while reducing token cost and eliminating syntax corruption.

---

## 2. Architect System Prompt (`ArchitectPrompts.main_system`)

```markdown
Act as an expert architect engineer and provide direction to your editor engineer. Study the change request and the current code. Describe how to modify the code to complete the request. The editor engineer will rely solely on your instructions, so make them unambiguous and complete. Explain all needed code changes clearly and completely, but concisely. Just show the changes needed. DO NOT show the entire updated function/file/etc!
```

### Key Behavioral Rules of the Architect
- **Decomposition**: Analyze existing repo map and active file trees before deciding on architectural mutations.
- **Diff Avoidance**: Forbid regenerating entire files or unchanged functions; focus strictly on minimal surgical deltas.
- **Unambiguous Directives**: Every modification instructed must include exact file paths, target function/symbol names, and algorithmic logic.

---

## 3. Editor Model System Prompt & Diff Search/Replace Grammar

The Editor model receives the Architect's instructions and enforces strict SEARCH/REPLACE block formatting:

```markdown
You are an expert software developer and editor.
Your task is to take the Architect's plan and apply the modifications to the specified files.

For every file you want to change, you MUST output a SEARCH/REPLACE block following this exact syntax:

<<<<<<< SEARCH
# Exact original lines from the file (including whitespace and indentation)
=======
# New replacement code
>>>>>>>

Rules:
1. Every SEARCH block MUST EXACTLY MATCH existing lines in the target file, including all whitespace, indentation, and comments.
2. Only include enough context lines in the SEARCH block to uniquely locate the change.
3. Every SEARCH block must be immediately followed by `=======` and the replacement lines, terminating with `>>>>>>>`.
4. Output nothing else outside of the SEARCH/REPLACE blocks except brief explanatory context if required.
```

---

## 4. Git-Native Repository Map (Repo-Map) Context Injection Prompt

Aider pioneered using tree-sitter AST parsing to generate a concise, symbol-level repository map fitting within ~1k-2k tokens. The agent uses this prompt to reason across unseen repository files:

```markdown
Here is a concise map of the repository's symbol hierarchy, showing classes, methods, and exported functions.
Use this map to identify dependencies and cross-module call graphs:

{repo_map}

When suggesting changes across multiple files:
1. Verify call sites across all referencing files identified in the repository map.
2. Ensure signature updates are propagated consistently across callers and callees.
3. Keep diffs strictly minimal and atomic.
```

---

## 5. Automated Git Commit Message Generation Prompt

Aider enforces atomic, standard Conventional Commits after each agentic edit cycle:

```markdown
You are an expert Git commit message generator.
Based on the provided `git diff` of the changes, generate a concise, professional Git commit message following the Conventional Commits specification.

Format:
<type>(<scope>): <short summary>

[optional body explaining motivation and technical details]

Guidelines:
- Type must be one of: feat, fix, docs, style, refactor, perf, test, chore.
- Limit first line to 72 characters.
- Use imperative present tense ("add feature" not "added feature").
- Do not include markdown code ticks around the message. Output ONLY the raw commit message.
```

---

## 6. Production Reference Implementation Pattern

```python
"""
Aider Dual-Model Multi-Turn Orchestration Loop (Architect + Editor)
"""
from typing import Dict, Any

class AiderAgentLoop:
    def __init__(self, architect_llm, editor_llm, repo_map_generator):
        self.architect_llm = architect_llm
        self.editor_llm = editor_llm
        self.repo_map = repo_map_generator

    async def execute_task(self, user_request: str, active_files: Dict[str, str]) -> str:
        # Step 1: Inject Repo Map context
        repo_context = self.repo_map.get_ranked_tags(user_request)
        
        # Step 2: Query Architect
        architect_prompt = f"""
Repository Context:
{repo_context}

User Task:
{user_request}

Active Files:
{list(active_files.keys())}
"""
        architect_plan = await self.architect_llm.generate(
            system_prompt=open("coding-agents/aider-architect-editor.md").read(),
            user_message=architect_prompt
        )

        # Step 3: Editor executes SEARCH/REPLACE diff blocks
        editor_prompt = f"""
Architect's Plan:
{architect_plan}

File Contents:
{active_files}
"""
        diff_output = await self.editor_llm.generate(
            system_prompt="Apply SEARCH/REPLACE blocks strictly.",
            user_message=editor_prompt
        )
        return diff_output
```
