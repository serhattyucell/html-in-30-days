# 29. Gün — Sayfaları birbirine bağlayan site

Bu gün, önceki küçük sayfaları aynı klasörde birbirine bağlar. 28. günde bağlantı, tek dosyanın içindeki bir başlığa iniyordu. Bugün bağlantı başka bir dosyayı açar. Yeni bir etiket yoktur. Her sayfada aynı gezinti durur. Açık olan sayfanın adı bağlantı değil, düz ve kalın bir kelimedir. Böylece “şu an neredeyim” sorusu, kendine giden bir bağlantı olmadan okunur.

Altı dosya aynı klasöre kaydedilir. Adlar şunlardır: `index.html`, `hakkinda.html`, `duraklar.html`, `iletisim.html`, `kiyas.html`, `sorular.html`. Birinin içindeki `href` yalnızca dosya adıdır. `https://` yazılmaz.

## Kapak, beş sayfayı açar

`index.html`, sitenin ilk açılan dosyasıdır. Beş satır, beş dosyaya gider.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notları</title>
  </head>
  <body>
    <header>
      <h1>Serhat'ın kent notları</h1>
      <p>Dört kent, beş sayfada durur.</p>
    </header>
    <nav>
      <ul>
        <li><strong>Kapak</strong></li>
        <li><a href="hakkinda.html">Hakkında</a></li>
        <li><a href="duraklar.html">Durak listesi</a></li>
        <li><a href="iletisim.html">İletişim</a></li>
        <li><a href="kiyas.html">Kıyaslama</a></li>
        <li><a href="sorular.html">Sorular</a></li>
      </ul>
    </nav>
    <main>
      <p>Okumaya durak listesinden başlanır. Kapak bir yol tarifi vermez.</p>
      <p><a href="duraklar.html">Durak listesini aç</a></p>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Kent notları” yazar. Büyük başlık “Serhat'ın kent notları”dır. Altında altı maddelik bir liste vardır. “Kapak” düz ve kalındır, altı çizili değildir, tıklanınca başka sayfa açmaz. Diğer beş ad mavi ve altı çizilidir. “Durak listesini aç” da mavidir. O bağlantı tıklanınca sekme değişir. `duraklar.html` gelince büyük başlık “Durak listesi” olur. Geri dönmek için o sayfadaki “Kapak” bağlantısı kullanılır. Adres çubuğunda dosya adı `index.html` iken kapak, `duraklar.html` iken durak listesi okunur.

## Diğer beş dosya

Her dosyada gezintinin aynı altı maddesi vardır. Yalnızca açık olan sayfa `<strong>` içine alınır. Gövde, o sayfanın kısa hâlidir. 24–28. günlerde yazılan uzun belgeler bu klasöre kendi adlarıyla da konabilir. Bugünkü kısa gövde, bağlantının çalıştığını görmek için yeter. Uzun gövde konursa gezinti yine aşağıdaki bağlantıları taşır.

