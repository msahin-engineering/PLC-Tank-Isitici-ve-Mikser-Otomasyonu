# PLC ile Tank Isıtıcı ve Mikser Otomasyonu

## Proje Hakkında

Bu proje, Siemens S7-1200 PLC kullanılarak TIA Portal ortamında geliştirilmiş bir tank ısıtma ve karıştırma otomasyonudur.

Sistem; tankın doldurulması, sıvı seviyesinin kontrol edilmesi, PT100 sıcaklık sensörü üzerinden sıcaklığın izlenmesi, ısıtıcı ve mikserin çalıştırılması ve tankın boşaltılması işlemlerini gerçekleştirmek amacıyla tasarlanmıştır.

PLC programı Ladder (LAD) programlama diliyle hazırlanmış ve S7-PLCSIM kullanılarak simülasyon ortamında test edilmiştir.

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

Başlatma komutuyla sistem devreye girer. Üst seviye sensöründen gelen bilgiye göre doldurma valfi kontrol edilir ve tankın doldurulması sağlanır.

![Tank doldurma işleminin başlatılması](gorseller/01-tank-doldurma.png)

### 2. Tank Dolumunun Tamamlanması

Sıvı seviyesi üst seviye sensörüne ulaştığında doldurma işlemi tamamlanır ve doldurma valfi kapatılır.

![Tank dolumunun tamamlanması](gorseller/02-tank-dolumu.png)

### 3. Isıtıcı ve Mikserin Devreye Girmesi

Tankın dolmasının ardından sıcaklık bilgisi PT100 sensöründen alınır.

PLC programında sıcaklık değeri işlenerek belirlenen sıcaklık koşuluna göre ısıtıcı ve mikser kontrol edilir.

![Isıtıcı ve mikserin devreye girmesi](gorseller/03-isitici-mikser.png)

### 4. Tank Boşaltma İşleminin Başlatılması

Sıcaklık koşulları sağlandığında boşaltma valfi devreye girer ve tank içerisindeki sıvının boşaltılması sağlanır.

![Tank boşaltma işleminin başlatılması](gorseller/04-tank-bosaltma.png)

## PLC Giriş ve Çıkış Adresleri

Projede kullanılan PLC giriş, çıkış ve hafıza adresleri aşağıdaki tabloda gösterilmiştir.

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
| Sıcaklık Değeri | %MD26 |

![PLC giriş ve çıkış adres tablosu](gorseller/05-plc-adres-tablosu.png)

## Projede Kullanılan PLC Programlama Teknikleri

- Ladder (LAD) programlama
- Başlatma ve durdurma kontrolü
- Seviye sensörleriyle valf kontrolü
- TON zamanlayıcı kullanımı
- PT100 sıcaklık verisinin işlenmesi
- Veri tipi dönüşümü (INT → REAL)
- Matematiksel işlemler ve sıcaklık karşılaştırması
- PLC giriş ve çıkışlarının simülasyon ortamında izlenmesi

## Projenin Amacı

Bu çalışmanın amacı, endüstriyel otomasyon sistemlerinde kullanılan PLC programlama tekniklerini uygulamalı olarak öğrenmek ve tank dolumu, sıcaklık kontrolü, karıştırma ve boşaltma işlemlerini tek bir otomasyon sistemi içerisinde gerçekleştirmektir.
