ADI
===

tzselect - bir saat dilimi seçin

ÖZET
====

**tzselect**

AÇIKLAMA
========

**Tzselect** programı kullanıcıdan geçerli konum hakkında bilgi ister ve ortaya çıkan saat dilimi açıklamasını standart çıktıya verir. Çıktı, **TZ** ortam değişkeni için bir değer olarak uygundur.

Kullanıcı ile tüm etkileşim standart girdi ve standart hata ile yapılır.

ÇIKIŞ DURUMU
============

Kullanıcıdan bir saat dilimi başarıyla alındıysa çıkış durumu sıfırdır, aksi takdirde sıfırdan farklıdır.

ÇEVRE
=====

**AWK**
   POSIX uyumlu bir *awk* programının adı (varsayılan: **awk**).

**TZDIR**
   Saat dilimi veri dosyalarını içeren dizinin adı (varsayılan: */usr/share/zoneinfo*).

DOSYALAR
========

**TZDIR**\ */iso3166.tab*
   ISO 3166 2 harfli ülke kodları ve ülke adları tablosu.

**TZDIR**\ */zone.tab*
   Ülke kodları, enlem ve boylam, TZ değerleri ve açıklayıcı yorumlar tablosu.

**TZDIR**\ */TZ*
   Saat dilimi *TZ* için saat dilimi veri dosyası.

AYRICA BAKINIZ
==============

**tzfile**\ (5), **zdump**\ (8), **zic**\ (8)
