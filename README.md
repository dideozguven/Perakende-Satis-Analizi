# Retail-Store-Sales-Prediction
Bu proje Python dili ile geliştirilmiş bir satış analizi model öğrenmesi uygulamasıdır.

Bu proje, bir perakende mağazası satış verileri üzerinde çeşitli makine öğrenmesi modelleri kullanarak toplam harcamaları tahmin etmeyi amaçlamaktadır.
# Veri Seti Hakkında
Projede kullanılan veri seti toplam 11 sütun ve 12576 satırdan oluşuyor.
  ## Sütunlar
  **Transaction ID:** Her satış işlemi için benzersiz bir kimlik numarasıdır. Bu, her bir işlemi diğerlerinden ayıran bir tanımlayıcıdır.Bu sütun için eksik veri yoktur.Veri tipi object'tir.
  
  **Customer ID:** Her müşteri için benzersiz bir kimlik numarasıdır.Başlangıçta bu sütun için eksik veri yoktur.Veri tipi object'tir.
  
  **Category:** Satılan ürünlerin ait olduğu kategori (örneğin, elektronik, giyim, gıda vb.) hakkında bilgi verir.Bu stünda eksik veri yoktur.Veri tipi object'tir.
  
  **Item:** Satılan ürünlerin adı ve kodu hakkında bilgi verir.1213 eksik veri bulunduruyor.Veri tipi object'tir.
  
  **Price Per Unit:** Ürünün birim fiyatıdır.609 eksik veri barındırıyor.Veri tipi float'tur.
  
  **Quantity:** Satılan ürünlerin adedi hakkında bilgi verir.604 eksik veri bulunuyor.Veri tipi float'tur.
  
  **Total Spent:** Müşterinin bir işlemde yaptığı toplam harcama tutarıdır.604 eksik veri bulunuyor.Veri tipi float'tur.
  
  **Payment Method:** Müşterinin ödeme yaptığı yöntem (örneğin, kredi kartı, nakit vb.). Bu sütun, ödeme türünü tanımlar.Eksik veri yoktur.Veri tipi object'tir.
  
  **Location:** Satış işleminin yapıldığı yer (onlineda,mağazada gibi) hakkında bilgi verir.Eksik veri yoktur.Veri tipi object'tir.
  
  **Transaction Date:** Satış işleminin yapıldığı tarihtir.Eksik veri yoktur.Veri tipi object'tir.
  
  **Discount Applied:** İşlemde indirim uygulanıp uygulanmadığı ile ilgili bilgi verir.4199 eksik veri bulunuyor.Veri tipi object'tir.
  
# Veri Önişleme
Bu veri kümesindeki eksik veriler, farklı sütunlarda farklı oranlarda bulunmaktadır. Veri önişleme sürecinde, sayısal sütunlardaki eksik veriler ortalama değerlerle dolduruldu, kategorik sütunlardaki eksik veriler ise en sık görülen değerlerle tamamlandı. Ayrıca, Item, Price Per Unit, Quantity, Total Spent ve Discount Applied gibi sütunlarda eksik veriler bulunması nedeniyle, bu sütunlardaki eksiklikler, analizlerde doğru sonuçlar elde edebilmek için dikkatlice ele alındı. Kategorik verilerde Label Encoding kullanılarak sayısal verilere dönüştürme işlemi yapıldı.
# Kullanılan Kütüphaneler
## pandas
Veri manipülasyonu ve analizi için kullanılır, özellikle CSV dosyasından veri okuma ve veri çerçeveleri ile çalışmak için idealdir.
## numpy
Sayısal hesaplamalar ve matematiksel işlemler için kullanılır, özellikle verilerin işlenmesi ve hesaplamalar yapılırken hız ve verimlilik sağlar.
## scikit-learn
Makine öğrenmesi algoritmalarını ve model değerlendirme metriklerini sağlamak için kullanılır, model oluşturma, eğitim ve test işlemleri için gereklidir.
## matplotlib 
Verilerin görselleştirilmesi için kullanılır, model performansını görsel olarak sunmak ve analiz sonuçlarını grafiklerle göstermek için idealdir.

# Kullanılan Modeller
## Linear Regression (Doğrusal Regresyon)
"Transaction ID", "Customer ID" ve "Transaction Date" gibi tahmin modeli için gereksiz veya doğrudan etkisi olmayan değişkenler kaldırılarak özellikler (X) oluşturulmuştur. Ayrıca, "Total Spent" bağımlı değişken olarak seçilmiştir çünkü modelin bu değeri tahmin etmesi hedeflenmektedir.

Ardından, train_test_split fonksiyonu kullanılarak veri seti %80 eğitim (%20 test) olacak şekilde ayrılmıştır. "random_state=42" parametresi kullanılarak bölme işlemi tekrarlanabilir hale getirilmiş, böylece her çalıştırmada aynı veri seti ayrımı sağlanmıştır. Bu yaklaşım, modelin farklı veri setlerinde tutarlı bir şekilde performans göstermesini ve test sonuçlarının güvenilir olmasını sağlar.
## Random Forest Regressor (Rastgele Orman Regresörü)
## Support Vector Regressor (Destek Vektör Regresörü - SVR)
## Decision Tree Regressor (Karar Ağaçları Regresörü)
# Modellerin Karşılaştırılması
![Ekran Görüntüsü (433)](https://github.com/user-attachments/assets/a9233b60-112f-4156-9cec-e259d57d4934)
## Öğrenme Yüzdeleri (r^2 değerleri)
  ### Linear Regression: %85.30
  ### Decision Tree Regressor: %93.26
  ### Random Forest Regressor: %95.58
  ### SVR: %91.98
Modellerin karşılaştırılması için her model için r^2, MSE ve MAE değerleri hesaplandı.Sonuç olarak en yüksek MSE değeri Linear Regression'da çıktı.Buna bağlı olarak r^2 değeri yani öğrenme yüzdesi 4 model arasında en düşük çıktı.Bu da lineer regression modelinin bu veri seti için en kötü sonuçları doğurduğu anlamına geliyor.

Bunun aksine MSE değerinin en düşük çıktığı, öğrenme yüzdesinin en yüksek çıktığı model olarak Random Forrest Regressor'ın bu veri seti için en ideal model olduğunu söyleyebiliriz.%95.58 öğrenme yüzdesi değeriyle modelin iyi öğrendiği ve gerçek değerlere oldukça yakın sonuçlar verdiği görülüyor.
# Gelecekte Yapılabilecek İyileştirmeler
Daha fazla özellik mühendisliği ile modelin performansı artırılabilir.

Derin öğrenme tabanlı regresyon modelleri denenebilir.

Mevcut model optimizasyonları (GridSearchCV, Hyperparameter Tuning) yapılabilir.
# Projenin Anlatıldığı Video
Youtube:  https://www.youtube.com/watch?v=3GgKtPzJ9l4 
