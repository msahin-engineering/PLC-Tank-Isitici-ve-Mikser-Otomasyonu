# PLC ile Tank Isıtıcı ve Mikser Otomasyonu

## Proje Hakkında

Bu proje, Siemens S7-1200 PLC kullanılarak TIA Portal ortamında geliştirilmiş bir tank ısıtma ve mikser otomasyonudur.

Sistem; tankın doldurulması, sıvı seviyesinin kontrol edilmesi, PT100 sıcaklık sensörüyle sıcaklığın izlenmesi, ısıtıcı ve mikserin çalıştırılması ve tankın boşaltılması işlemlerini otomatik olarak gerçekleştirmek amacıyla tasarlanmıştır.

PLC programı Ladder (LAD) programlama diliyle hazırlanmış ve S7-PLCSIM V18 ortamında simülasyon testleri gerçekleştirilmiştir.

## Kullanılan Donanım ve Yazılımlar

- Siemens S7-1200 PLC (CPU 1214C DC/DC/Rly)
- TIA Portal
- S7-PLCSIM V18
- PT100 sıcaklık sensörü
- Alt seviye sensörü
- Üst seviye sensörü
- Isıtıcı
- Mikser
- Doldurma valfi
- Boşaltma valfi
- Başlatma ve durdurma butonları

## Sistemin Çalışma Aşamaları

### 1. Tank Doldurma İşleminin Başlatılması

Sistem başlatıldığında tankın doluluk durumu seviye sensörleri aracılığıyla kontrol edilir. Üst seviye sensörü aktif değilse doldurma valfi açılır ve tankın doldurulması sağlanır.

![Tank doldurma işleminin başlatılması](Tank%20doldurma%20işleminin%20başlatılması.png)

### 2. Tank Dolumunun Tamamlanması

Sıvı seviyesi üst seviye sensörüne ulaştığında doldurma işlemi tamamlanır. Doldurma valfi kapatılarak sistemin ısıtma ve karıştırma aşamasına geçmesi sağlanır.

![Tank dolumunun tamamlanması](Tank%20dolumunun%20tamamlanması.png)

### 3. Isıtıcı ve Mikserin Devreye Girmesi

Tankın dolmasının ardından PT100 sıcaklık sensöründen alınan analog veri PLC tarafından işlenir.

Sıcaklık verisi INT veri tipinden REAL veri tipine dönüştürülür ve 10'a bölünerek sıcaklık değeri elde edilir.

Sıcaklık değeri belirlenen 50 °C sınırının altında olduğunda ısıtıcı ve mikser devreye girer.

![Isıtıcı ve mikserin devreye girmesi](Isıtıcı%20ve%20mikserin%20devreye%20girmesi.png)

### 4. Tank Boşaltma İşleminin Başlatılması

Sıcaklık değeri 50 °C seviyesine ulaştığında ısıtma işlemi sonlandırılır.

Boşaltma valfi devreye girerek tank içerisindeki sıvının tahliye edilmesini sağlar. Boşaltma işlemi seviye sensörlerinden alınan bilgilere göre kontrol edilir.

![Tank boşaltma işleminin başlatılması](Tank%20boşaltma%20işleminin%20başlatılması.png)

### 5. PLC Giriş ve Çıkış Adres Tablosu

Projede kullanılan PLC giriş, çıkış ve hafıza adresleri aşağıda gösterilmiştir.

![PLC giriş ve çıkış adres tablosu](PLC%20giriş%20ve%20çıkış%20adres%20tablosu.png)

| Değişken | Veri Tipi | PLC Adresi |
|---|---|---|
| Start Butonu | Bool | %I0.0 |
| Stop Butonu | Bool | %I0.1 |
| Alt Seviye Sensörü | Bool | %I0.2 |
| Üst Seviye Sensörü | Bool | %I0.3 |
| PT100 Girişi | Int | %IW96 |
| Isıtıcı | Bool | %Q0.0 |
| Mikser | Bool | %Q0.1 |
| Doldurma Valfi | Bool | %Q0.2 |
| Boşaltma Valfi | Bool | %Q0.3 |
| Sistem Genel Start | Bool | %M5.0 |
| Tag_1 | Int | %MW20 |
| Tag_2 | Real | %MD22 |
| Sıcaklık Değeri | Real | %MD26 |

## PLC Programında Kullanılan Teknikler

- Ladder (LAD) programlama
- Başlatma ve durdurma kontrolü
- Seviye sensörleriyle sıvı kontrolü
- Doldurma ve boşaltma valflerinin kontrolü
- TON zamanlayıcı kullanımı
- Analog sıcaklık verisinin işlenmesi
- MOVE komutuyla veri aktarımı
- CONV komutuyla INT → REAL dönüşümü
- DIV komutuyla sıcaklık değerinin ölçeklendirilmesi
- Sıcaklık karşılaştırma işlemleri
- PLC giriş ve çıkışlarının çevrim içi izlenmesi
- S7-PLCSIM ile simülasyon ve test işlemleri

## Projenin Amacı

Bu projenin amacı, endüstriyel otomasyon sistemlerinde kullanılan PLC programlama tekniklerini uygulamalı olarak geliştirmek ve tank dolumu, sıcaklık kontrolü, karıştırma ve boşaltma işlemlerini tek bir otomasyon sistemi içerisinde gerçekleştirmektir.

Proje kapsamında dijital giriş ve çıkışların kontrolü, analog verilerin işlenmesi, zamanlayıcıların kullanılması ve otomatik işlem sıralamasının oluşturulması üzerine çalışmalar gerçekleştirilmiştir.
