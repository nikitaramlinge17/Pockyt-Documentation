# Documentation

## Introduction

Pockyt is a payment gateway utilized by various companies in retail and online to process payments, offering a digital wallet for seamless transfers and processing payments through point-of-sale systems, In-store payment, and Pay-out services.

## Overview

Pockyt API provides a powerful solution for integrating custom payment forms seamlessly into your website or application. By utilizing both client and server-side code the API enables the creation of a user friendly checkout form with all necessary payment elements included for the chosen payment method. This allows for a streamlined payment process making it easier for customers to complete transactions and for businesses to manage their payment processing.

## Quickstart Tutorial

 Pockyt offers a secure and user-friendly payment experience for customers, supporting a variety of payment methods such as digital wallets and card payments. Pockyt partners with multiple digital wallet providers, enabling businesses to attract and retain digital-native customers from all over the world. n endpoint. We recommend completing our quickstart tutorial on Pockyt products to learn key concepts.
      1 - Hosted Pages
      2 - Digital Wallets
      3 - Credit Card

    The same Please note that all the tutorials and explanations in this document will reference the Pockyt's base Sandbox URLs

* A Sandbox API's Base URL  "https://mapi.yuansfer.yunkeguan.com"
* Production API's Base URL's "https://mapi.yuansfer.com/"

## Payment Methods

    Below are our payment integration methods, so you can choose what works best for you

* Asia Pacific Based Digital Wallets Alipay, WeChatPay, UnionPay, TrueMoney, AliPay HK, TNG, GCash, Dana, KakaoPay, BKash, EasyPasia
* US Based Payment Methods Major Credit Cards Visa, MasterCard, Discover, Amex, Union Pay, Digital Wallets Paypal, Venmo, CashApp

## Payment Integration Types

* **Online**: Online Payments enable e-wallet and payment acceptance, seamlessly integrated into your e-commerce and point-of-sale (POS) platforms. Refer the Documentation.
* **In-store**: In-store payments enable clients to make hassle-free payments through their mobile wallets while maintaining operational efficiency in your stores. Refer the Documentation.
* **Pay-out**: Effortlessly make payments to influencers, sellers, and contractors worldwide through their preferred payment methods, including digital wallets (such as PayPal and Alipay) and traditional bank accounts. Refer the Documentation

Prerequisites  Please ensure you have the following accounts and test devices available to complete your implementation project.

* Account ID's in the Apple iOS store, and Google Play store, with the iOS TestFlight application installed on your phone.
* An iOS device and an Android device on which you will download and install the test digital wallet applications from PayPal, AliPay and CashApp to generate payment barcode strings

# Guides

 In the Guides section, developers can find comprehensive documentation and detailed explanations of the API's functionality.

## Online Payment APIs

The Online Payment Implementation Guide is designed to help developers seamlessly integrate Pockyt's APIs into their host systems, facilitating a streamlined payment process.

The guide will walk developers through the steps of setting up an account with Pockyt, creating a sandbox test environment, incorporating Pockyt's APIs into their custom applications, and understanding how
these APIs can advance various online payment workflows, both custom and Pockyt-hosted.

### Pockyt Developement Sandbox

 High level steps

* STEP 1 - Setting up a development account with Pockyt.
* STEP 2 - Obtaining  API credentials.

For Obtaining API credentails, you need two sets of credentials from Pockyt to complete your implementation project.

### Step 1 - Sandbox API Credentials and Account Information

Enables you to test the entire transaction network relevant to your use cases.

    Perform the following steps to obtain your Sandbox API credentials:

    1 - Visit the Pockyt developer's website and go to the Support tab.

    2 - Click "Developer Tools" and go to the Sandbox Environment tab.

    3 - Click the "Apply Sandbox Credentials" link to start the application process.

    4 - Wait for the Pockyt team to review and approve your application (usually takes 2 days).

    5 - Once approved, Pockyt will provide you with a dedicated secret token for the Sandbox environment.

    6 - The base URL for the Sandbox environment API is "https://mapi.Pockyt.yunkeguan.com"

    7 - Use the RESTful endpoints relevant to your use case with the initial calls made in test mode credentials to avoid incurring any costs.

    8 - To ensure optimal integrations and testing, your Sandbox environment should feature the front-end user interface for online payment workflows.

    9 - By following these steps, you can easily set up a Pockyt Sandbox account to test and refine your integration with Pockyt's API, providing a secure and user-friendly payment experience to your customers.

### Step 2 - Production API Credentials and Account Information

    Enables you to begin processing live transactions from digital wallets and other payment methods.

    Perform the following steps to obtain your Production API credentials:

    1 - Click Login and select Create Account to access the 10-step merchant application form.

    2 - Enter your credentials and submit the required documents business license or registration voided check or bank letter with company name, and government-issued photo identification.

    3 - Pockyt's team reviews your application and submits it to each digital wallet service they work.

    4 - Once approved, Pockyt automatically activates your live accounts, which takes around 1-2 business days for processing and approval.

    5 -  Pockyt notifies you of your approval status and provides your Merchant No. and Store No. via email.

    6 - Log in to your account to collect your API token, which is required to build API parameters.

    7 - Each API request includes a verifySign parameter, which is the calculated MD5 hash value of your API token, allowing Pockyt to authenticate and authorize your API calls. For more information, visit "Signing API Parameters".

### Payment Scenarios and API Endpoints

This section provides a step-by-step summary of the primary payment scenarios and explanations of the API endpoints relevant to each use case.

The following are two use cases and implementation paths

* Pockyt Checkout method** (referred to as the "SecurePay API") allows you to redirect customers to a Pockyt-hosted page for checkout. This is a favorable alternative payment solution if a business cannot host its payment forms for some reason.
* Pockyt Integrated Option** (referred to as the "PrePay API")  is a more suitable option for businesses looking to customize their payment form and retain complete control over the latter. This method allows businesses/merchants to build their UI for all the payment methods preferred by their customers.

### Implementation Option 1 - Checkout API

 Using the SecurePay API, merchant websites can send customers to receive payments from Pockyt.

