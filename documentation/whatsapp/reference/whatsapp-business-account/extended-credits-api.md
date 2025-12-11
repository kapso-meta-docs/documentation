
# WhatsApp Cloud API - Extended Credits API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/extended-credits-api/v23.0.md/)

Version

v23.0

Retrieve extended credit line information for WhatsApp Business Accounts.

Returns credit line IDs and associated legal entity names

for billing and payment management.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Business-ID}/extendedcredits](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/extended-credits-api#get-version-business-id-extendedcredits) |

* * *

## GET /{Version}/{Business-ID}/extendedcredits

Endpoint reference: [Business > Extendedcredits](https://developers.facebook.com/docs/marketing-api/reference/extended-credit/)

### Request Syntax

**GET**/{Version}/{Business-ID}/extendedcredits

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/extendedcredits' \
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
      "data": [\
        {\
          "id": "1972385232742146",\
          "legal_entity_name": "Lucky Shrub"\
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

Business-IDstring·required

Responses

* * *

Endpoint reference: [Business > Extendedcredits](https://developers.facebook.com/docs/marketing-api/reference/extended-credit/)

200

Example response

Content Type: application/json

Schema: object

Show child attributes

* * *

dataarray of object

Show child attributes

* * *

data\[\]object

Show child attributes

* * *

idstring

* * *

legal_entity_namestring

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Business-ID}/extendedcredits' \
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
      "data": [\
        {\
          "id": "1972385232742146",\
          "legal_entity_name": "Lucky Shrub"\
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