# Spesifikasi hubungan diagram kumulatif SIA Pertemuan 4

| Sumber | Hubungan | Tujuan |
|:--|:--|:--|
| Mahasiswa | Asosiasi | SIA-UC01 Lihat Jadwal Kuliah |
| Mahasiswa | Asosiasi | SIA-UC02 Ajukan KRS |
| Mahasiswa | Asosiasi | SIA-UC04 Unduh Bukti Pengajuan |
| Mahasiswa | Asosiasi | SIA-UC09 Lihat KHS |
| Mahasiswa | Generalization | Civitas Akademika |
| Dosen | Generalization | Civitas Akademika |
| Civitas Akademika | Asosiasi | SIA-UC07 Lihat Kalender Akademik |
| Admin Akademik | Asosiasi | SIA-UC06 Kelola Jadwal Kuliah |
| Admin Akademik | Asosiasi | SIA-UC10 Kelola Data Mahasiswa |
| Admin Akademik | Asosiasi | SIA-UC11 Tambah Data Mahasiswa |
| Admin Akademik | Asosiasi | SIA-UC12 Ubah Data Mahasiswa |
| Admin Akademik | Asosiasi | SIA-UC13 Hapus Data Mahasiswa |
| Dosen Wali | Asosiasi | SIA-UC05 Persetujuan atau Penolakan KRS |
| Dosen Matkul | Asosiasi | SIA-UC08 Input Nilai Mata Kuliah |
| Dosen | Asosiasi | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-UC02 Ajukan KRS | «include» | SIA-UC03 Validasi KRS |
| SIA-UC04 Unduh Bukti Pengajuan | «extend» [mahasiswa memilih unduh] | SIA-UC02 Ajukan KRS |
| SIA-UC11 Tambah Data Mahasiswa | Generalization | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC12 Ubah Data Mahasiswa | Generalization | SIA-UC10 Kelola Data Mahasiswa |
| SIA-UC13 Hapus Data Mahasiswa | Generalization | SIA-UC10 Kelola Data Mahasiswa |
| SIA-CO01 Input Nilai Mata Kuliah | Realization | SIA-UC08 Input Nilai Mata Kuliah |
| SIA-CO02 Lihat KHS | Realization | SIA-UC09 Lihat KHS |

Model mempertahankan UC01–UC06 dari P03. UC07–UC13 adalah kebutuhan baru. Penghapusan dibatasi pada data mahasiswa tanpa data akademik aktif. SIA-R12 dicakup melalui dua realization collaboration.
