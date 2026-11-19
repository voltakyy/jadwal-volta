# Jadwal Volta

[![Live demo](https://img.shields.io/badge/live-jadwal--volta-2f7d5a?style=flat-square)](https://jadwal-volta.vercel.app)
[![Single file](https://img.shields.io/badge/build-none-D9A441?style=flat-square)](#menjalankan)
[![localStorage](https://img.shields.io/badge/penyimpanan-localStorage-197C7A?style=flat-square)](#data-yang-tersimpan)

Dashboard jadwal kuliah pribadi **Muhammad Rizky Prasetya** (NIM L200260089),
Program Studi Informatika UMS, Semester Gasal 2026/2027, Kelas B, 19 SKS.

Selain jadwal mingguan, halaman ini menyatukan materi dan silabus, peta studi
delapan semester, panduan memilih konsentrasi, alat bantu belajar, dan roadmap
menuju cumlaude. Seluruh aplikasi berada dalam satu file `index.html`.

**Live:** <https://jadwal-volta.vercel.app>

## Fitur

### Hari ini dan jadwal mingguan

- Ringkasan hari ini: daftar kelas, ruang, dan dosen.
- Kelas berikutnya lengkap dengan hitung mundur.
- Sorotan otomatis untuk kelas yang sedang berlangsung.
- Tab jadwal Senin–Jumat dan ringkasan beban mingguan.
- Ekspor `.ics` untuk Google Calendar, Apple Calendar, atau Outlook. Jadwal
  berulang 16 minggu dengan zona waktu `Asia/Jakarta`.

### Materi dan silabus

- Materi per mata kuliah dengan topik dari RPS dan tautan Google Drive.
- Progres belajar per topik yang tersimpan otomatis di browser.
- Silabus mata kuliah dalam bentuk akordeon.
- Daftar mata kuliah semester ini: 8 entri KRS (19 SKS) plus dua tes TOEFL
  wajib maba.

### Perencanaan studi

- Peta studi 8 semester dengan total SKS per semester.
- Panduan memilih konsentrasi sejak semester awal.
- Perbandingan tiga konsentrasi: Rekayasa Perangkat Lunak (145 SKS), Sistem
  Jaringan (147 SKS), dan Sistem Interaktif Cerdas (145 SKS).
- Roadmap cumlaude lima tahap, dari fondasi sampai skripsi.

### Alat bantu belajar

| Alat | Fungsi |
| --- | --- |
| To-Do List | Menambah, mencentang, dan menghapus tugas |
| Pomodoro Timer | Sesi fokus dengan hitungan waktu |
| Pelacak IPK | Menghitung IPK dari bobot nilai tiap mata kuliah |
| Catatan Cepat | Catatan bebas yang tersimpan otomatis |

## Data yang tersimpan

Semua data pribadi pengguna disimpan di `localStorage`; tidak ada akun, backend,
atau analytics.

| Kunci | Isi |
| --- | --- |
| `ums_materi_progress_v1` | Topik materi yang sudah selesai |
| `ums_todo_v1` | Daftar tugas |
| `ums_ipk_v1` | Nilai mata kuliah untuk perhitungan IPK |
| `ums_notes_v1` | Catatan cepat |

Menghapus data situs di browser akan mengosongkan semua progres tersebut.

## Menjalankan

File tunggal, tanpa build step dan tanpa dependensi:

```powershell
start index.html
```

Atau buka `index.html` langsung di browser. Koneksi internet hanya dibutuhkan
untuk memuat Google Fonts (Inter dan Plus Jakarta Sans); tanpa internet, font
fallback sistem tetap dipakai.

## Kustomisasi

Data akademik berada di dalam `<script>` pada `index.html`:

| Variabel | Isi |
| --- | --- |
| `scheduleData` | Jadwal mingguan per hari |
| `materiData` | Mata kuliah, topik, dan tautan materi |
| `silabusData` | Silabus per kode mata kuliah |
| `krsData` | Daftar mata kuliah dan SKS semester ini |
| `kurikulumData` | Peta studi 8 semester |
| `baseDate` | Tanggal mulai ekspor `.ics` (14 September 2026) |

Jika repo ini dipakai ulang, ganti nama, NIM, kelas, jadwal, dosen, dan tautan
materi terlebih dahulu. Data tersebut tertulis langsung di HTML dan ikut terlihat
di halaman publik.

## Struktur

```text
index.html   markup, CSS, data akademik, dan seluruh logika aplikasi
```

## Catatan

- Ini dashboard pribadi, bukan sistem resmi UMS. Jadwal dan silabus dapat berubah
  sewaktu-waktu; selalu cocokkan dengan informasi kampus.
- Data pribadi (nama, NIM, jadwal, tautan Drive) sengaja ditampilkan untuk
  keperluan pemilik. Jangan menambahkan data sensitif lain ke file ini.
- Tidak ada analytics atau backend. Satu-satunya permintaan eksternal adalah
  Google Fonts.
