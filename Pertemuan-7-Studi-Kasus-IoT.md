# 🏠 Pertemuan 7: Studi Kasus IoT pada Kandang dan Manajemen Ternak

> **"Teori tanpa praktik adalah kosong. Mari kita lihat bagaimana IoT benar-benar bekerja di lapangan!"**

---

## 👨‍🏫 Dosen Pengampu

- **Julinda** / **Yusuf** (Kelas A / Kelas B)

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Menganalisis implementasi IoT nyata di berbagai jenis peternakan
2. Mengidentifikasi komponen sistem IoT dalam studi kasus
3. Mengevaluasi keberhasilan dan tantangan implementasi
4. Merancang solusi IoT sederhana untuk permasalahan peternakan

---

## 📖 Pembuka: Belajar dari Pengalaman Nyata

**💭 "Saya sudah belajar teori IoT..."**

| ✅  | Materi Sebelumnya                             |
| --- | --------------------------------------------- |
| 1   | Pertemuan 1: Pengantar IoT                    |
| 2   | Pertemuan 2: Device, Gateway, Cloud, Aplikasi |
| 3   | Pertemuan 3: Sensor lingkungan                |
| 4   | Pertemuan 4: Aktuator & mikrokontroler        |
| 5   | Pertemuan 5: Komunikasi WiFi, LoRa, GSM       |
| 6   | Pertemuan 6: Dashboard monitoring             |

> ❓ **"Tapi... bagaimana semua ini DIGABUNGKAN dalam peternakan NYATA?"**

### 🎯 PERTEMUAN INI: STUDI KASUS!

Kita akan mempelajari **5 studi kasus nyata**:

| No  | Studi Kasus                   |
| --- | ----------------------------- |
| 1   | 🐔 Kandang Ayam Broiler       |
| 2   | 🥚 Kandang Ayam Petelur       |
| 3   | 🐄 Peternakan Sapi Perah      |
| 4   | 🐟 Budidaya Ikan (Akuakultur) |
| 5   | 🐐 Peternakan Kambing/Domba   |

---

## 🐔 STUDI KASUS 1: Smart Poultry Farm - Kandang Ayam Broiler

### Profil Kasus

**PROFIL: PT AYAM SEJAHTERA**

| Item            | Detail                          |
| --------------- | ------------------------------- |
| 📍 Lokasi       | Blitar, Jawa Timur              |
| 🏠 Kandang      | 4 unit @ 10.000 ekor            |
| 🐔 Total        | 40.000 ekor ayam broiler        |
| 👷 Pekerja      | 8 orang (sebelum IoT: 15 orang) |
| 📅 Implementasi | Januari 2024                    |
| 💰 Investasi    | Rp 120 juta (total 4 kandang)   |

**Masalah Sebelum IoT:**

- ❌ Mortalitas tinggi (6-8% per siklus)
- ❌ FCR buruk (rata-rata 1.9)
- ❌ Sulit mengontrol suhu malam hari
- ❌ Pekerja kelelahan (jaga malam)
- ❌ Tidak ada data historis

> 📚 **Catatan Akademis:**  
> Pendekatan seperti ini disebut _Precision Livestock Farming_ (PLF) - yaitu penggunaan teknologi untuk monitoring real-time guna mengoptimalkan produksi ternak (Berckmans, 2017).

### Arsitektur Sistem yang Diimplementasikan

**LAYER 1: SENSOR (per kandang)**

| Sensor               | Fungsi            | Jumlah  |
| -------------------- | ----------------- | ------- |
| 🌡️ DHT22             | Suhu + Kelembaban | 6 titik |
| 💨 MQ-135            | Amonia            | 2 titik |
| ⚖️ Load cell + HX711 | Timbangan         | 4 unit  |
| 💧 Flow sensor       | Konsumsi air      | 2 unit  |
| 🍽️ Hopper sensor     | Stok pakan        | 4 unit  |

**LAYER 2: MIKROKONTROLER**

- 🔌 ESP32 × 2 per kandang (sensor + aktuator)
- Total: 8 ESP32 untuk 4 kandang

**LAYER 3: GATEWAY**

- 📡 Raspberry Pi 4 + WiFi Router
- 1 unit di kantor farm (jangkauan 4 kandang)

**LAYER 4: CLOUD**

- ☁️ ThingsBoard (self-hosted di VPS)
- Biaya: Rp 200.000/bulan

**LAYER 5: APLIKASI**

- 📱 Dashboard web + Notifikasi WhatsApp
- 👤 User: Pemilik + Supervisor + Anak kandang

**AKTUATOR:**

| Aktuator            | Fungsi             | Jumlah        |
| ------------------- | ------------------ | ------------- |
| 💨 Exhaust fan      | Kontrol otomatis   | 8 per kandang |
| 🌬️ Cooling pad pump | Pendingin          | 2 per kandang |
| 💡 Dimmer lampu     | Kontrol intensitas | -             |
| 🚿 Misting system   | Pendingin darurat  | -             |

### Logika Otomasi yang Diterapkan

**🌡️ KONTROL SUHU**

| Kondisi                    | Aksi                                                    |
| -------------------------- | ------------------------------------------------------- |
| IF suhu > 30°C             | Kipas tambahan ON + Notifikasi "Suhu tinggi"            |
| IF suhu > 32°C             | Semua kipas ON 100% + Cooling pad ON + ALERT ke pemilik |
| IF suhu < 26°C (malam/DOC) | Heater ON + Kipas OFF                                   |

**💨 KONTROL AMONIA**

| Kondisi            | Aksi                                                         |
| ------------------ | ------------------------------------------------------------ |
| IF amonia > 15 ppm | Ventilasi ditingkatkan + Notifikasi "Cek litter"             |
| IF amonia > 25 ppm | ALERT: Ventilasi maksimal + Rekomendasi: Ganti litter segera |

**📊 MONITORING PAKAN**

| Kondisi                       | Aksi                           |
| ----------------------------- | ------------------------------ |
| IF stok pakan < 20%           | Notifikasi "Pesan pakan"       |
| IF konsumsi pakan turun > 15% | ALERT "Kemungkinan ayam sakit" |

### Hasil Setelah 6 Bulan

**PERBANDINGAN SEBELUM vs SESUDAH IoT**

