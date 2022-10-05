# State Management
Amplify uses Vuex 3 for state management. If you're coming from Vue 3, you might have used Vuex 4, which works similarly, or Pinia -- which is similar but simplifies some of the most annoying parts of Vuex. The [Vuex docs](https://v3.vuex.vuejs.org/) have some great information for Vuex newcomers; alternatively, there are tons of great resources on YouTube.

* Note: The _store_ parameter is an object that will expose state, actions, mutations, and any defined getters or setters. The _payload_ parameter holds whatever was passed in by a component.

## State
* **zipcode** _(string)_: The current zip code, as input by the user.
* **letterId** _(string)_: A LOB template id, generated during the letter creation workflow.
* **lobReturnAddressId** _(string)_: The user's return address id, generated after address validation.
* **selectedRep** _(object)_: Address information for the user's selected representative.
* **userData** _(object)_: Other user data collected during letter creation.

## Mutations
* **setGenericValue**(state, { key: string, value: any }): void
  * Sets the state attribute given by _key_ parameter to _value_.

## Actions
* **setLetterAttrs**(store, payload: object<string, any>): void
  * Updates state when the payload and state have a matching attribute.

* **dumpStateToLocalStorange**({ state }, sessionId: string): void
  * Before a Stripe checkout redirect, this method will capture the user's current state and store in their browser's Local Storage.

* **retrieveStatefromLocalStorage**(store, sessionId: string): void
  * Reconstitutes the user's state after a successful Stripe checkout redirects the user back to Amplify. Once the state has been retrieved, it is deleted from Local Storage.