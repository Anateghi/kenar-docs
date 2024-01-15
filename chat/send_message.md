# ارسال پیام در چت

برنامه‌‌های کنار دیوار می‌توانند پس از کسب اجازه از کاربر، در [یک چت][ارسال پیام در یک چت] یا [چت‌های یک آگهی][ارسال پیام در چت‌های آگهی] پیام ارسال کنند.
پیام‌های ارسالی از طرف کاربری که دسترسی به برنامه را داده و درخواست از سمتش بوده در چت ارسال می‌شود و در قسمت بالای پیام عنوان برنامهٔ مورد نظر نشان داده می‌شود. بنابراین هر دو طرف چت پیام را می‌بینند.

| ![نمایی از یک پیام ارسال شده توسط بات](/img/bot-message.png) |
| :----------------------------------------------------------: |
|   <sub dir="rtl">نمایی از یک پیام ارسال شده توسط بات</sub>   |

> ⭐️ بهتر است پیامی که در چت ارسال می‌کنید برای هر دو طرف معنادار باشد و اطلاعات مفید در راستای خدمت دریافت شده ارائه دهد.

> 🛑 برای مقاصد تبلیغاتی یا معرفی از این امکان استفاده نکنید.

## ارسال پیام در یک چت

| CHAT SEND MESSAGE |                                    |
| ----------------- | ---------------------------------- |
| API Permissions   | CHAT_SEND_MESSAGE_OAUTH            |
| OAuth Permissions | CHAT_SEND_MESSAGE_OAUTH            |
| Resource ID       | BASE64(user_id:post_token:peer_id) |

نمونه برای پارامترهای ارسالی

```
user_id = e9ba8a81-9583-4f7c-af54-b07df089d971
post_token = AZf3Uqr3
peer_id = 1697004f-e902-44c2-bbbe-bf8e20d54bff

resource_id = BASE64(e9ba8a81-9583-4f7c-af54-b07df089d971:AZf3Uqr3:1697004f-e902-44c2-bbbe-bf8e20d54bff) = ZTliYThhODEtOTU4My00ZjdjLWFmNTQtYjA3ZGYwODlkOTcxOkFaZjNVcXIzOjE2OTcwMDRmLWU5MDItNDRjMi1iYmJlLWJmOGUyMGQ1NGJmZg==

Scope:
CHAT_SEND_MESSAGE_OAUTH__ZTliYThhODEtOTU4My00ZjdjLWFmNTQtYjA3ZGYwODlkOTcxOkFaZjNVcXIzOjE2OTcwMDRmLWU5MDItNDRjMi1iYmJlLWJmOGUyMGQ1NGJmZg==
```

## ارسال پیام در چت‌های یک آگهی

| CHAT SEND MESSAGE |                                      |
| ----------------- | ------------------------------------ |
| API Permissions   | CHAT_SEND_MESSAGE_OAUTH              |
| OAuth Permissions | CHAT_SEND_MESSAGE_POST_CONVERSATIONS |
| Resource ID       | post_token                           |

نمونهٔ درخواست ارسالی برای ارسال پیام در یک چت مشخص

```http request
POST https://api.divar.ir/v2/open-platform/chat/conversation
Content-Type: application/json
x-api-key: {{apikey}}
x-access-token: {{access_token}}

{
    "user_id": "شناسهٔ کاربری که می خواهیم پیامی از سمت او وارد چت کنیم",
    "post_token": "توکن آگهی مورد چت",
    "peer_id": "شناسهٔ طرف مقابل در چت",
    "type": "TEXT",
    "message": "متن پیام",
    "sender_btn": {
        "action": "LINK",
        "data": {
            "icon_name": "نام آیکون مورد نظر برای این دکمه",
            "extra_data": {
                "your_custom_key":"اطلاعاتی که در ادامه هنگام کلیک روی دکمه نیاز داریم"
            },
            "caption": "متن دکمهٔ زیر پیام برای طرف فرستنده"
        }
    },
    "receiver_btn": {
        "action": "LINK",
        "data": {
            "icon_name": "نام آیکون مورد نظر برای این دکمه",
            "extra_data": {
                "your_custom_key":"اطلاعاتی که در ادامه هنگام کلیک روی دکمه نیاز داریم"
            },
            "caption": "متن دکمهٔ زیر پیام برای طرف گیرنده"
        }
    }
}
```

