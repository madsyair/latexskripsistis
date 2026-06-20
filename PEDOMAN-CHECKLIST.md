# Daftar Aturan Pedoman & Status Kepatuhan Template

Rujukan: **Pedoman Penyusunan Skripsi Prodi D-IV Komputasi Statistik – Politeknik Statistika STIS, Edisi Keenam Tahun 2025**, termasuk contoh pada Lampiran 1 (Halaman Sampul), Lampiran 2 (Halaman Judul), dan Lampiran 7 (Daftar Isi).

Status: ✅ sesuai & terverifikasi dari render · 🔧 diperbaiki pada revisi ini.
Konvensi spasi (setspace): **1 spasi → `\singlespacing` (≈14,5pt) · 1,5 spasi → `\onehalfspacing` (≈18pt) · 2 spasi → `\doublespacing` (≈24pt)**. Untuk jarak diskret, "1 spasi" = ukuran huruf (12pt badan; 14pt judul sampul).

---

## A. Format Umum Halaman

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| A1 | Kertas A4 (21×29,7 cm), HVS putih | `\documentclass[a4paper]` | ✅ |
| A2 | Margin ganjil: atas=bawah=kanan=3 cm, kiri=4 cm; genap dicerminkan | `geometry{inner=4cm,top=3cm,outer=3cm,bottom=3cm,twoside}` | ✅ |
| A3 | Alinea baru 1 tab = 1,27 cm | `\parindent=1.27cm` | ✅ |
| A4 | Times New Roman 12 pt, rata kiri-kanan (justify) | TeX Gyre Termes 12pt (metrik identik TNR), justify | ✅ |
| A5 | Jarak antar baris teks **2 spasi** | terukur 24,0 pt = 2 spasi | ✅ |
| A6 | Istilah asing dicetak miring | `\emph{...}` / `\textit{...}` | ✅ |
| A7 | Judul bab KAPITAL; subbab Huruf Besar Tiap Awal Kata | `\chapter{}` (uppercase), `\section{}` (title case) | ✅ |

## B. Jarak Judul, Float, & Daftar

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| B1 | Judul bab → subbab **4 spasi** | terukur 49 pt ≈ 4 spasi (`afterskip` bab 1,5·12pt) | 🔧 |
| B2 | Bab/subbab → teks **3 spasi** | terukur 36 pt = 3 spasi | 🔧 |
| B3 | Judul level-4 (pokok bahasan, **tebal, tanpa nomor**) → 4 spasi di atasnya | `\subsubsection{}` `beforeskip` 2·12pt | ✅ |
| B4 | Abstrak **1,5 spasi** | terukur 18,2 pt = 1,5 spasi | 🔧 |
| B5 | Daftar Isi bab↔subbab **1,5 spasi**; entri multi-baris 1 spasi | terukur 17,8 pt = 1,5 spasi (seragam) | 🔧 |
| B6 | Daftar Pustaka: dalam-entri **1 spasi**, antar-sumber **1,5 spasi**, hanging 1 tab | terukur 14,4 pt / 22 pt | ✅ |
| B7 | Tabel/gambar **3 spasi** dari teks | terukur ≈38 pt ≈ 3 spasi | 🔧 |

> Catatan teknis B1–B2 & B7: di bawah `\doublespacing`, `\normalbaselineskip` ikut menggembung (×1,67) sehingga jarak judul/float sempat **2× lipat**. Diperbaiki memakai panjang TETAP `\sjudul`=12 pt (kebal `\doublespacing`).

## C. Penomoran Halaman & Bab

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| C1 | Bagian awal: angka Romawi kecil, **tengah bawah** | `\pagenumbering{roman}`, footer center | ✅ |
| C2 | Bagian isi & akhir: angka Arab, **kanan bawah** | `\pagenumbering{arabic}`, footer right | ✅ |
| C3 | Setiap bab mulai halaman baru | `report` + `openright` | ✅ |
| C4 | Nomor bab Romawi besar (I, II, …); subbab Arab (2.1, 2.1.1, maks 3 level) | "BAB I", `\thesection` | ✅ |

