---
title: 'Shell Kullanımı'
date: '2018-07-10T19:00:40+03:00'
description: Shell, bilgisayardaki programları çalıştırmak için bir komut satırı arabirimidir.
  Bu yazımda Shell kullanımı ile ilgili bilgiler veriyorum.
layout: post
permalink: /shell-kullanimi/
image: /assets/img/posts/2018/07/shell-kullanımı-1.png
categories:
    - Programlama
tags:
    - bash
    - 'bash komutları'
    - 'bash kullanımı'
    - 'bash programlama'
    - kabuk
    - 'kabuk komutları'
    - 'kabuk kullanımı'
    - 'kabuk programlama'
    - 'komut istemi'
    - 'komut satırı'
    - 'konsol komutları'
    - 'linux komut satırı'
    - 'linux komutları'
    - 'linux konsol'
    - 'linux konsol komutları'
    - 'linux terminal komutları'
    - shell
    - 'shell komutları'
    - 'shell programlama'
    - terminal
    - 'terminal komutları'
---

## Shell (Kabuk) Nedir?

*Shell* (Kabuk), bilgisayardaki programları çalıştırmak için bir komut satırı arabirimidir. Siz komut isteminde komutları yazdığınızda, Shell sizin için programları çalıştırıyor ve size çıktılarını gösteriyor. Geliştiriciler Shell'i çok sık kullanıyor çünkü hızlı ve esnek. Ayrıca web sunucularının büyük bir kısmı Linux işletim sistemi kullanıyor. Dolayısıyla Shell, Linux kullanan sunucularda dağıtım ve uzaktan yönetim için çok önemli bir araç. Shell kullanırken, bir GUI (Graphical User Interface) kullanmaya kıyasla bazı komutları bilmeniz ve ezberlemeniz gerekiyor. Ancak biraz pratik yaptıktan sonra alışıyorsunuz ve birçok şeyin çok hızlı bir şekilde yapıldığını farkediyorsunuz. Eğer daha önceden program yazdıysanız, Shell kullanımı gerçekten programlama gibi. Komutları, Shell'e özel bir dilde yazıyorsunuz ve sistem bunları çalıştırıp size çıktısını gösteriyor. Shell, Linux işletim sistemlerinde hazır yüklü olarak geliyor. Birçok Shell programı var. Çoğu Linux sisteminde **bash** kullanılıyor. Bende bu yazıda Shell'in, **bash** programını kullanıyorum.

### Shell ile yapabilecekleriniz

- Dosya ve klasörlerle çalışmak.
- Programları çalıştırmak.
- Diğer bilgisayarlarla etkileşimde bulunmak.

Shell ile etkileşimde kullandığımız programa, *terminal programı* denir. Terminal, Shell kullanmamızı sağlayan bir arayüzdür. Linux veya Mac kullanıyorsanız, hali hazırda zaten bir terminal programı var. Eğer Windows kullanıyorsanız, Windows'un da bir terminal programı var. Ancak UNIX stilinde değil ve eski MS-DOS komut satırına dayanıyor. Yani yazılan komutlar Shell'de kullandığımızdan farklı. Web geliştiricileri için UNIX stili Shell, bir standart haline gelmiştir. Çünkü internetin büyük bir kısmı, belirttiğim gibi Linux sunucularında çalışıyor. Bu yüzden bir sonraki konu başlığında, Windows'ta nasıl Shell kullanacağınızı anlatacağım. Bu arada hangi terminali kullandığınız o kadar önemli değil. Terminal, Shell'e ulaşmak için kullanılan bir araç sonuçta. Eğer internete ulaşmak için Firefox kullanıyorsanız, Firefox'u *terminale* benzetebiliriz. Firefox'u açtıktan sonra yazdığınız web sitesi, *Shell'e* örnek olabilir. Yani Firefox, bizim web sitesine girebilmemiz için kullandığımız bir araçtır. Ama web sitesine Chrome, Opera, Safari kullanarak da girebilirsiniz. *Shell* için de şöyle bir örnek verebilirim. Kendi siteme girmek için **erdiucar.com** yazıyorum. Bunu bir Shell komutu olarak düşünebilirsiniz. Shell yerine başka bir şey kullansaydım, siteme girmek için belki de **167.99.222.34** yazacaktım. Deneyip görebilirsiniz. İkisi de beni web siteme ulaştırıyor. Fakat adres satırına farklı şeyler girerek bunu yaptım. Şimdi Windows kullanıyorsanız, Mac ve Linux'tekilerle aynı şekilde çalışan bir Shell ve terminal programını nasıl kuracağınızı göstereceğim. Aralarında en popüler UNIX stili kabuk olan "Git Bash" kabuğunu kuracağız. Ardından, Shell'i nasıl özelleştireceğinizi göstereceğim. Haydi işe koyulalım!

