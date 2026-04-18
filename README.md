# Melty Blood 2002 Archive Tools & Editor

Kumpulan alat (tools) untuk melakukan modding dan lokalisasi pada game **Melty Blood (2002)**. Tool ini mendukung penuh proses ekstraksi, pengeditan teks melalui GUI, hingga pengemasan ulang (*repacking*) file archive `.p`.

---

## Catatan Penting: Penggunaan Font
Game ini menggunakan sistem encoding yang spesifik. **Huruf Latin/Alfabet standar (Half-width) tidak akan terbaca dengan benar atau bahkan tidak muncul di dalam game.** Anda **wajib** menggunakan karakter **Fullwidth (Zenkaku)** untuk semua teks terjemahan.
- **Biasa:**
 "Di awal bulan Agustus."
- **Fullwidth:**
 "Ｄｉ　ａｗａｌ　ｂｕｌａｎ　Ａｇｕｓｔｕｓ．"

Pastikan IME Anda dalam mode *Full-width* saat mengetik terjemahan di dalam editor.

---

## Hasil Analisis Archive (data04.p)
Berdasarkan analisis teknis, file `data04.p` merupakan kontainer utama yang berisi aset-aset penting untuk lokalisasi:
- **Total Isi:** 189 file (~40 MB).
- **Aset Translatable:** 62 file `.TXT` berisi skrip dialog & narasi (~10.676 baris teks).
- **Aset Lainnya:** 107 file `.EX3` (Animasi/Efek), 9 file `.WAV` (Audio), dan 1 file `.FNT` (Font).
- **Versi:** Kompatibel dengan *Mirror Moon English Patch* (menggunakan format full-width ASCII dalam encoding Shift-JIS).

---

## Fitur Utama
Tool ini dirancang untuk memastikan integritas data tetap terjaga selama proses modding:
- **Unpack/Repack:** Ekstraksi dan pengemasan ulang archive .p yang sudah diverifikasi *byte-perfect*.
- **Security:** Dekripsi dan enkripsi otomatis menggunakan key `0xE3DF59AC` dengan algoritma *filename-based*.
- **GUI Editor:** Antarmuka pengeditan yang dilengkapi dengan *syntax highlighting* untuk skrip game.
- **Translation Management:** Fitur auto-save ke format JSON (tanpa merusak file asli), *find & replace* global, serta tracker progres.
- **Collaboration:** Mendukung ekspor/impor hasil terjemahan untuk memudahkan kerja tim.

---

## Preview Interface

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

## Cara Penggunaan

### 1. Menggunakan GUI Editor (Rekomendasi)
Metode paling mudah untuk menerjemahkan tanpa menyentuh kode teknis:
1. Jalankan editor:

   ```bash 
   python mb_core.py unpack data04.p extracted/   # Mengekstrak semua isi archive
   python mb_core.py repack extracted/ data04_new.p  # Mengemas ulang folder menjadi archive .p
   python mb_core.py info data04.p                # Melihat daftar file dan informasi isi archive
