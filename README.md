# 📈 Apple (AAPL) Stock Price Prediction using PyTorch (LSTM vs GRU)

## Proje Özeti
Bu proje, makine öğrenimi ve derin öğrenme teknikleri kullanılarak hisse senedi fiyatlarının (Zaman Serisi) tahmin edilmesini amaçlamaktadır. Proje kapsamında PyTorch altyapısı kullanılarak LSTM (Long Short-Term Memory) ve GRU (Gated Recurrent Unit) olmak üzere iki farklı tekrarlayan sinir ağı (RNN) modeli sıfırdan inşa edilmiş ve performansları karşılaştırılmıştır.

## 🛠️ Kullanılan Teknolojiler ve Kütüphaneler
* **Python** (Veri işleme ve modelleme)
* **PyTorch** (Derin öğrenme altyapısı)
* **yfinance** (Yahoo Finance üzerinden dinamik veri çekme)
* **Pandas & NumPy** (Veri manipülasyonu ve matris işlemleri)
* **Scikit-learn** (MinMaxScaler ile veri ölçeklendirme ve MSE/RMSE metrikleri)
* **Matplotlib** (Görselleştirme)

## 📊 Veri Seti ve Ön İşleme
* **Veri Kaynağı:** `yfinance` kütüphanesi üzerinden Apple (AAPL) hisse senedinin **2018-2024** yılları arasındaki geçmiş verileri canlı olarak çekilmiştir.
* **Ön İşleme:** Sadece 'Kapanış' (*Close*) fiyatları baz alınmış, veriler `MinMaxScaler` ile 0-1 aralığına ölçeklendirilmiştir. Modelin geçmiş kalıpları öğrenebilmesi için **60 günlük kaydırma pencereleri (sliding window)** oluşturulmuş; verinin %80'i eğitim, %20'si test seti olarak ayrılmıştır.

## 🚀 Kurulum ve Çalıştırma
Projeyi kendi ortamınızda çalıştırmak için aşağıdaki adımları izleyebilirsiniz:
1. Depoyu bilgisayarınıza klonlayın.
2. Gerekli kütüphaneleri yükleyin: `pip install yfinance pandas numpy matplotlib scikit-learn torch`
3. İçerisindeki `.ipynb` (Jupyter Notebook / Google Colab) dosyasını açıp hücreleri sırasıyla çalıştırın.

## 📉 Performans Değerlendirmesi (LSTM vs GRU)
Her iki model de aynı eğitim verisi üzerinde **100 epoch** boyunca eğitilmiş olup, görünmeyen test verisi üzerindeki performansları ve süreleri aşağıdaki gibidir:

* **LSTM Modeli:** MSE: 34.87 | RMSE: 5.91 | Eğitim Süresi: ~52 saniye
* **GRU Modeli:** MSE: 30.78 | RMSE: 5.55 | Eğitim Süresi: ~34 saniye (🏆 Daha yüksek doğruluk ve hız)

**Sonuç:** Beklenildiği üzere GRU modeli, sahip olduğu daha az parametre mimarisi sayesinde eğitimi çok daha hızlı tamamlamış ve hata metriklerinde LSTM'den daha isabetli bir performans sergilemiştir.

## ⚠️ Kapanış ve Eleştirel Değerlendirme (AI Snake Oil Perspektifi)
Makine öğrenimi modelleri finansal piyasaların genel trendini (yükseliş/düşüş) yakalamakta başarılı olsa da, hisse senedi tahmini son derece karmaşık ve dış etkenlere (haberler, krizler, insan psikolojisi) açık bir alandır. *"AI Snake Oil"* kavramında da sıkça vurgulandığı gibi, yapay zekanın öngörücü gücünü özellikle bu tarz kaotik sistemlerde abartmamak ve modellerin mükemmel geleceği görebilen kusursuz yapılar olmadığını bilmek gerekir. Bu proje, finansal bir yatırım tavsiyesi sunmaktan ziyade, zaman serisi analizi ve RNN mimarilerinin çalışma mantığını anlamak için geliştirilmiş akademik bir uygulamadır.
