# 🐔 Pertemuan 12: Penerapan Smart Poultry System

> **Dosen Pengampu:** Nurul Fajrih & Rizkuna  
> **Waktu:** 100 menit  
> **Semester Genap 2025/2026**

---

> 💬 **"Smart Poultry System adalah orkestrasi sempurna antara sensor, AI, dan aktuator - bekerja bersama 24/7 untuk peternak yang lebih sejahtera!"**

---

## 🎯 Tujuan Pembelajaran

Setelah mengikuti pertemuan ini, mahasiswa diharapkan mampu:

1. ✅ Memahami konsep Smart Poultry System secara menyeluruh
2. ✅ Menjelaskan komponen-komponen yang terintegrasi dalam sistem
3. ✅ Menganalisis alur kerja sistem dari sensor hingga aksi
4. ✅ Mengevaluasi contoh implementasi Smart Poultry System di Indonesia

---

## 🎬 Cerita Pembuka: Evolusi Peternakan Ayam

### 📅 Perjalanan Pak Surya: 20 Tahun Beternak

| Era                      | Cara Kerja                                      | Tantangan                                            |
| ------------------------ | ----------------------------------------------- | ---------------------------------------------------- |
| **2005 (Manual)**        | Cek suhu pakai termometer, kipas diatur manual  | Sering ketiduran, ayam mati kepanasan malam          |
| **2010 (Semi-Otomatis)** | Termostat sederhana untuk kipas                 | Tidak tahu kondisi real-time, tetap harus ke kandang |
| **2015 (IoT Dasar)**     | Sensor + HP, bisa monitoring jarak jauh         | Data banyak tapi bingung mau ngapain                 |
| **2020 (Smart System)**  | Semua terintegrasi, AI yang mengambil keputusan | "Akhirnya saya bisa tidur nyenyak!" 😴               |

### 🎉 Hasil Transformasi Pak Surya

| Aspek             | 2005 (Manual) | 2020 (Smart) | Perubahan |
| ----------------- | ------------- | ------------ | --------- |
| Mortalitas        | 8%            | 3%           | ⬇️ 62.5%  |
| FCR               | 1.95          | 1.58         | ⬇️ 19%    |
| Waktu di kandang  | 12 jam/hari   | 2 jam/hari   | ⬇️ 83%!   |
| Profit per siklus | Rp 15 juta    | Rp 45 juta   | ⬆️ 200%!  |

> 💡 **Pak Surya:** "Dulu saya kerja UNTUK kandang. Sekarang kandang bekerja UNTUK saya!"

---

## 📖 BAGIAN 1: Apa Itu Smart Poultry System?

### 📝 Definisi Sederhana

> 💡 **Smart Poultry System** adalah sistem peternakan unggas terintegrasi yang menggabungkan **sensor**, **konektivitas**, **AI/analytics**, dan **aktuator** untuk mengelola kandang secara **otomatis** dan **cerdas**.

### 🔄 Perbedaan dengan Sistem Sebelumnya

