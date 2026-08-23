## Recommended Remediation

* Implement server-side authorization checks for every transaction request.
* Verify that the requested account belongs to the authenticated user.
* Never rely solely on account identifiers supplied by the client.
* Use centralized object-level authorization controls.
* Consider using non-guessable identifiers where appropriate, but do not treat them as a replacement for authorization.
* Log and monitor unauthorized object-access attempts.
