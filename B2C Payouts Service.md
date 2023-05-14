# About this document

In this section, you will learn how to:

1. Implement payment scenarios in which businesses make payments to consumer digital wallets or bank accounts.
2. Implement Payouts Transactions to the following payment methods:

* PayPal / Venmo Digital Wallets
* Consumer Bank Accounts in USD
* AliPay+ Network - Coming Soon, will be included in future versions of this guide

3. Make secure API Calls with VeriSign: Use encryption tools to secure API interactions.

* Sandbox URL:  "https://mapi.yuansfer.yunkeguan.com/app-data-search/v3/cancel"
* Production URL: "https://mapi.yuansfer.com/app-data-search/v3/cancel"

# Getting started with Pockyt Developement Sandbox

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

# Terminology and Basic Payout User Work Flow

The basic payment scenario for Pockyt’s Payouts Payment API’s.

* The **Merchant (Payor)** uses Payout's service to transfer funds from their business bank account to an individual's (payee's) consumer digital wallet, bank account, or other consumer account payment methods.
* An **Individual Payee** has an Affiliate Marketing relationship with a merchant store. The Merchant Store pays a Commission to the Individual Payee when their traffic leads to a purchase at the store.
* When the Individual Payee directs traffic to the store, leading to a purchase, the Merchant Store pays a commission via their Pocky Payor Account.
* To receive their Commission Payout, the Individual Payee must create a **Pockyt Payee Account**, where they can configure their payout preferences, such as how they would like to receive their funds (bank account, PayPal, Venmo, etc).

  ![1683734210916](image/In-StoreDigitalWalletPaymentProcessingSandboxAPI’s/1683734210916.png)

# Payment Scenarios and API Endpoints

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

# Calculating the VeriSign Parameter Value

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

# Calculating the VeriSign Parameter Value

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
