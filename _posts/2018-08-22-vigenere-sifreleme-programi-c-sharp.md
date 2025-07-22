---
title: 'Vigenere Şifreleme Programı (C#)'
date: 2018-08-22 21:46:57 +0300
description: Vigenere şifreleme tekniği, bir zamanlar "kırılmaz şifre" diye anılıyordu.
  Yazımda, Vigenere şifreleme tekniğini kullanarak yazdığım programı anlatıyorum.
permalink: /vigenere-sifreleme-programi-c-sharp/
image: /assets/img/posts/2018/08/vigenere-sifreleme-825x510.jpg
categories: [Programlama]
tags: [sezar şifreleme, sezar şifrelemesi, vigenere algoritması, vigenere şifre çözme, vigenere şifreleme tekniği, vigenere şifrelemesi, vigenere tablosu]
---

## Blaise de Vigenère

Blaise de Vigenère, 1523-1596 yılları arasında yaşamış Fransız bir diplomattır. Roma'da görev yaptığı esnada kriptografi ile ilgilenmeye başlamış. O dönemde İtalya, Avrupa şifrebiliminin merkeziymiş. Vigenere emekliliği sırasında çeşitli konular üzerine kitaplar yazmış. Bunlardan birisi *Traictè des Chiffres ou Secrètes Manières d'Escrire* (1586) idi. Kitapta Giovan Battista Bellaso'nun *Tabula Recta (Kademeli Sezar şifreleme sistemi)* şiflemesi dahil, çeşitli kod ve şifreleri incelemiş. Tabula Recta 19. yüzyılda yanlışlıkla **de Vigenere**'e atfedilmiş. Vigenere, Bellaso'nun şifreleme yöntemini daha da geliştirerek kendi **Vigenere şifreleme** yöntemini oluşturmuş. Bu yöntemde tabloyu 26x26'ya genişletmiş ve şifreleme için otomatik anahtar sistemini ortaya atmış. Sistem, şifrebilim tarihinde bir dönüm noktası olmuş ve gizli mesaj gönderiminde, özellikle de savaş dönemlerinde çok güvenli bir yol sağlamış. 19. yüzyıl sonuna dek kullanılan bu sistem öyle güvenli görülüyormuş ki *kırılmaz şifre* diye anılıyormuş.

![Blaise de Vigenere (Vigenere Şifreleme)](/assets/img/posts/2018/08/Vigenere.jpg)
_Blaise de Vigenère_

## Vigenere Şifreleme Algoritması

Başlamadan önce programın nasıl çalıştığını gösterdiğim YouTube videosunu izleyebilirsiniz:

{% include embed/youtube.html id='0skRgW0xCMs' %}

