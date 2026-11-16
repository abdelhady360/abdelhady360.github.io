---
title: About
icon: fas fa-info-circle
order: 4
---

<div style="margin-top: 20px; line-height: 1.6;">
Hi! I'm Abdelhady, a Cybersecurity Researcher specializing in Penetration Testing, Malware Analysis, and OSINT Research. My work revolves around uncovering vulnerabilities, dissecting malicious software, tracing digital footprints, and investigating real-world cyber threats. Always curious about what's happening beneath the surface.
</div>

 
<style>
/* Chip Layout */
.about-chips {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
  margin: 16px 0 28px;
}

/* Default Light Mode */
.about-chips .about-chip {
  display: inline-flex;
  align-items: center;
  padding: 8px 13px;
  border: 1px solid #dcdcdc;
  border-radius: 5px;
  background: #f5f5f5;
  color: #555;
  font-family: Consolas, "Courier New", monospace;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.4;
  box-shadow: none;
  transition: border-color 0.2s ease;
}

/* Explicit Dark Mode */
html[data-mode="dark"] .about-chips .about-chip {
  background: #1c1c1c;
  border-color: #373737;
  color: #bcbcbc;
}

/* Automatic Dark Mode */
@media (prefers-color-scheme: dark) {
  html:not([data-mode]) .about-chips .about-chip {
    background: #1c1c1c;
    border-color: #373737;
    color: #bcbcbc;
  }
}

/* Hover */
.about-chips .about-chip:hover {
  border-color: #777;
}

/* Note */
.about-note {
  display: block;
  margin-top: -12px;
  margin-bottom: 28px;
  color: var(--text-muted-color, #888);
  font-size: 12px;
  line-height: 1.6;
}
</style>

## Areas of Expertise

<div class="about-chips">
  <span class="about-chip">Web Application Pentesting</span>
  <span class="about-chip">Network &amp; AD Pentesting</span>
  <span class="about-chip">Malware Analysis &amp; Reverse Engineering</span>
  <span class="about-chip">OSINT Research</span>
</div>

## Certification Tracks & Self-Study

<div class="about-chips">
  <span class="about-chip">PEN-200 (OSCP+)</span>
  <span class="about-chip">SANS SEC560</span>
  <span class="about-chip">SANS FOR610</span>
  <span class="about-chip">eWPTX</span>
</div>

<small class="about-note">
Studied independently. No certification exams taken.
</small>