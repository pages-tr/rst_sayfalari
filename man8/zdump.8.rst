ADI
===

zdump - saat dilimi damperi

ÖZET
====

**zdump** [ *seçenek* ... ] [ *saat dilimi* ... ]

AÇIKLAMA
========

**Zdump** programı, komut satırında belirtilen her *saat diliminde* geçerli saati yazdırır.

SEÇENEKLER
==========

**version**
   Çıktı sürüm bilgisi ve çıkış.

**help**
   Kısa kullanım mesajı çıktısı ve çıkışı.

**i**
   Zaman aralıklarının bir açıklamasını çıktılar. Komut satırındaki her bir saat dilimi için, *saat diliminin* aralık biçimli bir açıklamasını girin. Aşağıdaki “INTERVAL FORMAT” na bakın.

**v**
   Zaman aralıklarının ayrıntılı bir açıklamasını yazın. Komut satırındaki her *saat dilimi* için, zamanı mümkün olan en düşük zaman değerinde, mümkün olan en düşük zaman değerinden bir gün sonra, hem algılanan her zaman süresinden bir saniye önce tam olarak hem de tam olarak mümkün olan en yüksek zaman değeri ve mümkün olan en yüksek zaman değerindeki zaman. Her satırı, verilen zamanın sırasıyla yaz saati uygulaması, standart saat veya bilinmeyen bir saat türü olmasına bağlı olarak, D'nin pozitif, sıfır veya negatif olduğu **isdst=**\ D gelir. Verilen yerel saatin Greenwich'in N saniye doğusunda olduğu biliniyorsa, her satırı **gmtoff=**\ N takip eder.

**V**
   **V** gibi, hariç zamanları aşırı zaman değerlerine göre atlayın. Bu, farklı zaman gösterimlerine sahip uygulamalarınkine kıyasla daha kolay çıktı üretir.

**c**\ *[loyear*\ **,**\ *]\ hiyear*
   Verilen yıl (lar) da aralık çıktısını kesin. Kesim süreleri, 0 yılı olan ve Evrensel Zaman (UT) artık saniye göz ardı edilen proleptik Gregoryen takvimi kullanılarak hesaplanır. Kesikler her yılın başında, alt sınır zaman damgasının özel olduğu ve üst kısmın dahil olduğu; örneğin, **c 1970,2070**, 1970-01-01 00:00:00 UTC'den sonra ve 2070-01-01 00:00:00 UTC'den önce veya önce geçişleri seçer. Varsayılan kesme **500,2500**'dür.

**t**\ *[lotime*\ **,**\ *]\ hitime*
   1970-01-01 00:00:00 Koordineli Evrensel Zaman'dan (UTC) bu yana ondalık saniye cinsinden verilen belirli zaman (lar) da aralık çıktısını kesin. Saat dilimi, sayının artık saniye içerip içermediğini belirler. **C**'de olduğu gibi, kesimin alt sınırı özeldir ve üst sınırı kapsayıcıdır.

ARALIK FORMATI
==============

Aralık biçimi, hem insan hem de makine tarafından okunabilir olması amaçlanan kompakt bir metin temsilidir. Boş bir satır, sonra dizenin saat dilimini veren çift tırnaklı bir dize, varsa ilk geçişten önceki zaman aralığını açıklayan ikinci bir satır ve sıfır veya daha fazla satırdan oluşan "TZ = *string*" satırından oluşur. “*Tarih zaman aralığı*”, her geçiş zamanı ve sonraki aralık için bir satır. Alanlar tek sekmelerle ayrılır.

Tarihler *yyyy-aa-gg* biçimindedir ve süreler 24 saat *hh*:*mm*:*ss* biçimindedir, burada *hh*\ <24. Geçişten hemen sonra saatler yerel saattedir. Bir zaman aralığı açıklaması imzalı ± *hhmmss* biçiminde bir UT ofsetinden, bir zaman dilimi kısaltmasından ve bir isdst işaretinden oluşur. UT ofsetine eşit olan bir kısaltma atlanmıştır; diğer kısaltmalar, bir veya daha fazla alfabetik karakter içermedikçe çift tırnaklı dizelerdir. Standart bir süre için bir isdst işareti atlanır ve aksi halde, yaz saati için imzasız ve pozitif (genellikle 1) ve bilinmeyen için negatif olan bir ondalık sayıdır.

