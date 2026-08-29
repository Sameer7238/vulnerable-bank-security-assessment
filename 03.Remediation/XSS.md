Recommended remediation steps:

1. Implement context-aware output encoding for all user-controlled data.
2. Use the web framework's built-in HTML escaping mechanisms.
3. Validate input according to the expected format and data type.
4. Avoid inserting untrusted data directly into HTML, JavaScript, or
   other executable contexts.
5. Avoid unsafe DOM APIs such as `innerHTML` when processing untrusted
   input.
6. Implement a Content Security Policy (CSP) to provide an additional layer of protection against script execution.
7. Review other application endpoints for similar input-handling issues.
