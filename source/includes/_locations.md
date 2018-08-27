# Locations

## Find Nearby Locations

```shell
curl "https://api.runara.com/locations/nearby"
  -H "Authorization: Bearer:your.jwt.token"
```
> The above command returns the JSON structure:

```json
{
  "data": {
    "meta": {
      "categories": [
        {
          "id": "salon",
          "name": "Salon"
        },
        {
          "id": "spa",
          "name": "Spa"
        }
      ],
      "pagination": {
        "total": 3,
        "total_pages": 1,
        "per_page": 25,
        "current_page": 1,
        "next_page": null,
        "prev_page": null
      }
    },
    "user_location": {
      "address": "107 Mainside Ave, Charlotte, NC 28203, USA",
      "city": "Charlotte",
      "state": "NC",
      "postal": "28203",
      "x": -80.8658719,
      "y": 35.2047737
    },
    "results": [
      {
        "id": "5940b6259a892006485be2bd",
        "name": "Curves - Suburbia",
        "categories": [
          {
            "id": "pilates",
            "name": "Pilates"
          },
          {
            "id": "salon",
            "name": "Salon"
          },
          {
            "id": "spa",
            "name": "Spa"
          }
        ],
        "street": "712 Ideal Way",
        "street_2": null,
        "city": "Charlotte",
        "state": "NC",
        "postal": "28203",
        "distance": "< 1 mile away",
        "logo": null,
        "geo": {
          "lat": 35.199486,
          "lng": -80.85681
        }
      },
      {
        "..." : "..."
      }
    ]
  }
}
```


Finds nearby locations and returns paginated results within 25 miles of the user's (request originator) location. Location is determined by a series of geolocation tests.

Other qualifiers may be provided, such as `category` and `search`.

<aside class="info">
Results set includes meta information and user geolocatoin information alongside results.
</aside>

### HTTP Request

`GET https://api.runara.com/locations/nearby`

### URL Parameters

Parameter | Type | Required | Description | Example
--------- | -------- | -------- | ----------- | -----------
limit | integer | false | Number of results to return per-page. | `10`
page | integer | false | Page number of pagination set. | `1`
lng | double | false | Longitude value of user. | `-80.8659062`
lat | double | false | Latitude value of user. | `35.2047847`
search | string | false | Search term to use. | `Yoga`
category | string | false | Category to limit results to. | 'Spa'

## View Location Details

```shell
curl "https://api.runara.com/locations/{ID}"
  -H "Authorization: Bearer:your.jwt.token"
```
> The above command returns the JSON structure:

```json
{
  "data": {
    "id": "5940b6289a892006485be2c1",
    "name": "Curves - University",
    "categories": [
      {
        "id": "salon",
        "name": "Salon"
      },
    ],
    "street": "2200 Park Rd",
    "street_2": null,
    "city": "Charlotte",
    "state": "NC",
    "postal": "28203",
    "distance": "< 1 mile away",
    "hours": [
      {
        "Monday - Tuesday": [
          "Closed"
        ]
      },
      {
        "Wednesday - Thursday": [
          "8:00am - 5:00pm"
        ]
      },
      {
        "Friday - Saturday": [
          "Closed"
        ]
      },
      {
        "Sunday": [
          "8:00am - 1:00pm",
          "2:00pm - 6:00pm"
        ]
      }
    ],
    "phone": "+1-875-433-8032",
    "logo": "https:\/\/unsplash.it\/200\/300\/?random",
    "photo": {
      "default": "https:\/\/unsplash.it\/500\/500?random"
    },
    "rooms": [
      {
        "id": "5940b6289a892006485be2c3",
        "name": "Studio B"
      }
    ],
    "geo": {
      "lat": 35.2004625,
      "lng": -80.852509
    },
    "appointments": [
      {
        "name": "Coloring Session",
        "description": "Est aspernatur vel praesentium distinctio. Facere molestiae neque ratione modi quia ipsa. Tenetur deserunt adipisci alias laboriosam. Cum nobis repellat molestiae qui deserunt numquam sed.",
        "book_online": true,
        "staff": [
          {
            "id": "5940b6ac9a8920086234b594",
            "name": "Franz Kunze"
          },
          {
            "id": "5940b6a59a8920086234b589",
            "name": "Cecil Kuhn"
          },
          {
            "id": "5940b6aa9a892006423822ed",
            "name": "Zoie Osinski"
          }
        ],
        "id": "5940b6db9a892006485be2e1"
      },
    ],
    "classes": [
      {
        "timeseries": [
          {
            "_id": {
              "$oid": "5940b6f99a8920064238237b"
            },
            "start_date": "11\/18\/2016",
            "end_date": "08\/12\/2018",
            "repeat": "3",
            "days": null,
            "location": {
              "_id": {
                "$oid": "5940b6259a892006485be2bd"
              },
              "name": "Suburbia",
              "timezone": {
                "dstOffset": 3600,
                "rawOffset": -18000,
                "timeZoneId": "America\/New_York",
                "timeZoneName": "Eastern Daylight Time"
              },
              "room": {
                "_id": {
                  "$oid": "5940b6269a892006485be2bf"
                },
                "name": "Yoga Room"
              }
            },
            "expires": false,
            "capacity": 15,
            "start_time": "9:30am",
            "name": "9:30am",
            "staffed_by": {
              "_id": {
                "$oid": "5940b6a59a8920086234b589"
              },
              "name": "Cecil Kuhn",
              "photo": "https:\/\/randomuser.me\/api\/portraits\/men\/0.jpg"
            },
            "description": {
              "full": "Every 3rd Friday of the month at 09:30am until Aug 12th, 2018.",
              "time": "09:30am",
              "days": "Every 3rd Friday of the month",
              "until": "Aug 12th, 2018",
              "repeats": "Monthly"
            }
          }
        ],
        "name": "30-Minute Yoga",
        "description": "Dolores enim aut non quia et veritatis.",
        "category": {
          "_id": {
            "$oid": "5940b6f59a8920086234b5e5"
          },
          "name": "Cycling"
        },
        "id": "5940b6f89a89200642382376",
        "price": "$24.00"
      }
    ],
    "packages": [
      {
        "name": "Ivory Package",
        "description": "Nihil omnis nihil enim officia quo corporis ipsam. Doloremque hic eveniet vel quod hic. Quaerat impedit incidunt tempora et voluptas.",
        "price": "$16.00",
        "id": "5940b73b9a8920086234b651"
      }
    ],
    "products": [
      {
        "name": "T Shirt",
        "description": null,
        "id": "5940b7309a8920086234b634"
      }
    ],
    "staff": [
      {
        "first_name": "Cecil",
        "last_name": "Kuhn",
        "photo": {
          "thumb": "https:\/\/randomuser.me\/api\/portraits\/men\/0.jpg",
          "large": "https:\/\/randomuser.me\/api\/portraits\/men\/0.jpg",
          "original": "https:\/\/randomuser.me\/api\/portraits\/men\/0.jpg"
        },
        "category": {
          "_id": {
            "$oid": "5940b6a59a8920086234b58a"
          },
          "name": "Boat Builder and Shipwright"
        },
        "classes": 4,
        "appointments": 4,
        "id": "5940b6a59a8920086234b589"
      }
    ]
  }
}
```

Retrieves a location's details, as well as services and products offered at the location.

### HTTP Request

`GET https://api.runara.com/locations/{ID}`

### URL Parameters

Parameter | Type | Required | Description | Example
--------- | -------- | -------- | ----------- | -----------
ID | string | true | ID of location to view. | `568b55febffebc91068d4579`