`hakkinda.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hakkında</title>
  </head>
  <body>
    <header>
      <h1>Hakkında</h1>
    </header>
    <nav>
      <ul>
        <li><a href="index.html">Kapak</a></li>
        <li><strong>Hakkında</strong></li>
        <li><a href="duraklar.html">Durak listesi</a></li>
        <li><a href="iletisim.html">İletişim</a></li>
        <li><a href="kiyas.html">Kıyaslama</a></li>
        <li><a href="sorular.html">Sorular</a></li>
      </ul>
    </nav>
    <main>
      <p>Notu yazan <strong>Serhat</strong>’tır. Notlar İstanbul, İzmir, Trabzon ve Van’ı aynı defterde tutar.</p>
      <ul>
        <li>İstanbul</li>
        <li>İzmir</li>
        <li>Trabzon</li>
        <li>Van</li>
      </ul>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Hakkında”, sayfada en büyük satır “Hakkında”dır. Listede “Hakkında” kalın ve çizgisizdir. “Kapak” ve “Durak listesi” mavidir. Dört kent daireli ikinci bir listede durur. “Kapak” tıklanınca `index.html` açılır. Büyük başlık yeniden “Serhat'ın kent notları” olur.

`duraklar.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durak listesi</title>
  </head>
  <body>
    <header>
      <h1>Durak listesi</h1>
    </header>
    <nav>
      <ul>
        <li><a href="index.html">Kapak</a></li>
        <li><a href="hakkinda.html">Hakkında</a></li>
        <li><strong>Durak listesi</strong></li>
        <li><a href="iletisim.html">İletişim</a></li>
        <li><a href="kiyas.html">Kıyaslama</a></li>
        <li><a href="sorular.html">Sorular</a></li>
      </ul>
    </nav>
    <main>
      <ol>
        <li>İstanbul</li>
        <li>Trabzon</li>
        <li>Van</li>
        <li>İzmir</li>
      </ol>
      <p><a href="kiyas.html">Bu dört kenti tabloda kıyasla</a></p>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Büyük başlık “Durak listesi”dir. Gezintide bu ad kalındır. Numaralı sıra 1 İstanbul, 2 Trabzon, 3 Van, 4 İzmir diye iner. “Bu dört kenti tabloda kıyasla” tıklanınca `kiyas.html` açılır. Gezintideki “Kıyaslama” ile gövdedeki cümle aynı dosyaya gider. İkisi de mavidir. Sözleri farklıdır.

`iletisim.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İletişim</title>
  </head>
  <body>
    <header>
      <h1>İletişim</h1>
    </header>
    <nav>
      <ul>
        <li><a href="index.html">Kapak</a></li>
        <li><a href="hakkinda.html">Hakkında</a></li>
        <li><a href="duraklar.html">Durak listesi</a></li>
        <li><strong>İletişim</strong></li>
        <li><a href="kiyas.html">Kıyaslama</a></li>
        <li><a href="sorular.html">Sorular</a></li>
      </ul>
    </nav>
    <main>
      <form action="iletisim.html" method="get">
        <p>
          <label for="ad">Ad (zorunlu)</label>
          <input id="ad" name="ad" type="text" value="Serhat" required />
        </p>
        <p>
          <label for="kent">Kent (zorunlu)</label>
          <select id="kent" name="kent" required>
            <option value="">Seçin</option>
            <option value="istanbul">İstanbul</option>
            <option value="izmir">İzmir</option>
            <option value="trabzon">Trabzon</option>
            <option value="van">Van</option>
          </select>
        </p>
        <p>
          <button type="submit">İletiyi adres çubuğuna yaz</button>
        </p>
      </form>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
“İletişim” büyük başlıktır ve gezintide kalındır. Ad kutusunda “Serhat” vardır. Kent listesi “Seçin” ile açılır. Van seçilip düğmeye basılınca aynı dosya yenilenir. Adresin sonunda `ad` ve `kent=van` görünür. Gezinti yerinde kalır. Başka dosyaya geçilmez. “Sorular” tıklanınca form kaybolur, soru sayfası gelir.

`kiyas.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kıyaslama</title>
  </head>
  <body>
    <header>
      <h1>Kıyaslama</h1>
    </header>
    <nav>
      <ul>
        <li><a href="index.html">Kapak</a></li>
        <li><a href="hakkinda.html">Hakkında</a></li>
        <li><a href="duraklar.html">Durak listesi</a></li>
        <li><a href="iletisim.html">İletişim</a></li>
        <li><strong>Kıyaslama</strong></li>
        <li><a href="sorular.html">Sorular</a></li>
      </ul>
    </nav>
    <main>
      <table>
        <caption>Plakalar</caption>
        <thead>
          <tr>
            <th scope="col">Kent</th>
            <th scope="col">Plaka</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <th scope="row">İstanbul</th>
            <td>34</td>
          </tr>
          <tr>
            <th scope="row">İzmir</th>
            <td>35</td>
          </tr>
          <tr>
            <th scope="row">Trabzon</th>
            <td>61</td>
          </tr>
          <tr>
            <th scope="row">Van</th>
            <td>65</td>
          </tr>
        </tbody>
      </table>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
