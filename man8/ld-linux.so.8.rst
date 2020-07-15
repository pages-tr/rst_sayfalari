ADI
===

ld.so, ld-linux.so - dinamik bağlayıcı / yükleyici

ÖZET
====

Dinamik bağlayıcı, dinamik olarak bağlı bir program veya paylaşılan nesne çalıştırılarak dolaylı olarak çalıştırılabilir (bu durumda dinamik bağlayıcıya komut satırı seçenekleri geçirilemez ve ELF durumunda **.interp**'de depolanan dinamik bağlayıcı bölümü) veya doğrudan çalıştırarak:

*/lib/ld-linux.so.\** [SEÇENEKLER] [PROGRAM [ARGÜMANLAR]]

AÇIKLAMA
========

**ld.so** ve **ld-linux.so\*** programları, bir program için gereken paylaşılan nesneleri (paylaşılan kitaplıklar) bulur ve yükler, programı çalıştırmak için hazırlar ve çalıştırır.

Derleme sırasında **-static** seçeneği **ld**\ (1) 'e verilmedikçe Linux ikili dosyaları dinamik bağlantı (çalışma zamanında bağlantı) gerektirir.

**ld.so** programı, uzun zaman önce kullanılan bir ikili biçim olan a.out ikili dosyalarını işler. **ld-linux.so\*** programı (*libc5 için /lib/ld-linux.so.1*, glibc2 için */lib/ld-linux.so.2*) daha modern ELF biçimindeki ikili dosyaları işler. Her iki program da aynı davranışa sahiptir ve aynı destek dosyalarını ve programları (**ldd**\ (1), **ldconfig**\ (8) ve */etc/ld.so.conf*) kullanır.

Paylaşılan nesne bağımlılıklarını çözerken, dinamik bağlayıcı önce her bağımlılık dizesini eğik çizgi içerip içermediğini kontrol eder (bu, bağlantı zamanında eğik çizgiler içeren bir paylaşılan nesne yol adı belirtilmişse oluşabilir). Bir eğik çizgi bulunursa, bağımlılık dizesi (göreli veya mutlak) yol adı olarak yorumlanır ve paylaşılan nesne bu yol adı kullanılarak yüklenir.

Paylaşılan bir nesne bağımlılığı eğik çizgi içermiyorsa, aşağıdaki sırayla aranır:

o. Varsa, binary'nin DT_RPATH dinamik bölüm özniteliğinde belirtilen dizinlerin kullanılması ve DT_RUNPATH özniteliği yoktur. DT_RPATH kullanımı kullanımdan kaldırıldı.

p. Yürütülebilir dosya güvenli yürütme modunda (aşağıya bakın) çalıştırılmadığı sürece **LD_LIBRARY_PATH** ortam değişkenini kullanarak bu değişken göz ardı edilir.

q. Varsa, binary'nin DT_RUNPATH dinamik bölüm özelliğinde belirtilen dizinleri kullanarak. Bu tür dizinler yalnızca DT_NEEDED (doğrudan bağımlılıklar) girişlerinin gerektirdiği nesneleri bulmak için aranır ve kendilerinin kendi DT_RUNPATH girişlerine sahip olması gereken bu nesnelerin alt öğeleri için geçerli değildir. Bu, bağımlılık ağacındaki tüm çocuklara yapılan aramalara uygulanan DT_RPATH'den farklıdır.

r. Daha önce artırılmış kütüphane yolunda bulunan aday paylaşılan nesnelerin derlenmiş bir listesini içeren /etc/ld.so.cache önbellek dosyasından. Bununla birlikte, ikili dosya -z nodeflib bağlayıcı seçeneğiyle bağlantılıysa, varsayılan yollardaki paylaşılan nesneler atlanır. Donanım yeteneği dizinlerine yüklenen paylaşılan nesneler (aşağıya bakın) diğer paylaşılan nesneler için tercih edilir.

s. Varsayılan yol */lib* ve ardından */usr/lib*. (Bazı 64 bit mimarilerde 64 bit paylaşılan nesneler için varsayılan yollar */lib64* ve sonra */usr/lib64*'tür.) İkili dosya **-z nodeflib** bağlayıcı seçeneğiyle bağlanmışsa, bu adım atlanır.

Rpath belirteci genişletmesi
----------------------------

Dinamik bağlayıcı, bir rpath belirtimindeki (DT_RPATH veya DT_RUNPATH) belirli simge dizelerini anlar. Bu dizeler aşağıdaki gibi ikame edilir:

*$ORIGIN* (veya eşdeğer olarak *${ORIGIN}*)
   Bu, programı veya paylaşılan nesneyi içeren dizine genişler. Böylece, *somedir/app* içerisinde yer alan bir uygulama

   ::

      gcc -Wl,-rpath,'$ORIGIN/../lib'

   böylece, dizin hiyerarşisinde *somedir* nerede olursa olsun, *somedir/lib*'de ilişkili bir paylaşılan nesne bulur. Bu, özel dizinlere yüklenmesi gerekmeyen, ancak bunun yerine herhangi bir dizine açılabilir ve yine de kendi paylaşılan nesnelerini bulabilen "anahtar teslim" uygulamaların oluşturulmasını kolaylaştırır.

*$LIB* (veya eşdeğer olarak *${LIB}*)
   Bu, mimariye bağlı olarak *lib* veya *lib64*'e genişler (örneğin, x86-64'te, lib64'e genişler ve x86-32'de *lib*'e genişler).

*$PLATFORM* (veya eşdeğer olarak *${PLATFORM}*)
   Bu, ana bilgisayar sisteminin işlemci türüne karşılık gelen bir dizeye genişler (örneğin, "x86_64"). Bazı mimarilerde Linux çekirdeği, dinamik bağlayıcıya bir platform dizesi sağlamaz. Bu dizenin değeri yardımcı vektördeki **AT_PLATFORM** değerinden alınır (bkz.**getauxval**\ (3)).

SEÇENEKLER
==========

**--audit**\ *list*
   *list* adlandırılan nesneleri denetçi olarak kullanın. *list* nesneler iki nokta üst üste işaretiyle sınırlandırılır.

**--inhibit-cache**
   */etc/ld.so.cache* kullanmayın.

**--library-path**\ *path*
   **LD_LIBRARY_PATH** ortam değişkeni ayarı yerine *path* kullanın (aşağıya bakın). *ORIGIN*, *LIB* ve *PLATFORM* adları **LD_LIBRARY_PATH** ortam değişkeni olarak yorumlanır.

**--inhibit-rpath**\ *list*
   *list* nesne adlarındaki RPATH ve RUNPATH bilgilerini yok sayın. Güvenli yürütme modunda çalışırken bu seçenek yok sayılır (aşağıya bakın). *list* nesneler iki nokta üst üste veya boşlukla sınırlandırılır.

**--list**
   Tüm bağımlılıkları ve bunların nasıl çözümlendiğini listeleyin.

**--preload** *list* (glibc 2.30'dan beri)
   *Listede* belirtilen nesneleri önceden yükleyin. *Listedeki* nesneler iki nokta üst üste veya boşlukla sınırlandırılır. Nesneler, aşağıdaki **LD_PRELOAD** ortam değişkeninin açıklamasında açıklandığı gibi önceden yüklenir.

   **LD_PRELOAD**'ın aksine, **--preload** seçeneği, yeni bir program yürüten herhangi bir alt işlemde gerçekleştirilen önyüklemeyi etkilemeden tek bir yürütülebilir dosya için önyükleme gerçekleştirmenin bir yolunu sunar.

**--verify**
   Programın dinamik olarak bağlandığını ve bu dinamik bağlayıcıyı kaldırabildiğini doğrulayın.

ÇEVRE
=====

Çeşitli ortam değişkenleri dinamik bağlayıcının çalışmasını etkiler.

Güvenli yürütme modu
--------------------

Güvenlik nedeniyle, dinamik bağlayıcı bir ikili programın güvenli yürütme modunda çalıştırılması gerektiğini belirlerse, bazı ortam değişkenlerinin etkileri geçersiz kılınır veya değiştirilir ve ayrıca bu ortam değişkenleri ortamdan çıkarılır, böylece program bile tanımlara bakınız. Bu ortam değişkenlerinden bazıları dinamik bağlayıcının çalışmasını etkiler ve aşağıda açıklanmıştır. Bu şekilde işlem gören diğer ortam değişkenleri şunları içerir: **GCONV_PATH**, **GETCONF_DIR**, **HOSTALIASES**, **LOCALDOMAIN**, **LOCPATH**, **MALLOC_TRACE**, **NIS_PATH**, **NLSPATH**, **RESOLV_HOST_CONF**, **RES_OPTIONS**, **TMPDIR** ve **TZDIR**.

Yardımcı vektördeki **AT_SECURE** girişi (bkz. **getauxval**\ (3)) sıfır olmayan bir değere sahipse, güvenli yürütme modunda bir ikili yürütülür. Bu giriş, aşağıdakiler de dahil olmak üzere çeşitli nedenlerle sıfır olmayan bir değere sahip olabilir:

-  İşlemin gerçek ve etkili kullanıcı kimlikleri veya gerçek ve etkili grup kimlikleri farklıdır. Bu genellikle bir set-user-ID veya set-group-ID programının yürütülmesi sonucunda oluşur.

-  Kök olmayan bir kullanıcı kimliğine sahip bir işlem, işleme yetenekler sağlayan bir ikili dosya yürütür.

-  Linux Güvenlik Modülü tarafından sıfır dışında bir değer ayarlanmış olabilir.

Ortam Değişkenleri
------------------

Daha önemli çevre değişkenleri arasında şunlar vardır:

**LD_ASSUME_KERNEL** (glibc 2.2.3'ten beri)
   Paylaşılan her nesne, dinamik bağlayıcıyı gerektirdiği minimum çekirdek ABI sürümü hakkında bilgilendirebilir. (Bu gereksinim, **NT_GNU_ABI_TAG** etiketli bir bölüm olarak readn -n aracılığıyla görüntülenebilen bir ELF not bölümünde kodlanır.) Çalışma zamanında, dinamik bağlayıcı çalışan çekirdeğin ABI sürümünü belirler ve minimum ABI sürümlerini belirten paylaşılan nesneleri yüklemeyi reddeder Bu ABI sürümünü aşan.

   **LD_ASSUME_KERNEL**, dinamik bağlayıcının farklı bir çekirdek ABI sürümüne sahip bir sistemde çalıştığını varsaymasına neden olmak için kullanılabilir. Örneğin, aşağıdaki komut satırı, dinamik bağlayıcının *myprog* için gereken paylaşılan nesneleri yüklerken Linux 2.2.5 üzerinde çalıştığını varsaymasına neden olur:

   ::

      $ LD_ASSUME_KERNEL=2.2.5 ./myprog

   Farklı minimum çekirdek ABI sürüm gereksinimlerine sahip bir paylaşılan nesnenin (arama yolundaki farklı dizinlerde) birden çok sürümünü sağlayan sistemlerde, kullanılan nesnenin sürümünü (dizin arama sırasına bağlı olarak) seçmek için **LD_ASSUME_KERNEL** kullanılabilir .

   Tarihsel olarak, **LD_ASSUME_KERNEL** özelliğinin en yaygın kullanımı, hem LinuxThreads hem de NPTL sağlayan sistemlerde eski LinuxThreads POSIX iş parçacığı uygulamasını (bu tür sistemlerde genellikle varsayılan olarak varsayılan olan) el ile seçmekti; bkz. **pthreads**\ (7).

**LD_BIND_NOW** (glibc 2.1.1'den beri)
   Boş olmayan bir dizeye ayarlanırsa, dinamik bağlayıcı, işlev çağrısı çözümlemesini ilk başvurulan noktaya ertelemek yerine program başlangıcındaki tüm sembolleri çözmesine neden olur. Bu hata ayıklayıcı kullanırken faydalıdır.

**LD_LIBRARY_PATH**
   Yürütme sırasında ELF kitaplıklarının aranacağı dizinlerin listesi. Listedeki öğeler, iki nokta üst üste veya noktalı virgülle ayrılır ve her iki ayırıcıdan kaçmak için destek yoktur.

   Bu değişken güvenli yürütme modunda yok sayılır.

   **LD_LIBRARY_PATH** içinde belirtilen yol adları içinde, dinamik bağlayıcı *Rpath token genişletmesinde* yukarıda açıklandığı gibi *$ORIGIN*, *$LIB* ve *$PLATFORM* (veya adların etrafında süslü parantez kullanan sürümler) belirteçlerini genişletir. Bu nedenle, örneğin aşağıdakiler, yürütülecek programı içeren dizinin altındaki *lib* veya *lib64* alt dizininde bir kitaplığın aranmasına neden olur:

   ::

      $ LD_LIBRARY_PATH='$ORIGIN/$LIB' prog

   (*$ORIGIN* ve *$LIB* değerlerinin kabuk değişkenleri olarak genişletilmesini engelleyen tek tırnak kullanımını unutmayın!)

**LD_PRELOAD**
   Diğerlerinden önce yüklenecek ek, kullanıcı tanımlı, ELF paylaşılan nesnelerin listesi. Bu özellik, diğer paylaşılan nesnelerdeki işlevleri seçici olarak geçersiz kılmak için kullanılabilir.

   Listenin öğeleri boşluk veya iki nokta üst üste ile ayrılabilir ve ayırıcılardan kaçmak için destek yoktur. Nesneler, DESCRIPTION altında verilen kurallar kullanılarak aranır. Nesneler aranır ve listede belirtilen soldan sağa doğru sırada bağlantı eşlemesine eklenir.

   Güvenli yürütme modunda, eğik çizgiler içeren önyükleme yol adları yoksayılır. Ayrıca, paylaşılan nesneler yalnızca standart arama dizinlerinden ve yalnızca set-kullanıcı kimliği modu biti etkinleştirilmişse (tipik değildir) önceden yüklenir.

   **LD_PRELOAD** listesinde belirtilen adlar içinde dinamik bağlayıcı, yukarıda *Rpath token genişletmesinde* açıklandığı gibi *$ORIGIN*, *$LIB* ve *$PLATFORM* (veya adların etrafında süslü parantez kullanan sürümler) belirteçlerini anlar. (Ayrıca **LD_LIBRARY_PATH** açıklamasında alıntı yapma tartışmasına bakınız.)

   Önceden yüklenecek kütüphaneleri belirtmenin çeşitli yöntemleri vardır ve bunlar aşağıdaki sırayla ele alınır:

   (1) **LD_PRELOAD** ortam değişkeni.

   (2) Dinamik bağlayıcıyı doğrudan çağırırken **--preload** komut satırı seçeneği.

   (3) */etc/ld.so.preload* dosyası (aşağıda açıklanmıştır).

**LD_TRACE_LOADED_OBJECTS**
   (Herhangi bir değere) ayarlanırsa, programın normal bağımlılık yerine **ldd**\ (1) tarafından çalıştırılmış gibi dinamik bağımlılıklarını listelemesine neden olur.

Sonra, birçoğu eski veya sadece dahili kullanım için çok fazla veya daha az belirsiz değişken var.

**LD_AUDIT** (glibc 2.4'ten beri)
   Ayrı bir bağlayıcı ad alanında diğerlerinden önce yüklenecek kullanıcı tanımlı, ELF paylaşılan nesnelerin listesi (yani, işlemde oluşacak normal sembol bağlarına girmeyen) Bu nesneler işlemi denetlemek için kullanılabilir dinamik bağlayıcı. Listedeki öğeler iki nokta üstüste ayrılmıştır ve ayırıcıdan kaçmak için destek yoktur.

   **LD_AUDIT** güvenli yürütme modunda yok sayılır.

   Dinamik bağlayıcı, denetim paylaşılan nesnesindeki uygun bir işlevi çağırarak denetim paylaşılan nesnelerini denetim denetim noktalarında (örneğin, yeni bir paylaşılan nesne yükleme, bir sembol çözme veya başka bir paylaşılan nesneden bir simge çağırma) bildirir. Ayrıntılar için, bkz. **rtld-audit**\ (7). Denetim arabirimi, Bağlayıcı ve Kütüphaneler Kılavuzunda *Runtime Linker Denetim Arayüzü*bölümünde açıklandığı gibi Solaris'te sağlananla büyük ölçüde uyumludur.

   **LD_AUDIT** listesinde belirtilen adlar içinde dinamik bağlayıcı, yukarıda Rpath belirteci genişletmesinde açıklandığı gibi *$ORIGIN*, *$LIB* ve *$PLATFORM* (veya adların etrafında süslü parantez kullanan sürümler) belirteçlerini anlar. (Ayrıca **LD_LIBRARY_PATH** açıklamasında alıntı yapma tartışmasına bakınız.)

   Glibc 2.13, güvenli yürütme modunda, denetim listesindeki eğik çizgiler içeren adlar göz ardı edilir ve yalnızca standart arama dizinlerinde set-user-ID mod biti etkinleştirilmiş olan paylaşılan nesneler yüklenir.

**LD_BIND_NOT** (glibc 2.1.95'ten beri)
   Bu ortam değişkeni boş olmayan bir dizeye ayarlanırsa, bir işlev sembolünü çözdükten sonra GOT'u (genel ofset tablosu) ve PLT'yi (prosedür bağlantı tablosu) güncellemeyin. Bu değişkenin kullanımını **LD_DEBUG** (*bağlamalar* ve *semboller kategorileriyle*) ile birleştirerek, tüm çalışma zamanı işlev bağlamaları gözlemlenebilir.

**LD_DEBUG** (glibc 2.1'den beri)
   Dinamik bağlayıcının çalışması hakkında ayrıntılı hata ayıklama bilgileri çıktısı alın. Bu değişkenin içeriği, iki nokta üst üste, virgül veya (değer belirtilmişse) boşluklarla ayrılmış aşağıdaki kategorilerden daha fazladır:

   *help*
      Bu değişkenin değerinde yardım belirtilmesi belirtilen programı çalıştırmaz ve bu ortam değişkeninde hangi kategorilerin belirtilebileceği hakkında bir yardım iletisi görüntüler.

   *all*
      Tüm hata ayıklama bilgilerini yazdırın (*istatistikler* ve *kullanılmayanlar hariç*; aşağıya bakın).

   *bindings*
      Her sembolün bağlı olduğu tanım hakkında bilgi görüntüler.

   *files*
      Giriş dosyası için ilerleme durumunu görüntüler.

   *libs*
      Kitaplık arama yollarını görüntüleme.

   *reloc*
      Yer değiştirme işlemini görüntüleyin.

   *scopes*
      Kapsam bilgilerini görüntüler.

   *statistics*
      Yer değiştirme istatistiklerini görüntüler.

   *symbols*
      Her sembol araması için arama yollarını görüntüleyin.

   *unused*
      Kullanılmayan DSO'ları belirleyin.

   *versions*
      Sürüm bağımlılıklarını göster.

   Glibc 2.3.4 olduğundan, */etc/suid-debug* dosyası yoksa (dosyanın içeriği ilgisiz) **LD_DEBUG** güvenli yürütme modunda yok sayılır.

**LD_DEBUG_OUTPUT** (glibc 2.1'den beri)
   Varsayılan olarak, **LD_DEBUG** çıktısı standart hataya yazılır. **LD_DEBUG_OUTPUT** tanımlanmışsa, çıktı değeri tarafından belirtilen yol adına "." Sonekiyle yazılır. (nokta) ve ardından yol adına eklenen işlem kimliği.

   Güvenli yürütme modunda **LD_DEBUG_OUTPUT** yoksayılır.

**LD_DYNAMIC_WEAK** (glibc 2.1.91'den beri)
   Varsayılan olarak, bir sembol başvurusunu çözmek için paylaşılan kitaplıklarda arama yaparken, dinamik bağlayıcı bulduğu ilk tanıma çözümlenir.

   Eski glibc sürümleri (2.2'den önce) farklı bir davranış sağladı: eğer bağlayıcı zayıf bir sembol bulduysa, o sembolü hatırlar ve kalan paylaşılan kütüphanelerde aramaya devam eder. Daha sonra aynı sembolün güçlü bir tanımını bulsaydı, bunun yerine bu tanımı kullanırdı. (Başka sembol bulunamazsa, dinamik bağlayıcı başlangıçta bulduğu zayıf sembolü kullanır.)

   Eski glibc davranışı standart değildi. (Standart uygulama, zayıf ve güçlü semboller arasındaki ayrımın sadece statik bağlantı zamanında etkili olması gerektiğidir.) Glibc 2.2'de, dinamik bağlayıcı mevcut davranışı (buradaki diğer uygulamaların çoğu tarafından sağlanan davranış) sağlayacak şekilde değiştirilmiştir. zaman).

   **LD_DYNAMIC_WEAK** ortam değişkeninin tanımlanması (herhangi bir değerle) eski (standart olmayan) glibc davranışını sağlar, böylece bir paylaşılan kitaplıktaki zayıf bir sembol daha sonra başka bir paylaşılan kitaplıkta bulunan güçlü bir sembolle geçersiz kılınabilir. (Bu değişken ayarlandığında bile, paylaşılan kitaplıkta güçlü bir sembolün, ana programda aynı sembolün zayıf tanımını geçersiz kılmayacağını unutmayın.)

   Glibc 2.3.4'ten beri, **LD_DYNAMIC_WEAK** güvenli yürütme modunda yok sayılır.

**LD_HWCAP_MASK** (glibc 2.1'den beri)
   Donanım özellikleri için maske.

**LD_ORIGIN_PATH** (glibc 2.1'den beri)
   İkili dosyanın bulunduğu yol.

   Glibc 2.4'ten beri, **LD_ORIGIN_PATH** güvenli yürütme modunda yok sayılır.

**LD_POINTER_GUARD** (glibc 2.4'ten 2.22'ye)
   İşaretçi korumasını devre dışı bırakmak için 0 olarak ayarlayın. Başka bir değer de varsayılan olan işaretçi korumayı etkinleştirir. İşaretçi koruması, yazılabilir program belleğinde depolanan bazı kodlayıcıların (**setjmp**\ (3) tarafından kaydedilen dönüş adresleri veya çeşitli glibc dahili aygıtlar tarafından kullanılan işlev işaretleyicileri) bir saldırganın saldırganı ele geçirmesini zorlaştırmak için yarı rastgele karıştırıldığı bir güvenlik mekanizmasıdır. arabellek taşması veya istifleme saldırısı durumunda kullanılacak işaretçiler. Glibc 2.23 olduğundan, **LD_POINTER_GUARD** artık her zaman etkin olan işaretçi korumasını devre dışı bırakmak için kullanılamaz.

**LD_PROFILE** (glibc 2.1'den beri)
   Bir yol adı veya bir soyadı olarak belirtilecek, profillenecek (tek) paylaşılan bir nesnenin adı. Profil çıktısı, adı "*$LD_PROFILE_OUTPUT*/*$LD_PROFILE.profile*" olan dosyaya eklenir.

   Glibc 2.2.5 olduğundan, **LD_PROFILE** güvenli yürütme modunda yok sayılır.

**LD_PROFILE_OUTPUT** (glibc 2.1'den beri)
   **LD_PROFILE** çıktısının yazılması gereken dizin. Bu değişken tanımlanmamışsa veya boş bir dize olarak tanımlanmışsa, varsayılan */var/tmp* şeklindedir.

   **LD_PROFILE_OUTPUT** güvenli yürütme modunda yok sayılır; bunun yerine */var/profile* her zaman kullanılır. (Bu ayrıntı yalnızca glibc 2.2.5'ten önce geçerlidir, çünkü sonraki glibc sürümlerinde **LD_PROFILE** güvenli yürütme modunda da yok sayılır.)

**LD_SHOW_AUXV** (glibc 2.1'den beri)
   Bu ortam değişkeni tanımlanmışsa (herhangi bir değerle), çekirdekten geçen yardımcı diziyi gösterin (ayrıca bkz. **getauxval**\ (3)).

   Glibc 2.3.4'ten beri, **LD_SHOW_AUXV** güvenli yürütme modunda yok sayılır.

**LD_TRACE_PRELINKING** (glibc 2.4'ten beri)
   Bu ortam değişkeni tanımlanmışsa, adı bu ortam değişkenine atanan nesnenin ön bağlantısını izleyin. (İzlenebilecek nesnelerin bir listesini almak için **ldd**\ (1) kullanın.) Nesne adı tanınmazsa, tüm ön bağlantı etkinlikleri izlenir.

**LD_USE_LOAD_BIAS** (glibc 2.3.3'ten beri)
   Varsayılan olarak (yani, bu değişken tanımlanmadıysa), yürütülebilir dosyalar ve önceden bağlanmış paylaşılan nesneler, bağımlı paylaşılan nesnelerinin temel adreslerini onurlandırır ve (önceden bağlanmamış) konumdan bağımsız yürütülebilir dosyalar (PIE'ler) ve diğer paylaşılan nesneler, onurlandırmaz. **LD_USE_LOAD_BIAS** 1 değeriyle tanımlanırsa, hem yürütülebilir dosyalar hem de PIE'ler temel adresleri dikkate alır. **LD_USE_LOAD_BIAS** 0 değeriyle tanımlanırsa, ne yürütülebilir dosyalar ne de PIE'ler temel adresleri onurlandırmaz.

   Glibc 2.3.3'ten beri, bu değişken güvenli yürütme modunda yok sayılır.

**LD_VERBOSE** (glibc 2.1'den beri)
   Boş olmayan bir dizeye ayarlanırsa, **LD_TRACE_LOADED_OBJECTS** ortam değişkeni ayarlanmışsa, program hakkındaki sembol sürüm bilgilerini girin.

**LD_WARN** (glibc 2.1'den beri)
   Boş olmayan bir dizeye ayarlanırsa, çözülmemiş simgeler hakkında uyarın.

**LD_PREFER_MAP_32BIT_EXEC** (yalnızca x86-64; glibc 2.23'ten beri)
   Intel Silvermont yazılım optimizasyon kılavuzuna göre, 64 bit uygulamalar için bir dalın hedefi daldan 4 GB'den fazla olduğunda dal tahmini performansı olumsuz etkilenebilir. Bu ortam değişkeni (herhangi bir değere) ayarlanırsa, dinamik bağlayıcı önce **mmap**\ (2) **MAP_32BIT** bayrağını kullanarak yürütülebilir sayfaları eşlemeye çalışır ve bu girişim başarısız olursa bu bayrak olmadan eşlemeye geri döner. Not: MAP_32BIT, adres alanının düşük 2 GB'lik (4 GB değil) eşlemesini yapar.

   **MAP_32BIT**, adres alanı düzeni rastgele seçimi (ASLR) için kullanılabilir adres aralığını azalttığından, güvenli yürütme modunda **LD_PREFER_MAP_32BIT_EXEC** her zaman devre dışı bırakılır.

DOSYALAR
========

*/lib/ld.so*
   a.out dinamik bağlayıcı/yükleyici

*/lib/ld-linux.so.*\ {*1*,\ *2*}
   ELF dinamik bağlayıcı/yükleyici

*/etc/ld.so.cache*
   Paylaşılan nesneleri ve aday paylaşılan nesnelerin sıralı bir listesini aramak için derlenmiş bir dizin listesi içeren dosya. Bkz. **ldconfig**\ (8).

*/etc/ld.so.preload*
   Programdan önce yüklenecek boşlukla ayrılmış ELF paylaşılan nesnelerin listesini içeren dosya. Yukarıdaki **LD_PRELOAD** tartışmasına bakın. Hem **LD_PRELOAD** hem de /etc/ld.so.preload kullanılırsa, önce **LD_PRELOAD** tarafından belirtilen kütüphaneler önceden yüklenir. */etc/ld.so.preload* sistem genelinde bir etkiye sahiptir ve belirtilen kitaplıkların sistemde yürütülen tüm programlar için önceden yüklenmesine neden olur. (Bu genellikle istenmeyen bir durumdur ve genellikle yalnızca acil bir çözüm olarak, örneğin bir kitaplık yanlış yapılandırma sorununa geçici bir çözüm olarak kullanılır.)

*lib*.so\**
   paylaşılan nesneler

NOTLAR
======

Donanım özellikleri
-------------------

Bazı paylaşılan nesneler, her CPU'da bulunmayan donanıma özgü talimatlar kullanılarak derlenir. Bu nesneler, adları */usr/lib/sse2/* gibi gerekli donanım özelliklerini tanımlayan dizinlere kurulmalıdır. Dinamik bağlayıcı, bu dizinleri makinenin donanımına göre kontrol eder ve belirli bir paylaşılan nesnenin en uygun sürümünü seçer. CPU özelliklerini birleştirmek için donanım yeteneği dizinleri basamaklandırılabilir. Desteklenen donanım yeteneği adlarının listesi CPU'ya bağlıdır. Şu anda aşağıdaki adlar tanınmaktadır:

**Alpha**
   ev4, ev5, ev56, ev6, ev67

**MIPS**
   loongson2e, loongson2f, octeon, octeon2

**PowerPC**
   4xxmac, altivec, arch_2_05, arch_2_06, booke, cellbe, dfp, efpdouble,
   efpsingle, fpu, ic_snoop, mmu, notb, pa6t, power4, power5, power5+,
   power6x, ppc32, ppc601, ppc64, smt, spe, ucache, vsx

**SPARC**
   flush, muldiv, stbar, swap, ultra3, v9, v9v, v9v2

**s390**
   dfp, eimm, esan3, etf3enh, g5, highgprs, hpage, ldisp, msa, stfle,
   z900, z990, z9-109, z10, zarch

**x86 (32-bit only)**
   acpi, apic, clflush, cmov, cx8, dts, fxsr, ht, i386, i486, i586,
   i686, mca, mmx, mtrr, pat, pbe, pge, pn, pse36, sep, ss, sse, sse2,
   tm

AYRICA BAKINIZ
==============

**ld**\ (1), **ldd**\ (1), **pldd**\ (1), **sprof**\ (1),
**dlopen**\ (3), **getauxval**\ (3), **elf**\ (5),
**capabilities**\ (7), **rtld-audit**\ (7), **ldconfig**\ (8),
**sln**\ (8)
