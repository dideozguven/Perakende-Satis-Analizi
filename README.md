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
## seaborn
Seaborn, Python'da veri görselleştirme için kullanılan, estetik açıdan zengin ve istatistiksel grafikleri kolayca oluşturmayı sağlayan bir kütüphanedir. Matplotlib üzerine inşa edilmiştir ve özellikle veri analizi sırasında dağılım grafikleri ve kategorik görselleştirmeler gibi işlemler için idealdir.
## matplotlib 
Verilerin görselleştirilmesi için kullanılır, model performansını görsel olarak sunmak ve analiz sonuçlarını grafiklerle göstermek için idealdir.

# Kullanılan Modeller
## Linear Regression (Doğrusal Regresyon)
"Transaction ID", "Customer ID" ve "Transaction Date" gibi tahmin modeli için gereksiz veya doğrudan etkisi olmayan değişkenler kaldırılarak özellikler (X) oluşturulmuştur. Ayrıca, "Total Spent" bağımlı değişken olarak seçilmiştir çünkü modelin bu değeri tahmin etmesi hedeflenmektedir.

Ardından, train_test_split fonksiyonu kullanılarak veri seti %80 eğitim (%20 test) olacak şekilde ayrılmıştır. "random_state=42" parametresi kullanılarak bölme işlemi tekrarlanabilir hale getirilmiş, böylece her çalıştırmada aynı veri seti ayrımı sağlanmıştır. Bu yaklaşım, modelin farklı veri setlerinde tutarlı bir şekilde performans göstermesini ve test sonuçlarının güvenilir olmasını sağlar.

**Lineer regresyon modeline göre doğruluk yüzdesi ve hata oranları şu şekilde çıktı:**

Mean Squared Error (MSE): 1286.87716172463

Mean Absolute Error (MAE): 26.131206218864744

R-squared (R²): 0.8530210209053578

