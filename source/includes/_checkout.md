# Checkout

Checkout endpoints create and modify a shopping cart on the Runara platform. All account purchases are managed through the Checkout interface.

<aside class="notice">
All checkout endpoints return the same 204 response and schema unless an error is encountered.
</aside>

<aside class="notice">
There is no endpoint or action for cancelling/abandoning a cart. You may re-start a checkout process at any time with the same client without any conflicts with data, provided you submit the updated "cart" ID.
</aside>

## Create an Empty Cart

> Empty Cart Response:

```json
{
  "data": {
    "id": 1939,
    "payments_id": 0,
    "meta": {
      "flags": {
        "is_deposit_payment": null,
        "limited_to_single": null,
        "needs_secondary_payment": false,
        "pay_at_checkout": null,
        "purchase_type_defaulted": null,
        "ready_to_complete": false,
        "promo_enabled": false,
        "gratuity_enabled": true
      },
      "payment_options": [
        {
          "value": "card_100526",
          "name": "Visa ending in 4242",
          "class": "card-visa",
          "disabled": true
        },
        {
          "value": "cash",
          "name": "Cash",
          "class": "card-cash",
          "disabled": true
        }
      ],
      "credit_options": []
    },
    "status": "pending",
    "client": {
      "id": 100110,
      "first_name": "Tucker",
      "last_name": "Tuckerson",
      "email": "tucker@gmail.com",
      "photo": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photos\/photo_1520391437_thumb.jpg"
    },
    "items": [],
    "promos": null,
    "gratuity": null,
    "payment_option": null,
    "closeout": false,
    "sub_total": "$0.00",
    "tax_taxable": "0.00",
    "tax_rate": "0.00",
    "tax_total": "$0.00",
    "total": "$0.00"
  }
}
```

Create an empty cart to initialize it if you do not yet know which items the client would like to purchase.

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | User ID of client | `11223344`


### HTTP Request

`POST https://api.runara.com/cart`

## Create a Cart with Items Added

> Cart response with a Class/Session combo added

```json
{
  "data": {
    "id": 1940,
    "payments_id": 0,
    "meta": {
      "flags": {
        "is_deposit_payment": null,
        "limited_to_single": null,
        "needs_secondary_payment": false,
        "pay_at_checkout": null,
        "purchase_type_defaulted": true,
        "ready_to_complete": false,
        "promo_enabled": true,
        "gratuity_enabled": true
      },
      "payment_options": [
        {
          "value": "card_100526",
          "name": "Visa ending in 4242",
          "class": "card-visa",
          "disabled": false
        },
        {
          "value": "cash",
          "name": "Cash",
          "class": "card-cash",
          "disabled": false
        },
        {
          "value": "checkin",
          "name": "Pay at Check-In",
          "class": "card-cash",
          "disabled": false
        }
      ],
      "credit_options": [],
      "limited_to_single": false
    },
    "status": "pending",
    "client": {
      "id": 100110,
      "first_name": "Tucker",
      "last_name": "Tuckerson",
      "email": "tucker@gmail.com",
      "photo": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photos\/photo_1520391437_thumb.jpg"
    },
    "items": [
      {
        "item_name": "Advanced Pilates",
        "item_type_id": 1,
        "item_type": "Booking",
        "sub_type": "class",
        "item_id": 100115,
        "sku": null,
        "qty": 1,
        "price": "$5.00",
        "sub_total": "$5.00",
        "total": "$5.00",
        "staffed_by": {
          "id": 100115,
          "name": "Desmond Mann",
          "photo": "https:\/\/randomuser.me\/api\/portraits\/women\/0.jpg"
        },
        "location": {
          "id": 100118,
          "name": "Pineville"
        },
        "session_date": 1532706000,
        "session_date_formatted": "Friday, Jul 27th at 11:40am",
        "purchase_type": "Single Session",
        "purchase_type_id": "single",
        "purchase_price": "5.00",
        "purchase_options": [
          {
            "value": "single",
            "name": "Single Session",
            "label": "Single Session - $5.00",
            "price": "5.00",
            "description": null,
            "expires": null,
            "selected": true
          },
          {
            "value": "pkg_100121-100115",
            "name": "Package - 5 Sessions",
            "label": "Package - 5 Sessions for $50.00",
            "price": "50.00",
            "description": "5 Sessions",
            "expires": "Expires in 90 days",
            "selected": false
          },
          {
            "value": "pkg_100122-100115",
            "name": "Package - 10 Sessions",
            "label": "Package - 10 Sessions for $80.00",
            "price": "80.00",
            "description": "10 Sessions",
            "expires": "Does not expire.",
            "selected": false
          },
          {
            "value": "pkg_100123-100115",
            "name": "Package - 25 Sessions",
            "label": "Package - 25 Sessions for $125.00",
            "price": "125.00",
            "description": "25 Sessions",
            "expires": "Does not expire.",
            "selected": false
          }
        ],
        "limited_to_single": false
      }
    ],
    "promos": null,
    "gratuity": null,
    "payment_option": null,
    "closeout": false,
    "sub_total": "$5.00",
    "tax_taxable": "0.00",
    "tax_rate": "0.00",
    "tax_total": "$0.00",
    "total": "$5.00"
  }
}
```

