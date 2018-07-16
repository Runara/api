# Checkout

## Create Checkout (Cart) Item(s)

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

Creates a new checkout item, ready to have products/payment added.

### HTTP Request

`POST https://api.runara.com/profiles`

## Update Checkout Cart

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
    "id": "588676099a892004b8252ada",
    "client": {
      "id": "583e37e09a89202eba73abc2",
      "first_name": "Tucker",
      "last_name": "Wuori"
    },
    "items": [
      {
        "_id": "57eb32929a892032fe369709",
        "type": "package",
        "name": "Orchid Package",
        "qty": 3,
        "price": "40.00"
      }
    ],
    "payment": null
  }
}
```

Updates a cart's contents.

### HTTP Request

`POST https://api.runara.com/cart/:cart_id`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
itmes | false | Cart Items | Object
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

## Add a Gratuity

```shell
curl "https://api.runara.com/cart/gratuity"
  -H "Authorization: Bearer:your.jwt.token"
```

> The above command returns the cart JSON response.

Adds a gratuity amount to a checkout.

<aside class="notice">
To update / remove a gratuity, just pass in a new amount to overwrite the existing amount.
</aside>

### HTTP Request

`POST https://api.runara.com/cart/gratuity`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
cart | true | ID of cart | `sd5763ce9a89201a8f515fa4`
amount | true | Gratuity amount | `5.00`
