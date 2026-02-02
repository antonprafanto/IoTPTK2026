# 🌡️ Pertemuan 3: Sensor Lingkungan Kandang

> **"Kandang yang sehat dimulai dari lingkungan yang terpantau dengan baik!"**

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Memahami jenis-jenis sensor lingkungan untuk peternakan
2. Mengetahui cara kerja sensor suhu, kelembaban, gas, berat, dan pH
3. Mengaplikasikan pengetahuan sensor untuk monitoring kandang

---

## 📖 Mengapa Sensor Lingkungan Penting?

### Masalah Tanpa Sensor

❌ **Skenario Buruk Tanpa Monitoring:**

```
┌─────────────────────────────────────────────────────────────┐
│  🌙 Jam 2 malam...                                          │
│                                                             │
│  🔥 Suhu kandang naik drastis karena kipas mati            │
│  🐔 Ayam-ayam mulai stres dan berhenti makan               │
│  😴 Peternak sedang tidur, tidak menyadari                 │
│  ☀️ Pagi hari: ditemukan banyak ayam yang mati             │
│                                                             │
│  💸 Kerugian: BESAR!                                        │
└─────────────────────────────────────────────────────────────┘
```

✅ **Skenario Baik Dengan Sensor:**

```
┌─────────────────────────────────────────────────────────────┐
│  🌙 Jam 2 malam...                                          │
│                                                             │
│  🔥 Suhu kandang naik karena kipas mati                    │
│  🌡️ Sensor mendeteksi suhu > 32°C                          │
│  📱 Notifikasi langsung ke HP peternak                     │
│  🏃 Peternak bangun dan menyalakan kipas cadangan          │
│  ☀️ Pagi hari: semua ayam selamat!                         │
│                                                             │
│  💰 Kerugian: MINIMAL                                       │
└─────────────────────────────────────────────────────────────┘
```

---

## 1️⃣ SENSOR SUHU (Temperature Sensor)

### 🌡️ Apa itu Sensor Suhu?

Sensor suhu adalah alat yang **mengukur temperatur/panas** di sekitarnya dan mengubahnya menjadi data angka yang bisa dibaca.

### Jenis Sensor Suhu Populer

| Nama Sensor | Gambar   | Keunggulan              | Harga     |
| ----------- | -------- | ----------------------- | --------- |
| **DHT11**   | 🔵 Biru  | Murah, mudah digunakan  | Rp 15.000 |
| **DHT22**   | ⚪ Putih | Lebih akurat dari DHT11 | Rp 35.000 |
| **DS18B20** | ⬛ Kecil | Tahan air, bisa banyak  | Rp 20.000 |
| **BMP280**  | 🟣 Ungu  | + Tekanan udara         | Rp 25.000 |

### Cara Kerja Sederhana

```
┌─────────────────────────────────────────────────────────────┐
│                   CARA KERJA SENSOR SUHU                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   1. Sensor merasakan suhu udara di sekitarnya             │
│                     ↓                                       │
│   2. Mengubah suhu menjadi sinyal listrik                  │
│                     ↓                                       │
│   3. Sinyal dikirim ke mikrokontroler (Arduino/ESP32)      │
│                     ↓                                       │
│   4. Ditampilkan sebagai angka: "Suhu: 28°C"               │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 🐔 Suhu Ideal untuk Ternak

> 📚 **Catatan Akademis:**  
> Standar suhu ideal di bawah ini berdasarkan pedoman dari berbagai sumber termasuk _Poultry Science_ journal dan panduan FAO. Untuk ayam broiler, Aviagen (2018) merekomendasikan suhu yang menurun bertahap dari 32-33°C (DOC) hingga 20°C (panen).

| Jenis Ternak            | Suhu Ideal | Suhu Bahaya |
| ----------------------- | ---------- | ----------- |
| **Ayam Broiler**        | 21-27°C    | > 35°C      |
| **Ayam Layer**          | 18-24°C    | > 32°C      |
| **DOC (Day Old Chick)** | 32-35°C    | < 28°C      |
| **Sapi Perah**          | 13-18°C    | > 27°C      |
| **Babi**                | 15-20°C    | > 30°C      |
| **Kambing**             | 20-30°C    | > 38°C      |

### Contoh Penempatan Sensor

```
        ┌────────────────────────────────────────┐
        │           KANDANG AYAM                 │
        │                                        │
        │   🌡️←─── Sensor 1 (Atas)              │
        │         Mengukur suhu atas             │
        │                                        │
        │      🐔  🐔  🐔  🐔  🐔               │
        │                                        │
        │   🌡️←─── Sensor 2 (Tengah)            │
        │         Mengukur suhu di level ayam    │
        │                                        │
        │   🌡️←─── Sensor 3 (Bawah)             │
        │         Mengukur suhu dekat lantai     │
        │                                        │
        └────────────────────────────────────────┘

   💡 Tips: Pasang minimal 3 sensor untuk kandang besar
      agar mendapat gambaran suhu yang akurat!
