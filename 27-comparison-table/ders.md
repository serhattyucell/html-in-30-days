# 27. Gün — Küçük sayfa: kıyaslama tablosu

Bu gün, dört kenti aynı ölçülerle yan yana okutur. 26. gündeki form bir ileti topluyordu. Bugün okunan şey bir ızgaradır. Yeni bir etiket yoktur. Tablonun adı, sütun başlığı, satır başlığı, birleşen hücre ve alt bilgi 13. ve 14. günlerde kurulmuştu. Bölge, su ve plaka gerçek karşılıklardır. Plaka kodları 34, 35, 61 ve 65 olarak kalır.

## Dört satır, üç ölçü

Her satır bir kenttir. Sütunlar bölge, su ve plakadır. Üstteki “Konum” başlığı, bölge ile suyun ortak adıdır.

Belge `kiyas.html` adıyla kaydedilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kıyaslama</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Kıyaslama</h1>
      <p>
        İstanbul, İzmir, Trabzon ve Van aynı üç soruyla okunur: hangi bölge, hangi su, hangi plaka.
      </p>
    </header>
    <main id="icerik">
      <table>
        <caption>Dört kentin bölgesi, suyu ve plakası</caption>
        <thead>
          <tr>
            <th scope="col" rowspan="2">Kent</th>
            <th scope="col" colspan="2">Konum</th>
            <th scope="col" rowspan="2">Plaka</th>
          </tr>
          <tr>
            <th scope="col">Bölge</th>
            <th scope="col">Su</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">İstanbul</th>
            <td>Marmara Bölgesi</td>
            <td>İstanbul Boğazı</td>
            <td>34</td>
          </tr>
          <tr>
            <th scope="row">İzmir</th>
            <td>Ege Bölgesi</td>
            <td>Ege Denizi</td>
            <td>35</td>
          </tr>
          <tr>
            <th scope="row">Trabzon</th>
            <td>Karadeniz Bölgesi</td>
            <td>Karadeniz</td>
            <td>61</td>
          </tr>
          <tr>
            <th scope="row">Van</th>
            <td>Doğu Anadolu Bölgesi</td>
            <td>Van Gölü</td>
            <td>65</td>
          </tr>
        </tbody>
        <tfoot>
          <tr>
            <td colspan="4">Dört kent, aynı notun içindedir.</td>
          </tr>
        </tfoot>
      </table>
      <h2>Nasıl okunur</h2>
      <ul>
        <li>Satır soldan sağa, bir kenti bitirir.</li>
        <li>Sütun yukarıdan aşağı, aynı ölçüyü dört kentte tutar.</li>
        <li>Plaka kodu değişmez. 34 İstanbul’a, 35 İzmir’e, 61 Trabzon’a, 65 Van’a aittir.</li>
      </ul>
      <p>
        Çizgi bu tabloda görünmez. Izgara, kelimelerin hizasından okunur.
        Çizgi ileride CSS konusudur.
      </p>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Kıyaslama” yazar. Sayfanın en büyük satırı da “Kıyaslama”dır. Altında, üç soruyu sayan bir paragraf vardır. Tablonun adı “Dört kentin bölgesi, suyu ve plakası” tablonun üstünde durur.

Başlık kuşağında “Kent” solda, iki satır yüksekliğindedir ve kalındır. “Konum” onun sağında, “Bölge” ile “Su”nun üzerinde tek parça hâlinde yayılır. “Plaka” sağda, “Kent” gibi iki satır yüksektir. İkinci başlık satırında yalnızca “Bölge” ve “Su” vardır. “Kent” ve “Plaka” o satırda yeniden yazılmaz.

Veri dört satırdır. İstanbul’un bölgesi Marmara Bölgesi, suyu İstanbul Boğazı, plakası 34’tür. İzmir’de Ege Bölgesi, Ege Denizi ve 35 vardır. Trabzon’da Karadeniz Bölgesi, Karadeniz ve 61 vardır. Van’da Doğu Anadolu Bölgesi, Van Gölü ve 65 vardır. Kent adları kalın, bölge ve su adları düz, plaka rakamları düzdür. Çerçeve yoktur. Buna rağmen 61, Trabzon satırından kayıp İzmir’in yanına düşmez.

