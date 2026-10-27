# 🏢 AQAR IN — Egypt's Property Intelligence & Valuation Platform

منصة متكاملة للاستخبارات والتقييم العقاري الذكي في جمهورية مصر العربية، مبنية بأحدث معايير الويب الفاخرة مع دعم كامل لقاعدة بيانات **MySQL** و **Node.js (Express)** و **React 18 + Vite + Tailwind CSS**.

---

## 🌟 الميزات المكتملة في المشروع (Features)

1. **التقييم العقاري الذكي الفوري (Instant AI Valuation Engine)**:
   - معالج تفاعلي متعدد الخطوات (Multi-step Wizard) لتحديد المنطقة، الكمبوند، المساحة، نوع التشطيب، الدور والإطلالة.
   - حساب السعر العادل (Minimum, Maximum, Median)، وسعر المتر المربع (EGP/m²)، ونسبة الثقة (Confidence Score).
   - رسم بياني تفاعلي لتطور الأسعار خلال 5 سنوات وتوقعات النمو السنوي.
   - حساب العائد الإيجاري السنوي المتوقع (Rental Yield) وقيمة الإيجار الشهري.
   - إمكانية طباعة وتصدير شهادة التقييم الرسمية كـ **PDF**.

2. **محرك البحث والخرائط التفاعلية (Property Search & Map View)**:
   - تقسيم البحث: للبيع (Buy)، للإيجار (Rent)، وتجاري/إداري (Commercial).
   - وضع العرض المزدوج (Split View) بين قائمة العقارات والخريطة التفاعلية المباشرة (**Leaflet OpenStreetMap**).
   - فلاتر دقيقة: السعر، المساحة، عدد الغرف، نوع التشطيب، وطريقة الدفع (كاش / تقسيط).

3. **صفحة تفاصيل العقار الشاملة (Property Details)**:
   - معرض صور عالي الجودة مع شريط مصغرات.
   - كارت تقييم iScore Rating (9.4/10) مع تفاصيل الموقع والمواصفات.
   - حاسبة تمويل عقاري سريعة مدمجة في نفس الصفحة لحساب القسط الشهري للوحدة.
   - زر محادثة واتساب مباشر وزر اتصال هاتفي مع استمارة طلب معاينة فورية.

4. **منظومة التمويل العقاري للبنوك المصرية (Mortgage Hub)**:
   - حاسبة تفاعلية بمبادرات البنك المركزي المصري 8% وأسعار الفائدة التجارية.
   - مقارنة حية بين البنوك (CIB، البنك الأهلي، بنك مصر، QNB، AAIB).
   - استمارة التقديم على الموافقة المسبقة للتمويل العقاري.

5. **أدوات دعم القرار الذكية (Smart Decision Tools)**:
   - **ساعدني في الاختيار (Help Me Choose Quiz)**: اختبار ذكي لاقتراح أفضل كمبوندات ومناطق تناسب ميزانية وهدف المشتري (سكن أم استثمار).
   - **قائمة فحص البائع (Selling Due Diligence Checklist)**: دليل تفاعلي بمؤشر تقدم لتجهيز أوراق الملكية والمخالصات وتثمين الوحدة.
   - **طلب معاينة مهندس معتمد (Professional Valuation)**: حجز زيارة خبير تقييم معتمد للمعاينة الميدانية وإصدار تقرير رسمي للبنوك.
   - **برنامج الشركاء (Partners Program)**: للمطورين، البروكرز، ومكاتب التقييم.

6. **إضافة العقارات والحسابات (Listing & Dashboards)**:
   - استمارة نشر وإضافة عقار جديد بجميع المواصفات والصور.
   - لوحة تحكم المستخدم (**User Dashboard**) للعقارات المحفوظة وسجل التقييمات.
   - لوحة تحكم الإدارة (**Super Admin Dashboard**) لتعديل أسعار المتر المرجعية لكل منطقة وإدارة المنصة.
   - دعم كامل للغتين العربية والإنجليزية (**RTL / LTR Toggle**).

---

## 🏗️ هيكلية المشروع (Project Structure)

```text
buildingiscore/
├── client/                     # واجهة المستخدم React 18 + Vite + Tailwind
│   ├── src/
│   │   ├── components/         # Navbar, Footer, PropertyCard, PropertyMap, Badge...
│   │   ├── pages/              # Home, Valuation, Search, Details, Mortgage, HelpMeChoose...
│   │   ├── context/            # LanguageContext (EN/AR), AuthContext
│   │   ├── services/           # api.js (Express API + LocalStorage fallback)
│   │   └── data/               # mockData.js (بيانات الكمبوندات وأسعار المتر في مصر)
│   └── package.json
│
├── server/                     # الـ Backend REST API بـ Express و MySQL
│   ├── src/
│   │   ├── routes/             # authRoutes, propertyRoutes, valuationRoutes, mortgageRoutes...
│   │   ├── db.js               # اتصال MySQL Connection Pool
│   │   └── server.js
│   ├── .env                    # إعدادات السيرفر وقاعدة البيانات
│   └── package.json
│
├── database/                   # قاعدة البيانات MySQL
│   ├── schema.sql              # كود إنشاء الجداول والعلاقات كاملة
│   └── seed_data.sql           # بيانات واقعية لكمبوندات التجمع، زايد، العاصمة، والساحل
│
└── deploy/                     # ملفات النشر الجاهزة على السيرفر الخاص VPS
    ├── ecosystem.config.js     # إعدادات PM2 للتشغيل المستمر
    └── nginx.conf              # إعدادات Nginx مع SSL Reverse Proxy
```

---

## 🚀 كيفية التشغيل محلياً (Local Development)

### 1. تشغيل واجهة المستخدم (Frontend):
```bash
cd client
npm run dev
```
الموقع سيفتح مباشرة على: `http://localhost:5173`

### 2. تشغيل السيرفر (Backend API):
```bash
cd server
npm start
```
الـ API سيعمل على: `http://localhost:5000`

### 3. استيراد قاعدة بيانات MySQL:
افتح phpMyAdmin أو MySQL Workbench ونفذ الملفين:
1. `database/schema.sql`
2. `database/seed_data.sql`

---

## 🌐 كيفية النشر على السيرفر الخاص (VPS Deployment)

1. ارفع المشروع إلى مسار `/var/www/buildingiscore` على السيرفر.
2. شغل الـ Backend عبر **PM2**:
   ```bash
   pm2 start deploy/ecosystem.config.js
   pm2 save
   ```
3. انقل ملف `deploy/nginx.conf` إلى `/etc/nginx/sites-available/buildingiscore.com` واعمل له تفعيل مع تشغيل Certbot للـ SSL:
   ```bash
   sudo certbot --nginx -d buildingiscore.com -d www.buildingiscore.com
   sudo systemctl reload nginx
   ```
