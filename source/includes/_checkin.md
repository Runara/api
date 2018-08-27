## Check-In a Client

> Successful check-in returns an empty 204 response.

This endpoint adds a client to the requestor's current account.

<aside class="notice">
Check-Ins can be made for any pass-holding client of the requestor's current account. Clients are only allowed one pass per account at any given time.
</aside>

### HTTP Request

`POST https://api.runara.com/bookings/checkinpass`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true if no `code` | ID of client to check-in. | `1233243`
code | true if no `client` | Badge/Fob code for client. | `AA234444`
location | true | Current location ID where check-in occurs. | `2233344`
