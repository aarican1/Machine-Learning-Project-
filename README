**Makine Öğrenimi ile AIDS Virüsü Enfeksiyonu Tahmini Raporu**







|<br><br>Rapor Hakkında Ön Bilgilendirme||
| :-: | :- |
|<br>Rapor adı|<br>Makine Öğrenimi ile AIDS Virüsü Enfeksiyonu Tahmini |
|<br>Rapor Sahibi Ad Soyadı|<br>Abdurrahman Arıcan|
|<br>Rapor Sahibi Okul Numarası|<br>202013171063|
|<br>` `Ders Adı|<br>Makine Öğrenimi|
|<p></p><p>Ders Hocası</p>|<br>Dr. Öğr. Üyesi Pınar Özen Kavas|



**1.Özet**

Bu projede, AIDS Virüsü Enfekte Tahmini[6] veri seti kullanılarak bir sınıflandırma problemi çözüldü. Karar ağaçları, K En Yakın Komşu, Destek Vektör Makineleri, Yapay Sinir Ağları, Rastgele Orman algoritmaları kullanılarak model eğitildi ve doğruluk oranları karşılaştırıldı. Sonuçlar Yapay Sinir Ağları modelinin daha yüksek doğruluk sağladığını gösterdi.


**2.Giriş**

Projenin odaklandığı problem, AIDS virüsü enfekte olmuş bireylerin bulunmasıdır. AIDS Virüsü Enfekte Tahmini [6] veri seti kullanılarak, bireylerin enfekte olup olmadığını doğru bir şekilde sınıflandırmayı amaçlayan bir makine öğrenimi modeli geliştirilmiştir.

AIDS virüsü enfeksiyonunun erken teşhisi, tedavi süreçlerinin iyileştirilmesi ve hastalığın diğer sağlıklı bireylere yayılmasını önlenmesi için önemli bir rol oynamaktadır. Bu alanda doğru tahmin yapan bir makine öğrenimi modeli sağlık çalışanlarının daha etkili kararlar vermesini sağlayabilir. 

İncelenen literatür, makine öğrenmesinin HIV/AIDS tedavisi ve ilaç geliştirilmesinde önemli bir araç olduğunu, ancak hala direnç ve tedaviye yanıtla ilgili zorlukların devam ettiğini ortaya koymaktadır.[1].

Literatür de makine öğreniminin HIV/AIDS alt enfeksiyon türlerinin tedavi, teşhis ve tahmini işlemlerinde kullanıldığı fark edilmiştir. [2,3] 

Kullanılan veri seti ile geliştirilen makine öğrenimi örnekleri incelenmiştir. Bu örneklerde veri setindeki veri sayısının az olduğu ve doğruluk oranını %80-%90 aralığında olduğu fark edilmiştir.[5]


Projenin amacı AIDS virüsü enfekte tahmini yapmak için sınıflandırma algoritmalarını uygulamak, modellerin doğruluk oranlarını karşılaştırmak ve en iyi performansı sağlayan algoritmayı belirlemektir. Bu projede Rastgele Orman modelinin diğer modellere kıyasla daha yüksek doğruluk sağladığı sonucuna ulaşılmıştır.

**3.Veri Seti ve Veri Ön İşleme**

Bu bölümde AIDS virüsü enfekte tahmini için kullanılan veri setinin özellikleri tanıtılmış ve veri ön işleme adımları detaylandırılmıştır.

Bu projede AIDS Virüsü Enfekte Tahmini (**AIDS Virus Infection Prediction**) veri seti kullanılmıştır. Veri seti 50000 satır ve 23 sütundan oluşmaktadır. Sütunlar şunlardır:

