
# Template Comparison

Updated: Nov 14, 2025

You can compare two templates by examining how often each one is sent, which one has the lower ratio of blocks to sends, and each template’s top reason for being blocked.

## Requirements

A [User](https://developers.facebook.com/documentation/business-messaging/whatsapp/access-tokens#user-access-tokens) or [System User](https://developers.facebook.com/documentation/business-messaging/whatsapp/access-tokens#system-user-access-tokens) access token.
The [whatsapp_business_management](https://developers.facebook.com/docs/permissions/reference/whatsapp_business_management) permission.

## Limitations

Only two templates can be compared at a time.
Both templates must be in the same WhatsApp Business Account.
Templates must have been sent at least 1,000 times in the queries specified timeframe.
Lookback windows are limited to 7, 30, 60 and 90 days from the time of the request.

## Comparing templates

Use the [WhatsApp Message Template > Compare](https://developers.facebook.com/docs/graph-api/reference/whats-app-business-hsm/compare) endpoint to target one template and compare it with another.

### Request Syntax

```
GET /&lt;WHATSAPP_MESSAGE_TEMPLATE_ID&gt;/compare
  ?template_ids=[<TEMPLATE_IDS]
  &start=&lt;START&gt;
  &end=&lt;END&gt;
```

### Query parameters

| Placeholder | Description |
| --- | --- |
| `&lt;WHATSAPP_MESSAGE_TEMPLATE_ID&gt;` | ID of the WhatsApp Message Template to target. |
| `&lt;TEMPLATE_IDS&gt;` | ID of the WhatsApp Message Template to compare the target to. |
| `&lt;START&gt;` | UNIX timestamp indicating start of timeframe. See [Timeframes](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-comparison#timeframes). |
| `&lt;END&gt;` | UNIX timestamp indicating end of timeframe. See [Timeframes](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-comparison#timeframes). |

### Timeframes

Timeframes (lookback windows) are limited to 7, 30, 60 and 90 days from the time of the request. To define a timeframe, set your end date to the current time as a UNIX timestamp, then subtract the number of days for your desired timeframe, in seconds, from that value:

Subtract `604800` for a 7 day window.
Subtract `2592000` for a 30 day window.
Subtract `5184000` for a 60 day window.
Subtract `7776000` for a 90 day window.

### Response

Upon success, the API will return a list of [WhatsApp Business Template Comparison](https://developers.facebook.com/docs/graph-api/reference/whats-app-business-hsm-comparison) nodes describing each template’s block rate, number of times sent, and top reason for being blocked.

```
{
  "data": [\
    {\
      "metric": "BLOCK_RATE",\
      "type": "RELATIVE",\
      "order_by_relative_metric": [&lt;ORDER_BY_RELATIVE_METRIC&gt;]\
    },\
    {\
      "metric": "MESSAGE_SENDS",\
      "type": "NUMBER_VALUES",\
      "number_values": [&lt;NUMBER_VALUES&gt;]\
    },\
    {\
      "metric": "TOP_BLOCK_REASON",\
      "type": "STRING_VALUES",\
      "string_values": [&lt;STRING_VALUES&gt;]\
    }\
  ]
}
```

### Response contents

| Placeholder | Description |
| --- | --- |
| `&lt;ORDER_BY_RELATIVE_METRIC&gt;` | Array of template ID strings, in increasing order of block rate (ratio of blocks to sends). |
| `&lt;NUMBER_VALUES&gt;` | Array of message send number value objects. Objects have the following properties:<br />`key` — _String._ WhatsApp Message Template ID.<br />`value` — _Integer._ Number of times sent in a template message. |
| `&lt;STRING_VALUES&gt;` | Array of top block reason string value objects. Objects have the following properties:<br />`key` — _String._ WhatsApp Message Template ID.<br />`value` — _String._ Top block reason.<br />Block reasons can be:<br />`NO_LONGER_NEEDED`<br />`NO_REASON`<br />`NO_REASON_GIVEN`<br />`NO_SIGN_UP`<br />`OFFENSIVE_MESSAGES`<br />`OTHER`<br />`OTP_DID_NOT_REQUEST`<br />`SPAM`<br />`UNKNOWN_BLOCK_REASON`<br />See the [View metrics for your WhatsApp Business message template](https://www.facebook.com/business/help/511126334359303/) help center topic for descriptions of these reasons. |

### Example request

```
curl -X GET 'https://graph.facebook.com/v24.0/5289179717853347/compare?template_ids=[1533406637136032]&start=1674844791182&end=1674845395982' \
-H 'Authorization: Bearer EAAJB...'
```

### Example response

```
{
  "data": [\
    {\
      "metric": "BLOCK_RATE",\
      "type": "RELATIVE",\
      "order_by_relative_metric": [\
        "1533406637136032",\
        "5289179717853347"\
      ]\
    },\
    {\
      "metric": "MESSAGE_SENDS",\
      "type": "NUMBER_VALUES",\
      "number_values": [\
        {\
          "key": "5289179717853347",\
          "value": 1273\
        },\
        {\
          "key": "1533406637136032",\
          "value": 1042\
        }\
      ]\
    },\
    {\
      "metric": "TOP_BLOCK_REASON",\
      "type": "STRING_VALUES",\
      "string_values": [\
        {\
          "key": "5289179717853347",\
          "value": "UNKNOWN_BLOCK_REASON"\
        },\
        {\
          "key": "1533406637136032",\
          "value": "UNKNOWN_BLOCK_REASON"\
        }\
      ]\
    }\
  ]
}
```

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Requirements

Limitations

Comparing templates

Request Syntax

Query parameters

Timeframes

Response

Response contents

Example request

Example response

* * *