```

---

## 2️⃣ SENSOR KELEMBABAN (Humidity Sensor)

### 💧 Apa itu Sensor Kelembaban?

Sensor kelembaban mengukur **kadar uap air di udara**. Biasanya dinyatakan dalam persentase (%), disebut juga **RH (Relative Humidity)**.

### Mengapa Kelembaban Penting?

```
┌─────────────────────────────────────────────────────────────┐
│                DAMPAK KELEMBABAN                            │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  💧 TERLALU LEMBAB (>80%):                                 │
│     • Bakteri dan jamur mudah berkembang                   │
│     • Penyakit pernapasan meningkat                        │
│     • Litter (alas kandang) basah dan berbau               │
│     • Amonia meningkat                                     │
│                                                             │
│  🏜️ TERLALU KERING (<40%):                                 │
│     • Debu beterbangan                                     │
│     • Iritasi saluran pernapasan                           │
│     • Ternak mudah dehidrasi                               │
│     • Kulit dan bulu kering                                │
│                                                             │
│  ✅ IDEAL (50-70%):                                         │
│     • Ternak nyaman                                        │
│     • Penyakit minimal                                     │
│     • Produktivitas optimal                                │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Sensor Kelembaban Populer

> 💡 **Kabar Baik!** Sensor DHT11 dan DHT22 bisa mengukur **suhu DAN kelembaban sekaligus** dalam satu alat!

| Sensor     | Mengukur                    | Akurasi Kelembaban |
| ---------- | --------------------------- | ------------------ |
| **DHT11**  | Suhu + Kelembaban           | ±5%                |
| **DHT22**  | Suhu + Kelembaban           | ±2-5%              |
| **BME280** | Suhu + Kelembaban + Tekanan | ±3%                |

### Kelembaban Ideal untuk Ternak

| Jenis Ternak   | Kelembaban Ideal |
| -------------- | ---------------- |
| **Ayam**       | 50-70%           |
| **Sapi Perah** | 50-80%           |
| **Babi**       | 60-70%           |
| **Kambing**    | 60-80%           |

---

## 3️⃣ SENSOR GAS (Gas Sensor)

### 💨 Mengapa Perlu Monitoring Gas?

Di kandang tertutup, berbagai gas berbahaya bisa menumpuk:

