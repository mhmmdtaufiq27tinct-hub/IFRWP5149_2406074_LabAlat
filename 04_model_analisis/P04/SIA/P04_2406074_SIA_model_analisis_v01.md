# Model analisis use case kumulatif SIA P04

## Aktor

| Aktor | Kedudukan/fungsi |
|:--|:--|
| Civitas Akademika | Aktor umum; Lihat Kalender Akademik (UC07). |
| Mahasiswa | Khusus Civitas; mewarisi UC07 serta berasosiasi UC01, UC03, UC05, UC09. |
| Dosen | Khusus Civitas; mewarisi UC07 serta berasosiasi UC08. |
| Admin Akademik | Asosiasi UC02 dan UC10. UC11–UC13 mewarisi perilaku umum UC10. |
| Dosen Wali | Asosiasi UC06. |

## Katalog kumulatif

| ID | Nama use case | Sumber |
|:--|:--|:--|
| SIA-UC01 | Lihat Jadwal Kuliah | P02 / SIA-R01 |
| SIA-UC02 | Kelola Jadwal Kuliah | P02 / SIA-R02 |
| SIA-UC03 | Ajukan KRS | P03 / SIA-R03 |
| SIA-UC04 | Validasi KRS | P03 / SIA-R04 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | P03 / SIA-R05 |
| SIA-UC06 | Proses Keputusan KRS | P03 / SIA-R06 |
| SIA-UC07 | Lihat Kalender Akademik | P04 / SIA-R07 |
| SIA-UC08 | Input Nilai Mata Kuliah | P04 / SIA-R08 |
| SIA-UC09 | Lihat KHS | P04 / SIA-R09 |
| SIA-UC10 | Kelola Data Mahasiswa | P04 / SIA-R10 |
| SIA-UC11 | Tambah Data Mahasiswa | P04 / SIA-R11 |
| SIA-UC12 | Ubah Data Mahasiswa | P04 / SIA-R11 |
| SIA-UC13 | Hapus Data Mahasiswa | P04 / SIA-R11 |

## Spesifikasi hubungan diagram (P04)

| Sumber | Hubungan | Tujuan |
|:--|:--|:--|
| Mahasiswa | Asosiasi | UC01 Lihat Jadwal Kuliah |
| Mahasiswa | Asosiasi | UC03 Ajukan KRS |
| Mahasiswa | Asosiasi | UC05 Unduh Bukti Pengajuan KRS |
| Mahasiswa | Asosiasi | UC09 Lihat KHS |
| Admin Akademik | Asosiasi | UC02 Kelola Jadwal Kuliah |
| Admin Akademik | Asosiasi | UC10 Kelola Data Mahasiswa |
| Dosen Wali | Asosiasi | UC06 Proses Keputusan KRS |
| Civitas Akademika | Asosiasi | UC07 Lihat Kalender Akademik |
| Mahasiswa | Generalization | Civitas Akademika |
| Dosen | Generalization | Civitas Akademika |
| Dosen | Asosiasi | UC08 Input Nilai Mata Kuliah |
| UC03 Ajukan KRS | `include` | UC04 Validasi KRS |
| UC05 Unduh Bukti Pengajuan KRS | `extend` [mahasiswa memilih unduh] | UC03 Ajukan KRS; extension point: bukti tersedia setelah tersimpan |
| UC11 Tambah Data Mahasiswa | Generalization | UC10 Kelola Data Mahasiswa |
| UC12 Ubah Data Mahasiswa | Generalization | UC10 Kelola Data Mahasiswa |
| UC13 Hapus Data Mahasiswa | Generalization | UC10 Kelola Data Mahasiswa |
| SIA-CO01 Input Nilai Mata Kuliah | Realization | UC08 Input Nilai Mata Kuliah |
| SIA-CO02 Lihat KHS | Realization | UC09 Lihat KHS |

## Aturan model

- UC01 dan UC02 adalah fungsi jadwal P02; tidak bergantung pada keputusan KRS.
- Mahasiswa dan Dosen mewarisi fungsi kalender dari Civitas Akademika; asosiasi diwarisi tidak digambar ulang.
- UC11–UC13 adalah spesialisasi UC10; asosiasi aktor ke use case umum tidak perlu digambar ulang pada anak.
- UC08 hanya untuk Dosen pengampu; nilai tersimpan belum otomatis dipublikasikan.
- UC09 hanya menampilkan nilai yang sudah dipublikasikan.
- UC13 menghapus hanya data mahasiswa tanpa data akademik aktif.
- Collaboration merealisasikan use case, bukan aktor, use case tambahan, atau urutan aktivitas.