“Kıyaslama” büyük başlık ve gezintide kalın bir maddedir. Tablonun adı “Plakalar”dır. İstanbul 34, İzmir 35, Trabzon 61, Van 65 ile aynı satırdadır. Çerçeve yoktur. Kent adları kalın, plakalar düzdür.

`sorular.html`:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sorular</title>
  </head>
  <body>
    <header>
      <h1>Sorular</h1>
    </header>
    <nav>
      <ul>
        <li><a href="index.html">Kapak</a></li>
        <li><a href="hakkinda.html">Hakkında</a></li>
        <li><a href="duraklar.html">Durak listesi</a></li>
        <li><a href="iletisim.html">İletişim</a></li>
        <li><a href="kiyas.html">Kıyaslama</a></li>
        <li><strong>Sorular</strong></li>
      </ul>
    </nav>
    <main>
      <h2 id="kirik">Fotoğraf neden kırık görünür?</h2>
      <p>Görsel dosyası, HTML dosyasıyla aynı klasörde değilse kırık simge görünür.</p>
      <p><a href="index.html">Kapağa dön</a></p>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
“Sorular” en büyük satırdır. Gezintide bu ad kalın ve çizgisizdir. Altında daha küçük bir soru başlığı ve bir paragraf vardır. “Kapağa dön” tıklanınca `index.html` açılır. Gezintideki “Kapak” ile aynı dosyaya gider. Soru sayfası kapanır, kapaktaki “Kapak” kelimesi yeniden kalın olur.

## Sık yapılan hata

Adresin başına eğik çizgi koymak, dosyayı klasörün içinde değil, diskin kökünde aratır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kökte aranan</title>
  </head>
  <body>
    <h1>Kapak</h1>
    <p><a href="/hakkinda.html">Hakkında</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
“Hakkında” mavidir. Tıklanınca aynı klasördeki dosya açılmaz. Tarayıcı, diskin veya sitenin kökünde `hakkinda.html` arar. Çoğu zaman “dosya bulunamadı” sayfası gelir. Dosya klasörde durduğu hâlde bulunmamış sayılır.

Doğru adres, klasördeki dosyanın adıdır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanındaki dosya</title>
  </head>
  <body>
    <h1>Kapak</h1>
    <p><a href="hakkinda.html">Hakkında</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
`hakkinda.html` aynı klasördeyse tıklama o dosyayı açar. Büyük başlık “Hakkında” olur. Adres çubuğunun sonunda `hakkinda.html` okunur. Başında yalnızca bir klasör yolu vardır. Kökten başlayan tek başına bir `hakkinda.html` aranmaz.

İkinci hata, bütün maddeleri bağlantı yapmaktır. Açık sayfanın adına tıklanınca aynı sayfa yeniden yüklenir ve gezinti zıplar. Açık sayfa kalın yazı olarak kalır. Üçüncü hata, bir sayfada `Hakkinda.html`, dosya adında `hakkinda.html` yazmaktır. Büyük harf, birçok sistemde başka bir dosya adıdır. Altı dosyanın adı, yukarıdaki küçük harflerle birebir aynı olur.

## Egzersizler

1. Altı dosyayı aynı klasöre kaydedin. `index.html` açıldığında “Kapak” kalın ve çizgisiz, diğer beş ad mavi görünsün. “Hakkında” tıklanınca büyük başlık “Hakkında” olsun ve bu kez o kelime kalın dursun.
2. Durak listesindeki “Bu dört kenti tabloda kıyasla” tıklanınca plaka tablosu açılsın. İstanbul’un sağında 34, Van’ın sağında 65 görünsün. Oradan “Sorular” ile soru sayfasına, “Kapağa dön” ile yeniden kapağa geçilsin.
3. Bir bağlantının adresine başa eğik çizgi koyun. Dosya bulunamasın. Eğik çizgiyi silin. Aynı tıklama, klasördeki dosyayı açsın.

[← Önceki gün](../28-faq/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../30-closing/ders.md)
