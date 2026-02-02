# 🌾 Pertemuan 1: Pengantar Internet of Things (IoT) dan Penerapannya di Peternakan

> **"Bagaimana jika ternak Anda bisa 'berbicara' kepada Anda... bahkan saat Anda sedang tidur?"**

---

## 👨‍🏫 Dosen Pengampu

- **Julinda** / **Anhar** (Kelas A / Kelas B)

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Memahami konsep dasar Internet of Things (IoT)
2. Menjelaskan mengapa IoT penting untuk masa depan peternakan
3. Mengidentifikasi contoh-contoh penerapan IoT di bidang peternakan
4. Menyadari peluang dan tantangan IoT untuk peternak Indonesia

---

## 📖 Perkenalan: Mengapa Kita Belajar IoT?

### 🤔 Cerita Pembuka

Bayangkan dua orang peternak ayam:

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   👨‍🌾 PAK BUDI (Peternak Tradisional)                          │
│                                                                 │
│   • Bangun jam 4 pagi untuk cek kandang                        │
│   • Jalan kaki ke kandang yang 2 km dari rumah                 │
│   • Meraba-raba suhu dengan tangan: "Kayaknya panas nih..."    │
│   • Catat data di buku tulis (kadang lupa)                     │
│   • Suatu malam, kipas mati → tidak tahu → 200 ayam stres      │
│   • Tidak bisa pergi liburan karena harus jaga kandang         │
│                                                                 │
│   ⏱️ Waktu untuk monitoring: 3-4 jam/hari                       │
│   😰 Tingkat stres: TINGGI                                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   👩‍💼 BU ANI (Peternak dengan IoT)                              │
│                                                                 │
│   • Bangun pagi, cek HP: "Kandang 28°C, semua normal ✓"        │
│   • Jam 2 malam kipas mati → HP bunyi → langsung tahu          │
│   • Data tercatat otomatis, bisa lihat grafik mingguan         │
│   • Sedang di acara keluarga, tetap bisa pantau kandang        │
│   • Bisa prediksi: "Minggu depan harus panen, berat sudah 2kg" │
│   • Waktu luang untuk mengembangkan bisnis lain                │
│                                                                 │
│   ⏱️ Waktu untuk monitoring: 30 menit/hari                      │
│   😌 Tingkat stres: RENDAH                                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Pertanyaan:** Anda ingin menjadi peternak seperti siapa?

---

## 🌐 Apa itu Internet of Things (IoT)?

### Definisi Sederhana

**IoT** = **I**nternet **o**f **T**hings = **Internet untuk Benda-Benda**

```
┌─────────────────────────────────────────────────────────────────┐
│                    APA ITU IoT?                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🔹 "Internet" = Jaringan yang menghubungkan semuanya         │
│                   (seperti yang Anda pakai untuk WhatsApp)      │
│                                                                 │
│   🔹 "Things" = Benda-benda fisik                               │
│                 (sensor, lampu, kipas, timbangan, kamera, dll)  │
│                                                                 │
│   🔹 IoT = Benda-benda yang bisa "berbicara" via internet      │
│                                                                 │
│   ════════════════════════════════════════════════════════════  │
│                                                                 │
│   🌡️ Termometer                 📱 HP Anda                      │
│      di kandang     ────→          berbunyi:                    │
│      "Suhu 35°C!"                  "⚠️ Kandang panas!"          │
│                                                                 │
│   Itulah IoT dalam aksi!                                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Definisi Resmi (untuk Pengetahuan)

> 💡 **Tahukah Anda?** Istilah "Internet of Things" pertama kali dicetuskan oleh **Kevin Ashton** pada tahun 1999 saat ia bekerja di Procter & Gamble untuk menjelaskan sistem di mana benda-benda fisik dapat terhubung ke internet melalui sensor (Ashton, 2009).

Menurut **ITU (International Telecommunication Union)**, badan telekomunikasi PBB, IoT didefinisikan sebagai:

> _"Infrastruktur global untuk masyarakat informasi, yang memungkinkan layanan canggih dengan menghubungkan benda-benda (baik fisik maupun virtual) berdasarkan teknologi informasi dan komunikasi yang ada dan berkembang."_  
> — ITU-T Y.2060 (2012)

**🎓 Catatan untuk Mahasiswa:**  
Definisi di atas terdengar rumit, kan? Tenang, intinya sama saja dengan penjelasan sederhana kita: **benda-benda yang bisa terhubung dan berkomunikasi via internet!** Definisi resmi ini berguna jika Anda menulis skripsi atau jurnal.

### Analogi yang Mudah Dipahami

> **IoT seperti memberikan "Panca Indera" dan "Mulut" kepada kandang Anda!**

```
┌─────────────────────────────────────────────────────────────────┐
│              KANDANG BIASA vs KANDANG PINTAR (IoT)              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   KANDANG BIASA (Bisu)              KANDANG PINTAR (Bisa Bicara)│
│                                                                 │
│   🏠 Kandang tidak bisa            🏠💬 Kandang bisa bilang:    │
│      memberitahu apa-apa               "Pak, saya panas!"       │
│                                        "Pak, air habis!"        │
│                                        "Pak, ada yang aneh!"    │
│                                                                 │
│   😴 Anda tidur, kandang            😴📱 Anda tidur, HP bunyi   │
│      bermasalah → tidak tahu           jika ada masalah         │
│                                                                 │
│   📝 Catat manual di buku           📊 Data tercatat otomatis   │
│      (sering lupa/hilang)              (tersimpan aman di cloud)│
│                                                                 │
│   🚶 Harus ke kandang untuk         📱 Cukup buka HP untuk      │
│      tahu kondisi                      melihat kondisi          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📜 Sejarah Singkat IoT

### Dari Mana IoT Berasal?

