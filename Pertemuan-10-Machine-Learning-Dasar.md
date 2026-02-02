# 🤖 Pertemuan 10: Machine Learning Dasar dan Analisis Produksi Ternak Unggas Berbasis AI

> **Dosen Pengampu:** Novemia & Karenina  
> **Waktu:** 100 menit  
> **Semester Genap 2025/2026**

---

> 💬 **"Machine Learning mengubah data menjadi pengetahuan, dan pengetahuan menjadi keputusan yang lebih baik!"**

---

## 🎯 Tujuan Pembelajaran

Setelah mengikuti pertemuan ini, mahasiswa diharapkan mampu:

1. ✅ Memahami konsep dasar Machine Learning dengan bahasa sederhana
2. ✅ Mengenal jenis-jenis algoritma Machine Learning yang relevan untuk peternakan
3. ✅ Menganalisis data produksi ternak unggas menggunakan pendekatan ML
4. ✅ Menginterpretasi hasil analisis untuk pengambilan keputusan

---

## 🎬 Cerita Pembuka: Si Peternak yang Bingung dengan Data

### 😵 Dilema Pak Hendra

Pak Hendra punya peternakan ayam broiler dengan 5 kandang. Setelah 1 tahun pakai IoT, dia punya **banyak data**:

| Data yang Dikumpulkan | Jumlah                             |
| --------------------- | ---------------------------------- |
| Data suhu             | 525.600 baris (per menit, 1 tahun) |
| Data kelembaban       | 525.600 baris                      |
| Data konsumsi pakan   | 1.825 baris (per hari)             |
| Data berat ayam       | 7.300 baris (sampling harian)      |
| Data mortalitas       | 1.825 baris                        |
| Data FCR              | 365 baris                          |

> 😰 **Pak Hendra:** "Datanya banyak banget, tapi saya bingung mau ngapain!"
>
> 🤔 "Kenapa ya FCR kandang 3 selalu lebih buruk dari kandang lain?"
>
> 🤔 "Kapan waktu terbaik untuk panen supaya profit maksimal?"
>
> 🤔 "Bisa nggak saya prediksi berapa berat ayam minggu depan?"

### 💡 Solusi: Machine Learning!

Machine Learning bisa **menganalisis semua data** itu dan memberikan **jawaban** yang Pak Hendra butuhkan!

```
┌─────────────────────────────────────────────────────────────────┐
│                                                                 │
│   DATA MENTAH                    MACHINE LEARNING               │
│   (Ribuan angka)      →          (Menganalisis)                │
│                                        ↓                        │
│                              INSIGHT & PREDIKSI                 │
│                              (Jawaban yang berguna)             │
│                                                                 │
│   Contoh Output:                                                │
│   ✓ "FCR kandang 3 buruk karena suhu siang terlalu tinggi"     │
│   ✓ "Waktu panen optimal: hari ke-33 dengan berat 2.1 kg"      │
│   ✓ "Prediksi berat minggu depan: 1.85 kg (±5%)"               │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 1: Apa Itu Machine Learning?

### Definisi Sederhana

> 💡 **Machine Learning (ML)** adalah cabang AI di mana komputer **belajar dari data** untuk membuat keputusan atau prediksi, **tanpa diprogram secara eksplisit** untuk tugas tersebut.

### Analogi yang Mudah Dipahami

**🧒 Seperti Anak Kecil Belajar:**

| Tahap | Anak Belajar Mengenali Ayam     | Machine Learning             |
| ----- | ------------------------------- | ---------------------------- |
| 1     | Ibu tunjukkan foto: "Ini ayam"  | Diberi 1.000 foto ayam       |
| 2     | Anak melihat banyak foto ayam   | ML mempelajari pola          |
| 3     | Anak tahu ciri-ciri ayam        | ML menemukan fitur           |
| 4     | Melihat ayam baru → bisa kenali | Foto baru → bisa klasifikasi |

**Perbedaan dengan Program Biasa:**

```
┌─────────────────────────────────────────────────────────────────┐
│              PROGRAM BIASA vs MACHINE LEARNING                  │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🔧 PROGRAM BIASA (Rule-Based):                               │
│   ─────────────────────────────────────────────────────────────│
│   Programmer menulis aturan satu per satu:                     │
│                                                                 │
│   IF suhu > 32 THEN nyalakan kipas                             │
│   IF berat < 1.5 kg THEN tambah pakan                          │
│   IF mortalitas > 2% THEN kirim alert                          │
│                                                                 │
│   ⚠️ Masalah: Harus tahu semua aturan dari awal!              │
│                                                                 │
│   ════════════════════════════════════════════════════════════  │
│                                                                 │
│   🤖 MACHINE LEARNING:                                         │
│   ─────────────────────────────────────────────────────────────│
│   Diberi DATA, lalu ML menemukan POLA sendiri:                 │
│                                                                 │
│   Berikan: 10.000 data historis                                │
│   ML belajar: "Oh, ternyata kalau suhu 30°C + kelembaban 80%   │
│               + umur ayam 25 hari = FCR cenderung buruk"       │
│                                                                 │
│   ✅ Bisa menemukan pola yang manusia tidak sadari!            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

