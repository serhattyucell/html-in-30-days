# 25. Gün — Küçük sayfa: durak listesi

Bu gün, notların okunma sırasını numaralı bir listede toplar. 24. gündeki hakkında sayfası kentleri sırasız saymıştı. Bugün sıra bir okuma sırasıdır, bir karayolu değildir. Yeni bir etiket yoktur. Numaralı liste, iç içe maddeler, sayfa içi bağlantı, figür ve bölgeler daha önce kurulmuştu.

## Okuma sırası dört duraktır

Dış liste durakların sırasını, iç liste o durakta bakılacak yerleri tutar. İç listenin sırası zorunlu değilse daire kullanılır.

Belge `duraklar.html` adıyla kaydedilir. `sira.jpg`, dört adı tek kâğıtta gösteren bir çizim olabilir. Dosya yoksa alternatif metin görünür.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Durak listesi</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Durak listesi</h1>
      <p>Okuma sırası: İstanbul, Trabzon, Van, İzmir. Bu bir karayolu haritası değildir.</p>
    </header>
    <nav>
      <ol>
        <li><a href="#istanbul">İstanbul</a></li>
        <li><a href="#trabzon">Trabzon</a></li>
        <li><a href="#van">Van</a></li>
        <li><a href="#izmir">İzmir</a></li>
      </ol>
    </nav>
    <main id="icerik">
      <figure>
        <img src="sira.jpg" alt="Dört durağın okuma sırası: İstanbul, Trabzon, Van, İzmir" width="320" height="180" />
        <figcaption>Okuma sırasının özeti. Çizgi bir yol şeridi değildir.</figcaption>
      </figure>
      <ol>
        <li id="istanbul">
          İstanbul
          <ul>
            <li>Galata Kulesi</li>
            <li>Kapalıçarşı</li>
          </ul>
        </li>
        <li id="trabzon">
          Trabzon
          <ul>
            <li>Kıyı</li>
            <li>Çarşı</li>
          </ul>
        </li>
        <li id="van">
          Van
          <ul>
            <li>Van Gölü</li>
            <li>Van Kalesi</li>
          </ul>
        </li>
        <li id="izmir">
          İzmir
          <ul>
            <li>Saat Kulesi</li>
            <li>Kordon</li>
          </ul>
        </li>
      </ol>
    </main>
    <footer>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Durak listesi” yazar. En üstte “İçeriğe geç”, altında aynı adlı büyük başlık ve “bu bir karayolu haritası değildir” cümlesini içeren paragraf durur. Gezinti numaralıdır: 1 İstanbul, 2 Trabzon, 3 Van, 4 İzmir. Numaraların yanındaki adlar mavi ve altı çizilidir. Tıklanınca sayfa o durağın maddesine kayar. Adresin sonu `#van` gibi bir parça olur.

Figür, gezintinin altında, asıl listeden önce durur. Çizim varsa 320’ye 180 piksellik bir görsel görünür. Yoksa kırık simge ve “Dört durağın okuma sırası: İstanbul, Trabzon, Van, İzmir” yazısı durur. Alt yazı her iki durumda da görselin altındadır.

Asıl liste yeniden 1’den sayar. “1. İstanbul” satırının altında, daha içeride boş daireyle “Galata Kulesi” ve “Kapalıçarşı” vardır. “2. Trabzon”un altında “Kıyı” ve “Çarşı”, “3. Van”ın altında “Van Gölü” ve “Van Kalesi”, “4. İzmir”in altında “Saat Kulesi” ve “Kordon” durur. İç maddeler a, b diye veya 5, 6 diye numaralanmaz. Her kentin alt listesi kendi dairelerini taşır ve bir sonrakine sarkan numara üretmez. En altta “Notu yazan: Serhat” vardır. İki sütun ve yol çizgisi yoktur. Sırayı numaralar anlatır.

## İç liste o durakta kalır

Aşağıdaki kısa belge, yalnızca bir durağın içini sınar. Tam sayfanın kopyası değildir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Van durağı</title>
  </head>
  <body>
    <h1>Tek durak</h1>
    <ol start="3">
      <li>
        Van
        <ul>
          <li>Van Gölü</li>
          <li>Van Kalesi</li>
        </ul>
      </li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Tek madde vardır ve başında “3.” durur. “1.” görünmez. “Van” bu satırdadır. Altında iki daire, “Van Gölü” ve “Van Kalesi”, daha sağdadır. İkisi “4.” ve “5.” olmaz. Bu kısa deneme, tam listedeki Van’ın üçüncü durak olduğunu, göl ile kalenin ise ayrı bir numara sırası olmadığını gösterir.

## Sık yapılan hata

Bakılacak yerleri dış listenin kardeşi yapmak, kuleyi bir durak sayar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kaymış durak</title>
  </head>
  <body>
    <h1>Duraklar</h1>
    <ol>
      <li>İstanbul</li>
      <li>Galata Kulesi</li>
      <li>Kapalıçarşı</li>
      <li>Trabzon</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
Dört numara görünür. “2. Galata Kulesi” ve “3. Kapalıçarşı”, İstanbul’un altı değil, ondan sonraki duraklarmış gibi aynı hizadadır. Trabzon dördüncü durak olur. Okuma sırası bozulur. Kule, ikinci kent sanılır.

Doğru belgede kule, İstanbul maddesinin içindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yerinde durak</title>
  </head>
  <body>
    <h1>Duraklar</h1>
    <ol>
      <li>
        İstanbul
        <ul>
          <li>Galata Kulesi</li>
          <li>Kapalıçarşı</li>
        </ul>
      </li>
      <li>Trabzon</li>
    </ol>
  </body>
</html>
```

Tarayıcıda görünen:
“1. İstanbul” ve “2. Trabzon” aynı hizadadır. Kule ve Kapalıçarşı, İstanbul’un altında, daha sağda, daire ile durur. Trabzon ikinci duraktır. Üçüncü bir kent numarası kuleye verilmez.

## Egzersizler

1. `duraklar.html` dosyasında büyük başlık “Durak listesi” olsun. Numaralı sıra İstanbul, Trabzon, Van, İzmir diye insin. Van’ın altında daireli “Van Gölü” ve “Van Kalesi” görünsün. Bu iki satır 4 ve 5 numara almasın.
2. Üstteki gezintideki “Van” tıklanınca sayfa üçüncü durağa insin. Adresin sonunda `#van` görünsün. Dosya adı değişmesin.
3. Figürde görsel yokken dört durağın adı alternatif metin olarak okunsun. Görsel varken bu cümle kaybolsun, alt yazı “Okuma sırasının özeti” diye görselin altında kalsın.

[← Önceki gün](../24-about/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../26-contact-form/ders.md)