- time: Başarısızlığa ya da sansüre kadar geçen zaman 
- trt: Tedavi göstergesi (0 = yalnızca ZDV; 1 = ZDV + ddI, 2 = ZDV + Zal, 3 = yalnızca ddI) 
- age: Yaş
- wtkg: Ağırlık(kg)
- hemo: Hemofili (hayır  = 0, evet  = 1)
- homo:Homoseksüel (hayır  = 0, evet  = 1)
- drugs : IV ilaç kullanımı (hayır  = 0, evet  = 1)
- karnof**:** Karnofsky puanı (0-100 arası bir ölçekte)
- oprior: ZDV dışı antiretroviral tedavi 175 öncesi (0=hayır, 1=evet)
- z30: 175'ten önceki 30 günde ZDV (0=hayır, 1=evet)
- preanti: 175 antiretroviral tedavi öncesi günler
- race: Irk (0=Beyaz, 1=beyaz olmayan)
- gender: Cinsiyet (0=K, 1=E)
- str2: antiretroviral geçmişi (0=naif, 1=deneyimli)
- strat: antiretroviral geçmişi tabakalandırması (1='Antiretroviral Naif',2='> 1 ancak <= 52 hafta önceki antiretroviral tedavi',3='> 52 hafta)
- symptom: semptom: semptomatik gösterge (0=asimptot, 1=semptomlar)
- treat: tedavi göstergesi (0=sadece ZDV, 1=diğerleri)
- offtrt: 96+/-5 haftadan önce off-trt göstergesi (0=hayır, 1=evet)
- cd40: Başlangıçta CD4
- cd420: 20+/-5 haftada CD4
- cd80: Başlangıçta CD8
- cd820: 20+/-5 haftada CD8
- infected: AIDS'e yakalanmış (0=Hayır, 1=Evet)




Veri setinde sınıf dengesizliği bulunduğundan dolayı **SMOTE (Synthetic Minority Over-sampling Technique)** ile azınlık olan sınıfın verileri çoğaltılmıştır. Veri seti eğitim ve test olarak ikiye ayrılmıştır. Eğitim ve test ayrım işlemi StratifiedKFold yöntemi kullanılarak   eğitim ve test şeklinde ayrılmıştır. Parametrik olmayan özelliklere **log dönüşümü** işlemi uygulanmıştır.  Farklı ölçeklere sahip veriler **MinMaxScaler** yöntemiyle standartlaştırılmıştır. Böylece tüm özellikler aynı ölçek (minimum= 0, maximum = 1) üzerinde normalize edilmiştir.

Bu adımların sonunda, modele uygun hale getirilmiş bir veri seti elde edilmiştir. Bu veri seti, makine öğrenimi modellerinin eğitiminde ve testinde kullanılmıştır.


**4. Yöntemler** 


Bu çalışmada, çeşitli makine öğrenimi algoritmaları kullanılarak "infected" sınıfını tahmin etmek amaçlanmıştır.Bu çalışmada ilk olarak özellik elemesi yapmadan daha sonra da özellikler **Mutual Information** methodu ile elenerek kullanılmıştır. Uygulanan yöntemler, model seçim süreçleri ve performans ölçümleri aşağıda detaylandırılmıştır.

**4.1 Algoritmalar**


**Decision Tree (Karar Ağacı):**

Karar ağaçları, **sınıflandırma ve regresyon** problemleri için kullanılan, dallanma yapısına dayalı bir makine öğrenimi algoritmasıdır. Veri setindeki özellikleri (nitelikleri) kullanarak **karar kuralları** oluşturur ve bu kurallarla veri sınıflandırılır veya tahmin edilir.

**K-Nearest Neighbors (KNN-K En Yakın Komşu):**

K-En Yakın Komşu (K-Nearest Neighbors), hem **sınıflandırma** hem de **regresyon**      problemleri için kullanılabilen **denetimli öğrenme** (supervised learning) algoritmalarından biridir. Bu algoritma, bir veri noktasını sınıflandırmak veya değerini tahmin etmek için, komşuları ile olan mesafeye dayanır.

**Destek Vektör Makineleri (SVM):**


Veriyi, maksimum ayırma marjına sahip bir hiper düzlemle sınıflandırmayı hedefler. 




**Yapay Sinir Ağları (YSA):**

Yapay Sinir Ağları (YSA), insan beyninin çalışma prensiplerinden esinlenerek geliştirilmiş, veri işleme ve modelleme amacıyla kullanılan bir **makine öğrenimi** algoritmasıdır. YSA, büyük ve karmaşık veri setlerini işleyerek **sınıflandırma**, **regresyon**, **görüntü işleme**, **doğal dil işleme** gibi birçok alanda üstün performans gösterir.

**Random Forest Classifier (Rastgele Orman Sınıflandırma):**

Birden fazla karar ağacının birlikte kullanıldığı, grup (ensemble) bir yöntemdir. Özellikle aşırı öğrenmeye (overfitting) dayanıklı olmasıyla bilinir.

**4.2 Modeller**


**Karar Ağacı:** Karar Ağacı algoritması ile model oluşturulmuştur. Oluşturulan modelin eğitimi ve testi gerçekleştirilmiştir.

**KNN-K En Yakın Komşu:** K En Yakın Komşu algoritması ile model oluşturulmuştur. k değeri 3  olarak alınmıştır. Oluşturulan modelin eğitimi ve testi gerçekleştirilmiştir.

**Destek Vektör Makineleri:** Destek Vektör Makinesi algoritması ile model oluşturulmuştur. Karar sınırları doğrusal (linear) hyperplane oluşturulmuştur.  Oluşturulan modelin eğitimi ve testi gerçekleşmiştir.

**Yapay Sinir Ağları:** Yapay Sinir Ağları algoritması ile model oluşturulmuştur. Oluşturulan modelde bir adet giriş katmanı, iki adet gizli katman ve bir adette çıkış katmanı vardır. Gizli katmanlardaki nöron sayısı özellik sütunlarının yarısı miktarında oluşturulmuştur. Gizli katmanlardaki aktivasyon metodu relu olarak seçilmiştir. Relu, nöronların çıktılarında negatif değerleri sıfırlayan ve pozitif değerleri olduğu gibi bırakarak hesaplama yapan bir aktivasyon metodudur. Çıkış katmanında yalnızca bir adet nöron bulunur. Aktivasyon metodu olarak “sigmoid” kullanılmıştır. Sigmoid, ikili sınıflandırma problemleri için kullanılan yaygın bir metottur. Nöronun çıktısını 0 ve 1 değerlerine dönüştürür.

Modelin eğitimi gerçekleştirilirken devir(epochs) sayısı 100 olarak ayarlanmıştır. Modelin testi gerçekleştirilmiştir.  

**Rastgele Orman:** Rastgele Orman algoritması ile model oluşturulmuştur. Modelde 100 adet karar ağacı bulunmaktadır. Oluşturulan modelin eğitim ve testi gerçekleştirilmiştir.



**5. Sonuçlar**


Bu bölümde oluşturulan modellerin performans parametrelerine göre karşılaştırılması yapılacaktır.** 



**Karar Ağacı Modeli**


Modelin bazı performans parametreleri aşağıda gösterilmiştir.

||**Bütün Özellikler İle**|**Seçilen Özellikler İle**|
| :- | :-: | :-: |
|**Doğruluk (Accuary)**|68\.8%|68\.4%|
|**Duyarlılık (Sensitivity)**|68\.4%|67\.7%|
|**Precision**|70\.1%|70\.5%|
|**Özgüllük (Specificity)**|69\.3%|69\.2%|
|**F1 Skoru**|68\.8%|68\.4%|
|**Cohen’s Kappa Katsayısı**|0\.377|0\.368|

- Roc ve Auc:

  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.001.png)
