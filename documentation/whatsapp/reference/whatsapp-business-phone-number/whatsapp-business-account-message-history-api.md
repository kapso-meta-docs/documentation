
# WhatsApp Business Account Message History API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/whatsapp-business-account-message-history-api/v23.0.md/)

Version

v23.0

API for retrieving WhatsApp Business Account message history and delivery status information.

This endpoint allows businesses to retrieve comprehensive message history for their

WhatsApp Business Account phone numbers, including message delivery status events,

timestamps, and webhook update states.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Phone-Number-ID}/message_history](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/whatsapp-business-account-message-history-api#get-version-phone-number-id-message-history) |

* * *

## GET /{Version}/{Phone-Number-ID}/message_history

Retrieve paginated message history for a WhatsApp Business Account phone number,

including delivery status events, timestamps, and webhook update information.

Use Cases:

Track message delivery status and events

Monitor webhook delivery and update states

Retrieve historical message delivery information

Debug message delivery issues and webhook failures

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Message history data can be cached for moderate periods, but delivery status events

may change frequently. Implement appropriate cache invalidation strategies.

Pagination:

This endpoint supports cursor-based pagination. Use the after and before cursors

from the response to navigate through results.

### Request Syntax

**GET**/{Version}/{Phone-Number-ID}/message_history

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/message_history' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
{
  "message_history_with_events": {
    "summary": "Message history with delivery status events",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTRGAA==",\
          "events": {\
            "data": [\
              {\
                "id": "2345678901234567",\
                "delivery_status": "SENT",\
                "timestamp": 1640995200,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              },\
              {\
                "id": "3456789012345678",\
                "delivery_status": "DELIVERED",\
                "timestamp": 1640995260,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              }\
            ]\
          }\
        },\
        {\
          "id": "4567890123456789",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTJHAA==",\
          "events": {\
            "data": [\
              {\
                "id": "5678901234567890",\
                "delivery_status": "READ",\
                "timestamp": 1640995320,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              }\
            ]\
          }\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/message_history?after=MTAxNTExOTQ1MjAwNzI5NDE="
      }
    }
  },
  "filtered_by_message_id": {
    "summary": "Message history filtered by specific message ID",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTRGAA==",\
          "events": {\
            "data": [\
              {\
                "id": "2345678901234567",\
                "delivery_status": "SENT",\
                "timestamp": 1640995200,\
                "webhook_update_state": "DELIVERED"\
              },\
              {\
                "id": "3456789012345678",\
                "delivery_status": "DELIVERED",\
                "timestamp": 1640995260,\
                "webhook_update_state": "DELIVERED"\
              },\
              {\
                "id": "4567890123456789",\
                "delivery_status": "READ",\
                "timestamp": 1640995320,\
                "webhook_update_state": "DELIVERED"\
              }\
            ]\
          }\
        }\
      ]
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

Your WhatsApp Business Account phone number ID. This ID is provided when you register

the phone number and can be found in your WhatsApp Business Manager or through phone number APIs.

Query Parameters

* * *

message_idstring

Filter results by specific WhatsApp message ID (WAMID). When provided,

only message history for this specific message will be returned.

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id, message_id).

Available fields: id, message_id, events{delivery_status,webhook_update_state,timestamp,application,webhook_uri,error_description}

limitinteger \[min: 1, max: 100\]

Maximum number of message history entries to return per page.

Default is 25, maximum is 100.

afterstring

Cursor for pagination. Use this to get the next page of results.

This value comes from the paging.cursors.after field in previous responses.

beforestring

Cursor for pagination. Use this to get the previous page of results.

This value comes from the paging.cursors.before field in previous responses.

Responses

* * *

Retrieve paginated message history for a WhatsApp Business Account phone number,

including delivery status events, timestamps, and webhook update information.

Use Cases:

Track message delivery status and events

Monitor webhook delivery and update states

Retrieve historical message delivery information

Debug message delivery issues and webhook failures

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Message history data can be cached for moderate periods, but delivery status events

may change frequently. Implement appropriate cache invalidation strategies.

Pagination:

