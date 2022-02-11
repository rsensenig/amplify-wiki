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
|template_id|string|The Lob `template_id` created for this letter.|
|charge|<sup>*</sup> |Pass in the charge that was created by the user|

`to` is an address object with the following parameters. This address will be [verified](https://docs.lob.com/#operation/us_verification), recorded, and assigned an ID, if possible, when submitted.

```
{
name: 'Amy',
line1: 'Address line 1',
line2: 'Address line 2',
city: 'San Francisco',
state: 'CA',
zip: '94101'
}
```

`from`: is an object with the following parameter, which is an integer.

```
{
address_id: The `address_id` returned from the `createAddress` endpoint
}
```

<sup>*</sup> 2/10/22 Editor's Note: `charge` was not defined and could not be found in the [Lob documentation](https://docs.lob.com/#operation/letter_create). Perhaps it is something submitted by the user via a UI element?