```
┌─────────────────────────────────────────────────────────────────┐
│                   PERJALANAN IoT                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1999 │ Kevin Ashton menciptakan istilah "Internet of Things" │
│        │ saat bekerja di Procter & Gamble                       │
│        │                                                        │
│   2008 │ Jumlah "benda" yang terhubung internet                │
│        │ MELEBIHI jumlah manusia di bumi!                       │
│        │                                                        │
│   2010 │ Mulai muncul smart home (rumah pintar)                │
│        │                                                        │
│   2015 │ IoT mulai masuk ke pertanian & peternakan             │
│        │ → "Smart Farming" lahir!                               │
│        │                                                        │
│   2020 │ Pandemi mempercepat adopsi IoT                        │
│        │ (monitoring jarak jauh makin penting)                  │
│        │                                                        │
│   2024 │ Sudah ada 15+ MILIAR perangkat IoT di dunia!          │
│        │ (Sumber: Statista, 2024)                               │
│        │                                                        │
│   2030 │ Diprediksi akan ada 30+ MILIAR perangkat IoT          │
│        │ (Sumber prediksi: IoT Analytics, 2023)                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### IoT di Kehidupan Sehari-hari (yang Mungkin Tidak Anda Sadari!)

```
┌─────────────────────────────────────────────────────────────────┐
│           IoT SUDAH ADA DI SEKITAR KITA!                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📱 Smartphone Anda                                            │
│      • GPS melacak lokasi                                       │
│      • Sinkronisasi data ke cloud                               │
│                                                                 │
│   🚗 Grab/Gojek                                                 │
│      • Mengetahui lokasi driver real-time                       │
│      • Estimasi waktu kedatangan                                │
│                                                                 │
│   🏧 ATM/m-Banking                                              │
│      • Transaksi dari mana saja                                 │
│      • Notifikasi langsung ke HP                                │
│                                                                 │
│   📺 Smart TV                                                   │
│      • Streaming Netflix, YouTube                               │
│      • Update software otomatis                                 │
│                                                                 │
│   ⌚ Smartwatch                                                 │
│      • Monitor detak jantung                                    │
│      • Hitung langkah kaki                                      │
│                                                                 │
│   🔒 CCTV / Smart Lock                                          │
│      • Pantau rumah dari jauh                                   │
│      • Buka pintu dari HP                                       │
│                                                                 │
│   💡 Anda sudah menggunakan IoT setiap hari!                    │
│      Sekarang saatnya membawanya ke kandang ternak Anda.        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🐄 IoT untuk Peternakan: Mengapa Penting?

### Tantangan Peternak Modern

```
┌─────────────────────────────────────────────────────────────────┐
│              TANTANGAN PETERNAK SAAT INI                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   😓 WAKTU & TENAGA                                             │
│      • Monitoring manual memakan banyak waktu                   │
│      • Sulit jika punya banyak kandang tersebar                 │
│      • Tidak bisa tinggalkan kandang terlalu lama               │
│                                                                 │
│   📉 KERUGIAN AKIBAT KETERLAMBATAN                              │
│      • Penyakit tidak terdeteksi dini                           │
│      • Suhu/kelembaban tidak terkontrol                         │
│      • Kematian ternak yang bisa dicegah                        │
│                                                                 │
│   📝 PENCATATAN TIDAK KONSISTEN                                 │
│      • Data manual sering tidak lengkap                         │
│      • Sulit menganalisis tren jangka panjang                   │
│      • Tidak ada data untuk pengambilan keputusan               │
│                                                                 │
│   💰 EFISIENSI RENDAH                                           │
│      • Pakan berlebih atau kurang                               │
│      • Listrik boros (kipas/lampu menyala terus)                │
│      • Tidak tahu waktu optimal untuk panen/jual                │
│                                                                 │
│   🌍 PERSAINGAN GLOBAL                                          │
│      • Pasar menuntut kualitas lebih tinggi                     │
│      • Konsumen ingin tahu asal-usul produk                     │
│      • Sertifikasi memerlukan data dan dokumentasi              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Bagaimana IoT Menjawab Tantangan Ini?

```
┌─────────────────────────────────────────────────────────────────┐
│                 SOLUSI IoT                                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   TANTANGAN              →       SOLUSI IoT                     │
│   ─────────────────────────────────────────────────────────────│
│                                                                 │
│   ⏰ Monitoring manual   →   📱 Pantau dari HP 24/7             │
│      memakan waktu            kapan saja, di mana saja          │
│                                                                 │
│   😴 Tidak tahu masalah  →   🔔 Notifikasi otomatis             │
│      saat malam hari          langsung ke HP Anda               │
│                                                                 │
│   📝 Pencatatan manual   →   💾 Data tercatat otomatis          │
│      tidak konsisten          akurat, lengkap, tersimpan aman   │
│                                                                 │
│   🌡️ Suhu tidak stabil  →   🤖 Kontrol otomatis                │
│                               kipas/heater menyesuaikan         │
│                                                                 │
│   📊 Sulit menganalisis  →   📈 Dashboard & grafik              │
│                               analisis mudah dipahami           │
│                                                                 │
│   💸 Biaya membengkak    →   ⚡ Efisiensi energi & pakan        │
│                               hanya aktif saat diperlukan       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🇮🇩 Studi Kasus Nyata: IoT Peternakan di Indonesia

> **"Ini bukan fiksi! Sudah ada peternak Indonesia yang sukses dengan IoT!"**

### Startup & Perusahaan IoT Peternakan Indonesia

