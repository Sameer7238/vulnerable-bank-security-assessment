## Recommended Remediation

* Allow only required file types.
* Validate files based on their actual content, not only their extension.
* Use an allowlist of permitted MIME types and extensions.
* Generate safe, non-user-controlled filenames.
* Store uploads outside the web root where possible.
* Prevent uploaded files from being executed by the server.
* Apply appropriate file-size limits.
* Enforce authorization when accessing uploaded files.
* Serve uploaded content with safe response headers.
