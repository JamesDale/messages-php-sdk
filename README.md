# MessageMedia Messages PHP SDK
[![Travis Build Status](https://api.travis-ci.org/messagemedia/messages-php-sdk.svg?branch=master)](https://travis-ci.org/messagemedia/messages-php-sdk)
[![composer](https://img.shields.io/badge/composer-v1.1.2-orange.svg)](https://packagist.org/packages/messagemedia/messages-sdk)

The MessageMedia Messages API provides a number of endpoints for building powerful two-way messaging applications.

## ⭐️ Installing via Composer
Run the Composer command to install the latest stable version of the Messages SDK:
```
composer require messagemedia/messages-sdk
```

## 🎬 Get Started
It's easy to get started. Simply enter the API Key and secret you obtained from the [MessageMedia Developers Portal](https://developers.messagemedia.com) into the code snippet below and a mobile number you wish to send to.

### 🚀 Send an SMS
* Destination numbers (`destination_number`) should be in the [E.164](http://en.wikipedia.org/wiki/E.164) format. For example, `+61491570156`.
```php
<?php
require_once "vendor/autoload.php";

use MessageMediaMessagesLib\MessageMediaMessagesClient;
use MessageMediaMessagesLib\APIHelper;

$basicAuthUserName = 'YOUR_API_KEY'; // The username to use with basic authentication
$basicAuthPassword = 'YOUR_API_SECRET'; // The password to use with basic authentication

$client = new MessageMediaMessagesLib\MessageMediaMessagesClient($basicAuthUserName, $basicAuthPassword);

$messages = $client->getMessages();

$bodyValue = '{
   "messages":[
      {
         "content":"My first message",
         "destination_number":"YOUR_MOBILE_NUMBER"
      }
   ]
}';


$body = MessageMediaMessagesLib\APIHelper::deserialize($bodyValue);

$result = $messages->createSendMessages($body);
?>
```

### 🕓 Get Status of a Message
You can get a messsage ID from a sent message by looking at the `message_id` from the response of the above example.
```php
<?php
require_once "vendor/autoload.php";

use MessageMediaMessagesLib\MessageMediaMessagesClient;

$basicAuthUserName = 'YOUR_API_KEY'; // The username to use with basic authentication
$basicAuthPassword = 'YOUR_API_SECRET'; // The password to use with basic authentication

$client = new MessageMediaMessagesLib\MessageMediaMessagesClient($basicAuthUserName, $basicAuthPassword);

$messages = $client->getMessages();

$messageId = 'YOUR_MESSAGE_ID'; // The message id for the message you wish to get the status for

$result = $messages->getMessageStatus($messageId);
print_r($result);
?>
```

### 💬 Get replies to a message
You can check for replies that are sent to your messages
```php
<?php
require_once "vendor/autoload.php";

use MessageMediaMessagesLib\MessageMediaMessagesClient;

$basicAuthUserName = 'YOUR_API_KEY'; // The username to use with basic authentication
$basicAuthPassword = 'YOUR_API_SECRET'; // The password to use with basic authentication

$client = new MessageMediaMessagesLib\MessageMediaMessagesClient($basicAuthUserName, $basicAuthPassword);

$replies = $client->getReplies();


$result = $replies->getCheckReplies();
print_r($result);
?>
```

### ✅ Check Delivery Reports
This endpoint allows you to check for delivery reports to inbound and outbound messages.
```php
<?php
require_once "vendor/autoload.php";

use MessageMediaMessagesLib\MessageMediaMessagesClient;

$basicAuthUserName = 'YOUR_API_KEY'; // The username to use with basic authentication
$basicAuthPassword = 'YOUR_API_SECRET'; // The password to use with basic authentication

$client = new MessageMediaMessagesLib\MessageMediaMessagesClient($basicAuthUserName, $basicAuthPassword);

$deliveryReports = $client->getDeliveryReports();


$result = $deliveryReports->getCheckDeliveryReports();
print_r($result);
?>
```

## 📕 Documentation
The PHP SDK Documentation can be viewed [here](DOCUMENTATION.md)

## 😕 Got Stuck?
Please contact developer support at developers@messagemedia.com or check out the developer portal at [developers.messagemedia.com](https://developers.messagemedia.com/)
