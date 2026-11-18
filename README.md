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

## 📸 معرض صور النظام الموثقة (Screenshots Showcase)

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

## 🏛️ 1. الهيكلية التقنية الشاملة للنظام (System Architecture)

<p align="center">
  <img src="docs/diagrams/01_system_architecture.png" alt="الهيكلية الشاملة للنظام" width="95%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود المخطط السهمي التفاعلي (Mermaid Code)</b></summary>

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
        PG[("PostgreSQL Database")]
        STATIC["WhiteNoise Compressed Static Engine"]
    end

    UI --> Gateway
    Gateway --> ServiceLayer
    ServiceLayer --> StorageLayer
    BackgroundLayer --> ServiceLayer
    BackgroundLayer --> StorageLayer
```

</details>

---

## 🗄️ 2. مخطط الكيانات والعلاقات (Database Entity-Relationship Diagram)

<p align="center">
  <img src="docs/diagrams/02_database_erd.png" alt="مخطط الكيانات والعلاقات" width="95%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود مخطط الكيانات (Mermaid Code)</b></summary>

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
        string name
        string code UK
    }
    ROOM {
        int id PK
        int room_number
        int building_id FK
        string qr_code UK
    }
    STUDENT {
        int id PK
        string name
        string national_id UK
        string phone
        string status
    }
    METER {
        int id PK
        int room_id FK
        string meter_serial UK
        string connection_status
        datetime last_reading_at
    }
    INVOICE {
        int id PK
        int room_id FK
        decimal reading_old
        decimal reading_new
        decimal consumption
        decimal final_amount
        string status
        boolean is_overdue
        datetime created_at
        datetime paid_at
    }
    INSTALLMENT_PLAN {
        int id PK
        int room_id FK
        decimal total_amount
        string status
        int number_of_installments
    }
    SYSTEM_SETTINGS {
        int id PK
        decimal tariff_rate
        int payment_deadline_hours
        decimal service_fee
        decimal reconnect_debt_threshold
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

</details>

---

## 🔄 3. مخططات التتابع وسير العمليات (Sequence Diagrams)

### أ. تتابع عملية التحصيل وإعادة التوصيل الفورية (Payment & Auto-Reconnect)

<p align="center">
  <img src="docs/diagrams/03_sequence_payment.png" alt="مخطط تتابع التحصيل" width="95%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود المخطط (Mermaid Code)</b></summary>

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

</details>

<br>

### ب. تتابع الفحص الدوري والفصل الآلي عند التعثر (Hourly Auto-Disconnect)

<p align="center">
  <img src="docs/diagrams/04_sequence_disconnect.png" alt="مخطط تتابع الفصل الآلي" width="95%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود المخطط (Mermaid Code)</b></summary>

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

</details>

---

## 🚦 4. المخططات الحالية لحالات النظام (State Machine Diagrams)

### أ. دورة حياة الفاتورة (Invoice State Machine)

<p align="center">
  <img src="docs/diagrams/05_state_invoice.png" alt="دورة حياة الفاتورة" width="85%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود مخطط الحالات (Mermaid Code)</b></summary>

```mermaid
stateDiagram-v2
    [*] --> Pending : إنشاء الفاتورة وقراءة العداد
    Pending --> Approved : اعتماد المحاسب / المشرف
    Pending --> Cancelled : إلغاء لوجود خطأ في القراءة
    Approved --> Paid : سداد كامل المبلغ قبل المهلة
    Approved --> Overdue : انقضاء مهلة السداد (Deadline Passed)
    Overdue --> Paid : سداد متأخر + احتساب غرامة التأخير
    Paid --> [*]
    Cancelled --> [*]
