Validate an address to ensure that mailings will arrive. Amplify does not store this information; this API integrates with the Lob [US Verification API](https://docs.lob.com/#operation/us_verification).

## Verify a mailing address

Evaluates a single `address` object to determine if it is a valid, deliverable, residential address within the United States.

### POST

#### Syntax

`api/lob/addressVerification`

Sample query: `https://murmuring-headland-63935.herokuapp.com/api/lob/addressVerification`

Sample body:

```json
{"line1":"123 Street Name","line2":null,"city":"SomeCity","state":"CA","zip":"12345-6789"}
````

#### Returns

* Success: `Status 200`. The address is valid as written.
* Success: `Status 200`. The address is valid, but there is a `warning`, and a `revisedAddress` object. Example: The address is deliverable, but suite number "300" does not exist.
* Fail: `Status 400`. The address is invalid. Example: The zip code is only 4 digits.
* Fail: `Status 400`. The address is not deliverable. Non-residential addresses, PO boxes, and addresses in Puerto Rico are not supported.