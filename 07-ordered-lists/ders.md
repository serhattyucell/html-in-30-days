# 7. Gün — Sıralı listeler (Ordered Lists)

Bu gün, sırası değişince anlamı bozulan maddeleri numaralar. 6. gündeki daire, “hangisi önce” sorusuna cevap vermez. Bir yol tarifi, bir durak sırası veya bir işlem sırası `<ol>` ile yazılır.

## Madde numarası tarayıcıdan gelir

`<ol>` sıralı liste açar. Maddeler yine `<li>` ile yazılır. Numarayı tarayıcı koyar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durak sırası</title>
  </head>
  <body>
    <h1>Serhat'ın durak sırası</h1>
    <p>Bu sıra bir önceliktir. Birinci durak bitmeden ikinciye geçilmez.</p>
    <ol>
      <li>İstanbul</li>
      <li>Trabzon</li>
      <li>Van</li>
      <li>İzmir</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
“Serhat'ın durak sırası” büyük başlıktır. Açıklama paragrafı normal puntodadır. Altında dört satır girintilidir. Satırların başında daire değil, “1.” “2.” “3.” “4.” numaraları vardır. Numaralar kaynakta yazılmamıştır. “İstanbul” birincidir, “İzmir” dördüncüdür. Bir madde aradan silinirse tarayıcı kalan maddeleri yeniden sayar. El ile “3.” yazılmış bir paragraf bunu yapmaz.

`<ul>` ile `<ol>` aynı maddeleri taşıyabilir. Seçimi görünüş değil, sıra belirler. Kentlerin bir torbadaki adları daire ister. Yolculuğun hangi duraktan yürüdüğü numara ister. Bu listedeki İstanbul’dan İzmir’e giden çizgi bir karayolu haritası değildir. Notların okunma sırasıdır.

## Sayım verilen yerden başlar

`start` özelliği, ilk numaranın 1 dışında bir sayı olmasını sağlar. Liste önceki bir sayfadan devam ediyorsa kullanılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaldığı yer</title>
  </head>
  <body>
    <h1>Yolun devamı</h1>
    <p>İlk iki durak başka notta yazılmıştı. Bu sayfa üçüncüden alır.</p>
    <ol start="3">
      <li>Van</li>
      <li>İzmir</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
İki madde vardır. Birincinin başında “3.”, ikincinin başında “4.” durur. “1.” ve “2.” bu sayfada görünmez. “Van” üçüncü, “İzmir” dördüncü sıradadır. `start` kelimesi ekranda yazmaz. Yalnızca numaralar değişir.

Tek bir maddenin numarası da değiştirilebilir. `value` özelliği o maddeden itibaren sayımı yeniden kurar:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Atlanan numara</title>
  </head>
  <body>
    <h1>Seçilmiş duraklar</h1>
    <ol>
      <li>İstanbul</li>
      <li value="4">İzmir</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
“İstanbul” yanında “1.” vardır. “İzmir” yanında “2.” yoktur; “4.” vardır. Aradaki 2 ve 3 bu listede madde olarak durmaz. Bu, maddenin gerçekten dördüncü adım olduğunu söylemek içindir. Boşluk bırakarak maddeyi aşağı itmek için kullanılmaz.

## Sayım geriye yürür, harf de olur

`reversed` özelliği numarayı sondan başa dizer. `type` özelliği rakam yerine harf veya Romen rakamı seçer. İkisi de sırayı anlatmaya devam eder. Süs için harfe geçilmez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Geri sayım ve harf</title>
  </head>
  <body>
    <h1>Dönüş</h1>
    <h2>Geriye doğru</h2>
    <ol reversed>
      <li>İzmir</li>
      <li>Van</li>
      <li>Trabzon</li>
      <li>İstanbul</li>
    </ol>
    <h2>Alt adımlar</h2>
    <ol type="a">
      <li>Bileti al</li>
      <li>Çıkış kapısını bul</li>
      <li>Yerine geç</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
“Geriye doğru” başlığının altında dört madde vardır. En üstte “İzmir” ve onun solunda “4.” durur. Sonra “Van” yanında “3.”, “Trabzon” yanında “2.”, “İstanbul” yanında “1.” gelir. Liste yukarıdan aşağı okunur ama numaralar azalır. “Dönüş” anlatıldığı için büyük numara yolun sonundaki kenttedir.

“Alt adımlar” altında üç madde vardır. Başlarında “1.” değil, “a.” “b.” “c.” harfleri durur. `type` değeri `A` olursa harfler büyük, `i` olursa küçük Romen rakamı, `I` olursa büyük Romen rakamı görünür. `1` varsayılan rakamdır. Harf, maddenin bir ana adımın alt sırası olduğunu göstermek için seçilir. Rengi değiştirmek ileride CSS konusudur.

`reversed` yazılırken `reversed="reversed"` biçimi de doğrudur. Özelliğin yalnızca adının yazılması yeter. Bu tür özelliklerin kuralı 22. günde toplanır. Bugün sıralı listenin sayımını değiştirmek için kullanılır.

## Sık yapılan hata

Numarayı hem el ile yazmak hem de `<ol>` kullanmak, ekranda iki sayı yan yana getirir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Çift numara</title>
  </head>
  <body>
    <h1>İskele</h1>
    <ol>
      <li>1. İstanbul</li>
      <li>2. Trabzon</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Birinci satır “1. 1. İstanbul” gibi okunur. Soldaki numarayı tarayıcı, soldaki “1.” metnini ise kaynak koyar. İkinci satır “2. 2. Trabzon” olur. Madde silinince el ile yazılmış numaralar eski yerinde kalır, tarayıcının numaraları kayar. İki dizi birbirini tutmaz.

Doğru belge numarayı metne koymaz:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek numara</title>
  </head>
  <body>
    <h1>İskele</h1>
    <ol>
      <li>İstanbul</li>
      <li>Trabzon</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
“1. İstanbul” ve “2. Trabzon” satırları vardır. Her satırda tek numara görünür.

İkinci hata, sırası olmayan kent adlarını `<ol>` içine koymaktır. Tarayıcı yine “1. 2. 3.” basar. Okuyan kişi, İstanbul’un İzmir’den önce yapılması gereken bir iş olduğunu sanır. Öncelik yoksa liste `<ul>` olarak kalır.

Üçüncü hata, `start` değerine tırnak içinde harf yazmaktır. `start` bir sayıdır. Harf dizisi `type` ile seçilir.

## Egzersizler

1. Dört duraklık bir sıra kurun. Ekranda “1. İstanbul”, “2. Trabzon”, “3. Van”, “4. İzmir” görünsün. Numaralar kaynakta yazılı olmasın. İstanbul maddesini silin ve kalan üç satırın “1.”, “2.”, “3.” olarak yeniden sayıldığını görün.
2. Aynı yolun yalnızca son iki durağını gösteren ikinci bir liste yazın. Numaralar “3.” ve “4.” olarak başlasın. “1.” bu listede görünmesin.
3. Üç hazırlık adımını “a.”, “b.”, “c.” ile gösterin. Listenin üstünde, geriye sayılan bir durak listesi de dursun. En üst maddenin numarası madde sayısına eşit olsun, en alt maddenin numarası “1.” olsun.

[← Önceki gün](../06-unordered-lists/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../08-nested-lists/ders.md)
