---
name: resume-application-tracker
description: "Use guided questions to build and audit a résumé, find suitable résumé templates, generate a verified résumé, fill campus-job forms, and archive delivery records while preserving evidence, schema, and visual formatting."
---

# Resume Application Tracker

Use this skill for requests to fill a résumé or campus-job application form, read the currently open application/delivery-record page, or archive delivery records in the user's tracker workbook. It supports preparation and draft saving; it does not authorize final submission.

## Work modes

Choose the smallest mode that satisfies the request. Combine modes when the user asks for a full résumé refresh.

- **问答补全与简历审核**: gather missing facts one question at a time, then assess the current résumé and propose evidence-bounded improvements.
- **模板检索与简历生成**: translate the user's layout and usage preferences into template criteria, shortlist traceable templates, and generate a new résumé copy from verified facts.
- **网申填写与投递存档**: use the existing browser and tracker workflows below.

## Operating boundary

- A direct request such as “填简历” means start filling immediately. Do not ask whether the user wants the form filled again.
- Filling fields, saving a draft, and uploading explicitly requested attachments are in scope. Clicking a final action such as “立即投递”, “提交申请”, “预览并提交”, or accepting a legal declaration requires a fresh confirmation immediately before that action.
- Never infer unknown dates, ranks, locations, salaries, statuses, or company facts. Leave an optional field blank; use `待核验` or `未找到可核验直投入口` only in the tracker when a status placeholder is needed.
- Keep the user's latest stated scope and exclusions. In particular, do not silently add old or excluded projects.

## Guided résumé intake and audit

Use this mode when the user asks to make a résumé through Q&A, review strengths and weaknesses, or assess a current résumé.

1. Start from the user's current résumé or other explicitly named source. First list what is already known and what is missing; do not ask the user to repeat facts already visible in the source or prior answers.
2. Ask at most one easy, high-impact question per turn. Prioritize missing facts that block accuracy or materially affect fit, such as target role, employment dates, project outcome, location preference, language score, or desired résumé length. Record the answer before asking the next question.
3. Maintain three distinct buckets: verified facts, user-confirmed wording, and suggestions. Never turn a suggestion or inference into a fact. Unknown dates, metrics, rankings, or responsibilities remain blank or are explicitly marked for the user to complete.
4. Audit the current résumé on five axes: completeness of sections, internal consistency of dates/titles/locations, evidence and outcome strength, relevance to the target role, and readability/ATS robustness. Check for omissions, duplication, vague claims, unexplained gaps, unsupported seniority, and formatting defects.
5. Present the audit as strengths, weaknesses/risks, and prioritized edits. For role-specific review, map each important job requirement to supporting evidence or a clearly labeled gap. Do not invent keywords, metrics, or experience merely to increase a match score.
6. When the user approves edits, update only the requested copy or a new draft. Preserve the original résumé as the source of truth and re-run the same completeness and consistency checks after editing.

## Template discovery and résumé generation

Use this mode when the user asks to find a suitable résumé template or create a résumé using one.

1. Collect only the preferences needed to choose a template: target role/industry, language, one-page or two-page length, ATS-first versus visual style, preferred colors or typography, region, and desired output format (DOCX/PDF or another specified format). Ask one question at a time and reuse already known preferences.
2. Search the local workspace for existing templates and reference résumés first. If external templates are requested, use an appropriate web-search workflow, preserve the source URL, and prefer editable templates with clear provenance and usage terms. Do not upload personal résumé data to a third-party template site unless the user explicitly asks.
3. Evaluate each candidate against the user's preferences, section support, editability, ATS/readability, visual density, and privacy or licensing risks. Return a short shortlist with the tradeoff and source link for each; do not silently choose a template when the differences would materially change the result.
4. After a template is selected, populate it only with verified résumé facts and user-approved wording. The template controls layout, not the truth of the content. Keep the original résumé unchanged and save the generated version as a separate, clearly named copy unless the user explicitly requests an overwrite.
5. For DOCX output, load the documents skill and follow its render-and-inspect workflow for every page. For PDF output, load the PDF skill and visually verify every page. Check clipping, overlap, missing glyphs, section order, dates, links, and attachment/readability before delivery.
6. Re-run the résumé audit after generation and report any fields still missing, any content shortened for layout, the selected template/source, and the exact output file. Never claim a generated résumé is final until the rendered output has been inspected.