## D. Halaman Sampul — Lampiran 1

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| D1 | Judul mulai **baris kedua**, KAPITAL, TNR 14 pt, simetris, **2 spasi** antar baris, tanpa kata terpenggal | judul terukur **0,71 cm di bawah margin atas** (=baris kedua); antar-baris 28 pt = 2 spasi | 🔧 |
| D2 | Subjudul: baris berikutnya, **1,5 spasi** | `\fontsize{14}{21}` (1,5×14) | ✅ |
| D3 | Nama (KAPITAL TNR 12 pt) berjarak **5 spasi** dari baris terakhir judul/subjudul | `\vspace{5\spasi}` | ✅ |
| D4 | Nama → NIM **1,5 spasi** | `\fontsize{12}{18}` (1,5×12) | 🔧 |
| D5 | Program Studi → NIM **4,5 spasi**; "KOMPUTASI STATISTIK PROGRAM DIPLOMA IV" + peminatan; **blok di tengah** | `\vspace{4.5\spasi}`; tabular `p{6.7cm}` di `\centering` → blok di tengah, nilai membungkus rapi | 🔧 |
| D6 | Logo 5×5 cm, simetris di ruang antara Program Studi & tulisan STIS | `\includegraphics[width=5cm,height=5cm]` di antara dua `\vfill` | ✅ |
| D7 | Tiga baris terakhir (POLITEKNIK STATISTIKA STIS / JAKARTA / tahun) KAPITAL TNR 14 pt, **1,5 spasi**, di bawah | tahun terukur **3,05 cm dari bawah** (=margin bawah) | 🔧 |

## E. Halaman Judul — Lampiran 2

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| E1 | Format judul **sama** dengan sampul | sama (baris kedua, 14pt, 2 spasi) | ✅ |
| E2 | "SKRIPSI" berjarak **5 spasi** setelah judul | `\vspace{5\spasi}` | 🔧 |
| E3 | "Diajukan sebagai …" **1,5 spasi** | `\fontsize{12}{18}` | ✅ |
| E4 | "Oleh:" pada **baris ketiga** (3 spasi); lalu Nama/NIM; logo; institusi — **tanpa blok Prodi/Peminatan** | `\vspace{3\spasi}`; struktur sesuai | ✅ |

## F. Abstrak

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| F1 | "ABSTRAK" baris kedua, posisi tengah atas | `\chapter*{Abstrak}` (center) | ✅ |
| F2 | Nama, judul, info halaman (x + halaman isi+lampiran) | otomatis `viii+14 halaman` via `\pageref` | ✅ |
| F3 | Maksimum 200 kata, **1,5 spasi** | `\begin{spacing}{1.5}` | 🔧 |
| F4 | Kata kunci (3–5) di bawah | baris "Kata kunci: …" | ✅ |
| F5 | **Di halaman terpisah** | `\chapter*` + `\clearpage`, tanpa halaman kosong | 🔧 |

## G. Daftar Isi / Tabel / Gambar / Lampiran — Lampiran 7

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| G1 | "DAFTAR ISI" baris kedua, tengah | judul tocloft center | ✅ |
| G2 | Nama bab & subbab + nomor halaman; bab↔subbab **1,5 spasi**, multi-baris 1 spasi | `\cftbeforechapskip=0` → seragam 1,5 spasi | 🔧 |
| G3 | Daftar Tabel/Gambar/Lampiran: "No. … Judul … Halaman" | `\listoftables`, dll. dengan header kolom | ✅ |
| G4 | Abstrak & **tiap daftar di halaman terpisah** | `\clearpage` sebelum tiap daftar | 🔧 |
| G5 | Jarak **judul daftar → "Halaman"/header kolom = 4 spasi** (anotasi pedoman Lampiran 7 & 8) | `\vskip2\spasi` → terverifikasi rasio thd tinggi entri **2,58** vs pedoman **2,60** | 🔧 |
| G6 | Jarak "Halaman"/header → entri pertama ~2 spasi | `cftaftertoctitleskip=1.5\spasi` (TOC), `cftafter*titleskip=\spasi` (daftar) | 🔧 |