```
┌─────────────────────────────────────────────────────────────────┐
│          PEMAIN IoT PETERNAKAN DI INDONESIA                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🐔 CHICKIN (www.chickin.id)                                   │
│   ─────────────────────────────────────────────────────────────│
│   • Fokus: Peternakan ayam broiler                             │
│   • Layanan: Sensor + aplikasi monitoring kandang              │
│   • Fitur:                                                     │
│     - Monitoring suhu & kelembaban real-time                   │
│     - Notifikasi WhatsApp jika ada masalah                     │
│     - Rekap data harian otomatis                               │
│   • Klaim: Menurunkan mortalitas hingga 2%                     │
│   • Target: Peternak kemitraan & mandiri                       │
│                                                                 │
│   🐣 PITIK (www.pitik.id)                                       │
│   ─────────────────────────────────────────────────────────────│
│   • Fokus: Peternakan ayam dengan pendekatan data              │
│   • Model: Kemitraan dengan teknologi terintegrasi             │
│   • Fitur:                                                     │
│     - IoT device di setiap kandang mitra                       │
│     - Dashboard monitoring untuk peternak                      │
│     - Analisis performa dengan AI                              │
│   • Sudah bermitra dengan ribuan peternak                      │
│                                                                 │
│   🐟 eFISHERY (www.efishery.com)                                │
│   ─────────────────────────────────────────────────────────────│
│   • Fokus: Budidaya ikan & udang                               │
│   • Produk unggulan: Smart Feeder (pemberi pakan otomatis)     │
│   • Fitur:                                                     │
│     - Jadwal pakan otomatis via aplikasi                       │
│     - Monitoring konsumsi pakan                                │
│     - Prediksi waktu panen                                     │
│   • Status: Unicorn (valuasi > $1 miliar!)                     │
│   • Sudah dipakai 70.000+ kolam di Indonesia                   │
│                                                                 │
│   🐄 CERDAS (Cattle E-Recording Dashboard System)              │
│   ─────────────────────────────────────────────────────────────│
│   • Fokus: Pencatatan dan monitoring sapi                      │
│   • Dikembangkan oleh: Kementerian Pertanian                   │
│   • Fitur:                                                     │
│     - Recording data sapi digital                              │
│     - Tracking kesehatan & reproduksi                          │
│     - Integrasi dengan SINAS (Sertifikasi Nasional)            │
│                                                                 │
│   💡 PESAN: Startup Indonesia sudah membuktikan IoT BISA       │
│      diterapkan di peternakan kita!                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Kisah Sukses Peternak dengan IoT

```
┌─────────────────────────────────────────────────────────────────┐
│              TESTIMONI PETERNAK                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   👨‍🌾 Pak Hendra - Peternak Ayam, Jawa Timur                   │
│   ─────────────────────────────────────────────────────────────│
│   "Dulu saya harus bolak-balik kandang 5x sehari. Sekarang     │
│   cukup cek HP. Waktu luang saya pakai untuk buka kandang      │
│   kedua. Pendapatan naik 40%!"                                 │
│                                                                 │
│   Sebelum IoT:                                                  │
│   • Mortalitas: 5-6%                                           │
│   • Waktu monitoring: 4 jam/hari                               │
│   • Kelola 1 kandang                                           │
│                                                                 │
│   Sesudah IoT:                                                  │
│   • Mortalitas: 2-3%                                           │
│   • Waktu monitoring: 30 menit/hari                            │
│   • Kelola 3 kandang                                           │
│                                                                 │
│   ─────────────────────────────────────────────────────────────│
│                                                                 │
│   👩‍🌾 Bu Siti - Pembudidaya Lele, Jawa Barat                   │
│   ─────────────────────────────────────────────────────────────│
│   "Dulu pernah rugi besar karena aerator mati malam-malam.     │
│   Semua ikan mati. Sekarang pakai eFishery, kalau ada          │
│   masalah langsung ada notif ke HP."                           │
│                                                                 │
│   Kerugian dicegah: ± Rp 15 juta per kejadian                  │
│   Investasi IoT: Rp 3 juta                                     │
│   ROI: Sangat worth it! ✓                                       │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🔧 Bagaimana Sistem IoT Bekerja? (Preview)

> **Ini adalah gambaran umum yang akan kita pelajari detail di Pertemuan 2!**

### Arsitektur IoT Sederhana

```
┌─────────────────────────────────────────────────────────────────┐
│              CARA KERJA SISTEM IoT                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                        ☁️ CLOUD                                 │
│                    (Server di Internet)                         │
│                          │                                      │
│                          │ Data disimpan                        │
│                          │ & diproses                           │
│                          ▼                                      │
│   ┌──────────┐      ┌──────────┐      ┌──────────┐             │
│   │ 📱       │      │ 🌐       │      │ 🏠       │             │
│   │ APLIKASI │◄────►│ GATEWAY  │◄────►│ DEVICE   │             │
│   │ (HP/Web) │      │(Penghub.)│      │(Sensor)  │             │
│   └──────────┘      └──────────┘      └──────────┘             │
│       │                  │                  │                   │
│       │                  │                  │                   │
│       ▼                  ▼                  ▼                   │
│   Anda melihat       Mengirim data      Mengukur kondisi       │
│   data & mengon-     ke internet        kandang (suhu,         │
│   trol dari jauh                        kelembaban, dll)       │
│                                                                 │
│   ════════════════════════════════════════════════════════════  │
│                                                                 │
│   ALUR SEDERHANA:                                               │
│                                                                 │
│   🌡️ Sensor → 📡 Gateway → ☁️ Cloud → 📱 HP Anda               │
│   membaca     mengirim     menyimpan    menampilkan             │
│   suhu 35°C   ke internet  & proses     "Suhu Tinggi!"         │
│                                                                 │
│   Seperti WhatsApp, tapi untuk kandang Anda!                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Contoh Tampilan Dashboard (Ilustrasi)

```
┌─────────────────────────────────────────────────────────────────┐
│   📱 SMART FARM MONITORING              🔋 87%   📶   21:30    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🏠 KANDANG A - Ayam Broiler                      ✅ NORMAL   │
│   ┌─────────────────────────────────────────────────────────┐   │
│   │                                                         │   │
│   │   🌡️ Suhu          💧 Kelembaban      💨 Amonia        │   │
│   │   ┌─────────┐      ┌─────────┐       ┌─────────┐       │   │
│   │   │  28°C   │      │   65%   │       │  15 ppm │       │   │
│   │   │   ✓     │      │   ✓     │       │   ✓     │       │   │
│   │   └─────────┘      └─────────┘       └─────────┘       │   │
│   │                                                         │   │
│   │   ⚖️ Berat Rata-rata     🍽️ Pakan Tersisa              │   │
│   │   ┌─────────────┐        ┌─────────────┐               │   │
│   │   │   1.8 kg    │        │   75 kg     │               │   │
│   │   │  Target: 2kg│        │   🟢 Cukup  │               │   │
│   │   └─────────────┘        └─────────────┘               │   │
│   │                                                         │   │
│   │   📊 Grafik Suhu 24 Jam Terakhir                       │   │
│   │   32°│          ╭─╮                                    │   │
│   │   30°│    ╭────╯  ╰────╮                              │   │
│   │   28°│───╯              ╰─────────                    │   │
│   │   26°│                                                 │   │
│   │      └────────────────────────────────                │   │
│   │       00  04  08  12  16  20  24 (jam)                 │   │
│   │                                                         │   │
│   └─────────────────────────────────────────────────────────┘   │
│                                                                 │
│   ⚙️ Kontrol Cepat                                             │
│   ┌────────────┐  ┌────────────┐  ┌────────────┐               │
│   │ 💨 Kipas   │  │ 💡 Lampu   │  │ 💦 Sprayer │               │
│   │    [ON]    │  │   [AUTO]   │  │   [OFF]    │               │
│   └────────────┘  └────────────┘  └────────────┘               │
│                                                                 │
│   🔔 Notifikasi Terakhir:                                      │
│   • 14:30 - Suhu naik ke 32°C, kipas dinyalakan otomatis       │
│   • 08:00 - Pakan ditambahkan 50 kg                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> 💡 **Catatan:** Ini hanya ilustrasi. Tampilan asli bervariasi tergantung aplikasi yang digunakan. Yang penting: Anda bisa melihat semua informasi kandang dari HP!