R-squared (Percentage): 85.30%
![Ekran Görüntüsü (436)](https://github.com/user-attachments/assets/6c3156d1-7c66-4037-94d3-039a45887e6a)

 Bu grafik, gerçek değerler ile tahmin edilen değerler arasındaki ilişkiyi gösteren bir scatter plot (dağılım grafiği) olup, lineer regresyon modelinin performansını değerlendirmeye yardımcı olur.

Grafikte mavi noktalar, modelin tahminlerini gerçek değerlerle karşılaştırmaktadır. Kırmızı kesikli çizgi (y = x doğrusu) ise mükemmel tahmin çizgisini temsil eder. Eğer model mükemmel tahminler yapsaydı, tüm noktalar bu çizgi üzerine otururdu.

Genel olarak, noktaların kırmızı çizgi etrafında yoğunlaştığı gözlemlenmektedir, bu da modelin büyük ölçüde doğru tahminler yaptığını göstermektedir. Ancak, bazı noktalar çizgiden uzaklaşarak sapma (error) göstermektedir. Bu sapmalar, modelin bazı örneklerde hata yaptığını ve doğruluğun iyileştirilmesi için ek özellik mühendisliği, hiperparametre optimizasyonu veya farklı modelleme tekniklerinin değerlendirilebileceğini gösterir.

Genel olarak, modelin tahminleri ile gerçek değerler arasındaki korelasyonun güçlü olduğu, ancak modelin mükemmel olmadığı ve bazı iyileştirmelere ihtiyaç duyabileceği söylenebilir.


## Random Forest Regressor (Rastgele Orman Regresörü)
Random Forest modeli oldukça başarılı bir performans göstermektedir.

%95.59 R², modelin değişkenler ile hedef değişken arasındaki ilişkileri iyi öğrendiğini gösterir.

MAE'nin düşük olması, modelin genel olarak hassas tahminler yaptığını ortaya koymaktadır.

**Random Forest Regressor modeline göre sonuçlar:**

Mean Squared Error (MSE): 386.25348128055305

Mean Absolute Error (MAE): 3.5468970661448544

R-squared (R²): 0.9558845676658957

R-squared (Percentage): 95.59%

![Ekran Görüntüsü (438)](https://github.com/user-attachments/assets/04de5052-79ba-4f99-8589-052153c2dc6b)

Bu grafikte, özellikle yüksek değerler için tahmin edilen değerler ve gerçek değerler kırmızı çizgiye oldukça yakın durmaktadır.
Bu durum, Random Forest modelinin oldukça başarılı tahminler yaptığını gösterir.

Lineer Regresyon modeline kıyasla, burada noktaların kırmızı çizgiye daha iyi hizalandığı gözlemlenmektedir.
Bu, Random Forest modelinin daha esnek ve karmaşık yapısından kaynaklanıyor olabilir. Özellikle non-lineer ilişkileri daha iyi yakalayarak daha doğru tahminler yapıyor.

## Support Vector Regressor (Destek Vektör Regresörü - SVR)
SVR modeli genellikle küçük veri setlerinde ve karmaşık ilişkileri öğrenmede başarılıdır.
Ancak, bu model Random Forest modeline kıyasla daha yüksek hata oranlarına sahiptir.
Özellikle MSE ve MAE değerlerinin yüksek olması, modelin hatalarının daha büyük olduğunu gösteriyor.

SVR modeli genellikle büyük ölçekli değişimlere karşı duyarlıdır ve bu nedenle bazı uç değerleri yanlış tahmin edebilir.

Sonuç olarak, bu model bazı durumlarda faydalı olabilir, ancak mevcut veride Random Forest daha iyi performans göstermektedir.

**SVR modeline göre sonuçlar:**

Mean Squared Error (MSE): 702.0847536982345

Mean Absolute Error (MAE): 13.521735351383759

R-squared (R²): 0.9198123151100251

R-squared (Percentage): 91.98%

![Ekran Görüntüsü (440)](https://github.com/user-attachments/assets/37003898-f0f4-4040-aa9f-7b53d0a562f6)

## Decision Tree Regressor (Karar Ağaçları Regresörü)
Modelin başarısını ölçmek için Mean Squared Error (MSE), Mean Absolute Error (MAE) ve R-squared (R²) metrikleri kullanıldı.

Random Forest modeli ile kıyaslandığında (MSE: 386.25), Decision Tree modeli daha yüksek bir hata oranına sahiptir.
SVR modeline göre (MSE: 702.08) ise daha iyi bir performans göstermektedir.

Decision Tree modeli veriyi çok iyi öğrenir, ancak aşırı öğrenmeye (overfitting) yatkındır.
Tek başına kullanıldığında model, gürültüyü öğrenebilir ve genelleme yeteneği düşebilir.

Hata oranları makul seviyede olsa da, Random Forest modeli daha iyi performans göstermektedir.
Random Forest, Decision Tree modeline göre daha düşük hata oranı ile daha yüksek bir R² değerine sahiptir.
SVR modeline kıyasla Decision Tree daha iyi sonuçlar vermektedir.
Decision Tree modeli genellikle Random Forest modeline göre daha düşük genelleme yeteneğine sahiptir.

**Decision Tree Regressor modeline göre sonuçlar:**

Mean Squared Error (MSE): 590.354796222664

Mean Absolute Error (MAE): 4.270079522862832

R-squared (R²): 0.9325734049579785

R-squared (Percentage): 93.26%

![Ekran Görüntüsü (442)](https://github.com/user-attachments/assets/e469cc4d-dbf6-46a3-a35a-b679d6fc984c)

# Modellerin Karşılaştırılması
![Ekran Görüntüsü (433)](https://github.com/user-attachments/assets/a9233b60-112f-4156-9cec-e259d57d4934)
  ### Linear Regression: %85.30
  ### Decision Tree Regressor: %93.26
  ### Random Forest Regressor: %95.58
  ### Destek Vektör Regresyonu (SVR): %91.98
Modellerin karşılaştırılması için her model için r^2, MSE ve MAE değerleri hesaplandı.Sonuç olarak en yüksek MSE değeri Linear Regression'da çıktı.Buna bağlı olarak r^2 değeri yani öğrenme yüzdesi 4 model arasında en düşük çıktı.Bu da lineer regression modelinin bu veri seti için en kötü sonuçları doğurduğu anlamına geliyor.

Bunun aksine MSE değerinin en düşük çıktığı, öğrenme yüzdesinin en yüksek çıktığı model olarak Random Forrest Regressor'ın bu veri seti için en ideal model olduğunu söyleyebiliriz.%95.58 öğrenme yüzdesi değeriyle modelin iyi öğrendiği ve gerçek değerlere oldukça yakın sonuçlar verdiği görülüyor.

### Performans Analizi İçin Radar Chart
![indir (1)](https://github.com/user-attachments/assets/7c325b6c-a679-4ca8-b610-1772fa18c314)
Her modelin performansı kapalı bir poligon ile temsil edilmiştir. Merkeze daha yakın ve daha küçük poligonlar, daha iyi performansı ifade eder.

MSE ve MAE eksenlerinde büyük bir yayılım, daha yüksek hata oranlarını gösterir ve bu istenmeyen bir durumdur.

R² ekseninde daha geniş alan kaplayan modeller, veri açıklama gücü açısından daha başarılıdır.

Linear Regression (Doğrusal Regresyon):
Eğer bu model, MSE ve MAE eksenlerinde daha dışarıya uzanıyorsa, diğer modellere kıyasla daha yüksek hata oranına sahiptir.

Decision Tree Regressor (Karar Ağacı Regresyonu):
Bu model, genellikle R² ve hata metrikleri arasında dengeli bir performans sergiler. Ancak veri dağılımına göre sapmalar gösterebilir.

Random Forest Regressor (Rastgele Orman Regresyonu):
Genellikle tüm metriklerde daha başarılıdır. Daha küçük MSE ve MAE değerleri ile daha yüksek R²'ye sahiptir.

SVR (Destek Vektör Regresyonu):
Ayarlamalarına bağlı olarak bazı metriklerde iyi performans gösterirken diğerlerinde zayıf kalabilir.

# Gelecekte Yapılabilecek İyileştirmeler
Daha fazla özellik mühendisliği ile modelin performansı artırılabilir.

Derin öğrenme tabanlı regresyon modelleri denenebilir.

Mevcut model optimizasyonları (GridSearchCV, Hyperparameter Tuning) yapılabilir.
# Projenin Anlatıldığı Video
Youtube:  https://www.youtube.com/watch?v=pI79Wr6GJI0
