
# WhatsApp Business Pre-Verified Phone Number Partners API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-pre-verified-phone-number/whatsapp-business-pre-verified-phone-number-partners-api/v23.0.md/)

Version

v23.0

API for retrieving partner businesses associated with a WhatsApp Business Pre-Verified Phone Number.

This endpoint allows authorized applications to retrieve the list of partner businesses

that have been granted access to a specific pre-verified phone number.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Pre-Verified-Phone-Number-ID}/partners](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-pre-verified-phone-number/whatsapp-business-pre-verified-phone-number-partners-api#get-version-pre-verified-phone-number-id-partners) |

* * *

## GET /{Version}/{Pre-Verified-Phone-Number-ID}/partners

Retrieve the list of partner businesses that have been granted access to a specific

WhatsApp Business Pre-Verified Phone Number.

Use Cases:

Monitor partner business relationships and access permissions

Verify which businesses have access to shared pre-verified phone numbers

Retrieve partner business information for operational purposes

Validate partnership configurations before business operations

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Partner information can be cached for moderate periods, but partnership relationships

may change. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{Pre-Verified-Phone-Number-ID}/partners

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Pre-Verified-Phone-Number-ID}/partners' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_partners": {
    "summary": "Multiple partner businesses with full details",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Partner Business Solutions Inc",\
          "verification_status": "verified",\
          "created_time": "2023-01-15T10:30:00Z",\
          "updated_time": "2023-06-20T14:45:30Z",\
          "primary_page": "9876543210987654",\
          "timezone_id": 1,\
          "two_factor_type": "admin_required"\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Global Commerce Partners LLC",\
          "verification_status": "verified",\
          "created_time": "2023-03-10T08:15:00Z",\
          "updated_time": "2023-07-05T16:20:45Z",\
          "primary_page": "8765432109876543",\
          "timezone_id": 1,\
          "two_factor_type": "admin_required"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/partners?after=MTAxNTExOTQ1MjAwNzI5NDE%3D"
      }
    }
  },
  "single_partner": {
    "summary": "Single partner business with minimal details",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Partner Business Solutions Inc"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        }
      }
    }
  },
  "empty_partners": {
    "summary": "No partner businesses found",
    "value": {
      "data": [],
      "paging": {
        "cursors": {}
      }
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

Pre-Verified-Phone-Number-IDstring·required

Your Pre-Verified Phone Number ID. This ID is provided when the pre-verified phone number

is created and can be found in your WhatsApp Business Account management interface.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id, name). Available fields: id, name, created_time,

updated_time, verification_status, primary_page, timezone_id, two_factor_type

limitinteger \[min: 1, max: 100\]

Maximum number of partner businesses to return per page. Default is 25, maximum is 100.

afterstring

Cursor for pagination. Use the 'after' cursor from a previous response to get the next page.

beforestring

Cursor for pagination. Use the 'before' cursor from a previous response to get the previous page.

Responses

* * *

Retrieve the list of partner businesses that have been granted access to a specific

WhatsApp Business Pre-Verified Phone Number.

Use Cases:

Monitor partner business relationships and access permissions

Verify which businesses have access to shared pre-verified phone numbers

Retrieve partner business information for operational purposes

Validate partnership configurations before business operations

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Partner information can be cached for moderate periods, but partnership relationships

may change. Implement appropriate cache invalidation strategies.

200

Successfully retrieved partner businesses for the pre-verified phone number

Content Type: application/json

Schema: WhatsAppBusinessPreVerifiedPhoneNumberPartnersResponse

Show child attributes

* * *

WhatsAppBusinessPreVerifiedPhoneNumberPartnersResponse

* * *

dataarray of BusinessPartner·required

List of partner businesses with access to the pre-verified phone number

Show child attributes

* * *

data\[\]BusinessPartner

Business entity that has partner access to the pre-verified phone number

Show child attributes

* * *

idstring·required

Unique identifier for the partner business

* * *

namestring·required

Name of the partner business

* * *

created_timestring (date-time)

ISO 8601 timestamp when the business was created

* * *

updated_timestring (date-time)

ISO 8601 timestamp when the business was last updated

* * *

verification_statusOne of "not_verified", "pending", "verified"

Business verification status

* * *

primary_pagestring

Primary Facebook Page ID associated with the business

* * *

timezone_idinteger

Timezone identifier for the business location

* * *

two_factor_typeOne of "none", "admin_required"

Two-factor authentication method configured for the business

* * *

pagingCursorPaging

Cursor-based pagination information

Show child attributes

* * *

cursorsobject

Show child attributes

* * *

beforestring

Cursor pointing to the start of the page of data that has been returned

* * *

afterstring

Cursor pointing to the end of the page of data that has been returned

* * *

nextstring

Graph API endpoint URL for the next page of results

* * *

previousstring

Graph API endpoint URL for the previous page of results

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

Not Found - Pre-Verified Phone Number ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{Pre-Verified-Phone-Number-ID}/partners' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_partners": {
    "summary": "Multiple partner businesses with full details",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Partner Business Solutions Inc",\
          "verification_status": "verified",\
          "created_time": "2023-01-15T10:30:00Z",\
          "updated_time": "2023-06-20T14:45:30Z",\
          "primary_page": "9876543210987654",\
          "timezone_id": 1,\
          "two_factor_type": "admin_required"\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Global Commerce Partners LLC",\
          "verification_status": "verified",\
          "created_time": "2023-03-10T08:15:00Z",\
          "updated_time": "2023-07-05T16:20:45Z",\
          "primary_page": "8765432109876543",\
          "timezone_id": 1,\
          "two_factor_type": "admin_required"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/partners?after=MTAxNTExOTQ1MjAwNzI5NDE%3D"
      }
    }
  },
  "single_partner": {
    "summary": "Single partner business with minimal details",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Partner Business Solutions Inc"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        }
      }
    }
  },
  "empty_partners": {
    "summary": "No partner businesses found",
    "value": {
      "data": [],
      "paging": {
        "cursors": {}
      }
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