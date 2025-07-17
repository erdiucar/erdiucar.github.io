---
title: 'MVC Nedir? MVC&#8217;nin Avantajları Nelerdir?'
date: '2018-10-25T20:27:22+03:00'
description: MVC (Model View Controller), web tasarımında çok sık kullanılan bir yazılım
  kalıbı veya yazılım sistemidir. Bu yazımda sizlere MVC'yi anlatıyorum.
layout: post
permalink: /mvc-nedir-mvcnin-avantajlari-nelerdir/
image: /assets/img/posts/2018/10/mvc-825x510.png
categories:
  - Programlama
tags:
  - 'asp.net mvc'
  - model-view-controller
  - mvc
  - 'mvc nedir'
---

## MVC (Model-View-Controller)

MVC (Model View Controller), web tasarımında çok sık kullanılan bir yazılım kalıbı veya yazılım sistemidir. Kullanımının temel sebebi, kullanıcıları gereksiz detaylardan uzak tutmak ve uygulamanın veri güvenliğini sağlamaktır. Ayrıca uygulamanın front-end ve back-end kısımlarını birbirinden ayırdığı için geliştiricilere birçok kolaylık sağlar. Uygulamamızdaki her dosyanın kullanıcılar tarafından görülmesini istemeyiz. Model-View-Controller, bize bu konuda oldukça yardımcı olan bir yapıya sahip.

### Model

Model, sitenin önemli verilerinin yaşadığı kısımdır. Kullanıcı arayüzünden bağımsız olarak uygulamanın dinamik veri yapısını temsil eder. Uygulamanın veritabanını, mantığını ve kurallarını yönetmemizi sağlar.

### View

View, kullanıcıların gördüğü kısımdır. Yani uygulamamızda kullanıcıya gösterdiğimiz alanı temsil eder. Html olarak hazırlanan sayfalar View'a örnektir.

### Controller

Controller, uygulamamızda köprü görevi gören kısımdır. Kullanıcıdan (View) gelen isteklere göre veritabanından (Model) verileri alıp, gelen verileri tekrar kullanıcıya (View) gösterebiliriz.

![MVC Nedir](/assets/img/posts/2018/10/mvc-nedir.png)

Bu arada MVC, [ASP.NET](https://www.asp.net/)'e ait bir yazılım kalıbı değil. Microsoft sadece bu sistemi geliştiricilerin kullanımına sunmuş.

## MVC Kullanımının Avantajları

- Teste dayalı uygulama geliştirmeyi kolaylaştırır.
- Katmanlı yapısı sayesinde karışıklığı engeller.
- Uygulama güvenliği konusunda büyük artıları vardır. Dışarıdan ulaşan herkese View kısmı gösterilir.
- Büyük projelerde, projenin denetimini ve yönetimini kolaylaştırır.

---

Bir önceki paylaşımımda bu konuyla ilgili projemi paylaşmıştım. İncelemek isterseniz **[tıklayın](https://www.erdiucar.com/arduino-asp-net-mvc-rgb-led-kontrolu/)**.
