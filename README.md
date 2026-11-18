# ⚡ نظام إدارة وفوترة استهلاك الكهرباء الذكي
### Smart Electricity Billing & Automated Meter Telemetry System

<p align="center">
  <img src="https://img.shields.io/badge/Django-5.2-092E20?style=for-the-badge&logo=django&logoColor=white" alt="Django" />
  <img src="https://img.shields.io/badge/React-19.2-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React" />
  <img src="https://img.shields.io/badge/Vite-5.4-646CFF?style=for-the-badge&logo=vite&logoColor=white" alt="Vite" />
  <img src="https://img.shields.io/badge/PostgreSQL-16-4169E1?style=for-the-badge&logo=postgresql&logoColor=white" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/SimpleJWT-Token_Auth-FF6F00?style=for-the-badge&logo=jsonwebtokens&logoColor=white" alt="JWT" />
  <img src="https://img.shields.io/badge/APScheduler-Automated_Jobs-blueviolet?style=for-the-badge" alt="APScheduler" />
  <img src="https://img.shields.io/badge/Render-Production_Ready-46E3B7?style=for-the-badge&logo=render&logoColor=white" alt="Render" />
</p>

---

## 📖 نظرة عامة عن المشروع (Executive Overview)

**نظام إدارة وفوترة الكهرباء الذكي** هو منصة متكاملة على مستوى المؤسسات (Enterprise-grade) صُممت خصيصاً لإدارة شبكات استهلاك الكهرباء في المجمعات السكنية، السكنات الجامعية، والأبراج التجارية. يجمع النظام بين:
1. **التحكم والتحصيل المالي الآلي**: إصدار فواتير ذكية، احتساب الفروقات والديون المتراكمة، وربط بوابات الدفع الإلكتروني بنظام تسوية فوري ومنع الهجمات الاحتيالية (Anti-Replay).
2. **التحكم البرمجي في العدادات (Smart Telemetry & IoT Control)**: فصل وتوصيل الكهرباء آلياً للغرف عند التأخر في السداد، وإعادة التوصيل اللحظي عند السداد، مع إتاحة التحكم اليدوي المشروط بصلاحيات دقيقة وتدوين كامل للعمليات (Audit Logging).
3. **الخريطة التفاعلية للمباني (Interactive Floor Plan)**: شاشة رقمية تفاعلية توضح الحالة الكهربائية والمالية لكل غرفة بالألوان في الوقت الحقيقي.
4. **نظام تقارير وتدقيق مالي متقدم**: توليد فوري لتقارير الأداء والموازين المالية بصيغتي **PDF** مع دعم كامل للغة العربية (Cairo Font) و **Excel (.xlsx)**.

---

## 📸 معرض صور النظام (Screenshots Showcase)

<p align="center">
  <b>1. لوحة المؤشرات والإحصائيات الحية (Dashboard & Analytics)</b><br>
  <img src="docs/screenshots/02_dashboard_overview.png" alt="لوحة التحكم والمؤشرات" width="95%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

<br>

<p align="center">
  <b>2. الخريطة التفاعلية الحية للمباني والغرف (Interactive Floor Plan)</b><br>
  <img src="docs/screenshots/03_floor_plan.png" alt="الخريطة التفاعلية للمباني" width="95%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

<br>

<p align="center">
  <b>3. إدارة الفواتير وإجراءات السداد والاعتماد (Invoices Management)</b><br>
  <img src="docs/screenshots/04_invoices.png" alt="إدارة الفواتير" width="95%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

<br>

<p align="center">
  <b>4. التقارير المالية والتحليلات البيانية المتقدمة (Financial Reports & Export)</b><br>
  <img src="docs/screenshots/05_reports.png" alt="التقارير المالية" width="95%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

<br>

<p align="center">
  <b>5. إدارة الغرف وربط العدادات الذكية والـ QR Codes</b><br>
  <img src="docs/screenshots/06_rooms.png" alt="إدارة الغرف" width="95%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

<br>

<p align="center">
  <b>6. بوابة تسجيل الدخول الآمنة (Secure RBAC Authentication)</b><br>
  <img src="docs/screenshots/01_login.png" alt="بوابة الدخول" width="70%" style="border-radius: 8px; box-shadow: 0 4px 12px rgba(0,0,0,0.15);" />
