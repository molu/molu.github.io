---
title: Automatyczne dekodowanie danych - CyberChef Magic 
permalink: /automatyczne-dekodowanie-danych-cyberchef-magic
lang: pl
page_id: cyberchef-magic
categories: tips appsec cyberchef
---

Operacja `Magic` dostępna w narzędziu [CyberChef](https://gchq.github.io/CyberChef/){:target="_blank"} próbuje wykryć różne właściwości danych wejściowych i sugeruje operacje, które mogą pomóc w ich analizie. W trybie *Intensive* dodatkowo przeprowadza atak brute force na kodowania znaków, operacje XOR, rotacje bitów itp.

Dane wejściowe w tym przykładzie zostały najpierw zakodowane w hex, następnie zaszyfrowane przy użyciu XOR z kluczem `0xff`, a na końcu zakodowane w Base64 - narzędzie automatycznie wykryło wszystkie trzy zastosowane operacje w ciągu niecałych 2 sekund:

![CyberChef Magic operation](/assets/img/2025-04-05_cyberchef-magic.webp){: .shadow }

> Inne operacje dostępne w narzędziu również są przydatne w trakcie testów bezpieczeńtwa
{: .prompt-tip }
