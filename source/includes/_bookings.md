# Bookings

## Get All bookings

```shell
curl "https://api.runara.com/kittens"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
[
{"data":{"id":"asdf"}}
]
```

This endpoint retrieves all bookings for the current user.

### HTTP Request

`GET https://api.runara.com/bookings`

## Get a Specific Booking

```shell
curl "https://api.runara.com/bookings"
  -H "Authorization: you.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a single booking.

### HTTP Request

`GET https://api.runara.com/bookings/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the booking to retrieve

## Create a Booking

```shell
curl "https://api.runara.com/bookings"
  -H "Authorization: you.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": "5865eab69a892011972abc1b",
  "client": {
    "id": "583e37e09a89202eba73abc2",
    "first_name": "Tucker",
    "last_name": "Wuori"
  },
  "booking": {
    "id": "57f71b6a9a892007ef2acc69",
    "name": "30-Minute Yoga",
    "type": "class",
    "session": {
      "date": "1484128800",
      "date_formatted": null,
      "date_short": "1\/11\/17",
      "date_long": "January 11th 2017",
      "time": null,
      "location": {
        "id": "57f71b1a9a892008497f613c",
        "name": "Wolff LLC"
      },
      "staff": {
        "id": "581d41479a89200452530acc",
        "name": "Chester Von"
      }
    },
    "purchase": {
      "payment_source": "card_19VDNdEirlNVKsJXWphGWx4C",
      "purchase_type": "Single Session",
      "purchase_price": "22.00",
      "purchase_price_formatted": "$22.00",
      "promos": [
        {
          "id": "57fb12379a89201ca460c7ce",
          "code": "WOWCODE",
          "description": "Sapiente eum nam magnam minima quae atque. Pariatur ut eum illum ex veniam qui.",
          "amount": "15.00",
          "percentage": null,
          "discount_applied": "15.00"
        }
      ],
      "total": "7.00"
    }
  }
}
```

This endpoint retrieves a single booking.

### HTTP Request

`POST https://api.runara.com/bookings`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | The ID of the client to book | `58633ade9a89200fe53be77b`
appointment | Required without class | The ID of the appointment to book | `58633ade9a89200fe53be77b`
class | Required without appointment | The ID of the class to book | `58633ade9a89200fe53be77b`
session | true | Hyphen-Separated Timeseries ID and Timestamp of session to book | `584777b49a892049955bedf3-1483524000`
pricing | true | Pricing option to book | `single`, `unlimited`, `58633ade9a89200fe53be77b`
code | false | Promo code | `PROMOCODE20`
payment_source | true | String representing payment source | `Cash`, `card_58633ade9a89200fe53be77b`
complete | false | Boolean to process payment and finalize booking | `true`

## Update a Booking

```shell
curl "https://api.runara.com/bookings"
  -H "Authorization: you.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": "5865eab69a892011972abc1b",
  "client": {
    "id": "583e37e09a89202eba73abc2",
    "first_name": "Tucker",
    "last_name": "Wuori"
  },
  "booking": {
    "id": "57f71b6a9a892007ef2acc69",
    "name": "30-Minute Yoga",
    "type": "class",
    "session": {
      "date": "1484128800",
      "date_formatted": null,
      "date_short": "1\/11\/17",
      "date_long": "January 11th 2017",
      "time": null,
      "location": {
        "id": "57f71b1a9a892008497f613c",
        "name": "Wolff LLC"
      },
      "staff": {
        "id": "581d41479a89200452530acc",
        "name": "Chester Von"
      }
    },
    "purchase": {
      "payment_source": "card_19VDNdEirlNVKsJXWphGWx4C",
      "purchase_type": "Single Session",
      "purchase_price": "22.00",
      "purchase_price_formatted": "$22.00",
      "promos": [
        {
          "id": "57fb12379a89201ca460c7ce",
          "code": "WOWCODE",
          "description": "Sapiente eum nam magnam minima quae atque. Pariatur ut eum illum ex veniam qui.",
          "amount": "15.00",
          "percentage": null,
          "discount_applied": "15.00"
        }
      ],
      "total": "7.00"
    }
  }
}
```

This endpoint updates a booking.

### HTTP Request

`PUT https://api.runara.com/bookings`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | The ID of the client to book | `58633ade9a89200fe53be77b`
appointment | Required without class | The ID of the appointment to book | `58633ade9a89200fe53be77b`
class | Required without appointment | The ID of the class to book | `58633ade9a89200fe53be77b`
session | true | Hyphen-Separated Timeseries ID and Timestamp of session to book | `584777b49a892049955bedf3-1483524000`
pricing | true | Pricing option to book | `single`, `unlimited`, `58633ade9a89200fe53be77b`
code | false | Promo code | `PROMOCODE20`
payment_source | true | String representing payment source | `Cash`, `card_58633ade9a89200fe53be77b`
complete | false | Boolean to process payment and finalize booking | `true`

## Send a Message to all clients of a booking

```shell
curl "https://api.runara.com/bookings/message/{booking_id}"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns a 204 response on successful submission.

Sends a message to all clients registered for booking `booking_id`.

### HTTP Request

`POST https://api.runara.com/bookings/message/{booking_id}`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
message | true | Message to send to booked client(s). | "Due to inclement weather..."

## Cancel a booking for a single client

```shell
curl "https://api.runara.com/bookings/cancel"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns a 204 response on successful submission.

Cancels a booking for a single client passed in body.

### HTTP Request

`POST https://api.runara.com/bookings/cancel`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
client | true | ID of client to cancel | `58633ade9a89200fe53be77b`
message | false | Message to send clients | "Due to inclement weather..."

## Check-In a Pre-Paid Client

```shell
curl "https://api.runara.com/bookings/checkin"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns a 200 response on successful submission.

Checks-in a prepaid client to a booking session.

### HTTP Request

`POST https://api.runara.com/bookings/checkin`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
booking | true | ID of booking to check-in to | `58633ade9a89200fe53be77b`
client | true | ID of client to check-in | `58633ade9a89200fe53be77b`
undo | false | If `true`, reverts check-in status | `true`

## Re-Book a Session

```shell
curl "https://api.runara.com/bookings/rebook/{session_id}"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns a (200) booking response.

Retrieves booking information needed to create a re-booking request.

<aside class="notice">
You can pass either a 3-part session identifier or a single-part booking identifier for {session_id}.
</aside>

### HTTP Request

`GET https://api.runara.com/bookings/rebook/{session_id}`

### URL Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
session_id | true | ID of booking to to re-book | `58633ade9a89200fe53be77b`
