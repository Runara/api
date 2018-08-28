# Appointments

Appointments are single-client bookings.

## All Appointments

> Example Response:

```json
{
  "data": [
    {
      "id": 100112,
      "name": "Coloring Session",
      "description": "Veniam culpa et omnis quam rerum maiores sapiente iusto.",
      "base_price": "$27.00",
      "online_booking": true,
      "active": true
    },
    {
      "id": 100111,
      "name": "Cut and Shampoo",
      "description": "Iure voluptatem corporis excepturi sint similique officiis ab. Doloremque in eum dolores aut sunt ut doloribus. Similique necessitatibus sint mollitia. Non quia recusandae vel nihil doloribus.",
      "base_price": "$64.00",
      "online_booking": true,
      "active": true
    }
  ]
}
```

View all appointments belonging to an account.

### HTTP Request

`GET https://api.runara.com/appointments`

## Single Appointment

> Example Response:

```json
{
  "data": {
    "id": 100112,
    "name": "Coloring Session",
    "description": "Veniam culpa et omnis quam rerum maiores sapiente iusto.",
    "base_price": "$27.00",
    "online_booking": true,
    "staff": [
      {
        "id": 52,
        "name": "Trudie Kirlin",
        "price": "$37.00"
      },
      {
        "id": 53,
        "name": "Desmond Mann",
        "price": "$23.00"
      }
    ]
  }
}
```

View details of a specific appointment.

Includes a `base_price` that applies to any staff member that does not otherwise have a specified price for this appointment.

Staff members that charge a different amount are listed under the `staff` object.

### HTTP Request

`GET https://api.runara.com/appointments/{id}`