- Roc ve Auc: (Seçilmiş Özellikler) :
  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.002.png)
- Karmaşıklık Matriksi:
  ![metin, ekran görüntüsü, dikdörtgen, yazı tipi içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.003.png)
- Karmaşıklık Matriksi(Seçilmiş Özellikler) :
  ![metin, ekran görüntüsü, dikdörtgen, yazı tipi içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.004.png)


**K En Yakın Komşu Modeli**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.**


||**Bütün Özellikler İle**|**Seçilen Özellikler İle**|
| :- | :-: | :-: |
|**Doğruluk (Accuracy)**|72%|71\.2%|
|**Duyarlılık (Sensitivity)**|69\.6%|68\.8%|
|**Precision**|78%|79\.1%|
|**Özgüllük (Specificity)**|75%|75\.5%|
|**F1 Skoru**|72\.2%|72%|
|**Cohen’s Kappa Katsayısı**|0\.44|0\.433|

- Roc ve Auc:

  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.005.png)
- Roc ve Auc(Seçilmiş Özellikler):
  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.006.png)
- Karmaşıklık Matriksi: 
  ![metin, ekran görüntüsü, dikdörtgen, diyagram içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.007.png)
- Karmaşıklık Matriksi(Seçilmiş Özellikler) :
  ` `**![](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.008.png)**



