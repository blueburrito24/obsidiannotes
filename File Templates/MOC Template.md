---
type: MOC
module_code: {{title}}
status: #active
---

# {{title}} Map of Content

> [!abstract] Module Objective
> Briefly summarize what this module is about and what the key learning outcomes are. This helps with "Directional Learning."

---

## 🗺️ Curriculum Map
*This section is for manually ordered links to follow the lecture sequence.*

- **Phase 1: Foundations**
	- [[Concept A]]
	- [[Concept B]]
- **Phase 2: Core Theory**
	- [[Concept C]]
- **Phase 3: Implementation**
	- [[Concept D]]

---

## 🧪 Concept Tracker (Automated)
*The list below automatically pulls in any note that links back to this MOC.*

```dataview
TABLE tags AS "Status/Type", subjects AS "Subject"
FROM [[{{title}}]]
WHERE type = "concept"
SORT file.name ASC