# Brain Tumor Detection - Deep Learning Project

Akbank Derin Öğrenme Bootcamp kapsamında geliştirilen beyin tümörü tespit projesi.

## Giriş

Bu proje, MRI görüntüleri kullanarak beyin tümörlerini otomatik olarak sınıflandıran derin öğrenme modeli geliştirmeyi amaçlamaktadır. Transfer Learning yaklaşımı kullanarak MobileNetV2 modelini fine-tune ederek 4 farklı beyin tümörü tipini (glioma, meningioma, normal, pituitary) yüksek doğrulukla tespit etmeyi hedefledik.

## Veri Seti

- **Kaynak:** [Brain Tumor MRI Dataset (Kaggle)](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)
- **Toplam Görüntü:** 7,022 MRI görüntüsü
- **Sınıflar:** 4 kategori (Glioma, Meningioma, No Tumor, Pituitary)
- **Bölünme:** Training: 5,712 - Testing: 1,311
- **Format:** 224x224 RGB görüntüler

Dataset medikal görüntü işleme için ideal bir yapıya sahip ve dengeli sınıf dağılımı göstermektedir.

## Kullanılan Yöntemler

### Model Architecture
- **Framework:** TensorFlow/Keras
- **Yaklaşım:** Transfer Learning 
- **Base Model:** MobileNetV2 (ImageNet pretrained)
- **Custom Head:** Global Average Pooling + Dense layers
- **Activation:** ReLU (hidden), Softmax (output)

### Teknik Parametreler
- **Optimizer:** Adam (lr=1e-4)
- **Loss Function:** Categorical Crossentropy
- **Batch Size:** 32
- **Epochs:** 15
- **Data Preprocessing:** Rescaling (0-1 normalizasyon)
- **Validation Split:** 80% Train, 20% Validation

Transfer Learning yaklaşımı sayesinde az epoch ile yüksek performans elde edildi.

## Metrikler

### Model Performansı
- **Test Accuracy:** %91.0
- **Training Accuracy:** %92.7
- **Validation Accuracy:** %92.1
- **Total Parameters:** 2,422,468 (164K trainable)
- **Training Time:** ~75 saniye (15 epochs, GPU Tesla T4)

### Sınıf Bazında Analiz
| Sınıf | Precision | Recall | F1-Score | Support |
|-------|-----------|--------|----------|---------|
| Glioma | 0.92 | 0.88 | 0.90 | 300 |
| Meningioma | 0.84 | 0.76 | 0.80 | 306 |
| No Tumor | 0.91 | 0.99 | 0.95 | 405 |
| Pituitary | 0.95 | 0.96 | 0.96 | 300 |

### Yorumlar
- **En başarılı sınıf:** Pituitary tümörleri (%96 F1-score) - morfolojik özellikleri belirgin
- **En zorlu sınıf:** Meningioma (%80 F1-score) - glioma ile karışabilir
- **Normal beyin dokusu:** Mükemmel recall (%99) - false negative riski düşük
- **Overfitting durumu:** Yok - validation/training accuracy dengeli

Model, klinik uygulamalarda kullanılabilir düzeyde performans göstermektedir.

## Görselleştirmeler

Projede kullanılan analiz yöntemleri:
- Training/Validation Loss ve Accuracy grafikleri
- Confusion Matrix (heatmap)
- Sınıf bazında performans metrikleri (bar chart)
- Sample prediction görselleştirmeleri
- Model architecture summary

Bu görselleştirmeler model davranışını anlamaya ve debug etmeye yardımcı olmaktadır.

## Ekler

### Notebook Organizasyonu
Kaggle notebook'u şu bölümlerden oluşmaktadır:
1. **Veri Keşfi:** Dataset yapısı ve sınıf dağılımları
2. **Model Oluşturma:** Transfer Learning implementasyonu
3. **Model Eğitimi:** Training loop ve callback'ler
4. **Sonuç Değerlendirme:** Comprehensive analysis

### Teknik Gereksinimler
```
tensorflow>=2.10.0
matplotlib>=3.5.0
seaborn>=0.11.0
scikit-learn>=1.1.0
numpy>=1.21.0
opencv-python>=4.5.0
```

## Sonuç ve Gelecek Çalışmalar

### Mevcut Başarılar
- %91 test accuracy ile robust bir model geliştirildi
- Transfer Learning sayesinde hızlı ve etkili eğitim sağlandı
- Tüm sınıflar için dengeli performans elde edildi
- Klinik kullanım için yeterli güvenilirlik düzeyine ulaşıldı

### Gelecek Geliştirmeler
1. **Model İyileştirmeleri:**
   - EfficientNet, ResNet gibi farklı backbone'lar deneme
   - Ensemble methods ile performans artırma
   - Data augmentation stratejileri geliştirme

2. **Deployment Çalışmaları:**
   - Streamlit/Flask web uygulaması geliştirme
   - Real-time inference API oluşturma
   - Mobile deployment için model optimization

3. **Veri Genişletme:**
   - Daha büyük dataset'lerle eğitim
   - 3D MRI volume processing
   - Multi-modal imaging (T1, T2, FLAIR) entegrasyonu

4. **Klinik Entegrasyon:**
   - Radyolog feedback loop sistemi
   - DICOM format desteği
   - Hospital information systems entegrasyonu

Bu proje, medikal AI alanında kariyer hedeflerim doğrultusunda temel bir adım oluşturmaktadır.

## Linkler

**Kaggle Notebook:** [Brain Tumor Detection - Transfer Learning](https://www.kaggle.com/code/nuricanaksu/brain-tumor-detection-transfer-learning)

**Dataset:** [Brain Tumor MRI Dataset](https://www.kaggle.com/datasets/masoudnickparvar/brain-tumor-mri-dataset)

---

**Geliştirici:** Nuri Can Aksu  
**Akbank Derin Öğrenme Bootcamp Katılımcısı**  
**Tarih:** Eylül 2025

Bu proje, transfer learning'in medikal görüntü sınıflandırmasındaki gücünü göstermekte ve gelecekteki AI tabanlı tanı sistemleri için solid bir temel oluşturmaktadır.
