# 🌐 Pertemuan 2: Mengenal Perangkat IoT dalam Peternakan

> **"Bayangkan kandang ternak Anda bisa 'berbicara' dan memberitahu kondisinya kapan saja, di mana saja!"**

---

## 🎯 Tujuan Pembelajaran

Setelah mempelajari materi ini, mahasiswa diharapkan mampu:

1. Memahami komponen-komponen utama sistem IoT
2. Mengenal berbagai perangkat IoT yang digunakan di peternakan
3. Memahami bagaimana perangkat-perangkat tersebut saling terhubung

---

## 📖 Apa itu IoT?

### Definisi Sederhana

**IoT (Internet of Things)** = **Internet untuk Benda-benda**

Bayangkan jika:

- 🌡️ **Termometer di kandang** bisa mengirim SMS ke HP Anda ketika suhu terlalu panas
- 💧 **Tempat minum ternak** otomatis terisi ketika air hampir habis
- 📊 **Timbangan ternak** langsung mencatat berat ke komputer tanpa perlu menulis manual

**Itulah IoT!** Benda-benda biasa yang kita "beri otak" sehingga bisa:

- **Merasakan** kondisi lingkungan (sensing)
- **Berpikir** dan mengambil keputusan sederhana (processing)
- **Berbicara** dengan kita melalui internet (communicating)
- **Bertindak** sesuai kebutuhan (actuating)

---

## 🏗️ Arsitektur IoT: 4 Komponen Utama

Sistem IoT seperti **tubuh manusia** yang bekerja bersama:

```
┌─────────────────────────────────────────────────────────────────────┐
│                                                                     │
│   🖐️ DEVICE          🔗 GATEWAY        ☁️ CLOUD       📱 APLIKASI │
│   (Panca Indera)     (Saraf)           (Otak)        (Mata/Mulut)   │
│                                                                     │
│   Sensor suhu    →   WiFi Router   →   Server    →   HP/Laptop      │
│   Sensor berat   →   Modem         →   Internet  →   Dashboard      │
│   Kamera         →   LoRa Gateway  →   Database  →   Notifikasi     │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

> 📚 **Catatan Akademis:**  
> Model arsitektur 4 lapisan ini (Device → Gateway → Cloud → Aplikasi) merupakan arsitektur IoT yang umum digunakan dan dikenal sebagai **"layered architecture"**. Beberapa literatur seperti Al-Fuqaha et al. (2015) menjelaskan arsitektur ini dalam jurnal _IEEE Communications Surveys & Tutorials_.

Mari kita bahas satu per satu:

---

## 1️⃣ DEVICE (Perangkat/Sensor) - "Panca Indera Kandang"

### Apa itu Device?

Device adalah **alat-alat yang dipasang di kandang** untuk merasakan kondisi lingkungan atau melakukan tindakan tertentu.

### Jenis-jenis Device di Peternakan

#### A. 📡 Sensor (Alat Perasa)

| Jenis Sensor             | Fungsi                      | Contoh Penggunaan                               |
| ------------------------ | --------------------------- | ----------------------------------------------- |
| 🌡️ **Sensor Suhu**       | Mengukur temperatur         | Memantau suhu kandang ayam agar tidak kepanasan |
| 💧 **Sensor Kelembaban** | Mengukur kadar air di udara | Menjaga kelembaban ideal untuk penetasan telur  |
| 💨 **Sensor Gas**        | Mendeteksi gas berbahaya    | Mendeteksi amonia (bau pesing) di kandang       |
| ⚖️ **Sensor Berat**      | Menimbang berat             | Memantau pertumbuhan ternak secara otomatis     |
| 🧪 **Sensor pH**         | Mengukur keasaman           | Memantau kualitas air minum ternak              |
| 📷 **Kamera**            | Merekam gambar/video        | Memantau kesehatan dan perilaku ternak          |

#### B. 🎛️ Aktuator (Alat Penggerak)

| Jenis Aktuator   | Fungsi                   | Contoh Penggunaan                  |
| ---------------- | ------------------------ | ---------------------------------- |
| 💡 **Lampu**     | Menyala/mati otomatis    | Mengatur pencahayaan kandang layer |
| 🌀 **Kipas**     | Mengatur sirkulasi udara | Menyala ketika suhu terlalu panas  |
| 💧 **Pompa Air** | Mengalirkan air          | Mengisi tempat minum otomatis      |
| 🚿 **Sprinkler** | Menyemprotkan air        | Menurunkan suhu kandang saat panas |

---

### 🐔 Contoh Nyata: Kandang Ayam Pintar

```
     ┌──────────────────────────────────────────┐
     │           KANDANG AYAM PINTAR            │
     │                                          │
     │  🌡️ Sensor Suhu      → "Sekarang 32°C"   │
     │  💧 Sensor Kelembaban → "RH 75%"         │
     │  💨 Sensor Amonia    → "Level Aman"      │
     │  📷 Kamera           → "Ayam sehat"      │
     │                                          │
     │  🌀 Kipas            ← "Nyalakan!"       │
     │  💧 Sprinkler        ← "Siap siaga"      │
     │  💡 Lampu            ← "Terang optimal"  │
     │                                          │
     └──────────────────────────────────────────┘