</p>

---

## 🏛️ الهيكلية التقنية الشاملة للنظام (System Architecture)

```mermaid
flowchart TD
    subgraph ClientLayer ["طبقة العميل والواجهات (Frontend Layer)"]
        UI["React 19 + Vite SPA"]
        RT["React Router v7"]
        ST["Auth Context + Axios Interceptor"]
        RC["Recharts & Interactive Charts"]
        FP["Interactive Floor Plan Canvas"]
    end

    subgraph Gateway ["طبقة الأمان والوساطة (API & Security Gateway)"]
        CORS["CORS Middleware"]
        JWT["Custom JWT Authenticator"]
        RBAC["Role-Based Access Control (RBAC)"]
        EXC["Global Exception Handler"]
    end

    subgraph ServiceLayer ["طبقة المنطق التجاري (Business Service Layer)"]
        FS["FinancialReportService (PDF/Excel)"]
        MCS["MeterCommandService (Smart Relay Engine)"]
        PGS["PaymentGatewayService (Anti-Replay Verification)"]
        SPS["SettlePaymentService (Debt & Reconnect Logic)"]
        ALS["AuditLogger Service"]
    end

    subgraph BackgroundLayer ["طبقة المهام المجدولة (Background Scheduling)"]
        APS["APScheduler Daemon"]
        W1["send_critical_warnings (Hourly)"]
        W2["auto_disconnect_overdue_invoices (Hourly)"]
        W3["check_overdue_installments"]
    end

    subgraph StorageLayer ["طبقة قواعد البيانات والملفات (Storage & Database)"]
        PG[(PostgreSQL Database)]
        STATIC["WhiteNoise Compressed Static Engine"]
    end

    UI --> Gateway
    Gateway --> ServiceLayer
    ServiceLayer --> StorageLayer
    BackgroundLayer --> ServiceLayer
    BackgroundLayer --> StorageLayer
```

---

## 🗄️ مخطط الكيانات والعلاقات (Database Entity-Relationship Diagram)

```mermaid
erDiagram
    BUILDING ||--o{ ROOM : contains
    ROOM ||--o{ STUDENT : accommodates
    ROOM ||--|| METER : equipped_with
    ROOM ||--o{ INVOICE : billed_for
    ROOM ||--o{ INSTALLMENT_PLAN : contracted_under
    ROOM ||--o{ MANUAL_METER_ACTION : logs_action
    STUDENT ||--o{ COMPLAINT : files
    USER ||--o{ INVOICE : creates_or_approves
    USER ||--o{ AUDIT_LOG : initiates

    BUILDING {
        int id PK
        string name "اسم المبنى"
        string code UK "رمز المبنى الفريد"
    }

    ROOM {
        int id PK
        int room_number "رقم الغرفة"
        int building_id FK
        string qr_code UK "رمز QR الدائم"
    }

    STUDENT {
        int id PK
        string name "اسم الطالب"
        string national_id UK "الهوية الوطنية"
        string phone "رقم الجوال"
        string status "active / evacuated"
    }

    METER {
        int id PK
        int room_id FK
        string meter_serial UK "الرقم التسلسلي للعداد"
        string connection_status "connected / disconnected"
        datetime last_reading_at
    }

    INVOICE {
        int id PK
        int room_id FK
        decimal reading_old "القراءة السابقة"
        decimal reading_new "القراءة الحالية"
        decimal consumption "كمية الاستهلاك"
        decimal final_amount "المبلغ النهائي"
        string status "pending / approved / paid"
        boolean is_overdue "حالة التأخر"
        datetime created_at
        datetime paid_at
    }

    INSTALLMENT_PLAN {
        int id PK
        int room_id FK
        decimal total_amount "إجمالي المبلغ المقسط"
        string status "active / completed / defaulted"
        int number_of_installments
    }

    SYSTEM_SETTINGS {
        int id PK
        decimal tariff_rate "سعر الكيلوواط"
        int payment_deadline_hours "مهلة السداد بالساعات"
        decimal service_fee "رسوم الخدمة"
        decimal reconnect_debt_threshold "حد إعادة التوصيل"
    }

    AUDIT_LOG {
        int id PK
        int actor_id FK
        string action_type
        string target_model
        string description
        datetime timestamp
    }
```

