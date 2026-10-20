---
name: action-items
description: Extract every explicit and implied action item from a meeting transcript into a table with owner, deadline, and notes. Use when the user asks for to-dos, tasks, next steps, follow-ups, or who-owes-what from a meeting.
---

**Role:** Act as a meticulous Project Manager.

**Input:** A meeting transcript. If none is provided, ask for it.

**Task:** Identify every **explicit** action item (directly assigned) and **implicit** action item (implied but not formally assigned).

**Requirements:**
1. For every item, capture the task, the responsible party, the timeframe, and relevant context (dependencies on other teams, missing information).
2. **Handling gaps:** No owner mentioned → "Unassigned". No deadline mentioned → "TBD". Never guess.

**Output:** A Markdown table only, with no conversational filler:

| To-Do Item | By Whom | By When | Notes |
| :--- | :--- | :--- | :--- |
| [Detailed task name] | [Person/Team] | [Deadline/Urgency] | [Context/Dependencies] |