**Destek Vektör Makineleri Modeli**
**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.**    





||**Bütün Özellikler İle**|**Seçilen Özellikler İle**|
| :- | :-: | :-: |
|**Doğruluk (Accuary)**|63\.2%|63\.9%|
|**Duyarlılık (Sensitivity)**|76%|76\.1%|
|**Precision**|60\.6%|61\.1%|
|**Özgüllük (Specificity)**|50\.5%|51\.6%|
|**F1 Skoru**|67\.4%|67\.8%|
|**Cohen’s Kappa Katsayısı**|0\.265|0\.277|

- Roc ve Auc: 
  ![metin, çizgi, ekran görüntüsü, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.009.png)
- Roc ve Auc(Seçilmiş Özellikler):

![metin, çizgi, ekran görüntüsü, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.010.png)

- Karmaşıklık Matriksi: ![metin, ekran görüntüsü, diyagram, dikdörtgen içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.011.png)

- Karmaşıklık Matriksi(Seçilmiş Özellikler) :

  ![metin, ekran görüntüsü, diyagram, dikdörtgen içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.012.png)


**Yapay Sinir Ağları Modeli**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.**    


||**Bütün Özellikler İle**|**Seçilen Özellikler İle**|
| :- | :-: | :-: |
|**Doğruluk (Accuary)**|66\.9%|67\.1%|
|**Duyarlılık (Sensitivity)**|74\.7%|73\.1%|
|**Precision**|64\.6%|65\.3%|
|**Özgüllük (Specificity)**|59\.1%|61\.1%|
|**F1 Skoru**|66%|66\.5%|
|**Cohen’s Kappa Katsayısı**|0\.338|0\.342|




- Roc ve Auc: 

  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.013.png)
- Roc ve Auc(Seçilmiş Özellikler):

  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.014.png)

- Karmaşıklık Matriksi:
  ![metin, ekran görüntüsü, dikdörtgen, yazı tipi içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.015.png)

- Karmaşıklık Matriksi(Seçilmiş Özellikler) :
  ![metin, ekran görüntüsü, dikdörtgen, yazı tipi içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.016.png)

**Rastgele Orman Modeli**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.**    


||**Bütün Özellikler İle**|**Seçilen Özellikler İle**|
| :- | :-: | :-: |
|**Doğruluk (Accuary)**|78\.3%|76\.8%|
|**Duyarlılık (Sensitivity)**|80\.9%|78%|
|**Precision**|74%|74\.8%|
|**Özgüllük (Specificity)**|76%|75\.8%|
|**F1 Skoru**|78\.4%|76\.8%|
|**Cohen’s Kappa Katsayısı**|0\.566|0\.536|