```
┌─────────────────────────────────────────────────────────────────┐
│           EVOLUSI SISTEM PETERNAKAN UNGGAS                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1️⃣ MANUAL (Era Kakek)                                        │
│   ═══════════════════════════════════════════════════════════   │
│   Manusia → Cek kondisi → Ambil keputusan → Aksi manual        │
│                                                                 │
│   Contoh: "Hmm, kayaknya panas nih" → Nyalakan kipas           │
│   ⚠️ Lambat, subjektif, kelelahan                              │
│                                                                 │
│   2️⃣ OTOMATIS SEDERHANA (Era Bapak)                            │
│   ═══════════════════════════════════════════════════════════   │
│   Termostat → Suhu > 30°C → Kipas ON                           │
│                                                                 │
│   Contoh: Aturan tetap, tidak fleksibel                        │
│   ⚠️ Tidak adaptif, tidak bisa belajar                         │
│                                                                 │
│   3️⃣ IoT MONITORING (Era Kita - Sebelumnya)                    │
│   ═══════════════════════════════════════════════════════════   │
│   Sensor → Data → Dashboard → Manusia ambil keputusan          │
│                                                                 │
│   Contoh: "HP bunyi: suhu 32°C" → Peternak buka app → ON kipas │
│   ⚠️ Masih butuh manusia untuk keputusan                       │
│                                                                 │
│   4️⃣ SMART POULTRY SYSTEM (Era Kita - Sekarang)                │
│   ═══════════════════════════════════════════════════════════   │
│   Sensor → AI → Keputusan otomatis → Aksi otomatis             │
│           ↓                                                     │
│      Belajar dari data historis                                 │
│                                                                 │
│   Contoh: AI tahu umur ayam, cuaca, dan pola → Nyalakan kipas  │
│           SEBELUM suhu naik!                                    │
│   ✅ Proaktif, adaptif, terus belajar                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 2: Arsitektur Smart Poultry System

### 🏗️ Komponen Utama

```
┌─────────────────────────────────────────────────────────────────┐
│              ARSITEKTUR SMART POULTRY SYSTEM                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ┌─────────────────────────────────────────────────────────┐   │
│   │                    LAYER 5: USER                         │   │
│   │  📱 Mobile App    💻 Web Dashboard    📊 Reports         │   │
│   └──────────────────────────┬──────────────────────────────┘   │
│                              │                                   │
│   ┌──────────────────────────▼──────────────────────────────┐   │
│   │                 LAYER 4: CLOUD / AI                      │   │
│   │  🧠 Machine Learning    📈 Analytics    🔔 Alerts        │   │
│   └──────────────────────────┬──────────────────────────────┘   │
│                              │                                   │
│   ┌──────────────────────────▼──────────────────────────────┐   │
│   │              LAYER 3: CONNECTIVITY                       │   │
│   │  📡 WiFi/4G    🌐 LoRa    📶 Zigbee    🔗 MQTT          │   │
│   └──────────────────────────┬──────────────────────────────┘   │
│                              │                                   │
│   ┌──────────────────────────▼──────────────────────────────┐   │
│   │               LAYER 2: GATEWAY/EDGE                      │   │
│   │  🖥️ Raspberry Pi / ESP32 dengan Edge AI                 │   │
│   └──────────────────────────┬──────────────────────────────┘   │
│                              │                                   │
│   ┌──────────────────────────▼──────────────────────────────┐   │
│   │           LAYER 1: SENSORS & ACTUATORS                   │   │
│   │  🌡️ Suhu    💧 Humidity    💨 Amonia    📷 Kamera        │   │
│   │  🌀 Kipas   💡 Lampu      🚿 Misting   🍽️ Feeder        │   │
│   └─────────────────────────────────────────────────────────┘   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📊 Penjelasan Tiap Layer

#### Layer 1: Sensors & Actuators (Di Kandang)

| Komponen              | Fungsi                | Contoh Produk        | Harga Estimasi            |
| --------------------- | --------------------- | -------------------- | ------------------------- |
| **Sensor Suhu**       | Ukur temperatur       | DHT22, DS18B20       | Rp 25.000 - 75.000        |
| **Sensor Kelembaban** | Ukur humidity         | DHT22, SHT31         | Rp 25.000 - 150.000       |
| **Sensor Amonia**     | Ukur gas NH3          | MQ-135, MQ-137       | Rp 50.000 - 200.000       |
| **Sensor CO2**        | Ukur karbon dioksida  | MH-Z19               | Rp 150.000 - 300.000      |
| **Load Cell**         | Ukur berat pakan/ayam | HX711 + Load Cell    | Rp 75.000 - 200.000       |
| **Kamera**            | Visual monitoring     | ESP32-CAM, IP Camera | Rp 100.000 - 500.000      |
| **Kipas Exhaust**     | Ventilasi             | Industrial Fan       | Rp 500.000 - 2.000.000    |
| **Cooling Pad**       | Pendinginan           | Evaporative Cooling  | Rp 2.000.000 - 5.000.000  |
| **Lampu**             | Pencahayaan           | LED Dimmable         | Rp 100.000 - 300.000      |
| **Feeder Otomatis**   | Pemberian pakan       | Auger System         | Rp 3.000.000 - 10.000.000 |

---

#### Layer 2: Gateway/Edge (Otak Lokal)

