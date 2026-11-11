---
layout: default
title: IT support
permalink: /it-support/
---
{% assign it = site.data.it_support %}
<div class="it-flow">

<div class="prose narrow">
  <h1>IT support</h1>
  <p>Need help, or have an idea to make things better? Choose what it's about, check what to have ready, then lodge the form. It takes about 3 minutes.</p>
</div>

<aside class="urgent" aria-label="Urgent help">
  <p class="urgent-title">Urgent? Don't use the form.</p>
  <p>If you clicked a suspicious link, your device is lost or stolen, or nobody in your team can work, contact IT straight away{% if it.urgent_phone != "" %} on <a href="tel:{{ it.urgent_phone | remove: ' ' }}"><strong>{{ it.urgent_phone }}</strong></a>{% endif %}{% if it.urgent_email != "" %} or <a href="mailto:{{ it.urgent_email }}">{{ it.urgent_email }}</a>{% endif %}.</p>
</aside>

<!-- ======================= STEP 1: CHOOSE ======================= -->
<section class="it-chooser" id="start" aria-labelledby="choose-title">
  <ol class="steps" aria-label="Progress">
    <li class="is-current">Choose</li><li>Get ready</li><li>Lodge the form</li>
  </ol>
  <h2 id="choose-title">What do you need help with?</h2>

  <div class="it-grid">
    {% for cat in it.categories %}
    <a class="it-card" href="#{{ cat.id }}">
      <span class="it-card-title">{{ cat.title }}</span>
      <span class="it-card-summary">{{ cat.summary }}</span>
      {% if cat.examples %}<span class="it-card-eg">e.g. {{ cat.examples }}</span>{% endif %}
      <span class="it-card-go" aria-hidden="true">&rarr;</span>
    </a>
    {% endfor %}
  </div>

  <h2>Got an idea?</h2>
  <a class="it-card it-card-idea" href="#improvement">
    <span class="it-card-title">Suggest an improvement</span>
    <span class="it-card-summary">A task that could be quicker, a tool that would help, or something that could work better.</span>
    <span class="it-card-go" aria-hidden="true">&rarr;</span>
  </a>
</section>

