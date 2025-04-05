---
title: Jekyll Polyglot - adresy w różnych językach
permalink: /jekyll-polyglot-permalinki-w-roznych-jezykach
lang: pl
page_id: translate-permalinks
categories: tips jekyll
---
Aby zainstalować plugin `jekyll-polyglot`, dodaj do `Gemfile`:

```rb
group :jekyll_plugins do
  gem "jekyll-polyglot"
end
```

Instalacja pluginu: `bundle install`.

Dodaj atrybut `name` z nazwą do wyświetlenia dla każdego języka w plikach z tłumaczeniami w folderze `_data/locales/`.

Następnie, utwórz `lang-switcher.html` w katalogu `_includes`:

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

> Obiekt `page` posiada rzadko wspominany w dokumentacjach, a przydatny atrybut `permalink_lang`.
{: .prompt-info }

Zaimportuj utworzony wcześniej plik HTML w dowolnym miejscu (np. w `sidebar.html`):
{% raw %}
```liquid
{% include lang-switcher.html %}
```
{% endraw %}

Gotowe! Pamiętaj, że Twoje strony i posty muszą posiadać atrybuty `page_id` i `permalink`.

```md
---
layout: page
icon: fas fa-info-circle
order: 4
title: O mnie
page_id: about
permalink: /o-mnie/
---
```