> 📚 **Catatan Akademis:**  
> Machine Learning didefinisikan oleh Tom Mitchell (1997) sebagai: "Program komputer dikatakan belajar dari pengalaman E berkaitan dengan tugas T dan ukuran kinerja P, jika kinerjanya pada T, yang diukur oleh P, meningkat dengan pengalaman E."

---

## 📖 BAGIAN 2: Jenis-Jenis Machine Learning

### 🎯 Tiga Kategori Utama

```
┌─────────────────────────────────────────────────────────────────┐
│              JENIS-JENIS MACHINE LEARNING                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1️⃣ SUPERVISED LEARNING (Pembelajaran Terawasi)               │
│   ─────────────────────────────────────────────────────────────│
│   • Diberi data + jawaban yang benar (label)                   │
│   • ML belajar dari contoh                                      │
│   • Contoh: Foto ayam + label "sehat/sakit"                    │
│                                                                 │
│   2️⃣ UNSUPERVISED LEARNING (Pembelajaran Tak Terawasi)         │
│   ─────────────────────────────────────────────────────────────│
│   • Diberi data tanpa label                                     │
│   • ML menemukan pola/kelompok sendiri                         │
│   • Contoh: Mengelompokkan ayam berdasarkan perilaku           │
│                                                                 │
│   3️⃣ REINFORCEMENT LEARNING (Pembelajaran Penguatan)           │
│   ─────────────────────────────────────────────────────────────│
│   • ML belajar dari trial & error                              │
│   • Diberi reward jika benar, penalty jika salah               │
│   • Contoh: Robot pemberi pakan belajar timing optimal         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 📊 Untuk Peternakan Unggas, Paling Sering Digunakan:

| Jenis            | Penggunaan di Peternakan | Contoh                                                |
| ---------------- | ------------------------ | ----------------------------------------------------- |
| **Supervised**   | Prediksi produksi        | Input: data historis → Output: prediksi berat         |
| **Supervised**   | Klasifikasi penyakit     | Input: foto ayam → Output: sehat/sakit                |
| **Supervised**   | Prediksi mortalitas      | Input: kondisi kandang → Output: risiko tinggi/rendah |
| **Unsupervised** | Segmentasi performa      | Mengelompokkan kandang berperforma mirip              |
| **Unsupervised** | Anomaly detection        | Mendeteksi data sensor yang aneh                      |

---

## 📖 BAGIAN 3: Algoritma ML untuk Analisis Produksi Unggas

### 🔢 1. Regresi Linier (Linear Regression)

**Fungsi:** Memprediksi nilai numerik (angka kontinu)

```
┌─────────────────────────────────────────────────────────────────┐
│              REGRESI LINIER - PREDIKSI BERAT AYAM              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   CONTOH KASUS:                                                 │
│   Memprediksi berat ayam di hari ke-35 berdasarkan:            │
│   • Berat saat ini                                              │
│   • Konsumsi pakan                                              │
│   • Suhu rata-rata                                              │
│   • FCR sementara                                               │
│                                                                 │
│   VISUALISASI:                                                  │
│                                                                 │
│   Berat (kg)                                                    │
│     2.5│                              ╭─────● Prediksi          │
│     2.0│                    ╭─────────╯                         │
│     1.5│           ╭────────╯                                   │
│     1.0│     ╭─────╯                                            │
│     0.5│╭────╯                                                  │
│     0.0│────────────────────────────────────                    │
│        0    7    14   21   28   35 (Hari)                       │
│                                                                 │
│   OUTPUT: "Prediksi berat hari ke-35: 2.15 kg"                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Kegunaan Praktis:**

