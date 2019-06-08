# Faydalı Bilgiler <!-- omit in toc -->

## içerikler <!-- omit in toc -->

- [Eğitmen Bilgileri](#e%C4%9Fitmen-bilgileri)
- [CV Hazırlama](#cv-haz%C4%B1rlama)
- [Aksisc Anketlerini Otomatik Dolduran Script](#aksisc-anketlerini-otomatik-dolduran-script)
- [Yaz Okulu](#yaz-okulu)
- [Yatay Geçiş Notları](#yatay-ge%C3%A7i%C5%9F-notlar%C4%B1)
  - [İTÜ'ye Yatay Geçiş](#i%CC%87t%C3%BCye-yatay-ge%C3%A7i%C5%9F)

## Eğitmen Bilgileri

| Eğitmen         | İletişim                 |
| --------------- | ------------------------ |
| Özgür Can Turna | ozcantur@istanbul.edu.tr |

## CV Hazırlama

- CV'ni tasarım sitesi olan [canva][Canva]'dan hazırlayabilirsin

## Aksisc Anketlerini Otomatik Dolduran Script

- [Aksisc](https://aksis.istanbulc.edu.tr/) -> [OBS](http://obs.istanbulc.edu.tr/) -> Öğrenim Bilgileri -> [Sınav Sonuçları](http://obs.istanbulc.edu.tr/OgrenimBilgileri/SinavSonuclariVeNotlar/Index) kısmına gelin.
- Sağ tıklayıp '**Sayfa Kaynağını Görüntüle**' / '**Inspect**' seçeneğini seçin.
- Bu seçenekler yoksa **F12** tuşuna basabilirsiniz.
- Çıkan ekrandan '**Console**' kısmını seçin.
- Konsola altta verdiğim kodu yapıştırın.

```js
for(let i=0; i<$(".btn-danger").length; i++){
    setTimeout(function(){
        $(".btn-danger:eq(0)").click();
        setTimeout(function(){
            $('.panel-body input[type=radio]:nth-child(5)').prop('checked',true);
            $('#soru_CevapMetin').val('skip');
            $(".panel-footer > a").click();
        }, 2000);
    }, 5000*i);
}
```

## Yaz Okulu

| Okul        | Açıklanma Tarihi |
| ----------- | ---------------- |
| Marmara Üni | 26 Haziran 2019  |

## Yatay Geçiş Notları

### İTÜ'ye Yatay Geçiş

- [Yatay geçiş süreci][Yatay geçiş Süreci - İTÜ]
- [Çalışma yeri](http://www.testatolyesi.com/download_1_18.htm)

> Türkçe veya %30 İngilizce programlarından 5.yarıyıl için %100 İngilizce programlarına  yatay geçiş yapılamaz.

[Canva]: https://www.canva.com/
[Yatay geçiş Süreci - İTÜ]: http://www.sis.itu.edu.tr/tr/akademik_takvim/takvim2020/ycy_takvim.htm
