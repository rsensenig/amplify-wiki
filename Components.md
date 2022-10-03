# Amplify Components
The Amplify app has a number of Vue components, which are documented here. Check back frequently for the most recent information. To report errata or suggest changes, email glenn@piludu.io or message Glenn on Slack.

## ActionComplete.vue
This component renders when a user completes the check-out process after generating a campaign letter. It will show the letter delivery date, the donation amount, and other campaign-related sub-components. Because Stripe payments require a redirect away from Amplify, this component will use the _sessionId_ query parameter from Stripe to restore local state, which is stored in a user's Local Storage.

Importantly, this component is also responsible for creating a transaction record for the previously complete check-out.

**Props:** none.

**Data:**
  * loading _(boolean)_: If true, a loading animation will render while the transaction is recorded and campaign letter are generated.
  * email _(string)_: User's email address. Returned by the back-end when a transaction is recorded but currently has no use.
  * amount _(number)_: The amount of a user's campaign donation, in cents. Returned from createTransactionRecord (which it gets from the Stripe API). Shown in success message.
  * expectedDeliveryDate _(string)_: The expected campaign letter delivery date returned from LOB API.
  * congressMembers _(array of objects)_: List of congress people to display in subcomponent. Currently not implemented.

**Computed Properties:**
  * donationAmount _(number)_: amount converted from cents to dollars.
  * selectedRep _(string)_: Returns from local state the Representative that was selected during the campaign letter generation process.
  * userData _(object)_: Returns from local state user data to send to LOB API.
  * letterId _(string)_: Returns from local state the campaign letter template id for LOB.
  * lobReturnAddressId _(string)_: Returns from local state the return address id generated during the letter creation process.

**Methods:**
  * createTransactionRecord(sessionId: string): void
    * Verifies Stripe payment on the Amplify back-end and records the transaction into Amplify's database. Returns nothing, but modifies _amount_ and _email_ data attributes.
  * createCampaignLetter(sessionId: string): void
    * Creates a campaign letter with LOB. Returns nothing, but modifies _expectedDelieryDate_ and _loading_ data attributes.


**Views:**
* CompletePage.vue