- 📈 Prediksi berat panen
- 📊 Estimasi kebutuhan pakan total
- 💰 Prediksi pendapatan

---

### 🌳 2. Decision Tree (Pohon Keputusan)

**Fungsi:** Klasifikasi atau prediksi dengan logika if-then yang mudah dipahami

```
┌─────────────────────────────────────────────────────────────────┐
│              DECISION TREE - PREDIKSI RISIKO MORTALITAS        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   Contoh pohon keputusan yang dihasilkan ML:                   │
│                                                                 │
│                    [Suhu > 32°C?]                               │
│                    /           \                                │
│                  Ya             Tidak                           │
│                  /                 \                            │
│        [Kelembaban > 80%?]    [Umur < 7 hari?]                 │
│         /          \              /        \                   │
│       Ya          Tidak         Ya        Tidak                │
│       /              \           /            \                │
│   🔴 RISIKO      [Ventilasi?]  🟡 WASPADA   🟢 AMAN           │
│      TINGGI      /      \                                      │
│              Baik     Buruk                                    │
│               /          \                                      │
│          🟡 WASPADA   🔴 RISIKO                                │
│                       TINGGI                                   │
│                                                                 │
│   💡 Kelebihan: Mudah dipahami, bisa dijelaskan ke peternak   │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

**Kegunaan Praktis:**

- 🚨 Early warning system
- 📋 SOP berbasis data
- 👨‍🏫 Edukasi pekerja kandang

---

### 🌲 3. Random Forest

**Fungsi:** Gabungan banyak Decision Tree untuk hasil lebih akurat

```
┌─────────────────────────────────────────────────────────────────┐
│              RANDOM FOREST = BANYAK POHON KEPUTUSAN            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ANALOGI:                                                      │
│   ─────────────────────────────────────────────────────────────│
│   Seperti meminta pendapat 100 ahli, lalu ambil suara terbanyak│
│                                                                 │
│   🌳 Pohon 1: "Risiko TINGGI"                                  │
│   🌳 Pohon 2: "Risiko SEDANG"                                  │
│   🌳 Pohon 3: "Risiko TINGGI"                                  │
│   ...                                                           │
│   🌳 Pohon 100: "Risiko TINGGI"                                │
│                                                                 │
│   📊 Voting: 72 pohon bilang TINGGI, 28 bilang SEDANG          │
│   ✅ Keputusan final: RISIKO TINGGI (72% confidence)           │
│                                                                 │
│   💡 Lebih akurat karena mengurangi error individual           │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📈 4. K-Nearest Neighbors (KNN)

**Fungsi:** Klasifikasi berdasarkan "tetangga terdekat"

