# Machine-Learning-Project-
**Makine Öğrenimi ile AIDS Virüsü Enfeksiyonu Tahmini Raporu**

<br/><br/><br/>




**1.Özet**

Bu projede, AIDS Virüsü Enfekte Tahmini\[6\] veri seti kullanılarak bir sınıflandırma problemi çözüldü. Karar ağaçları, K En Yakın Komşu, Destek Vektör Makineleri, Yapay Sinir Ağları, Rastgele Orman algoritmaları kullanılarak model eğitildi ve doğruluk oranları karşılaştırıldı. Sonuçlar Yapay Sinir Ağları modelinin daha yüksek doğruluk sağladığını gösterdi.

**2.Giriş**

Projenin odaklandığı problem, AIDS virüsü enfekte olmuş bireylerin bulunmasıdır. AIDS Virüsü Enfekte Tahmini \[6\] veri seti kullanılarak, bireylerin enfekte olup olmadığını doğru bir şekilde sınıflandırmayı amaçlayan bir makine öğrenimi modeli geliştirilmiştir.  
<br/>AIDS virüsü enfeksiyonunun erken teşhisi, tedavi süreçlerinin iyileştirilmesi ve hastalığın diğer sağlıklı bireylere yayılmasını önlenmesi için önemli bir rol oynamaktadır. Bu alanda doğru tahmin yapan bir makine öğrenimi modeli sağlık çalışanlarının daha etkili kararlar vermesini sağlayabilir.

İncelenen literatür, makine öğrenmesinin HIV/AIDS tedavisi ve ilaç geliştirilmesinde önemli bir araç olduğunu, ancak hala direnç ve tedaviye yanıtla ilgili zorlukların devam ettiğini ortaya koymaktadır.\[1\].

Literatür de makine öğreniminin HIV/AIDS alt enfeksiyon türlerinin tedavi, teşhis ve tahmini işlemlerinde kullanıldığı fark edilmiştir. \[2,3\]

Kullanılan veri seti ile geliştirilen makine öğrenimi örnekleri incelenmiştir. Bu örneklerde veri setindeki veri sayısının az olduğu ve doğruluk oranını %80-%90 aralığında olduğu fark edilmiştir.\[5\]

Projenin amacı AIDS virüsü enfekte tahmini yapmak için sınıflandırma algoritmalarını uygulamak, modellerin doğruluk oranlarını karşılaştırmak ve en iyi performansı sağlayan algoritmayı belirlemektir. Bu projede Rastgele Orman modelinin diğer modellere kıyasla daha yüksek doğruluk sağladığı sonucuna ulaşılmıştır.  
<br/>

**3.Veri Seti ve Veri Ön İşleme  
<br/>**Bu bölümde AIDS virüsü enfekte tahmini için kullanılan veri setinin özellikleri tanıtılmış ve veri ön işleme adımları detaylandırılmıştır.  
<br/>Bu projede AIDS Virüsü Enfekte Tahmini (**AIDS Virus Infection Prediction**) veri seti kullanılmıştır. Veri seti 50000 satır ve 23 sütundan oluşmaktadır. Sütunlar şunlardır:

