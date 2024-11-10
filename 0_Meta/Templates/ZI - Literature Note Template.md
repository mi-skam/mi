---
in:
  - "[[Literature]]"
aliases: ["
      {%- if creators -%}
          {{creators[0].lastName}}
          {%- if creators|length > 1 %} et al.{% endif -%}
      {%- endif -%}
      {%- if date %} ({{date | format("YYYY")}}){% endif -%}
      {%- if shortTitle %} {{shortTitle | safe}} {%- else %} {{title | safe}} {%- endif -%}
"]
by: [{% for a in creators %}{{a.firstName}} {{a.lastName}}{% if not loop.last %}, {% endif %}{% endfor %}]
created: {{importDate | format("YYYY-MM-DD")}}
citekey: {{citekey}}
year: {{date | format("YYYY")}}
tags: [literature, {% for t in tags %}{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]

---
# {{citekey}}

Literature Note: [[{{title}}]]
URL: {{url}}
DOI: {{doi}}
Zotero Link: {{pdfZoteroLink}}

\```ad-abstract
title: Abstract
{{abstractNote}}
\```
{% for n in notes %}{% for t in n.tags %}{% if t.tag == "relevance" %}
```ad-seealso
{{n.note}}
\```
{% endif %}{% endfor %}{% endfor %}
## Annotations
{% persist "annotations" %} {% set annots = annotations | filterby("date", "dateafter", lastImportDate) %}
{% if annots.length > 0 %} {% for annot in annots %} {% if annot.annotatedText %} {% if annot.color == "#ffd400" %}
\```ad-main
title: Main Idea
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#f19837" %}
\```ad-explain
title: Extra Info
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#a28ae5" %}
```ad-definition
title: Definition
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#aaaaaa" %}
\```ad-thought
title: Thoughts
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#ff6666" %}
\```ad-question
title: Question
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#2ea8e5" %}
\```ad-reference
title: Further Resources
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#5fb236" %}
\```ad-research
title: Research Idea
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% elif annot.color == "#e56eee" %}
\```ad-fun
title: For Fun
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% else %}
\```ad-error
> {{annot.annotatedText}}

{% if annot.comment %}
{{annot.comment}}
{% endif %}
\```
{% endif %} {% endif %} {% endfor %} {% endif %} {% endpersist %}
