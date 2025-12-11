
# WhatsApp Business Account Solutions List API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/whatsapp-business-account-solutions-list-api/v23.0.md/)

Version

v23.0

API for retrieving Multi-Partner Solutions associated with a WhatsApp Business Account (WABA).

This endpoint allows authorized applications to retrieve a list of Multi-Partner Solutions

that are associated with a specific WhatsApp Business Account.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{WABA-ID}/solutions](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/whatsapp-business-account-solutions-list-api#get-version-waba-id-solutions) |

* * *

## GET /{Version}/{WABA-ID}/solutions

Retrieve a paginated list of Multi-Partner Solutions associated with the specified

WhatsApp Business Account. This endpoint supports field selection and cursor-based

pagination for efficient data retrieval.

Use Cases:

Discover available Multi-Partner Solutions for business onboarding

Monitor solution status and availability across your WABA

Retrieve solution ownership and permission details

Filter solutions by specific fields or status requirements

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Solution listings can be cached for short periods, but status information may change

frequently during transitions. Implement appropriate cache invalidation strategies.

Pagination:

This endpoint supports cursor-based pagination using limit, after, and before

parameters. Use the paging object in responses to navigate through result sets.

### Request Syntax

**GET**/{Version}/{WABA-ID}/solutions

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/solutions' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_solutions": {
    "summary": "Multiple solutions with different statuses",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "E-commerce Integration Solution",\
          "status": "ACTIVE",\
          "status_for_pending_request": "NONE",\
          "owner_app": {\
            "id": "9876543210987654",\
            "name": "Solution Partner App"\
          },\
          "owner_permissions": [\
            "MANAGE",\
            "DEVELOP",\
            "MANAGE_TEMPLATES",\
            "VIEW_INSIGHTS"\
          ]\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Customer Support Solution",\
          "status": "DRAFT",\
          "status_for_pending_request": "NONE"\
        }\
      ],
      "paging": {
        "cursors": {
          "before": "FAKE_CURSOR_BEFORE_123ABC",
          "after": "FAKE_CURSOR_AFTER_456DEF"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/solutions?limit=25&after=FAKE_CURSOR_AFTER_456DEF"
      }
    }
  },
  "single_solution": {
    "summary": "Single solution with minimal fields",
    "value": {
      "data": [\
        {\
          "id": "3456789012345678",\
          "name": "Analytics Integration Solution",\
          "status": "ACTIVE",\
          "status_for_pending_request": "NONE"\
        }\
      ],
      "paging": {
        "cursors": {
          "before": "FAKE_CURSOR_BEFORE_789GHI",
          "after": "FAKE_CURSOR_AFTER_789GHI"
        }
      }
    }
  },
  "empty_list": {
    "summary": "No solutions found for this WABA",
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

WABA-IDstring·required

WhatsApp Business Account ID for which to retrieve associated Multi-Partner Solutions.

This ID can be found in your WhatsApp Business Manager or through WABA management APIs.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (name, status, status_for_pending_request).

Available fields: id, name, status, status_for_pending_request, owner_app, owner_permissions

limitinteger \[min: 1, max: 100\]

Maximum number of solutions to return per page. Default is 25, maximum is 100.

afterstring

Cursor for pagination. Returns solutions after this cursor position.

Use the cursor from the previous response's paging.cursors.after field.

beforestring

Cursor for pagination. Returns solutions before this cursor position.

Use the cursor from the previous response's paging.cursors.before field.

Responses

* * *

Retrieve a paginated list of Multi-Partner Solutions associated with the specified

WhatsApp Business Account. This endpoint supports field selection and cursor-based

pagination for efficient data retrieval.

Use Cases:

Discover available Multi-Partner Solutions for business onboarding

Monitor solution status and availability across your WABA

Retrieve solution ownership and permission details

Filter solutions by specific fields or status requirements

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Solution listings can be cached for short periods, but status information may change

frequently during transitions. Implement appropriate cache invalidation strategies.

Pagination:

This endpoint supports cursor-based pagination using limit, after, and before

parameters. Use the paging object in responses to navigate through result sets.

200

Successfully retrieved Multi-Partner Solutions list

Content Type: application/json

Schema: SolutionsList

Show child attributes

* * *

SolutionsList

* * *

dataarray of WhatsAppBusinessSolution·required

Array of Multi-Partner Solutions associated with the WABA

Show child attributes

* * *

data\[\]WhatsAppBusinessSolution

Multi-Partner Solution details and configuration

Show child attributes

* * *

idstring·required

Unique identifier for the Multi-Partner Solution

* * *

namestring·required

Human-readable name of the Multi-Partner Solution

* * *

statusWhatsAppBusinessSolutionStatus

Current effective status of the Multi-Partner Solution

Show child attributes

* * *

status_for_pending_requestWhatsAppBusinessSolutionPendingStatus

Status of any pending solution status transition requests

* * *

owner_appApplicationNode

Meta application that owns the Multi-Partner Solution

Show child attributes

* * *

idstring

Unique identifier for the Meta application

* * *

namestring

Name of the Meta application

* * *

owner_permissionsarray of WhatsAppBusinessAccountPermissionTask

List of WhatsApp Business Account permissions granted to the solution owner

Show child attributes

* * *

owner_permissions\[\]WhatsAppBusinessAccountPermissionTask

Granular permission tasks for WhatsApp Business Account access

* * *

pagingPaging

Pagination information for cursor-based pagination

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

previousstring

Graph API endpoint URL for the previous page of data

* * *

nextstring

Graph API endpoint URL for the next page of data

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

Not Found - WABA ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/solutions' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_solutions": {
    "summary": "Multiple solutions with different statuses",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "E-commerce Integration Solution",\
          "status": "ACTIVE",\
          "status_for_pending_request": "NONE",\
          "owner_app": {\
            "id": "9876543210987654",\
            "name": "Solution Partner App"\
          },\
          "owner_permissions": [\
            "MANAGE",\
            "DEVELOP",\
            "MANAGE_TEMPLATES",\
            "VIEW_INSIGHTS"\
          ]\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Customer Support Solution",\
          "status": "DRAFT",\
          "status_for_pending_request": "NONE"\
        }\
      ],
      "paging": {
        "cursors": {
          "before": "FAKE_CURSOR_BEFORE_123ABC",
          "after": "FAKE_CURSOR_AFTER_456DEF"
        },
        "next": "https://graph.facebook.com/v23.0/1234567890123456/solutions?limit=25&after=FAKE_CURSOR_AFTER_456DEF"
      }
    }
  },
  "single_solution": {
    "summary": "Single solution with minimal fields",
    "value": {
      "data": [\
        {\
          "id": "3456789012345678",\
          "name": "Analytics Integration Solution",\
          "status": "ACTIVE",\
          "status_for_pending_request": "NONE"\
        }\
      ],
      "paging": {
        "cursors": {
          "before": "FAKE_CURSOR_BEFORE_789GHI",
          "after": "FAKE_CURSOR_AFTER_789GHI"
        }
      }
    }
  },
  "empty_list": {
    "summary": "No solutions found for this WABA",
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