---
name: translate
description: Coordinate translation assistance when the user has not chosen a standalone skill, selecting native-language translation, outgoing translation, explicit proofreading, or an ongoing reply exchange while retaining context.
---

# Translate

Select one of the four standalone translation skills and carry context between
requests. This skill requires `translate-to-native`, `translate-to-non-native`,
`proofread-non-native`, and `reply-in-non-native` for its supported operations.

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
Use the selected skill's output template, replacing placeholders with actual
content and localizing its labels. Preserve meaning and the requested style.

Retain relevant language, style, original message, and conversation context for
follow-ups. Language corrections, translation questions, and style changes
apply to the current task unless the user requests a different operation.
Ask only for missing information when mixed-language input or unclear intent
prevents completing the task. Each standalone skill works without `translate`.

## Select the operation

Prioritize the explicit request and active conversation context over detected
input language. After establishing the native language, use this order:

1. Explicit proofreading or correction: `proofread-non-native`.
2. A reply request or an ongoing exchange: `reply-in-non-native`.
3. Other non-native-language input: `translate-to-native`.
4. Other native-language input: `translate-to-non-native`.

If mixed languages or unclear intent prevent selection, ask only for the missing
information. A language change, translation question, or style adjustment stays
with the current operation unless the user requests another operation. An
explicit new operation takes precedence over an ongoing exchange; select again
when the task changes while retaining relevant settings.

## Load and hand off

Find the selected skill by its exact name in the available skills catalog and
read its `SKILL.md` using the catalog's location and access mechanism. In a
bundled filesystem layout, use the adjacent definition if no catalog entry is
available:

- `translate-to-native`: `../translate-to-native/SKILL.md`
- `translate-to-non-native`: `../translate-to-non-native/SKILL.md`
- `proofread-non-native`: `../proofread-non-native/SKILL.md`
- `reply-in-non-native`: `../reply-in-non-native/SKILL.md`

Resolve these paths relative to this skill's directory. Load only the selected
skill, not all four. If it cannot be found or read, name the missing skill and
explain in the native language that it must be installed or made available to
complete that operation. Do not silently substitute instructions or install it.

Pass the native language, current non-native language, requested style, original
message, speaker attribution, and relevant conversation context to the selected
skill. Follow that skill's output format and evaluation rules. Keep these
settings available within the conversation, including the original message when
switching from understanding an incoming message to composing a reply. Do not
write settings to external storage or send replies merely by invoking a skill.
