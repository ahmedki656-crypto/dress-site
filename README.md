# Inventory Dresses Web Viewer

عرض مباشر لمخزون الفساتين باستخدام Firebase Firestore.

## المميزات
- تحديث مباشر عند تغير البيانات في Firebase.
- البحث والتصفية حسب الموديل، اللون، أو المقاس.
- واجهة سهلة وبسيطة مناسبة للجوال والحاسوب.

## طريقة الاستخدام
1. جهز مشروع Firebase مع Firestore.
2. خزّن بيانات الفساتين في مجموعة `dresses` بحيث يكون لكل فستان:
   - model (نص)
   - color (نص)
   - size (نص)
   - status (نص) — مثلاً `"in_stock"` للفستان المتوفر.
3. حدّث إعدادات Firebase في ملف `index.html` بمعلومات مشروعك.
4. رفع ملف `index.html` على GitHub Pages أو أي استضافة ثابتة.
5. افتح الموقع على أي جهاز وتابع المخزون مباشرة.
6. استخدم مربع البحث لتصفية النتائج.

## ملاحظة
تأكد من قواعد الأمان في Firebase تسمح بقراءة مجموعة `dresses`.

```json
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /dresses/{dressId} {
      allow read: if true;  // عدّل حسب الحاجة
      allow write: if false; // لا يسمح بالكتابة من الموقع
    }
  }
}
