# Akbank_Bootcamp_24102024_DeepLearning


Proje: Balık Türlerini Sınıflandırma (Fish Classification)

Proje Tanımı
Bu proje, Kaggle üzerinde bulunan büyük ölçekli bir balık veri setini kullanarak farklı balık türlerini sınıflandırmayı amaçlamaktadır. Projede, görüntü işleme teknikleri ile balıkların fotoğraflarını işleyerek derin öğrenme modeline veriler sağlanır. Eğitim süreci boyunca çeşitli katmanlar kullanılarak model optimize edilir ve sınıflandırma doğruluğu artırılır. Proje kapsamında, modelin performansı doğrulama ve test veri setleri üzerinde değerlendirilmiş, ayrıca modelin tahminleri görselleştirilmiştir.

Veri Seti
Kullanılan veri seti, Kaggle platformundan alınmış "A Large-Scale Fish Dataset" veri setidir. Veri seti, çeşitli balık türlerinin resimlerini içerir. Veri setindeki her sınıf, bir balık türünü temsil eder ve her sınıf kendi klasöründe yer alır. Projede, bu görüntüler eğitim, doğrulama ve test setlerine ayrılarak model eğitiminde kullanılmıştır.

Veri Seti Özellikleri:
Görsel Formatı: .png
Sınıflar: Farklı balık türlerini temsil eden etiketler
Veri Kümesi Yapısı: Eğitim, doğrulama ve test setlerine bölünmüş.
Gereksinimler
Projenin çalışması için aşağıdaki Python kütüphanelerine ihtiyaç duyulmaktadır:

numpy
pandas
matplotlib
seaborn
tensorflow
sklearn
cv2
Bu kütüphaneler, Python ortamınıza aşağıdaki komutla kurulabilir:

bash
Kodu kopyala
pip install numpy pandas matplotlib seaborn tensorflow scikit-learn opencv-python
Proje Adımları
1. Veri Yükleme ve Ön İşleme
Görüntülerin Yüklenmesi: os ve cv2 kütüphaneleri kullanılarak balık görselleri dizinden yüklendi.
Etiketleme: Klasör yapısına göre her görselin sınıf etiketi belirlenerek bir pandas DataFrame oluşturuldu.
Veri Augmentasyonu: ImageDataGenerator kullanılarak, veri arttırma (data augmentation) işlemleri uygulandı (örn. döndürme, kaydırma, zoom vb.).
Eğitim ve Test Setlerine Bölme: Görseller eğitim ve test setlerine ayrıldı, ardından eğitim setinden bir doğrulama seti oluşturuldu.
Ölçeklendirme: StandardScaler kullanılarak eğitim, doğrulama ve test setleri ölçeklendirildi.
2. Derin Öğrenme Modeli Oluşturma
Model Mimarisi: Sequential model kullanılarak çok katmanlı bir yapay sinir ağı (DNN) oluşturuldu. Modelin yapısında farklı boyutlardaki Dense katmanlar, BatchNormalization, ve Dropout teknikleri kullanıldı.
Aktivasyon Fonksiyonları: Her katmanda ReLU aktivasyon fonksiyonu kullanılırken, çıkış katmanında çok sınıflı sınıflandırma için softmax aktivasyon fonksiyonu kullanıldı.
Optimizasyon ve Derleme: Model, Adam optimizatörü ve categorical_crossentropy kayıp fonksiyonu ile derlendi.
3. Modelin Eğitilmesi
Early Stopping ve Learning Rate Reduction: Modelin aşırı öğrenmesini önlemek ve eğitim sürecini optimize etmek için erken durdurma ve öğrenme hızını azaltma (learning rate reduction) callback'leri kullanıldı.
Eğitim Süreci: Model 100 epoch boyunca eğitildi ve doğrulama verileri ile performans izlendi.
4. Model Performansının Değerlendirilmesi
Model Değerlendirme: Test verileri kullanılarak modelin doğruluğu (accuracy) ve kaybı (loss) hesaplandı.
Sınıflandırma Raporu ve Confusion Matrix: Modelin sınıflar bazındaki performansı classification_report ile raporlandı ve confusion_matrix ile hangi sınıflarda doğru ve yanlış tahminler yapıldığını gösteren bir matris oluşturuldu.
Eğitim Süreci Görselleştirme: Eğitim ve doğrulama doğruluğu ile kaybı grafikleri çizilerek modelin zaman içerisindeki öğrenme süreci analiz edildi.
5. Tahminlerin Görselleştirilmesi
Rastgele Tahminlerin Görselleştirilmesi: Test setinden rastgele seçilen örnekler, modelin tahminleri ile birlikte görselleştirildi. Doğru tahminler yeşil, yanlış tahminler kırmızı renkle işaretlendi.
Confusion Matrix Görselleştirilmesi: Sınıflar arasındaki karışıklıkları daha iyi anlamak için confusion matrix ısı haritası oluşturuldu.
Kullanılan Fonksiyonlar
load_and_preprocess_data: Balık veri setini yükler, ölçeklendirir ve eğitim-test setlerine ayırır.
make_predictions: Modelin test seti üzerindeki tahminlerini döndürür.
plot_confusion_matrix: Gerçek ve tahmin edilen sınıfları kullanarak confusion matrix oluşturur ve görselleştirir.
plot_random_predictions: Test setinden rastgele seçilen örneklerin gerçek ve tahmin edilen etiketlerini görselleştirir.
Proje Sonuçları
Bu projede oluşturulan model, balık türlerini sınıflandırmada oldukça başarılı sonuçlar vermiştir. Eğitim sürecinde kullanılan veri arttırma ve erken durdurma gibi teknikler, modelin aşırı öğrenmesini önlemiş ve performansı artırmıştır. Sonuçlar, eğitim ve doğrulama setlerinde elde edilen doğruluk değerleri ile test setinde hesaplanan doğruluk oranı üzerinden değerlendirildi.

https://www.kaggle.com/code/yusufziyademirel/fish-classification-yusufziyademirel
