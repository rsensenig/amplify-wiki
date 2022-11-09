## `campaigns` table 

Describes all campaigns and the number of letters sent for each campaign.

### API reference

[API reference](https://github.com/ProgramEquity/amplify-back-end/wiki/Campaigns-API-Endpoints)  Retrieve information for all campaigns listed in the table or just one.

### Data description

|Column Name|Data Type|Description|
|---|---|---|
|id|integer|Auto-increments with each new campaign added. _(Not editable.)_|
|organization|string|The name of the organization responsible for this campaign.|
|name|string|The name of this particular campaign.|
|cause|enum Must be one of: `Civic Rights`, `Education`, `Climate Justice`|The cause this campaign is supporting.
|type|enum Must be one of: `Starter`, `Accelerator`, `Grant`| The type of campaign this is.
|page_url|text|The URL for this campaign's call to action.|
|letters_counter|integer|The number of letters sent for this campaign.|

_(Editor's note: Could not determine when/how `letters_counter` is modified)_

### Example

![CampaignTable](https://user-images.githubusercontent.com/66452376/142286849-cc5f817c-8503-4b76-93a0-3902b030f25e.png)

***

## `letter_versions` table

This data is sent to Lob, primarily **template_id** which is specific to each campaign by **office division**.  This data structure triages the letter object that's being _displayed_ and _sent_, specific to the `template_id` of the region that's being picked by the office.

### API reference

[API reference](https://github.com/ProgramEquity/amplify-back-end/wiki/Letter_Versions-API-Endpoints)
Returns information about every letter sent for a campaign.

### Data description
|Column Name|Data Type|Description|
|---|---|---|
| id | integer | Auto-increments with each new letter version added. _(Not editable.)_ This is used to create join or belong relationships between Users, Campaigns, and Letters Sent. |
| template_id | string | The Lob html letter template id. |
| office_division | enum Must be one of: `Federal`, `State`, `County`, `Municipality`. Default: `Federal`| Each campaign contains a different letter to enable filtering.  |
| state | string | The state this letter version is for. |
| county | string | The county this letter version is for. |
| CampaignID | integer | Maps this letter to a campaign|

### Example

​​![LetterVersions](https://user-images.githubusercontent.com/66452376/142286635-02c098db-fa85-4922-952b-0a21abc05a0e.png)

***

## `sent_letters` table

A way to understand volumes of letters being sent. This table is used to measure conversion rates for `letter_upload`, `constituent` and `user_campaign`. 

### API reference

None.

### Data description

|Column Name|Data Type|Description|
|---|---|---|
| id | integer | Auto-increments with each new letter sent added. _(Not editable.)_ |
| letter_version_id | integer | Foreign key that references `id` in the `letter_versions` table |
| constituent_id | integer | Foreign key that references `id` in the `constituents` table |
| request_id | string | The Lob API response ID, for tracking and management purposes |
| requested_at | timestamp |  |
| rep_name | string |  |
| rep_address | string | |

### Example
![letter_sent](https://user-images.githubusercontent.com/66452376/142287216-168da2ae-9bb6-48b7-a713-12f2ecc06ed8.png)

***

## `constituents` table

This information is collected from the review letter screen.

### API reference

None.

### Data description

|Column Name|Data Type|Description|
|---|---|---|
|Letters sent|Integer|The id of a letter that was successfully posted with Lob (payment and address verification went through) |
|User agreement|Boolean|User agrees to abide by the platform's best practices |
|Updates||Sends sending `campaign_id` so that we can send to advocacy groups so they can follow up and by our user education team <sup>*</sup> |
|Street address|string||
|City|string||
|State|string||
|Zipcode|string||

<sup>*</sup> _Editor's note: This sentence was left as written._

### Example
![constituent](https://user-images.githubusercontent.com/66452376/142287512-31914818-416b-4c14-b660-1c77abe39167.png)

***

## Stripe Payments Table

### API reference

None.

### Data description

|Column Name|Data Type|Description|
|---|---|---|
| day |timestamp |mm-dd-yyyy |
| id || <sup>*</sup> |
| amount | integer|The amount of the charge or refund. |
| currency |string |Currency identifier|
| source_id | | <sup>*</sup> |
| type |string|Payment type: charge or refund |

<sup>*</sup> _(Editor's note: Do not know what `id` and `source_id` are. It may be that one is the Amplify database identifier and the other is the Stripe identifier, so they can be mapped to each other.)_

### Example
![stripe](https://user-images.githubusercontent.com/66452376/142288686-d305f0e1-c83a-4f7e-bb54-96b37cf39e68.png)
