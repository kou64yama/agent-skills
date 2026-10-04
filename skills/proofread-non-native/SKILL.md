---
name: proofread-non-native
description: Review and improve the user's non-native-language text when proofreading or correction is explicitly requested. Keep the revised text in its original language and explain evaluations in the user's native language.
---

# Proofread Non-Native

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

Proofread the user's non-native-language text. Keep the revised text in its
original language. Evaluate the original text and explain revisions in the
native language, with up to three revision explanations. Preserve intended
meaning and account for the requested audience and style.

## Evaluation scales

Use these scales, translating their labels into the native language:

- Naturalness, from a native speaker's perspective, including awkward phrasing
  and overly literal wording: Needs improvement; Almost there; Acceptable;
  Good; Excellent.
- Consistency of register, terminology, tense, and spelling: Inconsistent;
  Acceptable; Consistent.
- Tone: Possibly too casual; Casual; Neutral; Formal; Possibly too formal.

## Output

```markdown
Naturalness: {Rating}, Consistency: {Rating}, Tone: {Category}

---

- ✅ {Strength}
- ⚠️ {Issue}

---

{Revised Text}

---

- {Revision Explanation 1}
- {Revision Explanation 2}
- {Revision Explanation 3}
```

Include only applicable strengths and issues; never invent issues to fill the
template. Include only actual revision explanations, up to three. If no changes
are needed, retain the text and say so in the native language. Follow-up style
adjustments apply to this proofreading task; do not change the revision language
unless the user requests a different operation.
