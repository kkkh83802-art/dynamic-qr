# Dynamic QR — واجهة عربية/إنجليزية

## محتويات الحزمة
- `index.html`: واجهة الموقع ولوحة إدارة العروض في ملف واحد.
- `supabase_setup.sql`: جدول العروض وسياسات RLS وStorage.

## قبل النشر
1. افتح `index.html` بمحرر نصوص.
2. ابحث عن `SUPABASE_URL` و `SUPABASE_ANON_KEY`.
3. ضع Project URL و anon/publishable key من Supabase > Project Settings > API.
4. لا تضع `service_role` أو أي مفتاح سري في الواجهة.

## تجهيز Supabase
1. افتح مشروع `dynamic-qr` ثم SQL Editor.
2. الصق محتوى `supabase_setup.sql` وشغّله.
3. تأكد أن لديك جدول `site_admins` وفيه `user_id` لحساب المشرف.
4. تأكد أن الدالة `public.is_site_admin()` موجودة وتُرجع true للمستخدم الموجود في `site_admins`.
5. في Authentication > Users أنشئ مستخدم المشرف بالبريد وكلمة المرور، ثم أضف UUID الخاص به إلى `site_admins` إذا لم يكن موجوداً.

## النشر من الهاتف عبر GitHub Pages
1. نزّل ZIP وفك ضغطه على الهاتف.
2. افتح github.com وسجّل الدخول، ثم أنشئ Repository جديداً باسم `dynamic-qr`.
3. اختر Add file > Upload files وارفع `index.html` فقط (ويمكن رفع SQL وREADME أيضاً).
4. افتح Settings > Pages.
5. في Build and deployment اختر Deploy from a branch، ثم `main` و`/(root)` واضغط Save.
6. انتظر رابط الموقع الذي يظهر في صفحة Pages.

## الاستخدام
- الزوار يرون العروض النشطة فقط.
- اضغط دخول الإدارة وسجّل بحساب المشرف.
- أضف العرض بالعربية والإنجليزية وارفع صورة اختيارياً وأدخل رابط الوجهة.
- احتفظ برابط الموقع وضعه خلف رمز QR الذي تطبعه أو تشاركه.

## ملاحظة مهمة
الواجهة تتوقع جدول `public.offers` بالأعمدة الموجودة في ملف SQL، وStorage bucket باسم `offers`.
قبل تشغيل SQL راجع وجود `public.is_site_admin()` و`public.site_admins(user_id)` لأنهما أُنشئا في خطواتك السابقة. إذا كانت أسماء الأعمدة أو الدالة مختلفة، لا تشغّل السياسات قبل مطابقة الأسماء.
