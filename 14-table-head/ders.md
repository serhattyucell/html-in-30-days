# 14. Gün — Tablo başlığı ve hücre birleştirme (Table Head and Span)

Bu gün, tablonun üst satırını başlık yapar ve bir hücrenin birden fazla satır ya da sütun kaplamasını sağlar. 13. günde “Kent” yazısı da veri gibi, sıradan bir hücreydi. Başlık hücresi, altındaki sütunun adı olduğunu söyler. Birleştirme ise “bu yazı iki sütunun ortak adıdır” demenin yoludur.

## Başlık hücresi sütunu adlandırır

`<th>`, başlık hücresidir. `<td>` veri hücresidir. Üst satırdaki başlıklar `<thead>` içine, veri satırları `<tbody>` içine alınır. Tablonun altında bir toplam veya sonuç varsa o satırlar `<tfoot>` içinde durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başlıklı tablo</title>
  </head>
  <body>
    <h1>Plakalar</h1>
    <table>
      <caption>Dört kentin plaka kodu ve suyu</caption>
      <thead>
        <tr>
          <th>Kent</th>
          <th>Plaka</th>
          <th>Su</th>
        </tr>
      </thead>
      <tbody>
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
      </tbody>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Tablonun adının altında üç başlık kalın durur ve çoğu tarayıcıda ortalanır: “Kent”, “Plaka”, “Su”. Alttaki dört satır kalın değildir ve sola yaslanır. İstanbul satırında 34 ve Boğaz, İzmir satırında 35 ve Ege Denizi, Trabzon satırında 61 ve Karadeniz, Van satırında 65 ve Van Gölü vardır. Çerçeve yine yoktur. Başlık ile veriyi ayıran şey puntodur. “Kent” kelimesi artık birinci veri gibi durmaz. Sütunun adıdır.

`<thead>`, `<tbody>` ve ileride eklenecek `<tfoot>` ekranda kutu çizmez. Onlar satırları üç öbeğe ayırır. Okuyan bir program, “34” hücresinin “Plaka” başlığının altında durduğunu bu yapıdan anlar. `<thead>` tablonun içinde, caption’dan sonra, veri satırlarından önce yazılır.

Sol sütunun kendisi de başlık olabilir. “İstanbul” bir veri değil, o satırın adıysa hücre `<th>` olur. `scope` özelliği, bu başlığın satıra mı yoksa sütuna mı ait olduğunu söyler. `scope="col"` sütun başlığı, `scope="row"` satır başlığı demektir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Satır başlığı</title>
  </head>
  <body>
    <h1>Bölgeler</h1>
    <table>
      <caption>Kent ve bölgesi</caption>
      <thead>
        <tr>
          <th scope="col">Kent</th>
          <th scope="col">Bölge</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">Van</th>
          <td>Doğu Anadolu Bölgesi</td>
        </tr>
        <tr>
          <th scope="row">Trabzon</th>
          <td>Karadeniz Bölgesi</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Kent” ve “Bölge” üstte, kalın ve çoğu tarayıcıda ortadadır. “Van” ve “Trabzon” solda kalın durur. “Doğu Anadolu Bölgesi” ve “Karadeniz Bölgesi” kalın değildir. `scope` kelimesi ekranda görünmez. Van’ın kalın olması, onun bir doğu bölgesi “verisi” değil, satırın adı olması yüzündendir. Bölge adı veri olarak düz kalır.

## Bir hücre iki sütun kaplar

`colspan`, hücrenin kaç sütun genişleyeceğini söyler. Ortak bir başlık, alttaki iki sütunun üstünde tek parça hâlinde durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Birleşen sütun</title>
  </head>
  <body>
    <h1>Kıyılar</h1>
    <table>
      <caption>Dört kent, iki küme</caption>
      <thead>
        <tr>
          <th rowspan="2">Kent</th>
          <th colspan="2">Konum</th>
        </tr>
        <tr>
          <th>Bölge</th>
          <th>Su</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">İstanbul</th>
          <td>Marmara Bölgesi</td>
          <td>Boğaz</td>
        </tr>
        <tr>
          <th scope="row">İzmir</th>
          <td>Ege Bölgesi</td>
          <td>Ege Denizi</td>
        </tr>
        <tr>
          <th scope="row">Trabzon</th>
          <td>Karadeniz Bölgesi</td>
          <td>Karadeniz</td>
        </tr>
        <tr>
          <th scope="row">Van</th>
          <td>Doğu Anadolu Bölgesi</td>
          <td>Van Gölü</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte solda “Kent” iki satır yüksekliğinde durur. Hem “Konum” satırının hem de “Bölge / Su” satırının hizasına iner. “Konum”, sağdaki iki sütunun üzerinde tek kalın başlık olarak yayılır. Onun altında “Bölge” ve “Su” ayrı ayrı durur. Veride İstanbul, Marmara Bölgesi ve Boğaz aynı satırdadır. Van, Doğu Anadolu Bölgesi ve Van Gölü aynı satırdadır. “Kent” hücresinin sağında, birinci üst satırda ikinci bir boş başlık yoktur. O yeri `rowspan` tutar. İkinci başlık satırında “Kent” yeniden yazılmaz. Yazılırsa fazladan bir sütun açılır ve “Bölge” sağa kayar.

