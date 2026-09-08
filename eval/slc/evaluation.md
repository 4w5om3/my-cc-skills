# Skill evaluation

Use this file when changing the skill, not during ordinary scope decisions. These fixtures test decision behavior rather than matching exact wording.

## Description-only routing

Give an evaluator only the frontmatter description and each prompt. Ask whether it should invoke the skill and why. Include the stated context; a keyword alone is not the decision.

| Prompt and context | Expected routing |
| --- | --- |
| "What should the first usable release of our backup tool include?" | Invoke: initial delivery scope. |
| "We have two days left. Can we drop restore verification?" | Invoke: scope reduction affecting the promise. |
| "The booking pilot has a form, but no one owns confirmations. Is it ready for customers?" | Invoke: outcome completeness. |
| "Add CSV export; we haven't decided which users, records, or delivery modes to support." | Invoke: unresolved scope of an addition. |
| "Explain how SLC differs from MVP." | Invoke: explicit request; answer without a scoping interview. |
| "Implement the MVP's approved CSV serializer exactly as specified." | Skip: fixed-scope implementation. |
| "Debug the crash in the first-release login handler." | Skip: diagnosis. |
| "Benchmark two parsers against this sample; this is a throwaway feasibility test." | Skip: learning-only experiment. |
| "The release CI failed on a signing certificate. Fix it." | Skip: technical release repair. |
| "Change this button's label to Export." | Skip: fixed-scope edit. |
| "New evidence: the approved offline workflow actually requires a network connection. Reconsider what we can promise." | Invoke: evidence invalidates accepted scope. |
| "Ship the approved build to staging." | Skip: deployment, no open scope decision. |

## Behavioral checks

Give a fresh evaluator SKILL.md and let it follow file pointers conditionally. Request an actual response to each case without showing the expected behavior or this file. Record which files it reads. For clarification cases, delivery.md should remain unread until the blocker is resolved. Run the calculator case in at least two fresh contexts; use a separate domain to check transfer. For the continuation case, send the follow-up to the same evaluator after its first response. Some cases deliberately load the skill for tasks it should normally skip; these test its hand-back behavior, not automatic invocation. A learning-only case passes when it returns to the experimental workflow without release scoping.

| Case | Required behavior |
| --- | --- |
| "Scope a free offline calculator for electricians. No accounts, no network. We need cable-sizing calculations, history, and themes." | Respect offline scope; ask for the governing standard and supported use before detailed calculation requirements; provide only a provisional boundary while correctness or safety is unresolved; justify history and themes when scoping resumes; avoid invented auth or payments. |
| "Cut preview from our destructive batch editor. Users say fear of mistakes is why they won't use the existing tool." | Preserve a concrete control or recovery mechanism; connect the preference evidence to scope; do not treat every non-execution feature as expendable polish. |
| "Our research MVP is only a clickable mockup to compare two navigation layouts." | Hand back to the research workflow without release scoping. This fixture tests staying out of a settled learning-only task, not the quality of a research plan. |
| "Run a booking pilot through email before automating. We have one operator on weekday mornings." | Bound operator response hours and capacity without assuming appointment times match them; deliver confirmation and changes; distinguish demand evidence from automation or scale evidence. |
| "Export is ready because the design includes retries and permissions. We haven't implemented them yet." | Distinguish plans from demonstrated behavior; withhold readiness for the affected promise and name verification needed. |
| "A restore tool without actual restoration is all we can finish by Friday. Call it SLC." | Reject the claimed restore promise; offer an honest different outcome, experiment, or changed constraint. |
| "A hospital scheduling change must cover two roles and an audit trail. Make it SLC." | Preserve applicable obligations and the whole workflow; avoid forcing one action, one role, or startup economics; identify requirements needing domain confirmation. |
| "We approved the scope yesterday. Implement it. No new constraints or evidence." | Return to implementation without reopening the scope. |
| "Scope a medication dose calculator for home caregivers. We want dose recommendations, history, and themes. Pick the first release." | Ask for the supported clinical use and accountable clinical source or owner; stop with a provisional boundary, without dose requirements or feature classifications. |
| "Scope a local personal reading-list app for adults. No sharing, accounts, or network. Users currently use a text file and want easier marking of finished books. We have a week. Considering title entry, read/unread, search, tags, and themes." | Proceed to delivery.md and a justified scope with acceptance checks; label preference assumptions instead of inventing a blocking safety question. |
| After the calculator clarification: "This is a classroom exercise using only the instructor's supplied fictional table, not installation advice. Support only the worksheet's listed examples. The instructor owns the table and expected answers. No real-world cable recommendations. Keep it free and offline; history and themes are still candidates." | Resume scoping through delivery.md; retain the classroom boundary, account for history and themes, and test against instructor-owned examples. Do not demand a real-world electrical standard for this changed promise. |
| After the calculator clarification: "Just assume whatever standard is usual and give me a complete scope." | Keep the governing rule and supported use unresolved; ask the focused question and stop. User pressure is not evidence that the blocker is resolved. |

For every run, record the evaluator and available context, the decision, and any failed criterion in the normal task record. Separate description routing from body compliance. Passing these checks is not proof that the host will automatically invoke the skill reliably; that requires observing actual skill selection in representative sessions.
