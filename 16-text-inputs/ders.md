# 16. Gün — Metin girdileri (Text Inputs)

Bu gün, tek satırlık kutunun türlerini ayırır ve birden çok satır isteyen notu ayrı bir alana koyar. 15. günde kutu, formun yürüdüğünü göstermek için düz bir metin alanıydı. Bugün parola, e-posta ve uzun not aynı kutuya yazılmaz. Her tür, tarayıcıya o kutuda hangi yazının beklendiğini söyler.

## Tek satır türleri

`<input>` tek satırlık bir alandır. `type` özelliği alanın türünü seçer. `text` düz yazı, `email` e-posta, `password` parola, `search` arama, `url` adres, `tel` telefon biçimidir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kutu türleri</title>
  </head>
  <body>
    <h1>Serhat'ın not başlığı</h1>
    <form action="kutular.html" method="get">
      <p>
        Ad
        <input type="text" name="ad" value="Serhat" maxlength="40" />
      </p>
      <p>
        E-posta
        <input type="email" name="eposta" placeholder="serhat@example.com" />
      </p>
      <p>
        Parola
        <input type="password" name="parola" />
      </p>
      <p>
        Aranan kent
        <input type="search" name="arama" />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Beş satır alt alta durur. “Ad” kutusunda “Serhat” yazılıdır. Bu yazı seçilip silinebilir. `maxlength="40"` kırkıncı karakterden sonra yeni harf kabul etmez. Kutuda fazla harf görünmez. “E-posta” kutusu boştur. İçinde soluk gri “serhat@example.com” durur. Bu bir değer değildir. `placeholder` ipucudur. Kutuya bir harf yazılınca ipucu kaybolur. Gönderildiğinde ipucu adrese eklenmez. Yalnızca gerçekten yazılan metin gider.

“Parola” kutusuna `van` yazılınca ekranda `van` değil, nokta veya yıldız görünür. Adres çubuğu aynı gizliliği vermez. `get` ile gönderilince `parola=van` adresin sonunda düz metin olarak durur. Parola kutusu bu yüzden gerçek bir gizleme aracı değildir. Noktalar yalnızca yanındaki bakışa karşıdır. Gerçek bir parola bu dersin dosyasında denenmez. Kutuya kısa bir deneme kelimesi yazılıp, adresin onu gizlemediği görülür, sonra adres deftere kaydedilmez.

“Aranan kent” kutusu da tek satırdır. Bazı tarayıcılarda içini boşaltan küçük bir çarpı bulunur. Çarpı yoksa kutu, düz metin kutusundan gözle ayırt edilmez. Ayrım türdedir. Arama kutusu, kent adı aramak içindir. Ad kutusu ise imza içindir.

`email` kutusuna `serhat` yazılıp düğmeye basılırsa tarayıcı çoğu zaman gönderimi durdurur. Kutunun yanında, tarayıcının kendi dilinde “bir e-posta adresi girin” benzeri bir uyarı belirir. Sayfa yenilenmez. Adres çubuğuna sorgu eklenmez. `serhat@example.com` yazılıp gönderilince uyarı kalkar ve adreste `eposta=serhat%40example.com` görünür. `%40`, `@` işaretinin kodudur. `url` kutusu `https://` ile başlamayan bir dizide benzer bir uyarı verebilir. `tel` kutusu, biçim kontrolünü bu kadar sık yapmaz. Yazılan rakamlar düz metin gibi pakete girer. `tel` yine de alanın telefon olduğunu söyler. Küçük ekranda tarayıcı rakam klavyesi açabilir.

## Uzun not, çok satır ister

`<textarea>`, birden fazla satır tutan kutudur. İçindeki başlangıç metni bir özellik olarak değil, açılış ile kapanışın arasına yazılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Uzun not</title>
  </head>
  <body>
    <h1>İzmir notu</h1>
    <form action="not.html" method="get">
      <p>
        Not
        <textarea name="not" rows="4" cols="40">Kordon kıyı boyunca yürür.</textarea>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Tek satırlık ince kutu yerine, yaklaşık dört satır yüksekliğinde ve kırk karakter genişliğinde bir alan vardır. İçinde “Kordon kıyı boyunca yürür.” cümlesi durur. Cümlenin sonuna “Saat Kulesi meydandadır.” eklenince iki cümle aynı alanın içinde, alt satıra inerek durur. Köşeden fare ile alan büyütülebilir. Bu tutamaç tarayıcıya aittir. `rows` ve `cols` başlangıç ölçüsünü verir. Ölçü bir çerçeve süsü değildir.

