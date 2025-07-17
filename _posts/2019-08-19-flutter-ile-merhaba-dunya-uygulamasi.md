---
title: 'Flutter ile Merhaba Dünya Uygulaması'
date: '2019-08-19T20:24:50+03:00'
description: Flutter yazı serime bu paylaşımımla devam ediyorum. Flutter ile Merhaba
  Dünya uygulaması yaptım ve detaylarını sizlerle paylaştım.
layout: post
permalink: /flutter-ile-merhaba-dunya-uygulamasi/
image: /assets/img/posts/2019/08/hello-world-app-flutter-825x448.png
categories:
  - Programlama
tags:
  - flutter
---

Flutter ile Merhaba Dünya Uygulaması yaparken, kod yapısına biraz aşinalık kazanacağız. Proje klasörünün oluşturulacağı konumda aşağıdaki kodu çalıştırıyoruz:

```sh
flutter create proje_ismi
```

Yüklemelerden sonra proje klasörlerini incelediğimizde, hem Android hem de iOS için klasörler oluşturulduğunu görüyoruz. Şimdilik bizim bu kısımlarla bir ilgimiz yok. Flutter uygulamamıza, **lib** klasöründeki *main.dart* dosyasını düzenleyerek başlayacağız. *main.dart* dosyasını temizleyip aşağıdaki kodu yapıştıralım:

```dart
import 'package:flutter/material.dart';

void main() => runApp(MyApp());

class MyApp extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(primarySwatch: Colors.cyan),
      home: Scaffold(
        backgroundColor: Colors.cyan[50],
        appBar: AppBar(
          title: Center(child: Text("Hello World")),
        ),
        floatingActionButton: FloatingActionButton(
          onPressed: printHelloWorld,
          child: Icon(Icons.print),
        ),
      ),
    );
  }
}

void printHelloWorld() {
  print("Hello World!");
}
```

![Flutter Merhaba Dünya](/assets/img/posts/2019/08/Screenshot_2019-08-18-23-00-24.png)

Ardından debug yapalım. Uygulama açılınca sağ alttaki butona basalım. Butona bastıktan sonra, Debug Console'da resimdeki gibi "Hello World!" yazısını görüyoruz.

![Print Hello World](/assets/img/posts/2019/08/print-hello-world.png)

`floatingActionButton`'ın `onPressed` özelliğine `printHelloWorld` fonksiyonunu yazdık. Bu sayede her butona basışımızda `printHelloWorld` fonksiyonu çalıştırılıyor.

---

Eğer Flutter ile ilgili daha detaylı bilgi almak isterseniz, [Flutter Nedir?](http://erdiucar.local/flutter-nedir-neden-flutter-kullanmaliyim/) ve [Flutter Kurulumu](http://erdiucar.local/flutter-kurulumu-windows/) başlıklı yazılarımı inceleyebilirsiniz. Proje klasörüne [GitHub](https://github.com/erdiucar/flutter_hello_world) sayfamdan ulaşabilirsiniz.
