# 🚗 تشخیص حواس‌پرتی راننده با شبکه‌های یادگیری عمیق (State Farm Distracted Driver Detection)

<div align="center">

[![Aparat Pitch Video](https://img.shields.io/badge/Aparat-Product_Pitch-ec1b24?style=for-the-badge&logo=aparat)](#YOUR_APARAT_LINK_HERE)
[![YouTube Pitch Video](https://img.shields.io/badge/YouTube-Product_Pitch-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](#YOUR_YOUTUBE_LINK_HERE)
[![Project Report](https://img.shields.io/badge/Google_Drive-Project_Report-1FA463?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1n0Htn8fYO4Xi63GhZazjSBeCDGAtRvAx/view)

</div>

---

## 📌 معرفی پروژه (Project Overview)
این پروژه به‌عنوان پروژه پایانی **درس یادگیری ماشین (Machine Learning)** طراحی و پیاده‌سازی شده است. هدف اصلی، توسعه یک سیستم هوشمند برای تشخیص و دسته‌بندی خودکار رفتار و حالات حواس‌پرتی رانندگان بر پایه الگوریتم‌های یادگیری عمیق و بینایی ماشین است.

با استفاده از مجموعه داده تصویری معتبر **State Farm Distracted Driver Detection**، رفتارهای راننده در ۱۰ کلاس مختلف طبقه‌بندی می‌شوند:
- `c0`: رانندگی ایمن و طبیعی (Safe driving)
- `c1`: پیام دادن با دست راست (Texting - right)
- `c2`: صحبت با تلفن با دست راست (Talking on the phone - right)
- `c3`: پیام دادن با دست چپ (Texting - left)
- `c4`: صحبت با تلفن با دست چپ (Talking on the phone - left)
- `c5`: تنظیم رادیو و تجهیزات (Operating the radio)
- `c6`: نوشیدن (Drinking)
- `c7`: دست بردن به صندلی عقب (Reaching behind)
- `c8`: آرایش و مرتب‌سازی ظاهر (Hair and makeup)
- `c9`: گفتگو با سرنشین جانبی (Talking to passenger)

---

## 🧠 معماری‌ها و استراتژی‌های یادگیری (Architectures & Strategies)
برای دست‌یابی به بیشترین دقت و مقایسه جامع عملکرد، از تکنیک **یادگیری انتقالی (Transfer Learning)** بر روی دو معماری مطرح استفاده شده است:

1. **ResNet50:** مدلی عمیق با ۵۰ لایه و اتصالات باقی‌مانده (Residual Connections) جهت استخراج ویژگی‌های پیچیده دیداری و دستیابی به بالاترین دقت دسته‌بندی.
2. **MobileNetV2:** مدلی بهینه‌سازی شده با کانولوشن‌های جداپذیر عمقی (Depthwise Separable Convolutions) برای محیط‌های با منابع محاسباتی محدود و سامانه لبه (Edge Devices).

### 💡 نکات فنی و استراتژی‌های پیاده‌سازی:
- 🛡️ **جلوگیری از نشت داده (Data Leakage):** جداسازی داده‌های آموزش و اعتبارسنجی بر اساس «شناسه راننده» (Driver ID) با استفاده از `GroupShuffleSplit` انجام شده است تا رانندگان حاضر در مجموعه اعتبارسنجی در فاز آموزش کاملاً ناشناخته باقی بمانند.
- 🔄 **دستکاری هدفمند داده‌ها (Targeted Augmentation):** عدم استفاده از قرینه‌سازی افقی (`horizontal_flip=False`) جهت حفظ تفاوت معنایی کلاس‌های مربوط به دست چپ و دست راست.
- 🚀 **آموزش دو فازی (Two-Phase Fine-Tuning):**
  - **فاز اول:** انجماد (Freeze) لایه‌های پایه شبکه و آموزش فقط لایه‌های طبقه‌بندی‌کننده پایانی.
  - **فاز دوم:** باز کردن قفل لایه‌های بالایی پایه و تنطیم دقیق (Fine-tuning) با نرخ یادگیری بسیار پایین (`lr = 1e-5`).

---

## 📂 ساختار مخزن (Repository Structure)
این مخزن بر اساس ضوابط معماری تمیز (Clean Architecture) به‌صورت زیر سازمان‌دهی شده است:

```text
📦 MachineLearning-2026-Project-DistractedDriver
 ┣ 📂 src/               # سورس‌کدهای پایتون، خط‌لوله داده و پیاده‌سازی مدل‌ها
 ┣ 📂 docs/              # فایل PDF گزارش نهایی و کدهای سورس LaTeX
 ┣ 📂 media/             # نمودارهای ارزیابی، ماتریس درهم‌ریختگی و فایل ارائه HTML
 ┣ 📂 data/              # راهنمای دریافت دیتاسِت (فایل‌ها به دلیل حجم بالا مستثنی شده‌اند)
 ┣ 📜 .gitignore         # فایل مستثنی‌کننده فایل‌های سنگین و موقت
 ┣ 📜 requirements.txt   # فهرست کتابخانه‌های پایتون مورد نیاز
 ┗ 📜 README.md          # مستندات و شناسنامه اصلی پروژه
