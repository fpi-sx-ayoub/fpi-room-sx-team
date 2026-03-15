# نشر المشروع على Vercel

## معلومات المستودع

- **GitHub Repository:** https://github.com/fpi-sx-ayoub/fpi-room-sx-team
- **المستخدم:** fpi-sx-ayoub
- **الفرع الرئيسي:** main

## خطوات النشر على Vercel

### الطريقة الأولى: النشر المباشر من Vercel Dashboard (الأسهل)

1. **اذهب إلى Vercel:**
   - افتح https://vercel.com/dashboard

2. **أضف مشروع جديد:**
   - انقر على "Add New..." → "Project"
   - اختر "Import Git Repository"

3. **ربط GitHub:**
   - اختر GitHub كمصدر
   - ابحث عن المستودع: `fpi-sx-ayoub/fpi-room-sx-team`
   - انقر "Import"

4. **تكوين المشروع:**
   - **Project Name:** fpi-room-sx-team
   - **Framework Preset:** Other
   - **Build Command:** `pnpm build`
   - **Output Directory:** `dist`
   - **Install Command:** `pnpm install`

5. **إضافة متغيرات البيئة:**
   - في قسم "Environment Variables"، أضف:
     ```
     API_KEY = YOUR_SECURE_API_KEY_HERE
     NODE_ENV = production
     ```

6. **النشر:**
   - انقر "Deploy"
   - سينتظر Vercel بناء المشروع ونشره

### الطريقة الثانية: استخدام Vercel CLI

```bash
# تثبيت Vercel CLI
npm install -g vercel

# تسجيل الدخول
vercel login

# الذهاب إلى مجلد المشروع
cd /home/ubuntu/fpi-room-sx-team

# نشر المشروع
vercel --prod

# إضافة متغيرات البيئة (إذا لم تُضف من قبل)
vercel env add API_KEY
# أدخل القيمة: YOUR_SECURE_API_KEY_HERE
```

## بعد النشر

### اختبار الـ API

```bash
# اختبار الصحة
curl https://fpi-room-sx-team.vercel.app/health

# بدء عملية spam (مثال)
curl -X POST https://fpi-room-sx-team.vercel.app/api/spam \
  -H "Content-Type: application/json" \
  -d '{
    "target_id": "123456789",
    "hours": 24,
    "api_key": "YOUR_SECURE_API_KEY_HERE"
  }'

# التحقق من حالة العملية
curl "https://fpi-room-sx-team.vercel.app/api/status/123456789?api_key=YOUR_SECURE_API_KEY_HERE"
```

## النشر التلقائي

بعد ربط المستودع مع Vercel:
- **أي push إلى الفرع main سيؤدي إلى نشر تلقائي**
- Vercel سيقوم بـ:
  1. سحب الكود الجديد
  2. تثبيت المكتبات
  3. بناء المشروع
  4. نشر الإصدار الجديد

## استكشاف الأخطاء

### خطأ في البناء
- تحقق من السجلات في Vercel Dashboard
- تأكد من أن `pnpm build` يعمل محلياً
- تحقق من أن جميع المكتبات مدرجة في `package.json`

### خطأ في المتغيرات
- تأكد من إضافة `API_KEY` في متغيرات البيئة
- تحقق من أن القيمة صحيحة

### خطأ في الاتصال
- تحقق من أن الـ API endpoints صحيحة
- تأكد من أن `server/index.ts` يتم بناؤه بشكل صحيح

## رابط المشروع

بعد النشر، سيكون المشروع متاح على:
```
https://fpi-room-sx-team.vercel.app
```

## المراقبة

- **لوحة تحكم Vercel:** https://vercel.com/dashboard
- **سجلات الدوال:** متاحة في إعدادات المشروع
- **تحليلات الأداء:** يمكن عرضها من لوحة التحكم

## دعم مخصص

إذا أردت استخدام نطاق مخصص:
1. اشترِ النطاق من أي مسجل
2. أضفه في إعدادات Vercel
3. اتبع تعليمات DNS
