# 60 Günlük Siber Operasyon Kampı - Başlangıç
## 1. Gun: Linux Temelleri ve Kritik Dizinler
* **/bin**: Sistemin komut cephaneliğidir (ls,cat,mkdir burada bulunur).
* **/var/log**: Sistemin kara kutusudur.Tüm olay kayıtları burada tutulur .Saldırganlar iz silmek için burayı hedefler. 
* **/etc**: Sistemin ayar ve kural merkezidir.Kullanıcı yetkileri (/etc/passwd) buradan yönetilir.
## 1. Gun / 2.Kisim: Yetki Sistemi ve Erişim Analizi
* **UID 0 Analizi**: /etc/passwd dosyası üzerinden root kullanıcısının sistemdeki mutlak yetkisi doğrulandı.
* **Erişim Kontrolü (chmod)**: 640 ve 000 senaryoları ile 'En Az Yetki İlkesi' (Principle of Least Privilege) Laboratuvar ortamında test edildi.
* **Yetki Aşımı (Privilege Escalation)**:Sudo mekanizmasının kısıtlı alanlara erişimdeki rolü ve riskleri gözlemlendi.
* **Kritik Analiz**: Sudo yetkisinin ele geçirilmesi, sistemdeki tüm dosya izinlerini (chmod 000 dahil) hükümsüz kılar.
## 1. Gun / 3. Kisim: Veri Dedektifligi (find & grep)
* **find**: Dosya ismine gore arama yapar. (Ornek: find /etc -name '*.conf')
* **grep**: Dosya icindeki metni arar. (Ornek: grep 'password' dosya.txt)
* **Pipe (|)**: Komutlar arasi veri koprusu kurar. Veriyi suzmemizi saglar.