## H. Tabel & Gambar

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| H1 | Tabel/gambar simetris **di tengah**, 3 spasi dari teks | `\centering`, `\intextsep` | ✅ |
| H2 | Nomor+judul: huruf kecil kecuali awal kata, **tanpa titik akhir** | `\caption{}`, `labelsep=period` | ✅ |
| H3 | Judul multi-baris **hanging** (baris ke-2 sejajar teks judul), **1 spasi** | `format=hang`, `stretch=1.0` (terverifikasi) | ✅ |
| H4 | Judul **tabel di ATAS**; judul **gambar di BAWAH** | `position=top`/`position=bottom` | ✅ |
| H5 | Judul & **sumber rata kiri di batas kiri teks**; objek di tengah | caption `raggedright`; `\sumber` `raggedright` | 🔧 |
| H6 | Urutan gambar: **gambar → judul → sumber** | `\caption` lalu `\sumber` | 🔧 |
| H7 | Sumber dicantumkan **hanya jika data sekunder** (primer/olahan sendiri: tidak) | `\sumber{...}` opsional | ✅ |
| H8 | Tabel lebar: landscape **atau** diperkecil (huruf min 8 pt) | contoh `\begin{landscape}` (Tabel 3) — judul atas-kiri, tabel di tengah, sumber bawah-kiri | 🔧 |
| H9 | Tabel panjang: "Tabel N (lanjutan)", judul kolom diulang tiap halaman | `xltabular` + `\endhead` | ✅ |

## I. Persamaan Matematika

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| I1 | Persamaan baris tersendiri, **1 tab (1,27 cm) dari batas kiri** | `fleqn`, `\mathindent=1.27cm` (terverifikasi) | ✅ |
| I2 | Diberi **nomor urut** dalam kurung **(1), (2), …** posisi **rata kanan** (pedoman: "nomor urut", contoh menampilkan "(1)" — *bukan* (bab.urut)) | `\theequation=(\arabic{equation})`, `\counterwithout{equation}{chapter}` | 🔧 |
| I3 | Pemenggalan: **operator di awal baris lanjutan**, sejajar suku pertama setelah "=" | `aligned` dgn `={}&` / `&{}+` (terverifikasi) | ✅ |

> Catatan I2: nomor persamaan sempat tampil tanpa kurung ("1", "2") karena blok `\AtBeginDocument` kedua (`\counterwithout`) menimpa format `\theequation`. Diperbaiki dengan menerapkan ULANG `(\arabic{equation})` setelah `\counterwithout` → kini **(1), (2)** dan rujukan **"Persamaan (1)"**.

## J. Daftar Pustaka

| # | Aturan (pedoman) | Contoh / Implementasi | Status |
|---|---|---|---|
| J1 | Format **APA versi 7** dengan penyesuaian bahasa Indonesia | biblatex-apa + `indonesian-apa.lbx` | ✅ |
| J2 | Urut **abjad** nama akhir pengarang | `sorting=nyt` (Cochran, Etang, Megawati, Taufiq) | ✅ |
| J3 | Hanging indent 1 tab; dalam-entri 1 spasi; antar-sumber 1,5 spasi | `\singlespacing` + `\bibitemsep` | ✅ |
| J4 | Penyesuaian Indonesia: dkk., dan, Dalam, hal., Ed./Eds., Penerj., Edisi ke-N | `.lbx` + `\DeclareDelimFormat` (terverifikasi: "dan", "Penerj.", "Edisi ke-2") | ✅ |

## K. Kutipan dalam Teks — Pedoman 4.4

