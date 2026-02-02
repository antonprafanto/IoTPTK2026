# 🏥 Pertemuan 11: Deteksi Penyakit dan Optimasi Pakan pada Ternak Unggas Berbasis AI

> **Dosen Pengampu:** Novemia & Carenina  
> **Waktu:** 100 menit  
> **Semester Genap 2025/2026**

---

> 💬 **"Mencegah lebih baik daripada mengobati - dan AI membantu kita mendeteksi masalah SEBELUM menjadi bencana!"**

---

## 🎯 Tujuan Pembelajaran

Setelah mengikuti pertemuan ini, mahasiswa diharapkan mampu:

1. ✅ Memahami bagaimana AI mendeteksi penyakit unggas secara dini
2. ✅ Menjelaskan teknologi yang digunakan untuk deteksi penyakit
3. ✅ Memahami konsep optimasi pakan berbasis AI
4. ✅ Menganalisis manfaat dan keterbatasan teknologi ini untuk peternak Indonesia

---

## 🎬 Cerita Pembuka: Wabah yang Bisa Dicegah

### 😢 Tragedi di Peternakan Pak Darno

| Hari         | Kejadian                                             |
| ------------ | ---------------------------------------------------- |
| **Senin**    | Pak Darno lihat 3 ayam agak lesu, pikir "cuma capek" |
| **Rabu**     | 15 ayam mulai bersin-bersin, Pak Darno kasih vitamin |
| **Jumat**    | 50 ayam mati, mulai panik!                           |
| **Minggu**   | 500 ayam mati, baru panggil dokter hewan             |
| **Minggu+2** | 2.000 dari 5.000 ayam mati (40%!) 💀                 |

**Kerugian Pak Darno:**

- 💀 2.000 ayam @ Rp 25.000 = **Rp 50.000.000**
- 💊 Biaya obat dan dokter = Rp 8.000.000
- 📉 Ayam sisa tidak optimal = kerugian tambahan Rp 20.000.000
- **Total kerugian: ~Rp 78.000.000** 😭

### 🎉 Cerita Berbeda: Bu Rina dengan AI

| Hari             | Kejadian                                                         |
| ---------------- | ---------------------------------------------------------------- |
| **Senin, 02:00** | Sistem AI mendeteksi 5 ayam dengan pola gerakan abnormal         |
| **Senin, 06:00** | Alert ke HP: "⚠️ 5 ayam zona C menunjukkan gejala awal penyakit" |
| **Senin, 08:00** | Bu Rina isolasi 5 ayam + cek laboratorium                        |
| **Selasa**       | Hasil lab: infeksi bakteri dini, 5 ayam diobati                  |
| **Minggu**       | 4.995 ayam sehat, hanya 5 yang sakit (0.1%) ✅                   |

**"Biaya" Bu Rina:**

- 💊 Pengobatan 5 ayam = Rp 150.000
- 🔬 Tes laboratorium = Rp 200.000
- **Total: Rp 350.000** (vs Rp 78.000.000 Pak Darno!)

> 💡 **Perbedaannya?** AI Bu Rina mendeteksi penyakit **SEBELUM** terlihat oleh mata manusia!

---

## 📖 BAGIAN 1: Deteksi Penyakit Unggas dengan AI

### 🔍 Mengapa Deteksi Dini Sangat Penting?

