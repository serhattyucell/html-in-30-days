# 13. Gün — Tablolar (Tables)

Bu gün, aynı türden bilgileri satır ve sütun hâlinde dizer. 6. gündeki liste tek bir diziydi. “Kent” ve “suyun adı” gibi yan yana durması gereken iki bilgi, listenin iki maddesi olursa ilişki kopar. Tablo, o iki bilgiyi aynı satırda tutar.

## Satır yatay, hücre satırın içindedir

`<table>` tablonun kendisidir. `<tr>` bir satır açar. `<td>` o satırdaki bir hücredir. Hücre, tablonun içinde doğrudan durmaz. Önce satır açılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent ve su</title>
  </head>
  <body>
    <h1>Dört kent</h1>
    <p>Her satır bir kenti, sağındaki hücre o kentin suyunu adlandırır.</p>
    <table>
      <tr>
        <td>İstanbul</td>
        <td>Boğaz</td>
      </tr>
      <tr>
        <td>İzmir</td>
        <td>Ege Denizi</td>
      </tr>
      <tr>
        <td>Trabzon</td>
        <td>Karadeniz</td>
      </tr>
      <tr>
        <td>Van</td>
        <td>Van Gölü</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Dört kent” başlığının ve açıklama paragrafının altında dört satırlık bir ızgara vardır. Soldaki sütunda İstanbul, İzmir, Trabzon ve Van alt alta, aynı hizada durur. Sağdaki sütunda, her kentin hizasında, Boğaz, Ege Denizi, Karadeniz ve Van Gölü okunur. “Ege Denizi” daha uzun olduğu için sağ sütun, en uzun hücreye göre genişler. Hücrelerin arasında kalın bir çerçeve görünmez. Çizgi ileride CSS konusudur. Çizgi olmadığı hâlde sütunlar ayırt edilir: kent adları bir dikey hat, su adları ikinci bir dikey hat üzerinde durur. Yazılar çoğu tarayıcıda soldan hizalanır ve hücrelerin içinde küçük bir boşluk yoktur; karakterler birbirine yakın durabilir.

Bu dört çift, dört ayrı paragraf olarak da yazılabilirdi. Paragrafta “Van” ile “Van Gölü” aynı cümlenin içinde kaybolur. Tabloda ikisi aynı yatay sıranın iki gözüdür. Üçüncü satır okununca Trabzon’un karşılığı Karadeniz’dir. Başka bir satırın suyu oraya kaymaz.

## Tablonun adı

`<caption>` tablonun adıdır. Başlıktan farkı, adın tabloya ait olmasıdır. Sayfanın `<h1>` başlığı bütün notu, caption yalnızca bu ızgarayı adlandırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tablonun adı</title>
  </head>
  <body>
    <h1>Serhat'ın notu</h1>
    <table>
      <caption>Kentin bölgesi</caption>
      <tr>
        <td>İstanbul</td>
        <td>Marmara Bölgesi</td>
      </tr>
      <tr>
        <td>İzmir</td>
        <td>Ege Bölgesi</td>
      </tr>
      <tr>
        <td>Trabzon</td>
        <td>Karadeniz Bölgesi</td>
      </tr>
      <tr>
        <td>Van</td>
        <td>Doğu Anadolu Bölgesi</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Sayfanın büyük başlığı “Serhat'ın notu”dur. Tablonun üstünde, ortaya yakın veya solda, “Kentin bölgesi” yazar. Bu, tablonun adıdır ve çoğu tarayıcıda normal puntodadır. Onun altında iki sütun vardır. Solda dört kent, sağda bölge adları aynı satırda eşleşir. İstanbul’un karşısında Marmara Bölgesi, Van’ın karşısında Doğu Anadolu Bölgesi durur. Bölge adları uydurma kısaltmalar değildir. Dört kent bu bölgelerin içindedir.

`<caption>`, `<table>` açılır açılmaz, ilk satırdan önce yazılır. Tablonun altında bir paragraf olarak durması başka bir cümledir. Ad, tablonun içinde kalır.

## Hücre sayısı her satırda aynıdır

