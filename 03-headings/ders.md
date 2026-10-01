# 3. Gün — Başlıklar (Headings)

Bu gün, bir sayfanın içindeki başlık sırasını kurar. 2. günde iskelet vardı ve gövdede tek bir ana başlık duruyordu. Bugün altı düzeyin anlamı, düzey atlamanın sonucu ve başlığın punto büyütme aracı olmadığı görülür.

## Sayfayı bölümlere ayıran satırlar

Başlık etiketleri, sayfadaki bölümlerin adlarını ve bu adların birbirine göre sırasını belirtir.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Dört kentin başlıkları</title>
  </head>
  <body>
    <h1>Serhat'ın kent notları</h1>
    <h2>İstanbul</h2>
    <h3>Boğaz</h3>
    <h2>İzmir</h2>
    <h3>Kordon</h3>
  </body>
</html>
```

Tarayıcıda görünen:
Sekmede “Dört kentin başlıkları” yazar. Sayfanın en üstünde en büyük ve kalın satır “Serhat'ın kent notları”dır. Onun altında, daha küçük ama hâlâ kalın bir satır “İstanbul” durur. “Boğaz”, “İstanbul”dan da küçüktür ve kalındır. Ardından “İzmir” yine “İstanbul” ile aynı büyüklükte gelir. “Kordon” ise “Boğaz” ile aynı, daha küçük düzeydedir. Her başlık kendi satırındadır. Satırlar arasında tarayıcının verdiği boşluk vardır. Çerçeve yoktur.

Bir sayfada konuların ana adı `<h1>` olur. O adın altındaki bölümler `<h2>`, onların alt başlıkları `<h3>` olur. Sıra kitaptaki bölüm, alt bölüm ve madde düzenine benzer. Tarayıcı bu sırayı, puntoyu küçülterek de gösterir. Punto, başlığın asıl işi olan sıranın yalnızca görünen sonucudur.

## Altı düzey

Altıncı düzeye kadar inen başlık, iyice küçük ve ayrıntılı bir alt konuyu adlandırır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Altı düzey</title>
  </head>
  <body>
    <h1>Van Gölü</h1>
    <h2>Kıyı</h2>
    <h3>Doğu kıyısı</h3>
    <h4>Gün doğumu</h4>
    <h5>İlk saat</h5>
    <h6>Bir dakikalık not</h6>
  </body>
</html>
```

Tarayıcıda görünen:
Altı satır alt alta durur. “Van Gölü” en büyüktür. Her yeni düzey bir öncekinden küçük görünür. “Bir dakikalık not” en küçük başlıktır ve yine de gövde metninden ayrı, kalın bir satırdır. Düzey numarası ekranda “1, 2, 3” diye yazılmaz. Numara yalnızca etiketin adındadır.

`<h7>` diye bir etiket yoktur. Yedi yazılırsa tarayıcı onu başlık saymaz; kelime sıradan bir yazı gibi, büyük puntolu bir satır olmadan durabilir. Altı düzey bir kent notu için zaten fazladır. Çoğu sayfa `<h1>`, `<h2>` ve `<h3>` ile biter.

## Tek ana başlık

Sayfanın bütününe ait ad bir kez, en üst düzeyde yazılır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Trabzon</title>
  </head>
  <body>
    <h1>Trabzon</h1>
    <h2>Kıyı</h2>
    <h2>Yayla yolu</h2>
    <h2>Çarşı</h2>
  </body>
