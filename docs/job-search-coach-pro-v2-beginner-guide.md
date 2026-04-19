# Job Search Coach Pro (v2): Beginner’s Guide

This guide is written for someone who has never used a “skill” before. It explains **which file to use**, **how to load it into an AI assistant**, and **how to get good results** without guessing.

## The one sentence version

**Give the AI the skill text file:** `skills/job-search-coach-pro-v2.md`  
That file is the “instruction manual” for how the assistant should behave (diagnose first, run modules, produce concrete outputs, never fabricate experience).

You **do not** need the Python generator (`scripts/generate_job_search_coach_skill.py`) unless you are editing how the markdown is produced.

---

## What you are actually “installing”

Different AI products use different words, but the idea is the same:

- You are attaching **long, persistent instructions** that shape tone, workflow, and deliverables.
- The skill file is **plain text** (Markdown with a small YAML header). It is not an executable program.

If someone shares the skill as `job-search-coach.skill`, that is usually the **same content** in a different wrapper/filename for a specific product’s “import skill” button. If you only have the `.md` from this repository, **use the `.md`**.

---

## Download the skill (pick the path that matches your situation)

### Path A: You are using this GitHub repository

1. Open the file in the repo: `skills/job-search-coach-pro-v2.md`
2. Download it (GitHub “Raw” → save), or clone the repository.

**Sanity check:** the file should begin with YAML like:

```yaml
---
name: job-search-coach-pro-v2
description: >
  ...
---
```

### Path B: Someone shared a Google Drive / Dropbox link

1. Open the link in your browser.
2. Download the file to your computer (usually your **Downloads** folder).
3. Keep the filename whatever it is (`.md`, `.skill`, etc.). The important part is the **contents**, not the extension.

**If your browser warns it cannot scan the file:** this is common for uncommon extensions. Plain-text skill files are not “programs,” but you should still only download from sources you trust.

---

## “Install” it in your AI (Claude web, Claude apps, ChatGPT, etc.)

Product UIs change, so use the **closest match** below.

### Option 1: Claude Projects (recommended for long skills)

1. Create a **Project** (or open an existing one).
2. Add **project knowledge / files** and upload `job-search-coach-pro-v2.md`.
3. In the project instructions (if available), add one line like:  
   **“Follow the uploaded Job Search Coach Pro v2 skill as your operating system for all job search tasks.”**

Why this works well: long instructions stay attached to the project instead of being pasted repeatedly.

### Option 2: Custom instructions (works everywhere, but has size limits)

1. Open **Settings** (or equivalent).
2. Find **Custom instructions** / **Personal preferences** / similar.
3. Paste the **entire** `job-search-coach-pro-v2.md` contents.

If it does not fit: use Projects, split across multiple pinned messages (less ideal), or use a desktop app that supports larger system prompts.

### Option 3: “Install skill from file” (if your Claude plan/UI has a Skills tab)

Some Claude experiences let you import a packaged `.skill` file.

1. Go to **Settings → Skills** (wording may vary).
2. Choose **Install from file**.
3. Select the downloaded skill file.

If your UI only accepts `.skill` but you only have `.md`, ask whoever shared it for the packaged file, or zip/rename only if your product explicitly documents that (do not guess).

### Option 4: Claude Code / Codex CLI / developer workflows

Typical pattern:

- Put the skill markdown in a known location in your repo.
- Configure your tool’s “instructions” or “skills directory” to load it (follow that tool’s official docs).

The exact flag or folder name depends on the CLI version.

---

## Your first run (60 seconds)

Open a new chat in the context where the skill is loaded (Project / Custom instructions / imported skill).

Send a message like:

> I’m using the Job Search Coach Pro v2 skill.  
> My biggest pain is: **I apply a lot but get ghosted**.  
> Target role: **{title}**  
> Location/remote: **{details}**  
> Recent results (approx is fine): **{applications / callbacks / interviews}** in the last **{timeframe}**  
> Here is my resume (paste text) and here is a JD (paste full text) if relevant: **{paste}**

Why this works: the skill is built to **diagnose the real bottleneck** before rewriting anything.