Vigenere şifreleme algoritması, Sezar şifreleme algoritmasının geliştirilmiş bir versiyonudur. Eğer sezar şifreleme yöntemini bilmiyorsanız, öncelikle onu öğrenmenizi tavsiye ediyorum. Bir önceki [yazımda](https://www.erdiucar.com/sezar-sifreleme-uygulamasi-c-sharp/) Sezar şifreleme yöntemini anlattım.

**Not:** *Vigenere Şifreleme programında, Sezar şifreleme programındaki gibi ASCII tablosunu kullanıyorum. Bu yüzden Türkçe karakterler işlemiyor.*

Sezar şifreleme yönteminde, anahtar sayı kullanarak alfabeyi ne kadar kaydıracağımızı belirliyorduk. Vigenere şifreleme yönteminde de alfabeyi kaydırıyoruz. Fakat, Sezar şifreleme yönteminden farklı olarak "anahtar sayı" yerine, "anahtar kelime" veya "anahtar metin" kullanıyoruz. Buradaki yöntem, anahtar kelimedeki harfin alfabede kaçıncı sırada olduğuna bakmak üzerine kurulu. Anahtar kelimedeki harf alfabede kaçıncı sıradaysa, alfabeyi o kadar ileri kaydırıyoruz.

Örneğin şifrelenecek harf olarak, **J** harfini kullanalım. Anahtar kelimemizdeki harf ise **E** harfi olsun. **E** harfi alfabede 4. sırada bulunuyor (**A**'nın alfabedeki sırasını 0 olarak varsayıyorum ve türkçe karakterleri hesaba katmıyorum). Bu durumda **J** harfinden 4 sonraki **N** harfi, şifrelenmiş harfimiz oluyor (J-K-L-M-**N**)

![Vigenere şifreleme örneği](/assets/img/posts/2018/08/Vigenere-ornek.jpg)

Vigenere şifrelemede anahtar kelime, şifrelenecek yazı bitene kadar kendini tekrar ediyor. Örneğin "HELLO" kelimesini "ABC" anahtar kelimesiyle şifreleyelim. A harfinin alfabedeki sırası 0, B'nin 1, C'nin 2.

### Örnek tablo ("HELLO" kelimesinin "ABC" anahtar kelimesiyle şifrelenmesi)

| Düz Metin | H | E | L | L | O |
|---|---|---|---|---|---|
| + Anahtar | A | B | C | A | B |
| + Anahtar | 0 | 1 | 2 | 0 | 1 |
| Şifreli Metin | H | F | N | L | P |

Aşağıdaki tablo üzerinden bütün harfleri kontrol edebilirsiniz.

![Vigenere şifreleme tablosu](/assets/img/posts/2018/08/Vigenere-square.png){: .bg-white .p-2 }

### Şifrelenen Harfin Alfabedeki Sıra Numarasını Öğrenmek

Şifrelenen harfin alfabedeki sırası **= (Şifrelenecek harfin alfabedeki sırası + Anahtar kelimedeki harfin alfabedeki sırası) mod 26**

Sezar şifreleme formülünden tek farkı, anahtar sayı yerine anahtar kelimedeki harfin alfabedeki sıra numarasını koymak.

## Vigenere Şifreleme Programının Kodları

Programı Visual Studio ortamında Windows Forms Uygulaması olarak yazdım. Dil olarak C# kullandım. Bir görsel arayüz hazırladım. Bu görsel arayüzle hem bir metni şifreleyebiliyor hem de deşifre edebiliyorsunuz.

![Vigenere Şifreleme Programı Arayüzü](/assets/img/posts/2018/08/vigenere-arayuz.png)

### Vigenere Şifreleme ve Deşifre Etme Sınıfının Kodları

Yazdığım sınıfın kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/VigenereCipher/VigenereCipher/VigenereCipher.cs).

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace VigenereCipher
{
    class VigenereCipher
    {
        // Kullanıcının yazdığı anahtar kelime
        private string anahtar_kelime;

        // Kullanıcının yazdığı anahtar kelimenin karakter sayısı
        private int anahtar_kelime_length;

        // Kullanıcının yazdığı anahtar kelime için sayaç
        private int anahtar_kelime_sayac;

        // Kullanıcının yazdığı yazı
        private string kullanici_yazi;

        // Şifrelenen ya da deşifre edilen yazı
        private string sifre_yazi;

        // Kurucu metod yazdım. Sınıfın nesnesini oluştururken kullanıcıdan anahtar kelime ve şifre-deşifre edilecek yazıyı alıyorum
        public VigenereCipher(string anahtar_kelime, string sifre_yazi)
        {
            this.anahtar_kelime = anahtar_kelime;
            this.kullanici_yazi = sifre_yazi;
            this.anahtar_kelime_length = anahtar_kelime.Length;
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

        // Anahtar kelimenin İngilizce karakterler dışında karakter içerip içermediğini kontrol eden fonksiyon
        public bool AnahtarKelimeAlfabetikMi()
        {
            bool sonuc = true;

            for (int i = 0, s = anahtar_kelime_length; i < s; i++)
            {
                if (char.IsLetter(anahtar_kelime[i]) && !TurkceMi(anahtar_kelime[i]))
                {
                    continue;
                }
                else
                {
                    sonuc = false;
                    break;
                }
            }

            return sonuc;
        }

        // "Sifrele" metodunu kullanarak yazının şifrelenmiş halini gönderiyorum
        public string Sifrele()
        {
            // Metod her çalıştırıldığında sifre_yazi değişkenini boş hale getiriyorum
            sifre_yazi = "";
            anahtar_kelime_sayac = 0;

            for (int i = 0, s = kullanici_yazi.Length; i < s; i++)
            {
                // Eğer karakterler harf ise ve Türkçe karakter değilse Vigenere şifreleme formülü uygulanıyor
                if (char.IsLetter(kullanici_yazi[i]) && !TurkceMi(kullanici_yazi[i]))
                {
                    // Vigenere formülü için integer değişken oluşturuyorum
                    int formul;

                    // Karakter büyük harfse formül bu şekilde oluyor
                    if (char.IsUpper(kullanici_yazi[i]))
                    {
                        formul = ((kullanici_yazi[i] - 65) + (char.ToUpper(anahtar_kelime[anahtar_kelime_sayac % anahtar_kelime_length]) - 65)) % 26;
                        sifre_yazi += (char)(formul + 65);
                        anahtar_kelime_sayac++;
                    }
                    // Karakter küçük harfse formül bu şekilde oluyor
                    else
                    {
                        formul = ((kullanici_yazi[i] - 97) + (char.ToLower(anahtar_kelime[anahtar_kelime_sayac % anahtar_kelime_length]) - 97)) % 26;
                        sifre_yazi += (char)(formul + 97);
                        anahtar_kelime_sayac++;
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
            anahtar_kelime_sayac = 0;

            for (int i = 0, s = kullanici_yazi.Length; i < s; i++)
            {
                // Eğer karakterler harf ise ve Türkçe karakter değilse Vigenere şifreleme formülü uygulanıyor
                if (char.IsLetter(kullanici_yazi[i]) && !TurkceMi(kullanici_yazi[i]))
                {
                    // Vigenere formülü için integer değişken oluşturuyorum
                    int formul;

                    // Karakter büyük harfse formül bu şekilde oluyor
                    if (char.IsUpper(kullanici_yazi[i]))
                    {
                        formul = ((kullanici_yazi[i] - 65) - (char.ToUpper(anahtar_kelime[anahtar_kelime_sayac % anahtar_kelime_length]) - 65)) % 26;

                        if (formul < 0)
                        {
                            formul += 26;
                        }

                        sifre_yazi += (char)(formul + 65);
                        anahtar_kelime_sayac++;
                    }
                    // Karakter küçük harfse formül bu şekilde oluyor
                    else
                    {
                        formul = ((kullanici_yazi[i] - 97) - (char.ToLower(anahtar_kelime[anahtar_kelime_sayac % anahtar_kelime_length]) - 97)) % 26;

                        if (formul < 0)
                        {
                            formul += 26;
                        }

                        sifre_yazi += (char)(formul + 97);
                        anahtar_kelime_sayac++;
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

### Vigenere Şifreleme Ekranının Kodları

Şifreleme ekranının kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/VigenereCipher/VigenereCipher/VigenereSifreleme.cs).

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace VigenereCipher
{
    public partial class VigenereSifreleme : Form
    {
        // Program açıldığında ilk burası çalışıyor
        public VigenereSifreleme()
        {
            InitializeComponent();

            // Program açıldığında hızlıca yazmaya başlamak için en üstteki textbox'ı seçiyorum
            txtAnahtarKelime.Select();
        }

        private void button1_Click(object sender, EventArgs e)
        {
            // Eğer textbox'lar boş değilse program başlıyor
            if (txtAnahtarKelime.Text != "" && txtYaziSifre.Text != "")
            {
                // Yazdığım sınıftan bir nesne oluşturuyorum.
                VigenereCipher vigenere = new VigenereCipher(txtAnahtarKelime.Text, txtYaziSifre.Text);

                // Anahtar kelimenin sadece İngilizce karakterler içerip içermediğine bakıyorum.
                // Sorun varsa uyarı mesajı yazdırıyorum
                if (vigenere.AnahtarKelimeAlfabetikMi())
                {
                    // Nesnenin "Sifrele" metodunu kullanarak yazıyı şifreliyorum ve textbox'a yazdırıyorum.
                    txtSifrelenenYazi.Text = vigenere.Sifrele();
                }
                else
                {
                    MessageBox.Show("Lütfen anahtar kelimeye İngilizce karakter dışında birşey girmeyiniz.");
                }
            }
            // Eğer kutular boşsa ekrana uyarı mesajı yazdırıyorum
            else
            {
                MessageBox.Show("Lütfen kutuları boş bırakmayınız.");
            }
        }

        // "Temizle" butonuna basılınca tüm textbox'ların içini temizliyorum
        private void button2_Click(object sender, EventArgs e)
        {
            txtAnahtarKelime.Clear();
            txtYaziSifre.Clear();
            txtSifrelenenYazi.Clear();
        }

        // Menüde "Şifre Çöz"e tıklanırsa, bu formu gizleyip 2. formu (Şifre Çöz) gösteriyorum
        private void şifreÇözToolStripMenuItem_Click(object sender, EventArgs e)
        {
            VigenereSifreCozucu form2 = new VigenereSifreCozucu();
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

### Vigenere Deşifre Ekranının Kodları

Şifreleme ekranından tek farkı, "Sifrele" metodu yerine "DesifreEt" metodunu kullanmam. Deşifre ekranının kodlarını Github'da incelemek için [tıklayın](https://github.com/erdiucar/C-Sharp-Windows-Forms/blob/master/VigenereCipher/VigenereCipher/VigenereSifreCozucu.cs).

```csharp
// Yazdığım sınıftan bir nesne oluşturuyorum.
VigenereCipher vigenere = new VigenereCipher(txtAnahtarKelime.Text, txtYaziSifre.Text);

// Anahtar kelimenin sadece İngilizce karakterler içerip içermediğine bakıyorum.
// Sorun varsa uyarı mesajı yazdırıyorum
if (vigenere.AnahtarKelimeAlfabetikMi())
{
    // Nesnenin "Sifrele" metodunu kullanarak yazıyı şifreliyorum ve textbox'a yazdırıyorum.
    txtDesifreEdilenYazi.Text = vigenere.DesifreEt();
}
else
{
    MessageBox.Show("Lütfen anahtar kelimeye İngilizce karakter dışında birşey girmeyiniz.");
}
```

## Yararlandığım Kaynaklar

1. Şifreler Kitabı - Paul Lunde
2. [Harvard CS50 - Introduction to Computer Science](https://www.edx.org/course/cs50s-introduction-computer-science-harvardx-cs50x)

---

Uygulamayı indirmek için tıklayın (VigenereCipher adlı klasör) => [Github](https://github.com/erdiucar/C-Sharp-Windows-Forms)

Sezar şifreleme uygulaması yazımı incelemek için tıklayın => [Sezar Şifreleme Uygulaması (C#)](https://www.erdiucar.com/sezar-sifreleme-uygulamasi-c-sharp/)

Diğer yazılarımı incelemek için tıklayın => [Erdi Uçar](https://www.erdiucar.com)