```
┌─────────────────────────────────────────────────────────────────┐
│              FUNGSI GATEWAY/EDGE                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📥 MENGUMPULKAN DATA                                          │
│   • Terima data dari semua sensor                               │
│   • Baca setiap 1-5 detik                                       │
│                                                                 │
│   🧮 PREPROCESSING                                              │
│   • Filter data yang error/noise                                │
│   • Hitung rata-rata per interval                               │
│                                                                 │
│   🧠 EDGE AI (Opsional)                                         │
│   • Keputusan cepat tanpa internet                             │
│   • Contoh: Suhu > 33°C → Langsung kipas ON                    │
│                                                                 │
│   📤 KIRIM KE CLOUD                                             │
│   • Data agregat per menit/5 menit                             │
│   • Hemat bandwidth                                             │
│                                                                 │
│   📩 TERIMA PERINTAH                                            │
│   • Dari cloud atau AI                                          │
│   • Eksekusi ke aktuator                                        │
│                                                                 │
│   💾 LOCAL STORAGE                                              │
│   • Simpan data jika internet mati                             │
│   • Sync saat online                                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Hardware yang Umum Digunakan:**

| Perangkat          | Kelebihan                        | Kekurangan                | Harga                  |
| ------------------ | -------------------------------- | ------------------------- | ---------------------- |
| **Raspberry Pi 4** | Powerful, Linux, fleksibel       | Butuh power supply stabil | Rp 800.000 - 1.200.000 |
| **ESP32**          | Murah, WiFi built-in, hemat daya | Kurang powerful           | Rp 50.000 - 150.000    |
| **Arduino Mega**   | Banyak I/O, mudah                | Tidak ada WiFi bawaan     | Rp 150.000 - 300.000   |
| **Industrial PLC** | Sangat reliabel                  | Mahal, perlu keahlian     | Rp 5.000.000+          |

---

#### Layer 3: Connectivity (Jembatan Data)

| Protokol   | Jarak     | Kecepatan | Kelebihan                 | Cocok Untuk             |
| ---------- | --------- | --------- | ------------------------- | ----------------------- |
| **WiFi**   | 50-100m   | Tinggi    | Mudah setup               | Kandang dengan internet |
| **4G/LTE** | Unlimited | Tinggi    | Jangkauan luas            | Kandang terpencil       |
| **LoRa**   | 2-15 km   | Rendah    | Hemat baterai, jarak jauh | Multi-kandang           |
| **Zigbee** | 100m      | Sedang    | Mesh network              | Banyak sensor           |

---

#### Layer 4: Cloud & AI (Otak Utama)

```
┌─────────────────────────────────────────────────────────────────┐
│              FUNGSI CLOUD & AI                                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   💾 DATA STORAGE                                               │
│   • Simpan semua data historis                                  │
│   • Bisa diakses kapan saja                                     │
│                                                                 │
│   🧠 MACHINE LEARNING                                           │
│   • Prediksi: berat panen, FCR, mortalitas                     │
│   • Deteksi: penyakit dini, anomali                            │
│   • Optimasi: pakan, suhu, ventilasi                           │
│                                                                 │
│   📊 ANALYTICS                                                  │
│   • Dashboard real-time                                         │
│   • Laporan performa per siklus                                │
│   • Benchmarking antar kandang                                  │
│                                                                 │
│   🔔 ALERTING                                                   │
│   • Push notification ke HP                                     │
│   • SMS untuk kondisi kritis                                    │
│   • Email laporan harian                                        │
│                                                                 │
│   🤖 AUTOMATION                                                 │
│   • Buat keputusan otomatis                                     │
│   • Kirim perintah ke aktuator                                  │
│   • Log semua aksi                                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

#### Layer 5: User Interface (Antarmuka Pengguna)

| Jenis             | Fungsi                  | Contoh Tampilan                         |
| ----------------- | ----------------------- | --------------------------------------- |
| **Mobile App**    | Monitoring di mana saja | Dashboard ringkas, notifikasi real-time |
| **Web Dashboard** | Analisis mendalam       | Grafik detail, laporan lengkap          |
| **Reports**       | Evaluasi performa       | PDF/Excel per siklus                    |

---

## 📖 BAGIAN 3: Alur Kerja Smart Poultry System

### 🔄 Skenario: Penanganan Suhu Tinggi