نمونهٔ درخواست ارسالی برای ارسال پیام در یک چت مشخص با لینک مستقیم

```http request
POST https://api.divar.ir/v2/open-platform/chat/conversation
Content-Type: application/json
x-api-key: {{apikey}}
x-access-token: {{access_token}}

{
    "user_id": "شناسهٔ کاربری که می خواهیم پیامی از سمت او وارد چت کنیم",
    "post_token": "توکن آگهی مورد چت",
    "peer_id": "شناسهٔ طرف مقابل در چت",
    "type": "TEXT",
    "message": "متن پیام",
    "sender_btn": {
        "action": "DIRECT_LINK",
        "data": {
            "icon_name": "نام آیکون مورد نظر برای این دکمه",
            "direct_link": "آدرس صفحهٔ مورد نظر برای باز شدن هنگام کلیک",
            "caption": "متن دکمهٔ زیر پیام برای طرف فرستنده"
        }
    },
    "receiver_btn": {
        "action": "DIRECT_LINK",
        "data": {
            "icon_name": "نام آیکون مورد نظر برای این دکمه",
            "direct_link": "آدرس صفحهٔ مورد نظر برای باز شدن هنگام کلیک",
            "caption": "متن دکمهٔ زیر پیام برای طرف گیرنده"
        }
    }
}
```

نمونهٔ پاسخ

```json
{
  "status": 200,
  "message": "success"
}
```

## کلیک کاربر روی دکمهٔ درج شده زیر پیام

در صورتی که کاربر روی دکمه‌ای که زیر پیام اضافه کرده‌اید کلیک کند، ابتدا دیوار یک درخواست به آدرسی که در ابتدا تنظیم کرده‌اید می‌زند. [توضیحات بیشتر](/management#session-initialization-url/)

به همراه این درخواست موارد زیر ارسال خواهند شد و سپس کاربر به آدرسی که در دکمهٔ مورد نظر درج شده‌است هدایت می‌شود.

نمونهٔ محتوای ارسالی درخواست از سمت دیوار

```JSON
{
    "extra_data": {
        "provider_data": {"your_custom_key":"اطلاعاتی که در درخواست ارسال پیام در مرحلهٔ قبل فرستادید"},
        "location": {
            "latitude": 35.683374373999364,
            "longitude": 51.34850978851319
        }
    },
    "callback_url": "آدرسی که کاربر پس از انجام فرایند در سرویس شما باید به آن هدایت شود",
    "post_token":   "توکن آگهی",
    "user_id":      "شناسهٔ کسی که روی لینک کلیک کرده یا فرایند را شروع کرده",
    "peer_id":      "شناسهٔ طرف مقابل چت",
    "Supplier": {
        "id": "شناسهٔ کاربر فروشنده (صاحب آگهی)"
    },
    "demand": {
        "id": "شناسهٔ کاربر خریدار"
    }
}

```

> در صورتی که پیام از نوع موقعیت مکانی باشد اطلاعات مرتبط به آن موقعیت در مقدار `location` قرار می‌گیرد.
> در پاسخ به این درخواست دیوار شما باید چنین پاسخی به دیوار بدهید تا کاربر به آدرس مورد نظر شما هدایت شود.

```
{
"status": "http status code (200, 400, ...)",
"message": "string",
"url": "https://yourapp.com/divar/will/redirect/user/here"
}
```

برای گرفتن شماره تماس کاربر می‌توانید از [احراز باز](/oauth/) و توضیحات [درخواست شماره تماس](oauth/get_user.md) استفاده کنید.

[ارسال پیام در یک چت]: #ارسال-پیام-در-یک-چت
[ارسال پیام در چت‌های آگهی]: #ارسال-پیام-در-چتهای-یک-آگهی

<br><br>

<div align="center">

<img src="/img/wire-puzzle-dark.svg#gh-dark-mode-only" height="156px"/>
<img src="/img/wire-puzzle-light.svg#gh-light-mode-only" height="156px"/>

</div>

<br><br>
