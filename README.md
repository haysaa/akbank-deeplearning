# akbank-deeplearning
Merhabalar bu repository akbank deep learning projesi için hazırlanmıştır.Project1 projenin ilk halidir.Project 2 son halidir.Modelimi düzenlerken verileri kaybetmemek adına tedbir olması amacıyla yüklenmiştir.

# Giriş
Bu proje, derin öğrenme tabanlı bir görüntü sınıflandırma sistemi geliştirmeyi amaçlamaktadır. Kullanılan veri seti farklı araba markalarına ait görsellerden oluşmaktadır. Projede Convolutional Neural Network (CNN) mimarisi temel alınmış, ayrıca transfer learning yöntemleriyle ResNet gibi önceden eğitilmiş modellerden faydalanılmıştır.
Proje adımları şu şekildedir:
1️⃣ Veri Hazırlama ve Artırma
Görseller, modelin giriş boyutuna uygun olarak yeniden boyutlandırılmıştır (224x224 piksel).
Veri artırma (data augmentation) teknikleri kullanılmıştır: döndürme, yakınlaştırma, yatay kaydırma, renk değişimi ve yatay çevirme.
Bu sayede eğitim verisinin çeşitliliği artırılarak overfitting riski azaltılmış ve modelin genelleme performansı yükseltilmiştir.
2️⃣ Model Mimarisi
Projede başlangıçta basit bir CNN mimarisi oluşturulmuştur.
Ardından, transfer learning yaklaşımıyla ResNet tabanlı modeller kullanılmıştır.
Transfer learning sayesinde daha hızlı yakınsama sağlanmış ve doğruluk oranı artırılmıştır.

✅ Eğitim Verisi
Her biri bir araba markasını temsil eden **33** alt klasör içerir.
Her klasörde ilgili markaya ait 349 görsel bulunur.
Makine öğrenimi modellerini eğitmek için kullanılır.

✅ Doğrulama Verisi
Her marka için 75 görsel içerir ve hiperparametre ayarlamaları için kullanılır.
Eğitim sırasında overfitting’i önlemeye yardımcı olur.

✅ Test Verisi
Her marka için 75 görsel içerir ve son model değerlendirmesi için kullanılır.
Eğitilen modellerin doğruluğunu ölçmeye yardımcı olur.
Bu veri seti, araba markası sınıflandırma problemleri için zengin ve çeşitlilik sağlayan bir kaynak sunmaktadır.

Proje Hedefleri
Araba markalarını doğru şekilde sınıflandırmak.
CNN tabanlı modellerin performansını transfer learning ile karşılaştırmak.
ResNet tabanlı önceden eğitilmiş modellerle %85+ doğruluk seviyesine ulaşmak.
Grad-CAM tekniği ile modelin karar verme süreçlerini görselleştirmek.
Veri artırma yöntemleriyle modelin farklı senaryolarda daha sağlam sonuçlar vermesini sağlamak.

# Metrikler

İlk aşamada veriler eğitim öncesi hazırlanmış ve data augmentation teknikleriyle çeşitlendirilmiştir. Bu süreç, modelin genelleme performansını artırmada başarılı sonuçlar vermiştir.
Transfer learning ile yapılan eğitimlerde her epoch sonunda elde edilen sonuçlar aşağıda gösterilmiştir:
<img width="1222" height="714" alt="image" src="https://github.com/user-attachments/assets/4f8494c0-cce3-4657-90f1-2f0e4c0ff94c" />
Ayrıca Grad-CAM görselleştirmeleriyle modelin karar mekanizması incelenmiştir. Eğitim sürecinde kullandığım flag’leri (örneğin USE_TENSORBOARD, USE_EARLY_STOP, USE_CLASS_WEIGHTS vb.) bazı denemelerde farklı ayarlanması ,sonuçların farklılık göstermesine neden olmuştur. Bu değişikliklerin model performansı üzerindeki etkisini gözlemlemek önemli bir deneyim oldu.
<img width="634" height="693" alt="image" src="https://github.com/user-attachments/assets/36d9882f-64aa-49cd-b496-55143e4c3504" />
<img width="1349" height="847" alt="image" src="https://github.com/user-attachments/assets/c1b81dfb-201d-4c8c-97cd-487e0e4e84c0" />
**Grad Cam**
Modelin eğitim sonucunda hangi noktalara daha çok odaklandığına göre bias(yanlılık) olup olmadığını anlamamızı sağlar.
**Confusion Matrix**
Modelin hangi sınıflarda hata yaptığını daha net görebilmek için confusion matrix kullanılmıştır:
Bu görselden, bazı araba markalarının (örneğin X ve Y) birbirine sıkça karıştığı anlaşılmaktadır. Bu durum, görsellerin birbirine çok benzemesinden kaynaklanıyor olabilir.
Transfer Learning metrik bakımından daha yüksek sonuç almıştır.


