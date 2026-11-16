# PLC ile Tank Isıtıcı ve Mikser Otomasyonu

## Proje Hakkında

Bu proje, Siemens S7-1200 PLC ve TIA Portal kullanılarak geliştirilmiş bir tank ısıtma ve mikser otomasyonudur.

Sistem; tankın doldurulması, sıvı seviyesinin kontrol edilmesi, PT100 sensörüyle sıcaklığın izlenmesi, ısıtıcı ve mikserin çalıştırılması ve tankın boşaltılması işlemlerini otomatik olarak gerçekleştirmek amacıyla tasarlanmıştır.

PLC programı Ladder (LAD) diliyle hazırlanmış ve S7-PLCSIM V18 ortamında test edilmiştir.

## Kullanılan Donanım ve Yazılımlar

- Siemens S7-1200 PLC (CPU 1214C DC/DC/Rly)
- TIA Portal
- S7-PLCSIM V18
- PT100 sıcaklık sensörü
- Alt ve üst seviye sensörleri
- Isıtıcı ve mikser
- Doldurma ve boşaltma valfleri
- Başlatma ve durdurma butonları

## Sistemin Çalışma Aşamaları

### 1. Tank Doldurma İşleminin Başlatılması

Sistem başlatıldığında tankın doluluk durumu kontrol edilir. Tank dolu değilse doldurma valfi açılır ve dolum işlemi başlatılır.

![1. Tank doldurma işleminin başlatılması](Screenshot%202026-11-16%20155153.png)

### 2. Tank Dolumunun Tamamlanması

Sıvı seviyesi üst seviye sensörüne ulaştığında doldurma valfi kapatılır. Tankın dolum işlemi tamamlanır.

![2. Tank dolumunun tamamlanması](Screenshot%202026-11-16%20155318.png)

### 3. Isıtıcı ve Mikserin Devreye Girmesi

Tank dolduktan sonra PT100 sensöründen alınan sıcaklık değeri PLC tarafından işlenir. Sıcaklık belirlenen değerin altındaysa ısıtıcı ve mikser çalıştırılır.

![3. Isıtıcı ve mikserin devreye girmesi](Screenshot%202026-11-16%20155405.png)

### 4. Tank Boşaltma İşleminin Başlatılması

Sıcaklık belirlenen seviyeye ulaştığında boşaltma valfi açılır ve tank içerisindeki sıvının boşaltılması sağlanır.

![4. Tank boşaltma işleminin başlatılması](Screenshot%202026-11-16%20155658.png)

### 5. PLC Giriş ve Çıkış Adres Tablosu

Projede kullanılan PLC giriş, çıkış ve hafıza adresleri aşağıda gösterilmiştir.

![5. PLC giriş ve çıkış adres tablosu](Screenshot%202026-11-16%20161155.png)

| Değişken | PLC Adresi |
|---|---|
| Start Butonu | %I0.0 |
| Stop Butonu | %I0.1 |
| Alt Seviye Sensörü | %I0.2 |
| Üst Seviye Sensörü | %I0.3 |
| PT100 Girişi | %IW96 |
| Isıtıcı | %Q0.0 |
| Mikser | %Q0.1 |
| Doldurma Valfi | %Q0.2 |
| Boşaltma Valfi | %Q0.3 |
| Sistem Genel Start | %M5.0 |
| Tag_1 | %MW20 |
| Tag_2 | %MD22 |
| Sıcaklık Değeri | %MD26 |

## Kullanılan PLC Programlama Teknikleri

- Ladder (LAD) programlama
- Başlatma ve durdurma kontrolü
- Seviye sensörleriyle valf kontrolü
- TON zamanlayıcı kullanımı
- PT100 sıcaklık verisinin işlenmesi
- INT ve REAL veri tipi dönüşümleri
- Sıcaklık karşılaştırma işlemleri
- PLC giriş ve çıkışlarının simülasyon ortamında izlenmesi

## Projenin Amacı

Bu çalışmanın amacı, endüstriyel otomasyon sistemlerinde kullanılan PLC programlama tekniklerini uygulamalı olarak geliştirmek ve tank dolumu, sıcaklık kontrolü, karıştırma ve boşaltma işlemlerini tek bir otomasyon sistemi içerisinde gerçekleştirmektir.