```
┌─────────────────────────────────────────────────────────────┐
│              GAS-GAS BERBAHAYA DI KANDANG                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🔹 AMONIA (NH3) - Bau pesing/kencing                      │
│     Sumber: Kotoran ternak + litter basah                  │
│     Bahaya: Kerusakan saluran napas, iritasi mata          │
│     Batas aman: < 25 ppm                                   │
│                                                             │
│  🔹 KARBON DIOKSIDA (CO2) - Tidak berbau                   │
│     Sumber: Pernapasan ternak                              │
│     Bahaya: Sesak napas, lemas                             │
│     Batas aman: < 3000 ppm                                 │
│                                                             │
│  🔹 HIDROGEN SULFIDA (H2S) - Bau telur busuk               │
│     Sumber: Pembusukan kotoran                             │
│     Bahaya: Sangat beracun!                                │
│     Batas aman: < 10 ppm                                   │
│                                                             │
│  🔹 METANA (CH4) - Tidak berbau                            │
│     Sumber: Pencernaan ternak (sendawa sapi/kambing)       │
│     Bahaya: Mudah terbakar                                 │
│     Batas aman: < 500 ppm                                  │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

> 💡 **Tahukah Anda?**  
> Batas aman amonia (<25 ppm) ditetapkan berdasarkan penelitian kesehatan unggas oleh Kristensen & Wathes (2000). Paparan amonia tinggi dalam jangka panjang dapat menurunkan pertumbuhan ayam hingga 20% (Miles et al., 2004).

### Jenis Sensor Gas

| Sensor     | Mendeteksi           | Penggunaan             |
| ---------- | -------------------- | ---------------------- |
| **MQ-135** | Amonia, CO2, Alkohol | Kualitas udara umum    |
| **MQ-137** | Amonia (khusus)      | Deteksi amonia kandang |
| **MQ-4**   | Metana               | Deteksi gas metana     |
| **MQ-136** | Hidrogen Sulfida     | Deteksi H2S            |

### Cara Baca Hasil Sensor Gas

```
┌─────────────────────────────────────────────────────────────┐
│              INDIKATOR KUALITAS UDARA                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🟢 HIJAU (0-25 ppm Amonia)                               │
│      Status: AMAN                                          │
│      Aksi: Tidak perlu tindakan                            │
│                                                             │
│   🟡 KUNING (25-50 ppm Amonia)                             │
│      Status: WASPADA                                       │
│      Aksi: Tingkatkan ventilasi                            │
│                                                             │
│   🟠 ORANGE (50-75 ppm Amonia)                             │
│      Status: BAHAYA                                        │
│      Aksi: Buka semua ventilasi, ganti litter              │
│                                                             │
│   🔴 MERAH (>75 ppm Amonia)                                │
│      Status: DARURAT!                                      │
│      Aksi: Evakuasi jika memungkinkan, bersihkan kandang   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Tips Mengurangi Gas Berbahaya

1. **Ventilasi yang baik** - Pastikan udara mengalir
2. **Jaga litter tetap kering** - Litter basah = lebih banyak amonia
3. **Bersihkan kotoran rutin** - Jangan biarkan menumpuk
4. **Kepadatan kandang sesuai** - Jangan terlalu padat

---

## 4️⃣ SENSOR BERAT (Weight/Load Cell Sensor)

### ⚖️ Mengapa Perlu Menimbang Otomatis?

