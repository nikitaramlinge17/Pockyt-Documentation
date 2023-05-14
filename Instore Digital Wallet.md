# About this document

In this section, you will learn how to:

1. Implement basic payment scenarios: Two types of In-Store QR Code payments: customer-presented and merchant-presented. Create a sandbox environment to test the APIs for In-Store QR Code Payments.
2. Make secure API Calls with VeriSign: Use encryption tools to secure API interactions.
3. Implement best practices: We provide answers to common questions and recommended implementations for features such as split payments, partial refunds, mid-transaction cancellations, and reporting workflows.

The tutorials and explanations in this document will refer to Pockyt's base Sandbox URLs:

Sandbox APIs Base URL: https://mapi.yuansfer.yunkeguan.com
Production APIs Base URL: https://mapi.yuansfer.com/

# Prerequisites

The following system components, peripherals, and test devices are required for the implementation of your project:

* A barcode scanner capable of extracting payment-barcode string values from a test digital wallet application
* You will need your Apple iOS store account ID and your Google Play store account ID with iOS TestFlight installed on your phone.
* To generate payment barcode strings, you will need an iOS and an Android device to install and test digital wallet applications from PayPal, AliPay, and CashApp.
* Depending on your network configuration, you may need to open ports in your firewall to allow r POST messagse frommPockyt to send messages to listener URLs on your back-end server.

# Getting started with Pockyt Developement Sandbox

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

# Payment Scenarios and API Endpoints

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

# Customer Presented QR Code Payment Scenario

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

# Merchant Presented QR Code

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


# Customer Refunds

For a refund request, the following request and response objects are initiated.


* The customer approaches the Point-of-Sale (POS) manager, who supervises the checkout process within an in-store retail environment.
* The POS manager will scan the barcode or paper receipt by selecting the “refund” button.
* With the transaction number, the Point-of-Sale identifies the original purchase and requests a refund from the digital wallet server using Pockyt's /refund API
  POST: https://mapi.yuansfer.com/app-data-search/v3/refund
* The wallet server will reimburse the transaction amount to the customer as well as alert the latter about the refund via a notification.



# Cancel the transaction / Void

The API allows merchants to cancel a payment transaction in either scenario if the transaction is abandoned before submission, enabling them to manage their transactions efficiently.


* The customer uses a digital wallet to pay for the items of purchase.
* The merchant selects “digital wallet” and the Point-of-Sale calls Pockyt’s /add API to generate a transaction object.
* The customer finds that they are unable to generate a QR code for the merchant to scan due to a lack of connectivity (or another issue).
* The merchant  select “cancel” in the Point-of-Sale system by calling Pockyt’s /cancel API. The cancel API enables cancelling a payment transaction. This applies to transactions that are abandoned before submission.
* Pockyt notifies the digital wallet server to abandon the transaction.
* The digital wallet server responds by canceling the transaction and notifying Pockyt of the
  cancellation status.
* Pockyt will then relay the information to the Point-of-Sale.


# Apendix B: Tutorial: Calculate VeriSign Value

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

# Calculating the VeriSign Parameter Value

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

# Calculating the VeriSign Parameter Value

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



# Appendix C: Tutorial: Instant Payment Notifications

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
| verifySign     | string | The parameter signature<br />                                                                                         |

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


# Code Sample: Calling the /Add API

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

# Code Sample: Calling the /Add API

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

# Code Sample: Calling the /PrePay API

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

# Code Sample: Calling the /PrePay API

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

# Code Sample: Calling the /PrePay API

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

# Code Sample: Calling the /Trans-Query API

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

# Code Sample: Calling the /Trans-Query API

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

# Code Sample: Calling the /Trans-Query API

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

# Code Sample: Calling the /Refund API

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

# Code Sample: Calling the /Refund API

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

# Code Sample: Calling the /Refund API

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

# Code Sample: Calling the /Cancel API

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

# Code Sample: Calling the /Cancel API

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

# Code Sample: Calling the /Cancel API

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
