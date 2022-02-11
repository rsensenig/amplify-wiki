
Brief summary of each API's endpoints. For details, click the `Full API reference` links on this page or in the sidebar.

### Address Verification 

[Full API Reference](Validating-a-mailing-address)

Endpoints to validate constituent/volunteer residential addresses and send physical mailings via the Lob API.
:warning: The previous syntax (`GET /api/lob/:templateId`) has been **deprecated** and is no longer valid.

| Query | Result |
|---|---|
| `POST /api/lob/addressVerification` | Verifies if a single Address object is considered a valid, deliverable, residential address within the United Status. |

### Campaigns

[Full API Reference](Campaigns-API-Endpoints)

Endpoints to retrieve internal information about campaigns being supported by ProgramEquity. Future implementation will enable adding data to the `campaigns` table.

| Query | Result |
|---|---|
| `GET /api/campaigns` | Returns list of Campaigns |
| `GET /api/campaigns/:id` | Returns a single campaign object based on `id` path parameter. |
|:warning: **NOT YET IMPLEMENTED!**<br /> `POST /api/campaigns` | Provides ability to integrate and submit data to the `campaigns` database table.|

### Create Letter

Create a new letter and specify a letter template.

[Full API Reference](Create-Letter-endpoint)

### Letter Versions

[Full API Reference](Letter_Versions-API-Endpoints)

Endpoints related to the letters uploaded per campaign into Lob.

| Query | Result |
|---|---|
| `GET /api/letter_versions/:campaignId` | Provides ability to retrieve data from `letter_versions` database based on the associated `campaignId` path parameter. For example, `display_letter` uses it to return a Lob HTML object. |
| :warning: **NOT YET IMPLEMENTED!** <br /> `GET /api/letter_versions/???` | Returns a single Letter object based on some parameter.|
| :warning: **NOT YET IMPLEMENTED!**<br />`POST /api/letter_versions/???` | Provides ability to integrate and submit data to the `letter_versions` database table. |

### Letter templates

[Full API Reference](Retrieving-a-letter-template)

Accessing a letter template used in a campaign.

:warning: The previous syntax (`GET /api/lob/:templateId`) has been **deprecated** and is no longer valid.

| Query | Result |
|---|---|
| `GET /api/lob/templates/:templateId` | Returns a single Letter Template object for a campaign based on `templateId` path parameter.|

### Representatives

[Full API Reference](Representatives-API-Endpoints)

Endpoints to retrieve public information about government representatives via the Google Civic API.

| Query | Result |
|---|---|
| `GET /api/representatives/:zipCode` | Returns list of Representatives based on `zipCode` path parameter. |

### Volunteers

:warning: **NOT YET IMPLEMENTED!** Endpoints related to constituents/volunteers.

| Query | Result |
|---|---|
| :warning: **NOT YET IMPLEMENTED!**<br />`GET /api/volunteers/:volunteerId` | Returns a single Volunteer object based on the `volunteerId` path parameter.|
| :warning: **NOT YET IMPLEMENTED!**<br />`POST /api/volunteers/???` | Provides ability to integrate and submit data to the `volunteers` database table. |
