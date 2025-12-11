
# Media

Updated: Dec 2, 2025

You use 4 different endpoints to manage your media:

| Endpoint | Uses |
| --- | --- |
| [`POST /PHONE_NUMBER_ID/media`](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#upload-media) | Upload media. |
| [`GET /MEDIA_ID`](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#get-media-url) | Retrieve the URL for a specific media. |
| [`DELETE /MEDIA_ID`](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#delete-media) | Delete a specific media. |
| [`GET /MEDIA_URL`](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#download-media) | Download media from a media URL. |

See [Supported Media Types](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#supported-media-types) for supported types and size limits.

## Get media ID

Some of the API requests described in this document require a media ID. Media IDs are returned by the API when [uploading media](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#upload-media), and are included in incoming media messages webhooks ( [image messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/image), [video messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/video), etc.)

Media IDs returned by the API expire after 30 days. Media IDs in webhooks expire after 7 days.

## Upload media

To upload media, make a `POST` call to `/PHONE_NUMBER_ID/media` and include the parameters listed below. All media files sent through this endpoint are encrypted and persist for 30 days, unless they are deleted earlier.

| Endpoint | Authentication |
| --- | --- |
| `/PHONE_NUMBER_ID/media`<br />(See [Get Phone Number ID](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/phone-numbers#get-all-phone-numbers)) | Developers can authenticate their API calls with the access token generated in the **App Dashboard** \> **WhatsApp** \> **API Setup**.<br />Solution Partners must authenticate themselves with an access token with the `whatsapp_business_messaging` permission. |

### Parameters

| Name | Description |
| --- | --- |
| `file` | **Required.**<br />Path to the file stored in your local directory. For example: “@/local/path/file.jpg”. |
| `type` | **Required.**<br />Type of media file being uploaded. See [Supported Media Types](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#supported-media-types) for more information. |
| `messaging_product` | **Required.**<br />Messaging service used for the request. In this case, use `whatsapp`. |

### Request

```
curl 'https://graph.facebook.com/&lt;API_VERSION&gt;/&lt;PHONE_NUMBER_ID&gt;/media' \
-H 'Authorization: Bearer &lt;ACCESS_TOKEN&gt;' \
-F 'messaging_product=whatsapp' \
-F 'file=@&lt;FILE_PATH_AND_NAME&gt;;type=&lt;MIME_TYPE&gt;'
```

### Response

Upon success:

```
{
  "id": "&lt;MEDIA_ID&gt;"
}
```

### Example request

```
curl 'https://graph.facebook.com/v24.0/106540352242922/media' \
-H 'Authorization: Bearer EAAJB...' \
-F 'messaging_product=whatsapp' \
-F 'file=@/media/template_assets/black_friday_2025.mp4;type=video/mp4'
```

### Example response

```
{
  "id": "1037543291543636"
}
```

## Get media URL

You can query a [media ID](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#get-media-id) directly to get a media URL, which you can then query directly with your access token to [download the media asset](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#download-media).

Starting November 12, 2025, incoming media messages webhooks ( [image messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/image), [video messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/webhooks/reference/messages/video), etc.) will include the media url automatically, and assign it to a new `url` property. **This property is being released to developers gradually over several weeks, so may not be available to you immediately.**

Media URLs **expire after 5 minutes**, after which you must query the ID again to get a new URL.

### Request syntax

```
curl 'https://graph.facebook.com/&lt;API_VERSION&gt;/&lt;MEDIA_ID&gt;?phone_number_id=&lt;BUSINESS_PHONE_NUMBER_ID&gt;' \
-H 'Authorization: Bearer EAAJB'
```

Note that `phone_number_id` is optional. If included, the request will only be processed if the business phone number ID included in the query matches the ID of the business phone number that the media was uploaded on.

### Response syntax

A successful response includes an object with a media url. The URL is only valid for 5 minutes. To use this URL, see [Download Media](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#download-media).

```
{
  "messaging_product": "whatsapp",
  "url": "&lt;MEDIA_URL&gt;",
  "mime_type": "&lt;MEDIA_MIME_TYPE&gt;",
  "sha256": "<SHA_256_HASH>",
  "file_size": "&lt;MEDIA_FILE_SIZE&gt;",
  "id": "&lt;MEDIA_ID&gt;"
}
```

## Delete media

Use the **DELETE /&lt;MEDIA_ID&gt;** endpoint to delete a media asset.

### Request syntax

```
curl -X DELETE 'https://graph.facebook.com/&lt;API_VERSION&gt;/&lt;MEDIA_ID&gt;?phone_number_id=&lt;BUSINESS_PHONE_NUMBER_ID&gt;' \
-H 'Authorization: Bearer EAAJB...'
```

Note that `phone_number_id` is optional. If included, the request will only be processed if the business phone number ID included in the query matches the ID of the business phone number that the media was uploaded on.

### Example response

```
{
  "success": true
}
```

## Download media

To download media, make a `GET` request on the media URL and include your access token. **If you omit your token, the request will fail.**

Note that when retrieving a media from a media ID received via webhook, the media ID will only be available to download for 7 days.

### Request syntax

```
curl '&lt;MEDIA_URL&gt;' \
-H 'Authorization: Bearer EAAJB...' \
-o '&lt;DESIRED_FILE_NAME&gt;'
```

Upon success, the API will respond with the binary data of the media asset. Response headers contain a content-type header to indicate the mime type of returned data. Check [supported media types](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#supported-media-types) for supported media types.

If the download attempt fails, you will receive a `404 Not Found` response code. In that case, we recommend you try to [get a new media URL](https://developers.facebook.com/documentation/business-messaging/whatsapp/business-phone-numbers/media#get-media-url) and download it again. If doing so doesn’t resolve the issue, renew your access token and attempt to download the media asset again.

## Supported media types

### Audio

| Audio Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| AAC | .aac | audio/aac | 16 MB |
| AMR | .amr | audio/amr | 16 MB |
| MP3 | .mp3 | audio/mpeg | 16 MB |
| MP4 Audio | .m4a | audio/mp4 | 16 MB |
| OGG Audio | .ogg | audio/ogg (OPUS codecs only; base audio/ogg not supported; mono input only) | 16 MB |

### Document

| Document Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Text | .txt | text/plain | 100 MB |
| Microsoft Excel | .xls | application/vnd.ms-excel | 100 MB |
| Microsoft Excel | .xlsx | application/vnd.openxmlformats-officedocument.spreadsheetml.sheet | 100 MB |
| Microsoft Word | .doc | application/msword | 100 MB |
| Microsoft Word | .docx | application/vnd.openxmlformats-officedocument.wordprocessingml.document | 100 MB |
| Microsoft PowerPoint | .ppt | application/vnd.ms-powerpoint | 100 MB |
| Microsoft PowerPoint | .pptx | application/vnd.openxmlformats-officedocument.presentationml.presentation | 100 MB |
| PDF | .pdf | application/pdf | 100 MB |

### Image

Images must be 8-bit, RGB or RGBA.

| Image Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| JPEG | .jpeg | image/jpeg | 5 MB |
| PNG | .png | image/png | 5 MB |

### Sticker

WebP images can only be sent in [sticker messages](https://developers.facebook.com/documentation/business-messaging/whatsapp/messages/sticker-messages).

| Sticker Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| Animated sticker | .webp | image/webp | 500 KB |
| Static sticker | .webp | image/webp | 100 KB |

### Video

Only H.264 video codec and AAC audio codec supported. Single audio stream or no audio stream only.

Note that videos encoded with the H.264 “High” profile and B-frames are not supported by Android WhatsApp clients. We recommend that you use H.264 “Main” profile without B-frames, or the H.264 “Baseline” profile when encoding (or re-encoding with a tool like ffmpeg), and place moov boxes before mdat boxes, for broader compatibility. If you are using ffmpeg, you can use the -movflags faststart flag to place moov boxes before mdata boxes.

| Video Type | Extension | MIME Type | Max Size |
| --- | --- | --- | --- |
| 3GPP | .3gp | video/3gpp | 16 MB |
| MP4 Video | .mp4 | video/mp4 | 16 MB |

Note that mismatched MIME type (`131053`) is a common error. We recommend that you inspect your media files to verify their MIME type, and make sure that your file name extensions reflect their types. For example, if you are using UNIX, you can inspect a file via the command line to determine its MIME type:

`file -I your-image-asset.png`

## Media message download constraints

The maximum supported file size for media messages on Cloud API is 100MB. In the event the customer sends a file that is greater than 100MB, you will receive a webhook with error code [131052](https://developers.facebook.com/documentation/business-messaging/whatsapp/support/error-codes#other-errors) and `title`:

_“Media file size too big. Max file size we currently support: 100MB. Please communicate with your customer to send a media file that is smaller than 100MB”_.

We advise that you send customers a warning message that their media file exceeds the maximum file size when this webhook event is triggered.

## Learn more

WhatsApp Business Blog – [Sending WhatsApp media messages from an app](https://l.facebook.com/l.php?u=https%3A%2F%2Fbusiness.whatsapp.com%2Fblog%2Fmedia-messages-via-app&h=AT2BYyqQfD4-PMuTTY-c1nWYBdMWPsBfv5tL_YLSPwr0jCJQkzOfQfobxZeRfvXzJJU4eXyJYqXr2k7eE9FpYczw12PVdhIoI-yWH9Bm7LfBjuHMLLVKS0LeOIx9VMGhViFcxfijo1JoCw)

Did you find this page helpful?

![Thumbs up icon](https://static.xx.fbcdn.net/rsrc.php/yR/r/OEXJ0_DJeZv.svg)

![Thumbs down icon](https://static.xx.fbcdn.net/rsrc.php/yb/r/qKPgNVNeatU.svg)

ON THIS PAGE

Get media ID

Upload media

Parameters

Request

Response

Example request

Example response

Get media URL

Request syntax

Response syntax

Delete media

Request syntax

Example response

Download media

Request syntax

Supported media types

Audio

Document

Image

Sticker

Video

Media message download constraints

Learn more

* * *