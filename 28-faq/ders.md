# 28. Gün — Küçük sayfa: sık sorulan sorular

Bu gün, notları okurken çıkan beş soruyu aynı sayfada cevaplar. 27. gündeki tablo kentleri ölçüyordu. Bugün ölçülen şey, sayfanın neden böyle göründüğüdür. Yeni bir etiket yoktur. Soru bir başlıktır, cevap bir paragraftır, soruların listesi sayfa içi bağlantıdır. Açılıp kapanan gizli bir kutu bu belgede kurulmaz. Bütün cevaplar açıktır.

## Beş soru, beş başlık

Üstteki liste, alttaki başlıklara iner. Cevap, başlığın hemen altında durur. Cevabı görmek için ikinci bir tıklama gerekmez.

Belge `sorular.html` adıyla kaydedilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Sık sorulan sorular</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>Sık sorulan sorular</h1>
      <p>Cevaplar bu sayfada açıktır. Bir soruya inmek, cevabı ortaya çıkarmak değildir. Cevap zaten oradadır.</p>
    </header>
    <nav>
      <ol>
        <li><a href="#yol">Notlar bir yol tarifi midir?</a></li>
        <li><a href="#kirik">Fotoğraf neden kırık görünür?</a></li>
        <li><a href="#form">Form neden ileti göndermez?</a></li>
        <li><a href="#cizgi">Tabloda çizgi neden yoktur?</a></li>
        <li><a href="#kent">Hangi kentler vardır?</a></li>
      </ol>
    </nav>
    <main id="icerik">
      <article>
        <h2 id="yol">Notlar bir yol tarifi midir?</h2>
        <p>
          Değildir. İstanbul, Trabzon, Van ve İzmir bir okuma sırasıdır.
          Dört ad, aynı karayolunun durakları diye yazılmamıştır.
        </p>
        <h2 id="kirik">Fotoğraf neden kırık görünür?</h2>
        <p>
          Sayfa, fotoğrafı içine gömmez. <code>sira.jpg</code> veya
          <code>izmir.jpg</code> adlı dosya HTML ile aynı klasörde yoksa
          tarayıcı kırık bir simge ve alternatif metni gösterir.
          Dosya doğru adla yanına konunca simge kalkar, resim gelir.
        </p>
        <h2 id="form">Form neden ileti göndermez?</h2>
        <p>
          Bu notlar bir sunucuya bağlı değildir. Düğme, yazılanları
          adres çubuğuna ekler. <code>serhat@example.com</code>
          bir örnektir. Posta kutusu açılmaz, ileti gitmez.
        </p>
        <blockquote>
          <p>Paket adresin sonunda duruyorsa form, bu dersin ölçüsünde çalışmıştır.</p>
        </blockquote>
        <h2 id="cizgi">Tabloda çizgi neden yoktur?</h2>
        <p>
          Çizgi bir stil işidir ve ileride CSS konusudur. Kent ile plaka
          aynı satırda ise tablo görevini yapmıştır. 34 İstanbul’un,
          65 Van’ın karşısındadır.
        </p>
        <h2 id="kent">Hangi kentler vardır?</h2>
        <p>Notlarda dört ad vardır:</p>
        <ul>
          <li>İstanbul</li>
          <li>İzmir</li>
          <li>Trabzon</li>
          <li>Van</li>
        </ul>
      </article>
    </main>
    <footer>
      <p><a href="#yol">İlk soruya dön</a></p>
      <p>Notu yazan: Serhat</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Sık sorulan sorular” yazar. Büyük başlığın altında, cevapların açık olduğunu söyleyen bir paragraf vardır. Numaralı beş bağlantı üstte durur. Her satır, sorunun tam cümlesidir. “tıklayın” diye bir satır yoktur. Üçüncü soruya tıklanınca sayfa “Form neden ileti göndermez?” başlığına kayar. Adresin sonunda `#form` görünür. Başlığın altında cevap paragrafı zaten duruyordur. Ek bir ok veya açılan kutu belirmez.

