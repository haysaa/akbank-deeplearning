# akbank-deeplearning
Merhabalar bu repository akbank deep learning projesi için hazırlanmıştır.

#Giriş
Bu proje, derin öğrenme tabanlı bir görüntü sınıflandırma sistemi geliştirmeyi amaçlamaktadır. Kullanılan veri seti farklı araba markalarına ait görsellerden oluşmaktadır. Projede Convolutional Neural Network (CNN) mimarisi temel alınmış, ayrıca transfer learning yöntemleriyle ResNet gibi önceden eğitilmiş modellerden faydalanılmıştır.

#Metrikler

İlk aşamada veriler eğitim öncesi hazırlanmış ve data augmentation teknikleriyle çeşitlendirilmiştir. Bu süreç, modelin genelleme performansını artırmada başarılı sonuçlar vermiştir.
Transfer learning ile yapılan eğitimlerde her epoch sonunda elde edilen sonuçlar aşağıda gösterilmiştir:
<img width="1222" height="714" alt="image" src="https://github.com/user-attachments/assets/4f8494c0-cce3-4657-90f1-2f0e4c0ff94c" />
Ayrıca Grad-CAM görselleştirmeleriyle modelin karar mekanizması incelenmiştir. Eğitim sürecinde kullandığım flag’leri (örneğin USE_TENSORBOARD, USE_EARLY_STOP, USE_CLASS_WEIGHTS vb.) bazı denemelerde değiştirmeyi unutmam, sonuçların farklılık göstermesine neden olmuştur. Bu değişikliklerin model performansı üzerindeki etkisini gözlemlemek önemli bir deneyim oldu.
<img width="634" height="693" alt="image" src="https://github.com/user-attachments/assets/36d9882f-64aa-49cd-b496-55143e4c3504" />
<img width="1349" height="847" alt="image" src="https://github.com/user-attachments/assets/c1b81dfb-201d-4c8c-97cd-487e0e4e84c0" />


#Sonuç ve Gelecek Çalışmalar

CNN mimarisini farklı derinlik ve katman kombinasyonlarıyla test ederek literatürdeki performanslarla karşılaştırmayı,
Transfer learning dışında self-supervised learning ve contrastive learning yaklaşımlarını incelemeyi,
Model açıklanabilirliğini (explainability) artırmak için Grad-CAM dışında farklı görselleştirme ve yorumlama yöntemlerini araştırmayı,
Eğitim sürecinde farklı kayıp fonksiyonlarının (loss functions) performans üzerindeki etkilerini analiz etmeyi planlıyorum.
