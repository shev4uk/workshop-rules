# PRD: Slidev Workshop Deck для Cursor / AI-Assisted Coding

## 1. Executive Summary

**Продукт**: Slidev-based workshop slide deck (та підтримуючі матеріали) для **intermediate-level, 90-120 хвилин, hands-on** воркшопу про **Cursor / AI-assisted coding**.

**Основна мета**: Учасники залишаються з практичними workflow для ефективного використання Cursor (prompting, навігація по кодовій базі, рефакторинг, тести, PR reviews), плюс повторюваний "playbook".

## 2. Goals (Що означає успіх)

### Learning Goals
- Учасники можуть використовувати Cursor для: дослідження незнайомих кодових баз, безпечної імплементації фіч, рефакторингу з впевненістю, генерації високоякісних PR.
- Учасники розуміють обмеження/ризики (hallucinations, security, licensing, privacy) і застосовують guardrails.

### Delivery Goals
- Deck підтримує live teaching: чіткий pacing, speaker notes, checkpoints, timeboxes.
- Workshop можна запустити на Windows 11 та macOS з мінімальним setup friction.

### Success Metrics
- **Completion**: ≥80% учасників завершують core lab(s) в межах timebox.
- **Quality**: Post-workshop rating ≥4.5/5 на корисність.
- **Behavior Change**: ≥60% повідомляють про adoption принаймні 2 workflow (наприклад, "search → read → plan → patch → validate" loop).

## 3. Audience

**Primary**: Intermediate developers (frontend/backend/fullstack) з реальним досвідом роботи з кодовою базою.

**Assumed Baseline**: Git basics, PR workflow, знайомство з Node tooling; не потрібно попереднього mastery Cursor.

## 4. Problem Statement

Developers часто "пробують AI" ad hoc. Їм потрібен структурований, безпечний, повторюваний підхід для використання Cursor для shipping реальних змін (не просто snippets), зберігаючи code quality та team standards.

## 5. Scope

### In Scope
- Slide deck (Slidev) з speaker notes та live-demo prompts.
- Hands-on labs з використанням невеликого practice repo (може бути цей repo або окремий "lab repo").
- Setup instructions та troubleshooting.
- Export/deploy як static SPA (Netlify/Vercel) та PDF export для offline use.

### Out of Scope (для цієї ітерації)
- Повноцінна course platform (auth, progress tracking).
- Глибока ML теорія.
- Multi-language локалізація за межами однієї primary мови.

## 6. Key Use Cases / User Stories

- **Як учасник**, я можу налаштувати Cursor та lab repo за <15 хвилин.
- **Як учасник**, я можу використовувати Cursor для:
  - Задавання targeted питань про існуючий код і отримання file/function pointers.
  - Генерації плану перед кодуванням, потім застосування incremental changes.
  - Написання тестів/validation steps та інтерпретації failures.
  - Підготовки PR description з ризиками, tradeoffs, та verification steps.
- **Як інструктор**, я можу запускати deck live, використовувати speaker notes, та надійно timebox labs.
- **Як maintainer**, я можу оновлювати slides/labs та швидко deploy нову версію.

## 7. Content Requirements (Deck Structure)

Target length: **90-120 хвилин**, включаючи **2 labs** + breaks.

### Module 0 — Setup (10-15 хв)
- Install/run prerequisites (Cursor, Git, Node).
- Відкрити repo, підтвердити що Slidev працює, підтвердити що lab repo build/tests.

### Module 1 — Mental Model & Guardrails (10-15 хв)
- Коли використовувати AI vs не використовувати.
- Безпечні prompting patterns (constraints, acceptance criteria, "show references", "don't guess").
- Security/privacy + secrets handling.

### Module 2 — Codebase Navigation Workflows (15-20 хв)
- "Map the system": entrypoints, configs, build pipeline, deps.
- Запитання "where is X handled?" та verification з search.

### Lab 1 — Small Feature + Tests (25-30 хв)
- Імплементація scoped feature з чіткими acceptance criteria.
- Додавання/adjusting тестів, запуск локально, виправлення failures.
- Акцент: incremental changes + verification.

### Module 3 — Refactoring & PR Quality (10-15 хв)
- Безпечний рефакторинг: rename, extract, simplify, remove dead code.
- PR description, risk assessment, rollout notes.

### Lab 2 — Refactor + PR Writeup (20-30 хв)
- Рефакторинг "smelly" модуля, збереження behavior, доказ через тести.
- Генерація PR summary з "what/why/how tested".

### Wrap-up (5 хв)
- Checklist/playbook.
- Next steps/resources.

**Speaker Notes**: Потрібні для всіх instructor-led slides (timing, demo commands, common pitfalls).

## 8. Functional Requirements (Repo + Authoring)

### Deck Authoring
- Primary content в `slidev/slides.md`, опціонально split через `src:` imports (наприклад, `slidev/pages/*.md`).
- Використання Slidev features: code highlighting, callouts, diagrams, interactive components тільки коли це покращує навчання.

### Labs
- Надати принаймні:
  - `README` з setup + tasks + expected outputs.
  - "Starter" state + "solution" reference (branch/tag або folder).

### Build & Run
- `pnpm dev` (або npm) запускає Slidev локально.
- `npm run build` створює `dist/` для deployment.

### Deploy
- Static SPA deploy підтримується (Netlify + Vercel configs вже існують).

## 9. Non-Functional Requirements

- **Clarity**: Немає wall-of-text slides; кожен slide має одне повідомлення + visuals/examples.
- **Accessibility**: Розумний contrast, читабельні font sizes, keyboard navigation.
- **Reliability**: Labs не повинні вимагати flaky external APIs.
- **Security**: Явні інструкції: ніколи не вставляти secrets; приклади redaction.

## 10. Acceptance Criteria (Definition of Done)

- Deck покриває всі модулі вище і вміщується в **90-120 хвилин** з timeboxes.
- Два labs можна запустити end-to-end з instructions та verification steps.
- Deck deployable і завантажується коректно як SPA; PDF export працює для offline.
- Speaker notes існують для ≥80% instructional slides (всі demos + labs).

## 11. Risks & Mitigations

- **Setup friction** → Надати "known-good" Node version, step-by-step checklist, fallback "watch-only" path.
- **AI unpredictability** → Використовувати prepared prompts та "expected answer characteristics", навчати verification.
- **Scope creep** → Дотримуватися timeboxes та тримати labs tightly scoped.

## 12. Milestones (Suggested)

- **M1**: Outline + timing + slide skeleton
- **M2**: Lab 1 complete + validated
- **M3**: Lab 2 complete + validated
- **M4**: Polish (notes, visuals, deploy, PDF) + dry run

## 13. Open Questions (To Finalize)

- **Мова**: Чи повинен deck бути переважно **українською чи англійською** (або bilingual)?
- **Lab repo choice**: Чи хочете labs всередині цього repo (просто) або окремий виділений "lab" repo (чистіше)?
