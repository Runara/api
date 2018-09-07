# Passes

Passes (also referred to as Memberships) are recurring payments or subscription to an account.

## All Passes

> Example Response:

```json
{
  "data": [
    {
      "id": 100113,
      "name": "Monthly Package",
      "description": "This monthly package includes...",
      "price": "$20.00"
    },
    {
      "id": 100116,
      "name": "Monthly Membership Plus",
      "description": "This is a monthly membership package that includes...",
      "price": "$55.00"
    }
  ]
}
```

View all passes belonging to an account.

### HTTP Request

`GET https://api.runara.com/passes`

## Single Pass

> Example Response:

```json
{
  "data": {
    "id": 100113,
    "name": "Monthly Package",
    "description": "This is a monthly pass for...",
    "price": "$20.00",
    "billing_interval": "month",
    "trial_period": null,
    "billing_descriptor": "Monthly Package at Abs",
    "all_classes": true,
    "classes": [],
    "all_appointments": false,
    "appointments": [
      {
        "id": 100110,
        "name": "Mens Haircut"
      },
      {
        "id": 100111,
        "name": "Cut and Shampoo"
      }
    ]
  }
}
```

View details of a specific pass.

### HTTP Request

`GET https://api.runara.com/passes/{id}`
