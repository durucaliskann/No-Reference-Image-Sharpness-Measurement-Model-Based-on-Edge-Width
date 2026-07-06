# Kenar Genişliğine Dayalı Referanssız Görüntü Netliği Ölçüm Modeli

## 📌 Proje Özeti
Ondokuz Mayıs Üniversitesi bünyesinde akademik bir mühendislik projesi kapsamında geliştirilen bu çalışma, içeriğe duyarlı olmayan, referanssız ve kenar genişliği istatistiklerini temel alan, kullanıcı destekli bir netlik ölçüm modelidir[cite: 1]. Projenin detaylı metodolojisi ve analizleri makale formatında raporlanmıştır[cite: 1].

> **Not:** Bu projenin kaynak kodları kapalı tutulmaktadır. Bu depo, geliştirilen mimarinin teorik altyapısını ve elde edilen istatistiksel performans çıktılarını sunmak amacıyla hazırlanmıştır.

## ⚙️ Metodoloji ve Teknolojiler
Yazılım mimarisi, nesne yönelimli programlama (OOP) prensiplerine uygun olarak **C++17** standardında geliştirilmiş ve matris operasyonları için açık kaynak kodlu **OpenCV 4.8.0** kütüphanesi ile entegre edilmiştir[cite: 1].

Geliştirilen özgün yapılar:
* **Çift Eşikli Kenar Mimarisi:** Klasik histerezis eşiklemesi aşılarak, "Ana Kenar" ve "Aday Kenar" havuzlarını birbirinden ayıran, bağlı bileşen tabanlı ön işlem mimarisi geliştirilmiştir[cite: 1].
* **Eğim Durmalı (Slope-Stop) Tarama:** Sabit mesafeli aramalar yerine, gri seviye profilinin anlık türevini izleyen Eğim Durmalı uç nokta tarama algoritması tasarlanmıştır[cite: 1].
* **Tip 3 Parabolik Mesafe Faktörü:** Bulanıklığın etkilerini yansıtan basamak kenarları, Tip 3 Parabolik Mesafe Faktörü ile ağırlıklandırılarak nihai skor elde edilmiştir[cite: 1].

## 📊 Analiz Sonuçları
Karmaşık dokulu görüntüler (örneğin uçak test görselleri) üzerindeki analizlerde sistem şu değerlere ulaşmıştır:
* **Geçerli Kenar Ölçüm Oranı:** %96.86[cite: 1].
* **Kayıp Ölçüm Oranı:** Geleneksel yöntemlere kıyasla %3.14 seviyesine indirilmiştir[cite: 1].
* **Hesaplama Süresi:** Görüntü başına yalnızca 0.22 saniye (Endüstriyel gerçek zamanlı sistem standartlarına uygundur)[cite: 1].
* **Sınıra Yaklaşma Oranı:** 0.00001[cite: 1].

## 👥 Proje Geliştiricileri
* Mehmet Emir ÇEBİ[cite: 1]
* Duru ÇALIŞKAN[cite: 1]
Elektrik Elektronik Mühendisliği, Mühendislik Fakültesi, Ondokuz Mayıs Üniversitesi, Samsun, Türkiye[cite: 1].
