
# WhatsApp Business Account - Schedules API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/schedules-api/v23.0.md/)

Version

v23.0

API for managing WhatsApp Business Account schedules and scheduling configurations.

This endpoint allows businesses to manage scheduling functionality for their WhatsApp Business Account,

including retrieving existing schedules and creating new scheduling configurations for automated messaging,

business hours, and other time-based operations.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{WABA-ID}/schedules](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/schedules-api#get-version-waba-id-schedules) |
| POST | [/{Version}/{WABA-ID}/schedules](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/schedules-api#post-version-waba-id-schedules) |

* * *

## GET /{Version}/{WABA-ID}/schedules

Retrieve all schedules associated with a WhatsApp Business Account, including their

configuration, status, and execution details.

Use Cases:

List all schedules in a WhatsApp Business Account

Monitor schedule status and performance

Check schedule configuration and timing details

Retrieve schedule execution history and metrics

Filtering:

You can filter results using the filtering parameter with JSON-encoded filter conditions.

Supported filters include status, schedule_type, and is_active.

Sorting:

Results can be sorted by created_time or updated_time in ascending or descending order.

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Schedule data can be cached for short periods, but status information may change

frequently. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{WABA-ID}/schedules

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/schedules' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_schedules": {
    "summary": "Multiple schedules with various types",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Business Hours Schedule",\
          "status": "ACTIVE",\
          "schedule_type": "BUSINESS_HOURS",\
          "description": "Standard business operating hours",\
          "start_time": "09:00",\
          "end_time": "17:00",\
          "timezone": "America/New_York",\
          "days_of_week": [\
            "MONDAY",\
            "TUESDAY",\
            "WEDNESDAY",\
            "THURSDAY",\
            "FRIDAY"\
          ],\
          "created_time": "2024-01-15T10:30:00Z",\
          "updated_time": "2024-01-20T14:45:00Z",\
          "is_active": true,\
          "recurrence_pattern": {\
            "frequency": "WEEKLY",\
            "interval": 1\
          }\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Weekend Maintenance",\
          "status": "INACTIVE",\
          "schedule_type": "MAINTENANCE_WINDOW",\
          "description": "System maintenance window",\
          "start_time": "02:00",\
          "end_time": "04:00",\
          "timezone": "UTC",\
          "days_of_week": [\
            "SATURDAY",\
            "SUNDAY"\
          ],\
          "created_time": "2024-01-10T08:00:00Z",\
          "updated_time": "2024-01-15T12:00:00Z",\
          "is_active": false\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE="
        }
      }
    }
  },
  "single_schedule": {
    "summary": "Single schedule response",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Business Hours Schedule",\
          "status": "ACTIVE",\
          "schedule_type": "BUSINESS_HOURS",\
          "start_time": "09:00",\
          "end_time": "17:00",\
          "is_active": true\
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

WABA-IDstring·required

WhatsApp Business Account ID. This ID can be found in your WhatsApp Manager

or through the business management APIs.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned. Available fields include: id, name, status,

schedule_type, description, start_time, end_time, timezone, days_of_week,

created_time, updated_time, is_active, recurrence_pattern

filteringstring

JSON-encoded array of filter conditions. Each filter should specify field, operator, and value.

Supported fields: status, schedule_type, is_active

sortOne of "created_time.asc", "created_time.desc", "updated_time.asc", "updated_time.desc"

Sort field and direction. Format: field_name.asc or field_name.desc

Supported fields: created_time, updated_time

limitinteger \[min: 1, max: 100\]

Maximum number of schedules to return per page

afterstring

Cursor for pagination - retrieve records after this cursor

beforestring

Cursor for pagination - retrieve records before this cursor

Responses

* * *

Retrieve all schedules associated with a WhatsApp Business Account, including their

configuration, status, and execution details.

Use Cases:

List all schedules in a WhatsApp Business Account

Monitor schedule status and performance

Check schedule configuration and timing details

Retrieve schedule execution history and metrics

Filtering:

You can filter results using the filtering parameter with JSON-encoded filter conditions.

Supported filters include status, schedule_type, and is_active.

Sorting:

Results can be sorted by created_time or updated_time in ascending or descending order.

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Schedule data can be cached for short periods, but status information may change

frequently. Implement appropriate cache invalidation strategies.

200

Successfully retrieved WhatsApp Business Account schedules

Content Type: application/json

Schema: WhatsAppBusinessAccountSchedulesConnection

Show child attributes

* * *

WhatsAppBusinessAccountSchedulesConnection

* * *

dataarray of WhatsAppBusinessAccountSchedule·required

Array of schedule records

Show child attributes

* * *

data\[\]WhatsAppBusinessAccountSchedule

WhatsApp Business Account schedule configuration and details

Show child attributes

* * *

idstring·required

Unique identifier for the schedule

* * *

namestring·required

Human-readable name for the schedule

* * *

statusWhatsAppScheduleStatus

Current status of the schedule

* * *

schedule_typeWhatsAppScheduleType

Type of schedule configuration

* * *

descriptionstring

Optional description of the schedule purpose

* * *

start_timestring (time)

Schedule start time in HH:MM format

* * *

end_timestring (time)

Schedule end time in HH:MM format

* * *

timezonestring

Timezone identifier for the schedule

* * *

days_of_weekarray of DayOfWeek

Days of the week when the schedule is active

Show child attributes

* * *

days_of_week\[\]DayOfWeek

Day of the week

* * *

created_timestring (date-time)

ISO 8601 timestamp when the schedule was created

* * *

updated_timestring (date-time)

ISO 8601 timestamp when the schedule was last updated

* * *

is_activeboolean

Whether the schedule is currently active

* * *

recurrence_patternRecurrencePattern

Pattern for recurring schedules

Show child attributes

* * *

frequencyOne of "DAILY", "WEEKLY", "MONTHLY", "YEARLY"

* * *

intervalinteger \[min: 1\]

Interval between recurrences

* * *

end_datestring (date)

End date for the recurrence pattern

* * *

pagingCursorPaging

Cursor-based pagination information

Show child attributes

* * *

cursorsobject

Show child attributes

* * *

beforestring

Cursor pointing to the start of the page

* * *

afterstring

Cursor pointing to the end of the page

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

Not Found - WhatsApp Business Account ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/schedules' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_schedules": {
    "summary": "Multiple schedules with various types",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Business Hours Schedule",\
          "status": "ACTIVE",\
          "schedule_type": "BUSINESS_HOURS",\
          "description": "Standard business operating hours",\
          "start_time": "09:00",\
          "end_time": "17:00",\
          "timezone": "America/New_York",\
          "days_of_week": [\
            "MONDAY",\
            "TUESDAY",\
            "WEDNESDAY",\
            "THURSDAY",\
            "FRIDAY"\
          ],\
          "created_time": "2024-01-15T10:30:00Z",\
          "updated_time": "2024-01-20T14:45:00Z",\
          "is_active": true,\
          "recurrence_pattern": {\
            "frequency": "WEEKLY",\
            "interval": 1\
          }\
        },\
        {\
          "id": "2345678901234567",\
          "name": "Weekend Maintenance",\
          "status": "INACTIVE",\
          "schedule_type": "MAINTENANCE_WINDOW",\
          "description": "System maintenance window",\
          "start_time": "02:00",\
          "end_time": "04:00",\
          "timezone": "UTC",\
          "days_of_week": [\
            "SATURDAY",\
            "SUNDAY"\
          ],\
          "created_time": "2024-01-10T08:00:00Z",\
          "updated_time": "2024-01-15T12:00:00Z",\
          "is_active": false\
        }\
      ],
      "paging": {
        "cursors": {
          "after": "MTAxNTExOTQ1MjAwNzI5NDE="
        }
      }
    }
  },
  "single_schedule": {
    "summary": "Single schedule response",
    "value": {
      "data": [\
        {\
          "id": "1234567890123456",\
          "name": "Business Hours Schedule",\
          "status": "ACTIVE",\
          "schedule_type": "BUSINESS_HOURS",\
          "start_time": "09:00",\
          "end_time": "17:00",\
          "is_active": true\
        }\
      ]
    }
  }
}
```

* * *

## POST /{Version}/{WABA-ID}/schedules

Create a new schedule configuration within a WhatsApp Business Account. This endpoint

allows businesses to set up automated scheduling for various operations such as business hours,

automated responses, and maintenance windows.

Use Cases:

Create business hours schedules for automated responses

Set up maintenance windows for system operations

Configure automated message campaigns with timing

Establish recurring schedule patterns for business operations

Prerequisites:

WhatsApp Business Account must have scheduling feature enabled

Appropriate permissions for schedule management

Valid timezone and time format specifications

Business must meet WhatsApp Business API requirements

Process Flow:

Submit schedule configuration with timing and recurrence details

System validates schedule parameters and conflicts

Schedule is created and activated based on is_active flag

Monitor schedule status through GET endpoint

Rate Limiting:

Schedule creation is subject to rate limits to prevent abuse.

Standard Graph API rate limits also apply.

Validation:

Start time must be before end time

Timezone must be valid IANA timezone identifier

Days of week must be valid if specified

Recurrence pattern must be consistent with schedule type

### Request Syntax

**POST**/{Version}/{WABA-ID}/schedules

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/schedules' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "name": "Business Hours Schedule",
  "schedule_type": "BUSINESS_HOURS",
  "description": "Standard business operating hours",
  "start_time": "09:00",
  "end_time": "17:00",
  "timezone": "America/New_York",
  "days_of_week": [\
    "MONDAY",\
    "TUESDAY",\
    "WEDNESDAY",\
    "THURSDAY",\
    "FRIDAY"\
  ],
  "is_active": true,
  "recurrence_pattern": {
    "frequency": "WEEKLY",
    "interval": 1
  }
}'
```

