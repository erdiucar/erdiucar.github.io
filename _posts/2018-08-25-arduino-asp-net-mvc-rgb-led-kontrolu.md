---
title: 'Arduino ve ASP.NET MVC ile RGB Led Kontrolü Projesi'
date: '2018-08-25T16:16:02+03:00'
description: Projemde, Arduino' ya internet sitesi üzerinden erişerek RGB Led kontrol
  ediyorum. Web sitesini ASP.NET MVC ile yaptım. Entity Framework ve LINQ kullandım.
layout: post
permalink: /arduino-asp-net-mvc-rgb-led-kontrolu/
image: /assets/img/posts/2018/08/Arduino-asp-net-mvc-rgb-led-825x510.jpg
categories:
  - Programlama
tags:
  - arduino
  - 'asp.net mvc'
  - 'internet of things'
  - iot
  - 'nesnelerin interneti'
  - 'rgb led'
---

## Arduino ile Nesnelerin İnterneti (Internet of Things - IoT)

Günümüz teknolojisi sayesinde internete bağlı olan nesneler, hayatlarımızda yer edinmeye başladı. Akıllı nesneler şu an endüstride, ev ve binaların otomasyonunda, ulaşımda, çevre analizinde, enerji ve sağlık sektöründe yoğun bir şekilde kullanılıyor. Arduino ve Raspberry Pi gibi kartları programlayarak, siz de nesneleri internete bağlayıp kontrol edebilirsiniz. Arduino'nun çeşit çeşit modeli var. Arduino'nun ethernet kartı olmayan versiyonlarında, internet bağlantısı için Ethernet Shield almanız gerekiyor. Raspberry Pi için böyle bir zorunluluk yok çünkü üzerinde ethernet kartı var.

![Arduino ile IoT](/assets/img/posts/2018/08/iot.png)

## Projeyi Nasıl Yaptım?

Bu projemde, Arduino'ya internet sitesi üzerinden erişerek RGB Led kontrol ediyorum. Önce internet sitesi üzerinde Hex kodunu kırmızı, yeşil ve mavi renk olarak ayırıyorum. Led'i açacaksam, karta mesajı "kırmızı + yeşil + mavi + hex kodu" olarak gönderiyorum. Kapayacaksam "Kapat" mesajı gönderiyorum. Arduino içinde bu gelen mesaja bakıyorum. Eğer mesaj renk açmayla ilgiliyse, mesajı tekrar renklere ayırıp Led'i yakıyorum. "Kapat" mesajı geldiyse Led'i kapıyorum. Ayrıca Arduino'dan, bağlanan siteye RGB Led'in durumuyla ilgili mesaj gönderiyorum. Aynı rengin tekrar açılması istendiyse Led'i ellemiyorum ve siteye "Renk aynı" mesajı gönderiyorum. Kapalıyken kapanması istendiyse, siteye "Kapalı" mesajı gönderiyorum. İnternet sitesine gelen mesaja bakarak, Arduino'nun hangi tarih-saatte açılıp kapandığının ve hangi renk olduğunun bilgisini veri tabanına ekliyorum. Eğer aynı rengi bir daha açma mesajı gönderdiysem veya kapalıyken tekrar kapama butonuna bastıysam, veri tabanına herhangi bir ekleme yapmıyorum ve sayfayı yeniliyorum. İnternet sitesini ASP.NET MVC ile yaptım. Tasarımını Bootstrap ile yaptım. Veri tabanını, Entity Framework kullanarak, *Code First* tekniğiyle oluşturdum. Veri sorgulama, ekleme ve çıkarma işlemlerini LINQ Ve Entity Framework aracılığıyla yaptım. Projeyi aşağıdaki videodan izleyebilirsiniz:

