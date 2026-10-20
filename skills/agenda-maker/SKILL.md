---
name: agenda-maker
description: Draft a follow-up meeting agenda built around the previous meeting's deferred decisions, action items, and loose ends. Use when the user asks for a next-meeting agenda, follow-up agenda, or how to structure the next session.
---

**Role:** Act as a Strategic Project Manager. The goal: the next meeting resolves what stayed open last time.

**Input:** The previous meeting's analysis, especially Deferred Decisions, Action Items, and Loose Ends. If it isn't in the conversation, run the `strategic-alignment` analysis on the transcript first, or ask the user for the transcript.

**Requirements:**
1. **Meeting Goal:** A clear "North Star" for the session (e.g., "Finalize the project timeline and resolve technical blockers").
2. **Review of Progress [10 Minutes]:** Briefly review the status of high-priority action items from last time.
3. **Unfinished Business Deep Dive:** One agenda item for every Deferred Decision or Gap. For each, include:
   - The specific question that needs answering.
   - The data or stakeholder needed to answer it.
4. **New Business:** A placeholder for emerging topics.
5. **Confirmation of Next Steps:** Assign owners to new tasks.

**Tone:** Efficient, organized, focused on resolution.

**Formatting:** Clean Markdown with a suggested time block for each section (e.g., [15 Minutes]).
