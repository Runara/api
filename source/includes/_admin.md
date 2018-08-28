# Admin

## What (and why) are Admin Routes?

The `admin` routes are helper endpoints created to assist staff with day-to-day workflow tasks, such as check-ins and payments. While these tasks can be achieved using other existing endpoints, `admin` routes are always set in the context of a staff member so any information returned is pertinent to the logged-in user (Staff Member).

## Admin View

> Example Result:

```json
{
    "meta" : {
        "accounts" : [
            {
                "id" : "sd5763ce9a89201a8f515fa4",
                "name" : "ABC and Co.",
                "role" : "staff"
            },
            {
                "id" : "335763ce9a89203a8f515fd0",
                "name" : "Curves on South",
                "role" : "staff"
            }
        ],
        "current_account" : [
            {
                "id" : "sd5763ce9a89201a8f515fa4",
                "name" : "ABC and Co.",
                "role" : "staff"
            }            
        ]
    },
  "data": [
        {
          "id": "5976940e9a81200a4f10c363",
          "session_id": "5959bdce1a892041711c4a2a-5959bdce1a892041711c4a2d-1500985800",
          "name": "Insanity Level 1",
          "type": "class",
          "item_id": "5959bdce1a892041711c4a2a",
          "date": "July 25th at 12:30pm",
          "timestamp": 1500985800,
          "duration": "60 minutes",
          "timespan": "12:30pm - 1:30pm",
          "clients": [
            {
              "id": "595b06a91a89204afc2fb2c4",
              "booking_id": "5959bdce9a892041711c4a2a-5959bdce1a892041711c4a2d-1500985800",
              "name": "Nestor DuBuque",
              "payment_status": {
                "status": 1,
                "description": "Paid - Credit Card"
              },
              "payment_amount": "24.00",
              "checked_in": false
            },
            {
              "id": "595b06a81a89204afe458627",
              "booking_id": "5959bdce9a891041711c4a2a-5959bdce9a892041711c4a2d-1500985800",
              "name": "Kenyon Hartmann",
              "payment_status": {
                "status": 0,
                "description": "Unpaid - Pay at checkin"
              },
              "payment_amount": "24.00",
              "checked_in": false
            }
          ],
          "account": {
            "id": "5940b4a81a892006485be28b",
            "name": "Curves2Go"
          },
          "staffed_by": {
            "id": "594c6d7f1a8920785c0e25e8",
            "name": "Michael Wuori"
          },
          "location": {
            "id": "5940b6251a892006485be2bd",
            "name": "Suburbia",
            "room": "Studio A"
          },
          "capacity": 25,
          "total_clients": 2,
          "total_checkins": 0
        }   
    ]
}
```

If logged-in as a staff member, returns upcoming bookings staff accounts.

<aside class="notice">
This endpoint should only be used by staff members. Non staff members will not receive any results from this endpoint.
</aside>

### HTTP Request

`GET https://api.runara.com/admin`


## Switch Accounts

```shell
curl "https://api.runara.com/admin/switch/{ID}"
  -H "Authorization: Bearer:your.jwt.token"
```

Switches the current account of the user, provided the user has access to the account.

<aside class="warning">
User must have access to the account before switching to it. If they do not, a `401` response is returned.
</aside>

### HTTP Request

`GET https://api.runara.com/admin/switch/{ID}`

### URL Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
ID | true | ID of account to switch to. | `568b55febffebc91068d4579`
