# 23. Gün — Erişilebilirlik (Accessibility)

Bu gün, ilk yirmi iki gündeki etiketleri, sayfayı başka türlü okuyan kişi de aynı bilgiye ulaşsın diye bir araya getirir. Yeni bir etiket yoktur. Dil, başlık sırası, alternatif metin, etiket bağı, tablo başlığı, bağlantı sözü ve düğme adı zaten öğrenildi. Bugün bunların aynı sayfada, birbirini eksiltmeden durması işlenir. Erişilebilir bir sayfa, renkli bir sayfa demek değildir. Renk ileride CSS konusudur. Bu sayfada anlam, doğru etiketle kurulur.

## Dil, sekme ve içeriğe atlama

Sayfanın dili ve sekme adı, sayfa açılır açılmaz okunacak iki bilgidir. En üstteki bağlantı, uzun bir notta gezintiyi atlayıp konuya iner.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notları</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Serhat'ın kent notları</h1>
    </header>
    <nav>
      <ul>
        <li><a href="#istanbul">İstanbul</a></li>
        <li><a href="#van">Van</a></li>
      </ul>
    </nav>
    <main id="icerik">
      <h2 id="istanbul">İstanbul</h2>
      <p>Boğaz kenti iki yakaya ayırır.</p>
      <h2 id="van">Van</h2>
      <p>Van Gölü geniştir.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Kent notları” yazar. Sayfanın en üstünde, büyük başlıktan önce, mavi ve altı çizili “İçeriğe geç” vardır. Bu bağlantı gizlenmez. Onu ekranın dışına almak ileride CSS konusudur. Bugün görünür kalması, atlamanın gerçekten çalıştığını gösterir. Onun altında “Serhat'ın kent notları” en büyük satırdır. İki bağlantı daireli listede durur. “İçeriğe geç” tıklanınca sayfa “İstanbul” bölümünün başladığı asıl konuya kayar. Üst başlık küçük bir pencerede yukarıda kalabilir. `lang="tr"` ekranda bir kelime olarak durmaz. Yazım denetimi ve sesli okuma, sayfayı Türkçe bir metin olarak alır.

`<title>` ile `<h1>` aynı işi yapmaz. Sekme kalabalıkken “Kent notları” hangi dosyanın açık olduğunu söyler. Sayfadaki `<h1>` ise notun adıdır. İkisi birden boş bırakılırsa sekmede dosya yolu, sayfada ise düz bir ilk paragraf kalır. Hangisinin ana ad olduğu seçilemez.

## Başlık sırası

Düzey atlamak, punto için küçük bir satır aramak demekti. Erişilebilir sayfada bu atlama, içindekilerde bir basamağın yok olmasıdır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başlık sırası</title>
  </head>
  <body>
    <header>
      <h1>Serhat'ın kent notları</h1>
    </header>
    <main>
      <h2>İzmir</h2>
      <h3>Saat Kulesi</h3>
      <p>Kule meydanın ortasındadır.</p>
      <h2>Trabzon</h2>
      <p>Kent Karadeniz kıyısındadır.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
“Serhat'ın kent notları” en büyüktür. “İzmir” ve “Trabzon” aynı, orta büyüklüktedir. “Saat Kulesi” ikisinden küçüktür ve yalnızca İzmir’in altındadır. Trabzon, kuleyle aynı küçüklükte değildir. Dört satır içindekiler gibi okunur: bir ana ad, iki kent, bir kentin altında bir yer. Düzey `<h4>` yapılsaydı kule, İzmir’in alt konusu değil, dip bir not gibi küçülürdü. Punto büyütmek ileride CSS konusudur. Sıra bugün bozulmaz.

## Görselin yerine geçen cümle

Bilgi taşıyan fotoğrafta `alt` doludur. Alt yazı ise herkesin gördüğü cümledir. İkisi birden durur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Görselin metni</title>
  </head>
  <body>
    <main>
      <h1>Van</h1>
      <figure>
        <img src="van-golu.jpg" alt="Van Gölü kıyısı" />
        <figcaption>Van Gölü, kente kıyıdan bakılınca.</figcaption>
      </figure>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Fotoğraf klasördeyse göl görünür ve “Van Gölü kıyısı” yazılmaz. Altında “Van Gölü, kente kıyıdan bakılınca.” satırı durur. Fotoğraf yoksa kırık simge, yanında “Van Gölü kıyısı”, altında yine alt yazı vardır. `alt` ile alt yazı aynı cümlenin kopyası olmak zorunda değildir. Biri resmin yerine geçer. Öteki resmin yanında duran açıklamadır. `alt="van-golu.jpg"` yazılırsa resim kırıkken ekranda bir dosya adı kalır. Bu, kıyıyı tarif etmez.

