# Template Skripsi LaTeX — Politeknik Statistika STIS (D-IV Komputasi Statistik)

Template LaTeX (Overleaf) untuk skripsi Prodi D-IV Komputasi Statistik, disusun
mengikuti **Pedoman Penyusunan Skripsi Edisi Keenam (2025)**. Template ini adalah
versi LaTeX murni dari paket R `skripsistis`, sehingga format (margin, font, judul
bab, tabel, gambar, persamaan, daftar pustaka) sudah sesuai pedoman.

## Cara memakai di Overleaf

1. **Unggah** berkas `skripsistis-overleaf.zip` ke Overleaf
   (New Project → Upload Project), atau salin seluruh berkas ke proyek baru.
2. **Setel compiler ke XeLaTeX**: Menu → Settings → Compiler → **XeLaTeX**.
   (Wajib, karena memakai `fontspec`/Times New Roman. Berkas `latexmkrc` juga
   sudah memaksa XeLaTeX bila langkah ini terlewat.)
3. Pastikan **Main document** = `main.tex`.
4. Klik **Recompile**. Overleaf otomatis menjalankan Biber untuk Daftar Pustaka.

> Kompilasi lokal: `latexmk -xelatex main.tex` (membutuhkan XeLaTeX + Biber), atau
> manual: `xelatex main` → `biber main` → `xelatex main` → `xelatex main`.

## Yang perlu Anda isi

| Berkas | Isi |
|---|---|
| `main.tex` | Metadata skripsi (judul, nama, NIM, peminatan, tahun, dosen, NIP) di bagian **METADATA SKRIPSI**. |
| `frontmatter/01-prakata.tex` | Prakata. |
| `frontmatter/02-abstrak.tex` | Abstrak + kata kunci. ("x+N halaman" dihitung otomatis.) |
| `frontmatter/03-daftar-singkatan.tex`, `04-daftar-simbol.tex` | Daftar Singkatan & Simbol (opsional — hapus `\input`-nya di `main.tex` bila tak perlu). |
| `bab/bab1-pendahuluan.tex` … `bab5-kesimpulan.tex` | Isi setiap bab. |
| `belakang/lampiran.tex`, `riwayat-hidup.tex` | Lampiran & Riwayat Hidup. |
| `referensi.bib` | Basis data referensi (format BibTeX/Biber). |
| `img/logo_stis.png` | Logo (sudah disertakan; ganti bila perlu). |

## Peminatan (satu sakelar)

Template mendukung kedua peminatan lewat **satu penanda** di `main.tex`:

- **Sains Data** (default, lima bab): biarkan baris `% \peminatansitrue` tetap
  dikomentari. Bab: Pendahuluan, Tinjauan Pustaka, Metode Penelitian, Hasil dan
  Pembahasan, Kesimpulan dan Saran.
- **Sistem Informasi Statistik** (enam bab): hilangkan tanda komentar menjadi
  `\peminatansitrue`, lalu ubah `\peminatan{Sains Data}` menjadi
  `\peminatan{Sistem Informasi Statistik}`. Bab: Pendahuluan, Tinjauan Pustaka,
  Metode Penelitian, **Analisis dan Perancangan**, **Implementasi dan Evaluasi**,
  Kesimpulan dan Saran.

Penanda ini otomatis: (a) mengganti paragraf *Sistematika Penulisan* (lima/enam
bab) pada `bab/bab1-pendahuluan.tex`, dan (b) memilih berkas bab yang tepat di
`main.tex`. Berkas bab kedua peminatan sudah tersedia:

| Sains Data | Sistem Informasi Statistik |
|---|---|
| `bab/bab3-metode.tex` | `bab/bab3-metodologi-si.tex` (SDLC/prototyping) |
| `bab/bab4-hasil.tex` | `bab/bab4-analisis-perancangan.tex` (kebutuhan, *use case*, ERD, antarmuka) |
| `bab/bab5-kesimpulan.tex` | `bab/bab5-implementasi-evaluasi.tex` (implementasi, pengujian *black-box*, evaluasi) |
| — | `bab/bab6-kesimpulan.tex` |

## Fitur format (sesuai pedoman)

- Kertas A4, margin *mirror* (dalam 4 cm; atas/luar/bawah 3 cm), cetak bolak-balik.
- Font **Times New Roman** (atau klon TeX Gyre Termes di Overleaf), 12 pt.
- Teks isi **2 spasi**; halaman muka, daftar, dan pustaka **1,5 spasi**.
- Judul bab **"BAB I"** (Romawi) rata tengah; subbab Arab (1.1, 1.1.1); jarak
  judul deterministik (bab→subbab 4 spasi, bab/subbab→teks 3 spasi).
- Nomor halaman: bagian awal Romawi (tengah bawah), bagian isi Arab (kanan bawah).
- **Tabel**: judul di atas, baris nomor kolom (1)(2)(3), `Sumber` di bawah,
  rata tengah; tabel panjang (`xltabular`) lintas-halaman, lebar ≥80%, judul
  "Tabel N (lanjutan)".
- **Gambar**: judul di bawah (urutan gambar → Sumber → judul).
- **Persamaan**: menjorok 1 tab, nomor (n) rata kanan, deret tunggal.
- **Daftar Pustaka**: APA 7 modifikasi Indonesia via `biblatex` (style=apa) +
  Biber, dengan lokalisasi mandiri `indonesian-apa.lbx` — penghubung "dan",
  "dkk.", "(Ed.)/(Eds.)", "Penerj.", "Dalam", "(hal. …)", "Edisi ke-N", urut
  abjad, *hanging indent*.

## Bantuan menulis

- **Tabel sederhana**: lihat contoh di `bab/bab4-hasil.tex` (lingkungan `table`
  dengan `\caption` di atas, baris `(1) & (2) & (3)`, dan `\sumber{...}`).
- **Tabel panjang**: lihat contoh `xltabular` 0,8\textwidth di `bab/bab4-hasil.tex`.
- **Persamaan multi-baris**: letakkan operator di awal baris lanjutan (lihat
  Persamaan (2) di `bab/bab3-metode.tex`).
- **Teorema/Definisi/Bukti**: lingkungan `definisi`, `teorema`, `lema`, `akibat`,
  `proposisi`, `contoh`, `proof` (label "Bukti") — lihat `bab/bab2`.
- **Algoritme**: lingkungan `algorithm` (kata kunci Indonesia) — lihat `bab/bab3`.
- **Diagram**: gaya TikZ `fc-*` (diagram alir) dan `uc-*` (use case) — lihat `bab/bab3`.
- **Sitasi**: `\textcite{kunci}` (naratif), `\parencite{kunci}` (dalam kurung),
  `\parencite[hal.~5]{kunci}` (dengan halaman).

## Struktur berkas

```
skripsistis-overleaf/
├── main.tex                      # dokumen utama + metadata + sakelar peminatan
├── skripsistis.sty               # seluruh format STIS
├── indonesian-apa.lbx            # lokalisasi APA bahasa Indonesia (biblatex)
├── latexmkrc                     # paksa XeLaTeX + Biber
├── referensi.bib                 # basis data referensi
├── img/logo_stis.png
├── frontmatter/                  # halaman muka, prakata, abstrak, daftar singkatan/simbol
├── bab/                          # bab1, bab2 (bersama) + varian Sains Data & SI
└── belakang/                     # lampiran, riwayat hidup
```

## Catatan

- Logo STIS (`img/logo_stis.png`) adalah milik Politeknik Statistika STIS dan
  disertakan hanya untuk keperluan templat skripsi institusi.

