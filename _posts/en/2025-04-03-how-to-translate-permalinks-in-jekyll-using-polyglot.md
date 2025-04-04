---
title: How to translate permalinks in Jekyll using Polyglot
permalink: /how-to-translate-permalinks-in-jekyll-using-polyglot
lang: en
page_id: translate-permalinks
categories: tips jekyll
---
To install the `jekyll-polyglot` plugin - add the following to your `Gemfile`:

```rb
group :jekyll_plugins do
  gem "jekyll-polyglot"
end
```

Install the plugin: `bundle install`.

Add `name` attribute to each locale file inside `_data/locales/`. This name will be displayed in switcher.

Create `lang-switcher.html` in `_includes`:

{% raw %}
```liquid
<!-- language switcher -->
<hr>
<ul style="list-style-type: none">
{% for lang in site.languages %}
  <li>
    <i class="fa-regular fa-flag" style="margin: 5px"></i> 
    <a class="lang-name" {% static_href %}href="{{ site.baseurl }}{% if lang != site.default_lang %}/{{lang}}{% endif %}{{ page.permalink_lang[lang] | default: '/' }}"{% endstatic_href %}>
      {{ site.data.locales[lang].name }}
    </a>
  </li>
{% endfor %}
</ul>
```
{% endraw %}

> The `page` object has a rarely mentioned, but helpful `permalink_lang` attribute.
{: .prompt-info }

Include it somewhere (e.g. in `sidebar.html`):
{% raw %}
```liquid
{% include lang-switcher.html %}
```
{% endraw %}

And voila! Remember that your pages and posts should have `page_id` and `permalink` attributes. 

```md
---
layout: page
icon: fas fa-info-circle
order: 4
title: About
page_id: about
permalink: /about/
---
```