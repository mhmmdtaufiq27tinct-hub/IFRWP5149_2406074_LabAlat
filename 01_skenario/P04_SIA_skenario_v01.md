# Sistem Informasi Akademik
## Skenario Tugas:
### Mahasiswa dan dosen sama-sama merupakan Civitas Akademika yang dapat melihat kalender akademik. Dosen menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. Mahasiswa melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasikan. Admin Akademik mengelola data mahasiswa; menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. Dua use case utama, Input Nilai Mata Kuliah dan Lihat KHS, ditunjukkan realisasinya oleh collaboration yang bersesuaian.
___
## Batas dan asumsi
* Kode kebutuhan dimulai dari SIA-R07 agar SIA-R01 dan SIA-R02 (Pertemuan 2) serta SIA-R03 sampai SIA-R06 (Pertemuan 3) tetap mempunyai identitas berbeda.
* Pengguna telah terautentikasi dan memiliki hak akses sesuai peran.
* Kalender akademik pada tugas ini adalah agenda resmi institusi (awal semester, batas KRS, masa ujian, dan sejenisnya); jangan menyamakannya dengan jadwal kuliah pada Pertemuan 2.
* Nilai hanya dapat diinput oleh dosen pengampu mata kuliah tersebut. Nilai yang diinput belum terpublikasi sebelum dinyatakan resmi oleh ketentuan tugas ini: KHS hanya menampilkan nilai yang sudah dipublikasikan.
* Hapus Data Mahasiswa hanya untuk mahasiswa yang tidak memiliki data akademik aktif. Ketentuan ini fiktif untuk latihan.
* Pengajuan KRS tetap digambar sebagai bagian diagram kumulatif dari Pertemuan 3. Pembayaran dan perancangan basis data berada di luar tugas ini.
___
## Identifikasi Aktor
| Aktor | Kedudukan | Tujuan terhadap sistem |
|:---:|:---|:---|
| Civitas Akademik | Umum (general), baru pada Pertemuan 4 | Peran umum bagi Civitas Akademik yang dapat melihat kalender Akademik. Mewariskan fungsinya kepada Mahasiswa dan Dosen. |
| Mahasiswa | Khusus dari Civitas Akademik, tetap dari Pertemuan 3 | Melihat Kartu Hasil Studi (KHS) untuk semester yang nilainya sudah dipublikasi. |
| Dosen | Khusus dari Peminjam, baru pada Pertemuan 4 | Menginput nilai mata kuliah yang diampunya setelah masa perkuliahan berakhir. |
| Admin Akademik | Laboratorium Tetap dari Pertemuan 3 | Menambah data mahasiswa baru, mengubah data mahasiswa, dan menghapus data mahasiswa. |
___
## Susun Katalog Usecase
| ID | Nama use case | Peran dalam model | Sumber Kebutuhan |
|:---:|:---|:---|:---|
| SIA-UC01 | Lihat Jadwal Kuliah | Fungsi utama Mahasiswa |  |
| SIA-UC02 | Ajukan KRS | Fungsi utama Mahasiswa |  |
| SIA-UC03 | Validasi KRS sebagai pengajuan | Prilaku yang disetakan UC02 |  |
| SIA-UC04 | Unduh Bukti Pengajuan | Tambahan bersyarat pada UC02 |  |
| SIA-UC05 | Persetujuan atau Penolakan KRS | Fungsi utama Dosen Wali |  |
| SIA-UC06 | Kelola Jadwal Kuliah | Fungsi utama Admin |  |
| SIA-UC07 | Melihat kalender akademik | Baru pada pertemuan 4; Fungsi utama civitas akademik | SIA-R07 |
| SIA-UC08 | Menginput nilai mata kuliah | Baru pada Pertemuan 4; Fungsi utama Dosen Matkul | SIA-R08 |
| SIA-UC09 | Melihat Kartu Hasil Studi (KHS). | Baru pada Pertemuan 4; fungsi utama Mahasiswa | SIA-R09 |
| SIA-UC10 | Kelola data mahasiswa. | Baru pada Pertemuan 4; use case KHUSUS dari SIA-UC02 | LAB-R08 |
| SIA-UC11 | Catat Pengembalian Peralatan Baru pada Pertemuan 4; fungsi utama petugas; direalisasikan LAB-UC02 | LAB-R09 |
| SIA-UC12 | Periksa Kondisi Peralatan | Baru pada Pertemuan 4; perilaku yang disertakan LAB-UC11 | LAB-R10 |