```
┌─────────────────────────────────────────────────────────────┐
│           MANFAAT PENIMBANGAN OTOMATIS                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  📊 MONITORING PERTUMBUHAN                                  │
│     • Apakah ternak tumbuh sesuai target?                  │
│     • Deteksi dini jika ada yang sakit (BB turun)          │
│                                                             │
│  🍽️ EFISIENSI PAKAN                                        │
│     • Hitung FCR (Feed Conversion Ratio)                   │
│     • Optimalkan jumlah pakan                               │
│                                                             │
│  💰 PREDIKSI PANEN                                          │
│     • Kapan waktu panen yang tepat?                        │
│     • Estimasi pendapatan                                  │
│                                                             │
│  📉 DETEKSI MASALAH                                         │
│     • Berat turun = ada masalah kesehatan                  │
│     • Berat stagnan = perlu evaluasi pakan                 │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Jenis Sensor Berat

| Sensor              | Kapasitas | Kegunaan              |
| ------------------- | --------- | --------------------- |
| **Load Cell 1kg**   | 0-1 kg    | Timbang DOC, burung   |
| **Load Cell 5kg**   | 0-5 kg    | Timbang ayam          |
| **Load Cell 50kg**  | 0-50 kg   | Timbang kambing/domba |
| **Load Cell 500kg** | 0-500 kg  | Timbang sapi          |

### Sistem Penimbangan Otomatis

```
┌─────────────────────────────────────────────────────────────┐
│           SISTEM TIMBANG OTOMATIS AYAM                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│                     ┌─────────┐                             │
│                     │  Papan  │  ← Ayam naik ke sini       │
│                     │ Timbang │                             │
│                     └────┬────┘                             │
│                          │                                  │
│                     ┌────┴────┐                             │
│                     │  Load   │  ← Sensor berat             │
│                     │  Cell   │                             │
│                     └────┬────┘                             │
│                          │                                  │
│                     ┌────┴────┐                             │
│                     │ HX711   │  ← Penguat sinyal           │
│                     │ Module  │                             │
│                     └────┬────┘                             │
│                          │                                  │
│                     ┌────┴────┐                             │
│                     │ ESP32/  │  ← Kirim ke Cloud           │
│                     │ Arduino │                             │
│                     └─────────┘                             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Contoh Data Pertumbuhan

```
┌─────────────────────────────────────────────────────────────┐
│              GRAFIK PERTUMBUHAN AYAM BROILER                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Berat (gram)                                               │
│  2500 │                                          ●──●       │
│       │                                    ●────●           │
│  2000 │                              ●────●                 │
│       │                        ●────●                       │
│  1500 │                  ●────●                             │
│       │            ●────●                                   │
│  1000 │      ●────●                                         │
│       │  ●──●                                               │
│   500 │●                                                    │
│       │                                                     │
│     0 └─────────────────────────────────────────────────    │
│         1   5   10   15   20   25   30   35 hari            │
│                                                             │
│  ✅ Pertumbuhan normal: naik konsisten                      │
│  ⚠️ Waspada jika: garis mendatar atau turun                 │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 5️⃣ SENSOR pH (Keasaman)

### 🧪 Apa itu pH?

pH adalah ukuran **tingkat keasaman atau kebasaan** suatu cairan.

```
┌─────────────────────────────────────────────────────────────┐
│                     SKALA pH                                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  0    1    2    3    4    5    6    7    8    9   10  11  12│
│  │────│────│────│────│────│────│────│────│────│────│────│───│
│  ←───── ASAM ─────→  NETRAL  ←───── BASA ─────→             │
│                                                             │
│  🍋 Jeruk     🥛 Susu   💧Air    🧼 Sabun   🧹 Pemutih      │
│  pH 2-3      pH 6.5    pH 7     pH 9-10    pH 12           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Penggunaan Sensor pH di Peternakan

| Penggunaan           | pH Ideal | Mengapa Penting                              |
| -------------------- | -------- | -------------------------------------------- |
| **Air Minum Ternak** | 6.5-8.5  | Air terlalu asam/basa = pencernaan terganggu |
| **Susu Sapi**        | 6.6-6.8  | pH berubah = tanda mastitis (radang ambing)  |
| **Kolam Ikan**       | 6.5-8.0  | pH tidak stabil = ikan stres/mati            |
| **Silase**           | 4.0-4.5  | pH rendah = fermentasi baik                  |

### Jenis Sensor pH

| Sensor               | Keunggulan          | Harga              |
| -------------------- | ------------------- | ------------------ |
| **pH Meter Probe**   | Akurat              | Rp 100.000-500.000 |
| **pH Sensor Module** | Bisa IoT            | Rp 80.000-150.000  |
| **Kertas pH**        | Murah, sekali pakai | Rp 20.000/pack     |

### Cara Kerja Sensor pH

