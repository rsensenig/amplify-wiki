This procedure creates the UI and integration for Stripe's Apple Pay, Google Pay, and Pay Now buttons.

<img src="https://user-images.githubusercontent.com/8395862/153504423-800f4253-3d05-4ece-81ed-5f61db829271.png" width="50%">

1. Follow all the steps in the [Stripe documentation](https://stripe.com/docs/stripe-js/elements/payment-request-button?html-or-react=react) for React. This will add the Stripe package to the UI, check if the user has a payment method on the device, and render the appropriate button.
2. When you get to [Step 4](https://stripe.com/docs/stripe-js/elements/payment-request-button?html-or-react=react#react-create-payment), call the `/create-payment-intent` API endpoint with the user's `donationAmount` to get the `clientSecret` back. The `clientSecret` is sent back to the client to securely complete the payment process instead of the entire `PaymentIntent` object.
3. In [Step 5](https://stripe.com/docs/stripe-js/elements/payment-request-button?html-or-react=react#react-complete-payment), use the `clientSecret` received in Step 4 to complete the payment.
4. Follow the [remaining steps](https://stripe.com/docs/stripe-js/elements/payment-request-button?html-or-react=react#react-testing) in the Stripe documentation.