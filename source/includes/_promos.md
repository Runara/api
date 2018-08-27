# Promos

## Check Promo Validity

> Example Response:

```json
[
{"data":{"id":"asdf"}}
]
```

Checks to see if promo is valid. Returns specific errors describing invalidity.

<aside class="notice">
A Booking ID must be applied as some promos only count against certain booking types, such as classes vs. appointments.
</aside>

### HTTP Request

`POST https://api.runara.com/discounts/attempt`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
code | true | The promo code to attempt | `WOWCODE20`
booking | true | ID of booking to attempt against | `58633ade9a89200fe53be77b`
