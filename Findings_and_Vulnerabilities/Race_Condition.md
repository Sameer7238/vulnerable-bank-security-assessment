# Race Condition – Concurrent Money Transfers

## Objective

Test whether the money transfer functionality correctly handles multiple requests submitted concurrently.

## Affected Functionality

**Money Transfer**

```text
POST /transfer
```

## Testing Methodology

1. Logged into the Vulnerable Bank application.
2. Identified the money transfer functionality.
3. Captured the transfer request using Burp Suite.
4. Observed the request parameters and authorization mechanism.
5. Tested the transfer functionality with concurrent requests.
6. Compared the account balance before and after the requests.
7. Analyzed the HTTP responses and application behavior.


## Observation

A transfer request returned:

```text
HTTP/1.0 200 OK
```

with the response indicating:

```json
{
  "message": "Transfer Completed",
  "status": "success"
}
```

During concurrent transaction testing, the account balance changed unexpectedly and became negative.

### Evidence

![Race Condition Transfer Request](Screenshots/Race_Condition_2.png)

![Race Condition Result](Screenshots/Race_Condition_4.png)

## Security Impact

A race condition in a financial transaction can potentially allow multiple requests to be processed based on an outdated account balance.

If the server does not properly synchronize balance validation and balance updates, an attacker may be able to submit concurrent transactions that bypass intended balance checks.

Potential impact includes:

* Unauthorized financial transactions
* Negative account balances
* Double-spending
* Incorrect transaction records
* Financial loss




## Conclusion

Testing of the Vulnerable Bank money-transfer functionality demonstrated unexpected balance behavior when transactions were processed concurrently.

This indicates a potential **race condition in the transaction-processing logic**.

The assessment was performed exclusively against a locally hosted Vulnerable Bank application in a controlled lab environment.
