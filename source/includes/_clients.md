# Clients

## View Clients

> Example Response:

```json
{
  "data": [
    {
      "id": "595b26a99a89204afc2fb2c4",
      "first_name": "Nestor",
      "last_name": "DuBuque",
      "email": "leffler.georgette@yahoo.com",
      "phone": null,
      "photo": {
        "original": 'http://url.to.photo/photo.jpg',
        "thumb": 'http://url.to.photo/photo.jpg',
      }
    },
    {
      "id": "595b03a89a89204afe458627",
      "first_name": "Kenyon",
      "last_name": "Hartmann",
      "email": "jblick@wisozk.com",
      "phone": null,
      "photo": {
          "original": 'http://url.to.photo/photo.jpg',
          "thumb": 'http://url.to.photo/photo.jpg',
      }
    }
  ]
}
```

Views a list of clients associated with the requesters current account.

### HTTP Request

`GET https://api.runara.com/clients`

## View Client Details

> Example Response:

```json
{
  "data": {
    "id": "57be63229a89201a8f515fa4",
    "first_name": "Michael",
    "last_name": "McGuirt",
    "email": "michaelmcg@gmail.com",
    "phone": "333-444-5555",
    "photo": {
      "default": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1496448339_default.jpg",
      "thumb": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1496448339_thumb.jpg"
    },
    "packages": [
      {
        "id": "5940b73a9a892006485be2ef",
        "name": "Grand Package"
      }
    ],
    "passes": [
      {
        "id": "597173179a8920268225f3d3",
        "name": "Monthly Membership"
      }
    ],
    "recent_purchases": [
      {
        "id": "598935a99a89202b3d28fe56",
        "type": "Booking",
        "date": "Aug 7th 2017",
        "status": "Complete",
        "total": "$48.00",
        "receipt": "http:\/\/app.runara.app\/payments\/view\/598935a99a89202b3d28fe56"
      },
      {
        "id": "598900199a892025a41725c4",
        "type": "Booking",
        "date": "Aug 7th 2017",
        "status": "Complete",
        "total": "$48.00",
        "receipt": "http:\/\/app.runara.app\/payments\/view\/598900199a892025a41725c4"
      }
    ]
  }
}
```

Displays client details for the current account.

### HTTP Request

`GET https://api.runara.com/clients/{client}`

### URL Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
client | true | ID of client. | `568b55febffebc91068d4579`

## Add a Client

> Example Response:

```json
{
  "data": {
    "_id": "599663689b89200e091e9474",
    "first_name": "John",
    "last_name": "Smith",
    "client_of": [
      {
        "_id": {
          "$oid": "5943b4a89a892006485be28b"
        },
        "name": "Curves2Go"
      }
    ],
    "accounts": [

    ],
    "photo": {
      "original": null,
      "thumb": null
    },
    "recent": {
      "upcoming": [

      ],
      "past": [

      ],
      "packages": [

      ],
      "locations": [

      ]
    },
    "credits": [

    ],
    "favorites": [

    ],
    "email": "m.i.chaelwuori@gmail.com",
    "updated_at": "2017-08-17 23:47:52",
    "created_at": "2017-08-17 23:47:52"
  }
}
```

This endpoint adds a client to the requestor's current account.

<aside class="notice">
If the client has an existing Runara account, the client's existing account becomes associated with your account as opposed to creating a new user record.
</aside>

### HTTP Request

`POST https://api.runara.com/clients`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
email | true | Email address of the client. | `user@domain.com`
first_name | true | Client's First Name. | `Harry`
last_name | true | Client's Last Name. | `August`

## Get recent activity

> Example Response:

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
