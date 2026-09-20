# 🛡️ Vulnerable Bank Security Assessment

An authorized web application security assessment performed
against a deliberately vulnerable banking application deployed
in an isolated local WSL environment.

## 🎯 Objectives

- Identified common web application vulnerabilities
- Analyzed HTTP requests and responses
- Practiced manual security testing with Burp Suite
- Mapped findings to the OWASP Top 10
- Documented vulnerabilities and their impact
- Recommended security remediation
- Analyzed selected attacks from a SOC perspective

## 🧪 Lab Environment

| Component | Technology |
|---|---|
| Host | Windows |
| Environment | WSL |
| Target | Vulnerable Bank |
| Proxy | Burp Suite |



## Vulnerability Summary

| # | Vulnerability | Severity | CVSS v3.1 |
|---|---|---|---:|
| 1 | Brute Force | Medium | 6.5 | 
| 2 | Unrestricted File Upload | High | 8.8 | 
| 3 | IDOR | High | 8.1 | 
| 4 | Privilege Escalation | High | 8.8 | 
| 5 | Race Condition | High | 7.5 | 
| 6 | SQL Injection (SQLi) | Critical | 9.8 |
| 7 | Cross-Site Scripting (XSS) | Medium | 6.1 | 


## ⚠️ Disclaimer

All security testing is performed against a deliberately
vulnerable application deployed in an environment controlled
by the author. No unauthorized systems are targeted.
