# Payments

## Add an Account Credit

Add an account credit to a client.

### HTTP Request

`POST https://api.runara.com/payments/credit`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
customer | true | ID of client. | `234432`
credit_type | true | Type of credit to add. | One of `amount`, `class` or `appointment`
amount | true if credit_type = `amount` | Currency amount to add to client. | `20.00`
class | true if credit_type = `class` | Class ID to credit. | `234432`
appointment | true if credit_type = `appointment` |  Appointment ID to credit. | `444323`
reason | false | Reason for credit. | `Could not complete original transaction.`

## Get All Customer Cards

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

> Example Response:

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
