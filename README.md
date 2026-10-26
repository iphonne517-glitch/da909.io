<div dir="rtl" align="right">

# 🐑 مراعي تيماء

متجر ثابت (Static) لبيع الذبائح واللحوم الطازجة. يُختار المنتج والتقطيع والتغليف ثم يُرسل الطلب مفصّلًا عبر **واتساب**. لا يحتاج خادمًا، ويعمل مباشرة على **GitHub Pages**.

## المزايا
- واجهة عربية RTL متجاوبة مع الجوال
- سلة مشتريات تُحفظ في المتصفح
- إرسال الطلب إلى واتساب مع الموقع الجغرافي
- التحكم بالتوفر لحظيًا عبر Firebase (اختياري)

## هيكل المشروع
```
├── index.html          الصفحة الرئيسية
├── css/style.css       التنسيق
├── js/
│   ├── config.js       إعدادات Firebase (اختياري)
│   ├── data.js         المنتجات والأسعار ورقم واتساب
│   └── app.js          منطق الموقع
├── firestore.rules     قواعد أمان Firestore
├── favicon.svg
└── .github/workflows/pages.yml   نشر تلقائي
```

## النشر على GitHub Pages
1. أنشئ مستودعًا جديدًا وارفع الملفات (أو `git push`).
2. من **Settings → Pages** اختر **Source: GitHub Actions**.
3. عند كل `push` على فرع `main` يُنشر الموقع تلقائيًا على:
   `https://USERNAME.github.io/REPO_NAME/`
4. عدّل الرابط في وسم `canonical` داخل `index.html`.

> بديل بدون Actions: Settings → Pages → Deploy from a branch → `main` / root.

## تعديل المنتجات والأسعار
عدّل الملف `js/data.js`:
- `WA` رقم واتساب بصيغة دولية بدون `+`
- `P` قائمة الذبائح وأحجامها وأسعارها
- `SERVICES` و`PACK` و`HEAD` خيارات الخدمات والتغليف والرأس

## التحكم بالتوفر
**بدون Firebase:** افتح `#/admin` على الموقع، ألغِ علامة ما هو غير متوفر، انسخ السطر الناتج والصقه مكان `let OFF=[]` في `js/data.js`.

**مع Firebase (تحديث فوري):**
1. أنشئ مشروعًا في [Firebase Console](https://console.firebase.google.com) وفعّل **Firestore** و**Authentication (Email/Password)**.
2. أضف حساب المشرف وانسخ الـ UID.
3. ضع الـ UID في `firestore.rules` مكان `YOUR_ADMIN_UID` وانشر القواعد.
4. ضع إعدادات المشروع في `js/config.js`.
5. أضف نطاق GitHub Pages في **Authentication → Settings → Authorized domains**.

## تشغيل محلي
```bash
python3 -m http.server 8000
```
ثم افتح `http://localhost:8000`.

## الترخيص
جميع الحقوق محفوظة © مراعي تيماء.

</div>
