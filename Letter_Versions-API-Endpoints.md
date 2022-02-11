Retrieve all versions of each letter, including the template id, sent out for a campaign.

### GET
 
#### Syntax

`api/Letter_Versions/:campaignid`
 
Sample query: `https://murmuring-headland-63935.herokuapp.com/api/Letter_Versions/1`

#### Returns

A list of JSON objects. For details on each parameter retrieved, see the `letter_versions` [database table](https://github.com/ProgramEquity/amplify-front-end/wiki/Data-Structures#letter_versions-table).

```json

[
{"id":1,"template_id":"tmpl_1057bb6f50f81fb ","campaign_id":1,"office_division":"Federal","state":null,"county":null,"municipality":null},
{"id":2,"template_id":"tmpl_1057bb6j23k81fg","campaign_id":1,"office_division":"State","state":"California","county":null,"municipality":null},
{"id":3,"template_id":"tmpl_1057bb322qwj2f","campaign_id":1,"office_division":"County","state":"California","county":null,"municipality":null}
]

```