```
┌─────────────────────────────────────────────────────────────────┐
│              KNN - KLASIFIKASI PERFORMA KANDANG                 │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   ANALOGI SEDERHANA:                                            │
│   ─────────────────────────────────────────────────────────────│
│   "Katakan siapa temanmu, dan aku akan bilang siapa kamu"      │
│                                                                 │
│   FCR                                                           │
│   1.9│    ❌ Buruk    ❌ Buruk                                  │
│   1.8│        ❌ Buruk                                          │
│   1.7│    ⭐ Baik   ❓ Baru      ← Kandang baru, performa?      │
│   1.6│    ⭐ Baik    ⭐ Baik                                    │
│   1.5│        ⭐ Baik                                           │
│      └────────────────────────────────                          │
│        1.8   1.9   2.0   2.1   2.2  Berat Panen (kg)           │
│                                                                 │
│   KNN melihat 3 tetangga terdekat:                             │
│   - 2 tetangga = ⭐ Baik                                       │
│   - 1 tetangga = ❌ Buruk                                      │
│   ✅ Kesimpulan: Kandang baru = Performa BAIK                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 4: Studi Kasus Analisis Produksi Unggas

### 📊 Kasus 1: Prediksi Berat Panen

**Masalah:** Pak Hendra ingin tahu berapa berat ayam di hari panen (hari ke-33)

**Data yang Dimiliki:**

| Variabel Input           | Contoh Data |
| ------------------------ | ----------- |
| Berat umur 7 hari        | 180 gram    |
| Berat umur 14 hari       | 520 gram    |
| Berat umur 21 hari       | 1.050 gram  |
| Konsumsi pakan kumulatif | 2.400 gram  |
| Suhu rata-rata           | 28°C        |
| FCR sementara            | 1.55        |

**Proses Machine Learning:**

```
┌─────────────────────────────────────────────────────────────────┐
│              PROSES ML PREDIKSI BERAT PANEN                    │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   1️⃣ PENGUMPULAN DATA HISTORIS                                 │
│      • 20 siklus pemeliharaan sebelumnya                       │
│      • Total: 100.000 data individual                          │
│                                                                 │
│   2️⃣ PREPROCESSING (PERSIAPAN)                                 │
│      • Bersihkan data yang salah/hilang                        │
│      • Normalisasi (samakan skala)                             │
│                                                                 │
│   3️⃣ TRAINING (PELATIHAN)                                      │
│      • 80% data untuk training                                  │
│      • ML mempelajari pola                                      │
│                                                                 │
│   4️⃣ TESTING (PENGUJIAN)                                       │
│      • 20% data untuk uji akurasi                              │
│      • Bandingkan prediksi vs realita                          │
│                                                                 │
│   5️⃣ DEPLOYMENT (PENERAPAN)                                    │
│      • Model siap digunakan                                     │
│      • Input data baru → prediksi keluar                       │
│                                                                 │
│   📊 HASIL:                                                     │
│   • Akurasi: 94%                                                │
│   • Error rata-rata: ±80 gram                                  │
│   • Prediksi hari ke-33: 2.150 gram                            │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📊 Kasus 2: Analisis Faktor yang Mempengaruhi FCR

**Masalah:** Mengapa FCR berbeda antar kandang? Faktor apa yang paling berpengaruh?

**Hasil Analisis ML (Feature Importance):**

| Peringkat | Faktor                    | Pengaruh |
| --------- | ------------------------- | -------- |
| 1         | 🌡️ Suhu rata-rata         | 28%      |
| 2         | 💧 Kelembaban             | 22%      |
| 3         | 🍽️ Jadwal pemberian pakan | 18%      |
| 4         | 💨 Kadar amonia           | 15%      |
| 5         | 👶 Kualitas DOC           | 12%      |
| 6         | 🧪 Formula pakan          | 5%       |

**Insight yang Didapat:**

```
┌─────────────────────────────────────────────────────────────────┐
│              INSIGHT DARI ANALISIS ML                           │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   🔍 TEMUAN UTAMA:                                              │
│   ─────────────────────────────────────────────────────────────│
│                                                                 │
│   1. Suhu + Kelembaban = 50% pengaruh                          │
│      → PRIORITAS: Perbaiki sistem climate control              │
│                                                                 │
│   2. Kandang 3 (FCR buruk) ternyata:                           │
│      • Suhu siang rata-rata 33°C (2°C lebih tinggi)           │
│      • Ventilasi kurang optimal                                 │
│      • SOLUSI: Tambah 2 exhaust fan                            │
│                                                                 │
│   3. Jadwal pakan pagi vs sore berbeda dampaknya:              │
│      • Pakan pagi lebih besar → FCR lebih baik                 │
│      • Rekomendasi: 60% pagi, 40% sore                         │
│                                                                 │
│   4. Amonia > 20 ppm berkorelasi kuat dengan FCR buruk         │
│      → Tingkatkan frekuensi ganti litter                       │
│                                                                 │
│   💡 ML menemukan pola yang tidak disadari Pak Hendra!         │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📊 Kasus 3: Prediksi Mortalitas Mingguan

**Model:** Random Forest Classifier

**Input:**

| Variabel                   | Minggu Ini |
| -------------------------- | ---------- |
| Suhu maksimum              | 34°C       |
| Kelembaban rata-rata       | 78%        |
| Konsumsi pakan vs target   | -12%       |
| Konsumsi air vs target     | +5%        |
| Mortalitas 3 hari terakhir | 0.3%       |
| Umur ayam                  | 24 hari    |

**Output ML:**

```
┌─────────────────────────────────────────────────────────────────┐
│              PREDIKSI MORTALITAS                                │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   📊 HASIL PREDIKSI:                                            │
│                                                                 │
│   Risiko Mortalitas Minggu Ini: 🔴 TINGGI (78% confidence)     │
│                                                                 │
│   Prediksi Jumlah: 45-60 ekor dari 5.000                       │
│   (Biasanya: 15-25 ekor)                                        │
│                                                                 │
│   ⚠️ FAKTOR RISIKO UTAMA:                                      │
│   1. Suhu maksimum 34°C (di atas ambang batas)                 │
│   2. Konsumsi pakan turun 12% (tanda stress)                   │
│   3. Kelembaban tinggi memperparah heat stress                 │
│                                                                 │
│   📋 REKOMENDASI AKSI:                                          │
│   ✓ Nyalakan cooling pad siang hari                            │
│   ✓ Tambah vitamin anti-stress di air minum                    │
│   ✓ Kurangi kepadatan jika memungkinkan                        │
│   ✓ Siapkan pekerja untuk monitoring intensif                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📖 BAGIAN 5: Langkah Memulai Analisis Data dengan ML

