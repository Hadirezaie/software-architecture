# راهنمای حذف ICCIDها از دیتابیس PostgreSQL با اسکریپت Bash

---

## 1. بررسی فایل iccids.txt

- این فایل باید به این شکل باشد (هر خط یک iccid، بدون هدر):

فرض کن این فایل الان تو پوشه خانه کاربری که باهاش لاگین هستی، یعنی /home/abc/iccids.txt هست.

2. نوشتن اسکریپت bash

   یک فایل متنی جدید بساز به نام delete_iccids.sh

   nano delete_iccids.sh

متن زیر را داخلش کپی کن (با تنظیمات دیتابیس خودت جایگزین کن):

#!/bin/bash

DB_NAME="dbName"
DB_USER="postgres"
TABLE_NAME="TABLE_NAME"
ICCIDS_FILE="/home/abc/iccids.txt"
export PGPASSWORD='postgresPass' # پسورد دیتابیس را اینجا بگذار

while IFS= read -r iccid; do
if [[! -z "$iccid"]]; then
echo "Deleting ICCID: $iccid"
    psql -U "$DB_USER" -d "$DB_NAME" -c "DELETE FROM $TABLE_NAME WHERE iccid = '$iccid';"
fi
done < "$ICCIDS_FILE"

حالا فایل رو ذخیره و خارج شو (در nano با Ctrl+O سپس Enter و بعد Ctrl+X).

3.  آماده‌سازی اسکریپت برای اجرا

    به ترمینال برگرد و این دستور را بزن تا فایل قابل اجرا شود:

    chmod +x delete_iccids.sh

4.  اجرای اسکریپت

    حالا برای اجرای اسکریپت، ساده بنویس:

    ./delete_iccids.sh

NOTE:

مشکل احتمالی اتصال به PostgreSQL

اگر موقع اجرا خطایی مثل این دریافت کردی:

FATAL: Peer authentication failed for user "postgres"

یعنی PostgreSQL نمی‌تواند به خاطر تنظیمات امنیتی سیستم به درستی وصل شود.

برای حل این مشکل:
روش اول: اجرای اسکریپت به عنوان کاربر postgres در سیستم

    دستور زیر را بزن (پسورد کاربر لینوکسی abc را وارد کن):

    sudo -i -u postgres

حالا مسیر اسکریپت را به یاد داشته باش. اگر اسکریپت در /home/simsys بود، باید به آنجا بروی:

cd /home/simsys
./delete_iccids.sh
نکته: اگر به هر دلیلی فایل delete_iccids.sh در مسیر دیگری است، آدرس کاملش را بده.
