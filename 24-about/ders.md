# 24. Gün — Küçük sayfa: hakkında

Bu gün, dört kentin notunu tutan sayfanın kim olduğunu tek belgede anlatır. Yeni bir etiket yoktur. Üst baş, gezinti, asıl yazı, vurgu, figür, zaman ve alt bilgi 1. günden 23. güne kadar kurulan parçalardır. İş, bu parçaları “hakkında” sayfasında yan yana, kopya cümleler olmadan durdurmaktır.

## Sayfa neyin hakkında

Hakkında sayfası, kentleri anlatmaz. Sayfayı kimin tuttuğunu, hangi dört kentin notlarda durduğunu ve notun hangi güne ait olduğunu söyler.

Aşağıdaki belge `hakkinda.html` adıyla kaydedilir. `serhat.jpg` aynı klasöre konursa portre görünür. Konmazsa alternatif metin onun yerini tutar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hakkında</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Hakkında</h1>
      <p>
        Bu notlar
        <time datetime="2026-10-01">1 Ekim 2026</time>
        günü bu hâli aldı.
      </p>
    </header>
    <nav>
      <ul>
        <li><a href="#amac">Amaç</a></li>
        <li><a href="#kentler">Dört kent</a></li>
        <li><a href="#yazar">Notu yazan</a></li>
      </ul>
    </nav>
    <main id="icerik">
      <article>
        <h2 id="amac">Amaç</h2>
        <p>
          Bu sayfa bir seyahat acentesi değildir. Serhat’ın HTML çalışırken
          kurduğu kent notlarının kapağıdır. Notlar bir yolu tarif etmez.
          Dört adı aynı belgede tutar.
        </p>
        <h2 id="kentler">Dört kent</h2>
        <p>Notların dışına şu dört ad çıkar:</p>
        <ul>
          <li>İstanbul, Boğaz’ın iki yakasında</li>
          <li>İzmir, Ege kıyısında</li>
          <li>Trabzon, Karadeniz kıyısında</li>
          <li>Van, gölün kıyısında</li>
        </ul>
        <p>
          Sıra bir öncelik değildir. Bu yüzden liste numaralı değildir.
          Durak sırası ayrı bir sayfanın işidir.
        </p>
        <h2 id="yazar">Notu yazan</h2>
        <figure>
          <img src="serhat.jpg" alt="Serhat’ın not defterinin kapağı" width="320" height="200" />
          <figcaption>Not defteri. Fotoğraf yoksa bu satır yerinde kalır.</figcaption>
        </figure>
        <p>
          Notu yazan <strong>Serhat</strong>’tır. Bu ad bir imzadır.
          Bir adres, bir yaş veya bir iş yeri bu sayfada yoktur.
        </p>
        <blockquote>
          <p>Dört kent aynı defterde durur. Defter bir güzergâh değildir.</p>
        </blockquote>
      </article>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Hakkında” yazar. En üstte mavi “İçeriğe geç” vardır. Onun altında sayfanın en büyük satırı yine “Hakkında”dır. Hemen altındaki cümlede “1 Ekim 2026” normal puntoda, günün cümlesinin içinde durur. Takvim açılmaz. Üç maddelik gezinti mavi ve dairelidir. “Amaç” tıklanınca o başlık üste kayar.

“Amaç” orta boy bir başlıktır. Altındaki paragraf, sayfanın acente olmadığını ve dört adı bir arada tuttuğunu söyler. “Dört kent” başlığının altında, madde işaretli dört satır vardır. Numara yoktur. İstanbul, İzmir, Trabzon ve Van aynı girintidedir. Her satırda kentin hangi suyla anıldığı da yazılıdır. Sonraki paragraf, bu sıranın bir yolculuk olmadığını söyler.

