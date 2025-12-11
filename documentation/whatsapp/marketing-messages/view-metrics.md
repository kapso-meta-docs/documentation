
# Viewing metrics

Updated: Dec 10, 2025

Marketing Messages API for WhatsApp (formerly known as Marketing Messages Lite API) is now generally available.

Conversion metrics will be solely available in the WhatsApp Manager UI and WhatsApp Business Management API that businesses use with Cloud API in October 2025.

As a result, the following conversion metrics will be depreciated:

Viewing conversion metrics via Ads Manager UI ( **September 8th, 2025**).
Viewing conversion metrics via Ads Insights API ( **Q1 2026**).

Businesses that use Marketing Messages API for WhatsApp can view metrics from 4 surfaces:

Via WhatsApp Business Platform surfaces
WhatsApp Manager UI
[WhatsApp Business Management API](https://developers.facebook.com/documentation/business-messaging/whatsapp/about-the-platform#whatsapp-business-management-api)
Via Ads surfaces (optional)
Ads Manager UI “Marketing Messages” tab
Marketing API “ [Insights API](https://developers.facebook.com/docs/marketing-api/insights)”

| ROI Reporting | WhatsApp Business Management surfaces | Ads surfaces |
| --- | --- | --- |
| Messages sent, delivered, read | Y | Y |
| Total amount spent | Y | Y |
| Cost per delivery | Y | Y |
| CTA URL link clicks | Y | Y |
| Cost per click | Y | Y |
| CTA URL link click rate | N | Y |
| Add to cart (Web + App) | Y | Y`*` |
| Checkout initiated (Web + App) | Y | Y`*` |
| Purchase, purchase value (Web + App) | Y | Y`*` |
| App Activations | Y | Y`*` |
| Quick Replies | N | N |

`*` Requires a business to report this conversion event via Meta Pixel or Conversions API for App Events [see Get started with the Meta Pixel and Conversions API](https://l.facebook.com/l.php?u=https%3A%2F%2Fwww.facebookblueprint.com%2Fstudent%2Factivity%2F212737&h=AT1vf1SMczbVCKTsTiv0uwBlrNSArcyHt1_YSLM-Lqjc6ZtHEDDUCZ3qbuoWMly67Kq47dBTKv5bKr2wtoCquazWlO0tEEDDFrJTtVsIiVh9Legyza6G3mvOR_DLGy_OFsg8soFlL7UBpA).

## View metrics via UIs

After sending Marketing Messages via Marketing Messages API for WhatsApp, view read-only metrics on sends, clicks, and conversions from two UIs:

WhatsApp Manager (does not include conversions)
Ads Manager “Marketing Messages” tab (includes conversions)

Marketing Messages API for WhatsApp metrics (not including conversions), can be viewed in WhatsApp Manager on both Phone Number and Template screens:

![](https://scontent-fra5-2.xx.fbcdn.net/v/t39.2365-6/476092006_1150702876444748_6174975982108219980_n.png?_nc_cat=106&ccb=1-7&_nc_sid=e280be&_nc_ohc=NjJ85H00f0cQ7kNvwGYBYdI&_nc_oc=Adn4kkImWRxdXsXHlZYOnNXTeBm2r9mTFLwPI1MVUdJzsS1umvR56ZwX7XdNpFVxYT4&_nc_zt=14&_nc_ht=scontent-fra5-2.xx&_nc_gid=-2O4iu0txcvtmOX6iJbWQw&oh=00_AfklqtBsVLvvakXUEpENB8rgayJU5jYcWQtho_ao66Z5tA&oe=695522AC)

### Benchmarks and recommendations metrics

Benchmark metrics provide insights into how your business is performing compared to similar businesses in your industry. These metrics are based on data from the past 30 days and take into account various factors that define similar businesses. Based on the benchmark metrics, we provide personalized recommendations to help you improve your template’s performance. If your template’s read rate or click rate falls below the benchmark, we provide suggestions to boost engagement.

### Calculating benchmarks

To calculate benchmark metrics, we consider the following characteristics:

**Business Country or Region**: We use the business country as the default cohort, but if the cohort size is too small, we switch to the business region.
**Business Industry**: We compare your business with others in the same industry or vertical to provide relevant benchmarks.
**Template Categories**: We only compare templates within the same category (e.g., marketing templates with other marketing templates) to ensure accurate and relevant benchmarks.

We then calculate two key benchmark metrics:

**Read Rate Benchmark**: We calculate this metric as the 75th percentile of read rates across similar businesses, representing the percentage of messages read out of total messages delivered.
**Click Rate Benchmark**: We calculate this metric as the 75th percentile of click rates across similar businesses, representing the percentage of link clicks out of total messages delivered.

### Understanding your ranking and how to use benchmark metrics

When you view your benchmark metrics, you will see a ranking that indicates how your template performs compared to templates in the same category. This ranking is calculated by comparing your template’s performance with the read rate or click rate performance of peer templates with high engagement over the past 30 days.

Use the benchmark metrics to compare your template’s performance to templates from similar businesses over the past 30 days. Benchmarks are calculated daily, with a delay of up to 2 days. This ensures that you have access to updated and relevant data to inform your business decisions.

To access the benchmark and recommendations metrics:

Go to the WhatsApp Manager and select “Manage templates”.
Choose the template you want to view.
Select the “Marketing Messages API for WhatsApp” option from the dropdown menu highlighted in red.
The benchmark metrics and recommendation cards will be displayed below the preview card in the left panel.

![](https://scontent-fra3-1.xx.fbcdn.net/v/t39.2365-6/489606125_1614641949479830_5793009593844219233_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=gcY6xgwohYYQ7kNvwG-Ripo&_nc_oc=Adm-LAZJWORQS6sNj4n2bpxBB-SuzIk19daPvNinIvDH1aFKUZrEmGKcQMgm9eawvgk&_nc_zt=14&_nc_ht=scontent-fra3-1.xx&_nc_gid=-2O4iu0txcvtmOX6iJbWQw&oh=00_Afnw0XAIc8ZJBKAQhc9ZcJszXVN1DTzCUPXm8WyW06mbOg&oe=69550D4B)

### Error metrics

You can see a summary of error messages your template encountered within a given period of time by navigating to the [**WhatsApp Manager**](https://business.facebook.com/latest/whatsapp_manager/) \> **Message templates** \> **Manage templates** panel and clicking on the template. Errors are displayed in the **Error messages** section.

![](https://scontent-fra3-1.xx.fbcdn.net/v/t39.2365-6/494916197_1372780987177522_8462538949406730249_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=zoh6I8g2X9QQ7kNvwHR7rpF&_nc_oc=Adkk7B6pI6uixac3HQnaVPPChXZz8wZSnRBj2u1T-dHI0dcz5dlJCCkk2WQvS00UAYE&_nc_zt=14&_nc_ht=scontent-fra3-1.xx&_nc_gid=-2O4iu0txcvtmOX6iJbWQw&oh=00_AfnFSjYIt9B7pQjIfJGuTP7e9Cfr0gXrbx0ATEbUzSKOog&oe=69552923)

The period of time can be defined using the date selector dropdown at the top of the page. See [Cloud API error codes](https://developers.facebook.com/documentation/business-messaging/whatsapp/support/error-codes) for a list of error codes and their descriptions.

The most frequently encountered message delivery errors are displayed in the **Summary** tab:

![](https://scontent-fra3-1.xx.fbcdn.net/v/t39.2365-6/494939750_1018419840401159_1265335467156200602_n.png?_nc_cat=105&ccb=1-7&_nc_sid=e280be&_nc_ohc=XR7x51-9td0Q7kNvwHwykJ8&_nc_oc=Adl8wckrtYHYfzg4bBzzG69_wZk63xjvF4_AEOuPQc5oMetnl2DxZipSzz7EGiCFmLI&_nc_zt=14&_nc_ht=scontent-fra3-1.xx&_nc_gid=-2O4iu0txcvtmOX6iJbWQw&oh=00_AfkvRqYSw6T11ZYbiDA73kG-xCGyJjUEgt7xiUW0sWyp3g&oe=69550756)

This information is also displayed as trend lines in the **Trend** tab:

![](https://scontent-fra5-1.xx.fbcdn.net/v/t39.2365-6/495675967_1251270636408181_5159031297095990508_n.png?_nc_cat=110&ccb=1-7&_nc_sid=e280be&_nc_ohc=Fw7G8Y3xBdkQ7kNvwEl7jN9&_nc_oc=AdkuMlC3JkTCHniu5hjfBwpGYmP-yTXoE8NC75EBi9AnYxRIELRqbkBmPgTnnbnG7FI&_nc_zt=14&_nc_ht=scontent-fra5-1.xx&_nc_gid=-2O4iu0txcvtmOX6iJbWQw&oh=00_AflmXoKvlvh8mOq7I0ShsTyAgtn-DZ2APw897lZlTj62_g&oe=6954F9E8)

## View metrics via APIs

After registering in Marketing Messages API for WhatsApp, analytics for a business’s marketing message templates sent via the API are available from two APIs:

The WhatsApp Business Management API (does not include conversions)
The Marketing API “Insights API” (includes conversions)

### Benchmark metrics

You can get benchmark metrics via Insights API for read rates and click rates by requesting the following fields:

`marketing_messages_read_rate_benchmark`
`marketing_messages_click_rate_benchmark`

#### Syntax

```
curl
'https://graph.facebook.com/&lt;API_VERSION&gt;/&lt;AD_GROUP_ID&gt;/insights?fields=&lt;METRICS&gt;' \
-H 'Authorization: Bearer &lt;ACCESS_TOKEN&gt;'
```

#### Example query

This example query returns the number of messages read, their read rate, and the benchmark read rate for comparison, as well as the number of button link clicks, their click rate, and the benchmark click rate for comparison, with a default lookback of 30 days:

```
curl 'https://graph.facebook.com/v17.0/120229306178900226/insights?fields=marketing_messages_read,marketing_messages_read_rate,marketing_messages_read_rate_benchmark,marketing_messages_link_btn_click,marketing_messages_link_btn_click_rate,marketing_messages_click_rate_benchmark' \
-H 'Authorization: Bearer EAACE...'
```

#### Example response

```
{
  "data": [\
    {\
      "date_start": "2025-05-11",\
      "date_stop": "2025-06-09",\
      "marketing_messages_read": "265",\
      "marketing_messages_read_rate": "481.818182",\
      "marketing_messages_read_rate_benchmark": "70.27",\
      "marketing_messages_link_btn_click": "59",\
      "marketing_messages_link_btn_click_rate": "107.272727",\
      "marketing_messages_click_rate_benchmark": "18.74"\
    }\
  ],
  "paging": {
    "cursors": {
      "after": "MAZDZD",
      "before": "MAZDZD"
    }
  }
}
```

### Measuring ROI with the Marketing API “Insights API” endpoint (richer analytics, recommended)

Businesses can use the [Meta Pixel](https://www.facebook.com/business/tools/meta-pixel) and [Conversions API for App Events](https://developers.facebook.com/docs/marketing-api/conversions-api/app-events) to send signals to Meta when customers take an action on their website or app, after clicking a URL in a marketing message. Note that in-thread conversion optimizations and reporting are not yet available for Marketing Messages API for WhatsApp.

The [Insights API](https://developers.facebook.com/docs/marketing-api/insights) is an interface to retrieve ads statistics, allowing a business to view all of the metrics of the Template Analytics plus additional metrics on when marketing messages sent via Marketing Messages API for WhatsApp led to an event reported from their website via Meta Pixel or Conversions API, like a user adding to cart or checking out. **It is required that the business that owns the Pixel is the same business that owns the WABA.**

#### Step 1) Fetch Ad IDs for Templates, using the Templates endpoint

When a business has registered for Marketing Messages API for WhatsApp, a read-only Ad account will be created for each WABA under their BMID, and any marketing message templates under the WABA will be linked to an Ad object in that Ad account. Each marketing message template under the WABA will also be linked to an Ad set. These IDs are needed when calling the Insights API to retrieve metrics on marketing campaigns sent via Marketing Messages API for WhatsApp.

Once a business has registered for the Marketing Messages API for WhatsApp, the Business Management API’s Template endpoint will return an additional parameter reflecting their Ad IDs.

`ad_id`
`ad_account_id`
`ad_campaign_id`
`ad_adset_id`

These fields indicate the Ad id of linked Ads object for each marketing message template.

Call the Template endpoint to retrieve the Ad IDs for each ad entity linked to marketing message templates, for calling the Insights API later.

| Endpoint | Authentication |
| --- | --- |
| `/WHATSAPP_BUSINESS_ACCOUNT_ID/message_templates` | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.<br />Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_messaging` permission. |

Request Syntax

```
GET /&lt;WHATSAPP_BUSINESS_ACCOUNT_ID&gt;/message_templates
  ?fields=category,ad_id,ad_adset_id,ad_campaign_id,ad_account_id
```

See docs: [GET Message Templates](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/overview#retrieve-templates)

If you only want to fetch 1 Template at a time, you can fetch the Ad ID fields at a Template level.

| Endpoint | Authentication |
| --- | --- |
| `/&lt;TEMPLATE_ID&gt;/` | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.<br />Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_management` permission. |

Request Syntax

```
GET /&lt;TEMPLATE_ID&gt;
  ?fields=category,ad_id,ad_adset_id,ad_campaign_id,ad_account_id
```

See docs: [GET Templates](https://developers.intern.facebook.com/documentation/business-messaging/whatsapp/reference/whatsapp-business-account/template-api#fields)

#### Step 2) Call the Insights API using the Ad IDs

Direct integrators or business messaging partners retrieve these read-only campaign objects through the existing Insights API endpoints:

| Endpoint | Authentication |
| --- | --- |
| `/AD_CAMPAIGN_ID/insights` | Partners must authenticate themselves with an access token with the `ads_read` permission. |

Get the specified metrics for at an ad object level (i.e., ad account, campaign, ad set, or ad id) given its ID:

### Example Request

```
curl --verbose -s -G -d "access_token=${ACCESS_TOKEN}" https://graph.facebook.com/v19.0/${AD_ACCOUNT_ID|CAMPAIGN_ID|AD_SET_ID|AD_ID}/insights?fields=marketing_messages_sent%2Cmarketing_messages_read"
```

### Example Response

```
{
  "data": [\
    {\
      "marketing_messages_sent": "2",\
      "marketing_messages_read": "1",\
      "date_start": "2023-09-24",\
      "date_stop": "2023-10-23"\
    }\
  ],
  "paging": {
    "cursors": {
      "before": "MAZDZD",
      "after": "MAZDZD"
    }
  }
}
```

This is only an example. For all available params of the API see the full doc: [Insights API docs](https://developers.facebook.com/docs/marketing-api/insights)

All available insights fields are listed below:

Sent, Read, Delivered, Click
marketing_messages_sent
marketing_messages_read
marketing_messages_delivered
marketing_messages_link_btn_click
Rates
marketing_messages_delivery_rate
marketing_messages_read_rate
marketing_messages_link_btn_click_rate
Spend metrics
marketing_messages_spend
marketing_messages_cost_per_delivered
marketing_messages_cost_per_link_btn_click
Conversion events
marketing_messages_website_add_to_cart
marketing_messages_website_initiate_checkout
marketing_messages_website_purchase
marketing_messages_website_purchase_values
marketing_messages_app_add_to_cart
marketing_messages_app_initiate_checkout
marketing_messages_app_purchase
marketing_messages_app_purchase_values

### Measuring ROI with the WhatsApp Business Management API “Template Analytics” endpoint (basic analytics)

The [Template Analytics](https://developers.facebook.com/documentation/business-messaging/whatsapp/analytics#template-analytics) endpoint of the WhatsApp Business Management API offers the ability to view metrics including: Sent, Delivered, Read, Clicked, and Cost.

In order to fetch metrics for messages sent via Marketing Messages API for WhatsApp, attach the new parameter “product_type” with the value below. If omitted, only analytics for Cloud API will be returned.

| Endpoint | Authentication |
| --- | --- |
| `/WHATSAPP_BUSINESS_ACCOUNT_ID/conversation_analytics`<br />Use the query parameter `conversation_categories` = `MARKETING_MESSAGES` to include data from the Marketing Messages API for WhatsApp.<br />If omitted, the API will return results for all conversation categories. | Developers can authenticate their API calls with the access token generated in the **App Dashboard > WhatsApp > API Setup**.<br />Business messaging partners must authenticate themselves with an access token with the `whatsapp_business_management` permission. |

Request Syntax

```
GET /WHATSAPP_BUSINESS_ACCOUNT_ID/?fields=conversation_analytics.start(&lt;START_TIMESTAMP&gt;).end(&lt;END_TIMESTAMP&gt;).granularity(DAILY).conversation_categories(MARKETING_LITE).dimensions(["CONVERSATION_CATEGORY"])
```

See docs: [GET Conversation Analytics](https://developers.facebook.com/documentation/business-messaging/whatsapp/analytics#conversation-analytics)

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

View metrics via UIs

Benchmarks and recommendations metrics

Calculating benchmarks

Understanding your ranking and how to use benchmark metrics

Error metrics

View metrics via APIs

Benchmark metrics

Syntax

Example query

Example response

Measuring ROI with the Marketing API “Insights API” endpoint (richer analytics, recommended)

Step 1) Fetch Ad IDs for Templates, using the Templates endpoint

Step 2) Call the Insights API using the Ad IDs

Example Request

Example Response

Measuring ROI with the WhatsApp Business Management API “Template Analytics” endpoint (basic analytics)

* * *