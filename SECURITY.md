# Security Policy

The **frontier-agent-prompts** project takes the security, privacy, and integrity of prompt engineering, model guardrails, and autonomous agent systems seriously. As an open-source research and engineering repository documenting frontier AI system instructions, we adhere to strict standards regarding privacy redaction, defensive safety, and responsible vulnerability disclosure.

---

## 🛡️ Supported Versions

We actively maintain and provide security updates for the current default branch (`main`).

| Branch / Release | Supported          | Security Scope |
| :--- | :--- | :--- |
| `main` | :white_check_mark: | Full active maintenance & CVE/vulnerability disclosures |
| Historical Tags | :x: | Archived releases |

---

## 🔒 Confidentiality & PII Redaction Policy

Our repository curates reverse-engineered, official, and academic system prompts from frontier AI models. To safeguard public and enterprise safety:

1. **Zero Secret Leakage**:
   - **Never** include real API tokens (OpenAI, Anthropic, GitHub, AWS, etc.).
   - **Never** expose internal IP addresses, non-public intranet URLs, private staging domains, or internal network endpoints.
   - **Never** disclose developer passwords, session cookies, database credentials, or private access tokens.
2. **PII Masking**:
   - All real names, personal paths (e.g., `/Users/username/`), private emails, and sensitive user metadata extracted from prompt telemetry must be masked with standardized synthetic placeholders (e.g., `{{WORKSPACE_DIRECTORY}}`, `{{API_KEY}}`, `/Users/Developer/workspace/`).

---

## 🚨 Reporting a Vulnerability or Sensitive Data Leak

If you discover:
- An unmasked private key, API token, internal domain, or credential in any file.
- A critical jailbreak vector or prompt injection payload that poses severe real-world harm.
- An accidental copyright or privacy violation.

**Please DO NOT open a public GitHub Issue.** Instead, please report it privately:

1. **GitHub Private Vulnerability Reporting**:
   - Navigate to the **Security** tab of this repository: `https://github.com/donsk08/frontier-agent-prompts/security/advisories`.
   - Click **Report a vulnerability** to open an encrypted advisory draft.
2. **Direct Security Contact**:
   - Contact the maintainer directly via GitHub profile: [@donsk08](https://github.com/donsk08).

### Information to Include in Your Report
- The file path and exact line numbers where the issue exists.
- The nature of the sensitivity (e.g., accidental token commit, private infrastructure reference).
- Recommended remediation steps.

---

## ⏱️ Response & Remediation SLA

- **Initial Triage**: Within **24 hours** of receipt.
- **Verification & Git History Purge**: Within **48 hours** (including purging commits via `git-filter-repo` if any sensitive token is verified).
- **Public Disclosure / Advisory Release**: Coordinated with the reporting researcher after remediation is merged.

---

## ⚖️ Academic & Defensive AI Safety Research Disclaimer

All artifacts, prompt instructions, and architecture patterns contained in this repository are published strictly for defensive engineering, prompt evaluation benchmarking, alignment research, and educational purposes under Fair Use principles. Maintainers do not endorse unauthorized bypass of third-party terms of service.