</html>
```

Tarayıcıda görünen:
En üstte bir tane en büyük başlık vardır: “Trabzon”. Altında üç satır aynı büyüklüktedir: “Kıyı”, “Yayla yolu”, “Çarşı”. Üçü de “Trabzon”dan küçüktür. Böylece üç bölümün aynı düzeyde kardeş olduğu, üçünün de Trabzon başlığının altında durduğu görünür.

İkinci bir `<h1>` teknik olarak yazılabilir ve o da en büyük puntoyla çizilir. Sayfa o zaman iki ayrı belge gibi bölünür. Kitap kapağında iki kitap adı olmasına benzer. Bu rehberdeki sayfalarda ana ad bir tanedir.

## Düzey atlanmaz

Bir alt konu, durduğu yerin bir alt düzeyini alır. Üç düzey birden küçültmek, o satırı daha önemsiz yapmaz; sırayı bozar.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Atlanmış düzey</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <h4>Saat Kulesi</h4>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” büyük, “Saat Kulesi” ondan belirgin biçimde küçüktür. Arada `<h2>` ve `<h3>` olmadığı için “Saat Kulesi” sanki çok dip bir notmuş gibi durur. Oysa Saat Kulesi, İzmir notunun doğrudan alt konusuysa onun düzeyi `<h2>` olmalıdır.

Doğru sıra:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Düzey yerinde</title>
  </head>
  <body>
    <h1>İzmir</h1>
    <h2>Saat Kulesi</h2>
    <h3>Konak meydanı</h3>
  </body>
</html>
```

Tarayıcıda görünen:
“İzmir” en büyük, “Saat Kulesi” orta, “Konak meydanı” daha küçüktür. Üç satır arasında birer adımlık bir küçülme vardır. Okuyan kişi, meydan notunun kule başlığının altında durduğunu punto farkından da çıkarır.

Büyük görünmesi istenen bir satır için düzey seçilmez. Küçük bir uyarıyı dev yapmak amacıyla `<h1>` kullanılmaz. Satırın boyutu ileride CSS ile değişir. HTML’de seçilen numara, o satırın belgedeki yerini söyler.

## Sık yapılan hata

Başlığı kapatmamak, sonraki cümleyi de başlığın içine alır.

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapanmamış başlık</title>
  </head>
  <body>
    <h1>Van
    <p>Göl bugün sakindir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
Tarayıcı, `<p>` görünce açık başlığı çoğu zaman kendi kapatır. “Van” büyük bir başlık, “Göl bugün sakindir.” ayrı bir paragraf olarak durabilir. Ekran neredeyse doğru göründüğü için hata fark edilmez. Kaynak yine de bozuktur. Başlıktan sonra paragraf gelmezse, yani bütün yazı aynı satırda kalırsa, o yazının tamamı dev bir başlık olur.

Doğru belge, başlığı kısa tutar ve paragrafı ayrıca kapatır:

```html
<!DOCTYPE html>
<html lang="tr">
  <head>
    <meta charset="UTF-8" />
    <title>Kapanmış başlık</title>
  </head>
  <body>
    <h1>Van</h1>
    <p>Göl bugün sakindir.</p>
  </body>
</html>
```

Tarayıcıda görünen:
“Van” tek başına büyük başlıktır. “Göl bugün sakindir.” normal puntodadır ve başlığın altında, arada boşlukla durur.

İkinci hata, punto için atlamaktır. Ana başlıktan sonra doğrudan `<h6>` yazılırsa satır dipnot gibi küçülür. Alt konu ise `<h2>` ile yazılır.

## Egzersizler

1. Ana başlık “Dört kent” olsun. Altında aynı düzeyde dört bölüm görünsün: İstanbul, İzmir, Trabzon, Van. Dördü de ana başlıktan küçük ve birbiriyle aynı puntoda olsun.
2. İstanbul bölümünün altına “Boğaz” satırını bir alt düzey olarak ekleyin. “Boğaz”, İstanbul satırından küçük, Van satırıyla aynı düzeyde olmasın.
3. Van’ın altına bilerek `<h5>` koyun ve sayfayı yenileyin. Satırın, İstanbul’daki “Boğaz”a göre çok daha küçük kaldığını görün. Sonra düzeyi bir adım alta indirin. Van’ın alt başlığı, “Boğaz” ile aynı büyüklükte dursun.

[← Önceki gün](../02-document/ders.md) · [İçindekiler](../README.md) · [Sonraki gün →](../04-paragraphs/ders.md)
