
# Template pausing

Updated: Oct 22, 2025

If a message template reaches the lowest quality rating (a status of **Active - Low quality** in WhatsApp Manager, or a `quality_score` of `RED` via API), it will automatically be paused for a period of time to protect the quality rating of phone numbers that have used the template. Pausing durations are as follows:

1st Instance: Paused for 3 hours
2nd Instance: Paused for 6 hours
3rd Instance: Disabled

When a message template is paused (status of **Paused**) it can’t be sent to customers, so you should halt any automated messaging campaigns that rely on that template. Although you won’t be charged for attempting to send a paused message template to a customer, and the attempt won’t count against your messaging limit, the API will reject these attempts anyway. You should only resume these campaigns when the template’s status has been set to Active again.

You may wish to edit a paused template if you feel that editing its content will reduce the amount of negative feedback it may receive and increase user engagement. Keep in mind, however, that once you edit a message template and resubmit it for approval, its status will change to In Review and it can’t be sent to customers again until it has been re-approved and its status set to Active.

You may also wish to make changes to your business logic (targeting, delivery parameters, etc.) if you feel it is contributing to negative feedback or low engagement.

Pausing will initially not impact the business phone number from which the message template was sent. Other high quality message templates can continue to be sent from the phone number. However, if a business consistently sends message templates that reach a Low quality status, the phone number may eventually be impacted.

## Pause Notifications

When a message template has been paused we will notify you by WhatsApp Manager notification, email, and a [message_template_status_update](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/message_template_status_update) webhook will be triggered.

### Unpausing

A template will unpause on its own after satisfying the pause duration outlined above. Once unpaused, the template’s status will be set to **Active** and you may begin sending it to customers again. If you didn’t halt any automated messaging campaigns that relied on a paused template, they should start working again. However, we recommend that you halt any campaigns that rely on a template that has been paused until it is unpaused, because our APIs will reject your requests anyway.

The template’s [quality rating](https://developers.facebook.com/documentation/business-messaging/whatsapp/templates/template-quality) will also be reset to a value based on the most recent customer feedback the template has received.

Similar to pause notifications, we will notify you by WhatsApp Manager notification, email, and webhook once the template’s status has been set to Active.

Applies to businesses in Brazil, Colombia, and Singapore, starting September 12, 2023. Applies to all businesses starting October 12, 2023.

With the introduction of Template Pacing, we’re also introducing the ability to unpause any paused template through:

The API by making a POST request to `/{whats_app_message_template_id}/unpause`
WhatsApp Manager by clicking the **manually unpause it** link highlighted in the screenshots below.

Note that templates paused during Template Pacing must be manually unpaused (API or WhatsApp Manager) before they can be used again.

![](https://scontent-lax3-2.xx.fbcdn.net/v/t39.2365-6/554797102_3175363515964237_8084410644890844296_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=yBUXhHG94WwQ7kNvwFRPJ1p&_nc_oc=AdlKq44VhaQMr0brmoQmIZS9PuVr0uEINKf8LvnCcnpXSr10ffdHFgQsAaGB3Qhb3nE&_nc_zt=14&_nc_ht=scontent-lax3-2.xx&_nc_gid=G1OxoBl6REX4IRMpjzgwKg&oh=00_Afly4CPSl_RmXU5DnKwJrBkjMJyOr3d9uLePYClHa1D69g&oe=6954FB58)

![](https://scontent-lax3-2.xx.fbcdn.net/v/t39.2365-6/554106571_1492926028278417_4141428697407616298_n.png?_nc_cat=107&ccb=1-7&_nc_sid=e280be&_nc_ohc=EmvGVaMtNJUQ7kNvwETFp_e&_nc_oc=AdkhKKY8IebX0BPN85mOuSMI0fhjriS7I6MiS0VA374uaObMOI9ygJNa4HDHktZUvpk&_nc_zt=14&_nc_ht=scontent-lax3-2.xx&_nc_gid=G1OxoBl6REX4IRMpjzgwKg&oh=00_AfnPmat1wZ4JDpLwFb6q_xnKGoW8iperDEJdl-i2AI-CqQ&oe=69550B51)

### Appeals

If your submission is rejected you may file an appeal. Note that appeals must include a sample. If an approved template has become disabled, you may also edit it and resubmit it for approval.

In the WhatsApp Manager:

Mouseover the suitcase icon ( **Account tools**) and click **Message templates**.
If you have multiple WhatsApp Business Accounts, use the dropdown menu in the top-right corner to select the account whose templates you want to manage.
Find the message template that you would like to edit and click it.
Edit the template’s contents.
Click the **Add Sample** button and add sample variable values and images.
Click **Submit**.

The appeal will be reviewed and a decision made within 24 hours.

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Pause Notifications

Unpausing

Appeals

* * *