```
┌─────────────────────────────────────────────────────────────────┐
│              TIMELINE PERKEMBANGAN PENYAKIT                     │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   HARI 1-2: FASE TERSEMBUNYI                                    │
│   ══════════════════════════════════════════════════════════    │
│   👁️ Mata Manusia: Tidak terlihat                              │
│   🤖 AI: BISA DETEKSI! (perubahan perilaku halus)              │
│   💊 Pengobatan: Sangat efektif, biaya minimal                  │
│                                                                 │
│   HARI 3-5: FASE AWAL GEJALA                                    │
│   ══════════════════════════════════════════════════════════    │
│   👁️ Mata Manusia: Mulai terlihat (lesu, bersin)              │
│   🤖 AI: Sudah konfirmasi sejak hari 1-2                        │
│   💊 Pengobatan: Masih efektif, biaya sedang                   │
│                                                                 │
│   HARI 6+: FASE AKUT                                            │
│   ══════════════════════════════════════════════════════════    │
│   👁️ Mata Manusia: Jelas terlihat (sekarat, mati)              │
│   🤖 AI: Sudah warning sejak hari 1!                            │
│   💊 Pengobatan: Sulit, banyak yang mati, biaya tinggi         │
│                                                                 │
│   💡 KESIMPULAN: AI memberi waktu 3-5 hari lebih awal!         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> 📚 **Catatan Akademis:**  
> Menurut penelitian Zhuang & Zhang (2019), deteksi penyakit berbasis AI dapat mengidentifikasi gejala 2-5 hari lebih awal dibanding pengamatan visual, dengan akurasi mencapai 95%.

---

### 🎥 Teknologi Deteksi Penyakit

#### 1️⃣ Computer Vision (Kamera + AI)

| Apa yang Diamati  | Indikator Penyakit                  | Akurasi |
| ----------------- | ----------------------------------- | ------- |
| **Postur tubuh**  | Sayap turun, kepala menunduk        | 92%     |
| **Warna jengger** | Pucat, kebiruan, atau terlalu merah | 88%     |
| **Mata**          | Berair, bengkak, tertutup           | 90%     |
| **Bulu**          | Kusam, rontok, tidak rapi           | 85%     |
| **Gerakan**       | Lesu, tidak aktif, berputar-putar   | 94%     |

```
┌─────────────────────────────────────────────────────────────────┐
│              CARA KERJA COMPUTER VISION                         │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📷 LANGKAH 1: Kamera merekam video 24/7                       │
│        ↓                                                        │
│   🔲 LANGKAH 2: AI memproses frame per frame                   │
│        ↓                                                        │
│   🔍 LANGKAH 3: AI menganalisis setiap ayam:                    │
│        • Postur tubuh                                           │
│        • Warna (jengger, mata)                                  │
│        • Pola gerakan                                           │
│        ↓                                                        │
│   📊 LANGKAH 4: Dibandingkan dengan database ayam sehat        │
│        ↓                                                        │
│   ⚠️ LANGKAH 5: Jika ada anomali → kirim ALERT                 │
│                                                                 │
│   ⏱️ Kecepatan: 50-100 ayam per detik!                         │
│   🕐 Frekuensi: Setiap 15 menit                                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

#### 2️⃣ Audio Analysis (Mikrofon + AI)

**Fakta Menarik:** Ayam "berbicara" tentang kondisinya melalui suara!

| Jenis Suara           | Artinya                  | Tindakan           |
| --------------------- | ------------------------ | ------------------ |
| 🔊 Kokok normal       | Sehat, aktif             | Tidak perlu        |
| 😤 Bersin berulang    | Gangguan pernapasan      | Cek kualitas udara |
| 😩 Rintihan/mengerang | Sakit atau stres         | Periksa segera     |
| 🤫 Terlalu hening     | Depresi/sakit parah      | Alert darurat!     |
| 😨 Berteriak panik    | Predator atau stres akut | Cek keamanan       |

> 💡 **Tahukah Anda?**  
> AI dapat membedakan suara batuk normal dengan batuk gejala CRD (Chronic Respiratory Disease) dengan akurasi 89% menurut penelitian Cuan et al. (2020).

---

#### 3️⃣ Sensor Perilaku + AI

