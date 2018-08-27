# Accounts

## Switch Accounts

Switches the current account context of the user.

<aside class="info">
User must have access to the account before switching to it. If they do not, a 401 response is returned.
</aside>

### HTTP Request

`GET https://api.runara.com/accounts/switch/{ID}`

### URL Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
ID | true | ID of account to switch to. | `1111034`

## View User Favorites

> Example Response:

```json
{
    "data":{
        [
          {
            "name": "Curves2Go",
            "locations": [
              {
                "name": "West End",
                "id": "234343"
              }
            ],
            "id": "2344342"
          }
        ]
    }
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
    "data":{
        [
          {
            "name": "Curves2Go",
            "multiple": true,
            "locations": [
              {
                "name": "West End",
                "id": "234343"
              }
            ],
            "id": "234334"
          }
        ]
    }
}
```

Adds or removes (favorites or un-favorites) a location for a client. If client already has the `location` marked as favorite, then this action will un-favorite the locaton.

### HTTP Request

`POST https://api.runara.com/accounts/favorite`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
location | true | ID of location to favorite. | `2343432`