## Windows'da Shell (Kabuk) Kurulumu ve Ayarları

[![Windows'a Shell Kurulumu](https://img.youtube.com/vi/5E0wopDFulY/hqdefault.jpg)](https://www.youtube.com/watch?v=5E0wopDFulY)

👉 [YouTube'da izle](https://www.youtube.com/watch?v=5E0wopDFulY)

Windows'a **Git-Bash**'i indirip kurmak için [tıklayınız](https://git-scm.com/download/win).

Birçok terminal programı, içinde font ve renk değişimi gibi özelliklere sahip. Ayrıca aynı anda birçok terminal açabilirsiniz. Birinde bir iş yaparken, diğerinde de başka bir işle uğraşabilirsiniz.

## Linux ve Mac Kullanıcıları İçin Terminal

![Linux ve Mac Terminal İkonu](/assets/img/posts/2018/07/terminal-ikon.png)

Terminal, bu resimde gördüğünüz gibi bir ikona sahip. Eğer bulamazsanız, bilgisayarda "terminal" diye arama yapın.

## Başlamadan Önce Tüyolar

Terminalde komut yazarken daha hızlı olmanızı sağlayacak bazı tüyolar vereceğim:

- Komutu yazmaya başladığınızda klavyede **Tab** tuşuna basarsanız, otomatik tamamlama işlevi çalışır. **Çift Tab**'ı kullanmayı da deneyin. **Çift Tab** ile bütün otomatik tamamlama olasılıklarını görebiliyorsunuz.
- Önceki yazdığınız komutları, klavyedeki yukarı ve aşağı ok tuşlarına basarak ekrana getirebiliyorsunuz. Yukarı bastıkça zamanda geriye gidersiniz, aşağıya bastıkça ileri gidersiniz.
- **Ctrl + R** kısayolu ile daha önceden yazdığınız komutları arayabilirsiniz. Ayrıca **history** komutu ile sıralı olarak geçmişte yazdığınız kodları görebilirsiniz.
- **clear** komutunu kullanarak terminal ekranını temizleyebilirsiniz. **Ctrl + L** kısayolu da aynı işlevi görüyor.
- Genellikle, **Ctrl + C** kısayolu ile veya **quit** komutu ile, çalışan programı durdurabilirsiniz. Bazı programlar terminalde tam ekran çalışıyor. Bu tarz programlar, genellikle **Q** tuşuyla durduruluyor. Bazılarıysa kendine özel çıkış yöntemleri bulunduruyor.
- **Ctrl + D** kısayolu ile, ayrıca **exit** veya **logout** komutu ile terminali kapatabilirsiniz. Eğer bir oturum açtıysanız, **Ctrl + D** kısayolunu kullandığınızda otomatik **logout** komutunu çalıştırır.

## Terminal Arayüzü

![Terminal Arayüzü](/assets/img/posts/2018/07/terminal-arayüz.png)

Terminalin görüntüsü.

![Terminal Arayüz Elemanları](/assets/img/posts/2018/07/terminal-arayüz-elemanları.png)

Arayüzdeki elemanların neler olduğunu renklerle ayırarak gösterdim.

---

## Shell Komutları

## İlk Komut (echo)

Komutları örneklerken, size yazdığım komutu ve altında koyu renkle çıktısını göstereceğim. Siz de terminalde bunları deneyerek öğrenebilirsiniz. **echo** komutu, bize yazdığımız bir harf, kelime veya cümlenin çıktısını çıktısını verir.

```bash
echo "Merhaba Erdi Uçar!"
```

Çıktı:

> Merhaba Erdi Uçar!

Ayrıca, değişkenlerin çıktısını verir. Aşağıdakiler Shell'in kendisine ait değişkenler. Değişkenler yazılırken başına **$ *dolar*** işareti konuyor. Shell'e ait değişkenleri yazarken büyük harfle belirtiyoruz.

```bash
echo $COLUMNS X $LINES
```

Çıktı:

> 80 X 24

Şimdi kendimiz bir değişken belirleyelim ve **echo** ile çıktısına bakalım.

```bash
erdi="erdiucar.com"
echo $erdi
```

Çıktı:

> erdiucar.com

## Dizinde Gezinmek (ls, cd, ..)

### ls

İngilizce "list" kelimesinin kısaltması. Türkçe'de "liste" anlamına geliyor. Bu komut bize bulunduğumuz dizindeki dosyaları ve klasörleri listeler.

```bash
ls
```

Çıktı:

> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  sözlük.txt  terminal-ikon.png

Mavi renkli olanlar klasör. Eğer "Desktop" klasörünün içinde ne olduğunu görmek istersem sonuna klasör ismini yazmam yeterli.

```bash
ls Desktop
```

Çıktı:

> Oyunlar  istatistik1.pdf  7-alışkanlık.epub  steve-jobs.epub  terminal-ikon.png

Masaüstünde "Oyunlar" isimli 1 adet klasörüm olduğu gözüküyor. Ayrıca Pdf ve epub formatında 3 adet kitap gözüküyor. Son olarak png formatında bir resmim var.

### cd

"Change Directory" nin kısaltması. Yani bu komut dizin değiştirmemizi sağlıyor. Terminali ilk açtığımda **Home** (ev) dizinindeydim. **Home** dizini "~" işaretiyle gösteriliyor. Her terminal açışınızda "~" dizininde olursunuz. Bende bilgisayarımda "~Erowen" klasörü oluyor burası. Sizin bilgisayarınızda, artık bilgisayara ne isim verdiyseniz o isimle olur. **ls** başlığında ilk **ls** komutumla alt dizinleri görmüştüm. Şimdi **cd** ile "Desktop" klasörüne girelim.

```bash
cd Desktop
```

Şu an masaüstündeyim. Artık **ls** yazarsam "Desktop" klasöründeki dosya ve klasörleri listelerim.

```bash
ls
```

Çıktı:

> Oyunlar  istatistik1.pdf  7-alışkanlık.epub  steve-jobs.epub  terminal-ikon.png

Şimdi "Oyunlar" klasörüne girelim ve girerken bu klasördeki oyunları listeleyelim. Bunun için bir yol var:

```bash
cd Oyunlar; ls
```

Çıktı:

> 'The Long Dark.url'

Üstteki komutu yazdığımda, önce "Oyunlar" klasörüne girmiş oldum, sonra içindeki dosyaları listeledim. Bu kadar klasör gezdik. Şimdi bir önceki dizine gitmek istiyorum. Bu durumda **cd ..** komutunu kullanıyoruz. Eğer bir önceki dizine yani "Desktop"'a dönmek istersem bunu yazmam yeterli.

```bash
cd ..
```

Şu an "Desktop" klasöründeyim. Bir kere daha **cd ..** yazarsam, başlangıçtaki dizine yani "~" dizinine dönebilirim. Ama bu durumda 2 kere aynı komutu yazmış olacağım. Aynı şeyi 2 kere yazmanıza gerek yok. Eğer **Home** dizinine ulaşmak istiyorsanız **cd** yazmanız yeterli. Yani üstteki komutu yazmadığımı varsayalım.

```bash
cd
```

Şu an "~" dizinine dönmüş oldum. Şimdi "~" dizininden tek bir komutla "Oyunlar" klasörüne girmek istesem ne yapabilirim? Bunun için **Tab** tuşunu kullanabiliriz. **cd Desktop** yazdığımda **Enter**'a basmadan 2 kere **Tab** tuşuna basarsam bütün yazabileceklerim listelenecek. Yani Oyunlar, Programlar, Kitaplar ve diğer dosyalar. Png ya da kitaplara **cd** komutu ile giremeyiz, çünkü bizim komutumuzla alakasız. Neyse **cd Desktop/o** yazdığımda bir kere **Tab** tuşuna basmamla beraber otomatik olarak **cd Desktop/Oyunlar/** komutu oluşuyor. Çünkü "o" harfiyle otomatik olarak tamamlanabilecek tek bir dosya ismi var, o da "Oyunlar". Sonrasında **Enter'**a basmam yetiyor.

```bash
cd Desktop/Oyunlar
```

Tek bir komutla "Oyunlar" klasörüne girmiş oldum.

## Geçerli dizini öğrenmek (pwd)

**pwd**, "Print Working Directory" nin kısaltılmış hali. Yani bu komutla bulunduğumuz dizini gösteren bir çıktı alabiliyoruz. En son "Oyunlar" klasöründeydim.

```bash
pwd
```

Çıktı:

> /c/Users/Erowen/Desktop/Oyunlar

Gördüğünüz üzere bu komut sayesinde bulunduğumuz konumu görmüş olduk.

## Parametreler ve Ayarlar (ls -a, ls -l, *)

**ls** komutu bize dizindeki tüm dosyaları göstermiyor. Klasörün içinde gizli dosyalar olabilir. Görmek isterseniz **ls -a** yazabilirsiniz. **-a** "all" kelimesinin kısaltması. Yani tümünü göster anlamına geliyor. Mesela, **Wordpress** sitelerde **htaccess** dosyası gizli oluyor. Dosyanın içinde onu da listelemek isterseniz **ls -a** yazmanız gerekiyor. Eğer dosyalar ve klasörler hakkında daha uzun ve detaylı bilgi almak istersem **ls** komutunun yanına **-l** komutunu ekleyebilirim. En son "Oyunlar" klasöründeydim.

```bash
ls -l
```

Çıktı:

> -rw-r--r-- 1 Erowen 197609 222 Kas 19 2016 'The Long Dark.url'

**ls**'in yanına **-l** yazdığımız zaman, yukarıda gördüğünüz gibi dosya veya klasör isimleri dışında, byte olarak boyutlarını ve son düzenlenme tarihini görüyoruz. Dosyamızın ismi 'The Long Dark.url". 222 byte boyutunda ve en son 19 Kasım 2016 tarihinde düzenlenmiş. Eğer belli formatları ya da isimleri listelemek istiyorsak, **\*** komutunu ekleyebiliriz. Mesela "Desktop" klasörüne gideyim ve sadece **epub** formatındaki dosyaları detaylı bir şekilde listeleyelim.

```bash
cd ..
ls -l *.epub
```

Çıktı:

> -rw-r--r-- 1 Erowen 197609 5658701 May  6 23:14 7-alışkanlık.epub
> -rw-r--r-- 1 Erowen 197609 1411521 Nis 19 16:35 steve-jobs.epub

Önce **cd ..** ile "Desktop"a döndüm. Sonrasında **\*** komutuyla bu klasörde sonu **.epub** ile biten dosyaları listelemesini istedim. Sonuç olarak "7-alışkanlık" ve "steve-jobs" isimli epub dosyalarını görmüş oldum. Aynı işlemi en başta **cd ..** yazmadan da yapabilirdim. **ls -l ../\*.epub** yazsam da aynı çıktıyı alacaktım. Çünkü **../** ile zaten bir önceki dizinin yolunu belirtmiş oldum. Eğer dosya isimlerinin sonuna göre değilde dosya isimlerinin başına göre listelemek istersem **\*** komutunu sona yazmam gerekir. Yani tam tersi şekilde işliyor. 7 ile başlayan dosyaları listelemek istersem şöyle yazabilirim.

```bash
ls -l 7*
```

Çıktı:

> -rw-r--r-- 1 Erowen 197609 5658701 May 6 23:14 7-alışkanlık.epub

Gördüğünüz gibi 7 ile başlayan tek bir dosya olduğu için sadece "7-alışkanlık.epub" dosyasını listeledi.

## Dosyaları Organize Etmek (mkdir, mv, cp, cp -r)

### mkdir

"Make Directory"nin kısaltması. Yani klasör oluşturmamızı sağlıyor. "Pdf-Kitaplar" ve "Epub-Kitaplar" isimli iki adet klasör oluşturalım ve masaüstündeki bütün dosya ve klasörleri listeleyelim.

```bash
mkdir "Pdf Kitaplar" "Epub-Kitaplar"; ls
```

Çıktı:

> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  istatistik1.pdf  7-alışkanlık.epub  steve-jobs.epub  terminal-ikon.png

Gördüğünüz gibi masaüstünde "Pdf-Kitaplar" ve "Epub-Kitaplar" isimli iki yeni klasör oluşturduk. Örnekteki gibi eğer birçok klasör oluşturmak istiyorsanız, aralarında bir boşluk bırakarak yazıyorsunuz.

### mv

"Move" kelimesinin kısaltması. Bu komut dosyaların yerlerini değiştirmeye ya da isimlerini değiştirmemize yarıyor. Az önce oluşturduğumuz "Pdf-Kitaplar" ve "Epub-Kitaplar" klasörlerine kitapları taşıyalım.

```bash
mv *.epub Epub-Kitaplar; ls Epub-Kitaplar
```

Çıktı:

> 7-alışkanlık.epub  steve-jobs.epub

Sonu epub ile biten dosyaları, "Epub-Kitaplar" klasörüne taşıdım ve listeledim. Yukarıdaki çıktıda bunu görüyorsunuz. Pdf formatındaki kitapları da aynı şekilde "Pdf-Kitaplar" klasörüne taşıyalım ve listeleyelim.

```bash
mv *.pdf Pdf-Kitaplar; ls Pdf-Kitaplar
```

Çıktı:

> istatistik1.pdf

Ayrıca **mv** komutunu kullanarak dosyaların isimlerini değiştirebilirsiniz. Örnek olarak:

```bash
cd Pdf-Kitaplar
mv istatistik1.pdf istatistik2.pdf; ls
```

Çıktı:

> istatistik2.pdf

"istatistik1.pdf'" dosyasının ismini "istatistik2.pdf" yaptım.

### cp

"Copy"nin kısaltması. Dosyaları ve klasörleri kopyalamaya yarıyor. Örneğin "Epub-Kitaplar" klasörüne girelim ve "7-alışkanlık.epub" dosyasını "7-adet-alışkanlık" ismiyle kopyalayalım. Şu an "Pdf-Kitaplar" klasünde olduğum için "Desktop" klasörüne geri gidip "Epub-Kitaplar" klasörüne gireceğim.

```bash
cd ../Epub-Kitaplar
cp 7-alışkanlık.epub 7-adet-alışkanlık.epub; ls
```

Çıktı:

> 7-adet-alışkanlık.epub  7-alışkanlık.epub  steve-jobs.epub

Şimdi bir klasörü içindekilerle beraber başka klasöre kopyalamaya çalışalım. Bunun için **-r** komutunu **cp** komutunun yanına eklememiz gerekiyor. Örnek olarak "Epub-Kitaplar" klasörünü, içindekilerle beraber "Epub-Kitaplar-2"ye kopyalayalım. Elimizde "Epub-Kitaplar-2" isimli bir klasör yok. Ama oluşturmamız gerekmiyor. Yazacağımız komutla kendiliğinden oluşacak. Önce **cd ..** ile "Desktop"a dönelim. Sonrasında **-r** komutu olmadan kopyalamaya çalışalım ve hata çıktısını görelim.

```bash
cd ..
cp Epub-Kitaplar Epub-Kitaplar-2
```

Çıktı:

> cp: -r not specified; omitting directory 'Epub-Kitaplar'

Gördüğünüz üzere **-r** komutunu yazmadınız diye uyardı. Şimdi **-r** komutunu ekleyerek yazalım.

```bash
cp -r Epub-Kitaplar Epub-Kitaplar-2; ls
```

Çıktı:

> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  terminal-ikon.png

Şimdi bakalım, klasörü içindekilerle beraber kopyalamış mı?

```bash
ls Epub-Kitaplar-2
```

Çıktı:

> 7-adet-alışkanlık.epub  7-alışkanlık.epub  steve-jobs.epub

Evet, içindekilerle beraber başarılı bir şekilde yeni bir dosyaya kopyalamış olduk.

## İndirme (curl)

"See Url" in kısaltması. Web sayfasını görmemizi sağlıyor. Mesela google'ın ana sayfasına bakalım. ![curl redirect](/assets/img/posts/2018/07/curl-redirect.png) Bize "google.com" linkinin "www.google.com" a yönlendirildiğinin bilgisi geliyor. Bu yüzden **curl** komutunu kullanırken, yönlendirmeler olabileceğini dikkate alarak komutun yanına **-L** eklemenizi tavsiye ederim. **-L** komutu, yönlendirmeleri takip etmeyi sağlıyor. Şimdi aynı kodu **-L** ekleyerek yazalım.

```bash
curl -L "http://google.com"
```

Çıktı:

> [HTML çıktısı: Google ana sayfası. Kod çok uzun olduğu için burada gösterilmemiştir.]

Çıktı çok uzun olduğu için tamamını yapıştırmadım buraya. Kısaca, bize Google'ın anasayfasının html kodunu gösteriyor. O halde ben bu kodu **.html** olarak bir dosyaya kaydedebilirim ve nasıl gözüktüğüne bakabilirim. Bunun için gelen bütün kodu kopyalayıp yeni bir **.txt** dosyası oluşturup içine yapıştırabilirim ve **.html** olarak kaydedebilirim. Neyse ki bütün bunlarla uğraşmama gerek yok. **-o** komutunu kullanarak belirlediğimiz isimde bir dosya oluşturup bu kodu indirebiliriz.

```bash
curl -L -o google-anasayfa.html "http://google.com"; ls
```

Çıktı:

> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  google-anasayfa.html  terminal-ikon.png

Masaüstüne "google-anasayfa.html" ismiyle html kodunu indirdim. Bu dosyaya tıkladığım zaman google anasayfasını resimler olmadan aşağıdaki gibi gördüm. ![Google anasayfa .html kodu](/assets/img/posts/2018/07/google-anasayfa.png)

## Dosyaları Görüntüleme (cat, less)

Komutlara girmeden önce internetten bir **.txt** dosyası indirelim. Link:

[https://tinyurl.com/zeyq9vc](https://tinyurl.com/zeyq9vc)

İndirmek için bir önceki başlıktaki bilgilerimizi kullanalım. İçinde birçok sözcük olan bir **txt** dosyası bu. Bu yüzden "sözlük.txt" ismiyle indireceğim. Merak etmeyin virüs değil :) İndirmeden önce sayfayı taratabilirsiniz.

```bash
curl -L -o sözlük.txt "https://tinyurl.com/zeyq9vc"; ls
```

Çıktı:

> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  google-anasayfa.html  sözlük.txt  terminal-ikon.png

Gördüğünüz gibi masaüstüne "sözlük.txt" ismiyle indirdik. Şimdi komutlara geçelim.

### cat

Bu komutu kullanarak, dosyaların içeriğini terminal üzerinde görebiliriz. İndirdiğimiz dosyayı bir açalım bakalım.

```bash
cat sözlük.txt
```

Çıktı:

> tadpole
> tadpole's
> tadpoles
> tads
> taffeta
> taffeta's
> taffies
> ...

O kadar çok sözcük var ki, terminal anca "t" harfinden sonrasını gösterdi. Tabiki bütün sözcükleri yapıştırmadım yukarıya. Bu yüzden sonuna "..." yazdım. Eee ben bu dosyanın içeriğinin tamamını nasıl göreceğim? Hani bu **cat** bize dosyaların içeriğini gösteriyordu? Yarım yamalak oldu bu iş :) Ama böyle durumlarda imdadımıza başka bir komut yetişiyor ;)

### less

Bu komut sayesinde terminalde çok yer kaplayacak dosyaların içeriğini dilediğimiz gibi görebiliriz. Hemen deneyelim.

```bash
less sözlük.txt
```

Çıktı:

> A
> A's
> AA's
> AB's
> ABM's
> AC's
> ACTH's
> AI's
> ...

Çok fazla sözcük olduğundan sonuna "..." yazdım. **Space** tuşu veya **Yukarı-Aşağı Yön** tuşu ile dosyanın tamamını gezebilirsiniz. Ayrıca "**/**" işaretinin yanına aradığınız harf ya da kelimeyi yazarsanız, o harf ya da kelimeyi içeren bütün sözcükleri işaretli olarak görürsünüz. Mesela "ar" yazalım. ![less araması](/assets/img/posts/2018/07/less-arama.png)Programdan çıkmak için **Q** harfine basmanız yeterli.

## Dosya ve Klasörleri kaldırmak (rm, rmdir)

### rm

"Remove" un kısaltması. Bu komutla dosyaları silebilirsiniz. **Uyarı:** Dosya ve klasörleri silerken çok dikkatli olun. Geri dönüşsüz siliyor! Eğer silerken bir uyarı almak istiyorsanız, komutun yanına **-i** komutunu ekleyin. Size silmek istediğinize emin misiniz diye soruyor. Eminseniz "**e**" harfine (evet) veya "**y**" harfine (yes) basıp **Enter** tuşuna basabilirsiniz. "google-anasayfa.html" dosyasıyla işim bitti. Artık silebilirim.

```bash
rm -i google-anasayfa.html; ls
```

Çıktı:

> rm: remove regular file 'curl-redirect.png'?
> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  sözlük.txt  terminal-ikon.png

#### Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  Epub-Kitaplar-2  sözlük.txt  terminal-ikon.png

**-i** komutunu eklediğim için silmek istediğinize emin misiniz diye sordu. "**e**" harfine basarak onayladım ve sonrasında masaüstünü listeledi. Artık bu dosya kalıcı olarak silindi.

### rmdir

"Remove Directory" nin kısaltması. Klasörleri silmeye yarıyor. Fakat şöyle bir durum var. Eğer klasörün içi doluysa **rmdir** komutuyla silemiyorsunuz. Hemen deneyelim.

```bash
rmdir Epub-Kitaplar-2
```

Çıktı:

> rmdir: failed to remove 'Epub-Kitaplar-2': Directory not empty

Uyarıyı gördünüz. Yani bu komutla sadece boş klasörleri silebiliyorsunuz. Eğer klasörü içindekilerle beraber silmek istiyorsanız **rm -r** komutunu kullanmanız gerekiyor. Silme uyarısı almak istiyorsanız komutları birleştirebilirsiniz. Yani **-ir** yazmanız yeterli.

```bash
rm -ir Epub-Kitaplar-2; ls
```

Çıktı:

> rm: descend into directory 'Epub-Kitaplar-2'? e
> rm: remove regular file 'Epub-Kitaplar-2/7-adet-alışkanlık.epub'? e
> rm: remove regular file 'Epub-Kitaplar-2/7-alışkanlık.epub'? e
> rm: remove regular file 'Epub-Kitaplar-2/steve-jobs.epub'? e
> rm: remove directory 'Epub-Kitaplar-2'? e
> Oyunlar  Pdf-Kitaplar  Epub-Kitaplar  sözlük.txt  terminal-ikon.png

Gördüğünüz gibi her silme uyarısını "**e**" yazıp onayladım. Klasör, içindekilerle beraber kalıcı olarak silindi.

## Arama Yapmak (grep, wc)

### grep

grep komutuyla harf ya da kelimelere göre arama yapıp, süzme işlemi yapabiliyorsunuz. Örneğin sözlük.txt dosyasından "erdi" içeren kelimeleri süzelim ve çıktısını alalım.

```bash
grep erdi sözlük.txt
```

Çıktı:

> Ferdinand
> Monteverdi
> Verdi
> gaberdine
> ...

İçinde "erdi" bulunan sözcükleri terminalde sıraladı. Farzedelim çok sayıda kelime var ve tamamını göremedik. Bunun için de çözüm var. O da önceden öğrendiğimiz **less** komutu.

```bash
grep erdi sözlük.txt | less
```

Komuta "**|**" işaretini eklediğiniz zaman, bir programın çıktısını, başka bir programa girdi olarak gönderebiliyorsunuz. Yani **grep** programıyla aldığım çıktıyı, **less** programına göndermiş oldum. Terminalde bana gözükense "erdi" kelimesini içeren bütün kelimelerin **less** programıyla gösterilen hali oldu. Yani son yazdığım komutun sonuçlarını gördüm. "**|**" işaretine **pipe** demişler. Artık boru mu, pipo mu veya düdük mü siz karar verin **: |**

### wc

"Word Count" ın kısaltılmış hali. Bu program bize kaç adet girdi aldığının sonucunu veriyor. "erdi" içeren kaç adet kelime olduğunu öğrenmek istiyorum.

```bash
grep erdi sözlük.txt | wc
```

Çıktı:

> 29      29     317

Soldaki sayı bize kaç satır olduğunu gösteriyor. Ortadaki sayı bize wc'nin aranılan kelimeden kaç tane bulduğunu gösteriyor. Sağdaki sayı ise bu bulunan kelimelerin toplamda kaç byte yer kapladığını gösteriyor. 29 adet "erdi" içeren kelime varmış. Benim için çıktının bu kadar detaylı olmasına gerek yok. Bana aradığım kelimeden kaç tane olduğunu görmek yetecek. Bunun için **wc -l** yazabilirsiniz. Bu sayede sadece kelime adetini göreceğim.

```bash
grep erdi sözlük.txt | wc -l
```

Çıktı:

> 29

Önce **grep** ile "erdi" içeren kelimelerin çıktısını aldık, ama bu çıktıyı görmedik, çünkü "|" komutuyla bu çıktıyı **wc** programına gönderdik. **wc** programı da bize girdinin kaç adet olduğunu saydı ve çıktı olarak bize bu sayıyı gösterdi. **grep** ve **wc** programları bir nevi süzgeç işlevi gördü. Bu süzgeç işini biraz daha abartmaya ne dersiniz?

```bash
curl -L "https://tinyurl.com/zeyq9vc" | grep erdi | wc -l
```

Çıktı:

> 29

Burada önce **curl** ile linkteki bütün kelimelerin çıktısını aldık, **grep** programına gönderdik. Orada "erdi" kelimelerini süzgeçten geçirdik ve **wc** programına teslim ettik. O da bize bu "erdi" içeren kelimeleri saydı ve çıktısını verdi. Vay be! :)

## Shell Başlangıç Ayarları

Shell sadece arayüz programı değil, aynı zamanda bir programlama dili. Shell komutları, içinde programlar barındırıyor. Siz de Shell komutları programlayabilirsiniz.

### .bash\_profile

Mac ve Windows'da .bash_profile dosyası bulunuyor. Linux'te bu dosya yok ama .bashrc dosyası üzerinden bu ayarları yapabilirsiniz. bash_profile, Shell'in açılırken neleri çalıştıracağını belirleyen dosya. Bu dosyayla oynayarak Shell'in açılışını kendiniz için optimize edebilirsiniz. "bash_profile" araması yaparak bu dosyanın hangi dizinde olduğunu bulabilirsiniz. Windows bilgisayarımda şu konumda bulunuyor: C:\Program Files\Git\etc\profile.d

Shell'i açtığım zaman, bana tarihi göstermesini ve selam vermesini sağlayacağım. Dosyayı açıp içine şunları ekliyorum:

```bash
# tarih gösterme
date

# selam verme
echo "Shell'e hoşgeldin Erdi Uçar ;)"
```

"**\#**" işareti olan yerler, yorum satırları. Yani program bu kısımlara bakmıyor. Dosyayı kaydedip terminalden çıkıyorum. Tekrar terminali açtığımda bana tarih gösterdiğini ve selam verdiğini görüyorum.

```text
Tue Jul 10 13:07:12 TSS 2018
Shell'e hoşgeldin Erdi Uçar ;)
```

## Shell Komut Görüntüsü Ayarları

![Shell bashrc ayarı](/assets/img/posts/2018/07/bashrc-standart.png)

Git-bash'i kurduktan sonra terminaldeki komut satırı görüntüsü

Bu kısmın nasıl görüneceğini ayarlayabiliyorsunuz. .bashrc dosyasını aratarak bulun. Bilgisayarımdaki konumu: C:\Program Files\Git\etc

Sonrasında bu siteye girin: [https://bashrcgenerator.com](https://bashrcgenerator.com)Bu site üzerinde dilediğiniz şekilde ayar yapıp, verilen çıktıyı **.bashrc** dosyasına yapıştıracaksınız. Ben şöyle bir ayar yaptım:

![shell bashrcgenerator](/assets/img/posts/2018/07/bashrcgenerator.png)

2 numaralı kısma, 1 numaralı kısımdan dilediğinizi sürükleyip bırakıyorsunuz. 2 numaralı kısımda ise bu sürüklediklerinizin üstüne çift tıklayarak renk ve kalınlık ayarı yapıyorsunuz. 3 numaralı kısımda komut satırının nasıl gözükeceği gösteriliyor. Son olarak istediğiniz komut görüntüsünü elde edince, 4 numaralı kısımdaki kodu kopyalayıp **.bashrc** dosyasının en altına yapıştırıyorsunuz. Kaydedip çıkıyorsunuz. Ben resimdeki gibi ayarladım ve terminalim aşağıdaki gibi oldu. 

![shell bashrc ayarı sonrası](/assets/img/posts/2018/07/shell-bashrc.png)

## Kendi Komutlarınızı Oluşturun (alias)

Shell size kendi komutlarınızı yazabilme imkanı sunuyor. **ls** komutunu bazen **sl** diye yazmanız mümkün. **sl** yazdığınızda da **ls**'in çalışmasını sağlayabilirsiniz. **alias** komutu sayesinde bunu yapabiliyoruz. Hemen deneyelim.

```bash
alias sl='ls'
```

Bu komutu yazdığımda, artık **sl** yazdığımda da **ls** komutu çalışacak. Bu en basit örneğiydi. Bir örnek daha yapalım. **cd ..** komutunu da çok sık kullanıyoruz.

```bash
alias ..='cd ..'
```

Artık **..** yazdığımda **cd ..** komutu çalışacak. Bunun gibi aklınıza gelen birçok komutu kendinize göre ayarlayabilirsiniz. Mesela web server'a ssh bağlantısı yaparken ip adresi yazılıyor. Kendiniz için kısa bir kod tanımlarsanız hızlıca bağlanabilirsiniz. Örnek vereyim:

```bash
ssh root@serverIpAdresi
```

Bu kodla server bağlantısı kuruyorsunuz diyelim. Ben "Server'a bağlan" cümlesini kısaltıyorum ve **sb** komutu oluşturayım diyorum. Hemen deneyelim.

```bash
alias sb='ssh root@serverIpAdresi'
```

Artık **sb** yazdığım zaman servera bağlanabilirim. **Not:** Komut satırında tanımladığımız komutlar, terminali kapatıncaya kadar geçerli. Eğer kalıcı olmasını istiyorsanız, Windows ve Mac' te **bash\_profile** dosyasına, Linux'te **bashrc** dosyasına alias tanımlayıp kaydetmeniz gerekiyor. Yani yukarıdaki kodu **bash\_profile**'a yazıp kaydettikten sonra her terminal açışımda **sb** yazarak server'a bağlanabilirim.

---

## Daha Fazlası

Shell hakkında daha detaylı bilgiler edinmek için bu kaynaklardan faydalanabilirsiniz: [The Bash Academy](https://www.bash.academy/)[Bash Beginners Guide](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/)[Bash Programming HOWTO](https://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)[Regexr — Learn Regular Expressions](https://regexr.com/)Ayrıca şu komutların ne işe yaradığını da araştırabilirsiniz: **man**, **sudo**, **chmod**, **ln**, **touch**, **diff**, **telnet**.

## Kaynaklar

Bu yazıyı hazırlarken genel olarak Udacity' nin "Shell Workshop" ve "Linux Command Line Basics" kursundan faydalandım. Ayrıca Harvard'ın CS50 dersinin "Command Line" videosunu kullandım. Bazı eklemeleri de, kendi bilgilerimi kullanarak yaptım. [Udacity - Workshop](https://www.udacity.com/course/shell-workshop--ud206)[Udacity - Linux Command Line Basics](https://www.udacity.com/course/linux-command-line-basics--ud595)[Harvard CS50 - Command Line](https://www.youtube.com/embed/BnJ013X02b8?autoplay=1&rel=0)

---

Diğer yazılarımı incelemek için tıklayın => [Erdi Uçar](https://www.erdiucar.com "Erdi Uçar")