“Notu yazan” başlığının altında 320’ye 200 piksellik bir alan vardır. `serhat.jpg` duruyorsa fotoğraf görünür, alternatif metin görünmez. Dosya yoksa kırık simge ve “Serhat’ın not defterinin kapağı” okunur. Her iki durumda da altında “Not defteri. Fotoğraf yoksa bu satır yerinde kalır.” alt yazısı vardır. “Serhat” kelimesi kalındır. Cümlenin geri kalanı düzdür. Alıntı girintilidir: “Dört kent aynı defterde durur. Defter bir güzergâh değildir.” En altta “Notu yazan: Serhat” bir kez daha, alt bilgide durur. Renkli bant ve iki sütun yoktur.

## Gezinti, sayfanın içindeki üç ada iner

Hakkında sayfası henüz başka dosyalara gitmez. 29. gün dosyaları birbirine bağlar. Bugün gezinti, bu belgenin üç bölümüne iner. Böylece uzun yazıda başlık aranmaz.

Parça tek başına da açılır. Aşağıdaki kısa belge, yalnızca gezintinin kaydırdığını sınamak içindir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Hakkında gezintisi</title>
  </head>
  <body>
    <header>
      <h1>Hakkında</h1>
    </header>
    <nav>
      <ul>
        <li><a href="#yazar">Notu yazan</a></li>
      </ul>
    </nav>
    <main>
      <h2 id="yazar">Notu yazan</h2>
      <p>Notu yazan Serhat’tır.</p>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
“Hakkında” büyük, “Notu yazan” bağlantısı mavidir. Pencere kısa tutulursa bağlantıya tıklayınca “Notu yazan” başlığı üste gelir. Adresin sonunda `#yazar` vardır. Sekme adı “Hakkında gezintisi” olarak kalır. Dosya değişmez.

## Sık yapılan hata

Hakkında sayfasını ikinci bir ana başlıkla iki belgeye bölmek, kapağın adını siler.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İki kapak</title>
  </head>
  <body>
    <h1>Hakkında</h1>
    <h1>Serhat</h1>
    <p>Notlar dört kent üzerine.</p>
  </body>
</html>
```

Tarayıcıda görünen:
İki satır da en büyük puntodadır. “Hakkında” ve “Serhat” aynı düzeyde yarışır. Sayfanın bir kapağı, sonra bir ikinci kapağı varmış gibi durur. Paragraf ikisinin de altında, hangisine ait olduğu belirsiz biçimde kalır.

Doğru belgede tek ana ad vardır. İmza, vurgu veya alt bilgi olarak durur. Dört kent bir liste olarak durur:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek kapak</title>
  </head>
  <body>
    <header>
      <h1>Hakkında</h1>
    </header>
    <main>
      <h2>Notu yazan</h2>
      <p>Notu yazan <strong>Serhat</strong>’tır.</p>
      <h2>Dört kent</h2>
      <ul>
        <li>İstanbul</li>
        <li>İzmir</li>
        <li>Trabzon</li>
        <li>Van</li>
      </ul>
    </main>
  </body>
</html>
```

Tarayıcıda görünen:
Yalnızca “Hakkında” en büyük satırdır. “Notu yazan” ve “Dört kent” ondan küçüktür ve birbiriyle aynı boydadır. “Serhat” kalındır ama başlık kadar büyük değildir. Dört kent daireli listededir.

## Egzersizler

1. `hakkinda.html` dosyasını kurun. Sekmede “Hakkında”, sayfada tek büyük “Hakkında” görünsün. Dört kent daireli listede, numarası olmadan alt alta dursun.
2. Aynı sayfada bir figür olsun. Fotoğraf yokken “Serhat’ın not defterinin kapağı” okunsun. Alt yazı fotoğrafın altında, figürün dışında kalan bir paragraf gibi kopuk durmasın.
3. “1 Ekim 2026” cümlenin içinde normal puntoda görünsün. O yazıya tıklanınca takvim açılmasın. Sayfanın en altında “Notu yazan: Serhat” ayrı bir alt bilgi olarak dursun.

[← Önceki gün](../23-accessibility/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../25-stop-list/ders.md)
