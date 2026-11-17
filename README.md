# Petualangan Calistung

Implementasi tampilan statis game edukasi untuk anak TK, berdasarkan screenshot, kode ekspor, dan frame Figma MulMet.

## Melihat tampilan

Buka `index.html` di browser. Tidak memerlukan instalasi paket, proses build, atau koneksi internet.

Halaman yang tersedia:

- `index.html`: Menu Utama.
- `pages/pilih-dunia.html`: Menu Pemilihan Dunia, dengan Hutan Huruf (Membaca), Taman Pensil (Menulis), dan Kerajaan Angka (Berhitung). Semua indikator kemajuan merupakan teks statis `0/5`.
- [Pilih Level — Hutan Huruf](pages/level-hutan-huruf.html): peta level 1–5, kemajuan `2/5`, level 3 disorot, dan level 4–5 terkunci.
- [Kerajaan Angka](pages/kerajaan-angka.html): tampilan permainan level 3, tujuh buah, serta pilihan angka `4`, `7`, `3`, dan `1`.
- [Taman Pensil](pages/taman-pensil.html): tampilan permainan level 3 dengan pola huruf A dan contoh garis yang sedang ditelusuri.
- [Pause / Jeda](pages/pause.html): panel Jeda di atas tampilan Kerajaan Angka yang digelapkan.
- [Hasil Berhasil](pages/hasil-berhasil.html): hasil Taman Pensil, bintang, tiga indikator terisi, dan tulisan `LEVEL 4 TERBUKA`.
- [Hasil Gagal](pages/hasil-gagal.html): hasil Taman Pensil dengan tulisan `Coba Lagi Ya`, bintang sedih, dan tombol Ulangi.
- [Hutan Huruf — Salah](pages/hutan-huruf-salah.html): gambar apel, pilihan `A`, `B`, `M`, dan `S`, dengan pilihan `S` berwarna merah.
- [Hutan Huruf — Benar](pages/hutan-huruf-benar.html): gambar pisang, pilihan `A`, `P`, `M`, dan `S`, dengan pilihan `P` berwarna hijau.

Setiap halaman dibuka langsung melalui file di atas. Tombol di dalam desain tidak berpindah halaman. Gambar pratinjau halaman dari Figma tersedia di folder `previews/`.

Opsional, jalankan server lokal dari folder proyek:

```sh
python -m http.server 8000
```

Kemudian buka `http://localhost:8000`.

## Ruang lingkup

- HTML dan CSS tanpa JavaScript.
- Menu utama dengan judul, ilustrasi burung hantu, bukit, pohon, awan, matahari, dan tombol Mulai.
- Tombol adalah elemen tampilan; tidak menjalankan permainan atau membuka halaman lain.
- Komposisi mengikuti rasio screenshot referensi, diperkecil atau diperbesar secara proporsional agar muat di layar. Ruang kosong di luar bidang permainan dapat muncul pada rasio layar berbeda.
- Garis seleksi dan handle biru dari editor Figma tidak disertakan.

Menu Utama dan Menu Pemilihan Dunia menggunakan ilustrasi yang dibuat ulang dari screenshot sebagai SVG di dalam HTML, serta font lokal Fredoka dan Nunito Sans. Detailnya dapat berbeda dari aset asli.

Delapan halaman tambahan menggunakan aset SVG asli yang diunduh melalui konektor Figma dan font lokal Fredoka One, Inter, serta Nunito Sans. Semuanya berupa HTML/CSS tanpa React, Tailwind, atau JavaScript. Angka, jawaban, posisi garis, hasil, dan status terkunci mengikuti kondisi statis pada frame sumber; tidak dihitung atau disimpan.

Halaman Hasil Gagal tetap menampilkan `LEVEL 4 TERBUKA` karena tulisan tersebut ada pada frame sumber. Ini adalah salinan kondisi visual prototype, bukan hasil perhitungan permainan.

Menu Pemilihan Dunia mengikuti screenshot terbaru dengan rasio frame 1133 × 744: langit biru, bukit hijau, awan, tombol kembali dan suara berwarna kuning, tiga kartu putih dengan panel ilustrasi berwarna, bintang pada indikator `0/5`, serta maskot dengan balon teks di kiri bawah. Kedua tombol tetap statis. Ilustrasi SVG dibuat ulang berdasarkan screenshot; aset asli diperlukan untuk pencocokan detail secara persis.

## Referensi Figma

| Halaman | Frame sumber |
| --- | --- |
| Pilih Level — Hutan Huruf | [50:2](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=50-2) |
| Kerajaan Angka — Level 3 | [50:372](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=50-372) |
| Taman Pensil — Level 3 | [51:535](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=51-535) |
| Pause — Kerajaan Angka | [91:1650](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=91-1650) |
| Hasil Berhasil — Taman Pensil | [91:1074](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=91-1074) |
| Hasil Gagal — Taman Pensil | [91:1157](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=91-1157) |
| Hutan Huruf — Salah | [113:4803](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=113-4803) |
| Hutan Huruf — Benar | [113:5092](https://www.figma.com/design/jbaD1Iyr9uThodd17Vv6ws/MulMet?node-id=113-5092) |

## Mengubah tampilan

Konten teks dapat diedit langsung pada file HTML masing-masing halaman. Delapan halaman tambahan berbagi `css/figma-screens.css`. Variabel CSS `--x`, `--y`, `--w`, dan `--h` pada setiap elemen menentukan posisi dan ukuran dalam persen; `--size` menentukan ukuran teks relatif terhadap lebar bidang permainan. Pendekatan ini mempertahankan komposisi tablet saat ukurannya berubah. Variabel `--matrix` mempertahankan rotasi atau pencerminan elemen, termasuk mulut bintang sedih.

File `assets/figma/layers.json` memetakan gambar ke node Figma dan posisi desainnya; `dimensions.json` menyimpan metadata ukuran SVG. File SVG asli tidak dimodifikasi, dan halaman tidak memakai URL aset Figma sementara maupun gambar screenshot utuh.

## Struktur

```text
index.html                  Struktur dan ilustrasi menu utama
pages/pilih-dunia.html       Tampilan statis pemilihan dunia
pages/level-hutan-huruf.html Peta level Hutan Huruf
pages/kerajaan-angka.html    Tampilan berhitung level 3
pages/taman-pensil.html      Tampilan menulis level 3
pages/pause.html             Tampilan panel Jeda
pages/hasil-berhasil.html    Tampilan hasil berhasil
pages/hasil-gagal.html       Tampilan hasil gagal
pages/hutan-huruf-salah.html Tampilan jawaban salah
pages/hutan-huruf-benar.html Tampilan jawaban benar
css/style.css               Layout, warna, font, dan tombol
css/pilih-dunia.css          Layout kartu dan dekorasi pemilihan dunia
css/figma-screens.css        Layout bersama delapan frame Figma
assets/figma/               Aset SVG asli dan metadata lapisan
assets/fonts/               Font lokal beserta lisensinya
previews/                   Screenshot hasil render halaman Figma
README.md                   Penjelasan proyek
```

## Mengunggah ke GitHub

Buat repository kosong di GitHub, kemudian jalankan dari folder ini, mengganti URL contoh dengan URL repository sendiri:

```sh
git init
git add .
git commit -m "Buat tampilan statis Petualangan Calistung"
git branch -M main
git remote add origin https://github.com/USERNAME/petualangan-calistung.git
git push -u origin main
```
