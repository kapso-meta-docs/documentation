
# Meta Graph API - Application Connected Client Businesses

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/application/application-connected-client-businesses/v23.0.md/)

Version

v23.0

API for retrieving connected client businesses associated with a Meta application.

This endpoint allows applications to retrieve information about businesses that have

established client connections through the application. This is essential for managing

business relationships and understanding client business configurations.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Application-ID}/connected_client_businesses](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/application/application-connected-client-businesses#get-version-application-id-connected-client-businesses) |

* * *

## GET /{Version}/{Application-ID}/connected_client_businesses

Retrieve a list of client businesses connected to the specified application.

Use Cases:

Monitor application-business client relationships

Verify connected business configurations

Retrieve business connection status and details

Manage client business access and permissions

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Business connection data can be cached for moderate periods, but status information may change.

Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{Application-ID}/connected_client_businesses

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Application-ID}/connected_client_businesses' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_businesses": {
    "summary": "Multiple connected client businesses",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Example Client Business A",\
          "verification_status": "VERIFIED",\
          "business_status": "ACTIVE",\
          "created_time": "2023-01-15T10:30:00Z",\
          "updated_time": "2023-06-20T14:45:00Z"\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Example Client Business B",\
          "verification_status": "PENDING",\
          "business_status": "PENDING_APPROVAL",\
          "created_time": "2023-03-10T09:15:00Z",\
          "updated_time": "2023-03-10T09:15:00Z"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "QVFIUjNpUWpVWmRBd0Rn"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890/connected_client_businesses?after=QVFIUjNpUWpVWmRBd0Rn"
      }
    }
  },
  "single_business": {
    "summary": "Single connected client business",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Example Client Business",\
          "verification_status": "VERIFIED",\
          "business_status": "ACTIVE"\
        }\
      ]
    }
  },
  "empty_response": {
    "summary": "No connected client businesses",
    "value": {
      "data": []
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

Application-IDstring·required

Your Meta Application ID. This ID is provided when you create the application

and can be found in your App Dashboard.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id, name, verification_status, business_status).

Available fields: id, name, verification_status, business_status, created_time, updated_time

limitinteger \[min: 1, max: 100\]

Maximum number of connected client businesses to return per page. Default is 25, maximum is 100.

afterstring

Cursor for pagination. Use this to get the next page of results.

beforestring

Cursor for pagination. Use this to get the previous page of results.

Responses

* * *

Retrieve a list of client businesses connected to the specified application.

Use Cases:

Monitor application-business client relationships

Verify connected business configurations

Retrieve business connection status and details

Manage client business access and permissions

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Business connection data can be cached for moderate periods, but status information may change.

Implement appropriate cache invalidation strategies.

200

Successfully retrieved connected client businesses

Content Type: application/json

Schema: ConnectedClientBusinessesResponse

Show child attributes

* * *

ConnectedClientBusinessesResponse

* * *

dataarray of ConnectedClientBusiness

Array of connected client businesses

Show child attributes

* * *

data\[\]ConnectedClientBusiness

Connected client business information and configuration

Show child attributes

* * *

idstring·required

Unique identifier for the connected client business

* * *

namestring·required

Name of the connected client business

* * *

verification_statusBusinessVerificationStatus

Verification status of the connected client business

* * *

business_statusBusinessStatus

Current status of the connected client business

* * *

created_timestring (date-time)

Timestamp when the business connection was created

* * *

updated_timestring (date-time)

Timestamp when the business connection was last updated

* * *

pagingCursorPaging

Cursor-based pagination information

Show child attributes

* * *

cursorsobject

Show child attributes

* * *

beforestring

Cursor pointing to the start of the page of data

* * *

afterstring

Cursor pointing to the end of the page of data

* * *

previousstring

URL for the previous page of results

* * *

nextstring

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

Not Found - Application ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{Application-ID}/connected_client_businesses' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_businesses": {
    "summary": "Multiple connected client businesses",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Example Client Business A",\
          "verification_status": "VERIFIED",\
          "business_status": "ACTIVE",\
          "created_time": "2023-01-15T10:30:00Z",\
          "updated_time": "2023-06-20T14:45:00Z"\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Example Client Business B",\
          "verification_status": "PENDING",\
          "business_status": "PENDING_APPROVAL",\
          "created_time": "2023-03-10T09:15:00Z",\
          "updated_time": "2023-03-10T09:15:00Z"\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "QVFIUjNpUWpVWmRBd0Rn"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890/connected_client_businesses?after=QVFIUjNpUWpVWmRBd0Rn"
      }
    }
  },
  "single_business": {
    "summary": "Single connected client business",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Example Client Business",\
          "verification_status": "VERIFIED",\
          "business_status": "ACTIVE"\
        }\
      ]
    }
  },
  "empty_response": {
    "summary": "No connected client businesses",
    "value": {
      "data": []
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