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

---

![Desktop View](/images/web_vulnerabilities/clickjacking/clickjacking_02.png){: .shadow }


## Exploitation

**Basic Payload**

```html
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
```
{: file='Clickjacking.html'}


### **Steps in the Attack:**

#### **1. Reconnaissance**  
The attacker identifies a target online banking platform that lacks adequate protections against clickjacking, such as `X-Frame-Options` or `Content Security Policy`. The attacker notes that the bank’s transfer confirmation button is exposed in its HTML structure.

#### **2. Creating the Malicious Page**  
The attacker creates a fraudulent webpage containing:  
- An iframe embedded with the bank’s fund transfer confirmation page.  
- The iframe is styled to be completely transparent.  
- A fake, enticing button (e.g., “Click here to claim your reward!”) is positioned directly over the confirmation button in the transparent iframe.

#### **3. Launching the Attack**  
The attacker lures the victim to visit the malicious webpage using phishing techniques, such as:  
- A promotional email or message offering a reward, free gift, or exclusive content.  
- A shortened or obfuscated link redirecting the victim to the attacker’s webpage.

#### **4. Victim Interaction**  
- The victim opens the malicious webpage and sees the fake button labeled with a compelling call-to-action, such as “Claim your $100 bonus!”  
- Without suspecting foul play, the victim clicks on the visible button.  
- The click passes through to the transparent iframe, activating the real “Confirm Transfer” button on the bank’s website.  
- The victim unknowingly authorizes a transfer of funds to the attacker’s account.


---

## How to find 
you should focus on pages that contain sensitive functions such as:
- Login.
- Changing passwords.
- Confirm transactions (such as transferring money).
- Account settings.


#### **Method 01: Try to embed the page in an iframe:**
- Create a simple HTML page with an iframe pointing to the target site:

```html
<html>
<body>
<h1>Testing Clickjacking</h1>
<iframe src="https://targetwebsite.com" width="800" height="600"></iframe>
</body>
</html>
```
{: file='Clickjacking.html'}

- Open this file in your browser.
- **If the page appears inside the frame, it is vulnerable.**
- **If an error message appears or the page does not appear, protection may be enabled.**


#### **Method 02: Burp Suite:**
- Scan the response to check for `X-Frame-Options` and `CSP` settings.



---

### **Preventive Measures**  
For Website Owners:  
- Implement `X-Frame-Options: DENY` or `SAMEORIGIN` headers to prevent your site from being embedded in iframes.  
- Use **Content Security Policy (CSP)** to restrict iframe embedding to trusted sources.  
- Design user interfaces with an additional layer of verification for sensitive actions, such as CAPTCHA or re-authentication.

For Users:  
- Avoid clicking on unfamiliar or suspicious links, especially from unknown senders.  
- Use updated browsers with built-in anti-clickjacking defenses.
- Regularly monitor bank account activity for unauthorized transactions.

---

## References

[**OWASP**](https://owasp.org/www-community/attacks/Clickjacking)

[**Hacktricks**](https://book.hacktricks.xyz/pentesting-web/clickjacking)

[**Portswigger**](https://portswigger.net/web-security/clickjacking)

[**Clickbandit**](https://portswigger.net/burp/documentation/desktop/tools/clickbandit)