---

## 💰 Berapa Biaya Sistem IoT?

> **"Apakah mahal? Tergantung kebutuhan!"**

### Perkiraan Harga Komponen IoT di Indonesia (2024)

```
┌─────────────────────────────────────────────────────────────────┐
│              ESTIMASI BIAYA SISTEM IoT                          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   💚 PAKET PEMULA (DIY - Do It Yourself)                       │
│   ─────────────────────────────────────────────────────────────│
│   Cocok untuk: Belajar & eksperimen                            │
│                                                                 │
│   │ Komponen                    │ Harga Perkiraan │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ ESP32 (mikrokontroler)      │ Rp 50.000-80.000│            │
│   │ Sensor Suhu DHT22           │ Rp 25.000-40.000│            │
│   │ Sensor Kelembaban           │ sudah include   │            │
│   │ Kabel & breadboard          │ Rp 30.000       │            │
│   │ Power supply/adaptor        │ Rp 25.000       │            │
│   │ Casing (opsional)           │ Rp 20.000       │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ TOTAL                       │ Rp 150.000-200.000           │
│   └─────────────────────────────┴─────────────────┘            │
│                                                                 │
│   💛 PAKET MENENGAH (Semi-Lengkap)                             │
│   ─────────────────────────────────────────────────────────────│
│   Cocok untuk: 1 kandang kecil-menengah                        │
│                                                                 │
│   │ Komponen                    │ Harga Perkiraan │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ IoT Gateway (siap pakai)    │ Rp 300.000-500.000           │
│   │ 2-3 Sensor (suhu, humidity) │ Rp 150.000-250.000           │
│   │ Relay untuk kontrol kipas   │ Rp 50.000-100.000            │
│   │ Instalasi & kabel           │ Rp 100.000      │            │
│   │ Langganan cloud (1 tahun)   │ Rp 0-500.000    │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ TOTAL                       │ Rp 600.000-1.500.000         │
│   └─────────────────────────────┴─────────────────┘            │
│                                                                 │
│   🧡 PAKET PROFESIONAL (Layanan Startup)                       │
│   ─────────────────────────────────────────────────────────────│
│   Cocok untuk: Peternak serius, skala menengah-besar           │
│                                                                 │
│   │ Layanan                     │ Harga Perkiraan │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ Perangkat lengkap           │ Rp 2-5 juta     │            │
│   │ Instalasi profesional       │ Include         │            │
│   │ Training penggunaan         │ Include         │            │
│   │ Langganan bulanan           │ Rp 50.000-200.000/bulan      │
│   │ Support & maintenance       │ Include         │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ TOTAL AWAL                  │ Rp 2-5 juta     │            │
│   │ BULANAN                     │ Rp 50.000-200.000            │
│   └─────────────────────────────┴─────────────────┘            │
│                                                                 │
│   🔴 PAKET ENTERPRISE (Sistem Lengkap)                         │
│   ─────────────────────────────────────────────────────────────│
│   Cocok untuk: Farm besar, kemitraan, perusahaan              │
│                                                                 │
│   │ Layanan                     │ Harga Perkiraan │            │
│   ├─────────────────────────────┼─────────────────┤            │
│   │ Full system integrasi       │ Rp 10-50 juta  │            │
│   │ Multiple kandang            │ tergantung skala│            │
│   │ Custom dashboard            │ Include         │            │
│   │ AI analytics                │ Include         │            │
│   └─────────────────────────────┴─────────────────┘            │
│                                                                 │
│   💡 TIPS HEMAT:                                                │
│   • Mulai dari yang sederhana (sensor suhu saja dulu)          │
│   • Manfaatkan program hibah/bantuan teknologi                 │
│   • Kerjasama dengan kampus untuk riset                        │
│   • Ikut program kemitraan startup (Chickin, Pitik)            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### Perbandingan: Biaya IoT vs Potensi Kerugian

```
┌─────────────────────────────────────────────────────────────────┐
│              APAKAH WORTH IT?                                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📊 Perhitungan untuk Kandang 5.000 Ayam Broiler:             │
│                                                                 │
│   TANPA IoT (Potensi Kerugian/Tahun):                          │
│   ┌───────────────────────────────────────────────────────┐    │
│   │ • Mortalitas lebih tinggi 2%                          │    │
│   │   = 100 ekor × 6 siklus × Rp 25.000 = Rp 15.000.000  │    │
│   │ • FCR tidak optimal                                   │    │
│   │   = Rp 500.000 × 6 siklus = Rp 3.000.000             │    │
│   │ • Listrik boros (kipas nyala terus)                  │    │
│   │   = Rp 200.000 × 12 bulan = Rp 2.400.000             │    │
│   │ • Waktu terbuang = kehilangan peluang bisnis         │    │
│   ├───────────────────────────────────────────────────────┤    │
│   │ TOTAL POTENSI KERUGIAN: Rp 20.000.000+/tahun         │    │
│   └───────────────────────────────────────────────────────┘    │
│                                                                 │
│   DENGAN IoT (Biaya):                                           │
│   ┌───────────────────────────────────────────────────────┐    │
│   │ • Investasi awal: Rp 2.000.000 (1x bayar)            │    │
│   │ • Biaya bulanan: Rp 100.000 × 12 = Rp 1.200.000      │    │
│   ├───────────────────────────────────────────────────────┤    │
│   │ TOTAL BIAYA: Rp 3.200.000/tahun                      │    │
│   └───────────────────────────────────────────────────────┘    │
│                                                                 │
│   📈 SELISIH (PENGHEMATAN): Rp 16.800.000/tahun!               │
│                                                                 │
│   ✅ KESIMPULAN: IoT SANGAT WORTH IT!                          │
│      Balik modal dalam 3-4 bulan pertama.                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🎬 Rekomendasi Video untuk Belajar Mandiri

