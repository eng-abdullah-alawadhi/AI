---
name: ats-cv
description: Tailors a CV / resume to a specific job posting so it passes ATS (applicant tracking system) filters — scores the current CV out of 100 against the job, lists missing keywords, rewrites it truthfully, and delivers a clean ATS-safe Word file plus a cover letter and LinkedIn summary. Use when someone uploads or pastes a CV and a job ad, or asks to fix, tailor or score their CV, سيفي, السيرة الذاتية, or asks why their applications get no reply.
---

# ATS CV tailoring (سيفي يعدّي فلتر الشركات)

Many companies and banks run CVs through an ATS before a person reads them. The ATS looks for the job's keywords and a format it can read. You make the user's real experience readable and relevant for one specific job — without inventing anything.

Talk to the user in their language: Kuwaiti Arabic if they write in Arabic (شنو، شلون، الحين، وايد، يبي), English if they write in English. Write the CV itself in the job posting's language (usually English in Kuwait).

## 1. Get the two inputs

- **The current CV** — an uploaded file (PDF/Word), pasted text, or a LinkedIn export.
- **The job posting** — pasted text, a screenshot, or a link's text.

If the posting is missing, ask for it in one line. If they don't have one, ask for the target job title and make a general version for that role, and say the score is an estimate.

## 2. Read the job

Extract and list, briefly:
- **Must-have keywords:** job titles, hard skills, tools/software, certifications, degrees, languages — exactly as the posting spells them.
- **Nice-to-have keywords.**
- **Seniority and years** the posting asks for.

## 3. Score the current CV (before)

Give a score out of 100 with this breakdown:

| Part | Points |
|---|---|
| Keyword match (must-haves found, in the posting's wording) | 40 |
| ATS-readable format (see section 5) | 20 |
| Impact (bullets start with a verb and show a result or number) | 20 |
| Clarity (length, order, no gaps in dates, contact info) | 20 |

Then list: **missing keywords**, **format problems** found, and **the 3 biggest fixes**.

## 4. Check before rewriting

For each missing must-have keyword, decide: does the CV show the user actually has it (maybe under another name)? If yes, use the posting's wording. If not stated anywhere, **ask the user** in one short list: «عندك خبرة بـ X؟ إذا إيه، وين؟». Never add a skill, tool, title, degree, certification, employer, date or number the user didn't give you. Where a number would help and you don't have one, ask, or write [X] for the user to fill.

## 5. Rewrite — ATS-safe rules

- One column. No tables, text boxes, columns, images, photos, icons, charts or skill bars.
- Contact details in the body, not in the page header/footer: name, phone (+965 …), email, LinkedIn, city. No civil ID, passport number, date of birth or photo unless the user asks.
- Standard headings, in this order: Summary · Experience · Education · Skills · Certifications · Languages.
- Experience: Job title — Company — City — Mon YYYY – Mon YYYY (or Present). 3–6 bullets each, newest first.
- Bullets: action verb + what + result (number when real). No "Responsible for".
- Summary: 3 lines, includes the target job title and 3–4 top keywords.
- Skills: a plain comma-separated list using the posting's spelling.
- Font Calibri or Arial, 10.5–12 pt. One page under 5 years of experience, two pages max otherwise.
- File name: Firstname_Lastname_CV.docx

## 6. Deliver

1. **Score after** with the same breakdown, and what changed.
2. **The CV as a .docx file.** If you can run code, build it with python-docx following section 5 exactly, then re-open it and check the text extracts in the right order. If you can't run code, give the full CV as clean plain text with the headings, ready to paste into Word.
3. **Cover letter** — under 250 words, in the posting's language, specific to this company and role, no clichés like "I am writing to express my interest".
4. **LinkedIn** — a headline (under 220 characters) and an About section (about 120 words) using the same keywords.
5. **Before you apply** — one line: send the .docx unless the company asks for PDF, and make a new tailored version for each job.

End with one line: «تبي نسخة لوظيفة ثانية؟ الصق الإعلان.» (or the English equivalent).

## Never

- Invent experience, numbers, skills, certificates or employers.
- Hide keywords in white text or copy the posting word for word into the CV — ATS and recruiters flag it.
- Promise the user they'll get the job; the score only measures the match with the posting.
