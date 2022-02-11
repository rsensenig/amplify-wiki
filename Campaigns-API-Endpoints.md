These APIs access information in the `campaigns` [table](https://github.com/ProgramEquity/amplify-front-end/wiki/Data-Structures#campaigns-table).

## Accessing a specific campaign

### GET
 
#### Syntax

`/api/campaigns/:campaignId` 

Example query: `https://murmuring-headland-63935.herokuapp.com/api/campaigns/4`

#### Returns

A JSON object with information for a single, specific campaign identified by `id`.

Example return object:

```json
{
  "campaign": {
    "id": 1,
    "organization": "M4BL",
    "name": "The Breath Act",
    "cause": "Civic Rights",
    "type": "Grant",
    "page_url": "www.thebreatheact.org",
    "letters_sent": 0
  }
}
```

## Accessing all campaigns

### GET
 
#### Syntax

`GET /api/campaigns` 

Example query: `https://murmuring-headland-63935.herokuapp.com/api/campaigns`

#### Returns

An array of JSON objects with information for each campaign in the `campaigns` [table](https://github.com/ProgramEquity/amplify-front-end/wiki/Data-Structures).

Example return object:

```json
{
  "Campaigns": [
    {
      "id": 1,
      "organization": "M4BL",
      "name": "The Breath Act",
      "cause": "Civic Rights",
      "type": "Grant",
      "page_url": "www.thebreatheact.org",
      "letters_sent": 0
    },
    {
      "id": 2,
      "organization": "AAAJ",
      "name": "AAAJ",
      "cause": "Education",
      "type": "Accelerator",
      "page_url": "www.aaaj.org",
      "letters_sent": 0
    }
  ]
}
```

## Adding data to a campaign

:warning: **NOT YET IMPLEMENTED!** :warning:

### POST

#### Syntax

`POST /api/campaigns`