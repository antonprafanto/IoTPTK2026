# 🔬 Pertemuan 3: Praktikum Sensor Lingkungan Kandang (WOKWI)

> **"Hari ini kita akan memasang sensor virtual di kandang virtual — tapi ilmunya nyata!"**

---

## 👨‍🏫 Dosen Pengampu

- **Anton Prafanto** / **Anhar** (Kelas A / Kelas B)

---

## 🎯 Tujuan Praktikum

Setelah praktikum ini, mahasiswa mampu:

1. Menggunakan simulator Wokwi untuk merangkai sensor
2. Memahami cara kerja sensor DHT22 (suhu & kelembaban)
3. Membuat sistem alarm sederhana untuk kandang ternak
4. Menghubungkan konsep sensor dengan kebutuhan peternakan nyata

---

## 🌐 Mengenal WOKWI — Laboratorium Virtual Kita

### Apa itu Wokwi?

**Wokwi** adalah website yang memungkinkan kita **merangkai dan menguji alat elektronik secara virtual** — tanpa perlu beli komponen!

> 💡 **Analoginya:** Seperti game simulasi pertanian (Harvest Moon), tapi ini simulasi elektronik!

### Cara Memulai

1. Buka browser (Chrome/Edge/Firefox)
2. Kunjungi **[wokwi.com](https://wokwi.com)**
3. Klik **"Start Creating"** atau **"Sign Up"** (gratis!)
4. Pilih **"New Project"** → **"ESP32"**

### Tampilan Wokwi

```
┌─────────────────────────────────────────────────────────────┐
│                        WOKWI.COM                            │
├────────────────────────┬────────────────────────────────────┤
│                        │                                    │
│   📝 AREA KODE         │   🔧 AREA RANGKAIAN               │
│   (Tempat menulis      │   (Tempat merangkai               │
│    program/resep)      │    komponen elektronik)            │
│                        │                                    │
│   Kita akan COPY-      │   Kita akan MENAMBAH               │
│   PASTE kode di        │   sensor, LED, dll                 │
│   sini                 │   di sini                          │
│                        │                                    │
├────────────────────────┴────────────────────────────────────┤
│   ▶️ TOMBOL PLAY — Klik untuk menjalankan simulasi          │
│   📟 SERIAL MONITOR — Tempat melihat hasil bacaan sensor   │
└─────────────────────────────────────────────────────────────┘
```

---

## 🌡️ PRAKTIK 1: Sensor Suhu & Kelembaban (DHT22)

### 🐔 Skenario Peternakan

> Pak Budi punya kandang ayam broiler 5000 ekor. Setiap malam dia harus bangun jam 2 untuk mengecek suhu kandang. Kalau kepanasan, ayam bisa stres dan mati. **Bagaimana jika ada alat yang otomatis memantau suhu dan memberi alarm?**

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│              SISTEM ALARM SUHU KANDANG                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🌡️ Sensor DHT22 membaca suhu dan kelembaban              │
│          ↓                                                  │
│   🧠 ESP32 mengecek: "Apakah suhu bahaya?"                 │
│          ↓                                                  │
│   ✅ Suhu AMAN (< 32°C)  → 🟢 LED Hijau menyala            │
│   ⚠️ Suhu BAHAYA (≥ 32°C) → 🔴 LED Merah menyala           │
│                                                             │
│   📟 Serial Monitor menampilkan angka suhu & kelembaban     │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen          | Fungsi                              | Jumlah |
| --- | ----------------- | ----------------------------------- | ------ |
| 1   | **ESP32**         | Otak sistem (mikrokontroler)        | 1      |
| 2   | **DHT22**         | Sensor suhu & kelembaban            | 1      |
| 3   | **LED Hijau**     | Lampu tanda AMAN                    | 1      |
| 4   | **LED Merah**     | Lampu tanda BAHAYA                  | 1      |
| 5   | **Resistor 220Ω** | Pelindung LED (agar tidak terbakar) | 2      |

### 🔌 Diagram Koneksi (Cara Menyambungkan)

```
                    ESP32
              ┌──────────────┐
              │              │
  DHT22       │   GPIO 15 ←──── Data dari DHT22
  ┌─────┐     │              │
  │ VCC ├────→│   3.3V       │
  │ DATA├────→│   GPIO 15    │
  │ GND ├────→│   GND        │
  └─────┘     │              │
              │   GPIO 2  ────→ LED Hijau → Resistor → GND
              │   GPIO 4  ────→ LED Merah → Resistor → GND
              │              │
              └──────────────┘
```

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)**
2. Klik **"New Project"**
3. Pilih **"ESP32"** → Pilih **"ESP32 DevKit V1"**
4. Klik **"Create Project"**

#### Langkah 2: Tambahkan Komponen

1. Klik tombol **"+" (Add Component)** di area rangkaian
2. Cari dan tambahkan:
   - Ketik **"DHT22"** → klik untuk menambahkan
   - Ketik **"LED"** → tambahkan **2 buah** (1 hijau, 1 merah)
   - Ketik **"Resistor"** → tambahkan **2 buah**

#### Langkah 3: Atur Warna LED

1. Klik LED pertama → ubah warna ke **Hijau (green)**
2. Klik LED kedua → ubah warna ke **Merah (red)**
3. Klik setiap Resistor → pastikan nilainya **220Ω**

#### Langkah 4: Sambungkan Kabel

Sambungkan sesuai diagram di atas:

- **DHT22 VCC** → **ESP32 3.3V**
- **DHT22 DATA** → **ESP32 GPIO 15**
- **DHT22 GND** → **ESP32 GND**
- **LED Hijau (+/Anode)** → **Resistor** → **ESP32 GPIO 2**
- **LED Hijau (-/Katode)** → **ESP32 GND**
- **LED Merah (+/Anode)** → **Resistor** → **ESP32 GPIO 4**
- **LED Merah (-/Katode)** → **ESP32 GND**

#### Langkah 5: Copy-Paste Kode

Hapus semua kode yang ada, lalu **copy-paste** kode di bawah ini:

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 🐔 SISTEM MONITORING SUHU KANDANG AYAM
// ============================================================
// Alat ini membaca suhu dan kelembaban kandang,
// lalu menyalakan lampu HIJAU jika aman,
// atau lampu MERAH jika terlalu panas.
// ============================================================

#include "DHTesp.h"  // Kita panggil "pustaka" untuk sensor DHT22

// --- PENGATURAN PIN (kabel mana ke mana) ---
const int PIN_SENSOR = 15;     // Sensor DHT22 disambungkan ke pin 15
const int PIN_LAMPU_AMAN = 2;  // LED Hijau disambungkan ke pin 2
const int PIN_LAMPU_BAHAYA = 4; // LED Merah disambungkan ke pin 4

// --- BATAS SUHU UNTUK AYAM BROILER ---
// Ayam broiler dewasa nyaman di suhu 21-27°C
// Di atas 32°C sudah bahaya!
const float SUHU_BAHAYA = 32.0;     // Derajat Celsius
const float KELEMBABAN_MAKS = 80.0; // Persen (%)

// Buat "alat baca" sensor
DHTesp sensorSuhu;

