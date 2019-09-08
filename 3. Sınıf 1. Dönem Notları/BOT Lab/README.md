# Bilgisayar Organizasyonu ve Tasarımı Lab 

## Ders Bilgileri

Hocanın hazırlamış olduğu videolar:

- [XILINX ile VHDL PROGRAMLAMA! - Full Adder (Tam Toplayıcı) Tasarımı #1](https://www.youtube.com/watch?v=-SZuTT3xa18)
- [XILINX ile VHDL PROGRAMLAMA! - Full Adder (Tam Toplayıcı) Tasarımı #2](https://www.youtube.com/watch?v=H7jihUQz-Io)
- [XILINX ile VHDL PROGRAMLAMA! - Full Adder (Tam Toplayıcı) Tasarımı #3](https://www.youtube.com/watch?v=Sw5ktjHl1zc)

## Final Hakkında

- Syntax yapılalarını özetlediğim not için [buraya](https://drive.google.com/open?id=1Lwj1DfOjI5fjtEXjytVzUuFdR9wtMz7g) tıklayabilirsin.
- Dalga similasyonu soruları hakkında:
  - Buradaki sorunun B şıkkı üzerine yazılmıştır.
  - İlk adım için:
  - x = 0 y = 1 E = 1
  - b-d = a-c (ki burada arkadaki adım alınır. Yani 1) . x (0)
  - b-d = 0 olarak hesaplanır.
  - a-d = ( b-c (bir önceki hali yani 0) xnor a-c (1) ) . y (1)
  - a-d = (0 xnor 1) . 1
  - a-d = 0
  - z = a-c (1) xnor b-c (0)
  - z = 1 xnor 0
  - z = 0
  - D flip flop için
  - b-c = b-d (yani 0)
  - a-c = a-d (yani 0)
  - (Giriş yaptığı gibi çıkar)
  - Net sonuç
  - a-d = 0
  - a-c = 0
  - b-d = 0
  - b-c = 0
  - z = 0
  - ( Fikir oluşması adına )