Her soru, ana başlıktan küçük ve diğer sorularla aynı büyüklüktedir. Cevaplar normal puntodadır. Fotoğraf cevabında `sira.jpg` ve `izmir.jpg` eşit aralıklı durur. Form cevabında `serhat@example.com` de eşit aralıklıdır. Onun altında girintili bir alıntı vardır: “Paket adresin sonunda duruyorsa form, bu dersin ölçüsünde çalışmıştır.” Çizgi sorusunun cevabı, 34 ile 65’in hangi kentte durduğunu söyler. Son sorunun altında daireli dört kent vardır. Numara, üstteki gezintidedir. Kent listesinde daire vardır. En altta “İlk soruya dön” mavi bir bağlantıdır. Tıklanınca sayfa birinci soruya kayar. Onun altında “Notu yazan: Serhat” durur.

## Tek soru da aynı iskeleti kullanır

Kısa belge, fotoğraf sorusunun tek başına da okunduğunu gösterir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Tek soru</title>
  </head>
  <body>
    <h1>Sık sorulan sorular</h1>
    <h2 id="kirik">Fotoğraf neden kırık görünür?</h2>
    <p>
      <code>izmir.jpg</code> bu dosyanın yanında yoksa kırık simge görünür.
    </p>
  </body>
</html>
```

Tarayıcıda görünen:
Büyük başlık “Sık sorulan sorular”, onun altında daha küçük “Fotoğraf neden kırık görünür?” vardır. Cümlede `izmir.jpg` eşit aralıklıdır. Sayfada gerçek bir kırık fotoğraf yoktur. Cevap, ne olacağını anlatan bir paragraftır. Başlık kapalı bir kutu değildir.

## Sık yapılan hata

Soruyu kalın bir paragraf, cevabı onun devamı yapmak, içindekilerde inilecek bir yer bırakmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başsız soru</title>
  </head>
  <body>
    <h1>Sorular</h1>
    <p><a href="#form">Form neden ileti göndermez?</a></p>
    <p><strong>Form neden ileti göndermez?</strong> Çünkü sunucu yoktur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Üstteki bağlantı mavidir. Tıklanınca sayfa hiçbir yere kaymaz. Adreste `#form` belirse de hedef yoktur. Soru, kalın bir cümlenin başıdır. Cevap aynı paragrafın içinde, noktanın ardından akar. İkisi arasında başlığın verdiği boşluk yoktur.

Doğru belgede soru bir başlıktır ve bağlantının adıyla aynı kimliği taşır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Başlıklı soru</title>
  </head>
  <body>
    <h1>Sorular</h1>
    <p><a href="#form">Form neden ileti göndermez?</a></p>
    <h2 id="form">Form neden ileti göndermez?</h2>
    <p>Çünkü bu notlar bir sunucuya bağlı değildir. Yazılanlar adres çubuğunda durur.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Bağlantı tıklanınca “Form neden ileti göndermez?” başlığı üste gelir. Cevap, başlığın altında ayrı bir paragraftır. Soru kalın bir cümle parçası olarak kalmaz. Orta boy bir başlık olur.

## Egzersizler

1. `sorular.html` dosyasında beş soru, numaralı bir listede mavi bağlantı olarak görünsün. Her bağlantı, aynı cümleyi taşıyan bir başlığa indirsin. Cevaplar sayfa açılır açılmaz görünsün. Açılan bir kutu belirmesin.
2. “Fotoğraf neden kırık görünür?” cevabında dosya adı eşit aralıklı dursun. Başlık, sayfanın en büyük satırı olmasın. En büyük satır “Sık sorulan sorular” olsun.
3. Sayfanın altına “İlk soruya dön” koyun. Tıklanınca birinci soru üste gelsin. Adresin sonu `#yol` olsun. Dosya adı değişmesin.

[← Önceki gün](../27-comparison-table/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../29-site/ders.md)
