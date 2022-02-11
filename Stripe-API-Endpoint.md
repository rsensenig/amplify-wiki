This procedure tests that the Payment Request button is properly hooked into the Stripe backend after you complete the [initial integration](Setting-up-Apple-Pay).

1. Create a Payment Intent Request. Call the `/create-payment-intent` endpoint in POST and send a `donationAmount` variable in the body. 
2. The Stripe API returns a `clientSecret`. Use this client secret in the Stripe UI package to create the transaction.
3. The Stripe UI package returns a response with the created transaction. Pass the transaction response to the `/create-transaction` endpoint via POST so that Amplify records the transaction in our database.
4. Show the user the corresponding success message on the UI.

## Test environment variables

### Backend

`STRIPE_SECRET_KEY`: `sk_test_51IravfFqipIA40A3FOW6EzlXlJiXjL9V0FXKfb9n7cxh25Ww9QMA9aWwCzTSQscBOQFcB7s1TI6UCtW1JG83Hz1z000Sg2vSIr`

### Frontend

Use this publishable key: `pk_test_51IravfFqipIA40A3SI50i113zqo0M0Smy1hNa59eEYl15AbdCBhHQC4qd1lhxkgAYXyoFGkeZGDg4vYB8P76N7GW00bI6nvygJ`