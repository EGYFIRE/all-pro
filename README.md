# كاشير المطعم الاحترافي - إصدارات التحميل

هذا الريبو **عام (Public)** ومخصص فقط لتوزيع نسخ البناء الجاهزة (exe للكاشير، apk لتطبيق
كابتن الصالة) عبر [Releases](../../releases). **السورس الكامل للمشروع خاص (Private)** في
ريبو منفصل ولا يظهر هنا أبداً — الـ workflows هنا بتاخد الكود وقت البناء فقط من الريبو
الخاص عبر مفتاح وصول للقراءة، وبتنشر الملف الناتج (exe/apk) كـ Release هنا.

السبب: الريبوهات العامة على GitHub بتاخد دقائق تشغيل (Actions) مجانية وغير محدودة، على
عكس الريبوهات الخاصة اللي ليها حد شهري مشترك بين كل مشاريعك.

## تحميل آخر نسخة

- **البرنامج (Windows exe)**: من تبويب [Releases](../../releases) — دوّر على أحدث تاج
  بيبدأ بـ `build-`.
- **تطبيق كابتن الصالة (Android apk)**: من نفس التبويب — دوّر على أحدث تاج بيبدأ بـ
  `apk-v0.1.`.

## إعداد لمرة واحدة (لصاحب المشروع فقط)

عشان الـ workflows هنا تقدر توصل للسورس الخاص، لازم تتعمل الخطوتين دول مرة واحدة بس:

1. اعمل Personal Access Token من
   [github.com/settings/tokens](https://github.com/settings/tokens) → **Generate new
   token (classic)** → صلاحية `repo` بس (أو fine-grained token بصلاحية Read-only على
   Contents لريبو `App-exe-pc` وحده لو حابب أدق صلاحية) → انسخ التوكن.
2. من إعدادات الريبو ده: **Settings → Secrets and variables → Actions → New repository
   secret** → الاسم `SOURCE_REPO_TOKEN` → الصق التوكن → Save.

بعد الخطوتين دول، أي تشغيل يدوي (workflow_dispatch) لأي workflow هنا هيشتغل عادي.