### 🚀 Panduan untuk Peternak

```
┌─────────────────────────────────────────────────────────────────┐
│        LANGKAH MEMULAI MACHINE LEARNING DI PETERNAKAN          │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   LEVEL 1: PEMULA (Bisa mulai sekarang!)                       │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Catat data harian di Excel/Google Sheets                  │
│   ✓ Minimal: suhu, pakan, berat sampel, mortalitas            │
│   ✓ Konsisten mencatat setiap hari                             │
│   ✓ Gunakan fitur chart di Excel untuk melihat tren           │
│                                                                 │
│   LEVEL 2: MENENGAH (Butuh bantuan IT)                         │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Gunakan platform IoT yang sudah ada fitur analisis        │
│   ✓ Contoh: Chickin, eFishery - sudah ada prediksi bawaan     │
│   ✓ Cukup lihat hasil, tidak perlu buat model sendiri         │
│                                                                 │
│   LEVEL 3: LANJUTAN (Butuh ahli data)                          │
│   ─────────────────────────────────────────────────────────────│
│   ✓ Custom ML model sesuai kebutuhan                           │
│   ✓ Tools: Python, R, atau AutoML                              │
│   ✓ Bisa kolaborasi dengan kampus/konsultan                   │
│                                                                 │
│   💡 TIPS: Mulai dari Level 1, naik bertahap!                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

### 📋 Variabel Penting untuk Direkam

| Kategori       | Variabel       | Frekuensi   | Alat Ukur             |
| -------------- | -------------- | ----------- | --------------------- |
| **Lingkungan** | Suhu           | Setiap jam  | Sensor DHT22          |
|                | Kelembaban     | Setiap jam  | Sensor DHT22          |
|                | Amonia         | 2x sehari   | Sensor MQ-135         |
| **Produksi**   | Berat sampel   | Harian      | Timbangan digital     |
|                | Konsumsi pakan | Harian      | Catatan manual/sensor |
|                | Konsumsi air   | Harian      | Flow meter            |
|                | Mortalitas     | Harian      | Catatan manual        |
| **Output**     | FCR            | Per periode | Hitung dari data      |
|                | Berat panen    | Saat panen  | Timbangan             |

---

## 📖 BAGIAN 6: Metrik Analisis Produksi Unggas

### 📐 Indikator Performa Kunci (KPI) yang Dianalisis ML

| KPI                     | Rumus                                           | Target Ideal | Dianalisis Untuk |
| ----------------------- | ----------------------------------------------- | ------------ | ---------------- |
| **FCR**                 | Total Pakan ÷ Total Berat                       | 1.5 - 1.7    | Efisiensi pakan  |
| **ADG**                 | (Berat Akhir - Berat Awal) ÷ Hari               | 55-65 g/hari | Pertumbuhan      |
| **Mortalitas**          | (Jumlah Mati ÷ Populasi) × 100%                 | < 4%         | Kesehatan        |
| **IP (Index Performa)** | (100 - Mortalitas) × Berat × 100 ÷ (Umur × FCR) | > 350        | Performa overall |
| **Deplesi**             | (DOC Masuk - Panen) ÷ DOC Masuk × 100%          | < 5%         | Total losses     |

### 📊 Contoh Perhitungan dengan ML

```
┌─────────────────────────────────────────────────────────────────┐
│              CONTOH: PREDIKSI FCR AKHIR                        │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   DATA SAAT INI (Hari ke-21):                                   │
│   • Berat rata-rata: 850 gram                                   │
│   • Total pakan dikonsumsi: 1.450 gram/ekor                    │
│   • FCR sementara: 1.450 ÷ 850 = 1.71                          │
│                                                                 │
│   ML MEMPREDIKSI (Hari ke-35):                                  │
│   ─────────────────────────────────────────────────────────────│
│   Berdasarkan 50 siklus data historis dengan kondisi serupa:   │
│                                                                 │
│   • Prediksi berat panen: 2.150 gram                           │
│   • Prediksi total pakan: 3.440 gram                           │
│   • Prediksi FCR akhir: 3.440 ÷ 2.150 = 1.60                   │
│                                                                 │
│   ✅ INSIGHT: FCR akan membaik dari 1.71 ke 1.60               │
│      karena fase finisher lebih efisien                        │
│                                                                 │
│   📋 REKOMENDASI ML:                                            │
│   • Pertahankan suhu 26-28°C                                   │
│   • Jangan kurangi pakan (ayam butuh untuk growth)             │
│   • Hasil: FCR target 1.55-1.60 bisa tercapai                  │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