- time: Başarısızlığa ya da sansüre kadar geçen zaman
- trt: Tedavi göstergesi (0 = yalnızca ZDV; 1 = ZDV + ddI, 2 = ZDV + Zal, 3 = yalnızca ddI)
- age: Yaş
- wtkg: Ağırlık(kg)
- hemo: Hemofili (hayır = 0, evet = 1)
- homo:Homoseksüel (hayır = 0, evet = 1)
- drugs : IV ilaç kullanımı (hayır = 0, evet = 1)
- karnof**:** Karnofsky puanı (0-100 arası bir ölçekte)
- oprior: ZDV dışı antiretroviral tedavi 175 öncesi (0=hayır, 1=evet)
- z30: 175'ten önceki 30 günde ZDV (0=hayır, 1=evet)
- preanti: 175 antiretroviral tedavi öncesi günler
- race: Irk (0=Beyaz, 1=beyaz olmayan)
- gender: Cinsiyet (0=K, 1=E)
- str2: antiretroviral geçmişi (0=naif, 1=deneyimli)
- strat: antiretroviral geçmişi tabakalandırması (1='Antiretroviral Naif',2='> 1 ancak &lt;= 52 hafta önceki antiretroviral tedavi',3='&gt; 52 hafta)
- symptom: semptom: semptomatik gösterge (0=asimptot, 1=semptomlar)
- treat: tedavi göstergesi (0=sadece ZDV, 1=diğerleri)
- offtrt: 96+/-5 haftadan önce off-trt göstergesi (0=hayır, 1=evet)
- cd40: Başlangıçta CD4
- cd420: 20+/-5 haftada CD4
- cd80: Başlangıçta CD8
- cd820: 20+/-5 haftada CD8
- infected: AIDS'e yakalanmış (0=Hayır, 1=Evet)

Veri seti eğitim ve test olarak ikiye ayrılmıştır. Eğitim ve test oranı eğitim %85, test %15 olacak şekilde ayrılmıştır. Farklı ölçeklere sahip veriler **StandartScaler** yöntemiyle standartlaştırılmıştır. Böylece tüm özellikler aynı ölçek (ortalama = 0, standart sapma = 1) üzerinde normalize edilmiştir.

Bu adımların sonunda, modele uygun hale getirilmiş bir veri seti elde edilmiştir. Bu veri seti, makine öğrenimi modellerinin eğitiminde ve testinde kullanılmıştır.

**4\. Yöntemler  
**

Bu çalışmada, çeşitli makine öğrenimi algoritmaları kullanılarak "infected" sınıfını tahmin etmek amaçlanmıştır. Uygulanan yöntemler, model seçim süreçleri ve performans ölçümleri aşağıda detaylandırılmıştır.  

**4.1 Algoritmalar  
**

**Decision Tree (Karar Ağacı):**

Karar ağaçları, **sınıflandırma ve regresyon** problemleri için kullanılan, dallanma yapısına dayalı bir makine öğrenimi algoritmasıdır. Veri setindeki özellikleri (nitelikleri) kullanarak **karar kuralları** oluşturur ve bu kurallarla veri sınıflandırılır veya tahmin edilir.  

**K-Nearest Neighbors (KNN-K En Yakın Komşu):**

K-En Yakın Komşu (K-Nearest Neighbors), hem **sınıflandırma** hem de **regresyon** problemleri için kullanılabilen **denetimli öğrenme** (supervised learning) algoritmalarından biridir. Bu algoritma, bir veri noktasını sınıflandırmak veya değerini tahmin etmek için, komşuları ile olan mesafeye dayanır.

**Destek Vektör Makineleri (SVM):  
**

Veriyi, maksimum ayırma marjına sahip bir hiper düzlemle sınıflandırmayı hedefler.

**Yapay Sinir Ağları (YSA):**

Yapay Sinir Ağları (YSA), insan beyninin çalışma prensiplerinden esinlenerek geliştirilmiş, veri işleme ve modelleme amacıyla kullanılan bir **makine öğrenimi** algoritmasıdır. YSA, büyük ve karmaşık veri setlerini işleyerek **sınıflandırma**, **regresyon**, **görüntü işleme**, **doğal dil işleme** gibi birçok alanda üstün performans gösterir.  

**Random Forest Classifier (Rastgele Orman Sınıflandırma):**

Birden fazla karar ağacının birlikte kullanıldığı, grup (ensemble) bir yöntemdir. Özellikle aşırı öğrenmeye (overfitting) dayanıklı olmasıyla bilinir.  

**4.2 Modeller  
**

**Karar Ağacı:** Karar Ağacı algoritması ile model oluşturulmuştur. Oluşturulan modelin eğitimi ve testi gerçekleştirilmiştir.  

**KNN-K En Yakın Komşu:** K En Yakın Komşu algoritması ile model oluşturulmuştur. k değeri 3 olarak alınmıştır. Oluşturulan modelin eğitimi ve testi gerçekleştirilmiştir.

**Destek Vektör Makineleri:** Destek Vektör Makinesi algoritması ile model oluşturulmuştur. Karar sınırları doğrusal (linear) hyperplane oluşturulmuştur. Oluşturulan modelin eğitimi ve testi gerçekleşmiştir.

**Yapay Sinir Ağları:** Yapay Sinir Ağları algoritması ile model oluşturulmuştur. Oluşturulan modelde bir adet giriş katmanı, iki adet gizli katman ve bir adette çıkış katmanı vardır. Gizli katmanlardaki nöron sayısı özellik sütunlarının yarısı miktarında oluşturulmuştur. Gizli katmanlardaki aktivasyon metodu relu olarak seçilmiştir. Relu, nöronların çıktılarında negatif değerleri sıfırlayan ve pozitif değerleri olduğu gibi bırakarak hesaplama yapan bir aktivasyon metodudur. Çıkış katmanında yalnızca bir adet nöron bulunur. Aktivasyon metodu olarak “sigmoid” kullanılmıştır. Sigmoid, ikili sınıflandırma problemleri için kullanılan yaygın bir metottur. Nöronun çıktısını 0 ve 1 değerlerine dönüştürür.

Modelin eğitimi gerçekleştirilirken devir(epochs) sayısı 100 olarak ayarlanmıştır. Modelin testi gerçekleştirilmiştir.  

**Rastgele Orman:** Rastgele Orman algoritması ile model oluşturulmuştur. Modelde 100 adet karar ağacı bulunmaktadır. Oluşturulan modelin eğitim ve testi gerçekleştirilmiştir.

**5\. Sonuçlar  
**

Bu bölümde oluşturulan modellerin performans parametrelerine göre karşılaştırılması yapılacaktır.**  
<br/>**

**Karar Ağacı Modeli**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.  

- Doğruluk (Accuary): %61.1
- Duyarlılık (Sensitivity): %37.9
- Özgüllük (Specificity): %72.4
- F1 Skoru: %49.8
- Karmaşıklık Matriksi:
![dt_C_M](https://github.com/user-attachments/assets/b1c16228-5b6c-4e1d-9df4-b8c315c7b316)

    
    <br/>

**  
K En Yakın Komşu Modeli  
<br/>**Modelin bazı performans parametreleri aşağıda gösterilmiştir.

- Doğruluk (Accuary): %65.5
- Duyarlılık (Sensitivity): %42.8
- Özgüllük (Specificity): %72.9
- F1 Skoru: %54
- Karmaşıklık Matriksi: ![KNN_C_M](https://github.com/user-attachments/assets/7ba7c866-01b4-4ee8-a4df-e0b345fa02d1)

**Destek Vektör Makineleri Modeli**


Modelin bazı performans parametreleri aşağıda gösterilmiştir.

- Doğruluk (Accuary): %69
- Duyarlılık (Sensitivity): %0

- Özgüllük (Specificity): %69
- F1 Skoru: %0
- Karmaşıklık Matriksi: ![SVM_C_M](https://github.com/user-attachments/assets/f2e1afda-08e9-4850-99a1-b873c71c89dc)
**Yapay Sinir Ağları Modeli  
<br/>**Modelin bazı performans parametreleri aşağıda gösterilmiştir.

- Doğruluk (Accuary): %70.5
- Duyarlılık (Sensitivity): %55.3
- Özgüllük (Specificity): %72.8
- F1 Skoru: %62.8
- Karmaşıklık Matriksi:![YSA_C_M](https://github.com/user-attachments/assets/c5f8aeea-726f-4bf5-aeb3-15bda0e5e897)

**Rastgele Orman Modeli**

Modelin bazı performans parametreleri aşağıda gösterilmiştir.

- Doğruluk (Accuary): %70.8
- Duyarlılık (Sensitivity): %57
- Özgüllük (Specificity): %72.8
- F1 Skoru: %63.9
- Karmaşıklık Matriksi:![RF_C_M](https://github.com/user-attachments/assets/165cf3b3-071a-44ca-9a2b-8ca508184645)


**  
<br/><br/>6.Değerlendirme**

Bu bölümde, geliştirilen modellerin performansları değerlendirilmiş ve karşılaştırılmıştır.  

**Karar Ağacı Modeli  
**  
Karar Ağacı modelinin doğruluk oranı %61.1 ile diğer modellere kıyasla daha düşük bir seviyededir. Duyarlılık oranı %37.9 ile oldukça zayıf olup, modelin pozitif sınıfları tespit etmede zorluk yaşadığını göstermektedir. Bununla birlikte, özgüllük oranı %72.4 ile daha yüksek bir değer elde edilmiştir. F1 skoru ise %49.8 ile orta seviyelerde kalmaktadır.  

**K En Yakın Komşu Modeli (KNN)**  
KNN modeli, doğruluk açısından %65.5 ile Karar Ağacı modeline kıyasla daha yüksek bir performans sergilemektedir. Duyarlılık oranı %42.8 ile biraz daha iyileşmiş olup, modelin pozitif sınıfları tespit etme başarısının arttığını göstermektedir. F1 skoru ise %54 ile daha iyi bir değere ulaşmıştır.  

**Destek Vektör Makineleri Modeli (SVM)**  
SVM modelinin doğruluk oranı %69 ile makul bir seviyededir. Ancak duyarlılık oranı sıfır (%0) olup, model pozitif sınıfları hiç doğru tahmin edememektedir. Bu durum, muhtemelen sınıf dengesizliği veya modelin yanlış parametrizasyonu nedeniyle düşük duyarlılık değerine yol açmaktadır. Özgüllük oranı ise %69 ile geçerli bir seviyede olmasına karşın, duyarlılıktaki sıfır değeri önemli bir sorun teşkil etmektedir.  

**Yapay Sinir Ağları Modeli (YSA)**  
Yapay Sinir Ağları modeli, doğruluk oranında %70.5 ile en yüksek performansı elde etmektedir. Duyarlılık oranı da %55.3 ile oldukça iyi seviyededir, bu da modelin pozitif sınıfları doğru şekilde tespit edebildiğini göstermektedir.  

**Rastgele Orman Modeli (Random Forest)**  
Rastgele Orman modeli, doğruluk oranında %70.8 ile YSA modelinden biraz daha yüksek bir performans sergilemektedir. Duyarlılık oranı %57 ile oldukça iyi olup, pozitif sınıfları tespit etme konusunda YSA modeline kıyasla biraz daha başarılıdır. F1 skoru ise %63.9 ile oldukça yüksek bir değere ulaşmıştır. Bu model, genel olarak en iyi performans gösteren model olarak öne çıkmaktadır.  

**Sonuçların Değerlendirilmesi:  
**

- **En Yüksek Performans**: **Rastgele Orman Modeli**, doğruluk, duyarlılık ve F1 skoru açısından diğer modellere göre üstün bir performans sergilemiştir.
- **İkinci En İyi Performans**: **Yapay Sinir Ağları (YSA)** modeli, doğruluk ve duyarlılık açısından çok yakın bir performans gösterirken, elde ettiği sonuçlar oldukça başarılıdır.
- **En Düşük Performans**: **Destek Vektör Makineleri (SVM)** modelinin duyarlılığının sıfır olması, bu modelin diğerlerinden daha düşük performans göstermesine neden olmuştur.  

Bu değerlendirmeler doğrultusunda, **Rastgele Orman** modelinin genel olarak en başarılı model olduğu, **Yapay Sinir Ağları (YSA)** modelinin ise ikinci en iyi performansı elde ettiği söylenebilmektedir.  

**Kaynakça**

1 - Machine learning approaches to study HIV/AIDS infection: A Review, Sweta Kumari, Usha Chouhan and Sunil Kumar Suryawanshi ,2017

[https://www.researchgate.net/profile/Sherif-Sharawy/publication/315810299_Evaluation_of_antimicrobial_and_synergistic_effects_of_selected_medicinal_plants_of_Hail_area_with_antibiotics/links/58e780ec4585152528df1c26/Evaluation-of-antimicrobial-and-synergi](https://www.researchgate.net/profile/Sherif-Sharawy/publication/315810299_Evaluation_of_antimicrobial_and_synergistic_effects_of_selected_medicinal_plants_of_Hail_area_with_antibiotics/links/58e780ec4585152528df1c26/Evaluation-of-antimicrobial-and-synergistic-effects-of-selected-medicinal-plants-of-Hail-area-with-antibiotics.pdf#page=44)  
<br/>2 - Machine learning-based prognostic prediction for hospitalized HIV/AIDS patients with _cryptococcus_ infection in Guangxi, China, [**https://link.springer.com/article/10.1186/s12879-024-10013-y**](https://link.springer.com/article/10.1186/s12879-024-10013-y)

**3 -** Construction of Machine Learning Models to Predict Changes in Immune Function Using Clinical Monitoring Indices in HIV/AIDS Patients After 9.9-Years of Antiretroviral Therapy in Yunnan, China, Bingxiang Li,Mingyu Li,Yu Song ,Xiaoning Lu

[**https://www.frontiersin.org/journals/cellular-and-infection-microbiology/articles/10.3389/fcimb.2022.867737/full**](https://www.frontiersin.org/journals/cellular-and-infection-microbiology/articles/10.3389/fcimb.2022.867737/full)

**4-** The predictive accuracy of machine learning for the risk of death in HIV patients: a systematic review and meta-analysis, Yuefei Li, Ying Feng, Qian He, Zhen Ni, Xiaoyuan Hu, Xinhuan Feng & Mingjian Ni  
[**https://link.springer.com/article/10.1186/s12879-024-09368-z**](https://link.springer.com/article/10.1186/s12879-024-09368-z)**  
<br/>5 -AIDS Classification EDA, Aadarsh velu ,Kaggle  
**[**https://www.kaggle.com/code/aadarshvelu/aids-classification-eda-acc-91**](https://www.kaggle.com/code/aadarshvelu/aids-classification-eda-acc-91)

**6 -AIDS Virus Infection Prediction  
**[**https://www.kaggle.com/datasets/aadarshvelu/aids-virus-infection-prediction/data**](https://www.kaggle.com/datasets/aadarshvelu/aids-virus-infection-prediction/data)