- Roc ve Auc:


  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.017.png)

- Roc ve Auc(Seçilmiş Özellikler):

  ![metin, ekran görüntüsü, çizgi, öykü gelişim çizgisi; kumpas; grafiğini çıkarma içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.018.png)

- Karmaşıklık Matriksi:

  ![metin, ekran görüntüsü, dikdörtgen, diyagram içeren bir resim

Açıklama otomatik olarak oluşturuldu](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.019.png)

Karmaşıklık Matriksi(Seçilmiş Özellikler) : 

![](Aspose.Words.e1e8a063-e3bd-4728-8f6a-3804f90446e4.020.png)


**6. Değerlendirme**
--------------------------------------------------------------
Bu bölümde, geliştirilen modellerin performansları, tüm özellikler ve seçilmiş özelliklerle karşılaştırılmış ve değerlendirilmiştir.

**Karar Ağacı Modeli**

Karar Ağacı modelinin tüm özelliklerle doğruluk oranı %68.8 iken, seçilmiş özelliklerle %68.4'e gerilemiştir. Duyarlılık oranı %68.4'ten %67.7'ye düşmüştür. Precision değeri ise %70.1'den %70.5'e yükselmiştir. Özgüllük oranı %69.3'ten %69.2'ye ve F1 skoru %68.8'den %68.4'e düşmüştür. Cohen's Kappa katsayısı da 0.377'den 0.368'e gerilemiştir. Bu sonuçlar, seçilmiş özelliklerin modeli iyileştirmediğini göstermektedir.

**K En Yakın Komşu Modeli (KNN)**

KNN modelinin tüm özelliklerle doğruluk oranı %72, seçilmiş özelliklerle %71.2 olarak hesaplanmıştır. Duyarlılık oranı %69.6'dan %68.8'e düşerken, Precision %78'den %79.1'e yükselmiştir. Özgüllük oranı %75'ten %75.5'e, F1 skoru ise %72.2'den %72'ye düşmüştür. Cohen's Kappa katsayısı %0.44'ten %0.433'e gerilemiştir. Seçilmiş özellikler modelin doğruluk oranında küçük bir düşüşe yol açmıştır.

**Destek Vektör Makineleri Modeli (SVM)**

SVM modelinin tüm özelliklerle doğruluk oranı %63.2 iken, seçilmiş özelliklerle %63.9'a yükselmiştir. Duyarlılık oranı %76'dan %76.1'e, Precision ise %60.6'dan %61.1'e yükselmiştir. Özgüllük oranı %50.5'ten %51.6'ya, F1 skoru %67.4'ten %67.8'e yükselmiştir. Cohen's Kappa katsayısı ise %0.265'ten %0.277'ye çıkmıştır. Bu modelde seçilmiş özellikler küçük bir performans artışı sağlamıştır.

**Yapay Sinir Ağları Modeli (YSA)**

Yapay Sinir Ağları modelinin tüm özelliklerle doğruluk oranı %66.9 iken, seçilmiş özelliklerle %67.1'e yükselmiştir. Duyarlılık oranı %74.7'den %73.1'e, Precision ise %64.6'dan %65.3'e değişmiştir. Özgüllük oranı %59.1'den %61.1'e yükselmiş, F1 skoru ise %66'dan %66.5'e yükselmiştir. Cohen's Kappa katsayısı %0.338'den %0.342'ye yükselmiştir. Seçilmiş özelliklerle model performansında genel olarak bir artış görülmüştür.

**Rastgele Orman Modeli**

Rastgele Orman modelinin tüm özelliklerle doğruluk oranı %78.3 iken, seçilmiş özelliklerle %76.8'e düşmüştür. Duyarlılık oranı %80.9'dan %78'e, Precision %74'ten %74.8'e yükselmiştir. Özgüllük oranı %76'dan %75.8'e ve F1 skoru %78.4'ten %76.8'e gerilemiştir. Cohen's Kappa katsayısı ise %0.566'dan %0.536'ya düşmüştür. Bu modelde seçilmiş özelliklerin kullanımı performansı hafifçe azaltmıştır.

