
# Registration

Updated: Nov 4, 2025

To use your business phone number with Cloud API you must register it. Register your business phone number in the following scenarios:

Account Creation: When you implement this API, you need to register the business phone number you want to use to send messages. We enforce setting two-step verification during account creation to add an extra layer of security to your accounts.
Name Change: In this case, your phone is already registered and you want to change your display name. To do that, you must [first file for a name change on WhatsApp Manager](https://www.facebook.com/business/help/378834799515077). Once the name is approved, you need to register your phone again under the new name.
Migrating your number from On-Premises API to Cloud API. See [Migration Exception](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/registration#migration-exception).

Before you can register your business phone number you must first [verify its ownership](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#verify).

### Migration Exception

If you are migrating a phone number from the On-Premises API to the Cloud API, there are extra steps you need to perform before registering a phone number with the Cloud API. See [Migrate From On-Premises API to Cloud API](https://developers.facebook.com/documentation/business-messaging/whatsapp/support/migrating-from-onprem-to-cloud) for the full process.

## Register a Business Phone Number

To register your verified business phone number, make a `POST` call to `PHONE_NUMBER_ID/register`. Include the parameters listed below.

| Endpoint | Authentication |
| --- | --- |
| `PHONE_NUMBER_ID/register`<br />(See [Get Phone Number ID](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#get-all-phone-numbers)) | Solution Partners must authenticate themselves with an access token with the `whatsapp_business_management` and `whatsapp_business_messaging` permissions. |

### Limitations

Requests to the registration endpoint are limited to 10 requests per business number in a 72 hour moving window.

When you make a registration request, we will check how many registration requests you have made to register that number in the last 72 hours. If you have already made 10 requests, the API will return error code `133016`, and the number will be prevented from being registered for the next 72 hours.

### Parameters

| Name | Description |
| --- | --- |
| `messaging_product` | **Required.**<br />Messaging service used. Set this to `"whatsapp"`. |
| `pin` | **Required.**<br />If your verified business phone number already has two-step verification enabled, set this value to your number’s 6-digit two-step verification PIN. If you cannot recall your PIN, you can change it. See [Two-step verification](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#two-step-verification).<br />If your verified business phone number does not have two-step verification enabled, set this value to a 6-digit number. This will be the newly verified business phone number’s two-step verification PIN. |
| `data_localization_region` | **Optional.**<br />If included, enables [local storage](https://developers.facebook.com/documentation/business-messaging/whatsapp/local-storage) on the business phone number. Value must be a 2-letter ISO 3166 country code (e.g. `IN`) indicating the country where you want data-at-rest to be stored.<br />Supported values:<br />**APAC**<br />Australia: `AU`<br />Indonesia: `ID`<br />India: `IN`<br />Japan: `JP`<br />Singapore: `SG`<br />South Korea: `KR`<br />**Europe**<br />EU (Germany): `DE`<br />Switzerland: `CH`<br />United Kingdom: `GB`<br />**LATAM**<br />Brazil: `BR`<br />**MEA**<br />Bahrain: `BH`<br />South Africa: `ZA`<br />United Arab Emirates: `AE`<br />**NORAM**<br />Canada: `CA`<br />Once enabled, cannot be disabled or changed directly. Instead, you must [deregister](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/registration#deregister) the number and register it again without this parameter (to disable), or include the parameter with the new country code (to change).<br />To enable local storage on a number that has already been registered, you must deregister the number, then register it again and include this parameter. |

### Example Request without Local Storage

```
curl 'https://graph.facebook.com/v24.0/106540352242922/register ' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "212834"
}
```

### Example Request with Local Storage

```
curl 'https://graph.facebook.com/v24.0/106540352242922/register ' \
-H 'Content-Type: application/json' \
-H 'Authorization: Bearer EAAJB...' \
-d '
{
  "messaging_product": "whatsapp",
  "pin": "212834",
  "data_localization_region": "CH"
}
```

All API calls require authentication with access tokens.

Developers can authenticate their API calls with the access token generated in the **App Dashboard** \> **WhatsApp** \> **API Setup**.

Solution Partners must authenticate themselves with an access token with the `whatsapp_business_messaging` and `whatsapp_business_management` permissions. See [System User Access Tokens](https://developers.facebook.com/documentation/business-messaging/whatsapp/access-tokens#system-user-access-tokens) for information.

## Deregister a Business Phone Number

Deregistering a business phone number makes it no longer usable with Cloud API and disables [local storage](https://developers.facebook.com/documentation/business-messaging/whatsapp/local-storage) on the number, if it had been enabled.

To deregister a business phone number, make a `POST` call to `PHONE_NUMBER_ID/deregister`:

| Endpoint | Authentication |
| --- | --- |
| `PHONE_NUMBER_ID/deregister`<br />(See [Get Phone Number ID](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#get-all-phone-numbers)) | Solution Partners must authenticate themselves with an access token with the `whatsapp_business_management` and `whatsapp_business_messaging` permissions. |

### Limitations

This endpoint cannot be used to deregister a business phone number that is in use with [both Cloud API and the WhatsApp Business app](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users).
Deregistration does not delete a number or its message history. To delete a number and its history, see [Delete Phone Number from a WABA](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#deleting-business-phone-numbers).
Requests to the deregistration endpoint are limited to 10 requests per business number in a 72-hour moving window. If you exceed this amount, the API will return error code `133016`, and the business phone number will be prevented from being deregistered for the next 72 hours.

### Example

Sample Request:

```
curl -X POST \
 'https://graph.facebook.com/v24.0/FROM_PHONE_NUMBER_ID/deregister' \
 -H 'Authorization: Bearer ACCESS_TOKEN'
```

A successful response looks like:

```
{
  "success": true
}
```

## See Also

[Resetting your PIN](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#changing-your-pin-via-whatsapp-manager)
[Cloud API Local Storage](https://developers.facebook.com/documentation/business-messaging/whatsapp/local-storage)

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Migration Exception

Register a Business Phone Number

Limitations

Parameters

Example Request without Local Storage

Example Request with Local Storage

Deregister a Business Phone Number

Limitations

Example

See Also

* * *