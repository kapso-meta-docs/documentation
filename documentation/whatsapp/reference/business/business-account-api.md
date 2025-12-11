
# WhatsApp Cloud API - Business Account API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/business-account-api/v23.0.md/)

Version

v23.0

Retrieve Meta Business Portfolio information by Business ID.

Returns business name, timezone, and other account details

for managing WhatsApp Business Account configurations.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Business-ID}](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/business/business-account-api#get-version-business-id) |

* * *

## GET /{Version}/{Business-ID}

Endpoint reference: [Business](https://developers.facebook.com/docs/marketing-api/reference/business/)

### Request Syntax

**GET**/{Version}/{Business-ID}

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200

* * *

```
\{
  "Example response": {
    "value": {
      "id": "506914307656634",
      "name": "Lucky Shrub",
      "timezone_id": 0
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

Business-IDstring·required

Query Parameters

* * *

fieldsstring

Responses

* * *

Endpoint reference: [Business](https://developers.facebook.com/docs/marketing-api/reference/business/)

200

Example response

Content Type: application/json

Schema: object

Show child attributes

* * *

idstring

* * *

namestring

* * *

timezone_idnumber

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200

* * *

```
\{
  "Example response": {
    "value": {
      "id": "506914307656634",
      "name": "Lucky Shrub",
      "timezone_id": 0
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