| Parameter        | Sebelum  | Sesudah | Perubahan |
| ---------------- | -------- | ------- | --------- |
| Mortalitas       | 7%       | 3.5%    | ↓ 50%     |
| FCR              | 1.9      | 1.65    | ↓ 13%     |
| Berat panen      | 1.8 kg   | 2.0 kg  | ↑ 11%     |
| Lama panen       | 35 hari  | 33 hari | ↓ 2 hari  |
| Pekerja          | 15 orang | 8 orang | ↓ 47%     |
| Konsumsi listrik | 100%     | 85%     | ↓ 15%     |

**💰 DAMPAK FINANSIAL (per siklus 40.000 ekor)**

| Kategori                    | Perhitungan                                | Nilai               |
| --------------------------- | ------------------------------------------ | ------------------- |
| ✅ Penghematan mortalitas   | (7% - 3.5%) × 40.000 × Rp 25.000           | Rp 35.000.000       |
| ✅ Penghematan FCR          | (1.9 - 1.65) × 2kg × 40.000 × Rp 8.000/kg  | Rp 80.000.000       |
| ✅ Tambahan berat panen     | (2.0 - 1.8)kg × 40.000 × Rp 20.000/kg live | Rp 160.000.000      |
| ✅ Penghematan tenaga kerja | 7 orang × Rp 2.500.000/bulan               | Rp 17.500.000/bulan |

> 💎 **TOTAL BENEFIT PER SIKLUS: ± Rp 275.000.000**
> 💎 **ROI (Return on Investment): 4 bulan**

### Tantangan yang Dihadapi

| ⚠️ Tantangan                  | Masalah                             | Solusi                                         |
| ----------------------------- | ----------------------------------- | ---------------------------------------------- |
| 1. Sensor rusak karena amonia | Sensor DHT22 rusak dalam 3 bulan    | Ganti ke sensor industrial + casing tahan debu |
| 2. Koneksi WiFi tidak stabil  | Kandang dari baja mengganggu sinyal | Tambah access point + gunakan antena external  |
| 3. Pekerja tidak terbiasa     | Anak kandang bingung baca dashboard | Training 1 minggu + buat SOP sederhana         |
| 4. Listrik padam              | IoT mati saat listrik padam         | UPS untuk sistem kritis + notifikasi "offline" |

---

## 🥚 STUDI KASUS 2: Smart Layer Farm - Kandang Ayam Petelur

### Profil Kasus

**PROFIL: PETERNAKAN TELUR MAKMUR**

| Item            | Detail                          |
| --------------- | ------------------------------- |
| 📍 Lokasi       | Mojokerto, Jawa Timur           |
| 🏠 Kandang      | Sistem cage (battery) 3 tingkat |
| 🐔 Populasi     | 25.000 ekor ayam petelur        |
| 📅 Implementasi | Maret 2023                      |
| 💰 Investasi    | Rp 85 juta                      |

**Fokus IoT:**

- Optimasi produksi telur
- Monitoring kualitas telur
- Efisiensi pakan (feed efficiency)

### Komponen IoT yang Dipasang

**📊 SENSOR KHUSUS LAYER:**

| Sensor                          | Fungsi                                                                                  |
| ------------------------------- | --------------------------------------------------------------------------------------- |
| 🥚 **EGG COUNTER**              | Sensor infrared di conveyor belt, menghitung telur per jam/hari, mendeteksi telur pecah |
| 💡 **LIGHT SENSOR**             | Monitoring program lighting (16 jam terang : 8 jam gelap), dimmer otomatis              |
| 🍽️ **FEED CONSUMPTION TRACKER** | Load cell di feeder, gram/ekor/hari, alert jika makan abnormal                          |
| 🌡️ **SUHU & KELEMBABAN**        | Per tingkat cage (beda suhu atas-bawah!), 9 titik sensor (3 per tingkat)                |

**📊 DASHBOARD KHUSUS - PRODUKSI HARI INI:**

| Target | Actual    | HD%      | Pecah  |
| ------ | --------- | -------- | ------ |
| 21.250 | 20.875 🟡 | 83.5% 🟡 | 125 ✅ |

> **HD%** = Hen Day Production (produksi per ekor per hari)
> Target HD%: 85%

### Hasil yang Dicapai

**📈 PENINGKATAN PRODUKSI**

- HD% naik dari 82% → 87% (+5%)
- Artinya: +1.250 telur/hari
- Atau: +37.500 telur/bulan
- Nilai: 37.500 × Rp 1.800 = **Rp 67.500.000/bulan**

**📉 PENURUNAN KERUGIAN**

- Telur pecah turun dari 2% → 0.8%
- Penghematan: 300 telur/hari × Rp 1.500 = **Rp 450.000/hari**

**🍽️ EFISIENSI PAKAN**

- Konsumsi pakan turun 5% (kontrol lebih presisi)
- Penghematan: **Rp 15.000.000/bulan**

**⏰ PENGHEMATAN WAKTU**

- Penghitungan telur: dari 2 jam → otomatis
- Pencatatan produksi: dari manual → otomatis
- Laporan untuk mitra: 1 klik

---

## 🐄 STUDI KASUS 3: Smart Dairy Farm - Peternakan Sapi Perah

### Profil Kasus

**PROFIL: KOPERASI SUSU SEJAHTERA**

| Item            | Detail                    |
| --------------- | ------------------------- |
| 📍 Lokasi       | Pujon, Malang, Jawa Timur |
| 🐄 Populasi     | 150 ekor sapi perah (FH)  |
| 🥛 Produksi     | ± 2.500 liter/hari        |
| 📅 Implementasi | Juli 2023                 |
| 💰 Investasi    | Rp 250 juta               |
| 🤝 Mitra        | Koperasi Susu             |

**Masalah Sebelum IoT:**

- ❌ Sulit mendeteksi birahi (estrus)
- ❌ Mastitis terdeteksi terlambat
- ❌ Produksi tidak merata antar sapi
- ❌ Sulit tracking kesehatan individual

### Sistem IoT yang Diterapkan

**🏷️ SMART COLLAR (Kalung Pintar)**

Dipasang di leher setiap sapi, memantau:

| Parameter     | Fungsi                        | Keterangan                                             |
| ------------- | ----------------------------- | ------------------------------------------------------ |
| 🔄 AKTIVITAS  | Langkah per jam               | Sapi gelisah = mungkin birahi atau sakit               |
| 🍽️ RUMINATING | Waktu mengunyah (cud chewing) | Normal: 8-10 jam/hari. Kurang = ada masalah pencernaan |
| 🌡️ SUHU TUBUH | Via sensor ear tag            | Normal: 38-39°C. Tinggi = demam/infeksi                |

