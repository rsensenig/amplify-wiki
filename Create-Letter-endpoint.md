Create a new letter and specify a letter template. Amplify does not store this information; this API leverages the Lob [createLetter API](https://docs.lob.com/#operation/letter_create)

### POST

`POST /api/createLetter`

#### Syntax

Request body parameters

|Name|Type|Description|
|---|---|---|
|description|string|A description that uniquely identifies this letter. Must be no longer than 255 characters.|
|to|object|_parameters below_|
|from|object|_parameters below_|
|templateId|string|The Lob `template_id` created for this letter.|
|sessionId|string|Stripe session id returned from checkout session redirect or from Stripe [API](https://stripe.com/docs/api/checkout/sessions/retrieve).|

`to` is an address object with the following parameters. This address will be [verified](https://docs.lob.com/#operation/us_verification), recorded, and assigned an ID, if possible, when submitted.

```
{
name: 'Amy',
address_line1: 'Address line 1',
address_line2: 'Address line 2',
address_city: 'San Francisco',
address_state: 'CA',
address_zip: '94101'
}
```

`from`: is an object with the following parameter, which is an integer.

```
{
address_id: The `address_id` returned from the `createAddress` endpoint
}
```