---
name: campus-job-research
description: Research current Chinese campus-job openings for a specified candidate, verify official details and direct application links, deduplicate against an application tracker, score fit, and produce a concise structured brief. Use for recurring job-search monitoring, not for submitting applications.
---

# 校园岗位信息收集

Use this skill when the user asks for a job-search brief, new campus roles, high-quality internships, or a refresh of previously collected openings. The deliverable is evidence-backed and selective: collect current roles, verify them, filter them against the candidate profile and constraints, and present only actionable candidates.

## Candidate and standing constraints

Use the candidate profile supplied in the current task and any user-maintained resume/strategy documents. Do not embed one person's identity, resume, or local file paths in a portable copy of this skill. Treat early or partial internships conservatively: record completed work only and never turn planned learning into an achievement.

Honor the latest user constraints before ranking. Prioritize the role families and cities stated by the current candidate; if a workspace strategy document exists, read it before searching. Exclude pure sales, low-quality outsourcing, clear graduation/degree mismatches, and any newly excluded city or industry. Do not carry another candidate's exclusions into a portable copy, and do not recommend a role merely to fill a quota.

## Evidence-first collection workflow

1. Read the latest application tracker and relevant strategy/memory notes before searching. Identify company + role duplicates, roles already applied to, current statuses, and any new city/salary exclusions. Treat a prior application as excluded from the new list unless the posting has a verifiable material change.
2. Search for leads across official career sites, official recruiting accounts/pages, and trusted university employment boards. Aggregators and social posts are lead sources only; do not call a role actionable until an official or trusted-board posting confirms the role, eligibility, location, and current availability.
3. Verify each candidate on the most authoritative reachable page. Capture exact role title, location, cohort/graduation window, publication or closing date, requirements, salary/benefits, and company/location context. Re-check that the posting is current rather than a historical pool.
4. Keep job-detail and application-entry evidence separate. Link the exact detail page when available and separately link the direct application entry. If no verified direct entry exists, write `未找到可核验直投入口`; never infer or invent a URL. A generic company portal must be labeled as generic and require role selection.
5. Score fit using hard eligibility first, then technical match, role priority, company/platform, city, compensation, and growth. State the main positive evidence and the largest gap or uncertainty. Clearly label inferences such as a likely industrial-park commute judgment.
6. Compare against the previous brief and tracker. Mark each row as `今日新增`, `发生变更`, `在招无变化`, `已投递跟踪`, or `观察`. Do not re-push unchanged applied roles.

## Output contract

Respond in Chinese and use three groups: `今日优先投递`, `可考虑`, and `暂不建议`. Keep 5–10 high-quality roles when enough evidence exists; fewer is better than padding. Use one row per role and these fixed columns, in this order:

`公司｜岗位全称｜地点及环境｜招聘类型/届别｜发布时间或截止日期｜匹配度｜岗位方向｜推荐理由｜缺口/风险｜公司规模｜薪资福利｜相对上一期状态｜岗位详情｜立即投递`

Put concise interview-preparation focus in the recommendation cell when useful. Mark unknown company scale, environment, salary, deadline, or direct-entry status explicitly as `未公开`, `无法判断`, `待核验`, or `未找到可核验直投入口`. Separate locations that the user has excluded from otherwise multi-city campaigns instead of silently recommending them.

Start with a short conclusion naming the top few actions and the deduplication result. End with a source list containing the actual URLs used. State that final application submission remains under candidate control; preparation and form-filling may be assisted after the candidate chooses a role, but do not submit without fresh confirmation.

## Source and operational notes

- Prefer live web verification for dates, availability, salary, locations, and application links because they drift.
- If a search helper fails, use the available web tool as a fallback and disclose that no helper-generated search file was produced.
- Do not modify the tracker during a read-only brief unless the user explicitly asks to archive or update it.
- Locate an application tracker from the current workspace, the user's supplied path, or the current task. Do not hard-code a user-specific Windows path in a portable copy; preserve any existing tracker schemas when later asked to update one.