```
┌─────────────────────────────────────────────────────────────────┐
│              ALUR KERJA: PENANGANAN SUHU TINGGI                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ⏱️ 13:00 - SENSOR MEMBACA DATA                                │
│   ─────────────────────────────────────────────────────────────│
│   🌡️ Suhu: 31.5°C (naik dari 29°C)                             │
│   💧 Kelembaban: 72%                                            │
│   📅 Umur ayam: 28 hari                                         │
│   ☀️ Cuaca luar: 34°C (lebih panas dari biasa)                 │
│                                                                 │
│   ⏱️ 13:01 - GATEWAY MENGIRIM DATA KE CLOUD                    │
│   ─────────────────────────────────────────────────────────────│
│   📤 Data dikirim via WiFi ke server                           │
│                                                                 │
│   ⏱️ 13:02 - AI MENGANALISIS                                    │
│   ─────────────────────────────────────────────────────────────│
│   🧠 AI membaca:                                                │
│   • Suhu naik 2.5°C dalam 1 jam                                │
│   • Cuaca luar panas → kemungkinan akan terus naik            │
│   • Ayam umur 28 hari sensitif terhadap heat stress           │
│   • Data historis: suhu > 32°C → mortalitas naik 15%          │
│                                                                 │
│   ⏱️ 13:03 - AI MENGAMBIL KEPUTUSAN                             │
│   ─────────────────────────────────────────────────────────────│
│   📋 Keputusan:                                                 │
│   ✓ Nyalakan 2 kipas tambahan (dari 4 jadi 6)                 │
│   ✓ Aktifkan cooling pad                                       │
│   ✓ Kurangi intensitas lampu 20%                               │
│   ✓ Tunda pemberian pakan siang (pindah ke sore)              │
│                                                                 │
│   ⏱️ 13:03 - PERINTAH DIKIRIM KE GATEWAY                       │
│   ─────────────────────────────────────────────────────────────│
│   📩 Gateway menerima perintah via MQTT                        │
│                                                                 │
│   ⏱️ 13:04 - AKTUATOR BEKERJA                                   │
│   ─────────────────────────────────────────────────────────────│
│   🌀 Kipas 5 & 6: ON                                            │
│   🚿 Cooling pad: ON                                            │
│   💡 Lampu: Dimmed 20%                                          │
│   🍽️ Feeder: Pause scheduled                                   │
│                                                                 │
│   ⏱️ 13:05 - NOTIFIKASI KE PETERNAK                             │
│   ─────────────────────────────────────────────────────────────│
│   📱 "Suhu naik ke 31.5°C. Sistem sudah aktifkan cooling.      │
│       Tidak perlu tindakan. Akan dimonitor terus."             │
│                                                                 │
│   ⏱️ 14:00 - AI MENGEVALUASI HASIL                              │
│   ─────────────────────────────────────────────────────────────│
│   🌡️ Suhu turun ke 28.5°C ✅                                   │
│   💧 Kelembaban naik ke 78% (masih OK)                         │
│   📊 AI belajar: strategi ini efektif untuk kondisi serupa    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> 📚 **Catatan Akademis:**  
> Menurut penelitian Fournel et al. (2017), sistem kontrol iklim otomatis berbasis AI dapat mengurangi heat stress pada broiler hingga 30% dibandingkan sistem termostat konvensional.

---

### 🔄 Skenario: Deteksi Penyakit Dini

```
┌─────────────────────────────────────────────────────────────────┐
│              ALUR KERJA: DETEKSI PENYAKIT DINI                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ⏱️ 02:00 (Dini Hari) - KAMERA MEREKAM                        │
│   ─────────────────────────────────────────────────────────────│
│   📷 Video dianalisis oleh AI                                   │
│   🔍 Ditemukan: 8 ayam dengan gerakan abnormal di zona B       │
│                                                                 │
│   ⏱️ 02:01 - AI MENGANALISIS                                    │
│   ─────────────────────────────────────────────────────────────│
│   🧠 Karakteristik terdeteksi:                                  │
│   • Aktivitas menurun 40%                                       │
│   • 3 ayam dengan sayap turun                                   │
│   • 2 ayam dengan kepala menunduk                              │
│   • Konsumsi pakan zona B turun 12% (3 hari terakhir)          │
│   📊 AI probabilitas: 85% indikasi penyakit awal               │
│                                                                 │
│   ⏱️ 02:02 - AI MENGAMBIL KEPUTUSAN                             │
│   ─────────────────────────────────────────────────────────────│
│   📋 Level: MEDIUM ALERT (bukan kritis, tapi perlu perhatian) │
│   ✓ Tandai lokasi 8 ayam di peta kandang                       │
│   ✓ Tingkatkan frekuensi monitoring zona B                     │
│   ✓ Siapkan notifikasi untuk pagi hari                         │
│                                                                 │
│   ⏱️ 06:00 - NOTIFIKASI KE PETERNAK                             │
│   ─────────────────────────────────────────────────────────────│
│   📱 "🟡 PERLU PERHATIAN: 8 ayam di Zona B menunjukkan         │
│       gejala abnormal. Rekomendasi: isolasi & cek kesehatan.   │
│       [Lihat Video] [Lihat Lokasi] [Jadwalkan Dokter]"         │
│                                                                 │
│   ⏱️ 08:00 - PETERNAK BERTINDAK                                 │
│   ─────────────────────────────────────────────────────────────│
│   👨‍🌾 Pak Surya ke kandang, cek 8 ayam                          │
│   🔬 2 ayam dikonfirmasi sakit, langsung diisolasi            │
│   💊 Pengobatan dimulai                                         │
│   ✅ 6 ayam lainnya sehat, tetap diawasi                       │
│                                                                 │
│   💡 HASIL: Penyakit terdeteksi 3-4 hari lebih awal!           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 4: Studi Kasus Implementasi di Indonesia

