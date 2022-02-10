## Campaigns table

Describes all campaigns and the number of letters sent for each campaign.

### API reference

[API reference](https://github.com/ProgramEquity/amplify-back-end/wiki/Campaigns-API-Endpoints) Retrieving information for all campaigns in the table or just one.

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

(something is modding `letters_counter`, have not yet identified when and how often)

### Example

![CampaignTable](https://user-images.githubusercontent.com/66452376/142286849-cc5f817c-8503-4b76-93a0-3902b030f25e.png)

***

## letter_versions table

This data is sent to Lob, primarily **template_id** which is specific to each campaign by **office division**.
This data structure triages the letter object that's being _displayed_ and _sent_, specific to the template_id of the region that's being picked by the office.

### API reference

[API reference](https://github.com/ProgramEquity/amplify-back-end/wiki/Letter_Versions-API-Endpoints)

Returns information about letter versions using a `campaignid` as a search key.

### Data description
|Column Name|Data Type|Description|
|---|---|---|
| id | integer | Auto-increments with each new letter version added. _(Not editable.)_ . This is used to create join or belong relationships for Users, Campaigns, and Letters sent. |
| template_id | string | The lob html template id. |
| office_division | enum Must be one of: `Federal`, `State`, `County`, `Municipality` | Each campaign has a different letter dependent on filter. Federal is the default. |
| state | string | The state this letter version is for. |
| county | string | The county this letter version is for. |
| CampaignID | integer | Used to map to campaigns table |

### Example

​​![LetterVersions](https://user-images.githubusercontent.com/66452376/142286635-02c098db-fa85-4922-952b-0a21abc05a0e.png)

***

## Letter Sent table
Way to understand volumes of letters being sent. This table will be used to measure conversion for letter_upload, user_volunteer and user_campaign. 

### API reference

### Data description
|Column Name|Data Type|Description|
|---|---|---|
| id | integer | Auto-increments with each new letter sent added. _(Not editable.)_ |
| letter_version_id | integer | foreign key that references `id` in the `letter_versions` table |
| volunteer_id | integer | foreign key that references `id` in the `volunteers` table |
| request_id | string | the Lob API response ID, for tracking and management purposes |
| requested_at | timestamp |  |
| rep_name | string |  |
| rep_address | string | |

### Example
![letter_sent](https://user-images.githubusercontent.com/66452376/142287216-168da2ae-9bb6-48b7-a713-12f2ecc06ed8.png)

***

## Constituent Table
*This information is collected from review letter screen
* Letters sent holds id of letter that was successfully posted with Lob (payment and address verification went through) 
* User agreement is a boolean that they abide by the platforms best practices 
* Updates is sending campaign_id so that we can send to advocacy groups so they can follow up and by our user education team 
* Street address, City, and State are strings
* Zipcode is a string
### API reference

### Data description
|Column Name|Data Type|Description|
|---|---|---|

### Example
![constituent](https://user-images.githubusercontent.com/66452376/142287512-31914818-416b-4c14-b660-1c77abe39167.png)


***

## Stripe Payments Table

### API reference

### Data description
|Column Name|Data Type|Description|
|---|---|---|
| day | | |
| id | | |
| amount | | |
| currency | | |
| source_id | | |
| type | | |
### Example
![stripe](https://user-images.githubusercontent.com/66452376/142288686-d305f0e1-c83a-4f7e-bb54-96b37cf39e68.png)

## Volunteer user table

### API reference

### Data description
|Column Name|Data Type|Description|
|---|---|---|
| name | string| |
| address | string | |
| letters | array of string `template_id` | |

### Example


