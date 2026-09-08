# إصدارات التحميل — كل المشاريع

هذا الريبو **عام (Public)** ومخصص فقط لبناء وتوزيع النسخ الجاهزة عبر
[Releases](../../releases). **سورس كل مشروع يفضل خاص (Private)** في ريبو منفصل ولا يظهر
هنا أبداً — الـ workflows هنا بتاخد الكود وقت البناء فقط من الريبو الخاص عبر مفتاح وصول
للقراءة (`SOURCE_REPO_TOKEN`)، وبتنشر الملف الناتج (exe/apk/aab) كـ Release هنا.

السبب: الريبوهات العامة على GitHub بتاخد دقائق تشغيل (Actions) مجانية وغير محدودة، على
عكس الريبوهات الخاصة اللي ليها حد شهري مشترك بين كل مشاريعك.

## المشاريع والتاجات

كل مشروع له workflow منفصل وتاج مميز، عشان الإصدارات ما تتلخبطش مع بعض:

| المشروع | الـ workflow | التاج | الريبو الخاص |
|---|---|---|---|
| كاشير المطعم (Windows) | `build-windows.yml` | `build-…` | `EGYFIRE/App-exe-pc` |
| كابتن الصالة (Android) | `build-android.yml` | `apk-v0.1.…` | `EGYFIRE/App-exe-pc` |
| قُطوف — فيديوهات قصيرة إسلامية (Android) | `qutoof-android.yml` | `qutoof-v…` | `EGYFIRE/Short-video` |
| ميعاد — إدارة الدروس الخصوصية (Android + Web) | `miaad-android.yml` | `miaad-v…` | `EGYFIRE/teacher` |

## الإصدارات مسوّدات، لا منشورات

الريبو ده **عام** لسبب واحد: دقائق Actions المجانية. مش عشان النسخ تكون متاحة لأي حد.

عشان كده **كل الـ workflows هنا** بتنشر إصداراتها **كمسوّدة (draft)**: الملفات ما تظهرش في
صفحة Releases للزوّار ولا تتحمّل بروابطها، وما يشوفها إلا صاحب الريبو وهو مسجّل دخول.

أي workflow جديد لازم ياخد نفس السطر تحت `softprops/action-gh-release`:

```yaml
          draft: true
```

**والتوزيع للعملاء يبقى منك انت**: نزّل الملف من صفحة الإصدار وابعته بالطريقة اللي تناسبك.
لو احتجت رابطًا عامًا لمشروع بعينه، انشر إصداره يدويًا من زر **Publish release**.

ولو في إصدارات **منشورة بالفعل** وعايز تخفيها أو تمسح ملفاتها، شغّل
[`release-guard.yml`](.github/workflows/release-guard.yml) من تبويب Actions وحدّد بادئة التاج.

## تحميل آخر نسخة

من تبويب [Releases](../../releases) وانت **مسجّل دخول بحسابك** — دوّر على أحدث تاج ببادئة
مشروعك من الجدول فوق. المسوّدات بتظهر فوق القائمة بعلامة `Draft`.

## إضافة مشروع جديد

انسخ أي workflow موجود وغيّر: اسم الملف، `repository` و`ref` في خطوة الـ checkout،
أوامر البناء، وبادئة التاج. خلّي البادئة فريدة للمشروع.

## إعداد لمرة واحدة (لصاحب المشروع فقط)

عشان الـ workflows هنا تقدر توصل للسورس الخاص، لازم تتعمل الخطوتين دول مرة واحدة بس:

1. اعمل Personal Access Token من
   [github.com/settings/tokens](https://github.com/settings/tokens) → **Generate new
   token (classic)** → صلاحية `repo` بس (أو fine-grained token بصلاحية Read-only على
   Contents لريبو `App-exe-pc` وحده لو حابب أدق صلاحية) → انسخ التوكن.
2. من إعدادات الريبو ده: **Settings → Secrets and variables → Actions → New repository
   secret** → الاسم `SOURCE_REPO_TOKEN` → الصق التوكن → Save.

بعد الخطوتين دول، أي تشغيل يدوي (workflow_dispatch) لأي workflow هنا هيشتغل عادي.
