# Melty Blood 2002 — Archive Tools & Editor

Kumpulan tool modding dan lokalisasi untuk game **Melty Blood (2002)**, mencakup ekstraksi, pengeditan teks via GUI, hingga pengemasan ulang arsip `.p` kembali ke format aslinya.

---

## Apa Ini?

Game Melty Blood (2002) menyimpan seluruh asetnya — script dialog, gambar, audio, dan font — di dalam arsip berekstensi `.p`. Format ini menggunakan enkripsi XOR berbasis nama file dan XOR tambahan pada header arsip, sehingga tidak bisa dibuka langsung dengan tool umum.

Repo ini menyediakan dua tool utama: `mb_core.py` sebagai library inti sekaligus tool command-line untuk unpack dan repack arsip, dan `mb_editor.py` sebagai antarmuka GUI yang memudahkan proses penerjemahan tanpa perlu menyentuh terminal sama sekali. Keduanya kompatibel dengan format arsip yang digunakan oleh *Mirror Moon English Patch* (Shift-JIS).

---

## Catatan Penting: Huruf Fullwidth

Game ini menggunakan sistem rendering font berbasis Shift-JIS yang tidak mengenali huruf Latin standar (half-width). Artinya, jika terjemahan ditulis dengan huruf biasa seperti `A`, `B`, `C`, teks tersebut tidak akan muncul di dalam game atau akan tampil sebagai karakter rusak.

Semua teks terjemahan **wajib menggunakan karakter Fullwidth (Zenkaku)**. Contoh perbandingannya:

```
Half-width (TIDAK AKAN TERBACA): "Di awal bulan Agustus."
Fullwidth (gunakan ini)        : "Ｄｉ　ａｗａｌ　ｂｕｌａｎ　Ａｇｕｓｔｕｓ．"
```

Karakter fullwidth bisa diketik dengan mengubah mode input IME ke Zenkaku, atau dengan menggunakan tabel konversi. Editor GUI sudah membantu menampilkan teks apa adanya agar mudah dikontrol.

---

## Struktur File Arsip

Arsip utama yang relevan untuk lokalisasi adalah `data04.p`, yang berisi 189 file dengan total ukuran sekitar 40 MB. Di dalamnya terdapat 62 file `.TXT` berisi script dialog (±10.676 baris), 107 file `.EX3` berisi data gambar/sprite, 9 file `.WAV` berisi audio, dan 1 file `.FNT` berisi data font game.

Untuk keperluan terjemahan, yang perlu diedit adalah file-file `.TXT` tersebut. File lainnya umumnya tidak perlu disentuh kecuali untuk modding grafis atau audio.

---

## Tentang `_manifest.json`

Setiap kali arsip diekstrak menggunakan tool ini, sebuah file bernama `_manifest.json` otomatis dibuat di dalam folder hasil ekstrak. File ini menyimpan urutan file asli dan flag header arsip — dua informasi yang dibutuhkan agar proses repack bisa menghasilkan arsip yang identik byte-per-byte dengan aslinya.

**Jangan hapus atau ubah `_manifest.json`.** Tanpa file ini, proses repack tidak bisa berjalan.

---

## Cara Pakai

### Mode GUI — Rekomendasi untuk Translator

Jalankan editor dengan perintah berikut:

```bash
python mb_editor.py
```

Setelah terbuka, klik **Open Archive (.p)** dan pilih file `data04.p`. Panel kiri akan menampilkan daftar file script yang ada di dalam arsip. Pilih salah satu, misalnya `00.TXT`, dan isi terjemahan pada kotak yang muncul di bawah setiap baris dialog. Editor mendukung syntax highlighting untuk memisahkan perintah game dari teks yang bisa diterjemahkan, fitur find & replace global, pelacak progres, serta ekspor dan impor hasil terjemahan untuk keperluan kolaborasi tim. Setelah selesai, klik **Repack Archive** untuk menghasilkan file `.p` baru yang siap digunakan.

### Mode CLI — Untuk Otomasi atau Penggunaan Lanjutan

`mb_core.py` bisa dijalankan langsung dari terminal untuk operasi unpack, repack, dan inspeksi arsip:

```bash
# Ekstrak semua isi arsip ke folder
python mb_core.py unpack data04.p extracted/

# Pack ulang folder hasil ekstrak menjadi arsip baru
python mb_core.py repack extracted/ data04_new.p

# Tampilkan informasi isi arsip tanpa mengekstrak
python mb_core.py info data04.p
```

Perintah `info` menampilkan daftar lengkap file beserta offset dan ukurannya — berguna untuk verifikasi sebelum atau sesudah proses repack.

---

## Format Script

File `.TXT` di dalam arsip menggunakan format script khusus. Baris yang diawali dengan `//` adalah komentar. Baris yang terdiri dari satu atau dua huruf kapital seperti `EF`, `GW`, `WI`, `MD`, `BP`, dan sejenisnya adalah perintah game yang tidak boleh diubah. Hanya baris yang berisi teks dialog atau narasi — biasanya diawali spasi atau karakter Jepang — yang merupakan bagian yang perlu diterjemahkan.

---

## Requirements

Tool ini membutuhkan **Python 3.10 atau lebih baru**. Tidak ada dependensi eksternal yang perlu diinstall untuk `mb_core.py`. Untuk `mb_editor.py` (GUI), pastikan `tkinter` tersedia — di Windows sudah terinstall otomatis bersama Python standar.

---

## Disclaimer

Tool ini dibuat untuk keperluan edukasi, penelitian, dan lokalisasi personal. Pengguna bertanggung jawab penuh untuk memastikan penggunaannya sesuai dengan aturan copyright dan Terms of Service dari game original.