Bir satırda iki hücre varsa diğer satırlarda da iki hücre aranır. Eksik hücre, sağdaki sütunu kaydırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Üç sütun</title>
  </head>
  <body>
    <h1>Plaka</h1>
    <table>
      <caption>Kentlerin plaka kodları</caption>
      <tr>
        <td>Kent</td>
        <td>Plaka</td>
        <td>Su</td>
      </tr>
      <tr>
        <td>İstanbul</td>
        <td>34</td>
        <td>Boğaz</td>
      </tr>
      <tr>
        <td>İzmir</td>
        <td>35</td>
        <td>Ege Denizi</td>
      </tr>
      <tr>
        <td>Trabzon</td>
        <td>61</td>
        <td>Karadeniz</td>
      </tr>
      <tr>
        <td>Van</td>
        <td>65</td>
        <td>Van Gölü</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Üst satırda “Kent”, “Plaka”, “Su” yan yana durur. Bu satır henüz özel bir başlık hücresi değildir. 14. gün onu başlık yapar. Bugün o da diğerleri gibi bir veri satırı olarak, aynı puntoda görünür. Alt satırlarda İstanbul ile 34 ve Boğaz aynı hizadadır. İzmir 35, Trabzon 61, Van 65 ile sağa doğru üç sütun kurar. Sayılar, il trafik plakası kodlarıdır ve değişmez. Sütunlar çizgisizdir. Yine de “34” sözcüğü “İstanbul”un sağında, “Boğaz”ın solunda durur. “61” Trabzon satırından İzmir satırına kaymaz.

Bir hücreye uzun bir cümle konursa o sütun genişler, diğer satırlardaki aynı sütun da genişler. Satır yüksekliği, o satırdaki en yüksek içeriğe göre artar. Yükseklik için boş satır eklenmez.

## Sık yapılan hata

Hücreyi satırın dışına yazmak, o yazıyı tablonun düzeninden çıkarır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Satır yok</title>
  </head>
  <body>
    <h1>Van</h1>
    <table>
      <td>Van</td>
      <td>Van Gölü</td>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Bazı tarayıcılar eksik satırı onarıp iki sözü yine yan yana çizer. Bazıları sözleri alt alta, tablonun dışında bırakır. Sonuç tarayıcıdan tarayıcıya değişir. “Van Gölü”nün “Van”ın sağında duracağı garanti değildir.

Doğru belgede her hücre bir satırın içindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Satır var</title>
  </head>
  <body>
    <h1>Van</h1>
    <table>
      <tr>
        <td>Van</td>
        <td>Van Gölü</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” solda, “Van Gölü” onun sağındadır. İkisi aynı yatay çizgide durur.

İkinci hata, bir satıra üç, sonraki satıra iki hücre koymaktır. Üçüncü sütun yalnızca birinci satırda varsa alttaki “Karadeniz” sola kayar ve Trabzon’un plaka sütununa oturur. Her satır aynı sayıda `<td>` taşır. Bir hücrenin iki sütunu kaplaması istenirse o, 14. günün birleştirme özelliğidir. Bugün hücreler birleştirilmez. Eksik yer boş bir `<td></td>` ile tutulur. Boş hücre, çizgi olmadığı için ince bir boşluk olarak görünebilir. Sütun hizası yine de bozulmaz.

Üçüncü hata, tabloyu paragraf boşluklarıyla taklit etmektir. Kelimeler pencere daralınca birbirinin altına düşer. “65” başka bir kentin yanında kalabilir. Aynı bilgi tabloya konunca dar pencerede yatay kaydırma çıksa bile Van ile 65 aynı satırda durur.

## Egzersizler

1. İki sütunluk bir tablo kurun. Dört satırda İstanbul, İzmir, Trabzon ve Van, sağlarında sırasıyla Marmara Bölgesi, Ege Bölgesi, Karadeniz Bölgesi ve Doğu Anadolu Bölgesi görünsün. Çerçeve olmasa da her bölge kendi kentinin hizasında kalsın.
2. Tablonun üstüne “Kentin bölgesi” adını koyun. Bu ad sayfanın büyük başlığı olmasın. Sayfanın büyük başlığı “Serhat'ın notu” olarak ayrı dursun.
3. Bir satırdan `<tr>` etiketini kaldırıp yenileyin. Hücrelerin hizası bozulursa veya tarayıcıdan tarayıcıya değişirse satırı geri koyun. Dört kent yeniden iki düzgün sütun kursun.

[← Önceki gün](../12-figure/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../14-table-head/ders.md)
