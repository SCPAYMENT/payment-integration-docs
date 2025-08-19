/*
Title: Overview
Sort: 1
*/


Nowadays, payment gateway online transaction is the fast and convenient way for merchants, to provide different Payment Options for different customer needs. The term includes not only provide different Payment Options to customers, it's also help those found in brick-and-mortal retail stores, able transform as e-businesses by expands business further.


<br />
<br />

# How Payment Gateways Work

<br />

The payment gateway is a key component of the electronic payment processing system, as it is the front-end technology responsible for sending customer information to the merchant acquiring bank, where the transaction is then processed.

From here, SC Payments Payment Gateaway help developer and/or merchant to integrate easily with us once, then merchant is able to provide different Payment Options based on different customer needs.

<br />
<br />

## Payment Gateway key stakeholders

<br />

- **Merchant**: The business or any person making the sale.
- **Cardholder** : Your customer making the purchase.
- **Issuing Bank** : The financial institution that holds the customer’s account, either a credit card account or a checking account connected to a debit card.
- **Card Schemes** : The credit card companies that manage the card, like Visa, Mastercard or American Express.
- **Acquiring Bank** : The financial institution that holds the merchant’s account.


<br />
<br />

## Process Flow

Below diagram showing how's SC Payments Payment Gateway process the transaction between each parties.

<br />
<br />

<img src="https://devdocs.scpayments.com.my/images/figure1.png" alt="Payment Process Flow"/>
<br />
<br />
<br />
<br />


1.	Customer place order over Merchant e-commerce website.
2.	Merchant redirect customer payment transaction to SC Payments Payment Gateway.
3.	SC Payments validate merchant's credential to ensure every transaction security is from trusted party.
4.	SC Payments display different Payment Options for customers selection.
5.	Customer select a payment option
6.	SC Payments will based on customer payment option selection, and redirect to the corresponding acquirer bank page.
7.	Payment gateway validates the payment details and signature received
8.	Display the security page to customer, such as OTP enter, or QR scanning and so on.
9.	Customer chooses the option display, either to login on web or scan the QR Code
10.	Customer proceeds the payment for their order
11.	Processes the payment with the respective financial institution
12.	Financial institution returns the payment response
13.	SC Payments validates the payment response and signature sent by payment gateway
14.	SC Payments return to merchant’s complete URL or cancel URL if customer exit the payment flow during payment processing.
15.	SC Payments POST a callback to merchant’s callback URL with parameters. This ensures that orders can be completed even in cases where the customer's connection is terminated prematurely. Callback will be in HTTP POST method.
16.	Redirect to merchant acknowledgement page based on redirect url passing in.