`rowspan="2"`, iki satır kapla demektir. `colspan="2"`, iki sütun kapla demektir. Sayı, gerçekten kapanan satır veya sütun adedidir. Tabloda üç sütun varsa `colspan="4"` yazılmaz. Taşan hücre, satırı tablonun dışına doğru uzatır.

## Alt bilgi, verinin özetini tutar

`<tfoot>`, veri satırlarından sonra görünmesi gereken özeti taşır. Kaynakta `<tbody>` öncesine de yazılabilir. Ekranda yine tablonun altında durur. Bu rehberde okunurluk için gövdeden sonra yazılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Alt bilgi</title>
  </head>
  <body>
    <h1>Notlardaki kentler</h1>
    <table>
      <caption>Listelenen yerler</caption>
      <thead>
        <tr>
          <th scope="col">Kent</th>
          <th scope="col">Not</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>İstanbul</td>
          <td>Boğaz</td>
        </tr>
        <tr>
          <td>İzmir</td>
          <td>Körfez</td>
        </tr>
        <tr>
          <td>Trabzon</td>
          <td>Kıyı</td>
        </tr>
        <tr>
          <td>Van</td>
          <td>Göl</td>
        </tr>
      </tbody>
      <tfoot>
        <tr>
          <td colspan="2">Dört kent aynı notta durur.</td>
        </tr>
      </tfoot>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Üstte kalın “Kent” ve “Not” vardır. Dört veri satırı altlarındadır. En altta “Dört kent aynı notta durur.” cümlesi, iki sütunun birden üzerine yayılmış tek bir hücre olarak durur. Cümle yalnızca soldaki dar sütunda sıkışmaz. Sağdaki “Göl” sütununun altına da uzanır. İki ayrı hücreye aynı cümle bölünmez.

## Sık yapılan hata

Birleştirilen hücrenin yerini yanındaki satırda yeniden doldurmak, fazla sütun üretir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Fazla hücre</title>
  </head>
  <body>
    <h1>Konum</h1>
    <table>
      <tr>
        <th colspan="2">Konum</th>
        <th>Artık</th>
      </tr>
      <tr>
        <td>İzmir</td>
        <td>Ege Bölgesi</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
Üst satırda “Konum” iki sütunluk yer kapladıktan sonra bir de “Artık” başlığı üçüncü sütunu açar. Alt satırda yalnızca iki hücre vardır. “Ege Bölgesi” ikinci sütundadır. Üçüncü sütun boş kalır veya tarayıcı kaymış bir ızgara çizer. “Artık” kelimesinin altında veri yoktur.

Doğru belgede üst satır tam iki sütundur. `colspan="2"` olan başlığın yanına üçüncü bir `<th>` konmaz:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tam hücre</title>
  </head>
  <body>
    <h1>Konum</h1>
    <table>
      <tr>
        <th colspan="2">Konum</th>
      </tr>
      <tr>
        <td>İzmir</td>
        <td>Ege Bölgesi</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Konum”, “İzmir” ile “Ege Bölgesi”nin üzerinde, ikisinin birden genişliğinde durur. Üçüncü bir boş sütun açılmaz.

İkinci hata, bütün hücreleri `<th>` yapmaktır. Tablonun tamamı kalın ve ortaya yaslı görünür. Veri ile başlık ayırt edilmez. Yalnızca sütunun veya satırın adı `<th>` olur. Plaka numarası, bölge ve su adı `<td>` kalır.

## Egzersizler

1. Üç sütunluk bir tablo kurun: Kent, Plaka, Su. Üst satır kalın olsun. İstanbul 34 ve Boğaz, Van 65 ve Van Gölü kendi satırlarında hizalansın. Plaka numaraları kalın olmasın.
2. “Konum” başlığı, Bölge ve Su sütunlarının üzerinde tek parça görünsün. Sol başta “Kent” iki satır yüksekliğinde dursun. İstanbul satırı kaymasın.
3. Tablonun en altına, iki sütunu birden kaplayan “Dört kent aynı notta durur.” cümlesini koyun. Cümle soldaki sütunda kesilip sağda boşluk bırakmasın.

[← Önceki gün](../13-tables/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../15-forms/ders.md)
