# IDOR – Unauthorized Access to Transaction Data

## Objective

Test whether the application properly enforces authorization when accessing transaction information belonging to different accounts.



## Testing Methodology

1. Logged into the Vulnerable Bank application as an authenticated user.
2. Captured the transaction history request using Burp Suite.
3. Observed that the account number was directly included in the URL.
4. Sent the request to Burp Repeater.
5. Modified the account number in the URL to another account number.
6. Sent the modified request using the same authenticated session.
7. Compared the responses to determine whether authorization was enforced.

## Original Request

The authenticated user requested transaction information for their account:

```http
GET /transactions/<ACCOUNT_A>
```

The server returned transaction information associated with that account.

## Modified Request

The account identifier was changed:

```http
GET /transactions/<ACCOUNT_B>
```

The request was sent using the same authenticated session.

## Observation

The application returned transaction information for the modified account identifier with:

```text
HTTP/1.0 200 OK
```

The response contained transaction information associated with the requested account.

This indicates that the server was relying on the user-supplied account identifier without properly verifying whether the authenticated user was authorized to access that account's transaction data.

### Evidence

![IDOR – Original Account](Screenshots/IDOR/IDOR_1.png)

![IDOR – Modified Account](Screenshots/IDOR/IDOR_2.png)

## Security Impact

An attacker who can identify or guess another account identifier could potentially access unauthorized transaction information.

This may expose:

* Transaction amounts
* Account numbers
* Transaction IDs
* Sender and recipient account information
* Transaction timestamps
* Transaction descriptions

In a real banking application, unauthorized access to this information could result in significant privacy and security impact.


## Result

The Vulnerable Bank application was found to be vulnerable to **Insecure Direct Object Reference (IDOR) / Broken Object Level Authorization** in the transaction history functionality.

By modifying the account identifier in the request, an authenticated user could retrieve transaction information associated with another account.

This assessment was performed against the Vulnerable Bank application in a controlled local lab environment.
