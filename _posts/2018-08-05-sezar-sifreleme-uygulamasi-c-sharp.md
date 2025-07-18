---
title: 'Sezar Şifreleme Uygulaması (C#)'
date: '2018-08-05T20:56:22+03:00'
description: Sezar şifreleme yöntemi, Gaius Julius Caesar tarafından kullanılmıştır.
  Bu yazımda, Sezar şifreleme yöntemini kullanarak hazırladığım uygulamayı paylaştım.
layout: post
permalink: /sezar-sifreleme-uygulamasi-c-sharp/
image: /assets/img/posts/2018/08/sezar-şifreleme-825x510.png
categories:
    - Programlama
tags:
    - sezar algoritması
    - sezar şifreleme algoritması
    - sezar şifreleme programı
    - sezar şifreleme yöntemi
    - sezar şifresi
---

## Gaius Julius Caesar

Gaius Julius Caesar, milattan önce 100-44 yılları arasında Roma İmparatorluğu'nda yaşamış bir general ve diktatördür. Diplomatik yazılar yazmada çok yetenekliymiş. Ayrıca gizli yazışmaları çok severmiş. **Sezar şifreleme** metodunu, Galya Seferi sırasında Roma'da bulunan dost ve meslektaşlarıyla olan yazışmalarında kullanmış. Çünkü, bu yazılar Roma'ya döndüğünde gerçekleştireceği politik entrikanın planlarını içeriyormuş. ![Gaius Julius Caesar](/assets/img/posts/2018/08/gaius-julius-caesar.jpg)
Gaius Julius Caesar (M.Ö 100-44)

## Sezar Şifreleme Algoritması

Detaylara girmeden önce programın nasıl çalıştığını gösterdiğim YouTube videosunu izleyebilirsiniz:

[![Sezar Şifreleme Uygulaması - C#](https://img.youtube.com/vi/jX6d1NVaZ5w/hqdefault.jpg)](https://www.youtube.com/watch?v=jX6d1NVaZ5w)

👉 [YouTube'da İzle](https://www.youtube.com/watch?v=jX6d1NVaZ5w)

**Not:** *Bu programda İngiliz alfabesini kullanıyorum. Çünkü programı kodlarken ASCII tablosunu kullandım. Ayrıca kullandığım bir fonksiyon, Türkçe harfleri alfabeden saymıyor.*

Sezar şifreleme algoritması, alfabetik düzenin basitçe kaydırılmasından ibaret. Alfabetik düzenin ne kadar kaydırılacağı en baştan belirleniyor. Yani, baştan bir anahtar sayı belirlemek gerekiyor. Eğer anahtarın varsa kapıyı rahatça açıyorsun. Anahtar sayımız 3 olsun diyelim. Yazılan harften 3 sonraki harf bizim şifrelenmiş harfimiz oluyor. Örneğin **B** harfinden 3 sonraki harf **E** harfi (B-C-D-**E**). Şifreli metinde **B** yerine **E** yazacağız. Alfabe bittiğinde ne yapacağım diye sorabilirsiniz. Cevabı basit. Alfabenin başına döneceksiniz. **Z** harfine 3 eklediğimde (Z-A-B-**C**), **C** harfine ulaşıyorum.

![Sezar Şifreleme Algoritması](/assets/img/posts/2018/08/sezar-şifreleme-algoritması.png)

### Örnek tablo ("erdi" kelimesinin anahtar sayıyla (1) şifrelenmesi)

| Düz Metin | e | r | d | i |
|---|---|---|---|---|
| + Anahtar | 1 | 1 | 1 | 1 |
| Şifreli Metin | f | s | e | j |

Son olarak Sezar şifreleme algoritmasını bir cümle için deneyelim. Anahtar sayımız 9 olsun. "Yarın sabah 4'te düşman birliğine baskın düzenleceğiz" cümlesine Sezar Şifreleme algoritmasını uyguladığımda, cümlenin şifrelenmiş hali "Hjaıw bjkjq 4'cn müşvjw kraurğrwn kjbtıw müinwunhnlnğri" oluyor (Türkçe karakterler yukarıda yazdığım sebeplerden ötürü olduğu gibi kalıyor). Şifreli metni deşifre etmek için tek yapmanız gereken alfabeyi 9 geri kaydırmak. Sezar şifreleme algoritmasının 25 potansiyel şifresi var (İngiliz alfabesi 26 harf olduğu için). Bu yüzden bu şifreleme sistemi çok güvenli değil. Sezar şifresinin kullanıldığından şüphelenen bir şifre analizcisinin yapması gereken tek şey, 25 olası anahtarı denemek. Tabi şifreyi zorlaştırmak yine sizin elinizde. Ben, programı size anlattığım en basit haliyle yazdım. Mesela şifreyi karmaşıklaştırmak için alfabeye özel karakterler ekleyebilirsiniz. Ya da 2 harfte bir şifreleme yapabilirsiniz. Boşlukları kaldırabilirsiniz veya boşlukları belirleyecek bir sembol koyabilirsiniz. Kısacası tamamen sizin hayal gücünüze kalmış ;)

### Şifrelenen harfin alfabedeki sırası

Şifrelenen harfin alfabedeki sırası = (Şifrelenecek harfin alfabedeki sırası + Anahtar sayı) mod 26

"mod", Modulo işlemi demek. Yani bir sayının başka bir sayıya bölümünden kalan anlamına geliyor. Programlamada `%` işareti Modulo alma işlevi görüyor. Formülde mod 26 olmasının sebebi, İngiliz alfabesinin 26 harf olması.

Hemen bir örnek yapalım:

**Not:** A harfinin alfabedeki sırasını 0 olarak varsaydım. Çünkü programı yazarken kullanacağım formülde buna göre hesap yapılıyor.

Şifrelenecek harf = A (Alfabedeki sırası 0)
Anahtar sayı = 2
Şifrelenen harfin alfabedeki sırası = (0 + 2) mod 26
Şifrelenen harfin alfabedeki sırası = 2 mod 26
Şifrelenen harfin alfabedeki sırası = 2 (**C** harfi)

| 0 | 1 | 2 |
|---|---|---|
| A | B | **C** |

---

Şimdi aynı formülü **Z** harfi için deneyelim:

Şifrelenecek harf = Z (Alfabedeki sırası 25 - A harfi 0 olduğu için Z harfi 25 oluyor)
Anahtar sayı = 2
Şifrelenen harfin alfabedeki sırası = (25 + 2) mod 26
Şifrelenen harfin alfabedeki sırası = 27 mod 26
Şifrelenen harfin alfabedeki sırası = 1 (**B** harfi)

| 25 | 0 | 1 |
|---|---|---|
| Z | A | **B** |

## Sezar Şifreleme Formülünün ASCII Tablosuna Uyarlanması

Şifrelenecek harfin alfabedeki sırasını öğrenmenin kodla ilgili kısmına geleyim. Başta belirttiğim üzere programda ASCII tablosunu temel alarak kodlama yaptım. Hemen ASCII tablosunu inceleyelim.

![ASCII Tablosu](/assets/img/posts/2018/08/ASCII-tablosu.png)

Her karakterin, ondalık sayı sisteminde (Decimal) bir karşılığı var. Mesela büyük "A" harfinin Decimal karşılığı 65. Küçük harf "a" harfinin Decimal karşılığı 97.

Büyük harfler tabloda 65. sırada başlıyor. Küçük harfler 97. sırada başlıyor. Yukarıda bahsettiğim formülü ASCII tablosuna uyarlamak gerekiyor.

### String değişkenler

Programlamada **char** değişkenler, ASCII tablosunu kullanıyor. **char** değişkenlerin ondalık sayı (Decimal) karşılıklarını kullanarak matematiksel işlemler yapabiliyorsunuz. İşlem sonucunda elde ettiğiniz sayıyı tekrar karaktere (**char**) çevirebiliyorsunuz. Kullanıcıdan şifrelenecek yazıyı alınca bunu **string** değişkenlere atıyoruz. **string** değişkenler aslında karakterlerin sırayla listelenmesinden ibaret. Örneğin "hello" kelimesini bir string değişkene atadığımızda şu şekilde listeleniyor:

| 0 | 1 | 2 | 3 | 4 |
|---|---|---|---|---|
| h | e | l | l | o |

Sayılar her karakterin liste sırasını gösteriyor. Kullanıcıdan bir kelime aldığımda **string** değişkenine atadığım için, her harfin tek tek kontrolünü sağlamak adına for döngüsü kullanıyorum. Kısaca özetlemem gerekirse:

1. Kullanıcıdan şifrelenmesini istediği metni alıyorum.
2. Bu metni oluşturduğum string değişkenine atıyorum.
3. Bu değişkenin toplamda kaç karakter içerdiğine bakıyorum.
4. Karakter sayısı kadar for döngüsü oluşturuyorum.
5. Her karakteri döngü sayesinde tek tek formülle şifreliyorum ve bu şifreli karakterleri başka bir string değişkenine atıyorum.
6. Döngü bitince, şifrelenmiş metni içeren string değişkenini ekranda yazdırıyorum.

### Formül

Şimdi önceki başlıkta gösterdiğim formülü, ASCII tablosundaki ondalık sayı değerlerini kullanarak nasıl kullanacağımıza bakalım. ASCII tablosunu incelediğimizde büyük harflerin 65. sırada başladığını görüyoruz. Küçük harflerse 97. sırada başlıyor. Büyük harfler için şifrelenecek harfin alfabedeki sırasını şu şekilde öğreniyoruz:

#### Şifrelenecek harfin alfabedeki sırası = Harfin ASCII decimal karşılığı - 65

Küçük harfler içinse şu şekilde öğreniyoruz:

#### Şifrelenecek harfin alfabedeki sırası = Harfin ASCII decimal karşılığı - 97

---

Şimdi **Z** harfi için formülü uygulayalım. Harf büyük olduğu için 65 çıkaracağız. Z harfinin ASCII decimal karşılığı 90. Anahtar sayımızda 2 olsun yukarıdaki gibi.

#### Şifrelenen harfin alfabedeki sırası = (Şifrelenecek harfin alfabedeki sırası + Anahtar sayı) mod 26

Şifrelenecek harfin alfabedeki sırası = Harfin ASCII decimal karşılığı - 65 = 90 - 65 = 25
Şifrelenen harfin alfabedeki sırası = (25 + 2) mod 26
Şifrelenen harfin alfabedeki sırası = 27 mod 26
Şifrelenen harfin alfabedeki sırası = 1 (**B** harfi)

Geriye tek bir adım kaldı. O da çıkan sayıyı 65 ile toplamak. Bu sayede **B** harfinin ASCII tablosundaki karşılığını elde etmiş olacağız.

**Şifrelenen harfin ASCII tablosundaki decimal karşılığı = 1 + 65 = 66** (Yani **B** harfi)

---

Şifreli bir harfi deşifre etmek isterseniz formülde şu değişikliği yapmak gerekiyor.

#### Deşifre edilen harfin alfabedeki sırası = (Deşifre edilecek harfin alfabedeki sırası - Anahtar sayı) mod 26

## Sezar Şifreleme Uygulamasının Kodları

Programı Visual Studio ortamında Windows Forms Uygulaması olarak yazdım. Dil olarak C# kullandım. Bir görsel arayüz hazırladım. Bu görsel arayüzle hem bir metni şifreleyebiliyor hem de deşifre edebiliyorsunuz. Uygulamanın arayüz ekranı:

![Sezar şifreleme uygulamasının arayüz ekranı](/assets/img/posts/2018/08/sezar-şifreleme-uygulama-ekranı.png)

### Sezar Şifreleme ve Deşifre Etme Sınıfının Kodları

Sınıfın kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/CaesarCipher/CaesarCipher/CaesarCipher.cs).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace CaesarCipher
{
    public class CaesarCipher
    {
        // Kullanıcının yazdığı anahtar sayı
        private byte anahtar_sayi;

        // Kullanıcının yazdığı yazı
        private string kullanici_yazi;

        // Şifrelenen ya da deşifre edilen yazı
        private string sifre_yazi;

        // Kurucu metod yazdım. Sınıfın nesnesini oluştururken kullanıcıdan anahtar sayı ve şifre-deşifre edilecek yazıyı alıyorum
        public CaesarCipher(byte anahtar_sayi, string sifre_yazi)
        {
            this.anahtar_sayi = anahtar_sayi;
            this.kullanici_yazi = sifre_yazi;
        }

        // ASCII tablosu kullanarak şifreleme yaptığım için, Türkçe karakterleri kontrol etmek adına bool fonksiyon yazıyorum
        private bool TurkceMi(char karakter)
        {
            if (karakter == 'ç' || karakter == 'Ç' || karakter == 'ğ' || karakter == 'Ğ' || karakter == 'ı' || karakter == 'İ' || karakter == 'ö' || karakter == 'Ö' || karakter == 'ş' || karakter == 'Ş' || karakter == 'ü' || karakter == 'Ü')
            {
                return true;
            }
            else
            {
                return false;
            }
        }

        // "Sifrele" metodunu kullanarak yazının şifrelenmiş halini gönderiyorum
        public string Sifrele()
        {
            // Metod her çalıştırıldığında sifre_yazi değişkenini boş hale getiriyorum
            sifre_yazi = "";

            for (int i = 0, s = kullanici_yazi.Length; i < s; i++)
            {
                // Eğer karakterler harf ise ve Türkçe karakter değilse Sezar şifreleme formülü uygulanıyor
                if (char.IsLetter(kullanici_yazi[i]) && !TurkceMi(kullanici_yazi[i]))
                {
                    // Sezar formülü için integer değişken oluşturuyorum
                    int formul;

                    // Karakter büyük harfse formül bu şekilde oluyor
                    if (char.IsUpper(kullanici_yazi[i]))
                    {
                        formul = ((kullanici_yazi[i] - 65) + anahtar_sayi) % 26;
                        sifre_yazi += (char)(formul + 65);
                    }
                    // Karakter küçük harfse formül bu şekilde oluyor
                    else
                    {
                        formul = ((kullanici_yazi[i] - 97) + anahtar_sayi) % 26;
                        sifre_yazi += (char)(formul + 97);
                    }
                }
                // Eğer karakterler harf değilse ve Türkçe ise, olduğu gibi sifre_yazi değişkenine aktarılıyor
                else
                {
                    sifre_yazi += kullanici_yazi[i];
                }
            }

            // Şifrelenmiş yazıyı gönderiyorum
            return sifre_yazi;
        }

        // "DesifreEt" metodu kullanarak yazının deşifre edilmiş halini gönderiyorum
        public string DesifreEt()
        {
            // Metod her çalıştırıldığında sifre_yazi değişkenini boş hale getiriyorum
            sifre_yazi = "";

            for (int i = 0, s = kullanici_yazi.Length; i < s; i++)
            {
                // Eğer karakterler harf ise ve Türkçe karakter değilse Sezar şifreleme formülü uygulanıyor
                if (char.IsLetter(kullanici_yazi[i]) && !TurkceMi(kullanici_yazi[i]))
                {
                    // Sezar formülü için integer değişken oluşturuyorum
                    int formul;

                    // Karakter büyük harfse formül bu şekilde oluyor
                    if (char.IsUpper(kullanici_yazi[i]))
                    {
                        formul = ((kullanici_yazi[i] - 65) - anahtar_sayi) % 26;

                        if (formul < 0)
                        {
                            formul += 26;
                        }

                        sifre_yazi += (char)(formul + 65);
                    }
                    // Karakter küçük harfse formül bu şekilde oluyor
                    else
                    {
                        formul = ((kullanici_yazi[i] - 97) - anahtar_sayi) % 26;

                        if (formul < 0)
                        {
                            formul += 26;
                        }

                        sifre_yazi += (char)(formul + 97);
                    }
                }
                // Eğer karakterler harf değilse ve Türkçe ise, olduğu gibi sifre_yazi değişkenine aktarılıyor
                else
                {
                    sifre_yazi += kullanici_yazi[i];
                }
            }

            // Deşifre edilmiş yazıyı gönderiyorum
            return sifre_yazi;
        }
    }
}
```

### Sezar Şifreleme Ekranının Kodları

Şifreleme ekranının kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/CaesarCipher/CaesarCipher/SezarSifreleme.cs).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Text.RegularExpressions;
using System.Threading;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace CaesarCipher
{
    public partial class SezarSifreleme : Form
    {
        // Program açıldığında ilk burası çalışıyor
        public SezarSifreleme()
        {
            InitializeComponent();

            // Program açıldığında hızlıca yazmaya başlamak için en üstteki textbox'ı seçiyorum
            txtAnahtarSayi.Select();
        }

        // "Onayla" butonuna basılınca program çalışıyor
        private void buton1_Click(object sender, EventArgs e)
        {
            // Eğer textbox'lar boş değilse program başlıyor
            if (txtAnahtarSayi.Text != "" && txtYaziSifre.Text != "")
            {
                // Anahtar sayı olarak byte girilmediğinde program hata vereceği için, programın geri kalanını try içine yazdım
                try
                {
                    // Yazdığım sınıftan bir nesne oluşturuyorum. Eğer anahtar sayı byte'a çevrilirken hata verirse program catch'e atlıyor
                    CaesarCipher sezar = new CaesarCipher(byte.Parse(txtAnahtarSayi.Text), txtYaziSifre.Text);

                    // Nesnenin "Sifrele" metodunu kullanarak yazıyı şifreliyorum ve textbox'a yazdırıyorum.
                    txtSifrelenenYazi.Text = sezar.Sifrele();
                }
                // Eğer girilen değer byte değilse ekrana uyarı mesajı yazdırıyorum
                catch
                {
                    MessageBox.Show("Lütfen anahtar sayıya 0 ile 255 arasında bir değer giriniz.");
                }
            }
            // Eğer kutular boşsa ekrana uyarı mesajı yazdırıyorum
            else
            {
                MessageBox.Show("Lütfen kutuları boş bırakmayınız.");
            }
        }

        // "Temizle" butonuna basılınca tüm textbox'ların içini temizliyorum
        private void buton2_Click(object sender, EventArgs e)
        {
            txtAnahtarSayi.Clear();
            txtYaziSifre.Clear();
            txtSifrelenenYazi.Clear();
        }

        // Menüde "Şifre Çöz"e tıklanırsa, bu formu gizleyip 2. formu (Şifre Çöz) gösteriyorum
        private void şifreÇözToolStripMenuItem_Click(object sender, EventArgs e)
        {
            SezarSifreCozucu form2 = new SezarSifreCozucu();
            this.Visible = false;
            form2.Show();
        }

        // "Programdan Çık" yazısına tıklanınca program kapanıyor
        private void programdanÇıkToolStripMenuItem_Click(object sender, EventArgs e)
        {
            Application.Exit();
        }
    }
}
```

### Sezar Deşifre Ekranının Kodları

Buradaki tek fark, "Sifrele" metodu yerine "DesifreEt" metodunu kullanmam. Deşifre ekranının kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/CaesarCipher/CaesarCipher/SezarSifreCozucu.cs).

```csharp
CaesarCipher sezar = new CaesarCipher(byte.Parse(txtAnahtarSayi.Text), txtYaziSifre.Text);

// Nesnenin "DesifreEt" metodunu kullanarak yazıyı deşifre ediyorum ve textbox'a yazdırıyorum.
txtDesifreEdilenYazi.Text = sezar.DesifreEt();
```

## Yararlandığım Kaynaklar

1. Şifreler Kitabı - Paul Lunde
2. [Harvard CS50 - Introduction to Computer Science](https://www.edx.org/course/cs50s-introduction-computer-science-harvardx-cs50x)

---

Uygulamayı indirmek için tıklayın (CaesarCipher adlı klasör) => [Github](https://github.com/erdiucar/C-Sharp-Windows-Forms)

Vigenere şifreleme üzerine yazdığım yazıyı incelemek için tıklayın => [Vigenere Şifreleme Programı](https://www.erdiucar.com/vigenere-sifreleme-programi-c-sharp/)

Diğer yazılarımı incelemek için tıklayın => [Erdi Uçar](https://www.erdiucar.com)
