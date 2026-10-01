# 26. Gün — Küçük sayfa: iletişim formu

Bu gün, not hakkında yazılmış bir iletiyi tek formda toplar. 25. gündeki durak listesi okunuyordu. Bugün ziyaretçi adını, bir kenti, bir yolu ve bir günü seçer. Yeni bir etiket yoktur. Metin kutusu, liste, onay, radyo, sayı, tarih, dosya, etiket ve düğme önceki günlerin parçalarıdır. Form, iletiyi bir sunucuya ulaştırmaz. `get` ile kurulan denemede sonuç, adres çubuğuna düşen pakettir.

## İleti, etiketli alanlarla kurulur

Her alanın adı ekranda yazılır ve o alana bağlanır. Zorunlu olanlar, parantez içinde “zorunlu” diye okunur.

Belge `iletisim.html` adıyla kaydedilir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>İletişim</title>
  </head>
  <body>
    <p><a href="#icerik">İçeriğe geç</a></p>
    <header>
      <h1>İletişim</h1>
      <p>Bu form bir ileti yollamaz. Gönderilince yazılanlar adres çubuğunda görünür.</p>
    </header>
    <main id="icerik">
      <form action="iletisim.html" method="get">
        <p>
          <label for="ad">Ad (zorunlu)</label>
          <input id="ad" name="ad" type="text" value="Serhat" maxlength="40" required />
        </p>
        <p>
          <label for="eposta">E-posta (zorunlu)</label>
          <input id="eposta" name="eposta" type="email" placeholder="serhat@example.com" required />
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
        <h2>İletişim yolu</h2>
        <p>
          <label>
            <input type="radio" name="yol" value="eposta" checked />
            E-posta
          </label>
        </p>
        <p>
          <label>
            <input type="radio" name="yol" value="yazi" />
            Yalnızca bu form
          </label>
        </p>
        <h2>Notta kalsın</h2>
        <p>
          <label>
            <input type="checkbox" name="konu" value="durak" checked />
            Durak sırası
          </label>
        </p>
        <p>
          <label>
            <input type="checkbox" name="konu" value="plaka" />
            Plaka tablosu
          </label>
        </p>
        <p>
          <label for="kisi">Kişi sayısı</label>
          <input id="kisi" name="kisi" type="number" min="1" max="6" step="1" value="1" />
        </p>
        <p>
          <label for="gun">Gün</label>
          <input id="gun" name="gun" type="date" value="2026-10-01" />
        </p>
        <p>
          <label for="not">Not</label>
          <textarea id="not" name="not" rows="4" cols="40">Van Gölü geniştir.</textarea>
        </p>
        <p>
          <button type="submit">İletiyi adres çubuğuna yaz</button>
          <button type="reset">Alanları ilk hâline döndür</button>
        </p>
      </form>
    </main>
    <footer>
      <p>Notu yazan: Serhat. Posta kutusu serhat@example.com bir örnektir, ileti gitmez.</p>
    </footer>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “İletişim” yazar. Büyük başlık aynı kelimedir. Altındaki paragraf, formun ileti yollamadığını söyler. “Ad (zorunlu)” kutusunda “Serhat” hazır durur. “Ad (zorunlu)” yazısına tıklanınca imleç o kutudadır. “E-posta (zorunlu)” kutusu boştur. İçinde soluk `serhat@example.com` ipucu vardır. İpucu gönderilmez. “Kent (zorunlu)” kapalı listesinde “Seçin” yazar. Açılınca dört kent çıkar.

“İletişim yolu”, sayfanın ana başlığından küçük bir başlıktır. Altında iki yuvarlak vardır. “E-posta” dairesi doludur. “Yalnızca bu form” seçilince birincisi boşalır. “Notta kalsın” aynı büyüklükte ikinci bir başlıktır. Altında iki kare vardır. “Durak sırası” işaretlidir. “Plaka tablosu” boştur. İkisi birden işaretlenebilir. “Kişi sayısı” kutusunda 1 yazar. Oklar 1 ile 6 arasında birer birer gider. “Gün” kutusunda 1 Ekim 2026, yerel biçimde durur. Yanında takvim simgesi vardır. “Not” dört satır yüksekliğindedir ve içinde “Van Gölü geniştir.” yazar.