> **Tonton video ini untuk memperkuat pemahaman Anda!**

### Video Bahasa Indonesia (Recommended!)

```
┌─────────────────────────────────────────────────────────────────┐
│              VIDEO REKOMENDASI                                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🎥 TENTANG IoT DASAR                                          │
│   ─────────────────────────────────────────────────────────────│
│   1. "Apa itu IoT? Penjelasan Sederhana"                       │
│      🔍 Cari di YouTube: "pengenalan IoT bahasa Indonesia"     │
│      ⏱️ Durasi: 5-10 menit                                     │
│                                                                 │
│   2. "Internet of Things untuk Pemula"                         │
│      🔍 Cari di YouTube: "IoT untuk pemula Indonesia"          │
│      ⏱️ Durasi: 10-15 menit                                    │
│                                                                 │
│   🎥 TENTANG IoT PETERNAKAN                                     │
│   ─────────────────────────────────────────────────────────────│
│   3. "Smart Farming Indonesia"                                  │
│      🔍 Cari di YouTube: "smart farm Indonesia"                │
│      ⏱️ Banyak contoh nyata dari peternak Indonesia            │
│                                                                 │
│   4. eFishery Official Channel                                  │
│      🔍 Cari di YouTube: "eFishery"                            │
│      ⏱️ Lihat demo produk smart feeder                         │
│                                                                 │
│   5. "Kandang Ayam Pintar / Smart Poultry"                     │
│      🔍 Cari di YouTube: "kandang ayam pintar IoT"             │
│      ⏱️ Contoh implementasi di Indonesia                       │
│                                                                 │
│   🎥 CHANNEL YANG BISA DIFOLLOW                                 │
│   ─────────────────────────────────────────────────────────────│
│   • Indobot Academy - Tutorial IoT bahasa Indonesia            │
│   • Kelas IoT - Belajar IoT dari dasar                         │
│   • Kementerian Pertanian RI - Program digitalisasi            │
│                                                                 │
│   💡 TIPS MENONTON:                                             │
│   • Tidak perlu mengerti 100%                                  │
│   • Fokus pada KONSEP, bukan detail teknis                     │
│   • Catat pertanyaan untuk didiskusikan di kelas               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 1. 🐔 Peternakan Ayam (Poultry)

```
┌─────────────────────────────────────────────────────────────────┐
│              IoT di PETERNAKAN AYAM                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🌡️ MONITORING SUHU & KELEMBABAN                               │
│      • Sensor memantau suhu 24 jam                              │
│      • Kipas & sprinkler otomatis                               │
│      • Notifikasi jika suhu tidak ideal                         │
│      Manfaat: Mengurangi kematian akibat heat stress            │
│                                                                 │
│   💨 MONITORING GAS AMONIA                                      │
│      • Sensor mendeteksi kadar amonia                           │
│      • Peringatan jika level berbahaya                          │
│      • Data untuk evaluasi manajemen litter                     │
│      Manfaat: Mencegah penyakit pernapasan                      │
│                                                                 │
│   ⚖️ PENIMBANGAN OTOMATIS                                       │
│      • Timbangan di dalam kandang                               │
│      • Ayam menimbang diri sendiri saat makan                   │
│      • Data berat real-time ke HP                               │
│      Manfaat: Tahu kapan waktu panen optimal                    │
│                                                                 │
│   🍽️ PEMBERIAN PAKAN OTOMATIS                                   │
│      • Pakan keluar sesuai jadwal                               │
│      • Porsi disesuaikan dengan umur                            │
│      • Konsumsi pakan tercatat                                  │
│      Manfaat: FCR (Feed Conversion Ratio) optimal               │
│                                                                 │
│   📷 KAMERA CCTV PINTAR                                         │
│      • Pantau perilaku ayam                                     │
│      • AI deteksi ayam sakit/mati                               │
│      • Rekaman tersimpan di cloud                               │
│      Manfaat: Deteksi dini masalah kesehatan                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 2. 🐄 Peternakan Sapi

