# Hauwei Ders1 <!-- omit in toc -->

Adı sonradan değiştirilmeli 😁

## Yazılım Notları

- `eNSP` Hauwei'nin sunduğu *network* similasyın uygulaması

### *MAC* varken Neden *IP* Adresi Var

- Paket alışverisi *IP* adresi ile yapılmaktadır (layer3)
- Router arasında aktarım yapılırken, Source *MAC* adresi sabit kalarak, Destination *MAC* adresleri değişmektedir
  - Source *MAC*, kaynağın kimliğini tutar
  - Destination *MAC*, paketin gönderileceği kaynağın adresini tutar.
  - *IP*, asıl kaynağın sanal adresini tutar
- Her kaynak bildiği hedefe paketi yollar (gateway yapısı)
  - Bildiği adres olarak ifade edilen *MAC* adresidir

### Layer Özellikleri

| Layer2                                 | Layer3                                                                                 |
| -------------------------------------- | -------------------------------------------------------------------------------------- |
| Aynı *network*'teki haberleşme (local) | Farklı *network*'teki haberlerşme                                                      |
| Modemlerdeki *LAN* portlarının katmanı | Modemdeki *ADSL* portunun katmanı                                                      |
| *Switch* ile gerçekleşir               | *Router* ile gerçekleşir                                                               |
| *MAC* adresleri ile haberleşilir       | Asıl hedefe *IP* adresi ile gidilir, *MAC* adresleri hedefe gidiş sırasında kullanılır |
| *Gateway* olmaz                        | *Gateway* olur                                                                         |

- *Router*, *switch*lerin haberleşmesini sağlar
- *switch*, aynı ağdaki bilgisayarların haberleşmesini sağlar
- *Gateway*, asıl hedefini belirtir ve hedefe giderken başka yerlere gitmesiyle ilgilnemez bilgisi olmaz. (kargo şirkerlerine paket vermek gibi)