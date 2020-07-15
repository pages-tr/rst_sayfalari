ADI
===

nscd - ad hizmeti önbelleği arka plan programı

AÇIKLAMA
========

**nscd**, en yaygın ad hizmeti istekleri için önbellek sağlayan bir arka plan programıdır. Varsayılan yapılandırma dosyası */etc/nscd.conf*, önbellek arka plan programının davranışını belirler. Bkz. **nscd.conf**\ (5).

**nscd**, **getwwnam**\ (3), **getpwuid**\ (3), **getgrnam**\ (3) gibi standart libc arabirimleri aracılığıyla **passwd**\ (5),
**group**\ (5), **hosts**\ (5) **services**\ (5) ve *netgroup* veritabanlarına erişim için önbellek sağlar. **getgrgid**\ (3), **gethostbyname**\ (3) ve diğerleri.

Her veritabanı için iki önbellek vardır: bulunan öğeler için pozitif ve bulunmayan öğeler için negatif. Her önbellek, verileri için ayrı bir TTL (yaşam süresi) süresine sahiptir. Gölge dosyasının özel olarak önbelleğe alınmadığını unutmayın. Bunun sonucunda **getspnam**\ (3) çağrıları önbelleğe alınmaz.

SEÇENEKLER
==========

**--help**
   size tüm seçenekleri ve yaptıklarını içeren bir liste verecektir.

NOTLAR
======

Daemon, her veritabanı için uygun yapılandırma dosyalarındaki değişiklikleri izlemeye çalışacaktır (örn. *Passwd* veritabanı için */etc/passwd* veya */etc/hosts* ve *hosts* veritabanı için /etc/resolv.conf) ve bunlar olduğunda önbelleği temizler değiştirildi. Bununla birlikte, bu sadece kısa bir gecikmeden sonra gerçekleşir (**inotify**\ (7) mekanizması mevcut değilse ve glibc 2.9 veya üstü mevcut değilse) ve bu otomatik algılama, standart dışı NSS modülleri tarafından isteniyorsa, yapılandırma dosyalarını kapsamaz. */etc/nsswitch.conf*. Bu durumda, *nscd* önbelleğini geçersiz kılacak şekilde veritabanının yapılandırma dosyasını değiştirdikten sonra aşağıdaki komutu çalıştırmanız gerekir:

::

   $ nscd -i <database>

AYRICA BAKINIZ
==============

**nscd.conf**\ (5), **nsswitch.conf**\ (5)
