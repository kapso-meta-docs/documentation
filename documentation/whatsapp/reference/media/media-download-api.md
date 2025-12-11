
# WhatsApp Cloud API - Media Download API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/media/media-download-api/v23.0.md/)

Version

v23.0

Download media files using URLs obtained from media retrieval endpoints.

Returns binary media content with appropriate MIME type headers.

Media URLs expire after 5 minutes and must be re-retrieved if expired.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{Media-URL}](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/media/media-download-api#get-version-media-url) |

* * *

## GET /{Version}/{Media-URL}

Download media files using URLs obtained from media retrieval endpoints.

Requires User Access Token with whatsapp_business_messaging permission.

Media URLs expire after 5 minutes and must be re-retrieved if expired.

Returns binary content with appropriate MIME type headers.

### Request Syntax

**GET**/{Version}/{Media-URL}

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Media-URL}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200

* * *

```
\{
  "Download Media": {
    "value": ""
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

Media-URLstring·required

Responses

* * *

Download media files using URLs obtained from media retrieval endpoints.

Requires User Access Token with whatsapp_business_messaging permission.

Media URLs expire after 5 minutes and must be re-retrieved if expired.

Returns binary content with appropriate MIME type headers.

200

Download Media

Content Type: text/plain

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{Media-URL}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200

* * *

```
\{
  "Download Media": {
    "value": ""
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