### 🏭 Kasus 1: PT Unggas Sejahtera (Jawa Tengah)

**Profil:**

- Kapasitas: 100.000 ekor broiler
- 10 kandang closed house
- Implementasi Smart System sejak 2022

**Komponen yang Dipasang:**

| Komponen             | Jumlah per Kandang | Total   |
| -------------------- | ------------------ | ------- |
| Sensor suhu-humidity | 6 unit             | 60 unit |
| Sensor amonia        | 2 unit             | 20 unit |
| Kamera AI            | 4 unit             | 40 unit |
| Gateway              | 1 unit             | 10 unit |

**Investasi:**

- Hardware: Rp 450.000.000
- Software + Cloud (setahun): Rp 120.000.000
- **Total investasi awal: Rp 570.000.000**

**Hasil Setelah 1 Tahun:**

| Parameter          | Sebelum       | Sesudah       | Perubahan |
| ------------------ | ------------- | ------------- | --------- |
| Mortalitas         | 4.5%          | 2.8%          | ⬇️ 38%    |
| FCR                | 1.68          | 1.54          | ⬇️ 8.3%   |
| Berat panen        | 2.08 kg       | 2.22 kg       | ⬆️ 6.7%   |
| Waktu tenaga kerja | 40 jam/minggu | 15 jam/minggu | ⬇️ 62.5%  |

**Perhitungan ROI:**

