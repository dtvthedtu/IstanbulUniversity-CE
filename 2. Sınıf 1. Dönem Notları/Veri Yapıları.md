# Veri Yapıları <!-- omit in toc -->

Bu yazı hala aktarım aşamasındadır, kaynak için [buraya](https://www.yemreak.com/2017/10/veri-yaplar.html) bakabilirsin.

<!-- TOOD Aktarılması tamamlanmadı  
http://yemreak.blogspot.com/2017/10/veri-yaplar.html
-->

> Drive yedeklemesi için [buraya][Yedekleme - Drive] bakabilirsin, ya da aşağıdan indekslenmiş olarak erişebilirsin.

[Yedekleme - Drive]: https://drive.google.com/drive/folders/1CpcnBvY3FQziQJI_UX2mTly-YBT4H09-

## İçerikler <!-- omit in toc -->

- [Ders Notları](#ders-notlar%C4%B1)
- [Sınav Notları](#s%C4%B1nav-notlar%C4%B1)
- [Ders için Kodlarım](#ders-i%C3%A7in-kodlar%C4%B1m)
  - [Stack](#stack)
  - [Queue](#queue)
  - [Linked List](#linked-list)
  - [Double Linked List Açıklama](#double-linked-list-a%C3%A7%C4%B1klama)
  - [Binary Tree](#binary-tree)

## Ders Notları

- Ders notlarına [buradan][Ders Notları] erişebilirsin.
- Derste işlenen slaytları [hocanın kendi sitesinde][Hocanın Sitesi] de bulabilirsin.
- **Fundamental Data Structures** adlı kitabın pdf'ine [buradan][Fundemental Data Structures] erişebilirsin.
- **Data Structures Using C++** adlı kitaba [buradan][Data Structures Using C++] erişebilirsin.
- Algoritma mantığını görselleştiren site için [buraya][Visioalgo] bakabilrsin.
- Prim kruksal vs. slaytı için [buraya](https://issuu.com/jemujan/docs/algoritma_analizi) bakabilirsin.

## Sınav Notları

- Sınav sorularına [buradan][Sınav Soruları] erişebilirsin.

## Ders için Kodlarım

### Stack

```c
#include <stdio.h>
#include <conio.h>
#include <stdlib.h>

/**
 * Yığın yapısı
 * @author Yunus Emre AK
 */
 
typedef struct node{
        int veri;
        struct node * altindaki;        
}Dugum;

/*  Yığın yapısında son giren ilk çıkacağı için "enUst" adında bir düğüm oluşturalım.
 * Oluşturulan bu yığın, üst üste konulan kitaplar gibi düşünülebilir.
 *
 *  
 */
Dugum *enUst = NULL;

// Yığına veri ekleme fonksiyonu.
void push(int veri){
 // İlk kez veri atama işlemi yapılmadan önce yığın düğümü oluşturulur.
 Dugum* yeniDugum;
  
 // Bellek atama işlemini yapıyoruz.
 yeniDugum = (Dugum*)malloc(sizeof(Dugum));
 
 // Veriyi atıyoruz.
 yeniDugum->veri = veri;
  
 /*  Yeni düğüm, enUst olarak ifade ettiğimiz düğümün üstünde olduğu için
  * yeni düğümün altındakini, eski enUst düğüm olarak atıyoruz.
  */
 yeniDugum->altindaki = enUst;
 
 /*  Yeni tanımladığımız düğüm artık en üstte olduğu için yeni düğümü en üste
  * atıyoruz, böylelikle ana düğüm en altta, diğer düğümler üstüne binecek şekilde 
  * veri depolanacak, yapılacak en son "altindaki" işlemi ana düğüme ulaştıracaktır.
  */
 enUst = yeniDugum;
 
}

// Yığından veri çıkarma fonksiyonu.
int pop(){
 /*  İlk olarak yığında veri olup olmadığı kontrol ediyoruz, eğer veri yoksa işlem
  * yapılamaz.
  */
 if(enUst == NULL){
   printf("\nYigin dugume sahip degil, hata!\n");
   
   // Hata kodu olması amaçlı , -1 döndürüyoruz.
  return -1;
 }
  
 // Düğümdeki veriyi geri döndürülecek olan sonuc'a atıyoruz.
 int sonuc = enUst->veri;
  
  /*  En üstteki düğüm silinmeden önce onun için ayrılan belleği serbest bırakmamız 
   * lazım, bu sebeple bellek bilgisini kaybetmemek için geçici bir düğüne atıyoruz.
   */
 Dugum *gecici = enUst;
 
 // En üstteki düğüm silineceği için, altındaki düğüm en üste gelecektir.
 enUst = enUst->altindaki;
 
 // Silinen düğüm için ayrılan belleği serbest bırakıyoruz.
 free(gecici);
 
 // düğümden aldığımız değeri ekrana döndürüyoruz.
 return sonuc;    
}

// Bütün düğüm verilerini ekrana yazdırma fonksiyonu.
void printStack(){
 /*  Ana yığının üzerinde değişiklik yapmamak için bir kopyasını oluşturuyoruz.
  *
  */
  
 Dugum *kopyaEnUst = enUst;
 
 // Görsel düzenleme için buradadır.
 printf("\n*******");
 
 // Değerler var olduğu sürece işlem devam etmeli.
 while(kopyaEnUst != NULL){
  printf("\nVeriler: %d ",kopyaEnUst->veri);
  
  /*  En üstteki veriye baktıktan sonra bir altındakinin bakmak için altındakini
   * en üste alıyoruz.
   */
  kopyaEnUst = kopyaEnUst->altindaki;
 }
 
 // Görsel düzenleme için buradadır.
 printf("\n*******");
}

int main(){
 int x = 10;
 for(x; x < 50; x+=10){
  push(x);
  printf("\n%d verisi eklendi",x);
  printStack();
 }
 
 int a,i = 1;
 
 for(a = pop(); i < 5; a = pop()){
  printf("\n%d verisi cikarildi.",a);
  
  printStack();
  i++;
 }
 
 push(30);
 printf("\n30 verisi eklendi");
 printStack();
}ack();
}
```

### Queue

```c
#include <stdio.h>
#include <stdlib.h>

/**
* Kuyruk yapısı
* @author Yunus Emre AK
*/

typedef struct kuy{
  int veri;
  
  struct kuy *arkasindaki;

}Dugum;

/*
*  Kuyruk yapısı FIFO (ilk giren, ilk çıkar) mantığıyla çalıştığı için;
*  -> Veriler silinirken "en önden" silinir.
*  -> Veriler eklenirken "en arkaya" eklenir.
*
* Pide kuyruğu şeklinde ifade edilebilir.
*
* (en arka)        (en ön)
*    |--------------->  
*
*  Başlangıçta en ön ve en arka birbirine eşit ve NULL(boşluk / hiç) olur.
*/
Dugum *enOn = NULL;
Dugum *enArka = NULL;

/*
* Kuyruğa eleman ekleme
* Hatırlatma: Veriler eklenirken "en arkaya" eklenir.
*  Not: Fonksiyon ismi "insert" olduğunda, kütüphanelerde kayılı olan insert fonksiyonları ile 
* karışmakta, bu sebele adı "myInsert" olarak tanımlanmıştır. 
*/
void myInsert(int veri){
 // Öncelikle alınan veri için yeni bir düğüm oluşturuyoruz.
 Dugum *yeni = (Dugum*)malloc(sizeof(Dugum));
 
 yeni->veri = veri; 
 
 /**
   *  Eğer kuyrukda dugum yoksa en ön ve en arka yeni oluşturulan düğüme 
   * eşit olur. Bu düğümlerin arkasında düğüm olmadığı için arkasına NULL atanır.
   */
 if(enOn == NULL){
  enOn = yeni;    
  enOn->arkasindaki = NULL;
  
  enArka = enOn;
 }
 
 // Kuyrukta zaten düğüm varsa.
 else{
  // Verilere eklenirken en arkaya ekleniyor.
  enArka->arkasindaki = yeni;
  
  // Eklenen yeni düğüm, en arkadaki eleman olduğu için en arkaya düğüm atanır.
  enArka = yeni;
  // En arkanın arkasında eleman olmayacağı için, arkasına NULL atanır.
  enArka->arkasindaki = NULL;
 }
 
}

/*  Veriler çıkartılırken en baştan çıkartılır.
 *
 *  Not: Fonksiyon ismi "remove" olduğunda, kütüphanelerde kayılı olan remove fonksiyonları ile 
 * karışmakta, bu sebele adı "myRemove" olarak tanımlanmıştır.
 */
int myRemove(){
 /*  Öncelikle kuyruğumuzdaki elemanları kontrol ediyoruz, eleman yoksa  işlem 
 * işlem olmaz. */
 if(enOn == NULL){
  printf("\nVeri olmadigi icin veri silme basarisiz!");
  
  // Hata kodu
  return -1;
 }
 
 /*  En öndeki düğümü tutan pointeri kaybetmemek için gecici bir pointer oluşturuyoruz.
  * bu sayede düğüm silindikten sonra, hafızada ayrılan yeri de serbest bırakabileceğiz.
  */
 Dugum *gecici = enOn;
 
 // Gecici düğüm, en öndeki (silinen) düğüm olduğu için silinen veriyi saklıyoruz.
 int veri = gecici->veri;
  
 /*  En öndeki düğümü arkasındakine atadığımız takdirde, son düğüm kuyruktan kopacak
  * ve serbest halde kalacak.
  */
 enOn = enOn->arkasindaki;
 
 printf("\nSilinen veri: %d", veri);
 
 // Serbest kalan gecici düğüm için ayrılan hafizayı da serbest bırakıyoruz.
 free(gecici);
 
 return veri;
}

// Fonksiyon isim sorunu olmamasi adina, "myDisplay" yazılmıştır.
void myDisplay(){
 // En öndeki düğüm adresini kaybetmemek için gezici bir düğüm tanımlıyoruz
 Dugum *gezici = enOn;
 
 if(gezici == NULL)
  printf("\n Veri bulunmamakta!");
  
 // Görsellik amaçlı.
 printf("\n-----------");
 
 /*  En önden başlayıp, en arkadaki düğüme kadar bakıyoruz. En arka düğüme geldiğimizde
  * arkası olmadığı için NULL'a denk geleceğiz ve döngü sona erecek.
  */
 while(gezici != NULL){
  printf("\nVeriler: %d", gezici->veri);
  
  // Bir arkadaki düğüme geçiyoruz.
  gezici = gezici->arkasindaki;
 }
 
 // Görsellik amaçlı.
 printf("\n-----------");
}

int main(){
 int i = 0;
 
 for(i; i < 20; i+=2){
  myInsert(i);
  myDisplay();
 }
 
 for(i = 0; i < 10; i++){
  printf("\n%d verisi cikarildi.", myRemove());
  myDisplay();
 }

}
```

### Linked List

```c
#include <stdio.h>
#include <stdlib.h>

/**
* Çift Yönlü Bağli Liste Yapısı
* @author Yunus Emre AK
*/

typedef struct node{
int veri;

struct node *oncesi;
struct node *sonrasi;
}Dugum;

/**
* İkili Bağlı listede veriler bir önceki ve bir sonraki veririnin adresini tutar.
* []-[]-[]-[]-[] (bagli liste)
*
*  Fonksiyonlarla işlem yaparken;
* Dugum* (Dugumun adresi)= Düğümlerle işlem yapmak için 
* Dugum** (Bağlı Listenin adresi) = Bağlı Listeyle işlem yapmak için
* kullanılır.
*
* Fonksiyonlarla değerlerde değişiklik yapmak için, değerin adresini vermek gerekir.
*/

/**
 * Alınan bağlı listenin en sonuna düğüm oluşturup veriyi ekleyen fonksiyon
 * Fonksiyonlar aldıkları parametreleri kopyalığı için, bağlı listenin adresini
 * tutan bir pointer almamız lazım.
 */
void append(Dugum **bagliListe, int veri){
 
 // Yeni düğüm oluşturup, hafızadan yer atıyoruz.
 Dugum *yeniDugum = (Dugum*)malloc(sizeof(Dugum));
 
 // Düğüme veri atıyoruz.
 yeniDugum->veri = veri;
 
 /**
  * Düğümün en sonuna ekleneceği için düğüm yapısı şu şeklildedir;
  * 
  * ... - (yeniDugum) - NULL
  */
  
  // Düğümün sonrası da, öncesi de null olduğu için atamaları yapıyoruz.
 yeniDugum->sonrasi = NULL;
 
 /**
   * Eğer düğüm boş ise, öncesinde de eleman olmayacağı için NULL atıyoruz.
   * NULL - (yeniDüğüm) - NULL
   */
 if(*bagliListe == NULL){
  yeniDugum->oncesi = NULL;
  
  // Yeni düğümümüzü ana düğüme ekliyoruz.
  *bagliListe = yeniDugum;
  
  //Fonksiyon sonu.
  return;
 }
 
 /**
  *  Dugumun en sonuna yeni dugum ekleneceği için, en sonunu bulmak için yardımcı 
  * düğüm oluşturuyoruz ki ana düğüm üzerinde değişiklik olmasın.
  */ 
 Dugum *sonDugum = *bagliListe;
 
 /**
  *  Yeni düğüm, düğüm sonuna ekleneceği için düğümü en sonuna alıyoruz.
  * Düğüm son düğümünün sonrası NULL olacağı için, son düğüm NULL olana kadar bir
  * sonrakinne geçiyoruz.
  */
 while(sonDugum->sonrasi != NULL)
  sonDugum = sonDugum->sonrasi;
 
 /**
  * Düğümün en sonu bulunduktan sonra düğüm yapısı şu şekilde olacaktır;
  * 
  * (sonDugum) - (yeniDugum) - NULL
  */
  
 // Yeni düğüm, son düğümün sonrasında olacağı için atama yapıyoruz.
 sonDugum->sonrasi = yeniDugum;
 
 // Son düğüm, yeni düğümün öncesinde olacağı için atama yapıyoruz.
 yeniDugum->oncesi = sonDugum;
 
 /**
    * sonDugum'ü daha kullanmayacağımız için alttaki atamaya gerek yoktur.
   * Yeni düğüm artık en sonda olacağı için son atamayı yapıyoruz.
    * sonDugum = yeniDugum;
    */
    
 
 // Fonksiyon sonu
 return;
}

/**
 * Alınan bağlı listenin en başına düğüm oluşturup veriyi ekleyen fonksiyon
 * Fonksiyonlar aldıkları parametreleri kopyalığı için, bağlı listenin adresini
 * tutan bir pointer almamız lazım.
 */
 void push(Dugum **bagliListe, int veri){
 // Eklenecek düğümü oluşturuyoruz.
 Dugum *yeniDugum = (Dugum*)malloc(sizeof(Dugum));
 
 // Düğüme veriyi atıyoruz.
 yeniDugum->veri = veri;
 
 /**
 * Eklenecek düğüm en başa ekleneceği için, bağlı liste şöyle olacaktır;
 * 
 * NULL - (yeniDüğüm) - ...
 */
 
 // Yeni düğümün öncesi NULL olacağı için atama yapıyoruz.
 yeniDugum->oncesi = NULL;
 
 /**
 * Eğer bağlı listede eleman yoksa yapı şöyle olacaktır;
 * 
 * NULL - (yeniDüğüm) - NULL
 */
 if(*bagliListe == NULL){
  // Yeni düğümün sonrasında NULL olacağı için atama yapıyoruz.
  yeniDugum->sonrasi = NULL;
  
  // Yeni düğümü bağlı listeye atıyoruz.
  *bagliListe = yeniDugum;
    
  // Fonksiyondan çıkış
  return;
 }
 
 // NOT: Bağlı listeden aldığımız düğüm değerinin değişmemesi için kopyalamlıyız.
 
 // Bağlı listenin en önünü bulmak için geçici düğüm tanımlıyoruz.
 Dugum *enOn = *bagliListe;
 
 
 
 /**
 * En öndeki elemanın bağlı listedeki konumu şöyle olacaktır;
 * 
 * NULL - (enOn) - ...
 * Bu yüzden enOn adlı düğümü öncesi NULL olana kadar öncekine atıyoruz.
 */
 while(enOn->oncesi != NULL)
  enOn = enOn->oncesi;
 
 /**
 * Eklenecek düğüm en başa ekleneceği için, bağlı liste şöyle olacaktır;
 * 
 * NULL - (yeniDüğüm) - (enON)
 * Not: yeniDugum'ün öncesine NULL ataması yukarıda yapılmıştı.
 */
 
 // enON, yeniDugum'ün sonrasında olacağı için atama yapıyoruz.
 yeniDugum->sonrasi = enOn;
 
 //yeniDugum, enOn'un öncesine olacağı için atama yapıyoruz.
 enOn->oncesi = yeniDugum;
 
 /**
 * enOn düğümünü daha kullanmayacağımız için alttaki atamaya gerek yoktur.
 * Yeni düğüm artık en önde olacağı için son atamayı yapıyoruz.
 * enOn = yeniDugum;
 */
 
 // Fonksiyon sonu.
 return;
 }
 


/**
*  Bağlı listeye eleman ekleme fonksiyonu.
*  Bu fonksyion listeden her hangi bir düğümün adresini ve yerleştirilecek veriyi
* parametre olarak alıyor, bu sayede veri alınan düğümün sonrasına ekleniyor.
*/
void insertAfter(Dugum *elimizdekiDugum, int veri){
 // İlk olarak düğümün doluluğu kontrol edilir, eğer boş ise işlem yapılmaz.
 if(elimizdekiDugum == NULL){
  printf("\n Dugumde veri bulunmamaktadir, hata !\nPush(param) fonksiyonunu kullaniniz.");
  
  
  // Hata  
  return;
 }
 // Verinin ekleneceği yeni düğüm oluşturuyoruz.
 Dugum *yeniDugum;
 
 // Oluşturulan bu düğüm yeni bir düğüm olduğu için bellek atıyoruz.
 yeniDugum =  (Dugum*)malloc(sizeof(Dugum));
 
 // Veriyi yeni düğümün verisine ekliyoruz.
 yeniDugum->veri = veri;
 
 /**
 *  Eklenecek olan yeni düğüm, parametre olarak verdiğimiz düğüm ile ondan sonraki
 * düğüm arasına ekleneceği için, parametre olarak verdiğimiz düğümün sonrasındaki
 * düğümün bilgisi de bize lazım olacaktır. Bu sebeple sonrakinin verisi tutan bir 
 * düğüm daha oluşturuyoruz.
 */
 Dugum *sonrakiDugum;
 
 /**
 *  Bu düğüm yeni bir düğüm olmayacağı için bellek atamıyoruz, elimizdeki düğümün
 * sonrasındaki düğümün adresini atıyoruz.
 */
 sonrakiDugum = elimizdekiDugum->sonrasi;
 
 
 /**
 *  Eklenecek olan yeni düğüm, elimizdeki düğüm ile onun sonrasındaki düğümün arasına
 * eklenceği gerekli atamaları yapıyoruz;
 *
 * (elimizdeki düğüm) - (yeni düğüm) - (elimizdekinden sonraki düğüm)
 */
 
 // Yeni düğüm, elimizden sonraki düğümden önce olduğu için atama yapıyoruz.
 if(sonrakiDugum != NULL)
  sonrakiDugum->oncesi = yeniDugum;
 
 // Elimizden sonraki düğüm, yeni düğümden sonra geldiği için atama yapıyoruz.
 yeniDugum->sonrasi = sonrakiDugum;
 
 // Elimizdeki düğüm, yeni düğümden önce olduğu için atama yapıyoruz.
 yeniDugum->oncesi = elimizdekiDugum;
 
 // Yeni düğüm, elimizdeki düğümden sonra geldiği için atama yapıyoruz.
 elimizdekiDugum->sonrasi = yeniDugum;
 
 // Fonksiyondan çıkış.
 return;
 
}

/**
 *  Düğüm silme fonksiyonu
 *
 *  Bu fonksiyon paremetre olarak aldığı silenecek düğümü silip, içindeki veriyi 
 * paremetre olarak aldığı veriAdresi'ne atıyor.
 *
 *  NOT: Bu fonksiyonu kullanırken doğrudan düğümün adresini göndermeyin, gönderdiğiniz düğüm
 * silineceği için bağlı listeye olan erişiminiz kesilecektir. Bu sebeple parametre olarak 
 * düğümün öncesini (prev) veya sonrasını (next) gönderin.
 */
void delete(Dugum *silinecekDugum, int *veriAdresi){
 // Öncelikle düğüm doluluğunu kontrol ediyoruz, boş ise işlem yapılamaz.
 if(silinecekDugum == NULL){
  printf("Silecek dugum bulunmamakta, hata!");
  
  // Fonksiyondan çıkış. 
  return;
 }
 
 /**
  *  İlk olarak silinecek düğümdeki veriyi alıyoruz. Veri adresi bir adres olduğu 
  * için, *(veriAdresi) yaparak, veri adresinin değerine atıyoruz.
  */
 *veriAdresi = silinecekDugum->veri;
 
 /**
  *  Düğümü silmeden önce öncesindeki ve sonrası düğüm arasındaki bağlantıyı
  * oluşturmamız lazım, be sebeple önceki ve sonraki düğüm adi altında 2 düğüm oluşturuyoruz.
  *
  * (önceki düğüm) - (silenecek düğüm) - (sonraki düğüm)
  */
 Dugum *oncekiDugum,*sonrakiDugum;
 
 // Silinecek düğümden önceki düğümü oluşturuyoruz.
 oncekiDugum = silinecekDugum->oncesi;
 
 // Silinecek düğümden sonraki düğümü oluşturuyoruz.
 sonrakiDugum = silinecekDugum->sonrasi;
 
 // Düğümü siliyoruz.
 free(silinecekDugum);
 
 /**
  * Düğüm silindikten sonra, düğümün yeni yapısı şu şekilde olacak;
  * (önceki düğüm) - - (sonraki düğüm)
  */
 
 // Önceki düğüm, sonraki düğümden önce geldiği için atama yapıyoruz.
 if(sonrakiDugum != NULL)
  sonrakiDugum->oncesi = oncekiDugum;
 
 // Sonraki düğüm, önceki düğümden sonra geldiği için atama yapıyoruz.
 if(oncekiDugum != NULL)
  oncekiDugum->sonrasi = sonrakiDugum;

 // Fonksiyondan çıkış.
 return;
}

/**
 * Verileri gösterme fonksiyonu
 * Alınan düğümün öncesindeki ve sonrasındaki her bir veriyi gösterir.
 */
void display(Dugum *dugum){
 // Öncelikle veri kontrolü yapıyoruz.
 if(dugum == NULL){
  printf("\n Verilen dugum bostur, hata!");
  
  // Fonksiyondan çıkış.
  return;
 }
 
 // Döğüm üzerinde gezinmek ve alınan düğüm adresini kaybetmemek için gezici tanımlıyoruz.
 Dugum *gezici = dugum;
 
 printf("\n-> Dugumdeki veri:\n%d",gezici->veri);
 printf("\n---------\n-> Dugumden sonraki veriler:\n");
  
 // Sonrasında veri olduğu sürece, verileri ekrana yazdırılmasını sağlıyoruz.
 while(gezici->sonrasi != NULL){
  // Düğümü bir sonrasındakine eşitleyerek, sonraki düğüme geçiyoruz.
  gezici = gezici->sonrasi;
  
  printf("%d, ", gezici->veri); 
 }
 
 // NULL olan geziciyi, tekrardan düğüme eşitliyoruz.
 gezici = dugum;
 
 printf("\n-> Dugumden onceki veriler:\n");
 
 // Öncesinde veri olduğu sürece, verileri ekrana yazdırılmasını sağlıyoruz.
 while(gezici->oncesi != NULL){
  // Düğümü bir öncekine eşitleyerek, önceki düğüme geçiyoruz.
  gezici = gezici->oncesi;
  
  printf("%d, ", gezici->veri);  
 }
 
 printf("\n---------");
 // Fonksiyondan çıkış.
 return;
}

int main(){
 Dugum *deneme = NULL;
 
 int i;
 int veri;
 
 for(i = 0; i < 10; i++){
  if(i%4 == 0)
   push(&deneme, i);
  else if(i%4 == 1)
   append(&deneme, i);
  else if(i%4 == 2)
   insertAfter(deneme->sonrasi, i);
  else if(i%4 == 3){
   delete(deneme->sonrasi, &veri);
   printf("----\n Silinen veri: %d",veri);
  }
  display(deneme);
}
 
}
```

### Double Linked List Açıklama

Açıklama için [buraya](https://www.yemreak.com/2017/10/double-linked-list-acklamas.html) bakabilirsin.

### Binary Tree

```c
#include <stdio.h>
#include <stdlib.h>

/**
 * İkili ağaç yapısı
 * @author Yunus Emre AK
 */


/**
 * İkili ağaç yapısında, daldaki değerden
 *  küçük ise soluna
 *  büyük ise sağına yazılır.
 *
 *       11
 *     /  \
 *      7    14
 *        / \   / \
 *       3   8  12  18
 *
 */
typedef struct _dal{
 int veri;
 
 _dal* solundaki;
 _dal* sagindaki;
}dal;

// Kullanıcı arayüzünüdeki yazıları oluşturan fonksiyon (Anlaşılabilirlik için.)
void menu();
// Kullanıcı arayüzünü oluşturan fonksiyon (Anlaşılabilirlik için.)
void loop(dal **);
// Ağacı oluşturmak için kullanılan fonksiyon.
void create(dal **);
// Bellek ayırmak için fonksiyon. (Tamamen kolaylık amaçlıdır.)
dal* get_leaf();
// İkili ağaç yapısına veri ekleme fonksiyonu.
void insert(dal*);
// Ağactaki verileri sıralayıp ekrana yazan fonksiyon (Anlaşılabilirlik için.)
void sort_disploy(dal*);
// Ağacta veri arama ve verinin bulundağı dalı geri döndüren fonksiyon.
dal* search(dal*, int);
// Ağacın dalları silen fonksiyon.
void destroy_leaf(dal*);
// Ağacı komple silen fonksiyon
void destroy_tree(dal**);


int main(){
 dal *agacim = NULL; 
  
 loop(&agacim);
}

// Fonksiyonlar;
dal* get_leaf(){
 return (dal*)malloc(sizeof(dal));
}

void insert(dal* gelen_dal, int veri){
 // Eğer gelen dal boş ise, yeni dal oluşturup veriyi atıyoruz.
 if(gelen_dal == NULL){
  printf("\n Agac yapisi mevcut degil. Lutfen once agaci olusturunuz.");
  
  return;
 }
 
 // Öncelikle gelen verinin baslangıç verimizden küçük olma durumunu inceliyoruz.
 if(veri < gelen_dal->veri){
  /**
   *  Eğer gelen veri, baş veriden "küçükse" dallarındaki diğer verileriyle de kıyaslamamız
   * lazım. Bu kıyaslama işlemi, küçük olma durumunu incelediğimiz için ağacın
   * başlangıcınının sol tarafında dal olmayana kadar devam etmeli.
   */
  if(gelen_dal->solundaki != NULL)
   /**
    *  Eğer dalın sonundaki null değilse, tekrardan ekleme fonksiyonunu çağırcağız.
    * Bu sayede her alt dal için başlangıç dalına uygulamış olduğumuz işlemler
    * uygulanacak.
    */
   insert(gelen_dal->solundaki, veri);
  /**
   *  Eğer dalın solunda başka dal yoksa, soluna yeni bir dal uluşturup veriyi atıyacağız.
      *           11
   *     /
    *    (Yeni Dal)
    *    /       \
    *   NULL      NULL
   */
  else{
   // Yeni dalımız için gelen dalın soluna dal oluşturuyoruz.
   gelen_dal->solundaki = get_leaf();
   // Gelen dalın soluna eklenen dala, gelen veriyi atıyoruz.
   gelen_dal->solundaki->veri = veri;
   /**
    *  Gelen dalın solunda oluşturulan daldan sonra dal olmadığı için her yönüne
    * de NULL atıyoruz.
    */
   gelen_dal->solundaki->solundaki = NULL;
   gelen_dal->solundaki->sagindaki = NULL;
  }  
 } 
 
  /**
   *  Eğer gelen veri, baş veriden "küçük değilse" dallarındaki diğer verileriyle de kıyaslamamız
   * lazım. Bu kıyaslama işlemi, küçük olma durumunu incelediğimiz için ağacın
   * başlangıcınının sağ tarafında dal olmayana kadar devam etmeli.
   */
 else{
  if(gelen_dal->sagindaki != NULL)
   /**
    *  Eğer dalın sonundaki null değilse, tekrardan ekleme fonksiyonunu çağırcağız.
    * Bu sayede her alt dal için başlangıç dalına uygulamış olduğumuz işlemler
    * uygulanacak.
    */
   insert(gelen_dal->sagindaki, veri);
   
  /**
   *  Eğer dalın sağında başka dal yoksa, sağında yeni bir dal uluşturup veriyi atıyacağız.
      *           11
   *      \
    *        (Yeni Dal)
    *         /       \
    *      NULL      NULL
   */
  else{
   // Yeni dalımız için gelen dalın sağına dal oluşturuyoruz.
   gelen_dal->sagindaki = get_leaf();
   // Gelen dalın sağına oluşturulan yeni dala veriyi atıyoruz.
   gelen_dal->sagindaki->veri = veri;
   /**
    *  Gelen dalın sağında oluşturulan daldan sonra dal olmadığı için her yönüne
    * de NULL atıyoruz.
    */
   gelen_dal->sagindaki->sagindaki = NULL;
   gelen_dal->sagindaki->solundaki = NULL;
  }
 } 
}

dal *search(dal* gelen_dal, int istenen_veri){
 // Sadece gelen dalda veri olduğu sürece işlem yapabiliriz.
 if(gelen_dal != NULL){
  // İlk olarak istenen veri gelen dalın verisi olup olmadığını kontrol ediyoruz.
  if(gelen_dal->veri == istenen_veri)
   return gelen_dal;
  
  /**
   *  Eğer istenen veri gelen daldan küçükse;
   * Ekleme yaparken küçük verileri gelen dalın soluna eklediğimiz için, bu fonksiyonu
   * gelen dalın solundaki dalı parametre vererek tekrar çağıracağız.
   */
  if(istenen_veri < gelen_dal->veri)
   search(gelen_dal->solundaki, istenen_veri);
   
  /**
   *  Eğer istenen veri gelen daldan küçük değilse yani gelen daldan büyük veya dala eşitse;
   * Ekleme yaparken küçük olmayan verileri gelen dalın sağına eklediğimiz için, bu fonksiyonu
   * gelen dalın sağındaki dalı parametre vererek tekrar çağıracağız.
   */
  else
   search(gelen_dal->sagindaki, istenen_veri);
  
  // Hiçbir koşul gerçekleşmiyorsa, istenen veri dalda mevcut değil demektir.
 }
 else
  return NULL;
}

void destroy_leaf(dal *gelen_dal){
/**
* (Agacın kökü (en üst verisi) gönderilirse, tüm ağacı siler.)
*        11                   11
*     /  \                /     \
*      7    14     ->      7        14
*        / \   / \           /  \    /    \
*       3   8  12  18      NULL NULL NULL NULL
*
* Alttan üste doğru silme işlemi yapmalıyız.
*
*/

 // Öncelikle gelen dal boş (NULL) değilse işlem yapılır.
 if(gelen_dal != NULL){
  /**
  *  Ağacın verileri silmeden önce ağacın dallarını temizlememiz gerekiyor,
  * aksi halde diğer dallara erişimimiz kesilecek ve dallar için ayrılan bellekleri
  * serbest bırakamayacağız. Bu sebeple bu fonksiyonu ağacın hem sağındaki hem de
  * solundaki dalları için tekrar çağırmamız, en sonda ağacın verisini silmemiz
  * gerekir.
  */
  destroy_leaf(gelen_dal->sagindaki);
  destroy_leaf(gelen_dal->solundaki);
  
  
  // Sağındaki ve solundaki tüm dallar silindikten sonra, ağacın baş verisi silinir.
  free(gelen_dal);
  
  
 }
}

void destroy_tree(dal **gelen_agac){
 // Öncelikle gelen dal boş (NULL) değilse işlem yapılır.
 if(*gelen_agac != NULL){
   // Agacin dallarını sildiriyoruz.
   destroy_leaf(*gelen_agac);
     
   // Gelen agacta dal kalmadığı için agaca NULL atıyoruz.
   *gelen_agac = NULL;
 }
}

void display_tree(dal *gelen_dal){
 if(gelen_dal != NULL){
  if(gelen_dal->solundaki != NULL)
   printf("| %d", gelen_dal->solundaki->veri);
  if(gelen_dal->sagindaki != NULL)
   printf("| %d", gelen_dal->sagindaki->veri);
 }
}

void sort_display(dal *gelen_dal){
 if(gelen_dal == NULL){
  printf("\nGosterilecek agac yok.");
  
  return;
 }
 
 if(gelen_dal->solundaki != NULL){
  sort_display(gelen_dal->solundaki);
 }
 
 printf("%d-",gelen_dal->veri);
 
 if(gelen_dal->sagindaki != NULL)
  sort_display(gelen_dal->sagindaki);
}

void menu(){
  printf("\n***************************\n");
 // Görsel hizalama için "%30s" 30 karakterlik alana sağa dayalı yazdırdık.
 printf("->%30s\n"," Agaci olusturmak icin 1'e");
 printf("->%30s\n"," Agaca sayi eklemek icin 2'e");
 printf("->%30s\n"," Agaci gostermek icin 3'e");
 printf("->%30s\n"," Agaci silmek icin 4'e");
 printf("->%30s\n"," Cikmak icin 0'a");
}

void loop(dal **agacim){ 
  int x = 5;
  
  while(x !=0){
  
  menu();
  
  /**
   *  Dipnot : Boşluk %c (" %c") yazılırsa, öncesinde basılan enter'ı veri olarak ("\n") görmez, hatalar engellenir.
    * %d kullanımı için bir satır atlatma karakteri algılama durumu olmaz. 
   */
  scanf("%d", &x);
  
  switch(x){
   case 1:
    create(agacim);
    
    break;
    
   case 2:
    printf("\nLutfen eklemek istediginiz veriyi giriniz:\t");
    
    int eklenecek_veri;
    
    scanf(" %d",&eklenecek_veri);
    
    insert(*agacim, eklenecek_veri);
    
    break;
   
   case 3:
    printf("Agacin verilerinin siralanmis hali:\n");
    sort_display(*agacim);
    
    break;
   
   case 4:
    printf("\nAgac silindi.\n");
    
    destroy_tree(agacim);
    
    break;
    
   default:
    break;
  }
 }
}

void create(dal **agac){
 if(*agac == NULL)
  *agac =get_leaf();
 
 printf("\nAgacin ilk verisini giriniz:\t");
 
 int bas_veri;
 
 scanf(" %d", &bas_veri);
 
 (*agac)->veri = bas_veri; 
 (*agac)->sagindaki = NULL;
 (*agac)->solundaki = NULL;
 
 printf("\nAgac %d verisiyle olusturuldu.", bas_veri);
}
```

<!-- Harici Bağlantılar -->

[Hocanın Sitesi]: http://www.oguzhanoztas.com/
[Fundemental Data Structures]: http://www.sncwgs.ac.in/wp-content/uploads/2015/11/Fundamental-Data-Structures.pdf
[Data Structures Using C++]: http://bu.edu.eg/portal/uploads/Computers%20and%20Informatics/Computer%20Science/1266/crs-10600/Files/Esam%20Halim%20Houssein%20Abd%20El-Halim_4-%20Data-Structure%20Using%20C++%20Malik.pdf
[Ders Notları]: https://drive.google.com/open?id=1FCwBorrNxHY817lMwgi7Lt7smXkDSx1A
[Sınav Soruları]: https://drive.google.com/open?id=1Db3cXWKAZ_WhpvxHIUPzBnTzwh70jSZO
[Visioalgo]: https://visualgo.net/en