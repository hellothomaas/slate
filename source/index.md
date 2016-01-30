Getting Started
===============

PCI Proxy is a service that can **securely collect, store and forward credit cards** (payment data) to any payment gateway (e.g. Stripe) or other PCI-certified third party (e.g. Expedia). It can even **extract payment data out of web service calls** (e.g. Booking.com) while allowing the message body to remain unaffected. By using tokenization, our APIs ensure **sensitive payment data never touches your system environment**.

##How it works
Bild mit komplettem Prozess (Inbound & Outbound)
![enter image description here](http://thomaas.com/img/thomaas.png)

##Quick Start Guide

Here is a quick step-by-step instruction on how to get started and quickly reduce your PCI scope.

 1. Collect or extract payment data with our APIs 
 2. Use stored payment data

**Important: Your API key (merchant ID)**
> For your convenience, we have pre-filled our examples with a test API key so you can start off testing right away.

On the following pages you will find several sample scripts that run on our test environment. You will notice the merchant ID attribute. Merchant IDs are unique API keys that will identify your environments at PCI Proxy once you are registered. 
You can have multiple merchant IDs. For instance, if you have different environments on which you receive payment data (e.g. website, web service, mobile app), we recommend separating your environments by using a single merchant ID for each.
In order to [go live](golive), you will need to replace the test API key with a production API key. You can get your production keys by [registering an account at PCI Proxy](register).

### Register Account

Before you register an account at PCI Proxy, you can use PCI Proxy only in test mode. With the exception that only test credit cards can be used, all PCI Proxy features are fully available in test mode.
Registering an account at PCI Proxy is simple. You send us an email to setup@pci-proxy.com with the follow-ing information:
Company name	
Language	
Country	

We will return a form, requesting some basic information about your company, contact persons, etc. 30 days free trial???

Sample Business Cases
=====================

The following list of business cases is not complete and should only give an overview of business types that already use PCI Proxy.

## Middle Office

*You are a middle office that receives booking information on behalf of your clients.*

> PCI Proxy supports a varienty of [different approaches for you to collect the payment data][1]. 
The most common approach is to submit data directly from your software using our [payment pages][2]. Another option is [pay-by-email][3] where payment links are issued that can be emailed to customers to let them enter their payment details by them-selves. Now you have shielded your server by using our APIs to extract and collect payment data and stored it in our PCI Proxy vault up front.

> PCI Proxy allows you to [forward vaulted payment data][4] to PCI compliant third parties.



*Travel agencies use your software to drop new bookings. At some point, they will enter the customers’ payment data in your software. In order to minimize your PCI scope, this payment data should be added without touching your server.*

*On behalf of your clients you want to process the booking or transact with different endpoints (e.g. Expedia, Stripe, TUI, Lufthansa, etc.).*



## Channel Manager

> PCI Proxy allows you to [extract payment data from web service calls][6] and securely store it in PCI Proxys' vault. Your server will never get in touch with sensitive card data which reduces your PCI scope immediately.
> PCI Proxy provides several ways on how to [use stored payment data][7]. Your clients can either [retrieve payment data][8] via NoShow.jsp, [charge payment data][9] against a payment processor or [forward payment data][4] to a PCI-compliant third party, eg. Expedia.


*You are a channel manager that requests or receives booking information from distribution channels, e.g. [Booking.com][5].*

*Hotels and accommodation providers transmit availabilities and prices to various distribution channels. It also automatically retrieves bookings including payment data from the online booking platforms.*
*Generally, you will store payment data only to allow your hotels to charge cards in case of a no-show.*

 [1]: #collect
 [2]: #paymentpages
 [3]: #paybyemail
 [4]: #forward
 [5]: http://www.booking.com/
 [6]: #extract
 [7]: #use
 [8]: #retrieve
 [9]: #charge

Features
========

PCI Proxy has 3 different features: Collect, Validate, Use. 

|Collect|Validate|Use|
|---|---|---|
|from web service|credit card check|Forward|
|from website||Charge|
|from mobile app||Retrieve|

First you need to collect payment data to store it in our secure vault. You will find different approaches on how you can collect or extract payment data from different environments (e.g. web service APIs, website, mobile app). If you have specific environments that are not listed, please get in touch. We are quick and flexible to enhance our Proxy features. 

Once you have collected the payment data, you might want to validate the credit cards and check if the card is valid and can be charged.

As soon as payment data is collected, you can make use of it. You can either forward payment data to PCI-compliant thirdparties (e.g. Expedia), charge payment data through a payment gateway (e.g. Datatrans), or retrieve single payment data sets (e.g. to book a No-Show). 

##Collect payment data

Whether you receive payment data via API, accept credit cards on a website or collect them in a mobile app, you can use PCI Proxy APIs. Our APIs automatically tokenize the payment information before they ever touch your systems to instantly reduce your PCI scope. 

PCI Proxy APIs are organized in environments, meaning the different ways on how you could possibly receive or collect payment data. 

**Considering the following cases:**

 - You receive or request messages including payment data via APIs from your partners or clients. For example, you receive transaction related data from Booking.com. [Learn about Extracting.](extract)
 - You collect payment data on a website. For instance, you have an Internet booking engine running on your website. [Learn about Payment Pages.](paymentpage)
 - You have a native mobile app (iOS or Android) and collect payment from customers. For instance, you give your clients the opportunity to book your product or service through a mobile app. [Learn about In-App Payment Libraries.](paymentlib)
 - You need to enter payment data into your system on behalf of your clients. For instance, you are a travel agency that works with a middle office system and want to avoid that employees get in contact with payment data. [Learn about Pay-by-Email.](paybyemail)


##From web service calls
If you run a web service that receives or requests messages via API from your partners or clients (channel) that include sensitive payment data, PCI Proxy can extract it and automatically store it securely in PCI Proxys’ vault. 

Together with the stored payment data, a reference number (token) is issued that substitutes the payment data field in your request. The message structure of the channel API always remains the same. The token can be used later on to charge, forward or retrieve payment data. All of this happens before sensitive payment data ever touch your server to minimize your PCI scope. 

> You are allowed to store the token in your system, as it is not PCI DSS relevant.

**PCI Proxy supports push and pull APIs**
In general, you either perform a pull request to receive data or a channel pushes data to your server. PCI Proxy can extract payment data from both operations before sensitive payment data touch your server.

##Extracting from pull API
When you perform a pull request against another API, payment data can easily extracted from already sup-ported APIs or by adding a new channel API.

**Consider a business that needs this ability:**
*You are a travel technology company that pulls new reservations from connected reservation portals such as Booking.com. When performing a pull request against Booking.com’s API, you receive booking information including payment data as a response. Booking.com asks all of their IT providers, which receive payment data to be PCI DSS compliant. 
With the use of PCI Proxy, Booking.com removes this requirement from you, as we as a company are PCI DSS compliant and you can bank on our full Level 1 PCI DSS compliance.* 

###How to start
You can start and perform the following cURL example. It will give you and understanding of how PCI Proxys’ pull channel API works. Once you have understand it, you can use one of our supported pull channel APIs or add a new pull channel API.  

    ```API Endpoint / cURL example einfügen```

###Supported pull channel APIs
We support a variety of channel APIs out of the box. Every day, more and more channels get added. Please find below an uncomplete list of channels we already support. In case your required API is not on the list, add-ing a new channel API is easy. 

    ```Booking.com – cURL example``` 

###Adding a new pull channel API
If your required channel API is not supported yet, you can easily add new pull channel APIs by yourself. Just send us the following information to setup@pci-proxy.com. 

|Information| Description   |
|---|---|
|Target URL|The URL where we should forward the populated request to (your server).|
|Sample Request & Response|Please include API name, required headers, auth fields, and request method.|
|IP Address|IP address of your partners’ server that will send the push messages.|
	
	
	