**📊 MILK METER (Pengukur Susu)**

Dipasang di mesin perah, memantau:

| Parameter       | Fungsi                       | Keterangan                      |
| --------------- | ---------------------------- | ------------------------------- |
| 🥛 VOLUME       | Liter per pemerahan per sapi | Mengukur produksi individual    |
| ⚡ CONDUCTIVITY | Daya hantar listrik susu     | Tinggi = indikasi mastitis!     |
| 🎨 WARNA        | Sensor optik                 | Abnormal = ada darah atau nanah |

**🌡️ ENVIRONMENT SENSOR**

- Suhu & kelembaban kandang
- Heat stress index
- Kualitas udara

> 💡 **Tahukah Anda?**  
> Deteksi birahi berbasis aktivitas memiliki akurasi 85-95% menurut penelitian Roelofs et al. (2010). Ini jauh lebih akurat dari deteksi visual manual (30-50%).

### Deteksi Birahi Otomatis - Fitur Andalan

**🔥 MENGAPA PENTING?**

- Birahi hanya 12-18 jam
- Waktu optimal IB: 12-18 jam setelah birahi mulai
- Gagal deteksi = gagal bunting = rugi 21 hari!

**📊 CARA KERJA DETEKSI:**

| Kondisi               | Aktivitas            | Ruminating    |
| --------------------- | -------------------- | ------------- |
| **Normal Day**        | 800 langkah/jam      | 9 jam/hari    |
| **Heat Day (Birahi)** | 2000+ langkah/jam ⬆️ | 4 jam/hari ⬇️ |

**📱 CONTOH NOTIFIKASI:**

> 🔔 **SAPI #47 (BELLA) kemungkinan BIRAHI!**
>
> - Aktivitas: 250% di atas normal
> - Ruminating: 55% di bawah normal
> - **Rekomendasi:** IB dalam 6-12 jam
> - **Konfirmasi:** Cek fisik → mucus bening, vulva bengkak

### Hasil Implementasi

**🔥 DETEKSI BIRAHI**

- Akurasi deteksi: 95% (sebelumnya 60% manual)
- Conception rate naik: 45% → 65%
- Calving interval turun: 450 hari → 390 hari

**🏥 DETEKSI PENYAKIT**

- Mastitis terdeteksi 24-48 jam lebih awal
- Biaya pengobatan turun 40%
- Kerugian susu afkir turun 60%

**🥛 PRODUKSI SUSU**

- Produksi naik 15% (heat stress management)
- Kualitas lebih konsisten

**💰 DAMPAK FINANSIAL**

| Kategori                          | Nilai            |
| --------------------------------- | ---------------- |
| Tambahan pendapatan susu          | Rp 45 juta/bulan |
| Penghematan biaya kesehatan       | Rp 8 juta/bulan  |
| Penghematan dari calving interval | Rp 15 juta/bulan |
| **ROI**                           | **4-5 bulan**    |

---

## 🐟 STUDI KASUS 4: Smart Aquaculture - Budidaya Ikan Lele

### Profil Kasus

**PROFIL: KOLAM LELE PAK AHMAD**

| Item            | Detail                            |
| --------------- | --------------------------------- |
| 📍 Lokasi       | Tulungagung, Jawa Timur           |
| 🏊 Kolam        | 10 kolam terpal @ 8×4 meter       |
| 🐟 Kapasitas    | 3.000 ekor/kolam = 30.000 ekor    |
| 📅 Implementasi | September 2023                    |
| 💰 Investasi    | Rp 45 juta (menggunakan eFishery) |

**Masalah Sebelum IoT:**

- ❌ Overfeed → pakan terbuang, air kotor
- ❌ Underfeed → ikan kurus, lama panen
- ❌ Kualitas air tidak terpantau
- ❌ Ikan mati mendadak (tidak tahu penyebab)

### Sistem IoT yang Diterapkan

**🍽️ SMART AUTO FEEDER (eFishery)**

- Pemberian pakan otomatis terjadwal
- Jumlah pakan sesuai algoritma (umur + biomassa)
- Mencatat total pakan otomatis
- Notifikasi jika pakan habis

**📊 WATER QUALITY SENSOR**

| Parameter    | Sensor    | Ideal Lele | Alert          |
| ------------ | --------- | ---------- | -------------- |
| Suhu air     | DS18B20   | 26-30°C    | <24 atau >32°C |
| pH           | pH Probe  | 6.5-8.5    | <6 atau >9     |
| DO (Oksigen) | DO Sensor | >3 mg/L    | <2 mg/L        |
| Amonia       | NH3 Probe | <0.02 mg/L | >0.05 mg/L     |

**🚨 EARLY WARNING SYSTEM**

- DO turun → Nyalakan aerator otomatis
- pH abnormal → Notifikasi + rekomendasi kapur
- Suhu tinggi → Alert ganti air

> 📚 **Catatan Akademis:**  
> Monitoring kualitas air real-time dapat meningkatkan survival rate hingga 20% menurut penelitian Føre et al. (2018) tentang _Precision Aquaculture_.

**📊 DASHBOARD KHUSUS:**

| Kolam   | Suhu    | pH     | DO     | Umur  | Est. Panen   |
| ------- | ------- | ------ | ------ | ----- | ------------ |
| Kolam 1 | 28°C ✅ | 7.2 ✅ | 4.5 ✅ | 45 hr | 15 hari lagi |
| Kolam 2 | 29°C ✅ | 7.0 ✅ | 3.2 🟡 | 30 hr | 30 hari lagi |
| Kolam 3 | 32°C 🔴 | 6.8 ✅ | 2.1 🔴 | 60 hr | Siap panen!  |

### Hasil yang Dicapai

| Parameter     | Sebelum    | Sesudah    | Perubahan |
| ------------- | ---------- | ---------- | --------- |
| FCR           | 1.3        | 1.0        | ↓ 23%     |
| Survival Rate | 75%        | 90%        | ↑ 15%     |
| Lama panen    | 90 hari    | 75 hari    | ↓ 15 hari |
| Berat panen   | 100 g      | 120 g      | ↑ 20%     |
| Waktu kerja   | 6 jam/hari | 2 jam/hari | ↓ 67%     |

**💰 PERHITUNGAN FINANSIAL (per siklus 30.000 ekor)**