```
┌─────────────────────────────────────────────────────────────┐
│                   CARA KERJA SENSOR pH                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   1. Probe dicelupkan ke dalam cairan                      │
│                     ↓                                       │
│   2. Sensor mendeteksi ion hidrogen (H+)                   │
│                     ↓                                       │
│   3. Mengubah deteksi menjadi sinyal listrik               │
│                     ↓                                       │
│   4. Sinyal dikonversi menjadi nilai pH (0-14)             │
│                     ↓                                       │
│   5. Ditampilkan: "pH Air: 7.2 (NORMAL)"                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### ⚠️ Tips Perawatan Sensor pH

1. **Kalibrasi rutin** - Minimal 1x seminggu
2. **Simpan dalam larutan** - Jangan biarkan kering
3. **Bersihkan setelah pakai** - Bilas dengan air bersih
4. **Hindari sentuh probe** - Minyak tangan merusak sensor

---

## 🔄 Integrasi: Sistem Multi-Sensor

### Contoh Sistem Lengkap di Kandang

```
┌─────────────────────────────────────────────────────────────┐
│               SISTEM MONITORING KANDANG LENGKAP             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   ┌─────────────────────────────────────────────────────┐   │
│   │                   KANDANG                           │   │
│   │                                                     │   │
│   │    🌡️ DHT22        💨 MQ-135       ⚖️ Load Cell    │   │
│   │    Suhu: 28°C      Gas: Aman       Berat: 2.1kg    │   │
│   │    RH: 65%                                          │   │
│   │                                                     │   │
│   │    💧 Tangki Air                                    │   │
│   │    pH: 7.0 ✓                                        │   │
│   │                                                     │   │
│   └─────────────────────────────────────────────────────┘   │
│                            │                                │
│                            ▼                                │
│   ┌─────────────────────────────────────────────────────┐   │
│   │                   ESP32                             │   │
│   │    Membaca semua sensor setiap 5 detik             │   │
│   └─────────────────────────────────────────────────────┘   │
│                            │                                │
│                            ▼                                │
│   ┌─────────────────────────────────────────────────────┐   │
│   │                   CLOUD                             │   │
│   │    Menyimpan data, analisis, notifikasi            │   │
│   └─────────────────────────────────────────────────────┘   │
│                            │                                │
│                            ▼                                │
│   ┌─────────────────────────────────────────────────────┐   │
│   │                DASHBOARD / HP                       │   │
│   │    Peternak melihat semua data real-time           │   │
│   └─────────────────────────────────────────────────────┘   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 📋 Tabel Ringkasan Sensor

| Sensor         | Parameter       | Satuan  | Ideal          | Bahaya        |
| -------------- | --------------- | ------- | -------------- | ------------- |
| **Suhu**       | Temperatur      | °C      | 21-27°C (ayam) | >35°C         |
| **Kelembaban** | RH              | %       | 50-70%         | <40% / >80%   |
| **Amonia**     | NH3             | ppm     | <25 ppm        | >50 ppm       |
| **CO2**        | Karbon dioksida | ppm     | <3000 ppm      | >5000 ppm     |
| **Berat**      | Massa           | gram/kg | Sesuai umur    | Turun drastis |
| **pH**         | Keasaman        | -       | 6.5-8.5        | <6 / >9       |

---

## 📝 Rangkuman

