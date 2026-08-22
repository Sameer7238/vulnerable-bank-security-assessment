# Brute Force Testing

## Objective

Test whether the login functionality is vulnerable to repeated username/password attempts.

## Target

Endpoint:http://127.0.0.1:5000/login

POST /login

Application:vulnerable-bank

Vulnerable Bank running locally.

## Tool

Burp Suite Intruder

## Methodology

1. Captured a login request using Burp Suite.
2. Sent the request to Intruder.
3. Identified the username and password parameters.
4. Configured payload positions.
5. Tested multiple credential combinations.
6. Compared HTTP status codes and response lengths.
7. Investigated responses that differed from failed authentication attempts.

## Results

The application returned different HTTP responses for tested credentials.

For example:

- Failed authentication → HTTP 401
- Successful authentication → HTTP 200

This response difference can potentially be used to distinguish valid credentials from invalid ones.

## Security Impact

An attacker could potentially automate login attempts if appropriate rate limiting, account lockout, or other protections are not implemented.