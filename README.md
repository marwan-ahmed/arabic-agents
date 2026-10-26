<div dir="rtl">

# قالب AGENTS.md بالعربية

**عقد عمل لوكلاء البرمجة بالذكاء الاصطناعي: كود أقل، وأمان أعلى، وأسئلة قبل الأخطاء لا بعدها.**

إعداد [Marwan Ahmed](https://marwan-ahmed.com/) · [English](README.en.md)

ملف قواعد واحد تضعه في جذر مشروعك، فيقرؤه وكيل البرمجة في بداية كل جلسة. أنت تكتب اسم المشروع فقط،
والوكيل يستنتج الباقي (اللغات، والأُطر، وقاعدة البيانات، والأوامر) من ملفات المشروع نفسه ويعرضه عليك للتأكيد.

## لماذا هذا القالب؟

- **يمنع الإفراط في الكتابة:** مبادئ Karpathy الأربعة — فكّر قبل أن تكتب، والبساطة أولاً، والتعديلات الجراحية، والتنفيذ الموجّه بالهدف.
- **الأمان شرط لا خيار:** المصادقة والصلاحيات، وعزل المستأجرين (multi-tenancy)، والتحقق من المدخلات، والأسرار، والأنماط المحظورة.
- **يضبط تصرفات الوكيل نفسه:** المحتوى الخارجي بيانات لا أوامر، وموافقة قبل الأوامر الخطرة، ولا commit بلا طلب، وتحقق من الحزم قبل تثبيتها.
- **بالعربية:** مع إبقاء المصطلحات التقنية بالإنجليزية كما يستخدمها المطوّرون.

## الملفات

| الملف | الغرض |
| --- | --- |
| [AGENTS.md](AGENTS.md) | القواعد نفسها — يُنسخ إلى مشروعك |
| [AGENTS.lite.md](AGENTS.lite.md) | نسخة مختصرة من القواعد — تُنسخ إلى مشروعك باسم `AGENTS.md` بدلاً من الكاملة |
| [AGENT_STATE.md](AGENT_STATE.md) | حالة العمل المتغيرة (المرحلة والمودول النشط) — يُنسخ إلى مشروعك |
| [CHANGELOG.md](CHANGELOG.md) | سجل إصدارات القالب |
| [LICENSE](LICENSE) | ترخيص هذا القالب (MIT) |
| [NOTICE](NOTICE) | إسناد المصدر وترخيصه |

## محتوى القالب

| القسم | الموضوع |
| --- | --- |
| 0 | المبادئ العليا وترتيب الأولويات عند التعارض |
| 1 | هوية المشروع وبروتوكول التهيئة |
| 2 | طريقة العمل (مبادئ Karpathy الأربعة) |
| 3 | اقتصاد التوكنز |
| 4 | منع الهلوسة |
| 5 | الأمان، ومنه قواعد تشغيل الوكيل (5.7) |
| 6 | جودة الكود |
| 7 | إدارة السياق |
| 8 | الأنماط المحظورة |
| 9 | بروتوكول التغييرات و migrations |
| 10 | مرجع سريع |
| 11 | قواعد خاصة بمشروعك |
| 12 | الإصدار والصيانة |

## النسخة المختصرة

`AGENTS.lite.md` يحتفظ بجوهر القواعد بصياغة مضغوطة وبلا تكرار، فيخفّ السياق الذي يُحمَّل في كل جلسة. أرقام أقسامه كما في النسخة الكاملة.

| | الكاملة `AGENTS.md` | المختصرة `AGENTS.lite.md` |
| --- | --- | --- |
| الطول | ~530 سطراً (~24 KB) | ~120 سطراً (~12 KB) |
| الأقسام | 0–12 | 0، 1، 2، 4، 5، 7.3–7.4، 8، 11 |
| الأسلوب | شرح وأمثلة كود وقوائم تحقق | قاعدة في سطر، ومثال قصير عند الحاجة |
| ما لا تتضمنه | — | اقتصاد التوكنز (3)، وجودة الكود (6)، وإعلانات الجلسة (7.1–7.2)، وبروتوكول التغييرات و migrations (9)، والمرجع السريع (10)، والإصدار (12) |

## التثبيت

من جذر مشروعك، شغّل أحد الأمرين. ينزّل الملفين، ولا يستبدل ملفاً موجوداً.

<div dir="ltr">

**bash** — macOS / Linux / Git Bash

```bash
for f in AGENTS.md AGENT_STATE.md; do [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f"; done
```

**PowerShell** — Windows

```powershell
foreach ($f in 'AGENTS.md','AGENT_STATE.md') { if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$f" -OutFile $f -UseBasicParsing } }
```

</div>

**أو النسخة المختصرة:** الأمران التاليان يحفظان `AGENTS.lite.md` باسم `AGENTS.md` مع `AGENT_STATE.md`، ولا يستبدلان ملفاً موجوداً.

<div dir="ltr">

**bash** — macOS / Linux / Git Bash

```bash
for s in AGENTS.lite.md AGENT_STATE.md; do f=${s/.lite/}; [ -e "$f" ] && echo "skip $f (exists)" || curl -fsSLo "$f" "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s"; done
```

**PowerShell** — Windows

```powershell
foreach ($s in 'AGENTS.lite.md','AGENT_STATE.md') { $f = $s -replace '\.lite', ''; if (Test-Path $f) { "skip $f (exists)" } else { Invoke-WebRequest "https://raw.githubusercontent.com/marwan-ahmed/arabic-agents/main/$s" -OutFile $f -UseBasicParsing } }
```

</div>

## طريقة الاستخدام

1. ثبّت `AGENTS.md` و `AGENT_STATE.md` في جذر مشروعك بأمر التثبيت أعلاه، أو انسخهما يدوياً.
2. اكتب اسم المشروع في الحقل `PROJECT_NAME` بالقسم 1.
3. افتح جلسة مع الوكيل: سيستنتج باقي الحقول من ملفات المشروع (القسم 1.1)، ويعرض كل قيمة ومصدرها، وينتظر تأكيدك.
4. أضف قواعد مشروعك في القسم 11.
5. في الفرق: أضف `AGENT_STATE.md` إلى `.gitignore`، فلكل مطوّر مودوله النشط.
6. لا تحذف سطر الإسناد في آخر `AGENTS.md`؛ يشترطه ترخيص المصدر.

## التوافق

`AGENTS.md` [صيغة مفتوحة](https://agents.md) تقرؤها أدوات برمجة كثيرة بالذكاء الاصطناعي.
إن كانت أداتك تقرأ اسم ملف آخر، فراجع توثيقها لتوجيهها إلى `AGENTS.md`.

## الإصدار

الإصدار الحالي **2.1.0** — التفاصيل في [CHANGELOG.md](CHANGELOG.md).

## الإسناد والترخيص

- القسم 2 مقتبس من [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills) لـ forrestchang (MIT)، المبني على ملاحظات Andrej Karpathy حول أخطاء نماذج اللغة في البرمجة. التفاصيل في [NOTICE](NOTICE).
- هذا القالب مرخّص بـ [MIT](LICENSE).

**المشرف على القالب:** [Marwan Ahmed](https://marwan-ahmed.com/)

</div>