## Formda ad, kutuya bağlıdır

Zorunlu alan, yalnız kırmızı çerçeveyle belli edilmez. Çerçeve ileride CSS konusudur. “Zorunlu” kelimesi etiketin içindedir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı form</title>
  </head>
  <body>
    <main>
      <h1>Kısa soru</h1>
      <form action="soru.html" method="get">
        <p>
          <label for="ad">Ad (zorunlu)</label>
          <input id="ad" name="ad" type="text" required />
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
          <button type="submit">Notu gönder</button>
        </p>
      </form>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
“Ad (zorunlu)” yazısına tıklanınca imleç kutuya gider. “Kent (zorunlu)” yazısına tıklanınca liste açılabilir veya odak listeye gelir. İkisi boşken “Notu gönder” tıklanınca sayfa yenilenmez. Tarayıcı ilk boş zorunlu alanda kendi uyarısını gösterir. Ad doldurulup kent seçilince adres `ad` ve `kent` değerlerini taşır. Düğmede “Gönder” yerine “Notu gönder” yazar. Ne gönderildiği düğmenin üstündedir. Kırmızı bir yıldız yoktur. Zorunluluk, parantez içindeki kelimeden okunur.

## Tablonun başlığı veriye bağlanır

Plaka hücresinin üstündeki “Plaka”, o sütunun adıdır. Sol baştaki kent adı da satırın adıdır. `scope` ekranda görünmez. Bağı o söyler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Okunur tablo</title>
  </head>
  <body>
    <main>
      <h1>Plakalar</h1>
      <table>
        <caption>Dört kentin plaka kodu</caption>
        <thead>
          <tr>
            <th scope="col">Kent</th>
            <th scope="col">Plaka</th>
          </tr>
        </thead>
        <tbody>
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
  </body>
