# Classes

Classes are multi-client bookings. Classes are constrained by `capacity`, which is determined by the timeseries entries attributed to each class. Each timeseries can have different locations, rooms and capacities.

## All Classes

> Example Response:

```json
{
  "data": [
    {
      "id": 100119,
      "name": "30-Minute Yoga",
      "description": "Molestiae sit ut sunt vel vero. Ut est dolores magni eligendi et laborum. Quidem inventore aut quidem aspernatur voluptas exercitationem occaecati. Deleniti voluptatem qui omnis eligendi reprehenderit eum quis. Autem atque ipsa autem.",
      "price": "$25.00",
      "requires_membership": false,
      "active": true
    },
    {
      "id": 100115,
      "name": "Advanced Pilates",
      "description": "Enim consequatur sunt adipisci. Quae architecto quasi accusamus ipsum neque deleniti. Earum sit impedit ipsum iusto aut sit. Qui voluptas et est excepturi inventore. Voluptatum nemo ut soluta.",
      "price": "$5.00",
      "requires_membership": false,
      "active": true
    },
    {
      "id": 100116,
      "name": "Introduction to Basic Yoga Techniques",
      "description": "Minus omnis error corporis aut error quisquam consequuntur.",
      "price": "$25.00",
      "requires_membership": false,
      "active": true
    }
  ]
}
```

View all classes belonging to an account.

### HTTP Request

`GET https://api.runara.com/classes`

## Single Class

> Example Response (?with_sessions enabled):

```json
{
  "data": {
    "id": 100119,
    "name": "30-Minute Yoga",
    "description": "Molestiae sit ut sunt vel vero. Ut est dolores magni eligendi et laborum. Quidem inventore aut quidem aspernatur voluptas exercitationem occaecati. Deleniti voluptatem qui omnis eligendi reprehenderit eum quis. Autem atque ipsa autem.",
    "capacity": 20,
    "duration": "30mins",
    "price": null,
    "pricing": {
      "single": null,
      "packages": [],
      "unlimited": null
    },
    "sessions": {
      "meta": {
        "name": "30-Minute Yoga",
        "description": "Molestiae sit ut sunt vel vero. Ut est dolores magni eligendi et laborum. Quidem inventore aut quidem aspernatur voluptas exercitationem occaecati. Deleniti voluptatem qui omnis eligendi reprehenderit eum quis. Autem atque ipsa autem.",
        "price": "$25.00",
        "duration": 30,
        "days": [
          "2018-08-28",
          "2018-08-29"
        ],
        "staff": [
          {
            "id": 100116,
            "name": "Trudie Kirlin",
            "photo": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg"
          }
        ],
        "locations": [
          {
            "id": 100116,
            "name": "123 Main"
          }
        ],
        "selected_date": null,
        "selected_week": null,
        "time_extremes": {
          "earliest": "11:00am",
          "latest": "8:00pm"
        },
        "booking_interval": 30,
        "dates": null
      },
      "dates": [
        {
          "id": "100148-1535468400",
          "timestamp": 1535468400,
          "ends": 1535470200,
          "formatted": {
            "short": "2018-08-28",
            "long": "August 28th 2018",
            "time": "11:00am",
            "span": "11:00am - 11:30am"
          },
          "meta": {
            "ts_id": 100148,
            "staff_id": 100116,
            "staff": "Trudie Kirlin",
            "staff_abbr": "Trudie K.",
            "staff_photo": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg",
            "location_id": 100116,
            "location": "123 Main",
            "timezone": "America\/New_York",
            "time": "11:00am",
            "end_time": null,
            "time_between": null,
            "price": "$25.00",
            "capacity": 10,
            "registered": 0,
            "is_full": false,
            "is_booked": false,
            "duration": 30,
            "name": "11:00am",
            "item_type": "class",
            "item_id": 100119,
            "spots_left": 10
          }
        },
        {
          "id": "100170-1535543100",
          "timestamp": 1535543100,
          "ends": 1535544900,
          "formatted": {
            "short": "2018-08-29",
            "long": "August 29th 2018",
            "time": "7:45am",
            "span": "7:45am - 8:15am"
          },
          "meta": {
            "ts_id": 100170,
            "staff_id": 100116,
            "staff": "Trudie Kirlin",
            "staff_abbr": "Trudie K.",
            "staff_photo": "https:\/\/randomuser.me\/api\/portraits\/men\/1.jpg",
            "location_id": 100116,
            "location": "123 Main",
            "timezone": "America\/New_York",
            "time": "7:45am",
            "end_time": null,
            "time_between": null,
            "price": "$25.00",
            "capacity": 5,
            "registered": 0,
            "is_full": false,
            "is_booked": false,
            "duration": 30,
            "name": "7:45am",
            "item_type": "class",
            "item_id": 100119,
            "spots_left": 5
          }
        }
      ]
    },
    "requires_membership": false,
    "active": true
  }
}
```

View details of a specific class.

URL parameter `with_sessions` can be passed to retrieve upcoming bookable sessions for the class.

### HTTP Request

`GET https://api.runara.com/classes/{id}`

### URL Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
with_sessions | false | Boolean. Returns upcoming sessions for which class is bookable. | `true`
