# Yazilim-Modeli-Final-odevi

Akıllı Atık Ayrıştırma Sistemi (Arduino & Proteus)

Bu proje, atıkların kaynağında otomatik olarak ayrıştırılmasını sağlayarak geri dönüşüm süreçlerini optimize eden Arduino tabanlı bir akıllı sistem prototipidir. Sistem; metal ve plastik atıkları sensör verileriyle ayırt eder, kullanıcıyı LCD ekran üzerinden bilgilendirir ve servo motor mekanizması ile atığı ilgili hazneye yönlendirir.

 Projenin Amacı ve Analizi

Küresel atık sorununun çözümünde en kritik adım, atıkların birbirine karışmadan ayrıştırılmasıdır. Bu proje:

    Otomasyon: Manuel ayrıştırma hatalarını ortadan kaldırır.

    Verimlilik: Geri dönüşüm tesislerine giden atığın saflık oranını artırır.

    Kullanıcı Deneyimi: Görsel ve işitsel (LED ve mesaj) geri bildirimlerle kullanıcıyı eğitir.

 Teknik Tasarım ve Bileşenler

Sistem, mikrodenetleyici kontrolünde çalışan bir elektromekanik döngüdür. Proteus üzerinde tasarlanan devrede kullanılan ana bileşenler şunlardır:

    Kontrolcü: Arduino Uno (ATmega328P)

    Gösterge: 16x2 I2C LCD Ekran (LM016L)

    Mekanizma: SG90 Servo Motor (Ayrıştırma kolu için)

    Sensörler: Logic State (Gerçek prototipte Endüktif ve Kızılötesi sensörleri temsil eder)

    Geri Bildirim: Kırmızı/Yeşil LED'ler ve 220Ω koruma dirençleri.

 Devre Şeması ve Bağlantı Mimarisi

Projenin donanım mimarisi, kararlılık ve düşük enerji tüketimi odaklıdır. Bağlantılar şu şekildedir:
1. Ekran ve Motor Bağlantıları

    LCD Ekran: RS(12), E(11), D4(4), D5(5), D6(6), D7(7) pinlerine bağlıdır.

    Servo Motor: Pin 9 üzerinden PWM sinyali ile kontrol edilir.

2. Sensör ve Gösterge Bağlantıları

    Atık Algılama Sensörü: Dijital Pin 2 (Kesme veya sürekli okuma için).

    Metal Tespit Sensörü: Dijital Pin 3.

    Durum LED'leri: Hazır durumu için Yeşil LED (A0), İşlem durumu için Kırmızı LED (A1).

 Algoritma ve Çalışma Mantığı

Yazılım, "Durum Makinesi" (State Machine) mantığıyla çalışır ve her aşamada kullanıcıyı yavaşlatılmış mesajlarla bilgilendirir.

    Bekleme Durumu: Yeşil LED yanar, LCD'de "Atik Bekleniyor" mesajı döner.

    Algılama: Atık girişi (Pin 2) aktif olduğunda Kırmızı LED yanar ve "Atik Geldi!" uyarısı verilir.

    Karar Verme: * Eğer Metal Sensörü (Pin 3) aktifse; Servo 180° açısına döner, LCD'de "Tur: METAL" yazar.

        Eğer pasifse; Servo 0° açısına döner, LCD'de "Tur: PLASTIK" yazar.

    Tahliye ve Reset: Atık hazneye düşene kadar beklenir, ardından Servo 90° (başlangıç) konumuna geri döner ve sistem tekrar hazır hale gelir.

Gelecek Geliştirmeler

    IoT Entegrasyonu: ESP8266 kullanılarak hazne doluluk oranının bulut sistemine aktarılması.

    Görüntü İşleme: Yapay zeka kamerası eklenerek kağıt, cam ve plastik ayrımının daha detaylı yapılması.

    Güneş Enerjisi: Sistemin dış mekanlarda kendi enerjisini üretecek şekilde revize edilmesi.
