# ⚙️ Pertemuan 4: Praktikum Aktuator & Mikrokontroler (WOKWI)

> **"Sensor membaca, Mikrokontroler berpikir, Aktuator BERTINDAK — hari ini kita buat kandang pintar yang bisa bergerak sendiri!"**

---

## 👨‍🏫 Dosen Pengampu

- **Anton Prafanto** / **Anhar** (Kelas A / Kelas B)

---

## 📋 Informasi Tugas Kelompok

> 🎯 **Pertemuan ini adalah Self-Paced Learning Berkelompok!**
>
> Mahasiswa belajar secara mandiri dalam kelompok menggunakan simulator Wokwi, kemudian merekam dan mengunggah **video presentasi ke YouTube** sebagai bukti hasil belajar.

| Aspek        | Keterangan                                             |
| ------------ | ------------------------------------------------------ |
| **Mode**     | Self-Paced Learning Berkelompok                        |
| **Anggota**  | 3–4 orang per kelompok                                 |
| **Platform** | [wokwi.com](https://wokwi.com) (gratis, tanpa instal)  |
| **Output 1** | Link proyek Wokwi (share link tiap praktik)            |
| **Output 2** | Video presentasi YouTube (Unlisted, durasi 7–10 menit) |
| **Deadline** | Sebelum Pertemuan 5 (dikumpulkan via form/LMS)         |

---

## 🎯 Tujuan Praktikum

Setelah praktikum ini, mahasiswa mampu:

1. Merangkai dan memprogram **relay** sebagai saklar otomatis di Wokwi
2. Merangkai dan memprogram **servo motor** untuk kontrol posisi
3. Mengintegrasikan **sensor + aktuator** dalam satu sistem otomatis
4. Menjelaskan kaitan setiap rangkaian dengan kebutuhan peternakan nyata

---

## 🔁 Review Singkat: Mengingat Wokwi

Sudah lupa cara pakai Wokwi? Ingat kembali:

1. Buka **[wokwi.com](https://wokwi.com)** di browser
2. Klik **"New Project"** → Pilih **"ESP32"**
3. Klik tombol **"+" (Add Component)** untuk menambah komponen
4. **Copy-paste kode** ke area kode (kiri), lalu klik **▶️ Play**
5. Lihat hasil di **Serial Monitor** (bawah layar) dan **area rangkaian** (kanan)

---

## 🌀 PRAKTIK 1: Relay — Kipas Otomatis Kandang

### 🐔 Skenario Peternakan

> Pak Hendra punya kandang ayam broiler 8.000 ekor. Di musim kemarau, suhu bisa mencapai 38°C pada siang hari. Pak Hendra kelelahan harus bolak-balik menyalakan dan mematikan kipas exhaust secara manual. **Bagaimana jika kipas bisa menyala dan mati sendiri sesuai suhu?**

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│        SISTEM KIPAS OTOMATIS KANDANG (RELAY)                │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🌡️ DHT22 membaca suhu kandang                            │
│          ↓                                                  │
│   🧠 ESP32 memutuskan: perlu kipas atau tidak?             │
│          ↓                                                  │
│   < 28°C  → 🔵 Relay OFF → 🌀 Kipas MATI (hemat listrik)  │
│   28–32°C → 🟡 Relay ON  → 🌀 Kipas 1 NYALA               │
│   > 32°C  → 🔴 Relay ON  → 🌀 Kipas 1 + 2 NYALA + ALARM   │
│                                                             │
│   📟 Serial Monitor menampilkan log real-time              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen          | Fungsi                          | Jumlah |
| --- | ----------------- | ------------------------------- | ------ |
| 1   | **ESP32**         | Mikrokontroler (otak sistem)    | 1      |
| 2   | **DHT22**         | Sensor suhu & kelembaban        | 1      |
| 3   | **LED Biru**      | Simulasi Kipas 1 (fase normal)  | 1      |
| 4   | **LED Merah**     | Simulasi Kipas 2 (fase darurat) | 1      |
| 5   | **LED Hijau**     | Indikator sistem aktif / aman   | 1      |
| 6   | **Buzzer**        | Alarm suhu darurat              | 1      |
| 7   | **Resistor 220Ω** | Pelindung setiap LED            | 3      |

> 💡 **Catatan:** Di Wokwi, kita simulasikan relay dengan LED. LED Biru = kipas 1 menyala, LED Merah = kipas 2 menyala. Di dunia nyata, ini diganti dengan Relay yang mengontrol kipas 220V.

### 🔌 Diagram Koneksi

<img width="1134" height="693" alt="image" src="https://github.com/user-attachments/assets/dedb76a2-5e50-40d1-81a9-028e484260d8" />

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: ⚠️ Install Library DHT (WAJIB!)

> 🚨 **Jangan dilewatkan!** Kode ini menggunakan library `DHTesp.h` yang harus diinstall terlebih dahulu.

1. Di bagian atas Wokwi, klik tab **"Library Manager"**
2. Klik tombol **"+" biru** (pojok kanan atas)
3. Ketik **`DHT sensor library for ESPx`** → klik **Install**

#### Langkah 3: Tambahkan Komponen

1. Klik **"+"** lalu tambahkan satu per satu:
   - **DHT22** (ketik "dht22")
   - **LED** × 3 buah — atur warna: **Hijau**, **Biru**, **Merah**
   - **Resistor** × 3 buah (nilai: **220Ω**)
   - **Buzzer** (ketik "buzzer")

#### Langkah 4: Sambungkan Kabel

Sambungkan sesuai diagram koneksi di atas. Pastikan:

- DHT22 DATA → GPIO 15
- LED Hijau → GPIO 2 → Resistor → GND
- LED Biru → GPIO 4 → Resistor → GND
- LED Merah → GPIO 5 → Resistor → GND
- Buzzer (+) → GPIO 18, Buzzer (–) → GND

#### Langkah 5: Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 🌀 SISTEM KIPAS OTOMATIS KANDANG
// Menggunakan Relay (disimulasikan dengan LED) + DHT22
// ============================================================
// Cara kerja:
//   Suhu < 28°C  → Semua kipas mati, kandang aman
//   28-32°C      → Kipas 1 menyala (cooling tahap 1)
//   Suhu > 32°C  → Kipas 1 + 2 menyala + Alarm berbunyi!
// ============================================================

#include "DHTesp.h"

// --- PENGATURAN PIN ---
const int PIN_SENSOR   = 15;   // DHT22
const int PIN_AMAN     = 2;    // LED Hijau (indikator aman)
const int PIN_KIPAS_1  = 4;    // LED Biru  (simulasi Relay Kipas 1)
const int PIN_KIPAS_2  = 5;    // LED Merah (simulasi Relay Kipas 2)
const int PIN_ALARM    = 18;   // Buzzer

// --- BATAS SUHU KANDANG (°C) ---
// Ayam broiler: nyaman 21-27°C, waspada 28-32°C, darurat >32°C
const float SUHU_WASPADA = 28.0;  // °C ke atas → Kipas 1 menyala
const float SUHU_DARURAT = 32.0;  // °C ke atas → Kipas 2 + Alarm

DHTesp sensorSuhu;

// Fungsi nyalakan alarm putus-putus
void bunyikanAlarm() {
  for (int i = 0; i < 3; i++) {
    tone(PIN_ALARM, 900);  // Aktifkan buzzer frekuensi 900Hz
    delay(150);
    tone(PIN_ALARM, 0);    // Matikan buzzer
    delay(150);
  }
}

void setup() {
  Serial.begin(115200);
  Serial.println("============================================");
  Serial.println("  🌀 SISTEM KIPAS OTOMATIS KANDANG AYAM");
  Serial.println("============================================");

  pinMode(PIN_AMAN,    OUTPUT);
  pinMode(PIN_KIPAS_1, OUTPUT);
  pinMode(PIN_KIPAS_2, OUTPUT);
  // Catatan: PIN_ALARM (buzzer) tidak perlu pinMode saat menggunakan tone()

  sensorSuhu.setup(PIN_SENSOR, DHTesp::DHT22);

  Serial.println("✅ Sistem aktif! Memantau suhu kandang...");
  Serial.println("");
}

void loop() {
  // 1️⃣ BACA SENSOR
  float suhu      = sensorSuhu.getTemperature();
  float kelembaban = sensorSuhu.getHumidity();

  if (isnan(suhu) || isnan(kelembaban)) {
    Serial.println("❌ Sensor error! Periksa kabel DHT22.");
    delay(2000);
    return;
  }

  // 2️⃣ TAMPILKAN DATA
  Serial.println("────────────────────────────────────────────");
  Serial.print("🌡️  Suhu Kandang  : "); Serial.print(suhu, 1);     Serial.println(" °C");
  Serial.print("💧 Kelembaban    : "); Serial.print(kelembaban, 1); Serial.println(" %");

  // 3️⃣ LOGIKA KONTROL RELAY (KIPAS)
  if (suhu > SUHU_DARURAT) {
    // 🔴 DARURAT: Suhu > 32°C, Kipas 1 + 2 ON + Alarm
    Serial.println("🔴 STATUS: 🚨 DARURAT! Suhu sangat panas!");
    Serial.println("   → Kipas 1 & 2 dinyalakan penuh!");
    Serial.println("   → Alarm berbunyi! Segera cek kandang!");

    digitalWrite(PIN_AMAN,    LOW);
    digitalWrite(PIN_KIPAS_1, HIGH);  // Kipas 1 ON
    digitalWrite(PIN_KIPAS_2, HIGH);  // Kipas 2 ON
    bunyikanAlarm();

  } else if (suhu >= SUHU_WASPADA) {
    // 🟡 WASPADA: Suhu 28-32°C, Kipas 1 ON, Kipas 2 OFF
    Serial.println("🟡 STATUS: ⚠️  Waspada! Kipas 1 dinyalakan.");
    Serial.println("   → Memantau perkembangan suhu...");

    digitalWrite(PIN_AMAN,    LOW);
    digitalWrite(PIN_KIPAS_1, HIGH);  // Kipas 1 ON
    digitalWrite(PIN_KIPAS_2, LOW);   // Kipas 2 OFF
    digitalWrite(PIN_ALARM,   LOW);

  } else {
    // 🟢 AMAN: Suhu < 28°C, semua kipas OFF
    Serial.println("🟢 STATUS: ✅ Aman! Suhu normal, kipas mati.");

    digitalWrite(PIN_AMAN,    HIGH);  // LED Hijau ON
    digitalWrite(PIN_KIPAS_1, LOW);   // Kipas 1 OFF
    digitalWrite(PIN_KIPAS_2, LOW);   // Kipas 2 OFF
    digitalWrite(PIN_ALARM,   LOW);
  }

  Serial.println("");
  delay(2000);  // Baca tiap 2 detik
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play** di Wokwi
2. Lihat **Serial Monitor** — log suhu akan muncul setiap 2 detik
3. **Klik sensor DHT22** di rangkaian → muncul slider suhu dan kelembaban
4. Geser suhu dan amati perubahan LED:
   - Suhu < 28°C → 🟢 LED Hijau menyala
   - Suhu 28–32°C → 🔵 LED Biru (Kipas 1) menyala
   - Suhu > 32°C → 🔵🔴 Dua LED + 🔊 Buzzer berbunyi

### 🧪 Eksperimen untuk Kelompok Anda

> **Tantangan 1:** Ubah `SUHU_DARURAT` dari 32°C menjadi **35°C** (sesuaikan untuk kandang kambing). Amati perbedaan responsnya!

> **Tantangan 2:** Ubah alarm dari 3x bunyi menjadi **5x bunyi** dengan jeda berbeda (100ms on, 200ms off). Sesuaikan fungsi `bunyikanAlarm()`.

> **Tantangan 3:** Tambahkan peringatan di Serial Monitor jika kelembaban melebihi **80%** (risiko penyakit pernapasan). Petunjuk: tambahkan `if (kelembaban > 80.0)` setelah bagian cek suhu.

### 📝 Lembar Pengamatan Praktik 1

Isi tabel berikut bersama kelompok, lalu fotret/screenshot sebagai dokumentasi:

| No  | Suhu (°C) | Kelembaban (%) | LED Hijau | LED Biru (Kipas 1) | LED Merah (Kipas 2) | Buzzer | Status Serial Monitor |
| --- | --------- | -------------- | --------- | ------------------ | ------------------- | ------ | --------------------- |
| 1   | 25        |                |           |                    |                     |        |                       |
| 2   | 28        |                |           |                    |                     |        |                       |
| 3   | 33        |                |           |                    |                     |        |                       |
| 4   | 35        |                |           |                    |                     |        |                       |
| 5   | 28        | 85             |           |                    |                     |        |                       |

### 🐔 Kaitan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          DI WOKWI  →  DI KANDANG NYATA                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🌡️ DHT22 (virtual)   →  🌡️ DHT22 asli (Rp 35.000)        │
│  🔵 LED Biru (Kipas 1) →  ⚡ Relay 1 + Kipas 220V          │
│  🔴 LED Merah (Kipas 2) → ⚡ Relay 2 + Kipas 220V          │
│  🔊 Buzzer (virtual)   →  🚨 Sirene kandang                │
│  🖱️ Geser slider suhu  →  🌤️ Perubahan cuaca nyata        │
│                                                             │
│  💰 Biaya hardware nyata: ± Rp 200.000                     │
│     (ESP32 + DHT22 + Relay 2ch + Buzzer + kabel)           │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 📐 PRAKTIK 2: Servo Motor — Pintu Kandang Otomatis

### 🐔 Skenario Peternakan

> Bu Lina memiliki kandang ayam petelur (layer) 2.000 ekor. Setiap pagi jam 06.00, pintu kecil kandang harus dibuka agar ayam bisa keluar ke area jalan-jalan (_free range_). Jam 18.00 harus ditutup agar predator tidak masuk. Bu Lina sering lupa, dan dua kali kandangnya dimasuki musang. **Bagaimana membuat pintu yang bisa buka-tutup otomatis sesuai jadwal?**

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│       SISTEM PINTU KANDANG OTOMATIS (SERVO MOTOR)           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🌡️ DHT22 membaca kondisi lingkungan                      │
│          ↓                                                  │
│   🧠 ESP32 simulasikan waktu & kondisi                     │
│          ↓                                                  │
│   Tekan tombol BUKA  → 📐 Servo 0°   (pintu TERBUKA)      │
│   Tekan tombol TUTUP → 📐 Servo 90°  (pintu TERTUTUP)     │
│   Suhu > 38°C        → 📐 Servo 45°  (pintu SETENGAH)     │
│                                                             │
│   📟 Serial Monitor menampilkan sudut servo & kondisi      │
│   💡 LED menunjukkan status pintu                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen               | Fungsi                           | Jumlah |
| --- | ---------------------- | -------------------------------- | ------ |
| 1   | **ESP32**              | Mikrokontroler                   | 1      |
| 2   | **Servo Motor (SG90)** | Aktuator pintu kandang           | 1      |
| 3   | **DHT22**              | Sensor suhu (kondisi lingkungan) | 1      |
| 4   | **Push Button**        | Tombol buka/tutup manual pintu   | 2      |
| 5   | **LED Hijau**          | Indikator pintu TERBUKA          | 1      |
| 6   | **LED Merah**          | Indikator pintu TERTUTUP         | 1      |
| 7   | **Resistor 10kΩ**      | Pull-down untuk tombol           | 2      |
| 8   | **Resistor 220Ω**      | Pelindung LED                    | 2      |

### 🔌 Diagram Koneksi

<img width="1054" height="678" alt="image" src="https://github.com/user-attachments/assets/e521f674-faf3-4d3f-a097-802d8f02ecd8" />

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: ⚠️ Install Library ESP32Servo (WAJIB!)

> 🚨 **Jangan dilewatkan!** Tanpa langkah ini, kode tidak akan bisa dikompilasi dan akan muncul error **"ESP32Servo.h: No such file or directory"**.

1. Di bagian atas Wokwi, klik tab **"Library Manager"**
2. Klik tombol **"+" biru** (pojok kanan atas)
3. Cari dan install **`ESP32Servo`** → klik Install
4. Klik **"+"** lagi, cari dan install **`DHT sensor library for ESPx`** → klik Install

#### Langkah 3: Tambahkan Komponen

1. Klik **"+"** lalu tambahkan:
   - **Servo** (ketik "servo" → pilih **"Servo"**)
   - **DHT22** (ketik "dht22")
   - **Pushbutton** × 2 buah (ketik "pushbutton")
   - **LED** × 2 buah (Hijau dan Merah)
   - **Resistor** × 4 buah (2 buah **220Ω** untuk LED, 2 buah **10kΩ** untuk tombol)

#### Langkah 4: Sambungkan Kabel

Sambungkan sesuai diagram di atas. Perhatikan:

- Kabel oranye/sinyal servo → GPIO 13
- Setiap tombol: satu kaki → GPIO, kaki lain → 3.3V, dengan resistor 10kΩ dari GPIO ke GND (pull-down)

> ⚠️ **Catatan Wokwi untuk Tombol:** Di Wokwi, saat Anda klik tombol **Pushbutton**, tombol aktif selama diklik dan **langsung melepas** saat kursor dilepas. Ini normal dan mensimulasikan perilaku tombol fisik. Kode menggunakan `INPUT_PULLDOWN` sehingga kondisi **tombol ditekan = HIGH**, tombol bebas = LOW.

#### Langkah 5: Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 📐 SISTEM PINTU KANDANG OTOMATIS (SERVO MOTOR)
// ============================================================
// Cara kerja:
//   Tombol BUKA ditekan  → Servo ke 0°   (pintu terbuka penuh)
//   Tombol TUTUP ditekan → Servo ke 90°  (pintu tertutup)
//   Suhu > 38°C          → Servo ke 45°  (pintu dibuka sebagian
//                                          agar ada sirkulasi)
// ============================================================

#include <ESP32Servo.h>
#include "DHTesp.h"

// --- PENGATURAN PIN ---
const int PIN_SERVO      = 13;   // Motor servo
const int PIN_SENSOR     = 15;   // DHT22
const int PIN_BTN_BUKA   = 25;   // Tombol BUKA pintu
const int PIN_BTN_TUTUP  = 26;   // Tombol TUTUP pintu
const int PIN_LED_BUKA   = 2;    // LED Hijau (pintu terbuka)
const int PIN_LED_TUTUP  = 4;    // LED Merah (pintu tertutup)

// --- POSISI SERVO ---
const int POS_TERBUKA    =  0;   // Derajat: pintu terbuka penuh
const int POS_SETENGAH   = 45;   // Derajat: pintu terbuka sebagian
const int POS_TERTUTUP   = 90;   // Derajat: pintu tertutup

// --- SUHU DARURAT PANAS ---
const float SUHU_PANAS   = 38.0; // Di atas ini → buka pintu sebagian

Servo servoPintu;
DHTesp sensorSuhu;

int posisiSekarang  = POS_TERTUTUP;  // Default: pintu tertutup
String statusPintu  = "TERTUTUP";

// Fungsi gerakkan servo perlahan (lebih halus, mirip pintu nyata)
void gerakkanServoPerlahan(int dari, int ke) {
  if (dari < ke) {
    for (int pos = dari; pos <= ke; pos++) {
      servoPintu.write(pos);
      delay(15);
    }
  } else {
    for (int pos = dari; pos >= ke; pos--) {
      servoPintu.write(pos);
      delay(15);
    }
  }
}

// Fungsi buka pintu
void bukaPintu(int derajat, String alasan) {
  Serial.println("────────────────────────────────────────────");
  Serial.print("🚪 Membuka pintu ke "); Serial.print(derajat); Serial.println("°");
  Serial.print("   Alasan: "); Serial.println(alasan);

  gerakkanServoPerlahan(posisiSekarang, derajat);
  posisiSekarang = derajat;
  statusPintu = (derajat == POS_TERBUKA) ? "TERBUKA PENUH" : "TERBUKA SEBAGIAN";

  digitalWrite(PIN_LED_BUKA,  HIGH);
  digitalWrite(PIN_LED_TUTUP, LOW);
  Serial.print("✅ Pintu sekarang: "); Serial.println(statusPintu);
}

// Fungsi tutup pintu
void tutupPintu(String alasan) {
  Serial.println("────────────────────────────────────────────");
  Serial.println("🚪 Menutup pintu...");
  Serial.print("   Alasan: "); Serial.println(alasan);

  gerakkanServoPerlahan(posisiSekarang, POS_TERTUTUP);
  posisiSekarang = POS_TERTUTUP;
  statusPintu = "TERTUTUP";

  digitalWrite(PIN_LED_BUKA,  LOW);
  digitalWrite(PIN_LED_TUTUP, HIGH);
  Serial.println("✅ Pintu sekarang: TERTUTUP RAPAT");
}

void setup() {
  Serial.begin(115200);
  Serial.println("============================================");
  Serial.println("  🚪 SISTEM PINTU KANDANG OTOMATIS");
  Serial.println("============================================");

  // Setup servo
  servoPintu.attach(PIN_SERVO);
  servoPintu.write(POS_TERTUTUP);  // Posisi awal: tutup

  // Setup sensor
  sensorSuhu.setup(PIN_SENSOR, DHTesp::DHT22);

  // Setup tombol (INPUT_PULLDOWN = tombol aktif HIGH saat ditekan)
  pinMode(PIN_BTN_BUKA,  INPUT_PULLDOWN);
  pinMode(PIN_BTN_TUTUP, INPUT_PULLDOWN);

  // Setup LED
  pinMode(PIN_LED_BUKA,  OUTPUT);
  pinMode(PIN_LED_TUTUP, OUTPUT);

  // Default: pintu tutup, LED merah menyala
  digitalWrite(PIN_LED_BUKA,  LOW);
  digitalWrite(PIN_LED_TUTUP, HIGH);

  Serial.println("✅ Sistem aktif! Pintu awal: TERTUTUP");
  Serial.println("   Tekan Tombol BUKA / TUTUP untuk kontrol manual");
  Serial.println("");
}

void loop() {
  // 1️⃣ BACA TOMBOL
  bool tombolBuka  = digitalRead(PIN_BTN_BUKA);
  bool tombolTutup = digitalRead(PIN_BTN_TUTUP);

  // 2️⃣ BACA SENSOR SUHU
  float suhu = sensorSuhu.getTemperature();

  // 3️⃣ PROSES KONTROL PINTU
  if (tombolBuka == HIGH && posisiSekarang != POS_TERBUKA) {
    // Tombol BUKA ditekan
    bukaPintu(POS_TERBUKA, "Tombol manual ditekan");
    delay(300);  // Anti double-press (debounce)

  } else if (tombolTutup == HIGH && posisiSekarang != POS_TERTUTUP) {
    // Tombol TUTUP ditekan
    tutupPintu("Tombol manual ditekan");
    delay(300);

  } else if (!isnan(suhu) && suhu > SUHU_PANAS && posisiSekarang == POS_TERTUTUP) {
    // Suhu darurat: buka sebagian untuk sirkulasi udara
    Serial.println("🌡️  Suhu darurat terdeteksi!");
    bukaPintu(POS_SETENGAH, "Suhu > 38°C, buka sebagian untuk ventilasi");
  }

  // 4️⃣ TAMPILKAN STATUS BERKALA
  if (!isnan(suhu)) {
    Serial.println("────────────────────────────────────────────");
    Serial.print("🌡️  Suhu         : "); Serial.print(suhu, 1); Serial.println(" °C");
    Serial.print("🚪 Status Pintu : "); Serial.println(statusPintu);
    Serial.print("📐 Sudut Servo  : "); Serial.print(posisiSekarang); Serial.println("°");
    Serial.println("");
  }

  delay(500);
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play**
2. Lihat posisi servo di area rangkaian (akan bergerak ke 90° secara default)
3. **Klik Tombol BUKA** → servo perlahan bergerak ke 0° (pintu terbuka)
4. **Klik Tombol TUTUP** → servo perlahan kembali ke 90° (pintu tertutup)
5. Geser suhu DHT22 di atas **38°C** → servo otomatis ke 45° (ventilasi darurat)

### 🧪 Eksperimen untuk Kelompok Anda

> **Tantangan 1:** Ubah `POS_TERTUTUP` dari 90° menjadi **120°** (untuk pintu dengan sudut berbeda). Amati perubahan gerakan servo!

> **Tantangan 2:** Ubah kecepatan gerakan servo dengan mengubah nilai `delay(15)` dalam fungsi `gerakkanServoPerlahan()`. Coba nilai **5** (cepat) vs **30** (lambat). Mana yang lebih mirip pintu kandang nyata?

> **Tantangan 3:** Tambahkan fitur: jika tombol BUKA dan TUTUP ditekan **bersamaan**, cetak pesan error di Serial Monitor: `"⚠️ Error: Dua tombol ditekan bersamaan!"`. Petunjuk: gunakan kondisi `if (tombolBuka && tombolTutup)`.

### 📝 Lembar Pengamatan Praktik 2

| No  | Aksi                 | Sudut Servo | Status Pintu | LED Hijau | LED Merah |
| --- | -------------------- | ----------- | ------------ | --------- | --------- |
| 1   | Awal (sebelum tekan) |             |              |           |           |
| 2   | Tekan Tombol BUKA    |             |              |           |           |
| 3   | Tekan Tombol TUTUP   |             |              |           |           |
| 4   | Suhu geser ke 39°C   |             |              |           |           |
| 5   | Suhu turun ke 25°C   |             |              |           |           |

### 🐔 Kaitan dengan Dunia Nyata

```
┌─────────────────────────────────────────────────────────────┐
│          DI WOKWI  →  DI KANDANG NYATA                      │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  📐 Servo SG90 (kecil) →  ⚙️ Servo MG996R / Linear         │
│  🔴 Tombol virtual     →  🔘 Tombol fisik waterproof        │
│  ⏰ Slider suhu        →  🌤️ Perubahan suhu nyata           │
│  📐 Sudut 0-90°        →  🚪 Pintu kandang buka/tutup       │
│                                                             │
│  💡 Di kandang nyata, bisa tambahkan RTC (Real Time Clock)  │
│     agar pintu otomatis buka jam 06.00 dan tutup jam 18.00! │
│                                                             │
│  💰 Hardware tambahan: RTC DS3231 (Rp 15.000)              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 🏗️ PRAKTIK 3: Sistem Gabungan — Smart Kandang Terintegrasi

### 🐔 Skenario Peternakan

> **Pak Arief adalah peternak ayam broiler modern.** Ia ingin satu sistem yang bisa: (1) memantau suhu dan kelembaban, (2) menyalakan kipas otomatis saat panas, (3) membuka pintu ventilasi secara otomatis, dan (4) memberikan peringatan jika kondisi berbahaya. **Inilah yang namanya _Smart Poultry System_ — dan kita buat versi simulasinya hari ini!**

### Apa yang Akan Kita Buat?

```
┌─────────────────────────────────────────────────────────────┐
│           SMART KANDANG TERINTEGRASI                        │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│   🌡️ DHT22 → membaca suhu & kelembaban kandang             │
│                                                             │
│   KONDISI → AKSI OTOMATIS:                                  │
│                                                             │
│   Suhu ≤ 28°C  → ✅ Normal: semua OFF, hemat energi        │
│   Suhu 28-32°C → ⚠️ Waspada: Kipas ON + Servo 45°          │
│   Suhu > 32°C  → 🚨 Darurat: Kipas Full + Servo 0° + Alarm │
│   Kelembaban>80% → 💧 Basah: Kipas ON + peringatan         │
│                                                             │
│   📺 LCD menampilkan ringkasan kondisi kandang              │
│   📟 Serial Monitor: log detail real-time                   │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 📦 Komponen yang Dibutuhkan (di Wokwi)

| No  | Komponen               | Fungsi                    | Jumlah |
| --- | ---------------------- | ------------------------- | ------ |
| 1   | **ESP32**              | Otak sistem               | 1      |
| 2   | **DHT22**              | Sensor suhu & kelembaban  | 1      |
| 3   | **Servo Motor (SG90)** | Kontrol ventilasi / pintu | 1      |
| 4   | **LED Biru**           | Simulasi kipas            | 1      |
| 5   | **LED Merah**          | Indikator darurat         | 1      |
| 6   | **LED Hijau**          | Indikator aman            | 1      |
| 7   | **Buzzer**             | Alarm kondisi darurat     | 1      |
| 8   | **LCD 16x2 (I2C)**     | Tampilkan status kandang  | 1      |
| 9   | **Resistor 220Ω**      | Pelindung LED (×3)        | 3      |

### 🔌 Diagram Koneksi

```
                         ESP32
                   ┌──────────────┐
                   │              │
  DHT22            │              │
  ┌─────┐          │              │
  │ VCC ├─────────→│  3.3V        │
  │ DATA├─────────→│  GPIO 15     │  ← Sensor suhu/kelembaban
  │ GND ├─────────→│  GND         │
  └─────┘          │              │
                   │              │
  Servo (SG90)     │              │
  ┌─────────┐      │              │
  │ Merah  ├──────→│  5V (VIN)    │  ← Power servo
  │ Coklat ├──────→│  GND         │
  │ Oranye ├──────→│  GPIO 13     │  ← Sinyal PWM servo
  └─────────┘      │              │
                   │              │
  LCD I2C          │              │
  ┌─────────┐      │              │
  │ VCC    ├──────→│  5V (VIN)    │
  │ GND    ├──────→│  GND         │
  │ SDA    ├──────→│  GPIO 21     │  ← Data I2C
  │ SCL    ├──────→│  GPIO 22     │  ← Clock I2C
  └─────────┘      │              │
                   │              │
                   │  GPIO 2  ───→ LED Hijau  → Resistor → GND
                   │  GPIO 4  ───→ LED Biru   → Resistor → GND
                   │  GPIO 5  ───→ LED Merah  → Resistor → GND
                   │  GPIO 18 ───→ Buzzer (+) → GND
                   │              │
                   └──────────────┘
```
<img width="1047" height="749" alt="image" src="https://github.com/user-attachments/assets/c512e3a2-cc03-4ccd-9894-537b324f8ccf" />

### 📋 Langkah-langkah Merangkai di Wokwi

#### Langkah 1: Buat Proyek Baru

1. Buka **[wokwi.com](https://wokwi.com)** → **New Project** → **ESP32**

#### Langkah 2: ⚠️ Install Library (WAJIB!)

> 🚨 **Jangan dilewatkan!** Praktik 3 menggunakan **3 library eksternal**. Ketiganya harus diinstall sebelum kode bisa berjalan.

1. Di bagian atas Wokwi, klik tab **"Library Manager"**
2. Klik tombol **"+" biru** (pojok kanan atas)
3. Cari dan install **`ESP32Servo`** → klik Install
4. Klik **"+"** lagi, cari dan install **`DHT sensor library for ESPx`** → klik Install
5. Klik **"+"** lagi, cari dan install **`LiquidCrystal I2C`** → klik Install

> 💡 Setelah install, ketiga library akan muncul di daftar **"Installed Libraries"**: `ESP32Servo`, `DHT sensor library for ESPx`, `LiquidCrystal I2C`.

#### Langkah 3: Tambahkan Semua Komponen

1. Klik **"+"** dan tambahkan secara berurutan:
   - **DHT22**
   - **Servo**
   - **LCD1602** (pilih yang ada tulisan "I2C")
   - **LED** × 3 buah (Hijau, Biru, Merah)
   - **Resistor** × 3 buah (220Ω)
   - **Buzzer**

#### Langkah 4: Sambungkan Semua Kabel

Ikuti diagram koneksi di atas dengan teliti. Kerja sama dalam kelompok: satu orang menyambungkan sensor, satu orang aktuator, satu orang LCD.

#### Langkah 5: Copy-Paste Kode

### 💻 Kode Program (Copy-Paste ke Wokwi)

```cpp
// ============================================================
// 🏗️ SMART KANDANG TERINTEGRASI
// Sensor DHT22 + Relay (LED) + Servo + LCD + Alarm
// ============================================================
// Sistem monitoring & kontrol otomatis kandang ayam:
//   ≤ 28°C         → Normal: semua off, hemat energi
//   28°C - 32°C    → Waspada: Kipas ON, Ventilasi 45°
//   > 32°C         → Darurat: Kipas Full, Ventilasi 0°, Alarm
//   Kelembaban >80% → Peringatan: Kipas ON (keringkan kandang)
// ============================================================

#include <ESP32Servo.h>
#include <LiquidCrystal_I2C.h>
#include "DHTesp.h"

// --- PENGATURAN PIN ---
const int PIN_SENSOR     = 15;   // DHT22
const int PIN_SERVO      = 13;   // Servo Motor
const int PIN_LED_AMAN   = 2;    // LED Hijau
const int PIN_LED_KIPAS  = 4;    // LED Biru (simulasi kipas)
const int PIN_LED_ALARM  = 5;    // LED Merah (darurat)
const int PIN_BUZZER     = 18;   // Buzzer

// --- BATAS SUHU DAN KELEMBABAN ---
const float SUHU_WASPADA   = 28.0;   // °C - mulai waspada
const float SUHU_DARURAT   = 32.0;   // °C - kondisi darurat
const float KELEMBABAN_MAX = 80.0;   // % - too humid

// --- POSISI SERVO (VENTILASI) ---
const int VENTILASI_TUTUP   = 90;    // Ventilasi tertutup
const int VENTILASI_SETENGAH = 45;   // Ventilasi sebagian
const int VENTILASI_BUKA    = 0;     // Ventilasi penuh terbuka

Servo servoVentilasi;
DHTesp sensorSuhu;
LiquidCrystal_I2C lcd(0x27, 16, 2);

// Variabel status
int sudutVentilasi = VENTILASI_TUTUP;  // Posisi servo saat ini

// Fungsi alarm
void bunyikanAlarm(int kali) {
  for (int i = 0; i < kali; i++) {
    tone(PIN_BUZZER, 900); delay(200);  // Aktifkan buzzer 900Hz
    tone(PIN_BUZZER, 0);   delay(100);  // Matikan buzzer
  }
}

// Fungsi gerak servo halus
void aturVentilasi(int targetSudut) {
  if (sudutVentilasi == targetSudut) return; // Tidak perlu gerak

  int langkah = (targetSudut > sudutVentilasi) ? 1 : -1;
  while (sudutVentilasi != targetSudut) {
    sudutVentilasi += langkah;
    servoVentilasi.write(sudutVentilasi);
    delay(10);
  }
}

// Fungsi update LCD
void updateLCD(float suhu, float kelembaban, String status) {
  lcd.clear();

  // Baris 1: Suhu dan kelembaban
  lcd.setCursor(0, 0);
  lcd.print("S:");
  lcd.print((int)suhu);
  lcd.print("C H:");
  lcd.print((int)kelembaban);
  lcd.print("%");

  // Baris 2: Status
  lcd.setCursor(0, 1);
  if (status.length() > 16) {
    status = status.substring(0, 16);  // Potong jika terlalu panjang
  }
  lcd.print(status);
}

void setup() {
  Serial.begin(115200);
  Serial.println("============================================");
  Serial.println("  🏗️  SMART KANDANG TERINTEGRASI");
  Serial.println("  IoT Peternakan - Universitas Mulawarman");
  Serial.println("============================================");

  // Inisialisasi semua komponen
  sensorSuhu.setup(PIN_SENSOR, DHTesp::DHT22);

  servoVentilasi.attach(PIN_SERVO);
  servoVentilasi.write(VENTILASI_TUTUP);

  lcd.init();
  lcd.backlight();
  lcd.setCursor(0, 0); lcd.print("Smart Kandang");
  lcd.setCursor(0, 1); lcd.print("Memuat...");

  pinMode(PIN_LED_AMAN,  OUTPUT);
  pinMode(PIN_LED_KIPAS, OUTPUT);
  pinMode(PIN_LED_ALARM, OUTPUT);
  // Catatan: PIN_BUZZER tidak perlu pinMode saat menggunakan tone()

  // Semua LED mati terlebih dahulu
  digitalWrite(PIN_LED_AMAN,  LOW);
  digitalWrite(PIN_LED_KIPAS, LOW);
  digitalWrite(PIN_LED_ALARM, LOW);
  tone(PIN_BUZZER, 0);   // Pastikan buzzer mati

  delay(2000);
  Serial.println("✅ Semua komponen siap!");
  Serial.println("");
}

void loop() {
  // 1️⃣ BACA SENSOR
  float suhu       = sensorSuhu.getTemperature();
  float kelembaban = sensorSuhu.getHumidity();

  if (isnan(suhu) || isnan(kelembaban)) {
    Serial.println("❌ Sensor error! Periksa kabel DHT22.");
    lcd.clear();
    lcd.setCursor(0, 0); lcd.print("ERROR SENSOR!");
    lcd.setCursor(0, 1); lcd.print("Cek kabel DHT22");
    delay(2000);
    return;
  }

  // 2️⃣ LOG DATA KE SERIAL MONITOR
  Serial.println("────────────────────────────────────────────");
  Serial.print("🌡️  Suhu         : "); Serial.print(suhu, 1);      Serial.println(" °C");
  Serial.print("💧 Kelembaban   : "); Serial.print(kelembaban, 1); Serial.println(" %");
  Serial.print("📐 Ventilasi    : "); Serial.print(sudutVentilasi); Serial.println("°");

  // 3️⃣ SISTEM KEPUTUSAN (Decision Logic)
  if (suhu > SUHU_DARURAT) {
    // 🔴 MODE DARURAT
    Serial.println("🔴 MODE: 🚨 DARURAT! Suhu kritik!");
    Serial.println("   → Kipas penuh + Ventilasi buka + Alarm!");
    Serial.println("   → HUBUNGI PETERNAK SEGERA!");

    digitalWrite(PIN_LED_AMAN,  LOW);
    digitalWrite(PIN_LED_KIPAS, HIGH);   // Kipas ON
    digitalWrite(PIN_LED_ALARM, HIGH);   // LED alarm ON
    aturVentilasi(VENTILASI_BUKA);       // Ventilasi buka penuh
    bunyikanAlarm(3);                    // Alarm 3x
    updateLCD(suhu, kelembaban, "DARURAT! Cek kand");

  } else if (suhu >= SUHU_WASPADA || kelembaban > KELEMBABAN_MAX) {
    // 🟡 MODE WASPADA: Suhu 28-32°C atau kelembaban tinggi
    Serial.println("🟡 MODE: ⚠️  Waspada! Kipas & Ventilasi aktif.");

    String pesanWaspada = "Waspada";
    if (kelembaban > KELEMBABAN_MAX) {
      Serial.println("   → Kelembaban tinggi! Risiko penyakit meningkat.");
      pesanWaspada = "Lembab! Cek litter";
    } else {
      pesanWaspada = "Suhu naik, waspada";
    }

    digitalWrite(PIN_LED_AMAN,  LOW);
    digitalWrite(PIN_LED_KIPAS, HIGH);      // Kipas ON
    digitalWrite(PIN_LED_ALARM, LOW);
    aturVentilasi(VENTILASI_SETENGAH);      // Ventilasi sebagian
    tone(PIN_BUZZER, 0);   // Buzzer mati
    updateLCD(suhu, kelembaban, pesanWaspada);

  } else {
    // 🟢 MODE NORMAL
    Serial.println("🟢 MODE: ✅ Normal! Semua sistem hemat energi.");

    digitalWrite(PIN_LED_AMAN,  HIGH);   // LED Hijau ON (tanda aman)
    digitalWrite(PIN_LED_KIPAS, LOW);    // Kipas OFF
    digitalWrite(PIN_LED_ALARM, LOW);    // Alarm OFF
    aturVentilasi(VENTILASI_TUTUP);      // Ventilasi tertutup
    tone(PIN_BUZZER, 0);   // Buzzer mati
    updateLCD(suhu, kelembaban, "Normal. Aman!");
  }

  // 4️⃣ RINGKASAN STATUS
  Serial.print("🔌 Kipas         : "); Serial.println(digitalRead(PIN_LED_KIPAS) ? "ON" : "OFF");
  Serial.print("🚪 Ventilasi     : ");
  if (sudutVentilasi == VENTILASI_BUKA)     Serial.println("TERBUKA PENUH");
  else if (sudutVentilasi == VENTILASI_SETENGAH) Serial.println("TERBUKA SEBAGIAN");
  else Serial.println("TERTUTUP");
  Serial.println("");

  delay(2000);
}
```

### ▶️ Cara Menjalankan

1. Klik **▶️ Play**
2. Tunggu LCD menampilkan **"Smart Kandang - Memuat..."** → lalu data suhu muncul
3. **Klik sensor DHT22** → geser slider suhu:
   - **25°C** → 🟢 Normal: semua mati, LCD: "Normal. Aman!"
   - **30°C** → 🟡 Waspada: LED Biru nyala, servo ke 45°
   - **35°C** → 🔴 Darurat: semua aktuator maksimal + buzzer berbunyi
4. Geser kelembaban di atas **80%** → lihat status "Lembab!" di LCD

### 🧪 Eksperimen Final (Wajib untuk Video)

> **Tantangan Utama — Wajib didemokan di video YouTube:**
>
> Bersama kelompok, ubah sistem untuk **jenis ternak berbeda**. Pilih salah satu:
>
> 🐑 **Kambing/Domba** → Batas suhu waspada: 30°C, darurat: 35°C, kelembaban max: 75%
>
> 🐷 **Babi/Ternak Besar** → Batas suhu waspada: 25°C, darurat: 30°C, kelembaban max: 70%
>
> 🐟 **Budidaya Ikan/Udang** → Fokus kelembaban/suhu air, modifikasi batas sesuai literatur
>
> Jelaskan dalam video **mengapa** Anda memilih nilai batas tersebut (dasar ilmiahnya dari materi teori)!

### 📝 Lembar Pengamatan Praktik 3

| No  | Suhu (°C) | Kelembaban (%) | Mode Sistem | Kipas (LED Biru) | LED Alarm | Sudut Servo | Tampilan LCD |
| --- | --------- | -------------- | ----------- | ---------------- | --------- | ----------- | ------------ |
| 1   | 25        | 60             |             |                  |           |             |              |
| 2   | 30        | 65             |             |                  |           |             |              |
| 3   | 35        | 70             |             |                  |           |             |              |
| 4   | 28        | 85             |             |                  |           |             |              |
| 5   | 38        | 90             |             |                  |           |             |              |

---

## 🎬 TUGAS KELOMPOK: VIDEO PRESENTASI YOUTUBE

### 📤 Format Pengumpulan

> Kumpulkan melalui form/LMS yang dibagikan dosen sebelum Pertemuan 5.

**Format nama kelompok untuk judul video YouTube:**

```
[Kelas]-[NamaKelompok] | Praktikum IoT P4 - Smart Kandang Wokwi
Contoh: A-KelompokAlpha | Praktikum IoT P4 - Smart Kandang Wokwi
```

**Yang harus dikumpulkan (per kelompok):**

| No  | Item                    | Keterangan                                    |
| --- | ----------------------- | --------------------------------------------- |
| 1   | Link YouTube (Unlisted) | Video presentasi 7-10 menit                   |
| 2   | Link Wokwi Praktik 1    | Proyek Relay + Kipas Otomatis                 |
| 3   | Link Wokwi Praktik 2    | Proyek Servo + Pintu Kandang                  |
| 4   | Link Wokwi Praktik 3    | Proyek Smart Kandang Gabungan (sudah dimodif) |
| 5   | Foto Lembar Pengamatan  | Screenshot/foto ketiga lembar pengamatan      |

> 💡 **Cara share link Wokwi:** Klik tombol **Share** (ikon link) di pojok kanan atas proyek Wokwi → Copy link → Tempel di form pengumpulan.

---

### 📌 Ketentuan Video

| Aspek              | Ketentuan                                                    |
| ------------------ | ------------------------------------------------------------ |
| **Durasi**         | 7–10 menit                                                   |
| **Platform**       | YouTube (Unlisted — hanya yang punya link yang bisa melihat) |
| **Bahasa**         | Indonesia                                                    |
| **Setiap anggota** | WAJIB berbicara minimal 1–2 menit di video                   |
| **Deadline**       | Sebelum Pertemuan 5                                          |
| **Pengumpulan**    | Form/LMS: link YouTube + link proyek Wokwi (semua 3 praktik) |

### 🎯 Konten Wajib dalam Video (Tidak Boleh Dilewatkan!)

Struktur video yang diharapkan:

```
📽️ STRUKTUR VIDEO (7-10 Menit)
├── [0:00 – 0:30] Pembukaan: Perkenalan kelompok & topik
├── [0:30 – 3:00] Demo Praktik 1: Relay + Kipas Otomatis
│   ├── Tampilkan rangkaian Wokwi
│   ├── Jalankan & demo slider suhu
│   └── Jelaskan kaitan dengan kandang nyata
├── [3:00 – 5:30] Demo Praktik 2: Servo Motor + Pintu Otomatis
│   ├── Tampilkan rangkaian Wokwi
│   ├── Demo tombol buka/tutup & suhu darurat
│   └── Jelaskan mengapa servo digunakan di peternakan
├── [5:30 – 8:30] Demo Praktik 3: Smart Kandang Gabungan
│   ├── Tampilkan rangkaian lengkap
│   ├── Demo semua mode (Normal, Waspada, Darurat)
│   ├── Demo modifikasi untuk ternak pilihan kelompok ← WAJIB
│   └── Jelaskan logika sistem dengan bahasa sederhana
└── [8:30 – 10:00] Refleksi & Penutup
    ├── Apa yang dipelajari hari ini?
    ├── Tantangan yang dihadapi & cara mengatasinya
    └── Ide pengembangan sistem ke depan
```

### 📊 Rubrik Penilaian Video

| Kriteria                         | Bobot | Deskripsi                                                              |
| -------------------------------- | ----- | ---------------------------------------------------------------------- |
| **Kelengkapan Demo (3 Praktik)** | 30%   | Semua 3 praktik didemonstrasikan dengan jelas & berjalan               |
| **Penjelasan Teknis**            | 25%   | Mampu menjelaskan cara kerja kode dan rangkaian dengan benar           |
| **Kaitan dengan Peternakan**     | 20%   | Menjelaskan relevansi setiap praktik dengan kebutuhan peternakan nyata |
| **Kreativitas Modifikasi**       | 15%   | Berhasil memodifikasi sistem untuk ternak pilihan (Tantangan Utama)    |
| **Partisipasi Semua Anggota**    | 10%   | Setiap anggota kelompok berbicara & berkontribusi di video             |

---

## 💡 Tips Sukses Self-Paced Learning

### Untuk Kelompok

```
┌─────────────────────────────────────────────────────────────┐
│              PEMBAGIAN PERAN KELOMPOK                       │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  🔧 Teknisi Wiring   → Menyambungkan komponen di Wokwi     │
│  💻 Teknisi Kode     → Copy-paste & modifikasi kode        │
│  📋 Pencatat         → Mengisi lembar pengamatan           │
│  🎙️ Presenter        → Menjelaskan saat rekam video        │
│                                                             │
│  💡 Gilir semua peran agar semua belajar semuanya!         │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Jika Ada Kendala

| Masalah                                       | Solusi                                                                        |
| --------------------------------------------- | ----------------------------------------------------------------------------- |
| **"ESP32Servo.h: No such file or directory"** | Buat file `libraries.txt` di Wokwi, isi dengan `ESP32Servo` (lihat Langkah 2) |
| **"LiquidCrystal_I2C.h: No such file"**       | Tambahkan `LiquidCrystal I2C` di `libraries.txt` (Praktik 3)                  |
| Kode error / tidak bisa compile               | Periksa tanda kurung `{}` dan titik koma `;` di setiap baris                  |
| Sensor tidak terbaca                          | Periksa sambungan VCC, GND, dan DATA pin                                      |
| Servo tidak bergerak                          | Pastikan pin PWM benar (GPIO 13) dan power dari 5V/VIN                        |
| LCD tidak muncul tulisan                      | Cek alamat I2C (0x27), pastikan SDA=GPIO21 dan SCL=GPIO22                     |
| Wokwi lambat / lag                            | Tutup tab browser lain, gunakan Chrome/Edge terbaru                           |

---

## 📝 Rangkuman Keseluruhan Praktikum 4

```
┌─────────────────────────────────────────────────────────────┐
│         RINGKASAN PRAKTIKUM AKTUATOR WOKWI                  │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Praktik 1️⃣  DHT22 + LED + Buzzer → Kipas Otomatis (Relay) │
│  Praktik 2️⃣  DHT22 + Servo + Tombol → Pintu Kandang Auto   │
│  Praktik 3️⃣  DHT22 + Servo + LCD + Buzzer → Smart Kandang  │
│                                                             │
│  💡 PELAJARAN UTAMA:                                        │
│  • SENSOR  → membaca kondisi → menghasilkan DATA            │
│  • ESP32   → menganalisis data → membuat KEPUTUSAN          │
│  • RELAY   → mengontrol perangkat listrik 220V              │
│  • SERVO   → menggerakkan pintu/katup secara presisi        │
│  • LCD     → menampilkan status untuk peternak              │
│                                                             │
│  💰 ESTIMASI BIAYA HARDWARE SISTEM NYATA (Praktik 3):       │
│  • ESP32               : Rp  60.000                         │
│  • DHT22               : Rp  35.000                         │
│  • Servo MG996R        : Rp  45.000                         │
│  • Relay 2 Channel     : Rp  15.000                         │
│  • LCD I2C 16x2        : Rp  25.000                         │
│  • Buzzer + LED + Kabel: Rp  20.000                         │
│  ─────────────────────────────────────────────────          │
│  • TOTAL               : ± Rp 200.000                       │
│                                                             │
│  🐔 Dengan Rp 200.000, kandang bisa dikontrol otomatis:     │
│     Kipas, Pintu Ventilasi, Alarm, Display Status           │
│     → 24 jam nonstop, tanpa perlu jaga manual!              │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## 📚 Referensi

| No  | Referensi                                                                                                                  | Keterangan                |
| --- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------- |
| 1   | Bolton, W. (2015). _Mechatronics: Electronic Control Systems in Mechanical and Electrical Engineering_ (6th ed.). Pearson. | Teori aktuator            |
| 2   | Espressif Systems. (2023). _ESP32 Technical Reference Manual_. Shanghai: Espressif.                                        | Dokumentasi pin ESP32     |
| 3   | Random Nerd Tutorials. _ESP32 with Servo Motor_. Tersedia di: randomnerdtutorials.com                                      | Tutorial servo ESP32      |
| 4   | Aviagen. (2018). _Ross Broiler Management Handbook_. Aviagen Ltd.                                                          | Standar suhu kandang ayam |
| 5   | Wokwi Documentation. _Getting Started_. Tersedia di: docs.wokwi.com                                                        | Panduan Wokwi             |

---

> 🎯 **Ingat:** Tujuan akhir praktikum ini bukan hanya membuat rangkaian bekerja di Wokwi, tapi memahami **MENGAPA** setiap komponen dipilih dan **BAGAIMANA** sistem ini akan membantu peternak di dunia nyata. Itulah inti dari _Smart Farming_!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan — Universitas Mulawarman_  
_Self-Paced Learning — Pertemuan 4 — Semester Genap 2025/2026_

