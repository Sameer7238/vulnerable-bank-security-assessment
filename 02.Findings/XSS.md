# Cross-Site Scripting (XSS)

## Objective

Test whether the application properly validates and handles user-controlled
input and prevents the execution of malicious JavaScript in the user's browser.

## Target

Endpoint: http://127.0.0.1:5000/login

POST /login

Application: vulnerable-bank

Vulnerable Bank running locally.

## Tool

Burp Suite

## Methodology

1. Accessed the login functionality of the application.
2. Captured the login request using Burp Suite.
3. Identified the input parameter accepting user-controlled data.
4. Injected a JavaScript payload into the affected parameter.
5. Used the following proof-of-concept payload:

   <script>alert(1)</script>

6. Forwarded the modified request to the application.
7. Observed the application's response and browser behavior.
8. Verified that the injected JavaScript was executed successfully.
9. Confirmed the vulnerability by observing the JavaScript alert displayed
   in the browser.

## Proof of Concept

Payload:

<script>alert(1)</script>

The payload resulted in the execution of JavaScript and displayed an
alert containing the value `1`.

## Results

The application accepted the supplied JavaScript payload without properly
neutralizing the input.

The injected payload was successfully executed in the browser after the
request was processed by the application.

Observed behavior:

- Input → `<script>alert(1)</script>`
- Application → Accepted the injected input
- Response → Redirected to `/dashboard`
- Browser → Executed the injected JavaScript
- Result → JavaScript alert displaying `1`

This confirms that the application is vulnerable to Cross-Site Scripting
(XSS).

## Security Impact

Successful exploitation of XSS could allow an attacker to execute
arbitrary JavaScript in a victim's browser within the application's
security context.

Depending on the application's functionality, this may allow an attacker
to:

- Modify or manipulate page content.
- Perform unauthorized actions on behalf of the victim.
- Steal sensitive information accessible to client-side JavaScript.
- Conduct phishing attacks by modifying legitimate application pages.
- Redirect users to malicious websites.
- Abuse authenticated user sessions where applicable.

The actual impact depends on the affected functionality, user privileges,
session-cookie protections, and other security controls implemented by
the application.

## Severity

Medium

## Remediation

The application should properly handle and neutralize untrusted user
input before rendering it in the browser.