Select status code

200400401403404409422429500

* * *

```
\{
  "successful_creation": {
    "summary": "Schedule successfully created",
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

WABA-IDstring·required

WhatsApp Business Account ID where the schedule will be created.

This ID can be found in your WhatsApp Manager or through business management APIs.

Request BodyRequired

* * *

Content Type: application/json

Schema: ScheduleCreateRequest

Show child attributes

* * *

ScheduleCreateRequest

* * *

namestring·required

Human-readable name for the schedule

* * *

schedule_typeWhatsAppScheduleType

Type of schedule configuration

* * *

descriptionstring

Optional description of the schedule purpose

* * *

start_timestring (time)·required

Schedule start time in HH:MM format

* * *

end_timestring (time)·required

Schedule end time in HH:MM format

* * *

timezonestring

Timezone identifier for the schedule

* * *

days_of_weekarray of DayOfWeek

Days of the week when the schedule is active

Show child attributes

* * *

days_of_week\[\]DayOfWeek

Day of the week

* * *

is_activeboolean

Whether the schedule should be active upon creation

* * *

recurrence_patternRecurrencePattern

Pattern for recurring schedules

Show child attributes

* * *

frequencyOne of "DAILY", "WEEKLY", "MONTHLY", "YEARLY"

* * *

intervalinteger \[min: 1\]

Interval between recurrences

* * *

end_datestring (date)

End date for the recurrence pattern

Responses

* * *

Create a new schedule configuration within a WhatsApp Business Account. This endpoint

allows businesses to set up automated scheduling for various operations such as business hours,

automated responses, and maintenance windows.

Use Cases:

Create business hours schedules for automated responses

Set up maintenance windows for system operations

Configure automated message campaigns with timing

Establish recurring schedule patterns for business operations

Prerequisites:

WhatsApp Business Account must have scheduling feature enabled

Appropriate permissions for schedule management

Valid timezone and time format specifications

Business must meet WhatsApp Business API requirements

Process Flow:

Submit schedule configuration with timing and recurrence details

System validates schedule parameters and conflicts

Schedule is created and activated based on is_active flag

Monitor schedule status through GET endpoint

Rate Limiting:

Schedule creation is subject to rate limits to prevent abuse.

Standard Graph API rate limits also apply.

Validation:

Start time must be before end time

Timezone must be valid IANA timezone identifier

Days of week must be valid if specified

Recurrence pattern must be consistent with schedule type

200

Successfully created schedule

Content Type: application/json

Schema: ScheduleCreateResponse

Show child attributes

* * *

ScheduleCreateResponse

* * *

idstring·required

Unique identifier for the created schedule

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

Forbidden - Insufficient permissions or schedule limit exceeded

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

Not Found - WhatsApp Business Account ID does not exist or is not accessible

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

409

Conflict - Schedule name already exists or time conflict

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
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/schedules' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "name": "Business Hours Schedule",
  "schedule_type": "BUSINESS_HOURS",
  "description": "Standard business operating hours",
  "start_time": "09:00",
  "end_time": "17:00",
  "timezone": "America/New_York",
  "days_of_week": [\
    "MONDAY",\
    "TUESDAY",\
    "WEDNESDAY",\
    "THURSDAY",\
    "FRIDAY"\
  ],
  "is_active": true,
  "recurrence_pattern": {
    "frequency": "WEEKLY",
    "interval": 1
  }
}'
```

Select status code

200400401403404409422429500

* * *

```
\{
  "successful_creation": {
    "summary": "Schedule successfully created",
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