#Getting Started

PCI Proxy is a service that can **securely collect, store and forward credit cards** (payment data) to any payment gateway (e.g. Stripe) or other PCI-certified third party (e.g. Expedia). It can even **extract payment data out of web service calls** (e.g. Booking.com) while allowing the message body to remain unaffected. By using tokenization, our APIs ensure **sensitive payment data never touches your system environment**.

##How it works
Bild mit komplettem Prozess (Inbound & Outbound)
![enter image description here](http://thomaas.com/img/thomaas.png)

##Sample Business Cases
The following list of business cases is not complete and should only give an overview of business types that already use PCI Proxy.

### Middle Office

> PCI Proxy supports a varienty of [different approaches for you to collect the payment data][1]. The most common approach is to submit data directly from your software using our [payment pages][2]. Another option is [pay-by-email][3] where payment links are issued that can be emailed to customers to let them enter their payment details by them-selves. Now you have shielded your server by using our APIs to extract and collect payment data and stored it in our PCI Proxy vault up front.
> PCI Proxy allows you to [forward vaulted payment data][4] to PCI compliant third parties.

*You are a middle office that receives booking information on behalf of your clients.*

*Travel agencies use your software to drop new bookings. At some point, they will enter the customers’ payment data in your software. In order to minimize your PCI scope, this payment data should be added without touching your server.*

*On behalf of your clients you want to process the booking or transact with different endpoints (e.g. Expedia, Stripe, TUI, Lufthansa, etc.).*



### Channel Manager

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

## Quick Start Guide
Here is a quick step-by-step instruction on how to get started and quickly reduce your PCI scope.

 1. Collect or extract payment data with our APIs 
 2. Use stored payment data

**Important: Your API key (merchant ID)**
> For your convenience, we have pre-filled our examples with a test API key so you can start off testing right away.

On the following pages you will find several sample scripts that run on our test environment. You will notice the merchant ID attribute. Merchant IDs are unique API keys that will identify your environments at PCI Proxy once you are registered. 
You can have multiple merchant IDs. For instance, if you have different environments on which you receive payment data (e.g. website, web service, mobile app), we recommend separating your environments by using a single merchant ID for each.
In order to [go live](golive), you will need to replace the test API key with a production API key. You can get your production keys by [registering an account at PCI Proxy](register).