void setup() {
  // --- PERSIAPAN AWAL (dijalankan sekali saat alat dinyalakan) ---

  Serial.begin(115200);  // Buka "layar monitor" untuk melihat hasil
  Serial.println("================================");
  Serial.println("🐔 MONITOR SUHU KANDANG AYAM");
  Serial.println("================================");

  // Atur pin LED sebagai OUTPUT (untuk menyalakan lampu)
  pinMode(PIN_LAMPU_AMAN, OUTPUT);
  pinMode(PIN_LAMPU_BAHAYA, OUTPUT);

  // Hubungkan sensor DHT22
  sensorSuhu.setup(PIN_SENSOR, DHTesp::DHT22);

  Serial.println("✅ Sensor siap! Mulai memantau kandang...");
  Serial.println("");
}

void loop() {
  // --- PEKERJAAN UTAMA (diulang terus-menerus) ---

  // 1️⃣ BACA DATA DARI SENSOR
  float suhu = sensorSuhu.getTemperature();        // Baca suhu (°C)
  float kelembaban = sensorSuhu.getHumidity();      // Baca kelembaban (%)

  // Cek apakah sensor berhasil membaca
  if (isnan(suhu) || isnan(kelembaban)) {
    Serial.println("❌ Gagal membaca sensor! Periksa kabel.");
    delay(2000);
    return;  // Coba lagi
  }

  // 2️⃣ TAMPILKAN DATA DI SERIAL MONITOR
  Serial.println("────────────────────────────────");
  Serial.print("🌡️ Suhu Kandang    : ");
  Serial.print(suhu, 1);  // 1 angka di belakang koma
  Serial.println(" °C");

  Serial.print("💧 Kelembaban      : ");
  Serial.print(kelembaban, 1);
  Serial.println(" %");

  // 3️⃣ CEK APAKAH SUHU AMAN ATAU BAHAYA
  if (suhu >= SUHU_BAHAYA) {
    // ⚠️ BAHAYA! Suhu terlalu panas untuk ayam!
    Serial.println("🔴 STATUS: ⚠️ BAHAYA! Suhu terlalu panas!");
    Serial.println("   → Segera nyalakan kipas atau sprinkler!");

    digitalWrite(PIN_LAMPU_AMAN, LOW);     // Matikan lampu hijau
    digitalWrite(PIN_LAMPU_BAHAYA, HIGH);  // Nyalakan lampu merah
  }
  else {
    // ✅ AMAN! Suhu normal untuk ayam
    Serial.println("🟢 STATUS: ✅ Suhu AMAN, ayam nyaman");

    digitalWrite(PIN_LAMPU_AMAN, HIGH);    // Nyalakan lampu hijau
    digitalWrite(PIN_LAMPU_BAHAYA, LOW);   // Matikan lampu merah
  }

  // 4️⃣ CEK KELEMBABAN JUGA
  if (kelembaban > KELEMBABAN_MAKS) {
    Serial.println("💧 PERINGATAN: Kelembaban terlalu tinggi!");
    Serial.println("   → Risiko penyakit pernapasan meningkat!");
  }

  Serial.println("");

  // 5️⃣ TUNGGU 2 DETIK SEBELUM BACA LAGI
  // (Sensor perlu waktu istirahat sebelum baca ulang)
  delay(2000);
}
```

### ▶️ Cara Menjalankan

1. Klik tombol **▶️ Play** (hijau) di bagian atas Wokwi
2. Tunggu beberapa detik sampai program ter-compile
3. Lihat **Serial Monitor** di bagian bawah — data suhu akan muncul!
4. **Klik sensor DHT22** di area rangkaian → akan muncul **slider**
5. **Geser slider suhu** ke atas 32°C → lihat LED merah menyala!
6. **Geser slider suhu** ke bawah 32°C → LED hijau menyala kembali!

### 🧪 Eksperimen untuk Mahasiswa

> **Tantangan 1:** Ubah batas suhu bahaya dari 32°C menjadi **27°C** (suhu ideal ayam layer lebih rendah). Amati apa yang terjadi!
>
> Petunjuk: Cari baris `const float SUHU_BAHAYA = 32.0;` dan ubah angkanya.

> **Tantangan 2:** Tambahkan peringatan jika kelembaban **terlalu rendah** (di bawah 50%). Petunjuk: Tambahkan `if (kelembaban < 50.0)` di bagian cek kelembaban.

> **Tantangan 3:** Coba geser slider kelembaban ke **85%**. Apa pesan yang muncul di Serial Monitor?

### 📝 Lembar Pengamatan Praktik 1

Isi tabel berikut selama praktikum:

| No  | Suhu (°C) | Kelembaban (%) | LED Hijau | LED Merah | Status di Monitor |
| --- | --------- | -------------- | --------- | --------- | ----------------- |
| 1   | 25        |                |           |           |                   |
| 2   | 28        |                |           |           |                   |
| 3   | 32        |                |           |           |                   |
| 4   | 36        |                |           |           |                   |
| 5   | 28        | 85             |           |           |                   |

### 🐔 Hubungan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          APA YANG KITA PELAJARI vs DUNIA NYATA              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Di Wokwi (Virtual):         Di Kandang (Nyata):          │
│                                                             │
│   🌡️ DHT22 (sensor)     →    🌡️ DHT22 asli (Rp 35.000)   │
│   🟢 LED Hijau           →    ✅ Lampu indikator aman      │
│   🔴 LED Merah           →    🚨 Alarm / sirene            │
│   📟 Serial Monitor      →    📱 Notifikasi ke HP          │
│   🖱️ Geser slider suhu   →    🌤️ Perubahan cuaca nyata    │
│   🧠 ESP32               →    🧠 ESP32 asli (Rp 50.000)   │
│                                                             │
│   💰 Total biaya nyata: ± Rp 120.000                       │
│      (ESP32 + DHT22 + LED + kabel)                         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 💨 PRAKTIK 2: Sensor Gas — Deteksi Amonia Kandang (Simulasi)

### 🐔 Skenario Peternakan

> Bu Sari memiliki kandang ayam tertutup (closed house). Saat musim hujan, ventilasi kurang lancar dan **bau amonia (pesing) dari kotoran ayam sangat menyengat**. Beberapa ayam mulai bersin-bersin dan matanya merah. Bu Sari butuh alat yang bisa **mendeteksi kadar amonia** dan memberi peringatan sebelum terlambat!

### 💡 Catatan Penting

> ⚠️ **Sensor gas MQ-135 belum tersedia di Wokwi**, jadi kita gunakan **Potentiometer** (knob putar) sebagai pengganti. Prinsipnya sama: keduanya menghasilkan **sinyal analog** (angka yang berubah-ubah).
>
> Bayangkan potentiometer sebagai **"remote control amonia"** — kita putar untuk mensimulasikan kadar gas naik atau turun.

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│          SISTEM DETEKSI GAS AMONIA KANDANG                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🎛️ Potentiometer (simulasi sensor gas MQ-135)            │
│          ↓                                                  │
│   🧠 ESP32 mengecek: "Berapa kadar amonianya?"             │
│          ↓                                                  │
│   🟢 AMAN (< 25 ppm)     → LED Hijau, tidak ada alarm      │
│   🟡 WASPADA (25-50 ppm) → LED Kuning, peringatan          │
│   🔴 BAHAYA (> 50 ppm)   → LED Merah + Buzzer berbunyi!    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen          | Fungsi                                 | Jumlah |
| --- | ----------------- | -------------------------------------- | ------ |
| 1   | **ESP32**         | Otak sistem                            | 1      |
| 2   | **Potentiometer** | Simulasi sensor gas (pengganti MQ-135) | 1      |
| 3   | **LED Hijau**     | Lampu tanda AMAN                       | 1      |
| 4   | **LED Kuning**    | Lampu tanda WASPADA                    | 1      |
| 5   | **LED Merah**     | Lampu tanda BAHAYA                     | 1      |
| 6   | **Buzzer**        | Alarm suara saat gas bahaya            | 1      |
| 7   | **Resistor 220Ω** | Pelindung LED                          | 3      |

### 🔌 Diagram Koneksi

```
                      ESP32
                ┌──────────────┐
                │              │
  Potentiometer │              │
  ┌─────────┐   │              │
  │ VCC  ├──→│   3.3V       │
  │ SIG  ├──→│   GPIO 34    │  ← Baca nilai analog
  │ GND  ├──→│   GND        │
  └─────────┘   │              │
                │   GPIO 2  ───→ LED Hijau  → Resistor → GND
                │   GPIO 4  ───→ LED Kuning → Resistor → GND
                │   GPIO 5  ───→ LED Merah  → Resistor → GND
                │   GPIO 18 ───→ Buzzer (+) → GND
                │              │
                └──────────────┘
