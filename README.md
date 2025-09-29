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
Kendi CNN modelimde doğruluk oranı düşük kalmıştır, bu durum veri setinin karmaşıklığından ve modelin sınırlı kapasitesinden kaynaklanmaktadır. Buna karşın transfer learning yönteminde doğruluk oranı belirgin şekilde artmıştır. Bu fark, transfer learning’in pratik projelerde neden sıkça tercih edildiğini göstermektedir.
CNN mimarisini farklı derinlik ve katman kombinasyonlarıyla test ederek literatürdeki performanslarla karşılaştırmayı,
Transfer learning dışında self-supervised learning ve contrastive learning yaklaşımlarını incelemeyi,
Model açıklanabilirliğini (explainability) artırmak için Grad-CAM dışında farklı görselleştirme ve yorumlama yöntemlerini araştırmayı,
Eğitim sürecinde farklı kayıp fonksiyonlarının (loss functions) performans üzerindeki etkilerini analiz etmeyi planlıyorum.

# Linkler
https://www.kaggle.com/datasets/ahmedelsany/car-brand-classification-dataset
https://www.kaggle.com/code/haysaa/project1
