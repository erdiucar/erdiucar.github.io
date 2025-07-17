---
title: 'Sass Nedir? Sass Nasıl Kullanılır?'
date: '2019-08-27T20:17:36+03:00'
description: Sass, CSS formatına dönüştürülebilen bir biçim şablon dilidir. Bu yazımda
  Sass'ın ne olduğunu ve nasıl kullanıldığını detaylıca anlattım.
layout: post
permalink: /sass-nedir-sass-nasil-kullanilir/
image: /assets/img/posts/2019/08/sass-logo-825x510.png
categories:
    - Programlama
tags:
    - CSS
    - 'css preprocessor'
    - SASS
    - SCSS
---

## Sass Nedir?

*Sass*, CSS formatına dönüştürülebilen bir biçim şablon dilidir. Sass dili CSS'e çok benzemektedir. Sass ile değişken, koşul, döngü, fonksiyon vb. gibi programlamaya özgü yöntemleri CSS içinde kullanabiliyoruz. Sass ile yazılan kodları, derleyerek CSS'e çevirmek gerekiyor. Bunun için birçok yöntem bulunmakta. Konsolda **sass** komutunu kullanarak derleme yapabilirsiniz. Veya Gulp, Webpack vs. kullanarak derleme işleminizi gerçekleştirebilirsiniz. Ben Visual Studio'ya yüklediğim eklentiyi kullanarak derleme işlemini gerçekleştiriyorum.

## Sass Nasıl Kullanılır?

