# Clients

## View Clients

```shell
curl "https://api.runara.com/clients"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns JSON structured like this:

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

```shell
curl "https://api.runara.com/clients/{client}"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns JSON structured like this:

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

```shell
curl "https://api.runara.com/clients"
  -H "Authorization: you.jwt.token"
```

> The above command returns JSON structured like this:

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