**SEBELUM IoT:**

- Panen: 22.500 ekor × 100g × Rp 22.000/kg = **Rp 49.500.000**
- Pakan: FCR 1.3 × 2.250 kg = 2.925 kg × Rp 8.000 = **Rp 23.400.000**
- Profit: **Rp 26.100.000**

**SESUDAH IoT:**

- Panen: 27.000 ekor × 120g × Rp 22.000/kg = **Rp 71.280.000**
- Pakan: FCR 1.0 × 3.240 kg = 3.240 kg × Rp 8.000 = **Rp 25.920.000**
- Profit: **Rp 45.360.000**

> 📈 **PENINGKATAN PROFIT: Rp 19.260.000/siklus (+74%)**

---

## 🐐 STUDI KASUS 5: Smart Goat Farm - Peternakan Kambing

### Profil Kasus

**PROFIL: PETERNAKAN KAMBING BERKAH**

| Item            | Detail                                |
| --------------- | ------------------------------------- |
| 📍 Lokasi       | Lumajang, Jawa Timur                  |
| 🐐 Populasi     | 200 ekor kambing PE (Peranakan Etawa) |
| 🥛 Fokus        | Kambing perah + pedaging              |
| 📅 Implementasi | Mei 2024                              |
| 💰 Investasi    | Rp 65 juta (DIY + konsultan lokal)    |

**Keunikan:**
Sistem semi-intensif, kambing di kandang malam, siang digembalakan.

### Sistem IoT yang Diterapkan

**📍 GPS TRACKER (untuk kambing indukan)**

- Kalung GPS untuk 20 indukan terbaik
- Tracking lokasi saat digembalakan
- Geo-fencing: alert jika keluar area
- History: berapa km jalan per hari

**🏥 HEALTH MONITORING**

- Ear tag dengan sensor suhu
- Normal: 38.5-40°C
- Demam = alert untuk cek kesehatan

**⚖️ SMART WEIGHING**

- Timbangan otomatis di pintu kandang
- Kambing ditimbang setiap keluar/masuk
- ID via RFID ear tag
- Data ADG otomatis tercatat

**🥛 MILK RECORDING (untuk kambing perah)**

- Volume susu per ekor per pemerahan
- History produksi susu
- Identifikasi kambing produktif vs afkir

**🌡️ ENVIRONMENT (kandang)**

- Suhu & kelembaban
- Amonia (kambing sensitif bau)
- Ventilasi otomatis

### Manfaat yang Dirasakan

**🐐 MANAJEMEN INDIVIDU**

- Setiap kambing punya "kartu identitas digital"
- History: berat, produksi susu, kesehatan, keturunan
- Seleksi breeding lebih akurat

**📍 PENCEGAHAN KEHILANGAN**

- 2 kasus kambing hampir "nyasar" terdeteksi cepat
- Geo-fence mengurangi risiko pencurian

**🏥 KESEHATAN**

- 3 kasus demam terdeteksi 2 hari lebih awal
- Mencegah penularan ke kambing lain

**💰 EFISIENSI**

- Operator berkurang dari 4 → 2 orang
- Waktu recording: 3 jam → 15 menit (otomatis)

---

## 📊 Perbandingan 5 Studi Kasus

| Aspek            | BROILER         | LAYER           | DAIRY            | LELE          | KAMBING           |
| ---------------- | --------------- | --------------- | ---------------- | ------------- | ----------------- |
| **Investasi**    | Rp 120jt        | Rp 85jt         | Rp 250jt         | Rp 45jt       | Rp 65jt           |
| **ROI**          | 4 bulan         | 3 bulan         | 5 bulan          | 3 bulan       | 6 bulan           |
| **Sensor Utama** | Env+Prod        | Env+Egg Counter | Collar+Milk      | Water Quality | GPS+RFID+Scale    |
| **Fokus**        | FCR, Mortalitas | HD%, FCR        | Estrus, Mastitis | FCR, Survival | Tracking Individu |
| **Platform**     | ThingsBoard     | Chickin         | Vendor Lokal     | eFishery      | DIY + Blynk       |

**📌 PELAJARAN UTAMA:**

1. Investasi berbeda sesuai kompleksitas dan skala
2. ROI umumnya 3-6 bulan
3. Sensor disesuaikan dengan kebutuhan spesifik ternak
4. Ada solusi siap pakai (eFishery, Chickin) dan DIY

---

## 🧠 Pelajaran dari Studi Kasus

### Faktor Keberhasilan

```
┌─────────────────────────────────────────────────────────────────┐
│              KUNCI SUKSES IMPLEMENTASI IoT                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ✅ FAKTOR KEBERHASILAN:                                       │
│   ─────────────────────────────────────────────────────────────│
│                                                                 │
│   1. MULAI DARI MASALAH, BUKAN TEKNOLOGI                       │
│      • Identifikasi dulu: apa masalah terbesar?                │
│      • Baru cari solusi IoT yang tepat                         │
│      • Jangan pasang sensor "karena keren"                     │
│                                                                 │
│   2. MULAI KECIL, SCALE UP BERTAHAP                            │
│      • Pilot di 1 kandang dulu                                  │
│      • Evaluasi, perbaiki, baru perluas                        │
│      • Kurangi risiko investasi besar gagal                    │
│                                                                 │
│   3. TRAINING UNTUK PEKERJA                                     │
│      • Teknologi bagus + SDM tidak siap = gagal               │
│      • Libatkan pekerja lapangan dari awal                     │
│      • Buat SOP sederhana dan jelas                            │
│                                                                 │
│   4. MAINTENANCE PLAN                                           │
│      • Sensor perlu perawatan rutin                            │
│      • Siapkan spare parts                                      │
│      • Punya kontak teknisi/vendor                             │
│                                                                 │
│   5. DATA HARUS DITINDAKLANJUTI                                 │
│      • Data bagus tapi tidak dipakai = sia-sia                │
│      • Buat protokol: "jika X, maka lakukan Y"                 │
│      • Review data berkala (mingguan)                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Kesalahan yang Harus Dihindari

```
┌─────────────────────────────────────────────────────────────────┐
│              KESALAHAN UMUM                                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ❌ JANGAN LAKUKAN:                                            │
│   ─────────────────────────────────────────────────────────────│
│                                                                 │
│   1. OVER-ENGINEERING                                           │
│      ✗ Pasang 50 sensor padahal butuh 10                       │
│      ✓ Mulai dengan sensor esensial dulu                       │
│                                                                 │
│   2. MENGABAIKAN INFRASTRUKTUR                                  │
│      ✗ Beli sensor mahal, WiFi masih lemot                     │
│      ✓ Pastikan koneksi internet stabil dulu                   │
│                                                                 │
│   3. TIDAK ADA BACKUP PLAN                                      │
│      ✗ IoT mati = kandang tanpa monitoring                     │
│      ✓ Tetap ada pengecekan manual sebagai backup              │
│                                                                 │
│   4. TERLALU PERCAYA 100% PADA SENSOR                           │
│      ✗ Sensor bilang OK, tidak pernah cek fisik               │
│      ✓ Sensor = alat bantu, bukan pengganti mata peternak     │
│                                                                 │
│   5. TIDAK MENGKALIBRASI                                        │
│      ✗ Sensor tidak pernah dikalibrasi                         │
│      ✓ Kalibrasi rutin setiap 3-6 bulan                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 Manajemen Ternak Berbasis IoT