```

---

## 2️⃣ GATEWAY - "Jembatan Penghubung"

### Apa itu Gateway?

Gateway adalah **alat penghubung** antara device di kandang dengan internet/cloud.

**Analogi:** Jika sensor adalah "mata dan telinga" di kandang, gateway adalah "telepon" yang mengirimkan informasi ke pemilik.

### Jenis-jenis Gateway

| Jenis               | Jangkauan           | Kegunaan                    |
| ------------------- | ------------------- | --------------------------- |
| 📶 **WiFi Router**  | 50-100 meter        | Kandang dekat rumah/kantor  |
| 📡 **LoRa Gateway** | 1-15 kilometer      | Peternakan luas di pedesaan |
| 📱 **Modem 4G/5G**  | Mengikuti sinyal HP | Lokasi terpencil            |

### Cara Kerja Gateway

```
  Kandang 1          Kandang 2          Kandang 3
     │                  │                  │
     ▼                  ▼                  ▼
 ┌───────┐          ┌───────┐          ┌───────┐
 │Sensor │          │Sensor │          │Sensor │
 └───┬───┘          └───┬───┘          └───┬───┘
     │                  │                  │
     └──────────────────┼──────────────────┘
                        │
                        ▼
                ┌───────────────┐
                │   GATEWAY     │
                │ (WiFi/LoRa)   │
                └───────┬───────┘
                        │
                        ▼
                    INTERNET
