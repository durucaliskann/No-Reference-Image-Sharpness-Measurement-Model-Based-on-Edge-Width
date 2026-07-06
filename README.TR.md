# Kenar Genişliğine Dayalı Referanssız Görüntü Netliği Ölçüm Modeli

## 📌 Proje Özeti
Ondokuz Mayıs Üniversitesi bünyesinde akademik bir mühendislik projesi kapsamında geliştirilen bu çalışma, içeriğe duyarlı olmayan, referanssız ve kenar genişliği istatistiklerini temel alan netlik ölçüm modelidir[cite: 1]. Projenin algoritmik detayları makale formatında raporlanmıştır[cite: 1].

> **Not:** Bu projenin kaynak kodları kapalı tutulmaktadır. Bu depo, geliştirilen mimarinin matematiksel altyapısını ve elde edilen performans çıktılarını sunmak amacıyla hazırlanmıştır.

## ⚙️ Metodoloji ve Algoritmik Mimari
Yazılım, nesne yönelimli programlama (OOP) prensiplerine uygun olarak **C++17** standardında geliştirilmiş ve açık kaynak kodlu **OpenCV 4.8.0** kütüphanesi ile entegre edilmiştir[cite: 1]. Bellek yönetimini optimize etmek amacıyla sistem durum verileri yapılandırılmış nesneler (encapsulation) içerisine alınmıştır[cite: 1].

Projenin temel algoritmik yapıtaşları şunlardır:
* **Çift Eşikli Etkileşimli Ön İşlem:** Klasik histerezis eşiklemesi aşılarak, bağlı bileşen (connected component) analizi ile "Ana Kenar" ve "Aday Kenar" havuzları ayrıştırılmıştır[cite: 1]. Rastgele piksel üretimine izin vermeyen ROI (Region of Interest) tabanlı fırça modülü ile gürültülerin elenmesi sağlanmıştır[cite: 1].
* **Sekiz Komşuluklu Yön Tayini:** Merkez kenar pikselleri etrafındaki $3\times3$ lokal matrisler üzerinden dikey, yatay ve çapraz eksenlerde mutlak gri seviye farkları hesaplanmıştır[cite: 1]. Minimum gradyan varyansını veren eksene dik açı, gerçek kenar yönü olarak atanmıştır[cite: 1].
* **Eğim Durmalı (Slope-Stop) Tarama:** Atanan yön doğrultusunda (maksimum 30 piksel arama limitiyle) anlık birinci türev takibe alınmıştır[cite: 1]. Eğim durma koşulu (`tolSlope=0.001`) ve ayrışma kontrastı (`minContrast=0.003`) sağlandığı anda profil uç noktaları kilitlenerek gerçek kenar genişliği hesaplanmıştır[cite: 1].
* **Tip 3 Parabolik Mesafe Ağırlıklandırması:** Ölçülen genişlikler 0.375 piksel (binWidth) hassasiyetle sepetlenerek baskın kenar genişliği ($w_{mp}$) tespit edilmiştir[cite: 1]. Histogram bileşenleri, monotonluk kararlılığı yüksek Tip 3 Parabolik Mesafe Faktörü ile ağırlıklandırılarak nihai nesnel netlik skoruna dönüştürülmüştür[cite: 1].

## 📊 Analiz Sonuçları
Sistem, bulut ve katı cisim barındıran karmaşık dokulu referans görseller üzerinde test edilmiş ve şu veriler elde edilmiştir:
* **Geçerli Kenar Ölçüm Oranı:** %96.86 (Eğim durmalı motorun uç nokta kilitlenme başarısı)[cite: 1].
* **Kayıp Ölçüm Oranı:** %3.14 (Gradyan süreksizliği nedeniyle elenen piksel oranı)[cite: 1].
* **Hesaplama Süresi:** Görüntü başına 0.22 saniye (Endüstriyel gerçek zamanlı süreçlere uygun)[cite: 1].
* **Sınıra Yaklaşma Oranı:** 0.0000 (Arama penceresinin doğal kenarları yapay olarak kırpmadığı kanıtlanmıştır)[cite: 1].

## 👥 Proje Geliştiricileri
* Mehmet Emir ÇEBİ[cite: 1]
* Duru ÇALIŞKAN[cite: 1]
Elektrik Elektronik Mühendisliği, Mühendislik Fakültesi, Ondokuz Mayıs Üniversitesi, Samsun, Türkiye[cite: 1].
