# 🧴 Skincare Products Analysis Dashboard

تحليل شامل لأكثر من 1,100 منتج عناية بالبشرة مع داشبورد تفاعلي وملف Excel منسق.

---

## 📊 نظرة عامة على الداتاسيت

| الخاصية | القيمة |
|---------|--------|
| المصدر | [lookfantastic.com](https://www.lookfantastic.com) |
| عدد المنتجات | 1,138 |
| عدد الفئات | 14 |
| متوسط السعر | £24.02 |
| نطاق الأسعار | £1.95 – £230 |

### الأعمدة

| العمود | الوصف |
|--------|--------|
| `product_name` | اسم المنتج |
| `product_url` | رابط المنتج |
| `product_type` | فئة المنتج (Serum, Moisturiser, ...) |
| `clean_ingreds` | قائمة المكونات المنظفة |
| `price` | السعر بالجنيه الإسترليني |

---

## 📁 محتويات المشروع

```
📦 skincare-analysis/
├── 📄 README.md
├── 📊 skincare_dashboard.html     # داشبورد تفاعلي يفتح في المتصفح
├── 📊 skincare_dashboard.xlsx     # ملف Excel مع شارتات وجداول
└── 📂 data/
    └── skincare_products_clean.csv
```

---

## 🔍 أبرز النتائج

- **أكثر الفئات منتجاً:** Mask (124) و Body Wash (123)
- **أغلى الفئات:** Peel بمتوسط £49.52، ثم Serum بـ £46.17
- **أرخص الفئات:** Bath Salts بمتوسط £11.40
- **أكثر الماركات:** Clinique (46 منتج)، La Roche-Posay (37)، Garnier (33)
- **أكثر المكونات شيوعاً:** Glycerin (784 منتج)، Phenoxyethanol (613)، Parfum (579)
- **غالبية المنتجات** تتراوح أسعارها بين £10–25 (37% من المنتجات)

---

## 🚀 كيفية الاستخدام

### 1. الداشبورد التفاعلي (HTML)
افتح `skincare_dashboard.html` في أي متصفح مباشرة — لا يحتاج إنترنت أو تثبيت.

### 2. ملف Excel
افتح `skincare_dashboard.xlsx` في Microsoft Excel أو LibreOffice Calc.

يحتوي على شيتين:
- **Dashboard** — ملخص مرئي مع شارتات وجداول
- **Raw Data** — جميع المنتجات قابلة للفلترة والبحث

### 3. تحليل Python
```python
import pandas as pd

df = pd.read_csv('data/skincare_products_clean.csv')
df['price_num'] = df['price'].str.replace('£', '').astype(float)

# فلترة حسب الفئة
serums = df[df['product_type'] == 'Serum']

# أغلى 10 منتجات
top10 = df.nlargest(10, 'price_num')[['product_name', 'product_type', 'price']]
print(top10)
```

---

## 📦 المتطلبات (للتحليل البرمجي)

```
pandas
openpyxl
```

```bash
pip install pandas openpyxl
```

---

## 📝 ملاحظات

- المكونات في عمود `clean_ingreds` محفوظة كـ Python list داخل string — استخدم `ast.literal_eval()` لتحويلها.
- الأسعار محفوظة كنص بصيغة `£XX.XX` — تحتاج إزالة رمز `£` قبل التحويل لأرقام.

---

## 📄 الرخصة

هذا المشروع للأغراض التعليمية والتحليلية فقط. البيانات مصدرها lookfantastic.com.