</html>
```

Tarayıcıda görünen:
Tablonun üstünde “Dört kentin plaka kodu” yazar. “Kent” ve “Plaka” kalın, çoğu tarayıcıda ortalıdır. “Trabzon” ve “Van” solda kalındır. 61 ve 65 düz rakamlardır. Çerçeve yoktur. Trabzon ile 61 aynı satırdadır. Sesli okuma, “61” başına “Plaka” sütununu ve “Trabzon” satırını bağlar. Bütün hücreler düz `<td>` olsaydı ekrandaki hiza benzer kalır, kalınlık kalkardı. Hangi rakamın hangi kentin plakası olduğu yalnızca yan yana duruşa kalırdı.

## Aynı sayfada toplanmış not

Aşağıdaki belge, bu günün işinin tamamıdır. Üstteki parçalar burada tek dosyada durur. Yeni bir etiket eklenmemiştir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kent notları</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Serhat'ın kent notları</h1>
      <p>
        Güncelleme:
        <time datetime="2026-10-01">1 Ekim 2026</time>
      </p>
    </header>
    <nav>
      <ul>
        <li><a href="#izmir">İzmir</a></li>
        <li><a href="#tablo">Plaka tablosu</a></li>
        <li><a href="#soru">Kısa soru</a></li>
      </ul>
    </nav>
    <main id="icerik">
      <article>
        <h2 id="izmir">İzmir</h2>
        <p>Saat Kulesi, <strong>meydanın ortasında</strong> durur.</p>
        <figure>
          <img src="izmir.jpg" alt="İzmir Saat Kulesi" />
          <figcaption>İzmir’de Saat Kulesi.</figcaption>
        </figure>
      </article>
      <section>
        <h2 id="tablo">Plaka tablosu</h2>
        <table>
          <caption>Notta duran kentlerin plakası</caption>
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
      </section>
      <section>
        <h2 id="soru">Kısa soru</h2>
        <form action="erisilebilir.html" method="get">
          <p>
            <label for="ad">Ad (zorunlu)</label>
            <input id="ad" name="ad" type="text" required />
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
            <button type="submit">Notu gönder</button>
          </p>
        </form>
      </section>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte “İçeriğe geç” bağlantısı vardır. Altında büyük “Serhat'ın kent notları” ve “Güncelleme: 1 Ekim 2026” satırı durur. Gün, kalın veya çerçeveli değildir. Üç maddelik mavi bir gezinti gelir. Asıl konuda “İzmir” başlığı, vurgulu bir cümle ve fotoğraf vardır. Fotoğraf yoksa kırık simge ile “İzmir Saat Kulesi”, altında “İzmir’de Saat Kulesi.” okunur. Sonra plaka tablosu gelir. Dört kent, 34, 35, 61 ve 65 ile aynı satırda eşleşir. “Kent” ve kent adları kalındır. En altta form vardır. İki alanda da “(zorunlu)” okunur. Düğmede “Notu gönder” yazar. Sayfanın sonunda “Notu yazan: Serhat” vardır. Renkli sütun, şerit ve çerçeve yoktur. “İçeriğe geç” tıklanınca gezinti atlanır, İzmir bölümü üste gelir. Form boş gönderilirse adres değişmez, tarayıcı uyarı verir.

## Sık yapılan hata

Bağlantının görünen sözünü “tıklayın” yapmak, o sözü sıradan ve aynı kılmaktır. Üç tane “tıklayın” alt alta durursa her biri mavi olsa da hedef okunmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Boş bağlantı sözü</title>
  </head>
  <body>
    <h1>Notlar</h1>
    <ul>
      <li><a href="#izmir">tıklayın</a></li>
      <li><a href="#van">tıklayın</a></li>
    </ul>
    <h2 id="izmir">İzmir</h2>
    <p>Kule bu bölümde.</p>
    <h2 id="van">Van</h2>
    <p>Göl bu bölümde.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki mavi “tıklayın” satırı vardır. Fareyle bakınca biri İzmir’e, öteki Van’a gider. Sözlerin kendisi bunu söylemez. İkisi de aynı kelimedir.

Doğru belgede her bağlantının sözü hedefin adıdır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Anlaşılır bağlantı</title>
  </head>
  <body>
    <h1>Notlar</h1>
    <ul>
      <li><a href="#izmir">İzmir</a></li>
      <li><a href="#van">Van</a></li>
    </ul>
    <h2 id="izmir">İzmir</h2>
    <p>Kule bu bölümde.</p>
    <h2 id="van">Van</h2>
    <p>Göl bu bölümde.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” ve “Van” ayrı ayrı mavi durur. Birine tıklanınca aynı adlı başlık pencerenin üstüne gelir.

İkinci hata, zorunlu alanı yalnızca `required` ile bırakıp etikete hiçbir kelime koymamaktır. Uyarı, düğmeye basılınca çıkar. Baskısından önce kutunun neden boş kalamayacağı okunmaz. “(zorunlu)” sözü etikette durur.

Üçüncü hata, fotoğrafın `alt` değerini boş bırakıp bilgiyi yalnızca renkli bir çerçeveye emanet etmektir. Çerçeve bu rehberde yoktur. Boş `alt`, bilgi taşıyan kuleyi sessiz bir simgeye çevirir.

## Egzersizler

1. Sayfanın en üstüne “İçeriğe geç” koyun. Tıklanınca gezinti atlanıp asıl konunun başlığı üste gelsin. Bağlantı ekranda görünsün. Sekmede “Kent notları”, sayfada tek bir büyük “Serhat'ın kent notları” dursun.
2. İzmir fotoğrafını kaldırın veya adını değiştirin. Kırık simgenin yanında “İzmir Saat Kulesi” okunsun. Dosya adının kendisi alternatif metin olmasın. Altında figürün alt yazısı da görünsün.
3. Formda “Ad (zorunlu)” yazısına tıklayınca imleç kutuya gelsin. Alan boşken “Notu gönder” adresi değiştirmesin. Bir kent seçilip ad yazılına kadar tarayıcı uyarı versin.

[← Önceki gün](../22-attributes/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../24-about/ders.md)