---

## 🔄 دورة حياة الفاتورة وفصل/توصيل الخدمة الآلي (Billing & Auto-Action Flows)

### 1. مخطط تتابع عملية التحصيل وإعادة التوصيل الفورية (Payment & Auto-Reconnect)

```mermaid
sequenceDiagram
    autonumber
    actor Student as الطالب / المحاسب
    participant Web as الواجهة الأمامية (React)
    participant API as خادم النظام (Django API)
    participant PayGov as بوابة الدفع (Payment Gateway)
    participant Relay as محرك العداد الذكي (Meter Engine)
    participant DB as قاعدة البيانات (PostgreSQL)

    Student->>Web: طلب سداد / تحقق من عملية دفع
    Web->>API: POST /api/settle-payment/ أو verify-transaction/
    API->>PayGov: مطابقة كود العملية مع رصيد الغرفة
    PayGov-->>API: العملية صحيحة وغير مكررة
    API->>DB: تحديث حالة الفاتورة إلى (Paid) وتوثيق تاريخ السداد
    API->>DB: فحص إجمالي المديونية المتبقية للغرفة
    alt المتبقي <= حد إعادة التوصيل (300 ريال) أو وجود خطة تقسيط نشطة
        API->>Relay: إرسال أمر توصيل الخدمة فوراً (CONNECT)
        Relay-->>API: تم فتح التيار الكهربائي بنجاح
        API->>DB: تحديث حالة العداد (connected)
        API->>DB: تسجيل حركة تدقيق في AuditLog
    end
    API-->>Web: إرجاع استجابة نجاح السداد مع حالة العداد
    Web-->>Student: إشعار أخضر وتحديث الخريطة التفاعلية
```

### 2. مخطط تتابع الفحص الدوري والفصل الآلي عند التعثر (Hourly Auto-Disconnect)

```mermaid
sequenceDiagram
    autonumber
    participant Job as مجدول المهام (APScheduler)
    participant Service as خدمة الفواتير والمراقبة
    participant Relay as محرك العداد (Smart Meter)
    participant DB as قاعدة البيانات (PostgreSQL)

    loop كل ساعة (Hourly Interval)
        Job->>Service: تشغيل فحص الفواتير send_critical_warnings
        Service->>DB: استعلام عن فواتير غير مسددة تبقى لها <= 5 ساعات
        DB-->>Service: قائمة الفواتير الحرجة
        Service-->>DB: إرسال إنذارات وتحديد warning_sent = True

        Job->>Service: تشغيل فحص المهلة auto_disconnect_overdue_invoices
        Service->>DB: استعلام عن فواتير انتهت مهلة سدادها وما زالت معلقة
        DB-->>Service: قائمة الفواتير المتعثرة
        loop لكل غرفة متعثرة
            Service->>DB: التأكد من عدم وجود خطة تقسيط نشطة (Active Plan)
            opt لا توجد خطة تقسيط
                Service->>Relay: إصدار أمر الفصل (DISCONNECT)
                Relay-->>Service: تم فصل التيار
                Service->>DB: تحديث حالة العداد (disconnected)
                Service->>DB: إضافة غرامة التأخير (service_fee)
            end
        end
    end
```

---

## 🚦 المخططات الحالية لحالات النظام (State Machine Diagrams)

### 1. دورة حياة الفاتورة (Invoice State Diagram)

```mermaid
stateDiagram-v2
    [*] --> Pending : إنشاء الفاتورة وقراءة العداد
    Pending --> Approved : اعتماد المحاسب / المشرف
    Pending --> Cancelled : إلغاء لوجود خطأ في القراءة
    Approved --> Paid : سداد كامل المبلغ قبل المهلة
    Approved --> Overdue : انقضاء مهلة السداد (payment_deadline_hours)
    Overdue --> Paid : سداد متأخر + احتساب غرامة التأخير
    Paid --> [*]
    Cancelled --> [*]
```

### 2. حالات العداد الذكي (Smart Meter Connection States)

