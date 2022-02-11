This API returns the list of Representatives based on Zip code. Amplify does not store any data; this API leverages the Google [Civic Information API](https://developers.google.com/civic-information).

### GET
 
#### Syntax

`GET /api/representatives/:zipCode`

Example query: `https://murmuring-headland-63935.herokuapp.com/api/representatives/98052`

#### Returns

A list of JSON objects with Representative information for the provided Zip code.

Example _partial_ return object for zip code `98052`:

```json
{
    "name": "Maria Cantwell",
    "title": "U.S. Senator",
    "address_line1": "511 Hart Senate Office Building",
    "address_city": "Washington",
    "address_state": "DC",
    "address_zip": "20510",
    "address_country": "US",
    "email": "Not Made Public",
    "twitter": "SenatorCantwell",
    "facebook": "senatorcantwell",
    "photoUrl": "http://bioguide.congress.gov/bioguide/photo/C/C000127.jpg"
}
```

## Troubleshooting errors

* The zip code must be in either the 5-digit Zip format (`99999`) or 9-digits Zip+4 format (`99999-9999`).
* If the zip code format is correct, but the value is not a valid zip code (such as `99999`), it will fail with a `500 Internal Server Error`. The error text says: `{"error":"Whoops"}`
* If the zip code format is incorrect (such as `dog`), it will fail with a `400 Bad Request` error. The error text says: `{"error":"Invalid zip code format, valid examples are 84054-6013 or 84054. The zip code used was dog"}`
* This API leverages the Google [Civic Information API](https://developers.google.com/civic-information). This API is free, but it has quotas of 25,000 requests per day, 2500 requests per 100 seconds, and 100 requests per 100 seconds per user. Exceeding these limits may result in a `429 Too Many Requests` error.
* This API does not return the President and Vice President. It also does not return every possible field retrieved by the 
Civic Information API. This is deliberate, and not an error.