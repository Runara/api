# Admin

## What are Admin Routes?

The `admin` routes are helper endpoints created to assist staff with day-to-day workflow tasks, such as check-ins and payments. While these tasks can be achieved using other existing endpoints, `admin` routes are always set in the context of a staff member so any information returned is pertinent to the logged-in user (Staff Member).

## Admin View

> Example Response:

```json
{
  "meta": {
    "accounts": [
      {
        "id": 100110,
        "name": "Body by Keelay",
        "role": "Administrator"
      },
      {
        "id": 100111,
        "name": "5x5 Inc",
        "role": "Staff"
      }
  ],
  "data": [
    {
      "id": 477,
      "session_id": null,
      "name": "StrongLifts Introduction",
      "type": "Class",
      "item_id": 100118,
      "date": "August 28th at 8:00am",
      "timestamp": 1535457600,
      "duration": "30 minutes",
      "timespan": "8:00am - 8:30am",
      "clients": [
        {
          "id": 100137,
          "booking_id": 477,
          "name": "Fatima Kuphal",
          "payment_status": 0,
          "payment_status_description": "Unpaid - Pay at Checkin",
          "payment_amount": "30.00",
          "checked_in": false,
          "photo": {
            "default": null,
            "thumb": null
          }
        }
      ],
      "account": {
        "id": 100110,
        "name": "Body by Keelay"
      },
      "staffed_by": {
        "id": 100135,
        "name": "Trudie Kirlin",
        "photo": {
          "default": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg",
          "thumb": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg"
        }
      },
      "location": {
        "id": 100118,
        "name": "Pineville",
        "room": null
      },
      "capacity": 20,
      "total_clients": 1,
      "total_checkins": 0
    },
    {
      "id": 848,
      "session_id": null,
      "name": "Cut and Shampoo",
      "type": "Appointment",
      "item_id": 100111,
      "date": "August 28th at 10:30am",
      "timestamp": 1535466600,
      "duration": "105 minutes",
      "timespan": "10:30am - 12:15pm",
      "clients": [
        {
          "id": 100112,
          "booking_id": 848,
          "name": "Jamie Kihn",
          "payment_status": 1,
          "payment_status_description": "Paid - Cash",
          "payment_amount": "64.00",
          "checked_in": false,
          "photo": {
            "default": null,
            "thumb": null
          }
        }
      ],
      "account": {
        "id": 100110,
        "name": "Body by Keelay"
      },
      "staffed_by": {
        "id": 100135,
        "name": "Trudie Kirlin",
        "photo": {
          "default": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg",
          "thumb": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg"
        }
      },
      "location": {
        "id": 100116,
        "name": "123 Main",
        "room": null
      },
      "capacity": null,
      "total_clients": 1,
      "total_checkins": 0
    }
  ]
}
}
```

If logged-in as a staff member, returns upcoming bookings staff accounts.

This endpoint should only be used by staff members. Non staff members will not receive any results from this endpoint.

### HTTP Request

`GET https://api.runara.com/admin`

<aside class="notice">
If logged-in as a manager or administrator, you can pass an optional staff ID in the request URL to view a particular staff member's bookings. Note: the `accounts` object will return empty as you are not allowed to view a staff member's associated accounts.
</aside>

### HTTP Request for Specific Staff (admin-only)

`GET https://api.runara.com/admin/{staff_id}`

### Route Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
ID | false | ID of staff to view. | `11234433`
