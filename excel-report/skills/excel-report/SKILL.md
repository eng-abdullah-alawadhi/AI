---
name: excel-report
description: Turns a messy Excel or CSV file into a clean, manager-ready report — cleans the data (duplicates, dates, blanks, spelling of names), calculates the key numbers, builds charts, and delivers a tidy Excel file with a Summary sheet, a short report (Word, PDF or PowerPoint) and a ready message to send to the manager. Use when someone uploads a spreadsheet (.xlsx, .xls, .csv) and asks for a report, summary, dashboard, charts, analysis, «تقرير», «ملخص», «اكسل», or says the file is messy and needs cleaning.
---

# Excel → report (من ملف Excel مخربط… لتقرير جاهز حق المدير)

People get a sheet exported from a system or filled by hand, and need a report by end of day. You clean the data, find the numbers that matter, and hand back something they can forward to their manager as is — with every number traceable to their file.

Talk to the user in their language: Kuwaiti Arabic if they write in Arabic (شنو، شلون، الحين، وايد، يبي), English if they write in English. Write the report in the language they ask for (default: the language they wrote in).

## 1. Get the inputs

- **The file** — .xlsx, .xls or .csv. If it has several sheets, list them and ask which ones matter (unless the request makes it obvious).
- **The goal** — what the report is about and who reads it. If they didn't say, ask one line: «التقرير عن شنو، وحق منو؟» Otherwise pick sensible defaults and state them.
- **Format** — Word, PDF or PowerPoint. Default: Word.

## 2. Look before you touch

If you can run code, load the file with pandas (openpyxl for .xlsx). Report briefly:
- Rows × columns per sheet, the header row (it is not always row 1), and what each column seems to be (date, amount, name, category, ID…).
- Problems found, with counts: exact duplicate rows, blank rows, empty key fields, dates stored as text or in mixed formats, numbers stored as text or with currency signs, the same name spelled several ways (e.g. «Al-Rai» / «AlRai» / «الري»), merged cells, totals rows mixed into the data, outliers that look like typos (e.g. 10x the median).

## 3. Clean — and log every change

- Never change the original file. Work on a copy.
- Fix only what is clearly wrong: trim spaces, convert types, unify date formats, remove exact duplicates and subtotal rows, unify obvious name variants.
- Anything that is a judgment call (possible duplicates that differ slightly, outliers, missing amounts) — **don't decide alone**. Show a short list and ask: keep, fix, or drop.
- Keep a **cleaning log**: what changed, how many rows, and why. Rows before → rows after.

## 4. Calculate what matters

Pick 4–6 numbers that answer the goal, for example: total and count, change vs the previous period (% and absolute), top 5 / bottom 5 (products, branches, staff, customers), share of total, average per day/order, trend by week or month.

Rules:
- Every number must come from the data. **Never invent, estimate or round silently.** If something can't be calculated from the file, say so.
- Check the totals reconcile: your grand total must equal the cleaned source total. Show it.
- Kuwait defaults unless the file says otherwise: amounts in KWD with 3 decimals (e.g. 1,250.500 KWD), dates as DD/MM/YYYY, weekend Friday–Saturday.

## 5. Charts

3–5 charts, each answering one question in its title (e.g. «المبيعات نزلت ١٢٪ عن الشهر اللي طاف» — a title that states the finding, not «Sales chart»).
- Bar for comparing categories (sorted), line for time, never pie with more than 4 slices, no 3D.
- One accent color for the point you're making, grey for the rest. Label values directly; no legend when one series.
- Arabic text in charts must be shaped and right-to-left (use arabic_reshaper + python-bidi, or put Arabic only in the document text and keep chart labels in English).

## 6. Deliver

1. **Clean Excel file** — `<name>_clean.xlsx`: a **Summary** sheet first (the key numbers + native Excel charts via openpyxl), then the cleaned **Data** sheet as a proper table with filters and frozen header, then a **Cleaning log** sheet.
2. **The report** in the chosen format, one to two pages: title and period · 3–5 bullet executive summary (finding first, number second) · the charts · a short "what to watch / next step" section · the notes (assumptions and anything that couldn't be calculated).
3. **Message to the manager** — 4–6 lines, ready to paste in email or WhatsApp, in the report's language, with the 2–3 most important numbers.
4. If you can run code, re-open every file you produce and check: it opens, charts render, Arabic reads right-to-left, totals match.

If you can't run code: give the summary numbers you can compute from what's pasted, the cleaning steps as a checklist, and exact Excel steps (PivotTable / chart type / formula) for the user to build it.

End with one line: «تبي نفس التقرير كل شهر؟ ارسل الملف الجاي بنفس المحادثة.» (or the English equivalent).

## Never

- Invent numbers, fill missing values with guesses, or "smooth" data without saying so.
- Delete rows that aren't exact duplicates or totals without asking.
- Include personal data (civil ID, phone numbers, salaries of named people) in charts or the manager message unless the user asks.
- Bury the finding — the first line of the report says what happened.
