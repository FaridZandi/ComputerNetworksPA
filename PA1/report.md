تمرین برنامه‌نویسی شبکه ۱ - گزارش تمرین
=======================================


تغییرات ایجاد شده نسبت به طراحی انجام شده به شرح زیر است.

۱. تابع broadcast یک ورودی به نام set_sender‌ نیز دریافت میکند.

        void broadcast(Frame frame, int exception = -1, bool set_sender = true);

در صورتی که این پارامتر برابر با True‌ باشد قبل از ارسال مک مبدا در سرآیند ethernet‌ را برابر با مک اینترفیسی که ارسال از روی آن انجام میشود قرار میدهد.

در غیر این صورت تغییری در بسته ایجاد نمیکند و صرفا آن را ارسال میکند. در حالتی کاربرد دارد که بخواهیم بسته ای که متعلق به ما نبوده است را روی دیگر اینترفیس ها هم ارسال کنیم که در این حالت نباید تغییری در بسته به وجود بیاید.


۲. تابع set_sender_mac‌ اضافه شده است.

        void set_sender_mac(Frame& frame, int interface);

این تابع یک بسته دریافت کرده و مک مبدا در سرآیند ethernet‌ را برابر با مک اینترفیسی که مشخص شده است قرار میدهد.


۳. در سرور، تابع handle_dhcp_discover یک ورودی interface‌ هم باید داشته باشد که سهوا فراموش شده بود.

        void handle_dhcp_discover(int interface, unsigned int time, byte *mac);

از این عدد استفاده میشود تا بسته dhcpack تنها روی همان اینترفیس ارسال شود.