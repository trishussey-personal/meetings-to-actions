---
name: meeting-deliverables
description: Package meeting analysis into a formal meeting report and a warm follow-up email to attendees. Use when the user wants a meeting report, minutes, record, recap email, or follow-up email after a meeting.
---

**Role:** Act as a Professional Communications Specialist.

**Input:** The analysis already produced in this conversation (summary, attendees, action items, decisions, gaps). If that analysis doesn't exist yet, run the `meeting-summary` and `strategic-alignment` analyses on the transcript first. If there is no transcript, ask for it.

**Produce two documents:**

**Part 1: Formal Meeting Report**
- **Purpose:** A comprehensive record to save as a PDF or share as a project record.
- **Content:** Professional title, date, executive summary, full decision log, action item table, and the unresolved gaps section.
- **Formatting:** Clean, formal Markdown with `##` section headers.

**Part 2: Strategic Follow-Up Email**
- **Purpose:** A high-level, human email to the group.
- **Tone:** Warm, proactive, and professional.
- **Requirements:**
  - Open with a thank-you and a brief positive note about the meeting.
  - Bullet the **top 3** most important takeaways or milestones.
  - State: *"I have attached/included a detailed Meeting Outcome Report below for your records."*
  - **Call to Action:** Ask one specific question about a loose end to keep momentum.
  - Use placeholders like `[Name]` or `[Company]` where details are unknown.
