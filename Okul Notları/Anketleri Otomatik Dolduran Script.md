# Anketleri Otomatik Dolduran Script

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