```

---

## 3️⃣ CLOUD - "Otak di Awan"

### Apa itu Cloud?

Cloud adalah **komputer super besar di internet** yang:

- 📥 Menerima data dari semua sensor
- 🧠 Menyimpan dan mengolah data
- ⚡ Membuat keputusan otomatis
- 📊 Menyajikan informasi yang mudah dipahami

### Analogi Sederhana

> Bayangkan Cloud seperti **Google Drive** atau **WhatsApp** - file dan chat Anda tidak tersimpan di HP, tapi di internet. Jadi bisa diakses dari mana saja!

> 💡 **Tahukah Anda?**  
> Istilah "Cloud Computing" dipopulerkan oleh Google CEO Eric Schmidt pada tahun 2006. Menurut NIST (2011), cloud computing didefinisikan sebagai model yang memungkinkan akses jaringan yang nyaman dan on-demand ke kumpulan sumber daya komputasi bersama.

### Layanan Cloud Populer untuk IoT

| Layanan          | Logo | Keunggulan                      |
| ---------------- | ---- | ------------------------------- |
| **Blynk**        | 🟢   | Mudah, gratis untuk pemula      |
| **ThingSpeak**   | 📊   | Bagus untuk grafik dan analisis |
| **AWS IoT**      | 🟠   | Profesional, kapasitas besar    |
| **Google Cloud** | 🔵   | Terintegrasi dengan AI          |

### Contoh Data di Cloud

```
┌────────────────────────────────────────────────────────┐
│                 DATABASE PETERNAKAN                    │
├─────────────┬─────────┬─────────────┬──────────────────┤
│ Waktu       │ Suhu    │ Kelembaban  │ Status           │
├─────────────┼─────────┼─────────────┼──────────────────┤
│ 08:00 WIB   │ 28°C    │ 70%         │ ✅ Normal        │
│ 12:00 WIB   │ 35°C    │ 60%         │ ⚠️ Panas         │
│ 14:00 WIB   │ 33°C    │ 65%         │ ✅ Normal        │
│ 18:00 WIB   │ 29°C    │ 72%         │ ✅ Normal        │
└─────────────┴─────────┴─────────────┴──────────────────┘
```

---

## 4️⃣ APLIKASI - "Mata dan Telinga Peternak"

### Apa itu Aplikasi IoT?

Aplikasi adalah **tampilan** yang memungkinkan peternak:

- 👀 Melihat kondisi kandang real-time
- 🔔 Menerima notifikasi/peringatan
- 🎮 Mengontrol peralatan dari jarak jauh
- 📈 Menganalisis data historis

### Jenis Aplikasi

#### A. 📱 Aplikasi Mobile (HP)

- Praktis dibawa ke mana-mana
- Notifikasi langsung ke HP
- Contoh: Blynk, Smart Farm Apps

#### B. 💻 Dashboard Web (Laptop/Komputer)

- Tampilan lebih besar dan detail
- Grafik dan analisis lengkap
- Bisa dicetak untuk laporan

### Contoh Tampilan Dashboard

```
┌────────────────────────────────────────────────────────────┐
│                  🏠 SMART FARM DASHBOARD                   │
├────────────────────────────────────────────────────────────┤
│                                                            │
│   ┌─────────┐   ┌─────────┐   ┌─────────┐   ┌─────────┐    │
│   │  🌡️     │   │  💧    │   │  💨     │   │  🐔    │    │
│   │  32°C   │   │  68%    │   │  AMAN   │   │  4,850  │    │
│   │  Suhu   │   │ Lembab  │   │  Gas    │   │  Ekor   │    │
│   └─────────┘   └─────────┘   └─────────┘   └─────────┘    │
│                                                            │
│   ┌──────────────────────────────────────────────────────┐ │
│   │  📊 Grafik Suhu 24 Jam Terakhir                      │ │
│   │       ╭──╮                                           │ │
│   │    ╭──╯  ╰──╮     ╭──╮                               │ │
│   │ ───╯        ╰─────╯  ╰───                            │ │
│   │  00  04  08  12  16  20  24                          │ │
│   └──────────────────────────────────────────────────────┘ │
│                                                            │
│   🔴 Kipas: MATI    🟢 Lampu: NYALA    🔴 Pompa: MATI     │
│                                                            │
└────────────────────────────────────────────────────────────┘
```

---

## 🔄 Bagaimana Semuanya Bekerja Bersama?

### Skenario: Kandang Terlalu Panas

```
LANGKAH 1: MERASAKAN
┌─────────────────────────────────────────┐
│  🌡️ Sensor suhu mendeteksi 36°C         │
│     (Batas aman: 32°C)                  │
└─────────────────────────────────────────┘
                    │
                    ▼
LANGKAH 2: MENGIRIM
┌─────────────────────────────────────────┐
│  📡 Gateway mengirim data ke Cloud      │
│     "Kandang 1: Suhu 36°C - BAHAYA!"    │
└─────────────────────────────────────────┘
                    │
                    ▼
LANGKAH 3: MEMPROSES
┌─────────────────────────────────────────┐
│  ☁️ Cloud menganalisis:                 │
│     - Suhu > 32°C → Terlalu panas!      │
│     - Keputusan: Nyalakan kipas         │
└─────────────────────────────────────────┘
                    │
                    ▼
LANGKAH 4: BERTINDAK
┌─────────────────────────────────────────┐
│  🌀 Perintah dikirim ke kipas           │
│     Gateway → Kipas → NYALA!            │
└─────────────────────────────────────────┘
                    │
                    ▼
