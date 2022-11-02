# Amplify Components
The Amplify app has a number of Vue components, which are documented here. Check back frequently for the most recent information. To report errata or suggest changes, email glenn@piludu.io or message Glenn on Slack.

## ActionComplete.vue
_Last updated: 10/1/2022_

This component renders when a user completes the check-out process after generating a campaign letter. It will show the letter delivery date, the donation amount, and other campaign-related sub-components. Because Stripe payments require a redirect away from Amplify, this component will use the _sessionId_ query parameter from Stripe to restore local state, which is stored in a user's Local Storage.

Importantly, this component is also responsible for creating a transaction record for the previously complete check-out.

**Props:** none.

**Data:**
  * loading _boolean_: If true, a loading animation will render while the transaction is recorded and campaign letter are generated.
  * email _string_: User's email address. Returned by the back-end when a transaction is recorded but currently has no use.
  * amount _number_: The amount of a user's campaign donation, in cents. Returned from createTransactionRecord (which it gets from the Stripe API). Shown in success message.
  * expectedDeliveryDate _string_: The expected campaign letter delivery date returned from LOB API.
  * congressMembers _array of objects_: List of congress people to display in subcomponent. Currently not implemented.

**Computed Properties:**
  * donationAmount _number_: amount converted from cents to dollars.
  * selectedRep _string_: Returns from local state the Representative that was selected during the campaign letter generation process.
  * userData _object_: Returns from local state user data to send to LOB API.
  * letterId _string_: Returns from local state the campaign letter template id for LOB.
  * lobReturnAddressId _string_: Returns from local state the return address id generated during the letter creation process.

**Methods:**
  * createTransactionRecord(sessionId: string): void
    * Verifies Stripe payment on the Amplify back-end and records the transaction into Amplify's database. Returns nothing, but modifies _amount_ and _email_ data attributes.
  * createCampaignLetter(sessionId: string): void
    * Creates a campaign letter with LOB. Returns nothing, but modifies _expectedDelieryDate_ and _loading_ data attributes.


&nbsp;
## AppFooter.vue
_Last updated: 10/1/2022_

This component defines the footer of Amplify. It should hold important legalese, as well as site navigation and social media links.

**Props:** none.

**Data:**
  * icons _string[ ]_: A list of icon identifiers for social media buttons.

**Computed Properties:** none.

**Methods:** none.



&nbsp;
## AppHeader.vue
_Last updated: 10/1/2022_

This component controls the navigation bar for the app.

**Props:** none.

**Data:**
  * dialog _boolean_: Present, but unused.
  * menuItems _Array<string, string>_: List of navigation links and their paths.

**Computed Properties:** none.

**Methods:** none.


&nbsp;
## AuthenticationButton.vue
_Last updated: 10/1/2022_

Handles whether a user will see a log in or log out button in Step 1 of the Amplify letter generation process.

![Authentication Button](https://imgur.com/7pIpQyD.png)

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:** none.


&nbsp;
## AuthNav.vue
_Last updated: 10/1/2022_

This component wraps the [AuthenticationButton](https://github.com/ProgramEquity/amplify/wiki/Components/#authenticationbuttonvue) component.

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:** none.

&nbsp;
## CampaignCard.vue
_Last updated: 10/29/22_

A single card for rendering campaign information

**Props:**
  * campaign _Campaign_

**Data:**
  * defaultCampaignLogoUrl _string_: * defaultCampaignLogoUrl _string_: a path for a default campaign image if none is sent with Campaign.

**Methods:**
  * getCampaignLogo(campaign: Campaign): string
    * returns a Campaign's image or the default campaign image.


&nbsp;
## CampaignCards.vue
_Last updated: 10/29/22_

A container to render CampaignCards.

**Props:** none.

**Data:**
 * campaigns _Campaign[ ]_: an array of Campaigns returned from the campaign API.
 * publicPath _string_: an environment variable exposing the public assets folder.
 * defaultCampaignLogoUrl _string_: a path for a default campaign image if none is returned.

**Computed Properties:** none.

**Methods:**
  * getCampaignLogo(campaign: Campaign): string
    * returns a Campaign's image or the default campaign image.

&nbsp;
## CauseCarousel.vue
_Last Updated: 10/30/22_

Holds one or more CampaignCards in a carousel element. Similar to CampaignCards.vue, but with more Vuetify. May be a good candidate to consolidate into one component.

**Props:** none.

**Data:**
  * slides _number_: Indexes the v-slide-group that powers the carousel. See Veutify's [side group docs](https://vuetifyjs.com/en/api/v-slide-group/) for more info.
  * defaultCampaignLogoUrl _string_: Path for a default campaign image if none is returned with the Campaign.
  * campaings _Campaign[ ]_: An array of Campaigns returned from the Campaign API.

**Computed Properties:** none.

**Methods:**
  * getCampaignLogo(campaign: Campaign): string
    *returns a Campaign's image or the default campaign image.


&nbsp;
## DonateMoney.vue
_Last Updated: 10/30/22_

Interface for the Amplify user to pick a donation amount and open a payment session.

**Props:** none.

**Data:**
  * Donation _number_: the donation amount selected by the user in dollars.

**Computed Properties:** none.

**Methods:**
  * submit(): void
    * Creates a checkout session with the checkout API, dumps user's state into the browser's Local Storage, and redirects the user to Stripe.


&nbsp;
## HeroHome.vue
_Last Updated: 10/30/22_

The Hero element for the Amplify home page.

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:** none.


&nbsp;
## LetterLoad.vue
_Last Updated: 10/30/22_

Renders a campaign letter for the user, filling in representative details.

**Props:**
  * repName _string_: Representative's name
  * letterBody _string_: HTML string containing a letter from the Lob API.
  * selectedRep _object<string, any>_: Information about the selected representative.

**Data:** none.
  * Date _Date_: User's current date.
  * isSubmitted: Controls if the letter content renders. Currently is always true.

**Computed Properties:** none.

**Methods:**
  * currentDate(): Date
    * Returns a formatted date. Is not currently used. As a side note, this type of formatting could be more easily done using the Intl module.

&nbsp;
## LoginButton.vue
_Last Updated: 11/31/22_

Appears if user is not logged in.

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:**
  * login (): void
    * Redirects an unauthenticated user to the 0Auth login.

&nbsp;
## LoginoutButton.vue
_Last Updated: 11/31/22_

Logs a user out and redirects to home page.

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:**
  * login (): void
    * Redirects an user to home back after logging them out.