> **"IoT bukan hanya tentang sensor dan data, tapi tentang MANAJEMEN yang lebih baik!"**

### Apa itu Manajemen Ternak?

```
DEFINISI MANAJEMEN TERNAK
=========================

Manajemen Ternak = Seni & ilmu mengelola peternakan
untuk mencapai tujuan produksi secara efisien

```

**Aspek-Aspek Manajemen Ternak:**

| No  | Aspek         | Nama Inggris         |
| --- | ------------- | -------------------- |
| 1   | 🏥 Kesehatan  | Health Management    |
| 2   | 👥 Populasi   | Herd Management      |
| 3   | 🍽️ Pakan      | Feed Management      |
| 4   | 🔄 Reproduksi | Breeding Management  |
| 5   | 👷 SDM        | HR Management        |
| 6   | 💰 Finansial  | Financial Management |

**🔑 IoT membantu SEMUA aspek ini menjadi lebih:**

- ✅ **Terukur** (data-driven)
- ✅ **Efisien** (hemat waktu & tenaga)
- ✅ **Akurat** (keputusan tepat)
- ✅ **Proaktif** (deteksi dini)

---

### 🏥 1. Manajemen Kesehatan (Health Management)

**Apa yang Dikelola?**

- Riwayat kesehatan setiap individu
- Jadwal vaksinasi & pengobatan
- Deteksi dini penyakit
- Pencatatan obat & vitamin yang diberikan

**Bagaimana IoT Membantu?**

#### 1️⃣ Health Recording Otomatis

**Contoh: SAPI #47 - BELLA**

| Tanggal     | Event                    | Status    |
| ----------- | ------------------------ | --------- |
| 15 Jan 2026 | Vaksin PMK               | ✅        |
| 20 Feb 2026 | Vitamin B-complex        | ✅        |
| 05 Mar 2026 | Mastitis ringan          | ✅ Sembuh |
| 10 Mar 2026 | Obat intramammary 3 hari | ✅        |

> 🔔 **Pengingat:**
>
> - Vaksinasi berikutnya: 15 Jul 2026
> - Cek mastitis rutin: setiap pemerahan

#### 2️⃣ Deteksi Dini Otomatis

| Tanda       | Terdeteksi Oleh | Alert                 |
| ----------- | --------------- | --------------------- |
| Demam       | Sensor suhu     | "Suhu >40°C!"         |
| Tidak makan | Feed sensor     | "Konsumsi turun 30%"  |
| Lesu        | Activity sensor | "Aktivitas turun 50%" |
| Mastitis    | Conductivity    | "SCC tinggi!"         |

#### 3️⃣ Jadwal Vaksinasi Otomatis

**Jadwal Vaksinasi Bulan Ini:**

| Tanggal | Vaksin  | Target                 |
| ------- | ------- | ---------------------- |
| 10 Feb  | ND+IB   | Kandang A (5.000 ekor) |
| 15 Feb  | Gumboro | Kandang B (5.000 ekor) |
| 20 Feb  | AI      | Semua kandang          |

**Sistem Notifikasi:**

- 📱 H-3: "Siapkan vaksin ND+IB"
- 📱 H-1: "Besok vaksinasi kandang A"
- 📱 H+1: "Konfirmasi vaksinasi selesai?"

**💡 Manfaat:**

- Tidak ada vaksinasi yang terlewat
- Riwayat kesehatan lengkap untuk tiap individu
- Penyakit terdeteksi 1-2 hari lebih awal
- Laporan kesehatan untuk dokter hewan siap 1 klik

---

### 👥 2. Manajemen Populasi (Herd/Flock Management)

**Apa yang Dikelola?**

- Data identitas setiap individu
- Silsilah/keturunan (genetic tracking)
- Performa individu (berat, produksi)
- Keputusan culling (afkir) & seleksi

**Bagaimana IoT Membantu?**

#### 1️⃣ Identitas Digital (RFID/Ear Tag)

> Setiap ternak punya **"KTP Digital"**!

**Contoh Data Identitas - SAPI BELLA:**