```
┌─────────────────────────────────────────────────────────────────┐
│              PERHITUNGAN ROI PT UNGGAS SEJAHTERA               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📈 PENGHEMATAN DARI MORTALITAS TURUN:                        │
│   ─────────────────────────────────────────────────────────────│
│   Produksi: 100.000 ekor × 7 siklus = 700.000 ekor/tahun      │
│   Selisih mortalitas: 4.5% - 2.8% = 1.7%                       │
│   Ayam terselamatkan: 700.000 × 1.7% = 11.900 ekor            │
│   Nilai: 11.900 × Rp 35.000 = Rp 416.500.000/tahun            │
│                                                                 │
│   📈 PENGHEMATAN DARI FCR TURUN:                               │
│   ─────────────────────────────────────────────────────────────│
│   Pakan per ekor sebelum: 2.08 × 1.68 = 3.49 kg               │
│   Pakan per ekor sesudah: 2.22 × 1.54 = 3.42 kg               │
│   Selisih: 0.07 kg/ekor × 682.000 ekor = 47.740 kg pakan/tahun│
│   Nilai: 47.740 × Rp 8.500 = Rp 405.790.000/tahun             │
│                                                                 │
│   📈 PENDAPATAN TAMBAHAN (BERAT NAIK):                         │
│   ─────────────────────────────────────────────────────────────│
│   Selisih berat: 0.14 kg/ekor × 682.000 ekor = 95.480 kg      │
│   Nilai: 95.480 × Rp 18.000 = Rp 1.718.640.000/tahun          │
│                                                                 │
│   💰 TOTAL BENEFIT: Rp 2.540.930.000/tahun                     │
│   💻 TOTAL INVESTASI: Rp 570.000.000                           │
│                                                                 │
│   📊 ROI: (2.540 - 570) / 570 × 100% = 346%                   │
│   ⏱️ PAYBACK PERIOD: 570 / 2.540 × 12 = 2.7 bulan!            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 🏠 Kasus 2: Peternakan Rakyat Pak Haji (Jawa Barat)

**Profil:**

- Kapasitas: 5.000 ekor broiler
- 1 kandang semi-closed
- Budget terbatas

**Solusi Low-Cost Smart System:**

| Komponen             | Pilihan   | Harga            |
| -------------------- | --------- | ---------------- |
| Mikrokontroler       | ESP32     | Rp 75.000        |
| Sensor DHT22         | 2 unit    | Rp 50.000        |
| Sensor MQ-135        | 1 unit    | Rp 75.000        |
| Relay 4 channel      | 1 unit    | Rp 50.000        |
| Power supply         | 1 unit    | Rp 50.000        |
| Kabel & housing      | -         | Rp 100.000       |
| **Platform Chickin** | Langganan | Rp 500.000/bulan |

**Total Investasi Awal: Rp 400.000 + Rp 500.000/bulan**

**Hasil Setelah 6 Bulan:**

| Parameter           | Sebelum  | Sesudah    | Perubahan |
| ------------------- | -------- | ---------- | --------- |
| Mortalitas          | 6%       | 4%         | ⬇️ 33%    |
| FCR                 | 1.75     | 1.65       | ⬇️ 5.7%   |
| Frekuensi cek malam | 3x/malam | 0x (alarm) | ⬇️ 100%   |

> 💡 **Pak Haji:** "Modal cuma Rp 400.000, tapi tidur saya tenang. Kalau ada masalah, HP bunyi!"

---

## 📖 BAGIAN 5: Platform Smart Poultry di Indonesia

### 🇮🇩 Solusi Lokal

| Platform    | Fitur Utama                               | Target User          | Harga                 |
| ----------- | ----------------------------------------- | -------------------- | --------------------- |
| **Chickin** | Monitoring, AI prediksi, ERP terintegrasi | Skala menengah-besar | Rp 500rb - 5jt/bulan  |
| **PITIK**   | Farm management, marketplace              | Skala kecil-menengah | Gratis - Rp 1jt/bulan |
| **Growpal** | Monitoring + investasi                    | Investor + peternak  | Bagi hasil            |
| **eFarm**   | Multi-commodity (ayam, ikan, sapi)        | Semua skala          | Rp 200rb - 2jt/bulan  |

### 🌍 Solusi Global yang Bisa Digunakan

| Platform         | Asal    | Keunggulan                                  |
| ---------------- | ------- | ------------------------------------------- |
| **Faromatics**   | Spanyol | Robot ChickenBoy yang keliling kandang      |
| **Fancom**       | Belanda | Sistem climate control industry-standard    |
| **Big Dutchman** | Jerman  | Solusi lengkap dari kandang sampai software |

---

## 📖 BAGIAN 6: Tantangan dan Solusi Implementasi

### ⚠️ Tantangan Umum

| Tantangan                 | Dampak                     | Solusi                                          |
| ------------------------- | -------------------------- | ----------------------------------------------- |
| **Investasi awal tinggi** | Peternak kecil tidak mampu | Mulai dari komponen esensial, scale up bertahap |
| **Internet tidak stabil** | Data tidak terkirim        | Gunakan Edge AI + penyimpanan lokal             |
| **Listrik sering mati**   | Aktuator tidak berfungsi   | UPS + generator backup                          |
| **SDM kurang terampil**   | Sistem tidak optimal       | Training intensif, UI yang mudah                |
| **Resistensi perubahan**  | Tidak mau pakai teknologi  | Tunjukkan ROI dari pilot project                |

### 💡 Tips Implementasi Bertahap

```
┌─────────────────────────────────────────────────────────────────┐
│              ROADMAP IMPLEMENTASI                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   FASE 1: MONITORING DASAR (Bulan 1-3)                         │
│   ═══════════════════════════════════════════════════════════   │
│   ✓ 2 sensor suhu-humidity per kandang                         │
│   ✓ 1 gateway (ESP32/Raspberry Pi)                             │
│   ✓ Dashboard sederhana (Blynk/ThingsBoard)                    │
│   💰 Budget: Rp 200.000 - 500.000                              │
│                                                                 │
│   FASE 2: OTOMASI DASAR (Bulan 4-6)                            │
│   ═══════════════════════════════════════════════════════════   │
│   ✓ Tambah relay untuk kontrol kipas                           │
│   ✓ Aturan otomatis sederhana (if-then)                        │
│   ✓ Alert ke HP jika kondisi abnormal                         │
│   💰 Budget tambahan: Rp 100.000 - 300.000                     │
│                                                                 │
│   FASE 3: SENSOR LENGKAP (Bulan 7-9)                           │
│   ═══════════════════════════════════════════════════════════   │
│   ✓ Tambah sensor amonia, CO2                                  │
│   ✓ Load cell untuk timbang pakan                              │
│   ✓ Data lebih komprehensif                                    │
│   💰 Budget tambahan: Rp 300.000 - 700.000                     │
│                                                                 │
│   FASE 4: AI & ANALYTICS (Bulan 10-12)                         │
│   ═══════════════════════════════════════════════════════════   │
│   ✓ Pilih platform dengan fitur AI (Chickin, dll)             │
│   ✓ Prediksi performa                                          │
│   ✓ Optimasi otomatis                                          │
│   💰 Budget tambahan: Rp 500.000 - 2.000.000/bulan             │
│                                                                 │
│   💡 TOTAL 1 TAHUN: Rp 1.000.000 - 5.000.000                   │
│      (Bisa disesuaikan dengan kemampuan finansial)             │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📊 Ringkasan Pertemuan 12