```

</details>

<br>

### ب. حالات العداد الذكي (Smart Meter Connection States)

<p align="center">
  <img src="docs/diagrams/06_state_meter.png" alt="حالات العداد الذكي" width="85%" style="border-radius: 12px; box-shadow: 0 4px 15px rgba(0,0,0,0.3);" />
</p>

<details>
<summary><b>🔍 اضغط هنا لعرض كود مخطط الحالات (Mermaid Code)</b></summary>

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

</details>

---

## 👥 5. مصفوفة الصلاحيات والأدوار (Role-Based Access Matrix - RBAC)

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

## 🔌 6. واجهات برمجة التطبيقات الأساسية (API Endpoints Overview)

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

## 🛠️ 7. دليل التثبيت والتشغيل المحلي (Installation & Setup)

### المتطلبات الأساسية (Prerequisites)
* **Python** (الإصدار 3.11 أو أحدث)
* **Node.js** (الإصدار 18 أو 20 أو أحدث) مع **npm**
* **PostgreSQL** (الإصدار 14 أو أحدث)

---

### إعداد وتشغيل الخادم الخلفي (Backend Setup)

```bash
# 1. تفعيل البيئة الافتراضية
cd ElectricityBillingSystem
venv\Scripts\activate   # لنظام Windows
# source venv/bin/activate # لنظام Linux/macOS

# 2. تثبيت الحزم البرمجية
pip install -r backend/requirements.txt

# 3. إعداد متغيرات البيئة (أنشئ ملف backend/.env):
# DB_NAME=billing_system
# DB_USER=postgres
# DB_PASSWORD=your_password
# DB_HOST=127.0.0.1
# DB_PORT=5432
# DEBUG=True

# 4. تطبيق الترحيلات وتجميع الملفات الثابتة
python backend/manage.py migrate
python backend/manage.py collectstatic --noinput

# 5. تشغيل خادم التطوير
python backend/manage.py runserver 127.0.0.1:8000
```

---

### إعداد وتشغيل لوحة التحكم (Frontend Setup)

```bash
# 1. الدخول إلى مجلد لوحة التحكم
cd admin-dashboard

# 2. تثبيت الحزم والاعتماديات
npm install

# 3. تشغيل خادم التطوير السريع (Vite)
npm run dev
```

الرابط المحلي للواجهة: `http://127.0.0.1:5173/`

---

## 🚀 8. النشر السحابي التلقائي (Cloud Deployment on Render)

المشروع مُهيأ بالكامل للنشر بنقرة واحدة عبر ملف `render.yaml`:
* **PostgreSQL Database**: قاعدة بيانات سحابية مدارة.
* **Backend Web Service**: خادم بايثون عالي الأداء مع `Gunicorn` و `WhiteNoise`.
* **Frontend Static Site**: موقع ثابت على شبكة CDN العالمية مع دعم إعادة التوجيه للـ SPA.

---

## 📁 9. هيكلية مجلدات المشروع (Repository Structure)

```text
ElectricityBillingSystem/
├── README.md                     # التوثيق الشامل والرسمي للمشروع
├── render.yaml                   # ملف إعدادات النشر السحابي (Infrastructure as Code)
├── docs/                         # التوثيقات والوسائط الرسومية
│   ├── diagrams/                 # المخططات الهندسية والسهمية (High-Res Images)
│   └── screenshots/              # لقطات شاشة موثقة للواجهات الحية
├── backend/                      # خادم Django REST Framework
│   ├── api/                      # التطبيق الرئيسي (Models, Views, Serializers, Tasks)
│   │   ├── services/             # طبقة الخدمات (Report, Meter, Payment, Audit)
│   │   ├── models.py             # نماذج قاعدة البيانات (Building, Room, Invoice, ...)
│   │   ├── views.py              # نقاط النهاية (Endpoints)
│   │   └── tasks.py              # المهام المجدولة (APScheduler)
│   ├── assets/fonts/             # الخطوط المعتمدة لتصدير الـ PDF العربي (Cairo Font)
│   └── manage.py                 # موجه أوامر Django
└── admin-dashboard/              # واجهة المستخدم React 19 + Vite
    ├── src/
    │   ├── api/                  # عميل Axios ومعالجة تجديد التوكنات
    │   ├── components/           # المكونات (FloorPlanSection, ReportsSection, ...)
    │   ├── context/              # سياق المصادقة وجلسة العمل (AuthContext)
    │   └── pages/                # الصفحات (DashboardPage, LoginPage, ...)
    ├── index.html
    └── package.json
```

---

<p align="center">
  <b>تم التطوير والتوثيق بأعلى معايير الجودة لضمان أداء مؤسسي موثوق وآمن ⚡</b>
</p>