---

## How invocation works (automatic vs explicit)

### Automatic routing (what the skill is designed to do)

If the skill is actually loaded into the session, the assistant should treat certain phrases as **intent signals** and pick modules accordingly (see the “Primary router” table inside the skill).

Examples:

- “Tailor my resume to this job” → **Module 1**
- “Quick LinkedIn feedback” → **Module 2**
- “Deep LinkedIn audit” + PDF/paste → **Module 3**
- “Interview prep plan” → **Module 4**
- “I’m applying everywhere / need strategy” → **Module 5**
- “Help me find better jobs / target companies” → **Module 6**
- “Referral / networking messages” → **Module 7**
- “Tell me about yourself / story bank” → **Module 8**
- “Compare offers / negotiate” → **Module 9**
- “Weekly plan / accountability / laid off” → **Module 10**

### If it picks the wrong module (common for beginners)

Be explicit:

> Use **Module 6** only: build a prioritized target company list for **{role}** in **{geo}**.  
> Do not rewrite my resume yet.

### Mixed problems (very common)

Say the combo you want:

> Start with diagnosis, then run **Modules 1 + 5 + 10** for ghosted applications.

The skill includes suggested stacks like “ghosted applications” in the **Secondary router** section.

---

## The 10 modules: what each one is for (beginner table)

| Module | Name | Use it when… |
|---:|---|---|
| 1 | ATS Resume Optimizer | You have a **specific JD** and need truthful tailoring + gap analysis |
| 2 | LinkedIn Quick Feedback | You want a fast, honest read on headline/about/experience |
| 3 | LinkedIn Deep Audit | You can provide **full profile** (PDF export or full paste) |
| 4 | Interview Prep Planner | You have a company/stage and need a realistic prep plan + drills |
| 5 | Job Search Strategy Builder | You’re unfocused / wrong targets / unclear lanes / bad channel mix |
| 6 | Company Targeting & Fresh Job Discovery | You need better targets + freshness workflow + search strings |
| 7 | Networking & Referral Engine | You need short outreach scripts + follow-ups + “do not say” list |
| 8 | Story Bank & Positioning Engine | Your interviews/networking fail because your narrative is weak |
| 9 | Offer Strategy & Negotiation | You have offer details / competing options and need scripts + tradeoffs |
| 10 | Job Search OS & Recovery Mode | You need weekly execution + tracking + urgent recovery structure |

---

## What to paste for each module (minimum viable inputs)

This mirrors the “minimum intake” rules inside the skill.

### Module 1 (Resume tailoring)

Paste:

- Your resume (text is best; PDF upload if your client supports it)
- The **full** job description (not a summary)

Optional but high value:

- Target company name
- Rough numbers if your bullets are vague (the skill should ask; you can volunteer early)

**Important honesty note:** the skill forbids inventing metrics, tools, or ownership. If a JD requirement is not true for you, the output should flag it as **not addable without misrepresentation**.

**PDF output note:** some assistants can generate a downloadable PDF; some cannot. If you need a PDF, ask explicitly:  
> Please format the final resume as a clean document and **export/save as PDF** if you can.

### Module 2 (LinkedIn quick feedback)

Minimum:

- Headline
- About
- Current role description
- Your **target role** (what you want to be hired for)

Optional:

- URL (only helpful if the assistant can fetch it)
- Featured, skills, recent activity

### Module 3 (LinkedIn deep audit)

Hard requirement:

- Full profile PDF **or** a full paste of all major sections

If you only paste headline/about, the skill itself says: do not pretend that is a deep audit.

### Module 4 (Interview prep)

Minimum:

- Role + seniority
- Company
- Stage (screen / onsite / take-home / etc.)
- Hours/week you can commit

Optional:

- JD
- Interview date / timeline

**Inference note:** company-specific interview processes may be inferred; the assistant should label uncertainty clearly.

### Module 5 (Strategy)

Minimum:

- Target role options
- Experience level
- Geography
- What results you’ve been getting (even rough)

### Module 6 (Targeting / discovery)

Minimum:

