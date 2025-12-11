
# Group messages webhook reference

Updated: Nov 10, 2025

This reference describes trigger events and payload contents for the WhatsApp Business Account **messages** webhook for messages that are sent to a group, or received from a group.

## Triggers

A WhatsApp user or a business sends a message to a group.
A Whatsapp user or a business receives a message within a group.

## Syntax

```
\{
  "object": "whatsapp_business_account",
  "entry": [\
    {\
      "id": "&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;",\
      "changes": [\
        {\
          "value": {\
            "messaging_product": "whatsapp",\
            "metadata": {\
              "display_phone_number": "&lt;BUSINESS_DISPLAY_PHONE_NUMBER&gt;",\
              "phone_number_id": "&lt;BUSINESS_PHONE_NUMBER_ID&gt;"\
            },\
            "contacts": [\
              {\
                "profile": {\
                  "name": "&lt;WHATSAPP_USER_PROFILE_NAME&gt;"\
                },\
                "wa_id": "&lt;WHATSAPP_USER_ID&gt;",\
                "identity_key_hash": "&lt;IDENTITY_KEY_HASH&gt;" <!-- only included if identity change check enabled -->\
              }\
            ],\
            "messages": [\
              {\
                "from": "&lt;WHATSAPP_USER_PHONE_NUMBER&gt;",\
                "group_id": "&lt;GROUP_ID&gt;",\
                "id": "&lt;WHATSAPP_MESSAGE_ID&gt;",\
                "timestamp": "&lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;",\
                "text": {\
                  "body": "&lt;MESSAGE_TEXT_BODY&gt;"\
                },\
                "type": "&lt;MESSAGE_TYPE&gt;"\
              }\
            ],\
          },\
          "field": "messages"\
        }\
      ]\
    }\
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `&lt;BUSINESS_DISPLAY_PHONE_NUMBER&gt;`<br />_String_ | Business display phone number. | `15550783881` |
| `&lt;BUSINESS_PHONE_NUMBER_ID&gt;`<br />_String_ | Business phone number ID. | `106540352242922` |
| `&lt;GROUP_ID&gt;`<br />_String_ | The string identifier of a group made using the Groups API.<br />This field shows when messages are sent, received, or read from a group.<br />[Learn more about the Groups API](https://developers.facebook.com/documentation/business-messaging/whatsapp/groups) | `"Y2FwaV9ncm91cDoxNzA1NTU1MDEzOToxMjAzNjM0MDQ2OTQyMzM4MjAZD"` |
| `&lt;IDENTITY_KEY_HASH&gt;`<br />_String_ | Identity key hash. Only included if you have enabled the [identity change check](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers) feature. | `DF2lS5v2W6x=` |
| `&lt;MESSAGE_TEXT_BODY&gt;`<br />_String_ | Text body of the message. | `What do you all think about this?` |
| `&lt;MESSAGE_TYPE&gt;`<br />_String_ | The type of message being sent. Will change depending on the message sent to the group.<br />Currently, the Groups API supports:<br />Text<br />Media<br />Text-based templates<br />Media-based templates | `text` |
| `&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;`<br />_String_ | WhatsApp Business Account ID. | `102290129340398` |
| `&lt;WHATSAPP_MESSAGE_ID&gt;`<br />_String_ | WhatsApp message ID. | `wamid.HBgLMTY1MDM4Nzk0MzkVAgASGBQzQUFERjg0NDEzNDdFODU3MUMxMAA=` |
| `&lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;`<br />_String_ | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `&lt;WHATSAPP_USER_PHONE_NUMBER&gt;`<br />_String_ | WhatsApp user phone number. This is the same value returned by the API as the `input` value when sending a message to a WhatsApp user. Note that a WhatsApp user’s phone number and ID may not always match. | `+16505551234` |
| `&lt;WHATSAPP_USER_PROFILE_NAME&gt;`<br />_String_ | WhatsApp user’s name as it appears in their profile in the WhatsApp client. | `Sheena Nelson` |
| `&lt;WHATSAPP_USER_ID&gt;`<br />_String_ | WhatsApp user ID. Note that a WhatsApp user’s ID and phone number may not always match. | `16505551234` |

## Example

```
\{
  "object": "whatsapp_business_account",
  "entry": [\
    {\
      "id": "102290129340398",\
      "changes": [\
        {\
          "value": {\
            "messaging_product": "whatsapp",\
            "metadata": {\
              "display_phone_number": "15550783881",\
              "phone_number_id": "106540352242922"\
            },\
            "contacts": [\
              {\
                "profile": {\
                  "name": "Tiago Mingo"\
                },\
                "wa_id": "16505551234"\
              }\
            ],\
            "messages": [\
              {\
                "from": "16505551234",\
                "group_id": "HBgLMTY1MDM4Nzk0MzkVAgASGBQzQTRBNjU5OUFFRTAzODEwMTQ0RgA",\
                "id": "wamid.HASDI128HJOPUERIH82ahdasd09ASDHi5>",\
                "timestamp": "1744344496",\
                "text": {\
                  "body": "What does everyone think about this?"\
                },\
                "type": "text"\
              }\
            ],\
          },\
          "field": "messages"\
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

Triggers

Syntax

Parameters

Example

* * *