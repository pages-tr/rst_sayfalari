ADI
===

ldconfig - dinamik bağlayıcı çalışma zamanı bağlamalarını yapılandır

ÖZET
====

**/sbin/ldconfig** [**-nNvXV**] [**-f** *conf*] [**-C** *cache*] [**-r**
*root*] *directory*...

**/sbin/ldconfig** **-l** [**-v**] *library*...

**/sbin/ldconfig** **-p**

AÇIKLAMA
========

**ldconfig**, komut satırında belirtilen dizinlerde, */etc/ld.so.conf* dosyasında ve güvenilen dizinlerde */lib* ve */usr/lib* (on'da bulunan en son paylaşılan kitaplıklara gerekli bağlantıları ve önbelleği oluşturur. *x86-64,/lib* ve */usr/lib* gibi bazı 64 bit mimariler 32 bit kitaplıklar için güvenilir dizinlerdir, 64 bit kitaplıklar için */lib64* ve /usr/lib64* kullanılır).

Önbellek, çalışma zamanı bağlayıcısı, ld.so veya *ld-linux.so* tarafından kullanılır. **ldconfig**, hangi sürümlerin bağlantılarının güncellenmesi gerektiğini belirlerken karşılaştığı kütüphanelerin başlıklarını ve dosya adlarını kontrol eder.

**ldconfig**, varsa kitaplığın hangi C kütüphanelerine bağlı olduğuna bağlı olarak ELF kütüphanelerinin türünü (yani, libc5 veya libc6 / glibc) çıkarmaya çalışacaktır.

Bazı mevcut kütüphaneler, türlerinin çıkarılmasına izin verecek yeterli bilgi içermemektedir. Bu nedenle, */etc/ld.so.conf* dosya biçimi beklenen türün belirtilmesine izin verir. Bu sadece çalışamayacağımız ELF kütüphaneleri için kullanılır. Biçim "dirname = TYPE" şeklindedir; burada TYPE libc4, libc5 veya libc6 olabilir. (Bu sözdizimi komut satırında da çalışır.) Boşluklara izin verilmez. Ayrıca **-p** seçeneğine bakın. **ldconfig** normalde süper kullanıcı tarafından çalıştırılmalıdır, çünkü bazı kök sahip dizinlerde ve dosyalarda yazma izni gerektirebilir.

**ldconfig** dosyasının yalnızca *lib*.so\** (normal paylaşılan nesneler için) veya *ld-*.so\** (dinamik yükleyicinin kendisi için) adlı dosyalara bakacağını unutmayın. Diğer dosyalar yok sayılır. Ayrıca, ldconfig, orta dosyanın (**libfoo.so.1** burada) kütüphane için SONAME olduğu durumlarda, örnek bağlantıların nasıl oluşturulduğuna dair belirli bir model bekler:

::

   libfoo.so -> libfoo.so.1 -> libfoo.so.1.12

Bu kalıba uyulmaması, yükseltme işleminden sonra uyumluluk sorunlarına neden olabilir.

SEÇENEKLER
==========

**-c** *fmt*, **--format=\ fmt**
   (Glibc 2.2'den beri) Kullanılacak önbellek biçimi: *eski*, *yeni* veya *uyumlu*. Glibc 2.32 olduğundan, varsayılan değer yenidir. Ondan önce *uyumluydu*.

**-C**\ *cache*
   */etc/ld.so.cache* yerine önbellek kullanın.

**-f**\ *conf*
   */etc/ld.so.conf* yerine conf komutunu kullanın.

**-i**, **--ignore-aux-cache**
   (Glibc 2.7'den beri) Yardımcı önbellek dosyasını yok sayın.

**-l**
   (Glibc 2.2'den beri) Kütüphane modu. Tek tek kitaplıkları manuel olarak bağlayın. Yalnızca uzmanlar tarafından kullanılması amaçlanmıştır.

**-n**
   Yalnızca komut satırında belirtilen dizinleri işleyin. Güvenilir dizinleri veya */etc/ld.so.conf* dosyasında belirtilen dizinleri işlemeyin. **-N**anlamına gelir.

**-N**
   Önbelleği yeniden oluşturmayın. **-X** belirtilmezse, bağlantılar yine de güncelleştirilir.

**-p**, **--print-cache**
   Geçerli önbellekte depolanan dizin ve aday kitaplıklarının listesini yazdırın.

**-r**\ *root*
   Kök dizini olarak değiştirin ve kök dizini olarak kullanın.

**-v**, **--verbose**
   Ayrıntılı mod. Geçerli sürüm numarasını, taranan her dizinin adını ve oluşturulan bağlantıları yazdırın. Sessiz modu geçersiz kılar.

**-V**, **--version**
   Program sürümünü yazdırın.

**-X**
   Bağlantıları güncelleme. **-N** belirtilmezse, önbellek yine de yeniden oluşturulur.

DOSYALAR
========

*/lib/ld.so*
   Çalışma zamanı bağlayıcı/yükleyici.

*/etc/ld.so.conf*
   Kütüphaneleri aramak için her satıra bir dizin içeren bir liste içeren dosya.

*/etc/ld.so.cache*
   */etc/ld.so.conf* dosyasında belirtilen dizinlerde ve güvenilir dizinlerde bulunan kitaplıkların sıralı bir listesini içeren dosya.

AYRICA BAKINIZ
==============

**ldd**\ (1), **ld.so**\ (8)