# Sonuç ve Gelecek Çalışmalar
Bu sonuçlar, 33 sınıftan oluşan bir veri setinde temel CNN mimarisi kullanılarak elde edilmiştir. Çok sınıflı bir problemde temel CNN mimarisi sınırlı kapasiteye sahip olduğu için doğruluk oranı düşük kalmıştır.
Genel doğruluk (accuracy): %25.09
Ortalama F1 (macro avg): ~0.24
Ağırlıklı ortalama F1 (weighted avg): ~0.24
Yani model, sınıfların büyük çoğunluğunu doğru ayırt etmekte zorlanmıştır.
🔍 Sınıf Bazlı Sonuçlar
Görece iyi tahmin edilen markalar: FIAT (f1: 0.45), Chrysler (f1: 0.42), Jeep (f1: 0.41), Aston Martin (recall: 0.61, f1: 0.39)
Orta seviyede kalan markalar: Land Rover (f1: 0.37), GMC (f1: 0.34), Dodge (f1: 0.29)
Zayıf tahmin edilen markalar: Ford (f1: 0.09), Kia (f1: 0.02), Honda (f1: 0.12), BMW (f1: 0.13)

Bazı markalarda model tamamen başarısız olurken, bazı markalarda nispeten daha iyi performans göstermiştir. Bu fark, transfer learning’in pratik projelerde neden sıkça tercih edildiğini göstermektedir.
Gelecek çalışmalarımda,
**Model Karmaşıklığını Artırma**:
Katman sayısı ve filtre boyutlarını artırarak daha derin CNN mimarilerini test edip, temel CNN ile elde edilen sonuçlarla karşılaştırmayı düşünüyorum.
Veri Dengesizliği ve Benzerlik Sorunları:
Sınıflar arasındaki görsel benzerlikleri azaltmak için daha güçlü data augmentation teknikleri (color jitter, random crop, Gaussian noise) uygulamayı planlıyorum. Ayrıca class weights veya weighted sampler kullanarak az tahmin edilen markaların öğrenilmesini güçlendirmeyi hedefliyorum.
**Model Açıklanabilirliği (Explainability)**:
Grad-CAM dışında farklı görselleştirme ve yorumlama yöntemlerini (ör. LIME, SHAP) araştırarak modelin karar verme mekanizmasını daha derinlemesine incelemeyi planlıyorum.
Farklı Öğrenme Paradigmaları:9
Transfer learning dışında self-supervised learning ve contrastive learning yaklaşımlarını da test ederek, sınıf ayrımını iyileştirmeyi hedefliyorum.
**Kayıp Fonksiyonları ve Hiperparametreler**:
CrossEntropyLoss dışında farklı loss fonksiyonlarının (ör. focal loss) performans üzerindeki etkilerini incelemeyi, ayrıca learning rate ve batch size gibi hiperparametreleri optimize etmeyi planlıyorum.

# Linkler
https://www.kaggle.com/datasets/ahmedelsany/car-brand-classification-dataset
https://www.kaggle.com/code/haysaa/project1
