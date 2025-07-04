# 🏗️ تشطيبك - Tashtibak 
**نظام ذكي لإدارة مشاريع التشطيبات والمقاولات**  
*يدير المشاريع، المقاولين، العمال، العملاء، المواد، والجوانب المالية بدقة واحترافية*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat&logo=fastapi)
![React Native](https://img.shields.io/badge/React_Native-20232A?style=flat&logo=react)
[![GitHub Repo](https://img.shields.io/badge/GitHub-Repository-181717?logo=github)](https://github.com/ahmeddev-inc/Tashtibak.git)

---

## 📖 فهرس المحتويات
1. [✨ حول المشروع](#حول-المشروع)
2. [🚀 المميزات](#المميزات)
3. [👥 الأدوار والصلاحيات](#الأدوار-والصلاحيات)
4. [🗄️ هيكل قاعدة البيانات](#هيكل-قاعدة-البيانات)
5. [📱 واجهات التطبيق](#واجهات-التطبيق)
6. [⚙️ نقاط نهاية API](#نقاط-نهاية-api)
7. [🛠️ التثبيت والتشغيل](#التثبيت-والتشغيل)
8. [📄 الرخصة](#الرخصة)

---

## ✨ حول المشروع
**تشطيبك** هو نظام متكامل مصمم خصيصًا لقطاع التشطيبات والمقاولات، يوفر:
- إدارة شاملة للمشاريع والمراحل والبنود
- نظام صلاحيات متعدد المستويات
- تقارير مالية ومستخلصات تلقائية
- تتبع المخزون والمواد في الوقت الفعلي
- إشعارات فورية للمستخدمين
- واجهات مُحسّنة للجوال والويب

**المستودع الرسمي**:  
[https://github.com/ahmeddev-inc/Tashtibak.git](https://github.com/ahmeddev-inc/Tashtibak.git)

---

## 🚀 المميزات
### 📊 إدارة المشاريع
- تقسيم المشروع لمراحل وبنود فرعية
- تتبع التقدم النسبي لكل بند
- ربط المهام بالمقاولين والعمال

### 💼 النظام المالي
- إنشاء فواتير PDF تلقائيًا
- حساب رواتب العمال حسب الحضور
- تقارير التكاليف والإيرادات

### 📦 إدارة المخزون
- تتبع كميات المواد المستخدمة
- تنبيهات نقص المخزون
- سجلات الشراء والتوريد

### 🔔 نظام الإشعارات
- إشعارات تغيير حالة المهام
- تنبيهات المواعيد النهائية
- إعلام بالمستحقات المالية

---

## 👥 الأدوار والصلاحيات
| الدور         | الصلاحيات الأساسية                                                                 | الوصول إلى الشاشات الرئيسية           |
|---------------|-----------------------------------------------------------------------------------|-------------------------------------|
| **👑 المشرف**  | إدارة كاملة (مستخدمين، مشاريع، مالية، مواد، تقارير، إعدادات النظام)              | لوحة التحكم، التقارير، الإعدادات     |
| **👨‍💼 العميل** | عرض تفاصيل مشروعه، متابعة التقدم المالي، تنزيل الفواتير، التواصل مع المقاولين    | مشروعاتي، الفواتير، المحادثات       |
| **👷‍♂️ المقاول** | استلام المهام، تحديث الحالة، رفع صور الإنجاز، إدارة العمال، طلب مواد             | المهام، العمال، الطلبات، المستحقات |
| **👷‍♀️ العامل**  | عرض المهام اليومية، تسجيل الحضور/الانصراف، متابعة الراتب، تلقي الإشعارات        | جدولي، رواتبي، الإشعارات            |

---

## 🗄️ هيكل قاعدة البيانات
### الكيانات الأساسية
```mermaid
erDiagram
    users ||--o{ projects : "يدير/يشارك"
    users {
        UUID id PK
        string name
        string email
        enum role
        string password_hash
    }
    projects ||--|{ project_stages : "يشمل"
    projects {
        UUID id PK
        string name
        UUID client_id FK
        decimal budget
    }
    project_stages ||--|{ tasks : "يتكون من"
    tasks {
        UUID id PK
        string title
        enum status
        UUID contractor_id FK
    }

جداول رئيسية
| الجدول          | الوصف                          | الحقول الحرجة                              |
|-----------------|-------------------------------|-------------------------------------------|
| **users**       | بيانات جميع المستخدمين        | `id`, `role`, `phone`, `created_at`       |
| **projects**    | المشاريع النشطة والمكتملة     | `id`, `client_id`, `start_date`, `status` |
| **materials**   | المواد والمخزون               | `id`, `current_stock`, `min_threshold`    |
| **transactions**| المعاملات المالية             | `id`, `type`, `amount`, `project_id`      |

---

## 📱 واجهات التطبيق
> *سيتم إضافة لقطات شاشة هنا بعد الانتهاء من التصميم*

### شاشات رئيسية
| الدور         | الشاشات الأساسية                                  |
|---------------|--------------------------------------------------|
| **المشرف**    | لوحة التحكم، إدارة المستخدمين، التقارير الشاملة   |
| **العميل**    | نظرة عامة على المشروع، الفواتير، المحادثات       |
| **المقاول**   | لوحة المهام، طلبات المواد، تقارير الإنجاز        |
| **العامل**    | المهام اليومية، سجل الحضور، كشف الراتب           |

---

## ⚙️ نقاط نهاية API
### المصادقة (Auth)
```http
POST /api/auth/login
Content-Type: application/json
{
  "email": "user@example.com",
  "password": "******"
}
```

### إدارة المشاريع (Projects)
```http
GET /api/projects
Authorization: Bearer <token>

POST /api/projects
{
  "name": "فيلا - القاهرة الجديدة",
  "client_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6"
}
```

### المهام (Tasks)
```http
PATCH /api/tasks/{id}/status
{
  "status": "in_progress"
}

GET /api/tasks?contractor_id={id}
```

### المواد (Materials)
```http
POST /api/materials/request
{
  "project_id": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "items": [
    { "material_id": 1, "quantity": 50 }
  ]
}
```

---

## 🛠️ التثبيت والتشغيل
### 1. استنساخ المستودع
```bash
git clone https://github.com/ahmeddev-inc/Tashtibak.git
cd Tashtibak
```

### 2. متطلبات النظام
- Python 3.10+
- Node.js 18+
- PostgreSQL 14+
- Android Studio (للتشغيل المحلي)

### 3. تشغيل الخلفية (FastAPI)
```bash
# الانتقال لمجلد الخلفية
cd backend

# إنشاء بيئة افتراضية
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate    # Windows

# تثبيت الاعتماديات
pip install -r requirements.txt

# تهيئة ملف البيئة (انظر الإرشادات أدناه)
uvicorn main:app --reload --port 8000
```

### 4. تشغيل الواجهة (React Native)
```bash
cd ../mobile-app
npm install

# للأندرويد
npx react-native run-android

# للآيفون (يتطلب macOS)
npx react-native run-ios
```

### 5. تهيئة قاعدة البيانات
1. إنشاء ملف `.env` في مجلد `backend`:
```env
DATABASE_URL=postgresql://user:password@localhost:5432/tashtibak_db
JWT_SECRET=your_strong_secret_here
ALGORITHM=HS256
ACCESS_TOKEN_EXPIRE_MINUTES=1440
```

---

## 📄 الرخصة
هذا المشروع مرخص تحت [رخصة MIT](LICENSE).

```text
Copyright (c) 2025 مشروع تشطيبك

يُسمح بالاستخدام الحر لأي غرض بما في ذلك الاستخدام التجاري،
شريطة ذكر حقوق الملكية وإرفاق نسخة من الرخصة مع جميع النسخ.
```

---

## 🔮 الخطوات القادمة
- [ ] إضافة شاشات التطبيق الفعلية
- [ ] دعم الترجمة الإنجليزية (مستودع منفصل)
- [ ] دعم المصادقة الثنائية (2FA)
- [ ] تكامل مع أنظمة الدفع الإلكتروني

**مستودع GitHub الرسمي**:  
[https://github.com/ahmeddev-inc/Tashtibak.git](https://github.com/ahmeddev-inc/Tashtibak.git)
```

### أهم التعديلات التي تمت:
1. **أضفت شارة GitHub Repository** أعلى الملف مباشرة
2. **تحديث قسم "حول المشروع"** بإضافة رابط المستودع الرسمي
3. **تعديل قسم التثبيت** ليشمل أمر `git clone` كخطوة أولى
4. **توضيح هيكل المجلدات** في أوامر التشغيل (backend/mobile-app)
5. **إضافة متغيرات بيئة أساسية** في ملف `.env`
6. **تحديث قسم الخطوات القادمة** برابط المستودع في النهاية
7. **تحسين تنسيق الأوامر** لتكون أكثر وضوحًا
