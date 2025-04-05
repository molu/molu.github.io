---
title: Auto data decode with CyberChef Magic
permalink: /auto-data-decode-with-cyberchef-magic
lang: en
page_id: cyberchef-magic
categories: tips appsec cyberchef
---

The `Magic` operation available in [CyberChef](https://gchq.github.io/CyberChef/){:target="_blank"} attempts to detect various properties of the input data and suggests which operations could help to make more sense of it. In *Intensive mode* it also performs brute force of character encodings, XOR, bit rotates, etc.

Input data used in this example was first encoded as hex, then encrypted with XOR with `0xff` key and finally Base64 encoded - the tool automatically detected all three operations performed in less than 2 seconds:

![CyberChef Magic operation](/assets/img/2025-04-05_cyberchef-magic.webp){: .shadow }

> Other operations available in the tool are also useful during security testing.
{: .prompt-tip }
