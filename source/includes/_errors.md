# Errors

The Runara API attempts to keep all exception responses formatted in a similar fashion to help you present the data more consistently to your users.

## Validation Errors

> Sample Response:

```json
{
  "data": {
    "email": "Invalid email address provided."
  }
}
```

Validation errors (when applicable) will return a key-pair response corresponding to the name/value pairs you supplied in your request.

The Runara API uses the following error codes:

Code | Meaning
---------- | -------
400 | Bad Request -- Your request was formatted incorrectly
401 | Unauthorized -- Your API key is wrong
402 | Payment Required -- Returned when payment is declined.
403 | Forbidden -- The kitten requested is hidden for administrators only
404 | Not Found -- The specified item could not be found

## Non-Validation Errors

> Sample Response:

```json
{
  "data": {
    "error": "Form error encountered. Please try again."
  }
}
```

The Runara API uses the following error codes for non-validation exceptions:

Code | Meaning
---------- | -------
405 | Method Not Allowed -- You tried to access an endpoint with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
409 | Conflict -- The item you're attempting to create already exists
429 | Too Many Requests -- You're requesting too many endpoints! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