```

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: Tambahkan Komponen

1. Klik **"+"** lalu tambahkan:
   - **Potentiometer** (ketik "potentiometer")
   - **LED** × 3 buah (hijau, kuning, merah)
   - **Resistor** × 3 buah (220Ω)
   - **Buzzer** (ketik "buzzer" → pilih yang biasa/passive)

#### Langkah 3: Sambungkan Kabel

Sambungkan sesuai diagram di atas.

#### Langkah 4: Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 💨 SISTEM DETEKSI GAS AMONIA KANDANG
// ============================================================
// Alat ini membaca kadar gas amonia di kandang
// (disimulasikan dengan potentiometer).
// Ada 3 level peringatan: AMAN, WASPADA, BAHAYA!
// ============================================================

// --- PENGATURAN PIN ---
const int PIN_SENSOR_GAS = 34;    // Potentiometer di pin 34 (analog)
const int PIN_LAMPU_AMAN = 2;     // LED Hijau
const int PIN_LAMPU_WASPADA = 4;  // LED Kuning
const int PIN_LAMPU_BAHAYA = 5;   // LED Merah
const int PIN_ALARM = 18;         // Buzzer

// --- BATAS KADAR AMONIA (dalam ppm) ---
// Menurut penelitian, batas aman amonia untuk ayam < 25 ppm
// Di atas 50 ppm sudah sangat berbahaya!
const int BATAS_WASPADA = 25;  // ppm
const int BATAS_BAHAYA = 50;   // ppm

void setup() {
  // --- PERSIAPAN AWAL ---
  Serial.begin(115200);
  Serial.println("================================");
  Serial.println("💨 DETEKTOR GAS AMONIA KANDANG");
  Serial.println("================================");

  // Atur pin sebagai OUTPUT
  pinMode(PIN_LAMPU_AMAN, OUTPUT);
  pinMode(PIN_LAMPU_WASPADA, OUTPUT);
  pinMode(PIN_LAMPU_BAHAYA, OUTPUT);
  pinMode(PIN_ALARM, OUTPUT);

  Serial.println("✅ Sensor gas siap! Mulai memantau...");
  Serial.println("");
}

void loop() {
  // --- PEKERJAAN UTAMA ---

  // 1️⃣ BACA NILAI DARI POTENTIOMETER (simulasi sensor gas)
  // Potentiometer memberi nilai 0-4095
  // Kita ubah ke skala 0-100 ppm agar mirip sensor asli
  int nilaiMentah = analogRead(PIN_SENSOR_GAS);
  int kadarAmonia = map(nilaiMentah, 0, 4095, 0, 100);

  // 2️⃣ TAMPILKAN DI SERIAL MONITOR
  Serial.println("────────────────────────────────");
  Serial.print("💨 Kadar Amonia  : ");
  Serial.print(kadarAmonia);
  Serial.println(" ppm");

  // 3️⃣ CEK LEVEL BAHAYA (3 tingkat)
  if (kadarAmonia >= BATAS_BAHAYA) {
    // 🔴 BAHAYA! Gas sangat tinggi!
    Serial.println("🔴 STATUS: 🚨 BAHAYA! Amonia sangat tinggi!");
    Serial.println("   → Buka semua ventilasi!");
    Serial.println("   → Ganti litter/alas kandang segera!");

    // Nyalakan LED merah + Buzzer
    digitalWrite(PIN_LAMPU_AMAN, LOW);
    digitalWrite(PIN_LAMPU_WASPADA, LOW);
    digitalWrite(PIN_LAMPU_BAHAYA, HIGH);

    // Buzzer berbunyi putus-putus (alarm!)
    digitalWrite(PIN_ALARM, HIGH);
    delay(200);
    digitalWrite(PIN_ALARM, LOW);
    delay(200);
    digitalWrite(PIN_ALARM, HIGH);
    delay(200);
    digitalWrite(PIN_ALARM, LOW);
  }
  else if (kadarAmonia >= BATAS_WASPADA) {
    // 🟡 WASPADA! Gas mulai naik
    Serial.println("🟡 STATUS: ⚠️ WASPADA! Amonia mulai tinggi");
    Serial.println("   → Tingkatkan ventilasi kandang");

    // Nyalakan LED kuning, matikan lainnya
    digitalWrite(PIN_LAMPU_AMAN, LOW);
    digitalWrite(PIN_LAMPU_WASPADA, HIGH);
    digitalWrite(PIN_LAMPU_BAHAYA, LOW);
    digitalWrite(PIN_ALARM, LOW);
  }
  else {
    // 🟢 AMAN! Gas dalam batas normal
    Serial.println("🟢 STATUS: ✅ Amonia AMAN, udara bersih");

    // Nyalakan LED hijau, matikan lainnya
    digitalWrite(PIN_LAMPU_AMAN, HIGH);
    digitalWrite(PIN_LAMPU_WASPADA, LOW);
    digitalWrite(PIN_LAMPU_BAHAYA, LOW);
    digitalWrite(PIN_ALARM, LOW);
  }

  Serial.println("");

  // Tunggu 1 detik sebelum baca lagi
  delay(1000);
}
```

### ▶️ Cara Menjalankan

1. Klik tombol **▶️ Play**
2. Lihat Serial Monitor — kadar amonia akan muncul
3. **Putar knob potentiometer** pelan-pelan ke kanan
4. Amati perubahan:
   - Knob di kiri (0-25 ppm) → 🟢 LED Hijau
   - Knob di tengah (25-50 ppm) → 🟡 LED Kuning
   - Knob di kanan (>50 ppm) → 🔴 LED Merah + 🔊 Buzzer berbunyi!

### 🧪 Eksperimen untuk Mahasiswa

> **Tantangan 1:** Ubah batas WASPADA dari 25 ppm menjadi **20 ppm**. Apakah alarm jadi lebih sensitif atau kurang sensitif?

> **Tantangan 2:** Ubah pola bunyi buzzer dari 2x menjadi **5x berturut-turut** saat BAHAYA.

