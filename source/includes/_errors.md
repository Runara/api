# Errors

> Sample Validation Error (422 402) with field->error pairs. This format is also returned for 401 errors when logging in with invalid user/pass combination.

```json
{
  "data": {
    "email": "Invalid email/password combination."
  }
}
```

> Sample Server Error (All other status codes)

```json
{
  "data": {
    "error": "Item does not exist."
  }
}
```

The Runara API uses the following error codes:

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
402 | Payment Required -- Returned when payment is declined.
403 | Forbidden -- The kitten requested is hidden for administrators only
404 | Not Found -- The specified kitten could not be found
405 | Method Not Allowed -- You tried to access an endpoint with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
409 | Conflict -- The item you're attempting to create already exists
429 | Too Many Requests -- You're requesting too many endpoints! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarially offline for maintanance. Please try again later.
