# Agent Based Modelling-Simulation of Influenza Spread-Project Pemodelan dan Simulasi

# Simulasi Persebaran Influenza Menggunakan Agent-Based Modeling (ABM)

Proyek ini merupakan simulasi sederhana penyebaran penyakit **influenza** menggunakan pendekatan **Agent-Based Modeling (ABM)** dengan bantuan library `mesa`. Simulasi ini dilakukan menggunakan **data dummy**, di mana setiap agen memiliki status kesehatan, tingkat imunitas, radius penyebaran, dan durasi infeksi.

---

## Dataset Dummy

- Dataset dummy dibuat secara acak untuk mewakili populasi agen.
- Setiap agen memiliki kolom:
  - `id`: Identitas unik agen
  - `status`: Kondisi awal agen ("healthy", "infected", "recovered")
  - `imunitas`: Tingkat kekebalan (0–1)
  - `durasi_infeksi`: Berapa lama agen akan tetap dalam kondisi terinfeksi
  - `radius_infeksi`: Jarak jangkauan agen untuk menularkan flu
  - 'posisi' : Posisi agen

---

##  Tools dan Library

- Python
- [Mesa](https://mesa.readthedocs.io/) (ABM Framework)
- Pandas
- NumPy
- Matplotlib
- Seaborn

---

## 🛠️ Alur Proses

### 1. Inisialisasi Data Dummy

- Data agen di-generate dengan menggunakan distribusi acak (`numpy.random`) untuk atribut:
  - Imunitas
  - Radius infeksi
  - Durasi infeksi
- Beberapa agen dipilih secara acak untuk menjadi **terinfeksi awal**.

---

### 2. Agent-Based Modeling dengan Mesa

- Dibuat dua class utama:
  - `InfluenzaAgent` → representasi individu dalam simulasi
  - `InfluenzaModel` → pengatur seluruh simulasi
- Aktivasi agen dilakukan secara acak setiap **step waktu** menggunakan `RandomActivation`.

---

### 3. Logika Penyebaran

Setiap step waktu simulasi (selama 30 langkah):

- Agen yang terinfeksi akan:
  - Menularkan flu kepada agen lain dalam radius tertentu
  - Menurunkan durasi infeksinya
  - Sembuh jika durasi infeksi selesai
- Agen sehat bisa tertular jika berada dalam radius agen yang terinfeksi dan memiliki imunitas rendah.

---

### 4. Pengumpulan Data

- Menggunakan `DataCollector` dari `mesa` untuk mencatat jumlah:
  - Agen sehat
  - Agen terinfeksi
  - Agen sembuh
- Data disimpan dalam bentuk `DataFrame` dan divisualisasikan menggunakan `matplotlib` dan `seaborn`.

---

### 5. Visualisasi dan Hasil

- Simulasi divisualisasikan dalam bentuk **Diagram Bar** untuk melihat tren perubahan populasi setiap status.
- Hasil menunjukkan bagaimana influenza dapat menyebar dengan cepat tergantung:
  - Jumlah agen awal yang terinfeksi
  - Radius penularan
  - Lama infeksi dan imunitas populasi

---

## 📌 Hasil & Kesimpulan

- Simulasi berhasil memodelkan dinamika penyebaran influenza dalam populasi sederhana.
- Parameter seperti radius infeksi dan tingkat imunitas memiliki dampak terhadap kecepatan penyebaran penyakit.

---
