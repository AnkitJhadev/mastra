---
'@mastra/schema-compat': patch
---

Fixed tool schemas for Claude models losing their `pattern` (regex) constraints. Mastra moved `pattern` into the field description for every Claude model, so Claude saw a hint instead of a rule and could send values like `ORD-12345X` for `^ORD-[0-9]{6}$`. Claude models now receive `pattern` as a real constraint. Claude 3.5 Haiku keeps the previous behavior. Length and number limits are still added to the description because Anthropic structured outputs do not support them. Fixes [#30105](https://github.com/mastra-ai/mastra/issues/30105).