LANGKAH 5: MEMBERITAHU
┌─────────────────────────────────────────┐
│  📱 Notifikasi ke HP peternak:          │
│     "⚠️ Kandang 1 panas (36°C).         │
│      Kipas sudah dinyalakan otomatis"   │
└─────────────────────────────────────────┘
```

---

## 💡 Manfaat IoT untuk Peternak

### Tanpa IoT vs Dengan IoT

| Aspek                     | ❌ Tanpa IoT                           | ✅ Dengan IoT                 |
| ------------------------- | -------------------------------------- | ----------------------------- |
| **Monitoring**            | Harus ke kandang setiap saat           | Pantau dari HP kapan saja     |
| **Deteksi Masalah**       | Terlambat menyadari                    | Notifikasi langsung real-time |
| **Pencatatan**            | Manual di buku, sering lupa            | Otomatis tersimpan di Cloud   |
| **Pengambilan Keputusan** | Berdasarkan perkiraan                  | Berdasarkan data akurat       |
| **Efisiensi Waktu**       | Banyak waktu untuk cek rutin           | Waktu bisa untuk hal lain     |
| **Keamanan**              | Tidak tahu jika ada masalah malam hari | Alarm 24 jam                  |

---

## 📝 Rangkuman

```
┌─────────────────────────────────────────────────────────────┐
│                    4 KOMPONEN IoT                           │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  1. DEVICE (Sensor & Aktuator)                              │
│     → Alat yang merasakan dan bertindak                     │
│                                                             │
│  2. GATEWAY                                                 │
│     → Jembatan penghubung ke internet                       │
│                                                             │
│  3. CLOUD                                                   │
│     → Otak yang menyimpan dan mengolah data                 │
│                                                             │
│  4. APLIKASI                                                │
│     → Tampilan untuk memantau dan mengontrol                │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

---

## ❓ Pertanyaan Diskusi

1. **Menurut Anda, sensor apa yang paling penting untuk peternakan ayam? Mengapa?**

2. **Jika kandang ternak Anda berada 5 km dari rumah, gateway jenis apa yang cocok digunakan?**

3. **Apa yang mungkin terjadi jika sistem IoT di kandang kehilangan koneksi internet?**

4. **Selain yang disebutkan di materi, ide sensor atau aktuator apa lagi yang bisa membantu peternak?**

---

## 📚 Istilah Penting

| Istilah       | Arti                                            |
| ------------- | ----------------------------------------------- |
| **IoT**       | Internet of Things - internet untuk benda-benda |
| **Sensor**    | Alat untuk merasakan/mengukur sesuatu           |
| **Aktuator**  | Alat untuk melakukan tindakan fisik             |
| **Gateway**   | Penghubung antara device dan internet           |
| **Cloud**     | Komputer di internet untuk menyimpan data       |
| **Dashboard** | Tampilan visual untuk monitoring                |
| **Real-time** | Langsung/saat itu juga                          |

---

> 📌 **Pertemuan Selanjutnya:** Kita akan belajar lebih detail tentang **Sensor Lingkungan Kandang** - bagaimana sensor suhu, kelembaban, gas, berat, dan pH bekerja untuk membantu peternakan Anda!

---

_Materi ini disusun untuk Mata Kuliah Internet of Things (IoT)_  
_Program Studi Peternakan - Universitas Mulawarman_

---

## 📚 Daftar Pustaka (Referensi)

> 🎓 **Untuk Mahasiswa:**  
> Referensi ini berguna jika Anda ingin mempelajari lebih dalam atau mengutip untuk tugas/skripsi.

### Sumber Akademik

| No  | Referensi                                                                                                                                                                                                | Keterangan                             |
| --- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------- |
| 1   | Al-Fuqaha, A., et al. (2015). Internet of Things: A Survey on Enabling Technologies, Protocols, and Applications. _IEEE Communications Surveys & Tutorials_, 17(4), 2347-2376.                           | Survei komprehensif arsitektur IoT     |
| 2   | Mell, P., & Grance, T. (2011). _The NIST Definition of Cloud Computing_. NIST Special Publication 800-145.                                                                                               | Definisi resmi cloud computing         |
| 3   | Banhazi, T. M., et al. (2012). Precision Livestock Farming: An international review of scientific and commercial aspects. _International Journal of Agricultural and Biological Engineering_, 5(3), 1-9. | Review sensor dan teknologi peternakan |
| 4   | Wathes, C. M., et al. (2008). Is precision livestock farming an engineer's daydream or nightmare? _Computers and Electronics in Agriculture_, 64, 2-10.                                                  | Diskusi aplikasi sensor di peternakan  |

### Sumber Praktis

| No  | Referensi                                                                      | Keterangan                          |
| --- | ------------------------------------------------------------------------------ | ----------------------------------- |
| 5   | Blynk Documentation. _Getting Started with Blynk_. Tersedia di: docs.blynk.io  | Tutorial platform IoT untuk pemula  |
| 6   | ThingSpeak. _IoT Analytics Platform_. Tersedia di: thingspeak.com              | Platform cloud gratis untuk belajar |
| 7   | LoRa Alliance. (2020). _LoRaWAN Specification_. Tersedia di: lora-alliance.org | Standar komunikasi IoT jarak jauh   |

