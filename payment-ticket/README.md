# فلوی تیکت پرداخت

در شرایطی نیاز است تا پرداخت یک افزونه توسط دیوار انجام شود. برای مثال برای کاربری که بلک لیست شده و قصد آزادسازی با احراز را دارد، میخواهیم احراز رایگان صورت پذیرد. در این صورت، نیاز است با پروتکل خاصی این مهم به سرویس پروایدر ارسال شود و به صورت یک فاکتور پرداختی برای دیوار ذخیره شود.
در هنگام باز شدن یک اپ در وب‌ویو یا برازر یک پارامتر به نام `ticket_uuid` در لینک وجود دارد. اگر این پارامتر در کوئری پارام‌های ریکوئست وجود داشت و کاربر تا انتهای فلو را دنبال کرد، باید اندپورینت `validate` پلتفرم دیوار با تیکت مورد نظر فراخوانی شود تا از صحت آن اطمینان حاصل شود. پس از آنکه صحت تیکت پرداخت محرز شد ، کاربر نباید به درگاه پرداخت ارجاع شود. در عوض هنگام ساخت افزونه ی کاربر `USER_ADDON` باید در body ریکوئست فیلد `ticket_uuid` در کنار سایر مقادیر فرستاده شده، قرار داده شود تا این تیکت برای این سرویس پروایدر مصرف شده و فاکتور پرداخت برای آن ساخته شود.

-  [ساخت تیکت توسط اپ های دیوار](generate.md)
-  [اعتبار‌ستجی تیکت توسط سرویس پروایدر ها](validate.md)