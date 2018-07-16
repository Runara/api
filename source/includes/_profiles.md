# Profiles

## Get User Profile

```shell
curl "https://api.runara.com/profile"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "sd5763ce9a89201a8f515fa4",
    "email": "user.name@email.com",
    "first_name": "Mike",
    "last_name": "Jones",
    "photo": {
      "default": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_default.jpg",
      "thumb": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_thumb.jpg"
    },
    "street": null,
    "street_2": null,
    "city": null,
    "state": null,
    "postal": null
  }
}
```

Returns the profile of the user requesting the endpoint.

### HTTP Request

`GET https://api.runara.com/profiles`

## Update Profile

```shell
curl "https://api.runara.com/profiles"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "sd5763ce9a89201a8f515fa4",
    "email": "user.name@email.com",
    "first_name": "Mike",
    "last_name": "Jones",
    "photo": {
      "default": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_default.jpg",
      "thumb": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_thumb.jpg"
    },
    "street": null,
    "street_2": null,
    "city": null,
    "state": null,
    "postal": null
  }
}
```

Updates a user's profile.

<aside class="notice">
If a new email address is provided, the user will no longer be able to log-in with their previously-stored address. User will be notified via email of the change.
</aside>

### HTTP Request

`POST https://api.runara.com/profile/update`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
first_name | true | User's first name. | `Jason`
last_name | true | User's last name. | `Vorhees`
email | true | User's email address. | `user@email.com`
street | false | User's street address. | `123 Yellow Ln`
street_2 | false | User's street address extension. | `#4567`
city | false | User's city. | `Hollywood`
state | false | User's state. | `CA`
postal | false | User's postal code. | `90210`

## Update Profile Photo

```shell
curl "https://api.runara.com/profiles"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "sd5763ce9a89201a8f515fa4",
    "email": "user.name@email.com",
    "first_name": "Mike",
    "last_name": "Jones",
    "photo": {
      "default": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_default.jpg",
      "thumb": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photo_1484882588_thumb.jpg"
    },
    "street": null,
    "street_2": null,
    "city": null,
    "state": null,
    "postal": null
  }
}
```

Updates or adds a user's profile photo.

<aside class="notice">
Photo is automatically duplicated and resized twice upon upload.
</aside>

### HTTP Request

`POST https://api.runara.com/profile/photo`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
image | true | Image file | `[FILE]`

## Remove Profile Photo

```shell
curl "https://api.runara.com/profiles"
  -H "Authorization: Bearer:your.jwt.token"
```

```javascript
const runara = require('runara');

let api = runara.authorize('you.jwt.token');
let kittens = api.kittens.get();
```

> The above command returns JSON structured like this:

```json
{
  "data": {
    "id": "sd5763ce9a89201a8f515fa4",
    "email": "user.name@email.com",
    "first_name": "Mike",
    "last_name": "Jones",
    "photo": {
      "default": null,
      "thumb": null
    },
    "street": null,
    "street_2": null,
    "city": null,
    "state": null,
    "postal": null
  }
}
```

Removes a user's profile photo.

### HTTP Request

`DELETE https://api.runara.com/profile/photo`