### 📈 Analisis Tren Produksi Antar Siklus

| Siklus | FCR  | Mortalitas | Berat Panen | IP  | Analisis ML           |
| ------ | ---- | ---------- | ----------- | --- | --------------------- |
| 1      | 1.72 | 4.8%       | 2.05 kg     | 298 | Baseline              |
| 2      | 1.68 | 4.2%       | 2.10 kg     | 320 | Suhu lebih stabil     |
| 3      | 1.75 | 5.5%       | 2.00 kg     | 280 | 🔴 Masalah ventilasi  |
| 4      | 1.62 | 3.8%       | 2.18 kg     | 355 | ✅ Perbaikan berhasil |
| 5      | 1.58 | 3.5%       | 2.22 kg     | 375 | ✅ Konsisten baik     |

> 💡 **ML menemukan:** Siklus 3 bermasalah karena ada kombinasi suhu tinggi + kelembaban tinggi di minggu ke-3. Perbaikan ventilasi di siklus 4 langsung terlihat hasilnya!

## 📊 Ringkasan Pertemuan 10

| Topik                     | Poin Penting                                                         |
| ------------------------- | -------------------------------------------------------------------- |
| **Apa itu ML?**           | Komputer belajar dari data untuk membuat prediksi                    |
| **Jenis ML**              | Supervised (dengan label), Unsupervised (tanpa label), Reinforcement |
| **Algoritma Populer**     | Regresi Linier, Decision Tree, Random Forest, KNN                    |
| **Kegunaan untuk Unggas** | Prediksi berat, analisis FCR, deteksi risiko mortalitas              |
| **Cara Memulai**          | Catat data konsisten, gunakan platform yang ada, naik level bertahap |
| **Feature Importance**    | ML bisa menentukan faktor mana yang paling berpengaruh               |
| **Pesan Utama**           | Data + ML = Insight yang tidak terlihat oleh mata manusia            |

---

## ❓ Pertanyaan Diskusi

1. **Dari kasus Pak Hendra, insight mana yang paling mengejutkan Anda? Mengapa ML bisa menemukan hal itu sementara peternak tidak?**

2. **Menurut Anda, variabel apa lagi yang mungkin penting untuk dicatat tapi belum disebutkan?**

3. **Jika Anda punya data 10 siklus pemeliharaan, analisis apa yang pertama kali ingin Anda lakukan?**

4. **Apa hambatan terbesar peternak Indonesia untuk menerapkan analisis data berbasis ML?**

---

## 📚 Istilah Penting Pertemuan Ini

| Istilah                   | Arti Sederhana                           |
| ------------------------- | ---------------------------------------- |
| **Machine Learning**      | Komputer belajar dari data               |
| **Supervised Learning**   | Belajar dengan contoh + jawaban          |
| **Unsupervised Learning** | Belajar tanpa jawaban, cari pola sendiri |
| **Training**              | Proses mengajari model dengan data       |
| **Testing**               | Menguji akurasi model                    |
| **Feature**               | Variabel input (suhu, kelembaban, dll)   |
| **Label**                 | Jawaban yang benar (sehat/sakit, berat)  |
| **Prediction**            | Hasil tebakan model                      |
| **Accuracy**              | Seberapa sering prediksi benar           |
| **Feature Importance**    | Seberapa penting tiap variabel           |

