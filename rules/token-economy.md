---
description: token-economy rules
globs: "*"
---

# Token Economy & Efficient Code Exploration Rules

1. **Targeted Reading (No Full File Dumps):**
   When examining code files > 50 lines, do NOT read the entire file. Use `StartLine` and `EndLine` parameters in `read_file` to read only the targeted function or block, or use CodeGraph (`codegraph_explore`).
2. **Subagents Verdict-Only Constraint:**
   Subagents must never return raw intermediate tool logs to the parent agent. Output must be strictly bounded to <= 15 lines (Status + 2-3 risks + action).
3. **Subagent Model Tiering:**
   Always default subagent invocations to `Model: "flash"` or `"flash_lite"` unless deep multi-step architectural arbitration explicitly requires `Model: "pro"`.
4. **Brief Responses:**
   Strictly observe `hz-brief-responses`: concise factual reports without conversational filler, ending with one short line.