## Source and browser state

1. Start from the most recently focused browser tab. If the user says they are on a page or names a company, inspect that visible page first; do not close it or navigate away just to use a guessed URL.
2. Identify the application company, role, form sections, required errors, and visible current values before editing. Use the browser skill for browser control and keep the existing signed-in session.
3. Use the latest résumé source explicitly specified by the user. If no filename is given, discover the current résumé in the user's workspace. When a filename is specified, lock to that file and reconcile every section against it; do not merge another workspace résumé silently.
4. After each section, re-read visible field text and cards. Before claiming completion, re-read the whole visible form, required-field errors, attachment names, and save state. If a browser wrapper cannot set a file input, report that exact attachment limitation instead of pretending it was uploaded.

## Application-form workflow

Fill all applicable sections from the chosen résumé, adapting only wording that is clearly role-relevant:

- Basic information: use supplied facts only. Do not guess sensitive fields, gender, or work authorization.
- Education: include every source entry, including all verified education experiences. If a site requires a full date and only a month is known, use day `01` for education dates; do not invent days for internships or projects. Leave unknown ranking/GPA fields blank.
- Internships and projects: include all relevant source entries with correct company/role/date pairing. Add a project only when supported by the source or the user's explicit instruction; do not fabricate metrics.
- Awards: create one award per entry. Add a short project description only when the source provides a related project; otherwise leave the description blank.
- Languages and skills: keep language scores together but keep technical skills in separate, readable groups instead of one undifferentiated list. Preserve the user's latest verified scores.
- Self-evaluation: tailor emphasis to the job while remaining evidence-bounded. Do not inflate seniority or turn a candidate into an unsupported specialist profile.
- Attachments: upload only files explicitly supplied or requested (for example the chosen résumé PDF, photo, transcript, or patent). Verify the displayed filename after upload.

Save the draft if the page provides a save action. Stop before final submission and report what is filled and any fields or uploads that remain unresolved.

## Delivery-record archive workflow

When the user asks for `存档`, begin the progress update with the exact phrase `我需要注意格式`.

1. Use the user's original tracker workbook only. If multiple workbooks exist, prefer the one explicitly named by the user or the one already used for the current tracker; do not create a second tracker or rename/reorder its columns.
2. Before editing, inspect and render the existing workbook. Preserve the established appearance: fills, borders, fonts, alignment, row heights, date/time formats, merged cells, filters, and the status/priority/match-score colors.
3. Use the fixed schemas:
   - `投递记录` A:S: `序号｜公司｜岗位全称｜岗位方向｜地点｜招聘项目/届别｜投递日期｜具体时间｜投递渠道｜内推码｜官网岗位链接｜当前状态｜优先级｜匹配度｜简历版本｜下次跟进日期｜跟进动作｜面试重点方向｜备注`
   - `面试准备` A:I: `公司｜岗位｜定位｜核心知识｜优先项目案例｜高频追问｜主要风险/补强｜准备状态｜目标日期`
4. Read the delivery page itself. If a role card can be opened, click into its detail and capture the exact title, location, status, date, time, channel, and link. Never substitute a search-result location or a guessed company address. Keep one role per row; distinct roles at the same company get distinct rows.
5. Update an existing matching company+role row rather than duplicating it. For a cancelled or rejected application, retain the row and apply the workbook's established strikethrough treatment to the row or status text, matching the original style. Do not delete historical applications unless the user explicitly asks.
6. Write dates and times as sortable values where supported, keep unknowns blank/`待核验`, and retain the original résumé-version and follow-up conventions.
7. After writeback, read the changed range and render the affected sheet(s). Verify values, formulas, row height, borders, fills, fonts, alignment, date display, and status/priority/match colors against neighboring original rows. Check for formula errors and confirm the workbook remains a single original file.

For spreadsheet authoring, load and follow the spreadsheet skill; use its artifact-tool and render/inspect verification requirements. Keep source URLs in the workbook when available so each archived row is traceable.

## Completion report

Report the exact file changed, rows added/updated, any facts left blank or marked `待核验`, and whether final submission was intentionally not performed. Do not claim a browser save, upload, or workbook writeback that was not re-read and verified.
