---
title: 'Palindrom Denetleyicisi (JavaScript)'
date: 2019-03-05 11:45:23 +0300
description: Bu yazımda girilen kelime, sayı veya cümlenin palindrom olup olmadığını
  denetleyen programın kodlarını paylaştım. Programı JavaScript ile yazdım.
permalink: /palindrom-denetleyicisi-javascript/
image: /assets/img/posts/2019/03/palindrom-denetleyicisi-skyrim-825x510.png
categories: [Programlama]
tags: [ejderha dili, javascript, palindrom, palindrom denetleyicisi, palindrom nedir, skyrim]
---

## Palindrom Nedir?

Bir kelime, sayı veya cümlenin tersten okunuşunun da aynı olmasına **palindrom** deniyor. "kaçak", "ama", "2332" gibi sayı ve kelimeler palindroma örnek olarak gösterilebilir.

![Palindrom nedir](/assets/img/posts/2019/03/Palindrom-nedir.png)

## Palindrom Denetleyicisinin Kodları

Eğer girdi palindrom ise "true", değilse "false" döndüren bir program yazdım. Kodları aşağıda ve [github](https://github.com/erdiucar/palindrome_checker) sayfamda paylaştım.

```javascript
// Is string alpha numeric and char
function isAlphaNumeric(str) {
  /* [a-z0-9] a or b or c or ...z or 0 or 1 or ... 9 /i case-insensitive */
  return str.length === 1 && /[a-z0-9]/i.test(str);
}
// Palindrome checker function
function palindrome(str) {
  // Create an empty string
  let changedStr = '';
  // Add the alpha numeric characters to changedStr variable
  for (let i = 0; i < str.length; i += 1) {
    const element = str[i];
    // Change the char to lower case
    if (isAlphaNumeric(element)) {
      changedStr += element.toLowerCase();
    }
  }
  // Reverse the changed string
  const reversedStr = changedStr
    .split('')
    .reverse()
    .join('');
  // Check normal and reversed string for equality. If they are equal, return true
  if (changedStr === reversedStr) {
    return true;
  }
  return false;
}
// Try it
console.log(palindrome('HAH'));
```

## Ejderha Dili

İçerik görselindeki "HAH" kelimesinin palindrom olduğunu farketmişsinizdir. Eğer *The Elder Scrolls V: Skyrim* oyununu oynadıysanız, muhtemelen ejderha dilinden haberdarsınızdır. "HAH", ejderha dilinde "akıl" anlamına geliyor. Konuyla uyumlu bir görsel hazırlamak istedim. Aklıma bu geldi. :) Eğer ejderha dili hakkında daha fazla bilgi edinmek isterseniz şu [sayfayı](https://www.thuum.org/learn/) inceleyebilirsiniz.
