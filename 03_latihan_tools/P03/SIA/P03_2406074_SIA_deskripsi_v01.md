# Deskripsi use case SIA Pertemuan 3

## SIA-UC02 Ajukan KRS

| Elemen | Deskripsi |
|:--|:--|
| Tujuan | Menyimpan pengajuan KRS yang lolos validasi untuk menunggu keputusan dosen wali |
| Aktor utama | Mahasiswa |
| Sumber kebutuhan | SIA-R03, SIA-R04, SIA-R05 |
| Pemicu | Mahasiswa memilih Ajukan KRS |
| Prasyarat | Mahasiswa terautentikasi; katalog mata kuliah dan data prasyarat tersedia |
| Pascakondisi berhasil | Pengajuan tersimpan dengan status Menunggu persetujuan dosen wali |
| Pascakondisi gagal | Tidak ada pengajuan baru yang berhasil tersimpan |
| Include | SIA-UC03 Validasi KRS: kelengkapan, prasyarat, dan benturan jadwal |
| Extension point | Bukti pengajuan tersedia setelah tersimpan |
| Extend | SIA-UC04 Unduh Bukti Pengajuan jika [mahasiswa memilih unduh] |

### Alur utama

| Langkah | Kegiatan aktor | Respons sistem |
|:--:|:--|:--|
| 1 | Memilih mata kuliah untuk KRS | Menampilkan pilihan mata kuliah |
| 2 | Mengirim pengajuan | Memeriksa kelengkapan, prasyarat, dan benturan jadwal (SIA-UC03) |
| 3 | — | Jika valid, menyimpan KRS dengan status menunggu persetujuan |
| 4 | Melihat konfirmasi | Menampilkan ringkasan pengajuan serta bukti yang tersedia |
| 5 | Memilih unduh bila diinginkan | Menjalankan SIA-UC04 pada kondisi extend |

**Alternatif:** Validasi gagal menampilkan alasan dan tidak menyimpan pengajuan berhasil. Tidak memilih unduh tidak memengaruhi keberhasilan. **Catatan:** Lihat Jadwal Kuliah (SIA-UC01) dan Kelola Jadwal Kuliah (SIA-UC06) merupakan fungsi mandiri sesuai kebutuhan P02, bukan ekstensi persetujuan KRS.