| # | Aturan (pedoman) | Contoh terverifikasi | Status |
|---|---|---|---|
| K1 | Tidak langsung (parafrase): nama + tahun, **tanpa halaman** | `\textcite` → "Cochran (1991)"; `\parencite` → "(Cochran, 1991)" | ✅ |
| K2 | Dua pengarang → **"dan"** (naratif & kurung) | "Taufiq dan Mariyah (2021)"; "(Taufiq dan Mariyah, 2021)" | ✅ |
| K3 | Lebih dari dua pengarang → **"dkk."** | "Etang dkk. (2022)"; "(Etang dkk., 2022)" | ✅ |
| K4 | Langsung pendek (≤40 kata): tanda kutip + **"hal."**; naratif → halaman di akhir; kurung → di dalam | "Cochran (1991) … '…' (hal. 10)."; "'…' (Taufiq dan Mariyah, 2021, hal. 781)." | 🔧 |
| K5 | Langsung panjang (>40 kata): **paragraf tersendiri, 1 tab dari kiri**, tanpa tanda kutip | env `kutipanpanjang` (`\leftskip=1.27cm`) | 🔧 |
| K6 | Sitasi sekunder: "… seperti dikutip dalam …"; hanya sumber sekunder di Daftar Pustaka | "Nelder dan Wedderburn (1972), seperti dikutip dalam Cochran (1991)" | 🔧 |
| K7 | Lembaga/instansi: **pertama** nama lengkap+akronim, **selanjutnya** akronim; Daftar Pustaka **selalu nama lengkap** (pedoman 4.4) | `author={{Badan Pusat Statistik}}`,`shortauthor={{BPS}}` → otomatis "Badan Pusat Statistik (BPS, 2024)" lalu "BPS (2024)" | 🔧 |
| K8 | Direktorat di bawah kementerian (APA-7): unit terspesifik = **penulis**, kementerian = **penerbit** | `author={{Direktorat Jenderal …}}`,`institution={Kementerian …}` → "Direktorat … (Ditjen PDP, 2023)"; di Pustaka kementerian sbg penerbit | 🔧 |

> Catatan persamaan: kata **"Persamaan"/"persamaan" ditulis MANUAL** (`Persamaan~\ref{eq:...}` di Overleaf; `eq-prefix` kosong + ketik "Persamaan" di paket R). `\ref`/`@eq-...` hanya menghasilkan nomor "(N)". Pada paket R (CSL), pola lembaga pertama-penuh-akronim ditulis manual: `[BPS, -@kunci]`.

---

### Ringkasan perbaikan pada revisi ini (🔧)
1. **Jarak judul** (B1–B2, B7) — unit tetap `\sjudul`=12 pt agar kebal `\doublespacing`.
2. **Abstrak** (B4, F3) — 1 spasi → **1,5 spasi**.
3. **Daftar Isi** (B5, G2) — diseragamkan **1,5 spasi**.
4. **Tata letak tabel/gambar** (H5, H6) — judul & sumber **rata kiri di batas kiri teks**; urutan gambar **gambar→judul→sumber**.
5. **Halaman terpisah** (F5, G4) — Abstrak & tiap daftar di halaman sendiri, **tanpa halaman kosong**.
6. **Sampul & Judul** (D1, D4, D5, D7, E2) — judul tepat di **baris kedua**; tahun di **margin bawah**; blok Prodi **di tengah** (nilai membungkus); spasi antar bagian dengan unit eksplisit (2 spasi=2×font, 1,5 spasi=1,5×font); judul **multi-baris** (1–5 baris) tetap muat satu halaman.
7. **Nomor persamaan** (I2) — kurung "(1), (2)" yang sempat hilang **dipulihkan**.
8. **Tabel lebar landscape** (H8) — ditambah **contoh nyata** (Tabel 3) sesuai aturan tata letak.
9. **Kutipan dalam teks** (K1–K6) — ditambah **demonstrasi lengkap** di Bab II (parafrase, langsung pendek, langsung panjang/blok 1 tab, sitasi sekunder) — semua terverifikasi "dan/dkk./hal." sesuai APA-7 Indonesia.
