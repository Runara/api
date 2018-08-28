---
title: Runara API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://app.runara.com/developer'>Sign Up for a Developer Key</a>

includes:
  - errors
  - accounts
  - appointments
  - admin
  - classes
  - clients
  - favorites
  - locations
  - profiles
  - checkout
  - bookings
  - checkin

search: true
---

# Introduction

Welcome to the Runara API! You can use our API to access Runara endpoints.

# Authentication

> To authorize, use this code:

```ruby
require 'runara'

api = Kittn::APIClient.authorize!('you.jwt.token')
```

```python
import runara

api = runara.authorize('you.jwt.token')
```

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: you.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
```

> Make sure to replace `you.jwt.token` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](https://api.runara.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer your.jwt.token`

<aside class="notice">
You must replace <code>you.jwt.token</code> with your personal API key.
</aside>

# Payments

## Get All Customer Cards

```shell
curl "https://api.runara.com/kittens"
  -H "Authorization: Bearer your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
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
}```

Retrieves all stored payments sources for the current user.

### HTTP Request

`POST https://api.runara.com/payments/cards`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
customer | true | The ID of the customer | `58633ade9a89200fe53be77b`

## Add a Card

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

This endpoint adds a single payment source to a customer's records.

### HTTP Request

`POST https://api.runara.com/payments/cards/add`

### URL Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
customer | true | The ID of the customer | `58633ade9a89200fe53be77b`
cc_number | true | Credit card number of card | `4444 4444 4444 4444`
cc_exp_month | true | Expiration Month of card | `08`
cc_exp_year | true | Expiration Year of card | `2016`
cc_cvc | true | CVC code of card | `333`

## Update a Card

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

This endpoint updates a single payment source.

<aside class="notice">
You can only update the a card's expiration date and its status as "default".
</aside>

### HTTP Request

`POST https://api.runara.com/payments/cards/update`

### URL Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
customer | true | The ID of the customer | `58633ade9a89200fe53be77b`
card | true | ID of payment source | `card_58633ade9a89200fe53be77b`
cc_exp_month | true | Expiration Month of card | `08`
cc_exp_year | true | Expiration Year of card | `2016`
make_default | false | Boolean to make card the default payment source | `true`

## Remove a Card

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

Removes a payment source from a customer's record.

### HTTP Request

`POST https://api.runara.com/cards/remove`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
customer | true | The ID of the customer | `58633ade9a89200fe53be77b`
card | true | ID of payment source | `card_58633ade9a89200fe53be77b`

# Promos

## Check Promo Validity

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

# Me

## Get recent activity

```shell
curl "https://api.runara.com/me"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "recent": {
      "upcoming": [
        {
          "booking_id": "586c7d5e9a89201a3975a7a5",
          "type": "class",
          "type_id": "57f71b6a9a892007ef2acc69",
          "name": "30-Minute Yoga",
          "date": "1483956000",
          "date_short": "1\/09\/17",
          "date_long": "January 9th 2017",
          "time": "10:00am",
          "location": {
            "id": "57f71b1b9a892007ef2acc2f",
            "name": "Shields Ltd",
            "room": {
              "id": null,
              "name": null
            }
          },
          "staffed_by": {
            "_id": "581d41449a89200452530aca",
            "name": "Bianka Cassin"
          }
        },
        {
          "booking_id": "586c7d7e9a89200fe53be793",
          "type": "class",
          "type_id": "57f71b759a892007ef2acc78",
          "name": "5 Minute Abs",
          "date": "1484541000",
          "date_short": "1\/16\/17",
          "date_long": "January 16th 2017",
          "time": "4:30am",
          "location": {
            "id": "57f71b4f9a892008497f6169",
            "name": "Schuppe, Bergstrom and Carter",
            "room": {
              "id": "57f71b509a892008497f616b",
              "name": "MediumSpringGreen"
            }
          },
          "staffed_by": {
            "_id": null,
            "name": null
          }
        }
      ],
      "past": [
        {
          "booking_id": "586c822d9a89201a3975a7a9",
          "type": "class",
          "type_id": "57f71b799a892007d959ee1d",
          "name": "Grow an Ass Wuori Would Love",
          "date": "1483763400",
          "date_short": "1\/07\/17",
          "date_long": "January 7th 2017",
          "time": "4:30am",
          "location": {
            "id": "57f71b329a892007ef2acc41",
            "name": "Ledner, Murphy and Pfeffer",
            "room": {
              "id": "57f71b339a892007ef2acc42",
              "name": "Tan"
            }
          },
          "staffed_by": {
            "_id": null,
            "name": null
          }
        },
        {
          "booking_id": "586d99399a892004494e6421",
          "type": "class",
          "type_id": "57f71b6a9a892007ef2acc69",
          "name": "30-Minute Yoga",
          "date": "1483603200",
          "date_short": "1\/05\/17",
          "date_long": "January 5th 2017",
          "time": "8:00am",
          "location": {
            "id": "57f71b249a892008497f6145",
            "name": "Botsford PLC",
            "room": {
              "id": null,
              "name": null
            }
          },
          "staffed_by": {
            "_id": "581d41489a8920045120499c",
            "name": "Joannie Becker"
          }
        }
      ],
      "purchases": [

      ],
      "locations": [
        {
          "id": "57f71b259a892007ef2acc38",
          "name": "Mertz-Moore",
          "room": {
            "id": "57f71b269a892007ef2acc39",
            "name": "Red"
          }
        },
        {
          "id": "57f71b1b9a892007ef2acc2f",
          "name": "Shields Ltd",
          "room": {
            "id": null,
            "name": null
          }
        },
        {
          "id": "57f71b4f9a892008497f6169",
          "name": "Schuppe, Bergstrom and Carter",
          "room": {
            "id": "57f71b509a892008497f616b",
            "name": "MediumSpringGreen"
          }
        }
      ]
    }
  }
}
```

Returns recent bookings, purchases and locations from the client's records.

### HTTP Request

`POST https://api.runara.com/me`