```
┌─────────────────────────────────────────────────────────────────────┐
│                    IoT di PETERNAKAN SAPI                           │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│   📍 PELACAKAN GPS (untuk sapi yang digembalakan)                  │
│      • Collar/kalung dengan GPS                                     │
│      • Tahu lokasi sapi real-time                                  │
│      • Peringatan jika sapi keluar area                            │
│      Manfaat: Mencegah kehilangan/pencurian                        │
│                                                                     │
│   🌡️ SENSOR SUHU TUBUH                                             │
│      • Sensor di telinga atau minum                                 │
│      • Deteksi demam = tanda penyakit                              │
│      • Deteksi birahi untuk inseminasi                             │
│      Manfaat: Deteksi dini penyakit, tingkatkan keberhasilan IB    │
│                                                                     │
│   🥛 MONITORING PRODUKSI SUSU (Sapi Perah)                         │
│      • Sensor di mesin perah                                        │
│      • Ukur volume susu tiap pemerahan                             │
│      • Deteksi mastitis dari kualitas susu                         │
│      Manfaat: Optimasi produksi, deteksi dini mastitis             │
│                                                                     │
│   🚶 SENSOR AKTIVITAS                                               │
│      • Accelerometer di kalung sapi                                 │
│      • Deteksi pola jalan, makan, istirahat                        │
│      • Sapi lebih aktif = tanda birahi                             │
│      Manfaat: Timing inseminasi tepat = tingkat kebuntingan naik   │
│                                                                     │
│   ⚖️ PENIMBANGAN WALK-OVER                                         │
│      • Timbangan di jalan menuju minum                              │
│      • Sapi ditimbang otomatis saat lewat                          │
│      • Data berat harian tanpa stres                               │
│      Manfaat: Monitor pertumbuhan, prediksi waktu jual             │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

### 3. 🐷 Peternakan Babi

```
┌─────────────────────────────────────────────────────────────────┐
│              IoT di PETERNAKAN BABI                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🌡️ KONTROL IKLIM OTOMATIS                                     │
│      • Sensor suhu di tiap kandang                              │
│      • Sistem pendingin/pemanas otomatis                        │
│      • Berbeda untuk anak babi dan induk                        │
│                                                                 │
│   📷 MONITORING VIDEO + AI                                      │
│      • Kamera di atas kandang                                   │
│      • AI mendeteksi batuk (tanda penyakit)                     │
│      • Hitung jumlah babi otomatis                              │
│                                                                 │
│   🍽️ SMART FEEDING                                              │
│      • Dispenser pakan otomatis                                 │
│      • Porsi disesuaikan berat & umur                           │
│      • RFID mengidentifikasi babi individual                    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 4. 🐐 Peternakan Kambing/Domba

```
┌─────────────────────────────────────────────────────────────────┐
│              IoT di PETERNAKAN KAMBING/DOMBA                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📍 GPS TRACKING                                               │
│      • Pelacakan saat digembalakan                              │
│      • Geofencing (batas virtual)                               │
│      • Anti pencurian                                           │
│                                                                 │
│   🌡️ SENSOR SUHU TUBUH                                          │
│      • Deteksi penyakit dini                                    │
│      • Monitoring kebuntingan                                   │
│      • Prediksi waktu beranak                                   │
│                                                                 │
│   ⚖️ PENIMBANGAN BERKALA                                        │
│      • Monitor pertumbuhan anak                                 │
│      • Evaluasi kualitas pakan                                  │
│      • Tentukan waktu jual optimal                              │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 5. 🐟 Budidaya Ikan (Akuakultur)

```
┌─────────────────────────────────────────────────────────────────┐
│              IoT di BUDIDAYA IKAN                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🌡️ MONITORING KUALITAS AIR                                    │
│      • Suhu air                                                 │
│      • pH (keasaman)                                            │
│      • Oksigen terlarut (DO)                                    │
│      • Amonia                                                   │
│      Manfaat: Mencegah kematian massal ikan                     │
│                                                                 │
│   🍽️ SMART FEEDER                                               │
│      • Pemberian pakan otomatis                                 │
│      • Jadwal sesuai jam makan optimal                          │
│      • Kurangi pakan terbuang                                   │
│                                                                 │
│   💨 AERATOR OTOMATIS                                           │
│      • Nyalakan jika oksigen rendah                             │
│      • Hemat listrik (tidak nyala terus)                        │
│      • Peringatan jika aerator rusak                            │
│                                                                 │
│   📷 KAMERA BAWAH AIR                                           │
│      • Pantau perilaku ikan                                     │
│      • Deteksi penyakit                                         │
│      • Estimasi populasi                                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 💰 Manfaat Ekonomi IoT untuk Peternak

> 📚 **Catatan Akademis:**  
> Menurut studi dari FAO (2022), digitalisasi peternakan terbukti dapat meningkatkan efisiensi produksi hingga 15-30% dan mengurangi kerugian pascapanen. Konsep ini dikenal sebagai **Precision Livestock Farming (PLF)** yang dikembangkan sejak awal 2000-an (Berckmans, 2017).

```
┌─────────────────────────────────────────────────────────────────┐
│              DAMPAK FINANSIAL IoT                               │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📊 HASIL RISET & STUDI KASUS:                                 │
│                                                                 │
│   ┌───────────────────────────────────────────────────────┐     │
│   │ Aspek                    │ Peningkatan/Penghematan  │     │
│   ├───────────────────────────────────────────────────────┤     │
│   │ Mortalitas (kematian)    │ ⬇️ Turun 15-30%          │     │
│   │ Efisiensi pakan (FCR)    │ ⬆️ Naik 5-15%            │     │
│   │ Waktu monitoring         │ ⬇️ Turun 50-70%          │     │
│   │ Biaya listrik            │ ⬇️ Hemat 10-20%          │     │
│   │ Deteksi penyakit         │ ⬆️ Lebih cepat 24-48 jam │     │
│   │ Produktivitas susu       │ ⬆️ Naik 10-15%           │     │
│   │ Keberhasilan IB          │ ⬆️ Naik 20-30%           │     │
│   └───────────────────────────────────────────────────────┘     │
│                                                                 │
│   💡 CONTOH PERHITUNGAN SEDERHANA:                              │
│                                                                 │
│   Peternakan 5.000 ekor ayam broiler                            │
│   Mortalitas normal: 5% = 250 ekor mati                         │
│   Dengan IoT: 3% = 150 ekor mati                                │
│   Selisih: 100 ekor × Rp 25.000 = Rp 2.500.000/siklus          │
│                                                                 │
│   Dalam 1 tahun (6 siklus):                                     │
│   Rp 2.500.000 × 6 = Rp 15.000.000 PENGHEMATAN!                │
│                                                                 │
│   💵 Investasi sistem IoT sederhana: ~Rp 5.000.000              │
│   📈 ROI (Return on Investment): Balik modal dalam 1 tahun!    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## ⚠️ Tantangan Penerapan IoT di Indonesia

### Kita Harus Realistis!

```
┌─────────────────────────────────────────────────────────────────┐
│              TANTANGAN & SOLUSINYA                              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ❌ TANTANGAN 1: Tidak Ada Internet di Kandang                 │
│   ✅ SOLUSI:                                                    │
│      • Gunakan teknologi LoRa (jangkauan 15 km tanpa internet)  │
│      • Pakai modem GSM/4G (mengikuti sinyal HP)                 │
│      • Sistem hybrid: simpan data lokal, kirim saat ada sinyal  │
│                                                                 │
│   ❌ TANTANGAN 2: Tidak Ada Listrik Stabil                      │
│   ✅ SOLUSI:                                                    │
│      • Solar panel + baterai                                    │
│      • Perangkat IoT hemat daya                                 │
│      • Sistem backup power (UPS)                                │
│                                                                 │
│   ❌ TANTANGAN 3: Biaya Awal Mahal                              │
│   ✅ SOLUSI:                                                    │
│      • Mulai dari yang sederhana (suhu saja dulu)               │
│      • Sistem DIY dengan komponen murah                         │
│      • Kerjasama dengan kampus/lembaga penelitian               │
│      • Akses pembiayaan (KUR, hibah teknologi)                  │
│                                                                 │
│   ❌ TANTANGAN 4: Tidak Paham Teknologi                         │
│   ✅ SOLUSI:                                                    │
│      • Ini sebabnya Anda di kelas ini! 📚                       │
│      • Aplikasi yang user-friendly                              │
│      • Pelatihan dan pendampingan                               │
│      • Komunitas peternak smart farming                         │
│                                                                 │
│   ❌ TANTANGAN 5: Perangkat Rusak/Error                         │
│   ✅ SOLUSI:                                                    │
│      • Pilih perangkat berkualitas                              │
│      • Perawatan rutin                                          │
│      • Redundancy (backup sensor)                               │
│      • Garansi dan layanan purna jual                           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🚀 Tren Masa Depan: Kemana IoT Akan Membawa Peternakan?

