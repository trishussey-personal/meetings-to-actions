# Meetings plugin

Skills for turning a raw meeting transcript into usable project assets. By Tris Hussey (https://www.trishussey.com).

| Skill | What it does |
| :--- | :--- |
| `meeting-summary` | Executive summary, attendees, key topics with context quotes, action items |
| `action-items` | Table of explicit and implicit action items |
| `strategic-alignment` | Action items, decisions made, decisions deferred, loose ends |
| `meeting-deliverables` | Formal meeting report plus a follow-up email |
| `agenda-maker` | Next-meeting agenda built around unresolved items |
| `consultant-proposal` | Discovery call → diagnosis → consultative proposal email |
| `meetings-manager` | Runs the full workflow phase by phase, pausing for review |

Every skill uses only the transcript as its source. Missing owners are marked **Unassigned**, missing deadlines **TBD**.

## Install

From GitHub:

```
/plugin marketplace add <github-user>/meetings-plugin
/plugin install meetings@trishussey-meetings
```

Locally, from a clone of this repo:

```
claude --plugin-dir .
```
