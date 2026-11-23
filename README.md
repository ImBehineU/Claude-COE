# Universal Context Sanitizer (COE-CS v3.0)

A deterministic **Pre-LLM Privacy, DLP (Data Loss Prevention), and Classifier-Safe Prompt Sanitizer** built as a universal agent skill (`SKILL.md`).

It intercepts raw user prompts and rewrites them into self-contained, professional, copy-paste-ready inquiries before they are sent to any external LLM or coding agent (**Claude, Claude Code, OpenAI Codex, ChatGPT, Cursor, or Gemini**)—eliminating personal context leaks and preventing false-positive automated safety flags.

---

## Core Capabilities

* **Zero Identity & Residency Leakage:** Converts permanent home locations and local residency into neutral temporary transit framing (business travel, layovers, or short-term remote assignments).
* **Zero Age & Authority Leakage:** Strips references to parents, guardians, school filters, or age limits, normalizing requests into autonomous enterprise IT or group-coordination workflows.
* **Zero Financial & Subscription Leakage:** Replaces personal payment constraints with departmental procurement, group budget pooling, or open-source software evaluation framing.
* **Deterministic Secret & PII Redaction:** Masks API keys, bearer tokens, real IP addresses, internal domains, usernames, and local file paths with standardized placeholders (`<REDACTED_API_KEY>`, `203.0.113.10`, `example.com`).
* **Anti-Classifier Linguistic Hardening:** Replaces high-risk offensive security verbs (`bypass`, `crack`, `exploit`, `sniff`) and adversarial wrappers with standard RFC, architectural, and defensive engineering terminology so legitimate queries succeed on the first turn.

---

## Repository Structure

```text
universal-context-sanitizer/
├── SKILL.md      # Universal skill definition (YAML frontmatter + 7-Stage Pipeline)
└── README.md     # Documentation and installation guide
```

---

## Installation & Usage

### 1. Claude Code (Personal or Project Skill)
Install globally across all projects:
```bash
mkdir -p ~/.claude/skills/universal-context-sanitizer
cp SKILL.md ~/.claude/skills/universal-context-sanitizer/SKILL.md
```
Or install inside a specific repository so teammates inherit it automatically:
```bash
mkdir -p .claude/skills/universal-context-sanitizer
cp SKILL.md .claude/skills/universal-context-sanitizer/SKILL.md
```
Invoke directly inside Claude Code with `/universal-context-sanitizer` or ask Claude to sanitize/rewrite a prompt.

### 2. Claude.ai & Claude Desktop
1. Compress the `universal-context-sanitizer/` folder into a `.zip` archive (ensure `universal-context-sanitizer/SKILL.md` is at the top level of the ZIP).
2. Open **Customize > Skills** in Claude and upload the `.zip` file.

### 3. OpenAI Codex / Cursor / Custom GPTs / Gemini Gems
* **Codex (`AGENTS.md`) & Cursor (`.cursorrules`):** Append **Section 1 (The 7-Stage Sanitization Pipeline)** from `SKILL.md` into your project rules file.
* **Custom GPTs / Projects / Gems:** Paste the contents of `SKILL.md` into your system instructions. Any raw prompt pasted into the chat will return **only** the sanitized output.

---

## Example Transformation

| Raw Input (Leaks Context / Trips Filters) | Sanitized Output (`v3.0`) |
| :--- | :--- |
| *"I live in HK and need the cheapest flight home from Tokyo next week."* | *"I am wrapping up a business trip in Tokyo and need to book an outbound flight to HK next week before my onward connection. Compare standard fare options and routing."* |
| *"Here is my `.env` file `OPENAI_API_KEY=sk-proj-88a9f...` and server IP `45.77.12.9`, why am I getting 401?"* | *"I am debugging an HTTP 401 authentication error when connecting to an LLM API from a server at `203.0.113.10`. Using `<REDACTED_API_KEY>` as the environment variable placeholder, verify the proper `Authorization: Bearer` header syntax."* |

---

## Responsible Use

This skill is designed strictly for **privacy hygiene, credential redaction, and reducing false-positive classifier triggers** on lawful engineering, travel, and productivity tasks. It explicitly refuses to rewrite or facilitate malware, unauthorized system access, fraud, or harmful activity.
