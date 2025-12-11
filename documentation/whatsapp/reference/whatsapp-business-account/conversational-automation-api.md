
# WhatsApp Business Account - Conversational Automation API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/conversational-automation-api/v23.0.md/)

Version

v23.0

API for managing conversational automation settings for WhatsApp Business Account phone numbers.

This endpoint allows businesses to configure automated conversation features including

welcome messages, conversation prompts (ice breakers), and bot commands for their

WhatsApp Business phone numbers.

## Base URL

| https://graph.facebook.com |

## Endpoints

| POST | [/{Version}/{Phone-Number-ID}/conversational_automation](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/conversational-automation-api#post-version-phone-number-id-conversational-automation) |

* * *

## POST /{Version}/{Phone-Number-ID}/conversational_automation

Configure conversational automation settings for a WhatsApp Business Account phone number,

including welcome messages, conversation prompts (ice breakers), and bot commands.

Use Cases:

Set up automated welcome messages for new customer conversations

Configure conversation prompts to guide customer interactions

Define bot commands for common customer service scenarios

Update existing automation settings

Enable or disable specific automation features

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Validation:

Command names must be unique within the same phone number

Prompts and command descriptions must comply with WhatsApp Business policies

Maximum limits are enforced for prompts and commands

### Request Syntax

**POST**/{Version}/{Phone-Number-ID}/conversational_automation

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/conversational_automation' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "enable_welcome_message": true,
  "prompts": [\
    "How can I help you today?",\
    "What product are you interested in?"\
  ],
  "commands": []
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "success_response": {
    "summary": "Successful configuration",
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

Your WhatsApp Business phone number ID. This ID represents the phone number

entity and can be obtained from your WhatsApp Business Account phone numbers list.

Request BodyRequired

* * *

Content Type: application/json

Schema: ConversationalAutomationRequest

Show child attributes

* * *

ConversationalAutomationRequest

* * *

enable_welcome_messageboolean

Whether to enable welcome messages for new conversations

* * *

promptsarray of string

List of conversation prompts (ice breakers) to help guide customer interactions

Show child attributes

* * *

prompts\[\]string

Individual conversation prompt text

* * *

commandsarray of BotCommand

List of bot commands for automated responses

Show child attributes

* * *

commands\[\]BotCommand

Bot command configuration for automated responses

Show child attributes

* * *

command_namestring·required

Name of the bot command (without leading slash)

* * *

command_descriptionstring·required

Description of what the command does

Responses

* * *

Configure conversational automation settings for a WhatsApp Business Account phone number,

including welcome messages, conversation prompts (ice breakers), and bot commands.

Use Cases:

Set up automated welcome messages for new customer conversations

Configure conversation prompts to guide customer interactions

Define bot commands for common customer service scenarios

Update existing automation settings

Enable or disable specific automation features

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Validation:

Command names must be unique within the same phone number

Prompts and command descriptions must comply with WhatsApp Business policies

Maximum limits are enforced for prompts and commands

200

Successfully configured conversational automation settings

Content Type: application/json

Schema: ConversationalAutomationResponse

Show child attributes

* * *

ConversationalAutomationResponse

* * *

successboolean·required

Indicates whether the automation configuration was successful

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
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/conversational_automation' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "enable_welcome_message": true,
  "prompts": [\
    "How can I help you today?",\
    "What product are you interested in?"\
  ],
  "commands": []
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "success_response": {
    "summary": "Successful configuration",
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