Sass kullanımını örnekleriyle size göstereceğim. Yazıda Visual Studio üzerinden nasıl kullanıldığını anlatacağım. Ayrıca .scss formatını kullanacağım. SCSS, CSS yazar gibi yazmanızı sağlıyor. Daha fazla detay için kendi sitesindeki [şu sayfayı](https://sass-lang.com/guide) inceleyebilirsiniz. Öncelikle Visual Studio'ya, [Web Compiler](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.WebCompiler) eklentisini kurun. Sonrasında proje klasöründe ".scss" formatında bir dosya oluşturun. Bu dosyaya kod yazıp kaydettiğimiz zaman, yüklediğimiz eklenti sayesinde otomatik olarak derleme yapılıyor ve .css, min.css dosyaları oluşturuluyor. Siz, HTML'de CSS dosya yolu olarak bu oluşturulan CSS dosyalarından birini yazın. Şimdi nasıl yazıldığını inceleyelim:

### Değişkenler

```css
$brand-color: red;
h1 {
  color: $brand-color;
}
```

Color parametresine $brand-color değişkenini atadık. Tüm h1 etiketli başlıklar kırmızı renk oldu.

### Mixin

Mixin, Sass kullanırken yazdığımız **fonksiyonlara** verilen isimdir. Kullanımı aşağıdaki gibidir:

```css
@mixin standard-button($background-color) {
  font-size: $button-font-size;
  width: $button-width;
  padding: $button-padding;
  color: $button-text-color;
  background-color: $background-color;
}
@mixin border-radius-vendor($radius) {
  -webkit-border-radius: $radius;
  -moz-border-radius: $radius;
  -ms-border-radius: $radius;
}
.primary-button {
  @include standard-button($brand-color);
  @include border-radius-vendor(20px);
}
```

*.primary-button* sınıfına 2 adet fonksiyon ekledik. Birinde parametre olarak *background-color* ekledik. Diğerinde 20px ekledik.

### İç içe Kullanım

```css
// CSS
nav { }
nav ul { }
// SASS
nav {
  ul { }
}
```

Diğer kullanımı da şu şekilde:

```css
// CSS
nav { }
nav > ul { }
// SASS
nav {
  > ul { }
}
```

*:focus*, *:hover* gibi özellikleri kullanırken başına "&" karakterini ekleyerek yazabilirsiniz:

```css
// CSS
.button {
  background-color: red;
}
.button:hover {
  background-color: blue;
}
// SASS
.button {
  background-color: red;
  &:hover {
    background-color: blue;
  }
}
```

Eğer elinizde "button" ve "button-danger" isimli iki sınıfınız varsa şu şekilde yazabilirsiniz:

```css
// CSS
.button {
  background-color: blue;
}
.button-danger {
  background-color: red;
}
// SASS
.button {
  background-color: blue;
  &-danger {
    background-color: red;
  }
}
```

### Çoklu Stil Dosyaları

Yazdığınız ***Sass*** kodunu parçalara bölebilirsiniz. Aşağıdaki örnekte gördüğünüz gibi değişkenleri ve mixin'leri farklı dosyalara koydum. *style.scss* dosyasının içinde @import ile bu dosyaları gösterdim. Dikkat etmeniz gereken 2 nokta var. Birincisi, çağırdınız dosyaların isimlerinin başına alt çizgi "_" eklemeyi unutmayın. Yani *_variables.scss*, *_mixins.scss* olarak kaydedin. İkincisi, *style.scss* dosyasında @import ile dosyaları gösterirken isimlerini alt çizgisiz yazın.

![Multiple Sass Files](/assets/img/posts/2019/08/multiple-sass-files.png)

### @extend Kullanımı

```css
.button {
  color: wheat;
  text-align: center;
}
.yes {
  @extend .button;
  background-color: green;
}
.no {
  @extend .button;
  background-color: red;
}
.cancel {
  @extend .button;
  background-color: brown;
}
```

HTML içinde butonunun sınıfları içerisine class="button yes" yazmak yerine, sadece class="yes" yazarsak, hem *button*'ın özellikleri, hem de *yes*'in özellikleri olur.

### Yorum Satırları

```css
// Bu şekilde yorum satırı yazabilirsiniz.
/* Ya da bu şekilde yorum yazabilirsiniz. */
```

### Hatalar

@debug ve @warn kullanarak debug veya uyarı mesajı yazdırabilirsiniz.

```css
$brand-color: red;
@debug total width $brand-color;
```

### Matematik İşlemleri

```css
$total-pixel-width: 1000px - 200px;
$number-of-columns: 2 * 2 - 1;
$col-width: $total-pixel-width / $number-of-columns;
.column {
  width: $col-width;
  height: (400px / 2);
}
```

### Liste Fonksiyonları

#### length()

Listenin eleman sayısını döndürür.

```css
$space-delimited-list: 10px 20px 30px 40px;
@debug length is length($space-delimited-list);
```

#### nth()

Listeden istediğiniz sıradaki elemanı döndürür.

```css
$comma-seperated-list: #ffa752, #52ff90, #fd52ff;
@debug 2nd item is nth($comma-seperated-list, 2);
```

#### join()

Listeleri birleştirir.

```css
$space-delimited-list: 10px 20px 30px 40px;
$another-space-delimited-list: 50px 60px 70px 80px;
$joined: join($space-delimited-list, $another-space-delimited-list);
@debug joined list $joined;
```

#### append()

Listeye ekleme yapar.

```css
$comma-seperated-list: #ffa752, #52ff90, #fd52ff;
$comma-seperated-list: append($comma-seperated-list, blue);
@debug appended list $comma-seperated-list;
```

#### index()

Belirtilen elemanın sırasını döndürür.

```css
@debug index of blue index($comma-seperated-list, blue);
```

### Mixin İçinde @content Kullanımı

@content yazdığımız yere, mixin kullanırken eklediğimiz her özellik eklenir. Aşağıda Scss ve CSS karşılaştırmasına bakabilirsiniz.

```css
// SCSS
@mixin screen-media($width) {
  @media screen and (max-width: $width) {
    @content;
  }
}
aside {
  width: 200px;
  float: left;
  background-color: red;
  @include screen-media(400px) {
    display: none;
    visibility: collapse;
  }
  @include screen-media(700px) {
    background-color: green;
  }
}
// CSS
aside {
  width: 200px;
  float: left;
  background-color: red;
}
@media screen and (max-width: 400px) {
  aside {
    display: none;
    visibility: collapse;
  }
}
@media screen and (max-width: 700px) {
  aside {
    background-color: green;
  }
}
```

### Mixin İçinde Çoklu Parametre Kullanımı

C#'taki *params* gibi, mixin'e birden fazla parametre girmek mümkün.

```css
@mixin shadow($shadows...) {
  box-shadow: $shadows;
}
#tile1 {
  @extend .tile;
  background-color: red;
  // pass a single value
  @include shadow(10px 10px 5px black);
}
#tile2 {
  @extend .tile;
  background-color: violet;
  @include shadow(10px 10px 5px black, -10px -10px 10px 5px purple);
}
```

![Params](/assets/img/posts/2019/08/params.png)

### Renk Fonksiyonları

Tüm [renk fonksiyonlarını](https://sass-lang.com/documentation/functions/color) kendi sitesinden inceleyebilirsiniz. Aşağıda *lighten()* ve *darken()* fonksiyonlarını gösterdim.

```css
$root-color: #0099ff;
// Rengi %35 açıklaştırıyor
body {
  background-color: lighten($root-color, 35%);
}
// Rengi %45 koyulaştırıyor
h1 {
  background-color: darken($root-color, 45%);
}
```

### If - Else Kullanımı

Örnekte gördüğünüz gibi parametreye göre değişen bir kod yapısı var.

```css
@mixin mediaQuery($break) {
  $value: map-get($breakpoints, $break);
  @if $break == "lg" {
    @media (min-width: $value) {
      @content;
    }
  } @else {
    @media (max-width: $value) {
      @content;
    }
  }
}
```

### For Döngüsü Kullanımı

Aşağıdaki örnekte 5 adet farklı renkte div'in for döngüsüyle nasıl oluşturulduğunu görüyoruz. Ayrıca @extend kullanımının diğer bir şeklini de (% karakteri) kodlarda görebilirsiniz.

```css
$tile-size: 100px;
%tile {
  width: $tile-size;
  height: $tile-size;
}
@for $i from 1 through 5 {
  #tile-#{$i} {
    @extend %tile;
    background-color: darken(yellow, $i * 5);
  }
}
```

![Sass For Döngüsü](/assets/img/posts/2019/08/sass-for-dongusu.png)

### Each Döngüsü Kullanımı

Each döngüsünün kullanımı, C#'taki foreach döngüsü gibi. Bir listenin elemanlarını döndürmek istediğiniz zaman kullanabilirsiniz.

```css
$tile-size: 100px;
$tile-colors: blue, green, yellow, orange, red;
%tile {
  width: $tile-size;
  height: $tile-size;
}
@each $color in $tile-colors {
  $i: index($tile-colors, $color);
  #tile-#{$i} {
    @extend %tile;
    background-color: $color;
  }
}
```

![Sass Each Döngüsü](/assets/img/posts/2019/08/sass-each-dongusu.png)

### Map Kullanımı

Map, key ve value barındıran bir listedir. Aşağıdaki *$team-colors*, bir map örneğidir. Kodun en altında *map-get()* metodu var. Bu metot ile value döndürülebiliyor.

```css
$tile-size: 100px;
$team-colors: (
  turkey: red,
  australia: orange
);
%tile {
  width: $tile-size;
  height: $tile-size;
}
@each $team, $color in $team-colors {
  ##{$team} {
    @extend %tile;
    background-color: $color;
  }
}
@debug Turkey color is map-get($team-colors, turkey);
```

![Team Colors](/assets/img/posts/2019/08/sass-team-colors.png)

### Nested Properties Kullanımı

font-family, font-size gibi "-" işaretinden öncesi aynı olan özellikler için aşağıdaki gibi tanımlama yapabilirsiniz.

```css
// CSS
body {
  font-family: Arial;
  font-size: 40pt;
  font-weight: bold;
}
// Sass
body {
  font: {
    family: Arial;
    size: 40pt;
    weight: bold;
  }
}
```

## Kaynaklar

Bu yazıyı hazırlarken Pluralsight'ın [Simplifying CSS in Visual Studio With Sass](https://www.pluralsight.com/courses/simplifying-css-visual-studio-sass) isimli kursundan ve Sass'ın kendi [sitesinden](https://sass-lang.com/documentation) faydalandım.

---

Programlama üzerine paylaştığım diğer yazılara bu [linkten](http://erdiucar.local/kategori/programlama/) ulaşabilirsiniz.
