---
title: "Go Phish: Running a Controlled Phishing Campaign for Class"
date: January 2026
author: Brett (BM Cyber)
layout: post
---

# Go Phish: Running a Controlled Phishing Campaign for Class

This was a classroom exercise in cybersecurity where I designed, deployed, and analyzed a **controlled phishing simulation**. The goal was to understand attacker tactics, credential-harvesting infrastructure, and how defenders can detect and mitigate these threats.

**Important Ethical & Legal Notes**  
- This was a fully authorized, instructor-approved simulation.  
- No real individuals or organizations were targeted.  
- All testing used test accounts and isolated lab infrastructure.  
- Full participant disclosure, opt-in consent, and debrief occurred immediately after the campaign ended.  
- No real credentials, personal data, or harm were involved.

## 1. Campaign Goal & Defensive Value

**Objective**  
Simulate a realistic phishing attack designed to harvest credentials through a spoofed “security alert” email.

**Behavioral Goal**  
Trigger the user to perform a password reset on a cloned login page, allowing analysis of:  
- Password creation patterns  
- User susceptibility to urgency-based pretexts  
- UI elements that increase or decrease trust

**Security Value**  
This exercise helps defenders understand:  
- How credential-harvesting kits operate  
- How SMTP reputation affects email delivery  
- How cloned login pages capture sensitive data  
- How to detect and block similar attacks in real environments

## 2. Target Profile (Simulated)

A fictional persona was created for this lab:  
**Simulated User**  
- Role: Graduate research assistant in cloud infrastructure  
- Interests: AWS, homelabs, cloud security  
- Behavioral Traits: Likely to trust professional-platform security alerts

**Environmental Vulnerability**  
Because the persona relies heavily on professional networking platforms, a spoofed “security alert” email is a plausible attack vector.

**Privacy & Scope**  
No real individuals were profiled. All reconnaissance was performed on fictional accounts created solely for this lab.

## 3. Attack Chain Simulation

**Attacker Infrastructure**  
- Hosting: Cloudflare-protected web server  
- Backend: Simple database for storing captured test credentials  
- Landing Page: 1:1 clone of a professional networking site’s password reset page

**Delivery Mechanism**  
- SMTP Relay: High-reputation email provider to bypass spam filters  
- Sender Alias: Spoofed “Security Team” identity  
- Pretext: “Password breach detected — reset required”

**Exploit**  
- HTML email with embedded malicious link  
- Link redirects to cloned reset page  
- Submitted credentials are captured, then user is silently redirected to the real site

**Data Exfiltration**  
- Captured fields: username + new password  
- Stored in backend database for analysis  
- No real credentials were used

## 4. Email Construction

**Design Process**  
1. Initiated a real password reset on a test account to study legitimate formatting  
2. Extracted HTML from the authentic email  
3. Used AI assistance to restructure and clean the HTML for editing  
4. Manually replaced: text content, hyperlinks, branding elements, button URLs

**Final Email Characteristics**  
- Subject: “Action Required: Your password may have been compromised”  
- Sender Alias: “Security Team”  
- Source Address: Test Gmail account  
- Social Engineering: Urgency + fear of account breach  
- Obfuscation: Malicious link embedded in “Reset Password” button

## 5. Landing Page Construction

**Design Inspiration**  
A cloned version of a professional networking site’s password reset page.

**Technical Stack**  
- HTML5 for structure  
- CSS3 for styling and responsiveness  
- JavaScript for form handling and redirect logic

**AI Usage**  
Gemini 3 was used iteratively to generate initial HTML/CSS, improve layout responsiveness, refine typography and spacing, and add realistic UI elements.

**Final Output**  
A visually accurate clone capable of:  
- Accepting username + new password  
- Logging submissions to backend  
- Redirecting user to the legitimate site

## 6. Defensive Takeaways

**Email Security**  
- High-reputation SMTP providers dramatically increase delivery success  
- SPF/DKIM/DMARC checks can be bypassed with clever aliasing  
- HTML emails remain a major attack vector

**User Behavior**  
- Urgency and fear are still highly effective  
- Professional-platform alerts are trusted more than generic messages

**Detection Opportunities**  
- Cloudflare-hosted phishing pages can still be fingerprinted  
- Redirect chains often reveal malicious intent  
- Email metadata exposes spoofing attempts

**Mitigation Strategies**  
- Enforce MFA  
- Use password managers to detect domain mismatches  
- Implement browser-based phishing protection  
- Train users to inspect sender domains and URLs

## Final Thoughts

Running a controlled phishing simulation was one of the most eye-opening exercises I’ve done in my homelab. It showed just how effective even basic social engineering can be — and how important it is for defenders to think like attackers while building better protections.

If you're interested in replicating this (ethically and legally), start with open-source tools like GoPhish or King Phisher, always get explicit consent, and debrief participants immediately.

Questions or feedback? Reach out on X or via the contact form.

*(Last updated: January 2026)*
