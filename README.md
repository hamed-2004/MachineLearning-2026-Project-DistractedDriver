# 🚗 تشخیص حواس‌پرتی راننده با شبکه‌های عمیق (State Farm Distracted Driver Detection)

<div align="center">

[![Aparat Pitch Video](https://img.shields.io/badge/Aparat-Product_Pitch-ec1b24?style=for-the-badge&logo=aparat)](#YOUR_VIDEO_LINK_HERE)
[![YouTube Pitch Video](https://img.shields.io/badge/YouTube-Product_Pitch-FF0000?style=for-the-badge&logo=youtube&logoColor=white)](#YOUR_VIDEO_LINK_HERE)
[![Project Report](https://img.shields.io/badge/Google_Drive-Project_Report-1FA463?style=for-the-badge&logo=googledrive&logoColor=white)](https://drive.google.com/file/d/1n0Htn8fYO4Xi63GhZazjSBeCDGAtRvAx/view)

</div>

## 📌 معرفی پروژه (Project Overview)
این پروژه با هدف توسعه یک سیستم بینایی ماشین برای تشخیص و طبقه‌بندی خودکار حواس‌پرتی رانندگان حین رانندگی پیاده‌سازی شده است. با بهره‌گیری از مجموعه داده تصویری **State Farm**، رفتار رانندگان در ۱۰ کلاس مختلف (مانند استفاده از تلفن همراه، پیام دادن با دست چپ/راست، نوشیدن، تنظیم رادیو و رانندگی ایمن) تحلیل و دسته‌بندی می‌شود.

## 🧠 معماری‌ها و استراتژی مدل (Architectures & Strategies)
در این خط‌لوله (Pipeline) کامل یادگیری عمیق، از رویکرد **یادگیری انتقالی (Transfer Learning)** با دو معماری مطرح استفاده شده است:
1. **MobileNetV2**: مدلی سبک و بهینه‌سازی شده برای استنتاج سریع در لبه (Edge Devices).
2. **ResNet50**: مدلی عمیق‌تر با اتصالات باقی‌مانده (Residual) جهت استخراج ویژگی‌های پیچیده و مقایسه عملکرد.

**ویژگی‌های کلیدی پیاده‌سازی:**
- 🛡️ **جلوگیری از نشت داده (Data Leakage):** برای ارزیابی کاملاً واقعی، جداسازی داده‌های آموزش و اعتبارسنجی بر اساس «شناسه راننده» (۲۶ راننده یکتا) با استفاده از `GroupShuffleSplit` انجام شده است تا هیچ راننده‌ای در هر دو مجموعه تکرار نشود.
- 🔄 **Augmentation هدفمند:** عدم استفاده از قرینه‌سازی افقی (Horizontal Flip) برای جلوگیری از تداخل معنایی کلاس‌های دست چپ و راست.
- 🚀 **آموزش دو فازی (Two-Phase Training):** فاز اول برای استخراج ویژگی (یخ‌زدن لایه‌های پایه) و فاز دوم برای تنظیم دقیق (Fine-tuning) با نرخ یادگیری پایین‌تر.

## 📂 ساختار مخزن (Repository Structure)
این مخزن با رعایت معماری تمیز (Clean Structure) به بخش‌های زیر تقسیم شده است:

```text
📦 [Course-Name]-[Year]-DistractedDriver
 ┣ 📂 src/               # سورس کدهای پایتون و پیاده‌سازی مدل‌ها
 ┣ 📂 docs/              # فایل فیزیکی گزارش مکتوب (PDF) و سورس‌کدهای LaTeX
 ┣ 📂 media/             # عکس‌های خروجی پروژه و سورس کد ارائه HTML
 ┣ 📂 data/              # دیتاست پروژه (مستثنی شده به دلیل حجم بالا)
 ┣ 📜 .gitignore         # فایل‌های مستثنی‌شده از گیت‌هاب
 ┣ 📜 requirements.txt   # نیازمندی‌ها و کتابخانه‌های پایتون
 ┗ 📜 README.md          # مستندات اصلی پروژه