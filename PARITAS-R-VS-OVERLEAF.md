# Paritas Fitur: Paket R `skripsistis` vs Template Overleaf (pure-LaTeX)

Dokumen ini memverifikasi bahwa template **Overleaf** (pure-LaTeX) telah memuat
semua hal yang ada pada paket **R `skripsistis`**, dan mencatat perbedaan yang
disengaja (karena perbedaan mesin: Quarto/pandoc + CSL vs LaTeX + biblatex).

## Ringkasan

| Fitur / Aturan pedoman | Paket R `skripsistis` | Template Overleaf | Status |
|---|---|---|---|
| Margin (4-3-3-3 cm, twoside, mirror) | `geometry` di `preamble.tex` | `geometry` di `skripsistis.sty` | ✅ setara |
| Times New Roman (fallback TeX Gyre Termes) | `fontspec` (deteksi font asli) | `fontspec` (deteksi font asli) | ✅ setara |
| Spasi 2/1,5/1 (`setspace`) | ✅ | ✅ | ✅ setara |
| Jarak judul bab/subbab/teks | `titlesec` (satuan `\normalbaselineskip`) | `titlesec` (satuan tetap `\sjudul`=12 pt) | ✅ setara* |
| Penomoran halaman (romawi awal, arab isi, kanan-bawah) | `fancyhdr` | `fancyhdr` | ✅ setara |
| Dua peminatan (Sains Data / Sistem Informasi Statistik) | `bab3_metode(_si)`, `bab4_hasil`/`analisis`, `bab5_*` | `\peminatansitrue`, `bab3-metode`/`metodologi-si`, dst. | ✅ setara |
| Sampul & halaman judul (Lampiran 1 & 2) | `tex/00_frontmatter.tex` | `frontmatter/00-halaman-muka.tex` | ✅ setara |
| Prakata, Abstrak (x+N halaman otomatis) | `lastpage`+`refcount` | `lastpage`+`refcount` | ✅ setara |
| Daftar Isi/Tabel/Gambar/Lampiran (`tocloft`) | ✅ | ✅ | ✅ setara |
| Daftar Singkatan & Simbol | `glossaries`/CSV/off + `scan_singkatan.R` | tabel front-matter (`03/04-daftar-*.tex`) | ✅ setara (impl. beda) |
| Tabel (judul tengah, sumber tepi kiri, nomor kolom, total) | `tabel_skripsi()` | pola `\sbox`+`\parbox` + `\sumber` | ✅ setara |
| Tabel panjang lintas-halaman | `tabel_skripsi_panjang()` (`xltabular`) | `xltabular` (`\endfirsthead/\endhead`) | ✅ setara |
| Gambar (gambar→sumber tepi kiri→judul tengah) | `gambar_skripsi()` | pola `\sbox`+`\parbox` | ✅ setara |
| Tabel/gambar lebar **landscape** | `pdflscape`+`rotating` | `pdflscape`+`rotating` | ✅ setara |
| Persamaan (1 tab, nomor "(n)" rata kanan, pemotongan operator) | `fleqn`, `\mathindent`, `\theequation` | idem | ✅ setara |
| Kutipan APA-7 Indonesia (dan/dkk./hal., langsung pendek/panjang, sekunder) | **CSL** `apa-stis-id.csl` | **biblatex-apa** + `indonesian-apa.lbx` | ✅ setara (mesin beda) |
| Daftar Pustaka APA-7 Indonesia (Penerj., Edisi ke-N, hanging indent, abjad) | CSL | biblatex + `.lbx` | ✅ setara |
| Lampiran (penomoran "Lampiran 1, 2", masuk Daftar Lampiran) | `lampiran.qmd` + `\lampiran` | `belakang/lampiran.tex` + `\lampiran` | ✅ setara |
| Riwayat Hidup | front/belakang qmd | `belakang/riwayat-hidup.tex` | ✅ setara |
| **Listing kode (lipat baris panjang)** | `fvextra` (`code-overflow: wrap`) | **`listings`** (`breaklines=true`) — *ditambahkan* | ✅ setara (baru) |
| Definisi/Teorema/Bukti | (amsthm via Quarto bila dipakai) | `amsthm` (Definisi/Teorema/Bukti) | ✅ ada di Overleaf |
| Algoritme | `algorithm2e` | `algorithm2e` | ✅ setara |

\*Jarak judul: hasil render identik. Overleaf memakai satuan **tetap** `\sjudul`=12 pt
agar kebal terhadap `\doublespacing` (di paket R satuan `\normalbaselineskip` —
hasil sama selama dipanggil pada konteks `\singlespacing` judul).

## Perbedaan yang disengaja (bukan kekurangan)

1. **Mesin sitasi.** Paket R memakai **CSL** (pandoc-citeproc) melalui Quarto;
   Overleaf memakai **biblatex-apa** + berkas lokalisasi `indonesian-apa.lbx`.
   Keduanya menghasilkan APA-7 versi Indonesia yang sama (terverifikasi:
   "dan", "dkk.", "hal.", "Penerj.", "Edisi ke-N", hanging indent, urut abjad).
