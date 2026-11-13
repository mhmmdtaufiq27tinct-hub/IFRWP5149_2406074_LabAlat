# Skenario tugas Sistem Informasi Akademik — P03

## Skenario tugas

Mahasiswa memilih mata kuliah dan mengajukan KRS. Setiap pengajuan divalidasi untuk kelengkapan, prasyarat, dan benturan jadwal. Jika valid, sistem menyimpan pengajuan dengan status menunggu persetujuan Dosen Wali. Pada konfirmasi penyimpanan, Mahasiswa dapat memilih mengunduh bukti pengajuan. Dosen Wali menyetujui atau menolak KRS dan memberikan catatan keputusan.

Ketentuan ini fiktif untuk praktikum. Batas SKS, pembayaran, dan kewenangan institusi nyata tidak ditambahkan tanpa sumber. Pertemuan 3 memodelkan kebutuhan KRS SIA-R03–SIA-R06; fungsi jadwal SIA-R01–SIA-R02 dan aktor Admin Akademik tetap berada pada model P02 dan tidak dimasukkan ke diagram SIA P03.

## Kebutuhan tugas P03

| ID | Kebutuhan |
|:--:|:--|
| SIA-R03 | Mahasiswa dapat mengajukan KRS. |
| SIA-R04 | Sistem memvalidasi KRS sebagai bagian pengajuan. |
| SIA-R05 | Mahasiswa dapat mengunduh bukti jika memilihnya pada konfirmasi pengajuan. |
| SIA-R06 | Dosen Wali dapat memproses persetujuan atau penolakan KRS. |

## Aktor P03

| Aktor | Tujuan |
|:--|:--|
| Mahasiswa | Mengajukan KRS dan mengunduh bukti pengajuan bila dipilih. |
| Dosen Wali | Memproses persetujuan atau penolakan KRS. |

## Katalog use case SIA P03

| ID | Nama use case | Peran dalam model |
|:--|:--|:--|
| SIA-UC03 | Ajukan KRS | Fungsi utama Mahasiswa |
| SIA-UC04 | Validasi KRS | Perilaku wajib yang di-include UC03 |
| SIA-UC05 | Unduh Bukti Pengajuan KRS | Tambahan bersyarat pada UC03 |
| SIA-UC06 | Proses Keputusan KRS | Fungsi utama Dosen Wali |

SIA-UC03 `include` SIA-UC04 karena pemeriksaan selalu dijalankan sebagai bagian pengajuan. SIA-UC05 `extend` SIA-UC03 pada extension point **bukti pengajuan tersedia setelah tersimpan**, dengan condition **[mahasiswa memilih unduh]**. Pengajuan tetap berhasil tanpa unduh bukti.

## Batas dan asumsi

- Pengguna terautentikasi; data mata kuliah, prasyarat, dan jadwal tersedia.
- Validasi gagal berarti tidak ada pengajuan baru yang berhasil tersimpan.
- KRS tersimpan belum berarti disetujui.
- Jadwal kuliah dan kelola jadwal adalah fungsi P02; keduanya bukan bagian diagram SIA P03.
- Pembayaran, pengisian nilai, dan implementasi basis data berada di luar cakupan.