İki düğme vardır. “İletiyi adres çubuğuna yaz” formu gönderir. E-posta `serhat` gibi eksikse veya kent “Seçin”de bırakılırsa sayfa yenilenmez, tarayıcı uyarı verir. E-posta `serhat@example.com`, kent Van olunca adres `ad`, `eposta`, `kent`, `yol`, `konu`, `kisi`, `gun` ve `not` değerlerini `&` ile taşır. Notun boşlukları kodlanır. “Alanları ilk hâline döndür” adresi değiştirmez. Kutuları yeniden “Serhat”, boş e-posta, “Seçin”, işaretli e-posta dairesi ve “Van Gölü geniştir.” hâline getirir. En altta, örneğin bir posta kutusu olmadığı ve ileti gitmediği düz bir cümleyle yazar. Dosya alanı bu denemede yoktur. `get`, fotoğrafı taşımaz. Fotoğraf seçimi aşağıdaki ikinci belgededir. İki grup, “İletişim yolu” ve “Notta kalsın” başlıklarıyla ayrılır. Çerçeve ileride CSS konusudur.

## Fotoğraf seçimi ayrı yöntem ister

Kısa bir ikinci belge, iletiye eklenecek fotoğrafın seçilmesini gösterir. Bu belge gönderilince dosya gitmez. Seçilen adın düğme yanında durması, gözlenen sonuçtur.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Fotoğraf ekleme</title>
  </head>
  <body>
    <h1>Fotoğraf ekleme</h1>
    <form action="foto.html" method="post" enctype="multipart/form-data">
      <p>
        <label for="foto">Kıyı fotoğrafı</label>
        <input id="foto" name="foto" type="file" accept="image/*" />
      </p>
      <p>
        <button type="submit">Dosyayı seçtim</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Kıyı fotoğrafı” yazısının yanında tarayıcının dosya düğmesi durur. Türkçe arayüzde düğme “Dosya seçin” benzeri bir yazıdır. Bir resim seçilince düğmenin yanında o dosyanın adı belirir. Fotoğraf sayfada çizilmez. “Dosyayı seçtim” tıklanınca, dosya diskte `file:///` yoluyla açıksa, sunucu olmadığı için tarayıcı uyarı verebilir. Adres çubuğunda `?foto=` görünmez. Ad, düğmenin yanında kaldıysa seçim çalışmıştır.

## Sık yapılan hata

Grupları etiketlemeden düz yazı gibi bırakmak, “E-posta” kelimesine tıklanınca daireyi doldurmaz.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağsız yol</title>
  </head>
  <body>
    <h1>İletişim</h1>
    <form action="iletisim.html" method="get">
      <p>
        <input type="radio" name="yol" value="eposta" />
        E-posta
      </p>
      <p>
        <input type="radio" name="yol" value="yazi" />
        Yalnızca bu form
      </p>
      <p>
        <button type="submit">İletiyi adres çubuğuna yaz</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
İki yuvarlak ve sağlarında yazılar durur. “E-posta” kelimesine tıklanınca daire boş kalır. Yalnızca küçük dairenin kendisi seçimi değiştirir. İki daire aynı `name` ile bağlı olduğu için biri diğerini yine de kapatır. Eksik olan, yazının hedef büyüklüğüdür.

Doğru belgede yazı, kendi dairesini sarar:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Bağlı yol</title>
  </head>
  <body>
    <h1>İletişim</h1>
    <form action="iletisim.html" method="get">
      <p>
        <label>
          <input type="radio" name="yol" value="eposta" checked />
          E-posta
        </label>
      </p>
      <p>
        <label>
          <input type="radio" name="yol" value="yazi" />
          Yalnızca bu form
        </label>
      </p>
      <p>
        <button type="submit">İletiyi adres çubuğuna yaz</button>
      </p>
    </form>
  </body>
</html>
```

Tarayıcıda görünen:
“Yalnızca bu form” kelimesine tıklanınca o daire dolar, e-posta dairesi boşalır. Gönderilince adreste tek bir `yol=yazi` vardır.

## Egzersizler

1. `iletisim.html` dosyasında ad kutusunda “Serhat”, not kutusunda “Van Gölü geniştir.” hazır görünsün. Kent listesinde dört kent olsun. Kent seçilmeden gönderince adres değişmesin.
2. İzmir seçilip e-posta `serhat@example.com` yazıldığında adres çubuğunda `kent=izmir` ve `eposta` görünsün. “Alanları ilk hâline döndür” tıklanınca kent yeniden “Seçin”, ad yeniden “Serhat” olsun. Adres çubuğu bu tıklamada değişmesin.
3. “Durak sırası” karesinin yazısına tıklayınca kare dolsun veya boşalsın. İki kare birden işaretliyse adreste `konu` iki kez bulunsun. Radyo düğmelerinden ikisi birden dolu kalmasın.

[← Önceki gün](../25-stop-list/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../27-comparison-table/ders.md)