---

## 🎯 Tugas Pertemuan 10

### Tugas Individu

**Analisis Data Sederhana:**

1. Download dataset contoh yang diberikan (Excel)
2. Buat minimal 3 grafik untuk melihat pola
3. Tuliskan 3 insight/temuan dari grafik tersebut
4. Jika Anda adalah peternak, keputusan apa yang akan diambil berdasarkan insight tersebut?

**Format:** Laporan 2-3 halaman dengan grafik

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna jika Anda ingin mempelajari lebih dalam tentang Machine Learning untuk peternakan.

### Sumber Akademik

| No  | Referensi                                                                                                                                                    | Keterangan          |
| --- | ------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------- |
| 1   | Mitchell, T. (1997). _Machine Learning_. McGraw-Hill.                                                                                                        | Definisi klasik ML  |
| 2   | Liakos, K. G., et al. (2018). Machine learning in agriculture: A review. _Sensors_, 18(8), 2674.                                                             | Review ML pertanian |
| 3   | Morota, G., et al. (2018). Big data analytics and precision animal agriculture symposium. _Journal of Animal Science_, 96(4), 1540-1550.                     | ML di peternakan    |
| 4   | Neethirajan, S. (2020). The role of sensors, big data and machine learning in modern animal farming. _Sensing and Bio-Sensing Research_, 29, 100367.         | Sensor dan ML       |
| 5   | Bahlo, C., et al. (2019). The role of interoperable data standards in precision livestock farming. _Computers and Electronics in Agriculture_, 156, 459-466. | Standar data        |

### Tools dan Platform

| No  | Referensi                                  | Keterangan              |
| --- | ------------------------------------------ | ----------------------- |
| 6   | Google AutoML. _cloud.google.com/automl_   | ML tanpa coding         |
| 7   | Orange Data Mining. _orangedatamining.com_ | Visual ML untuk pemula  |
| 8   | Chickin Indonesia. _chickin.id_            | Platform analisis ayam  |
| 9   | Scikit-learn. _scikit-learn.org_           | Library Python untuk ML |
| 10  | Kaggle. _kaggle.com_                       | Dataset dan kompetisi   |

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar tentang **Deteksi Penyakit dan Optimasi Pakan pada Ternak Unggas Berbasis AI** - aplikasi ML yang lebih spesifik!

---

## 🔗 Koneksi dengan Materi Sebelumnya

```
┌─────────────────────────────────────────────────────────────────┐
│           HUBUNGAN PERTEMUAN 10 DENGAN MATERI SEBELUMNYA       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│   Pertemuan 1-7: FONDASI IoT                                    │
│   ─────────────────────────────────────────────────────────────│
│   • Sensor mengumpulkan DATA                                    │
│   • Gateway mengirimkan DATA                                    │
│   • Cloud menyimpan DATA                                        │
│   • Dashboard menampilkan DATA                                  │
│                                                                 │
│   Pertemuan 9: PENGENALAN AI                                    │
│   ─────────────────────────────────────────────────────────────│
│   • AI = mesin yang bisa berpikir                              │
│   • Jenis-jenis AI untuk peternakan                            │
│   • Contoh aplikasi AI                                          │
│                                                                 │
│   👉 Pertemuan 10: MACHINE LEARNING (SEKARANG)                  │
│   ─────────────────────────────────────────────────────────────│
│   • ML = bagian dari AI yang BELAJAR dari DATA                 │
│   • Menganalisis DATA dari IoT                                  │
│   • Menghasilkan PREDIKSI dan INSIGHT                          │
│                                                                 │
│   Pertemuan 11: APLIKASI ML SPESIFIK                            │
│   ─────────────────────────────────────────────────────────────│
│   • Deteksi penyakit dengan ML                                  │
│   • Optimasi pakan dengan ML                                    │
│                                                                 │
│   💡 ALUR: IoT → Data → ML → Insight → Keputusan Lebih Baik    │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_  
_Semester Genap 2025/2026_
