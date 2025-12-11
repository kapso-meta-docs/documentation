
# WhatsApp Business Account - Subscribed Apps API

Copy for LLM

[View as Markdown](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/subscribed-apps-api/v23.0.md/)

Version

v23.0

API for managing app subscriptions to WhatsApp Business Account webhooks and retrieving

subscription details. This endpoint allows apps to subscribe to, unsubscribe from, and

query webhook subscriptions for WhatsApp Business Accounts.

## Base URL

| https://graph.facebook.com |

## Endpoints

| GET | [/{Version}/{WABA-ID}/subscribed_apps](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/subscribed-apps-api#get-version-waba-id-subscribed-apps) |
| POST | [/{Version}/{WABA-ID}/subscribed_apps](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/subscribed-apps-api#post-version-waba-id-subscribed-apps) |
| DELETE | [/{Version}/{WABA-ID}/subscribed_apps](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/subscribed-apps-api#delete-version-waba-id-subscribed-apps) |

* * *

## GET /{Version}/{WABA-ID}/subscribed_apps

Retrieve a list of all applications currently subscribed to webhook events

for the specified WhatsApp Business Account.

Use Cases:

Monitor which apps are subscribed to WABA webhook events

Audit subscription configurations and permissions

Verify subscription status before making changes

Retrieve subscription details for troubleshooting

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Subscription data can be cached for short periods, but may change when apps

subscribe or unsubscribe. Implement appropriate cache invalidation strategies.

### Request Syntax

**GET**/{Version}/{WABA-ID}/subscribed_apps

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request GET \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_subscriptions": {
    "summary": "Multiple apps subscribed to WABA",
    "value": {
      "data": [\
        {\
          "whatsapp_business_api_data": {\
            "id": "1234567890123456",\
            "name": "Business Messaging App",\
            "link": "https://www.facebook.com/games/?app_id=1234567890123456"\
          }\
        },\
        {\
          "whatsapp_business_api_data": {\
            "id": "2345678901234567",\
            "name": "Customer Support Bot",\
            "link": "https://www.facebook.com/games/?app_id=2345678901234567"\
          }\
        }\
      ]
    }
  },
  "no_subscriptions": {
    "summary": "No apps subscribed to WABA",
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

WABA-IDstring·required

WhatsApp Business Account ID. This ID can be found in your WhatsApp Manager

or through business management APIs.

Query Parameters

* * *

fieldsstring

Comma-separated list of fields to include in the response. If not specified,

default fields will be returned. Available fields: id, name, link

Responses

* * *

Retrieve a list of all applications currently subscribed to webhook events

for the specified WhatsApp Business Account.

Use Cases:

Monitor which apps are subscribed to WABA webhook events

Audit subscription configurations and permissions

Verify subscription status before making changes

Retrieve subscription details for troubleshooting

Rate Limiting:

Standard Graph API rate limits apply. Use appropriate retry logic with exponential backoff.

Caching:

Subscription data can be cached for short periods, but may change when apps

subscribe or unsubscribe. Implement appropriate cache invalidation strategies.

200

Successfully retrieved list of subscribed applications

Content Type: application/json

Schema: SubscribedAppsResponse

Show child attributes

* * *

SubscribedAppsResponse

* * *

dataarray of SubscribedApp·required

Array of subscribed applications

Show child attributes

* * *

data\[\]SubscribedApp

Subscribed application details

Show child attributes

* * *

whatsapp_business_api_dataWhatsAppBusinessApiData

Application subscription data for WhatsApp Business Account

Show child attributes

* * *

idstring·required

Unique identifier for the subscribed application

* * *

namestring·required

Name of the subscribed application

* * *

linkstring

URL link to the application

* * *

override_callback_uristring

Custom webhook callback URL for this subscription

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
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "multiple_subscriptions": {
    "summary": "Multiple apps subscribed to WABA",
    "value": {
      "data": [\
        {\
          "whatsapp_business_api_data": {\
            "id": "1234567890123456",\
            "name": "Business Messaging App",\
            "link": "https://www.facebook.com/games/?app_id=1234567890123456"\
          }\
        },\
        {\
          "whatsapp_business_api_data": {\
            "id": "2345678901234567",\
            "name": "Customer Support Bot",\
            "link": "https://www.facebook.com/games/?app_id=2345678901234567"\
          }\
        }\
      ]
    }
  },
  "no_subscriptions": {
    "summary": "No apps subscribed to WABA",
    "value": {
      "data": []
    }
  }
}
```

* * *

## POST /{Version}/{WABA-ID}/subscribed_apps

Subscribe your application to webhook events for the specified WhatsApp Business Account.

This enables your app to receive real-time notifications for events such as message

deliveries, status updates, and other WABA activities.

Use Cases:

Enable webhook notifications for your app

Configure custom callback URLs for webhook delivery

Set up webhook verification tokens for security

Override default app webhook settings for specific WABAs

Rate Limiting:

Standard Graph API rate limits apply. Subscription operations may have additional

throttling to prevent abuse.

Security:

Always use HTTPS endpoints for webhook callbacks. Verify webhook authenticity

using the provided verification tokens and signature validation.

### Request Syntax

**POST**/{Version}/{WABA-ID}/subscribed_apps

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "basic_subscription_success": {
    "summary": "Basic subscription successful",
    "value": {
      "success": true
    }
  },
  "custom_callback_success": {
    "summary": "Custom callback subscription successful",
    "value": {
      "success": true,
      "data": [\
        {\
          "override_callback_uri": "https://your-webhook-endpoint.com/webhook",\
          "whatsapp_business_api_data": {\
            "id": "1234567890123456",\
            "name": "Business Messaging App",\
            "link": "https://www.facebook.com/games/?app_id=1234567890123456"\
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

WABA-IDstring·required

WhatsApp Business Account ID. This ID can be found in your WhatsApp Manager

or through business management APIs.

Request BodyOptional

* * *

Optional configuration for webhook subscription

Content Type: application/json

Schema: SubscriptionRequest

Show child attributes

* * *

SubscriptionRequest

* * *

override_callback_uristring

Custom webhook callback URL to override app default

* * *

verify_tokenstring

Verification token for webhook security

Responses

* * *

Subscribe your application to webhook events for the specified WhatsApp Business Account.

This enables your app to receive real-time notifications for events such as message

deliveries, status updates, and other WABA activities.

Use Cases:

Enable webhook notifications for your app

Configure custom callback URLs for webhook delivery

Set up webhook verification tokens for security

Override default app webhook settings for specific WABAs

Rate Limiting:

Standard Graph API rate limits apply. Subscription operations may have additional

throttling to prevent abuse.

Security:

Always use HTTPS endpoints for webhook callbacks. Verify webhook authenticity

using the provided verification tokens and signature validation.

200

Successfully subscribed to WABA webhooks

Content Type: application/json

Schema: SubscriptionResponse

Show child attributes

* * *

SubscriptionResponse

* * *

successboolean·required

Indicates whether the subscription operation was successful

* * *

dataarray of SubscribedApp

Array containing subscription details

Show child attributes

* * *

data\[\]SubscribedApp

Subscribed application details

Show child attributes

* * *

whatsapp_business_api_dataWhatsAppBusinessApiData

Application subscription data for WhatsApp Business Account

Show child attributes

* * *

idstring·required

Unique identifier for the subscribed application

* * *

namestring·required

Name of the subscribed application

* * *

linkstring

URL link to the application

* * *

override_callback_uristring

Custom webhook callback URL for this subscription

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
curl --request POST \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "basic_subscription_success": {
    "summary": "Basic subscription successful",
    "value": {
      "success": true
    }
  },
  "custom_callback_success": {
    "summary": "Custom callback subscription successful",
    "value": {
      "success": true,
      "data": [\
        {\
          "override_callback_uri": "https://your-webhook-endpoint.com/webhook",\
          "whatsapp_business_api_data": {\
            "id": "1234567890123456",\
            "name": "Business Messaging App",\
            "link": "https://www.facebook.com/games/?app_id=1234567890123456"\
          }\
        }\
      ]
    }
  }
}
```

* * *

## DELETE /{Version}/{WABA-ID}/subscribed_apps

Unsubscribe your application from webhook events for the specified WhatsApp Business Account.

This will stop your app from receiving webhook notifications for this WABA.

Use Cases:

Disable webhook notifications when no longer needed

Clean up subscriptions during app decommissioning

Temporarily disable webhooks for maintenance

Remove subscriptions for WABAs no longer managed by your app

Rate Limiting:

Standard Graph API rate limits apply. Unsubscription operations are typically

processed immediately.

Important:

Unsubscribing will immediately stop all webhook deliveries for this WABA.

Ensure your application can handle the cessation of webhook events gracefully.

### Request Syntax

**DELETE**/{Version}/{WABA-ID}/subscribed_apps

Try it

Select language

cURLJavaScriptPython

* * *

```
curl --request DELETE \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "unsubscribe_success": {
    "summary": "Unsubscription successful",
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

WABA-IDstring·required

WhatsApp Business Account ID. This ID can be found in your WhatsApp Manager

or through business management APIs.

Responses

* * *

Unsubscribe your application from webhook events for the specified WhatsApp Business Account.

This will stop your app from receiving webhook notifications for this WABA.

Use Cases:

Disable webhook notifications when no longer needed

Clean up subscriptions during app decommissioning

Temporarily disable webhooks for maintenance

Remove subscriptions for WABAs no longer managed by your app

Rate Limiting:

Standard Graph API rate limits apply. Unsubscription operations are typically

processed immediately.

Important:

Unsubscribing will immediately stop all webhook deliveries for this WABA.

Ensure your application can handle the cessation of webhook events gracefully.

200

Successfully unsubscribed from WABA webhooks

Content Type: application/json

Schema: SubscriptionResponse

Show child attributes

* * *

SubscriptionResponse

* * *

successboolean·required

Indicates whether the subscription operation was successful

* * *

dataarray of SubscribedApp

Array containing subscription details

Show child attributes

* * *

data\[\]SubscribedApp

Subscribed application details

Show child attributes

* * *

whatsapp_business_api_dataWhatsAppBusinessApiData

Application subscription data for WhatsApp Business Account

Show child attributes

* * *

idstring·required

Unique identifier for the subscribed application

* * *

namestring·required

Name of the subscribed application

* * *

linkstring

URL link to the application

* * *

override_callback_uristring

Custom webhook callback URL for this subscription

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

Not Found - WABA ID does not exist or subscription not found

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
curl --request DELETE \
  --url 'https://graph.facebook.com/{Version}/{WABA-ID}/subscribed_apps' \
  --header 'Authorization: Bearer <Token>' \
  --header 'Content-Type: application/json' \
  --data '{}'
```

Select status code

200400401403404422429500

* * *

```
\{
  "unsubscribe_success": {
    "summary": "Unsubscription successful",
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