```
┌─────────────────────────────────────────────────────────────────┐
│              INDIKATOR PERILAKU ABNORMAL                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📉 KONSUMSI PAKAN TURUN                                       │
│   ─────────────────────────────────────────────────────────────│
│   Normal: 110-130 gram/ekor/hari                               │
│   Warning: Turun > 10% selama 2 hari berturut                  │
│   Alert: Turun > 20%                                            │
│                                                                 │
│   📉 KONSUMSI AIR TURUN                                         │
│   ─────────────────────────────────────────────────────────────│
│   Normal: 180-220 ml/ekor/hari (1.7-2x pakan)                  │
│   Warning: Rasio air:pakan < 1.5                               │
│   Alert: Rasio < 1.3                                           │
│                                                                 │
│   📊 BERAT BADAN TIDAK NAIK                                     │
│   ─────────────────────────────────────────────────────────────│
│   Normal: ADG 55-65 gram/hari                                   │
│   Warning: ADG < 50 gram/hari                                   │
│   Alert: ADG < 40 gram/hari atau turun                         │
│                                                                 │
│   🏃 AKTIVITAS MENURUN                                          │
│   ─────────────────────────────────────────────────────────────│
│   (Diukur dengan sensor gerak atau kamera)                     │
│   Warning: Aktivitas < 70% dari normal                         │
│   Alert: Aktivitas < 50%                                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 🦠 Penyakit yang Bisa Dideteksi AI

| Penyakit                   | Gejala yang Dideteksi AI       | Waktu Deteksi       |
| -------------------------- | ------------------------------ | ------------------- |
| **Newcastle Disease (ND)** | Gerakan abnormal, sayap turun  | 2-3 hari lebih awal |
| **Avian Influenza (AI)**   | Jengger kebiruan, lesu         | 2-4 hari lebih awal |
| **CRD**                    | Suara bersin, nafas berat      | 3-5 hari lebih awal |
| **Gumboro (IBD)**          | Bulu kusut, diare (via kamera) | 2-3 hari lebih awal |
| **Coccidiosis**            | Feses berdarah, lesu           | 1-2 hari lebih awal |

---

## 📖 BAGIAN 2: Optimasi Pakan dengan AI

### 🍽️ Mengapa Pakan Perlu Dioptimasi?

```
┌─────────────────────────────────────────────────────────────────┐
│              FAKTA TENTANG PAKAN                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   💰 BIAYA PAKAN = 60-70% TOTAL BIAYA PRODUKSI                 │
│                                                                 │
│   Pada peternakan 10.000 ekor ayam broiler:                    │
│   • Total pakan per siklus: ~35.000 kg                         │
│   • Harga pakan: ~Rp 8.500/kg                                  │
│   • Biaya pakan per siklus: ~Rp 297.500.000                    │
│                                                                 │
│   ⚠️ JIKA FCR BURUK (1.8 vs target 1.6):                       │
│   • Kelebihan pakan: 4.200 kg                                   │
│   • Kerugian: Rp 35.700.000 per siklus!                        │
│                                                                 │
│   ✅ JIKA AI BISA OPTIMASI 5% SAJA:                            │
│   • Hemat pakan: 1.750 kg                                       │
│   • Hemat biaya: Rp 14.875.000 per siklus!                     │
│   • Per tahun (7 siklus): Rp 104.125.000!                      │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 🔬 Bagaimana AI Mengoptimasi Pakan?

#### 1️⃣ Precision Feeding (Pemberian Pakan Presisi)

| Faktor                | Pengaruh ke Pakan         | Penyesuaian AI             |
| --------------------- | ------------------------- | -------------------------- |
| **Umur ayam**         | Kebutuhan nutrisi berubah | Sesuaikan formula per fase |
| **Berat aktual**      | Target vs realita         | Tambah/kurangi porsi       |
| **Suhu lingkungan**   | Panas → makan berkurang   | Ubah jadwal pemberian      |
| **Kondisi kesehatan** | Sakit → nafsu makan turun | Tambah vitamin/obat        |
| **Target panen**      | Berat yang diinginkan     | Hitung kebutuhan total     |

