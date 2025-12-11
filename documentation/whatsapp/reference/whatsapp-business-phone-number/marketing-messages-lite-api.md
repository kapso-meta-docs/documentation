
# WhatsApp Cloud API - Marketing Messages Lite API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/marketing-messages-lite-api/v23.0.md/)

Version

v23.0

Send marketing template messages with automatic delivery optimization.

Delivers relevant, timely messages to customers most likely to engage,

with enhanced deliverability and down-funnel conversion insights.

## Base URL

| https://graph.facebook.com |

## Endpoints

| POST | [/{Version}/{Phone-Number-ID}/marketing_messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-phone-number/marketing-messages-lite-api#post-version-phone-number-id-marketing-messages) |

* * *

## POST /{Version}/{Phone-Number-ID}/marketing_messages

Send marketing template messages using pre-approved templates. Supports optional product policy controls and message activity sharing settings.

### Request Syntax

**POST**/{Version}/{Phone-Number-ID}/marketing_messages

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/marketing_messages' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16315552222",
  "type": "template",
  "template": {
    "name": "hello_world",
    "language": {
      "code": "en"
    }
  }
}'
```

Select status code

200400401403

* * *

```
\{
  "Successful Response": {
    "summary": "Successful marketing message response",
    "value": {
      "contacts": [\
        {\
          "input": "16315552222",\
          "wa_id": "16315552222"\
        }\
      ],
      "messages": [\
        {\
          "id": "wamid.gBGGSFcCNEOPAgkO_KJ55r4w_ww"\
        }\
      ],
      "messaging_product": "whatsapp",
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

Content-TypeOne of "application/json", "application/x-www-form-urlencoded", "multipart/form-data"·required

Media type of the request body

Path Parameters

* * *

Versionstring·required

WhatsApp API version (e.g., v20.0)

Phone-Number-IDstring·required

WhatsApp Business Phone Number ID

Request BodyRequired

* * *

Content Type: application/json

Schema: MarketingMessageRequestPayload

Show child attributes

* * *

MarketingMessageRequestPayload

* * *

messaging_product"whatsapp"·required

Messaging service used. Must be "whatsapp"

* * *

recipient_type"individual"·required

Type of recipient. Must be "individual"

* * *

tostring·required

WhatsApp ID or phone number of the message recipient

* * *

type"template"·required

Type of message. Must be "template" for marketing messages

* * *

templateobject·required

Show child attributes

* * *

namestring·required

Name of the template.

* * *

languageLanguageObject·required

Contains a language object. Specifies the language the template may be rendered in

* * *

componentsarray of TemplateComponent

Array of components objects containing the parameters of the message.

Show child attributes

* * *

components\[\]TemplateComponent

* * *

product_policyOne of "CLOUD_API_FALLBACK", "STRICT"

Optional product policy setting

* * *

message_activity_sharingboolean

Optional flag to control message activity sharing

Responses

* * *

Send marketing template messages using pre-approved templates. Supports optional product policy controls and message activity sharing settings.

200

Marketing message sent successfully

Content Type: application/json

Schema: MarketingMessageResponsePayload

Show child attributes

* * *

MarketingMessageResponsePayload

* * *

contactsarray of object

Show child attributes

* * *

contacts\[\]object

Show child attributes

* * *

inputstring

* * *

wa_idstring

* * *

messagesarray of object

Show child attributes

* * *

messages\[\]object

Show child attributes

* * *

idstring

* * *

message_statusOne of "accepted", "held_for_quality_assessment", "paused"

The status of a WhatsApp message:

accepted: The message has been accepted by WhatsApp and is being processed

held_for_quality_assessment: The message is being held for quality assessment before delivery

paused: The message delivery has been paused

* * *

messaging_productstring

400

Bad Request - Invalid request parameters

Content Type: application/json

401

Unauthorized - Invalid or missing access token

Content Type: application/json

403

Forbidden - Template not approved or insufficient permissions

Content Type: application/json

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{Phone-Number-ID}/marketing_messages' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "recipient_type": "individual",
  "to": "16315552222",
  "type": "template",
  "template": {
    "name": "hello_world",
    "language": {
      "code": "en"
    }
  }
}'
```

Select status code

200400401403

* * *

```
\{
  "Successful Response": {
    "summary": "Successful marketing message response",
    "value": {
      "contacts": [\
        {\
          "input": "16315552222",\
          "wa_id": "16315552222"\
        }\
      ],
      "messages": [\
        {\
          "id": "wamid.gBGGSFcCNEOPAgkO_KJ55r4w_ww"\
        }\
      ],
      "messaging_product": "whatsapp",
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