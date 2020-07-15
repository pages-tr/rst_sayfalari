ADI
===

iconvconfig - iconv modülü yapılandırma önbelleği oluştur

SYNOPSIS
========

**iconvconfig** [*seçenekler*] [*rehber*]...

AÇIKLAMA
========

**Iconv**\ (3) işlevi dahili olarak bir karakter kümesine ve karakter kümesinden dönüştürmek için *gconv* modüllerini kullanır. Bir dönüştürme için gereken modülleri belirlemek için bir yapılandırma dosyası kullanılır. Bu tür bir yapılandırma dosyasının yüklenmesi ve ayrıştırılması, **iconv**\ (3) kullanan programları yavaşlatır, bu nedenle bir önbellek mekanizması kullanılır.

**Iconvconfig** programı, iconv modülü yapılandırma dosyalarını okur ve hızlı yüklenen bir gconv modülü yapılandırma önbellek dosyası yazar.

Sistem tarafından sağlanan gconv modüllerine ek olarak, kullanıcı **GCONV_PATH** ortam değişkeni ile özel gconv modülü dizinleri belirtebilir. Ancak, iconv modülü yapılandırma önbelleği yalnızca **GCONV_PATH** ortam değişkeni ayarlanmadığında kullanılır.

SEÇENEKLER
==========

**--nostdlib**
   Sistem varsayılan gconv dizininde arama yapmayın, yalnızca komut satırında sağlanan dizinleri arayın.

**-o**\ *outputfile*\ **, --output=**\ *outputfile*
   Çıktı için sistem varsayılan önbellek konumu yerine *outputfile* kullanın.

**--prefix=**\ *pathname*
   Sistem yol adlarının başına eklenecek öneki ayarlayın.Aşağıdaki DOSYALAR'a bakın. Varsayılan olarak önek boştur.Öneki *foo* olarak ayarlandığında, gconv modülü yapılandırması *foo/usr/lib/gconv/gconv-modules* okunur ve önbellek *foo/usr/lib/gconv/gconv-modules.cache*'ye yazılır.

**-?**, **--help**
   Bir kullanım özeti yazdırın ve çıkın.

**--usage**
   Kısa bir kullanım özeti yazdırın ve çıkın.

**-V**, **--version**
   **Iconv** için sürüm numarasını, lisansı ve garanti feragatnamesini yazdırın.

ÇIKIŞ DURUMU
============

Başarı sıfır, hatalar sıfır değil.

DOSYALAR
========

*/usr/lib/gconv*
   Her zamanki varsayılan gconv modülü yolu.

*/usr/lib/gconv/gconv-modules*
   Normal sistem varsayılan gconv modülü yapılandırma dosyası.

*/usr/lib/gconv/gconv-modules.cache*
   Normal sistem gconv modülü yapılandırma önbelleği.

AYRICA BAKINIZ
==============

**iconv**\ (1), **iconv**\ (3)
