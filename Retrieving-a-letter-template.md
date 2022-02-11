Retrieve a letter template used to create letters for a campaign. Amplify does not store this information; this API integrates with the Lob [Templates API](https://docs.lob.com/#operation/template_retrieve).

## Access a single letter template

Retrieve a template used for creating letters for a campaign.

### GET
 
#### Syntax

`GET /api/lob/templates/:templateId`

:warning: The previous syntax (`/api/lob/:templateId`) has been deprecated and is no longer valid.
 
Example query: `https://murmuring-headland-63935.herokuapp.com/api/lob/templates/1234`

#### Returns

List of JSON objects. 

Note that multiple versions of the same template may be returned. To ensure you are using the most current template, reference the ID of the `published_version`. 

```json
{
  "id": "tmpl_c94e83ca2cd5121",
  "description": "Test Template",
  "versions": [
    {
      "id": "vrsn_362184d96d9b0c9",
      "description": "Test Template",
      "html": "<html>HTML for {{name}}</html>",
      "date_created": "2017-11-07T22:56:10.962Z",
      "date_modified": "2017-11-07T22:56:10.962Z",
      "object": "version"
    }
  ],
  "published_version": {
    "id": "vrsn_362184d96d9b0c9",
    "description": "Test Template",
    "html": "<html>HTML for {{name}}</html>",
    "date_created": "2017-11-07T22:56:10.962Z",
    "date_modified": "2017-11-07T22:56:10.962Z",
    "object": "version"
  },
  "metadata": {},
  "date_created": "2017-11-07T22:56:10.962Z",
  "date_modified": "2017-11-07T22:56:10.962Z",
  "object": "template"
}
```