```
┌─────────────────────────────────────────────────────────────────┐
│              CONTOH PRECISION FEEDING                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📊 DATA INPUT:                                                │
│   • Umur: 21 hari                                               │
│   • Berat rata-rata: 850 gram (target: 900 gram)               │
│   • Suhu kandang: 31°C (lebih panas dari ideal)                │
│   • FCR saat ini: 1.55                                          │
│                                                                 │
│   🧠 AI MENGANALISIS:                                           │
│   • Ayam 50 gram di bawah target                               │
│   • Suhu tinggi menyebabkan nafsu makan turun                  │
│   • FCR masih bagus, potensi untuk dipertahankan               │
│                                                                 │
│   📋 REKOMENDASI AI:                                            │
│   ─────────────────────────────────────────────────────────────│
│   1. Tambah porsi pakan 5% (80 → 84 gram per pemberian)        │
│   2. Ubah jadwal: 60% pakan di pagi (sejuk), 40% sore          │
│   3. Tambah feeding frequency: 3x → 4x sehari                  │
│   4. Alert jika suhu > 32°C (nyalakan cooling)                 │
│                                                                 │
│   🎯 TARGET: Berat kembali on-track dalam 3 hari               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

#### 2️⃣ Formula Pakan Dinamis

**Masalah Tradisional:**

- Peternak beli 1 jenis pakan untuk semua kondisi
- Tidak mempertimbangkan kondisi aktual ayam
- "Satu ukuran untuk semua" = tidak efisien

**Solusi AI:**

| Fase     | Umur       | Protein | Energi     | Catatan AI             |
| -------- | ---------- | ------- | ---------- | ---------------------- |
| Starter  | 0-10 hari  | 22-24%  | 3.000 kcal | Fokus pembentukan otot |
| Grower   | 11-24 hari | 20-22%  | 3.100 kcal | Pertumbuhan optimal    |
| Finisher | 25-35 hari | 18-20%  | 3.200 kcal | Efisiensi konversi     |

> 📚 **Catatan Akademis:**  
> Menurut Aviagen (2022), penyesuaian formula pakan berdasarkan performa aktual dapat meningkatkan efisiensi pakan (FCR) hingga 3-5%.

---

#### 3️⃣ Smart Feeder dengan AI

```
┌─────────────────────────────────────────────────────────────────┐
│              CARA KERJA SMART FEEDER                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ┌─────────┐                                                   │
│   │ SILO    │ ← Pakan disimpan                                  │
│   │ PAKAN   │                                                   │
│   └────┬────┘                                                   │
│        │                                                         │
│        ▼                                                         │
│   ┌─────────┐      ┌─────────┐                                  │
│   │ HOPPER  │──────│ SENSOR  │ ← Mengukur jumlah pakan         │
│   │         │      │ BERAT   │                                  │
│   └────┬────┘      └─────────┘                                  │
│        │                                                         │
│        ▼                                                         │
│   ┌─────────┐      ┌─────────┐                                  │
│   │TEMPAT   │──────│ SENSOR  │ ← Mendeteksi ayam makan         │
│   │ PAKAN   │      │ AKTIVITAS│                                 │
│   └─────────┘      └─────────┘                                  │
│        │                                                         │
│        ▼                                                         │
│   ┌─────────────────────────────┐                               │
│   │        AI CLOUD             │                               │
│   │ • Analisis pola konsumsi    │                               │
│   │ • Prediksi kebutuhan        │                               │
│   │ • Rekomendasi pemberian     │                               │
│   └─────────────────────────────┘                               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📊 Studi Kasus: Optimasi Pakan dengan AI

**Peternakan:** PT Maju Jaya, Jawa Timur  
**Kapasitas:** 50.000 ekor ayam broiler

| Parameter         | Sebelum AI | Sesudah AI | Perubahan |
| ----------------- | ---------- | ---------- | --------- |
| FCR               | 1.72       | 1.58       | ⬇️ 8.1%   |
| Berat Panen       | 2.05 kg    | 2.18 kg    | ⬆️ 6.3%   |
| Uniformity        | 78%        | 89%        | ⬆️ 11%    |
| Biaya Pakan/kg BB | Rp 14.600  | Rp 13.400  | ⬇️ 8.2%   |

**Penghematan per Tahun:**

