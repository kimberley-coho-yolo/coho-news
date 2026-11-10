---
layout: default
title: Ask a question
permalink: /ask/
---
<div class="prose narrow" markdown="1">

# Ask a question

No question is too small. If you're wondering about it, someone else probably is too. We answer common questions in the next update, without names.

**Please don't include passwords or bank details in this form.**

</div>

{% if site.form_embed_url != "" %}
<div class="form-frame">
  <iframe src="{{ site.form_embed_url }}" title="Question form" loading="lazy" referrerpolicy="strict-origin-when-cross-origin">Loading the form…</iframe>
</div>
{% if site.form_link_url != "" %}
<p class="center"><a class="button button-ghost" href="{{ site.form_link_url }}" target="_blank" rel="noopener">Form not showing? Open it in a new tab</a></p>
{% endif %}
{% else %}
<div class="notice">
  <p><strong>The question form is coming soon.</strong></p>
  <p>In the meantime, email {% if site.contact_email %}<a href="mailto:{{ site.contact_email }}?subject=Technology%20roadmap%20question">{{ site.contact_email }}</a>{% else %}the IT team{% endif %} or talk to your site champion.</p>
</div>
{% endif %}
