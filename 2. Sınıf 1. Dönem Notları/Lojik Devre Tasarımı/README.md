# Lojik Devre Tasarımı 

## Ders Bilgileri

- Alakalı konu olan **Sayısal Tasarım** notlarına [buradan][Sayısal Tasarım - Ege Uni] erişebilirsin.
- **Digital Desing** ek kaynak için [buraya][Digital Design - ITU] bakabilirsin.

## Final için Referanslar

- [Decoders][Decoders]
- [Mux][Mux] (video kaynak için [buraya][Mux - Video])
- Kombinezonsal Devre notları için [buraya][Kombinezonsal Devre]
- [Tümleştirilmiş K.D][Tümleştirilmiş K.D]
- [Ardışıl Lojik Devreler (Flip, Flop, Moore)][Ardışıl Lojik Devreler (Flip Flop / Moore / ...)]
- [A/Synchronized Counter With Load / Clear][A/Synchronized Counter With Load / Clear]

### Durum Diyagramı Açıklamam

> ⚠ Hatalı bilgi içerebilir.

![lojik_state_diagram](../res/lojik_state_diagram.png)
![lojik_state_diagram_answer](../res/lojik_state_diagram_answer.png)

- İlk A B C D istenen durum için tasarlanıyor.
- 101 için A B C D
- A E F G de 010 için tasarlanmış
- A başlangıç değeri oluyor, eğer girdi 0 ise, 010 kontrolü - olacağı için A'dan E ye gidiyor
- Şuan elimizde 0 verisi var Ve E deyiz
- E'de iken 1 verisi girilirse, elimizdeki dizi 01 olacak 010 - araması için uygun
- Bundan dolayı, E'den F'ye ok çiziyoruz
- F de iken, girilen veri 0 ise 010 olacak dizi ve istenen - değere ulaşacağız, o da G oluyor
- F'den G'ye ok çekiyoruz, bir de Z çıktısı değiştiği için G / - 1 yapıyoruz
- A B C E F vs. bunların hepsinin yanında aslında gizli 0 var - (Z nin değeri) a / 0 yani aslında
- 010 için durum diyagramı oluşturduk, aynısını 101 için - yapacağız şimdi
- Burada da ilk veri 1 ilse (101 e uyumlu) B'ye geçiyoruz
- B'de iken 0 girilirse (10 olacak yine uyumlu) C'ye geçiyoruz
- C'de iken 1 girilirse (101 olacak istenen dizi) D / 1 'e - geçiyoruz (Z = 1 olduğu için)
- Buraya kadar ki kısım tamam mı şu an?
- Çünkü, istenen durum dışındaki durum için biraz daha farklı - düşüneceğiz, şu anlık sadece isteneni çizdik
- A kısmını yaptık (A'dan 2 ok çıkıyor) B'ye geçiyorum
- B'de 0 alırsak C oluyor (10 olduğu için) ama 1 alırsak - dizimiz 11 olacak, elimizdeki istenen durumlara bakıyoruz - 101, 010, hangisine daha uyumlu ise ona yönlendreceğiz
- 11, 101'e daha yakın, yani istenen dizinin ilk elemanını - tutuyor 1'i
- İstenen dizimiz A B C D idi. Burada
- 1 -> B
- 10 -> C
- 101 -> D
- ye ok çekeceğiz
- 101'in 1'ine uydupu için, B'den 1 verisi girilirse tekrardan - kendisine ok çekiyoruz
- Şimdi sıra geldi C'den 0 girilirse ne olacağına;
- C'den 0 girilirse dizimiz 100 olacak bu hangisine en uygun - diye bakıyoruz
- 010 'a daha uygun
- İstenen dizimiz A E F G  idi. Burada
- 0 -> E
- 01 -> F
- 010 -> G
- ye ok çekeceğiz
- 100 dizisi ile 010 dizisinde ortak bitler, baştakı 0, yani E - oluyor, C'den 0 girilmesi durumunda E'ye ok çekiyoruz
- C de tamam sıra D'de;
- D'de iken dizimin 101 olacak, sırasıyla inceliyoruz;
- 0 ise;  girilen veri 1 010 olacak bu, fark edildiği üzere - 010 da sağlanmış oluyor bu sebeple 1 girdisi aldığımızda - G'ye gidecek
- 1 ise; girilen veri 101 1 olacak, 1 01'in ilk kısmına uyuyor,-  yani B
- A, B, C, D tamamdır, sıra E'de
- E 'de input 0 ise; girilen veri 0 0 olacak 0 10 'un ilk - verisine uyum sağlıyor, bu sebeple E olacak yani kendisine - ok çekeceğiz
- F için input 1 ise;
- 01 1 olacak 1 01 'in ilk bitine uyuyor, 1 -> B, B ye ok - çekeceğiz
- G için;
- input 1 -> girilen dizi 0 101 olacak 101 de sağlanmış oluyor - bu sebeple D'ye ok çekeceğiz
- G için;
- input = 0 -> dizi : 010 0 olacak 0 10 'ın ilk bitine uyuyor, - yani E'ye ok çekeceğiz
- Hatırlatma ;
- A = başlangıç değeri (değeri yok)
- B = 1 (101 için)
- C = 10 (101 için)
- D = 101 (101 için)
- E = 0 (010 için)
- F = 01 (010 için)
- G = 010 (010 için)
- Diyelim bunları karıştırdınız değerlerini;
- E yi bulmak için A'dan başlayıp okları takip ederek - geliyorsunuz ve inputlar E oluyor
- F'yi unuttuk diyelim;
- A dan 0
- E den 1
- F'teyiz, yani F = 01 (010 için)

[Digital Design - ITU]: https://web.itu.edu.tr/~orssi/dersler/LD/Chap_01.pdf
[Sayısal Tasarım - Ege Uni]: http://tec.ege.edu.tr/dersler/say_tas_ders_notu.pdf
[Decoders]: http://www-ee.ccny.cuny.edu/wwwn/yltian/Courses/EE210/EE210-Lecture11.pdf
[Mux]: http://320volt.com/coklayicilar-veri-seciciler-multiplexers-data-selector/
[Mux - Video]: https://www.youtube.com/watch?v=SQp-r0Rw7zQ
[Kombinezonsal Devre]: http://www.yildiz.edu.tr/~uzun/LDT_PDF/PLDT_05_KombDevreT.pdf
[Tümleştirilmiş K.D]: http://kisi.deu.edu.tr//ozlem.karaca/s04_2.pdf
[Ardışıl Lojik Devreler (Flip Flop / Moore / ...)]: http://www.yildiz.edu.tr/~uzun/LD_PDF/PLDT_06_ArdisilLojikDevre.pdf
[A/Synchronized Counter With Load / Clear]: https://www.tutorialspoint.com/sequential_circuit_design/design_of_mod6_counter_using_load_and_clear.asp
