# Accounts

## Switch Accounts

Switches the current account of the user, provided the user has access to the account.

<aside class="info">
User must have access to the account before switching to it. If they do not, a `401` response is returned.
</aside>

### HTTP Request

`GET https://api.runara.com/admin/switch/{ID}`

### Route Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
ID | true | ID of account to switch to. | `11234433`
