# HIGGS Dataset Üzerinde Makine Öğrenmesi Pipeline Uygulaması

Bu proje, UCI Machine Learning Repository'de yer alan HIGGS veri seti üzerinde kapsamlı bir makine öğrenmesi süreci uygulanarak gerçekleştirilmiştir. Çalışma, Üsküdar Üniversitesi Yapay Zeka Mühendisliği bölümünde Makine Öğrenmesi dersi kapsamında final ödevi olarak hazırlanmıştır.

## 🔍 Proje Amacı

Parçacık fiziğine dayalı HIGGS veri seti kullanılarak aşağıdaki adımları içeren bir makine öğrenmesi pipeline'ı uygulanmıştır:

- Aykırı değer analizi ve temizleme (IQR yöntemi)
- Özellik ölçekleme (MinMaxScaler)
- Özellik seçimi (Mutual Information yöntemi)
- Nested Cross-Validation ile hiperparametre ayarı ve model değerlendirmesi
- ROC eğrileriyle performans analizi

## 📁 Kullanılan Veri Seti

- **Kaynak:** [UCI HIGGS Dataset](https://archive.ics.uci.edu/ml/datasets/HIGGS)
- **Orijinal Boyut:** 11 milyon gözlem, 28 öznitelik
- **Kullanılan Alt Küme:** 100.000 örnekten 5000 tanesi modelleme için ayrılmıştır
- **Etiket:** 1 = Higgs olayı, 0 = Arka plan

## ⚙️ Uygulanan Modeller

Her model, 5 outer fold ve 3 inner fold ile nested cross-validation altında değerlendirilmiştir:

- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Multi-Layer Perceptron (MLP)
- XGBoost Classifier

Hiperparametre ayarlamaları `GridSearchCV` ile yapılmıştır.

## 📊 Performans Karşılaştırması

| Model     | Accuracy | Precision | Recall | F1 Score | ROC-AUC |
|-----------|----------|-----------|--------|----------|---------|
| KNN       | 0.6138   | 0.6172    | 0.7296 | 0.6686   | 0.6514  |
| SVM       | 0.6624   | 0.6656    | 0.7401 | 0.7007   | 0.7169  |
| MLP       | 0.6754   | 0.6794    | 0.7434 | 0.7090   | 0.7322  |
| XGBoost   | 0.6894   | 0.7069    | 0.7157 | 0.7109   | 0.7587  |

## 📈 ROC Eğrileri

Tüm modellerin ROC eğrileri OvA (One-vs-All) yöntemiyle çizilmiş ve AUC skorları görselleştirilmiştir. En iyi performans XGBoost modeline aittir.

## 📚 Kullanılan Kütüphaneler

- `pandas`, `numpy`
- `scikit-learn`
- `xgboost`
- `matplotlib`, `seaborn`

## 📌 Dosya Açıklamaları

- `higgs_ml_pipeline.ipynb`: Projenin tüm kodlarını, yorumlarını, çıktıları ve görselleri içeren Jupyter Notebook dosyası
- `higgs_100k_clean.csv`: 100.000 satırlık orijinal veriden filtrelenmiş küçük örnek veri (dahil edilmediyse Google Drive'dan erişilebilir)

## 🧠 Notlar

- Tüm modellerde özellik seçimi sabit tutulmuştur (Mutual Information)
- Nested CV yapısında veri sızıntısını önlemek için outer-inner split mantığına dikkat edilmiştir
- KNN modeli sadece 5000 örnekle sınanmıştır (hesaplama maliyeti nedeniyle)

## 🏁 Sonuç

En yüksek başarı XGBoost + Mutual Information kombinasyonu ile elde edilmiştir. Bu yapı, hem doğruluk hem ROC-AUC açısından öne çıkmıştır.

---

📌 **Hazırlayan:**  
Rojbin Karakoç Çelik  
Üsküdar Üniversitesi – Yapay Zeka Mühendisliği  
Makine Öğrenmesi Final Ödevi, Haziran 2025
