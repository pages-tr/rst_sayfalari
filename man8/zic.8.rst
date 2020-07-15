ADI
===

zic - saat dilimi derleyicisi

ÖZET
====

**zic** [ *seçenek* ... ] [ *dosya adı* ... ]

AÇIKLAMA
========

**Zic** programı, komut satırında belirtilen dosyalardan metin okur ve bu girdide belirtilen zaman dönüştürme bilgi dosyalarını oluşturur. Bir *dosya adı* “” ise, standart girdi okunur.

SEÇENEKLER
==========

**version**
   Çıktı sürüm bilgisi ve çıkış.

**help**
   Kısa kullanım mesajı çıktısı ve çıkışı.

**d**\ *directory*
   Zaman dönüştürme bilgi dosyalarını, aşağıda belirtilen standart dizinden ziyade, adlandırılmış dizinde oluşturun.

**l**\ *timezone*
   *Saat dilimini* yerel saat olarak kullan. **zic**, giriş formun bir bağlantı satırını içeriyormuş gibi davranacaktır

Yerel *saat dilimi* bağlantısı

**p**\ *timezone*
   POSIX biçimindeki *saat dilimi* ortam değişkenlerini işlerken saat dilimi kurallarını kullanın. **zic**, giriş formun bir bağlantı satırını içeriyormuş gibi davranacaktır

Bağlantı *saat dilimi* posixrules

**L**\ *leapsecondfilename*
   Verilen ada sahip artık saniye bilgisini dosyadan okuyun. Bu seçenek kullanılmazsa, çıktı dosyalarında artık saniye bilgisi görünmez.

**v**
   Daha ayrıntılı olun ve aşağıdaki durumlar hakkında şikayet edin:

   Girdi, bir bağlantının bağlantısını belirtir.

   Veri dosyasında görünen bir yıl, **zaman**\ (2) değerleriyle temsil edilebilen yıl aralığının dışında.

   Girişte 24:00 veya daha fazla bir zaman görünür. 1998 öncesi **zic** sürümleri 24:00, 2007 öncesi sürümleri ise 24: 00'den büyük süreleri yasaklar.

   Kural ayın başlangıcını veya sonunu aşar. 2004 öncesi **zic** versiyonları bunu yasaklamaktadır.

   Çıktı dosyası, bir zaman diliminin uzun vadeli geleceğiyle ilgili tüm bilgileri içermez, çünkü gelecek genişletilmiş POSIX TZ dizesi olarak özetlenemez. Örneğin, 2013 itibariyle bu sorun, öngörülemeyen gelecek için İran'ın gün ışığından yararlanma kuralları için ortaya çıkmaktadır, çünkü bu kurallar temsil edilemeyen İran takvimine dayanmaktadır.

   Çıktı, daha eski **zic** çıktı formatları için tasarlanmış istemci kodu tarafından düzgün işlenemeyen veriler içeriyor. Bu uyumluluk sorunları yalnızca 1970'den önce veya 2038'in başlangıcından sonra zaman damgalarını etkiler.

   Bir saat dilimi kısaltmasının 3'ten az karakteri vardır. POSIX en az 3 gerektirir.

   Çıktı dosyası adı, ASCII harfi, “”, “/” veya “_” olmayan bir bayt içeriyor; veya 14 bayttan fazla içeren veya “” ile başlayan bir dosya adı bileşeni içeriyorsa.

**s**
   Çıktı dosyalarında saklanan zaman değerlerini, imzalanmaları veya imzalanılmamaları için alınan değerlerle sınırlandırın. SVVS uyumlu dosyalar oluşturmak için bu seçeneği kullanabilirsiniz.