Perform the following steps to use Pockyt Checkout for online payment checkout.

    1 - The merchant system calls the create API to register a customer.

    2 - The merchant system generates a customer ID for future transactions and stores it in its database.

    3 - The merchant system then calls the secure-pay API to retrieve a cashierURL from Pockyt.

    4 - Using the cashierURL, the customer is redirected to Pockyt's hosted payment form.

    5 - After the payment is completed, Pockyt redirects the customer back to the merchant's payment result page using the provided callback URL in the request body of the secure-pay API.

    6 - Pockyt relays the transaction results to the merchant's website using the IPN callback function.

    7 - To receive the payment results, the merchant website creates an IPN listener page and uses its URL in the request body of the secure-pay API.

    8 - The merchant's website displays the payment confirmation message to the customer.

    Pockyt Checkout: API Workflow Diagram![Pockyt Checkout](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image1.png)

### Implementation Option 2 - Integrated Payments

    Pockyt Integrated Payments offers a highly customizable payment form for businesses that want to retain complete control over the payment process.

    This method enables businesses to build their user interface for all preferred payment methods, providing a seamless payment experience for their customers.

    Merchants have the option to integrate Pockyt's APIs directly into their system for self-hosted mobile payments, or they can accept customer payments by integrating their system with Braintree, using both the /secure-pay API and the /process API.

    Pockyt Integrated Payments Workflow (Braintree)
    Integrating the merchant system with Braintree will allow your customers to utilize digital wallets such as Google Pay, Apple Pay, Paypal, and Venmo to make payments for purchases secured on your website.
    You can use Pockyt`s process API (discussed below) and/or secure-pay API (discussed earlier) to integrate with Braintree.

    The first step is to create a Braintree account and then add the Braintree JavaScript SDK to the web page to accept payments and remain PCI-compliant.
      Soon after creating an account, the merchant system will receive a payment_method_nonce, which is a one-time-use reference ID for the payment method.

  **API Workflow for Merchants**:

* The merchant system registers first-time customers by calling the create API, generating a customer number stored in the merchant's database for future reference.
* When the customer is ready to make a payment, the merchant website displays its payment page and calls the secure-pay API with YIP as the terminal value.
* The merchant system receives an authorization token and transaction ID instead of a cashier URL, which is required to accept payments with Braintree.
* Upon customer confirmation, the merchant system calls the process API to initiate the transaction.
* Pockyt uses the payment_method_nonce and transaction ID to request that Braintree process the payment.
* Braintree complies with the request and passes the transaction results to Pockyt, who relays them back to the merchant website.

  Pockyt Integrated Payments: Process + SecurePay API Workflow Diagram
  ![Process + Securepay API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image2.png)

### PrePay for In-App and Wechat Mini Solutions

    Pockyt Prepare API enables merchants systems to accept mobile via- In App and Wechat Mini Programs solutions. It is important to note that this API does not support credit card payments.
      Our suite of software developement tools provides easy prepay API intrgrations for iOs and Andriod, supporting several programming langauges, including but not limited to Java, JavaScript, and C.

  **Use Case Flow**:

* The merchant's system must begin by calling the create API to register first-time customers.
* This will generate a customer id. that the merchant can store for future transactions.
* When the customer is ready to make the payment, the merchant website will display its own payment page where the customer can indicate their preferred payment method.
* Once the customer confirms the payment method, the merchant`s website passes the payment request to Pockyt for processing using the prepay API.
* The payment request should include the necessary parameters listed below.
* Pockyt will advance the request to the digital wallet server that will process the payment and notify Pockyt about the transaction details.
* Pockyt will then relay the results to the merchant`s system.

  Pockyt Integrated Payments: Prepay API Workflow Diagram
  ![Prepay API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image3.png)

### Customer Refunds

    In the instance where a customer requests a refund, the following request and response objects are initiated to complete the refund workflow.

### Refund API Workflow

    The following steps depicts Refund API workflow:

    1 - The customer will apply for a refund on the merchant`s website using the transaction number.

    2 - The merchant`s system will use the transaction number to identify the exact details of the original purchase and call refund API which will request the digital wallet server to refund the payment originally made by the customer.

    3 - The wallet server will reimburse the transaction amount to the customer as well as alert the latter about the refund via a notification.

    ![Refund API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image4.png)

    # Cancel the transaction / void
      In the event of a customer canceling the purchase the following request and response objects are created to complete the cancellation process successfully.

### Cancel API Workflow

    The following steps depicts Cancel API workflow:

    1 - The customer applies for payment on the merchant's website after shopping.

    2 - If the customer is unable to confirm payment due to connectivity issues, they can select the cancel option in the payment UI.

    3 - The merchant's system calls Pockyt's /cancel API to cancel the payment transaction.

    4 - Pockyt notifies the digital wallet server to abandon the transaction.

    5 - The digital wallet server cancels the transaction and notifies Pockyt of the cancellation status.

    6 - Pockyt relays the information to the merchant's system.

    ![Cancel API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image5.png)

### Recurring Payments (Auto Debit)

    Recurring Payments is known as auto-debit, it is a payment solution recommended by Pockyt that facilitates users with automated payments in the future.

    Auto Debit prevents the merchant from having to repeat the entire payment protocol every time a customer makes a purchase. Instead, the merchant can directly deduct money from the customer`s account using an authorization token.

    For the merchant to avail Auto Debit Payment feature, the user will have to sign an agreement, like a three-party withholding agreement, with the merchant in advance. This will authorize the merchant to obtain a token (known as an authorization token) that they can use to initiate any auto payment request made by the customer.

    API Endpoints in Recurring Payments (Auto Debit)
    * Consult
    * Apply token
    * Pay
    * Revovke

    ## Recurring Payments API Workflow
    The following steps depicts Recurring Payments API workflow:

    1 - Create a vendor list page that includes vendors supported by Pockyt.

    2 - Call the consult API to retrieve an authorization URL that redirects the customer to a vendor`s interface to authorize the merchant for future payments.

    3 - Based on the terminal value, Pockyt will provide either a normalURL or applinkURL and generate an autoDebitNo. unique to the Pockyt system.

    4 - The customer will authorize the merchant to deduct payments from their wallet via the vendor's interface.

    5 - The vendor will redirect the customer back to a redirection URL (autoRedirectURL) provided by the merchant in the request body of the consult API along with passing the authorization result to it.

    6 - Call the apply-token API using the autoDebitNo. in the request parameter to get the token from the vendor.

    7 - Use the pay API, following a fixed schedule, to initiate an auto-debit payment for any purchase made and process the payment results based on the transaction status returned by Pockyt.

    8 - Use the revoke API to cancel the authorization agreement if the customer requests it.

    9 - Once Pockyt receives the revoke request, the access token will become invalid, and the merchant system will be unable to access the user resource scope.

### Apendix B: Tutorial: Calculate VeriSign Value

    ## Secure API Calls with VeriSign Signature
    Transactions made via Pockyt do not involve any secret tokens or user passwords eliminating the chances of hacking or fraud incidents. Instead, we use the verifySign parameter to authenticate and authorize the API requests at every step of the transaction process.
    The verifySign parameter serves as your API parameter signature. You can build this parameter by retrieving the API token from Pockyt`s dashboard and using the latter along with MD5 encryption to calculate the MD5 authentication hash value.

    Follow these best practices to make sure your API token is safe.

    * Store your API token in a secure location, such as a database or configuration file on the backend of the application, and restrict access to only those who need them. Do not har-code the token into your code or include it in version control.
    * Use secure encryption algorithms: Use encryption algorithms like AES or RSA to encrypt your API token before storing it. This helps protect against unauthorized access to the token.
    * Implement rate limiting: Implement rate limiting to prevent attackers from launching brute force attacks against your API. This helps protect against attempts to guess valid tokens.
    * Monitor logs: Regularly monitor logs for any suspicious activity, such as multiple failed API access attempts or requests with invalid tokens, and take action if necessary.
    *
    These best practices will help you secure your API token and ensure the security of your system.