```
┌─────────────────────────────────────────────────────────────────┐
│              MASA DEPAN PETERNAKAN CERDAS                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🤖 ARTIFICIAL INTELLIGENCE (AI)                               │
│      • AI memprediksi penyakit sebelum gejala muncul           │
│      • Rekomendasi pakan optimal dari data                      │
│      • Deteksi perilaku abnormal otomatis                       │
│                                                                 │
│   🔗 BLOCKCHAIN                                                 │
│      • Lacak asal-usul produk (farm to table)                  │
│      • Sertifikasi digital yang tidak bisa dipalsukan          │
│      • Kepercayaan konsumen meningkat                          │
│                                                                 │
│   🦾 ROBOTIKA                                                   │
│      • Robot pemberi pakan                                      │
│      • Robot pembersih kandang                                  │
│      • Robot pemerah susu otomatis                              │
│                                                                 │
│   🛸 DRONE                                                      │
│      • Memantau ternak di padang gembala                       │
│      • Menghitung populasi dari udara                          │
│      • Mendeteksi predator                                      │
│                                                                 │
│   🌱 PRECISION LIVESTOCK FARMING                                │
│      • Setiap ternak diperlakukan individu                     │
│      • Pakan, obat, perawatan disesuaikan                      │
│      • Maksimalkan potensi genetik                             │
│                                                                 │
│   💡 KABAR BAIKNYA:                                             │
│      Dengan mempelajari IoT sekarang, Anda sudah menyiapkan    │
│      diri untuk masa depan peternakan Indonesia!                │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📋 Overview Mata Kuliah Ini

### Apa Saja yang Akan Kita Pelajari?

```
┌─────────────────────────────────────────────────────────────────┐
│              ROADMAP MATA KULIAH IoT                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📗 BAGIAN 1: DASAR-DASAR (Pertemuan 1-5)                     │
│   ├── 1. Pengantar IoT dan Penerapannya ← ANDA DI SINI!        │
│   ├── 2. Perangkat IoT (Device, Gateway, Cloud, Aplikasi)      │
│   ├── 3. Sensor Lingkungan Kandang                             │
│   ├── 4. Aktuator dan Mikrokontroler                           │
│   └── 5. Sistem Komunikasi IoT (WiFi, LoRa, GSM)               │
│                                                                 │
│   📘 BAGIAN 2: APLIKASI & MONITORING (Pertemuan 6-7)           │
│   ├── 6. Monitoring Kandang (Dashboard Produksi)               │
│   └── 7. Studi Kasus IoT pada Manajemen Ternak                 │
│                                                                 │
│   ═══════════════════ UTS ═══════════════════                   │
│                                                                 │
│   📙 BAGIAN 3: AI & MACHINE LEARNING (Pertemuan 9-11)          │
│   ├── 9. Penerapan AI pada Bidang Peternakan                   │
│   ├── 10. Machine Learning untuk Analisis Produksi             │
│   └── 11. Deteksi Penyakit dan Optimasi Pakan berbasis AI      │
│                                                                 │
│   📕 BAGIAN 4: SMART FARMING (Pertemuan 12-15)                 │
│   ├── 12. Penerapan Smart Poultry System                       │
│   ├── 13. Integrasi Smart Circular Farming                     │
│   └── 14-15. Rancangan Smart Poultry & Circular Farming        │
│                                                                 │
│   🎯 TUJUAN AKHIR:                                              │
│   Anda bisa merancang sistem IoT sederhana untuk peternakan!   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📝 Rangkuman Pertemuan 1

