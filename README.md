# Kino Top — Telegram Mini App

Bu loyiha ikki qismdan iborat:

- **`bot.py`** — Telegram bot (Python, aiogram). `/start` buyrug'iga javoban mini appni ochuvchi tugma yuboradi.
- **`webapp/index.html`** — mini appning o'zi: filmlar ro'yxati, qidiruv, janr bo'yicha filtr va har bir film uchun batafsil ma'lumot oynasi. Toza HTML/CSS/JS, hech qanday freymvorksiz.

## 1-qadam: Bot yaratish

1. Telegramda [@BotFather](https://t.me/BotFather) ga yozing.
2. `/newbot` buyrug'ini yuboring va ko'rsatmalarga amal qiling.
3. Sizga beriladigan **tokenni** saqlab qo'ying.

## 2-qadam: Mini appni internetga joylash

Telegram Web App faqat **HTTPS** manzillar bilan ishlaydi, shuning uchun `webapp/index.html` faylini biror joyga joylashtirish kerak. Eng oson variantlar:

- **GitHub Pages** — repo yarating, `webapp` papkasini yuklang, Pages'ni yoqing.
- **Netlify / Vercel** — `webapp` papkasini drag-and-drop qilib yuklash mumkin (bepul).
- Test uchun: `ngrok http 8000` orqali vaqtinchalik HTTPS manzil olsa ham bo'ladi.

Joylashtirgandan so'ng sizga shunga o'xshash manzil beriladi:
`https://sizning-nomingiz.github.io/kinotop/index.html`

## 3-qadam: BotFather orqali mini appni ulash (ixtiyoriy, lekin tavsiya etiladi)

1. BotFather'da `/mybots` → botingizni tanlang → **Bot Settings** → **Menu Button** → **Configure Menu Button**.
2. Mini app manzilini yuboring — endi bot menyusida "Kino Top" tugmasi chiqadi.
3. Yoki `/newapp` orqali to'liq Mini App sifatida ro'yxatdan o'tkazishingiz mumkin.

## 4-qadam: Botni ishga tushirish

```bash
pip install -r requirements.txt

export BOT_TOKEN="BotFather'dan olingan token"
export WEBAPP_URL="https://sizning-manzilingiz/index.html"

python bot.py
```

Botga `/start` yuboring — "🎬 Kino Top'ni ochish" tugmasi chiqadi, bosilganda mini app ochiladi.

## Keyingi qadamlar (ixtiyoriy)

- Hozircha filmlar ro'yxati `webapp/index.html` ichida JavaScript massivida (statik). Buni haqiqiy ma'lumotlar bazasi yoki API bilan almashtirish mumkin.
- "Tomosha qilish" tugmasi hozircha xabar chiqaradi — buni haqiqiy video havolasiga yoki to'lov/obuna oqimiga ulash mumkin.
- Foydalanuvchi ma'lumotlarini saqlash kerak bo'lsa (masalan, sevimlilar ro'yxati), Telegram Web App'ning `initData`sini backendda tekshirib, ma'lumotlar bazasiga yozish tavsiya etiladi.
