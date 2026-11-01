# منصة اقرأ

مشروع Laravel للتجربة محليًا. يحتاج PHP 8.2 أو أحدث مع إضافات PHP المعتادة لـLaravel، و`pdo_sqlite` لتشغيل SQLite، بالإضافة إلى Composer.

## تشغيل محلي على Windows

من PowerShell داخل مجلد المشروع:

```powershell
Copy-Item .env.example .env
composer install
php artisan key:generate
if (-not (Test-Path database/database.sqlite)) { New-Item database/database.sqlite -ItemType File }
php artisan migrate --seed
php artisan storage:link
php artisan serve
```

افتح `http://127.0.0.1:8000`. حساب الإدارة المحلي الذي ينشئه الـseeder هو رقم `01000000000` وكلمة المرور `admin123456`. غيّر بياناته قبل أي نشر، ولا ترفع ملف `.env` أو قاعدة البيانات المحلية.

لو أردت بدء قاعدة البيانات من جديد محليًا، استخدم `php artisan migrate:fresh --seed`؛ هذا الأمر يحذف بيانات قاعدة البيانات الحالية.