-----
**Genel Değerlendirme**

1. **En Yüksek Performans**: Rastgele Orman modeli, tüm özelliklerle en iyi doğruluk (%78.3), duyarlılık (%80.9) ve F1 skoru (%78.4) değerlerini elde etmiştir.
1. **Seçilmiş Özelliklerle Performans**: Modellerin büyük çoğunluğunda seçilmiş özellikler kullanıldığında performans düşüşü gözlenmiştir. Bu durum, veri setinin yapısına ve özellik seçiminin modelle uyumuna bağlı olabilir.
1. **SVM ve YSA Modelleri**: SVM ve YSA modelleri, seçilmiş özelliklerle küçük ama olumlu bir performans artışı sağlamıştır.

Sonuç olarak, tüm özelliklerle Rastgele Orman modeli en başarılı performansı göstermiştir. Ancak seçilmiş özellikler kullanılarak daha hafif modeller elde edilmek isteniyorsa SVM ve YSA modelleri tercih edilebilir.




**Kaynakça**



1 - Machine learning approaches to study HIV/AIDS infection: A Review, Sweta Kumari, Usha Chouhan and Sunil Kumar Suryawanshi ,2017

[https://www.researchgate.net/profile/Sherif-Sharawy/publication/315810299_Evaluation_of_antimicrobial_and_synergistic_effects_of_selected_medicinal_plants_of_Hail_area_with_antibiotics/links/58e780ec4585152528df1c26/Evaluation-of-antimicrobial-and-synergi](https://www.researchgate.net/profile/Sherif-Sharawy/publication/315810299_Evaluation_of_antimicrobial_and_synergistic_effects_of_selected_medicinal_plants_of_Hail_area_with_antibiotics/links/58e780ec4585152528df1c26/Evaluation-of-antimicrobial-and-synergistic-effects-of-selected-medicinal-plants-of-Hail-area-with-antibiotics.pdf#page=44)

2 - Machine learning-based prognostic prediction for hospitalized HIV/AIDS patients with *cryptococcus* infection in Guangxi, China, [**https://link.springer.com/article/10.1186/s12879-024-10013-y**](https://link.springer.com/article/10.1186/s12879-024-10013-y)

**3 -** Construction of Machine Learning Models to Predict Changes in Immune Function Using Clinical Monitoring Indices in HIV/AIDS Patients After 9.9-Years of Antiretroviral Therapy in Yunnan, China<a name="h1"></a>, Bingxiang Li,Mingyu Li,Yu Song ,Xiaoning Lu

[**https://www.frontiersin.org/journals/cellular-and-infection-microbiology/articles/10.3389/fcimb.2022.867737/full**](https://www.frontiersin.org/journals/cellular-and-infection-microbiology/articles/10.3389/fcimb.2022.867737/full)

**4-**  The predictive accuracy of machine learning for the risk of death in HIV patients: a systematic review and meta-analysis, Yuefei Li, Ying Feng, Qian He, Zhen Ni, Xiaoyuan Hu, Xinhuan Feng & Mingjian Ni
[**https://link.springer.com/article/10.1186/s12879-024-09368-z](https://link.springer.com/article/10.1186/s12879-024-09368-z)

**5 -AIDS Classification EDA, Aadarsh velu ,Kaggle
[https://www.kaggle.com/code/aadarshvelu/aids-classification-eda-acc-91**](https://www.kaggle.com/code/aadarshvelu/aids-classification-eda-acc-91)**

**6 -AIDS Virus Infection Prediction
[https://www.kaggle.com/datasets/aadarshvelu/aids-virus-infection-prediction/data**](https://www.kaggle.com/datasets/aadarshvelu/aids-virus-infection-prediction/data)**

**




