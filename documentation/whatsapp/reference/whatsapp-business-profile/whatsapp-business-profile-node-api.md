
# WhatsApp Business Profile Node API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-profile/whatsapp-business-profile-node-api/v23.0.md/)

Version

v23.0

This endpoint allows applications to retrieve comprehensive information about WhatsApp Business Profiles,

including profile details, contact information, and business metadata. This is essential for managing

business profile lifecycle and understanding current configuration state.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{WhatsApp-Business-Profile-ID}](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-profile/whatsapp-business-profile-node-api#get-version-whatsapp-business-profile-id) |
| POST | [/{Version}/{WhatsApp-Business-Profile-ID}](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-profile/whatsapp-business-profile-node-api#post-version-whatsapp-business-profile-id) |

* * *

## GET /{Version}/{WhatsApp-Business-Profile-ID}

Retrieve comprehensive details about a WhatsApp Business Profile, including business information,

contact details, and profile configuration.

Use Cases:

Retrieve business profile information and metadata

Verify profile configuration and contact details

Check profile status and business information

Validate profile state before business operations

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Profile details can be cached for moderate periods, but business information may change

occasionally. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{WhatsApp-Business-Profile-ID}

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Business-Profile-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "complete_profile": {
    "summary": "Complete business profile with all details",
    "value": {
      "id": "1234567890123456",
      "account_name": "E-commerce Business Account",
      "description": "Leading e-commerce platform for quality products",
      "email": "contact@business-example.com",
      "about": "Quality products delivered worldwide",
      "address": "123 Business Street, Commerce City, CC 12345",
      "vertical": "RETAIL",
      "websites": [\
        "https://www.business-example.com",\
        "https://shop.business-example.com"\
      ],
      "profile_picture_url": "https://pps.whatsapp.net/v/profile-picture-url",
      "messaging_product": "whatsapp"
    }
  },
  "minimal_profile": {
    "summary": "Minimal business profile with required fields only",
    "value": {
      "id": "2345678901234567"
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

WhatsApp-Business-Profile-IDstring·required

Your WhatsApp Business Profile ID. This ID is provided when the profile is created

and can be found in your WhatsApp Business Manager or through business management APIs.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned (id and any available profile fields).

Available fields: id, account_name, description, email, about, address, vertical, websites, profile_picture_url, messaging_product

Responses

* * *

Retrieve comprehensive details about a WhatsApp Business Profile, including business information,

contact details, and profile configuration.

Use Cases:

Retrieve business profile information and metadata

Verify profile configuration and contact details

Check profile status and business information

Validate profile state before business operations

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Profile details can be cached for moderate periods, but business information may change

occasionally. Implement appropriate cache invalidation strategies.

200

Successfully retrieved WhatsApp Business Profile details

Content Type: application/json

Schema: WhatsAppBusinessProfileNode

Show child attributes

* * *

WhatsAppBusinessProfileNode

* * *

idstring·required

Unique identifier for the WhatsApp Business Profile

* * *

account_namestring

Name of the business account

* * *

descriptionstring

Business description text

* * *

emailstring (email)

Contact email address of the business

* * *

aboutstring

About section text for the business profile

* * *

addressstring

Physical address of the business

* * *

verticalWhatsAppBusinessVertical

Industry vertical classification for the business

* * *

websitesarray of string (uri)

List of website URLs associated with the business

Show child attributes

* * *

websites\[\]string (uri)

* * *

profile_picture_urlstring (uri)

URL of the business profile picture

* * *

profile_picture_handlestring

Handle of the profile picture for upload operations

* * *

messaging_product"whatsapp"

The messaging service used

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

Not Found - WhatsApp Business Profile ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Business-Profile-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "complete_profile": {
    "summary": "Complete business profile with all details",
    "value": {
      "id": "1234567890123456",
      "account_name": "E-commerce Business Account",
      "description": "Leading e-commerce platform for quality products",
      "email": "contact@business-example.com",
      "about": "Quality products delivered worldwide",
      "address": "123 Business Street, Commerce City, CC 12345",
      "vertical": "RETAIL",
      "websites": [\
        "https://www.business-example.com",\
        "https://shop.business-example.com"\
      ],
      "profile_picture_url": "https://pps.whatsapp.net/v/profile-picture-url",
      "messaging_product": "whatsapp"
    }
  },
  "minimal_profile": {
    "summary": "Minimal business profile with required fields only",
    "value": {
      "id": "2345678901234567"
    }
  }
}
```

* * *

## POST /{Version}/{WhatsApp-Business-Profile-ID}

Update the WhatsApp Business Profile information such as business description, email, address,

and other profile details. This operation corresponds to the GraphWhatsAppBusinessProfilePost functionality.

Use Cases:

Update business profile information and metadata

Modify contact details and business description

Change business vertical classification

Update website URLs and profile picture

Maintain current business profile information

Profile Picture Upload:

It is recommended to use the Resumable Upload API to obtain an upload ID, then use this

upload ID to obtain the picture handle for the profile_picture_handle field.

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

### Request Syntax

**POST**/{Version}/{WhatsApp-Business-Profile-ID}

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Business-Profile-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "account_name": "Updated E-commerce Business",
  "description": "Updated leading e-commerce platform for premium products",
  "email": "updated-contact@business-example.com",
  "about": "Premium products delivered worldwide with excellent service",
  "address": "456 Updated Business Avenue, Commerce City, CC 54321",
  "vertical": "RETAIL",
  "websites": [\
    "https://www.updated-business-example.com",\
    "https://shop.updated-business-example.com"\
  ],
  "profile_picture_handle": "4:VGVzdC5wbmc=:aW1hZ2UvanBlZw==:ARat4Mt-L09JON3f30SmDkdyPSuyBkDDYiB4TFXuXISjdgHoNp2b7j882_9Jzr2tPrdKxi92UygyVzTivJiOvmebMpZ6MIjTik3gTyI3ZCQAgQ:e:1659995302:2022308451254161:636685196:ARZf1ftR5N6-qSLtklU"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "successful_update": {
    "summary": "Successful profile update response",
    "value": {
      "id": "1234567890123456",
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

WhatsApp-Business-Profile-IDstring·required

Your WhatsApp Business Profile ID. This ID is provided when the profile is created

and can be found in your WhatsApp Business Manager or through business management APIs.

Request BodyRequired

* * *

Content Type: application/json

Schema: WhatsAppBusinessProfileUpdateRequest

Show child attributes

* * *

WhatsAppBusinessProfileUpdateRequest

* * *

messaging_product"whatsapp"·required

The messaging service used for the request

* * *

account_namestring

Name of the business account

* * *

descriptionstring

Business description text

* * *

emailstring (email)

Contact email address of the business

* * *

aboutstring

About section text for the business profile

* * *

addressstring

Physical address of the business

* * *

verticalWhatsAppBusinessVertical

Industry vertical classification for the business

* * *

websitesarray of string (uri)

List of website URLs associated with the business

Show child attributes

* * *

websites\[\]string (uri)

* * *

profile_picture_handlestring

Handle of the profile picture generated from Resumable Upload API

Responses

* * *

Update the WhatsApp Business Profile information such as business description, email, address,

and other profile details. This operation corresponds to the GraphWhatsAppBusinessProfilePost functionality.

Use Cases:

Update business profile information and metadata

Modify contact details and business description

Change business vertical classification

Update website URLs and profile picture

Maintain current business profile information

Profile Picture Upload:

It is recommended to use the Resumable Upload API to obtain an upload ID, then use this

upload ID to obtain the picture handle for the profile_picture_handle field.

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

200

Successfully updated WhatsApp Business Profile

Content Type: application/json

Schema: WhatsAppBusinessProfileUpdateResponse

Show child attributes

* * *

WhatsAppBusinessProfileUpdateResponse

* * *

idstring

WhatsApp Business Profile ID that was updated

* * *

successboolean

Indicates if the update was successful

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

Not Found - WhatsApp Business Profile ID does not exist or is not accessible

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
  --url 'https://graph.facebook.com/{Version}/{WhatsApp-Business-Profile-ID}' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{
  "messaging_product": "whatsapp",
  "account_name": "Updated E-commerce Business",
  "description": "Updated leading e-commerce platform for premium products",
  "email": "updated-contact@business-example.com",
  "about": "Premium products delivered worldwide with excellent service",
  "address": "456 Updated Business Avenue, Commerce City, CC 54321",
  "vertical": "RETAIL",
  "websites": [\
    "https://www.updated-business-example.com",\
    "https://shop.updated-business-example.com"\
  ],
  "profile_picture_handle": "4:VGVzdC5wbmc=:aW1hZ2UvanBlZw==:ARat4Mt-L09JON3f30SmDkdyPSuyBkDDYiB4TFXuXISjdgHoNp2b7j882_9Jzr2tPrdKxi92UygyVzTivJiOvmebMpZ6MIjTik3gTyI3ZCQAgQ:e:1659995302:2022308451254161:636685196:ARZf1ftR5N6-qSLtklU"
}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "successful_update": {
    "summary": "Successful profile update response",
    "value": {
      "id": "1234567890123456",
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