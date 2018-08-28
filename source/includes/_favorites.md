# Favorites

Favorites allow clients easy-access to commonly-used businesses. When a client purhcases from a new business, that business (and location) will be automatically added to their favorites.

## View User Favorites

> Example Response:

```json
{
  "data": [
    {
      "id": 59,
      "users_id": 100110,
      "accounts_id": 100110,
      "locations_id": 100116,
      "name": "Body by Keelay - 123 Main",
      "street": "15235 John J Delaney Dr",
      "street_2": null,
      "city": "Charlotte",
      "state": "NC",
      "postal": "28277",
      "categories": [
        {
          "id": 100110,
          "name": "Barre"
        },
        {
          "id": 100113,
          "name": "Dance"
        },
        {
          "id": 100115,
          "name": "Gym"
        }
      ],
      "photo": {
        "default": null,
        "original": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/locations\/photos\/photo_1519872697_orig.png"
      },
      "geo": {
        "lat": 35.0539776,
        "lng": -80.8486842
      }
    },
    {
      "id": 67,
      "users_id": 100110,
      "accounts_id": 100111,
      "locations_id": 100113,
      "name": "5x5 Inc - Center City",
      "street": "1400 Central Ave",
      "street_2": null,
      "city": "Charlotte",
      "state": "NC",
      "postal": "28205",
      "categories": [
        {
          "id": 100110,
          "name": "Barre"
        },
        {
          "id": 100113,
          "name": "Dance"
        }
      ],
      "photo": {
        "default": null,
        "original": null
      },
      "geo": {
        "lat": 35.2195292,
        "lng": -80.8145677
      }
    }
  ]
}
```

Returns the clients's favorites list.

<aside class="info">
If you wish to view the favorites of a different client, you can change the method of this request to POST and pass the client's ID as "client".
</aside>

### HTTP Request

`GET https://api.runara.com/accounts/favorites`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
client | false | ID of client if not current client. | `234334`

## Manage User Favorites

> Example Response:

```json
{
  "data": [
    {
      "id": 59,
      "users_id": 100110,
      "accounts_id": 100110,
      "locations_id": 100116,
      "name": "Body by Keelay - 123 Main",
      "street": "15235 John J Delaney Dr",
      "street_2": null,
      "city": "Charlotte",
      "state": "NC",
      "postal": "28277",
      "categories": [
        {
          "id": 100110,
          "name": "Barre"
        },
        {
          "id": 100113,
          "name": "Dance"
        },
        {
          "id": 100115,
          "name": "Gym"
        }
      ],
      "photo": {
        "default": null,
        "original": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/locations\/photos\/photo_1519872697_orig.png"
      },
      "geo": {
        "lat": 35.0539776,
        "lng": -80.8486842
      }
    },
    {
      "id": 67,
      "users_id": 100110,
      "accounts_id": 100111,
      "locations_id": 100113,
      "name": "5x5 Inc - Center City",
      "street": "1400 Central Ave",
      "street_2": null,
      "city": "Charlotte",
      "state": "NC",
      "postal": "28205",
      "categories": [
        {
          "id": 100110,
          "name": "Barre"
        },
        {
          "id": 100113,
          "name": "Dance"
        }
      ],
      "photo": {
        "default": null,
        "original": null
      },
      "geo": {
        "lat": 35.2195292,
        "lng": -80.8145677
      }
    }
  ]
}
```

Adds or removes (favorites or un-favorites) a location for a client. If client already has the `location` marked as favorite, then this action will un-favorite the locaton.

### HTTP Request

`POST https://api.runara.com/accounts/favorite`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
location | true | ID of location to favorite. | `2343432`
