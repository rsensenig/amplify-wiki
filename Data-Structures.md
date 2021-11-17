### Campaigns table
Describes the campaigns and the amount of letters sent for each campaign.
![CampaignTable](https://user-images.githubusercontent.com/66452376/142286849-cc5f817c-8503-4b76-93a0-3902b030f25e.png)

***

### letter_versions table
This data is sent to Lob, primarily **template_id** which is specific to each campaign by **office division**.
This data structure triages the letter object that's being _displayed_ and _sent_, specific to the template_id of the region that's being picked by the office.

​​![LetterVersions](https://user-images.githubusercontent.com/66452376/142286635-02c098db-fa85-4922-952b-0a21abc05a0e.png)

* keyID: use to create join or belong relationships for Users, Campaigns, and Letters sent
* template_id: lob html template
* office_division: each campaign has a different letter dependent on filter. Federal is the default.
* state: Custom versions per state
* county: Custom versions per county
* CampaignID: maps to campaigns table 

***

### letter_sent table
Way to understand volumes of letters being sent. This table will be used to measure conversion for letter_upload, user_volunteer and user_campaign. 
![letter_sent](https://user-images.githubusercontent.com/66452376/142287216-168da2ae-9bb6-48b7-a713-12f2ecc06ed8.png)



