
# Template Library

Updated: Nov 14, 2025

Template Library makes it faster and easier for businesses to create utility templates for common use cases, like payment reminders, delivery updates — and authentication templates for common identity verification use cases.

These pre-written templates have already been categorized as utility or authentication. Library templates contain fixed content that cannot be edited and parameters you can adapt for business or user-specific information.

You can browse and create templates using Template Library in WhatsApp Manager, or programmatically via the API.

## Creating Templates via WhatsApp Manager (WAM)

Follow the instructions below to create templates using the Template Library in [WhatsApp Manager](https://business.facebook.com/wa/manage/template-library).

1: In the sidebar of WAM, under **Message Templates**, select **Create Template**.

![Image](https://scontent-lax3-2.xx.fbcdn.net/v/t39.2365-6/564050140_1339317901260194_2215442945738675402_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=7hQKErF1VZAQ7kNvwH9P6O3&_nc_oc=AdlLYdKIYHsidyti51AwEH3IhB31srUZWFM5hMRX0D6EA6O40LLwiLhvdf-Yn8Xvmck&_nc_zt=14&_nc_ht=scontent-lax3-2.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_AfkXDaifq6HezjGjl5efvD0xrm1cnYjcImBJAVUegsG4ww&oe=6955318A)

2: Under _Browse the WhatsApp Template Library_, select **Browse Templates**.

![Image](https://scontent-lax3-1.xx.fbcdn.net/v/t39.2365-6/560898429_1339318461260138_2068693222637029790_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=4sAx7i1w9sMQ7kNvwFwloF0&_nc_oc=Adk_A0foumhmItveybCNl9E22kQMUhLnvo2rGPQFJOyQ_-3UY55oghnM1U3KGTuvTcA&_nc_zt=14&_nc_ht=scontent-lax3-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_AflLCH01Q_Eog7lQkocuk4Ujmtgw2z2qzTcXnPaX-QevwA&oe=6954FD22)

3: You will now see all currently available templates. Use the search bar to search by topic or use case, or use the dropdown options on the sidebar to filter the results.

Note that hovering over a template will show you its parameter values.

![Image](https://scontent-lax7-1.xx.fbcdn.net/v/t39.2365-6/560665283_1339318454593472_1581401886238873208_n.jpg?_nc_cat=101&ccb=1-7&_nc_sid=e280be&_nc_ohc=CfsmSXTpN8wQ7kNvwHrBLNI&_nc_oc=AdmjxVUxIzGDYjBQ1ZRi9hLzoRnkPb5BsN76a_f2A4YkETZxeNOZv_g3T5q28IHj-LE&_nc_zt=14&_nc_ht=scontent-lax7-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_Afkp6vcJQGPXBib9qM-Ch2iaGnjU0tLMVILFMdycs3ASkA&oe=69552599)

4: To create a template, **select one** by clicking on it. Then, add your template name, select the language, and fill out the button details. Once you have completed these steps, click **Submit**.

Note: If you choose **Customize template**, your template will have to go through review before you are able to send messages.

![Image](https://scontent-lax3-1.xx.fbcdn.net/v/t39.2365-6/564202977_1339318004593517_4596535304491755062_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=45UZ5bxkIegQ7kNvwHRdbO8&_nc_oc=Adnivl2Nq1Wma6Uz4IxpYTspL17MPs32a7UY0XCQIz9-McEnZVdzOZKkryPmF78PyIg&_nc_zt=14&_nc_ht=scontent-lax3-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_AfkOxDvv1E7m8b36SWJdJBGZBj2DKqPMlMn5gChoCkjktA&oe=6955145C)

## Template Parameters and Restrictions

When a template contains the value `library_template_name` in the `GET &lt;WABAID&gt;/message_templates?name=&lt;TEMPLATE_NAME&gt;` response, it is a template created from the Template Library and is subject to type checks and restrictions.

![Image](https://scontent-lax3-1.xx.fbcdn.net/v/t39.2365-6/564078988_1339317931260191_355325833187515070_n.jpg?_nc_cat=104&ccb=1-7&_nc_sid=e280be&_nc_ohc=zjR32hsr35sQ7kNvwHdm2RX&_nc_oc=AdnYNX2o2eaAvIXA_KCkae0ndSa657BYyHQea4qfoEgkg8XeU3s0Ym87Sc5FBtxkay0&_nc_zt=14&_nc_ht=scontent-lax3-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_Afl_mPJw5J9B3IU_AwskssEnrkb_DUa5c-eNeaKqByWJ5A&oe=69552AAA)![Image](https://scontent-lax3-1.xx.fbcdn.net/v/t39.2365-6/560193637_1339318421260142_6827805123941026588_n.jpg?_nc_cat=109&ccb=1-7&_nc_sid=e280be&_nc_ohc=hYEMxgw4VAMQ7kNvwHAdOf6&_nc_oc=Adk_HnbR7ik5RdXTYgqIsg3P1-9ItISPEnVhpt5FjqKeF85EMyIgrJtiQnevwxxY5W8&_nc_zt=14&_nc_ht=scontent-lax3-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_AfnYA_Vpo7pi0sp7Qw9SBvzDNg1WyrWuUwUlIMYCkbJFWg&oe=6955215E)

Templates in the library contain both fixed content and parameters. The parameters represent spaces in the template where variable information can be inserted, such as names, addresses, and phone numbers.

In the example above, parameters like the name `Jim` or the business name `CS Mutual` can be modified to accept variables like your customer’s name and your business’s name.

Messages sent using templates from Template Library are subject to parameter checks during send time. Values used in parameters that are outside of the established ranges listed below will cause the message send to fail.

### List of parameters and sample values

All parameters are length restricted. If you receive an error, try again with a shorter value.

| Parameter Type | Description | Sample Value |
| --- | --- | --- |
| `ADDRESS` | A location address.<br />Must be a valid address | `1 Hacker Way, Menlo Park, CA 94025` |
| `TEXT` | Basic text. | `regarding your order.`<br />`12 pack of paper towels`<br />`your request`<br />`purchase`<br />`Jasper's Market` |
| `AMOUNT` | A number signifying a quantity.<br />May contain a prefix or suffix for monetary values such as USD or RS<br />May contain decimals (.) and commas (,)<br />May contain valid currency symbols such as $ and € | `145`<br />`USD $375.32`<br />`€1,376.22 EUR`<br />`RS 1200` |
| `DATE` | A standard calendar date. | `2021-04-19`<br />`13/03/2021`<br />`5th January 1982`<br />`08.22.1991`<br />`January 1st, 2024`<br />`05 12 2022` |
| `PHONE NUMBER` | A telephone number.<br />May contain numbers, spaces, dashes (-), parentheses, and plus symbols (+) | `+1 4256789900`<br />`+91-7884-789122`<br />`+39 87 62232` |
| `EMAIL` | A standard email address.<br />Must be a valid email address | `1hackerway@meta.com`<br />`yourcustomername@gmail.com`<br />`abusinessorcustomername@hotmail.com` |
| `NUMBER` | A number.<br />Must be a number.<br />Cannot contain spaces. | `23444`<br />`90001234921388904`<br />`453638` |

## Forms

Forms are only available to accounts who have had their message limits increased.

![Image](https://scontent-lax3-1.xx.fbcdn.net/v/t39.2365-6/561076760_1339318104593507_1250042269511586117_n.jpg?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=ZB-EZlEYT7cQ7kNvwFk3NCB&_nc_oc=AdnZfmq4XhZtnE95HPE5aSZOLP18rlXLBUfkuT96MWqA2XJrDa0unaMpwKZmPGBmTzY&_nc_zt=14&_nc_ht=scontent-lax3-1.xx&_nc_gid=d-97859b0SJFvSIMXzwTsQ&oh=00_AfnYA8_idRwiNRYEjVtBS4N3W6RtnsglLW432wuPSBPwDA&oe=6954FCD0)

Some templates in Template Library are interactive forms that are powered by WhatsApp Flows.

In WhatsApp Manager, you can identify these specific templates by the “Form” label they contain. The current supported use cases are Customer Feedback and Delivery Failure.

### Identifying forms in the request response

When calling the `GET /message_template_library` endpoint, the `type` key in the `buttons` array will show as `"FORMS"`.

```
{
      "name": "delivery_failed_2_form",
      "language": "en_US",
      "category": "UTILITY",
      "topic": "ORDER_MANAGEMENT",
      "usecase": "DELIVERY_FAILED",
      "industry": [\
        "E_COMMERCE"\
      ],
      "body": "We were unable to deliver order {{1}} today.

Please {{2}} to schedule another delivery attempt.",
      "body_params": [\
        "#12345",\
        "try a redelivery"\
      ],
      "body_param_types": [\
        "TEXT",\
        "TEXT"\
      ],
      "buttons": [\
        {\
          "type": "FLOW",\
          "text": "Reschedule"\
        }\
      ],
      "id": "7138055039625658"
},
```

## Using the API

The Template Library API has two endpoints:

```
// Used to browse available library templates
GET /message_template_library
```

```
// Used when you are ready to create a template from the library.
POST /&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;/message_templates
```

### Searching and Filtering Available Templates

Templates with `Header` parameter types of `Document` only support PDFs

To browse and filter available templates, use the `message_template_library` endpoint.

Once you find the template you are interested in, note the name as you will use it when creating the template via the `POST` method.

### Request Syntax

```
// Get all available templates
GET /message_template_library

// Search for substring
GET /message_template_library?search=&lt;SEARCH_KEY&gt;

// Filter by template topic
GET/message_template_library?topic=&lt;TOPIC&gt;

// Filter by template use case
GET/message_template_library?usecase=&lt;USECASE&gt;

// Filter by template industry
GET/message_template_library?industry=&lt;INDUSTRY&gt;

// Filter by template language
GET/message_template_library?language=&lt;LANGUAGE&gt;
```

### Query String Parameters

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `&lt;SEARCH_KEY&gt;`<br />_String_ | **Optional.**<br />A substring you are searching for in the content, name, header, body, or footer of the template. | `payments` |
| `&lt;TOPIC&gt;`<br />_Enum_ | **Optional.**<br />The topic of the template.<br />See Template Filters below | `ORDER_MANAGEMENT` |
| `&lt;USECASE&gt;`<br />_Enum_ | **Optional.**<br />The use case of the template.<br />See Template Filters below | `SHIPMENT_CONFIRMATION` |
| `&lt;INDUSTRY&gt;`<br />_Enum_ | **Optional.**<br />The industry of the template.<br />See Template Filters below | `E_COMMERCE` |
| `&lt;LANGUAGE&gt;`<br />_Enum_ | **Optional.**<br />The template language locale code.<br />See [Supported Languages](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/supported-languages) | `en_US` |

### Example Request

```
curl 'https://graph.facebook.com/v24.0/102290129340398/message_templates?search="payments"'
-H 'Authorization: Bearer EAAJB...'
```

### Example Response

```
{
      "name": "low_balance_warning_1",
      "language": "en_US",
      "category": "UTILITY",
      "topic": "PAYMENTS",
      "usecase": "LOW_BALANCE_WARNING",
      "industry": [\
        "FINANCIAL_SERVICES"\
      ],
      "header": "Your account balance is low",
      "body": "Hi {{1}},
This is to notify you that your {{2}} in your {{3}} account, ending in {{4}} is below your pre-set {{5}} of {{6}}.
Click the button to deposit more {{7}}.
{{8}}",
      "body_params": [\
        "Jim",\
        "available funds",\
        "CS Mutual checking plus",\
        "1234",\
        "limit",\
        "$75.00",\
        "funds",\
        "CS Mutual"\
      ],
      "buttons": [\
        {\
          "type": "URL",\
          "text": "Make a deposit",\
          "url": "https://www.example.com/"\
        },\
        {\
          "type": "PHONE_NUMBER",\
          "text": "Call us",\
          "phone_number": "+18005551234"\
        }\
      ],
      "id": "7147013345418927"
}
```

### Template Filters

There are several templates to choose from in the Template Library. You can use the API to filter them based on a few factors.

**Industry**

`E_COMMERCE`
`FINANCIAL_SERVICES`

**Topic**

`ACCOUNT_UPDATE`
`CUSTOMER_FEEDBACK`
`ORDER_MANAGEMENT`
`PAYMENTS`

**Use case**

`ACCOUNT_CREATION_CONFIRMATION`
`AUTO_PAY_REMINDER`
`DELIVERY_CONFIRMATION`
`DELIVERY_FAILED`
`DELIVERY_UPDATE`
`FEEDBACK_SURVEY`
`FRAUD_ALERT`
`LOW_BALANCE_WARNING`
`ORDER_ACTION_NEEDED`
`ORDER_CONFIRMATION`
`ORDER_DELAY`
`ORDER_OR_TRANSACTION_CANCEL`
`ORDER_PICK_UP`
`PAYMENT_ACTION_REQUIRED`
`PAYMENT_CONFIRMATION`
`PAYMENT_DUE_REMINDER`
`PAYMENT_OVERDUE`
`PAYMENT_REJECT_FAIL`
`PAYMENT_SCHEDULED`
`RECEIPT_ATTACHMENT`
`RETURN_CONFIRMATION`
`SHIPMENT_CONFIRMATION`
`STATEMENT_ATTACHMENT`
`STATEMENT_AVAILABLE`
`TRANSACTION_ALERT`

## **Creating Templates**

**Note: The modification of rules surrounding body properties for this endpoint is for the explicit purpose of showcasing how to use the endpoint with Template Library.**

To create a new template using the Template Library, call the existing `&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;/message_templates` endpoint using the body properties below.

### Request Syntax

```
POST /&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;/message_templates
```

### Post Body

```
{
  "name": "&lt;NAME&gt;",
  "category": "UTILITY",
  "language": "en_US",
  “library_template_name”: “&lt;LIBRARY_TEMPLATE_NAME&gt;”,
  "library_template_button_inputs": "[\
    {'type': 'URL', 'url': {'base_url' : 'https://www.example.com/{{1}}',\
    'url_suffix_example' : 'https://www.example.com/demo'}},\
    {type: 'PHONE_NUMBER', 'phone_number': '+16315551010'}\
]"
}
```

### Body Properties

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `&lt;NAME&gt;`<br />_String_ | **Required.**<br />The name you are providing for your template.<br />Maximum 512 characters. | `my_payment_template` |
| `&lt;CATEGORY&gt;`<br />_Enum_ | **Required.**<br />The template category.<br />**Must be `UTILITY` for use with Template Library.** | `UTILITY` |
| `&lt;LANGUAGE&gt;`<br />_Enum_ | **Required.**<br />The template language locale code.<br />See [Supported Languages](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/supported-languages) | `en_US` |
| `&lt;LIBRARY_TEMPLATE_NAME&gt;`<br />_String_ | **Required.**<br />The exact name of the Template Library template. | `delivery_update_1` |
| `&lt;LIBRARY_TEMPLATE_BUTTON_INPUTS&gt;`<br />_Array of objects_ | **Optional.**<br />The website and/or phone number of the business being used in the template.<br />**Note: For utility templates that have button inputs, this property is _not_ optional.** | `“[<br />{'type': 'URL', 'url': {'base_url' : 'https://www.example.com/{{1}}',<br />'url_suffix_example' : 'https://www.example.com/demo'}},<br />{type: 'PHONE_NUMBER', 'phone_number': '+16315551010'}<br />]"<br />` |

### Library template button inputs

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `type`<br />_enum_ | The button type<br />`QUICK_REPLY`, `URL`, `PHONE_NUMBER`, `OTP`, `MPM`, `CATALOG`, `FLOW`, `VOICE_CALL`, `APP`<br />_Required_ | `OTP` |
| `phone_number`<br />_String_ | Phone number for the button.<br />_Optional_ | `"+13057652345"` |
| `url`<br />_JSON Object_ | [View JSON object URL parameters `base_url` and `url_suffix_example` here](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/template-api#post-version-waba-id-message-templates)<br />_Optional_ |  |
| `zero_tap_terms_accepted`<br />_boolean_ | Wether the zero tap terms were accepted by the user or not.<br />_Optional_ | `TRUE` |
| `otp_type`<br />_enum_ | The OTP type.<br />`COPY_CODE`, `ONE_TAP`, `ZERO_TAP`<br />_Optional_ | `TRUE` |
| `supported_apps`<br />_Array of JSON Object_ | [View JSON object Supported App parameters `package_name` and `signature_hash` here](https://developers.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/template-api#post-version-waba-id-message-templates)<br />_Optional_ |  |

### Library template body inputs

| Placeholder | Description | Sample Value |
| --- | --- | --- |
| `&lt;LIBRARY_TEMPLATE_BODY_INPUTS&gt;`<br />_JSON Object_ | **Optional.**<br />Optional data during creation of a template from Template Library. These are optional fields for the button component.<br />[_Learn how to create templates using Template Library_](https://developers.facebook.com/docs/whatsapp/cloud-api/guides/send-message-templates/utility-templates) |  |
| `add_contact_number`<br />_boolean_ | Boolean value to add information to the template about contacting business on their phone number.<br />_Optional_ | `TRUE` |
| `add_learn_more_link`<br />_boolean_ | Boolean value to add information to the template about learning more information with a url link.<br />Not widely available and will be ignored if not available.<br />_Optional_ | `TRUE` |
| `add_security_recommendation`<br />_boolean_ | Boolean value to add information to the template about not sharing authentication codes with anyone.<br />_Optional_ | `TRUE` |
| `add_track_package_link`<br />_boolean_ | Boolean value to add information to the template to track delivery packages.<br />Not widely available and will be ignored if not available.<br />_Optional_ | `TRUE` |
| `code_expiration_minutes`<br />_int64_ | Integer value to add information to the template on when the code will expire.<br />_Optional_ | `5` |

### Example Request

```
curl 'https://graph.facebook.com/v19.0/102290129340398/message_templates'
-H 'Authorization: Bearer EAAJB...'
-H 'Content-Type: application/json'
-d '
{
  "name": "my_delivery_update",
  "language": "en_US",
  "category": "UTILITY",
  “library_template_name”: “delivery_update_1”,
  "library_template_button_inputs": "[\
    {'type': 'URL', 'url': {'base_url' : 'https://www.example.com/{{1}}',\
    'url_suffix_example' : 'https://www.example.com/order_update}}\
  ]"
}
```

### Example Response

```
{
  "id": "{hsm-id}",
  "status": "APPROVED",
  "category": "UTILITY"
}
```

## Sending Template Messages

To learn how to send templated messages, view the [Send Templates guide](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/template-messages)

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Creating Templates via WhatsApp Manager (WAM)

Template Parameters and Restrictions

List of parameters and sample values

Forms

Identifying forms in the request response

Using the API

Searching and Filtering Available Templates

Request Syntax

Query String Parameters

Example Request

Example Response

Template Filters

Creating Templates

Request Syntax

Post Body

Body Properties

Library template button inputs

Library template body inputs

Example Request

Example Response

Sending Template Messages

* * *