Gönderilince adres `not=` ile başlar ve cümlenin kodlanmış hâlini taşır. Boşluklar `+` veya `%20` olur. Alanın içi silinip boş gönderilirse `not=` ifadesinin sağı boş kalır.

`<textarea>` için `value` özelliği yazılmaz. Yazılırsa o kelime kutunun içinde görünmez. Görünen metin, iki etiket arasında duran metindir. Kapanış unutulursa sayfanın geri kalanı kutunun içine karışır. “Gönder” düğmesi alanın içinde bir yazı gibi durabilir.

## Zorunlu alan ve hazır değer

`required` özelliği, boş alanın gönderilmesini tarayıcının kendi uyarısıyla keser. `readonly` ise hazır değeri göstermeye izin verir, değiştirmeye izin vermez.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Zorunlu kent</title>
  </head>
  <body>
    <h1>Durak</h1>
    <form action="durak.html" method="get">
      <p>
        Notu yazan
        <input type="text" name="ad" value="Serhat" readonly />
      </p>
      <p>
        Kent
        <input type="text" name="kent" required />
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Notu yazan” kutusunda “Serhat” durur. Kutuya tıklanınca imleç gelebilir ama harf silinmez, yenisi yazılmaz. Kutu çoğu tarayıcıda normal renkli kalır. “Kent” kutusu boştur. Gönderilince sayfa yenilenmez. Kent kutusunun yanında “bu alanı doldurun” benzeri bir uyarı çıkar. Uyarının tam cümlesi tarayıcının diline göredir. Kutuya `Trabzon` yazılıp yeniden gönderilince uyarı kaybolur. Adres `ad=Serhat&kent=Trabzon` olur. `readonly` olan alan da pakete girer. Yazılamaz ama gönderilir.

Boş bir ipucu ile zorunluluk karıştırılmaz. `placeholder="Trabzon"` kutuyu dolu saymaz. Gönderimde Trabzon gitmez. Ziyaretçi bir şey yazmamışsa zorunlu alan yine uyarı verir.

## Sık yapılan hata

Uzun notu tek satırlık kutuya ve `value` özelliğinin içine sıkıştırmak, satır sonlarını ve kapanışı bozar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Yanlış uzun not</title>
  </head>
  <body>
    <h1>Van</h1>
    <form action="yanlis.html" method="get">
      <textarea name="not" value="Göl geniştir."></textarea>
      <button type="submit">Gönder</button>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Çok satırlı kutu boş açılır. “Göl geniştir.” kutunun içinde yoktur. `value` bu etikette yok sayılır. Gönderilince `not` boş gider. Ziyaretçi cümleyi kendi yazmazsa paket boş kalır.

Doğru belgede cümle etiketin içindedir:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Doğru uzun not</title>
  </head>
  <body>
    <h1>Van</h1>
    <form action="dogru.html" method="get">
      <p>
        <textarea name="not">Göl geniştir.</textarea>
      </p>
      <p>
        <button type="submit">Gönder</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
Kutu açılınca içinde “Göl geniştir.” vardır. Gönderilince bu cümle `not` adıyla adrese girer.

İkinci hata, e-posta kutusuna `type="text"` deyip biçimin denetleneceğini sanmaktır. `serhat` gibi `@` içermeyen bir dizi düz metin kutusundan uyarısız geçer. Tür `email` olunca aynı dizi durdurulur.

Üçüncü hata, `name` değerini Türkçe bir cümle yapmaktır. `name="kent adı"` boşluk yüzünden dağınık bir sorgu üretir. Ad kısa ve boşluksuzdur: `kent`, `ad`, `not`, `eposta`.

## Egzersizler

1. Ad kutusu “Serhat” ile dolu açılsın ve en çok 40 karakter alsın. E-posta kutusunda soluk bir `serhat@example.com` ipucu görünsün. Kutuya `serhat` yazıp gönderin. Tarayıcı uyarı versin ve adres değişmesin. Tam adresi yazınca `eposta` adreste görünsün.
2. Parola kutusuna kısa bir deneme kelimesi yazın. Ekranda nokta görünsün, gönderince aynı kelime adres çubuğunda düz yazı olarak durur. Bu yüzden gerçek bir parola yazmayın.
3. Dört satır yüksekliğinde bir not alanı açın. İçinde “Van Gölü geniştir.” cümlesi hazır dursun. `value` ile değil, etiketin arasında dursun. Gönderilince cümle `not` adıyla adrese geçsin.

[← Önceki gün](../15-forms/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../17-select-checkbox-radio/ders.md)