| Field             | Data                      |
| ----------------- | ------------------------- |
| 🏷️ ID             | SAPI-2024-047             |
| 📛 Nama           | BELLA                     |
| 🎂 Lahir          | 15 Maret 2022 (2 tahun)   |
| 👪 Induk/Pejantan | SARI (#032) / BEJO (#015) |
| 🏠 Lokasi         | Kandang B, Stall #12      |
| 📊 Status         | Laktasi ke-2, bulan ke-5  |

#### 2️⃣ Tracking Performa Individu

**Performa BELLA (SAPI-2024-047):**

| Aspek               | Data                                   |
| ------------------- | -------------------------------------- |
| 🥛 Produksi Susu    | Laktasi 1: 12L → Laktasi 2: 15L (↑25%) |
| ⚖️ Berat Badan      | Lahir: 35kg → Sekarang: 450kg          |
| 🔄 Calving Interval | 380 hari ✅ (target <400)              |
| 📊 Conception Rate  | 2 IB (baik)                            |
| 🏆 Ranking          | #5 dari 150 sapi (TOP 5%)              |

#### 3️⃣ Seleksi & Culling Berbasis Data

**Rekomendasi Sistem:**

| Kategori           | Ternak        | Alasan                            |
| ------------------ | ------------- | --------------------------------- |
| 🌟 **PERTAHANKAN** | BELLA (#047)  | Produksi tinggi, reproduksi baik  |
| 🌟 **PERTAHANKAN** | CANTIK (#023) | Produksi stabil, mudah bunting    |
| ⚠️ **EVALUASI**    | DEWI (#089)   | Produksi menurun 20%              |
| ⚠️ **EVALUASI**    | MAWAR (#067)  | 3x IB gagal                       |
| ❌ **AFKIR**       | MELATI (#045) | 4x IB gagal, produksi rendah      |
| ❌ **AFKIR**       | TUA (#012)    | Umur 10 tahun, produksi turun 50% |

> 💡 **Keputusan tetap di tangan peternak!** Sistem hanya memberi rekomendasi.

#### 4️⃣ Genetic Tracking

**Silsilah BELLA:**

```

          NENEK              KAKEK
         PUTRI ─────────── JAGOAN
                   │
          ─────────┴─────────
                   │
          INDUK           PEJANTAN
          SARI ─────────── BEJO
                   │
          ─────────┴─────────
                   │
            ┌──────┴──────┐
            │             │
          BELLA         DINI
         (#047)        (#048)

```

> 💡 **Manfaat:** Hindari inbreeding dengan tracking silsilah otomatis!

**💡 Manfaat Manajemen Populasi:**

- Keputusan seleksi berbasis data, bukan "feeling"
- Cegah inbreeding dengan tracking silsilah
- Identifikasi ternak produktif vs tidak
- Nilai jual ternak unggulan lebih tinggi

---

### 👷 3. Manajemen SDM (Sumber Daya Manusia)

**Apa yang Dikelola?**

- Jadwal tugas pekerja
- Monitoring pekerjaan
- Pembagian shift jaga
- Efisiensi tenaga kerja

**Bagaimana IoT Membantu?**

#### 1️⃣ Otomasi = Kurangi Kebutuhan Tenaga

| Aktivitas    | Sebelum IoT    | Sesudah IoT              |
| ------------ | -------------- | ------------------------ |
| Cek suhu     | Manual 6x/hari | Otomatis setiap menit    |
| Jaga malam   | 2 orang        | Alert ke HP jika masalah |
| Rekap data   | Manual 3 jam   | Laporan otomatis 1 klik  |
| Hitung telur | Manual 2 jam   | Counter otomatis         |

**Dampak:**

- Tenaga kerja: 15 orang → 8 orang
- Shift jaga malam: 2 shift → 1 shift (on-call)
- Pekerja fokus ke pekerjaan yang butuh keahlian

#### 2️⃣ Task Management Digital

**Contoh: Tugas Hari Ini - Pak Joko**

| Jam   | Tugas                                  | Status      |
| ----- | -------------------------------------- | ----------- |
| 06:00 | Pemberian pakan pagi                   | ✅ Otomatis |
| 07:00 | Penimbangan ayam sampling (50 ekor)    | ⏳          |
| 09:00 | Ganti litter kandang A (amonia tinggi) | ⏳          |
| 12:00 | Cek cooling pad (cuaca panas)          | ⏳          |
| 18:00 | Pemberian pakan sore                   | ✅ Otomatis |

> ⚠️ **ALERT:** Kipas #3 kandang B error, perlu dicek!

#### 3️⃣ Monitoring Kinerja Pekerja

| Pekerja  | Tugas Selesai | Response Time | Mortalitas | Status      |
| -------- | ------------- | ------------- | ---------- | ----------- |
| Pak Joko | 95%           | 5 menit ✅    | 3.2% ✅    | 🟢 Baik     |
| Bu Sri   | 88%           | 15 menit ⚠️   | 4.5% ⚠️    | 🟡 Evaluasi |

> 💡 **Evaluasi:** Perlu training ulang untuk Bu Sri

#### 4️⃣ Komunikasi Terintegrasi

**Contoh Grup WhatsApp Otomatis:**

> 🤖 **BOT KANDANG (08:30):** Suhu kandang A 31°C. @PakJoko tolong cek kipas.
>
> 👤 **Pak Joko:** Sudah dicek, kipas #2 macet. Sudah diperbaiki.
>
> 🤖 **BOT KANDANG (08:45):** Suhu turun ke 28°C. ✅
>
> 👨‍💼 **Supervisor:** Good job, Pak Joko! 👍

**💡 Manfaat Manajemen SDM:**

- Supervisor tidak perlu di kandang 24 jam
- Tanggung jawab jelas (siapa mengerjakan apa)
- Evaluasi kinerja berbasis data
- Koordinasi tim lebih efisien

---

### 💰 4. Manajemen Finansial (Financial Management)

**Apa yang Dikelola?**

- Biaya operasional (pakan, obat, listrik)
- Pendapatan (penjualan ternak/produk)
- Profitabilitas per kandang/individu
- Laporan keuangan & analisis

**Bagaimana IoT Membantu?**

#### 1️⃣ Tracking Biaya Otomatis

**Biaya Operasional - Kandang A (Februari 2026)**

| Kategori         | Detail                  | Total             |
| ---------------- | ----------------------- | ----------------- |
| 🍽️ Pakan         | 4.500 kg × Rp 8.000/kg  | Rp 36.000.000     |
| 💊 Obat & Vaksin | ND+IB, Gumboro, Vitamin | Rp 1.200.000      |
| ⚡ Listrik       | Runtime kipas/heater    | Rp 2.500.000      |
| **TOTAL**        |                         | **Rp 39.700.000** |

#### 2️⃣ Proyeksi Pendapatan

**Proyeksi Penjualan - Kandang A:**

| Data                    | Nilai                      |
| ----------------------- | -------------------------- |
| Populasi hidup          | 4.850 ekor (mortalitas 3%) |
| Berat rata-rata         | 2.1 kg                     |
| Total biomassa          | 10.185 kg                  |
| Harga pasar             | Rp 21.000/kg live          |
| **PROYEKSI PENDAPATAN** | **Rp 213.885.000**         |

**Estimasi Profit:**

- Pendapatan: Rp 213.885.000
- Biaya: Rp 39.700.000
- DOC: Rp 25.000.000
- **PROFIT: Rp 149.185.000** ✅

#### 3️⃣ Analisis Profitabilitas

**Perbandingan 4 Kandang:**

| Kandang | FCR  | Mort% | Profit/ekor | Status     |
| ------- | ---- | ----- | ----------- | ---------- |
| A       | 1.62 | 3.0%  | Rp 30.760   | 🟢 Best    |
| B       | 1.68 | 3.5%  | Rp 28.500   | 🟢 Good    |
| C       | 1.75 | 4.2%  | Rp 25.200   | 🟡 Average |
| D       | 1.85 | 5.1%  | Rp 21.000   | 🔴 Poor    |

> 💡 **Analisis:** Kandang D perlu evaluasi!
>
> - FCR tinggi → cek kualitas pakan
> - Mortalitas tinggi → cek kesehatan

#### 4️⃣ Laporan untuk Stakeholder

**Laporan Tersedia (1 Klik):**

| Untuk         | Jenis Laporan                                   |
| ------------- | ----------------------------------------------- |
| 📊 Pemilik    | Profit bulanan, trend 12 bulan, ROI per kandang |
| 🏦 Bank       | Aset, cash flow, proyeksi pendapatan            |
| 🤝 Mitra/Inti | Performa (FCR, mortality), penggunaan pakan     |
| 🏛️ Dinas      | Populasi, kesehatan, vaksinasi                  |

**💡 Manfaat Manajemen Finansial:**

- Tahu persis berapa profit setiap kandang
- Identifikasi kandang yang tidak profitable
- Laporan siap untuk berbagai keperluan
- Data untuk keputusan investasi

---

### 🔄 5. Manajemen Reproduksi (Breeding Management)

**Apa yang Dikelola?**

- Deteksi birahi (estrus)
- Jadwal IB (Inseminasi Buatan)
- Pemeriksaan kebuntingan
- Pencatatan kelahiran
- Penyapihan & periode kering

**Bagaimana IoT Membantu?**

#### 1️⃣ Timeline Reproduksi Otomatis

Contoh: **SAPI BELLA (#047) - Calendar Reproduksi**

| Tanggal | Event        | Keterangan                 |
| ------- | ------------ | -------------------------- |
| 10 Jan  | 🔥 Birahi    | Aktivitas 250% dari normal |
| 11 Jan  | 💉 IB        | Semen: SUPER-001           |
| 01 Feb  | ⏰ Reminder  | Cek birahi ulang (21 hari) |
| 10 Mar  | 🔍 PKB       | Pemeriksaan Kebuntingan    |
| 10 Mar  | ✅ Hasil     | BUNTING ±60 hari           |
| 17 Okt  | 📅 Perkiraan | Melahirkan (280 hari)      |
| 01 Okt  | 🔔 Reminder  | Masa kering (2 mg sebelum) |

#### 2️⃣ Notifikasi Proaktif

**Contoh Notifikasi Hari Ini:**

> 🔥 **08:00** - SARI (#032) menunjukkan tanda birahi!
>
> - Aktivitas: +180% dari normal
> - Rekomendasi: IB dalam 8-14 jam

> ⏰ **09:00** - DEWI (#089) hari ke-21 pasca IB
>
> - Perhatikan tanda birahi ulang
> - Jika tidak birahi: kemungkinan BUNTING

> 🔍 **10:00** - MAWAR (#067) sudah 60 hari pasca IB
>
> - Jadwalkan PKB dengan dokter hewan

> 📅 **14:00** - BELLA (#047) estimasi melahirkan 7 hari
>
> - Pindahkan ke kandang melahirkan
> - Siapkan peralatan

#### 3️⃣ Analisis Efisiensi Reproduksi

**Rekap Reproduksi 2025:**

| Indikator              | Nilai         | Status |
| ---------------------- | ------------- | ------ |
| Total IB               | 120 kali      | -      |
| Berhasil bunting       | 78 ekor (65%) | ✅     |
| Birahi ulang           | 42 ekor (35%) | -      |
| Service per conception | 1.8           | ✅     |
| Calving interval       | 385 hari      | ✅     |

**Perbandingan dengan tahun lalu (tanpa IoT):**

- Conception rate: 45% → 65% (↑ 20%)
- Calving interval: 450 → 385 hari (↓ 65 hari)

**💡 Manfaat:**

- Tidak ada birahi yang terlewat
- Timing IB lebih tepat = conception rate naik
- Pengingat otomatis untuk semua milestone
- Calving interval lebih pendek = lebih produktif

---

### 📊 Integrasi Semua Aspek Manajemen

> **"Semua aspek manajemen TERHUBUNG dalam satu sistem!"**

```
                    ┌──────────────────┐
                    │  DASHBOARD UTAMA │
                    │  (Satu Layar)    │
                    └────────┬─────────┘
                             │
    ┌────────┬───────┬───────┼───────┬────────┐
    ▼        ▼       ▼       ▼       ▼        ▼
┌────────┐┌────────┐┌────────┐┌────────┐┌────────┐
│Health  ││Populasi││ Pakan  ││ Repro  ││Finance │
└────┬───┘└───┬────┘└───┬────┘└───┬────┘└───┬────┘
     └────────┴─────────┴────┬────┴─────────┘
                             ▼
                    ┌──────────────┐
                    │ DATA TERNAK  │
                    └──────────────┘
```

#### Contoh Integrasi: SAPI BELLA (#047)

| Aspek         | Data                           | Status           |
| ------------- | ------------------------------ | ---------------- |
| 🏥 Kesehatan  | Sehat, vaksinasi lengkap       | ✅               |
| 👥 Populasi   | Umur 2 tahun, ranking #5       | ✅               |
| 🍽️ Pakan      | Konsumsi 25 kg/hari (normal)   | ✅               |
| 🔄 Reproduksi | Bunting 5 bulan, lahir Oktober | ✅               |
| 💰 Finansial  | Profit Rp 45 juta/tahun        | ⭐ Above Average |

**→ KEPUTUSAN: Pertahankan & jadikan indukan unggulan!**

---

## 📝 Rangkuman Pertemuan 7

### 📚 5 Studi Kasus yang Dipelajari:

| No  | Jenis Ternak | Fokus IoT                  |
| --- | ------------ | -------------------------- |
| 1   | 🐔 Broiler   | FCR, mortalitas, suhu      |
| 2   | 🥚 Layer     | HD%, pencatatan telur      |
| 3   | 🐄 Dairy     | Estrus detection, mastitis |
| 4   | 🐟 Lele      | Kualitas air, auto feeding |
| 5   | 🐐 Kambing   | Tracking individu, GPS     |

### 💡 Pelajaran Utama:

- IoT bukan "one size fits all"
- Disesuaikan dengan jenis ternak & masalah
- ROI rata-rata 3-6 bulan
- Training SDM sama pentingnya dengan teknologi
- Mulai kecil, scale up bertahap

### 🎯 Pesan Utama:

> **"Teknologi adalah ALAT, bukan TUJUAN.**
> **Tujuan tetap: ternak sehat, produktif, menguntungkan!"**

---

## ❓ Pertanyaan Diskusi

1. **Dari 5 studi kasus, mana yang paling menarik bagi Anda? Mengapa?**

2. **Jika Anda adalah peternak ayam broiler skala kecil (2.000 ekor), parameter apa yang akan Anda prioritaskan untuk dimonitor?**

3. **Apa tantangan terbesar implementasi IoT di peternakan Indonesia menurut Anda?**

4. **Bagaimana pendapat Anda tentang penggunaan GPS tracker untuk ternak? Apakah worth it?**

5. **Jika memiliki budget Rp 50 juta, jenis ternak apa yang akan Anda pilih untuk implementasi IoT pertama kali?**

---

## 📚 Istilah Penting Pertemuan Ini

| Istilah              | Arti                                                    |
| -------------------- | ------------------------------------------------------- |
| **FCR**              | Feed Conversion Ratio - rasio pakan terhadap berat      |
| **HD%**              | Hen Day Production - produksi telur per ekor per hari   |
| **Estrus**           | Masa birahi / masa subur pada betina                    |
| **Mastitis**         | Infeksi/radang pada ambing (kelenjar susu)              |
| **DO**               | Dissolved Oxygen - oksigen terlarut dalam air           |
| **Conception Rate**  | Tingkat keberhasilan bunting setelah IB                 |
| **Calving Interval** | Jarak waktu antar kelahiran                             |
| **Geo-fencing**      | Batas virtual geografis untuk tracking                  |
| **RFID**             | Radio Frequency Identification - identifikasi via radio |
| **Survival Rate**    | Tingkat kelangsungan hidup                              |

---

## 🎯 Tugas Pertemuan 7

### Tugas Kelompok (3-4 orang)

**Analisis Studi Kasus**

1. Pilih SATU jenis peternakan (selain yang dibahas di kelas)
   - Contoh: bebek, kelinci, lebah, cacing, burung puyuh, dll.

2. Rancang sistem IoT sederhana untuk peternakan tersebut:
   - Identifikasi 3 masalah utama
   - Tentukan sensor yang dibutuhkan
   - Gambar arsitektur sederhana
   - Perkirakan investasi dan ROI

3. Presentasi 10 menit di Pertemuan 9 (setelah UTS)

---

> 📌 **Pertemuan Selanjutnya:** UTS (Ujian Tengah Semester)
>
> Materi UTS: Pertemuan 1-7

---

## 🔗 Koneksi dengan Materi Sebelumnya

```

┌─────────────────────────────────────────────────────────────────┐
│ INTEGRASI SEMUA PERTEMUAN │
├─────────────────────────────────────────────────────────────────┤
│ │
│ Setiap studi kasus menggunakan SEMUA yang sudah dipelajari: │
│ │
│ Pertemuan 1: KONSEP IoT │
│ ↓ diterapkan dalam studi kasus nyata │
│ │
│ Pertemuan 2: DEVICE + GATEWAY + CLOUD + APP │
│ ↓ terlihat dalam arsitektur setiap kasus │
│ │
│ Pertemuan 3: SENSOR │
│ ↓ DHT22, MQ-135, pH, DO, load cell... │
│ │
│ Pertemuan 4: AKTUATOR + MIKROKONTROLER │
│ ↓ Fan, pump, heater, ESP32, Arduino... │
│ │
│ Pertemuan 5: KOMUNIKASI │
│ ↓ WiFi, LoRa, GSM dalam studi kasus │
│ │
│ Pertemuan 6: DASHBOARD │
│ ↓ Tampilan monitoring di setiap kasus │
│ │
│ SEKARANG: Pertemuan 7 - MELIHAT SEMUANYA BEKERJA BERSAMA! │
│ │
└─────────────────────────────────────────────────────────────────┘

```

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_
_Program Studi Peternakan - Universitas Mulawarman_
_Semester Genap 2025/2026_

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna jika Anda ingin mempelajari lebih dalam atau mengutip untuk tugas/skripsi tentang studi kasus IoT peternakan.

### Sumber Akademik

| No  | Referensi                                                                                                                                | Keterangan             |
| --- | ---------------------------------------------------------------------------------------------------------------------------------------- | ---------------------- |
| 1   | Berckmans, D. (2017). General introduction to precision livestock farming. _Animal Frontiers_, 7(1), 6-11.                               | Pengantar PLF          |
| 2   | Roelofs, J., et al. (2010). When is a cow in estrus? Clinical and practical aspects. _Theriogenology_, 74(3), 327-344.                   | Deteksi birahi         |
| 3   | Føre, M., et al. (2018). Precision fish farming: A new framework. _Biosystems Engineering_, 173, 176-193.                                | Smart aquaculture      |
| 4   | Neethirajan, S. (2017). Recent advances in wearable sensors for animal health management. _Sensing and Bio-Sensing Research_, 12, 15-29. | Wearable sensor ternak |
| 5   | Benjamin, M., & Yik, S. (2019). Precision livestock farming in swine welfare. _Frontiers in Veterinary Science_, 6, 318.                 | PLF dan kesejahteraan  |

### Platform dan Produk Indonesia

| No  | Referensi                                                                     | Keterangan         |
| --- | ----------------------------------------------------------------------------- | ------------------ |
| 6   | eFishery. _Smart Feeding Solution for Aquaculture_. Tersedia di: efishery.com | Auto-feeder ikan   |
| 7   | Chickin Indonesia. _Smart Poultry Farming_. Tersedia di: chickin.id           | IoT ayam           |
| 8   | PITIK. _Integrated Poultry Technology_. Tersedia di: pitik.id                 | Kemitraan ayam IoT |

### Dokumentasi Teknis

| No  | Referensi                                                              | Keterangan         |
| --- | ---------------------------------------------------------------------- | ------------------ |
| 9   | ThingsBoard. _IoT Platform Documentation_. Tersedia di: thingsboard.io | Platform dashboard |
| 10  | Blynk. _Getting Started Guide_. Tersedia di: blynk.io/docs             | Platform IoT DIY   |
