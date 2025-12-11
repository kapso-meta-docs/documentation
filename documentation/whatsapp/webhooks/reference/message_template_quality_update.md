
# message_template_quality_update webhook reference

Updated: Oct 22, 2025

This reference describes trigger events and payload contents for the WhatsApp Business Account `message_template_quality_update` webhook.

The **message_template_quality_update** webhook notifies you of changes to a template’s [quality score](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-quality).

## Triggers

A template’s quality score changes.

## Syntax

```
\{
  "entry": [\
    {\
      "id": "&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;",\
      "time": &lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;,\
      "changes": [\
        {\
          "value": {\
            "previous_quality_score": "&lt;PREVIOUS_QUALITY_SCORE&gt;",\
            "new_quality_score": "&lt;NEW_QUALITY_SCORE&gt;",\
            "message_template_id": &lt;TEMPLATE_ID&gt;,\
            "message_template_name": "&lt;TEMPLATE_NAME&gt;",\
            "message_template_language": "&lt;TEMPLATE_LANGUAGE_AND_LOCALE_CODE&gt;"\
          },\
          "field": "message_template_status_update"\
        }\
      ]\
    }\
  ],
  "object": "whatsapp_business_account"
}
```

## Parameters

| Placeholder | Description | Example value |
| --- | --- | --- |
| `&lt;NEW_QUALITY_SCORE&gt;`<br />_String_ | New template [quality score](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-quality).<br />Values can be:<br />`GREEN` — Indicates high quality.<br />`RED` — Indicates low quality.<br />`YELLOW` — Indicates medium quality.<br />`UNKNOWN` — Indicates quality pending. | `GREEN` |
| `&lt;PREVIOUS_QUALITY_SCORE&gt;`<br />_String_ | Previous template [quality score](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-quality).<br />Values can be:<br />`GREEN` — Indicates high quality.<br />`RED` — Indicates low quality.<br />`YELLOW` — Indicates medium quality.<br />`UNKNOWN` — Indicates quality pending. | `YELLOW` |
| `&lt;TEMPLATE_ID&gt;`<br />_Integer_ | Template ID. | `806312974732579` |
| `&lt;TEMPLATE_NAME&gt;`<br />_String_ | Template name. | `welcome_template` |
| `&lt;TEMPLATE_LANGUAGE_AND_LOCALE_CODE&gt;`<br />_String_ | Template [language and locale](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/supported-languages) code. | `en-US` |
| `&lt;WEBHOOK_TRIGGER_TIMESTAMP&gt;`<br />_Integer_ | Unix timestamp indicating when the webhook was triggered. | `1739321024` |
| `&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;`<br />_String_ | WhatsApp Business Account ID. | `102290129340398` |

## Example

```
\{
  "entry": [\
    {\
      "id": "102290129340398",\
      "time": 1674864290,\
      "changes": [\
        {\
          "value": {\
            "previous_quality_score": "GREEN",\
            "new_quality_score": "YELLOW",\
            "message_template_id": 806312974732579,\
            "message_template_name": "welcome_template",\
            "message_template_language": "en-US"\
          },\
          "field": "message_template_status_update"\
        }\
      ]\
    }\
  ],
  "object": "whatsapp_business_account"
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