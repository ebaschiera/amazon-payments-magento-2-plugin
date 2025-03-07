# Change Log

## 5.7.1
* Fixed issue when phone number not required and entered in Magento
* Updated API calls to take in a masked cart ID so they can be used without relying on Magento sessions
* Updated logging to sanitize some data

## 5.7.0
* Changed the response of completeCheckoutSession API call to include both increment ID and order ID
* Fixed issue with logging in when a customer has an empty password hash (thanks @rafczow!)
* Fixed issue with sending too many decimal points to Amazon API, particularly an issue when using TaxJar as it uses more decimal points than Magento typically does (thanks @vkalchenko!)
* Fixed issue where the Address Form would not be shown even though Amazon address did not provide a needed field, particularly State/Province
* Fixed issue where using Amazon Pay in the Payment Methods section did not work on one step checkouts
* Fixed issue where using Amazon Pay in the Payment Methods section could bypass agreeing to Terms and Conditions
* Removed usage of isPlaceOrderActionAllowed in js components
* Updated response validators to look for specific response code and states

## 5.6.0
* Changed the merchantReferenceId to be set on the charge permission after the order is completed
* Changed IPN handling so that it wouldn’t re-try capture on duplicate messages
* Changed flow so any changes at billing step route back to shipping details as address could have changed
* Fixed issue where only the first invoice created would capture payment
* Fixed issue where sometimes the payment method isn’t set on the payment if the PayNow button is used
* Fixed issue where the street on German addresses could get set twice
* Fixed issue with the mobile tooltip being truncated

## 5.5.1
* Add url to csp_whitelist.xml
* Fix issue with the payment method button and UK addresses

## 5.5.0
* Added Auto Key Exchange for configuring the credentials
* Added PayNow functionality for the button on the final step of checkout
* Added more logging to the Alexa feature
* Added more logging to capturing flow
* Added validation that Amazon API always returns a buyerId
* Changed Sandbox config to be available at store view scope
* Fixed admin stylesheets for non-US locale
* Fixed issue with one Amazon account logging into multiple stores (thanks @flaviy!)
* Fixed race condition that could happen when re-drawing the button

## 5.4.0
* Fixed credential validation when inheriting from parent scope
* Fixed issue to properly handle when Amazon Pay returns empty buyer ID
* Fixed issue with using Alexa notifications and custom carriers
* Fixed issue where a quote could be submitted to Magento multiple times

## 5.3.0
* Support for OneStepCheckout v1.2.047+
* Added sort order to payment method config
* Changed the REST requests to pass in the Amazon Checkout Session ID instead of the cart ID
* Fixed bug where multiple url parameters would cause reloading in checkout
* Fixed bug with the way serializer was called in Alexa notification processing
* Fixed incorrect exception messaging in Alexa notification (thanks @dmitriyklyuzov!)
* Removed quote to Amazon Session mapping table
* Updated how javascript customizations are implemented
* Updated the cart and success redirect behavior to be configurable

## 5.2.0
* Added Sign in with Amazon to the authentication modal
* Fixed bug where pressing enter on a text input config field would open the file selector for Amazon Private Key
* Fixed usage of a php8 str_contains so that installations that don't have the Symfony polyfill will still work correctly
* Fixed issue that crawlers could trigger by hitting the login/checkout path without an Amazon checkout session
* Modified Amazon Pay button rendering so that it will be triggered by customer data loading after the Amazon javascript runs
* Updated MFTF tests to handle authentication popup that happens in desktop view now
* Updated composer.json requires to specify a few additional dependencies that are used

## 5.1.0
* General availability release
* Added tests for refund, multi auth refund, and multi auth with capture initiated
* Added Japanese translations and updates translations for other languages
* Change to use the button page URL as the redirect back when cancelling the session.
* Fixed bug with updating configuration without changing the private key.
* Fixed customer data not getting cleared when getting signed in via Amazon Pay checkout
* Replaced PHP8 only function being used for a more compatible one.
* Updated Alexa feature name
* Updated private key field to also allow usage of a .pem file.
* Updated the platform_id for the new module version

## 5.0.1
* Removed reliance on legacy config value being set.

## 5.0.0
* Beta release, replacing all versions that were included as part of the "Vendor Bundled Extension" (VBE) program in previous Magento releases.
* Added input validation and test upon saving for credentials.
* Changed calling `closeChargePermission` instead of `cancelCharge` when voiding an order.
* Changed the button to create the session directly instead of through Magento.
* Fixed creating a credit memo against a split capture invoice.
* Fixed loading correct config when switching store view before a cart is initiated.
* Fixed product page button hover and tooltip button placement.
* Removed redirect to cart on login if the customer has products in cart.
