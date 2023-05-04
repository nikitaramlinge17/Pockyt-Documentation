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

*  A Sandbox API's Base URL  "https://mapi.yuansfer.yunkeguan.com"
*  Production API's Base URL's "https://mapi.yuansfer.com/"

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

# Guides
      
    In the Guides section, developers can find comprehensive documentation and detailed explanations of the API's functionality.
    
## Getting Started with Online Payment APIs

    Our Online digital wallet payment processing APIs help you to understand technical concepts and provide step-by-step tutorials for implementing them.
    
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

    
### Step 3 - Installing the test digital wallet applications.


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

    Pockyt Checkout: API Workflow Diagram
    ![Pockyt Checkout](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image1.png)

    
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
  *  Braintree complies with the request and passes the transaction results to Pockyt, who relays them back to the merchant website. 
    
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
    
    # Customer Refunds
    In the instance where a customer requests a refund, the following request and response objects are initiated to complete the refund workflow.

    ## Refund API Workflow

    The following steps depicts Refund API workflow:

      1 - The customer will apply for a refund on the merchant`s website using the transaction number.
      
      2 - The merchant`s system will use the transaction number to identify the exact details of the original purchase and call refund API which will request the digital wallet server to refund the payment originally made by the customer.
      
      3 - The wallet server will reimburse the transaction amount to the customer as well as alert the latter about the refund via a notification.
       
      ![Refund API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image4.png) 

    # Cancel the transaction / void
      In the event of a customer canceling the purchase the following request and response objects are created to complete the cancellation process successfully.
    
    ## Cancel API Workflow 

    The following steps depicts Cancel API workflow:

      1 - The customer applies for payment on the merchant's website after shopping.

      2 - If the customer is unable to confirm payment due to connectivity issues, they can select the cancel option in the payment UI.

      3 - The merchant's system calls Pockyt's /cancel API to cancel the payment transaction.

      4 - Pockyt notifies the digital wallet server to abandon the transaction.

      5 - The digital wallet server cancels the transaction and notifies Pockyt of the cancellation status.

      6 - Pockyt relays the information to the merchant's system.

      ![Cancel API](https://raw.githubusercontent.com/nikitaramlinge17/Pockyt-Documentation/main/assets/image5.png)
    
    # Recurring Payments (Auto Debit)
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

    # Apendix B: Tutorial: Calculate VeriSign Value

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

      * Create an IPN listener page on your website. This listener page will contain a custom script or a program to receive back-end messages.
      * Include the URL of this listener page in the request body. This will allow you to receive all of the transaction-related event notifications sent by Pockyt to your website.
      * Every time a transaction occurs, Pockyt sends an instant payment notification (IPN) to the merchant`s listener page URL using the secure POST method.
      * The IPN listener page parses the transaction information and processes them to the custom script for verification.
      * After verifying the success status of these messages, the custom script or program will forward them to the back-end applications for processing.
      * At this point, the listener page must acknowledge Pockyt`s IPN messages with a “success” string.
      * Keep in mind that the IPN messages are not synchronous with the merchant`s website and there is always a chance for these notifications to get lost or delayed due to poor internet connectivity.

      Pockyt`s IPN service continues to resend the IPN messages until the listener page acknowledges. If the listener page fails to acknowledge the messages, it will continue to receive them up to eight times in two hours.

**Callback parameters**

      It is recommended for the merchant system to validate the parameters in the callback information using verifySign. This is to eliminate the possibility of processing tampered information. Pockyt`s callback function will contain the following parameters along with the IPN.


