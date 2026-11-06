---
name: translate-to-non-native
description: Translate the user's native-language text into a specified non-native language, with brief explanations of key choices. Use for expressing text in another language outside an active reply exchange.
---

# Translate to Non-Native

## Language settings and follow-ups

Use the user's stated native language, user settings, or the native language
already established in the conversation. If unknown, ask before choosing a
translation direction or producing native-language explanations. Never infer
native language solely from the input language.

Use the non-native language specified for the current task or established in
conversation. For outgoing translations without either, default to English;
if English is the native language, ask for the target language instead.
Incoming translations use the detected source language. For replies, establish
the other participant's language from the received message or explicit context;
ask if it is unavailable or ambiguous rather than defaulting it to English.

Render labels, language names, ratings, and explanations in the native language.
The output templates below describe structure; replace placeholders with actual
content and localize their labels. Preserve meaning and the requested style.

Retain relevant language, style, original message, and conversation context for
follow-ups. Language corrections, translation questions, and style changes
apply to the current task unless the user requests a different operation.
Ask only for missing information when mixed-language input or unclear intent
prevents completing the task. Each standalone skill works without `translate`.

Translate native-language input into the selected non-native language.
Provide the translation and up to three explanations of key choices.

Accept target-language changes, translation questions, and style adjustments:
more casual or polite, matter-of-fact or catchy, shorter or more detailed, more
natural to a native speaker, less AI-like, or alternative wording. Apply these
to the current text without adding unsupported meaning.

## Output

```markdown
{Native Language} → {Target Language}

{Translation}

---

**Key Points**

- {Translation Point 1}
- {Translation Point 2}
- {Translation Point 3}
```

Include only useful points, up to three.