| Topik                  | Poin Penting                                              |
| ---------------------- | --------------------------------------------------------- |
| **Definisi**           | Integrasi sensor, AI, aktuator untuk pengelolaan otomatis |
| **5 Layer**            | Sensor → Gateway → Connectivity → Cloud/AI → User         |
| **Kunci Sukses**       | Proaktif (bertindak SEBELUM masalah), belajar dari data   |
| **ROI**                | Payback period bisa 2-3 bulan untuk skala besar           |
| **Low-Cost Option**    | Budget Rp 400.000 sudah bisa mulai monitoring             |
| **Platform Indonesia** | Chickin, PITIK, eFarm                                     |
| **Implementasi**       | Bertahap, mulai dari monitoring → otomasi → AI            |

---

## ❓ Pertanyaan Diskusi

1. **Dari evolusi Pak Surya (20 tahun beternak), fase mana yang menurut Anda paling transformatif? Mengapa?**

2. **Jika Anda adalah peternak dengan budget Rp 1 juta, komponen mana yang akan Anda prioritaskan untuk Smart Poultry System Anda?**

3. **Menurut Anda, mengapa masih banyak peternak Indonesia yang belum mengadopsi Smart Poultry System?**

4. **Bandingkan ROI PT Unggas Sejahtera (skala besar) dengan Pak Haji (skala kecil). Mana yang lebih menarik? Mengapa?**

---

## 📚 Istilah Penting Pertemuan Ini

| Istilah                  | Arti Sederhana                                              |
| ------------------------ | ----------------------------------------------------------- |
| **Smart Poultry System** | Sistem peternakan unggas yang terintegrasi dan cerdas       |
| **Gateway**              | Perangkat penghubung sensor dengan cloud                    |
| **Edge AI**              | AI yang berjalan di perangkat lokal (tanpa internet)        |
| **Layer**                | Lapisan dalam arsitektur sistem                             |
| **Actuator**             | Perangkat yang melakukan aksi (kipas, lampu, dll)           |
| **MQTT**                 | Protokol komunikasi ringan untuk IoT                        |
| **Closed House**         | Kandang tertutup dengan kontrol lingkungan penuh            |
| **Payback Period**       | Waktu yang dibutuhkan untuk investasi kembali modal         |
| **ROI**                  | Return on Investment - persentase keuntungan dari investasi |
| **Scale Up**             | Memperbesar skala implementasi secara bertahap              |

