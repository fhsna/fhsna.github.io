---
title: Meeting Notes
permalink: /meeting-notes/
---

{% assign meetings = site.meetings | sort: "date" | reverse %}
{% for meeting in meetings %}
## {{ meeting.title }}
{: #meeting-{{ meeting.date | date: "%Y-%m-%d" }} }

{{ meeting.content }}

---

{% endfor %}