2. **Antarmuka tabel/gambar.** Paket R menyediakan **fungsi** (`tabel_skripsi()`,
   `gambar_skripsi()`) yang *meng-generate* LaTeX; Overleaf menyediakan **pola
   LaTeX** setara (`\sbox`+`\parbox`+`\sumber`) yang ditulis tangan. Keluaran
   tata letaknya kini identik.
3. **Daftar Singkatan/Simbol.** Paket R mendukung tiga mode (`glossaries`, CSV,
   off) dengan pemindai pra-render; Overleaf memakai tabel front-matter sederhana
   yang diisi manual. Keduanya menghasilkan halaman daftar yang patuh pedoman.
4. **Paket yang otomatis ditambahkan Quarto/pandoc** (amsmath, graphicx,
   hyperref, dll.) tidak tampil di `preamble.tex` paket R karena disuntik oleh
   pandoc; di Overleaf dideklarasikan eksplisit pada `skripsistis.sty`.

## Perbaikan tata letak judul/sumber (diterapkan di KEDUA tempat)

Sesuai instruksi terbaru, **judul tabel dan judul gambar kini DIPUSATKAN**
(boleh melebihi tepi kiri-kanan objek), sedangkan **sumber diletakkan di tepi
kiri objek**; khusus **gambar**, urutannya **gambar → Sumber → judul**.

| Elemen | Sebelum | Sesudah (kedua deliverable) |
|---|---|---|
| Judul tabel | rata kiri tepi tabel | **di tengah** |
| Judul gambar | rata kiri tepi gambar | **di tengah** |
| Sumber tabel | (Overleaf: tepi teks) | **tepi kiri tabel** |
| Sumber gambar | setelah judul | **tepi kiri gambar, sebelum judul** |

Implementasi:
- Paket R: `R/tabel.R` (`tabel_skripsi`, `tabel_skripsi_panjang`) & `R/gambar.R`
  (`gambar_skripsi`) — judul `\captionof` dikeluarkan dari `\parbox` agar
  ter-pusatkan; `justification=centering` pada `preamble.tex`.
- Overleaf: `skripsistis.sty` (`\captionsetup{...justification=centering}`) +
  contoh `bab4-hasil.tex` (pola `\sbox`+`\parbox`).

**Kesimpulan:** Template Overleaf telah memuat **seluruh** fitur paket R
(termasuk listing kode yang baru ditambahkan); perbedaan tersisa hanyalah pilihan
mesin (CSL vs biblatex) dan antarmuka (fungsi R vs pola LaTeX), dengan keluaran
yang setara dan patuh pedoman.

## Verifikasi tambahan: Sampul, Halaman Judul, & jarak Daftar (paket R)

Konstruksi **sampul** dan **halaman judul** paket R disamakan dengan template
Overleaf yang sudah diverifikasi terhadap pedoman (Lampiran 1 & 2). Hasil ukur
render paket R:

| Aturan | Overleaf | Paket R (setelah perbaikan) |
|---|---|---|
| Judul mulai ~baris kedua (di bawah margin atas) | 0,71 cm | **0,71 cm** (identik) |
| Judul kapital 14 pt, antar baris 2 spasi | ✅ | ✅ |
| Subjudul 14 pt, 1,5 spasi | ✅ | ✅ |
| Nama/NIM 12 pt; jarak Nama 5 spasi, Prodi 4,5 spasi | ✅ | ✅ |
| Blok Program Studi/Peminatan **di tengah** (membungkus) | ✅ | ✅ (sebelumnya rata kiri) |
| Tiga baris penutup 14 pt/1,5 spasi, terkunci bawah (`\vfill`) | ✅ | ✅ |
| Halaman judul: SKRIPSI→Diajukan(1,5)→Oleh(3 spasi)→nama/NIM, tanpa blok prodi | ✅ | ✅ |

**Jarak Daftar (Isi/Tabel/Gambar/Lampiran)** — diperbaiki di **kedua** template:

| Jarak | Sebelum | Sesudah |
|---|---|---|
| Judul "DAFTAR ISI" → "Halaman" | 0,5 baris | 0,7 baris |
| "Halaman" → entri pertama | **2 baris** | **1 baris** |
| Judul "DAFTAR TABEL/GAMBAR/LAMPIRAN" → header kolom | **4 baris** | **1,5 baris** |
| Header kolom → entri pertama | 1,5 baris | 1 baris |

### Satu perbedaan tersisa (catatan)
Jarak **judul bab/subbab** paket R masih memakai satuan `\normalbaselineskip`
(`3\normalbaselineskip`), sedangkan Overleaf memakai satuan **tetap** `\sjudul`=12 pt
agar kebal terhadap `\doublespacing`. Hasil render keduanya sesuai pedoman selama
judul berada pada konteks `\singlespacing` (sebagaimana saat ini); penyelarasan ke
`\sjudul` dapat dilakukan bila diinginkan keseragaman penuh.
