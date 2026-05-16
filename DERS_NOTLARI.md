# 🛡️ Siber Güvenlik ve Pentest Yolculuğu - Portföy

Bu döküman, 2026 Siber Güvenlik Kampı süresince gerçekleştirilen teknik çalışmaları, laboratuvar operasyonlarını ve sistem analizlerini içermektedir.

---

## 📑 İçindekiler
* [Modül 01: Linux Sistem Güvenliği ve Operasyonel Temeller](#modül-01-linux-sistem-güvenliği-ve-operasyonel-temeller)
* [Modül 02: Ağ Temelleri ve Keşif (Yükleniyor...)](#modül-02-ağ-temelleri-ve-keşif)

---

## Modül 01: Linux Sistem Güvenliği ve Operasyonel Temeller
**Tarih:** 15 Mayıs 2026  
**Odak Noktası:** Yetki Hiyerarşisi, Süreç Yönetimi ve Veri Dedektifliği

### 🛠 Teknik Yetkinlikler
* **Hiyerarşi Analizi:** `/etc/passwd` üzerinden UID 0 (Root) yetki kontrolleri.
* **Erişim Sıkılaştırma (Hardening):** `chmod` ile "En Az Yetki İlkesi" (Least Privilege) uygulamaları.
* **Veri Madenciliği:** `grep` ve `find` araçlarıyla log dosyası analizi.
* **Süreç İmhası:** `ps aux` ve `kill` ile şüpheli süreçlerin (Backdoor/Sleep) tespiti.

### 🚩 Uygulamalı Operasyon: "Köstebek Avı" (Final Challenge)
Sistem üzerinde kilitli bir veri kaynağına ulaşma ve zararlı bir süreci durdurma simülasyonu başarıyla tamamlanmıştır.

1. **Erişim ve Sızdırma:** `chmod 400` yetkisine sahip kısıtlı bir log dosyası, `sudo` ve `grep` kullanılarak yetki aşımı (Privilege Escalation) yöntemiyle analiz edilmiş ve kritik token ele geçirilmiştir.
   - **Ele Geçirilen Veri:** `BUGRA_FINAL_BASARI_2026`
2. **Tehdit Avcılığı:** Arka planda sızma girişimi olarak simüle edilen `sleep 666` süreci PID üzerinden tespit edilerek sonlandırılmıştır.
3. **İz Silme:** `rm -rf` operasyonu ile sistem üzerinde hiçbir dijital kanıt bırakılmadan süreç tamamlanmıştır.

---
## 🛰️ 2. Gün: Ağ Temelleri ve Trafik Analizi Laboratuvarı

### 1. Teorik Çerçeve (Mülakat Notları)
* **OSI Modeli Güvenlik Bakışı:** * Katman 2 (Data Link): MAC adresleri üzerinden yerel ağ iletişimi (Risk: ARP Poisoning).
  * Katman 3 (Network): IP adresleri üzerinden yönlendirme (Risk: IP Spoofing).
  * Katman 4 (Transport): TCP (Garantici/Üçlü El Sıkışma) ve UDP (Hızlı/Bağlantısız) protokol yönetimi (Risk: SYN Flood DDoS).
* **Portlar:** Sistem üzerindeki 0-65535 arası sanal kapılar. Servislerin dış dünyaya açılan yüzüdür. Saldırı yüzeyini daraltmak için sadece zorunlu portlar (Örn: 443 HTTPS) açık tutulmalıdır.

### 2. Pratik Terminal Komutları ve Tehdit Avcılığı
* `ip a`: Sistemin fiziksel (MAC) ve mantıksal (IP) adreslerini doğrulamak için kullanılır.
* `ss -tulpn`: Sistemde aktif olarak "Dinleme (LISTEN)" modunda olan TCP/UDP portlarını ve bu portları işgal eden süreçlerin PID numaralarını listeler. Şüpheli arka kapıların (Backdoor) tespitinde ilk adımdır.
* `nc -lvp [Port]`: Netcat ile belirtilen portta test amaçlı dinleme başlatır.
* `dig [Domain]`: Hedef sistem hakkında DNS (Port 53/UDP) üzerinden bilgi toplama (A, MX, TXT kayıtları) ve OSINT çalışmalarında kullanılır. 
