# Skenario dan katalog kumulatif SIA P04

## Skenario tugas

Mahasiswa dan Dosen adalah Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat KHS untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa dengan menambah, mengubah, dan menghapus data. SIA-CO01 merealisasikan Input Nilai Mata Kuliah; SIA-CO02 merealisasikan Lihat KHS.

## Aktor dan generalization

| Aktor | Kedudukan dan fungsi |
|:--|:--|
| Civitas Akademika | Aktor umum; dapat melihat Kalender Akademik (UC07). |
| Mahasiswa | Aktor khusus Civitas Akademika; mewarisi UC07, dan memiliki fungsi UC01, UC03, UC05, UC09. |
| Dosen | Aktor khusus Civitas Akademika; mewarisi UC07, dan menginput nilai (UC08). |
| Admin Akademik | Aktor tetap; mengelola Jadwal Kuliah (UC02) dan Data Mahasiswa (UC10). |
| Dosen Wali | Aktor tetap; memproses keputusan KRS (UC06). |

## Katalog kumulatif SIA P04

| ID | Nama use case | Aktor/peran | Sumber |
|:--|:--|:--|:--|
| SIA-UC01 | Lihat Jadwal Kuliah | Mahasiswa | P02; SIA-R01 |
| SIA-UC02 | Kelola Jadwal Kuliah | Admin Akademik | P02; SIA-R02 |
| SIA-UC03 | Ajukan KRS | Mahasiswa | P03; SIA-R03 |
| SIA-UC04 | Validasi KRS | Include UC03 | P03; SIA-R04 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Mahasiswa; extend UC03 | P03; SIA-R05 |
| SIA-UC06 | Proses Keputusan KRS | Dosen Wali | P03; SIA-R06 |
| SIA-UC07 | Lihat Kalender Akademik | Civitas Akademika | P04; SIA-R07 |
| SIA-UC08 | Input Nilai Mata Kuliah | Dosen | P04; SIA-R08; SIA-CO01 |
| SIA-UC09 | Lihat KHS | Mahasiswa | P04; SIA-R09; SIA-CO02 |
| SIA-UC10 | Kelola Data Mahasiswa | Admin Akademik; umum | P04; SIA-R10 |
| SIA-UC11 | Tambah Data Mahasiswa | Khusus UC10 | P04; SIA-R11 |
| SIA-UC12 | Ubah Data Mahasiswa | Khusus UC10 | P04; SIA-R11 |
| SIA-UC13 | Hapus Data Mahasiswa | Khusus UC10 | P04; SIA-R11 |

UC03 `include` UC04. UC05 `extend` UC03 dengan condition [mahasiswa memilih unduh] di extension point bukti pengajuan tersedia. UC11–UC13 adalah spesialisasi UC10; aktor Admin Akademik berasosiasi dengan UC10 dan fungsi anak mewarisi perilaku umumnya. Mahasiswa dan Dosen mewarisi asosiasi UC07 dari Civitas Akademika tanpa menggambar ulang asosiasi tersebut.

## Batas dan asumsi

- Kalender akademik adalah agenda resmi institusi, terpisah dari jadwal mata kuliah.
- Dosen hanya menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir.
- Nilai input belum otomatis dipublikasikan; KHS hanya menampilkan nilai yang sudah dipublikasikan.
- Hapus data mahasiswa hanya diperbolehkan bila tidak ada data akademik aktif.
- Pengguna terautentikasi dan memiliki hak sesuai peran. Pembayaran dan rancangan basis data di luar cakupan.
