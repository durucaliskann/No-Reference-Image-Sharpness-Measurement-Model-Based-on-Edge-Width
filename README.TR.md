# Kenar Genişliğine Dayalı Referanssız Görüntü Netliği Ölçüm Modeli

## 📌 Proje Özeti
Ondokuz Mayıs Üniversitesi bünyesinde akademik bir mühendislik projesi kapsamında geliştirilen bu çalışma, içeriğe duyarlı olmayan, referanssız ve kenar genişliği istatistiklerini temel alan netlik ölçüm modelidir. Projenin algoritmik detayları makale formatında raporlanmıştır.

> **Not:** Bu projenin kaynak kodları kapalı tutulmaktadır. Bu depo, geliştirilen mimarinin matematiksel altyapısını ve elde edilen performans çıktılarını sunmak amacıyla hazırlanmıştır.

## ⚙️ Metodoloji ve Algoritmik Mimari
Yazılım, nesne yönelimli programlama (OOP) prensiplerine uygun olarak **C++17** standardında geliştirilmiş ve açık kaynak kodlu **OpenCV 4.8.0** kütüphanesi ile entegre edilmiştir. Bellek yönetimini optimize etmek amacıyla sistem durum verileri yapılandırılmış nesneler (encapsulation) içerisine alınmıştır.

Projenin temel algoritmik yapıtaşları şunlardır:
* **Çift Eşikli Etkileşimli Ön İşlem:** Klasik histerezis eşiklemesi aşılarak, bağlı bileşen (connected component) analizi ile "Ana Kenar" ve "Aday Kenar" havuzları ayrıştırılmıştır. Rastgele piksel üretimine izin vermeyen ROI (Region of Interest) tabanlı fırça modülü ile gürültülerin elenmesi sağlanmıştır.
* **Sekiz Komşuluklu Yön Tayini:** Merkez kenar pikselleri etrafındaki 3x3 lokal matrisler üzerinden dikey, yatay ve çapraz eksenlerde mutlak gri seviye farkları hesaplanmıştır. Minimum gradyan varyansını veren eksene dik açı, gerçek kenar yönü olarak atanmıştır.
* **Eğim Durmalı (Slope-Stop) Tarama:** Atanan yön doğrultusunda (maksimum 30 piksel arama limitiyle) anlık birinci türev takibe alınmıştır. Eğim durma koşulu (`tolSlope=0.001`) ve ayrışma kontrastı (`minContrast=0.003`) sağlandığı anda profil uç noktaları kilitlenerek gerçek kenar genişliği hesaplanmıştır.
* **Tip 3 Parabolik Mesafe Ağırlıklandırması:** Ölçülen genişlikler 0.375 piksel (binWidth) hassasiyetle sepetlenerek baskın kenar genişliği (w_mp) tespit edilmiştir. Histogram bileşenleri, monotonluk kararlılığı yüksek Tip 3 Parabolik Mesafe Faktörü ile ağırlıklandırılarak nihai nesnel netlik skoruna dönüştürülmüştür.

## 📊 Analiz Sonuçları
Sistem, bulut ve katı cisim barındıran karmaşık dokulu referans görseller üzerinde test edilmiş ve şu veriler elde edilmiştir:
* **Geçerli Kenar Ölçüm Oranı:** %96.86 (Eğim durmalı motorun uç nokta kilitlenme başarısı)
* **Kayıp Ölçüm Oranı:** %3.14 (Gradyan süreksizliği nedeniyle elenen piksel oranı)
* **Hesaplama Süresi:** Görüntü başına 0.22 saniye (Endüstriyel gerçek zamanlı süreçlere uygun)
* **Sınıra Yaklaşma Oranı:** 0.0000 (Arama penceresinin doğal kenarları yapay olarak kırpmadığı kanıtlanmıştır)

## 👥 Proje Geliştiricileri
* Duru ÇALIŞKAN
* Mehmet Emir ÇEBİ
Elektrik Elektronik Mühendisliği, Mühendislik Fakültesi, Ondokuz Mayıs Üniversitesi, Samsun, Türkiye.
