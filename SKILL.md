---
name: writing-eloquent-arabic
description: Use when writing, reviewing, translating, or polishing any Arabic user-facing content — UI strings, onboarding, errors, notifications, buttons, empty states, legal/consent copy — especially Arabic adapted from English that reads literal, calqued, robotic, or ركيك (weak). Triggers when Arabic sounds translated rather than natively written, or when بلاغة, fluency, or register needs checking.
---

# Writing Eloquent Arabic (بلاغة)

## Overview

Arabic written by translating English word-for-word is **secretly built on English grammar** — it is grammatical, but a native ear hears the English underneath. That is ركيك (weak) copy. Eloquent Arabic (بليغ) is composed in Arabic structure from the start, not mapped from a source sentence.

**Core principle:** If a sentence can be back-translated to the exact English word-for-word, it is probably calqued — rewrite it.

**Eloquent ≠ ornate.** The most native choice is usually the *simplest* idiomatic one. A fancier word or a cleverer construction is often *less* بليغ — and over-translating is its own failure (e.g. "You did it!" → ❌ أنت أنجزته vs ✅ أحسنت). When in doubt, reach for the plain expression a native speaker would actually say, not a more elaborate one.

**This skill does two things:** (1) flag where Arabic content reads translated/weak, naming the specific failure, and (2) propose a natively-structured rewrite, honoring the right register.

> **Market note:** the dialect examples below use Saudi/Gulf white dialect (عامية بيضاء). The *failure modes* are pan-Arabic; for another market, keep the modes and swap the colloquial register for your audience's (Egyptian, Levantine, Maghrebi…).

## When to use

- Any user-facing Arabic copy: onboarding, errors, notifications, buttons, labels, empty states, consent/legal, marketing.
- Arabic produced by translating an English string (the common source of ركيك copy).
- When someone says the Arabic "sounds weak / translated / robotic" or asks to make it بليغ.

**Not for:** Arabic layout/RTL/numerals/fonts — that is the `designing-arabic-frontends` skill. This skill is about the *words*, not the rendering.

## Register: match the context

The single most common failure (register-mismatch). Pick before writing:

| Context | Register |
|---|---|
| Errors, consent/legal, destructive confirms, financial/account terms | **فصحى (MSA)** — formal but not stiff |
| Onboarding, greetings, empty states, nudges, motivational, CTAs | **Warm** — light colloquial (e.g. عامية بيضاء) is welcome |

Wrong register reads worse than a small grammar slip. A signage word (تنبيه) or a sermon verb (أنفق, لقد) in a friendly nudge breaks the tone instantly.

## The 8 failure modes

Scan every Arabic string against these. Each row: the tell → the fix.

| Mode | Tell (English bleeding through) | Fix |
|---|---|---|
| **register-mismatch** | formal/bookish word in casual copy: تنبيه, لقد أنفقت, متأكد | use the lived word: انتبه، صرفت، بالفعل |
| **literal-idiom** | idiom/interjection mapped 1:1: تحكّم في = "take control"; أنت أنجزته = "You did it!" | native equivalent: خُذ زمام; for interjections use the Arabic one — أحسنت/مبروك, انتبه, يا سلام — never structural translation |
| **weak-connector** | choppy `.` between bound ideas; bare و listing actions; **comma-splicing two complete sentences** | bind *related* ideas with و / ثمّ / causal link — but **two complete sentences take a full stop, not a comma** (comma splice reads weak in Arabic) |
| **english-word-order** | الـ + الذي + verb relative clause; trailing time adverbial; **SVO in فصحى** (جلستك انتهت); **fronted English-style intro clause** ("For your security, …" → لأمان حسابك،) | compress to possessive (مستقبلك not المستقبل الذي...); **lead with the verb (VSO)** and let purpose **trail**: انتهت جلستك لحماية حسابك، تعذّرت المزامنة |
| **calque** | بمجرد + masdar; explicit لك on indefinite noun; agentless masdar dropping "you" | keep user as agent: أول ما تضيف، not بمجرد الإضافة |
| **awkward-idafa** | noun-stacking; same root twice (متكررة لتتكرر) | drop a link; use distinct roots: التكرار + يتجدّد |
| **wrong-preposition** | bare abstract noun: اتصالك ("your connection") | spell it out: اتصالك بالإنترنت |
| **robotic-tone** | لم نتمكّن confession-framing; raw stat with no human frame | frame around the process: تعذّرت المزامنة |

## Worked examples (ركيك → بليغ)

> Verify final wording with a native speaker and adapt to your product's voice — eloquence is a judgment call, not a rule.

