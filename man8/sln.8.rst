ADI
===

sln - sembolik bağlantılar oluştur

ÖZET
====

| **sln**\ *source dest*
| **sln**\ *filelist*

AÇIKLAMA
========

**sln** programı sembolik bağlantılar oluşturur. **ln**\ (1) programından farklı olarak, statik olarak bağlıdır. Bu, herhangi bir nedenle dinamik bağlayıcı çalışmıyorsa, **sln**'nin dinamik kitaplıklara sembolik bağlantılar yapmak için kullanılabileceği anlamına gelir.

Komut satırı iki forma sahiptir. İlk formda *dest*, *kaynağa* yeni bir sembolik bağ olarak yaratılır.

İkinci formda, *filelist*, boşlukla ayrılmış yol adı çiftlerinin bir listesidir ve etki, her yol satırı için argüman olarak iki yol adı ile *sln* dosyasının bir kez yürütüldüğü gibidir.

**sln** programı komut satırı seçeneklerini desteklemez.

AYRICA BAKINIZ
==============

**ln**\ (1), **ld.so**\ (8), **ldconfig**\ (8)
