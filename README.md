# Melty Blood 2002 Archive Tools & Editor

Kumpulan alat modding dan lokalisasi untuk game **Melty Blood (2002)**. Mendukung ekstraksi, pengeditan teks via GUI, hingga pengemasan ulang archive `.p` ke format aslinya.

---

### Catatan Penting: Penggunaan Font
Game ini menggunakan sistem encoding spesifik. **Huruf Latin standar (Half-width) tidak akan terbaca.** Wajib menggunakan karakter **Fullwidth (Zenkaku)** agar teks muncul di dalam game.

* **Biasa:** "Di awal bulan Agustus."
* **Fullwidth:** "Ｄｉ　ａｗａｌ　ｂｕｌａｎ　Ａｇｕｓｔｕｓ．"

---

### Analisis Archive (data04.p)
File `data04.p` adalah kontainer utama untuk lokalisasi dengan rincian aset:
* **Total Isi:** 189 file (~40 MB)
* **Skrip Dialog:** 62 file `.TXT` (~10.676 baris teks)
* **Aset Lain:** 107 file `.EX3`, 9 file `.WAV`, 1 file `.FNT`
* **Versi:** Kompatibel dengan *Mirror Moon English Patch* (Shift-JIS)

---

### Fitur Utama
Sistem ini menjamin integritas data tetap terjaga selama proses modding:
* **Unpack & Repack:** Ekstraksi dan pengemasan ulang yang terverifikasi *byte-perfect*.
* **Keamanan:** Dekripsi dan enkripsi otomatis (Key: `0xE3DF59AC`) berbasis algoritma nama file.
* **Editor GUI:** Antarmuka khusus dengan *syntax highlighting* skrip game.
* **Manajemen Teks:** Auto-save ke JSON, fitur *find & replace* global, dan pelacak progres.
* **Kolaborasi:** Fitur ekspor/impor hasil terjemahan untuk kerja tim.

---

### Preview Interface
<div align="center">
  <table style="margin-left: auto; margin-right: auto;">
    <tr>
      <td align="center"><b>Melty Blood Script Editor</b></td>
    </tr>
    <tr>
      <td><img src="https://imgur.com/SDN7Vsz.png" width="750" alt="Editor Preview"></td>
    </tr>
  </table>
</div>

---

### Cara Penggunaan

#### 1. Mode GUI (Rekomendasi)
1. Jalankan `python mb_editor.py`.
2. Klik **Open Archive (.p)** lalu pilih `data04.p`.
3. Pilih file skrip (contoh: `00.TXT`) pada panel kiri.
4. Ketik terjemahan pada kotak **↳** di bawah baris dialog yang dipilih.
5. Klik **Repack Archive** untuk membuat file `.p` baru.

#### 2. Mode CLI (Terminal)
```bash
python mb_core.py unpack data04.p extracted/     # Mengekstrak isi archive
python mb_core.py repack extracted/ data04.p     # Mengemas ulang folder
python mb_core.py info data04.p                  # Melihat informasi isi archive