> **Tantangan 3:** Bayangkan Anda peternak kambing. Menurut materi teori, apakah batas amonia untuk kambing sama dengan ayam? Jika berbeda, ubah batasnya!

### 📝 Lembar Pengamatan Praktik 2

Putar potentiometer dan catat hasilnya:

| No  | Posisi Knob  | Kadar Amonia (ppm) | LED Hijau | LED Kuning | LED Merah | Buzzer |
| --- | ------------ | ------------------ | --------- | ---------- | --------- | ------ |
| 1   | Paling kiri  |                    |           |            |           |        |
| 2   | ¼ putaran    |                    |           |            |           |        |
| 3   | ½ putaran    |                    |           |            |           |        |
| 4   | ¾ putaran    |                    |           |            |           |        |
| 5   | Paling kanan |                    |           |            |           |        |

### 🐔 Hubungan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          PRAKTIK vs DUNIA NYATA                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Di Wokwi:                   Di Kandang:                  │
│                                                             │
│   🎛️ Potentiometer      →    💨 Sensor MQ-135 (Rp 25.000) │
│   🟢🟡🔴 3 LED          →    🚦 Lampu indikator 3 warna   │
│   🔊 Buzzer             →    🚨 Sirene / alarm kandang     │
│   🔄 Putar knob         →    💨 Gas amonia dari kotoran    │
│                                                             │
│   💡 Di kandang nyata, sensor MQ-135 mendeteksi gas        │
│      secara otomatis — tidak perlu diputar manual!         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## ⚖️ PRAKTIK 3: Sensor Berat — Pantau Pertumbuhan Ternak (Simulasi)

### 🐔 Skenario Peternakan

> Pak Dani punya 3000 ekor ayam broiler. Setiap minggu dia harus menimbang sampel ayam untuk memastikan **pertumbuhannya sesuai target**. Kalau berat ayam di bawah standar, mungkin ada masalah pakan atau penyakit. **Bagaimana jika timbangan bisa otomatis mencatat dan memberi peringatan?**

### 💡 Catatan Penting

> ⚠️ **Load Cell + HX711 belum tersedia di Wokwi**, jadi kita gunakan **Potentiometer** sebagai simulasi. Putar knob = berat ayam berubah. Di dunia nyata, ayam naik ke papan timbang dan beratnya otomatis terbaca!

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│          SISTEM TIMBANG OTOMATIS TERNAK                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🎛️ Potentiometer (simulasi Load Cell / timbangan)        │
│          ↓                                                  │
│   🧠 ESP32 membaca berat dan bandingkan target             │
│          ↓                                                  │
│   📟 LCD menampilkan berat + status pertumbuhan            │
│   🟢 Berat NORMAL   → "Pertumbuhan OK!"                    │
│   🟡 Berat KURANG   → "Peringatan: Berat kurang!"          │
│   🔴 Berat TURUN    → "BAHAYA: Kemungkinan sakit!"         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen           | Fungsi                                   | Jumlah |
| --- | ------------------ | ---------------------------------------- | ------ |
| 1   | **ESP32**          | Otak sistem                              | 1      |
| 2   | **Potentiometer**  | Simulasi timbangan (pengganti Load Cell) | 1      |
| 3   | **LCD 16x2 (I2C)** | Layar untuk menampilkan berat            | 1      |
| 4   | **LED Hijau**      | Indikator pertumbuhan normal             | 1      |
| 5   | **LED Merah**      | Indikator berat kurang/turun             | 1      |
| 6   | **Resistor 220Ω**  | Pelindung LED                            | 2      |

### 🔌 Diagram Koneksi

```
                      ESP32
                ┌──────────────┐
                │              │
  Potentiometer │              │
  ┌─────────┐   │              │
  │ VCC  ├──→│   3.3V       │
  │ SIG  ├──→│   GPIO 34    │  ← Baca berat (analog)
  │ GND  ├──→│   GND        │
  └─────────┘   │              │
                │              │
  LCD I2C       │              │
  ┌─────────┐   │              │
  │ VCC  ├──→│   5V         │
  │ GND  ├──→│   GND        │
  │ SDA  ├──→│   GPIO 21    │  ← Data LCD
  │ SCL  ├──→│   GPIO 22    │  ← Clock LCD
  └─────────┘   │              │
                │   GPIO 2  ───→ LED Hijau  → Resistor → GND
                │   GPIO 4  ───→ LED Merah  → Resistor → GND
                │              │
                └──────────────┘
```

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: Tambahkan Komponen

1. Klik **"+"** lalu tambahkan:
   - **Potentiometer** (ketik "potentiometer")
   - **LCD1602** (ketik "lcd" → pilih yang **I2C** / ada tulisan "I2C")
   - **LED** × 2 buah (hijau, merah)
   - **Resistor** × 2 buah (220Ω)

#### Langkah 3: Sambungkan Kabel

Sambungkan sesuai diagram di atas. Untuk LCD I2C, pastikan SDA ke GPIO 21 dan SCL ke GPIO 22.

#### Langkah 4: Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// ⚖️ SISTEM TIMBANG OTOMATIS TERNAK
// ============================================================
// Alat ini membaca berat ayam (simulasi potentiometer)
// dan menampilkan di layar LCD.
// Memberi tahu apakah pertumbuhan ayam normal atau tidak.
// ============================================================

#include <LiquidCrystal_I2C.h>  // Pustaka untuk layar LCD

// --- PENGATURAN PIN ---
const int PIN_TIMBANGAN = 34;    // Potentiometer (simulasi load cell)
const int PIN_LAMPU_OK = 2;      // LED Hijau
const int PIN_LAMPU_MASALAH = 4; // LED Merah

// --- TARGET BERAT AYAM BROILER (gram) ---
// Berdasarkan standar Aviagen (2018):
// Minggu 1: 180g, Minggu 2: 450g, Minggu 3: 850g
// Minggu 4: 1300g, Minggu 5: 1800g
// Kita simulasikan potentiometer 0-3000 gram
const int BERAT_MINIMUM = 1000;   // Berat minimum target (gram)
const int BERAT_MAKSIMUM = 3000;  // Berat maksimum simulasi (gram)

// Buat layar LCD (alamat 0x27, ukuran 16 kolom x 2 baris)
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  // --- PERSIAPAN AWAL ---
  Serial.begin(115200);
  Serial.println("================================");
  Serial.println("⚖️ TIMBANGAN OTOMATIS TERNAK");
  Serial.println("================================");

  // Nyalakan layar LCD
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Timbang Ayam");
  lcd.setCursor(0, 1);
  lcd.print("Siap!");

  // Atur LED
  pinMode(PIN_LAMPU_OK, OUTPUT);
  pinMode(PIN_LAMPU_MASALAH, OUTPUT);

  Serial.println("✅ Timbangan siap!");
  delay(2000);
}

