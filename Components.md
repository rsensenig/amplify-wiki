# Amplify Components
The Amplify app has a number of Vue components, which are documented here. Check back frequently for the most recent information. To report errata or suggest changes, email glenn@piludu.io or message Glenn on Slack.

## ActionComplete.vue
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

**Parent Components:**
* CompletePage.vue

**Child Components:** none.

&nbsp;
## AppFooter.vue
This component defines the footer of Amplify. It should hold important legalese, as well as site navigation and social media links.

**Props:** none.

**Data:**
  * icons _string[ ]_: A list of icon identifiers for social media buttons.

**Computed Properties:** none.

**Methods:** none.

**Parent Components:**
  * App.vue

**Child Components:** none.

&nbsp;
## AppHeader.vue
This component controls the navigation bar for the app.

**Props:** none.

**Data:**
  * dialog _boolean_: Present, but unused.
  * menuItems _Array<string, string>_: List of navigation links and their paths.

**Computed Properties:** none.

**Methods:** none.

**Parent Components:**
  * App.vue

**Child Components:** none.

&nbsp;
## AuthenticationButton.vue
Handles whether a user will see a log in or log out button in Step 1 of the Amplify letter generation process.

![Authentication Button](https://imgur.com/7pIpQyD.png)

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:** none.

**Parent Components:**
  * [AuthNav.vue](https://github.com/ProgramEquity/amplify/wiki/Components/#authnavvue)

**Child Components:**
  * LogoutButton.vue
  * LoginButton.vue

&nbsp;
## AuthNav.vue
This component wraps the [AuthenticationButton](https://github.com/ProgramEquity/amplify/wiki/Components/#authenticationbuttonvue) component.

**Props:** none.

**Data:** none.

**Computed Properties:** none.

**Methods:** none.

**Parent Components:**
 * LetterLoad.vue

**Child Components:**
  * [AuthenticationButton.vue](https://github.com/ProgramEquity/amplify/wiki/Components/#authenticationbuttonvue)