**Follow the steps below to implement the VeriSign feature**

    1 Sort the parameters alphabetically according to the parameter name.

    2 Concatenate the parameter names and values using '=' and '&' characters.

    3 Append the MD5 hash value of your API token to the end of your parameters with the '&'prefix.

    4 Calculate the MD5 hash value of the Step 3 result.

    # Calculating the VeriSign Parameter ValueCalculating the VeriSign Parameter Value

    Consider the following

    # Appendix C:Tutorial: Instant Payment Notifications

    The Instant Payment Notification (IPNurl) is a callback function that helps Pockyt notify the merchant about any new transaction-related event. Pockyt waits for the merchant`s website to acknowledge the IPN messages before it can take action for further processing.

    Here is how to access Pockyt`s IPN service.

Create an IPN listener page on your website. This listener page will contain a custom script or a program to receive back-end messages.

* Include the URL of this listener page in the request body. This will allow you to receive all of the transaction-related event notifications sent by Pockyt to your website.
* Every time a transaction occurs, Pockyt sends an instant payment notification (IPN) to the merchant `s listener page URL using the secure POST method.       `

`The IPN listener page parses the transaction information and processes them to the custom script for verification.      `

`After verifying the success status of these messages, the custom script or program will forward them to the back-end applications for processing.      `

`* At this point, the listener page must acknowledge Pockyt`s IPN messages with a “success” string.

Keep in mind that the IPN messages are not synchronous with the merchant`s website and there is always a chance for these notifications to get lost or delayed due to poor internet connectivity.

    Pockyt`s IPN service continues to resend the IPN messages until the listener page acknowledges. If the listener page fails to acknowledge the messages, it will continue to receive them up to eight times in two hours.