```
┌─────────────────────────────────────────────────────────────────┐
│              PERHITUNGAN ROI                                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📦 Produksi per tahun: 50.000 × 7 siklus × 2.18 kg           │
│      = 763.000 kg daging                                        │
│                                                                 │
│   💰 Hemat biaya pakan (Rp 1.200/kg BB):                       │
│      = 763.000 × Rp 1.200 = Rp 915.600.000/tahun               │
│                                                                 │
│   📈 Tambahan pendapatan (berat naik 130g/ekor):               │
│      = 350.000 ekor × 130g × Rp 18.000/kg                      │
│      = Rp 819.000.000/tahun                                     │
│                                                                 │
│   🎯 TOTAL BENEFIT: Rp 1.734.600.000/tahun!                    │
│                                                                 │
│   💻 Investasi AI: Rp 250.000.000                              │
│   ⏱️ Payback: 2 bulan!                                          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 3: Integrasi Deteksi Penyakit + Optimasi Pakan

### 🔄 Sistem Terintegrasi

```
┌─────────────────────────────────────────────────────────────────┐
│              SISTEM AI TERINTEGRASI                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                    ┌──────────────┐                             │
│                    │  DASHBOARD   │                             │
│                    │   PETERNAK   │                             │
│                    └──────┬───────┘                             │
│                           │                                     │
│            ┌──────────────┴──────────────┐                      │
│            │         AI ENGINE           │                      │
│            │  (Mengolah semua data)      │                      │
│            └──────────────┬──────────────┘                      │
│                           │                                     │
│     ┌─────────────────────┼─────────────────────┐               │
│     │                     │                     │               │
│     ▼                     ▼                     ▼               │
│ ┌────────┐          ┌──────────┐          ┌──────────┐         │
│ │DETEKSI │          │OPTIMASI  │          │LINGKUNGAN│         │
│ │PENYAKIT│          │  PAKAN   │          │ KANDANG  │         │
│ ├────────┤          ├──────────┤          ├──────────┤         │
│ │• Kamera│          │• Feeder  │          │• Suhu    │         │
│ │• Audio │          │• Sensor  │          │• Humidity│         │
│ │• Sensor│          │• Formula │          │• Amonia  │         │
│ └────────┘          └──────────┘          └──────────┘         │
│                                                                 │
│   💡 CONTOH INTEGRASI:                                          │
│   AI deteksi: "5 ayam zona C mulai sakit"                      │
│   AI action:  "Kurangi pakan zona C 10%, tambah vitamin"        │
│   AI alert:   "Isolasi 5 ayam, jadwalkan pemeriksaan"          │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 4: Platform yang Tersedia di Indonesia

### 🇮🇩 Solusi Lokal

| Platform    | Fitur                                         | Kelebihan                    | Harga Estimasi     |
| ----------- | --------------------------------------------- | ---------------------------- | ------------------ |
| **Chickin** | Monitoring, prediksi performa, alert penyakit | Khusus unggas, support lokal | Rp 500rb-2jt/bulan |
| **JALA**    | Untuk akuakultur (referensi teknologi serupa) | Precision feeding            | Rp 1-3jt/bulan     |
| **FarmIn**  | Manajemen ternak terintegrasi                 | Multi-species                | Rp 300rb-1jt/bulan |

### 🌍 Solusi Global

| Platform       | Fokus                       | Keunggulan                          |
| -------------- | --------------------------- | ----------------------------------- |
| **Faromatics** | Robot monitoring ayam       | ChickenBoy - robot keliling kandang |
| **Cainthus**   | Computer vision sapi/unggas | Akurasi deteksi sangat tinggi       |
| **eYeGrow**    | Monitoring ayam             | Analisis video real-time            |

---

## 📖 BAGIAN 5: Tantangan dan Solusi

### ⚠️ Tantangan Implementasi