Zamanlarda ve mutlak değeri 100 saatten az olan UT ofsetlerinde, saniyeler sıfırlarsa, sıfırlarsa dakikalar da çıkarılır. Pozitif UT ofsetleri Greenwich'in doğusundadır. UT ofseti 00, gerçek ofsetin belirtilmediği alanlarda bir UT yer tutucusunu belirtir; geleneksel olarak, UT ofseti sıfır olduğunda ve saat dilimi kısaltması “” ile başladığında veya “zzz” olduğunda bu gerçekleşir.

Çift tırnaklı dizelerde, çıkış dizileri olağandışı karakterleri temsil eder. Kaçış dizileri boşluk için \s ve C programlama dilinde olağan anlamları olan \ ", \, \f, \n, \r, \t ve \v şeklindedir. Örneğin, çift tırnaklı" "CET'ler dizesi "\" "," CET "" karakter dizisini temsil eder.

Burada, önde gelen boş satır atlanmış olarak çıktıya bir örnek verilmiştir. (Bu örnek, sekmeli sütunlar hizalanacak şekilde birbirinden yeterince ayrılmış sekme duraklarıyla gösterilmiştir.)

::


   TZ="Pacific/Honolulu"
   -	-	-103126	LMT
   1896-01-13	12:01:26	-1030	HST
   1933-04-30	03	-0930	HDT	1
   1933-05-21	11	-1030	HST
   1942-02-09	03	-0930	HWT	1
   1945-08-14	13:30	-0930	HPT	1
   1945-09-30	01	-1030	HST
   1947-06-08	02:30	-10	HST

Burada yerel saat UT 10 saat, 31 dakika ve 26 saniye batısında başlar ve standart bir zaman kısaltılmış LMT. İlk geçişten hemen sonra, tarih 1896-01-13 ve saat 12:01:26'dır ve aşağıdaki zaman aralığı standart bir zaman dilimi HST olarak kısaltılmış UT'nin 10.5 saat batısındadır. İkinci geçişten hemen sonra, tarih 1933-04-30 ve saat 03:00:00 ve aşağıdaki zaman aralığı UT'nin 9.5 saat batısındadır, HDT olarak kısaltılmıştır ve yaz saati uygulamasıdır. Son geçişten hemen sonra tarih 1947-06-08'dir ve saat 02:30:00'dir ve aşağıdaki zaman aralığı, standart bir saat HST olarak kısaltılmış UT'nin 10 saat batısındadır.

İşte başka bir örnekten alıntılar:

::


   TZ="Europe/Astrakhan"
   -	-	+031212	LMT
   1924-04-30	23:47:48	+03
   1930-06-21	01	+04
   1981-04-01	01	+05		1
   1981-09-30	23	+04
   ...
   2014-10-26	01	+03
   2016-03-27	03	+04

Bu zaman dilimi UT'nin doğusudur, bu yüzden UT ofsetleri pozitiftir. Ayrıca, zaman dilimi kısaltmalarının birçoğu UT ofsetinin metnini çoğalttığından çıkarılır.

SINIRLAMA
=========

Zaman süreksizlikleri, yerel saate göre döndürülen sonuçların on iki saatlik aralıklarla örneklenmesi ile bulunur. Bu, tüm gerçek dünyadaki durumlarda işe yarar; bunun başarısız olduğu yapay zaman dilimleri yapılabilir.

**V** ve **V** çıkışında “UT”, modern zaman damgaları için UTC ve UTC'nin girişinden önceki zaman damgaları için başka bir UT aroması kullanan **gmtime**\ (3) tarafından döndürülen değeri ifade eder. Şu anda çıktının daha yeni için "UTC" ve daha eski zaman damgaları için "UT" kullanması için hiçbir girişimde bulunulmamıştır, çünkü kısmen UTC'nin giriş tarihi sorunludur.

AYRICA BAKINIZ
==============

**tzfile**\ (5), **zic**\ (8)
