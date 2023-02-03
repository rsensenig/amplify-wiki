
A description of the constituent user journey. For types of users, and the user story, click the `User Story` link in the sidebar.

### Browse Causes

![2](https://user-images.githubusercontent.com/9143339/174918508-6fc222ac-2037-44b8-be3b-790d214cf4bb.png)


This layout assumes that we are a landing point from a call to action that an advocacy group puts out on social media, email blasts, and other comms - but not the first time the constituent is hearing about the cause.

That's why we are letting the campaigns be a simple gallery while the landing page is where there is more context per the campaign requests.


<img width="469" alt="Screen Shot 2022-02-07 at 12 35 43 PM" src="https://user-images.githubusercontent.com/9143339/152867622-df435a4d-8779-4225-8573-1e09edc35929.png">

<img width="603" alt="Screen Shot 2022-02-07 at 12 36 51 PM" src="https://user-images.githubusercontent.com/9143339/152867838-3a186952-f86c-4fe3-b240-3e079ff6f336.png">

### Browse Representatives

![3](https://user-images.githubusercontent.com/9143339/174918609-e2a6ee15-9362-43bd-9327-7c55575d7215.png)

This feature has the user enter their zipcode and select the government scale they wish to work within, and returns a list of representatives for their causes, as well as (in the future) showing other reps running for the same cause. 

The decision to input only zipcode is partially due to how the Google Civic API is set up. The scope will be constricted based on the jurisdiction the campaign letters apply to.

<img width="422" alt="Screen Shot 2022-02-07 at 12 51 50 PM" src="https://user-images.githubusercontent.com/9143339/152869987-ed88e70a-5e25-47e7-8b3e-e20905bdf0cf.png">

### Choose Representative 

![3](https://user-images.githubusercontent.com/9143339/174919318-258ffc8f-3062-4d83-82c3-44393df7342b.png)


- User input displays local, state and federal representatives
- Clicking on a representative will give you a preview of the letter

<img width="464" alt="Screen Shot 2022-02-07 at 12 52 08 PM" src="https://user-images.githubusercontent.com/9143339/152870062-632648a6-e0a1-47fa-8fa9-11a0c49b2d07.png">
<img width="594" alt="Screen Shot 2022-02-07 at 12 52 41 PM" src="https://user-images.githubusercontent.com/9143339/152870094-98576f25-062d-48ff-87bb-ad3e62ed8bb5.png">

### Review Letter

![4](https://user-images.githubusercontent.com/9143339/175099798-410eb542-5a93-4fb3-ad0b-283048916348.png)

Allows user to review information and add their own experiences as it relates to topics being discussed 

<img width="557" alt="Screen Shot 2022-02-09 at 7 07 41 PM" src="https://user-images.githubusercontent.com/9143339/153334061-492411e7-8885-44b4-91ee-6781e7be7368.png">

### Validate Address 

![8](https://user-images.githubusercontent.com/9143339/175100577-e95720ba-553e-42da-a8fa-9d6ca8916ee1.png)

- User enters address, which is then validated, so that their advocacy holds weight
- User can sign up to hear updates about this cause further via text 

<img width="531" alt="Screen Shot 2022-02-09 at 7 07 49 PM" src="https://user-images.githubusercontent.com/9143339/153334233-6dcce94c-3e22-4cac-9b82-a3382edbaf70.png">

###  Select Donation

![8](https://user-images.githubusercontent.com/9143339/175102360-c5131527-743b-4630-947f-8088bd8b6a6c.png)

- User pays a default of 1.00 (close to a forever stamp) which offsets the use of APIs like Lob, Stripe, and Cicero to mail the letter
- User can select a donation amount to support their cause further
- A progress bar creates a visual incentive of the goal to support
- User clicks "Donate and Send Letter" button to approve sending the letter and making a donation

<img width="514" alt="Screen Shot 2022-02-09 at 7 56 26 PM" src="https://user-images.githubusercontent.com/9143339/153334319-3f9ca4b8-cc65-439c-971e-74298a699dd5.png">

### Finalize Checkout & Send Letter

![10](https://user-images.githubusercontent.com/9143339/175102530-6c702e70-859f-421c-8ac6-4a38bac0c42c.png)

- User enters payment information to complete donation
- Once user clicks "Pay" button, payment is made and letter is sent

<img width="463" alt="Screen Shot 2022-02-09 at 7 56 32 PM" src="https://user-images.githubusercontent.com/9143339/153334359-281ddf87-5962-49a0-a41b-cbe6ba56618d.png">

### Action Complete

![9](https://user-images.githubusercontent.com/9143339/175101430-bdfeb630-6f39-4bf1-a510-042552b41dad.png)

- User arrives at to action complete page
- User is given "Congratulations!" message that confirms their letter is being delivered
- A progress bar shows the user how much money has been raised in the campaign
- User is reminded of options to repeat actions for other causes or invite a friend

<img width="417" alt="Screen Shot 2022-02-09 at 8 00 21 PM" src="https://user-images.githubusercontent.com/9143339/153334630-a994d877-cf9a-46a8-ac72-4ab609b77556.png">
<img width="739" alt="Screen Shot 2022-02-10 at 5 13 03 AM" src="https://user-images.githubusercontent.com/9143339/153415374-43af781f-e61c-4bda-9c9e-352328ed6274.png">