Giriş dosyaları metin dosyaları olmalıdır, yani her biri yeni satır baytıyla biten ve en fazla 511 bayt içeren ve herhangi bir NUL bayt içermeyen sıfır veya daha fazla satırdan oluşan bir dizi olmalıdır. Giriş metninin kodlaması tipik olarak UTF-8 veya ASCII'dir; POSIX Taşınabilir Karakter Kümesi (PPCS) için unibyte temsili olmalıdır ve http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap06.html ve kodlamanın unibyte olmayan karakterleri tamamen PPCS olmayan baytlardan oluşmalıdır. PPCS olmayan karakterler genellikle yalnızca yorumlarda görülür: çıktı dosyası adları ve saat dilimi kısaltmaları hemen hemen her karakteri içerebilirse de, **v** seçeneği altında açıklanan kısıtlı sözdizimi ile sınırlıysa diğer yazılımlar daha iyi çalışır.

Giriş satırları alanlardan oluşur. Alanlar birbirinden bir veya daha fazla boşluk karakteriyle ayrılır. Beyaz boşluk karakterleri boşluk, form besleme, satır başı, satırsonu, sekme ve dikey sekmedir. Giriş satırlarında öndeki ve sondaki beyaz boşluk yok sayılır. Girişteki alıntılanmamış bir keskin karakter (#), keskin karakterin göründüğü satırın sonuna kadar uzanan bir açıklama getirir. Bir alanın parçası olarak kullanılacaklarsa boşluk karakterleri ve keskin karakterler çift tırnak işareti (") içine alınabilir. Boş olan herhangi bir satır (yorum soyma işleminden sonra) yok sayılır. Boş olmayan satırlardan biri üç tür: kural çizgileri, bölge çizgileri ve bağlantı çizgileri.

İsimler İngilizce olmalı ve büyük / küçük harfe duyarlı değildir. Birkaç bağlamda görünürler ve ay, hafta içi adları ve yalnızca **maksimum**, **Yuvarlama** ve **Bölge** gibi anahtar kelimeler içerirler. Bir ad, bir ilk önek hariç tümü hariç tutularak kısaltılabilir; herhangi bir kısaltma, bağlam bakımından açık olmalıdır.

Bir kural satırı şu şekildedir

::


   Rule	NAME	FROM	TO	TYPE	IN	ON	AT	SAVE	LETTER/S

   For example:

   Rule	US	1967	1973		Apr	lastSun	2:00w	1:00	D

Bir kural satırı oluşturan alanlar şunlardır:

**ADI**
   Bu satırı içeren kural kümesinin adını verir. Ad, ne ASCII basamağı ne de “” veya “+” olmayan bir karakterle başlamalıdır. Gelecekteki uzantılara izin vermek için, alıntılanmamış bir ad “!$%&'()*,/:;<=>?@[]^`{|}~” kümesinden karakterler içermemelidir.

**FROM**
   Kuralın uygulandığı ilk yılı verir. İmzalı bir tamsayı yılı sağlanabilir; proleptik Gregoryen takvimi, 1. yıldan önceki yıl 0 ile varsayılır. **Minimum** (veya bir kısaltma) kelimesi, belirsiz geçmiş anlamına gelir. **Maksimum** kelimesi (veya bir kısaltma) belirsiz gelecek anlamına gelir. Kurallar, tekrarlanamayan zamanlar yok sayılırken, zaman değerleri olarak gösterilemeyen zamanları tanımlayabilir; bu, kuralların farklı zaman değeri türlerine sahip ana bilgisayarlar arasında taşınabilir olmasını sağlar.

**TO**
   Kuralın uygulandığı son yılı verir. **Minimum** ve **maksimuma** (yukarıdaki gibi) ek olarak, **FROM** alanının değerini tekrarlamak için **yalnızca** kelime (veya bir kısaltma) kullanılabilir.

**TYPE**
   "" olmalı ve yıl türlerini içerebileceği eski **zic** sürümleriyle uyumluluk için hazır olmalıdır.

**IN**
   Kuralın yürürlüğe girdiği ayı adlandırır. Ay adları kısaltılabilir.

**ON**
   Kuralın yürürlüğe girdiği günü verir. Tanınan formlar şunları içerir:

::


   5	the fifth of the month
   lastSun	the last Sunday in the month
   lastMon	the last Monday in the month
   Sun>=8	first Sunday on or after the eighth
   Sun<=25	last Sunday on or before the 25th

Hafta içi bir ad (ör. **Pazar**) veya "son" (örn. **SonPazar**) öğesinden önce gelen bir hafta içi ad kısaltılabilir veya tam olarak belirtilebilir. **AÇIK** alanında boşluk olmamalıdır.

**AT**
   Kuralın yürürlüğe girdiği günün saatini verir. Tanınan formlar şunları içerir:

::


   2	time in hours
   2:00	time in hours and minutes
   01:28:14	time in hours, minutes, and seconds
   15:00	24-hour format time (for times after noon)
   260:00	260 hours after 00:00
   2:30	2.5 hours before 00:00
   	equivalent to 0

0 saati günün başında gece yarısıdır ve 24 saati günün sonunda gece yarısıdır. Bu formlardan herhangi birini, verilen zaman yerel “duvar saati” zamanı ise **w** harfi, verilen zaman yerel “standart” zaman ise **s** veya verilen zaman evrensel zaman ise **u** (veya **g** veya **z**) takip edebilir. ; bir gösterge olmadığında, duvar saati zamanı varsayılır. Amaç, kural alanında, **AT** alanında belirtilen saat türüne ayarlanmış bir saat / takvim, belirtilen tarih ve günün saatini göstereceği anları tanımlamaktır.

**SAVE**
   Kural yürürlükte olduğunda yerel standart saate eklenecek süreyi verir. Bu alan **AT** alanıyla aynı formata sahiptir (tabii ki **w** ve **s** sonekleri kullanılmaz). Negatif ofsetlere izin verilir; İrlanda'da, örneğin, yaz saati uygulaması kışın gözlemlenir ve İrlanda Standart Saati'ne göre negatif bir dengelemeye sahiptir. Ofset sadece standart saate eklenir; örneğin, **zic** 10:30 standart saat artı 0:30 **SAVE** saatini 10:00 standart saat artı 1:00 **SAVE** değerinden ayırmaz.

**LETTER/S**
   Bu kural geçerli olduğunda kullanılacak saat dilimi kısaltmalarının “değişken kısmını” (örneğin, “EST” veya “EDT” deki “S” veya “D”) verir. Bu alan “” ise, değişken kısım null olur.

Bölge hattı şu şekildedir

::

   Zone	NAME	UTOFF	RULES	FORMAT	[UNTIL]

   For example:

   Zone	Asia/Amman	2:00	Jordan	EE%sT	2017 Oct 27 01:00

Bir bölge çizgisini oluşturan alanlar şunlardır:

**NAME**
   Saat diliminin adı. Bu, saat dilimi için zaman dönüştürme bilgi dosyasını oluştururken kullanılan addır. Bir dosya adı bileşeni “.” İçermemelidir. veya “..”; bir dosya adı bileşeni, “/” içermeyen maksimum bir alt dizedir.

**UTOFF**
   Standart zamanı elde etmek için UT'ye eklenecek süre. Bu alan, kural satırlarının **AT** ve **SAVE** alanlarıyla aynı biçime sahiptir; UT'den zaman çıkarılması gerekiyorsa alana eksi işareti ile başlayın.

**RULES**
   Saat diliminde veya alternatif olarak, kural satırı KAYDET sütunuyla aynı formatta geçerli olan ve yerel standart zaman efektine eklenecek süreyi ve sonuçta ortaya çıkan sürenin standart olup olmadığını belirleyen kuralların adı veya gün ışığından yararlanma. Bu alan varsa, standart zaman her zaman geçerlidir. Bir süre verildiğinde, sadece standart sürenin toplamı ve bu miktar önemlidir.

**FORMAT**
   Saat dilimi kısaltmalarının biçimi. **%S** karakter çifti, saat dilimi kısaltmasının “değişken kısmı” nın nereye gittiğini göstermek için kullanılır. Alternatif olarak, bir format **%z** çiftini UT kayması için ± *hh*, ± *hhmm* veya ± *hhmmss* biçiminde, *hh*, *mm* ve *ss*'nin bilgi kaybetmeyen en kısa formu kullanarak UT'nin doğusundaki (+) veya batı (-) saat, dakika ve saniye. Alternatif olarak, bir eğik çizgi (/), standart ve gün ışığı kısaltmalarını ayırır. POSIX ile uyumlu olmak için, bir saat dilimi kısaltmasında yalnızca alfasayısal ASCII karakterleri, “+” ve “” bulunmalıdır.

**UNTIL**
   Bir konum için UT ofsetinin veya kural (lar) ın değiştiği zaman. YEAR [AY [GÜN [TIME]]] şeklindedir. Bu belirtilirse, zaman dilimi bilgisi verilen UT ofsetinden oluşturulur ve kural, belirtilen zamana kadar değişir; bu, geçişten hemen önce geçerli kurallar kullanılarak yorumlanır. Ay, gün ve günün saati, bir kuralın IN, ON ve AT alanlarıyla aynı biçime sahiptir; sondaki alanlar atlanabilir ve eksik alanlar için varsayılan olarak mümkün olan en erken değer olabilir.

   Bir sonraki satır bir “devam” satırı olmalıdır; bu, bölge çizgisi ile aynı forma sahiptir, ancak "Bölge" dizesi ve adın çıkarılması, devam çizgisi, tarafından kullanılan dosyada önceki satırda "bitiş" bilgisi olarak belirtilen saatten itibaren bilgi yerleştireceğinden önceki satır. Devam çizgileri, tıpkı bölge çizgilerinin yaptığı gibi, bir sonraki çizginin başka bir devam olduğunu belirten “bitiş” bilgisini içerebilir.

Bir bölge aynı anda bir kuralın önceki bölgede veya devam çizgisinde etkili olacağı şekilde değişirse, kural yoksayılır. Tek bir bölgede, aynı anda iki kuralın geçerli olması veya aynı anda iki bölge değişikliğinin geçerli olması bir hatadır.

Bir bağlantı satırı şu forma sahiptir

::

   Link	TARGET	LINK-NAME

   For example:

   Link	Europe/Istanbul	Asia/Istanbul

**TARGET** alanı, bazı bölge satırlarında **NAME** alanı olarak görünmelidir. **LINK-NAME** alanı o bölge için alternatif bir ad olarak kullanılır; bir bölge çizgisinin **NAME** alanı ile aynı sözdizimine sahiptir.

Devam çizgileri dışında, girdilerdeki sırada herhangi bir sırada çizgiler görünebilir. Ancak, birden çok bölge veya bağlantı satırı aynı adı tanımlarsa veya bir bağlantı satırının kaynağı diğerinin hedefi ise davranış belirtilmez.

Dosyadaki artık saniyeleri açıklayan satırlar aşağıdaki forma sahiptir:

::


   Leap	YEAR	MONTH	DAY	HH:MM:SS	CORR	R/S

   For example:

   Leap	2016	Dec	31	23:59:60	+	S

**YEAR**, **MONTH**, **DAY**, ve **HH:MM:SS** alanları artık saniye ne zaman gerçekleştiğini söyler. Bir saniye eklenirse CORR alanı “+” veya bir saniye atlanırsa “” olmalıdır. **R/S** alanı, diğer alanlar tarafından verilen artık ikinci kez UTC olarak yorumlanmalı veya (bir kısaltma) “alan” ise, diğer alanlar tarafından verilen ikinci saniye ise "Yuvarlanmalı" olmalıdır. yerel duvar saati zamanı olarak yorumlanabilir.

GENİŞLETİLMİŞ ÖRNEK
===================

| Burada, özelliklerinin çoğunu göstermesi amaçlanan geniş bir zic girişi örneği. Bu örnekte, AB kuralları Avrupa Birliği ve selefi Avrupa Toplulukları içindir.


::


   # Rule	NAME	FROM	TO	TYPE	IN	ON	AT	SAVE	LETTER/S
   Rule	Swiss	1941	1942		May	Mon>=1	1:00	1:00	S
   Rule	Swiss	1941	1942		Oct	Mon>=1	2:00	0	

   Rule	EU	1977	1980		Apr	Sun>=1	1:00u	1:00	S
   Rule	EU	1977	only		Sep	lastSun	1:00u	0	
   Rule	EU	1978	only		Oct	 1	1:00u	0	
   Rule	EU	1979	1995		Sep	lastSun	1:00u	0	
   Rule	EU	1981	max		Mar	lastSun	1:00u	1:00	S
   Rule	EU	1996	max		Oct	lastSun	1:00u	0	

   # Zone	NAME	UTOFF	RULES	FORMAT	[UNTIL]
   Zone	Europe/Zurich	0:34:08		LMT	1853 Jul 16
   		0:29:46		BMT	1894 Jun
   		1:00	Swiss	CE%sT	1981
   		1:00	EU	CE%sT

   Link	Europe/Zurich	Europe/Vaduz

Bu örnekte, saat dilimi Europe / Zurich olarak adlandırılmıştır ancak Europe / Vaduz olarak takma adı vardır. Bu örnek, Zürih'in yasal ofset 7 ° 26 ′ 22,50 changed olarak değiştirildiği 00: 00'da 1853-07-16 tarihine kadar UT'nin 34 dakika 8 saniye doğusunda olduğunu; Bu 0: 29: 45.50 olarak çalışsa da, giriş biçimi kesirli saniyeleri temsil edemez, bu nedenle burada yuvarlanır. 1894-06-01 saat 00: 00'dan sonra UT ofseti bir saat oldu ve İsviçre yaz saati kuralları (“Kural Swiss” ile başlayan satırlarla tanımlanır) uygulanır. 1981'den günümüze AB gün ışığından yararlanma kuralları uygulandı ve UTC dengesi bir saatte kaldı.

1941 ve 1942'de, gün ışığından yararlanma saati Mayıs ayının ilk Pazartesi günü saat 01: 00'den Ekim ayının ilk Pazartesi günü saat 02: 00'ye kadar geçerlidir. 1981 öncesi AB gün ışığından yararlanma kurallarının burada bir etkisi yoktur, ancak bütünlük için dahil edilmiştir. 1981'den bu yana, gün ışığından yararlanma Mart ayının son Pazar günü saat 01: 00'de başladı. 1995'e kadar Eylül ayının son Pazar günü 01:00 UTC'de sona erdi, ancak bu 1996'da başlayan Ekim ayının son Pazar gününe dönüştü.

Görüntüleme amacıyla, başlangıçta sırasıyla “LMT” ve “BMT” kullanılmıştır. İsviçre kuralları ve daha sonra AB kuralları uygulandığından, zaman dilimi kısaltması standart zaman için CET ve yaz saati için CEST olmuştur.

DOSYALAR
========

*/etc/localtime*
   Varsayılan yerel saat dilimi dosyası.

*/usr/share/zoneinfo*
   Varsayılan saat dilimi bilgi dizini.

NOTLAR
======

İkiden fazla yerel saat türüne sahip alanlar için, derlenen dosyaya kaydedilen en erken geçiş süresinin doğru olduğundan emin olmak için en erken geçiş süresi kuralının **AT** alanında yerel standart saati kullanmanız gerekebilir.

Belirli bir saat diliminde, gün ışığından yararlanma işleminin başlamasının neden olduğu bir saat ilerlemesi çakışıyorsa ve UT ofsetindeki bir değişikliğin neden olduğu bir saat geri çekilmesine eşitse, **zic** yeni UT ofsetinde (hiç olmadan duvar saati zaman değişikliği). Ayrı geçişler elde etmek için, evrensel zamanı kullanarak geçiş örneklerini belirten çoklu bölge devam çizgilerini kullanın.

AYRICA BAKINIZ
==============

**tzfile**\ (5), **zdump**\ (8)
s