```mermaid
stateDiagram-v2
    [*] --> Disconnected : إنشاء عداد جديد
    Disconnected --> Connected : سداد كامل المديونية / تفعيل خطة تقسيط
    Connected --> Disconnected : تأخر السداد وانتهاء المهلة (Auto Disconnect)
    Connected --> Disconnected : فصل يدوي بقرار إداري (Manual Disconnect)
    Disconnected --> Connected : إعادة توصيل يدوي بقرار معتمد (Manual Override)
    Connected --> Maintenance : عطل فني في القواطع
    Maintenance --> Connected : انتهاء أعمال الصيانة
```

---

## 👥 مصفوفة الصلاحيات والأدوار (Role-Based Access Matrix - RBAC)

| الوظيفة / الإجراء | المشرف العام (Admin) | المحاسب (Accountant) | المندوب (Delegate) | أمين الصندوق (Cashier) |
| :--- | :---: | :---: | :---: | :---: |
| **إدارة المباني والغرف والطلاب** | ✅ كامل الصلاحية | 👁️ عرض فقط | 👁️ عرض فقط | ❌ غير متاح |
| **إدخال قراءات العدادات** | ✅ متاح | ❌ غير متاح | ✅ متاح | ❌ غير متاح |
| **اعتماد الفواتير المالية** | ✅ متاح | ✅ متاح | ❌ غير متاح | ❌ غير متاح |
| **تسجيل وتأكيد المقبوضات النقدية** | ✅ متاح | ✅ متاح | ❌ غير متاح | ✅ متاح |
| **إنشاء خطط التقسيط (Installments)** | ✅ متاح | ✅ متاح | ❌ غير متاح | ❌ غير متاح |
| **التحكم اليدوي المباشر بالعدادات** | ✅ مع توثيق السبب | ❌ غير متاح | ❌ غير متاح | ❌ غير متاح |
| **استخراج وتصدير التقارير (PDF/Excel)** | ✅ كامل الصلاحية | ✅ كامل الصلاحية | ❌ غير متاح | ❌ غير متاح |
| **تعديل الإعدادات والتعرفة (Tariff)** | ✅ متاح | ❌ غير متاح | ❌ غير متاح | ❌ غير متاح |
| **سجلات الرقابة والتدقيق (Audit Logs)**| ✅ متاح | ❌ غير متاح | ❌ غير متاح | ❌ غير متاح |

---

## 🔌 واجهات برمجة التطبيقات الأساسية (API Endpoints Overview)

| Method | Endpoint | الصلاحية المطلوبة | الوصف |
| :--- | :--- | :--- | :--- |
| `POST` | `/api/login/` | للجميع | تسجيل الدخول واستخراج JWT Access & Refresh Tokens |
| `POST` | `/api/token/refresh/` | للجميع | تجديد الـ Access Token المنتهي |
| `GET` | `/api/buildings/` | مصادق عليه | جلب قائمة المباني مع الغرف |
| `GET` | `/api/buildings/{id}/floor_plan/` | مصادق عليه | بيانات الخريطة التفاعلية للمبنى وحالات العدادات |
| `GET/POST` | `/api/invoices/` | مصادق عليه | استعراض الفواتير مع دعم الفلترة وإنشاء فواتير جديدة |
| `POST` | `/api/invoices/{id}/approve/` | Admin, Accountant | اعتماد الفاتورة لتصبح مستحقة السداد |
| `POST` | `/api/settle-payment/` | Admin, Accountant, Cashier | تسديد فاتورة أو جزء منها وفحص إعادة التوصيل |
| `POST` | `/api/verify-transaction/` | مصادق عليه | التحقق الفوري من إيصال الدفع الإلكتروني |
| `POST` | `/api/installment-plans/` | Admin, Accountant | إنشاء خطة تقسيط لجدولة المديونية |
| `POST` | `/api/manual-meter-action/` | Admin فقط | أمر فصل/توصيل يدوي مع تسجيل سبب إلزامي |
| `GET` | `/api/reports/financial/` | Admin, Accountant | توليد وتصدير التقارير المالية (JSON, PDF, Excel) |
| `GET/PATCH`| `/api/settings/` | Get: الكل / Patch: Admin | استعراض وتحديث سعر الكيلوواط والمهل الزمنية |
| `GET` | `/api/audit-logs/` | Admin فقط | استعراض سجلات التدقيق الرقابي للعمليات الحساسة |

---

## 🛠️ دليل التثبيت والتشغيل المحلي (Installation & Setup)

