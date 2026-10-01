# 30. Gün — Kapanış sayfası: iskelet, başlık, liste, bağlantı, görsel, tablo ve form

Bu gün, otuzuncu sayfada iskeleti, başlığı, listeyi, bağlantıyı, görseli, tabloyu ve formu bir kez daha aynı belgede toplar. Yeni bir etiket yoktur. 29. gündeki site altı dosyayı birbirine bağladı. Bu sayfa tek dosyadır ve o parçaların her birinin ekranda ayrı ayrı göründüğünü bitirir. Parça eksikse sayfa kapanış sayfası olmaz.

## Yedi parça aynı belgede

İskelet, dosyanın türünü ve dilini kurar. Başlık, sayfanın adını koyar. Liste, dört kenti dizer. Bağlantı, başka bir adrese gider. Görsel, klasördeki dosyayı çağırır. Tablo, kenti plakayla hizalar. Form, bir kenti adres çubuğuna yazar.

Belge `kapanis.html` adıyla kaydedilir. `kapanis.jpg` aynı klasöre konursa görsel belirir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapanış</title>
  </head>
  <body>
    <header>
      <h1>Kapanış</h1>
      <p>
        Bu sayfa
        <time datetime="2026-10-01">1 Ekim 2026</time>
        gününün notudur.
      </p>
    </header>
    <nav>
      <ul>
        <li><a href="#liste">Liste</a></li>
        <li><a href="#tablo">Tablo</a></li>
        <li><a href="#form">Form</a></li>
      </ul>
    </nav>
    <main>
      <h2 id="liste">Liste</h2>
      <p>Dört kent, bir öncelik sırası olmadan durur:</p>
      <ul>
        <li>İstanbul</li>
        <li>İzmir</li>
        <li>Trabzon</li>
        <li>Van</li>
      </ul>
      <p>
        Sıranın numaralı hâli ayrı bir sayfadadır.
        <a href="duraklar.html">Durak listesini aç</a>
      </p>
      <figure>
        <img src="kapanis.jpg" alt="Dört kentin adının yazdığı bir not kâğıdı" width="320" height="180" />
        <figcaption>Kapanış görseli. Dosya yoksa alternatif metin burada durur.</figcaption>
      </figure>
      <h2 id="tablo">Tablo</h2>
      <table>
        <caption>Kapanıştaki plakalar</caption>
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
      <h2 id="form">Form</h2>
      <form action="kapanis.html" method="get">
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
          <button type="submit">Kenti adres çubuğuna yaz</button>
        </p>
      </form>
      <blockquote>
        <p>İskelet, başlık, liste, bağlantı, görsel, tablo ve form bu dosyada birlikte durur.</p>
      </blockquote>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Kapanış” yazar. Sayfanın en büyük satırı da “Kapanış”tır. Onun altında “1 Ekim 2026” normal puntoda, cümlenin içindedir. Takvim açılmaz. Üç mavi bağlantı daireli listededir: Liste, Tablo, Form. “Tablo” tıklanınca sayfa tablo başlığına kayar. Dosya değişmez.

“Liste” orta boy bir başlıktır. Altında İstanbul, İzmir, Trabzon ve Van daireli dört satır olarak durur. Numara yoktur. “Durak listesini aç” mavidir. `duraklar.html` aynı klasördeyse tıklanınca 29. günün durak sayfası gelir. Dosya yoksa tarayıcı “dosya bulunamadı” der. Bağlantı yine de mavi durur.

Görsel, 320’ye 180 piksellik bir alandır. `kapanis.jpg` duruyorsa fotoğraf görünür, “Dört kentin adının yazdığı bir not kâğıdı” yazılmaz. Dosya yoksa kırık simge ve bu cümle görünür. Her iki durumda da altında “Kapanış görseli. Dosya yoksa alternatif metin burada durur.” alt yazısı vardır.

“Tablo” başlığının altında tablonun adı “Kapanıştaki plakalar” yazar. “Kent” ve “Plaka” kalındır. İstanbul 34, İzmir 35, Trabzon 61, Van 65 ile aynı satırda durur. Kent adları da kalındır. Çerçeve yoktur. 65, Van’ın sağındadır.

“Form” başlığının altında “Kent (zorunlu)” ve “Seçin” yazılı bir liste vardır. “Kent (zorunlu)” yazısına tıklanınca odak listeye gelir. Liste boşken düğme adresi değiştirmez. Tarayıcı uyarı verir. Trabzon seçilip “Kenti adres çubuğuna yaz” tıklanınca sayfa yenilenir. Adresin sonunda `kent=trabzon` görünür. Başlık, liste, görsel ve tablo yerinde kalır.