---

## 🎯 Tugas Pertemuan 12

### Tugas Kelompok (Lanjutan dari Pertemuan 11)

**Progress Check:**

- Kelompok melaporkan progress desain sistem deteksi penyakit
- Konsultasi jika ada kendala
- Presentasi final di Pertemuan 13

### Tugas Individu

**Mini Case Study:**

1. Pilih salah satu platform Smart Poultry (Chickin, PITIK, atau eFarm)
2. Riset fitur-fitur yang ditawarkan
3. Buat ringkasan 1 halaman meliputi:
   - Fitur utama
   - Target pengguna
   - Kelebihan dan kekurangan
   - Harga (jika tersedia)
4. Kumpulkan minggu depan

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna untuk mempelajari lebih dalam tentang Smart Poultry System.

### Sumber Akademik

| No  | Referensi                                                                                                                                                          | Keterangan           |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------- |
| 1   | Fournel, S., et al. (2017). Rethinking environment control strategy of confined animal housing systems. _Biosystems Engineering_, 155, 96-123.                     | Kontrol iklim AI     |
| 2   | Berckmans, D. (2017). General introduction to precision livestock farming. _Animal Frontiers_, 7(1), 6-11.                                                         | Konsep PLF           |
| 3   | Neethirajan, S., et al. (2021). Digital phenotyping in livestock. _Animals_, 11(7), 2009.                                                                          | Fenotipe digital     |
| 4   | Astill, J., et al. (2020). Smart poultry management: Smart sensors, big data, and the internet of things. _Computers and Electronics in Agriculture_, 170, 105291. | Review Smart Poultry |

### Platform Indonesia

| No  | Referensi                        | Keterangan                    |
| --- | -------------------------------- | ----------------------------- |
| 5   | Chickin Indonesia. _chickin.id_  | Platform smart farming unggas |
| 6   | PITIK. _pitik.id_                | Farm management system        |
| 7   | eFishery (eFarm). _efishery.com_ | Platform multi-commodity      |

### Hardware & Tools

| No  | Referensi                            | Keterangan               |
| --- | ------------------------------------ | ------------------------ |
| 8   | ESP32 Documentation. _espressif.com_ | Mikrokontroler IoT       |
| 9   | Raspberry Pi. _raspberrypi.org_      | Single-board computer    |
| 10  | ThingsBoard. _thingsboard.io_        | IoT platform open-source |

---

## 🔗 Koneksi dengan Materi Sebelumnya

```
┌─────────────────────────────────────────────────────────────────┐
│           PERTEMUAN 12 = INTEGRASI SEMUA MATERI!               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   Pertemuan 1: Pengantar IoT         → Konsep dasar            │
│   Pertemuan 2: Perangkat IoT         → Hardware                │
│   Pertemuan 3: Sensor Lingkungan     → Layer 1 (Input)         │
│   Pertemuan 4: Aktuator              → Layer 1 (Output)        │
│   Pertemuan 5: Sistem Komunikasi     → Layer 3                 │
│   Pertemuan 6: Monitoring Kandang    → Layer 4 & 5             │
│   Pertemuan 7: Studi Kasus           → Implementasi nyata      │
│   Pertemuan 9: AI Peternakan         → Layer 4 (AI)            │
│   Pertemuan 10: Machine Learning     → Layer 4 (ML)            │
│   Pertemuan 11: Deteksi & Optimasi   → Aplikasi AI             │
│                                                                 │
│   👉 Pertemuan 12: SMART POULTRY SYSTEM (SEKARANG)             │
│   ═══════════════════════════════════════════════════════════   │
│   MENGGABUNGKAN SEMUA MENJADI SATU SISTEM TERINTEGRASI!        │
│                                                                 │
│   Pertemuan 13: Smart Circular Farming                          │
│   └── Extended concept: sustainability + smart farming         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar tentang **Integrasi Smart Circular Farming** - bagaimana menggabungkan konsep smart farming dengan ekonomi sirkular untuk keberlanjutan!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_  
_Semester Genap 2025/2026_
