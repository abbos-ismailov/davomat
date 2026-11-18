<div align="center">

<img src="assets/logo.png" width="140" alt="Davomat hisobi logosi">

# 📚 Davomat hisobi

**Repetitor va oʻqituvchilar uchun davomat, daromad va oʻquvchilar nazorati ilovasi**

![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![Firebase](https://img.shields.io/badge/Firebase-FFCA28?logo=firebase&logoColor=black)
![Vercel](https://img.shields.io/badge/Vercel-000000?logo=vercel&logoColor=white)
![Mobile friendly](https://img.shields.io/badge/📱-Mobile%20friendly-2563eb)

</div>

---

## ✨ Nima qiladi?

Har bir darsdan keyin **nechta oʻquvchi keldi / kelmadi** ekanini kiritasiz, ilova esa shu oydagi **daromadingizni** avtomatik hisoblab boradi. Hamma maʼlumot bulutda saqlanadi, telefon va kompyuterda bir xil koʻrinadi.

| | |
|---|---|
| 💰 **Daromad hisobi** | Har bir davomat uchun pul oyning kunlariga qarab hisoblanadi |
| 👥 **4 ta guruh** | Guruh nomi, dars vaqti va kunlarini oʻzingiz oʻzgartirasiz |
| 📅 **Kunlik daromad** | Bugun va har kuni qancha pul tushgani |
| 📈 **Oyma-oy taqqoslash** | Oʻtgan oy bilan kunma-kun diagramma: koʻpayyaptimi yoki kamayyaptimi |
| 🧑‍🎓 **Oʻquvchilar nazorati** | Kim darsni umuman qoldirmayapti, kim necha marta progul qilgan |
| ☁️ **Bulutli sinxronlash** | Telefon va kompyuter bir xil maʼlumotni koʻradi |
| 📴 **Oflayn ishlaydi** | Internet boʻlmasa ham kiritasiz, ulanganda oʻzi yuboriladi |
| 📥 **Excel hisobot** | Tanlangan oy uchun darslar roʻyxatini yuklab olish |

---

## 📸 Skrinshotlar

<div align="center">

| ➕ Kiritish | 📊 Hisob | 📋 Roʻyxat |
|:---:|:---:|:---:|
| <img src="assets/screens/kiritish.png" width="220"> | <img src="assets/screens/hisob.png" width="220"> | <img src="assets/screens/royxat.png" width="220"> |

| 👥 Oʻquvchilar | ✅ Yoqlama |
|:---:|:---:|
| <img src="assets/screens/oquvchilar.png" width="220"> | <img src="assets/screens/yoqlama.png" width="220"> |

<sub>Skrinshotlardagi ismlar va summalar namuna (demo) maʼlumotlar.</sub>

</div>

---

## 💰 Pul qanday hisoblanadi?

Barcha oʻquvchilar hamma darsga qatnashsa, oyiga **100 000 soʻm** tushadi. Bitta davomat narxi oyning uzunligiga bogʻliq:

| Oy | Boʻluvchi | 1 davomat narxi |
|---|---|---|
| 31 kunlik oy | 13,5 | 100 000 ÷ 13,5 ≈ **7 407 soʻm** |
| Boshqa oylar | 13 | 100 000 ÷ 13 ≈ **7 692 soʻm** |

> Summa va boʻluvchilarni ⚙️ **Sozlamalar** boʻlimida oʻzgartirish mumkin.

**Oylik daromad = shu oydagi jami davomat × 1 davomat narxi**

---

## 🧭 Boʻlimlar

- **➕ Kiritish** — umumiy pul, bugungi daromad, guruhlar boʻyicha summa va yangi dars qoʻshish formasi. Sana va hozirgi vaqtga qarab guruh avtomatik tanlanadi.
- **📊 Hisob** — oʻtgan oy bilan taqqoslash diagrammasi va kunlik daromad roʻyxati.
- **📋 Roʻyxat** — kiritilgan darslar (eng yangisi tepada), tahrirlash, oʻchirish, Excel yuklash va kelmaganlarni belgilash.
- **👥 Oʻquvchilar** — guruhlar boʻyicha oʻquvchilar roʻyxati (yigʻiladigan) va oylik progul statistikasi.

### ✅ Yoqlama qanday ishlaydi?

1. Guruhga oʻquvchilarni bir marta kiritasiz.
2. Dars tugagach **Keldi 10, Kelmadi 2** deb sonlarni kiritib saqlaysiz.
3. Keyin **📋 Roʻyxat** da shu dars yonidagi **👥** tugmasini bosib, kelmagan 2 ta oʻquvchini belgilaysiz.
4. 👥 Oʻquvchilar boʻlimida kim necha marta kelmagani va qaysi kunlari ekani koʻrinadi.

---

## 🛠 Texnologiyalar

- **Frontend:** bitta `index.html` fayl (HTML, CSS, vanilla JavaScript), kutubxonasiz
- **Maʼlumotlar bazasi:** Firebase Firestore (oflayn kesh bilan)
- **Kirish:** Firebase Authentication (email/parol va Google)
- **Hosting:** Vercel
- **Excel:** SheetJS (faqat hisobot yuklashda yuklanadi)

---

## 🚀 Oʻrnatish

### 1. Firebase loyihasini tayyorlash

1. [Firebase Console](https://console.firebase.google.com) da yangi loyiha oching.
2. **Build → Firestore Database → Create database** (Production mode).
3. **Build → Authentication → Sign-in method** da **Email/Password** va **Google** ni yoqing.
4. **Authentication → Settings → Authorized domains** ga Vercel manzilingizni qoʻshing.
5. **Project settings → Your apps → Web (`</>`)** orqali `firebaseConfig` ni oling.

### 2. Xavfsizlik qoidalari (majburiy!)

**Firestore → Rules** ga quyidagini qoʻyib **Publish** qiling. Bu har bir foydalanuvchiga faqat oʻz maʼlumotini koʻrish imkonini beradi:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid}/{document=**} {
      allow read, write: if request.auth != null && request.auth.uid == uid;
    }
  }
}
```

### 3. Kalitlarni ulash

`index.html` ichidagi `FBCFG` obyektini oʻz kalitlaringiz bilan almashtiring:

```js
const FBCFG = {
  apiKey: "...",
  authDomain: "loyiha.firebaseapp.com",
  projectId: "loyiha",
  storageBucket: "loyiha.firebasestorage.app",
  messagingSenderId: "...",
  appId: "..."
};
```

> ℹ️ Firebase web kalitlari maxfiy emas. Maʼlumotni himoya qiladigan narsa yuqoridagi **Rules**.

### 4. Vercel ga joylash

1. Reponi GitHub ga yuklang.
2. [Vercel](https://vercel.com) da **Add New → Project** orqali shu repoʻni tanlang.
3. Sozlamalarsiz **Deploy** bosing, tayyor.

---

## 📱 Telefon va kompyuterga ilova sifatida oʻrnatish

- **Telefon (Chrome):** ⋮ → **Bosh ekranga qoʻshish**
- **Kompyuter (Chrome):** ⋮ → **Uzatish, saqlash va ulashish → Yorliq yaratish** → *Oyna sifatida ochish*
- **Kompyuter (Edge):** ⋯ → **Ilovalar → Bu saytni ilova sifatida oʻrnatish**

---

## 🗂 Maʼlumotlar tuzilmasi

```
users/{uid}/
├── lessons/{id}    # sana, guruh, keldi, kelmadi, roster, absent
├── students/{id}   # ism, guruh, off (chiqarilgan)
└── cfg/main        # oylik summa, boʻluvchilar, guruhlar (nom, vaqt, kunlar)
```

## 📁 Loyiha tuzilmasi

```
.
├── index.html          # butun ilova
├── README.md
└── assets/
    ├── logo.png
    ├── logo.svg
    └── screens/        # README uchun skrinshotlar
```

---

## 🔒 Maxfiylik

- Har bir foydalanuvchi maʼlumoti faqat oʻz akkauntiga bogʻlangan.
- Oʻquvchilar ismlari ham shu akkauntda, bulutda saqlanadi.
- Brauzer xotirasini tozalash maʼlumotni oʻchirmaydi, qayta kirsangiz hammasi joyida.

## 🗺 Rejalar

- [ ] Android uchun APK
- [ ] Oylik Excel hisobotga kelmagan oʻquvchilar ismlari
- [ ] Guruhlar sonini oʻzgartirish
- [ ] Oʻquvchi toʻlovlari hisobi

---

<div align="center">

Oʻqituvchilar uchun ❤️ bilan yaratildi

</div>