```
┌─────────────────────────────────────────────────────────────────┐
│                       RANGKUMAN                                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1️⃣ APA ITU IoT?                                               │
│      Internet of Things = benda-benda yang terhubung internet   │
│      dan bisa "berbicara" memberikan informasi                  │
│                                                                 │
│   2️⃣ MENGAPA PENTING UNTUK PETERNAKAN?                          │
│      • Monitoring 24/7 dari jarak jauh                          │
│      • Deteksi masalah lebih cepat                              │
│      • Data akurat untuk pengambilan keputusan                  │
│      • Efisiensi waktu, tenaga, dan biaya                       │
│                                                                 │
│   3️⃣ CONTOH PENERAPAN                                           │
│      • Monitoring suhu, kelembaban, gas                         │
│      • Penimbangan otomatis                                     │
│      • Pemberian pakan otomatis                                 │
│      • Pelacakan GPS ternak                                     │
│      • Deteksi penyakit dini                                    │
│                                                                 │
│   4️⃣ TANTANGAN DI INDONESIA                                     │
│      • Infrastruktur (internet, listrik)                        │
│      • Biaya awal                                               │
│      • Pengetahuan teknologi                                    │
│      → Semua bisa diatasi dengan solusi yang tepat!             │
│                                                                 │
│   5️⃣ PESAN UTAMA                                                │
│      IoT bukan menggantikan peternak, tapi MEMBANTU peternak   │
│      bekerja lebih CERDAS, bukan lebih KERAS!                   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## ❓ Pertanyaan Diskusi

1. **Menurut pengalaman Anda atau keluarga, apa masalah terbesar dalam mengelola peternakan yang mungkin bisa diselesaikan dengan IoT?**

2. **Jika Anda bisa memilih SATU sensor untuk dipasang di kandang, sensor apa yang akan Anda pilih dan mengapa?**

3. **Apa kekhawatiran terbesar Anda tentang penerapan teknologi IoT di peternakan tradisional?**

4. **Bayangkan peternakan ideal Anda 10 tahun ke depan. Teknologi apa saja yang akan ada di sana?**

5. **Menurut Anda, apakah peternak kecil di Indonesia bisa mengadopsi IoT? Bagaimana caranya?**

---

## 📚 Istilah Penting Pertemuan Ini

| Istilah           | Arti                                                          |
| ----------------- | ------------------------------------------------------------- |
| **IoT**           | Internet of Things - benda-benda yang terhubung internet      |
| **Smart Farming** | Pertanian/peternakan yang menggunakan teknologi digital       |
| **Sensor**        | Alat untuk mendeteksi dan mengukur kondisi (suhu, berat, dll) |
| **Cloud**         | Penyimpanan data di internet (bukan di komputer lokal)        |
| **Real-time**     | Data yang dikirim dan diterima saat itu juga                  |
| **Dashboard**     | Tampilan visual untuk memonitor data                          |
| **Notifikasi**    | Pemberitahuan otomatis (biasanya ke HP)                       |
| **Monitoring**    | Pemantauan kondisi secara berkala/terus-menerus               |

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Daftar pustaka ini berguna jika Anda ingin mempelajari lebih dalam atau mengutip untuk tugas/skripsi. Tidak perlu membaca semuanya sekarang!

### Sumber Akademik

| No  | Referensi                                                                                                  | Keterangan                                         |
| --- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------- |
| 1   | Ashton, K. (2009). _That 'Internet of Things' Thing_. RFID Journal.                                        | Artikel asli pencetus istilah "Internet of Things" |
| 2   | ITU-T (2012). _Recommendation ITU-T Y.2060: Overview of the Internet of Things_. Geneva: ITU.              | Definisi resmi IoT dari badan PBB                  |
| 3   | Berckmans, D. (2017). General introduction to precision livestock farming. _Animal Frontiers_, 7(1), 6-11. | Pengantar konsep Precision Livestock Farming       |
| 4   | FAO (2022). _The State of Food and Agriculture 2022: Leveraging automation in agriculture_. Rome: FAO.     | Laporan global digitalisasi pertanian & peternakan |
| 5   | Neethirajan, S., & Kemp, B. (2021). Digital Phenotyping in Livestock Farming. _Animals_, 11(7), 2009.      | Jurnal tentang teknologi digital di peternakan     |

### Sumber Data Statistik

| No  | Referensi                                                                               | Keterangan                           |
| --- | --------------------------------------------------------------------------------------- | ------------------------------------ |
| 6   | Statista (2024). _Number of IoT connected devices worldwide_. Tersedia di: statista.com | Data jumlah perangkat IoT global     |
| 7   | IoT Analytics (2023). _State of IoT 2023_. Tersedia di: iot-analytics.com               | Prediksi pertumbuhan IoT hingga 2030 |

### Sumber Lokal Indonesia

| No  | Referensi                                                                             | Keterangan                                 |
| --- | ------------------------------------------------------------------------------------- | ------------------------------------------ |
| 8   | Kementerian Pertanian RI (2023). _Roadmap Digitalisasi Pertanian 2024-2045_. Jakarta. | Kebijakan pemerintah tentang smart farming |
| 9   | Chickin Technology. (2023). _Laporan Dampak IoT pada Peternakan Ayam Broiler_.        | Studi kasus startup IoT lokal              |
| 10  | Pitik Indonesia. _Digital Poultry Farming Report_. Tersedia di: pitik.id              | Implementasi IoT kemitraan ayam            |

---

## 📖 Bacaan Tambahan (Opsional)

> 💡 Ini untuk yang ingin eksplorasi lebih lanjut secara santai!

**Video YouTube (Bahasa Indonesia):**

- "Pengenalan IoT untuk Pemula" - Channel Indobot Academy
- "Smart Farm Indonesia" - berbagai testimoni peternak
- "eFishery Official" - demo smart feeder untuk ikan

**Website Bermanfaat:**

- **pertanian.go.id** - Portal resmi Kementerian Pertanian
- **chickin.id** - Solusi IoT peternakan ayam lokal
- **efishery.com** - Platform smart aquaculture Indonesia

**Komunitas Online:**

- Grup Facebook: "Smart Farming Indonesia"
- Telegram: Komunitas IoT Indonesia

---

## 🎯 Tugas Pertemuan 1

### Tugas Individu (Dikumpulkan Minggu Depan)

1. **Observasi Singkat**
   - Kunjungi atau wawancara peternak di sekitar Anda (ayam, sapi, kambing, ikan, dll)
   - Tanyakan: Apa masalah terbesar yang mereka hadapi dalam mengelola ternak?
   - Pikirkan: Apakah masalah tersebut bisa diselesaikan dengan IoT?

2. **Tulis Laporan Singkat (1 halaman)**
   - Jenis ternak apa yang diobservasi?
   - Masalah apa yang ditemukan?
   - Ide solusi IoT yang mungkin membantu

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar tentang **Perangkat IoT** - apa saja komponen yang diperlukan untuk membangun sistem IoT di peternakan (Device, Gateway, Cloud, Aplikasi)!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_  
_Semester Genap 2025/2026_