This endpoint supports cursor-based pagination. Use the after and before cursors

from the response to navigate through results.

200

Successfully retrieved WhatsApp Business Account message history

Content Type: application/json

Schema: MessageHistoryResponse

Show child attributes

* * *

MessageHistoryResponse

* * *

dataarray of WhatsAppMessageHistory

Array of message history entries

Show child attributes

* * *

data\[\]WhatsAppMessageHistory

WhatsApp message history entry with delivery status information

Show child attributes

* * *

idstring·required

Unique identifier for the message history entry

* * *

message_idstring·required

WhatsApp message ID (WAMID) for the message

* * *

eventsobject

Message delivery status events and occurrences

Show child attributes

* * *

dataarray of MessageDeliveryStatusEvent

Array of delivery status events

Show child attributes

* * *

data\[\]MessageDeliveryStatusEvent

Message delivery status event occurrence

Show child attributes

* * *

idstring·required

Unique identifier for the delivery status event

* * *

delivery_statusWhatsAppMessageDeliveryStatus

Message delivery status

* * *

webhook_update_stateWebhookUpdateState

State of webhook update delivery

* * *

timestampinteger (int64)·required

Unix timestamp when the delivery status event occurred

* * *

applicationobject

Application information for the event

Show child attributes

* * *

idstring

Application ID that processed the event

* * *

webhook_uristring (uri)

Webhook URI where the event was delivered

* * *

error_descriptionstring

Error description if the delivery failed

* * *

pagingPaginationInfo

Pagination information for navigating through results

Show child attributes

* * *

cursorsobject

Pagination cursors for navigation

Show child attributes

* * *

beforestring

Cursor for the previous page of results

* * *

afterstring

Cursor for the next page of results

* * *

previousstring (uri)

URL for the previous page of results

* * *

nextstring (uri)

URL for the next page of results

* * *

pagingPaginationInfo

Pagination information for navigating through results

Show child attributes

* * *

cursorsobject

Pagination cursors for navigation

Show child attributes

* * *

beforestring

Cursor for the previous page of results

* * *

afterstring

Cursor for the next page of results

* * *

previousstring (uri)

URL for the previous page of results

* * *

nextstring (uri)

URL for the next page of results

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
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/message_history' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
{
  "message_history_with_events": {
    "summary": "Message history with delivery status events",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTRGAA==",\
          "events": {\
            "data": [\
              {\
                "id": "2345678901234567",\
                "delivery_status": "SENT",\
                "timestamp": 1640995200,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              },\
              {\
                "id": "3456789012345678",\
                "delivery_status": "DELIVERED",\
                "timestamp": 1640995260,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              }\
            ]\
          }\
        },\
        {\
          "id": "4567890123456789",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTJHAA==",\
          "events": {\
            "data": [\
              {\
                "id": "5678901234567890",\
                "delivery_status": "READ",\
                "timestamp": 1640995320,\
                "webhook_update_state": "DELIVERED",\
                "application": {\
                  "id": "9876543210987654"\
                },\
                "webhook_uri": "https://example.com/webhook"\
              }\
            ]\
          }\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE=",
          "before": "MAZDZD"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/message_history?after=MTAxNTExOTQ1MjAwNzI5NDE="
      }
    }
  },
  "filtered_by_message_id": {
    "summary": "Message history filtered by specific message ID",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "message_id": "wamid.HBgLMTY0NzM3Nzc3NzUVAgARGBI5QTNEQTA2RjdGMEY4RTRGAA==",\
          "events": {\
            "data": [\
              {\
                "id": "2345678901234567",\
                "delivery_status": "SENT",\
                "timestamp": 1640995200,\
                "webhook_update_state": "DELIVERED"\
              },\
              {\
                "id": "3456789012345678",\
                "delivery_status": "DELIVERED",\
                "timestamp": 1640995260,\
                "webhook_update_state": "DELIVERED"\
              },\
              {\
                "id": "4567890123456789",\
                "delivery_status": "READ",\
                "timestamp": 1640995320,\
                "webhook_update_state": "DELIVERED"\
              }\
            ]\
          }\
        }\
      ]
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