Alıntı girintilidir: “İskelet, başlık, liste, bağlantı, görsel, tablo ve form bu dosyada birlikte durur.” En altta “Notu yazan: Serhat” yazar. Renkli şerit yoktur. Yedi parçanın her biri kendi yerinde, yukarıdan aşağı okunur.

Kaynakta iskelet de durur. `DOCTYPE` satırı, `lang="tr"` ve karakter satırı ekranda kelime olarak görünmez. Sayfa kaynağı açılınca üçü de dosyanın başındadır. Türkçe harfler, “İstanbul” ve “İzmir” adlarında bozulmadan durur.

## Parça silinince sayfa eksik kalır

Aşağıdaki kısa belge, tablosu ve formu olmayan bir denemedir. Kapanış sayfası bu hâlde bitmiş sayılmaz. Ekranda neyin kaldığı bilinçli olarak görülür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Eksik kapanış</title>
  </head>
  <body>
    <h1>Kapanış</h1>
    <ul>
      <li>İstanbul</li>
      <li>Van</li>
    </ul>
    <p><a href="https://example.com">Example Domain</a></p>
  </body>
</html>
```

Tarayıcıda görünen:
Büyük “Kapanış”, iki daireli madde ve mavi “Example Domain” vardır. Bağlantı tıklanınca Example Domain sayfası açılır. O sayfada “Example Domain” başlığı durur. Bu kısa belgede fotoğraf, plaka tablosu ve kent listesi yoktur. İskelet, başlık, liste ve bağlantı vardır. Görsel, tablo ve form eksiktir. Kapanış sayfası, `kapanis.html` belgesindeki yedi parçanın tamamı bir aradayken tamamdır.

## Sık yapılan hata

Görseli tablonun içine yazı diye koymak, resmi kaybeder. Formu tablonun dışına ve bağlantının içine almak, düğmeyi başka sayfaya götürür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Karışmış kapanış</title>
  </head>
  <body>
    <h1>Kapanış</h1>
    <table>
      <tr>
        <td>kapanis.jpg</td>
        <td>65</td>
      </tr>
    </table>
    <p>
      <a href="duraklar.html">
        <button type="submit">Duraklara git</button>
      </a>
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Tabloda “kapanis.jpg” diye bir yazı ve “65” yan yana durur. Fotoğraf görünmez. Dosya adı bir hücre metnidir. Alttaki düğme, düğme gibi görünür. Bağlantının içinde olduğu için tıklanınca `duraklar.html` sayfası açılabilir. Form yoktur. Kent seçilmez. Adres çubuğuna `kent=van` yazılmaz. Düğme ile bağlantı birbirinin içine girmiştir. İkisi ayrı işlerdir.

Doğru belgede görsel `<img>` ile, düğme formun içinde, durak sayfası da kendi bağlantısında durur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Ayrılmış kapanış</title>
  </head>
  <body>
    <h1>Kapanış</h1>
    <p><a href="duraklar.html">Durak listesini aç</a></p>
    <img src="kapanis.jpg" alt="Dört kentin adının yazdığı bir not kâğıdı" />
    <table>
      <tr>
        <th scope="row">Van</th>
        <td>65</td>
      </tr>
    </table>
    <form action="kapanis.html" method="get">
      <p>
        <label for="kent">Kent (zorunlu)</label>
        <select id="kent" name="kent" required>
          <option value="">Seçin</option>
          <option value="van">Van</option>
        </select>
      </p>
      <p>
        <button type="submit">Kenti adres çubuğuna yaz</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Durak listesini aç” mavi bir yazıdır. Düğme gibi durmaz. Fotoğraf veya kırık simge ile alternatif metin, tablodan önce görünür. Tabloda “Van” ve “65” aynı satırdadır. “kapanis.jpg” hücrede yazı olarak durmaz. Formda “Van” seçilip düğmeye basılınca adres `kent=van` ile biter. Düğme, durak sayfasını açmaz.

## Egzersizler

1. `kapanis.html` dosyasını açın. Sekmede “Kapanış”, sayfada tek büyük “Kapanış” görünsün. Dört kent daireli listede dursun. “Durak listesini aç” mavi bir bağlantı olsun. Düğme gibi görünmesin.
2. Görsel dosyasını klasörden çıkarın. Kırık simge ve “Dört kentin adının yazdığı bir not kâğıdı” görünsün. Alt yazı görselin altında kalsın. Dosyayı geri koyunca simge kalksın, alt yazı yerinde dursun.
3. Tabloda Van’ın sağında 65 görünsün. Formda kent seçilmeden düğme adresi değiştirmesin. Trabzon seçilince adresin sonunda `kent=trabzon` belirsın. Sayfadaki liste, görsel ve tablo bu yenilemeden sonra da yerinde kalsın.

[← Önceki gün](../29-site/ders.md) · [İçindekiler](../README.md)
