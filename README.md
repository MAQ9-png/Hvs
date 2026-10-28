# ميثا ♡ — بوت ديسكورد عربي بالذكاء الاصطناعي

مشروع بوت Discord يرد بالعربية عند منشنه أو الرد على رسالته. يلزم إعداد مفاتيحك وتشغيله على استضافة قبل أن يصبح متصلًا.

## المزايا
- العربية واللهجة السعودية والخليجية.
- الرد عند المنشن أو عند الرد على رسالة كتبها البوت.
- سياق محادثة قصير مؤقت داخل كل قناة.
- يستخدم OpenAI API لتوليد الردود.

## 1) إعداد Discord
1. افتح https://discord.com/developers/applications وأنشئ تطبيقًا.
2. من قسم Bot أنشئ البوت وانسخ التوكن، ولا تشاركه مع أحد.
3. من Bot → Privileged Gateway Intents فعّل Message Content Intent.
4. من OAuth2 → URL Generator اختر bot والصلاحيات View Channels وSend Messages وRead Message History.
5. استخدم رابط الدعوة الناتج لإضافة البوت إلى السيرفر.

## 2) إعداد مفاتيح التشغيل
أنشئ مفتاح API من https://platform.openai.com/api-keys. قد تتطلب API فوترة منفصلة عن اشتراك ChatGPT.

أضف متغيرات البيئة التالية في منصة الاستضافة (لا تضع القيم السرية في GitHub):
- DISCORD_TOKEN
- OPENAI_API_KEY
- OPENAI_MODEL = gpt-4.1-mini
- MAX_HISTORY_MESSAGES = 12
- LOG_LEVEL = INFO

## 3) التشغيل محليًا
يتطلب Python 3.10 أو أحدث.

```bash
pip install -r requirements.txt
python bot.py
```

أو باستخدام Docker بعد إنشاء ملف .env محليًا:

```bash
docker compose up --build -d
docker compose logs -f
```

## ملاحظات
- يجب أن تبقى عملية البوت أو خدمة الاستضافة تعمل ليظل متصلًا.
- الذاكرة مؤقتة وتُمسح عند إعادة التشغيل.
- الرسائل والسياق القصير يُرسلان إلى OpenAI للحصول على رد.
- لا ترفع ملف .env إلى GitHub ولا ترسل توكن Discord أو مفتاح API لأي شخص.
- إذا انكشف توكن Discord، أعد توليده فورًا.
