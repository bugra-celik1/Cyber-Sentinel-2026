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
