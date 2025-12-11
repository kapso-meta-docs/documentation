
# WhatsApp Business Management - Add Phone Numbers API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/add-phone-numbers-api/v23.0.md/)

Version

v23.0

API for adding phone numbers to a WhatsApp Business Account.

This endpoint allows businesses to add phone numbers to their WhatsApp Business Account

for messaging purposes.

## Base URL

| https://graph.facebook.com |

## Endpoints

| POST | [/{Version}/{Business-ID}/add_phone_numbers](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/add-phone-numbers-api#post-version-business-id-add-phone-numbers) |

* * *

## POST /{Version}/{Business-ID}/add_phone_numbers

Add a preverified phone number to a WhatsApp Business Account. This endpoint is used by

Partners to create a pool of Partner owned numbers that end clients

can purchase.

Use Cases:

Add new phone numbers to scale messaging operations

Set up phone numbers for different business locations

Manage phone number inventory for business messaging

Configure phone numbers for specific messaging workflows

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Phone Number Requirements:

Must be in E.164 format (e.g., +1234567890)

Must not be already registered to another WhatsApp Business Account

Must be capable of receiving SMS for verification

Must comply with WhatsApp's business messaging policies

### Request Syntax

**POST**/{Version}/{Business-ID}/add_phone_numbers

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/add_phone_numbers' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "phone_number": "+1234567890"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "success": {
    "summary": "Phone number successfully added",
    "value": {
      "id": "1234567890123456"
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

Business-IDstring·required

Your WhatsApp Business Account ID. This ID can be found in your Business Manager

or through business management APIs.

Request BodyRequired

* * *

Phone number to add to the business account

Content Type: application/json

Schema: AddPhoneNumbersRequest

Show child attributes

* * *

AddPhoneNumbersRequest

* * *

phone_numberstring·required

Phone number to add to the business account. Accepts E.164 format or formatted numbers

with spaces, hyphens, and parentheses (e.g., +1234567890, +1 (631) 555-1000, +1-631-555-1000).

The phone number will be normalized and validated by the endpoint.

Responses

* * *

Add a preverified phone number to a WhatsApp Business Account. This endpoint is used by

Partners to create a pool of Partner owned numbers that end clients

can purchase.

Use Cases:

Add new phone numbers to scale messaging operations

Set up phone numbers for different business locations

Manage phone number inventory for business messaging

Configure phone numbers for specific messaging workflows

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Phone Number Requirements:

Must be in E.164 format (e.g., +1234567890)

Must not be already registered to another WhatsApp Business Account

Must be capable of receiving SMS for verification

Must comply with WhatsApp's business messaging policies

200

Phone number successfully added

Content Type: application/json

Schema: AddPhoneNumbersResponse

Show child attributes

* * *

AddPhoneNumbersResponse

* * *

idstring·required

Unique identifier for the preverified phone number entity that was created

400

Bad Request - Invalid parameters, malformed request, or phone number already registered

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

Not Found - Business ID does not exist or is not accessible

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
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/add_phone_numbers' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "phone_number": "+1234567890"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "success": {
    "summary": "Phone number successfully added",
    "value": {
      "id": "1234567890123456"
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