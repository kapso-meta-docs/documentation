
# smb_app_state_sync webhook reference

Updated: Oct 22, 2025

This reference describes trigger events and payload contents for the WhatsApp Business Account **smb_app_state_sync** webhook.

The **smb_app_state_sync** webhook is used for synchronizing contacts of [WhatsApp Business app users who have been onboarded](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users) via a solution provider.

## Triggers

A solution provider [synchronizes the WhatsApp Business app contacts](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users#step-1--initiate-contacts-synchronization) of a business customer with a WhatsApp Business app phone number who the provider has [onboarded](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users).
A business customer with a WhatsApp Business app phone number who has been [onboarded](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users) by a solution provider adds a contact to their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT0q3wvaane8UP8vN08xzBDlPGOcmijB5SZ1dXzFZgNUgDdKCALLKkcrgedmPC5H_36_SBrAD75FI1PhHXfH0bmvL0Iqr3iseLaRvYDGo2r2t_yZpDG9Jrr075MrAFwAGIw6TgwxZQh_aw).
A business customer with a WhatsApp Business app phone number who has been [onboarded](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users) by a solution provider removes a contact from their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT0q3wvaane8UP8vN08xzBDlPGOcmijB5SZ1dXzFZgNUgDdKCALLKkcrgedmPC5H_36_SBrAD75FI1PhHXfH0bmvL0Iqr3iseLaRvYDGo2r2t_yZpDG9Jrr075MrAFwAGIw6TgwxZQh_aw).
A business customer with a WhatsApp Business app phone number who has been [onboarded](https://developers.facebook.com/documentation/business-messaging/whatsapp/embedded-signup/onboarding-business-app-users) by a solution provider edits a contact in their WhatsApp Business app [contacts](https://l.facebook.com/l.php?u=https%3A%2F%2Ffaq.whatsapp.com%2F1270784217226727%2F&h=AT0q3wvaane8UP8vN08xzBDlPGOcmijB5SZ1dXzFZgNUgDdKCALLKkcrgedmPC5H_36_SBrAD75FI1PhHXfH0bmvL0Iqr3iseLaRvYDGo2r2t_yZpDG9Jrr075MrAFwAGIw6TgwxZQh_aw).

## Syntax

```
\{
  "object": "whatsapp_business_account",
  "entry": [\
    {\
      "id": "&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;",\
      "changes": [\
        {\
          "value": {\
            "messaging_product": "whatsapp",\
            "metadata": {\
              "display_phone_number": "&lt;BUSINESS_DISPLAY_PHONE_NUMBER&gt;",\
              "phone_number_id": "&lt;BUSINESS_PHONE_NUMBER_ID&gt;"\
            },\
            "state_sync": [\
              {\
                "type": "contact",\
                "contact": {\
                  "full_name": "&lt;CONTACT_FULL_NAME&gt;",\
                  "first_name": "&lt;CONTACT_FIRST_NAME&gt;",\
                  "phone_number": "&lt;CONTACT_PHONE_NUMBER&gt;"\
                },\
                "action": "&lt;ACTION&gt;",\
                "metadata": {\
                  "timestamp": "&lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;"\
                }\
              },\
              <!-- Additional contacts would follow, if any -->\
            ]\
          },\
          "field": "smb_app_state_sync"\
        }\
      ]\
    }\
  ]
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `&lt;ACTION&gt;`<br />_String_ | Indicates if the business customer added, edited, or deleted a contact from their WhatsApp Business app phone address book.<br />Values can be:<br />`add` — Indicates the WhatsApp Business app user added or edited a contact.<br />`remove` — Indicates the WhatsApp Business app user removed a contact. | `add` |
| `&lt;BUSINESS_DISPLAY_PHONE_NUMBER&gt;`<br />_String_ | Business display phone number. | `15550783881` |
| `&lt;BUSINESS_PHONE_NUMBER_ID&gt;`<br />_String_ | Business phone number ID. | `106540352242922` |
| `&lt;CONTACT_FIRST_NAME&gt;`<br />_String_ | The contact’s first name, as it appears in the business customer’s WhatsApp Business app phone address book.<br />Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo` |
| `&lt;CONTACT_FULL_NAME&gt;`<br />_String_ | The contact’s full name, as it appears in the business customer’s WhatsApp Business app phone address book.<br />Not included when the business customer removes a contact from their WhatsApp Business app phone address book. | `Pablo Morales` |
| `&lt;CONTACT_PHONE_NUMBER&gt;` _String_ | The contact’s WhatsApp phone number. | `16505551234` |
| `&lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;`<br />_Integer_ | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;`<br />_String_ | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
\{
  "object": "whatsapp_business_account",
  "entry": [\
    {\
      "id": "102290129340398",\
      "changes": [\
        {\
          "value": {\
            "messaging_product": "whatsapp",\
            "metadata": {\
              "display_phone_number": "15550783881",\
              "phone_number_id": "106540352242922"\
            },\
            "state_sync": [\
              {\
                "type": "contact",\
                "contact": {\
                  "full_name": "Pablo Morales",\
                  "first_name": "Pablo",\
                  "phone_number": "16505551234"\
                },\
                "action": "add",\
                "metadata": {\
                  "timestamp": "1739321024"\
                }\
              }\
            ]\
          },\
          "field": "smb_app_state_sync"\
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