<!-- =================== STEP 2: ONE PANEL PER CATEGORY =================== -->
{% for cat in it.categories %}
{% assign form_url = cat.form_url | default: it.ticket_form_url %}
<section class="it-step" id="{{ cat.id }}" aria-labelledby="{{ cat.id }}-title">
  <p class="back"><a href="#start">&larr; Choose a different category</a></p>
  <ol class="steps" aria-label="Progress">
    <li class="is-done">Choose</li><li class="is-current">Get ready</li><li>Lodge the form</li>
  </ol>
  <span class="label">IT support request</span>
  <h2 class="it-step-title" id="{{ cat.id }}-title">{{ cat.title }}</h2>
  <p>{{ cat.summary }}</p>

  {% if cat.notice %}<p class="it-notice">{{ cat.notice }}</p>{% endif %}

  <div class="it-cols">
    <div class="it-panel">
      <h3>Have this ready</h3>
      <ul class="checklist">
        {% for item in cat.have_ready %}<li>{{ item }}</li>{% endfor %}
      </ul>
    </div>
    <div class="it-panel">
      {% if cat.forms %}
      <h3>The forms will ask</h3>
      {% for f in cat.forms %}
      <p class="asks-form"><span class="form-num">{{ forloop.index }}</span> {{ f.title }}</p>
      <ol class="asks">
        {% for a in f.asks %}<li>{{ a.q }}{% if a.options %}<span class="opts">{{ a.options }}</span>{% endif %}</li>{% endfor %}
      </ol>
      {% endfor %}
      {% else %}
      <h3>The form will ask</h3>
      <ol class="asks">
        {% unless cat.skip_common %}{% for a in it.common_asks %}<li>{{ a.q }}{% if a.options %}<span class="opts">{{ a.options }}</span>{% endif %}</li>{% endfor %}{% endunless %}
        {% for a in cat.form_asks %}<li>{{ a.q }}{% if a.options %}<span class="opts">{{ a.options }}</span>{% endif %}</li>{% endfor %}
      </ol>
      {% endif %}
    </div>
  </div>

  <div class="it-submit">
    <ol class="steps" aria-label="Progress">
      <li class="is-done">Choose</li><li class="is-done">Get ready</li><li class="is-current">Lodge the form</li>
    </ol>
    {% if cat.forms %}
    <p>Fill these in <strong>in order</strong>. Each opens Microsoft Forms in a new tab. Sign in with your Coho work account.</p>
    <ol class="form-steps">
      {% for f in cat.forms %}
      <li class="form-step">
        <span class="form-num" aria-hidden="true">{{ forloop.index }}</span>
        <div class="form-step-body">
          <strong>{{ f.title }}</strong>
          {% if f.when %}<span class="meta">{{ f.when }}</span>{% endif %}
        </div>
        <a class="button" href="{{ f.url }}" target="_blank" rel="noopener">Open form {{ forloop.index }}</a>
      </li>
      {% endfor %}
    </ol>
    {% elsif form_url != "" %}
    {% if cat.form_url %}<p>This opens the <strong>{{ cat.title }}</strong> form. {% if cat.sign_in %}Sign in with your Coho work account.{% else %}You don't need to sign in.{% endif %}</p>{% else %}<p>When the form asks what you need help with, choose <strong>{{ cat.title }}</strong>.</p>{% endif %}
    <a class="button" href="{{ form_url }}" target="_blank" rel="noopener">Open the form</a>
    <p class="meta">Opens Microsoft Forms in a new tab.</p>
    {% else %}
    <p class="it-notice"><strong>The support form is coming soon.</strong> Until then, email {% if it.urgent_email != "" %}<a href="mailto:{{ it.urgent_email }}?subject={{ cat.title | url_encode }}">{{ it.urgent_email }}</a>{% else %}<a href="mailto:{{ site.contact_email }}?subject={{ cat.title | url_encode }}">{{ site.contact_email }}</a>{% endif %} with the details above.</p>
    {% endif %}
  </div>

  <div class="it-next">
    <h3>What happens next</h3>
    <ol>
      <li>You'll get a confirmation that your request has been received.</li>
      <li>IT will contact you if they need more detail.</li>
      <li>We'll let you know when it's sorted.</li>
    </ol>
  </div>
</section>
{% endfor %}

<!-- ======================= IMPROVEMENT REQUEST ======================= -->
<section class="it-step" id="improvement" aria-labelledby="improvement-title">
  <p class="back"><a href="#start">&larr; Back to IT support</a></p>
  <span class="label">Improvement request</span>
  <h2 class="it-step-title" id="improvement-title">Suggest an improvement</h2>
  <p>Got a repetitive task that could be automated, a tool that would save time, or a process that could work better? We'd like to hear it. Every idea is read, and the best ones are shared in the news updates.</p>

  <div class="it-cols">
    <div class="it-panel">
      <h3>Good ideas often start with</h3>
      <ul class="checklist">
        <li>"I do this by hand every week…"</li>
        <li>"We type the same information into two places…"</li>
        <li>"It takes ages to find…"</li>
        <li>"Our clients keep asking for…"</li>
      </ul>
    </div>
    <div class="it-panel">
      <h3>Helpful to include</h3>
      <ul class="checklist">
        <li>What happens today</li>
        <li>What would be better</li>
        <li>Who it would help and how much time it could save</li>
      </ul>
    </div>
  </div>

  {% if it.improvement.form_url != "" %}
  {% if it.improvement.embed %}
  <div class="form-frame">
    <iframe src="{{ it.improvement.form_url }}&amp;embed=true" title="Improvement request form" loading="lazy" referrerpolicy="strict-origin-when-cross-origin">Loading the form…</iframe>
  </div>
  {% endif %}
  <p class="center"><a class="button{% if it.improvement.embed %} button-ghost{% endif %}" href="{{ it.improvement.form_url }}" target="_blank" rel="noopener">{% if it.improvement.embed %}Form not showing? Open it in a new tab{% else %}Open the improvement form{% endif %}</a></p>
  {% endif %}
</section>

</div>
