# Deskripsi use case kumulatif SIA P04

## Batas dan aturan

Model menggabungkan kebutuhan SIA P03 dan P04. Pengguna terautentikasi. Kalender akademik adalah agenda institusi, terpisah dari jadwal mata kuliah. Dosen pengampu hanya memasukkan nilai untuk mata kuliah yang diampunya. KHS hanya menampilkan nilai yang telah dipublikasikan. Hapus data mahasiswa hanya jika tidak memiliki data akademik aktif. Pembayaran dan kewenangan institusi nyata berada di luar cakupan.

## Aktor

Mahasiswa dan Dosen merupakan bentuk khusus Civitas Akademika dan mewarisi fungsi melihat kalender akademik. Mahasiswa melihat jadwal kuliah, mengajukan KRS, mengunduh bukti, dan melihat KHS. Dosen Wali memproses persetujuan/penolakan KRS; Dosen Matkul menginput nilai. Admin Akademik mengelola jadwal kuliah dan data mahasiswa.

## Katalog use case

| ID | Nama | Kebutuhan |
|:--|:--|:--|
| SIA-UC01 | Lihat Jadwal Kuliah | SIA-R01 |
| SIA-UC02 | Ajukan KRS | SIA-R03 |
| SIA-UC03 | Validasi KRS | SIA-R04 |
| SIA-UC04 | Unduh Bukti Pengajuan | SIA-R05 |
| SIA-UC05 | Persetujuan atau Penolakan KRS | SIA-R06 |
| SIA-UC06 | Kelola Jadwal Kuliah | SIA-R02 |
| SIA-UC07 | Lihat Kalender Akademik | SIA-R07 |
| SIA-UC08 | Input Nilai Mata Kuliah | SIA-R08 |
| SIA-UC09 | Lihat KHS | SIA-R09 |
| SIA-UC10 | Kelola Data Mahasiswa | SIA-R10 |
| SIA-UC11 | Tambah Data Mahasiswa | SIA-R11 |
| SIA-UC12 | Ubah Data Mahasiswa | SIA-R11 |
| SIA-UC13 | Hapus Data Mahasiswa | SIA-R11 |

SIA-UC02 «include» SIA-UC03 karena validasi selalu menjadi bagian pengajuan. SIA-UC04 «extend» SIA-UC02 pada extension point bukti tersedia dengan kondisi [mahasiswa memilih unduh]. UC11–UC13 adalah bentuk khusus UC10. Collaboration SIA-CO01 Input Nilai Mata Kuliah merealisasikan UC08; SIA-CO02 Lihat KHS merealisasikan UC09.

## Deskripsi use case utama

### SIA-UC02 Ajukan KRS

**Aktor:** Mahasiswa. **Pemicu:** memilih Ajukan KRS. **Prasyarat:** telah terautentikasi dan data mata kuliah tersedia. **Alur:** mahasiswa memilih mata kuliah dan mengirim pengajuan; sistem memvalidasi kelengkapan, prasyarat, dan benturan jadwal; bila valid, sistem menyimpan pengajuan berstatus Menunggu persetujuan dosen wali serta menampilkan konfirmasi. **Alternatif:** validasi gagal menampilkan alasan dan tidak menyimpan pengajuan berhasil. **Pascakondisi:** pengajuan tersimpan menunggu keputusan. Unduh bukti opsional dan tidak mengubah keberhasilan pengajuan.

### SIA-UC08 Input Nilai Mata Kuliah

**Aktor:** Dosen Matkul. **Prasyarat:** dosen berwenang atas mata kuliah tersebut dan masa perkuliahan berakhir. **Alur:** dosen memilih mata kuliah dan mahasiswa, memasukkan nilai, lalu menyimpan; sistem memvalidasi isian dan mencatat nilai. Nilai belum otomatis dianggap dipublikasikan.

### SIA-UC09 Lihat KHS

**Aktor:** Mahasiswa. **Alur:** mahasiswa memilih semester; sistem menampilkan KHS hanya untuk nilai yang telah dipublikasikan. Bila belum ada nilai terpublikasi, sistem menyampaikan bahwa KHS belum tersedia.
