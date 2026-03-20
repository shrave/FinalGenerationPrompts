# FinalGenerationPrompts

Prompt templates for a test‑generation workflow, including call‑chain discovery and log‑based vulnerability verdicts. ([]())

**What’s inside**
- `TestGenPrompt` — Main JUnit test‑generation prompt template with strict rules around call paths, assertions, and build behavior. ([raw.githubusercontent.com](https://raw.githubusercontent.com/shrave/FinalGenerationPrompts/main/TestGenPrompt))
- `TestGenPrompt_without_sudo` — Variant of the test‑generation prompt that explicitly avoids sudo requirements. ([raw.githubusercontent.com](https://raw.githubusercontent.com/shrave/FinalGenerationPrompts/main/TestGenPrompt_without_sudo))
- `callChainPrompt` — Template for discovering source‑to‑sink call chains in a codebase. ([raw.githubusercontent.com](https://raw.githubusercontent.com/shrave/FinalGenerationPrompts/main/callChainPrompt))
- `gptAnalysis` — Short instruction set for classifying log outcomes into a JSON verdict. ([raw.githubusercontent.com](https://raw.githubusercontent.com/shrave/FinalGenerationPrompts/main/gptAnalysis))

**Usage**
1. Pick the prompt template you need.
2. Substitute the placeholders (for example `{source_method}`, `{client_rel_path}`, `{sink_method}`, `{vulnerable_id}`).
3. Provide the filled prompt to your model runner.
4. For log triage, use `gptAnalysis` and parse the JSON response.

**Expected analysis output**
The log‑analysis template expects a strict JSON object with these fields:
- `triggered` (yes/no/unknown)
- `confidence` (low/medium/high)
- `reasoning` (short explanation referencing log evidence) ([raw.githubusercontent.com](https://raw.githubusercontent.com/shrave/FinalGenerationPrompts/main/gptAnalysis))
