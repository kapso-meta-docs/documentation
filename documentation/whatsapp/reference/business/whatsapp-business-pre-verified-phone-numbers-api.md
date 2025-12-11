
# WhatsApp Business Pre-Verified Phone Numbers API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/whatsapp-business-pre-verified-phone-numbers-api/v23.0.md/)

Version

v23.0

API for retrieving pre-verified phone numbers associated with a WhatsApp Business Account.

This endpoint allows businesses to retrieve information about pre-verified phone numbers

that are available for use with their WhatsApp Business Account.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Business-ID}/preverified_numbers](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/whatsapp-business-pre-verified-phone-numbers-api#get-version-business-id-preverified-numbers) |

* * *

## GET /{Version}/{Business-ID}/preverified_numbers

Retrieve pre-verified phone numbers available for use with the specified business.

This endpoint provides information about phone numbers that have been pre-verified

and are ready for immediate use with WhatsApp Business messaging operations.

Use Cases:

Retrieve available pre-verified phone numbers for business messaging setup

Check verification status and availability of phone numbers

Monitor pre-verified phone number inventory

Validate phone number options before WhatsApp Business Account configuration

Facilitate quick business messaging setup with pre-verified numbers

Filtering and Pagination:

Results can be filtered by verification status, availability, and country

Cursor-based pagination is supported for large result sets

Default page size is 25 items, maximum is 100 items per page

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Phone number information can be cached for short periods, but availability status

may change frequently. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{Business-ID}/preverified_numbers

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/preverified_numbers' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "basic_response": {
    "summary": "Basic response with pre-verified phone numbers",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "display_phone_number": "+1 (555) 123-4567",\
          "country_prefix": 1,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "created_time": "2024-01-15T10:30:00Z",\
          "last_updated": "2024-01-20T14:45:00Z",\
          "supported_features": [\
            "MESSAGING",\
            "BUSINESS_PROFILE",\
            "WEBHOOKS"\
          ],\
          "country_code": "US",\
          "region": "North America"\
        },\
        {\
          "id": "2345678901234567",\
          "display_phone_number": "+44 20 1234 5678",\
          "country_prefix": 44,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "created_time": "2024-01-10T08:15:00Z",\
          "last_updated": "2024-01-18T16:20:00Z",\
          "supported_features": [\
            "MESSAGING",\
            "TEMPLATES",\
            "ANALYTICS"\
          ],\
          "country_code": "GB",\
          "region": "Europe"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "QVFIUjJ5WjBpMGpJWXprYzVYaVhabW9PVks4ZD0"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/preverified_numbers?after=QVFIUjJ5WjBpMGpJWXprYzVYaVhabW9PVks4ZD0"
      }
    }
  },
  "filtered_response": {
    "summary": "Filtered response by country and status",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "display_phone_number": "+1 (555) 123-4567",\
          "country_prefix": 1,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "country_code": "US",\
          "region": "North America"\
        }\
      ],
      "paging": {
        "cursors": {}
      }
    }
  },
  "empty_response": {
    "summary": "Empty response when no phone numbers are available",
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

Business-IDstring·required

Your Business ID for which to retrieve pre-verified phone numbers.

This ID can be found in your Meta Business Manager or through business management APIs.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id, display_phone_number, verification_status).

Available fields: id, display_phone_number, country_prefix, verification_status,

availability_status, created_time, last_updated, supported_features, country_code, region

limitinteger \[min: 1, max: 100\]

Maximum number of phone numbers to return per page. Default is 25, maximum is 100.

afterstring

Cursor for pagination. Use this to retrieve the next page of results.

This value is provided in the 'paging' object of previous responses.

beforestring

Cursor for pagination. Use this to retrieve the previous page of results.

This value is provided in the 'paging' object of previous responses.

verification_statusPhoneNumberVerificationStatus

Filter results by verification status. Only phone numbers with the specified

verification status will be returned.

availability_statusPhoneNumberAvailabilityStatus

Filter results by availability status. Only phone numbers with the specified

availability status will be returned.

