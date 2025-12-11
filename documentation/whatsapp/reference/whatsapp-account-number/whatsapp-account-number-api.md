
# WhatsApp Business API - WhatsApp Account Number API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-account-number/whatsapp-account-number-api/v23.0.md/)

Version

v23.0

API for retrieving WhatsApp Account Number details and configuration information.

This endpoint allows businesses to retrieve comprehensive information about their

WhatsApp Account Numbers, including status, verification details, and configuration settings.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{WhatsApp-Account-Number-ID}](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-account-number/whatsapp-account-number-api#get-version-whatsapp-account-number-id) |

* * *

## GET /{Version}/{WhatsApp-Account-Number-ID}

Retrieve comprehensive details about a WhatsApp Account Number, including its current status,

verification information, quality rating, and configuration settings.

Use Cases:

Monitor account number status and quality rating

Verify account number configuration before messaging operations

Check verification and approval status

Retrieve display name and business profile information

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Account number details can be cached for short periods, but status information may change

frequently. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{WhatsApp-Account-Number-ID}

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Account-Number-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "verified_account_number": {
    "summary": "Verified account number with full details",
    "value": {
      "id": "1234567890123456",
      "display_phone_number": "+1 631-555-5555",
      "verified_name": "Jasper's Market",
      "status": "CONNECTED",
      "quality_rating": "GREEN",
      "country_code": "US",
      "country_dial_code": "1",
      "code_verification_status": "VERIFIED",
      "name_status": "APPROVED",
      "messaging_limit_tier": "TIER_1K",
      "account_mode": "LIVE",
      "is_official_business_account": false
    }
  },
  "unverified_account_number": {
    "summary": "Unverified account number with minimal details",
    "value": {
      "id": "2345678901234567",
      "display_phone_number": "+1 555-123-4567",
      "status": "UNVERIFIED",
      "quality_rating": "NA",
      "code_verification_status": "UNVERIFIED",
      "name_status": "NONE"
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

WhatsApp-Account-Number-IDstring·required

Your WhatsApp Account Number ID. This ID represents the account number entity

and can be obtained from your WhatsApp Business Account phone numbers list.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id, display_phone_number, status).

Available fields: id, display_phone_number, verified_name, status, quality_rating,

country_code, country_dial_code, code_verification_status, name_status,

messaging_limit_tier, account_mode, certificate, is_official_business_account

Responses

* * *

Retrieve comprehensive details about a WhatsApp Account Number, including its current status,

verification information, quality rating, and configuration settings.

Use Cases:

Monitor account number status and quality rating

Verify account number configuration before messaging operations

Check verification and approval status

Retrieve display name and business profile information

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Account number details can be cached for short periods, but status information may change

frequently. Implement appropriate cache invalidation strategies.

200

Successfully retrieved WhatsApp Account Number details

Content Type: application/json

Schema: WhatsAppAccountNumber

Show child attributes

* * *

WhatsAppAccountNumber

* * *

idstring·required

Unique identifier for the WhatsApp Account Number

* * *

display_phone_numberstring·required

Phone number in international format for display purposes

* * *

verified_namestring

Business name verified for this phone number

* * *

statusWhatsAppAccountNumberStatus

Current status of the WhatsApp Account Number

* * *

quality_ratingWhatsAppPhoneNumberQualityRating

Quality rating based on message delivery and user feedback

* * *

country_codestring

ISO 3166-1 alpha-2 country code

* * *

country_dial_codestring

Country dialing code

* * *

code_verification_statusWhatsAppCodeVerificationStatus

Two-step verification status for the phone number

* * *

name_statusWhatsAppDisplayNameStatus

Status of the display name associated with the phone number

* * *

messaging_limit_tierOne of "TIER_50", "TIER_250", "TIER_1K", "TIER_10K", "TIER_100K", "TIER_UNLIMITED"

Current messaging limit tier for the account number

* * *

account_modeWhatsAppBusinessSandboxEligibility

Account mode indicating sandbox or live environment

* * *

certificatestring

Business certificate information for the account number

* * *

is_official_business_accountboolean

Whether this is an official business account

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

Not Found - Account Number ID does not exist or is not accessible

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

Unprocessable Entity - Request parameters are valid but cannot be processed

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
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Account-Number-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "verified_account_number": {
    "summary": "Verified account number with full details",
    "value": {
      "id": "1234567890123456",
      "display_phone_number": "+1 631-555-5555",
      "verified_name": "Jasper's Market",
      "status": "CONNECTED",
      "quality_rating": "GREEN",
      "country_code": "US",
      "country_dial_code": "1",
      "code_verification_status": "VERIFIED",
      "name_status": "APPROVED",
      "messaging_limit_tier": "TIER_1K",
      "account_mode": "LIVE",
      "is_official_business_account": false
    }
  },
  "unverified_account_number": {
    "summary": "Unverified account number with minimal details",
    "value": {
      "id": "2345678901234567",
      "display_phone_number": "+1 555-123-4567",
      "status": "UNVERIFIED",
      "quality_rating": "NA",
      "code_verification_status": "UNVERIFIED",
      "name_status": "NONE"
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