En altta, dört sütunun birden üzerine yayılmış “Dört kent, aynı notun içindedir.” cümlesi durur. Cümle yalnızca soldaki dar hücreye sıkışmaz. Tablonun altında “Nasıl okunur” orta boy bir başlık ve üç daireli madde vardır. Son paragraf, çizginin bu belgede olmadığını ve hizanının kelimelerden geldiğini söyler. Sayfa “Notu yazan: Serhat” ile biter.

## Tek satır da tablo olur

Kısa belge, Van satırının kendi başına da hizayı koruduğunu gösterir. Tam tablonun tekrarı değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Van satırı</title>
  </head>
  <body>
    <h1>Tek satır</h1>
    <table>
      <caption>Van</caption>
      <thead>
        <tr>
          <th scope="col">Bölge</th>
          <th scope="col">Su</th>
          <th scope="col">Plaka</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Doğu Anadolu Bölgesi</td>
          <td>Van Gölü</td>
          <td>65</td>
        </tr>
      </tbody>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Tek satır” büyük başlıktır. Tablonun adı “Van”dır. Altında kalın “Bölge”, “Su” ve “Plaka” yan yana durur. Tek veri satırında “Doğu Anadolu Bölgesi”, “Van Gölü” ve “65” aynı yatay sıradadır. 65, gölün altına inmez. Sağdaki hücrede kalır.

## Sık yapılan hata

“Konum” iki sütun kaplarken ikinci başlık satırına bir de “Kent” koymak, plakayı sağa iter.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaymış plaka</title>
  </head>
  <body>
    <h1>Kaymış tablo</h1>
    <table>
      <tr>
        <th rowspan="2">Kent</th>
        <th colspan="2">Konum</th>
        <th rowspan="2">Plaka</th>
      </tr>
      <tr>
        <th>Kent</th>
        <th>Bölge</th>
        <th>Su</th>
      </tr>
      <tr>
        <td>Van</td>
        <td>Doğu Anadolu Bölgesi</td>
        <td>Van Gölü</td>
        <td>65</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
İkinci satırda fazladan bir “Kent” vardır. “Su” sağa kayar. Van satırındaki 65, “Plaka” başlığının altında durmaz. Boş bir sütun veya kaymış bir başlık görünür. “Konum” hâlâ iki sütunluk yer tuttuğu için alttaki hücre sayısı ona uymaz.

Doğru belgede ikinci satır yalnızca birleşmenin açtığı iki boşluğu doldurur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hizalı plaka</title>
  </head>
  <body>
    <h1>Hizalı tablo</h1>
    <table>
      <tr>
        <th rowspan="2">Kent</th>
        <th colspan="2">Konum</th>
        <th rowspan="2">Plaka</th>
      </tr>
      <tr>
        <th>Bölge</th>
        <th>Su</th>
      </tr>
      <tr>
        <th scope="row">Van</th>
        <td>Doğu Anadolu Bölgesi</td>
        <td>Van Gölü</td>
        <td>65</td>
      </tr>
    </table>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” solda, “Doğu Anadolu Bölgesi” bölge sütununda, “Van Gölü” su sütununda, “65” plaka sütunundadır. “Plaka” başlığı 65’in üzerindedir.

## Egzersizler

1. `kiyas.html` dosyasında İstanbul 34 ve İstanbul Boğazı, İzmir 35 ve Ege Denizi, Trabzon 61 ve Karadeniz, Van 65 ve Van Gölü ile aynı satırda dursun. Çerçeve görünmese de her plaka kendi kentinin hizasında kalsın.
2. “Konum” başlığı bölge ve suyun üzerinde tek parça görünsün. “Kent” ile “Plaka” iki satır yüksekliğinde olsun. İkinci başlık satırında “Kent” yeniden yazılmasın.
3. Tablonun en altında “Dört kent, aynı notun içindedir.” cümlesi dört sütunun birden altında uzansın. Soldaki dar hücrede kesilip sağda boş sütun bırakmasın.

[← Önceki gün](../26-contact-form/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../28-faq/ders.md)