### 1. المتطلبات الأساسية (Prerequisites)
* **Python** (الإصدار 3.11 أو أحدث)
* **Node.js** (الإصدار 18 أو 20 أو أحدث) مع **npm**
* **PostgreSQL** (الإصدار 14 أو أحدث)

---

### 2. إعداد الخادم الخلفي (Backend Setup)

```bash
# 1. الدخول إلى مجلد المشروع وتفعيل البيئة الافتراضية
cd ElectricityBillingSystem
python -m venv venv
# لنظام Windows:
venv\Scripts\activate
# لنظام Linux/macOS:
source venv/bin/activate

# 2. تثبيت الحزم البرمجية
pip install -r backend/requirements.txt

# 3. إعداد متغيرات البيئة (أنشئ ملف backend/.env):
# DB_NAME=billing_system
# DB_USER=postgres
# DB_PASSWORD=your_password
# DB_HOST=127.0.0.1
# DB_PORT=5432
# DEBUG=True

# 4. تطبيق الترحيلات على قاعدة البيانات
python backend/manage.py migrate

# 5. تجميع الملفات الثابتة
python backend/manage.py collectstatic --noinput

# 6. تشغيل خادم التطوير
python backend/manage.py runserver 127.0.0.1:8000
```

---

### 3. إعداد لوحة التحكم (Frontend Setup)

```bash
# 1. الدخول إلى مجلد لوحة التحكم
cd admin-dashboard

# 2. تثبيت الحزم والاعتماديات
npm install

# 3. تشغيل خادم التطوير السريع (Vite)
npm run dev
```

ستفتح الواجهة على الرابط: `http://127.0.0.1:5173/`

---

## 🚀 النشر على السحابة (Cloud Deployment on Render)

المشروع مُهيأ بالكامل وجاهز للنشر المباشر عبر ملف `render.yaml` الصريح:
* **قاعدة بيانات مدارة**: PostgreSQL مجانية ومنشأة تلقائياً.
* **الخادم الخلفي (Web Service)**: يعمل ببيئة Python مع خادم `Gunicorn` و `WhiteNoise` للملفات الثابتة.
* **الواجهة الأمامية (Static Site)**: بناء آلي عبر Vite ونشر عالي السرعة مع توجيه المسارات `/* -> /index.html`.

---

## 📁 هيكلية مجلدات المشروع (Repository Structure)

```text
ElectricityBillingSystem/
├── README.md                     # التوثيق الشامل والرسمي للمشروع
├── render.yaml                   # ملف إعدادات النشر السحابي (Infrastructure as Code)
├── docs/                         # التوثيقات والوسائط
│   └── screenshots/              # لقطات شاشة موثقة للواجهات الحية
├── backend/                      # خادم Django REST Framework
│   ├── api/                      # التطبيق الرئيسي (Models, Views, Serializers, Tasks)
│   │   ├── services/             # طبقة الخدمات (Report, Meter, Payment, Audit)
│   │   ├── models.py             # نماذج قاعدة البيانات (Building, Room, Invoice, ...)
│   │   ├── views.py              # الـ ViewSets ونقاط النهاية (Endpoints)
│   │   ├── tasks.py              # المهام المجدولة (APScheduler Functions)
│   │   └── authentication.py     # مصادقة JWT المخصصة
│   ├── assets/fonts/             # الخطوط المعتمدة لتصدير الـ PDF العربي (Cairo Font)
│   ├── config/                   # إعدادات المشروع الرئيسية (settings.py, urls.py)
│   └── manage.py                 # موجه أوامر Django
└── admin-dashboard/              # واجهة المستخدم React 19 + Vite
    ├── src/
    │   ├── api/                  # عميل Axios ومعالجة تجديد التوكنات
    │   ├── components/           # المكونات (FloorPlanSection, ReportsSection, ...)
    │   ├── context/              # سياق المصادقة وصلاحيات الجلسة (AuthContext)
    │   ├── pages/                # الصفحات (DashboardPage, LoginPage, RoomPaymentPage)
    │   └── App.jsx               # موجه المسارات والتنبيهات
    ├── index.html
    └── package.json
```

---

<p align="center">
  <b>تم التطوير والتوثيق بأعلى معايير الجودة لضمان أداء مؤسسي موثوق وآمن ⚡</b>
</p>
