# MikroTik Hotspot Login Page Reflected XSS Vulnerability Advisory

## Overview
A reflected Cross-Site Scripting (XSS) vulnerability was discovered in the MikroTik RouterOS Hotspot login page. The vulnerability is triggered via the `dst` URL parameter, which improperly sanitizes input, allowing malicious JavaScript code to be executed in the victim’s browser.

## Affected Product
- MikroTik RouterOS Hotspot login page  
- Versions lower than 7.20

## Vulnerability Details
- The vulnerability occurs when an attacker crafts a URL like:
  
http://<router-ip>/login?dst=javascript:alert(3)

- When users visiting this URL reflects the JavaScript in the response, leading to script execution in the browser.

## Impact
This vulnerability can lead to session hijacking, phishing attacks, or redirecting users to malicious websites, compromising the security of users interacting with the hotspot login page.

## Attack Vector
- Requires user interaction to visit the crafted URL.
- The attacker must be able to send the victim the malicious link (via phishing or social engineering).
- The victim must access the hotspot login page on the vulnerable MikroTik Router.

## Recommendations
- Properly sanitize and validate all user input, especially URL parameters like `dst`.
- Apply output encoding to prevent injection of executable scripts.
- Deploy Web Application Firewall (WAF) rules to detect and block malicious payloads.
- Update MikroTik RouterOS to version 7.20 or later once a fix is released.

## Credits
- Discovered by Prak Sokchea

## Vulnerability Demonstration

Below is a screenshot demonstrating the reflected XSS payload executing in the MikroTik Hotspot login page:

![XSS Payload](./POC%201.png)