```
┌─────────────────────────────────────────────────────────────┐
│              5 SENSOR LINGKUNGAN KANDANG                    │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. 🌡️ SENSOR SUHU                                         │
│     Menjaga ternak dari kepanasan/kedinginan               │
│                                                             │
│  2. 💧 SENSOR KELEMBABAN                                    │
│     Mencegah penyakit akibat udara terlalu lembab/kering   │
│                                                             │
│  3. 💨 SENSOR GAS                                           │
│     Mendeteksi amonia, CO2, dan gas berbahaya lainnya      │
│                                                             │
│  4. ⚖️ SENSOR BERAT                                         │
│     Memantau pertumbuhan dan kesehatan ternak              │
│                                                             │
│  5. 🧪 SENSOR pH                                            │
│     Menjaga kualitas air minum dan kesehatan ternak        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## ❓ Pertanyaan Diskusi

1. **Jika Anda hanya bisa memasang 2 sensor di kandang ayam, sensor apa saja yang akan Anda pilih? Mengapa?**

2. **Menurut Anda, apa yang terjadi jika sensor kelembaban rusak dan tidak terdeteksi selama seminggu?**

3. **Bagaimana cara peternak tradisional mengecek kondisi kandang tanpa sensor? Apa kelemahannya?**

4. **Untuk peternakan sapi perah, sensor tambahan apa yang mungkin berguna selain yang sudah dibahas?**

---

## 📚 Istilah Penting

| Istilah       | Arti                                            |
| ------------- | ----------------------------------------------- |
| **ppm**       | Parts per million - bagian per juta (untuk gas) |
| **RH**        | Relative Humidity - kelembaban relatif          |
| **Load Cell** | Sensor beban/berat                              |
| **Kalibrasi** | Menyetel ulang sensor agar akurat               |
| **Real-time** | Data langsung/saat itu juga                     |
| **Probe**     | Bagian sensor yang dicelupkan ke cairan         |

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar tentang **Aktuator dan Mikrokontroler** - alat yang bertindak berdasarkan data sensor dan "otak" yang mengendalikan semuanya!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna jika Anda ingin mempelajari lebih dalam atau mengutip untuk tugas/skripsi.

### Sumber Akademik

| No  | Referensi                                                                                                                                                                                                                                 | Keterangan                       |
| --- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
| 1   | Aviagen (2018). _Ross Broiler Management Handbook_. Aviagen Group.                                                                                                                                                                        | Standar suhu untuk ayam broiler  |
| 2   | Kristensen, H. H., & Wathes, C. M. (2000). Ammonia and poultry welfare: a review. _World's Poultry Science Journal_, 56(3), 235-245.                                                                                                      | Dampak amonia pada unggas        |
| 3   | Miles, D. M., et al. (2004). Atmospheric ammonia is detrimental to the performance of modern commercial broilers. _Poultry Science_, 83(10), 1650-1654.                                                                                   | Efek amonia terhadap pertumbuhan |
| 4   | Lin, H., et al. (2006). Responses of laying hens to acute heat stress. _Poultry Science_, 85(9), 1602-1608.                                                                                                                               | Dampak stres panas pada produksi |
| 5   | Banhazi, T. M., et al. (2008). Precision Livestock Farming: A suite of electronic systems to ensure the application of best practice management on livestock farms. _Australian Journal of Multi-disciplinary Engineering_, 6(2), 99-107. | Review sistem sensor peternakan  |

### Sumber Teknis Sensor

| No  | Referensi                                                   | Keterangan                |
| --- | ----------------------------------------------------------- | ------------------------- |
| 6   | Sensirion AG. _DHT22 Datasheet_. Tersedia di: sensirion.com | Spesifikasi sensor DHT22  |
| 7   | Figaro Engineering Inc. _MQ-Series Gas Sensor Datasheet_.   | Spesifikasi sensor gas MQ |
| 8   | AVIA Semiconductor. _HX711 Load Cell Amplifier Datasheet_.  | Modul penguat load cell   |

### Sumber Lokal Indonesia

| No  | Referensi                                                                                                         | Keterangan                     |
| --- | ----------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| 9   | Dirjen Peternakan dan Kesehatan Hewan. (2020). _Pedoman Teknis Budidaya Ayam Ras Pedaging_. Jakarta: Kementan RI. | Standar kandang ayam Indonesia |
| 10  | SNI 7310:2008. _Bibit Niaga (final stock) Ayam Ras Tipe Pedaging Umur Sehari_. BSN.                               | Standar nasional DOC           |
