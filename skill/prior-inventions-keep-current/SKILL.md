---
name: prior-inventions-keep-current
description: Use when I finish building or designing something new (an app, tool, skill, prompt or method), or ask to add something to my Prior Inventions page.
---

# Prior Inventions: Keep It Current (version 2.0.2)

My request: "Keep my Prior Inventions page current as I build new things."

## My setup (fill these in once)

- My name: [YOUR FULL NAME]
- My Prior Inventions page: [PASTE THE LINK TO YOUR PRIOR INVENTIONS PAGE]
- My time zone: [YOUR TIME ZONE, A CITY IS FINE]

If any of these is still in square brackets, look among my artifacts for a page titled "[my name] - Prior Inventions" and use it. If you cannot find it, ask me once for the link.

Read and write my page's data with the artifact data tools (named ArtifactData in some sessions, and db_get, db_list and db_write in others; load them via ToolSearch if needed), using my page link. The page keeps each item as a document in the "items" collection, revision history rows in "revisions", and its version and my details in "settings/main".

## When this runs

- When I start building or designing something new: do step 1.
- When I finish a new build or design, or say "add this to my Prior Inventions": do steps 2 to 5.
- When I make a material change to something already on my list: do step 1 for the change, then offer to update its Register entry.
- When I say "Update my Prior Inventions skill" or "Update my Prior Inventions page": follow "Updates" below.

## 1. Document control on every new build

Every new build gets a document control block and a dated revision history, at the top of its design document, or at the top of the doc or page itself if it is one.

- Document control is a two-column table (Field, Value): Document ID, Owner, Classification, Current version, Status, Review cycle and Time zone.
- The revision history is a table with the columns Version, Date, Time, Author, Description of change and Approved by, listed oldest first. Times are in my time zone.
- The version is 0.1 while the design is worked out, then 0.2, 0.3 and so on. It becomes 1.0 when I approve it.
- After 1.0, add a row only for a material change: a change to what the item does or how it works. Wording fixes, styling and small corrections do not get a row.

## 2. Ask before adding

When I finish, ask me one question: "Do you want to add [item name] to your Prior Inventions page?" If I say no, stop.

## 3. Draft the entry

1. List the "items" collection on my page.
2. If the item is already on the list, or is a new version of an item on it, say so. Offer to update that item, or to add a sub-item under it (for example S-01.21), instead of adding a new one.
3. Otherwise give it the next free ID in its group. M is for methodologies, S for software built and D for designed, not built. Never reuse an ID, including any listed in "retiredIds" in settings/main.
4. Date it from records. Conceived is the earliest dated record of the idea, and Built is the earliest dated record of a working version. Link each date to its record, such as this chat or the published artifact. Follow the rules below.
5. Suggest In, Out or Discuss, with a one-line reason. Anything built as part of a job is not a prior invention, so suggest Out. If settings/main has an employment start date and this item came after it, tell me it may belong to my employer, suggest Discuss and draft a question for the legal counsel list.
6. Show me the entry exactly as it will appear, and wait for my approval.

## 4. After I approve

1. Write the item with op "set" to "items/<id in lowercase, with hyphens for dots>" (for example s-01-21): id, type ("M", "S" or "D"), parent (the parent ID or ""), name, what, conceived and built (each {text, url, label}; text is a date such as "13 Mar 2026", "On or before 2 Oct 2026" or "Confirm"; label is neutral link text), include, notes, createdAt.
2. If it is In, also write problem, value, how, apart, related (IDs and item names only) and exhibitDesc (one or two general sentences with nothing confidential).
3. Add a revision row with op "set" to "revisions/r-<timestamp>": version (the next minor version after docVersion in settings/main, such as 1.3 after 1.2), date (YYYY-MM-DD), time (HH:MM in my time zone), author "Claude, at [my name]'s direction", description "Added [ID] [item name]", approvedBy [my name], order (the timestamp). Then update settings/main docVersion to match.
4. Check what you added against the rules below.

## 5. Design document (optional)

Ask whether I want a design document for the item. If I do, create it as a Claude doc titled "[my name] - [ID] [item name] - Design". Include document control, a revision history, dated milestones (Date, Milestone and Record that proves it), Purpose, Value, How it works, related items (ID and Item only), To confirm and Sources. Add its link to the item's designDocs list as {label: "Design document", url}.

## Rules

- Never invent a date. When the only record shows that something existed by a date, write "On or before" that date. When there is no dated record, write "Confirm" and ask me. An exact date or a range I am confident of is fine.
- Link text says what the record is and its date, in neutral words, such as "Claude chat, 13 Mar 2026". Never use a chat's, file's or artifact's own title as link text.
- Only date the item itself. Leave out records that show it being used, shown to someone or reworked later.
- Name no people other than me. Say "legal counsel", "a client" or "a contact" instead.
- Company and client names appear only in the legal counsel list. They never appear in the Register fields, the Exhibit description, a related-item list or a design document.
- The Exhibit description is general, with nothing confidential and no links.
- Write in plain, connected sentences, with no em dashes.

## Updates

When I say "Update my Prior Inventions page": get document "settings/tasks" on my page. If it has an "update" task ID, write document "activity/a-<timestamp>" with kind "update", label "Update to the latest version", status "running" and startedAt ISO now. Then start that scheduled task with a two-line message: "ACTIVITY ID: a-<timestamp>" on the first line and "MODE: APPLY UPDATE" on the second. Tell me to reload my page when the notification arrives. If there is no task, or you cannot start it, follow the APPLY MODE steps in https://raw.githubusercontent.com/RevCeleris/prior-inventions/main/tasks/update.txt yourself, with my page link and time zone, skipping any step about a scheduled task.

When I say "Update my Prior Inventions skill", download https://raw.githubusercontent.com/RevCeleris/prior-inventions/main/skill/prior-inventions-keep-current/SKILL.md with the Bash tool using curl -fsSL (or WebFetch if curl fails). Offer it to me as an update to this skill, keeping the values I filled in under "My setup". After I save it, update settings/update on my page with skillInstalled set to the version in the new skill's title.

## Reply to me

Keep it short: one line saying what you added, with the link to my page, then anything I need to confirm.

---

Prior Inventions Keep It Current skill, version 2.0.2. (c) 2026 Rich Henderson. Shared under CC BY-NC 4.0: free to use and adapt for your own records, with credit. Not for resale or use in a paid product. Not legal advice.
