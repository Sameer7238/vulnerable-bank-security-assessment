# File Upload Vulnerability

## Objective

Test whether the application properly validates and restricts uploaded files.


## Testing Methodology

1. Accessed the profile section of the application.
2. Identified the file upload functionality.
3. Uploaded a test file through the profile picture upload feature.
4. Observed how the application processed and stored the uploaded file.
5. Examined the resulting file URL.
6. Verified whether the uploaded file was directly accessible through the web application.

## Observation

In the observed case, a Python source file was accessible through:

```text
/static/uploads/242117_rbac.py
```

The browser displayed the contents of the uploaded Python file.

### Evidence

![File Upload Vulnerability](Screenshots/File_upload.png)

## Security Impact

Improper file-upload validation can allow attackers to upload files that should not be permitted by the application.

Depending on the server configuration and the types of files accepted, this could potentially lead to:

* Unauthorized file storage
* Exposure of uploaded files
* Source-code disclosure
* Storage of malicious files
* Potential server-side code execution if executable file types are accepted and executed by the server



## Result

The assessment identified a potential file-upload security weakness in the Vulnerable Bank application.

The application accepted an uploaded file and made it accessible through a predictable web path. Further validation should be performed to determine whether additional file types can be uploaded and whether uploaded files can be executed or accessed by unauthorized users.

This testing was performed against the Vulnerable Bank application in a controlled local lab environment.
