# Sistem Informasi Akademik
### Skenario tugas:
Mahasiswa mengajukan KRS dengan memilih mata kuliah. 
Setiap pengajuan menjalankan validasi KRS yang memeriksa kelengkapan, prasyarat mata kuliah, dan benturan jadwal.
Jika validasi berhasil, sistem menyimpan pengajuan berstatus menunggu persetujuan dosen wali.
Pada konfirmasi penyimpanan, mahasiswa dapat memilih mengunduh bukti pengajuan.
Dosen wali menyetujui atau menolak KRS dan memberikan catatan keputusan.
Ketentuan ini fiktif untuk praktikum.
Batas SKS, aturan pembayaran, dan kewenangan institusi nyata tidak boleh ditambahkan tanpa sumber.
### Tabel Kebutuhan
| ID | Kebutuhan tugas |
|:---:|:---|
| SIA-R01 | Mahasiswa dapat melihat jadwal kuliah |
| SIA-R02 | Admin akademik dapat mengelola jadwal kuliah |
| SIA-R03 | Mahasiswa dapat mengajukan KRS |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan |
| SIA-R06 | Dosen wali dapat memproses persetujuan atau penolakan KRS |

Kode dimulai dari R03 agar kebutuhan jadwal SIA-R01 dan SIA-R02 dari
Pertemuan 2 tetap mempunyai identitas berbeda.
### Batas dan asumsi:
- Pengguna telah terautentikasi.
- Data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi gagal menyebabkan pengajuan belum berhasil tersimpan.
- Unduh bukti tidak menjadi syarat keberhasilan pengajuan.
- KRS tersimpan belum berarti disetujui.
- Pembayaran, pengisian nilai, dan implementasi basis data berada di luar tugas.
___
### Tentukan Aktor
| Aktor | Tujuan terhadap sistem |
|:---:|:---|
| Mahasiswa | Mengajukan KRS, Melihat jadwal kuliah, Mengunduh bukti pengajuan jika memilih [Konfirmasi pengajuan] |
| Dosen wali | Memproses Persetujuan atau Penolakan KRS |
| Admin Akademik | Mengelola Jadwal kuliah |
___
### Katalog Usecase:
| ID | Nama use case | Peran dalam model |
|:---:|:---|:---|
| SIA-UC01 | Lihat Jadwal Kuliah | Fungsi utama Mahasiswa |
| SIA-UC02 | Ajukan KRS | Fungsi utama Mahasiswa |
| SIA-UC03 | Validasi KRS sebagai pengajuan | Fungsi Utama Admin Akademik |
| SIA-UC04 | Unduh Bukti Pengajuan | Tambahan bersyarat pada UC03 |
| SIA-UC05 | Memproses Persetujuan atau Penolakan KRS | Fungsi utama Dosen Wali |
___
### Relasi Include
#### LAB-UC02 «include» LAB-UC03
##### Alasan: pemeriksaan menjadi bagian validasi pengajuan.
___
### Relasi Extend
#### LAB-UC04 «extend» LAB-UC03
##### Extension point: Bukti pengajuan tersedia.
##### Kondisi: [mahasiswa memilih unduh].
##### Alasan: pengajuan tetap berhasil tanpa pengunduhan.