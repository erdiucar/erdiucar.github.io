---
title: 'Monty Hall Problemi ve Monty Hall Problemi Programı (C#)'
date: '2020-03-01T21:55:00+03:00'
description: Monty Hall problemi, Amerikan TV yarışma programı Let's Make a Deal'a
  dayanır. Bu yazımda, Monty Hall problemini anlattım ve programını paylaştım.
layout: post
permalink: /monty-hall-problemi-ve-monty-hall-problemi-programi/
image: /assets/img/posts/2020/03/monty-hall-problemi-825x510.jpg
categories:
  - Genel
  - Programlama
tags:
  - 'monty hall'
  - 'monty hall problemi'
  - 'monty hall problemi programı'
  - 'monty hall problemi simülasyonu'
  - 'monty hall programı'
  - 'monty hall simülasyonu'
---

**Monty Hall problemi**, Amerikan TV yarışma programı [*Let's Make a Deal*](https://tr.wikipedia.org/wiki/Let%27s_Make_a_Deal?oldformat=true)'a dayanır. Bu problem, adını yarışmayı sunan Monty Hall'dan alır. Öncelikle Monty Hall problemini anlamak için yarışmanın formatını size anlatmak istiyorum.

![Monty Hall Problemi](/assets/img/posts/2020/03/1280px-Monty_open_door.svg_.png)

Yarışmada 3 tane kapı bulunuyor. Kapıların arkasında ne olduğunu göremiyorsunuz. Bu kapıların bir tanesinin arkasında araba bulunuyor. Diğer 2 kapının arkasında ise keçi var. Sunucu sizden bir kapıyı seçmenizi istiyor. Siz kapıyı seçtikten sonra, sunucu sizin seçmediğiniz 2 kapıdan arkasında keçi bulunan bir tanesini açıyor. Ardından size seçtiğiniz kapıyı değiştirmek ister misiniz diye soruyor. Önünüzde açılmamış iki tane kapı var. Arkasında araba olan kapıyı seçerseniz araba sizindir. Siz olsanız en başta seçtiğiniz kapıyı değiştirir misiniz?

İşler burada karışıyor. Kapıyı değiştirseniz de değiştirmeseniz de %50 ihtimalle arabayı kazanacağınızı düşünebilirsiniz. Ama böyle düşünüyorsanız, size yanıldığınızı söylemeliyim.

Problemi en baştan ele alalım ve 1. kapıyı seçtiğinizi varsayalım:

- Eğer araba 1. kapının arkasındaysa, kapıyı değiştirirseniz arabayı *kaybedersiniz.*
- Eğer araba 2. kapının arkasındaysa, kapıyı değiştirirseniz arabayı *kazanırsınız.*
- Eğer araba 3. kapının arkasındaysa, kapıyı değiştirirseniz arabayı *kazanırsınız.*

Yani kapıyı *değiştirmezseniz* tek bir durumda arabayı kazanırsınız. *Değiştirirseniz* iki durumda da arabayı kazanırsınız.

Olayı yüzdeye vurursak:

- Kapıyı değiştirmediğiniz durumda, %33.33 olasılıkla arabayı kazanırsınız.
- Kapıyı değiştirdiğiniz durumdaysa, %66.66 olasılıkla arabayı kazanırsınız.

## Monty Hall Problemi Programı

Monty Hall probleminin olasılıklarını görmek adına bir program yazdım. Siz de bilgisayarınıza kurup deneyebilirsiniz. Aşağıdaki resimde 1000 kere programa katılırsanız, kapıyı değiştirmeme ve değiştirme durumunda arabayı kaç kere kazandığınızı görebilirsiniz. Yukarıda anlattığım gibi sonuçların %33 ve %66'ya ne kadar yakın olduğu ortada.

![Monty Hall Problemi Programı](/assets/img/posts/2020/03/monty-hall-problemi-program.png)

Programı [GitHub sayfamdan](https://github.com/erdiucar/monty_hall_problem) indirebilirsiniz ve detaylarını inceleyebilirsiniz. Aşağıda da Program.cs dosyasını paylaştım.

```csharp
using System;
namespace monty_hall_problem {
    class Program {
        private const int COMPETITION_REPEAT_COUNT = 1000;
        private const int DOORS_COUNT = 3;
        static void Main() {
            try {
                Statistics statistics = new Statistics();
                for (int i = 0; i < COMPETITION_REPEAT_COUNT; i++) {
                    // Start a new competition
                    Competition competition = new Competition(DOORS_COUNT);
                    // If the car is behind the picked door, increase staying wins, else increase changing wins
                    if (competition.Competitor.PickedDoor.Number == competition.Stage.CarDoorNumber)
                        statistics.WinningCountWhenStayOnThePickedDoor++;
                    else
                        statistics.WinningCountWhenChangeThePickedDoor++;
                }
                MontyHallProblemConsole montyHallProblemConsole = new MontyHallProblemConsole(statistics);
                montyHallProblemConsole.WriteStatistics();
            } catch (Exception e) {
                Console.WriteLine("Error: {0}", e.Message);
            }
        }
    }
}
```

---

Daha önceden [programlama üzerine yazdığım yazıları](http://erdiucar.local/kategori/programlama/) da inceleyebilirsiniz.