| Tantangan                 | Penjelasan                        | Solusi                         |
| ------------------------- | --------------------------------- | ------------------------------ |
| **Biaya awal tinggi**     | Kamera, sensor, software mahal    | Mulai dari 1 kandang pilot     |
| **Butuh internet stabil** | AI cloud perlu koneksi            | Cari provider dengan edge AI   |
| **SDM kurang terampil**   | Peternak belum familiar teknologi | Training bertahap              |
| **Data privacy**          | Data produksi sensitif            | Pilih vendor terpercaya        |
| **Akurasi belum 100%**    | AI masih bisa salah               | Kombinasikan dengan pengalaman |

### 💡 Tips Implementasi

```
┌─────────────────────────────────────────────────────────────────┐
│              LANGKAH IMPLEMENTASI BERTAHAP                      │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   TAHAP 1: PERSIAPAN (Bulan 1-2)                               │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Pastikan infrastruktur (listrik, internet) siap           │
│   ✓ Pilih 1 kandang untuk pilot project                        │
│   ✓ Riset dan pilih vendor yang sesuai budget                 │
│                                                                 │
│   TAHAP 2: PILOT (Bulan 3-4)                                    │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Install sistem di 1 kandang                                │
│   ✓ Training untuk operator                                    │
│   ✓ Kumpulkan data, bandingkan dengan kandang kontrol         │
│                                                                 │
│   TAHAP 3: EVALUASI (Bulan 5-6)                                 │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Hitung ROI dari pilot                                      │
│   ✓ Identifikasi masalah dan solusi                            │
│   ✓ Putuskan: lanjut atau tidak                                │
│                                                                 │
│   TAHAP 4: SCALE UP (Bulan 7+)                                  │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Jika sukses, expand ke kandang lain                        │
│   ✓ Bertahap sesuai kemampuan finansial                        │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📊 Ringkasan Pertemuan 11

| Topik                  | Poin Penting                                       |
| ---------------------- | -------------------------------------------------- |
| **Deteksi Penyakit**   | AI deteksi 2-5 hari lebih awal dari mata manusia   |
| **Teknologi**          | Computer Vision, Audio Analysis, Sensor Perilaku   |
| **Optimasi Pakan**     | Pakan = 60-70% biaya, optimasi 5% = hemat jutaan   |
| **Precision Feeding**  | Sesuaikan pakan berdasarkan kondisi aktual         |
| **Integrasi**          | Deteksi penyakit + optimasi pakan saling terhubung |
| **Platform Indonesia** | Chickin, FarmIn (unggas), JALA (ikan)              |
| **Tantangan**          | Biaya, SDM, internet, akurasi belum 100%           |
| **Tips**               | Mulai pilot kecil, evaluasi ROI, scale up bertahap |

---

## ❓ Pertanyaan Diskusi

1. **Dari cerita Pak Darno dan Bu Rina, pelajaran apa yang paling penting untuk peternak Indonesia?**

2. **Menurut Anda, teknologi deteksi penyakit mana (kamera, audio, sensor) yang paling cocok untuk peternakan rakyat skala kecil? Mengapa?**

3. **Jika Anda adalah peternak dengan budget terbatas, mana yang akan Anda prioritaskan: sistem deteksi penyakit atau sistem optimasi pakan? Jelaskan alasannya.**

4. **Apa hambatan terbesar adopsi teknologi AI di peternakan tradisional Indonesia?**

---

## 📚 Istilah Penting Pertemuan Ini

| Istilah               | Arti Sederhana                                       |
| --------------------- | ---------------------------------------------------- |
| **Computer Vision**   | AI yang bisa "melihat" dan memahami gambar           |
| **Audio Analysis**    | AI yang menganalisis suara (batuk, bersin)           |
| **Precision Feeding** | Pemberian pakan yang disesuaikan kondisi aktual      |
| **FCR**               | Feed Conversion Ratio - efisiensi pakan              |
| **ADG**               | Average Daily Gain - pertambahan berat per hari      |
| **Early Detection**   | Mendeteksi penyakit sebelum gejala terlihat          |
| **Smart Feeder**      | Alat pemberi pakan otomatis dengan sensor            |
| **Edge AI**           | AI yang berjalan di perangkat lokal (tanpa internet) |
| **ROI**               | Return on Investment - berapa cepat investasi balik  |
| **Pilot Project**     | Uji coba skala kecil sebelum implementasi penuh      |

---

## 🎯 Tugas Pertemuan 11

### Tugas Kelompok (3-4 orang)

**Desain Sistem Deteksi Penyakit Sederhana:**

1. Pilih salah satu penyakit unggas yang umum di Indonesia
2. Identifikasi:
   - Gejala yang bisa dideteksi AI (visual, audio, perilaku)
   - Teknologi yang dibutuhkan
   - Estimasi biaya implementasi
   - Potensi penghematan jika terdeteksi dini
3. Buat presentasi 10 menit
4. Presentasi di Pertemuan 13

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna untuk mempelajari lebih dalam tentang deteksi penyakit dan optimasi pakan berbasis AI.

### Sumber Akademik

| No  | Referensi                                                                                                                                                                               | Keterangan                  |
| --- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------- |
| 1   | Zhuang, X., & Zhang, T. (2019). Detection of sick broilers by digital image processing. _Biosystems Engineering_, 179, 106-116.                                                         | Deteksi penyakit via kamera |
| 2   | Cuan, K., et al. (2020). Detection of avian influenza-infected chickens based on a chicken sound convolutional neural network. _Computers and Electronics in Agriculture_, 178, 105688. | Deteksi via suara           |
| 3   | Neethirajan, S. (2020). The role of sensors, big data and machine learning. _Sensing and Bio-Sensing Research_, 29, 100367.                                                             | Review AI peternakan        |
| 4   | Aviagen. (2022). _Ross 308 Broiler Performance Objectives_.                                                                                                                             | Standar performa            |
| 5   | van der Sluis, W. (2019). Precision feeding: The future of poultry nutrition. _Poultry World_.                                                                                          | Konsep precision feeding    |

### Platform Indonesia

| No  | Referensi                       | Keterangan                     |
| --- | ------------------------------- | ------------------------------ |
| 6   | Chickin Indonesia. _chickin.id_ | Platform monitoring unggas     |
| 7   | FarmIn. _farmin.id_             | Manajemen peternakan           |
| 8   | JALA. _jfrx.co_                 | Presisi akuakultur (referensi) |

---

## 🔗 Koneksi dengan Materi Sebelumnya

```
┌─────────────────────────────────────────────────────────────────┐
│           HUBUNGAN PERTEMUAN 11 DENGAN MATERI SEBELUMNYA       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   Pertemuan 3: SENSOR                                           │
│   ─────────────────────────────────────────────────────────────│
│   • Sensor suhu, kelembaban → Input untuk AI                   │
│   • Sensor gas → Deteksi kualitas udara                        │
│                                                                 │
│   Pertemuan 9: PENGENALAN AI                                    │
│   ─────────────────────────────────────────────────────────────│
│   • Konsep AI dasar                                             │
│   • Jenis-jenis AI                                              │
│                                                                 │
│   Pertemuan 10: MACHINE LEARNING DASAR                          │
│   ─────────────────────────────────────────────────────────────│
│   • Algoritma ML (foundation untuk materi ini)                 │
│   • Analisis produksi                                          │
│                                                                 │
│   👉 Pertemuan 11: APLIKASI SPESIFIK (SEKARANG)                 │
│   ─────────────────────────────────────────────────────────────│
│   • Deteksi penyakit = Computer Vision + ML                    │
│   • Optimasi pakan = Precision Feeding + ML                    │
│                                                                 │
│   Pertemuan 12: SMART POULTRY SYSTEM                            │
│   ─────────────────────────────────────────────────────────────│
│   • Integrasi semua komponen menjadi sistem utuh               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar tentang **Penerapan Smart Poultry System** - melihat bagaimana semua komponen bekerja bersama!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_  
_Semester Genap 2025/2026_
