---
title: How to translate permalinks in Jekyll using Polyglot
permalink: /how-to-translate-permalinks-in-jekyll-using-polyglot
lang: en
page_id: translate-permalinks
---
To install the `jekyll-polyglot` plugin - add the following to your `Gemfile`:

```yaml
group :jekyll_plugins do
    gem "jekyll-polyglot"
end
```

Install the plugin: `bundle install`

Create `lang-switcher.html` in `_includes`:

{% raw %}
```html
<!-- language switcher -->
<hr>
<ul style="list-style-type: none">
{% for lang in site.languages %}
  <li>
    <i class="fa-regular fa-flag" style="margin: 5px"></i> 
    <a class="lang-name" {% static_href %}href="{{ site.baseurl }}{% if lang != site.default_lang %}/{{lang}}{% endif %}{{ page.permalink_lang[lang] | default: '/' }}"{% endstatic_href %}>
      {{ site.data.locales[lang].language }}
    </a>
  </li>
{% endfor %}
</ul>
```
{% endraw %}

> Note: the `page` object has `permalink_lang` attribute - this is something I missed while looking for solutions.

Include it somewhere (e.g. in `sidebar.html`):
{% raw %}
```html
{% include lang-switcher.html %}
```
{% endraw %}

And voila! Remember that your pages and posts should have `permalink` and `lang` attributes.