- Target role
- Geography
- Remote/hybrid/onsite preference
- Company size preference (if any)

### Module 7 (Networking)

Minimum:

- Target role
- Who you’re messaging (recruiter / HM / possible referrer)
- 3–6 sentences about your background + any shared context

### Module 8 (Story bank)

Minimum:

- Target role
- Top achievements/projects/transitions (bullet list is fine)

### Module 9 (Offers)

Minimum:

- Offer facts you know: base/bonus/equity/title/location/deadline
- What you optimize for (cash vs learning vs title vs stability)

### Module 10 (Weekly OS / recovery)

Minimum:

- Hours/week
- Urgency (quiet vs urgent)
- Employed vs unemployed

---

## How to read the outputs (what “good” looks like)

The skill is designed to avoid generic advice. Strong outputs usually include:

- A **diagnosis** (“the bottleneck looks like X because Y”)
- **Ranked actions** (not 20 equal bullets)
- **Concrete artifacts**: rewrites, tables, scripts, checklists, scorecards
- A clear **“what I still need from you”** section

If you get vague fluff, your skill probably **is not loaded** in that chat/session, or the model is not following it—re-attach it or switch to a Project.

---

## Multi-module workflows (copy/paste starters)

### “Ghosted applications” stack

> Diagnose first. Then run **Modules 1, 5, 6, 7, 10**.  
> Here are my numbers for the last 14–30 days: …  
> Here is my resume: …  
> Here is a representative JD: …

### “Interviews but no offer” stack

> Diagnose first. Then run **Modules 4, 8, 10**.  
> Company: … Stage: … Hours/week: …

### “Laid off / urgent” stack

> Start **Module 10** recovery mode, then **Modules 1, 2, 5, 7, 8** in priority order.  
> Hours/week: … Target roles: …

---

## Troubleshooting (beginner FAQ)

### “It didn’t follow the skill”

- Confirm you loaded it into **this exact chat context** (Project file / custom instructions / imported skill).
- Start the message with: **“Follow the Job Search Coach Pro v2 skill.”**

### “It rewrote my resume but the job is a bad fit”

That is a **Module 5 / 6** problem (targeting and strategy), not a resume polish problem. Ask for a strategy pass.

### “It invented metrics”

Tell it to stop and regenerate with this constraint:

> Regenerate with **no invented metrics**. Use placeholders like **[TBD: revenue impact]** where numbers are missing.

### “It sounds robotic”

Ask for:

> Preserve my voice. Keep changes minimal but high-impact. Show **before/after** only for changed bullets.

---

## Safety and ethics (read once)

- Do not ask the AI to **lie** or inflate titles, tools, metrics, or ownership.
- Do not use manipulative networking tricks; the skill is designed to avoid guilt-based outreach.
- Treat compensation and interview-process claims as **hypotheses** unless you have first-hand confirmation.

---

## Where this guide lives in the repository

- Skill file: `skills/job-search-coach-pro-v2.md`
- This guide: `docs/job-search-coach-pro-v2-beginner-guide.md`
- Generator (maintainers only): `scripts/generate_job_search_coach_skill.py`

---

## Quick start phrases (copy/paste)

- **Module 1:** “Module 1: tailor my resume to this JD. Here is resume + full JD.”
- **Module 2:** “Module 2: quick LinkedIn feedback. Headline/about/current role/target role below.”
- **Module 3:** “Module 3: deep audit. LinkedIn PDF attached / full paste below.”
- **Module 4:** “Module 4: interview prep plan for {company} {role} at {stage}. I have {N} hours/week.”
- **Module 5:** “Module 5: job search strategy. I’m getting ghosted; here are my targets + numbers.”
- **Module 6:** “Module 6: target companies + fresh discovery workflow for {role} in {geo}.”
- **Module 7:** “Module 7: write recruiter + HM + referral messages for {company}.”
- **Module 8:** “Module 8: build story bank + 30s/90s intros for {target role}.”
- **Module 9:** “Module 9: offer negotiation. Here are offer facts + my priorities.”
- **Module 10:** “Module 10: weekly job search OS + recovery sprint. Hours/week + urgency below.”
