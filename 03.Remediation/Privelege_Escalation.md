## Recommended Remediation

* Use an allowlist of fields permitted during registration.
* Never allow clients to set administrative privileges.
* Set `is_admin` server-side to `false` for normal registrations.
* Set account balances using trusted server-side logic.
* Validate and sanitize all registration parameters.
* Avoid returning internal/debug information in production responses.
* Remove sensitive fields from API responses unless they are explicitly required.
* Implement server-side authorization checks for administrative functionality.
