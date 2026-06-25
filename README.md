# writing-eloquent-arabic

مهارة لـ Claude Code تكتب وتراجع المحتوى العربي للواجهات فتجعله بليغًا لا ركيكًا — تكشف الترجمة الحرفية المبنية على قواعد الإنجليزية وتعيد صياغتها بأسلوب عربي أصيل.

A [Claude Code](https://claude.com/claude-code) skill that writes and reviews **Arabic UI copy** so it reads **بليغ, not ركيك**. It catches Arabic that is grammatical but secretly built on English grammar — literal calques, wrong register, robotic tone — and rewrites it in native Arabic structure.

Most "Arabic support" stops at translation. A translated string is grammatical and still wrong: a native ear hears the English underneath. This skill targets that gap — the *words*, not the layout (for RTL/fonts/numerals, see [`designing-arabic-frontends`](https://github.com/ahmed-badawood/designing-arabic-frontends)).

## Why trust it

Built with TDD for documentation — every rule targets a failure observed in real agent testing, measured by blind A/B with an independent Arabic editor:

| Phase | Strings | Skill wins | Ties | Skill losses | Failure modes (control vs skill) |
|---|---|---|---|---|---|
| Baseline (no skill) | 10 | — | — | — | **10/10 strings came back weak** |
| With the skill (first draft) | 8 | 2 | 3 | 3 | 6 vs 7 |
| After corrections, re-test | 8 | 5 | 1 | 2 | 12 vs 4 |
| Final | 8 | **7** | 1 | **0** | **11 vs 2** |

Ten realistic Arabic UI strings (onboarding, errors, notifications, consent, destructive confirms) were translated by agents **without** the skill; an expert Arabic editor diagnosed every one as weak/calqued, and those failures became the skill's 8-mode catalog. New strings were then generated **with** vs **without** the skill and judged **blind**: the skill removed ~82% of failure modes and won 7 of 8 head-to-head, with zero losses, after two refinement rounds.

## What it covers (ordered by how often agents get it wrong)

1. **register-mismatch** — a formal/bookish word in casual copy (تنبيه، لقد أنفقت)
2. **literal-idiom** — idioms/interjections mapped 1:1 ("take control" → تحكّم في; "You did it!" → أنت أنجزته)
3. **weak-connector** — choppy stops and comma splices where Arabic binds with و / ثمّ
4. **english-word-order** — relative-clause shapes, SVO in فصحى, fronted "For your security, …" clauses
5. **calque** — بمجرد + masdar, explicit لك, agentless masdar dropping "you"
6. **awkward-idafa** — noun-stacking and same-root tautology (متكررة لتتكرر)
7. **wrong-preposition** — bare abstract nouns (اتصالك instead of اتصالك بالإنترنت)
8. **robotic-tone** — لم نتمكّن confession-framing, raw stats with no human frame

Plus a register guide (فصحى vs colloquial by context), worked ركيك→بليغ examples, and a formal→lived lexicon. The dialect examples use Saudi/Gulf white dialect; the failure modes are pan-Arabic and adapt to any market.

## Install

```bash
npx skills add ahmed-badawood/writing-eloquent-arabic
```

Works with Claude Code, Cursor, Codex, and any agent supported by the [skills CLI](https://github.com/vercel-labs/skills) — installs into the current project; add `-g` to install globally. Or install manually:

```bash
git clone https://github.com/ahmed-badawood/writing-eloquent-arabic.git ~/.claude/skills/writing-eloquent-arabic
```

Claude Code discovers it automatically. It triggers on any task touching Arabic UI copy and composes with design skills like `frontend-design`, `impeccable`, and `designing-arabic-frontends`, layering Arabic copy quality on top.

The skill follows the [Agent Skills specification](https://agentskills.io/specification), so it also works with other agents that support `SKILL.md` skills.

## License

[MIT](LICENSE)
