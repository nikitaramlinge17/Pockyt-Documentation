# Documentation

## Introduction

Pockyt is a payment gateway utilized by various companies in retail and online to process payments, offering a digital wallet for seamless transfers and processing payments through point-of-sale systems, In-store payment, and Pay-out services.


## Overview

Pockyt API provides a powerful solution for integrating custom payment forms seamlessly into your website or application. By utilizing both client and server-side code the API enables the creation of a user friendly checkout form with all necessary payment elements included for the chosen payment method. This allows for a streamlined payment process making it easier for customers to complete transactions and for businesses to manage their payment processing.

## Pockyt Checkout: API Workflow Diagram

[![Pockyt Checkout](https://raw.githubusercontent.com/mcharudatta/YuansferDocs/main/assets/image1.png)](https://raw.githubusercontent.com/mcharudatta/YuansferDocs/main/assets/image1.png)

## Quickstart Tutorial

Pockyt offers a secure and user-friendly payment experience for customers, supporting a variety of payment methods such as digital wallets and card payments. Pockyt partners with multiple digital wallet providers, enabling businesses to attract and retain digital-native customers from all over the world. n endpoint. We recommend completing our quickstart tutorial on Pockyt products to learn key concepts.

1. Hosted Pages
2. Digital Wallets
3. Credit Card

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

## Prerequisites

Please ensure you have the following accounts and test devices available to complete your implementation project.

* Account ID's in the Apple iOS store, and Google Play store, with the iOS TestFlight application installed on your phone.
* An iOS device and an Android device on which you will download and install the test digital wallet applications from PayPal, AliPay and CashApp to generate payment barcode strings

## Guides

In the Guides section, developers can find comprehensive documentation and detailed explanations of the API's functionality.

### Getting Started with Online Payment APIs

Our Online digital wallet payment processing APIs help you to understand technical concepts and provide step-by-step tutorials for implementing them.

## Pockyt Developement Sandbox

High level steps

* STEP 1 - Setting up a development account with Pockyt.
* STEP 2 - Obtaining  API credentials.

For Obtaining API credentails, you need two sets of credentials from Pockyt to complete your implementation project.

### Step 1 - Sandbox API Credentials and Account Information

Enables you to test the entire transaction network relevant to your use cases.

Perform the following steps to obtain your Sandbox API credentials:

1. Visit the Pockyt developer's website and go to the Support tab.
2. Click "Developer Tools" and go to the Sandbox Environment tab.
3. Click the "Apply Sandbox Credentials" link to start the application process.
4. Wait for the Pockyt team to review and approve your application (usually takes 2 days).
5. Once approved, Pockyt will provide you with a dedicated secret token for the Sandbox environment.
6. The base URL for the Sandbox environment API is "https://mapi.Pockyt.yunkeguan.com"
7. Use the RESTful endpoints relevant to your use case with the initial calls made in test mode credentials to avoid incurring any costs.
8. To ensure optimal integrations and testing, your Sandbox environment should feature the front-end user interface for online payment workflows.
9. By following these steps, you can easily set up a Pockyt Sandbox account to test and refine your integration with Pockyt's API, providing a secure and user-friendly payment experience to your customers.

### Step 2 - Production API Credentials and Account Information

Enables you to begin processing live transactions from digital wallets and other payment methods.

Perform the following steps to obtain your Production API credentials:

1. Click Login and select Create Account to access the 10-step merchant application form.
2. Enter your credentials and submit the required documents business license or registration voided check or bank letter with company name, and government-issued photo identification.
3. Pockyt's team reviews your application and submits it to each digital wallet service they work.
4. Once approved, Pockyt automatically activates your live accounts, which takes around 1-2 business days for processing and approval.
5. Pockyt notifies you of your approval status and provides your Merchant No. and Store No. via email.
6. Log in to your account to collect your API token, which is required to build API parameters.
7. Each API request includes a verifySign parameter, which is the calculated MD5 hash value of your API token, allowing Pockyt to authenticate and authorize your API calls. For more information, visit "Signing API Parameters".

### Step 3 - Installing the test digital wallet applications.

## Payment Scenarios and API Endpoints

This section provides a step-by-step summary of the primary payment scenarios and explanations of the API endpoints relevant to each use case.

The following are two use cases and implementation paths

* Pockyt Checkout method** (referred to as the "SecurePay API") allows you to redirect customers to a Pockyt-hosted page for checkout. This is a favorable alternative payment solution if a business cannot host its payment forms for some reason.
* Pockyt Integrated Option** (referred to as the "PrePay API")  is a more suitable option for businesses looking to customize their payment form and retain complete control over the latter. This method allows businesses/merchants to build their UI for all the payment methods preferred by their customers.

## Implementation Option 1 - Checkout API

Using the SecurePay API, merchant websites can send customers to receive payments from Pockyt.

Perform the following steps to use Pockyt Checkout for online payment checkout.

1. The merchant system calls the create API to register a customer.
2. The merchant system generates a customer ID for future transactions and stores it in its database.
3. The merchant system then calls the secure-pay API to retrieve a cashierURL from Pockyt.
4. Using the cashierURL, the customer is redirected to Pockyt's hosted payment form.
5. After the payment is completed, Pockyt redirects the customer back to the merchant's payment result page using the provided callback URL in the request body of the secure-pay API.
6. Pockyt relays the transaction results to the merchant's website using the IPN callback function.
7. To receive the payment results, the merchant website creates an IPN listener page and uses its URL in the request body of the secure-pay API.
8. The merchant's website displays the payment confirmation message to the customer.

## Implementation Option 2 - Integrated Payments

Pockyt Integrated Payments offers a highly customizable payment form for businesses that want to retain complete control over the payment process.

This method enables businesses to build their user interface for all preferred payment methods, providing a seamless payment experience for their customers.

Merchants have the option to integrate Pockyt's APIs directly into their system for self-hosted mobile payments, or they can accept customer payments by integrating their system with Braintree, using both the /secure-pay API and the /process API.

## Pockyt Integrated Payments Workflow (Braintree)

Integrating the merchant system with Braintree will allow your customers to utilize digital wallets such as Google Pay, Apple Pay, Paypal, and Venmo to make payments for purchases secured on your website.

You can use Pockyt`s process API (discussed below) and/or secure-pay API (discussed earlier) to integrate with Braintree.

The first step is to create a Braintree account and then add the Braintree JavaScript SDK to the web page to accept payments and remain PCI-compliant.

Soon after creating an account, the merchant system will receive a payment_method_nonce, which is a one-time-use reference ID for the payment method.

### API Workflow for Merchants:

* The merchant system registers first-time customers by calling the create API, generating a customer number stored in the merchant's database for future reference.
* When the customer is ready to make a payment, the merchant website displays its payment page and calls the secure-pay API with YIP as the terminal value.
* The merchant system receives an authorization token and transaction ID instead of a cashier URL, which is required to accept payments with Braintree.
* Upon customer confirmation, the merchant system calls the process API to initiate the transaction.
* Pockyt uses the payment_method_nonce and transaction ID to request that Braintree process the payment.
* Braintree complies with the request and passes the transaction results to Pockyt, who relays them back to the merchant website.