country_codestring

Filter results by country code. Only phone numbers from the specified

country will be returned. Use ISO 3166-1 alpha-2 country codes.

Responses

* * *

Retrieve pre-verified phone numbers available for use with the specified business.

This endpoint provides information about phone numbers that have been pre-verified

and are ready for immediate use with WhatsApp Business messaging operations.

Use Cases:

Retrieve available pre-verified phone numbers for business messaging setup

Check verification status and availability of phone numbers

Monitor pre-verified phone number inventory

Validate phone number options before WhatsApp Business Account configuration

Facilitate quick business messaging setup with pre-verified numbers

Filtering and Pagination:

Results can be filtered by verification status, availability, and country

Cursor-based pagination is supported for large result sets

Default page size is 25 items, maximum is 100 items per page

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Phone number information can be cached for short periods, but availability status

may change frequently. Implement appropriate cache invalidation strategies.

200

Successfully retrieved pre-verified phone numbers

Content Type: application/json

Schema: PreVerifiedPhoneNumbersResponse

Show child attributes

* * *

PreVerifiedPhoneNumbersResponse

* * *

dataarray of PreVerifiedPhoneNumber·required

List of pre-verified phone numbers

Show child attributes

* * *

data\[\]PreVerifiedPhoneNumber

Pre-verified phone number details and status information

Show child attributes

* * *

idstring·required

Unique identifier for the pre-verified phone number

* * *

display_phone_numberstring·required

Formatted display version of the phone number

* * *

country_prefixinteger \[min: 1, max: 999\]

Country code prefix for the phone number

* * *

verification_statusPhoneNumberVerificationStatus

Current verification status of the pre-verified phone number

* * *

availability_statusPhoneNumberAvailabilityStatus

Current availability status of the pre-verified phone number

* * *

created_timestring (date-time)

Timestamp when the phone number was pre-verified

* * *

last_updatedstring (date-time)

Timestamp when the phone number information was last updated

* * *

supported_featuresarray of WhatsAppBusinessFeature

List of WhatsApp Business features supported by this phone number

Show child attributes

* * *

supported_features\[\]WhatsAppBusinessFeature

WhatsApp Business features supported by the phone number

* * *

country_codestring

ISO 3166-1 alpha-2 country code for the phone number

* * *

regionstring

Geographic region or area for the phone number

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

Not Found - Business does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/preverified_numbers' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "basic_response": {
    "summary": "Basic response with pre-verified phone numbers",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "display_phone_number": "+1 (555) 123-4567",\
          "country_prefix": 1,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "created_time": "2024-01-15T10:30:00Z",\
          "last_updated": "2024-01-20T14:45:00Z",\
          "supported_features": [\
            "MESSAGING",\
            "BUSINESS_PROFILE",\
            "WEBHOOKS"\
          ],\
          "country_code": "US",\
          "region": "North America"\
        },\
        {\
          "id": "2345678901234567",\
          "display_phone_number": "+44 20 1234 5678",\
          "country_prefix": 44,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "created_time": "2024-01-10T08:15:00Z",\
          "last_updated": "2024-01-18T16:20:00Z",\
          "supported_features": [\
            "MESSAGING",\
            "TEMPLATES",\
            "ANALYTICS"\
          ],\
          "country_code": "GB",\
          "region": "Europe"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "QVFIUjJ5WjBpMGpJWXprYzVYaVhabW9PVks4ZD0"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/preverified_numbers?after=QVFIUjJ5WjBpMGpJWXprYzVYaVhabW9PVks4ZD0"
      }
    }
  },
  "filtered_response": {
    "summary": "Filtered response by country and status",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "display_phone_number": "+1 (555) 123-4567",\
          "country_prefix": 1,\
          "verification_status": "VERIFIED",\
          "availability_status": "AVAILABLE",\
          "country_code": "US",\
          "region": "North America"\
        }\
      ],
      "paging": {
        "cursors": {}
      }
    }
  },
  "empty_response": {
    "summary": "Empty response when no phone numbers are available",
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