[![Arduino ve ASP.NET MVC ile RGB Led Kontrolü Projesi](https://img.youtube.com/vi/wOaQA5FbZU8/hqdefault.jpg)](https://www.youtube.com/watch?v=wOaQA5FbZU8)

👉 [YouTube'da İzle](https://www.youtube.com/watch?v=wOaQA5FbZU8)

## Projede kullandığım malzemeler

- Arduino Uno Rev3
- Arduino Ethernet Shield
- Breadboard
- 3 x 220 Ω direnç
- 1 x Ortak anot RGB Led
- 4 x İki ucu erkek jumper kablo

## Arduino Bağlantı Şeması, Modem Ayarı ve Kodu

### Bağlantı Şeması

![Arduino Bağlantı Şeması](/assets/img/posts/2018/08/arduino-sema.png)

**Not:** RGB Led'in uzun bacağı 5V'a bağlanıyor.

### Modem Ayarı

Arduino ile internet projelerinde, modemde bir IP ve Port eşleştirme yapmanız gerekiyor. Ben projemde "192.168.1.13" IP'si ve 8090 portunu Arduino ile eşleştirdim. Tarayıcınızın adres satırına "192.168.1.1" yazarak modeminizin paneline ulaşabilirsiniz. Benim kullandığım modemde "Gelişmiş - NAT - Port Eşleştirme" kısmından ayarlama yapılıyor.

### Kod

Github üzerinde incelemek için [tıklayın](https://github.com/erdiucar/Arduino/blob/master/Arduino_ile_Internet_Uzerinden_Rgb_Led_Kontrolu/Arduino_ile_Internet_Uzerinden_Rgb_Led_Kontrolu.ino).

```cpp
// Kullanılacak kütüphaneler çağrılıyor
#include <SPI.h>
#include <Ethernet.h>
// Kırmızı, yeşil ve mavi renk için sabit oluşturuyorum
const int kirmizi = 6;
const int yesil = 5;
const int mavi = 3;
// Led' in son durumunu bu değişkende tutuyorum. Eğer kapalı değilse son gelen renk hex formatında atanıyor (#000000 gibi)
String sonRenk = "Kapalı";
// Ethernet kalkanının, mac ve ip adresi giriliyor. Başka adreslerle çakışmadığı sürece istenilen girilebilir
byte mac[] = {0x00, 0xAA, 0xBB, 0xCC, 0xDE, 0x02};
// Ip adresi elle belirleniyor. istenirse otomatik atama da yapılabilir
IPAddress ip(192,168,1,13);
// HTTP için 8090 portunu açtığım için onu yazıyorum
EthernetServer server(8090);
// Burada gerekli ön hazırlıklar yapılıyor.
void setup() {
  // Bilgisayarla seri iletişim başlatılıyor. Saniyede 9600 bit gönderimi ayarlanıyor
  Serial.begin(9600);
  // Çıkış olarak 3,5,6 numaralı pinler belirleniyor
  pinMode(kirmizi, OUTPUT);
  pinMode(yesil, OUTPUT);
  pinMode(mavi, OUTPUT);
  // Led başlangıçta kapatılıyor. Rgb led anot olduğu için HIGH yapınca kapanıyor.
  digitalWrite(kirmizi, HIGH);
  digitalWrite(yesil, HIGH);
  digitalWrite(mavi, HIGH);
  // Ethernet belirlenen ip'de çalıştırılıyor
  Ethernet.begin (mac, ip);
  // Sunucu başlatılıyor
  server.begin();
}
// Döngü başlatılıyor
void loop() {
  // İstemcinin bağlanmasını bekleniyor
  EthernetClient client = server.available();
  // Eğer istemci bağlandıysa bu bölüm çalışıyor
  if (client) {
    String gelen = "";
    // İstemci bağlı olduğu sürece bu döngü çalışıyor
    while (client.connected()) {
      if (client.available()) {
        // Arduino'ya bağlanan bilgisayardan gelen mesajın karakteri okunup c değişkenine atanıyor
        char c = client.read();
        // Seri monitörde gelen karakterleri sırayla yazdırıyorum
        Serial.print(c);
        // İstemciden gelen karakterler "gelen" isimli stringe ekleniyor
        gelen += c;
        // Eğer boş bir satırdan sonra tekrar boş bir satıra denk gelinirse HTTP isteği sonlanmış demektir
        if (c == '\n') {
          // İstemciden gelen mesaj "Kapat" ise led kapanıyor ve sonRenk değişkeni "Kapalı" oluyor.
          if (gelen == "Kapat\n") {
            client.print(sonRenk);
            sonRenk = ledKapa();
            //Serial.println(sonRenk);
          } else {
            // Renk aynı mı diye kontrol etmek amaçlı bir değişken oluşturuyorum
            String kontrol = renkAyarla(gelen);
            // Eğer renk aynıysa sonRenk aynı kalıyor ve istemciye "Renk aynı" diye mesaj gönderiliyor
            if (kontrol == "Renk aynı") {
              client.print("Renk aynı");
              //Serial.println(sonRenk);
              //Serial.println("Renk aynı");
            }
            // Değilse sonRenk'e yeni gelen renk atanıyor ve istemciye en son gönderdiği renk gönderiliyor
            else {
              sonRenk = kontrol;
              client.print(sonRenk);
              //Serial.println(sonRenk);
            }
          }
          break;
        }
      }
    }
    // Web tarayıcıya verileri alması için 1 ms zaman veriliyor
    delay(1);
    // İstemciyle bağlantı sonlandırılıyor
    client.stop();
  }
}
// Bu metodla rgb led'in renkleri ayarlanıyor
void setColor(int red, int green, int blue) {
  analogWrite(kirmizi, red);
  analogWrite(yesil, green);
  analogWrite(mavi, blue);
}
// Bu metodla rgb led kapanıyor ve "Kapalı" mesajı döndürüyor
String ledKapa() {
  digitalWrite(kirmizi, HIGH);
  digitalWrite(yesil, HIGH);
  digitalWrite(mavi, HIGH);
  return "Kapalı";
}
// Rgb led anot olduğu için renk düzenlemesi yapmak gerekiyor
int renkDuzenle (int renk) {
  return (255 - renk);
}
// Bu metodla gelen mesaj parçalara ayrılıyor. İstemciye gönderilecek renk belirleniyor
String renkAyarla(String s) {
  String red = "";
  String green = "";
  String blue = "";
  String gonderilecekRenk = "";
  byte sayac = 1;
  // Gelen mesajın tüm karakterleri kontrol ediliyor. '+' karakteri görülürse sayaç arttırılarak diğer renge atama yapılıyor. '\n' ise döngü sonlandırılıyor.
  for(int i = 0, r = s.length(); i < r; i++) {
    if (s[i] == '+') {
      sayac++;
      continue;
    } else if (s[i] == '\n') {
      break;
    } else {
      if (sayac == 1) {
        red += s[i];
      } else if (sayac == 2) {
        green += s[i];
      } else if (sayac == 3) {
        blue += s[i];
      } else {
        gonderilecekRenk += s[i];
      }
    }
  }
  // sonRenk değişkeniyle gelen renk aynı ise, "Renk aynı" mesajı döndürülüyor
  if (gonderilecekRenk == sonRenk) {
    return "Renk aynı";
  }
  // Renk aynı değilse yeni renk ayarlanıyor ve bu yeni renk döndürülüyor
  else {
    setColor(renkDuzenle(red.toInt()), renkDuzenle(green.toInt()), renkDuzenle(blue.toInt()));
    return gonderilecekRenk;
  }
}
```

## ASP.NET MVC Anasayfa, Veri Tabanı Ekranı ve Kodu

### Ana Sayfa

![Ana Sayfa](/assets/img/posts/2018/08/ana-sayfa.png)

### Veri Tabanı Ekranı

![Veri tabanı ekranı](/assets/img/posts/2018/08/veri-tabani.png)

### Kodlar

Model, View ve Controller kodları burada çok yer kaplayacağı için Github sayfa linklerini verdim.

**Model:**

- [Database modeli](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Models/RgbLedDb.cs)
- [Diğer model](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Models/NewViewModel.cs)

**View:**

- [Ana sayfa](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Views/Home/Index.cshtml)
- [Veri tabanı ekranı](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Views/VeriTabani/Index.cshtml)

**Controller:**

- [Ana sayfa](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Controllers/HomeController.cs)
- [Veri tabanı ekranı](https://github.com/erdiucar/ASP.NET-MVC/blob/master/RgbLedMvc/RgbLedMvc/Controllers/VeriTabaniController.cs)

---

Projeyi indirmek isterseniz:

- Arduino için [tıklayın](https://github.com/erdiucar/Arduino) ("Arduino_ile_Internet_Uzerinden_Rgb_Led_Kontrolu" adlı klasör)
- ASP.NET MVC için [tıklayın](https://github.com/erdiucar/ASP.NET-MVC) ("RgbLedMvc" adlı klasör)

Diğer yazılarımı incelemek için tıklayın => [Erdi Uçar](https://www.erdiucar.com)
