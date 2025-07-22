---
title: 'Flutter Kurulumu (Windows)'
date: 2019-08-10 14:15:08 +0300
description: Windows'a Flutter kurulumu nasıl yapılır sorusuna bu yazıma bakarak cevap
  bulabilirsiniz. Diğer platformlara kurulum için de yönlendirmeler yazıda mevcut.
permalink: /flutter-kurulumu-windows/
image: /assets/img/posts/2019/08/flutter-kurulumu-825x510.png
categories: [Programlama]
tags: [android studio, flutter, flutter kurulumu, flutter kurulumu windows, windows flutter kurulumu]
---

## Flutter Kurulumu İçin Minimum Sistem Gereksinimleri

Flutter kurulumu için Windows 7 (64-bit) veya üzeri bir işletim sistemine sahip olmanız gerekli. Ayrıca [Windows PowerShell 5.0](https://docs.microsoft.com/en-us/powershell/scripting/setup/installing-windows-powershell) ve [Git for Windows](https://git-scm.com/download/win)'un (PowerShell veya Windows komut isteminden **git** komutlarının kullanılabileceği şekilde yüklenmiş.) bilgisayarınızda kurulu olması gerekli.

## Flutter Kurulumu

`C:\src\flutter` isminde bir klasör oluşturun. Bu klasörün içinde aşağıdaki komutu çalıştırın.

```sh
git clone -b stable https://github.com/flutter/flutter.git
```

Dosya yüklemeleri bittikten sonra **flutter_console.bat**'e tıklayın. Bu ekrandan flutter komutlarını çalıştırabilirsiniz.

## PATH Ayarları

**Kontrol Paneli > Sistem ve Güvenlik > Sistem > Gelişmiş Sistem Ayarları > Gelişmiş** sekmesinde **Ortam Değişkenleri**'ne tıklayın:

![Ortam değişkenleri](/assets/img/posts/2019/08/environment-variables.png)

2 numarada gösterdiği gibi PATH'i seçin ve Edit...'e tıklayın. Son olarak `C:\src\flutter\bin` yolunu 3 numarada gösterildiği gibi Variable value değerinin sonuna başında noktalı virgülle ekleyin.

## Android Kurulumu

Ben Android Studio ile son SDK'yı kurdum. Size de bu şekilde zahmetsiz bir kurulum öneririm. Buradan [Android Studio](https://developer.android.com/studio)'yu indirip kurabilirsiniz. Kurulum esnasında eğer emülatör kullanmak istiyorsanız mutlaka seçin.

## Diğer Gereksinimler

Eğer debug ve testleriniz için telefon kullanacaksanız, telefondan **Geliştirici Ayarları**'nı ve **USB Hata Ayıklama**'yı açın. Ayrıca kullandığınız telefonun internet sitesinden USB Driver'ını mutlaka indirin ve kurun.

## Flutter Doctor

`C:\src\flutter` dosya yoluna gidin. Burada komut istemini açın ve şu komutu çalıştırın:

```sh
flutter doctor
```

![Flutter Doctor](/assets/img/posts/2019/08/flutter-doctor.png)

Komut çalıştıktan sonra flutter ihtiyaç duyduğu tüm programları ve bağlantıları kontrol ediyor. Siz de bu şekilde bir eksik var mı görebilirsiniz. Bu örnekte bir telefon bağlamadığım için gördüğünüz gibi uyarı aldım.

## IDE

**Android Studio**, **IntelliJ IDEA** ve **Visual Studio Code** ile Flutter uygulamaları geliştirebilirsiniz. Ben Flutter uygulaması geliştirirken **Visual Studio Code** kullanıyorum. Çünkü diğer IDE'lere göre kullanımı daha basit. Ayrıca çok hızlı açılması ve hafif olması benim için büyük bir artı. Eğer Visual Studio Code kullanacaksanız Flutter eklentisini indirmelisiniz.

## Mac OSX'e Flutter Kurulumu

Eğer Mac OSX için kurulum yapmak isterseniz, **Ege Şenkul**'un **teknotra.com**'daki [yazısına](https://www.teknotra.com/flutter-kurulumu-ve-ilk-projeyi-olusturma/) bakabilirsiniz.

## Detaylı Flutter Kurulumu Bilgileri

Eğer daha detaylı kurulum bilgileri almak isterseniz, Flutter'ın kendi [kurulum sayfasına](https://flutter.dev/docs/get-started/install) bakabilirsiniz.

---

Flutter hakkında daha detaylı bilgi için, bir önceki [Flutter Nedir? Neden Flutter Kullanmalıyım?](https://www.erdiucar.com/flutter-nedir-neden-flutter-kullanmaliyim/) başlıklı yazımı inceleyebilirsiniz. İlk Flutter uygulamanızı yapmak için [Flutter ile Merhaba Dünya Uygulaması](https://www.erdiucar.com/flutter-ile-merhaba-dunya-uygulamasi/) başlıklı yazıma bakabilirsiniz.
