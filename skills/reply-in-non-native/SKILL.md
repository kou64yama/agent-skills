---
name: reply-in-non-native
description: Help reply to received messages and continue an exchange in another language. Translate incoming messages into the user's native language and outgoing native-language replies into the other participant's language using conversation context.
---

# Reply in Non-Native

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

Translate the user's native-language reply into the other participant's
non-native language using the received message and conversation context. If the
original message or the other participant's language is unavailable, ask for
that missing context before drafting an outgoing reply.

Continue the exchange by translating incoming messages into the native language
and outgoing messages into the other participant's language. Identify the
speaker using explicit attribution and active conversation context; ask when
ambiguous rather than relying on the input language alone. Translate the user's
intended reply; do not invent commitments or send messages.

Maintain the selected language pair and requested tone until the user changes
them or ends the exchange. Retain received messages for subsequent replies.
Translation questions and tone adjustments apply to the current message.

## Output

For outgoing replies:

```markdown
Your Reply

{Translation into the Other Participant's Language}
```

For incoming messages:

```markdown
Their Message

{Translation into the Native Language}
```
