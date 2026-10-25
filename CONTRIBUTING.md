# Contributing to Frontier Agent Prompts

Thank you for your interest in contributing to **frontier-agent-prompts**! This project aims to be the world's most comprehensive, academically grounded, and production-tested repository of frontier AI system prompts, autonomous agent instructions, and architecture patterns.

---

## 🎯 Contribution Principles

1. **Authenticity & Integrity**: All submitted system prompts must be verified against real-world production systems, reverse-engineered binaries, official releases, or transparent research methodologies.
2. **Redaction of Sensitive Secrets**: 
   - **NEVER submit API keys, tokens, session IDs, private URLs, personal identifiable information (PII), or confidential enterprise credentials.**
   - All environment variables or tokens must be masked with placeholders (e.g., `{{API_KEY}}` or `<REDACTED>`).
3. **Structured Formatting**:
   - Every file must be formatted in clean, standard Markdown (`.md`).
   - Include version numbers, release dates, and model names at the top of the file.
4. **Educational & Research Focus**: Submissions should be framed to advance defensive AI safety, prompt robustness, anti-injection resilience, and system engineering.

---

## 🛠️ How to Submit a Pull Request

1. **Fork the Repository**:
   Click the "Fork" button at the top right of this repository.

2. **Clone your Fork**:
   ```bash
   git clone https://github.com/<your-username>/frontier-agent-prompts.git
   cd frontier-agent-prompts
   ```

3. **Create a Feature Branch**:
   ```bash
   git checkout -b feature/add-new-agent-prompt
   ```

4. **Add or Update Content**:
   - Place your prompt in the appropriate category folder (`claude/`, `openai/`, `coding-agents/`, `deepseek-open-source/`, `architecture-guides/`).
   - If introducing a new category, ensure it aligns with the taxonomy.
   - Update `README.md` to reflect the new entry in the quick navigation table.

5. **Commit and Push**:
   ```bash
   git add .
   git commit -m "feat: add <System Name> system prompt and guidelines"
   git push origin feature/add-new-agent-prompt
   ```

6. **Open a Pull Request**:
   Go to your fork on GitHub and submit a PR against the `main` branch. Describe the origin of the prompt, version information, and why it provides value to the community.

---

## 🧪 Markdown Quality Guidelines

- Use standard CommonMark syntax.
- Ensure all relative links within the repository resolve correctly.
- Do not introduce trailing whitespace or broken header tags.

Thank you for helping empower the global AI engineering community!