**Callback parameters**

    It is recommended for the merchant system to validate the parameters in the callback information using verifySign. This is to eliminate the possibility of processing tampered information. Pockyt`s callback function will contain the following parameters along with the IPN.

# B2C Payouts Service

The B2C payouts Service Guide is designed to help developers to implement the Pockyt's Payout Service APIs.

## About this document

In this section, you will learn how to:

1. Implement payment scenarios in which businesses make payments to consumer digital wallets or bank accounts.
2. Implement Payouts Transactions to the following payment methods:

* PayPal / Venmo Digital Wallets
* Consumer Bank Accounts in USD
* AliPay+ Network - Coming Soon, will be included in future versions of this guide

3. Make secure API Calls with VeriSign: Use encryption tools to secure API interactions.

* Sandbox URL:  "https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/cancel"
* Production URL: "https://mapi.yuansfer.com/app-data-search/v3/cancel"

## Getting started with Pockyt Developement Sandbox

This section provides instructions for setting up a development account with Pockyt, obtaining
sandbox credentials, and installing the test digital wallet applications.

High level steps

* STEP 1 - Setting up a development account with Pockyt.
* STEP 2 - Using your Merchant ID, Store ID, and API Token Values

For Obtaining API credentails, you need two sets of credentials from Pockyt to complete your implementation project.

## Step 1 - Setting up a development account with Pockyt

Enables you to test the entire transaction network relevant to your use cases.

1. Send a request for a sandbox account to devsupport@pockyt.io.
2. Upon receiving payment information, Pockyt's developer support team will contact you. We can assist you with enabling methods and developing payment use cases.

## STEP 2 - Using your Merchant ID, Store ID, and API Token Values

Upon registering for a Sandbox account, you will receive each of these values.

In order to use our APIs, you will need these authentication credentials, which are only available to you in your sandbox account.

Once your testing in the sandbox is complete, you will receive production credentials. You should update these credentials when interacting with Pockyt's production APIs.

{
"merchantNo": "200043",
"storeNo": "300014",
"verifySign": "f38965887c5676e2fb19d951251eb613", //Calculated with Token Value
}

## Terminology and Basic Payout User Work Flow

The basic payment scenario for Pockyt’s Payouts Payment API’s.

* The **Merchant (Payor)** uses Payout's service to transfer funds from their business bank account to an individual's (payee's) consumer digital wallet, bank account, or other consumer account payment methods.
* An **Individual Payee** has an Affiliate Marketing relationship with a merchant store. The Merchant Store pays a Commission to the Individual Payee when their traffic leads to a purchase at the store.
* When the Individual Payee directs traffic to the store, leading to a purchase, the Merchant Store pays a commission via their Pocky Payor Account.
* To receive their Commission Payout, the Individual Payee must create a **Pockyt Payee Account**, where they can configure their payout preferences, such as how they would like to receive their funds (bank account, PayPal, Venmo, etc).

  ![1683734210916](image/In-StoreDigitalWalletPaymentProcessingSandboxAPI’s/1683734210916.png)

## Payment Scenarios and API Endpoints

A merchant (Payor) transfers funds from their business bank account to an individual's digital wallet, bank account, or other payment method through the Payout service

Below is a list of APIs designed to streamline customer-presented QR Code payments. All of these definitions use the Sandbox Base URL.

* **Register endpoint: v3/payee/register**

  You must first register an account with Pockyt to initiate payments to your payees. Send a POST request to the Register Customer endpoint, and you'll receive a customer number in response.
* **Retrieve endpoint: /v3/payee/retrieve**

  Send a POST request to Pockyt's Retrieve Payee Account API to obtain detailed account information about a payee. As a result, you can manage and verify payee accounts effectively, ensuring payments are processed properly.
* **Update endpoint: /v3/payee/update**

  To update payee details such as name, address, email, and bank information by providing customer
  No and new details. The API returns a confirmation message upon successful execution.
* **Add Payee Funding Source: /v3/payee/account/create/bank-account**

  Add a new payment method for the payee, such as a bank account. This endpoint requires the
  user to provide the Merhcnat ID and the payment details in the request payload
* **Retrieve Payee Funding Source: v3/payee/payout-accounts**

  * Sandbox URL:  https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/cancel
  * Production URL: https://mapi.yuansfer.com/app-data-search/v3/cancel
* **Transfer Endpoint: /v3/payouts/pay**

  To execute a payment, send a POST request to the payments endpoint. After successful validation, the specified amount will be transferred to the receiver.

## API made during Payee Registration and Payment

![1683735863150](image/In-StoreDigitalWalletPaymentProcessingSandboxAPI’s/1683735863150.png)

## Secure API Calls with VeriSign Signature

Pockyt transactions don't require secret tokens or passwords, so there's no risk of hacking or fraud. Instead, we use the verifySign parameter to authenticate and authorize API requests at every step of the transaction process.

The verifySign parameter serves as your API parameter signature. You can build this parameter by retrieving the API token from Pockyt’s dashboard. MD5 authentication hashes can then be calculated using the latter and MD5 encryption.

To ensure the security of your API token, follow these best practices.

1. Store your API token securely on the backend of your application, such as in a database or configuration file. Ensure that only those who need them have access to them. Version control or hardcoding of your token is not recommended.
2. Use secure encryption algorithms: Use encryption algorithms like AES or RSA to encrypt your API token before storing it. By doing so, the token is protected from unauthorized access.
3. Implement rate limiting to prevent attackers from launching brute-force attacks against your API. The purpose of this is to prevent attempts to guess valid tokens.
4. Monitor logs for suspicious activity, such as multiple failed API access attempts or requests with invalid tokens, and take the necessary action.

Follow the steps below to implement the VeriSign feature:

1. Sort the parameters alphabetically according to the parameter name.
2. Concatenate the parameter names and values using '=' and '&' characters.
3. Append the MD5 hash value of your API token to the end of your parameters with the '&'
   prefix.
4. Calculate the MD5 hash value of the Step 3 result.

## Calculating the VeriSign Parameter Value

Consider the following Parameters

amount = '1.00'
storeNo = '300014'
currency = 'USD'
merchantNo = '200043'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
terminal = 'ONLINE'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
reference = 'seq_1525922323'
vendor = 'alipay'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
timeout = '120'

First, sort the parameters alphabetically

amount = '1.00'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
currency = 'USD'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
merchantNo = '200043'
reference = 'seq_1525922323'
storeNo = '300014'
terminal = 'ONLINE'
timeout = '120'
vendor = 'alipay'

Next, concatenate the parameter names and values using '=' and '&' characters.

amount=1.00&callbackUrl=https://wx.yuansfer.yunkeguan.com/wx&
currency=USD&goodsInfo=
[{"goods_name":"Yuansfer","quantity":"1"}]&ipnUrl=https://wx.yuansfer.yunkeguan.com/wx&m
erchantNo=200043&reference=seq_1525922323&storeNo=300014&terminal=ONLINE&timeo
ut=120&vendor=alipay

## Calculating the VeriSign Parameter Value

Calculate the MD5 value of your API token and append to the string with the '&' character.
For example, if the API token is 5cbfb079f15b150122261c8537086d77a the MD5 hash
value is 186abea4b8610d7ff03768255588597a so the resulting string is:

amount=1.00&callbackUrl=https://wx.yuansfer.yunkeguan.com/wx&
currency=USD&goodsInfo=
[{"goods_name":"Yuansfer","quantity":"1"}]&ipnUrl=https://wx.yuansfer.yunkegu
an.com/wx&merchantNo=200043&reference=seq_1525922323&storeNo=3000
14&terminal=ONLINE&timeout=120&vendor=alipay&186abea4b8610d7ff03768
255588597a

Finally, you will calculate the MD5 hash value of the entire string in the block above.
The MD5 hash value is b6bfd66531ae7c9499115c7480a2c8aa and this is the value that
you will pass in the VeriSign parameter of your API request.

Next, concatenate the parameter names and values using '=' and '&' characters

url -XPOST -d '{
amount = '1.00'
storeNo = '300014'
currency = 'USD'
merchantNo = '200043'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
terminal = 'ONLINE'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
reference = 'seq_1525922323'
vendor = 'alipay'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
timeout = '120'
"verifySign": "b6bfd66531ae7c9499115c7480a2c8aa",
}' 'https://mapi.yuansfer.com/app-instore/v3/add'

## Appendix C: Tutorial: Instant Payment Notifications

The Instant Payment Notification (IPNurl) is a callback function that helps Pockyt notify the merchant about any new transaction-related event. Pockyt waits for the merchant’s website to Acknowledge the IPN messages before proceeding.

Here’s how to access Pockyt’s IPN service

* Create an IPN listener page on your website. This listener page will contain a custom script **or a program** to receive back-end messages.
* Include the URL of this listener page in the request body. This will allow you to receive all transaction-related event notifications sent by Pockyt.
* Every time a transaction occurs, Pockyt sends an instant payment notification (IPN) to the merchant’s listener page URL using the secure POST method.
* The IPN listener page parses the transaction information and processes them to the custom script for verification.
* After verifying the success status of these messages, the custom script or program will forward them to the back-end applications for processing.
* At this point, the listener page must acknowledge Pockyt’s IPN messages with a “success” string.
* IPN messages are not synchronized with the merchant's website and can get lost or delayed due to poor internet connectivity.

For this reason, Pockyt’s IPN service continues to resend IPN messages until the listener page acknowledges them. If the listener page does not acknowledge messages, eight messages will be sent in two hours.

#### Call Parameters

It is recommended for the merchant system to validate the parameters in the callback information using verifySign. This is to eliminate the possibility of tampering with the data. Pockyt’s callback function will contain the following parameters along with the IPN.

| Parameter      | Type   | Description                                                                                                           |
| -------------- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| transactionNo  | string | The Transaction ID in the Pockyt system.                                                                              |
| status         | string | The status of the transaction                                                                                         |
| amount         | string | The transaction amount.                                                                                               |
| currency       | string | The supported transaction currency are "USD", "CNY", "PHP",  "IDR", "KRW", "HKD", "THB", "MYR", "GBP", "BDT", "PKR". |
| settleCurrency | string | The supported settlement currency are "USD", "GBP"                                                                    |
| time           | string | The date and time when the authorization was createdFormat :"YYYYMMDDHHMMSS."                                         |
| Reference      | string | The transaction's invoice number in the merchant’s system.                                                           |
| vendorId       | string | Providers Transaction ID                                                                                              |
| note           | string | The payment note                                                                                                      |
| verifySign     | string | The parameter signature                                                                                               |

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// POCKYT TRANSACT QUERY AFTER AND ADD TO CHECK RESULTS API
sandbox example
// Import crypto for MD5 hash calculation
var crypto = require('crypto');
// Assign all Sanbox parameters
varURL="https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/tranquery" ;
var merchantNo = "200043" ;
var storeNo = "303660" ;
var MyToken = "359c05eb811c7c8576f4a8a277dc6f6b" ;
// construct POS fields and assign to object
var myPOSParamObject = {
merchantNo: merchantNo,
storeNo: storeNo,
transactionNo: "316129873376769782",
// reference: No reference in this case
}
// Calculate the VeriSign signature:
var MySignature = CalculateSignature(MyToken, myPOSParamObject)
// Add the signature to the POS parametes so we
// can use it in the body of the API call
var MyPocketParamObject = {
merchantNo: myPOSParamObject.merchantNo,
storeNo: myPOSParamObject.storeNo,
verifySign: MySignature,
// transactionNo: myPOSParamObject.transactionNo,
// reference: myPOSParamObject.reference
transactionNo: myPOSParamObject.transactionNo
}

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alfabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace : for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// alphabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// Prepare JASON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

# In-Store Digital Wallet Payment Processing Sandbox API’s

The B2C payouts Service Guide is designed to help developers to implement In-Store Digital Wallet Payment Processing Sandbox API’s.

About this document

In this section, you will learn how to:

1. Implement basic payment scenarios: Two types of In-Store QR Code payments: customer-presented and merchant-presented. Create a sandbox environment to test the APIs for In-Store QR Code Payments.
2. Make secure API Calls with VeriSign: Use encryption tools to secure API interactions.
3. Implement best practices: We provide answers to common questions and recommended implementations for features such as split payments, partial refunds, mid-transaction cancellations, and reporting workflows.

The tutorials and explanations in this document will refer to Pockyt's base Sandbox URLs:

Sandbox APIs Base URL: https://mapi.yuansfer.yunkeguan.com
Production APIs Base URL: https://mapi.yuansfer.com/

## Prerequisites

The following system components, peripherals, and test devices are required for the implementation of your project:

* A barcode scanner capable of extracting payment-barcode string values from a test digital wallet application
* You will need your Apple iOS store account ID and your Google Play store account ID with iOS TestFlight installed on your phone.
* To generate payment barcode strings, you will need an iOS and an Android device to install and test digital wallet applications from PayPal, AliPay, and CashApp.
* Depending on your network configuration, you may need to open ports in your firewall to allow r POST messagse frommPockyt to send messages to listener URLs on your back-end server.

## Getting started with Pockyt Developement Sandbox

This section provides instructions for setting up a development account with Pockyt, obtaining
sandbox credentials, and installing the test digital wallet applications.

High level steps

* STEP 1 - Setting up a development account with Pockyt.
* STEP 2 - Download and Install Sandbox Digital Wallet Applications: PayPal, AliPay, CashApp

## Step 1 - Setting up a development account with Pockyt

1. Send a request for a sandbox account to devsupport@pockyt.io.
2. Upon receiving payment information, Pockyt's developer support team will contact you. We can assist you with enabling methods and developing payment use cases.

## STEP 2 - Download and Install Sandbox Digital Wallet Applications: PayPal, AliPay, CashApp

To test the customer-presented QR code payment scenario, you need to install a test application on a mobile device. Provide the Apple IDs and Google Play IDs associated with the mobile devices where you will install the sandbox digital wallet applications.  We will forward you invitations for iOS Testflight and the Google Play store to install these test applications.

Various digital wallet apps are available, but you can install a single digital wallet type on your mobile device to test the full transaction flow.

| Digital Wallet Type |  | iOS                 | Android OS           |
| ------------------- | - | ------------------- | -------------------- |
| PayPal              |  | Provide Apple ID’s | Provide Play ID’s   |
| CashApp             |  | Provide Apple ID’s | Provide Play ID’s   |
| AliPay              |  | Not Available       | Direct Download only |

We recommend installing the AliPay test digital wallet on an Android test device.

Follow the steps to install the Alipay digital wallet test application:

1. Send an email to devsupport@pockyt.io and request the AliPay .APK file
2. Install the .apk file onto the Android mobile device that you will use for testing.
3. Pockyt will provide you with login credentials.

You can use PayPal or CashApp digital wallet test applications.

To install Paypal and CashApp Follow these steps:

1. Send an email to devsupport@pockyt.io with the Apple ID’s and / or the Google Play ID’s
   associated with the mobile device.
2. You will receive an email  from the iOS Appstore or the Google Play store with an invitation to install the sandbox applications.

## Payment Scenarios and API Endpoints

Pockyt's In-Store payment API supports two basic payment scenarios.

* Customer Presented QR Code Payments
* Merchant Presented QR Code Payments

Below is a list of APIs designed to streamline customer-presented QR Code payments. All of these definitions use the Sandbox Base

* **/add endpoint**

Enables the creation of a transaction object and retrieval of a transaction number.

Sandbox URL: "https://mapi.yuansfer.yunkeguan.com/app-instore/v3/add"
Production URL: "https://mapi.yuansfer.com/app-instore/v3/add"

By using the /add endpoint, the customer can create a transaction object and retrieve a transaction number.

* **/create endpoint** is intended for merchants who present QR codes to customers. This API **generates** a QR code and transaction number for the customer to scan via their digital wallet **app, **allowing them to initiate the payment process.

Sandbox URL: "https://mapi.yuansfer.yunkeguan.com/app-instore/v3/create"
Production URL: "https://mapi.yuansfer.com/app-instore/v3/create"

* **/prepay** is intended for the Customer Presented QR Code use case, providing finalization of payment transactions and submission to digital wallet servers for payment.

  Sandbox URL: https://mapi.yuansfer.yunkeguan.com/app-instore/v3/prepay
  Production URL: https://mapi.yuansfer.com/app-instore/v3/prepay
* **/refund endpoint** can be used to refund payments in either use case, providing flexibility and
  ease of use.
* **/cancel endpoint**

If a payment transaction is abandoned before submission, it can be canceled using the /cancel endpoint. It helps merchants manage their transactions.

Sandbox URL: "https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/refund"
Production URL: "https://mapi.yuansfer.com/app-data-search/v3/refund"

The **/trans-query** endpoint enables the retrieval of details of past transactions, allowing merchants to keep track of their transactions and reconcile their records.

Sandbox URL: ""https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/trans-query"
Production URL: "https://mapi.yuansfer.com/app-data-search/v3/trans-query"

## Customer Presented QR Code Payment Scenario

In this type of In-Store payment, customers present a QR Code generated by their digital wallet app on their mobile device. The merchant then scans the code at the point-of-sale terminal to process the transaction.

Here are the steps of a merchant-presented QR Code payment transaction itinerary.

1. Imagine an in-store retail environment with a customer checkout Point-of-Sale (POS) system.
2. A customer approaches POS manager for an itemized bill for 'outgoing merchandise.
3. The consumer reveals that they prefer to pay with a digital wallet.
4. POS manager selects 'Digital Wallet' that prompts Point-of-Sale to call the "/add" API for the creation of the transaction ID.

   POST https://mapi.yuansfer.com/app-instore/v3/add
5. At the same time, Point-of-Sale analyzes the /add API response message to identify and store the transaction number.
6. After creating a transaction ID, the customer presents a QR code to the POS manager.
7. As the QR code is scanned, the POS system calls Pockyt’s “/prepay” API to process the digital wallet payment.

   POST https://mapi.yuansfer.com/app-instore/v3/prepay
8. With the "/tran-query" API, the POS manager checks the transaction status and prompts the customer to confirm the transaction.

   POST https://mapi.yuansfer.com/app-data-search/v3/tran-query
9. After confirmation, the digital wallet server processes the payment and notifies Pockyt.
10. After a successful transaction, the POS system displays a 'success' message to the customer screen.
11. POS systems generate a transaction receipt that contains all information about the transaction.

## Merchant Presented QR Code

Merchants generate QR codes either on their customer-facing displays or on paper receipts. Using their digital wallet, the customer scans this code to complete the payment.

In-Store User Workflows and API Interactions

Listed below are the steps of a QR Code payment made by a merchant

1. The customer approaches the Point-of-Sale (POS) manager, who supervises the checkout process within an in-store retail environment.
2. During the purchase process, the customer asked about paying via a digital wallet.
3. The POS manager selects “Digital Wallet” as the tender type, and the POS system calls Pockyt’s /create-trans-qrcode API to generate the QR Code.

   POST: https://mapi.yuansfer.com/app-instore/v3/create-trans-qrcode
4. The Pockyt endpoint generates the QR Code along with a transaction no. that appears
   on a customer-facing display.
5. Using their digital wallet application, the customer scans the merchant's QR code to pay. In order to process the payment, the customer must confirm (or cancel) the transaction before it can proceed.
6. Upon confirmation, the digital wallet server processes the payment and alerts Pockyt with the transaction result and a transaction number.
7. Pockyt relays the processing results from the wallet service to the merchant’s Pointof-Sale via IPN callback.
   See tutorial section attached on how to configure your IPN callback settings
8. The Point-of-Sale generates a customer receipt marking the end of the transaction.

## Customer Refunds

For a refund request, the following request and response objects are initiated.

* The customer approaches the Point-of-Sale (POS) manager, who supervises the checkout process within an in-store retail environment.
* The POS manager will scan the barcode or paper receipt by selecting the “refund” button.
* With the transaction number, the Point-of-Sale identifies the original purchase and requests a refund from the digital wallet server using Pockyt's /refund API
  POST: https://mapi.yuansfer.com/app-data-search/v3/refund
* The wallet server will reimburse the transaction amount to the customer as well as alert the latter about the refund via a notification.

## Cancel the transaction / Void

The API allows merchants to cancel a payment transaction in either scenario if the transaction is abandoned before submission, enabling them to manage their transactions efficiently.

* The customer uses a digital wallet to pay for the items of purchase.
* The merchant selects “digital wallet” and the Point-of-Sale calls Pockyt’s /add API to generate a transaction object.
* The customer finds that they are unable to generate a QR code for the merchant to scan due to a lack of connectivity (or another issue).
* The merchant  select “cancel” in the Point-of-Sale system by calling Pockyt’s /cancel API. The cancel API enables cancelling a payment transaction. This applies to transactions that are abandoned before submission.
* Pockyt notifies the digital wallet server to abandon the transaction.
* The digital wallet server responds by canceling the transaction and notifying Pockyt of the
  cancellation status.
* Pockyt will then relay the information to the Point-of-Sale.

## Apendix B: Tutorial: Calculate VeriSign Value

Pockyt transactions don't require secret tokens or passwords, so there's no risk of hacking or fraud. Instead, we use the verifySign parameter to authenticate and authorize API requests at every step of the transaction process.

The verifySign parameter serves as your API parameter signature. You can build this parameter by retrieving the API token from Pockyt’s dashboard. MD5 authentication hashes can then be calculated using the latter and MD5 encryption.

**To ensure the security of your API token, follow these best practices.**

1. Store your API token securely on the backend of your application, such as in a database or configuration file. Ensure that only those who need them have access to them. Version control or hardcoding of your token is not recommended.
2. Use secure encryption algorithms: Use encryption algorithms like AES or RSA to encrypt your API token before storing it. By doing so, the token is protected from unauthorized access.
3. Implement rate limiting to prevent attackers from launching brute-force attacks against your API. The purpose of this is to prevent attempts to guess valid tokens.
4. Monitor logs for suspicious activity, such as multiple failed API access attempts or requests with invalid tokens, and take the necessary action.

**Follow the steps below to implement the VeriSign feature:**

1. Sort the parameters alphabetically according to the parameter name.
2. Concatenate the parameter names and values using '=' and '&' characters.
3. Append the MD5 hash value of your API token to the end of your parameters with the '&'
   prefix.
4. Calculate the MD5 hash value of the Step 3 result.

## Calculating the VeriSign Parameter Value

Consider the following Parameters

```
amount = '1.00'
storeNo = '300014'
currency = 'USD'
merchantNo = '200043'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
terminal = 'ONLINE'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
reference = 'seq_1525922323'
vendor = 'alipay'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
timeout = '120'
```

First, sort the parameters alphabetically

```
amount = '1.00'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
currency = 'USD'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
merchantNo = '200043'
reference = 'seq_1525922323'
storeNo = '300014'
terminal = 'ONLINE'
timeout = '120'
vendor = 'alipay'
```

Next, concatenate the parameter names and values using '=' and '&' characters

```
amount=1.00&callbackUrl=https://wx.yuansfer.yunkeguan.com/wx&
currency=USD&goodsInfo=
[{"goods_name":"Yuansfer","quantity":"1"}]&ipnUrl=https://wx.yuansfer.yunkeguan.com/wx&m
erchantNo=200043&reference=seq_1525922323&storeNo=300014&terminal=ONLINE&timeo
ut=120&vendor=alipay
```

## Calculating the VeriSign Parameter Value

Calculate the MD5 value of your API token and append to the string with the '&' character.

For example, if the API token is **5cbfb079f15b150122261c8537086d77a** the MD5 hash
value is **186abea4b8610d7ff03768255588597a** so the resulting string is:

amount=1.00&callbackUrl=https://wx.yuansfer.yunkeguan.com/wx&
currency=USD&goodsInfo=
[{"goods_name":"Yuansfer","quantity":"1"}]&ipnUrl=https://wx.yuansfer.yunkegu
an.com/wx&merchantNo=200043&reference=seq_1525922323&storeNo=3000
14&terminal=ONLINE&timeout=120&vendor=alipay&186abea4b8610d7ff03768
255588597a

Finally, you will calculate the MD5 hash value of the entire string in the block above.
The MD5 hash value is **b6bfd66531ae7c9499115c7480a2c8aa** and this is the value that
you will pass in the VeriSign parameter of your API request.

Next, concatenate the parameter names and values using '=' and '&' characters

curl -XPOST -d '{
amount = '1.00'
storeNo = '300014'
currency = 'USD'
merchantNo = '200043'
callbackUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
terminal = 'ONLINE'
ipnUrl = 'https://wx.yuansfer.yunkeguan.com/wx'
reference = 'seq_1525922323'
vendor = 'alipay'
goodsInfo = '[{"goods_name":"Yuansfer","quantity":"1"}]'
timeout = '120'
"verifySign": "b6bfd66531ae7c9499115c7480a2c8aa",
}' 'https://mapi.yuansfer.com/app-instore/v3/add'

## Appendix C: Tutorial: Instant Payment Notifications

The Instant Payment Notification (IPNurl) is a callback function that helps Pockyt notify the merchant about any new transaction-related event. Pockyt waits for the merchant’s website to Acknowledge the IPN messages before proceeding.

Here’s how to access Pockyt’s IPN service

* Create an IPN listener page on your website. This listener page will contain a custom script **or a program** to receive back-end messages.
* Include the URL of this listener page in the request body. This will allow you to receive all transaction-related event notifications sent by Pockyt.
* Every time a transaction occurs, Pockyt sends an instant payment notification (IPN) to the merchant’s listener page URL using the secure POST method.
* The IPN listener page parses the transaction information and processes them to the custom script for verification.
* After verifying the success status of these messages, the custom script or program will forward them to the back-end applications for processing.
* At this point, the listener page must acknowledge Pockyt’s IPN messages with a “success” string.
* IPN messages are not synchronized with the merchant's website and can get lost or delayed due to poor internet connectivity.

  For this reason, Pockyt’s IPN service continues to resend IPN messages until the listener page acknowledges them. If the listener page does not acknowledge messages, eight messages will be sent in two hours.

### **Call Parameters**

It is recommended for the merchant system to validate the parameters in the callback information using verifySign. This is to eliminate the possibility of tampering with the data. Pockyt’s callback function will contain the following parameters along with the IPN.

| Parameter      | Type   | Description                                                                                                           |
| -------------- | ------ | --------------------------------------------------------------------------------------------------------------------- |
| transactionNo  | string | The Transaction ID in the Pockyt system.                                                                              |
| status         | string | The status of the transaction                                                                                         |
| amount         | string | The transaction amount.                                                                                               |
| currency       | string | The supported transaction currency are "USD", "CNY", "PHP",  "IDR", "KRW", "HKD", "THB", "MYR", "GBP", "BDT", "PKR". |
| settleCurrency | string | The supported settlement currency are "USD", "GBP"                                                                    |
| time           | string | The date and time when the authorization was createdFormat :"YYYYMMDDHHMMSS."                                         |
| Reference      | string | The transaction's invoice number in the merchant’s system.                                                           |
| vendorId       | string | Providers Transaction ID                                                                                              |
| note           | string | The payment note                                                                                                      |
| verifySign     | string | The parameter signature                                                                                               |

Tutorial: Processing an AliPay Payment

Here is a step-by-step tutorial that describes how to accept payments from AliPay digital wallets at the Point of Sale. Our Javascript code samples demonstrate each API interaction. We have published SDKs on GitHub that include code samples in other languages.

In-Store User Workflows and API Interactions

Here are the steps of a QR code payment presented by a merchant.

1. Consider an in-store retail environment with a customer checkout Point-of-Sale (POS).
2. A customer approaches the POS manager who drafts an itemized bill for the ‘outgoing
   merchandise’.
3. Upon inquiry, the consumer states that they would prefer to pay using a digital wallet.
4. The POS manager selects ‘Digital Wallet’ which prompts the Point-of-Sale to call the "/add".

API for the creation of a transaction ID.

POST https://mapi.yuansfer.com/app-instore/v3/add

First you will need to calculate the VeriSign parameter value (instructions are available in a separate tutorial)

First you will need to calculate the VeriSign parameter value (instructions are available in a
separate tutorial)

* Sort the parameters alphabetically according to the parameter name.
* Concatenate the parameter names and values using '=' and '&' characters.
* Append the MD5 hash value of your API token to the end of your parameters with the '&' prefix
* Calculate the MD5 hash value of the Step 3 result.

## Code Sample: Calling the /Add API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alphabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace: for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// alphabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}
}

## Code Sample: Calling the /Add API

Example in Javascript

// Prepare JSON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

Next, receive Transaction ID and call to /PrePay

* At the same time, the Point-of-Sale analyzes the response message from the /add API
  to identify and store the transaction number.
* Once the transaction ID is created, the customer will present a QR code to the POS
  manager for scanning.
* As the QR code is scanned, the POS system calls Pockyt’s “/prepay” API to process
  the digital wallet payment.
  POST https://mapi.yuansfer.com/app-instore/v3/prepay

## Code Sample: Calling the /PrePay API

Example in Javascrip

// POCKYT ADD API sandbox example
// Import crypto for MD5 hash calculation
var crypto = require('crypto');
// Assign all Sanbox parameters
var URL = "https://mapi.yuansfer.yunkeguan.com/app-instore/v3/prepay" ;
var merchantNo = "200043" ;
var storeNo = "303660" ;
var MyToken = "359c05eb811c7c8576f4a8a277dc6f6b" ;
// construct POS fields and assign to object
var myPOSParamObject = {
merchantNo: merchantNo,
storeNo: storeNo,
transactionNo: "316129873376769782",
paymentBarcode: "286521182446652715",
vendor: "alipay"
}
// Calculate the VeriSign signature:
var MySignature = CalculateSignature(MyToken, myPOSParamObject)
// Add the signature to the POS parametes so we
// can use it in the body of the API call
var MyPocketParamObject = {
merchantNo: myPOSParamObject.merchantNo,
storeNo: myPOSParamObject.storeNo,
verifySign: MySignature,
transactionNo: myPOSParamObject.transactionNo,
paymentBarcode: myPOSParamObject.paymentBarcode,
vendor: myPOSParamObject.vendor
}

## Code Sample: Calling the /PrePay API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alphabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace:
for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// algabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}
}

## Code Sample: Calling the /PrePay API

Example in Javascript

// Prepare JSON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// POCKYT TRANSACT QUERY AFTER AND ADD TO CHECK RESULTS API
sandbox example
// Import crypto for MD5 hash calculation
var crypto = require('crypto');
// Assign all Sanbox parameters
varURL="https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/tranquery" ;
var merchantNo = "200043" ;
var storeNo = "303660" ;
var MyToken = "359c05eb811c7c8576f4a8a277dc6f6b" ;
// construct POS fields and assign to object
var myPOSParamObject = {
merchantNo: merchantNo,
storeNo: storeNo,
transactionNo: "316129873376769782",
// reference: No reference in this case
}
// Calculate the VeriSign signature:
var MySignature = CalculateSignature(MyToken, myPOSParamObject)
// Add the signature to the POS parametes so we
// can use it in the body of the API call
var MyPocketParamObject = {
merchantNo: myPOSParamObject.merchantNo,
storeNo: myPOSParamObject.storeNo,
verifySign: MySignature,
// transactionNo: myPOSParamObject.transactionNo,
// reference: myPOSParamObject.reference
transactionNo: myPOSParamObject.transactionNo
}

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alfabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace : for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// alphabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}

## Code Sample: Calling the /Trans-Query API

Example in Javascript

// Prepare JASON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

## Code Sample: Calling the /Refund API

Example in Javascript

// POCKYT ADD API sandbox example
// Import crypto for MD5 hash calculation
var crypto = require('crypto');
// Assign all Sanbox parameters
var URL = "https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/refund" ;
var merchantNo = "200043" ;
var storeNo = "303660" ;
var MyToken = "359c05eb811c7c8576f4a8a277dc6f6b" ;
// construct POS fields and assign to object
var myPOSParamObject = {
merchantNo: merchantNo,
storeNo: storeNo,
refundAmount: "10",
currency: "USD",
settleCurrency: "USD",
transactionNo: "316129873376769782",
}
// Calculate the VeriSign signature:
var MySignature = CalculateSignature(MyToken, myPOSParamObject)
// Add the signature to the POS parametes so we
// can use it in the body of the API call
var MyPocketParamObject = {
merchantNo: myPOSParamObject.merchantNo,
storeNo: myPOSParamObject.storeNo,
verifySign: MySignature,
refundAmount: myPOSParamObject.refundAmount,
currency: myPOSParamObject.currency,
settleCurrency: myPOSParamObject.settleCurrency,
transactionNo: myPOSParamObject.transactionNo
}

## Code Sample: Calling the /Refund API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alfabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace : for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// algabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}
}

## Code Sample: Calling the /Refund API

Example in Javascript

// Prepare JASON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));

## Code Sample: Calling the /Cancel API

Example in Javascript

// POCKYT ADD API sandbox example
// Import crypto for MD5 hash calculation
var crypto = require('crypto');
// Assign all Sanbox parameters
var URL = "https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/cancel" ;
var merchantNo = "200043" ;
var storeNo = "303660" ;
var MyToken = "359c05eb811c7c8576f4a8a277dc6f6b" ;
// construct POS fields and assign to object
var myPOSParamObject = {
merchantNo: merchantNo,
storeNo: storeNo,
transactionNo: "316130255682193722"
}
// Calculate the VeriSign signature:
var MySignature = CalculateSignature(MyToken, myPOSParamObject)
// Add the signature to the POS parametes so we
// can use it in the body of the API call
var MyPocketParamObject = {
merchantNo: myPOSParamObject.merchantNo,
storeNo: myPOSParamObject.storeNo,
verifySign: MySignature,
transactionNo: myPOSParamObject.transactionNo
}

## Code Sample: Calling the /Cancel API

Example in Javascript

// function that calculates the signature according to Pockyt rules
function CalculateSignature(token,parameters)
{
// calculate the hash value of the token
var ApiTokenHashvalue = crypto.createHash('md5').update(token).digest("hex")
// order parameters alfabetically
var SortedParams = sortObj(parameters);
// Concatenate: add '&' between key and value pair and replace : for =
var MyString = '' ;
for (const [key, value] of Object.entries(SortedParams)) {
MyString += (`${key}=${value}&`);}
// add hash value of token at the and of the string
MyString += ApiTokenHashvalue ;
// create the verifySign
const MySignature = crypto.createHash('md5').update(MyString).digest("hex");
return MySignature;
// algabetical sort helper function
function sortObj(obj) {
return Object.keys(obj).sort().reduce(function (result, key) {
result[key] = obj[key];
return result;
}, {});
}
}

## Code Sample: Calling the /Cancel API

Example in Javascript

// Prepare JASON that will be used in the body of the API call
var MyPocketParamJason = JSON.stringify(MyPocketParamObject);
console.log(MyPocketParamJason);
fetch(URL, {
method: "POST",
headers: {
"Content-Type": "application/json"
},
body: MyPocketParamJason
})
.then(response => response.json())
.then(data => console.log(data))
.catch(error => console.error(error));
