
# Groups API Pricing

Updated: Oct 22, 2025

## Per-message pricing on Groups API

Groups API uses Cloud API’s [per-message pricing model](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing#per-message-pricing) to determine if a given message is billable. However, **you are charged each time a billable message is delivered to someone in the group.**

For example, if you send a (billable) marketing template message to a group with 5 WhatsApp users and it is delivered to all 5 users, you would be charged for 5 delivered messages at the going marketing message rate for each recipient’s country calling code.

If the message was delivered to only 4 of the 5 users, you would only be charged for the 4 delivered messages.

## How customer service windows work with Groups API

Customer service windows work differently when using Groups API.

When any WhatsApp user in the group messages you, a [customer service window](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/send-messages#customer-service-windows) is opened between you and the entire group (or is refreshed, if one already exists). This allows you to send utility and marketing template messages, or free form messages, for free.

This is different from 1:1 messaging, where when a WhatsApp user messages you, a [customer service window](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/send-messages#customer-service-windows) is opened between you and that customer (or is refreshed, if one already exists).

Everything else about [customer service windows](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/send-messages#customer-service-windows) remains the same.

## Pricing information in Message Status webhook

Pricing information for messages sent using Groups API is included in [messages status webhooks](https://developers.facebook.com/documentation/business-messaging/whatsapp/groups/webhooks#pricing-information).

### How `read` and `delivered` message status webhooks are processed

In order for a message status to be considered `read`, it must have been at least `delivered`.

In some scenarios, such as when a user is present in the chat thread when a message arrives, the message is marked `delivered` and `read` nearly simultaneously. In this and other similar scenarios, the `delivered` webhook is not sent back. This is because it is implied that the message was delivered since it has been read.

### How pricing data is displayed in the Message Status webhook

Not all Message Status webhooks include pricing information.

With the introduction of [Per-message Pricing](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing#per-message-pricing), pricing data can be present in `sent`, `delivered` or `read` status webhook. If a message is **charged**, you can expect that at least one webhook (`delivered` or `read`) will contain the pricing information.

### Sent message status webhook

```
// All versions

"pricing": {
  "billable": "&lt;IS_BILLABLE&gt;",
  "pricing_model": "&lt;PRICING_MODEL&gt;",  // new value, see table below
  "type": "&lt;PRICING_TYPE&gt;",            // new property, see table below
  "category": "&lt;CONVERSATION_CATEGORY&gt;"
}
```

### Delivered / Read message status webhook

```
// Version 24.0 and higher

"pricing": {
  "billable": "<IS_BILLABLE?>",
  "pricing_model": "&lt;PRICING_MODEL&gt;",  // new value, see table below
  "type": "&lt;PRICING_TYPE&gt;",            // new property, see table below
  "category": "&lt;CONVERSATION_CATEGORY&gt;"
}
// Version 23.0 and lower
"conversation": {
  "id": "&lt;CONVERSATION_ID&gt;",           // new behavior, see table below
  "expiration_timestamp": "&lt;CONVERSATION_EXPIRATION_TIMESTAMP&gt;",
  "origin": {
    "type": "&lt;CONVERSATION_CATEGORY&gt;"
  }
},

"pricing": {
  "billable": "<IS_BILLABLE?>",
  "pricing_model": "PMP",              // Value is now "PMP" instead of "CBP"
  "type": "&lt;PRICING_TYPE&gt;",            // new property, see table below
  "category": "&lt;PRICING_CATEGORY&gt;"
}
```

### Parameters

| Placeholder | Description |
| --- | --- |
| `&lt;CONVERSATION_ID&gt;` | Version 24.0 and higher:<br />The `conversation` object will be omitted entirely<br />Version 23.0 and lower:<br />Value will now be set to a unique ID per-message, instead of per-conversation. |
| `&lt;CONVERSATION_CATEGORY&gt;` | Not changing. |
| `&lt;CONVERSATION_EXPIRATION_TIMESTAMP&gt;` | Not changing. |
| `<IS_BILLABLE?>` | Not changing.<br />However, the `billable` property will be deprecated in a future [versioned release](https://developers.facebook.com/docs/graph-api/guides/versioning#calling_older_versions), so we recommend that you start using `pricing.type` and `pricing.category` together to determine if a message is billable, and if so, its [billing rate](https://developers.facebook.com/documentation/business-messaging/whatsapp/groups/pricing#identifying-billable-messages). |
| `&lt;PRICING_TYPE&gt;` | New property. Values can be:<br />`regular` — indicates the message is billable.<br />`free_group_customer_service` — indicates the message is free because it was either a utility template message or non-template message sent within a [customer service window](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/send-messages#customer-service-windows). |
| `&lt;PRICING_CATEGORY&gt;` | Values are not changing, but can now be interpreted as follows:<br />`group_marketing` — indicates a marketing template message.<br />`group_utility` — indicates a utility template message.<br />`group_service` — indicates a non-template message. |

### Identifying billable messages

Billable messages have `pricing.type` set to regular. The `pricing.category` value indicates the rate (`group_marketing` or `group_utility`).

### Identifying free messages

Free messages have `pricing.type` set to `free_group_customer_service`. The `pricing.category` value tells you why it was free:

`group_utility` — the message was sent within an open group customer service window.
`group_service` — all non-templates messages are free.

## Messaging analytics for Groups API

The `analytics` field provides the number and type of messages sent and delivered by the phone numbers associated with a specific WABA — for conversation metrics, see Conversation Analytics.

You can use the following endpoint to retrieve analytics for messages sent using Groups API:

```
/&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;?fields=analytics.&lt;FILTER_PARAMETER&gt;.&lt;FILTER_PARAMETER&gt;...
```

### Filter parameters for messaging analytics

For a full list of messaging analytics filter parameters, view the [Messaging Analytics reference](https://developers.facebook.com/documentation/business-messaging/whatsapp/analytics#conversation-analytics).

### Changes to filter parameters for Groups API

| Name | Description |
| --- | --- |
| `product_types`<br />type: Array | _Optional._<br />The types of messages (notification messages and/or customer support messages) for which you want to retrieve notifications.<br />Provide an array and include:<br />`101` for group notification messages<br />`102` for group customer support messages.<br />`103` for inbound group messages<br />If the above values are not provided, the API call will be return analytics for all messages together.<br />Inbound product type cannot be queried together with other product types, or you will see an error similar to the one below:<br />```<br /> {<br /> "error": {<br />   "message": "Invalid parameter",<br />   "type": "OAuthException",<br />   "code": 100,<br />   "error_subcode": 2388077,<br />   "is_transient": false,<br />   "error_user_title": "Insight Invalid Product Type Combination",<br />   "error_user_msg": "Unable to query this combination of product types. Please query individually and try again.",<br /> }<br />}<br />``` |

### Response value

Successful responses to the analytics API when querying Groups API message data will return an object similar to the following:

**Note: The country code filter is not supported for group sent messages.**

```
With Country code filter
{
  "analytics": {
    "phone_numbers": [\
      "16505550111",\
      "16505550112",\
      "16505550113"\
    ],
    "country_codes": [\
      "US",\
      "BR"\
    ],
    "granularity": "DAY",
    "data_points": [\
      {\
        "start": 1543543200,\
        "end": 1543629600,\
        "sent": 196093,\
        "delivered": 179715,\
        "groups_delivered": 4\
      },\
      {\
        "start": 1543629600,\
        "end": 1543716000,\
        "sent": 147649,\
        "delivered": 139032\
      }\
      # more data points\
    ]
  },
  "id": "102290129340398"
}

Without Country code filter
{
  "analytics": {
    "phone_numbers": [\
      "16505550111",\
      "16505550112",\
      "16505550113"\
    ],
    "granularity": "DAY",
    "data_points": [\
      {\
        "start": 1543543200,\
        "end": 1543629600,\
        "sent": 196093,\
        "delivered": 179715,\
        "groups_sent": 2,\
        "groups_delivered": 4\
      },\
      {\
        "start": 1543629600,\
        "end": 1543716000,\
        "sent": 147649,\
        "delivered": 139032\
      }\
      # more data points\
    ]
  },
  "id": "102290129340398"
}
```

## Pricing analytics for Groups API

The `pricing_analytics` field allows you to get pricing breakdowns for any messages delivered within a specified date range.

```
GET /&lt;WABA_ID&gt;
?fields=pricing_analytics
.start(&lt;START&gt;)
.end(&lt;END&gt;)
.granularity(&lt;GRANULARITY&gt;)
.phone_numbers(&lt;PHONE_NUMBERS&gt;)
.country_codes(&lt;COUNTRY_CODES&gt;)
.metric_types(&lt;METRIC_TYPES&gt;)
.pricing_types(&lt;PRICING_TYPES&gt;)
.pricing_categories(&lt;PRICING_CATEGORIES&gt;)
.dimensions(&lt;DIMENSIONS&gt;)
```

### Filter parameters for pricing analytics

For a full list of messaging analytics filter parameters, view the [Messaging Analytics reference](https://developers.facebook.com/documentation/business-messaging/whatsapp/analytics#pricing-analytics).

### Changes to filter parameters for Groups API

| Name | Description |
| --- | --- |
| `&lt;PRICING_CATEGORIES&gt;`<br />_Array of strings_ | _Optional._<br />Array of pricing categories. If you send an empty array, we return results for all pricing categories.<br />Values can be:<br />`GROUP_MARKETING`: Group messages charged the marketing rate.<br />`GROUP_SERVICE`: Group messages that were not charged. Includes all non-template messages and utility messages sent inside of a customer service window.<br />`GROUP_UTILITY`: Group messages charged the utility rate. |
| `&lt;PRICING_TYPES&gt;`<br />_Array of strings_ | _Optional._<br />Array of pricing types. If you send an empty array, we return results for all pricing types.<br />Values can be:<br />`FREE_GROUP_CUSTOMER_SERVICE`: Free group messages. These are non-template messages and utility messages sent within group customer service windows.<br />`REGULAR`: Billable messages. Includes all authentication and marketing template messages, and any utility template messages sent outside of a customer service window. |

## Rate cards

Group utility messages are not eligible for volume tiers.

Messaging rates for Groups API are the same as per-messaging pricing rates for 1 to 1 messaging.

[View per-message pricing rate cards](https://developers.facebook.com/documentation/business-messaging/whatsapp/pricing#rate-cards-and-volume-tiers)

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Per-message pricing on Groups API

How customer service windows work with Groups API

Pricing information in Message Status webhook

How read and delivered message status webhooks are processed

How pricing data is displayed in the Message Status webhook

Sent message status webhook

Delivered / Read message status webhook

Parameters

Identifying billable messages

Identifying free messages

Messaging analytics for Groups API

Filter parameters for messaging analytics

Changes to filter parameters for Groups API

Response value

Pricing analytics for Groups API

Filter parameters for pricing analytics

Changes to filter parameters for Groups API

Rate cards

* * *