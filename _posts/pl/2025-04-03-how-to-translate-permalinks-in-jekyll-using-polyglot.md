---
title: Jekyll Polyglot - permalinki w różnych językach
permalink: /jekyll-polyglot-permalinki-w-roznych-jezykach
lang: pl
page_id: translate-permalinks
---
Aby zainstalować plugin `jekyll-polyglot`, dodaj do `Gemfile`:

```yaml
group :jekyll_plugins do
    gem "jekyll-polyglot"
end
```

Instalacja pluginu: `bundle install`

Następnie, utwórz `lang-switcher.html` w katalogu `_includes`:

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

> Uwaga: objekt `page` posiada atrybut `permalink_lang` - nie jest to chyba wymienione w żadnej dokumentacji.

Zaimportuj utworzony wcześniej plik HTML w dowolnym miejscu (np. w `sidebar.html`):
{% raw %}
```html
{% include lang-switcher.html %}
```
{% endraw %}

Gotowe! Pamiętaj, że Twoje strony i posty muszą posiadać atrybuty `permalink` i `lang`.