void loop() {
  // --- PEKERJAAN UTAMA ---

  // 1️⃣ BACA BERAT DARI POTENTIOMETER (simulasi timbangan)
  int nilaiMentah = analogRead(PIN_TIMBANGAN);
  // Ubah nilai 0-4095 menjadi berat 0-3000 gram
  int beratAyam = map(nilaiMentah, 0, 4095, 0, BERAT_MAKSIMUM);

  // 2️⃣ TAMPILKAN DI SERIAL MONITOR
  Serial.println("────────────────────────────────");
  Serial.print("⚖️ Berat Ayam    : ");
  Serial.print(beratAyam);
  Serial.println(" gram");

  // 3️⃣ TAMPILKAN DI LAYAR LCD
  lcd.clear();
  lcd.setCursor(0, 0);  // Baris pertama
  lcd.print("Berat: ");
  lcd.print(beratAyam);
  lcd.print(" g");

  lcd.setCursor(0, 1);  // Baris kedua

  // 4️⃣ CEK STATUS PERTUMBUHAN
  if (beratAyam >= BERAT_MINIMUM) {
    // ✅ Berat normal — ayam tumbuh sesuai target
    lcd.print("Status: NORMAL");

    Serial.println("🟢 STATUS: ✅ Pertumbuhan NORMAL");
    Serial.print("   → Berat di atas target (");
    Serial.print(BERAT_MINIMUM);
    Serial.println("g)");

    digitalWrite(PIN_LAMPU_OK, HIGH);
    digitalWrite(PIN_LAMPU_MASALAH, LOW);
  }
  else if (beratAyam >= BERAT_MINIMUM / 2) {
    // 🟡 Berat agak kurang — perlu perhatian
    lcd.print("KURANG! Cek pakan");

    Serial.println("🟡 STATUS: ⚠️ Berat KURANG dari target");
    Serial.println("   → Evaluasi kualitas pakan!");
    Serial.println("   → Cek apakah ada yang sakit");

    // LED merah berkedip pelan
    digitalWrite(PIN_LAMPU_OK, LOW);
    digitalWrite(PIN_LAMPU_MASALAH, HIGH);
  }
  else {
    // 🔴 Berat sangat kurang — kemungkinan masalah serius
    lcd.print("BAHAYA! Cek kes.");

    Serial.println("🔴 STATUS: 🚨 BAHAYA! Berat sangat kurang");
    Serial.println("   → Kemungkinan ayam sakit!");
    Serial.println("   → Segera hubungi dokter hewan!");

    // LED merah berkedip cepat
    digitalWrite(PIN_LAMPU_OK, LOW);
    digitalWrite(PIN_LAMPU_MASALAH, HIGH);
    delay(200);
    digitalWrite(PIN_LAMPU_MASALAH, LOW);
    delay(200);
    digitalWrite(PIN_LAMPU_MASALAH, HIGH);
  }

  // Hitung FCR sederhana (Feed Conversion Ratio)
  // FCR = Total pakan / Berat ayam
  // Asumsi pakan kumulatif 2x berat saat ini
  if (beratAyam > 0) {
    float fcr = (beratAyam * 2.0) / beratAyam;
    Serial.print("📊 FCR (estimasi): ");
    Serial.println(fcr, 1);
    Serial.println("   (FCR ideal ayam broiler: 1.5-1.8)");
  }

  Serial.println("");
  delay(1000);
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play**
2. Lihat **layar LCD** — akan menampilkan "Timbang Ayam - Siap!"
3. **Putar knob potentiometer** untuk mengubah berat ayam
4. Amati:
   - Berat di atas 1000g → 🟢 LCD: "Status: NORMAL"
   - Berat 500-1000g → 🟡 LCD: "KURANG! Cek pakan"
   - Berat di bawah 500g → 🔴 LCD: "BAHAYA! Cek kes." + LED berkedip

### 🧪 Eksperimen untuk Mahasiswa

> **Tantangan 1:** Ubah `BERAT_MINIMUM` menjadi **1800** gram (target ayam broiler minggu ke-5). Putar knob dan amati perbedaannya!

> **Tantangan 2:** Ubah batas `BERAT_MAKSIMUM` menjadi **50000** (50 kg) untuk mensimulasikan timbangan **kambing**. Sesuaikan juga `BERAT_MINIMUM` menjadi **15000** (15 kg).

> **Tantangan 3:** Perhatikan angka **FCR** di Serial Monitor. Menurut materi, FCR ideal ayam broiler adalah 1.5-1.8. Apa artinya jika FCR = 2.5?

### 📝 Lembar Pengamatan Praktik 3

| No  | Posisi Knob  | Berat (gram) | Tampilan LCD | LED Hijau | LED Merah | Status |
| --- | ------------ | ------------ | ------------ | --------- | --------- | ------ |
| 1   | Paling kiri  |              |              |           |           |        |
| 2   | ¼ putaran    |              |              |           |           |        |
| 3   | ½ putaran    |              |              |           |           |        |
| 4   | ¾ putaran    |              |              |           |           |        |
| 5   | Paling kanan |              |              |           |           |        |

### 🐔 Hubungan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          PRAKTIK vs DUNIA NYATA                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Di Wokwi:                    Di Kandang:                 │
│                                                             │
│   🎛️ Potentiometer       →    ⚖️ Load Cell (Rp 30.000)    │
│   📟 LCD 16x2            →    📟 Layar digital timbangan   │
│   🔄 Putar knob          →    🐔 Ayam naik ke timbangan   │
│                                                             │
│   💡 Di kandang nyata, timbangan dipasang di tempat        │
│      bertengger. Ayam naik sendiri dan beratnya            │
│      otomatis tercatat + dikirim ke HP peternak!           │
│                                                             │
│   💰 Biaya: Load Cell + HX711 + ESP32 ≈ Rp 100.000        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 🧪 PRAKTIK 4: Sensor pH — Jaga Kualitas Air Minum Ternak (Simulasi)

### 🐔 Skenario Peternakan

> Bu Ratna adalah peternak sapi perah. Beberapa sapinya mengalami diare dan produksi susu menurun. Setelah diperiksa, ternyata **air minum sapi terlalu asam** karena sumber air tercemar. Kalau ada sensor pH, Bu Ratna bisa tahu sejak awal sebelum sapi-sapinya sakit!

### 💡 Catatan Penting

> ⚠️ **Sensor pH probe belum tersedia di Wokwi**, jadi kita gunakan **Potentiometer** untuk simulasi. Putar knob = nilai pH berubah dari 0 (sangat asam) ke 14 (sangat basa).

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│          SISTEM MONITORING pH AIR MINUM TERNAK              │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🎛️ Potentiometer (simulasi sensor pH)                    │
│          ↓                                                  │
│   🧠 ESP32 membaca pH dan cek apakah aman                  │
│          ↓                                                  │
│   🔴 pH < 6.0 (Terlalu ASAM)  → LED Merah                  │
│   🟢 pH 6.5-8.5 (IDEAL)       → LED Hijau                  │
│   🔵 pH > 9.0 (Terlalu BASA)  → LED Biru                   │
│                                                             │
│   📟 LCD menampilkan nilai pH + status                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen           | Fungsi                 | Jumlah |
| --- | ------------------ | ---------------------- | ------ |
| 1   | **ESP32**          | Otak sistem            | 1      |
| 2   | **Potentiometer**  | Simulasi sensor pH     | 1      |
| 3   | **LCD 16x2 (I2C)** | Layar tampilan pH      | 1      |
| 4   | **LED Merah**      | Indikator terlalu ASAM | 1      |
| 5   | **LED Hijau**      | Indikator IDEAL        | 1      |
| 6   | **LED Biru**       | Indikator terlalu BASA | 1      |
| 7   | **Resistor 220Ω**  | Pelindung LED          | 3      |

### 🔌 Diagram Koneksi

```
                      ESP32
                ┌──────────────┐
  Potentiometer │              │
  ┌─────────┐   │              │
  │ VCC  ├──→│   3.3V       │
  │ SIG  ├──→│   GPIO 34    │  ← Baca pH (analog)
  │ GND  ├──→│   GND        │
  └─────────┘   │              │
                │              │
  LCD I2C       │              │
  ┌─────────┐   │              │
  │ VCC  ├──→│   5V         │
  │ GND  ├──→│   GND        │
  │ SDA  ├──→│   GPIO 21    │
  │ SCL  ├──→│   GPIO 22    │
  └─────────┘   │              │
                │   GPIO 2  ───→ LED Merah  → Resistor → GND
                │   GPIO 4  ───→ LED Hijau  → Resistor → GND
                │   GPIO 5  ───→ LED Biru   → Resistor → GND
                │              │
                └──────────────┘
```

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: Tambahkan Komponen

1. Klik **"+"** lalu tambahkan:
   - **Potentiometer**
   - **LCD1602** (pilih yang **I2C**)
   - **LED** × 3 buah (merah, hijau, biru)
   - **Resistor** × 3 buah (220Ω)

#### Langkah 3: Sambungkan sesuai diagram, lalu Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 🧪 SISTEM MONITORING pH AIR MINUM TERNAK
// ============================================================
// Alat ini membaca pH air minum ternak
// (disimulasikan dengan potentiometer).
// Memberi tahu apakah air aman diminum ternak.
// ============================================================

#include <LiquidCrystal_I2C.h>

// --- PENGATURAN PIN ---
const int PIN_SENSOR_PH = 34;    // Potentiometer (simulasi pH)
const int PIN_LED_ASAM = 2;      // LED Merah (terlalu asam)
const int PIN_LED_IDEAL = 4;     // LED Hijau (pH ideal)
const int PIN_LED_BASA = 5;      // LED Biru (terlalu basa)

// --- BATAS pH UNTUK AIR MINUM TERNAK ---
// pH ideal air minum ternak: 6.5 - 8.5
const float PH_TERLALU_ASAM = 6.0;
const float PH_BATAS_BAWAH = 6.5;
const float PH_BATAS_ATAS = 8.5;
const float PH_TERLALU_BASA = 9.0;

// Layar LCD
LiquidCrystal_I2C lcd(0x27, 16, 2);

void setup() {
  Serial.begin(115200);
  Serial.println("================================");
  Serial.println("🧪 MONITOR pH AIR MINUM TERNAK");
  Serial.println("================================");

  // Nyalakan LCD
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Monitor pH Air");
  lcd.setCursor(0, 1);
  lcd.print("Siap!");

  // Atur LED
  pinMode(PIN_LED_ASAM, OUTPUT);
  pinMode(PIN_LED_IDEAL, OUTPUT);
  pinMode(PIN_LED_BASA, OUTPUT);

  Serial.println("✅ Sensor pH siap!");
  delay(2000);
}

void loop() {
  // 1️⃣ BACA NILAI DARI POTENTIOMETER
  int nilaiMentah = analogRead(PIN_SENSOR_PH);
  // Ubah 0-4095 menjadi pH 0.0-14.0
  float nilaiPH = nilaiMentah * 14.0 / 4095.0;

  // 2️⃣ TAMPILKAN DI SERIAL MONITOR
  Serial.println("────────────────────────────────");
  Serial.print("🧪 pH Air Minum  : ");
  Serial.println(nilaiPH, 1);

  // 3️⃣ TAMPILKAN DI LCD
  lcd.clear();
  lcd.setCursor(0, 0);
  lcd.print("pH: ");
  lcd.print(nilaiPH, 1);

  lcd.setCursor(0, 1);

  // 4️⃣ CEK STATUS pH
  if (nilaiPH < PH_TERLALU_ASAM) {
    // 🔴 Terlalu ASAM!
    lcd.print("ASAM! Bahaya!");

    Serial.println("🔴 STATUS: ⚠️ Air TERLALU ASAM!");
    Serial.println("   → Pencernaan ternak terganggu");
    Serial.println("   → Tambahkan kapur/penetral");

    digitalWrite(PIN_LED_ASAM, HIGH);
    digitalWrite(PIN_LED_IDEAL, LOW);
    digitalWrite(PIN_LED_BASA, LOW);
  }
  else if (nilaiPH <= PH_BATAS_ATAS) {
    // 🟢 pH IDEAL
    lcd.print("IDEAL! Aman");

    Serial.println("🟢 STATUS: ✅ pH IDEAL, air aman!");

    digitalWrite(PIN_LED_ASAM, LOW);
    digitalWrite(PIN_LED_IDEAL, HIGH);
    digitalWrite(PIN_LED_BASA, LOW);
  }
  else if (nilaiPH > PH_TERLALU_BASA) {
    // 🔵 Terlalu BASA!
    lcd.print("BASA! Bahaya!");

    Serial.println("🔵 STATUS: ⚠️ Air TERLALU BASA!");
    Serial.println("   → Bisa iritasi saluran cerna");
    Serial.println("   → Periksa sumber air");

    digitalWrite(PIN_LED_ASAM, LOW);
    digitalWrite(PIN_LED_IDEAL, LOW);
    digitalWrite(PIN_LED_BASA, HIGH);
  }
  else {
    // 🟡 Mendekati batas
    lcd.print("Hati-hati!");

    Serial.println("🟡 STATUS: pH mendekati batas aman");
    Serial.println("   → Pantau terus!");

    digitalWrite(PIN_LED_ASAM, LOW);
    digitalWrite(PIN_LED_IDEAL, HIGH);
    digitalWrite(PIN_LED_BASA, LOW);
  }

  // Info tambahan berdasarkan jenis ternak
  Serial.println("   📋 Referensi pH ideal:");
  Serial.println("      Air minum ternak : 6.5 - 8.5");
  Serial.println("      Susu sapi segar  : 6.6 - 6.8");
  Serial.println("      Kolam ikan       : 6.5 - 8.0");

  Serial.println("");
  delay(1000);
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play**
2. Lihat **LCD** — akan menampilkan nilai pH dan statusnya
3. **Putar knob potentiometer** pelan-pelan:
   - Kiri (pH rendah) → 🔴 LED Merah: "ASAM! Bahaya!"
   - Tengah (pH 6.5-8.5) → 🟢 LED Hijau: "IDEAL! Aman"
   - Kanan (pH tinggi) → 🔵 LED Biru: "BASA! Bahaya!"

### 🧪 Eksperimen untuk Mahasiswa

> **Tantangan 1:** Ubah batas pH untuk **susu sapi** (6.6-6.8). Apakah rentangnya lebih sempit? Apa artinya bagi peternak sapi perah?

> **Tantangan 2:** Tambahkan peringatan khusus di Serial Monitor jika pH menunjukkan kemungkinan **mastitis** (pH susu > 6.8).

> **Tantangan 3:** Jika Anda peternak ikan lele, pH ideal kolam adalah 6.5-8.0. Ubah batas pH di kode dan uji coba!

### 📝 Lembar Pengamatan Praktik 4

| No  | Posisi Knob  | pH  | Tampilan LCD | LED Merah | LED Hijau | LED Biru | Status |
| --- | ------------ | --- | ------------ | --------- | --------- | -------- | ------ |
| 1   | Paling kiri  |     |              |           |           |          |        |
| 2   | ¼ putaran    |     |              |           |           |          |        |
| 3   | ½ putaran    |     |              |           |           |          |        |
| 4   | ¾ putaran    |     |              |           |           |          |        |
| 5   | Paling kanan |     |              |           |           |          |        |

### 🐔 Hubungan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          PRAKTIK vs DUNIA NYATA                             │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   Di Wokwi:                    Di Kandang:                 │
│                                                             │
│   🎛️ Potentiometer       →    🧪 pH Probe (Rp 100.000)    │
│   📟 LCD                 →    📱 Notifikasi ke HP          │
│   🔄 Putar knob          →    💧 Celup probe ke air       │
│                                                             │
│   💡 Di peternakan nyata, sensor pH dicelupkan ke:         │
│      • Tempat minum ternak                                 │
│      • Tangki air                                          │
│      • Susu segar (deteksi mastitis)                       │
│      • Kolam ikan                                          │
│                                                             │
│   💰 pH Sensor + ESP32 ≈ Rp 150.000                        │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 🔗 PROYEK GABUNGAN: Sistem Monitoring Kandang Lengkap

### 🐔 Skenario Peternakan

> Sekarang kita akan menjadi **"insinyur IoT peternakan"**! Bayangkan Anda diminta merancang sistem monitoring untuk kandang ayam Bu Ani yang punya 10.000 ekor. Sistem ini harus bisa memantau **suhu, kelembaban, gas amonia, DAN pH air** sekaligus — semua dalam satu alat!

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│       🏠 SISTEM MONITORING KANDANG LENGKAP                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🌡️ DHT22          → Suhu + Kelembaban                    │
│   🎛️ Potentiometer 1 → Simulasi Gas Amonia                 │
│   🎛️ Potentiometer 2 → Simulasi pH Air                     │
│          ↓                                                  │
│   🧠 ESP32 (menganalisis semua data)                       │
│          ↓                                                  │
│   📟 LCD        → Tampilkan data bergantian                │
│   🟢🟡🔴 LED   → Indikator status keseluruhan              │
│   🔊 Buzzer     → Alarm jika ada bahaya                    │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan

| No  | Komponen           | Fungsi                   | Jumlah |
| --- | ------------------ | ------------------------ | ------ |
| 1   | **ESP32**          | Otak sistem              | 1      |
| 2   | **DHT22**          | Sensor suhu & kelembaban | 1      |
| 3   | **Potentiometer**  | Simulasi sensor gas & pH | 2      |
| 4   | **LCD 16x2 (I2C)** | Layar tampilan data      | 1      |
| 5   | **LED**            | Hijau, Kuning, Merah     | 3      |
| 6   | **Buzzer**         | Alarm                    | 1      |
| 7   | **Resistor 220Ω**  | Pelindung LED            | 3      |

### 🔌 Diagram Koneksi

```
                        ESP32
                  ┌──────────────┐
  DHT22           │              │
  ┌─────┐         │              │
  │ DATA├────→   │   GPIO 15    │
  │ VCC ├────→   │   3.3V       │
  │ GND ├────→   │   GND        │
  └─────┘         │              │
                  │              │
  Pot 1 (Gas)     │              │
  ┌─────┐         │              │
  │ SIG ├────→   │   GPIO 34    │
  └─────┘         │              │
                  │              │
  Pot 2 (pH)      │              │
  ┌─────┐         │              │
  │ SIG ├────→   │   GPIO 35    │
  └─────┘         │              │
                  │              │
  LCD I2C         │              │
  ┌─────┐         │              │
  │ SDA ├────→   │   GPIO 21    │
  │ SCL ├────→   │   GPIO 22    │
  └─────┘         │              │
                  │   GPIO 2  ───→ LED Hijau
                  │   GPIO 4  ───→ LED Kuning
                  │   GPIO 5  ───→ LED Merah
                  │   GPIO 18 ───→ Buzzer
                  │              │
                  └──────────────┘
```

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 🏠 SISTEM MONITORING KANDANG LENGKAP
// ============================================================
// Menggabungkan SEMUA sensor yang sudah kita pelajari:
// - DHT22 (Suhu + Kelembaban)
// - Potentiometer 1 (Simulasi Gas Amonia)
// - Potentiometer 2 (Simulasi pH Air)
// Dengan output: LCD + 3 LED + Buzzer
// ============================================================

#include "DHTesp.h"
#include <LiquidCrystal_I2C.h>

// --- PENGATURAN PIN ---
const int PIN_DHT = 15;          // Sensor suhu & kelembaban
const int PIN_GAS = 34;          // Potentiometer 1 (gas)
const int PIN_PH = 35;           // Potentiometer 2 (pH)
const int PIN_LED_AMAN = 2;      // LED Hijau
const int PIN_LED_WASPADA = 4;   // LED Kuning
const int PIN_LED_BAHAYA = 5;    // LED Merah
const int PIN_BUZZER = 18;       // Buzzer

// --- BATAS-BATAS AMAN ---
const float SUHU_MAKS = 32.0;       // °C
const float KELEMBABAN_MAKS = 80.0;  // %
const int GAS_WASPADA = 25;          // ppm
const int GAS_BAHAYA = 50;           // ppm
const float PH_MIN = 6.5;
const float PH_MAKS = 8.5;

// Inisialisasi sensor dan LCD
DHTesp dht;
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Variabel untuk tampilan bergantian di LCD
int tampilanKe = 0;

void setup() {
  Serial.begin(115200);
  Serial.println("╔════════════════════════════════════╗");
  Serial.println("║  🏠 MONITORING KANDANG LENGKAP     ║");
  Serial.println("╚════════════════════════════════════╝");

  // Setup sensor DHT22
  dht.setup(PIN_DHT, DHTesp::DHT22);

  // Setup LCD
  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0);
  lcd.print("Smart Kandang");
  lcd.setCursor(0, 1);
  lcd.print("Loading...");

  // Setup LED dan Buzzer
  pinMode(PIN_LED_AMAN, OUTPUT);
  pinMode(PIN_LED_WASPADA, OUTPUT);
  pinMode(PIN_LED_BAHAYA, OUTPUT);
  pinMode(PIN_BUZZER, OUTPUT);

  Serial.println("✅ Semua sensor siap!");
  delay(2000);
}

void loop() {
  // ═══════════════════════════════════════
  // 1️⃣ BACA SEMUA SENSOR
  // ═══════════════════════════════════════
  float suhu = dht.getTemperature();
  float kelembaban = dht.getHumidity();

  int nilaiGasMentah = analogRead(PIN_GAS);
  int kadarAmonia = map(nilaiGasMentah, 0, 4095, 0, 100);

  int nilaiPhMentah = analogRead(PIN_PH);
  float nilaiPH = nilaiPhMentah * 14.0 / 4095.0;

  // Cek sensor DHT
  if (isnan(suhu)) suhu = 0;
  if (isnan(kelembaban)) kelembaban = 0;

  // ═══════════════════════════════════════
  // 2️⃣ TAMPILKAN DI SERIAL MONITOR
  // ═══════════════════════════════════════
  Serial.println("════════════════════════════════════");
  Serial.println("📊 LAPORAN KONDISI KANDANG");
  Serial.println("────────────────────────────────────");
  Serial.print("🌡️ Suhu         : "); Serial.print(suhu, 1); Serial.println(" °C");
  Serial.print("💧 Kelembaban   : "); Serial.print(kelembaban, 1); Serial.println(" %");
  Serial.print("💨 Amonia       : "); Serial.print(kadarAmonia); Serial.println(" ppm");
  Serial.print("🧪 pH Air       : "); Serial.println(nilaiPH, 1);

  // ═══════════════════════════════════════
  // 3️⃣ ANALISIS: Hitung jumlah masalah
  // ═══════════════════════════════════════
  int jumlahMasalah = 0;
  String masalah = "";

  if (suhu >= SUHU_MAKS) {
    jumlahMasalah++;
    masalah += "Suhu! ";
  }
  if (kelembaban > KELEMBABAN_MAKS) {
    jumlahMasalah++;
    masalah += "Lembab! ";
  }
  if (kadarAmonia >= GAS_BAHAYA) {
    jumlahMasalah++;
    masalah += "Gas! ";
  }
  if (nilaiPH < PH_MIN || nilaiPH > PH_MAKS) {
    jumlahMasalah++;
    masalah += "pH! ";
  }

  // ═══════════════════════════════════════
  // 4️⃣ TENTUKAN STATUS KESELURUHAN
  // ═══════════════════════════════════════
  Serial.println("────────────────────────────────────");

  if (jumlahMasalah == 0) {
    Serial.println("🟢 KONDISI KANDANG: ✅ SEMUA AMAN");
    digitalWrite(PIN_LED_AMAN, HIGH);
    digitalWrite(PIN_LED_WASPADA, LOW);
    digitalWrite(PIN_LED_BAHAYA, LOW);
    digitalWrite(PIN_BUZZER, LOW);
  }
  else if (jumlahMasalah == 1) {
    Serial.print("🟡 KONDISI KANDANG: ⚠️ WASPADA - ");
    Serial.println(masalah);
    digitalWrite(PIN_LED_AMAN, LOW);
    digitalWrite(PIN_LED_WASPADA, HIGH);
    digitalWrite(PIN_LED_BAHAYA, LOW);
    digitalWrite(PIN_BUZZER, LOW);
  }
  else {
    Serial.print("🔴 KONDISI KANDANG: 🚨 BAHAYA! - ");
    Serial.println(masalah);
    digitalWrite(PIN_LED_AMAN, LOW);
    digitalWrite(PIN_LED_WASPADA, LOW);
    digitalWrite(PIN_LED_BAHAYA, HIGH);
    // Alarm buzzer!
    digitalWrite(PIN_BUZZER, HIGH);
    delay(150);
    digitalWrite(PIN_BUZZER, LOW);
  }

  // ═══════════════════════════════════════
  // 5️⃣ TAMPILKAN DI LCD (bergantian)
  // ═══════════════════════════════════════
  lcd.clear();

  switch (tampilanKe) {
    case 0:
      lcd.setCursor(0, 0);
      lcd.print("Suhu: ");
      lcd.print(suhu, 1);
      lcd.print(" C");
      lcd.setCursor(0, 1);
      lcd.print("Lembab: ");
      lcd.print(kelembaban, 1);
      lcd.print(" %");
      break;
    case 1:
      lcd.setCursor(0, 0);
      lcd.print("Amonia: ");
      lcd.print(kadarAmonia);
      lcd.print(" ppm");
      lcd.setCursor(0, 1);
      lcd.print("pH Air: ");
      lcd.print(nilaiPH, 1);
      break;
    case 2:
      lcd.setCursor(0, 0);
      if (jumlahMasalah == 0) lcd.print("KANDANG: AMAN!");
      else if (jumlahMasalah == 1) lcd.print("KANDANG: WASPADA");
      else lcd.print("KANDANG: BAHAYA!");
      lcd.setCursor(0, 1);
      lcd.print("Masalah: ");
      lcd.print(jumlahMasalah);
      break;
  }

  // Ganti tampilan setiap 2 detik
  tampilanKe = (tampilanKe + 1) % 3;

  Serial.println("");
  delay(2000);
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play**
2. Amati **LCD** — data bergantian setiap 2 detik:
   - Halaman 1: Suhu + Kelembaban
   - Halaman 2: Gas Amonia + pH Air
   - Halaman 3: Status keseluruhan kandang
3. Coba buat beberapa skenario:

| Skenario     | DHT22     | Pot 1 (Gas) | Pot 2 (pH) | Hasil              |
| ------------ | --------- | ----------- | ---------- | ------------------ |
| Semua aman   | 25°C, 60% | Kiri        | Tengah     | 🟢 AMAN            |
| Suhu panas   | 36°C      | Kiri        | Tengah     | 🟡 WASPADA         |
| Suhu + Gas   | 36°C      | Kanan       | Tengah     | 🔴 BAHAYA + Buzzer |
| Semua bahaya | 36°C      | Kanan       | Kiri       | 🔴 BAHAYA + Buzzer |

### 🧪 Tantangan Akhir

> **Tantangan Boss:** Bayangkan Anda adalah tim IoT yang diminta merancang sistem untuk **peternakan sapi perah**. Ubah semua batas aman (suhu, kelembaban, gas, pH) sesuai kebutuhan sapi! Gunakan tabel di materi teori sebagai panduan.

---

## 📝 Rangkuman Keseluruhan Praktikum

```
┌─────────────────────────────────────────────────────────────┐
│         RINGKASAN PRAKTIKUM SENSOR WOKWI                   │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Praktik 1️⃣  DHT22 → Suhu & Kelembaban + LED Alarm        │
│  Praktik 2️⃣  Potentiometer → Simulasi Gas + 3 LED + Buzzer│
│  Praktik 3️⃣  Potentiometer → Simulasi Berat + LCD         │
│  Praktik 4️⃣  Potentiometer → Simulasi pH + 3 LED + LCD    │
│  Gabungan 🔗  Semua sensor → Monitoring Kandang Lengkap    │
│                                                             │
│  💡 PELAJARAN UTAMA:                                        │
│  • Sensor membaca kondisi lingkungan → DATA                │
│  • Mikrokontroler menganalisis data  → KEPUTUSAN           │
│  • LED/Buzzer/LCD memberi tahu kita  → AKSI                │
│  • Ini adalah INTI dari Internet of Things!                 │
│                                                             │
│  💰 ESTIMASI BIAYA SISTEM NYATA:                            │
│  • ESP32            : Rp  50.000                           │
│  • DHT22            : Rp  35.000                           │
│  • MQ-135 (gas)     : Rp  25.000                           │
│  • Load Cell+HX711  : Rp  30.000                           │
│  • pH Sensor        : Rp 100.000                           │
│  • LCD + LED + Kabel: Rp  30.000                           │
│  ─────────────────────────────                             │
│  • TOTAL            : ± Rp 270.000                         │
│                                                             │
│  🐔 Dengan Rp 270.000, Anda bisa memantau:                 │
│     Suhu, Kelembaban, Gas, Berat, dan pH                   │
│     → 24 jam nonstop, dari mana saja!                      │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

_Materi praktikum ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_  
_Semester Genap 2025/2026_
