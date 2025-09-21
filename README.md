# Brain Tumor Detection - Deep Learning Project

Akbank Derin Öğrenme Bootcamp kapsamında geliştirilen beyin tümörü tespit projesi.

## Proje Amacı
MRI görüntüleri kullanarak beyin tümörlerini otomatik olarak sınıflandıran derin öğrenme modeli geliştirmek.

## Veri Seti
- **Kaynak:** Brain Tumor MRI Dataset (Kaggle)
- **Toplam Görüntü:** 7,022 MRI görüntüsü
- **Sınıflar:** Glioma, Meningioma, No Tumor, Pituitary
- **Format:** 224x224 RGB görüntüler

## Kullanılan Yöntemler
- **Framework:** TensorFlow/Keras
- **Model:** Transfer Learning (MobileNetV2)
- **Optimizer:** Adam
- **Loss:** Categorical Crossentropy

## Sonuçlar
- **Test Accuracy:** %91.0
- **En iyi performans:** Pituitary (%96 F1-score)
- **Model boyutu:** 2.4M parametre

## Kaggle Notebook
[Brain Tumor Detection Project](https://www.kaggle.com/code/nuricanaksu/brain-tumor-detection-transfer-learning)

## Bootcamp Hedefleri
- ✅ CNN tabanlı model
- ✅ Transfer Learning
- ✅ Model değerlendirme
- ✅ Görselleştirmeler

**Geliştirici:** Nuri Can Aksu  
**Tarih:** Eylül 2025