**Onboarding (friendly)** — literal-idiom + word-order + register
- ❌ مرحبًا بك! تحكّم في أموالك وابنِ المستقبل الذي تطمح إليه.
- ✅ مرحبًا بك! خُذ زمام أموالك، وابنِ المستقبل اللي تحلم فيه.
- *why:* خُذ زمام = real empowerment idiom (not mechanical تحكّم في); تحلم فيه drops aspirational تطمح to warm; light dialect اللي...فيه speaks *to* the user.

**Sync error (formal)** — robotic-tone + calque + wrong-preposition
- ❌ لم نتمكّن من مزامنة حسابك في الوقت الحالي. يُرجى التحقق من اتصالك والمحاولة مرة أخرى.
- ✅ تعذّرت مزامنة حسابك حاليًّا. يُرجى التأكد من اتصالك بالإنترنت ثمّ إعادة المحاولة.
- *why:* تعذّرت frames it as the process failing (not a "we couldn't" confession); حاليًّا replaces calqued في الوقت الحالي; بالإنترنت spells out the bare noun; ثمّ sequences instead of flat و.

**Budget nudge (friendly)** — register-mismatch
- ❌ تنبيه — لقد أنفقت 90٪ من ميزانية المطاعم لهذا الشهر.
- ✅ انتبه 👋 صرفت 90٪ من ميزانية المطاعم هذا الشهر.
- *why:* صرفت is the everyday spoken verb (أنفق = accounting/charity register); drops bookish لقد and signage-grade تنبيه.

**Delete confirm (formal)** — calque + weak-connector
- ❌ هل أنت متأكد أنك تريد حذف حسابك؟ سيؤدي ذلك إلى محو جميع بياناتك نهائيًا...
- ✅ هل تريد بالفعل حذف حسابك؟ سيتم حذف جميع بياناتك نهائيًا دون إمكانية استرجاعها.
- *why:* folds "sure you want to" into one adverb بالفعل; states the consequence directly (سيتم حذف) instead of the bureaucratic سيؤدي إلى; ها refers straight to the data.

**Recurring helper (formal)** — awkward-idafa tautology
- ❌ اضبط معاملة متكررة لتتكرر تلقائيًا كل شهر.
- ✅ فعِّل التكرار ليتجدّد هذا القيد تلقائيًا كل شهر دون الحاجة إلى إعادته.
- *why:* فعّل (enable) not اضبط (calibrate); breaks the ك-ر-ر stutter with two roots (تكرار + يتجدّد); adds the implicit payoff "set once."

## Lexicon — formal/bookish → lived (Saudi/Gulf)

> Adapt to your market and verify with a native ear. Hand-curated — no authoritative dialect lexicon is freely/commercially licensed.

| Bookish / calqued | Lived | Note |
|---|---|---|
| أنفق | صرف | "spend" — أنفق = accounting/charity register |
| تنبيه | انتبه / بس عشان تدري | "heads up" — تنبيه = signage |
| تحقّق من | تأكّد من | "check" — تحقّق leans auditing |
| معاملة | عملية | "transaction" — معاملة = paperwork |
| في الوقت الحالي | حاليًّا | "right now" |
| بمجرد + masdar | أول ما + verb | "once …" — keep the user as agent |
| اضبط | فعِّل | "set up" — اضبط = calibrate |
| لا توجد … بعد | ما عندك … للحين | "none yet" — warmer, second-person |
| تحكّم في | خُذ زمام | "take control" |
| لقد + perfect | (drop it) | emphatic past, too bookish for microcopy |

## References (MSA authority)

- **KSAA Riyadh Dictionary** — dictionary.ksaa.gov.sa — authoritative contemporary **MSA** (use for the formal register; no dialect).
- **KSAA SIWAR** — siwar.ksaa.gov.sa — 20+ dictionaries for MSA word lookups while authoring.

## Process

1. **Read it aloud.** Would a native say this, or does it echo the English sentence?
2. **Scan the 8 modes** against the string (use the table).
3. **For each weak spot:** name the mode, rewrite in native Arabic structure, keep UI copy *tight* (eloquent ≠ longer).
4. **Match register** to context (table above).
5. **Output:** the flag + the rewrite + a one-line why.

## Red flags — you're shipping ركيك

- The Arabic maps one-to-one onto the English clause order.
- You translated an idiom literally instead of finding the Arabic one.
- A formal/bookish word landed in friendly copy (or vice versa).
- Two clauses joined by a bare `.` that Arabic would bind.
- An explicit لك / agentless masdar that only exists because English had "your" / a noun.

**All of these mean: stop, name the mode, rewrite from Arabic structure.**
