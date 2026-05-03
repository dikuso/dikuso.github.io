Jekyll Portfolio Engineering Guide & Checklist
This guide outlines the Layout Chain logic you've successfully identified and provides a repeatable checklist for adding new technical sections to your portfolio.

1. The Architecture Logic (The Layout Chain)
---------------------------------------------------------------------------------------------------------------------------
Your site uses a modular approach to connect the homepage to specific deep-dive pages. The flow follows this sequence:

Homepage Trigger: _layouts/home.html includes a summary component (e.g., data_ai_journey_summary.html).

Routing: The summary links to a root folder (e.g., /data-ai-journey/).

Folder Entry: Jekyll reads the index.md inside that folder.

Layout Selection: The index.md front matter specifies layout: page and a unique type (e.g., type: datascience).

Conditional Rendering: _layouts/page.html checks the type and includes the corresponding detailed content file from _includes/.

------------------------------------------------------------------------------------------------------------------
2. Checklist: Adding a New Section
Use these steps to add a new category (e.g., "Cloud Security") to your site.

Phase A: The Homepage Summary
------------------------------
-----------------------------
[ ] Create a new file: _includes/home_sections/topic_summary.html.

[ ] Add a <section class="section-block"> with a link to /topic-folder/.

[ ] Insert {% include home_sections/topic_summary.html %} into _layouts/home.html.

Phase B: The Content Routing
---------------------------------
------------------------------------
[ ] Create a new folder at the root: /topic-folder/.

[ ] Create an index.md inside that folder with the following front matter:

YAML
---
layout: page
title: "Title"
type: unique_topic_name
---

Phase C: The Layout Logic
------------------------------------------
-------------------------------------
[ ] Open _layouts/page.html.

[ ] Add an elsif block for your new type:

Code snippet
{% elsif page.type == "unique_topic_name" %}
  <h2>Section Heading</h2>
  {% include topic_detailed_content.html %}
  
Phase D: The Detailed Content
------------------------------------------
------------------------------------------
[ ] Create _includes/topic_detailed_content.html and add your technical projects and descriptions.
