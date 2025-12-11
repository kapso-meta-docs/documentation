
# WhatsApp Business Cloud API - Phone Number Registration

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/phone-number-registration/v23.0.md/)

Version

v23.0

API for registering WhatsApp Business phone numbers with the Cloud API platform.

This endpoint allows businesses to register their phone numbers for WhatsApp Business messaging,

enabling two-step verification and activating the phone number for business communications.

## Base URL

| https://graph.facebook.com |

## Endpoints

| POST | [/{Version}/{Phone-Number-ID}/register](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/phone-number-registration#post-version-phone-number-id-register) |

* * *

## POST /{Version}/{Phone-Number-ID}/register

Register a WhatsApp Business phone number for messaging capabilities and enable

two-step verification. This is a required step before sending messages through

the WhatsApp Business Cloud API.

Registration Process:

Phone number must be in UNVERIFIED status

Provide a 6-digit PIN for two-step verification

Optionally provide backup data for account migration

Registration activates messaging capabilities

Migration Support:

For migrating from on-premises WhatsApp Business API, include backup data

with password and encrypted account information.

Rate Limiting:

Registration attempts are rate-limited to prevent abuse. Standard Graph API

rate limits apply with additional restrictions for registration endpoints.

Security Requirements:

Two-step verification is mandatory for all registered numbers

PIN must be securely stored and managed by the business

Registration enables webhook delivery and message sending capabilities

### Request Syntax

**POST**/{Version}/{Phone-Number-ID}/register

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/register' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "pin": "123456"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "successful_registration": {
    "summary": "Successful registration",
    "value": {
      "success": true
    }
  }
}
```

Header Parameters

* * *

User-Agentstring

The user agent string identifying the client software making the request.

Authorizationstring·required

Bearer token for API authentication. This should be a valid access token obtained through the appropriate OAuth flow or system user token.

Path Parameters

* * *

Versionstring·required

Graph API version to use for this request. Determines the API behavior and available features.

Phone-Number-IDstring·required

The ID of the phone number to register. This ID is provided when the phone number

is added to your WhatsApp Business Account and can be found in WhatsApp Manager.

Request BodyRequired

* * *

Registration request payload with PIN and optional migration data

Content Type: application/json

Schema: WhatsAppBusinessPhoneNumberRegistrationRequest

Show child attributes

* * *

WhatsAppBusinessPhoneNumberRegistrationRequest

* * *

messaging_product"whatsapp"·required

Must be 'whatsapp' to indicate WhatsApp Business messaging product

* * *

pinstring·required

6-digit PIN for two-step verification setup

* * *

backupWhatsAppBusinessAccountBackup

Backup data for migrating existing WhatsApp Business accounts

Show child attributes

* * *

passwordstring

Backup password for account migration

* * *

datastring

Encrypted backup data for account migration

* * *

data_localization_regionWhatsAppDataLocalizationRegion

Data localization region for message storage (deprecated in v21+)

* * *

meta_store_retention_minutesinteger \[min: 60, max: 60\]

Message retention period in minutes (deprecated in v21+)

Responses

* * *

Register a WhatsApp Business phone number for messaging capabilities and enable

two-step verification. This is a required step before sending messages through

the WhatsApp Business Cloud API.

Registration Process:

Phone number must be in UNVERIFIED status

Provide a 6-digit PIN for two-step verification

Optionally provide backup data for account migration

Registration activates messaging capabilities

Migration Support:

For migrating from on-premises WhatsApp Business API, include backup data

with password and encrypted account information.

Rate Limiting:

Registration attempts are rate-limited to prevent abuse. Standard Graph API

rate limits apply with additional restrictions for registration endpoints.

Security Requirements:

Two-step verification is mandatory for all registered numbers

PIN must be securely stored and managed by the business

Registration enables webhook delivery and message sending capabilities

200

Successfully registered WhatsApp Business phone number

Content Type: application/json

Schema: WhatsAppBusinessPhoneNumberRegistrationResponse

Show child attributes

* * *

WhatsAppBusinessPhoneNumberRegistrationResponse

* * *

successboolean·required

Indicates whether the registration was successful

400

Bad Request - Invalid parameters or malformed request

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

401

Unauthorized - Invalid or missing access token

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

403

Forbidden - Insufficient permissions or access denied

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

404

Not Found - Phone number ID does not exist or is not accessible

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

422

Unprocessable Entity - Phone number cannot be registered in current state

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

429

Too Many Requests - Rate limit exceeded

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

500

Internal Server Error - Unexpected server error

Content Type: application/json

Schema: GraphAPIError

Show child attributes

* * *

GraphAPIError

* * *

errorobject·required

Show child attributes

* * *

messagestring·required

Human-readable error message

* * *

typestring·required

Error category type

* * *

codeinteger·required

Numeric error code

* * *

error_subcodeinteger

More specific error subcode when available

* * *

fbtrace_idstring

Unique identifier for debugging and support requests with Meta

* * *

is_transientboolean

Indicates whether this error is temporary and the request should be retried

* * *

error_user_titlestring

User-friendly error title for display purposes

* * *

error_user_msgstring

User-friendly error message for display purposes

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/register' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "pin": "123456"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "successful_registration": {
    "summary": "Successful registration",
    "value": {
      "success": true
    }
  }
}
```

## Authentication

| **Scheme** | **Type** | **Location** |
| bearerAuth | HTTP Bearer | Header: Authorization |

### Usage Examples

bearerAuth:

Include Authorization: Bearer your-token-here in request headers

### Global Authentication Requirements

All endpoints require:

bearerAuth

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

* * *