You can also create a cart with items already added.

### HTTP Request

`POST https://api.runara.com/cart`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | User ID of client | `11223344`

### Example: Add a class session:

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
item | true | Item to add to cart. | `class-11223344`
session | true | Session ID to book. | `100133-1532706000`

## Add an Item

> Cart response with a product added

```json
{
  "data": {
    "id": 1941,
    "payments_id": 0,
    "meta": {
      "flags": {
        "is_deposit_payment": null,
        "limited_to_single": null,
        "needs_secondary_payment": false,
        "pay_at_checkout": null,
        "purchase_type_defaulted": null,
        "ready_to_complete": false,
        "promo_enabled": true,
        "gratuity_enabled": true
      },
      "payment_options": [
        {
          "value": "card_100526",
          "name": "Visa ending in 4242",
          "class": "card-visa",
          "disabled": false
        },
        {
          "value": "cash",
          "name": "Cash",
          "class": "card-cash",
          "disabled": false
        }
      ],
      "credit_options": []
    },
    "status": "pending",
    "client": {
      "id": 100110,
      "first_name": "Tucker",
      "last_name": "Tuckerson",
      "email": "tucker@gmail.com",
      "photo": "https:\/\/s3-us-west-2.amazonaws.com\/runara\/users\/profiles\/photos\/photo_1520391437_thumb.jpg"
    },
    "items": [
      {
        "item_name": "T Shirt - #519608",
        "item_type_id": 2,
        "item_type": "Product",
        "sub_type": "product",
        "item_id": 100111,
        "sku": "519608",
        "qty": 1,
        "price": "$25.00",
        "sub_total": "$25.00",
        "total": "$25.00",
        "staffed_by": {
          "id": 0,
          "name": null,
          "photo": null
        },
        "location": {
          "id": 0,
          "name": null
        },
        "session_date": null,
        "session_date_formatted": "Wednesday, Dec 31st at 7:00pm",
        "purchase_type": null,
        "purchase_type_id": null,
        "purchase_price": null,
        "purchase_options": [],
        "limited_to_single": false
      }
    ],
    "promos": null,
    "gratuity": null,
    "payment_option": null,
    "closeout": false,
    "sub_total": "$25.00",
    "tax_taxable": "0.00",
    "tax_rate": "0.00",
    "tax_total": "$0.00",
    "total": "$25.00"
  }
}
```

Adds and item to an existing cart.

You can add an item to a cart provided it meets the following conditions:

* Items can not be added to an initial booking of a class or appointment.
* Only one pass or package is allowed for each purchase.

### HTTP Request

`POST https://api.runara.com/cart/items/add`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | User ID of client | `11223344`
cart | true | ID of cart to add item to | `11223344`

*The above parameters are required for each of the examples below*

### Example: Add a product:

<aside class="notice">
Products are passed as a combination of product and SKU.
</aside>

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
item | true | Item to add to cart. | `product-11223344-323423`
qty | false | Quantity of product/SKU to add. Default: `1`. | `1`

### Example: Add a booking:

<aside class="notice">
Bookings are passed as a pair of class/appointment ID and session ID.
</aside>

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
item | true | Item to add to cart. | `class-11223344` or `appt-11223344`
session | true | Session ID to book. | `100133-1532706000`

### Example: Add a package:

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
item | true | Package to add to cart. | `package-11223344`

### Example: Add a pass:

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
item | true | Pass to add to cart. | `pass-11223344`

## Remove an Item

Removes an item from an existing cart.

### HTTP Request

`POST https://api.runara.com/cart/items/remove`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | User ID of client | `11223344`
cart | true | ID of cart to add item to | `11223344`
item | true | ID of item to remove | `11223344`

<aside class="notice">
The "item" parameter is the item id of the cart.items object, not the item itself. ("11223344" vs. "product-112233-334411").
</aside>

## Update Item Quantity

Updates the quantity of a single item added to cart.

<aside class="notice">
Quantity only applies to products. Other items are single-purchase only.
</aside>

### HTTP Request

`POST https://api.runara.com/cart/items/remove`

### BODY Parameters

Parameter | Required | Description | Example
--------- | ----------- | ----------- | -----------
client | true | User ID of client | `11223344`
cart | true | ID of cart to add item to | `11223344`
item | true | ID of item to remove | `11223344`
qty | true | Quantity of item to purchase. | `4`

**Note:** The following validation occurs when adjusting quantity:

* If `qty` is `0`, the item will be removed
* If `qty` is greater than inventory on-hand, a 422 validation error will be returned.
