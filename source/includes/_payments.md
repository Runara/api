# Payments

## Add an Account Credit

```shell
curl "https://api.runara.com/payments/credit"
  -H "Authorization: Bearer:your.jwt.token"
```

Add an account credit to a client.

### HTTP Request

`POST https://api.runara.com/payments/credit`

### BODY Parameters

Parameter | Required | Description | Example
--------- | -------- | ----------- | -----------
customer | true | ID of client. | `234432`
credit_type | true | Type of credit to add. | One of `amount`, `class` or `appointment`
amount | true if credit_type = `amount` | Currency amount to add to client. | `20.00`
class | true if credit_type = `class` | Class ID to credit. | `234432`
appointment | true if credit_type = `appointment` |  Appointment ID to credit. | `444323`
reason | false | Reason for credit. | `Could not complete original transaction.`
